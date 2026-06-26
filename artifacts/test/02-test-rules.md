# Test Specification — Stage 2: Validation Rules & Behaviours

Each block was internally checked against the Stage 2 quality gate for completeness, precision, and traceability.

---
**UW-001 — QR Session Activation**

- **Functional Area:** Customer Onboarding
- **Source References:** FR-001
- **Preconditions:**
  - A table-specific QR code is displayed in the venue.
  - The customer uses a mobile browser-capable device.
- **Input Constraints:**
  - Input is a QR code payload resolving to one table identifier.
  - The code must be recognised by the system before the flow can continue.
- **Validation Rules:**
  - Each valid QR code maps to exactly one table.
  - Unrecognised or duplicate-invalid codes are rejected before session creation.
- **System Behaviours (Success):**
  - The system opens the ordering flow and creates an active session for the table.
- **System Behaviours (Failure):**
  - The system blocks progress and keeps the customer out of the ordering flow.
- **Postconditions:**
  - A valid session exists only for recognised table codes.
- **Edge/Boundary Conditions:**
  - Invalid payloads must not create partial sessions.
  - Same table code reused on a later legitimate visit must still resolve to the same table.
- **Error Handling:**
  - Show a clear invalid-code message with retry guidance.
  - ⚠️ Exact error copy and recovery path are unspecified.
- **⚠️ Gaps:**
  - ⚠️ The specification says invalid or duplicate-invalid codes must be rejected gracefully, but does not define the grace behaviour.

---
**UW-002 — Customer Name Entry**

- **Functional Area:** Customer Onboarding
- **Source References:** FR-002; NFR-007
- **Preconditions:**
  - A valid session has been activated from the scanned QR code.
- **Input Constraints:**
  - Name entry is mandatory before proceeding.
  - The value must be stored in the active session only.
- **Validation Rules:**
  - Empty input is rejected.
  - A maximum length must be enforced to prevent abuse.
  - Customer personal data must not outlive the active ordering purpose.
- **System Behaviours (Success):**
  - The system stores the name in session context and unlocks the next step.
- **System Behaviours (Failure):**
  - The system keeps the customer on the name-entry step and highlights the invalid field.
- **Postconditions:**
  - The active session contains a usable display name until the order flow ends.
- **Edge/Boundary Conditions:**
  - Blank spaces only must be treated as empty.
  - Very long input must be rejected or truncated according to the configured limit.
- **Error Handling:**
  - Display an inline validation message when the field is blank or too long.
  - ⚠️ Exact maximum length and message text are not specified.
- **⚠️ Gaps:**
  - ⚠️ The maximum allowed customer-name length is not defined.
  - ⚠️ The exact deletion point for customer names after order completion is not defined.

---
**UW-003 — Service Mode Selection**

- **Functional Area:** Customer Onboarding
- **Source References:** FR-003
- **Preconditions:**
  - A valid session exists and the customer name has been captured.
- **Input Constraints:**
  - Only two values are allowed: self-service or staff-assisted.
  - Exactly one option may be active in a session.
- **Validation Rules:**
  - Mode selection is mandatory.
  - The two options are mutually exclusive.
  - The selected mode determines the rest of the journey and must lock the downstream flow.
- **System Behaviours (Success):**
  - The chosen mode is saved and the customer is routed to the matching experience.
- **System Behaviours (Failure):**
  - The system blocks onward navigation if no mode is selected.
  - The system rejects attempts to activate both modes.
- **Postconditions:**
  - The session has one persisted service mode controlling allowed actions.
- **Edge/Boundary Conditions:**
  - Refreshing after selection must preserve the selected mode.
  - Attempting to change mode after entering a downstream flow must be blocked or restart the flow.
- **Error Handling:**
  - Show a validation prompt when the customer tries to continue without a mode.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define whether customers may deliberately restart and choose another mode after selection.

---
**UW-004 — Table-Session Association**

- **Functional Area:** Customer Onboarding
- **Source References:** FR-004
- **Preconditions:**
  - A valid QR code has been resolved to a table.
  - A session has been created.
- **Input Constraints:**
  - The table identifier comes only from the scanned QR code.
  - The session must carry the table reference through ordering or notification completion.
