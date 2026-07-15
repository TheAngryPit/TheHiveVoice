# Security Policy

## Current support status

TheHive Voice has not published a supported release. Security reports are still
welcome for code on the `product` branch and for fork-specific changes. Issues
that reproduce unchanged on `main` should also be reported to OpenWhispr through
its own security process.

## Reporting a vulnerability

Do not open a public issue for a suspected vulnerability.

Use GitHub private vulnerability reporting for
[`TheAngryPit/TheHiveVoice`](https://github.com/TheAngryPit/TheHiveVoice/security/advisories/new).
Include the affected commit, platform, reproduction steps, impact, and whether
the issue also reproduces on upstream OpenWhispr.

Do not include live API keys, OAuth tokens, recordings, personal transcripts, or
other user data in the report. Use synthetic evidence and redact logs.

We do not publish a response-time or remediation-time guarantee before the first
supported release.

## Scope

Security-sensitive surfaces include:

- microphone, system-audio, accessibility, and automation permissions;
- native key listeners, paste helpers, and packaged binaries;
- Electron main/renderer/preload boundaries and IPC;
- local loopback APIs, agent routes, and remote/tailnet connections;
- API keys, OAuth tokens, provider credentials, and local databases;
- crafted audio, transcripts, model output, and imported content;
- dependency, build, update, signing, and release supply chains.

## Fork boundary

`main` is the upstream mirror. `product` contains TheHive Voice integration work.
TheHive Voice does not inherit OpenWhispr Cloud operations, sponsor relationships,
security contacts, signing identities, or release guarantees merely because the
source is forked.
