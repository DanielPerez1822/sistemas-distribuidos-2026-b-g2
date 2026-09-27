<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       08-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 08

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Refine Di Lucca's cross-service contracts and domain documentation, and prepare a dependency-aware MVP 2 story map.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-IAM-001 | Define staff authentication and authorization behavior | doing | [PR #24](https://github.com/code-corhuila/dlc-docs/pull/24) |
| HU-PAT-001 | Refine patient data, ownership, and access rules | doing | [PR #11](https://github.com/code-corhuila/dlc-docs/pull/11), [PR #24](https://github.com/code-corhuila/dlc-docs/pull/24) |
| HU-APT-001 | Refine the appointment service contract and review | doing | [PR #17](https://github.com/code-corhuila/dlc-docs/pull/17) |
| HU-CLN-002 | Document clinical care contracts and care-closure flow | doing | [PR #17](https://github.com/code-corhuila/dlc-docs/pull/17), [PR #23](https://github.com/code-corhuila/dlc-docs/pull/23) |
| HU-XCT-001 | Document idempotent care closure and cross-service outcomes | doing | [PR #23](https://github.com/code-corhuila/dlc-docs/pull/23) |
| HU-BIL-002 | Refine invoice and care/payment contract documentation | doing | [PR #17](https://github.com/code-corhuila/dlc-docs/pull/17), [PR #23](https://github.com/code-corhuila/dlc-docs/pull/23) |
| HU-BIL-003 | Refine payment and financial-history documentation | doing | [PR #17](https://github.com/code-corhuila/dlc-docs/pull/17), [PR #23](https://github.com/code-corhuila/dlc-docs/pull/23) |

These statuses record documentation work only. They do not mean the application stories are implemented, tested, or released.

## 2. My individual contribution
- Merged documentation updates in `dlc-docs`: data models and migration guidance (#11), appointment/care/payment API contracts (#17), care-closure and financial-history diagrams (#23), and security/authentication governance (#24).
- Prepared a draft MVP 2 story map from the product backlog; its estimates are not a team-approved commitment.
- Agile/DevOps work was not done this week and is not claimed here.

## 3. Blockers and risks
- The attached workspace has no service implementation or CI evidence for these proposed flows; this report does not claim runtime delivery or passing tests.
- No completed-sprint throughput/velocity is recorded. The 19-point scope is a planning proposal, not an approved team commitment; confirm it with planning poker and actual velocity.
- The Week 8 Session 1 Agile/DevOps activity was not worked on.

## 4. Plan for next week
- Validate the MVP 2 estimates with the team, compare scope with completed-sprint velocity, and record the agreed sprint goal and owners.
- Convert the selected cross-service slice into contract tests and implementation tasks, then attach CI/PR evidence as it becomes available.

## 5. Compliance self-check
- [x] Conventional Commits - merged documentation commits use `type(scope): summary`.
- [ ] Per-environment HU branch + PR to that environment - documentation PRs are evidenced; application environment promotion is not verified here.
- [x] Testable acceptance criteria - source stories and the proposed slice specify observable outcomes.
- [ ] Tests added/updated (unit / integration) - documentation-only evidence; no service tests were run or claimed.
- [x] DDD / hexagonal boundaries respected - contracts and diagrams preserve service ownership and bounded-context responsibilities.
- [x] No secrets; config via environment variables.

## 6. Evidence links
- [MVP 2 story map and candidate scope](./mvp2-story-map.md)
- [Week 8 Session 1 activity](../../../distribuidos/08-week/01-session/index.html)
- [Week 8 Session 2 activity](../../../distribuidos/08-week/02-session/index.html)
- [Merged PR #11 - data models](https://github.com/code-corhuila/dlc-docs/pull/11)
- [Merged PR #17 - appointments, care, and payments API contracts](https://github.com/code-corhuila/dlc-docs/pull/17)
- [Merged PR #23 - care closure and financial history diagrams](https://github.com/code-corhuila/dlc-docs/pull/23)
- [Merged PR #24 - security governance and authentication](https://github.com/code-corhuila/dlc-docs/pull/24)