- **Validation Rules:**
  - The table reference persists from session start to order confirmation or staff notification.
  - The customer must not be able to overwrite the table identifier from the UI.
- **System Behaviours (Success):**
  - All downstream actions use the original table reference.
- **System Behaviours (Failure):**
  - If table context is missing, dependent actions must be blocked rather than misrouted.
- **Postconditions:**
  - Orders or staff notifications are traceable to the originating table.
- **Edge/Boundary Conditions:**
  - Page refresh or route changes must not detach the session from its table.
  - Expired or corrupted session context must not create cross-table leakage.
- **Error Handling:**
  - Display a recoverable session error if the table reference is lost.
  - ⚠️ Session recovery mechanics are not specified.
- **⚠️ Gaps:**
  - ⚠️ No timeout or explicit session-expiry rule is given for customer table sessions.

---
**UW-005 — Menu Display by Category**

- **Functional Area:** Menu Browsing
- **Source References:** FR-005; NFR-002; NFR-009
- **Preconditions:**
  - An active session exists.
  - Menu data contains enabled items maintained by the admin.
- **Input Constraints:**
  - The system reads current menu data and category assignments.
  - Only enabled items are eligible for display.
- **Validation Rules:**
  - Items are grouped by category.
  - Disabled items are hidden from customers.
  - The menu should become browsable within 3 seconds of first access.
- **System Behaviours (Success):**
  - Customers see only enabled items, organised into categories.
- **System Behaviours (Failure):**
  - If no enabled items exist in a category, the category must not expose disabled content.
- **Postconditions:**
  - The customer can browse the menu and continue building an order if in self-service mode.
- **Edge/Boundary Conditions:**
  - An empty category must not show disabled placeholders.
  - The UI must remain usable on standard mobile browsers.
- **Error Handling:**
  - ⚠️ No empty-menu message is specified if the whole menu has no enabled items.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define the customer message for an empty or unavailable menu.

---
**UW-006 — Item Detail Display**

- **Functional Area:** Menu Browsing
- **Source References:** FR-006
- **Preconditions:**
  - The menu item exists and is enabled for customer viewing.
- **Input Constraints:**
  - Each item record includes name, description, price, allergen information, and at least one photo.
- **Validation Rules:**
  - Allergen information is mandatory and prominent.
  - Items missing allergen data must not be published.
- **System Behaviours (Success):**
  - Customers can see a complete detail card for each published item.
- **System Behaviours (Failure):**
  - The system suppresses publication of items that lack allergen data.
- **Postconditions:**
  - Visible items remain fully described for informed ordering.
- **Edge/Boundary Conditions:**
  - Items with multiple allergens must show them together.
  - Photo absence must prevent publication.
- **Error Handling:**
  - ⚠️ No fallback image behaviour is specified if stored media becomes unavailable.
- **⚠️ Gaps:**
  - ⚠️ The required prominence level for allergen display is not defined beyond “prominently displayed”.

---
**UW-007 — Add Item to Order**

- **Functional Area:** Menu Browsing
- **Source References:** FR-007
- **Preconditions:**
  - The customer is in self-service mode with an active cart context.
  - The selected menu item is enabled and visible.
- **Input Constraints:**
  - Input is a customer action on an enabled item.
  - The same item may be added more than once.
- **Validation Rules:**
  - Adding an item updates the active cart.
  - Repeated adds of the same item are cumulative and increase quantity.
- **System Behaviours (Success):**
  - The item appears in the cart with the correct quantity and line total.
- **System Behaviours (Failure):**
  - Unavailable or hidden items must not be added to the cart.
- **Postconditions:**
  - The cart reflects the latest selected items.
- **Edge/Boundary Conditions:**
  - Fast repeated taps must not create inconsistent quantities.
  - Adding the same item from different views must merge into one line item.
- **Error Handling:**
  - Show a non-blocking message if the item became unavailable before the add request completed.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define any maximum quantity per item.

---
**UW-008 — Adjust Item Quantity**

- **Functional Area:** Menu Browsing
- **Source References:** FR-008
- **Preconditions:**
  - The cart already contains the target item.
