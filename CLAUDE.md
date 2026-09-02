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
  - `wiki/answer-patterns.md` — static glance-reference of **answer shape**:
    the five archetypes every question in the corpus belongs to, each with its
    skeleton, what earns the marks, and a worked exemplar. **The fourth of the
    four glance-references, added 2026-09-03 and the most SE-specific thing in
    this vault.** [[syllabus]] answers *what is in scope*, [[weightage]] *what it
    is worth*, [[story]] *why it exists*, and this one *what a correct answer
    looks like*. Derived from the corpus, so it is regenerated when a paper is
    ingested. Read it before building any topic page.
  - `wiki/weightage.md` — static glance-reference of **marks**, from the PYQs
    only. Deliberately a separate page from `syllabus.md`: rules 1 and 2 name
    different sources of truth, so they get different pages. Never merge them.
  - `wiki/log.md` — append-only timeline.
- `CLAUDE.md` — this file.

## Topic pages

> [!info] Rebuilt 2026-09-03 — the schema is now SE's, not CN's
> The original structure was inherited from the CN vault, where nearly every
> topic is a formula and nearly every question is a calculation. It gave each
> subtopic a *Formulas & variables* part and a *Solved questions* part, which
> is **the numerical archetype and nothing else**. Measured against this
> corpus, that covers 28% of the marks and leaves the largest earner —
> *explain with reason*, 24 of 80 — with no support at all. Evidence of the
> mismatch was visible in the pages themselves: every discursive topic had to
> fall back to an improvised "Definitions & distinctions" part.
>
> **[[answer-patterns]] is now the spine of this vault.** Read it before
> building any topic page.

```yaml
---
phase: Requirements          # the lifecycle-phase folder
topic: Requirements Engineering
lectures: 13                 # of the handout's 53-lecture plan — depth, NOT weightage
co: CSE3102.2                # course outcome, as printed in the handout
mte: true                    # inside lectures 1-32 — see the override on [[syllabus]]
asked_as: [scenario, explain]  # the answer archetypes the corpus has used — see below
studied: false               # user's manual "finished learning this" signal
status: not-started          # not-started | weak | developing | strong | mastered
pyq_marks: 2                 # of 80 across the corpus — the rule-2 figure
assignment_qs: 1             # coursework count — evidence of emphasis, NEVER marks
attempts: 0                  # activity volume, not a performance verdict
last_practiced: null         # YYYY-MM-DD
---
```

**`asked_as` is the field that makes this vault SE-shaped.** Its values are the
five archetypes on [[answer-patterns]]: `scenario` · `explain` · `numerical` ·
`draw` · `compare`. It is a **factual record of how the corpus has asked this
topic**, not a prediction — an empty list means the corpus has never asked it,
which is a rule-7 statement, not permission to skip.

**`assignment_qs` counts coursework questions and is deliberately separate from
`pyq_marks`.** Rule 2 says weightage comes from the exam papers and nothing
else, so an assignment can never move `pyq_marks`. But coursework is direct
evidence of what the instructor thinks matters, and throwing that away would be
its own mistake — so it gets its own field and is read as *emphasis*, never as
*weight*.

`pyq_marks` is stated against the denominator on [[weightage]]. **`pyq_marks_latest`
was removed on 2026-09-03** — the schema itself admitted the two fields are
identical while the corpus is one paper, so it was a column of duplicated data.
Reintroduce it when a second paper lands and the two genuinely differ.

`mte` is derived from `lectures`, not judged: true iff the topic's highest lecture
is ≤ 32. The filename is the topic name verbatim so `[[Topic Name]]` wikilinks
resolve — keep them in sync on any rename. `status` is a qualitative judgment from
graded papers, Personal Notes and conversation — not a formula.

Directly under the H1, before Overview, every topic page carries a one-line
**Prerequisites** entry: the wikilinks to the topics that must be read first for
this page to parse, or `none`. Keep it to what is genuinely load-bearing — two or
three links, not a dependency graph. This is what makes studying in weightage
order survivable: the queue can be reordered freely as long as each page states
its own entry conditions. Anything a page needs that has no topic of its own gets
**defined on the page that needs it**, not delegated to a topic the reader has not
reached.

### The page's shape — six sections, one job each

