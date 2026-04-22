# Entrepreneurial Strategist — MVP Specification

## A Claude Code Skill for Founder Intake, Vertical Selection, and Beachhead Recommendation

**Author:** Ken Grafals
**Status:** Draft v1
**Date:** April 2026
**Companion document:** *Entrepreneurial Strategist Product Vision Document* (v3)

---

## 1. Purpose

This document specifies the MVP for **Entrepreneurial Strategist**, scoped as a single Claude Code skill that operates within a project folder on the user's filesystem. The MVP is the wedge implementation of the broader product vision: it delivers a useful end-to-end experience for the most validated user need (founder intake → vertical comparison → beachhead recommendation) while deferring later capabilities (positioning, customer evidence workflows, ongoing review, team collaboration, integrations).

The MVP exists to validate three things:
1. That the underlying methodology — founder context + Aulet-style structured comparison + pressure-testing + real research — produces decisions the founder values.
2. That Claude Code as a delivery surface is workable for this use case (vs. a web app, desktop app, or chat interface).
3. That the file-based artifact model creates a strategic operating system the founder returns to over time.

If those three validate, later versions extend toward the full vision. If they do not, the MVP cost is bounded and the lessons inform the next iteration.

---

## 2. Scope

### In Scope (MVP)

- Founder intake — building a structured profile of the founder (or small team) including skills, geography, network, constraints, goals, risk tolerance, current commitments.
- Idea exploration — helping the founder articulate what they want to build, or generating candidate directions if they arrive without one.
- Vertical/segment comparison — holding multiple candidate verticals or segments in parallel and scoring them against Aulet-derived criteria.
- Beachhead recommendation — converging on a recommended beachhead with reasoning grounded in founder context.
- Wedge product/service definition — first-pass description of what the founder would actually build or sell into the chosen beachhead.
- Red-teaming — both on demand and automatically at decision points.
- Research integration — three paths: Perplexity MCP (recommended), external research dropped in as files (Claude app deep research, ChatGPT deep research), or Claude's native web search as fallback.
- Two operational modes — Guided (sequential, structured) and Advisor (open-ended, conversational).
- Project scaffolding — creating and maintaining a folder structure the user can inspect, version-control, and revisit.
- Decision log — append-only record of what was decided and why.

### Out of Scope (MVP)

- **Dunford positioning workflow.** Beachhead selection is the wedge; positioning extends in v2.
- **The Mom Test customer evidence workflow.** Interview design, note interpretation, evidence-as-input — all v2.
- **GTM execution design** (channel partnerships, first-ten-customer plans, pricing models).
- **Sequencing, milestones, and kill criteria** as dedicated workflows.
- **Ongoing strategic review.** The MVP produces a snapshot; v2 supports returning for periodic review.
- **Team collaboration features.** The MVP supports solo founders; team support comes later.
- **Mode auto-detection.** Mode is chosen at project init or via a `/mode` command.
- **Tone adaptation by user state.** MVP defaults to "experienced peer" tone.
- **Integration with external tools** (Notion, Linear, CRM, etc.).
- **Web/desktop UI.** MVP is Claude Code only.

### Explicit Anti-Scope

- The MVP does not generate pitch decks, business plans, or investor-facing artifacts.
- The MVP does not make decisions for the founder. It structures, informs, and pressure-tests; final calls belong to the founder.
- The MVP does not pretend to be a substitute for primary customer research. It will tell the founder when they need to go talk to people, even though it does not (yet) help them do that well.

---

## 3. User and Usage Model

The MVP serves a single primary user persona: a founder (solo or small team operating as one decision-maker for MVP purposes) who is choosing what to build next or evaluating which vertical to enter. The user has Claude Code installed, comfort with the command line, and a project folder where they want the skill to operate.

A typical session flow for a new project:

1. User creates an empty folder, navigates into it, opens Claude Code.
2. User invokes the skill (e.g., "I want to use Entrepreneurial Strategist to figure out what to build next" or any natural-language phrasing that triggers the skill description match).
3. Skill confirms it understands the request, asks the user which mode they want (Guided or Advisor), and asks permission to scaffold the project.
4. User approves; skill creates the folder structure and `MEMORY.md`.
5. Skill begins founder intake.
6. Across one or many sessions, the founder works through intake → idea exploration → vertical candidates → comparison → beachhead recommendation.
7. Founder leaves with a populated project folder containing all artifacts, including a beachhead recommendation file and a decision log.

A typical session for a returning user:

1. User opens Claude Code in the existing project folder.
2. User invokes the skill or asks a strategic question.
3. Skill loads `MEMORY.md` and the relevant analysis files, picks up where the founder left off.
4. Founder continues the work or asks specific questions in Advisor mode.

---

## 4. Skill Architecture

### Single Skill, Progressive Loading

The MVP is **one Claude Code skill** with the standard SKILL.md entry point and progressive-loading reference files. This is the recommended Anthropic pattern and avoids the fragility of cross-skill composition.

The skill reads its own SKILL.md when triggered; the SKILL.md describes capabilities and references additional files that are loaded only when relevant. This keeps Claude Code's context window lean during simple operations and only loads detailed instructions when needed.

### Proposed File Layout for the Skill Itself

```
entrepreneurial-strategist/
  SKILL.md                          # Entry point — overview, when to trigger, top-level routing
  reference/
    project-scaffold.md             # How to create the project folder structure
    memory-format.md                # Structure and update rules for MEMORY.md
    intake-flow.md                  # Founder intake questions and sequencing
    idea-exploration.md             # Helping founders articulate or generate ideas
    vertical-analysis.md            # How to analyze a single candidate vertical
    comparison-framework.md         # Multi-option comparison logic and Aulet-derived criteria
    beachhead-recommendation.md     # How to converge on and present a recommendation
    red-teaming.md                  # Red-team triggers, structure, and output format
    research-integration.md         # Perplexity MCP, file drop, native search routing
    guided-mode.md                  # Sequential flow specification
    advisor-mode.md                 # Open-ended interaction patterns
  templates/
    MEMORY.template.md
    vertical-analysis.template.md
    comparison.template.md
    beachhead-recommendation.template.md
    research-prompt.template.md
    decision-log.template.md
```

### When Each Reference File Loads

The SKILL.md contains routing logic. Reference files are loaded by Claude only when the relevant capability is being exercised. For example:

- `intake-flow.md` loads when the skill is gathering or updating founder context.
- `vertical-analysis.md` loads when the skill is analyzing a specific candidate vertical.
- `red-teaming.md` loads when red-teaming is triggered (manually or automatically).
- `research-integration.md` loads only when external research is being initiated or consumed.

This keeps the skill's footprint small for any given operation. A typical interaction might load SKILL.md plus one or two reference files.

---

## 5. Project Folder Structure (Created by the Skill)

When the skill scaffolds a project, it creates the following structure inside the user's chosen project folder:

```
<project-name>/
  MEMORY.md                         # Main founder context, decisions, open threads
  intake/
    founder-profile.md              # Detailed founder profile (queryable, editable)
    constraints-and-goals.md        # Financial runway, timeline, risk tolerance, goals
  verticals/
    <vertical-name>.md              # One file per candidate vertical under analysis
    ...
  comparisons/
    <comparison-name>.md            # Comparison matrices (e.g., "initial-five-vs.md")
    ...
  research/
    prompts/
      <topic>-<date>.md             # Prompts the skill generates for external research
    results/
      <topic>-<date>.md             # Research files dropped by user (markdown only)
    perplexity-cache/               # Optional cache of Perplexity MCP responses
  decisions/
    decision-log.md                 # Append-only chronological record
    red-team-log.md                 # All red-team passes, traceable
  recommendations/
    beachhead-recommendation.md     # The "done" artifact for the MVP
    wedge-product-concept.md        # First-pass description of what to build
  README.md                         # Project overview, mode in use, last-touched date
```

### Permissions Model

The skill asks permission before creating any files outside the agreed structure. It also asks permission once at project init by showing the planned folder structure as a preview. After approval, the skill writes freely inside the agreed structure. Anything outside requires a per-file confirmation.

If the user declines the scaffold preview, the skill asks which parts to omit or modify and presents an updated preview.

---

## 6. MEMORY.md Structure

`MEMORY.md` is the single most important file the skill maintains. It is loaded at the start of any session in an existing project and serves as the founder's persistent context.

The file uses a hybrid structure: a structured top section (rewritten as the skill learns more) followed by an append-only chronological log.

