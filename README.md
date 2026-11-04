# VOID3D: Beaconfall

A single-file first-person survival slice. Explore one procedural pine coast, gather materials, craft a torch, and relight the old beacon before night turns dangerous.

## Play

Open `index.html` in a modern browser with an internet connection. Three.js loads from jsDelivr; no other assets, build step, server, or installation are needed.

- **WASD** move, **mouse** look, **Shift** sprint, **Space** jump
- **E** gather nearby timber or emberstone, or relight the beacon
- **Click** strike a nearby wisp, **I** open your pack, **Esc** pause
- The beacon costs **4 timber + 3 emberstone**. Crafting a torch is optional.
- Enter a seed to regenerate the same coast. Progress autosaves locally; **Continue** resumes in that browser.

## In this slice

Procedural island terrain and pine trees, first-person movement, tree/crystal gathering, a beacon objective and safe radius, optional torch crafting, day/night pressure, one hostile wisp, a rotating minimap, and local save/continue.

## Not implemented

This is not the full campaign in the original pitch. Five islands, additional biomes, the drowned cathedral and boss, NPCs/quests, the enemy roster and advanced AI, full crafting/economy, manual save slots, weather, audio, configurable settings, and measured long-session performance guarantees remain out of scope. The game file includes the same cut list; those features are not presented as working.

## Checks

JavaScript syntax and static structure pass. Runtime/browser play and performance are not yet verified; no FPS or memory-growth guarantee is claimed.
