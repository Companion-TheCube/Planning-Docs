# Python Example

## Source repo

`AppExample-Python`

## Packaging model

- Manifest type: `python`
- Entry: `src/main.py`
- Runtime requirement: Python 3.9+

## Behavior

The example app:

- Displays a greeting
- Plays or simulates a short chime
- Uses `pygame`
- Assumes some Core-provided SDK/runtime integration for device interaction

## Files of interest

- `src/main.py`
- `requirements.txt`
- `manifest.json`
- `assets/chime.wav`

## Notes

Python is a good candidate for rapid prototyping, AI-adjacent utilities, and integrations where packaging simplicity matters more than raw performance.

## Open Items

- `Needs verification:` whether the referenced `cube_sdk` is a real distributed runtime dependency or an aspirational placeholder in the example README. Current direction: build and distribute a Python SDK, but verify its actual implementation status before treating it as a real dependency.
- `Open question:` what the final packaging, dependency-management, and runtime-isolation policy for Python apps will be. Current recommendation: use `requirements.txt`-based dependency management for now, while later documenting stronger isolation guidance such as virtual environments or containerization if needed.

## Sources

- Local: `AppExample-Python/README.md`
- Local: `AppExample-Python/requirements.txt`
- Local: `AppExample-Python/manifest.json`
