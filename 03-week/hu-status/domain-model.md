# Patient and Clinical Domain Model

## Ubiquitous language

- **Patient:** active or deactivated person receiving care; no login account.
- **ClinicalRecord:** longitudinal record owned by Clinical.
- **Consultation:** a dentist-authored encounter note.
- **Procedure:** performed care linked to an appointment.
- **Evolution:** immutable historical progress entry.
- **Additional clinical need:** material or extra requirement identified by the dentist; it contains no monetary value.

## Aggregate boundaries

`Patient` protects identity uniqueness and lifecycle. `ClinicalRecord` protects the ordered history of consultations, diagnoses, treatments and procedures. A procedure may reference `appointmentId`, but Appointments remains the owner of appointment state.

## Invariants

1. A patient document identifier is unique.
2. A deactivated patient cannot be scheduled for a new appointment.
3. Only an authorized dentist can author clinical content.
4. A clinical procedure requires an appointment correlation and author.
5. Amendments preserve the previous clinical history; they do not overwrite it silently.
6. Additional needs contain code/type, quantity and clinical reason, never price.
7. Procedure completion is emitted once per idempotency key.

## Ports and adapters

```text
adapters/in/http       -> application -> domain <- ports/out <- adapters/out/mongodb
adapters/in/messaging  -> application                    <- adapters/out/event-publisher
```

The domain must remain free of HTTP, MongoDB, ORM and framework imports. This follows [`hexagonal-architecture.md`](../../../dlc-docs/05-architecture/hexagonal-architecture.md).

## Domain event

`ProcedureCompleted` is immutable and past-tense. Minimum payload:

```json
{
  "eventId": "evt-uuid",
  "schemaVersion": 1,
  "appointmentId": "apt-uuid",
  "patientId": "pat-uuid",
  "procedureId": "proc-uuid",
  "items": [{"code": "CLEANING", "quantity": 1}],
  "extras": [{"code": "MATERIAL-X", "quantity": 2, "reason": "clinical need"}],
  "occurredAt": "2026-09-02T12:00:00Z",
  "correlationId": "corr-uuid"
}
```

Billing resolves all prices from its own versioned catalog. The event must not contain `unitPrice`, `total` or any other financial value.
