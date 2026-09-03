# MVP 1 Release and Retrospective

## Release definition

MVP 1 is released only when a versioned, running increment meets its acceptance criteria and can be deployed by someone outside the implementation team. This is aligned with [`definition-of-done.md`](../../../dlc-docs/00-governance/definition-of-done.md).

## Release checklist

| Check | Status | Evidence to attach |
|---|---|---|
| Acceptance criteria verified | pending | Acceptance test report |
| Unit and integration tests green | pending | CI run and coverage |
| Docker Compose starts the real databases | pending | Smoke-test log |
| Happy path and key error path verified | pending | API/e2e evidence |
| No secrets in repository or image | specified | `docker history`/secret scan |
| README, ADRs and contracts updated | done | [`containerization.md`](./containerization.md), [`mvp1-sprint-plan.md`](../04-week/hu-status/mvp1-sprint-plan.md) |
| Version tag and changelog created | pending | `v1.0.0` and CHANGELOG |

## Promotion flow

```text
develop -- HU branches and review --> qa -- integration/smoke --> main -- tag v1.0.0 --> registry
```

Promotion is blocked when tests are red, the container cannot reach its real database, or a required acceptance criterion is missing. An MVP reduces scope, not quality standards.

## Demo script

1. Start the stack with Compose.
2. Call `GET /health`.
3. Authenticate an authorized staff member.
4. Schedule an appointment for an active patient and dentist.
5. Show the persisted appointment after restarting the application container.
6. Show the conflict response for an overlapping appointment.
7. Point to the contract, ADR and test evidence.

## Retrospective

### Keep

- Walking skeleton and thin vertical slices.
- Explicit bounded-context ownership.
- Environment-specific branches and review.

### Drop

- Calling work released without runtime evidence.
- Large tasks that cannot be verified within a sprint.
- Configuration embedded in images.

### Try next corte

- Run contract tests in CI for API and events.
- Add image scanning and Compose smoke tests to the pipeline.
- Measure lead time, deployment frequency and failed deployment recovery.

## Current limitation

This report records the release activity and evidence plan. It does not claim that MVP 1 was executed locally because the application implementation and Docker configuration are outside the attached workspace.
