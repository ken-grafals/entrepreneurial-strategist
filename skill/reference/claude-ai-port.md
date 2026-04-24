<!-- v0.1.0: new reference file documenting how to replicate the skill as a Claude.ai Project. Derived from the voice-ai-ventures port (2026-04-23). -->

# Claude.ai Port — Replicating the Skill as a Claude.ai Project

Loaded when the founder wants to replicate their Claude Code strategist project as a **Claude.ai Project** — typically so they can run advisor sessions from the iPhone app, web, or desktop app instead of (or in parallel to) the terminal.

The port is feasible but not 1:1. This file defines the substitution architecture, the gaps, the setup flow, and the authoring structure for the per-project files the founder ends up with in `claude-ai-project-agent/`.

## When to load this file

- Founder asks to set up a Claude.ai project for their venture.
- Founder wants multi-device access (iPhone, web) to strategist sessions.
- Founder asks whether running the skill as a Claude.ai project is possible.
- Author is refreshing or extending an existing Claude.ai port.

## Prerequisites — not all projects are port-ready

Port assumes the project is **past intake and into Analysis / Comparison / Recommendation / Complete phase**. Porting mid-intake is possible but under-delivers — intake is conversational and benefits from the tighter feedback loop of Claude Code. Recommended: finish intake in Claude Code, then port.

Port also assumes the founder has:

- **Shelf MCP** (or equivalent file-store MCP) connected to Claude.ai.
- **Perplexity MCP** connected — research is continuous per `research-integration.md`.
- An email / calendar MCP if outreach is part of the phase the port will operate in (e.g., iCloud MCP, Gmail MCP).

Without Shelf the port collapses — the filesystem substitute is load-bearing. Flag this and stop if Shelf is not available.

## The three-layer substitution

Claude Code reads files from disk via `Read` / `Edit` / `Write` / `Bash`. Claude.ai has no disk access — only the three layers below. The port maps skill files to layers by access pattern.

| Claude.ai layer | What it holds | Access pattern | Update cadence |
|---|---|---|---|
| **Project custom instructions** | Condensed `SKILL.md` + phase-critical reference files + routing + protocols | Every turn, always in context | Rarely (update when skill itself evolves) |
| **Project knowledge base** | Stable founder-context facts — intake files | RAG-retrieved per question | Occasionally (when facts change materially) |
| **Shelf (or equivalent MCP)** | Live artifacts, decisions, hypotheses, recommendations, dormant reference files, templates, writing styles | Fetched on demand via MCP | Every session |

**The routing rule:** if a file changes frequently, it goes in Shelf. If it's stable but referenced every turn, it goes in instructions. If it's stable and referenced sometimes, it goes in the knowledge base. This is the same reasoning Claude Code uses when deciding what to `Read` on demand vs. what lives in `CLAUDE.md` — expressed through Claude.ai's fixed layers.

## The seven gaps

Each is a real difference from Claude Code. Founders considering a port should understand all seven before starting.

### Gap 1 — No auto-loading of the full skill

Claude Code reads `SKILL.md` then `Read`s reference files on demand. Claude.ai project instructions are always-on but size-capped. The full 13 reference files + 11 templates don't fit.

**Fix:** put the 3–4 phase-critical reference files in instructions (`advisor-mode.md` + `post-recommendation-advisor.md` + red-team principles from `red-teaming.md`, plus the condensed `SKILL.md` itself). Shelf the rest. Write `entrepreneurial-strategist/skill/INDEX.md` so the agent can pick the right dormant reference file when a phase transition happens.

### Gap 2 — No Bash

No `git log`, no `find -regex`, no ad-hoc scripts. For a skill that's ~all markdown editing, the loss is manageable — `shelf_search` covers grep; `shelf_list_contents` covers `ls`; `shelf_outline` covers file-structure scans.

**Fix:** none needed. Accept the loss. Use Shelf tools where Bash would have been used. Note that Shelf versions every write automatically, which substitutes for `git diff` between versions.

### Gap 3 — No Skill chaining

Claude Code can invoke another skill mid-flow (e.g., `my-writing-styles` to draft voice-matched outreach). Claude.ai projects can't invoke other skills or projects.

