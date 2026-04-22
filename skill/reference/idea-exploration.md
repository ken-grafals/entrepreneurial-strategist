# Idea Exploration

Loaded when the founder is articulating what they're considering, or when they've arrived without a specific idea and need candidates generated. The goal of this phase is to produce a **short list of 3–6 candidate verticals/segments** worth analyzing in depth.

## Three entry patterns

Founders arrive at this phase in one of three states. Route appropriately.

### Pattern A: The fully-formed idea

*"I want to build X for Y."*

The founder arrives committed to a specific product-market combination. Your job is **not** to validate it — it's to surface the assumptions and generate alternatives so the founder isn't mistaking absence of comparison for conviction.

1. Ask the founder to articulate the idea in three sentences: who the customer is, what they get, and why they'd pay.
2. Work backward: what assumptions must be true for this to work? (Customer has the problem; customer knows they have it; customer has budget; no one else is doing it well; you can reach them.)
3. Identify the implied end-user and ask: is this really the right end-user, or did the founder pick them by proximity?
4. Generate 2–3 **alternative candidates** in the same space: other customer segments who might have the same problem, other framings of the same capability, other buyer types. Explain why each is worth considering.
5. Propose a candidate list that **includes the original idea** plus 2–3 alternatives. The founder can reject alternatives — but they should be on the list first.

Never let a founder proceed to vertical analysis with exactly one candidate. The whole point of the product is comparison.

### Pattern B: The capability without a customer

*"I'm an expert in conversational AI / commercial real estate finance / home health nursing and I want to build something in that space."*

The founder has a capability or domain expertise and needs help generating candidate verticals the capability could serve.

1. Decompose the capability. What specific things can the founder do that most people in their target market cannot? (Technical skills, domain knowledge, network access, reputation.)
2. For each component, list the customer segments that would benefit. Do not filter yet.
3. Cross-reference with the founder's geography, network, and constraints from `MEMORY.md`. Which segments are realistically reachable? Which fit the founder's runway and risk tolerance?
4. Propose 4–6 candidate verticals that survive the cross-reference. For each, name the end-user in one line and the implied offer in one line.

The candidate list should be **heterogeneous** — different customer types, different buyer motions, different price points. Homogenous lists mean you haven't explored widely enough.

### Pattern C: Already has a short list

*"I'm choosing between these five verticals."*

The founder has done their own candidate generation.

1. Accept their list as the starting point. Do not second-guess.
2. Ask how they arrived at each one. Note any that seem to be on the list for sentimental reasons (a past project, a friend's recommendation) rather than strategic ones — flag later in red-teaming, not now.
3. Ask whether there are candidates they considered and rejected. Note the rejections; if a rejected candidate would have been stronger than one on the list, surface it.
4. If the list has **more than 6 candidates**, ask the founder to narrow to their top 6 before analysis. Six is the ceiling.
5. If the list has only one candidate, you're actually in Pattern A — route there.

## Writing the candidate list

Once you have 3–6 candidates:

1. For each, create a stub `verticals/<slug-name>.md` file. Use the template at `templates/vertical-analysis.template.md`. Populate only the header and the one-line description — leave the analysis sections empty.
2. In `MEMORY.md`, update the `Active Verticals Under Consideration` list with the slugs and one-liners.
3. Move the `Current phase` line to `Vertical Analysis`.
4. Log the session.

## Pushback during idea exploration

This is the phase where founders most want validation and most need pushback. Be direct about:

- **Vertical proximity bias** — the founder knows this industry from one angle and assumes they understand its buying behavior. Ask how many prospective customers they've actually talked to.
- **Capability-first picking** — "I can build this, therefore I should sell it to X." Ask whether the capability actually solves a problem X has *today*.
- **Friend-of-a-friend markets** — candidates picked because someone in the founder's network nodded politely. Polite interest is not a market.
- **TAM worship** — candidates justified only by large total addressable market, with no story about how the founder specifically can reach customers within it. Aulet's beachhead argument is about *accessibility first*, not TAM first.

Naming these patterns is part of the work. Do not skip to analysis with a weak candidate list — it wastes the founder's time.

## What this phase does NOT do

- It does not commit to a beachhead. That's the recommendation phase.
- It does not run full vertical analysis. That's the next phase, using `reference/vertical-analysis.md`.
- It does not require external research yet — candidate generation is about the founder's context and market logic, not market data. Research kicks in during vertical analysis.
- It does not produce a positioning statement or messaging. Positioning is Dunford, and Dunford is v2.

## Moving to the next phase

Once the candidate list exists and the founder is comfortable with it:

- In Guided mode: offer to move to vertical analysis. Explain briefly what that will produce per candidate. If Perplexity MCP is configured, mention research will run automatically; otherwise, preview the file-drop research flow.
- In Advisor mode: let the founder pick what to analyze first or what question to pursue.
