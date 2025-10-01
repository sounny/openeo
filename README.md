# openeo

This repository collects notes and helper snippets for working with NASA's
Global Imagery Browse Services (GIBS) layers in client applications such as
Leaflet.

## Debugging CORB warnings with GIBS imagery

Chrome's Cross-Origin Read Blocking (CORB) warnings can appear when loading
GIBS VIIRS layers if the imagery date does not exist for the selected
platform. The server responds with an XML `ServiceException`, but because the
client expects image bytes the browser logs a CORB warning even though the
request succeeded.

### Why it happens

* **Wrong platform/date combination** – for example, requesting
  `VIIRS_NOAA20_CorrectedReflectance_TrueColor` tiles for 2013 returns a
  `ServiceException` because NOAA-20 only began producing data in late 2017.
* **Supported time formats** – daily products accept `TIME=YYYY-MM-DD` (ISO
  timestamps such as `YYYY-MM-DDTHH:MM:SSZ` are also accepted, but the date must
  exist for the layer).
* **Meaning of CORB** – CORB blocks cross-origin HTML/XML/JSON bodies from
  being read when an image response was expected; it does not mean the network
  request failed.

### Fixes

* Request a valid date for the selected platform, e.g.
  `TIME=2018-01-02` for NOAA-20 VIIRS corrected reflectance.
* Use the Suomi-NPP VIIRS layer (`VIIRS_SNPP_CorrectedReflectance_TrueColor`)
  when imagery prior to late 2017 is required (data coverage starts on
  2015-11-24).

### Leaflet example

```html
<div id="map" style="height: 70vh;"></div>
<label>
  Date:
  <input id="date" type="date" value="2018-01-02" min="2017-11-19" max="2025-10-01">
</label>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css">
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script>
  const map = L.map('map').setView([20, 0], 2);

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 9,
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  const gibsEndpoint = 'https://gibs.earthdata.nasa.gov/wms/epsg3857/best/wms.cgi';

  const viirsLayer = L.tileLayer.wms(gibsEndpoint, {
    layers: 'VIIRS_NOAA20_CorrectedReflectance_TrueColor',
    version: '1.3.0',
    format: 'image/jpeg',
    transparent: false,
    time: '2018-01-02',
    tileSize: 256,
    crossOrigin: 'anonymous'
  }).addTo(map);

  document.getElementById('date').addEventListener('change', (event) => {
    viirsLayer.setParams({ TIME: event.target.value });
  });

  // Switch to Suomi-NPP for pre-2017 dates
  // viirsLayer.setParams({ layers: 'VIIRS_SNPP_CorrectedReflectance_TrueColor', TIME: '2016-01-02' });
</script>
```

This example demonstrates how to update the `TIME` parameter in response to a
date-picker control. Use `format: 'image/png'` with `transparent: true` when
overlaying the imagery on top of another basemap.
