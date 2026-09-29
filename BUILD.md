# Building KSP Wingtip Vapor

This project is built against the assemblies included with KSP 1.12.x.

The original Wingtip Vortex project did not include its Visual Studio project because it referenced a local KSP installation. This fork therefore uses a direct C# compilation command instead.

## Requirements

You need:

* A KSP 1.12.x installation
* A C# compiler compatible with the KSP runtime
* The KSP assemblies listed below

The following assemblies are required:

* `Assembly-CSharp.dll`
* `UnityEngine.dll`
* `UnityEngine.CoreModule.dll`
* `UnityEngine.UI.dll`
* `UnityEngine.ParticleSystemModule.dll`

These assemblies are part of KSP and are not included in this repository.

## Source layout

The retained WingVapor implementation is located in:

`Source/WingVapor/`

The original `Source/WingtipVortex.cs` is intentionally absent. It contained the original visible wingtip vortex system, which has been removed from this modification.

`WingtipVortexShim.cs` provides the `WingtipVortex.ModVersion` constant required by the retained WingVapor code. It does not implement the original wingtip vortex system.

## Building on Linux

This project can be built using Mono's C# compiler (`mcs`).

On Fedora-based systems, install the Mono development tools:

```bash
sudo dnf install mono-devel
```

Set `KSP` to the `KSP_x64_Data/Managed` directory of your KSP installation:

```bash
KSP="/path/to/Kerbal Space Program/KSP_x64_Data/Managed"
```

The source files used by the build should be placed in a temporary build directory containing:

* All files from `Source/WingVapor/`
* `WingtipVortexShim.cs`

For example:

```bash
mkdir -p build
cp Source/WingVapor/*.cs build/
cp Source/WingtipVortexShim.cs build/
```

Then compile:

```bash
mcs \
  -target:library \
  -out:build/WingtipVortex.dll \
  -r:"$KSP/Assembly-CSharp.dll" \
  -r:"$KSP/UnityEngine.dll" \
  -r:"$KSP/UnityEngine.CoreModule.dll" \
  -r:"$KSP/UnityEngine.UI.dll" \
  -r:"$KSP/UnityEngine.ParticleSystemModule.dll" \
  build/*.cs
```

The resulting `WingtipVortex.dll` can be installed at:

`GameData/WingtipVortex/Plugins/WingtipVortex.dll`

The `build/` directory is only a temporary build directory and does not need to be included in the repository.

## Building on other platforms

The source can be compiled with another C# compiler compatible with the KSP runtime.

The important requirements are the same: compile the retained `Source/WingVapor/` source files and `WingtipVortexShim.cs` against the required KSP and Unity assemblies.

Do not include KSP or Unity assemblies in this repository.

## Modifying the project

The WingVapor implementation is contained in `Source/WingVapor/`.

The original Wingtip Vortex rendering system has intentionally been removed.

If `WingVaporAddon.cs` is modified, be aware that it references `WingtipVortex.ModVersion`. `WingtipVortexShim.cs` provides this value for compatibility and should remain present unless that reference is removed or changed.
