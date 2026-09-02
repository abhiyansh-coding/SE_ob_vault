---
phase: Testing
topic: Cyclomatic Complexity & Graph Matrices
lectures: 39-40
co: CSE3102.4
asked_as: [draw, numerical]
mte: false
studied: false
status: not-started
pyq_marks: 6
assignment_qs: 0
attempts: 0
last_practiced: null
---

# Cyclomatic Complexity & Graph Matrices

**Prerequisites:** [[White-Box Testing]]

> [!warning] Page not built
> Scaffolded on 2026-09-02 from the handout's lecture plan. No subtopics, Quick
> Reference or Question Bank yet — those come from reading the decks below
> (rule 8). Out of MTE scope; End Term only.

## Overview

> [!info] 6 of 80 in [[se-ete-2025-26]] — question C1 (part)
> The vault's **only** paper, so this is the whole of rule 2's evidence:
> one sitting, not a trend. See [[weightage]] for what that can and
> cannot tell you. Lectures 39-40 is *syllabus depth* and rule 3 forbids
> reading it as marks.

Drawing the control flow graph and computing V(G) three ways, then the graph matrix as its tabular form. A guaranteed numerical wherever testing is examined.

## How it's asked

**6 of 80 — C1(a) and C1(b), the drawing half of the basis-path question.** The
path-enumeration half (4 marks) is on [[White-Box Testing]].

### Draw & label — C1(a), 3 marks

- **Spot it:** a short program listed with line numbers, "draw the control flow
  graph".
- **Skeleton:** legend (node = statement or block, edge = flow of control, predicate
  node = a decision) → the graph with **nodes numbered to match the line numbers**
  → the reading: node count *N*, edge count *E*, predicate count *P*.
- **Earns the marks:** numbering nodes to the source lines, so part (b) is
  checkable against the drawing.

### Numerical — C1(b), 3 marks

- **Skeleton:** compute **all three ways and show they agree** —
  *V(G)* = *E* − *N* + 2 · *V(G)* = *P* + 1 · *V(G)* = number of regions.
  Agreement across three formulas is a built-in sanity check and reads as mastery.
- **Trap:** miscounting edges. Recount against the drawing before finalising.

See [[answer-patterns]] §3 and §4.

## Course Material

- `raw/sources/ppts/2025/L11 Software Testing_5.pdf`
- `raw/sources/ppts/2025/Estimation of Test Coverage Metrics and Structural Complexity.docx`
