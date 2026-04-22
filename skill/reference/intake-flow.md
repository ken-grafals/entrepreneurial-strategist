<!-- v0.3.0: intake reframed as producing a living constraints file; added constraint-eliciting prompts per retrospective 2026-04-22 (rec 5). -->

# Intake Flow

Loaded when you are conducting founder intake for the first time, or updating the founder profile during a later session. Intake is a **living document, not a phase you leave**. Every subsequent phase (Idea Exploration, Vertical Analysis, Comparison, Recommendation, Wedge) is expected to update — not just read — `intake/constraints-and-goals.md` when new founder constraints emerge.

Constraints commonly surface after formal intake is "done": a delivery-stack rule emerges during Idea Exploration when the founder rejects a candidate; a geography-is-a-bonus-not-a-wedge rule emerges during Comparison when scoring over-weights a soft advantage. These are founder constraints, not transient preferences — capture them.

## Purpose

The intake produces three things:

1. A deep, structured profile of the founder that informs every subsequent analysis — their skills, constraints, network, goals, risk tolerance.
2. Written artifacts at `intake/founder-profile.md` and `intake/constraints-and-goals.md` that the founder can read, correct, and return to.
3. A structured summary in `MEMORY.md`'s Founder Profile section.

For first-time founders, intake is also the first time they've been asked to articulate their situation in a structured way. The exercise itself has value. Do not rush it.

## Mode awareness

- In **Guided mode**, you lead the founder through the question areas in order, one at a time, with context and pushback where warranted.
- In **Advisor mode**, you gather what you need as it becomes relevant to the conversation, and backfill the intake files in the background.

## Question areas

Cover the following five areas. In Guided mode, move through them in this order. Do not ask every sub-question — pick what's pertinent, and let follow-ups emerge from what the founder says.

### 1. Identity and context
- What should I call you?
- Where are you based? (City and country; remote/hybrid/in-person preference.)
- Languages you work in professionally?
- Solo founder, or working with co-founders? If co-founders: how many, what are their backgrounds, and how is the team organized so far?

### 2. Background and expertise
- How many years in your current or most recent domain?
- What are your two or three areas of deepest expertise? (Be specific — not "software" but "real-time inference pipelines for video".)
- Notable past work, ventures, or roles that shape how people see you?
- Technical skills you'd be willing to build with yourself vs. hire for?
- What do you know unusually well that most people in your target space don't?

### 3. Constraints
- Financial runway: how many months can you go before you need revenue or funding?
- Time commitment: full-time, part-time, evenings-and-weekends?
- Geographic constraints: customers you must or cannot serve; travel limits; timezone realities.
- Other commitments: existing job, family responsibilities, non-compete or IP restrictions.
- **Delivery-stack exclusions:** are there platforms, stacks, or vendor dependencies you've decided you will **not** build on — even if the market demands it? Why? (This catches rules like "must run on own stack, not third-party enterprise platforms" that otherwise surface mid-comparison and invalidate candidates.)
- **Bonus-not-load-bearing advantages:** are there founder attributes (language fluency, geography, industry credential) that you consider *bonuses* rather than *load-bearing* for a wedge? Name them. (This catches over-weighting in scoring — e.g., Spanish-language capability as a credential, not a wedge.)

### 4. Goals and values
- What does success look like in 2 years? In 5?
- Revenue scale you're targeting (lifestyle / $1M ARR / $10M+ ARR / VC-scale)?
- Risk tolerance: are you willing to bet everything on one shot, or would you prefer a venture with a higher probability of a smaller outcome?
- Personal values that should shape the venture — e.g., industries you won't work in, customer types you refuse to build for, work-life boundaries.
- If you had to name the kind of company you absolutely do **not** want to run, what would it be?

### 5. Network and resources
- Who in your network would you be willing to call for an intro or an honest opinion about a vertical you're considering?
- Existing distribution channels or relationships (an audience, a newsletter, a customer base from a past product)?
- Other resources: capital you can invest yourself, intellectual property from past work, prior assets you can repurpose.
- Anyone who has already said they would buy from you if you built X?

## How to ask

- **One area at a time.** Do not dump the whole question list.
- **Use the founder's language.** If they said "healthcare," don't later call it "medical vertical" — match vocabulary.
- **Push back when the answer is too generic.** "I'm good at engineering" is not useful. "I built a team of 12 that shipped a real-time ML platform that processed 40M events/day" is.
- **Ask for specific examples** when you need to test whether a self-assessment is grounded in actual experience.
- **Do not lecture** on why each question matters. If the founder asks, explain briefly. Otherwise move.

## Writing the intake files

As answers come in, write them to the two intake files. Do not wait until the end.

- `intake/founder-profile.md` — identity, background, expertise, network. See `templates/founder-profile.template.md`.
- `intake/constraints-and-goals.md` — runway, time, geography, other commitments, goals, values, risk tolerance. See `templates/constraints-and-goals.template.md`.

Also update `MEMORY.md`'s Founder Profile section in parallel, keeping it short (bullet form, key facts only). Depth lives in the intake files.

## When intake is "done"

Intake is never finished, but for the purpose of moving to idea exploration, it is sufficient when:

- The founder's expertise is specific enough that you could explain it to a stranger in two sentences.
- Constraints (runway, time, geography) are numeric or explicit, not vague.
- The founder has named at least one personal value or non-negotiable that will shape vertical selection.
- You know whether they have existing distribution or not.

At that point, summarize what you've gathered back to the founder in 5–8 bullets and ask for confirmation or correction. Then — if in Guided mode — offer to move to idea exploration. If in Advisor mode, just note you're ready whenever they are.

## Updating intake later

When you learn new context in a later session:

- Update the relevant intake file in place. Do not lose prior content; if a detail is superseded, preserve the original in a `## Superseded notes` subsection at the bottom.
- Update the `MEMORY.md` Founder Profile if the change is significant enough to affect future analysis.
- Log the update in the session log.

## Constraints that emerge after intake

When a constraint emerges in a later phase (Idea Exploration, Vertical Analysis, Comparison, etc.), it is as load-bearing as an intake-elicited constraint — and is often more surprising, because it had to be triggered by a specific candidate or scoring decision. When this happens:

1. **Update `intake/constraints-and-goals.md`** with the new constraint, dated. Use the "Delivery-stack exclusions" or "Bonus-not-load-bearing segments" sub-section if it fits one; otherwise add a new bullet under Constraints with a dated note.
2. **Write a `decisions/decision-log.md` entry** immediately (not at phase end), explaining when and why the constraint emerged. Example: *"2026-04-22 — Own-stack constraint. Surfaced when Claude proposed a conversational-ai-platform-partner candidate; founder rejected on grounds that the venture must run on own stack. Reversal condition: the own-stack rule is relaxed if …"*
3. **Update `MEMORY.md`** Founder Profile § Constraints (or add a dedicated `§ Strategic constraints` block if multiple constraints accumulate), and write an auto-memory of type `feedback` with **Why:** and **How to apply:** lines per the user's private memory conventions.

Do not wait for the current phase to end to do any of the above. Constraints that live only in the transcript get lost when the session compacts.

## Red flags during intake

Note these silently and come back to them in red-teaming:

- A founder whose expertise doesn't match the vertical they're about to propose.
- Runway shorter than the realistic sales cycle of the business they want to build.
- Values that conflict with the business model they're gravitating toward (e.g., wants mission-driven, gravitating toward adtech).
- An "unusually good network" that turns out to be LinkedIn connections, not people who would actually take a call.

Don't call these out aggressively mid-intake. Capture them and raise them when the founder proposes something that triggers the mismatch.
