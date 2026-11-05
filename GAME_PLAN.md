# FRONTLINE: ERANGEL — Complete Game Plan

## Product objective
Build a serious, mobile-first, landscape 3D battle-royale shooter inspired by the scale, clarity, and interaction patterns of modern mobile tactical shooters. This is an original browser game, not a PUBG asset/code copy. Prioritize responsive controls, readable combat, convincing materials/lighting, a large explorable battlefield, and systems that actually work over decorative mock controls.

## Product boundaries
- Target: modern mobile browsers first; desktop browsers supported for development and keyboard/mouse.
- Orientation: landscape-first, with an orientation prompt on narrow portrait screens.
- Rendering: WebGL through Three.js; adaptive pixel ratio, capped shadow quality, instancing/merged geometry where useful.
- Assets: prefer permissively licensed, ready-to-use GLB/GLTF assets when verified; procedural fallback geometry ensures the game never depends on a third-party model host.
- Multiplayer: prepare clean seams for a future online transport, but this milestone is offline-first. No fake online mode.
- Original identity: FRONTLINE: ERANGEL, with original UI, map layout, names, and generated/procedural assets.

## Requested experience and acceptance criteria

### 1. Launch / home
- Premium military-tactical presentation, clear hierarchy, responsive landscape layout.
- Fullscreen control using the browser Fullscreen API.
- Settings panel: graphics preset, sound toggle/volume, sensitivity, aim sensitivity, camera inversion, quality/performance options.
- Offline and Online entry points. Online is visibly marked as coming/integration-ready until a real server exists.
- Customize HUD action opens a drag-layout editor. Persist layout positions locally.
- Settings and launch navigation must work on touch and desktop.

### 2. Offline lobby
- Start Match action.
- Two teams, Blue and Red.
- Independent bot count controls for each team, each starting at 0.
- Plus/minus controls, bounded safely; clear team labels and total count.
- Map/mode briefing and match configuration summary.
- Bots spawn only after starting a match; no bots are silently added in the lobby.

### 3. Match / battlefield
- Large outdoor battlefield with distinct terrain zones, roads, vegetation, rocks, cover, compound buildings, multi-storey structures (1–2–3 floors), stair access, windows/doorways and loot locations.
- Third-person player controller with a fixed-position joystick (not dynamic), fast default sprint movement, camera orbit, collision and ground handling.
- Combat: fire, aim/scope, reload, weapon switching, hit feedback, health and ammo.
- Two primary weapon slots; swap between them. Backpack has unlimited capacity for collected items (no arbitrary slot cap).
- Loot pickups distributed through the world: ammunition, medical supplies, optics, weapon pickups and equipment.
- Functional backpack/inventory panel and item collection feedback.
- Jump, crouch, heal, pause and resume.
- Pause panel includes return to lobby and HUD layout customization.
- Bot AI: navigation/roaming, target acquisition, line-of-sight checks, cover-aware firing, damage/death, team affiliation. Bots must not shoot through solid building walls.
- Team logic: bots identify enemies, not allies; independent Blue/Red team counts.
- Minimap: player arrow, camera field-of-view wedge, visible teammate/enemy markers with clear team colors, world bounds and orientation.
- Multi-touch: movement + aim + fire + jump/crouch/scope should be independently usable. Avoid one global touch handler swallowing all controls.
- Desktop keyboard/mouse fallback.

### 4. HUD / touch controls
- Fixed left joystick; separate right-side look region.
- Dedicated fire, scope/aim, weapon swap, backpack, jump, crouch, heal, pause.
- Layout editor supports dragging individual HUD controls and saving/resetting the layout.
- Large touch targets, safe-area insets, landscape scaling and pointer capture.
- Buttons provide visible pressed/active/disabled states and meaningful feedback.

### 5. Quality, stability and performance
- No toy-like flat UI; use layered tactical panels, restrained accent colors, typography, icons, depth and consistent spacing.
- Materials, fog, directional lighting, sky, terrain variation and environmental composition.
- No critical external runtime dependency beyond the Three.js CDN; if model assets fail, procedural geometry remains.
- Adaptive quality for mobile GPU and desktop.
- Resize handling, context-loss messaging, pause-on-background behavior, and safe restart.
- Test startup, lobby, match start, movement, camera, firing, weapon swap, pickups, inventory, healing, pause/resume, return to lobby, minimap, HUD editor and mobile multi-touch.

## Implementation sequence (follow in order; update this file after each step)

- [x] Step 1 — Establish architecture and product specification. Define runtime, boundaries, screens, systems, and acceptance checklist. (This file.)
- [ ] Step 2 — Build the launch experience and responsive design system: fullscreen, settings, offline/online entry points, landscape handling, HUD editor shell.
- [ ] Step 3 — Build offline lobby: two teams, independent bot counters defaulting to zero, start match.
- [ ] Step 4 — Build 3D world foundation: camera, lighting, terrain, environment composition, buildings and collision.
- [ ] Step 5 — Build player controller: fixed joystick, fast sprint, camera look, jump, crouch, desktop controls, multi-touch.
- [ ] Step 6 — Build combat and weapon systems: two weapon slots, swap, firing, scope, reload, health/damage.
- [ ] Step 7 — Build loot, unlimited backpack, pickups and healing.
- [ ] Step 8 — Build bot AI and team combat: navigation, line of sight, wall occlusion, team awareness, spawn counts.
- [ ] Step 9 — Build minimap and tactical HUD: FOV wedge, player/bot markers, ammo/health/team status.
- [ ] Step 10 — Complete pause flow and draggable/persistent HUD layout customization.
- [ ] Step 11 — Add audio hooks, effects, polish, graphics settings, responsive performance tuning and resilience.
- [ ] Step 12 — Run functional/static checks, fix defects, update documentation and verify deployed service.

## Current implementation notes
Step 1 completed. The next implementation step is Step 2. Keep this checklist honest: only mark a step complete after its code exists and its acceptance checks have been performed. If a feature is partial, describe it as partial rather than claiming completion.

## Deployment
Host as a static site on Render from the GitHub repository. No server/database is required for the offline milestone. A later online multiplayer milestone can add an authoritative game server separately.
