---
phase: Foundations
topic: Software Engineering as a Layered Technology
lectures: 4-5
co: CSE3102.1
asked_as: []
mte: true
studied: false
status: not-started
pyq_marks: 0
assignment_qs: 0
attempts: 0
last_practiced: null
---

# Software Engineering as a Layered Technology

**Prerequisites:** [[Introduction to Software Engineering]]

## Overview

> [!warning] 0 of 80 in [[se-ete-2025-26]] — not asked once, on one paper
> A single paper cannot show a topic is unexamined, only that it was not asked
> that day. In syllabus and taught, so fully examinable. Lectures 4-5 is
> *syllabus depth* and rule 3 forbids reading it as marks.

- **What it supplies:** four layers, each resting on the one below, and a
  **process framework** of five activities every project performs whatever model
  it follows.
- **Why it matters:** it is the vocabulary the rest of the course speaks in —
  "framework activity", "umbrella activity" and "process model" get their
  meanings here.

> [!warning] This page is almost entirely unsourced
> Zero deck hits for "layered", "umbrella", "generic process" and "process
> framework" as lecture content, across all 24 decks. The handout names all of
> them in lecture 4, and again in Module 1 and the syllabus paragraph. Pressman
> 8e is not in `raw/sources/`, so rule 6's fallback is unavailable too.
> Everything except subtopic 4 is **standard Pressman material, not your
> instructor's slides.** Rule 5: deck silence is not evidence of being out of
> scope. **This is the page to fix first if you can get the lecture 4-5 slides.**

## Quick Reference

> [!abstract] The two structures that carry this topic
> - **The four layers, bottom-up: quality focus → process → methods → tools.**
>   Each rests on the one beneath. Quality focus is the bedrock, not the top.
> - **Five framework activities: communication, planning, modeling,
>   construction, deployment.** Every project does all five. What changes between
>   process models is *how often and in what order*, never *whether*.

**The layered technology** — read bottom-up; drawing it upside down is the
classic error:

| Layer | What it is | If it is missing |
|---|---|---|
| **Tools** | automated or semi-automated support (CASE tools) | methods must be applied by hand |
| **Methods** | the technical "how to": requirements analysis, design, coding, testing | the process has activities but no technique to perform them |
| **Process** | the glue — holds methods and tools together, defines order and deliverables | methods are applied ad hoc; results are unrepeatable |
| **Quality focus** | the organisational commitment to continuous improvement | there is no reason for any of the above to exist |

**The five framework activities:**

| Activity | What happens |
|---|---|
| Communication | talk to the customer; gather requirements |
| Planning | define the work — tasks, risks, resources, schedule |
| Modeling | build the analysis and design models |
| Construction | code it and test it |
| Deployment | deliver, get feedback, support |

**Umbrella activities** run *across* all five, throughout the project — not a
phase: project tracking and control · risk management · quality assurance ·
technical reviews · measurement · configuration management · reusability
management · work product preparation and production.

**Two distinctions that get confused:**

| | Process framework | Process model |
|---|---|---|
| What it is | the set of activities every project performs | a specific arrangement of those activities |
| Example | communication, planning, modeling, construction, deployment | waterfall, spiral, incremental |
| Varies by project? | no | yes — this is the choice you make |

| | Framework activity | Umbrella activity |
|---|---|---|
| When | happens in sequence, as a phase | runs continuously, across all phases |
| Example | modeling | risk management |

**Software products:**

| Product type | Built for | Requirements come from |
|---|---|---|
| Generic | the open market, sold to many customers | the developing organisation |
| Customised (bespoke) | one specific customer | that customer |

**Not repeated here:** software = program + documentation + operating procedures,
the five characteristics, the eight application domains — all on
[[Introduction to Software Engineering]]. The handout assigns them to lecture 5;
the deck teaches them alongside lecture 1-3 material, so rule 8 keeps them there.

## How it's asked

**Never asked, on the one paper in this vault** — `asked_as` is empty. Rule 7
requires saying that plainly rather than inventing drill.

**If it appears, the two likely shapes** (prediction, not evidence):
- **`compare`** — *framework activity vs umbrella activity*, or *process framework
  vs process model*. Both pairs are in Quick Reference; answer as a table with the
  dimension named in every row. See [[answer-patterns]] §5.
- **`explain`** — "explain software engineering as a layered technology", 2 marks.
  Four names bottom-up, one line each, **and draw the stack** — it costs ten
  seconds and makes the ordering unambiguous.

**The single most likely thing to be tested** is the *direction* of the stack:
quality focus at the bottom, tools at the top.

## Contents

| # | Section | Type | Archetype | Marks | Why it's here |
|---|---|---|---|---|---|
| 1 | Software engineering as a layered technology | definitional | — | 0 | the four-layer stack — **no deck** |
| 2 | The generic process framework | procedural | — | 0 | the five activities every model rearranges — **no deck** |
| 3 | Umbrella activities | definitional | — | 0 | what runs across all phases — **no deck** |
| 4 | The process, and software products | definitional | — | 0 | generic vs customised; points back to topic 1 |

