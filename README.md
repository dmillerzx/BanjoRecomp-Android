# 📱 Banjo: Recompiled — Community Android & Handheld Port

<p align="center">
  <a href="https://github.com/dmillerzx/BanjoRecomp-Android/releases/latest">
    <img src="https://img.shields.io/github/v/release/dmillerzx/BanjoRecomp-Android?label=Latest%20Android%20APK&amp;color=brightgreen&amp;style=for-the-badge" alt="Latest Android APK">
  </a>
  <a href="https://github.com/dmillerzx/BanjoRecomp-Android/releases">
    <img src="https://img.shields.io/badge/Platform-Android%20arm64--v8a-blue?style=for-the-badge&amp;logo=android" alt="Platform: Android arm64-v8a">
  </a>
  <a href="https://github.com/dmillerzx/BanjoRecomp-Android/issues">
    <img src="https://img.shields.io/github/issues/dmillerzx/BanjoRecomp-Android?style=for-the-badge&amp;color=orange" alt="GitHub Issues">
  </a>
</p>

> [!NOTE]
> **Community Handheld Fork Notice**: This repository is a community-driven fork maintained by [dmillerzx](https://github.com/dmillerzx) focused on physical Android gaming handhelds — actively maintained and verified on the **Retroid Pocket 5** (Qualcomm Snapdragon 865, Adreno 650, Android 13) and generic AArch64 devices.
>
> * Upstream Android port by [@AurelioB](https://github.com/AurelioB/BanjoRecomp-Android) (originally developed and tested on the AYN Thor dual-screen handheld).
> * Desktop releases and core recompilation by [N64: Recompiled](https://github.com/N64Recomp/N64Recomp).
> * **No Game Assets**: This repository and its releases do not contain game assets or ROMs. You must provide an authentic **Banjo-Kazooie (USA) v1.0** ROM (`.z64`).


## Features

### Feature complete with the PC version

- High-framerate and widescreen support from the PC version.
- Faithful audio and original game behavior.
- Modern quality of life features such as note saving.
- Full mod support, including local mod and texture-pack import.

### Full controller & handheld hardware support

- **Primary Test Device**: Actively maintained and verified on the **Retroid Pocket 5 (RP5)** (Qualcomm Snapdragon 865 / Adreno 650, Android 13) at native 1080p, locked 60 FPS in 16:9 widescreen presentation.
- **Physical Controls**: Tuned controller mapping including modern dual-trigger crouch multi-bind (`ZL` + `L1`).
- **Adreno 650 / Snapdragon 865 Crash Guard**: Null-pipeline SPIR-V guard preventing driver `SIGSEGV` faults on Qualcomm devices.
- **Turnip GPU Driver Loader**: Built-in AdrenoTools driver loader supporting Mesa Turnip drivers (e.g. Turnip v24.3.0 R9v2) for enhanced Vulkan stability.
- **Zero-Touch ROM Hydration**: Automatically searches `/storage/*/ROMs/n64/` and app files on launch, extracting `.zip` archives and verifying ROM headers so the game is ready to play immediately.
- **Header Inspection Dialog**: Detects unsupported revisions (e.g. Rev A / v1.1) and displays a clear explanation dialog rather than failing silently.
- *(Note: Upstream project was originally developed and tested on the dual-screen AYN Thor).*

### Android save management

The Android settings include a **Save Management** page for importing and exporting the active Banjo-Kazooie save and selecting an Android DocumentsUI folder for synchronized storage. The game keeps an app-private runtime copy for native I/O; when a folder is selected, its `banjo-kazooie.bin` document is authoritative across launches and the app writes a safe snapshot back when it pauses.

Selecting an empty destination copies the existing save into it. A destination containing a recognized Banjo save or backup is never overwritten automatically; import that file explicitly if it should replace the active save. See [Android save storage](docs/plans/android-save-storage.md) for backup and failure behavior.

### Dual-screen companion display

On supported devices, the second screen becomes a live companion display, including:

- Double tap to toggle secondary display on/off.
- Animated icons for game status and collectibles.
- Dynamic backgrounds based on the current game area.
- Live gameplay stats such as health, lives, notes, eggs, feathers, Jiggies, Mumbo tokens, Jinjos, and level context.
- Smooth transitions between areas.

## Screenshots

| Label | Primary display | Secondary display |
|---|---|---|
| Main menu | ![Main menu on the primary display](docs/assets/android-dual-screen/main-menu-primary.png) | ![Main menu companion logo on the secondary display](docs/assets/android-dual-screen/main-menu-secondary.png) |
| Slot select | ![Slot select on the primary display](docs/assets/android-dual-screen/slot-select-primary.png) | ![Slot select companion stats on the secondary display](docs/assets/android-dual-screen/slot-select-secondary.png) |
| Gruntilda's lair | ![Gruntilda's lair on the primary display](docs/assets/android-dual-screen/gruntildas-lair-primary.png) | ![Gruntilda's lair companion stats on the secondary display](docs/assets/android-dual-screen/gruntildas-lair-secondary.png) |
| Mumbo's Mountain | ![Mumbo's Mountain on the primary display](docs/assets/android-dual-screen/mumbos-mountain-primary.png) | ![Mumbo's Mountain companion stats on the secondary display](docs/assets/android-dual-screen/mumbos-mountain-secondary.png) |

## Mods on Android

So far, I've only tried the [BK Reloaded texture pack](https://thunderstore.io/c/banjo-recompiled/p/GhostlyDark/BK_Reloaded/)
Please report if you find an incompatible mod

## Development notes

For Android setup, build commands, ADB verification, screenshot capture conventions, and artifact hygiene, see [docs/android-port.md](docs/android-port.md).

For the experimental dual-screen implementation details, see:

- [Android dual-screen companion display API](docs/android-dualscreen-framework-api.md)
- [Dual-screen ownership boundaries](docs/plans/android-dualscreen-framework-ownership.md)
- [Dual-screen transition findings](docs/android-dual-screen-transition-findings.md)

## Upstream project and credits

This Android port is based on Banjo: Recompiled. See [README.original.md](README.original.md) for the original project overview, desktop feature list, FAQ, and upstream acknowledgements.

Core upstream projects include:

- [N64: Recompiled](https://github.com/N64Recomp/N64Recomp)
- [RT64](https://github.com/rt64/rt64)
- [N64ModernRuntime](https://github.com/N64Recomp/N64ModernRuntime)
- [RecompFrontend](https://github.com/N64Recomp/RecompFrontend)
- [Banjo-Kazooie Decompilation](https://gitlab.com/banjo.decomp/banjo-kazooie)
