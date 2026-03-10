# Приложения

## Приложение A: Шаблон AGENTS.md

Скопируйте этот шаблон в корень вашего репозитория и адаптируйте под ваш проект.

```markdown
# AGENTS.md

## HOW — Как работать в проекте

### Менеджер пакетов и команды
- Менеджер пакетов: `pnpm` (использовать `pnpm install`, не `npm install`)
- Тесты: `pnpm test` (запускает все тесты с coverage)
- Линт: `pnpm lint` (ESLint + Prettier)
- Type check: `pnpm typecheck` (TypeScript компиляция без эмита)
- Сборка: `pnpm build` (production build)

### Перед созданием PR обязательно
1. Все тесты проходят: `pnpm test`
2. Линт чистый: `pnpm lint`
3. Type check проходит: `pnpm typecheck`
4. Сборка успешна: `pnpm build`

### Что НЕ делать без явного согласования
- Не добавляйте новые зависимости без обоснования в PR
- Не меняйте публичные API без обновления `docs/api-contracts.md`
- Не используйте `any` в TypeScript без комментария с причиной
- Не оставляйте `console.log` в production коде

## WHY — Зачем проект существует

### Продукт
- Название: [Название продукта]
- Назначение: [Краткое описание продукта]
- Целевая аудитория: [Кто использует продукт]

### Архитектурные приоритеты
1. **Надежность** — данные пользователей не должны теряться
2. **Производительность** — ключевые операции < 200ms
3. **Поддерживаемость** — код читается новым инженером за 1 день

### Ключевые архитектурные решения
- Модульный монолит (не микросервисы) — для скорости разработки
- Vertical Slice Architecture — каждая фича в своей директории
- Event-driven для асинхронных операций
- CQRS для read-heavy операций (где применимо)

## WHAT — Что находится в репозитории

### Структура директорий
```
├── apps/
│   ├── web/                 # Frontend (Next.js)
│   │   ├── src/
│   │   │   ├── features/    # Фичи по Vertical Slice
│   │   │   ├── components/  # Shared компоненты
│   │   │   └── lib/         # Утилиты и хелперы
│   │   └── tests/
│   └── api/                 # Backend API (FastAPI/Node)
│       ├── src/
│       │   ├── features/    # Фичи по Vertical Slice
│       │   ├── domain/      # Доменные модели
│       │   └── infrastructure/ # DB, external APIs
│       └── tests/
├── packages/
│   ├── domain/              # Shared доменные модели
│   ├── ui/                  # Shared UI компоненты
│   └── config/              # Shared конфигурации
├── docs/
│   ├── adr/                 # Architecture Decision Records
│   ├── api-contracts/       # API контракты
│   └── dev/                 # Документация для разработчиков
└── scripts/                 # Автоматизация
```

### Ключевые файлы
- `AGENTS.md` — этот файл (правила работы с AI)
- `README.md` — общая документация проекта
- `docs/adr/` — архитектурные решения и их причины
- `docs/api-contracts/` — актуальные API контракты

## Read if relevant — Когда что читать

### Работа с конкретной фичей
- `docs/features/[feature-name].md` — описание фичи и её границ
- `apps/*/src/features/[feature-name]/README.md` — детали реализации фичи

### Разработка и тестирование
- `docs/dev/testing.md` — стратегия тестирования и команды для локального прогона
- `docs/dev/release.md` — процесс релиза и чеклист
- `docs/dev/deployment.md` — как деплоить в разные окружения

### Архитектурные решения
- `docs/adr/` — все ADR с датами и статусами
- `docs/adr/001-why-monolith.md` — почему выбрали монолит
- `docs/adr/002-vertical-slices.md` — почему Vertical Slice Architecture

### API и интеграции
- `docs/api-contracts/` — OpenAPI спецификации
- `docs/integrations/` — интеграции с внешними системами
```

---

## Приложение B: AI Readiness Checklist (расширенный)

### Инженерные практики

- [ ] **One obvious way** — Для каждой типовой задачи есть один предпочтительный путь реализации
- [ ] **Тесты защищают критические flows** — Важные сценарии пользователя покрыты тестами
- [ ] **Build/lint/test работают без догадок** — Команды явно задокументированы и воспроизводимы
- [ ] **Deprecated patterns помечены** — Старые подходы явно отмечены как не рекомендуемые
- [ ] **Дубли и конфликтующие абстракции сокращены** — Нет нескольких "правильных" реализаций одной задачи
- [ ] **Документация описывает архитектуру** — Есть связь между кодом, решением и бизнес-смыслом
- [ ] **CI ловит типовые регрессии** — Основные проверки качества автоматизированы и обязательны

### AI-specific практики

- [ ] **AGENTS.md создан** — В корне репозитория есть файл с HOW/WHY/WHAT
- [ ] **Context packing документирован** — Понятно, какие файлы нужны для типовых задач
- [ ] **ADR для ключевых решений** — Архитектурные решения документированы с причинами
- [ ] **Deprecated zones помечены** — Код, который не должен копироваться AI, явно помечен
- [ ] **Guardrails настроены** — Линтинг, type checking, тесты блокируют merge при нарушениях
- [ ] **Code review для AI-generated кода** — Есть чеклист для review AI-generated изменений

### Организационная готовность

- [ ] **Baseline метрики собраны** — Есть данные до внедрения AI для сравнения
- [ ] **Пилотная команда выбрана** — Есть команда для первого внедрения
- [ ] **Champions network** — Выделены энтузиасты для помощи другим командам
- [ ] **Training program** — План обучения команд работе с AI
- [ ] **Governance policy** — Понятно, кто отвечает за AI-generated код

### Self-assessment по уровням зрелости

**Уровень 1 — Chaotic (0-2 пункта)**
- Риск: AI ускоряет накопление техдолга

**Уровень 2 — Basic (3-4 пункта)**
- Риск: Локальные улучшения есть, но масштабирование ломается

**Уровень 3 — Structured (5 пунктов)**
- Эффект: Заметный рост скорости без резкого роста дефектов

**Уровень 4 — Optimized (6 пунктов)**
- Эффект: AI-ассистенты работают предсказуемо, доля rework снижается

**Уровень 5 — AI-Native (7+ пунктов)**
- Эффект: Высокая скорость поставки и управляемое качество на уровне организации

---

## Приложение C: Пример структуры Vertical Slice

```
src/
├── features/
│   ├── user-profile/              # Фича: Профиль пользователя
│   │   ├── api/                   # API endpoints для фичи
│   │   │   ├── get-profile.ts
│   │   │   └── update-profile.ts
│   │   ├── components/            # UI компоненты фичи
│   │   │   ├── ProfileCard.tsx
│   │   │   └── EditProfileForm.tsx
│   │   ├── hooks/                 # React hooks фичи
│   │   │   ├── useProfile.ts
│   │   │   └── useUpdateProfile.ts
│   │   ├── services/              # Бизнес-логика
│   │   │   ├── profile-service.ts
│   │   │   └── validation.ts
│   │   ├── types/                 # Типы фичи
│   │   │   └── profile-types.ts
│   │   ├── tests/                 # Тесты фичи
│   │   │   ├── profile-api.test.ts
│   │   │   └── profile-service.test.ts
│   │   └── README.md              # Документация фичи
│   │
│   ├── authentication/            # Фича: Аутентификация
│   │   ├── api/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── types/
│   │   ├── tests/
│   │   └── README.md
│   │
│   └── payment/                   # Фича: Платежи
│       ├── api/
│       ├── components/
│       ├── hooks/
│       ├── services/
│       ├── types/
│       ├── tests/
│       └── README.md
│
├── shared/                        # Shared код между фичами
│   ├── components/                # UI kit
│   ├── hooks/                     # Общие hooks
│   ├── lib/                       # Утилиты
│   └── types/                     # Shared types
│
└── app/                          # Инициализация приложения
    ├── layout.tsx
    ├── providers.tsx
    └── routes.ts
```

### Почему это AI-friendly

1. **Все файлы фичи в одном месте** — AI видит полный контекст без прыжков по директориям
2. **Предсказуемая структура** — Каждая фича следует одному шаблону
3. **README в каждой фиче** — Документация рядом с кодом
4. **Четкие границы** — Минимум shared кода, максимум явных зависимостей

---

## Приложение D: Шаблон метрик/дашборда

### Input Metrics (Adoption)

| Метрика | Источник данных | Частота сбора | Целевое значение |
|---|---|---|---|
| Adoption rate | Tool analytics / surveys | Еженедельно | > 80% команды использует |
| Usage frequency | IDE plugin logs / CLI logs | Ежедневно | > 5 сессий на разработчика в день |
| % AI-assisted PRs | Git provider API (labels/comments) | Еженедельно | > 30% PRs с AI-помощью |
| Lines of code generated | IDE/CLI analytics | Еженедельно | Тренд, не цель |

### Output Metrics (Productivity)

| Метрика | Источник данных | Частота сбора | Целевое значение |
|---|---|---|---|
| PR velocity (time to merge) | Git provider API | Еженедельно | -20% vs baseline |
| Cycle time | Git provider API / issue tracker | Еженедельно | -15% vs baseline |
| Test coverage | CI reports | На каждый PR | Не снижать ниже baseline |
| Rework rate (code churn) | Git provider API | Еженедельно | < 15% изменений в первую неделю |
| Build success rate | CI logs | Ежедневно | > 95% |

### Outcome Metrics (Business)

| Метрика | Источник данных | Частота сбора | Целевое значение |
|---|---|---|---|
| Time-to-market (feature delivery) | Issue tracker + release notes | Ежемесячно | -10% vs baseline |
| Defect rate (production bugs) | Bug tracker | Еженедельно | Не выше baseline |
| Developer satisfaction | Surveys (eNPS) | Ежеквартально | > 7/10 |
| DORA metrics | Git + CI/CD data | Ежемесячно | Улучшение на 1 уровень |

### Baseline Template (заполнить до старта)

```
Дата сбора baseline: [YYYY-MM-DD]
Период сбора: [4 недели]

Input Metrics:
- Adoption rate: [X]%
- Usage frequency: [X] сессий/день
- % AI-assisted PRs: [X]%

Output Metrics:
- PR velocity: [X] дней
- Cycle time: [X] дней
- Test coverage: [X]%
- Rework rate: [X]%
- Build success rate: [X]%

Outcome Metrics:
- Time-to-market: [X] дней
- Defect rate: [X] багов/неделю
- Developer satisfaction: [X]/10
- DORA Deploy Frequency: [X]/день
- DORA Lead Time: [X] часов
- DORA Change Failure Rate: [X]%
- DORA MTTR: [X] часов
```

---

## Приложение E: Источники и рекомендуемое чтение

### Ключевые источники

1. **OpenAI Harness Engineering** (Feb 2026)
   - https://openai.com/index/harness-engineering/
   - OpenAI's experience building 1M LOC product with zero manual code

2. **Emerging "Harness Engineering" Playbook** (Feb 2026)
   - https://www.ignorance.ai/p/the-emerging-harness-engineering
   - Analysis of patterns from OpenAI, Stripe, OpenClaw

3. **My LLM coding workflow going into 2026** — Addy Osmani (Dec 2025)
   - https://addyo.substack.com/p/my-llm-coding-workflow-going-into
   - Best practices from engineering leader

4. **AI-Ready Software Architecture** — Patrick Kalkman (Apr 2025)
   - https://practical-engineer.ai/ai-ready-software-architecture-ship-faster-by-design/
   - Vertical Slice Architecture and AI-friendly patterns

5. **AI-Ready Codebase Guide** — LLMx (Sep 2025)
   - https://llmx.de/blog/ai-ready-codebase-claude-cursor-integration-guide/
   - Claude.md, Vertical Slices, best practices

6. **Prepare Your Codebase Before You Hand It to AI Agents** — Dakic (Mar 2026)
   - https://dakic.com/2026-03-02-prepare-codebase-for-ai-agents
   - Why cleanup must come before AI acceleration

7. **Enterprise AI Implementation: Complete 2026 Guide**
   - https://ssntpl.com/enterprise-ai-implementation-complete-2026-guide/
   - Statistics: 95% pilots fail, 56% CEOs get "nothing"

8. **How to measure AI ROI in enterprise software projects** — DX
   - https://getdx.com/blog/ai-roi-enterprise
   - Framework for measuring AI impact

9. **Writing a good CLAUDE.md** — HumanLayer
   - https://www.humanlayer.dev/blog/writing-a-good-claude-md
   - AGENTS.md/CLAUDE.md best practices

10. **12 Rules for AI-Ready Teams** — Augment Code
    - https://www.augmentcode.com/guides/enterprise-coding-standards-12-rules-for-ai-ready-teams
    - Enterprise coding standards

### Инструменты и технологии

- **Tabby ML**: https://github.com/TabbyML/tabby
- **Continue.dev**: https://github.com/continuedev/continue
- **Ollama**: https://ollama.ai
- **vLLM**: https://github.com/vllm-project/vllm

### Рекомендуемый порядок чтения для CTO

1. Executive Summary (этот отчёт)
2. OpenAI Harness Engineering (понимание возможностей)
3. Enterprise AI Implementation Guide (понимание рисков)
4. AI-Ready Software Architecture (технические паттерны)
5. Приложения (готовые шаблоны для внедрения)