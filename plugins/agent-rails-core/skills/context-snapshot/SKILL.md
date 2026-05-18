---
name: context-snapshot
description: Create a compact repository context snapshot for agentic work without overloading the model.
argument-hint: '[task or feature area]'
---

# /context-snapshot

Capture only the context needed for the current task.

## Instructions

1. Identify the feature area or module relevant to the task.
2. List key files and their roles.
3. List nearby tests.
4. List existing patterns to follow.
5. List known invariants and boundaries.
6. Exclude unrelated files and broad architecture commentary.

## Output

```markdown
# Context Snapshot

## Task area
...

## Key files
...

## Existing patterns
...

## Nearby tests
...

## Invariants and boundaries
...

## Out of scope
...
```
