# Change Intent: Format Product Prices in the Product List

## 1. Problem

The product list currently displays raw numeric prices. Users should see prices formatted as euros with two decimal places.

## 2. Expected behavior

Examples:

- `12` becomes `€12.00`
- `12.5` becomes `€12.50`
- `0` becomes `€0.00`

## 3. Affected files / modules

Expected areas:

- product list component;
- existing price formatting utility if present;
- component/unit tests for product rendering.

Forbidden unless explicitly approved:

- backend API contract;
- database model;
- global state store structure;
- unrelated layout redesign;
- dependency upgrades.

## 4. Non-goals

This change must not:

- implement multi-currency support;
- change price calculation;
- change sorting/filtering behavior;
- redesign the product card;
- add a new UI library.

## 5. Invariants to preserve

- Prices must remain numeric in internal data structures.
- Sorting/filtering must still use numeric values, not formatted strings.
- No API payload shape must change.
- Existing layout density should remain unchanged.

## 6. Test plan

Add or update tests proving:

- product list renders prices as `€X.XX`;
- numeric sorting/filtering behavior is unchanged if covered by existing tests;
- null/undefined price behavior follows the existing application convention.

Manual verification:

- open product list;
- check several prices;
- verify no unrelated visual changes.

## 7. Rollback plan

Rollback by reverting the formatting helper/component change. No backend or data changes are expected.
