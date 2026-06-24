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
- [#171: Add days remaining counter in basket (frontebd)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/171)
- [#172: Days remaining in basket (backend)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/172)

*Quality & Automation Work:*
- CI/CD pipeline configuration for frontend, backend, and docs repositories
- Quality Requirements definition (QR-001, QR-002, QR-003)
- Automated Quality Requirement Tests in backend (QRT-001, QRT-002, QRT-003)
- Unit and integration tests for critical modules in backend (≥30% coverage)
- Branch protection rules for all repositories


## Sprint 3: Assignment 5
- **Milestone:** [Sprint 3](in Assignment5)
- **Dates:** 29.06.2026 – 05.07.2026
- **Sprint Goal:** Enhance product with weather integration.
- **Focus:** US-12 (Weather Integration),  additional UX improvements.

**Planned Items:**
- [US-12: Weather Integration](https://github.com/veronika1977/digital_wardrobe_team_44/issues/82)
- Follow-up UX improvements based on customer feedback


## Future Sprints

- **Sprint 4:** Sharing capabilities ([US-10](https://github.com/veronika1977/digital_wardrobe_team_44/issues/91)) and AI Material Detection ([US-07](https://github.com/veronika1977/digital_wardrobe_team_44/issues/90)).

## Removed 

- **US-03:** AI Outfit Generation (Removed: Out of scope for current MVP vision)
- **US-09:** Social Network (Removed: Replaced by simple link sharing in US-10)