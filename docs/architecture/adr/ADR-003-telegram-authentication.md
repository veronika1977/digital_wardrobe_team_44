# ADR-003: Telegram Authentication

## Quality Requirements Impact

| QR | Impact | Evidence |
|----|--------|----------|
| **QR-001: API Response Time < 3s** | Supports | HMAC validation is <200ms; JWT stateless auth avoids DB lookup on each request |
| **QR-002: Fault Tolerance (100% data preservation)** |  Neutral | Auth layer doesn't handle user data; failures return 401 without data loss |
| **QR-003: Testability (≥30% critical module coverage)** | Supports | `initData` parsing and JWT generation are pure functions; easily unit-tested |

**Rationale:** Telegram's HMAC validation is fast and stateless JWT avoids per-request DB hits, supporting low latency (QR-001). The auth layer is isolated from data operations, so failures don't risk user content (QR-002 neutral). Core auth logic is pure and mockable for tests (QR-003).

## Status
Accepted

## Context

The Digital Wardrobe is a Telegram Mini App that needs user authentication. The team evaluated the following options:

- **Telegram Login Widget:** Native Telegram authentication using Telegram account
- **Email/Password:** Traditional registration with email verification
- **OAuth (Google, GitHub):** Third-party OAuth providers
- **Phone number verification:** SMS-based authentication

**Constraints:**

- Must work within Telegram Mini App interface
- Must provide seamless user experience (no separate registration)
- Must be secure and prevent unauthorized access
- Must comply with Telegram's Mini App guidelines

## Decision

The team selected **Telegram Login** for authentication.

**Rationale:**
1. **Seamless UX:** Users log in with their existing Telegram account — no forms, no emails, no passwords
2. **Native integration:** Telegram provides built-in authentication for Mini Apps
3. **Security:** Telegram verifies user identity cryptographically, preventing spoofing
4. **Reduced friction:** Eliminates registration barriers, increasing user adoption
5. **User data:** Automatically retrieves user ID, name, and profile photo from Telegram

## Consequences

### Positive

- **Zero registration friction:** Users start using the app immediately after opening
- **No password management:** Users don't need to remember passwords
- **Verified identity:** Telegram guarantees user authenticity
- **Lower development cost:** No need to build registration, email verification, password reset flows

### Negative

- **Telegram dependency:** Users must have a Telegram account to use the app
- **Limited user data:** Only get Telegram profile data (name, photo), no email or phone
- **Platform lock-in:** App is tied to Telegram ecosystem
- **VPN requirement:** Telegram is blocked in some regions, requiring VPN for access

### Neutral

- **Session management:** Still need to implement session tokens for API authentication
- **User mapping:** Must map Telegram user IDs to internal user records in PostgreSQL

## Related Quality Requirements

- **QR-001 (Time Behaviour):** Telegram authentication completes in < 1 second
- **QR-002 (Fault Tolerance):** If Telegram API is unavailable, show clear error message

## Related Documentation
- [docs/quality-requirements.md](../../quality-requirements.md)
- [docs/architecture/README.md](../README.md)
- [CHANGELOG.md](../../../CHANGELOG.md) — US-01 implementation

---

**Date:** 2026-06-29  
