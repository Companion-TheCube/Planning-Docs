# Server

## Purpose

`Companion-TheCube-Server` is the cloud/server-side API prototype for the platform. Its documented and implemented responsibilities include:

- User auth
- Audio ingestion and remote speech recognition
- Remote intent detection and command interpretation
- Text-to-speech generation and audio response APIs
- LLM-backed chat/session handling
- Device registration and heartbeat
- Telemetry ingestion
- WebSocket-based streaming transcription
- A small admin/management surface

The target backend architecture is microservices. The long-term plan is to separate major functional areas such as auth, LLM, audio, device management, telemetry, and app distribution into independent services that can be deployed and scaled separately. The current repository is a monolithic prototype and should be treated as an intermediate implementation that will need to be rewritten to match that architecture.

## Current implementation

### Entry points

- `server.js`: Express + HTTP server bootstrap
- `wsServer.js`: WebSocket server for streaming transcription sessions

### Mounted route groups

- `/API/auth`
- `/API/audio`
- `/API/llm`
- `/API/user`
- `/API/device`
- `/API/telemetry`
- `/MANAGE`

### Other exposed endpoints

- `/health-check`
- `/signin`

## Implemented behavior by route group

### Auth

Current auth routes include:

- `POST /API/auth/login`
- `POST /API/auth/refresh` (TODO)
- `GET /API/auth/validate` (placeholder success path)
- `GET /API/auth/logout` (placeholder)

### Audio

Current audio routes include:

- `POST /API/audio/stream-in` returning `501 Not Implemented`
- `POST /API/audio/verify-wakeword`
- `POST /API/audio/command-interpret`
- `POST /API/audio/synthesize`

The implementation uses OpenAI for transcription/chat-style interpretation and AWS Polly for text-to-speech.

Architecture direction: these speech/intelligence capabilities stay server-side. Core should not perform on-device speech recognition, text-to-speech synthesis, or intent detection.

### LLM

Current LLM routes include:

- `POST /API/llm/session`
- `POST /API/llm/chat`

The code implements session creation, DynamoDB-backed session storage, and function-calling examples for `getCurrentTime` and `getDeviceStatus`.

### User

- `GET /API/user/profile`

### Device

- `POST /API/device/register`
- `POST /API/device/heartbeat`

### Telemetry

- `POST /API/telemetry/ingest`
- `GET /API/telemetry/view`

These routes are present but still appear incomplete. For example, the code references `timestream` without a visible local definition in the inspected route file.

## Data and infrastructure dependencies

The package manifest and source tree show dependencies on:

- AWS Cognito
- DynamoDB
- Polly
- Transcribe Streaming
- Timestream
- PostgreSQL client libraries
- OpenAI SDK
- Express, EJS, Winston, and WebSocket support

## Status assessment

This repo is beyond pure scaffolding, but it is still a prototype:

- Some endpoints are implemented enough to document concretely.
- Some are placeholders or partially wired.
- The Drive API spec describes a broader target API than the code currently exposes.

Any external-facing API documentation should therefore separate:

- Current code-backed behavior
- Draft/planned behavior from the Drive spec

## Open Items

- `Decision needed:` lock a stable external API shape, including route naming and whether `/API/...` remains the long-term prefix. Current direction: keep the `/API/...` prefix unless the microservices rewrite produces a clearer naming convention.
- `Needs verification:` telemetry, auth refresh, auth validation, and some admin behaviors are only partially implemented or rely on surrounding infrastructure not confirmed in this pass. Current status: development is ongoing, and the monolithic prototype is not yet a reliable indicator of the final service behavior.
- `Open question:` decide whether auth, LLM, audio, device, and telemetry remain in one service or split into separate deployable services over time. Current direction: split these areas into microservices. The unresolved part is the exact service boundary and how much consolidation, if any, remains appropriate after the rewrite.
- `Confirmed architecture:` speech recognition, intent detection, and text-to-speech are remote-server responsibilities; on-device Core should only capture audio, stream/request processing, and render/play responses.

## Sources

- Local: `Companion-TheCube-Server/server.js`
- Local: `Companion-TheCube-Server/wsServer.js`
- Local: `Companion-TheCube-Server/routes/api/*.js`
- Local: `Companion-TheCube-Server/package.json`
- Local: `Companion-TheCube-Server/Roadmap.md`
- Drive: `API Spec` (`1MRpHKmnv0gBC6W04ChiXAwaYl-vGiCHyDwbuDkOoI48`)
