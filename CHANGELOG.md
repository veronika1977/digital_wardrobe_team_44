# Changelog

All notable changes to the Digital Wardrobe project will be documented in this file.

## [Unreleased]

### Added
- Confirmation dialog for restoring items from cart (PBI #169)

### Changed
- Replaced small delete badge (✕) with explicit "Удалить" button on item cards (PBI #168)
- Replaced color text labels with visual color swatches (PBI #179)

## [1.1.0] - 2026-06-27
### Added

- **US-08: Automatic Background Removal** — integrated Rembg AI to automatically remove backgrounds from uploaded clothing photos [#86](https://github.com/veronika1977/digital_wardrobe_team_44/issues/86)
  - Unified `/upload` endpoint: accepts image, processes it, saves both original and processed versions
  - Processing time < 5 seconds for standard images (validates QR-001)
  - Fault-tolerant design: if Rembg fails or times out, original photo is retained (validates QR-002)
  - Backend: CPU-optimized `rembg` integration, model pre-downloaded during Docker build, strict file validation (JPEG/PNG only)
  - Frontend: Upload flow with loading state
  - backend integration tests covering success 

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