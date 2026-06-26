# coverage_matrix

## coverage_summary

| dimension | total_items | covered | uncovered | coverage_pct |
|---|---|---|---|---|
| scenarios_or_stories | 16 | 16 | 0 | 100% |
| features | 7 | 7 | 0 | 100% |
| requirements_or_epics | 27 | 27 | 0 | 100% |
| components | 11 | 11 | 0 | 100% |

## traceability_matrix_wbs_items

| wbs_item_id | level | name | covered_scenarios_or_stories | covered_features | covered_requirements_or_epics | covered_components | status |
|---|---|---|---|---|---|---|---|
| F1.D1 | deliverable | Backend Runtime Foundation | — | [FEAT-001](../03_features.md#feat-001), [FEAT-007](../03_features.md#feat-007) | [FR-004](../02_functional_requirements.md#fr-004) | [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-007](../07_components.md#comp-007), [comp-008](../07_components.md#comp-008), [comp-009](../07_components.md#comp-009), [comp-010](../07_components.md#comp-010), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F1.D1.WP1 | work_package | Establish backend modular monolith skeleton | — | — | — | [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-007](../07_components.md#comp-007), [comp-008](../07_components.md#comp-008), [comp-009](../07_components.md#comp-009), [comp-010](../07_components.md#comp-010), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F1.D1.WP2 | work_package | Establish PostgreSQL schemas, migrations, and seed baseline | — | [FEAT-001](../03_features.md#feat-001), [FEAT-007](../03_features.md#feat-007) | [FR-004](../02_functional_requirements.md#fr-004) | [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-008](../07_components.md#comp-008), [comp-009](../07_components.md#comp-009) | ✅ TRACEABLE |
| F1.D2 | deliverable | Frontend Workspace Foundation | — | [FEAT-005](../03_features.md#feat-005), [FEAT-006](../03_features.md#feat-006) | — | [comp-001](../07_components.md#comp-001), [comp-002](../07_components.md#comp-002), [comp-003](../07_components.md#comp-003), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F1.D2.WP1 | work_package | Bootstrap multi-shell React workspace and design-system baseline | — | — | — | [comp-001](../07_components.md#comp-001), [comp-002](../07_components.md#comp-002), [comp-003](../07_components.md#comp-003) | ⚠️ ENABLING |
| F1.D2.WP2 | work_package | Establish frontend API client, state, and realtime baseline | — | [FEAT-005](../03_features.md#feat-005), [FEAT-006](../03_features.md#feat-006) | — | [comp-001](../07_components.md#comp-001), [comp-002](../07_components.md#comp-002), [comp-003](../07_components.md#comp-003), [comp-011](../07_components.md#comp-011) | ✅ TRACEABLE |
| F1.D3 | deliverable | Delivery, Deployment, and Operability Baseline | — | — | — | [comp-001](../07_components.md#comp-001), [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-008](../07_components.md#comp-008), [comp-010](../07_components.md#comp-010), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F1.D3.WP1 | work_package | Provision development environment, CI, and deployment packaging | — | — | — | [comp-001](../07_components.md#comp-001), [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-008](../07_components.md#comp-008) | ⚠️ ENABLING |
| F1.D3.WP2 | work_package | Implement observability, configuration, and resilience baseline | — | — | — | [comp-006](../07_components.md#comp-006), [comp-008](../07_components.md#comp-008), [comp-010](../07_components.md#comp-010), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F2.D1 | deliverable | QR Session Onboarding | [SCN-001](../04b_scenarios.md#scn-001), [SCN-002](../04b_scenarios.md#scn-002), [SCN-003](../04b_scenarios.md#scn-003) | [FEAT-001](../03_features.md#feat-001) | [FR-001](../02_functional_requirements.md#fr-001), [FR-002](../02_functional_requirements.md#fr-002), [FR-003](../02_functional_requirements.md#fr-003), [FR-004](../02_functional_requirements.md#fr-004) | [comp-001](../07_components.md#comp-001), [comp-004](../07_components.md#comp-004) | ⚠️ ENABLING |
| F2.D1.WP1 | work_package | Implement QR session onboarding and service-mode routing | [SCN-001](../04b_scenarios.md#scn-001), [SCN-002](../04b_scenarios.md#scn-002), [SCN-003](../04b_scenarios.md#scn-003) | [FEAT-001](../03_features.md#feat-001) | [FR-001](../02_functional_requirements.md#fr-001), [FR-002](../02_functional_requirements.md#fr-002), [FR-003](../02_functional_requirements.md#fr-003), [FR-004](../02_functional_requirements.md#fr-004) | [comp-001](../07_components.md#comp-001), [comp-004](../07_components.md#comp-004) | ✅ TRACEABLE |
| F2.D2 | deliverable | Menu Browsing and Cart Composition | [SCN-004](../04b_scenarios.md#scn-004), [SCN-005](../04b_scenarios.md#scn-005) | [FEAT-002](../03_features.md#feat-002), [FEAT-003](../03_features.md#feat-003) | [FR-005](../02_functional_requirements.md#fr-005), [FR-006](../02_functional_requirements.md#fr-006), [FR-007](../02_functional_requirements.md#fr-007), [FR-008](../02_functional_requirements.md#fr-008), [FR-009](../02_functional_requirements.md#fr-009) | [comp-001](../07_components.md#comp-001), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006) | ⚠️ ENABLING |
| F2.D2.WP1 | work_package | Implement menu browsing with category allergen and media presentation | [SCN-004](../04b_scenarios.md#scn-004) | [FEAT-002](../03_features.md#feat-002) | [FR-005](../02_functional_requirements.md#fr-005), [FR-006](../02_functional_requirements.md#fr-006) | [comp-001](../07_components.md#comp-001), [comp-005](../07_components.md#comp-005) | ✅ TRACEABLE |
| F2.D2.WP2 | work_package | Implement self-service cart mutations and live order summary | [SCN-004](../04b_scenarios.md#scn-004), [SCN-005](../04b_scenarios.md#scn-005) | [FEAT-003](../03_features.md#feat-003) | [FR-007](../02_functional_requirements.md#fr-007), [FR-008](../02_functional_requirements.md#fr-008), [FR-009](../02_functional_requirements.md#fr-009) | [comp-001](../07_components.md#comp-001), [comp-006](../07_components.md#comp-006) | ✅ TRACEABLE |
| F2.D3 | deliverable | Staff-Assisted Service Request | [SCN-010](../04b_scenarios.md#scn-010) | [FEAT-005](../03_features.md#feat-005) | [FR-015](../02_functional_requirements.md#fr-015), [FR-016](../02_functional_requirements.md#fr-016), [FR-017](../02_functional_requirements.md#fr-017), [FR-018](../02_functional_requirements.md#fr-018) | [comp-001](../07_components.md#comp-001), [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-007](../07_components.md#comp-007), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F2.D3.WP1 | work_package | Implement browse-only assisted ordering and readiness notification flow | [SCN-010](../04b_scenarios.md#scn-010) | [FEAT-005](../03_features.md#feat-005) | [FR-015](../02_functional_requirements.md#fr-015), [FR-016](../02_functional_requirements.md#fr-016), [FR-017](../02_functional_requirements.md#fr-017), [FR-018](../02_functional_requirements.md#fr-018) | [comp-001](../07_components.md#comp-001), [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-007](../07_components.md#comp-007), [comp-011](../07_components.md#comp-011) | ✅ TRACEABLE |
| F3.D1 | deliverable | Self-Service Checkout and Payment | [SCN-007](../04b_scenarios.md#scn-007), [SCN-008](../04b_scenarios.md#scn-008), [SCN-006](../04b_scenarios.md#scn-006), [SCN-009](../04b_scenarios.md#scn-009) | [FEAT-004](../03_features.md#feat-004) | [FR-010](../02_functional_requirements.md#fr-010), [FR-011](../02_functional_requirements.md#fr-011), [FR-012](../02_functional_requirements.md#fr-012), [FR-013](../02_functional_requirements.md#fr-013), [FR-014](../02_functional_requirements.md#fr-014) | [comp-001](../07_components.md#comp-001), [comp-006](../07_components.md#comp-006), [comp-010](../07_components.md#comp-010) | ⚠️ ENABLING |
| F3.D1.WP1 | work_package | Implement checkout review validation and cash order confirmation | [SCN-007](../04b_scenarios.md#scn-007), [SCN-008](../04b_scenarios.md#scn-008) | [FEAT-004](../03_features.md#feat-004) | [FR-010](../02_functional_requirements.md#fr-010), [FR-011](../02_functional_requirements.md#fr-011), [FR-012](../02_functional_requirements.md#fr-012), [FR-013](../02_functional_requirements.md#fr-013), [FR-014](../02_functional_requirements.md#fr-014) | [comp-001](../07_components.md#comp-001), [comp-006](../07_components.md#comp-006) | ✅ TRACEABLE |
| F3.D1.WP2 | work_package | Integrate Stripe card authorization and payment failure recovery | [SCN-006](../04b_scenarios.md#scn-006), [SCN-009](../04b_scenarios.md#scn-009) | [FEAT-004](../03_features.md#feat-004) | [FR-011](../02_functional_requirements.md#fr-011), [FR-012](../02_functional_requirements.md#fr-012), [FR-013](../02_functional_requirements.md#fr-013) | [comp-006](../07_components.md#comp-006), [comp-010](../07_components.md#comp-010) | ✅ TRACEABLE |
| F3.D2 | deliverable | Public Order Status Display | [SCN-011](../04b_scenarios.md#scn-011) | [FEAT-006](../03_features.md#feat-006) | [FR-019](../02_functional_requirements.md#fr-019), [FR-020](../02_functional_requirements.md#fr-020) | [comp-003](../07_components.md#comp-003), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F3.D2.WP1 | work_package | Implement public display projection for active self-service orders | [SCN-011](../04b_scenarios.md#scn-011) | [FEAT-006](../03_features.md#feat-006) | [FR-019](../02_functional_requirements.md#fr-019), [FR-020](../02_functional_requirements.md#fr-020) | [comp-003](../07_components.md#comp-003), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011) | ✅ TRACEABLE |
| F4.D1 | deliverable | Admin Access Control | [SCN-016](../04b_scenarios.md#scn-016) | [FEAT-007](../03_features.md#feat-007) | [FR-023](../02_functional_requirements.md#fr-023) | [comp-002](../07_components.md#comp-002), [comp-009](../07_components.md#comp-009) | ⚠️ ENABLING |
| F4.D1.WP1 | work_package | Implement admin authentication and protected session handling | [SCN-016](../04b_scenarios.md#scn-016) | [FEAT-007](../03_features.md#feat-007) | [FR-023](../02_functional_requirements.md#fr-023) | [comp-002](../07_components.md#comp-002), [comp-009](../07_components.md#comp-009) | ✅ TRACEABLE |
| F4.D2 | deliverable | Backoffice Menu and Order Operations | [SCN-014](../04b_scenarios.md#scn-014), [SCN-015](../04b_scenarios.md#scn-015), [SCN-012](../04b_scenarios.md#scn-012), [SCN-013](../04b_scenarios.md#scn-013) | [FEAT-007](../03_features.md#feat-007), [FEAT-006](../03_features.md#feat-006) | [FR-024](../02_functional_requirements.md#fr-024), [FR-025](../02_functional_requirements.md#fr-025), [FR-026](../02_functional_requirements.md#fr-026), [FR-027](../02_functional_requirements.md#fr-027), [FR-021](../02_functional_requirements.md#fr-021), [FR-022](../02_functional_requirements.md#fr-022) | [comp-002](../07_components.md#comp-002), [comp-005](../07_components.md#comp-005), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F4.D2.WP1 | work_package | Implement menu item creation and editing with validation | [SCN-014](../04b_scenarios.md#scn-014) | [FEAT-007](../03_features.md#feat-007) | [FR-024](../02_functional_requirements.md#fr-024), [FR-025](../02_functional_requirements.md#fr-025) | [comp-002](../07_components.md#comp-002), [comp-005](../07_components.md#comp-005) | ✅ TRACEABLE |
| F4.D2.WP2 | work_package | Implement menu visibility toggles and deletion safeguards | [SCN-015](../04b_scenarios.md#scn-015) | [FEAT-007](../03_features.md#feat-007) | [FR-026](../02_functional_requirements.md#fr-026), [FR-027](../02_functional_requirements.md#fr-027) | [comp-002](../07_components.md#comp-002), [comp-005](../07_components.md#comp-005) | ✅ TRACEABLE |
| F4.D2.WP3 | work_package | Implement admin order-readiness and display-removal controls | [SCN-012](../04b_scenarios.md#scn-012), [SCN-013](../04b_scenarios.md#scn-013) | [FEAT-006](../03_features.md#feat-006) | [FR-021](../02_functional_requirements.md#fr-021), [FR-022](../02_functional_requirements.md#fr-022) | [comp-002](../07_components.md#comp-002), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011) | ✅ TRACEABLE |
| F5.D1 | deliverable | Compliance and Security Hardening | — | — | [FR-011](../02_functional_requirements.md#fr-011), [FR-023](../02_functional_requirements.md#fr-023), [FR-001](../02_functional_requirements.md#fr-001), [FR-017](../02_functional_requirements.md#fr-017), [FR-021](../02_functional_requirements.md#fr-021), [FR-024](../02_functional_requirements.md#fr-024) | [comp-004](../07_components.md#comp-004), [comp-006](../07_components.md#comp-006), [comp-009](../07_components.md#comp-009), [comp-010](../07_components.md#comp-010), [comp-005](../07_components.md#comp-005), [comp-007](../07_components.md#comp-007), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |
| F5.D1.WP1 | work_package | Implement GDPR retention purge and secure session policies | — | — | [FR-011](../02_functional_requirements.md#fr-011), [FR-023](../02_functional_requirements.md#fr-023) | [comp-004](../07_components.md#comp-004), [comp-006](../07_components.md#comp-006), [comp-009](../07_components.md#comp-009), [comp-010](../07_components.md#comp-010) | ✅ TRACEABLE |
| F5.D1.WP2 | work_package | Implement platform-wide validation authorization audit and abuse controls | — | — | [FR-001](../02_functional_requirements.md#fr-001), [FR-017](../02_functional_requirements.md#fr-017), [FR-021](../02_functional_requirements.md#fr-021), [FR-024](../02_functional_requirements.md#fr-024) | [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-007](../07_components.md#comp-007), [comp-008](../07_components.md#comp-008), [comp-009](../07_components.md#comp-009), [comp-011](../07_components.md#comp-011) | ✅ TRACEABLE |
| F5.D2 | deliverable | Performance, Reliability, and Release Readiness | — | [FEAT-002](../03_features.md#feat-002), [FEAT-003](../03_features.md#feat-003), [FEAT-004](../03_features.md#feat-004), [FEAT-005](../03_features.md#feat-005), [FEAT-006](../03_features.md#feat-006) | — | [comp-001](../07_components.md#comp-001), [comp-003](../07_components.md#comp-003), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011), [comp-002](../07_components.md#comp-002), [comp-004](../07_components.md#comp-004), [comp-007](../07_components.md#comp-007), [comp-009](../07_components.md#comp-009), [comp-010](../07_components.md#comp-010) | ⚠️ ENABLING |
| F5.D2.WP1 | work_package | Optimize performance and concurrency for customer and display flows | — | [FEAT-002](../03_features.md#feat-002), [FEAT-003](../03_features.md#feat-003), [FEAT-004](../03_features.md#feat-004), [FEAT-005](../03_features.md#feat-005), [FEAT-006](../03_features.md#feat-006) | — | [comp-001](../07_components.md#comp-001), [comp-003](../07_components.md#comp-003), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-008](../07_components.md#comp-008), [comp-011](../07_components.md#comp-011) | ✅ TRACEABLE |
| F5.D2.WP2 | work_package | Execute automated quality suite and go-live operational validation | — | — | — | [comp-001](../07_components.md#comp-001), [comp-002](../07_components.md#comp-002), [comp-003](../07_components.md#comp-003), [comp-004](../07_components.md#comp-004), [comp-005](../07_components.md#comp-005), [comp-006](../07_components.md#comp-006), [comp-007](../07_components.md#comp-007), [comp-008](../07_components.md#comp-008), [comp-009](../07_components.md#comp-009), [comp-010](../07_components.md#comp-010), [comp-011](../07_components.md#comp-011) | ⚠️ ENABLING |

## traceability_matrix_scenarios_or_stories

| scenario_or_story_id | title | covered_by_wbs_items | status |
|---|---|---|---|
| SCN-001 | Successful Session Initiation — Self-Service Mode | [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-002 | Successful Session Initiation — Staff-Assisted Mode | [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-003 | Invalid or Unrecognised QR Code | [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-004 | Customer Browses Menu and Adds Multiple Items | [F2.D2.WP1](10_wbs.md#wbs_table), [F2.D2.WP2](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-005 | Customer Removes an Item from Cart | [F2.D2.WP2](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-006 | Successful Self-Service Order with Card Payment | [F3.D1.WP2](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-007 | Successful Self-Service Order with Cash Payment | [F3.D1.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-008 | Submission Attempted with Empty Cart | [F3.D1.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-009 | Card Payment Failure | [F3.D1.WP2](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-010 | Customer Requests Staff Assistance After Browsing | [F2.D3.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-011 | Customer Monitors Order Status on Public Display | [F3.D2.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-012 | Admin Marks Order as Ready for Pickup | [F4.D2.WP3](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-013 | Order Removed from Display After Timeout | [F4.D2.WP3](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-014 | Admin Adds a New Menu Item | [F4.D2.WP1](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-015 | Admin Disables an Unavailable Menu Item | [F4.D2.WP2](10_wbs.md#wbs_table) | ✅ COVERED |
| SCN-016 | Admin Attempts Login with Invalid Credentials | [F4.D1.WP1](10_wbs.md#wbs_table) | ✅ COVERED |

## traceability_matrix_features

| feature_id | feature_name | related_scenarios_or_stories | covered_by_wbs_items | coverage_status |
|---|---|---|---|---|
| FEAT-001 | QR-Based Table Session Initiation | [SCN-001](../04b_scenarios.md#scn-001), [SCN-002](../04b_scenarios.md#scn-002), [SCN-003](../04b_scenarios.md#scn-003) | [F1.D1.WP2](10_wbs.md#wbs_table), [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FEAT-002 | Menu Browsing with Full Item Details | [SCN-004](../04b_scenarios.md#scn-004) | [F2.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FEAT-003 | Order Composition and Cart | [SCN-004](../04b_scenarios.md#scn-004), [SCN-005](../04b_scenarios.md#scn-005) | [F2.D2.WP2](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FEAT-004 | Self-Service Checkout and Payment | [SCN-006](../04b_scenarios.md#scn-006), [SCN-007](../04b_scenarios.md#scn-007), [SCN-008](../04b_scenarios.md#scn-008), [SCN-009](../04b_scenarios.md#scn-009) | [F3.D1.WP1](10_wbs.md#wbs_table), [F3.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FEAT-005 | Staff Assistance Request | [SCN-010](../04b_scenarios.md#scn-010) | [F1.D2.WP2](10_wbs.md#wbs_table), [F2.D3.WP1](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FEAT-006 | Order Status Public Display | [SCN-011](../04b_scenarios.md#scn-011), [SCN-012](../04b_scenarios.md#scn-012), [SCN-013](../04b_scenarios.md#scn-013) | [F1.D2.WP2](10_wbs.md#wbs_table), [F3.D2.WP1](10_wbs.md#wbs_table), [F4.D2.WP3](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FEAT-007 | Menu Management | [SCN-014](../04b_scenarios.md#scn-014), [SCN-015](../04b_scenarios.md#scn-015), [SCN-016](../04b_scenarios.md#scn-016) | [F1.D1.WP2](10_wbs.md#wbs_table), [F4.D1.WP1](10_wbs.md#wbs_table), [F4.D2.WP1](10_wbs.md#wbs_table), [F4.D2.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |

## traceability_matrix_requirements_or_epics

| requirement_or_epic_id | name | related_features | covered_by_wbs_items | coverage_status |
|---|---|---|---|---|
| FR-001 | QR Code Session Activation | [FEAT-001](../03_features.md#feat-001) | [F2.D1.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-002 | Customer Name Entry | [FEAT-001](../03_features.md#feat-001) | [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-003 | Service Mode Selection | [FEAT-001](../03_features.md#feat-001) | [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-004 | Table-Session Association | [FEAT-001](../03_features.md#feat-001) | [F1.D1.WP2](10_wbs.md#wbs_table), [F2.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-005 | Menu Display by Category | [FEAT-002](../03_features.md#feat-002) | [F2.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-006 | Item Detail Display | [FEAT-002](../03_features.md#feat-002) | [F2.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-007 | Add Item to Order | [FEAT-003](../03_features.md#feat-003) | [F2.D2.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-008 | Adjust Item Quantity | [FEAT-003](../03_features.md#feat-003) | [F2.D2.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-009 | Running Order Summary | [FEAT-003](../03_features.md#feat-003) | [F2.D2.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-010 | Order Review Before Submission | [FEAT-004](../03_features.md#feat-004) | [F3.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-011 | Payment Method Selection | [FEAT-004](../03_features.md#feat-004) | [F3.D1.WP1](10_wbs.md#wbs_table), [F3.D1.WP2](10_wbs.md#wbs_table), [F5.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-012 | Order Submission and Number Assignment | [FEAT-004](../03_features.md#feat-004) | [F3.D1.WP1](10_wbs.md#wbs_table), [F3.D1.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-013 | Order Confirmation Display | [FEAT-004](../03_features.md#feat-004) | [F3.D1.WP1](10_wbs.md#wbs_table), [F3.D1.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-014 | Empty Cart Validation | [FEAT-004](../03_features.md#feat-004) | [F3.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-015 | Menu Display in Staff-Assisted Mode | [FEAT-005](../03_features.md#feat-005) | [F2.D3.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-016 | Customer Readiness Signal | [FEAT-005](../03_features.md#feat-005) | [F2.D3.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-017 | Staff Notification | [FEAT-005](../03_features.md#feat-005) | [F2.D3.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-018 | No Payment or Order Number in Staff Mode | [FEAT-005](../03_features.md#feat-005) | [F2.D3.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-019 | Public Order Status Display | [FEAT-006](../03_features.md#feat-006) | [F3.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-020 | Order Status Tracking | [FEAT-006](../03_features.md#feat-006) | [F3.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-021 | Admin Mark Order Ready | [FEAT-006](../03_features.md#feat-006) | [F4.D2.WP3](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-022 | Order Removal from Display | [FEAT-006](../03_features.md#feat-006) | [F4.D2.WP3](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-023 | Admin Interface Access Control | [FEAT-007](../03_features.md#feat-007) | [F4.D1.WP1](10_wbs.md#wbs_table), [F5.D1.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-024 | Add Menu Item | [FEAT-007](../03_features.md#feat-007) | [F4.D2.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-025 | Edit Menu Item | [FEAT-007](../03_features.md#feat-007) | [F4.D2.WP1](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-026 | Enable or Disable Menu Item | [FEAT-007](../03_features.md#feat-007) | [F4.D2.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |
| FR-027 | Remove Menu Item Permanently | [FEAT-007](../03_features.md#feat-007) | [F4.D2.WP2](10_wbs.md#wbs_table) | ✅ COMPLETE |

## traceability_matrix_components

| component_id | component_name | covered_by_wbs_items | features_supported | coverage_status |
|---|---|---|---|---|
| comp-001 | Customer Web Experience | [F1.D2.WP1](10_wbs.md#wbs_table), [F1.D2.WP2](10_wbs.md#wbs_table), [F1.D3.WP1](10_wbs.md#wbs_table), [F2.D1.WP1](10_wbs.md#wbs_table), [F2.D2.WP1](10_wbs.md#wbs_table), [F2.D2.WP2](10_wbs.md#wbs_table), [F2.D3.WP1](10_wbs.md#wbs_table), [F3.D1.WP1](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-001](../03_features.md#feat-001), [FEAT-002](../03_features.md#feat-002), [FEAT-003](../03_features.md#feat-003), [FEAT-004](../03_features.md#feat-004), [FEAT-005](../03_features.md#feat-005), [FEAT-006](../03_features.md#feat-006) | ✅ COVERED |
| comp-002 | Admin Backoffice Experience | [F1.D2.WP1](10_wbs.md#wbs_table), [F1.D2.WP2](10_wbs.md#wbs_table), [F4.D1.WP1](10_wbs.md#wbs_table), [F4.D2.WP1](10_wbs.md#wbs_table), [F4.D2.WP2](10_wbs.md#wbs_table), [F4.D2.WP3](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-006](../03_features.md#feat-006), [FEAT-007](../03_features.md#feat-007) | ✅ COVERED |
| comp-003 | Public Display Experience | [F1.D2.WP1](10_wbs.md#wbs_table), [F1.D2.WP2](10_wbs.md#wbs_table), [F3.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-006](../03_features.md#feat-006) | ✅ COVERED |
| comp-004 | Session & Table Service | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D1.WP2](10_wbs.md#wbs_table), [F1.D3.WP1](10_wbs.md#wbs_table), [F2.D1.WP1](10_wbs.md#wbs_table), [F2.D3.WP1](10_wbs.md#wbs_table), [F5.D1.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-001](../03_features.md#feat-001), [FEAT-005](../03_features.md#feat-005) | ✅ COVERED |
| comp-005 | Menu Catalog Service | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D1.WP2](10_wbs.md#wbs_table), [F1.D3.WP1](10_wbs.md#wbs_table), [F2.D2.WP1](10_wbs.md#wbs_table), [F2.D3.WP1](10_wbs.md#wbs_table), [F4.D2.WP1](10_wbs.md#wbs_table), [F4.D2.WP2](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-002](../03_features.md#feat-002), [FEAT-007](../03_features.md#feat-007) | ✅ COVERED |
| comp-006 | Order Management Service | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D1.WP2](10_wbs.md#wbs_table), [F1.D3.WP1](10_wbs.md#wbs_table), [F1.D3.WP2](10_wbs.md#wbs_table), [F2.D2.WP2](10_wbs.md#wbs_table), [F3.D1.WP1](10_wbs.md#wbs_table), [F3.D1.WP2](10_wbs.md#wbs_table), [F5.D1.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-003](../03_features.md#feat-003), [FEAT-004](../03_features.md#feat-004) | ✅ COVERED |
| comp-007 | Assistance Coordination Service | [F1.D1.WP1](10_wbs.md#wbs_table), [F2.D3.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-005](../03_features.md#feat-005) | ✅ COVERED |
| comp-008 | Order Status Service | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D1.WP2](10_wbs.md#wbs_table), [F1.D3.WP1](10_wbs.md#wbs_table), [F1.D3.WP2](10_wbs.md#wbs_table), [F3.D2.WP1](10_wbs.md#wbs_table), [F4.D2.WP3](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-006](../03_features.md#feat-006) | ✅ COVERED |
| comp-009 | Access Control Module | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D1.WP2](10_wbs.md#wbs_table), [F4.D1.WP1](10_wbs.md#wbs_table), [F5.D1.WP1](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-007](../03_features.md#feat-007) | ✅ COVERED |
| comp-010 | Payment Gateway Adapter | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D3.WP2](10_wbs.md#wbs_table), [F3.D1.WP2](10_wbs.md#wbs_table), [F5.D1.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-004](../03_features.md#feat-004) | ✅ COVERED |
| comp-011 | Realtime Update Gateway | [F1.D1.WP1](10_wbs.md#wbs_table), [F1.D2.WP2](10_wbs.md#wbs_table), [F1.D3.WP2](10_wbs.md#wbs_table), [F2.D3.WP1](10_wbs.md#wbs_table), [F3.D2.WP1](10_wbs.md#wbs_table), [F4.D2.WP3](10_wbs.md#wbs_table), [F5.D1.WP2](10_wbs.md#wbs_table), [F5.D2.WP1](10_wbs.md#wbs_table), [F5.D2.WP2](10_wbs.md#wbs_table) | [FEAT-005](../03_features.md#feat-005), [FEAT-006](../03_features.md#feat-006) | ✅ COVERED |

## gap_analysis

### Uncovered Scenarios or User Stories
| scenario_or_story_id | title | parent_feature | reason_assessment |
|---|---|---|---|
| — | None | — | All scenarios are covered by at least one work package. |

### Uncovered Features
| feature_id | feature_name | parent_requirement_or_epic | scenario_or_story_count | reason_assessment |
|---|---|---|---|---|
| — | None | — | 0 | All features are represented in the WBS. |

### Uncovered Requirements or Epics
| requirement_or_epic_id | name | related_features | reason_assessment |
|---|---|---|---|
| — | None | — | All functional requirements are covered by at least one work package. |

### Uncovered Components
| component_id | component_name | supported_features | reason_assessment |
|---|---|---|---|
| — | None | — | Every logical component is explicitly addressed by the WBS. |

### Recommendations
- No structural gaps were identified; preserve the declared source_refs and traceability links during implementation to maintain 100% coverage.

COVERAGE_COMPLETED: 100% scenarios, 100% features, 100% requirements, 100% components — 0 gaps
