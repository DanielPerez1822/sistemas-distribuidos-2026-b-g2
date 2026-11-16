<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       12-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 12

Reporting period: October 26–November 1, 2026 (America/Bogota).

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Extend Patients persistence with audit, messaging and controlled access.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-PAT-001 | Patient administrative management | doing | [DB #5](https://github.com/code-corhuila/dlc-patient-db/pull/5), [#6](https://github.com/code-corhuila/dlc-patient-db/pull/6), [#7](https://github.com/code-corhuila/dlc-patient-db/pull/7), [#8](https://github.com/code-corhuila/dlc-patient-db/pull/8), [#9](https://github.com/code-corhuila/dlc-patient-db/pull/9), [#10](https://github.com/code-corhuila/dlc-patient-db/pull/10), [#11](https://github.com/code-corhuila/dlc-patient-db/pull/11) |
| HU-BIL-001 | Procedure price catalog: review | doing | [Portal #102](https://github.com/code-corhuila/dlc-billing-portal/pull/102), [#105](https://github.com/code-corhuila/dlc-billing-portal/pull/105), [#106](https://github.com/code-corhuila/dlc-billing-portal/pull/106), [#107](https://github.com/code-corhuila/dlc-billing-portal/pull/107) |
| HU-BIL-002 | Invoice review and payment: review | doing | [Portal #86](https://github.com/code-corhuila/dlc-billing-portal/pull/86), [#101](https://github.com/code-corhuila/dlc-billing-portal/pull/101) |
| HU-BIL-004 | Manual charges: review | doing | [Portal #95](https://github.com/code-corhuila/dlc-billing-portal/pull/95) |

## 2. My individual contribution
- Added audit, idempotency, transactional outbox and durable deduplicated inbox storage; implemented restricted runtime access and environment bootstrap. Added durable deactivation operations. PR #11 reports a 33-migration local suite and disposable environment checks.

- Approved teammates’ Billing PRs covering PDF controls, payment navigation, manual charges and procedure-price HTTP integration; links are in the story table. Also approved [Docs #140](https://github.com/code-corhuila/dlc-docs/pull/140), recording Appointments persistence contracts. These are review contributions.

## 3. Blockers and risks
- Storage does not implement broker consumers or publishers; deactivation coordination and reconciliation remain pending. Disposable environment tests are not real deployment evidence.

## 4. Plan for next week
- Validate search, recovery and readiness; implement the API and coordinate deactivation.

## 5. Compliance self-check
- [ ] Conventional Commits - not independently verified for every commit.
- [ ] Per-environment HU branch + PR to that environment - complete promotion trail not verified.
- [ ] Testable acceptance criteria - complete story acceptance not independently verified.
- [x] Tests added/updated (unit / integration) - documented in the linked PRs, not rerun for this report.
- [ ] DDD / hexagonal boundaries respected (domain has no I/O) - complete story not independently audited.
- [ ] No secrets; config via environment variables - complete scope not independently audited.

## 6. Evidence links
- [HU-PAT-001 canonical story](https://github.com/code-corhuila/dlc-docs/issues/53).
- PR links above document the increments and reported validation; they do not by themselves establish final acceptance.
