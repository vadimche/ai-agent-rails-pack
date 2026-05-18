# Agent Self-Check After Implementation

Use this after the coding agent completes the change.

## Intent match

- [ ] The change sends one confirmation email only after successful order creation.
- [ ] The change does not modify payment capture behavior.
- [ ] The change does not modify order status transition rules.
- [ ] The change reuses existing email infrastructure.

## Scope control

- [ ] No unrelated refactoring was done.
- [ ] No new mail provider dependency was introduced.
- [ ] No database schema was changed.

## Tests/checks

- [ ] Test proves email is requested after successful order creation.
- [ ] Test proves email is not sent when order creation fails.
- [ ] Test proves email failure does not duplicate an order or alter payment semantics.
- [ ] Existing order tests still pass.

## Human review note

If any item above is unchecked, do not mark the change as ready. Explain the gap and ask for human review.
