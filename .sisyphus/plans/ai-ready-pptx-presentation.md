# AI-Ready core deck PPTX generation

## TL;DR
> **Summary**: Build a net-new local generator that converts the approved markdown presentation artifacts into a 12-slide `.pptx` core deck, with recreated shape-based visuals and embedded speaker notes. Use `python-pptx` as the default engine and verify output through automated file/XML inspection rather than manual slide review.
> **Deliverables**:
> - local PPTX generator for the 12 core slides
> - normalized intermediate slide spec derived from approved markdown sources
> - generated core-deck `.pptx` file with embedded notes
> - automated PPTX verification commands/scripts for structure and content
> **Effort**: Medium
> **Parallel**: YES - 2 waves
> **Critical Path**: 1 → 2 → 4 → 5/6 → 7 → 8

## Context
### Original Request
Собрать презентацию PPTX по `google-slides-blueprint.md`.

### Interview Summary
- The requested output is now a real `.pptx`, not only markdown planning artifacts.
- Missing visuals referenced as `user-provided visual in session` must be recreated directly in slides as simple diagrams.
- No corporate template is required; use a neutral leadership-style theme.
- Version 1 includes the 12 core slides only; appendix slides are explicitly out of scope.
- The repo has no existing slide-generation pipeline, no PPTX assets, no build scripts, and no existing brand pack.

### Metis Review (gaps addressed)
- Added a required normalization layer so generation does not read conflicting markdown files ad hoc.
- Locked a source-of-truth hierarchy so `google-slides-blueprint.md` outranks all supporting docs when conflicts appear.
- Added PPTX-specific verification requirements: file existence, slide count, title presence, notes presence, and appendix absence via zip/XML inspection.
- Prevented scope creep into brand systems, Google Slides API auth flows, and appendix generation.

## Work Objectives
### Core Objective
Produce a deterministic local workflow that generates a 12-slide PPTX leadership deck from the approved markdown artifacts, using embedded text, embedded speaker notes, and recreated in-slide diagrams that preserve the blueprint meaning.

### Deliverables
- Generator entrypoint for building the core deck PPTX locally
- Normalized machine-readable slide specification derived from markdown inputs
- Slide rendering logic for all 12 core slides
- Embedded speaker notes for all 12 slides
- Automated verification commands/scripts for PPTX structure and core content
- Output file at `ai-ready-report-work/ai-ready-codebase-core-deck.pptx`

### Definition of Done
- `python3 tools/generate_pptx.py --output ai-ready-report-work/ai-ready-codebase-core-deck.pptx` exits with code 0
- `ai-ready-report-work/ai-ready-codebase-core-deck.pptx` exists and has non-zero size
- PPTX container contains exactly 12 slide XML files and exactly 12 notes-slide XML files
- PPTX content includes all 12 approved slide titles and excludes appendix titles
- Final slide includes the approved takeaway `Fund a staged rollout where trust grows only behind proof.`
- Generated deck is built only from approved source materials and recreated shapes; no invented external assets are required

### Must Have
- Source hierarchy: blueprint first, then outline, speaker notes, visual notes, source map
- `python-pptx` as default generation engine
- Embedded speaker notes in the `.pptx` for all 12 slides
- Shape-based diagram recreation for concept visuals
- Automated verification with binary pass/fail commands

### Must NOT Have
- No appendix slides in v1
- No Google Slides API/OAuth/Drive workflow unless a required capability is proven impossible locally
- No invented metrics, screenshots, or brand assets
- No dependency on missing `user-provided visual in session` files
- No manual-only acceptance criteria such as “open PowerPoint and inspect visually”

## Verification Strategy
> ZERO HUMAN INTERVENTION — all verification is agent-executed.
- Test decision: tests-after + command-driven verification using Python and zip/XML inspection
- QA policy: Every task includes generation or validation scenarios with exact commands and expected binary outcomes
- Evidence: `.sisyphus/evidence/task-{N}-{slug}.{ext}`

## Execution Strategy
### Parallel Execution Waves
> Target: 5-8 tasks per wave. <3 per wave (except final) = under-splitting.

Wave 1: source normalization, generator scaffold, shared layout/theme primitives, verification scaffold

