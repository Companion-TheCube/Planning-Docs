# Native C++ Example

## Source repo

`AppExample-Native-CPP`

## Packaging model

- Manifest type: `native`
- Entry: `bin/hello-cube`
- Build system: CMake

## Build flow

- Configure with CMake
- Build into `bin/hello-cube`
- Package with the manifest and assets

## Files of interest

- `CMakeLists.txt`
- `src/main.cpp`
- `manifest.json`
- `assets/icon.png`

## Notes

This is the most direct path for performance-sensitive native apps and is closest to the language and tooling already used by Core.

## Sources

- Local: `AppExample-Native-CPP/README.md`
- Local: `AppExample-Native-CPP/CMakeLists.txt`
- Local: `AppExample-Native-CPP/manifest.json`
