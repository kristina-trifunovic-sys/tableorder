# 1. Project Overview

## Organizational Context
A single restaurant/café establishment operating in the food & beverage sector, serving customers across a combination of dine-in and counter-service formats. The venue operates with front-of-house staff responsible for taking and managing customer orders, a model that has become increasingly strained during periods of high footfall.

## Current Challenges
The venue currently relies entirely on staff to receive and process every customer order — a manual and people-intensive approach that generates long wait times and places disproportionate pressure on the team during peak hours. These bottlenecks reduce the quality of the customer experience and limit the number of orders the venue can handle efficiently within a given timeframe.

## Strategic Objective
The initiative is driven by the need to modernize the ordering experience by reducing the venue's dependency on manual counter service and empowering customers to place orders independently when they choose to. The goal is to introduce a self-service ordering channel that coexists with traditional staff-assisted service, giving customers the flexibility to choose how they interact with the venue.

## Expected Business Outcomes
By introducing a digital ordering channel alongside the existing staff-assisted model, the venue expects to reduce the number of staff required at the counter, increase the throughput of orders during peak periods, and improve customer satisfaction and long-term retention through a faster, more convenient ordering experience.

---

# 2. Business Requirements

| ID     | Name                           | Description                                                                                                                                                                      |
| ------ | ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BR-001 | Reduced Order Wait Time        | The venue must reduce the average time it takes a customer to place an order, alleviating pressure during peak hours and delivering a noticeably faster experience at every table or counter. |
| BR-002 | Increased Daily Revenue        | The initiative must enable the venue to increase daily revenue by improving the throughput of orders processed per service period, particularly during high-demand hours.         |
| BR-003 | Reduced Counter Staff Dependency | The venue must reduce reliance on front-of-house staff for order-taking by enabling customers to place and complete orders independently when they choose to do so.              |
| BR-004 | Improved Customer Retention    | The initiative must improve customer satisfaction to a level that encourages repeat visits, contributing to long-term revenue stability and stronger customer loyalty.            |

---

# 3. Functional Requirements

## 3.1 Customer Onboarding
> *Traces to: BR-001, BR-003, BR-004*

- The system must activate the ordering flow when a customer scans a table-specific QR code, without requiring account creation or login.
- The system must prompt the customer to enter their name before any further interaction is allowed.
- The system must present two mutually exclusive service mode options side by side: self-service ordering (via the app) and staff-assisted service (a staff member comes to the table).
- The system must associate the customer session with the specific table identified by the scanned QR code throughout the entire ordering interaction.

## 3.2 Menu Browsing
> *Traces to: BR-001, BR-002, BR-004*

- The system must display the full menu of available food and drink items, organized into categories (e.g., food, drinks).
- The system must display the name, description, price, allergen information, and at least one photo for each menu item.
- The system must allow the customer to add one or more items to their active order.
- The system must allow the customer to adjust the quantity of each selected item before submitting the order.
- The system must display a running summary of selected items and the total amount due, updated in real time as items are added or removed.

## 3.3 Self-Service Order Submission
> *Traces to: BR-001, BR-002, BR-003*

- The system must allow the customer to review their full order summary and total price before confirming submission.
- The system must require the customer to select a payment method — card or cash — before the order is submitted.
- The system must submit the confirmed order and assign a unique order number to the customer.
- The system must display the assigned order number to the customer immediately after successful order submission.
- If a customer has not selected any items, the system must prevent order submission and prompt the customer to add at least one item.

## 3.4 Staff-Assisted Service Request
> *Traces to: BR-003, BR-004*

- When the customer selects the staff-assisted service mode, the system must display the menu to allow the customer to browse items in advance.
- The system must provide a clear action for the customer to signal they are ready to be approached by a staff member.
- Upon the customer confirming readiness, the system must send a notification to staff indicating that the customer at the identified table is ready to place an order.
- The system must not process a payment or generate an order number in the staff-assisted flow; order capture and payment are handled by the staff member directly.

