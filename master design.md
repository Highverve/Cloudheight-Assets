### Summary

Cloudheight, as I'm codenaming this project, is an exploration-focused, 2D action game.

### Gameplay Loop

Exploration.

Combat.

Story?

---

### World Layout

The game is separated into two primary worlds: the **sky world**, the **lower world**.

The sky world is a vast collection of floating islands—both small and large. The lower world is an interconnected province of varios biomes.

Both worlds have hand-crafted levels, of both larger hubs and smaller locales. These hubs are connected together via procedurally generated levels. They use a visual hexagonal tile map which will be modifiable in devtools to reduce art demand when a new visitable node is added or biome changed. The maps have a fog of war effect, allowing only visited locations to be visible. The fog of war effect is split, meaning visiting a corresponding map node in the sky world will not remove the fog in the lower world. The maps are predominantly for reference. Far off locations and quest objectives are charted towards with the spyglass tool (more on this design later).

There is a direct correspondence with the sky node above and the lower node below. If a player falls off the sky world map, they will land at the lower world node directly below it. This allows for unique interactions, such as a two-phase mini-boss, where phase one takes place on a node above, is knocked off the island by the player, giving a small reward, then the node directly below it is the battleground for the mini-boss's second phase.

The lower world scrolls across the sky gradually as the day and night progresses. Some lower world nodes may only be accessible by falling at a certain time and location!

The procedural nodes will save their map state until global reset has occurred. The global reset is a weekly event which regenerates each procedural node, effectively shifting the landscape below, allowing for new enemies, loot, and challenges to be taken on.

One in-game 24-hour cycle is equal to a half hour real-time, which gives the player 3 ½ hours to explore the lower world before reset.

Planned biomes include a forest/plains region, desert/volcano region, mountain/snow region, and marsh/fungal. Each generated node can have different premade structures, such as abandoned houses.

Throughout the world, the sky world and lower world are connected via "skytowers". Each region/biome has a unique skytower with different puzzles, enemy designs, and bosses. These are essentially many-floored dungeon towers. The skytowers are sealed off at the top, meaning the player must approach and enter from below, clear out the enemies, kill the boss, and unseal it at the top.

### World Navigation

Details about navigation progression go here.

If the player falls off an island, he crashes on a node in the lower world, landing on a pile of leaves or a haystack. To return to the sky world in the early game, the player must find and activate a portal. Ropes, bridges, ziplines, restricting the player to the nearby starting location. Hookshot, allowing the player to create their own ziplines, allowing access towards closer islands. The hookshot can be used if the player falls off the island to get back up. Glider, allowing the player to fly towards moderate islands under correct wind conditions. The Airship, which opens the skys up for the player, which should be an early-mid-game unlock.

While navigating between islands in the airship, random events may take place in a manner similar to Wind Waker. This will keep sky navigation interesting. Event possibilities could include pirate airship attacks, flocks of birds flying near the airship, a small uncharted island appearing with a chest, turbulent weather such as high winds, or a large travelling airship the player could dock his smaller airship at.

### Puzzles

Puzzle ideas go here.

Navigation puzzle. A subtle sign that suggests a time of day, indicating a node that can only be reached by falling at that sky island at that time of day.

Procedural world generation. A puzzle which lets the player set the random seed for the next global reset (the seed determines the exact layouts of the procedurally generated world, meaning the same seed will have the exact same layout). Other players could share this with each other.

---

### Combat

Enemy encounters ebb and flow between small encounters (where the enemy may require more thought to find a weakness), to medium encounters (such as taking out a goblin encampment), and large horde-like encounters (where swarms of enemies pour out and attempt to overwhelm the player with sheer number).

The player's combat actions are instantaneous. Enemy combat actions always show projection, which highlights the exact direction and reach their attacks will hit just a moment before execution. This gives the player time to react, with dodging, jumping, blocking, countering, stunning, potentially disarming, or knocking back. The projection timeframe will first show the area, and just before striking, the enemy will rapidly flash white multiple times before striking.

