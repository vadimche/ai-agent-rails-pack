# Demo Task: Order Confirmation Email

## User request

Add an email notification after a customer successfully places an order.

## Important context

The application already has:

- an `OrderService` that creates orders;
- an `EmailSender` abstraction;
- existing order status transitions;
- tests around order creation.

## Hidden risk

A coding agent may be tempted to put email sending directly into the order transaction, change order status rules, or introduce a new mail library even though the repository already has one.

## Goal of the demo

Show how the rails force the agent to make the change small, explicit, testable and reversible before it starts coding.
