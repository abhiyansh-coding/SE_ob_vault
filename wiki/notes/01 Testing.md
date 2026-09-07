---
marks: 20
of: 80
asked: C1 (10 marks) · C2 (10 marks)
lectures: 35-43, 45
---

# 01 · Testing

**Before this:** nothing. Testing is the one topic in this course you can start
cold. You need to know what a *program* is and that programs are built out of
smaller pieces — that's all.

---

## Where you are

The course so far has been about *building*: work out what the customer wants,
design a structure, write the code. Lectures 1–34. At the end of it you have a
system that compiles and runs.

**And you have no idea whether it works.**

That's the situation this topic exists for, and it is a genuinely hard one. You
ran the program a few times, it gave the right answer, and that tells you almost
nothing — you tried maybe five inputs out of billions. Somewhere in there is an
input that breaks it. Testing is the discipline of **finding that input on
purpose, before a customer finds it by accident.**

Everything below is one of two things: a **strategy for choosing which few inputs
to try** (§3, §4), or a **strategy for organising the search** (§5–§8).

**It is also 20 of the 80 marks — the biggest topic on the paper**, and both
questions are Section C long answers. C1 gives you a program and asks you to
*draw*. C2 gives you a spec and asks you to *design test cases*. Neither can be
bluffed, and neither is recall.

---

## 1 · What "testing" actually means

Start with the obvious idea and watch it fail.

You've written a program. You want to be confident it's correct. So you run it on
some inputs and check the answers come out right. Every test passes. **What have
you learned?**

Very little — because you chose inputs you expected to work. You've confirmed the
program does what you already believed it did. The bugs are, by definition, in the
cases you didn't think of.

This is why the deck opens by listing three natural-sounding definitions **and
rejecting all three**:

- ~~Testing demonstrates that errors are **not** present.~~
- ~~Testing shows a program performs its intended functions correctly.~~
- ~~Testing establishes confidence that a program does what it is supposed to do.~~

> **The one it accepts:** *"Testing is the process of executing a program with
> the intent of finding errors."*

**Not proving it works — trying to break it.** That inversion is the practical
content of the definition, because it changes what you do. Testing a licence
system that accepts ages 18 to 60, the "confidence" mindset tries 25, 40, 33. The
"find errors" mindset goes straight for **17, 18, 60, 61** — and that instinct is
literally the answer to question C2.

**A test that passes taught you almost nothing. A test that fails just paid for
itself.**

Two consequences the deck draws out:

- **Developers shouldn't be the only ones testing their own code.** It is hard to
  attack something you just built and believe in. Most organisations separate the
  two roles and staff them differently.
- **Find defects early.** The later a defect is found, the more expensive it is to
  remove — a requirements mistake caught at the requirements stage is a
  conversation; caught after release it is a recall. This single fact justifies
  reviews, inspections and unit testing all at once, and it's also the argument
  question B3 wants over in [[02 Process Models]].

### The three words for "something went wrong"

When a program misbehaves, three different things happened at three different
times, and the exam expects you to tell them apart.

Follow one bug through its life:

1. A developer misreads the spec and writes `>` where they meant `>=`. **That
   human act is an *error*** — "mistake" is the exact synonym. It happened in a
   person's head, at 4pm on a Tuesday.
2. That error leaves something behind in the code: the wrong character, sitting
   on line 40. **That is a *fault*** — and **"defect" is the standard synonym**. A
   fault is the *representation* of an error, so faults live in artefacts, not
   just code: a wrong arrow on a DFD is a fault, so is a wrong sentence in a
   requirements document.
3. Months later somebody enters exactly 18, line 40 executes, and the system
   rejects a valid applicant. **That is a *failure*** — the inability of a system
   to perform a required function.

> **error → fault → failure.** A person makes an error, which leaves a fault,
> which causes a failure **only when executed**.

**That last clause is why testing is hard.** A fault sitting in a branch nobody
ever takes produces no failure and is invisible. You are hunting for something
that only reveals itself if you happen to run the right line.

*("Bug" is the informal word for a mistake made while coding — the deck treats it
as a kind of error, not a fourth category.)*

### What a "test case" is, precisely

You'll be asked to *design test cases*, so it's worth being exact about what one
is. It is **not** just an input.

| | |
|---|---|
| **Test scenario** | *what* is to be tested — the situation, broadly |
| **Test case** | one condition run with **known inputs** and a **predefined expected output**. Input description **+** expected output description |
| **Test suite** | a set of test cases |

**The expected output is half of it, and it must be written before you run
anything.** Otherwise you'll run the program, see 61 rejected, and record "61 →
rejected, pass" — which proves nothing, because you'd have written down whatever
it did.

The deck's **test case template** enforces this by splitting the form in two:

| Filled in **before** execution | Filled in **after** |
|---|---|
| Purpose · Pre-condition · **Inputs** · **Expected outputs** · Post-conditions · Written by · Date | Execution history · **Result** · If it fails, possible reason · Observations · Suggestions · Run by · Date |

*In C2, a table of ages with no expected-output column is a half-answer.*

