# AGENTS.md — Guidelines for Coding Agents

This document provides operating instructions for AI coding agents working on the Digital Wardrobe project.

> Note: This project is part of Innopolis University Software Project course. All generated code must be reviewed by a human before merging.

---

## Repository Map

This project uses multiple repositories. Identify which repository you are working in before making changes:

| Repository | URL | Purpose |
|------------|-----|---------|
| **Coordination (this repo)** | `digital_wardrobe_team_44` | Assignment reports, documentation, ADRs, roadmap, handover docs |
| **Frontend** | `digital_wardrobe_777` | React + TypeScript + Vite Telegram Mini App |
| **Backend** | `digital-wardrobe` | FastAPI + PostgreSQL API server |

**Important:** This `AGENTS.md` file lives in the coordination repository (`digital_wardrobe_team_44`). 

---

## Source of Truth and Routing

Before editing, identify the authoritative source for the change:

| Topic | Authoritative Source | Location |
|-------|---------------------|----------|
| Artifact semantics and structure | Artifact Requirements | Course docs |
| Process and Scrum semantics | Process Requirements | Course docs |
| Repository workflow and CI | Repository Requirements | Course docs |
| Assignment 6 specifics | Assignment 6 spec | Course docs |
| Product architecture | ADRs | `digital_wardrobe_team_44/docs/architecture/adr/` |
| Quality requirements | Quality Requirements | `digital_wardrobe_team_44/docs/quality-requirements.md` |
| Contribution workflow | CONTRIBUTING.md | In each code repo |
| Agent guidelines | This file | `digital_wardrobe_team_44/AGENTS.md` |

When boundaries overlap, reason across all affected authoritative files before editing. Prefer updating the authoritative shared file over duplicating text.

---

## Project Context

Digital Wardrobe is a Telegram Mini App for personal wardrobe management with AI-powered outfit suggestions.

### Tech Stack

- **Frontend (digital_wardrobe_777):** React 18, TypeScript, Vite, TailwindCSS, Vitest, Telegram WebApp SDK
- **Backend (digital-wardrobe):** Python 3.10+, FastAPI, SQLAlchemy, PostgreSQL, pytest, aiohttp
- **AI Integration:** Qwen via DashScope API (OpenAI-compatible endpoint)
- **Bot Integration:** Telegram Bot API via direct HTTP requests
- **Deployment:** Cloudflare Pages (frontend), Docker Compose on VPS (backend)

---

## Essential Commands for Agents

### Frontend Repository (`digital_wardrobe_777`)

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Run tests
npm run test

# Run tests with coverage
npm run test -- --coverage

# Lint and type-check
npm run lint
npm run typecheck

# Build for production
npm run build
```

### Backend Repository (`digital-wardrobe`)

```bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run development server
python main.py

# Run tests
pytest

# Run tests with coverage
pytest --cov=src --cov-report=html

# Type-check
mypy src/

# Lint
flake8 src/ tests/
```

### Coordination Repository (`digital_wardrobe_team_44`)

```bash
# Check links (Lychee)
lychee . --exclude 'localhost' --exclude 't.me'

