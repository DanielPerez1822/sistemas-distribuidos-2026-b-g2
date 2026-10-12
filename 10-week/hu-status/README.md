<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       10-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 10

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Prepare and compose the Patients and Billing frontend demo increments for MVP 2, with tested administrative workflows, versioned portal delivery, and clear integration boundaries.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| HU-PAT-001 | Build and compose the patient administrative management demo | doing | [Patients #13](https://github.com/code-corhuila/dlc-patient-portal/pull/13), [#17](https://github.com/code-corhuila/dlc-patient-portal/pull/17), [#18](https://github.com/code-corhuila/dlc-patient-portal/pull/18), [Front #85](https://github.com/code-corhuila/dlc-front/pull/85) |
| HU-BIL-002 | Prepare Billing composition and connect the dummy invoice list | doing | [Billing #29](https://github.com/code-corhuila/dlc-billing-portal/pull/29), [#30](https://github.com/code-corhuila/dlc-billing-portal/pull/30), [#32](https://github.com/code-corhuila/dlc-billing-portal/pull/32), [#33](https://github.com/code-corhuila/dlc-billing-portal/pull/33) |

Both stories remain in progress. The frontend increments use fictional data and do not establish real API integration, authoritative persistence, server authorization, or full HU acceptance. Billing PR #33 is open at the time of this report; the other PRs listed in the table are merged into `develop`.

## 2. My individual contribution
- Authored the Patients Angular skeleton and initial federation setup ([#2](https://github.com/code-corhuila/dlc-patient-portal/pull/2), [#3](https://github.com/code-corhuila/dlc-patient-portal/pull/3)), then added the feature route, fictional patient list, and owner-aligned administrative/care projection models ([#5](https://github.com/code-corhuila/dlc-patient-portal/pull/5), [#6](https://github.com/code-corhuila/dlc-patient-portal/pull/6), [#7](https://github.com/code-corhuila/dlc-patient-portal/pull/7)).
- Added the Patients composition lifecycle, portal identity corrections, Angular 21 lockfile reconciliation, and coverage/CI baseline ([#8](https://github.com/code-corhuila/dlc-patient-portal/pull/8), [#9](https://github.com/code-corhuila/dlc-patient-portal/pull/9), [#10](https://github.com/code-corhuila/dlc-patient-portal/pull/10), [#11](https://github.com/code-corhuila/dlc-patient-portal/pull/11)). The portal consumes shell capabilities and cleans up mounted resources.
- Connected shell-provided session/navigation and dummy patient registration ([#12](https://github.com/code-corhuila/dlc-patient-portal/pull/12), [#13](https://github.com/code-corhuila/dlc-patient-portal/pull/13)). Added Administrator/Assistant presentation gates, safe failure states, duplicate-document checks in memory, and unsaved-change protection.
- Added shared creation validation, a reusable patient form, versioned dummy updates, and patient editing ([#14](https://github.com/code-corhuila/dlc-patient-portal/pull/14), [#15](https://github.com/code-corhuila/dlc-patient-portal/pull/15), [#16](https://github.com/code-corhuila/dlc-patient-portal/pull/16), [#17](https://github.com/code-corhuila/dlc-patient-portal/pull/17)). Editing submits changed administrative fields plus `expectedVersion`; stale versions preserve the draft and require explicit reload.
- Prepared versioned Patients delivery and integrated the demo with the `dlc-front` registry, same-origin proxy, and Docker network ([Patients #18](https://github.com/code-corhuila/dlc-patient-portal/pull/18), [Front #85](https://github.com/code-corhuila/dlc-front/pull/85)). PR #18 reports 154 Angular tests and five delivery tests passing; Front #85 reports 143 tests and Docker/browser checks for Patients editing and existing Appointments/Clinical navigation.
- Established the Billing test baseline and composition lifecycle, packaged a versioned ESM release, and hardened publication/preview behavior ([#28](https://github.com/code-corhuila/dlc-billing-portal/pull/28), [#29](https://github.com/code-corhuila/dlc-billing-portal/pull/29), [#30](https://github.com/code-corhuila/dlc-billing-portal/pull/30), [#31](https://github.com/code-corhuila/dlc-billing-portal/pull/31), [#32](https://github.com/code-corhuila/dlc-billing-portal/pull/32)). Atomic publication preserves existing releases, serializes builds, and cleans up handled failures. PR #32 reports 113 tests passing and coverage above 80% for lines, statements, branches, and functions.
- Opened Billing [PR #33](https://github.com/code-corhuila/dlc-billing-portal/pull/33) to connect the fictional invoice list to the composition adapter, preserving search, status filters, pagination, and shell navigation. It reports 118 tests passing, successful builds, and desktop/mobile browser checks. Publication, actual shell registry updates, CI verification, and independent review remain pending in that PR.

Test counts and browser results above are attributed to the linked PR validation records. They were not rerun while preparing this status document; local results do not substitute for CI evidence on the final published revision.

## 3. Blockers and risks
- Patient data remains in memory and resets on reload/full unmount. Owner API integration, persistent uniqueness/audit, administrative deactivation rules, and assigned-patient Dentist access are still required.
- Billing invoice detail, issuance, payments, and PDF download remain pending in the composed portal. PR #33 currently routes invoice selection to the unavailable/local 404 frame.
- Release-build tests and Compose configuration checks do not establish production deployment. Billing Docker runtime validation and revision-specific acceptance/CI evidence remain pending according to the linked PRs.
- Week 10 also requires distributed persistence and an integrated MVP 2 release. These frontend PRs do not prove backend saga compensation, transactional outbox, idempotent consumers, environment promotion, or a `v2.0.0` release; those remain acceptance gaps.

## 4. Plan for next week
- Resolve Billing PR #33 review and CI findings, publish the accepted release, and update the real shell registry with browser evidence for the exact revision.
- Implement the composed invoice detail and issuance flow, then connect owner APIs through the shell-provided HTTP/session capabilities.
- Replace patient fixtures with the Patients owner integration and verify authorization, version conflicts, uniqueness, status transitions, and persistence using contract/integration tests.
- Coordinate end-to-end MVP 2 acceptance covering service-owned data, outbox delivery, duplicate-event handling, and a failure/compensation path before QA/main promotion and release tagging.

## 5. Compliance self-check
- [ ] Conventional Commits - `type(scope): summary` - documented for several increments; not verified for every commit in all linked PRs.
- [ ] Per-environment HU branch + PR to that environment (hu-xxx-dev -> develop, ...) - feature/HU PRs target `develop`; QA/main promotion is not evidenced.
- [x] Testable acceptance criteria - linked PRs define observable lifecycle, validation, version-conflict, and release-preservation checks for the frontend increments.
- [x] Tests added/updated (unit / integration) - unit/component, packaging, and composition tests are documented; real backend integration acceptance remains pending.
- [x] DDD / hexagonal boundaries respected (domain has no I/O) - reported frontend increments isolate dummy data and preserve owner contracts and shell-managed HTTP/session responsibilities.
- [x] No secrets; config via environment variables - linked delivery increments report no credentials and provide environment/deployment configuration.

## 6. Evidence links
- [HU-PAT-001 canonical story](https://github.com/code-corhuila/dlc-docs/issues/53) and [Patients portal issue #1](https://github.com/code-corhuila/dlc-patient-portal/issues/1).
- [HU-BIL-002 canonical story](https://github.com/code-corhuila/dlc-docs/issues/64) and [Billing portal issue #3](https://github.com/code-corhuila/dlc-billing-portal/issues/3).
- [Patients #13 - dummy registration](https://github.com/code-corhuila/dlc-patient-portal/pull/13), [#16 - versioned updates](https://github.com/code-corhuila/dlc-patient-portal/pull/16), [#17 - editing flow](https://github.com/code-corhuila/dlc-patient-portal/pull/17), and [#18 - versioned delivery](https://github.com/code-corhuila/dlc-patient-portal/pull/18).
- [Patients PR #16 CI run](https://github.com/code-corhuila/dlc-patient-portal/actions/runs/38118051088) - the PR associates this run with head `c029c61`; it does not validate later revisions.
- [Front #85 - Patients demo integration](https://github.com/code-corhuila/dlc-front/pull/85).
- [Billing #29 - composition lifecycle](https://github.com/code-corhuila/dlc-billing-portal/pull/29), [#30 - versioned release](https://github.com/code-corhuila/dlc-billing-portal/pull/30), [#32 - atomic publication and coverage](https://github.com/code-corhuila/dlc-billing-portal/pull/32), and [#33 - composed invoice list (open)](https://github.com/code-corhuila/dlc-billing-portal/pull/33).
