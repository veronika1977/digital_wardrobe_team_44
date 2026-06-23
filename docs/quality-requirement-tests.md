# Quality Requirement Tests — Digital Wardrobe

This document defines automated tests that verify quality requirements.

## QRT-001: API Response Time

**Linked quality requirement:** QR-001

**Verification method:** Automated integration test with timing measurement.

**Test data, setup, or environment:** 
- Backend running on localhost:8000
- Valid JWT token for authenticated requests
- Sample clothing item data (name, category, season, color, material)

**Automated command or CI check:** 
```bash
npm run test:integration -- --grep "response time"
```

**Expected measurable result:**

- API responds within 3 seconds for 95% of requests
- Test logs: "Response time: 1.2s < 3s threshold"
**Evidence link:** Latest CI run showing test results and timing metrics.


## QRT-002: Background Removal Fault Tolerance

**Linked quality requirement: QR-002 **
**Verification method:** Automated integration test with mocked Rembg failure.

**Test data, setup, or environment:**
- Backend running on localhost:127.0.0.1
- Mocked Rembg service that throws error
- Sample image file (valid png)

**Automated command or CI check:**

```bash
npm run test:integration -- --grep "background removal failure"
```

**Expected measurable result:**

- Original photo is saved (no data loss)
- User notification is returned: "Background removal unavailable"
- Test completes within 5 seconds

**Evidence link:** Latest CI run showing fault tolerance test results.

## QRT-003: Critical Module Coverage

**Linked quality requirement:** QR-003

**Verification method:** Automated coverage check in CI.

**Test data, setup, or environment:**

1. Standard CI environment
2. Unit tests for critical modules:
  - src/auth/ (authentication logic)
  - src/items/ (item management)
  - src/rembg/ (background removal)

**Automated command or CI check:**

```bash
npm run test:unit -- --coverage --coverageThreshold='{"global":{"lines":30}}'
```

**Expected measurable result:**
- Each critical module has ≥30% line coverage
- Coverage report shows: "Lines: 42% (threshold: 30%)"

**Evidence link:** Latest CI run showing coverage report.

## Test Execution Summary

| QRT ID | Linked QR | Test Type | Command | Status | Evidence |
|--------|-----------|-----------|---------|--------|----------|
| QRT-001 | QR-001 | Integration | `npm run test:integration` |  Not implemented yet | *(link on running)* |
| QRT-002 | QR-002 | Integration | `npm run test:integration` | Not implemented yet | *(link on running)* |
| QRT-003 | QR-003 | Unit + Coverage | `npm run test:unit -- --coverage` | Not implemented yet | *(link on running)* |


Last updated: June 24, 2026
Author: @veronika1977
Reviewer: @Evgeni1a