# Week 6 Reflection — Sprint 4

**Sprint:** Sprint 4 (Week 6, 06.07.2026 – 12.07.2026)
**Release:** v2.1.0 — Trial Release
**Customer meeting date:** 2026-07-09
**Team:** Team 44 — Digital Wardrobe

---

## Learning points

### 1. We defended a wrong UX decision until the customer cited an industry pattern

During the navigation review, the team initially defended placing the AI Stylist icon first in the bottom tab bar. The customer did not argue from personal preference — she cited established mobile UX patterns:

> "Let's look at some social networks or mobile apps. For example, Instagram — we open the homepage, it's on the left. Duolingo — the home icon is on the left... We read from left to right, not from the center outward... There are standard patterns in apps and SaaS — homepage is always on the left, and the profile is always on the right."

We accepted this immediately and created PBI #300. The deeper lesson: when a customer invokes an established industry pattern, the correct team response is to investigate the pattern, not to defend the current implementation. We should have known this pattern ourselves before shipping.

### 2. We built the wrapper but not the core value of the AI feature

The customer asked directly:

> "So you added outfit loading and assembly, but you didn't add a simple chat for communication?"

And then clarified the real product vision:

> "I mentioned System Prompt — it's just a configuration on top of the chat, providing context so it responds as an AI stylist. Not just a generic model like DeepSeek, but a stylist who understands color theory, materials, and how to combine them. You went through all this effort but didn't implement the core value. That's funny."

We had inverted the priority: we treated the LLM call (US-14, ADR-004) as the feature, when the customer treats the conversation as the feature and the LLM call as plumbing. PBI #301 (conversational AI chat with System Prompt for color theory and materials) was created and completed in Sprint 4 to correct this. Lesson: when a feature is marketed as "AI-powered", users expect conversational access to the AI, not just a button that produces output.

### 3. The bot reminder was solving the wrong problem entirely

We implemented US-15 (ADR-005) as a 19:00 prompt asking "what did you wear today?" — framing it like calorie tracking. The customer rejected this framing outright:

> "It's not like calorie tracking where you mark what you ate today — this is forward-looking."

She specified the correct behavior:

- If tomorrow has no planned outfit → "Choose an outfit for tomorrow"
- If tomorrow has a planned outfit → "Tomorrow you have outfit X"
- When a user plans an outfit for a date → all items in that outfit auto-marked as worn on that date (eliminating separate logging)
- The "log worn items" modal should be removed from the frontend entirely: *"I'm removing that window from the frontend entirely."*

