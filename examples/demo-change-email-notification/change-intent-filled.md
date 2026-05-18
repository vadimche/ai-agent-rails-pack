# Change Intent: Send Confirmation Email After Successful Order Placement

## 1. Problem

Customers currently receive no confirmation email after an order is successfully placed. We need to send one confirmation email only after the order has been persisted successfully.

## 2. Expected behavior

When an order is created successfully:

- the order is persisted as before;
- the customer receives one confirmation email;
- the email includes order id, total amount and basic delivery information if already available;
- failed email delivery must not create a duplicate order.

## 3. Affected files / modules

Expected areas:

- `OrderService` or existing order-created event handler;
- existing `EmailSender` abstraction;
- existing order creation tests;
- possibly email template resources.

Forbidden unless explicitly approved:

- database schema;
- payment logic;
- order status transition rules;
- authentication/authorization;
- new mail provider dependency.

## 4. Non-goals

This change must not:

- redesign order processing;
- introduce async messaging unless already present;
- change payment capture behavior;
- send marketing emails;
- add a new email infrastructure library.

## 5. Invariants to preserve

- An order must never be created twice because email delivery failed.
- Existing order status transitions must remain unchanged.
- Payment capture and order creation semantics must remain unchanged.
- The existing email abstraction must be reused if available.

## 6. Test plan

Add or update tests proving:

- confirmation email is requested after successful order creation;
- no email is sent when order creation fails;
- payment/order status behavior remains unchanged;
- email failure does not duplicate an order.

Manual verification:

- run existing order service test suite;
- run any email/template rendering tests;
- inspect one generated email body.

## 7. Rollback plan

Rollback by reverting the small change in the order notification integration and any added email template. No data migration is expected.

## 8. Questions for human approval

- Should email sending be synchronous or use the existing async/event mechanism if present?
- What exact email content is required for the first version?
