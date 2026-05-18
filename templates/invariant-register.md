# Invariant Register

List the rules that must not be broken by agent-generated changes.

| ID | Invariant | Why it matters | How to verify |
|---|---|---|---|
| INV-001 | Example: Payment amount must never be recalculated on the client. | Prevents tampering and accounting errors. | Server-side test for checkout total. |
| INV-002 | Example: External API calls must have timeout and error handling. | Prevents cascading failures. | Integration test / code inspection. |
