# User Acceptance Tests — Digital Wardrobe

This document defines end-user-facing scenarios for customer validation.

**Last updated:** July 18, 2026  
**Author:** @veronika1977  
**Reviewer:** @CatherineHar

---

## UAT-001: Add a New Clothing Item with Photo

**Status:** Active

**User goal:** Add a new clothing item to the wardrobe with a photo and attributes.

**Preconditions:**

- User is logged in via Telegram Mini App
- User has at least one photo of a clothing item on their device
- Wardrobe is not empty (at least 1 item exists)

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Navigate to the "Гардероб" (Wardrobe) screen
3. Tap the "+ Добавить вещь" (Add item) button
4. Tap "Выбрать фото" (Choose photo) and select an image from device
5. Verify photo preview is displayed
6. Enter item name: "футболка"
7. Select category: "Верх" (Top)
8. Select season: "Демисезон" (Demiseason) — *Note: Later renamed to "Base" per PBI #170*
9. Select color: "Зелёный" (Green)
10. Select material: "Хлопок" (Cotton)
11. Tap "Сохранить" (Save) button
12. Verify the item appears in the wardrobe gallery

**Expected outcome:**

- Photo is displayed correctly in the gallery
- Item name "футболка" is visible under the photo
- All selected attributes (category, season, color, material) are saved
- Item appears in the wardrobe grid immediately after saving

**Execution results:**

- Date: 25.06.2026
- Executed by: Customer
- Result: Passed
- Customer comments: 
    - "Adding items is intuitive"
    - "I'd like to see the actual color, not just the word 'blue'"
- Follow-up PBI or issue:
   - PBI #179: Replace color text label with color swatch

---

## UAT-002: Delete an Item and Verify It Appears in Cart

**Status:** Active

**User goal:** Delete a clothing item and verify it moves to the cart (soft delete with 14-day retention).

**Preconditions:**
- User is logged in
- Wardrobe contains at least one item
- User is on the Wardrobe screen

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Navigate to the "Гардероб" (Wardrobe) screen
3. Find any item in the gallery
4.  Tap the "Удалить" button on the item card
5. Confirm deletion in the modal dialog: "Переместить в корзину?"
6. Verify the item disappears from the wardrobe gallery
7. Tap the cart icon in the header
8. Navigate to the "Корзина" (Cart) screen
9. Verify the deleted item appears in the cart
10. Verify the info banner shows: "Вещи хранятся в корзине 14 дней, после чего удаляются автоматически"
11. Tap the restore button (return arrow) on the item
12. Verify the item returns to the wardrobe gallery

**Expected outcome:**

- Deleted item is no longer visible in the main wardrobe
- Deleted item appears in the cart with restore option
- Info banner about 14-day retention is visible
- Restored item reappears in the wardrobe gallery

**Execution results:**

- Date: 25.06.2026
- Executed by: Customer
- Result: Passed
- Customer comments:
    - "Replace delete badge with explicit 'Delete' button"
- Follow-up PBI or issue:
    - PBI #168 : Replace delete badge with explicit "Delete" button
    - PBI #169: Add confirmation dialog for restore from cart
 
---

## UAT-003: Filter Wardrobe Items by Season

**Status:** Active

**User goal:** Filter wardrobe items by season to find relevant clothing for the current weather.

**Preconditions:**

- User is logged in
- Wardrobe contains items with different seasons (at least 2 different seasons)
- User is on the Wardrobe screen

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Navigate to the "Гардероб" (Wardrobe) screen
3. Verify the total item count is displayed (e.g., "Всего вещей: 10")
4. Tap the "Сезон" (Season) filter dropdown
5. Select "Осень" (Autumn) from the list
6. Observe the filtered results
7. Verify only items with season="Осень" are displayed
8. Verify the item count updates to show filtered total
9. Tap the "Сезон" filter again
10. Click on the filter name 
11. Verify all items are displayed again

**Expected outcome:**

- After selecting a season filter, only matching items are shown
- Item count reflects the filtered total (not the original total)
- Clearing the filter restores the full wardrobe view
- Filter works without page reload (instant UI update)

**Execution results:**

- Date: 25.06.2026
- Executed by: Customer
- Result: Passed
- Customer comments:
    - No problems, all good

