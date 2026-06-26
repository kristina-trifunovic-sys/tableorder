# Test Specification — Stage 3: Scenarios & Test Data

Scenario IDs remain traceable to Stage 1 Units of Work and cover happy, boundary, negative, edge, and state behaviours.

---
**UW-001 — QR Session Activation**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-001-TC-001 | Scan a valid table QR code | Happy Path | QR payload: tableorder://table/T12 | The app opens a new session for table T12 and displays the name-entry step. |
| UW-001-TC-002 | Reject an unrecognised QR code | Negative | QR payload: tableorder://table/UNKNOWN | The app blocks session creation and shows an invalid-table error with retry guidance. |


---
**UW-002 — Customer Name Entry**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-002-TC-001 | Accept a valid customer name | Happy Path | Name: Alice Morgan | The name is saved in the session and the service-mode selection step is shown. |
| UW-002-TC-002 | Reject an empty customer name | Negative | Name: "   " | The app keeps the customer on the name-entry step and shows an inline required-field message. |


---
**UW-003 — Service Mode Selection**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-003-TC-001 | Choose self-service mode | Happy Path | Mode: Self-service | The app stores self-service mode and opens the self-service menu flow. |
| UW-003-TC-002 | Block progress with no service mode selected | Negative | Mode: none | The app prevents navigation and prompts the customer to select one mode. |
| UW-003-TC-003 | Prevent mode switching after the downstream flow starts | State | Initial mode: Self-service; second action: Staff-assisted | The app keeps the original self-service flow or forces an explicit restart instead of silently switching modes. |


---
**UW-004 — Table-Session Association**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-004-TC-001 | Persist the table reference through checkout | State | Table: T12; Customer: Alice Morgan; Payment: Cash | The confirmed order keeps table T12 as its origin from activation through confirmation. |
| UW-004-TC-002 | Block downstream actions if table context is lost | Negative | Session with missing table reference | Checkout or staff notification is blocked and the customer sees a session-recovery error. |


---
**UW-005 — Menu Display by Category**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-005-TC-001 | Show only enabled menu items grouped by category | Happy Path | Enabled items: Classic Burger, Cola 330ml; Disabled item: IPA Beer | The customer sees Classic Burger and Cola under their categories and does not see IPA Beer. |
| UW-005-TC-002 | Keep disabled items hidden after a fresh menu load | Negative | Disabled item: Vegan Salad | The customer cannot find or open Vegan Salad from the refreshed menu. |


---
**UW-006 — Item Detail Display**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-006-TC-001 | Display complete item details for a published menu item | Happy Path | Item: Classic Burger; Price: 12.50 EUR; Allergens: gluten, milk; Photo: burger.jpg | The item card shows name, description, price, allergen list, and at least one photo. |
| UW-006-TC-002 | Suppress publication of an item missing allergen information | Negative | Item: Lemon Tart; Allergens: missing | The item is not visible to customers until allergen information is completed. |


---
**UW-007 — Add Item to Order**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-007-TC-001 | Add one enabled item to the cart | Happy Path | Item: Classic Burger at 12.50 EUR | The cart contains Classic Burger with quantity 1 and line total 12.50 EUR. |
| UW-007-TC-002 | Increment quantity when the same item is added twice | State | Item: Cola 330ml at 3.00 EUR added twice | The cart contains one line for Cola 330ml with quantity 2 and line total 6.00 EUR. |


---
**UW-008 — Adjust Item Quantity**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-008-TC-001 | Increase an existing line-item quantity | Happy Path | Item: Margherita Pizza from quantity 1 to 2 | The cart updates Margherita Pizza to quantity 2 and recalculates totals. |
| UW-008-TC-002 | Remove an item by decreasing quantity to zero | Boundary | Item: Margherita Pizza from quantity 1 to 0 | The item is removed from the cart when quantity reaches zero. |
| UW-008-TC-003 | Reject quantity changes below zero | Negative | Attempted quantity: -1 for Cola 330ml | The app prevents the quantity going below zero and leaves the cart unchanged. |


---
**UW-009 — Running Order Summary**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-009-TC-001 | Recalculate the running total after cart changes | Happy Path | Classic Burger 12.50 EUR + Cola 330ml 3.00 EUR | The running summary shows two items and total 15.50 EUR immediately after the changes. |
| UW-009-TC-002 | Return the summary to an empty-cart state after the last item is removed | Boundary | Remove final cart item Classic Burger | The summary shows zero selected items and total 0.00 EUR after the last line is removed. |


