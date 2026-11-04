# Beaconfall · The Keeper's Atlas

Third-person survival slice on a storybook island. The Keeper is visible, the camera follows and orbits, and the gather → prepare → relight loop stays central.

## Play

Open `index.html` in a modern browser with an internet connection. Three.js loads from jsDelivr; all game art is procedural.

- **WASD** move relative to camera · **Drag** orbit · **Wheel** zoom
- **Shift** run · **Space** hop · **E** gather/use · **Click** strike
- **I** satchel · **J** Keeper's ledger · **Esc or P** pause
- Read three traces at the wreck, compass ruin, and Gold Crown. Each choice gives a different practical reward, persists in the ledger, and contributes to the closing reading. There is no morality score.
- After all three traces, gather **4 driftwood + 3 heartglass** to wake the beacon. Pick and eat wild berries to restore hunger.
- Use [BROWSER-PLAYTHROUGH-CHECKLIST.md](BROWSER-PLAYTHROUGH-CHECKLIST.md) for the repeatable real-WebGL acceptance run.

## Save compatibility

Continue restores saves from this build. Saves under the earlier `void3d.slice.save` key are intentionally **not migrated** and are ignored; start a fresh journey on this build. The previous saves are abandoned, not converted.

## Issue disposition

- **Food lockout: fixed.** Finite berry bushes restore hunger; harvests persist through Continue.
- **GPU leak on replay: fixed.** Replay disposes unique scene geometries, materials, textures, shadow maps, renderer lists, and renderer.
- **Three.js r160 UMD: deferred.** The no-build single-HTML classic-script loader remains pinned. ESM/import-map migration is a separate change requiring browser/CDN validation.
- **Lantern repel: verified in real WebGL.** A fueled, equipped hand lantern repels wisps within its radius; beacon protection covers a wider area.
- **Dead-wisp cleanup: verified in real WebGL.** Killed wisps are disposed and removed from the live list.
- **Heading-up minimap: implemented.** Terrain and markers rotate together with player heading.
- **Crown trace target: fixed.** Story sites are prioritized before harvest nodes when the interaction distance ties, so the Gold Crown's story opens without chopping it.
- **Victory-ledger pause: fixed.** Opening the ledger from the victory screen clears the ending state, so pause works after the ledger is closed.

## Verification

Victor's real-WebGL playthrough reported zero console errors and verified the third-person Keeper and camera, camera-relative movement, all three story dialogs and rewards, cross-site echoes, the three-trace beacon gate, beacon lighting, victory and the ledger's “a record, not a score” wording, berry gather/eat, lantern craft/equip/fuel, night shade spawn/chase, lantern repel, kill pruning, and Continue restoring story choices, harvests, and berries.

Follow-up regression checks on the current build verify Crown wins target selection over the colocated golden harvest tree, the victory-ledger handler resets both `ending` and `paused`, pause can open after closing the ledger, and the inline game script parses. The fixes do not change the already-tested WebGL gameplay path.

One island, one beacon, one wisp archetype. Multi-island campaign, boss, NPC questlines, advanced enemy navigation, weather, full economy, manual save slots, UMD-to-ESM migration, and long-session performance guarantees remain out of scope.
