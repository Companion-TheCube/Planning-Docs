# App Platform Overview

## Purpose

TheCube app platform is the layer that allows third-party or bundled applications to extend the device beyond the built-in Core behaviors.

## Current app types in the repo

The example app set shows four practical packaging styles:

- Docker container app
- Node.js app
- Python app
- Native binary app

The native category is demonstrated in multiple languages:

- C++
- C#
- Go
- Rust

## Shared app shape across examples

Across the example repos, apps generally include:

- A manifest file
- A source entry point or compiled binary
- Optional assets
- Build or run instructions
- Environment-variable driven configuration

The examples consistently use a simple HelloCube pattern:

- Read `GREETING`
- Print or display a message
- Simulate audio output
- Package metadata in a manifest

## Runtime model

### Example-manifest model

The example repos currently use a simple JSON manifest with fields such as:

- `id`
- `name`
- `version`
- `description`
- `type`
- `entry`
- `permissions`
- `env`
- `args`
- `ui`

This model is enough for starter apps and documentation examples.

### Emerging Core manifest model

Core also contains a richer YAML manifest example with explicit sections for:

- Runtime hints
- Filesystem mounts
- Fine-grained permissions
- cgroup limits
- secrets
- event subscriptions/publications

That suggests the platform is moving toward a more structured deployment and sandboxing model than the public examples currently show.

## Current documentation reality

The public docs repo has app-platform placeholders, but the example repos already define a practical first-pass contract:

- App package contains an entry point and metadata
- App requests a small permission set
- Core is expected to launch and supervise it
- UI and audio are first-class app capabilities

## Recommended interpretation for v1 docs

Use the simple JSON manifests as the concrete, example-backed format. Treat the richer YAML schema inside Core as the likely next-stage internal contract and document it as forward-looking.

## Sources

- Local: `AppExample-Docker/manifest.json`
- Local: `AppExample-NodeJS/manifest.json`
- Local: `AppExample-Python/manifest.json`
- Local: `AppExample-Native-CPP/manifest.json`
- Local: `AppExample-Native-CSharp/manifest.json`
- Local: `AppExample-Native-Go/manifest.json`
- Local: `AppExample-Native-Rust/manifest.json`
- Local: `Companion-TheCube---Core/src/apps/exampleApp.manifest.yml`
