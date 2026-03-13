# Native Rust Example

## Source repo

`AppExample-Native-Rust`

## Packaging model

- Manifest type: `native`
- Entry: `bin/hello-cube-rust`
- Build system: Cargo

## Build flow

- Run `cargo build --release`
- Copy the built binary into `bin/`
- Package with `manifest.json`

## Files of interest

- `Cargo.toml`
- `build.sh`
- `src/main.rs`
- `manifest.json`

## Notes

The Rust example demonstrates a path for safe native apps that still deploy as standalone binaries within the same Core app-launching model.

## Open Items

- `Open question:` whether Rust is officially supported as a first-class app runtime or just represented by an example. Current direction: treat Rust as a first-class runtime in v1, while continuing to validate demand and support burden.
- `Needs verification:` whether Cargo-produced artifacts need additional wrapper metadata, signing, or install-time preparation beyond the current example.

## Sources

- Local: `AppExample-Native-Rust/README.md`
- Local: `AppExample-Native-Rust/Cargo.toml`
- Local: `AppExample-Native-Rust/build.sh`
- Local: `AppExample-Native-Rust/manifest.json`
