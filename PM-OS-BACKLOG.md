# PM OS — Adoption Backlog

Tracks what we've reviewed from the PM OS system and the adoption status of each component. Updated as things move from backlog to implemented.

Source system: `~/ai-workspace/File Landing/PM-OS/`

---

## Implemented

| Skill / Component | Where it lives | Notes |
|---|---|---|
| Meeting Summary | `.claude/skills/meeting-summary/` | Wraps existing internal-meeting-summary-prompt.md |
| After-Action Review | `.claude/skills/aar/` | Wraps existing aar-generation-prompt.md |
| Teams Message | `.claude/skills/teams-message/` | Adapted from PM OS slack-message for Teams context |
| Status Update | `.claude/skills/status-update/` | Adapted for B&M practice reporting context |

---

## Now — Ready to implement when needed

| Item | What it is | Notes |
|---|---|---|
| PRD Review Panel | Multi-agent PRD review: Engineering / Client / Delivery / Skeptic perspectives run in parallel | Adapt PM OS prd-review-panel; replace consumer-focused reviewers with B&M-relevant ones |
| Skeptic sub-agent | Devil's advocate reviewer: "is this a real problem?", "what are we NOT building?", "could we solve this without code?" | Standalone or as part of review panel |
| Impact Sizing | Structured framework for estimating value + effort of a feature/initiative | Fills the gap in the evaluation process where "revenue impact" and "strategic value" need a sizing method |

---

## Soon — Try these out in the next few weeks

| Item | What it is | Notes |
|---|---|---|
| Napkin Sketch | ASCII wireframes + annotations for including rough layouts in PRDs or tickets | PM OS implementation is solid; adapt for B&M context |
| Generate AI Prototype | Produces copy-paste prompts for v0.dev / Lovable / Bolt.new from a PRD spec | Useful when building internal tools; try on next internal tool build |
| Prototype Feedback | Structured critique of a prototype against PRD requirements | Use alongside generate-ai-prototype |
| Journey Map | Map how a client (e.g., OT security program manager) moves through a procurement or engagement lifecycle | Consumer UX framing needs to be replaced with B&M client engagement framing |
| Decision Doc | Document a decision with rationale, alternatives, owner | Broadly applicable; minimal adaptation needed |

---

## Later — Valuable, not yet the right context

| Item | What it is | Why later |
|---|---|---|
| Strategy Sprint | Write product/practice strategy in 1-day, 1-week, or 1-month format | Right tool; need more of the practice operating model in place first |
| Activation Analysis | Setup→Aha→Habit framework for diagnosing onboarding funnel | Requires a shipped product with measurable activation events |
| Experiment Decision | When to A/B test vs. ship | Requires a large user base running live experiments |
| Experiment Metrics | STEDII framework for selecting valid experiment metrics | Same dependency |
| Feature Metrics | Define success metrics for a shipped feature | Applicable in adapted form once a platform is live |
| Feature Results | Post-launch analysis vs. predicted metrics | Requires live usage data |
| Retention Analysis | Cohort analysis, D1/D7/D14/D30 retention curves | Requires a product with recurring users |
| Expansion Strategy | Upsell/cross-sell framework based on NRR | Applicable once services are in market and being sold; framework needs translation from SaaS to project-based consulting |
| Define North Star | Identify a practice-level north star metric | Interesting once the practice is running real work |
| Planning / Rhythm Tools (daily-plan, weekly-plan, weekly-review) | Sprint-cadence planning tools | Low value given current work pattern; revisit if managing a larger backlog |

---

## Skip — Not applicable

| Item | Why |
|---|---|
| Slack message | On Teams, not Slack — replaced by teams-message skill |
| User interview / Interview guide / Interview prep / Interview feedback | Individual interview model; not the current research approach |
| User research synthesis | Same — built for one-to-one interview synthesis, not corpus research |
| Connect MCPs | Toolstack-specific; handle directly as needed |
| Ralph Wiggum | Same function as Skeptic sub-agent, just with a Simpsons persona wrapper — covered by Skeptic |
