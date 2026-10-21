# Witness

**Don't trust the agent's word. Check the screen.**

![Status: planning](https://img.shields.io/badge/status-planning-orange)
![Hackathon: Meta Global AI Developer](https://img.shields.io/badge/hackathon-Meta%20Global%20AI%20Developer-0668E1)
![Track: Indie](https://img.shields.io/badge/track-Indie%20developer-blue)
![Models: Muse Spark 1.3 + SAM 3.1](https://img.shields.io/badge/models-Muse%20Spark%201.3%20%2B%20SAM%203.1-informational)
![Code: none yet](https://img.shields.io/badge/code-none%20yet-lightgrey)

Witness gives every AI-run task a *receipt*: what the agent **claimed** it did, and what the screen **actually showed**.

> **Status: planning (no code yet).** Built for the [Meta Global AI Developer Hackathon](https://dev.meta.ai/events/global-hackathon), Indie developer track. Build window: Oct 26 – Nov 4, 2026. Submission due Nov 4, 9:00 PM ET.

---

## The problem in 30 seconds

AI agents (and old-style RPA bots) now type data into software for people: invoices into accounting tools, forms into portals. They finish and report **"done ✅"**. But "the steps ran" is not the same as "the right data landed". A wrong digit, a silent error toast or a half-saved row can hide behind a green checkmark.

If you can query the database, check there. Often you **can't**: legacy desktop software, third-party portals, remote desktops. In those places the screen is the only witness.

## What Witness will do (planned)

1. Watch the **screen recording** of an agent entering invoices into a UI that has no API.
2. Extract the agent's **claims** ("invoice 1043, ₹48,250, GST 18%").
3. Find the relevant fields, rows and error messages on screen (**SAM 3.1**, by text prompt) and crop them.
4. Read the values from the pixels (**Muse Spark** vision) and compare them to the source invoice.
5. Issue a **receipt** per invoice: `VERIFIED` · `MISMATCH` · `UNVERIFIABLE`, with an annotated frame as evidence.

## What we will *not* claim

- Not "a better judge than WebJudge / Universal Verifier". Those exist. See [docs/02-honest-evaluation.md](docs/02-honest-evaluation.md).
- Not a replacement for database checks when you have backend access.
- Not tested on real bank or government portals. We use a mock app and synthetic data only.

## Meta stack we plan to use

Muse Spark 1.3 (vision + structured output) · SAM 3.1 (grounding on video frames) · Meta Model API (OpenAI-compatible) · optional: Muse Wonder / Muse Code for the stretch agent. Details and prices: [docs/04-meta-stack.md](docs/04-meta-stack.md).

## Repo map

| Path | What is in it |
|---|---|
| [docs/](docs/) | Idea, honest evaluation, architecture, Meta stack, benchmark plan, build plan, presentation plan |
| [research/](research/) | Competitor matrix, papers, references, and the research playbook |
| [hackathon/](hackathon/) | Event facts, perks, rules to re-check, kickoff checklist |
| [data/](data/) | Synthetic-data spec and failure-injection catalog |
| [application/](application/) | Application-answer drafts and evidence of skill |
| [assets/](assets/) | Future screenshots, GIFs, diagrams |
| [DECISIONS.md](DECISIONS.md) | Decision log (what we chose and why) |
| [NEXT_ACTIONS.md](NEXT_ACTIONS.md) | The live to-do list. **Start here.** |

## Author

Yatharth Chopra · Gurugram, India · [GitHub](https://github.com/yatharthchopra2424)

## Licence

Undecided. Choose after the official rules are published on Oct 26.
