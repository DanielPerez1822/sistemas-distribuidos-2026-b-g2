# Context Map and Architecture Backlog

## Context map

```text
IAM -- verified claims --> Appointments -- lifecycle --> Clinical
 |                            |                         |
 +--------------------------> Billing <--- ProcedureCompleted

Clinical owns patient and care data.
Appointments owns schedules and appointment state.
Billing owns prices, invoices and payments.
No context reads another context's tables.
```

| Context | Owns | Exposes |
|---|---|---|
| IAM | staff, roles, sessions | verified identity and authorization claims |
| Appointments | availability, appointments, reminders | schedule and lifecycle contracts |
| Clinical | patient profiles, histories, procedures | patient validation and `ProcedureCompleted` |
| Billing | prices, charges, invoices, payments | financial state and payment outcomes |

## Sprint backlog

| Priority | Story | Acceptance criteria | Estimate |
|---|---|---|---:|
| Must | Isolate Clinical behind an application port | No module imports Clinical persistence; unit and architecture tests pass | 5 |
| Must | Define `ProcedureCompleted` v1 | Required identifiers, schema version, correlation and idempotency fields documented | 3 |
| Must | Define patient validation contract | Active patient response and explicit not-found/inactive errors | 3 |
| Should | Add contract fixtures | Consumer and provider fixtures run in CI | 3 |
| Could | Measure extraction trigger | Dashboard records independent load and deployment metrics | 2 |
| Won't for MVP 1 | Split every context into deployable services | Reconsider only after measured need and a new ADR | 0 |

## Decision rule

The team accepts a service extraction only when both conditions are demonstrated: a real bounded context with independent data ownership, and a measured need for independent scaling or deployment. This prevents a distributed monolith.

## Evidence references

- [`domain-map.md`](../../../dlc-docs/02-domain/domain-map.md)
- [`product-backlog.md`](../../../dlc-docs/03-product/product-backlog.md)
- [`ADR-002-polyglot-persistence.md`](../../../dlc-docs/05-architecture/decisions/ADR-002-polyglot-persistence.md)
