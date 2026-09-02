---
type: reference
scope: how SE answers are shaped, derived from the corpus
---

# Answer Patterns

**The fourth glance-reference.** [[syllabus]] says what is in scope, [[weightage]]
says what it is worth, [[story]] says why it exists — and this page says **what a
correct answer looks like**.

> [!abstract] The finding this page exists for
> Every question in this corpus belongs to one of **five answer archetypes**, and
> **the archetype governs the shape of the answer far more than the topic does.**
> A CMMI scenario and a process-model scenario are answered the same way. A DFD
> and an activity diagram are marked the same way. Learn five skeletons and you
> can shape an answer for a topic you half-remember.

## Why this page replaced the old approach

The vault's original schema came from the CN vault, where nearly every topic is a
formula and nearly every question is a calculation. It gave each subtopic a
*Formulas & variables* part and a *Solved questions* part — which is the
**numerical archetype and nothing else**.

Measured against the actual corpus, that covers 28% of the marks:

| Archetype | End Term marks | % of 80 | Assignment Qs | Old schema support |
|---|---|---|---|---|
| **Explain with reason** | **24** | **30%** | 5 | **none** |
| **Numerical** | 23 | 28% | 9 | full |
| **Scenario → identify & justify** | 15 | 19% | 1 | none |
| **Draw & label** | 13 | 16% | 7 | partial |
| **Compare & distinguish** | 5 | 6% | 2 | partial |

**The largest single earner had no support at all.** That is what this page fixes.

> [!warning] One paper, and rule 2 still governs
> The mark column is from [[se-ete-2025-26]] — a single sitting. The *archetypes*
> are corroborated by [[se-assign-1-2026]], which is coursework and contributes
> **no marks** (rule 2), but does show the instructor setting the same five
> shapes. Treat the shapes as well-evidenced and the exact percentages as thin.

---

## 1 · Scenario → identify & justify

**15 of 80 · the instructor's signature move.** Five of the paper's fifteen
questions open on a scenario. **There is not one "define X" question on the
entire paper.**

**Spot it.** A short story about an organisation or a project — *"A company
faces…"*, *"A family hires an architect…"*, *"A 15-year-old COBOL system…"* —
ending in **"identify … and justify"** or **"…with justification"**.

**The skeleton.**

1. **Name it in the first line.** One sentence, no preamble. *"This is the
   Waterfall model."* The examiner is looking for the name before anything else.
2. **Quote two or three phrases from the scenario back**, and map each to a
   property of the thing you named. This is where the marks are.
3. **Say why the nearest alternative is wrong** — one line. Scenarios are written
   to contain signals for more than one answer.
4. **Close with the general condition** — one line on when this answer applies.

**What earns the marks.** The **mapping**, not the naming. A 2-mark scenario
question is 0.5 for the name and 1.5 for the justification.

**What earns zero.** A textbook description of the thing you named. If your
answer would be identical for a different scenario, you have written the wrong
answer.

**Worked exemplar** — [[se-ete-2025-26]] A2, 2 marks:

> *"A company faces missed deadlines and inconsistent quality. They document all
> processes and collect metrics like defect rates and effort. Processes are
> adjusted based on data, resulting in more predictable, high-quality project
> delivery. Identify the CMMI maturity level and justify."*

1. **Level 4, Quantitatively Managed.**
2. *"Document all processes"* → level 3 capability, so at least 3. *"Collect
   metrics like defect rates and effort"* → quantitative measurement, level 4's
   addition. *"Adjusted based on data"* → decisions from statistics, level 4's
   defining behaviour. *"More predictable"* → level 4's stated focus.
3. **Not level 5**, which needs continuous improvement through innovation and new
   technology — neither appears in the scenario.
4. Level 4 is where a defined process becomes a *measured* one.

**Traps.**
- **Matching one keyword.** "Documented" suggests 3, "metrics" suggests 4,
  "improvement" suggests 5 — and the scenario contains several on purpose. Read
  for the **highest capability demonstrated**, and let the *outcome* phrase
  ("predictable", "consistent", "continuously improving") break the tie.
- **Hedging.** "It could be 4 or 5" scores as neither. Commit, then say why the
  other loses.
- **Answering with a category instead of a name** — "an evolutionary model"
  rather than "incremental". Your sources disagree on categories; they agree on
  names.

**Where it appears:** [[SDLC & CMMI]] · [[Conventional Process Models]] ·
[[Evolutionary Process Models]] · [[Introduction to Software Engineering]] ·
[[Coupling & Cohesion]] · [[Re-engineering & Reverse Engineering]]

---

## 2 · Explain with reason

**24 of 80 — the largest earner in the corpus, and the one with no formula to
hide behind.**

**Spot it.** *"Illustrate with reason…"* · *"Explain how X produces Y"* ·
*"Explain the distribution of … by relating them to …"* · *"How does X contribute
to Y?"* · any 6-marker whose verb is **explain**, **illustrate**, **discuss** or
**relate**.

