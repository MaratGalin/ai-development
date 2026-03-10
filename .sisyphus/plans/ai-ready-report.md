# AI-Ready Codebase: Аналитический отчёт и план внедрения для Enterprise

## TL;DR

> **Цель**: Написать комплексный аналитический отчёт для CTO/VP Engineering крупной компании (100+ разработчиков) с конкретными практиками превращения кодовой базы в AI-Ready, и пошаговый план внедрения AI-инструментов в процессы разработки.
> 
> **Deliverables**:
> - Аналитический отчёт на русском языке (~30-40 стр. markdown): индустриальный контекст, практики, roadmap, метрики, риски
> - Приложения: чеклисты, шаблоны AGENTS.md, сравнительные таблицы инструментов (self-hosted)
> - Каждый раздел отчёта завершается блоком «Решение / Рекомендация / Trade-offs» для CTO
> 
> **Estimated Effort**: Large
> **Parallel Execution**: YES — 4 волны
> **Critical Path**: T1 (исследование self-hosted) → T5 (архитектура) → T10 (roadmap) → T15 (сборка) → F1-F4

---

## Context

### Original Request
Пользователь запросил исследование "Как сделать кодовую базу AI-Ready: конкретные практики и рекомендации" с целью подготовить отчёт для руководства и принять решения по внедрению AI в Enterprise-компании.

### Interview Summary
**Key Discussions**:
- **Формат**: Два deliverable — аналитический отчёт + план внедрения (work plan)
- **Компания**: Enterprise, 100+ разработчиков, начальная стадия AI-adoption
- **Безопасность**: Код НЕ может покидать периметр компании — только self-hosted/on-premise решения
- **Аудитория**: CTO / VP Engineering
- **Решения**: изменение процессов, подготовка кода, обучение команды, измерение эффекта
- **Глубина**: Полный отчёт — executive summary + детальные практики + примеры
- **Язык**: Русский + английские технические термины

**Research Findings (15+ источников)**:
- **OpenAI Harness Engineering**: 3 инженера → 1M LOC, 0 ручного кода, 3.5 PR/день, 10x ускорение
- **Addy Osmani**: specs-before-code, small chunks, context packing, CLAUDE.md, human-in-the-loop
- **Vertical Slice Architecture**: AI-friendliest pattern (feature-based vs layer-based)
- **AGENTS.md/CLAUDE.md**: HOW/WHY/WHAT структура для onboarding AI-агентов
- **Enterprise stats**: 95% пилотов не масштабируются, 56% CEO получают «ничего» от AI
- **Self-hosted constraint**: критическое влияние на выбор инструментов

### Metis Review
**Identified Gaps (addressed)**:
- Отчёт рискует стать «блог-контентом» → каждый раздел заканчивается блоком решений
- Scope creep в «построить платформу» → ограничено Year-1 scope
- Отсутствие baseline метрик → включён раздел про сбор baseline до внедрения
- Security backlash → включена модель угроз и data handling policy
- Архитектурные рекомендации слишком абсолютны → позиционирование как «направление», не «единственный путь»
- Edge cases: air-gapped среды, регулируемый код, legacy monolith, polyglot stack, IP/лицензирование

---

## Work Objectives

### Core Objective
Создать executive-grade аналитический отчёт на русском языке, который позволит CTO/VP Engineering принять обоснованные решения по систематическому внедрению AI-инструментов в процессы разработки Enterprise-компании с учётом ограничения «код не покидает периметр».

### Concrete Deliverables
- `ai-ready-codebase-report.md` — основной аналитический отчёт (~30-40 стр.)
- Приложения внутри отчёта: шаблон AGENTS.md, AI Readiness Checklist, сравнительная таблица self-hosted инструментов, пример Vertical Slice структуры, шаблон метрик

### Definition of Done
- [x] Отчёт содержит ≥ 8 основных разделов
- [x] Язык: русский текст + английские технические термины (AI-ready, LLM, guardrails, Vertical Slice, DORA)
- [x] Каждый раздел завершается блоком «Решение / Рекомендация / Trade-offs»
- [x] Self-hosted/on-premise ограничение явно учтено во всех рекомендациях по инструментам
- [x] ≥ 10 явных decision points для CTO
- [x] Roadmap содержит фазы с критериями выхода и ответственными
- [x] Все числа и кейсы подкреплены ссылками на источники

