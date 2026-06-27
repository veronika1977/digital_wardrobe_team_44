# Testing Status — Digital Wardrobe

This document tracks testing status, coverage, and quality gates for Digital Wardrobe.

**Last updated:** June 28, 2026  

---

## Critical Modules and Coverage

| Critical module | Why critical | Required line coverage | Current line coverage | Evidence |
|-----------------|--------------|----------------------:|---------------------:|----------|
| `app/services/upload.py` (Backend) | US-08: Core background removal logic | 30% | 83% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| `app/routers/capsules.py` (Backend) | US-05: Capsule management API | 30% | 84% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| `app/routers/clothes.py` (Backend) | Core wardrobe management | 30% | 72% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| `app/routers/upload.py` (Backend) | US-08: Upload endpoint | 30% | 86% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| `app/models/capsule.py` (Backend) | US-05: Data model for capsules | 30% | 100% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| `app/models/clothing_item.py` (Backend) | Core data model | 30% | 100% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| `src/wardrobe.ts` (Frontend) | Core wardrobe logic | 30% | 100% | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) ([run #28290024710](https://github.com/veronika1977/digital_wardrobe_777/actions/runs/28290024710)) |

**Global coverage:**
- Backend: 66% (989 statements, 332 missed) — **exceeds 30% requirement** 
- Frontend: 100% for `wardrobe.ts`

---

## Automated Test Status

| Test type | Scope | Command or CI check | Latest result | Evidence |
|-----------|-------|---------------------|---------------|----------|
| Unit tests (Backend) | Critical product logic (capsules, items, upload, rembg) | `pytest tests/` | **64 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Integration tests (Backend) | API endpoints with database (TestClient + PostgreSQL) | `pytest tests/` | **Passing** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Automated QRTs | QR-001 (response time), QR-002 (fault tolerance) | `pytest tests/quality/` | **4 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Frontend unit tests | `wardrobe.ts` (core logic) | `npm run test:coverage` | **3 passed, 100% coverage** | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) ([run #28290024710](https://github.com/veronika1977/digital_wardrobe_777/actions/runs/28290024710)) |

---


## CI and QA Check Status

| Gate or check | Required for Done? | Latest protected-branch status | Evidence |
|---------------|-------------------|-------------------------------|----------|
| **Frontend CI** | | | |
| Linting (ESLint) | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Type checking (TypeScript) | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Build | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Unit tests | Yes |  Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) ([run #28290024710](https://github.com/veronika1977/digital_wardrobe_777/actions/runs/28290024710)) |
| Coverage (30% critical modules) | Yes | 100% for wardrobe.ts | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) ([run #28290024710](https://github.com/veronika1977/digital_wardrobe_777/actions/runs/28290024710)) |
| **Backend CI** | | | |
| Linting (flake8) | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Formatting (black) | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Build verification | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Unit tests (pytest) | Yes | **64 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Integration tests | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Automated QRTs | Yes | **4 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Coverage (≥30% critical modules) | Yes | **66% globally, 72-100% per module** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| **Documentation CI** | | | |
| Lychee link checker | Yes | Passing | [Lychee CI](https://github.com/veronika1977/digital_wardrobe_team_44/actions) |

## Additional QA Check Status

| QA objective or risk | Additional QA check | Scope | Latest result | Evidence | Limitations or follow-up |
|----------------------|---------------------|-------|---------------|----------|--------------------------|
| Dead code (unused functions, classes, variables) increases maintenance burden and may hide bugs | **Vulture** (static analysis for dead code) | All Python source code in `app/` | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859485226) | May produce false positives for dynamically used code |

---

## Manual Evidence That Does Not Count as QRT

| Evidence | Scope | Result | Follow-up PBI or issue |
|----------|-------|--------|------------------------|
| Customer UAT (June 25, 2026) | US-05 (Capsules) | Passed | Minor UI feedback - [#170](https://github.com/veronika1977/digital_wardrobe_team_44/issues/170) |
| Customer UAT (June 25, 2026) | US-06 (Edit Item) | Passed | Requested "days remaining" - [#171](https://github.com/veronika1977/digital_wardrobe_team_44/issues/171) |
| Customer UAT (June 25, 2026) | US-08 (Background Removal) | Passed | Performance acceptable |

---

## Assignment 4 Quality Gates

The following quality gates are **mandatory** for all PBIs starting from Assignment 4 and must remain active for later project work:

### Automated Tests
- Unit tests for critical modules (≥30% line coverage) — **implemented (66% coverage)**
- Integration tests for API endpoints — **implemented (64 tests passing)**
- Automated Quality Requirement Tests (QRT-001, QRT-002, QRT-003) — **implemented (4 tests passing)**

### CI Pipeline
- Linting (flake8 for backend, ESLint for frontend)
- Formatting / type checking (black for backend, TypeScript for frontend)
- Build verification
- Unit + integration tests
- Coverage reporting (66%)
- Lychee link checker for documentation

### Quality Requirements
- **QR-001: API Response Time < 3 seconds** — QRT-001 implemented and passing
- **QR-002: Background Removal Fault Tolerance** — QRT-002 implemented and passing
- **QR-003: Critical Module Testability** — verified via coverage report (66% > 30%)

### Documentation
- CHANGELOG.md updated for user-visible changes (US-05, US-06, US-08)
- Testing status documented in `docs/testing.md`
- Quality requirements documented in `docs/quality-requirements.md`
- QRT documented in `docs/quality-requirement-tests.md`

---

## Branch Protection Evidence

All repositories have branch protection rules enabled for `main`:

| Repository | Protection rules | Evidence |
|------------|-----------------|----------|
| Frontend | Require PR, 1 approval, status checks | [Screenshot](../reports/week4/images/branch-protection-frontend_1.png) |
| Frontend | Require PR, 1 approval, status checks | [Screenshot](../reports/week4/images/branch-protection-frontend_2.png) |
| Frontend | Require PR, 1 approval, status checks | [Screenshot](../reports/week4/images/branch-protection-frontend_3.png) |
| Backend | Require PR, 1 approval, status checks | [Screenshot](../reports/week4/images/branch-protection-backend_1.png) |
| Backend | Require PR, 1 approval, status checks | [Screenshot](../reports/week4/images/branch-protection-backend_2.png) |
| Backend | Require PR, 1 approval, status checks | [Screenshot](../reports/week4/images/branch-protection-backend_3.png) |
| Main repo | Require PR, 1 approval, Lychee check | [Screenshot](../reports/week4/images/branch-protection-main_1.png) |
| Main repo | Require PR, 1 approval, Lychee check | [Screenshot](../reports/week4/images/branch-protection-main_2.png) |
| Main repo | Require PR, 1 approval, Lychee check | [Screenshot](../reports/week4/images/branch-protection-main_3.png) |

---

## Next Steps (Sprint 3)

1. **DONE:** Unit tests for critical backend modules — 64 tests passing
2. **DONE:** Integration tests for API endpoints — passing
3. **DONE:** QRT for QR-001, QR-002 — 4 tests passing
4. **DONE:** Achieve ≥30% coverage for backend critical modules (67%)
5. Continue updating this document with Sprint 3 test results

---