## 3.5 Order Status Display
> *Traces to: BR-001, BR-004*

- The system must provide a public-facing display screen showing the status of self-service orders, visible to customers in the venue.
- The system must show which order numbers are currently being prepared and which are ready for pickup.
- The system must allow the admin to mark a self-service order as ready for pickup, which immediately updates the public display.
- The system must remove an order number from the display once the customer has collected their order or a configurable timeout has elapsed.

## 3.6 Menu Management
> *Traces to: BR-002, BR-003*

- The system must provide a protected admin interface accessible only to authorized administrators.
- The system must allow the admin to add new menu items, specifying name, description, price, category, allergen information, and at least one photo.
- The system must allow the admin to edit the details of any existing menu item, including name, description, price, category, allergen information, and photo.
- The system must allow the admin to enable or disable individual menu items so that unavailable items are hidden from customers without being permanently deleted.
- The system must allow the admin to remove menu items permanently from the system.

---

# 4. Technical Constraints

## 4.1 Development & Delivery

- **Backend Language:** The server-side application must be implemented in Java. This is a mandatory technology decision established by the project owner.
- **Frontend Technology:** The choice of frontend framework is open and will be determined during the design phase based on suitability for cross-device reach (desktop and mobile).

## 4.2 Security & Access

- **Admin Authentication:** The admin interface must enforce authentication via username and password. No external identity provider is required at this stage.
- **Customer Sessions:** Customers do not require accounts or credentials; sessions are initiated via QR code scan and are scoped to a single ordering interaction.

## 4.3 Data & Compliance

- **GDPR Applicability:** The venue is located within the European Union/EEA; the solution must comply with the General Data Protection Regulation (GDPR). Any personal data collected (e.g., customer name) must be handled in accordance with GDPR principles including data minimisation, purpose limitation, and appropriate retention policies.
- **Data Minimisation:** The system must collect only the data strictly necessary to fulfil the ordering interaction. No customer accounts, profiles, or persistent personal data stores are required beyond the active order lifecycle.

## 4.4 Integration & Interoperability

- **Payment Gateway:** The system must integrate with a third-party payment gateway to support card payments. The specific provider is an open decision to be made during the design phase; no existing vendor contract or exclusion applies.
- **No Other External System Integrations:** No integration with existing internal systems (e.g., POS, ERP, accounting) is required at this stage.

## 4.5 Infrastructure & Hosting

- **Hosting Model:** No specific infrastructure or cloud provider is mandated. The hosting model (cloud, on-premise, or hybrid) is an open architectural decision to be determined during the design phase.

## 4.6 Vendor & Licensing

- **No Licensing Constraints:** No existing vendor contracts, software licences, or technology exclusions apply to this project at this stage.

---

# 5. Non-Functional Requirements

## 5.1 Performance
> *Traces to: BR-001, BR-002*

| ID      | Requirement                        | Target / Condition                                                                 | Applies When                                                                 |
| ------- | ---------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| NFR-001 | Order & Payment Confirmation Speed | The order confirmation screen must appear within 3 seconds of the customer submitting their order | During self-service order submission, for both card and cash payment methods |
| NFR-002 | Menu Load Time                     | The menu must be fully loaded and browsable within 3 seconds                       | When a customer first accesses the app after scanning the QR code            |

## 5.2 Availability & Reliability
> *Traces to: BR-001, BR-002, BR-003*

| ID      | Requirement            | Target / Condition                                                                                          | Applies When                                              |
| ------- | ---------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| NFR-003 | Service Availability   | The system must be operational throughout all venue service hours; brief unplanned outages of a few minutes are acceptable | During all venue operating hours                          |
| NFR-004 | Order Durability       | A confirmed order must not be lost or corrupted due to a system error after the confirmation screen has been shown to the customer | At any point after order confirmation is displayed        |

