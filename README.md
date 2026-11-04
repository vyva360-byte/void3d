# void3d

A single-file Three.js survival slice for Beaconfall.

## Play

Open `index.html` in a modern browser with an internet connection. Three.js is loaded from jsDelivr.

- WASD move, mouse look, Shift sprint, Space jump
- E gathers or uses nearby objects; click attacks; I opens pack; Esc or P pauses
- Gather 4 timber and 3 emberstone to relight the beacon
- Enter a world seed for a repeatable coast. Continue restores the latest local save.

## Verified scope

One procedural pine coast, gathering, lantern crafting, one beacon objective, day/night survival pressure, one wisp enemy, pause, and local save/Continue. The in-game CUT LIST names the larger systems intentionally left out.

Checks: JavaScript syntax passes. Targeted smoke tests pass for movement after turning, pause on pointer-lock exit, depleted resource persistence, and victory → title → new-game flow. Food restoration, repeated-play GPU cleanup, Three.js upgrade, full campaign content, and long-session performance remain known limitations; no performance guarantees are made.
