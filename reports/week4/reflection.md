# Team Reflection - Week 4

## Learning points

1. **Customer feedback reveals blind spots** — UAT on June 25 surfaced issues (e.g., "days remaining" feature) we would never have found ourselves.
2. **Non-functional requirements need automation** — manual checks for response time and fault tolerance are unreliable; QRT-001, QRT-002, QRT-003 now verify them in CI.
3. **Automated testing pays off quickly** — writing 64 tests took time, but caught real bugs and made refactoring safe.
4. **CI setup requires iteration** — pytest, coverage, and Vulture needed multiple attempts before working reliably.

---

## Validated assumptions

1. **FastAPI + PostgreSQL stack works well** — no major issues encountered during implementation.
2. **pytest is the right choice for backend testing** — easy to set up, good coverage reporting, integrates well with CI.
3. **30% coverage requirement is too low** — we achieved 66% easily, proving the bar should be higher.
4. **connect feedback with backend is harder then we expected**
---

## Friction and gaps

1. **Frontend testing is minimal** — only 3 tests for wardrobe.ts; other React components untested.
2. **Frontend-backend integration problems** — CORS issues, data format mismatches, and async handling required significant debugging.

---

## Planned response

1. **Expand frontend testing** — write tests for App.tsx and core components, target 50% frontend coverage by Sprint 3 end.
2. **Update docs per PBI** — add "Documentation Updated" checkbox to PR template; reviewer verifies before approval.
3. **Close next user stories** — implement US-12 (Weather integration), improve quality of app's work in Sprint 3 with full test coverage.