# VOID3D: Beaconfall

A single-file, first-person survival slice on one procedural pine coast. Gather timber and emberstone, make a torch, and relight the old beacon before night takes the shore.

## Play

Open `index.html` in a modern browser with an internet connection. Three.js loads from jsDelivr.

- **WASD** move · **Mouse** look · **Shift** sprint · **Space** jump
- **E** gather/use · **Click** strike · **I** pack · **Esc or P** pause
- Gather **4 timber + 3 emberstone** to relight the beacon.
- Enter a seed to regenerate the same coast. Progress autosaves locally; **Continue** restores gathered resources.

## Verified

Victor played the loop in Chromium with real WebGL: gathering, torch craft, beacon relight, wisp combat and reward, night damage/spawns, pause and save/Continue, with zero console errors. The recent fix pass also tested movement after a camera turn, Esc/pointer-lock pause, collected-resource persistence, victory return-to-title and starting a new run. Buildkite build #7 passed.

## Known limits

No food restoration/source, no full campaign or extra biomes, and no measured long-session performance guarantee. Repeated-run GPU cleanup and upgrading from Three.js r160 UMD remain follow-up work. Wisps are not repelled by the hand torch, dead wisp entries remain in the array, and the minimap still needs a direction check. The in-game CUT LIST is the authority on excluded systems.