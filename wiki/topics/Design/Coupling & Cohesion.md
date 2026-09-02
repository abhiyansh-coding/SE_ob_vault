---
phase: Design
topic: Coupling & Cohesion
lectures: 28
co: CSE3102.2
asked_as: [compare, scenario]
mte: true
studied: false
status: not-started
pyq_marks: 6
assignment_qs: 0
attempts: 0
last_practiced: null
---

# Coupling & Cohesion

**Prerequisites:** [[Design Concepts & Principles]]

## Overview

> [!info] 6 of 80 in [[se-ete-2025-26]] — question B2
> B2 is 3 + 3: **(a)** define and differentiate cohesion and coupling; **(b)**
> examine a `Library` / `Member` code snippet and identify the type of cohesion
> and coupling **with justification**. One paper only; see [[weightage]].

> [!tip] The deck contains part (b) with the classes changed
> `L9 Coupling and Cohesion.pptx` slides 5-6 pose the *identical* pattern — one
> class instantiating another and using it — and print the answer. Rule 8 again.
> The deck's answer is reproduced and examined in subtopic 3, **including where
> it disagrees with standard theory.**

- **Where "good design" stops being taste and becomes measurable.**
- **Cohesion** asks whether a module does one job; **coupling** asks how much it
  depends on others.
- **Both are ranked scales**, so you can name exactly how bad a design is rather
  than just disliking it.
- The goal is the most quoted rule in the subject: **high cohesion, low
  coupling.**

## Quick Reference

> [!abstract] The one line that answers B2(a)
> **Cohesion is *within* a module — how strongly its own elements belong
> together. Coupling is *between* modules — how much they depend on each other.
> Good design maximises cohesion and minimises coupling.**
> Cohesion is intra-module, coupling is inter-module. That contrast is the mark.

### Cohesion — seven levels, best to worst

**Cohesion is the degree to which the elements of a module are functionally
related** — the internal glue that keeps the module together.

| Rank | Type | Elements are related by | Deck's example |
|---|---|---|---|
| **1 best** | **Functional** | every element contributes to a **single computation** | a `Multiply` class whose only job is multiplying |
| 2 | **Sequential** | one element's **output is the next one's input** | `getSquare()` computes, `printSquare()` consumes it |
| 3 | **Communicational** | they operate on the **same input or output data** | update a record in the database, then send it to the printer |
| 4 | **Procedural** | they must run in a certain **order** | calculate student GPA, print student record, calculate cumulative GPA, print it |
| 5 | **Temporal** | they happen at the **same time** | system initialisation code |
| 6 | **Logical** | they are the **same category** of task but do significantly different things | a component reading input from tape, disk and network |
| **7 worst** | **Coincidental** | **nothing** but location in the source file | print next line + reverse a string, in one component |

**The deck's verdicts:** coincidental ❌ worst, avoid · logical ⚠ acceptable but
not ideal · sequential ✅ recommended · functional = the ideal situation.

### Coupling — six levels, best to worst

**Coupling is the measure of the degree of interdependence between modules.**

| Rank | Type | Modules communicate by | Deck's note |
|---|---|---|---|
| **1 best** | **Data** | passing **only data** as parameters | components independent; no tramp data. Example: customer billing system |
| 2 | **Stamp** | passing a **whole data structure** | involves tramp data; may be justified for efficiency — "a choice made by the insightful designer, not a lazy programmer" |
| 3 | **Control** | passing **control information** (a flag that selects behaviour) | bad if the parameter selects completely different behaviour; good if it enables reuse — e.g. a sort taking a comparison function |
| 4 | **External** | dependence on something **outside** the software — hardware, protocol, file format | protocol, external file, device format |
| 5 | **Common** | **shared global data** | any change means tracing every module that touches it; harms reuse, access control and maintainability |
| **6 worst** | **Content** | one module **modifies another's data**, or control jumps between them | the worst form; should be avoided |

**Tramp data** — data passed through a module that does not itself use it. It is
what distinguishes stamp coupling from data coupling.

### Mnemonics

Coupling, worst → best: **C**ontent · **C**ommon · **E**xternal · **C**ontrol ·
**S**tamp · **D**ata — *"Come Christmas Eve, Consider Stamping Data."*

Cohesion, worst → best: **C**oincidental · **L**ogical · **T**emporal ·
**P**rocedural · **C**ommunicational · **S**equential · **F**unctional —
*"Cool Lemons Taste Pretty Cool, Says Fred."*