## 5.3 Security
> *Traces to: BR-002, BR-004*

| ID      | Requirement                  | Target / Condition                                                                                                   | Applies When                                      |
| ------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| NFR-005 | Card Data Isolation          | The system must never store, log, or transmit raw card data; all card payment data must be processed exclusively by the integrated payment gateway | During any card payment transaction               |
| NFR-006 | Admin Session Security       | Admin sessions must require authentication and must expire after a period of inactivity [TO BE REFINED]              | At all times when the admin interface is active   |
| NFR-007 | Customer Data Retention      | Customer personal data (e.g., name) must not be persisted beyond the completion of the active order, in compliance with GDPR data minimisation principles | For all customer ordering sessions                |

## 5.4 Scalability
> *Traces to: BR-001, BR-002*

| ID      | Requirement                  | Target / Condition                                                                              | Applies When                              |
| ------- | ---------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------- |
| NFR-008 | Concurrent Session Capacity  | The system must support up to 50 simultaneous active customer sessions without performance degradation | During peak service hours at the venue    |

## 5.5 Usability
> *Traces to: BR-001, BR-004*

| ID      | Requirement               | Target / Condition                                                                                                  | Applies When                                        |
| ------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| NFR-009 | Ordering Flow Completion  | A first-time customer must be able to complete the full ordering flow — from QR scan to order submission — without requiring external assistance | For all customers, including those with limited digital literacy |
| NFR-010 | Device Compatibility      | The customer-facing app must function correctly on both mobile devices and desktop browsers                         | For all customers accessing the app via QR code     |

## 5.6 Maintainability & Operability
> *Traces to: BR-001, BR-002*

| ID      | Requirement              | Target / Condition                                                                                                            | Applies When                                      |
| ------- | ------------------------ | ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| NFR-011 | Incident Diagnosability  | The system must produce sufficient logs and error information to allow the on-standby technical team to diagnose and resolve production incidents | During any production incident or service degradation |
| NFR-012 | Update Deployment        | The system must support deployment of updates and patches without requiring extended service interruptions                    | During scheduled maintenance and patch rollouts   |

---

# 6. Customer Experience Requirements

## 6.1 User Types & Access Journey

- Users are customers of mixed ages — including elderly and young people — seated at a table in the venue, accessing the app from their own personal mobile device by scanning a table-specific QR code.
- Users must be able to choose between placing their order independently via the app or requesting a staff member to come to their table, without requiring any guidance from staff to make that choice.
- The full ordering flow must be completable by a first-time user with no prior experience with the app and without any assistance.

## 6.2 Device & Channel

- The customer-facing experience must be delivered as a browser-based web application; customers must not be required to download or install anything on their device.
- The interface must be fully functional, legible, and easy to interact with on standard mobile phone screen sizes.

## 6.3 Core Ordering Experience

- Users must be able to browse the full menu, add food and drink items, adjust quantities, and review their selection before submitting.
- Users must be presented with a clear and unambiguous payment method selection — card or cash — as a required step before completing their order.
- Users must be able to complete the entire ordering flow — from QR scan to order submission — within a small number of steps, without unnecessary screens or detours.

## 6.4 Information Visibility

- Each menu item must display its name, description, price, and at least one photo.
- Allergen information must be especially prominently displayed for each menu item, ensuring customers can identify allergens before selecting any item.
- A running total of selected items and the cumulative price must be persistently visible at the bottom of the menu page as the customer builds their order.

## 6.5 Order Confirmation & Status

- Upon successful order submission, the customer must be shown a unique order number clearly and prominently displayed on screen.
- The confirmation screen must communicate to the customer that their order number will appear on the venue's public display screen when the order is ready for pickup, and that no mobile notification will be sent.
- If a payment fails, the interface must clearly explain what went wrong and what the customer should do next, without leaving them on a blank or ambiguous screen.
