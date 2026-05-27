# PM Documentation Process

- The 7-section PRD is the default unit of delivery — 9-section and executive formats exist but require explicit request; defaulting to them creates unnecessary overhead

- MVF and Future must be explicitly separated in every PRD — blurring them is the most common source of scope creep in early engineering handoffs

- Section 4 (Core Functionality) always follows What it Eats / What it Does / What it Outputs — this structure forces the author to specify inputs, state changes, and output destinations rather than describing behavior in abstract

- Background narrative belongs in Appendix A, not Section 1 — the PRD body is for engineers, not stakeholders; context and "why" are important but shouldn't dilute the functional spec

- When information is missing: proceed with labeled assumptions and an Open Questions section — never invent specifics; hallucinated requirements are worse than acknowledged gaps

- The JTBD-sliced flow needs an umbrella Initiative Brief to stay coherent — without it, child PRDs drift and cross-PRD dependencies go unmapped; the brief holds: problem, objectives, non-goals, global constraints, shared dependencies, sequencing, cross-PRD metrics

- User Stories require 7 fields: ID, persona, story (When/I want/So that), inputs, outputs, acceptance criteria, PRD reference — stories missing inputs/outputs are not engineering-ready

- Development Readiness Check has 7 failure modes to flag: MVF scope, inputs/outputs, state transitions, integration/alerting patterns, dependencies, story derivation criteria, QA acceptance criteria — any one unclear blocks handoff

- Feature & Outcome Progression tables map capability phases to user-visible outcomes — they answer "what can users do after this phase?" not "what did we build?" and are the right artifact for leadership alignment

- PR/FAQ and Executive Slide Summary are supported deliverables but rarely needed — PR/FAQ for GTM alignment, Executive Slide Summary for calendar-based phase overviews; generate only when asked

- Ask Markdown vs Word before generating a full PRD — engineers want .md, stakeholders often need .docx; transcript summaries and reviews default to Markdown

- Full-track development (PRD-driven) is warranted when: multiple user types, external integrations requiring formal specs, multi-day builds, or compliance requirements; otherwise use the lightweight track (tell the AI what to build directly)

## Sources

- [pm-docs-gpt-prompt.md](pm-docs-gpt-prompt.md) — full spec, instructions, and Claude/ChatGPT portability guide
