---
phase: Testing
topic: White-Box Testing
lectures: 38, 41
co: CSE3102.4
asked_as: [draw, numerical]
mte: false
studied: false
status: not-started
pyq_marks: 4
assignment_qs: 0
attempts: 0
last_practiced: null
---

# White-Box Testing

- Structural testing: basis path testing and data flow testing, driven by the code's own control structure.

**Prerequisites:** [[Testing Fundamentals]]
**Asked as:** draw, numerical — **4 of 80** in [[se-ete-2025-26]]

> [!warning] Page not built
> Scaffolded on 2026-09-02 from the handout's lecture plan. No subtopics, Quick
> Reference or Question Bank yet — those come from reading the decks below
> (rule 8). Out of MTE scope; End Term only.

> [!info] What it asked — question C1 (part)
> The vault's **only** paper, so this is the whole of rule 2's evidence:
> one sitting, not a trend. See [[weightage]] for what that can and
> cannot tell you. Lectures 38, 41 is *syllabus depth* and rule 3 forbids
> reading it as marks.

## How it's asked

**4 of 80 — C1(c), the path-enumeration half.** The CFG and V(G) parts (6 marks)
are on [[Cyclomatic Complexity & Graph Matrices]].

### Derive & enumerate — C1(c), 4 marks

- **Spot it:** *"list all independent paths"*, following a CFG and a computed
  V(G).
- **Skeleton:** state that **the number of independent paths equals V(G)** →
  list exactly that many, each as a node sequence (1-2-4-7…) → confirm each new
  path introduces **at least one edge not on any previous path**.
- **Earns the marks:** the count matching V(G), and every path written as an
  explicit node sequence.
- **Trap:** listing more paths than V(G) (you have listed dependent ones) or
  fewer (you have missed a branch).

See [[answer-patterns]] §3.

## Sources

- `raw/sources/ppts/2025/L11 Software Testing_5.pdf`
