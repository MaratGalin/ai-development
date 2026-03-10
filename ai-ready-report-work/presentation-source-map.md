# AI-Ready Presentation Source Map

Purpose: trace each core slide to the report, transcript notes, and relevant visual anchors. The report remains the primary source of truth. Transcript references are secondary and used where they sharpen framing, visual reading, or concrete examples.

## Slide 1. AI-Ready Codebase: not about the model, about the environment
- **Core claim:** Leadership should approve a Year-1 AI-ready rollout because environment quality, not raw model quality, determines scalable results.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:36` Executive Summary
  - `ai-ready-codebase-report.md:41` Opportunity
  - `ai-ready-codebase-report.md:51` Action Plan
  - `ai-ready-codebase-report.md:61` Key Decisions to Make
  - `ai-ready-codebase-report.md:247` Harness Engineering as working concept
- **Transcript refs:** none required; report already carries the executive framing.
- **Relevant visual references:** no required screenshot; simple decision contrast slide.

## Slide 2. What happens without preparation
- **Core claim:** Unprepared codebases force agents into search, drift, and wasted context before useful execution begins.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:332` What is AI-Ready Codebase
  - `ai-ready-codebase-report.md:349` 7 key characteristics
  - `ai-ready-codebase-report.md:431` Why this is a system approach, not just tests
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:52` 21:04 task explanation failure
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:56` 21:50 exploration/search path in-project
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:60` 22:49 context fill
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:82` 28:50 consequences of compaction in unprepared projects
- **Relevant visual references:** user-provided visual in session for the no-prep path.

## Slide 3. What changes after preparation
- **Core claim:** Preparation shifts work from wandering to execution by giving agents structure, navigation, and bounded tasks.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:336` AI-ready definition
  - `ai-ready-codebase-report.md:349` checklist signals
  - `ai-ready-codebase-report.md:247` harness composition
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:87` 29:49 project preparation
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:92` 31:46 hierarchical structure benefit
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:139` 45:49 navigation need as size signal
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:149` 47:26 navigation useful even in smaller projects
- **Relevant visual references:** user-provided visual in session comparing unprepared vs prepared path.

## Slide 4. Why long context does not save us: attention limits
- **Core claim:** Bigger context windows do not remove the scarcity of attention or the degradation caused by repeated compaction.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:455` architecture/context limit framing
  - `ai-ready-codebase-report.md:627` documentation as working guidance, not context dump
  - `ai-ready-codebase-report.md:690` context engineering and context packing
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:60` 22:49 filling context lowers quality
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:64` 24:44 compaction loss
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:68` 26:35 repeated compaction degradation
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:173` 56:17 attention as stretched resource
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:178` 57:04 attention limits
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:183` 58:45 memory limitation
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:187` 59:15 decomposition and complexity
- **Relevant visual references:** user-provided visual in session for attention spread / compaction / free context capacity.

## Slide 5. Dynamic Context Layer
- **Core claim:** Task-aware context assembly beats repository dumping because it selects relevant files, constraints, and checks per task.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:623` Documentation: AGENTS.md, Context and Dual Audience Design
  - `ai-ready-codebase-report.md:690` context packing
  - `ai-ready-codebase-report.md:838` minimum documentation set
  - `ai-ready-codebase-report.md:865` minimum required documentation decision
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:102` 33:42 context-as-a-service mention
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:105` 34:08 project indexing and dynamic context formation
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:115` 36:35 context engines and ontology/index refresh
- **Relevant visual references:** user-provided visual in session for context engine / context-as-a-service.

## Slide 6. Before coding: crowding, decomposition, scoping
- **Core claim:** Agents need pre-coding discipline so they work on small, locally coherent, bounded changes.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:1023` evolution from chat to agents
  - `ai-ready-codebase-report.md:1069` Addy Osmani workflow
  - `ai-ready-codebase-report.md:1099` humans steer, agents execute
  - `ai-ready-codebase-report.md:1117` practices to standardize
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:154` 48:27 planning/spec review before coding
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:159` 51:39 crowding
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:164` 54:00 task дробление / decomposition
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:187` 59:15 complexity reduction via decomposition
- **Relevant visual references:** optional simple workflow diagram; no file-backed visual required.

