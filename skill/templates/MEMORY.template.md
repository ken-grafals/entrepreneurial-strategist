<!-- Governed by skill/reference/memory-format.md. Rewrite the structured sections as new information arrives. Never edit the session log retroactively. -->

# Project Memory — {{PROJECT_NAME}}

## Founder Profile

### Identity
- Name(s): {{NAMES}}
- Location: {{LOCATION}}
- Languages: {{LANGUAGES}}

### Background and Expertise
- Years in industry: {{YEARS}}
- Domains of expertise: {{EXPERTISE}}
- Notable past work or ventures: {{PAST_WORK}}
- Technical skills: {{TECHNICAL_SKILLS}}

### Constraints
- Financial runway: {{RUNWAY}}
- Time commitment available: {{TIME}}
- Geographic constraints: {{GEOGRAPHY}}
- Other commitments: {{OTHER_COMMITMENTS}}

### Goals and Values
- What success looks like: {{SUCCESS}}
- Risk tolerance: {{RISK}}
- Timeline ambitions: {{TIMELINE}}
- Personal values shaping the venture: {{VALUES}}

### Network and Resources
- Relevant network: {{NETWORK}}
- Existing distribution channels: {{DISTRIBUTION}}
- Other resources (capital, IP, prior assets): {{RESOURCES}}

## Active Project State

- **Current mode:** {{MODE}}
- **Current phase:** {{PHASE}} <!-- Intake | Idea Exploration | Vertical Analysis | Comparison | Recommendation | Wedge | Complete -->

### Phase substate

<!-- Write-through buffer — update after every material action within the current phase.
     Examples:
       - Scored urgency on verticals/hvac.md (4/5)
       - Ran flip-sensitivity on comparisons/initial-comparison.md — no flip under heavy-market; flips under heavy-fit
       - Persisted research/results/perplexity-hvac-tam-2026-04-28.md
     Delete this comment when real content is written. If the phase just started, this block can read "Phase just started — no mid-phase state yet."
-->

### Last reliable checkpoint

{{LAST_CHECKPOINT}} <!-- e.g., "Intake complete @ 2026-04-22 — intake files + MEMORY founder profile written" -->

### Active Verticals Under Consideration
- {{VERTICAL_ONELINER_1}}
- {{VERTICAL_ONELINER_2}}
<!-- Repeat one bullet per candidate, up to 4 active + 2 backlog. Delete unused bullets; do not ship placeholder tokens. -->

### Active Hypotheses

<!-- Load-bearing falsifiable claims the strategy depends on. One line per hypothesis with a confidence marker.
     Confidence markers: untested | up (strengthened) | down (softened) | confirmed | disconfirmed
     Format: "H<N>: <claim>. Confidence: <marker> (<one-line reason + date if moved>)"
     Example:
       - H1: Mid-market HVAC owners feel after-hours pain sharply enough to pay $1.5k-$3k/mo. Confidence: untested.
       - H2: ServiceTitan does not ship bundled voice AI with >=70% parity inside 12 months. Confidence: untested.
     Populated at Recommendation phase from the beachhead's reversal conditions + wedge's price/channel/moat assumptions.
     Full-form store (with reasoning and signal history) is intake/active-hypotheses.md; this block is the one-glance surface.
     Do not delete disconfirmed hypotheses — mark them `disconfirmed` so the strategy's evolution stays visible.
     Delete this comment once real hypotheses are written. -->

### Active Open Questions
- {{OPEN_QUESTION_1}}
- {{OPEN_QUESTION_2}}
<!-- Repeat one bullet per open question. Delete unused bullets. -->


## Session in progress

<!-- Scratch draft of the current session's log entry. Updated at every phase boundary per skill/reference/phase-boundary-checklist.md.
     On clean session end: promote to the Session Log below and clear this block.
     On session death: the next session promotes this block during the resume protocol.
     Format is identical to a Session Log entry:

### YYYY-MM-DD — Session N
- Summary of what was discussed so far
- Decisions made
- Files created or updated
- Next steps

If no session is currently in progress, leave this comment block intact. -->


## Session Log

<!-- Append-only. One entry per session. Never edit prior entries. Format:

### YYYY-MM-DD — Session N
- Summary of what was discussed
- Decisions made
- Files created or updated
- Next steps
-->