**The thread:** "process" is one of the four layers, so what is in it? (1→2) —
five activities in sequence, but some work never stops (2→3) — and that machinery
exists to produce something (3→4), whose nature decides which model is viable.

## 1 · Software engineering as a layered technology

- **The argument:** organisations buy tools and expect to become good at
  software. Tools sit at the *top* of a stack — under them the **methods** that
  say what to do, under that the **process** that decides when and in what order,
  and at the bottom a **quality focus** giving all of it a reason to exist.
- **Remove a lower layer and everything above has nothing to stand on.** A team
  with tools but no process just makes mistakes faster.
- Four layers and their failure modes: Quick Reference. **Direction is the
  content** — quality focus at the bottom, tools at the top.
- **Never examined.** If it appears, most likely a 2-mark Section A "explain SE
  as a layered technology" — four names bottom-up, one line each, and **draw the
  stack**; it costs ten seconds and makes the ordering unambiguous.

## 2 · The generic process framework

- **The argument:** strip any process model down and the same five things happen
  — someone talks to the customer, plans, models, builds, ships. **Waterfall does
  each once, in order. Spiral does all five per loop. Agile does all five per
  sprint.**
- **What differs between models is the arrangement, never the ingredients** —
  which is exactly why the comparison table on [[Evolutionary Process Models]] is
  possible at all.
- **Framework vs model** is the precise part: the framework is fixed and
  universal, the model is the choice you make. Both tables: Quick Reference.
- **Never examined.** Know the five names in order — they are the vocabulary of
  every process-model answer, and using them makes those answers noticeably more
  precise.

## 3 · Umbrella activities

- **The argument:** you cannot schedule risk management as week six, or do
  configuration management on Tuesday and then stop. Some work runs continuously,
  because the moment it stops the project degrades without anyone noticing.
- Drawn as a **band across the whole timeline**, not a box within it. All eight:
  Quick Reference.
- **The examinable point is the contrast**, not the list: framework activities
  are phases, umbrella activities are continuous.
- Two get whole topics later — risk on [[Risk Analysis & Estimation]], QA and
  technical reviews on [[Software Quality Assurance]].
- **Never examined.** If asked, the distinction earns the marks; reciting all
  eight without it does not.

## 4 · The process, and software products

- **A process** is a set of activities with an order and deliverables — what turns
  "we built something" into "we can build another one the same way".
- **What you build shapes it:** a product sold to thousands has no single customer
  to consult, so the developing organisation invents the requirements itself. A
  bespoke system has exactly one customer, the sole authority. That difference
  propagates into which process model is even viable. Split: Quick Reference.
- **Handout vs deck:** the handout assigns *software products, characteristics and
  applications* to lecture 5; the deck teaches all three in its opening run. Rule
  8 — the deck sets teaching structure — so they live on
  [[Introduction to Software Engineering]]. Revise them there.
- **Never examined.**

## Question Bank

- **PYQ — none.** No question on [[se-ete-2025-26]] tests this topic.
- **Deck — none**, because no deck covers the topic.
- **Textbook — unavailable.** Pressman 8e is prescribed by
  [[se-handout-2026-muj]] and is not in `raw/sources/`.
- **No questions in any of the three tiers.** Stated rather than filled with
  invented drill. If the lecture 4-5 slides or the textbook land, this section is
  the first thing to rebuild.

## Mistakes & Traps

- **Drawing the layer stack upside down.** Quality focus is the *bottom*. Tools at
  the base inverts the argument the diagram exists to make.
- **Confusing framework with umbrella activities.** Phases versus continuous —
  the distinction any question here would target.
- **Confusing the process framework with a process model.** The framework is what
  every project does; the model is how one project arranges it.
- **Listing the five framework activities out of order.** Communication →
  planning → modeling → construction → deployment. The order is the content.

## Course Material

**No deck covers this topic.** Confirmed by keyword sweep of all 24 files in
`raw/sources/ppts/`:

| Handout content | Lecture | Hits across all decks |
|---|---|---|
| Layered approach | 4 | **0** for "layered" |
| Generic approach | 4 | **0** for "generic process" |
| Process framework | 4 | **0** as lecture content |
| Umbrella activities | 4 | **0** for "umbrella" |
| The process, software products | 5 | partial — taught on the earlier page |
| Software characteristics, applications | 5 | covered, on [[Introduction to Software Engineering]] |

- Rule 5 governs: the handout names this material three separate times, so it is
  in scope regardless of the decks' silence.
- Rule 6's fallback is unavailable — Pressman 8e is not in the vault.
- **Highest-value fix available to this vault:** the lecture 4-5 slides, or
  Pressman 8e chapters 1-2.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] ·
previous [[Introduction to Software Engineering]] · next
[[Conventional Process Models]]