- **Input Constraints:**
  - Quantity change input applies to an existing line item only.
- **Validation Rules:**
  - Increasing quantity increments the count.
  - Decreasing quantity updates the count.
  - Reducing quantity to zero removes the item from the cart.
- **System Behaviours (Success):**
  - The cart quantity and totals update immediately.
- **System Behaviours (Failure):**
  - Quantities below zero are invalid and must be rejected.
- **Postconditions:**
  - The line item reflects the requested valid quantity or is removed at zero.
- **Edge/Boundary Conditions:**
  - Zero is the removal boundary.
  - Rapid increment/decrement actions must keep a consistent final quantity.
- **Error Handling:**
  - Show inline feedback if a decrement is attempted on an item no longer in the cart.
- **⚠️ Gaps:**
  - ⚠️ No upper quantity boundary is defined.

---
**UW-009 — Running Order Summary**

- **Functional Area:** Menu Browsing
- **Source References:** FR-009
- **Preconditions:**
  - The customer is browsing the menu in self-service mode.
- **Input Constraints:**
  - The summary consumes the current cart state and item prices.
- **Validation Rules:**
  - The total always reflects the latest selections.
  - The summary stays visible at the bottom of the menu page.
- **System Behaviours (Success):**
  - The item list and total refresh immediately after cart changes.
- **System Behaviours (Failure):**
  - A stale total or hidden summary is invalid.
- **Postconditions:**
  - The customer can review cost impact before checkout.
- **Edge/Boundary Conditions:**
  - Removing the last item returns the summary to an empty-cart state.
  - Price changes made after carting an item are not specified for in-flight sessions.
- **Error Handling:**
  - ⚠️ No explicit fallback is defined if price recalculation fails.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define whether in-session admin price changes recalculate existing carts.

---
**UW-010 — Order Review Before Submission**

- **Functional Area:** Self-Service Order Submission
- **Source References:** FR-010
- **Preconditions:**
  - The cart contains at least one item.
  - The session is in self-service mode.
- **Input Constraints:**
  - The review step reads the final cart contents and total.
- **Validation Rules:**
  - The review step is mandatory.
  - No modifications are allowed after the customer confirms the order.
- **System Behaviours (Success):**
  - The customer sees the complete order summary and can proceed to payment selection.
- **System Behaviours (Failure):**
  - Bypassing review or editing after confirmation is blocked.
- **Postconditions:**
  - The reviewed order snapshot is ready for payment selection and submission.
- **Edge/Boundary Conditions:**
  - Browser back-navigation after confirmation must not reopen editable state without revalidation.
- **Error Handling:**
  - ⚠️ The specification does not define whether a customer may cancel and return to the cart from review.
- **⚠️ Gaps:**
  - ⚠️ Cancel/return behaviour from the review step is not specified.

---
**UW-011 — Payment Method Selection**

- **Functional Area:** Self-Service Order Submission
- **Source References:** FR-011; NFR-005
- **Preconditions:**
  - The order review step has been completed.
- **Input Constraints:**
  - Allowed values are card or cash only.
  - One payment method must be selected before submission.
- **Validation Rules:**
  - Selection is mandatory.
  - Card payments must route through the third-party gateway without raw card handling by the app.
  - Cash payments must not trigger gateway interaction.
- **System Behaviours (Success):**
  - The chosen payment method is stored on the pending order.
- **System Behaviours (Failure):**
  - Submitting with no method selected is blocked.
  - Unsupported values are rejected.
- **Postconditions:**
  - The pending order has exactly one valid payment method.
- **Edge/Boundary Conditions:**
  - Re-selecting the same method must not duplicate payment initialisation.
  - Switching from card to cash before submission must cancel the card path cleanly.
- **Error Handling:**
  - Display a clear validation message when no payment method is selected.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define how payment-method selection is presented to assistive technologies.

---
**UW-012 — Order Submission and Number Assignment**

- **Functional Area:** Self-Service Order Submission
- **Source References:** FR-012; NFR-001; NFR-004; NFR-005
- **Preconditions:**
  - The reviewed order has at least one item and a selected payment method.
  - Card payments have a successful gateway response before order confirmation.
