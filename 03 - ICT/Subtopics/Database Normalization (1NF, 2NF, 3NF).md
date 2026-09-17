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