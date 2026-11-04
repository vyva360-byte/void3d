# Beaconfall · The Keeper's Atlas

Third-person, single-file survival slice on a storybook island. The keeper is on screen; the camera follows and orbits. The gather → prepare → relight loop is intact.

## Play

Open `index.html` in a modern browser with an internet connection. Three.js loads from jsDelivr; the island, keeper, signal tower, wisp, and action tones are procedural.

- **WASD** move · **Drag** orbit · **Wheel** zoom · **Shift** run · **Space** hop
- **E** gather/use · **Click** strike · **I** satchel · **Esc** pause
- Gather **4 driftwood + 3 heartglass** to wake the beacon.
- Enter an island seed to recreate the same coast. Progress autosaves locally; Continue restores the latest run.

## What's in the upgrade

A third-person keeper with animated stride, weather cape, lantern and blade; a floating-atlas coast with a shipwreck, broken compass ruin, gold-leaf landmark tree and monumental signal tower; day/night color and survival pressure; resource gathering, lantern crafting, one hostile wisp, a safe beacon radius, minimap, pause and local save/Continue.

## Scope and verification

One island, one beacon objective, one wisp archetype. No full campaign, boss, NPC questlines, advanced enemy navigation, weather, complete economy, manual save slots, or measured performance guarantees. Those cuts are stated in the game.

Verified: `node --check` on the inline script; a Chromium logic smoke test with a Three.js API test double covered start, third-person state, movement, heartglass collection, pause/save/Continue, and opening the satchel with no JavaScript errors. Actual Three.js rendering and representative-device performance still need a network-enabled browser pass.
