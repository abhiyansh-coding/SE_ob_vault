---
phase: Process Models
topic: Agile Development
lectures: 9-11
co: CSE3102.1
mte: true
studied: false
status: not-started
pyq_marks: 0
pyq_marks_latest: 0
attempts: 0
last_practiced: null
---

# Agile Development

**Prerequisites:** [[Evolutionary Process Models]]

## Overview

> [!warning] 0 of 80 in [[se-ete-2025-26]] — not asked once, on one paper
> A single paper cannot show a topic is unexamined. In syllabus, taught across
> **three lectures**, and it is the module's longest deck treatment. Lectures 9-11
> is *syllabus depth* and rule 3 forbids reading it as marks.

> [!tip] Zero marks, but the richest question supply on any page in this vault
> The deck carries **two full numericals** — release planning and sprint capacity
> — and rule 8 rates deck questions as drill of the highest value even when a
> form has never been examined. Both are worked in the Question Bank. If this
> topic is ever examined numerically, that is what it will look like.

Agile takes the evolutionary argument to its conclusion. If requirements will
change anyway, stop treating change as failure and build the process to absorb
it: short iterations, working software over documents, the customer in the room.
Three lectures cover the manifesto, then the model zoo — Scrum, XP, ASD, DSDM,
FDD, Crystal, Agile Modeling, Kanban.

## Quick Reference

> [!abstract] The four values, which are the whole thing
> Each is "**A over B**" — B still has value, A has *more*.
> - **People over processes**
> - **Working solutions over detailed documentation**
> - **Customer collaboration over rigid contracts**
> - **Adapting to change over following a strict plan**

**Benefits:** faster time to market · better stakeholder involvement · increased
team productivity.

**Disadvantages** — the deck's own table, and the likelier exam target because
students only revise the benefits:

| Challenge | Impact |
|---|---|
| Unclear scope and timelines | hard to predict deadlines and costs |
| High stakeholder involvement | burnout and decision fatigue |
| Risk of lost details | less documentation may lose information |
| Harder to scale for large teams | coordination becomes complex |
| Team discipline needed | self-managing teams may lack focus |

**Agile vs traditional:** waterfall is strict and sequential and suits **stable
requirements**; agile breaks work into repeatable phases, involves the customer
throughout, and suits **fast-changing** projects where adaptability and speed
matter.

**The eight models the deck names:** Scrum · FDD · ASD · DSDM · XP · Crystal ·
Agile Modeling (AM) · Kanban.

### Scrum

| | |
|---|---|
| Created by | Jeff Sutherland and Ken Schwaber |
| Principles | transparency · reflection · adaptation |
| Values (5) | commitment · courage · focus · openness · respect |
| Sprint length | a time-boxed period, typically **30 days** |

**Three artifacts**

| Artifact | What it is |
|---|---|
| Product Backlog | dynamic prioritised list of everything needed; owned by the Product Owner |
| Sprint Backlog | the items chosen for the current sprint; may evolve during it |
| Increment | the usable end product of a sprint |

**Three roles**

| Role | Responsible for |
|---|---|
| Product Owner | defines stories, prioritises the backlog, decides release timing |
| Scrum leader / Master | sets up the team and sprint meetings, removes obstacles |
| Development Team | self-organising, cross-functional; plans and estimates its own sprint work |

**Events:** Sprint Planning · Sprint (the work period) · Daily Scrum / stand-up ·
Sprint Review · Sprint Retrospective.

Team size heuristic: the **two-pizza rule** — small enough to share two pizzas.

### Extreme Programming (XP)

The most specific agile framework on engineering practice. Four activities:

| Activity | Practices |
|---|---|
| Planning | **user stories** on index cards, written by the customer; team assigns a cost to each; stories grouped into a deliverable increment; **project velocity** sets later delivery dates |
| Design | KIS (keep it simple) · **CRC cards** (Class-Responsibility-Collaborator) · **spike solutions** for hard problems · **refactoring** |
| Coding | write the **unit test before the code** · **pair programming** |
| Testing | all unit tests run daily · **acceptance tests** defined by the customer |

A **spike** is a very simple program built to explore whether a proposed solution
is suitable — similar to a prototype.

### The other models

