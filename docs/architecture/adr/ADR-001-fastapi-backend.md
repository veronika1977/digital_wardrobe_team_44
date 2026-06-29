# ADR-001: FastAPI + PostgreSQL Backend

## Status

Accepted

## Context

The Digital Wardrobe project needed a backend framework for a Telegram Mini App that:
- Handles user authentication via Telegram
- Manages clothing items with photos
- Supports capsule wardrobes and calendar planning
- Integrates with AI services (Rembg for background removal)
- Must respond within 3 seconds (QR-001)
- Must achieve ≥30% test coverage (QR-003)

The team evaluated the following options:
- **Django:** Mature, feature-rich, but heavier and slower for async operations
- **FastAPI:** Modern, async-first, automatic OpenAPI docs, excellent performance
- **Flask:** Lightweight, but lacks built-in async support and validation
- **Express.js (Node.js):** Good performance, but team has more Python expertise

## Decision

The team selected **FastAPI** with **PostgreSQL** as the backend stack.

**Technology stack:**

- **Web framework:** FastAPI (async-first, Python 3.10+)
- **ASGI server:** Uvicorn (production-ready, handles async requests)
- **ORM:** SQLAlchemy 2.0 (async support, declarative models)
- **Database:** PostgreSQL (via `psycopg2-binary` driver)
- **Authentication:** `python-jose` (JWT tokens) + `passlib` (password hashing)
- **Configuration:** `python-dotenv` (environment variables)
- **Image processing:** `Pillow` + `pillow-heif` (HEIC support from iOS devices)
- **AI integration:** `rembg[cpu]` (background removal)
- **HTTP client:** `httpx` (async calls to external APIs like weather)
- **File uploads:** `python-multipart` (multipart/form-data handling)

**Rationale:**
1. **Async-first design:** FastAPI's async support enables concurrent handling of multiple requests, critical for AI service calls (Rembg) and weather API integration via `httpx`
2. **Automatic API documentation:** OpenAPI/Swagger docs generated automatically, reducing documentation maintenance effort
3. **Type safety:** Pydantic integration provides request/response validation out of the box
4. **Performance:** Benchmarks show FastAPI is 2-3x faster than Django for I/O-bound operations
5. **Team expertise:** Team has strong Python background, reducing learning curve
6. **PostgreSQL choice:** Robust relational database with JSON support for flexible metadata storage, accessed via SQLAlchemy ORM
7. **HEIC support:** `pillow-heif` enables processing of photos directly from iOS devices without manual conversion
8. **Async HTTP:** `httpx` allows non-blocking calls to external services (weather API, Telegram Bot API)


## Consequences

### Positive

- **Fast development:** Automatic validation and docs reduced boilerplate code by ~40%
- **High performance:** API response times consistently under 1 second (QR-001 validated)
- **Easy testing:** Dependency injection simplifies unit testing, helped achieve 66% coverage
- **Type safety:** Pydantic catches data errors at runtime, reducing bugs

### Negative

- **Smaller ecosystem:** Fewer third-party packages compared to Django
- **Learning curve:** Team needed to learn async/await patterns (mitigated by Python experience)
- **Less built-in admin:** No Django admin panel; custom admin interface required

### Neutral

- **Migration complexity:** PostgreSQL migrations via SQLAlchemy/Alembic require careful planning for production deployments
- **Deployment:** Requires Uvicorn as ASGI server (managed via Docker or systemd)
- **Environment configuration:** `python-dotenv` requires `.env` file management across environments (dev/staging/prod)
- **HEIC dependency:** `pillow-heif` adds ~5MB to the Docker image but enables iOS photo support

## Related Quality Requirements

- **QR-001 (Time Behaviour):** FastAPI's async design enables API response time < 3 seconds
- **QR-003 (Testability):** FastAPI's dependency injection simplifies unit and integration testing

## Related Documentation
- [docs/quality-requirements.md](../../quality-requirements.md)
- [docs/architecture/README.md](../README.md)
- [docs/development-process.md](../../development-process.md)

---

**Date:** 2026-06-29  