# Syllabus

**Scope, and only scope.** What this course covers, from
[[se-handout-2026-muj]] and nothing else (rule 1). What any of it is *worth*
lives on [[weightage]]; why it exists lives on [[story]]. The three are
deliberately separate pages.

## The course

| | |
|---|---|
| Course | Software Engineering |
| Code | **CSE3102** |
| Programme | B.Tech, III Year / V Semester |
| LTPC | 3 1 0 4 |
| Session | 2026-2027 |
| Coordinators | Dr. Akshay Jadhav, Dr. Susheela Vishnoi |
| Lectures | **53** |
| Textbook | R. Pressman, *Software Engineering: A Practitioner's Approach*, 8e, McGraw Hill, 2019 |

## Assessment

| Component | | Marks |
|---|---|---|
| **Mid-Term Examination** (close book) | | **30** |
| CWS | Attendance | 5 |
| | Assignments (2) | 10 |
| | Quizzes (3 × 10) | 15 |
| **End Term Exam** (close book) | | **40** |
| | **Total** | **100** |

75% attendance required to sit the End Semester examination.

> [!warning] Rule-1 override — the Mid-Term stops at lecture 32
> The handout's own *Mode of Assessing CO* column marks lectures **1-34** as
> Mid-Term assessable. The user has stated the Mid-Term syllabus is **lectures
> 1-32**, and that instruction **overrides the handout**.
>
> It is recorded here rather than applied silently because rule 1 names the
> handout as the authority on scope, and this departs from it. Two things
> support the override:
> - It lands on a clean seam. Lecture 32 is *Transform mapping: refining the
>   architectural design* — the last lecture of the Design block. Lecture 33
>   opens Construction.
> - What it drops is exactly the two Construction lectures, **33** (Development,
>   coding standards and conventions) and **34** (Programming styles, code
>   inspection, code review, walkthrough) — one coherent unit, not an arbitrary
>   cut.
>
> **Consequence worth knowing: CO3 leaves the Mid-Term entirely.** In lectures
> 1-34 the only CO3 lectures are 33 and 34. With the override, the MTE covers
> **CO1 (lectures 1-12) and CO2 (lectures 13-32)** and nothing else.

## Course outcomes

| CO | Statement | Bloom | Lectures |
|---|---|---|---|
| CSE3102.1 | Demonstrate an understanding of the fundamentals of software engineering principles, methodologies, and techniques | L2 Understand | 1-12 |
| CSE3102.2 | Illustrate software requirements analysis, SRS documents, software metrics, and system modeling | L2 Understand | 13-32 |
| CSE3102.3 | Develop software systems to meet specified requirements efficiently | L3 Apply | 33-34 |
| CSE3102.4 | Analyze test cases for software systems using various testing techniques | L4 Analyze | 35-45 |
| CSE3102.5 | Assess software quality, analyze evolutionary processes, and evaluate software security measures effectively | L5 Evaluate | 46-53 |

## The five modules

| # | Module | Topics as the handout words them |
|---|---|---|
| 1 | Introduction to Software Engineering | The Evolving Role of Software, The Changing Nature of Software, Legacy Software, Software Myths, Software Engineering as a Layered Technology, Process Framework, CMMI |
| 2 | Software Process Models & Agile Development | Specialized Process Models, Unified Process, Agile Process Models, Agile Principles, Adaptive Software Development |
| 3 | Software Engineering Practices & System Engineering | Communication Practice, Planning Practices, Modeling Practices, Construction Practice, Deployment, Computer-Based Systems, The System Engineering Hierarchy, Business Process Engineering, Product Engineering |
| 4 | Modeling, Analysis and Quality Management | Data Modeling Concepts, Object-Oriented Analysis, Flow-Oriented Modeling, Taxonomy of Quality Attributes, Perspectives of Quality, Quality System, SQA, Capability Maturity Model |
| 5 | Project Management & DevOps | Estimation and Project Planning Process, Software Scope and Feasibility, Human Resources, Empirical Estimation Models, Introduction to DevOps, Cloud Computing & Virtualization, Migration to DevOps, DevOps Tools |

> [!note] The modules are not the teaching order — the lecture plan is
> The five modules group the syllabus paragraph thematically; the 53-lecture
> plan is what actually happens in class, and the two do not line up. Module 4
> puts modeling and quality management together, but the lecture plan teaches
> modeling at 19-23 and quality at 46-48, twenty-five lectures apart. **The
> vault's topic folders follow the lecture plan**, because that is the order
> you will meet the material and the order the exam follows.

## The 53-lecture plan

Grouped as the vault's phase folders. **Bold rows are inside the Mid-Term
window** (lectures 1-32, per the override above).