**The skeleton.** A 6-mark explain question is **three components**, and the
third is the one candidates skip:

1. **State the thing** — the definition, the baseline numbers, the list. Roughly
   a third of the marks, and the part everyone writes.
2. **Apply it to what the question named** — the environments, the phases, the
   two contexts being contrasted. Usually a **table**. Another third.
3. **Give the mechanism — *why* it is so.** One short paragraph of causation.
   This is the final third, it is the part that is almost always missing, and it
   is what separates a recited answer from an understood one.

**What earns the marks.** Component 3. Two candidates write the same table; the
one who explains *why the trend exists* scores higher.

**What earns zero.** Listing without relating. If the question says *"relating
them to traditional, structured and CASE environments"* and your answer never
compares the three, you have answered a different question.

**Worked exemplar** — [[se-ete-2025-26]] B3, 6 marks:

> *"Explain the distribution of effort in different phases of a SDLC model by
> relating them to traditional, structured, and CASE development environments."*

1. **State:** the 40-20-40 rule — ~40% analysis and design, ~20% coding, ~40%
   testing. Finer: planning 2-3%, requirements 10-25%, design 20-25%, coding
   15-20%, testing 30-40%.
2. **Apply:** a table of the three environments against the phases, showing effort
   moving *earlier* as sophistication rises — traditional codes early and pays in
   maintenance; structured moves effort into design; CASE pushes it earliest and
   cuts coding and maintenance hardest.
3. **Mechanism:** the cost of correcting a defect rises steeply with the phase in
   which it is found, so front-loaded effort is not *additional* effort — it is
   effort **relocated** from a later phase where it would have bought less.

**Traps.**
- **Stopping after component 1.** The 40-20-40 rule alone is a third of a
  6-marker.
- **Writing prose where a table is faster.** Component 2 is almost always a grid.
- **Ignoring a qualifier.** "In large-scale projects but often avoided in Agile"
  is two contexts; answer both, then give the principle that unifies them.

**Where it appears:** [[SDLC & CMMI]] · [[Requirements Engineering]] ·
[[Software Quality Assurance]] · [[DevOps, Cloud & Virtualization]] ·
[[Black-Box Testing]] · [[Software Size Estimation]]

---

## 3 · Numerical

**23 of 80, and 9 of the assignment's 15.** All-or-nothing: a unit slip loses the
whole question.

**Spot it.** Numbers in the stem, coefficients in a note, or a table of
estimates. **COCOMO, function points, Halstead, cyclomatic complexity, velocity
and capacity** are the whole of it.

**The skeleton.**

1. **Given block, before any working.** A table: every quantity with its symbol,
   its value, and **its unit** — with conversions done here (LOC → KLOC is the
   classic). Final row: **Find**, naming what is being solved for.
2. **Numbered steps, one idea each.** Show the substitution, not just the result.
   For a fractional power, **show the log-antilog working** — that is method
   marks: `log₁₀400 = 2.60206 → × 1.05 = 2.732163 → antilog = 539.71`.
3. **The answer on its own line, with its unit.**
4. **A sanity line** where one is available — a second route to the same number,
   or a plausibility check (an average staff size of 0.4 people is wrong).

**What earns the marks.** The Given block catches half the traps in this class of
question before you start. It is not decoration.

**What earns zero.** Right method, wrong unit. **Person-months and months are
different answers to different questions** and are routinely confused.

**Worked exemplar** — [[se-ete-2025-26]] D1, 10 marks, worked in full on
[[Effort Estimation & COCOMO]]. Its shape: convert 100000 LOC → 100 KLOC · nominal
effort · EAF per case · effort and duration per case · then the *variation*
between them, which is the part the question actually asks for.

**Traps.**
- **Not dividing by 1000.** The single most expensive error available.
- **Computing duration from size instead of from effort.** *D* takes *E* as input.
- **Rounding iterations down.** ⌈2.65⌉ = 3. A partial iteration costs a whole one.
- **Giving one number when the input is a range.** Two velocities → two answers.
- **Stopping at the quantity asked for and skipping the comparison** when the verb
  is *analyze*, *evaluate* or *compare*.

**Where it appears:** [[Effort Estimation & COCOMO]] · [[Software Size Estimation]]
· [[Agile Development]] · [[Cyclomatic Complexity & Graph Matrices]] ·
[[Black-Box Testing]]

---

## 4 · Draw & label

**13 of 80 on the paper, 7 of the assignment's questions.** Graded on **notation**,
not neatness.

**Spot it.** *"Draw…"* · *"Develop the Level-0…"* · *"Construct…"* · *"Provide a
… diagram"*.

**The skeleton — three parts, always:**

1. **Legend first.** State the convention before you draw: what each shape,
   arrowhead and line style means, and **which convention** you are using
   (Yourdon vs Gane-Sarson for DFDs; the UML version otherwise). Where sources
   differ, **the deck's convention wins**.
2. **The diagram, with every element labelled.** Every arrow, every store, every
   multiplicity.
