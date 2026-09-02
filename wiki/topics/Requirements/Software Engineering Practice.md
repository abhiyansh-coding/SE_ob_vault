---
phase: Requirements
topic: Software Engineering Practice
lectures: 14
co: CSE3102.2
asked_as: []
mte: true
studied: false
status: not-started
pyq_marks: 0
assignment_qs: 0
attempts: 0
last_practiced: null
---

# Software Engineering Practice

- **[[Requirements Engineering]] said *what* a requirement is. This topic is the
  *procedure* for getting them** — the five activities of requirements practice:
  elicitation, analysis, documentation, validation and management, as the handout
  words lecture 14.
- **Each answers a different failure:** not knowing · not agreeing · not writing
  it down · not checking · not keeping up.

**Prerequisites:** [[Requirements Engineering]]
**Asked as:** — — **0 marks** on the one paper

**The thread:** the five activities are a pipeline, and each answers a different failure — not knowing (1) · not agreeing (2) · not writing it down (3) · not checking (4) · not keeping up (5).

> [!warning] Never asked — on one paper, which is nearly no evidence
> A single paper cannot show a topic is unexamined. In syllabus and taught.
> Lecture 14 is *syllabus depth* and rule 3 forbids reading it as marks.

## How it's asked

**Never asked, on the one paper in this vault** — `asked_as` is empty.

**If it appears, the likely shape** (prediction, not evidence): an `explain`
question naming one activity — *"explain the requirement elicitation techniques"*
— or a `compare` between two techniques. The **seven elicitation techniques with
when each fits** is the only part of this page with enough content to carry a
6-marker. See [[answer-patterns]] §2 and §5.

**Note the overlap:** specification detail lives on [[Requirements Engineering]],
which *is* examined. If a question names the SRS, answer from there.
**Also worth knowing:**
- **Validation is where V&V enters the course.** *Verification vs validation* is
  examined behaviour in the testing module ([[Testing Fundamentals]]), so get it
  right the first time you meet it here.
- **The traceability chain is management's one carryable fact** — and it explains
  why [[Software Maintenance]] is expensive when it is absent.
- Analysis's value is as the bridge into the analysis-modeling phase.

## Quick Reference

> [!abstract] The five activities, in order
> **Elicitation → Analysis → Specification (documentation) → Validation →
> Management.**
> Gather it · make sense of it · write it down · check it is right · keep it
> current. Each is defined by the failure it prevents.

| # | Activity | What happens | Techniques |
|---|---|---|---|
| 1 | **Elicitation** (gathering) | collect requirements from stakeholders | interviews · questionnaires · brainstorming · observation · workshops · prototyping · use cases / user stories |
| 2 | **Analysis** | understand, refine, resolve conflicts; classify as functional or non-functional | modeling with UML, ER diagrams |
| 3 | **Specification** (documentation) | document requirements clearly | **SRS to IEEE 830** · use cases · user stories · diagrams |
| 4 | **Validation** | check requirements are correct, complete and aligned with user needs | reviews · walkthroughs · prototyping · test-case generation |
| 5 | **Management** | handle change during development; maintain traceability | tracking tools · traceability matrix |

**Traceability chain:** requirement → design → code → test. Maintaining it is
activity 5's job and is why activity 3 must produce a written baseline.

**Verification vs validation** — introduced on [[Evolutionary Process Models]]
with the V-model, and the reason activity 4 is called *validation*:

| | Question |
|---|---|
| Verification | are we building the product **right**? |
| **Validation** | are we building the **right** product? |

**Tools named by the deck**

| Tool | Used for |
|---|---|
| JIRA | agile requirement tracking |
| IBM Rational DOORS | requirement management |
| RequisitePro | requirement documentation |
| StarUML / Enterprise Architect | modeling requirements |
| Trello, Asana | task and requirement management |

**The five framework activities** — the broader "software engineering practice"
of Module 3, defined on [[Software Engineering as a Layered Technology]] and not
repeated here: communication · planning · modeling · construction · deployment.

**Elicitation technique selection**

| Use | When |
|---|---|
| Interviews | few stakeholders, deep detail needed |
| Questionnaires | many stakeholders, shallow breadth |
| Observation | the stated process differs from the real one |
| Prototyping | the customer cannot describe what they want — the *undreamed* case |
| Workshops / brainstorming | stakeholders disagree and must converge |

## 1 · Elicitation

- **Requirements are not lying around waiting to be collected.** Users describe
  solutions rather than problems, omit everything they consider obvious, and
  cannot describe what they have never seen — the *undreamed* requirements from
  [[Requirements Engineering]].
- **Elicitation is therefore an active technique problem:** pick the method that
  suits how the knowledge is distributed.