### Must Have
- Executive Summary на 1 странице
- Индустриальный контекст: реальные кейсы (OpenAI, Stripe, Anthropic) + статистика (Gartner, McKinsey)
- Определение AI-Ready Codebase с конкретными характеристиками
- 5+ конкретных практик (архитектура, документация, guardrails, процессы, context engineering)
- Дорожная карта внедрения (4 фазы: аудит → cleanup → пилот → масштабирование)
- Метрики и KPI для измерения эффекта
- Раздел рисков и митигации (включая security, human factors, technical debt amplification)
- Рекомендации по self-hosted инструментам (с учётом «код не покидает периметр»)
- Приложения с готовыми к использованию шаблонами

### Must NOT Have (Guardrails)
- Никакого vendor hype — объективные сравнения с trade-offs
- Никаких непроверяемых claims — все цифры с источниками
- Никаких рекомендаций «перепишите весь монолит» — только инкрементальный подход
- Никаких SaaS-only решений — всё проверено на self-hosted совместимость
- Никакого расширения scope в «AI-стратегию всей компании» (sales, HR, support) — только разработка
- Никакого глубокого бенчмарка LLM-моделей — только shortlist + evaluation rubric
- Никакого построения RAG-платформы или prompt gateway — это отдельный проект
- Отчёт НЕ должен читаться как перевод блог-постов — это CTO decision memo

---

## Verification Strategy

> **ZERO HUMAN INTERVENTION** — ALL verification is agent-executed. No exceptions.

### Test Decision
- **Infrastructure exists**: N/A (writing task)
- **Automated tests**: None (document, not code)
- **Framework**: N/A

### QA Policy
Каждая задача включает QA-сценарии для проверки качества написанного раздела:
- **Структура**: наличие обязательных подразделов
- **Язык**: русский текст + английские термины
- **Decision content**: наличие блоков решений
- **Self-hosted coverage**: упоминание on-prem ограничений
- **Source attribution**: ссылки на источники
Evidence сохраняется в `.sisyphus/evidence/task-{N}-{scenario}.txt`

---

## Execution Strategy

### Parallel Execution Waves

```
Wave 1 (Start Immediately — исследование + foundation):
├── Task 1: Исследовать self-hosted AI-инструменты [deep]
├── Task 2: Написать Executive Summary [writing]
├── Task 3: Написать раздел «Индустриальный контекст» [writing]
└── Task 4: Написать раздел «Что такое AI-Ready Codebase» [writing]

Wave 2 (After Wave 1 — core practices, MAX PARALLEL):
├── Task 5: Написать разд��л «Архитектура: Vertical Slices» [writing]
├── Task 6: Написать раздел «Документация: AGENTS.md и контекст» [writing]
├── Task 7: Написать раздел «Инженерные Guardrails» [writing]
├── Task 8: Написать раздел «Процессы разработки с AI» [writing]
└── Task 9: Написать раздел «Обучение команды и новые роли» [writing]

Wave 3 (After Wave 2 — implementation + measurement):
├── Task 10: Написать раздел «Дорожная карта внедрения (4 фазы)» [writing]
├── Task 11: Написать раздел «Метрики и KPI» [writing]
├── Task 12: Написать раздел «Риски и митигация» [writing]
├── Task 13: Написать раздел «Self-Hosted инструменты» (depends: T1) [writing]
└── Task 14: Написать приложения (чеклисты, шаблоны, таблицы) [writing]

Wave 4 (After Wave 3 — assembly + review):
├── Task 15: Собрать финальный отчёт из всех разделов [writing]
└── Task 16: Вычитка и polish финального отчёта [writing]

Wave FINAL (After ALL tasks — independent review, 4 parallel):
├── Task F1: Аудит соответствия плану [deep]
├── Task F2: Проверка качества текста и структуры [writing]
├── Task F3: Проверка decision content и source attribution [deep]
└── Task F4: Проверка self-hosted compliance [deep]

Critical Path: T1 → T13 → T15 → F1-F4
Parallel Speedup: ~65% быстрее последовательного выполнения
Max Concurrent: 5 (Waves 2 & 3)
```

### Dependency Matrix

| Task | Depends On | Blocks | Wave |
|------|-----------|--------|------|
| 1 | — | 13 | 1 |
| 2 | — | 15 | 1 |
| 3 | — | 15 | 1 |
| 4 | — | 5,6,7,8,9,15 | 1 |
| 5 | 4 | 10,15 | 2 |
| 6 | 4 | 10,14,15 | 2 |
| 7 | 4 | 10,15 | 2 |
| 8 | 4 | 10,15 | 2 |
| 9 | 4 | 10,15 | 2 |
| 10 | 5,6,7,8,9 | 15 | 3 |
| 11 | — | 15 | 3 |
| 12 | — | 15 | 3 |
| 13 | 1 | 15 | 3 |
| 14 | 6 | 15 | 3 |
| 15 | 2,3,4,5-14 | 16, F1-F4 | 4 |
| 16 | 15 | F1-F4 | 4 |
| F1-F4 | 16 | — | FINAL |

