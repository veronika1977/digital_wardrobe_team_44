# Changelog

All notable changes to the Digital Wardrobe project will be documented in this file.

## [Unreleased]

## [3.0.0] - 2026-07-16

MVP v3 — Final Course Version: Monetization, Conversational AI Chat, Prospective Bot Planning

### Added

- **Monetization (US-16):** Free/Premium tier system with Telegram Payments integration for 490₽ one-time Premium upgrade ([#284](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284))
  - Backend: Free tier limits enforcement (1 capsule, 3 outfits, 10 items, no AI Stylist), payment processing API, usage stats endpoints ([#285](https://github.com/veronika1977/digital_wardrobe_team_44/issues/285))
  - Frontend: Paywall screens on limit breach, one-tap upgrade flow via Telegram Payments, Premium status indicator and usage meter ([#286](https://github.com/veronika1977/digital_wardrobe_team_44/issues/286))
- **Conversational AI Chat Frontend (PBI #322):** Chat interface for AI Stylist with context-aware responses, completing backend API from Sprint 4 ([#322](https://github.com/veronika1977/digital_wardrobe_team_44/issues/322))

### Changed

- **Bot Reminder Reframed (PBI #303):** Daily 19:00 notification now prompts planning tomorrow's outfit instead of logging today's worn items (breaking change to US-15) ([#303](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303))
  - If tomorrow has no planned outfit → "Choose an outfit for tomorrow"
  - If tomorrow has a planned outfit → "Tomorrow you have outfit X"
  - Planned outfits auto-marked as worn on target date
  - Removed retrospective "log worn items" modal from frontend

### Documentation

- Updated `docs/customer-handover.md` with final handover level and customer confirmation status
- Updated `docs/roadmap.md` — Sprint 5 completed, MVP v3 delivered
- Updated `docs/user-stories.md` — US-16 active, US-07 and US-10 removed
- Recorded public sanitized demo video for MVP v3

### Links

- **Release:** [v3.0.0](https://github.com/veronika1977/digital_wardrobe_team_44/releases/tag/v3.0.0)
- **Product:** [@digital_wardrobe_app_bot](https://t.me/digital_wardrobe_app_bot)
- **Hosted Docs:** [GitHub Pages](https://veronika1977.github.io/digital_wardrobe_team_44/)
- **Demo Video:** [Google Drive](https://drive.google.com/drive/folders/1QmeQpMIMS3NxZ2RVd2gaNRPiYpNO2f7B?usp=sharing)
- **Full Changelog:** [CHANGELOG.md](CHANGELOG.md)

## [2.1.0] - 2026-07-10

Sprint 4 Trial Release — AI Stylist & Telegram Bot Notifications for Daily Outfits

### Added

- **AI Stylist (US-14):** Qwen-powered outfit suggestions with occasion-based filtering (work, casual, sport) and graceful fallback when LLM is unavailable ([#217](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217), [ADR-004](docs/architecture/adr/ADR-004-ai-strategy.md))
  - Backend: `POST /api/ai/suggest-outfit` endpoint with 10s timeout, Qwen (DashScope) integration, fallback to versatile wardrobe basics
  - Frontend: AI Stylist screen with occasion selector, loading state, graceful error handling
  - Architecture: Polling-based notification worker, direct HTTP to Telegram Bot API
  - Testing: QRT for response time, fallback strategy tests, integration tests for AI service
  - Docs: ADR-004 (AI Strategy), updated API documentation
- **Telegram Bot Notifications for Daily Outfits (US-15):** Daily reminders at 19:00 (user's local time) with inline buttons for quick wear logging ([#218](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218), [ADR-005](docs/architecture/adr/ADR-005-bot-architecture.md))
- **Conversational AI Chat backend (PBI #301):** Backend API endpoints for conversational AI stylist chat with context-aware responses ([#301](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301))
- **Outfit for Today widget (PBI #302):** Quick-access widget on Home screen for planning today's outfit without navigating to Calendar ([#302](https://github.com/veronika1977/digital_wardrobe_team_44/issues/302))

### Changed

- **Navigation reorder (PBI #300):** Home tab moved to leftmost position, AI Stylist to middle position per customer feedback on UX patterns ([#300](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300))

### Fixed

- Outfits now display as grouped sets instead of individual items ([PBI #270](https://github.com/veronika1977/digital_wardrobe_team_44/issues/270))
- Calendar layout persistence across sessions ([PBI #271](https://github.com/veronika1977/digital_wardrobe_team_44/issues/271))

## [2.0.0] - 2026-07-03

### Added

- **US-12: Weather Integration**
  - Backend: `GET /api/user/location` endpoint (extracts coords from Telegram `initData` + supports manual override)
  - Frontend: Direct OpenWeatherMap API calls, weather UI component, hybrid flow (Backend → coords → Frontend → weather)
  - Architecture: Updated Deployment & Component diagrams to reflect hybrid weather flow
  - Docs: Acceptance criteria, QR-001/002 traceability, ADR synchronization
  - Testing: QRT-004 automated test (`test_qr004_weather_location.py`), UAT-004 passed

- **US-13: Calendar Planning**
  - Backend: Capsule/outfit CRUD endpoints with date sync (`/api/capsules`, `/api/outfits`)
  - Frontend: Calendar view with green date highlight, instant save, outfit preview modal
  - Architecture: Updated Static & Dynamic and Deployment views to include calendar flow
  - Docs: Acceptance criteria, QR-001/002 traceability, ADR synchronization
  - Testing: QRT-005 automated test (`test_qr005_calendar_outfit.py`), UAT-005 passed

### Changed

- Aligned CI/CD quality gates with QR-003 (≥30% critical module coverage minimum)
- Finalized ADR-001/002/003 with explicit Quality Requirements Impact sections
- Updated `docs/testing.md`, `docs/quality-requirements.md`, `docs/definition-of-done.md` for MVP v2 scope

### Documentation

- Added Traceability Matrix (`ADR ↔ QR ↔ Views`) to `docs/architecture/README.md`
- Completed `docs/development-process.md` (branching, PR workflow, CI/CD, release strategy)
- Added MVP v2 Testing Scope + Evidence Summary to `docs/testing.md`
- Added QRT-004/005 with evidence links to `docs/quality-requirement-tests.md`
- Added MVP v2 Verification Summary to `docs/quality-requirements.md`
- Added MVP v2 Additions checklist to `docs/definition-of-done.md`

## [1.1.0] - 2026-06-25

### Added

- Confirmation dialog for restoring items from cart (PBI #169)
- **US-08: Automatic Background Removal** — integrated Rembg AI to automatically remove backgrounds from uploaded clothing photos [#86](https://github.com/veronika1977/digital_wardrobe_team_44/issues/86)
  - Unified `/upload` endpoint: accepts image, processes it, saves both original and processed versions
  - Processing time < 5 seconds for standard images (validates QR-001)
  - Fault-tolerant design: if Rembg fails or times out, original photo is retained (validates QR-002)
  - Backend: CPU-optimized `rembg` integration, model pre-downloaded during Docker build, strict file validation (JPEG/PNG only)
  - Frontend: Upload flow with loading state
  - backend integration tests covering success paths, fallback scenarios, invalid inputs, and timeout handling
- **US-05: Capsule Wardrobes** — users can create named capsule collections (e.g., "Office", "Vacation") to group clothing items by occasion [#88](https://github.com/veronika1977/digital_wardrobe_team_44/issues/88)
  - Full CRUD lifecycle: create, view details, edit (add/remove items), and delete capsules
  - Deleting a capsule preserves all clothing items in the main wardrobe (soft-delete protection)
  - Backend: new `capsules` and `capsule_items` tables, REST API (`POST/GET/PUT/DELETE /api/capsules`)
  - Frontend: creation modal, multi-select item picker, capsule gallery view
  - Validation: prevents duplicate names, requires at least 1 item, isolates capsules per user

-  **Quality Requirements & CI/CD** — established automated quality gates based on ISO/IEC 25010 in backend repository (https://github.com/Mrxfg/digital-wardrobe/pull/27)
  - QR-001 (Time Behaviour): API response time < 3 seconds, verified by QRT-001
  - QR-002 (Fault Tolerance): Rembg failures preserve original photo, verified by QRT-002
  - QR-003 (Testability): test coverage ≥ 30%, achieved 66%, verified by QRT-003
  - Backend CI pipeline with 7 quality gates (linting, type checking, build, unit tests, integration tests, QRT, security scan)
  - Frontend CI pipeline with linting, type checking, build, and Vitest unit tests
  - Branch protection rules on all 3 repositories (main branch requires PR + 1 review + passing CI)
  - Lychee link checker for documentation with narrow, justified exclusions

### Changed

- Replaced small delete badge (✕) with explicit "Удалить" button on item cards (PBI #168)
- Replaced color text labels with visual color swatches (PBI #179)
- **US-06: Edit Clothing Item** — users can now modify all attributes of an existing clothing item after creation [#101](https://github.com/veronika1977/digital_wardrobe_team_44/issues/101)
  - Edit form pre-fills current values and applies the same validation rules as creation
  - Supports editing: name, category, season, color, material, and photo
  - Photo replacement triggers automatic background removal
  - Backend: `PUT /api/items/{id}` endpoint with transactional updates and optimistic concurrency
  - Frontend: edit button on item detail, responsive form with save/cancel, instant UI refresh
  - Changes propagate immediately to wardrobe grid, capsules, and season filters

## [1.0.0] - 2026-06-21
### Added
- Team Definition of Done (`docs/definition-of-done.md`)
- User Stories Registry (`docs/user-stories.md`)
- Product Roadmap (`docs/roadmap.md`)
- GitHub Issue Templates
- Initial README with setup instructions
- Added possibility to log in to the Digital Wardrobe Mini App using their Telegram account without any registration forms. Includes welcome page, onboarding flow, and automatic redirect to the Home page after successful authentication [#105](https://github.com/veronika1977/digital_wardrobe_team_44/issues/105#issue-4685504661)
- Added a delete button to clothing item cards in the wardrobe view, allowing users to remove items with visual feedback and error handling [#77](https://github.com/veronika1977/digital_wardrobe_team_44/issues/77#issue-4674006802)
- Added tagging system for clothing items (category, season, material, color) and wardrobe filtering by tags [#87](https://github.com/veronika1977/digital_wardrobe_team_44/issues/87#issue-4678207198)
- Added the ability to upload photos and create new clothing items with category, colors, materials and season selection [#85](https://github.com/veronika1977/digital_wardrobe_team_44/issues/85#issue-4678164428)
- UI Kit and Design System [#98](https://github.com/veronika1977/digital_wardrobe_team_44/issues/98#issue-4684187410)
- Telegram Bot Setup [#94](https://github.com/veronika1977/digital_wardrobe_team_44/issues/94#issue-4683945852), [#95](https://github.com/veronika1977/digital_wardrobe_team_44/issues/95#issue-4683990483)

### Changed

- Initial release of the Digital Wardrobe Telegram Mini App (MVP v1).