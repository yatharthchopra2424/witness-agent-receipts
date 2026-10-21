# Research playbook: how to study competitors and keep improving

Time-box: about 3 hours total. Output goes into `competitors.md`, `papers.md`, `references.md`, `open-questions.md`.

## Rules of evidence
- Tag every fact **[V]** verified from the primary page/paper, or **[U]** unverified (blog, vendor, abstract only).
- Record the date and URL for each fact.
- Quote numbers exactly and say whose numbers they are ("authors report…").
- Vendor blogs are marketing; use them for *ideas*, not for statistics.

## Step 1 · Find (45 min)
Search queries to run (web and Hugging Face / arXiv / GitHub):
- "computer use agent verifier", "web agent trajectory judge", "task completion verification screenshots"
- "RPA verification", "RPA silent failure", "UI automation audit trail"
- "agent audit trail screen recording", "invoice automation verification"
- "segment anything UI element", "SAM 3 screenshot", "GUI grounding benchmark"
GitHub CLI examples:
```
gh search repos "web agent evaluation" --sort stars --limit 20
gh api search/repositories -f q="computer use verifier" -f sort=stars
```
Also check: Hugging Face datasets/papers pages for CUAVerifierBench, AgentRewardBench; arXiv listing for citations of WebJudge.

## Step 2 · Read (60 min)
Read the **full text** of: Universal Verifier paper (arXiv 2604.06240), WebJudge paper (2504.01382), AgentRewardBench (2504.08942), "Are We Done Yet?" (2511.20067). For each, write 5 lines: method, data, result, limitation, what we can borrow.

## Step 3 · Compare (45 min)
Fill the feature matrix in `competitors.md`. Columns: input type, output granularity (task vs claim), evidence artifact, backend needed?, open source?, licence, last commit, stars, target user, price.
Then answer in writing: *"What does Witness do that none of them do?"* If the answer is weak, change the angle in `DECISIONS.md`.

## Step 4 · Real-world cases (30 min)
Collect 5–8 real incidents or practitioner write-ups of automation succeeding on paper but failing in fact. For each: source, what failed, how it was detected, cost if stated. Put them in `references.md` under "Real-world cases". Mark anecdotes as [U].

## Step 5 · Talk to people (optional, 30 min)
Ask 2–3 accountants or finance-ops friends: "If a bot types your invoices, how do you check it did it right?" Write their answers verbatim in `research/interviews.md` (create it; remove names).

## Step 6 · Keep it alive during the hackathon
- Revisit once on Oct 30 and once on Nov 2. Record new competitors or new Meta posts.
- Watch the hackathon Discord for projects with similar ideas; note them and differentiate.
- Re-run the `gh search` queries sorted by `updated`.

## Scoring a competitor (0–2 each, 10 max)
Same scenario? · Per-claim evidence? · Pixel-grounded? · Works without backend? · Open and runnable?
Higher score = closer competitor = must address in README "Related work".
