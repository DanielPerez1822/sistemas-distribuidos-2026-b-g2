<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       05-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 05

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: OdontoSys
- SPRINT_GOAL: Package and evaluate the MVP 1 increment as a reproducible, versioned release.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-DEVOPS-001 | Specify secure multi-stage containerization and Compose topology | done | [containerization.md](./containerization.md) |
| HU-REL-001 | Define the MVP 1 release checklist, demo and retrospective | done | [mvp1-release.md](./mvp1-release.md) |

## 2. My individual contribution
- Defined Docker image, Compose network, volume, environment configuration and health-check requirements.
- Prepared the MVP 1 release checklist, promotion flow, demo script and retrospective actions.

## 3. Blockers and risks
- Dockerfiles, Compose configuration and backend runtime are not present in this workspace; execution evidence remains pending.

## 4. Plan for next week
- Add CI smoke tests, image scanning and contract tests for the release pipeline.

## 5. Compliance self-check
- [x] Conventional Commits - `type(scope): summary`
- [x] Per-environment HU branch + PR to that environment (hu-xxx-dev -> develop, ...)
- [x] Testable acceptance criteria
- [ ] Tests added/updated (unit / integration) - runtime repository unavailable here
- [x] DDD / hexagonal boundaries respected (domain has no I/O)
- [x] No secrets; config via environment variables

## 6. Evidence links
- [containerization.md](./containerization.md)
- [mvp1-release.md](./mvp1-release.md)
- [Week 5 Session 1 activity](../../../distribuidos/05-week/01-session/index.html)
- [Week 5 Session 2 activity](../../../distribuidos/05-week/02-session/index.html)
- [definition-of-done.md](../../../dlc-docs/00-governance/definition-of-done.md)
