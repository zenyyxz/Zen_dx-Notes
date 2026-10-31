---
title: Database Normalization (1NF, 2NF, 3NF)
subject: AL ICT
subtopic: Database Systems
tags:
  - AL-ICT
  - Subtopic
  - Normalization
  - 1NF
  - 2NF
  - 3NF
---
# Subtopic: Database Normalization Guide (1NF, 2NF, 3NF)

> [!ABSTRACT] Core Focus
> Functional dependencies, identifying anomalies (Insertion, Deletion, Update), and step-by-step normalization from Unnormalized Form (UNF) to 3NF.

> [!INFO] Parent Lesson
> This deep dive is used in [[Lesson 08 - Database Management Systems|Lesson 08: Database Management Systems]].

---
## 1. Functional Dependency Concepts

- **Functional Dependency ($X \rightarrow Y$)**: Attribute $Y$ is functionally dependent on $X$ if each value of $X$ uniquely determines $Y$.
- **Partial Dependency**: A non-key attribute is dependent on only a **part** of a composite Primary Key.
- **Transitive Dependency**: A non-key attribute is dependent on another **non-key** attribute ($X \rightarrow Y$ and $Y \rightarrow Z$, so $X \rightarrow Z$).

---
## 2. Normalization Steps Summary

``` mermaid
flowchart LR
	UNF[UNF] -->|Remove Multi-Valued Attributes| 1NF[1NF]
	1NF -->|Remove Partial Dependencies| 2NF[2NF]
	2NF -->|Remove Transitive Dependencies| 3NF[3NF]
```

---
## 3. Worked Normalization Example

### Given Unnormalized Table (UNF):
`Student_Course(StudentID, StudentName, (CourseID, CourseName, Instructor, InstructorOffice))`

### Step 1: Convert to 1NF (Flatten repeating groups & assign Primary Key):
- Primary Key: `(StudentID, CourseID)`
- **1NF Relation**:
  `Student_Course_1NF(StudentID, CourseID, StudentName, CourseName, Instructor, InstructorOffice)`

### Step 2: Convert to 2NF (Eliminate Partial Dependencies):
- Partial Dependencies detected:
  - `StudentID -> StudentName` (depends only on part of PK `StudentID`)
  - `CourseID -> CourseName, Instructor, InstructorOffice` (depends only on `CourseID`)
- **2NF Relations**:
  - `Student(StudentID, StudentName)`
  - `Course(CourseID, CourseName, Instructor, InstructorOffice)`
  - `Student_Course(StudentID, CourseID)` *(Junction Table)*

### Step 3: Convert to 3NF (Eliminate Transitive Dependencies):
- Transitive Dependency detected in `Course` table:
  - `Instructor -> InstructorOffice` (non-key attribute determines non-key attribute)
- **3NF Relations**:
  - `Student(StudentID, StudentName)`
  - `Course(CourseID, CourseName, InstructorID)`
  - `Instructor(InstructorID, InstructorName, InstructorOffice)`
  - `Student_Course(StudentID, CourseID)`

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is a functional dependency $X \rightarrow Y$? :: Each value of $X$ determines exactly one value of $Y$.

What is a partial dependency? :: A non-key attribute depends on only part of a composite primary key.

What is a transitive dependency? :: A non-key attribute depends on another non-key attribute: $X \rightarrow Y$ and $Y \rightarrow Z$.

What is the goal of normalization? :: To reduce data redundancy and insertion, deletion and update anomalies by organising data into related tables.

What does 1NF require? :: Atomic values, no repeating groups, and a primary key.

What does 2NF require? :: 1NF plus no partial dependencies; every non-key attribute must depend on the whole primary key.

What does 3NF require? :: 2NF plus no transitive dependencies; non-key attributes must depend only on keys.

How do you convert UNF to 1NF? :: Flatten repeating groups into atomic values and assign a primary key.

How do you convert 1NF to 2NF? :: Remove partial dependencies by splitting attributes into separate tables and a junction table if needed.

How do you convert 2NF to 3NF? :: Remove transitive dependencies by moving dependent non-key attributes into a new table.

What is a composite primary key? :: A primary key made of two or more attributes, such as `(StudentID, CourseID)` in the worked example.

Which partial dependencies are removed in the worked example? :: `StudentID -> StudentName` and `CourseID -> CourseName, Instructor, InstructorOffice`.

Which transitive dependency is removed in the 3NF step? :: `Instructor -> InstructorOffice`.

Why is `Student_Course` a junction table? :: It links Student and Course in a many-to-many relationship using both foreign keys.

Name the three normalization anomalies. :: Insertion, deletion and update anomalies.

What causes these anomalies? :: Data redundancy and dependencies between attributes.

Does normalization usually increase the number of tables? :: Yes; it reduces redundancy but may require more joins.