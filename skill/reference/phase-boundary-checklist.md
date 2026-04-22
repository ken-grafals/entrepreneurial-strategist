<!-- v0.3.0: added per retrospective 2026-04-22 (rec 1) — mid-phase memory capture to prevent session-death data loss. -->

# Phase-Boundary Checklist

Loaded at every phase transition in Guided mode, and at any equivalent break in Advisor mode (e.g., when a sub-task concludes and the founder changes direction). The checklist is self-directed — you run through it without prompting the founder. Its job is to prevent load-bearing insight from evaporating if the session is compacted or ends unexpectedly.

Memory discipline in this skill is **continuous, not terminal**. Waiting until end-of-session to capture what was learned is how insight gets lost. This file defines the mid-phase capture rule.

## Three capture questions — ask yourself before writing the handoff summary

Before transitioning to the next phase, pause and answer these three questions silently. Write anything load-bearing into the appropriate place.

### 1. Did I learn a fact about the founder in this phase that is not already in `MEMORY.md`?

If yes: update `MEMORY.md` Founder Profile **and** write an auto-memory of type `user` (see `/Users/kengrafals/.claude/projects/-Users-kengrafals-Workspace-entrepreneurial-strategist/memory/` conventions). Examples from past sessions: the founder's PR base was a geographic anchor, not a bonus; the founder's Spanish-language capability is a credential, not a wedge; the founder's years at a F1000 are a sales-trust weapon, not enterprise-experience baggage.

### 2. Did the founder correct my approach or validate a non-obvious choice?

If yes: write an auto-memory of type `feedback`. Include the **why** (the reason the founder gave — often a past incident or strong preference) and **how to apply it** (when/where this guidance kicks in). Corrections are easy to notice; validations are quieter — watch for the founder accepting an unusual approach without pushback, and save that too.

### 3. Did I discover a structural property of the domain / market / vertical that future sessions will need?

If yes: write an auto-memory of type `project`. Structural properties are facts about how the market works that are not obvious from code or public research — bimodal seasonality, procurement cycles tied to regulatory dates, buyer personas that self-select. These are expensive to re-derive.

If the answer to all three is "no," move on. Do not invent captures to seem thorough.

## Draft the session log entry now

At every phase boundary, draft a Session Log entry into the **`### Session in progress`** scratch section of `MEMORY.md` (see `reference/memory-format.md`). Do not wait until session end.

The scratch draft uses the normal session-log format (`### YYYY-MM-DD — Session N` header with 3–6 bullets) but lives above the append-only log. On clean session end, promote the scratch to the Session Log and clear the scratch. If the session dies, the scratch IS the record — the next session promotes it during the resume protocol.

## Immediate decision-log and red-team-log entries

Write decision-log and red-team-log entries **immediately after the decision or pass**, not at the end of the phase. Mid-phase decisions and mid-phase red-teams both qualify. A decision logged at phase end is a decision that the next session will not find if the transcript is compacted between the decision and the log entry.

Specifically:
- A strategic constraint that emerges mid-phase (e.g., "venture must run on own stack, not third-party enterprise platforms") gets a `decisions/decision-log.md` entry at the moment the founder articulates it.
- A red-team pass — automatic or on-demand — gets a `decisions/red-team-log.md` entry at the moment it completes, appended alongside the Red-Team Pass block on the target file.

## Handoff summary follows the capture

Only after the three questions are answered and the scratch is updated do you write the handoff summary to the founder (the "here's what we finished, here's what's next" sentence or two). The order is deliberate: capture first, then summarize.

## What this checklist does NOT do

- It does not introduce a new founder-facing prompt. The capture is silent on the agent's side.
- It does not replace the end-of-session Session Log. It feeds it.
- It does not duplicate work the founder already did. If the founder has already articulated a constraint and it's already in `intake/constraints-and-goals.md`, don't re-capture — verify, then move on.
