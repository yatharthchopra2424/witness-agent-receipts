# 07 · Presentation plan

Goal: someone with no AI background understands the project in 30 seconds and believes it in 3 minutes.

## Patterns copied from top repos (checked 2026-10-21 via `gh`)
| Repo | Stars | Pattern to copy |
|---|---|---|
| browser-use/browser-use | ~119k | One-line promise as title; "which do I need?" table; three quickstart paths; benchmark section |
| microsoft/fara | ~6k | Badges; dated "Updates" log; "Key capabilities"; "Performance highlights"; separate benchmark section |
| OSU-NLP-Group/Online-Mind2Web | ~0.2k | Results table that compares against existing methods |
| promptfoo/promptfoo | ~26k | Short README: what, why, quickstart |
| facebookresearch/sam3 | ~12k | Runnable examples near the top |
Also read OSINT-Scout-Ainos (your own README) as the style you already do well: demo video up top, contents list, screenshots per screen.

## README order (final)
1. Title + tagline + status badges
2. 20-second GIF: failing run → red circle → receipt
3. The problem in 3 lines
4. Results table (A vs B vs C) with counts
5. Quickstart (target: 4 commands)
6. How it works (one diagram)
7. Meta models used (table)
8. Honest limits
9. Related work (credit WebJudge, Universal Verifier, others)
10. Reproduce the benchmark

## 3-minute video script
| Time | Scene | Voice-over idea |
|---|---|---|
| 0:00–0:25 | Agent finishes: "All 10 invoices posted ✅" | "This is what AI agents tell us. Can we trust it?" |
| 0:25–1:15 | Witness replays; red circle on ₹48,520 vs ₹48,250; silent error toast on #1047 | "Witness checks the screen, not the story." |
| 1:15–2:00 | Bar chart: missed failures for A, B, C | "In our 30-run test, the text log missed X of N. Witness missed Y." (fill with real numbers) |
| 2:00–2:40 | Architecture diagram | "Muse Spark reads, SAM 3.1 finds, code compares." |
| 2:40–3:00 | Limits + who it's for | "Best when you have no backend access. Not a replacement for database checks." |

Rules: show the failure before explaining anything; use real numbers only; no jargon in the first minute; add captions.

## Slide deck (if the submission asks for one), 8 slides
1. Title + tagline  2. Problem  3. Who it hurts (the clerk)  4. Demo screenshot  5. How it works  6. Results  7. Meta models used  8. Limits + next steps

## Plain-language glossary (put in README)
- **Agent**: software that uses an AI model to do tasks on its own.
- **Claim**: something the agent says it did.
- **Receipt**: our proof of what the screen showed for each claim.
- **Segmentation (SAM)**: marking exactly which pixels belong to an object, like a field or a message.

## Quality checklist before submitting
- [ ] A stranger can say what it does after 30 seconds
- [ ] Every number in the README is reproducible from the repo
- [ ] Limits section present and honest
- [ ] Credits to prior work present
- [ ] No keys, no personal data, no phone numbers in the repo
- [ ] Demo works from a clean clone; backup video recorded
