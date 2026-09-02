# SE Vault — Schema

Second-brain database for **Software Engineering**, Manipal University Jaipur.
Maintained on the same LLM Wiki pattern as the CN vault (`../CN_ob_vault`) and
the CAT prep vault. Read this file at the start of every session.

> [!info] State as of 2026-09-02
> Ingested: the **CSE3102 handout** (scope), **one End Term paper** (weightage),
> and **24 lecture decks**. All 30 topic pages exist as **scaffolds** —
> frontmatter, Prerequisites, Overview and deck list, but no subtopics, Quick
> Reference or Question Bank. Building those is the work; see [[SE Roadmap]].
>
> Still missing: **the Pressman textbook** (rule 6 has no fallback), **any
> Mid-Term paper** (the MTE's format is unknown), and **more End Term papers** —
> the corpus is one sitting, which is barely a corpus at all.

## Prime directive

**The vault is only the database. The LLM and the user are the backend.**
Flows (mock papers, cram sheets, worksheets, "what should I revise" queries…)
are invented conversationally as needed — never pre-built as rigid workflows.
The invariant is database quality: every session must leave the wiki current,
consistent, and well-linked. The schema is expected to evolve; when a better
structure emerges, migrate the pages and update this file.

## The eight rules

These govern every judgment call in this vault. They are not negotiable and
they are not defaults. They were learned the hard way in the CN vault — each
one is there because breaking it cost real work — and they are about **where
knowledge comes from**, not about any one subject, so they transfer intact.

1. **The syllabus is the only source of truth for scope.** The course handout
   decides what is in and what is out. A topic that appears in the PYQs but not
   in the syllabus is out. A topic in the syllabus that has never once appeared
   in a PYQ is still in.

2. **The PYQs are the only source of truth for weightage.** Marks distribution,
   which topics get asked, how deeply, and in what form — all of it comes from
   the papers in `raw/sources/`. [[weightage]] is where that lives, and it is
   derived from nothing else.

3. **Never derive weightage from course material.** The number of slides on a
   topic, the length of a Pressman chapter, the count of practice questions in
   a deck — none of it says anything about exam weight. Lecture allocation is
   recorded on topic pages as *syllabus depth*, explicitly not as weightage.

4. **The PYQ syllabus is not this year's syllabus.** Course codes change,
   topics get added and dropped, and an older paper may have been set under a
   different scheme entirely. Record each paper's course code on its page.
   Always cross-check a PYQ question against the current syllabus, and flag
   questions now out of scope rather than silently including them.

5. **The course material may be incomplete.** Slides can be missing, partial,
   or never uploaded. Absence from `raw/sources/ppts/` is **not** evidence a
   topic is out of scope; only the syllabus decides that. Fall back to the
   textbook or flag the gap on the page.

6. **The textbook is useful but excessive.** Pressman/Sommerville is the best
   reference for filling gaps and understanding depth, but it covers far more
   than this course. Use it to explain syllabus topics — never let it expand
   scope. If it is not in the syllabus, do not study it, however thoroughly the
   book treats it. It is the **fallback**, reached for after the decks, not
   before (rule 8).

7. **When rules 1 and 2 pull in different directions** — an in-syllabus topic
   with no PYQ history, or a heavily-asked topic now dropped — **say so
   explicitly** instead of silently picking one.

8. **The lecture decks are the priority source for teaching a topic, and they
   are read first — always, whenever one exists.** They are the closest thing in
   this vault to the examiner's own hand: in the CN vault a deck's worked
   examples repeatedly turned out to be the PYQ questions with the numbers
   changed. **Never cite a deck you have not opened.** On every topic build:
   - Sweep `raw/sources/ppts/` for **every** deck touching the topic, not just
     the obvious one — match by title and by content search, never by lecture
     number (see Layout).
   - Read them **first**, before the textbook and before a word is written.
     The textbook comes after, to fill what the deck leaves out.
   - Record on the page what the deck adds: worked examples that mirror PYQ
     questions, the notation and diagram conventions the course actually uses,
     and **any error in the deck** — in CN, one deck was demonstrably wrong.
   - If no deck covers the topic, say so on the page. That is rule 5's gap, not
     permission to skip the check.

   This is about **content and form only**. Deck volume still says nothing about
   marks — rule 3 is untouched.

   **Rule 8 has a corollary, learned on 2026-09-02:** a deck that appears after
   a sweep can overturn a rule-1 scope call. In CN, a topic absent from the
   entire handout was taught across eleven slides by the instructor setting the
   paper, and was moved into scope on that evidence. If that happens here,
   **record the override as a visible reasoned banner on [[syllabus]]** — never
   silently. Re-sweep `raw/sources/ppts/` by timestamp at the start of a build;
   decks get uploaded mid-semester.

### Source precedence

Which source wins depends on the question being asked. There is no single
ranking, and collapsing these into one is how the rules get broken:

| For… | The authority | Never |
|---|---|---|
| **Scope** — is this in or out | [[syllabus]] (rule 1) | PYQs, decks, textbook |
| **Weightage** — what it's worth | the PYQ papers (rule 2) | decks or textbook, ever (rule 3) |
| **Teaching** — explaining it, worked method, notation, diagram form | **the decks first** (rule 8), then the textbook for gaps and depth (rules 5, 6) | letting either expand scope |

## Layout

- `raw/` — **immutable. Read, never edit.**
  - `raw/sources/` — the syllabus, PYQ papers, and textbook. Editioned sources
    are renamed on ingest to `{content}-{year}-{publisher}.{ext}` (e.g.
    `se-ete-2025-26-mujstella.pdf`) so later editions coexist without collision.
  - `raw/sources/ppts/` — the lecture decks, original filenames kept. **Deck
    lecture numbering does not reliably match the handout's lecture plan** —
    match decks by title and content, never by number. Rule 8: read them on
    every build. They are not plain text and the Read tool cannot open them;
    extract with this, which handles both `.ppt` and `.pptx`:

    ```python
    # .pptx: unzip, pull <a:t> runs from ppt/slides/slideN.xml
    # .ppt (OLE2): regex UTF-16LE and ASCII runs straight out of the bytes,
    #              dedupe, drop shape names (Rectangle N, TextBox N, ...)
    ```

    Sweep by content, not by filename — `grep -ci` the extracted text of every
    deck for the topic's keywords and rank. **SE decks are diagram-heavy**, so
    expect slides whose entire content is an image with no extractable text:
    when a sweep finds a slide title but no body, say so and flag the slide
    number for the user to open by eye rather than inventing what was on it.
  - `raw/submissions/` — the user's worked answers, labelled with the paper ID
    they answer.
- `wiki/` — everything the LLM writes and maintains.
  - `wiki/topics/{phase}/` — one page per syllabus topic, nested by **lifecycle
    phase**. Set on ingest from the handout's **53-lecture plan**, not from its
    five-module grouping: the two disagree on ordering (module 4 pairs modeling
    with quality management; the lecture plan teaches them 25 lectures apart)
    and the lecture plan is the order you meet the material. The ten phases, in
    lecture order: `Foundations` · `Process Models` · `Requirements` ·
    `Project Planning` · `Analysis Modeling` · `Design` · `Construction` ·
    `Testing` · `Quality & Maintenance` · `DevOps`. Wikilinks resolve by
    filename regardless of folder, so the nesting is free.
  - `wiki/topics/SE Roadmap.md` — `type: plan`, not a topic (no status/attempts).
    The ordered study queue with a single mutable *Next up* callout. Read it when
    the user asks what to study next. A second `MTE Roadmap.md` is added when a
    mid-term window is known, scoped to the lectures actually covered.
  - `wiki/papers/` — one page per paper. Ingested PYQ pages sit at the top
    level; **generated** papers go in `wiki/papers/worksheets/` so the real
    corpus stays visually separate from drill.
  - `wiki/index.md` — catalog of all topics, papers, and ingested sources.
  - `wiki/syllabus.md` — static glance-reference of **scope**: the syllabus
    text, the lecture plan, the COs, the assessment split. Content, not progress
    tracking.
  - `wiki/story.md` — static glance-reference of **understanding**: what the
    subject is about, why each phase exists, and why each follows the one
    before. The third of the three, and the one that cannot be memorized —
    [[syllabus]] answers *what is in scope*, [[weightage]] answers *what it is
    worth*, [[story]] answers *why any of it exists*. Regenerate when a topic is
    added or the phase structure changes.

    **SE's story is unusually strong and should be written to exploit that:**
    the lifecycle is already a narrative with causation built in — you cannot
    design what you have not specified, cannot build what you have not designed,
    cannot test what you have not built, and every process model in the course
    is an argument about how rigidly that order must hold. A student who can
    recite that chain can reconstruct most of the syllabus from it. That is the
    page's job.
  - `wiki/weightage.md` — static glance-reference of **marks**, from the PYQs
    only. Deliberately a separate page from `syllabus.md`: rules 1 and 2 name
    different sources of truth, so they get different pages. Never merge them.
  - `wiki/log.md` — append-only timeline.
- `CLAUDE.md` — this file.

## Topic pages

```yaml
---
phase: Requirements          # the lifecycle-phase folder
topic: Requirements Elicitation
lectures: 9-11               # of the handout's 53-lecture plan — depth, NOT weightage
co: CSE3102.2                # course outcome, as printed in the handout
mte: true                    # inside lectures 1-32 — see the override on [[syllabus]]
studied: false               # user's manual "finished learning this" signal
status: not-started          # not-started | weak | developing | strong | mastered
pyq_marks: 0                 # of 80 across the corpus — the rule-2 figure
pyq_marks_latest: 0          # of 80 in the most recent paper; identical while the corpus is one paper
attempts: 0                  # activity volume, not a performance verdict
last_practiced: null         # YYYY-MM-DD
---
```

Both `pyq_marks` denominators are stated on [[weightage]] and change when a
paper is ingested. **While the corpus is a single paper the two fields are
always equal** — keep them so, and split them only when a second paper lands.
`mte` is derived from `lectures`, not judged: true iff the topic's highest
lecture is ≤ 32. The filename is the topic name verbatim so `[[Topic Name]]`-style
wikilinks resolve — keep them in sync on any rename. `status` is a qualitative
judgment maintained from graded papers, Personal Notes, and conversation — not a
formula. Both `pyq_marks` fields are factual counts from the corpus and change
only when a new paper is ingested.

Directly under the H1, before Overview, every topic page carries a one-line
**Prerequisites** entry: the wikilinks to the topics that must be read first for
this page to parse, or `none`. Keep it to what is genuinely load-bearing — two
or three links, not a dependency graph. This is what makes studying in weightage
order survivable: the queue can be reordered freely as long as each page states
its own entry conditions. Anything a page needs that has no topic of its own
(a formula, a distinction) gets **defined on the page that needs it**, not
delegated to a topic the reader has not reached.

Body sections, grown only when there is content for them (no empty
boilerplate): Overview · Quick Reference · Subtopic map · **Mindmap** · **the
numbered subtopics** · Personal Notes · Practice History · Mistakes & Traps ·
Question Bank · Course Material.

**Quick Reference and Question Bank are not optional.** Every topic page carries
both — the one-page cheat sheet and the worked drill set. They are the two
sections the page is actually used from.

### Mindmap

A **mermaid diagram of the whole topic**, sitting directly after the Subtopic map
and before subtopic 1 — the last thing read before diving in, and the thing
reread when the detail stops cohering. One node per subtopic, numbered to match,
with its marks on it, and **labelled edges** carrying the reason one subtopic
leads to the next. The edges are the point: a bare tree of headings adds nothing
the Subtopic map does not already give.

**The diagram and nothing else.** No per-subtopic capsules under it — they were
a third restatement of what Quick Reference tabulates and the Subtopic map
lists, and they were cut on 2026-09-02 for exactly that reason. If a fact is
worth carrying, it belongs in Quick Reference, where it is carried once.

Use `graph TD`/`graph LR` rather than mermaid's `mindmap` type — the flowchart
renderer is the one Obsidian is known to handle here, and labelled edges need it.
**Never put a `[[wikilink]]` inside a mermaid label** — Obsidian renders it as
literal text. Plain text inside diagrams, links outside them.

### Subtopics — the page's spine

**A topic is taught and built one subtopic at a time**, never as one wall. The
division comes **from the lecture decks** (rule 8): follow the deck's own slide
order and section breaks, drop the parts that belong to a different topic page,
and add anything the syllabus names that the deck skipped. The deck decides the
boundaries, the shape below is fixed, and each subtopic gets four parts in this
order:

1. **Intuition** — what the thing is *for*, before any notation: why it
   exists, what breaks without it, the mental picture. **Bullets, three to
   five, one idea each — never a paragraph.** A heavy subtopic may run to
   seven, a never-examined one gets two. Never repeat a table Quick Reference
   already carries; point at it.
2. **Formulas & variables** — the formulas *and* what every variable ranges
   over, the constants worth memorizing, the tables. Never a bare formula. For
   a subtopic whose content is definitional rather than numerical, this part
   becomes **Definitions & distinctions**: the terms that get confused for each
   other, side by side. SE is full of pairs that are examined precisely because
   they are easy to blur — verification vs validation, error/fault/failure,
   coupling vs cohesion, black-box vs white-box.
3. **Solved questions** — worked examples, in full. PYQ questions first, quoted
   verbatim and cited; then the deck's own worked examples (rule 8 — these have
   repeatedly turned out to be the PYQ questions with the numbers changed); the
   textbook's only to fill a gap. **Every step, not a sketch** — the reader is
   learning the method here, not being reminded of it — ending in the answer and
   a `✓` once checked against a printed solution. Numericals follow the **Given →
   Steps → Answer** shape below; drawn answers follow **Diagram answers**.
