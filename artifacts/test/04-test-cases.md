# Test Specification — Stage 4: Formatted Test Cases

All formatted test cases were generated from Stage 3 scenarios and checked for mandatory fields, numbered steps, and traceability.

## Functional Area: Customer Onboarding

---
**Test Case: UW-001-TC-001**

| Field | Detail |
| --- | --- |
| Title | Scan a valid table QR code |
| Functional Area | Customer Onboarding |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Customer is at table T12 with a supported mobile browser. |
| Test Data | QR payload: tableorder://table/T12 |
| Expected Result | The app opens a new session for table T12 and displays the name-entry step. |
| Postconditions | Active customer session exists for table T12. |
| Traceability | UW-001; FR-001 |

**Test Steps:**
1. Open the camera or QR scanner on the mobile device.
2. Scan the QR code containing `tableorder://table/T12`.
3. Allow the browser to open the TableOrder web app.
4. Verify the landing flow opens for table T12 and requests the customer name.


---
**Test Case: UW-001-TC-002**

| Field | Detail |
| --- | --- |
| Title | Reject an unrecognised QR code |
| Functional Area | Customer Onboarding |
| Test Type | Negative |
| Priority | High |
| Preconditions | Customer is on a supported mobile browser. |
| Test Data | QR payload: tableorder://table/UNKNOWN |
| Expected Result | The app blocks session creation and shows an invalid-table error with retry guidance. |
| Postconditions | No active session is created. |
| Traceability | UW-001; FR-001 |

**Test Steps:**
1. Open the QR scanner on the mobile device.
2. Scan the QR code containing `tableorder://table/UNKNOWN`.
3. Wait for the browser to open the app.
4. Verify the app does not proceed past activation and shows an invalid-code message.


---
**Test Case: UW-002-TC-001**

| Field | Detail |
| --- | --- |
| Title | Accept a valid customer name |
| Functional Area | Customer Onboarding |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | A valid table session is active at the name-entry step. |
| Test Data | Name: Alice Morgan |
| Expected Result | The name is saved in the session and the service-mode selection step is shown. |
| Postconditions | Session contains customer name `Alice Morgan`. |
| Traceability | UW-002; FR-002; NFR-007 |

**Test Steps:**
1. Scan a valid table QR code.
2. Enter `Alice Morgan` in the name field.
3. Tap the continue action.
4. Verify the app stores the name and opens service-mode selection.


---
**Test Case: UW-002-TC-002**

| Field | Detail |
| --- | --- |
| Title | Reject an empty customer name |
| Functional Area | Customer Onboarding |
| Test Type | Negative |
| Priority | High |
| Preconditions | A valid table session is active at the name-entry step. |
| Test Data | Name: "   " |
| Expected Result | The app keeps the customer on the name-entry step and shows an inline required-field message. |
| Postconditions | Session has no stored customer name. |
| Traceability | UW-002; FR-002; NFR-007 |

**Test Steps:**
1. Scan a valid table QR code.
2. Enter three spaces in the name field.
3. Tap the continue action.
4. Verify the app does not advance and shows a required-name validation message.


---
**Test Case: UW-003-TC-001**

| Field | Detail |
| --- | --- |
| Title | Choose self-service mode |
| Functional Area | Customer Onboarding |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | A valid session exists and a customer name has been captured. |
| Test Data | Mode: Self-service |
| Expected Result | The app stores self-service mode and opens the self-service menu flow. |
| Postconditions | Session mode is `self-service`. |
| Traceability | UW-003; FR-003 |

**Test Steps:**
1. Complete QR activation and valid name entry.
2. Tap the `Self-service` option.
3. Tap continue if the UI requires confirmation.
4. Verify the menu opens with cart and checkout controls available.


---
**Test Case: UW-003-TC-002**

| Field | Detail |
| --- | --- |
| Title | Block progress with no service mode selected |
| Functional Area | Customer Onboarding |
| Test Type | Negative |
| Priority | High |
| Preconditions | A valid session exists and a customer name has been captured. |
| Test Data | Mode: none |
| Expected Result | The app prevents navigation and prompts the customer to select one mode. |
| Postconditions | Session has no selected mode. |
| Traceability | UW-003; FR-003 |

**Test Steps:**
1. Complete QR activation and valid name entry.
2. Leave both service modes unselected.
3. Tap the continue action.
4. Verify the app remains on the selection step and shows a validation prompt.


---
**Test Case: UW-003-TC-003**

| Field | Detail |
| --- | --- |
| Title | Prevent mode switching after the downstream flow starts |
| Functional Area | Customer Onboarding |
| Test Type | State |
| Priority | Medium |
| Preconditions | A session is already routed into the self-service menu flow. |
| Test Data | Initial mode: Self-service; second action: Staff-assisted |
| Expected Result | The app keeps the original self-service flow or forces an explicit restart instead of silently switching modes. |
| Postconditions | Session remains bound to one service mode. |
| Traceability | UW-003; FR-003 |

**Test Steps:**
1. Start a session and select `Self-service`.
2. Enter the menu flow.
3. Use the browser back button or direct navigation to return to the mode step.
4. Attempt to switch to `Staff-assisted` and verify the original mode remains locked or a restart is required.


---
**Test Case: UW-004-TC-001**

| Field | Detail |
| --- | --- |
| Title | Persist the table reference through checkout |
| Functional Area | Customer Onboarding |
| Test Type | State |
| Priority | Critical |
| Preconditions | A valid QR code for table T12 is available. |
| Test Data | Table: T12; Customer: Alice Morgan; Payment: Cash |
| Expected Result | The confirmed order keeps table T12 as its origin from activation through confirmation. |
| Postconditions | Confirmed order is linked to table T12. |
| Traceability | UW-004; FR-004 |

**Test Steps:**
1. Start a session from the QR code for table T12.
2. Complete the self-service flow with one menu item and cash payment.
3. Submit the order successfully.
4. Verify the resulting order record and confirmation are associated with table T12.


