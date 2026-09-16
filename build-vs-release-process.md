# Build vs. Release Process: Brief and Suggested Evolutions

## Purpose

This brief defines the distinction between build and release: what each is, who owns it, and how a release ties back to roadmap items and sprint effort.

A set of suggested evolutions to the existing release process follows separately. Those are suggestions for how the process could support the model below, not part of the core proposal, and should be evaluated and decided on independently.

## The Build vs. Release Distinction

- **Build**: owned entirely by engineering. Cut whenever, no ceremony required. A minimum build cadence exists in practice already (nightly), which satisfies any minimum cadence a team would want. No cadence requirement needs to be pre-mandated; if cadence ever scales back, that is the trigger to revisit it.
- **Release**: a separate decision, owned by a small core group, independent/neutral manager, product, development lead, and a sales lead once staffed, with a customer-facing operations lead present in an advisory, non-voting capacity.
- A release is a curated bundle of one or more builds, selected because they deliver roadmap items or PRD features that are fully done, not a calendar event and not a size threshold. This is how a release ties back to the roadmap: each release names the roadmap item(s) it satisfies, and each roadmap item's status can be traced to the release that delivered it. The same logic ties a release to sprint effort: a sprint's completed work becomes build content; a release is declared once enough of that content, across one or more sprints, is fully done.
- Every release also declares an explicit **purpose and objective**: what it is meant to accomplish, not only which builds it bundles. Roadmap burn-down is one valid purpose, not the only one — a release can exist to prove something specific (a research/experimental pass, a release candidate validating a named handful of things) without checking off every item on the roadmap. The declared purpose determines which of the four release tiers (Internal, Preview, Beta, GA — see `delivery-and-distribution.md`) the release targets, and scopes what State 2 of the eligibility gate below needs to prove for that release specifically, rather than open-ended testing of everything that could be tested.
- What this protects against: code reaching production without the downstream work happening (documentation, support enablement, sales readiness, and where scoped, legal), not slow releases.

## Suggested Evolutions to the Release Process

The following are suggestions for how a release process could evolve to support the model above. They are not part of the build vs. release proposal itself; each should be evaluated and decided on independently.

1. **Release-eligibility gate**: a roadmap item or PRD feature must fully clear a three-state definition of done before it can be bundled into a release:
   - State 1: mechanical checks pass (build, QA, lint/tests)
   - State 2: evidence the feature was actually exercised against its written acceptance criteria, scoped to the release's declared purpose — a research or beta release names the specific handful of things it needs to prove, rather than requiring exhaustive testing of everything that could be tested
   - State 3: human review confirms intent and edge cases, not just that it runs

   This turns "have we moved the needle enough" from a judgment call into a checkable fact. The readiness-review group still decides timing and packaging, but decides on top of a fact, not a feeling.
2. **Per-build manifest**: every build produces a structured record of what it contains, using a release-notes format (Security / Added / Changed / Fixed / Internal, ticket-linked), instead of requiring anyone to read source control directly. This replaces having to read commit history directly to piece together what shipped.
3. **Versioning**: what a version number should formally signal (breaking change, new capability, or fix) is an open item to address, not resolved as part of this proposal. See Open Items below.
4. **Roadmap and changelog kept as two distinct, linked artifacts**: the roadmap/PRD is the forward-looking list of what's planned; the changelog/release notes is the backward-looking record of what shipped, linked back to the roadmap item it satisfies. This also gives a way to confirm every intended roadmap item is eventually addressed, either shipped and reflected in a changelog entry, or explicitly marked as not proceeding, so nothing goes silently missing between the two.
5. **Risk-based tiering**, in addition to audience-based tiering: classify by blast radius (security fix, new feature, breaking change) as well as by audience (internal/dev-facing vs. customer-facing). Both dimensions determine how much ceremony a release needs.
6. **Immutable artifact identity and promotion, at two levels**:
   - **Build-level**: each build is captured once with a fixed identity (a version or hash) and promoted unchanged through stage, rather than rebuilt.
   - **Release-level**: a release is not just a pointer to which builds it bundles. Everything that makes up the release, the code from every constituent build plus all accompanying documentation, training materials, and updated process artifacts, collapses into its own single immutable identity, its own hash. The release artifact is the complete, addressable sum of everything that shipped with it, not the code alone.

   This is the technical foundation that versioning (item 3) and rollback (item 7) depend on. It requires an engineering pipeline change; that cost does not make it optional; it is foundational to answering "what exactly is running for this customer," for the code and everything delivered alongside it.
