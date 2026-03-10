---
marp: true
theme: default
paginate: true
title: AI-Ready Codebase
description: Leadership deck on funding an AI-ready engineering environment
---

# AI-Ready Codebase: not about the model, about the environment

- Same model quality, very different delivery outcomes
- Ad hoc AI use scales tool access, not delivery reliability
- Recommendation: fund a Year 1 rollout with baselines, guardrails, a limited pilot, and self-hosted constraints

**Takeaway:** Approve the environment now, before uncontrolled usage becomes the default.

---

# What happens without preparation

- Agents lose time to search, re-reading, and guesswork
- Context fills with exploration before useful execution begins
- Output looks fast at first, then turns into rework and fragile changes
- Visual: user-provided visual in session

**Takeaway:** Unprepared adoption creates hidden cost and unstable quality.

---

# What changes after preparation

- Clear entry points reduce unnecessary codebase traversal
- Bounded tasks shift effort from exploration to execution
- Shared guidance improves first-pass accuracy and predictability
- Visual: user-provided visual in session

**Takeaway:** Preparation is the multiplier that turns model capability into dependable delivery.

---

# Why long context does not save us: attention limits

- Bigger context windows add storage, not reliable working attention
- Attention still stretches across the full prompt
- Repeated compaction drops fidelity over long sessions
- Visual: user-provided visual in session

**Takeaway:** We need to protect scarce attention, not just buy bigger prompts.

---

# Dynamic Context Layer

- Assemble task-relevant files, docs, contracts, and checks on demand
- Preserve working room for reasoning and execution
- Make context a retrieval and composition capability, not a repository dump
- Visual: user-provided visual in session

**Takeaway:** The key systems investment is task-aware context assembly.

---

# Before coding: crowding, decomposition, scoping

- Crowding checks local fit and nearby constraints
- Decomposition keeps work small enough to stay coherent
- Scoping defines what the agent may touch, and what stays off-limits
- Visual: simple pre-coding workflow

**Takeaway:** Planning discipline is part of the control system.

---

# What must actually be built in the project

- Navigation assets: project maps, module guidance, run commands
- Knowledge assets: glossary, ADR access, domain graphs
- Control assets: guardrails, verification entry points, no-go zones

**Takeaway:** Approval is for a bounded infrastructure package, not abstract AI experimentation.

---

# AI-ready architecture: module boundaries and external contracts

- Bounded modules keep changes local and blast radius small
- Explicit contracts define what must remain stable
- Structural rules in CI make those boundaries enforceable
- Visual: user-provided visual in session

**Takeaway:** Safe autonomy depends on clear edges and meaningful verification.

---

# Project ontology and domain graphs

- A shared glossary reduces ambiguity in business terms
- Domain graphs expose relationships the file tree can't show
- Expert knowledge becomes reusable system guidance
- Visual: user-provided visual in session

**Takeaway:** Domain modeling lowers semantic mistakes and search cost.

---

# Memoberry Bank: documentation as a navigation system

- Start with top-level orientation, then move into local detail
- Reveal module guidance only when the task needs it
- Keep context focused without losing access to depth
- Visual: user-provided visual in session

**Takeaway:** Good docs route work through the system with less noise and fewer wrong turns.

---

# Documentation lifecycle and ADR lifecycle

- Stale guidance misleads agents faster than missing guidance
- Update docs and ADRs on architecture change, repeated mistakes, and rollout learning
- Keep current rationale in one source of truth
- Visual: user-provided visual in session

**Takeaway:** Documentation freshness is an operating responsibility.

---

# Verification is the bridge to autonomy

- Raise autonomy only behind tests, linting, types, structural rules, and review
- Keep approval boundaries for external APIs, destructive actions, deploys, data migrations, and secrets
- Year 1 ask: baseline measurement, one limited pilot, enforced guardrails, Dynamic Context infrastructure, self-hosted constraints
- Visual: user-provided visual in session

**Takeaway:** Fund a staged rollout where trust grows only behind proof.

---

# Appendix 1. Why not just use stronger models and larger context?

- Model quality is no longer the main bottleneck in large projects
- Long context adds storage, but attention and compaction limits remain
- Better navigation and task shaping cut waste more reliably than prompt expansion
- Visuals: user-provided visual in session, no-prep vs prepared path; user-provided visual in session, attention and compaction limits

---

# Appendix 2. Is self-hosted deployment practical enough for Year 1?

- Treat self-hosted constraints as a design boundary from day one
- Match pilot scope to infrastructure maturity, GPU envelope, and integration surface
- Central policy and approved tool paths matter more than maximum feature richness
- Caveats: licensing, compliance, and OSS maintenance risk

---

# Appendix 3. Will architecture and documentation work become a costly side program?

- Start with the minimum scaffold, not a rewrite
- Build one obvious path, critical verification commands, AGENTS.md, and a small ADR base
- Prefer incremental vertical-slice adoption over full migration
- Use layered artifacts: project map, module guidance, glossary, contracts, ADR links, verification paths

---

# Appendix 4. Are contracts and module boundaries enforceable in a messy enterprise codebase?

- Contract-first discipline matters more than local elegance
- Public APIs and dependency rules can be enforced with CI and structural tests
- High-risk legacy zones should move in stages, not all at once
- Contract discipline supports approval boundaries and safer autonomy

---

# Appendix 5. How do we know the metrics are real and not vanity?

- Baseline measurement is mandatory before pilot claims
- Separate adoption, productivity, and outcome metrics
- Rework, defect leakage, review latency, and DORA-style outcomes matter more than raw PR count
- Metric ownership must be explicit to prevent gaming

---

# Appendix 6. What about regulated domains, sensitive changes, and rollout-risk control?

- Sensitive zones stay under tighter task classes and stronger review
- No silent changes to external APIs, secrets, deploys, destructive operations, or data migrations
- Pilot design should rehearse production governance, not just demo success
- Repeated failures should feed back into rules, tests, and documentation
