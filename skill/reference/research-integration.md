<!-- v0.3.0: required persistence for Perplexity calls + sharpened model-selection decision tree per retrospective 2026-04-22 (rec 9). -->

# Research Integration

Loaded when you are initiating external research or consuming research the founder has dropped into the project. Research matters in this MVP for two jobs: **market sizing** and **competitive / alternatives analysis**. Other research is welcome but secondary.

Three paths, in priority order.

---

## Path 1: Perplexity MCP (preferred)

If the user has a Perplexity MCP server configured, use it directly. The common server surface is a single tool — `mcp__perplexity__perplexity_ask` — which is a thin wrapper over Perplexity's OpenAI-compatible `/chat/completions` endpoint. You select depth by choosing the **model** inside the request, not by choosing between different tools.

### Detection

At the start of a research task, check whether `mcp__perplexity__perplexity_ask` (or any `mcp__perplexity__*` tool) is available. If yes, use Path 1. If no, move to Path 2.

### Model selection (the key decision)

Pick the model that matches the task's depth. Default to the cheapest model that will actually answer the question — do not route every query through `sonar-deep-research`.

**Decision tree:**

- Is the question **factual** (counts, sizes, named players, recent news)? → `sonar-pro`. (Use `sonar` for a single fact check.)
- Is the question **analytical** (read the landscape, compare 2–3 options, synthesize sources)? → `sonar-reasoning-pro`.
- Is the question a **full investigation** that the agent can't reason through alone (market sizing with methodology, regulatory scan, deep competitive map)? → **confirm with the founder first** (cost + latency), then `sonar-deep-research`.

| Model | Use for | Latency | Rough cost / call |
|---|---|---|---|
| `sonar` | Single fact-check, quick competitor list, recent news scan | seconds | cents |
| `sonar-pro` | Multi-source synthesis, targeted factual question with citations | seconds | cents |
| `sonar-reasoning-pro` | Competitive landscape analysis, multi-step reasoning with web search (CoT + Pro search, no multi-minute research mode) | ~10–30s | low tens of cents |
| `sonar-deep-research` | Full market sizing, regulatory scan, deep-research equivalent — autonomously runs dozens of searches and synthesizes a long-form report | **2–5 minutes** | **$0.50–$1.00+** per call |

Prefer `sonar-reasoning-pro` when you need analysis but not a multi-minute autonomous research run. Reserve `sonar-deep-research` for the handful of decision-critical questions per project where deep synthesis genuinely changes the recommendation (e.g., vertical market sizing, regulatory landscape for a regulated segment).

### Deep research — `sonar-deep-research` specifics

This is the API equivalent of Perplexity's Research (formerly Deep Research) mode. Request shape via `perplexity_ask`:

```json
{
  "messages": [
    {"role": "user", "content": "<research question — be specific and scoped>"}
  ],
  "model": "sonar-deep-research",
  "reasoning_effort": "high"
}
```

Notes on the knobs and response:

- **`reasoning_effort`** — `low` | `medium` (default) | `high`. Directly controls how many reasoning tokens are burned and how deep it goes. Use `low` for a quicker sweep, `high` for the full pro-style deep dive. Pricing on `sonar-deep-research` is multi-dimensional (input $2/M, output $8/M, citation $2/M, reasoning $3/M, search queries $5/1k) — a single `high`-effort query can easily hit $0.50–$1.00+.
- **Latency** — expect 2–5 minutes per call. MCP/HTTP timeouts on the user's side may fire before the response arrives. If a deep-research call times out or errors, **surface it to the founder** rather than retrying blindly — retrying is expensive.
- **Response shape** — the assistant `content` starts with a `<think>...</think>` block containing the reasoning plan, followed by the final markdown report. **Strip the `<think>` block** before presenting or caching the content; keep only the report. The response also includes a `citations` array (URLs) and a `search_results` array (title/url/snippet per source) alongside `usage` with the full token/cost breakdown.
- **Before calling** — confirm with the founder that a deep-research call is warranted for this specific question. One sentence: *"This will take 2–5 minutes and cost roughly $0.50–$1 — proceed?"* Do not run deep research silently.

### Prompt quality for Perplexity calls

The prompt-quality guidance in the "Prompt quality matters" section below applies equally to MCP calls as to file-drop prompts. A vague prompt to `sonar-deep-research` burns real money for generic output — scope the question, state the founder's context in 2–4 sentences, ask for citations, forbid strategic advice.

### Installation (if the user asks how)

MCP-server specifics vary. Point the user at Perplexity's official MCP documentation and tell them it will need their `PERPLEXITY_API_KEY`. Do **not** run install commands for them — MCP config modifications and API-key handling are theirs.

If they want to call the API directly without MCP, it is OpenAI-compatible — set `base_url` to `https://api.perplexity.ai` and use any OpenAI SDK with their Perplexity key.

### Persistence (required, not optional)

**Every Perplexity call's output is persisted** to `research/results/perplexity-<topic>-<YYYY-MM-DD>.md` with the exact query at the top. This is load-bearing for resumability: if the session compacts, the research is still on disk; if the agent is reasoning through a comparison and needs to re-check a cited stat, the file is there. Transcript-only research is lost research.

This applies to **all** Perplexity models — including cheap `sonar` sanity checks. The cost of writing one file per call is trivial; the cost of re-running a lost `sonar-deep-research` call is $0.50–$1.00+ and 2–5 minutes.

Persistence location is **`research/results/`** for Perplexity-MCP outputs (not `research/cache/`). Treat MCP-originated research the same as founder-dropped external research — both are primary research material that later phases depend on. `research/cache/` remains reserved for Path 3 (native web search) outputs.

At the top of each persisted file include:

```
**Provider:** perplexity
**Model:** <sonar | sonar-pro | sonar-reasoning-pro | sonar-deep-research>
**Reasoning effort:** <low | medium | high>   (deep-research only)
**Date:** YYYY-MM-DD
**Prompt:** <the exact user message sent>
**Cost / usage:** <from the response `usage` block, if available>
```

Then the stripped report body (strip the `<think>...</think>` block first for deep-research outputs), followed by the citations list.

### Error handling

If a Perplexity call fails (network, auth, rate limit, timeout): **surface the error to the founder and offer the options** — retry (cheap models only; confirm before retrying deep research), fall back to Path 2 (file-drop), fall back to Path 3 (native web search with a depth caveat). Do not silently degrade — the founder needs to know what they're getting.

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

Save significant native-search outputs into `research/cache/<topic>-<YYYY-MM-DD>.md` with a `**Provider:** native-web-search` stamp at the top, along with the search query and the sources you read. `research/cache/` is reserved for Path 3 native-search outputs; `research/results/` holds founder-dropped external research (Path 2) and MCP-originated Perplexity calls (Path 1). Separate directories preserve provenance at a glance.

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
