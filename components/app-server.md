# App Server

## Purpose

`Companion-TheCube-AppServer` is intended to be the app catalog and distribution service for TheCube ecosystem. Its README describes a service that would:

- Provide metadata about available apps
- Store data in PostgreSQL
- Expose HTTP routes with Express
- Potentially render UI with server-side templates

## Current implementation

The current codebase is significantly simpler than the README description:

- Single Express entry point in `src/index.js`
- ESM-based Node project
- In-memory `apps` array
- Routes:
  - `GET /`
  - `GET /apps`
  - `GET /apps/:name`
- StdIn handling for an `exit` command
- Large TODO list for auth, testing, logging, caching, messaging, tracing, file upload, and documentation

## Package and runtime notes

- Runtime: Node.js
- Module system: ESM (`"type": "module"`)
- Current dependencies: `express`, `jsonwebtoken`, `pg`, `winston`
- Startup command: `node --env-file=.env src/index.js`

## Documentation stance

This component should be documented as an early prototype for app distribution, not as a finished marketplace or production app store.

Useful current takeaways:

- The service exists as a separate concern from the main cloud/server repo.
- It already has the right conceptual boundary: app listing and distribution metadata.
- It still needs real persistence, auth, packaging rules, and deployment guidance.

## Sources

- Local: `Companion-TheCube-AppServer/Readme.md`
- Local: `Companion-TheCube-AppServer/src/index.js`
- Local: `Companion-TheCube-AppServer/package.json`