4. **What gets asked** — sized to the **PYQ marks for that subtopic and nothing
   else** (rule 2, rule 3):
   - **Heavy** (a recurring long-answer block): spell out the question forms,
     the phrasing that identifies each, and the trap each invites.
   - **Light**: one or two lines — "this can be asked as a 2-marker", or just
     what is important here.
   - **Never asked**: say exactly that, and keep it to the definition. Do not
     manufacture drill for a subtopic the corpus has never touched.

Per-subtopic marks must **reconcile to the topic's `pyq_marks`**, with rider
parts counted inside the question that carried them rather than double-counted.

### Bullets, not prose

**Learned 2026-09-02, from the user, after the first fifteen pages were built:
the pages were unnecessarily long.** Measured, they came to ~48,000 words with
*no* correlation to marks — the longest page in the vault (Software Size
Estimation, 4,613 words) was worth zero, and 39% of every word sat above the
first subtopic in four layers that each re-summarised the topic.

The fix is not to drop content. It is to stop writing content as prose:

- **Every explanatory section is bullets.** Intuition, What gets asked,
  Mistakes & Traps, Course Material, the Overview body. One idea per bullet,
  bolded lead-in, no connective paragraph around them.
- **Prose survives in exactly three places:** the Overview weightage banner,
  the *Reading* lines under a diagram, and the narrative steps of a worked
  solution. Everywhere else, bullets or a table.