---
**UW-010 — Order Review Before Submission**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-010-TC-001 | Show full order review before payment selection | Happy Path | Cart: Classic Burger x1, Cola 330ml x2 | The review screen lists every item, quantity, and the correct total before payment selection. |
| UW-010-TC-002 | Block cart edits after the customer confirms the review | State | Confirmed review for cart total 18.50 EUR | After review confirmation, the customer cannot modify the order unless the flow explicitly returns to the cart. |


---
**UW-011 — Payment Method Selection**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-011-TC-001 | Select card as the payment method | Happy Path | Payment method: card | The pending order stores card as the selected method and starts the gateway path only when the order is submitted. |
| UW-011-TC-002 | Select cash as the payment method | Happy Path | Payment method: cash | The pending order stores cash as the selected method without invoking the card gateway. |
| UW-011-TC-003 | Block order submission when no payment method is selected | Negative | Payment method: none | The app blocks submission and shows a required-payment-method validation message. |


---
**UW-012 — Order Submission and Number Assignment**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-012-TC-001 | Submit a valid cash order and assign a unique order number | Happy Path | Order: Classic Burger x1; Payment: cash | The order is persisted successfully within 3 seconds and receives one unique order number. |
| UW-012-TC-002 | Do not confirm the order when card payment fails | Negative | Order: Classic Burger x1; Payment: card; Gateway result: DECLINED | The app shows a payment failure message and does not create an order record or assign an order number. |
| UW-012-TC-003 | Assign different order numbers to two successful submissions in one service session | State | Submission 1: Classic Burger x1; Submission 2: Cola 330ml x1 | Each successful submission receives a distinct order number even within the same service session. |


---
**UW-013 — Order Confirmation Display**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-013-TC-001 | Show order number and pickup guidance on confirmation | Happy Path | Confirmed order number: A127 | The confirmation screen shows order number A127 and tells the customer to watch the public display for pickup readiness. |
| UW-013-TC-002 | Refresh the confirmation screen without creating a duplicate order | State | Confirmed order number: A127; user action: browser refresh | Refreshing the confirmation page shows the existing order number and does not create a second order. |


---
**UW-014 — Empty Cart Validation**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-014-TC-001 | Block checkout when the cart is empty | Negative | Cart items: none | The customer cannot submit and sees a prompt to add at least one item. |
| UW-014-TC-002 | Allow checkout once one item exists in the cart | Boundary | Cart: Cola 330ml x1 | A cart containing exactly one item can proceed to the review step. |


---
**UW-015 — Menu Display in Staff-Assisted Mode**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-015-TC-001 | Show the menu in browse-only mode for staff-assisted service | Happy Path | Mode: staff-assisted | The customer can browse menu items but cannot build a cart. |
| UW-015-TC-002 | Prevent add-to-cart actions in staff-assisted mode | Negative | Item: Classic Burger in staff-assisted mode | The app does not allow the item to be added to a cart while in assisted mode. |


---
**UW-016 — Customer Readiness Signal**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-016-TC-001 | Record a one-time readiness request | Happy Path | Ready action tapped once | The session records one readiness event and shows that staff have been called. |
| UW-016-TC-002 | Ignore a second readiness tap in the same session | State | Ready action tapped twice | Only one readiness event is stored and the second activation is ignored or blocked. |


---
**UW-017 — Staff Notification**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-017-TC-001 | Send a staff notification containing the table number | Happy Path | Table: T12 | The staff-facing notification includes table T12 so staff know where to go. |
| UW-017-TC-002 | Block notification if table context is missing | Negative | Readiness event with missing table reference | The app does not send a malformed notification and surfaces a recoverable session error. |


---
**UW-018 — No Payment or Order Number in Staff Mode**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-018-TC-001 | Finish the staff-assisted flow without payment or order number | State | Staff-assisted session for table T12 | After readiness is recorded, no order number is generated and no app-side payment is processed. |
| UW-018-TC-002 | Block direct navigation to checkout in staff-assisted mode | Negative | Attempted route: /checkout while session mode = staff-assisted | The app blocks checkout access and explains that the current session uses staff-assisted service. |


---
**UW-019 — Public Order Status Display**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-019-TC-001 | Open the public order board without authentication | Happy Path | Public display URL | The display loads current order-status information without requiring login. |
| UW-019-TC-002 | Keep admin controls off the public order board | Negative | Public display URL with active orders present | The public board shows order statuses only and does not expose ready/dismiss controls. |