### High cohesion, low coupling — the deck's model answer

```java
class Calculator {              // High cohesion: all methods are calculations
    public int add(int a, int b)      { return a + b; }
    public int multiply(int a, int b) { return a * b; }
}
class Display {                 // Low coupling: separate responsibility
    public void showResult(int result) { System.out.println("Result: " + result); }
}
```

The deck's analysis: `Calculator` focuses only on mathematical operations
(**functional cohesion**); `Display` is responsible only for showing results.
They are independent and only share data — **Display can be replaced without
affecting Calculator.**

## How it's asked

Generic skeletons are on [[answer-patterns]]; this section carries only what is
specific to this topic. **Both archetypes appear in one question — B2 is
`compare` then `scenario`, 3 marks each.**

### Compare & distinguish — B2(a), 3 marks

- **Spot it:** "Define **and** differentiate cohesion and coupling." Two
  instructions, and the second is where the marks are.
- **Skeleton:** a five-row table — scope · what it measures · desired direction ·
  effect if wrong · number of levels — then **one closing line**: *cohesion is
  intra-module and should be maximised; coupling is inter-module and should be
  minimised.* That line is the mark.
- **Earns the marks:** the contrast. Defining each separately and stopping earns
  roughly half.
- **Trap:** listing the seven and six levels instead of differentiating. The
  levels are subtopics 1-2; part (a) wants the *distinction*.

### Scenario → identify & justify — B2(b), 3 marks

- **Spot it:** a code snippet, usually two classes, and "identify the type of
  cohesion and coupling **with justification**."
- **Skeleton:**
  1. Name the cohesion type and the coupling type — one line each.
  2. **Point at specific lines.** *"`generateBill()` is a billing operation, a
     different concern from `addBook()` and `issueBook()`"* — quote the method
     names.
  3. Say why the adjacent level is not it.
  4. One line on how to fix it — split the class, or pass data instead.
- **Earns the marks:** step 2. **An unsupported label earns almost nothing.**
- **Trap:** the deck's own answer disagrees with standard theory on this snippet
  — see subtopic 3, which carries both readings and which to write.

**Never asked as:** `numerical`, `draw`, `explain`. Do not prepare a diagram for
this topic.

## Contents

| # | Section | Type | Archetype | Marks | Why it's here |
|---|---|---|---|---|---|
| 1 | Cohesion — the seven levels | definitional | — | 0 | the scale, and how to recognise each |
| 2 | Coupling — the six levels | definitional | — | 0 | the other scale |
| 3 | Reading code for cohesion and coupling | procedural | scenario | **6** | **carries B2**, both parts |

**The thread:** a module that does one job well still has to talk to others (1→2),
and two scales stay theory until you name them in real code (2→3) — where the fix
is always the same: **split it, or pass less**.

*(Sections 1 and 2 carry no marks of their own — B2(a)'s 3 marks are counted in
section 3, which is where the definition-and-differentiate answer is worked.)*

## 1 · Cohesion — the seven levels

- **Ask why a module's parts are in the same box.** "They all serve one
  computation" is the best possible reason — **functional cohesion**. "They happen
  at the same time" is weaker. "No reason, they were just typed near each other"
  is the worst — **coincidental**.
- The scale is a ranking of *reasons for togetherness*.
- **The practical consequence is change:** a module with one reason to exist has
  one reason to change; a module with three has three.

**Terms and distinctions.** The seven levels with the deck's own examples are
tabulated in Quick Reference. The two most confusable pairs:

| Pair | Difference |
|---|---|
| **Logical vs coincidental** | logical elements are the *same category* of task (all input routines); coincidental ones have **no** conceptual relationship at all |
| **Sequential vs communicational** | sequential: one's **output feeds** the next. Communicational: they merely **use the same data**, in no particular chain |

The deck's coincidental example is deliberately absurd — *print the next line and
reverse the characters of a string, in one component* — because the point is that
there is no defensible reason for the pairing.

## 2 · Coupling — the six levels

- **Coupling is the cost of changing something.** If A only receives data through
  parameters, you can rewrite A's insides freely.
- If A reaches into B and modifies B's variables, neither can change without
  checking the other — and if a hundred modules share a global, changing it means
  checking a hundred modules.
- **The scale ranks how far a change can propagate.**

**Terms and distinctions.** All six with the deck's notes are in Quick
Reference. Three points the deck stresses that improve an answer:

- **Control coupling is not automatically bad.** It is bad if the parameter
  selects completely different behaviour, but good if it enables factoring and
  reuse — a sort function taking a comparison function is control coupling and is
  good design.
