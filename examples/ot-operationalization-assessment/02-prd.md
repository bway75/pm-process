# PRD — OT Program Readiness Assessment Platform (OPRA)

**PRD ID:** PRD-001  
**Version:** 0.1  
**Status:** Draft — pending Dev handoff  
**PM:** [name]  
**Date:** 2026-05

---

## 1. Problem / Why

Organizations purchase OT security tools and fail to operationalize them. Fewer than 10% of OT networks are meaningfully monitored despite significant tool investment. The failure mode is operational: tools installed but not configured for the site environment, no staff trained to review output, no process for acting on findings, no integration with adjacent systems.

Security vendors have a commercial conflict in addressing this — they sell tools, not tool activation. No commercial product or service currently addresses operationalization as a structured, measurable offering.

1898 & Co. has OT engineering credentials and no tool-vendor revenue model. The opportunity is a platform-backed assessment service that converts this position into a repeatable delivery capability.

---

## 2. Context & Objectives

**Why now:** The operationalization gap is the highest-confidence finding from the 27-track B&M OT security research corpus (2025–2026). Federal corroboration (CISA August 2025, co-authored with four named US critical infrastructure operators) and independent survey data (SANS/Claroty 2025, n=330) provide the anchoring evidence. No competitor has moved into this space.

**MVF objective:** 1898 engagement teams can run a complete operationalization assessment using the platform and deliver a scored, client-ready gap report.

**Measurable MVF outcomes:**
- 2 live client assessments run within 90 days of launch
- Engagement time from kickoff to delivered report ≤ 3 weeks
- Zero manual reformatting required: report is client-ready on export

**Non-goals (MVF):**
- Client self-service portal — clients receive the deliverable; they do not log in
- API ingestion from tool vendors (Dragos, Claroty, Nozomi) — all input is manual in Phase 1
- Cross-engagement benchmarking — Phase 2
- Multi-site rollup within a single engagement

---

## 3. Target Users & Use Cases

**Primary — 1898 Engagement Lead**
- Role: manages client relationship, runs the assessment, delivers the report
- Use case: create an engagement, input tool inventory, complete checklists, generate and export the client report — end to end in ≤ 3 weeks of elapsed time, ≤ 4 hours of active platform time

**Secondary — 1898 Practice Lead**
- Role: quality review across all engagements; not an engagement operator
- Use case: view all active and completed engagements; open any engagement to review inputs and scores; confirm consistent quality before client delivery

**MVF excludes:**
- Client users — no client-facing access
- Concurrent multi-user editing within a single engagement
- Engineering team — not a platform user

---

## 4. Core Functionality

### What it Eats

| Input | Source | Required |
|---|---|---|
| Engagement metadata | Engagement Lead entry | Yes |
| Tool inventory | Engagement Lead entry (manual) | Yes — min 1 tool |
| Checklist responses | Engagement Lead entry — 6 dimensions per tool | Yes — all tools must be complete before report |
| Root cause categories | Engagement Lead selection | Yes — required when dimension score < 2 |
| Report format selection | Engagement Lead at export | Yes |

**Engagement metadata fields:** Client name · Industry segment · Site name · Engagement lead (self) · Start date

**Tool inventory fields:** Tool name · Vendor · Category (passive detection / active scanning / SIEM / SOAR / asset management / other) · Installation status (installed / not installed) · License status (active / expired / unknown)

**Operationalization checklist — 6 dimensions per tool:**

| Dimension | What it evaluates |
|---|---|
| 1. Installation and connectivity | Tool deployed to relevant OT network segments; OT zones represented |
| 2. Configuration | Policies, rules, and thresholds configured for this site — not default/out-of-box |
| 3. Data completeness | Tool ingesting from the devices it should; coverage gaps documented |
| 4. Staff proficiency | Named owner exists; documented training or demonstrated proficiency on record |
| 5. Process integration | Documented process for reviewing tool output and acting on findings |
| 6. Lateral integration | Tool output connected to adjacent systems (SIEM, ticketing, response workflow) |

Each dimension: 0 = not met / 1 = partially met / 2 = met.

### What it Does

**Scoring:**
- Tool-level operationalization score = sum of 6 dimension scores / 12, expressed as percentage
- Score is calculated server-side; not directly editable
- Root cause categories aggregate to an engagement-level heat map by cause type (staffing / process / configuration / integration / licensing)

**Remediation roadmap generation:**
- Triggered after all tool checklists are marked complete
- Produces a sorted action list from low scores + root cause data
- Priority weighting: security consequence (detection-critical tools with low scores first) → effort (lower effort within same priority first)
- Each action: Tool + Dimension + Gap description + Recommended action + Effort estimate (S / M / L) + Priority (1–3)

**Engagement states:** Draft → Checklists complete → Roadmap generated → Exported

### What it Outputs

| Output | Audience | Format |
|---|---|---|
| Engagement dashboard | Engagement Lead, Practice Lead | Web UI |
| Per-tool scores | Engagement Lead, Practice Lead | Web UI |
| Root cause heat map | Engagement Lead, Practice Lead | Web UI |
| Remediation roadmap | Engagement Lead, Practice Lead | Web UI |
| Client gap report | Client (via Engagement Lead) | PDF + Word export |
| Engagement record | Practice Lead (all engagements) | Web UI |