---
**Test Case: UW-004-TC-002**

| Field | Detail |
| --- | --- |
| Title | Block downstream actions if table context is lost |
| Functional Area | Customer Onboarding |
| Test Type | Negative |
| Priority | High |
| Preconditions | An active session exists but the stored table reference is deliberately removed or corrupted. |
| Test Data | Session with missing table reference |
| Expected Result | Checkout or staff notification is blocked and the customer sees a session-recovery error. |
| Postconditions | No order or staff notification is created. |
| Traceability | UW-004; FR-004 |

**Test Steps:**
1. Create a valid session from a QR code.
2. Corrupt or clear the stored table reference in the session.
3. Try to proceed to checkout or trigger staff readiness.
4. Verify the app blocks the action and shows a recoverable session error.


## Functional Area: Menu Browsing

---
**Test Case: UW-005-TC-001**

| Field | Detail |
| --- | --- |
| Title | Show only enabled menu items grouped by category |
| Functional Area | Menu Browsing |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Admin has enabled `Classic Burger` and `Cola 330ml` and disabled `IPA Beer`. |
| Test Data | Enabled items: Classic Burger, Cola 330ml; Disabled item: IPA Beer |
| Expected Result | The customer sees Classic Burger and Cola under their categories and does not see IPA Beer. |
| Postconditions | Customer can browse current enabled categories. |
| Traceability | UW-005; FR-005; NFR-002; NFR-009 |

**Test Steps:**
1. Start a self-service session.
2. Open the menu page.
3. Observe the categories and listed items.
4. Verify enabled items appear in the right categories and disabled `IPA Beer` is absent.


---
**Test Case: UW-005-TC-002**

| Field | Detail |
| --- | --- |
| Title | Keep disabled items hidden after a fresh menu load |
| Functional Area | Menu Browsing |
| Test Type | Negative |
| Priority | High |
| Preconditions | Admin has disabled `Vegan Salad` before the customer opens the menu. |
| Test Data | Disabled item: Vegan Salad |
| Expected Result | The customer cannot find or open Vegan Salad from the refreshed menu. |
| Postconditions | Disabled item remains unavailable to the customer. |
| Traceability | UW-005; FR-005; NFR-002; NFR-009 |

**Test Steps:**
1. Disable `Vegan Salad` in the admin interface.
2. Start a new self-service session.
3. Open the menu and search visually for `Vegan Salad`.
4. Verify the item does not appear anywhere in the customer menu.


---
**Test Case: UW-006-TC-001**

| Field | Detail |
| --- | --- |
| Title | Display complete item details for a published menu item |
| Functional Area | Menu Browsing |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | `Classic Burger` is enabled with complete item data. |
| Test Data | Item: Classic Burger; Price: 12.50 EUR; Allergens: gluten, milk; Photo: burger.jpg |
| Expected Result | The item card shows name, description, price, allergen list, and at least one photo. |
| Postconditions | Customer can inspect full item details before ordering. |
| Traceability | UW-006; FR-006 |

**Test Steps:**
1. Start a self-service session.
2. Open the menu.
3. Open or inspect the `Classic Burger` item card.
4. Verify name, description, `12.50 EUR`, allergens `gluten, milk`, and a photo are visible.


---
**Test Case: UW-006-TC-002**

| Field | Detail |
| --- | --- |
| Title | Suppress publication of an item missing allergen information |
| Functional Area | Menu Browsing |
| Test Type | Negative |
| Priority | High |
| Preconditions | Admin saved or attempted to publish `Lemon Tart` without allergen data. |
| Test Data | Item: Lemon Tart; Allergens: missing |
| Expected Result | The item is not visible to customers until allergen information is completed. |
| Postconditions | Customer menu excludes the incomplete item. |
| Traceability | UW-006; FR-006 |

**Test Steps:**
1. Create or edit `Lemon Tart` so allergen information is empty.
2. Start a new customer session.
3. Open the menu page.
4. Verify `Lemon Tart` is not published in the customer menu.


---
**Test Case: UW-007-TC-001**

| Field | Detail |
| --- | --- |
| Title | Add one enabled item to the cart |
| Functional Area | Menu Browsing |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Customer is in self-service mode on the menu page. |
| Test Data | Item: Classic Burger at 12.50 EUR |
| Expected Result | The cart contains Classic Burger with quantity 1 and line total 12.50 EUR. |
| Postconditions | Cart contains one Classic Burger. |
| Traceability | UW-007; FR-007 |

**Test Steps:**
1. Open the menu in a self-service session.
2. Locate `Classic Burger`.
3. Tap the add action once.
4. Verify the cart shows `Classic Burger` quantity 1 with total `12.50 EUR`.


---
**Test Case: UW-007-TC-002**

| Field | Detail |
| --- | --- |
| Title | Increment quantity when the same item is added twice |
| Functional Area | Menu Browsing |
| Test Type | State |
| Priority | High |
| Preconditions | Customer is in self-service mode on the menu page. |
| Test Data | Item: Cola 330ml at 3.00 EUR added twice |
| Expected Result | The cart contains one line for Cola 330ml with quantity 2 and line total 6.00 EUR. |
| Postconditions | Cart quantity for Cola 330ml is 2. |
| Traceability | UW-007; FR-007 |

**Test Steps:**
1. Open the menu in a self-service session.
2. Tap add on `Cola 330ml` twice.
3. Open the cart or summary.
4. Verify the cart shows a single `Cola 330ml` line with quantity 2 and total `6.00 EUR`.


---
**Test Case: UW-008-TC-001**

