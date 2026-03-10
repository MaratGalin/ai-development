# AI-Ready Presentation for Engineering Leaders

## TL;DR
> **Summary**: Create a new decision-oriented presentation that converts the completed AI-Ready report into a concise but technically credible deck for engineering leaders. The deck must drive one primary decision: approve a Year-1 AI-ready rollout built around baseline measurement, guardrails, a limited pilot, and self-hosted constraints.
> **Deliverables**:
> - Slide-by-slide outline for a 10-12 slide core deck
> - Speaker notes for every core slide
> - Optional backup appendix topics for objections and Q&A
> - Source mapping from each slide to report sections
> **Effort**: Short
> **Parallel**: YES - 2 waves
> **Critical Path**: Task 1 → Task 2 → Task 5 → Task 7 → F1-F4

## Context
### Original Request
Пользователь попросил изучить уже найденные материалы и составить презентацию.

### Interview Summary
- Формат: `executive deck`
- Аудитория: `engineering leaders`
- Цель: `decision memo`
- Deliverable: `slide outline + speaker notes`
- Уровень детализации: `technical-heavy`
- В workspace нет существующей презентации, deck нужно создавать с нуля
- Пользователь зафиксировал ключевые слайды: путь агента без подготовки, путь агента с подготовкой, context-as-a-service, внимание в нейросетях, роль краудинга/crowding, построение онтологии проекта, доменные графы с экспертами, документация по модели Memoberry Bank

### Metis Review (gaps addressed)
- Зафиксирован **один primary decision**, чтобы deck не стал пересказом всего отчёта
- Ограничен core deck: **10-12 slides**, остальное уходит в appendix
- Разделены **core narrative** и **technical appendix**, чтобы совместить executive flow и technical-heavy depth
- Исключены скрытые scope jumps: без визуального дизайна, без новой research-программы, без procurement deep dive
- Добавлены acceptance criteria для структуры deck, speaker notes и source mapping

## Work Objectives
### Core Objective
Подготовить decision-complete план создания новой презентации, которая на основе готового отчёта `ai-ready-codebase-report.md` приведёт engineering leadership к решению: запускать ли Year-1 AI-ready rollout с ограниченным pilot, обязательными guardrails, baseline metrics и perimeter-safe/self-hosted подходом.

### Deliverables
- `presentation-outline.md` — структурированный outline core deck
- `presentation-speaker-notes.md` — notes по каждому core slide
- `presentation-appendix-outline.md` — backup/appendix topics для objections, caveats и Q&A
- `presentation-source-map.md` — traceability: slide → report sections → supporting notes
- `presentation-visual-notes.md` — указания по использованию предоставленных диаграмм/скриншотов как visual anchors для ключевых слайдов

### Definition of Done (verifiable conditions with commands)
- [x] Core outline contains **10-12** slide sections
- [x] One slide explicitly states the **Primary Decision**
- [x] One slide explicitly states **Why now / why pilots fail to scale**
- [x] Core outline includes the user-requested comparison: **agent path without preparation vs with preparation**
- [x] Core outline includes a slide on **Context-as-a-Service** (or approved equivalent name)
- [x] Core outline includes slides on **attention limits**, **crowding**, **ontology/domain graphs**, and **documentation architecture**
- [x] Core outline includes a slide on **documentation lifecycle and ADR lifecycle**
- [x] Core outline includes a slide on **module boundaries, contracts, and architecture-for-agents**
- [x] At least one core slide covers **architecture + documentation + guardrails** as enabling system, not isolated practices
- [x] At least one core slide covers **roadmap + metrics + governance**
- [x] At least one core slide covers **self-hosted constraint and tooling implication**
- [x] Every core slide has speaker notes
- [x] Appendix outline exists and contains objection-handling topics
- [x] Source map includes at least one report reference per core slide

### Must Have
- Recommendation-first story, not section-by-section report summary
- Primary ask framed early: approve Year-1 rollout direction
- Technical credibility via concrete evidence from architecture, process, metrics, risks, and tooling sections
- Explicit handling of self-hosted/perimeter constraint
- Clear distinction between core deck and appendix
- User-provided visuals from the video must be treated as first-class anchors for slide design and narrative sequencing
- Video transcript must be used as a secondary source for terminology and examples where it sharpens the report
- Documentation must be framed as a **living operational system** with lifecycle, drift risk, and consolidation into the main architecture narrative
- Architecture guidance must emphasize **module boundaries and external contracts** over local code-style purity
- English technical terms may remain where already established in source material