**Client gap report contents:**
- Engagement summary (client, scope, date, engagement lead)
- Overall operationalization score
- Per-tool scored findings
- Root cause heat map (aggregated)
- Prioritized remediation roadmap

---

## 5. Architecture & Dependencies

**Components:**
- Web application — single-tenant in MVF (one org namespace; all 1898 users share a tenant)
- Checklist and scoring engine — server-side; scores are authoritative, derived from inputs, not manually entered
- Report generation — PDF and Word export from structured template
- Engagement storage — persistent; engagement records are not session-scoped

**Authentication and authorization:**
- 1898 internal users only in MVF
- Two roles: Engagement Lead (create / edit / generate within own engagements) and Practice Lead (view-all + approve)
- Engagement Leads cannot view other leads' client data

**Data handling:**
- Client tool inventory and security posture data is sensitive
- Auth-required access; no public indexing
- Hosted in B&M / 1898 managed environment — not public SaaS in MVF

**External dependencies (MVF):**
- None — all input is manual
- 1898 brand template required before report export feature is built (blocking dependency)
- Rubric SME sign-off required before dev starts (blocking dependency — see Section 6)

**Open question for Dev:**
- Report generation approach: server-side HTML → PDF (e.g., Puppeteer) vs document template library (e.g., docxtemplater) — preference is whichever produces clean Word output for client delivery without manual formatting correction

---

## 6. Delivery Phases & Scope

### Phase 1 — MVF

**Inclusions:**
- Engagement creation and metadata management
- Tool inventory input (manual form)
- Operationalization checklist — 6 dimensions per tool, 3-point scale
- Root cause capture per low-scoring dimension
- Automated scoring (server-side, percentage per tool)
- Root cause heat map (aggregated view)
- Remediation roadmap generation (sorted, prioritized)
- Client gap report export (PDF + Word) using 1898 template
- Practice lead review view (all engagements, read-only)

**Exclusions:**
- Client portal / client login
- API ingestion from tool vendors
- Cross-engagement analytics / benchmarking
- Multi-site rollup
- Mobile or offline use
- Concurrent multi-user editing

**Pre-dev dependencies (blocking):**
- Rubric SME review: operationalization dimensions and scoring scale reviewed by a named OT security SME before checklist is built
- Brand template: 1898 client report template finalized before report export is built
- Hosting environment: confirmed before deployment

**Risks:**
- Rubric validity: if dimensions are too generic, scores won't differentiate or be defensible to clients — SME pass is non-negotiable
- Adoption: engagement leads will revert to existing methods if the platform doesn't cover the full workflow — MVF must be end-to-end, not supplemental
- Scope creep: client portal and cross-engagement analytics are post-MVF; must not slip into Phase 1

### Phase 2 — Operationalization and validation (post-MVF)

- Re-assessment tracking: score-over-time view for repeat clients
- Cross-engagement aggregate view (practice lead only; no cross-lead client data)
- Report template improvements based on MVF feedback

### Phase 3 — Scale

- Client self-service: client inputs own inventory; engagement lead reviews and approves
- API ingestion: Dragos, Claroty, Nozomi asset/coverage data pull
- Cross-client benchmark dataset (aggregated, anonymized)

---

## 7. Risks, Metrics & Success

**Risks:**
- **Rubric validity** — operationalization scoring is only defensible if dimensions are calibrated by OT practitioners; SME review is a blocking pre-dev dependency
- **Report quality** — client-facing deliverable must meet 1898 standards; brand/template alignment must be completed before the export feature is built
- **Data security** — client tool inventory is sensitive; auth and access controls are blocking requirements, not post-launch hardening

**Metrics (MVF):**
- 2 completed client engagements within 90 days of launch
- Engagement time: kickoff to delivered report ≤ 3 weeks
- Active platform time per engagement ≤ 4 hours
- Zero manual report editing required post-export

**Success criteria (testable):**
- An engagement lead with no prior training completes a full assessment and generates a report in ≤ 4 hours of active platform time
- A practice lead can review all active engagements in a single view without opening individual records
- Generated report passes a 1898 client delivery review without manual editing
- Scores are reproducible: two engagement leads assessing the same inputs produce the same score

---

## Appendix A — Research Background

The operationalization gap is the highest-confidence finding from the B&M OT security research corpus. The <10% monitoring figure is federally corroborated (CISA August 2025 guidance co-authored with American Water, BP, Duke Energy, Southern California Edison) and independently confirmed by SANS/Claroty 2025 survey data (n=330). Root-cause structure (staffing, process, configuration, integration) is derived from the Competitive Analysis track findings across 20 OT security vendor profiles and from the managed-ot-security and it-soc-lens tracks. Full evidence chain in `ot-security-l4-convergence-brief-v2.md`, Section E, Target 2.

---

## Open Questions

1. Report export: PDF-only sufficient for MVF, or is Word required from day one? (Affects report generation approach.)
2. Single-tenant assumption: is the intent one 1898-wide deployment, or should engagements be namespace-isolated by practice area?
3. Rubric SME: who is the named reviewer — PM, practice lead, or a named OT security SME?
