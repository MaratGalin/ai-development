# Self-Hosted инструменты: сравнение и рекомендации

## Резюме для принятия решения

**Рекомендация:** Для Enterprise с ограничением «код не покидает периметр» оптимальный стек — **Tabby** (IDE-ассистент) + **Continue** (гибкий frontend) + **vLLM/Ollama** (локальный inference backend). Альтернативы существуют, но требуют компромиссов.

---

## Сравнительная таблица self-hosted инструментов

| Инструмент | Категория | Модель развёртывания | Требования к GPU | Лицензия | Зрелость | Ключевые ограничения для strict on-prem |
|---|---|---|---|---|---|---|
| **Tabby** | IDE-ассистент / self-hosted Copilot alternative | Self-hosted server (Docker/K8s), editor plugins | RTX 4090 для пилота, A100/H100 для высокой конкурентности | Apache-2.0 (OSS), отдельная EE лицензия | **Production-ready** (стабильные релизы) | Требует настройки local model ops и indexing |
| **Continue** | IDE-ассистент + CI интеграция | VS Code/JetBrains extension + self-hosted endpoints (Ollama/vLLM) | Зависит от backend (обычно 1x 24GB+ GPU для пилота) | Apache-2.0 | **Production-used**, быстрое развитие | Многие команды используют внешние API без централизованного контроля |
| **Cody (Sourcegraph Enterprise)** | IDE + CLI с enterprise context | Self-hosted Sourcegraph Enterprise + model config | Если Cody Gateway — не требует GPU; self-hosted model — требует GPU | Проприетарная (Sourcegraph EE) | **Enterprise production** | "Fully on-prem" зависит от пути model-provider и настройки policy |
| **Kilo Code** | IDE + CLI агент | Open-source; подключается к local endpoints | Backend-зависим | MIT | **Active, high velocity** | Часто API-first; strict perimeter требует policy enforcement |
| **OpenCode** | CLI агент | Local terminal agent; поддерживает LOCAL_ENDPOINT | Backend-зависим | MIT | **Early / transitioned** (оригинальный repo archived) | Риск долгосрочной поддержки; migration path неясен |
| **Claude Code** | CLI/IDE агент | Anthropic surfaces + enterprise controls | Не требует local GPU (provider-hosted) | Проприетарная | **Enterprise-ready** | **Не fully self-hosted inference**; требует enterprise controls для compliance |
| **PR-Agent** | Code review бот | Self-hosted via GitHub Action/CLI/Docker/webhook | Низкие (inference backend определяет GPU) | AGPL-3.0 | Широко используется | AGPL лицензия; качество зависит от LLM backend |
| **Qodo Cover** | Test generation | CLI/CI интеграция | Низкие (model backend определяет GPU) | AGPL-3.0 | **Maintenance risk** (repo не поддерживается) | Статус поддержки и AGPL constraints |

---

## Local LLM бэкенды (для perimeter-safe deployment)

| Бэкенд | Лучше всего подходит | Инфраструктура | Enterprise замечания |
|---|---|---|---|
| **Ollama** | Быстрый локальный rollout, пилоты | CPU или single-GPU; Docker images с CPU/NVIDIA/AMD | Сильная сторона — скорость пилота; меньше контроля на hyperscale чем vLLM |
| **vLLM** | High-throughput shared inference | GPU-centric serving; сильная batching/throughput | Лучше для centralized enterprise inference tier; выше SRE/K8s complexity |
| **llama.cpp** | Edge/on-device/air-gapped | Может работать CPU-only; поддерживает CUDA/Metal/Vulkan | Отлично для hard perimeter и low-footprint deployments; ниже throughput для multi-user |

### Практические GPU рекомендации

- **Пилот (10–30 разработчиков):** 1–2 inference nodes, RTX 4090 / L40S
- **Департамент (50–150 разработчиков):** Shared inference service, A100 80GB / H100
- **Enterprise platform (100+ concurrent users):** Multi-node vLLM с autoscaling, H100/A100 pools

---

## Категорийные рекомендации

### A. IDE-ассистенты

**Primary self-hosted candidates:**
- **Tabby** — наиболее прямой on-prem Copilot alternative
- **Continue** — наиболее гибкий frontend, backend-agnostic
- **Cody Enterprise** — если Sourcegraph уже strategic platform

### B. CLI-агенты

**Primary perimeter-safe pattern:**
- **Kilo/OpenCode-style CLI** или equivalent agent frontends, подключённые к **local OpenAI-compatible endpoints** (vLLM/Ollama gateway)

