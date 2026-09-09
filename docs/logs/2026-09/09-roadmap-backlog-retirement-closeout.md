# Roadmap Backlog Retirement Closeout

Status: complete (pending review and merge)
Date: 2026-09-09
Owner: core-product
Task: `8f4cfe12-06cf-4028-b11e-a19428fdface`
Handoff: `docs/handoffs/20260909-151020-retire-roadmap-backlog.md`
Canonical authority: Northstar `retire-roadmap-backlog-prompt.md` (commit `b8ce1b0`, installed Northstar)

## Summary

The one-time Northstar roadmap-backlog retirement is applied. Every item
under `docs/roadmaps/backlog/` has a truthful disposition below, the backlog
surface is deleted, and current project docs agree that roadmaps contain
promoted executable tasks while triage holds unresolved or deferred
candidates until promotion.

No product code, release state, workflow, dependency, provider setting,
product behavior, generation rollover, or task execution changed.

## Disposition manifest

| Backlog file | Classification | Canonical destination |
| --- | --- | --- |
| `post-g04-consumer-release-and-backend-breadth.md` | Promoted (into `g05` on 2026-03-12) | Generation record `docs/roadmaps/generation-index.md` (`g05` row); removed without placeholder |
| `post-g05-publication-promotion-and-shared-acceptance-depth.md` | Promoted (into `g06` on 2026-03-13, narrowed) | Generation record (`g06` row); removed without placeholder |
| `post-g06-chorus-feature-expansion-and-g07-candidate-suite.md` | Promoted (into `g07` on 2026-03-16; criteria checked) | Generation record (`g07` row); removed without placeholder |
| `post-g08-repeated-run-environment-matrices-and-downstream-workflow-depth.md` | Deferred candidate | `docs/triage/20260909-retired-backlog-post-g08-environment-matrices.md` |
| `post-g10-rebuild-on-demand.md` (shipped plugin baseline, `g11.001`, `g11.002` sections) | Implemented / superseded | Contract `072` plus architecture docs (already authoritative); removed without placeholder |
| `post-g10-rebuild-on-demand.md` (engine server, device depth, SRC, beat tracking, graph successor, multichannel, product shells) | Deferred candidates | `docs/triage/20260909-retired-backlog-post-g10-rebuild-on-demand.md` |
| `README.md`, `backlog-item-template.md` | Live scaffolding | Deleted; roadmaps hold executable tasks, triage holds candidates |

No approved executable work was merged into an owning `gNN.NNN` task: there
is no ready task and no active lane, and migration is not approval. No
durable rule needed promotion: the strategic runway already owns the
product-pull bets and now points at the triage notes.

## Files changed and deleted

Deleted: `docs/roadmaps/backlog/` (6 files: `README.md`,
`backlog-item-template.md`, and the four `post-gNN` items above).

Repointed or retuned from roadmap backlog to triage: `docs/roadmaps/README.md`,
`docs/roadmaps/strategic-runway.md`, `docs/roadmaps/generation-index.md`,
`docs/roadmaps/g11/README.md`, `docs/README.md`,
`docs/contracts/001-working-rules.md`, `docs/contracts/007-*.md`,
`docs/contracts/011-*.md`, `docs/contracts/071-*.md`,
`docs/architecture/system-architecture.md`, `docs/architecture/README.md`,
`docs/architecture/retired-boundary-descriptions.md`,
`docs/architecture/production-host-assembly-integration.md`,
`docs/architecture/shared-sandbox-multiplexing.md`,
`docs/architecture/graph-runtime-feature-reference.md`,
`docs/triage/README.md`,
`docs/triage/20260829-224753-stale-next-task-pointers.md`,
`docs/logs/templates/roadmap-currentness-triage-template.md`.

Added: the two triage notes above plus this closeout log.

## Retained historical exceptions

Unchanged on purpose: archived generation roll-ups (`docs/roadmaps/archive/`),
historical batch logs, closed handoffs, closed `g11.NNN` task records, and the
generic runtime-scheduler vocabulary (`backlog class`, `backlog pressure` in
prework/supervisor surfaces) plus Soundcheck-owned backlog references in
Contracts `086`/`087`, which name another project's intake rather than
Signal's retired roadmap surface.

## Current approved frontier

Unchanged: `g11.001`, `g11.002`, and `g11.003` complete; no ready task; do
not open `g12`. Deferred work waits in triage for operator-selected product
pull.

## Next Task

Merge this PR through normal review, then synchronize `main` and retire the
cleanup workspace via Northstar Queue.
