# Testing Status — Digital Wardrobe

This document tracks testing status, coverage, and quality gates for Digital Wardrobe.

**Last updated:** June 24, 2026  
**Author:** @veronika1977

---

## Critical Modules and Coverage

| Critical module | Why critical | Required line coverage | Current line coverage | Evidence |
|-----------------|--------------|----------------------:|---------------------:|----------|
| `app/auth/` (Backend) | Handles Telegram authentication and JWT tokens. Security-critical. | 30% | 0% | Tests pending |
| `app/items/` (Backend) | Core CRUD operations for clothing items. Main user workflow. | 30% | 0% | Tests pending |
| `app/rembg/` (Backend) | Background removal integration. Risk of data loss on failure. | 30% | 0% | Tests pending |
| `src/components/` (Frontend) | UI components for wardrobe management. User-facing. | 30% | 0% |  Tests pending |

---

## Automated Test Status

| Test type | Scope | Command or CI check | Latest result | Evidence |
|-----------|-------|---------------------|---------------|----------|
| Unit tests | Critical product logic (backend) | `pytest tests/unit/` | Not implemented | — |
| Integration tests | API endpoints (backend) | `pytest tests/integration/` | Not implemented | — |
| Automated QRTs | QR-001, QR-002, QR-003 | `pytest tests/quality/` | Not implemented | — |
| Frontend unit tests | UI components (React) | `npm run test` | Not implemented | — |

---

## CI and QA Check Status

| Gate or check | Required for Done? | Latest protected-branch status | Evidence |
|---------------|-------------------|-------------------------------|----------|
| **Frontend CI** | | | |
| Linting (ESLint) | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Type checking (TypeScript) | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Build | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Unit tests | Yes |  Placeholder | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| Coverage (30% critical modules) | Yes | Not implemented | — |
| Additional QA (npm audit) | Yes | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) |
| **Backend CI** | | | |
| Linting (flake8) | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Formatting (black) | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Build verification | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Unit tests (pytest) | Yes | Placeholder | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Integration tests | Yes |  Placeholder | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Automated QRTs | Yes | Placeholder | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| Coverage (30% critical modules) | Yes |  Not implemented | — |
| Additional QA (pip-audit) | Yes | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) |
| **Documentation CI** | | | |
| Lychee link checker | Yes | Passing | [Lychee CI](https://github.com/veronika1977/digital_wardrobe_team_44/actions) |

---

## Additional QA Check Rationale

| QA objective or risk | Additional QA check | Scope | Latest result | Evidence | Limitations or follow-up |
|----------------------|---------------------|-------|---------------|----------|--------------------------|
| Dependencies with known vulnerabilities may expose users to security risks | `npm audit` (Frontend) | `package.json` and `package-lock.json` | Passing | [Frontend CI](https://github.com/veronika1977/digital_wardrobe_777/actions) | Some vulnerabilities may require manual triage or delayed upstream fixes |
| Python dependencies with known vulnerabilities | `pip-audit` (Backend) | `requirements.txt` | Passing | [Backend CI](https://github.com/Mrxfg/digital-wardrobe/actions) | Some vulnerabilities may require manual triage |
| Broken links in documentation | Lychee link checker | All `*.md` files |Passing | [Lychee CI](https://github.com/veronika1977/digital_wardrobe_team_44/actions) | Placeholder URLs are excluded |

---

## Manual Evidence That Does Not Count as QRT

| Evidence | Scope | Result | Follow-up PBI or issue |
|----------|-------|--------|------------------------|
| Customer UAT observation | Add item flow |  Pending UAT | — |
| Customer UAT observation | Delete item flow | Pending UAT | — |
| Customer UAT observation | Filter wardrobe | Pending UAT | — |

---

## Assignment 4 Quality Gates

The following quality gates are **mandatory** for all PBIs starting from Assignment 4 and must remain active for later project work:

### Automated Tests
- Unit tests for critical modules (≥30% line coverage) — **pending implementation**
- Integration tests for API endpoints — **pending implementation**
- Automated Quality Requirement Tests (QRT-001, QRT-002, QRT-003) — **pending implementation**

### CI Pipeline
- Linting (flake8 for backend, ESLint for frontend)
- Formatting / type checking (black for backend, TypeScript for frontend)
- Build verification
- Unit + integration tests (placeholders configured)
- Coverage reporting — **pending test implementation**
- Additional QA check (pip-audit for backend, npm audit for frontend)
- Lychee link checker for documentation

### Quality Requirements
- QR-001: API Response Time < 3 seconds — **test pending**
- QR-002: Background Removal Fault Tolerance — **test pending**
- QR-003: Critical Module Testability (≥30% coverage) — **tests pending**

### Documentation
- CHANGELOG.md updated for user-visible changes
- Testing status documented in `docs/testing.md`
- Quality requirements documented in `docs/quality-requirements.md`
- QRT documented in `docs/quality-requirement-tests.md`

---

## Branch Protection Evidence

All repositories have branch protection rules enabled for `main`:

| Repository | Protection rules | Evidence |
|------------|-----------------|----------|
| Frontend | Require PR, 1 approval, status checks | [Settings](https://github.com/veronika1977/digital_wardrobe_777/settings/branches) |
| Backend | Require PR, 1 approval, status checks | [Settings](https://github.com/Mrxfg/digital-wardrobe/branches) |
| Main repo | Require PR, 1 approval, Lychee check | [Settings](https://github.com/veronika1977/digital_wardrobe_team_44/settings/branches) |

---

## Next Steps

1. **Write unit tests** for critical backend modules (`app/auth/`, `app/items/`, `app/rembg/`)
2. **Write integration tests** for API endpoints
3. **Implement QRT** for QR-001, QR-002, QR-003
4. **Write frontend tests** for React components
5. **Achieve ≥30% coverage** for all critical modules
6. **Update this document** with real test results and coverage reports

---

**Reviewer:** @Evgeni1a