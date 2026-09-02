---
phase: Analysis Modeling
topic: Data Modeling & ERD
lectures: 19-20
co: CSE3102.2
asked_as: []
mte: true
studied: false
status: not-started
pyq_marks: 0
assignment_qs: 1
attempts: 0
last_practiced: null
---

# Data Modeling & ERD

- **The first of three modeling lenses.** Requirements written in prose are
  ambiguous; redrawn as a diagram with rules, **the ambiguity becomes a missing
  arrow**.
- **This one asks: what does the system remember?** — entities, their attributes,
  and the relationships between them.
- The other two: [[Flow-Oriented Modeling & DFD]] asks what the system *does*;
  [[UML & Use Case Modeling]] asks what *objects* exist.

**Prerequisites:** [[Software Engineering Practice]]
**Asked as:** — — **0 marks** on the one paper · **1** in [[se-assign-1-2026]]

**The thread:** ask what the system must remember (1) — then how those things relate, which is two questions students merge (2) — and the diagram is the deliverable, graded on notation as much as content (3).

> [!warning] Never asked — on one paper, which is nearly no evidence
> A single paper cannot show a topic is unexamined. In syllabus, taught across
> two lectures, and **it is a drawing topic on a paper that put 20 of 80 marks
> on drawings**. Lectures 19-20 is *syllabus depth*; rule 3 forbids reading it
> as marks.

## 1 · Entities, attributes and keys

**Data object / entity** — something the system needs to store information about.
**Attribute** — a named property of an entity. **Relationship** — a named
association between entities.

- **Start by asking what the system has to remember.** A university remembers
  students and courses; a hotel remembers rooms and reservations.
- Each of those is an **entity type**; the facts kept about each — name, address,
  phone number — are its **attributes**.
- **One attribute (or a combination) must tell two instances apart**, or the
  system cannot refer to anything reliably. That is the key.

**Terms and distinctions.** An **attribute** is a property or characteristic
of an entity that is *of interest to the organisation* — the qualifier matters,
because it is what stops the model growing without limit.

A **candidate key** uniquely identifies each instance. When there are several, one
is chosen as the **identifier**. In the deck's STUDENT example, Student_ID is the
candidate key and becomes the identifier, with Name, Address and Phone_No as
ordinary attributes.

## 2 · Relationships — degree and cardinality

- **Two different questions get asked about the same line on a diagram**, and
  students routinely answer one when asked the other.
- **Degree** — how many *entity types* the relationship connects: one, two or
  three boxes.
- **Cardinality** — for a given relationship, how many *instances* of one side
  attach to each instance of the other.
- **They vary independently:** a unary relationship (one entity type related to
  itself) can still be one-to-many — an employee manages many employees. That is
  exactly why they need separate names.

**Terms and distinctions.** The degree table, the three binary cardinality
examples:

**Degree of relationship**

The **number of entity types that participate** in the relationship.

| Degree | Entity types | Deck's example |
|---|---|---|
| **Unary** (recursive) | 1 | PERSON *is married to* PERSON — one-to-one; EMPLOYEE *manages* EMPLOYEE — one-to-many |
| **Binary** | 2 | the ordinary case — see below |
| **Ternary** | 3 | VENDOR *ships* PART *to* WAREHOUSE |

**Binary relationships by cardinality — the deck's three examples

| Cardinality | Example | Reading |
|---|---|---|
| **One-to-one** | EMPLOYEE *is assigned* PARKING PLACE | each employee has one place, each place has one employee |
| **One-to-many** | PRODUCT LINE *contains* PRODUCT | a line has many products, a product belongs to one line |
| **Many-to-many** | STUDENT *registers for* COURSE | a student takes many courses, a course has many students |

A fourth, from the training example: EMPLOYEE *completes* COURSE — many-to-many,
because each employee may complete more than one course and each course may be
completed by more than one employee.

**Cardinality and optionality**

**Cardinality** of a relationship is *the number of instances of entity B that can
be associated with each instance of entity A*.

**Minimum cardinality** is the *minimum* number of instances of B that may be
associated with each instance of A. If it is **zero**, B is an **optional
participant**.

> Deck example: MOVIE *is stocked as* VIDEO TAPE. The minimum number of tapes
> available for a movie is zero, so **VIDEO TAPE is an optional participant** in
> the *is-stocked-as* relationship.

**Keys**

| Term | Definition |
|---|---|
| **Candidate key** | an attribute, or combination of attributes, that uniquely identifies each instance of an entity type |
| **Identifier** | the candidate key chosen to be *the* unique characteristic for that entity type |

