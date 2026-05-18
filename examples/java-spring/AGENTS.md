# Java/Spring Agent Instructions

Use these instructions in addition to the root `AGENTS.md` for Java/Spring repositories.

## Boundaries

- Keep controllers thin.
- Put business rules in services/domain objects, not controllers.
- Do not bypass repositories or transaction boundaries without explicit approval.
- Do not introduce new frameworks for small changes.

## Testing

- Prefer focused unit tests for business rules.
- Add integration tests for persistence, transactions, security configuration and external API boundaries.
- For risky changes, state which Spring profile/configuration was used for testing.

## Risk gates

Request human approval before changing:

- authentication/authorization;
- transaction boundaries;
- database migrations;
- external payment/order/email integrations;
- production configuration.
