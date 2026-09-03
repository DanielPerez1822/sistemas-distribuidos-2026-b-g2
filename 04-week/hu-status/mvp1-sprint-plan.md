# MVP 1 Sprint Plan

## Sprint goal

A staff member can schedule a valid appointment for an active patient and dentist, and the service can demonstrate the first persisted vertical slice through a real database.

## Contract-first backlog

| Priority | Work item | Acceptance evidence | Points |
|---|---|---|---:|
| Must | `GET /health` | 200/503 behavior tested | 2 |
| Must | Appointment aggregate | overlap, active references and timezone rules tested | 5 |
| Must | `POST /api/v1/appointments` | 201, 409 and 422 contract tests | 5 |
| Must | PostgreSQL adapter + migration | integration test against container | 5 |
| Must | In-memory adapter | application tests run without infrastructure | 3 |
| Should | OpenAPI and README update | reviewed contract linked from service docs | 2 |
| Could | Frontend appointment form | demo only after Must items are green | 3 |
| Won't now | Payments and discounts | outside this sprint goal; remains backlog | 0 |

## Definition of Done

A story is complete only when acceptance criteria, unit/integration tests, review, documentation and staging smoke verification pass. The project checklist is [`definition-of-done.md`](../../../dlc-docs/00-governance/definition-of-done.md).

## Risks and mitigations

- **Database unavailable:** keep an in-memory adapter for fast tests and fail health explicitly.
- **Scope creep:** move payments, discounts and unrelated UI improvements to the backlog.
- **Contract drift:** update OpenAPI before implementation and run contract tests in CI.
- **Cross-context inconsistency:** keep care closure out of this first slice until its pending/retry states are implemented.

## Review checklist

- [ ] Branch follows the per-environment flow.
- [ ] Commit uses Conventional Commits.
- [ ] No secrets are committed; configuration uses environment variables.
- [ ] Domain has no I/O imports.
- [ ] Real database container and staging smoke test are green.
