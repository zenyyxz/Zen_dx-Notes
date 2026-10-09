---
title: Lesson 07 - System Analysis & Design
subject: AL ICT
unit: 07
competency: Explores the systems concept and uses systems analysis and design methodology in developing information systems
tags:
  - AL-ICT
  - Lesson-07
  - SDLC
  - SSADM
  - DFD
  - Feasibility
  - Testing
  - Flashcards
---
# :LiBook: Lesson 07: System Analysis & Design

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide 7.1-7.10)
> - 7.1 Systems concept + characteristics + classification
> - 7.2 Manmade information systems (OAS-TPS-MIS-DSS-ESS-GIS-KMS-CMS-ERPS-Smart)
> - 7.3 SDLC models (Waterfall/Spiral/Agile/Prototyping/RAD) + Structured/OO
> - 7.4 SSADM intro + stages covered
> - 7.5 Preliminary investigation + feasibility (Technical/Economic/Operational/Organizational)
> - 7.6 Analysis: requirements + BAM/DFD/EPD/LDS + BSO
> - 7.7 Logical + physical design (UI, tables, data dictionary)
> - 7.8 Build + test (white/black, unit/integration/system/acceptance)
> - 7.9 Deployment (parallel/direct/pilot/phase) + aftercare
> - 7.10 Off-the-shelf packages (gap analysis, mapping, reengineering)

---
## 1. Systems Concept (7.1)

A **System** is a collection of interrelated components working together towards a common goal by accepting inputs, processing them, and producing outputs within a boundary.

- Characteristics: boundary, inputs/outputs, processing, feedback, hierarchy of subsystems.
- **Open vs Closed**: open exchanges with environment (e.g. Information System); closed isolated.
- **Natural vs Manmade**: natural (river ecosystem) vs manmade (school system).
- **Living vs Physical**: living (organisms) vs physical (machines).

---
## 2. Manmade Information Systems (7.2)

Compare by objective + functionality:

- **OAS**: office automation (word processing, email).
- **TPS**: transaction processing (POS billing, ATM).
- **MIS**: management reports from TPS data.
- **DSS**: decision support with models/what-if.
- **ESS**: executive dashboards for seniors.
- **GIS**: geographic/mapped data.
- **KMS**: captures/shares knowledge.
- **CMS**: creates/manages web content.
- **ERPS**: integrates all resources (HR, stock, finance).
- **Smart systems**: sensor-driven automated (IoT).

---
## 3. SDLC Models + SSADM (7.3-7.4)

### SDLC (Waterfall stages):
Planning -> Analysis -> Design -> Development -> Testing -> Implementation -> Maintenance.

### Models:
- **Waterfall**: linear sequential. Easy to manage, inflexible to change.
- **Prototyping**: quick prototype for feedback. Best when requirements unclear.
- **Spiral**: iterative + **Risk Analysis** each loop. Best for large/high-risk.
- **Agile**: short sprints, working software fast. Highly adaptable.
- **RAD**: rapid app dev with reusable components/tools.

### Methodologies:
- **Structured**: process/data-driven (DFD, ER). Syllabus focus via SSADM.
- **Object-Oriented**: class/object-driven (UML).

**SSADM** = Structured Systems Analysis and Design Methodology. Covers analysis + logical/physical design stages of SDLC (not coding/testing directly).

---
## 4. Preliminary Investigation + Feasibility (7.5)

### Preliminary investigation tasks:
1. Identify problems in current system.
2. Suggest alternative solutions.
3. Prioritize information-system needs.

### Feasibility (TG = 4 types):
- **Technical**: technology + expertise available?
- **Economic**: cost-benefit favourable?
- **Operational**: users will accept/operate it?
- **Organizational**: fits org structure/policies?

> [!WARNING] TELOS vs TG
> Industry uses TELOS (+Legal +Schedule). NIE 7.5 lists only the 4 above. Write the 4 on paper; mention Legal/Schedule only if asked as extra.

---
## 5. Analysis: Requirements + Tools + BSO (7.6)

### Requirement analysis:
- **Functional**: what system does (e.g. calculate bill).
- **Non-functional**: how well (speed, security, usability). IEEE: requirements must be unambiguous, verifiable, traceable.

