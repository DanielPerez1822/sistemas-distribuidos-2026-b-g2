<!-- HU-STATUS TEMPLATE - do NOT remove the <!-- ... --> markers or the table headers.
     Your weekly grade is read AUTOMATICALLY from this file:
       14-week/hu-status/README.md  (inside YOUR fork). English. -->

# Weekly Status - Week 14

Reporting period: November 9–15, 2026 (America/Bogota).

<!-- CONFIG-START - must match your profile repo (username/username) CONFIG -->
- FULL_NAME: Daniel Perez Lozada
- GITHUB_USER: DanielPerez1822
- TEAM: Di Lucca
- SPRINT_GOAL: Support local stack validation, notification configuration and release documentation review.
<!-- CONFIG-END -->

## 1. User stories worked this week
| HU ID | Title | Status (todo/doing/done) | Evidence (PR or commit URL) |
|---|---|---|---|
| Project infrastructure | Local stack and notification configuration | doing | [CI commit](https://github.com/code-corhuila/dlc-infra/commit/fb50c01b3840dd66cd92399166cde7d6f30fad6c), [runtime commit](https://github.com/code-corhuila/dlc-infra/commit/21e2a68e8c67d0e4954dd06d36f68cd766ea97f5) |

## 2. My individual contribution
- Authored changes to validate the composed local stack in CI and configure local notification delivery, SMTP settings and runtime access. The linked commits were subsequently cherry-picked by another contributor; their author dates fall in this week.
- Approved [Docs #175](https://github.com/code-corhuila/dlc-docs/pull/175) and [#176](https://github.com/code-corhuila/dlc-docs/pull/176) on November 14, reviewing release 3.0.0 status and technical debt. These are reviews of others’ work.

## 3. Blockers and risks
- Notification delivery configuration depends on the worker consumer and appointment scheduler; configuration alone does not establish end-to-end delivery. Release documentation records HU-OPS-001 as incomplete and identifies remaining technical debt.
- The commits add validation scripts and CI configuration; a successful run for the exact revision was not independently verified.

## 4. Plan for next week
- Verify the complete notification flow and CI results, and follow up on the release technical backlog.

## 5. Compliance self-check
- [ ] Conventional Commits - not independently verified for every commit.
- [ ] Per-environment HU branch + PR to that environment - complete promotion trail not verified.
- [ ] Testable acceptance criteria - complete story acceptance not independently verified.
- [x] Tests added/updated (unit / integration) - verification scripts are present in the linked commit; execution was not independently verified.
- [ ] DDD / hexagonal boundaries respected (domain has no I/O) - complete story not independently audited.
- [ ] No secrets; config via environment variables - complete scope not independently audited.

## 6. Evidence links
- [HU-PAT-001 canonical story](https://github.com/code-corhuila/dlc-docs/issues/53).
- PR links above document the increments and reported validation; they do not by themselves establish final acceptance.
