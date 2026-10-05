<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       09-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 09

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Align Auth and Gateway contracts and prepare a secure configuration and progressive-delivery plan for MVP 2.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-IAM-001 | Align staff authentication behavior and the Auth/Gateway contract | doing | [PR #37](https://github.com/code-corhuila/dlc-docs/pull/37), [PR #41](https://github.com/code-corhuila/dlc-docs/pull/41) |
| HU-IAM-006 | Align refresh-token/session data and Auth operational guidance | doing | [PR #41](https://github.com/code-corhuila/dlc-docs/pull/41) |

The statuses above describe documentation and contract work only. Neither HU is claimed as implemented, tested, or released by these documentation PRs.

## 2. My individual contribution
- Merged [PR #37](https://github.com/code-corhuila/dlc-docs/pull/37), aligning the Auth and API Gateway contracts, service guidance, startup diagram, and runbooks.
- Merged [PR #41](https://github.com/code-corhuila/dlc-docs/pull/41), aligning Auth/Gateway data models, decisions, runbooks, and the Clinical service overview.
- Merged [PR #42](https://github.com/code-corhuila/dlc-docs/pull/42), aligning shared data-model terminology. This is cross-cutting documentation, not a separate user story.
- Completed the Week 9 planning activity in [secure-config-rollout-plan.md](./secure-config-rollout-plan.md). It records the current app baseline and the pending hardening work; it does not claim those pending controls are deployed.

## 3. Blockers and risks
- In the current app repository, `.env.example`, `.gitignore`, and Compose-required `POSTGRES_PASSWORD`/`JWT_SECRET` are present; a pre-commit secret scanner and feature-flag control are not.
- `JWT_SECRET` is required by Spring configuration and the JWT library rejects weak keys, but the app does not yet provide a project-specific startup-validation message.
- No application implementation or rollout PR for the proposed flag, secret rotation, or canary is included in this week's GitHub evidence.

## 4. Plan for next week
- Refine and approve the technical hardening tasks in [secure-config-rollout-plan.md](./secure-config-rollout-plan.md), then implement them in the application repository with tests.
- Keep the invoice-email flag off until the canary recipient controls, monitoring, and rollback have been verified in a non-production environment.

## 5. Compliance self-check
- [x] Conventional Commits - the merged documentation changes use `docs:` commit messages.
- [ ] Per-environment HU branch + PR to that environment - documentation PRs are evidenced; application promotion is not verified.
- [x] Testable acceptance criteria - the proposed hardening tasks include observable acceptance checks.
- [ ] Tests added/updated (unit / integration) - no application tests were added as part of the merged documentation PRs.
- [x] DDD / hexagonal boundaries respected - the Auth/Gateway contracts preserve service ownership.
- [x] No secrets; config via environment variables - the plan uses placeholders and environment-based injection only.

## 6. Evidence links
- [Week 9 Session 1 activity](../../../distribuidos/09-week/01-session/index.html)
- [Week 9 Session 2 activity](../../../distribuidos/09-week/02-session/index.html)
- [Secure configuration and progressive-delivery plan](./secure-config-rollout-plan.md)
- [PR #37 - Auth and Gateway contracts](https://github.com/code-corhuila/dlc-docs/pull/37)
- [PR #41 - Auth and Gateway service alignment](https://github.com/code-corhuila/dlc-docs/pull/41)
- [PR #42 - common data-model alignment](https://github.com/code-corhuila/dlc-docs/pull/42)
