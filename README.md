# Live OGF Americana — web prototype

A mobile-friendly MapLibre web viewer aimed at OpenGeofiction's OpenMapTiles data.

## Run

```bash
npm install
npm run dev
```

Then open the Vite URL on a browser. For an iPhone, deploy the built `dist/` folder to any HTTPS static host.

## Important: “instant” vs official Americana

OpenGeofiction's official Americana vector dataset is rebuilt periodically, so **a browser-only project cannot make that source update instantly**. This prototype deliberately makes only normal slippy-map tile requests and lets HTTP/browser caching do its job.

For genuinely near-live data, the source behind `OGF_TILEJSON` must be an OpenMapTiles-compatible endpoint fed by OGF replication (or another server-side tile pipeline). That is the part that cannot be implemented safely/reliably as static browser JavaScript without repeatedly requesting large raw OGF bounding boxes.

## Americana

The real OpenStreetMap Americana project is CC0 and uses MapLibre + OpenMapTiles. To use the *exact* current Americana runtime style (including its dynamic shields), build/fork `osm-americana/openstreetmap-americana` and point its OpenMapTiles source at the OGF-compatible tile endpoint. This starter includes a lightweight Americana-compatible fallback style so the project stays small and easy to run.

## Endpoint

`src/main.js` currently expects:

    https://openmaptiles.opengeofiction.net/data/v3.json

If OGF exposes its TileJSON at a different path, change the `OGF_TILEJSON` constant. The OGF FAQ confirms the service root is `https://openmaptiles.opengeofiction.net/`, but does not document a stable TileJSON subpath.
