# FP Sizing — TableOrder

**Project:** tableorder  
**Method:** IFPUG + SNAP  
**Calculation mode:** MCP (deterministic)  
**Date:** 2026-06-26  
**Status:** FP_DRAFT

---

## 1. Perimeter & Boundary

| | |
|---|---|
| **System boundary** | TableOrder web application (customer-facing ordering + admin management interface) |
| **Primary actors** | Customer (role-001), Admin (role-002) |
| **Supporting actor** | Staff Member (role-003 — receives on-screen notification only) |
| **External system** | Payment Gateway (card processing; EIF — data maintained externally) |

---

## 2. IFPUG Data Functions

### Internal Logical Files (ILF)

| ID | Name | DETs | RETs | Complexity | FP |
|---|---|---|---|---|---|
| ILF-01 | MenuItem | 8 | 1 | Low | 7 |
| ILF-02 | Order | 10 | 2 | Low | 7 |
| ILF-03 | CustomerSession | 5 | 1 | Low | 7 |
| ILF-04 | AdminUser | 4 | 1 | Low | 7 |
| ILF-05 | Table | 3 | 1 | Low | 7 |
| | | | | **Subtotal ILF** | **35** |

**ILF detail:**

- **MenuItem** — id, name, description, price, category, allergen_info, photo_url, enabled (1 subgroup)
- **Order** — header: order_number, table_id, customer_name, payment_method, status, created_at; lines: item_id, item_name, qty, unit_price (2 subgroups: header + line items)
- **CustomerSession** — session_id, table_id, customer_name, service_mode, readiness_flag (1 subgroup)
- **AdminUser** — username, password_hash, session_token, last_login (1 subgroup)
- **Table** — table_id, qr_code, capacity (1 subgroup)

### External Interface Files (EIF)

| ID | Name | DETs | RETs | Complexity | FP |
|---|---|---|---|---|---|
| EIF-01 | PaymentGateway | 5 | 1 | Low | 5 |
| | | | | **Subtotal EIF** | **5** |

**EIF detail:**

- **PaymentGateway** — transaction_id, status, amount, currency, timestamp; maintained by external card processor

---

## 3. IFPUG Transactional Functions

### External Inputs (EI)

| ID | Name | Source FR | DETs | FTRs | Complexity | FP |
|---|---|---|---|---|---|---|
| EI-01 | Session Initiation via QR | FR-001, FR-002 | 3 | 1 | Low | 3 |
| EI-02 | Service Mode Selection | FR-003 | 2 | 1 | Low | 3 |
| EI-03 | Add Item to Cart | FR-008, FR-010 | 3 | 1 | Low | 3 |
| EI-04 | Update Cart Item Quantity | FR-010 | 3 | 1 | Low | 3 |
| EI-05 | Submit Order | FR-011, FR-012 | 7 | 2 | Average | 4 |
| EI-06 | Signal Staff Readiness | FR-004 | 2 | 1 | Low | 3 |
| EI-07 | Admin Login | FR-022 | 2 | 1 | Low | 3 |
| EI-08 | Admin Add Menu Item | FR-017, FR-018 | 7 | 1 | Low | 3 |
| EI-09 | Admin Edit Menu Item | FR-017, FR-018 | 7 | 1 | Low | 3 |
| EI-10 | Admin Enable/Disable Menu Item | FR-017 | 2 | 1 | Low | 3 |
| EI-11 | Admin Delete Menu Item | FR-017 | 1 | 1 | Low | 3 |
| EI-12 | Admin Mark Order Ready | FR-025 | 2 | 1 | Low | 3 |
| EI-13 | Payment Gateway Response | FR-013, FR-014 | 5 | 2 | Average | 4 |
| | | | | | **Subtotal EI** | **40** |

### External Outputs (EO)

| ID | Name | Source FR | DETs | FTRs | Complexity | FP |
|---|---|---|---|---|---|---|
| EO-01 | Order Confirmation with Order Number | FR-015, FR-016 | 5 | 2 | Low | 4 |
| EO-02 | Running Order Total | FR-009 | 4 | 1 | Low | 4 |
| EO-03 | Staff Readiness Notification | FR-005 | 3 | 1 | Low | 4 |
| EO-04 | Public Order Status Update | FR-019, FR-020 | 3 | 1 | Low | 4 |
| EO-05 | Payment Failure Message | FR-014 | 3 | 1 | Low | 4 |
| | | | | | **Subtotal EO** | **20** |

### External Queries (EQ)

