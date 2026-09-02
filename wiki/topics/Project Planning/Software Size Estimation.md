---
phase: Project Planning
topic: Software Size Estimation
lectures: 15-16
co: CSE3102.2
asked_as: []
mte: true
studied: false
status: not-started
pyq_marks: 0
assignment_qs: 4
attempts: 0
last_practiced: null
---

# Software Size Estimation

- **Someone will ask for a date.** Size is the only thing estimable from
  requirements alone, so it comes first.
- **LOC** counts what you will write · **function points** count what the user
  will get · **static models** convert either into effort and duration.
- Then [[Effort Estimation & COCOMO]] does the same job properly.

**Prerequisites:** [[Requirements Engineering]]
**Asked as:** — — **0 marks** on the one paper · **4** in [[se-assign-1-2026]]

> [!warning] Never asked — on one paper, which is nearly no evidence
> A single paper cannot show a topic is unexamined. In syllabus, taught across
> two lectures. Lectures 15-16 is *syllabus depth* and rule 3 forbids reading it
> as marks.

> [!tip] Zero marks, but do not skip it — and it is loaded with drill
> Two reasons. First, it is the **prerequisite for
> [[Effort Estimation & COCOMO]]**, the heaviest topic in the MTE window at 10
> marks — COCOMO takes size as its input, and you cannot estimate effort from a
> size you cannot compute. Second, the decks carry **four fully worked
> numericals** plus a 61-item question bank from the Aggarwal & Singh text, which
> rule 8 rates as the highest-value drill available.

## 1 · Feasibility study and software scope

- **The deck opens with an uncomfortable question** — *is cancelling a project bad
  news?* — and answers it with IBM's numbers: **nearly a third of projects are
  cancelled anyway, and half of the survivors nearly triple their cost estimates.**
- **So the useful question is not how to avoid cancellation but how to cancel with
  the least work wasted.**
- **That is the feasibility study:** a small, deliberate investigation run before
  commitment, whose job is partly to kill projects cheaply.

**Terms and distinctions.** The three feasibility types and the IBM figures
are:

The IBM figures the deck uses to justify it: **31% of projects are cancelled
before completion**, **53% over-run their cost estimates by an average of 189%**,
and for every 100 projects there are **94 restarts**.

| Type | Asks |
|---|---|
| Technical | can it be built with available technology? |
| Economic | do the benefits exceed the costs? |
| Operational | will it work in the organisation, and will people use it? |

The deck's own technical-feasibility examples are
deliberately extreme — *is it technically feasible to provide direct
communication connectivity through space between two points on the globe?*, *is
it feasible to design a programming language using Sanskrit?* — to make the point
that technical feasibility asks whether the thing is possible **with available
technology and skills**, not whether it is imaginable.

**Software scope** bounds what the system will and will not do: the functions and
features delivered, the data in and out, the performance and constraints. It is
the input to every estimate — you cannot size what you have not bounded.

> [!note] Where this is taught
> The **L5 requirements deck** teaches feasibility inside the requirements
> chapter, immediately after requirement types. The **handout** instead names
> *Software Scope and Feasibility* under Module 5, Project Management. This vault
> follows the handout and teaches it here; revising from the L5 deck, you will
> meet it alongside [[Software Engineering Practice]].

## 2 · LOC estimation

**Definition.** A line of code includes all lines containing **program header,
declaration, and executable and non-executable statements**. **Comments and blank
lines are counted** under this definition — the predominant research definition,
and the one the deck's worked figure of **17 LOC** uses.

- **The obvious way to measure a program is to count its lines** — simple,
  automatable, directly comparable across projects in the same language, which is
  why every static model and COCOMO takes KLOC as input.
- **The problem is equally obvious.** You cannot count the lines of a program that
  does not exist yet, so at estimation time **LOC is itself an estimate**.
- **And it depends on the language:** the same functionality is more "lines" in C
  than in Python. **Function points exist because of exactly that second
  objection.**

**Formula.** The deck's definition:

> A line of code "includes all lines containing program header, declaration, and
> executable and non-executable statements".

So comments and declarations count. The deck's worked figure is counted at **17
LOC** under this rule.

