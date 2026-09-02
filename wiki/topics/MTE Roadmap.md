---
type: plan
scope: Mid-Term Examination, lectures 1-32
max_marks: 30
---

# MTE Roadmap

The queue for the **30-mark Mid-Term**, close book, covering **lectures 1-32**
per the override recorded on [[syllabus]] — not the handout's 1-34.

> [!tip] Next up
> **Session 1, step 2 — [[Software Engineering as a Layered Technology]].**
> Step 1 is built. Move this callout as each step completes.

## What the Mid-Term covers

**18 of the vault's 30 topics. CO1 and CO2 only** — the override moves lectures
33-34 out, and those were the only CO3 lectures in the window, so CO3 is
entirely absent from this exam.

> [!warning] The format is unknown, the content is not
> The handout sets the MTE at 30 marks and says nothing about its sections. No
> past MTE paper exists in this vault. What follows is ordered by evidence from
> [[se-ete-2025-26]] — a **End Term** paper — of which **46 of 80 marks fall
> inside this window**. That is a strong content signal and no format signal at
> all.

## Triage — if time is short

Ordered by marks earned in the one paper we have. These eight topics took **46
of its 80 marks**; the other ten in-window topics took none.

| Topic | Marks | The form it took |
|---|---|---|
| [[Effort Estimation & COCOMO]] | 10 | 10-mark Section D numerical |
| [[UML & Use Case Modeling]] | 10 | 10-mark **drawing** — activity diagram from a described workflow |
| [[SDLC & CMMI]] | 8 | CMMI-level scenario (2) + effort distribution essay (6) |
| [[Coupling & Cohesion]] | 6 | definition (3) + read a code snippet and name the types (3) |
| [[Evolutionary Process Models]] | 4 | scenario → name the model, with justification |
| [[Conventional Process Models]] | 2 | same question, waterfall case |
| [[Requirements Engineering]] | 2 | why SRS survives waterfall but not Agile |
| [[Risk Analysis & Estimation]] | 2 | identification vs assessment |

**Two of those are the whole game if you have one evening:** COCOMO, because it
is the only numerical on the paper and numericals are all-or-nothing; and UML,
because a 10-mark drawing is the largest single block in the window.

## The plan — 8 sessions, ~22 hours

Lecture order, which is also dependency order: every page's Prerequisites are
satisfied by the pages above it. Hours are sized by **marks first, then by how
much method the topic carries** — a zero-mark topic with three lectures of
notation (DFD) costs more than a two-mark topic with one definition (Risk).

> [!note] The MTE date is not recorded in this vault
> The handout gives no exam date. 22 hours is the content; how it spreads is
> yours to set. If it turns out to be tight, the triage block above is the
> order to cut in — sessions 4 and 6 are the two that must survive.

| Session | Steps | Topics | Hours | Marks |
|---|---|---|---|---|
| 1 | 1-4 | Foundations, then conventional and evolutionary models | 3.25 | 8 |
| 2 | 5-6 | Agile, then SDLC & CMMI | 3.0 | 8 |
| 3 | 7-9 | Requirements, practice, size estimation | 3.0 | 2 |
| 4 | 10-11 | **COCOMO**, then risk | 3.25 | 12 |
| 5 | 12-13 | ERD, then DFD | 2.5 | 0 |
| 6 | 14 | **UML & use cases** | 2.5 | 10 |
| 7 | 15-16 | Design concepts, then coupling & cohesion | 2.5 | 6 |
| 8 | 17-18 | Architecture, then transform mapping | 2.25 | 0 |
| | | **Total** | **22.25** | **46** |

**Sessions 4 and 6 are 22 of the 46 in-window marks in 5.75 hours.** If the
schedule collapses, they are what survives.

## The build queue

Marks are from [[se-ete-2025-26]].

| # | Ses | Topic | Lec | Marks | Hrs | Built | Note |
|---|---|---|---|---|---|---|---|
| 1 | 1 | [[Introduction to Software Engineering]] | 1-3 | **2** | 0.75 | **yes** | myths and the deterioration curve |
| 2 | 1 | [[Software Engineering as a Layered Technology]] | 4-5 | 0 | 0.5 | no | short |
| 3 | 1 | [[Conventional Process Models]] | 6-7 | 2 | 1.0 | no | |
| 4 | 1 | [[Evolutionary Process Models]] | 8 | 4 | 1.0 | no | the comparison table is the payload |
| 5 | 2 | [[Agile Development]] | 9-11 | 0 | 1.5 | no | deck carries a **velocity/cost numerical** |
| 6 | 2 | [[SDLC & CMMI]] | 12 | 8 | 1.5 | no | |
| 7 | 3 | [[Requirements Engineering]] | 13 | 2 | 1.0 | no | |
| 8 | 3 | [[Software Engineering Practice]] | 14 | 0 | 0.5 | no | |
| 9 | 3 | [[Software Size Estimation]] | 15-16 | 0 | 1.5 | no | numerical; **prerequisite for step 10** |
| 10 | 4 | [[Effort Estimation & COCOMO]] | 17 | 10 | 2.5 | no | heaviest topic in the window |
| 11 | 4 | [[Risk Analysis & Estimation]] | 18 | 2 | 0.75 | no | |
| 12 | 5 | [[Data Modeling & ERD]] | 19-20 | 0 | 1.0 | no | drawing |
| 13 | 5 | [[Flow-Oriented Modeling & DFD]] | 19, 21 | 0 | 1.5 | no | drawing; **prerequisite for step 18** |
| 14 | 6 | [[UML & Use Case Modeling]] | 22-23 | 10 | 2.5 | no | drawing; only topic with a 2026-27 deck |
| 15 | 7 | [[Design Concepts & Principles]] | 24-26 | 0 | 1.0 | no | |
| 16 | 7 | [[Coupling & Cohesion]] | 28 | 6 | 1.5 | no | |
| 17 | 8 | [[Software Architecture]] | 27, 29-30 | 0 | 1.0 | no | |
| 18 | 8 | [[Transform & Transaction Mapping]] | 31-32 | 0 | 1.25 | no | drawing; needs step 13 |

Flip **Built** to `yes` as each page is finished.

Cumulative: **28 of the 46 in-window marks are covered by step 10**, and 44 of
46 by step 16.

## Rule 1 vs rule 2, stated plainly

Ten of the eighteen in-window topics scored **zero** on the one paper — including
all of [[Flow-Oriented Modeling & DFD]], [[Data Modeling & ERD]],
[[Software Architecture]] and the whole of Foundations. Rule 7 requires saying
this out loud rather than picking a side:

- **Rule 1 says they are in.** They are in the syllabus and taught across
  lectures 1-32. A 30-mark paper drawn from 32 lectures cannot avoid them all.
- **Rule 2 says they earned nothing.** On one sitting. Which is nearly no
  evidence — with a single paper, "0 marks" and "not asked that day" are the
  same observation.
- **DFD deserves specific suspicion.** It has a dedicated deck, a dedicated
  question sheet (`Flowdiagram Ques.pdf`), and two full lectures — and it scored
  zero on an End Term whose drawing question went to UML instead. A Mid-Term
  that must fit 32 lectures into 30 marks is exactly where a DFD question fits.

**Do not skip a zero-mark topic on this evidence.** Study them second, not never.
