<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       01-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 01

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: OdontoSys
- SPRINT_GOAL: Apply distributed-systems failure, consistency and engineering foundations to the Di Lucca product.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-FOUND-001 | Apply consistency, failure and idempotency decisions to care closure | done | [distributed-foundations.md](./distributed-foundations.md) |
| HU-FOUND-002 | Document engineering workflow, architecture boundaries and quality gates | done | [engineering-foundations.md](./engineering-foundations.md) |
| HU-FOUND-003 | Compare Scrum and Kanban for the team's delivery flow | done | [Scrum-Kanban.md](./Scrum-Kanban.md) |

## 2. My individual contribution
- Applied CAP/PACELC, at-least-once delivery, idempotency, Saga and outbox decisions to the care-closure scenario.
- Documented the repository workflow, hexagonal boundary rules and test pyramid for the individual delivery.

## 3. Blockers and risks
- Backend implementation evidence is not available in this workspace; outbox/inbox behavior remains a follow-up risk.

## 4. Plan for next week
- Create the architecture decision and bounded-context backlog for the MVP.

## 5. Compliance self-check
- [ ] Conventional Commits - `type(scope): summary`
- [ ] Per-environment HU branch + PR to that environment (hu-xxx-dev -> develop, ...)
- [ ] Testable acceptance criteria
- [ ] Tests added/updated (unit / integration)
- [ ] DDD / hexagonal boundaries respected (domain has no I/O)
- [ ] No secrets; config via environment variables

## 6. Evidence links
- [distributed-foundations.md](./distributed-foundations.md)
- [engineering-foundations.md](./engineering-foundations.md)
- [Week 1 Session 1 activity](../../../distribuidos/01-week/01-session/index.html)
- [Week 1 Session 2 activity](../../../distribuidos/01-week/02-session/index.html)
- [definition-of-done.md](../../../dlc-docs/00-governance/definition-of-done.md)