**Fix:** Shelf any helper-skill content the port depends on. For writing styles: copy the guides from `my-writing-styles` to `writing-styles/` in Shelf. Add a rule to project instructions: *"Before drafting any outreach or customer-facing copy, fetch `writing-styles/<style-name>.md` from Shelf first."* Accept the manual fetch as a deliberate cost.

### Gap 4 — No auto-memory harness

Claude Code's `~/.claude/projects/<slug>/memory/` directory has no Claude.ai equivalent.

**Fix:** if the skill project is already following the convention in `memory-routing.md` (venture-specific facts in `intake/project-facts.md` and `intake/active-hypotheses.md`, not in auto-memory), no migration needed — those files already live in the project scaffold and get mirrored to Shelf. If auto-memory is holding load-bearing project state, migrate it to project-folder files **before** starting the port.

### Gap 5 — No parallel tool calls

Claude Code fires multiple tool calls per turn; Claude.ai serializes. Multi-file loads feel noticeably slower (2–3× on a "read decision-log + hypotheses + wedge" turn).

**Fix:** consolidate where natural. `MEMORY.md` is already a single-file snapshot — a typical turn fetches only that. Front-load common fetches via the session-start protocol. Accept the latency as a UX tax, not a correctness problem.

### Gap 6 — No TaskCreate / TodoWrite

Minor. Use markdown-native tracking — `first-14-days.md` as a live checklist, decision log + session log for permanent record.

### Gap 7 — Conversations don't persist across chats

Each Claude.ai chat is fresh. Same as Claude Code sessions — `MEMORY.md` + append-only decision log are the bridge. **But** in Claude.ai there's no live-session leakage to cover for sloppy MEMORY.md updates, so the discipline bar is higher.

**Fix:** make session-end hygiene an explicit instruction in the project instructions. Every decision, every field signal, every red-team pass lands in Shelf during the session it occurred in — never deferred to "next session," because next session is zero-state except for what's in Shelf + knowledge + instructions.

## Setup flow

Six steps. Steps 1–3 happen outside Claude.ai; 4–6 in Claude.ai itself.

### Step 1 — Verify MCPs in Claude.ai

Shelf, Perplexity, and outreach-related MCPs (iCloud / Gmail / etc.) must be authorized in the founder's Claude.ai account before anything else. If any are missing, stop and set up first.

### Step 2 — Migrate files to Shelf

Three passes:

1. **Skill reference + templates.** Copy `skill/reference/*.md` and `skill/templates/*.md` to Shelf at `entrepreneurial-strategist/skill/reference/` and `entrepreneurial-strategist/skill/templates/`. Write `entrepreneurial-strategist/skill/INDEX.md` — one line per reference file describing when to fetch it.
2. **Project artifacts.** Mirror the founder's `<project>/` directory to Shelf at `ventures/<project-slug>/`. Includes MEMORY.md, intake/, decisions/, recommendations/, comparisons/, verticals/, recordings/, research/. Verify append-only files (`decisions/decision-log.md`, `decisions/red-team-log.md`) migrated correctly.
3. **Helper-skill content** — writing styles or any other dependency from a chained skill. Shelf at `writing-styles/` or the appropriate root.

### Step 3 — Verify migration

`shelf_list_contents` on each expected folder. Every path the project instructions reference must resolve — otherwise the agent's first `shelf_read` fails and the session is dead.

### Step 4 — Create the Claude.ai project

- **Name:** deliberate, findable (shows up in chat history + iPhone). Recommended pattern: `<Venture> — Strategist`.
- **Description:** paste from the project's `claude-ai-project-agent/project-description.md`.
- **Custom instructions:** paste from `claude-ai-project-agent/project-instructions.md`. If rejected for length, apply the fallback — move red-team principles to a Shelf fetch rule (see "Instruction authoring" below).
- **Default model:** pin to the strongest reasoning model available (currently Opus for Anthropic). Don't leave on auto.
- **MCPs:** enable Shelf, Perplexity, and outreach MCPs on the project.