**Conditional/non-primary:**
- **Codex CLI / Claude Code** — только если governance принимает managed-provider path с approved gateway controls

### C. Code review боты

- **PR-Agent** для self-hosted PR analysis в CI
- Использовать local model gateway для сохранения diffs/code в периметре

### D. Test generation

- **Qodo Cover** концептуально подходит, но maintenance status требует caution
- Предпочесть actively maintained alternatives для long-term support

---

## Evaluation rubric (weighted, enterprise-focused)

| Критерий | Вес | Что значит "хорошо" |
|---|---|---:|:---|
| **Data residency / perimeter compliance** | **25%** | Full on-prem operation, auditable no-exfil path, policy enforcement |
| **Integration with existing SDLC** | **15%** | IDE/CI/VCS integration с низкой стоимостью change-management |
| **Model backend flexibility** | **12%** | Native support для Ollama/vLLM/OpenAI-compatible endpoints |
| **Operational maturity** | **12%** | Stable releases, active maintainers, clear upgrade path |
| **Security/governance controls** | **10%** | RBAC, logs, policy, approvals, admin controls |
| **Developer experience / adoption speed** | **10%** | Good UX, low friction onboarding, low prompt overhead |
| **Performance at team scale** | **8%** | Acceptable latency при realistic concurrency |
| **License and legal fit** | **8%** | License совместимая с enterprise policy (включая AGPL review) |

### Pass/fail gates перед weighted scoring

1. **Perimeter compliance gate:** Инструмент должен поддерживать полностью локальную работу без обязательных внешних вызовов.
2. **Active maintenance gate:** Публичный репозиторий с активностью в последние 3 месяца или enterprise vendor support contract.
3. **License compatibility gate:** License проходит legal review (особое внимание к AGPL в enterprise контексте).

---

## Рекомендуемые стеки (варианты)

### Минимальный стек (пилот, быстрый старт)
- **IDE:** Continue + Ollama на рабочих станциях разработчиков
- **Backend:** Ollama с Llama 3.1/CodeLlama
- **GPU:** RTX 4090 или CPU-only для пилота
- **Cost:** $3-5k на GPU, 0 на лицензии
- **Time to value:** 1-2 дня

### Оптимальный стек (департамент, продакшн)
- **IDE:** Tabby (server) + Continue (frontend)
- **Backend:** vLLM на shared inference cluster
- **GPU:** A100 80GB x 2-4 для команды 50-100 человек
- **Code review:** PR-Agent + local model gateway
- **Cost:** $50-100k на GPU + $10-20k на инфраструктуру
- **Time to value:** 2-4 недели

### Максимальный стек (enterprise platform)
- **IDE:** Tabby Enterprise + Cody (если Sourcegraph уже используется)
- **Backend:** Multi-node vLLM с autoscaling, model routing
- **GPU:** H100/A100 pools, 8+ GPUs
- **Code review:** PR-Agent с централизованным gateway
- **Test generation:** Self-hosted alternatives к Qodo Cover
- **Cost:** $200-500k на GPU + $50-100k на инфраструктуру + лицензии
- **Time to value:** 2-3 месяца

---

## Решение: Какой стек выбрать и сколько это стоит

### Для начала (Year 1)

**Рекомендация:** Начать с **оптимального стека** — он даёт правильный баланс между time-to-value и enterprise readiness.

**Последовательность:**
1. Пилот с Continue + Ollama (1-2 недели, proof of concept)
2. Переход на Tabby + vLLM для production (2-4 недели)
3. Добавление PR-Agent для code review (1-2 недели)
4. Масштабирование на enterprise platform по мере роста команды

**Budget Year 1:**
- GPU infrastructure: $50-150k (зависит от размера команды)
- Software licenses: $0-30k (Tabby OSS бесплатен, Sourcegraph/Cody платный)
- SRE/DevOps effort: 0.5-1 FTE на 3-6 месяцев
- Training and adoption: включено в общий training budget

### Trade-offs

| Подход | Pros | Cons |
|---|---|---|
| **Минимальный** | Быстрый старт, низкая стоимость | Не масштабируется, performance issues при росте команды |
| **Оптимальный** | Правильный баланс, production-ready | Требует инвестиций в GPU и SRE |
| **Максимальный** | Enterprise-grade, полный контроль | Высокая стоимость, длительный time-to-value |

**Вывод:** Для Enterprise с 100+ разработчиками оптимальный стек — лучший выбор для Year 1. Минимальный подходит только для proof of concept, максимальный — для mature organizations с существующей ML Ops инфраструктурой.