Dealing damage and receiving damage have hitstop frames (game world pauses very briefly, conveying big damage). See *Monster Hunter: World*.

The player can increase their maximum health by exploring the lower world and discovering health statues (work-in-progress).

Buffs/debuffs. Block 2 (blocks damage if it is 2 damage points or less), bleed (drains HP), disease (drains HP slowly, spreads between nearby enemies).

### Weapons

Weapons are unique, non-randomized, non-degradable items that are acquired in hand-picked locations throughout the game world. Specific weapons may be bought in a weapon shop in a certain town, or received as a drop from a boss, or hidden away in a chest behind a challenging puzzle. Each weapon class has specific, immutable characteristics which give the weapon enhanced definition and style. Here are the suggested weapon types. Weapons have no stamina cost to use, ranged weapons have infinite ammo, and magic has no mana cost. This incentivizes the player to *use* their weapons, and not dissuade them.

##### Melee Weapons

1. **Sword & Shield**. Average damage, shield blocks all damage in direction character faces (think *Zelda: Minish Cap*). Default starter weapon.

2. **Dual Daggers**. Small, faster damage. Bleed or disease damage.

3. **Spear**. Long reach, stabbing, vaulting (higher jump ability).

4. **Warhammer**. Slow, big damage, forward radial AoE, stuns enemies.

5. **Longsword**. Sweeping arc, knockback, counters attacks (enemy attacks are canceled with good timing).

6. **Fists**. Fast jabs, disarming can remove the enemy's weapon.

##### Ranged Weapons

1. **Shortbow**. Short distance, yet fast.

2. **Longbow**. Long distance, yet slow. Knocks down flying enemies.

3. **Crossbow**. Powerful, reload time, pierces multiple enemies.

4. **Revolver**. Six shooter, reload time, fast projectiles.

5. **Blunderbuss**. Stunning, bullet spread, reload time.

##### Magic Weapons

Work-in-progress.

##### Airship Weapons

1. **Iron-shot**. Average speed. Default weapon.

2. **Multi-shot**. Arc projectile.

3. **Cluster-shot**. Splinters on enemy hit, dealing damage to nearby enemies.

4. **Explosive shot**. Explodes on impact.

---

### Characters & Monsters

Enemy types, animal types, and character outlines go here. Ground-based and sky-based enemies. Ground-based enemies are non-flying enemies, while sky-based enemies are typically larger enemies encounters mid-flight, such as pirate airships. A ground-based enemy could include giant bats or vultures, which can fly, but are encountered when on land and are killed with melee or ranged weapons.

---

### Outfits

Outfits are upgradeable clothes and armors that give the player unique boosts.

### Tools

**Skyglass**. This primary navigation tool is a combination of a spyglass and compass, and is meant to mimick Wind Waker's spyglass in functionality. On use, a circular skyglass UI will display on-screen which shows the sky's horizon. Since our game uses a 2D top-down perspective, the Skyglass is a sideview style layout. At the bottom edge will be the parallax layer (clouds in the sky world, trees in the lower world), a shader-rendered sky gradient which will fade between sunrise/sunset/noon/night colors, moon/sun/stars/constellations, and most importantly for gameplay, nearby and distant landmarks. The distant landmarks will appear as silhouettes and will gradually gain color as the player approaches. At the bottom edge, in front of the parallax layer, will be the compass, which will show notches and NWSE direction markers.

**Watch**. The watch is an analog watch that shows the game-time using a dynamic hour/minute hand. On the edges are the seven days of the week, and the current day is highlighted. The last day of the week, Sunday at Midnight, is the day of global reset (name to-be-determined), which resets all lower world procedurally generated map nodes.

**Instrument** (type to-be-determined, possibly a Magic Flute). The instrument is a magical tool that the player can use to solve puzzles and has further world interaction capabilities, possibly with animals. See Animal Well's Flute implementation.

**Lingualizer**. Absorb languages. Enables communicating with lower species. Quest, combat and puzzle implications.

