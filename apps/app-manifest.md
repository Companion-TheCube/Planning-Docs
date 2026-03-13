# App Manifest

## Status

There are currently two manifest shapes visible in the source material:

1. A simple JSON manifest used by the example apps.
2. A richer YAML manifest example in Core that appears to target a more complete runtime/sandbox model.

This document records both, with the JSON shape treated as the current practical example format.

## Simple JSON manifest

### Common fields

| Field | Meaning |
| --- | --- |
| `id` | Unique app identifier |
| `name` | Human-readable app name |
| `version` | App version |
| `description` | Short summary |
| `type` | Runtime type such as `docker`, `nodejs`, `python`, or `native` |
| `entry` | Runtime entry point, script, binary path, or image tag |
| `permissions` | Requested capabilities such as `ui` and `audio` |
| `env` | Default environment variables |
| `args` | Argument list |
| `ui.icon` | Relative icon path |
| `ui.displayName` | UI-facing display name |
| `ui.screenUI` | Whether the app uses screen UI |

### Example

```json
{
  "id": "hello-cube-nodejs",
  "name": "HelloCube (Node.js)",
  "version": "1.0.0",
  "description": "A Node.js starter app that prints a greeting and simulates a chime.",
  "type": "nodejs",
  "entry": "src/index.js",
  "permissions": ["ui", "audio"],
  "env": {
    "GREETING": "Welcome to TheCube from Node.js!"
  },
  "args": [],
  "ui": {
    "icon": "assets/icon.png",
    "displayName": "HelloCube (Node.js)",
    "screenUI": true
  }
}
```

## Rich YAML manifest draft from Core

The Core example introduces a more operationally complete schema:

- `runtime` for language and execution hints
- `fs` for state directories and bind mounts
- `permissions` for network, IPC, database, hardware, time, files, and env
- `cgroups` for resource controls
- `secrets` for secret materialization
- `events` for publish/subscribe patterns

This format is better aligned with a managed app runtime and sandbox model.

## Current documentation guidance

- Use the JSON manifest for example-app docs and quickstarts.
- Use the richer YAML schema as the internal direction for future platform design.
- Avoid claiming that the richer schema is already the active production contract unless Core implementation confirms it.

## Sources

- Local: `AppExample-Docker/manifest.json`
- Local: `AppExample-NodeJS/manifest.json`
- Local: `AppExample-Python/manifest.json`
- Local: `AppExample-Native-CPP/manifest.json`
- Local: `AppExample-Native-CSharp/manifest.json`
- Local: `AppExample-Native-Go/manifest.json`
- Local: `AppExample-Native-Rust/manifest.json`
- Local: `Companion-TheCube---Core/src/apps/exampleApp.manifest.yml`
