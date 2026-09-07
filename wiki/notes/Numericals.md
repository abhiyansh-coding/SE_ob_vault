---
scope: MTE — lectures 1 to 32
types: 12
companion: Theory
---

# Numericals — Mid-Term (Lectures 1–32)

**Every kind of calculation the Mid-Term syllabus can ask**, in the order the
lectures teach them. Each type gets: **what it is · the formulas · the method ·
worked examples · the trap.**

> [!info] SE looks like a theory subject and is not
> On the one End Term paper in this vault, **23 of 80 marks were numerical**, and
> **9 of the assignment's 15 questions** were. Every one of them is a type below.

> [!tip] Rule 8, confirmed hard — the deck's worked examples become the questions
> Three assignment questions are deck examples with the numbers changed, and one
> is **verbatim**. The exam's COCOMO question is the deck's Example 4.7 at a
> different size. **Work the deck's examples and you have worked the paper.**
> Every example below is either a deck example or an assessed question.

---

## Contents — the 12 types, their source, and what they are worth

**One row per type.** *Lec* is the handout's 53-lecture plan. *Chapter* is the
deck it was read from, with the Aggarwal & Singh chapter number where the deck
carries one. **Two evidence columns, deliberately separate** — see the warning.

| §      | Type                                | Lec   | Chapter / deck                             | ETE marks | Assign. Qs | The core formula                                          |
| ------ | ----------------------------------- | ----- | ------------------------------------------ | --------- | ---------- | --------------------------------------------------------- |
| **0**  | *How to answer any numerical*       | —     | —                                          | —         | —          | Given → Steps → Answer → sanity                           |
| **1**  | Communication paths                 | 1–3   | `L1 PPT 1–8`                               | 0         | 0          | *n*(*n*−1)/2                                              |
| **2**  | Agile release planning (velocity)   | 9–11  | `L4 Print Questions Agile`                 | 0         | **1**      | *N* = ⌈*P*/*V*⌉                                           |
| **3**  | Sprint capacity and commitment      | 9–11  | `L4 Print Questions Agile`                 | 0         | **1**      | capacity = days × hrs/day                                 |
| **4**  | Phase effort distribution           | 12    | **unsourced** — standard text              | 0         | 0          | phase = total × phase %                                   |
| **5**  | Function point analysis             | 15    | `L7 Software Project planning` (A&S ch. 4) | 0         | **1**      | UFP = Σ(count × weight); FP = UFP × CAF                   |
| **6**  | Function points → effort → cost     | 15–16 | `L7 Software Project planning` (A&S ch. 4) | 0         | **1**      | *E* = FP ÷ productivity                                   |
| **7**  | Halstead software metrics           | 16    | **unsourced** — standard text              | 0         | **1**      | *V* = *N* log₂ *n*; *D* = (*n*₁/2)(*N*₂/*n*₂)             |
| **8**  | Static models — SEL, Walston-Felix  | 16    | `L7 Software Project planning` (A&S ch. 4) | 0         | 0          | *E* = *aL*<sup>*b*</sup>; *L* = (*E*/*a*)<sup>1/*b*</sup> |
| **9**  | The language cost break-even        | 16    | **no deck** — GATE-style                   | 0         | **1**      | set total cost<sub>L1</sub> = total cost<sub>L2</sub>     |
| **10** | Basic COCOMO                        | 17    | `L7 Software Project planning` (A&S ch. 4) | 0         | **3**      | *E* = *a*(KLOC)<sup>*b*</sup>; *D* = *cE*<sup>*d*</sup>   |
| **11** | **Intermediate COCOMO and the EAF** | 17    | `L7 Software Project planning` (A&S ch. 4) | **10**    | 0          | *E* = *a*(KLOC)<sup>*b*</sup> × EAF                       |
| **12** | Risk exposure                       | 18    | `L7 Software Project planning`             | 0         | 0          | RE = *P*(loss) × magnitude                                |
|        |                                     |       |                                            | **10**    | **9**      |                                                           |

**Appendix A** — fractional powers by hand (log → multiply → antilog), the log
table worth memorising, and log₂ for Halstead.
**Appendix B** — the master formula sheet: every formula on this page in one block.

### Which types to drill first

**Rank by the evidence you actually have, which is both columns together.**

| Priority | § | Type | Why |
|---|---|---|---|
| **1** | **11** | Intermediate COCOMO | **the only numerical on the exam paper — 10 of 80.** Its deck example is the exam question at a different size |
| **2** | **10** | Basic COCOMO | **3 assignment questions**, one of them a deck example **verbatim**. Feeds §11 |
| **3** | **5** | Function points | 1 assignment question, **3 deck worked examples**, and the weight table is never supplied |
| **4** | **2, 3** | Agile release planning and sprint capacity | 1 assignment question each — **§3 was reused from the deck verbatim, same numbers** |
| **5** | **7** | Halstead | a **seven-part** assignment question, and it is unsourced, so nobody else has revised it |
| **6** | **6, 9** | FP→cost, break-even | 1 assignment question each; both are short |
| **7** | **8** | Static models | deck Example 4.4 only — but it is the model-comparison form |
| **8** | **1, 4, 12** | Comm paths, phase effort, risk exposure | never assessed anywhere; small, cheap insurance |

> [!warning] Why ETE marks and assignment questions are two columns and never one
> **Rule 2: weightage comes from the exam papers and nothing else.** An assignment
> is not a sitting of the exam, so **no coursework question can ever move the marks
> column** — which is why §10 shows **0 marks** despite carrying three assignment
> questions.
>
> **But throwing coursework away would be its own mistake.** It is direct evidence
> of what your instructor thinks matters, so it gets its own column and is read as
> **emphasis, never as weight**.
>
> Read the two together and the message is unambiguous: **the exam paper computed
> COCOMO and nothing else, while the coursework computed nine different things.**
> The 0 in the ETE column next to function points and Halstead means *not asked on
> one day* — not *safe to skip*.
>
> And once more: **these are End Term marks. The Mid-Term's format is unknown** —
> the handout sets it at 30 marks and says nothing about its sections.

## §0 · How to answer any numerical — the skeleton that earns method marks

**Four parts, always, in this order.** Skipping part 1 is how half the marks in
this class are lost before any arithmetic starts.

1. **A Given block, before any working.** A small table: every quantity, its
   symbol, its **value** and its **unit** — with conversions done *here*
   (LOC → KLOC, person-years → person-months). Last row: **Find**, naming what is
   being solved for.
2. **Numbered steps, one idea each.** Show the **substitution**, not just the
   result. For a fractional power, **show the log-antilog working** — that is
   method marks (see the appendix).
3. **The answer on its own line, with its unit.**
4. **A sanity line** where a second route exists — or a plausibility check. *An
   average staff size of 0.4 people is wrong. A duration of 19 months when effort
   was 19 person-months is a unit error.*

> [!warning] The unit rule that decides the most marks
> **Person-months and months are different answers to different questions.**
> *Effort* is in **person-months**. *Duration* is in **months**. *Staff size* is
> in **persons**. Writing "19 months" for an effort of 19 PM is the single
> commonest wrong answer in this subject.

**If the verb is *analyze*, *evaluate*, *compare* or *find the variation*, the
last step is not the quantity — it is the comparison.** Candidates who compute
both cases correctly still lose those marks by stopping.

---

## §1 · Lectures 1–3 — Communication paths *(the one-line numerical)*

**What it is.** The arithmetic behind "adding people to a late project makes it
later". Rarely a question on its own; **always worth one line inside the written
answer**, because it converts an assertion into a proof.

$$\text{communication channels} = \frac{n(n-1)}{2}$$

| *n* people | Channels | vs *n* = 3 |
|---|---|---|
| 3 | 3 | — |
| 6 | 15 | **5×** the channels for 2× the people |
| 12 | 66 | **22×** the channels for 4× the people |

**The point to write:** output rises **at best linearly** with *n*, while
coordination cost rises **quadratically**. Somewhere the second overtakes the
first, and past that point adding people **subtracts** throughput.

---

## §2 · Lectures 9–11 — Agile release planning (velocity)

**What it is.** *"When will this release be done, and what will it cost?"* You are
given a backlog of estimates, a **velocity range** and a cost per iteration.

**Why a range:** velocity is **measured, not promised** — it is what the team
actually completed last iteration. Because the input is a range, **the answer is a
range.** Giving one number is a wrong answer even if the arithmetic is right.

### Formulas

| Symbol | Meaning | Units |
|---|---|---|
| *P* | total story points / ideal days in the release | points |
| *V* | velocity — completed per iteration | points/iteration |
| *N* | number of iterations | iterations — **always rounded UP** |
| *L* | iteration length | weeks |
| *C* | cost per iteration | currency |

$$N = \left\lceil \frac{P}{V} \right\rceil \qquad \text{Duration} = N \times L \qquad \text{Cost} = N \times C$$

**⌈ ⌉ is the ceiling — round up.** ⌈2.65⌉ = **3**. A partial iteration still
occupies a whole one; you cannot buy 0.65 of a two-week sprint.

### Method

1. **Sum the story estimates** → *P*.
2. **Compute twice** — once at the low velocity, once at the high.
3. *N* = ⌈*P*/*V*⌉ **at each bound**. Round up both times.
4. Duration = *N* × *L*. Cost = *N* × *C*.
5. **Report both bounds as a range**, in *both* iterations and weeks if asked.

### Worked — [[se-assign-1-2026]] Q1 *(deck question, numbers changed)*