| Field | Detail |
| --- | --- |
| Title | Increase an existing line-item quantity |
| Functional Area | Menu Browsing |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Cart already contains `Margherita Pizza` quantity 1. |
| Test Data | Item: Margherita Pizza from quantity 1 to 2 |
| Expected Result | The cart updates Margherita Pizza to quantity 2 and recalculates totals. |
| Postconditions | Cart shows quantity 2. |
| Traceability | UW-008; FR-008 |

**Test Steps:**
1. Open a self-service session with `Margherita Pizza` already in the cart.
2. Tap the increase quantity control once.
3. Observe the cart summary.
4. Verify the quantity becomes 2 and totals increase accordingly.


---
**Test Case: UW-008-TC-002**

| Field | Detail |
| --- | --- |
| Title | Remove an item by decreasing quantity to zero |
| Functional Area | Menu Browsing |
| Test Type | Boundary |
| Priority | High |
| Preconditions | Cart contains `Margherita Pizza` quantity 1. |
| Test Data | Item: Margherita Pizza from quantity 1 to 0 |
| Expected Result | The item is removed from the cart when quantity reaches zero. |
| Postconditions | Cart no longer contains Margherita Pizza. |
| Traceability | UW-008; FR-008 |

**Test Steps:**
1. Open a self-service session with `Margherita Pizza` quantity 1 in the cart.
2. Tap the decrease quantity control once.
3. Observe the cart summary.
4. Verify the item disappears from the cart and the total is reduced.


---
**Test Case: UW-008-TC-003**

| Field | Detail |
| --- | --- |
| Title | Reject quantity changes below zero |
| Functional Area | Menu Browsing |
| Test Type | Negative |
| Priority | Medium |
| Preconditions | Cart contains no `Cola 330ml` item or the line is already at zero. |
| Test Data | Attempted quantity: -1 for Cola 330ml |
| Expected Result | The app prevents the quantity going below zero and leaves the cart unchanged. |
| Postconditions | Cart remains unchanged. |
| Traceability | UW-008; FR-008 |

**Test Steps:**
1. Open the menu with no `Cola 330ml` in the cart.
2. Try to trigger a decrement on `Cola 330ml` or submit a quantity of `-1` through the client.
3. Observe the cart state.
4. Verify the app rejects the action and does not create a negative quantity.


---
**Test Case: UW-009-TC-001**

| Field | Detail |
| --- | --- |
| Title | Recalculate the running total after cart changes |
| Functional Area | Menu Browsing |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Customer is on the menu page in self-service mode. |
| Test Data | Classic Burger 12.50 EUR + Cola 330ml 3.00 EUR |
| Expected Result | The running summary shows two items and total 15.50 EUR immediately after the changes. |
| Postconditions | Summary reflects the latest cart state. |
| Traceability | UW-009; FR-009 |

**Test Steps:**
1. Open a self-service session.
2. Add `Classic Burger` once.
3. Add `Cola 330ml` once.
4. Verify the persistent summary shows total `15.50 EUR` and both items.


---
**Test Case: UW-009-TC-002**

| Field | Detail |
| --- | --- |
| Title | Return the summary to an empty-cart state after the last item is removed |
| Functional Area | Menu Browsing |
| Test Type | Boundary |
| Priority | Medium |
| Preconditions | Cart contains only `Classic Burger` quantity 1. |
| Test Data | Remove final cart item Classic Burger |
| Expected Result | The summary shows zero selected items and total 0.00 EUR after the last line is removed. |
| Postconditions | Cart is empty. |
| Traceability | UW-009; FR-009 |

**Test Steps:**
1. Open a self-service session with only `Classic Burger` in the cart.
2. Decrease the quantity to zero.
3. Observe the summary section.
4. Verify the summary returns to an empty-cart state with total `0.00 EUR`.


## Functional Area: Self-Service Order Submission

---
**Test Case: UW-010-TC-001**

| Field | Detail |
| --- | --- |
| Title | Show full order review before payment selection |
| Functional Area | Self-Service Order Submission |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Cart contains at least one item and customer is in self-service mode. |
| Test Data | Cart: Classic Burger x1, Cola 330ml x2 |
| Expected Result | The review screen lists every item, quantity, and the correct total before payment selection. |
| Postconditions | Pending order is ready for payment-method selection. |
| Traceability | UW-010; FR-010 |

**Test Steps:**
1. Build a cart with `Classic Burger x1` and `Cola 330ml x2`.
2. Tap the checkout action.
3. Observe the review screen.
4. Verify the screen lists both items, quantities, and total `18.50 EUR`.


---
**Test Case: UW-010-TC-002**

| Field | Detail |
| --- | --- |
| Title | Block cart edits after the customer confirms the review |
| Functional Area | Self-Service Order Submission |
| Test Type | State |
| Priority | High |
| Preconditions | Customer is on the order review screen with a non-empty cart. |
| Test Data | Confirmed review for cart total 18.50 EUR |
| Expected Result | After review confirmation, the customer cannot modify the order unless the flow explicitly returns to the cart. |
| Postconditions | Confirmed review remains locked for the current submission path. |
| Traceability | UW-010; FR-010 |

**Test Steps:**
1. Open the review screen with a non-empty cart.
2. Confirm that the order is correct.
3. Attempt to edit item quantities without returning to the cart.
4. Verify the app blocks edits on the confirmed review path.


---
**Test Case: UW-011-TC-001**

| Field | Detail |
| --- | --- |
| Title | Select card as the payment method |
| Functional Area | Self-Service Order Submission |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Customer is on the payment-method step after review. |
| Test Data | Payment method: card |
| Expected Result | The pending order stores card as the selected method and starts the gateway path only when the order is submitted. |
| Postconditions | Pending order has `card` selected. |
| Traceability | UW-011; FR-011; NFR-005 |

**Test Steps:**
1. Reach the payment-method step with a reviewed order.
2. Tap the `Card` option.
3. Observe the selected state.
4. Verify `Card` is selected and no order is yet submitted.


---
**Test Case: UW-011-TC-002**

