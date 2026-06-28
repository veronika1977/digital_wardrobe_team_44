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

- Original photo is saved (no data loss)
- Test completes within 5 seconds

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

## Test Execution Summary

| QRT ID | Linked QR | Test Type | Command | Status | Evidence |
|--------|-----------|-----------|---------|--------|----------|
| QRT-001 | QR-001 | Integration | `pytest tests/quality/test_qr001_response_time.py` | Implemented |  [CI run](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859755265) |
| QRT-002 | QR-002 | Integration | `pytest tests/quality/test_qr002_fault_tolerance.py` | Implemented |  [CI run](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859755265) |
| QRT-003 | QR-003 | Unit + Coverage | `pytest tests/ --cov=app --cov-fail-under=30` | Implemented  |  [CI run](https://github.com/Mrxfg/digital-wardrobe/actions/runs/28304967461/job/83859755265) |


Last updated: June 28, 2026
Author: @veronika1977
Reviewer: @Evgeni1a