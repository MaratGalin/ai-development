# Presentation Verification

Purpose: define the final acceptance checks for the five markdown planning artifacts so final approval can be based on command-verifiable structure and cross-artifact coherence rather than subjective review.

Artifacts under verification:
- `presentation-outline.md`
- `presentation-speaker-notes.md`
- `presentation-appendix-outline.md`
- `presentation-source-map.md`
- `presentation-visual-notes.md`


## Command Checks

Run all commands from `/home/marat/ocrv/ai-development/ai-ready-report-work`.

### 1. Outline has exactly 12 core slides

Command:

```bash
grep -c '^## Slide [0-9]\+\.' presentation-outline.md
```

Expected result:
- returns `12`

Why it matters:
- confirms the core deck stayed within the approved 12-slide structure

### 2. Speaker notes cover exactly 12 core slides

Command:

```bash
grep -c '^## Slide [0-9]\+\.' presentation-speaker-notes.md
```

Expected result:
- returns `12`

Why it matters:
- confirms every core slide has a matching notes section and no extra hidden narrative was added

### 3. Appendix keeps the approved objection-indexed structure

Commands:

```bash
grep -c '^## Appendix [0-9]\+\.' presentation-appendix-outline.md
grep -n '^## Appendix [0-9]\+\. ".*"$' presentation-appendix-outline.md
grep -n '^## Appendix Use Rules$' presentation-appendix-outline.md
```

Expected result:
- first command returns `6`
- second command returns 6 matches, one for each objection-style appendix title
- third command returns 1 match

Why it matters:
- confirms the appendix is grouped by objections rather than retelling the main deck
- confirms the appendix keeps explicit usage boundaries

### 4. Source map covers all 12 slides

Commands:

```bash
grep -c '^## Slide [0-9]\+\.' presentation-source-map.md
grep -c '\*\*Primary report refs:\*\*' presentation-source-map.md
grep -c '\*\*Core claim:\*\*' presentation-source-map.md
```

Expected result:
- first command returns `12`
- second command returns `12`
- third command returns `12`

Why it matters:
- confirms every core slide has its own source-map section
- confirms every slide is grounded in the report, not only transcript notes or visuals

### 5. Source map order matches outline order

Command:

```bash
grep '^## Slide [0-9]\+\.' presentation-outline.md > /tmp/presentation-outline-slides.txt && grep '^## Slide [0-9]\+\.' presentation-source-map.md > /tmp/presentation-source-map-slides.txt && diff -u /tmp/presentation-outline-slides.txt /tmp/presentation-source-map-slides.txt
```

Expected result:
- no diff output

Why it matters:
- confirms source traceability follows the same slide order as the core narrative

### 6. Notes order matches outline order

Command:

```bash
grep '^## Slide [0-9]\+\.' presentation-outline.md > /tmp/presentation-outline-slides.txt && grep '^## Slide [0-9]\+\.' presentation-speaker-notes.md > /tmp/presentation-notes-slides.txt && diff -u /tmp/presentation-outline-slides.txt /tmp/presentation-notes-slides.txt
```

Expected result:
- no diff output

Why it matters:
- confirms speaker notes preserve the core outline sequence instead of drifting into a different narrative order

### 7. Appendix usage rules prevent main-deck duplication

Command:

```bash
grep -n 'not a second core deck\|Do not retell the 12-slide narrative in order\|Prefer tables, thresholds, examples, and exception handling' presentation-appendix-outline.md
```

Expected result:
- returns matches for all three guardrails

Why it matters:
- confirms the appendix stays backup-only and does not duplicate the live deck

### 8. Visual notes cover all 12 slides

Command:

```bash
grep -c '^## Slide [0-9]\+\.' presentation-visual-notes.md
```

Expected result:
- returns `12`

Why it matters:
- confirms visual planning exists for every core slide, ensuring communication intent is documented before design implementation

### 9. Visual notes include visual type guidance

Command:

```bash
grep -c 'Visual type:' presentation-visual-notes.md
```

Expected result:
- returns at least `12` (all core slides have visual type documented)

