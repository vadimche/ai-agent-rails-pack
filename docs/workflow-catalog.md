# Workflow Catalog

Use these workflows as copy-pasteable entry points.

## 1. Change Intent Gate

Use before implementation.

```text
Read AGENTS.md and templates/change-intent.md.
Do not modify code yet.
Write a Change Intent for this task.
Include affected files, non-goals, invariants, tests and rollback notes.
Wait for my approval.
```

## 2. Context Snapshot

Use when the repository is large or the agent is losing focus.

```text
Create a compact context snapshot for this task.
List only relevant files, existing patterns, nearby tests and invariants.
Exclude unrelated architecture commentary.
```

## 3. Scope Drift Check

Use after implementation.

```text
Compare the actual diff against the approved Change Intent.
Identify expected changes, unexpected changes, hidden refactors and tests still missing.
Return PASS, WARN or BLOCK.
```

## 4. Agent Handoff

Use when switching from planner to builder, builder to reviewer, or one AI session to another.

```text
Create an agent handoff.
Summarize task state, decisions, changed files, risks, tests and next steps.
Make it concise enough to paste into a new session.
```

## 5. Human Approval Gate

Use before merge, deploy or irreversible operation.

```text
Prepare a human approval checklist for this change.
Focus on invariants, tests, rollback, unexpected file changes and production risk.
```
