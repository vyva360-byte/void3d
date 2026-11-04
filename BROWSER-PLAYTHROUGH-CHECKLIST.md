# Beaconfall: browser playthrough checklist

**Audience:** Victor or a tester validating the Keeper's Atlas in a real Chromium/Chrome browser with WebGL.

**Goal:** Prove the current PR build works as a player experiences it, including both reported regressions: the Gold Crown story must win its exact-coordinate tie with the harvest tree, and pause must work after opening and closing the victory ledger.

**Build under test:** Use the current PR #3 head. Record its commit SHA before starting. Do not test an older preview by accident.

## Test setup

- [ ] Open the exact PR #3 build in a Chromium/Chrome browser with WebGL enabled. **Pass:** the game's title screen appears; Three.js loads; no fatal overlay is shown.
- [ ] Use a separate temporary browser profile or isolated test profile. **Pass:** this run cannot overwrite or clear any existing Beaconfall save; do not clear storage in your regular profile.
- [ ] Open DevTools Console and keep it visible or recording. **Pass:** the console is ready to capture errors and warnings during the run.
- [ ] Record build SHA, browser/version, OS, viewport size, test date, and test profile. **Pass:** all five values are in the run record below.

## Playthrough

### Start, camera, and movement

- [ ] Select **Step ashore**. **Pass:** the Keeper, island, HUD, island atlas, and objective render; no uncaught console error appears.
- [ ] Drag to orbit the camera and use the wheel to zoom in, then out. **Pass:** camera angle and distance change smoothly; the Keeper stays in view.
- [ ] Turn the camera, then hold **W** briefly and release it. **Pass:** the Keeper moves forward relative to the new camera heading; position changes in the expected direction.
- [ ] Hold **A/D**, then **Shift** while moving, and press **Space** once. **Pass:** lateral movement, sprint stamina use, and a single jump work without a stuck key or unexpected pause.

### Three traces and choice persistence

Visit these in order so each later trace can show the prior choice as an echo: shipwreck, compass ruin, Gold Crown. Use the visible shipwreck on the southwest shore, the broken arch west of center, and the gold-leaf tree east of center; do not assume the atlas marks story sites.

- [ ] Approach the shipwreck and press **E** at its prompt. **Pass:** the Wreck story dialog opens with three choices; the selected response and its reward match the displayed option.
- [ ] Choose one Wreck response. **Pass:** exactly one trace is recorded, the correct reward is added (boards: +2 driftwood; lens: +1 heartglass; leave standing: no material), and the Keeper's ledger reflects the choice.
- [ ] Approach the compass ruin and press **E**. **Pass:** the dialog opens, displays the Wreck choice's echo, and offers three distinct responses.
- [ ] Choose one Compass response. **Pass:** the selected reward matches (central lens: +1 heartglass; frame: +2 driftwood; let needles turn: no material), and the ledger records it.
- [ ] Approach the Gold Crown without harvesting its tree, then press **E** at the landmark. **Pass:** the prompt says **Read THE GOLD CROWN** and the Crown story dialog opens immediately; the tree remains visible and no tree harvest is recorded.
- [ ] Confirm the Crown dialog carries the Compass choice's echo, then choose one response. **Pass:** berries grants +3 berries, write grants +1 heartglass, or blank grants no material; the third trace is recorded.
- [ ] Open the ledger with **J**. **Pass:** it shows all three choices and receipts, reports 3 of 3 traces, and says it is a record, not a score. No morality score or preferred answer appears.

### Beacon gate, gathering, and provisions