### Agent Dispatch Summary

- **Wave 1**: **4** — T1 → `deep`, T2-T4 → `writing`
- **Wave 2**: **5** — T5-T9 → `writing`
- **Wave 3**: **5** — T10-T14 → `writing`
- **Wave 4**: **2** — T15, T16 → `writing`
- **FINAL**: **4** — F1 → `deep`, F2 → `writing`, F3 → `deep`, F4 → `deep`

---

## TODOs

> Каждая задача — написание одного раздела отчёта.
> КАЖДАЯ задача содержит: контент-план, источники, QA-сценарии.
> Язык всех разделов: русский + английские технические термины.

- [x] 1. Исследовать self-hosted AI-инструменты для Enterprise

  **What to do**:
  - Провести глубокое исследование AI-инструментов разработки, которые можно развернуть on-premise (код не покидает периметр компании)
  - Категории: IDE-ассистенты (Copilot Enterprise, Cody, Continue.dev, Tabby, Kilo Code), CLI-агенты (Claude Code self-hosted, Codex CLI, OpenCode + oh-my-opencode), code review боты, test generation
  - Для каждого инструмента: модель развёртывания, требования к GPU/инфраструктуре, лицензирование, зрелость, ограничения
  - Исследовать local LLM варианты (Ollama, vLLM, llama.cpp) как бэкенд для self-hosted инструментов
  - Оценить реалистичность self-hosted развёртывания: стоимость GPU, команда SRE, K8s зрелость
  - Подготовить сравнительную таблицу: tool / deployment model / GPU requirements / license / maturity / limitations

  **Must NOT do**:
  - Не рекомендовать SaaS-only решения как основные
  - Не проводить бенчмарк моделей — только shortlist + evaluation rubric
  - Не рекомендовать строить собственную RAG-платформу

  **Recommended Agent Profile**:
  - **Category**: `deep`
    - Reason: Требуется глубокое исследование с множеством источников, сравнительный анализ
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1 (with Tasks 2, 3, 4)
  - **Blocks**: Task 13
  - **Blocked By**: None

  **References**:
  - Tabby ML: https://github.com/TabbyML/tabby
  - Continue.dev: https://github.com/continuedev/continue
  - Cody by Sourcegraph: https://sourcegraph.com/cody
  - Ollama: https://ollama.ai
  - vLLM: https://github.com/vllm-project/vllm
  - Enterprise adoption guide: https://www.faros.ai/blog/enterprise-ai-coding-assistant-adoption-scaling-guide
  - Kilo Code (open-source AI coding assistant): https://github.com/kilocode/kilo
  - OpenCode (open-source CLI coding agent): https://github.com/opencode-ai/opencode
  - oh-my-opencode (расширения и конфигурации для OpenCode): https://github.com/ocrv/oh-my-opencode

  **Acceptance Criteria**:
  - [x] Сравнительная таблица ≥ 5 self-hosted инструментов
  - [x] Каждый инструмент оценён по: deployment, GPU, license, maturity
  - [x] Есть evaluation rubric для выбора

  **QA Scenarios:**
  ```
  Scenario: Полнота таблицы инструментов
    Tool: Bash (grep)
    Steps:
      1. Проверить наличие ≥ 5 инструментов в таблице
      2. Проверить колонки: Tool, Deployment, GPU, License, Maturity
    Expected Result: Таблица содержит ≥ 5 строк
    Evidence: .sisyphus/evidence/task-1-tools-table.txt
  ```

  **Commit**: NO (промежуточный артефакт, войдёт в T15)

