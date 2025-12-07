# Pull Request Review

## Summary
The current implementation works as a simple GIBS viewer, but there are a few functional gaps that would impact users switching layers and dates.

## Findings
1. **Hard-coded default date is brittle** – The UI initializes to `2025-06-06` regardless of when the app is opened. Once that date is outside the available imagery window, the first load will fail silently and show a blank map. The default should be computed dynamically (e.g., today minus a safety buffer or by querying the layer capabilities) instead of a fixed string.【F:index.html†L115-L204】
2. **Date bounds don't match layer availability** – The date picker allows any date back to 2000, but VIIRS NOAA-20 and SNPP coverage starts much later. Selecting early dates returns empty tiles without feedback. The min/max should adjust per layer (e.g., NOAA-20 from 2018, SNPP from 2012) to prevent impossible requests.【F:index.html†L79-L204】
3. **Layer switches don't validate the current date** – When changing the layer, the existing date is reused even if it's outside the new layer's range, again producing blank imagery. The change handler should clamp/validate the selected date for the chosen layer or prompt the user.【F:index.html†L115-L221】

Addressing these points would make the viewer more reliable and reduce confusing blank-map states for users.
