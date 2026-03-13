# BT Manager

## Purpose

`Companion-TheCube-BTManager` appears to be a dedicated Bluetooth management utility separated from the main Core runtime. Based on the available source and build files, it is responsible for Bluetooth-related networking or device management tasks that can run as an independent executable.

## Technical profile

- Language: C++23
- Build system: CMake
- Primary framework: Qt 6
- Required Qt components:
  - `Bluetooth`
  - `Network`
  - `Core`
- Additional dependencies:
  - `nlohmann/json`
  - `cpp-httplib`
  - `argparse`

## Build behavior

The `CMakeLists.txt`:

- Produces a `BT_Manager` executable
- Downloads missing header-only dependencies into `libraries/`
- Configures Qt search paths differently for Windows and non-Windows builds
- Adds Windows-specific DLL copy steps after build

## Current doc limitations

There is very little narrative documentation in the repo. The safest current description is:

- It is a standalone Bluetooth-focused helper tool.
- It is built with Qt Bluetooth rather than the Core GUI stack.
- It likely integrates with the rest of the platform over HTTP or local process boundaries, but that interface is not yet documented in the available source material.

## Open Items

- `Open question:` what exact runtime contract does BT Manager expose to Core or other services?
- `Needs verification:` whether BT Manager is meant to remain a standalone executable or eventually fold back into Core.

## Sources

- Local: `Companion-TheCube-BTManager/CMakeLists.txt`
- Local: `Companion-TheCube-BTManager/src/main.cpp`
- Local: `Companion-TheCube-BTManager/src/main.h`
