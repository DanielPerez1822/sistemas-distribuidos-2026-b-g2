<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       11-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 11

Reporting period: October 19–25, 2026 (America/Bogota).

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Establish the Patients database foundation.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-PAT-001 | Patient administrative management | doing | [DB #2](https://github.com/code-corhuila/dlc-patient-db/pull/2), [#3](https://github.com/code-corhuila/dlc-patient-db/pull/3), [#4](https://github.com/code-corhuila/dlc-patient-db/pull/4) |
| HU-BIL-002 | Invoice review and issuance: review | doing | [Billing portal #73](https://github.com/code-corhuila/dlc-billing-portal/pull/73) |

## 2. My individual contribution
- Prepared Liquibase migrations and CI, patient identity and document uniqueness, and emergency contacts with constraints and rollback. The PRs report local PostgreSQL verification.

- Approved a teammate’s invoice-detail HTTP read flow ([Billing portal #73](https://github.com/code-corhuila/dlc-billing-portal/pull/73)) and reviewed appointment-notification documentation ([Docs #110](https://github.com/code-corhuila/dlc-docs/pull/110)). These were reviews, not implementation authored here.

## 3. Blockers and risks
- Audit, idempotency, API authorization and integration remained pending. Local tests do not establish deployment or acceptance.

## 4. Plan for next week
- Implement audit, idempotency and reliable event storage; check CI and review.

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
