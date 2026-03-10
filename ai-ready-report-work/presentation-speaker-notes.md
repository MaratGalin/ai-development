# AI-Ready Presentation Speaker Notes

## Slide 1. AI-Ready Codebase: not about the model, about the environment
- **Spoken notes:** Open with the decision, not the technology trend. Our recommendation is to approve a Year-1 AI-ready rollout now, because the main bottleneck is no longer raw model capability. The bottleneck is whether the engineering environment lets agents navigate, act safely, and verify their work. This frames the deck as an operating-model decision, not a tool-shopping exercise.
- **Leadership takeaway:** Fund the environment, guardrails, and pilot structure now, instead of letting ad hoc AI use expand without control.
- **Why this slide is here:** It sets the approval frame at the start so the rest of the deck reads as support for one decision.
- **Transition:** To make that decision credible, we first need to see what agent work looks like when the environment is not prepared.

## Slide 2. What happens without preparation
- **Spoken notes:** In an unprepared codebase, the agent spends most of its effort trying to figure out where it is, what matters, and which files are safe to touch. That means token budget goes into search, repeated reading, and wrong turns, not into execution. What looks fast in a demo turns into drift, rework, and fragile output in a real project.
- **Leadership takeaway:** Unstructured AI adoption creates hidden cost, not neutral experimentation.
- **Why this slide is here:** After the opening decision frame, we show the failure pattern that makes action necessary.
- **Visual reading:** First, notice how much of the path is exploration rather than implementation. Second, notice the waste pattern, repeated scanning, context fill, and loss of task focus.
- **Transition:** The next slide shows that the model does not need to become smarter for results to improve, the project needs to become easier to navigate.

## Slide 3. What changes after preparation
- **Spoken notes:** Once the project gives agents a map, a glossary, bounded tasks, and clear entry points, the workflow changes. The agent reads less irrelevant material, gets to the right area faster, and spends more of the session doing the intended work. The gain is not just speed. It is predictability, because the path through the codebase becomes more repeatable.
- **Leadership takeaway:** Preparation is the multiplier that turns model capability into dependable delivery.
- **Why this slide is here:** It pairs directly with slide 2 so leaders can compare environment failure against environment preparation.
- **Visual reading:** First, notice the shorter path from task start to execution. Second, notice that structure reduces wandering, not by adding more prompt text, but by improving navigation.
- **Transition:** That contrast raises the next question, why can't we solve the same problem by simply giving the model more context?

## Slide 4. Why long context does not save us: attention limits
- **Spoken notes:** Bigger context windows help at the margin, but they do not remove the core constraint. Attention still has to spread across everything in the prompt, and the more we stuff in, the thinner that attention gets. When sessions keep compacting, the model also loses fidelity about earlier reasoning and project state. So the answer is not to keep dumping repository data into the conversation.
- **Leadership takeaway:** We need to protect scarce model attention, not assume long context makes structure unnecessary.
- **Why this slide is here:** It explains the mechanism behind the failure pattern, so the audience does not misdiagnose the problem as a temporary model issue.
- **Visual reading:** First, notice that free working room inside context is limited and valuable. Second, notice how compaction trades apparent continuity for loss of detail over time.
- **Transition:** If attention is finite, the right response is to assemble the right context on demand.

## Slide 5. Dynamic Context Layer
- **Spoken notes:** This is the core systems idea. Instead of pasting large chunks of the repository into every session, we build a context layer that can locate relevant files, contracts, docs, and checks for the specific task at hand. That turns context from a storage problem into a retrieval and composition problem. It also leaves more room for the agent to reason and execute.
- **Leadership takeaway:** The highest-leverage investment is task-aware context assembly, not bigger prompts or more hint files alone.
- **Why this slide is here:** After naming the attention constraint, we show the direct system response that makes agent work scale.
- **Visual reading:** First, notice the flow from task request to selected knowledge, not from repository bulk to prompt dump. Second, notice that the layer combines guidance, code locations, and verification paths into one assembled package.
- **Transition:** Better context helps, but agents still fail if the task itself is too broad or poorly shaped before coding begins.

## Slide 6. Before coding: crowding, decomposition, scoping
- **Spoken notes:** Good agent work starts before implementation. Crowding checks how a change fits local patterns and nearby constraints. Decomposition breaks the job into pieces small enough to keep attention focused. Scoping defines what the agent should touch, and just as important, what it must not touch. This is how we reduce avoidable drift before code is written.
- **Leadership takeaway:** Planning discipline is part of the control system, not administrative overhead.
- **Why this slide is here:** It completes the middle mechanism sequence, attention limit, dynamic context, then work shaping before execution.
- **Visual reading:** First, notice the order, understand local fit, split the task, then execute inside bounds. Second, notice that each step narrows risk before the agent changes code.
- **Transition:** Once work is shaped correctly, we can define the minimum project assets the environment must provide.