7. **Rollback process**, built on that same artifact identity: rollback means re-promoting the last known-good artifact, not an improvised recovery under pressure. Needs a defined process and a named owner.

Items 6 and 7 are coupled (rollback needs an addressable artifact to roll back to) and should be built together. That is a dependency, not a deferral.

### Deferred Suggestions

- **Feature flags / dark launches**: appropriate once volume and customer count grow; not deferred because it is hard, deferred because it does not solve a real problem yet at low scale.
- **Canary / progressive rollout**: appropriate once there is more than one distribution channel and rollback exists. At low scale, a single distribution channel with a solid rollback plan can substitute.

### Complementary, Does Not Block the Above

- **DORA measurement**: a set of four measurements, from Google's DevOps Research and Assessment group (the book *Accelerate*), that reliably separate high-performing engineering organizations from low-performing ones:
  1. **Deployment frequency**: how often the team actually ships to production.
  2. **Lead time for changes**: how long from a commit being written to it running in production.
  3. **Change failure rate**: what percentage of shipped changes cause a problem in production.
  4. **Time to restore**: when something does break, how fast the team recovers.

  These measure the health and speed of the delivery pipeline itself, not whether a given release is warranted, that question is answered by the release-eligibility gate above. DORA is useful for validating or tuning practices like build cadence over time, once there is enough deployment history to measure against, but it should not hold up anything above.

## Open Items Requiring a Decision

1. Named owner for the rollback process.
2. Confirmation of current branching practice with engineering.
3. Exact composition and voting rule for the release-readiness group.
4. What a version number should formally signal, semantic versioning conventions not yet formalized.
5. Terminology for release purpose (research, beta/release-candidate, internal production, customer-ready) is not yet agreed across the team. Labeling a release "research" or "experimental" may carry commercial or licensing implications (e.g., customer/entitlement counting) that need legal or commercial input before the terms are formalized.

## Relationship to Delivery and Distribution

This document covers the build-to-release decision, what happens before a release candidate exists. `delivery-and-distribution.md` (Stages 5 to 6) picks up once development is complete and a release candidate is ready to be assessed, staged, and distributed. This document is the piece that precedes it. The four release tiers a release's declared purpose maps to (Internal, Preview, Beta, GA) are defined there, not duplicated here.

## References

- Artifact Promotion Best Practices for Reliable CI/CD, https://www.devopsness.com/blog/artifact-promotion-instead-of-rebuilds-the-release-control-pattern-that-stopped-drift-2026-03-26
- Immutable Artifacts, MinimumCD Practice Guide, https://beyond.minimumcd.org/docs/reference/practices/immutable-artifacts/
- DORA, four keys, https://dora.dev/guides/dora-metrics-four-keys/
- How to Use Feature Flags for Trunk-Based Development, Flagsmith, https://www.flagsmith.com/blog/trunk-based-development-feature-flags
- Using Semantic Versioning to Simplify Release Management, AWS, https://aws.amazon.com/blogs/devops/using-semantic-versioning-to-simplify-release-management/
- Keep a Changelog, Quackback, https://quackback.io/blog/keep-a-changelog
- Release Readiness Checklist, TQ Systems, https://www.tqsystems.io/blog/release-readiness-checklist
- Definition of Done for AI-Generated Code: The Three States, Shiplight AI, https://www.shiplight.ai/blog/definition-of-done-ai-generated-code
