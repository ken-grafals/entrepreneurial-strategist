<!-- Governed by skill/reference/comparison-framework.md. Scores come from the individual vertical analyses. -->

# Comparison: {{COMPARISON_NAME}}

- **Date:** {{DATE}}
- **Mode:** {{MODE}}
- **Status:** {{STATUS}} <!-- Provisional / Final -->
- **Comparison based on:** {{BASIS}} <!-- e.g., initial analyses / post-research re-scoring on YYYY-MM-DD -->

## Candidates

- **{{SLUG_1}}** — {{ONE_LINER_1}} ([analysis](../verticals/{{SLUG_1}}.md))
- **{{SLUG_2}}** — {{ONE_LINER_2}} ([analysis](../verticals/{{SLUG_2}}.md))
- **{{SLUG_3}}** — {{ONE_LINER_3}} ([analysis](../verticals/{{SLUG_3}}.md))
<!-- Up to 4 active + 2 backlog. Mark backlog candidates with "(backlog)" in the one-liner. -->

## Weights used

| Criterion | Weight |
|---|---|
| Market size | {{W_MARKET}} |
| Accessibility | {{W_ACCESS}} |
| Urgency | {{W_URGENCY}} |
| Ability to pay | {{W_PAY}} |
| Founder fit | {{W_FIT}} |
| Competitive density | {{W_COMPETITION}} |
| Sales motion | {{W_SALES}} |
| Time to revenue | {{W_TIME}} |

**Weight rationale:** {{WEIGHT_RATIONALE}}

## Scoring matrix

| Criterion | {{SLUG_1}} | {{SLUG_2}} | {{SLUG_3}} |
|---|---|---|---|
| Market size | {{MS_1}} | {{MS_2}} | {{MS_3}} |
| Accessibility | {{A_1}} | {{A_2}} | {{A_3}} |
| Urgency | {{U_1}} | {{U_2}} | {{U_3}} |
| Ability to pay | {{P_1}} | {{P_2}} | {{P_3}} |
| Founder fit | {{F_1}} | {{F_2}} | {{F_3}} |
| Competitive density | {{C_1}} | {{C_2}} | {{C_3}} |
| Sales motion | {{SM_1}} | {{SM_2}} | {{SM_3}} |
| Time to revenue | {{TTR_1}} | {{TTR_2}} | {{TTR_3}} |

## Weighted totals (current weights)

| Candidate | Weighted total | Rank |
|---|---|---|
| {{SLUG_1}} | {{TOTAL_1}} | {{RANK_1}} |
| {{SLUG_2}} | {{TOTAL_2}} | {{RANK_2}} |
| {{SLUG_3}} | {{TOTAL_3}} | {{RANK_3}} |

## Flip-sensitivity check

Mandatory. Record rankings under all three alternative weightings even if no flip occurs — a "no flip" result is itself informative.

- **Heavy market size (market_size=3, others=1):** {{HEAVY_MARKET_RESULT}}
- **Heavy founder fit (founder_fit=3, others=1):** {{HEAVY_FIT_RESULT}}
- **Heavy accessibility + time-to-revenue (access=2, ttr=2, others=1):** {{HEAVY_ACCESS_RESULT}}

### Flip narrative

{{FLIP_NARRATIVE}}

<!-- One paragraph in plain language.
     If flipped: "Under your current weights, X wins. Under heavy-market, Y wins. Tiebreaker is which weighting reflects your real situation — is market size more load-bearing than founder fit for you right now? This is a strategy choice, not a scorecard result."
     If stable: "X wins across all three alternative weightings. The ranking is robust to reasonable weighting shifts — this is a strong signal, not a close call." -->

## Fusion hypotheses

<!-- Optional. Populate only if two or more candidates cluster within 0.2 weighted-total AND share a plausible combined ICP.
     A fusion must reduce to a single Aulet end-user or it is not a valid beachhead.
     If the cluster-within-0.2 + shared-ICP precondition does not hold, delete this entire section. -->

- **Fusion candidate:** {{FUSION_NAME}}
- **Parent candidates:** {{FUSION_PARENTS}}
- **Single end-user (required):** {{FUSION_END_USER}}
- **Fusion scores on 8 criteria:** {{FUSION_SCORES}}
- **Fusion weighted total:** {{FUSION_TOTAL}}
- **Flip-sensitivity on fusion:** {{FUSION_FLIP}}
- **Verdict:** {{FUSION_VERDICT}} <!-- outperforms parents / underperforms / invalid (does not reduce to single end-user) -->

## Narrative read

{{NARRATIVE}}

## Open questions before a recommendation

- {{OPEN_Q_1}}
- {{OPEN_Q_2}}

## Red-Team Pass

<!-- Appended by the automatic red-team pass per skill/reference/red-teaming.md. -->