```markdown
# Project Memory

## Founder Profile (Structured — Updated by Skill)

### Identity
- Name(s):
- Location:
- Languages:

### Background and Expertise
- Years in industry:
- Domains of expertise:
- Notable past work or ventures:
- Technical skills:

### Constraints
- Financial runway:
- Time commitment available:
- Geographic constraints:
- Other commitments (job, family, etc.):

### Goals and Values
- What success looks like:
- Risk tolerance:
- Timeline ambitions:
- Personal values that should shape the venture:

### Network and Resources
- Relevant network:
- Existing distribution channels or relationships:
- Other resources (capital, IP, prior assets):

## Active Project State (Structured)

### Mode
- Current mode: Guided | Advisor

### Phase
- Current phase: Intake | Idea Exploration | Vertical Analysis | Comparison | Recommendation

### Active Verticals Under Consideration
- (List with brief one-liner each, link to file)

### Active Open Questions
- (Questions the skill or founder has raised that are not yet resolved)

## Session Log (Append-Only — Chronological)

### YYYY-MM-DD — Session N
- Summary of what was discussed
- Decisions made
- Files created or updated
- Next steps
```

The skill rewrites the structured sections as new information arrives. The session log is append-only and never edited retroactively. This gives the founder both a current-state snapshot and a chronological record of how their thinking evolved.

---

## 7. Mode Design

The MVP launches with both modes implemented. Mode is chosen at project init or changed via a `/mode` command (interpreted by the skill, not a Claude Code primitive). Mode is recorded in MEMORY.md and persisted across sessions.

### Guided Mode

Sequential, framework-led. The skill leads the founder through a defined flow:

1. **Intake.** Founder profile, constraints, goals, network. Output: `intake/founder-profile.md` and `intake/constraints-and-goals.md`.
2. **Idea exploration.** What is the founder considering? If they arrive with a fully-formed idea, the skill helps work backward to surface assumptions. If they arrive with a vague direction or capability, the skill helps generate candidate verticals.
3. **Vertical analysis.** For each candidate (typically 3–6), the skill creates a `verticals/<name>.md` file and runs structured analysis against Aulet-derived criteria: market size, accessibility, urgency of problem, ability to pay, founder fit, competitive density, sales motion difficulty, time to revenue.
4. **Comparison.** The skill creates a `comparisons/<name>.md` file holding all candidates side by side, scored against criteria with weighting that reflects the founder's stated priorities.
5. **Red-team pass.** Automatic at this point — the skill challenges the emerging recommendation before presenting it.
6. **Beachhead recommendation.** The skill produces `recommendations/beachhead-recommendation.md` with the named winner, scoring rationale, founder-context factors that influenced the call, and a list of open questions requiring primary research.
7. **Wedge product concept.** First-pass description of what the founder would actually build or sell into the chosen beachhead. Output: `recommendations/wedge-product-concept.md`.

The flow is the canonical sequence but the founder can skip steps, revisit prior steps, or switch to Advisor mode at any point. The skill remembers what has been covered and never makes the founder redo work.

### Advisor Mode

Open-ended, conversational. No fixed sequence. The founder asks questions; the skill responds with analysis grounded in the existing project context. The founder can ask for vertical analysis, request comparisons, run red-team passes, or explore tangents.

In Advisor mode the skill is more reactive than directive. It still creates files when work warrants it (a meaningful vertical analysis becomes `verticals/<name>.md`; a comparison run becomes `comparisons/<name>.md`), but the founder drives what gets analyzed and when.

### Mode Interplay

A founder can switch modes at any time with `/mode guided` or `/mode advisor`. State and files persist across mode switches. A founder might use Guided mode for the initial pass and switch to Advisor mode to explore a specific question that came up.

---

## 8. Red-Teaming

Red-teaming is treated as a first-class capability, not a side feature.

### Triggers

- **Automatic** at decision points: when narrowing to a recommended beachhead, when finalizing a wedge product concept, when the founder appears to be making an irreversible commitment.
- **On demand** at any time: the founder can ask "red-team this" or use a `/red-team [topic]` command.
- **When external research is introduced**: when the founder drops in a Perplexity report or a third-party analysis, the skill runs a red-team pass on the report's recommendations against the founder's specific context. (This is the "Perplexity recommended trade contractors but it ignored your geography" moment from the source-conversation experience.)

### Output

Red-team output appends as a "Red-Team Pass" section to the relevant file (the comparison file, the recommendation file, the dropped research file). A copy is also logged to `decisions/red-team-log.md` with timestamp, trigger, target, and outcome.

A red-team pass includes:
- What is being red-teamed (file, recommendation, claim).
- What would have to be true for this to be wrong.
- What the skill is assuming that has not been verified.
- Founder-context factors that the analysis may be ignoring or under-weighting.
- A specific recommendation: proceed, revise, gather more evidence, or reject.

### Tone

For the MVP, red-team tone is "experienced peer" — direct, specific, evidence-based. No softening for novice users (deferred to v2).

