# Krita SpaceMouse Plugin
![Krita SpaceMouse](krita_spacemouse/images/Krita_Spacemouse_Full_View.png)

A feature-rich plugin integrating SpaceMouse (especially Enterprise) with Krita on Linux, eliminating the keyboard for a streamlined art workflow.

> **This is a fork** of [Totem-FPV/Krita_Spacemouse](https://github.com/Totem-FPV/Krita_Spacemouse), the original plugin by Totem-FPV.
> It adds smoother canvas motion and a few new settings (see below). All changes are also offered back to the original project.

[**Documentation Wiki**](https://github.com/Totem-FPV/Krita_Spacemouse/wiki) (original project)

## Features
- Map 6 axes (X, Y, Z, RX, RY, RZ) to canvas actions (Pan, Zoom, Rotate) with custom curves.
- Bind 31 buttons (plus modifiers) to Krita actions via an interactive docker.
- Save presets for buttons and curves, persisting across sessions.

### What's new in this fork
- **Continuous zoom**: zoom follows the puck smoothly instead of jumping in steps, and also works at low sensitivity settings.
- **Smooth pan and rotation**: slow pushes move the canvas continuously (sub-pixel accumulation), and rotation is no longer limited to whole-degree steps.
- **Axis Max Input** (Advanced tab): set the full-travel value your device reports, so every axis can reach the top of its response curve. Use **350** for SpaceMouse Enterprise/Pro; the default (500) keeps the original behavior.
- **Dominant Motion Only** (Advanced tab, off by default): applies only the strongest of pan, zoom and rotation, so a slight twist does not leak into pan (and vice versa).

## Requirements (Linux-only)
- Krita 5.x
- `spacenavd` running, and the `libspnav` library
- Python modules `pyqtgraph`, `numpy` and `pyautogui`, available to Krita's Python

On Debian/Ubuntu:
```bash
sudo apt install spacenavd libspnav0 python3-pyqtgraph python3-numpy python3-pyautogui
```

## Installation
Krita loads Python plugins from `~/.local/share/krita/pykrita/`. The plugin consists of the `krita_spacemouse` folder and the `krita_spacemouse.desktop` file, and **both must sit directly** in that folder.

**Option A, release zip (recommended)**
1. Download `Krita_Spacemouse-<version>.zip` from the [Releases](https://github.com/joaulo/Krita_Spacemouse/releases) page.
2. Unpack it into `~/.local/share/krita/pykrita/`.

**Option B, Git** (easy updates with `git pull`)
1. Clone the repository anywhere you like:
   ```bash
   git clone https://github.com/joaulo/Krita_Spacemouse.git
   ```
2. Link the two plugin items into Krita's plugin folder (run from inside the cloned folder):
   ```bash
   mkdir -p ~/.local/share/krita/pykrita
   ln -s "$PWD/krita_spacemouse" ~/.local/share/krita/pykrita/krita_spacemouse
   ln -s "$PWD/krita_spacemouse.desktop" ~/.local/share/krita/pykrita/krita_spacemouse.desktop
   ```

**Then, in Krita**
1. `Settings > Configure Krita > Python Plugin Manager`: enable "Spacemouse Plugin", then restart Krita.
2. `Settings > Dockers > Spacemouse Controls`.
3. SpaceMouse Enterprise/Pro users: in the docker's **Advanced** tab, set **Axis Max Input** to 350.

**Note**: Ensure SpaceMouse buttons (including modifiers) pass through as normal keys in `spnav`, not system modifiers.

## Feedback
Report bugs for this fork at [GitHub Issues](https://github.com/joaulo/Krita_Spacemouse/issues).

## Credits and license
Original plugin by [Totem-FPV](https://github.com/Totem-FPV). Fork maintained by [joaulo](https://github.com/joaulo).

The original repository does not include a license; a request to add one is open in [Totem-FPV/Krita_Spacemouse#3](https://github.com/Totem-FPV/Krita_Spacemouse/issues/3). Until then, this fork is shared free of charge, with full credit to the original author.
