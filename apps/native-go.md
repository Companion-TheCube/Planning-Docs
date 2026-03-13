# Native Go Example

## Source repo

`AppExample-Native-Go`

## Packaging model

- Manifest type: `native`
- Entry: `bin/hello-cube-go`
- Runtime requirement: Go 1.18+

## Build flow

- Run `build.sh`
- Compile `src/main.go`
- Output binary to `bin/hello-cube-go`

## Files of interest

- `build.sh`
- `src/main.go`
- `manifest.json`

## Notes

The Go example is a good fit for network-heavy tools, daemons, and cross-compiled utilities that should ship as a single binary.

## Open Items

- `Open question:` what the official cross-compilation and target-ABI guidance should be for Go apps.
- `Needs verification:` whether Go is considered an officially supported production runtime or only an example template at this stage.

## Sources

- Local: `AppExample-Native-Go/README.md`
- Local: `AppExample-Native-Go/build.sh`
- Local: `AppExample-Native-Go/manifest.json`