**KLOC** = LOC ÷ 1000, and **KLOC is what every formula on this page and on
[[Effort Estimation & COCOMO]] takes**. Substituting raw LOC into
*E* = 1.4 *L*<sup>0.93</sup> gives an answer wrong by a factor of roughly a
thousand.

## 3 · Function point analysis

> [!tip] The CAF sanity check
> Each *F<sub>i</sub>* is rated **0 to 5**, so Σ*F<sub>i</sub>* runs 0-70 and
> **CAF runs 0.65 to 1.35**. If your CAF falls outside that band you have made an
> error — check it before going further.

- **LOC measures what the *developer* writes; function points measure what the
  *user* gets.**
- **Alan Albrecht at IBM** recognised in the 1970s that the first is unusable at
  estimation time — there is no code to count — and language-biased besides.
- **So FPA counts externally visible functionality:** what information goes in,
  what comes out, what can be asked, what the system stores, what it borrows from
  other systems.
- **Because all five can be read off the requirements, you can size a system
  before writing a line of it.** Each count is weighted by complexity, and the
  total adjusted by 14 environmental factors.

**Formula.**

$$\text{UFP} = \sum_{i=1}^{5}\sum_{j=1}^{3} Z_{ij}\,w_{ij}$$

| Symbol | Meaning |
|---|---|
| *i* | row of the weight table — the five functional unit types |
| *j* | column — Low, Average, High |
| *w<sub>ij</sub>* | the weight at row *i*, column *j* |
| *Z<sub>ij</sub>* | **count** of type-*i* units classified at complexity *j* |

$$\text{FP} = \text{UFP} \times \text{CAF}, \qquad \text{CAF} = 0.65 + 0.01\sum_{i=1}^{14} F_i$$

Each *F<sub>i</sub>* ∈ {0,…,5}, so ΣF<sub>i</sub> ∈ [0, 70] and **CAF ∈ [0.65,
1.35]**. That range is a free self-check on every answer.

**Function point weighting factors**

| Functional unit | Low | Average | High |
|---|---|---|---|
| External Inputs (EI) | 3 | **4** | 6 |
| External Outputs (EO) | 4 | **5** | 7 |
| External Inquiries (EQ) | 3 | **4** | 6 |
| Internal Logical Files (ILF) | 7 | **10** | 15 |
| External Interface Files (EIF) | 5 | **7** | 10 |

**Memorise this table.** Every function-point question needs it and it is never
supplied. Mnemonic: the three transactional types start at 3, 4, 3; the two file
types are much heavier (7 and 5) because files represent stored data.

**The five functional units, in two categories:**

| Category | Unit | Definition |
|---|---|---|
| **Data** | ILF | user-identifiable group of related data **maintained within** the system |
| **Data** | EIF | related data **referenced by** the system but maintained in **another** system |
| **Transactional** | EI | processes data or control information coming **from outside** |
| **Transactional** | EO | information **leaving** the system |
| **Transactional** | EQ | requests for **instant access** to information |

An EIF for one system may be an ILF in another — the classification depends on
which system you are counting.

**The 14 complexity adjustment factors**

Rated **0 = no influence · 1 = incidental · 2 = moderate · 3 = average ·
4 = significant · 5 = essential**.

Reliable backup and recovery · data communication · distributed processing ·
performance critical · heavily utilised operational environment · online data
entry · input built over multiple screens · master files updated online · complex
inputs/outputs/files/inquiries · complex internal processing · reusable code ·
conversion and installation included · multiple installations in different
organisations · designed for change and ease of use.

**Exam shortcut:** "assume all factors are average" means every *F<sub>i</sub>* =
3, so ΣF<sub>i</sub> = 14 × 3 = 42 and **CAF = 0.65 + 0.42 = 1.07**.

**Neither is supplied
in an exam** — both must be memorised.

**Worked example.** Three worked deck examples, in full in the Question Bank
below. They escalate exactly as an exam would: all-average, mixed with a given
CAF, then fully mixed with the CAF derived from stated conditions.

## 4 · Static estimation models

**Static, single-variable** — one predictor, usually size:

$$C = a L^{b}$$

**SEL (Software Engineering Laboratory) model**, *L* in KLOC:

