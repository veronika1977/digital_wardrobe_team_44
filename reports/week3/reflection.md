# Team Reflection - Week 3

## Learning points

- **Product Backlog migration**: Learned how to migrate user stories from a static document (`reports/week2/user-stories.md`) into a live issue-based Product Backlog on GitHub, preserving stable IDs (US-01, US-02, etc.) and traceability links.
- **GitHub Projects for Scrum**: Discovered how to use GitHub Projects with custom fields (MVP version, Story Points, Work Status) to maintain both Product Backlog and Sprint Backlog views from the same issue pool.
- **Acceptance Criteria in Gherkin**: Learned to write testable, scenario-based AC using Given/When/Then format, which made it clear when a PBI is truly "Done".
- **Design system creation**: Learned how to build a design system in Figma that serves as a single source of truth for colors, components, and icons — and how to document it for developers.
- **Sprint Planning with Story Points**: Learned how to estimate PBIs using Story Points and how to decompose large User Stories into smaller technical subtasks that can be worked on in parallel.
- **Telegram Mini App specifics**: Learned the specifics process of work with Telegram Web App 


## Validated assumptions

- **Rembg over cloud APIs**: Rejected the initial assumption that we should use a cloud API (remove.bg, ClipDrop) for background removal. After research, validated that Rembg (local Python library) is better for MVP v1: free, no rate limits, no API keys, better privacy.
- **Design system prevents inconsistency**: Validated that having a design system (even a minimal one) prevents UI inconsistencies when multiple team members work on different screens.
- **Soft delete with `deletedAt`**: Validated that using a `deletedAt` timestamp field (instead of hard delete) enables the "Trash basket with 14-day retention" feature without extra database tables.
- **LocalStorage is not enough**: Rejected the assumption that frontend-only storage (localStorage) would be sufficient for MVP v1 — backend integration is required for real authentication and data persistence.


## Friction and gaps

- **Story Point estimation**: Initial estimates were inconsistent across team members. Some PBIs were overestimated (e.g., documentation tasks), while others (like Telegram auth integration) were underestimated.
- **MVP v1 scope boundaries**: It was unclear which "nice-to-have" features (weather widget, capsules, outfit generation) should be deferred to MVP v2. This required explicit negotiation with the customer.
- **Acceptance Criteria granularity**: Writing AC that are specific enough to be testable but not overly restrictive was challenging — some scenarios were too vague, others too detailed.
- **Time pressure**: 34 Story Points across 19 tasks in a 4-day sprint. Some tasks were simplified or move in another versions of project.

## Planned response

- **API contract first**: Before starting implementation in the next sprint, we will finalize and agree on the API contract (`docs/api-contract.md`) so frontend and backend developers can work in parallel without blocking each other. This will be tracked in [Sprint 2 milestone](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/2)
- **Stricter MVP scoping**: For MVP v2, we will apply a stricter "Must Have vs Should Have" filter during Sprint Planning to avoid scope creep. This affects PBIs in [Sprint 2](https://github.com/veronika1977/digital_wardrobe_team_44/milestone/2) and will be reflected in the [Product Roadmap](../../docs/roadmap.md).
- **Earlier customer check-ins**: Instead of waiting for the formal Sprint Review, we will share incremental demos with the customer mid-sprint to catch misalignments earlier.
- **Earlier Sprint Backlog**: Instead of doing Sprint Backlog before 4 days of deadline, it is better to do it on the first day of the week, so team will have more time on solving tasks.