# Verify Markdown formatting
# (No build step — this repo contains docs and reports only)
```

---

## Repository Workflow for Agents

### Before Generating Code

1. Identify which repository you are working in (frontend, backend, or coordination)
2. Read the relevant issue or PBI to understand the expected outcome
3. Check existing code in the target module for style and patterns
4. Review related ADRs in `digital_wardrobe_team_44/docs/architecture/adr/` for architectural constraints
5. Verify acceptance criteria are testable

### When Generating Code

1. Follow existing code style:
   - Frontend: TypeScript strict mode, React functional components, TailwindCSS utilities
   - Backend: Python type hints, FastAPI dependency injection, SQLAlchemy ORM
2. Add tests for new functionality:
   - Frontend: Vitest unit tests for components
   - Backend: pytest unit/integration tests for endpoints and business logic
3. Update documentation if the change affects public APIs or setup steps
4. Use Conventional Commits format for commit messages:
   ```
   <type>(<scope>): <description>
   
   # Examples:
   feat(us-14): add AI outfit suggestion endpoint
   fix(backend): handle Telegram API timeout in auth flow
   docs(handover): update customer-handover.md for Week 6
   ```

### After Generating Code

1. Run local tests to verify the change works
2. Ensure no new linting or type-checking errors are introduced
3. Do not commit secrets, credentials, or PII
4. Link the change to the relevant issue in the PR description
5. For cross-repo changes, reference related PRs in other repositories

### Pull Request Expectations

- Every PR must link to an issue or PBI
- Include a brief description of changes and testing performed
- At least one human team member must review before merge
- CI checks must pass (linting, tests, build, coverage)
- For coordination repo changes: ensure links to code repos remain valid

---

## Sensitive Data and Safety Cautions

### Never Generate or Commit

- Real API keys, tokens, or credentials
- Database connection strings with passwords
- Personal data, PII, or customer-identifying information
- `.env` files with real values (use `.env.example` as template)

### Environment Variables Reference

**Backend (`digital-wardrobe`):**
```bash
TELEGRAM_BOT_TOKEN=       # From @BotFather
DASHSCOPE_API_KEY=        # From DashScope Console (Qwen AI)
DATABASE_URL=             # PostgreSQL connection string
SECRET_KEY=               # Application security key
```

**Frontend (`digital_wardrobe_777`):**
```bash
VITE_TELEGRAM_BOT_ID=     # Telegram bot ID for Mini App
VITE_API_BASE_URL=        # Backend API base URL
```

### If You Accidentally Expose Sensitive Data

1. Stop and alert a human team member immediately
2. Do not proceed with the commit or push
3. Help rotate the exposed credential if needed
4. Document the incident for the team

---

## Architecture and Design Constraints

### Backend (FastAPI) — `digital-wardrobe`

- Use dependency injection for testability
- All endpoints must have Pydantic models for request/response validation
- Database operations must use SQLAlchemy ORM (no raw SQL unless justified)
- Error handling must return appropriate HTTP status codes with JSON error format
- Bot notifications: use direct HTTP to Telegram Bot API with retry logic

### Frontend (React) — `digital_wardrobe_777`

- Use TypeScript with strict mode enabled
- Component props must have explicit types
- State management: prefer local state or context; avoid global stores unless necessary
- API calls must handle loading, error, and success states
- Telegram WebApp SDK: use `window.Telegram.WebApp` for Mini App integration

### AI Integration (Qwen via DashScope)

- Use OpenAI-compatible client for Qwen API calls
- Always implement timeout (10 seconds) and fallback logic
- Never send user PII to external AI APIs
- Cache responses for identical inputs to reduce API costs

### Cross-Repo Coordination

- API contracts between frontend and backend must be documented in `digital_wardrobe_team_44/docs/api/`
- Version changes to API endpoints must be reflected in CHANGELOG.md in the digital_wardrobe_team_44 repository
- Frontend should handle backend API errors gracefully (network failures, 4xx/5xx responses)

---

## Documentation Links for Agents

### Coordination Repository (`digital_wardrobe_team_44`)

- [CONTRIBUTING.md](CONTRIBUTING.md) — Human contributor workflow
- [README.md](README.md) — Project overview and repo map
- [docs/customer-handover.md](docs/customer-handover.md) — Customer-facing handover docs
- [docs/architecture/adr/](docs/architecture/adr/) — Architecture Decision Records
- [docs/testing.md](docs/testing.md) — Testing strategy and status
- [docs/quality-requirement-tests.md](docs/quality-requirement-tests.md) — Automated quality tests
- [docs/definition-of-done.md](docs/definition-of-done.md) — Completion criteria

---

## Course-Specific Reminders

- All work must be traceable to an issue or PBI in the relevant repository
- Maintain documentation: update ADRs, handover docs, and testing docs in the coordination repo when relevant changes are made
- Weekly reports (`reports/week6/`, `reports/week7/`) are graded artifacts in the coordination repo — do not modify unless instructed
- Demo Day preparation is mandatory — ensure generated code supports the final presentation

---

## When in Doubt

1. Ask a human team member before making architectural changes
2. Prefer small, incremental changes over large refactors
3. When generating tests, prioritize critical modules and user-facing flows
4. If acceptance criteria are unclear, request clarification before proceeding
5. If unsure which repository to modify, check the issue labels or ask the team

---

*This document is a maintained artifact. It is updated when agent workflow, commands, safety constraints, or linked documentation change.*

*Last updated: 2026-07-07*  
*Maintained by: Team 44 — Digital Wardrobe*