| Field | Detail |
| --- | --- |
| Title | Select cash as the payment method |
| Functional Area | Self-Service Order Submission |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Customer is on the payment-method step after review. |
| Test Data | Payment method: cash |
| Expected Result | The pending order stores cash as the selected method without invoking the card gateway. |
| Postconditions | Pending order has `cash` selected. |
| Traceability | UW-011; FR-011; NFR-005 |

**Test Steps:**
1. Reach the payment-method step with a reviewed order.
2. Tap the `Cash` option.
3. Observe the selected state.
4. Verify `Cash` is selected and no card-gateway action is triggered.


---
**Test Case: UW-011-TC-003**

| Field | Detail |
| --- | --- |
| Title | Block order submission when no payment method is selected |
| Functional Area | Self-Service Order Submission |
| Test Type | Negative |
| Priority | High |
| Preconditions | Customer is on the payment-method step after review. |
| Test Data | Payment method: none |
| Expected Result | The app blocks submission and shows a required-payment-method validation message. |
| Postconditions | No order is submitted. |
| Traceability | UW-011; FR-011; NFR-005 |

**Test Steps:**
1. Reach the payment-method step with a reviewed order.
2. Leave both `Card` and `Cash` unselected.
3. Tap the submit order action.
4. Verify the app blocks submission and shows a payment-method validation message.


---
**Test Case: UW-012-TC-001**

| Field | Detail |
| --- | --- |
| Title | Submit a valid cash order and assign a unique order number |
| Functional Area | Self-Service Order Submission |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Customer has a reviewed non-empty order and selected `cash`. |
| Test Data | Order: Classic Burger x1; Payment: cash |
| Expected Result | The order is persisted successfully within 3 seconds and receives one unique order number. |
| Postconditions | One confirmed order record exists with a unique order number. |
| Traceability | UW-012; FR-012; NFR-001; NFR-004; NFR-005 |

**Test Steps:**
1. Build and review an order containing `Classic Burger x1`.
2. Select `Cash` as payment method.
3. Tap the submit order action.
4. Verify one confirmed order is created within 3 seconds and an order number is assigned.


---
**Test Case: UW-012-TC-002**

| Field | Detail |
| --- | --- |
| Title | Do not confirm the order when card payment fails |
| Functional Area | Self-Service Order Submission |
| Test Type | Negative |
| Priority | Critical |
| Preconditions | Customer has a reviewed non-empty order and selected `card`. |
| Test Data | Order: Classic Burger x1; Payment: card; Gateway result: DECLINED |
| Expected Result | The app shows a payment failure message and does not create an order record or assign an order number. |
| Postconditions | No confirmed order exists. |
| Traceability | UW-012; FR-012; NFR-001; NFR-004; NFR-005 |

**Test Steps:**
1. Build and review an order containing `Classic Burger x1`.
2. Select `Card` as payment method.
3. Force the payment gateway response to `DECLINED` and submit the order.
4. Verify the app shows a failure message and no confirmed order number is created.


---
**Test Case: UW-012-TC-003**

| Field | Detail |
| --- | --- |
| Title | Assign different order numbers to two successful submissions in one service session |
| Functional Area | Self-Service Order Submission |
| Test Type | State |
| Priority | High |
| Preconditions | A customer session can place two separate successful orders one after the other. |
| Test Data | Submission 1: Classic Burger x1; Submission 2: Cola 330ml x1 |
| Expected Result | Each successful submission receives a distinct order number even within the same service session. |
| Postconditions | Two confirmed orders exist with different order numbers. |
| Traceability | UW-012; FR-012; NFR-001; NFR-004; NFR-005 |

**Test Steps:**
1. Submit a first successful self-service order in one session.
2. Return to menu and build a second valid order in the same session.
3. Submit the second order successfully.
4. Verify the two confirmed orders have different order numbers.


---
**Test Case: UW-013-TC-001**

| Field | Detail |
| --- | --- |
| Title | Show order number and pickup guidance on confirmation |
| Functional Area | Self-Service Order Submission |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | A self-service order has been confirmed successfully. |
| Test Data | Confirmed order number: A127 |
| Expected Result | The confirmation screen shows order number A127 and tells the customer to watch the public display for pickup readiness. |
| Postconditions | Customer can note order number A127 for later tracking. |
| Traceability | UW-013; FR-013; NFR-001 |

**Test Steps:**
1. Complete a successful self-service order.
2. Wait for the confirmation screen.
3. Read the confirmation content.
4. Verify the assigned order number and pickup guidance are both visible.


---
**Test Case: UW-013-TC-002**

| Field | Detail |
| --- | --- |
| Title | Refresh the confirmation screen without creating a duplicate order |
| Functional Area | Self-Service Order Submission |
| Test Type | State |
| Priority | High |
| Preconditions | A self-service order confirmation page is already open. |
| Test Data | Confirmed order number: A127; user action: browser refresh |
| Expected Result | Refreshing the confirmation page shows the existing order number and does not create a second order. |
| Postconditions | Still only one confirmed order exists for the submission. |
| Traceability | UW-013; FR-013; NFR-001 |

**Test Steps:**
1. Complete a successful self-service order.
2. Stay on the confirmation page.
3. Refresh the browser page once.
4. Verify the page still shows the same order number and no duplicate order was created.


---
**Test Case: UW-014-TC-001**

| Field | Detail |
| --- | --- |
| Title | Block checkout when the cart is empty |
| Functional Area | Self-Service Order Submission |
| Test Type | Negative |
| Priority | Critical |
| Preconditions | Customer is in self-service mode with an empty cart. |
| Test Data | Cart items: none |
| Expected Result | The customer cannot submit and sees a prompt to add at least one item. |
| Postconditions | Cart remains empty and no order exists. |
| Traceability | UW-014; FR-014 |

