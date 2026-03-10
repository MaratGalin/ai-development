# Черновик исследования: AI-Ready Codebase

## Цель исследования
Подготовить отчёт для руководства с конкретными практиками и рекомендациями по:
1. Превращению кодовой базы в AI-Ready
2. Правильной разработке кода и продуктов с помощью AI
3. Дорожной карте внедрения в компании

## Ключевые источники (собрано)

### 1. OpenAI Harness Engineering (Февраль 2026)
**Источник:** Ryan Lopopolo, OpenAI Engineering Blog

**Ключевые цифры:**
- Команда из 3 инженеров → 7 инженеров
- 0 строк кода, написанных человеком
- 1 миллион строк кода за 5 месяцев
- 3.5 PR на инженера в день
- В 10 раз быстрее традиционной разработки

**Core концепция:** Humans steer. Agents execute.
- Инженеры больше НЕ пишут код
- Их работа: проектировать среды, специфицировать интент, строить feedback loops
- AGENTS.md — центральный документ направления агентов

### 2. Addy Osmani — LLM Coding Workflow 2026
**Источник:** Менеджер инженерной команды Google Chrome (бывший)

**Ключевые практики:**
1. **Specs before code** — спецификация ДО кода
2. **Break into small chunks** — итеративные маленькие задачи
3. **Extensive context** — «context packing»
4. **Human in the loop** — обязательный review и тестирование
5. **Commit often** — частые коммиты как save points
6. **Customize with rules** — CLAUDE.md, GEMINI.md для кастомизации

**Цитата:** *"AI coding assistants are incredible force multipliers, but the human engineer remains the director of the show."*

### 3. Vertical Slice Architecture
**Источник:** Jimmy Bogard + Patrick Kalkman (Practical AI Engineer)

**Почему это AI-friendly:**
- Все компоненты фичи в одном месте
- AI видит полный контекст без прыжков между слоями
- Уменьшает context window usage
- Легче навигация для AI

**Сравнение архитектур:**
| Архитектура | AI-Friendly | Примечание |
|-------------|-------------|------------|
| Vertical Slice | ★★★★★ | Лучший вариант |
| Layered | ★★☆☆☆ | AI теряется в слоях |
| Microservices | ★★★☆☆ | Зависит от реализации сервиса |
| Pipes & Filters | ★★★★☆ | Хорош для data pipelines |

### 4. CLAUDE.md / AGENTS.md Specification
**Источник:** HumanLayer, Paolo Perrone, Anthropic

**Назначение:**
- Единственный файл, который агент читает в каждой сессии
- Содержит HOW, WHY, WHAT проекта
- Onboarding агента в кодовую базу

**Структура:**
```markdown
# HOW — как работать
- Команды сборки/тестирования
- Конвенции кода
- Что НЕ делать

# WHY — зачем проект существует
- Цель продукта
- Архитектурные решения
- Бизнес-контекст

# WHAT — что это за проект
- Стек технологий
- Структура директорий
- Ключевые модули
```

### 5. Dakic — Prepare Your Codebase Before AI Agents
**Ключевая мысль:**
> "AI agents are force multipliers, not cleanup crews."

**Проблема:**
- Команды дают AI доступ к «грязной» кодовой базе
- AI копирует все shortcut'ы, inconsistences, workaround'ы
- Ускоряется не только output, но и technical debt

**AI Readiness Checklist:**
- [ ] Один очевидный способ реализовывать типовые задачи
- [ ] Тесты защищают критические user flows
- [ ] Build/lint/test работают без догадок
- [ ] Deprecated patterns явно помечены
- [ ] Дублирующие utility функции удалены
- [ ] Документация описывает архитектуру и цели продукта
- [ ] CI ловит регрессии до мержа

### 6. Enterprise AI Adoption — Проблемы внедрения
**Источник:** Gartner, PwC, MIT GenAI Divide report

**Статистика:**
- 95% генеративных AI-пилотов не выходят за пределы эксперимента
- 56% CEO получают "ничего" от AI-усилий
- Только 23% компаний количественно доказывают ROI
- 42% отказываются от инициатив после пилотов
- 26% выходят за proof of concept

