# cost_matrix

## estimation_parameters

| parameter | value |
|---|---|
| estimation_date | 2026-06-26 |
| methodology | WBS work-package sizing + factor-based scoring |
| confidence_level | Medium |
| assumptions | Greenfield modular monolith delivered by a small cross-functional team (2 full-stack engineers, 1 part-time QA/DevOps), with infrastructure and Stripe accounts available when implementation begins. |

## cost_summary

| metric | value |
|---|---|
| total_work_packages | 21 |
| total_man_days_min | 79 |
| total_man_days_max | 145 |
| total_man_days_typical | 116 |
| average_per_work_package | 5.5 |

## cost_by_phase

| phase_id | phase_name | work_package_count | man_days_min | man_days_max | man_days_typical | pct_of_total |
|---|---|---|---|---|---|---|
| F1 | Project Foundation & Platform Setup | 6 | 24 | 45 | 36 | 31.0% |
| F2 | Customer Ordering Experience | 4 | 12 | 20 | 16 | 13.8% |
| F3 | Payment & Order Lifecycle | 3 | 13 | 25 | 20 | 17.2% |
| F4 | Admin & Menu Management | 4 | 14 | 25 | 20 | 17.2% |
| F5 | Cross-Cutting Concerns & Production Readiness | 4 | 16 | 30 | 24 | 20.7% |

## cost_by_priority

| priority | work_package_count | man_days_min | man_days_max | man_days_typical | pct_of_total |
|---|---|---|---|---|---|
| High | 16 | 60 | 110 | 88 | 75.9% |
| Medium | 5 | 19 | 35 | 28 | 24.1% |
| Low | 0 | 0 | 0 | 0 | 0.0% |

## cost_by_tshirt

| tshirt_size | work_package_count | man_days_min | man_days_max | man_days_typical |
|---|---|---|---|---|
| XS | 0 | 0 | 0 | 0 |
| S | 0 | 0 | 0 | 0 |
| M | 13 | 39 | 65 | 52 |
| L | 8 | 40 | 80 | 64 |
| XL | 0 | 0 | 0 | 0 |

## work_package_estimates