### Must NOT Have (guardrails, AI slop patterns, scope boundaries)
- No attempt to turn every report chapter into a slide
- No creation of visual design system, theme, PPTX, Marp, or reveal implementation unless separately requested
- No unsupported claims beyond the existing report and notes
- No reopening broad tool/vendor research unless a direct gap blocks deck structure
- No expansion into full implementation roadmap execution, budget model, or legal opinion
- No “AI hype” framing without risk, trade-off, and governance treatment

## Verification Strategy
> ZERO HUMAN INTERVENTION — all verification is agent-executed.
- Test decision: none for product code; content artifacts verified via file structure and search checks
- QA policy: every task includes agent-executed scenarios for structure, completeness, and evidence traceability
- Evidence: `.sisyphus/evidence/task-{N}-{slug}.{ext}`

## Execution Strategy
### Parallel Execution Waves
> Target: 5-8 tasks per wave. Shared narrative decisions are extracted into Wave 1 to maximize parallelism.

Wave 1: narrative foundation, evidence selection, and deck boundaries
- Task 1: Define presentation thesis, primary decision, and narrative spine
- Task 2: Select core evidence and map report sections to candidate slides
- Task 3: Define core-deck vs appendix split and objection strategy
- Task 4: Define slide-level messaging rules and speaker-notes policy

Wave 2: artifact planning and quality enforcement
- Task 5: Plan `presentation-outline.md`
- Task 6: Plan `presentation-speaker-notes.md`
- Task 7: Plan `presentation-appendix-outline.md` and `presentation-source-map.md`
- Task 8: Plan final coherence audit and verification checks

### Dependency Matrix (full, all tasks)
| Task | Depends On | Blocks | Wave |
|------|-----------|--------|------|
| 1 | — | 2,3,4,5,6,7 | 1 |
| 2 | 1 | 5,7 | 1 |
| 3 | 1 | 5,7 | 1 |
| 4 | 1 | 6,8 | 1 |
| 5 | 1,2,3 | 8 | 2 |
| 6 | 1,4,5 | 8 | 2 |
| 7 | 2,3,5 | 8 | 2 |
| 8 | 4,5,6,7 | F1-F4 | 2 |
| F1-F4 | 8 | — | FINAL |

### Agent Dispatch Summary (wave → task count → categories)
- Wave 1 → 4 tasks → `writing`, `deep`
- Wave 2 → 4 tasks → `writing`, `deep`
- Final → 4 tasks → `oracle`, `unspecified-high`, `writing`, `deep`

## TODOs
> Implementation + Test = ONE task. Never separate.
> EVERY task MUST have: Agent Profile + Parallelization + QA Scenarios.

- [x] 1. Define presentation thesis, primary decision, and narrative spine

  **What to do**: Establish the exact decision the deck must drive, and define a recommendation-first storyline for the core deck. Fix the narrative sequence as: current failure pattern → why AI-ready is a system issue → recommended Year-1 operating model → rollout path → metrics/risk control → decision ask. Explicitly state that the deck is for engineering leaders, not a general AI awareness session.
  **Must NOT do**: Do not turn this into a full slide script. Do not introduce multiple equal-priority decisions. Do not frame the deck as generic innovation storytelling.

  **Recommended Agent Profile**:
  - Category: `writing` — Reason: This is messaging architecture and leadership narrative design.
  - Skills: [] — No special skills required.
  - Omitted: [`frontend-ui-ux`] — No visual design work is required.

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: 2,3,4,5,6,7 | Blocked By: none

  **References**:
  - Pattern: `ai-ready-codebase-report.md:36` — executive summary opening structure
  - Pattern: `ai-ready-codebase-report.md:61` — existing key decisions framing
  - Pattern: `ai-ready-codebase-report.md:204` — paradox framing for why pilots fail
  - Pattern: `ai-ready-codebase-report.md:1190` — Year-1 operating mode recommendation
  - Source: `.sisyphus/drafts/ai-ready-presentation.md:3` — confirmed audience, format, and goal

  **Acceptance Criteria** (agent-executable only):
