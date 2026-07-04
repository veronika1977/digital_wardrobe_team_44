# Sprint Review Summary

**Date:** 2026-07-03
**Participants:** Veronika Drozd, Ekaterina Kharamanian, Evgeniia Zakharova

## Sprint Goal Reviewed

The Sprint Goal for MVP Version 2 was presented: deliver two key user stories – weather integration and built-in outfit planning with the calendar. The team also created architectural documentation (three UML diagrams: Static, Dynamic, and Deployment) and linked all technical decisions to quality requirements.

## Delivered Increment Discussed

The team demonstrated the following implemented functionality:
- Welcome Page with geolocation-based weather display
- City selection for weather (manual or automatic via GPS)
- Calendar view with outfit planning capability

The following issues were acknowledged as work in progress:
- Outfit arrangement does not save correctly (needs to preserve user layout)
- Outfits and capsules are not yet synced
- Weather city selection button is not visible for some users
- Backend not fully implemented for outfit loading via calendar

**Traceability:**

- US-12 (Weather): [#82](https://github.com/veronika1977/digital_wardrobe_team_44/issues/82) → [PR #243](https://github.com/veronika1977/digital_wardrobe_team_44/pull/243)
- US-13 (Calendar): [#216](https://github.com/veronika1977/digital_wardrobe_team_44/issues/216) → [PR #252](https://github.com/veronika1977/digital_wardrobe_team_44/pull/252)
- Sprint 3 Milestone: [Link](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/3)
- Related PBIs: [#270](https://github.com/veronika1977/digital_wardrobe_team_44/issues/270) (grouped outfits), [#271](https://github.com/veronika1977/digital_wardrobe_team_44/issues/271) (layout persistence)


---

# UAT

## Results

**Date of UAT interview:** 2026-07-03

**Participants:** Veronika Drozd, Ekaterina Kharamanian, Evgeniia Zakharova

### Which UAT scenarios passed:

- **UAT-001:** Add Clothing Item with Photo — PASSED
- **UAT-002:** Delete Item and Verify in Cart — PASSED
- **UAT-003:** Filter Wardrobe by Season — PASSED
- **UAT-004:** See topical weather in current location — PASSED
- **UAT-005:** Plan outfits on Calendar - PASSED

### Post-UAT Adjustments & Notes:

- **UAT-004:** The customer didn't have geolocation access on their laptop, so the weather wasn't showing automatically. Also, during testing, we didn't have a button to manually change the geolocation. To ensure the client had everything working on their computer, we fixed the button visibility bug immediately after UAT.

---
## Architecture Evidence Discussed
The team presented the following architectural artifacts:
- Three UML diagrams: Static, Dynamic, and one Deployment
- Documentation linking all technical decisions to quality requirements
- Technical stack includes rembg library – identified as a potential performance risk

## Feedback
Positive:
- Overall, the customer likes the application
- The weather functionality works
- The interface is improving

Improvement requests:

- Fix outfit arrangement saving to preserve user layout
- Fix outfit loading from calendar – should display as full outfit, not as separate items
- Add a direct button on the main panel to load an outfit for today
- Fix city selection button visibility for weather
- Consider AI enhancement for image standardization (future improvement)

## Approvals

The customer approved the MVP Version 2 increment as presented and confirmed that the sprint and tasks look good. 

## Requested changes

- Fix outfit arrangement saving to preserve user layout.
- Fix outfit loading from calendar to display as complete outfits rather than separate items and capsules.
- Add a direct button on the main panel to load an outfit for today.
- Fix city selection button visibility for weather.
- Consider implementing AI image standardization for casual photos to studio quality

## Risks
The rembg library may slow down CPU with traffic growth

## Action Points
1. The team will fix outfit arrangement saving to preserve user layout.
2. The team will fix outfit loading from calendar to display as complete outfits.
3. The team will add a direct button on the main panel to load an outfit for today.
4. The team will fix the city selection button visibility for weather.
5. The team will consider implementing AI image standardization (time permitting).
6. The team will continue work on calendar, outfit planning, and bot notifications in subsequent sprints.

## Resulting Product Backlog or Scope Changes

Added to backlog:
- Fix outfit arrangement saving
- Fix outfit loading from calendar
- Add direct "load outfit for today" button on main panel
- Fix city selection button visibility
- AI image standardization (consideration)

Confirmed for future sprints:
- AI stylist integration
- Telegram bot notifications (reminders for forgotten outfits)
- Further calendar and outfit planning enhancements

## Publication Status

- **Recording permitted:** Yes, customer consented to recording before session start.
- **Public transcript publication permitted:** Yes, sanitized transcript published in [`sprint-review-transcript.md`](./sprint-review-transcript.md).
- **Private instructor sharing:** Full recording and exact timecodes submitted via Moodle private channel.