*(Tools the deck names for managing these: **JIRA**, **Mantis**.)*

### Verification and validation

Here is a failure mode that testing-by-running cannot catch. You build exactly
what the specification says. Every test passes. You deliver it, and the customer
says *"that's not what I wanted."*

Nothing was wrong with your code. Something was wrong with the **spec**, and no
amount of executing the program will reveal that. So checking software has to
happen along two independent axes:

| | **Verification** | **Validation** |
|---|---|---|
| Asks | *Are we building the product **right**?* | *Are we building the **right** product?* |
| Against | the specification | the user's actual need |
| How | reviews, meetings, checklists, walkthroughs, inspections | **executing** the software |
| Code runs? | **no** — static | **yes** — dynamic |
| When | throughout, during each phase | **after** verification |

> **Testing = Verification + Validation.**

**Which is which is a standing trap, so anchor it on the word.** *Verify* = check
against a written reference (the spec). *Validate* = check against reality (the
need). A system can pass verification perfectly and still be the wrong system.

### Who does the final test, and where

At the end, someone other than you has to try it. Three named arrangements,
distinguished by **who runs it, where, and whether you're standing there**:

| | Run by | Where | Developer present? |
|---|---|---|---|
| **Acceptance** | the **customer / end user** | on the customer's terms | — |
| **Alpha** | in-house QA and test teams (sometimes potential users) | **your site**, controlled conditions | yes |
| **Beta** | real customers / end users | **their site**, real conditions you can't control | **no** |

- **Acceptance testing** applies when software is built **for one specific
  customer** — a series of tests letting them confirm all their requirements are
  met. It can range from ad-hoc to a planned systematic series.
- **Alpha** is the last testing done in-house, after acceptance testing and before
  the software goes out for beta.
- **Beta's whole value is the loss of control** — real hardware, real data, real
  misuse. Three kinds: *traditional* (released to the target market, data gathered
  and used for improvement) · *public* (released openly online to anyone — the
  deck's example is Microsoft's Windows 8 beta, the largest ever run) ·
  *technical* (released to an internal group, feedback gathered from employees).

---

## 2 · Why you can't just test everything

The obvious solution to "which inputs do I try?" is *all of them*. Watch it die.

> Take a program with **two 8-bit integer inputs**. The combinations are
> 2⁸ × 2⁸ = 65,536. At one second per test that is **18 hours** — for the most
> trivial program imaginable.

And real programs take more than two inputs, wider than 8 bits, and must also be
tested on every **invalid** input, of which there are more still.

> **Exhaustive testing is not merely expensive. It is impossible.**

**This is the fact the entire topic is built on.** You will run maybe a few dozen
tests. There are billions of possible inputs. So testing is a **sampling problem**:
which few inputs are most likely to expose a fault?

There are exactly two ways to answer, depending on **what you're allowed to look
at** — and they are the two halves of this topic and of the exam paper:

| | **Black box** (functional) | **White box** (structural) |
|---|---|---|
| You look at | the **specification** — the promised inputs and outputs | the **code** — its internal structure |
| So you hunt for | places the spec has edges and categories | paths through the code nothing has run |
| Need the source? | no | yes |
| On the paper | **C2, 10 marks** | **C1, 10 marks** |

**They catch different things, which is why you do both.** Black box cannot tell
you a branch was never executed. White box cannot tell you a requirement was never
implemented at all — there's no code to look at.

---

## 3 · Black box testing — 10 marks (C2)

**The situation:** you have the specification and nothing else. "Ages 18 to 60 are
eligible." That's it. Where do you point your handful of tests?

Three techniques, each a different theory of where faults hide.

### 3.1 Boundary Value Analysis — the paper's question

**Think about how the mistake actually gets made.** Nobody writes code that fails
for age 34. The faults programmers really produce are:

- `if (age > 18)` where they meant `>=` — rejects 18-year-olds
- a loop stopping one iteration early
- an array sized one element short

**Every one of those misbehaves only at the edge of the range.** Test at 34 and
all of them pass. So: **faults cluster at boundaries**, and that is the whole
premise.

**The method.** For a variable ranging over [a, b], test **five** values:

> **min · min⁺ · nominal · max⁻ · max** — that is `a`, `a+1`, a typical middle
> value, `b−1`, `b`.

*"Nominal" just means an ordinary, unremarkable value from the middle — 39 for our
age range. It's there as a control: if the nominal case fails too, the bug isn't
about boundaries at all.*

**Now: what if there are several inputs?** Vary them all together and you're back
to the combinatorial explosion of §2. BVA escapes it with an assumption borrowed
from reliability theory:

> **The single fault assumption:** failures are rarely the result of two or more
> faults occurring *simultaneously*.

If that's true, you never need two variables at extremes at the same time. So:

> **Hold every variable at its nominal value except one; let that one take its
> extreme values. Repeat for each variable in turn.**

Count it: each of the *n* variables contributes 4 extreme cases (min, min⁺, max⁻,
max), and the all-nominal case is shared by all of them. **4n + 1.**

**Two variants change one decision each:**

