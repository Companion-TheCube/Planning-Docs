# Privacy and Data

## Status

This is an explicit draft and gap document. A standalone Privacy Policy source document was not found during the first Drive pass.

What is available today:

- The product planning docs emphasize local-first processing and privacy as a core differentiator.
- The Terms of Service draft refers to a separate Privacy Policy.
- Core has TODOs to load and display a privacy policy from a file.
- The public docs site's cloud privacy page is currently a placeholder.

## Current privacy posture from available sources

### Product intent

TheCube is intended to favor:

- Local processing where feasible
- Optional cloud augmentation rather than mandatory cloud dependence
- Permission-gated hardware and data access

### Known cloud processing paths

The current server and terms drafts imply or state use of third-party processors for:

- LLM interactions
- Speech transcription
- Text-to-speech
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
3. Decide which data stays on-device versus which is transmitted off-device.
4. Replace the placeholder public docs page with the reviewed policy or a policy summary.

## Sources

- Drive: `Project Plan` (`1MGhYIrw1OeJNf3VE6GtfyWub_-aGOUIYPgzjNJoUXzg`)
- Drive: `Terms of Service (Draft)` (`18QYIVrWo9-3psN0YSRZE-vg5tu_SxR4ONWZF7nr7VNs`)
- Local: `Companion-TheCube---Core/TODO's.md`
- Local: `Companion-TheCube.github.io/cloud/data-privacy.md`
