# AI-Ready Presentation Outline

## Slide 1. AI-Ready Codebase: not about the model, about the environment
- **Title:** AI-Ready Codebase: not about the model, about the environment
- **Slide message:** The leadership decision is to fund an AI-ready engineering environment now, because model quality is no longer the main limit to scalable agent work.
- **Leadership takeaway:** Approve a Year-1 rollout built on baseline measurement, guardrails, limited pilot scope, and self-hosted constraints, instead of letting ad hoc AI usage spread without an operating model.
- **Evidence to show:**
  - Leader cases already show that strong results come from disciplined environments, not prompt tricks alone.
  - Most failed pilots share the same pattern: tool access rises, delivery reliability does not.
  - Our recommendation is evolutionary: Audit, then Pilot, then Scale.
- **Visual anchor:** Simple decision framing slide with one contrast, model-first experimentation vs environment-first rollout.
- **Transition:** To justify approval early, we first show what agent work looks like when the environment is not prepared.
- **Source refs:** `ai-ready-codebase-report.md` Executive Summary: Problem, Opportunity, Action Plan, Key Decisions to Make; `ai-ready-codebase-report.md` Industry Context leader cases.

## Slide 2. What happens without preparation
- **Title:** What happens without preparation
- **Slide message:** In an unprepared codebase, agents spend their budget on search, guesswork, and re-reading, so apparent speed turns into drift, waste, and fragile output.
- **Leadership takeaway:** Saying yes to AI without environment preparation is not a neutral choice, it is a decision to absorb hidden rework and unstable quality.
- **Evidence to show:**
  - Agents get lost in large projects when task framing is weak and navigation cues are missing.
  - Context fills with exploratory reads before useful execution starts.
  - Compaction and repeated repo scanning raise cost and lower reliability.
- **Visual anchor:** Screenshot or diagram of the no-prep path, with drift, exploration, and wasted context highlighted.
- **Transition:** The next slide shows that the same class of model behaves differently once the project is prepared for navigation and bounded execution.
- **Source refs:** `ai-ready-codebase-report.md` What is AI-Ready Codebase: Definition, checklist, maturity framing; `.sisyphus/drafts/ai-ready-video-transcript.md` 21:04, 21:50, 22:49, 24:44, 28:50.

## Slide 3. What changes after preparation
- **Title:** What changes after preparation
- **Slide message:** Once the project gives agents clear entry points, bounded tasks, and explicit guidance, the workflow shifts from exploration-heavy to execution-heavy.
- **Leadership takeaway:** Preparation is the main multiplier for delivery, because it converts raw model capability into repeatable work inside our codebase.
- **Evidence to show:**
  - Hierarchical navigation and task shaping reduce unnecessary codebase traversal.
  - Shared glossary, project structure, and task artifacts improve first-pass accuracy.
  - The gain is predictability, not just speed.
- **Visual anchor:** Side-by-side comparison, unprepared path vs prepared path.
- **Transition:** That improvement happens because long context is not a real substitute for structure.
- **Source refs:** `ai-ready-codebase-report.md` What is AI-Ready Codebase; `ai-ready-codebase-report.md` Harness Engineering concept; `.sisyphus/drafts/ai-ready-video-transcript.md` 29:49, 31:46, 45:49, 47:26.

## Slide 4. Why long context does not save us: attention limits
- **Title:** Why long context does not save us: attention limits
- **Slide message:** Larger context windows do not remove the core limit, because model attention still stretches thin, state still degrades, and compaction still drops fidelity.
- **Leadership takeaway:** We should not buy our way out of the problem with bigger prompts alone, we need an operating model that protects scarce attention.
- **Evidence to show:**
  - Attention spreads across the whole prompt, it does not scale linearly with more context.
  - Compaction compresses state and can erase critical working memory.
  - Repeated compaction in large projects degrades output quality over time.
- **Visual anchor:** Attention and compaction diagram, with free context capacity called out as scarce working room.
- **Transition:** If attention is finite, the right answer is not more repo in the prompt, it is better context assembly.
- **Source refs:** `ai-ready-codebase-report.md` architecture-under-context framing; `.sisyphus/drafts/ai-ready-video-transcript.md` 22:49, 24:44, 26:35, 56:17, 57:04, 58:45, 59:15.

