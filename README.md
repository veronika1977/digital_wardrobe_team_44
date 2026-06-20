# Telegram Mini App for digital wardrobe

Digital wardrobe app that helps users organize clothing items, create outfits, capsules and track wear frequency.

## Technology Stack

- **Frontend:** React + TypeScript + Vite
- **Backend:** Python
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

## Documentation

### Maintained Artifacts
- [Definition of Done](docs/definition-of-done.md)
- [User Stories Registry](docs/user-stories.md)
- [Product Roadmap](docs/roadmap.md)
- [Changelog](CHANGELOG.md)

### Course reports
- [Week 2 Report](reports/week2/README.md)
- [MVP v0 Report](reports/week2/mvp-v0-report.md)
- [User Stories (week 2)](reports/week2/user-stories.md)
- [Week 3 Report](reports/week3/README.md)

### License

- [License](LICENSE)

### Related Repositories 
- [Repository with backend](https://github.com/Mrxfg/digital-wardrobe)
- [Repository with frontend](https://github.com/veronika1977/digital_wardrobe_777)


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