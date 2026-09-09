# Flattened Northstar Task Migration Closeout

Status: complete; merged through PR `#21` after one review wave
Date: 2026-09-09
Updated: 2026-09-09
Owner: core-product
Task: `9dbdc492-61cf-488a-ab12-ecfa5244864d`
Handoff: `docs/handoffs/20260909-140500-flattened-task-switchover.md`
PR: `https://github.com/inflatable-cookie/signal/pull/21`
Merged commit: `109d04531707326c74f4309821c25c28125dcbc3`

## Summary

The one-time Northstar flattened-task migration is complete. The merged
documentation change compacted safely closed generations `g01`–`g10`, flattened
active `g11` into three top-level `g11.NNN` tasks, removed the old milestone and
`batch-cards/` execution hierarchy, and aligned the live front doors.

No product code, release state, workflow, provider setting, or planning
direction changed.

## Historic compaction

- `g01`–`g10` were classified safely closed and moved to non-procedural
  roll-ups under `docs/roadmaps/archive/`.
- The closed `g09` strict-lane spec moved to `docs/specs/archive/` unchanged.
- `g10.017` hardware depth was rehomed to the device-depth backlog.
- `g10.022`, `g10.023`, and `g10.025` were explicitly removed as superseded by
  the `g10.030` closure and frozen baseline.
- Material evidence remains in the retained logs, contracts, archived spec,
  handoffs, and the new archive roll-ups. Historical terminology was not
  modernized.

The preservation manifest is the merged migration diff: archive roll-ups
`g01.md`–`g10.md`, the archived `g09` spec, retained evidence paths, and the
explicit dispositions above. Deleted expanded trees are limited to the paths
represented by that manifest.

## Active-generation flattening

The old-to-new map is:

- `g11.001` absorbs former batch cards `001`–`003`.
- `g11.002` absorbs former batch cards `004`–`007`.
- `g11.003` absorbs former batch card `008`.

Each task file preserves its scope, governing refs, acceptance oracle,
validation, evidence, ownership, and stop conditions. The `g11` README is the
single roadmap and frontier. No active surface depends on milestone wrappers,
nested `batch-cards/`, or the removed milestone template.

## Review and validation

- Independent exact-head approval: review comment `5602676789` at
  `a17eada6c38d9e068244b5dabe1c825f849dbf35`.
- Round-1 findings were all resolved: Contract `001`'s old delivery grammar,
  its stale `g11.003` status, and residual future-facing card terminology.
- `effigy qa:docs`, `effigy qa:docs:links`,
  `effigy qa:docs:agent-defaults`, and `effigy qa:northstar` passed.
- `git diff --check` passed at the reviewed head.
- CI workflow run `34357365596` completed successfully at the reviewed head.
- The merge synchronized `main` at `109d04531707326c74f4309821c25c28125dcbc3`.

## Deferred limits

- The open PAPERCUTS entry on planning-authority pointer rot remains a future
  maintenance observation; it is not part of this closeout.
- Frozen historical records and generic vision/template language retain
  descriptive `milestone` terminology by design.
- No ready task remains. The approved next pointer is operator planning or
  backlog selection; do not open `g12` or infer a product pull.

## Next Task

Return to operator planning or backlog selection. Normal dispatch has not
resumed because the approved runway is empty.
