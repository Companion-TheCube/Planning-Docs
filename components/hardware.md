# Hardware

## Current documented hardware target

The current planning docs describe a desk-sized modular device centered around:

- Raspberry Pi 5 compute core
- 4-inch 720x720 touchscreen
- Stereo microphones and speakers
- Wi-Fi and Bluetooth connectivity
- NFC
- mmWave presence sensing
- IMU and knock sensing
- Magnetic stacking surfaces
- Two expansion slots with mixed peripheral support

## Architectural intent

The hardware is not just a shell for the software. The product concept depends on:

- Physical presence on the desk
- Expandable modules and toppers
- Multi-device or multi-module interaction
- Sensor-driven contextual behaviors
- A display and audio system suitable for character presentation

## Current source-of-truth problem

Hardware documentation is currently fragmented:

- The project plan contains the clearest consolidated hardware summary.
- The public docs repo has hardware placeholders but not finished specifications.
- Core source code names the hardware integration areas but does not replace a hardware specification.

## What this means for the docs

This document should currently be treated as a planning-level hardware summary, not a manufacturing or electrical specification.

Follow-up documentation is still needed for:

- Board-level architecture
- Expansion connector pinout and electrical constraints
- Sensor and display part selection
- Mechanical dimensions
- Power budget and thermal design
- Variant strategy for MiniCube/WideCube/DoubleCube concepts

## Sources

- Drive: `Project Plan` (`1MGhYIrw1OeJNf3VE6GtfyWub_-aGOUIYPgzjNJoUXzg`)
- Local: `Companion-TheCube.github.io/hardware/specs.md`
- Local: `Companion-TheCube---Core/src/hardware/**`
