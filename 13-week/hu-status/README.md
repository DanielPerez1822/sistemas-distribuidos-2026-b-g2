<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       13-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 13

Reporting period: November 2–8, 2026 (America/Bogota).

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Integrate Patients storage, API and portal and prepare QA promotion.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-PAT-001 | Patient administrative management | doing | [DB #16](https://github.com/code-corhuila/dlc-patient-db/pull/16), [API #12](https://github.com/code-corhuila/dlc-patient-api/pull/12), [#28](https://github.com/code-corhuila/dlc-patient-api/pull/28), [Portal #34](https://github.com/code-corhuila/dlc-patient-portal/pull/34), [#42](https://github.com/code-corhuila/dlc-patient-portal/pull/42) |
| HU-BIL-001 | Procedure prices: API review | doing | [Billing API #11](https://github.com/code-corhuila/dlc-billing-api/pull/11), [#12](https://github.com/code-corhuila/dlc-billing-api/pull/12), [#13](https://github.com/code-corhuila/dlc-billing-api/pull/13), [#14](https://github.com/code-corhuila/dlc-billing-api/pull/14) |
| HU-IAM-004 | Password recovery endpoint: review | doing | [IAM API #29](https://github.com/code-corhuila/dlc-iam-api/pull/29) |

## 2. My individual contribution
- Added search indexes, backup and restore checks, synthetic seeds and rollback-history validation ([DB #12](https://github.com/code-corhuila/dlc-patient-db/pull/12), [#13](https://github.com/code-corhuila/dlc-patient-db/pull/13), [#14](https://github.com/code-corhuila/dlc-patient-db/pull/14)). Built registration, search, read and update API increments and a deactivation recovery policy ([API #16](https://github.com/code-corhuila/dlc-patient-api/pull/16), [#20](https://github.com/code-corhuila/dlc-patient-api/pull/20), [#24](https://github.com/code-corhuila/dlc-patient-api/pull/24), [#28](https://github.com/code-corhuila/dlc-patient-api/pull/28)). Connected the portal to the API, removed demo fallback, prepared release 1.0.0 and QA promotion ([Portal #36](https://github.com/code-corhuila/dlc-patient-portal/pull/36), [#39](https://github.com/code-corhuila/dlc-patient-portal/pull/39), [#42](https://github.com/code-corhuila/dlc-patient-portal/pull/42)). Portal #42 reports 88 passing tests, eight packaging checks and a local stack GET returning 200.

- Aligned Patients documentation and contracts ([Docs #144](https://github.com/code-corhuila/dlc-docs/pull/144), [#145](https://github.com/code-corhuila/dlc-docs/pull/145), [#146](https://github.com/code-corhuila/dlc-docs/pull/146)); contributed PostgreSQL provisioning and CI checks ([Infra PostgreSQL #5](https://github.com/code-corhuila/dlc-infra-postgres/pull/5), [#6](https://github.com/code-corhuila/dlc-infra-postgres/pull/6)).
- Approved teammates’ Billing API price-query, JWT and route PRs, the IAM password-reset endpoint and [project operations documentation #162](https://github.com/code-corhuila/dlc-docs/pull/162). These are review contributions; the implementation belongs to their authors.

## 3. Blockers and risks
- GitHub Actions was reported blocked by the organization billing lock. Real IAM, coordinated deactivation, cross-service recovery and final acceptance still require evidence. Promotion PRs do not prove production deployment.

## 4. Plan for next week
- Resolve CI or agree an approved alternative, obtain review, and validate IAM and coordinated deactivation end to end.

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
