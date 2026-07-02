# Quality Requirement Tests — Digital Wardrobe

This document defines automated tests that verify quality requirements.

## QRT-001: API Response Time

**Linked quality requirement:** QR-001

**Verification method:** Automated integration test with timing measurement.

**Test file:** [`backend/tests/quality/test_qr001_response_time.py`](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/quality/test_qr001_response_time.py)

**Test data, setup, or environment:** 
- Backend running on localhost:127.0.0.1
- Valid JWT token for authenticated requests
- Sample clothing item data (name, category, season, color, material)

**Automated command or CI check:** 
```bash
cd backend
pytest tests/quality/test_qr001_response_time.py -v
```

**Expected measurable result:**

- API responds within 3 seconds for 95% of requests
- Test logs: "Response time: 0.75s < 3s threshold"

**Evidence link:** Latest CI run showing test results and timing metrics.


## QRT-002: Background Removal Fault Tolerance

**Linked quality requirement:** QR-002

**Verification method:** Automated integration test with mocked Rembg failure.

**Test file:** [`backend/tests/quality/test_qr002_fault_tolerance.py`](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/quality/test_qr002_fault_tolerance.py)

**Related tests:** 

- [backend/tests/test_fallback_strategy.py](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/test_fallback_strategy.py) — 8 tests covering success, corrupted image, timeout scenarios
- [backend/tests/test_background_removal.py](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/test_background_removal.py) — 10 tests (3 unit + 5 integration + 2 edge cases)

**Test data, setup, or environment:**

- Backend running on localhost:127.0.0.1
- Mocked Rembg service that throws error
- Sample image file (valid png)

**Automated command or CI check:**

```bash
cd backend
pytest tests/quality/test_qr002_fault_tolerance.py -v
pytest tests/test_fallback_strategy.py -v
pytest tests/test_background_removal.py -v
```

**Expected measurable result:**

- Original photo is saved to storage (100% data preservation)
- Error is logged with details
- Main application remains fully operational (0% downtime for unrelated features)
- Test completes successfully

**Evidence link:** Latest CI run showing fault tolerance test results.

## QRT-003: Critical Module Coverage

**Linked quality requirement:** QR-003

**Verification method:** Automated coverage check in CI.

**Test files:**
- [backend/tests/test_items.py](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/test_items.py?spm=a2ty_o01.29997173.0.0.6b5d55fbdW2YOD&file=test_items.py)
- [backend/tests/test_background_removal.py](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/test_background_removal.py?spm=a2ty_o01.29997173.0.0.6b5d55fbdW2YOD&file=test_background_removal.py)
- [backend/tests/test_fallback_strategy.py](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/test_fallback_strategy.py?spm=a2ty_o01.29997173.0.0.6b5d55fbdW2YOD&file=test_fallback_strategy.py)

**Critical modules:**
- [app/auth/] (authentication logic)
- [app/items/] (item management)
- [app/rembg/] (background removal)

**Automated command or CI check:**

```bash
cd backend
pytest tests/ --cov=app --cov-report=term-missing --cov-fail-under=30
```

**Expected measurable result:**

- Each critical module has ≥30% line coverage
- Coverage report shows: "Lines: 66% (threshold: 30%)"

**Evidence link:** Latest CI run showing coverage report.

## QRT-004: Weather Integration Performance & Fault Tolerance (US-12)

**Linked quality requirement:** QR-001

**Verification method:** Integration test + UAT validation.

**Test file:** [`backend/tests/quality/test_qr004_weather_location.py`](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/quality/test_qr004_weather_location.py)

**Test data, setup, or environment:**

- Backend running on localhost:8000 with valid JWT
- Test user with/without location configured

**Automated command or CI check:**

```bash
cd backend
pytest tests/quality/test_qr004_weather_location.py -v
```
**Expected measurable result:**

- GET /api/user/location returns valid coords or 404 in < 500ms
- Response structure matches schema (latitude, longitude as numbers)

**Evidence link:** [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions), [UAT-004](./user-acceptance-tests.md#UAT-004) 

---

## QRT-005: Calendar Planning Responsiveness & Persistence (US-13)

**Linked quality requirement:** QR-001, QR-002

**Verification method:** Integration test + UAT validation.

**Test file:** [`backend/tests/quality/test_qr005_calendar_outfit.py`](https://github.com/Mrxfg/digital-wardrobe/blob/main/backend/tests/quality/test_qr005_calendar_outfit.py)

**Test data, setup, or environment:**

- Backend running on localhost:8000 with valid JWT
- PostgreSQL test database via fixtures

**Automated command or CI check:**

```bash
cd backend
pytest tests/quality/test_qr005_calendar_outfit.py -v
```

**Expected measurable result:** 

- CRUD operations return valid status codes (200/201/400)
- Cascade safety verified via existing capsule/item tests
- UI sync < 500ms verified via UAT-005

**Evidence link:** [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions), [UAT-005](../user-acceptance-tests.md#UAT-005)

## Test Execution Summary

| QRT ID | Linked QR | Test Type | Command | Status | Evidence |
|--------|-----------|-----------|---------|--------|----------|
| QRT-001 | QR-001 | Integration | `pytest tests/quality/test_qr001_response_time.py` | Implemented | [CI run](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859755265) |
| QRT-002 | QR-002 | Integration | `pytest tests/quality/test_qr002_fault_tolerance.py` |Implemented | [CI run](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859755265) |
| QRT-003 | QR-003 | Coverage | `pytest tests/ --cov=app --cov-fail-under=30` | Implemented | [CI run](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859755265) |
| QRT-004| QR-001 | Integration + UAT | `pytest tests/quality/test_qr004_weather_location.py` | Implemented | [CI](https://github.com/Mrxfg/digital-wardrobe/actions/), [UAT-004](../user-acceptance-tests.md#uat-004) |
| QRT-005 | QR-001, QR-002 | Integration + UAT | `pytest tests/quality/test_qr005_calendar_outfit.py` | Implemented | [CI](https://github.com/Mrxfg/digital-wardrobe/actions/), [UAT-005](../user-acceptance-tests.md#uat-005) |


Last updated: July 2, 2026
Author: @veronika1977
Reviewer: @Evgeni1a