- [x] 2. Написать Executive Summary

  **What to do**:
  - Написать на русском executive summary на 1 стр. для CTO/VP Engineering
  - Структура: проблема → возможность → ключевые цифры → что делать → эффект
  - Включить 3-5 ключевых цифр (OpenAI: 10x, Stripe: 1000 PR/week, 95% пилотов fail)
  - Call-to-action: «Аудит → пилот 4 недели → масштабирование 3 месяца»
  - Завершить блоком «Ключевые решения для принятия» (3-5 пунктов)

  **Must NOT do**:
  - Не использовать hype-язык
  - Не обещать ROI без оговорок
  - Не писать больше 1 страницы

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: Бизнес-текст на русском для C-level
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1
  - **Blocks**: Task 15
  - **Blocked By**: None

  **References**:
  - OpenAI Harness Engineering: https://openai.com/index/harness-engineering/
  - Harness Playbook: https://www.ignorance.ai/p/the-emerging-harness-engineering
  - Enterprise stats: MIT GenAI Divide, PwC 2026 CEO Survey

  **Acceptance Criteria**:
  - [x] ≤ 500 слов
  - [x] ≥ 3 цифры с источниками
  - [x] Есть блок «Ключевые решения»

  **QA Scenarios:**
  ```
  Scenario: Длина и структура
    Tool: Bash (wc + grep)
    Steps: wc -w → ≤ 500; grep 'Решени' → найдено
    Expected Result: ≤ 500 слов, есть блок решений, ≥ 3 цифры
    Evidence: .sisyphus/evidence/task-2-exec-summary.txt
  ```

  **Commit**: NO (войдёт в T15)

- [x] 3. Написать раздел «Индустриальный контекст»

  **What to do**:
  - Написать раздел ~3-4 стр. на русском: текущее состояние AI в разработке ПО
  - Подразделы: (а) Кейсы лидеров (OpenAI Harness: 1M LOC / 0 ручного кода / 3.5 PR/день; Stripe Minions: 1000+ PR/неделя; Anthropic: 90% self-written; OpenClaw: 6600 commits/month solo), (б) Статистика adoption (Gartner, McKinsey, MIT, PwC), (в) Парадокс: 95% пилотов fail, (г) Концепция Harness Engineering
  - Каждый кейс: цифры + что именно делали + уроки
  - Завершить блоком: «Решение: Какой подход выбрать для нашей компании — эволюционный vs революционный»

  **Must NOT do**:
  - Не пересказывать блог-посты целиком — только ключевые выводы
  - Не приводить данные без источника

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: Аналитический текст на русском с цитированием
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1
  - **Blocks**: Task 15
  - **Blocked By**: None

  **References**:
  - OpenAI Harness Engineering: https://www.engineering.fyi/article/harness-engineering-leveraging-codex-in-an-agent-first-world
  - Harness Playbook: https://www.ignorance.ai/p/the-emerging-harness-engineering
  - Vitthal Mirji: https://vitthalmirji.com/2026/02/build-the-harness-not-the-code
  - Enterprise AI 2026 Guide: https://ssntpl.com/enterprise-ai-implementation-complete-2026-guide/
  - AI ROI: https://www.synlabs.io/post/ai-roi-software-engineering

  **Acceptance Criteria**:
  - [x] ≥ 4 кейса с конкретными цифрами
  - [x] Все цифры имеют ссылки на источники
  - [x] Есть блок «Решение» в конце

  **QA Scenarios:**
  ```
  Scenario: Наличие кейсов и источников
    Tool: Bash (grep)
    Steps: Подсчитать упоминания компаний и наличие ссылок
    Expected Result: ≥ 4 кейса, каждый с источником
    Evidence: .sisyphus/evidence/task-3-industry.txt
  ```

  **Commit**: NO (войдёт в T15)

- [x] 4. Написать раздел «Что такое AI-Ready Codebase»

  **What to do**:
  - Определение AI-Ready Codebase: что это, чем отличается от просто «хорошей кодовой базы»
  - 7 ключевых характеристик: (1) Один очевидный способ делать типовые задачи, (2) Тесты защищают критические flows, (3) Build/lint/test работают без догадок, (4) Deprecated patterns помечены, (5) Дублирование удалено, (6) Документация описывает архитектуру и цели, (7) CI ловит регрессии
  - Формула: «AI-Ready = Human-Friendly + Machine-Navigable + Well-Documented Intent»
  - AI Readiness Maturity Model: 5 уровней (Chaotic → Basic → Structured → Optimized → AI-Native)
  - Self-assessment checklist (да/нет по каждому пункту)
  - Блок «Решение: На каком уровне ваша компания и каков следующий шаг»

  **Must NOT do**:
  - Не сводить к «просто напишите тесты» — системный подход
  - Не делать чеклист из 50 пунктов — фокус на самом важном

  **Recommended Agent Profile**:
  - **Category**: `writing`
    - Reason: Концептуальный раздел с моделью зрелости
  - **Skills**: []

  **Parallelization**:
  - **Can Run In Parallel**: YES
  - **Parallel Group**: Wave 1
  - **Blocks**: Tasks 5-9
  - **Blocked By**: None

  **References**:
  - Dakic: https://dakic.com/2026-03-02-prepare-codebase-for-ai-agents
  - LLMx AI-Ready Guide: https://llmx.de/blog/ai-ready-codebase-claude-cursor-integration-guide/
  - Hypercube: https://wearehypercube.com/ready-for-ai-preparing-your-codebase-for-assistants/
  - Propel Code: https://www.propelcode.ai/blog/structuring-codebases-for-ai-tools-2025-guide

  **Acceptance Criteria**:
  - [x] Чёткое определение AI-Ready
  - [x] Maturity Model из 5 уровней
  - [x] Self-assessment checklist
  - [x] Блок «Решение» в конце

  **QA Scenarios:**
  ```
  Scenario: Структура раздела
    Tool: Bash (grep)
    Steps: Проверить наличие определения, maturity model, checklist, решения
    Expected Result: Все 4 элемента присутствуют
    Evidence: .sisyphus/evidence/task-4-definition.txt
  ```

  **Commit**: NO (войдёт в T15)

