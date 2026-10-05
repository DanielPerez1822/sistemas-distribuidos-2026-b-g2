# Week 09 - Secure Configuration and Progressive Delivery Plan

## Goal

Prepare a verifiable MVP 2 hardening plan for configuration, secret handling, feature flags, canary rollout, and rollback. This is a planning deliverable; the pending work below is not represented as implemented or deployed.

## Current application baseline

| Control | Observed baseline | Week 9 outcome |
|---|---|---|
| Local configuration | `.env.example` documents PostgreSQL, JWT, ports, CORS, and optional SMTP values; `.env` is ignored by Git. | Keep local values in `.env`; never commit real credentials. |
| Required configuration | Compose requires `POSTGRES_PASSWORD` and `JWT_SECRET`; Spring requires `JWT_SECRET`. | Add an explicit startup validator with a safe error that names the missing/invalid variable but never prints its value. |
| JWT key strength | The token provider uses the HMAC key utility, which rejects keys shorter than 32 bytes. | Add a direct test and actionable validation message before accepting traffic. |
| Secret scanning | No pre-commit secret scanner is configured in the app repository. | Add the pinned Gitleaks hook and run it on the full repository before merge. |
| Feature flags | No application feature-flag setting currently exists. | Add `FEATURE_INVOICE_EMAIL_ENABLED`, default `false`, before enabling invoice email in any environment. |

## Secret ownership and rotation

The owners and cadence below are proposals for team approval. Secret values must be unique per environment and injected at runtime from the deployment secret store; they must not appear in Git, Docker build arguments, logs, screenshots, or this document.

| Secret | Accountable owner | Storage and injection | Rotation proposal | Verification |
|---|---|---|---|---|
| `JWT_SECRET` | Auth/security owner | Environment-specific deployment secret store; inject into the backend at runtime. Local development uses a generated value in ignored `.env`. | Every 90 days and immediately after suspected exposure. Coordinate rotation with token expiry/re-authentication because current signing uses one key. | Startup rejects missing or under-32-byte values without logging the value; login and token verification pass after rotation. |
| `POSTGRES_PASSWORD` | Database/platform owner | Environment-specific secret store; Compose injects it into backend and PostgreSQL. Local development uses ignored `.env`. | Every 90 days and immediately after suspected exposure; rotate the database credential and service secret as one change. | Backend health check succeeds with the new value; old credential fails; no secret appears in logs. |
| `MAIL_PASSWORD` | Messaging/operations owner | Secret store for deployed environments; inject only into the backend. Leave unset in local development unless using a controlled SMTP sandbox. | Every 90 days and immediately after suspected exposure or provider-user changes. | Sandbox delivery succeeds after rotation; the application starts when optional mail is unset. |

### Secret-handling controls

- Keep `.env` ignored and `.env.example` limited to variable names and unmistakable placeholders.
- Configure a pre-commit hook with a pinned Gitleaks release and require the same scan in CI before merge. Developers install the hook with `pre-commit install`; run `pre-commit run --all-files` to scan existing tracked content.
- If a secret is detected after commit, revoke/rotate it first. Removing it from the latest file is not sufficient because Git history retains it.
- Fail startup on missing or malformed required configuration. Error messages may name a variable, but must never include its value.

## Feature-flag policy

| Rule | Proposed policy |
|---|---|
| Flag | `FEATURE_INVOICE_EMAIL_ENABLED` |
| Owner | Billing capability owner; operations can disable it during an incident. |
| Default | `false` in code, Compose, and new environments. |
| Scope | Invoice receipt email only; password-reset and appointment notifications are not controlled by this flag. |
| Rollout | Enable in a sandbox-backed non-production environment first. Production stays off until the canary recipient restriction and data-minimization review are approved. |
| Removal | Review after two successful release cycles; remove the flag and fallback path once the capability is stable and the team approves cleanup. |

The application currently has no recipient-cohort flag. A boolean environment flag alone cannot safely target a percentage of patients; do not describe it as percentage-based canary support until targeting is implemented.

## Canary and rollback

1. Deploy the same tested artifact with invoice email disabled. Verify health, required configuration, and the ordinary invoice workflow.
2. In a non-production environment, enable the flag against an SMTP sandbox with synthetic patient records. Verify the message contains only approved financial data and no clinical narrative.
3. Before any production pilot, implement and approve a recipient allowlist or equivalent cohort control. Start with a small, explicitly approved test cohort; do not enable the global flag for all patient recipients as a canary.
4. Observe delivery success/failure, application errors, and support reports for at least 30 minutes and the first five pilot receipts. Proceed only with no secret exposure, no duplicate receipts, no unexpected data, and no material error increase from the pre-canary baseline.
5. If a stop condition is met, set `FEATURE_INVOICE_EMAIL_ENABLED=false`, verify subsequent requests do not send receipts, and record the incident and affected invoice IDs for follow-up.

Rollback is a flag/configuration change, not a database rollback. An already-sent email cannot be recalled; notify the operations owner and follow the incident process if a message was sent incorrectly.

## Proposed technical tasks and acceptance criteria

These are technical work items, not approved product HUs; no new HU identifiers are assigned here.

| Work item | Testable acceptance criteria | State |
|---|---|---|
| Validate startup configuration | Missing `JWT_SECRET` or database credentials prevent startup; a JWT secret below 32 UTF-8 bytes fails with an actionable message; logs never contain the provided value. | Existing required-variable behavior is partial; explicit validation/tests remain pending. |
| Add secret scanning | A pinned Gitleaks pre-commit hook and CI check scan tracked files; a synthetic known test secret fails the check; `.env` remains ignored. | Pending. |
| Add invoice-email feature flag | Flag defaults off; when off, the invoice-email capability does not deliver messages; when on, a sandbox test proves the intended path; unrelated auth and appointment email behavior is unchanged. | Pending. |
| Gate a pilot and rollback | The canary is restricted to an approved cohort; the stop conditions are observable; disabling the flag stops subsequent delivery within one minute; test evidence and operator steps are attached to the PR. | Pending. |

## References

- [Week 9 Session 1 - Configuration, secrets, and feature flags](../../../distribuidos/09-week/01-session/index.html)
- [Week 9 Session 2 - Secure configuration and progressive delivery](../../../distribuidos/09-week/02-session/index.html)
- [Di Lucca `.env.example`](../../../di-lucca/.env.example)
- [Di Lucca Compose configuration](../../../di-lucca/docker-compose.yml)
- [Auth/Gateway contract PR #37](https://github.com/code-corhuila/dlc-docs/pull/37)
- [Auth service alignment PR #41](https://github.com/code-corhuila/dlc-docs/pull/41)
- [Shared data model PR #42](https://github.com/code-corhuila/dlc-docs/pull/42)