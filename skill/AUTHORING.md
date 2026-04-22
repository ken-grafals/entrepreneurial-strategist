# Skill Authoring Notes

(Previously `skill/CLAUDE.md`; renamed to avoid collision with Claude Code's working-directory CLAUDE.md auto-load behavior.)

This file is for anyone (you, future-you, another contributor, another Claude instance) editing the Entrepreneurial Strategist skill. It describes how the skill is structured and the invariants to preserve.

## Progressive loading

The skill is built around Claude Code's progressive-loading pattern. `SKILL.md` is the entry point and stays small enough to fit comfortably in every turn. Reference files in `reference/` are loaded **only when the relevant capability is being exercised**. Templates in `templates/` are read when a new artifact is about to be produced.

The routing table in `SKILL.md` is the source of truth for which file loads when. If you add a new reference file, add it to the routing table. If you remove one, remove the routing entry.

A well-behaved turn loads `MEMORY.md` (from the founder's project, if there is one) plus one or two reference files — never everything.

## File responsibilities

| File | Responsibility |
|---|---|
| `SKILL.md` | Entry point: frontmatter, principles, routing, mode handling, anti-scope. Do not put deep capability logic here — route to reference files instead. |
| `reference/project-scaffold.md` | The folder tree for a new founder project; preview-and-approve flow; per-file permission rules. |
| `reference/memory-format.md` | Shape and update rules for the founder's `MEMORY.md` — structured top (rewritable) + append-only session log. |
| `reference/intake-flow.md` | The question bank for founder intake and the order in which to ask. |
| `reference/idea-exploration.md` | Two paths: working backward from a raw idea, or generating candidates from a capability/interest. |
| `reference/vertical-analysis.md` | Aulet-derived single-vertical analysis: the dimensions, how to score them, how to cite research. |
| `reference/comparison-framework.md` | Multi-vertical scoring, default weighting, flip-sensitivity surfacing. |
| `reference/beachhead-recommendation.md` | Convergence, the recommendation artifact, the wedge-product concept. |
| `reference/red-teaming.md` | Triggers, output structure, tone, logging to `decisions/red-team-log.md`. |
| `reference/research-integration.md` | The three research paths and how to choose between them. |
| `reference/guided-mode.md` | The canonical 7-step flow, with permission for the founder to skip/revisit. |
| `reference/advisor-mode.md` | Open-ended interaction patterns; when to write files anyway. |

## Invariants

These do not change casually. Treat them as contracts:

1. **Never edit the founder's session log retroactively.** The log in `MEMORY.md` is append-only. New entries only.
2. **Never write outside the agreed scaffold without per-file confirmation.** The scaffold is the trust boundary with the founder.
3. **Always red-team at decision points.** At minimum: before finalizing the beachhead recommendation, before finalizing the wedge-product concept, on ingestion of external research.
4. **No sycophancy.** If the evidence is against the founder's preferred direction, say so.
5. **No pitch decks, business plans, investor-facing artifacts.** MVP anti-scope, and also long-term product anti-scope.
6. **Founder context before framework.** When specifics conflict with Aulet, specifics win. Note the conflict in the analysis.
7. **No hallucinated market data.** Either research it (see `research-integration.md`) or flag the gap in the artifact.

## Versioning

`SKILL.md` carries a version in its YAML frontmatter. Bump it when:

- **Patch** (0.1.x) — wording tweaks in reference files that don't change user-visible flow.
- **Minor** (0.x.0) — changes to flow, routing, or artifacts (e.g., adding a new reference file, changing the comparison criteria).
- **Major** (x.0.0) — scope expansion beyond MVP (e.g., adding Dunford positioning, adding Mom Test workflow). These are v2 work.

Record the reason for any bump in the repo-level commit message. The skill itself does not maintain a separate changelog; git history is the record.

## Editing the skill

1. Read `docs/mvp-spec.md` §2 first if you're unsure whether a change is in scope.
2. Prefer edits to the smallest relevant reference file. If a change affects routing, edit `SKILL.md` as well.
3. Templates in `templates/` should be minimal — just the structure the skill needs to fill in. Do not bake in opinions there; opinions belong in reference files.
4. After editing, dry-run in a scratch project:
   ```bash
   mkdir -p ~/tmp/es-test && cd ~/tmp/es-test && claude
   ```
   Exercise the affected flow. Browse the resulting files. Check that the artifact matches the template.
5. If the change alters behavior a returning founder would notice, bump the version.

## When the spec and your instincts disagree

The MVP spec is authoritative for scope. The vision document is authoritative for principles. When your instinct says "it would be better if the skill did X," and X is outside MVP scope, add a note in the relevant reference file (`<!-- v2: consider X because ... -->`) rather than implementing it. Scope discipline is part of the product.
