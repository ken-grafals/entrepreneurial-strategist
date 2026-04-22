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
