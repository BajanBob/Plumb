# Plumb Field Survey

An offline-first field companion for land surveyors, built for use anywhere in the world.

- **Points & QA** – record or import points (CSV/PNEZD, lat/long or UTM). Every point is checked as you go: duplicate IDs, double shots, accuracy over tolerance, float/DGPS/autonomous solutions, missing heights or codes, points outside the job's UTM zone, and too few clean control points. A to-scale plan shows each point's status.
- **Deed closure** – enter bearings and distances in metres, international or US survey feet, chains, links, rods or yards. Get the misclosure, precision ratio (1:n), perimeter and Bowditch-adjusted area (ha, acres, m², sq ft), plus a plot showing the closing error.
- **Convert** – WGS84 latitude/longitude ↔ UTM for every zone (including the Norway and Svalbard exceptions), DMS ↔ decimal, and distance unit conversion.
- **Export** – DXF (layer per code), LandXML 1.2, PNEZD CSV, GeoJSON and a field QA report, singly or as one zip.
- **Device GPS** (desktop and Android builds) – averages phone or laptop fixes for 15 s. These are metre-level fixes, for finding marks, not for setting boundaries.

## Builds

| Platform | File | Notes |
|---|---|---|
| Android | `Plumb-<version>.apk` | Debug-signed, for sideloading. Enable "Install unknown apps". |
| Windows | `Plumb-Setup-<version>.exe` | Installer |
| Windows | `Plumb-Portable-<version>.exe` | Single exe, no install |
| Windows | `Plumb-<version>-win-x64.zip` | Unzip and run `Plumb Field Survey.exe` |

GitHub Actions builds all of these on every push to `main` and attaches them to the GitHub Release for the version in `package.json` (bump the version to publish a new release).

## Develop

```bash
npm ci
npm start                 # run the desktop app
npx cap sync android      # copy www/ into the Android project
npm run dist:win          # Windows builds (needs Windows, or Linux with Wine)
```

The whole app is `www/index.html` with no dependencies.

## Geodesy notes

UTM uses the Krüger series on WGS84 and agrees with PROJ to 0.1 mm. National grids and local datums need their own transformation; Plumb doesn't apply one.
