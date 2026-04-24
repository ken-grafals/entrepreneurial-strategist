<!-- v0.4.0: added per 2026-04-23 field-signal retrospective — route venture facts to project files, not Claude auto-memory. -->

# Memory routing — project files vs. Claude auto-memory

Loaded when you are about to write a remembered fact and need to decide *where* it lives: in a project file (inside the venture's folder) or in Claude's auto-memory (the global, user-level memory store outside the project tree).

The two stores have different purposes and different lifetimes. Getting the routing wrong strands venture knowledge in a location where it either cannot travel with the project or leaks into unrelated work.

## The decision test

Before writing any remembered fact, ask:

> *If the founder starts a second, unrelated venture tomorrow, would this memory help?*

- **Yes** → Claude auto-memory. The fact is about the **user**: work style, communication preferences, stack defaults carried across ventures, generic feedback that should follow them everywhere.
- **No** → project file. The fact is about **this venture**: market shape, ICP specifics, named customers or contacts, competitive landscape, hypothesis state, channel findings, seasonality, regulatory notes.

When in doubt, **default to the project file**. Auto-memory is the rare branch, not the default. A venture fact mistakenly written to auto-memory pollutes future projects; a user-level fact mistakenly written to a project file is merely redundant.

## Worked examples

**Auto-memory (user-level, outlives this venture):**
- "Ken prefers terse responses without trailing summaries."
- "Ken's stack standard is Anthropic + Next + Postgres regardless of project."
- "Ken runs Claude Code with `--dangerously-skip-permissions`."

**Project file (venture-specific, dies if the venture dies):**
- "HVAC has bimodal seasonality — emergency after-hours calls spike in summer and winter."
- "Anthony at Duct Doctor is the first warm-contact customer-zero; he shows operator-AI pain alongside voice pain."
- "ServiceTitan has not yet shipped bundled voice AI as of 2026-Q2."
- "Mid-market HVAC owners report $1.5k–$3k/mo as a tolerable price point (H1 in active hypotheses)."

All four "project file" facts would be wrong in auto-memory — they would bleed into an unrelated legal-tech or fintech project later.

## Where in the project to write venture facts

Two canonical files inside the project scaffold:

- **`intake/project-facts.md`** — standalone venture facts without an embedded hypothesis. Market shape, seasonality, competitive notes, regulatory context, channel observations. Append-only; each fact gets a one-line source citation (call notes path, research file, email thread).
- **`intake/active-hypotheses.md`** — load-bearing **falsifiable** claims the strategy depends on, each with a confidence marker. This is the full-form store for the `### Active Hypotheses` block surfaced in `MEMORY.md` (see `reference/memory-format.md`). Reversal conditions from the beachhead recommendation and load-bearing assumptions from the wedge concept belong here.

If neither fits cleanly, fall back to the nearest existing artifact (e.g., a competitive observation belongs in the relevant `verticals/<slug>.md` or in the comparison file). Do not create new top-level files without need — prefer updating existing ones per SKILL.md's file-writing discipline.

## What makes auto-memory the wrong store for venture facts

Auto-memory exists outside the project tree. It does not travel with the project folder, is not git-trackable, and is not visible when the founder browses the venture's filesystem. Concretely:

- **Portability.** If the founder clones the project to a second machine, auto-memory does not come with it.
- **Version control.** Project files can be committed; auto-memory cannot.
- **Readability.** A future session reading the venture's folder should see the whole strategy in one place. Split state between project files and auto-memory and the founder has to mentally join two stores.
- **Project rename / reorganization.** Auto-memory is keyed to project paths. Renaming the folder orphans the memory; project files travel with the rename.
- **Permission surface.** Project writes fall inside the scaffold's approved write surface. Auto-memory writes land outside the project tree and sometimes trigger permission prompts even under `--dangerously-skip-permissions`.

None of these matter for user-level facts — work style and stack preferences *should* follow the user across projects. They matter greatly for venture-specific facts that should live and die with the venture.

## The rule

**Default to the project file. Write to auto-memory only if the fact would be useful in an unrelated project or an unrelated conversation.**

If the founder asks you to remember something ambiguous, say which store you're writing to and why before writing. One sentence. This gives them a chance to redirect before the fact lands in the wrong place.
