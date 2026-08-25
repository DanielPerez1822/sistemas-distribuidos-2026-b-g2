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
| HU-XXX-001 | Document Patient Management bounded context in domain-map.md | done |  |
| HU-XXX-00 | Define Patient entity and business rules in entities-and-rules.md | done |  |
| HU-XXX-003 | Add Patient Management events to domain-events.md | done |  |

## 2. My individual contribution
Completed domain modeling for **Patient Management** bounded context:

- Added Patient Management to `domain-map.md` with Ubiquitous Language and context relationships
- Defined `Patient` aggregate and business rules (PAT-INV-001 to PAT-INV-010) in `entities-and-rules.md`
- Added 6 events to `domain-events.md`: `PatientRegistered`, `PatientProfileUpdated`, `EmergencyContactRemoved`, `PatientDeactivated`

## 3. Blockers and risks
- No blockers identified.

## 4. Plan for next week
- Continue with Appointments bounded context
- Sync with team on integration points

## 5. Compliance self-check
| Practice | Status |
|---|---|
| Conventional Commits | ✅ Done |
| HU branch + PR | ✅ Done |
| DDD / hexagonal boundaries | ✅ Done |

## 6. Evidence links
- https://github.com/code-corhuila/ods-docs/tree/main/01-context
- https://github.com/code-corhuila/ods-docs/tree/main/02-domain
