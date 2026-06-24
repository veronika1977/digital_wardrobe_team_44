# User Acceptance Tests — Digital Wardrobe

This document defines end-user-facing scenarios for customer validation.

**Last updated:** June 24, 2026  
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
6. Enter item name: "Blue Denim Jacket"
7. Select category: "Верх" (Top)
8. Select season: "Осень" (Autumn)
9. Select color: "Синий" (Blue)
10. Select material: "Хлопок" (Cotton)
11. Tap "Сохранить" (Save) button
12. Verify the item appears in the wardrobe gallery

**Expected outcome:**

- Photo is displayed correctly in the gallery
- Item name "Blue Denim Jacket" is visible under the photo
- All selected attributes (category, season, color, material) are saved
- Item appears in the wardrobe grid immediately after saving

**Execution results:**

- Date: [TBD]
- Executed by: [Customer name]
- Result: [Pending]
- Customer comments: —
- Follow-up PBI or issue: —

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
4. Tap the delete badge (✕) on the item card
5. Confirm deletion in the modal dialog: "Переместить в корзину?"
6. Verify the item disappears from the wardrobe gallery
7. Tap the cart icon in the header
8. Navigate to the "Корзина" (Cart) screen
9. Verify the deleted item appears in the cart
10. Verify the info banner shows: "Вещи хранятся в корзине 14 дней, после чего удаляются автоматически"
11. Tap the restore button (↩) on the item
12. Verify the item returns to the wardrobe gallery

**Expected outcome:**
- Deleted item is no longer visible in the main wardrobe
- Deleted item appears in the cart with restore option
- Info banner about 14-day retention is visible
- Restored item reappears in the wardrobe gallery

**Execution results:**

- Date: [TBD]
- Executed by: [Customer name]
- Result: [Pending]
- Customer comments: —
- Follow-up PBI or issue: —

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
- Date: [TBD]
- Executed by: [Customer name]
- Result: [Pending]
- Customer comments: —
- Follow-up PBI or issue: —

---

## UAT Execution History

| UAT ID | Date | Executed by | Result | Customer Comments | Follow-up PBI |
|--------|------|-------------|--------|-------------------|---------------|
| UAT-001 | [TBD] | [Customer] | Pending | — | — |
| UAT-002 | [TBD] | [Customer] |  Pending | — | — |
| UAT-003 | [TBD] | [Customer] |  Pending | — | — |

---

## Traceability

| UAT ID | Related User Stories | Related Quality Requirements |
|--------|----------------------|------------------------------|
| UAT-001 | US-02 (Add Clothing Item) | QR-001 (API Response Time) |
| UAT-002 | US-11 (Delete Item) | QR-002 (Fault Tolerance) |
| UAT-003 | US-02, US-04 (Tags/Filter) | QR-001 (API Response Time) |