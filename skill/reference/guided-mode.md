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
**Output:** A candidate list of 3–6 verticals in `MEMORY.md` under Active Verticals Under Consideration; stub files at `verticals/<slug>.md`.
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

- Always update `MEMORY.md` before ending a session (even mid-step).
- Every session appends a single Session Log entry; see `reference/memory-format.md`.
- If the founder pauses mid-step, leave the phase label at the step they're in — do not prematurely advance.

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
- [ ] Session-log entry is composed at the end of the session (not mid-session) and summarizes files touched.
- [ ] Filenames use slug-style (lowercase, hyphenated, `YYYY-MM-DD` where dated).

## What Guided mode does NOT do

- It does not lock the founder out of Advisor mode.
- It does not prevent the founder from adding new candidates mid-comparison (but warn them: adding late biases the analysis toward the new candidate, which will have had less scrutiny).
- It does not produce v2 artifacts even if the sequence technically runs to completion. Positioning, Mom Test interview design, full GTM plans, and kill-criteria workflows are outside MVP.
