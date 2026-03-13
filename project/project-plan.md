# Project Plan

## Companion, TheCube

## Introduction

Companion, TheCube is a modular desktop companion device that combines AI-assisted interaction, playful character design, and expandable hardware in a desk-sized form factor. The current concept centers on a 10 cm cube built around a Raspberry Pi 5, a 4-inch 720x720 touchscreen, embedded sensors, audio I/O, and magnetic expansion for toppers and modules.

The product is framed as both a tool and a character. It is intended to help with productivity, wellness, and entertainment while still feeling personable rather than sterile.

## Need And Requirement

### Problem statement

Remote workers, students, and professionals spend long periods at their desks. Existing assistants often feel impersonal, over-collect data, or do not provide enough presence or delight to feel companion-like.

### Requirements to solve the problem

TheCube should:

- Provide interactive companionship through adjustable personality and animated characters.
- Support productivity workflows such as reminders, notifications, and contextual information.
- Offer entertainment through apps, games, and playful behaviors.
- Fit cleanly into desk environments.
- Favor plug-and-play setup with NFC-assisted onboarding.
- Support modular expansion over time.
- Prefer local processing with optional cloud extensions.

### Market justification

The concept sits at the intersection of desk gadgets, privacy-conscious assistants, maker hardware, and personality-driven consumer electronics. The differentiation is the combination of usefulness, charm, and expandability.

## Product Overview

### High-level overview

TheCube blends:

- Hardware: cube enclosure, display, sensors, audio, and expansion interfaces.
- Software: Core runtime, app platform, cloud services, and SDKs.
- Personality: adjustable traits, character roster, expressive animation, and multi-Cube interactions.

### Solution description

- Interactive companionship through touch, voice, animation, and character-driven responses.
- Productivity support through notifications, calendar/message integration, timers, and reminders.
- Entertainment through games, storytelling, and a broader app ecosystem.
- Desk-friendly physical design with modular add-ons and magnetic stacking.
- Simplified setup through companion-app flows and NFC-assisted configuration.
- Open APIs and SDKs for community-driven extensions.

### Future plans

- More advanced sensors and larger or alternate display formats.
- Continued expansion of apps, games, and productivity tooling.
- New modules for environmental sensing and other hardware extensions.
- A broader third-party ecosystem around open APIs and app distribution.

## Major Features

### Hardware features

- Raspberry Pi 5 based core system.
- 4-inch 720x720 LCD touchscreen.
- mmWave presence sensing, IMU, and knock sensing.
- NFC reader/writer and embedded tags.
- Stereo microphones and speakers.
- Wi-Fi and Bluetooth/BLE.
- Two expansion slots with support for HDMI, I2C, SPI, UART, CAN, MIPI CSI/DSI, and 1-wire.
- Magnetic stacking surfaces for toppers and modules.

### Software features

- Optional cloud-backed speech and language processing.
- Local-first alternative paths for speech recognition, interpretation, and speech synthesis.
- App platform for entertainment and productivity features.
- Inter-unit communication across NFC and wireless links.
- Multi-unit collective display or coordinated behavior.
- Expandable, app-driven user experience.

## Project Process Description

The project uses a solo-developer-friendly Agile workflow with room for future open-source contributions.

### Planned phases

1. Project planning
   - Define scope, objectives, milestones, and high-level schedule.
2. Requirements gathering
   - Capture functional, non-functional, and interface requirements for hardware and software.
3. System design
   - Establish hardware schematics and software architecture.
4. Development and implementation
   - Build the initial codebase and hardware prototypes.
5. Testing and validation
   - Perform unit, integration, and system-level validation.
6. Documentation
   - Produce user-facing and contributor-facing documentation.
7. Release and deployment
   - Prepare builds, distribution, and first-user rollout.
8. Maintenance and upgrades
   - Address bugs, updates, and capability growth after release.
9. Community engagement
   - Support contributors, review pull requests, and keep public repos healthy.

## Project Schedule

### Phase 1: Planning and requirements

- Duration: 1 to 2 months
- Milestones:
  - Scope and deliverables defined
  - Initial requirements gathered
  - Project plan approved

### Phase 2: System design

- Duration: 1 to 2 months
- Milestones:
  - Hardware schematics drafted
  - Software architecture finalized
  - Design reviewed

### Phase 3: Development and implementation

- Duration: 6 to 12 months
- Milestones:
  - Initial software and hardware prototype completed
  - Core functionality running

### Phase 4: Testing and validation

- Duration: 2 to 3 months
- Milestones:
  - Feature and integration testing completed
  - Major bugs identified and fixed

### Phase 5: Documentation and pre-release

- Duration: 1 month
- Milestones:
  - User manuals complete
  - Technical docs prepared for contributors

### Phase 6: Release and initial feedback

- Duration: 1 month
- Milestones:
  - Prototype or early release distributed
  - Initial feedback collected

### Phase 7: Maintenance and community engagement

- Duration: ongoing
- Milestones:
  - Regular updates
  - Continued contributor and community management

### Schedule flexibility

- Use catch-up weeks to absorb delays.
- Reassess goals quarterly and adjust phase timing as needed.

## Project Work And Product Estimates

### Effort hours

- Research and planning: 100h
- Requirements gathering and design: 150h
- Development and implementation: 500h
- Testing and validation: 200h
- Documentation and pre-release: 120h
- Release and community engagement: 80h
- Ongoing maintenance, year 1: 150h

### Lines of code

- Core and platform software: 60,000 to 120,000 LOC
- Apps, SDK, and utilities: 10,000 to 20,000 LOC
- Total estimate: 70,000 to 140,000 LOC

## Team

The current working assumption is a single primary contributor: Andrew McDaniel.

Roles currently consolidated into one person:

- Project manager
- Systems architect
- Lead developer
- QA engineer
- Technical writer
- Community manager

## Scope And Limitations

### In scope

- Core Cube hardware and software
- Personality system and character roster
- Modular expansion ecosystem
- Open SDK and developer community
- TheCube+ subscription service

### Current limitations

- No mobility or robotic-arm concepts in v1
- Single-user focus in v1
- Advanced AI models depend on optional cloud services
- Limited smart home integrations at launch
- Security model is local-first but still evolving

## TheCube+ Subscription Service

- Free tier: local AI only
- Cube+1: casual cloud AI usage
- Cube+2: expanded voice and premium interactions
- Cube+3: highest-capacity tier for heavy users and developers

Pricing in the source plan should be treated as draft product planning, not final commercial policy.

## Marketing And Community Engagement

- Lore-driven blog and personality content
- Short-form videos and humorous office-life content
- Discord, GitHub, and 3D-print-sharing community channels
- Limited-edition toppers, campaigns, and fan-driven accessories
- Device-specific content and personality ecosystems

## Open Items

- `Decision needed:` finalize subscription tiers, naming, and pricing before treating this as a product baseline. Current status: the tiers and pricing in this document are still draft planning values.
- `Needs verification:` schedule ranges, effort estimates, LOC estimates, and single-person role assumptions are planning estimates, not validated delivery commitments.
- `Needs verification:` the hardware feature list, character roster, and ecosystem scope are still planning-level and may not match the eventual shipped v1 surface.

## Sources

- Drive: `Project Plan` (`1MGhYIrw1OeJNf3VE6GtfyWub_-aGOUIYPgzjNJoUXzg`)