Why it matters:
- confirms each slide has explicit visual type guidance, preventing drift into design speculation without communication intent

### 10. Visual notes include presenter reading guidance

Command:

```bash
grep -c 'Reading guidance for presenter:' presentation-visual-notes.md
```

Expected result:
- returns at least `12` (all slides have presenter guidance)

Why it matters:
- confirms visual-heavy slides include explicit reading order, reducing misinterpretation risk during live delivery

## Coherence Audit

These checks confirm that the five artifacts are not only structurally complete, but also narratively aligned.

### A. One primary decision only

Audit question:
- Do all artifacts support one decision: approve the Year-1 AI-ready rollout built around baseline measurement, guardrails, a limited pilot, and self-hosted constraints?

Pass condition:
- the opening outline slide frames the approval decision
- the closing outline slide repeats the Year-1 ask
- speaker notes open and close on the same approval logic
- no appendix section introduces a competing strategic decision

### B. Recommendation-first framing stays intact

Audit question:
- Does the deck stay recommendation-first instead of turning into a report summary?

Pass condition:
- slide 1 contains the decision frame
- slide 2 starts with failure pattern evidence
- slides 3-11 justify the decision through mechanism and build program
- slide 12 closes on verification-backed approval, not an open-ended recap

### C. Anti-duplication boundaries for slides 4-6

Audit question:
- Are the most overlap-prone mechanism slides still separated cleanly?

Pass condition:
- slide 4 owns attention limits and compaction only
- slide 5 owns dynamic context selection/composition only
- slide 6 owns crowding, decomposition, and scoping only
- notes and source-map sections preserve the same ownership split and order

### D. Anti-duplication boundaries for slides 8-11

Audit question:
- Are the later infrastructure slides still separated by function rather than blended together?

Pass condition:
- slide 8 owns module boundaries and external contracts
- slide 9 owns ontology and domain graphs
- slide 10 owns documentation as navigation/progressive disclosure
- slide 11 owns documentation freshness, ADR lifecycle, and source-of-truth consolidation

### E. Appendix does not duplicate the main deck

Audit question:
- Does the appendix deepen objections instead of replaying the 12-slide sequence?

Pass condition:
- appendix titles are phrased as leadership objections/questions
- appendix use rules explicitly ban retelling the main deck in order
- appendix material adds caveats, tables, thresholds, or exceptions rather than restating core slide messages

### F. Source map and notes preserve outline order

Audit question:
- Can a reader move from outline to notes to sources without losing sequence or thesis?

Pass condition:
- all three core artifacts use slide numbers 1-12 in the same order
- notes reinforce each outline slide's message rather than introducing new side narratives
- source map traces each slide to evidence in the same order as the outline

### G. Async-circulation logic check

Audit question:
- Can the deck still make the same recommendation if a leader reads the outline plus notes without hearing the live talk?

Pass condition:
- each notes section contains a leadership takeaway and transition logic
- the opening and closing slides state the decision clearly enough for async readers
- appendix remains optional, not required to understand the recommendation

### H. Visual notes stay subordinate to outline and source map

SZ|Audit question:
- Do visual notes remain planning guidance rather than becoming a design spec or new evidence layer?

KN|Pass condition:
- visual notes describe communication intent, not visual design implementation (e.g., "Visual type" not "Design spec")
- visual notes do not introduce new evidence or sources beyond what the outline and source-map establish
- visual notes reference the same slide order as the outline (1-12) without adding, removing, or reordering slides
- visual notes' "What the visual must communicate" aligns with the outline's slide message, not contradicting or expanding it

Why it matters:
- ensures visual planning supports the approved narrative rather than drifting into parallel design authority
- prevents visual notes from becoming a shadow deck that competes with the outline as source of truth
## No visual runtime validation required

No visual runtime validation required: these deliverables are markdown planning artifacts, not executable UI, browser flows, or slide-rendering code. Final acceptance should therefore stay content-centric and command-verifiable. Browser QA or runtime UI checks become relevant only if a later task converts this material into a presentation tool, app, or rendered slide system.
