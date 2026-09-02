# Weightage

**Derived from [[se-ete-2025-26]] and from nothing else.** Slide counts, chapter
lengths and the number of practice questions in the course material carry no
weight here — see rule 3 in `CLAUDE.md`.

Corpus: **1 paper × 80 marks = 80 marks.** Every mark is assigned to exactly one
topic and the paper reconciles at 80/80. Questions straddling two topics are
split and the split is noted on both pages and on the paper page.

> [!warning] One paper is not a corpus — read every number below twice
> The CN vault runs on four papers and 320 marks, and even there 2-mark
> differences are noise. This vault has **one sitting**. A topic showing 0 here
> was not asked **once**; that is absence of evidence, not evidence of absence.
> A topic showing 12 was heavy **on one day**. Nothing below is a trend, and
> nothing below justifies skipping a syllabus topic (rule 1 still governs
> scope). Treat it as the single best guess available, not as a distribution.
>
> The one thing that *is* solid: the paper's **course code is CSE3102/CS3201**,
> the same code as this year's handout. There is no syllabus drift to discount
> (rule 4), so what it asked is what this course asks.

## By phase

| Phase | Lectures | Marks (of 80) | Share | In MTE window? |
|---|---|---|---|---|
| Testing | 35-43 | 20 | 25.0% | no |
| Process Models | 6-12 | 14 | 17.5% | **yes** |
| Project Planning | 15-18 | 14 | 17.5% | **yes** |
| Analysis Modeling | 19-23 | 10 | 12.5% | **yes** |
| Quality & Maintenance | 44, 46-50 | 8 | 10.0% | no |
| Design | 24-32 | 6 | 7.5% | **yes** |
| DevOps | 51-53 | 6 | 7.5% | no |
| Requirements | 13-14 | 2 | 2.5% | **yes** |
| Foundations | 1-5 | 0 | 0% | **yes** |
| Construction | 33-34 | 0 | 0% | no |
| **Total** | | **80** | **100%** | |

## By topic

| Topic | Phase | Marks | Question | MTE |
|---|---|---|---|---|
| [[Effort Estimation & COCOMO]] | Project Planning | 12 | A5, D1 | **yes** |
| [[Black-Box Testing]] | Testing | 10 | C2 | no |
| [[UML & Use Case Modeling]] | Analysis Modeling | 10 | D2 | **yes** |
| [[SDLC & CMMI]] | Process Models | 8 | A2, B3 | **yes** |
| [[Coupling & Cohesion]] | Design | 6 | B2 | **yes** |
| [[Cyclomatic Complexity & Graph Matrices]] | Testing | 6 | C1 (part) | no |
| [[DevOps, Cloud & Virtualization]] | DevOps | 6 | B5 | no |
| [[Evolutionary Process Models]] | Process Models | 4 | B1 (part) | **yes** |
| [[White-Box Testing]] | Testing | 4 | C1 (part) | no |
| [[Software Quality Assurance]] | Quality & Maintenance | 3 | B4 (part) | no |
| [[Software Reliability & ISO Standards]] | Quality & Maintenance | 3 | B4 (part) | no |
| [[Conventional Process Models]] | Process Models | 2 | B1 (part) | **yes** |
| [[Requirements Engineering]] | Requirements | 2 | A3 | **yes** |
| [[Risk Analysis & Estimation]] | Project Planning | 2 | A4 | **yes** |
| [[Re-engineering & Reverse Engineering]] | Quality & Maintenance | 2 | A1 | no |
| [[Introduction to Software Engineering]] | Foundations | 0 | — | **yes** |
| [[Software Engineering as a Layered Technology]] | Foundations | 0 | — | **yes** |
| [[Agile Development]] | Process Models | 0 | — | **yes** |
| [[Software Engineering Practice]] | Requirements | 0 | — | **yes** |
| [[Software Size Estimation]] | Project Planning | 0 | — | **yes** |
| [[Data Modeling & ERD]] | Analysis Modeling | 0 | — | **yes** |
| [[Flow-Oriented Modeling & DFD]] | Analysis Modeling | 0 | — | **yes** |
| [[Design Concepts & Principles]] | Design | 0 | — | **yes** |
| [[Software Architecture]] | Design | 0 | — | **yes** |
| [[Transform & Transaction Mapping]] | Design | 0 | — | **yes** |
| [[Coding Standards & Practices]] | Construction | 0 | — | no |
| [[Testing Fundamentals]] | Testing | 0 | — | no |
| [[Levels of Testing & Tools]] | Testing | 0 | — | no |
| [[Debugging]] | Testing | 0 | — | no |
| [[Software Maintenance]] | Quality & Maintenance | 0 | — | no |

## What this says about the Mid-Term

**46 of the 80 marks on this paper fall inside the MTE window** (lectures 1-32,
per the override on [[syllabus]]) — 57.5% of an End Term paper sits in material
the Mid-Term also covers. Ranked, the in-window topics that earned marks:

| Rank | Topic | Marks | Form it took |
|---|---|---|---|
| 1 | [[Effort Estimation & COCOMO]] | 12 | a 10-mark Section D numerical + a 2-mark Brooks's-Law justification |
| 2 | [[UML & Use Case Modeling]] | 10 | a 10-mark Section D **drawing** (activity diagram from a described workflow) |
| 3 | [[SDLC & CMMI]] | 8 | a 2-mark CMMI-level scenario + a 6-mark effort-distribution essay |
| 4 | [[Coupling & Cohesion]] | 6 | 3 marks definition + 3 marks reading a code snippet |
| 5 | [[Evolutionary Process Models]] | 4 | two of three scenario-matching cases |
| 6= | [[Conventional Process Models]] | 2 | one scenario-matching case |
| 6= | [[Requirements Engineering]] | 2 | why SRS survives in waterfall but not Agile |
| 6= | [[Risk Analysis & Estimation]] | 2 | identification vs assessment |

> [!warning] The MTE structure is unknown
> The handout sets the Mid-Term at **30 marks, close book** and says nothing
> about its section split. This vault has no past MTE paper. Until one arrives,
> any mock built here is guessing at the shape — the *content* ranking above is
> evidence-based, the *format* is not.

## What the paper's form says

Worth more than the topic ranking, because form is stable even when topics move:

- **Nothing is recall.** There is no "define X" question on the entire paper.
  Five of fifteen open on a scenario and ask for a judgment with justification —
  "identify the CMMI maturity level and justify", "identify the software process
  model and provide a brief justification", "select the re-engineering approach
  and explain the reason".
- **Drawings are 20 of 80 marks** — a control flow graph (C1) and an activity
  diagram (D2), both in the long sections. In the MTE window this matters
  doubly, because the drawing question that landed there was UML.
- **Numericals are 10 of 80** and all of them are COCOMO (D1). Nothing else on
  the paper computes anything.
- **Section A rewards precision, not breadth**: each 2-marker is a one-idea
  distinction (risk identification vs assessment; SRS in Agile vs waterfall;
  Brooks's Law).

## Caveats

- **One paper.** Everything above rests on a single sitting. Two more papers
  would change this table more than any amount of reasoning about it.
- The paper is out of **80**; the handout weights the End Term at **40 of 100**,
  so marks here are scaled at grading time. The 80 is the paper's own scale.
- The paper's printed COs agree with the natural topic classification almost
  everywhere — unusual, and better than the CN corpus managed. The single
  disagreement is B3 and it is recorded on [[se-ete-2025-26]].
- No solution key was supplied with the paper. Nothing here is checked against
  a printed answer, so no `✓` marks exist in this vault yet.
