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

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Systems Concept (Open vs Closed Systems)
> - SDLC Phases & Software Process Models (Waterfall, Spiral, Agile, Prototyping)
> - Feasibility Study (TELOS Framework)
> - SSADM: Data Flow Diagrams (DFD Context & Level 1)
> - System Testing Types & Deployment Strategies

---
## 1. Systems Concept

A **System** is a collection of interrelated components working together towards a common goal by accepting inputs, processing them, and producing outputs within a boundary.
- **Open System**: Interacts with its environment (exchanges info/energy; e.g., Information System).
- **Closed System**: Isolated from its environment.

---
## 2. Systems Development Life Cycle (SDLC)

SDLC consists of sequential/iterative phases:
1. **Identification / Planning**: System request, defining scope.
2. **Analysis**: Feasibility study, requirement gathering, DFD modeling.
3. **Design**: Architectural design, database schema, UI design, algorithm design.
4. **Development / Coding**: Software encoding in programming languages.
5. **Testing**: Verifying correctness and removing bugs.
6. **Implementation / Deployment**: Installing system, user training, data conversion.
7. **Maintenance**: Corrective, Adaptive, Perfective maintenance.

---
## 3. SDLC Software Models

- **Waterfall Model**: Linear sequential model. Easy to manage, but inflexible to requirement changes.
- **Prototyping Model**: Builds a quick prototype for user feedback. Ideal when requirements are unclear.
- **Spiral Model**: Iterative model focusing heavily on **Risk Analysis**. Suitable for large, high-risk projects.
- **Agile Model**: Iterative & incremental development delivering functional software in short sprints. Highly adaptable.

---
## 4. Feasibility Study (TELOS Framework)

Before developing a system, a **Feasibility Study** evaluates whether the project should proceed:
- **T - Technical Feasibility**: Is required technology and expertise available?
- **E - Economic Feasibility**: Is cost-benefit ratio favorable (ROI, financial viability)?
- **L - Legal Feasibility**: Does system comply with laws, regulations, and copyright?
- **O - Operational Feasibility**: Will users accept and operate the system effectively?
- **S - Schedule Feasibility**: Can system be completed within target timeframe?

---
## 5. DFD & SSADM Structured Modeling

> [!INFO] Deep Dive Note
> For DFD symbols (Gane & Sarson), Context Diagram rules, Level 1 DFD decomposition, and Data Dictionary, read: [[Subtopics/System Analysis DFD & ER Modeling|DFD & ER Modeling Guide]].

---
## 6. System Testing & Deployment Strategies

### System Testing Levels:
- **Unit Testing**: Testing individual modules/functions.
- **Integration Testing**: Testing interactions between combined modules.
- **System Testing**: Testing the complete integrated system against functional requirements.
- **Acceptance Testing**:
  - **Alpha Testing**: Conducted by internal test team at developer site.
  - **Beta Testing**: Conducted by real end-users in real operating environment.

### Deployment Strategies:
- **Direct Changeover**: Immediately replaces old system with new system (High risk, lowest cost).
- **Parallel Running**: Runs old and new systems simultaneously (Lowest risk, expensive).
- **Pilot Implementation**: Deploys system in one department/branch first; expands after success.
- **Phased Implementation**: Deploys system module by module gradually.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is an Open System? :: A system that interacts with its external environment by exchanging inputs, outputs, and feedback.
<!--SR:!2026-08-03,3,250-->

What does the acronym TELOS stand for in Feasibility Studies? :: Technical, Economic, Legal, Operational, Schedule feasibility.

What is the main characteristic of the Spiral SDLC model? :: High emphasis on risk analysis and iterative development cycles.
<!--SR:!2026-08-03,3,250-->

What is the difference between Alpha Testing and Beta Testing? :: Alpha testing is conducted by developers/testers at the developer's site; Beta testing is performed by actual end-users in their real operational environment.

What is Direct Changeover deployment, and what is its major risk? :: Stopping the old system completely and immediately switching to the new system; high risk if the new system fails as there is no backup.

What is Parallel Running deployment? :: Operating the old system and new system simultaneously for a period until the new system is proven reliable.
<!--SR:!2026-08-04,4,270-->