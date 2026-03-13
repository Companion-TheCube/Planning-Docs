# App Server

## Purpose

`Companion-TheCube-AppServer` is intended to be the app catalog and distribution service for TheCube ecosystem. Its README describes a service that would:

- Provide metadata about available apps
- Store data in PostgreSQL
- Expose HTTP routes with Express
- Potentially render UI with server-side templates

Within the planned backend microservices architecture, this component is intended to become the app-distribution microservice rather than remain part of a monolithic backend.

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

## Open Items

- `Decision needed:` define the exact boundary between App Server and the main Server repo. Current direction: App Server focuses on app cataloging and distribution, while the main Server repo handles broader backend APIs and account/device concerns.
- `Open question:` decide whether this service remains a simple app catalog or expands into packaging, publishing, signing, and install/update workflows. Current direction: start as a catalog/distribution service first, then add deeper publishing and package-management features later if they are needed.
- `Needs verification:` the current README describes a more mature service than the code actually implements. Current interpretation: the README is aspirational and does not yet match the implementation status.

## Sources

- Local: `Companion-TheCube-AppServer/Readme.md`
- Local: `Companion-TheCube-AppServer/src/index.js`
- Local: `Companion-TheCube-AppServer/package.json`
