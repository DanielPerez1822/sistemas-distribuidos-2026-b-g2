# Walking Skeleton Specification

## Goal

Prove one runnable path through HTTP, application, domain, persistence and container configuration before adding the complete MVP. The structure follows [`hexagonal-architecture.md`](../../../dlc-docs/05-architecture/hexagonal-architecture.md).

```text
adapters/in/http/HealthController
        -> application/HealthUseCase
        -> domain/ServiceStatus
        -> ports/out/HealthRepository
        -> adapters/out/persistence/PostgresHealthRepository
```

## Required endpoints

### `GET /health`

- `200`: `{ "status": "ok", "service": "di-lucca-mvp", "timestamp": "..." }`
- `503`: same shape with `status: "degraded"` when the database is unavailable.
- No authentication required.

### `POST /api/v1/appointments`

Request: active `patientId`, active `dentistId`, start/end in the clinic timezone and location.

- `201`: persisted appointment identifier and `SCHEDULED` status.
- `409`: overlapping appointment or inactive patient/dentist.
- `422`: invalid time range or missing timezone.

## Adapter substitution

Production uses `PostgresAppointmentRepository`; tests use `InMemoryAppointmentRepository` behind the same output port. The composition root selects the implementation. No use case constructs a concrete database adapter.

## Verification matrix

| Test | Proof |
|---|---|
| Unit | Appointment rejects overlap and invalid lifecycle |
| Integration | PostgreSQL repository persists and reads an appointment |
| Contract | OpenAPI examples match `201`, `409` and `422` |
| E2E | Container starts with PostgreSQL and completes the HTTP path |
| Smoke | `/health` reports database status |

The implementation is pending because application source repositories are not present in this workspace; this file is the build-ready contract rather than a claim of runtime execution.