Wave 2: slide implementation for slides 1-6, slide implementation for slides 7-12, notes/output integration, final verification hardening

### Dependency Matrix (full, all tasks)
- 1 blocks 3, 5, 6, 7, 8
- 2 blocks 4, 5, 6, 7, 8
- 3 blocks 5, 6, 7
- 4 blocks 5, 6
- 5 blocks 7, 8
- 6 blocks 7, 8
- 7 blocks 8
- 8 blocks Final Verification Wave

### Agent Dispatch Summary
- Wave 1 → 4 tasks → quick / unspecified-low / writing
- Wave 2 → 4 tasks → unspecified-high / deep / quick
- Final Verification → 4 tasks → oracle / unspecified-high / deep

## TODOs
> Implementation + Test = ONE task. Never separate.
> EVERY task MUST have: Agent Profile + Parallelization + QA Scenarios.

- [ ] 1. Define canonical source hierarchy and normalized slide spec

  **What to do**: Create a normalization layer that reads the approved markdown inputs and produces one machine-readable intermediate slide spec for the 12 core slides. Enforce this source precedence: `google-slides-blueprint.md` for title/on-slide copy/footer/layout/build instructions, `presentation-outline.md` for slide message and ordering cross-check, `presentation-speaker-notes.md` for embedded notes, `presentation-visual-notes.md` for visual intent, `presentation-source-map.md` for traceability metadata. Explicitly define conflict resolution so downstream rendering never decides ad hoc which source wins.
  **Must NOT do**: Do not treat `presentation-deck.md` as a co-equal source. Do not include appendix sections. Do not infer missing business claims.

  **Recommended Agent Profile**:
  - Category: `writing` — Reason: source normalization rules and data contracts must be stated clearly and unambiguously
  - Skills: `[]` — no special skill required
  - Omitted: `['git-master']` — no git work needed

  **Parallelization**: Can Parallel: NO | Wave 1 | Blocks: [3, 5, 6, 7, 8] | Blocked By: []

  **References**:
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:7` — core deck build rules and slide-by-slide canonical build spec
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:16` — start of the approved 12-slide sequence
  - Pattern: `ai-ready-report-work/presentation-outline.md:3` — title/order and leadership framing cross-check
  - Pattern: `ai-ready-report-work/presentation-speaker-notes.md:3` — notes sections align one-to-one with slides
  - Pattern: `ai-ready-report-work/presentation-visual-notes.md:7` — visual communication intent for recreated diagrams
  - Pattern: `ai-ready-report-work/presentation-source-map.md:5` — traceability metadata per slide

  **Acceptance Criteria**:
  - [ ] A documented source hierarchy exists in code/comments/docs used by the generator, with blueprint declared highest priority
  - [ ] The intermediate spec contains exactly 12 core slide records and zero appendix records
  - [ ] Each slide record includes at minimum: title, bullets, footer takeaway, layout type, visual type/recipe, notes text, and source references
  - [ ] Generator execution fails fast with a clear error if any required source section is missing for a core slide

  **QA Scenarios**:
  ```
  Scenario: Build normalized core-slide spec
    Tool: Bash
    Steps: Run `python3 tools/generate_pptx.py --dump-spec --output /tmp/ai-ready-core-deck.pptx > .sisyphus/evidence/task-1-normalized-spec.json`
    Expected: command exits 0 and evidence JSON contains 12 slide objects with titles matching the approved core deck
    Evidence: .sisyphus/evidence/task-1-normalized-spec.json

  Scenario: Appendix excluded from normalized spec
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import json
from pathlib import Path
p = Path('.sisyphus/evidence/task-1-normalized-spec.json')
data = json.loads(p.read_text())
titles = [s['title'] for s in data['slides']]
print(any('Appendix' in t for t in titles))
PY`
    Expected: prints `False`
    Evidence: .sisyphus/evidence/task-1-normalized-spec.txt
  ```

  **Commit**: NO | Message: `feat(presentation): define normalized slide spec` | Files: `tools/generate_pptx.py`, related helper modules

- [ ] 2. Select and scaffold the local PPTX generation engine with deterministic entrypoint

  **What to do**: Implement the generator around `python-pptx` and define a single deterministic CLI entrypoint, default output path, slide size, typography defaults, spacing constants, color palette, and helper abstractions for title, bullet stack, footer takeaway, callout bars, and notes. Keep the implementation local-file based and independent from external APIs.
  **Must NOT do**: Do not introduce Google Slides API, Drive API, or browser automation for primary generation. Do not require Node/npm as the default path.

  **Recommended Agent Profile**:
  - Category: `quick` — Reason: scaffolding and library wiring are bounded implementation work
  - Skills: `[]` — no special skill required
  - Omitted: `['playwright']` — no browser interaction needed

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: [4, 5, 6, 7, 8] | Blocked By: []

  **References**:
  - External: `https://context7.com/scanny/python-pptx/llms.txt` — python-pptx support for text boxes, tables, shapes, and notes
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:9` — leadership-facing simplicity rules to encode as defaults
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:35` — repeated build-instructions pattern suggests reusable slide primitives

  **Acceptance Criteria**:
  - [ ] `python3 tools/generate_pptx.py --output ai-ready-report-work/ai-ready-codebase-core-deck.pptx` is a valid command and exits 0 after implementation
  - [ ] The generator sets an explicit slide size and uses only locally available fonts/styles
  - [ ] Shared helper functions/classes exist for repeated layout primitives so slide logic does not duplicate raw positioning everywhere
  - [ ] The generator can create a non-empty PPTX even before all final slides are fully rendered

  **QA Scenarios**:
  ```
  Scenario: Generator entrypoint produces a PPTX file
    Tool: Bash
    Steps: Run `python3 tools/generate_pptx.py --output ai-ready-report-work/ai-ready-codebase-core-deck.pptx`
    Expected: exit code 0 and file `ai-ready-report-work/ai-ready-codebase-core-deck.pptx` exists
    Evidence: .sisyphus/evidence/task-2-generate.txt

  Scenario: Generated file is not empty
    Tool: Bash
    Steps: Run `python3 - <<'PY'
