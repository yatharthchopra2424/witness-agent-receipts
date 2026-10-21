# 05 · Benchmark plan

The benchmark is what turns "cool demo" into "technical ambition". Define it before building.

## Question
When an agent enters invoices into a UI, how many of its **false claims of success** does each checker catch?

## Checkers compared
| ID | Checker | Sees | Role |
|---|---|---|---|
| A | Text-log judge | Agent's own log and final message only | Baseline: "trust the agent's story" |
| B | Whole-frame vision judge | Full screenshots, no cropping | Baseline: common approach |
| C | **Witness** | SAM-cropped regions + claim-level checks + deterministic compare | Ours |

## Test set
- 30 runs × 10 invoices each = 300 invoice entries.
- About half of runs contain 1–3 injected failures; the rest are clean.
- Failure types are listed in `data/failure-catalog.csv`.
- Ground truth: the mock app's database (we control it), so labels are exact.
- Split: 10 runs for tuning prompts, 20 held-out for the reported numbers. **Never tune on the held-out set.**

## Metrics (report all, lead with the first)
1. **Missed-failure rate** = failures marked VERIFIED ÷ all injected failures. *The dangerous error.*
2. **False-alarm rate** = clean entries marked MISMATCH ÷ clean entries.
3. **UNVERIFIABLE rate**: how often it abstains. Abstaining is fine if rare.
4. Cost and time per run.
5. Ablation: C with SAM crops vs C with whole frames. Tells us if SAM earns its place.

## Reporting rules
- Show counts, not only percentages (e.g. "caught 41 of 45").
- State the test-set size and that failures were injected by us.
- If C does not beat B, say so and explain. Do not hide it.
- Publish the prompts and the data spec.

## Stretch: external check
Score task-level verdicts on **CUAVerifierBench** (`microsoft/CUAVerifierBench` on Hugging Face; 106 human-labelled web trajectories in the `fara7b_om2w_browserbase` split). Report agreement (accuracy, Cohen's κ) beside the published Universal Verifier numbers.
Before doing this: confirm the dataset licence, and that it fits our inputs (screenshots + log). It is web tasks, not invoices, so describe it as a sanity check only.

## Threats to validity (write these in the README)
- Failures are synthetic and may be easier than real ones.
- The mock app is clean; real apps have clutter.
- Same model family reads and writes; mitigated by deterministic compare.
- Small test set; no confidence intervals beyond simple counts.