### Analytical tools:
- **BAM (Business Activity Model)**: high-level activities of the business.
- **DFM**: Data Flow Modeling — **Context diagram** (whole system as one process + entities), **Level 1 DFD** (decompose into sub-processes + data stores), **Document flow diagram** (paper flow before computerisation).
- **EPD (Elementary Process Description)**: text/pseudocode for each lowest-level process.
- **LDM/LDS**: Logical Data Modeling — entities/attributes/relationships without physical detail.

### BSO (Business System Options):
Propose several system options -> compare cost/benefit/risk -> select most appropriate.

> [!INFO] Deep Dive Note
> For DFD symbols (Gane & Sarson), Context rules, Level 1 decomposition, EPD writing, LDS, and Data Dictionary, read: [[Subtopics/System Analysis DFD & ER Modeling|DFD & ER Modeling Guide]].

---
## 6. Design: Logical + Physical (7.7)

- **Logical DFDs** for proposed system (from EPDs up to context).
- **EPD in pseudocode** for each elementary process.
- **UI design**: input screens, outputs, navigation.
- **Logical Data Structure (LDS)** for proposed system.
- **Physical DB design**: tables + record specs (field/type/size/key), **data dictionary** (metadata catalogue), database construction.

---
## 7. Build + Test (7.8)

- **Program development** (coding) + **Database development**.
- **Test cases**: planned inputs + expected outputs.
- **White box**: tests internal logic/code paths.
- **Black box**: tests inputs/outputs without seeing code.
- **Unit**: single module. **Integrated**: combined modules. **System**: whole system vs requirements. **Acceptance**: user accepts (alpha internal / beta real users).

---
## 8. Deployment + Aftercare (7.9)

- **Parallel**: old + new run together (safest, costly).
- **Direct**: instant cutover (cheapest, riskiest).
- **Pilot**: one branch/department first, then expand.
- **Phase**: module-by-module gradual rollout.
- Aftercare: hardware/software install, **data migration**, **user training**, review, support, maintenance (corrective/adaptive/perfective).

---
## 9. Off-the-Shelf Packages (7.10)

- **Pros**: cheaper/faster, tried, supported. **Cons**: misfit, customization cost, vendor dependence.
- Steps: identify package capabilities/workflows -> **gap analysis** (business need vs package) -> **mapping** (activities onto package flow) -> **reengineering** (change business process) or **customization** (change package).
- Compare investment/operational/maintenance cost vs custom build.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Name 3 classifications of systems with examples. :: Open/closed, natural/manmade, living/physical; e.g. open IS vs closed lab experiment.

What is the difference between TPS, MIS, and DSS? :: TPS records transactions; MIS reports from TPS for managers; DSS models/what-if for decisions.

What is the main characteristic of the Spiral SDLC model? :: High emphasis on risk analysis and iterative development cycles.

When to use Prototyping vs Spiral? :: Prototyping when requirements unclear; Spiral for large high-risk projects.

What does SSADM cover? :: Structured analysis + logical/physical design stages (not coding/testing).

What are the 3 preliminary investigation tasks? :: Identify current problems, suggest alternatives, prioritize needs.

What are the 4 NIE feasibility types? :: Technical, Economic, Operational, Organizational (Legal/Schedule are TELOS extras, not TG 7.5).

Distinguish functional vs non-functional requirements. :: Functional = what it does; non-functional = how well (speed/security/usability).

What tools draw in 7.6? :: BAM, context/Level 1 DFD, document flow, EPD, LDS; then propose/select BSO.

What must every DFD process have? :: At least one input AND one output flow (else black hole/miracle).

What is an EPD and data dictionary? :: EPD = pseudocode for each elementary process; dictionary = metadata catalogue of tables/fields.

White box vs black box? :: White tests internal code paths; black tests inputs/outputs without code.

Name 4 tests in order. :: Unit -> integrated -> system -> acceptance (alpha internal, beta real users).

What is Direct Changeover deployment, and what is its major risk? :: Stopping the old system completely and immediately switching to the new system; high risk if the new system fails as there is no backup.

What is Parallel Running deployment? :: Operating the old system and new system simultaneously for a period until the new system is proven reliable.

Pilot vs phased deployment? :: Pilot = one site first then expand; phased = module-by-module rollout.

What is gap analysis for off-the-shelf? :: Compare business process needs vs package features to find misfits, then reengineer process or customize package.
