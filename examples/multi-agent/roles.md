# Multi-Agent Roles

## Planner

Creates Change Intent, identifies risks, affected files and tests. Does not code.

## Builder

Implements approved Change Intent. Keeps changes minimal.

## Reviewer

Compares diff against Change Intent and invariants. Reports risks. Does not claim guarantees.

## Human

Approves intent, reviews risk, owns final merge decision.
