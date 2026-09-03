# Service Contracts and MVP 1 Vertical Slice

## Data ownership

| Fact | Owner | Consumer access |
|---|---|---|
| Patient status | Clinical | `GET /api/v1/patients/{patientId}/status` |
| Dentist availability | Appointments | `GET /api/v1/dentists/{dentistId}/availability` |
| Procedure prices | Billing | Billing application port only |
| Appointment lifecycle | Appointments | Versioned API/events |
| Clinical procedure | Clinical | `ProcedureCompleted` v1 event |

No service reads another service's database.

## Synchronous contracts

### Patient validation

`GET /api/v1/patients/{patientId}/status`

- `200`: `{ "patientId": "...", "status": "ACTIVE" }`
- `404`: `{ "error": { "code": "PATIENT_NOT_FOUND", "message": "..." } }`
- `409`: `{ "error": { "code": "PATIENT_INACTIVE", "message": "..." } }`

### Create order analogue for Di Lucca: close attention

`POST /api/v1/clinical/appointments/{appointmentId}/completion`

Request: procedure codes, quantities, clinical extras, reason, author and `Idempotency-Key`.

- `202`: closure accepted and pending cross-context processing.
- `409`: appointment already completed or invalid lifecycle.
- `422`: missing clinical justification or invalid quantity.
- `503`: dependency unavailable; retry using the same idempotency key.

## Asynchronous contract

Event: `ProcedureCompleted.v1` is published from Clinical's outbox. Billing and Appointments consume it with inbox deduplication. The event contains identifiers and clinical facts only; it never contains a price.

## Anti-Corruption Layer

External email/provider payloads are translated at the Appointments adapter. Provider-specific fields such as `template_id` or `recipient_ref` cannot enter the domain model.

## MVP 1 vertical slice

1. Staff authenticates and receives verified claims.
2. Secretary selects an active patient and available dentist.
3. Appointments creates an appointment and returns its identifier.
4. Dentist records a minimal procedure through Clinical.
5. Clinical persists and publishes `ProcedureCompleted.v1`.
6. Billing resolves a price snapshot; Appointments and Billing expose pending/completed status.

References: [`user-stories.md`](../../../dlc-docs/04-requirements/user-stories.md), [`api-gateway.yaml`](../../../dlc-docs/07-api/contracts/openapi/api-gateway.yaml), and [`domain-events.md`](../../../dlc-docs/02-domain/domain-events.md).
