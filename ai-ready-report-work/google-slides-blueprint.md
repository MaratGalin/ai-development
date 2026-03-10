# Google Slides Blueprint, AI-Ready Codebase

Purpose: practical handoff for manual assembly in Google Slides.

Use this file as the build guide for the core 12-slide deck. Keep the approved narrative, slide order, and leadership framing intact. Treat all visual references marked `user-provided visual in session` as concepts discussed in working sessions, not as workspace files.

## Core deck build rules

- Keep slides clean, leadership-facing, and easy to scan in presentation mode.
- Prefer 3 to 4 on-slide bullets plus one short takeaway line.
- Use sentence case titles.
- Use diagrams and screenshots only where the approved artifacts already call for them.
- Don't invent file-based assets, metrics, or proof points that are not in the approved materials.
- Build for live delivery first, then for async reading.

## Slide 1. AI-Ready Codebase: not about the model, about the environment

**On-slide copy**
- Same model quality, very different delivery outcomes
- Ad hoc AI use scales tool access, not delivery reliability
- Recommendation: fund a Year 1 rollout with baselines, guardrails, a limited pilot, and self-hosted constraints

**Footer takeaway**
Approve the environment now, before uncontrolled usage becomes the default.

**Recommended layout**
Two-column contrast, left for model-first experimentation, right for environment-first rollout, with short takeaway footer.

**Visual placement note**
Use the right half for a simple comparison graphic built directly in Slides. No external asset is required. Keep both columns balanced so the recommendation reads as a choice, not a dense text slide.

**Speaker-note summary**
Open on the leadership decision. Frame this as an operating-model funding choice, not a model-shopping discussion. Stress that the main bottleneck is the engineering environment around the model.

**Build instructions**
Create a two-column slide. Add 2 to 3 short labels or icons under each path. Make the right column visually cleaner and more ordered. Place the takeaway as a bottom bar or footer line.

## Slide 2. What happens without preparation

**On-slide copy**
- Agents lose time to search, re-reading, and guesswork
- Context fills with exploration before useful execution begins
- Output looks fast at first, then turns into rework and fragile changes
- Visual: user-provided visual in session

**Footer takeaway**
Unprepared adoption creates hidden cost and unstable quality.

**Recommended layout**
Visual-led slide, about two-thirds visual and one-third text, with bullets stacked beside or under the visual.

**Visual placement note**
Reserve the main canvas for the no-prep path visual concept. If no source image is available at build time, recreate a simple winding path diagram with loop-backs and a small execution zone.

**Speaker-note summary**
Explain that the agent burns budget on orientation and search before real work begins. Tie the waste pattern to drift, repeated scanning, and fragile output.

**Build instructions**
Place the title at top. Put the visual on the left or center. Keep bullets short on the right. Highlight exploration area size versus execution area size with one accent color.

## Slide 3. What changes after preparation

**On-slide copy**
- Clear entry points reduce unnecessary codebase traversal
- Bounded tasks shift effort from exploration to execution
- Shared guidance improves first-pass accuracy and predictability
- Visual: user-provided visual in session

**Footer takeaway**
Preparation is the multiplier that turns model capability into dependable delivery.

**Recommended layout**
Side-by-side comparison slide, unprepared path on the left and prepared path on the right, with short bullets above or below.

**Visual placement note**
Give the prepared path more visual clarity and a straighter flow. If the session visual is unavailable, recreate both paths as simple journey diagrams so the contrast remains obvious.

**Speaker-note summary**
Show that the model does not need to get smarter for outcomes to improve. The project becomes easier to navigate, which makes execution more predictable.

**Build instructions**
Use mirrored panels. Label them clearly, `Unprepared` and `Prepared`. Keep arrows, checkpoints, and spacing consistent so the contrast reads instantly from the back of the room.

## Slide 4. Why long context does not save us: attention limits

**On-slide copy**
- Bigger context windows add storage, not reliable working attention
- Attention still stretches across the full prompt
- Repeated compaction drops fidelity over long sessions
- Visual: user-provided visual in session

**Footer takeaway**
We need to protect scarce attention, not just buy bigger prompts.

**Recommended layout**
Diagram-first slide with one main attention graphic and a smaller compaction callout.

**Visual placement note**
Main diagram should show the context window as a finite container with a small amount of free working room. Add a compact before-and-after compaction inset if space allows.

**Speaker-note summary**
Clarify why long context is not a complete answer. Attention still thins out, and compaction loses detail over time, so structure matters more than raw prompt size.

**Build instructions**
Keep text minimal. Use one accent color to mark scarce free working room. If recreating manually, use simple containers and arrows rather than detailed illustration.

