# 06 · Build plan (1–2 hours per day)

Hackathon: kickoff Oct 26, workshops Oct 27 – Nov 4, **submit by Nov 4, 9:00 PM ET**. US clocks go back on Nov 1, so 9:00 PM ET on Nov 4 (EST, UTC−5) is about **7:30 AM IST on Nov 5**. Re-check the time on the submission page. **Aim to submit on Nov 4 IST, a day early.**

## Budget
About 9 build days × 1–2 h ≈ 10–18 hours. Plan for 12. Anything beyond is a stretch.

## Pre-hackathon (now to Oct 25)
| Day | Time | Task |
|---|---|---|
| Oct 21–22 | 1 h | Application answers (see `application/`) |
| Oct 22–24 | 2 h total | Research playbook, competitor matrix |
| Oct 25 | 30 min | Submit application well before the deadline |

## During hackathon
| Day | Date | Hours | Goal | Done when |
|---|---|---|---|---|
| 0 | Oct 26 | 1 | Kickoff; read rules; API key; hello-world to Spark and SAM; record answers to the kickoff questions | One successful call to each model, noted in `docs/api-notes.md` |
| 1 | Oct 27 | 1.5 | Test SAM 3.1 on 5 UI screenshots (field, toast, row). Decide SAM vs fallback | Written verdict in `DECISIONS.md` |
| 2 | Oct 28 | 2 | Mock ledger app + invoice data per `data/README.md`. **Kill-check: API access** | App runs locally; 10 sample invoices |
| 3 | Oct 29 | 2 | Scripted agent + recorder + failure injection | One clean and one failing run recorded |
| 4 | Oct 30 | 2 | Claim extractor + value reader + deterministic comparer | Correct verdict on 5 hand-picked runs |
| 5 | Oct 31 | 2 | SAM region finder wired in; receipt builder + hash chain | HTML receipt for one run |
| 6 | Nov 1 | 2 | Generate 30 runs; run checkers A, B, C. **Kill-check: ≥70% clean-run accuracy** | Results table (tuning split) |
| 7 | Nov 2 | 1.5 | Held-out results; ablation; honest limits | Final numbers frozen |
| 8 | Nov 3 | 2 | README, diagram, GIF, 3-minute video | Video uploaded |
| 9 | Nov 4 | 1 | Submit early; keep a recorded demo as backup | Submission confirmed |

## Cut list (cut in this order if behind)
1. Real Muse computer-use agent
2. CI gate and CUAVerifierBench
3. Hash chain (keep a simple checksum list)
4. Ablation (keep A vs B vs C)
Never cut: the failing-run demo, the benchmark table, the limits section.

## Working rules
- Commit small, daily. Write one line in `docs/devlog.md` each day (create this file): what worked, what broke.
- Save every prompt that works into `docs/prompts.md` (create this file).
- Never commit keys. `.env` stays out of git.
- Use Muse Code or any coding agent to speed up boilerplate, but understand every line you submit.
