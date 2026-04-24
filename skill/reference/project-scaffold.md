# Project Scaffold

Loaded when you are creating the folder structure for a new founder project, or when a founder has navigated to an empty folder and wants to start.

## The tree

When the founder approves, create exactly this structure inside their chosen project folder:

```
<project-name>/
  MEMORY.md                          # founder context + session log (see memory-format.md)
  README.md                          # brief project overview (see templates/project-README.template.md)
  intake/
    founder-profile.md               # identity, background, expertise
    constraints-and-goals.md         # runway, time, risk tolerance, goals
  verticals/                         # one file per candidate under analysis
    .gitkeep
  comparisons/                       # multi-vertical side-by-sides
    .gitkeep
  research/
    prompts/                         # research prompts the skill generates
      .gitkeep
    results/                         # external research dropped in by the founder (markdown only)
      .gitkeep
    cache/                           # provider-agnostic cache of research responses worth re-reading (Perplexity MCP, native web search)
      .gitkeep
  decisions/
    decision-log.md                  # append-only chronological record
    red-team-log.md                  # every red-team pass, traceable
  recommendations/
    .gitkeep                         # beachhead-recommendation.md and wedge-product-concept.md land here when ready
```

`.gitkeep` is an empty file that keeps empty directories tracked if the founder version-controls the folder.

Two additional files in `intake/` are created on demand, not at scaffold time, and only when first needed:

- `intake/project-facts.md` — venture-specific facts (market shape, seasonality, competitive notes) that should live with the project rather than in Claude auto-memory. See `reference/memory-routing.md`.
- `intake/active-hypotheses.md` — full-form store for the load-bearing falsifiable claims mirrored into the `### Active Hypotheses` block of `MEMORY.md`. Created at Recommendation phase. See `reference/memory-format.md`.

## Preview-and-approve flow

Before writing anything:

1. Show the founder the tree above, in a fenced code block.
2. Name each top-level directory and explain what it's for in one line (Intake, Verticals, Comparisons, Research, Decisions, Recommendations).
3. Ask: "Can I create this structure here? I'll also create `MEMORY.md` and `README.md` from templates."
4. Wait for explicit approval.

If the founder declines or wants changes:

- Ask which parts they want to omit or modify. Do not assume.
- Present an updated preview.
- Wait for approval before writing.

If the founder has an opinion about the project folder name, use it. Otherwise, the folder they are already in is fine; you don't need to create a nested one.

## Writing the scaffold

Once approved:

1. Create the directories.
2. Write `MEMORY.md` from `templates/MEMORY.template.md`. Fill in the `Mode` line with the founder's chosen mode and the `Phase` line with `Intake`. Leave the founder profile sections empty — they fill in during intake.
3. Write `README.md` from `templates/project-README.template.md`.
4. Create `decisions/decision-log.md` (empty, with a header — use `templates/decision-log.template.md`).
5. Create `decisions/red-team-log.md` (empty, with a header — use `templates/red-team-log.template.md`).
6. Create the `.gitkeep` files in the otherwise-empty directories.

Confirm the scaffold is in place with a short list of what was created (one line per top-level directory), then load `reference/intake-flow.md` and begin intake.

## After the scaffold exists

Once the scaffold is written, **you have blanket permission to write inside it without re-asking.** Anything outside it — e.g., a new top-level directory, a file at the root that isn't `MEMORY.md` or `README.md` — requires a per-file confirmation.

Do not create a file just because a template for it exists. Create a file when the work warrants it. Empty artifacts are noise.

## Non-empty starts

If the founder points you at a folder that already has an Entrepreneurial Strategist structure (from a prior session):

- Do **not** overwrite.
- Read `MEMORY.md` and pick up per the returning-session instructions in `SKILL.md`.

If the folder has unrelated files and the founder still wants to scaffold:

- Show the tree.
- Flag any naming conflicts (e.g., they already have a `research/` folder for something else).
- Ask how they want to resolve.
