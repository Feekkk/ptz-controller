# PIXY E3138 — Browser PTZ Remote

A single-page remote control for the EMEET PIXY E3138 webcam. It drives UVC pan, tilt, and zoom straight from the browser — no install, no backend.

## Live site

https://feekkk.github.io/ptz-script.github.io/

Deployed automatically to GitHub Pages on every push to `main` via `.github/workflows/pages.yml`. The HTTPS URL satisfies the secure-context requirement for camera access.

## Run locally

The camera API only works on `localhost` or HTTPS. Opening `index.html` from disk (`file://`) will not work.

```sh
python3 -m http.server 8080
```

Then open http://localhost:8080 in Chrome or Edge.

## PTZ limits

- Pan/tilt/zoom uses the browser's `getUserMedia` PTZ constraints, which only Chromium browsers (Chrome, Edge) expose. Other browsers show the preview but disable the PTZ controls.
- The PIXY locks digital zoom at 4K and at 1080p 60 fps; the zoom controls are disabled in those modes.
- Only UVC pan/tilt/zoom is possible from a webpage. AI tracking, privacy mode, and gesture control require the EMEET Studio desktop app.
- If the camera opens but PTZ is missing, close apps holding the camera (EMEET Studio, Zoom, Teams), replug the USB cable, and retry in Chrome or Edge.
