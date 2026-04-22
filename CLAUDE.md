# CLAUDE.md — Entrepreneurial Strategist repo

This repo contains the source of the **Entrepreneurial Strategist** Claude Code skill, along with the product vision and MVP specification that drive its design.

## What lives where

- `docs/vision.md` — full product vision. This is the "north star" document. Every substantive behavioral decision in the skill should be traceable back to a principle or capability in this document.
- `docs/mvp-spec.md` — MVP specification. This is the **authoritative scope** for the current implementation. If it is not in MVP scope (§2), it does not ship in the skill yet.
- `skill/` — the Claude Code skill itself. See `skill/AUTHORING.md` for authoring conventions.
- `README.md` — public-facing overview and install instructions.

## Authoring principles

The skill is **prompt-and-reference-file-driven** — no code. All behavior is controlled by the markdown in `skill/SKILL.md`, `skill/reference/`, and `skill/templates/`. Iteration happens by editing those files.

When making changes, follow this hierarchy:
1. **MVP spec first.** If a proposed change is outside MVP scope, it belongs in v2 — leave a note in the relevant reference file rather than implementing.
2. **Vision principles second.** When the MVP spec is silent, consult `docs/vision.md` §4 (Core Principles) — *judgment over generation*, *founder context is the moat*, *pressure-test honestly*, *teach through use*, *frameworks are tools*, *comparison is first-class*, *research is continuous*, *the founder stays in charge*.
3. **Anti-scope third.** The MVP does not produce pitch decks, does not decide for the founder, and does not pretend to substitute for primary customer research. Do not drift into any of these.

## How to install the skill locally

From this repo:

```bash
ln -s "$(pwd)/skill" ~/.claude/skills/entrepreneurial-strategist
```

(Use `cp -R` instead of `ln -s` if you prefer an independent copy.) Confirm Claude Code has picked it up by starting a new session in any folder and prompting "what should I build next" — the skill's description should match.

## How to iterate

1. **Edit the relevant reference file.** Most behavior changes are scoped to one file in `skill/reference/`. The routing table in `skill/SKILL.md` says which file governs which capability.
2. **Bump the version** in `skill/SKILL.md` if the change alters user-visible behavior.
3. **Dry-run the change** against a scratch project folder:
   ```bash
   mkdir -p ~/tmp/es-test && cd ~/tmp/es-test
   claude
   ```
   Then exercise the affected flow end-to-end.
4. **Check the artifacts.** The skill's value lives in the files it writes. After a dry run, browse the scratch project's folder tree and confirm the outputs match the relevant template in `skill/templates/`.

## How to validate

The MVP success criteria (from `docs/mvp-spec.md` §11) are the validation target:

- A founder completes Guided mode in 2–4 sessions and leaves with artifacts they value.
- A returning founder picks up productively without re-explaining context.
- Red-teaming produces at least one "I had not thought about that" moment per project.
- External research is integrated meaningfully, not just summarized.
- The folder structure is worth keeping, version-controlling, and revisiting.

Failure modes to watch for:
- Noisy folder (too many files, too small).
- Red-team output that feels generic rather than context-specific.
- Mode switches losing state.
- Sycophancy (treat as a defect, per vision §4).

## Workspace conventions

- **Writing inside `skill/` is free-form.** Edit, add, delete, restructure as needed.
- **Do not edit files in `docs/`** unless Ken explicitly asks. The vision and spec are stable reference points; changes require intentional versioning.
- **No emojis** in any file unless explicitly requested.
- **No generated marketing copy** (pitch-deck language, hype, breathless feature lists). The product's tone is "experienced peer."