## Slide 5. Dynamic Context Layer

**On-slide copy**
- Assemble task-relevant files, docs, contracts, and checks on demand
- Preserve working room for reasoning and execution
- Make context a retrieval and composition capability, not a repository dump
- Visual: user-provided visual in session

**Footer takeaway**
The key systems investment is task-aware context assembly.

**Recommended layout**
Horizontal flow diagram, task request to context layer to focused context package to agent, with short support bullets under the flow.

**Visual placement note**
Center the context engine as the dominant object on the slide. Show multiple knowledge sources feeding in, but keep the output visually smaller and more focused than the inputs.

**Speaker-note summary**
Present this as the core systems response to finite attention. The point is not to stuff more repo data into prompts, but to assemble what matters for the task.

**Build instructions**
Use four stages in one line. Label sources clearly, for example docs, contracts, ADRs, checks. Add a small visual size contrast between raw repository bulk and focused context package.

## Slide 6. Before coding: crowding, decomposition, scoping

**On-slide copy**
- Crowding checks local fit and nearby constraints
- Decomposition keeps work small enough to stay coherent
- Scoping defines what the agent may touch, and what stays off-limits
- Visual: simple pre-coding workflow

**Footer takeaway**
Planning discipline is part of the control system.

**Recommended layout**
Three-step horizontal workflow with one short line under each stage, plus a takeaway footer.

**Visual placement note**
This can be created directly in Slides. Use three connected blocks with increasing clarity from left to right, ending in a bounded execution box.

**Speaker-note summary**
Make clear that better results start before implementation. Crowding, decomposition, and scoping narrow risk before the agent writes code.

**Build instructions**
Build three equal-width blocks. Add a small icon or shape for each stage. Mark the scoping block with a visible boundary and one subtle no-go indicator.

## Slide 7. What must actually be built in the project

**On-slide copy**
- Navigation assets: project maps, module guidance, run commands
- Knowledge assets: glossary, ADR access, domain graphs
- Control assets: guardrails, verification entry points, no-go zones

**Footer takeaway**
Approval is for a bounded infrastructure package, not abstract AI experimentation.

**Recommended layout**
Three-column inventory slide with clear group labels and checklist-style item stacks.

**Visual placement note**
No heavy visual needed. Let the grouping itself do the work. This should feel like an operating inventory, not a conceptual framework slide.

**Speaker-note summary**
Translate the prior mechanism slides into a concrete build program. Stress that leadership is approving a manageable asset stack and rule set.

**Build instructions**
Create three columns with bold headers. Keep each item as a concrete noun phrase. Use light icons only if they help scanning. Avoid decorative graphics.

## Slide 8. AI-ready architecture: module boundaries and external contracts

**On-slide copy**
- Bounded modules keep changes local and blast radius small
- Explicit contracts define what must remain stable
- Structural rules in CI make those boundaries enforceable
- Visual: user-provided visual in session

**Footer takeaway**
Safe autonomy depends on clear edges and meaningful verification.

**Recommended layout**
Boundary diagram with short bullets in a narrow side column or along the bottom.

**Visual placement note**
The module diagram should dominate the slide. Show 3 to 4 bounded modules, explicit contract points, and approved dependency directions.

**Speaker-note summary**
Focus on blast radius, bounded change, and stable interfaces. The point is less about code style and more about safe change zones plus enforceable rules.

**Build instructions**
Keep arrows directional and sparse. Use one visual marker to show a change staying inside a module. If useful, add one forbidden dependency with a red X.

## Slide 9. Project ontology and domain graphs

**On-slide copy**
- A shared glossary reduces ambiguity in business terms
- Domain graphs expose relationships the file tree can't show
- Expert knowledge becomes reusable system guidance
- Visual: user-provided visual in session

**Footer takeaway**
Domain modeling lowers semantic mistakes and search cost.

**Recommended layout**
Graph-led slide with a compact text column or bottom strip for the three bullets.

**Visual placement note**
Use business terms for node labels, not file names. If the session visual is not available, recreate a small domain graph with a few highlighted relationships and a tiny file-tree contrast note.

**Speaker-note summary**
Explain that code structure does not carry enough business meaning on its own. The ontology turns expert knowledge into reusable navigation infrastructure.

**Build instructions**
Limit the graph to a readable number of nodes. Highlight 2 to 3 relationships only. Keep the labels large enough for projection.

## Slide 10. Memoberry Bank: documentation as a navigation system

