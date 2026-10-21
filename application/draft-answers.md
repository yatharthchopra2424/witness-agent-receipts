# Draft answers

Status: **skeleton only.** Real answers are written one question at a time once `form-questions.md` is filled. Everything below is a reusable source text; trim to each limit.

## Project idea (≈100 words, reusable)
Witness gives every AI-run task a receipt. When an AI agent or automation types invoices into software with no API, it can report "done ✅" while a digit is wrong or a save silently failed. Witness watches the screen recording, extracts what the agent claimed, uses SAM 3.1 to find the relevant fields and messages, and Muse Spark to read their values from the pixels. Code then compares them with the source invoice. Each claim gets VERIFIED, MISMATCH or UNVERIFIABLE with an annotated frame as evidence. I will measure how many false successes a text-log judge, a whole-frame vision judge and Witness each miss, on 30 synthetic runs.

## Theme fit
Push the Frontier (software): giving agent-run work an independent, auditable check. Also Build for Your World: the clerk in a small Indian back office who cannot re-check every row.

## Technical skill (≈100 words, reusable)
I build production LLM agents and eval harnesses. OSINT Scout (LangGraph, claim-level citations, discards unsupported facts, eval harness that fails the CI build) and the IT Desk Agent (hybrid retrieval, safety eval gate, tamper-evident audit trail) are live with demo videos. I have shipped video detection and tracking (YOLOv8 bird counting on CCTV, served with FastAPI) and forecasting systems (GridCast, XGBoost + LSTM). Witness combines these: agent claims, evidence, an audit trail and a measured benchmark.

## Feasibility (≈80 words)
Scope is deliberately small: a mock ledger app, a scripted agent with injected failures, and a 30-run benchmark. Models read values; deterministic code compares them. I have a day-by-day plan for about 12 hours of work, with kill criteria and a fallback. Estimated model cost is under $20 at published Meta prices.

## Meta models to be used
Muse Spark 1.3 (structured claims, reading values from crops), SAM 3.1 (grounding fields and messages in video frames), Meta Model API. Optional: Muse Wonder / Muse Code.

## Honest-limits sentence (use where space allows)
"Failures are synthetic and the mock app is cleaner than real software; I will report that, and whether SAM crops actually beat whole-frame reading."

## Do not write
"State of the art", "better than WebJudge", any statistic about how often automations fail, anything implying testing on real portals.
