# 6-Pager — OT Security Operationalization Assessment (OPRA)

**Status:** Draft — pending evaluation  
**Author:** PM  
**Date:** 2026-05

---

## Introduction

Burns & McDonnell / 1898 & Co. has accumulated deep OT security research and engineering credentials. The opportunity in front of us is to convert that depth into a repeatable, commercial service offering.

The specific opportunity: helping OT asset owners operationalize the security tools they have already purchased but are not running. This is not a new problem and not a niche one — federal agencies, four major US critical infrastructure operators, and independent survey research all confirm the same finding. Tools are bought. Tools are not running. The gap is operational, not technical, and no current commercial offering is designed to close it.

This document makes the case for building a platform-backed assessment service — OPRA — and describes what it would look like, what it would cost us to build, and what it would return.

---

## Background

### The Problem

Fewer than 10% of OT networks are meaningfully monitored. This figure comes from CISA's August 2025 guidance, co-authored with American Water, BP, Duke Energy, and Southern California Edison. It is not a vendor estimate or a research projection — it is a federal multi-agency finding anchored to named critical infrastructure operators.

SANS and Claroty's 2025 survey (330 respondents) confirms the operational outcome: 57% of organizations have an incident response plan; 19% still take more than a month to remediate an OT incident. The plan exists. The capability does not.

The failure mode is not tools. It is operationalization. Organizations have purchased passive detection platforms, SIEMs, asset management tools. Those tools are installed and licensed. They are not:

- Configured for the specific OT environment (policies and thresholds are at default)
- Connected to the network segments they are meant to cover
- Staffed by someone with documented proficiency on the tool
- Integrated into a process — someone reviewing the output and doing something with it
- Connected to adjacent systems — no alert gets from the OT tool to a ticketing system or response workflow

### Why Vendors Can't Solve This

Security tool vendors have a structural conflict. Their commercial model depends on selling additional tools or expanding licenses. No vendor can build a product that maximizes operationalization of a competitor's platform — and the category problem (tools not running) implicates every vendor simultaneously, including their own. There is no product category here. It is a gap.

### Why 1898 Can

1898 is an engineering firm, not a security vendor. We have no tool-vendor revenue model. We can take an objective view of a client's existing environment and assess it honestly — without recommending new tools as the default answer.

More specifically: operationalizing OT security tools requires OT engineering knowledge. Understanding why a passive detection sensor is not covering the right network segments, or why alert logic is not calibrated for a specific industrial process, requires someone who understands the industrial environment. That is B&M's core competency. It is not a pure security firm's core competency.

We have a competitive position here that is structural, not marginal.

---

## Proposed Solution

A platform-backed assessment service delivered by 1898 engagement teams.

**The engagement model:** A 1898 consultant works with the client over 2–3 weeks. The platform provides structure — a consistent assessment framework — so every engagement produces a comparable, defensible output. The consultant provides interpretation — OT domain knowledge that converts checklist scores into meaningful guidance.

**What the platform does:**
The engagement lead inputs the client's tool inventory and completes a structured operationalization checklist for each tool across six dimensions: installation and connectivity, configuration, data completeness, staff proficiency, process integration, and lateral integration. Each dimension is scored on a three-point scale. The platform calculates a tool-level operationalization score, maps root causes by category, and generates a prioritized remediation roadmap.

**What the client receives:**
A scored gap report and prioritized remediation roadmap delivered as a branded 1898 document. The report shows the client exactly where their tools are and are not working, why, and what to fix first.

**What the platform is not (in Phase 1):**
Client-facing. Clients receive the deliverable; they do not log in. The platform is an internal tool that makes engagement delivery consistent and scalable.

---

## Customer Experience

### From the client's perspective

A VP of OT Security at a mid-sized utility has purchased three security platforms over the past 18 months: a passive detection tool, a SIEM fed from OT sources, and an asset management platform. None of them are producing the output she expected. The detection tool covers one of four production segments. The SIEM has OT alerts turned off because they generated too much noise during initial setup and no one reconfigured them. The asset management platform has 60% coverage because several legacy PLCs were not in the initial discovery scan scope.

