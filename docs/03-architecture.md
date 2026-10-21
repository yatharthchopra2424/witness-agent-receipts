# 03 · Architecture (planned, no code yet)

## Pipeline

```
 ┌────────────┐   video + action log   ┌────────────────┐
 │ Mock ledger │ ─────────────────────▶ │ Recorder        │
 │ app + agent │                        │ (browser video) │
 └────────────┘                        └───────┬────────┘
                                               │ frames (sampled)
        agent's final message                  ▼
              │                        ┌────────────────┐
              ▼                        │ Region finder   │  SAM 3.1: text prompts like
      ┌───────────────┐                │ (SAM 3.1)       │  "amount field", "error toast"
      │ Claim extractor│               └───────┬────────┘
      │ (Muse Spark)   │                       │ crops + masks
      └──────┬────────┘                        ▼
             │ structured claims        ┌────────────────┐
             └────────────────────────▶ │ Value reader +  │  Muse Spark vision, then
                                        │ comparer        │  deterministic string/number match
                                        └───────┬────────┘
                                                ▼
                                        ┌────────────────┐
                                        │ Receipt builder │  verdicts + annotated frames
                                        │ + hash chain    │  + HTML report
                                        └────────────────┘
```

## Components and contracts

| Component | Input | Output | Meta model | Notes |
|---|---|---|---|---|
| Recorder | Mock app session | Video, timestamped action log | none | Browser video capture; no Meta call. |
| Claim extractor | Agent final message + log | JSON list of claims (invoice id, field, value) | Muse Spark 1.3, structured output | Schema-validated JSON. |
| Region finder | Sampled frames + text prompts | Boxes and masks per prompt | SAM 3.1 | $0.20 per 1,000 video frames. |
| Value reader | Region crops | Text value per field | Muse Spark 1.3 vision | Ask for the raw text only; no reasoning in the answer. |
| Comparer | Read value + source invoice | match / mismatch | none | **Deterministic** compare. Do not let an LLM decide equality. |
| Toast/state detector | Frames around save action | error / success / none | Spark + SAM | Catches silent failures. |
| Receipt builder | All of the above | HTML report, JSON, annotated frames, hash chain | none | Hash chain = tamper evidence. |

## Design principles
1. **Deterministic where possible.** Models read; code compares.
2. **Evidence first.** Every verdict links to a frame and a crop.
3. **Three verdicts only.** VERIFIED · MISMATCH · UNVERIFIABLE. Unsure is never "verified".
4. **Separate process from outcome.** (Idea borrowed from the Universal Verifier paper; credit it.)
5. **Cheap by default.** Sample frames around save events, not every frame.

## Open design questions
- How many frames per invoice are enough? (decide with a small pilot)
- Does SAM 3.1 handle UI elements (text fields, toasts) well, or is it better at physical objects? **Test on day 3 before committing.** If poor, use Spark's own grounding and report it honestly.
- Is video input to SAM billed per frame at our sampling rate? (check the pricing page; $0.20 per 1,000 frames)
- Which reasoning-effort setting is best for reading text? (probably low)

## Cost estimate (rough, label as estimate)
30 runs × 10 invoices × ~6 frames ≈ 1,800 frames → SAM roughly **$0.36**. Spark vision tokens depend on image size; plan on **under $20** total including retries. Check real usage in the dashboard after the pilot.
