---
phase: Foundations
topic: Introduction to Software Engineering
lectures: 1-3
co: CSE3102.1
asked_as: [scenario]
mte: true
studied: false
status: not-started
pyq_marks: 2
assignment_qs: 0
attempts: 0
last_practiced: null
---

# Introduction to Software Engineering

- **The course justifies its own existence here:** what software is · what went
  wrong when industry treated it like manufacturing · which beliefs still make
  projects fail.
- Everything in [[story]] hangs off this page.

**Prerequisites:** none — this is the entry point of the course.
**Asked as:** scenario — **2 of 80** in [[se-ete-2025-26]]

> [!info] What it asked — question A5
> A5 asks whether a late project can be rescued by adding people. The deck plants
> that answer in its **software crisis** slide, and the paper tags it **CO1**
> (lectures 1-12) — so it is examined here, not on [[Effort Estimation & COCOMO]]
> where the person-month arithmetic lives. One paper only; see [[weightage]].

> [!warning] Two subtopics have no source in this vault
> **Legacy software** and **software myths** are named in the handout (lecture 3)
> and appear in **no deck** — zero hits for "myth" across all 24 decks, no
> lecture-3 treatment of "legacy". Pressman 8e is not in `raw/sources/`, so rule
> 6's fallback is unavailable. Subtopics 6-7 are standard Pressman material,
> **labelled unsourced** — indicative, not your instructor's wording.

## 1 · What software engineering is

| Term | It means |
|---|---|
| Program | executable code alone |
| Software | program **+** documentation **+** operating procedures |
| Software crisis | the late-1960s realisation that software development does not behave like manufacturing |
| Legacy software | older systems still in service, business-critical, poorly documented, expensive to change |

- **The gap it fills:** CS says what a machine *can compute*; it does not say how
  five people build a payroll system in nine months for a customer who keeps
  changing their mind.

**Definition.** Software engineering is an engineering discipline concerned with
all aspects of software production — aiming at **fault-free software, meeting
user needs, on time and within budget**. The deck's fuller phrasing adds: *adopt
a systematic and organised approach, using appropriate tools and techniques
depending on the problem, the development constraints and the resources
available.*

| | Computer science | Software engineering |
|---|---|---|
| Supplies | theories, computer function and methods | tools and techniques to solve the problem |
| Faces | the machine | the customer and their problem |

- **Never examined.** Know it well enough to open a longer answer with it.

## 2 · The software crisis

- By the late 1960s: **software behaves like nothing else engineers build**.
- Projects ran late, and the obvious fix — more programmers — made them *later*.
- Hardware got cheaper as software got bigger and costlier, so the thing **least
  under control became the thing that mattered most**.
- It is the **problem statement the remaining 50 lectures answer**.

**The six causes**, in the deck's order: lack of communication between developer
and user · cost of software rising relative to hardware · growth in software size
· project management problems · inadequate training in software engineering ·
skill shortage.

**The three canonical failures** — one per cause, worth naming precisely:

| Failure | Year | Cause |
|---|---|---|
| Ariane 5 | 1996 | destroyed 39 s after launch; 10 years and $7 bn of development, four satellites lost |
| Patriot missile | 1991 | clock timing error accumulating over 100 h of operation; 28 US soldiers killed at Dhahran |
| Y2K | 2000 | two-digit year fields — an assumption, not a coding bug |

- **The deck's wording:** adding programmers late "does not always help speed up
  the development process. Instead, sometimes it may have negative impacts like
  delay in achieving the scheduled targets, degradation of software quality."
- **Three mechanisms:**
  1. **Training cost** — newcomers are brought up to speed by the people who are
     already the bottleneck, so throughput drops before it rises.
  2. **Communication overhead** — *n* people have *n(n−1)/2* pairwise channels;
     doubling a team roughly quadruples coordination cost.
  3. **Partitioning limits** — some tasks cannot be subdivided. The formal version
     is on [[Effort Estimation & COCOMO]], where effort in person-months and
     duration in months are shown not to be interchangeable.

**Worked example.**

> **[[se-ete-2025-26]] Q A5 (2 marks, CO1)** — "A software development process is
> delayed from its scheduled time. Is it possible to develop the software on time
> by adding more employees? Justify your answer."

**Answer: no.** Any two of the three mechanisms earn the marks — training diverts
the staff you can least spare · communication paths grow as *n(n−1)/2* against
at-best-linear output · sequential work cannot be compressed by parallelism.
**Close with the real remedies:** reduce scope · extend the schedule · re-plan
with the time remaining. *(No solution key for this paper — unchecked, no `✓`.)*

## 3 · Program vs software

- **Students arrive believing they have written software. They have written
  programs.** The difference shows the moment somebody *else* must run,
  understand or change the thing.
- **No documentation → nobody can modify it safely. No operating procedures →
  nobody can install or administer it.** Both are deliverables, so a "finished"
  program is roughly a **third** of a finished product.

