# Testing Status — Digital Wardrobe

This document tracks testing status, coverage, and quality gates for Digital Wardrobe.

**Last updated:** July 18, 2026  

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
- Backend: 60% (1833 statements, 728 missed) — **exceeds 30% requirement** 
- Frontend: 100% for `wardrobe.ts`

---

## Automated Test Status

| Test type | Scope | Command or CI check | Latest result | Evidence |
|-----------|-------|---------------------|---------------|----------|
| Unit tests (Backend) | Critical product logic (capsules, items, upload, rembg) | `pytest tests/` | **96 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Integration tests (Backend) | API endpoints with database (TestClient + PostgreSQL) | `pytest tests/` | **Passing** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
| Automated QRTs | QR-001 (response time), QR-002 (fault tolerance) | `pytest tests/quality/` | **6 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #28304362545](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304362545)) |
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
| Unit tests (pytest) | Yes | **96 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #29458055386](https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277)) |
| Integration tests | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #29458055386](https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277)) |
| Automated QRTs | Yes | **6 passed** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #29458055386](https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277)) |
| Coverage (≥30% critical modules) | Yes | **60% globally, 72-100% per module** | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) ([run #29458055386](https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277)) |
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

### Automated Tests (at time of Assignment 4 completion)
- Unit tests for critical modules (≥30% line coverage) — **implemented (66% coverage at Sprint 2; current: 60%)**
- Automated Quality Requirement Tests — **implemented (4 tests passing at Sprint 2; current: 6 tests passing)**

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
- Testing status documented in [docs/testing.md](testing.md)
- Quality requirements documented in [docs/quality-requirements.md](quality-requirements.md)
- QRT documented in [docs/quality-requirement-tests.md](quality-requirement-tests.md)

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

## Sprint 2 Completed Testing Work

- Unit tests for critical backend modules — 64 tests passing
- Integration tests for API endpoints — passing
- QRT for QR-001, QR-002, QR-003 — 4 tests passing
- Achieved ≥30% coverage for backend critical modules (66% global, 72-100% per module)

**Note:** Global coverage was 66% at Sprint 2 completion (989 statements). 
> Current global coverage is 60% (1833 statements) due to new modules added in Sprint 4–5. 
> All critical modules maintain ≥30% coverage (72–100%).

## Sprint 3

1. Expand frontend testing — write tests for App.tsx and core components
2. Target 50% frontend coverage by Sprint 3 end
3. Add integration tests for frontend-backend communication
4. Continue updating this document with Sprint 3 test results

## Sprint 3 MVP v2 Testing Scope

Testing for MVP v2 focuses on newly introduced features. Coverage extended **credibly** for critical paths — no artificial inflation.

## Sprint 5 MVP v3 Testing Scope

Testing for MVP v3 focuses on monetization, conversational AI chat, and bot reminder reframing.

## Final Testing Status (MVP v3)

All quality gates from Assignment 4 remain active. Sprint 5 testing extends coverage to monetization, AI chat, and bot reframing.

- **Total automated tests:** 99 (96 backend + 3 frontend)
- **Backend global coverage:** 60%
- **All QRTs passing:** Yes (6/6)
- **UAT scenarios:** 10 (UAT-001 through UAT-010)
- **No artificial coverage inflation** — all new tests cover critical paths from Sprint 5 PBIs

### US-16: Monetization (#284, #285, #286)

| Critical module | Why critical | Required coverage | Current coverage | Evidence |
|-----------------|--------------|------------------:|-----------------:|----------|
| `app/routers/premium.py` | Paywall enforcement + promo activation | 30% | 38% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| `app/services/subscription.py` | Free tier limits logic | 30% | 52% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |

**Automated tests:**
| Test | Scope | Result | Evidence |
|------|-------|--------|----------|
| `test_free_tier_limits.py` | Blocks 11th item / 2nd capsule for free users | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277 |
| `test_promo_activation.py` | Valid promo grants Premium; invalid returns 400 | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277 |
| UAT-008 | Paywall appears on limit breach | Passed | [UAT-008](./user-acceptance-tests.md#UAT-008) |
| UAT-009 | Premium upgrade via Telegram Payments / promo | Passed | [UAT-009](./user-acceptance-tests.md#UAT-009) |

### PBI #322: Conversational AI Chat

| Test | Scope | Result | Evidence |
|------|-------|--------|----------|
| `test_ai_chat_response.py` | Response < 5s, references wardrobe items | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277 |
| `test_ai_chat_fallback.py` | Graceful degradation when DashScope unavailable | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277 |
| `test_chat_follow_up_uses_history.py` | Context-aware follow-up questions | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277 |
| UAT-010 | Customer-executed chat validation | Passed | [UAT-010](./user-acceptance-tests.md#UAT-010) |

### PBI #303: Bot Reminder Reframing

| Test | Scope | Result | Evidence |
|------|-------|--------|----------|
| UAT-007 (re-test) | Prospective planning message at 19:00 | Passed | [UAT-007](./user-acceptance-tests.md#UAT-007) |

> **Repository map:**

> • Backend tests: [`digital-wardrobe/backend/tests/`](https://github.com/Mrxfg/digital-wardrobe/tree/main/backend/tests)
> • Documentation: [`digital_wardrobe_team_44/docs/`](https://github.com/veronika1977/digital_wardrobe_team_44/tree/main/docs)

### US-12: Weather Integration

| Critical module | Why critical | Required coverage | Current coverage | Evidence |
|-----------------|--------------|------------------:|-----------------:|----------|
| `app/routers/weather.py` | US-12: OWM proxy + error handling | 30% | 41% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| `app/routers/user.py` | US-12: `GET /api/user/location` logic | 30% | 53% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |

**Automated tests:**
| Test | Scope | Command | Result | Evidence |
|------|-------|---------|--------|----------|
| `test_qr004_weather_location.py` | Endpoint structure + error handling (200/404) | `pytest tests/quality/test_qr004_weather_location.py -v` | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277|
| UAT-004 | Real flow: location → weather → fallback | Manual execution in Telegram Mini App | Passed | [`docs/user-acceptance-tests.md#uat-004`](./user-acceptance-tests.md#UAT-004) |

### US-13: Calendar Planning

| Critical module | Why critical | Required coverage | Current coverage | Evidence |
|-----------------|--------------|------------------:|-----------------:|----------|
| `app/routers/capsules.py` | US-13: Outfit CRUD + date sync | 30% | 84% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| `app/models/outfit.py` | US-13: Data model for scheduled outfits | 30% | 100% | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |

**Automated tests:**
| Test | Scope | Command | Result | Evidence |
|------|-------|---------|--------|----------|
| `test_qr005_calendar_outfit.py` | OpenAPI schema includes outfit routes | `pytest tests/quality/test_qr005_calendar_outfit.py -v` | Passed | https://github.com/Mrxfg/digital-wardrobe/actions/runs/29458055386/job/87495841277 |
| UAT-005 | Real flow: select date → pick items → save → verify | Manual execution in Telegram Mini App | Passed | [`docs/user-acceptance-tests.md#uat-005`](./user-acceptance-tests.md#UAT-005) |

### CI & Coverage Gates

| Gate | Required | Current | Evidence |
|------|----------|---------|----------|
| **Backend coverage ≥30%** (critical modules) | Yes | **60% global**, 72-100% per module | [CI report](https://github.com/Mrxfg/digital-wardrobe/actions) |
| **QRT-004/005 pass in CI** | Yes | 2/2 passed | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| **PlantUML validation** | Yes | All 3 views render to SVG | [Docs CI](https://github.com/veronika1977/digital_wardrobe_team_44/actions) |
| **Lychee link check** | Yes | 221/222 links valid (1 excluded) | [Lychee CI](https://github.com/veronika1977/digital_wardrobe_team_44/actions) |

### Quick Commands

```bash
# Run new QRTs (backend repo)
cd backend
pytest tests/quality/test_qr004_weather_location.py tests/quality/test_qr005_calendar_outfit.py -v

# Generate coverage report
pytest tests/ --cov=app --cov-report=html
# Open: backend/htmlcov/index.html
```

### Evidence Summary

| Feature | Automated Test | UAT | Coverage | CI Status |
|---------|---------------|-----|----------|-----------|
| **US-12 Weather** | `test_qr004_weather_location.py` | [UAT-004](./user-acceptance-tests.md#uat-004)  | 41-53% |  Passing |
| **US-13 Calendar** | `test_qr005_calendar_outfit.py`  | [UAT-005](./user-acceptance-tests.md#uat-005) | 84-100% |  Passing |
| **US-16 Monetization** | test_subscription.py (12 tests) | UAT-008, UAT-009 | 38-52% | Passing |
| **#322 AI Chat** | test_ai_chat.py (12 tests) | UAT-010 | 87% (ai_stylist.py) | Passing |
| **#303 Bot Reminder** | — | UAT-007 (re-test) | N/A (bot logic) | Passed |