| ID | Name | Source FR | DETs | FTRs | Complexity | FP |
|---|---|---|---|---|---|---|
| EQ-01 | Customer Menu Display | FR-006, FR-007 | 8 | 1 | Low | 3 |
| EQ-02 | Admin Order Queue | FR-024 | 6 | 1 | Low | 3 |
| EQ-03 | Admin Menu List | FR-021 | 8 | 1 | Low | 3 |
| EQ-04 | Admin Single Item View | FR-021 | 8 | 1 | Low | 3 |
| | | | | | **Subtotal EQ** | **12** |

---

## 4. IFPUG Summary

| Category | Count | FP |
|---|---|---|
| ILF | 5 | 35 |
| EIF | 1 | 5 |
| EI | 13 | 40 |
| EO | 5 | 20 |
| EQ | 4 | 12 |
| **Total UFP** | **28** | **112** |

---

## 5. SNAP Classification

| ID | Name | NFR Ref | SNAP Sub-category | Group | Complexity | SNAP Pts |
|---|---|---|---|---|---|---|
| SN-01 | Allergen Data Validation | FR-018, NFR-011 | 1.3 Data Formatting | Data Operations | Low | 1 |
| SN-02 | QR Code Validation | FR-001, FR-002 | 1.3 Data Formatting | Data Operations | Low | 1 |
| SN-03 | GDPR Data Purge on Order Completion | NFR-009 | 4.1 Component-Based Software | Architecture | High | 10 |
| SN-04 | Admin Session Timeout | NFR-006 | 4.1 Component-Based Software | Architecture | High | 10 |
| | | | | | **Total SNAP** | **22** |

**SNAP narrative:**

- **SN-01 Allergen Data Validation** — System enforces that `allergen_info` must be populated before a menu item can be enabled/published. Constraint applied at EI-08 and EI-09.
- **SN-02 QR Code Validation** — Session initiation (EI-01) rejects unrecognised or malformed QR codes; `table_id` must exist in ILF-05 (Table).
- **SN-03 GDPR Data Purge** — Customer name and session data in ILF-03 (CustomerSession) are automatically deleted upon order lifecycle completion, enforcing the GDPR data minimisation requirement (EU/EEA).
- **SN-04 Admin Session Timeout** — ILF-04 (AdminUser) session token is invalidated after a configurable inactivity period. ⚠️ *Timeout value flagged as `[TO BE REFINED]` in NFR-006.*

---

## 6. Effort Estimate

| Metric | Value |
|---|---|
| Total UFP (IFPUG) | 112 FP |
| Total SNAP | 22 pts (≈ 4.4 FP equivalent) |
| **Total Equivalent FP** | **116.4** |
| Team velocity | Medium (8 h/FP — standard team) |
| **Estimated effort** | **931 h** |
| **Person-days** | **116 GG/U** |

### Velocity scenarios

| Scenario | Rate | Hours | Person-Days |
|---|---|---|---|
| High (experienced team) | 6 h/FP | ~699 h | ~87 GG/U |
| **Medium (standard team)** | **8 h/FP** | **~931 h** | **~116 GG/U** |
| Low (junior/complex stack) | 12 h/FP | ~1,397 h | ~175 GG/U |

> **Recommended planning baseline:** 116 GG/U (Medium velocity). A technical team is on standby — if experienced with Java + modern frontend, the High scenario (87 GG/U) is a realistic optimistic bound.

---

## 7. Key Assumptions & Open Points

| # | Item | Impact |
|---|---|---|
| 1 | NFR-006 Admin session timeout value is `[TO BE REFINED]` | SNAP SN-04 complexity confirmed as High; actual implementation effort unaffected |
| 2 | No kitchen/staff view in v1 scope | No additional ILFs or EIs for staff-side management |
| 3 | Card data handled exclusively by payment gateway | EIF-01 count is minimal; no PCI-DSS ILF required |
| 4 | QR code generation out of scope (pre-printed labels assumed) | No EO for QR generation included |
| 5 | Public order status display is read-only polling | Classified as EO-04, not a real-time push |
| 6 | ~10 tables, peak ~40-50 concurrent users | Does not affect FP count; affects NFR scaling only |

---

## 8. Traceability

| IFPUG Element | Features | Use Cases |
|---|---|---|
| ILF-01 MenuItem | FEAT-001 (Menu Browsing), FEAT-003 (Menu Management) | UC-001, UC-005 |
| ILF-02 Order | FEAT-002 (Ordering), FEAT-005 (Payment) | UC-002, UC-003, UC-006 |
| ILF-03 CustomerSession | FEAT-001, FEAT-002, FEAT-006 (Order Status) | UC-001, UC-002 |
| ILF-04 AdminUser | FEAT-003, FEAT-004 (Admin Dashboard) | UC-004, UC-005 |
| ILF-05 Table | FEAT-007 (QR Access) | UC-001 |
| EIF-01 PaymentGateway | FEAT-005 | UC-003 |