from pathlib import Path
p = Path('ai-ready-report-work/ai-ready-codebase-core-deck.pptx')
print(p.exists(), p.stat().st_size > 0)
PY`
    Expected: prints `True True`
    Evidence: .sisyphus/evidence/task-2-file-check.txt
  ```

  **Commit**: NO | Message: `feat(presentation): scaffold pptx generator` | Files: `tools/generate_pptx.py`, helper modules, requirements if needed

- [ ] 3. Encode shared layout system and slide-theme primitives

  **What to do**: Build reusable layout recipes for the blueprint’s recurring structures: two-column contrast, visual-led slide with side bullets, side-by-side mirrored panels, diagram-first slide, horizontal flow, three-column inventory, boundary diagram with narrow text strip, graph-led slide, layered hierarchy, lifecycle loop, and autonomy ladder. Define a neutral non-branded leadership theme with sentence-case titles, 3–4 concise bullets, and one strong footer bar/takeaway line.
  **Must NOT do**: Do not build a full corporate design system. Do not over-style diagrams or depend on external icon packs.

  **Recommended Agent Profile**:
  - Category: `unspecified-high` — Reason: requires careful abstraction over multiple slide patterns without overengineering
  - Skills: `[]` — no special skill required
  - Omitted: `['frontend-ui-ux']` — deck styling is bounded, not a full UI design exercise

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: [5, 6, 7] | Blocked By: [1]

  **References**:
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:26` — two-column contrast pattern
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:49` — visual-led pattern
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:72` — mirrored side-by-side comparison
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:95` — diagram-first attention slide
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:118` — horizontal flow for Dynamic Context Layer
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:163` — three-column inventory

  **Acceptance Criteria**:
  - [ ] The rendering layer exposes named layout helpers that map directly to blueprint layout patterns
  - [ ] Theme defaults enforce readable title, bullet, and takeaway hierarchy without per-slide reinvention
  - [ ] All recreated diagrams can be composed from shapes, lines, arrows, text, and fills available in `python-pptx`
  - [ ] Layout helpers support binary selection by slide spec rather than manual branching on raw coordinates in every slide implementation

  **QA Scenarios**:
  ```
  Scenario: Layout helpers cover all core slide types
    Tool: Bash
    Steps: Run `python3 tools/generate_pptx.py --dump-spec --output /tmp/ai-ready-core-deck.pptx > .sisyphus/evidence/task-3-layout-spec.json` and verify every slide's `layout_type` maps to an implemented helper via generator self-check
    Expected: command exits 0 with no "unknown layout" errors
    Evidence: .sisyphus/evidence/task-3-layout-spec.json

  Scenario: Missing layout type fails loudly
    Tool: Bash
    Steps: Run the generator's built-in self-check or unit-style command against an intentionally invalid layout fixture if provided
    Expected: non-zero exit code with explicit "unknown layout type" error
    Evidence: .sisyphus/evidence/task-3-layout-error.txt
  ```

  **Commit**: NO | Message: `feat(presentation): add reusable slide layouts` | Files: rendering helpers and theme modules

