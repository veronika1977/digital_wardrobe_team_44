# Week 3 Report: Digital Wardrobe

This document serves as the public index for the Assignment 3 submission.

## Project Information

- **Project Name:** Digital Wardrobe
- **Team Number:** 44
- **Repository:** [digital_wardrobe_team_44](https://github.com/veronika1977/digital_wardrobe_team_44)
- **License:** [LICENSE](../../LICENSE)

**Description:**  
Digital Wardrobe is a Telegram Mini App that helps users manage their clothing items. Users can log in via Telegram, add items with photos, categorize them by material/season/colors, and organize their wardrobe efficiently. The app uses Telegram's native authentication for seamless onboarding.

## Customer Feedback from Assignment 2

During Assignment 2 review, the customer requested:
1. **Design revisions** — addressed via UI Kit (PBI #98)
2. **Weather integration** — added as US-12, planned for MVP v2

## Key Links

- [Historical User Stories (Assignment 2)](../week2/user-stories.md)
- [Current User Stories Index](../../docs/user-stories.md)
- [Sprint Report](./sprint-report.md)
- [Product Backlog Board](https://github.com/users/veronika1977/projects/1/views/2)
- [Sprint 1 Backlog Board](https://github.com/users/veronika1977/projects/1/views/6)
- [Sprint 1 Milestone](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/1)
- [MVP v1 Scope View](#) *(replace with actual GitHub Project filtered view link)*
- [SemVer Release](#) *(replace with actual GitHub Release link)*
- [CHANGELOG](../../CHANGELOG.md)
- [Process Requirements](../../Process_Requirements.md)

- **Access/Run Instructions:** [README.md](../../README.md)
- [Roadmap](../../docs/roadmap.md)
- [Definition of Done](../../docs/definition-of-done.md)


## Week 3 Reports

- [**Customer Review Summary**](customer-review-summary.md)
- [**Customer Review Transcript**](customer-review-transcript.md)
- [**Week 3 Reflection**](reflection.md)
- [**Sprint Retrospective**](retrospective.md)
- [**LLM Usage Report**](llm-report.md)

## Story Points

- **Total Product Backlog size:** 63 SP
- **Total Sprint 1 size:** 34 SP

## Sprint Goal

Enable users to securely log in via Telegram and manage their clothing items (add with photo upload or files upload, name, material, season, colors, and delete). The MVP v1 focuses on core wardrobe CRUD operations with Telegram authentication as the entry point.

## MVP v1 Scope
## Next Steps

### User Stories

- **US-01: Telegram Authentication** — [#84](https://github.com/veronika1977/digital_wardrobe_team_44/issues/84)
- **US-02: Add Clothing Item with Photo** — [#85](https://github.com/veronika1977/digital_wardrobe_team_44/issues/85)
- **US-04: Tags for Clothing Items** — [#87](https://github.com/veronika1977/digital_wardrobe_team_44/issues/87)
- **US-11: Delete Item (Soft Delete)** — [#77](https://github.com/veronika1977/digital_wardrobe_team_44/issues/77)

### Supporting Technical PBIs

- Setup Telegram Bot API (#94)
- Create Telegram Bot with /start Command (#95)
- Research AI background removal API (#96)
- API Documentation (#97)
- Create UI Kit and Design System (#98)

### Task Decomposition

Each User Story has been decomposed into smaller technical PBIs for implementation:

- **US-01** in 3 subtasks (Backend Auth, Frontend SDK, Auth State)
- **US-02** in 3 subtasks (Backend API, Frontend Form, Photo Upload)
- **US-04** in 2 subtasks (Backend Tags, Frontend Tags UI)
- **US-11** in 2 subtasks (Backend Delete, Frontend Delete Button)

## PBI Types, Statuses & Priorities

Following the shared Process Requirements:
- **PBI Types:** User Story, Technical PBI, Course Task, Bug Report
- **Work Status:** To Do, Ready, In Progress, Review, Done
- **MoSCoW Priority:** Must Have, Should Have, Could Have, Won't Have
- **MVP Version Tracking:** Custom field in GitHub Projects (MVP v1, MVP v2, Future)
- **Sprint Milestone:** Used as the authoritative container for Sprint-selected PBIs

## Roadmap

- **Current Sprint (Sprint 1):** MVP v1 — Core wardrobe CRUD with Telegram auth
- **Next Sprint (Sprint 2):** MVP v2 — Weather integration, AI background removal, capsule wardrobes

[Full roadmap](../../docs/roadmap.md)

## Current Product Status

**MVP v1 Status:** 


## Workflow Evidence

### Reviewed Issue-Linked PRs

- [PR #1: Telegram Auth Backend](#) *(replace with actual PR link)*
- [PR #2: Add Item Backend](#) *(replace with actual PR link)*
- [PR #3: Telegram Auth Frontend](#) *(replace with actual PR link)*
- [PR #4: Add Item Frontend](https://github.com/veronika1977/digital_wardrobe_777/pull/4)
- [PR #5: Sprint Report Update](#) *(replace with actual PR link)*

### Issue & PR Templates

- [User Story Template](../../.github/ISSUE_TEMPLATE/user-story.md)
- [Other PBI Template](../../.github/ISSUE_TEMPLATE/pbi.md)
- [Course Task Template](../../.github/ISSUE_TEMPLATE/course-task.md)
- [Bug Report Template](../../.github/ISSUE_TEMPLATE/bug-report.md)
- [Extended PR Template](../../.github/pull_request_template.md)

## Verification Evidence

All MVP v1 PBIs will be verified against their Acceptance Criteria:
- [US-01 verification](https://github.com/veronika1977/digital_wardrobe_team_44/issues/84) *(add comment link after verification)*
- [US-02 verification](https://github.com/veronika1977/digital_wardrobe_team_44/issues/85)
(add comment link after verification)*
- [US-04 verification](https://github.com/veronika1977/digital_wardrobe_team_44/issues/87)
(add comment link after verification)*
- [US-11 verification](https://github.com/veronika1977/digital_wardrobe_team_44/issues/77)
(add comment link after verification)*

## Delivered MVP v1

- [**Live Frontend**](https://digwardrobe.netlify.app/)
- [**Backend API**](https://yourapp.railway.app) *(replace after deploy)*
- [**Telegram Bot**](https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)
- [**Full Setup Guide**](../../README.md)

## Video Demonstration
[**Link**](https://drive.google.com/drive/folders/1U6ZyvhWXD34KY7kA_3uiMyZwmU-Z02DT?usp=sharing)

## Contribution Traceability Table

| Team Member | Issues Created | PRs Created | PRs Reviewed | Meaningful Comments |
| :--- | :--- | :--- | :--- | :--- |
| Veronika Drozd (@veronika1977) | [#77, #82, #84, #85, #87] | [ ] | [ ] | [ ] |
| Evgeni1a (@Evgeni1a) | [#94, #95, #96, #97, #98] | [ ] | [ ] | [ ] |
| Catherine Har (@CatherineHar) | [ ] | [ ] | [ ] | [ ] |
| Darina Luch (@DarinaLuch) | [ ] | [ ] | [ ] | [ ] |
| Mrxfg (@Mrxfg) | [ ] | [ ] | [ ] | [ ] |

## Screenshots

![Product Backlog view][#]
![Sprint Backlog view][#]
![Sprint milestone][#]
![SemVer release][#]
![Delivered MVP v1 deployment 1](images/photo_mvp_v1_1.png)
![Delivered MVP v1 deployment 2](images/photo_mvp_v1_2.png)
![Delivered MVP v1 deployment 3](images/photo_mvp_v1_3.png)
![Delivered MVP v1 deployment 4](images/photo_mvp_v1_4.png)
![Delivered MVP v1 deployment 5](images/photo_mvp_v1_5.png)
![Delivered MVP v1 deployment 6](images/photo_mvp_v1_6.png)
![Delivered MVP v1 deployment 7](images/photo_mvp_v1_7.png)
![Delivered MVP v1 deployment 8](images/photo_mvp_v1_8.png)
![Example of a reviewed issue-linked PR/MR 1](images/PR1.png)
![Example of a reviewed issue-linked PR/MR 2](images/PR2.png)
![Example of a reviewed issue-linked PR/MR 3](images/PR3.png)