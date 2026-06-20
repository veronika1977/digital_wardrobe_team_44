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

## 3. CI/CD & Testing
- [ ] All required GitHub Actions (or other CI pipelines) have completed **successfully** (green status).
- [ ] Linters (code style checks) pass without errors.
- [ ] If the task involved adding new logic or fixing a bug, a corresponding **automated test** (unit or integration) has been written and passes successfully.

## 4. Documentation
- [ ] The `CHANGELOG.md` file is updated (if the change affects product functionality).
- [ ] `README.md` or other setup/deployment instructions are updated if dependencies, environment variables, or installation steps have changed.
- [ ] Clear comments are present in the code where the logic is non-obvious.

## 5. Final Verification
- [ ] Changes are successfully **merged** into the protected default branch (`main` or `master`).
- [ ] The implementation satisfies the **Acceptance Criteria** described in the body of the specific Issue.

---
*Note: If any of these items are not applicable to a specific task (e.g., a purely documentation task that does not require code tests), this must be explicitly justified in a comment on the PR or in the Issue itself.*