## Slide 7. What must actually be built in the project
- **Spoken notes:** AI-readiness is not a slogan. It is a small but concrete build program. Teams need project maps, glossary and domain terms, module guidance, ADR access, run and verification commands, and guardrails that define safe task classes and no-go zones. This is the practical package leadership is being asked to fund.
- **Leadership takeaway:** Approval is for a bounded infrastructure layer that teams can build and maintain, not for abstract AI experimentation.
- **Why this slide is here:** It turns the prior concepts into a concrete asset inventory before we unpack the most important layers one by one.
- **Visual reading:** First, notice the stack as a minimum operating set, not a wish list. Second, notice that the inventory points forward to architecture, ontology, documentation navigation, and lifecycle.
- **Transition:** The first layer to get right is architecture, because safe autonomy starts with clear boundaries.

## Slide 8. AI-ready architecture: module boundaries and external contracts
- **Spoken notes:** Agents work best when they can change code locally while knowing exactly which interfaces must remain stable. Clear module boundaries reduce blast radius, and explicit external contracts tell the agent what cannot be broken silently. That matters more than perfect local elegance, because the real goal is bounded change plus meaningful verification.
- **Leadership takeaway:** Architecture for agents is about limiting risk through boundaries and contracts.
- **Why this slide is here:** Once the asset inventory is clear, architecture comes first because it defines the safe shape of change.
- **Visual reading:** First, notice the module edges and the approved dependency directions. Second, notice that contracts sit at the points where autonomy becomes risky, which is why they deserve more weight than local code aesthetics.
- **Transition:** Boundaries solve structural ambiguity, but agents also need a shared model of business meaning.

## Slide 9. Project ontology and domain graphs
- **Spoken notes:** Source files alone do not explain business meaning. An ontology and domain graph connect terms, entities, workflows, and dependencies into a model the agent can navigate. This is also where expert knowledge stops living only in a few senior engineers and becomes reusable guidance for the wider system.
- **Leadership takeaway:** Domain modeling lowers semantic mistakes by turning expert context into shared infrastructure.
- **Why this slide is here:** After structural boundaries, the deck moves to semantic boundaries, how the project explains meaning, not just code layout.
- **Visual reading:** First, notice the key entities and how they relate, not just the number of nodes. Second, notice that the graph captures relationships the file tree cannot express.
- **Transition:** Once meaning is modeled, documentation can guide the agent through that knowledge progressively instead of overwhelming it all at once.

## Slide 10. Memoberry Bank: documentation as a navigation system
- **Spoken notes:** Documentation should guide movement through the system, not just describe it. The top layer gives orientation, then lower layers reveal module-specific detail only when the task needs it. That progressive disclosure keeps sessions focused while still preserving access to depth. In practice, good documentation reduces wrong turns and improves handoffs between people and agents.
- **Leadership takeaway:** Documentation is part of navigation infrastructure, not a passive reference library.
- **Why this slide is here:** After the ontology slide explains meaning, this slide shows how meaning is delivered to the agent in usable layers.
- **Visual reading:** First, notice the top-down path from overview to local detail. Second, notice that the point is controlled descent through the knowledge base, not dumping all documentation into context.
- **Transition:** Navigation only helps if the knowledge stays current, otherwise documentation becomes another source of failure.

## Slide 11. Documentation lifecycle and ADR lifecycle
- **Spoken notes:** Stale guidance is often worse than missing guidance, because it creates false confidence. Documentation and ADRs need a maintenance loop tied to architecture change, repeated agent mistakes, and rollout learning. ADRs preserve why the system was shaped a certain way, and that rationale needs to stay consolidated around the current source of truth rather than scattered across old files and memory.
- **Leadership takeaway:** AI-ready documentation is an operating responsibility with freshness rules, not a one-time cleanup task.
- **Why this slide is here:** After documentation-as-navigation, we show the governance loop that keeps that navigation trustworthy over time.
- **Visual reading:** First, notice the lifecycle loop, change in code should trigger updates in docs and decisions. Second, notice that ADR consolidation protects architectural intent from drift.
- **Transition:** With structure, meaning, navigation, and freshness in place, the final control layer is verification.

## Slide 12. Verification is the bridge to autonomy
- **Spoken notes:** This is where the deck closes the decision. Agents become safe to trust only when larger tasks are backed by tests, linting, type checks, structural rules, review paths, and clear approval boundaries. Year 1 should raise autonomy only where verification proves it is safe. That means baseline measurement, one limited pilot, enforced guardrails, documentation and context infrastructure, and self-hosted constraints from day one.
- **Leadership takeaway:** Approve a staged rollout where autonomy grows only behind proof, not optimism.
- **Why this slide is here:** The full narrative resolves here, from failure pattern to control system to the final approval ask.
- **Visual reading:** First, notice that autonomy rises only with verification strength, not with model confidence. Second, notice the explicit red lines, no silent external API changes, destructive actions, deploys, data migrations, or secrets handling without approval.
- **Transition:** End of core deck.