She has brought this to her security vendor contacts. Each vendor points to a different cause and each suggests an additional product or service from their own portfolio.

She engages 1898. Over three weeks, an engagement lead works through a structured assessment of all three tools. The output is a scored gap report: each tool is scored on six dimensions, each gap has an identified root cause, and a prioritized roadmap tells her which six actions — in which order — will deliver the most improvement for the least effort.

She knows what to fix. She has a document she can share with her CFO to justify the remediation investment without buying a fourth tool.

### From the engagement lead's perspective

Before OPRA, an engagement lead running a tool assessment worked from a custom spreadsheet or document template. The output varied by engagement lead. There was no consistent scoring model, and generating a client-ready report required significant reformatting effort after the assessment.

With OPRA, the engagement lead works through a structured checklist in the platform. Scoring is automatic. The heat map and roadmap are generated from the input data. The client report exports directly from the platform using the 1898 template. The engagement lead's time goes to interpretation and client relationship — not to spreadsheet maintenance and document formatting.

---

## Business Case

### Revenue model

OPRA is a billable consulting engagement. Initial assessment engagement: estimated 2–3 weeks of consultant time at standard 1898 rates. Re-assessment engagements (same client, subsequent year or post-change) are a natural upsell at reduced scope and time.

**Indicative economics (one engagement):**
- 3-week engagement at typical 1898 consulting rates = significant billable revenue
- Platform cost amortizes across engagements — per-engagement marginal cost is low once built
- Re-assessment cadence (annual or event-driven) creates recurring revenue per client

### Market size

The operationalization gap affects every sector where OT security tools have been deployed: electric utilities, oil and gas, water and wastewater, manufacturing. The CISA/SANS data confirms this is not a single-sector problem. B&M / 1898 already has client relationships across these sectors.

### Differentiation

No competitor currently offers a structured, platform-backed operationalization assessment. Pure security consultancies focus on posture assessment, compliance gaps, or tool implementation — not tool activation. Tool vendors have the conflict described above. The gap is open.

### Long-term value

Phase 3 of the roadmap includes a cross-client benchmark dataset. After a sufficient number of engagements, 1898 holds aggregated operationalization data across sectors, tool categories, and organization sizes — data that no single client and no vendor can produce. This is a differentiated insight asset that enables new service offerings and strengthens the OPRA brand.

---

## Risks and Concerns

**Rubric validity.** The operationalization scoring dimensions and scale must be reviewed by a named OT security SME before development begins. If the rubric is too generic or miscalibrated, scores will not be defensible to clients and the platform's value proposition collapses. This is the highest-priority pre-development risk.

**Engagement adoption.** If OPRA does not cover the full engagement workflow end-to-end, engagement leads will use it as a supplemental data entry tool alongside their existing methods — which means the consistency benefit is lost and the platform adds overhead rather than removing it. MVF must be complete enough to replace existing methods entirely.

**Report quality.** The client deliverable is a 1898-branded document. If it does not meet the firm's client delivery standards, it creates a brand risk rather than a brand benefit. The 1898 report template must be finalized and approved before the export feature is built.

**Scope discipline.** Client portal, API ingestion, and cross-engagement analytics are post-MVF. There will be pressure to include them early. They must stay out of Phase 1.

---

## Open Questions

1. Who is the named OT security SME responsible for rubric review and sign-off before development begins?
2. Does the client provide direct tool access for verification, or do we rely on self-report plus interview? This affects checklist design and on-site time estimates.
3. What is the commercial model for re-assessments — a separate engagement, a retainer, or a subscription?
4. Are there existing 1898 client relationships where an OPRA pilot engagement is feasible within 90 days of MVP launch?
5. Who owns the OPRA service offering commercially — which practice or individual is the internal champion?
6. Report export: is Word output required from day one, or is PDF sufficient for the first pilot engagements?
