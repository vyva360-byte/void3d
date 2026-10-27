# void3d
You are a senior game engineer shipping a complete commercial-quality game. No explanations, no apologies, no plan documents, no preamble. Deliver ONE playable game file.
CONCEPT: BEACONFALL. You are the last Keeper, shipwrecked on a procedurally generated archipelago of 5 islands. A living dark called the Gloom spreads every night from the drowned cathedral at the map's heart. By day you explore, gather, craft, trade, and quest. By night you survive: the Gloom hunts, beacons you have relit push it back, and unlit ground is lethal. Win the game: relight all 5 island beacons, then enter the cathedral and destroy the Gloomheart. Lose the game: death. Death respawns you at your last lit beacon, drops your carried resources at your corpse as a recoverable cache, and costs 10 percent of your gold. At least 60 minutes of unique gameplay from first spawn to victory. Three difficulty presets (Story, Keeper, Nightmare) that genuinely change enemy damage, spawn rates, and survival drain, not just a label. Nothing inside the game may mention that it is a test, an experiment, or who built it. The game presents itself as a game, nothing else.
TECH, NON-NEGOTIABLE:
ONE self-contained .html file. It opens by double-click in any modern browser. No build step, no server, no install, no other files.
Three.js via CDN for the 3D world. Everything else is hand-written in the same file. No other frameworks.
ZERO external assets. No downloaded models, textures, images, fonts, or audio files. All visuals are procedural: geometry, canvas-generated textures, vertex colors. All audio is synthesized with WebAudio. No audio files.
NO placeholders anywhere. No "coming soon," no dead buttons, no lorem ipsum, no fake numbers, no simulated activity presented as real. Every number on screen is computed by a live system.
Zero console errors from menu to victory.
If you cannot implement a listed system, do NOT fake it: list it in a CUT LIST comment at the top of the file and leave it out of the game entirely. A short honest game beats a large fake one.
THE 3D WORLD:
Procedural archipelago: 5 islands, each a distinct biome: pine forest, desert dunes, volcanic rock, marsh, frozen shore. Beaches, cliffs, and at least one explorable ruin per island.
Terrain with real height variation, water you can swim in, and collision everywhere: the player cannot walk through terrain, trees, rocks, walls, or the seafloor.
Day/night cycle, roughly 10 minutes of day and 4 minutes of night, with a visible sun and moon.
Dynamic weather: clear, rain, fog, storm. Weather changes visibility, movement speed, and enemy aggression, and it is driven by a live system, not a timer that ignores gameplay.
A drowned cathedral at the map's heart, sealed until all 5 beacons are lit. Villages with NPCs on at least 2 islands.
Draw distance and fog that make the world feel large, not a small arena.
THE PLAYER (first-person):
Controls: WASD move, mouse look with pointer lock, sprint on stamina, jump, crouch, swim, dodge roll with invulnerability frames, interact with E, attack with click, block with right mouse and a parry timing window.
Stats: health, stamina, hunger, thirst, warmth. The frozen shore drains warmth; fire and cooked food restore it. Hunger and thirst drain over time and bite into health when empty.
Progression: XP from quests, kills, and discovery. 10 levels. Skill points. A 2D skill tree screen with 3 branches (Keeper, Combat, Survival) and at least 9 unlockable skills that actually change mechanics, not just numbers on a card.
COMBAT AND ENEMIES:
Melee weapons (crafted sword, spear) and a ranged bow with real arrow drop and crafted arrows.
At least 5 enemy types with distinct behavior: Gloom wisps (fast, weak), husks (melee), spitters (ranged), brutes (heavy, slow), and the Gloomheart boss with 3 phases and telegraphed attacks.
Enemy AI with perception: a sight cone and a hearing radius. States: patrol, investigate, chase, attack, retreat. Enemies navigate around obstacles instead of walking through walls.
Night increases spawn rate and aggression. Lit-beacon radius repels and weakens Gloom enemies. This must be a real radius check, not a visual effect.
Damage numbers, hit flash, knockback, death drops, a boss health bar, and a boss intro banner.
NPCS, QUESTS, DIALOGUE:
At least 6 named NPCs with roles and daily schedules: they move between home, work, and market by time of day, and the player can find them where the schedule says they are.
Branching dialogue trees in a 2D interface. Choices matter: at least 3 quests with mutually exclusive outcomes that change later dialogue and rewards.
A main quest line (5 beacons plus the cathedral) and at least 8 side quests across fetch, hunt, delivery, discovery, and puzzle types.
A quest log with active objectives, world markers, and a compass. Completing a quest updates the log and pays gold and XP through a live transaction, not a scripted popup.
At least 2 traders with buy/sell screens, real gold balances, and a reputation discount earned by finishing their quests.
CRAFTING, INVENTORY, SURVIVAL:
A 2D inventory grid with a weight limit and equipment slots for weapon, torch, and armor.
Gathering: chop trees, mine rocks, pick herbs, and a fishing minigame with a timed bar.
At least 15 crafting recipes in a 2D crafting screen across tools, weapons, armor, food, torches, potions, and beacon fuel.
Campfires: cooking turns raw food into cooked food with better hunger value, resting saves the game, and campfire light is a safe radius the Gloom cannot enter.
Torches: a real light radius at night that burns fuel down and must be crafted and refueled.
THE 2D SYSTEMS:
HUD: health, stamina, hunger, thirst, and warmth bars, gold, XP bar, buff and debuff icons, damage vignette, low-health pulse, compass strip, and an objective tracker.
A live 2D minimap canvas that rotates with the player, and a fullscreen map with fog of war that reveals only where the player has actually been.
Inventory, crafting, skill tree, dialogue, quest log, and trader screens: all 2D, navigable by mouse and keyboard. Esc pauses everything, including enemies.
Main menu (New Game, Continue, How to Play, Settings), pause menu, death screen, victory screen with time and stats, and credits.
Settings that really work: graphics quality (Low, Medium, High, Ultra) that changes draw distance and pixel ratio, mouse sensitivity, FOV slider, and separate music and SFX volume sliders. Settings persist after reload.
Enemy versus friendly markers use shape as well as color, never color alone.
AUDIO, ALL SYNTHESIZED:
Adaptive procedural music: a calm exploration layer, a tension layer at night, and a combat layer in fights, crossfaded by live game state, generated with WebAudio oscillators.
Synthesized sound effects: footsteps that change by surface, swings, hits, bow release, pickups, crafting, dialogue blips, the beacon relight sting, the boss roar, and UI clicks. Mute and volume controls that work.
SAVE AND LOAD:
localStorage: 3 manual slots plus autosave on every beacon relight and every campfire rest. Continue loads the latest save.
A save holds position, stats, inventory, quest states, beacon states, and the world seed. The same seed generates the same world across loads, and the seed is shown on the save file. New Game generates a fresh seed, and the player may type in a seed.
PERFORMANCE AND ROBUSTNESS:
60 frames per second target on a mid-range laptop at Medium quality. An automatic quality scaler drops pixel ratio if frame rate stays below 45 for 5 seconds.
No memory growth over a 30-minute session. No per-frame allocations in hot loops where avoidable.
Keyboard and mouse only. All text legible at 1080p.
ACCEPTANCE. Verify every one of these yourself before delivering, and fix failures. Do not ship a list of known failures outside the CUT LIST:
New Game spawns the player on a beach. The player can move, look, jump, and swim without falling through the world.
Chopping a tree puts wood in the inventory. Crafting a torch and equipping it produces a real light radius at night.
Night falls, Gloom spawns increase, unlit ground is dangerous, and lit-beacon radius is safe. All four are observable in play, not asserted in text.
Talking to an NPC opens a branching dialogue, accepting a quest creates a marker, and completing it updates the log and pays gold and XP.
Each enemy type can be killed, drops loot, and pays XP. The boss fight has 3 phases and a victory sequence.
Relighting all 5 beacons opens the cathedral. Defeating the Gloomheart shows the victory screen with time and stats.
Save, close the browser, reopen, Continue: same world, same inventory, same quest state.
Changing quality, sensitivity, or volume in Settings takes effect immediately and persists after reload.
Thirty minutes of continuous play: no crash, no runaway memory, frame rate holds or the scaler engages.
Zero console errors from menu to victory.
DELIVERY: Output ONLY the complete .html file. No preamble, no explanation, no summary after it. If the file exceeds your output limit, deliver it in sequential parts labeled PART 1 of N, PART 2 of N, and so on, with no summaries between parts.
