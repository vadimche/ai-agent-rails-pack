# Quick Start

Get useful rails into a repository in 60 seconds.

## Option A — plain repository pack

1. Copy these files into your repository:

```text
AGENTS.md
docs/
templates/
.github/pull_request_template.md
```

2. Fill the invariant register:

```text
templates/invariant-register.md
```

Add 3–10 rules that must not be broken. Examples:

- order placement must remain idempotent;
- payment status transitions must not change without approval;
- frontend components must not call the database/API directly;
- no new dependency without explicit approval.

3. Before coding, ask the agent:

```text
Read AGENTS.md and templates/change-intent.md.
Do not modify code yet.
First write a Change Intent for this task.
Wait for my approval before implementation.
```

4. After coding, ask the agent:

```text
Compare the diff against the approved Change Intent.
Fill the self-check section:
- intended files changed
- unexpected files changed
- invariants affected
- tests run
- rollback path
```

## Option B — Claude Code plugin-style pack

This repository also includes an optional Claude Code plugin-style structure under:

```text
plugins/agent-rails-core/
```

Use it as a reference if you want slash-command style workflows such as:

```text
/agent-rails-core:change-intent
/agent-rails-core:self-check
/agent-rails-core:handoff
/agent-rails-core:context-snapshot
```

The plugin files are markdown/JSON templates and can be adapted to the Claude Code plugin system or copied into your own agent workflow.

## What this does not do

This pack does not review code for correctness, security, compliance, or production readiness.

It helps the human make intent, boundaries, invariants, tests and rollback explicit before an agent starts changing files.
