# Week 7 Reflection — Digital Wardrobe

**Sprint:** 5 (Final)  
**Date:** 2026-07-18 
**Team:** Team 44  

---

## Learning points

### 1. Customer feedback is the most reliable scope regulator
Throughout Sprints 4–5, every major product pivot came directly from customer validation, not internal assumptions. The bot reminder reframing (PBI #303) was rejected in its original retrospective form during the Week 6 trial and replaced with prospective planning based on explicit customer language: *«It's not like calorie tracking where you mark what you ate today — this is forward-looking»*. Similarly, the AI Stylist evolved from a button-only interface to a conversational chat (PBIs #301 + #322) only after the customer stated it was «not the core value» without dialogue. **Lesson:** UAT is not a checkbox at the end of development; it is the primary mechanism for discovering what the product should actually be. Features that pass functional tests but fail the customer’s mental model are not done.

### 2. Documentation drift is inevitable without automation
The repeated discrepancies between `docs/testing.md` and actual CI output (66% vs 60% coverage, 4 vs 6 QRTs) demonstrated that manually maintained documentation referencing live metrics will always lag under deadline pressure. Each sync iteration consumed time that could have been spent on feature quality or tech debt reduction. **Lesson:** Any documentation that references CI-derived metrics (coverage, test counts, QRT status) must either be auto-generated from CI artifacts or validated by a CI gate that fails when docs are stale. Trusting manual updates is a process risk, not a discipline problem.

### 3. Handover is a design constraint, not an afterthought
The customer’s spontaneous adoption of GitHub Fork Sync over ZIP exports ([16:44–16:57] in final meeting transcript) validated that repository structure and documentation quality directly determine post-course sustainability. Had our repos been poorly organized or our `CONTRIBUTING.md`/`AGENTS.md` incomplete, the customer would have required ZIP archives and ongoing support. **Lesson:** Building for handover from Sprint 1 forces better architectural decisions, cleaner documentation, and more predictable CI/CD. The handover artifact (`customer-handover.md`) is not a deliverable to write at the end; it is a continuous quality bar that shapes every commit.

---

## Validated assumptions

| Assumption | Validation Evidence | Outcome |
| :--- | :--- | :--- |
| Customer prefers self-service code access over manual ZIP delivery | Customer forked repos independently and requested sync notifications instead of ZIPs | Validated — GitHub Fork Sync adopted as primary delivery method |
| Monetization paywall must enforce limits before blocking actions | UAT-008 confirmed free tier blocks at 1 capsule / 10 items / 3 outfits with correct paywall messaging | Validated — paywall UX matches customer expectations |
| Conversational AI chat is more valuable than button-only generation | Customer explicitly stated button interface was «not the core value» in Week 6; UAT-010 confirmed context-aware chat works in Week 7 | Validated — chat interface addresses core styling advisory need |
| Prospective planning aligns with user mental model better than retrospective logging | Customer rejected «what did you wear today» framing; approved PBI #303 prospective reminder | Validated — bot now prompts tomorrow’s outfit, matching forward-looking workflow |
| Documentation set is sufficient for independent use without team support | Customer reviewed all 4 docs live and confirmed: *«Все понятно сразу, вообще идеально»*; formal Accepted status granted | Validated — handover level «Ready for independent use» achieved |
| ≥30% critical module coverage threshold is achievable alongside rapid feature development | All critical modules maintained 72–100% coverage despite adding ~850 lines in Sprints 4–5 | Validated — threshold holds even during high-velocity sprints |

---

## Friction and gaps

### Coverage regression during high-velocity delivery
Global backend coverage dropped from 66% to 60% because tests for monetization (`subscription.py` 38%), AI stylist (`ai_stylist.py` 26%), and YooMoney integration (`yoomoney.py` 20%) were written after implementation rather than alongside it. While all critical modules exceed the 30% threshold, the gap between new-module coverage and established-module coverage reveals that our Definition of Done does not enforce test-first or test-alongside practices under deadline pressure. This created multiple manual sync cycles for `docs/testing.md` and left technical debt that would compound in future sprints.


### Manual documentation-CI synchronization is unsustainable
Every release required manual reconciliation of `docs/testing.md` with CI reality. Historical values (Sprint 2: 66%) conflicted with current metrics, duplicate URLs appeared in evidence links, and QRT counts needed correction across multiple tables. This friction exists because we treat documentation as a static artifact updated by humans rather than a derived artifact validated by automation. Under course deadline pressure, this manual process consumed hours that should have been allocated to testing or tech debt.

---

## Planned response

> **Note:** As this is the final sprint, planned responses are framed as **transferable practices for future projects** rather than next-sprint commitments.

### 1. Enforce test-alongside-development in Definition of Done
For any future project, require ≥30% coverage *in the same PR* as feature code for new modules. Add a CI gate that compares coverage delta against a baseline and warns when new modules fall below threshold. This prevents the coverage regression pattern observed in Sprints 4–5 and eliminates post-hoc test writing as accepted practice.

### 2. Automate documentation-metric synchronization
Create a CI job that extracts coverage, QRT counts, and test totals from pytest/Jest output and either injects them into documentation templates or fails the build when docs diverge from CI reality by more than a defined tolerance. Treat documentation referencing live metrics as generated artifacts, not authored content. This eliminates the manual sync friction that consumed multiple iterations in Week 7.

### 3. Build handover artifacts continuously from Sprint 1
Maintain `customer-handover.md`, `CONTRIBUTING.md`, and `AGENTS.md` as living documents updated each sprint, not final-week deliverables. Use handover readiness as a Definition of Done criterion for every PBI: if a feature cannot be explained in handover docs, it is not done. This ensures repository structure and documentation quality evolve alongside product functionality, making post-course sustainability a design constraint rather than a documentation exercise.
