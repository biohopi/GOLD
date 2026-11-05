# FRONTLINE: ERANGEL

A mobile-first, landscape-oriented 3D tactical battle royale prototype built for the browser.

## Run locally
Serve this directory over HTTP (ES modules and WebGL require a local server):
```bash
python -m http.server 8080
```
Open `http://localhost:8080` on a desktop or mobile browser. On mobile, rotate to landscape and tap **Enter Fullscreen**.

## Current scope
Offline single-player training match with two configurable bot teams. Online multiplayer is intentionally left as a future integration point.

## Tech
Three.js, WebGL, ES modules, procedural environment assets, responsive touch HUD. No build step.

See [GAME_PLAN.md](GAME_PLAN.md) for the implementation plan and completion checklist.
