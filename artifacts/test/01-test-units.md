# Test Specification — Stage 1: Units of Work

Source artifacts: `01_business_requirements.md`, `02_functional_requirements.md`, `03_features.md`, `04_use_cases.md`, `04b_scenarios.md`, `04c_non_functional_requirements.md`.

Total functional areas: **6**  
Total units of work: **27**

## Functional Area: Customer Onboarding

QR entry, customer identification, service mode choice, and table-session binding.

| ID | Name | Description | Actor(s) | Dependencies | Source Ref |
| --- | --- | --- | --- | --- | --- |
| UW-001 | QR Session Activation | Starts a customer session when a valid table QR code is scanned. | Customer, System | None | FR-001 |
| UW-002 | Customer Name Entry | Captures the customer name before any ordering interaction can continue. | Customer, System | UW-001 | FR-002; NFR-007 |
| UW-003 | Service Mode Selection | Requires the customer to choose either self-service or staff-assisted mode before proceeding. | Customer, System | UW-002 | FR-003 |
| UW-004 | Table-Session Association | Keeps the active customer session bound to the table identified by the scanned QR code for the full interaction. | System | UW-001, UW-003 | FR-004 |


## Functional Area: Menu Browsing

Customer-facing menu presentation, cart building, quantity changes, and live totals.

| ID | Name | Description | Actor(s) | Dependencies | Source Ref |
| --- | --- | --- | --- | --- | --- |
| UW-005 | Menu Display by Category | Shows customers the enabled menu items grouped into food and drink categories. | Customer, System | UW-003, UW-023-UW-027 | FR-005; NFR-002; NFR-009 |
| UW-006 | Item Detail Display | Displays full menu item details including allergens and at least one photo. | Customer, System | UW-005 | FR-006 |
| UW-007 | Add Item to Order | Lets the customer add one or more menu items to the active order cart. | Customer, System | UW-005, UW-006 | FR-007 |
| UW-008 | Adjust Item Quantity | Allows the customer to increase or decrease quantities for already selected items. | Customer, System | UW-007 | FR-008 |
| UW-009 | Running Order Summary | Displays a continuously updated cart summary and cumulative total at the bottom of the menu page. | Customer, System | UW-007, UW-008 | FR-009 |


## Functional Area: Self-Service Order Submission

Checkout review, payment choice, order submission, confirmation, and empty-cart protection.

| ID | Name | Description | Actor(s) | Dependencies | Source Ref |
| --- | --- | --- | --- | --- | --- |
| UW-010 | Order Review Before Submission | Forces the customer to review the full order and total before the order can be confirmed. | Customer, System | UW-009 | FR-010 |
| UW-011 | Payment Method Selection | Requires the customer to choose either card or cash before order submission. | Customer, System | UW-010 | FR-011; NFR-005 |
| UW-012 | Order Submission and Number Assignment | Submits the confirmed self-service order and creates a unique order number on success. | Customer, System, Payment Gateway | UW-011 | FR-012; NFR-001; NFR-004; NFR-005 |
| UW-013 | Order Confirmation Display | Shows the assigned order number and pickup guidance immediately after successful submission. | Customer, System | UW-012 | FR-013; NFR-001 |
| UW-014 | Empty Cart Validation | Prevents checkout submission when the cart has no items. | Customer, System | UW-009 | FR-014 |


## Functional Area: Staff-Assisted Service Request

Browse-only assisted flow, readiness capture, staff notification, and exclusions from self-service checkout.

| ID | Name | Description | Actor(s) | Dependencies | Source Ref |
| --- | --- | --- | --- | --- | --- |
| UW-015 | Menu Display in Staff-Assisted Mode | Shows the full menu for browsing when the customer chooses staff-assisted service. | Customer, System | UW-003 | FR-015 |
| UW-016 | Customer Readiness Signal | Provides a one-time action for the customer to request staff attention. | Customer, System | UW-015 | FR-016 |
| UW-017 | Staff Notification | Sends a staff notification containing the table number after customer readiness is confirmed. | System, Staff Member | UW-016 | FR-017 |
| UW-018 | No Payment or Order Number in Staff Mode | Prevents the staff-assisted flow from creating payments or order numbers inside the app. | Customer, System | UW-015, UW-016, UW-017 | FR-018 |