**Test Steps:**
1. Start a self-service session without adding any items.
2. Open checkout if the UI allows it or tap submit.
3. Observe the response.
4. Verify the app blocks progress and prompts the customer to add at least one item.


---
**Test Case: UW-014-TC-002**

| Field | Detail |
| --- | --- |
| Title | Allow checkout once one item exists in the cart |
| Functional Area | Self-Service Order Submission |
| Test Type | Boundary |
| Priority | High |
| Preconditions | Customer is in self-service mode. |
| Test Data | Cart: Cola 330ml x1 |
| Expected Result | A cart containing exactly one item can proceed to the review step. |
| Postconditions | Review step is available. |
| Traceability | UW-014; FR-014 |

**Test Steps:**
1. Start a self-service session.
2. Add `Cola 330ml` once.
3. Tap the checkout action.
4. Verify the order review screen opens successfully.


## Functional Area: Staff-Assisted Service Request

---
**Test Case: UW-015-TC-001**

| Field | Detail |
| --- | --- |
| Title | Show the menu in browse-only mode for staff-assisted service |
| Functional Area | Staff-Assisted Service Request |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Customer has selected staff-assisted mode. |
| Test Data | Mode: staff-assisted |
| Expected Result | The customer can browse menu items but cannot build a cart. |
| Postconditions | Session remains in browse-only assisted state. |
| Traceability | UW-015; FR-015 |

**Test Steps:**
1. Start a session and choose `Staff-assisted`.
2. Open the menu screen.
3. Browse the visible items.
4. Verify the menu is visible and no cart total or checkout control is available.


---
**Test Case: UW-015-TC-002**

| Field | Detail |
| --- | --- |
| Title | Prevent add-to-cart actions in staff-assisted mode |
| Functional Area | Staff-Assisted Service Request |
| Test Type | Negative |
| Priority | High |
| Preconditions | Customer is on the browse-only menu in staff-assisted mode. |
| Test Data | Item: Classic Burger in staff-assisted mode |
| Expected Result | The app does not allow the item to be added to a cart while in assisted mode. |
| Postconditions | No cart is created. |
| Traceability | UW-015; FR-015 |

**Test Steps:**
1. Start a session and choose `Staff-assisted`.
2. Open the menu screen.
3. Try to add `Classic Burger` to the cart via UI or direct request.
4. Verify the add-to-cart action is unavailable or rejected.


---
**Test Case: UW-016-TC-001**

| Field | Detail |
| --- | --- |
| Title | Record a one-time readiness request |
| Functional Area | Staff-Assisted Service Request |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Customer is in a staff-assisted session on the browse-only menu. |
| Test Data | Ready action tapped once |
| Expected Result | The session records one readiness event and shows that staff have been called. |
| Postconditions | Session is marked as waiting for staff. |
| Traceability | UW-016; FR-016 |

**Test Steps:**
1. Start a session in staff-assisted mode.
2. Browse the menu.
3. Tap `Ready to Order` once.
4. Verify the app records the request and acknowledges that staff have been called.


---
**Test Case: UW-016-TC-002**

| Field | Detail |
| --- | --- |
| Title | Ignore a second readiness tap in the same session |
| Functional Area | Staff-Assisted Service Request |
| Test Type | State |
| Priority | Medium |
| Preconditions | A staff-assisted session has already recorded readiness once. |
| Test Data | Ready action tapped twice |
| Expected Result | Only one readiness event is stored and the second activation is ignored or blocked. |
| Postconditions | Still only one readiness event exists. |
| Traceability | UW-016; FR-016 |

**Test Steps:**
1. Start a session in staff-assisted mode.
2. Tap `Ready to Order` once successfully.
3. Tap `Ready to Order` again.
4. Verify the second activation does not create another readiness request.


---
**Test Case: UW-017-TC-001**

| Field | Detail |
| --- | --- |
| Title | Send a staff notification containing the table number |
| Functional Area | Staff-Assisted Service Request |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | A valid readiness event exists for table T12. |
| Test Data | Table: T12 |
| Expected Result | The staff-facing notification includes table T12 so staff know where to go. |
| Postconditions | Staff-facing channel contains one notification for table T12. |
| Traceability | UW-017; FR-017 |

**Test Steps:**
1. Create a valid staff-assisted session for table T12.
2. Tap `Ready to Order`.
3. Open the staff notification channel or queue.
4. Verify one notification is present and includes table `T12`.


---
**Test Case: UW-017-TC-002**

| Field | Detail |
| --- | --- |
| Title | Block notification if table context is missing |
| Functional Area | Staff-Assisted Service Request |
| Test Type | Negative |
| Priority | High |
| Preconditions | A staff-assisted session exists but its table reference has been removed or corrupted. |
| Test Data | Readiness event with missing table reference |
| Expected Result | The app does not send a malformed notification and surfaces a recoverable session error. |
| Postconditions | No notification is delivered. |
| Traceability | UW-017; FR-017 |

**Test Steps:**
1. Create a valid staff-assisted session.
2. Corrupt the stored table reference.
3. Tap `Ready to Order`.
4. Verify no notification is sent and the app shows a session error.


---
**Test Case: UW-018-TC-001**

| Field | Detail |
| --- | --- |
| Title | Finish the staff-assisted flow without payment or order number |
| Functional Area | Staff-Assisted Service Request |
| Test Type | State |
| Priority | Critical |
| Preconditions | Customer is in a valid staff-assisted session. |
| Test Data | Staff-assisted session for table T12 |
| Expected Result | After readiness is recorded, no order number is generated and no app-side payment is processed. |
| Postconditions | No app-side order record exists. |
| Traceability | UW-018; FR-018 |

**Test Steps:**
1. Start a session and choose `Staff-assisted`.
2. Browse the menu and tap `Ready to Order`.
3. Wait for the acknowledgement.
4. Verify there is no payment step, no order number, and no confirmed order record in the app.


---
**Test Case: UW-018-TC-002**