> A team decides the next release includes Stories 1–11. Velocity for release
> planning is **14–20 ideal days per iteration**. The team works in a **2-week
> iteration**. It costs **$48,000 per iteration** to fund the team.
> Calculate the estimated duration (in iterations and weeks), and the cost.
>
> | Story | S1 | S2 | S3 | S4 | S5 | S6 | S7 | S8 | S9 | S10 | S11 |
> |---|---|---|---|---|---|---|---|---|---|---|---|
> | **Ideal days** | 4 | 6 | 5 | 3 | 7 | 2 | 5 | 6 | 4 | 8 | 3 |

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Story estimates | — | 4, 6, 5, 3, 7, 2, 5, 6, 4, 8, 3 ideal days |
| Velocity range | *V* | **14 to 20** ideal days per iteration |
| Iteration length | *L* | 2 weeks |
| Cost per iteration | *C* | $48,000 |
| **Find** | | duration in iterations **and** weeks; total cost |

**Step 1 — total the release scope.**

*P* = 4 + 6 + 5 + 3 + 7 + 2 + 5 + 6 + 4 + 8 + 3 = **53 ideal days**

**Step 2 — iterations at the optimistic velocity, *V* = 20.**

*N* = ⌈53 / 20⌉ = ⌈2.65⌉ = **3 iterations**

**Step 3 — iterations at the pessimistic velocity, *V* = 14.**

*N* = ⌈53 / 14⌉ = ⌈3.79⌉ = **4 iterations**

**Step 4 — duration.** 3 × 2 = **6 weeks** · 4 × 2 = **8 weeks**

**Step 5 — cost.** 3 × $48,000 = **$144,000** · 4 × $48,000 = **$192,000**

> **Answer: 3 to 4 iterations — 6 to 8 weeks — costing $144,000 to $192,000.**

**Traps.**
- **Rounding down.** 2.65 → **3**, not 2.
- **Giving one number.** Two velocities, two answers, every time.
- **Reporting iterations and forgetting weeks.** The question asks for both.

---

## §3 · Lectures 9–11 — Sprint capacity and commitment

**What it is.** *"Which stories should the team commit to this sprint?"* Given
per-member availability and a prioritised backlog with task-hour estimates.

**The one thing to internalise: capacity is in HOURS and commitment is decided in
HOURS.** Story points are reported, **never used for the stopping rule**.

### Formulas

$$\text{member capacity} = \text{days available} \times \text{hours per day}$$
$$\text{team capacity} = \sum \text{member capacities} \qquad \text{(a range, if hours/day is a range)}$$

**The stopping rule:** walk the backlog **in priority order**, accumulating task
hours, and **stop at the first story that does not fit.**

### Method

1. **Per member: days × hours/day**, computing a **low and a high** where
   hours/day is a range.
2. **Sum** for team capacity as a range; take the **midpoint** as the working
   figure.
3. **Accumulate task hours down the prioritised list.**
4. **Apply the stopping rule at each bound** and say which bound you planned to.

### Worked — [[se-assign-1-2026]] Q4 *(deck question, VERBATIM — identical numbers)*

> Your team is planning out the next sprint. You've chosen to fill the sprint by
> taking stories in priority order from the product backlog and **stopping when
> you reach the first story that won't fit** in the sprint. Based on the following
> details, which stories should the team commit to for a sprint?
>
> **Table 1:** Prioritized stories with estimated story points and total estimate
> in hrs of tasks for that story.
>
> | Story | Story Points | Total of Tasks Estimates |
> |---|---|---|
> | Story 1 | 5 | 16 hrs |
> | Story 2 | 8 | 16 hrs |
> | Story 3 | 5 | 24 hrs |
> | Story 4 | 3 | 16 hrs |
> | Story 5 | 13 | 32 hrs |
> | Story 6 | 8 | 26 hrs |
> | Story 7 | 5 | 8 hrs |
> | Story 8 | 8 | 15 hrs |
> | Story 9 | 5 | 12 hrs |
>
> **Table 2:** Capacity of team members for the given sprint.
>
> | Name | # days available | Hours / day | Capacity (hrs) |
> |---|---|---|---|
> | John | 3 | 4-5 | *you compute this* |
> | Matt | 5 | 2-3 | |
> | Sally | 5 | 4-5 | |
> | Ram | 5 | 2-3 | |

**Given:** nine prioritised stories with points and task hours; four members with
days available and an hours/day range. **Find:** team capacity, and the stories to
commit to.

**Step 1 — each member's capacity as a range.**

| Member | Days | Hrs/day | Low | High |
|---|---|---|---|---|
| John | **3** | 4–5 | 3 × 4 = 12 | 3 × 5 = 15 |
| Matt | 5 | 2–3 | 5 × 2 = 10 | 5 × 3 = 15 |
| Sally | 5 | 4–5 | 5 × 4 = 20 | 5 × 5 = 25 |
| Ram | 5 | 2–3 | 5 × 2 = 10 | 5 × 3 = 15 |
| **Team total** | | | **52 hrs** | **70 hrs** |

**Midpoint capacity = (52 + 70) / 2 = 61 hrs.**

**Step 2 — accumulate task hours in priority order.**

| After story | Task hrs | Cumulative hrs | Cumulative points |
|---|---|---|---|
| Story 1 | 16 | 16 | 5 |
| Story 2 | 16 | 32 | 13 |
| Story 3 | 24 | **56** | 18 |
| Story 4 | 16 | 72 | 21 |

**Step 3 — apply the stopping rule at each bound.**

- **Conservative, 52 hrs:** Stories 1–2 fit at 32 hrs. Story 3 would reach 56 > 52
  → stop. **Commit Stories 1–2** (32 hrs, 13 points).
- **Midpoint, 61 hrs:** Stories 1–3 fit at 56 hrs. Story 4 would reach 72 > 61
  → stop. **Commit Stories 1–3** (56 hrs, 18 points).
- **Optimistic, 70 hrs:** Stories 1–3 still fit at 56. Story 4 reaches 72 > 70
  → stop. **Commit Stories 1–3.**

> **Answer: commit to Stories 1, 2 and 3 — 56 hours of tasks against a team
> capacity of 52–70 hours (midpoint 61), totalling 18 story points.** Story 4
> would need 72 hours, exceeding even the optimistic bound. A team planning
> strictly to the conservative 52-hour figure commits only Stories 1 and 2.

**Traps.**
- **Committing by story points.** The rule compares **task hours** to capacity.
- **Forgetting John has only 3 days.** Every other member has 5. That asymmetry is
  the arithmetic the question is checking.
- **Not stating the range.** Give capacity as 52–70 and say which bound you planned
  to.

---

## §4 · Lecture 12 — Phase effort distribution

**What it is.** Given a total effort, split it across the SDLC phases — or given
one phase's effort, recover the total. Small, and it turns the 40-20-40 rule from
a recited fact into a computed one.

### Formulas

$$\text{phase effort} = \text{total effort} \times \text{phase \%}$$

| Group | Share | Finer split (organic) | Share |
|---|---|---|---|
| Analysis + design | **~40%** | planning | 2–3% |
| Coding | **~20%** | requirements | 10–25% |
| Testing + debugging | **~40%** | design | 20–25% |
| | | coding | 15–20% |
| | | testing | 30–40% |

**Detailed COCOMO's one figure:** the **plan and requirements** phase is **6–8% of
effort** and **10–40% of development time**.

### Worked — a 1133 PM semi-detached project *(constructed, from §10's Example 4.6)*

> A 200 KLOC semi-detached project has been estimated at **1133 PM over 29.3
> months**. Distribute the effort across phases using the 40-20-40 rule and state
> the average staffing for the coding phase.

**Given:** *E* = 1133 PM, *D* = 29.3 months. **Find:** phase efforts.

**Step 1 — the three-way split.**

| Group | % | Effort |
|---|---|---|
| Analysis + design | 40% | 0.40 × 1133 = **453 PM** |
| Coding | 20% | 0.20 × 1133 = **227 PM** |
| Testing + debugging | 40% | 0.40 × 1133 = **453 PM** |
| **Total** | 100% | **1133 PM** ✔ |

**Step 2 — sanity check.** 453 + 227 + 453 = 1133 PM. The parts must reconcile to
the total; if they do not, a percentage was misread.

**Step 3 — the point worth stating.** **Coding is the smallest phase.** The 227 PM
of coding is dwarfed by the 906 PM spent before and after it — which is the whole
argument of the 40-20-40 rule.

**Trap.** **Lifetime vs development.** Maintenance is ~60% of *lifetime* effort;
40-20-40 describes *development* effort only. **Say which you are splitting.**

---

## §5 · Lecture 15 — Function point analysis

**What it is.** Size the system from **externally visible functionality**, read
straight off the requirements — **before a line of code exists**. Count the five
functional units, weight each by complexity, then optionally adjust by 14
environmental factors.

### Formulas

$$\text{UFP} = \sum_{i=1}^{5}\sum_{j=1}^{3} Z_{ij}\,w_{ij} \;=\; \sum(\text{count} \times \text{weight})$$

$$\text{CAF} = 0.65 + 0.01\sum_{i=1}^{14} F_i \qquad\qquad \text{FP} = \text{UFP} \times \text{CAF}$$