| Quantity | Formula | Units |
|---|---|---|
| Effort | *E* = 1.4 *L*<sup>0.93</sup> | person-months |
| Documentation | *DOC* = 30.4 *L*<sup>0.90</sup> | pages |
| Duration | *D* = 4.6 *L*<sup>0.26</sup> | months |

**Static, multivariable** — several environment variables. **Walston-Felix**:

| Quantity | Formula |
|---|---|
| Effort | *E* = 5.2 *L*<sup>0.91</sup> |
| Duration | *D* = 4.1 *L*<sup>0.36</sup> |

**Reversing for size:** *L* = (*E* / *a*)<sup>1/*b*</sup>

**Derived quantities**

| Quantity | Formula |
|---|---|
| Productivity | LOC ÷ effort (per person-month or person-year) |
| **Average manning** | total effort ÷ duration = persons |
| Effort from FP | FP ÷ productivity (FP per person-month) |
| Cost | effort (PM) × average cost per person-month |

**Unit trap:** 1 person-year = **12 person-months**. *L* is in **KLOC** in every
formula above — substituting raw LOC is the single most common error here.

- **Once you have a size, effort follows from an empirical power law** fitted to
  past projects: *E* = *aL*<sup>b</sup>.
- **Different organisations measured different constants** — the Software
  Engineering Laboratory got *E* = 1.4*L*<sup>0.93</sup>, Walston and Felix got
  *E* = 5.2*L*<sup>0.91</sup>. **The gap between them is the honest measure of how
  uncertain this all is.**
- **Because *b* is close to 1 in both, effort scales nearly linearly with size.**
- **Duration uses a much smaller exponent** — which is the formal reason schedule
  cannot be compressed in proportion to effort. That is Brooks's Law from
  [[Introduction to Software Engineering]] appearing as arithmetic.

**Formula.** All four equations, the reversal
*L* = (*E*/*a*)<sup>1/*b*</sup>, and the derived quantities are in Quick
Reference.

| Symbol | Meaning | Units |
|---|---|---|
| *L* | size | **KLOC** |
| *E* | effort | person-months |
| *D* | duration | months |
| *DOC* | documentation | pages |
| *a*, *b* | model constants | — |

**Average manning** = total effort ÷ duration, in persons — the average number of
people needed on the project per month.

**Worked example.** Deck Example 4.4 is worked in full in the Question Bank.

## 5 · Halstead size estimation

> [!warning] Unsourced — no deck teaches this
> The handout names *Halstead Size Estimation* at lecture 16. Across all 24 files
> in `raw/sources/ppts/`, "Halstead" appears **only as multiple-choice options**
> in the Aggarwal & Singh chapter — never as taught content. Pressman 8e is not in
> the vault. What follows is standard textbook material. Rule 5: absence from the
> decks is not evidence of being out of scope.

- **LOC can be inflated by formatting; function points depend on subjective
  complexity ratings.**
- **Halstead's software science tries for something more intrinsic** by counting
  the program's **vocabulary** — how many distinct operators and operands it uses,
  and how often.
- **From four counts, everything else is derived by formula.**

**Formula.**

| Symbol | Meaning |
|---|---|
| *n*<sub>1</sub> | number of **distinct operators** |
| *n*<sub>2</sub> | number of **distinct operands** |
| *N*<sub>1</sub> | **total** occurrences of operators |
| *N*<sub>2</sub> | **total** occurrences of operands |

| Quantity | Formula |
|---|---|
| Vocabulary | *n* = *n*<sub>1</sub> + *n*<sub>2</sub> |
| Length | *N* = *N*<sub>1</sub> + *N*<sub>2</sub> |
| Estimated length | *N̂* = *n*<sub>1</sub> log₂ *n*<sub>1</sub> + *n*<sub>2</sub> log₂ *n*<sub>2</sub> |
| Volume | *V* = *N* log₂ *n* |
| Difficulty | *D* = (*n*<sub>1</sub> / 2) × (*N*<sub>2</sub> / *n*<sub>2</sub>) |
| Effort | *E* = *D* × *V* |

The distinction that carries any question here: **lower-case *n* counts distinct
symbols, upper-case *N* counts total occurrences.** Confusing them makes every
derived quantity wrong.

## How it's asked

**Zero marks on the one paper — and four of the assignment's fifteen questions.**
Like [[Agile Development]], the coursework says what the exam did not.

> [!warning] Do not read the zero as "skip it"
> This page is the **prerequisite for [[Effort Estimation & COCOMO]]**, which is
> the heaviest topic in the window. Function points and Halstead are also
> examinable on their own — the handout names both, and rule 1 governs scope.

### Numerical — the archetype to prepare

Three distinct calculations live here, and the assignment used all three:

- **Function points** — count × weight per functional unit → UFP → optionally
  × CAF. **Memorise the weighting table; it is rarely supplied.** *(Assignment
  Q14 supplied it, the deck's own examples do not.)*
- **Halstead** — four counts → vocabulary, length, volume, difficulty, effort,
  time, defects. **Lower-case *n* is distinct, upper-case *N* is total**; confuse
  them and every derived quantity is wrong. *(Assignment Q13.)*
- **Static models** — *E* = *aL*<sup>b</sup>, SEL vs Walston-Felix.
- **Cost from size** — FP ÷ productivity = effort, × rate = cost. *(Q10.)*

**Skeleton:** the standard Given → Steps → Answer of [[answer-patterns]] §3, with
the log-antilog working shown for any fractional power.

**Traps specific to this page:**
- **Applying the CAF when the question says *Unadjusted*.** UFP stops before it.
- **Confusing ILF and EIF** — maintained *inside* vs referenced from *elsewhere*.
- **Using log₁₀ in Halstead.** It is base 2 throughout.

### Explain — assignment Q13 and Q14(b)

Both open with a written part: *"explain Halstead as a technique"*, *"explain how
FPA assists estimation"*. **Lead with what the technique fixes about the
alternative** — FPA can be counted before code exists and is language-independent;
Halstead is objective where LOC is formatting-sensitive.

**Never asked as:** `draw`, `compare`, `scenario`.
**Traps specific to function points, from the deck's three worked examples:**
- **Using the wrong weight column.** The default is *Average*, not Low.
- **"All factors average" means ΣF = 42**, not 14. CAF = 0.65 + 0.42 = 1.07.
- **Classifying user files as EI rather than ILF.** The file types carry the
  heaviest weights, so misclassifying one costs the most.

**Also worth knowing:**
- **Feasibility study:** most plausible as a 2-mark "what is it / name its types".
- **LOC's unit convention is load-bearing** — KLOC is the input to D1 on
  [[Effort Estimation & COCOMO]], the paper's only numerical.
- **Static models**, if asked, take the comparison form: given an effort, reverse
  both models for size, then compute duration, productivity and manning for each.
- **Halstead:** know the four counts, vocabulary, length and volume. Do not go
  deeper until a deck or the textbook says to.

## Quick Reference

> [!abstract] The ten-minute recall card
> Everything here is taught in full above.

**Function points** — memorise the weights; they are rarely supplied:

| Functional unit | Low | **Average** | High |
|---|---|---|---|
| External Inputs (EI) | 3 | **4** | 6 |
| External Outputs (EO) | 4 | **5** | 7 |
| External Inquiries (EQ) | 3 | **4** | 6 |
| Internal Logical Files (ILF) | 7 | **10** | 15 |
| External Interface Files (EIF) | 5 | **7** | 10 |

$$\text{UFP} = \sum(\text{count} \times \text{weight}) \qquad \text{CAF} = 0.65 + 0.01\sum F_i \qquad \text{FP} = \text{UFP} \times \text{CAF}$$

- **"All factors average" ⇒ ΣF = 42**, so CAF = 0.65 + 0.42 = **1.07**.
- **CAF always lies between 0.65 and 1.35.** Outside that, you erred.
- **ILF is maintained inside** the system; **EIF is referenced but maintained
  elsewhere.** Misclassifying costs most — the file weights are heaviest.
- **"Unadjusted" means stop before the CAF.**

**Halstead** — lower-case *n* is **distinct**, upper-case *N* is **total**:

| Quantity | Formula |
|---|---|
| Vocabulary | *n* = *n*₁ + *n*₂ |
| Length | *N* = *N*₁ + *N*₂ |
| Estimated length | *N̂* = *n*₁log₂*n*₁ + *n*₂log₂*n*₂ |
| Volume | *V* = *N* log₂ *n* |
| Difficulty | *D* = (*n*₁/2) × (*N*₂/*n*₂) |
| Effort | *E* = *D* × *V* |
| Time | *T* = *E*/18 seconds |
| Delivered defects | *B* = *V*/3000 |