- [x] 5. Написать раздел «Архитектура: Vertical Slices и AI-дружелюбные паттерны»

  **What to do**:
  - Объяснить почему архитектура влияет на эффективность AI (контекстное окно, навигация, количество файлов для изменения фичи)
  - Сравнение архитектур: Vertical Slice (★★★★★) vs Layered (★★) vs Microservices (★★★) vs Pipes&Filters (★★★★)
  - Ключевой вопрос: «Сколько файлов AI должен открыть, чтобы изменить фичу X?»
  - Практический пример структуры директорий Vertical Slice
  - Оговорка: когда VS НЕ применять (shared kernels, performance-critical, legacy cores)
  - Блок «Решение: Нужно ли мигрировать архитектуру и как»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 2 (with T6-T9) | **Blocks**: T10, T15 | **Blocked By**: T4

  **References**:
  - Practical AI Engineer (Kalkman): https://practical-engineer.ai/ai-ready-software-architecture-ship-faster-by-design/
  - LLMx Vertical Slice Guide: https://llmx.de/blog/ai-ready-codebase-claude-cursor-integration-guide/
  - Jimmy Bogard (original VS): https://www.jimmybogard.com/vertical-slice-architecture/

  **Acceptance Criteria**:
  - [x] Сравнительная таблица архитектур
  - [x] Пример структуры директорий
  - [x] Оговорки когда НЕ применять
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 6. Написать раздел «Документация: AGENTS.md, контекст и «Dual Audience Design»»

  **What to do**:
  - AGENTS.md/CLAUDE.md: что это, структура HOW/WHY/WHAT, пример заполненного файла
  - Context Engineering: что такое «context packing», почему ��ажно, инструменты (gitingest, repo2txt)
  - Architecture Decision Records (ADR): зачем документировать «почему», а не только «что»
  - Dual Audience Design: документация для людей И для машин одновременно
  - Практический шаблон AGENTS.md (готовый к использованию)
  - Блок «Решение: Какой уровень документации внедрять и каков минимум»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 2 | **Blocks**: T10, T14, T15 | **Blocked By**: T4

  **References**:
  - HumanLayer CLAUDE.md guide: https://www.humanlayer.dev/blog/writing-a-good-claude-md
  - Complete Guide to Memory Files: https://hackernoon.com/the-complete-guide-to-ai-agent-memory-files-claudemd-agentsmd-and-beyond
  - Addy Osmani: https://addyo.substack.com/p/my-llm-coding-workflow-going-into
  - Agent-Friendly Code (Dmitriy Zhuk): https://leanpub.com/agent-friendly-code

  **Acceptance Criteria**:
  - [x] Шаблон AGENTS.md готов к копированию
  - [x] Объяснен context engineering
  - [x] ADR описаны
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 7. Написать раздел «Инженерные Guardrails: CI/CD, тесты, линтинг, автоматизация»

  **What to do**:
  - Почему guardrails стали ещё важнее с AI («эффект усиления» — ошибки тоже ускоряются)
  - Минимальный набор: linting + formatting + type checking + tests + CI
  - Automated enforcement: pre-commit hooks, CI checks, structural tests
  - Code review для AI-generated кода: дополнительные проверки (no `as any`, нет пустых catch, нет console.log в prod)
  - Структурные тесты для архитектурных инвариантов (custom linters)
  - Блок «Решение: Какие guardrails внедрить в первую очередь»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 2 | **Blocks**: T10, T15 | **Blocked By**: T4

  **References**:
  - Dakic guardrails: https://dakic.com/2026-03-02-prepare-codebase-for-ai-agents
  - Augment Code 12 Rules: https://www.augmentcode.com/guides/enterprise-coding-standards-12-rules-for-ai-ready-teams
  - MetaCTO Code Review Standards: https://www.metacto.com/blogs/establishing-code-review-standards-for-ai-generated-code
  - Addy Osmani on CI/testing: https://addyo.substack.com/p/my-llm-coding-workflow-going-into

  **Acceptance Criteria**:
  - [x] Минимальный набор guardrails описан
  - [x] Специфика code review для AI-generated кода
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 8. Написать раздел «Процессы разработки с AI: от Copilot до Agent Fleets»

  **What to do**:
  - Эволюция режимов: autocomplete → chat → agents → background agents → agent fleets
  - Workflow Addy Osmani: specs-before-code → small chunks → context pack → test → commit → review
  - Harness Engineering workflow: humans steer, agents execute
  - Практики: TDD с AI, частые коммиты как save points, git worktrees, мульти-модельный подход
  - Code review для AI-generated кода: AI-on-AI review, дополнительные проверки
  - Governance: кто отвечает за AI-generated код, политика merge, blast radius
  - Блок «Решение: Какой режим внедрять на Year-1»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 2 | **Blocks**: T10, T15 | **Blocked By**: T4

  **References**:
  - Addy Osmani workflow: https://addyo.substack.com/p/my-llm-coding-workflow-going-into
  - OpenAI Harness: https://openai.com/index/harness-engineering/
  - AI Coding Best Practices: https://allahabadi.dev/blogs/ai/ai-coding-best-practices-2025/
  - Large Codebase Strategies: https://developertoolkit.ai/en/cursor-ide/advanced-techniques/large-codebase-strategies

  **Acceptance Criteria**:
  - [x] Эволюция режимов описана
  - [x] Конкретный workflow описан
  - [x] Governance политика описана
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 9. Написать раздел «Обучение команды и новые роли»

  **What to do**:
  - Новая роль инженера: от «пишу код» к «проектирую среду для агентов» (Harness Engineer)
  - Архитектор как дирижёр: guardrails, patterns, boundaries
  - Новые компетенции: prompt engineering, context engineering, AI review skills
  - Риски: juniors передоверяют AI, seniors игнорируют, неравномерное adoption
  - Программа обучения: champions network, практические workshops, парное программирование с AI
  - Блок «Решение: Формат и сроки обучения, кто отвечает»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 2 | **Blocks**: T10, T15 | **Blocked By**: T4

  **References**:
  - OpenAI новая роль инженера: https://openai.com/index/harness-engineering/
  - Kalkman Architect as Director: https://practical-engineer.ai/ai-ready-software-architecture-ship-faster-by-design/
  - Codex team structure: https://newsletter.eng-leadership.com/p/how-openais-codex-team-works-and
  - OpenClaw solo dev: https://www.ignorance.ai/p/the-emerging-harness-engineering

  **Acceptance Criteria**:
  - [x] Новые роли и компетенции описаны
  - [x] Программа обучения описана
  - [x] Риски human factors описаны
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 10. Написать раздел «Дорожная карта внедрения (4 фазы)»

  **What to do**:
  - **Фаза 0: Аудит (1-2 недели)**: оценка текущего состояния кодовой базы, сбор baseline метрик (DORA, cycle time, defect rate, test coverage), определение уровня AI Readiness Maturity, выбор пилотной команды/модуля
  - **Фаза 1: Cleanup и guardrails (2-4 недели)**: удаление дублирования, настройка CI/linting/formatting, написание AGENTS.md, документирование архитектуры, пометка legacy zones
  - **Фаза 2: Пилот (4-8 недель)**: развёртывание self-hosted инструментов, обучение пилотной команды, измерение и сравнение с baseline, итерация на практиках
  - **Фаза 3: Масштабирование (8-12 недель)**: расширение на все команды, стандартизация практик, champions network, непрерывное измерение
  - Для каждой фазы: цель, критерии входа/выхода, ответственные роли, конкретные действия, риски
  - Блок «Решение: С какой команды/модуля начать пилот, тайминги»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 3 (with T11-T14) | **Blocks**: T15 | **Blocked By**: T5-T9

  **References**: Все предыдущие разделы + Enterprise AI Implementation Guide: https://ssntpl.com/enterprise-ai-implementation-complete-2026-guide/

  **Acceptance Criteria**:
  - [x] 4 фазы с критериями выхода
  - [x] Ответственные роли указаны
  - [x] Тайминги реалистичны
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 11. Написать раздел «Метрики и KPI»

  **What to do**:
  - Проблема измерения: adoption volume ≠ success, линии кода ≠ value
  - 3 уровня метрик: Input (принятие) → Output (продуктивность) → Outcome (бизнес)
  - Input: adoption rate, usage frequency, доля AI-assisted PRs
  - Output: PR velocity, cycle time, покрытие тестами, rework rate
  - Outcome: time-to-market, defect rate, DORA metrics, developer satisfaction
  - Базовые метрики ДО внедрения (baseline) — ОБЯЗАТЕЛЬНО
  - Шаблон дашборда: что измерять, как собирать, как отчитываться
  - Блок «Решение: Какие метрики внедрить на каждой фазе, как отчитываться перед руководством»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 3 | **Blocks**: T15 | **Blocked By**: None

  **References**:
  - AI ROI Framework: https://www.synlabs.io/post/ai-roi-software-engineering
  - Enterprise ROI Metrics: https://blog.exceeds.ai/enterprise-ai-coding-adoption-insights-ai-adoption/
  - DX ROI Framework: https://getdx.com/blog/ai-roi-enterprise
  - Faros AI adoption: https://www.faros.ai/blog/enterprise-ai-coding-assistant-adoption-scaling-guide

  **Acceptance Criteria**:
  - [x] 3 уровня метрик описаны
  - [x] Baseline требование явное
  - [x] Шаблон дашборда есть
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 12. Написать раздел «Риски и митигация»

  **What to do**:
  - **Technical debt amplification**: AI ускоряет накопление долга если нет guardrails
  - **Security**: утечка кода, logging промптов/ответов, model inversion, IP leakage, data classification
  - **Compliance**: лицензирование AI-generated кода, OSS compliance, провенанс кода
  - **Human factors**: передоверие, деградация навыков, сопротивление изменениям
  - **Регулируемые зоны**: код, где AI нельзя использовать даже on-prem (крипто, auth, персданные)
  - Для каждого риска: описание, вероятность, влияние, митигация, остаточный риск
  - Блок «Решение: Какие риски принять, какие митигировать в первую очередь»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 3 | **Blocks**: T15 | **Blocked By**: None

  **Acceptance Criteria**:
  - [x] ≥ 5 категорий рисков с митигацией
  - [x] Security model для on-prem описан
  - [x] Блок «Реше��ие»

  **Commit**: NO (войдёт в T15)