**Divining Rods**. Searches for items and object. Work-in-progress idea.

### Consumables

Potions are the primary method of healing and acquiring buffs. A wayback stone may be used when on the lower world to return to the last sky island visited. A permanent item may include a perk which allows the player to teleport to various visited locations.

---

### User Interfaces

The **Heads-Up Display** (HUD) will have multiple elements that appear and fade depending on its relevancy. The player will have an **health bar** below their character, which will show at all times if health is below 50%, and will show regardless when a combat encounter begins. There are also quick debuff/buff icons shown below the HP bar.

The player's **equipment/quickslots** display on the bottom left of the screen. The keybound swap button displays on each slot, and possibly the use button for consumables/tools (see **Controls**). Button hints should be toggleable in the options menu.

The player's **coins** and **perk XP** are displayed at the top-right corner, and is active only when collecting coins or experience after defeating enemies.

When in the airship, a wind indicator will appear.

During a boss or mini-boss fight, a boss bar will appear at the top of the screen. This will show the boss's name as well as its current buffs and debuffs.

The **Dialogue** interface shows dialogue interaction between the player and other characters centered at the bottom. It may include a higher resolution character portrait, or possibly just the character's low-resolution sprite.

The **World Map** opens to the player's current world (sky or lower world), and can be swapped between the two with **Cycle Tab Left/Right** (`L2` / `R2`, or `Q` / `E`). Both world maps are displayed as hexagonal tile grids, with unvisited locations being completely hidden (save for the hexagonal tile outline). Persistent locations (non-procedural) will keep their map data between world resets.

The **Inventory** has unlimited item slots with no weight or size limits. Certain items will have a maximum stack count, such as consumables items like food and potions. There are four tabs: Equipment, Tools, Consumables, Key Items. The player can swap between tabs with **Cycle Tab Left/Right** (`L2` / `R2`, or `Q` / `E`).

The equipped items and quickslots are to the left of the inventory slots. Equipment tab has two melee weapon slots, one ranged weapon slot, one outfit slot, and one vehicle slot (such as airships), and maybe a hat slot (lightweight on animation). Both the Tools tab and Consumables tab have five quickslots each.

The player's coin amount is displayed at the top-right of the Inventory (regardless of selected tab). Interaction options with controls display below the inventory slots.

The **Upgrades** interface shows perk trees for weapons, outfits, and vehicles. Perks are permanent upgrades that enhance existing equipment. When first opening the item page, the player's equipped items (shown by the tab name) can be cycled through with **Cycle Tab Left/Right** (`L2` / `R2`, or `Q` / `E`). Non-equipped item perk trees can be viewed by selecting the item in the inventory and pressing View Upgrades (Triangle/R), which will open the Upgrades page for that item directly. At first, the perk tree will show one unlocked perk at the bottom, with more perks cascading above it. Higher perks require lower perks in the tree to be unlocked first.

Here are a few example perks:

1. **Skyglass**. Focuser (unlocks zoom), Cosmic Knowledge (display constellations at night, puzzle implications).

2. **Plate Armor** (outfit). High Guard (always have Block 1—all enemy attacks that deal 1 damage are negated), Mobility (move faster in armor).

3. **Magic Flute**. Songbook (flute patterns can be memorized and replayed).

4. **Watch**. Passage of Time (quickly advance the time of day).

5. **Airship**. Coal Engine (faster speed, tighter turning), Fully Loaded (additional weapon slot).

The **System** interface allows the player to open sub-menus, which include: **options**, **save/load**, **main menu**, and **quit**.

All of these interfaces (with the exception of World-centric interfaces such as the HUD, dialogue interface, and tool-specific interfaces) exist in the same window under a primary tab bar. They can be cycled through with **Cycle Menu Left/Right** (`L1` / `R1`), or the keyboard keybinds, which have their corresponding **Open Map** (Tilde `~`), **Open Inventory** (`Tab`), **Open Upgrades** (`U`), **Open System** (`Escape`) keybinds. They are listed in this order: Map, Inventory, Upgrades, System.

