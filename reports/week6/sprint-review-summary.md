# Sprint Review Summary

**Date:** 2026-07-09

**Participants:** Veronika Drozd, Ekaterina Kharamanian, Evgeniia Zakharova

## Sprint Goal Reviewed
The Sprint Goal for MVP Version 2 was presented: deliver two key user stories – AI stylist integration and daily reminders from the Telegram bot. The team also fixed the outfit image display error reported in the previous review and added documentation.

## Delivered Increment Discussed
The team demonstrated the following implemented functionality:
- AI stylist feature (outfit generation based on a single prompt)
- Daily reminders from the Telegram bot (default at 7 PM)
- Fixed outfit image display error
- Item addition with photo upload
- "Last worn" tracking in item cards

Issues acknowledged as work in progress:
- AI stylist - chat functionality needs to be added
- Home icon placement – customer requested it to be on the left (standard UX pattern)
- Bot reminder logic needs refinement (planning vs. tracking)

# UAT

## Feedback
AI stylist:
- Current implementation neededs several changes, such as AI-chat addition with prompt to talk with stylist.
Navigation:
- The homepage button should be on the left of navigationpanel, as a standart UX pattern
Bot notifications:
- Current notification system needs to be changes, since custoer wanted to plan outfits rather than mark clothes items which already were worn.
Item management\statistics:
- There should be a button to add an outfit for today, in case it was not planned, to make it more convinient

## Approvals
The customer approved the MVP Version 2 increment as presented and confirmed that the sprint and tasks look good.

## Requested changes
- Add chat functionality to the AI stylist
- Move home icon to the left in the bottom navigation bar
- Change bot notification to evening (planning for tomorrow) instead of morning (tracking today)
- Remove manual "mark worn today" feature – outfits should be auto-tracked when planned
- Add a direct button on the main panel to set an outfit for today

## Action Points
1. The team will add a chat interface to the AI stylist.
2. The team will move the home icon to the left in the bottom navigation bar.
3. The team will change bot notification timing to evening (planning for tomorrow).
4. The team will remove the manual "mark worn today" feature.
5. The team will add a direct button on the main panel to set an outfit for today.

## Transition Discussion
**Handover readiness:** Product assessed as partially ready, for full handover team needs to complete all requested changes.

**Handover format and access:** ZIP export, GitHub access (2 relevant repositories) for designated contact, the customer already has access to VM there all relevant files are located.

**Final approval:** Product ready after Week 7 changes, provided no further modifications requested, except those marked in backlog for the next sprint.

## Resulting Product Backlog or Scope Changes
Added to backlog:
- AI stylist chat functionality
- Move home icon to the left in bottom navigation
- Change bot notification to evening (planning)
- Remove manual "mark worn today" feature
- Add direct "set outfit for today" button on main panel

Confirmed for future sprints:
- Monetization (subscription model)
  
## Publication Status

- **Recording permitted:** Yes, customer consented to recording before session start.
- **Public transcript publication permitted:** Yes, sanitized transcript published in [`sprint-review-transcript.md`](./sprint-review-transcript.md).
- **Private instructor sharing:** Full recording and exact timecodes submitted via Moodle private channel.
