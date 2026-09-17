---
title: DFD & ER Diagram Modeling Guide
subject: AL ICT
subtopic: Systems Analysis & Design
tags:
  - AL-ICT
  - Subtopic
  - DFD
  - ERD
  - SSADM
---
# :LiAreaChart: Subtopic: DFD & ER Diagram Modeling Guide

> [!ABSTRACT] Core Focus
> Gane & Sarson DFD symbols, Context Diagram rules, Level 1 DFD decomposition, ER Diagram symbols, cardinalities, and converting ERD into relational tables.

---
## 1. Data Flow Diagram (DFD) Symbols (Gane & Sarson)

- **External Entity (Square / Rectangle)**: Source or destination of data outside system boundary (e.g., `Customer`, `Bank`).
- **Process (Rounded Rectangle / Circle)**: Transforms incoming data flow into outgoing data flow. Must contain a process number and verb phrase (e.g., `1.0 Calculate Total Bill`).
- **Data Store (Open-ended Rectangle)**: Repository where data is stored at rest (e.g., `D1 Customer File`).
- **Data Flow (Arrow)**: Represents data in motion labeled with noun phrase (e.g., `Payment Details`).

---
## 2. Rules for Constructing Valid DFDs

> [!CAUTION] Critical DFD Rules tested in A/L Exams
> 1. **No direct flow between External Entities**: Entity $\rightarrow$ Entity is **FORBIDDEN**. Must go through a Process.
> 2. **No direct flow between Entity and Data Store**: Entity $\rightarrow$ Data Store is **FORBIDDEN**. Must go through a Process.
> 3. **No direct flow between Data Stores**: Store $\rightarrow$ Store is **FORBIDDEN**.
> 4. **Process input/output requirement**: A Process must have **at least one input flow AND at least one output flow**.
>    - Process with input only = *Black Hole* (Invalid).
>    - Process with output only = *Miracle* (Invalid).

---
## 3. Entity-Relationship (ER) Diagram Symbols

- **Entity (Rectangle)**: Real-world object/concept (e.g., `Student`, `Course`).
- **Relationship (Diamond)**: Association between entities (e.g., `Enrolls`).
- **Attribute (Oval)**: Property of an entity.
  - **Key Attribute**: Underlined text (Primary Key).
  - **Multivalued Attribute**: Double oval (e.g., `Phone_Number`).
  - **Composite Attribute**: Sub-branches (e.g., `Name` $\rightarrow$ `First_Name`, `Last_Name`).
  - **Derived Attribute**: Dashed oval (e.g., `Age` calculated from `DOB`).

---
## 4. Converting ER Diagram to Relational Schema

1. **Strong Entity**: Converts into a relation; Key attribute becomes Primary Key.
2. **1:1 Relationship**: Place Primary Key of one entity as Foreign Key in the other.
3. **1:N Relationship**: Place Primary Key of the "1" side as **Foreign Key in the "N" side** relation.
4. **M:N Relationship**: Create a **Junction / Composite Relation**. Its Primary Key is a composite of the PKs of both participating entities.

> [!INFO] Not-Syllabus Deep Dive
> For Enhanced / Extended ER concepts (Specialization, Generalization, Inheritance Constraints, Aggregation, Composition), read: [[Extended & Enhanced ER (EER) Modeling|Extended & Enhanced ER Modeling]]