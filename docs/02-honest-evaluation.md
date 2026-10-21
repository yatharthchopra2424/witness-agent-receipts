# 02 · Honest evaluation

Written as a skeptical judge would write it. Re-read before every major decision.

## Verdict
**Worth building in the narrow form. Not worth it as "a better judge".**

## Novelty: what already exists
| Work | What it does | Reported result | Source quality |
|---|---|---|---|
| WebJudge (Online-Mind2Web) | LLM judge over key screenshots | ~85% agreement with humans | Peer-style paper; authors' numbers |
| AgentRewardBench | Benchmark of 12 judges on 1,302 trajectories | No single judge wins everywhere | Paper |
| Universal Verifier + CUAVerifierBench (Microsoft, `microsoft/fara`, MIT) | Rubric-based verifier; open human-labelled benchmark | Claims near-zero false positives vs ≥22% (WebJudge) and ≥45% (WebVoyager) | Authors' claim; abstract read only |
| "Are We Done Yet?" | Vision judge for computer-use agents | up to 73% accuracy, 42 macOS apps | Workshop paper; abstract read only |
| web-eval-agent (refreshdotdev) | MCP server that evaluates web apps | 1.2k stars; **sunset** | README |

**Consequence:** a general "screenshot judge" is not novel. We must not claim it is.

## What is still open (our wedge)
- Existing judges give **one verdict per task**. They do not produce a **per-claim, pixel-grounded receipt** with cropped evidence.
- They focus on web tasks; **UI-without-API back-office entry** is a narrow scenario with a clear user.
- A **tamper-evident** evidence trail (hash chain) is not what those papers focus on. (Unverified; check during research.)

## Honest scorecard (my current estimate, 1–5)
| Criterion (indie track) | Score | Why |
|---|---|---|
| Creativity | 3.5 | Receipt framing is fresh; underlying idea is not. |
| Technical ambition | 3.5–4 | Multi-model pipeline plus a measured benchmark. Higher if CUAVerifierBench stretch lands. |
| Works / demo-able | 4 | Mock app + scripted agent is controllable. Risk is low if scope is held. |
| Real-world clarity | 4 | Easy to explain to non-experts. |

## Biggest risks (ordered)
1. **API access from India is unconfirmed.** July 2026 launch reporting described a US-only public preview. Hackathon access is promised to accepted participants. Confirm at kickoff. Fallback: partner-hosted open weights (Baseten/Modal/Fireworks credits), vision support unchecked.
2. **SAM may not help.** If SAM crops do not beat whole-frame reading, say so. A negative result reported honestly is still a result.
3. **Time.** 1–2 h/day gives roughly 10–18 hours. Cut stretch goals first.
4. **Demo failure.** Always keep a recorded demo.
5. **Judge-model bias.** Spark reading Spark-written claims could share errors. Mitigate with deterministic checks (exact string compare of numbers) after reading.
6. **Overclaiming.** Use words like "in our 30-run benchmark" not "state of the art".

## Kill criteria (stop and switch to the fallback idea)
- No working Meta API access by **Oct 28**.
- By **Nov 1** the pipeline cannot read a field value correctly on at least 70% of clean (no-failure) runs.
Fallback: *Sentinel Walk* (SAM-based site-inspection reports), see `DECISIONS.md`.

## What I have not verified
Full text of the papers; whether general eval tools (Promptfoo, DeepEval, Braintrust, Langfuse, Phoenix, Inspect) offer visual verification; RPA vendors' own verification features; the OpenAdapt "5 of 7 faults silently pass" claim (vendor source). These go in `research/open-questions.md`.
