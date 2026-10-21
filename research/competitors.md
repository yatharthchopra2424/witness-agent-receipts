# Competitor and prior-art matrix

Seeded 2026-10-21. [V] = verified on the primary page; [U] = unverified. Fill the empty cells using `PLAYBOOK.md`.

## Closest work (research)
| Name | Link | Input | Output granularity | Evidence artifact | Needs backend? | Open source | Key claim (authors') | Tag |
|---|---|---|---|---|---|---|---|---|
| Universal Verifier / CUAVerifierBench | github.com/microsoft/fara · huggingface.co/datasets/microsoft/CUAVerifierBench | Screenshots + log | Task-level with rubric + process/outcome scores | Rubric scores | No | Yes, MIT [V] | Near-zero false positives; baselines ≥22% (WebJudge), ≥45% (WebVoyager) | [V] repo, [U] paper details |
| WebJudge / Online-Mind2Web | github.com/OSU-NLP-Group/Online-Mind2Web | Key screenshots | Task-level | None | No | Yes | ~85% agreement with humans | [V] README, [U] paper |
| AgentRewardBench | agent-reward-bench.github.io | Trajectories | Benchmark of judges | n/a | No | Yes | No judge wins everywhere | [U] abstract |
| "Are We Done Yet?" | arxiv.org/abs/2511.20067 | Screenshots | Task-level | None | No | ? | up to 73% on 42 macOS apps | [U] abstract |
| web-eval-agent (refreshdotdev) | github.com/refreshdotdev/web-eval-agent | Live web app | Test report | Logs/screens | No | Yes | **Sunset** | [V] |

## Adjacent tools (not visual verification, to confirm)
| Name | What it is | Does it verify UI outcomes visually? | Tag |
|---|---|---|---|
| Promptfoo | LLM eval and red-teaming, CI | ? | [U] |
| DeepEval | pytest-style LLM evals | ? | [U] |
| Inspect (UK AISI) | Evaluation framework | ? | [U] |
| Braintrust, Langfuse, Phoenix, TruLens | Observability / eval platforms | ? | [U] |
| browser-use | Browser agent library (the *agent*, not the verifier) | ? | [V] it's an agent |

## RPA / automation vendors (to check)
UiPath, Automation Anywhere, Microsoft Power Automate, Pega. Questions: do they offer screenshot-based outcome verification or only step logs? (Pega docs describe coarse statuses like "Completed with errors" [U].) Fill in.

## Questions to answer in writing
1. What does Witness do that none of the above do? (draft: per-claim, pixel-grounded, tamper-evident receipts for UI-without-API entry)
2. Which one would a judge name first as "already exists"? Plan a one-line answer.
3. Can any of them be used *inside* Witness (e.g., borrow their rubric idea with credit)?

## Scores (see PLAYBOOK for rubric, 0–10)
| Name | Score | Notes |
|---|---|---|
| Universal Verifier | | |
| WebJudge | | |