**On-slide copy**
- Start with top-level orientation, then move into local detail
- Reveal module guidance only when the task needs it
- Keep context focused without losing access to depth
- Visual: user-provided visual in session

**Footer takeaway**
Good docs route work through the system with less noise and fewer wrong turns.

**Recommended layout**
Layered hierarchy diagram on the left or center, with concise bullets on the right and a footer takeaway.

**Visual placement note**
Show the documentation stack as a path from overview to local instructions. The visual should communicate controlled descent, not a flat pile of documents.

**Speaker-note summary**
Position documentation as active navigation infrastructure. The point is progressive disclosure, so agents get orientation first and detail only when needed.

**Build instructions**
Use 3 to 4 hierarchy levels. Make the top layer visually broad and shallow, then narrow toward implementation detail. Add arrows to show downward movement.

## Slide 11. Documentation lifecycle and ADR lifecycle

**On-slide copy**
- Stale guidance misleads agents faster than missing guidance
- Update docs and ADRs on architecture change, repeated mistakes, and rollout learning
- Keep current rationale in one source of truth
- Visual: user-provided visual in session

**Footer takeaway**
Documentation freshness is an operating responsibility.

**Recommended layout**
Lifecycle loop with trigger callouts and one short takeaway footer.

**Visual placement note**
The loop should be central. Include update triggers as small callouts around the loop. Keep drift or stale guidance visible as the failure mode.

**Speaker-note summary**
Stress that stale guidance creates false confidence. Docs and ADRs need a maintenance loop tied to system change and repeated failure patterns.

**Build instructions**
Use a 4 to 5 step circular loop. Label each step with plain nouns or verb phrases. Add a small warning marker for drift outside the loop, not inside it.

## Slide 12. Verification is the bridge to autonomy

**On-slide copy**
- Raise autonomy only behind tests, linting, types, structural rules, and review
- Keep approval boundaries for external APIs, destructive actions, deploys, data migrations, and secrets
- Year 1 ask: baseline measurement, one limited pilot, enforced guardrails, Dynamic Context infrastructure, self-hosted constraints
- Visual: user-provided visual in session

**Footer takeaway**
Fund a staged rollout where trust grows only behind proof.

**Recommended layout**
Autonomy ladder or staircase graphic with bullets in a side column and Year 1 highlight on the lower rungs.

**Visual placement note**
Show autonomy increasing only as verification strengthens. Make red-line approval boundaries clearly visible. Keep the Year 1 marker conservative and grounded in lower-risk levels.

**Speaker-note summary**
Close the deck by tying trust to verification, not optimism. Re-state the approval ask as a staged Year 1 rollout with guardrails and limited scope.

**Build instructions**
Use a clear vertical or diagonal ladder. Add one color for allowed Year 1 range and one contrasting color for approval gates. Put the final takeaway in a strong footer bar.

## Appendix backup-slide rules

Use appendix slides only for objections, caveats, and Q&A. Don't retell the 12-slide narrative. Keep each objection to one backup slide. Prefer tables, thresholds, examples, and exception handling over repeated story slides. Reuse the same visual concepts only when they sharpen the rebuttal. Keep appendix styling lighter than the core deck so it reads as backup material.

## Appendix 1. Why not just use stronger models and larger context?

**Appendix title**
Why stronger models and larger context are not enough

**On-slide copy**
- Model quality is no longer the main bottleneck in large codebases
- Long context adds storage, not reliable working attention
- Repeated compaction still loses fidelity over long sessions
- Better navigation and task shaping cut waste more reliably than bigger prompts

**Recommended layout**
Two-column backup slide, left for constraint table, right for short rebuttal bullets.

**Visual placement note**
If helpful, reuse the no-prep vs prepared path concept or the attention and compaction visual, both referenced as `user-provided visual in session`. If neither is used, build a simple table contrasting `bigger prompt` vs `better environment`.

**Speaker-note summary**
Answer the model-first objection directly. The point is not that better models do nothing, it's that they do not remove navigation cost, attention spread, or compaction loss inside real projects.

**Build instructions**
Keep this compact. Use 3 row comparison logic, for example bottleneck, failure mode, better response. Make the final row clearly favor environment design over prompt expansion.

## Appendix 2. Is self-hosted deployment practical enough for Year 1?

**Appendix title**
Self-hosted practicality for a bounded Year 1 rollout

**On-slide copy**
- Self-hosted constraints change tool choices and rollout speed, but do not block a bounded pilot
- Treat infrastructure, licensing, and policy constraints as design boundaries from day one
- Pilot scope should match available GPU, integration, and support maturity
- Approved tool paths matter more than maximum feature richness

