# 04 · Meta stack: what we use and what we get

Source: dev.meta.ai pages fetched 2026-10-21. Re-check at kickoff; prices and limits change.

## What we use from Meta
| Meta product | Model ID | Our use | Required? |
|---|---|---|---|
| Meta Model API | base URL `https://api.meta.ai/v1` (OpenAI-SDK compatible) | All model calls | Yes |
| Muse Spark 1.3 | `muse-spark-1.3` | Claim extraction (structured JSON), reading values from crops, state detection | Yes |
| SAM 3.1 | `sam-3.1` | Find fields, rows, toasts by text prompt in video frames; masks for annotated evidence | Yes (core Meta differentiator) |
| Muse Wonder | `muse-wonder-1.0` | Stretch: a real computer-use agent as a test subject | Optional |
| Muse Code | CLI | Stretch: speed up building; audit/replay patterns from its cookbook | Optional |
| Muse Spark Open / Glimmer | open weights | Fallback if the hosted API is unavailable; run via partner credits | Fallback |
| Muse Image, Voice Transcribe | | Not used | No |

Cookbook pages worth reading first: Quickstart (chat completions), Structured output, Vision input, SAM API basics, Perception grounding, Computer use, Deterministic replay in CI, Error handling and retry. All at dev.meta.ai/docs/cookbook/.

## Prices (pay-as-you-go)
| Item | Price |
|---|---|
| Muse Spark 1.3 input / cached input / output | $1.25 / $0.15 / $4.25 per 1M tokens |
| Muse Spark 1.3 **Contributor** input / cached / output | $0.10 / $0.002 / $0.20 per 1M tokens |
| Muse Wonder input / cached / output | $4.00 / $0.20 / $20.00 per 1M tokens |
| SAM 3.1 | $2.50 per 1,000 images · $0.20 per 1,000 video frames |
| Web search grounding | $2.50 per 1,000 queries (not needed) |

## Rate limits (per team)
Muse Spark 1.3: 3,000 requests/min, 4M tokens/min. SAM 3.1: 3,000 requests/min. Far above what we need.

## ⚠️ Contributor mode
Cheaper, but you **let Meta use your prompts, code, files and model responses to train future models.** Rule for this project: **standard mode by default.** Contributor mode only if we send nothing but synthetic data and cost becomes a real problem. Never with real invoices.

## What the hackathon gives us (complimentary)
Confirmed from the event page:
- Free entry if selected. Virtual, worldwide (except sanctioned regions).
- "Access to our newest models" (details of credits **not stated**).
- Live workshops from Meta and partners, Oct 27 – Nov 4, plus office hours on Discord.
- Share of a **$1,000,000 cash prize pool** across the Indie and Startup tracks (split **not published**).
- Partner credits for **select participants**, for Meta's open-weights models:
  - Baseten: $100 credits and 2M tokens-per-minute rate limits
  - Modal: $100 credits (Endpoints, serverless GPUs, sandboxes, training tools)
  - Fireworks: $25 credits, plus a workshop by Sinan Ozdemir

Not confirmed (ask at kickoff):
- Free Model API credits for participants. A July 2026 Reuters-sourced report mentioned $20 free credits for new US sign-ups; the pricing page today says nothing about credits.
- Whether the Model API is available from India (the docs list no restriction, but a July report described a US-only preview).
- Whether a Muse Code subscription is included (plans are $5–$200 per month).

## Account setup checklist (after approval on Oct 26)
1. Create a Model API account and open the dashboard.
2. API keys → Create API key. Store as env var `MODEL_API_KEY`. Never commit it.
3. The OpenAI SDK does not read `MODEL_API_KEY` by itself; pass it explicitly.
4. Make one call to `muse-spark-1.3` and one to `sam-3.1`. Record latency and token usage in `docs/api-notes.md` (create this file).
5. Set a spending alert if the dashboard offers one.
