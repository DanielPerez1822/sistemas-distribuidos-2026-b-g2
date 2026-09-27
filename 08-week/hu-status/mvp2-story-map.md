# Week 08 - MVP 2 Story Map and Candidate Commitment

## Goal

Plan a thin, end-to-end Di Lucca slice that moves from an authorized staff member to a persisted appointment and clinical outcome, with the care-closure event reconciled across service boundaries. The existing [product backlog](../../../dlc-docs/03-product/product-backlog.md) and [user-story acceptance criteria](../../../dlc-docs/04-requirements/user-stories.md) remain authoritative; estimates below are planning inputs, not approved implementation status.

## Story map

| User journey | Candidate story / slice | Estimate | Dependency or contract |
|---|---|---:|---|
| Access the clinic | `HU-IAM-001`: authenticate active, verified staff and enforce role access | 2 SP | Auth contract and authorization rules |
| Select the visit context | Use an existing active patient and dentist; defer full patient administration | 1 SP | Seeded/known IDs and patient ownership rules |
| Schedule the visit | `HU-APT-001`: persist a valid appointment and reject overlapping or invalid references | 3 SP | Patients ownership contract; appointment API and clinic timezone |
| Record the clinical work | `HU-CLN-002`: persist consultation, diagnosis, treatment, procedure, author, and time | 5 SP | Appointment ID; Clinical service owns clinical narrative |
| Publish care closure | First `HU-XCT-001` slice: persist the clinical change and its outbox event atomically | 3 SP | Event schema, idempotency key, MongoDB transaction/outbox behavior |
| Reconcile service outcomes | Second `HU-XCT-001` slice: consume closure idempotently in Appointments and Billing; expose pending/failure and retry state | 5 SP | Consumer contracts, PostgreSQL persistence, retry/reconciliation evidence |
| Issue invoice and record payment | `HU-BIL-002` and `HU-BIL-003` | Later slice | Depends on reliable care closure and invoice rules; outside this candidate commitment |

The proposed release line is after **Reconcile service outcomes**: $2 + 1 + 3 + 5 + 3 + 5 = 19$ SP. Invoice issuance and payments remain below the line. The lookup estimate covers using existing data only; patient registration, notification, analytics, and real payment processing are not included.

## Cross-service dependency order

1. Confirm identity, patient ownership, event, appointment, and billing contracts before parallel implementation. Provide mocks for consumers or producers that are not ready.
2. Make patient and dentist references available before appointment creation; test the clinic timezone and overlap rules at the appointment boundary.
3. Persist clinical work and the outbox event together. Do not publish a success state if either write fails.
4. Make each consumer idempotent and retain a visible pending/failure state. Verify retry and reconciliation without duplicating appointment or billing outcomes.
5. Keep clinical narrative in the Clinical context; Billing receives only the financial facts required to calculate and explain a charge.

## Candidate acceptance evidence

- Authorized staff can authenticate; inactive, invalid, or locked identities are rejected, and patient accounts are not introduced.
- An appointment is stored for an active patient and dentist, while invalid references and overlapping times return the documented errors.
- The clinical record retains its author, timestamp, and required clinical fields; amendments do not erase history.
- A care-closure write either persists both the clinical change and outbox record or persists neither.
- Replaying a closure event does not duplicate downstream outcomes; a failed consumer remains observable and can be retried/reconciled.
- API and event contract tests, persistence integration tests, and a smoke test cover the slice before release. These are acceptance requirements, not tests executed by this documentation task.

## Estimation and commitment

The 19 SP total uses a Fibonacci-style scale and splits the 8-point cross-context story into two smaller slices. Estimates are provisional and must be revised in team planning poker.

The [Week 4 MVP 1 plan](../../04-week/hu-status/mvp1-sprint-plan.md) totals 20 SP for its planned Must items, but it does not report completed-sprint velocity. Treat 20 SP only as a historical planning reference, not measured capacity. The candidate 19 SP scope is therefore **not a final team commitment** until the team checks completed-sprint throughput, availability, and dependencies. If measured capacity is lower, drop or defer scope rather than exceed it.

The separate [MVP 2 orchestration backlog](../../06-week/hu-status/mvp2-backlog.md) still has Compose health checks, secure configuration, artifact promotion, and environment-branch mapping in progress or todo. Their implementation and verification must be sequenced with this product slice; this story map does not mark them complete.

## DLC documentation merged this week

These merges provide the documentation baseline for the story map. They are documentation evidence, not proof that the services or flows have been implemented.

| PR | Merged contribution | Related documentation |
|---|---|---|
| [#11](https://github.com/code-corhuila/dlc-docs/pull/11) | Refined data dictionary, models, modeling conventions, normalization assessment, and migration strategy | [Data models](../../../dlc-docs/06-data/models.md), [migration strategy](../../../dlc-docs/06-data/migration-strategy.md) |
| [#17](https://github.com/code-corhuila/dlc-docs/pull/17) | Added appointment and care/payment contract reviews; refined OpenAPI service contracts | [Appointment review](../../../dlc-docs/07-api/contract-reviews/appointments.md), [care and payments review](../../../dlc-docs/07-api/contract-reviews/care-and-payments.md) |
| [#23](https://github.com/code-corhuila/dlc-docs/pull/23) | Added care-closure sequence and financial-history snapshot diagrams | [Care closure sequence](../../../dlc-docs/08-diagrams/diagrams/09-care-closure-sequence.puml), [financial history](../../../dlc-docs/08-diagrams/diagrams/13-financial-history-snapshots.puml) |
| [#24](https://github.com/code-corhuila/dlc-docs/pull/24) | Formalized security governance, authentication, authorization, and related API/context documentation | [Authentication](../../../dlc-docs/07-api/authentication.md), [security rules](../../../dlc-docs/00-governance/security-rules.md) |

## References

- [Session 2 - Story mapping, estimation, and MVP 2 commitment](../../../distribuidos/08-week/02-session/index.html)
- [Product backlog](../../../dlc-docs/03-product/product-backlog.md)
- [User stories and acceptance criteria](../../../dlc-docs/04-requirements/user-stories.md)
- [MVP 2 orchestration backlog](../../06-week/hu-status/mvp2-backlog.md)