# MVP 2 Environment and Orchestration Plan

## Goal

Run the same Di Lucca artifact in `develop`, `qa` and `prod`, changing only environment configuration. This follows [`environments.md`](../../../dlc-docs/10-devops/environments.md) and the Week 06 activities.

## Environment matrix

| Environment | Purpose | Data | Required gate |
|---|---|---|---|
| `develop` | Fast integration and disposable feedback | Synthetic | Green CI, unit tests and build |
| `qa` | Production-like contract and integration testing | Synthetic/anonymized | Pact/contract tests, integration tests and smoke test |
| `prod` | Real users | Production data | Approved release, resolved conversations and rollback plan |

The image is built once and promoted. `DB_URL`, broker endpoints, log level, CORS origin and secrets are supplied by the target environment; they are never hard-coded in application code or Docker images.

## Orchestration requirements

1. Compose starts the gateway, IAM, Appointments, Clinical, Billing and their databases with health checks.
2. Services depend on readiness, not merely container start order.
3. PostgreSQL uses owned schemas for IAM, Appointments and Billing; Clinical uses its own MongoDB.
4. Persistent data uses named volumes; disposable service containers do not own state.
5. Startup fails clearly when a required environment variable is missing.
6. Service-to-service URLs use DNS service names, never fixed IP addresses or `localhost`.
7. Logs include `correlationId`, service name and environment without secrets.

## Branch and promotion record

The repository currently exposes only `main` and `origin/main`. No local or remote `develop`, `qa`, or HU child branches are available in this workspace. Therefore this document is a ready-to-implement plan, not evidence that promotion occurred.

Required flow when branches exist:

```text
feat/hu-xxx-orchestration -> PR develop
qa/hu-xxx-orchestration   -> PR qa       (Pact + integration checks)
release/2.0.0             -> PR main     (required approval: ariel5253)
```

Promotion must re-apply the validated commit with `cherry-pick -x`; direct `develop -> qa` or `qa -> main` merges are not the course policy.

## Acceptance criteria

- `docker compose config` resolves without secrets.
- Health checks prevent traffic before dependencies are ready.
- The same image digest is recorded for `develop`, `qa` and `prod`.
- Missing configuration fails at startup with a clear variable name.
- A QA deployment is blocked when contract or smoke tests fail.