---

## 9. Research Integration

The skill supports three research paths, recommended in order:

### Path 1: Perplexity MCP (Recommended)

The skill recommends the user install the official Perplexity MCP server (`@perplexity-ai/mcp-server`) for Claude Code. Installation is one command:

```
claude mcp add perplexity --env PERPLEXITY_API_KEY="<key>" -- npx -y @perplexity-ai/mcp-server
```

When configured, the skill uses Perplexity directly for research tasks: market sizing for candidate verticals, competitive analysis, regulatory scans. The skill chooses the appropriate Perplexity model (Sonar for standard search, Sonar Pro for reasoning, Sonar Deep Research for comprehensive analysis) based on the depth needed.

Optionally, the skill caches significant Perplexity responses to `research/perplexity-cache/` so the founder has a record of what was researched and can re-read it without re-querying.

### Path 2: External Research File Drop

If Perplexity MCP is not configured, the skill helps the user run research externally and drop the result back in.

The flow:
1. Skill writes a research prompt to `research/prompts/<topic>-<YYYY-MM-DD>.md` using a template tailored to the research target.
2. Skill instructs the user to run the prompt in their tool of choice — Claude app's deep research, ChatGPT deep research, Perplexity web app, or another.
3. User exports the research result as markdown and drops it into `research/results/<topic>-<YYYY-MM-DD>.md`.
4. User tells the skill the result is ready (or the skill checks the directory at the next interaction).
5. Skill consumes the file, runs a red-team pass against the founder's context, and integrates findings into the active analysis.

The prompt template explicitly instructs the external tool to consider the founder's context (passed in the prompt) and to surface assumptions, not just conclusions.

### Path 3: Claude's Native Capabilities

If neither Perplexity MCP nor external research is available, the skill falls back to Claude's built-in web search and reasoning. This is lower-fidelity research than the other two paths and the skill flags this in the output: "This analysis was produced without Perplexity or external deep research; depth and recency are limited."

### Format Constraints

The MVP supports markdown only for dropped research files. PDFs and other formats are out of scope (handled in v2 or by user converting to markdown manually).

---

## 10. Key Flows

This section walks through the most important user flows in concrete terms. These are not feature specs; they are the user-visible texture of the MVP.

### Flow A: New Project, Guided Mode

1. User: "I want to use Entrepreneurial Strategist to figure out what to build next."
2. Skill confirms intent, asks which mode (offers brief description of each), recommends Guided for first project.
3. User chooses Guided.
4. Skill displays the proposed folder structure and asks permission to scaffold.
5. User approves; skill creates folders and `MEMORY.md` and `README.md`.
6. Skill begins intake, asking about background, location, expertise, constraints, goals, network. Each section feeds into `intake/founder-profile.md` and `intake/constraints-and-goals.md` as it is collected.
7. Skill summarizes the founder profile and asks for confirmation/edits.
8. Skill moves to idea exploration: "What are you thinking about building, or do you want help generating candidates?"
9. User describes what they're considering (or asks for candidates).
10. Skill identifies 3–6 candidate verticals worth analyzing.
11. For each, skill creates `verticals/<name>.md`, runs research (via configured path), and populates the file with structured analysis.
12. Skill creates a comparison in `comparisons/initial-comparison.md` scoring all candidates.
13. Skill runs an automatic red-team pass on the emerging recommendation, appending findings.
14. Skill produces `recommendations/beachhead-recommendation.md` and `recommendations/wedge-product-concept.md`.
15. Skill updates `MEMORY.md` with current state and logs the session.
16. Founder leaves with a populated project folder.

### Flow B: Returning User, Advisor Mode

1. User opens Claude Code in existing project folder.
2. User: "I've been thinking more about vertical X — can we explore the partnership angle?"
3. Skill loads `MEMORY.md`, identifies that vertical X is one of the candidates analyzed previously, loads `verticals/X.md`.
4. Skill responds with analysis specific to the partnership angle, grounded in existing context.
5. If the conversation produces meaningful new analysis, skill writes it back to the relevant file.
6. Skill logs the session in `MEMORY.md`.

### Flow C: External Research Integration

1. User: "I had Perplexity Pro do a deep research report on this vertical — let me run it through the strategist."
2. Skill notes that Perplexity MCP is not configured (or is configured but the user prefers to use Pro web app for this query).
3. Skill writes a research prompt to `research/prompts/vertical-deep-dive-2026-04-21.md` and tells the user to run it.
4. User runs it externally, exports as markdown, drops it into `research/results/vertical-deep-dive-2026-04-21.md`.
5. User: "The research is in."
6. Skill reads the file, runs an automatic red-team pass against founder context, integrates findings into the relevant `verticals/<name>.md` and `comparisons/<name>.md` files, and presents a summary of what changed.

