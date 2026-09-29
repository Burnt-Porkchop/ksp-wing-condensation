# KSP Wingtip Vapor

A modified version of [KSP Wingtip Vortex](https://github.com/PogKai/ksp-wingtip-vortex) 1.4.0 by PogKai.

This version retains the **WingVapor** system while removing the original **Wingtip Vortex** rendering system. This allows another mod, such as KerbalFX, to provide the visible wingtip vortex effects while this mod provides the wing condensation and vapor effects.

[![KSP](https://img.shields.io/badge/KSP-1.12.x-4c9a4c?style=flat-square)](#install)
[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-lightgrey?style=flat-square)](LICENSE.md)

**[Original project](https://github.com/PogKai/ksp-wingtip-vortex)**
 ·  [Changelog](CHANGELOG.md)

---

## What it does

This mod adds wing condensation effects to aircraft based on their aerodynamic conditions.

The effect is most visible during high alpha maneuvers, such as hard turns and pulls.

|                          |                                                                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Wing vapor**           | A visible sheet of condensation that forms over the wings during hard pulls and high-lift conditions. It is intentionally difficult to produce under normal flight conditions. |
| **Aerodynamic response** | The vapor effect responds to the aerodynamic conditions of the aircraft and its wings.                                                                                         |
| **FAR support**          | When Ferram Aerospace Research is installed, the vapor system can use FAR's aerodynamic data. FAR is not required.                                                             |

The original wingtip vortex rendering system has been removed from this version.

---

## Why this version exists

The original KSP Wingtip Vortex mod provides both wingtip vortex effects and wing vapor effects.

This modification removes the original vortex rendering and management code while retaining the WingVapor system.

The goal is to use the wing vapor effects from this project alongside a separate vortex-effect implementation, in my case KerbalFX aero, rather than having two mods render competing wingtip vortex effects.

---

## Install

1. Download the latest release.
2. Copy the `WingtipVortex` folder inside the zip's `GameData` folder into your KSP `GameData` folder.

KSP 1.12.x · no dependencies · to upgrade, replace the folder · to remove, delete it.

---

## Compatibility

The retained WingVapor system works with:

* Stock KSP aerodynamics
* Ferram Aerospace Research
* KerbalFX
* Other visual mods that do not conflict with its vapor rendering

The original Wingtip Vortex rendering system is **not included** in this version.

---

## Original project

This project is based on **KSP Wingtip Vortex 1.4.0** by **PogKai**.

Original project:

https://github.com/PogKai/ksp-wingtip-vortex

The original project contains both the Wingtip Vortex and WingVapor systems. This fork removes the Wingtip Vortex rendering system and retains the WingVapor functionality.

---

## Source structure

### `Source/WingVapor/`

The retained wing vapor implementation.

- `WingVaporAddon.cs` — KSP addon/entry point
- `WingVapor.cs` — wing vapor behavior
- `VaporRenderer.cs` — vapor rendering
- `AeroState.cs` — aerodynamic state
- `LiftingLine.cs` — lifting-line calculations
- `Planform.cs` — wing geometry
- `Condensation.cs` — condensation calculations
- `TrailedVorticity.cs` — aerodynamic/vorticity calculations used by WingVapor
- `Sunlight.cs` — lighting-related calculations
- `BDArmoryCraft.cs` — BDArmory craft handling

### Removed

`WingtipVortex.cs` and the original `WingtipVortexManager` are intentionally
absent. They were responsible for the original visible wingtip vortex system.

### Compatibility shim

`WingtipVortexShim.cs` provides the `WingtipVortex.ModVersion` constant
expected by `WingVaporAddon.cs`. It does not implement the original vortex
system.

## Credits

**Original author:** PogKai

**Original project:** KSP Wingtip Vortex 1.4.0

This project is a modification of PogKai's original work. Credit is retained in accordance with the original project's license. 

**Modification:** The Wingtip Vortex rendering and management system was removed while the WingVapor system was retained for use alongside a separate vortex-effect implementation.

---

## License

[CC BY-NC-SA 4.0](LICENSE.md)

This project is a modified version of KSP Wingtip Vortex 1.4.0, which is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.

You may:

|               |                                                   |
| ------------- | ------------------------------------------------- |
| **Use it**    | In your own game, videos, streams and screenshots |
| **Change it** | Fork it, modify it, fix it, and build on it       |
| **Share it**  | Redistribute it or include it in a free modpack   |

When sharing a derivative, retain appropriate credit to PogKai and the original project, and follow the terms of CC BY-NC-SA 4.0.

Versions of the original project up to 1.2.0 were released under the MIT License and remain under that license. This modification is based on version 1.4.0.

---

## AI disclosure

This project was developed with assistance from AI tools.

|                      |                                                                                                                                                                  |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **PogKai**           | Original project, research, design, KSP integration, and original in-game testing                                                                                |
| **Claude (Anthropic)** | Assisted with development of the original KSP Wingtip Vortex project, as disclosed by PogKai |
| **Fork author**      | Modified the project to remove the Wingtip Vortex rendering system, retained the WingVapor system, built the modified DLL, and tested the resulting modification |
| **ChatGPT (OpenAI)** | Assisted with source-code analysis, identifying the WingVapor/Wingtip Vortex separation, and creating the modified build configuration                           |

AI assistance does not replace the original author's credit or the original project's license.

---

## Free, always

This modification is intended to remain freely available and is not intended to be sold or placed behind a paywall.

---

CC BY-NC-SA 4.0 · Based on work by PogKai
