# AI-Ready Presentation Visual Notes

Purpose: explain what each visual-heavy slide must communicate to the audience. These notes are for planning alignment, not design implementation or slide rendering.

---

## Slide 1. AI-Ready Codebase: not about the model, about the environment

**Visual type:** Simple decision-framing contrast slide

**What the visual must communicate:**
- Two paths side by side: "Model-first experimentation" vs "Environment-first rollout"
- Model-first path: shows scattered tools, ad-hoc usage, rising complexity
- Environment-first path: shows structured rollout, guardrails, and measured progress
- The contrast should make clear that both paths use the same model quality, but get different results

**Key visual elements:**
- Two parallel tracks or columns
- Icons representing tools/chaos on left, structure/control on right
- A subtle arrow or flow suggesting evolution from left to right is the recommended path

**Reading guidance for presenter:**
- First, notice that both paths start with the same model capability
- Second, notice that the difference is the operating environment around the model

---

## Slide 2. What happens without preparation

**Visual type:** Diagram of the no-prep agent path (user-provided visual in session)

**What the visual must communicate:**
- An agent workflow that spends most of its effort on exploration before reaching execution
- Drift: the agent searching through large project space without clear navigation
- Exploration: repeated file reads, directory scanning, context filling
- Waste: context window filling with search activity rather than task progress
- The path should look winding, looping, or backtracking

**Key visual elements:**
- A start point labeled "Task request"
- A wandering path through "Exploration / Search" territory
- Multiple loop-backs or dead-ends representing wrong turns
- A compressed "Execution" zone at the end
- Visual emphasis on the large area consumed by exploration vs small area for delivery

**Reading guidance for presenter:**
- First, notice how much of the path is exploration rather than implementation
- Second, notice the waste pattern: repeated scanning, context fill, and loss of task focus

---

## Slide 3. What changes after preparation

**Visual type:** Side-by-side comparison: unprepared vs prepared path (user-provided visual in session)

**What the visual must communicate:**
- Left side: the wandering, exploration-heavy path from Slide 2
- Right side: a direct, structured path from task to execution
- The prepared path shows clear entry points, bounded scope, and focused work
- The contrast demonstrates predictability gain, not just speed gain

**Key visual elements:**
- Two parallel journey maps or flow diagrams
- Left: loops, backtracks, broad search areas (labeled "Unprepared")
- Right: straight-line path with checkpoints (labeled "Prepared")
- Highlighted zones: "Navigation" → "Bounded Task" → "Execution"
- Visual metaphor: maze vs guided pathway

**Reading guidance for presenter:**
- First, notice the shorter path from task start to execution
- Second, notice that structure reduces wandering, not by adding more prompt text, but by improving navigation

---

## Slide 4. Why long context does not save us: attention limits

**Visual type:** Attention and compaction diagram (user-provided visual in session)

**What the visual must communicate:**
- Context window as a finite container with scarce "free working room"
- Attention spreading across the entire context, getting thinner as context grows
- Compaction as a compression process that loses detail over time
- The core message: more context ≠ better attention

**Key visual elements:**
- A container or tank representing the context window
- "Used context" filling most of the space
- A small highlighted zone labeled "Free working room" or "Available attention"
- Arrows showing attention having to cover the entire filled area
- A secondary diagram showing compaction: before/after state with detail loss

**Reading guidance for presenter:**
- First, notice that free working room inside context is limited and valuable
- Second, notice how compaction trades apparent continuity for loss of detail over time

---

## Slide 5. Dynamic Context Layer

**Visual type:** Context-as-a-service or task-aware context engine diagram (user-provided visual in session)

**What the visual must communicate:**
- A shift from "dump repository into prompt" to "assemble relevant context per task"
- Task request flowing into a selection/filtering layer
- Selection layer pulling from indexed knowledge: files, contracts, docs, checks
- Assembled context package delivered to agent, leaving room for execution