- [ ] Before recording all three traces, approach the beacon and press **E**. **Pass:** a clear message says all three traces are required; the beacon stays dark and resources are unchanged.
- [ ] After all traces, gather driftwood and heartglass from ordinary harvest nodes. **Pass:** each node disappears once harvested, the matching inventory count increases, and the objective updates.
- [ ] If testing the full lantern-plus-beacon loop, collect at least 6 driftwood and 4 heartglass total before spending: 2 driftwood + 1 heartglass for the lantern, then 4 driftwood + 3 heartglass for the beacon. **Pass:** the satchel and objective show the exact remaining amounts.
- [ ] Pick berries from a bush and open the satchel with **I**. **Pass:** berry count rises by 3; eating one consumes exactly one berry and increases hunger by 35, capped at 100.
- [ ] Craft the lantern from the satchel. **Pass:** 2 driftwood and 1 heartglass are consumed, the lantern appears equipped and lit, and its fuel timer is visible.
- [ ] Lower and raise the lantern, then refuel it if needed. **Pass:** equipped state toggles correctly, fuel decreases while lit, and refueling consumes 2 driftwood and resets fuel.

### Night, wisps, and combat

- [ ] Let the game clock reach **THE LONG DARK** (the day/night cycle is about 190 seconds; night begins after roughly 118 seconds). **Pass:** night lighting appears and wisps spawn and pursue the Keeper outside a safe light radius.
- [ ] Equip and raise a fueled lantern near a wisp. **Pass:** the wisp retreats within lantern range; it resumes approaching outside that range.
- [ ] Face a wisp and strike it until defeated. **Pass:** the wisp disappears, its reward is added once, and its dead entry is removed from the live encounter list.
- [ ] Check the island atlas while moving and turning. **Pass:** player heading stays at the top of the heading-up map and visible wisp markers rotate consistently with the map.

### Ending, pause recovery, and Continue

- [ ] After all three traces and the required materials, approach the beacon and press **E**. **Pass:** materials are consumed once, the beacon lights, and the victory reading reflects the choices without scoring them.
- [ ] Select **Read the ledger** from the victory screen. **Pass:** the Keeper's ledger opens and retains all three choices.
- [ ] Close the ledger, then press **P** or **Escape**. **Pass:** the pause menu opens. This is the regression check for the ending-state bug.
- [ ] Resume, save and return to title, then select **Continue journey** in the same test profile. **Pass:** the beacon, story choices, harvested nodes, and remaining berries/materials restore; already-recorded traces do not reopen as new encounters. Record remaining lantern fuel as an observation if a lantern was made; do not treat equipped/stowed state as a save requirement.
- [ ] Start a new run through the intended replay/new-journey flow. **Pass:** the previous scene stops rendering, the new run starts at the title's new seed/state, and no repeated-run console error appears.

## Done criteria

- [ ] Every required step above is PASS, or is explicitly marked BLOCKED with a reason and evidence.
- [ ] Both regression checks pass: the Crown story opens without chopping the tree, and pause works after closing the victory ledger.
- [ ] The Console has zero uncaught errors during the playthrough. Record any non-fatal warnings separately; do not silently call them clean.
- [ ] Attach evidence for the Crown prompt/dialog, beacon gate, victory ledger then pause menu, Continue-restored state, and the Console result.
- [ ] Leave PR #3 in draft until the tester records the result and Victor decides whether to mark it ready. This checklist does not authorize merge or deployment.

## Failure handling

- **Crown opens harvest instead of story:** mark FAIL, record the exact prompt and position, capture a screenshot, and stop the acceptance run.
- **Pause does not open after closing the victory ledger:** mark FAIL, capture the ending/ledger/pause sequence, and stop the acceptance run.
- **Three.js/WebGL fails to initialize:** mark BLOCKED, record browser/GPU details and Console output, then retry only in a supported browser/profile; do not mislabel it a gameplay pass.
- **Save/Continue changes or loses an existing save:** stop immediately; do not clear or overwrite more browser storage. Use only the isolated test profile for further checks.
- **Any other mismatch:** record steps to reproduce, expected versus actual result, browser, commit SHA, and screenshot/console evidence. Keep the PR draft.

## Run record

- Result: NOT RUN / PASS / FAIL / BLOCKED
- Commit SHA:
- Browser and version:
- OS / GPU:
- Viewport:
- Test date:
- Tester:
- Console errors and warnings:
- Evidence links/files:
- Failed or blocked checklist items:
- Follow-up issue or PR:
