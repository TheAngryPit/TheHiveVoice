# Upstream, Product, Worktrees, and Crabbox

## Why two persistent branches exist

The repository needs two truths that cannot occupy the same branch:

- an exact, low-friction mirror of OpenWhispr upstream;
- a branded product branch with different docs, policy, UI, and features.

Therefore `main` mirrors upstream and `product` is the default TheHive Voice
branch. This avoids pretending a customized `main` is still identical upstream.

## Upstream synchronization

The canonical remotes in a maintainer checkout are:

```bash
git remote add upstream https://github.com/OpenWhispr/openwhispr.git
git fetch upstream
git switch main
git merge --ff-only upstream/main
git push origin main
```

Then open a reconciliation pull request from a temporary branch based on the new
`main` into `product`. Resolve product conflicts there. Do not copy files between
branches manually and do not force-push either persistent branch.

## Choosing the contribution lane

| Change | Base | Pull request target |
| --- | --- | --- |
| Generic OpenWhispr bug fix | `main` | `OpenWhispr/openwhispr:main` |
| TheHive Voice product feature | `product` | `TheAngryPit/TheHiveVoice:product` |
| Upstream reconciliation | updated `main` | `TheAngryPit/TheHiveVoice:product` |
| Release preparation | `product` | `TheAngryPit/TheHiveVoice:product` |

A product fix may later be extracted into a clean branch from `main` if it proves
generally useful upstream.

## Minimal worktree policy

The default is one active product worktree. Add another only when work must remain
isolated while another implementation continues.

Good reasons:

- a long-running upstream pull request;
- a risky UI migration that must not mix with runtime work;
- release stabilization while product development continues.

Bad reasons:

- reading code;
- running one review;
- giving a subagent a small bounded question;
- avoiding a normal branch switch.

Create worktrees outside the repository directory, name them after the branch,
and remove them after integration. Never attach the same branch to two worktrees.

## Local and remote proof

Local checks are the fast feedback loop:

```bash
npm test
npm run typecheck
npm run lint
npm run format:check
```

Crabbox is for broad tests, CI parity, packaged/native lanes, or checks too heavy
for the operator Mac. It is orchestration, not a generic project manager.

Before claiming Crabbox proof, record:

- provider (`aws` or `blacksmith-testbox`);
- lease ID (`cbx_...` or `tbx_...`);
- synchronized commit;
- exact command and exit code;
- cleanup state for one-shot or retained leases.

The repository does not yet include a Crabbox wrapper or provider configuration.
That integration is a separate, reviewable infrastructure change. Until it lands,
CI and focused local checks are the available proof surfaces.

## Release boundary

Inherited release workflows reference upstream assumptions and secret material.
Do not tag or publish TheHive Voice from them until signing, notarization,
artifacts, update channels, provenance, and rollback are defined for this fork.
