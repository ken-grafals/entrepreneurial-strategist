<!-- Governed by skill/reference/research-integration.md. Used for Path 2 (external file-drop) research. Fill in context and question, then hand to the founder to run in their research tool of choice. -->

# Research Prompt: {{TOPIC}}

- **Date:** {{DATE}}
- **Project:** {{PROJECT_NAME}}
- **For:** {{VERTICAL_OR_COMPARISON}}
- **Intended tool:** {{TOOL}} <!-- Claude.ai Research / ChatGPT Deep Research / Perplexity Pro / other -->

---

## Instructions to the founder

Paste everything below (from "Context" through "Output format") into {{TOOL}}. When the result comes back, save it as markdown at:

`research/results/{{TOPIC_SLUG}}-{{DATE}}.md`

Then tell me the research is in — I'll read it, red-team it, and integrate the findings.

---

## Prompt to paste

### Context

{{CONTEXT_PARAGRAPH}}

<!-- 2–4 sentences from MEMORY.md: who the founder is, what they're considering, what decision this research informs. Do not include sensitive detail. -->

### Research question

{{RESEARCH_QUESTION}}

<!-- Specific. "Size of the US home-health credentialing software market, with vendor share and TAM methodology" beats "home health market research." -->

### What to include

- Sources and citations for every non-obvious claim.
- Methodology for any estimate (top-down / bottom-up, assumptions made).
- A list of assumptions the analysis depends on, separate from the conclusions.
- Non-obvious alternatives customers currently use (including manual processes, spreadsheets, "do nothing").
- Recent (last 18 months) activity signals: regulatory changes, funding, M&A, product launches.

### What NOT to include

- **Do not recommend a strategic direction.** That is our job, not yours. Report on the market, not on what the founder should do.
- **Do not extrapolate without stating the extrapolation.** If you are inferring, say so.
- **Do not pad.** Shorter and sharper beats longer and vaguer.

### Output format

Markdown. Headers for each major claim. Citations inline. A final "Assumptions" section listing what must be true for the analysis to hold.