This collapsed [PBI #303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) into a breaking change to US-15, completed in Sprint 4. Lesson: features that look analogous to existing popular patterns (calorie tracking) may in fact be the opposite of what the user needs. We should have validated the "retrospective vs. prospective" framing with the customer before implementing US-15.

### 4. The customer wants the product sold, not maintained

When asked how to increase the chance the product remains useful after the course, the customer answered in one word:

> "Sell it."

This was not a throwaway line — it reframed monetization (US-16, [PBI #284](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284), 490₽ one-time Premium tier) from a post-course optional enhancement to a core business expectation. Free tier limits (1 capsule, 3 outfits, 10 items, no AI Stylist) are now understood as a conversion funnel, not arbitrary gating. Lesson: when a customer is a business stakeholder, the business model is part of the product scope, not a separate concern. US-16 is promoted to a Sprint 5 must-have.

### 5. The customer prefers ZIP export over GitHub access for handover

When asked about final handover format, the customer said:

> "I think it's better to export files as a ZIP. You need to have the API files — repositories won't work because API keys shouldn't be in repositories."

This contradicted our assumption that granting a collaborator (Misha) GitHub access was the natural handover path. The customer is specifically concerned about secrets hygiene in the repo history. Sprint 5 must produce a sanitized ZIP export as a first-class handover deliverable.

### 7. Mid-sprint customer feedback can be absorbed if the team reserves capacity

Sprint 4 was originally planned at 29 SP. After the 09.07.2026 meeting, four customer-requested changes (PBIs #300, #301, #302, #303) were absorbed mid-sprint, bringing the total to 47 SP — and all were completed before the v2.1.0 release. This was possible only because no major unplanned technical issues arose. Lesson: rapid iteration on a trial release is expected by customers, and future trial-phase sprints should explicitly reserve 20% capacity for feedback response rather than treating it as emergent work.

---

## Validated assumptions

| # | Assumption | Validated? | Evidence from Week 6 meeting |
|---|-----------|-----------|----------|
| 1 | Qwen via DashScope generates useful outfit suggestions with fallback (ADR-004) | Yes | Customer confirmed outfit assembly works and called it "great" |
| 2 | Telegram inline buttons are a natural UX for quick outfit actions (ADR-005) | Partially | Customer did not object to inline buttons, but reframed the entire reminder flow — the UX question moved up one level |
| 3 | The AI Stylist is a secondary feature behind the Home screen | **No — invalidated** | Customer cited Instagram/Duolingo patterns; [PBI #300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300) completed in Sprint 4 to fix navigation |
| 4 | Outfit generation alone is sufficient AI value | **No — invalidated** | Customer called it "not the core value"; PBI #301 (conversational chat) completed in Sprint 4 |
| 5 | Daily wear logging is the right framing for the bot | **No — invalidated** | Customer rejected calorie-tracking analogy; [PBI #303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) completed in Sprint 4 to reframe as tomorrow-planning |
| 6 | The Home screen needs a "no outfit today" empty state | **No — invalidated** | Customer asked for a quick-add button instead; [PBI #302](https://github.com/veronika1977/digital_wardrobe_team_44/issues/302) completed in Sprint 4 |
| 7 | Monetization is optional / post-course | **No — invalidated** | Customer said "Sell it" when asked about long-term usefulness |
| 8 | GitHub collaborator access is the natural handover mechanism | **No — invalidated** | Customer explicitly preferred ZIP export due to secrets-hygiene concerns |
| 9 | Customer would adopt the product independently after Week 7 | Yes | Customer confirmed: *"Finish what we discussed today, and then I think you can start using it independently"* |

---

## Friction and gaps

### 1. We defended bad decisions instead of investigating them

On navigation (AI icon first vs. Home icon left), the team defended the current implementation before the customer produced the Instagram/Duolingo/pattern argument that resolved the discussion immediately. This is the second time in the course (after the soft-delete badge in Sprint 2, PBI #168) that we defended a UI decision the customer had to override with a stronger argument. The friction was not technical — it was social. We treated the customer's feedback as a preference to be negotiated rather than a UX principle to be researched.

### 2. The AI feature was shipped inside-out

We implemented the most technically interesting part (Qwen-driven outfit generation via DashScope, ADR-004) and left the most user-valuable part (conversational access to the AI) for later. The customer's reaction — *"You went through all this effort but didn't implement the core value."* — was a clear signal that our internal prioritization was inverted. The friction came from treating the LLM call as the feature, rather than treating the conversation as the feature and the LLM call as an implementation detail. [PBI #301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301) corrected this in Sprint 4.

### 3. The bot reminder was built without validating the problem framing

[US-15 (ADR-005)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218#issue-4767227415) was specified as "daily reminders at 19:00 + quick wear logging." We never validated with the customer whether retrospective logging was the right framing. During the Week 6 meeting, the customer rejected the entire framing within two minutes and specified the correct behavior (prospective planning, auto-marking planned outfits as worn, removing the logging modal from frontend entirely). [PBI #303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) corrected this in Sprint 4, but the friction remains a lesson: features that introduce new user rituals (daily, weekly, event-driven) require problem-framing validation with the customer before implementation begins.

---

## Planned response

[**Sprint 5 Milestone**](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/5)

### For Sprint 5 (Week 7):

1. **Promote US-16 (monetization) to a Sprint 5 must-have.** Following the customer's explicit "Sell it" directive, the Free/Premium tier (490₽ one-time) will be treated as a core delivery of Sprint 5, not an optional enhancement. Paywall screens for 2nd capsule, 4th outfit, 11th item, and locked AI Stylist will be implemented per [PBI #284](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) acceptance criteria.

2. **Prepare a sanitized ZIP export as the primary handover package.** Before the final Week 7 meeting, the team will produce two ZIP files (frontend `digital_wardrobe_777`, backend `digital-wardrobe`) with `.env.example` instead of real secrets, no git history, and a `HANDOVER.txt` pointing to the hosted documentation. This will be the handover artifact the customer actually receives, in addition to the GitHub collaborator invite for Misha if she still wants it. A new PBI will be created in Sprint 5 for this.

7. **Treat the handover level and customer-confirmation status as two separate tracked fields.** In `customer-handover.md` for Week 7, we will explicitly maintain both fields as independent dimensions (current state: `Ready for independent use` + `Accepted with follow-up items`) and update them separately based on the final transition confirmation.