### Flow D: On-Demand Red-Team

1. User: "Red-team the recommendation."
2. Skill loads `recommendations/beachhead-recommendation.md` and the supporting comparison.
3. Skill runs a red-team pass: what would have to be true for this to be wrong, what assumptions are unverified, what founder-context factors might be under-weighted.
4. Skill appends "Red-Team Pass" section to the recommendation file and logs to `decisions/red-team-log.md`.
5. Skill summarizes findings to the user and asks whether to revise the recommendation.

---

## 11. Success Criteria

The MVP is successful if:

- A founder can complete a full Guided-mode run (intake through beachhead recommendation) in 2–4 working sessions and leaves with artifacts they value.
- The founder can return to the project weeks later and pick up productively without re-explaining context.
- The red-teaming output produces at least one moment in a typical project where the founder says "I had not thought about that."
- External research dropped into the project is integrated meaningfully, not just summarized.
- The folder structure is something the founder is willing to keep, version-control, and revisit — not a throwaway artifact.

The MVP is unsuccessful if:

- Founders complete a run and the artifacts are not referenced again.
- The red-teaming feels generic or templated rather than context-specific.
- Mode-switching causes context loss or file corruption.
- The skill writes too much to too many files and the project folder becomes noise.

---

## 12. Open Questions

These are MVP-level questions that should be resolved during build, not before:

- **SKILL.md trigger phrasing.** What natural-language phrasings should trigger the skill? "Help me figure out what to build" is obvious; less obvious cases need exploration.
- **Comparison criteria weighting.** Aulet provides default criteria but their relative weights depend on the founder. Does the MVP ask for explicit weighting, infer it from intake, or use defaults? Probably defaults with override capability.
- **How many verticals is too many?** The vision allows arbitrary candidates; the MVP needs a sensible cap (probably 6) before the comparison becomes unwieldy.
- **Perplexity MCP error handling.** If the MCP call fails, does the skill fall back to native search silently or prompt the user?
- **Red-team frequency.** Automatic red-teaming at decision points is committed; how often is too often? The MVP may need a minimum interval to avoid noise.
- **MEMORY.md size limits.** The session log grows monotonically. At what size does the skill summarize older sessions or move them to an archive file?
- **Vertical naming.** Should vertical filenames be slug-style (`small-law-firms.md`) or human-readable with spaces? Slug-style is filesystem-friendly; readability matters for the founder browsing the folder.
- **Concurrency.** What happens if the user has two Claude Code sessions open against the same project? MVP can probably ignore this and document it as a single-session tool, but worth flagging.

---

## 13. Build Considerations (Non-Specification, for Reference)

These are not part of the spec but are useful context for whoever builds this:

- **Skill format.** Standard Claude Code skill structure with SKILL.md plus reference files in `reference/` and templates in `templates/`. See https://docs.claude.com for current skill authoring documentation.
- **Distribution.** For personal use and sharing with AI meetup friends, the skill can be distributed as a directory the user clones into their `.claude/skills/` directory (or equivalent).
- **No external dependencies for the skill itself.** All skill logic runs through Claude Code; the only external dependency is the Perplexity MCP server, and only when the user configures it.
- **Versioning.** SKILL.md should include a version header so users can tell what they have installed.
- **Iterating on prompts.** Most of the skill's behavior is in the reference files (which are prompts/instructions to Claude). Iteration happens by editing those files, not by writing code.

---

## 14. Relationship to the Vision Document

This MVP delivers Capability Pillars 6.1 (Founder Intake), 6.2 (Idea Development), 6.3 (Multi-Option Comparison), 6.4 (Deep Research), 6.5 (Pressure-Testing) from the vision document — fully or partially.

It defers:
- 6.6 (Positioning) — full Dunford workflow comes in v2.
- 6.7 (Customer Evidence) — Mom Test workflow comes in v2 or v3.
- 6.8 (GTM Design) — comes after positioning.
- 6.9 (Sequencing and Milestones) — comes after GTM.
- 6.10 (Ongoing Review) — requires v2 to support meaningful review cycles.
- 6.11 (Team Collaboration) — explicitly deferred.

If the MVP validates the core hypothesis, the natural next increment is positioning (Dunford), because the wedge product concept produced by the MVP is the input to positioning work.