- **Robustness testing** — BVA only ever uses *legal* values, so it never checks
  that bad input is rejected. Robustness adds **just below min** and **just above
  max**, where the expected output is an error message. Six values per variable:
  **6n + 1**.
- **Worst-case testing** — *rejects* the single fault assumption and lets every
  variable take all five values at once. That's the full Cartesian product: **5ⁿ**.
  Far more thorough, far more expensive, and **BVA's cases are a proper subset of
  it**.

| Technique | The assumption it makes | Cases | *n*=1 | *n*=2 | *n*=3 |
|---|---|---|---|---|---|
| **BVA** | single fault; valid inputs only | **4n + 1** | 5 | 9 | 13 |
| **Robustness** | single fault; adds invalid inputs | **6n + 1** | 7 | 13 | 19 |
| **Worst case** | no single-fault assumption | **5ⁿ** | 5 | 25 | **125** |

#### Worked — the paper's C2, 6 + 2 + 2 = 10 marks

> **[[se-ete-2025-26]] C2.** A driving licence system, valid age **18 to 60
> inclusive**. (a) Design the BVA test cases. (b) Explain how BVA catches
> boundary defects. (c) Explain how BVA handles multiple input variables.

**(a) — 6 marks.** One input variable, so *n* = 1 and BVA gives **4(1) + 1 = 5**
test cases. Range [18, 60], nominal 39.

| TC | Age | Boundary value | Expected output |
|---|---|---|---|
| 1 | **18** | min | Eligible |
| 2 | **19** | min⁺ | Eligible |
| 3 | 39 | nominal | Eligible |
| 4 | **59** | max⁻ | Eligible |
| 5 | **60** | max | Eligible |

**Then add the robustness cases.** A licence system's real job is to *reject*
people, and notice that all five BVA cases expect "Eligible" — pure BVA never
tests a rejection once. **6(1) + 1 = 7:**

| TC | Age | Value | Expected output |
|---|---|---|---|
| 6 | **17** | just below min | **Not eligible** — error message |
| 7 | **61** | just above max | **Not eligible** — error message |

*State the formula, state n, then table it with the expected-output column. Adding
the robustness pair with one sentence of justification is what separates a full
answer from a competent one.*

**(b) — 2 marks.** Because **defects cluster at boundaries**, and the commonest
coding fault is the off-by-one — `age > 18` written for `age >= 18`, or `age < 60`
for `age <= 60`. Such a fault is **invisible everywhere except at the boundary**:
a test at 39 passes under either version, so it can never distinguish them.
Testing **18 and 17, 60 and 61** places one value on each side of every decision,
so a misplaced comparison operator changes the observed result and the fault is
forced into the open.

**(c) — 2 marks.** Through the **single fault assumption** — failures rarely
result from two or more faults occurring simultaneously. BVA therefore **varies
one variable at a time while holding all others at their nominal values**, and
repeats for each variable in turn. For *n* variables this gives **4n + 1** test
cases instead of the 5ⁿ that varying them together would require. If the
single-fault assumption is rejected — every variable at an extreme simultaneously
— you get **worst-case testing** at **5ⁿ** cases: more thorough, far costlier.

#### The deck's running example — the quadratic equation

Almost every worked example in the deck uses one program, so expect it in some
form. Inputs a, b, c ∈ [0, 100]; outputs *Not a quadratic equation* (a = 0),
*Real roots* (b²−4ac > 0), *Imaginary roots* (b²−4ac < 0), *Equal roots*
(b²−4ac = 0).

Three variables → **13** BVA cases, **19** robust, **125** worst case. Five of the
13, nominal = 50:

| TC | a | b | c | Expected |
|---|---|---|---|---|
| 1 | **0** | 50 | 50 | Not quadratic |
| 2 | **1** | 50 | 50 | Real roots |
| 3 | 50 | 50 | 50 | Imaginary roots |
| 9 | 50 | **100** | 50 | Equal roots |
| 10 | 50 | 50 | **0** | Real roots |

**Compute each expected output; never guess it.** TC 9 is *equal* roots only
because 100² − 4(50)(50) = 10000 − 10000 = 0 exactly.

### 3.2 Equivalence class testing

**BVA's blind spot:** it tests edges obsessively and the vast interior barely at
all. And there's an opposite observation to exploit — **if 200 and 201 run through
exactly the same code, testing both is wasted effort.**

So partition the input domain into **classes whose members are interchangeable**,
and test **one representative from each**.

**Two steps:**

1. **Identify the classes.** Take each input condition and split it into **valid**
   and **invalid** classes. *"1 to 999"* yields one valid class `[1 ≤ item ≤ 999]`
   and two invalid ones, `item < 1` and `item > 999`.
2. **Generate the cases.** Cover all the valid classes, then write **one test case
   per invalid class, never combining two invalid values in one test.** Otherwise
   one invalid input can **mask** another: enter age −5 *and* name blank, get one
   error message, and you've no idea whether the second check exists at all.

**Do it on the output domain too, not just the input** — the deck is explicit
about this. For the quadratic program:

- **Output classes** — 4 cases, one per possible result: not quadratic / real /
  imaginary / equal.
- **Input classes** — a = 0, a < 0, 1 ≤ a ≤ 100, a > 100, and likewise for b and
  c: 10 cases, of which two turn out redundant.

**On the licence spec:** valid `18 ≤ age ≤ 60` → one case (35); `age < 18` → one
case (10); `age > 60` → one case (75). **Three cases against BVA's five** —
cheaper, and it never once touches a boundary. **That's why you run both:** they
are blind in opposite directions.

### 3.3 Decision table testing

**A third blind spot:** both techniques above vary one input at a time. Some
requirements are about **combinations** — "the user gets in only if the ID is
valid *and* the password is valid" — and the bug is a combination nobody
considered.

A **decision table** lays out every combination in a grid, so a missed one is
visible rather than merely forgotten. It's also called a **cause-effect table**.

**Four quadrants:** the **condition stub** (top left — the conditions) and
**condition entries** (top right, **one column per rule**); the **action stub**
(bottom left) and **action entries** (bottom right, where an **X** marks the
action taken).

> **Each column is one rule, and one rule is one test case.**

Deck example — a login page. Two conditions (User ID, Password), each Blank /
Invalid / Valid; two actions. 3 × 3 = 9 rules:

| | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|
| **User ID** | B | B | B | I | I | I | V | V | **V** |
| **Password** | B | I | V | B | I | V | B | I | **V** |
| Login succeeds | | | | | | | | | **X** |
| "Invalid credentials" | X | X | X | X | X | X | X | X | |

**Then collapse it.** Rules 1–8 all produce the identical action, so one
representative from each equivalent group is enough — the deck reduces nine rules
to three test cases. **The collapse is where the marks are;** building the raw
grid is mechanical.

**Two refinements worth showing:**

- **`--` means "don't care".** In the deck's triangle problem, if *"are x, y, z
  the sides of a triangle?"* is **N**, nothing else matters and the rest of the
  column is `--`. That's a second way to shrink the table.
- **An "Impossible" action row.** Some combinations contradict themselves —
  x = y and x = z but y ≠ z. Marking those *impossible* rather than inventing an
  output shows you're reading the logic, not filling in boxes.

---

## 4 · White box testing — 10 marks (C1)

**Now the situation changes: you can see the code.** That makes a different
question available, and it's the one black box can never ask —

> **Which parts of this program has my testing never executed at all?**

A fault in a line you never ran cannot possibly have shown up. So instead of
reasoning about inputs, reason about **the code's structure** and make sure the
tests reach all of it. Hence the name **structural testing**.

C1 is one exercise in three parts, and each part feeds the next: draw the
structure, count the paths through it, then list them.

### 4.1 Drawing the code as a graph

To talk about "paths through a program" you first need a picture of its shape,
with everything irrelevant stripped out. That picture is the **control flow
graph** — a **directed graph** where **nodes are statements or fragments of
statements** and **edges are the flow of control** from one to the next.

**The four rules for drawing one:**

1. **Sequential statements collapse into a single node.** Ten assignments in a row
   with no branching have exactly one way through, so they carry no information
   about paths. This is what keeps the graph small.
2. **Every `if`, `while`, `for` or `case` becomes a decision node** — a node with
   **two or more edges leaving it**. These are also called **predicate nodes**
   (a *predicate* is just a statement that asks a true/false question).
3. **Where branches rejoin, their edges merge into one node.**
4. **One entry node, one exit node.** Every node reachable from the entry, and the
   exit reachable from every node.

**The DD-path graph** (decision-to-decision) squeezes it further: each sequential
run becomes a single lettered node so only decisions and merges survive. The deck
maps a 39-node quadratic-equation flow graph down to 19 lettered nodes — *"nodes 1
to 10 → A, sequential"*, *"node 11 → B, decision node"*, *"node 16 → F, two edges
are combined here"*.

#### Worked — the paper's C1, 3 + 3 + 4 = 10 marks

> **[[se-ete-2025-26]] C1.** A 21-line program that finds the **largest of three
> numbers**. (a) Draw the control flow graph. (b) Compute the cyclomatic
> complexity. (c) List all independent paths.

*The paper's exact listing isn't in this vault. Below is the standard form of that
program; the method transfers line for line, and only the node count depends on
the listing you're handed.*

```c
1   main() {
2     int a, b, c;
3     scanf("%d %d %d", &a, &b, &c);   ─┐ node 1   (lines 2-3, sequential)
4     if (a > b)                        ─  node 2   ← decision
5     {
6       if (a > c)                      ─  node 3   ← decision
7         printf("a is largest");       ─  node 4
8       else
9         printf("c is largest");       ─  node 5
10    }
11    else
12    {
13      if (b > c)                      ─  node 6   ← decision
14        printf("b is largest");       ─  node 7
15      else
16        printf("c is largest");       ─  node 8
17    }
18  }                                   ─  node 9   ← exit
```

