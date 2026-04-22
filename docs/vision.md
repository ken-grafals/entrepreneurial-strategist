# Entrepreneurial Strategist

## Product Vision Document

**Author:** Ken Grafals
**Status:** Draft v3
**Date:** April 2026

---

## 1. Vision Statement

Entrepreneurial Strategist is an AI-powered strategic thinking partner for founders making consequential decisions under uncertainty. It holds a founder's full context — their skills, constraints, goals, and active research — in persistent memory, applies rigorous strategic frameworks, conducts real market research, and pressure-tests conclusions against reality. It is designed to help founders choose what to build, who to build it for, and how to bring it to market, with the judgment of an experienced strategist and the tirelessness of a research team.

The product meets founders where they are. A first-time founder with a raw idea gets structure, framework education, and a guided path from concept to first customer. An experienced operator weighing a pivot or comparing beachheads gets an open-ended thinking partner that can keep up with sophisticated analysis. The same product serves both through two complementary modes that are equal in standing.

It is not a pitch deck generator. It is not a business plan template. It is not a wizard that abandons the founder once the template is filled. It is the product that would have saved every founder who spent months building the wrong thing, choosing the wrong beachhead, or hiring the wrong cofounder — not by giving them answers, but by forcing the right questions and refusing to let them skip past the hard ones.

---

## 2. The Problem

Founders make a small number of decisions that determine everything that follows: what to build, for whom, how to sell it, who to build it with, and when to pivot. These decisions get made under uncertainty, with incomplete information, and with cognitive biases pulling in every direction. Get them right and execution becomes tractable. Get them wrong and no amount of execution excellence compensates.

The tools available today fail founders at this decision layer in specific, identifiable ways:

**General-purpose LLMs (ChatGPT, Claude, Gemini)** produce high-quality reasoning on demand but have no persistent memory of the founder, no enforced framework discipline, and no ability to hold multiple options in working memory across sessions. A founder comparing five verticals starts fresh every conversation and loses the synthesis work from the last one.

**Research tools (Perplexity, Gemini Deep Research)** produce comprehensive research reports but cannot apply founder-specific judgment. They recommend based on generic market analysis without knowing the founder's geography, skills, network, or constraints. They pattern-match to "bigger market wins" when the right answer for a specific founder might be the smaller, more defensible one.

**Founder copilot products (MIT JetPack, siift.ai, aicofounder, Cofounder.im)** either apply frameworks mechanically without judgment, generate one-shot documents rather than enabling iterative strategic work, or target a narrow band of the founder journey. Their market data is often placeholder. Their output is frequently optimized for investor-ready documents rather than for the founder's own decision-making. Most are designed for a single point in the founder journey and do not continue to add value as the founder progresses.

**GTM and prospecting tools (Clay, Octave, Landbase, Apollo)** are valuable but operate downstream of the strategic decision. They help execute within a chosen vertical; they do not help choose the vertical.

**Strategy consultants and fractional advisors** bring real judgment but are expensive, inconsistent, and often lack domain-specific knowledge of the founder's target verticals. They also do not retain the founder's context between engagements in any structured way.

The common failure across all of these categories is that **none of them integrate persistent founder context, framework rigor, real research, and pressure-testing judgment in one place, for founders at any stage of the journey.** That integration is where strategic decisions actually get made. That is the gap Entrepreneurial Strategist fills.

---

## 3. Who This Is For

Entrepreneurial Strategist is built for founders making strategic decisions — but the needs of a founder with a raw idea and a founder evaluating a pivot are genuinely different. Rather than picking one and underserving the other, the product is organized around the founder's current state, not their level of experience.

### The First-Time Founder with a Raw Idea

This founder has technical skill, domain knowledge, or a compelling observation about a problem — but no structured way to evaluate whether their idea is worth pursuing. They have not yet internalized frameworks like Aulet's market segmentation, Dunford's positioning, or Fitzpatrick's customer interview discipline. They need the frameworks *and* the judgment. Generic AI tools leave them staring at a blank prompt. Startup books give them frameworks without helping them apply them to their specific situation. Advisors and accelerators are expensive, episodic, and hard to access early.

For this founder, the product provides structure: a guided path through the questions that must be answered, frameworks introduced at the moment they become relevant, and gentle but honest pushback when assumptions need examining. The product teaches through use — the founder finishes with both a clearer idea and a working understanding of strategic frameworks they can carry into future decisions.

