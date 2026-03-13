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

- `Open question:` what the official cross-compilation and target-ABI guidance should be for Go apps. Current recommendation: use Go's built-in cross-compilation and prefer statically linked binaries for supported device targets such as Linux x86_64 and ARM64.
- `Needs verification:` whether Go is considered an officially supported production runtime or only an example template at this stage.

## Sources

- Local: `AppExample-Native-Go/README.md`
- Local: `AppExample-Native-Go/build.sh`
- Local: `AppExample-Native-Go/manifest.json`