- [ ] 4. Add PPTX-specific verification utilities and commands

  **What to do**: Extend the repo’s markdown verification pattern into PPTX verification utilities. Add commands/scripts that inspect the generated `.pptx` as a zip container and verify slide count, notes count, title presence, takeaway presence, appendix absence, and optionally per-slide ordering markers. Keep the checks local and scriptable.
  **Must NOT do**: Do not rely on opening PowerPoint manually. Do not verify only the source markdown while ignoring the generated PPTX.

  **Recommended Agent Profile**:
  - Category: `quick` — Reason: validation utilities are bounded and command-oriented
  - Skills: `[]` — no special skill required
  - Omitted: `['playwright']` — browser checks are not required for v1

  **Parallelization**: Can Parallel: YES | Wave 1 | Blocks: [8] | Blocked By: [2]

  **References**:
  - Pattern: `ai-ready-report-work/presentation-verification.md:13` — command-verification style to mirror
  - Pattern: `ai-ready-report-work/presentation-verification.md:17` — exact-count verification precedent
  - Pattern: `ai-ready-report-work/presentation-verification.md:83` — sequence/order verification precedent

  **Acceptance Criteria**:
  - [ ] A command exists that prints `12` for slide XML count in the generated PPTX
  - [ ] A command exists that prints `12` for notes-slide XML count in the generated PPTX
  - [ ] A command exists that confirms approved titles are present in PPTX XML text
  - [ ] A command exists that confirms appendix titles are absent from PPTX XML text

  **QA Scenarios**:
  ```
  Scenario: Verify slide and notes counts from PPTX container
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import re, zipfile
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
with zipfile.ZipFile(pptx) as z:
    slides = sorted(n for n in z.namelist() if re.match(r'ppt/slides/slide\d+\.xml$', n))
    notes = sorted(n for n in z.namelist() if re.match(r'ppt/notesSlides/notesSlide\d+\.xml$', n))
    print(len(slides), len(notes))
PY`
    Expected: prints `12 12`
    Evidence: .sisyphus/evidence/task-4-counts.txt

  Scenario: Verify appendix titles are absent
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import zipfile
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
forbidden=['Appendix 1.','Appendix 2.','Appendix 3.','Appendix 4.','Appendix 5.','Appendix 6.']
with zipfile.ZipFile(pptx) as z:
    blob=b'\n'.join(z.read(n) for n in z.namelist() if n.startswith('ppt/slides/slide') and n.endswith('.xml'))
text=blob.decode('utf-8', errors='ignore')
print(all(item not in text for item in forbidden))
PY`
    Expected: prints `True`
    Evidence: .sisyphus/evidence/task-4-appendix-absent.txt
  ```

  **Commit**: NO | Message: `test(presentation): add pptx verification commands` | Files: verification script(s), docs updates if needed

