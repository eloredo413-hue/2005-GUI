# Sources for the 2005 Studio (create mode) accuracy pass

No build of the 2005 Roblox client is known to survive, so every change in `05 ui` was checked against
the best surviving evidence: the original 2005 Toolbox model files, a recreation of the October 2005
client whose interface was measured from period screenshots, and community research into the early
clients. This file lists each source and what it was used for.

## Sources

| # | Source | What it is |
|---|--------|------------|
| 1 | [Phelpzio/ToolboxModels](https://github.com/Phelpzio/ToolboxModels) | The original XML of 52 of the 2004-05 Toolbox models (asset IDs 770-864), re-uploaded by the `Toolbox` account between May 10 and May 13, 2005. Collected by Old ROBLOX Client Search. |
| 2 | [KeyboardCombination/Blocks3D](https://github.com/KeyboardCombination/Blocks3D) (formerly RBX05R) | A recreation of the client "as it stood in October 2005 with the 'Morgan McGuire builds'". Its README credits McGuire's pre-2006 website for "the only existing colour pictures of 2005 era roblox". It contains the original client textures and the toolbox pages (`content/page/*.html`). |
| 3 | [On the Origin of Roblox's Rendering](https://clientsearch.tumblr.com/post/173388510468/on-the-origin-of-robloxs-rendering) (Old ROBLOX Client Search) | Explains that McGuire's 3 colour screenshots let the recreation take "pixel-perfect measurements of the original UI", alongside 18 black and white screenshots from the original patent. |
| 4 | [History of Roblox, 2003-2006](https://clientsearch.tumblr.com/post/179286351133/history-of-roblox-2003-2006) ([mirror](https://robloxopolis.com/archives/history-of-roblox-2003-2006/)) | Timeline of the early builds: menus, left panel, camera cluster, toolbox, surfaces and HopperBins. |
| 5 | [Controllers: an in-depth examination](https://clientsearch.tumblr.com/post/169442434723/controllers-an-in-depth-examination) ([mirror](https://robloxopolis.com/archives/controllers-an-in-depth-examination/)) | How ControllerSchemes worked: key sets, Chase / Flee, flag and motor-ring colours. |
| 6 | [Roblox Wiki: Toolbox (user)](https://roblox.fandom.com/wiki/Player:Toolbox) | Upload dates of the 2005 models; the chassis was driven with the arrow keys in 2005. |
| 7 | [Legacy Roblox Wiki: Studio](https://rbxlegacy.wiki/index.php/Studio) | `Format > Set Model Front` and how it pointed the controller flag. |
| 8 | [US 2006/0258447 A1, "Online building toy"](https://patents.google.com/patent/US20060258447A1/en), filed May 11, 2005 | Roblox's own description of the builder; models get a controller (keyboard, joypad or AI). |
| 9 | [Roblox Creator Docs: HopperBin](https://create.roblox.com/docs/reference/engine/classes/HopperBin) | `BinType` values `GameTool`, `Grab`, `Clone` and `Hammer` (plus `Script`, added later). |

## What changed, and why

### Layout (source 2, checked against 3 and 4)
- **Menus:** the menus are File, Edit, View, Insert and Format, each 125 px wide and starting at the left edge. Titles are white 16 px text with a grey outline. The "Run" menu was removed because source 4 lists *"Run" menu removed* for the October 2005 builds.
- **Left panel:** an 80 x 330 translucent grey (153,153,153 at 40% opacity) panel holding, top to bottom:
  - GO / STOP (65 x 65)
  - Drag (50 x 50)
  - Resize + Axis Drag (40 x 40)
  - Rotate + Tilt (30 x 30)
  - a divider
  - Group, UnGroup and Duplicate as cyan 12 px text, greyed out when they can't apply
  - Delete (40 x 46)
  - MENU

  This matches the tool list in source 4: *Go, Drag, Axis Drag, Resize, Rotate, Tilt, Group, Ungroup, Duplicate, Delete*. The **Velocity** and **Selection Up / Down** buttons were removed because neither source puts them on the 2005 panel.
- **Toolbox tabs:** Model, Surface, Color, Controller and Hopper, each 80 x 24 with cyan text, sitting above a **60 px** toolbox strip. The strip uses Windows XP ButtonFace (236,233,216) with an outset border.
- **CameraMenu:** a 120 x 117 box. The original texture names show that the **big white arrows are CameraZoomIn / CameraZoomOut** and the **small circled arrows are CameraTiltUp / CameraTiltDown**. The old script had these two pairs swapped. Steps follow the recreation:
  - zoom moves 1/5 of the distance per click
  - pan steps to the next 45 degree heading
  - tilt moves 25 degrees
  - Center focuses on the selection
- **Timer / Score:** 20 px text in 0x81C518 (129,197,24) with a black outline, at (screen width - 120, 25) and (screen width - 120, 50).
- **FPS:** small yellow "FPS: 30.000" text at (120, 25).
- **Win / lose message:** a translucent 0xB2B2B2 box in the middle of the view, (screen width / 2 + 100) wide and a third as tall, with white text.
- **Selection and handles:** the selection outline is cyan, Axis Drag arrows are G3D orange (255,128,0), and Resize handles are cyan.

### Toolbox pages (source 2 `content/page/*.html`, data from source 1)
- **Surface:** Flat, Bump, Hinge and four Motor tools (left/right, slow/fast). A tool changes **only the face you click**, as in the recreation's SurfaceTool. Glue and Weld were removed; source 4 says Glue later *superseded* Bumps, and in the 2005 files the surface types are only Smooth / Bumps with Hinge / Motor / SteppingMotor constraints.
- **Color:** colours were plain RGB in 2005 (the model files store `Color3`, not BrickColor). The page copies a screenshot of the original 2005 Color page that the repo owner supplied: 20 colours in two rows of 10, each a 20 x 20 sunken swatch 4 px apart, with no current-colour well. This replaces the later BrickColor swatches. The colour values and sizes were measured from that screenshot. Blocks3D's `color.html` uses the stock Windows colour-dialog palette instead, which is a placeholder and not what the 2005 client showed.
- **Controller:** arrow keys (blue flag), W/A/S/D (red flag), Chase, Flee and None. The made-up "Player 2" scheme was removed.
- **Hopper:** the HopperBin commands a level could hand out (source 4: *Clone, Grab, and Hammer*; source 9 adds GameTool). These replace the figure-spawn buttons, which were not HopperBins.

### Model data (source 1)
- Removed the invented "Kill Brick" (865) and "Win Brick" (866). The real 2005 items are 859 *Lose Game Beacon* and 860 *Win Game Beacon*.
- Models now arrive with their real controller: vehicles and robots use KeyboardRight, the bugs use Chase / Flee, 863 Blue figure uses KeyboardRight and 864 Red Figure uses KeyboardLeft. In 781, 782 and 827 it is the motor parts themselves that carry KeyboardRight. Flags are hidden on the two figures (`ControllerFlagShown = false`).
- `NameShown` labels: "100 Points" and "5 sec". The Win / Lose Game Beacons are left unlabelled.
- OnTouch sounds: Ping, Clock, Boing and Victory. OnTouch is `SingleShot`, so it fires once per run.
- Figure colours are pure RGB red (255,0,0) and blue (0,0,255), not the later BrickColor values.

### Behaviour (sources 2, 4, 5)
- **Key sets:** KeyboardLeft = W/A/S/D and KeyboardRight = arrow keys. Previously every controller answered both. Player answers either key set; Joypad1 / 2 do nothing.
- **Movement:** controllers drive motors, and only the PhysicalCharacter figures walk by themselves.
- **Chase / Flee:** they turn toward or away from the nearest model with a different controller.
- **Set Model Front:** added to the Format menu. Driving and Chase / Flee use the front it sets.
- **Rotate / Tilt** turn the selection by 90 degrees (Tilt about the Z axis). **Duplicate** drops the copy on top of the original.
- **No timer tick:** the countdown does not tick each second.
- **Level properties:** with nothing selected, Properties shows the 2005 Level settings: WinMessage, LoseMessage, HighScoreIsGood, InitialTimerValue (0 = no limit), InitialScoreValue, TimerUpAction and TimerAffectsScore. Win, lose and timer-up stop the run and show the message.

### Bugs fixed along the way
- **View menu crashes:** "Main Menu" referenced an undefined `LeftFloatingPanel`, and "Toolbox" / "Color Menu" referenced `BottomBar`, which was out of scope. All three raised `attempt to index nil`.
- **Edit menu:** "Group" called `GroupBtn.MouseButton1Click:Wait()`, which yields until the next click instead of grouping. "Ungroup" did nothing.
- **2006 font never applied to game text:** the font section indexed an out-of-scope `fontStates`, so the conversion threw inside `pcall` every time.
- **Sprite crash:** `applySpriteToImage` indexed a nil sprite entry for sprites that exist only as cloud IDs.
- **Single parts couldn't trigger OnTouch:** a standalone part directly in the spawned-models folder could never trigger a beacon.
- **"Flat" didn't stick:** making a face Flat left the stud texture behind, and the 3D bump pool rebuilt the bumps.
- **Figure floated:** your 2005 figure was placed at your avatar's height plus a lift, so it hovered in edit mode. It now stands on whatever is under you.
- **Invisible thing in the way:** your real avatar is hidden, but it still blocked the figure (Humanoids turn Torso / Head collision back on every physics step) and the Drag tool could grab it. It is now non-solid on every step and clicks pass straight through it. It also stays parked during GO instead of falling out of the world and respawning.
- **GO froze in 3D stud mode:** every frame, each 3D bump on a moving part was moved by setting its CFrame. Because bumps are welded to their part, that teleported the whole model once per bump, and a model with hundreds of bumps froze the game. Welded bumps now just ride along with physics.
- **ForceField and particles:** the spawn ForceField bubble, particle emitters, sparkles, fire, smoke and explosion blasts are hidden on your screen, since 2005 had none of them (setting `HIDE_FORCEFIELDS_AND_PARTICLES`).
- **Dead View items:** the CameraMenu, Controllers and Camera/TrackView items referenced fields that were never set.

## Still unverified
- **Model categories:** the toolbox model categories (Blocks / Vehicles / ...) have no 2005 source; the closest is the 2006+ toolbox, which used "Bricks" and "Robots".
- **Edit and View menus:** these items aren't documented for 2005. They only use commands the 2005 client had, from the left panel and the panels themselves.
- **Postures:** Stand / Sit / Climb come from the RBLX04 recreation. Only `PostureXML = Stand` appears in the 2005 files.
- **Exact palette values:** the 20 colours were sampled from a compressed screenshot, so each channel may be off by a few points.
- **Motor speeds:** the speeds of the four Motor tools are a guess, because the recreation does not implement them.

## Art
Most of the button art is the original Roblox client art the script already embedded. The second sprite sheet (Surface tools, CameraMenu hover/press states, the ScaleTool states for Resize, and the HopperBin icons) packs more of those original textures, taken from source 2's `content/images` folder.
