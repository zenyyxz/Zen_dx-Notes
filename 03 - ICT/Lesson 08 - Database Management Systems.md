---
title: Lesson 08 - Database Management Systems
subject: AL ICT
unit: 08
competency: Designs and develops database systems to manage data efficiently and effectively
tags:
  - AL-ICT
  - Lesson-08
  - Database
  - RelationalModel
  - Normalization
  - SQL
  - Flashcards
---
# :LiBook: Lesson 08: Database Management Systems

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - File-based systems vs DBMS advantages
> - Relational Model Terminology (Relation, Tuple, Attribute, Keys)
> - ER Modeling & Transformation to Logical Schema
> - Database Normalization (1NF, 2NF, 3NF)
> - SQL: DDL (CREATE, ALTER, DROP) & DML (SELECT, INSERT, UPDATE, DELETE, JOINs)

> [!INFO] Extra / Not-Syllabus Deep Dive
> For Enhanced / Extended ER (EER) concepts (Specialization, Generalization, Inheritance, Aggregation, Composition), see: [[Subtopics/Extended & Enhanced ER (EER) Modeling|Extended & Enhanced ER (EER) Modeling]]

---
## 1. File-Based Systems vs. DBMS

| File-Based System Drawbacks                   | DBMS Advantages                                                 |
| :-------------------------------------------- | :-------------------------------------------------------------- |
| Data Redundancy & Inconsistency               | Centralized data control eliminates redundancy.                 |
| Data Isolation & Difficulty in accessing data | Shared multi-user data access with query languages (SQL).       |
| Integrity & Security Problems                 | Enforces Referential Integrity and Access Security permissions. |
| Atomicity & Concurrency issues                | ACID properties ensure crash recovery and transaction safety.   |

---
## 2. Relational Database Terminology

- **Relation**: A 2D table consisting of rows and columns.
- **Tuple**: A single row in a table (represents a single record).
- **Attribute**: A column in a table (represents a field/property).
- **Cardinality**: Number of tuples (rows) in a relation.
- **Degree**: Number of attributes (columns) in a relation.
- **Keys**:
  - **Primary Key (PK)**: Attribute(s) that uniquely identify each tuple in a relation (Must be UNIQUE and NOT NULL).
  - **Candidate Key**: Any set of attributes that could serve as a Primary Key.
  - **Alternate Key**: A Candidate Key not chosen as the Primary Key.
  - **Foreign Key (FK)**: An attribute in one table that references the Primary Key of another table (Enforces **Referential Integrity**).
  - **Composite Key**: A Primary Key composed of two or more attributes.

---
## 3. Entity-Relationship (ER) Diagrams & Mapping

> [!INFO] Deep Dive Note
> For ER Diagram symbols, cardinalities ($1:1, 1:N, M:N$), and step-by-step conversion rules of ERD to relational schema, read: [[Subtopics/System Analysis DFD & ER Modeling|DFD & ER Modeling Guide]].

### 3.1 Strong vs. Weak Entities

| Aspect | **Strong Entity** | **Weak Entity** |
|--------|-------------------|-----------------|
| **Key** | Own **Primary Key** | **Partial Key** + Owner's PK → **Composite PK** |
| **Dependence** | Independent | **Existence-dependent** on owner (cascading delete) |
| **ER Notation** | Single rectangle, single diamond | **Double rectangle**, **double diamond**, partial key *dashed underline* |
| **Example** | **Student** (`Student_ID`) | **Dependent** of Employee (`Emp_ID` + `Dep_Name` = PK) |

### 3.2 Participation Constraints

| Constraint | Notation | Meaning | Example |
|------------|----------|---------|---------|
| **Total Participation** | **Double line** (Entity ⟶ Relationship) | **Every** entity instance **must** participate in the relationship | A **Dependent** *must* belong to an Employee (weak entity → always total) |
| **Partial Participation** | **Single line** (Entity ⟶ Relationship) | Entity instance **may or may not** participate | An **Employee** *may* have zero Dependents |

> **Key Distinction**: **Strong/Weak** = structural *identity* (has own PK vs. borrows PK). **Total/Partial** = *participation cardinality* (mandatory vs. optional). A weak entity **always** has total participation in its identifying relationship, but a strong entity can *also* have total participation (e.g., every `Order` must have a `Customer`).

---
## 4. Database Normalization (1NF, 2NF, 3NF)

> [!INFO] Deep Dive Note
> For functional dependencies, partial/transitive dependency definitions, and step-by-step normalization examples, read: [[Subtopics/Database Normalization (1NF, 2NF, 3NF)|Database Normalization Guide]].

- **1NF**: Remove multi-valued/composite attributes; ensure atomic values and define Primary Key.
- **2NF**: In 1NF + Remove **Partial Dependencies** (all non-key attributes must be fully functionally dependent on the entire Primary Key).
- **3NF**: In 2NF + Remove **Transitive Dependencies** (no non-key attribute depends on another non-key attribute).

---
## 5. Structured Query Language (SQL)

> [!INFO] Deep Dive Note
> For SQL data types, constraints, DDL, DML, `SELECT`, conditions, grouping, aggregate functions, and joins, read: [[Subtopics/SQL Query Language Guide|SQL Query Language Guide]].

SQL is used to create database structures and manage/retrieve data in relational databases.

| Category | Meaning | Commands |
|----------|---------|----------|
| **DDL** | Defines or changes database/table structure | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** | Manipulates records/data inside tables | `INSERT`, `UPDATE`, `DELETE` |
| **DQL** | Retrieves data from tables | `SELECT` |

```sql
-- DDL examples
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    ClassID INT
);

ALTER TABLE Student ADD Email VARCHAR(100);
TRUNCATE TABLE Student; -- removes all rows, keeps table structure
DROP TABLE Student;     -- removes table completely

-- DML examples
INSERT INTO Student (StudentID, Name, ClassID)
VALUES (101, 'Kamal Perera', 12);

UPDATE Student SET Name = 'Kamal Silva' WHERE StudentID = 101;
DELETE FROM Student WHERE StudentID = 101;

-- Query example
SELECT Student.Name, Class.ClassName
FROM Student
INNER JOIN Class ON Student.ClassID = Class.ClassID
WHERE Student.ClassID = 12
ORDER BY Student.Name ASC;
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the difference between Cardinality and Degree in relational database terminology? :: Cardinality is the total number of tuples (rows); Degree is the total number of attributes (columns) in a relation.

What is a Foreign Key, and what rule does it enforce? :: An attribute in a table that references the Primary Key of another table; it enforces Referential Integrity.
<!--SR:!2026-09-26,1,230-->

State the rule for 1st Normal Form (1NF). :: All attributes must contain atomic (indivisible) values, and a Primary Key must be defined.
<!--SR:!2026-11-24,60,310-->

State the rule for 2nd Normal Form (2NF). :: The table must be in 1NF, and all partial functional dependencies must be eliminated (every non-key attribute must fully depend on the primary key).
<!--SR:!2026-09-29,4,270-->

State the rule for 3rd Normal Form (3NF). :: The table must be in 2NF, and all transitive functional dependencies must be eliminated (no non-key attribute should depend on another non-key attribute).

What is the difference between DDL and DML in SQL? :: DDL defines/modifies database structures (e.g., `CREATE`, `ALTER`, `DROP`, `TRUNCATE`); DML changes records inside tables (e.g., `INSERT`, `UPDATE`, `DELETE`). `SELECT` retrieves data and is often treated as DQL.
<!--SR:!2026-10-02,15,290-->
