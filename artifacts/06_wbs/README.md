# WBS Artifacts — tableorder

## Index

- [10_wbs.md](10_wbs.md) — 4-level Work Breakdown Structure covering phases, deliverables, work packages, activities, predecessors, and source traceability.
- [11_coverage_matrix.md](11_coverage_matrix.md) — Full traceability matrix from WBS work packages to scenarios, features, requirements, and components.
- [12_cost_matrix.md](12_cost_matrix.md) — Factor-based effort estimates for every work package, including phase, priority, and T-shirt breakdowns.

## Navigation Guide

1. Start with [10_wbs.md](10_wbs.md) to understand the execution sequence and decomposition.
2. Use [11_coverage_matrix.md](11_coverage_matrix.md) to verify which WBS items cover each scenario, feature, requirement, and component.
3. Use [12_cost_matrix.md](12_cost_matrix.md) to size work packages and plan staffing or iteration slices.
4. Follow the embedded links to jump from WBS IDs to upstream requirements and design artifacts.

## Key Stats

| metric | value |
|---|---|
| phases | 5 |
| deliverables | 12 |
| work_packages | 21 |
| activities | 63 |
| coverage_scenarios | 100% |
| coverage_features | 100% |
| coverage_requirements | 100% |
| coverage_components | 100% |
| total_man_days_min | 79 |
| total_man_days_max | 145 |
| total_man_days_typical | 116 |
| gaps | 0 |

## Notes

- The WBS assumes a greenfield delivery with Spring Boot, React + TypeScript, PostgreSQL, and Stripe.
- Foundation work is intentionally front-loaded in F1 to satisfy the greenfield and modular-monolith constraints before business feature implementation.