- **Nothing is deleted, only compressed.** Every fact, every deck verdict,
  every definition pair keeps its line. If a rewrite loses a fact, it is wrong.
- **Say it once.** A fact belongs to Quick Reference *or* to its subtopic, not
  both. A subtopic that needs the table points at Quick Reference by name.
- **Length is earned by marks and by method, in that order.** A 10-mark topic
  may run long; a 0-mark topic is tight *unless* it carries a worked numerical
  or a drawing convention, which are never compressed away — those are the
  method, and method is what the marks are actually paid for.

### Quick Reference

**The one-page cheat sheet — the whole topic, revisable from this section
alone.** What you reread in the ten minutes before the exam, and the test is
that nothing important is missing from it. Not formulas alone: formulas **plus**
the variables they range over, the definition pairs, the diagram notation
legends, and the memorize-this facts (COCOMO coefficient tables, the process
model comparison grid, UML arrowhead meanings, testing-level definitions).
Dense and scannable — tables over prose.

**It must cover every subtopic, including the never-examined ones.** A subtopic
worth zero marks still gets its line — one row, the definition, done. The point
is that a reader revising from Quick Reference alone is never silently missing a
piece of the topic. Weight the space by marks; do not let it drop anything.

### Numerical solutions — Given, then steps

SE looks like a theory subject and is not: COCOMO effort and duration, function
point counting, cyclomatic complexity, PERT/CPM critical paths and slack,
reliability (MTBF/MTTF/availability), defect density, Halstead metrics and
earned value are all standard long-answer numericals.