3. **The reading** — two or three lines saying what the diagram *asserts*, plus
   **the rule it must satisfy** to be correct.

**The validity rule, per diagram type** — this is the part that converts a
drawing into a defensible answer:

| Diagram | The rule it must satisfy |
|---|---|
| DFD | **Levelling balance** — every flow crossing the parent's boundary crosses the child's, unchanged in name. No data stores at level 0. |
| ER | **Cardinality at both ends** of every relationship; every many-to-many resolved into an associative entity; identifier underlined. |
| Class | Multiplicity at both ends; correct arrowhead for association vs aggregation vs composition vs inheritance. |
| Sequence | Activation lifetimes correct; every message named; order top to bottom is the semantics. |
| Activity | **Fork and join bars match** — every fork is joined; decisions are diamonds, parallelism is a bar, and confusing them is the error the question exists to catch. |
| Control flow graph | Edge and node counts must feed **V(G) = E − N + 2** consistently. |

**What earns the marks.** Labels. **An unlabelled diagram is worth close to
zero** in this subject.

**What earns zero.** A flowchart drawn with DFD symbols. A DFD has no decisions,
no loops and no sequence — it says *what data goes where*, never *in what order*.

**Worked exemplar** — [[se-ete-2025-26]] D2, 10 marks: a Bank Loan Processing
System activity diagram with a **fork/join on document verification and credit
check**. The fork is the entire point of the question; drawing a decision diamond
there loses most of the 10 marks. Worked on [[UML & Use Case Modeling]].

**Traps.**
- **Data stores in a context diagram.** There are none — one bubble and the
  outside world.
- **Unbalanced levels.** Check flow by flow before submitting.
- **Skipping the legend** because "everyone knows the symbols". It costs two lines
  and it is where the convention marks are.

**Where it appears:** [[UML & Use Case Modeling]] · [[Flow-Oriented Modeling & DFD]]
· [[Data Modeling & ERD]] · [[Cyclomatic Complexity & Graph Matrices]] ·
[[Transform & Transaction Mapping]]

---

## 5 · Compare & distinguish

**5 of 80 — the smallest archetype, and the cheapest marks on the paper.**

**Spot it.** *"Difference between X and Y"* · *"Define and differentiate…"* ·
*"Compare and contrast…"*.

**The skeleton.**

1. **A table, not prose.** Rows are *dimensions of comparison*, columns are the
   things. Three to five rows for a 3-marker.
2. **Name the dimension in every row.** "Scope", "when it happens", "who performs
   it" — not an unlabelled list of differences.
3. **One closing line naming the single distinction that matters most**, if there
   is one. *"Cohesion is intra-module, coupling is inter-module"* is the mark.

**What earns the marks.** Choosing dimensions that are actually discriminating.
Two rows that both say the same thing count once.

**What earns zero.** Defining each thing separately and never comparing them.
"Define **and** differentiate" is two instructions.

**Worked exemplar** — [[se-ete-2025-26]] B2(a), 3 marks: *"Define and differentiate
cohesion and coupling."* The answer is the definition of each plus the contrast:
**cohesion is within a module, coupling is between modules; good design maximises
the first and minimises the second.**

**The pairs this subject examines** — SE is full of these precisely because they
are easy to blur:

| Pair | The distinction |
|---|---|
| Verification / validation | building the product *right* / building the *right* product |
| Cohesion / coupling | within a module / between modules |
| Error / fault / failure | human mistake / its manifestation in code / observed wrong behaviour |
| Functional / non-functional | what it does / how well it does it |
| Incremental / iterative | each pass **adds** features / each pass **refines** the whole |
| Risk identification / assessment | finding risks / analysing and ranking them |
| Black-box / white-box | tested from the specification / tested from the code |
| Framework / umbrella activity | a phase in sequence / continuous across all phases |
| Process framework / process model | what every project does / how one project arranges it |
| ILF / EIF | maintained inside the system / referenced but maintained elsewhere |

**Where it appears:** [[Coupling & Cohesion]] · [[Risk Analysis & Estimation]] ·
[[Testing Fundamentals]] · [[Requirements Engineering]] ·
[[Evolutionary Process Models]]

---

## Using this page

- **Planning revision:** each topic page's frontmatter carries `asked_as`. Sort by
  archetype to drill one shape across many topics — five scenario questions in a
  row teaches the skeleton better than five questions on one topic.
- **In the exam:** read the verb first. *Identify* → pattern 1. *Explain* →
  pattern 2. *Calculate* → pattern 3. *Draw* → pattern 4. *Differentiate* →
  pattern 5. The verb tells you the shape before you have recalled any content.
- **When you half-remember a topic:** the skeleton still earns partial marks. A
  scenario answer that names the wrong model but maps the scenario's phrases
  carefully will out-score a right name with no justification.

**Related:** [[syllabus]] · [[weightage]] · [[story]] · [[index]] ·
[[se-ete-2025-26]] · [[se-assign-1-2026]]