- [x] 13. Написать раздел «Self-Hosted инструменты: сравнение и рекомендации»

  **What to do**:
  - Интегрировать результаты исследования из T1 в раздел отчёта
  - Сравнительная таблица self-hosted инструментов с анализом
  - Evaluation rubric с взвешенными критериями для выбора
  - Рекомендация по стеку (2-3 варианта: минимальный, оптимальный, максимальный)
  - Блок «Решение: Какой стек выбрать и сколько это стоит»

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 3 | **Blocks**: T15 | **Blocked By**: T1

  **Acceptance Criteria**:
  - [x] Сравнительная таблица
  - [x] Evaluation rubric
  - [x] 2-3 рекомендуемых стека
  - [x] Блок «Решение»

  **Commit**: NO (войдёт в T15)

- [x] 14. Написать приложения (чеклисты, шаблоны, таблицы)

  **What to do**:
  - **Приложение A**: Шаблон AGENTS.md (готовый к копированию, с HOW/WHY/WHAT)
  - **Приложение B**: AI Readiness Checklist (из T4, расширенный)
  - **Приложение C**: Пример Vertical Slice структуры директорий (tree view)
  - **Приложение D**: Шаблон метрик/дашборда (таблица метрик с источниками данных)
  - **Приложение E**: Список источников и рекомендуемое чтение

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Wave 3 | **Blocks**: T15 | **Blocked By**: T6

  **Acceptance Criteria**:
  - [x] 5 приложений готовы
  - [x] Шаблон AGENTS.md копируем
  - [x] Checklist включает ≥ 15 пунктов

  **Commit**: NO (войдёт в T15)