**Every numerical solution in this vault opens by stating what it was given**,
before a single line of working — on topic pages and in the Question Bank alike.
A short table: each quantity with its symbol and value, units converted where the
question stated them awkwardly (KLOC vs LOC is the classic), and a final **Find**
row naming what is being solved for. Then the numbered steps, one idea each,
showing the substitution and not just the result. Then the answer on its own
line, **with its unit** — person-months and months are different answers to
different questions and are routinely confused.

This is not decoration. Half the traps in this class of question are unit and
mode errors — LOC read as KLOC, organic coefficients used on an embedded
project — and they are caught in the Given block or not at all.

### Diagram answers — legend, then drawing, then reading

**SE's distinctive answer type is a drawing**, and the marks are in the notation
as much as the content: DFDs (context/level-0/level-1 and levelling balance),
UML class, use-case, sequence, state and activity diagrams, ER diagrams, control
flow graphs, and Gantt/PERT charts. A question that says *draw* is graded on
whether the symbols mean what the convention says they mean.

Every drawn answer in this vault carries three parts:

1. **Legend** — the notation being used, stated before the drawing: what each
   shape, arrowhead and line style means in this diagram type, and **which
   convention** (Yourdon vs Gane-Sarson for DFDs; UML version for the rest).
   Conventions differ between textbooks and the deck's convention wins (rule 8).
