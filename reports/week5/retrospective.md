# Sprint Retrospective — Week 5 

Author: @Mrxfg 
Date: 2026-07-03  
Sprint: 3 (MVP v2)

## What went well

- CI as automated quality gate: Enforcing linting, type checking, coverage thresholds, and link checks in CI reduced manual review overhead and caught integration issues before merge.
- Architecture-first implementation: Updating Static, Dynamic, and Deployment views before coding US-12/13 clarified component boundaries and prevented costly rework during frontend-backend sync.
- Combined UAT and Sprint Review: Running customer validation and the sprint demo in a single session accelerated feedback capture, PBI creation, and backlog prioritization.
- Explicit Definition of Done: Requiring QRT execution, documentation updates, and peer review before merge eliminated "almost done" PRs and post-merge hotfixes.

## What did not go well

- Frontend automated testing lag: Only core hooks/components are covered; UI state tests for US-12/13 rely entirely on manual UAT, increasing regression risk for future UI changes.
- Late discovery of fallback paths: Geolocation permission issues on the customer's device were only identified during UAT-004, requiring an immediate post-review hotfix for the manual city selector.
- Cross-repo PR coordination overhead: Backend schema changes required synchronous frontend updates, extending review cycles and increasing merge conflict risk across three repositories.
- Manual ADR traceability maintenance: Updating the QR ↔ ADR ↔ US mapping matrix required manual edits, creating a risk of documentation drift as the project scales.

## What the team changed or attempted to change based on the previous Sprint Retrospective, and what results they observed

In the Week 4 retrospective, the team committed to:
1. Enforcing strict DoD gates for every PR — Result: All merged PRs now include automated test evidence, coverage reports, and documentation updates. Post-merge bug rate dropped significantly.
2. Stabilizing the CI pipeline for testing and coverage — Result: pytest, coverage, and Vulture checks run reliably on every push. The team no longer spends cycles debugging flaky pipeline configurations.
3. Improving cross-repo issue traceability — Result: GitHub issue references across backend, frontend, and docs repositories reduced lost tasks and clarified ownership during MVP v2 planning.

## Action points
1. Add frontend UI testing to Definition of Done — Require React Testing Library + MSW tests for all new UI components before merge. Target ≥50% frontend coverage by end of Sprint 4.
   - Related docs: [`docs/definition-of-done.md`](../../docs/definition-of-done.md), [`docs/testing.md`](../../docs/testing.md)
2. Implement automated OpenAPI contract validation in CI — Add a CI step that fails the build if backend endpoint changes break frontend TypeScript types or documented schemas.
   - Related docs: [`docs/development-process.md`](../../docs/development-process.md)
   - Related QR: QR-001 (Response time), QR-002 (Fault tolerance)
