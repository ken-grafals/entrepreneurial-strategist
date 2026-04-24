<!-- v0.3.0: parallel cash-wedge SKU as first-class concept for runway-constrained founders per retrospective 2026-04-22 (rec 4). -->

# Beachhead Recommendation

Loaded when you are converging on a recommended beachhead and producing the final two artifacts of the MVP: `recommendations/beachhead-recommendation.md` and `recommendations/wedge-product-concept.md`.

Produce these **only after** the following prerequisites are met:

- All candidate verticals have complete (non-`RESEARCH-PENDING`) analyses.
- The comparison file is complete with weights signed off by the founder.
- The flip-sensitivity check has been run.
- An **automatic red-team pass** has been appended to the comparison file.

If any are missing, stop and complete them first.

---

## The beachhead recommendation file

Template: `templates/beachhead-recommendation.template.md`.

### Sections

1. **Header** — date, mode, project name, link to comparison file used.
2. **Recommendation** — the named beachhead. One sentence describing it in the specific form Aulet asks for: a named end-user and their defining characteristics. Not "small law firms" — "solo practitioners in U.S. estate-planning practices with 0–2 support staff and annual revenue between $200k and $800k."
3. **Why this beachhead** — 4–7 sentences grounded in the comparison and the founder's context. Name the two or three founder-context factors that drove the call. Reference the dimension scores, not the raw totals.
4. **Runner-up(s) and why they didn't win** — 2–3 sentences per runner-up. Be specific about what would have to change for them to win. This is useful both as honesty and as an insurance policy: if conditions change (new research, new founder context), the runner-up may need to be re-raised.
5. **Founder-context factors that drove the call** — bulleted, each referencing the founder's intake. This is what distinguishes the recommendation from a generic analysis.
6. **Open questions requiring primary research** — what the founder needs to verify by talking to customers (out of MVP scope but named). Each open question should be actionable: "Confirm that credential-renewal cycles drive procurement timing" is actionable; "Confirm market attractiveness" is not.
7. **What would reverse this recommendation** — 2–4 specific, falsifiable conditions. If the founder discovers any of these in primary research, they should return and re-evaluate.
8. **Red-Team Pass** — appended after the final automatic red-team pass (see below).

### The final red-team pass

Before considering the recommendation "done":

1. Run an automatic red-team pass **on the recommendation itself**, not on the comparison (the comparison already got one).
2. Append the pass to this file.
3. If the pass returns "Revise" or "Reject," act on it — revise the recommendation or flag it as unready. Do not ship a recommendation with an unresolved red-team output saying "Revise."
4. If the pass returns "Proceed" or "Gather more evidence," the recommendation is ready; the evidence-gathering items feed into the Open Questions section.

### Append-only discipline (these two files are append-only once shipped)

Both `recommendations/beachhead-recommendation.md` and `recommendations/wedge-product-concept.md` follow the same discipline as `decisions/decision-log.md`: never rewrite the body once the file has shipped (red-team passed and handed off to the founder). Strategic evolution happens in dated addenda, not in silent body edits.

- **New field signal that touches the recommendation** — append a dated block under `## Post-ship addenda` at the bottom of `beachhead-recommendation.md`. Name the update type ("Channel update — 2026-MM-DD", "Pain update", "Competitive update", "Reversal-condition update"). Do **not** edit the original Recommendation / Why / Runners-up / Reversal sections.
- **New field signal that changes the wedge** — same pattern at the bottom of `wedge-product-concept.md`. If the wedge's shape changes outright (not just a parameter), write a new dated version block that supersedes but does not overwrite the primary or cash-wedge sections above it.
- **Every addendum must cite its originating signal** — the call notes path, research file, email thread, or Shelf report that triggered the update. Addenda without provenance are unauditable six months later when memory has faded.
- **Why append-only.** Red-teaming a decision months later requires seeing what the strategist and founder believed at the time it was made. An edit-in-place strategy loses that signal. Append-only is how the artifact both stays current *and* stays honest about its evolution.

Trivial fixes (typos, broken links, formatting) can be edited in place without ceremony. The append-only rule protects claims and reasoning, not punctuation.

---

## The wedge-product concept file

Template: `templates/wedge-product-concept.template.md`.

The wedge product is the **first thing the founder would actually build or sell** into the chosen beachhead. It is not the full product vision — it is the minimum viable wedge that gets the founder to a first paying customer in the chosen segment.

### Sections

