# Customer Review Summary

**Date:** 2026-06-18  
**Participants:** Veronika Drozd, Ekaterina Kharamanian, Evgeniia Zakharova - iterviewers

## Scope Reviewed

The team presented MVP Version 1, which includes the following functionality: Login through Telegram, Adding items from files or by taking a photo, manual addition of name and tags (season, material, category), deleting items with 14-day storage in the recycle bin, restoring items from the recycle bin.

The following features were explicitly excluded from MVP Version 1, to add in further versions:

Capsules, Automatic background removal using AI, Weather integration with calendar, Custom tags, AI stylist functionality

## Implemented Progress

The team demonstrated a working Telegram Mini App with the following screens:
- Main screen with calendar and weather placeholders
- Wardrobe view with tabs for clothing
- Item addition flow (name, tags, photo upload)
- Item deletion and restoration via recycle bin
- Outfit creation and deletion
- Search functionality on the main page was identified as unnecessary and will be removed.


## Approvals / Requested Changes

**Approved:**
- The customer explicitly approved MVP Version 1 as presented
- The UX was acknowledged as improved and logical
  
**Requested Changes:** 
- Remove the search bar from the main page – confirmed as unnecessar
- When deleting an item used in an outfit, show a confirmation prompt 
- If an item is deleted from an outfit, the outfit should remain (no automatic deletion)
- customer prefers a daily reminder at 6-7 PM to choose an outfit for tomorrow
- No notifications about items not worn for a long time – instead, provide statistics in the user profile

## Risks

- AI stylist implementation, since the customer requested it recently and the team was not ready
- Backend not yet fully connected to the frontend demo
- Customer has unspecified design concerns
- Potential rework depending on customer feedback from MVP testing

## Action Points

1.The team will remove the search bar from the main page.
2. The team will implement a confirmation prompt when deleting an item that is used in an outfit.
3. The team will ensure the outfit remains intact when items are deleted from it.
4. The team will implement daily notifications at 6-7 PM reminding the user to choose an outfit for tomorrow.
5. The team discussed the unwanted notifications, and came to replacing it with a statistics feature in the user profile (showing wear history).
6. The team will contact Mikhail to obtain an API key for the AI stylist and share it with the team.
7. The team will send the MVP link to the customer for testing and feedback.
8. The customer will provide detailed feedback (critical vs. non-critical) after testing.

## Resulting Product Backlog or Scope Changes:

- Search bar removed from MVP Version 1 scope
- Recycle bin moved to bottom bar
- Confirmation prompt added for deleting items used in outfits
- Daily notification at 6-7 PM added to MVP Version 1 scope
- Statistics feature (wear history) added to product backlog
- AI stylist confirmed as part of the project scope – customer will provide API key
- Custom tags, capsules, background removal, and weather integration remain deferred to future versions
- Sprint 1 backlog currently contains 19 tasks for the current week
