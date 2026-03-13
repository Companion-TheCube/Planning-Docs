# Native C# Example

## Source repo

`AppExample-Native-CSharp`

## Packaging model

- Manifest type: `native`
- Entry: `bin/HelloCubeCSharp`
- Target framework: `.NET 6.0`
- Runtime identifier: `linux-x64`

## Build flow

- Use `dotnet publish`
- Produce a self-contained executable under `bin/`

## Files of interest

- `HelloCubeCSharp.csproj`
- `build.sh`
- `src/Program.cs`
- `manifest.json`

## Notes

This example shows that TheCube's native runtime model is language-agnostic as long as the app ultimately exposes a native executable and compatible manifest.

## Sources

- Local: `AppExample-Native-CSharp/README.md`
- Local: `AppExample-Native-CSharp/HelloCubeCSharp.csproj`
- Local: `AppExample-Native-CSharp/build.sh`
- Local: `AppExample-Native-CSharp/manifest.json`
