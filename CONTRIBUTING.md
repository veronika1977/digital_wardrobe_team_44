# Contributing to Digital Wardrobe

Thank you for your interest in contributing to Digital Wardrobe — a Telegram Mini App for personal wardrobe management with AI-powered outfit suggestions.

This document outlines the process for contributing to the project. Please read it before submitting your first contribution.

> Note: This project is part of Innopolis University Software Project course (Assignment 6). All contributions must follow the course requirements.

---

## Quick Start

### Prerequisites

- Node.js 18+ (for frontend)
- Python 3.10+ (for backend)
- Git
- Telegram account (for testing Mini App)

### Repository Structure

```
digital_wardrobe_team_44/
├── frontend/          # React + TypeScript + Vite
├── backend/           # FastAPI + PostgreSQL
├── docs/              # Documentation (ADRs, handover, etc.)
├── reports/           # Weekly reports for Assignment 6
├── CONTRIBUTING.md    # This file
├── AGENTS.md          # Rules for AI assistants
└── README.md          # Project overview
```

### Local Development Setup

**Clone the repository**

```bash
git clone https://github.com/veronika1977/digital_wardrobe_team_44.git
cd digital_wardrobe_team_44
```

**Frontend setup**
```bash
git clone https://github.com/veronika1977/digital_wardrobe_777.git
cd digital_wardrobe_777
npm install
npm run dev
```