- [x] 15. Собрать финальный отчёт из всех разделов

  **What to do**:
  - Собрать все разделы (T2-T14) в единый файл `ai-ready-codebase-report.md`
  - Обеспечить логичные переходы между разделами
  - Добавить оглавление (Table of Contents)
  - Проверить нумерацию разделов и перекрёстные ссылки
  - Подсчитать общее количество decision points (≥ 10)

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Sequential | **Blocks**: T16, F1-F4 | **Blocked By**: T2-T14

  **Acceptance Criteria**:
  - [x] Единый файл с оглавлением
  - [x] ≥ 8 основных разделов
  - [x] Логичные переходы
  - [x] ≥ 10 decision points

  **Commit**: YES
  - Message: `docs: add AI-Ready Codebase analytical report`
  - Files: `ai-ready-codebase-report.md`

- [x] 16. Вычитка и polish финального отчёта

  **What to do**:
  - Проверить единообразие стиля и тона
  - Удалить повторы между разделами
  - Проверить все ссылки на источники
  - Проверить что читается как decision memo, не как блог
  - Проверить self-hosted compliance всех рекомендаций

  **Recommended Agent Profile**: `writing` | **Skills**: []
  **Parallelization**: Sequential | **Blocks**: F1-F4 | **Blocked By**: T15

  **Acceptance Criteria**:
  - [x] Единый стиль и тон
  - [x] Нет повторов
  - [x] Все ссылки рабочие
  - [x] Tone: CTO decision memo

  **Commit**: YES
  - Message: `docs: polish and finalize AI-Ready report`
  - Files: `ai-ready-codebase-report.md`