---

### Controls

Controls should be abstracted away from input action (`Square`, `Cross`) to in-game action (`Use Tool`, `Jump`) to allow flexible player control between game states. `Cross` is both the **Jump** button in-game and the **Confirm** button in the UI, whereas **Jump** and **Confirm** defined in the game state are not. This allows the user to change keybinds of both Jump and Confirm rather than having the two permanently linked to the bound key.

The **Move Around** (`Left Stick`, `W` `A` `S` `D`) control is to used to move the player.

The **Zoom View** (`R3`, `Mouse Scroll`) button cycles between three zoom scales.

The **Look Ahead** (`Right Stick`, `Mouse`) control let's the player move the camera in the direction held.

The **Jump** (`Cross`, `Spacebar`) button causes the player to... jump.

The **Brace** (Hold `Cross`, hold `Spacebar`) causes the player to hold on to the ground, bracing himself against strong wind, explosions, or earthquakes. Subject to change or be removed.

The **Use Tool** (`Square`, `E`) button uses the player's equipped tool.

The **Interact** (`Square`, `E`) button uses a selected item when highlighted in the game world.

The **Sprint** (`Circle`, `Shift Key`) button causes the player to run when held. If tapped, it becomes a Dodge (`Circle`, `Shift`) button.

The **Use Food** (`Triangle`, `F`) button uses the player's equipped food/potion item.

The **Cycle Weapon** (`D-Pad Right`, `1`) button cycles through the player's equipped weapons. Two weapons may be equipped at a time.

The **Cycle Consumable** (`D-Pad Up`, `2`) button cycles through the player's equipped food/potion items. Five consumables may be equipped at a time.

The **Cycle Tool** (`D-Pad Left`, `3`) button cycles through the player's equipped tools. Three tools may be equipped at a time.

The **Whistle** (`D-Pad Down`, `4`) button calls the player's vehicle if unlocked (such as their airship).

The **Primary Weapon** (`R1`, `LMB`) button uses the player's equipped melee weapon.

Some weapons support a **Secondary Weapon** (`L1`, `MMB`) button, such as the sword and shield blocking with the shield when held.

The **Fire Ranged** (`R2`, `RMB`) button pulls up the aimer when held. Release the button to fire. Some weapons may require reloading, which can be done at any point with the **Reload** (`Square` while holding `R2`, `R`).

While in combat, the **Target Select** (`L2`, `Q`) button locks on to nearby enemies. Out of combat, cycles between interactable items close together.

The **Open Map** (`Select`, Tilde `~`) button opens the Map screen.

The **Open Inventory** (`Start`, `Tab`) button opens the Inventory screen.

The **Open Upgrades** (unassigned, `U`) button opens the Inventory screen.

The **Open System** (unassigned, `Escape`) button opens the Inventory screen.

Additional keybind options should be considered, such as Toggle HUD.

---

### Technical Details

World maps, map nodes, biome information, player information, quest and dialogue trees, and other such data will be saved in JSON. This also indirectly enables partial mod support. `Newtonsoft.JSON`.

The player class and viewport will be coded in such a way to make a later addition of two-player split-screen play possible. The viewport will require separate render targets of each layer (world, weather, UI, dynamic shader effects, etc.). The players can be in different nodes (levels) simultaneously and can be revived in non-boss encounters. Equipment (weapons, armor, and items) and quest progression are shared. Consumables, unlocked perks, experience, and coins aren't shared.

**GameStateManager** (distinguishes between main menu, game world, sub-states). `MainMenu`, `Loading`, `World`, `Paused`. `Stack<GameState>` with `Push`, `Pop`, and `Replace`. Similar to Flutter's `GoRouter`.

**LocalizationManager**. All text is written in an en-US.json file to enable multi-language support. `LoadLanguage(languageCode)`, `Get(key)` returns the value by key or the key itself for visibility, `Get(key, params)` which returns `string.Format(Get(key), args);`. Example: "coins_collected": "Found {0} coins" -> `localization.Get("coins_collected", 50)` -> "Found 50 coins".