---

## UAT-004: See topical weather in current location (US-12)

**Status:** Active

**User goal:** View current weather for location to make informed outfit decisions.

**Preconditions:**

- User is logged in via Telegram Mini App
- User allowed use his location or type it manually
- Frontend has valid weather API configuration

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Observe the weather widget on the main screen
3. Verify temperature, weather icons
4. Check network logs (dev tools) to confirm direct call to OpenWeatherMap API
5. (Optional) Change manual location
6. (Optional) Return to Home screen and verify weather updates to new coordinates

**Expected outcome:**

- Weather data loads in < 3 seconds (QR-001)
- Frontend calls OpenWeatherMap directly using backend-provided coordinates
- Manual location overrides Telegram location correctly

**Execution results:**

- Date: 03.07.2026
- Executed by: Customer
- Result: Passed
- Customer comments: Weather loads <3s and displays accurate local conditions. Geolocation button was initially hidden due to device permissions; fallback to manual city selection verified and button visibility fixed post-UAT.

---

## UAT-005: Plan outfits on Calendar (US-13)

**Status:** Active

**User goal:** Schedule outfits for specific dates using the calendar view to plan daily looks.

**Preconditions:**

- User is logged in via Telegram Mini App
- Wardrobe contains at least 2 clothing items
- User is on the Calendar screen

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Navigate to the main screen with "Календарь" (Calendar) widget
3. Tap on a future date (e.g., tomorrow) or on today (if there is no outfit)
4. Tap "Создать новый образ" (Create Outfit) or choose from existing outfits
5. Select outfit or create
6. Tap "Сохранить" (Save)
7. Verify the selected date turns green
8. Click on this day and verify the outfit preview appears on the selected date

**Expected outcome:**

- Outfit is saved and visually pinned to the selected date
- Date become green 
- Calendar updates instantly without page reload
- Operation completes in < 3 seconds (QR-001)

**Execution results:**

- Date: 03.07.2026
- Executed by: Customer
- Result: Passed
- Customer comments: Core scheduling works and dates highlight correctly. Noted UX gaps: outfit arrangement not preserved, outfits load as individual items instead of grouped sets. All feedback captured as PBIs for next Sprints.

---

## UAT-006: AI Stylist generates outfit suggestions (US-14)

**Status:** Active

**User goal:** Receive AI-powered outfits recommendations based on wardrobe.

**Preconditions:**

- User is logged in via Telegram Mini App
- Wardrobe contains at least 3 items with varied categories/seasons
- AI integration is enabled (DASHSCOPE_API_KEY configured)

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Navigate to the AI Stylist screen
3. Tap "Generate Outfit"
4. Wait for response
5. Review suggested outfits
6. (Optional) Tap "Save" on a suggested outfit
7. (Optional) Trigger fallback by temporarily blocking AI endpoint (for team testing)

**Expected outcome:**

- Response returns within 5 seconds
- 3 completed outfits are displayed
- If AI fails, fallback returns versatile wardrobe basics with clear message
- Saved outfit appears in outfits

**Assignment 6 (Week 6) Execution results:**

- Date: 09.07.2026
- Executed by: Customer during trial meeting
- Result: Passed (functionally)
- Customer comments:
    - *"Not just a generic model like DeepSeek, but a stylist who understands color theory, materials, and how to combine them."*
    - AI Stylist works, but the feature is "not the core value" without conversational chat interface. Customer expects a chat with System Prompt, not just a button.