> **Software = Program + Documentation + Operating Procedures**

**Documentation, by phase** — the deck's own table:

| Phase | Documents |
|---|---|
| Analysis / specification | formal specification, context diagram, DFDs |
| Design | flow charts, ER diagram |
| Implementation | source code listings, cross-reference listing |
| Testing | test data, test results |

**Operating procedures** are two manual families:
- **User manuals** — system overview, beginner's guide, tutorial, reference guide.
- **Operational manuals** — installation guide, system administration guide.

| Term | It means |
|---|---|
| Program | executable code alone |
| Software | program **+** documentation **+** operating procedures |

- **Never examined**, but exactly the one-line definition Section A likes.

## 4 · Software characteristics and the deterioration curve

- **A bridge fails because steel fatigues.** Software has no steel, so ideally
  its failure rate falls as early defects are found, then stays flat forever.
- **It does not.** Every post-release change fixes one thing and disturbs
  another, so the curve jumps at each release and settles *higher*.
- **Software does not wear out — it deteriorates** — and the agent is change
  itself.

**The two failure curves.** Be able to draw both, labelled:

| | Hardware | Software |
|---|---|---|
| Curve shape | bathtub: burn-in, useful life, wear-out | falling, then a ratchet upward at each change |
| Failure cause | physical decay — dust, vibration, temperature | change: each fix introduces new faults |
| End of life | wears out | retired for environmental change, new requirements, new expectations |

**The five characteristics:** does not wear out · developed or engineered, **not
manufactured** in the classical sense · components are reusable · highly flexible
· a **logical** rather than physical system element.

- **The pairing that matters:** *engineered, not manufactured* means the cost sits
  in **development**, not reproduction. Copying is free — which is why every cost
  is a design cost.
- **Never examined, but draw both curves.** Cheap insurance in any maintenance or
  quality answer — this course puts 20 of 80 marks on drawings.

## 5 · The changing nature of software

- **Software never wears out and can be reshaped endlessly**, so it spread into
  every domain that would have it — firmware in a washing machine to a
  recommendation engine.
- **That spread is what makes a single universal process impossible**, which is
  the argument [[Conventional Process Models]] picks up.

**The eight application domains:** system · real-time · embedded · engineering
and scientific · business · web-based · personal computer · artificial
intelligence.

- **Never examined.** A listing answer — name the eight, one example each if
  pushed, stop.

## 6 · Legacy software

> [!warning] Unsourced — no deck covers this
> The handout names it in lecture 3; no deck treats it (the two hits for "legacy"
> are incidental, in the DevOps and re-engineering decks), and Pressman 8e is not
> in this vault. Standard textbook material, not your instructor's slides.

- **Definition.** An older system still in service, typically: poor quality from
  years of unstructured patching · absent or outdated documentation · brittle
  design · obsolete hardware, languages or platforms · and, despite all of it,
  **business criticality**.
- **The four responses, in increasing cost:** leave it alone if stable and
  isolated · re-engineer for maintainability · adapt it to interoperate · replace
  it. The machinery is on [[Re-engineering & Reverse Engineering]].
- **Why it is a category, not just old code:** it cannot be switched off (the
  business depends on it) and cannot easily be changed (nobody fully understands
  it; documentation is wrong or missing). Business-critical *and* unmaintainable.
- **Typical symptoms:** poor quality from years of unstructured patching · absent
  or outdated documentation · brittle design · obsolete hardware, languages or
  platforms.
- **Never examined *here*.** [[se-ete-2025-26]] Q A1 is a legacy scenario — a
  15-year-old COBOL system with outdated documentation — but asked as
  re-engineering, so its 2 marks sit on [[Re-engineering & Reverse Engineering]].
  Definition here; method there.

## 7 · Software myths

> [!warning] Unsourced — no deck covers this
> Zero hits for "myth" across all 24 decks. The handout names software myths in
> lecture 3 and the syllabus paragraph names them again — a rule-5 gap: absence
> from the decks is not evidence the topic is out of scope. Standard Pressman.

| Myth | Held by | The reality |
|---|---|---|
| "A book of standards exists, so my people have all they need" | management | it may be unread, out of date, or quietly ignored |
| "We can add programmers to catch up" | management | adding people to a late project makes it later — section 2 |
| "Outsourcing lets me relax" | management | outsourced projects fail for the same reasons in-house ones do |
| "A general statement of objectives is enough to start" | customer | ambiguous requirements are the largest single cause of failure |
| "Requirements change is easy to absorb — software is flexible" | customer | the cost of change rises steeply the later it lands |
| "Once the program works, we're done" | practitioner | 60%+ of total effort is spent *after* first delivery |
| "Until the program runs, quality can't be assessed" | practitioner | reviews and inspections find defects earlier and cheaper |
| "The only deliverable is the working program" | practitioner | software = program + documentation + operating procedures |
- **Never examined.** Know two or three per category. The management myth about
  adding programmers deserves extra attention — same content as A5, so it is the
  one already proven examinable.

