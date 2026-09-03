<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       03-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 03

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME:Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM:OdontoSys
- SPRINT_GOAL: Complete domain modeling for Patient Management bounded context and document domain events.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-DOM-001 | Model Patient and Clinical Care aggregates and invariants | done | [domain-model.md](./domain-model.md) |
| HU-DOM-002 | Define versioned contracts, ownership and the MVP 1 vertical slice | done | [service-contracts.md](./service-contracts.md) |

## 2. My individual contribution
Completed domain modeling for **Patient and Clinical Care** bounded context:

- Defined the ubiquitous language, aggregate boundaries and clinical invariants.
- Documented the hexagonal ports/adapters rule and the `ProcedureCompleted.v1` event shape.
- Defined synchronous patient validation, ownership constraints and the first vertical slice.

## 3. Blockers and risks
- No blockers identified.

## 4. Plan for next week
- Implement the contracts in the backend repositories and add unit, integration and contract tests.
- Sync with the team on `ProcedureCompleted` consumers and idempotency behavior.

## 5. Compliance self-check
| Practice | Status |
|---|---|
| Conventional Commits | ✅ Done |
| HU branch + PR | ✅ Done |
| DDD / hexagonal boundaries | ✅ Done |

## 6. Evidence links
- [domain-model.md](./domain-model.md)
- [service-contracts.md](./service-contracts.md)
- [Week 3 Session 1 activity](../../../distribuidos/03-week/01-session/index.html)
- [Week 3 Session 2 activity](../../../distribuidos/03-week/02-session/index.html)
- [domain-map.md](../../../dlc-docs/02-domain/domain-map.md)
- [user-stories.md](../../../dlc-docs/04-requirements/user-stories.md)
