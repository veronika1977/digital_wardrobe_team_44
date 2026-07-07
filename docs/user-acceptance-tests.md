# User Acceptance Tests — Digital Wardrobe

This document defines end-user-facing scenarios for customer validation.

**Last updated:** July 12, 2026  
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
4. Tap the delete badge (x) on the item card
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
3. Tap on a future date (e.g., tomorrow) on today (if there is no outfit)
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

**User goal:** Receive AI-powered outfit recommendations based on wardrobe, occasion, and context.

**Preconditions:**

- User is logged in via Telegram Mini App
- Wardrobe contains at least 2-4 items with varied categories/seasons
- AI integration is enabled (DASHSCOPE_API_KEY configured)

**Steps:**

1. Open Digital Wardrobe Mini App in Telegram
2. Navigate to the AI Stylist screen
3. Tap "Generate Outfit"
4. Wait for response
5. Review suggested outfit
6. (Optional) Tap "Save" on a suggested outfit
7. (Optional) Trigger fallback by temporarily blocking AI endpoint (for team testing)

**Expected outcome:**

- Response returns within 5 seconds
- complete outfit are displayed
- If AI fails, fallback returns versatile wardrobe basics with clear message
- Saved outfit appears in outfits

**Assignment 6 (Week 6) Execution results:**

- Date: 09.07.2026
- Executed by: Customer during trial meeting
- Result: Passed
- Customer comments: ##
- Follow-up PBI or issue: ##

---

## UAT-007: Receive daily 19:00 bot reminder and log wear (US-15)

**Status:** Active

**User goal:** Receive a daily Telegram reminder and quickly log worn outfits via inline buttons.

**Preconditions:**

- User is logged in via Telegram Mini App
- User has at least one planned outfit in Calendar or Wardrobe
- Notification preferences are enabled (default)

**Steps:**

1. Open Telegram and wait for 19:00 local time notification
2. Verify message arrives: "Что вы носили сегодня?"
3. Verify inline keyboard shows recent outfits
4. Tap an outfit button to log it as worn
5. Tap "Done"
6. Verify confirmation message is received

**Expected outcome:**

- Message arrives at ~19:00 (plus/minus polling delay)
- Inline buttons are clickable and responsive
- Tap logs wear record in database
- Confirmation message confirms successful logging
- Fallback/error handling works if API is temporarily unavailable

**Assignment 6 (Week 6) Execution results:**
- Date: 09.07.2026
- Executed by: Customer during trial meeting (simulated time trigger + real delivery test)
- Result: Passed
- Customer comments: ##
- Follow-up PBI or issue:
   - None

---

## UAT Execution History

| UAT ID | Date | Executed by | Result | Customer Comments | Follow-up PBI |
|--------|------|-------------|--------|-------------------|---------------|
| UAT-001 | 25.06.2026 | Customer | Passed | "I'd like to see the actual color, not just the word 'blue'" | PBI #179 |
| UAT-002 | 25.06.2026 | Customer | Passed | "Delete badge too small; add confirmation for restore" | PBI #168, PBI #169 |
| UAT-003 | 25.06.2026 | Customer | Passed | "No problems, all good" | — |
| UAT-004 | 03.07.2026 | Customer | Passed | Weather accurate, fallback verified | US-12 |
| UAT-005 | 03.07.2026 | Customer | Passed | UX gaps noted, captured as PBIs | US-13 |
| UAT-006 | 09.07.2026 | Customer | Passed | Relevant, needs more variety | - |
| UAT-007 | 09.07.2026 | Customer | Passed | Convenient, inline buttons work | — |

---

## Traceability

| UAT ID | Related User Stories | Related Quality Requirements |
|--------|----------------------|------------------------------|
| UAT-001 | US-02 (Add Clothing Item) | QR-001 (API Response Time) |
| UAT-002 | US-11 (Delete Item) | QR-002 (Fault Tolerance) |
| UAT-003 | US-02, US-04 (Tags/Filter) | QR-001 (API Response Time) |
| UAT-004 | US-12 (Weather Integration) | QR-001 (Performance) |
| UAT-005 | US-13 (Calendar Planning) | QR-001 (Time Behaviour) |
| UAT-006 | US-14 (AI Stylist) | -|
| UAT-007 | US-15 (Bot Notifications) | -|