**Recommended layout**
Single-slide decision matrix, top row for constraint categories, bottom row for rollout implication.

**Visual placement note**
No external asset needed. Build a 3 to 4 column table in Slides, for example infrastructure, licensing, maintenance, policy. Keep the Year 1 pilot column visually conservative.

**Speaker-note summary**
Frame self-hosted constraints as a boundary condition, not a blocker. The leadership choice is whether to run a scoped pilot that fits the current perimeter, not whether every ideal tool is available immediately.

**Build instructions**
Use short table cells only. Add one final line at the bottom: `bounded pilot remains practical if scope matches perimeter reality`.

## Appendix 3. Will architecture and documentation work become a costly side program?

**Appendix title**
Minimum scaffolding, not a side program

**On-slide copy**
- Start with the minimum operational layer: one obvious path, key commands, AGENTS.md, small ADR base
- Add artifacts incrementally by vertical slice, not by full rewrite
- Use layering: project map, module guidance, glossary, contracts, ADR links, verification paths
- Keep over-documentation and architecture purity out of scope

**Recommended layout**
Left-to-right maturity strip, minimum viable layer to incremental expansion, with one caveat box.

**Visual placement note**
Create directly in Slides. Show a narrow first layer and 2 to 3 later additions. Use the caveat box for exceptions like shared kernels, legacy cores, or performance-critical zones.

**Speaker-note summary**
Defuse the fear that this becomes a large parallel program. Emphasize that the ask is minimal scaffolding that lowers search cost and blast radius, then grows only where value is proven.

**Build instructions**
Use one horizontal band for `minimum now` and one smaller band for `expand later`. Add a compact caveat callout rather than a long exception list.

## Appendix 4. Are contracts and module boundaries actually enforceable in a messy enterprise codebase?

**Appendix title**
Contract-first enforcement in imperfect codebases

**On-slide copy**
- Boundaries reduce files-per-change and make verification meaningful
- Public APIs and dependency rules can be enforced through CI and structural tests
- Not every area should migrate at once, high-risk legacy zones need staged handling
- Stable edges are the basis for approval boundaries and safer autonomy

**Recommended layout**
Two-part backup slide, top for enforceability claims, bottom for staged-handling caveats.

**Visual placement note**
If a visual helps, reuse the bounded-module concept as `user-provided visual in session`. Otherwise build a simple `enforce now / stage later` table with one red-line example.

**Speaker-note summary**
Make this practical, not purist. The argument is that agents need stable edges and meaningful checks, even if the full codebase remains uneven for a long time.

**Build instructions**
Use 2 columns only, `enforce now` and `stage later`. Include one example of protected external contract versus flexible internal refactor space.

## Appendix 5. How do we know the metrics are real and not vanity?

**Appendix title**
Metrics discipline for Year 1

**On-slide copy**
- Separate adoption, productivity, and outcome metrics
- Baseline is mandatory before any pilot claim
- Rework, defect leakage, review latency, and DORA-style outcomes matter more than raw PR volume
- Metric ownership must be explicit to prevent local gaming

**Recommended layout**
Compact metrics table with columns for metric class, example signal, and misuse risk.

**Visual placement note**
No external visual required. A clean table is stronger here than a chart. If space allows, add one thin footer row for phase-specific thresholds.

**Speaker-note summary**
Answer the credibility question by showing governance, not just numbers. The point is that Year 1 metrics must be baseline-backed, phase-specific, and owned by named teams.

**Build instructions**
Keep the table to 3 rows only: adoption, productivity, outcome. Add a short bottom note that raw output alone is a false signal.

## Appendix 6. What about regulated domains, sensitive changes, and rollout-risk control?

**Appendix title**
Tighter control for sensitive zones

**On-slide copy**
- No silent changes to external APIs, secrets, deploys, destructive operations, or data migrations
- Regulated, privacy, cryptography, and authentication areas need narrower task classes and stronger human review
- Pilot design should rehearse production governance, not just demo success
- Repeated agent failures should feed back into rules, tests, and documentation updates

**Recommended layout**
Three-zone control slide, low-risk work, controlled work, approval-only work.

**Visual placement note**
Build directly in Slides as a simple tiered control diagram. Use one conservative accent color for the approval-only zone. No external asset is required.

**Speaker-note summary**
Close objection handling on control. Stress that rollout expands only where verification and approvals are strong enough, while sensitive areas remain under tighter review and tighter task boundaries.

**Build instructions**
Use 3 stacked bands with 2 to 3 examples in each. Make the approval-only band unmistakable. Add one short footer note that governance must be exercised in the pilot, not added afterward.