## Slide 5. Dynamic Context Layer
- **Title:** Dynamic Context Layer
- **Slide message:** The project needs a context layer that selects and assembles task-relevant knowledge on demand, instead of dumping the repository into every session.
- **Leadership takeaway:** This is the key systems investment, because it turns context from a storage problem into a retrieval and composition capability.
- **Evidence to show:**
  - Indexed project knowledge can pre-locate relevant files, contracts, docs, and checks.
  - Task-aware context reduces wasted search and preserves working room for execution.
  - Dynamic composition is more resilient than static hint files alone.
- **Visual anchor:** Context-as-a-service or task-aware context engine diagram.
- **Transition:** Even with better context assembly, agents still need disciplined work shaping before they start coding.
- **Source refs:** `ai-ready-codebase-report.md` Documentation and context engineering sections; `.sisyphus/drafts/ai-ready-video-transcript.md` 33:42, 34:08, 35:06, 36:35.

## Slide 6. Before coding: crowding, decomposition, scoping
- **Title:** Before coding: crowding, decomposition, scoping
- **Slide message:** Better results start before implementation, when the task is decomposed, scoped, and crowded against nearby code so the agent works on a small, coherent problem.
- **Leadership takeaway:** Planning discipline is not overhead, it is the control surface that keeps agent output aligned with the existing system.
- **Evidence to show:**
  - Crowding checks whether a proposed change fits local patterns and nearby constraints.
  - Decomposition keeps tasks small enough to avoid context collapse.
  - Scoping limits side effects and clarifies what the agent must not touch.
- **Visual anchor:** Simple pre-coding workflow, crowding to decomposition to bounded execution.
- **Transition:** Once work is shaped correctly, we can define the minimum project assets the environment must provide.
- **Source refs:** `ai-ready-codebase-report.md` Harness Engineering, process guidance, and AI-ready checklist; `.sisyphus/drafts/ai-ready-video-transcript.md` 48:27, 51:39, 54:00, 59:15.

## Slide 7. What must actually be built in the project
- **Title:** What must actually be built in the project
- **Slide message:** AI-readiness is a concrete build program, a small set of artifacts and rules that give agents stable ways to navigate, decide, and verify their work.
- **Leadership takeaway:** Approval is not for abstract AI adoption, it is for a bounded infrastructure package that teams can build and maintain.
- **Evidence to show:**
  - Core artifacts include project maps, glossary, module guidance, ADR access, run commands, and verification entry points.
  - Core rules include guardrails, allowed task classes, and explicit no-go zones.
  - These assets set up the next four slides, architecture, ontology, documentation navigation, and lifecycle.
- **Visual anchor:** One inventory slide listing the minimum AI-ready asset stack.
- **Transition:** The first asset to get right is architecture, because safe autonomy starts with clear boundaries and external contracts.
- **Source refs:** `ai-ready-codebase-report.md` AI-ready checklist; `ai-ready-codebase-report.md` Architecture: Vertical Slices and AI-Friendly Patterns; `ai-ready-codebase-report.md` Documentation: AGENTS.md and context; `ai-ready-codebase-report.md` Guardrails.

## Slide 8. AI-ready architecture: module boundaries and external contracts
- **Title:** AI-ready architecture: module boundaries and external contracts
- **Slide message:** Agents work safely when modules are bounded and contracts are explicit, because they can change internals locally while respecting stable interfaces.
- **Leadership takeaway:** Architecture for agents is less about perfect local code style and more about boundaries that limit blast radius and make verification meaningful.
- **Evidence to show:**
  - Vertical slice locality reduces files-per-change and lowers cross-system drift.
  - Public contracts tell the agent what must remain stable.
  - Structural rules in CI turn architecture from advice into enforceable policy.
- **Visual anchor:** Boundary diagram showing modules, external contracts, and allowed dependency directions.
- **Transition:** Boundaries reduce ambiguity in code, but the agent also needs a shared model of business meaning across the project.
- **Source refs:** `ai-ready-codebase-report.md` Architecture: Vertical Slices and AI-Friendly Patterns; `ai-ready-codebase-report.md` Decision: Do we need to migrate architecture and how; `.sisyphus/drafts/ai-ready-video-transcript.md` 01:56:54.

