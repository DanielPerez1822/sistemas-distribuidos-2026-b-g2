# MVP 2 Orchestration Backlog

| Priority | User story | Acceptance criteria | Status |
|---|---|---|---|
| Must | Start all services with one Compose command | Health checks, named volumes and service-name DNS work | doing |
| Must | Externalize configuration | Required variables validated; no secrets committed | doing |
| Must | Promote the same artifact to QA | Image digest is unchanged; QA config is injected | todo |
| Must | Map branch to environment | Child PRs target the correct parent branch | todo |
| Should | Add environment smoke tests | `/health` and one business path run in QA | todo |
| Could | Add deployment metrics | Lead time and rollback time are recorded | todo |

## Approved baseline

MVP 1 documentation was accepted on `main` through the existing history up to commit `59d8d77` (`docs: add week 5 reports for containerization and MVP1 release`). This is baseline evidence only; it does not approve the new MVP 2 stories.

## Risks

- Branches required by the policy are absent from the checked-out repository.
- No Compose or service implementation is present in the attached G2 workspace.
- Configuration drift can make QA differ from production if variable names are not centralized.

## References

- [`branching-policy.md`](../../../dlc-docs/00-governance/branching-policy.md)
- [`environments.md`](../../../dlc-docs/10-devops/environments.md)
- [`local-setup.md`](../../../dlc-docs/10-devops/local-setup.md)