- **Input Constraints:**
  - Input is the confirmed order payload plus the selected payment method.
  - Order numbers must be unique per service session.
- **Validation Rules:**
  - A successful submission persists the order and assigns one unique order number.
  - Card-payment failures must not create a confirmed order.
  - The confirmation outcome should be available within 3 seconds of submission.
- **System Behaviours (Success):**
  - The system stores the order, assigns a unique number, and exposes it to downstream display logic.
- **System Behaviours (Failure):**
  - The system leaves the order unconfirmed if payment fails or submission cannot complete safely.
- **Postconditions:**
  - Exactly one confirmed order record exists for a successful submission.
- **Edge/Boundary Conditions:**
  - Back-end retries must not create duplicate order numbers for one customer action.
  - Two successful orders in the same service session must still receive distinct numbers.
- **Error Handling:**
  - Show a payment/submission failure message and offer a retry or alternate payment path when card payment fails.
- **⚠️ Gaps:**
  - ⚠️ The order-number format is preferred to be sequential or short, but not formally specified.
  - ⚠️ No idempotency mechanism is explicitly defined for duplicate submit taps.

---
**UW-013 — Order Confirmation Display**

- **Functional Area:** Self-Service Order Submission
- **Source References:** FR-013; NFR-001
- **Preconditions:**
  - A self-service order has been confirmed successfully.
- **Input Constraints:**
  - The confirmation screen consumes the persisted order number.
- **Validation Rules:**
  - The assigned order number must be visible immediately after success.
  - The screen must explain that the public display will later show the order number when ready.
- **System Behaviours (Success):**
  - The customer sees a confirmation page with order number and next-step guidance within 3 seconds.
- **System Behaviours (Failure):**
  - A missing order number or missing pickup guidance makes the confirmation invalid.
- **Postconditions:**
  - The customer can leave the checkout flow while retaining the order number reference.
- **Edge/Boundary Conditions:**
  - Refreshing the confirmation screen must not generate a new order.
- **Error Handling:**
  - ⚠️ No alternate recovery path is specified if the order succeeds but the confirmation screen fails to render.
- **⚠️ Gaps:**
  - ⚠️ The exact pickup guidance wording is not specified.

---
**UW-014 — Empty Cart Validation**

- **Functional Area:** Self-Service Order Submission
- **Source References:** FR-014
- **Preconditions:**
  - The customer is in self-service mode and attempts to reach submission logic.
- **Input Constraints:**
  - The validation reads the current cart state.
- **Validation Rules:**
  - Submission is blocked when the cart is empty.
  - The customer is prompted to add at least one item before proceeding.
- **System Behaviours (Success):**
  - A non-empty cart can proceed to review and payment steps.
- **System Behaviours (Failure):**
  - An empty cart cannot be submitted.
- **Postconditions:**
  - The cart remains editable until at least one item exists.
- **Edge/Boundary Conditions:**
  - A cart that becomes empty after removing the last line item must immediately re-trigger the block.
- **Error Handling:**
  - Display a direct message instructing the customer to add at least one item.
- **⚠️ Gaps:**
  - ⚠️ The specification does not say whether the checkout button is hidden, disabled, or allowed to trigger a message.

---
**UW-015 — Menu Display in Staff-Assisted Mode**

- **Functional Area:** Staff-Assisted Service Request
- **Source References:** FR-015
- **Preconditions:**
  - The session is active and staff-assisted mode is selected.
- **Input Constraints:**
  - The system reads the current enabled menu catalogue.
- **Validation Rules:**
  - The menu is displayed in a browse-only state.
  - The customer cannot add items to a cart or submit an order in this mode.
- **System Behaviours (Success):**
  - Customers can preview items before staff arrive.
- **System Behaviours (Failure):**
  - Interactive self-service controls are suppressed in assisted mode.
- **Postconditions:**
  - The customer remains in a browse-only state until readiness is signalled.
- **Edge/Boundary Conditions:**
  - Deep links to cart or payment screens must remain inaccessible in assisted mode.
- **Error Handling:**
  - ⚠️ No explicit message is defined to explain why cart actions are unavailable.
- **⚠️ Gaps:**
  - ⚠️ The specification does not say whether prices/totals are shown differently in browse-only mode.

