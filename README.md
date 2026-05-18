# AI Agent Rails Pack

**Practical guardrails for Codex, Claude Code, Cursor and other GenAI coding agents.**

AI coding agents are powerful, but without a lightweight workflow they tend to start coding too early, lose intent, touch unrelated files, break invariants, and leave humans with a large diff and weak explanation.

This pack gives teams a small set of repository-level rails:

- clear task intent before coding;
- explicit invariants and non-goals;
- human approval gates;
- test expectations;
- rollback notes;
- agent handoff format;
- post-change self-check.

This is **not** an automated code-review guarantee and not a replacement for human engineering judgment. It is a workflow pack that helps humans and agents work with less chaos.

## Who this is for

- solo developers using Codex, Claude Code, Cursor or similar tools;
- CTOs and engineering managers introducing AI-assisted development;
- architects who need agents to respect system boundaries;
- teams that want less vibe-coding and better change traceability.

## What is included

```text
AGENTS.md                         # default repo-level agent instructions
docs/agent-workflow.md             # recommended workflow
docs/human-approval-checklist.md   # review gate for humans
templates/change-intent.md         # fill before coding
templates/invariant-register.md    # system invariants to protect
templates/rollback-plan.md         # rollback notes
templates/agent-handoff.md         # handoff between agents/humans
examples/java-spring/AGENTS.md     # Java/Spring specialization
examples/vue/AGENTS.md             # Vue frontend specialization
examples/multi-agent/roles.md      # planner/builder/reviewer roles
.github/pull_request_template.md   # PR template aligned with the pack
```

## Quick start

1. Copy `AGENTS.md`, `docs/`, and `templates/` into your repository.
2. Fill `templates/invariant-register.md` with 3–10 critical rules of your system.
3. Before asking an agent to code, create a `change-intent.md` from the template.
4. Ask the agent to implement only after the change intent is clear.
5. Before merge, use `docs/human-approval-checklist.md`.

## Example prompt

```text
Read AGENTS.md and templates/change-intent.md.
Do not modify code yet.
First produce a Change Intent for the task below, including affected files, non-goals, invariants, test plan and rollback notes.
After I approve the Change Intent, proceed with implementation.
```

## Core principle

> The agent may write code fast, but the human must keep intent, boundaries and judgment explicit.

## License

MIT.
