# Software Requirements

## Status

This document is a cleaned draft derived from the Drive `Software Requirements Specifications` document. It reflects the intended role of TheCube-Core and should be treated as a requirements baseline, not a finalized contract.

## Purpose

TheCube-Core is the central software controller for TheCube. It is responsible for:

- Managing hardware interactions
- Processing AI-driven commands
- Handling notifications and user events
- Exposing APIs for third-party applications

## Intended audience

- Developers building against TheCube-Core
- System architects
- Security and privacy reviewers
- Project stakeholders

## Scope

### In scope

- Hardware interactions: Bluetooth, NFC, audio, display, sensors, accelerometer
- Remote AI processing for voice and contextual interaction, orchestrated by Core
- Event processing and notifications
- API exposure for third-party apps
- Security and permission enforcement

### Out of scope for v1

- On-device speech recognition, on-device text-to-speech synthesis, and on-device intent detection
- Standalone user-facing apps as part of Core itself
- Advanced automation/scripting workflows inside Core

## External interfaces

### Hardware interfaces

- Display
- Audio I/O
- Sensors and accelerometer
- Bluetooth and NFC

### Software interfaces

- Linux-based operating environment
- Remote AI services for speech recognition, intent detection, and text-to-speech
- System services such as networking and power management
- Companion mobile or desktop setup app

### Communication interfaces

- Bluetooth and NFC
- API-based app communication

## Functional requirements

### System initialization

- Core shall initialize hardware components on boot.
- Core shall expose setup/configuration APIs.

### Device control API

- Core shall expose hardware functions to apps.
- App access shall be permission-gated.

### AI processing and context awareness

- Core shall capture voice input and forward speech workloads to remote AI services.
- Core shall use remote services for speech recognition, intent detection, and text-to-speech generation.
- Core shall render and/or play back returned responses locally.

### Event handling and notifications

- Core shall manage notifications from apps and system services.
- Apps shall be able to subscribe to relevant events.

### Application API and permissions

- Apps shall receive event-based updates through Core APIs.
- Permission-based access control shall be enforced.

## Non-functional requirements

### Performance

- Voice-command responsiveness target: within 2 seconds
- Idle CPU target from source draft: under 5%

### Security and privacy

- Minimize transmitted data and send only what is required for remote processing
- Encrypt external communication
- Log API access for auditing

### Maintainability

- Support modular updates and component-based evolution

## Use cases

### Configure device

- User powers on TheCube
- Device enters setup flow
- User configures network and preferences
- Settings are saved and applied

### Interact with device

- User issues a voice command
- Core streams/forwards audio and context to remote AI services
- TheCube responds and may update the display

### Handle notifications

- An app or system service sends a notification
- Core surfaces it through display and/or audio
- User acknowledges or dismisses it

## Architecture summary

The requirements source describes four layers:

1. Hardware layer
2. Core API layer
3. Remote AI processing layer
4. Event system

The current Core source tree broadly matches that separation, though the exact code organization is more granular.

## Open questions

- The source uses both mobile and desktop companion setup assumptions.
- Some interfaces are described at a conceptual level but not yet pinned to concrete contracts.
- The referenced Lucidchart system architecture diagram should be pulled into version control or recreated locally.

## Open Items

- `Decision needed:` choose whether device onboarding is formally mobile-first, desktop-first, or dual-path. Current direction: support mobile, desktop, and on-device onboarding flows in parallel.
- `Open question:` define concrete interface contracts and acceptance criteria for the conceptual requirements listed here.
- `Needs verification:` latency and CPU targets from the draft need validation against the current hardware/software stack.

## Sources

- Drive: `Software Requirements Specifications` (`11mgJ2IAxiTnyASn0a1NNlY1wSSCYfW13u-MHpugQhZA`)
- Drive: `Vision and Scope Document` (`1KmqlUA8gLHlX3OnUMb12ywlze50fWG-7NQnUSH0SAWg`)
