# Task 1 — Self-Hosted / On-Premise AI Coding Tools for Enterprise (100+ devs)

## Scope and assumptions

- Constraint: **source code must not leave company perimeter**.
- Goal: compare practical tooling options for IDE assistants, CLI agents, code review bots, and test generation.
- Important: several popular tools (Claude Code, Codex CLI) are included per request, but are flagged where they are **not fully self-hosted** under strict air-gapped policy.

---

## 1) Comparative table (shortlist)

| Tool | Category | Deployment model | Typical GPU/compute profile | License | Maturity | Key limitations for strict on-prem |
|---|---|---|---|---|---|---|
| **Tabby** | IDE assistant / self-hosted Copilot alternative | Self-hosted server (Docker/K8s), editor plugins | Supports consumer GPUs; practical baseline: 1x RTX 4090 for pilot, A100/H100 for higher concurrency | Apache-2.0 for OSS parts; separate EE licensing for `ee/` components | **Production-ready** (stable releases, long release history) | Requires local model ops and indexing tuning; quality depends on selected local models |
| **Continue** | IDE assistant + checks in CI | VS Code/JetBrains extension + self-hosted model endpoints (Ollama/vLLM/OpenAI-compatible) | GPU depends on backend model (often 1x 24GB+ GPU for pilot); can run small local models CPU-only with lower quality | Apache-2.0 | **Production-used**, fast-moving | Core extension is local-friendly, but many teams still rely on external model APIs unless centrally enforced |
| **Cody (Sourcegraph Enterprise)** | IDE + CLI assistant with enterprise context | Self-hosted Sourcegraph Enterprise + model config (Cody Gateway or BYOK/provider overrides) | If using Cody Gateway/BYOK APIs: no local inference GPU required; if self-hosting model endpoints, GPU profile shifts to backend | Proprietary enterprise product (Sourcegraph EE) | **Enterprise production** | Strong enterprise feature set, but “fully on-prem/no-exfil” depends on model-provider path and policy setup |
| **Kilo Code** | IDE + CLI agent | Open-source agent tooling; typically connected to external providers, can be adapted to local endpoints | Backend-dependent (same as Continue/OpenCode pattern) | MIT | **Active, high velocity** | Operational model still often API-first; strict perimeter requires hard policy controls and local backend enforcement |
| **OpenCode** (archived, moved to Crush) | CLI agent | Local terminal agent; supports `LOCAL_ENDPOINT` (OpenAI-like) | Backend-dependent (local GPU if using local model server) | MIT | **Early / transitioned** (original repo archived) | Original repo archived; migration path and long-term support risk |
| **Codex CLI** | CLI coding agent | Local CLI client; model inference primarily via OpenAI/ChatGPT ecosystem | No local inference GPU required if using OpenAI endpoints | Apache-2.0 (client) | **Very active** | **Not a pure self-hosted model stack**; strict no-exfil posture is difficult without approved gateway/proxy design |
| **Claude Code** | CLI/IDE coding agent | Anthropic surfaces + enterprise controls, cloud/provider integrations, optional gateways/proxies | No local inference GPU required (provider-hosted inference) | Proprietary | **Enterprise-ready** | **Not fully self-hosted inference**; can fit regulated environments via enterprise controls, but not pure air-gapped local LLM |
| **PR-Agent** | Code review bot | Self-hosted via GitHub Action/CLI/Docker/webhook | Usually low compute itself; inference backend determines GPU | AGPL-3.0 | **Widely used**, community-maintained legacy project | Licensing (AGPL), plus quality/latency tied to chosen LLM backend |
| **Qodo Cover (qodo-cover)** | Test generation | CLI/CI integration, self-hostable execution | Similar to PR-Agent: orchestration low; model backend dictates GPU | AGPL-3.0 | **Maintenance risk** (repo states no longer maintained) | Maintenance status and AGPL constraints; verify viability before enterprise rollout |

### Required tools explicitly evaluated