- [x] Plan specifies exactly one primary decision for the deck
- [x] Plan defines a 5-7 step narrative spine in fixed order
- [x] Narrative positions the deck as recommendation-first for engineering leaders

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Primary decision is explicit
    Tool: Bash
    Steps: Run `grep -n "primary decision\|Primary Decision" .sisyphus/plans/ai-ready-presentation.md`
    Expected: At least one match in Core Objective / Task 1 / Success Criteria
    Evidence: .sisyphus/evidence/task-1-primary-decision.txt

  Scenario: Narrative is recommendation-first, not report-summary-first
    Tool: Bash
    Steps: Run `grep -n "recommendation-first\|current failure pattern\|rollout path\|decision ask" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm fixed story order elements are present
    Evidence: .sisyphus/evidence/task-1-narrative-check.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 2. Select core evidence and map report sections to candidate slides

  **What to do**: Choose the minimum evidence set that makes the deck credible without overloading it. Select 3-5 core findings from the report: leader cases, paradox/adoption failure, AI-ready definition, architecture/documentation/guardrails, roadmap/metrics/risk controls, and self-hosted tooling implications. Map each selected finding to a likely core slide and identify which detailed material belongs in appendix only.
  **Must NOT do**: Do not include every report section. Do not add new external research. Do not duplicate appendix-only material into the main deck.

  **Recommended Agent Profile**:
  - Category: `deep` — Reason: Requires evidence compression and selective sourcing from a broad report.
  - Skills: [] — No special skills required.
  - Omitted: [`playwright`] — No browser work required.

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: 5,7 | Blocked By: 1

  **References**:
  - Pattern: `ai-ready-codebase-report.md:44` — key numbers for executive proof points
  - Pattern: `ai-ready-codebase-report.md:68` — industry context and leader cases
  - Pattern: `ai-ready-codebase-report.md:332` — AI-ready definition and maturity framing
  - Pattern: `ai-ready-codebase-report.md:453` — architecture evidence
  - Pattern: `ai-ready-codebase-report.md:878` — guardrails evidence
  - Pattern: `ai-ready-codebase-report.md:1434` — roadmap evidence
  - Pattern: `ai-ready-codebase-report.md:1721` — metrics and KPI evidence
  - Pattern: `ai-ready-codebase-report.md:2036` — risks evidence
  - Pattern: `ai-ready-codebase-report.md:2248` — self-hosted tooling implications

  **Acceptance Criteria** (agent-executable only):
- [x] Plan names 3-5 core evidence groups for the main deck
- [x] Plan distinguishes core-slide evidence from appendix-only evidence
- [x] Plan includes source mapping expectations for every core slide

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Core evidence groups are capped and explicit
    Tool: Bash
    Steps: Run `grep -n "core evidence\|leader cases\|paradox\|roadmap\|self-hosted" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches identify a bounded evidence selection strategy
    Evidence: .sisyphus/evidence/task-2-core-evidence.txt

  Scenario: Source mapping is required
    Tool: Bash
    Steps: Run `grep -n "source map\|traceability\|report reference per core slide" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm traceability requirement exists
    Evidence: .sisyphus/evidence/task-2-source-map.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 3. Define core-deck vs appendix split and objection strategy

  **What to do**: Specify exactly which topics must remain in the core 10-12 slides and which move to appendix. Core deck must contain only decision-driving material. Appendix must hold backup detail for objections on self-hosted constraints, risks, metrics design, AGENTS.md, Vertical Slice caveats, legal/licensing caveats, and rollout questions.
  **Must NOT do**: Do not let appendix duplicate the main deck. Do not make appendix mandatory for understanding the recommendation.

  **Recommended Agent Profile**:
  - Category: `writing` — Reason: This is a communication-boundary and deck-structure decision.
  - Skills: [] — No special skills required.
  - Omitted: [`git-master`] — No git work required.

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: 5,7 | Blocked By: 1

  **References**:
  - Pattern: `ai-ready-codebase-report.md:610` — architecture caveats suitable for appendix
  - Pattern: `ai-ready-codebase-report.md:860` — documentation minimum level decision
  - Pattern: `ai-ready-codebase-report.md:1008` — guardrails prioritization
  - Pattern: `ai-ready-codebase-report.md:2022` — metrics-by-phase decision
  - Pattern: `ai-ready-codebase-report.md:2226` — risk acceptance vs mitigation decision
  - Pattern: `ai-ready-codebase-report.md:2365` — stack choice and cost discussion suited for objections/Q&A
  - Source: `.sisyphus/notepads/ai-ready-report/decisions.md:1` — licensing and tool classification caveats

  **Acceptance Criteria** (agent-executable only):
- [x] Plan states core deck target is 10-12 slides
- [x] Plan explicitly lists appendix-only topics
- [x] Plan defines appendix as objection-handling support, not duplicate narrative

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Appendix boundary is explicit
    Tool: Bash
    Steps: Run `grep -n "appendix\|backup\|objection" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches show appendix topics and purpose are documented
    Evidence: .sisyphus/evidence/task-3-appendix-boundary.txt

  Scenario: Core deck size limit exists
    Tool: Bash
    Steps: Run `grep -n "10-12" .sisyphus/plans/ai-ready-presentation.md`
    Expected: At least one match confirms core slide limit
    Evidence: .sisyphus/evidence/task-3-slide-limit.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 4. Define slide-level messaging rules and speaker-notes policy

  **What to do**: Establish slide construction rules for the downstream executor. Each core slide must have: title, objective, 2-4 key bullets, source reference(s), and speaker notes sized for leadership delivery rather than transcript form. Speaker notes must work for synchronous presentation and asynchronous review.
  **Must NOT do**: Do not allow transcript-length notes. Do not allow source-free slides. Do not require visual design choices.

  **Recommended Agent Profile**:
  - Category: `writing` — Reason: This defines content standards and note density.
  - Skills: [] — No special skills required.
  - Omitted: [`frontend-ui-ux`] — No slide design system is in scope.

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: 6,8 | Blocked By: 1

  **References**:
  - Pattern: `ai-ready-codebase-report.md:51` — concise action-plan summary style
  - Pattern: `ai-ready-codebase-report.md:58` — expected impact framing
  - Pattern: `ai-ready-codebase-report.md:1698` — decision slide style from roadmap section
  - Source: `.sisyphus/drafts/ai-ready-presentation.md:12` — confirmed executive + technical-heavy balance

  **Acceptance Criteria** (agent-executable only):
