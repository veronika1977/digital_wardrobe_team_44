# Design System — Digital Wardrobe

This document describes the design system for the Digital Wardrobe Telegram Mini App. It serves as the single source of truth for all UI components, colors, typography, and icons.

**Figma File:** [Digital Wardrobe Design System](https://www.figma.com/design/bH3tg2a626fBWdNWXmsB3b/UI-Components?node-id=8-6&t=ooSLwReyyrNfCI4r-1)


## Color Palette

All colors are defined as Variables in Figma. The app uses a light theme only.

| Variable | Hex | Usage |
|---|---|---|
| `bg/primary` | `#E6E5E3` | Main app background |
| `bg/secondary` | `#F5F5F5` | Section backgrounds, filter bars |
| `bg/card` | `#FFFFFF` | Cards (clothing item cards, outfit cards) |
| `border` | `#D4D3D1` | Input borders, card borders, dividers |
| `text/primary` | `#151414` | Headings, button labels, item names |
| `text/secondary` | `#6B6A69` | Subtitles, metadata (season, material) |
| `text/muted` | `#8B8A89` | Placeholders, hints, disabled labels |
| `accent/primary` | `#151414` | Primary buttons, active nav icons |
| `destructive` | `#E57373` | Delete button, error states, trash confirmation |
| `success` | `#4CAF50` | Success confirmations, wear-log checkmarks |


### Icon set

| Icon name | Usage in the app |
|---|---|
| **Cansel** | Dismiss modal, cancel action, clear search field |
| **Search** | Search field trigger in wardrobe and outfits screens |
| **Arrow** | Navigation forward, redirect to outfit builder |
| **Add** | Add item button, add outfit, add to capsule |
| **Person** | Profile tab in bottom navigation |
| **button** (undo/recover) | Restore item from trash (Recover action) |
| **Logo** | Logo |
| **icon** (trash) | Delete item or outfit, move to trash |
| **Home** | Home tab in bottom navigation |
| **More items** | Expand dropdown, show more options |


### Save
- Background: `accent/primary` (`#151414`)
- Label color: `bg/card` (`#FFFFFF`)
- Label: **"Сохранить"**
- **Used for:** saving a clothing item after filling in all fields (UC-1), saving an outfit (UC-2), saving a capsule (UC-6)

 
### Add item
- Background: `accent/primary` (`#151414`)
- Label color: `bg/card` (`#FFFFFF`)
- Label: **"+ Добавить вещь"**
- Full width
- **Used for:** opening the add item flow from the wardrobe screen (UC-1)
---
 
### Choose bar (confirmation modal)
A modal dialog that appears before a destructive action.
- Modal background: `bg/card` (`#FFFFFF`)
- Message text color: `text/primary` (`#151414`)
- Message: **"Переместить в корзину?"**
Two buttons inside:
- **"Да"** — background: `destructive` (`#E57373`), label color: `bg/card` (`#FFFFFF`)
- **"Отмена"** — background: `bg/card` (`#FFFFFF`), label color: `text/primary` (`#151414`), border: `border` (`#D4D3D1`)
**Used for:** confirming item deletion before moving to trash (UC-8). Always shown before any irreversible action.
 

 
### Filtering
A horizontal row of dropdown chips. Each chip shows a label and a **More items** icon.
 
- Active chip — background: `accent/primary` (`#151414`), label color: `bg/card` (`#FFFFFF`), icon color: `bg/card` (`#FFFFFF`)
- Inactive chip — background: `bg/card` (`#FFFFFF`), label color: `text/primary` (`#151414`), border: `border` (`#D4D3D1`), icon color: `text/primary` (`#151414`)
Chips in the set: **Категория**, **Материал**, **Цвет**, **Сезон**
 
**Used for:** filtering the wardrobe item list (UC-9) and outfit list (UC-10).
 
> Note: Material options differ by category — clothing, outerwear, footwear, and accessories each have their own material list. Color options are shared across all categories. Multi-color selection is supported: if a user sets red as one of several colors, the item appears in red-filtered results (UC-9).
 
 
### Category (dropdown)
A full-width dropdown selector.
 
- Background: `bg/secondary` (`#F5F5F5`)
- Label color: `text/primary` (`#151414`)
- Icon (**More items**) color: `text/primary` (`#151414`)
- Border: `border` (`#D4D3D1`)
Dropdowns in the Add item form: **Категория**, **Сезон**, **Цвет**, **Материал**
 
**Used for:** filling in item attributes when adding or editing a clothing item (UC-1).
 
 
### Name item
A full-width text input field.
 
- Background: `bg/secondary` (`#F5F5F5`)
- Border: `border` (`#D4D3D1`)
- Placeholder text color: `text/muted` (`#8B8A89`)
- Input text color: `text/primary` (`#151414`)
- Placeholder: **"Название вещи"**
**Used for:** entering the item name when adding or editing a clothing item (UC-1).
 
---
 
### Add item (photo upload area)
A large tappable area for uploading a photo.
 
- Background: `bg/secondary` (`#F5F5F5`)
- Border: dashed, `border` (`#D4D3D1`)
- **Add** icon color: `text/primary` (`#151414`)
- Label **"Выбрать фото"** color: `text/primary` (`#151414`)
- Hint **"Нажмите, чтобы выбрать файл"** color: `text/muted` (`#8B8A89`)
Accepted formats: jpg, jpeg, png, pdf, up to 10 MB. If the file fails validation, show an inline error in `Caption` style below the area with the exact reason (wrong format or file too large) and accepted requirements. Error text color: `destructive` (`#E57373`).
 
**Used for:** uploading or replacing a clothing item photo (UC-1).
 
 
### Find
A circular icon button.
 
- Background: `bg/card` (`#FFFFFF`)
- **Search** icon color: `text/primary` (`#151414`)
Counter label **"Всего вещей: N"** color: `text/secondary` (`#6B6A69`).
 
**Used for:** opening the search input to find items by name in the wardrobe (UC-9) and outfits screen (UC-10).
 
---
 
### Reco… (Recover)
An icon button using the **button** (undo) icon.
 
- Background: transparent
- Icon color: `text/primary` (`#151414`)
Paired with the **Cansel** icon button to cancel the restore action. Both icons color: `text/primary` (`#151414`).
 
**Used for:** restoring a deleted item or outfit from trash (UC-8).
 
 
### Nav
Bottom navigation bar with two tabs.
 
- Bar background: `bg/card` (`#FFFFFF`)
- Active tab icon color: `accent/primary` (`#151414`)
- Inactive tab icon color: `text/muted` (`#8B8A89`)
Tabs:
- **Home** tab — uses **Home** icon
- **Person** tab — uses **Person** icon
 
### Capsules
Pill-shaped tags showing capsule summary info.
 
- Active state — background: `accent/primary` (`#151414`), label color: `bg/card` (`#FFFFFF`)
- Inactive state — background: `bg/card` (`#FFFFFF`), label color: `text/primary` (`#151414`), border: `border` (`#D4D3D1`)
Examples: **"8 items : 3 outfits"** (active), **"10 items : 5 outfits"** (inactive)
 
**Used for:** selecting or displaying capsules on the capsules screen (UC-6).
 
## Usage Guidelines

### When to use the Choose bar
Show the **Choose bar** ("Переместить в корзину?") before any destructive action. The user must explicitly tap **"Да"** to confirm. Never delete an item without this confirmation step. The **"Отмена"** button must always be present so the user can abort.

### Trash and recovery flow (UC-8)
When a user deletes an item, it moves to trash — it is not permanently deleted immediately. The user must be warned that the item will disappear from any outfits it belongs to. Those outfit slots become empty and can be filled via outfit editing. The **Reco…** button restores the item back to the wardrobe.

### Filtering behavior (UC-9, UC-10)
**Filtering** chips show all available options. Tapping a chip opens its dropdown. To reset a single filter, select the empty or "Все" option inside it. A "Сбросить все фильтры" action removes all active filters at once. The **Find** (Search) field works independently from the filter chips — it filters items by name only.

For outfits, the only filter available is **Сезон** (UC-10). For wardrobe items, all four filters are available: **Категория**, **Материал**, **Цвет**, **Сезон** (UC-9).

### Season and universality logic
Items and outfits can be marked Universal (always visible) or Seasonal (visible only in their active season). The wear counter runs only during the item's active season for seasonal items, and at all times for universal items (UC-5).

### Wear reminders (UC-5)
The "Давно не носишь" block appears on the home screen passively — no push notification. It shows items not worn for more than a month during their active period. From this block the user can either build an outfit with the item or remove it from the wardrobe using the **icon** (trash) button followed by the **Choose bar** confirmation.

### Photo upload (UC-1)
Accepted formats: jpg, jpeg, png, pdf. Max size: 10 MB. If validation fails, show an inline error in `Caption` style below the **Add item** upload area explaining the exact issue and accepted requirements.