| Model | Proposed by | Distinguishing feature |
|---|---|---|
| **ASD** — Adaptive Software Development | Jim Highsmith | three phases: **speculation → collaboration → learning**; mission-driven planning, time-boxing, explicit risk consideration |
| **DSDM** — Dynamic Systems Development Method | — | **timeboxing** with firm deadlines; deliver business benefit early and often |
| **FDD** — Feature Driven Development | — | five iterative activities, organised around **features** |
| **Crystal** | Cockburn and Highsmith | **colour-coded by risk to human life** (Crystal Clear → Crystal Sapphire); six aspects — people, interaction, community, communication, skills, talents; process is secondary |
| **Agile Modeling (AM)** | — | values, principles and practices for effective modeling |
| **Kanban** | — | named by the deck, not developed |

### Planning arithmetic

| Term | Meaning |
|---|---|
| Story point / ideal day | relative size estimate for a user story |
| **Velocity** | story points a team completes per iteration |
| Iteration / sprint | fixed time box (2 weeks in the deck's example) |
| **Iterations = ceil(total points ÷ velocity)** | round **up** — a partial iteration is still an iteration |
| **Cost = iterations × cost per iteration** | |
| **Capacity (hrs) = days available × hours per day**, summed over the team | |

## Subtopic map

| # | Subtopic | Marks | Why it's here |
|---|---|---|---|
| 1 | The Agile manifesto and its trade-offs | 0 | the four values, and the disadvantages students skip |
| 2 | Scrum | 0 | the most detailed model in the deck |
| 3 | Extreme Programming | 0 | the engineering-practice model — pair programming, TDD, refactoring |
| 4 | The other agile models | 0 | ASD, DSDM, FDD, Crystal, AM, Kanban |
| 5 | Agile planning arithmetic | 0 | **two deck numericals** — the page's real drill |

## Mindmap

```mermaid
graph TD
    S1["1 · Manifesto &<br/>trade-offs · 0 marks"]
    S2["2 · Scrum<br/>0 marks"]
    S3["3 · Extreme Programming<br/>0 marks"]
    S4["4 · Other models<br/>0 marks"]
    S5["5 · Planning arithmetic<br/>0 marks · 2 deck numericals"]

    S1 -->|"values are not a process.<br/>who does what, when?"| S2
    S2 -->|"Scrum manages the team.<br/>it says nothing about the code"| S3
    S3 -->|"two answers exist. there are<br/>six more, each for a different fear"| S4
    S4 -->|"whichever you pick, someone<br/>still asks: how long, how much?"| S5
    S5 -.->|"and the answer is a range,<br/>because change is assumed"| S1
```

**1 · The Agile manifesto and its trade-offs — 0 marks**
- **What:** four "A over B" values, plus agile's benefits and its real costs.
- **Why:** every agile practice downstream is one of these four values made
  operational.
- **Important:** never examined. Know all four values **in the A-over-B form** —
  "documentation has no value" is the classic misreading. Know three
  disadvantages too.

**2 · Scrum — 0 marks**
- **What:** a management framework of three artifacts, three roles and five
  events, run in time-boxed sprints.
- **Why:** it is how agile becomes an actual schedule with accountable people.
- **Important:** never examined. If asked, the **3 artifacts / 3 roles** grid is
  the answer. Sprint ≈ 30 days; Sutherland and Schwaber.

**3 · Extreme Programming — 0 marks**
- **What:** the agile model that prescribes engineering practice — user stories,
  pair programming, test-first, refactoring, CRC cards, spikes.
- **Why:** Scrum organises people; XP is the one that says how to write the code.
- **Important:** never examined. The memorable four: **user stories, pair
  programming, test-before-code, refactoring**. Know what a *spike* is.

**4 · The other agile models — 0 marks**
- **What:** ASD, DSDM, FDD, Crystal, Agile Modeling, Kanban.
- **Why:** each optimises for a different fear — risk, deadlines, features, human
  safety.
- **Important:** never examined. One distinguishing feature each is enough; the
  table in Quick Reference is the whole subtopic. **Crystal's colour-coding by
  risk to human life** is the most memorable single fact here.

**5 · Agile planning arithmetic — 0 marks**
- **What:** velocity, release duration and cost; sprint capacity and commitment.
- **Why:** it is the one part of agile that produces a number, and numbers are
  what long questions are built from.
- **Important:** never examined — **but the deck carries two worked numericals**,
  which rule 8 rates as the highest-value drill available. **Always round
  iterations up**, and always give the answer as a **range** when velocity is
  given as a range.

## 1 · The Agile manifesto and its trade-offs

**Intuition.** Agile is not "less process". It is a bet that in a world where
requirements change, the cost of *predicting* exceeds the cost of *adapting*. So
it inverts four priorities — not abolishing the right-hand side of each pair, but
demoting it. The most common exam error is reading "working solutions over
detailed documentation" as "no documentation"; it means documentation that does
not help ship working software is waste.

**Definitions & distinctions.** The four values, the benefits and the
disadvantages table are in Quick Reference, along with the agile-vs-traditional
comparison. The framing worth carrying: waterfall suits **stable requirements**;
agile suits **fast-changing** ones. That is the same requirement-stability
question that decides every model on [[Conventional Process Models]] and
[[Evolutionary Process Models]].

**What gets asked.** Never examined on the one paper here. Note though that
[[se-ete-2025-26]] Q A3 asks why an SRS is required in large projects but often
avoided in Agile — the *answer* is agile's second value, but the marks sit on
[[Requirements Engineering]].

## 2 · Scrum

**Intuition.** Agile's values do not tell anyone what to do on Monday. Scrum
does: a small self-organising team pulls a slice of work from a prioritised list,
commits to finishing it inside a fixed time box, meets briefly every day, and
shows the result at the end. The time box is the trick — it is never extended,
so when work does not fit, *scope* gives rather than the date. That single rule is
what makes agile plannable.

**Definitions & distinctions.** Artifacts, roles, events, principles and values
are all tabulated in Quick Reference. Points that make an answer look informed:

- **Product Backlog vs Sprint Backlog.** The product backlog is everything, owned
  and reprioritised by the Product Owner. The sprint backlog is the slice chosen
  for the current sprint.
- **The Increment is usable.** Not a demo, not a branch — the usable end product
  of the sprint.
- **The Scrum leader is not a manager.** They remove obstacles and coach; the
  team plans and estimates its own work.
- Meetings are deliberately short — the deck notes stand-ups are "sometimes
  conducted without chairs".

**What gets asked.** Never examined. Most plausible form is a 2-marker on the
roles or the artifacts. The 3-and-3 grid answers both.

## 3 · Extreme Programming

**Intuition.** Scrum tells you how to organise people and says nothing about the
code. XP is the opposite: it is opinionated about engineering practice, and takes
each practice to an "extreme". If code review is good, review continuously — pair
programming. If testing is good, test before there is anything to test — write
the unit test first. If simple design is good, never build for a future you
cannot see, and restructure continuously — refactoring.

**Definitions & distinctions.** The four activities and their practices are in
Quick Reference. Terms worth defining precisely:

- **User story** — a simple, informal statement of a needed function, written by
  the customer on an index card. Similar to a use case.
- **Spike** — a very simple program built to explore whether a proposed solution
  is suitable. Similar to a prototype.
- **CRC card** — Class-Responsibility-Collaborator, XP's design notation.
- **Project velocity** — measured after the first increment, then used to set
  delivery dates for the rest. This is the link into subtopic 5.

**What gets asked.** Never examined. If it appears, pair programming and
test-before-code are the practices worth naming first.

## 4 · The other agile models

**Intuition.** The remaining models each answer a different worry. ASD worries
about risk and learning. DSDM worries about deadlines and fixes them absolutely.
FDD worries about losing track of what the product actually does, so it organises
everything around features. Crystal worries about *people* — and, uniquely,
grades its own ceremony by how much harm failure would cause. Picking between
them is picking which of those worries is yours.

**Definitions & distinctions.** The comparison table is in Quick Reference. Two
details worth holding:

- **ASD's three phases: speculation → collaboration → learning.** "Speculation"
  rather than "planning" is deliberate — it admits the plan is a guess. Adaptive
  cycle planning uses the mission statement, project constraints and basic
  requirements to produce a time-boxed release plan.
- **Crystal is colour-coded by risk to human life.** Crystal Clear for a
  six-developer project in one room; Crystal Sapphire where lives are at stake.
  Process is explicitly secondary to people.

**What gets asked.** Never examined. One distinguishing feature each is the right
depth — do not learn these in the detail of Scrum or XP.

## 5 · Agile planning arithmetic

**Intuition.** The objection to agile is always "so when will it be done?" The
answer is velocity: measure how many story points the team actually completed
last iteration, divide the remaining work by it, and you get a number of
iterations. Because velocity is measured rather than promised, it is honest — and
because it is a range, the answer is a range. Multiply iterations by the team's
burn rate and you have a cost.

**Formulas & variables.**

| Symbol | Meaning | Units |
|---|---|---|
| *P* | total story points (or ideal days) in the release | points |
| *V* | velocity — points completed per iteration | points/iteration |
| *N* | number of iterations | iterations, **always rounded up** |
| *L* | iteration length | weeks |
| *C* | cost per iteration | currency |

$$N = \lceil P / V \rceil \qquad \text{Duration} = N \times L \qquad \text{Cost} = N \times C$$

For sprint capacity, per team member: **capacity = days available × hours per
day**, summed across the team. Where hours per day is a range, the team capacity
is a range too.

**Solved questions.** Both worked in full in the Question Bank below — they are
the drill for this page.

**What gets asked.** Never examined on the one paper in this vault. But these are
**deck questions**, which rule 8 rates as the highest-value drill available,
because deck examples have repeatedly turned out to be exam questions with the
numbers changed. Two forms:

- **Spot it** — a backlog table with estimates, plus a velocity (or a velocity
  range) and an iteration length. Or a capacity table with days and hours per day.
- **Method** — sum the points; divide by velocity; **round up**; multiply out for
  duration and cost. For capacity, compute per person, sum, then take stories in
  priority order until the next one does not fit.
- **Trap** — rounding iterations *down*, or reporting a single number when the
  velocity is given as a range. Both lose the marks that the range was there to
  test. Second trap: in the sprint question, commitment is decided by **task
  hours against capacity**, not by story points.

## Question Bank

**PYQ questions — none.** No question on [[se-ete-2025-26]] tests this topic.
A3 mentions Agile but tests the SRS; its marks are on [[Requirements Engineering]].

**Deck questions — 2**, both from
`raw/sources/ppts/2025/L4 Print Questions Agile.pdf`.

### Deck Q1 — release planning duration and cost

> A team was doing release planning and they decided that the next release will
> include all stories from Story 1 to Story 11. The velocity range to be used for
> the release planning is **15-22**. The team works in a **2 week iteration**. It
> costs about **$50,000 per iteration** to fund the entire team.
> **Calculate the estimated duration for the next release. Additionally, how much
> will this release cost?**

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Story estimates, Stories 1-11 | — | 5, 5, 8, 3, 5, 5, 3, 5, 8, 8, 3 ideal days |
| Velocity range | *V* | 15 to 22 points per iteration |
| Iteration length | *L* | 2 weeks |
| Cost per iteration | *C* | $50,000 |
| **Find** | | duration and cost of the release |

**Step 1 — total the release scope.**

5 + 5 + 8 + 3 + 5 + 5 + 3 + 5 + 8 + 8 + 3 = **58 ideal days**

**Step 2 — iterations at the optimistic (high) velocity.**

*N* = ⌈58 / 22⌉ = ⌈2.64⌉ = **3 iterations**

**Step 3 — iterations at the pessimistic (low) velocity.**

*N* = ⌈58 / 15⌉ = ⌈3.87⌉ = **4 iterations**

Rounding **up** in both cases: a release needing 2.64 iterations of capacity
still occupies three iterations, because iterations are not divisible.

**Step 4 — convert to duration.**

3 × 2 = 6 weeks · 4 × 2 = 8 weeks

**Step 5 — convert to cost.**

3 × $50,000 = $150,000 · 4 × $50,000 = $200,000

**Answer: 6 to 8 weeks (3 to 4 iterations), costing $150,000 to $200,000.**

*(Deck question with no printed solution — arithmetic independently verified, but
unchecked against a key, so no `✓`.)*

### Deck Q2 — sprint commitment from capacity

> Your team is planning out the next sprint. You've chosen to fill the sprint by
> taking stories in priority order from the product backlog and **stopping when
> you reach the first story that won't fit** in the sprint. Based on the following
> details, which stories should the team commit to for a sprint?

**Given**

| Story | Story points | Task estimate (hrs) |
|---|---|---|
| 1 | 5 | 16 |
| 2 | 8 | 16 |
| 3 | 5 | 24 |
| 4 | 3 | 16 |
| 5 | 13 | 32 |
| 6 | 8 | 26 |
| 7 | 5 | 8 |
| 8 | 8 | 15 |
| 9 | 5 | 12 |

| Member | Days available | Hours/day |
|---|---|---|
| John | 3 | 4-5 |
| Matt | 5 | 2-3 |
| Sally | 5 | 4-5 |
| Ram | 5 | 2-3 |

**Find:** team capacity, and the stories to commit to.

**Step 1 — compute each member's capacity as a range.**

| Member | Low | High |
|---|---|---|
| John | 3 × 4 = 12 | 3 × 5 = 15 |
| Matt | 5 × 2 = 10 | 5 × 3 = 15 |
| Sally | 5 × 4 = 20 | 5 × 5 = 25 |
| Ram | 5 × 2 = 10 | 5 × 3 = 15 |
| **Total** | **52 hrs** | **70 hrs** |

Midpoint capacity = **61 hrs**.

**Step 2 — accumulate task hours in priority order.**

| After story | Cumulative hrs | Cumulative points |
|---|---|---|
| 1 | 16 | 5 |
| 2 | 32 | 13 |
| 3 | 56 | 18 |
| 4 | 72 | 21 |

**Step 3 — apply the stopping rule at each capacity bound.**

- At the **conservative** 52 hrs: stories 1 and 2 fit (32 hrs). Story 3 would take
  the total to 56 > 52, so stop. **Commit stories 1-2**, 32 hrs, 13 points.
- At the **midpoint** 61 hrs: stories 1-3 fit (56 hrs). Story 4 would take it to
  72 > 61, so stop. **Commit stories 1-3**, 56 hrs, 18 points.
- At the **optimistic** 70 hrs: same as midpoint — stories 1-3 fit at 56 hrs;
  story 4 reaches 72 > 70. **Commit stories 1-3.**

**Answer: commit to Stories 1, 2 and 3 — 56 hours of task estimates against a
team capacity of 52-70 hours (midpoint 61).** Stop there: Story 4 would need 72
hours, exceeding even the optimistic capacity. If the team plans strictly against
the conservative 52-hour bound, commit only Stories 1 and 2.

*(Deck question with no printed solution — arithmetic independently verified,
unchecked against a key, so no `✓`.)*

**Textbook questions — unavailable for this topic.** Pressman 8e is not in
`raw/sources/`. The two Aggarwal & Singh chapters that *are* in the vault cover
project planning and design, not agile.

## Mistakes & Traps

- **Reading the manifesto as "B has no value".** Every value is *A over B*, not
  *A instead of B*. Agile teams do document — just not for its own sake.
- **Rounding iterations down.** ⌈58/22⌉ = 3, not 2. A partial iteration still
  costs a whole iteration.
- **Giving one number when velocity is a range.** The range is the question. Two
  bounds, two durations, two costs.
- **Committing a sprint by story points instead of task hours.** Capacity is in
  hours; the stopping rule compares task estimates against it.
- **Confusing Product Backlog with Sprint Backlog.** Everything versus this
  sprint's slice.
- **Calling the Scrum leader a project manager.** They remove obstacles; the team
  self-organises.

## Course Material

- `raw/sources/ppts/2025/L2 Lec (9 - 14).pdf` — the main source. Manifesto, four
  values, benefits, the disadvantages table, agile vs traditional, the eight
  models, and Scrum in depth (principles, five values, three artifacts, three
  roles, all five events). Also XP, DSDM, FDD, Crystal and Agile Modeling.
- `raw/sources/ppts/2025/L1 PPT from 1 to 8.pdf` — a second treatment of XP
  (planning/design/coding/testing with user stories, spikes, CRC cards, pair
  programming), ASD with its three phases, Scrum, and Crystal.
- `raw/sources/ppts/2025/L4 Print Questions Agile.pdf` — **the two numericals**,
  worked above.

> [!warning] One deck for this topic has not been read
> `raw/sources/ppts/2025/L3 Agile Development models.pdf` is **17 pages of images
> with zero extractable text**. It is named for this topic and has not been opened
> visually. Nothing on this page is cited to it. It may hold additional models,
> diagrams or worked examples — worth a look by eye before the exam, and worth
> asking me to read if you want it folded in.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] ·
previous [[Evolutionary Process Models]] · next [[SDLC & CMMI]]
