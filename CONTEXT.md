# TheHive Voice Context

## Current truth

This repository is a public MIT fork of OpenWhispr. The inherited Electron/React
desktop application is the functional baseline. TheHive Voice product work is at
foundation stage and has no release yet.

## Branches

- `main`: upstream mirror, not the product integration branch.
- `product`: TheHive Voice integration and default contribution branch.

## Product goal

Build a local-first voice operating layer that can act as dictation, TTS,
realtime conversation, or a governed interface to user-selected agents. macOS is
the first complete product; iOS and watchOS are continuity surfaces afterward.

## Near-term sequence

1. Preserve and prove the inherited desktop baseline.
2. Establish fork workflow, security, and CI truth.
3. Migrate the UI primitive layer deliberately, with visual regression proof.
4. Add explicit voice modes and routing contracts.
5. Add agent authority and computer-control surfaces behind visible approvals.
6. Build native Apple continuity clients after desktop contracts stabilize.

## Non-authority

OpenWhispr Cloud, its website, sponsors, signing credentials, release artifacts,
and operational guarantees do not become TheHive Voice infrastructure by fork.
