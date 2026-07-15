# Agent Instructions

Read `CONTEXT.md` and `docs/UPSTREAM-WORKFLOW.md` before changing this repository.

## Branch authority

- `main` is an exact mirror of `OpenWhispr/openwhispr:main`. Do not put TheHive
  Voice-only commits on it.
- `product` is the TheHive Voice integration branch and default pull-request
  target for product work.
- A change intended for OpenWhispr upstream starts from `main` and must remain
  independent of TheHive Voice-only code.

## Worktree discipline

- Use the fewest worktrees possible.
- Create one only for a long-lived or concurrent implementation lane.
- One worktree owns one branch. Never share a branch between worktrees.
- Read-only investigation and short reviews stay in the current worktree.
- Remove completed worktrees after their commits are integrated and proven.

## Proof discipline

- Focused edit loops run locally.
- Broad or CI-parity checks use Crabbox when configured.
- Every Crabbox claim names the actual provider, lease ID, command, and result.
- Do not claim a queued, unavailable, or stale remote box as proof.
- Do not run signing, notarization, release publication, microphone capture, or
  live credential-backed routes without explicit operator approval.

## Product invariants

- Keep working dictation functional while adding new modes.
- No silent provider, model, transport, or agent fallback.
- Local, tailnet, BYOK, and managed routes remain explicit user choices.
- Agent action requires visible authority, state, stop, and recovery controls.
- Do not describe planned iOS/watchOS/realtime/agent functionality as shipped.