## How it's asked

Generic skeleton on [[answer-patterns]] §1. **2 of 80, all of it in one 2-marker.**

### Scenario → identify & justify — A5, 2 marks

- **Spot it:** a project behind schedule, asking whether adding people can rescue
  it. Any phrasing of "add more developers / employees / programmers".
- **Skeleton:** answer **no in the first line** → give two of the three mechanisms
  (training diverts your best people · communication paths grow as *n(n−1)/2*
  against at-best-linear output · sequential work cannot be parallelised) → close
  by naming the real remedies: reduce scope, extend the schedule, re-plan.
- **Earns the marks:** the mechanism. A 2-marker wants the *reason*.
- **Trap:** "yes, if they are added early" — the question says the project is
  *already* late. Second trap: naming Brooks's Law and stopping. **The eponym
  earns nothing on its own.**

**Never asked as:** `numerical`, `draw`, `compare`, `explain`. The six crisis
causes and three named failures are plausible Section A material and have not been
asked — a prediction, not evidence (rule 7).

## Quick Reference

> [!abstract] The ten-minute recall card
> Everything here is taught in full above. This is the compressed form.

**The three facts that carry the topic**
- **Software = Program + Documentation + Operating Procedures.** A program is one
  third of a software product.
- **Hardware wears out; software deteriorates.** The curve ratchets up at every
  maintenance release and never returns to its baseline.
- **Adding people to a late project makes it later.** The whole of A5.

**Definition, one line:** an engineering discipline covering all aspects of
software production — fault-free, meeting user needs, on time, within budget.

| Ask | Answer |
|---|---|
| Six crisis causes | communication · cost vs hardware · size · project management · training · skill shortage |
| Three failures | Ariane 5 (1996) · Patriot (1991) · Y2K (2000) |
| Five characteristics | doesn't wear out · engineered not manufactured · reusable · flexible · logical |
| Eight domains | system · real-time · embedded · engineering/scientific · business · web · PC · AI |
| Four maintenance types | corrective · adaptive · perfective · preventive |
| Four legacy responses | leave · re-engineer · adapt · replace |
| Myth categories | management · customer · practitioner |

**The four maintenance types** — introduced here, examined on
[[Software Maintenance]]:

| Type | Purpose |
|---|---|
| Corrective | fix defects missed during development |
| Adaptive | port to a new platform or environment |
| Perfective | add or enhance functionality on request |
| Preventive | pre-empt future problems |

**A5 in one line:** No — training diverts your best people, communication paths
grow as *n(n−1)/2* against at-best-linear output, and sequential work cannot be
parallelised. Remedies: **cut scope, extend the schedule, re-plan.**

**Draw if asked:** the two failure curves, side by side, labelled.

## Practice

**PYQ — 1.**

> **[[se-ete-2025-26]] Q A5 (2 marks, CO1)** — "A software development process is
> delayed from its scheduled time. Is it possible to develop the software on time
> by adding more employees? Justify your answer."

Worked in full in subtopic 2. Short form: **No.** Training diverts existing staff;
communication paths grow as *n(n−1)/2* against linear output; some tasks are not
partitionable. Remedies: scope reduction, schedule extension, re-planning.
*(Unchecked — no solution key exists.)*

- **Deck — none.** `L1 PPT from 1 to 8.pdf` is expository throughout: no worked
  examples, MCQs or practice bank.
- **Textbook — unavailable.** Pressman 8e is prescribed by
  [[se-handout-2026-muj]] and is not in `raw/sources/`.
- **Total drill supply: one question, one paper.** Stated rather than padded out
  with invented questions.

## Traps

- **Answering A5 "yes, if added early enough."** The project is already delayed.
  Answer no, then justify.
- **Naming Brooks's Law instead of explaining it.** The eponym earns nothing.
- **Confusing the two curves.** Bathtub = *hardware*. Software's ideal curve
  flattens; its real curve ratchets upward. Label which is which.
- **Saying software "wears out".** It deteriorates — the wrong verb signals you
  missed the point of the diagram.
- **Treating documentation as optional.** It is one of the three components of
  software by definition.

## Sources

- `raw/sources/ppts/2025/L1 PPT from 1 to 8.pdf` — covers lectures 1-8. For this
  topic: the definition, SE vs CS, the crisis with its six causes and three
  failures, program vs software with both documentation tables, the five
  characteristics, the two failure curves, the eight application domains.

**Deck gaps**, confirmed by keyword sweep across all 24 decks:

| Handout content | Lecture | Deck coverage |
|---|---|---|
| Software myths | 3 | **none — zero hits for "myth" in any deck** |
| Legacy software | 3 | **none as lecture content** |
| Evolving role of software | 2 | **none under that name** |

- Rule 5: absence from the decks is **not** evidence these are out of scope.
- Rule 6's fallback is unavailable — Pressman 8e is not in the vault.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] · next
topic [[Software Engineering as a Layered Technology]]
