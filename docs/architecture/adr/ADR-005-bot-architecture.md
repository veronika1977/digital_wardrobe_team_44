# ADR-005: Telegram Bot Architecture for Daily Notifications

## Status
Accepted

## Date
2026-07-07

## Context

The Digital Wardrobe application requires a Telegram Bot feature that:
- Sends daily reminders to users at 19:00 (user's local time)
- Provides inline buttons for quick wear tracking ("What did you wear today?")
- Updates the database with wear statistics based on user selections
- Handles multiple users across different timezones reliably

The system must gracefully handle cases when the Telegram API is unavailable or rate-limited.

**Important:** The bot must reuse the existing `/wear-records` API endpoint and `wear_records` table (introduced in Sprint 3 for US-13 Calendar) rather than creating a separate wear tracking infrastructure.

This ADR supports **US-15: Telegram Bot Daily Wear Tracking**

**Key Requirements:**

- Daily notifications at 19:00 per user's timezone
- Inline keyboard buttons for instant outfit selection (no typing required)
- Reliable delivery with retry logic
- Cost-effective and maintainable
- Compatible with existing FastAPI backend and Telegram WebApp SDK (frontend)
- Reuse existing `/wear-records` endpoint and `wear_records` table

## Decision

We will use a **polling-based architecture** where a separate notification worker periodically queries the backend API for users who need notifications, then sends messages via direct HTTP requests to the Telegram Bot API. The bot records wear events using the existing `POST /wear-records` endpoint.

### 1. Technology Stack

- **Backend API:** FastAPI (existing) — exposes:
  - `GET /bot-api/users-to-notify` — returns users who need notifications
  - `POST /wear-records` — existing endpoint, reused for bot wear tracking
  - `GET /wear-records` — existing endpoint for wear history
- **Notification Worker:** Separate Python process that polls the backend
- **Telegram Integration:** Direct HTTP requests to `https://api.telegram.org/bot<TOKEN>/sendMessage`
- **HTTP Client:** `aiohttp` for async API calls
- **Database:** PostgreSQL (shared with main backend)

### 2. Request Flow

```
Notification Worker (polling loop)
        ↓ (every 60 seconds)
GET /bot-api/users-to-notify
        ↓
Backend filters users:
  - notification_enabled = true
  - current time in user's timezone ≈ 19:00
  - no notification sent today
  - user has at least 1 outfit
        ↓
Returns list of {user_id, telegram_chat_id, recent_outfits}
        ↓
For each user:
  → Build message with inline keyboard (recent outfits as buttons)
  → POST to https://api.telegram.org/bot<TOKEN>/sendMessage
  → Log delivery to notification_log
        ↓
User clicks inline button → Callback Handler → POST /wear-records → Confirmation

```

### 3. Backend Endpoint: `/bot-api/users-to-notify`

**Responsibility:** Return users who need notifications RIGHT NOW, with their recent outfits for quick selection.

**Filtering logic (on backend side):**

1. `notification_enabled = true`
2. Current time in user's timezone is within notification window (19:00-19:05)
3. No notification sent today (check `notification_log`)
4. User has at least 1 outfit

### 4. Bot Authentication for `/wear-records`

The bot needs to create wear records on behalf of users. Two approaches considered:

**Approach A: Service Account Token (chosen)**
- Create a dedicated bot user in the `users` table with `telegram_id = 0`
- Issue a long-lived JWT for this bot user
- Bot includes this token in `Authorization` header when calling `POST /wear-records`
- The `user_id` field in `wear_records` is set to the actual user (not the bot)

**Approach B: Bot-specific endpoint**
- Create a new endpoint `POST /bot-api/wear-records` that accepts `user_id` + `outfit_id`
- Endpoint validates bot token, then creates wear record for the specified user
- More secure, but requires new code

**Decision:** Approach A is simpler and reuses existing infrastructure. The bot's JWT is stored in environment variable `BOT_JWT_TOKEN` and rotated monthly.

## Consequences

### Positive

- **Reuse over reinvent:** Leverages existing `/wear-records` infrastructure — less code, fewer bugs
- **Unified analytics:** Calendar (US-13) and Bot (US-15) share the same wear history
- **Separation of concerns:** Backend handles business logic, worker handles delivery
- **Testable:** Can mock `/bot-api/users-to-notify` and `/wear-records` in tests
- **Scalable:** Worker can be scaled independently
- **Resilient:** If backend is down, worker retries on next poll
- **No heavy dependencies:** Direct HTTP calls, no need for `python-telegram-bot` or `APScheduler`

### Negative

- **Polling overhead:** Worker makes API calls even when no users need notifications
- **Latency:** Up to 60s delay before notification is sent
- **Complexity:** Two processes to manage (backend + worker)
- **Bot token management:** Need service account token for bot to call `/wear-records` on behalf of users (mitigated by dedicated bot user with long-lived JWT, rotated monthly)

### Risks

- **Polling interval too long:** Users may receive notifications late (mitigated by 60s interval)
- **Worker crash:** Notifications may be missed (mitigated by supervisor/systemd restart)
- **Backend overload:** Frequent polling may stress backend (mitigated by caching)
- **Telegram policy changes:** Telegram may restrict proactive messages (mitigated by staying within 24h window rules)


## Alternatives Considered

### Alternative 1: Separate wear_log table for bot

**Pros:**
- Clean separation between Calendar and Bot wear tracking
- Can add bot-specific fields (e.g., response_time, button_clicked)

**Cons:**
- Data duplication (same wear event in two tables)
- Complex analytics (need to join two tables)
- More database migrations

**Decision:** Rejected. Reusing wear_records is simpler and provides unified analytics. Bot-specific metadata can be added as columns to wear_records if needed.

### Alternative 2: APScheduler (in-process)

**Pros:**
- No separate worker process
- Precise timing (no polling delay)
- Built-in timezone support

**Cons:**
- Tightly coupled with backend process
- If backend restarts, scheduler state may be lost
- Hard to scale independently

**Decision:** Rejected due to tight coupling and scaling limitations. Polling architecture provides better separation of concerns.

### Alternative 3: python-telegram-bot library

**Pros:**
- High-level abstractions for bot development
- Built-in callback handlers
- Active community

**Cons:**
- Additional dependency (~2MB)
- Overkill for simple notification sending
- Less control over HTTP-level details

**Decision:** Rejected for MVP v3 due to unnecessary complexity. Direct HTTP calls to Telegram Bot API are simpler and sufficient for our use case.

### Alternative 4: System Cron

**Pros:**
- Simple to set up
- OS-level reliability
- No additional dependencies

**Cons:**
- No timezone awareness (requires manual conversion per user)
- Difficult to manage per-user schedules
- Hard to monitor and debug

**Decision:** Rejected due to lack of timezone support. Backend-side filtering in `/bot-api/users-to-notify` is more flexible.

## Testing Strategy

- **Unit tests:** Mock `/bot-api/users-to-notify`, test worker loop logic, test callback handler
- **Integration tests:** Real backend + Telegram Bot API in staging
- **Timezone tests:** Verify backend correctly filters users by timezone
- **Retry tests:** Simulate Telegram API failures, verify retry behavior
- **Wear record tests:** Verify bot correctly calls `POST /wear-records` with valid data
- **Callback tests:** Verify inline button clicks trigger correct wear record creation

## Related Documents

- [US-15: Telegram Bot Daily Wear Tracking](https://github.com/veronika1977/digital_wardrobe_team_44/issues/218)
- [US-13: Calendar with Outfits](https://github.com/veronika1977/digital_wardrobe_team_44/issues/216)
- [ADR-003: Telegram Authentication (bot token reuse)](ADR-003-telegram-authentication.md)
- [Telegram Bot API Documentation](https://core.telegram.org/bots/api)

