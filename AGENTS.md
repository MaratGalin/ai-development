# AGENTS.md

This file is the operating guide for agentic coding assistants in this repository.
Goal: produce safe, verifiable changes without inventing missing project facts.

---

## 1) Repository Profile (Read First)

- Current repository is documentation-first (reports/templates), not a runnable app codebase.
- No executable manifests detected in current state:
  - `package.json`
  - `pyproject.toml`
  - `Makefile`
  - `tox.ini`
  - `Justfile`
- No CI workflow files detected under `.github/workflows/`.

Agent implications:
- Separate **documented policy commands** from **commands executable now**.
- Never report “tests/build passed” unless command execution happened in this repo.
- If user asks for runtime checks, first verify that runnable project files exist.

---

## 2) Build / Lint / Test Commands

### 2.1 Documented commands (policy from repo docs)

The repository documentation includes an AGENTS template with these commands:

- Install: `pnpm install`
- Test (all): `pnpm test`
- Lint: `pnpm lint`
- Typecheck: `pnpm typecheck`
- Build: `pnpm build`
- Workspace examples: `pnpm -r test`, `pnpm -r build`

Sources:
- `ai-ready-codebase-report.md`
- `ai-ready-report-work/sections/task-14-appendices.md`
- `ai-ready-report-work/sections/task-6-documentation.md`

### 2.2 Running a single test

- **No authoritative single-test command is currently defined.**
- Reason: there is no actual test runner config/manifest to confirm syntax.

Agent rule:
- Do not guess single-test syntax.
- When real test config appears, derive exact command and update this file.

### 2.3 What is executable now

- File edits
- Git operations
- Manual/structured document verification

Not currently guaranteed:
- App build, lint, typecheck, or automated test pipelines

---

## 3) Verification Expectations for PR Work

When executable code exists (per documented policy), expected checks are:

1. `pnpm test`
2. `pnpm lint`
3. `pnpm typecheck`
4. `pnpm build`

Current-state caveat:
- These are policy targets from docs; they are not automatically runnable in today’s repo state.

Required reporting format:
- **Documented policy:** commands required by docs
- **Executed:** commands actually run
- **Gap:** missing files/config preventing execution

---

## 4) Code Style Guidelines

Because no formatter/linter config files are present, follow explicit documented constraints only.

### 4.1 Imports

- No explicit import ordering/grouping rule is configured now.
- If code is added later, follow local patterns in nearby modules/files.

### 4.2 Formatting

- Documentation references ESLint + Prettier via `pnpm lint`.
- Until real config exists, keep edits minimal and consistent with surrounding style.
- For markdown: clear headings, short bullet lists, low ambiguity.

### 4.3 Types

- Template policy expects `pnpm typecheck` for TS projects.
- Avoid `any` unless rationale is explicit and reviewed.

### 4.4 Naming and structure

Documented architecture intent emphasizes:
- Vertical Slice structure (feature-oriented directories)
- Descriptive names
- Feature-specific docs close to implementation

### 4.5 Error handling and debug hygiene

- No repository-enforced code-level error-handling standard is present yet.
- Prefer explicit failures over silent suppression.
- Do not leave `console.log` in production code (template rule).

---

## 5) Change Management Rules

- Make minimal, local changes aligned to the request.
- Preserve existing patterns unless scope requires structured change.
- Do not add dependencies without justification.
- Do not change public contracts/API behavior without updating related docs.
- Avoid broad refactors for narrow tasks.

Documentation quality rules:
- Keep root instructions concise and practical.
- Prefer “Do / Do not” constraints where useful.
- Link to source-of-truth docs instead of duplicating large sections.

---

## 6) Cursor / Copilot Rules

Checked and currently not found:

- `.cursor/rules/`
- `.cursorrules`
- `.github/copilot-instructions.md`

If added later:
- Treat them as high-priority constraints.
- Reconcile this AGENTS.md immediately with those files.

---

## 7) Recommended Agent Workflow

1. Confirm repo maturity (docs-only vs executable codebase).
2. Locate real manifests/config files before choosing commands.
3. Run only commands supported by discovered configs.
4. Report command evidence and limitations explicitly.
5. Update AGENTS.md as conventions become concrete.

---

## 8) Current Source-of-Truth References

- `ai-ready-codebase-report.md`
- `ai-ready-report-work/sections/task-14-appendices.md`
- `ai-ready-report-work/sections/task-6-documentation.md`

These currently contain the strongest explicit guidance for this repository.

---

## 9) Maintenance Triggers

Update this file whenever any of the following appears:

- project manifests (`package.json`, `pyproject.toml`, etc.)
- lint/type/test/build configs
- CI workflow definitions
- Cursor/Copilot instruction files

Rule of thumb:
- Prefer precise, verifiable instructions over generic best-practice prose.
