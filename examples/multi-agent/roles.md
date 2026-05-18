# Multi-Agent Workflow Roles

This is a minimal role split for teams using planner/builder/reviewer agents.

## Planner

Creates the Change Intent. Must not edit production code.

Outputs:

- problem statement;
- affected modules;
- non-goals;
- invariants;
- test plan;
- rollback notes.

## Builder

Implements only the approved Change Intent.

Rules:

- do not expand scope silently;
- reuse existing patterns;
- update tests/checks;
- produce a concise change summary.

## Reviewer

Checks the diff against the approved Change Intent.

Outputs:

- intent match / mismatch;
- scope creep;
- missing tests;
- invariant risk;
- rollback clarity;
- recommendation: approve, revise, or escalate to human.

## Human owner

Owns judgment and final approval. The agents produce structured evidence; they do not own production risk.
