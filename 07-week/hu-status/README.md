<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       07-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 07

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Establish versioned service contracts and contract-testing gates for MVP 2.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-API-001 | Define REST and event communication contracts for Di Lucca | doing | [communication-contracts.md](./communication-contracts.md) |
| HU-API-002 | Plan consumer-driven contract tests and compatibility gates | doing | [contract-test-backlog.md](./contract-test-backlog.md) |

## 2. My individual contribution
- Defined REST versus asynchronous event choices, versioning rules, error envelopes and idempotency fields.
- Prepared the consumer Pact, producer verification and duplicate-event testing backlog.

## 3. Blockers and risks
- No week 7 branch or PR is present in the local repository; these stories are not approved for promotion.
- Service source, Pact broker and CI workflow are not included in the attached workspace.

## 4. Plan for next week
- Add the OpenAPI/event schemas and open the child PR to `develop`, then promote through QA only after Pact passes.

## 5. Compliance self-check
- [x] Conventional Commits - `type(scope): summary`
- [ ] Per-environment HU branch + PR to that environment - branches unavailable in this workspace
- [x] Testable acceptance criteria
- [ ] Tests added/updated (unit / integration) - service source unavailable here
- [x] DDD / hexagonal boundaries respected (domain has no I/O)
- [x] No secrets; config via environment variables

## 6. Evidence links
- [communication-contracts.md](./communication-contracts.md)
- [contract-test-backlog.md](./contract-test-backlog.md)
- [Week 7 Session 1 activity](../../../distribuidos/07-week/01-session/index.html)
- [Week 7 Session 2 activity](../../../distribuidos/07-week/02-session/index.html)
- [branching-policy.md](../../../dlc-docs/00-governance/branching-policy.md)
- [testing-strategy.md](../../../dlc-docs/11-quality/testing-strategy.md)
