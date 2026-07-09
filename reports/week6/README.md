# Week 6 Public Report — Sprint 4: Trial Release

## Project Overview

- **Project Name:** Digital Wardrobe (Team 44)
- **Description:** Telegram Mini App for personal wardrobe management with AI-powered outfit suggestions, calendar planning, and daily wear tracking.
- **Product Backlog:** [GitHub Projects Board](https://github.com/users/veronika1977/projects/1/views/1)
- **Sprint 4 Backlog:** [Sprint 4 View](https://github.com/users/veronika1977/projects/1/views/10)
- **Sprint 4 Milestone:** [Sprint 4](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/4)

## Repository Structure

This project uses a **multi-repo architecture** with three independent repositories. Each code repository has its own contribution guidelines and AI agent instructions tailored to its tech stack.

| Repository | Purpose | Tech Stack | Contribution Guide |
|------------|---------|------------|-------------------|
| **This repo** ([digital_wardrobe_team_44](https://github.com/veronika1977/digital_wardrobe_team_44)) | Coordination: ADRs, reports, handover docs, roadmap | Markdown | [CONTRIBUTING.md](CONTRIBUTING.md) \| [AGENTS.md](AGENTS.md) |
| [digital_wardrobe_777](https://github.com/veronika1977/digital_wardrobe_777) | Frontend: Telegram Mini App UI | React 18, TypeScript, Vite, TailwindCSS | [CONTRIBUTING.md](https://github.com/veronika1977/digital_wardrobe_777/blob/main/CONTRIBUTING.md) \| [AGENTS.md](https://github.com/veronika1977/digital_wardrobe_777/blob/main/AGENTS.md) |
| [digital-wardrobe](https://github.com/Mrxfg/digital-wardrobe) | Backend: API server | Python 3.10+, FastAPI, PostgreSQL, Rembg | [CONTRIBUTING.md](https://github.com/Mrxfg/digital-wardrobe/blob/main/CONTRIBUTING.md) \| [AGENTS.md](https://github.com/Mrxfg/digital-wardrobe/blob/main/AGENTS.md) |

> **Note:** Code contributions go to the frontend or backend repositories (see their respective `CONTRIBUTING.md`). This repository contains only documentation, reports, and architectural artifacts.


## Sprint 4 Scope & Planning

- **Sprint Goal:** Deliver a stable trial release with AI Stylist and Daily Wear Tracking, complete customer-facing documentation, conduct a transition-readiness meeting, and establish evidence for independent customer use.
- **Dates:** 06.07.2026 – 12.07.2026
- **Total Story Points:** 42 SP
- **Scope Summary:** Implemented AI-powered outfit generation (US-14), Telegram bot daily reminders with wear logging (US-15), outfit layout persistence, grouped outfit display, and finalized all customer-facing documentation (handover, contributing, agent guidelines, ADRs).

## Week 6 Trial Release (v2.1.0)

- **SemVer Release:** [v2.1.0 — Trial Release](link)
- **Changelog:** [CHANGELOG.md](../../CHANGELOG.md)
- **Product Access:** [@digital_wardrobe_app_bot](https://t.me/digital_wardrobe_app_bot) (Telegram Mini App)
- [**Demo Video:**](https://drive.google.com/drive/folders/1QmeQpMIMS3NxZ2RVd2gaNRPiYpNO2f7B?usp=sharing)(< 2 min, sanitized)
- **Run/Access Instructions:** [README.md](../../README.md#getting-started)

- **Repository Entry Points:** 

  - [README.md](../../README.md)
  - [CONTRIBUTING.md](../../CONTRIBUTING.md)
  - [AGENTS.md](../../AGENTS.md)
  - [docs/customer-handover.md](../../docs/customer-handover.md)
  - [Hosted Documentation Site](https://veronika1977.github.io/digital_wardrobe_team_44/)

## Customer-Facing Documentation Review

During Week 6, the customer reviewed the updated documentation set.
- **Clear:** Setup steps, Telegram bot access, handover scope, environment variables.
- **Unclear/Missing:** Initially, the distinction between legacy code repositories and the current coordination repo was ambiguous; resolved by adding a repository map to `README.md` and `AGENTS.md`.
- **Action Taken:** Updated `customer-handover.md` with explicit asset ownership tables, multi-repo routing instructions, and clear transfer procedures.

## Transition-Readiness Summary

- **Current Handover Level:** Ready for independent use
- **Customer Confirmation:** Accepted with follow-up items
- **What is Ready:** Full access to Telegram Mini App, complete setup/deployment instructions, documented architecture decisions, CI pipeline stability, customer handover document. Customer confirmed willingness to use the product independently.
- **What remains partial:** Monetization (US-16) not yet implemented; AI Stylist prompt variety planned for Sprint 5; share-by-link feature deferred to post-course.
- **What Must Happen in Week 7:** Implement monetization (US-16), complete deferred customer feedback PBIs (#301, #303, #322), obtain final customer confirmation, release MVP v3, prepare Demo Day materials.
- **Blockers:** None that prevent independent use. All remaining items are enhancements that the team will deliver in Sprint 5 or defer to post-course work.

## Customer Feedback & Response

All feedback from the Week 6 customer meeting (2026-07-09) was applied mid-sprint and included in v2.1.0 release:

| Feedback Point | Resulting PBI / Issue | Status |
|----------------|----------------------|--------|
| Navigation layout unintuitive — Home should be leftmost, AI Stylist should be in the middle | [#300: Reorder bottom navigation tabs](https://github.com/veronika1977/digital_wardrobe_team_44/issues/300) | Completed in v2.1.0 |
| Want conversational AI chat, not just outfit generation | [PBI #301: Add conversational AI chat backend](https://github.com/veronika1977/digital_wardrobe_team_44/issues/301), [PBI #322: Add conversational AI chat frontend](https://github.com/veronika1977/digital_wardrobe_team_44/issues/322) | Deferred to Sprint 5 |
| Need faster way to plan today's outfit from Home screen | [PBI #302: Add "Outfit for Today" widget](https://github.com/veronika1977/digital_wardrobe_team_44/issues/302) | Completed in v2.1.0 |
| Bot should prompt planning tomorrow's outfit, not ask what was worn today | [PBI #303: Change bot reminder to prompt planning](https://github.com/veronika1977/digital_wardrobe_team_44/issues/303) | Deferred to Sprint 5 (breaking change to US-15) |
| Monetization tier for premium features | [PBI #284: Add monetization (US-16)](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) | Deferred to Sprint 5 |

**Feedback Deferred to Sprint 5:**

- **Monetization (PBI #284):** Deferred to Sprint 5 to prioritize applying customer feedback from Week 6 meeting. Monetization is not a blocker for handover or transition-readiness — it's a business enhancement.
- **Conversational AI chat (PBI #301 backend, #322 frontend):** Deferred to Sprint 5 — requires significant backend+frontend work.
- **Bot reminder reframing (PBI #303):** Deferred to Sprint 5 — breaking change to US-15 requires careful migration.

## Roadmap & Supporting Documentation

- **Roadmap:** [docs/roadmap.md](../../docs/roadmap.md)
- **Quality & Testing:** [docs/testing.md](../../docs/testing.md), [docs/quality-requirement-tests.md](../../docs/quality-requirement-tests.md)
- **Architecture & ADRs:** [docs/architecture/README.md](../../docs/architecture/README.md), [ADR-004: AI Strategy](../../docs/architecture/adr/ADR-004-ai-strategy.md), [ADR-005: Bot Architecture](../../docs/architecture/adr/ADR-005-bot-architecture.md)
- **Development Process:** [docs/development-process.md](../../docs/development-process.md), [Definition of Done](../../docs/definition-of-done.md)

## UAT & Customer Trial Results

- Executed 7 maintained UAT scenarios during Week 6 trial meeting.
- **Result:** 7/7 passed. No critical blockers identified.
- **Key Feedback:** AI Stylist works but needs conversational chat interface (not just button) — PBI #301 (backend) and #322 (frontend) created, deferred to Sprint 5; 19:00 bot reminder timing is highly convenient; inline buttons for planning work smoothly; navigation must follow Instagram/Duolingo pattern (Home leftmost) — addressed via PBI #300 (completed in v2.1.0).
- **Full UAT Document:** [docs/user-acceptance-tests.md](../../docs/user-acceptance-tests.md)

## Release & Changelog

- **Week 6 Trial Release:** [v2.1.0](link)
- **Changelog:** [CHANGELOG.md](../../CHANGELOG.md)

## Sprint Review & Process Artifacts

- **Sprint Review Transcript:** [reports/week6/sprint-review-transcript.md](sprint-review-transcript.md) (recording permitted, public transcript publication permitted, private instructor sharing permitted)
- **Sprint Review Summary:** [reports/week6/sprint-review-summary.md](sprint-review-summary.md)
- **Reflection:** [reports/week6/reflection.md](reflection.md)
- **Retrospective:** [reports/week6/retrospective.md](retrospective.md)
- **LLM Report:** [reports/week6/llm-report.md](llm-report.md)

## Current Product Status & Week 7 Follow-up

The product is functionally complete for core user workflows (add items, plan outfits, AI suggestions, daily wear tracking). Infrastructure is stable, documentation is current, and CI gates pass consistently. Week 7 will focus on implementing the monetization tier (US-16), finalizing customer handover confirmation, and preparing the MVP v3 release for Demo Day.

## Contribution Traceability

| Team Member | Role | Issues | PRs | Reviews Given | Comments |
|-------------|------|--------|-----|--------------|----------|
| @veronika1977 | Scrum Master | [#217](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217), [#287](https://github.com/veronika1977/digital_wardrobe_team_44/issues/287#issue-4821414891), [#318](https://github.com/veronika1977/digital_wardrobe_team_44/issues/319), [#320](https://github.com/veronika1977/digital_wardrobe_team_44/issues/320#issue-4848371102) | [#217](https://github.com/veronika1977/digital_wardrobe_team_44/pull/297#issue-4838101679), [#288](https://github.com/veronika1977/digital_wardrobe_team_44/pull/288#issue-4821424154), [#319](https://github.com/veronika1977/digital_wardrobe_team_44/pull/319) | [#299](https://github.com/veronika1977/digital_wardrobe_team_44/pull/299), [#307](https://github.com/veronika1977/digital_wardrobe_team_44/pull/307), [#311](https://github.com/veronika1977/digital_wardrobe_team_44/pull/311), [#317](https://github.com/veronika1977/digital_wardrobe_team_44/pull/317) | [#299](https://github.com/veronika1977/digital_wardrobe_team_44/pull/299#pullrequestreview-4660828697), [#307](https://github.com/veronika1977/digital_wardrobe_team_44/pull/307#pullrequestreview-4662492840), [#311](https://github.com/veronika1977/digital_wardrobe_team_44/pull/311#pullrequestreview-4662710753) |
| @Evgeni1a | Developer | [#306](https://github.com/veronika1977/digital_wardrobe_team_44/issues/306), [#309](https://github.com/veronika1977/digital_wardrobe_team_44/issues/309) | [#307](https://github.com/veronika1977/digital_wardrobe_team_44/pull/307), [#310](https://github.com/veronika1977/digital_wardrobe_team_44/pull/310) | [#297](https://github.com/veronika1977/digital_wardrobe_team_44/pull/297) | [#297](https://github.com/veronika1977/digital_wardrobe_team_44/pull/297#pullrequestreview-4654858984) |
| @Mrxfg | Developer | [#308](https://github.com/veronika1977/digital_wardrobe_team_44/issues/308) | [#311](https://github.com/veronika1977/digital_wardrobe_team_44/pull/311) | [#310](https://github.com/veronika1977/digital_wardrobe_team_44/pull/310)| [#310](https://github.com/veronika1977/digital_wardrobe_team_44/pull/310#pullrequestreview-4662657431) |
| @CatherineHar | Developer | [#316](https://github.com/veronika1977/digital_wardrobe_team_44/issues/316) | [#317](https://github.com/veronika1977/digital_wardrobe_team_44/pull/317) | [#296](https://github.com/veronika1977/digital_wardrobe_team_44/pull/296), [#288](https://github.com/veronika1977/digital_wardrobe_team_44/pull/288) | [#296](https://github.com/veronika1977/digital_wardrobe_team_44/pull/296#pullrequestreview-4648378857) |
| @DarinaLuch | Scrum Owner | [#298](https://github.com/veronika1977/digital_wardrobe_team_44/issues/298) | [#299](https://github.com/veronika1977/digital_wardrobe_team_44/pull/299) | [#319](https://github.com/veronika1977/digital_wardrobe_team_44/pull/319#issue-4848218185) | [#319](https://github.com/veronika1977/digital_wardrobe_team_44/pull/319#pullrequestreview-4665112386) |

---

## Evidence Screenshots

![Sprint 4 Milestone](link)
![v2.1.0 Release](link)
![Reviewed PR Example](link)
![CI Pipeline Status](link)
![Customer Handover Doc](link)