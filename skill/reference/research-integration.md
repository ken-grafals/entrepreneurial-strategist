# Research Integration

Loaded when you are initiating external research or consuming research the founder has dropped into the project. Research matters in this MVP for two jobs: **market sizing** and **competitive / alternatives analysis**. Other research is welcome but secondary.

Three paths, in priority order.

---

## Path 1: Perplexity MCP (preferred)

If the user has the official `@perplexity-ai/mcp-server` configured, use it directly.

### Detection

At the start of a research task, check whether any of the four Perplexity MCP tools are available:

| Tool | Purpose | Perplexity model |
|---|---|---|
| `mcp__perplexity__search` | Quick market scan, single fact-check, short competitor list | **Sonar** |
| `mcp__perplexity__ask` | Targeted factual question with citations | **Sonar** |
| `mcp__perplexity__reason` | Multi-step reasoning / competitive landscape with analysis | **Sonar Pro** |
| `mcp__perplexity__research` | Full market sizing, regulatory scan, deep-research equivalent | **Sonar Deep Research** |

If at least one is present, use Path 1. Pick the tool whose purpose matches the research task's depth — don't route every query through `research` (cost and latency) or every query through `search` (insufficient depth for sizing work). If no Perplexity tools are present, move to Path 2.

### Installation (if the user asks how)

Guide them to run:

```
claude mcp add perplexity --env PERPLEXITY_API_KEY="<their-key>" -- npx -y @perplexity-ai/mcp-server
```

Then restart Claude Code. Do **not** run this command for them — it modifies MCP config and requires the user's API key.

### Model selection

Model selection is implicit in the tool choice above — each tool is bound to a Perplexity model by the MCP server (`search`/`ask` → Sonar, `reason` → Sonar Pro, `research` → Sonar Deep Research). If a newer version of the server exposes model choice as an explicit parameter, use the corresponding model; otherwise rely on the tool-to-model mapping and note any limitation in the output.

### Caching

Cache significant Perplexity responses to `research/cache/<topic>-<YYYY-MM-DD>.md` so the founder has a local record they can re-read. "Significant" = responses used as evidence in a vertical analysis or comparison. One-off sanity checks don't need caching. Include a `**Provider:** perplexity (<tool name>)` line at the top of each cached file so the source is traceable — `research/cache/` is provider-agnostic and holds outputs from Path 1 and Path 3 both.

### Error handling

If a Perplexity call fails (network, auth, rate limit): **surface the error to the founder and offer the options** — retry, fall back to Path 2 (file-drop), fall back to Path 3 (native web search with a depth caveat). Do not silently degrade — the founder needs to know what they're getting.

---

## Path 2: External research file drop

If Perplexity MCP is not configured, or the founder prefers to use a specific external tool (Claude.ai deep research, ChatGPT deep research, Perplexity web app, Gemini deep research), use this path.

### Flow

1. **Write a research prompt** to `research/prompts/<topic>-<YYYY-MM-DD>.md` using `templates/research-prompt.template.md`. The prompt must:
   - State the **founder's context** concisely (2–4 sentences from `MEMORY.md`).
   - State the **specific research question**, not a generic one. "Size of the US home-health credentialing software market, with vendor share and TAM methodology" beats "home health market research."
   - Ask for **sources and citations**.
   - Ask the research to flag **assumptions** it makes, not just conclusions.
   - Ask explicitly: *"Do not recommend a strategic direction — that is our job. Report on the market."*

2. **Tell the founder to run it** in their preferred tool and paste the prompt. Name specific options: Claude.ai's Research feature, ChatGPT's Deep Research, Perplexity Pro web app.

3. **Instruct the founder to save the result** as markdown at `research/results/<topic>-<YYYY-MM-DD>.md` (matching the prompt filename).

4. **Wait.** The founder will come back and say the research is in, or return in a later session. When they do, or when you notice a new file in `research/results/`, read it.

5. **Run an automatic red-team pass** on the external research (see `reference/red-teaming.md`). Append the pass to the results file.

6. **Integrate findings** into the relevant vertical file(s) and the comparison. Update scores where the research moves them. Log the integration in the session log and `decisions/decision-log.md`.

### Format constraint

Markdown only. PDFs, Google Docs links, and web URLs are out of scope for this MVP — the founder needs to export/paste as markdown. If they push back, acknowledge it as a v2 item (document ingestion) and proceed with markdown for now.

---

## Path 3: Claude's native web search (fallback)

If neither Perplexity MCP nor an external deep-research tool is available, fall back to native web search.

### Caveats

- **Lower fidelity** than Path 1 or Path 2. Flag this in the output: `*This analysis was produced without Perplexity or external deep research; depth and recency are limited.*`
- Use native search for narrow questions (single stat, single competitor check). For anything requiring synthesis across multiple sources, push the founder toward Path 2.

### Logging

Save significant native-search outputs into `research/cache/<topic>-<YYYY-MM-DD>.md` with a `**Provider:** native-web-search` stamp at the top, along with the search query and the sources you read. `research/results/` is reserved for research the founder dropped in from external tools — keeping cache and founder-sourced results in separate directories preserves provenance.

---

## Choosing what to research

Research is not a blanket action — it is scoped to the decision. Typical triggers:

- **New candidate vertical added** → research market size and top competitors for that vertical.
- **Urgency or ability-to-pay dimension needs grounding** → research buying signals (recent acquisitions, regulatory changes, complaint volume).
- **Competitive density dimension is weak** → research alternatives, including non-obvious ones (incumbents, manual processes, substitutes).
- **Founder is considering a geography or regulation-heavy segment** → research the regulatory landscape.

What **not** to research:

- Generic "is this a good market?" questions. The comparison and red-team are the way to answer that, not research.
- Founder-context questions. The founder is the source of truth for their skills and network.
- Customer opinions or intent. That requires primary research, which is out of MVP scope — say so.

## Prompt quality matters

A vague research prompt produces vague output. When writing the prompt file:

- Scope tight. "Top 5 credentialing software vendors serving US home-health agencies, including private ones, with 2023–2025 activity signals" is useful. "Competitive analysis for home health" is not.
- Ask for evidence. "Cite sources. Distinguish vendor-reported revenue from analyst-estimated."
- Forbid strategic advice. "Do not tell us which segment to enter. Report on the market."

## Integration discipline

When research comes back:

1. Do **not** treat it as gospel. It is one input among many.
2. Red-team it against founder context before integrating (always).
3. Update scores in the relevant vertical file with a transparent note: `Score 3 → 4 post-research 2026-04-28: evidence of specific procurement activity in target segment.`
4. If the research contradicts the founder's prior belief, name the contradiction in the session log. Do not paper over it.
