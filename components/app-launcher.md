# App Launcher

## Purpose

`App-Launcher` is documented as a helper app for TheCube Core that launches apps.

## Current known scope

Available source material is minimal:

- A short README describing it as a helper app
- A CMake project file

Based on its name and placement, the likely role is to act as a lightweight launcher or bridge between Core and installed apps, but the repository does not currently provide enough narrative documentation to define its runtime contract precisely.

## Recommended follow-up

This component needs one of the following in a later pass:

- A design doc describing when Core delegates to App-Launcher
- A code walkthrough of its executable behavior
- A decision about whether it remains separate or gets absorbed into Core app-management logic

## Open Items

- `Open question:` what launch responsibilities actually belong to this component versus Core's `appsManager`? Current direction: Core's AppManager owns overall lifecycle management, systemd manages process supervision, and App Launcher acts as the lightweight launch helper that starts apps with the correct environment and sandboxing. The current plan also calls for Landlock-based sandboxing in App Launcher.
- `Decision needed:` keep App Launcher as a separate component or fold its responsibilities into Core. Current recommendation: keep it separate for now, while re-evaluating that split if future implementation shows the boundary is too thin to justify.

## Sources

- Local: `App-Launcher/README.md`
- Local: `App-Launcher/CMakeLists.txt`
