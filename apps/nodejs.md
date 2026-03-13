# Node.js Example

## Source repo

`AppExample-NodeJS`

## Packaging model

- Manifest type: `nodejs`
- Entry: `src/index.js`
- Runtime requirement: Node.js 14+

## Behavior

The example app:

- Displays a greeting using `GREETING`
- Simulates audio playback with a printed chime
- Uses a simple `npm start` flow

## Files of interest

- `package.json`
- `src/index.js`
- `manifest.json`
- `assets/`

## Notes

This is the simplest script-based example and is a good fit for lightweight integrations or tools that benefit from JavaScript ecosystem support without containerization.

## Open Items

- `Open question:` what is the official support level for Node.js apps on target devices?
- `Needs verification:` dependency isolation, supervision, and packaging/publishing rules for Node.js apps are not yet concrete in this repo.

## Sources

- Local: `AppExample-NodeJS/README.md`
- Local: `AppExample-NodeJS/package.json`
- Local: `AppExample-NodeJS/manifest.json`
