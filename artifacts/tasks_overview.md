# TableOrder — Obsidian Task Overview

> 63 tasks · 5 phases · A1→A2→A3 dependency chains per Work Package  
> Generated: 2026-06-26

---

## 🏗️ F1 — Project Foundation & Platform Setup (18 tasks)

### F1.D1.WP1 — Backend Modular Skeleton
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-002 | A1 | Define backend module boundaries and ownership rules | ⬆ High | todo |
| T-022 | A2 | Create Spring Boot application skeleton and shared bootstrap code | ⬆ High | todo |
| T-045 | A3 | Verify module isolation and startup health with smoke checks | ⬆ High | todo |

### F1.D1.WP2 — Database Schema & Migrations
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-009 | A1 | Define module-owned database schemas and migration conventions | ⬆ High | todo |
| T-024 | A2 | Create baseline migrations, seed data, and retention placeholders | ⬆ High | todo |
| T-044 | A3 | Verify migration repeatability and seed integrity | ⬆ High | todo |

### F1.D2.WP1 — Frontend Workspace & Design System
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-001 | A1 | Design route shells and responsive UI primitives | ⬆ High | todo |
| T-023 | A2 | Create React workspace structure and design-system scaffolding | ⬆ High | todo |
| T-043 | A3 | Verify responsive rendering and build stability | ⬆ High | todo |

### F1.D2.WP2 — State Management & API Integration
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-004 | A1 | Design frontend state boundaries and transport conventions | ⬆ High | todo |
| T-025 | A2 | Implement shared API clients, route guards, and realtime adapters | ⬆ High | todo |
| T-046 | A3 | Verify session persistence, route protection, and realtime reconnection | ⬆ High | todo |

### F1.D3.WP1 — CI/CD & Dev Environment
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-006 | A1 | Define local environment and pipeline workflow | ⬆ High | todo |
| T-026 | A2 | Create development compose stack, CI jobs, and deployment packaging | ⬆ High | todo |
| T-048 | A3 | Verify environment bootstrap and pipeline repeatability | ⬆ High | todo |

### F1.D3.WP2 — Observability & Resilience Primitives
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-003 | A1 | Define observability and resilience conventions | ⬆ High | todo |
| T-029 | A2 | Implement logging, metrics, health endpoints, and retry-config primitives | ⬆ High | todo |
| T-047 | A3 | Verify operational signals and degraded-mode behavior | ⬆ High | todo |

---

## 🛒 F2 — Customer Ordering Experience (12 tasks)

### F2.D1.WP1 — QR Code Onboarding
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-005 | A1 | Design QR onboarding screens and decision points | ⬆ High | todo |
| T-028 | A2 | Implement QR validation, session persistence, and mode-based routing | ⬆ High | todo |
| T-049 | A3 | Verify successful and invalid QR journeys | ⬆ High | todo |

### F2.D2.WP1 — Menu Catalog & Allergen Display
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-007 | A1 | Design mobile menu discovery layouts and allergen prominence | ⬆ High | todo |
| T-027 | A2 | Implement customer menu queries and responsive catalog presentation | ⬆ High | todo |
| T-050 | A3 | Verify menu completeness, latency, and responsive readability | ⬆ High | todo |

### F2.D2.WP2 — Cart & Running Total
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-021 | A1 | Design cart interactions and persistent total visibility | ⬆ High | todo |
| T-030 | A2 | Implement cart state mutations and real-time totals | ⬆ High | todo |
| T-051 | A3 | Verify cart calculation accuracy and mutation behavior | ⬆ High | todo |

### F2.D3.WP1 — Assisted-Service Browse Mode
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-008 | A1 | Design browse-only assisted-service screens and readiness interaction | — Med | todo |
| T-031 | A2 | Implement assisted-mode browsing and staff notification orchestration | — Med | todo |
| T-052 | A3 | Verify no-order constraints and notification delivery | — Med | todo |

---

## 💳 F3 — Payment & Order Lifecycle (9 tasks)

### F3.D1.WP1 — Checkout & Cash Payment
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-012 | A1 | Design checkout review and payment-choice screens | ⬆ High | todo |
| T-032 | A2 | Implement checkout validation, payment selection, cash confirmation | ⬆ High | todo |
| T-054 | A3 | Verify checkout validation and cash confirmation integrity | ⬆ High | todo |