- Follow-up PBI or issue:
    - [PBI #301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301): Add conversational AI chat to AI Stylist in backend
    - [PBI #322](https://github.com/veronika1977/digital_wardrobe_team_44/issues/322#issue-4849508694): Add conversational AI chat to AI Stylist in frontend

---

## UAT-007: Receive daily 19:00 bot reminder and plan tomorrow's outfit (US-15, post-PBI #303)

**Status:** Active

**User goal:** Receive a daily Telegram reminder to plan tomorrow's outfit and quickly set it via inline buttons.

**Note:** This scenario describes the current (post-Sprint 4) behavior after PBI #303. The historical version tested on 09.07.2026 asked "what did you wear today" — that framing was rejected by the customer and replaced with prospective planning. See Execution results below.

**Preconditions:**

- User is logged in via Telegram Mini App
- User has at least one planned outfit in Calendar or Wardrobe
- Notification preferences are enabled (default)

**Steps:**

1. Wait for 19:00 notification
2. Message: "Не забудьте запланировать образ на завтра! Что вы будете носить?"
3. Inline buttons: "Выбрать образ"
4. Tap "Выбрать образ" → verify Mini App opens screen with items
5. Select or create a new outfit from the wardrobe items
6. Plan outfit for tomorrow
7. Navigate to the Calendar screen and verify the outfit is saved to tomorrow's date
8. Verify all items in the planned outfit are auto-marked as worn on tomorrow's date

**Expected outcome:**

- Message arrives at 19:00
- Inline buttons are clickable and responsive
- Prospective planning (plan tomorrow)
- Auto-marking planned outfits as worn
- No separate "log worn today" flow

**Assignment 6 (Week 6) Execution results:**

- Date: 09.07.2026
- Executed by: Customer during trial meeting (simulated time trigger + real delivery test)
- Result: Passed (functionally) — but framing rejected by customer
- Customer comments:
    - *"It's not like calorie tracking where you mark what you ate today — this is forward-looking."*
    - *"If there's no outfit for the next day, it sends a reminder to choose an outfit for tomorrow. And if there is an outfit, it sends a morning notification saying 'Today you have outfit X.'"*
    - Customer rejected retrospective "what did you wear today" framing; specified prospective planning behavior implemented in PBI #303.
- Follow-up PBI or issue:
    - [PBI #303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303): Change bot reminder to prompt planning for tomorrow (breaking change to US-15)

---

## UAT-008: Monetization Paywall for Free Tier Users

**Status:** Active

**User goal:** Verify that free tier limits are enforced and paywall is displayed correctly.

**Preconditions:**

- User is logged in as free tier user
- User has reached at least one free tier limit (e.g., 10 items, 3 outfits, 1 capsule)

**Steps:**

1. Open Digital Wardrobe Mini App
2. Attempt to add an 11th clothing item (or create 2nd capsule / 4th outfit / open AI Stylist)
3. Verify paywall screen appears with message about specific limit
4. Verify "Upgrade to Premium" button is visible and clickable
5. Tap "Upgrade to Premium" → verify Telegram Payments flow initiates

**Expected outcome:**

- Creation/addition is blocked before paywall
- Paywall shows correct limit message (e.g., "Free tier allows only 10 items")
- Upgrade button opens Telegram Payments
- No data loss or error state during blocking

**Execution results:**
- Date: 18.07.2026
- Executed by: Customer
- Result: Passed
- Customer comments: Verified free tier limits (1 capsule, 10 items, 3 outfits). Paywall displays correctly with upgrade prompt.
- Follow-up PBI or issue: —


## UAT-009: Premium Upgrade via Telegram Payments

**Status:** Active

**User goal:** Upgrade from Free to Premium tier using Telegram Payments.

**Preconditions:**

- User is logged in as free tier user
- User has seen paywall screen (UAT-008)

**Steps:**

1. Open Digital Wardrobe Mini App
2. Trigger any free tier limit to see paywall
3. Tap "Upgrade to Premium" button
4. Verify Telegram Payments sheet opens with 490₽ price
5. Complete payment flow (promocode or real card)
6. Return to app
7. Verify previously blocked action now works without paywall

**Expected outcome:**

- Telegram Payments initiates correctly with 490₽
- After successful payment, Premium badge visible
- All free tier limits removed immediately
- No duplicate charges or error states

**Execution results:**

- Date: 18.07.2026
- Executed by: Customer
- Result: Passed
- Customer comments: Activated Premium via promo code
- Follow-up PBI or issue: —

## UAT-010: Conversational AI Stylist Chat

**Status:** Active

**User goal:** Get personalized styling advice through conversational chat interface.

**Preconditions:**

- User is logged in as Premium user (AI Stylist unlocked)
- Wardrobe contains at least 3 items

**Steps:**
1. Navigate to AI Stylist screen
2. Tap "Chat with AI Stylist" button
3. Type "What should I wear for casual Friday at work?"
4. Wait for response (< 5 seconds)
5. Verify response includes specific item recommendations from wardrobe
6. Ask follow-up: "Can I pair this with my blue sneakers?"
7. Verify context-aware response referencing previous outfit

**Expected outcome:**

- Chat interface opens with welcome message
- Response arrives within 5 seconds (QR-001)
- Recommendations reference actual wardrobe items
- Follow-up questions maintain conversation context
- Graceful fallback if AI unavailable (QR-002)

**Execution results:**

- Date: 18.07.2026
- Executed by: Customer
- Result: Passed
- Customer comments: Chat interface opens correctly, responds with wardrobe-based recommendations. Context-aware follow-up working as expected.
- Follow-up PBI or issue: —

## UAT Execution History

| UAT ID | Date | Executed by | Result | Customer Comments | Follow-up PBI |
|--------|------|-------------|--------|-------------------|---------------|
| UAT-001 | 25.06.2026 | Customer | Passed | "I'd like to see the actual color" | [#179](https://github.com/veronika1977/digital_wardrobe_team_44/issues/179) |
| UAT-002 | 25.06.2026 | Customer | Passed | "Delete badge too small" | [#168](https://github.com/veronika1977/digital_wardrobe_team_44/issues/168), [#169](https://github.com/veronika1977/digital_wardrobe_team_44/issues/169) |
| UAT-003 | 25.06.2026 | Customer | Passed | "No problems, all good" | — |
| UAT-004 | 03.07.2026 | Customer | Passed | Weather accurate, fallback verified | [US-12](https://github.com/veronika1977/digital_wardrobe_team_44/issues/82) |
| UAT-005 | 03.07.2026 | Customer | Passed | UX gaps noted | [US-13](https://github.com/veronika1977/digital_wardrobe_team_44/issues/215) |
| UAT-006 | 09.07.2026 | Customer | Passed (functionally) | "Not the core value" — chat missing | [#301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301), [#322](https://github.com/veronika1977/digital_wardrobe_team_44/issues/322) |
| UAT-007 | 09.07.2026 | Customer | Passed (framing rejected) | "Forward-looking, not calorie tracking" | [#303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) |
| UAT-008 | 18.07.2026 | Customer | Passed | Free tier limits verified, paywall correct | — |
| UAT-009 | 18.07.2026 | Customer | Passed | Promo activation works, limits removed | — |
| UAT-010 | 18.07.2026 | Customer | Passed | Chat context-aware, recommendations relevant | — |


---

## Traceability

| UAT ID | Related User Stories | Related Quality Requirements |
|--------|----------------------|------------------------------|
| UAT-001 | [US-02](https://github.com/veronika1977/digital_wardrobe_team_44/issues/85) (Add Clothing Item) | QR-001 (API Response Time) |
| UAT-002 | [US-11](https://github.com/veronika1977/digital_wardrobe_team_44/issues/77) (Delete Item) | QR-002 (Fault Tolerance) |
| UAT-003 | [US-02](https://github.com/veronika1977/digital_wardrobe_team_44/issues/85), [US-04](https://github.com/veronika1977/digital_wardrobe_team_44/issues/87) (Tags/Filter) | QR-001 (API Response Time) |
| UAT-004 | [US-12](https://github.com/veronika1977/digital_wardrobe_team_44/issues/82) (Weather Integration) | QR-001 (Performance), [QRT-004](quality-requirement-tests.md#qrt-004-weather-location) |
| UAT-005 | [US-13](https://github.com/veronika1977/digital_wardrobe_team_44/issues/216) (Calendar Planning) | QR-001 (Time Behaviour), [QRT-005](quality-requirement-tests.md#qrt-005-calendar-outfit) |
| UAT-006 | [US-14](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217) (AI Stylist) | QR-001 (Response time < 5s), QR-002 (Fallback when LLM unavailable) |
| UAT-007 | [US-15](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218) (Bot Notifications) | QR-001 (Response time), QR-002 (Bot fault tolerance) |
| UAT-008 | [US-16](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) (Monetization) | QR-001 (Response time), QR-002 (Fault tolerance) |
| UAT-009 | [US-16](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) (Monetization) | QR-001 (Payment flow < 3s) |
| UAT-010 | [US-14](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217) (AI Stylist Chat) | QR-001 (Response < 5s), QR-002 (Fallback) |