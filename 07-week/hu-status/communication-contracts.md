# Service Communication and Contract Plan

## Communication choice

| Interaction | Mode | Contract | Reason |
|---|---|---|---|
| Staff to gateway | REST | OpenAPI `v1` | Immediate response and public tooling |
| Appointments to Clinical patient validation | REST | OpenAPI `v1` | Scheduling needs an immediate active/inactive decision |
| Clinical to Billing and Appointments | Async event | `ProcedureCompleted.v1` schema | Decouples care closure and supports retries |
| Internal fast, typed calls if measured necessary | gRPC | `.proto` version | Only when latency/throughput justifies the added operational cost |

## Contract rules

Every endpoint or event declares method/name, request, response, errors, version and correlation data. Errors use the standard envelope with `code`, `message`, `details` and `trace_id`. Times are ISO-8601 UTC and identifiers are UUIDs.

Compatible changes add optional fields. Removing, renaming or retyping a field requires a new API/event version. The old version is deprecated, announced and retired only after consumers migrate.

## Idempotency

`ProcedureCompleted.v1` includes `eventId`, `schemaVersion`, `aggregateId`, `correlationId` and `occurredAt`. Each consumer stores the event identifier in an inbox before applying its local effect. Redelivery returns the prior result and cannot create duplicate charges or appointment transitions.

## Contract testing flow

```text
Consumer test -> pact file -> producer verification in CI -> QA promotion
```

The producer build fails when it breaks a consumer expectation. Unit tests alone are insufficient because they cannot detect a response rename such as `available` to `qty`.

## Di Lucca contract examples

### Patient status

`GET /api/v1/patients/{patientId}/status`

- `200`: active/inactive status.
- `404`: `PATIENT_NOT_FOUND`.
- `409`: `PATIENT_INACTIVE`.

### Procedure completion

`ProcedureCompleted.v1` contains clinical identifiers, procedure codes, quantities and justified extras. Clinical does not publish prices; Billing resolves money from its own catalog.

## References

- [`07-api/README.md`](../../../dlc-docs/07-api/README.md)
- [`user-stories.md`](../../../dlc-docs/04-requirements/user-stories.md)
- [`testing-strategy.md`](../../../dlc-docs/11-quality/testing-strategy.md)
- [`domain-events.md`](../../../dlc-docs/02-domain/domain-events.md)
