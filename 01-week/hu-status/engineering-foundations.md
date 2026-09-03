# Engineering Foundations Delivery

## Repository and workflow agreement

The product is maintained as a documentation repository plus independent backend, database and frontend repositories. Work follows `develop -> qa -> main`; each HU uses an environment-specific branch and pull request. Commit examples:

- `docs(domain): record patient ownership rules`
- `feat(appointments): reject overlapping schedules`
- `test(billing): verify idempotent payment registration`

The weekly individual report is kept at `01-week/hu-status/README.md`, as required by the course material.

## Architecture rules

- Bounded contexts own their rules and data.
- Domain code contains no HTTP, ORM, MongoDB or PostgreSQL imports.
- Use cases orchestrate ports; adapters implement ports.
- Events are immutable, versioned and named in the past tense.
- Every cross-boundary change updates API/event/data documentation and receives an ADR review.

These rules align with [`hexagonal-architecture.md`](../../../dlc-docs/05-architecture/hexagonal-architecture.md) and the team's [`definition-of-done.md`](../../../dlc-docs/00-governance/definition-of-done.md).

## Quality plan

| Layer | Evidence required |
|---|---|
| Domain | Unit tests for invariants and aggregate transitions |
| Adapter | Integration tests against real persistence or a container |
| Contract | OpenAPI/event contract tests for each changed boundary |
| Workflow | End-to-end test for the staff flow under test |
| Delivery | CI, staging smoke test, review and updated documentation |

## Individual contribution

I translated the course foundations into concrete rules for Di Lucca, documented the failure-first care-closure path, and connected the weekly work to the canonical architecture, domain and quality documents. Implementation evidence remains pending until the backend repositories are available in this workspace.
