# g11.002 - SharedSandbox Tier

Status: complete
Owner: core-product
Created: 2026-08-17
Updated: 2026-08-17
Depends on: g11.001
Vision tags: `PLUGINS`, `SANDBOX`, `RECOVERY`
Governing refs: `docs/contracts/014-plugin-isolation-policy-transport-rebind-and-shared-sandbox-continuity-contract.md`, `docs/contracts/072-real-plugin-hosting-discovery-and-sandbox-execution-contract.md`, `docs/architecture/shared-sandbox-multiplexing.md`, `docs/architecture/production-host-assembly-integration.md`

## Outcome

`SharedSandbox` shipped: one broker child hosts many plugin instances that
share a grouping key (v1 grouping is plugin type identity), reusing
`ShmPluginProcessor` per member lease with no new audio-thread backend.
Products with several compatible plugin instances under one sandbox boundary
no longer pay one child process per plugin when runtime placement selects
`SharedSandbox`.

## Problem

Signal models three isolation tiers in `PluginIsolationTier`:

- `InProcess`
- `DedicatedSandbox` — shipped; one plugin per broker child
- `SharedSandbox` — one broker child, many plugin instances that share a
  grouping key

## Research posture

**No separate research lane is required.** Contract `014` owns semantics.
The multiplexing map is frozen at
`docs/architecture/shared-sandbox-multiplexing.md`.

## Goals

- [x] implement SharedSandbox in `signal-plugin-sandbox` broker multiplexing
- [x] reuse `ShmPluginProcessor` per member lease (no new audio-thread backend)
- [x] prove multi-instance continuity and terminal blast radius through runtime
  receipts and focused tests
- [x] integrate SharedSandbox selection through the `g11.001` host assembly

## Non-Goals

- [x] changing Contract `014` isolation vocabulary
- [x] product browser or trust UX
- [x] replacing DedicatedSandbox as the default isolation tier
- [x] vendor certification matrices
- [x] vendor/format grouping (v1 grouping is plugin identity only)

## Delivery record

Absorbed the former milestone batches and execution cards `004`–`007`
(multiplexing design note, broker multiplexing, host-assembly integration,
continuity proof and closeout) during the flattened-task migration; no scope
changed. Operator product pull 2026-08-17.

- Multiplexing design note (docs-only): broker multiplexing documented
  against Contract `014`; proof surfaces and stop conditions named; no new
  contract needed.
- Broker multiplexing: sandbox broker extended to host multiple plugin
  instances in one child (`load-plugin-instance`, `activate-instance`,
  `unload-plugin-instance`; omitted `instance_id` still means `sandbox_id`);
  DedicatedSandbox single-slot behavior unchanged; crash attribution per
  Contract `014` preserved.
- Host-assembly integration: `PluginIsolationTier::SharedSandbox` routed
  through the `g11.001` factory — find or spawn the broker session for
  grouping key `plugin:{plugin_type_id}`, allocate a unique `instance_id`,
  return two `ShmPluginProcessor` handles for two prepares of the same type.
- Continuity proof and closeout: Contract `014` shared-boundary blast radius
  proved on runtime receipts (child death and terminal outcomes visible for
  every member); Contract `072` remaining-gaps table updated; SharedSandbox
  no longer described as unimplemented.

## Acceptance Criteria

- [x] runtime placement can select SharedSandbox without host-local heuristics
- [x] one shared boundary failure is explainable through runtime-owned receipts
  for all member instances
- [x] DedicatedSandbox behavior remains unchanged for existing paths
- [x] docs no longer describe SharedSandbox as "unimplemented" without pointing
  at this task and Contract `014`

## Risks and Mitigations

- Risk: shared boundary hides per-plugin crash isolation.
- Mitigation: keep DedicatedSandbox as default; SharedSandbox only via explicit
  runtime placement policy.

- Risk: broker multiplexing reintroduces synthetic lifecycle behavior.
- Mitigation: require the same real `process()` and transport proof bar as
  DedicatedSandbox.

## Evidence

- Dispatch handoff: `docs/handoffs/20260817-185000-g11-002-shared-sandbox.md`
  (closed; retained as history, not authority).
- Batch logs: `docs/logs/2026-08/17-g11-002-batch-2-0-multiplexing-design-note.md`
  through `17-g11-002-batch-2-3-continuity-proof-and-closeout.md`.
- Continuity proof references Contract `014` rules explicitly.

## Stop Conditions

- planning gaps, contract contradictions, or failed evidence gates stop the
  task; none remain open.

## Next Task

`g11.002` closed. Stop for operator review; do not start a follow-on
generation from this task.
