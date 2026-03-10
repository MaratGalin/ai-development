# Draft: AI-ready PPTX Presentation

## Requirements (confirmed)
- собрать презентацию PPTX по `ai-ready-report-work/google-slides-blueprint.md`

## Technical Decisions
- Source of truth: `ai-ready-report-work/google-slides-blueprint.md` as primary build spec
- Supporting materials should be reused if needed: `presentation-outline.md`, `presentation-speaker-notes.md`, `presentation-visual-notes.md`, `presentation-source-map.md`, `presentation-verification.md`
- Current workspace has no existing PPTX generation pipeline, no brand asset pack, and no embedded visual asset files for the blueprint's `user-provided visual in session` references
- Visuals marked `user-provided visual in session` should be recreated directly in slides as simple diagrams unless source files are later supplied
- Default automation approach should be `PptxGenJS` rather than Google Slides API or `python-pptx`, because it offers stronger slide-master support, straightforward shape/diagram authoring, speaker notes support, and direct `.pptx` output without Google auth complexity
- Brand requirement default: neutral leadership-style theme, no corporate template assumed

## Research Findings
- `ai-ready-report-work/google-slides-blueprint.md`: complete 12-slide core deck + appendix blueprint with copy, layout, notes, and build instructions
- `ai-ready-report-work/presentation-verification.md`: manual verification patterns exist for deck structure/content, but not for PPTX generation
- No `.pptx`, no slide-export scripts, no Marp/reveal/python-pptx pipeline found in workspace
- External docs review indicates `PptxGenJS` supports slide masters, shapes, formatted text, tables, and speaker notes well; `python-pptx` is viable but less convenient for master-driven deck styling; Google Slides API is powerful but adds authentication/Drive friction for simple local PPTX generation

## Open Questions
- Should the initial PPTX include appendix slides, or only the core 12-slide deck?

## Scope Boundaries
- INCLUDE: PPTX deck assembly plan derived from approved blueprint
- EXCLUDE: inventing missing metrics, assets, or proof points not present in approved materials
