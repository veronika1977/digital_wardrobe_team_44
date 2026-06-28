# Sprint 2 Retrospective

## What Went Well

1. **Test coverage exceeded requirements** — achieved 66% global coverage (requirement: 30%), critical modules at 72-100%.
2. **Quality Requirement Tests implemented** — QRT-001 (response time < 3s), QRT-003 and QRT-002 (fault tolerance) are automated and passing.
3. **Customer UAT provided valuable feedback** — UAT on June 25 led to issues #170, #171, both closed within Sprint 2.
4. **CI pipeline fully operational** — backend (linting, tests, coverage, QRT, Vulture), frontend (linting, type checking, tests), and documentation (Lychee) all working.
5. **Additional QA check added** — Vulture detects dead code, improving maintainability.

---

## What Did Not Go Well

1. **Testing infrastructure setup took longer than expected** — conftest.py and database fixtures required multiple iterations, delaying test writing by ~1 day.
2. **Documentation updates were reactive** — docs/testing.md was updated multiple times at sprint end, causing temporary inconsistencies.
3. **Frontend testing is minimal** — only 3 tests for wardrobe.ts, other components untested.
4. **Connecting frontend with backend** — it was harder than we expected.

---

## What You Changed Compared to the Previous Sprint

Based on the Sprint 1 retrospective, in Sprint 2 we:

1. **Added automated testing** — went from 0 tests to 64 tests (unit + integration + QRT).
2. **Added quality requirement tests** — QRT-001 and QRT-002 now verify non-functional requirements automatically.
3. **Added code coverage tracking** — pytest-cov integrated, 66% coverage achieved.
4. **Added additional QA check** — Vulture for dead code detection.
5. **Conducted first customer UAT** — June 25, 2026, received actionable feedback.
6. **Established backend-frontend integration** — connected API endpoints with frontend components.

---

## One or Two Concrete Process Improvements for the Next Sprint

### Improvement 1: Update documentation after each PBI, not at sprint end

**Problem:** docs/testing.md was out of sync during Sprint 2 because we updated it only at the end.

**Change:** Add "Documentation Updated" checkbox to PR template. Reviewer must verify docs are current before approving.

**Success metric:** Zero documentation drift between CI runs and docs/testing.md.

### Improvement 2: Improve frontend-backend integration and testing

**Problem:** Sprint 2 had 64 backend tests but only 3 frontend tests. Connecting frontend with backend took longer than expected.

**Change:** Allocate 30% of testing time to frontend in Sprint 3. Write tests for App.tsx and at least 2 core components. Create integration tests for frontend-backend communication.

**Success metric:** Frontend coverage ≥ 50% by end of Sprint 3, and frontend-backend integration issues resolved within 1 day.
