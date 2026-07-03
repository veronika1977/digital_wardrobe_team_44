# Team Reflection — Week 5 

**Author:** @CatherineHar  
**Date:** 2026-07-03  
**Sprint:** 3 (MVP v2)

---

## Learning points

1. **Architecture views clarify integration boundaries** — Writing Static, Dynamic, and Deployment diagrams in PlantUML forced the team to explicitly define component interfaces, failure paths, and deployment constraints before implementation. This prevented costly rework during frontend-backend integration.
2. **ADRs make decisions traceable, not just documented** — Linking each ADR to QR-001/002/003 and User Stories created a living decision log that answers "why was this built this way?" during code reviews and customer demos.
3. **Credible coverage requires targeting changed contracts** — Instead of inflating metrics with trivial assertions, QRT-004/005 validate response structure, status codes, and fallback behavior for new endpoints. This approach proved more valuable than arbitrary coverage growth.
4. **Cross-repo coordination needs explicit contracts** — Managing three repositories (backend, frontend, docs) highlighted that API schema changes must be synchronized via OpenAPI validation in CI, not informal communication.
5. **UAT + Sprint Review in one session accelerates feedback** — Capturing customer observations, triaging them into PBIs, and updating the backlog within the same meeting prevented scope creep and aligned priorities immediately.

---

## Validated assumptions

1. **PlantUML + CI rendering works for maintained diagrams** — Source `.puml` files stay in repo, SVGs auto-generated in CI, links remain stable across branches.
2. **Hybrid weather flow (backend coords → frontend API call) reduces latency** — Direct frontend-to-OpenWeatherMap calls cut round-trip time and simplified backend error handling.


---

## Friction and gaps

1. **Frontend automated testing still lags backend** — Only core hooks/components covered; UI state tests for US-12/13 rely on manual UAT.
2. **Geolocation permissions vary by device** — UAT-004 initially failed on customer laptop; required immediate fallback UI fix post-review.
3. **ADR traceability matrix required manual updates** — No automated tooling to generate QR ↔ ADR ↔ US mappings from metadata.
4. **Cross-repo PR coordination added review overhead** — Schema changes required simultaneous updates in backend + frontend repos, extending review cycles.

---

## Planned response

1. **Expand frontend automated testing** — Add React Testing Library + MSW tests for Weather and Calendar UI states; target 50% frontend coverage by Sprint 6.
   - Related docs: [`docs/testing.md`](../../docs/testing.md), [`docs/quality-requirement-tests.md`](../../docs/quality-requirement-tests.md)
   - Related milestone: [Sprint 6](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/6)

2. **Automate traceability matrix generation** — Explore extracting ADR metadata (status, QR links, US links) to auto-generate the matrix in `docs/architecture/README.md`.
   - Related docs: [`docs/architecture/README.md`](../../docs/architecture/README.md), [`docs/architecture/adr/`](../../docs/architecture/adr/)
   - Related QR: QR-003 (Testability)

3. **Enforce cross-repo API contract validation** — Add OpenAPI schema diff check to CI; block PRs if backend endpoint changes break frontend types.
   - Related docs: [`docs/development-process.md`](../../docs/development-process.md), [`.github/workflows/ci.yml`](https://github.com/Mrxfg/digital-wardrobe/blob/main/.github/workflows/ci.yml)
   - Related QR: QR-001 (Response time), QR-002 (Fault tolerance)

4. **Instrument production metrics for QR validation** — Add response time logging and error rate monitoring for Weather/Calendar endpoints to validate QR-001/002 under real traffic.
   - Related docs: [`docs/quality-requirements.md`](../../docs/quality-requirements.md)
   - Related milestone: [Sprint 6](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/6)

---
*Related artifacts:*  
[Sprint Review Summary](./sprint-review-summary.md) | [Retrospective](./retrospective.md) | [LLM Report](./llm-report.md)