| Field | Detail |
| --- | --- |
| Title | Block direct navigation to checkout in staff-assisted mode |
| Functional Area | Staff-Assisted Service Request |
| Test Type | Negative |
| Priority | High |
| Preconditions | Customer has an active staff-assisted session. |
| Test Data | Attempted route: /checkout while session mode = staff-assisted |
| Expected Result | The app blocks checkout access and explains that the current session uses staff-assisted service. |
| Postconditions | Session remains in assisted mode with no checkout access. |
| Traceability | UW-018; FR-018 |

**Test Steps:**
1. Start a session and choose `Staff-assisted`.
2. Manually navigate to the self-service checkout route.
3. Observe the response.
4. Verify the app blocks checkout and shows a mode-based access message.


## Functional Area: Order Status Display

---
**Test Case: UW-019-TC-001**

| Field | Detail |
| --- | --- |
| Title | Open the public order board without authentication |
| Functional Area | Order Status Display |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | The public display endpoint is available in the venue. |
| Test Data | Public display URL |
| Expected Result | The display loads current order-status information without requiring login. |
| Postconditions | Customer can view the public board. |
| Traceability | UW-019; FR-019 |

**Test Steps:**
1. Open the public display URL in a browser that has no admin session.
2. Wait for the page to load.
3. Observe the content.
4. Verify the order board is shown without any login prompt.


---
**Test Case: UW-019-TC-002**

| Field | Detail |
| --- | --- |
| Title | Keep admin controls off the public order board |
| Functional Area | Order Status Display |
| Test Type | Negative |
| Priority | Medium |
| Preconditions | At least one active self-service order exists. |
| Test Data | Public display URL with active orders present |
| Expected Result | The public board shows order statuses only and does not expose ready/dismiss controls. |
| Postconditions | Public board remains read-only. |
| Traceability | UW-019; FR-019 |

**Test Steps:**
1. Create at least one active self-service order.
2. Open the public display URL.
3. Inspect the visible actions on the page.
4. Verify no admin-only status update or dismissal controls are exposed.


---
**Test Case: UW-020-TC-001**

| Field | Detail |
| --- | --- |
| Title | Show a new self-service order as In Preparation |
| Functional Area | Order Status Display |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | A self-service order has just been confirmed successfully. |
| Test Data | Confirmed order number: A127 |
| Expected Result | The public board shows order A127 in the In Preparation section after submission. |
| Postconditions | Order A127 is visible as In Preparation. |
| Traceability | UW-020; FR-020 |

**Test Steps:**
1. Submit a successful self-service order and note the assigned order number.
2. Open the public display.
3. Locate the order number.
4. Verify the order appears under `In Preparation`.


---
**Test Case: UW-020-TC-002**

| Field | Detail |
| --- | --- |
| Title | Exclude staff-assisted sessions from the public order board |
| Functional Area | Order Status Display |
| Test Type | Negative |
| Priority | High |
| Preconditions | A customer completes the staff-assisted readiness flow. |
| Test Data | Staff-assisted session for table T12 |
| Expected Result | No public-board entry is created for the assisted session because no self-service order exists. |
| Postconditions | Public board contains no entry derived from the assisted session. |
| Traceability | UW-020; FR-020 |

**Test Steps:**
1. Complete a staff-assisted session and trigger readiness.
2. Open the public display.
3. Search for any identifier linked to that assisted session.
4. Verify no new public-board entry appears.


---
**Test Case: UW-021-TC-001**

| Field | Detail |
| --- | --- |
| Title | Mark an in-preparation order as ready for pickup |
| Functional Area | Order Status Display |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Admin is logged in and order A127 is in In Preparation. |
| Test Data | Order number: A127 currently In Preparation |
| Expected Result | The selected order moves to Ready for Pickup and the public board updates immediately. |
| Postconditions | Order A127 is displayed as Ready for Pickup. |
| Traceability | UW-021; FR-021 |

**Test Steps:**
1. Log in to the admin interface.
2. Open the active order queue.
3. Mark order `A127` as ready.
4. Verify the public display moves `A127` to `Ready for Pickup` immediately.


---
**Test Case: UW-021-TC-002**

| Field | Detail |
| --- | --- |
| Title | Reject a ready-status change from an unauthenticated user |
| Functional Area | Order Status Display |
| Test Type | Negative |
| Priority | Critical |
| Preconditions | Order A127 is in In Preparation and no admin session is active. |
| Test Data | Order number: A127; user state: not authenticated |
| Expected Result | The system denies the status change and leaves A127 in its original state. |
| Postconditions | Order A127 status is unchanged. |
| Traceability | UW-021; FR-021 |

**Test Steps:**
1. Ensure order `A127` is in `In Preparation`.
2. Open the ready-action endpoint or page without logging in.
3. Attempt to mark the order ready.
4. Verify access is denied and the order remains unchanged.


---
**Test Case: UW-022-TC-001**

| Field | Detail |
| --- | --- |
| Title | Remove a collected order from the public display |
| Functional Area | Order Status Display |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Order A127 is displayed as Ready for Pickup and admin is logged in. |
| Test Data | Order number: A127 marked collected by admin |
| Expected Result | The public board removes order A127 after collection is confirmed. |
| Postconditions | Order A127 no longer appears on the public board. |
| Traceability | UW-022; FR-022 |

**Test Steps:**
1. Log in as admin and open the order queue.
2. Confirm collection for ready order `A127`.
3. Open the public display.
4. Verify `A127` has been removed from the board.


---
**Test Case: UW-022-TC-002**

| Field | Detail |
| --- | --- |
| Title | Keep a ready order visible just before timeout expiry |
| Functional Area | Order Status Display |
| Test Type | Boundary |
| Priority | Medium |
| Preconditions | Order A127 is ready for pickup and display-timeout configuration is 10 minutes. |
| Test Data | Configured timeout: 10 minutes; elapsed time: 9 minutes 59 seconds |
| Expected Result | The ready order still appears on the public board before the timeout threshold is reached. |
| Postconditions | Order A127 remains visible until timeout actually expires. |
| Traceability | UW-022; FR-022 |

