# Customer Handover — Digital Wardrobe

> **Document version:** Week 6 (Sprint 4) — Trial Release v2.1.0
> **Last updated:** 2026-07-12
> **Next update:** Week 7 (Sprint 5) — Final Release v3.0.0
> **Maintained by:** @veronika1977

## Handover Status

- **Current level:** Ready for independent use
- **Customer confirmation:** Accepted with follow-up
- **Confirmation date:** 2026-07-09
- **Confirmed by:** Customer


### What "Ready for independent use" means in our case

The customer can start using the product independently via the Telegram Mini App without assistance from the team. All core user workflows (add items, plan outfits) are functional and documented.

### What remains partial

The product is ready for independent use in its current state, but the following aspects are not yet finalized and will be addressed in Sprint 5 (Week 7) or post-course:

- **Monetization (US-16):** Paywall and Premium tier not yet implemented — free tier fully functional
- **AI Stylist variety:** Suggestions work but prompt tuning for color/style diversity is planned (PBI #285)
- **Outfit sharing:** Share-by-link feature is deferred to post-course (PBI #287)

## Blockers analysis

- **Blocker owner:** Team side (not customer or external)
- **Evidence of readiness obtained:** 
  - Customer independently tested the trial release during Week 6 meeting
  - All 7 UAT scenarios passed during trial meeting
  - Customer confirmed willingness to adopt after Sprint 5 adjustments
  - CI pipeline stable, documentation complete, deployment verified
- **Remaining actions for full acceptance:**
  - Implement monetization (PBI #284) in Sprint 5
  - Apply customer trial feedback (PBIs #300-303) in Sprint 4 final days
  - Obtain final customer confirmation after Sprint 5 changes


---

## Follow-up Items (Customer-Requested)

The customer confirmed acceptance with the following follow-up items to be addressed in Sprint 5:

| # | Follow-up Item | Priority | PBI/Issue | Status |
|---|----------------|----------|-----------|--------|
| 1 | Add monetization | High | [US-16](https://github.com/veronika1977/digital_wardrobe_team_44/issues/284) | Planned for Sprint 5 |


**Note:** All other customer feedback from Week 6 meeting (navigation reorder, conversational AI, Outfit for Today widget, bot planning prompt) was applied mid-sprint and included in v2.1.0 release.

## What Is Available to Customer Right Now

| Asset | Access Type | Status |
|-------|-------------|--------|
| Telegram Bot | Public access via [@digital_wardrobe_app_bot](https://t.me/digital_wardrobe_app_bot) | Available |
| Hosted Documentation | Public access via [GitHub Pages](https://veronika1977.github.io/digital_wardrobe_team_44/) | Available |
| Product Features | Full access to all current features (US-01 to US-15) |  Available |

**Note:** The customer can independently use the product via the Telegram Mini App without any assistance from the team. All core features are functional and documented.

---

## What Remains with the Team (Not Transferred)

| Asset | Details | Reason |
|-------|---------|--------|
| Repository (Frontend) | https://github.com/veronika1977/digital_wardrobe_777 (frontend/) | Course requirement — team maintains until end of course |
| Repository (Backend) | https://github.com/Mrxfg/digital-wardrobe (backend/) | Course requirement — team maintains until end of course |
| Repository (Documentation)| https://github.com/veronika1977/digital_wardrobe_team_44 | Course requirement — team maintains until end of course|
| Deployment (Frontend) | Cloudflare Pages (team account) | Team manages CI/CD during course |
| Deployment (Backend) | Docker Compose on VPS (team account) | Team manages infrastructure during course |
| Telegram Bot | @digital_wardrobe_app_bot | Team maintains bot token and webhook |
| Database | PostgreSQL on VPS | Team manages backups and migrations |
| Domain | Not applicable | No custom domain used |

**Note:** All infrastructure remains under team control during the course. After course completion (19.07.2026), the team can transfer full ownership if the customer requests it.

---

## What Can Be Transferred After Course (Upon Request)

If the customer wants full ownership after the course, the following can be transferred:

| Asset | Transfer Process | Effort |
|-------|------------------|--------|
| Repository ownership | Transfer GitHub repositories to customer's account | 1 hour |
| Cloudflare Pages | Transfer project to customer's Cloudflare account | 30 min |
| VPS + Database | Provide credentials + migration guide | 2 hours |
| Telegram Bot | Transfer bot token via [@BotFather](https://t.me/BotFather) | 15 min |
| Environment variables | Provide `.env` template (without secrets) | 30 min |

**Total estimated effort:** ~4 hours for full transfer.

---

## Environment Variables Required

| Variable | Purpose | How to obtain |
|----------|---------|---------------|
| `TELEGRAM_BOT_TOKEN` | Bot operations | From [@BotFather](https://t.me/BotFather) |
| `DASHSCOPE_API_KEY` | AI Stylist functionality (Qwen) | From [DashScope Console](https://dashscope.aliyun.com/) |
| `WEATHER_API_KEY` | Weather display | From [OpenWeatherMap](https://openweathermap.org/) |
| `DATABASE_URL` | Database connection | From VPS provider |
| `SECRET_KEY` | Application security | Generate with `openssl rand -base64 32` |

**Security Note:** Never commit `.env` files to the repository. Use environment-specific configuration management.

---

## Setup & Deployment Steps

### Prerequisites

- Node.js 18+
- Python 3.10+
- Telegram Bot Token from [@BotFather](https://t.me/BotFather)

### Frontend (Local Development)

```bash
git clone https://github.com/veronika1977/digital_wardrobe_777.git
cd digital_wardrobe_777
npm install
npm run dev
```

### Backend (Local Development)

``` bash
git clone https://github.com/Mrxfg/digital-wardrobe.git
cd digital-wardrobe
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

# Set up environment variables
export TELEGRAM_BOT_TOKEN="your_bot_token_here"
export DATABASE_URL="postgresql://user:pass@localhost:5432/wardrobe"

# Run the server
python main.py
```
### Production Deployment

- **Frontend:** Auto-deployed via Cloudflare Pages on push to main
- **Backend:** Docker Compose on VPS (docker-compose up -d)

### Verification Steps

After deployment, verify:
1. Open https://t.me/digital_wardrobe_app_bot → tap Start → should see main screen
2. Add a test item → should appear in wardrobe
3. Check weather widget → should display current weather
4. Open Calendar → should allow outfit planning
5. Wait for 19:00 → should receive daily reminder from bot

## How to Rotate Secrets

Generate new secret key:

```bash
openssl rand -base64 32
```
Update environment variables in your deployment environment. Restart services:

``` bash
docker-compose restart
```

## Main Entry Points for Customer Use

| Purpose | Link | Documentation |
|---------|------|---------------|
| Product Access (Telegram Mini App) | [@digital_wardrobe_app_bot](https://t.me/digital_wardrobe_app_bot) | — |
| Documentation repository (this repo) | [digital_wardrobe_team_44](https://github.com/veronika1977/digital_wardrobe_team_44) | [CONTRIBUTING.md](CONTRIBUTING.md) · [AGENTS.md](AGENTS.md) |
| Frontend repository | [digital_wardrobe_777](https://github.com/veronika1977/digital_wardrobe_777) | [CONTRIBUTING.md](https://github.com/veronika1977/digital_wardrobe_777/blob/main/CONTRIBUTING.md) · [AGENTS.md](https://github.com/veronika1977/digital_wardrobe_777/blob/main/AGENTS.md) |
| Backend repository | [digital-wardrobe](https://github.com/Mrxfg/digital-wardrobe) | [CONTRIBUTING.md](https://github.com/Mrxfg/digital-wardrobe/blob/main/CONTRIBUTING.md) · [AGENTS.md](https://github.com/Mrxfg/digital-wardrobe/blob/main/AGENTS.md) |
| Hosted Documentation | [GitHub Pages](https://veronika1977.github.io/digital_wardrobe_team_44/) | — |
| Issue Tracker | [GitHub Issues](https://github.com/veronika1977/digital_wardrobe_team_44/issues) | — |

> **Note:** This project uses a multi-repo architecture. Each code repository has its own `CONTRIBUTING.md` and `AGENTS.md` tailored to its tech stack (React/Vite for frontend, Python/FastAPI for backend). This repository contains only documentation, reports, and architectural artifacts.

## Usage Instructions

1. Open [@digital_wardrobe_app_bot](https://t.me/digital_wardrobe_app_bot) in Telegram
2. Tap **Start** → automatic login via Telegram
3. **Add items:** Tap `+` → upload photo → fill attributes → save
4. **Plan outfits:** Open `Calendar` → pick date → select items → save
5. **Track wear:** Respond to daily 19:00 bot messages to log worn items

For more examples, please refer to the [Hosted Documentation](https://veronika1977.github.io/digital_wardrobe_team_44/)

## Included Features (Scope of Handover)

The following features are fully functional and included in the handover:
- US-01: Telegram Authentication
- US-02: Add Clothing Item with Photo
- US-04: Tags for Clothing Items
- US-05: Capsule Wardrobes
- US-06: Edit Clothing Item
- US-08: Automatic Background Removal
- US-11: Delete Item (Soft Delete)
- US-12: Weather Integration
- US-13: Calendar with Outfits
- US-14: AI Stylist (Sprint 4)
- US-15: Telegram Bot Daily Wear Tracking (Sprint 4)
- PBI #300: Reordered Navigation (Sprint 4)
- PBI #301: Conversational AI Chat (Sprint 4)
- PBI #302: Outfit for Today Widget (Sprint 4)
- PBI #303: Bot Prompts Planning for Tomorrow (Sprint 4)

## Architecture & Technical Decisions

Key architectural decisions relevant to the customer:

| ADR | Decision | Customer Impact |
|-----|----------|-----------------|
| [ADR-001](architecture/adr/ADR-001-fastapi-backend.md) | FastAPI + PostgreSQL | Async API, reliable data storage |
| [ADR-002](architecture/adr/ADR-002-rembg-background-removal.md) | CPU-based Rembg | Background removal works offline, no external API dependency |
| [ADR-003](architecture/adr/ADR-003-telegram-authentication.md) | Telegram Mini App Auth | No registration required, instant login |
| [ADR-004](architecture/adr/ADR-004-ai-strategy.md) | LLM provider for AI Stylist | AI suggestions with fallback when LLM is unavailable |
| [ADR-005](architecture/adr/ADR-005-bot-architecture.md) | Telegram Bot scheduler | Daily reminders at 19:00 with inline buttons |

## Quality Guarantees

The following quality requirements are verified by automated tests:

| QRT | Requirement | Target | Status |
|-----|-------------|--------|--------|
| QRT-001 | Backend test coverage | ≥30% | 66% achieved |
| QRT-002 | CI pipeline stability | 100% green on main | Verified |


For full list, see [Quality Requirement Tests](quality-requirement-tests.md).

## Limitations & Known Issues

### Technical Limitations

- Rembg model: Requires ~170MB disk space for background removal
- Single-node deployment: No horizontal scaling configured
- Weather API quota: OpenWeatherMap free tier has 1000 calls/day limit

### Known Issues

No critical known issues

## Support Expectations

### During Course (until 19.07.2026)

- Team provides active development and bug fixes
- Customer can report issues via GitHub Issues
- Team responds within 24 hours

### After Course

- No active support from the team (course completed)
- Customer can:
    - Use the product as-is (all features functional)
    - Self-maintain using CONTRIBUTING.md and AGENTS.md
    - Hire developers to extend the product (codebase is well-documented)
    - Request full ownership transfer (see "What Can Be Transferred After Course")


## Documentation Sufficiency Assessment

**Question:** Is the current documentation set sufficient for the reached handover level ("Ready for independent use")?

**Answer:**  **Yes, the documentation set is sufficient for the "Ready for independent use" level.**

**Justification:**
- `README.md` provides complete setup and usage instructions
- `CONTRIBUTING.md` explains how to extend the codebase
- `AGENTS.md` provides rules for AI assistants working with the code
- Hosted documentation site contains detailed user guides
- All environment variables are documented
- Deployment steps are reproducible and verified
- Architecture decisions are documented in ADRs
- Quality requirements are defined and tested

**Remaining support necessary:** None for basic usage. Advanced customization (e.g., changing payment provider, adding new AI models, migrating to a different database) would require developer assistance and is covered by `CONTRIBUTING.md`.