### The Founder in the Middle of the Journey

This founder has made some initial decisions — chosen a space, maybe shipped an early product, perhaps found early customers — and now faces new questions. Which segment do we double down on? Should we expand or focus? Is it time to pivot? How do we price? They need less hand-holding and more depth. Specific questions, specific analysis, real research integrated with their own accumulated context.

For this founder, the product is a thinking partner that can be summoned for specific decisions and that remembers everything from prior sessions. The founder can ask a question and get analysis grounded in their situation without re-explaining context every time.

### The Experienced Operator

This founder has a track record. They have read the books. They have pattern recognition. What they need is not structure — they have their own — but a partner who can keep up with sophisticated analysis, hold multiple options in working memory, conduct real research on demand, and push back when their reasoning has gaps. They value specificity over generality, judgment over templates, and honest disagreement over encouragement.

For this founder, the product is an open-ended sparring partner. No wizards, no fixed sequences. The founder drives; the product responds with analysis, research, pushback, and structured comparisons as the work demands.

### Solo Founders and Small Teams

Across all three states, the product supports both solo founders and small teams of up to three people. For teams, the product models each member individually and the team as a unit — capturing complementarity, gaps, and potential founder's-dilemma conflicts. Team members can contribute context, review shared analyses, and work through decisions together with the product surfacing where views diverge and helping resolve them through framework-based analysis rather than loudest-voice dynamics.

### State, Not Stage

A founder rarely occupies one state permanently. An experienced operator entering a genuinely unfamiliar domain may want the structure of Guided mode for baseline context. A first-timer who has worked through Guided mode and now understands the frameworks may want the openness of Advisor mode for a specific question. The product does not classify users and restrict them to a mode; it lets founders choose the experience that matches what they are trying to do right now.

---

## 4. Core Principles

These principles shape every design decision in the product. They are not features; they are commitments.

**Judgment over generation.** The product's primary value is helping founders think better, not producing more artifacts. A pitch deck is a side effect of strategic clarity, not a substitute for it. Every feature must be evaluated by whether it improves decision quality, not whether it produces impressive output.

**Founder context is the moat.** A generic AI can reason about beachhead markets in the abstract. Entrepreneurial Strategist reasons about *this founder's* beachhead markets, given their skills, geography, constraints, network, past decisions, and current research. Context accumulates across sessions and shapes every analysis. The product becomes more valuable the longer it is used.

**Pressure-test honestly, calibrate the delivery.** The product does not agree with founders to be agreeable. When external research conflicts with founder intuition, the product surfaces the conflict directly. When the founder's reasoning has a weakness, the product names it. The red-teaming moment — where the product challenges a recommendation that looked correct on paper — is one of the most valuable things it does. What varies with context is the tone: a first-timer exploring a raw idea gets challenged with patience and explanation; an experienced operator in the middle of vertical comparison gets challenged directly. The substance of the pressure-testing does not change. Sycophancy is a product defect regardless of user.

**Teach through use.** For founders who are encountering frameworks for the first time, the product introduces concepts at the moment they become relevant — never as a lecture, always in service of the decision being made. Over time, the founder internalizes the frameworks through application. The product is pedagogically honest: it explains *why* a framework applies, not just *what* the framework says.

**Frameworks are tools, not constraints.** The product is framework-aware but does not force a single framework on every decision. It selects the right lens for the moment and explains why. When frameworks conflict with the specifics of a founder's situation, the specifics win. The current framework stack is a working starting point, not a permanent commitment.

**Comparison is first-class.** Most strategic decisions are comparisons — between verticals, between beachheads, between partnership structures, between pricing models. The product is built from the ground up to hold multiple options in working memory, compare them against criteria, and track the comparison as new information arrives. For founders who arrive with only one idea, the product helps generate alternatives to compare against, preventing premature commitment.

**Research is continuous, not episodic.** Markets change, competitors launch, regulations shift. The product treats external reality as an ongoing input, not a one-time research pass. A vertical analysis from three months ago is re-evaluated against current conditions when the founder returns to the question.

**The founder stays in charge.** The product does not make decisions. It structures them, informs them, and stress-tests them. Final calls belong to the founder. The product is a thinking partner, not an autopilot.

---

## 5. Methodological Foundation

