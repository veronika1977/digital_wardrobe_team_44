# ADR-004: AI Strategy for Outfit Generation

## Status
Accepted

## Date
2026-07-07

## Context

The Digital Wardrobe application requires an AI-powered outfit suggestion feature that generates personalized outfit recommendations based on:

- User's existing wardrobe inventory

The system must gracefully handle cases when the AI service is unavailable.


This ADR supports **US-14: AI Stylist**

**Key Requirements:**

- Fallback mechanism when AI is unavailable
- High-quality outfit reasoning in Russian (primary audience language)
- Cost-effective for production use
- Maintainable and extensible for future AI models

## Decision

We will use **Qwen AI** (Alibaba Cloud) via the **DashScope OpenAI-compatible API** with the following architecture:

### 1. LLM Provider Selection

- **Primary:** Qwen
- **Model:** `qwen-plus` (balanced quality/cost) or `qwen-turbo` (faster, cheaper)
- **Fallback:** Return top-N most versatile items from user's wardrobe 
- **API Format:** OpenAI-compatible REST API (allows switching to OpenAI/Anthropic if needed)

### 2. Request Flow

```
User Request → Backend API → Qwen API → Parse Response → Return Outfits
                                    ↓ (timeout / error)
                              Fallback Logic → Return versatile items
```

### 3. Retry Strategy

- **HTTP timeout:** 10 seconds (technical default, not a performance requirement)
- **Retries:** 1 retry with exponential backoff (1s, 2s)
- **Fallback trigger:** If both attempts fail or timeout, use fallback logic

### 4. Fallback Logic

When Qwen is unavailable:

1. Sort by versatility score (items that match more tags rank higher)
2. Return top 3-5 items as "suggested basics"
3. Mark response with `{"fallback": true, "reason": "llm_unavailable"}`

### 5. Prompt Engineering

System prompt structure (optimized for Qwen's Russian language capabilities):

```
Ты — ассистент-стилист. На основе гардероба пользователя 
предложи полноценный образ. Образ должен включать 2-4 вещи, которые хорошо сочетаются. Учитывай:
- Сочетание цветов
- Стилистическую согласованность

Верни ответ в формате JSON:

{
  "outfits": [
    {
      "items": ["item_id_1", "item_id_2"],
      "reasoning": "Краткое объяснение"
    }
  ]
}

```


### 6. Caching Strategy

- Cache Qwen responses for identical inputs (wardrobe hash) for 1 hour
- Reduces API costs and improves response time for repeated queries

## Consequences

### Positive

- **Excellent Russian language support:** Qwen is optimized for Russian — better outfit reasoning quality for our primary audience vs. GPT-4o-mini
- **Fast response:** `qwen-turbo`/`qwen-plus` typically respond within 2-4 seconds
- **Graceful degradation:** Fallback ensures feature always works
- **Cost-effective:** Qwen pricing is competitive (~$0.0008-0.002 per 1K tokens)
- **Provider-agnostic:** OpenAI-compatible API allows switching to OpenAI, Anthropic, etc.
- **Testable:** Mock Qwen responses in unit tests
- **Privacy-friendly:** DashScope offers data processing agreements compliant with Russian regulations

### Negative

- **External dependency:** Relies on DashScope API availability
- **Cost:** ~$0.001 per request (acceptable for MVP, may need optimization at scale)
- **Prompt maintenance:** Prompts may need tuning based on user feedback
- **Privacy:** User wardrobe data sent to external API (mitigated by not storing responses)

### Risks

- **API rate limits:** DashScope has rate limits (mitigated by caching)
- **Response quality:** AI may suggest inappropriate outfits (mitigated by fallback + user feedback loop)
- **Region availability:** DashScope may have regional restrictions (mitigated by fallback)

## Alternatives Considered

### Alternative 1: OpenAI GPT-4o-mini

**Pros:**

- Industry-standard quality
- Extensive documentation
- Large ecosystem

**Cons:**

- Weaker Russian language quality compared to Qwen for our use case
- More expensive (~$0.003 per 1K tokens vs. Qwen's ~$0.001)
- Potential payment issues from Russia (requires foreign card)

**Decision:** Rejected due to higher cost, payment complexity from Russia, and slightly weaker Russian language quality for fashion domain.

### Alternative 2: Local AI Model (e.g., LLaMA, Qwen local)

**Pros:**

- No external API dependency
- No per-request cost
- Full data privacy

**Cons:**

- Requires significant compute resources (GPU or high-end CPU)
- ~170MB+ model size (similar to Rembg, but slower inference)
- Complex deployment (model serving infrastructure)
- Slower inference on CPU (>10s for complex prompts)

**Decision:** Rejected for MVP v3 due to deployment complexity and latency concerns. Can be reconsidered for post-course production if user base grows.

### Alternative 3: Rule-Based System (No AI)

**Pros:**
- Zero external dependencies
- Instant response (<100ms)
- No API costs
- Fully predictable behavior

**Cons:**

- Limited personalization (cannot learn from user preferences)
- Less engaging user experience

**Decision:** Rejected because AI personalization is a key differentiator for US-14. Fallback logic serves as a simplified rule-based backup.

### Alternative 4: YandexGPT

**Pros:**

- Excellent Russian language support
- Local provider (Russian payment methods)
- Data residency in Russia

**Cons:**

- More expensive than Qwen
- Less flexible API
- Smaller community / fewer examples

**Decision:** Rejected due to higher cost and less flexible API. Qwen provides better price/quality ratio while maintaining strong Russian language support.

## Testing Strategy

- **Unit tests:** Mock Qwen responses, verify JSON parsing, test fallback logic
- **Integration tests:** Real Qwen API calls in staging environment
- **Fallback tests:** Simulate Qwen unavailability, verify graceful degradation
- **Russian language tests:** Verify prompt quality and response language in Russian
- **Error handling tests:** Verify behavior on malformed responses, empty wardrobe, invalid JSON

## Related Documents

- [US-14: AI Stylist](https://github.com/veronika1977/digital_wardrobe_team_44/issues/217)
- [ADR-002: Rembg Background Removal (similar fallback pattern)](ADR-002-rembg-background-removal.md)
- [DashScope Documentation](https://www.alibabacloud.com/help/en/model-studio/)