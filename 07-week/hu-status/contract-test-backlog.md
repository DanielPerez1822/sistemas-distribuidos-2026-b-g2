# Contract Testing Backlog

| Priority | Work item | Gate | Status |
|---|---|---|---|
| Must | Add OpenAPI contract for patient status | Request/response/error schemas validate | doing |
| Must | Add Pact consumer for Appointments -> Clinical | Pact file published from consumer CI | todo |
| Must | Verify Clinical producer against Pact | Producer build fails on incompatible response | todo |
| Must | Version `ProcedureCompleted.v1` | Event schema and consumers agree | doing |
| Should | Add compatibility check for optional fields | Safe changes pass; breaking changes require v2 | todo |
| Should | Add duplicate-event acceptance test | Same `eventId` produces one effect | todo |

## Approval state

No week 7 branch or PR is present in the local repository. These items are therefore not marked approved. They require a child branch, PR to the correct environment and the corresponding automated gate before promotion.

## Branch flow

```text
feat/hu-07-contracts -> PR develop
qa/hu-07-contracts   -> PR qa + Pact verification
release/2.0.0        -> PR main + approval from ariel5253
```

## Definition of done for this slice

The contract is versioned, machine-readable, linked to the owning service, covered by consumer and producer tests, and documented with the affected domain event and data ownership. See [`testing-strategy.md`](../../../dlc-docs/11-quality/testing-strategy.md) and [`definition-of-done.md`](../../../dlc-docs/00-governance/definition-of-done.md).
