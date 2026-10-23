# Additions to the original `05 ui`

`05 ui` is the original script with two additions:

## 2005 Surface tool icons
The Surface tab shows the real October 2005 Surface toolbox icons instead of plain text buttons:
- **Flat:** the crossed-out glue tube. Sets the top surface to Smooth.
- **Bump:** the glue tube. Sets the top surface to Studs (2005 "Bumps").
- **Hinge**
- **Motor Left, Motor Left Fast, Motor Right, Motor Right Fast:** each sets a Motor surface, and the speed is written to `TopParamB`.

The original **Glue** and **Weld** buttons are kept as text buttons, because 2005 had no icons for them. Each button still works the way the original's did: it applies to the selected object, and the Surface tool applies it to whatever you click.

The icons are the original 2005 client textures (`FlatTool`, `BumpTool`, `HingeTool`, `LeftMotorTool`, `LeftMotorFastTool`, `RightMotorTool`, `RightMotorFastTool` and their `_dn` pressed states). They come from [KeyboardCombination/Blocks3D](https://github.com/KeyboardCombination/Blocks3D) (GPL-2.0), a recreation of the October 2005 client, whose `content/page/surface.html` shows this same tool row. The icons are packed into one embedded sheet, written to `2005Gui/2005_surface_tools.png` at startup. Without `getcustomasset`, the buttons fall back to text.

## ForceField and particle remover
`HIDE_FORCEFIELDS_AND_PARTICLES = true` in the settings hides, on your screen only:
- spawn ForceField bubbles
- ParticleEmitters, Sparkles, Fire and Smoke
- Explosion blasts

This covers effects already in the game and any created later. The ForceField still protects you, and other players still see the effects.
