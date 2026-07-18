# Week 7 Retrospective — Digital Wardrobe

**Sprint:** 5 (Final)
**Date:** 2026-07-18
**Team:** Team 44
**Facilitator:** @CatherineHar

---

## What went well

###  Successful Product Handover & Customer Acceptance
-   Customer explicitly confirmed **"Accepted"** status during the final meeting on 2026-07-18
-   Transitioned to **"Ready for independent use"** handover level as defined in `docs/customer-handover.md`.
-   Customer independently adopted **GitHub Fork Sync** as the delivery method, rejecting ZIP exports. This validates our documentation and repository structure quality.
-   All 6 Sprint 5 follow-up items (#284, #300, #301, #302, #303, #322) were completed and verified by the customer during the live UAT session.

### Complete UAT Validation of MVP v3.0.0
-   All **10 UAT scenarios passed**, including the newly implemented monetization and AI chat flows.
-   Monetization paywall correctly enforced limits (1 capsule, 10 items, 3 outfits) and promo code activation worked instantly.
-   Conversational AI Chat demonstrated context-aware follow-ups, addressing the Week 6 feedback that the button-only interface was "not the core value."
-   Bot reminder successfully reframed to prospective planning (PBI #303), resolving the customer's Week 6 rejection of retrospective logging.


### Effective Feedback-to-Delivery Loop
-   Week 6 trial feedback was converted into traceable PBIs within hours and delivered in Sprint 5.
-   Customer saw their exact requests (navigation reorder, AI chat, bot reframing, outfit widget) implemented and tested in a single sprint cycle.
-   Documentation (`customer-handover.md`, `testing.md`, `user-acceptance-tests.md`) was updated in lockstep with code, enabling smooth handover.

---

## What did not go well

### Coverage Regression During Rapid Feature Development
-   Global backend coverage dropped from **66% to 60%** due to adding monetization, AI chat, and YooMoney integration without parallel test writing.
-   New modules have acceptable but lower coverage: `subscription.py` (38%), `ai_stylist.py` (26%), `yoomoney.py` (20%).
-   Tests were written *after* implementation rather than alongside, creating temporary tech debt and requiring multiple `docs/testing.md` sync iterations.

---

## What the team changed or attempted to change based on the previous Sprint Retrospective, and what results they observed

### From Week 6 Retrospective Action Points

| Previous Action Point | What We Changed | Observed Result |
| :--- | :--- | :--- |
| *"Convert all customer feedback to traceable PBIs immediately"* | Created PBIs #300–303, #322 within hours of Week 6 trial meeting |  All 5 PBIs completed and accepted in Sprint 5; customer confirmed alignment |
| *"Implement monetization before final handover"* | Prioritized US-16 as highest-priority Sprint 5 PBI | Paywall, promo codes, and Telegram Payments verified by customer |
| *"Reframe bot from retrospective to prospective planning"* | Implemented PBI #303 as breaking change to US-15 |  Customer approved new framing: *«Forward-looking, not calorie tracking»* |
| *"Add conversational AI chat, not just button"* | Completed PBI #301 (backend) + #322 (frontend) | Context-aware chat validated in UAT-010; addressed "not core value" feedback |
| *"Prepare handover documentation early"* | Drafted `customer-handover.md` in Week 6, finalized in Week 7 | Customer reviewed docs live |

### Results Summary
All 5 action points from the Week 6 retrospective were **successfully executed**. The team's ability to convert feedback into delivered features within one sprint improved significantly compared to earlier sprints. However, the *process* of executing these changes exposed new gaps (coverage regression, tech debt accumulation) that become the focus of this final retrospective.

---

## Action points

> **Note:** As this is the final sprint, these action points are framed as **lessons learned for future projects** rather than next-sprint improvements.
> ### 1. Write Tests Alongside Code, Not After
-   **Problem:** Coverage dropped 6 percentage points during rapid Sprint 4–5 development because tests were deferred.
-   **Lesson:** Adopt TDD or test-alongside-development practices to prevent coverage regression. Define test acceptance criteria *before* implementation begins.
-   **Future Application:** For any new module, require ≥30% coverage *in the same PR* as the feature code, not as a follow-up task.

### 2. Automate Documentation-CI Metric Synchronization
-   **Problem:** Manual updates to `docs/testing.md` caused repeated discrepancies (66% vs 60%, 4 vs 6 QRTs).
-   **Lesson:** Documentation that references CI metrics should be auto-generated or validated via CI gates. Manual sync is error-prone under deadline pressure.
-   **Future Application:** Create a CI job that extracts coverage/QRT data and either injects it into docs or fails the build if docs are stale.