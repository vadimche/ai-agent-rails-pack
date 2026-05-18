# Agent Rails Core

Core workflow rails for coding agents.

## Commands / skills

| Skill | Purpose |
|---|---|
| `cold-start-interview` | Learn repository context, critical invariants, test commands and approval gates. |
| `change-intent` | Prepare an implementation plan before coding starts. |
| `self-check` | Compare the final diff against the approved intent. |
| `handoff` | Create a compact handoff for another agent or human. |
| `context-snapshot` | Capture relevant repo context without flooding the model. |

## Usage model

Start with `cold-start-interview`, then use `change-intent` before implementation and `self-check` after implementation.
