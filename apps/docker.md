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

## Open Items

- `Open question:` are Docker apps intended to be first-class in v1 or mainly a convenience/example path? Current direction: support Docker as a first-class packaging option in v1 alongside native executables.
- `Needs verification:` the install, update, trust, and security model for container image distribution is not yet documented here. Current direction: use a trusted Docker registry for official apps and document signing/verification expectations for third-party images.

## Sources

- Local: `AppExample-Docker/README.md`
- Local: `AppExample-Docker/Dockerfile`
- Local: `AppExample-Docker/main.sh`
- Local: `AppExample-Docker/manifest.json`