### Step 5 — Upload knowledge-base files

Four stable intake files, uploaded from the local filesystem:

- `intake/founder-profile.md`
- `intake/constraints-and-goals.md`
- `intake/strategic-constraints.md`
- `intake/project-facts.md`

These are RAG-indexed and available to every chat without re-fetching from Shelf. Do **not** upload `MEMORY.md`, decision logs, hypotheses, recommendations, or anything that changes frequently — those stay Shelf-only so there's a single source of truth.

### Step 6 — First-chat test

Open a new chat; paste the generic opener ("Where are we at?"). Expected: agent fetches `MEMORY.md` from Shelf, summarizes current state per Active Project State + Resume here, names any live clocks (reversal deadlines, runway), and offers what's next.

If the agent doesn't fetch MEMORY.md, the session-start protocol in the instructions wasn't absorbed. If `shelf_read` returns 404, Shelf migration is incomplete. If the agent gives generic advice, knowledge-base files didn't upload or aren't being retrieved.

## The `claude-ai-project-agent/` directory

Every ported project should end up with a `claude-ai-project-agent/` directory at the project root, containing seven files. This directory is the setup + operating manual for the port and should be kept in sync as the project evolves.

| File | Purpose |
|---|---|
| `README.md` | Overview + pre-setup sanity checklist (confirm MCPs, model pinned, naming, chat convention, append-only rule, etc.) |
| `SETUP.md` | Step-by-step setup guide (the six steps above, project-specific) |
| `project-description.md` | Ready-to-paste text for Claude.ai project description field (1 paragraph, describes venture + current phase + core constraints) |
| `project-instructions.md` | Ready-to-paste text for custom instructions field (condensed skill + project state + protocols) |
| `knowledge-base.md` | Manifest of files to upload + source paths + re-upload triggers |
| `shelf-layout.md` | Target Shelf tree + migration plan + verification commands + source-of-truth policy |
| `first-chat-prompt.md` | Session opener + session-end closer templates |

See `ventures/voice-ai-ventures/claude-ai-project-agent/` (in the voice-ai-ventures project) for the canonical worked example. When setting up a new port, use those files as templates — adapt the project-specific sections (state snapshot, Shelf tree, knowledge files) while preserving the structure.

## Instruction authoring

`project-instructions.md` is the hardest piece. Budget is tight (historically ~8K tokens), so every section must earn its place. Required sections, in order:

1. **Role.** One paragraph. Who the agent is for, what they do, what they don't do (autopilot).
2. **Current state snapshot.** Mode, phase, selected beachhead, selected wedge, live clocks, customer-zero status. Dated; agent verifies against MEMORY.md each session. This is the one section that's guaranteed to drift — budget for a refresh on any material strategy change.
3. **Session-start protocol.** "Fetch MEMORY.md first. Always." Plus: when to fetch which other file (recent conversation, recommendation, hypothesis file, reference file, writing-style guide).
4. **Shelf folder map.** Full tree. The agent uses this to pick paths without guessing.
5. **Routing table.** "When the user asks about X, fetch Y from Shelf." One row per common question shape.
6. **Phase-specific patterns.** For post-recommendation: the 6 patterns from `post-recommendation-advisor.md` (A outreach, B debrief, C scope, D pricing, E channel, F reconsidering beachhead). For mid-Guided-flow: the relevant `guided-mode.md` subset.
7. **Red-teaming.** Triggers, output format, principles. This is the biggest section after Shelf folder map. If length is a problem, this is what moves to Shelf first (see fallback below).
8. **Append-only discipline.** "Never use `shelf_write` or `shelf_str_replace` on decision-log or red-team-log. Only `shelf_append`." Without this rule the agent will silently rewrite history.
9. **Session-end protocol.** What must be updated before the chat ends. Load-bearing — see Gap 7.
10. **Tone.** Experienced peer, direct, no preamble. With 2–3 right-toned example sentences.
11. **Anti-scope.** Same list from `SKILL.md` — no pitch decks, no business plans, no Dunford, no Mom Test workflow, no "next 10 things" lists.
12. **When to call out drift.** The "you've asked about X three times, what would make you act?" script.

