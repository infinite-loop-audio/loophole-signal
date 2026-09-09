# g11.003 - Northstar Instruction And Rust Quality Audit

Status: complete; merged through PR `#18` after one review wave
Owner: core-product
Created: 2026-08-31
Updated: 2026-09-01
Depends on: g11.002
Vision tags: `QUALITY`, `MAINTAINABILITY`, `REALTIME`
Governing refs: `AGENTS.md`, `docs/contracts/001-working-rules.md`, `docs/contracts/rust-quality-profile.json`, `docs/contracts/rust-quality-deviations.json`, `docs/architecture/system-architecture.md`, `docs/architecture/product-guardrails.md`

## Outcome

One repository-scope Northstar instruction and strict Rust audit with only
pre-authorized finding-first repairs, landed through one reviewable PR with
complete preservation and validation evidence. No product behavior, no new
generation.

## Problem

Signal's instruction surface was refreshed before the latest host and sandbox
work, and its Rust workspace has not been assessed as one repository-scope
Northstar explicit audit. The repository needs a current reader-journey review
and a finding-first Rust audit without turning maintenance into a product or
architecture rewrite.

## Goals

- audit and, where justified, tighten `AGENTS.md` and the root `CLAUDE.md`
  bridge while preserving Signal's project-specific boundaries
- assess every owned Rust package under Northstar's strict explicit-audit
  projection at the declared Rust 1.95 MSRV
- repair only recorded `review_required` findings inside the audit recorder's
  owned units
- leave report-only, unsafe, public-contract, foreign-error, version-policy,
  and other operator decisions visible rather than silently changing them
- finish with one reviewable PR and deterministic audit evidence

## Non-Goals

- opening `g12` or selecting a product backlog item
- redesigning realtime, plugin, IPC, hardware, or public API contracts
- blanket formatting, blanket lint fixing, dependency upgrades, or god-file
  demolition by threshold
- treating the AGENTS checker, Clippy, stopslop, or line counts as prose or
  architecture verdicts
- changing `.github/workflows/` or running release mutations

## Delivery record

Absorbed the former execution card `008` (Northstar AGENTS and Rust audit)
during the flattened-task migration; no scope changed. Card `008` ran as one
worker lane:

- reviewed the full instruction reader journey and exact Claude bridge
- initialized the Rust audit recorder before source mutation
- partitioned all workspace crates into disjoint architecture-aligned units
- ran correctness, architecture, and human-quality assessments for every unit
- applied only bounded recorder-authorized repairs, then finalized evidence
  and reconciled the planning/log surfaces

## Acceptance Criteria

- the AGENTS disposition covers every section and records preserved intent,
  before/after measurements, and the bridge result
- the Rust recorder covers the complete Cargo package/target/feature inventory,
  public APIs, unsafe/FFI, async/concurrency, realtime, and foreign-boundary risk
- every normative Rust rule has a verdict for every audit unit; every exact
  forwarder candidate has an explicit retain or report-only disposition
- only `review_required` repairs authorized before mutation change source;
  report-only and operator-decision surfaces remain unchanged
- Rust 1.95 floor evidence and repository-native current-toolchain validation
  are recorded honestly, including unavailable or warning-bearing evidence
- docs, task, log, and front doors agree on the result and next state

## Review Oracle

Invariant: the audit may improve instructions and recorder-authorized Rust
quality without weakening realtime safety, plugin isolation, public API/error
semantics, MSRV, or the audit's finding-first evidence chain.

Smallest adversarial counterexamples:

- a source edit appears before its unit assessment and repair plan
- an unsafe/FFI or public-contract finding is repaired under ordinary audit
  authority
- a passing newest-toolchain run is presented as proof of Rust 1.95 support
- one workspace crate, public surface, exact forwarder, or excluded file has no
  recorded disposition
- AGENTS becomes shorter by dropping a safety, authority, worktree, or
  completion boundary

Expected response: the worker stops before the unauthorized mutation or the
review rejects the PR. Required proof is the finalized recorder report,
changed-file attribution, preservation hashes, exact command evidence, AGENTS
section map, and clean final diff.

## Result

Audit `signal-g11-003-repository-audit` covered all 28 crates in 14 units at
status `degraded`: 89 recorder-authorized repairs applied (28 `RUST-MSRV-001`,
47 `RUST-API-001`, 14 `RUST-ERR-001`) and 8 `RUST-UNSAFE-001` findings left
report-only. `AGENTS.md` kept all eight sections and every boundary;
`CLAUDE.md` is unchanged. Required local validation all exits 0.
Evidence: `docs/logs/2026-08/31-g11-003-northstar-agents-rust-audit-closeout.md`.

One review wave followed orchestrator review. Linux CI falsified the first-wave
`AuProcessSession` `Debug` repair, because the recorder's `plugin-formats`
evidence was collected host-local on macOS and never compiled that `cfg`-split
public type's non-macOS shape. The corrected file is a review-wave change outside
the finalized recorder hashes; the sealed result stands unmodified. This is the
task's own acceptance criterion working — validation exposed a defect and the
limitation is now recorded rather than papered over.

Two follow-ups were surfaced and deliberately not opened: the unsafe-hardening
lane (214 undocumented unsafe blocks, an operator decision under this rule's
report-only authority) and the `missing_errors_doc` backlog (222 sites, an
evaluation-only lint that grants no repair authority).

## Stop Conditions

- the recorder cannot resolve or preserve repository scope
- a repair needs a new public API, foreign error, realtime, unsafe/FFI,
  compatibility, dependency, or version-policy decision
- a missing external contract prevents an honest assessment
- validation changes the plan or exposes work outside this maintenance lane

## Next Task

Return to operator planning or backlog selection. There is no ready task; do
not infer another product or maintenance batch.
