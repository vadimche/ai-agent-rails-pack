# AI Agent Rails Pack

**Practical guardrails for Codex, Claude Code, Cursor and other GenAI coding agents.**

> AI coding agents are fast. That is exactly why they need rails.

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
examples/java-spring/AGENTS.md                  # Java/Spring specialization
examples/vue/AGENTS.md                          # Vue frontend specialization
examples/multi-agent/roles.md                   # planner/builder/reviewer roles
examples/demo-change-email-notification/        # demo: controlled backend change
examples/demo-change-price-formatting/          # demo: controlled frontend change
.github/pull_request_template.md                # PR template aligned with the pack
```

## Quick start

1. Copy `AGENTS.md`, `docs/`, and `templates/` into your repository.
2. Fill `templates/invariant-register.md` with 3–10 critical rules of your system.
3. Before asking an agent to code, create a `change-intent.md` from the template.
4. Ask the agent to implement only after the change intent is clear.
5. Before merge, use `docs/human-approval-checklist.md`.


## Demo examples

The pack includes two small demos that show the workflow in practice. They are intentionally simple: the goal is not to demonstrate a complex architecture, but to show how a coding agent can be kept inside a clear intent boundary.

### Demo 1: backend change — order confirmation email

Path:

```text
examples/demo-change-email-notification/
```

Scenario:

> Add an email notification after successful order placement.

Why this demo matters: this looks like a small feature, but an agent can easily touch order transactions, payment flow, status transitions, or introduce a new mail dependency. The filled Change Intent makes the boundary explicit before coding starts.

Files:

```text
examples/demo-change-email-notification/task.md
examples/demo-change-email-notification/change-intent-filled.md
examples/demo-change-email-notification/agent-self-check.md
```

Use it like this:

```text
Read the demo task and filled Change Intent.
Explain how the Change Intent limits implementation scope.
Then implement only within that approved boundary.
After implementation, complete agent-self-check.md.
```

### Demo 2: frontend change — price formatting

Path:

```text
examples/demo-change-price-formatting/
```

Scenario:

> In the Vue product list, show prices with the euro symbol and two decimal places.

Why this demo matters: agents often over-edit frontend code. A formatting task should not change API contracts, store structure, sorting logic, dependency versions, or unrelated layout. The rails make that visible.

Files:

```text
examples/demo-change-price-formatting/task.md
examples/demo-change-price-formatting/change-intent-filled.md
examples/demo-change-price-formatting/agent-self-check.md
```

Use it like this:

```text
Read the task and Change Intent.
Before editing code, list the files you expect to touch and the files you must not touch.
After implementation, compare the diff against agent-self-check.md.
```

### What the demos are meant to prove

They do not prove that an AI agent is safe or that code is production-ready. They show a more modest and useful practice:

> make intent, scope, invariants, tests and rollback explicit before giving an agent permission to modify code.

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
