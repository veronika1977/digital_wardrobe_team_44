# Interview summary
**Date:** 2026-06-27
**Participants:** Veronika Drozd, Evgeniia Zakharova, Ekaterina Kharamanian

## Sprint Goal Reviewed
The Sprint Goal for MVP Version 2 was presented: release with three key user stories – wardrobe capsules, editing items, and automatic background removal. The total sprint volume is 41 story points.

## Delivered Increment Discussed
The team demonstrated the following implemented functionality:
- Item addition with image cropping
- Color selection as color blocks (replacing text-based selection)
- Item editing (season, category, etc.)
- Delete function – cross icon replaced with a dedicated "Delete item" button; items move to recycle bin with countdown display for permanent deletion
- Outfit creation with item selection
- Capsules – new functionality allowing grouping of items and creating outfits within capsules
- Search button removed from the main screen (based on previous feedback)

The following were noted as not yet fully refined:
- Multiple selection for seasons (to be added)
- Shadows on items (to be removed)
- Background removal – currently cropping only, not AI-enhanced

## UAT Results
**Date of UAT interview:** 2026-06-24
**Participants:** Veronika Drozd, Ekaterina Kharamanian
### Which UAT scenarios passed:
- **UAT-001:** Add Clothing Item with Photo — PASSED
- **UAT-002:** Delete Item and Verify in Cart — PASSED (with feedback)
- **UAT-003:** Filter Wardrobe by Season — PASSED

### Which UAT scenarios failed or need product changes:
- **UAT-002:** Delete flow needs UX improvement
  - Current: Small "✕" badge on item card
  - Required: Replace with explicit "Удалить" button
  - **Follow-up PBI:** #168

### Most important feedback points received:
1. **HIGH:** Replace delete badge with explicit "Delete" button (PBI #168)
2. **HIGH:** Replace color text label with color swatch (PBI #179)
2. **MEDIUM:** Add confirmation dialog for restore from cart (PBI #169)

### Resulting PBIs:
- [ ] **#168:** Replace delete badge with explicit "Delete" button (3 SP, Must Have)
- [ ] **#169:** Add confirmation dialog for restore from cart (2 SP, Should Have)
- [ ] **#179:** Replace color text label with color swatch (3 SP, Should Have)

**Total follow-up work:** 8 SP

## Quality Evidence Discussed
The team presented the following quality metrics and practices:
- Automated tests added to prevent regression
- Documentation updated
- Continuous Integration (CI) is green
- Backend test coverage: 66%
- Frontend test coverage: 100%

Three Quality Requirements defined based on ISO/IEC 25010:
- Time behavior – API response under 3 seconds
- Fault tolerance – data preservation during failures
- Traceability – test coverage ≥ 30%
  
Seven automated quality checks implemented: linting, code style, formatting, type checking, build verification, unit tests, integration tests, quality requirement tests, security scans, Branch Protection configured, so no direct merges to Main without pull request and review.

## Feedback
The customer provided the following feedback:
- The application looks better and has improved since the previous review
- Overall, the product's design looks good
- The sprint and tasks for the next sprint are approved
- Shadows on items should be removed
- Question raised about AI enhancement for images – currently only cropping is used, AI enhancement is being considered.The customer suggested adding AI to convert casual photos to studio-quality images

## Approvals
The customer approved the MVP Version 2 increment as presented and confirmed that the sprint and the tasks for the next sprint look good.

## Requested changes
The following changes were requested or acknowledged:
- Remove shadows from item images
- Add ability to select multiple seasons for an item
- Consider implementing AI enhancement for image quality (converting casual photos to studio quality)

## Risks:
Telegram requires VPN and proxies for access

## Action Points
- The team will remove shadows from item images
- The team will add support for selecting multiple seasons
- The team will consider adding an "Enhance with AI" feature (time permitting)
- The team will continue work on calendar, outfit planning, and bot notifications in subsequent sprints

## Resulting Product Backlog or Scope Changes
The following updates were made or confirmed:
- Shadows removal – added to backlog for the next sprint
- Multiple season selection – added to backlog
- AI image enhancement – under consideration, dependent on time and API availability
- Calendar, outfit planning, and bot notifications – planned for subsequent sprints
- AI stylist and weather integration – planned for subsequent sprints