- [ ] 5. Implement slides 1-6 with recreated visuals and approved copy

  **What to do**: Render slides 1 through 6 from the normalized spec using shared layout helpers. Use the blueprint as canonical for on-slide copy, takeaway, and layout instructions. Recreate concept visuals with simple shapes/lines/text only: two-column contrast (slide 1), wandering no-prep path (slide 2), mirrored prepared vs unprepared journey (slide 3), attention/compaction container diagram (slide 4), Dynamic Context Layer flow (slide 5), and the crowding/decomposition/scoping workflow (slide 6). Embed the corresponding speaker notes for each slide.
  **Must NOT do**: Do not use missing external images as blockers. Do not add more than the approved bullets/takeaway. Do not reinterpret slide order or messaging.

  **Recommended Agent Profile**:
  - Category: `unspecified-high` — Reason: combines rendering logic, content fidelity, and diagram recreation across six distinct slides
  - Skills: `[]` — no special skill required
  - Omitted: `['frontend-ui-ux']` — must follow blueprint, not redesign it

  **Parallelization**: Can Parallel: YES | Wave 2 | Blocks: [7, 8] | Blocked By: [1, 2, 3]

  **References**:
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:16` — slide 1 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:38` — slide 2 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:61` — slide 3 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:84` — slide 4 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:107` — slide 5 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:130` — slide 6 canonical copy/layout/build instructions
  - Test: `ai-ready-report-work/presentation-speaker-notes.md:3` — notes text for slides 1-6
  - Test: `ai-ready-report-work/presentation-visual-notes.md:7` — visual intent for slides 1-6

  **Acceptance Criteria**:
  - [ ] Slides 1-6 exist in the generated PPTX in the approved order
  - [ ] Each of slides 1-6 includes its approved title, on-slide bullets, and footer takeaway text
  - [ ] Each of slides 1-6 includes embedded notes text from `presentation-speaker-notes.md`
  - [ ] Each recreated visual follows the blueprint’s communication intent without relying on unavailable image files

  **QA Scenarios**:
  ```
  Scenario: Verify titles for slides 1-6 are present
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import zipfile
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
expected=[
 'AI-Ready Codebase: not about the model, about the environment',
 'What happens without preparation',
 'What changes after preparation',
 'Why long context does not save us: attention limits',
 'Dynamic Context Layer',
 'Before coding: crowding, decomposition, scoping'
]
with zipfile.ZipFile(pptx) as z:
    blob=b'\n'.join(z.read(n) for n in z.namelist() if n.startswith('ppt/slides/slide') and n.endswith('.xml'))
text=blob.decode('utf-8', errors='ignore')
for item in expected:
    print(item, item in text)
PY`
    Expected: each line ends with `True`
    Evidence: .sisyphus/evidence/task-5-titles.txt

  Scenario: Verify slide 1-6 notes exist in PPTX
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import zipfile,re
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
needles=['Open with the decision, not the technology trend.','In an unprepared codebase, the agent spends most of its effort','This is the core systems idea.','Good agent work starts before implementation.']
with zipfile.ZipFile(pptx) as z:
    notes=b'\n'.join(z.read(n) for n in z.namelist() if re.match(r'ppt/notesSlides/notesSlide\d+\.xml$', n))
text=notes.decode('utf-8', errors='ignore')
for item in needles:
    print(item, item in text)
PY`
    Expected: each line ends with `True`
    Evidence: .sisyphus/evidence/task-5-notes.txt
  ```

  **Commit**: NO | Message: `feat(presentation): render slides 1-6` | Files: generator render modules

