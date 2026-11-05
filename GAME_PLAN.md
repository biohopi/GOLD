# FRONTLINE: ERANGEL — Complete Game Plan

## Product objective
Build a serious, mobile-first, landscape 3D battle-royale shooter inspired by the scale, clarity, and interaction patterns of modern mobile tactical shooters. This is an original browser game, not a PUBG asset/code copy. Prioritize responsive controls, readable combat, convincing materials/lighting, a large explorable battlefield, and systems that actually work over decorative mock controls.

## Product boundaries
- Target: modern mobile browsers first; desktop browsers supported for development and keyboard/mouse.
- Orientation: landscape-first, with an orientation prompt on narrow portrait screens.
- Rendering: WebGL through Three.js; adaptive pixel ratio, capped shadow quality, instancing/merged geometry where useful.
- Assets: prefer permissively licensed, ready-to-use GLB/GLTF assets when verified; procedural fallback geometry ensures the game never depends on a third-party model host.
- Multiplayer: online play is a required product goal. Keep the offline mode usable while implementing a real authoritative online server; never present a placeholder as playable multiplayer.
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
- [x] Step 2 — Build the launch experience and responsive design system: fullscreen, settings, offline/online entry points, landscape handling, HUD editor shell.
- [x] Step 3 — Build offline lobby: two teams, independent bot counters defaulting to zero, start match.
- [x] Step 4 — Build 3D world foundation: camera, lighting, terrain, environment composition, buildings and collision (first-pass procedural world; detailed interior navigation remains a later polish item).
- [ ] Step 5 — Build player controller: fixed joystick, correctly mapped directional controls, fast sprint, stable full-area camera drag, jump, crouch, collision, desktop controls and multi-touch. (In progress: joystick horizontal mapping and document-level drag tracking improved; needs device verification.)
- [ ] Step 6 — Build combat and weapon systems: two weapon slots, swap, firing, selectable 1x/2x/4x/8x optics, scoped view, reload, hit feedback and health/damage. (In progress: optic selection, scoped overlay and reload control added.)
- [ ] Step 7 — Build loot, unlimited backpack, pickups and healing.
- [ ] Step 8 — Build bot AI and team combat: navigation, line of sight, wall occlusion, team awareness, spawn counts.
- [ ] Step 9 — Build minimap and tactical HUD: correctly oriented FOV wedge, player/bot markers, ammo/health/team status. (In progress: corrected wedge heading; verify on device.)
- [ ] Step 10 — Complete pause flow and draggable/persistent HUD layout customization.
- [ ] Step 11 — Add audio hooks, effects, polish, graphics settings, responsive performance tuning and resilience.
- [ ] Step 12 — Run functional/static checks, fix defects, update documentation and verify deployed service.
- [ ] Step 13 — Design and implement online architecture: authoritative match server, room lifecycle, player identity/session, reconnect handling, server tick and state replication.
- [ ] Step 14 — Build online room lobby: create/join room, host controls, two-team player slots, independent bot counts per team, ready state and launch flow.
- [ ] Step 15 — Integrate real-time multiplayer gameplay: movement replication, server-authoritative combat/damage, bot simulation, loot state, match end and disconnect recovery.
- [ ] Step 16 — Deploy and load-test online services, configure production environment/secrets, validate latency and reconnect behavior.

## Current implementation notes
The first control-and-world refinement pass has been committed: square-bodied block soldiers replace capsule characters; the blocked doorway filler was removed; joystick horizontal mapping was reversed to match expected left/right input; camera drag tracking now continues at document level after pointer capture; the old AIM label was replaced by a hold-to-scope control with selectable 1x/2x/4x/8x optics and a scope overlay; reload was added; the minimap view wedge now follows camera heading. These are code changes, not yet verified on a physical phone. Building interiors, stairs, collision, weapon feel, AI and online multiplayer remain incomplete. The online button is still only a placeholder; real online server work remains required in Steps 13–16. Keep this checklist honest: only mark a step complete after its code exists and its acceptance checks have been performed.

## Deployment
Host as a static site on Render from the GitHub repository. No server/database is required for the offline milestone. A later online multiplayer milestone can add an authoritative game server separately.
