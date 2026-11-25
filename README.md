# WATER POLO 3D — Olympic Water Polo

[![Play Live](https://img.shields.io/badge/▶%20Play%20Live-GitHub%20Pages-0891b2?style=for-the-badge)](https://ashoebb.github.io/water-polo-3d/)
[![Three.js](https://img.shields.io/badge/Three.js-0.169.0-1e6de8?style=for-the-badge)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge)](LICENSE)

**Live Demo:** [https://ashoebb.github.io/water-polo-3d/](https://ashoebb.github.io/water-polo-3d/)

A self-contained **3D WebGL Water Polo** game built with HTML5, CSS, and **Three.js (`0.169.0`)** in a single zero-build file (`waterpolo-3d.html`).

Play 7v7 Olympic water polo from a FIFA-style broadcast perspective featuring procedural articulated swimmers, real-time animated water with caustics and splash physics, tactical 3-3 half-court sets, counter-attacks, and authentic water polo rules.

---

## Features

### 1. 3D Olympic Arena & Animated Water (`PoolArena`)
- **25m × 20m × 2m Pool:** Tiled basin and floor lane markings, coping rim, tiled pool decks, starting blocks, multi-tiered stadium seating, and 4 floodlight towers.
- **Official Markings & Goals:** Floating boundary ropes, red `2m` and yellow `6m` boundary markers, and 3D goal cages with net meshes at `x = -12.5` and `x = +12.5`.
- **Real-Time Water & Splash Physics:** Subdivided `y = 0` water surface (`#088ba8`) with vertex wave displacement, clearcoat highlights, animated pool-floor caustic patterns, and pooled 3D wake rings and spray droplets.

### 2. Articulated 7v7 Swimmers & Procedural Animation (`SwimmerRig`)
- **14 Hierarchical 3D Characters:** Blue (`#1e6de8`) vs White (`#f4f1ea`) with `pelvis`, `torso`, `headGroup` (numbered cap texture + goggles), shoulders, elbows, hands, hips, knees, and feet.
- **Procedural Animation States:**
  - **Treading Water:** Upright eggbeater leg kicks, sculling hands, and vertical bobbing.
  - **Freestyle Swim/Sprint:** Speed-blended horizontal pitch, overhead arm strokes, flutter kicks, body roll, and side-breathing head turns.
  - **Ball Carry, Pump Fake & Shot Wind-Up:** Cocked throwing arm above water, baulk/pump-fake motion, torso wind-up, and release follow-through.
  - **Goalkeeper:** High-tread stance with raised hands and lateral/upward save lunges.

### 3. Authentic Water Polo Rules, Tactics & AI (`AIController`, `Ball3D`, `GameEngine`)
- **3 AI Difficulty Levels:** `ROOKIE`, `PRO`, and `OLYMPIC` scaling AI swim speed, decision cadence, passing-lane interceptions, GK reaction speed, shot placement, pump fakes, and counter-attack awareness.
- **Real Formations & Counter-Attacks:** 3-3 Umbrella/Arc half-court offense (Point, Left/Right Drivers, Left/Right Wings, 2m Center Forward), goal-side + M-zone slough defense, and dynamic breakaway counter-attacks on steals, interceptions, and saves.
- **Official Rules Implemented:**
  - Quarter **Swim-Offs** (`Q1–Q4`, `2:00` quarters, `30s` shot clock).
  - **2-Meter Offside** rule with live HUD warning chip.
  - **Ordinary Fouls** (free-throw protection) & **20-Second Exclusions (6v5 Man-Up)**.
  - **Goal Throws** & **2m Corner Throws** on wide/parried shots.
  - **Goalkeeper Possession Control & Protection** (control your GK when in possession; opponents cannot press or crowd a ball-holding GK).
- **Ballistics & Techniques:** Spin-stabilized passes, water **skip shots**, driven corner shots, **lob shots**, and **pump fakes (baulks)** to bait goalkeepers.

### 4. Broadcast Camera, On-Water Cues & Audio (`Renderer3D`, `SoundFX`)
- Smooth sideline broadcast camera with ball-speed and pitch-position zoom.
- Active player FIFA-style selection ring, pass-target indicator ring, 3D water-surface aim arrow, and curved shot power gauge.
- Auto-switching on defense/loose balls with manual `Q`/`E` override lock (`2.6s`) and HUD toggle (`AUTO-SW`).
- Procedural Web Audio synthesizer (whistle, splashes, throws, goalpost clang, goal horn) with zero external audio assets.

---

## Controls

| Input | Action |
| :--- | :--- |
| `WASD` / `Arrow Keys` | Swim in 8 directions (relative to camera) |
| `Shift` | Sprint (uses stamina) |
| `Mouse` | Aim pass / shot in 3D world space |
| `Space` *(Tap)* | Pass to best-aligned teammate |
| `Space` *(Hold & Release)* | Charge & fire power / skip shot |
| `R` | Lob shot over goalkeeper |
| `Right-Click` or `B` | Pump fake / baulk (baits goalkeeper) |
| `E` | Switch to nearest defender / Call for pass |
| `Q` | Cycle controlled Blue player |
| `F` | Close-range steal / tackle lunge |
| `P` or `Esc` | Pause / Resume / Change difficulty |

---

## Architecture

All code is cleanly modularized inside [`waterpolo-3d.html`](waterpolo-3d.html):

- `PoolArena` — Pool geometry, stadium seating, floodlights, boundary markers, goal cages, animated water mesh, caustics, and splash/droplet pools.
- `SwimmerRig` — Hierarchical `THREE.Group` character rig and procedural animation state machine.
- `Ball3D` — Ballistic gravity, spin, water skip-shot bounce, goalpost/crossbar collisions, goal detection, and endline out-of-bounds.
- `AIController` — 3-3 attack spacing, M-zone/goal-side defense, counter-attack lane sprinting, smart passing/shooting, and goalkeeper tracking/lunging.
- `Renderer3D` — Three.js scene, lighting, shadows, broadcast camera, and on-water visual cues.
- `GameEngine` — Match loop, clocks, input handling, auto-switch, rules enforcement, and HUD synchronization.
- `SoundFX` — Procedural Web Audio API sound effects.

---

## Running Locally

Because `waterpolo-3d.html` loads Three.js (`0.169.0`) via ES module CDN (`unpkg.com`), an internet connection is required when opening the page.

**Option 1 — Open directly**
Double-click `waterpolo-3d.html` in your file explorer, or open it in any modern WebGL-capable browser (Chrome, Edge, Firefox, Safari).

**Option 2 — Serve via local HTTP server**
```bash
npx serve .
# or
python -m http.server 8080
```
Then open `http://localhost:8080/waterpolo-3d.html`.

---

## License

Released under the [MIT License](LICENSE).
