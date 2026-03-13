# Project Overview

`Project Overview` is a synthesized document. No exact Drive source with that title was found, so this file combines the current project plan, the Core vision/scope document, local repo reality, and the public docs structure.

## What Companion, TheCube Is

Companion, TheCube is an open, modular desktop companion platform built around a small character-driven device. It combines:

- A desk hardware product with display, audio, sensors, and expansion interfaces.
- A Core runtime that manages hardware, apps, configuration, personality logic, and local APIs.
- Optional cloud services for voice, AI, telemetry, account, and device-linked features.
- An app platform with multiple runtime models and example templates.
- A broader ecosystem of characters, modules, accessories, and community contributions.

## Product pillars

### 1. Companion-first interaction

TheCube is meant to feel like a character, not just an appliance. Personality traits, animated characters, playful reactions, and expressive UI are core product features rather than decorative extras.

### 2. Useful desk assistance

The practical value proposition is reminders, notifications, AI interaction, lightweight productivity support, and integration with surrounding devices or services.

### 3. Local-first privacy

The intended architecture prefers local processing where possible, with optional cloud augmentation for heavier AI workloads or subscription-based features.

### 4. Modularity

Both the hardware and software are designed to expand:

- Hardware through toppers, docks, ports, and form-factor variants.
- Software through apps, SDKs, app distribution, and community contributions.

## Current system boundaries

### Core runtime

`Companion-TheCube---Core` is the main local runtime. It already has clear subsystem boundaries for:

- API and auth
- App management
- Audio capture/output/routing
- Database access
- Decision engine and personality handling
- GUI and rendering
- Hardware integration
- Logging, settings, and telemetry

This makes Core the central integration point for device behavior.

### Cloud/server layer

`Companion-TheCube-Server` acts as the main cloud/server prototype. It currently includes:

- Auth routes
- Audio and voice-processing routes
- LLM chat/session routes
- Device registration and heartbeat
- Telemetry endpoints
- A WebSocket server for streaming transcription

The implementation is partly operational and partly draft, so docs need to distinguish present behavior from planned behavior.

The target backend architecture is microservices, with separate services planned for major domains such as auth, LLM, audio, device management, telemetry, and app distribution. The current monolithic server code should therefore be treated as a transitional prototype that will need to be rewritten to match the planned service boundaries.

### App catalog/distribution

`Companion-TheCube-AppServer` is the app catalog/distribution service. Its README describes a fuller service backed by Postgres, but the current implementation is still a thin Express app with in-memory app listings and a TODO-heavy roadmap.

### Public docs site

`Companion-TheCube.github.io` already contains the public docs skeleton and some Core content. This repo should not duplicate the whole site. Instead, `Planning-Docs` should store the planning and internal source material that can later feed the public site.

## Primary audiences

- The project owner and future collaborators
- App developers building against the platform
- Contributors working on Core, servers, or support tooling
- Stakeholders reviewing product scope, priorities, and maturity

## What this documentation set should accomplish

- Preserve the source planning material from Drive in versioned Markdown.
- Explain the current architecture as implemented, not only as envisioned.
- Keep draft specifications visible while marking uncertainty explicitly.
- Give every major subsystem a stable internal reference doc.
- Document the current app model across the example runtimes.

## Near-term documentation priorities

1. Stabilize the planning and product narrative.
2. Clarify the relationship between Core, server, app server, and public docs.
3. Turn the example apps into a reusable packaging and manifest reference.
4. Record open gaps: privacy policy, non-Docs Drive artifacts, and partially implemented server specs.

## Open Items

- `Decision needed:` define the stable boundary between `Planning-Docs` as an internal/source repo and `Companion-TheCube.github.io` as the public docs site. Current direction: `Planning-Docs` remains the internal/source repo and `Companion-TheCube.github.io` remains the polished public docs site.
- `Needs verification:` the current descriptions of server and app-server responsibilities combine implemented code with planned scope and will need periodic re-validation.
- `Open question:` decide whether separate audience-specific overviews are needed for contributors, public users, and business/stakeholder readers.

## Sources

- Drive: `Project Plan` (`1MGhYIrw1OeJNf3VE6GtfyWub_-aGOUIYPgzjNJoUXzg`)
- Drive: `Vision and Scope Document` (`1KmqlUA8gLHlX3OnUMb12ywlze50fWG-7NQnUSH0SAWg`)
- Local: `Companion-TheCube---Core/readme.md`
- Local: `Companion-TheCube---Core/src/**`
- Local: `Companion-TheCube.github.io/index.md`
- Local: `Companion-TheCube.github.io/core/index.md`