- Tabby ML ✅
- Continue.dev ✅
- Cody (Sourcegraph) ✅
- Claude Code self-hosted feasibility ✅
- Codex CLI ✅
- OpenCode ✅
- Kilo Code ✅

---

## 2) Local LLM backends (for perimeter-safe deployment)

| Backend | Best fit | Infra profile | Enterprise notes |
|---|---|---|---|
| **Ollama** | Fast local rollout, developer workstation + small team pilots | CPU or single-GPU easy start; Docker images include CPU/NVIDIA/AMD paths | Strong for pilot/adoption speed; less control at hyperscale than vLLM |
| **vLLM** | High-throughput shared inference (team/organization level) | GPU-centric serving; strong batching/throughput; CPU mode exists with tradeoffs | Best for centralized enterprise inference tier; higher SRE/K8s complexity |
| **llama.cpp** | Edge/on-device/air-gapped, quantized inference | Can run CPU-only; also supports CUDA/Metal/Vulkan/HIP backends | Excellent for hard perimeter and low-footprint deployments, but lower throughput for large multi-user workloads |

### Practical GPU guidance (planning, not benchmark claims)

- **Pilot (10–30 developers):**
  - 1–2 inference nodes, typically RTX 4090 / L40S class for coding-sized models.
- **Department (50–150 developers):**
  - Shared inference service; A100 80GB / H100 class becomes practical for latency + concurrency.
- **Enterprise shared platform (100+ active concurrent users):**
  - Multi-node vLLM with autoscaling, model routing, and cache strategy; H100/A100 pools are typical.

---

## 3) Category coverage recommendation (what to use for what)

### A. IDE assistants

Primary self-hosted candidates:
- **Tabby** (most direct on-prem Copilot alternative)
- **Continue** (most flexible frontend, backend-agnostic)
- **Cody Enterprise** (if Sourcegraph already strategic platform)

### B. CLI agents

Primary perimeter-safe pattern:
- **Kilo/OpenCode-style CLI** or equivalent agent frontends connected to **local OpenAI-compatible endpoints** (vLLM/Ollama gateway).

Conditional/non-primary under strict policy:
- **Codex CLI / Claude Code** only if governance accepts managed-provider path and approved gateway controls.

### C. Code review bots

- **PR-Agent** for self-hosted PR analysis in CI.
- Use local model gateway to keep diffs/code in perimeter.

### D. Test generation

- **Qodo Cover** conceptually fits, but maintenance status requires caution.
- Prefer actively maintained alternatives if long-term support is mandatory.

---

## 4) Evaluation rubric (weighted, enterprise-focused)

Use this weighted rubric for final tool selection (score each criterion 1–5).

| Criterion | Weight | What “good” looks like |
|---|---:|---|
| **Data residency / perimeter compliance** | **25%** | Full on-prem operation, auditable no-exfil path, policy enforcement |
| **Integration with existing SDLC** | **15%** | IDE/CI/VCS integration with low change-management cost |
| **Model backend flexibility** | **12%** | Native support for Ollama/vLLM/OpenAI-compatible endpoints |
| **Operational maturity** | **12%** | Stable releases, active maintainers, clear upgrade path |
| **Security/governance controls** | **10%** | RBAC, logs, policy, approvals, admin controls |
| **Developer experience / adoption speed** | **10%** | Good UX, low friction onboarding, low prompt overhead |
| **Performance at team scale** | **8%** | Acceptable latency under realistic concurrency |
| **License and legal fit** | **8%** | License compatible with enterprise policy (incl. AGPL review where needed) |

### Recommended pass/fail gates before weighted scoring

1. Must support on-prem deployment path (or approved enclave/gateway exception).
2. Must provide auditability and admin governance.
3. Must integrate with existing auth and CI controls.

---

## 5) Cost analysis (GPU + SRE + K8s)

## 5.1 Cost components

1. **Inference infrastructure**
   - GPU servers (CAPEX or reserved cloud capacity)
   - Storage for models/artifacts
   - Network and observability overhead

