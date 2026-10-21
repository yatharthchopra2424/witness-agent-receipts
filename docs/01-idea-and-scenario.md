# 01 · Idea and scenario

## One-line pitch
Witness issues a **receipt** for every task an AI agent does on a screen: what it claimed vs. what the screen showed.

## Who it is for
A small accounting or back-office team (the typical Indian MSME case) that lets an automation or AI agent type invoices into software that has **no API** (older desktop accounting tools, third-party portals, remote desktops). They need proof of what was actually entered, without re-checking every row by hand.

## The problem
"Run succeeded" only proves the steps executed. It does not prove the right data landed. Public sources describing this gap (blogs and anecdotes, **not** measured studies):
- Activepieces: a workflow can run successfully and still be wrong.
- A practitioner's bank-download bot broke silently after a login change.
- A dev.to essay: "Your automation's green checkmark is lying to you."
Links are in `research/references.md`. We do **not** have hard numbers on how often this happens; never quote any.

## When Witness is the right tool, and when it is not
| Situation | Best check |
|---|---|
| You can query the database or API | Check the backend (more reliable). Witness is optional extra evidence. |
| No backend access (legacy UI, third-party portal, remote desktop) | **Witness** |
| You need evidence the agent cannot edit | **Witness** (independent recording, hash-chained) |

Say this plainly in the pitch. It makes the project more credible, not less.

## The demo story (what a judge sees)
1. A scripted agent "posts" 10 invoices to a mock ledger app. Its final message: *"All 10 invoices posted ✅"*.
2. Witness replays the recording. For invoice **#1043** the agent claimed ₹48,250 but the screen shows ₹48,520. Witness circles the field.
3. For invoice **#1047** the agent claimed success but a silent error toast appeared and the row never saved.
4. A chart shows how many false successes three checkers missed: text-log judge, whole-frame vision judge, Witness.

## Receipt format (design target)
Per invoice:
- Claim (field → value) · Evidence frame + timestamp · Region crop · Value read from pixels · Source value · Verdict · Confidence note.
Per run: summary table, counts of each verdict, and a hash chain over all evidence files so tampering is detectable.

## Scope: in / out
**In:** mock ledger web app; scripted agent with failure injection; claim extraction; SAM-based region crops; value reading; receipt report; benchmark of 3 checkers.
**Stretch (only if time):** a real Muse-driven computer-use agent; CI gate that fails on `MISMATCH`; score on the public CUAVerifierBench.
**Out:** real bank or government portals; real personal data; mobile apps; training or fine-tuning; a general-purpose judge.

## Naming and tagline options
Witness · "Don't trust the agent's word. Check the screen." · Alternatives to consider: Receipt, Proof of Work, Ledger Eye.