**How those nodes were chosen:** lines 2–3 run straight through, so they collapse
to one node (rule 1). Each of the three `if`s gets its own node (rule 2). Each
`printf` is a separate node because control arrives at it from only one branch.
All four branches rejoin at the closing brace, so that merge is the exit (rules 3
and 4).

**(a) — 3 marks.** Nine nodes, eleven edges:

```
                    ( 1 )  read a, b, c
                      |
                    ( 2 )  a > b ?
                   /       \
             true /         \ false
                 /           \
            ( 3 ) a > c ?    ( 6 ) b > c ?
            /     \           /      \
       true/       \false true/        \false
          /         \       /          \
      ( 4 )       ( 5 )  ( 7 )        ( 8 )
      "a"         "c"    "b"          "c"
          \         |      |         /
           \        |      |        /
            ------( 9 ) exit -------
```

**Label every node and mark true/false on every branch.** An unlabelled graph
earns close to nothing, and part (c) is literally unanswerable without the labels.

**(b) — 3 marks.** How many tests would be enough here? The graph answers it. The
measure is **cyclomatic complexity, V(G)**, and there are three ways to compute
it — they always agree, so computing two checks your own drawing:

| Method | Working | V(G) |
|---|---|---|
| **e − n + 2P** | e = 11 edges, n = 9 nodes, P = 1 → 11 − 9 + 2 | **4** |
| **π + 1** | π = 3 decision nodes (2, 3, 6) → 3 + 1 | **4** |
| **Regions** | 3 enclosed areas + 1 unbounded area outside | **4** |

**Show at least two.** If e − n + 2 and π + 1 disagree, you have miscounted an
edge — that's the check, and it's free.

*A **region** is any area completely enclosed by edges when the graph is drawn
flat with no crossings, **plus** the infinite area outside the whole graph. Here:
the loop 3-4-9-5, the loop 6-7-9-8, the big area between the two branches, and the
outside.*

**(c) — 4 marks.** **V(G) = 4, so there are exactly 4 independent paths.** Write
that sentence down — it shows (b) and (c) are the same fact, which is the point of
the question.

| Path | Nodes | Conditions | Test case (a, b, c) | Output |
|---|---|---|---|---|
| P1 | 1-2-3-4-9 | a>b, a>c | (9, 5, 3) | a is largest |
| P2 | 1-2-3-5-9 | a>b, a≤c | (9, 5, 12) | c is largest |
| P3 | 1-2-6-7-9 | a≤b, b>c | (5, 9, 3) | b is largest |
| P4 | 1-2-6-8-9 | a≤b, b≤c | (5, 9, 12) | c is largest |

**Give a test case per path if there's room.** That turns a graph exercise into an
actual test suite, which is the entire purpose — the technique is called **basis
path testing** precisely because the independent paths form a *basis* you build
your tests from.

### 4.2 Cyclomatic complexity, properly

**McCabe's metric.** Memorise all three forms:

$$V(G) = e - n + 2P \qquad V(G) = \pi + 1 \qquad V(G) = \text{number of regions}$$

- **e** = edges · **n** = nodes · **π** = number of **predicate (decision)
  nodes** · **P** = number of **connected components** — how many separate,
  unjoined graphs you have drawn.
- **P = 1 for a single program**, and that's the case you'll almost always be in.
  P exceeds 1 only when you measure a *collection*: the deck's example is a main
  program M calling subroutines A and B, drawn as three disconnected graphs, where
  V(M ∪ A ∪ B) = 13 − 13 + 2×3 = **6** — and this equals V(M) + V(A) + V(B).
  **The complexity of a collection is the sum of its parts.**

**Six properties, as the deck lists them:**

1. V(G) ≥ 1, always.
2. **V(G) is the maximum number of independent paths in G.** ← the one that matters
3. Inserting or deleting **functional** statements does not change V(G).
4. V(G) = 1 **if and only if** G has only one path.
5. Inserting a new edge increases V(G) by one.
6. **V(G) depends only on the decision structure of G.**

**Properties 3 and 6 are the same insight twice: only branching costs
complexity.** A hundred sequential assignments add nothing, because they add no
new way through.

**What the number is for.** Two things: it **bounds the testing effort** (that
many paths to cover), and it **flags unmaintainable modules** — above roughly 10,
a module is generally judged too complex and due for splitting.

### 4.3 Graph matrices

Drawing graphs by hand doesn't scale, and a tool can't read a drawing. So
represent the same graph as a table a program can process.

A **graph matrix** is a **square matrix with one row and one column per node** —
so its size is the number of nodes. An entry in row *i*, column *j* means **there
is an edge from node *i* to node *j***.

- Put the **edge's name** in the cell (or just **1**); leave it blank if there's
  no connection.
- A **connection matrix** uses only 1 and 0.
- **Parallel edges are both recorded** — the deck notes a case where the matrix
  shows two separate paths `ab` and `cd` from node 1 to node 2.
- **The cell value can carry a weight**: probability of taking that link,
  processing time, memory used. The matrix then supports analyses beyond path
  counting.

*Lecture 40, never yet examined — but a 2-mark definition is cheap to carry.*

### 4.4 Data flow testing

