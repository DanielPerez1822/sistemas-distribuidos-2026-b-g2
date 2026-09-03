<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       02-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 02

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: OdontoSys
- SPRINT_GOAL: Choose a modular-monolith MVP architecture with explicit bounded contexts, ownership and extraction criteria.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-ARCH-001 | Record the modular-monolith-first architecture decision | done | [architecture-decision.md](./architecture-decision.md) |
| HU-ARCH-002 | Define bounded contexts, data ownership and MVP backlog | done | [context-map-and-backlog.md](./context-map-and-backlog.md) |

## 2. My individual contribution
- Proposed a modular monolith for MVP 1 while preserving IAM, Appointments, Clinical and Billing boundaries.
- Defined ownership, extraction triggers, backlog priorities and testable acceptance criteria.

## 3. Blockers and risks
- The architecture source repositories are not present in this workspace, so CI and runtime evidence remain pending.

## 4. Plan for next week
- Model the Patient/Clinical domain and define versioned service contracts.

## 5. Compliance self-check
- [ ] Conventional Commits - `type(scope): summary`
- [ ] Per-environment HU branch + PR to that environment (hu-xxx-dev -> develop, ...)
- [ ] Testable acceptance criteria
- [ ] Tests added/updated (unit / integration)
- [ ] DDD / hexagonal boundaries respected (domain has no I/O)
- [ ] No secrets; config via environment variables

## 6. Evidence links
- [architecture-decision.md](./architecture-decision.md)
- [context-map-and-backlog.md](./context-map-and-backlog.md)
- [Week 2 Session 1 activity](../../../distribuidos/02-week/01-session/index.html)
- [Week 2 Session 2 activity](../../../distribuidos/02-week/02-session/index.html)
- [domain-map.md](../../../dlc-docs/02-domain/domain-map.md)
