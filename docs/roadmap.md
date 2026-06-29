# Product Roadmap: Digital Wardrobe

This document outlines the Sprint-by-Sprint delivery plan for the Digital Wardrobe Telegram Mini App. 
It serves as a lightweight, traceable guide to our delivery cadence.

## Product Vision
To help users easily organize their wardrobe directly in Telegram, without complex registration or extra apps.

## Sprint 1: MVP v1 Core Delivery
- **Milestone:** [Sprint 1](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/1)
- **Dates:** 15.06.2026 – 21.06.2026
- **Sprint Goal:** Deliver a functional MVP v1 that allows users to log in via Telegram, add clothing items with photos, and choose tags.
- **Focus:** Core infrastructure, Telegram auth, and basic item management.

**Planned Items:**

*User Stories:*
- [US-01: Telegram Authentication](https://github.com/veronika1977/digital_wardrobe_team_44/issues/84)
- [US-02: Add Clothing Item with Photo](https://github.com/veronika1977/digital_wardrobe_team_44/issues/85)
- [US-11: Delete Item (Soft Delete)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/77)
- [US-04: Tags for Clothing Items](https://github.com/veronika1977/digital_wardrobe_team_44/issues/87)

*Supporting PBIs (Technical/Infrastructure):*
- [API Documentation and Setup Instructions](https://github.com/veronika1977/digital_wardrobe_team_44/issues/97)
- [Research and document AI background](https://github.com/veronika1977/digital_wardrobe_team_44/issues/96)
- [Create UI Kit and Design System for Telegram Mini App](https://github.com/veronika1977/digital_wardrobe_team_44/issues/98)
- [Setup Telegram Bot API](https://github.com/veronika1977/digital_wardrobe_team_44/issues/94)
- [Create Telegram Bot with /start Command](https://github.com/veronika1977/digital_wardrobe_team_44/issues/95)


## Sprint 2: Organization & Filtering
- **Milestone:** [Sprint 2](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/2)
- **Dates:** 22.06.2026 – 28.06.2026
- **Sprint Goal:** Enable users to organize their added items using tags and edit existing items, improving the usability of the digital wardrobe, 
while establishing quality automation infrastructure (CI/CD, quality requirements, automated tests).
- **Focus:** Item metadata, filtering, and edit capabilities.
- **Release:** v1.1.0 (MVP v2)

**Planned Items:**

- [US-06: Edit Clothing Item](https://github.com/veronika1977/digital_wardrobe_team_44/issues/89)
- [US-05: Capsule Wardrobes](https://github.com/veronika1977/digital_wardrobe_team_44/issues/88)
- [US-08: Automatic Background Removal](https://github.com/veronika1977/digital_wardrobe_team_44/issues/86)

*Customer Feedback PBIs:*

- [#170: Replace "Demiseason" with "Base" Category](https://github.com/veronika1977/digital_wardrobe_team_44/issues/170)
- [#171: Add days remaining counter in basket (frontend)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/171)
- [#172: Days remaining in basket (backend)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/172)

*Quality & Automation Work:*
- CI/CD pipeline configuration for frontend, backend, and docs repositories
- Quality Requirements definition (QR-001, QR-002, QR-003)
- Automated Quality Requirement Tests in backend (QRT-001, QRT-002, QRT-003)
- Unit and integration tests for critical modules in backend (≥30% coverage)
- Branch protection rules for all repositories


## Sprint 3: Assignment 5
- **Milestone:** [Sprint 3](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/3)
- **Dates:** 29.06.2026 – 05.07.2026
- **Sprint Goal:** Deliver MVP v2 with weather information display (US-12) and calendar/outfit planning (US-13), while documenting system architecture through three architectural views, creating ADRs, and establishing hosted documentation.
- **Focus:** Weather display, calendar/outfit planning, architecture documentation, ADRs, hosted docs.
- **Release:** MVP v2

**Planned Items:**

*User Stories:*

**US-12: Weather Integration (5 SP)** — [Issue #82](https://github.com/veronika1977/digital_wardrobe_team_44/issues/82)
- Display current weather on the main screen so users can make informed decisions about what to wear.
- **PBI: Weather API Backend Integration (3 SP)**
  - Integrate OpenWeatherMap API
  - Endpoint: `GET /api/weather?lat={lat}&lon={lon}`
  - Caching (6 hours)
  - Fallback mechanism for API failures
- **PBI: Weather Display Frontend (2 SP)**
  - Weather component on main screen
  - Temperature, icon, description display
  - Manual refresh button
  - Loading and error states

**US-13: Calendar with Outfits (8 SP)** — [Issue #216](https://github.com/veronika1977/digital_wardrobe_team_44/issues/216)
- Plan outfits in a weekly/monthly calendar view so users can organize their wardrobe for the week ahead.
- **PBI: Calendar Backend API (5 SP)**
  - `CalendarEntry` model (date, outfit_id, user_id)
  - CRUD endpoints: `POST/GET/PUT/DELETE /api/calendar`
  - Validation (prevent duplicates)
- **PBI: Calendar UI with Weather Display (3 SP)**
  - Interactive calendar component
  - Display planned outfits on dates
  - Weather forecast integration (icons)
  - Navigation between months

*Architecture Work:*
- Component diagram (static view)
- Sequence diagram (dynamic view)
- Deployment diagram (deployment view)
- 3 Architecture Decision Records (ADRs)
- `docs/development-process.md` with Mermaid gitGraph
- Hosted documentation site (GitHub Pages / Netlify)

*Quality & Testing:*
- Extend tests for US-12, US-13
- Update `docs/testing.md`, `docs/quality-requirement-tests.md`, `docs/definition-of-done.md`

**Total Sprint 3 velocity:** 13 SP (user stories only) + architecture work

## Future Sprints

### Sprint 4: AI Stylist & Daily Wear Tracking
- **Focus:** AI-powered outfit suggestions and daily wear tracking

**Planned User Stories:**
- [US-14: AI Stylist for Outfit Generation](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217) (13 SP)
  - AI-generated outfit suggestions based on wardrobe, weather, and occasion
  - User can save or reject suggestions
  - AI learns from user preferences
- [US-15: Telegram Bot Daily Wear Tracking](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218) (8 SP)
  - Daily reminder at 7:00 PM: "What did you wear today?"
  - Quick marking of worn items
  - Wear statistics and analytics

### Sprint 5: Sharing & AI Material Detection
- **Focus:** Social features and advanced AI capabilities

**Planned User Stories:**
- [US-10: Share Outfit by Link](https://github.com/veronika1977/digital_wardrobe_team_44/issues/91) (3 SP)
  - Share outfits with friends via Telegram
  - Public wardrobe profiles (optional)
- [US-07: AI Material Detection](https://github.com/veronika1977/digital_wardrobe_team_44/issues/90) (13 SP)
  - Automatic material detection from photos
  - Integration with existing material tags

## Removed 

- **US-03:** AI Outfit Generation (Removed: Out of scope for current MVP vision)
- **US-09:** Social Network (Removed: Replaced by simple link sharing in US-10)