Deck example: STUDENT has attributes Student_ID, Name, Address, Phone_No.
**Student_ID is the candidate key**, and is chosen as the identifier.

**Minimum cardinality** is the subtlety worth carrying. Ordinary cardinality says
how many *can* be associated; minimum cardinality says how few *may* be. When the
minimum is zero the participation is **optional** — a movie may be stocked as zero
tapes, so VIDEO TAPE optionally participates. In an exam this is the difference
between drawing "must have exactly one" and "may have none", and it is the detail
that separates a careful diagram from an approximate one.

**Worked example.** The deck works several small ones:

> **Deck** — "A training department is interested in tracking which training
> courses each of its employees has completed."

EMPLOYEE —*completes*— COURSE, **many-to-many**: each employee may complete more
than one course, and each course may be completed by more than one employee.

> **Deck** — "Vendors quote prices for several parts along with quantity of
> parts. Draw an E-R diagram."

VENDOR —*quote-price*— PARTS, with **quantity** as an attribute of the
relationship (it belongs to the pairing, not to either entity alone). Cardinality
is many-to-many: a vendor quotes for several parts, and a part may be quoted by
several vendors.

## 3 · Drawing the ER diagram

- **The diagram is the deliverable**, and in this subject it is graded on notation
  as much as on content.
- Get the shapes right, **underline the identifier**, and put a cardinality marker
  at **both** ends of every relationship line.

**Legend.**

Read this before drawing anything — an unlabelled ER diagram scores near zero.

| Symbol | Means |
|---|---|
| Rectangle | entity type |
| Diamond | relationship |
| Ellipse | attribute |
| Underlined attribute | identifier / key |
| Line | participation in the relationship |
| **1** / **M** / **N** on a line | cardinality at that end |

**Label both ends of every relationship.** Cardinality is a property of each
direction separately, and a one-to-many drawn without the 1 and the M is
indistinguishable from a many-to-many.

