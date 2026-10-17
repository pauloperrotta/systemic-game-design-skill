# Evaluation

## Setup

- Three realistic prompts, one per mode (design, analysis, balance). Full text in [`evals/evals.json`](../evals/evals.json).
- Each prompt was run twice by independent sub-agents: once with the skill, once with no skill access. No clarifying questions were allowed; assumptions had to be declared.
- Each answer was graded against 7 to 8 objective assertions per prompt (23 total), for example "computes sustained DPS including reload for all 6 weapons" or "identifies gold glut as inflation or a faucet without a sink".

## Results

| Prompt | With skill | Without skill |
|---|---|---|
| 1. Survival game loops (design) | 8/8 | 6/8 |
| 2. Roguelite act-2 boredom (analysis) | 7/7 | 7/7 |
| 3. Weapon and XP balance (balance) | 8/8 | 8/8 |
| **Total** | **23/23** | **21/23** |

The without-skill design answer missed two assertions: loop diagrams without sources/sinks or R/B labels, and part attributes without ranges. The aggregate benchmark reports 92% without the skill because it averages the per-prompt rates (75%, 100%, 100%).

| Cost | With skill | Without skill |
|---|---|---|
| Average tokens per run | about 144k | about 80k |
| Average time per run | about 111 s | about 72 s |

## Reading the numbers

- A strong base model already passes most assertions, so they barely separate the two conditions.
- The visible difference is qualitative: loop maps with types and limits, named failure modes, quantified sinks, a metric per change, a repeatable valuation method. Compare the paired outputs yourself.
- Two runs read only part of the long reference files. Index-and-section reading guidance was added to `SKILL.md` afterwards; it was not re-tested.

## Triggering test

- 20 prompts (10 should trigger, 10 near-miss that should not) written in Spanish.
- Original description: first measurement, 22% recall on the training split and 8% on the held-out split, with 100% precision (no false activations).
- Rewritten description (tested once, all 20 prompts): 1 of 10 should-trigger prompts activated, 0 of 10 false activations. No improvement, so the original was kept.
- Conclusion: ask for the skill by name or add a project-instructions line.

## Known weaknesses of this evaluation

Three prompts, one run each, graded by the author's assertions. Small, early, and not blind. Please add harder prompts and other models.
