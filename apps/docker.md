# Docker Example

## Source repo

`AppExample-Docker`

## Packaging model

- Manifest type: `docker`
- Entry: Docker image reference (`hello-cube-docker:latest`)
- Runtime entrypoint inside the image: `main.sh`

## Behavior

The example:

- Reads a `GREETING` environment variable
- Prints a greeting
- Simulates a chime message
- Sleeps briefly to emulate playback time

## Files of interest

- `Dockerfile`
- `main.sh`
- `manifest.json`
- `assets/`

## Notes

This is the clearest example of containerized app packaging for TheCube and is a useful template for isolated or dependency-heavy apps.

## Sources

- Local: `AppExample-Docker/README.md`
- Local: `AppExample-Docker/Dockerfile`
- Local: `AppExample-Docker/main.sh`
- Local: `AppExample-Docker/manifest.json`
