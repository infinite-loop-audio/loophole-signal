# <NNN> - <Task Title>

**Type: TEMPLATE** -- Copy to `docs/roadmaps/gNN/NNN-<slug>.md` and fill in for each Northstar task (`gNN.NNN`).

Status: draft
Owner: <owner>
Created: YYYY-MM-DD
Governing refs: <architecture files>, <contract files>
Depends on: <gNN.NNN or none>
Vision tags: `<TAG1>`, `<TAG2>`

## Outcome

State the exact bounded outcome for this task.

## Problem

Describe the specific short-term problem this task solves.

## Goals

- [ ] <goal 1>
- [ ] <goal 2>

## Non-Goals

- explicit non-goals; what this task will not do

## Work

1. <ordered step>
2. <ordered step>

## Acceptance Criteria

- [ ] <criterion 1>
- [ ] <criterion 2>

## Risks and Mitigations

- Risk: <risk>
- Mitigation: <mitigation>

## Review Oracle

Required when acceptance is high-risk, universal, exact, or negative;
otherwise state explicitly that it is not required.

Invariant: <claim the work must preserve>.

Smallest adversarial counterexamples:

- <smallest falsifying case>

Expected response: the worker stops before the unauthorized mutation or the
review rejects the PR. Required proof: <test/check/evidence>.

## Evidence Requirements

- [ ] <log or artifact for closeout>
- [ ] <manual validation checks and commands actually run>
- [ ] <if new checker script is proposed, record owner + cadence + sunset trigger>

## Stop Conditions

- stop on planning gaps, contract contradictions, or failed evidence gates
- ask for operator intent if an unresolved planning branch or generation choice appears

## Evidence

On completion, record: outcome, validation actually run, PR link, reviewed
exact head, merge commit, and material limits or blockers.

## Next Task

State the next ready task or promotion step unlocked by this task, or where
operator planning resumes.