2. **The diagram** — mermaid where it renders faithfully (`classDiagram`,
   `sequenceDiagram`, `stateDiagram-v2`, `erDiagram`, `flowchart` for CFGs and
   activity diagrams). Where mermaid cannot express the notation honestly — DFDs
   especially, which have no mermaid type and whose bubbles/open-ended stores are
   the examinable part — **do not fake it with a flowchart**: use a clean ASCII
   or table rendering and say what the real symbols are, so the reader draws the
   right thing on paper.
3. **Reading** — two or three lines saying what the diagram asserts, and the
   **rule it must satisfy** to be correct: DFD levelling balance, a class
   diagram's multiplicity at both ends, a sequence diagram's activation
   lifetimes, a CFG's edge count feeding cyclomatic complexity.

An unlabelled diagram is worth close to zero marks in this subject. Label
everything: every arrow, every store, every multiplicity.

### Question forms, inside "What gets asked"

Where a subtopic is heavy enough to name its question forms, each gets:

- **Spot it** — the phrasing that identifies the form in the wild.
- **Method** — the approach, in a line or two.
- **Trap** — the specific wrong turn it invites.

Forms derive from real PYQ questions only. Expect 1–3 per heavy subtopic, not an
exhaustive taxonomy. A solution that contradicts a paper's printed one gets
investigated and the disagreement recorded — third-party solution keys have been
wrong before, and so has a lecture deck.

### Question Bank

**The drill section: every question this topic has, each with a full
step-by-step worked answer.** Not an index — the answers live here, written out,
in a form you can check yourself against. Three tiers, in this order, each
labelled with its source:

1. **PYQ questions** — quoted verbatim and cited to the paper, with the printed
   solution's method followed and a `✓` once checked against it. A disagreement
   with a printed solution gets investigated and recorded.
2. **Deck questions** — the lecture decks' own worked examples and any MCQ or
   practice bank they carry (rule 8). These have repeatedly turned out to be the
   PYQ questions with the numbers changed, so they are drill of the highest
   value even when a form has never been examined.
3. **Textbook questions** — the prescribed textbook's end-of-chapter set, as the
   fallback when the first two are thin (rule 6: to fill gaps, never to expand
   scope).

Solved questions also appear inline inside their subtopic, where they teach the
method in context. That overlap is deliberate: **the subtopic teaches, the
Question Bank drills.** If a topic has no questions in any of the three tiers,
say exactly that rather than inventing them.

### Subtopic map

A table directly under Quick Reference, before the subtopics themselves: one row
per subtopic with its **PYQ marks** and a one-line "why it's here". It is the
page's contents page and its weightage statement in one, and it is what makes
"do the heavy subtopic first" possible without reading the whole page.

### Visual style

Read in Obsidian. Use **callouts** (`> [!type] title`) for material **above the
first subtopic** — the Overview banner, the Quick Reference cram sheet, the
subtopic map's flags. Inside a subtopic, keep the **plain format** (bold inline
labels, blockquoted questions): it reads better for dense worked solutions. One
exception: the **Intuition** part may use `> [!note]` when a memory hook carries
it better than prose.

| Callout | Used for |
|---|---|
| `> [!info]` | the weightage banner at the top of Overview |
| `> [!warning]` | a never-examined topic, or a missing-material gap |
| `> [!abstract]` | Quick Reference hero — the few facts that carry the topic |
| `> [!tip]` | a shortcut or rule of thumb |
| `> [!note]` | asides, memory hooks, cross-references |

