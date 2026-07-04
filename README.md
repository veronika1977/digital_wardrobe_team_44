# Telegram Mini App for Digital Wardrobe

Digital wardrobe app that helps users organize clothing items, create outfits, capsules and track wear frequency.

## Technology Stack

- **Frontend:** React + TypeScript + Vite
- **Backend:** Python (FastAPI) + Rembg
- **Deployment:** Netlify (Frontend), Local (Backend for development)

## MVP v0 (Week 2 Deliverable)

- [Deployed website version (smoke check)](https://agent-6a29aac2b0946--benevolent-frangollo-a08785.netlify.app)
- [Deployed Telegram version (smoke check)](http://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)

## MVP v1 (Week 3 Deliverable)

- **[Live Telegram Mini App](https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)** — main production deployment
- **[Live Website Version](https://digwardrobe.netlify.app/)** — web preview for testing

### Features included in MVP v1:
- Telegram authentication (no registration required)
- Add clothing items with photo upload
- Tag system (category, season, material, color)
- Filter wardrobe by tags
- Soft delete with 14-day trash retention
- Restore items from trash

## MVP v1.1.0 (Assignment 4 / Sprint 2)

- **[Live Telegram Mini App](https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)** — main production deployment
- **[SemVer Release v1.1.0](https://github.com/veronika1977/digital_wardrobe_team_44/releases/tag/v1.1.0)**
- **[Demo Video](https://drive.google.com/drive/folders/11g03djGSts4WhYvRZkQ2ZdtfoOnMf1PW?usp=sharing)**

### Features added in MVP v2:
- **US-05:** Capsule Wardrobes — create and manage clothing capsules
- **US-06:** Edit Clothing Item — edit items with soft delete
- **US-08:** Automatic Background Removal — AI-powered background removal with fallback
- **Quality Gates:** CI/CD pipelines, automated tests, QRT, Vulture
- **66% code coverage** (exceeds 30% requirement)
- **64 backend tests + 3 frontend tests**

## MVP v2 (Assignment 5 / Sprint 3)

- **[Live Telegram Mini App](https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)** — main production deployment
- **[SemVer Release v2.0.0](https://github.com/veronika1977/digital_wardrobe_team_44/releases/tag/v2.0.0)**

### Features added in MVP v2:
- **US-12:** Weather Integration — display current weather based on user location with manual fallback
- **US-13:** Calendar Planning — schedule outfits for specific dates with instant UI sync


## Documentation

### Maintained Artifacts

- [Definition of Done](docs/definition-of-done.md)
- [User Stories Registry](docs/user-stories.md)
- [Product Roadmap](docs/roadmap.md)
- [Changelog](CHANGELOG.md)
- [Hosted Documentation Site](https://veronika1977.github.io/digital_wardrobe_team_44/)

### Quality & Testing

- [Quality Requirements](docs/quality-requirements.md)
- [Quality Requirement Tests](docs/quality-requirement-tests.md)
- [Testing Status](docs/testing.md)
- [User Acceptance Tests](docs/user-acceptance-tests.md)

### Course Reports

- [Week 2 Report](reports/week2/README.md)
- [MVP v0 Report](reports/week2/mvp-v0-report.md)
- [Week 3 Report](reports/week3/README.md)
- [Week 4 Report (Assignment 4)](reports/week4/README.md)
- [Week 5 Report (Assignment 5)](reports/week5/README.md)

### License

- [MIT License](LICENSE)

### Related Repositories

- [Backend Repository](https://github.com/Mrxfg/digital-wardrobe)
- [Frontend Repository](https://github.com/veronika1977/digital_wardrobe_777)

## Quick Start

### Prerequisites
- Node.js 18+
- Python 3.10+
- Telegram Bot Token (from @BotFather)

### Frontend

```bash
git clone https://github.com/veronika1977/digital_wardrobe_777.git
cd digital_wardrobe_777
npm install
npm run dev 
```
### Backend (Local Development Only)

```bash
git clone https://github.com/Mrxfg/digital-wardrobe.git
cd digital-wardrobe
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

# Set up environment variables
export TELEGRAM_BOT_TOKEN="your_bot_token_here"

# Run the server
python main.py
```