**Key visual elements:**
- Input: "Task request" with specific parameters
- Central engine: "Context Assembly" or "Dynamic Context Layer"
- Indexed sources feeding into the engine: Project Knowledge, Contracts, ADRs, Verification Paths
- Output: "Focused Context Package" (smaller, relevant) → Agent
- Contrast indicator: show size reduction vs raw repository dump

**Reading guidance for presenter:**
- First, notice the flow from task request to selected knowledge, not from repository bulk to prompt dump
- Second, notice that the layer combines guidance, code locations, and verification paths into one assembled package

---

## Slide 6. Before coding: crowding, decomposition, scoping

**Visual type:** Simple pre-coding workflow diagram

**What the visual must communicate:**
- A three-stage workflow before implementation begins
- Stage 1: Crowding (check local fit and constraints)
- Stage 2: Decomposition (break into bounded pieces)
- Stage 3: Scoping (define boundaries: touch this, not that)
- The progression shows risk reduction before code changes

**Key visual elements:**
- Three connected blocks or stages in horizontal flow
- Crowding: magnifying glass or context bubble showing nearby code
- Decomposition: splitting one large block into smaller pieces
- Scoping: bounded box with clear edges and "no-go" zones marked
- Optional: show a small output arrow labeled "Ready to implement"

**Reading guidance for presenter:**
- First, notice the order: understand local fit, split the task, then execute inside bounds
- Second, notice that each step narrows risk before the agent changes code

---

## Slide 7. What must actually be built in the project

**Visual type:** Inventory-style list slide (minimal visual design required)

**What the visual must communicate:**
- A concrete stack of artifacts and rules, not abstract concepts
- The minimum set needed for AI-readiness
- Grouping: Navigation assets, Knowledge assets, Control assets

**Key visual elements:**
- Three clear groupings or columns:
  - Navigation: Project maps, Module guidance, Run commands
  - Knowledge: Glossary, ADR access, Domain graphs
  - Control: Guardrails, Verification entry points, No-go zones
- Visual treatment should feel like a checklist, not a wish list
- Each item should be a concrete noun (thing to build), not a concept

**Reading guidance for presenter:**
- First, notice the stack as a minimum operating set, not a wish list
- Second, notice that the inventory points forward to architecture, ontology, documentation navigation, and lifecycle

---

## Slide 8. AI-ready architecture: module boundaries and external contracts

**Visual type:** Boundary diagram showing modules, external contracts, and allowed dependency directions (user-provided visual in session)

**What the visual must communicate:**
- Modules as bounded containers with clear edges
- External contracts as explicit interfaces between modules
- Allowed dependency directions (which modules can call which)
- The concept of blast radius: changes stay inside boundaries

**Key visual elements:**
- 3-4 module boxes with clear borders
- Contract points marked at module edges (interface markers)
- Directional arrows showing approved dependencies
- A change indicator (star or highlight) staying inside one module
- Optional: red X over an arrow showing a forbidden dependency

**Reading guidance for presenter:**
- First, notice the module edges and the approved dependency directions
- Second, notice that contracts sit at the points where autonomy becomes risky, which is why they deserve more weight than local code aesthetics

---

## Slide 9. Project ontology and domain graphs

**Visual type:** Ontology or domain graph, with a few key entity relationships highlighted (user-provided visual in session)

**What the visual must communicate:**
- Domain concepts connected by relationships (not files in a directory)
- Key entities as nodes, business relationships as edges
- The file tree cannot express these semantic connections
- Expert knowledge captured in reusable form

**Key visual elements:**
- A network graph with 6-10 nodes representing domain concepts
- Nodes labeled with business terms (not technical file names)
- Edges showing relationships: "has many", "belongs to", "triggers", "depends on"
- A few key relationships highlighted with color or weight
- Contrast inset: a file tree showing that file structure ≠ domain structure

**Reading guidance for presenter:**
- First, notice the key entities and how they relate, not just the number of nodes
- Second, notice that the graph captures relationships the file tree cannot express

---

## Slide 10. Memoberry Bank: documentation as a navigation system

**Visual type:** Memoberry-style documentation hierarchy, overview to local detail (user-provided visual in session)