---
**UW-016 — Customer Readiness Signal**

- **Functional Area:** Staff-Assisted Service Request
- **Source References:** FR-016
- **Preconditions:**
  - The customer is in an active staff-assisted session.
- **Input Constraints:**
  - Input is a tap/click on the readiness action.
  - The trigger is one-time per session.
- **Validation Rules:**
  - The readiness action records a session event.
  - The action cannot be undone once triggered.
- **System Behaviours (Success):**
  - The system records the request and moves the session to a waiting-for-staff state.
- **System Behaviours (Failure):**
  - Repeated activation attempts after the first trigger are rejected or ignored.
- **Postconditions:**
  - The session reflects that staff assistance has been requested.
- **Edge/Boundary Conditions:**
  - Double tapping must still result in only one readiness event.
- **Error Handling:**
  - Show clear acknowledgement that staff have been called.
  - ⚠️ The exact acknowledgement text is not specified.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define whether an accidental readiness request can be cancelled by staff.

---
**UW-017 — Staff Notification**

- **Functional Area:** Staff-Assisted Service Request
- **Source References:** FR-017
- **Preconditions:**
  - A readiness event has been recorded.
  - The session still has a valid table reference.
- **Input Constraints:**
  - Notification payload includes the identified table number.
- **Validation Rules:**
  - The system notifies staff when readiness is confirmed.
  - The notification must include the table number.
- **System Behaviours (Success):**
  - A staff-facing channel receives a notification linked to the requesting table.
- **System Behaviours (Failure):**
  - If the table reference is missing, the notification must not be sent with wrong data.
- **Postconditions:**
  - Staff can identify which table to approach.
- **Edge/Boundary Conditions:**
  - Multiple staff recipients must still see the same table number.
  - Retry behaviour is not specified if delivery is delayed.
- **Error Handling:**
  - ⚠️ The specification does not define delivery retries, acknowledgement, or escalation if notification delivery fails.
- **⚠️ Gaps:**
  - ⚠️ Notification transport and failure handling are unspecified.

---
**UW-018 — No Payment or Order Number in Staff Mode**

- **Functional Area:** Staff-Assisted Service Request
- **Source References:** FR-018
- **Preconditions:**
  - The session is in staff-assisted mode.
- **Input Constraints:**
  - All navigation attempts are interpreted in the context of staff-assisted mode.
- **Validation Rules:**
  - The app must not process payment in assisted mode.
  - The app must not generate an order number in assisted mode.
- **System Behaviours (Success):**
  - The session ends with staff notification only, leaving order capture and payment to staff.
- **System Behaviours (Failure):**
  - Any attempt to reach self-service checkout screens in assisted mode is blocked.
- **Postconditions:**
  - No app-side order record or payment transaction exists for the assisted session.
- **Edge/Boundary Conditions:**
  - Users reopening the session later must still remain outside the self-service checkout unless the flow is restarted.
- **Error Handling:**
  - Show a mode-based access message if an assisted customer reaches a self-service route.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define whether staff can convert an assisted session into a self-service session.

---
**UW-019 — Public Order Status Display**

- **Functional Area:** Order Status Display
- **Source References:** FR-019
- **Preconditions:**
  - At least one self-service order may exist.
  - A display screen is available in the venue.
- **Input Constraints:**
  - Input is the current set of active self-service orders.
  - Viewing the board requires no login.
- **Validation Rules:**
  - The display is public and read-only.
  - No authentication is required to view it.
- **System Behaviours (Success):**
  - Customers can open or see the board and monitor active orders.
- **System Behaviours (Failure):**
  - Admin-only controls must not appear on the public board.
- **Postconditions:**
  - Customers can independently inspect order progress.
- **Edge/Boundary Conditions:**
  - The board should remain meaningful when there are zero active orders.
  - ⚠️ Empty-board content is unspecified.
- **Error Handling:**
  - ⚠️ No explicit unavailable-display fallback is specified.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define the empty-state message for the public display.

---
**UW-020 — Order Status Tracking**

- **Functional Area:** Order Status Display
- **Source References:** FR-020
- **Preconditions:**
  - A self-service order exists with a valid order number.
