# Lychee Exclusions Justification

This document justifies every exclusion in the Lychee link checker configuration.

## Configuration
- **Workflow:** `.github/workflows/lychee.yml`
- **Checked files:** All repository Markdown (`./**/*.md`)
- **Runs on:** Push to main, PRs to main, manual dispatch

## Exclusions

### 1. `http://localhost` and `http://127.0.0.1`

**Pattern:** `--exclude 'http://localhost'`, `--exclude 'http://127.0.0.1'`

**Justification:**
Local development URLs are not accessible from GitHub Actions CI runners.
These links appear in `docs/setup.md` and other developer documentation
as examples for local setup instructions.

**Category:** Local development (not publicly accessible)

---

### 2. `mailto:` links

**Pattern:** `--exclude '^mailto:'`

**Justification:**
Lychee is an HTTP/HTTPS link checker and cannot validate email addresses.
Email links use the `mailto:` protocol, which is outside Lychee's scope.

**Category:** Non-HTTP protocol (technical limitation)

---

## What is NOT excluded (and why)

The following link types are **validated by Lychee** (not excluded):

| Link Type | Why Validated |
|-----------|---------------|
| `https://github.com/...` | Public GitHub links; GITHUB_TOKEN avoids rate limits |
| `https://youtube.com/...` | Public YouTube videos |
| `https://t.me/...` | Public Telegram bots/channels |
| `https://docs.python.org/...` | Public documentation |
| Relative links (`docs/setup.md`) | Repository-relative, always accessible |

## Verification Process

Before each submission:
1. Run `lychee` locally to identify broken links
2. Fix broken links rather than excluding them
3. Document any new exclusions with justification
4. Manually verify excluded links work (where applicable)
