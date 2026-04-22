# Vertical Analysis

Loaded when you are analyzing a single candidate vertical in depth. Each candidate gets its own file at `verticals/<slug-name>.md`, built from `templates/vertical-analysis.template.md`.

This is the Aulet analytical spine. You are answering, for one candidate: *is this a real market, is it reachable, does the founder fit, and what would a wedge look like?*

## Output dimensions

Every vertical analysis covers these eight dimensions, in order. They map to Aulet's beachhead-selection criteria with service-business adaptations.

1. **Market description** — who is the end-user, what is their job-to-be-done, and what triggers them to look for a solution? Specific: not "small businesses" but "independent agencies managing 20–100 home-care caregivers who are responsible for credential compliance."
2. **Market size** — best available TAM estimate with methodology. If research is not yet in, flag as `RESEARCH-PENDING` and note the specific question that will be researched.
3. **Accessibility** — how does the founder reach this customer? Channels they can realistically use (direct outbound, existing network, content, partnerships, paid). Flag if the only answer is "we'll figure out distribution later" — that is a fail signal.
4. **Urgency of problem** — on a 1–5 scale, how urgent is this to the customer? 5 = they are actively searching. 3 = they'd engage if pitched. 1 = "nice to have." Cite evidence.
5. **Ability to pay** — do they have budget, and what line item does this come out of? Who approves the spend?
6. **Founder fit** — given the intake profile, does the founder have unusual advantages here (domain expertise, network, credibility)? Or are they a generic entrant?
7. **Competitive density** — direct competitors, indirect alternatives (incl. spreadsheets, manual processes, "do nothing"). Is there room, and is the incumbent beatable for this specific segment?
8. **Sales motion difficulty and time to revenue** — product-led? Inbound? Outbound? 6-month enterprise cycle, or 2-week self-serve? Flag if the sales motion conflicts with the founder's runway.

## Process

### 1. Decide what research you need

Before populating the file, decide which of the eight dimensions require external research versus which can be answered from the founder's context.

- **Market size** almost always requires research.
- **Competitive density** usually requires research (at minimum to surface non-obvious alternatives).
- **Accessibility** can usually be reasoned from the founder's network and the segment's known buying patterns.
- **Urgency** benefits from research (news, complaints, regulatory changes) but is ultimately validated by customer conversations — which are out of MVP scope.
- **Ability to pay** can often be inferred from the segment's financial profile.
- **Founder fit** is an internal analysis.
- **Sales motion** is reasoned, not researched.

Flag dimensions that need research as `RESEARCH-PENDING` in the file, initiate research per `reference/research-integration.md`, and come back to fill them in.

### 2. Populate the file

Use `templates/vertical-analysis.template.md`. For each dimension:

- **State a claim** in one or two sentences.
- **Back it with evidence** — citation from research, a specific founder-context fact, or a named assumption. If it's an assumption, label it: `Assumption:`.
- **Score** on the 1–5 scale for scorable dimensions (urgency, ability to pay, founder fit, competitive density, sales-motion ease).

Keep prose tight. The file is a decision artifact, not an essay. If a section runs long, you are writing narrative instead of analysis.

### 3. Surface the open questions

Every vertical analysis ends with an **Open Questions** section listing what would need to be verified to move from "candidate" to "selected beachhead." These become research prompts or — once the founder reaches a primary-research phase (v2) — customer conversation targets.

## Multiple verticals

Analyze each candidate to the same depth before moving to comparison. Uneven analysis biases the comparison toward whichever candidate got more attention.

If a candidate becomes obviously unworkable partway through (e.g., research shows the market is a tenth of what the founder assumed, and runway cannot support the sales cycle), you may stop the analysis early. Record why in the vertical file and flag for the founder. The candidate stays in `MEMORY.md`'s list with a `DROPPED` marker so the reasoning is preserved.

## Research-pending state

If research is in flight, the vertical file can be "provisional." Mark unfilled dimensions with:

```
**Market size:** RESEARCH-PENDING — see research/prompts/market-size-<vertical>-YYYY-MM-DD.md
```

Do not hallucinate data to fill the gap. The founder needs to know what you know vs. what you are inferring.

## Pushback during analysis

If the founder insists on a dimension score that isn't supported by the evidence:

- State what you see: "Your urgency score of 5 implies they're actively searching — is that based on specific conversations you've had, or on your sense of the market?"
- Do not argue. Record both the founder's score and your assessment, with reasoning, in the file.
- Let the comparison phase surface the disagreement — it often self-resolves when the founder sees the side-by-side.

## Output to MEMORY.md

When a vertical analysis is complete:

- Update the `Active Verticals Under Consideration` one-liner in `MEMORY.md` if the analysis changed how the vertical is best described.
- If the vertical was dropped, move it to a `Dropped Verticals` subsection with the reason.
- Log to the session log: which file was updated, what state (complete vs. provisional).

## What this phase does NOT do

- It does not produce a recommendation. That comes after comparison and red-teaming.
- It does not produce positioning. Dunford is v2.
- It does not simulate customer conversations. Mom Test is v2.
- It does not assume one vertical is the winner. Treat each candidate independently on first pass.