- **Stamp coupling can be a deliberate choice.** The deck's phrasing is worth
  quoting: it "may be necessary due to efficiency factors — this choice was made
  by the insightful designer, not a lazy programmer."
- **Common coupling's real cost is traceability.** Changing global data means
  tracing back to *every* module that accesses it to evaluate the effect.

**Worked example.** The deck works three coupling types through one Java
program, and its verdict is worth carrying:

> **Deck, slides 7-9** — stamp coupling (passing an `Address` object where only
> part is used) is rated **acceptable**; common coupling (a `static sharedData`
> global) and content coupling (`modifyArray` writing `arr[0] = 100` inside an
> array it does not own) are both rated **avoid**. Among those three, **stamp is
> the best choice** because it reduces redundancy and improves modularity without
> exposing global state or modifying external structures.

*(Deck illustration with a printed analysis; not a posed question, so no `✓`.)*

## 3 · Reading code for cohesion and coupling

- **The exam form is not "define coupling"** but "here is a class, name what is
  wrong with it".
- **The method is mechanical.** For **cohesion**: list what the methods in one
  class actually do, ask whether they serve a single purpose. For **coupling**:
  find every place one class names another, ask how tight that link is.
- **Then justify by pointing at specific lines. The justification is where the
  marks are** — an unsupported label earns almost nothing.

**Worked example.**

> **[[se-ete-2025-26]] Q B2 (3 + 3 = 6 marks, CO3)** —
> **(a)** Define and differentiate Cohesion and Coupling in software design.
> **(b)** Examine the code below and identify type of cohesion and coupling with
> justification.
> ```java
> class Library {
>     void addBook()     {}
>     void issueBook()   {}
>     void generateBill(){}
> }
> class Member {
>     Library lib = new Library();
> }
> ```

**Part (a) — 3 marks.**

| | Cohesion | Coupling |
|---|---|---|
| **Scope** | **within** a single module | **between** two or more modules |
| **Measures** | how strongly a module's own elements are functionally related | the degree of interdependence between modules |
| **Desired** | **high** | **low** |
| **Effect if wrong** | a module with several jobs must change for several reasons | a change in one module forces changes in others |
| **Scale** | 7 levels, coincidental → functional | 6 levels, content → data |

**One-line differentiation:** *cohesion is intra-module and should be maximised;
coupling is inter-module and should be minimised.*

**Part (b) — 3 marks.**

**Cohesion of `Library`: logical cohesion (weak).**

Justification from the code: `addBook()` and `issueBook()` both operate on books
and belong together, but `generateBill()` is a **billing** operation — a different
concern. The three methods are related only by the *category* "things a library
does", while the functions they perform are significantly different. That is
precisely the deck's definition of logical cohesion: *"the elements are logically
related and not functionally… operations are related, but the functions are
significantly different."*

**Improvement:** split billing into its own `Billing` class, leaving `Library`
with book operations only — raising it toward functional cohesion.

**Coupling between `Member` and `Library`: data coupling by the deck's own
precedent; stamp coupling by stricter theory. Either way it is a *tight,
unnecessary* dependency.**

Justification from the code: `Member` contains `Library lib = new Library();` —
it **directly instantiates a concrete class**, so `Member` depends on `Library`'s
existence and constructor. `Library` cannot be substituted or mocked without
editing `Member`.

> [!warning] Two defensible answers — know both, and why
> **The deck answers this exact pattern.** Slides 5-6 pose:
> ```java
> class Volume { public static void main(String args[]) {
>     Box b = new Box(5,5,5);
>     System.out.println(b.volume); } }
> class Box { public int volume; Box(int l,int w,int h){ this.volume = l*w*h; } }
> ```
> and print: *"The above code exhibits **data coupling**… the Volume class
> creates an instance of the Box class and accesses its volume variable
> directly… the Volume class is sharing data with the Box class through the
> volume variable."*
>
> **That is the same structure as B2(b)**, so by rule 8 the expected answer is
> **data coupling**.
>
> **But the deck's reasoning is questionable by standard theory.** Data coupling
> is defined — on the deck's *own* slide 2 — as modules that "communicate by
> passing **only data**" as parameters. Reading a public field of another object
> is not parameter passing; holding a whole `Library` object when only some of it
> is needed is closer to **stamp coupling**, and directly touching another
> class's public data is arguably a step toward **content coupling**.
>
> **What to write:** name **data coupling** (following your course's own
> worked example), and add one sentence noting that the dependency is on the
> concrete class and could be reduced by passing the object in or programming to
> an interface. That earns the mark under the deck's answer while showing you
> understand the scale. If you prefer stamp coupling, justify it explicitly by
> "a whole object is held where only part is needed" — a justified answer should
> score either way.