**What the visual must communicate:**
- Progressive disclosure: top-level overview first, drilling to local detail as needed
- Documentation as navigation, not just reference
- Hierarchy levels: System overview → Area guides → Module detail → Local instructions

**Key visual elements:**
- A layered pyramid or tree structure
- Top layer: "AGENTS.md" or "Project Overview" (broad, shallow)
- Middle layers: Area guides, Module docs (moderate depth)
- Bottom layer: Local implementation detail (deep, narrow)
- Arrows showing the descent path from general to specific
- Contrast: a flat "dump" of all docs vs the layered access

**Reading guidance for presenter:**
- First, notice the top-down path from overview to local detail
- Second, notice that the point is controlled descent through the knowledge base, not dumping all documentation into context

---

## Slide 11. Documentation lifecycle and ADR lifecycle

**Visual type:** Lightweight lifecycle loop diagram (user-provided visual in session)

**What the visual must communicate:**
- Documentation and ADRs as living documents, not one-time artifacts
- The maintenance loop: code changes trigger doc updates
- Drift as the enemy: stale docs mislead both humans and agents
- Source-of-truth consolidation as the goal

**Key visual elements:**
- A circular loop with 4-5 stages:
  - Code / Architecture change
  - Documentation update
  - ADR refresh (if decision involved)
  - Source-of-truth consolidation
  - Back to change detection
- Trigger indicators: what causes updates (architecture change, repeated mistakes, rollout learning)
- Warning icon: "Drift" or "Stale guidance" shown as loop failure

**Reading guidance for presenter:**
- First, notice the lifecycle loop: change in code should trigger updates in docs and decisions
- Second, notice that ADR consolidation protects architectural intent from drift

---

## Slide 12. Verification is the bridge to autonomy

**Visual type:** Autonomy ladder tied to verification strength and approval gates (user-provided visual in session)

**What the visual must communicate:**
- Autonomy rising as verification strength increases
- Staged progression: assistance → bounded autonomy → expanded autonomy
- Red lines: hard stops where autonomy cannot proceed without approval
- The Year-1 rollout stays in the lower rungs

**Key visual elements:**
- A ladder or staircase with 4-5 rungs
- Bottom rung: "Assistance only" (full review)
- Middle rungs: "Bounded autonomy" (tests + lint + type + structural rules)
- Upper rungs: "Expanded autonomy" (full verification stack)
- Red barrier lines at: external API changes, destructive actions, deploys, data migrations, secrets
- Year-1 marker: highlighting which rungs are approved for Year 1

**Reading guidance for presenter:**
- First, notice that autonomy rises only with verification strength, not with model confidence
- Second, notice the explicit red lines: no silent external API changes, destructive actions, deploys, data migrations, or secrets handling without approval

---

## Visual Asset Traceability

| Slide | Visual Reference | Source |
|-------|------------------|--------|
| 1 | Decision contrast | To be created |
| 2 | No-prep path | user-provided visual in session |
| 3 | Unprepared vs prepared comparison | user-provided visual in session |
| 4 | Attention/compaction diagram | user-provided visual in session |
| 5 | Context engine diagram | user-provided visual in session |
| 6 | Pre-coding workflow | To be created (simple diagram) |
| 7 | Asset inventory | Text-based slide |
| 8 | Module boundary diagram | user-provided visual in session |
| 9 | Domain ontology graph | user-provided visual in session |
| 10 | Memoberry documentation hierarchy | user-provided visual in session |
| 11 | Documentation lifecycle loop | user-provided visual in session |
| 12 | Autonomy ladder | user-provided visual in session |

---

## Notes for Design Implementation

- These notes describe communication intent, not visual design specs
- Actual slide design should follow organizational presentation standards
- All "user-provided visual in session" references indicate concepts discussed in working sessions that shaped the deck but do not exist as standalone design files
- Simple diagrams (slides 1, 6, 7) can be created with basic presentation tools
- Complex conceptual diagrams (slides 2-5, 8-12) should be reviewed against source materials before design finalization
