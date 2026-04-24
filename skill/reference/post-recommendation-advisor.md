<!-- v0.3.0: added per retrospective 2026-04-22 (rec 8) — patterns for post-Complete Advisor work so the skill does not drift into generic chat. -->

# Post-Recommendation Advisor

Loaded when `MEMORY.md` shows `Current phase: Complete` and the founder brings an execution-flavored question. The founder has both artifacts (beachhead recommendation + wedge-product concept); they are now moving into the work of actually selling, and they will bring back pricing questions, pitch questions, channel questions, first-call reports, and customer-asked-for-X scope questions.

These are legitimate uses of the skill. They need structure — otherwise Advisor mode drifts into generic LLM chat and loses its founder-context-aware edge. This file names the patterns.

## Operating posture in `Complete` phase

- `MEMORY.md` remains the anchor. Load it before any non-trivial response.
- Continue to hold the recommendation and wedge concept as **load-bearing constraints** — the founder chose them; your job is to help them execute, not to re-open them without evidence.
- Short advice is often the right response shape. Not every question needs an artifact. Over-writing files in `Complete` phase is noise.
- Red-team discipline remains active. If a question is an irreversible commitment wearing a different hat, flag it.

## Common patterns

Each pattern names: (a) the typical question shape, (b) the response shape, (c) which file (if any) to update, (d) whether a red-team fires.

### Pattern A — Outreach / first-contact help

**Question shape:** *"Help me write the outreach email to [warm contact]."* / *"What should I say in the first call with [prospect]?"*

**Response shape:** Short. A paragraph or two of advice, optionally a draft email. Grounded in the founder's `MEMORY.md` network entry and the wedge-product concept (what you're actually pitching).

**File update:** None by default. If the founder wants to save the draft, suggest `outreach/<contact-slug>-<date>.md` — but do not create it proactively.

**Red-team:** None. This is craft work, not commitment work.

### Pattern B — Post-call debrief

**Question shape:** *"I had a first call with [prospect] — help me red-team how it went."* / *"Here's what they said. What do I do with it?"*

