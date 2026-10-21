# Decision log

Format: date · decision · why · what would change it.

| Date | Decision | Why | Revisit if |
|---|---|---|---|
| 2026-10-21 | Track: **Indie developer** | Solo builder, 1–2 h/day. Judged on creativity, technical ambition, whether it works. | Never; the track is fixed per project. |
| 2026-10-21 | Project: **Witness**, a visual verifier for agent runs | Matches existing skills: agents, eval harnesses with CI gates, video detection/tracking. | The Meta API turns out to be unavailable and no fallback works. |
| 2026-10-21 | Scenario: **invoice entry into a UI with no API** | Narrow, real, explainable to non-experts. Avoids competing head-on with general web-agent judges. | A better narrow scenario appears during research. |
| 2026-10-21 | Claim: **per-claim, pixel-grounded receipts**, not "a better judge" | Generic judges exist (WebJudge, Universal Verifier, others). We cannot beat them in about 15 hours. | Our benchmark shows we do beat a strong baseline. |
| 2026-10-21 | Data: **synthetic only**, mock app we write ourselves | No privacy risk. Avoids touching real portals. | Never for real PII. |
| 2026-10-21 | Use **standard** (not Contributor) Meta models by default | Contributor mode lets Meta train on prompts and outputs. | Only synthetic data is sent and cost becomes a problem. |
| 2026-10-21 | Start the code **fresh on/after Oct 26** | Official rules are not published yet; avoid any prior-work dispute. | Rules explicitly allow earlier work. |