| Lectures | Phase | Content |
|---|---|---|
| **1-3** | **Foundations** | Introduction; software and its emergence; evolving role, changing nature; legacy software, myths, software crisis |
| **4-5** | **Foundations** | Layered approach, generic approach, process framework; the process, software products, characteristics, applications |
| **6-7** | **Process Models** | Conventional: traditional Waterfall, prototype, RAD |
| **8** | **Process Models** | Evolutionary: incremental, spiral, component-based, unified process; comparison of models |
| **9-11** | **Process Models** | Agile view of process, human factors; XP, Adaptive Software Development, DSDM; Scrum, Crystal, FDD, Agile Modeling |
| **12** | **Process Models** | Software development life cycle; assessment model — CMMI |
| **13** | **Requirements** | Requirement engineering, types of requirements, SRS |
| **14** | **Requirements** | SE practice: elicitation, analysis, documentation, validation, management |
| **15** | **Project Planning** | Size estimation — LOC, Function Count method |
| **16** | **Project Planning** | Cost estimation, Halstead size estimation |
| **17** | **Project Planning** | Effort estimation — COCOMO model |
| **18** | **Project Planning** | Risk analysis and risk estimation |
| **19** | **Analysis Modeling** | Analysis modeling: data modeling, functional modeling and information flow, DFDs |
| **20** | **Analysis Modeling** | Behavioral modeling; mechanics of structured analysis; creating the ER diagram |
| **21** | **Analysis Modeling** | Data flow model, control flow model, control and process specification, data dictionary |
| **22** | **Analysis Modeling** | UML — class, object, sequence, use case diagrams |
| **23** | **Analysis Modeling** | Case study based on software design *(flipped classroom)* |
| **24** | **Design** | Design concepts and principles, the design process |
| **25** | **Design** | Design and software quality, design principles |
| **26** | **Design** | Abstraction, refinement, modularity |
| **27** | **Design** | Software architecture, control hierarchy, structural partitioning, data structure, software procedure, information hiding |
| **28** | **Design** | Effective modular design: functional independence, cohesion, coupling |
| **29** | **Design** | Data design: data modeling, data structures, databases, the data warehouse |
| **30** | **Design** | Analyzing alternative architectural designs, architectural complexity |
| **31** | **Design** | Mapping requirements into a software architecture; transform flow, transaction flow |
| **32** | **Design** | Transform mapping: refining the architectural design |
| 33 | Construction | Development, coding standards and conventions |
| 34 | Construction | Programming styles, code inspection, code review and walkthrough |
| 35 | Testing | Testing techniques and fundamentals (re-engineering, reverse engineering, restructuring, forward engineering) |
| 36 | Testing | Functional (black box): boundary value analysis |
| 37 | Testing | Equivalence class testing, decision-table-based testing |
| 38 | Testing | Structural (white box): path testing |
| 39 | Testing | Cyclomatic complexity |
| 40 | Testing | Graph matrices |
| 41 | Testing | Data flow testing |
| 42 | Testing | Unit, integration, system, validation testing; static and dynamic testing tools |
| 43 | Testing | Debugging techniques, approaches, tools |
| 44 | Quality & Maintenance | Software re-engineering, reverse engineering, restructuring, forward engineering |
| 45 | Testing | Case study based on software testing *(flipped classroom)* |
| 46 | Quality & Maintenance | Quality concepts, SQA, SQA activities, software reviews |
| 47 | Quality & Maintenance | Formal technical reviews, review reporting and guidelines, formal approaches to SQA |
| 48 | Quality & Maintenance | Statistical SQA; reliability and availability measures; ISO 9000 / ISO 9001 |
| 49 | Quality & Maintenance | Characteristics of software maintenance, maintenance process models |
| 50 | Quality & Maintenance | Case study on SQA and maintenance *(flipped classroom)* |
| 51 | DevOps | Introduction to DevOps |
| 52 | DevOps | Cloud computing and virtualization |
| 53 | DevOps | Migration to DevOps, DevOps tools |

**32 of 53 lectures are inside the Mid-Term window — 60% of the course.**

## Out of scope

Nothing has been ruled out yet. The handout's syllabus paragraph and lecture
plan agree closely, and no source has so far pushed past them. Two standing
watch-items:

- **Pressman 8e covers far more than this course** (rule 6). Formal methods,
  cleanroom engineering, web/mobile engineering, security engineering and the
  whole of Part 4 are in the book and not in this syllabus.
- **CO5 mentions "software security measures"** but no lecture in the 53-lecture
  plan teaches security. Recorded as a discrepancy in the handout itself, not as
  scope. Do not build a security topic on the strength of a CO statement.

## Material gaps

- **No textbook in `raw/sources/`.** Pressman 8e is the prescribed reference and
  is not in the vault, so rule 6's fallback is unavailable. Everything must come
  from the decks until it lands.
- **One deck is from this year's session** (`ppts/2026-27/`, UML & Use Case
  diagrams). The other 23 are from the 2025 session. Where they disagree, the
  2026-27 deck wins.
- **Five deck files are image-only** and five more are image-heavy — see
  [[index]]. Several sit on Mid-Term topics.