---
**UW-020 — Order Status Tracking**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-020-TC-001 | Show a new self-service order as In Preparation | Happy Path | Confirmed order number: A127 | The public board shows order A127 in the In Preparation section after submission. |
| UW-020-TC-002 | Exclude staff-assisted sessions from the public order board | Negative | Staff-assisted session for table T12 | No public-board entry is created for the assisted session because no self-service order exists. |


---
**UW-021 — Admin Mark Order Ready**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-021-TC-001 | Mark an in-preparation order as ready for pickup | Happy Path | Order number: A127 currently In Preparation | The selected order moves to Ready for Pickup and the public board updates immediately. |
| UW-021-TC-002 | Reject a ready-status change from an unauthenticated user | Negative | Order number: A127; user state: not authenticated | The system denies the status change and leaves A127 in its original state. |


---
**UW-022 — Order Removal from Display**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-022-TC-001 | Remove a collected order from the public display | Happy Path | Order number: A127 marked collected by admin | The public board removes order A127 after collection is confirmed. |
| UW-022-TC-002 | Keep a ready order visible just before timeout expiry | Boundary | Configured timeout: 10 minutes; elapsed time: 9 minutes 59 seconds | The ready order still appears on the public board before the timeout threshold is reached. |


---
**UW-023 — Admin Interface Access Control**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-023-TC-001 | Allow access with valid admin credentials | Happy Path | Username: admin.tableorder; Password: Admin#2026 | The system authenticates the admin and opens the protected admin interface. |
| UW-023-TC-002 | Show a generic error for invalid admin credentials | Negative | Username: admin.tableorder; Password: Wrong#2026 | Login is rejected and a generic authentication error is shown without identifying which field was wrong. |
| UW-023-TC-003 | Expire an idle admin session after the configured inactivity threshold | State | Configured inactivity timeout: 15 minutes | After 15 minutes of inactivity, the admin session expires and protected actions require re-authentication. |


---
**UW-024 — Add Menu Item**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-024-TC-001 | Create a new menu item with all mandatory fields | Happy Path | Name: Vegan Salad; Description: Mixed greens with avocado; Price: 9.00; Category: Salads; Allergens: nuts; Photo: vegan-salad.jpg | The system saves Vegan Salad successfully and makes it available to future customer sessions when enabled. |
| UW-024-TC-002 | Reject a new menu item missing allergen information | Negative | Name: Lemon Tart; Price: 5.50; Category: Desserts; Allergens: empty; Photo: lemon-tart.jpg | The system blocks the save and highlights the missing allergen information. |
| UW-024-TC-003 | Save special characters correctly when adding a menu item | Edge | Name: Crème Brûlée; Description: Vanilla custard – chef’s special; Price: 6.20; Category: Desserts; Allergens: eggs, milk; Photo: creme-brulee.jpg | The item is saved and the accented characters and punctuation are preserved exactly. |


---
**UW-025 — Edit Menu Item**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-025-TC-001 | Update price and allergens for an existing menu item | Happy Path | Item: Classic Burger; New price: 13.00; New allergens: gluten, milk, sesame | The item is updated and future customer sessions see the revised price and allergen list. |
| UW-025-TC-002 | Reject an invalid edited price | Negative | Item: Classic Burger; Edited price: abc | The system blocks the update and highlights the invalid price field. |


---
**UW-026 — Enable or Disable Menu Item**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-026-TC-001 | Disable a menu item without affecting existing confirmed orders | Happy Path | Item: IPA Beer | IPA Beer becomes hidden from new customer sessions, while older confirmed orders containing it stay unchanged. |
| UW-026-TC-002 | Re-enable a previously disabled item | State | Item: IPA Beer | The item becomes visible again in new customer sessions after being re-enabled. |
| UW-026-TC-003 | Reject adding a newly disabled item from a stale customer page | Negative | Item: IPA Beer disabled after customer opened the menu | The add attempt fails and the stale page cannot submit IPA Beer to the cart. |


---
**UW-027 — Remove Menu Item Permanently**

| TC ID | Scenario Description | Test Type | Input Data | Expected Result |
| --- | --- | --- | --- | --- |
| UW-027-TC-001 | Delete a menu item only after confirmation | Happy Path | Item: Seasonal Soup; Confirmation: confirm delete | The system deletes Seasonal Soup from the active catalogue only after explicit confirmation. |
| UW-027-TC-002 | Keep the menu item when delete confirmation is cancelled | Negative | Item: Seasonal Soup; Confirmation: cancel | The system keeps Seasonal Soup unchanged when the admin cancels the confirmation prompt. |
