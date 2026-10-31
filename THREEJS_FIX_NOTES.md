# Three.js / 3D Studio Fix

## Changes
- Pinned `three` to `0.128.0` in `package.json`.
- Replaced independent CDN script tags with a sequential loader that tries the npm-installed local build first and then the matching CDN build.
- Deferred Three.js-dependent objects in `studio3d.js` until `THREE` is confirmed to exist.
- Added guarded initialization and a user-facing fallback/retry state for unavailable Three.js or WebGL initialization failures.
- Removed the invalid `three.min.js` placeholder file (it contained an unpkg policy error response, not JavaScript).
- Removed unused OrbitControls, GLTFLoader, and MeshoptDecoder script requests; the current studio engine does not reference those APIs.

## Run locally
```bash
npm install
npm start
```
Open `http://localhost:5050/`.

## Validation still required in a browser
- Confirm the Network panel loads `node_modules/three/build/three.min.js` with HTTP 200.
- Confirm the 3D Studio renders and camera/garment interactions work.
- Block both local and CDN Three.js requests and confirm the fallback appears while the rest of the app remains usable.
- Test a browser/device without WebGL and confirm the fallback appears.
