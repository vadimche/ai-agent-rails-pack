# Vue Agent Instructions

Use these instructions in addition to the root `AGENTS.md` for Vue repositories.

## Boundaries

- Keep UI formatting local when possible.
- Do not change API contracts or store structure for presentation-only tasks.
- Reuse existing components/composables before adding new abstractions.
- Avoid broad CSS/layout rewrites for small visual requests.

## Testing/checks

- Run the existing frontend test/lint command when available.
- For UI changes, provide a short manual verification checklist.
- Preserve accessibility basics: labels, keyboard interaction and readable contrast.

## Risk gates

Request human approval before changing:

- routing;
- authentication/session logic;
- global store structure;
- API client behavior;
- build configuration.