**Response shape:** On-demand red-team targeting the call notes. Ask the founder to summarize the call (3–5 bullets: what they said they need, what they objected to, what they didn't ask). Then run a red-team pass against the wedge concept — does what you heard confirm or challenge the wedge?

**File update:** Save the call summary to `conversations/<contact-slug>-<date>.md`. If the red-team recommends revising the wedge, open a decision-log entry.

**Red-team:** Yes. This is one of the highest-value red-team moments — primary evidence meeting the wedge hypothesis.

### Pattern C — Customer-asked-for-X scope question

**Question shape:** *"A customer asked for X feature — does that break the wedge discipline or is it a valid expansion?"* / *"Prospect said they'd pay if we also did Y — should we say yes?"*

**Response shape:** Scope-fence check against `recommendations/wedge-product-concept.md` § "What it deliberately does not do." If X is explicitly out of scope, name it. Then ask: is the wedge wrong, or is the customer wrong for the wedge?

**File update:** None unless the answer changes the wedge. If it does: open a decision-log entry, revise the wedge-product-concept file in place (preserving the original in a dated sub-section), and re-run the wedge red-team.

**Red-team:** Yes if the founder is leaning toward saying yes. Scope creep pre-launch is the single most common wedge-failure mode.

### Pattern D — Pricing / packaging adjustment

**Question shape:** *"The first three prospects all pushed back on $15k. Should I drop to $8k?"* / *"Should I add a cheaper tier for budget buyers?"*

**Response shape:** Anchor against the wedge's price range hypothesis and the buyer-alternative-cost reasoning. Distinguish signal (3 prospects from the same ICP all pushing back → real) from noise (1 out-of-ICP prospect pushing back → not real).

**File update:** If a price adjustment is warranted, update the wedge-product-concept's "Price range hypothesis" section in place with a dated note. Do not rewrite silently.

**Red-team:** Optional. Fire if the founder is dropping price to close an out-of-ICP prospect — that's a beachhead drift signal.

### Pattern E — Channel / tactic question

**Question shape:** *"My primary channel isn't working — should I switch to cold outbound?"* / *"Should I post on LinkedIn about this?"*

**Response shape:** Short advice grounded in the founder's network and distribution entries. If they're proposing a channel that contradicts their stated constraints (e.g., cold outbound when they said they refuse to cold-call), name it.

**File update:** None by default.

**Red-team:** None unless the tactic change would drain runway significantly.

### Pattern F — Reconsidering the beachhead

**Question shape:** *"I'm not sure this beachhead is right anymore — [reason]."*

**Response shape:** Serious. Load `recommendations/beachhead-recommendation.md` § "What would reverse this recommendation." Check whether the founder's new evidence matches a stated reversal condition. If yes, this may be a return to Comparison phase. If no, red-team the doubt itself.

**File update:** Potentially material. If the founder is returning to Comparison, transition `Current phase` back with a decision-log entry explaining why.

**Red-team:** Yes, always. Beachhead abandonment on thin evidence is itself a failure mode.

## The artifact index

On transition to `Complete`, write `README-artifacts.md` at the project root. This is the founder's map of what they have.

Format:

```markdown
# Project Artifacts — <project-name>

Generated on transition to Complete phase, <YYYY-MM-DD>. Update when new material artifacts are added.

## Intake
- `intake/founder-profile.md` — <one-line summary>
- `intake/constraints-and-goals.md` — <one-line summary, including latest-update date>

## Verticals
- `verticals/<slug>.md` — <one-line summary of analysis>
- (one line per vertical file)

## Comparison
- `comparisons/initial-comparison.md` — <one-line summary + selected-winner>
- (any later re-scorings)

## Recommendation
- `recommendations/beachhead-recommendation.md` — <one-line description of the beachhead>
- `recommendations/wedge-product-concept.md` — <one-line description of the wedge>

## Decision and red-team logs
- `decisions/decision-log.md` — <N entries>
- `decisions/red-team-log.md` — <N red-team passes>

## Research
- `research/results/` — <count of founder-dropped reports>
- `research/results/perplexity-*.md` — <count of MCP-persisted calls>
- `research/cache/` — <count of native-search caches>
```

Each line is the artifact's path plus a one-line human summary — not a verbatim quote from the file. The goal is scannability: the founder should be able to look at this file and remember what each artifact is for without opening it.

Update this index when:
- A new material artifact is added (new vertical, new comparison, new research file).
- An existing artifact is materially revised (wedge adjusted, beachhead re-opened).

Do **not** update for every minor edit (typo fixes, session-log appends).

## What this phase does NOT do

- It does not produce pitch decks, business plans, or fundraising collateral — still anti-scope.
- It does not produce a Dunford-style positioning doc — still v2.
- It does not re-open the beachhead or wedge without evidence. The founder can always force a return to Comparison, but the skill does not initiate it unprompted.
- It does not generate a list of "next 10 things to do." The founder owns sequencing.

## v2 — Field-Signal Reconciliation (deferred)

Post-Complete field-signal handling (discovery-call reports, lost deals, pricing responses, competitive signals, macro signals touching named reversal conditions) is currently handled ad-hoc via the Common Patterns above plus the append-only discipline on the recommendation and wedge files (see `reference/beachhead-recommendation.md` § "Append-only discipline") and the four signal-driven principles (see `reference/red-teaming.md` § "Principles for signal-driven passes").

A proposed 8th phase — **Field-Signal Reconciliation** — with a five-file sweep, red-team re-trigger rules, and a dedicated call-prep template is drafted in the Shelf doc `ventures/voice-ai-ventures/entrepreneurial-strategist-skill-field-signal-updates.md`. It is out of MVP scope per `docs/mvp-spec.md` §2 (ongoing strategic review → v2, Pillar 6.10). Revisit when v2 begins.