## Slide 7. What must actually be built in the project
- **Core claim:** AI-readiness is a concrete asset stack: project maps, glossary, rules, ADR access, verification entry points, and guardrails.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:349` 7 key characteristics
  - `ai-ready-codebase-report.md:623` documentation section
  - `ai-ready-codebase-report.md:838` minimum documentation set
  - `ai-ready-codebase-report.md:878` engineering guardrails
  - `ai-ready-codebase-report.md:1008` which guardrails to implement first
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:87` 29:49 map plus glossary
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:320` 01:35:07 progressive documentation hierarchy
- **Relevant visual references:** inventory-style slide; no fixed screenshot needed.

## Slide 8. AI-ready architecture: module boundaries and external contracts
- **Core claim:** Bounded modules and explicit contracts reduce blast radius and make autonomous changes verifiable.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:453` Architecture: Vertical Slices and AI-Friendly Patterns
  - `ai-ready-codebase-report.md:459` why architecture determines AI result
  - `ai-ready-codebase-report.md:473` architecture comparison
  - `ai-ready-codebase-report.md:491` why vertical slice usually wins
  - `ai-ready-codebase-report.md:578` caveats
  - `ai-ready-codebase-report.md:610` migration decision
  - `ai-ready-codebase-report.md:959` structural tests
  - `ai-ready-codebase-report.md:1155` governance, merge policy, blast radius
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:387` 01:56:54 boundaries and contracts matter more than local code beauty
- **Relevant visual references:** user-provided visual in session if a boundary/contract diagram was shown; otherwise use an abstract module-boundary diagram.

## Slide 9. Project ontology and domain graphs
- **Core claim:** Agents need a semantic map of domain terms, entities, and relationships, not just file paths.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:744` dual audience design
  - `ai-ready-codebase-report.md:761` what it gives in practice
  - `ai-ready-codebase-report.md:828` domain glossary reference
  - `ai-ready-codebase-report.md:842` minimum documentation set including ADR/docs foundation
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:210` 01:05:26 glossary
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:214` 01:06:18 ontology graph
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:219` 01:08:04 expert-time and practical limits
- **Relevant visual references:** user-provided visual in session for ontology or domain graph.

## Slide 10. Memoberry Bank: documentation as a navigation system
- **Core claim:** Documentation should route the agent through the system via progressive disclosure rather than act as a flat knowledge dump.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:623` documentation section opening
  - `ai-ready-codebase-report.md:633` what AGENTS.md is
  - `ai-ready-codebase-report.md:645` less but more precise
  - `ai-ready-codebase-report.md:744` dual audience design
  - `ai-ready-codebase-report.md:767` practical AGENTS.md template
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:320` 01:35:07 Memoberry Bank and progressive disclosure
- **Relevant visual references:** user-provided visual in session for Memoberry-style hierarchy.

## Slide 11. Documentation lifecycle and ADR lifecycle
- **Core claim:** Documentation becomes trustworthy only when freshness, ADR maintenance, and source-of-truth consolidation are operational duties.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:724` ADR rationale
  - `ai-ready-codebase-report.md:735` practical value of ADR
  - `ai-ready-codebase-report.md:831` how to keep documentation alive
  - `ai-ready-codebase-report.md:860` minimum documentation decision
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:359` 01:47:56 documentation hygiene
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:364` 01:49:40 source-of-truth conclusion
- **Relevant visual references:** user-provided visual in session if lifecycle loop was shown; otherwise a simple loop diagram.

## Slide 12. Verification is the bridge to autonomy
- **Core claim:** Autonomy should rise only where tests, type checks, linting, CI, review, and approval boundaries prove that the blast radius is controlled.
- **Primary report refs:**
  - `ai-ready-codebase-report.md:878` guardrails section
  - `ai-ready-codebase-report.md:890` minimum guardrails
  - `ai-ready-codebase-report.md:970` code review for AI-generated code
  - `ai-ready-codebase-report.md:1190` Year-1 mode decision
  - `ai-ready-codebase-report.md:1434` implementation roadmap
  - `ai-ready-codebase-report.md:1721` metrics and KPI
  - `ai-ready-codebase-report.md:1956` phase thresholds
  - `ai-ready-codebase-report.md:2036` risks and mitigation
  - `ai-ready-codebase-report.md:2226` risk decision
  - `ai-ready-codebase-report.md:2248` self-hosted tools: comparison and recommendations
- **Transcript refs:**
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:228` 01:09:29 tests as bridge to autonomy
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:233` 01:11:08 verification stack
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:243` 01:12:59 task classes for agents
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:248` 01:14:34 red-line restrictions
  - `../.sisyphus/drafts/ai-ready-video-transcript.md:277` 01:21:15 readiness profile and staged autonomy
- **Relevant visual references:** user-provided visual in session for autonomy ladder if shown; otherwise simple verification-to-autonomy ladder.

## Mapping Rules
- Every slide keeps at least one primary report source; transcript notes are supporting evidence only.
- Use “user-provided visual in session” when speaker notes rely on screenshots or diagrams that are not stored in the workspace.
- If a slide gains extra appendix backup later, keep the core source map unchanged unless the slide thesis changes.
