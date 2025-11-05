# AI Activities — README

Compact overview of the single-file, client-side demos in this folder. Open any `.html` file in a modern browser (Chrome / Edge / Firefox). No server required.

---

## Files
- `activity1_maze_modern.html` — Activity 1: AI Maze Solver (modern UI)
- `activity2_waste_routing.html` — Activity 2: Smart Waste Collection Routing (Leaflet)
- `activity3_parking_modern.html` — Activity 3: AI-Based Parking Assistant (modern UI)
- `activity4_faults_retro_blue.html` — Activity 4: Symbolic Fault Diagnosis (retro terminal, blue/white theme)
- `activity5_smart_home_modern.html` — Activity 5: Smart Home Assistant (modern UI)

---

## How to run
1. Copy the `.html` files into a folder.
2. Open any file in a browser (double-click or File → Open).
3. All apps are client-side; no server required. If local file issues occur, run a simple server (Windows example):
   - python: `python -m http.server` (from the folder)
   - Node: `npx http-server .`

---

## Activity summaries

### Activity 1 — AI Maze Solver
- Purpose: Interactive maze builder + animated search demo (BFS, DFS, A*, Greedy).
- Main UI: grid editor, algorithm selector, speed/diagonal toggles, generate/solve/export.
- Key JS functions: `buildModel`, `renderGrid`, `neighborsOf`, `solveAnimated`, `export` (canvas PNG).

### Activity 2 — Smart Waste Collection Routing (file: activity2_waste_routing.html)
- Purpose: Plan and simulate waste collection routes on real street networks; truck returns to depot after collecting bins.
- Libraries used: Leaflet, Leaflet Routing Machine.
- Main UI: city selector (Bangalore, Manhattan, Downtown LA, Central London, Chicago, SoMa SF); mode buttons (Place Depot, Add Waste Bin); controls (traffic level, Plan Route, Start Collection, Clear All, Reset Route); map area (click to place depot/bins; depot & truck markers; right-click to remove); legend & statistics panel; loading overlay.
- Typical user flow: select city → Place Depot → Add Waste Bin(s) → choose traffic → Plan Route (nearest‑neighbour ordering + road routing) → Start Collection (animated truck collects bins) → Clear/Reset.
- Key JS functions: `initializeMap`, `onMapClick`, `placeDepot`, `addWasteBin`, `setMode`, `updateModeInstructions`, `updateTrafficInfo`, `checkRouteReadiness`, `selectCity`, `planOptimalRoute`, `findOptimalOrderWithRoads`, `calculateHaversineDistance`, `startCollection`, `checkBinCollection`, `isNearDepot`, `getTrafficMultiplier`, `calculateFuelCost`, `showLoading`, `resetRouting`, `resetSimulation`, `clearAll`, `updateStats`, `updateProgress`.
- Notes & limitations: nearest‑neighbour heuristic for ordering (approximation); routing uses Leaflet Routing Machine summaries; traffic modeled via simple multipliers (not live); emoji icons used for prototyping.

### Activity 3 — Parking Assistant
- Purpose: Simulate parking lot grid and find nearest free slot (BFS).
- Main UI: parking grid, entry point (Shift+Click), occupancy toggles, controls (Generate, Find Closest, Export JSON).
- Key JS functions: `makeGrid`, `render`, `findClosest`, `autoFillFn`, export handler.

### Activity 4 — Symbolic Fault Diagnosis
- Purpose: KB editor and inference engine showing forward/backward chaining with traceability.
- Main UI: terminal-like pane with rules/facts/trace, editors, and control buttons.
- Rule format: `If A AND B -> C` (antecedents separated by `AND`).
- Key JS functions: `parseRules`, `forwardChain`, `backwardChain`, `cmd_load`, `cmd_forward`, `cmd_backward`, `cmd_export`.

### Activity 5 — Smart Home Assistant
- Purpose: Small logic-driven assistant for home automation decisions (mix of propositional and simple predicate patterns).
- Main UI: rule editor, facts editor, Forward/Backward/Why controls.
- Notes: Temperature facts like `Temperature(Room,16)` are preprocessed to `LT18` style facts for easier matching.
- Key JS functions: `parseRules`, `preprocessFacts`, `forwardChain`, `backwardChain`.

---

## Common implementation notes
- Each demo is a single HTML file with inline JS and uses Tailwind or simple CSS for UI.
- Inference engines (Activities 4 & 5) are simple, string-based educational implementations — not production-grade.
- Visual solvers implement BFS and a basic A* variant. Greedy search is A* without path-cost accumulation.

---

## Extending the demos (ideas)
- Persist KB & layouts to `localStorage`.
- Replace the heuristic queue with a binary heap / priority queue for faster A* on large grids.
- Add GIF/video guides or short screencasts for each activity.
- Add server-side routing or a real TSP/VRP solver for the routing demo if re-introduced.

---

## Troubleshooting
- Grid appears too small: resize browser or reduce rows/cols; maze demo adapts cell size using a ResizeObserver.
- Browser blocks local file access: serve files with `python -m http.server` or similar.
- If an activity references an external library and fails, confirm the library is included or available offline.

---

## License
Provided as-is for learning and prototyping. Modify freely for educational or non-commercial use.

---

## Next steps
I can:
- Package all files into a ZIP, or
- Add short tutorial GIFs for each activity, or
- Provide a minimal Node.js static server script to serve the demos locally.

Which would you like next?