Rebuilt again on 2026-09-03, after the first pass left **five preamble layers**
(Overview → Quick Reference → How it's asked → Contents → Mindmap) stacked before
any material. That is the same fault the compression pass diagnosed, reintroduced.
The page is now:

```
---
frontmatter
---
# Topic

- two to four orientation bullets: what this topic is, why it exists

**Prerequisites:** ...
**Asked as:** <archetypes> — <marks> in [[se-ete-2025-26]] · <n> in [[se-assign-1-2026]]

**The thread:** one line on how the sections connect   (optional, short topics)

> [!info] What it asked — <question ref, and what it wanted>
> [!warning] any scope, deck-gap or unsourced flag

## How it's asked      ← exam-facing; leads the page
## Quick Reference     ← the cram layer; tables only
## 1 · … 2 · … N · …   ← the material, in deck order
## Practice            ← worked answers, four tiers
## Traps               ← content confusions only
## Sources             ← decks read, gaps, related links
```

**What was removed, and why:**

| Gone | Replaced by |
|---|---|
| `## Overview` | the orientation bullets and the banners, directly under the H1. The section header was a wrapper around two things that stand on their own. |
| `## Contents` | the section headings themselves. Its marks column was near-useless — with one paper, 11 of 15 pages had all-zero rows, so "do the heavy one first" had nothing to point at. Its "why it's here" column duplicated the headings. |
| `## Mindmap` as a top-level layer | a one-line **The thread** under the metadata for short topics; for topics with **five or more sections** the mermaid moves inside Quick Reference, where a recall aid belongs. |

**Renamed** for plain speech: `Question Bank` → **Practice** · `Mistakes & Traps`
→ **Traps** · `Course Material` → **Sources`.

**The division of labour between How it's asked and Traps is strict:**
**How it's asked owns answer-shape traps** (hedging, describing instead of
justifying, stopping after component 1). **Traps owns content confusions** (unit
errors, reversing verification and validation, LOC vs KLOC). If a trap is about
*how you write the answer*, it belongs in the first; if it is about *what you
believe about the material*, the second.

### How it's asked — the section that replaced "What gets asked"

The old schema scattered a *What gets asked* part across every subtopic. That
fragmented the one thing a reader most needs into a dozen pieces and repeated
"never examined" 38 times across the vault. **It is now one section, near the top,
organised by archetype:**

- **One block per archetype in `asked_as`.** Nothing for archetypes the corpus has
  not used — say so once, in a line.
- Each block: **Spot it** (the phrasing) · **Skeleton** (this topic's version, not
  a restatement of the generic one) · **Earns the marks** · **Trap**.
- **Link to [[answer-patterns]] for the generic shape and never repeat it.**
- For a topic the corpus has never asked: name the most likely archetype **and say
  it is a prediction**, per rule 7.
- Anything worth knowing that is not tied to an archetype goes in a short **Also
  worth knowing** list at the end of the section.

### The numbered sections — shaped by type, not by template

**A topic is still taught one section at a time, and the division still comes from
the decks (rule 8).** What changed is the internals: the old fixed four-part
template is gone. **Choose the shape that fits the content**, from four:

| Content type | The shape |
|---|---|
| **Definitional** — terms, taxonomies, lists | a **term table**, then the **confusable pairs** side by side. No prose restatement of the table. |
| **Procedural** — a method, a lifecycle, a sequence of steps | the **steps in order**, each with its output; then what breaks if one is skipped. |
| **Numerical** — a formula and its use | **formula box** (every variable, its meaning, its unit), then a worked example in Given → Steps → Answer form. |
| **Notational** — a diagram convention | **legend**, a **specimen diagram**, and the **validity rule** it must satisfy. |

Every section opens with **two to five bullets of intuition** — what the thing is
for, what breaks without it — and then goes straight to its shape. **No section
repeats a table that Quick Reference already carries; it points at it.**

Length is earned by marks and by method, in that order. A never-examined
definitional section is a term table and four bullets. Do not pad it to match the
shape of a heavy one.

### Mindmap — now conditional

Keep a `graph TD`/`graph LR` diagram **only where the edges carry an argument** —
where one section genuinely causes or motivates the next, as in the process-model
progression or the lifecycle chain. There, the labelled edges are the content.

**Drop it where the topic is a flat list.** A bare tree of section headings adds
nothing the Contents table does not already give, and eight of the built pages had
exactly that. The per-subtopic capsules were removed on 2026-09-02 and are not
coming back — they were a third restatement of Quick Reference.

**Never put a `[[wikilink]]` inside a mermaid label** — Obsidian renders it as
literal text. Plain text inside diagrams, links outside them.

### Contents — the table under Quick Reference

One row per numbered section: **number · name · type · archetype · marks · why
it's here.** It is the page's contents list, its weightage statement and its
answer-shape map in one, and it is what makes "do the heavy one first" possible
without reading the page.

Per-section marks must **reconcile to the topic's `pyq_marks`**, with rider parts
counted inside the question that carried them rather than double-counted.

### Bullets, not prose

**Learned 2026-09-02, from the user: the pages were unnecessarily long.** Measured,
~48,000 words with *no* correlation to marks — the longest page in the vault was
worth zero, and 39% of every word sat above the first subtopic in four layers that
each re-summarised the topic.

- **Every explanatory section is bullets.** One idea per bullet, bolded lead-in,
  no connective paragraph around them.
- **Prose survives in exactly three places:** the Overview banner, the *reading*
  lines under a diagram, and the narrative steps of a worked solution.
- **Nothing is deleted, only compressed.** If a rewrite loses a fact, it is wrong.
- **Say it once.** A fact belongs to Quick Reference *or* to its section, never
  both. A section that needs the table points at Quick Reference by name.

### Quick Reference

**The one-page cheat sheet — the whole topic, revisable from this section alone.**
Formulas **plus** the variables they range over, the definition pairs, the
notation legends, and the memorize-this facts. Dense and scannable — tables over
prose.

**It must cover every section, including never-examined ones.** A section worth
zero marks still gets its line. A reader revising from Quick Reference alone must
never be silently missing a piece of the topic. Weight the space by marks; do not
let it drop anything.

### Numerical solutions — Given, then steps

SE looks like a theory subject and is not: COCOMO, function points, Halstead,
cyclomatic complexity, PERT/CPM, reliability, velocity and capacity are all
standard long-answer numericals — **23 of the paper's 80 marks**.

**Every numerical solution opens by stating what it was given**, before a single
line of working: a table of each quantity with its symbol, value and **unit**,
conversions done here (KLOC vs LOC is the classic), and a final **Find** row.

Then numbered steps, one idea each, showing the substitution. **Show the
log-antilog working for any fractional power** — `log₁₀400 = 2.60206 → × 1.05 =
2.732163 → antilog = 539.71` — because the exam is handwritten and that working is
method marks. Then the answer on its own line **with its unit**, and a **sanity
check** where a second route exists.

Half the traps in this class are unit and mode errors, and they are caught in the
Given block or not at all.

### Diagram answers — legend, then drawing, then reading

**SE's distinctive answer type is a drawing** — 13 of 80 on the paper and 7 of the
assignment's questions — and the marks are in the notation.

1. **Legend** — the convention, stated before the drawing. Where sources differ,
   **the deck's convention wins** (rule 8).
2. **The diagram** — mermaid where it renders faithfully (`classDiagram`,
   `sequenceDiagram`, `stateDiagram-v2`, `erDiagram`, `flowchart`). Where mermaid
   cannot express the notation honestly — **DFDs especially, which have no mermaid
   type and whose bubbles and open-ended stores are the examinable part** — do not
   fake it: use clean ASCII and say what the real symbols are.
3. **Reading** — what the diagram asserts, and **the validity rule** it must
   satisfy. The rules are tabulated on [[answer-patterns]].

**Label everything.** An unlabelled diagram is worth close to zero.

### Question Bank

**The drill section: every question this topic has, each with a full worked
answer.** Four tiers, in this order, each labelled with its source:

1. **PYQ questions** — quoted verbatim and cited, `✓` once checked against a
   printed solution. A disagreement with a printed key gets investigated and
   recorded.
2. **Assignment questions** — quoted and cited to [[se-assign-1-2026]]. **New tier,
   added 2026-09-03.** Coursework, so it never touches `pyq_marks` — but the
   assignment reused two deck questions verbatim and a third with the numbers
   changed, so it is drill of proven value.
3. **Deck questions** — the decks' own worked examples and practice banks (rule 8).
   These have repeatedly turned out to be the assessed questions with the numbers
   changed.
4. **Textbook questions** — the fallback when the first three are thin (rule 6).

**Quote the question verbatim, including its tables.** Learned 2026-09-03: a
paraphrased question cannot be practised against.

Solved questions may also appear inline in their section where they teach the
method. **The section teaches, the Question Bank drills.** Where a full solution
would be duplicated, keep it in the Question Bank and have the section point at
it in two lines.

If a topic has no questions in any tier, say exactly that rather than inventing
them.

### Visual style

Read in Obsidian. Use **callouts** (`> [!type] title`) above the first numbered
section — the Overview banner, the Quick Reference cram sheet, scope flags. Inside
a section, keep the **plain format** (bold inline labels, blockquoted questions):
it reads better for dense worked solutions.

| Callout | Used for |
|---|---|
| `> [!info]` | the weightage banner at the top of Overview |
| `> [!warning]` | a never-examined topic, a missing-material gap, a scope flag |
| `> [!abstract]` | Quick Reference hero — the few facts that carry the topic |
| `> [!tip]` | a shortcut, a rule of thumb, a rule-8 find |
| `> [!note]` | asides, memory hooks, cross-references |

Large reference grids stay as plain tables. No decorative emoji.

**Two Obsidian bugs, both hit in the CN vault, both silent:** a wikilink broken
across a line wrap does not resolve, and a wikilink inside a mermaid label renders
as literal text. Sweep for both before declaring a build done.

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