| Symbol | Meaning |
|---|---|
| *Z<sub>ij</sub>* | **count** of type-*i* units classified at complexity *j* |
| *w<sub>ij</sub>* | the **weight** at row *i*, column *j* |
| *F<sub>i</sub>* | the *i*-th complexity adjustment factor, rated **0–5** |
| **UFP** | **Un**adjusted Function Points |
| **CAF** | Complexity Adjustment Factor |

### The weight table — MEMORISE IT; it is rarely supplied

| Functional unit | Low | **Average** | High |
|---|---|---|---|
| **External Inputs (EI)** | 3 | **4** | 6 |
| **External Outputs (EO)** | 4 | **5** | 7 |
| **External Inquiries (EQ)** | 3 | **4** | 6 |
| **Internal Logical Files (ILF)** | 7 | **10** | 15 |
| **External Interface Files (EIF)** | 5 | **7** | 10 |

**Mnemonic:** the three *transactional* types start at **3, 4, 3**; the two *file*
types are much heavier — **7 and 5** — because files represent stored data.

### The 14 adjustment factors

Rated **0 = no influence · 1 = incidental · 2 = moderate · 3 = average ·
4 = significant · 5 = essential**.

Reliable backup and recovery · data communication · distributed processing ·
performance critical · heavily utilised operational environment · online data
entry · input built over multiple screens · master files updated online · complex
inputs/outputs/files/inquiries · complex internal processing · reusable code ·
conversion and installation included · multiple installations in different
organisations · designed for change and ease of use.

> [!tip] Two free self-checks
> **Each *F<sub>i</sub>* ∈ [0, 5], so Σ*F<sub>i</sub>* ∈ [0, 70] and CAF ∈
> [0.65, 1.35].** A CAF outside that band is arithmetically impossible — check
> before going further.
> **"All factors average" ⇒ Σ*F* = 14 × 3 = 42**, so **CAF = 0.65 + 0.42 = 1.07**.
> *Not* 14.

### Method

1. **Table the counts** — unit, count, complexity, weight. Read the weight off the
   **right row AND the right column**.
2. **UFP = Σ (count × weight).**
3. **If, and only if, the question asks for the adjusted count:** rate the 14
   factors, sum, CAF = 0.65 + 0.01ΣF, FP = UFP × CAF.
4. **"Unadjusted" means stop at step 2.**

### Worked A — deck Example 4.1, all factors average

> User inputs = 50, user outputs = 40, user enquiries = 35, user files = 06,
> external interfaces = 04. **Assume all complexity adjustment factors and
> weighting factors are average.** Compute the function points.

**Given**

| Functional unit | Count | Complexity | Weight |
|---|---|---|---|
| External Inputs | 50 | average | 4 |
| External Outputs | 40 | average | 5 |
| External Inquiries | 35 | average | 4 |
| **Internal Logical Files** | 6 | average | **10** |
| External Interface Files | 4 | average | 7 |
| **Find** | | | FP |

*Note: "user files" are **ILF**, weight 10 — not inputs at weight 4.*

**Step 1 — UFP.**

UFP = 50×4 + 40×5 + 35×4 + 6×10 + 4×7
  = 200 + 200 + 140 + 60 + 28 = **628**

**Step 2 — CAF.** All 14 factors average, so each *F<sub>i</sub>* = 3:

Σ*F<sub>i</sub>* = 14 × 3 = **42** → CAF = 0.65 + 0.01 × 42 = **1.07**

**Step 3 — FP.** 628 × 1.07 = 671.96

