<!-- Governed by skill/reference/project-scaffold.md. Written into the founder's project folder at scaffold time. -->

# {{PROJECT_NAME}}

This folder is a working project maintained by the **Entrepreneurial Strategist** Claude Code skill. It holds the founder's context, candidate verticals, comparisons, research, and the resulting beachhead recommendation.

- **Mode:** {{MODE}}
- **Started:** {{DATE}}
- **Last touched:** {{LAST_TOUCHED}}

## How to use this folder

Open this folder in Claude Code and ask any strategic question, or say "let's continue" to pick up where you left off. The skill reads `MEMORY.md` first and re-orients before responding.

## What's in here

- `MEMORY.md` — founder profile, project state, and session log.
- `intake/` — deep founder profile and constraints/goals.
- `verticals/` — one file per candidate under analysis.
- `comparisons/` — side-by-side scored comparisons of verticals.
- `research/` — research prompts (`prompts/`), founder-dropped external results (`results/`), and a provider-agnostic cache of significant research outputs the skill ran (`cache/`).
- `decisions/` — append-only decision log and red-team log.
- `recommendations/` — beachhead recommendation and wedge-product concept, once produced.

## Version control

This folder is safe to put under git. The skill does not write secrets. If you share the folder with a collaborator, know that `MEMORY.md` and the intake files contain personal context about you — redact before sharing if that matters.
