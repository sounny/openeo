# Open EO Viewer

Open EO Viewer is a lightweight Leaflet application for exploring NASA's Global Imagery Browse Services (GIBS) layers. It lets you switch between common true-color products, pick a date, and sketch areas of interest directly on the map. Drawn shapes can be exported to GeoJSON for further analysis or sharing with other tools.

## Features

- **Leaflet + GIBS integration** – browse daily NASA imagery without needing an API key.
- **Layer switching** – toggle between VIIRS and MODIS true-color layers with a single dropdown.
- **Date selection** – start from the latest NOAA-20 true-color image (2025-06-06) or choose any other available day.
- **Drawing tools** – capture polygons or rectangles on top of the imagery and export them as GeoJSON.

## Getting started

1. Open `index.html` in a browser (or serve the repository with your favorite static file server).
2. Use the layer and date controls in the toolbar to update the map imagery.
3. Activate the drawing controls in the lower-left corner to sketch features and export them via the **Export GeoJSON** button.

## Contributing

This project is intentionally simple and we welcome ideas that make it more useful. If you build a new capability—such as additional imagery layers, new export formats, or enhanced map interactions—please open a pull request so others can benefit as well. Bug fixes, documentation improvements, and other suggestions are also appreciated!

## License

This repository is released under the MIT License. See [LICENSE](LICENSE) for details.
