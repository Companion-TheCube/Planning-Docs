# Privacy and Data

## Status

This is an explicit draft and gap document. A standalone Privacy Policy source document was not found during the first Drive pass.

What is available today:

- The current architecture direction sets speech recognition, intent detection, and text-to-speech as remote-server processing paths.
- The Terms of Service draft refers to a separate Privacy Policy.
- Core has TODOs to load and display a privacy policy from a file.
- The public docs site's cloud privacy page is currently a placeholder.

## Current privacy posture from available sources

### Product intent

TheCube is intended to favor:

- Data minimization and strong transport security for remote AI operations
- Clear separation of local orchestration vs remote AI processing
- Permission-gated hardware and data access

### Known cloud processing paths

The current server and terms drafts imply or state use of third-party processors for:

- LLM interactions
- Speech transcription (remote)
- Intent detection/interpretation (remote)
- Text-to-speech (remote)
- Payment processing

### Known data categories

Based on current code and specs, the platform may process:

- Account and auth data
- Device identifiers and registration state
- Voice/audio input
- Transcripts and prompts
- AI outputs
- App metadata
- Telemetry
- Notification content

## Current documentation gap

A full privacy policy is still needed to define:

- Data collection categories
- Retention periods
- Local vs cloud processing rules
- Third-party processor list
- User rights and deletion flows
- Children's data rules
- Security practices
- Cross-border transfer language

## Recommended next steps

1. Locate or draft the missing standalone Privacy Policy.
2. Align the policy with actual Core/server data flows.
3. Define exact minimization rules for what audio/context is transmitted off-device for remote AI processing.
4. Replace the placeholder public docs page with the reviewed policy or a policy summary.

- `Decision needed:` create and approve the authoritative Privacy Policy.
- `Open question:` define exact transmission/retention rules for prompts, audio, telemetry, and app data now that voice AI is remote-server-owned.
- `Needs verification:` confirm the actual third-party processors and retained data categories from the current code paths.

## Sources

- Drive: `Project Plan` (`1MGhYIrw1OeJNf3VE6GtfyWub_-aGOUIYPgzjNJoUXzg`)
- Drive: `Terms of Service (Draft)` (`18QYIVrWo9-3psN0YSRZE-vg5tu_SxR4ONWZF7nr7VNs`)
- Local: `Companion-TheCube---Core/TODO's.md`
- Local: `Companion-TheCube.github.io/cloud/data-privacy.md`
