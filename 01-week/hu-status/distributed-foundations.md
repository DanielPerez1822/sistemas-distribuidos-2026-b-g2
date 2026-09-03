# Distributed Foundations Applied to Di Lucca

## Scope

This activity applies the Week 01 models to the Di Lucca Dental Care & Technology product. The canonical domain and ownership references are [`domain-map.md`](../../../dlc-docs/02-domain/domain-map.md), [`domain-events.md`](../../../dlc-docs/02-domain/domain-events.md), and [`ADR-002-polyglot-persistence.md`](../../../dlc-docs/05-architecture/decisions/ADR-002-polyglot-persistence.md).

## Decisions

| Concern | Decision | Reason |
|---|---|---|
| Clinical records | MongoDB owned by Clinical | Clinical records vary in shape and must remain inside the Clinical boundary. |
| IAM, Appointments, Billing | PostgreSQL schemas `iam`, `appointments`, `billing` | Strong transactional consistency is required for credentials, scheduling and money. |
| Care closure | Saga with explicit `pending`, `completed`, and `failed` states | MongoDB and PostgreSQL cannot share one local ACID transaction. |
| Event delivery | At-least-once plus inbox/idempotency key | Redelivery must not create duplicate charges or appointment updates. |
| Money and stock-like constraints | Strong consistency at the owning service | Financial balances and appointment overlap cannot tolerate stale writes. |
| Reports and analytics | Eventual consistency | A delayed descriptive view is preferable to coupling operational writes. |

## Failure path: close a dental attention

1. Clinical validates the dentist, appointment and procedure, then commits the clinical record and `ProcedureCompleted` in its MongoDB outbox transaction.
2. The publisher retries until the event is delivered with its stable `eventId` and `correlationId`.
3. Billing consumes once, resolves its own price rules, and stores an immutable charge snapshot.
4. Appointments consumes once and marks the attention complete.
5. A timeout or pricing failure leaves the process `pending` or `failed`; retry and reconciliation are visible and auditable.
6. Clinical never sends a price. Billing is the only owner of money.

## Causality and idempotency

Every event carries `eventId`, `occurredAt`, `aggregateId`, `correlationId`, and `schemaVersion`. Consumers persist `eventId` before applying the effect. A repeated delivery returns the previous result and does not create another charge, invoice item, or lifecycle transition.

## Applied self-check

- The system does not use wall-clock timestamps as a causal ordering mechanism.
- A network partition is handled with a pending state, not a distributed database lock.
- `ProcedureCompleted` is a past-tense integration event.
- Consistency is selected per operation rather than declared globally.

## Next verification

Implement the outbox/inbox behavior in the service repositories and add an acceptance test for safe retry, following the shared Definition of Done in [`definition-of-done.md`](../../../dlc-docs/00-governance/definition-of-done.md).
