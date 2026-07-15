# Contributing to TheHive Voice

TheHive Voice has two contribution lanes. Choose the lane before editing so a
useful upstream fix is not trapped inside product-only work.

## 1. Upstreamable OpenWhispr work

Use this lane for a focused bug fix or improvement that applies to OpenWhispr
without TheHive Voice dependencies.

1. Branch from `main`.
2. Keep the change independent of TheHive Voice product code.
3. Run the focused local checks and the upstream-required checks.
4. Open the pull request against `OpenWhispr/openwhispr:main`.
5. Reconcile the accepted upstream change back through the normal upstream sync.

## 2. TheHive Voice product work

Use this lane for Apple continuity, TheHive-specific UX, agent routing, governed
device control, product policy, or integrations that are not yet upstream-ready.

1. Branch from `product` using a short descriptive branch name.
2. Keep one coherent product slice per pull request.
3. Target `TheAngryPit/TheHiveVoice:product`.
4. State which behavior is inherited, changed, and newly introduced.
5. Include proof and explicit remaining gaps.

## Worktrees

Use one worktree only for a long-lived or concurrently active implementation
lane. Do not create a worktree for read-only exploration or a brief review. Each
worktree owns exactly one branch and is removed after the pull request is merged
or abandoned.

See [`docs/UPSTREAM-WORKFLOW.md`](../docs/UPSTREAM-WORKFLOW.md).

## Local setup and checks

```bash
nvm use
npm ci
npm test
npm run typecheck
npm run lint
```

Use `npm run format:check` before requesting final review. Avoid `npm run format`
on a broad dirty tree because it mutates files.

Crabbox is the preferred remote surface for broad or CI-parity proof when it is
configured. Report its actual provider and lease ID. Do not describe an AWS
Crabbox lease and a Blacksmith Testbox-through-Crabbox run as the same backend.

## Pull requests

Every pull request should include:

- source branch and target lane;
- user-visible behavior changed;
- tests and commands run;
- proof level and known gaps;
- screenshots or recordings for UI changes;
- security/privacy impact for audio, permissions, credentials, or agent control.

## Issues and security

Use the repository issue templates for normal bugs and feature requests. Follow
[`SECURITY.md`](../SECURITY.md) for vulnerabilities; never file them publicly.
