# AI-Ready Presentation Appendix Outline

Purpose: backup material for objections, caveats, and Q&A. This appendix is not a second core deck. It exists to deepen decision confidence when leaders challenge practicality, safety, rollout discipline, or measurement.

## Appendix 1. "Why not just use stronger models and larger context?"
- Rebuttal frame: model quality is no longer the main bottleneck; attention spread, compaction loss, and navigation cost remain.
- Backup points:
  - Long context increases available storage, not reliable working attention.
  - Repeated compaction degrades session fidelity on large projects.
  - Navigation and task shaping reduce waste more reliably than prompt expansion.
- Useful backup visuals:
  - user-provided visual in session showing no-prep vs prepared path
  - user-provided visual in session showing attention/compaction limits
- Suggested evidence:
  - Report: Executive Summary; What is AI-Ready Codebase; Architecture; Documentation and context engineering
  - Transcript: 22:49, 24:44, 26:35, 56:17, 57:04, 58:45, 59:15

## Appendix 2. "Is self-hosted deployment practical enough for Year 1?"
- Rebuttal frame: self-hosted constraint changes tooling choices and rollout speed, but it does not block a bounded pilot.
- Backup points:
  - Treat self-hosted as a design boundary from day one, not a late procurement issue.
  - Pilot scope should match available infrastructure maturity, GPU envelope, and integration surface.
  - Different tool classes carry different readiness, licensing, and maintenance trade-offs.
  - Centralized policy and approved tool paths matter more than maximizing feature richness.
- Caveats to hold in backup:
  - fully self-hosted inference vs enterprise-controlled hosted tools
  - licensing/compliance gates
  - maintenance risk for weakly supported OSS options
- Suggested evidence:
  - Report: Executive Summary constraint; Implementation Roadmap pilot prerequisites; Self-Hosted tools comparison and category recommendations; Risks on code leakage and licensing

## Appendix 3. "Will architecture and documentation work become a costly side program?"
- Rebuttal frame: the goal is not a documentation rewrite or architecture purity exercise; it is the minimum operational scaffolding that reduces blast radius and search cost.
- Backup points:
  - Start with one obvious way, critical verification commands, AGENTS.md, and a small ADR base.
  - Prefer incremental vertical-slice adoption over full migration.
  - Use artifact layering: project map, module guidance, glossary, contracts, ADR links, verification paths.
  - Documentation must stay compressed in the core deck and expand here only as templates, exceptions, and operating caveats.
- Backup subtopics:
  - ADR drift and source-of-truth consolidation
  - minimum viable documentation level vs over-documentation
  - practical vertical-slice caveats: shared kernels, performance-critical areas, legacy cores, platform-heavy zones
- Suggested evidence:
  - Report: Architecture decision and caveats; Documentation minimum level; ADR rationale; appendices for AGENTS.md and Vertical Slice structure
  - Transcript: 29:49, 31:46, 35:06, 01:35:07, 01:47:56, 01:49:40, 01:56:54

## Appendix 4. "Are contracts and module boundaries actually enforceable in a messy enterprise codebase?"
- Rebuttal frame: contract-first practicality matters more than local elegance because agents need stable edges and bounded change zones.
- Backup points:
  - Module boundaries reduce files-per-change and make verification meaningful.
  - Public API and dependency rules can be enforced through CI and structural tests.
  - Not every area should migrate at once; high-risk legacy and shared-kernel zones need staged handling.
  - Contract discipline is the basis for approval boundaries and safe autonomy.
- Backup subtopics:
  - when vertical slices should be partial, not universal
  - external contract protection vs internal refactoring freedom
  - structural tests as management control, not architecture theater
- Suggested evidence:
  - Report: Architecture sections on AI-friendly patterns, files-per-change, caveats, migration decision; Guardrails structural tests; Processes governance and blast radius
  - Transcript: 01:56:54

## Appendix 5. "How do we know the metrics are real and not vanity?"
- Rebuttal frame: output metrics alone are dangerous; Year 1 should be governed by baseline, comparable windows, and phase-specific thresholds.
- Backup points:
  - Separate adoption, productivity, and outcome metrics.
  - Baseline is mandatory before pilot claims.
  - Rework, defect leakage, review latency, and DORA-style outcomes matter more than raw PR count.
  - Metric ownership must be explicit to prevent local gaming.
- Backup subtopics:
  - metrics-by-phase thresholds
  - false-positive productivity patterns
  - dashboard/reporting template as appendix-only material
- Suggested evidence:
  - Report: Executive Summary action plan; Metrics and KPI rules, dashboard, phase thresholds, decision section; risk of misleading velocity without control

## Appendix 6. "What about regulated domains, sensitive changes, and rollout-risk control?"
- Rebuttal frame: the rollout should expand only where verification and approvals are strong enough; sensitive zones stay under tighter control.
- Backup points:
  - No silent changes to external APIs, secrets, deploys, destructive operations, or data migrations.
  - Regulated, privacy, cryptography, and authentication areas need stronger human review and narrower task classes.
  - Pilot design must rehearse production governance, not just demo success.
  - Repeated agent failures should feed back into rules, tests, and documentation updates.
- Backup subtopics:
  - regulated/high-risk repositories
  - human approval boundaries
  - risk acceptance vs risk-first mitigation order
  - why pilots fail to scale when governance is missing
- Suggested evidence:
  - Report: Paradox and root causes; Guardrails; Processes with AI; Risks and mitigation; roadmap phase gates; self-hosted perimeter constraints
  - Transcript: 01:09:29, 01:11:08, 01:12:59, 01:14:34, 01:17:25, 01:18:40, 01:19:30, 01:21:15

## Appendix Use Rules
- Use appendix only when an executive objection requires more proof, a caveat, or a decision boundary.
- Do not retell the 12-slide narrative in order.
- Prefer tables, thresholds, examples, and exception handling over repeated slide summaries.
- Keep formulas, comparison matrices, templates, and detailed caveats here unless they are essential to the core approval ask.
