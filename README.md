# Beaconfall · The Keeper's Atlas

Third-person survival slice on a storybook island. The Keeper is visible, the camera follows and orbits, and the gather → prepare → relight loop remains central.

## Play

Open `index.html` in a modern browser with an internet connection. Three.js loads from jsDelivr; all game art is procedural.

- **WASD** move relative to camera · **Drag** orbit · **Wheel** zoom
- **Shift** run · **Space** hop · **E** gather/use · **Click** strike
- **I** satchel · **Esc or P** pause
- Gather **4 driftwood + 3 heartglass** to wake the beacon. Pick wild berries with E and eat them from the satchel to restore hunger.
- Island seed reproduces the same coast; Continue restores gathered nodes and inventory.

## Issue disposition

- **Food lockout: fixed.** Berry bushes provide finite food nodes; the satchel consumes berries to restore hunger. Harvested bushes persist across Continue.
- **GPU leak on replay: fixed.** Replay disposes unique scene geometries, materials, textures, shadow maps, renderer lists, and the renderer.
- **Three.js r160 UMD: deferred.** The no-build single-HTML classic-script loader remains pinned and functional. Migration needs a deliberate ESM/import-map change plus browser/CDN validation; it is not claimed as fixed.
- **Torch safety: implemented, WebGL validation pending.** A fueled, equipped hand lantern repels wisps inside its radius; beacon protection remains broader.
- **Dead wisps: implemented, WebGL validation pending.** Killed-wisp resources are disposed and dead instances are pruned from the live array.
- **Minimap heading: implemented, WebGL validation pending.** Terrain and markers rotate together with player heading; the label reflects heading-up behavior.

## Verification

The inline script passes `node --check`. Local logic regression checks pass for camera orbit, camera-relative movement, zoom, pause fallback, berry harvest, hunger restoration, berry persistence through Continue, and replay renderer/scene disposal, with no JavaScript errors in the harness. This harness uses a Three.js test double and is not a WebGL pass.

**Keep this PR draft until a real-browser WebGL playthrough verifies** the third-person camera feel, lantern repel, minimap orientation, gathering/crafting, pause/save/Continue, and beacon/victory flow. One island, one beacon, one wisp archetype. Multi-island campaign, boss, NPC questlines, advanced navigation, weather, full economy, manual save slots, UMD-to-ESM migration, and long-session performance guarantees remain out of scope.
