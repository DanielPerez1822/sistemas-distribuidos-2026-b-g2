# Architecture Decision: Modular Monolith First

- **Status:** Proposed for MVP 1
- **Date:** 2026-09-02
- **Scope:** Di Lucca MVP 1

## Context

The product has clear business contexts: IAM, Appointments, Clinical Care, and Billing. However, MVP 1 needs fast vertical delivery, shared operational visibility and a small team. Extracting every context immediately would add deployment, tracing, contract and reconciliation costs before those boundaries are proven.

Catalog-like read spikes are not currently part of the approved Di Lucca MVP scope. A future extraction must be triggered by measured independent scaling or deployment need, not by service count.

## Decision

Build MVP 1 as a modular monolith with explicit modules and ports. Preserve the bounded-context ownership defined in [`domain-map.md`](../../../dlc-docs/02-domain/domain-map.md). Keep Clinical persistence logically separate from IAM, Appointments and Billing, following [`ADR-002-polyglot-persistence.md`](../../../dlc-docs/05-architecture/decisions/ADR-002-polyglot-persistence.md).

The first extraction candidate is Clinical only if its workload, persistence needs or release cadence demonstrate independent scaling. Any extraction must retain its API/event contracts and create a new superseding ADR.

## Alternatives rejected

| Alternative | Reason rejected |
|---|---|
| Twelve microservices from day one | Operational complexity without evidence of independent scaling. |
| One unstructured monolith | Loses ownership, makes later extraction and testing harder. |
| Shared tables across modules | Creates hidden coupling and violates data ownership. |

## Consequences

- Positive: one deployable MVP with clear internal boundaries and a short feedback loop.
- Positive: domain and contract work remains reusable if a service is extracted.
- Negative: the runtime must prevent module-internal imports from bypassing ports.
- Negative: independent scaling is limited until a measured extraction occurs.

## Backlog slice

1. Define module ports for Clinical, Appointments and Billing.
2. Add architecture tests that reject direct access to another module's persistence.
3. Record extraction metrics: latency, throughput, deployment frequency and failure rate.
4. Revisit this decision after MVP 1 staging evidence.

## Traceability

- Product scope: [`product-backlog.md`](../../../dlc-docs/03-product/product-backlog.md)
- Architecture rule: [`hexagonal-architecture.md`](../../../dlc-docs/05-architecture/hexagonal-architecture.md)
- Requirements: [`user-stories.md`](../../../dlc-docs/04-requirements/user-stories.md)