**Backend setup (in another terminal)**
```bash
git clone https://github.com/Mrxfg/digital-wardrobe.git
cd digital-wardrobe
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**Set environment variables (see .env.example)**
```bash
export TELEGRAM_BOT_TOKEN="your_token"
export DASHSCOPE_API_KEY="your_key"
export DATABASE_URL="postgresql://user:pass@localhost:5432/wardrobe"
```

**Run backend**
```bash
python main.py
```

---

## Branching Strategy

We use a simplified Git Flow:

| Branch | Purpose |
|--------|---------|
| `main` | Protected. Only merged PRs from `develop` or hotfixes. Tags for releases (v2.1.0, v3.0.0). |
| `develop` | Integration branch. All features merge here first. |
| `feature/*` | New features (e.g., `feature/us-14-ai-stylist`). Branch from `develop`. |
| `fix/*` | Bug fixes (e.g., `fix/telegram-auth-timeout`). Branch from `develop` or `main`. |
| `docs/*` | Documentation updates (e.g., `docs/update-handover`). |

### Branch Naming Convention

```
<issue-number>/<short-description>

# Examples:
217-ai-stylist-endpoint
218-bot-notification-worker
```

---

## Commit Message Convention

We use Conventional Commits for clear history and automated changelogs.

### Format
```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | When to use |
|------|-------------|
| `feat` | New feature (user-facing) |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no logic change |
| `refactor` | Code change, no new feature/bugfix |
| `test` | Adding/updating tests |
| `chore` | Build, config, tooling (no production code) |

### Examples
```bash
# Good:
feat(us-14): add AI outfit suggestion endpoint
fix(backend): handle Telegram API timeout in auth flow
docs(handover): update customer-handover.md for Week 6
test(frontend): add Vitest tests for PaywallModal
chore(ci): add Lychee link checker to GitHub Actions

# Bad:
update code
fixed bug
wip
```

---

## Pull Request Process

### Before Creating a PR

1. Create an issue (or link existing one) describing the change
2. Branch from `develop` (not `main`)
3. Write tests for new functionality
4. Run local checks:
   ```bash
   # Backend
   cd backend
   pytest --cov=src
   
   # Frontend
   cd frontend
   npm run test
   npm run lint
   ```

### PR Template

Every PR must include:

```markdown
## Description
[Brief description of changes]

## Related Issue
Closes #<issue_number>

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation
- [ ] Refactoring
- [ ] Tests

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests pass
- [ ] Manual testing completed (screenshots if UI)

## Checklist
- [ ] Code follows project style guide
- [ ] Self-reviewed my code
- [ ] Added comments for complex logic
- [ ] Updated documentation (if needed)
- [ ] No new warnings/errors
```

### Review Process

1. Assign reviewers: At least 1 team member (different from implementer)
2. CI checks must pass: linting, type-check, tests, build
3. Address feedback: Respond to all review comments
4. Squash and merge: Use "Squash and merge" for clean history
5. Delete branch: After merge, delete feature branch

### Definition of Done

A PBI/issue is "Done" when:

- [ ] Code is merged to `develop` (or `main` for hotfixes)
- [ ] All tests pass (unit + integration)
- [ ] CI pipeline is green
- [ ] Documentation updated (if applicable)
- [ ] Peer review completed
- [ ] No critical security issues
- [ ] Feature tested in staging environment

See [Definition of Done](docs/definition-of-done.md) for details.

---

## Testing Requirements

### Backend (FastAPI)

```bash
# Run all tests
cd backend
pytest

# With coverage
pytest --cov=src --cov-report=html

# Specific test file
pytest tests/test_auth.py
```

**Requirements:**
- Minimum 30% overall coverage (QRT-001)
- Critical modules: >=70% coverage
- All new code must have tests

### Frontend (React + Vitest)

```bash
# Run tests
cd frontend
npm run test

# With coverage
npm run test -- --coverage

# Watch mode
npm run test -- --watch
```

**Requirements:**
- Component tests for all user-facing UI
- Integration tests for critical flows (auth, item creation)

### End-to-End (Manual)

Before merging, verify in staging:
1. Telegram Mini App loads correctly
2. Auth flow works (new + existing user)
3. Core features functional (add item, create outfit, etc.)

---

## Documentation

### When to Update Docs

Update documentation when:
- Adding new API endpoints -> Update `docs/api/README.md`
- Changing architecture -> Create/update ADR in `docs/architecture/adr/`
- Modifying setup/deploy steps -> Update `README.md`
- Changing contributor workflow -> Update this file

### Documentation Locations

| Doc | Path | Purpose |
|-----|------|---------|
| API Reference | `docs/api/README.md` | Endpoint specs, examples |
| Architecture | `docs/architecture/` | ADRs, diagrams, decisions |
| Handover | `docs/customer-handover.md` | Customer-facing transfer docs |
| Quality | `docs/testing.md`, `docs/quality-requirement-tests.md` | Testing strategy, QRTs |
| Process | `docs/development-process.md` | Git workflow, DoD, reviews |

---

## AI Assistant Guidelines

This project uses AI assistants for code generation and documentation. When working with AI tools:

1. Read `AGENTS.md` first — it contains rules for AI assistants
2. Never commit AI-generated code without review — always verify logic, security, and style
3. Disclose AI usage in PR description if AI helped generate the code
4. Test thoroughly — AI may generate code that looks correct but has edge-case bugs

See [AGENTS.md](AGENTS.md) for detailed rules.

---

## Security and Secrets

### Never Commit

- `.env` files with real credentials
- API keys, tokens, passwords
- Database connection strings with credentials
- Personal data or PII

### Use Environment Variables

Store secrets in environment variables or secret manager:

```bash
# Example .env (NOT committed)
TELEGRAM_BOT_TOKEN=123456:ABC-DEF...
DASHSCOPE_API_KEY=sk-...
DATABASE_URL=postgresql://user:pass@host:5432/db
SECRET_KEY=your-secret-here
```

### Rotate Secrets

If a secret is accidentally committed:
1. Revoke/regenerate the secret immediately
2. Remove it from git history (use `git filter-branch` or BFG)
3. Update all environments with new secret
4. Document the incident in team chat

---

## Reporting Issues

Found a bug? Please:

1. Search existing issues to avoid duplicates
2. Create a new issue with:
   - Clear title and description
   - Steps to reproduce
   - Expected vs actual behavior
   - Environment (OS, browser, Telegram version)
   - Screenshots/logs if applicable
3. Label appropriately: `bug`, `frontend`, `backend`, `priority:high`, etc.

---

## Getting Help

- Questions? Ask in team chat or create a `question` issue
- Code review stuck? Tag `@veronika1977` (Scrum Master)
- Architecture decisions? Refer to `docs/architecture/adr/` or create new ADR

---

## Course-Specific Notes

This repository is part of Innopolis University Software Project course. Key reminders:

- All work must be traceable: Link every PR to a PBI/issue
- Maintain documentation: `customer-handover.md`, `AGENTS.md`, ADRs must be current
- Weekly reports: `reports/week6/`, `reports/week7/` are graded artifacts
- Demo Day prep: Week 7 lab rehearsal + Week 8 presentation are mandatory


---

*This document is a maintained artifact. It is updated when contribution workflow, verification commands, review expectations, or linked documentation change.*

*Last updated: 2026-07-07*  
*Maintained by: Team 44 — Digital Wardrobe*