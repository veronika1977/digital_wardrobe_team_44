# Changelog

All notable changes to the Digital Wardrobe project will be documented in this file.

## [Unreleased]

# [1.1.0] - 2026-06-25
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