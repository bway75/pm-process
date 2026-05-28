# User Stories — OPRA Platform MVF

**PRD reference:** PRD-001  
**Version:** 0.1  
**Scope:** Phase 1 (MVF) only

---

## Personas

| ID | Persona | Role |
|---|---|---|
| P1 | Engagement Lead | 1898 consultant running a client assessment |
| P2 | Practice Lead | 1898 senior reviewer overseeing all engagements |

---

## US-001 — Create New Engagement

**Persona:** P1 — Engagement Lead  
**Story:** When I start a new client project, I want to create a new engagement record, so that all assessment work for that client is organized in one place.

**Inputs:**
- Client name (required)
- Industry segment (required — selection from defined list: electric utility / oil & gas / water & wastewater / manufacturing / other)
- Site name (required)
- Start date (required)
- Engagement lead auto-set to logged-in user

**Outputs:**
- New engagement record in Draft state
- Engagement visible to the creating engagement lead and to all Practice Leads
- Tool inventory section available and empty

**Acceptance criteria:**
- All required fields enforced before engagement is saved
- Engagement created in Draft state; report generation blocked until all checklists are complete
- Duplicate engagement names for the same client surface a warning (not a hard block)
- Practice Lead sees new engagement in the all-engagements view immediately on creation

**PRD ref:** Section 4 (engagement metadata), Section 3 (users)

---

## US-002 — Add Tool to Inventory

**Persona:** P1 — Engagement Lead  
**Story:** When I am capturing what security tools a client has, I want to add each tool to the engagement inventory, so that the assessment covers their full environment.

**Inputs:**
- Tool name (required, free text)
- Vendor (required, free text)
- Category (required — selection: passive detection / active scanning / SIEM / SOAR / asset management / other)
- Installation status (required — selection: installed / not installed)
- License status (required — selection: active / expired / unknown)

**Outputs:**
- Tool added to engagement inventory
- Operationalization checklist for that tool becomes available
- Tool displayed in inventory list with installation and license status visible

**Acceptance criteria:**
- All required fields enforced before tool is saved
- Category list matches the defined taxonomy exactly
- Tools can be added, edited, or removed while engagement is in Draft state
- Removing a tool also removes its associated checklist data; confirmation required before deletion
- No minimum tool count enforced at add time; minimum of 1 required before checklist can be started (enforced at the checklist step, not here)

**PRD ref:** Section 4 (tool inventory)

---

## US-003 — Complete Operationalization Checklist for a Tool

**Persona:** P1 — Engagement Lead  
**Story:** When I am assessing a specific tool's operationalization, I want to complete a structured checklist for that tool, so that the scoring is consistent across all tools and all engagements.

**Inputs (per tool, per dimension — 6 dimensions):**
- Score: 0 (not met) / 1 (partially met) / 2 (met)
- Root cause category (required when score < 2): staffing gap / process gap / configuration gap / integration gap / licensing gap
- Notes (optional, free text)

**Outputs:**
- Tool-level operationalization score calculated and stored (sum of 6 dimension scores / 12, expressed as percentage)
- Root cause categories recorded and available for heat map aggregation
- Tool checklist status updated: Incomplete → Complete

**Acceptance criteria:**
- All 6 dimensions must be scored before the tool checklist is marked Complete
- Root cause field is required when any dimension score is 0 or 1; checklist cannot be marked Complete without it
- Score is calculated server-side from dimension inputs; no direct score editing
- Partial saves allowed — engagement lead can save progress and return to an incomplete checklist
- Completed tool checklists can be re-opened and revised while engagement is in Draft state; score recalculates on save
- Completed tool checklists cannot be edited after engagement state advances to Roadmap Generated

**PRD ref:** Section 4 (checklist and scoring)

---

## US-004 — View Engagement Scoring Summary

**Persona:** P1 — Engagement Lead  
**Story:** When all tool checklists are complete, I want to see a summary of scores and root causes, so that I can confirm the data before generating the roadmap.

**Inputs:**
- Completed checklist data (all tools, all dimensions)

**Outputs:**
- Per-tool operationalization score displayed as percentage and as a visual indicator (color-coded: < 40% red / 40–70% amber / > 70% green)
- Root cause heat map: count of gaps by cause category across all tools
- Overall engagement operationalization score (average across all tools)