> **Answer: FP = 672.** *(Matches the deck's printed answer.)*

### Worked B — deck Example 4.2, mixed complexities, CAF supplied

> 10 low external inputs, 12 high external outputs, 20 low internal logical files,
> 15 high external interface files, 12 average external inquiries, CAF = **1.10**.
> What are the **unadjusted** and **adjusted** function point counts?

**Given**

| Functional unit | Count | Complexity | Weight |
|---|---|---|---|
| External Inputs | 10 | **low** | 3 |
| External Outputs | 12 | **high** | 7 |
| Internal Logical Files | 20 | **low** | 7 |
| External Interface Files | 15 | **high** | 10 |
| External Inquiries | 12 | average | 4 |
| CAF | | | 1.10 |
| **Find** | | | UFP **and** FP |

**Step 1 — UFP.**

UFP = 10×3 + 12×7 + 20×7 + 15×10 + 12×4
  = 30 + 84 + 140 + 150 + 48 = **452**

**Step 2 — FP.** 452 × 1.10 = **497.2**

> **Answer: UFP = 452, FP = 497.2.** *(Matches the deck.)*

**This example exists to catch one thing:** the counts are **not in table order**
and each carries **its own complexity**. Read the weight off the right row *and*
the right column.

### Worked C — deck Example 4.3, full mixed count, CAF derived from words

> External Inputs: 10 low, 15 average, 17 high. External Outputs: 6 low, 13 high.
> External Inquiries: 3 low, 4 average, 2 high. Internal logical files: 2 average,
> 1 high. External Interface files: 9 low. In addition the system requires:
> **significant** data communication; performance is **very critical**; designed
> code may be **moderately** reusable; the system is **not designed** for multiple
> installation in different organizations. Other factors are **average**. Compute
> the function points.

**Step 1 — build the UFP table.**

| Unit | Count × weight | Sub-totals | Unit total |
|---|---|---|---|
| **EI** | 10×3 · 15×4 · 17×6 | 30 · 60 · 102 | **192** |
| **EO** | 6×4 · 0×5 · 13×7 | 24 · 0 · 91 | **115** |
| **EQ** | 3×3 · 4×4 · 2×6 | 9 · 16 · 12 | **37** |
| **ILF** | 0×7 · 2×10 · 1×15 | 0 · 20 · 15 | **35** |
| **EIF** | 9×5 · 0×7 · 0×10 | 45 · 0 · 0 | **45** |
| | | **UFP** | **424** |

**Step 2 — rate the 14 factors.** The four stated conditions override the default
of *average* (3):

| Factor | Rating | From the words |
|---|---|---|
| data communication | **4** | "**significant**" |
| performance critical | **5** | "**very critical**" = essential |
| reusable code | **2** | "**moderately**" |
| multiple installations | **0** | "**not designed for**" = no influence |
| all ten others | 3 | "treated as average" |

Σ*F<sub>i</sub>* = 3+4+3+5+3+3+3+3+3+3+2+3+0+3 = **41**

**Step 3 — CAF.** 0.65 + 0.01 × 41 = **1.06** *(inside [0.65, 1.35] ✔)*

**Step 4 — FP.** 424 × 1.06 = 449.44

> **Answer: FP = 449.** *(Matches the deck.)*

**This is the exam-shaped version:** the CAF must be **derived by mapping words
onto the 0–5 scale**. ***Significant* = 4 and *essential* = 5 are the two most
easily confused.**

### Worked D — [[se-assign-1-2026]] Q14, **Unadjusted** only

> Online Hospital Management System. EI = 18, EO = 15, EQ = 10, ILF = 8, EIF = 4.
> Weights: EI=4, EO=5, EQ=4, ILF=10, EIF=7. Calculate the **Unadjusted Function
> Point (UFP)**.

| Unit | Calculation | FP |
|---|---|---|
| EI | 18 × 4 | 72 |
| EO | 15 × 5 | 75 |
| EQ | 10 × 4 | 40 |
| ILF | 8 × 10 | 80 |
| EIF | 4 × 7 | 28 |
| **UFP** | | **295** |

> **Answer: UFP = 295 function points.**

*(Had it asked for **adjusted** FP with all factors average: CAF = 1.07, so
FP = 295 × 1.07 = 315.65 ≈ **316**. **Not asked — do not volunteer it as the
answer**, but knowing it protects you if the wording changes.)*

**Traps for this whole type.**
- **Applying the CAF when the question says *Unadjusted*.** UFP stops before it.
- **Taking "all factors average" as Σ*F* = 14.** It is **42**.
- **A CAF outside 0.65–1.35.** Arithmetically impossible.
- **Reading the wrong weight column.** Default is *Average*; ILF spans 7/10/15.
- **Misclassifying "user files" as EI.** They are **ILF** — the heaviest weights,
  so this is the costliest mistake available.
- **Confusing ILF and EIF.** Maintained **inside** vs referenced from **elsewhere**.

---

## §6 · Lectures 15–16 — Function points to effort and cost

**What it is.** The bridge from a size to money. **Effort comes from
productivity**; cost comes from a **rate per person-month**.

### Formulas

$$\text{Effort (PM)} = \frac{\text{size in FP}}{\text{productivity in FP per PM}}$$
$$\text{avg cost per PM} = \frac{\text{team monthly cost}}{\text{team size}} \qquad \text{Total cost} = \text{Effort} \times \text{avg cost per PM}$$

**And the cross-check route:** Duration = Effort ÷ team size, then
Total cost = Duration × team monthly cost. **Both routes must agree** — that is
what tells you the averaging step was legitimate.

### Worked — [[se-assign-1-2026]] Q10 *(also a deck question)*

> A project is estimated at **400 FP**. A team of five (one project manager, two
> senior developers, one junior developer, one tester) is assigned. Monthly
> salaries are **₹90,000, ₹70,000, ₹50,000 and ₹45,000** respectively. Average
> productivity is **10 FP per person-month**. Calculate the total cost.

**Given**

| Quantity | Value |
|---|---|
| Size | 400 FP |
| Productivity | 10 FP per person-month |
| Team | 1 PM, **2 senior developers**, 1 junior, 1 tester = **5 people** |
| Salaries/month | ₹90,000 (PM) · ₹70,000 (**each** senior) · ₹50,000 (junior) · ₹45,000 (tester) |
| **Find** | total project cost |

> **State the ambiguity and resolve it:** four salary figures are given for five
> people. **The two senior developers share the ₹70,000 rate.**

**Step 1 — effort.** *E* = 400 FP ÷ 10 FP/PM = **40 person-months**

**Step 2 — team cost per month.**

= 90,000 + (**2** × 70,000) + 50,000 + 45,000
= 90,000 + 140,000 + 50,000 + 45,000 = **₹3,25,000 per month**

**Step 3 — average cost per person-month.** ₹3,25,000 ÷ 5 = **₹65,000 per PM**

**Step 4 — total cost.** 40 PM × ₹65,000 = **₹26,00,000**

**Step 5 — cross-check by the other route.**
Duration = 40 PM ÷ 5 people = **8 months**.
Cost = 8 months × ₹3,25,000/month = **₹26,00,000** ✔ Both routes agree.

> **Answer: ₹26,00,000 (₹26 lakh), over an 8-month schedule with 40 person-months
> of effort.**

**Traps.**
- **Counting ₹70,000 once.** There are **two** senior developers.
- **Multiplying 40 PM by the full team monthly cost.** That double-counts the team
  — ₹1.3 crore instead of ₹26 lakh. **Person-months already account for
  headcount.**
- Stating the answer without the ambiguity note.

---

## §7 · Lecture 16 — Halstead software metrics

**What it is.** Size and complexity from **counting tokens**. Every token in a
program is either an **operator** (anything that acts: `+`, `=`, `if`, `while`,
function names, brackets) or an **operand** (anything acted upon: variables,
constants, literals). **From four counts, everything else follows by formula.**

**Why it exists:** LOC can be inflated by formatting; FP depends on subjective
ratings. **Halstead's counts are objective and mechanically extractable from
source.** Its limitation, worth one honest line: **it needs the code to exist**, so
unlike function points it **cannot be used before implementation**.

### Formulas

| Symbol | Meaning |
|---|---|
| ***n*₁** | number of **distinct** operators |
| ***n*₂** | number of **distinct** operands |
| ***N*₁** | **total** occurrences of operators |
| ***N*₂** | **total** occurrences of operands |

> **Lower-case *n* = DISTINCT. Upper-case *N* = TOTAL.** Confusing them makes every
> derived quantity wrong. **Log base 2 throughout.**

| Quantity | Formula | What it means |
|---|---|---|
| Vocabulary | *n* = *n*₁ + *n*₂ | how many different tokens exist |
| Length | *N* = *N*₁ + *N*₂ | how many tokens in total |
| Estimated length | *N̂* = *n*₁log₂*n*₁ + *n*₂log₂*n*₂ | predicted length from vocabulary alone |
| **Volume** | ***V* = *N* log₂ *n*** | information content, in **bits** |
| **Difficulty** | ***D* = (*n*₁/2) × (*N*₂/*n*₂)** | how hard to write or understand |
| Level | *L* = 1/*D* | the inverse — higher is simpler |
| **Effort** | ***E* = *D* × *V*** | elementary mental discriminations |
| Time | *T* = *E*/18 | **seconds** (18 = the Stroud number) |
| Delivered defects | *B* = *V*/3000 | predicted bugs at delivery |

### Method

Write the four inputs down first, **labelled**. Then substitute in order:
*n*, *N* → *N̂* → *V* → *D* → *E* → *T*, *B*. **Nothing here is a choice; it is
all substitution.**

### Worked — [[se-assign-1-2026]] Q13

> A banking application module contains **25 distinct operators, 40 distinct
> operands, 150 total operators, and 250 total operands.** Estimate the program
> vocabulary and length; the estimated program length; the volume; the difficulty;
> the effort; the development time and delivered defects; and interpret.

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Distinct operators | *n*₁ | **25** |
| Distinct operands | *n*₂ | **40** |
| Total operators | *N*₁ | **150** |
| Total operands | *N*₂ | **250** |
| **Find** | | vocabulary, length, *N̂*, *V*, *D*, *E*, *T*, *B* |

**(a) Vocabulary and length.**

*n* = *n*₁ + *n*₂ = 25 + 40 = **65**
*N* = *N*₁ + *N*₂ = 150 + 250 = **400**

**(b) Estimated program length.**

log₂25 = ln 25 / ln 2 = 3.2189 / 0.6931 = **4.6439**
log₂40 = ln 40 / ln 2 = 3.6889 / 0.6931 = **5.3219**

*N̂* = 25 × 4.6439 + 40 × 5.3219 = 116.10 + 212.88 = **328.97**

*Compare with the actual N = 400:* the estimate is ~18% low, which is normal —
*N̂* predicts length from vocabulary alone and **cannot see repetition**.

**(c) Volume.**

log₂65 = ln 65 / ln 2 = 4.1744 / 0.6931 = **6.0224**
*V* = *N* × log₂*n* = 400 × 6.0224 = **2408.95 bits**

**(d) Difficulty.**

*D* = (*n*₁/2) × (*N*₂/*n*₂) = (25/2) × (250/40) = 12.5 × 6.25 = **78.125**

**(e) Effort.**

*E* = *D* × *V* = 78.125 × 2408.95 = **1,88,199** elementary mental discriminations

*(Also worth stating: program level *L* = 1/*D* = 1/78.125 = **0.0128** — very low,
confirming a dense implementation.)*

**(f) Time and delivered defects.**

*T* = *E*/18 = 1,88,199 / 18 = **10,455.5 seconds ≈ 2.9 hours**
*B* = *V*/3000 = 2408.95 / 3000 = **0.80 ≈ 1 delivered defect**

*(The alternative formula B = E^(2/3)/3000 gives **1.09** — also about 1 defect.
**State which formula you used.**)*

**(g) Interpretation** — a whole part of the question, and the one that asks
whether you understand the numbers:

- **Volume ≈ 2409 bits** — a small-to-moderate module. Volume measures the
  **information content** of the implementation, so it is comparable **across
  languages** in a way LOC is not.
- **Difficulty ≈ 78 is high.** It is driven by *N*₂/*n*₂ = **6.25** — each operand
  is reused on average 6.25 times — and by 25 distinct operators. **High operand
  reuse in a small vocabulary signals dense, tightly-coupled logic**, which is
  error-prone and hard to read.
- **Effort ≈ 1.88 × 10⁵ and time ≈ 2.9 hours** to comprehend or re-implement the
  module. **That is a *mental* effort figure, not a project schedule — do not
  confuse it with COCOMO person-months.**
- **≈ 1 delivered defect** predicted. **For a banking module that is not
  acceptable:** it argues for splitting the module to reduce difficulty, and for
  targeted review and testing before release.
- **The engineering recommendation:** reduce difficulty by decomposing the module
  and introducing more, better-named operands — the coupling-and-cohesion argument
  reached from a metric instead of by inspection.

**Traps.**
- **Swapping *n* and *N*.** The single error that ruins the whole question.
- **Using log₁₀.** Halstead is **base 2** throughout.
- **Skipping the interpretation part.** It is a whole part of the marks.
- **Confusing Halstead effort with COCOMO effort.** Different units, different
  meanings.

---

## §8 · Lecture 16 — Static estimation models (SEL and Walston-Felix)

**What it is.** Once you have a size, effort follows from an **empirical power law**
fitted to past projects. Different organisations measured different constants —
**and the gap between them is the honest measure of how uncertain estimation is.**

### Formulas

**Static single-variable** — one predictor, usually size: **C = a L^b**

**SEL (Software Engineering Laboratory)**, *L* in **KLOC**:

| Quantity | Formula | Units |
|---|---|---|
| Effort | *E* = **1.4 *L*<sup>0.93</sup>** | person-months |
| Documentation | *DOC* = 30.4 *L*<sup>0.90</sup> | pages |
| Duration | *D* = **4.6 *L*<sup>0.26</sup>** | months |

**Walston-Felix** (static multivariable):

| Quantity | Formula |
|---|---|
| Effort | *E* = **5.2 *L*<sup>0.91</sup>** |
| Duration | *D* = **4.1 *L*<sup>0.36</sup>** |

**Reversing for size:** $L = \left(\dfrac{E}{a}\right)^{1/b}$

**Derived quantities**

| Quantity | Formula | Units |
|---|---|---|
| Productivity | LOC ÷ effort | LOC per PM or per PY |
| **Average manning** | **total effort ÷ duration** | **persons** |
| Cost | effort (PM) × cost per PM | currency |

> **Unit trap: 1 person-year = 12 person-months.** And ***L* is in KLOC*** in
> every formula — substituting raw LOC is off by a factor of ~1000.

**Because *b* is close to 1 in both models, effort scales nearly linearly with
size. Duration uses a much smaller exponent** — which is the formal reason
schedule cannot be compressed in proportion to effort. **That is the
"adding-people" argument appearing as arithmetic.**

### Worked — deck Example 4.4, comparing the two models

> Compare the Walston-Felix model with the SEL model on a software development
> expected to involve **8 person-years** of effort. (a) lines of source code
> produced (b) duration of development (c) productivity in LOC/PY (d) average
> manning.

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Effort | *E* | 8 person-years = **96 person-months** |
| SEL | | *E* = 1.4 *L*<sup>0.93</sup>, *D* = 4.6 *L*<sup>0.26</sup> |
| Walston-Felix | | *E* = 5.2 *L*<sup>0.91</sup>, *D* = 4.1 *L*<sup>0.36</sup> |
| **Find** | | LOC, duration, productivity, average manning — **for each model** |

**Step 0 — convert units.** 8 PY × 12 = **96 person-months**. Every constant above
is fitted for person-months; **using 8 here is the classic error.**

**Step (a) — reverse each effort equation for size.** *L* = (*E*/*a*)<sup>1/*b*</sup>

*L*(SEL) = (96 / 1.4)<sup>1/0.93</sup> = (68.571)<sup>1.0753</sup> = 94.264 KLOC =
**94,264 LOC**

*L*(W-F) = (96 / 5.2)<sup>1/0.91</sup> = (18.462)<sup>1.0989</sup> = 24.632 KLOC =
**24,632 LOC**

**Step (b) — duration.**

*D*(SEL) = 4.6 × (94.264)<sup>0.26</sup> = **15.0 months**
*D*(W-F) = 4.1 × (24.632)<sup>0.36</sup> = **13.0 months**

**Step (c) — productivity**, LOC per person-year, over 8 PY:

*P*(SEL) = 94,264 / 8 = **11,783 LOC/PY**
*P*(W-F) = 24,632 / 8 = **3,079 LOC/PY**

**Step (d) — average manning** = total effort ÷ duration:

SEL: 96 / 15 = **6.4 persons** · W-F: 96 / 13 = **7.4 persons**

> **Answer.** The two models disagree by nearly a **factor of four** on size
> (94,264 vs 24,632 LOC) from **identical effort** — which is the point of the
> comparison. Walston-Felix assumes much lower productivity, so the same effort
> buys less code, finishes slightly sooner, and needs slightly more people at once.
> *(All figures match the deck.)*

**Traps.** Using 8 instead of 96 · substituting LOC where KLOC is wanted ·
reporting productivity per PM when the question said per **PY**.

---

## §9 · Lecture 16 — The language cost break-even

**What it is.** A cost-comparison algebra problem: two languages, different
productivity and maintenance profiles, **find the size at which they cost the
same**. Not from any deck — a classic GATE-style item — but its machinery is the
cost side of size estimation.

### Method

1. **Let *L* = the LOC for the cheaper-to-write language.** Express the other in
   terms of *L*.
2. **Total cost = development + maintenance**, for each.
3. Development cost = (LOC ÷ productivity) man-years × cost per man-year.
4. Maintenance = years × annual maintenance cost.
5. **Set the two totals equal and solve for *L*.**
6. **Substitute back to verify.**

### Worked — [[se-assign-1-2026]] Q11(ii)

> LOC using **L2 is twice** the LOC using L1. The product is maintained for
> **five years**. What is the LOC for L1 at which the two projects cost the same?
>
> | Parameter | L1 | L2 |
> |---|---|---|
> | Man-years for development | LOC/10000 | LOC/10000 |
> | Development cost per man-year | ₹10,00,000 | ₹7,50,000 |
> | Maintenance time | 5 years | 5 years |
> | Cost of maintenance per year | ₹1,00,000 | ₹50,000 |

**Given**

| Parameter | L1 | L2 |
|---|---|---|
| LOC | ***L*** | **2*L*** |
| Man-years | *L*/10000 | 2*L*/10000 |
| Development cost per man-year | ₹10,00,000 | ₹7,50,000 |
| Maintenance | 5 × ₹1,00,000 | 5 × ₹50,000 |
| **Find** | | *L* such that total cost is equal |

**Step 1 — total cost using L1.**

Development = (*L*/10000) × 10,00,000 = **100*L***
Maintenance = 5 × 1,00,000 = **5,00,000**
Total<sub>L1</sub> = **100*L* + 5,00,000**

**Step 2 — total cost using L2.**

Development = (**2***L*/10000) × 7,50,000 = **150*L***
Maintenance = 5 × 50,000 = **2,50,000**
Total<sub>L2</sub> = **150*L* + 2,50,000**

**Step 3 — set equal.**

100*L* + 5,00,000 = 150*L* + 2,50,000
5,00,000 − 2,50,000 = 150*L* − 100*L*
2,50,000 = 50*L*
*L* = **5,000 LOC**

**Step 4 — verify.**

L1: 100(5000) + 5,00,000 = 5,00,000 + 5,00,000 = **₹10,00,000**
L2: 150(5000) + 2,50,000 = 7,50,000 + 2,50,000 = **₹10,00,000** ✔

> **Answer: *L* = 5,000 LOC.** Below 5,000 LOC, L2's cheaper maintenance dominates
> and **L2 wins**; above it, L2's doubled code volume dominates and **L1 wins**.

**Traps.**
- **Forgetting to double L2's LOC.** It is the whole point of the question.
- **Dropping maintenance.** Total cost is explicitly development **plus** five
  years of maintenance.
- **Not verifying.** Substituting back takes ten seconds and catches sign errors.

---

## §10 · Lecture 17 — Basic COCOMO

**What it is.** **CO**nstructive **CO**st **MO**del — Boehm's. Takes **KLOC** and
returns **effort in person-months** and **duration in months**. Assumes effort
depends **only on size**.

### Formulas

$$E = a_b\,(\text{KLOC})^{b_b} \qquad\qquad D = c_b\,(E)^{d_b}$$

| Symbol | Meaning | Units |
|---|---|---|
| KLOC | size | **thousands** of lines of code |
| *E* | effort | **person-months** |
| *D* | development time | **months** |

**Basic COCOMO coefficients:**

| Mode | *a<sub>b</sub>* | *b<sub>b</sub>* | *c<sub>b</sub>* | *d<sub>b</sub>* | Size band |
|---|---|---|---|---|---|
| **Organic** | **2.4** | 1.05 | 2.5 | 0.38 | 2–50 KLOC |
| **Semi-detached** | **3.0** | 1.12 | 2.5 | 0.35 | 50–300 KLOC |
| **Embedded** | **3.6** | 1.20 | 2.5 | 0.32 | > 300 KLOC |

**Derived quantities**

$$\text{Average staff size (manpower)} = \frac{E}{D} \text{ persons} \qquad \text{Productivity} = \frac{\text{KLOC}}{E} \text{ KLOC/PM}$$

$$\text{Cost} = E \times \text{cost per person-month}$$

> **Duration takes EFFORT as its input, never size.** *D* = *c*(*E*)^*d*.
> Computing *D* from KLOC is one of the two most expensive errors in this topic.

### Method

1. **Convert LOC → KLOC on the first line.** *(÷ 1000.)*
2. **Choose the mode** — from the words if it is not stated (see §9.3 of
   [[Theory]]). The size band is a guide; *real-time*, *embedded*, *tight
   deadline* override it.
3. ***E* = *a*(KLOC)^*b***, showing the log-antilog working.
4. ***D* = *c*(*E*)^*d***, using the effort you just computed.
5. **Then whatever else is asked** — staff size *E*/*D*, productivity KLOC/*E*,
   cost *E* × rate.
6. **Answer line with units.**

### Worked A — deck Example 4.5, all three modes *(reused verbatim as assignment Q6)*

> A project was estimated to be **400 KLOC**. Calculate the effort and development
> time for each of the three modes.

**Given:** KLOC = 400; Basic coefficients. **Find:** *E* and *D* per mode.

**(i) Organic** — *a* = 2.4, *b* = 1.05, *c* = 2.5, *d* = 0.38

*E* = 2.4 × (400)<sup>1.05</sup>
  · log₁₀400 = 2.60206 → × 1.05 = 2.732163 → antilog = **539.71**
  · *E* = 2.4 × 539.71 = **1295.31 PM**
*D* = 2.5 × (1295.31)<sup>0.38</sup> = **38.07 months**

**(ii) Semi-detached** — *a* = 3.0, *b* = 1.12, *c* = 2.5, *d* = 0.35

*E* = 3.0 × (400)<sup>1.12</sup> = **2462.79 PM**
*D* = 2.5 × (2462.79)<sup>0.35</sup> = **38.45 months**

**(iii) Embedded** — *a* = 3.6, *b* = 1.20, *c* = 2.5, *d* = 0.32

*E* = 3.6 × (400)<sup>1.20</sup> = **4772.81 PM**
*D* = 2.5 × (4772.81)<sup>0.32</sup> = **37.6 ≈ 38 months**

> **Answer.** Effort ranges from **1295 to 4773 PM — a factor of 3.7** — while
> duration stays near **38 months in all three modes**.
> **Say this explicitly, it is the lesson:** the mode changes how many **people**
> you need far more than how **long** it takes.
> *(Matches the deck.)*

### Worked B — deck Example 4.6, mode selection + staff size + productivity

> A project size of **200 KLOC** is to be developed. The team has **average
> experience on similar types of project**. The schedule is **not very tight**.
> Calculate the effort, development time, average staff size and productivity.

**Step 1 — choose the mode.** 200 KLOC sits in the semi-detached band (50–300),
the team has *average previous experience*, and the schedule is *not very tight*.
**All three signals agree: semi-detached.** *(The deck justifies it on exactly
those two phrases, not on the size — say so.)*

**Step 2 — effort.** *E* = 3.0 × (200)<sup>1.12</sup> = **1133.12 PM**

**Step 3 — duration.** *D* = 2.5 × (1133.12)<sup>0.35</sup> = **29.3 months**

**Step 4 — average staff size.** SS = *E*/*D* = 1133.12 / 29.3 = **38.7 persons**

**Step 5 — productivity.** *P* = KLOC/*E* = 200 / 1133.12 = **0.1765 KLOC/PM**,
i.e. about **177 LOC per person-month**

> **Answer: *E* = 1133.12 PM · *D* = 29.3 months · SS ≈ 38.7 persons ·
> *P* ≈ 0.177 KLOC/PM.** *(Matches the deck.)*

### Worked C — [[se-assign-1-2026]] Q9, with cost and manpower

> Estimated size **4000 LOC**, **Basic COCOMO**, **embedded** category.
> *a* = 3.6, *b* = 1.20, *c* = 2.5, *d* = 0.32. Average cost per person-month
> **₹50,000**. Calculate: (i) Effort (ii) Cost (iii) Time (iv) Manpower.

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Size | KLOC | 4000 LOC = **4 KLOC** |
| Mode | — | embedded (stated) |
| Coefficients | *a*, *b*, *c*, *d* | 3.6, 1.20, 2.5, 0.32 |
| Cost per person-month | — | ₹50,000 |
| **Find** | | effort, cost, time, manpower |

**(i) Effort.**

*E* = 3.6 × (4)<sup>1.20</sup>
· log₁₀4 = 0.60206 → × 1.20 = 0.722472 → antilog = **5.278**
· *E* = 3.6 × 5.278 = **19.00 person-months**

**(ii) Cost.** = *E* × ₹50,000 = 19.00 × 50,000 = **₹9,50,000**

**(iii) Time.**

*D* = 2.5 × (19.00)<sup>0.32</sup>
· log₁₀19 = 1.27875 → × 0.32 = 0.409201 → antilog = **2.566**
· *D* = 2.5 × 2.566 = **6.41 months**

**(iv) Manpower** — average staff size. *N* = *E*/*D* = 19.00 / 6.41 = 2.96
≈ **3 persons**

> **Answer: *E* = 19 PM · Cost = ₹9,50,000 · *D* = 6.41 months · Manpower ≈ 3
> people.**

**Sanity check:** 3 people × 6.41 months ≈ 19 person-months ✔ — and 3 people is a
plausible team. *If your manpower comes out as 0.4 or 300, your E or D is wrong.*

### Worked D — [[se-assign-1-2026]] Q11(i), mode from the words

> A simple stand-alone software utility in 'C' by a **team of software experts**
> for a computer running Linux; overall size **20,000 LOC**. (*a*, *b*) = (2.4,
> 1.05); (*c*, *d*) = (2.5, 0.38). **Approximately how long** does the project take?

**Step 0 — identify the mode.** The question does not name it: *"a simple
stand-alone utility"*, *"team of software experts"*, familiar environment →
**organic**. The given (2.4, 1.05) confirms it.

**Given:** 20,000 LOC = **20 KLOC**; organic. **Find: development time.**

**Step 1 — effort.** *(needed, because D depends on it)*

*E* = 2.4 × (20)<sup>1.05</sup>
· log₁₀20 = 1.30103 → × 1.05 = 1.366081 → antilog = **23.23**
· *E* = 2.4 × 23.23 = **55.76 person-months**

**Step 2 — duration.**

*D* = 2.5 × (55.76)<sup>0.38</sup>
· log₁₀55.76 = 1.74629 → × 0.38 = 0.663591 → antilog = **4.609**
· *D* = 2.5 × 4.609 = **11.52 months**

> **Answer: approximately 11.5 months — call it about 12 months.**

**Trap:** reporting **55.76** as the answer. That is **effort**, not time. The
question says *"how long"*, which is *D*.

---

## §11 · Lecture 17 — Intermediate COCOMO and the EAF

**What it is.** Basic COCOMO says a 100 KLOC embedded system costs a fixed amount
regardless of **who** builds it, on **what** hardware, under **what** reliability
requirement. **That is obviously false.** Intermediate COCOMO corrects it with
**15 cost drivers**, whose product is the **Effort Adjustment Factor**.

> [!warning] The coefficient set identifies the model — the question will not say so
> **Only *a* changes between Basic and Intermediate.** *b*, *c* and *d* are
> identical. And *a* moves in **opposite directions**:
>
> | Mode | Basic *a* | Intermediate *a* |
> |---|---|---|
> | Organic | 2.4 | **3.2** ↑ |
> | Semi-detached | 3.0 | 3.0 — unchanged |
> | Embedded | 3.6 | **2.8** ↓ |
>
> **Given *a* = 2.8 you are in Intermediate, embedded.** Given *a* = 3.2 you are
> in Intermediate, organic.

### Formulas

$$E = a_i\,(\text{KLOC})^{b_i} \times \text{EAF} \qquad\qquad D = c_i\,(E)^{d_i}$$

$$\text{EAF} = \prod_{\text{applicable drivers}} (\text{multiplier})$$

**Intermediate COCOMO coefficients:**

| Mode | *a<sub>i</sub>* | *b<sub>i</sub>* | *c<sub>i</sub>* | *d<sub>i</sub>* |
|---|---|---|---|---|
| Organic | **3.2** | 1.05 | 2.5 | 0.38 |
| Semi-detached | 3.0 | 1.12 | 2.5 | 0.35 |
| Embedded | **2.8** | 1.20 | 2.5 | 0.32 |

> **EAF is a PRODUCT, never a sum.**
> **EAF multiplies the effort only.** Duration is computed from the *adjusted*
> effort — so the EAF reaches duration **indirectly, through *E***, and never by
> multiplying *D*.

### The cost-driver multiplier table

| Driver | Very low | Low | Nominal | High | Very high | Extra high |
|---|---|---|---|---|---|---|
| RELY reliability | 0.75 | 0.88 | 1.00 | 1.15 | 1.40 | — |
| DATA database size | — | 0.94 | 1.00 | 1.08 | 1.16 | — |
| CPLX complexity | 0.70 | 0.85 | 1.00 | 1.15 | 1.30 | 1.65 |
| TIME runtime perf. | — | — | 1.00 | 1.11 | 1.30 | 1.66 |
| STOR memory | — | — | 1.00 | 1.06 | 1.21 | 1.56 |
| VIRT VM volatility | — | 0.87 | 1.00 | 1.15 | 1.30 | — |
| TURN turnaround | — | 0.87 | 1.00 | 1.07 | 1.15 | — |
| ACAP analyst capability | 1.46 | 1.19 | 1.00 | 0.86 | 0.71 | — |
| AEXP application exp. | **1.29** | 1.13 | 1.00 | 0.91 | **0.82** | — |
| **PCAP** programmer capability | 1.42 | **1.17** | 1.00 | **0.86** | **0.70** | — |
| VEXP virtual machine exp. | 1.21 | 1.10 | 1.00 | 0.90 | — | — |
| **LEXP** language experience | **1.14** | 1.07 | 1.00 | **0.95** | — | — |
| MODP modern practices | 1.24 | 1.10 | 1.00 | 0.91 | 0.82 | — |
| TOOL software tools | 1.24 | 1.10 | 1.00 | 0.91 | 0.83 | — |
| SCED required schedule | 1.23 | 1.08 | 1.00 | 1.04 | 1.10 | — |

**Directions:** capability and experience drivers → **below 1** when better (less
effort). Demand drivers (RELY, CPLX, TIME, STOR) → **above 1** when more
demanding. **SCED is the odd one — both ends exceed 1.00**, because compressing
*or* stretching a schedule costs effort.

### Method

1. **Given block; convert LOC → KLOC on the first line.** State the mode **and
   which model the coefficients belong to**.
2. **Nominal effort** *E*<sub>nom</sub> = *a*(KLOC)^*b*, with the log-antilog
   working shown.
3. **EAF = product** of the supplied multipliers.
4. **Adjusted effort** = *E*<sub>nom</sub> × EAF. **Then** *D* = *c*(*E*)^*d*.
5. **Repeat for each case.**
6. **Compute what was actually asked** — usually **the variation between the
   cases, absolute AND percentage.**

### Worked — [[se-ete-2025-26]] Q D1, 10 marks (4 + 4 + 2)

> "For a project of **100000 LOC embedded system**, compare the efforts and time
> duration and find out the **effort variation and time variation** if:
> • Highly capable programmers but very little experience in programming language
> (**PCAP = .86, LEXP = 1.14**)
> • Programmers of low capability but a lot of experience with programming
> language (**PCAP = 1.17, LEXP = .95**)
> (Note: *a<sub>i</sub>* = 2.8, *b<sub>i</sub>* = 1.20, *c<sub>i</sub>* = 2.5,
> *d<sub>i</sub>* = .32)"

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Size | KLOC | 100000 LOC = **100 KLOC** |
| Mode | — | **embedded** (stated) |
| Model | — | **Intermediate** — *a* = 2.8 identifies it |
| Effort coefficients | *a<sub>i</sub>*, *b<sub>i</sub>* | 2.8, 1.20 |
| Duration coefficients | *c<sub>i</sub>*, *d<sub>i</sub>* | 2.5, 0.32 |
| Case (i) | PCAP, LEXP | 0.86 (high), 1.14 (very low) |
| Case (ii) | PCAP, LEXP | 1.17 (low), 0.95 (high) |
| **Find** | | effort and duration for each; then **effort variation and time variation** |

**Step 1 — convert the size.** 100000 LOC ÷ 1000 = **100 KLOC**.
*Using 100000 here inflates the answer by (100000/100)^1.2 ≈ 4000×.*

**Step 2 — nominal effort, before any adjustment.**

*E*<sub>nominal</sub> = 2.8 × (100)<sup>1.20</sup>
· (100)<sup>1.20</sup> = (10²)<sup>1.2</sup> = 10<sup>2.4</sup> = **251.1886**
· *E*<sub>nominal</sub> = 2.8 × 251.1886 = **703.33 PM**

**Step 3 — case (i): highly capable, inexperienced in the language.**

EAF = PCAP × LEXP = 0.86 × 1.14 = **0.9804**
*E*₁ = 703.33 × 0.9804 = **689.54 PM**
*D*₁ = 2.5 × (689.54)<sup>0.32</sup> = 2.5 × 8.0977 = **20.24 months**

**Step 4 — case (ii): low capability, experienced in the language.**

EAF = PCAP × LEXP = 1.17 × 0.95 = **1.1115**
*E*₂ = 703.33 × 1.1115 = **781.75 PM**
*D*₂ = 2.5 × (781.75)<sup>0.32</sup> = 2.5 × 8.4290 = **21.07 months**

**Step 5 — the variations.** *(These are the last 2 marks — do not stop before
them.)*

**Effort variation** = 781.75 − 689.54 = **92.21 person-months**
  as a percentage: 92.21 / 689.54 = **13.37% more effort** for case (ii)

**Time variation** = 21.07 − 20.24 = **0.83 months**
  as a percentage: 0.83 / 20.24 = **4.10% longer** for case (ii)

**Answer**

| | Case (i) capable, inexperienced | Case (ii) low capability, experienced |
|---|---|---|
| EAF | 0.9804 | 1.1115 |
| Effort | **689.54 PM** | **781.75 PM** |
| Duration | **20.24 months** | **21.07 months** |

> **Effort variation ≈ 92.21 PM (13.37%); time variation ≈ 0.83 months (4.10%) —
> both in favour of case (i).**

**Step 6 — the conclusion. Write it; it is the point of the question.**

**Hiring highly capable programmers who are new to the language beats hiring
low-capability programmers who know it well.** Raw programmer capability
(**PCAP spans 1.42 down to 0.70**) has a far wider range of influence than
language experience (**LEXP spans only 1.14 down to 0.95**), so **capability
dominates**. Language experience is quickly acquired; capability is not.

*(No solution key exists for this paper, so this answer is unchecked — no `✓`.
All arithmetic independently verified.)*

### The same question in the deck — and the error it contains

> [!warning] Deck Example 4.7 is D1 at 400 KLOC, and its own slide says "EAF is wrong, please check"
> The deck asks the identical question — an embedded project, two pools of
> developers — at **400 KLOC**, with the multipliers not supplied. It then uses
> **0.82** for "very highly capable" and **1.29** for "low quality".
>
> **Neither is a PCAP value. Both are from the AEXP row.**
>
> | Row | Very low | Low | Nominal | High | Very high |
> |---|---|---|---|---|---|
> | **PCAP** programmer capability | 1.42 | **1.17** | 1.00 | 0.86 | **0.70** |
> | **AEXP** application experience | **1.29** | 1.13 | 1.00 | 0.91 | **0.82** |
>
> The deck read *programmer capability* off the *application experience* line. The
> correct PCAP values are **0.70** (very high) and **1.17** (low).
>
> **Corrected**, with *E*<sub>nom</sub> = 2.8 × 400<sup>1.20</sup> = 3712 PM:
>
> | Case | EAF | *E* | *D* |
> |---|---|---|---|
> | I PCAP very high (0.70) × LEXP very low (1.14) | **0.798** | **2962 PM** | **32.3 months** |
> | II PCAP low (1.17) × LEXP high (0.95) | **1.1115** | **4126 PM** | **35.9 months** |
>
> **The conclusion is unchanged and the correction strengthens it** — the gap
> widens from 1058 PM to 1164 PM. **The exam sidesteps the error entirely by
> supplying PCAP = 0.86 and 1.17, both genuine PCAP entries.** Whoever set D1
> appears to have known.

**Traps for the whole COCOMO type.**
- **Not converting LOC to KLOC.** The single most expensive error available.
- **Adding the cost-driver multipliers.** EAF is a **product**.
- **Computing *D* from KLOC.** *D* = *c*(*E*)^*d* — duration comes from the
  **adjusted effort**, always.
- **Using the wrong *a*.** Basic embedded is 3.6; **Intermediate embedded is 2.8**.
- **Applying the EAF to duration as well.** It adjusts effort only.
- **Omitting the variation.** D1's last 2 marks are the differences — give both
  absolute and percentage.
- **Reading a multiplier off the wrong row.** This is exactly the deck's own error;
  PCAP and AEXP are adjacent lines.
- **Dropping units.** Effort = **person-months**. Duration = **months**. Staff
  size = **persons**.

---

## §12 · Lecture 18 — Risk exposure

**What it is.** Ranking risks on one scale so limited attention goes where it does
most good. **A likely-but-minor risk and an unlikely-but-catastrophic one need a
common currency**, and this is it.

> [!warning] Never asked in this corpus — a prediction, not evidence
> The deck **defines** risk exposure but works no example. A risk-table question
> is the natural numerical form for the topic and has **never appeared**. Worth
> ten minutes, no more. *(Rule 7: stated as prediction, not fact.)*

### Formula

$$\text{Risk Exposure (RE)} = P(\text{loss}) \times \text{magnitude of loss}$$

| Symbol | Meaning | Units |
|---|---|---|
| *P*(loss) | probability of incurring a loss due to the risk | **0 to 1** |
| magnitude | potential size of that loss | money, time, or a severity score |
| RE | risk exposure | same units as the magnitude |

### Method

1. **Table the risks** — one row each, with probability and magnitude.
2. **RE = P × magnitude** for each. **Keep the units consistent** across rows, or
   the ranking is meaningless.
3. **Rank by RE, descending.** That ranking *is* risk prioritisation.
4. **State the total exposure** if asked — it is the sum of the column.
5. **Say what you would do about the top one or two** — that is risk control.

### Worked — a risk table *(constructed; no deck example exists)*

> A project team identifies four risks. Compute the risk exposure for each and
> prioritise them.
>
> | Risk | Probability | Potential loss |
> |---|---|---|
> | R1 Key developer resigns | 0.30 | ₹8,00,000 |
> | R2 Requirements change late | 0.60 | ₹3,00,000 |
> | R3 Third-party API is withdrawn | 0.10 | ₹20,00,000 |
> | R4 Test environment unavailable | 0.50 | ₹1,00,000 |

**Given:** four risks with probability *P* ∈ [0,1] and loss in ₹.
**Find:** RE for each, and the priority order.

**Step 1 — RE = P × magnitude, per risk.**

| Risk | *P* | Loss (₹) | **RE = P × loss** | Rank |
|---|---|---|---|---|
| R1 Key developer resigns | 0.30 | 8,00,000 | 0.30 × 8,00,000 = **₹2,40,000** | **1** |
| R3 Third-party API withdrawn | 0.10 | 20,00,000 | 0.10 × 20,00,000 = **₹2,00,000** | **2** |
| R2 Requirements change late | 0.60 | 3,00,000 | 0.60 × 3,00,000 = **₹1,80,000** | **3** |
| R4 Test environment unavailable | 0.50 | 1,00,000 | 0.50 × 1,00,000 = **₹50,000** | 4 |
| **Total exposure** | | | **₹6,70,000** | |

**Step 2 — read the ranking, and say what it shows.**

> **Answer: R1 (₹2,40,000) > R3 (₹2,00,000) > R2 (₹1,80,000) > R4 (₹50,000);
> total exposure ₹6,70,000.**
>
> **The point of the exercise:** **R2 is the most *likely* risk (P = 0.60) and
> ranks only third.** **R3 is the least likely (P = 0.10) and ranks second**,
> because its loss is enormous. **Ranking by probability alone would have got the
> order wrong twice** — which is precisely why exposure is the currency.

**Step 3 — control, in one line each.** R1: cross-train a second developer and
document the design (reduces magnitude). R3: negotiate a contractual notice period
or wrap the API behind an interface (reduces both). **Risk avoidance — not doing
the risky thing — is always on the menu.**

**Traps.**
- **Ranking by probability alone.** A rare catastrophe can outrank a frequent
  nuisance.
- **Mixing units across rows** — money in one, days in another. The ranking then
  means nothing.
- **Calling something a risk that has already happened.** That is a **problem**.

---

## Appendix A · Fractional powers by hand — the log-antilog method

**The exam is handwritten and closed-book. Every COCOMO and static-model question
needs a fractional power, and the working IS method marks — show it even if you
can do it on a calculator.**

**To compute *x*<sup>*p*</sup>:**

$$x^{p} = \text{antilog}\left(p \times \log_{10} x\right)$$

**Write it as three arrows.** The canonical example:

> (400)<sup>1.05</sup> :  log₁₀400 = **2.60206** → × 1.05 = **2.732163** →
> antilog = **539.71**

**Then multiply by the coefficient:** *E* = 2.4 × 539.71 = **1295.31 PM**.

### Logs worth having in your head

| *x* | log₁₀ *x* | | *x* | log₁₀ *x* |
|---|---|---|---|---|
| 2 | 0.30103 | | 20 | 1.30103 |
| 3 | 0.47712 | | 40 | 1.60206 |
| 4 | 0.60206 | | 50 | 1.69897 |
| 5 | 0.69897 | | 100 | **2.00000** |
| 8 | 0.90309 | | 200 | 2.30103 |
| 10 | **1.00000** | | 400 | 2.60206 |

**Two shortcuts that save real time:**

- **A power of 10 needs no log table at all.** (100)<sup>1.2</sup> =
  (10²)<sup>1.2</sup> = 10<sup>2.4</sup> = **251.19**. This is exactly what D1
  needs.
- **log₁₀(*ab*) = log *a* + log *b*.** So log 400 = log 4 + log 100 = 0.60206 + 2
  = **2.60206**. You only need the logs of 1–10.

### Halstead needs base 2, not base 10

$$\log_2 x = \frac{\ln x}{\ln 2} = \frac{\log_{10} x}{0.30103}$$

| *x* | log₂ *x* |
|---|---|
| 25 | 4.6439 |
| 40 | 5.3219 |
| 64 | **6.0000** |
| 65 | 6.0224 |

**Sanity anchor: log₂64 = 6 exactly.** So log₂65 must be a hair above 6 — if your
answer is 8 or 4, you used the wrong base.

---

## Appendix B · The master formula sheet

**Everything on this page, in one block.** If you memorise nothing else, memorise
this and the function-point weight table.

### Agile
$$N = \lceil P/V \rceil \qquad \text{Duration} = N \times L \qquad \text{Cost} = N \times C$$
$$\text{member capacity} = \text{days} \times \text{hours/day}$$

### Size
$$\text{KLOC} = \text{LOC} / 1000 \qquad \text{1 person-year} = \text{12 person-months}$$
$$\text{UFP} = \sum(\text{count} \times \text{weight}) \qquad \text{CAF} = 0.65 + 0.01\textstyle\sum F_i \qquad \text{FP} = \text{UFP} \times \text{CAF}$$

### Halstead — **log base 2**, lower-case *n* distinct, upper-case *N* total
$$n = n_1 + n_2 \qquad N = N_1 + N_2 \qquad \hat{N} = n_1\log_2 n_1 + n_2\log_2 n_2$$
$$V = N\log_2 n \qquad D = \frac{n_1}{2}\cdot\frac{N_2}{n_2} \qquad E = D \times V \qquad T = E/18 \qquad B = V/3000$$

### Static models — *L* in **KLOC**
$$\text{SEL: } E = 1.4L^{0.93},\; D = 4.6L^{0.26},\; DOC = 30.4L^{0.90}$$
$$\text{Walston-Felix: } E = 5.2L^{0.91},\; D = 4.1L^{0.36} \qquad L = (E/a)^{1/b}$$

### COCOMO
$$E = a(\text{KLOC})^{b} \times \text{EAF} \qquad D = c\,E^{d} \qquad \text{EAF} = \prod \text{drivers}$$
$$\text{Staff size} = E/D \qquad \text{Productivity} = \text{KLOC}/E \qquad \text{Cost} = E \times \text{rate per PM}$$

| Mode | **Basic** *a* | **Interm.** *a* | *b* | *c* | *d* |
|---|---|---|---|---|---|
| Organic | 2.4 | **3.2** | 1.05 | 2.5 | 0.38 |
| Semi-detached | 3.0 | 3.0 | 1.12 | 2.5 | 0.35 |
| Embedded | 3.6 | **2.8** | 1.20 | 2.5 | 0.32 |

### Effort and risk
$$\text{Effort from FP} = \frac{\text{FP}}{\text{FP per PM}} \qquad \text{phase effort} = \text{total} \times \text{phase \%}$$
$$\text{Risk Exposure} = P(\text{loss}) \times \text{magnitude} \qquad \text{channels} = \frac{n(n-1)}{2}$$

---

## The trap list — read this the morning of the exam

**Ranked by how much they cost.**

| # | Trap | Cost |
|---|---|---|
| 1 | **Not converting LOC → KLOC.** 100000 LOC is **100** KLOC | ~4000× wrong. Destroys every subsequent number |
| 2 | **Person-months reported as months.** Effort ≠ duration | the whole answer |
| 3 | **Computing *D* from KLOC** instead of from *E* | *D* = *c*(*E*)^*d*, always |
| 4 | **Adding the cost drivers.** EAF is a **product** | the whole EAF |
| 5 | **Wrong *a*.** Basic embedded 3.6 vs **Intermediate embedded 2.8** | every number after |
| 6 | **Stopping before the variation** when the verb is *compare*/*analyze* | the last 2 marks, reliably |
| 7 | **Swapping *n* and *N*** in Halstead, or using log₁₀ | every derived quantity |
| 8 | **Applying the CAF when the question says "Unadjusted"** | the answer is UFP |
| 9 | **"All factors average" read as Σ*F* = 14.** It is **42** → CAF **1.07** | the CAF |
| 10 | **Misclassifying user files as EI (4) rather than ILF (10)** | the heaviest weights |
| 11 | **Rounding iterations down.** ⌈2.65⌉ = **3** | a whole iteration of cost |
| 12 | **One answer where the input is a range.** Two velocities → two answers | half the marks |
| 13 | **Using 8 person-years where the formula wants 96 person-months** | 12× wrong |
| 14 | **Committing a sprint by story points** instead of task hours | the stopping rule |
| 15 | **Ranking risks by probability alone** | the whole ranking |
| 16 | **Reading a multiplier off an adjacent row** (PCAP vs AEXP) | *the deck's own error* |
| 17 | **Forgetting the second senior developer** in a salary list | the cost |
| 18 | **Multiplying person-months by the whole team's monthly cost** | 5× over — PM already counts heads |

### The four sanity checks that cost ten seconds each

1. **CAF must lie in [0.65, 1.35].** Outside it, you erred.
2. **Average staff size must be a plausible team.** 2.96 → 3 people ✔. 0.4 or 300
   means *E* or *D* is wrong.
3. **Staff size × duration ≈ effort.** 3 × 6.41 ≈ 19 PM ✔.
4. **Phase efforts must sum to the total.** 453 + 227 + 453 = 1133 ✔.

---

## What is NOT on this page

**These are numerical types in this course but sit OUTSIDE the Mid-Term window
(lectures 1–32):**

| Type | Lecture | Where it lives |
|---|---|---|
| **Cyclomatic complexity** *V(G) = e − n + 2P = π + 1 = regions* | 39 | [[01 Testing]] §4.2 |
| **BVA case counts** — 4*n*+1, robustness 6*n*+1, worst case 5ⁿ | 36 | [[01 Testing]] §3.1 |
| **Test coverage %** — lines executed ÷ total lines × 100 | 42 | [[01 Testing]] §8 |
| **Mutation score** — killed ÷ (total − equivalent) × 100 | — | [[01 Testing]] §4.5 |
| Reliability and availability measures (MTBF, MTTF, MTTR) | 48 | not yet built |

**Do not revise these for the Mid-Term.** They are listed only so you know the
page is not missing them by accident.

---

## Sources

- `raw/sources/ppts/2025/L7 Software Project planning_6.pdf` — **the main source
  for this page.** LOC definition; function point analysis in full (the five units,
  the weight table, the UFP formula, the 14 factors, CAF); worked **Examples 4.1,
  4.2, 4.3, 4.4, 4.5, 4.6 and 4.7**; the FP-to-cost question; the static
  single-variable and multivariable models with the SEL and Walston-Felix
  constants; all three COCOMO levels with both coefficient tables and the complete
  15-driver multiplier table; and risk exposure.
- `raw/sources/ppts/2025/L4 Print Questions Agile.pdf` — the two agile numericals:
  release planning (Q1) and sprint capacity (Q2). **Q2 was reused verbatim in the
  assignment.**
- `raw/sources/ppts/2025/Chapter 4 Software Project planning.pdf` — **Aggarwal &
  Singh chapter 4** (*not* the prescribed Pressman): a **61-item MCQ and exercise
  bank**, much of it COCOMO. **No answer key.** Directly relevant items: **4.16**
  (organic, 32,000 LOC — effort and nominal development time), **4.18** (effort
  distribution for a 240 KLOC organic project under four changing cost drivers),
  **4.20** (office automation, five modules of 0.5/1.5/2.0/1.0/2.0 KLOC, high
  complexity and reliability, low programmer capability — cost, schedule and
  per-phase estimates), **4.21** (600 KLOC, all three modes). *COCOMO-II items
  4.22–4.25 are **outside** this syllabus.*
- [[se-ete-2025-26]] — **Q D1**, the paper's only numerical, 10 marks.
- [[se-assign-1-2026]] — **Q1, Q4, Q6, Q9, Q10, Q11, Q13, Q14** — nine of fifteen
  questions are numerical.

**Verification status.** All arithmetic on this page has been **independently
recomputed**; every deck example matches the deck's printed figure except
**Example 4.7**, whose error is diagnosed in §11. **No solution key exists for any
paper in this vault, so nothing here carries a `✓`.**

**Gaps:**
- **Halstead is taught by no deck** — it appears across all 24 files only as MCQ
  options. §7 is standard textbook material. *(Rule 5: deck silence is not
  evidence of being out of scope; the handout names it at lecture 16.)*
- **Risk exposure has no worked example anywhere in the corpus.** §12's table is
  constructed and labelled as such.
- **Pressman 8e is not in the vault**, so rule 6's fallback is unavailable.

**Related:** [[Theory]] · [[01 Testing]] · [[answer-patterns]] §3 ·
[[Effort Estimation & COCOMO]] · [[Software Size Estimation]] ·
[[Risk Analysis & Estimation]] · [[Agile Development]] · [[weightage]] ·
[[MTE Roadmap]]
