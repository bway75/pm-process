# Concept Narrative — OT Security Operationalization Assessment (OPRA)

**Status:** Draft — pending evaluation  
**Author:** PM  
**Date:** 2026-05

---

## Problem

Organizations purchase OT security tools and then fail to operationalize them. Fewer than 10% of OT networks are meaningfully monitored — a figure federally corroborated by CISA in August 2025 alongside American Water, BP, Duke Energy, and Southern California Edison. The dominant failure mode is not the tools themselves. It is operational: no one trained to use the tool, no process for reviewing its output, no integration with adjacent systems, no documented response to what it finds.

This is not a problem security vendors can solve. Their revenue depends on selling additional tools. No vendor has a commercial incentive to maximize operationalization of a competitor's product, and evidence that a competitor's tool isn't running is not something any vendor can productize.

Burns & McDonnell / 1898 & Co. holds a different position. We are an engineering firm with OT domain credentials and no tool-vendor revenue model. We can enter this gap credibly in a way pure security consultancies cannot — because operationalizing OT security requires engineering knowledge of the industrial environment, not just cybersecurity expertise.

No named commercial product or service addresses operationalization as a standalone, structured offering.

---

## Goals

**MVF:** 1898 engagement teams can run a structured operationalization assessment and deliver a scored, client-facing gap report. The platform provides structure and consistency; the engagement team provides OT operational interpretation.

**12 months:** Establish OPRA as a named 1898 service offering, differentiated by operationalization depth rather than tool licensing or implementation resale.

**Longer term:** Build a cross-client benchmark dataset. No single client engagement can see across the market. Aggregated anonymized data from repeated engagements creates a differentiated insight layer no vendor or consulting competitor holds.

---

## Direction

A platform-backed assessment service. The platform is an internal tool in MVF — engagement leads use it, clients do not log in. The client receives a deliverable: a scored gap report and prioritized remediation roadmap, delivered as a 1898-branded document.

The assessment structure:

- **Tool inventory** — what does the client have?
- **Operationalization scoring** — for each tool, across six dimensions, is it running and producing value?
- **Root cause mapping** — why is it not running? (staffing / process / configuration / integration / licensing)
- **Remediation roadmap** — what actions, in what sequence, will improve the score?

Six operationalization dimensions per tool: Installation and connectivity · Configuration · Data completeness · Staff proficiency · Process integration · Lateral integration.

---

## Fit Assessment

**Strategic:** Directly addresses the highest-confidence finding from the 27-track OT security research corpus. No competitor currently occupies this space. B&M engineering credentials and OT operational knowledge are the natural moat.

**Commercial:** Assessment engagement is billable consulting. Repeat assessments at the same client are a natural cadence (annual or after significant tool changes). Re-assessment upsell is built into the model.

**Build complexity:** MVF is a structured web application with a checklist engine and report generation. No external integrations required in Phase 1. Moderate complexity.

**Risk:** Rubric validity. Operationalization scoring is only useful if the dimensions and scale are calibrated correctly. SME review of the rubric before development is a hard dependency.

---

## Open Questions

1. Does the client share direct tool access for verification, or do we rely on self-report + interview? (Affects checklist design and time-on-site requirements.)
2. How do we handle multi-site clients — per-site assessment with rollup, or single-site scope in MVF?
3. What is the handoff model between a completed OPRA engagement and follow-on implementation work?
4. Is there a natural re-assessment cadence to build into the commercial model (annual, post-incident, post-tool-change)?
5. Who owns the rubric internally — PM, practice lead, or a named SME from the OT security team?
