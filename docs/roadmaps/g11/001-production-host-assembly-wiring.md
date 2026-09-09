# g11.001 - Production Host-Assembly Wiring

Status: complete
Owner: core-product
Created: 2026-08-17
Depends on: g10 closeout (stretch audit complete)
Vision tags: `PLUGINS`, `RUNTIME`, `INTEGRATION`
Governing refs: `docs/contracts/072-real-plugin-hosting-discovery-and-sandbox-execution-contract.md`, `docs/contracts/009-shared-host-convenience-api-and-consumer-edge-contract.md`, `docs/contracts/014-plugin-isolation-policy-transport-rebind-and-shared-sandbox-continuity-contract.md`, `docs/architecture/system-inventory.md`, `docs/architecture/production-host-assembly-integration.md`

## Outcome

One honest assembly path from scan → placement → bridge backend →
render-plane execution for Loophole and other consumers, without
reconstructing test-only wiring. v1 supports `InProcess` and
`DedicatedSandbox`; `SharedSandbox` stays a typed rejection until `g11.002`.

## Problem

Signal already hosts CLAP, VST3, AU, and LV2 through adapter crates,
`signal-plugin-sandbox`, and `signal-plugin-bridge`. Proof lives in bridge,
sandbox, and render-plane tests.

`signal-host-local` still stops short of a production consumer path:

- discovery and sandbox broker exercises record runtime receipts
- bridge backends are not wired into the Pulse-facing host assembly end to end
- render-plane plugin stages are not driven from the host assembly in the
  canonical consumer path
- host crate docs still understate what is and is not wired today

## Goals

- [x] freeze the host-assembly integration contract: authority chain, placement
  tiers supported in v1 (`InProcess`, `DedicatedSandbox`), and explicit non-goals
- [x] add a host-owned bridge backend factory on `LocalRuntimeHost` that can
  load, activate, and hand out `RenderPluginProcessor` handles for CLAP, VST3,
  AU, and LV2
- [x] wire render-plane plugin stages through the host assembly for at least one
  offline proof path and one public host-edge proof path
- [x] refresh host crate docs, architecture inventory, and front doors so they
  describe integration seams accurately

## Non-Goals

- rebuilding adapter hosting from scratch
- SharedSandbox tier implementation (see `g11.002`)
- product browser, preset, or workflow UX
- Loophole mixer/layout policy or Chorus realization
- graph successor or device-depth backlog items

## Delivery record

Absorbed the former milestone batches and execution cards `001`–`003`
(bridge backend factory, render-plane consumer wiring, host-edge proof and
closeout) during the flattened-task migration; no scope changed.

- Integration contract freeze (docs-only): authority chain, v1 tiers, and
  non-goals frozen; map at
  `docs/architecture/production-host-assembly-integration.md`.
- Bridge backend factory on `LocalRuntimeHost`: host-owned construction for
  in-process CLAP/VST3/AU/LV2 plus `ShmPluginProcessor` construction bound
  to existing broker sessions for `DedicatedSandbox`; typed failures for
  unsupported tiers, layouts, and missing discovery records.
- Render-plane consumer wiring: at least one offline render-plane plugin
  stage driven from the host assembly with parameter/event/state handoff
  boundaries proved.
- Public host-edge proof and closeout: `signal-host-local` public tests
  exercise real bridge backends; `LocalRuntimeHost` crate docs and
  architecture front doors refreshed; milestone closed with the `g11.002`
  product-pull gate named.

## Acceptance Criteria

- [x] a consumer can follow one documented path from host assembly to real plugin
  audio through bridge backends
- [x] v1 explicitly supports `InProcess` and `DedicatedSandbox` only
- [x] `SharedSandbox` remains a typed rejection until `g11.002`
- [x] no doc surface claims plugin hosting is missing or discovery-only
- [x] public host-edge proof exists beyond broker attach/exercise metadata

## Risks and Mitigations

- Risk: host assembly becomes a second plugin authority beside runtime/contracts.
- Mitigation: keep placement, lifecycle, and supervisor meaning runtime-owned;
  host code stays orchestration and backend construction only.

- Risk: wiring only one format leaves a false "production ready" story.
- Mitigation: the factory batch requires all four adapter families.

- Risk: test-only wiring persists without consumer entry points.
- Mitigation: the closeout batch requires public host-edge proof on the same
  path the consumer wiring uses.

## Evidence

- Dispatch handoff: `docs/handoffs/20260817-160800-g11-001-host-assembly-wiring.md`
  (closed; retained as history, not authority).
- Batch logs: `docs/logs/2026-08/17-g11-001-batch-1-1-host-assembly-integration-map.md`
  through `17-g11-001-batch-1-4-host-edge-proof-and-closeout.md`.
- Validation recorded in the batch logs (`effigy validate`, targeted crate
  tests).

## Stop Conditions

- planning gaps, contract contradictions, or failed evidence gates stop the
  task; none remain open.

## Next Task

`g11.001` closed. Continued at `g11.002`
(`docs/roadmaps/g11/002-shared-sandbox-tier.md`).