- [ ] 6. Implement slides 7-12 with recreated visuals and approved copy

  **What to do**: Render slides 7 through 12 from the normalized spec using shared layout helpers. Recreate inventory, boundary, ontology, documentation hierarchy, lifecycle loop, and autonomy-ladder visuals using shapes and text. Preserve the leadership framing and final ask exactly as written in the blueprint. Embed notes for all six slides.
  **Must NOT do**: Do not drift into appendix content. Do not create extra implementation-program slides or add unsupported evidence points.

  **Recommended Agent Profile**:
  - Category: `unspecified-high` — Reason: second half of deck includes several semantically distinct diagrams and the final decision slide
  - Skills: `[]` — no special skill required
  - Omitted: `['frontend-ui-ux']` — must preserve blueprint intent, not redesign

  **Parallelization**: Can Parallel: YES | Wave 2 | Blocks: [7, 8] | Blocked By: [1, 2, 3]

  **References**:
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:153` — slide 7 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:175` — slide 8 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:198` — slide 9 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:221` — slide 10 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:244` — slide 11 canonical copy/layout/build instructions
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:267` — slide 12 canonical copy/layout/build instructions
  - Test: `ai-ready-report-work/presentation-speaker-notes.md:44` — notes text for slides 7-12
  - Test: `ai-ready-report-work/presentation-visual-notes.md` — visual intent for slides 7-12

  **Acceptance Criteria**:
  - [ ] Slides 7-12 exist in the generated PPTX in the approved order
  - [ ] Each of slides 7-12 includes its approved title, bullets, and footer takeaway text
  - [ ] Slide 12 includes the exact Year 1 ask and final takeaway text from the blueprint
  - [ ] Each of slides 7-12 includes embedded notes text from `presentation-speaker-notes.md`

  **QA Scenarios**:
  ```
  Scenario: Verify titles for slides 7-12 are present
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import zipfile
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
expected=[
 'What must actually be built in the project',
 'AI-ready architecture: module boundaries and external contracts',
 'Project ontology and domain graphs',
 'Memoberry Bank: documentation as a navigation system',
 'Documentation lifecycle and ADR lifecycle',
 'Verification is the bridge to autonomy'
]
with zipfile.ZipFile(pptx) as z:
    blob=b'\n'.join(z.read(n) for n in z.namelist() if n.startswith('ppt/slides/slide') and n.endswith('.xml'))
text=blob.decode('utf-8', errors='ignore')
for item in expected:
    print(item, item in text)
PY`
    Expected: each line ends with `True`
    Evidence: .sisyphus/evidence/task-6-titles.txt

  Scenario: Verify final-slide ask and takeaway are present
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import zipfile
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
needles=[
 'Year 1 ask: baseline measurement, one limited pilot, enforced guardrails, Dynamic Context infrastructure, self-hosted constraints',
 'Fund a staged rollout where trust grows only behind proof.'
]
with zipfile.ZipFile(pptx) as z:
    blob=b'\n'.join(z.read(n) for n in z.namelist() if n.startswith('ppt/slides/slide') and n.endswith('.xml'))
text=blob.decode('utf-8', errors='ignore')
for item in needles:
    print(item, item in text)
PY`
    Expected: each line ends with `True`
    Evidence: .sisyphus/evidence/task-6-final-slide.txt
  ```

  **Commit**: NO | Message: `feat(presentation): render slides 7-12` | Files: generator render modules