**Log base 2 throughout.**

**Static models:** *E* = *aL*^b — SEL gives 1.4*L*^0.93, Walston-Felix 5.2*L*^0.91.
The gap between them is the honest measure of how uncertain estimation is.

**Feasibility:** technical · economic · operational. Its job is partly to **kill
projects cheaply**.

## Practice

**PYQ questions — none.** No question on [[se-ete-2025-26]] tests this topic.

**Deck questions — 4 worked examples**, all from
`raw/sources/ppts/2025/L7 Software Project planning_6.pdf`. Arithmetic
independently re-verified against the deck; all four match exactly.

### Deck Example 4.1 — function points, all factors average

> Consider a project with the following functional units: user inputs = 50,
> user outputs = 40, user enquiries = 35, user files = 06, external interfaces =
> 04. **Assume all complexity adjustment factors and weighting factors are
> average.** Compute the function points (FP).

**Given**

| Functional unit | Count | Complexity | Weight |
|---|---|---|---|
| External Inputs | 50 | average | 4 |
| External Outputs | 40 | average | 5 |
| External Inquiries | 35 | average | 4 |
| Internal Logical Files | 6 | average | 10 |
| External Interface Files | 4 | average | 7 |
| **Find** | | | FP |

**Step 1 — UFP.**

UFP = 50×4 + 40×5 + 35×4 + 6×10 + 4×7
= 200 + 200 + 140 + 60 + 28 = **628**