The product is not framework-neutral. It commits to specific methodologies for specific jobs, selected because they cover the three most common failure points in early-stage strategy. This section names the current stack and describes how the product operationalizes each framework.

The stack is a **working starting point, not a locked-in decision.** Framework-dependent capabilities are marked as such throughout this document. If the stack evolves — through use, through surfaced gaps, or through better alternatives — the product's capability pillars and principles remain stable; the specific frameworks underneath them do not.

### The Three Pillars of the Current Stack

The three frameworks address three distinct layers of the early-stage decision problem:

| Layer | Framework | What it answers |
|-------|-----------|-----------------|
| Analytical spine | Aulet's *Disciplined Entrepreneurship* (24 steps) | What should I build, and for whom? |
| Communication | Dunford's *Obviously Awesome* (positioning) | How do I explain it so the right people choose me? |
| Evidence | Fitzpatrick's *The Mom Test* | How do I know what's actually true? |

They stack rather than overlap. Aulet produces a beachhead and an end-user profile. Dunford takes that beachhead and produces a positioning statement that does not sound like every other vendor in the category. The Mom Test is the evidence layer that keeps both honest — ensuring the analytical work is grounded in what prospective customers actually think and do, rather than what the founder hopes they think and do.

### How the Product Operationalizes Aulet

Aulet's 24 steps are the analytical spine of Guided mode and the reference grammar of Advisor mode. The product treats steps 1–6 (market segmentation, beachhead selection, end-user profile, TAM, persona, full life cycle use case), 9–10 (competitive position, DMU), 15–17 (business model, pricing, LTV), and 19 (COCA) as the critical subset for the first 90 days of vertical/beachhead selection and offer design. Later steps are supported but treated as downstream once the beachhead is set.

Where the product goes beyond the book:

- **Parallel beachhead scoring.** The book asks founders to score candidate segments on criteria like accessibility, urgency, ability to pay, and word-of-mouth. The product holds multiple candidates in working memory and scores them side by side, re-scoring as new research or founder input arrives. A comparison that would take a founder weeks of manual spreadsheet work becomes a living artifact.
- **Automated desk research.** The TAM and competitive-position steps require real market data. The product runs this research on demand, integrates it into the analysis, and preserves citations.
- **Living artifacts.** The book produces static output (a filled-in worksheet). The product produces artifacts that update as conditions change and that the founder returns to over weeks or months.
- **Service-business adaptation.** Aulet is written for tech-product founders pursuing VC-fundable outcomes. Steps 11–12 on product architecture, and parts of the economic model, do not map cleanly to service businesses, productized services, or hybrid models. The product adapts or skips these steps when the founder's intended business model does not fit the book's assumptions. Whether this adaptation should be formalized into a documented variant is an open question (see Section 12).

### How the Product Operationalizes Dunford

Dunford's five-component positioning exercise (competitive alternatives → unique attributes → value → who cares most → market category) runs after the founder has a defined beachhead. The product treats positioning as a first-class deliverable, not a downstream marketing task.

Where the product goes beyond the book:

- **Alternatives surfaced with research.** The "competitive alternatives" component benefits enormously from live research. The product identifies both direct competitors and the *actual* alternatives customers use — including manual processes, spreadsheets, or doing nothing — and integrates this into the positioning work.
- **Value tied to the Aulet end-user profile.** The "who cares most" component is answered with reference to the already-defined end-user persona, not generated in isolation.
- **Output connects to downstream artifacts.** The positioning statement feeds directly into marketing copy, sales messaging, landing-page drafts, and first-ten-customer outreach. The same positioning work does not have to be redone every time a new artifact is needed.
- **Category design support.** When the positioning work suggests the founder should create a new category rather than compete in an existing one, the product makes that explicit and supports the harder work that implies.

### How the Product Operationalizes The Mom Test

The Mom Test is a technique, not a framework in the strategic sense. It is the discipline that keeps the other two honest. Its core insight — that founder-driven customer conversations produce false-positive validation unless structured to avoid it — is built into how the product treats customer evidence throughout.

Where the product goes beyond the book:

- **Interview preparation.** Before a founder goes to talk to prospective customers, the product helps design the conversation: which questions are safe to ask (past behavior, specific examples), which are dangerous (hypotheticals, opinions about an idea), and what the founder is trying to learn.
- **Evidence capture and interpretation.** When the founder returns with notes from a conversation, the product helps interpret what was actually said — distinguishing compliment from commitment, surfacing contradictions with prior founder assumptions, and flagging where the founder may have asked leading questions.
- **Evidence as a first-class input to the Aulet and Dunford layers.** Customer evidence updates the beachhead analysis and positioning work. A founder who hears consistent signals that their assumed persona is wrong does not discover this later — it feeds back into the analytical spine immediately.
- **Ongoing discipline, not one-time event.** The product treats customer conversations as a recurring practice, not a box to check. It prompts the founder to keep talking to customers throughout the journey, not just during initial validation.

Whether The Mom Test needs a structured in-app interview assistant or lives only as guidance and evidence-capture support is an open question (see Section 12).

### What This Stack Does Not Cover

The current three-framework stack is deliberately focused on **what to build, how to position it, and how to know it's real.** It is less complete on:

- **Channel and traction.** Once the beachhead is set and the positioning is clean, the founder has to find a repeatable way to reach customers. Dunford answers *what to say*; she does not answer *where to show up*. For productized-service businesses especially, this question arises immediately after beachhead selection, not later. The current stack does not include a traction framework (Weinberg & Mares's *Traction* / Bullseye was considered and deferred). This is the most likely addition to the stack — flagged as an open question in Section 12.
- **Partnership and team structure.** Founder's-dilemma questions (equity splits, vesting, role definition) are supported by the product but not grounded in a committed framework in the current stack. Wasserman's *The Founder's Dilemmas* is a candidate if a fourth pillar is warranted for team-stage decisions.
- **Customer development as a system.** Blank's customer development methodology overlaps with The Mom Test but goes further into acquisition-channel testing and pivot triggers. It was considered and deferred. If the traction gap is filled, Blank may be the better choice than Bullseye because it integrates customer discovery with acquisition testing.

None of these gaps invalidate the current stack for the product's initial scope (vertical selection, beachhead, offer design, early positioning). They are surfaced so the product's evolution path is explicit.

---

## 6. Capability Pillars

These are the major capabilities the full product supports. Not all will be in the MVP, which will be defined separately. Together they describe what Entrepreneurial Strategist becomes over time. Capabilities that depend on specific frameworks are marked *(framework-contingent)* — these may change if the framework stack changes.

### 6.1 Founder Intake and Context

The product builds and maintains a deep model of the founder: their domain expertise, technical skills, languages, geographic situation, network, financial runway, past ventures, current commitments, personal goals, risk tolerance, and values. For teams of two or three, it models each member individually and the team as a unit — capturing complementarity, gaps, and potential founder's-dilemma conflicts. This context is not a one-time intake; it is updated continuously through use.

The founder model is queryable and editable. The founder can see what the product believes about them, correct misunderstandings, and add context the product has not surfaced. Privacy controls let the founder mark certain context as sensitive or exclude it from specific analyses.

For first-time founders, intake serves a second purpose: it is often the first time they have been asked to articulate their strengths, constraints, and goals in a structured way. The intake itself is a valuable exercise.

### 6.2 Idea Development and Vertical Exploration *(framework-contingent: Aulet)*

The product meets the founder wherever their thinking starts. A founder who arrives with a raw idea gets help moving from concept to a structured set of candidate opportunities — through framework-based segmentation, jobs-to-be-done decomposition, and capability-to-market mapping. A founder who arrives with a fully-formed idea gets help working backward to identify the implied assumptions, the actual customer, the competitive landscape, and the alternatives they may not have considered. A founder who arrives with several candidates gets direct comparison.

This capability operationalizes Aulet's market segmentation step (and its service-business adaptation). The product does not assume the founder knows what a beachhead is; it explains when the concept becomes relevant and shows why it matters for their specific situation.

### 6.3 Multi-Option Comparison *(framework-contingent: Aulet scoring criteria)*

This is the capability that most closely mirrors the work done in real strategic decisions. The product holds multiple candidates — verticals, segments, products, pricing models, partnership structures — in parallel and compares them against a set of criteria that adapts to the decision type. For beachhead selection, the criteria are drawn from Aulet (market size, accessibility, urgency, ability to pay, strategic value, founder fit, competition). For other decisions, the criteria adapt.

The comparison is not a static report. It is a live artifact that updates as the founder adds information, runs experiments, or as market conditions change. The product can rank, recommend, and explain tradeoffs — but it shows its work, surfaces uncertainty, and flags when a "winner" is only marginally ahead or when the answer changes under different weightings.

For founders who arrive with a single idea they are committed to, the product can generate alternative candidates to compare against — a protection against the common failure mode of evaluating one idea in isolation and mistaking absence of comparison for conviction.

### 6.4 Deep Research and Synthesis

The product conducts real research — web search, document retrieval, structured data pulls, and synthesis across sources. It is not dependent on its training data. Research is scoped to the decision at hand: market sizing for a candidate vertical, competitive analysis for a specific product category, regulatory scan for a jurisdiction, channel research for a target segment.

Synthesis is the harder half. Research results are integrated into the founder's context and the active comparison, with conflicting sources flagged, credibility assessed, and citations preserved. The founder can always trace a claim back to its source.

### 6.5 Pressure-Testing and Red-Teaming

On demand or proactively, the product challenges its own and the founder's conclusions. It asks: what would have to be true for this to be wrong? What are we assuming that we have not verified? What does a smart skeptic say? When third-party research (from Perplexity, a consultant, a market report) is introduced into the workspace, the product evaluates it against the founder's specific context and flags where the research's generic recommendation fails to account for the founder's situation.

The tone of pressure-testing is calibrated to where the founder is. For a first-timer exploring a new idea, challenges come with explanation and patience: *here is what a skeptic would ask, here is why this matters, here is what you could do to test it.* For an experienced operator deep in comparison work, challenges are direct and peer-level: *this recommendation ignores your geography; pattern-matching to TAM produced the wrong answer.* The substance is the same; the delivery matches the context.

This capability is what transforms the product from a research summarizer into a strategic partner. The red-teaming moment — where the product disagrees with a conclusion the founder or another tool has drawn, and explains why with specific reference to the founder's context — is a core use case, not a side feature.

### 6.6 Positioning and Messaging *(framework-contingent: Dunford)*

Once a beachhead is selected, the product runs the founder through Dunford's five-component positioning exercise. Competitive alternatives are surfaced with live research (including non-obvious alternatives like manual processes or the status quo). Unique attributes are tested against those alternatives. Value is articulated in the language the end-user persona would actually use. The "who cares most" component is grounded in the Aulet-defined persona rather than generated in isolation. Market category is chosen deliberately — including a clear call on whether to compete in an existing category or to create a new one.

The positioning artifact is living: it updates as the founder learns more from customer conversations or as the competitive landscape shifts. It feeds directly into downstream capabilities — marketing copy, sales scripts, landing pages, outreach templates — without requiring the founder to redo the positioning work each time.

### 6.7 Customer Evidence and Interview Discipline *(framework-contingent: The Mom Test)*

The product supports the full loop of customer research: designing conversations that avoid false-positive validation, preparing specific questions that probe past behavior rather than hypothetical interest, capturing notes from conversations, and interpreting what was actually said. When founders return with interview notes, the product helps distinguish compliment from commitment, surfaces contradictions with prior assumptions, and flags where leading questions may have produced unreliable signal.

Customer evidence is a first-class input to the analytical spine and the positioning work. A founder whose interviews consistently contradict their assumed persona does not discover this in a separate workflow — it feeds back into the beachhead analysis immediately.

### 6.8 Go-to-Market Design

Once a beachhead is selected and positioning is clean, the product helps design the approach to market: wedge product, pricing model, sales motion, first-ten-customer plan, channel partnerships, and early messaging. It draws on the founder's network and geography to identify realistic distribution paths. It models unit economics at the level of detail the founder needs, not at the level of a generic business plan template.

This capability is currently thinner than the others because the framework stack does not yet include a dedicated channel/traction methodology. It is flagged in Section 12 as the most likely gap for the next framework addition.

### 6.9 Sequencing and Milestones

Strategy without sequencing is wishful thinking. The product helps founders sequence their next 90 days, identify the leading indicators that would unlock the next phase, and — critically — define kill criteria that would trigger a pivot or shutdown. Kill criteria are a discipline most founders avoid; the product makes them a default output. First-time founders in particular benefit from having kill criteria named explicitly, since the discipline of defining them up front is usually skipped.

### 6.10 Ongoing Strategic Review

After initial decisions are made, the product stays in the loop. It prompts periodic strategic reviews: is the beachhead working? Are the kill criteria tripping? Has the competitive landscape shifted? Is it time to expand to adjacent segments? Over time, the product accumulates a record of the founder's decisions and outcomes, which sharpens future analysis and creates a rare asset: a structured history of the founder's strategic thinking.

This capability is where the product earns its keep over the long term. A first-time founder who uses the product to pick a beachhead gets value once. A founder who returns every quarter for strategic review gets compounding value — and the product gets compounding context that makes each review sharper than the last.

### 6.11 Collaboration for Small Teams

For two- and three-person founding teams, the product supports collaborative strategic work. Team members can each contribute context, review shared analyses, disagree in structured ways, and work through decisions together. The product surfaces where team members have conflicting views and helps resolve them through framework-based analysis rather than loudest-voice-wins dynamics.

---

## 7. Mode Design: Guided and Advisor

The product operates in two modes that are equal in standing. Both access the same underlying engine, context, and capability pillars. What differs is the surface presented to the founder. Mode is a choice the founder makes based on what they are trying to do right now — not a classification the product imposes based on who they are.

### Guided Mode

Structured, sequential, framework-led. The product leads the founder through a defined flow — starting with founder and idea intake, moving through the Aulet beachhead sequence, into the Dunford positioning exercise, with Mom Test-informed customer conversations woven throughout. The flow is modeled on the three-framework stack but is not locked to it; if the stack changes, the canonical flow adapts.

Guided mode is optimized for founders who benefit from structure: first-timers who do not yet know which questions to ask, experienced operators entering an unfamiliar domain, teams who want to work through a decision systematically. Frameworks are introduced at the moment they become relevant, with explanation of why this framework applies to this decision. The founder can skip steps, override defaults, or switch to Advisor mode at any point. The product remembers what has been covered and never makes the founder redo work.

What Guided mode does *not* do is infantilize. The structure is in service of decision quality, not in service of making the founder feel led. Pushback, red-teaming, and honest assessment are just as present in Guided mode as in Advisor mode; they are delivered with more explanation.

### Advisor Mode

Open-ended, conversational, context-dense. The founder drives the conversation; the product responds with analysis, research, pushback, and structured comparisons as the work demands. There is no fixed sequence. The founder can jump between vertical comparison, pricing analysis, positioning, customer evidence interpretation, and GTM design as their thinking moves. The product tracks the state of all active analyses and maintains coherence across them.

Advisor mode is optimized for founders who know what they are trying to figure out and want a partner who can keep up. It assumes framework literacy but invokes frameworks by name when helpful. It feels like working with a senior strategic advisor who knows the founder well.

### Mode Interplay

A founder might start in Guided mode to establish baseline context, switch to Advisor mode for deep vertical comparison, and return to Guided mode to work through positioning with structure. Mode is a UI choice, not a state change — all context and analyses carry across. A team might use Guided mode for shared strategic reviews and Advisor mode for individual analysis between sessions.

The MVP may launch with a single mode to start; the vision is that both are supported and interoperate. Which mode ships first is an MVP scoping decision, not a vision question.

---

## 8. What Makes This Different

Entrepreneurial Strategist is not the first AI tool for founders. The field is crowded. What distinguishes this product is a specific combination of commitments that no existing tool makes in full:

**Persistent founder context, not session-scoped chat.** Most AI tools start fresh every conversation. Entrepreneurial Strategist accumulates a deep, queryable model of the founder that sharpens every subsequent interaction.

**Multi-option comparison as a first-class primitive, not a side effect.** Most tools evaluate one idea at a time. The product is structurally designed to hold and compare several in parallel — and to generate alternatives when the founder arrives with only one.

**A committed methodological stack, not generic advice.** The product operationalizes specific frameworks (Aulet, Dunford, Mom Test) in integrated ways, rather than treating them as references the founder is expected to consult separately. The stack is explicit and the integration is deliberate.

**Real research, integrated with judgment.** The product does live research (not just summarize training data) and integrates findings into founder-specific analysis rather than presenting them as standalone reports.

**Pressure-testing as a core feature, not a prompt trick.** The product is designed to disagree when disagreement is warranted, including with external research and with the founder. Tone is calibrated to context; honesty is not.

**Serves the full founder journey, not a single moment.** Most tools in the category optimize for a narrow slice — idea validation, pitch decks, or post-selection execution. Entrepreneurial Strategist stays with the founder from first idea through ongoing strategic review, accumulating context at every step.

**Both Guided and Advisor modes are first-class.** First-time founders and experienced operators are both genuinely served — not by being funneled into a single experience, but by choosing the mode that matches the decision they are making right now.

---

## 9. Evolution Over Time

The product described here is ambitious. It will not ship as a single release. Rather than a roadmap — which belongs in a separate planning document — this section describes the general arc of evolution.

**Early stages** focus on the founder intake, idea development, vertical comparison, and initial positioning capabilities, because these are where the product's differentiation is clearest and where existing tools are weakest. The MVP will likely concentrate here: understanding the founder, surfacing candidate directions, running structured Aulet-based comparisons, and delivering a beachhead recommendation with a defined wedge product and first-pass Dunford positioning.

**Middle stages** extend into customer evidence workflows (Mom Test-informed interview support), GTM design, sequencing, and kill criteria — the work that turns a chosen beachhead into an executable plan. The product begins to retain a record of decisions and outcomes, which sharpens future analysis. This is also the stage where the framework stack is most likely to expand, probably to include a channel/traction methodology.

**Later stages** expand into ongoing strategic review, team collaboration, and integration with execution tools. The product becomes a strategic operating system that stays with the founder across ventures, not just a tool used once to pick a beachhead.

Throughout, the product stays true to its principles: judgment over generation, founder context as the moat, pressure-testing as a core behavior, the founder in charge, and teach-through-use as the default disposition toward founders who are still building their strategic vocabulary.

---

## 10. What This Is Not

Clear scoping is easier when what is excluded is stated directly:

- **Not a pitch deck generator.** Deck generation may exist as a downstream capability, but it is not the product's purpose.
- **Not a business plan template.** Templates are static; this product is dynamic.
- **Not a prospecting or GTM execution tool.** Clay, Octave, and similar tools do that work well; Entrepreneurial Strategist operates upstream of them and can hand off to them.
- **Not a cofounder matching service.** Partnership analysis is supported; matchmaking is not.
- **Not a replacement for talking to customers.** Primary market research is irreplaceable. The product prepares the founder to do it well and processes what comes back — that is the Mom Test layer.
- **Not a fundraising tool.** Fundraising readiness may be a downstream capability, but the product is optimized for strategic clarity, not investor appeal.
- **Not an autopilot.** The product never decides for the founder. It structures, informs, and pressure-tests.
- **Not a school.** Frameworks are taught in service of decisions, not as curriculum. The product does not replace books, courses, or human mentorship; it complements them.

---

## 11. Open Product Questions

These are product-level questions the vision does not yet resolve. Framework-specific questions are captured separately in Section 12.

- **Guided mode flow.** What is the canonical flow through Guided mode? How much is prescribed versus how much the founder can rearrange?
- **Mode detection.** Does the product suggest a mode based on the founder's question, or does the founder always choose? Both have tradeoffs.
- **Team collaboration model.** For two- and three-person teams, does the product support asynchronous multi-user contribution, real-time sessions, or both? What is the conflict-resolution mechanism when team members disagree?
- **Integration surface.** Does the product expose an API, integrate with existing tools (Notion, Slack, Linear, CRM), or stand alone? For personal use this is less urgent; for broader sharing it matters.
- **Privacy and data model.** What is stored where? What can the founder export, delete, or mark sensitive? The product's value depends on deep context retention, which raises real privacy stakes.
- **Commercial model, if any.** The product starts as a personal tool with selective sharing to trusted peers. If it later becomes commercial, the pricing and positioning decisions sit outside the vision document.

---

## 12. Open Framework Questions

These are questions about the methodological foundation specifically. They are separated from product questions because the answers may change the framework stack, and framework-contingent capabilities will need to adapt accordingly.

- **Aulet service-business adaptation.** Aulet's 24 steps are written for tech-product founders pursuing VC-fundable outcomes. Steps 11–12 (product architecture) and parts of the economic model do not map cleanly to service businesses, productized services, or hybrid models. Should the product maintain a formal documented variant for service-business founders, or handle this inline through Guided mode adaptations? The answer affects the canonical Guided flow and the scoring criteria in multi-option comparison.
- **The Mom Test interview assistant.** Does The Mom Test need a structured in-app interview assistant (real-time prompts, question suggestions during a customer conversation) or does it live as pre-conversation preparation and post-conversation interpretation? The more ambitious version is a larger product commitment and may exceed MVP scope.
- **Channel and traction framework.** The current three-framework stack is thin on the "how do I actually reach customers" question. For productized-service businesses in particular, this question arises immediately after beachhead selection. Bullseye (Weinberg & Mares) was considered and deferred; Blank's customer development was also considered and may be a better fit because it integrates customer discovery with acquisition testing. If a fourth pillar is added, which one, and at what trigger point in the founder journey does it activate?
- **Partnership and team-structure framework.** Founder's-dilemma questions (equity splits, vesting, role definition) are supported in the product but not grounded in a committed framework in the current stack. Wasserman's *The Founder's Dilemmas* is a candidate if a partnership-specific framework is warranted. The gap is less urgent than the traction gap but real for three-person team users.
- **Framework conflict resolution.** When two frameworks would suggest different approaches — for example, Aulet's TAM-driven approach to beachhead selection versus a founder-fit-driven approach derived from customer evidence — how does the product resolve the conflict? The current principle ("the specifics win") is a direction, not an algorithm.
- **Framework deprecation.** If a framework in the current stack is found to be the wrong fit through use, what is the process for removing or replacing it? The product's capability pillars should remain stable; the underlying methodology may not.

---

## Appendix A: Example Scenarios

The following scenarios illustrate the product in use across different founder states. They are not feature specs; they are texture.

**Scenario 1: The first-timer with a raw idea.** A founder with ten years of nursing experience has an idea for a tool that helps home health agencies manage caregiver credentials. She has never started a company. She enters Guided mode. The product begins with founder intake, asking about her background, network, geography, and constraints. It moves into idea exploration, introducing Aulet's market segmentation framework at the moment it becomes relevant and showing how it applies to her specific idea. It generates candidate segments she had not considered — small independent agencies, larger multi-state operators, franchise networks — and helps her compare them against Aulet's criteria. Once she selects a beachhead, the product guides her through Dunford's positioning exercise and prepares her for her first round of Mom Test-style customer conversations. By the end of the flow, she has a defined beachhead, a first-pass positioning statement, a list of customers to interview, a set of interview questions designed to avoid false-positive validation, and a working understanding of frameworks she can carry forward.

**Scenario 2: The vertical comparison.** A solo founder with deep domain expertise in conversational AI arrives with five candidate verticals he is considering. He enters Advisor mode. The product pulls his context (skills, geography, network, constraints), runs structured research on each vertical, and produces a side-by-side comparison against Aulet's beachhead criteria adapted to his situation. When the comparison surfaces a counterintuitive recommendation, he asks the product to defend it. The product explains the reasoning and notes the specific founder-context factors that flipped the ranking from what a generic analysis would produce.

**Scenario 3: The red-team.** A founder pastes in a research report from a third-party tool recommending a specific vertical as the best beachhead. The product reviews the report, identifies the founder-context factors the external tool missed, and recommends reconsidering. It does not simply agree with the external report because it is external and polished; it evaluates it against the founder's specific situation and pushes back where warranted.

**Scenario 4: Customer evidence feeding back.** A founder has completed a Guided-mode run and selected a beachhead. She conducts five customer conversations using the interview questions the product helped her design. She returns with notes. The product reads her notes, distinguishes compliment from commitment, surfaces that three of the five interviews suggest her assumed persona is off (the decision-maker is not who she thought), and recommends revisiting the Aulet end-user profile step before moving deeper into positioning. The founder avoids six weeks of building the wrong offer for the wrong buyer.

**Scenario 5: The mid-journey pivot analysis.** A founder two years into a venture is seeing flat growth and is considering a pivot to an adjacent segment. He enters Advisor mode and asks the product to pull his original beachhead analysis, compare the current state against the kill criteria defined at launch, and evaluate the pivot candidate against Aulet's criteria alongside fresh Mom Test-style evidence from recent customer conversations. The product does not have to re-learn his business; it has been in the loop throughout.

**Scenario 6: The ongoing review.** A founder who used the product six months ago to pick a beachhead returns to check in. The product pulls up the prior analysis, runs fresh research on current market conditions, compares the founder's progress against the kill criteria defined at launch, and surfaces whether the beachhead is still the right one or whether a pivot should be considered. The founder does not have to re-explain context; it is all still there.