> **"It has nothing to do with data flow diagrams."** The deck says so in as many
> words, because the names collide and the confusion is the trap. DFDs are a
> *requirements* notation ([[04 Modeling]]); this is a code-level test technique.

**A different structural question.** So far we've asked which *paths* go untested.
Now ask it of **variables**: between the line where a variable gets its value and
the line where that value is used, what happens to it?

| Term | Meaning |
|---|---|
| **DEF(v, n)** — defining node | node n where variable v's **value is set** |
| **USE(v, n)** — usage node | node n where v's value is **read**. It's a **predicate use (p)** if n is a predicate statement, otherwise a **computation use (c)** |
| **du-path** | a path from a **DEF** of v to a **USE** of v |
| **dc-path** | a du-path with **no other definition of v anywhere in between** — "definition clear" |

**Why the dc distinction matters:** if a du-path is *not* definition-clear, the
value being used is not the one you set — something overwrote it on the way.
**Those are the potential trouble spots**, and they are what you write tests for.

**The method:** draw the flow graph → build the DD-path graph → list DEF and USE
nodes for every variable → enumerate every du-path → **flag those that are not
definition-clear.**

**Three anomalies worth naming:** a variable **defined but never used** · **used
but never defined** · **defined twice before being used**.

### 4.5 Mutation testing

There's one question none of the above answers: **how good is my test suite?**
Coverage says which lines ran, not whether a test would have *noticed* a fault
there.

So deliberately plant faults and see if the tests catch them. Make many copies of
the program, each with one small alteration — each copy is a **mutant**. Run the
suite: a mutant that some test case detects is **killed**. **A good suite kills
them all.**

- **First-order mutant** = one change to one expression; a second-order mutant is a
  mutation of a first-order one. Only low-order mutants are practical.
- **Equivalent mutants** can't be killed by anything — e.g. a change inside dead
  code no input can reach. They're excluded from the score rather than counted as
  failures.
- **Mutation score** = killed / (total − equivalent) × 100%.

> [!warning] Deck content, outside the lecture plan
> Lectures 35–43 don't name mutation testing. It's in the deck, so it's cheap
> insurance — but don't spend real revision time here.

---

## 5 · Levels of testing

**A practical problem the techniques above ignore.** You have a system of forty
modules. Do you assemble all forty, run it, and start hunting? If something fails
you have forty suspects and no way to narrow them down.

So you test the way you built: **pieces first, then combinations, then the
whole.** The deck's framing:

> **Testing in the small** = unit testing. **Testing in the large** = integration
> and system testing.

*(A **module** here means one self-contained unit of code — a function, a class, a
file. Modules and how to choose them are the subject of [[06 Design]].)*

### Unit testing

Take **one module and run it in isolation** with prepared test cases, comparing
actual results against those predicted by the specification and design.

- The **most 'micro'** scale of testing. Needs knowledge of internal design and
  code, so its method is **white box** and it is **done by programmers, not
  testers**.
- **Why isolation pays:** a single module is small enough to locate a fault
  easily, and it eliminates the confusing interaction of several faults in
  different parts of the software at once.

**But a module doesn't run on its own.** It expects to be called by something, and
it calls other things that may not be written yet. So you fake both ends:

| | What it is | Stands in for |
|---|---|---|
| **Driver** | a "main program" that accepts test data, passes it to the module, prints the results | the module's **caller** — what's **above** it |
| **Stub** | a dummy standing in for a subordinate module, returning canned values | the modules it **calls** — what's **below** it |

> **Top-down integration needs stubs; bottom-up integration needs drivers.**

That follows directly: start at the top and the things *below* you don't exist
yet, so you stub them. Start at the bottom and the thing *above* you doesn't exist
yet, so you write a driver. **This is the most likely 2-marker in the section.**

### Integration testing

Every module passes its own unit tests. Assemble them and it still breaks —
because unit testing never tested the **joins**. Integration testing does exactly
that: it **verifies the interfaces between modules**.

Modules are combined in an order fixed by an **integration plan**, and the
partially-assembled system is tested **after each step**, so that when something
breaks you know which addition broke it.

**Why unit testing isn't enough** — the deck's list:
- One module can adversely affect another.
- Sub-functions that work alone may not combine into the desired major function.
- Interfacing errors invisible to unit testing appear.
- **Timing problems** in real-time systems aren't detectable by unit testing.
- **Resource contention** problems aren't either.

| | **Top-down** | **Bottom-up** |
|---|---|---|
| Starts from | the **main control module** | the **atomic modules** (lowest level) |
| Moves | downward through the control hierarchy, depth-first or breadth-first | upward, combining modules into **clusters** (also called *builds*) |
| Needs | **stubs** | **drivers**, removed as real modules arrive |
| You get early | a working skeleton of the whole system | thoroughly tested low-level modules |

Three terms live in this family because each one is a response to *"we just
changed the software"*:

- **Regression testing** — *"a full or partial selection of already executed test
  cases which are re-executed to ensure that changes have not propagated
  unintended side effects."* Every integration step creates new data flow paths
  and invokes new control logic, so things that worked can silently stop working.
  **Automate it when changes are frequent**, or the cost escalates: the deck names
  **Selenium** (open source, browser-based) and **QTP / HP Quick Test
  Professional** (VBScript, data-driven, keyword-based).
- **Smoke testing** — also *Build Verification Testing* or *Confidence Testing*.
  Covers **most of the major functions but none of them in depth**, purely to
  decide whether this build is worth testing at all. **Pass → carry on; fail →
  halt and demand a new build.** Cheap gate, run early.
- **Sanity testing** — after a build containing a few small fixes, check the
  reported bugs really are fixed and nothing previously working has broken. **A
  narrow substitute for a full regression run** when a full one isn't worth it.

### System testing

Now the whole thing is assembled, and the question changes again: not "do the
pieces join up?" but **"does this system meet its requirements?"** Run by the
development team and users, **after** integration testing.

It's really a family of different tests:

| Test | Checks |
|---|---|
| **Functional** | the system against its functional requirements/specifications |
| **Recovery** | how well it recovers from crashes and hardware failures |
| **Security** | that data and resources are protected from intruders |
| **Performance** | compliance with stated performance requirements |
| **Load** | behaviour under heavy load — at what load does response degrade or fail |
| **Stress** | behaviour under *unusually* heavy loads, heavy repetition, huge input values, complex queries |

**Stress vs load** — the deck notes the terms are often used interchangeably. If
forced to separate them: *load* asks "how much can it take?", *stress* asks "what
happens beyond that?"

**Exploratory / ad-hoc testing** — informal, no formal test plan or test cases;
testers learn the software as they go. The opposite pole from everything above,
and it still finds things.

---

## 6 · Static testing — finding faults without running anything

Everything so far requires **executing** the program, which means the code must
exist and be runnable. But a fault is in the code the moment it's typed — and by
§1, the earlier you find it the cheaper it is.

**Static testing tests the software without executing it** — checking syntax,
coding standards, code optimisation. It is the **verification** half of V&V, and
it's mostly people reading things.

Four kinds, and the axis is **formality**:

| Type | Formality | Led by | What it's for |
|---|---|---|---|
| **Informal review** | none | anyone | early-stage comments; a two-person team suffices; the goal is to help the author improve the document |
| **Walkthrough** | informal | **the author** | **the author explains the work product to the team**; participants ask questions; a scribe records comments. Run after the code compiles clean, to find **algorithmic and logical** errors |
| **Technical review** | semi-formal | peers | checks technical documents — test strategy, test plan, requirement specs — against standards |
| **Inspection** | **formal** | a **trained moderator** | strict defined process; **reviewers work from a checklist**; defects recorded and returned for rectification |

> **Walkthrough vs inspection is the examinable pair: author-led and informal
> versus moderator-led, checklist-driven and formal.**

**The formal review's six steps:** planning → kick-off → preparation → review
meeting → rework → follow-up.

**What a code inspection checklist hunts for** — all classic oversight bugs:
uninitialised variables · jumps into loops · non-terminating loops · array indices
out of bounds · mismatches between actual and formal parameters. The deck's
checklist is grouped as **data handling** (correct initialisation of variables,
arrays, pointers, counters, flags, strings; subscripts in bounds and in the right
order; valid pointer references; strings free of off-by-one errors) and **control
flow** (correct subroutines called in the correct order; every loop terminates;
loop counts correct; every loop reachable).

*Static testing tool named: **Jtest**.*

---

## 7 · Debugging

**A test just failed.** That tells you *something* is wrong and where the symptom
surfaced. It does not tell you what is wrong, or where. Closing that gap is
**debugging** — and it is a different activity from testing, which is why it gets
its own lecture.

**Why it's genuinely hard** — Pressman's characteristics of bugs:

- **The symptom and the cause may be geographically remote.** The symptom appears
  in one part of the program, the cause sits in another. **Highly coupled
  structures make this much worse** — which is the real payoff of [[06 Design]]:
  low coupling is a debugging argument, not an aesthetic preference.
- The symptom may **disappear temporarily** when some *other* error is corrected.
- The symptom may be caused by a **non-error** — a round-off inaccuracy.
- The symptom may be caused by **human error that isn't easily traced**.
- The symptom may result from **timing** problems rather than processing ones.
- Input conditions may be **hard to reproduce** exactly — real-time systems where
  input ordering is indeterminate.
- The symptom may be **intermittent**, especially in embedded systems where
  hardware and software are inextricably coupled.

**Two approaches, and they run in opposite directions:**

| | **Induction** — specific → general | **Deduction** — general → specific |
|---|---|---|
| 1 | **Locate** the pertinent data | **Enumerate** all possible causes or hypotheses |
| 2 | **Organise** the data | **Use the data to eliminate** possible causes |
| 3 | **Devise** a hypothesis | **Refine** the remaining hypothesis |
| 4 | **Prove** the hypothesis | **Prove** the remaining hypothesis |