- **Input Constraints:**
  - Allowed public statuses are In Preparation and Ready for Pickup.
- **Validation Rules:**
  - Orders appear as In Preparation until marked ready.
  - Ready orders move to Ready for Pickup.
  - Only self-service orders participate in the board.
- **System Behaviours (Success):**
  - The board reflects the current status of each active self-service order.
- **System Behaviours (Failure):**
  - Unsupported statuses or staff-assisted sessions must not appear.
- **Postconditions:**
  - Customers can correlate their order number with one of the two allowed states.
- **Edge/Boundary Conditions:**
  - The board must not show duplicate lines for the same order number.
  - An order must change state without disappearing prematurely.
- **Error Handling:**
  - ⚠️ No ordering/sorting rule is specified for multiple active order numbers.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define how the board orders or paginates many simultaneous orders.

---
**UW-021 — Admin Mark Order Ready**

- **Functional Area:** Order Status Display
- **Source References:** FR-021
- **Preconditions:**
  - The admin is authenticated.
  - At least one self-service order is currently In Preparation.
- **Input Constraints:**
  - Input is an admin action on a specific eligible order.
- **Validation Rules:**
  - Only admins may change order status.
  - Changing an order to Ready for Pickup updates the public display without delay.
- **System Behaviours (Success):**
  - The selected order moves to Ready for Pickup on the board.
- **System Behaviours (Failure):**
  - Unauthorised users cannot change order status.
  - Orders outside the eligible state must not transition incorrectly.
- **Postconditions:**
  - The order is publicly visible as ready until removed.
- **Edge/Boundary Conditions:**
  - Repeated ready actions must be idempotent.
  - ⚠️ “Without delay” is not quantified.
- **Error Handling:**
  - Show an access-denied or invalid-state message when the action is not allowed.
- **⚠️ Gaps:**
  - ⚠️ The maximum acceptable propagation delay to the public display is unspecified.

---
**UW-022 — Order Removal from Display**

- **Functional Area:** Order Status Display
- **Source References:** FR-022
- **Preconditions:**
  - The order is already displayed as Ready for Pickup.
- **Input Constraints:**
  - Removal can be triggered by admin collection confirmation or timeout expiry.
- **Validation Rules:**
  - Collected orders are removed from the display.
  - A configurable timeout removes stale ready orders.
- **System Behaviours (Success):**
  - The order number disappears from the public board when a valid removal condition occurs.
- **System Behaviours (Failure):**
  - Orders must remain visible until collection or timeout actually occurs.
- **Postconditions:**
  - The public board contains only currently active ready orders.
- **Edge/Boundary Conditions:**
  - Timeout must be configurable.
  - Orders just below the timeout threshold must remain visible.
- **Error Handling:**
  - ⚠️ Default timeout value and configuration constraints are not defined.
- **⚠️ Gaps:**
  - ⚠️ The default timeout, minimum timeout, and who may configure it are not specified.

---
**UW-023 — Admin Interface Access Control**

- **Functional Area:** Menu Management
- **Source References:** FR-023; NFR-006
- **Preconditions:**
  - The admin interface is reachable from a supported browser.
- **Input Constraints:**
  - Credentials consist of username and password.
  - Only authorised admin accounts may authenticate.
- **Validation Rules:**
  - Valid credentials create an authenticated admin session.
  - Invalid credentials are handled gracefully.
  - Admin sessions must expire after a configurable inactivity period.
- **System Behaviours (Success):**
  - An authenticated admin can access protected admin functions.
- **System Behaviours (Failure):**
  - Invalid credentials do not reveal which field was wrong.
  - Expired sessions force re-authentication.
- **Postconditions:**
  - Protected features remain available only inside an active admin session.
- **Edge/Boundary Conditions:**
  - Idle-session expiry must occur after the configured threshold.
  - Direct access to admin URLs without login must redirect or deny access.
- **Error Handling:**
  - Show a generic authentication error for invalid login attempts.
  - Show a session-expired message on inactivity timeout.
- **⚠️ Gaps:**
  - ⚠️ The inactivity timeout value is explicitly marked TO BE REFINED.
  - ⚠️ No lockout or rate-limit rule is defined for repeated failed logins.