### Fallback if instructions exceed the limit

Remove sections in this order until it fits:

1. Red-team output format + principles → replace with one line: *"For any red-team pass, fetch `entrepreneurial-strategist/skill/reference/red-teaming.md` from Shelf first."* (saves ~150 lines)
2. Full Shelf folder map → replace with: *"Fetch `entrepreneurial-strategist/skill/INDEX.md` at session start."* (saves ~50 lines)
3. Routing table rows for low-frequency cases → move to INDEX.md.

Do not remove the session-start protocol, session-end protocol, or append-only discipline — those are load-bearing.

## Knowledge-base selection criteria

A file belongs in the Claude.ai knowledge base (vs. Shelf-only) if all three are true:

1. **Stable.** Updates at most once per quarter under normal project operation.
2. **Grounding-relevant.** Referenced implicitly in most turns, even if not named.
3. **Fits the RAG chunking model.** Self-contained enough that retrieval on a query like "what's the runway?" returns the right passage.

For this skill, that's exactly the four intake files. Recommendations, hypotheses, and decision logs fail criterion 1 — they update constantly. Verticals and comparisons fail criterion 2 — they're reference material, not grounding material. Templates fail all three.

## Operating conventions (document in `first-chat-prompt.md`)

- **One chat per session.** Name by date + topic (`2026-05-02 — Frazier outreach`). Fresh context each session is the same pattern as Claude Code; don't fight it.
- **Session opener:** paste a predetermined prompt (generic: "Where are we at?"). This triggers the session-start protocol deterministically even if the agent might otherwise skip MEMORY.md fetch on short questions.
- **Session closer:** paste a predetermined closer ("Run the session-end protocol: update MEMORY.md, append decisions, update hypotheses, log red-teams"). This is more important than the opener — a missed closer loses decisions.

## Source-of-truth policy

Once migration is verified, the founder must decide:

- **Shelf is canonical.** All edits through Shelf. Local filesystem is backup. Pro: single source of truth, automatic versioning, cross-device. Con: every edit is an MCP call. **Recommended default.**
- **Local fs canonical, sync to Shelf.** Edits happen locally, a sync step pushes to Shelf before each session. Pro: git history, fast local editing. Con: discipline-dependent, divergence risk.

Whichever is chosen, document it in the `shelf-layout.md` for that project.

## Keeping the Claude Code version usable in parallel

The port does not retire the Claude Code version. Both can operate if:

- Both read from Shelf (Claude Code via the Shelf MCP).
- The local filesystem is either read-only or kept in sync.
- The source-of-truth policy is clear so neither surface silently diverges.

Common pattern: Claude Code for heavy lifts (multi-file refactors, scaffolding new verticals, long research synthesis), Claude.ai for mobile / quick-turn advisor sessions (post-call debrief from the airport, "should I say yes to $8k?" from the kitchen). Both update the same Shelf artifacts.

## Red flags

Stop the port and raise with the founder if any of these appear:

- **Shelf MCP is not connected and the founder doesn't know how to connect it.** The port cannot work without it; don't proceed with partial setup.
- **Founder wants to skip the Shelf migration** and use project knowledge upload as the filesystem substitute. This fails: knowledge is read-only; decision log can't be appended to; no editability.
- **Founder wants to skip the session-end protocol** because "it's annoying." This guarantees state drift. Push back and explain Gap 7.
- **Founder wants to use Claude.ai's user-level Memory as the bridge between chats.** It's not project-scoped and not under agent write control; will silently leak state across projects or lose facts. Use MEMORY.md in Shelf instead.

## Related files

- `SKILL.md` routing table — add a row for this file: *"Porting a project to Claude.ai | `reference/claude-ai-port.md`"*.
- `memory-format.md` — MEMORY.md structure; unchanged by the port.
- `memory-routing.md` — what goes in project files vs. auto-memory; the port works best when this has already been applied (Gap 4).
- `post-recommendation-advisor.md` — the 6 patterns that drive most ported-project turns.
- `red-teaming.md` — may be fetched on-demand per the fallback rule rather than embedded in instructions.
