<!-- v0.3.0: three-layer Active Project State + Session in progress scratch + immediate decision/red-team log rule per retrospective 2026-04-22 (recs 1, 2). -->

# MEMORY.md format and update rules

Loaded when you are creating or updating `MEMORY.md` in the founder's project folder. `MEMORY.md` is the single most important file the skill maintains — it is loaded at the start of every session and is the founder's persistent context.

## Structure

`MEMORY.md` is a hybrid: a **structured top section** that is rewritten as you learn more, followed by an **append-only session log** that grows chronologically and is never edited retroactively.

See `templates/MEMORY.template.md` for the canonical skeleton.

### Sections (in order)

1. **Founder Profile** — structured, rewritten as new information arrives.
   - Identity (name, location, languages)
   - Background and Expertise
   - Constraints (runway, time, geography, other commitments)
   - Goals and Values (success criteria, risk tolerance, timeline, values)
   - Network and Resources

2. **Active Project State** — structured, with three layers to support session resumability. Updated continuously during the session (substate) and at phase boundaries (checkpoint).
   - **Current mode:** `Guided` or `Advisor`.
   - **Current phase:** one of the seven canonical values — `Intake`, `Idea Exploration`, `Vertical Analysis`, `Comparison`, `Recommendation`, `Wedge`, or `Complete`. No other values are permitted. `Complete` covers post-wedge work (including continued Advisor-mode exploration); there is no `Post-Recommendation`.
   - **Phase substate** — free-form bullets describing mid-phase progress. Written-through after every material action (e.g., "scored urgency on `verticals/hvac.md`"; "wrote red-team pass on `comparisons/initial-comparison.md`"; "persisted `research/results/perplexity-hvac-tam-2026-04-28.md`"). This is the working buffer. If the session dies mid-phase, this block is how the next session re-hydrates.
   - **Last reliable checkpoint** — updated only at phase boundaries. States the last point at which state is known-good. Format: `<phase-just-completed> @ <YYYY-MM-DD>` + one line summarizing what's durable. The resume protocol (see `reference/guided-mode.md`) resumes from here if `Phase substate` is empty or stale.
   - **Active verticals under consideration** — one-liner + link per candidate.
   - **Active open questions** — not yet resolved.

3. **Session in progress** (scratch) — between Active Project State and Session Log. This is the draft session-log entry, updated at every phase boundary per `reference/phase-boundary-checklist.md`. On clean session end, promote to the Session Log and clear the scratch. On session death, the scratch IS the record — the next session promotes it during the resume protocol.

   Format: the same `### YYYY-MM-DD — Session N` header and 3–6 bullets that a final Session Log entry would have.

4. **Session Log** — append-only, chronological. Entry format:

   ```
   ### YYYY-MM-DD — Session N
   - Summary of what was discussed
   - Decisions made
   - Files created or updated
   - Next steps
   ```

## Update rules

### Structured sections (Founder Profile, Active Project State)

- **Rewrite in place** when new information arrives.
- Never lose information. If the founder corrects something, keep the correction but preserve the original if it was a meaningful signal about their earlier thinking — in that case, move the superseded detail to a brief `## Superseded` subsection at the bottom of the structured block, timestamped.
- If you are uncertain whether to overwrite, **ask the founder**.
- Keep the structured sections scannable. Brevity beats completeness here — deep detail belongs in `intake/founder-profile.md` and `intake/constraints-and-goals.md`, not in `MEMORY.md`.

### Session Log

- **Append only.** Never edit prior entries. Never reorder.
- **One entry per working session, composed at the end** (or at the next natural pause if the session ends mid-turn). Do not append mid-session entries or one line per file touched — track files-touched privately during the session and roll them into the end-of-session entry.
- Session number increments monotonically. `Session 1` is the first session that writes to the log.
- Date is the date you are writing, not the date being discussed. Use `YYYY-MM-DD` (zero-padded).
- Summaries are short: 3–6 bullets. Details belong in the files the session touched.

## When to update

- **After every material action within a phase** (scored a vertical on a dimension, wrote a red-team block, persisted a research call, made a mid-phase strategic decision), update `### Phase substate` immediately. This is the write-through buffer that protects against session death.
- **At every phase boundary** (Intake → Idea Exploration, Idea Exploration → Vertical Analysis, etc.), update `### Last reliable checkpoint` with the phase that just completed and a one-line summary of what's durable. At the same boundary, run `reference/phase-boundary-checklist.md` and draft/update the `### Session in progress` scratch entry.
- **Immediately after any non-trivial decision** (constraint surfaces mid-phase, weight re-negotiated with the founder, candidate added or dropped), write a `decisions/decision-log.md` entry — do not wait for phase end.
- **Immediately after any red-team pass completes** (automatic or on-demand), write a `decisions/red-team-log.md` entry alongside appending the Red-Team Pass block to the target file — do not wait for phase end.
- **At the end of every working session**, promote `### Session in progress` to the Session Log as a final entry, and clear the scratch. If the founder leaves mid-turn, the scratch is the record; the next session handles promotion.
- **Whenever founder context changes** (they share a new constraint, their timeline shifts, a new team member arrives), update the structured Founder Profile section.
- **Whenever the phase changes** (intake → idea exploration → vertical analysis, etc.), update the Active Project State `Current phase` line AND `### Last reliable checkpoint`.
- **Whenever a vertical is added, dropped, or renamed**, update the Active Verticals list.
- **Whenever a question is resolved**, move it from Active Open Questions to the `### Session in progress` scratch with a note on the resolution.

## When the log gets long

The session log grows monotonically and is loaded on every session. If it exceeds ~500 lines or the founder flags it as noisy:

1. Create `MEMORY.archive.md` (if it doesn't exist).
2. Move entries older than **90 days** out of `MEMORY.md` into `MEMORY.archive.md`, preserving chronological order.
3. In `MEMORY.md` immediately after `## Session Log`, add a single line: `*Entries before YYYY-MM-DD moved to `MEMORY.archive.md`.*`
4. Log the archiving action in the current session's entry.

Do not do this automatically on your own timeline. Do it only when the log hits the threshold or the founder asks.

## Loading order at session start

When you open a project folder:

1. Read `MEMORY.md` completely.
2. From the Active Project State, note the current mode and phase.
3. Load only the files relevant to the current phase (e.g., for Vertical Analysis, skim `verticals/*.md`; for Comparison, read the latest `comparisons/*.md`).
4. If there is a `MEMORY.archive.md` and the founder is asking about early-stage context, you may read it — otherwise leave it alone.

## What NOT to put in MEMORY.md

- Long research passages. Those live in `research/results/<topic>.md`.
- Full vertical analyses. Those live in `verticals/<name>.md`.
- The beachhead recommendation itself. That lives in `recommendations/beachhead-recommendation.md`.
- Red-team output. That appends to the red-teamed file and logs to `decisions/red-team-log.md`.

`MEMORY.md` is the **index and context anchor**, not the content store.