### F3.D1.WP2 — Card Payment via Stripe
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-011 | A1 | Design card-payment and failure-recovery states | ⬆ High | todo |
| T-033 | A2 | Implement Stripe authorization adapter and idempotent confirmation path | ⬆ High | todo |
| T-053 | A3 | Verify card success, failure, and data-isolation with Stripe tests | ⬆ High | todo |

### F3.D2.WP1 — Public Order Display
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-010 | A1 | Design public display states and order-number visibility | — Med | todo |
| T-034 | A2 | Implement order-status projections and public display rendering | — Med | todo |
| T-055 | A3 | Verify display freshness, readability, and lifecycle accuracy | — Med | todo |

---

## ⚙️ F4 — Admin & Menu Management (12 tasks)

### F4.D1.WP1 — Admin Authentication
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-013 | A1 | Design admin login and protected-session behaviors | ⬆ High | todo |
| T-040 | A2 | Implement admin credential verification, session expiry, route enforcement | ⬆ High | todo |
| T-056 | A3 | Verify invalid-login handling and session-expiry protection | ⬆ High | todo |

### F4.D2.WP1 — Menu Item Create & Edit
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-016 | A1 | Design menu-maintenance forms and validation feedback | — Med | todo |
| T-035 | A2 | Implement menu create/edit workflows with allergen publishability validation | — Med | todo |
| T-057 | A3 | Verify create-edit validation and catalog persistence | — Med | todo |

### F4.D2.WP2 — Item Visibility & Deletion
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-018 | A1 | Design visibility-toggle and delete-confirmation interactions | — Med | todo |
| T-038 | A2 | Implement item visibility updates and deletion safeguards | — Med | todo |
| T-058 | A3 | Verify visibility propagation and deletion safety | — Med | todo |

### F4.D2.WP3 — Order Queue & Readiness Management
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-017 | A1 | Design order-queue readiness actions and timeout-control feedback | — Med | todo |
| T-036 | A2 | Implement readiness commands, timeout rules, and display-removal updates | — Med | todo |
| T-059 | A3 | Verify readiness-update latency and timeout cleanup | — Med | todo |

---

## 🔒 F5 — Cross-Cutting Concerns & Production Readiness (12 tasks)

### F5.D1.WP1 — GDPR & Secure Session
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-015 | A1 | Define retention and secure-session policies (GDPR) | ⬆ High | todo |
| T-039 | A2 | Implement automated data purge, secure cookies, secret-backed payment config | ⬆ High | todo |
| T-062 | A3 | Verify retention execution and secure-session enforcement | ⬆ High | todo |

### F5.D1.WP2 — Validation, Authorization & Audit
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-020 | A1 | Define validation, authorization, and audit-control standards | ⬆ High | todo |
| T-037 | A2 | Implement validation guards, audit events, and abuse throttles | ⬆ High | todo |
| T-060 | A3 | Verify protected-action logging and abuse-control behavior | ⬆ High | todo |

### F5.D2.WP1 — Performance & Load Testing
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-014 | A1 | Define performance hotspots and concurrency test targets | ⬆ High | todo |
| T-042 | A2 | Implement caching, query tuning, and transport fallbacks | ⬆ High | todo |
| T-061 | A3 | Verify load behavior and response targets with soak tests | ⬆ High | todo |

### F5.D2.WP2 — Release Gates & Go-Live
| Task | Type | Title | Priority | Status |
|------|------|-------|----------|--------|
| T-019 | A1 | Define release gates, dashboards, and rollback criteria | ⬆ High | todo |
| T-041 | A2 | Execute regression automation and finalize production monitoring | ⬆ High | todo |
| T-063 | A3 | Verify release readiness and go-live deployment behavior | ⬆ High | todo |

---

## Summary

| Phase | Tasks | High Priority | Med Priority |
|-------|-------|---------------|--------------|
| F1 — Foundation | 18 | 18 | 0 |
| F2 — Ordering Experience | 12 | 9 | 3 |
| F3 — Payment & Lifecycle | 9 | 6 | 3 |
| F4 — Admin & Menu | 12 | 3 | 9 |
| F5 — Cross-Cutting | 12 | 12 | 0 |
| **Total** | **63** | **48** | **15** |

> **Dependency rule:** within each Work Package, A1 must be done before A2, and A2 before A3.  
> A1 tasks across different WPs are fully independent and can start in parallel.