- [x] Plan defines required slide fields: title, objective, bullets, sources, notes
- [x] Plan constrains notes to presenter-grade depth, not full memo transcripts
- [x] Plan states that notes must support both live presentation and async review

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Slide field policy is specified
    Tool: Bash
    Steps: Run `grep -n "title, objective, 2-4 key bullets, source reference\|speaker notes" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Match confirms exact slide field policy exists
    Evidence: .sisyphus/evidence/task-4-slide-fields.txt

  Scenario: Notes are bounded in scope
    Tool: Bash
    Steps: Run `grep -n "transcript\|async review\|leadership delivery" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm notes are bounded and dual-use
    Evidence: .sisyphus/evidence/task-4-notes-policy.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 5. Plan `presentation-outline.md`

  **What to do**: Specify the exact structure for the core deck outline artifact. Lock the slide order and purpose so the executor makes zero narrative decisions. Final approved core structure: 1) **AI-Ready Codebase: not about the model, about the environment**, 2) **What happens without preparation**, 3) **What changes after preparation**, 4) **Why long context does not save us: attention limits**, 5) **Dynamic Context Layer** (aka `Task-Aware Context Engine`), 6) **Before coding: crowding, decomposition, scoping**, 7) **What must actually be built in the project**, 8) **AI-ready architecture: module boundaries and external contracts**, 9) **Project ontology and domain graphs**, 10) **Memoberry Bank: documentation as a navigation system**, 11) **Documentation lifecycle and ADR lifecycle**, 12) **Verification is the bridge to autonomy**. If a roadmap must be shown explicitly, it should be embedded as a subsection of slide 12 or moved to appendix to preserve the approved 12-slide narrative.
  **Must NOT do**: Do not exceed 12 core slides. Do not reorder the narrative into a topic dump. Do not hide the decision ask until the end.
  **Slide Boundary Rules**:
  - Slide 1 owns the thesis reframe only; it must NOT explain symptoms or implementation details.
  - Slide 2 owns failure symptoms only; it must NOT explain architectural solutions.
  - Slide 3 owns improvement outcomes only; it must NOT duplicate the mechanics from slides 4-6.
  - Slide 4 owns the core constraint: finite attention and context degradation.
  - Slide 5 owns the response architecture: dynamic context selection/composition.
  - Slide 6 owns operational shaping practices: crowding, decomposition, scoping.
  - Slide 7 owns the artifact inventory only; it must tee up slides 8-11 without unpacking them fully.
  - Slide 8 owns boundaries and contracts only; it is the prerequisite for verification.
  - Slide 9 owns the knowledge model: ontology and domain relationships.
  - Slide 10 owns navigation through knowledge: Memoberry/progressive disclosure.
  - Slide 11 owns governance/freshness: document drift, ADR lifecycle, consolidation into source of truth.
  - Slide 12 owns verification, approval boundaries, and the final ask; it must NOT re-explain prior slides.

  **Recommended Agent Profile**:
  - Category: `writing` — Reason: This is the primary communication artifact structure.
  - Skills: [] — No special skills required.
  - Omitted: [`dev-browser`] — No browser interaction is needed.

  **Parallelization**: Can Parallel: YES | Wave 2 | Blocks: 8 | Blocked By: 1,2,3

  **References**:
  - Pattern: `ai-ready-codebase-report.md:36` — executive summary structure
  - Pattern: `ai-ready-codebase-report.md:623` — documentation and context engineering
  - Pattern: `ai-ready-codebase-report.md:724` — ADR rationale and why decisions must be recorded
  - Pattern: `ai-ready-codebase-report.md:878` — guardrails and verification
  - Pattern: `ai-ready-codebase-report.md:453` — architecture and structure framing
  - Pattern: `ai-ready-codebase-report.md:1019` — operating model and human/agent split
  - Pattern: `ai-ready-codebase-report.md:1434` — roadmap source
  - Pattern: `ai-ready-codebase-report.md:1721` — metrics source
  - Pattern: `ai-ready-codebase-report.md:2036` — risks source
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:75` — context compaction and degradation
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:101` — project preparation, hierarchy, and navigation
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:189` — attention limitations
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:217` — crowding and task decomposition
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:245` — ontology and glossary
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:351` — Memoberry Bank and progressive disclosure
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:359` — documentation hygiene and freshness
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:387` — module boundaries, contracts, and architecture best practices

  **Acceptance Criteria** (agent-executable only):
