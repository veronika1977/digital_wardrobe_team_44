# Team Definition of Done (DoD)

This document defines the minimum quality standards that must be met for any task (PBI or Course Task) to be moved to the **Done** status.

A task is considered complete **only when** ALL items in this checklist are satisfied, along with the specific Acceptance Criteria of the individual task.

## 1. Process & Roles
- [ ] The Issue explicitly names two different people: **Implementer** (who does the work) and **Reviewer** (who verifies it).
- [ ] The task has an up-to-date **Work Status** (To Do → Ready → In Progress → Review → Done).
- [ ] **Traceability** is maintained: the Issue contains a link to the corresponding Pull Request / Merge Request (or vice versa, the PR/MR links to the Issue, e.g., `Closes #XX`).

## 2. Code Quality & Review
- [ ] Code is written according to the project style guide (properly formatted, no "junk" code or commented-out legacy fragments).
- [ ] The Pull Request / Merge Request has been reviewed and received an **Approval** from the designated Reviewer.
- [ ] There are no merge conflicts with the protected default branch (`main` or `master`).
- [ ] All review comments have been addressed before merge.

## 3. CI/CD & Automated Checks
- [ ] All required GitHub Actions (or other CI pipelines) have completed **successfully** (green status).
- [ ] Linters (code style checks) pass without errors.
- [ ] Formatting and type checking pass (if applicable to the stack).
- [ ] Build succeeds without errors.
- [ ] **Branch protection rules** are enforced (no direct pushes to `main`, required approvals).

## 4. Testing & Coverage
- [ ] If the task involved adding new logic or fixing a bug, a corresponding **automated test** (unit or integration) has been written and passes successfully.
- [ ] **Unit tests** cover critical product logic.
- [ ] **Integration tests** cover important interactions between product components (e.g., API endpoints, database interactions).
- [ ] **Critical modules** maintain at least **30% automated line coverage** (unless TA-approved exception).
- [ ] Testing evidence is preserved in PR/MR description, CI logs, or linked documentation.

## 5. Quality Requirements & QRT
- [ ] Relevant **Quality Requirements** (QR-001, QR-002, QR-003) are satisfied or explicitly documented as not applicable.
- [ ] Relevant **automated Quality Requirement Tests** (QRT-001, QRT-002, QRT-003) pass successfully.
- [ ] If a quality requirement is not applicable to the current task, this is explicitly justified in the PR/MR description.

## 6. Documentation
- [ ] The `CHANGELOG.md` file is updated (if the change affects product functionality).
- [ ] `README.md` or other setup/deployment instructions are updated if dependencies, environment variables, or installation steps have changed.
- [ ] Clear comments are present in the code where the logic is non-obvious.
- [ ] API documentation (`docs/api-contract.md`) is updated if endpoints changed.
- [ ] Design system documentation (`docs/design-system.md`) is updated if UI components changed.

## 7. Final Verification
- [ ] Changes are successfully **merged** into the protected default branch (`main` or `master`).
- [ ] The implementation satisfies the **Acceptance Criteria** described in the body of the specific Issue.
- [ ] For User Stories: all linked supporting PBIs are completed and marked Done.

---

## Assignment 4 Quality Gates

The following quality gates are **mandatory** for all PBIs starting from Assignment 4 and must remain active for later project work:

### Automated Tests
- Unit tests for critical modules (≥30% line coverage)
- Integration tests for API endpoints
- Automated Quality Requirement Tests (QRT-001, QRT-002, QRT-003)

### CI Pipeline
- Linting (code style)
- Formatting / type checking
- Build verification
- Unit + integration tests
- Coverage reporting
- Additional QA check (e.g., dependency vulnerability scan)

### Quality Requirements
- QR-001: API Response Time < 3 seconds
- QR-002: Background Removal Fault Tolerance
- QR-003: Critical Module Testability (≥30% coverage)

### Documentation
- CHANGELOG.md updated for user-visible changes
- Testing status documented in `docs/testing.md`
- Quality requirements documented in `docs/quality-requirements.md`
- QRT documented in `docs/quality-requirement-tests.md`

---

## Exceptions

If any of these items are not applicable to a specific task, this must be explicitly justified in a comment on the PR or in the Issue itself.

If a quality requirement or QRT is not applicable to the current task, document why in the PR/MR description and link to the relevant QR/QRT documentation.

**Last updated:** June 24, 2026  
**Author:** @veronika1977  
**Reviewer:** @Evgeni1a