**Improvement:** inject the dependency — pass a `Library` (or an interface) into
`Member` rather than constructing one inside it.

*(No printed solution key exists for this paper, so this answer is unchecked —
no `✓`. The disagreement with the deck's printed reasoning is recorded above, as
rule 8 requires.)*


## Question Bank

**PYQ questions — 1.**

> **[[se-ete-2025-26]] Q B2 (6 marks, CO3)** — define and differentiate cohesion
> and coupling; then identify both types in the `Library` / `Member` snippet with
> justification.

Worked in full in subtopic 3. Short form: (a) cohesion is intra-module and should
be high, coupling is inter-module and should be low. (b) **Logical cohesion** —
`generateBill()` is a different concern from `addBook()`/`issueBook()`;
**data coupling** per the deck's own worked precedent — `Member` instantiates a
concrete `Library`. *(Unchecked; deck reasoning disputed, see subtopic 3.)*

**Deck questions — 4**, all from
`raw/sources/ppts/2025/L9 Coupling and Cohesion.pptx`:

1. **Slides 5-6, the `Volume` / `Box` snippet** — B2(b)'s structure with different
   classes. Printed answer: data coupling. Reproduced and examined in subtopic 3.
2. **Slides 13-14, the `Multiply` class** — "what type of cohesion?" Printed
   answer: **functional cohesion**, because `mul()` performs a single task and its
   variables serve only that task. The slide also gives the low-cohesion
   counter-example: a class that multiplies two numbers *and* creates a pop-up
   window to display the result — fixed by splitting into `Multiply` and
   `Display`.
3. **Slides 7-9, the three-coupling Java program** — stamp (acceptable), common
   (avoid), content (avoid); stamp is best of the three.
4. **Slides 17-19, the three-cohesion Java program** — coincidental
   (`printMessage` + `addNumbers` + `displayTime`, unrelated, worst), logical
   (`performOperation` with a `switch` on `choice`, acceptable but not ideal),
   sequential (`getSquare` feeding `printSquare`, best of the three).

All four carry printed analyses in the deck. None is `✓`-checked against an
independent key.

**Textbook questions — the design chapter is present but its exercises were not
extracted.** `L8 Chapter 5 Software Design_3.pdf` is Aggarwal & Singh chapter 5;
Pressman 8e is not in the vault.

## Mistakes & Traps

- **Reversing the directions.** Cohesion **high**, coupling **low**. Getting this
  backwards invalidates the whole answer.
- **Labelling without justifying.** B2 says *with justification*. Quote the line
  that causes your classification.
- **Confusing logical with coincidental cohesion.** Logical = same category,
  different functions. Coincidental = no relationship at all.
- **Confusing stamp with data coupling.** Stamp passes a **whole structure** and
  involves **tramp data**; data passes only what is needed.
- **Calling control coupling always bad.** It is bad when the flag selects
  unrelated behaviour, good when it enables reuse.
- **Answering only one of the two types.** B2(b) asks for cohesion **and**
  coupling.

## Course Material

- `raw/sources/ppts/2025/L9 Coupling and Cohesion.pptx` — the main source and one
  of the richest decks in the vault. All six coupling types and all seven cohesion
  types with definitions and examples; the `Volume`/`Box` coupling question with
  its printed answer; the `Multiply` cohesion question with its printed answer;
  the low-cohesion pop-up counter-example; a full Java program demonstrating
  stamp, common and content coupling with an analysis and a verdict; another
  demonstrating coincidental, logical and sequential cohesion likewise; and the
  `Calculator`/`Display` high-cohesion-low-coupling model answer.
- `raw/sources/ppts/2025/L8 Chapter 5 Software Design_3.pdf` — Aggarwal & Singh
  chapter 5, covering modularity and functional independence alongside the design
  concepts on [[Design Concepts & Principles]].

**Deck disagreement recorded** (rule 8): the deck classifies direct field access
on an instantiated object as **data coupling**, which conflicts with its own
definition of data coupling as communication by parameter passing. Recorded in
subtopic 3 with both readings and guidance on what to write.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] ·
previous [[Design Concepts & Principles]] · next [[Software Architecture]]