1. **Header** — date, project, link to the beachhead recommendation.
2. **The wedge in one sentence** — "A [form factor] that [does X] for [the named end-user] so they can [achieve Y]." No more than 30 words.
3. **Form factor** — is this a software product, a productized service, a pure service, or a hybrid? Name it explicitly. This is the MVP form factor, not the eventual product.
4. **What it does** — 3–7 bullets. What the customer gets on day one. Not a feature list — a capability list from the customer's perspective.
5. **What it deliberately does not do** — 2–4 bullets. The point is to name what's out of scope so the founder doesn't drift.
6. **Why this wedge for this beachhead** — 2–4 sentences. Tie the wedge to the end-user's job-to-be-done from the vertical analysis.
7. **How the founder would actually sell it** — outbound, inbound, content, partnerships, self-serve. One primary channel, one backup. Cite the founder's network and constraints.
8. **Price range hypothesis** — one or two price points or ranges, explicitly marked as hypothesis, with the reasoning (what comparable offerings charge, what the buyer's alternative costs).
9. **First 10 customer acquisition hypothesis** — a *one-paragraph* sketch, not a plan. Who the first 10 could realistically come from. Detailed GTM is v2 work.
10. **Red-Team Pass** — appended after the automatic red-team pass on the wedge concept.

### The red-team pass on the wedge

Separate from the red-team pass on the recommendation. This pass asks:

- Is the wedge *actually* minimum? Or is the founder smuggling a larger product in?
- Does the wedge solve a *sharp, urgent* problem for the named end-user, or is it "nice to have"?
- Is the sales motion consistent with the founder's runway and skills?
- Does the price range match the buyer's budget authority?

Append to the file, log to `decisions/red-team-log.md`.

### Parallel cash-wedge SKUs

Runway-constrained founders may need **two SKUs from day one**, not one: a **primary wedge** that produces the high-quality beachhead pull-through (slow but strategic) **and** a **cash wedge** that produces bridge revenue from the founder's warm network (fast but tactical). Most real beachheads have an asymmetry between "best long-term ICP" and "fastest-to-cash ICP"; forcing the founder to pick one loses runway or loses strategy.

**Trigger.** Add a parallel cash-wedge SKU to the recommendation when **either** condition holds:

- **Runway < 6 months** as stated in `intake/constraints-and-goals.md`.
- **Founder signals** they need bridge revenue — e.g., they've said "I can't wait 9 months for enterprise procurement to close," or they've named a warm contact who would buy a scoped service "tomorrow."

Do not add a cash wedge by default; it is asymmetry-driven, not runway-safe-by-default.

**Structure.** When both SKUs are warranted, the wedge-product-concept file carries **two wedge blocks**, not one:

- **Primary wedge** — the minimum viable product/service that converts the named beachhead end-user. Slow sales motion is acceptable if the price/LTV math works.
- **Cash wedge (parallel)** — a smaller, faster-sold SKU drawn from the founder's warm network. Typically: a productized version of expertise the founder already has, sold to a known buyer within 30 days. Named explicitly as a cash vehicle, not as beachhead-relevant.

Each block carries the same subsections (form factor, capabilities, scope fences, channels, price hypothesis, first-10 acquisition hypothesis). The header notes whether the file is `primary-only` or `primary + cash`.

**Sequencing.** Name which SKU the founder starts in week one. Typically: cash wedge first (revenue immediately, network-sold, low-risk), primary wedge in parallel (prospecting begins week one but doesn't close for 60–180 days). The cash wedge must not consume more than ~50% of the founder's execution time, or it becomes the venture by accident.

**Red-team adjustment.** The wedge red-team runs on **both** blocks separately. Cash-wedge-specific red-team questions:

- Is the cash wedge actually network-sold, or does it require cold outbound the founder claims to refuse?
- Does the cash wedge drift toward the beachhead's ICP (warning sign of scope collapse) or stay genuinely orthogonal (intended)?
- Will delivering the cash wedge eat enough time that the primary wedge starves?

If the cash wedge fails red-team, ship primary-only and flag the runway constraint as an open primary-research question for the founder.

---

## Updating MEMORY.md

When both artifacts exist and have passed their red-team passes:

- Phase transitions: `Recommendation` (during the beachhead file) → `Wedge` (during the wedge-concept file) → `Complete` (once both have shipped). `Complete` covers continued Advisor-mode work; there is no separate `Post-Recommendation` phase.
- Add a prominent line at the top of the Active Project State section:

  ```
  **Selected beachhead:** <one-sentence description>
  **Wedge product:** <one-sentence description>
  **Artifacts:** recommendations/beachhead-recommendation.md, recommendations/wedge-product-concept.md
  ```

- Update the decision log at `decisions/decision-log.md` with an entry summarizing the recommendation, the key factors, and the kill conditions.
- Populate the `### Active Hypotheses` block in `MEMORY.md` with the beachhead's reversal conditions (as hypotheses) plus the wedge's load-bearing price, channel, and competitive-moat assumptions. Each starts at confidence `untested`. Mirror the full-form versions (with reasoning and expected evidence) into `intake/active-hypotheses.md`.

## Handoff to the founder

At the end of this phase, tell the founder plainly:

1. The beachhead recommendation and wedge concept are in their respective files.
2. What the red-team pass found and what they should act on.
3. What the Open Questions are and why they require primary customer research — which is out of MVP scope.
4. That positioning (Dunford) is the natural next step, and is planned for v2.

Do **not** invent a v2 roadmap for them. Do not promise dates. Just name what exists and what doesn't.

## What this phase does NOT do

- It does not produce a business plan, pitch deck, financial model, or fundraising narrative.
- It does not design a full go-to-market. Channel strategy, first-ten-customer plans, and pricing models beyond a range hypothesis are v2.
- It does not commit the founder to the recommendation. The founder's ownership is explicit — the recommendation is a recommendation, not a decision.
- It does not stop the founder from continuing in Advisor mode afterward with specific questions. That is a valid use of the tool.
