# TableOrder App — Analysis Artifacts

## Generated Artifacts

| File | Description |
|---|---|
| [01_business_requirements.md](01_business_requirements.md) | Business requirements extracted from the PRD and the list of system roles (Customer, Admin, Staff Member). |
| [02_functional_requirements.md](02_functional_requirements.md) | Functional areas and atomic functional requirements with actors, inputs, outputs, and business rules. |
| [03_features.md](03_features.md) | Feature catalog mapping discrete capabilities to business and functional requirements with roles and business value. |
| [04_use_cases.md](04_use_cases.md) | Use case catalog describing goal-oriented interactions between actors and the system, with preconditions and postconditions. |
| [04b_scenarios.md](04b_scenarios.md) | Scenario catalog with Main, Alternate, and Exception paths, including step-by-step execution traces per scenario. |
| [04c_non_functional_requirements.md](04c_non_functional_requirements.md) | Non-functional requirements organized by quality area (Performance, Availability, Security, Usability, Scalability, Maintainability). |

## Traceability Chain

```
BR (Business Requirement)
 └── FR (Functional Requirement)   — what the system must do to satisfy the BR
      └── Feature                  — a coherent capability grouping one or more FRs
           └── Use Case            — a goal-oriented actor interaction traced to Features and FRs
                └── Scenario       — a concrete execution path (Main / Alternate / Exception) for a Use Case

NFR (Non-Functional Requirement)   — quality conditions that apply across the entire solution,
                                     each traced to one or more BRs
```

## Statistics

- **Business Requirements:** 4 (BR-001 → BR-004)
- **Roles:** 3 (Customer, Admin, Staff Member)
- **Functional Areas:** 6 (FA-001 → FA-006)
- **Functional Requirements:** 27 (FR-001 → FR-027)
- **Features:** 7 (FEAT-001 → FEAT-007)
- **Use Cases:** 7 (UC-001 → UC-007)
- **Scenarios:** 16 (SCN-001 → SCN-016) — 8 Main, 4 Alternate, 4 Exception
- **Non-Functional Requirements:** 12 (NFR-001 → NFR-012) across 6 quality areas

## Design Artifacts

| File | Description |
|---|---|
| [05_logical_entities.md](05_logical_entities.md) | Bounded contexts, logical entity catalog, relationships, and ER diagram for the TableOrder domain model. |
| [06_processes.md](06_processes.md) | Core, supporting, and management business processes with detailed steps and Mermaid flowcharts. |
| [07_components.md](07_components.md) | Logical components, interfaces, responsibilities, and the component diagram for the application design. |
| [08_dependencies.md](08_dependencies.md) | Dependency catalog, risk analysis, requirement traceability matrix, and dependency graph. |
| [09_architecture_design.md](09_architecture_design.md) | Architecture characteristics, style fitness analysis, ADRs, C4 diagrams, mapping tables, and architecture quanta. |

### Design Navigation Notes

- IDs inside the design artifacts are cross-linked across files for fast navigation between entities, processes, components, dependencies, and ADRs.
- Upstream requirement IDs also link back to the analysis artifacts so that each design decision can be traced to its source.
- Start with `05_logical_entities.md`, continue through `08_dependencies.md`, and use `09_architecture_design.md` for the final architectural decisions and deployment view.
