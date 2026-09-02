---
phase: Testing
topic: Black-Box Testing
lectures: 36-37
co: CSE3102.4
asked_as: [numerical, explain]
mte: false
studied: false
status: not-started
pyq_marks: 10
assignment_qs: 0
attempts: 0
last_practiced: null
---

# Black-Box Testing

**Prerequisites:** [[Testing Fundamentals]]

> [!warning] Page not built
> Scaffolded on 2026-09-02 from the handout's lecture plan. No subtopics, Quick
> Reference or Question Bank yet — those come from reading the decks below
> (rule 8). Out of MTE scope; End Term only.

## Overview

> [!info] 10 of 80 in [[se-ete-2025-26]] — question C2
> The vault's **only** paper, so this is the whole of rule 2's evidence:
> one sitting, not a trend. See [[weightage]] for what that can and
> cannot tell you. Lectures 36-37 is *syllabus depth* and rule 3 forbids
> reading it as marks.

Functional testing without seeing the code: boundary value analysis, equivalence class partitioning and decision-table-based testing.

## How it's asked

**10 of 80 — the largest testing block, and the heaviest non-MTE topic.** C2 mixes
two archetypes.

### Numerical / derive — C2(a), 6 marks

- **Spot it:** a range with inclusive bounds — *"valid age 18–60 inclusive"* — and
  "design the BVA test cases".
- **Skeleton:** state the technique's rule (**min−1, min, min+1, nominal, max−1,
  max, max+1**) → tabulate the cases with expected result for each → count them.
- **Earns the marks:** the table with *expected outcome* per case, and including
  the **invalid** boundaries (17 and 61). Candidates who list only valid values
  lose half.
- **Trap:** off-by-one on an *inclusive* bound.

### Explain — C2(b) and C2(c), 2 marks each

- *"How BVA catches boundary defects"* → because **defects cluster at boundaries**,
  where relational operators are written wrong (`<` for `<=`).
- *"How BVA handles multiple input variables"* → hold all but one at nominal and
  vary that one through its boundaries; for *n* variables this gives **4n + 1**
  test cases (or 6n + 1 with robustness).

See [[answer-patterns]] §2 and §3.

## Course Material

- `raw/sources/ppts/2025/L11 Software Testing_5.pdf`