**Induction starts from the evidence and builds a theory. Deduction starts from
every theory and eliminates.** Note both end at *prove the hypothesis* — never
"apply the fix". A fix applied to an unproven hypothesis is exactly how the second
bug characteristic above happens: the symptom vanishes and the fault doesn't.

---

## 8 · Tools, and knowing when to stop

**Two broad categories of testing tool: static and dynamic** — the same split as
§6 versus everything else. The deck's eight types:

| Tool | Does |
|---|---|
| **Static analyser** | examines programs systematically and automatically |
| **Code inspector** | checks programs meet minimum quality standards |
| **Standards enforcer** | imposes rules on the developer |
| **Coverage analyser** | measures the extent of coverage |
| **Output comparator** | determines whether a program's output is appropriate |
| **Test file / data generator** | sets up test inputs |
| **Test harness** | simplifies test operations |
| **Test archiving system** | provides documentation about programs |

*Named tools across the deck: **Jtest** (static) · **Selenium**, **QTP**
(regression) · **JIRA**, **Mantis** (test case management).*

**And the "when do I stop" measure.** Since exhaustive testing is impossible (§2),
you need some quantity that says how much of the program your tests actually
touched:

$$\text{Test coverage \%} = \frac{\text{lines of code executed by all test cases}}{\text{total lines of code}} \times 100$$

*50 lines executed out of 500 → **10%** coverage.* Crude — it counts lines run, not
whether running them would have revealed a fault, which is precisely the gap §4.5
exists to fill.

---

## The cram card

Everything below is taught above. This is the compressed form, for the last ten
minutes.

**The six that carry 20 marks**

1. *"Testing is the process of executing a program with the intent of finding
   errors."* — trying to break it, not to confirm it.
2. **Exhaustive testing is impossible** (2 × 8-bit inputs = 18 hours). Everything
   else is a strategy for sampling.
3. **BVA 4n+1 · robustness 6n+1 · worst case 5ⁿ.**
4. **V(G) = e − n + 2P = π + 1 = regions.** Compute two; they must agree.
5. **V(G) = the number of independent paths.** That links C1(b) to C1(c).
6. **Verification** = building it right (static, vs the spec). **Validation** =
   building the right thing (dynamic, vs the need). **Testing = V + V.**

| Ask | Answer |
|---|---|
| error / fault / failure | human mistake / its trace in the artefact (= defect) / what happens when the fault executes |
| a test case is | inputs **+ expected output**, both written before running |
| alpha / beta | in-house, controlled, developer present / customer's site, uncontrolled, developer absent |
| BVA's five values | min · min⁺ · nominal · max⁻ · max |
| BVA's assumption | **single fault** — vary one variable, hold the rest nominal |
| robustness adds | just below min, just above max — the **invalid** cases |
| worst case | rejects the single-fault assumption → 5ⁿ |
| equivalence classes | one representative per class; **never two invalid values in one test** (masking) |
| decision table | one column = one rule = one test case; **collapse it** |
| CFG rules | sequential statements → one node; each `if` → a decision node; one entry, one exit |
| π | number of decision (predicate) nodes |
| P | number of connected components — **1** for a single program |
| a region | an area enclosed by edges, **plus** the unbounded outside |
| stubs vs drivers | stub = fake **callee** (top-down) · driver = fake **caller** (bottom-up) |
| smoke testing | major functions, no depth — decides if the build is worth testing |
| walkthrough vs inspection | author-led, informal / **moderator**-led, **checklist**, formal |
| debugging: induction | data → organise → hypothesis → prove |
| debugging: deduction | all causes → eliminate → refine → prove |
| test coverage % | lines executed ÷ total lines × 100 |

**The three highest-value habits in the exam:** state the formula and *n* before
tabling BVA cases · compute V(G) two ways so the drawing checks itself · put an
expected-output column on every test case table.

---

## Sources

- `raw/sources/ppts/2025/L11 Software Testing_5.pdf` — **the whole topic.** It is
  Aggarwal & Singh chapter 8, and it carries everything above: the four
  definitions, the terminology, V&V, alpha/beta, the three levels, BVA /
  robustness / worst case with the quadratic-equation examples worked in full (13,
  19 and all 125 cases printed), equivalence classes, decision tables, the CFG and
  DD-path graph, all three V(G) methods, graph matrices, data flow testing,
  mutation testing, the static review types, debugging, and the tool list.
- `raw/sources/ppts/2025/Flowdiagram Ques.pdf` — **misnamed; not DFD content.**
  Aggarwal & Singh pp. 416-422: **two worked control-flow-graph / DD-path /
  independent-path problems** — direct C1 drill. Image-only, so open it by eye.
- `raw/sources/ppts/2025/Estimation of Test Coverage Metrics and Structural
  Complexity.docx` — the coverage formula only.
- **Not in the vault:** Pressman 8e.

**One gap, stated rather than papered over:** the deck teaches everything through
the quadratic-equation program, but the exam's C1 used *largest of three numbers*
and this vault doesn't hold the paper's actual 21-line listing. The CFG in §4.1 is
reconstructed from the standard form of that program. The method is identical; the
node count depends on the exact listing you're given.
