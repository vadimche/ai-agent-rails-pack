# Agent Workflow

## Phase 0 — Context scan

The agent reads:

- `AGENTS.md`;
- relevant docs;
- existing similar implementation;
- invariant register;
- issue/task description.

No code changes yet.

## Phase 1 — Change Intent

Agent writes the Change Intent:

- goal;
- scope;
- non-goals;
- affected files;
- constraints;
- invariants;
- test plan;
- rollback notes.

Human approves or edits.

## Phase 2 — Implementation

Agent implements the smallest useful change.

Rules:

- no unrelated refactoring;
- no broad rewrites;
- no dependency upgrades unless needed;
- no silent behavior changes.

## Phase 3 — Self-check

Agent compares diff against the approved Change Intent:

- Did we solve the stated problem?
- Did we touch only expected areas?
- Did we preserve invariants?
- Did we add/update tests?
- Is rollback possible?

## Phase 4 — Human review

Human uses `docs/human-approval-checklist.md`.