- Ask a few experts in depth · survey many shallowly · **watch people work when
  what they say differs from what they do** · build something when they cannot say
  at all.

**Terms and distinctions.** The seven techniques and the selection guide are
in Quick Reference. **Prototyping appears here as an elicitation technique**, not
only as a process model — it is how you elicit requirements the customer cannot
articulate, which is the same argument the prototyping model makes on
[[Conventional Process Models]].

## 2 · Analysis

- **Elicitation produces a pile of wants, and some contradict each other** — the
  customer wants low cost, the developer maintainability, the manager speed.
- **Analysis is where those get negotiated** into a consistent set, sorted into
  functional and non-functional, and expressed in a notation precise enough to
  check.
- **It is where the modeling topics enter:** the deck names UML and ER diagrams as
  the analysis notation — exactly what [[Data Modeling & ERD]],
  [[Flow-Oriented Modeling & DFD]] and [[UML & Use Case Modeling]] go on to teach.

**Terms and distinctions.** Analysis does three things: **understand, refine,
resolve conflicts**; **classify** requirements as functional or non-functional;
and **model** them. The classification is taught on [[Requirements Engineering]]
and not repeated here.

## 3 · Specification

The output of analysis lives in people's heads and in meeting
notes. **Specification writes it down in a form that can be handed to someone who
was not in the room** — which is the only way work can be divided at all.

**Terms and distinctions.** Formats: the **SRS to IEEE 830**, use cases, user
stories and diagrams. The SRS's structure, purpose, characteristics and common
mistakes are all on [[Requirements Engineering]], which is where A3's marks sit —
they are not duplicated here.

## 4 · Validation

- **A requirements document can be internally perfect and still specify the wrong
  system.**
- **Validation is the check against reality:** show the specification back to
  stakeholders and confirm it is what they meant — before anyone builds anything.
- This is where the course introduces the question that recurs through the whole
  testing module: *are we building the right product?*

**Terms and distinctions.** Four techniques: **reviews, walkthroughs,
prototyping, test-case generation**. The last is the subtle one — if you cannot
write a test case for a requirement, the requirement is not verifiable, so
attempting the test cases validates the specification as a side effect.

The verification/validation pair is tabulated in Quick Reference and taught in
full on [[Evolutionary Process Models]] with the V-model.

## 5 · Management

- **Requirements change during development; that is assumed, not exceptional.**
- **Requirement management is the machinery that keeps change from silently
  invalidating everything downstream:** every change tracked, every requirement
  linked to the design, code and tests that implement it.
- **Without that chain**, a changed requirement leaves stale code and passing tests
  that verify the wrong thing.

**Terms and distinctions.** Two responsibilities: **handle changes** during
development, tracked in tools; and **maintain traceability** —
*requirement → design → code → test*. The tools table is in Quick Reference.

## Practice

**PYQ questions — none.** No question on [[se-ete-2025-26]] tests this topic
directly. A3 tests the SRS and its marks sit on [[Requirements Engineering]].

**Deck questions — none.** `L2 Lec (9 - 14).pdf` is expository for the RE-phases
section and carries no worked examples or practice bank.

**Textbook questions — unavailable for this topic.** Pressman 8e is not in
`raw/sources/`; the two Aggarwal & Singh chapters in the vault cover project
planning and design.

**This topic has no questions in any of the three tiers.** Stated rather than
filled with invented drill.

## Traps

- **Reversing verification and validation.** *Right product* is validation.
  This costs marks repeatedly in the testing module.
- **Treating elicitation as one technique.** The examinable content is *which*
  technique suits *which* situation.
- **Listing the five activities out of order.** Elicitation → analysis →
  specification → validation → management. The order is the content.
- **Forgetting that prototyping appears twice** — once as a process model, once
  as an elicitation technique. Same idea, two roles.
- **Ignoring traceability.** It is the reason requirement management exists.

## Sources

- `raw/sources/ppts/2025/L2 Lec (9 - 14).pdf` — the main source. All five RE
  phases with their technique lists, the traceability chain, the RE tools table,
  and the challenges list.
- `raw/sources/ppts/2025/L5 Chapter 3 Software Requirements_2.pdf` — the "crucial
  process steps of requirement engineering" diagram and the requirements-review
  step feeding the SRS.

> [!note] Where feasibility went
> The L5 deck teaches the **feasibility study** immediately after requirement
> types, inside the requirements chapter. The handout instead names *Software
> Scope and Feasibility* under Module 5, Project Management. This vault follows
> the handout and teaches it on [[Software Size Estimation]], where the estimation
> deck also covers scope — but if you are revising from the L5 deck, expect to
> meet it here.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] ·
previous [[Requirements Engineering]] · next [[Software Size Estimation]]
