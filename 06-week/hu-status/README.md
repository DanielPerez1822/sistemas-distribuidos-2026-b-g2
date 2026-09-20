<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       06-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 06

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Define reproducible environments, secure configuration and MVP 2 orchestration.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-OPS-001 | Define environment, configuration and orchestration requirements | doing | [environment-orchestration.md](./environment-orchestration.md) |
| HU-OPS-002 | Slice the MVP 2 orchestration backlog | doing | [mvp2-backlog.md](./mvp2-backlog.md) |

## 2. My individual contribution
- Documented the develop/qa/prod matrix, same-artifact promotion, health checks, volumes and 12-factor configuration.
- Mapped the required branch and approval flow for future MVP 2 promotion.

## 3. Blockers and risks
- G2 currently contains only `main` and `origin/main`; required environment and HU branches are not available locally.
- Compose and service implementation files are not present, so runtime promotion cannot be claimed.

## 4. Plan for next week
- Implement Compose health checks and environment validation, then open the child PR for `develop`.

## 5. Compliance self-check
- [x] Conventional Commits - `type(scope): summary`
- [ ] Per-environment HU branch + PR to that environment - branches unavailable in this workspace
- [x] Testable acceptance criteria
- [ ] Tests added/updated (unit / integration) - implementation repository unavailable here
- [x] DDD / hexagonal boundaries respected (domain has no I/O)
- [x] No secrets; config via environment variables

## 6. Evidence links
- [environment-orchestration.md](./environment-orchestration.md)
- [mvp2-backlog.md](./mvp2-backlog.md)
- [Week 6 Session 1 activity](../../../distribuidos/06-week/01-session/index.html)
- [Week 6 Session 2 activity](../../../distribuidos/06-week/02-session/index.html)
- [branching-policy.md](../../../dlc-docs/00-governance/branching-policy.md)