Implement rich text layout design for improved text control (bold, italics, custom colors, animated text, typewriter effect). Example: `[bounce][c=#FF4444]Spyglass obtained![/c][/bounce]`.

**EventBus**. Greatly improves systems interactions efficiency and legibility, and makes mod support easier through event subscriptions.  `Subscribe`, `Unsubscribe`, `Publish`.

**DialogueManager**. `dialogueId` -> `nodes` -> `id` (start), `speaker`, `portrait`, `text`, `next` (player_response `id` with `type` (choices), `choices` -> `text`, `next`, `condition`).

**AssetManager**. Dictionaries of `textures`, `sounds`, `music`, and `shaders`. `GetTexture` loads fresh texture or existing texture if already loaded. `UnloadGroup` unloads all textures by group tag.

**Shaders**. All rendered entities and tiles/maps are sorted by their depth and drawn to world render target, in new Begin calls with the relevant shader. Multiple entities with the same status effect with a very close depth should be batched (calculated by a depth tolerance), essentially stacking/rendering in the correct order. Shaders on entities should be ordered by priority. Palette Quantizer shader (restricted colors to Endesga64 palette) applied to game world, except sky render target and UIs. Load the palette from a texture (allows simple color modding). Vignette. Disturbance map (receives input from moving entities, explosions, wind) which influences weather like rain and fog.

**Devtools**. `Debug overlay`, `Time/weather editor`, `Map/tile editor`, `Save/load system`, `Procedural generation tool`, `Entity inspector`.

FMOD Studio API for in-game audio management (audio effects such as reverb).

**Game clock**. `TimeOfDay` is a float between `0.0` and `1.0`. `DayCount`, `WeekDay` is `DayCount` modulo 7. The skyglass's sun angle is then simply `TimeOfDay * 360f`. Moon angle should move at a seventh the speed of the sun, so that it comes back to the same position for weekly reset. Moon phase changes based on the day.

**Tile Engine**. Auto-tiling, which makes tile map creation a seamless painting process, and aids procedural generated maps.

**Procedural Generation**. Earth Node Surface Maps (*Cellular Automata*), dungeons (Hybrid approach: *Binar Space Partitioning*, handcrafted rooms), spare sky islands (*Noise-based generation*)

---

### Technical Software

C# coding language with the MonoGame framework, HLSL shaders, JSON data, in Visual Studio 2026. Weakness: HLSL. I will have Claude do the heavy-lifting here.

Art assets are created with the ENDESGA64 palette in a low, 16x16 resolution. The small resolution directly addresses my biggest art weakness: spritesheet animating. At this low resolution, sprites are much easier to animate, which leads to lower psychological debt and greater incentive. I've experimented with and have confirmed this. Additionally, paired with the moderately restrictive 64-color palette, color consistency is enforced, which leads to stronger asset aesthetics, and less time fiddling with colors means faster art.

For more complex art assets, specifically animations, I have found Pixel Composer to be exceptional. I can design a workflow, add my sprite, tweak a few variables, and outfit consistent spritesheet animations, such as rotating sprites (coin animation), metallic highlght shines, explosions, weapon swoosh effects, and more. This is a large weight off of my animation time budget.

The sounds effects will be predominantly generated chiptune effects in BXFR. This is to match the artstyle it is in, and due to the ease of creating sound effects significantly outweighs attempting to record and edit my own foley, or the cost of using paid sound libraries, and the inconsistency between all sound libraries, paid or free. BXFR sounds may be run through FL Studio 25 to further refine the effect. Ambient tracks, such as forest noises, birds chirping, flowing rivers are still to be decided on how to create or find.

Music tracks will be made in FL Studio 25 using a few free VST software, specifically Vital and Splice Instrument. I intend to make the music more atmospheric, ambient and texturized, drawing inspiration from Caves of Qud and Animal Well, while some songs will be more melodic, akin to Hyper Light Drifter.
