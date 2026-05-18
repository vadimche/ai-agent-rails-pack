# AI Agent Rails Pack

**Practical workflow rails for Codex, Claude Code, Cursor and other GenAI coding agents.**

> AI coding agents are fast. That is exactly why they need rails.

Modern coding agents can generate large diffs in minutes. That is useful. It is also how small tasks turn into broad, hard-to-review changes.

This repository gives humans a lightweight way to keep control:

- write intent before coding;
- name invariants before touching files;
- define non-goals explicitly;
- keep diffs small and reviewable;
- require human approval at the right points;
- make every agent handoff compact and auditable;
- self-check the final diff against the original intent.

This is **not** an automated code-review guarantee. It is **not** a security tool. It is **not** a replacement for engineering judgment.

It is a practical rails pack for teams that use AI coding agents and do not want to vibe-code their production system.

---

## Why this exists

AI agents often fail in boring, expensive ways:

- they start coding before the task is understood;
- they touch unrelated files;
- they silently change old behavior;
- they perform a refactor hidden inside a small feature;
- they forget critical invariants;
- they leave weak tests and unclear rollback;
- they hand a human reviewer a large diff with no decision trail.

The fix is not a bigger prompt.

The fix is a small operating model:

```text
Intent → Boundaries → Invariants → Approval → Implementation → Self-check → Human review
```

---

## Who this is for

- solo developers using Codex, Claude Code, Cursor, Gemini CLI, Copilot or similar tools;
- CTOs and engineering managers introducing AI-assisted development;
- architects who need agents to respect system boundaries;
- teams that want less prompt chaos and better change traceability;
- anyone who has seen an agent turn a small task into a suspiciously large diff.

---

## What is included

```text
AGENTS.md                                      # default repo-level agent instructions
QUICKSTART.md                                  # 60-second setup guide
docs/agent-workflow.md                         # recommended human-controlled workflow
docs/human-approval-checklist.md               # review gate for humans
docs/trust-and-safety.md                       # safe positioning and responsibility boundary
docs/workflow-catalog.md                       # copy-paste workflows
templates/change-intent.md                     # fill before coding
templates/invariant-register.md                # system invariants to protect
templates/rollback-plan.md                     # rollback notes
templates/agent-handoff.md                     # handoff between agents/humans
examples/java-spring/AGENTS.md                 # Java/Spring specialization
examples/vue/AGENTS.md                         # Vue frontend specialization
examples/multi-agent/roles.md                  # planner/builder/reviewer roles
examples/demo-change-email-notification/       # demo: controlled backend change
examples/demo-change-price-formatting/         # demo: controlled frontend change
examples/demo-agent-plugin-session/            # demo: plugin-style session
.github/pull_request_template.md               # PR template aligned with the pack
.claude-plugin/marketplace.json                # optional Claude plugin-style marketplace reference
plugins/agent-rails-core/                      # optional Claude Code plugin-style skills
```

---

## Quick start

Copy the core files into your repository:

```text
AGENTS.md
docs/
templates/
.github/pull_request_template.md
```

Fill the invariant register:

```text
templates/invariant-register.md
```

Then ask your coding agent:

```text
Read AGENTS.md and templates/change-intent.md.
Do not modify code yet.
First produce a Change Intent for the task below.
Include affected files, non-goals, invariants, test plan and rollback notes.
After I approve the Change Intent, proceed with implementation.
```

After implementation:

```text
Compare the diff against the approved Change Intent.
List expected changes, unexpected changes, invariant impact, tests run, tests missing and rollback path.
Return PASS, WARN or BLOCK.
```

See [`QUICKSTART.md`](QUICKSTART.md) for the 60-second setup.

---

## Core workflow

```text
1. Context snapshot
   The agent identifies only the files, tests and patterns relevant to the task.

2. Change intent
   The agent writes what it plans to do before touching code.

3. Human approval
   The human approves, narrows or rejects the intent.

4. Implementation
   The agent implements only inside the approved boundary.

5. Self-check
   The agent compares the diff against the original intent.

6. Human review
   The human reviews with a short decision trail instead of a mystery diff.
```

---

## Optional Claude Code plugin-style structure

This repository includes an optional plugin-style pack under:

```text
plugins/agent-rails-core/
```

It contains markdown skills that can be adapted into Claude Code / Claude plugin workflows:

| Skill | Purpose |
|---|---|
| `cold-start-interview` | Learn repository purpose, invariants, boundaries, tests and approval gates. |
| `change-intent` | Prepare the implementation plan before coding starts. |
| `context-snapshot` | Capture relevant repo context without flooding the model. |
| `self-check` | Compare the final diff against the approved intent. |
| `handoff` | Create a compact handoff for another agent or human reviewer. |

These are reference templates. Everything is markdown and JSON. No build step.

---

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

### Demo 3: plugin-style agent session

Path:

```text
examples/demo-agent-plugin-session/
```

Shows the intended flow with optional slash-command style skills:

```text
/agent-rails-core:cold-start-interview
/agent-rails-core:change-intent
/agent-rails-core:self-check
/agent-rails-core:handoff
```

---

## What the demos are meant to prove

They do not prove that an AI agent is safe or that generated code is production-ready.

They show a more modest and useful practice:

> make intent, scope, invariants, tests and rollback explicit before giving an agent permission to modify code.

---

## What this pack does not do

This pack does **not**:

- guarantee correct code;
- guarantee secure code;
- replace human review;
- make legal, compliance or production-readiness claims;
- certify AI-generated changes;
- turn an AI agent into an autonomous engineer.

Use it as a workflow layer, not as an assurance product.

---

## Recommended repository policy

Add this rule to your team’s AI coding policy:

> No AI-generated code change may proceed without an approved Change Intent for non-trivial work. The final diff must be checked against the approved intent before human review.

For small changes, use a short intent. For risky changes, use the full template.

---

## Good first use cases

- feature changes that should touch only a few files;
- bug fixes with important invariants;
- frontend formatting or UI changes that must not affect API contracts;
- backend changes near payments, orders, auth, user data or external integrations;
- multi-agent workflows where planner, builder and reviewer need clean handoffs.

---

## Bad use cases

Do not use this pack as the only control for:

- security-sensitive changes;
- regulated systems;
- payments or trading logic without expert human review;
- production migrations;
- credential rotation;
- irreversible data operations;
- anything where a wrong answer can cause serious harm.

---

## Suggested LinkedIn launch message

```text
AI coding agents are fast.

That is useful.

It is also dangerous when the agent starts coding before the human has made the intent, boundaries and invariants explicit.

So I created AI Agent Rails Pack: a small open-source workflow pack for Codex, Claude Code, Cursor and other GenAI coding agents.

It includes:
- AGENTS.md
- Change Intent template
- Invariant Register
- Rollback template
- Agent Handoff template
- Human approval checklist
- Java/Spring and Vue examples
- optional Claude plugin-style skills

It is not an automated code-review guarantee.
It is not a replacement for engineering judgment.

It is just a practical way to stop vibe-coding into production and keep humans in control.
```

---

## License

MIT.