**Test Steps:**
1. Configure the ready-order timeout to 10 minutes.
2. Mark order `A127` as ready for pickup.
3. Advance system time or wait until 9 minutes 59 seconds have elapsed.
4. Verify `A127` is still visible on the public board.


## Functional Area: Menu Management

---
**Test Case: UW-023-TC-001**

| Field | Detail |
| --- | --- |
| Title | Allow access with valid admin credentials |
| Functional Area | Menu Management |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | A valid admin account exists. |
| Test Data | Username: admin.tableorder; Password: Admin#2026 |
| Expected Result | The system authenticates the admin and opens the protected admin interface. |
| Postconditions | Authenticated admin session is active. |
| Traceability | UW-023; FR-023; NFR-006 |

**Test Steps:**
1. Open the admin login page.
2. Enter username `admin.tableorder`.
3. Enter password `Admin#2026`.
4. Submit the form and verify the protected admin interface opens.


---
**Test Case: UW-023-TC-002**

| Field | Detail |
| --- | --- |
| Title | Show a generic error for invalid admin credentials |
| Functional Area | Menu Management |
| Test Type | Negative |
| Priority | High |
| Preconditions | Admin login page is available. |
| Test Data | Username: admin.tableorder; Password: Wrong#2026 |
| Expected Result | Login is rejected and a generic authentication error is shown without identifying which field was wrong. |
| Postconditions | No admin session is created. |
| Traceability | UW-023; FR-023; NFR-006 |

**Test Steps:**
1. Open the admin login page.
2. Enter username `admin.tableorder`.
3. Enter password `Wrong#2026`.
4. Submit the form and verify access is denied with a generic authentication error.


---
**Test Case: UW-023-TC-003**

| Field | Detail |
| --- | --- |
| Title | Expire an idle admin session after the configured inactivity threshold |
| Functional Area | Menu Management |
| Test Type | State |
| Priority | High |
| Preconditions | Admin is logged in and inactivity timeout is configured to 15 minutes. |
| Test Data | Configured inactivity timeout: 15 minutes |
| Expected Result | After 15 minutes of inactivity, the admin session expires and protected actions require re-authentication. |
| Postconditions | Admin must log in again before using protected features. |
| Traceability | UW-023; FR-023; NFR-006 |

**Test Steps:**
1. Log in to the admin interface.
2. Leave the session idle for 15 minutes.
3. Try to open menu management or update an order.
4. Verify the session has expired and the app requests re-authentication.


---
**Test Case: UW-024-TC-001**

| Field | Detail |
| --- | --- |
| Title | Create a new menu item with all mandatory fields |
| Functional Area | Menu Management |
| Test Type | Happy Path |
| Priority | Critical |
| Preconditions | Admin is logged in to menu management. |
| Test Data | Name: Vegan Salad; Description: Mixed greens with avocado; Price: 9.00; Category: Salads; Allergens: nuts; Photo: vegan-salad.jpg |
| Expected Result | The system saves Vegan Salad successfully and makes it available to future customer sessions when enabled. |
| Postconditions | Menu item `Vegan Salad` exists in the catalogue. |
| Traceability | UW-024; FR-024 |

**Test Steps:**
1. Open menu management as an authenticated admin.
2. Start creating a new item.
3. Enter all mandatory fields for `Vegan Salad` and upload `vegan-salad.jpg`.
4. Submit the form and verify the item is saved successfully.


---
**Test Case: UW-024-TC-002**

| Field | Detail |
| --- | --- |
| Title | Reject a new menu item missing allergen information |
| Functional Area | Menu Management |
| Test Type | Negative |
| Priority | High |
| Preconditions | Admin is logged in to menu management. |
| Test Data | Name: Lemon Tart; Price: 5.50; Category: Desserts; Allergens: empty; Photo: lemon-tart.jpg |
| Expected Result | The system blocks the save and highlights the missing allergen information. |
| Postconditions | No new Lemon Tart item is created. |
| Traceability | UW-024; FR-024 |

**Test Steps:**
1. Open menu management as an authenticated admin.
2. Start creating `Lemon Tart`.
3. Leave the allergen field empty while filling other mandatory data.
4. Submit the form and verify the save is rejected with field validation.


---
**Test Case: UW-024-TC-003**

| Field | Detail |
| --- | --- |
| Title | Save special characters correctly when adding a menu item |
| Functional Area | Menu Management |
| Test Type | Edge |
| Priority | Medium |
| Preconditions | Admin is logged in to menu management. |
| Test Data | Name: Crème Brûlée; Description: Vanilla custard – chef’s special; Price: 6.20; Category: Desserts; Allergens: eggs, milk; Photo: creme-brulee.jpg |
| Expected Result | The item is saved and the accented characters and punctuation are preserved exactly. |
| Postconditions | Menu item `Crème Brûlée` exists with preserved text. |
| Traceability | UW-024; FR-024 |

**Test Steps:**
1. Open menu management as an authenticated admin.
2. Create a new item using the special-character values provided.
3. Submit the form.
4. Verify the saved item shows `Crème Brûlée` and `chef’s special` exactly as entered.


---
**Test Case: UW-025-TC-001**

| Field | Detail |
| --- | --- |
| Title | Update price and allergens for an existing menu item |
| Functional Area | Menu Management |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Admin is logged in and `Classic Burger` already exists. |
| Test Data | Item: Classic Burger; New price: 13.00; New allergens: gluten, milk, sesame |
| Expected Result | The item is updated and future customer sessions see the revised price and allergen list. |
| Postconditions | Classic Burger stores the new price and allergen values. |
| Traceability | UW-025; FR-025 |

