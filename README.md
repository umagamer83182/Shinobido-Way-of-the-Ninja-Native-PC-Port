# Shinobido: Way of the Ninja — Native PC Port

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011%20x64-blue)
![Graphics](https://img.shields.io/badge/graphics-DirectX%2011-informational)
![Game data](https://img.shields.io/badge/game%20data-not%20included-red)

A native Windows port of **Shinobido: Way of the Ninja** (PlayStation 2, European release, **SCES-53931**), made by
*static recompilation*: the game's original PS2 code was translated into native PC code with
[PS2Recomp](https://github.com/ran-j/PS2Recomp) and runs on a PC runtime. It is not an emulator. It runs at 60 fps,
renders at high resolutions with Direct3D 11, supports the PCSX2 HD texture pack, and adds an in-game settings menu,
a launcher, character texture mods and full keyboard, mouse and controller support.

> **No game data is included.** You need your own copy of the game: an ISO dumped from your original European
> DVD. The launcher installs the game files from that ISO on your PC.

---

## Contents

- [Features](#features)
- [Requirements](#requirements)
- [Packages](#packages)
- [Installation](#installation)
- [Playing](#playing)
- [The launcher](#the-launcher)
- [Controls](#controls)
- [In-game settings menu (F9)](#in-game-settings-menu-f9)
- [HD textures](#hd-textures)
- [Character texture mods](#character-texture-mods)
- [Files and folders](#files-and-folders)
- [Troubleshooting](#troubleshooting)
- [Antivirus / SmartScreen false positives](#antivirus--smartscreen-false-positives)
- [FAQ](#faq)
- [Known issues](#known-issues)
- [Credits and licenses](#credits-and-licenses)
- [Legal](#legal)

---

## Features

| Area | What you get |
|---|---|
| **Frame rate** | 60 fps (also 50, or 25 as on the European PS2). The game always runs at its original speed: the game clock follows real time at any frame rate. Story scenes play at 25 fps, at their original length. |
| **Resolution** | Internal 3D resolution up to 3840×2160 (21:9: up to 5120×2160), supersampling 1.5× / 2×, texture filter (Enhanced / Original / Pixelated), anisotropic filtering up to 16×, sharpening. |
| **Widescreen** | The game's own 16:9 mode, plus an experimental **21:9** ultrawide mode (wider camera, HUD not stretched, 2D screens and videos kept at 16:9). |
| **Field of view** | 0.7 to 1.5 × the original. |
| **Display** | Windowed, borderless or exclusive fullscreen; V-Sync; frame pacing; brightness, contrast and saturation. |
| **Screen effects** | Blur / afterimage / haze toggle, cutscene letterbox toggle, black borders toggle. |
| **HUD** | Hide the whole HUD or each element (health bar, awareness eye, compass, mission banners, message boxes, item holder, enemy markers); in 21:9 the HUD can stay in the centre or move to the screen edges. |
| **HD textures** | Reads the PCSX2 HD texture pack of the game straight from its folder (nothing is copied). |
| **Settings menu** | **F9** in game or in the menus: Video, Graphics, Game, Cheats, Skins, Controls, drawn with the game's own menu art and font. Picture options show a live preview panel over the game. |
| **Cheats** | Infinite health, one-hit kill, infinite items, infinite item time, infinite jump, invisibility, super speed, moon jump, Kids Mode, refill health, max health, max money, all items, max item stock, unlock all extras, unlock Kinu. |
| **Skins** | Model change, costume, animation set and special weapon (including the Ancestral Sword), applied immediately. |
| **Mods** | Character and weapon texture mods: drop PNG/DDS textures in `mods\`, they appear as extra costumes. |
| **Auto lock-on** | Optional: locks onto the nearest enemy by itself (Original: hold L1, as in the game). |
| **Controls** | Xbox / XInput controllers and PS2 pads on USB adapters, keyboard, mouse look; every key and button can be rebound. |
| **Videos** | All the game's videos (logos, intro, story scenes) play with picture and sound, and can be skipped as on the PS2. |
| **Performance overlay** | FPS, or FPS + frame time, under the health bar. |
| **Launcher** | Installs the game from your ISO, sets the options before you play, creates a desktop shortcut. Drawn like a screen of the game. |

---

## Requirements

- **Windows 10 or 11, 64-bit.**
- **A graphics card with DirectX 11.** 4 GB of video memory or more is recommended with the HD texture pack.
- **Your own copy of the game:** a `.iso` disc image of **Shinobido: Way of the Ninja, European release (PAL,
  SCES-53931)**, dumped from your original DVD. Other releases (US, Japanese) do not work. Compressed images
  (`.chd`, `.cso`, `.zip`, `.7z`) and `.bin`/`.cue` must be converted to a plain `.iso` first.
- About **4.7 GB** of free disk space for the installed game.
- Optional: the PCSX2 HD texture pack of the game.

No emulator and no PS2 BIOS are needed.

---

## Packages

| Package | What it contains | Size |
|---|---|---|
| **Lite** (`Shinobido.exe`) | One file: the launcher with the PC runtime packed inside. The game files come from your ISO. | ~70 MB |
| **Full** (`Shinobido PC` folder) | The launcher, the runtime already unpacked in `runtime\`, and the folders `game\`, `textures\` and `mods\`. | — |

Both use the same launcher.

---

## Installation

### Lite package

1. Put `Shinobido.exe` in a folder of its own, for example `C:\Games\Shinobido\`, and run it.
2. If no game files are found yet, the launcher opens on **Game Files**.
3. **Disc Image (ISO):** press Enter or click the row and choose your `.iso` (or drag the ISO onto the window).
   The launcher checks it right away:
   - ✔ `Shinobido - Way of the Ninja, Europe (SCES-53931): verified` — the right disc;
   - `Wrong version` — another release of the game;
   - `Not an ISO` — not a disc image, or a compressed / `.bin` image;
   - `damaged or modified` — the European disc, but its game executable differs (a bad dump).
4. **HD Texture Pack** (optional): choose the folder of the pack (the pack's folder, its `SCES-53931` folder or its
   `replacements` folder). The number of textures found is shown. `Delete` goes back to the original textures.
5. **Install:** the launcher unpacks the runtime into `runtime\` (a few seconds) and copies the disc's files into
   `game\` (about 3.9 GB, one or two minutes). The window stays responsive; the same row becomes **Stop** while it
   runs.
6. Press **Return** (Esc) to go back to the title screen, then **Play**.

After the install the ISO is no longer used: you can move or delete it.

Unattended install (scripts):

```bat
Shinobido.exe --iso="D:\Images\Shinobido.iso" --textures="D:\Packs\Shinobido HD" --no-launch
Shinobido.exe --iso="D:\Images\Shinobido.iso" --textures=none --no-launch
```

### Full package

The game is already in place: run `Shinobido.exe` and choose **Play**.

### Updating

To update the Lite package, replace `Shinobido.exe` with the new one. The next **Play** updates the `runtime\` folder
by itself; the game files, the settings and the saves stay.

---

## Playing

- **Run `Shinobido.exe`** and choose **Play** (or press Enter).
- **Straight to the game:** in the launcher, **Launcher → Desktop Shortcut → On** creates a `Shinobido` shortcut on
  the desktop that starts the game directly, as Play does, without showing the launcher. It runs
  `Shinobido.exe --play`.
- **To quit the game:** Esc or Alt+F4.

---

## The launcher

The launcher is laid out like the game's own screens: its title screen, its Options screen and the Mission Editor.

| Screen | What it does |
|---|---|
| **Title** | Play (Install before the game is installed), Game Files, Video, Graphics, Game, Launcher, Game Folder, Patch Notes, Read Me, Exit. At the bottom: what is installed (runtime, game files, HD textures, monitor, graphics card). |
| **Game Files** | The ISO, the HD texture pack and the install (see [Installation](#installation)). |
| **Video** | Your Goal preset (Smooth / Balanced / Quality), resolution, supersampling, aspect ratio, field of view, frame rate, screen mode, V-Sync, frame pacing. |
| **Graphics** | Texture filter, anisotropic filter, sharpening, HD textures, brightness, contrast, saturation, blur effects, cutscene letterbox, black borders. |
| **Game** | Auto lock-on, HUD and each HUD element, ultrawide HUD position, performance overlay. |
| **Launcher** | Close on Play, Desktop Shortcut, and buttons to open the game folder, the patch notes and this file. |

The options are the same as in the in-game F9 menu and are saved in `runtime\settings.ini`; they apply the next time
the game starts (while the game is open, use F9).

**Navigation:** arrow keys, Enter, Esc / Backspace (back), Q / E (previous / next page), Delete (Return to Default);
the mouse (hovering picks a row, clicking uses it); or a controller (d-pad, A, B / Y, X, LB / RB, Start).

**The launcher's look:** its font and pictures are read from the game itself — the `game\` folder, another
installation of the game on the same PC, or the ISO (found automatically next to `Shinobido.exe`, in its parent
folder, in Downloads, on the Desktop or in Documents, or the one you choose). They are kept in
`%LOCALAPPDATA%\Shinobido\look\` so the launcher keeps that look afterwards. Until the game is found, the launcher
draws a similar look of its own. Hold **Shift** while starting `Shinobido.exe` (or use `--setup`) to open directly on
Game Files.

---

## Controls

**Controller:** Xbox / XInput controllers, or PS2 pads on a USB adapter. Any connected controller controls player 1.

**Keyboard (default):**

| PS2 | Key |
|---|---|
| D-pad | Arrow keys / WASD |
| ✕ | X / Space |
| ○ | C |
| □ | Z |
| △ | V |
| Start | Enter |
| Select | Tab |
| L1 / R1 | Q / E |
| L2 / R2 | Left Shift / Right Shift |

**Mouse:** moving the mouse turns the camera (together with the right stick). While you play the cursor is hidden
and held in the window; it comes back when a menu (F9) opens, on Alt+Tab or when the window is minimized. In
**F9 → Controls**: Mouse look on/off, mouse sensitivity (10–300 %), invert X / invert Y.

**Rebinding:** in **F9 → Controls**, double-click a binding and press the new key or button. A keyboard binding
also accepts mouse buttons (left, right, middle, Mouse 4 / 5) and the wheel (Wheel Up / Down).

---

## In-game settings menu (F9)

Press **F9** during the game or in its menus. Sections: **Video**, **Graphics**, **Game**, **Cheats**, **Skins**,
**Controls**.

- **Keyboard:** arrows move and change values, Enter = Okay, Esc = back (closes the menu from the section list),
  Q / E = previous / next section, F9 closes.
- **Controller:** d-pad, A (✕) = Okay, B (○) or Y (△) = back, LB / RB (L1 / R1) = section.
- **Mouse:** click options and sections, drag the bars, the wheel scrolls, right click goes back.
- **Live preview:** options that change the picture (field of view, brightness, filters…) open a panel at the
  bottom, over the running game: Confirm keeps the value, Cancel (Esc / ○ / right click) restores the previous one.

Everything applies at once and is saved in `runtime\settings.ini`. A notice appears when the menu closes
(`Settings saved`, or the cheat / skin chosen). Screen modes use the monitor the game window is on.

**Skins:** model change and costume (including mod costumes) apply at once, during a mission and in the hideout.
Animation set and special weapon apply at once in a mission and from the next mission in the hideout.

---

## HD textures

The game reads the PCSX2 HD texture pack of Shinobido straight from its folder; nothing is copied.

- **Lite:** choose the pack in **Game Files → HD Texture Pack**.
- **Full:** the pack in `textures\SCES-53931\replacements\` is used.
- **Graphics → HD Textures** turns the pack on or off.

---

## Character texture mods

The first time the game starts it creates a `mods\` folder (next to `runtime\` and `game\`) with
`mods\_templates\<Character>\`: the original textures of each character and of the weapons, as PNG.

1. Copy the textures you want to change into a new folder inside `mods\`, named after your mod, keeping the file
   names, e.g. `mods\Red Kinu\kn_kimono_top.png`.
2. Edit them. You can raise the resolution (2×, 4×…) as long as the proportions stay.
3. Start the game: the mod appears as one more costume of that character in **F9 → Skins → Costume**, after the
   original ones.

- Loose files in `mods\` (or in a folder named after a character) become "Mod 1", "Mod 2"…
- Weapon textures always apply.
- Files named like PCSX2 replacement textures (`<hash>-<hash>-<bits>.png` / `.dds`) also work, so PCSX2 mod packs can
  be dropped into `mods\` as they are (each folder of textures becomes a costume). Extract `.7z` / `.zip` packs first.
- Mods take priority over the HD texture pack.
- Mods are read when the game starts: restart it after changing the folder.
- Delete `mods\_templates` to have the templates made again.

---

## Files and folders

| Path | Contents |
|---|---|
| `Shinobido.exe` | The launcher (in the Lite package, with the runtime inside). |
| `Shinobido.ini` | The launcher's choices: installed runtime, ISO, HD texture folder, close on play. |
| `runtime\` | The game runtime (`ps2EntryRunner.exe` and its libraries). |
| `runtime\settings.ini` | All game settings (the F9 menu and the launcher read and write it). |
| `runtime\log.txt` | The game's log, written anew each time the game starts. |
| `game\` | The game files copied from your ISO. |
| `game\mc0\` | The memory card (your saves). |
| `textures\` | Full package: the HD texture pack. |
| `mods\` | Character texture mods and their templates. |
| `launcher.log` | What the launcher did at start: where it read the game's look from, or why it could not. |
| `%LOCALAPPDATA%\Shinobido\look\` | The launcher's look, read once from your game (made on your PC). |

---

## Troubleshooting

- **The game does not start or closes:** look at `runtime\log.txt` (next to the game; it is rewritten each time the
  game starts).
- **The launcher looks plain (no game art):** it has not found the game yet. Install the game, or choose your ISO in
  Game Files; `launcher.log` says where it looked.
- **The ISO is refused:** see the message under the Disc Image row (wrong release, not an ISO, damaged dump).
- **Not enough disk space:** the Game Files page shows how much the install needs and how much is free.
- **Old icon after an update:** Windows caches icons; it updates after a restart.

---

## Antivirus / SmartScreen false positives

**`Shinobido.exe` and `ps2EntryRunner.exe` are not viruses.** They are a recompilation of the game's own code into a
Windows program, plus a launcher; they contain no malware.

Some antivirus engines, or Windows SmartScreen, may still flag them, because:

- the executables are **unsigned** and **newly built**, so they have no download reputation yet;
- they are produced by **static recompilation**, so their code looks unlike ordinary hand-written programs;
- the **Lite** `Shinobido.exe` is a **self-extracting** program: it carries the compressed runtime inside and unpacks
  it into `runtime\`;
- the runtime does **low-level work** that running console code on a PC needs, such as reserving and mapping large blocks of
  memory.

If that happens:

- **SmartScreen** ("Windows protected your PC"): click **More info → Run anyway**.
- **Antivirus quarantine:** restore the file from quarantine and add an **exclusion for the game's folder** only.
  There is no need to turn your antivirus off.

Download the packages only from the official release page, and check that your file is the published one by
comparing its SHA256 hash with the one in the release notes:

```bat
certutil -hashfile Shinobido.exe SHA256
```

```powershell
Get-FileHash .\Shinobido.exe -Algorithm SHA256
```

---

## FAQ

**Does it include the game?**
No. You need your own European ISO; the launcher installs the game files from it on your PC.

**Does it work with the US or Japanese release?**
No, only the European release (PAL, SCES-53931).

**Do I need a PS2 BIOS or an emulator?**
No.

**Can I keep using the HD texture pack I have for PCSX2?**
Yes: point the launcher at its folder (Lite) or put it in `textures\` (Full).

**My antivirus says it is a virus. Is it?**
No. It is a false positive caused by an unsigned, newly built, self-extracting program; see
[Antivirus / SmartScreen false positives](#antivirus--smartscreen-false-positives).

**Where are my saves?**
In `game\mc0\`, the memory card.

**Can I play at 25 fps like on the PS2?**
Yes: Video → Frame Rate → 25 (Original). The game speed is the same at every frame rate.

---

## Known issues

- **21:9 is experimental.** The wider view shows more of each scene, so big fights can run a little below 60 fps.
- **Heavy spots:** the heaviest fight in Mokuami Fortress and a few isolated moments in Mokuami Fortress and Sengen
  Town can drop into the 50s.
- **Skins:** the bear model covers part of the hideout menu; changing the animation set or the special weapon can
  cause a short hitch.

---

## Credits and licenses

This port is built on:

| Project | Used for | License |
|---|---|---|
| [PS2Recomp](https://github.com/ran-j/PS2Recomp) | Static recompiler and PC runtime for PS2 games | GPL-3.0 |
| [raylib](https://github.com/raysan5/raylib) | Window, input and drawing of the menus | zlib |
| [Dear ImGui](https://github.com/ocornut/imgui) and [rlImGui](https://github.com/raylib-extras/rlImGui) | Debug panel | MIT |
| [FFmpeg](https://ffmpeg.org/) (libavcodec, libavutil, libswresample, libswscale) | The game's videos | LGPL-2.1-or-later |
| [libjxl](https://github.com/libjxl/libjxl), [libwebp](https://chromium.googlesource.com/webm/libwebp), [Brotli](https://github.com/google/brotli), [zlib](https://zlib.net/) | Libraries loaded by FFmpeg | BSD-3-Clause, BSD-3-Clause, MIT, zlib |
| [xxHash](https://github.com/Cyan4973/xxHash) | Texture hashing (HD texture pack, mods) | BSD-2-Clause |
| [XZ Utils / liblzma](https://tukaani.org/xz/) | The Lite launcher's packed runtime | 0BSD |

The HD texture pack is not part of this project; it is made and distributed by its own authors.

---

## Legal

This is an unofficial, non-commercial fan project. It is **not affiliated with, endorsed or sponsored by** Sony
Interactive Entertainment, Spike or Acquire. *Shinobido: Way of the Ninja* and its names, logos and artwork belong
to their respective owners.

**No copyrighted game data is distributed.** The packages contain only the recompiled program and its libraries;
the game files are installed from the user's own legally owned copy, and the launcher's game-styled look is read
from those files on the user's own PC.