Large reference grids (comparison tables, notation legends) stay as plain
tables. No decorative emoji.

**Two Obsidian bugs, both hit in the CN vault, both silent:** a wikilink broken
across a line wrap (`[[Requirements\nElicitation]]`) does not resolve, and a
wikilink inside a mermaid label renders as literal text. Sweep for both before
declaring a build done.

## Paper pages

One file per paper in `wiki/papers/`, paper ID as filename:

```yaml
---
id: se-ete-2025-26
type: pyq                # pyq | mock | worksheet
exam: Odd Semester End Term Examination, November 2025
course_code: <as printed on the paper>
max_marks: 80
topics: ["[[Requirements Elicitation]]", ...]
status: unattempted      # unattempted | graded
score: null
---
```

Body: Notes (paper defects, CO scheme, anything anomalous) · Questions (a table
of every question with its marks, what it asks, and the topic it links to) ·
Results (appended after grading). Every paper page must reconcile: **the marks
in its question table sum to the paper's maximum.**

## Linking rules

The links ARE the second brain. Every page wikilinks to what it relates
to, both directions, updated in the same pass as the content:

- Paper page ↔ every topic page it tested.
- Topic page ↔ every paper that tested it and every source that taught it.
- `index.md` → everything.

A graded paper that doesn't appear on its topics' pages is a maintenance
failure. Graph view should show a connected web, not islands.

## index.md, weightage.md and log.md

- `index.md`: tables of topics (studied/status/marks columns mirroring
  frontmatter — update both in the same pass), papers, and sources.
- `weightage.md`: regenerate whenever a paper is ingested. Both mark totals
  must still reconcile (papers × max marks).
- `log.md`: append-only, newest at the bottom. Format, greppable via
  `grep "^## \[" wiki/log.md`:

  ```
  ## [YYYY-MM-DD] <op> | <short description>
  ```

  where `<op>` is `ingest`, `generate`, `grade`, `query`, `lint`, `scaffold`, or
  another short verb. Do not put escaped `[[...]]` inside log prose — it trips
  the vault's own broken-link sweeps.

## Example flows (illustrations, not an API)

- **Ingest**: a file lands in `raw/sources/` → read it, discuss takeaways,
  update topic pages, add a paper page if it's a paper, re-derive
  [[weightage]], update index, log it.
- **Generate**: user asks for a mock/worksheet → one page in
  `wiki/papers/worksheets/` with a unique ID, weighted by [[weightage]] and by
  weak/untouched topics. Match the real paper structure unless told otherwise.
  Log it.
- **Grade**: answers land in `raw/submissions/` naming a paper ID → grade
  against the paper, append Results, update the topics' frontmatter, Practice
  History and Mistakes & Traps, update index, log it.
- **Query**: "what do I revise tonight", "how's my prep on testing" → read
  index + [[weightage]] + the relevant topic pages (especially Personal Notes)
  and answer; file answers worth keeping into the wiki.
- **Lint** (on request): contradictions, stale stats, missing links, marks that
  no longer reconcile, ungraded submissions, wrapped wikilinks, links inside
  mermaid.

## What this vault still needs

| Want | Why it matters |
|---|---|
| **More End Term papers** | The corpus is **one paper**. Every number on [[weightage]] rests on a single sitting, where "scored zero" and "not asked that day" are the same observation. Two more papers would change that table more than any reasoning about it can. |
| **Any Mid-Term paper** | The handout sets the MTE at 30 marks and says nothing about its sections. The *content* ranking on [[MTE Roadmap]] is evidence-based; the *format* is a guess. |
| **Pressman 8e** → `raw/sources/` | Rule 6's fallback, currently unavailable. Every page must come from decks alone until it lands. |
| **A solution key** | Nothing in this vault is checked against a printed answer, so no `✓` marks exist yet. |

### The image-only deck problem

Ten of the 24 decks are images rather than text — five yield nothing at all,
five yield fragments. Three of the silent ones sit on Mid-Term topics: the agile
models deck, the DFD question sheet, and the design case study. They are listed
in [[index]] with page counts.

**They are readable — by eye, not by extraction.** Read them with the Read tool's
`pages` parameter at build time (max 20 pages per call). Never write a worked
example "from" one of these decks without having actually looked at the slide;
constructed replacements get labelled as constructed.

## Git

Commit after meaningful wiki updates (ingest, generate, grade) with a short
message describing the operation.
