# Core

## Purpose

The Core is the primary runtime that runs on TheCube device hardware. It owns the local user experience and most device-side orchestration:

- Boot-time startup and configuration
- Hardware integration
- GUI rendering and character presentation
- App execution and lifecycle management
- Audio input/output plus remote voice-AI handoff flows
- Local APIs, auth, settings, and telemetry
- Personality and decision logic

## Current implementation shape

The current source tree in `Companion-TheCube---Core/src` is organized into the following main subsystems:

| Subsystem         | Role                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| `api/`            | Local REST-style interface exposure, auth helpers, interface registration                                           |
| `apps/`           | Running app abstraction, app DB, app manager, Docker/native/python hooks                                            |
| `audio/`          | Capture, output, routing, wake-word client, remote audio transport hooks                                            |
| `database/`       | Core DB and blob/data access                                                                                        |
| `decisionEngine/` | Remote intent/transcription orchestration, function registry, scheduling, transcription events, personality manager |
| `gui/`            | Renderer, status bar, character manager, menus, message boxes, shaders                                              |
| `hardware/`       | Bluetooth, Wi-Fi, NFC, mmWave, peripheral management, fan/system control, I2C                                       |
| `logger/`         | Structured logging                                                                                                  |
| `settings/`       | Settings loading and global settings                                                                                |
| `telemetry/`      | Device-side telemetry                                                                                               |

## API surface

The in-repo API README describes a local API bootstrapped through an initial request to `TheCube.local` or `localhost`, then exposed over port `55280` or a Unix socket. Documented interface groups include:

- Audio manager
- Cube auth
- Cube DB
- Bluetooth
- GUI
- Notifications
- Personality manager
- Logger

This local API appears to be device-facing and distinct from the separate cloud/server repo.

## Build and test model

The top-level README positions Core as a Debian/Ubuntu-targeted C++ project using CMake. It documents:

- Development and deployment dependency installation
- Release and debug builds
- Optional build-server integration
- `.env`-driven configuration
- Google Test-based test targets
- Ubuntu-container validation under `testing/`

## Current documentation alignment

The public docs repo already has a solid Core docs skeleton and some useful conceptual framing. The internal version here should stay closer to the codebase and its real subsystem map.

## Known gaps and risks

The TODO inventory shows that Core is still actively evolving in these areas:

- App installation, update, and lifecycle completeness
- Audio robustness and remote voice pipeline polish (streaming, retries, latency, playback)
- GUI settings, legal pages, privacy policy display, and system information pages
- Database schema hardening and API cleanup
- More complete documentation across app and character management

That means this doc should be treated as a subsystem map and current-state reference, not as a statement that all advertised platform behaviors are finished.

## Open Items

- `Open question:` confirm the intended long-term boundary between the device-local Core API and the separate cloud/server API. Current direction: Core owns device-local interactions such as app lifecycle management, hardware control, wake-word detection, and local UX, while the cloud/server APIs own speech recognition, intent detection, text-to-speech, backend services, user management, and remote interactions.
- `Decision needed:` decide whether Core continues to own most app lifecycle concerns directly or delegates more responsibility to helper components such as App Launcher or BT Manager. Current direction: Core keeps overall lifecycle ownership, while App Launcher handles the mechanics of launching apps. The current plan also calls for Landlock sandboxing in App Launcher alongside systemd supervision.
- `Needs verification:` several subsystems described in public-facing materials are still represented in code as active TODO areas rather than finished capability. Current documentation will need periodic review against the codebase as implementation advances.

## Sources

- Local: `Companion-TheCube---Core/readme.md`
- Local: `Companion-TheCube---Core/src/api/readme.md`
- Local: `Companion-TheCube---Core/src/**`
- Local: `Companion-TheCube---Core/testing/README.md`
- Local: `Companion-TheCube---Core/TODO's.md`
- Local: `Companion-TheCube.github.io/core/index.md`