- [ ] 7. Integrate slide assembly, notes embedding, and deterministic output ordering

  **What to do**: Combine normalized data, layout helpers, and slide renderers into one end-to-end generation pass that always outputs the 12 core slides in canonical order with notes attached to the corresponding slides. Ensure output naming is stable and generation is repeatable.
  **Must NOT do**: Do not let slide order depend on filesystem ordering or markdown parsing quirks. Do not drop notes silently.

  **Recommended Agent Profile**:
  - Category: `quick` — Reason: final assembly and ordering logic should be narrow after rendering pieces are complete
  - Skills: `[]` — no special skill required
  - Omitted: `['git-master']` — no git work needed

  **Parallelization**: Can Parallel: NO | Wave 2 | Blocks: [8] | Blocked By: [1, 2, 3, 5, 6]

  **References**:
  - Pattern: `ai-ready-report-work/presentation-outline.md:3` — canonical 12-slide sequence
  - Pattern: `ai-ready-report-work/presentation-speaker-notes.md:79` — slide 12 notes confirm end-of-core-deck boundary
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:267` — final core slide boundary before appendix rules

  **Acceptance Criteria**:
  - [ ] The generated PPTX always contains slides 1-12 in the same approved order
  - [ ] The generated PPTX contains exactly 12 notes slides, aligned to the 12 core slides
  - [ ] Output path defaults to `ai-ready-report-work/ai-ready-codebase-core-deck.pptx`
  - [ ] Re-running the generator overwrites or regenerates the same target file deterministically

  **QA Scenarios**:
  ```
  Scenario: Verify output ordering matches approved sequence
    Tool: Bash
    Steps: Run generator, then run a verification command/script that extracts slide XML text in order and checks the 12 approved titles appear in sequence
    Expected: exit code 0 with explicit success message for ordered title match
    Evidence: .sisyphus/evidence/task-7-order.txt

  Scenario: Verify notes count aligns with slide count
    Tool: Bash
    Steps: Run `python3 - <<'PY'
import re, zipfile
pptx='ai-ready-report-work/ai-ready-codebase-core-deck.pptx'
with zipfile.ZipFile(pptx) as z:
    slides=len([n for n in z.namelist() if re.match(r'ppt/slides/slide\d+\.xml$', n)])
    notes=len([n for n in z.namelist() if re.match(r'ppt/notesSlides/notesSlide\d+\.xml$', n)])
    print(slides == notes == 12)
PY`
    Expected: prints `True`
    Evidence: .sisyphus/evidence/task-7-notes-alignment.txt
  ```

  **Commit**: NO | Message: `feat(presentation): assemble deterministic core deck output` | Files: generator main flow

- [ ] 8. Harden end-to-end verification and failure reporting for v1 delivery

  **What to do**: Finalize a repeatable verification workflow that generates the PPTX and runs all structural/content checks in one pass. Include clear failure messages for missing source sections, unsupported layout types, missing notes, wrong slide count, title mismatches, and accidental appendix leakage. Document the exact command sequence for future regeneration.
  **Must NOT do**: Do not leave validation scattered across ad hoc shell snippets only. Do not allow silent partial success.

  **Recommended Agent Profile**:
  - Category: `deep` — Reason: this is the quality gate that converts multiple moving parts into a trustworthy delivery workflow
  - Skills: `[]` — no special skill required
  - Omitted: `['playwright']` — browser preview is optional and out of critical path

  **Parallelization**: Can Parallel: NO | Wave 2 | Blocks: [Final Verification Wave] | Blocked By: [1, 2, 4, 5, 6, 7]

  **References**:
  - Pattern: `ai-ready-report-work/presentation-verification.md:3` — acceptance should be based on command-verifiable structure and cross-artifact coherence
  - Pattern: `ai-ready-report-work/presentation-source-map.md:5` — slide traceability confirms canonical titles/content ground truth
  - Pattern: `ai-ready-report-work/google-slides-blueprint.md:290` — appendix is explicitly backup material and therefore out of v1 scope

  **Acceptance Criteria**:
  - [ ] One documented command sequence generates and verifies the deck end to end with zero manual steps
  - [ ] Failure messages name the exact missing slide, section, or verification rule that failed
  - [ ] Verification checks include slide count, notes count, approved title presence, final takeaway presence, and appendix absence
  - [ ] Successful verification leaves evidence files under `.sisyphus/evidence/`

  **QA Scenarios**:
  ```
  Scenario: End-to-end generation and verification pass
    Tool: Bash
    Steps: Run the documented generation command followed by the documented verification command/script bundle
    Expected: all commands exit 0 and evidence files for counts, titles, notes, and appendix exclusion are created
    Evidence: .sisyphus/evidence/task-8-end-to-end.txt

  Scenario: Missing required source section fails with explicit error
    Tool: Bash
    Steps: Run generator self-check against a temporary invalid fixture or built-in validation mode that simulates a missing slide section
    Expected: non-zero exit code and explicit error naming the missing slide/section
    Evidence: .sisyphus/evidence/task-8-missing-section.txt
  ```

  **Commit**: NO | Message: `test(presentation): harden end-to-end pptx verification` | Files: verification tooling and generator validation paths

## Final Verification Wave (4 parallel agents, ALL must APPROVE)
- [ ] F1. Plan Compliance Audit — oracle
- [ ] F2. Code Quality Review — unspecified-high
- [ ] F3. Real Manual QA — unspecified-high (+ playwright if UI import preview is added)
- [ ] F4. Scope Fidelity Check — deep

## Commit Strategy
- No commit required by default.
- If the executor is later asked to commit, use one commit after generation and verification succeed.
- Preferred commit message: `feat(presentation): generate ai-ready core deck pptx`

## Success Criteria
- The repo can generate the 12-slide core deck deterministically from markdown sources
- The output is a local `.pptx`, not only a Google Slides manual guide
- The deck preserves approved narrative order, notes, and takeaways
- The workflow proves appendix exclusion and notes inclusion automatically
