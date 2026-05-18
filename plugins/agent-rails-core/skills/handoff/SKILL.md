---
name: handoff
description: Create a compact handoff for another agent or human reviewer: task state, decisions, changed files, risks, tests and next steps.
argument-hint: '[current task context]'
---

# /handoff

Create a handoff when switching agents, pausing work, or asking a human to review.

## Instructions

1. Summarize the task and current state.
2. Record decisions already made.
3. List changed files and why they changed.
4. List known risks and uncertainties.
5. List tests run and results.
6. List next recommended steps.
7. Keep the handoff concise enough to paste into another agent session.

## Output

Use `templates/agent-handoff.md` format.