## Final Verification Wave

> 4 review agents run in PARALLEL. ALL must APPROVE. Rejection → fix → re-run.

- [x] F1. **Аудит соответствия плану** — `deep`
  Прочитать план целиком. Для каждого «Must Have»: проверить наличие в отчёте. Для каждого «Must NOT Have»: поискать нарушения. Сверить deliverables с планом.
  Output: `Must Have [N/N] | Must NOT Have [N/N] | Tasks [N/N] | VERDICT: APPROVE/REJECT`

- [x] F2. **Проверка качества текста** — `writing`
  Проверить: единообразие стиля, отсутствие повторов между разделами, логичность переходов, наличие executive summary. Проверить что не выглядит как перевод блог-постов.
  Output: `Style [PASS/FAIL] | Duplicates [PASS/FAIL] | Flow [PASS/FAIL] | VERDICT`

- [x] F3. **Проверка decision content** — `deep`
  Для каждого раздела: проверить наличие блока «Решение / Рекомендация / Trade-offs». Подсчитать количество decision points (минимум 10). Проверить что все цифры имеют ссылки на источники.
  Output: `Decision Points [N≥10] | Source Attribution [N/N] | VERDICT`

- [x] F4. **Проверка self-hosted compliance** — `deep`
  Проверить каждую рекомендацию по инструментам: совместима ли с «код не покидает периметр». Пометить нарушения. Проверить что раздел рисков включает security модель.
  Output: `Tools Compliant [N/N] | Security Model [PRESENT/MISSING] | VERDICT`

---

## Commit Strategy

- **Wave 4 (T15)**: `docs: add AI-Ready Codebase analytical report` — ai-ready-codebase-report.md
- **Wave 4 (T16)**: `docs: polish and finalize AI-Ready report` — ai-ready-codebase-report.md

---

## Success Criteria

### Verification Commands
```bash
# Проверка структуры отчёта (≥8 разделов)
grep -c "^## " ai-ready-codebase-report.md  # Expected: ≥ 8

# Проверка русского текста + английские термины
grep -c "AI-ready\|LLM\|guardrails\|Vertical Slice\|DORA" ai-ready-codebase-report.md  # Expected: ≥ 5

# Проверка decision points
grep -ci "Решение\|Рекомендация\|Trade-off" ai-ready-codebase-report.md  # Expected: ≥ 10

# Проверка self-hosted coverage
grep -ci "on-prem\|self-host\|периметр\|локальн" ai-ready-codebase-report.md  # Expected: ≥ 5
```

### Final Checklist
- [x] Все «Must Have» присутствуют
- [x] Все «Must NOT Have» отсутствуют
- [x] ≥ 10 decision points для CTO
- [x] Все рекомендации по инструментам совместимы с «код не покидает периметр»
- [x] Roadmap содержит 4 фазы с критериями выхода
- [x] Приложения содержат готовые к использованию шаблоны
- [x] Отчёт читается как decision memo, не как блог
- [x] Все «Must NOT Have» отсутствуют
- [x] ≥ 10 decision points для CTO
- [x] Все рекомендации по инструментам совместимы с «код не покидает периметр»
- [x] Roadmap содержит 4 фазы с критериями выхода
- [x] Приложения содержат готовые к использованию шаблоны
- [x] Отчёт читается как decision memo, не как блог
