# Comparison Framework

Loaded when you are comparing multiple candidate verticals side-by-side against a shared set of criteria. The output is a file at `comparisons/<name>.md`, built from `templates/comparison.template.md`.

The first comparison in a project is typically `comparisons/initial-comparison.md`. Later re-scorings (e.g., after new research or new customer evidence) get dated names like `comparisons/post-research-2026-04-28.md`.

## Criteria

Use the same eight Aulet-derived dimensions from vertical analysis, collapsed into scorable criteria:

| # | Criterion | Scale |
|---|---|---|
| 1 | Market size (is the opportunity big enough to matter to the founder's goals?) | 1–5 |
| 2 | Accessibility (can the founder realistically reach customers?) | 1–5 |
| 3 | Urgency (are customers actively searching or close to it?) | 1–5 |
| 4 | Ability to pay (budget, approval path) | 1–5 |
| 5 | Founder fit (unusual advantages vs. generic entrant) | 1–5 |
| 6 | Competitive density (room to enter and win) | 1–5, higher = more room |
| 7 | Sales motion (easier motion = higher score) | 1–5 |
| 8 | Time to revenue (shorter = higher score, against runway) | 1–5 |

Scores come from the individual vertical analyses. If a vertical's analysis is incomplete (`RESEARCH-PENDING` dimensions), the comparison is **provisional** — label it as such at the top of the file and do not present it as final.

## Weighting

### Default: equal weights

Start with equal weights across all eight criteria. This is the floor.

### Ask the founder to weight

Before producing the final score line, ask the founder:

*"Default is equal weight across all eight criteria. Given your situation (runway, goals, risk tolerance), do you want to override? Common overrides: boosting Time-to-Revenue if runway is short, boosting Founder Fit if you have unusual advantages in one candidate, boosting Market Size if your goal is a large outcome."*

Accept their overrides or their choice to stick with defaults. Record the weights used in the comparison file.

### Math

**Weighted total formula:**

```
weighted_total(candidate) = Σ(weight_i × score_i) / Σ(weight_i)
```

Normalize by the sum of weights so the total is on the same 1–5 scale regardless of how the founder weights the criteria. Do not present unnormalized sums — they become arbitrarily large when the founder uses heavier weights and mislead comparison against absolute thresholds.

**Worked example (equal weights, three candidates, eight criteria):**

```
scores:
  A = [4, 3, 4, 4, 5, 3, 3, 2]   (market, access, urgency, pay, fit, comp, sales, time)
  B = [5, 2, 3, 4, 2, 4, 3, 3]
  C = [3, 4, 4, 3, 4, 3, 4, 4]
weights = [1, 1, 1, 1, 1, 1, 1, 1]   (Σ = 8)

weighted_total(A) = (4+3+4+4+5+3+3+2) / 8 = 28 / 8 = 3.50
weighted_total(B) = (5+2+3+4+2+4+3+3) / 8 = 26 / 8 = 3.25
weighted_total(C) = (3+4+4+3+4+3+4+4) / 8 = 29 / 8 = 3.63

rank: C (3.63), A (3.50), B (3.25)
```

Show the arithmetic in the file. A total without its components is not auditable.

### Flip-sensitivity check

This is the key capability beyond a static scorecard. After scoring, recompute under **three canonical alternative weightings** so the check is reproducible and comparable across projects:

1. Compute the ranking under the founder's chosen weights.
2. Re-compute under each of the three alternatives below:
   - **Heavy market size:** `market_size = 3`, all others = `1`.
   - **Heavy founder fit:** `founder_fit = 3`, all others = `1`.
   - **Heavy accessibility + time-to-revenue (runway-constrained):** `accessibility = 2`, `time_to_revenue = 2`, all others = `1`.
3. **If the #1 rank flips between weightings**, surface this explicitly: *"Under your current weights, X wins. Under the heavy-market weighting, Y wins. Under the heavy-fit weighting, Z wins. The recommendation is not robust to weighting assumptions — we should look more carefully at what the founder actually values."*
4. If the #1 rank is stable across weightings, say so explicitly too — that's a strong signal.

If the founder's own weights closely resemble one of the three canonical alternatives (e.g., they weighted founder_fit heavily), it's still useful to run all three — the point is to probe the ranking's robustness, not to find a novel weighting.

## Structure of the comparison file

See `templates/comparison.template.md`. Sections in order:

1. **Header** — comparison name, date, mode, status (provisional or final), weights used.
2. **Candidates** — one-line description per candidate, linking to its vertical file.
3. **Scoring matrix** — the 8×N table with scores.
4. **Weighted totals** — total per candidate under chosen weights.
5. **Flip-sensitivity** — results under alternative weightings, with a one-line interpretation.
6. **Narrative read** — 3–6 sentences summarizing what the numbers are saying and what they aren't. Identify the leader, the close-behind, and the definitely-out. Name the founder-context factors driving the ranking.
7. **Open questions before recommendation** — what needs to be resolved before converging on a recommendation.
8. **Red-Team Pass** — appended after the automatic red-team runs at the end of comparison (see `reference/red-teaming.md`).

## Comparison is a living artifact

The comparison file is updated, not replaced, when:

- New research arrives that changes scores on one or more dimensions. Record the old score and the new score with a note: `Urgency: 3 → 4 (post-research 2026-04-28: evidence of active procurement activity)`.
- The founder corrects their own weights.
- A new candidate is added or a candidate is dropped. (Adding late-stage is unusual and warrants discussion first.)

Significant updates trigger a re-read of the flip-sensitivity and the narrative read. They do **not** trigger an automatic red-team — that already happened at the first complete pass. Additional red-teams are on demand.

## When comparison is "done"

The comparison is sufficient to move to recommendation when:

- Every candidate has complete (non-`RESEARCH-PENDING`) scores on all 8 criteria.
- The founder has signed off on the weights.
- The flip-sensitivity has been run and the result interpreted.
- The automatic red-team pass has been appended.

At that point, move to `reference/beachhead-recommendation.md`.

## What this phase does NOT do

- It does not produce the recommendation itself. The comparison is an input to the recommendation; the recommendation artifact lives in `recommendations/`.
- It does not collapse scores into a single "winner" without the narrative and flip-sensitivity. A number-only output is a disservice — founders optimize for what they measure, and a false precision in the total is worse than an honest qualitative read.
- It does not hide close calls. If two candidates are within 5% of each other, say so and explain what would tip the call.