*(In one line: rectangle for entity, diamond
for relationship, ellipse for attribute, underline for identifier, 1/M/N for
cardinality. State which convention you are using if there is any doubt.

**The diagram.** Mermaid's `erDiagram` renders the structure faithfully, though
exam answers are drawn in the classic rectangle-diamond-ellipse notation. The
deck's hotel example, reconstructed:

```mermaid
erDiagram
    GUEST ||--o{ RESERVATION : makes
    ROOM  ||--o{ RESERVATION : "is booked in"
    GUEST {
        int  Guest_ID PK
        string Name
        string Phone_No
    }
    ROOM {
        int  Room_No PK
        string Type
        float Rate
    }
    RESERVATION {
        int  Reservation_ID PK
        date Check_in
        date Check_out
    }
```

**Reading.** A GUEST makes zero or more RESERVATIONs; a ROOM is booked in zero or
more RESERVATIONs. Each reservation belongs to exactly one guest and one room —
so RESERVATION resolves what would otherwise be a many-to-many between GUEST and
ROOM. **The rule it must satisfy:** every relationship carries a cardinality at
both ends, and every entity carries exactly one underlined identifier.

> [!note] Source honesty
> The deck's ER example is captioned *"ER Diagram → Hotel Reservation System"*
> but **the diagram itself is an image** with no extractable text. The structure
> above is a faithful reconstruction of a standard hotel reservation ERD, **not a
> transcription of your instructor's slide.** Open
> `L6 Requirement Analysis Diagrams.pdf` by eye to compare before relying on the
> specific entities and attributes.

## How it's asked

Generic skeleton on [[answer-patterns]] §4. **Zero marks on the paper — one
assignment question ([[se-assign-1-2026]] Q5(c), a 12-entity clinic ERD).**

### Draw & label — the archetype to prepare

- **Spot it:** *"Draft an ERD (entities, keys, relationships) for…"* — usually
  with the entities listed for you, which makes it a **notation** test rather than
  a modelling one.
- **Skeleton:**
  1. **Legend** — which notation: crow's foot or Chen. State it.
  2. **An entity table** — entity · **primary key** · attributes · foreign keys.
     This earns marks the diagram alone does not, and it is fast to write.
  3. **The diagram**, with **cardinality at both ends of every relationship**.
  4. **Reading** — what it asserts, plus the validity rule: **every many-to-many
     resolved into an associative entity**, every identifier underlined.
- **Earns the marks:** cardinality markers and keys. **An unlabelled ERD is worth
  close to zero.**
- **Trap:** drawing a direct many-to-many. Resolve it through the entity that
  already exists in the domain (patient↔provider resolves through *appointment*).
- **Second trap:** answering *degree* when asked *cardinality*. Degree counts how
  many **entity types** a relationship connects; cardinality counts **instances**
  per side. They vary independently — see section 2.

**Never asked as:** `numerical`, `explain`, `scenario`. `compare` is plausible for
*degree vs cardinality*.
**Also worth knowing, though never asked:**
- The **candidate key vs identifier** distinction is the plausible 2-marker here.
- **The drawing skill transfers.** [[UML & Use Case Modeling]] carries a 10-mark
  drawing in Section D, which establishes that this instructor asks for diagrams
  at long-answer length — even though ER was not the notation tested.

## Quick Reference

> [!abstract] The ten-minute recall card
> Everything here is taught in full above.

| Ask | Answer |
|---|---|
| **Degree** | how many **entity types** a relationship connects — unary, binary, ternary |
| **Cardinality** | how many **instances** of one side attach to each of the other |
| They vary | **independently** — a unary relationship can still be one-to-many |
| Three binary cardinalities | 1:1 · 1:M · M:N |
| **Identifier** | the candidate key actually chosen, **underlined** in the diagram |
| Minimum cardinality | whether participation is optional (0) or mandatory (1) |
| M:N must be | **resolved into an associative entity** |
| Notation | rectangle = entity · diamond = relationship · ellipse = attribute · underline = identifier |

**The rule that makes an ERD correct:** cardinality at **both** ends of every
relationship line, every identifier underlined, no unresolved many-to-many.

**An unlabelled ERD is worth close to zero.**

## Practice

**PYQ questions — none.** No question on [[se-ete-2025-26]] tests this topic.

**Deck questions — 2 small ones**, both from
`raw/sources/ppts/2025/L5 Chapter 3 Software Requirements_2.pdf`, both worked in
subtopic 2:

1. Training department tracking which courses each employee has completed →
   EMPLOYEE *completes* COURSE, many-to-many.
2. "Vendors quote prices for several parts along with quantity of parts. Draw an
   E-R diagram." → VENDOR *quote-price* PARTS, many-to-many, quantity as a
   relationship attribute.

Neither carries a printed solution beyond the diagram itself, so neither is
`✓`-checked.

**Textbook questions — unavailable for this topic.** Pressman 8e is not in
`raw/sources/`. The two Aggarwal & Singh chapters present in the vault cover
project planning and design.

> [!warning] The obvious question source turned out to be something else
> `Flowdiagram Ques.pdf` was catalogued at ingest as a DFD/ER question sheet on
> the strength of its filename. **It is not.** Read by eye on 2026-09-02, it is
> Aggarwal & Singh chapter 8, *Software Testing*, pages 416-422 — two worked
> control-flow-graph problems. Its content belongs to [[White-Box Testing]] and
> [[Cyclomatic Complexity & Graph Matrices]]. **This topic has no question sheet.**

**Assignment questions — [[se-assign-1-2026]].** **Q5(c)** ERD for a Clinic Management System — 12 entities with keys and cardinality

Worked in full on that page, with method and traps. **Coursework, so it does not
change [[weightage]]** — but it is direct evidence of what the instructor
considers important.

## Traps

- **Confusing degree with cardinality.** Degree counts entity *types*;
  cardinality counts *instances*. A unary relationship can be one-to-many.
- **Labelling only one end of a relationship.** Cardinality is per direction.
- **Forgetting optional participation.** Minimum cardinality zero is a real and
  examinable distinction, not a detail.
- **Not underlining the identifier.** It is how the diagram says which attribute
  is the key.
- **Attaching a relationship's attribute to an entity.** *Quantity* in the vendor
  example belongs to the *quote-price* relationship, not to VENDOR or PARTS.
- **Leaving a many-to-many unresolved when the model needs data about the
  pairing.** If the association itself has attributes, it needs its own box.

## Sources

- `raw/sources/ppts/2025/L5 Chapter 3 Software Requirements_2.pdf` — the main
  source. Degree of relationship with unary, binary and ternary examples; the
  three binary cardinality cases; cardinality, minimum cardinality and optional
  participation with the MOVIE / VIDEO TAPE example; attributes; candidate keys
  and identifiers with the STUDENT example; and the vendor/parts exercise.
- `raw/sources/ppts/2025/L6 Requirement Analysis Diagrams.pdf` — captions an ER
  diagram for a **Hotel Reservation System**, plus data dictionary, decision
  table and state transition diagram material. **Image-heavy: the diagrams
  themselves have no extractable text.** Worth opening by eye.

**Related:** [[story]] · [[syllabus]] · [[weightage]] · [[MTE Roadmap]] ·
previous [[Risk Analysis & Estimation]] · next [[Flow-Oriented Modeling & DFD]]