**Acceptance criteria:**
- Summary view requires all tool checklists to be Complete; blocked if any checklist is Incomplete
- Color thresholds applied consistently: < 40% = red, 40–70% = amber, > 70% = green
- Root cause heat map shows absolute count by category (e.g., staffing gap: 7, process gap: 4)
- Engagement lead can navigate from summary view to any individual tool checklist to review or revise

**PRD ref:** Section 4 (scoring, heat map)

---

## US-005 — Generate Remediation Roadmap

**Persona:** P1 — Engagement Lead  
**Story:** When I have reviewed the scoring summary, I want to generate a prioritized remediation roadmap, so that the client has a concrete action plan.

**Inputs:**
- Completed checklist data (all tools, all dimensions, all root causes) — generated from stored data; no additional input required

**Outputs:**
- Sorted action list: one action per dimension gap (score < 2)
- Each action: Tool name · Dimension · Gap description (auto-generated from dimension + root cause) · Recommended action (auto-generated) · Effort estimate (S / M / L) · Priority (1–3)
- Priority logic: Priority 1 = detection-critical tool category (passive detection, SIEM, SOAR) with score < 40%; Priority 2 = all other tools with score < 40%, or detection-critical tools 40–70%; Priority 3 = all remaining gaps

**Acceptance criteria:**
- Generation blocked until all tool checklists are Complete
- Roadmap contains one action row per dimension with score < 2 (dimensions scoring 2 do not generate an action)
- Priority sorting applied correctly and consistently
- Within the same priority tier, lower-effort actions (S before M, M before L) appear first
- Engagement lead can review the roadmap before advancing to export
- Roadmap can be regenerated if checklist inputs are revised (engagement state returns to Checklists Complete)

**PRD ref:** Section 4 (roadmap generation), Section 6 (MVF inclusions)

---

## US-006 — Export Client Gap Report

**Persona:** P1 — Engagement Lead  
**Story:** When the assessment is complete and the roadmap looks correct, I want to export a client-ready gap report, so that I can deliver it without any manual reformatting.

**Inputs:**
- Engagement in Roadmap Generated state (all checklists complete, roadmap generated)
- Format selection: PDF or Word

**Outputs:**
- Formatted report file using 1898 brand template, containing:
  - Engagement summary (client, site, industry, date, engagement lead name)
  - Overall operationalization score
  - Per-tool scored findings with dimension breakdown
  - Root cause heat map
  - Prioritized remediation roadmap
- Export logged with timestamp and format in engagement record

**Acceptance criteria:**
- Export only available when engagement is in Roadmap Generated state; blocked otherwise
- Both PDF and Word formats available and selectable
- Report uses the approved 1898 brand template (colors, fonts, logo, footer)
- No manual editing required: content, layout, and branding complete on export
- Exported file contains all roadmap actions in priority order as they appear in the platform
- Export action creates an immutable record (engagement moves to Exported state; further edits require re-generating the roadmap and re-exporting)

**PRD ref:** Section 4 (outputs), Section 7 (success criteria: zero manual reformatting)

---

## US-007 — Practice Lead: Review All Engagements

**Persona:** P2 — Practice Lead  
**Story:** When I want to ensure consistent quality across all OPRA engagements, I want to see all active and completed engagements in one view, so that I can review findings before client delivery.

**Inputs:**
- No additional input — view auto-populated from all engagement records

**Outputs:**
- Engagement list with: Client name · Engagement lead · Status · Overall operationalization score · Date created · Date exported (if applicable)
- Ability to open any engagement and view all checklist inputs, scores, heat map, and roadmap

**Acceptance criteria:**
- All engagements visible to Practice Lead regardless of which engagement lead created them
- Engagement Lead cannot view another Engagement Lead's client data (role enforcement: engagement leads see only their own engagements)
- Practice Lead can open any engagement in read-only mode; they cannot edit checklist data
- Engagement list sortable by: status / overall score (ascending or descending) / date created / engagement lead name
- No additional client data exposure: client name and score visible in list; full details only on open

**PRD ref:** Section 3 (Practice Lead), Section 5 (auth/roles)

---

## Development Readiness Check

Before picking up these stories, confirm the following are resolved:

| Item | Status |
|---|---|
| Rubric SME sign-off: 6 dimensions and 3-point scale reviewed by named OT security SME | Required before checklist is built |
| 1898 brand template: client report template finalized | Required before export is built |
| Hosting environment confirmed | Required before deployment |
| Report generation approach decided (PDF/Word): Puppeteer vs docxtemplater | Open — needs Dev input |
| Single-tenant vs namespace-isolated deployment | Open — needs PM + Dev decision |
