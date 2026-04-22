<!-- v0.3.0: added compact checkpoints, post-compact rehydration, resume protocol, and phase-boundary hook per retrospective 2026-04-22 (recs 1, 2, 3). -->

# Guided Mode

Loaded when the founder is operating in Guided mode (set at project init or via `/mode guided`). This file describes the canonical sequence. The founder is always free to skip, revisit, or switch to Advisor mode; the skill remembers what has been covered and never makes the founder redo work.

## The canonical seven-step flow

Each step has an entry condition, an output, and a handoff to the next step. Each step also carries the MEMORY phase label the step corresponds to — these are the only permitted values in `MEMORY.md`'s `Current phase` line (see `reference/memory-format.md`).

### 1. Intake

**MEMORY phase:** `Intake`
**Entry:** Fresh project, or a returning project with missing intake data.
**Reference:** `reference/intake-flow.md`.
**Output:** `intake/founder-profile.md`, `intake/constraints-and-goals.md`, Founder Profile section populated in `MEMORY.md`.
**Handoff:** Summarize intake back to the founder in 5–8 bullets. Ask for confirmation or correction. Move `Current phase` to `Idea Exploration`.

### 2. Idea exploration

**MEMORY phase:** `Idea Exploration`
**Entry:** Intake is sufficient (per `reference/intake-flow.md`).
**Reference:** `reference/idea-exploration.md`.
**Output:** A candidate list of 3–4 active verticals (plus up to 2 backlog) in `MEMORY.md` under Active Verticals Under Consideration; stub files at `verticals/<slug>.md`.
**Handoff:** Offer to move to vertical analysis. Explain briefly what that will produce per candidate.

### 3. Vertical analysis

**MEMORY phase:** `Vertical Analysis`
**Entry:** Candidate list exists.
**Reference:** `reference/vertical-analysis.md`.
**Output:** A complete `verticals/<slug>.md` for each candidate. Each analysis covers all eight Aulet-derived dimensions.
**Research:** Initiated per `reference/research-integration.md` as needed. In Guided mode, kick off research proactively; don't wait for the founder to ask.
**Handoff:** When all candidates have complete (non-`RESEARCH-PENDING`) analyses, move to comparison.

### 4. Comparison

**MEMORY phase:** `Comparison`
**Entry:** All candidate analyses complete.
**Reference:** `reference/comparison-framework.md`.
**Output:** `comparisons/initial-comparison.md` with scoring matrix, weights, weighted totals, flip-sensitivity, and narrative read.
**Handoff:** Trigger an automatic red-team pass on the comparison (step 5).

### 5. Automatic red-team on the comparison

**MEMORY phase:** `Comparison` (no phase transition — this is the closing move of the Comparison phase)
**Entry:** Comparison is complete.
**Reference:** `reference/red-teaming.md`.
**Output:** Red-Team Pass section appended to `comparisons/initial-comparison.md`; log entry in `decisions/red-team-log.md`.
**Handoff:** If the pass returns "Proceed," move to recommendation. If "Revise," present the revision to the founder and act before proceeding. If "Gather more evidence," initiate the relevant research. If "Reject," stop and discuss with the founder.

### 6. Beachhead recommendation + final red-team

**MEMORY phase:** `Recommendation`
**Entry:** Comparison is final (including red-team).
**Reference:** `reference/beachhead-recommendation.md`.
**Output:** `recommendations/beachhead-recommendation.md`, with the recommendation red-teamed before it ships.
**Handoff:** Move to wedge-product concept.

### 7. Wedge-product concept + final red-team

**MEMORY phase:** `Wedge` (transition to `Complete` at the end of this step)
**Entry:** Beachhead recommendation is final.
**Reference:** `reference/beachhead-recommendation.md` (same file — covers both artifacts).
**Output:** `recommendations/wedge-product-concept.md`, with the concept red-teamed before it ships. `MEMORY.md` updated with `Selected beachhead` and `Wedge product` lines. Decision log entry.
**Handoff:** Summarize to the founder what exists, what the open primary-research questions are, and that positioning is v2. Update `Current phase` to `Complete`.

## Between-step behavior

- **At every phase transition, run `reference/phase-boundary-checklist.md` silently before writing the handoff summary.** This is the load-bearing hook that prevents session-death data loss — it captures founder facts, feedback, and domain structure into auto-memory, drafts the in-progress session-log entry, and forces immediate (not end-of-phase) decision-log and red-team-log writes.
- Always update `MEMORY.md` `### Phase substate` (working buffer) after every material action within a phase — scoring a vertical, writing a red-team, persisting a research call. Update `### Last reliable checkpoint` only at phase boundaries. See `reference/memory-format.md` for the three-layer Active Project State.
- Every session appends a single Session Log entry; see `reference/memory-format.md`. During the session, draft into `### Session in progress`.
- If the founder pauses mid-step, leave the phase label at the step they're in — do not prematurely advance.

## Compact checkpoints

`/compact` frees working context by summarizing the transcript. The summary is imperfect — it is load-bearing only when material state has already been written to files. Recommend compact **only** at the natural checkpoints named below, never between them.

Natural compact checkpoints in a Guided run:

1. **After intake is complete** — `intake/founder-profile.md`, `intake/constraints-and-goals.md`, and `MEMORY.md` Founder Profile are all written.
2. **After all vertical analyses are complete** — every `verticals/*.md` has non-`RESEARCH-PENDING` scores on all 8 Aulet dimensions.
3. **After the comparison file is written with the red-team appended** — `comparisons/initial-comparison.md` includes scoring matrix, weighted totals, flip-sensitivity, narrative read, and Red-Team Pass.
4. **(Optional) After the beachhead recommendation ships but before the wedge** — only if context feels heavy.

