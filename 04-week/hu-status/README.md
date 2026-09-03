<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       04-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 04

- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca Dental Care & Technology
- SPRINT_GOAL: Implement and integrate a functional monolithic MVP of the Di Lucca system, covering the core workflows for authentication, patient management, appointment scheduling, clinical management, billing, and payments.

## 1. User stories worked this week

| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-IAM-001 | Staff authentication and authorized access | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-IAM-002 | Staff role management and authorization | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-CLN-001 | Patient registration and search | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-APT-001 | Appointment scheduling | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-APT-003 | Dentist calendar and appointment visualization | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-CLN-002 | Clinical history and care documentation | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-BIL-001 | Procedure base price management | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-BIL-002 | Invoice review and issuance | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-BIL-003 | Payment registration | doing | https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72 |
| HU-ARCH-004 | Define walking skeleton and MVP 1 sprint scope | done | [walking-skeleton.md](./walking-skeleton.md), [mvp1-sprint-plan.md](./mvp1-sprint-plan.md) |

## 2. My individual contribution

- Contributed to the implementation and integration of the functional Di Lucca monolithic MVP.
- Worked on connecting the main frontend and backend workflows required for the MVP.
- Supported the implementation of authentication and role-based access for clinic staff.
- Worked on patient management, including patient registration, search, and information management.
- Contributed to the appointment management workflow, including scheduling and appointment visualization.
- Supported the implementation of clinical information management required for dental care.
- Contributed to the billing workflow, including procedure prices, invoice information, and payment registration.
- Tested the integration between the main MVP modules to verify that the principal clinic workflow operates correctly in the monolithic application.
- Fixed integration and configuration issues found while running the complete application.
- Defined the walking skeleton, endpoint behavior, adapter substitution strategy and MVP 1 contract-first sprint scope.

## 3. Blockers and risks

- Integration between frontend and backend required adjustments to ensure that the main MVP workflows worked correctly.
- Some functionality still requires additional automated unit and integration tests before the related User Stories can be considered fully Done.
- Authorization and role restrictions need further validation to guarantee that each staff role can access only the appropriate system functions.
- The current implementation is focused on a functional monolithic MVP; therefore, architectural evolution toward distributed services must preserve the existing domain boundaries and business rules.
- Cross-context operations such as clinical attention closure, billing consistency, retries, and idempotency remain important risks that require further implementation and validation.
- The implementation repositories and runtime environment are not included in this workspace, so the walking skeleton cannot be claimed as executed here.

## 4. Plan for next week

- Complete validation of the functional monolithic MVP.
- Add and improve unit and integration tests for the implemented User Stories.
- Validate role-based authorization for the main system workflows.
- Improve error handling and input validation across frontend and backend.
- Review pending MVP User Stories and identify the functionality that still needs to be completed.
- Prepare the current monolithic implementation for the next architectural stage while preserving the Di Lucca domain boundaries.
- Update technical documentation and repository evidence according to the implemented functionality.
- Execute the walking skeleton against a real PostgreSQL container and attach test evidence.

## 5. Compliance self-check

- [x] Testable acceptance criteria
- [ ] Tests added/updated (unit / integration)
- [x] DDD / hexagonal boundaries respected (domain has no I/O)
- [x] No secrets; config via environment variables

## 6. Evidence links

- Di Lucca documentation repository: https://github.com/code-corhuila/dlc-docs
- Course repository: https://github.com/DanielPerez1822/sistemas-distribuidos-2026-b-g2
- Functional monolithic MVP repository: https://github.com/DanielPerez1822/di-lucca-mvp
- Main implementation commit/PR: https://github.com/DanielPerez1822/di-lucca-mvp/commit/df491e611504d08a2174e8209e8b3fa689466b72
- [walking-skeleton.md](./walking-skeleton.md)
- [mvp1-sprint-plan.md](./mvp1-sprint-plan.md)
- [Week 4 Session 1 activity](../../../distribuidos/04-week/01-session/index.html)
- [Week 4 Session 2 activity](../../../distribuidos/04-week/02-session/index.html)
- [definition-of-done.md](../../../dlc-docs/00-governance/definition-of-done.md)
