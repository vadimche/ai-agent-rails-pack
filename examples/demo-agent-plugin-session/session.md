# Demo Agent Rails Session

This example shows the intended flow with the optional plugin-style skills.

## Step 1 — cold start

```text
/agent-rails-core:cold-start-interview
```

Expected result: a short repository profile with purpose, invariants, boundaries, tests and approval gates.

## Step 2 — prepare intent

```text
/agent-rails-core:change-intent Add order confirmation email after successful order placement.
```

Expected result: a filled Change Intent. No code is changed yet.

## Step 3 — approve and implement

Human reviews the Change Intent. If approved, the agent implements only inside the stated boundary.

## Step 4 — self-check

```text
/agent-rails-core:self-check
```

Expected result: PASS / WARN / BLOCK with files changed, scope drift, invariants and tests.

## Step 5 — handoff

```text
/agent-rails-core:handoff
```

Expected result: a compact handoff for a human reviewer or another agent.
