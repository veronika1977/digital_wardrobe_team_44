# Sprint Review Summary — Week 6

**Date:** 2026-07-09
**Sprint:** Sprint 4 (06.07.2026 – 12.07.2026)
**Release reviewed:** [v2.1.0](https://github.com/veronika1977/digital_wardrobe_team_44/releases/tag/v2.1.0) (Trial Release)
**Sprint Goal reviewed:** Enable intelligent outfit recommendations and daily wear tracking ([Sprint 4 milestone](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/4))

## Participants

**Team (presenters):**
- Veronika Drozd (Scrum Master)
- Ekaterina Kharamanian (QA / Documentation)
- Evgeniia Zakharova (Frontend)

**Customer:** Attended, actively tested the product during the meeting.

## Artifacts Demonstrated

- **Live product:** [@digital_wardrobe_app_bot](https://t.me/digital_wardrobe_app_bot) (Telegram Mini App)
- **Trial release:** [v2.1.0](https://github.com/veronika1977/digital_wardrobe_team_44/releases/tag/v2.1.0)
- **Documentation reviewed:**
  - [customer-handover.md](../../docs/customer-handover.md)
  - CONTRIBUTING.md and AGENTS.md (across all three repositories)
  - [Hosted documentation site](https://veronika1977.github.io/digital_wardrobe_team_44/)

## Sprint Goal Reviewed

Sprint 4 Goal: deliver AI Stylist integration ([US-14](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217)), daily Telegram bot reminders ([US-15](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218)), fix outfit image display error ([PBI #270](https://github.com/veronika1977/digital_wardrobe_team_44/issues/270)), and add customer-facing documentation.

## Delivered Increment

Demonstrated:
- AI Stylist feature (outfit generation from single prompt)
- Daily bot reminders at 19:00
- Fixed outfit display (grouped sets)
- Outfit layout persistence ([PBI #271](https://github.com/veronika1977/digital_wardrobe_team_44/issues/271))
- "Last worn" tracking in item cards

Issues acknowledged as requiring rework mid-sprint:
- AI Stylist chat interface (became [PBI #301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301))
- Navigation order (became [PBI #300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300))
- Bot reminder framing (became [PBI #303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303))

## UAT Results

All 7 maintained UAT scenarios ([UAT-001 to UAT-007](../../docs/user-acceptance-tests.md)) were executed by the customer during the live trial. Result: **7/7 passed, no critical blockers**.

Two scenarios triggered significant feature-feedback:
- **UAT-006 (AI Stylist):** Passed functionally, but customer called current implementation "not the core value" — chat interface missing.
- **UAT-007 (Bot reminder):** Passed functionally, but customer rejected the retrospective "what did you wear today" framing.

## Customer Feedback

| # | Feedback | Customer quote |
|---|----------|----------------|
| 1 | AI Stylist must be conversational, not a button | "You went through all this effort but didn't implement the core value." |
| 2 | Navigation: Home must be leftmost, AI Stylist in the middle | "Instagram, Duolingo — homepage is always on the left. We read from left to right." |
| 3 | Bot reminder must prompt planning tomorrow, not log today | "It's not like calorie tracking — this is forward-looking." |
| 4 | Home screen needs quick-add button for today's outfit | "Not 'no outfit for today', but a button to set an outfit for today." |
| 5 | Monetization is long-term survival mechanism | "Sell it." |

## Approvals

- **Handover level reached:** `Ready for independent use`
- **Customer confirmation:** `Accepted with follow-up items`
- **Customer quote:** "Finish what we discussed today, and then I think you can start using it independently."
- **Approved features:** "Everything I didn't criticize works as I expected."

## Requested Changes (converted to PBIs)

| Change | PBI | Priority | Sprint |
|--------|-----|----------|--------|
| Add conversational AI chat | [#301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301) | Should Have | Sprint 4 (completed mid-sprint) |
| Reorder navigation (Home left, AI middle) | [#300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300) | Should Have | Sprint 4 (completed mid-sprint) |
| Add "Outfit for Today" widget | [#302](https://github.com/veronika1977/digital_wardrobe_team_44/issues/302) | Should Have | Sprint 4 (completed mid-sprint) |
| Change bot to prompt planning for tomorrow (breaking change to US-15) | [#303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) | Must Have | Sprint 4 (completed mid-sprint) |
| Implement monetization (490₽ Premium) | [#284](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) | Should Have | Sprint 5 |

## Action Points

| # | Action | Owner | Deadline |
|---|--------|-------|----------|
| 1 | Ship US-16 (monetization) as Sprint 5 must-have | @Mrxfg | Before v3.0.0 |
| 2 | Prepare sanitized ZIP handover package | @veronika1977 | Before final Week 7 meeting |
| 3 | Validate UI decisions with customer before implementation | Team | Ongoing Sprint 5 |

## Risks

1. **Sprint 4 scope expanded mid-sprint** from 29 SP to 47 SP. Team absorbed all 4 customer-requested PBIs without dropping committed scope, but future sprints should explicitly reserve capacity for feedback.
2. **US-15 breaking change (PBI #303)** shipped in same sprint as original US-15. Documented explicitly in [CHANGELOG.md](../../CHANGELOG.md) under `Changed` category with ADR-005 reference.
3. **Handover ZIP package not yet prepared.** Customer prefers ZIP over GitHub collaborator access due to secrets-hygiene concerns.

## Resulting Product Backlog Changes

### Added mid-sprint (completed before v2.1.0)
- [#300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300) — Reorder navigation
- [#301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301) — Conversational AI chat
- [#302](https://github.com/veronika1977/digital_wardrobe_team_44/issues/302) — Outfit for Today widget
- [#303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) — Bot prompts planning (breaking change to US-15)

### Confirmed for Sprint 5
- [#284](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) (US-16) — Monetization (490₽ one-time Premium)

## Publication Status

- **Recording permitted:** Yes (customer consented before session start)
- **Public transcript publication permitted:** Yes — sanitized transcript published in [`sprint-review-transcript.md`](./sprint-review-transcript.md)
- **Private instructor sharing:** Full recording and exact private timecodes submitted via Moodle