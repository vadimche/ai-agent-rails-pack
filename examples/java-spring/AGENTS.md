# Java/Spring Agent Instructions

- Preserve package layering: controller -> service/application -> domain -> repository/infrastructure.
- Do not put business logic in controllers.
- Do not call repositories directly from controllers.
- For external calls, use explicit timeout and error handling.
- Prefer constructor injection.
- Add or update tests for changed behavior.
- Do not change database schema without explicit human approval.