**Step 2 — CAF.** All 14 factors average, so each *F<sub>i</sub>* = 3:

ΣF<sub>i</sub> = 14 × 3 = 42
CAF = 0.65 + 0.01 × 42 = 0.65 + 0.42 = **1.07**

**Step 3 — FP.**

FP = 628 × 1.07 = 671.96

**Answer: FP = 672.** *(Matches the deck's printed answer.)*

### Deck Example 4.2 — mixed complexities, CAF given

> An application has: 10 low external inputs, 12 high external outputs, 20 low
> internal logical files, 15 high external interface files, 12 average external
> inquiries, and a complexity adjustment factor of **1.10**. What are the
> unadjusted and adjusted function point counts?

**Given**

| Functional unit | Count | Complexity | Weight |
|---|---|---|---|
| External Inputs | 10 | low | 3 |
| External Outputs | 12 | high | 7 |
| Internal Logical Files | 20 | low | 7 |
| External Interface Files | 15 | high | 10 |
| External Inquiries | 12 | average | 4 |
| CAF | | | 1.10 |
| **Find** | | | UFP and FP |

**Step 1 — UFP.**

UFP = 10×3 + 12×7 + 20×7 + 15×10 + 12×4
= 30 + 84 + 140 + 150 + 48 = **452**

**Step 2 — FP.**

FP = 452 × 1.10 = **497.2**

**Answer: UFP = 452, FP = 497.2.** *(Matches the deck.)*

Note the trap this example is built around: the counts are **not** in table order,
and each carries its own complexity. Read the weight off the right row *and* the
right column.

### Deck Example 4.3 — full mixed count, CAF derived

> External Inputs: 10 low, 15 average, 17 high. External Outputs: 6 low, 13 high.
> External Inquiries: 3 low, 4 average, 2 high. Internal logical files: 2 average,
> 1 high. External Interface files: 9 low. In addition the system requires:
> significant data communication; performance is very critical; designed code may
> be moderately reusable; system is not designed for multiple installation in
> different organizations. **Other complexity adjustment factors are treated as
> average.** Compute the function points.

**Given / Find:** the counts above; find FP.

**Step 1 — build the UFP table.**

| Unit | Count × weight | Complexity totals | Unit total |
|---|---|---|---|
| **EI** | 10 × 3 · 15 × 4 · 17 × 6 | 30 · 60 · 102 | **192** |
| **EO** | 6 × 4 · 0 × 5 · 13 × 7 | 24 · 0 · 91 | **115** |
| **EQ** | 3 × 3 · 4 × 4 · 2 × 6 | 9 · 16 · 12 | **37** |
| **ILF** | 0 × 7 · 2 × 10 · 1 × 15 | 0 · 20 · 15 | **35** |
| **EIF** | 9 × 5 · 0 × 7 · 0 × 10 | 45 · 0 · 0 | **45** |
| | | **UFP** | **424** |

**Step 2 — rate the 14 factors.** The four stated conditions override the
default of *average* (3):

| Factor | Rating | From |
|---|---|---|
| F2 data communication | **4** | "significant" |
| F4 performance critical | **5** | "very critical" = essential |
| F11 reusable code | **2** | "moderately" |
| F13 multiple installations | **0** | "not designed for" = no influence |
| all ten others | 3 | "treated as average" |

ΣF<sub>i</sub> = 3+4+3+5+3+3+3+3+3+3+2+3+0+3 = **41**

**Step 3 — CAF.**

CAF = 0.65 + 0.01 × 41 = **1.06**

**Step 4 — FP.**

FP = 424 × 1.06 = 449.44

**Answer: FP = 449.** *(Matches the deck.)*

This is the exam-shaped version: the CAF must be **derived** by mapping words
onto the 0-5 scale. *Significant* = 4 and *essential* = 5 are the two most
easily confused.

### Deck Example 4.4 — comparing SEL and Walston-Felix

> Compare the Walston-Felix model with the SEL model on a software development
> expected to involve **8 person-years** of effort. (a) Calculate the number of
> lines of source code that can be produced. (b) Calculate the duration of
> development. (c) Calculate the productivity in LOC/PY. (d) Calculate the
> average manning.

**Given**

| Quantity | Symbol | Value |
|---|---|---|
| Effort | *E* | 8 person-years = **96 person-months** |
| SEL | | *E* = 1.4 *L*<sup>0.93</sup>, *D* = 4.6 *L*<sup>0.26</sup> |
| Walston-Felix | | *E* = 5.2 *L*<sup>0.91</sup>, *D* = 4.1 *L*<sup>0.36</sup> |
| **Find** | | LOC, duration, productivity, average manning for each |

**Step 0 — convert units.** 8 PY × 12 = **96 person-months**. Every constant
above is fitted for person-months; using 8 here is the classic error.

**Step (a) — reverse each effort equation for size.** *L* = (*E*/*a*)<sup>1/b</sup>

*L*(SEL) = (96 / 1.4)<sup>1/0.93</sup> = (68.571)<sup>1.0753</sup> = 94.264 KLOC =
**94,264 LOC**
*L*(W-F) = (96 / 5.2)<sup>1/0.91</sup> = (18.462)<sup>1.0989</sup> = 24.632 KLOC =
**24,632 LOC**

**Step (b) — duration.**

*D*(SEL) = 4.6 × (94.264)<sup>0.26</sup> = **15 months**
*D*(W-F) = 4.1 × (24.632)<sup>0.36</sup> = **13 months**

**Step (c) — productivity**, LOC per person-year, over 8 PY:

*P*(SEL) = 94,264 / 8 = **11,783 LOC/PY**
*P*(W-F) = 24,632 / 8 = **3,079 LOC/PY**

**Step (d) — average manning** = total effort ÷ duration:

SEL: 96 / 15 = **6.4 persons**
W-F: 96 / 13 = **7.4 persons**

**Answer:** the two models disagree by nearly a factor of four on size (94,264 vs
24,632 LOC) from identical effort — which is the point of the comparison.
Walston-Felix assumes much lower productivity, so the same effort buys less code,
finishes slightly sooner, and needs slightly more people at once.
*(All figures match the deck.)*

### Deck cost question — FP to cost

> A software project is estimated at **400 FP**. A team of five (one project
> manager, two senior developers, one junior developer, one tester) is assigned.
> Monthly salaries are ₹90,000, ₹70,000, ₹50,000 and ₹45,000 respectively.
> Average productivity is **10 FP per person-month**. Calculate the total cost.

**Step 1 — effort.** *E* = size ÷ productivity = 400 / 10 = **40 person-months**

**Step 2 — average cost per person-month.**

(90,000 + 70,000 + 70,000 + 50,000 + 45,000) / 5 = 325,000 / 5 = **₹65,000**

Note the two senior developers *both* draw ₹70,000 — five people, four salary
figures.

**Step 3 — total cost.** 40 × 65,000 = **₹26,00,000**

**Answer: ₹26,00,000.** *(Matches the deck.)*

**Textbook questions — 61 items available.**
`raw/sources/ppts/2025/Chapter 4 Software Project planning.pdf` is chapter 4 of
**K.K. Aggarwal & Yogesh Singh, *Software Engineering* (3rd ed.), New Age
International, 2007** — not the prescribed text — and carries a **Multiple Choice
Questions** bank and an **Exercises** set covering size estimation, function
points and COCOMO. **No answer key is included.** Rule 6: use it to drill
syllabus topics, never to expand scope. Most of the COCOMO items belong on
[[Effort Estimation & COCOMO]].

**Assignment questions — [[se-assign-1-2026]].** **Q10** FP → effort → project cost · **Q11(ii)** L1/L2 cost break-even · **Q13** Halstead, seven parts · **Q14** Unadjusted Function Points

Worked in full on that page, with method and traps. **Coursework, so it does not
change [[weightage]]** — but it is direct evidence of what the instructor
considers important.

## Traps

- **Substituting LOC where the formula wants KLOC.** Off by ~1000. Every static
  model and COCOMO takes *L* in thousands.
- **Using 8 instead of 96** in Example 4.4. Person-years must be converted to
  person-months; **1 PY = 12 PM**.
- **Taking "all factors average" as ΣF = 14.** It is 14 × 3 = **42**, giving
  CAF = 1.07.
- **A CAF outside 0.65-1.35.** Impossible — ΣF ranges 0 to 70. Check every answer
  against this.
- **Reading the wrong weight column.** Default is *Average*; low and high differ
  substantially, most of all for ILF (7 / 10 / 15).
- **Misclassifying files as inputs.** "User files" are **ILF**, weight 10 average
  — not EI at 4. File types carry the heaviest weights, so this is the costliest
  misclassification.
- **Confusing *significant* (4) with *essential* (5)** when deriving CAF from
  words.
- **Confusing *n* with *N*** in Halstead. Lower case = distinct, upper case =
  total.

## Sources

- `raw/sources/ppts/2025/L7 Software Project planning_6.pdf` — the main source.
  LOC definition with a 17-LOC worked figure; Albrecht and function point
  analysis in full (the five functional units in two categories, the weight
  table, the UFP formula, the 14 factors with the 0-5 scale, CAF); worked
  Examples 4.1, 4.2, 4.3 and 4.4; the FP-to-cost question; and the static
  single-variable and multivariable models with SEL and Walston-Felix constants.
- `raw/sources/ppts/2025/Chapter 4 Software Project planning.pdf` — **Aggarwal &
  Singh textbook chapter 4**, with 61 numbered MCQ and exercise items. No answer
  key.
- `raw/sources/ppts/2025/Chapter_26.ppt` — Pressman chapter 26, *Estimation for
  Software Projects*: understanding the customer's needs, the business context,
  project boundaries and motivation; and what **software scope** describes —
  functions and features delivered to end users, data in and out, content
  presented, and performance and constraints.
- `raw/sources/ppts/2025/L5 Chapter 3 Software Requirements_2.pdf` — the
  **feasibility study** section, with the IBM cancellation statistics and the
  technical-feasibility examples.

**Deck gap:** *Halstead Size Estimation* is named by the handout at lecture 16 and
is taught by **no deck**. It appears in the corpus only as MCQ options in the
Aggarwal & Singh chapter. Subtopic 5 is written from standard textbook material
and flagged inline.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] ·
previous [[Software Engineering Practice]] · next [[Effort Estimation & COCOMO]]
