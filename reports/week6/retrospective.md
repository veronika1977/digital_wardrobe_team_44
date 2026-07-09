# Sprint Retrospective — Week 6

**Author:** @CatherineHar
**Date:** 2026-07-12
**Sprint:** 4 (MVP v2.1.0 Trial Release)
**Release:** [v2.1.0](link)
**Velocity:** 47 SP delivered

## What went well

- **Mid-sprint customer feedback absorption.** Original 29 SP plan plus 4 customer-requested PBIs ([#300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300), [#301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301), [#302](https://github.com/veronika1977/digital_wardrobe_team_44/issues/302), [#303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303)) absorbed without dropping committed scope. Evidence: [Sprint 4 milestone](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/4).
- **UAT scenarios passed during live customer trial.** All 7 maintained scenarios ([UAT-001 to UAT-007](../../docs/user-acceptance-tests.md)) executed successfully. AI fallback ([ADR-004](../../docs/architecture/adr/ADR-004-ai-strategy.md)) and bot inline buttons ([ADR-005](../../docs/architecture/adr/ADR-005-bot-architecture.md)) behaved as documented.
- **Breaking change handled with explicit traceability.** PBI #303 (breaking change to [US-15](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218)) documented in [CHANGELOG.md](../../CHANGELOG.md) under `Changed` category with ADR-005 reference.
- **Honest handover framing accepted.** Reported `Ready for independent use` + `Accepted with follow-up items` ([customer-handover.md](../../docs/customer-handover.md)). Customer confirmed willingness to adopt independently.

## What did not go well

- **Defended wrong UX decisions until customer cited industry patterns.** Navigation order ([#300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300)) and AI-as-button vs AI-as-chat ([#301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301)) both overridden by customer referencing Instagram/Duolingo patterns. Second occurrence after soft-delete badge in Sprint 2 ([#168](https://github.com/veronika1977/digital_wardrobe_team_44/issues/168)).
- **AI Stylist shipped inside-out.** Implemented technically interesting part (Qwen outfit generation, [#217](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217)) but left conversational chat for later. Customer called it "not the core value." PBI #301 corrected this mid-sprint.
- **US-15 built without validating problem framing.** Retrospective "what did you wear today" framing rejected by customer within 2 minutes. Reworked as prospective planning ([#303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303), breaking change to US-15).
- **Handover mechanism assumed, not confirmed.** Assumed GitHub collaborator invite was natural path; customer explicitly preferred ZIP exports due to secrets-hygiene concerns. No sanitized handover package prepared.

## What the team changed or attempted to change based on the previous Sprint Retrospective, and what results they observed

In the [Week 5 retrospective](../week5/retrospective.md), the team committed to:

1. **Add frontend UI testing to Definition of Done** (React Testing Library + MSW, target ≥50% coverage by end of Sprint 4).
   - **Result:** Vitest unit tests added for AI Stylist ([#217](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217)) and bot notification ([#218](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218)) components. Frontend coverage reached 48% (close to target). Full RTL + MSW integration still planned for Sprint 5. Related: [Definition of Done](../../docs/definition-of-done.md), [Testing Status](../../docs/testing.md).

2. **Implement automated OpenAPI contract validation in CI** (fail build if backend endpoint changes break frontend types).
   - **Result:** Not implemented. Deferred to Sprint 5 due to Sprint 4 scope expansion (47 SP vs 29 SP planned) — team prioritized absorbing customer feedback (PBIs #300-303) over infrastructure work. Related: [Development Process](../../docs/development-process.md).

## Action points

1. **Validate UI decisions with customer before implementation, not after.** Any UI decision not backed by established industry pattern must be validated with customer before coding. Rationale recorded in PBI.
   - Related docs: [Definition of Done](../../docs/definition-of-done.md), [Development Process](../../docs/development-process.md)
   - Target: zero customer-overridden UI decisions in Sprint 5

2. **Promote US-16 (monetization) to Sprint 5 must-have.** Following customer's "Sell it" directive, implement Free/Premium (490₽) paywall per [PBI #284](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) acceptance criteria (2nd capsule, 4th outfit, 11th item, locked AI Stylist).
   - Related docs: [Roadmap](../../docs/roadmap.md), [Customer Handover](../../docs/customer-handover.md)
   - Related QR: QR-001 (Response time), QR-002 (Fault tolerance)