## Slide 9. Project ontology and domain graphs
- **Title:** Project ontology and domain graphs
- **Slide message:** A project ontology gives agents the domain map they do not get from source files alone, connecting terms, entities, workflows, and dependencies into a navigable meaning layer.
- **Leadership takeaway:** Domain modeling is where expert knowledge becomes reusable system guidance, instead of staying locked in a few senior engineers.
- **Evidence to show:**
  - Glossary reduces ambiguity in overloaded business terms.
  - Domain graphs show relationships the file tree cannot express.
  - Expert time is needed, but the payoff is lower search cost and fewer semantic mistakes.
- **Visual anchor:** Ontology or domain graph, with a few key entity relationships highlighted.
- **Transition:** Once business meaning is modeled, documentation can guide the agent through that knowledge progressively instead of overwhelming it all at once.
- **Source refs:** `ai-ready-codebase-report.md` Documentation and context sections on glossary, intent, and architecture memory; `.sisyphus/drafts/ai-ready-video-transcript.md` 01:05:26, 01:06:18, 01:08:04.

## Slide 10. Memoberry Bank: documentation as a navigation system
- **Title:** Memoberry Bank: documentation as a navigation system
- **Slide message:** Documentation should act as a navigation system with progressive disclosure, so agents can start from the top-level map and descend into the exact detail they need.
- **Leadership takeaway:** Good docs do not just explain the system, they route work through the system with less noise, fewer wrong turns, and better handoffs.
- **Evidence to show:**
  - Top-level docs orient the agent before it reads code.
  - Lower-level docs expose module-specific guidance only when needed.
  - This keeps context focused while preserving access to depth.
- **Visual anchor:** Memoberry-style documentation hierarchy, overview to local detail.
- **Transition:** Navigation only works if the knowledge stays fresh, otherwise the guidance becomes another source of failure.
- **Source refs:** `ai-ready-codebase-report.md` Documentation: AGENTS.md and context; `ai-ready-codebase-report.md` minimum documentation decision; `.sisyphus/drafts/ai-ready-video-transcript.md` 01:35:07.

## Slide 11. Documentation lifecycle and ADR lifecycle
- **Title:** Documentation lifecycle and ADR lifecycle
- **Slide message:** Documentation and ADRs need their own maintenance loop, because stale guidance misleads agents faster than missing guidance.
- **Leadership takeaway:** AI-ready documentation is an operating responsibility, not a one-time writing task, and it must stay consolidated around the current source of truth.
- **Evidence to show:**
  - ADRs preserve why the system is shaped the way it is.
  - Drift between architecture, docs, and code creates false confidence for both humans and agents.
  - Updates should be triggered by architecture change, repeated agent mistakes, and rollout learning.
- **Visual anchor:** Lightweight lifecycle loop, code change to doc update to ADR refresh to source-of-truth consolidation.
- **Transition:** With boundaries, domain knowledge, and living documentation in place, the final control layer is verification.
- **Source refs:** `ai-ready-codebase-report.md` Documentation sections on ADR rationale and minimum documentation; `.sisyphus/drafts/ai-ready-video-transcript.md` 01:47:56, 01:49:40.

## Slide 12. Verification is the bridge to autonomy
- **Title:** Verification is the bridge to autonomy
- **Slide message:** Agents become safe to trust only when every larger task is backed by reliable verification, explicit approval boundaries, and a staged path from assistance to bounded autonomy.
- **Leadership takeaway:** The approval ask is to fund a Year-1 rollout that raises autonomy only where tests, linting, type checks, reviews, and guardrails prove it is safe.
- **Evidence to show:**
  - Verification stack: tests, linting, type checks, structural rules, AI review, and human approval for sensitive changes.
  - Approval boundaries: no silent changes to external APIs, destructive actions, deploys, data migrations, or secrets handling.
  - Year-1 ask: approve baseline measurement, one limited pilot, guardrail enforcement, documentation and context infrastructure, and self-hosted tooling constraints from day one.
- **Visual anchor:** Autonomy ladder tied to verification strength and approval gates.
- **Transition:** End of core deck.
- **Source refs:** `ai-ready-codebase-report.md` Guardrails; `ai-ready-codebase-report.md` Processes with AI; `ai-ready-codebase-report.md` Implementation Roadmap (4 Phases); `ai-ready-codebase-report.md` Metrics and KPI; `ai-ready-codebase-report.md` Risks and mitigation; `ai-ready-codebase-report.md` Self-Hosted tools: comparison and recommendations; `.sisyphus/drafts/ai-ready-video-transcript.md` 01:09:29, 01:11:08, 01:12:59, 01:14:34, 01:21:15.