- [x] Plan defines the exact slide order for 10-12 core slides
- [x] Slide 1 or 2 contains the primary decision/approval ask
- [x] Outline includes the approved 12-slide narrative with practical-build, lifecycle, and contract slides
- [x] Outline ends with verification/autonomy framing and explicit approval asks
- [x] Plan assigns one primary theme owner to each slide with no duplicated ownership across adjacent slides
- [x] Plan includes explicit boundary rules for slides 4-6 and 8-11

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Core slide structure is complete
    Tool: Bash
    Steps: Run `grep -n "not about the model, about the environment\|What happens without preparation\|What changes after preparation\|attention limits\|Dynamic Context Layer\|What must actually be built in the project\|module boundaries and external contracts\|Project ontology and domain graphs\|Memoberry Bank\|Documentation lifecycle and ADR lifecycle\|Verification is the bridge to autonomy" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm all mandatory slide types are planned
    Evidence: .sisyphus/evidence/task-5-outline-structure.txt

  Scenario: Decision ask appears early
    Tool: Bash
    Steps: Run `grep -n "Slide 1 or 2\|decision ask\|approval ask" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm early decision framing rule exists
    Evidence: .sisyphus/evidence/task-5-decision-early.txt

  Scenario: Adjacent slides do not share the same primary ownership
    Tool: Bash
    Steps: Run `grep -n "Slide Boundary Rules\|owns the core constraint\|owns the response architecture\|owns operational shaping practices\|owns the knowledge model\|owns navigation through knowledge\|owns governance/freshness" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm explicit non-overlapping ownership for overlap-prone slide groups
    Evidence: .sisyphus/evidence/task-5-boundary-rules.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 6. Plan `presentation-speaker-notes.md`

  **What to do**: Define the structure and expected depth of speaker notes for each slide. Notes must clarify the meaning of each bullet, highlight one intended leadership takeaway per slide, and include transitions between slides. For visual slides based on user-provided screenshots, notes must explicitly explain what the viewer should notice: wasted context, compaction, free context capacity, dynamic context generation, relation between ontology nodes, progressive disclosure in documentation, document drift risk, ADR consolidation into architecture docs, and why contracts matter more than local code aesthetics.
  **Must NOT do**: Do not create verbatim presenter script. Do not let notes drift into a standalone memo longer than the outline itself. Do not omit transitions or leadership takeaway.

  **Recommended Agent Profile**:
  - Category: `writing` — Reason: Requires concise explanatory prose and rhetorical continuity.
  - Skills: [] — No special skills required.
  - Omitted: [`playwright`] — No UI validation required.

  **Parallelization**: Can Parallel: YES | Wave 2 | Blocks: 8 | Blocked By: 1,4,5

  **References**:
  - Pattern: `ai-ready-codebase-report.md:38` — problem framing language
  - Pattern: `ai-ready-codebase-report.md:41` — opportunity framing language
  - Pattern: `ai-ready-codebase-report.md:58` — expected impact language
  - Pattern: `ai-ready-codebase-report.md:1698` — decision synthesis pattern
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:69` — no-prep failure path
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:121` — prepared path and navigation
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:181` — attention and limited focus explanation
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:351` — documentation disclosure model
  - Source: `.sisyphus/plans/ai-ready-presentation.md:37` — deliverable definition for speaker notes

  **Acceptance Criteria** (agent-executable only):
- [x] Plan requires notes for every core slide
- [x] Plan requires one leadership takeaway per slide
- [x] Plan requires slide-to-slide transitions in notes
- [x] Plan requires visual-reading notes for screenshot/diagram slides
- [x] Plan requires notes to explain ADR/document lifecycle and module-boundary significance

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Speaker notes are required for each slide
    Tool: Bash
    Steps: Run `grep -n "notes for every core slide\|speaker notes" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm mandatory per-slide notes
    Evidence: .sisyphus/evidence/task-6-notes-required.txt

  Scenario: Notes include takeaways and transitions
    Tool: Bash
    Steps: Run `grep -n "leadership takeaway\|transitions between slides\|viewer should notice\|ADR\|contracts matter" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm note requirements and visual-reading guidance exist for lifecycle and contracts slides
    Evidence: .sisyphus/evidence/task-6-note-depth.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 7. Plan `presentation-appendix-outline.md` and `presentation-source-map.md`

  **What to do**: Define two support artifacts. First, an appendix outline that prepares backup slides for expected objections on risks, tooling, governance, legal/licensing caveats, metrics interpretation, architecture caveats, ADR/document drift handling, contract-first architecture questions, and naming alternatives for the context-engine slide. Second, a source map that traces every core slide and appendix topic back to exact report sections, the video transcript notes, and the user-provided screenshots/diagrams.
  **Must NOT do**: Do not let appendix become a second main deck. Do not leave any core slide unsourced. Do not reference sources outside the discovered workspace without justification.

  **Recommended Agent Profile**:
  - Category: `deep` — Reason: Requires precise traceability and objection modeling.
  - Skills: [] — No special skills required.
  - Omitted: [`git-master`] — No repository history work needed.

  **Parallelization**: Can Parallel: YES | Wave 2 | Blocks: 8 | Blocked By: 2,3,5

  **References**:
  - Pattern: `ai-ready-codebase-report.md:578` — Vertical Slice caveats
  - Pattern: `ai-ready-codebase-report.md:1314` — human-factor risks
  - Pattern: `ai-ready-codebase-report.md:2022` — metrics decision thresholds
  - Pattern: `ai-ready-codebase-report.md:2226` — risk prioritization decisions
  - Pattern: `ai-ready-codebase-report.md:2365` — stack/cost decision and caveats
  - Source: `.sisyphus/notepads/ai-ready-report/decisions.md:1` — conditional tool classification and AGPL caveat
  - Source: `.sisyphus/notepads/ai-ready-report/learnings.md:11` — verified quality metrics for confidence statements
  - Source: `.sisyphus/drafts/ai-ready-video-transcript.md:1` — supplemental source for slide language and examples
  - Source: user-provided screenshots in session — anchor visuals for no-prep / prep / context / attention / domain graph / markdown-doc slides

  **Acceptance Criteria** (agent-executable only):
- [x] Plan requires an appendix artifact with objection-focused topics
- [x] Plan requires a source map with at least one source per core slide
- [x] Plan requires supporting notes files to be used where caveats matter
- [x] Plan requires user-provided visuals to be mapped to the relevant core slides
- [x] Plan includes appendix support for ADR drift, contract objections, and boundary-related questions

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Appendix topics are objection-oriented
    Tool: Bash
    Steps: Run `grep -n "objections\|legal/licensing caveats\|metrics interpretation\|architecture caveats\|ADR/document drift\|contract-first architecture\|boundary-related questions" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm appendix topics are tuned for objections/Q&A including lifecycle and contracts
    Evidence: .sisyphus/evidence/task-7-appendix-topics.txt

  Scenario: Source map traceability is enforced
    Tool: Bash
    Steps: Run `grep -n "source map\|at least one source per core slide\|user-provided visuals\|video transcript" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm traceability requirement exists for report, transcript, and visuals
    Evidence: .sisyphus/evidence/task-7-traceability.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

- [x] 8. Plan final coherence audit and verification checks

  **What to do**: Define the final verification pass that checks whether all planned presentation artifacts align on the same thesis, do not exceed scope, and retain recommendation-first flow. Include concrete command-based checks for slide count, notes presence, appendix presence, and source traceability. Add a final logic audit to ensure the deck can stand both in a live meeting and in async circulation.
  **Must NOT do**: Do not rely on human subjective review as the only acceptance gate. Do not require visual inspection if the deliverable remains outline + notes.

  **Recommended Agent Profile**:
  - Category: `deep` — Reason: This task defines consistency and verification logic across all artifacts.
  - Skills: [] — No special skills required.
  - Omitted: [`frontend-ui-ux`] — No design QA required.

  **Parallelization**: Can Parallel: YES | Wave 2 | Blocks: F1-F4 | Blocked By: 4,5,6,7

  **References**:
  - Pattern: `ai-ready-codebase-report.md:61` — decision-oriented framing to preserve
  - Pattern: `ai-ready-codebase-report.md:1694` — continue/adjust/stop logic for decision checkpoints
  - Source: `.sisyphus/COMPLETION_SUMMARY.md:90` — next-step framing useful for closing logic
  - Source: Metis review in session — acceptance criteria must be command-verifiable

  **Acceptance Criteria** (agent-executable only):
- [x] Plan contains command-verifiable checks for slide count, notes, appendix, and source map
- [x] Plan requires one final coherence audit for thesis consistency
- [x] Plan explicitly states that no visual validation is required unless a slide tool is later chosen

  **QA Scenarios** (MANDATORY — task incomplete without these):
  ```
  Scenario: Verification checks are command-based
    Tool: Bash
    Steps: Run `grep -n "slide count\|source map\|appendix\|command-verifiable" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm command-oriented verification guidance exists
    Evidence: .sisyphus/evidence/task-8-command-checks.txt

  Scenario: Coherence audit is required
    Tool: Bash
    Steps: Run `grep -n "coherence audit\|thesis consistency\|async circulation" .sisyphus/plans/ai-ready-presentation.md`
    Expected: Matches confirm final logic audit requirement exists
    Evidence: .sisyphus/evidence/task-8-coherence.txt
  ```

  **Commit**: NO | Message: `n/a` | Files: `.sisyphus/plans/ai-ready-presentation.md`

## Final Verification Wave (4 parallel agents, ALL must APPROVE)
- [x] F1. Plan Compliance Audit — oracle
- [x] F2. Content Quality Review — writing
- [x] F3. Deck Logic and Evidence Audit — deep
- [x] F4. Scope Fidelity Check — deep

## Commit Strategy
- Commit: NO
- Reason: planning artifact only; no commit unless user explicitly requests it

## Success Criteria
- A downstream executor can create the presentation artifacts without making additional narrative, scope, or sourcing decisions
- The resulting deck is recommendation-first, technically credible, and bounded to engineering-leadership decisions
- The resulting deck can be consumed synchronously in a leadership meeting or asynchronously via notes without changing the core message