| wbs_wp_id | deliverable_id | work_package_name | priority | scenarios_or_stories_count | components_count | func_cx | tech_cx | integ_cx | data_cx | risk | total_score | tshirt | man_days_min | man_days_max | man_days_typical |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1.D1.WP1 | [F1.D1](10_wbs.md#wbs_table) | Establish backend modular monolith skeleton | High | 0 | 8 | 2 | 3 | 2 | 1 | 4 | 12 | L | 5 | 10 | 8 |
| F1.D1.WP2 | [F1.D1](10_wbs.md#wbs_table) | Establish PostgreSQL schemas, migrations, and seed baseline | High | 0 | 5 | 2 | 3 | 2 | 3 | 2 | 12 | L | 5 | 10 | 8 |
| F1.D2.WP1 | [F1.D2](10_wbs.md#wbs_table) | Bootstrap multi-shell React workspace and design-system baseline | High | 0 | 3 | 2 | 2 | 2 | 1 | 4 | 11 | M | 3 | 5 | 4 |
| F1.D2.WP2 | [F1.D2](10_wbs.md#wbs_table) | Establish frontend API client, state, and realtime baseline | High | 0 | 4 | 2 | 2 | 2 | 1 | 4 | 11 | M | 3 | 5 | 4 |
| F1.D3.WP1 | [F1.D3](10_wbs.md#wbs_table) | Provision development environment, CI, and deployment packaging | High | 0 | 5 | 2 | 2 | 2 | 1 | 3 | 10 | M | 3 | 5 | 4 |
| F1.D3.WP2 | [F1.D3](10_wbs.md#wbs_table) | Implement observability, configuration, and resilience baseline | High | 0 | 4 | 2 | 3 | 2 | 1 | 4 | 12 | L | 5 | 10 | 8 |
| F2.D1.WP1 | [F2.D1](10_wbs.md#wbs_table) | Implement QR session onboarding and service-mode routing | High | 3 | 2 | 3 | 2 | 2 | 1 | 2 | 10 | M | 3 | 5 | 4 |
| F2.D2.WP1 | [F2.D2](10_wbs.md#wbs_table) | Implement menu browsing with category allergen and media presentation | High | 1 | 2 | 2 | 2 | 2 | 2 | 2 | 10 | M | 3 | 5 | 4 |
| F2.D2.WP2 | [F2.D2](10_wbs.md#wbs_table) | Implement self-service cart mutations and live order summary | High | 2 | 2 | 3 | 2 | 2 | 2 | 2 | 11 | M | 3 | 5 | 4 |
| F2.D3.WP1 | [F2.D3](10_wbs.md#wbs_table) | Implement browse-only assisted ordering and readiness notification flow | Medium | 1 | 5 | 2 | 2 | 3 | 1 | 3 | 11 | M | 3 | 5 | 4 |
| F3.D1.WP1 | [F3.D1](10_wbs.md#wbs_table) | Implement checkout review validation and cash order confirmation | High | 2 | 2 | 3 | 2 | 2 | 2 | 2 | 11 | M | 3 | 5 | 4 |
| F3.D1.WP2 | [F3.D1](10_wbs.md#wbs_table) | Integrate Stripe card authorization and payment failure recovery | High | 2 | 2 | 3 | 3 | 3 | 1 | 3 | 13 | L | 5 | 10 | 8 |
| F3.D2.WP1 | [F3.D2](10_wbs.md#wbs_table) | Implement public display projection for active self-service orders | Medium | 1 | 3 | 2 | 3 | 2 | 2 | 3 | 12 | L | 5 | 10 | 8 |
| F4.D1.WP1 | [F4.D1](10_wbs.md#wbs_table) | Implement admin authentication and protected session handling | High | 1 | 2 | 2 | 2 | 2 | 1 | 4 | 11 | M | 3 | 5 | 4 |
| F4.D2.WP1 | [F4.D2](10_wbs.md#wbs_table) | Implement menu item creation and editing with validation | Medium | 1 | 2 | 3 | 2 | 2 | 3 | 2 | 12 | L | 5 | 10 | 8 |
| F4.D2.WP2 | [F4.D2](10_wbs.md#wbs_table) | Implement menu visibility toggles and deletion safeguards | Medium | 1 | 2 | 2 | 2 | 2 | 2 | 2 | 10 | M | 3 | 5 | 4 |
| F4.D2.WP3 | [F4.D2](10_wbs.md#wbs_table) | Implement admin order-readiness and display-removal controls | Medium | 2 | 3 | 2 | 2 | 2 | 2 | 3 | 11 | M | 3 | 5 | 4 |
| F5.D1.WP1 | [F5.D1](10_wbs.md#wbs_table) | Implement GDPR retention purge and secure session policies | High | 0 | 4 | 2 | 2 | 2 | 2 | 4 | 12 | L | 5 | 10 | 8 |
| F5.D1.WP2 | [F5.D1](10_wbs.md#wbs_table) | Implement platform-wide validation authorization audit and abuse controls | High | 0 | 7 | 2 | 2 | 2 | 2 | 3 | 11 | M | 3 | 5 | 4 |
| F5.D2.WP1 | [F5.D2](10_wbs.md#wbs_table) | Optimize performance and concurrency for customer and display flows | High | 0 | 6 | 2 | 3 | 2 | 1 | 4 | 12 | L | 5 | 10 | 8 |
| F5.D2.WP2 | [F5.D2](10_wbs.md#wbs_table) | Execute automated quality suite and go-live operational validation | High | 0 | 11 | 2 | 2 | 2 | 1 | 4 | 11 | M | 3 | 5 | 4 |

## estimation_notes

### [F1.D1.WP1](10_wbs.md#wbs_table): Establish backend modular monolith skeleton
- **Primary drivers**: Module boundaries span all backend services and must enforce the modular-monolith style from ADR-001.
- **Risks**: Risk is concentrated in early architecture choices that can either preserve or erode future maintainability.
- **Assumptions**: Assumes one shared Spring Boot deployable with package-level and test-enforced ownership rules.

### [F1.D1.WP2](10_wbs.md#wbs_table): Establish PostgreSQL schemas, migrations, and seed baseline
- **Primary drivers**: Data ownership spans sessions, menu items, orders, statuses, and admin identities.
- **Risks**: Schema mistakes would undermine order durability and GDPR retention from day one.
- **Assumptions**: Assumes PostgreSQL plus a migration tool and deterministic seed data for local and test environments.

### [F1.D2.WP1](10_wbs.md#wbs_table): Bootstrap multi-shell React workspace and design-system baseline
- **Primary drivers**: One frontend codebase must support three distinct experiences without accidental coupling.
- **Risks**: Shared primitives reduce delivery cost but routing and shell separation must be deliberate.
- **Assumptions**: Assumes React + TypeScript with a mobile-first design system and shared build pipeline.

### [F1.D2.WP2](10_wbs.md#wbs_table): Establish frontend API client, state, and realtime baseline
- **Primary drivers**: The baseline must support anonymous customer flows, protected admin routes, and realtime display updates.
- **Risks**: Transport and state mistakes would ripple into multiple downstream work packages.
- **Assumptions**: Assumes shared API client abstractions and a thin realtime adapter around SSE/WebSocket or polling fallback.

### [F1.D3.WP1](10_wbs.md#wbs_table): Provision development environment, CI, and deployment packaging
- **Primary drivers**: The project is greenfield, so every developer and pipeline path must be bootstrapped.
- **Risks**: The main risk is fragmented environments or manual release steps that slow later delivery.
- **Assumptions**: Assumes container-friendly packaging and one CI pipeline covering backend and frontend builds/tests.

### [F1.D3.WP2](10_wbs.md#wbs_table): Implement observability, configuration, and resilience baseline
- **Primary drivers**: Observability and resilience span multiple modules and are critical to [NFR-003](../04c_non_functional_requirements.md#nfr-003), [NFR-011](../04c_non_functional_requirements.md#nfr-011), and ADR-007.
- **Risks**: The work is cross-cutting and touches error semantics, logging, retries, and configuration hygiene.
- **Assumptions**: Assumes structured logging, health endpoints, metrics, and safe retry patterns rather than a heavy platform stack.

### [F2.D1.WP1](10_wbs.md#wbs_table): Implement QR session onboarding and service-mode routing
- **Primary drivers**: This work package owns both happy-path modes and the invalid-QR exception flow.
- **Risks**: Usability is important because first-time customers must complete onboarding without assistance.
- **Assumptions**: Assumes QR labels already exist physically and only server-side validation plus routing must be built.

### [F2.D2.WP1](10_wbs.md#wbs_table): Implement menu browsing with category allergen and media presentation
- **Primary drivers**: The scope combines read-model presentation with mandatory allergen and media completeness rules.
- **Risks**: Performance matters because menu load time is a visible first impression after onboarding.
- **Assumptions**: Assumes the admin-populated menu becomes the sole customer-visible source of truth.

### [F2.D2.WP2](10_wbs.md#wbs_table): Implement self-service cart mutations and live order summary
- **Primary drivers**: Cart behavior covers additive updates, quantity changes, zero-quantity removal, and total recalculation.
- **Risks**: Errors here directly affect checkout trust and perceived responsiveness.
- **Assumptions**: Assumes pricing snapshots are taken from the menu service while the session remains active.

### [F2.D3.WP1](10_wbs.md#wbs_table): Implement browse-only assisted ordering and readiness notification flow
- **Primary drivers**: This path must stay intentionally lightweight: browse only, one readiness signal, no order or payment record.
- **Risks**: Realtime notification adds integration complexity even though functional scope is limited.
- **Assumptions**: Assumes staff receive the notification through the browser/device channel delivered by the realtime gateway.

### [F3.D1.WP1](10_wbs.md#wbs_table): Implement checkout review validation and cash order confirmation
- **Primary drivers**: This package covers review, validation, mandatory payment selection, and the cash branch of order confirmation.
- **Risks**: Order durability and confirmation speed both make this more than a simple form flow.
- **Assumptions**: Assumes cash payment bypasses the external gateway but still creates a durable order and customer-visible number.

### [F3.D1.WP2](10_wbs.md#wbs_table): Integrate Stripe card authorization and payment failure recovery
- **Primary drivers**: Stripe integration is the highest-risk business flow because it touches external authorization and failure semantics.
- **Risks**: The gateway path must remain idempotent and never create an order after a failed authorization.
- **Assumptions**: Assumes Stripe is the only payment provider and the application never handles raw card data.

### [F3.D2.WP1](10_wbs.md#wbs_table): Implement public display projection for active self-service orders
- **Primary drivers**: The display is read-only for customers but depends on timely projection from confirmed-order data.
- **Risks**: The realtime/polling boundary and display readability add complexity beyond a static listing.
- **Assumptions**: Assumes one in-venue public screen with passive viewing and no authentication.

### [F4.D1.WP1](10_wbs.md#wbs_table): Implement admin authentication and protected session handling
- **Primary drivers**: Although narrow in scope, admin auth is security-sensitive and must enforce session expiry correctly.
- **Risks**: The venue context makes unattended admin sessions a realistic risk.
- **Assumptions**: Assumes Spring Security plus secure cookies and no external identity provider.

### [F4.D2.WP1](10_wbs.md#wbs_table): Implement menu item creation and editing with validation
- **Primary drivers**: Menu maintenance carries moderate data complexity because publishability depends on multiple mandatory fields.
- **Risks**: The admin experience must stay fast while enforcing completeness to protect downstream customer browsing.
- **Assumptions**: Assumes media references are stored and validated as part of the menu item lifecycle.

### [F4.D2.WP2](10_wbs.md#wbs_table): Implement menu visibility toggles and deletion safeguards
- **Primary drivers**: The logic is smaller than full CRUD but still needs consistency around existing orders and customer visibility.
- **Risks**: Accidental deletion is the main business risk, so confirmation and soft visibility semantics must be explicit.
- **Assumptions**: Assumes disable/enable changes affect only new customer sessions while historical order snapshots remain intact.

### [F4.D2.WP3](10_wbs.md#wbs_table): Implement admin order-readiness and display-removal controls
- **Primary drivers**: This work package closes the loop between backoffice actions and the public display lifecycle.
- **Risks**: Timeout handling and near-real-time updates must behave predictably during service hours.
- **Assumptions**: Assumes admins act from the backoffice queue and the display can refresh through realtime or fallback polling.

### [F5.D1.WP1](10_wbs.md#wbs_table): Implement GDPR retention purge and secure session policies
- **Primary drivers**: This package addresses the strongest compliance obligations: GDPR minimisation and secure admin/customer session handling.
- **Risks**: Risk is high because retention or cookie mistakes create compliance and security exposure.
- **Assumptions**: Assumes retention can be driven by order lifecycle completion and configuration-backed security defaults.

### [F5.D1.WP2](10_wbs.md#wbs_table): Implement platform-wide validation authorization audit and abuse controls
- **Primary drivers**: Abuse resistance and auditability cut across public QR entry, assisted notifications, admin actions, and order-state updates.
- **Risks**: The breadth of touchpoints raises coordination risk more than raw implementation difficulty.
- **Assumptions**: Assumes basic rate limits, validation policies, and audit-event logging are sufficient for v1 threat posture.

### [F5.D2.WP1](10_wbs.md#wbs_table): Optimize performance and concurrency for customer and display flows
- **Primary drivers**: This package addresses the most visible latency and concurrency NFRs across menu, checkout, and display updates.
- **Risks**: Risk comes from cross-module hotspots such as catalog reads, order confirmation, and realtime propagation.
- **Assumptions**: Assumes one-venue load of roughly 40–50 users and optimization via caching, query tuning, and fallback transport behavior.

### [F5.D2.WP2](10_wbs.md#wbs_table): Execute automated quality suite and go-live operational validation
- **Primary drivers**: The final release package is broad because it spans regression confidence, dashboards, alerts, deployment, and rollback preparedness.
- **Risks**: The main risk is missing integration regressions or operational blind spots before live service hours.
- **Assumptions**: Assumes a production readiness checklist plus automated suites across backend, frontend, and key end-to-end journeys.

COST_COMPLETED: 21 work packages estimated — Total: 79–145 man-days (typical: 116)
