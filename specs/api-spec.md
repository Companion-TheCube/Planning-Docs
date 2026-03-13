# API Spec

## Status

This is a cleaned draft that combines:

- The Drive `API Spec` document
- The currently implemented routes in `Companion-TheCube-Server`
- The local Core API notes in `Companion-TheCube---Core`

The important distinction is that not every endpoint in the Drive spec exists in code yet.

## API surfaces in the project

### 1. Device-local Core API

The Core repo documents a local REST-style API reached through `TheCube.local` or `localhost`, then exposed on port `55280` or a Unix socket.

Documented interface groups include:

- AudioManager
- CubeAuth
- CubeDB
- Bluetooth
- GUI
- Notifications
- PersonalityManager
- Logger

### 2. Cloud/server API

The server repo currently mounts these route groups:

- `/API/auth`
- `/API/audio`
- `/API/llm`
- `/API/user`
- `/API/device`
- `/API/telemetry`

It also exposes a WebSocket transcription flow.

## Currently implemented cloud/server endpoints

| Endpoint | Status | Notes |
| --- | --- | --- |
| `POST /API/auth/login` | Implemented | Username/password login against DynamoDB-backed user lookup |
| `POST /API/auth/refresh` | Placeholder | Present but TODO |
| `GET /API/auth/validate` | Placeholder | Returns `200` on auth middleware pass |
| `GET /API/auth/logout` | Placeholder | Stub response |
| `POST /API/audio/stream-in` | Stub | Returns `501 Not Implemented` |
| `POST /API/audio/verify-wakeword` | Implemented | STT then wake-word detection |
| `POST /API/audio/command-interpret` | Implemented | STT then LLM interpretation |
| `POST /API/audio/synthesize` | Implemented | AWS Polly TTS, streaming or base64 response |
| `POST /API/llm/session` | Implemented | Creates chat session |
| `POST /API/llm/chat` | Implemented | Chat with optional function-calling behavior |
| `GET /API/user/profile` | Implemented | Returns user profile |
| `POST /API/device/register` | Implemented | Registers device |
| `POST /API/device/heartbeat` | Implemented | Updates heartbeat |
| `POST /API/telemetry/ingest` | Partial | Route exists; implementation references external Timestream client assumptions |
| `GET /API/telemetry/view` | Partial | Route exists; admin-only intent |

## Drive-draft cloud/server endpoints

The Drive API draft describes a broader target surface, including:

- `POST /auth/refresh`
- `POST /auth/validate`
- `POST/GET /chat/RANDOM`
- `POST /audio/transcribe`
- `GET /audio/cancelTranscribe`
- `POST /audio/stream`
- `POST /command/interpret`
- `GET /api/test`
- `GET /user/profile`
- `POST /device/register`
- `POST /audio/synthesize`
- `POST /device/heartbeat`
- `POST /telemetry/logs`

## Divergences between draft and code

### Route naming

- Drive draft uses paths like `/auth/refresh` and `/audio/stream`.
- Current code mounts route groups under `/API/...`.

### Chat flow

- Drive draft uses a polling workflow on `/chat/RANDOM`.
- Current code uses `/API/llm/session` plus `/API/llm/chat`.

### Audio flow

- Drive draft proposes explicit transcribe/stream/cancel endpoints.
- Current code provides wake-word verification, command interpretation, and TTS, plus a stub streaming route.

### Telemetry

- Drive draft names `/telemetry/logs`.
- Current code uses `/API/telemetry/ingest` and `/API/telemetry/view`.

## Documentation guidance

- Treat the current route files as the source of truth for implemented behavior.
- Treat the Drive API spec as the intended target direction.
- Keep both documented until the server repo is aligned to one stable API contract.

## Open issues

- Auth refresh and validation are not fully implemented.
- Some route files appear to reference missing or externally defined objects.
- The Drive draft still contains TODO markers and unfinished endpoint planning.
- The Core local API and the cloud/server API need a clearer contract boundary in future revisions.

## Open Items

- `Decision needed:` select one stable API contract and naming scheme for the cloud/server surface.
- `Open question:` define the exact boundary between device-local Core APIs and remote/cloud APIs.
- `Needs verification:` determine which draft endpoints will be kept, renamed, replaced, or removed as implementation catches up.

## Sources

- Drive: `API Spec` (`1MRpHKmnv0gBC6W04ChiXAwaYl-vGiCHyDwbuDkOoI48`)
- Local: `Companion-TheCube-Server/server.js`
- Local: `Companion-TheCube-Server/routes/api/*.js`
- Local: `Companion-TheCube-Server/wsServer.js`
- Local: `Companion-TheCube---Core/src/api/readme.md`