2. **Platform/SRE staffing**
   - Initial rollout: platform engineer(s) for serving, gateway, policy, observability
   - Ongoing: patching, incident handling, capacity planning, model lifecycle

3. **K8s/platform maturity cost**
   - If K8s maturity is low, hidden cost is high (operational toil, slower rollout)
   - vLLM at scale strongly benefits from mature Kubernetes + autoscaling + SLOs

4. **Tool licensing and legal/compliance**
   - OSS is not zero-cost (support, maintenance, legal review)
   - AGPL tools can introduce legal/process overhead

## 5.2 Practical sizing scenarios

- **Scenario A — conservative pilot (20–40 dev):**
  - 1–2 GPU nodes + lightweight gateway + one shared IDE assistant.
  - Goal: prove value with minimal platform complexity.

- **Scenario B — multi-team rollout (100+ dev):**
  - Central inference tier (vLLM), model routing, HA gateway, observability stack.
  - Requires explicit SRE ownership and capacity planning.

- **Scenario C — strict air-gapped segments:**
  - More llama.cpp/Ollama edge cells + selective central high-throughput cluster.
  - Tradeoff: strongest compliance vs lower average model quality/throughput in edge zones.

## 5.3 Cost-risk tradeoff summary

- Lowest initial cost ≠ lowest total cost.
- Under-investing in SRE/governance usually causes:
  - shadow SaaS fallback,
  - unstable latency,
  - policy bypasses,
  - and failed scale phase.

---

## 6) Recommended strategy for this program (strict perimeter first)

### Primary recommendation (Phase 1)

1. **IDE layer:** Continue + Tabby pilot in 2 teams.
2. **Inference layer:** Ollama for fast pilot, with migration path to vLLM for shared production serving.
3. **Automation:** PR-Agent for code review augmentation in CI.
4. **Governance:** enforce local endpoints only; block unmanaged external providers.

### Phase 2 (scale)

1. Consolidate on vLLM-backed shared inference.
2. Standardize model catalog and routing policy.
3. Add SLOs (p95 latency, availability, queue depth, cost per 1k accepted tokens).
4. Re-evaluate Cody Enterprise if Sourcegraph platform standardization is strategic.

### Tools to treat as conditional (not primary for strict on-prem)

- **Claude Code** and **Codex CLI**: evaluate only with explicit enterprise exception and gateway controls, since they are not pure self-hosted inference by default.

---

## 7) Decision / Recommendation / Trade-offs

## Decision

Adopt a **self-hosted-first stack** centered on **Continue/Tabby + local inference backends (Ollama→vLLM)**, with **PR-Agent** for CI review automation.

## Recommendation

- Start with a 4–6 week controlled pilot on two teams.
- Measure adoption + quality gates before broad rollout.
- Build the inference tier as a platform product (not a side project).

## Trade-offs

- You gain strongest compliance and control, but assume higher platform ownership cost.
- You reduce vendor lock-in risk, but must invest in SRE/model operations competency.
- Some high-polish SaaS experiences may be unavailable under strict perimeter policy.

---

## Sources used (key)

- Tabby repository/docs (self-hosted positioning, releases, license).
- Continue repository/docs (Apache-2.0, local/offline guidance, Ollama/OpenAI-compatible provider config).
- Sourcegraph Cody docs (Enterprise enablement, model configuration, self-hosted options).
- Anthropic Claude Code docs (enterprise deployment options, gateways/proxies, third-party integrations).
- OpenAI Codex repository/docs (CLI maturity, enterprise admin setup).
- OpenCode repository (archived status, local endpoint support).
- Kilo repositories (active project + older archived/moved repository).
- PR-Agent and Qodo Cover repositories (category coverage, deployment patterns, AGPL licensing, maintenance signals).
- vLLM / Ollama / llama.cpp official docs (deployment modes, CPU/GPU support, serving patterns).
