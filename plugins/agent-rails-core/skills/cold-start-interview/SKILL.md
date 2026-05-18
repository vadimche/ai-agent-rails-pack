---
name: cold-start-interview
description: Learn the repository's architecture, invariants, test commands, approval gates and agent operating rules before using other Agent Rails skills.
argument-hint: '[repository context or project path]'
---

# /cold-start-interview

Run this before serious agentic development in a repository.

## Instructions

1. Ask the human for the repository purpose in 2–4 sentences.
2. Ask for the critical invariants: rules that must not be broken.
3. Ask for architectural boundaries: modules, layers, packages, services, APIs.
4. Ask for the normal test commands and validation workflow.
5. Ask what requires explicit human approval.
6. Ask what files, data, credentials or systems are off-limits.
7. Produce a concise practice profile suitable for `CLAUDE.md` or `AGENTS.md`.

## Output

```markdown
# Repository Agent Profile

## Purpose
...

## Critical invariants
...

## Architecture boundaries
...

## Test and validation commands
...

## Human approval gates
...

## Off-limits areas
...

## Agent operating rules
...
```

## Boundary

Do not claim that the profile guarantees correctness or safety. It is a workflow aid.