**Test Steps:**
1. Open menu management as an authenticated admin.
2. Edit `Classic Burger`.
3. Change the price to `13.00` and allergens to `gluten, milk, sesame`.
4. Save and verify the updated values are shown for a new customer session.


---
**Test Case: UW-025-TC-002**

| Field | Detail |
| --- | --- |
| Title | Reject an invalid edited price |
| Functional Area | Menu Management |
| Test Type | Negative |
| Priority | High |
| Preconditions | Admin is logged in and `Classic Burger` already exists. |
| Test Data | Item: Classic Burger; Edited price: abc |
| Expected Result | The system blocks the update and highlights the invalid price field. |
| Postconditions | Classic Burger keeps its previous valid price. |
| Traceability | UW-025; FR-025 |

**Test Steps:**
1. Open menu management as an authenticated admin.
2. Edit `Classic Burger`.
3. Replace the price with `abc` and submit the form.
4. Verify the system rejects the update and retains the previous valid price.


---
**Test Case: UW-026-TC-001**

| Field | Detail |
| --- | --- |
| Title | Disable a menu item without affecting existing confirmed orders |
| Functional Area | Menu Management |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Admin is logged in, IPA Beer exists, and at least one historical confirmed order contains IPA Beer. |
| Test Data | Item: IPA Beer |
| Expected Result | IPA Beer becomes hidden from new customer sessions, while older confirmed orders containing it stay unchanged. |
| Postconditions | IPA Beer state is disabled and historical orders still reference it. |
| Traceability | UW-026; FR-026 |

**Test Steps:**
1. Log in to menu management.
2. Disable `IPA Beer`.
3. Open a new customer session and confirm the item is hidden.
4. Verify older confirmed orders that already contained IPA Beer still retain the item reference.


---
**Test Case: UW-026-TC-002**

| Field | Detail |
| --- | --- |
| Title | Re-enable a previously disabled item |
| Functional Area | Menu Management |
| Test Type | State |
| Priority | Medium |
| Preconditions | Admin is logged in and `IPA Beer` is currently disabled. |
| Test Data | Item: IPA Beer |
| Expected Result | The item becomes visible again in new customer sessions after being re-enabled. |
| Postconditions | IPA Beer state is enabled. |
| Traceability | UW-026; FR-026 |

**Test Steps:**
1. Log in to menu management.
2. Locate disabled item `IPA Beer`.
3. Switch the visibility toggle back to enabled.
4. Verify a new customer session can see `IPA Beer` again.


---
**Test Case: UW-026-TC-003**

| Field | Detail |
| --- | --- |
| Title | Reject adding a newly disabled item from a stale customer page |
| Functional Area | Menu Management |
| Test Type | Negative |
| Priority | High |
| Preconditions | Customer opened the menu while IPA Beer was enabled; admin disables it before the customer taps add. |
| Test Data | Item: IPA Beer disabled after customer opened the menu |
| Expected Result | The add attempt fails and the stale page cannot submit IPA Beer to the cart. |
| Postconditions | Customer cart does not contain IPA Beer. |
| Traceability | UW-026; FR-026 |

**Test Steps:**
1. Open a customer session while `IPA Beer` is enabled.
2. Disable `IPA Beer` from the admin interface.
3. Return to the stale customer page and tap add on `IPA Beer`.
4. Verify the app rejects the add request and leaves the cart unchanged.


---
**Test Case: UW-027-TC-001**

| Field | Detail |
| --- | --- |
| Title | Delete a menu item only after confirmation |
| Functional Area | Menu Management |
| Test Type | Happy Path |
| Priority | High |
| Preconditions | Admin is logged in and `Seasonal Soup` exists. |
| Test Data | Item: Seasonal Soup; Confirmation: confirm delete |
| Expected Result | The system deletes Seasonal Soup from the active catalogue only after explicit confirmation. |
| Postconditions | Seasonal Soup no longer exists in the active catalogue. |
| Traceability | UW-027; FR-027 |

**Test Steps:**
1. Log in to menu management.
2. Start deleting `Seasonal Soup`.
3. Confirm the delete action when prompted.
4. Verify the item is removed from the active catalogue.


---
**Test Case: UW-027-TC-002**

| Field | Detail |
| --- | --- |
| Title | Keep the menu item when delete confirmation is cancelled |
| Functional Area | Menu Management |
| Test Type | Negative |
| Priority | Medium |
| Preconditions | Admin is logged in and `Seasonal Soup` exists. |
| Test Data | Item: Seasonal Soup; Confirmation: cancel |
| Expected Result | The system keeps Seasonal Soup unchanged when the admin cancels the confirmation prompt. |
| Postconditions | Seasonal Soup remains in the active catalogue. |
| Traceability | UW-027; FR-027 |

**Test Steps:**
1. Log in to menu management.
2. Start deleting `Seasonal Soup`.
3. Cancel the confirmation prompt.
4. Verify the item still exists and is unchanged.


## Test Case Summary by Functional Area and Priority

| Functional Area | Total TCs | Critical | High | Medium | Low |
| --- | ---: | ---: | ---: | ---: | ---: |
| Customer Onboarding | 9 | 3 | 5 | 1 | 0 |
| Menu Browsing | 11 | 3 | 6 | 2 | 0 |
| Self-Service Order Submission | 12 | 6 | 6 | 0 | 0 |
| Staff-Assisted Service Request | 8 | 1 | 6 | 1 | 0 |
| Order Status Display | 8 | 3 | 3 | 2 | 0 |
| Menu Management | 13 | 2 | 8 | 3 | 0 |
| **TOTAL** | **61** | **18** | **34** | **9** | **0** |

## Test Case Summary by Type

| Test Type | Total |
| --- | ---: |
| Happy Path | 25 |
| Boundary | 4 |
| Negative | 21 |
| Edge | 1 |
| State | 10 |