## Functional Area: Order Status Display

Public order board visibility, live status transitions, ready updates, and removal rules.

| ID | Name | Description | Actor(s) | Dependencies | Source Ref |
| --- | --- | --- | --- | --- | --- |
| UW-019 | Public Order Status Display | Provides a venue-facing status board that customers can view without authentication. | Customer, Admin, System | UW-012, UW-013 | FR-019 |
| UW-020 | Order Status Tracking | Shows each active self-service order as In Preparation or Ready for Pickup on the public board. | Customer, Admin, System | UW-019, UW-021 | FR-020 |
| UW-021 | Admin Mark Order Ready | Allows an authenticated admin to mark a self-service order as ready and update the public board immediately. | Admin, System | UW-020, UW-023 | FR-021 |
| UW-022 | Order Removal from Display | Removes a ready order from the public board after collection or timeout. | Admin, System | UW-021 | FR-022 |


## Functional Area: Menu Management

Protected admin access plus menu item creation, change, visibility, and removal controls.

| ID | Name | Description | Actor(s) | Dependencies | Source Ref |
| --- | --- | --- | --- | --- | --- |
| UW-023 | Admin Interface Access Control | Restricts the admin interface to authorised administrators using username and password authentication. | Admin, System | None | FR-023; NFR-006 |
| UW-024 | Add Menu Item | Allows the admin to create a new menu item with all mandatory commercial and allergen data. | Admin, System | UW-023 | FR-024 |
| UW-025 | Edit Menu Item | Allows the admin to update existing menu item details including price, allergens, and photo. | Admin, System | UW-023 | FR-025 |
| UW-026 | Enable or Disable Menu Item | Lets the admin hide or re-expose menu items without deleting them. | Admin, System | UW-023 | FR-026 |
| UW-027 | Remove Menu Item Permanently | Allows the admin to permanently delete a menu item after explicit confirmation. | Admin, System | UW-023 | FR-027 |


## ⚠️ Ambiguities and Gaps

- UW-001: The specification says invalid or duplicate-invalid codes must be rejected gracefully, but does not define the grace behaviour.
- UW-002: The maximum allowed customer-name length is not defined.
- UW-002: The exact deletion point for customer names after order completion is not defined.
- UW-003: The specification does not define whether customers may deliberately restart and choose another mode after selection.
- UW-004: No timeout or explicit session-expiry rule is given for customer table sessions.
- UW-005: The specification does not define the customer message for an empty or unavailable menu.
- UW-006: The required prominence level for allergen display is not defined beyond “prominently displayed”.
- UW-007: The specification does not define any maximum quantity per item.
- UW-008: No upper quantity boundary is defined.
- UW-009: The specification does not define whether in-session admin price changes recalculate existing carts.
- UW-010: Cancel/return behaviour from the review step is not specified.
- UW-011: The specification does not define how payment-method selection is presented to assistive technologies.
- UW-012: The order-number format is preferred to be sequential or short, but not formally specified.
- UW-012: No idempotency mechanism is explicitly defined for duplicate submit taps.
- UW-013: The exact pickup guidance wording is not specified.
- UW-014: The specification does not say whether the checkout button is hidden, disabled, or allowed to trigger a message.
- UW-015: The specification does not say whether prices/totals are shown differently in browse-only mode.
- UW-016: The specification does not define whether an accidental readiness request can be cancelled by staff.
- UW-017: Notification transport and failure handling are unspecified.
- UW-018: The specification does not define whether staff can convert an assisted session into a self-service session.
- UW-019: The specification does not define the empty-state message for the public display.
- UW-020: The specification does not define how the board orders or paginates many simultaneous orders.
- UW-021: The maximum acceptable propagation delay to the public display is unspecified.
- UW-022: The default timeout, minimum timeout, and who may configure it are not specified.
- UW-023: The inactivity timeout value is explicitly marked TO BE REFINED.
- UW-023: No lockout or rate-limit rule is defined for repeated failed logins.
- UW-024: Allowed price precision, photo size limits, and category value set are not specified.
- UW-025: Behaviour for already-open customer sessions after an edit is not specified.
- UW-026: The specification does not define whether in-progress carts containing a newly disabled item may still submit.
- UW-027: The specification does not define how deleted items are represented in historical reporting or past orders.
