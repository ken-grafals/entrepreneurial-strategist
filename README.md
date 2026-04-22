# Entrepreneurial Strategist

A Claude Code skill that acts as a strategic thinking partner for founders making consequential decisions under uncertainty. It holds the founder's context in persistent, file-based memory, applies Aulet's *Disciplined Entrepreneurship* framework in the MVP (Dunford's *Obviously Awesome* and Fitzpatrick's *The Mom Test* extend the skill in later versions), conducts real research, and pressure-tests conclusions against reality.

**Status:** MVP — founder intake, idea exploration, vertical comparison, and beachhead recommendation. Positioning, customer-evidence workflows, GTM design, and ongoing review are deferred to v2+. See [`docs/mvp-spec.md`](docs/mvp-spec.md) for the precise scope and [`docs/vision.md`](docs/vision.md) for the product direction.

## What it does

- Builds a deep profile of the founder (or small team) — skills, geography, constraints, network, goals.
- Generates or structures candidate verticals when the founder arrives with a raw idea or a vague direction.
- Holds multiple candidates in working memory and scores them side by side against Aulet-derived criteria.
- Runs real research (via Perplexity MCP, external deep-research drop-in, or Claude's web search).
- Pressure-tests emerging recommendations — automatically at decision points and on demand.
- Outputs a file-based strategic workspace the founder can keep, version-control, and revisit.

Two modes, equal in standing:
- **Guided** — sequential flow from intake through beachhead recommendation. Best for first-time founders or anyone entering an unfamiliar domain.
- **Advisor** — open-ended, conversational. Best for operators who know what they're trying to figure out.

## Install

Clone this repo and symlink (or copy) the `skill/` directory into your Claude Code skills folder:

```bash
git clone https://github.com/ken-grafals/entrepreneurial-strategist.git
cd entrepreneurial-strategist
ln -s "$(pwd)/skill" ~/.claude/skills/entrepreneurial-strategist
```

Then open Claude Code in any project folder and ask something like *"help me figure out what to build next"* or *"I want to use Entrepreneurial Strategist."* The skill's description triggers on intent; it does not need a slash command.

### Optional: Perplexity MCP for research

Install the Perplexity MCP server for deeper research:

```bash
claude mcp add perplexity --env PERPLEXITY_API_KEY="<your-key>" -- npx -y @perplexity-ai/mcp-server
```

If Perplexity MCP is not configured, the skill will help you run research in Claude.ai, ChatGPT, or Perplexity's web app and drop the results back in as markdown.

## Repo layout

```
.
├── README.md                 # this file
├── CLAUDE.md                 # repo-level instructions (how to iterate on the skill)
├── docs/
│   ├── vision.md             # product vision document (v3)
│   └── mvp-spec.md           # MVP specification (v1)
└── skill/                    # the installable Claude Code skill
    ├── SKILL.md
    ├── AUTHORING.md          # skill authoring notes (invariants, versioning, iteration)
    ├── reference/            # progressive-load instruction files
    └── templates/            # markdown templates the skill fills in
```

## License / Status

Personal tool, shared openly under the [MIT License](LICENSE). Not yet a commercial product — use, fork, or adapt as you like.