At each checkpoint, surface a single line to the founder: *"We just crossed a natural checkpoint. All state is persisted. If you want to free context, this is a safe place to `/compact` — resumption will work from `MEMORY.md` and the artifacts."*

**Explicitly do not recommend `/compact` between checkpoints**, regardless of how long the transcript has grown. Mid-phase state lives in the transcript; compacting would summarize it imperfectly and lose in-flight reasoning (e.g., a red-team insight that hasn't been written down yet).

## Post-compact rehydration

Immediately after `/compact` fires (detectable because the conversation has been replaced by a compact summary), **before responding to the founder**:

1. Re-read `MEMORY.md` completely — Founder Profile, Active Project State (all three layers), Session in progress scratch.
2. Re-read the last-modified artifact in the project (the file the founder and you were actively working on — latest `verticals/*.md`, the comparison, a recommendation draft).
3. Re-read the current phase's primary reference file (e.g., `reference/comparison-framework.md` if in Comparison).
4. Give the founder a one-sentence "I just re-hydrated from MEMORY and the artifacts — here's where we are: [state]." This gives them a chance to correct a bad summary before you act on it.

The post-compact summary is imperfect. Assume it missed something and verify against files on disk.

## Resume protocol (new-session pick-up)

On session start (per SKILL.md "Returning to an existing project folder"), after reading `MEMORY.md`:

1. Check whether `### Phase substate` has content beyond `### Last reliable checkpoint`. If yes, the previous session ended mid-phase — run the pick-up routine:
   - Read the substate block fully.
   - Read the target file named in the substate (e.g., "Scoring verticals/hvac.md, 5 of 8 dimensions done" → open `verticals/hvac.md`).
   - Read the current phase's primary reference file.
   - Tell the founder in one–two sentences what you've re-hydrated: *"Previous session ended with 3 of 5 vertical analyses complete; `verticals/voice-mid-market.md` has urgency scored but not ability-to-pay. Picking up from there."*
   - Proceed.
2. Check whether `### Session in progress` has a draft session-log entry. If yes (and if the draft's date is prior to today or its Session N is the number of the previous session), the previous session died before promoting the scratch — promote it to the Session Log now, clear the scratch, and mention the promotion to the founder.
3. If neither condition holds, state is clean — proceed with the normal "Current phase / Active Verticals / Active Open Questions" summary.

## Skipping and revisiting

- The founder can say "skip intake, I've got a structured bio I'll paste in." Accept it; offer to read whatever they paste and populate the intake files from it.
- The founder can say "I've already analyzed these four verticals; let me paste the analyses." Accept them; convert to `verticals/<slug>.md` files.
- The founder can return to a prior step at any time. Do not rewrite, append. If a vertical analysis is re-done post-research, the old scores stay in the file with a dated note — do not delete history.
- If the founder says "skip the red-team on the comparison," explain once why it's recommended and, if they insist, skip it. Log the skip in the decision log.

## Switching to Advisor mode

`/mode advisor` at any step switches to Advisor mode. State persists. When the founder returns to Guided (or if they stay in Advisor and do the equivalent work), the skill picks up from whatever the current phase label indicates.

## Tone and pace

- Do not rush. A Guided run is typically 2–4 working sessions (per MVP success criteria). Forcing it into one sitting produces shallow analyses.
- Do not over-explain. The point of Guided mode is structure, not lectures on why each step matters. Teach-through-use: introduce a framework concept only at the moment it becomes relevant.
- Push back on weak inputs. A Guided flow that lets through unsupported scores or hand-wavy research is worse than Advisor mode because it wears a veneer of rigor.

## Handoff checklist

Run this checklist before declaring any step's output "done" and advancing the MEMORY phase. All items must hold; if any fail, fix before handoff.

- [ ] No `{{` placeholder tokens remain in the written file.
- [ ] No `RESEARCH-PENDING` markers remain on a file marked `Complete` or `Final`.
- [ ] For comparison, recommendation, and wedge artifacts: a `## Red-Team Pass` block is present, and its Recommendation is `Proceed` — or a `Revise` that has been acted on (with the follow-up recorded in the same file).
- [ ] Scores in the comparison include the arithmetic (weighted totals and flip-sensitivity) per `reference/comparison-framework.md`, not just the rank.
- [ ] `MEMORY.md` `Current phase` matches the canonical enum and reflects the step's phase label.
- [ ] Session-log entry is composed at the end of the session (not mid-session) and summarizes files touched. (During the session, the scratch draft in `### Session in progress` is the source.)
- [ ] `decisions/decision-log.md` and `decisions/red-team-log.md` entries were written immediately after their triggering decisions/passes, not deferred to phase end (per `reference/phase-boundary-checklist.md`).
- [ ] Filenames use slug-style (lowercase, hyphenated, `YYYY-MM-DD` where dated).

## What Guided mode does NOT do

- It does not lock the founder out of Advisor mode.
- It does not prevent the founder from adding new candidates mid-comparison (but warn them: adding late biases the analysis toward the new candidate, which will have had less scrutiny).
- It does not produce v2 artifacts even if the sequence technically runs to completion. Positioning, Mom Test interview design, full GTM plans, and kill-criteria workflows are outside MVP.