**Проблемы измерения ROI:**
- Adoption volume ≠ success
- Lines of code generated ≠ value
- Нужны code-level analytics (commits, PR level)

### 7. Architect as Director (Patrick Kalkman)
**Изменение роли архитектора:**
- От "строителя с молотком" к "дирижёру с батоном"
- Проектирование guardrails и boundaries
- Продвижение reusable patterns
- Баланс стандартизации и гибкости
- Создание explicit architectural context

**Guardrails:**
- Module boundaries
- Naming conventions
- Defined integration points
- Automated enforcement (CI, linters)

### 8. AI Coding Best Practices 2025 (Complete Playbook)
**8 Core Practices:**
1. Станьте Project Manager — чёткие инструкции с приоритетами
2. Используйте reasoning models для сложных задач
3. Правильный выбор model для каждой задачи
4. Асинхронные агенты (Jules, Copilot Agent) для фоновой работы
5. Human-in-the-loop — review всего
6. Частые коммиты и granular version control
7. Кастомизация через rules файлы
8. CI/CD как force multiplier

## Открытые вопросы для уточнения

### Контекст компании:
1. **Размер команды разработки?**
2. **Технологический стек?** (JavaScript/TypeScript, Python, Java, etc.)
3. **Текущее состояние кодовой базы?** (legacy, moderately clean, greenfield)
4. **Есть ли CI/CD, тесты, линтеры?**

### Цели внедрения:
5. **Что приоритетнее:** скорость разработки или качество кода?
6. **Какие метрики успеха для руководства?** (PR velocity, bug rate, time-to-market)
7. **Есть ли бюджетные ограничения?** (платные AI-инструменты vs open source)

### Организационные аспекты:
8. **Уровень зрелости команды?** (junior-heavy, balanced, senior-heavy)
9. **Есть ли сопротивление изменениям?**
10. **Сколько времени на пилот?**

## Предварительная структура отчёта

### Раздел 1: Executive Summary
- Парадокс AI-внедрения: 95% пилотов проваливаются
- Harness Engineering — новая парадигма
- ROI: когда и как измерять

### Раздел 2: Текущее состояние индустрии
- OpenAI кейс: 1M LOC, 0 ручного кода
- Stripe: 1000+ PR/неделю от AI-агентов
- Anthropic: 90% кода Claude Code пишет сам себя

### Раздел 3: Что такое AI-Ready Codebase
- Определение
- Характеристики
- Отличие от "хорошей кодовой базы"

### Раздел 4: Конкретные практики
4.1. Архитектура: Vertical Slices
4.2. Документация: AGENTS.md/CLAUDE.md
4.3. Инженерные guardrails
4.4. Контекст и "context packing"
4.5. Итеративная работа с AI

### Раздел 5: Дорожная карта внедрения
5.1. Фаза 0: Аудит текущей кодовой базы
5.2. Фаза 1: Cleanup и guardrails (2-4 недели)
5.3. Фаза 2: Пилот с одной командой (4-8 недель)
5.4. Фаза 3: Масштабирование (8-12 недель)
5.5. Фаза 4: Измерение и оптимизация

### Раздел 6: Метрики и KPI
- Input metrics: adoption rate, usage frequency
- Output metrics: PR velocity, cycle time
- Outcome metrics: time-to-market, defect rate

### Раздел 7: Риски и митигация
- Technical debt amplification
- Security and compliance
- Knowledge silos
- Over-reliance on AI

### Раздел 8: Рекомендации по инструментам
- Claude Code / Cursor / Copilot
- AGENTS.md генераторы
- Context packing tools
- Code review automation

### Приложения:
- A: Шаблон AGENTS.md
- B: AI Readiness Checklist
- C: Пример Vertical Slice структуры
- D: Сравнительная таблица AI-инструментов

---

*Черновик создан: 2026-03-07*
*Следующий шаг: уточнить контекст компании и сформировать финальный план*