---
**UW-024 — Add Menu Item**

- **Functional Area:** Menu Management
- **Source References:** FR-024
- **Preconditions:**
  - The admin is authenticated and on the menu-management interface.
- **Input Constraints:**
  - Mandatory fields are name, price, category, allergen information, and at least one photo.
  - Description is also captured by the form.
- **Validation Rules:**
  - Partial submissions are rejected.
  - A valid submission persists the item.
  - The item becomes customer-visible if it is enabled.
- **System Behaviours (Success):**
  - The new menu item is saved with complete details.
- **System Behaviours (Failure):**
  - Missing mandatory fields block save.
- **Postconditions:**
  - A new item record exists for future customer sessions.
- **Edge/Boundary Conditions:**
  - Special characters in names or descriptions must persist correctly.
  - Large image files are not constrained in the specification.
- **Error Handling:**
  - Display field-level validation for each missing mandatory field.
- **⚠️ Gaps:**
  - ⚠️ Allowed price precision, photo size limits, and category value set are not specified.

---
**UW-025 — Edit Menu Item**

- **Functional Area:** Menu Management
- **Source References:** FR-025
- **Preconditions:**
  - The admin is authenticated and a target menu item already exists.
- **Input Constraints:**
  - Editable fields include name, description, price, category, allergen information, and photo.
- **Validation Rules:**
  - Edits persist to the menu item record.
  - Changes to price or allergen data take effect immediately for subsequent customer sessions.
- **System Behaviours (Success):**
  - Updated values are stored and exposed to future customers.
- **System Behaviours (Failure):**
  - Invalid field values must block the update.
- **Postconditions:**
  - The menu item reflects the new values for subsequent sessions.
- **Edge/Boundary Conditions:**
  - A customer session already in progress may or may not see the change; this is unspecified.
  - Replacing the photo must not erase mandatory allergen data.
- **Error Handling:**
  - Show validation messages for invalid edited values.
- **⚠️ Gaps:**
  - ⚠️ Behaviour for already-open customer sessions after an edit is not specified.

---
**UW-026 — Enable or Disable Menu Item**

- **Functional Area:** Menu Management
- **Source References:** FR-026
- **Preconditions:**
  - The admin is authenticated and a target item exists.
- **Input Constraints:**
  - Input is a visibility toggle on an existing menu item.
- **Validation Rules:**
  - Disabled items are hidden from customers.
  - Re-enabled items become visible again.
  - Disabling an item does not alter already placed orders that contain it.
- **System Behaviours (Success):**
  - The visibility state changes immediately for customer-facing availability.
- **System Behaviours (Failure):**
  - Customers must not add newly disabled items from fresh sessions.
- **Postconditions:**
  - The item remains stored with the selected enabled/disabled state.
- **Edge/Boundary Conditions:**
  - Cached customer pages must not permit successful addition of a newly disabled item.
  - Existing confirmed orders keep the historical item reference.
- **Error Handling:**
  - Show the updated visibility state clearly in the admin UI.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define whether in-progress carts containing a newly disabled item may still submit.

---
**UW-027 — Remove Menu Item Permanently**

- **Functional Area:** Menu Management
- **Source References:** FR-027
- **Preconditions:**
  - The admin is authenticated and a target item exists.
- **Input Constraints:**
  - Input is an admin delete command on a specific menu item.
- **Validation Rules:**
  - Permanent removal requires confirmation.
  - Confirmed removal deletes the menu item from the active catalogue.
- **System Behaviours (Success):**
  - The menu item is deleted only after the admin confirms the action.
- **System Behaviours (Failure):**
  - Cancelling or skipping confirmation must keep the item unchanged.
- **Postconditions:**
  - The deleted item is no longer available for future customer sessions.
- **Edge/Boundary Conditions:**
  - Historical-order retention after deletion is not specified.
  - Repeated delete attempts on an already deleted item must not corrupt data.
- **Error Handling:**
  - Ask for confirmation before deleting and show a clear result message.
- **⚠️ Gaps:**
  - ⚠️ The specification does not define how deleted items are represented in historical reporting or past orders.
