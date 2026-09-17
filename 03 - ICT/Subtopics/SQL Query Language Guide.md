---
title: SQL Query Language Guide
subject: AL ICT
subtopic: Database Systems
tags:
  - AL-ICT
  - Subtopic
  - SQL
  - Database
  - DDL
  - DML
  - Flashcards
---
# Subtopic: SQL Query Language Guide

> [!ABSTRACT] Core Focus
> SQL command categories, table creation, constraints, data manipulation, queries, conditions, sorting, grouping, aggregate functions, and joins.

---
## 1. SQL Command Categories

| Category | Meaning | Commands |
|----------|---------|----------|
| **DDL** | Defines/changes database structures | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** | Changes records/data in tables | `INSERT`, `UPDATE`, `DELETE` |
| **DQL** | Retrieves data | `SELECT` |
| **DCL** | Controls access | `GRANT`, `REVOKE` |
| **TCL** | Manages transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

> `SELECT` is sometimes grouped under DML in school notes, but strictly it is DQL.

---
## 2. Data Types and Constraints

### Common SQL Data Types

| Category | Data Type | Description | Example |
|----------|-----------|-------------|---------|
| **Numeric (Exact)** | `INT` / `INTEGER` | Whole numbers (typically 4 bytes) | `StudentID INT` |
| | `SMALLINT` | Small integers (2 bytes) | `Age SMALLINT` |
| | `BIGINT` | Large integers (8 bytes) | `BigID BIGINT` |
| | `DECIMAL(p,s)` / `NUMERIC(p,s)` | Fixed-point exact decimals | `Salary DECIMAL(10,2)` |
| **Numeric (Approximate)** | `FLOAT(n)` | Single-precision floating point | `Weight FLOAT` |
| | `DOUBLE` / `REAL` | Double-precision floating point | `Price DOUBLE` |
| **Character Strings** | `CHAR(n)` | **Fixed-length** string (padded with spaces) | `Gender CHAR(1)` |
| | `VARCHAR(n)` | **Variable-length** string (max n) | `Name VARCHAR(50)` |
| | `TEXT` / `LONGTEXT` | Large text (up to 65K / 4GB) | `Description TEXT` |
| **Binary Strings** | `BINARY(n)` | Fixed-length binary | `Hash BINARY(32)` |
| | `VARBINARY(n)` | Variable-length binary | `FileData VARBINARY(MAX)` |
| | `BLOB` / `LONGBLOB` | Binary large objects (images, files) | `Photo BLOB` |
| **Date & Time** | `DATE` | Date only (YYYY-MM-DD) | `DOB DATE` |
| | `TIME` | Time only (HH:MM:SS) | `StartTime TIME` |
| | `DATETIME` | Date + Time (YYYY-MM-DD HH:MM:SS) | `CreatedAt DATETIME` |
| | `TIMESTAMP` | Auto-updating timestamp | `UpdatedAt TIMESTAMP` |
| | `YEAR` | Year only (YYYY) | `EnrollmentYear YEAR` |
| **Other** | `BOOLEAN` / `BIT` | True/False (stored as 1/0) | `IsActive BOOLEAN` |
| | `ENUM('a','b','c')` | Predefined list of allowed values | `Status ENUM('A','I')` |
| | `JSON` | JSON documents (MySQL 5.7+, PostgreSQL) | `Config JSON` |

### Constraints

| Constraint | Use | Example |
|------------|-----|---------|
| `PRIMARY KEY` | Unique identifier (NOT NULL + UNIQUE) | `StudentID INT PRIMARY KEY` |
| `FOREIGN KEY` | Links to another table | `FOREIGN KEY (ClassID) REFERENCES Class(ClassID)` |
| `NOT NULL` | Must have a value | `Name VARCHAR(50) NOT NULL` |
| `UNIQUE` | No duplicates | `Email VARCHAR(100) UNIQUE` |
| `DEFAULT` | Default value | `Status VARCHAR(10) DEFAULT 'Active'` |
| `CHECK` | Value condition | `CHECK (Marks >= 0 AND Marks <= 100)` |
| `AUTO_INCREMENT` / `IDENTITY` | Auto-generate sequential integers | `ID INT AUTO_INCREMENT PRIMARY KEY` |

---
## 3. DDL: Data Definition Language

```sql
CREATE DATABASE school_db;

CREATE TABLE Class (
    ClassID INT PRIMARY KEY,
    ClassName VARCHAR(20) NOT NULL
);

CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    DOB DATE,
    Marks INT CHECK (Marks >= 0 AND Marks <= 100),
    ClassID INT,
    FOREIGN KEY (ClassID) REFERENCES Class(ClassID)
);

ALTER TABLE Student ADD Email VARCHAR(100);
ALTER TABLE Student MODIFY Name VARCHAR(75);
ALTER TABLE Student DROP COLUMN Email;

TRUNCATE TABLE Student; -- removes all rows, keeps table structure
DROP TABLE Student;     -- removes table structure and data
```

> `TRUNCATE` is usually classified as **DDL**. It removes all records but keeps the table.

---
## 4. DML: Data Manipulation Language

```sql
INSERT INTO Student (StudentID, Name, DOB, Marks, ClassID)
VALUES (101, 'Kamal Perera', '2005-04-12', 85, 12);

UPDATE Student
SET Marks = 90
WHERE StudentID = 101;

DELETE FROM Student
WHERE StudentID = 101;
```

---
## 5. SELECT Queries

```sql
SELECT * FROM Student;

SELECT StudentID, Name, Marks
FROM Student
WHERE Marks >= 75;

-- DISTINCT: return only unique values (remove duplicates)
SELECT DISTINCT ClassID FROM Student;

-- LIMIT: restrict number of rows returned (useful for pagination)
SELECT StudentID, Name
FROM Student
LIMIT 10;
```

### Common Conditions

```sql
WHERE Marks >= 75 AND ClassID = 12;
WHERE ClassID = 12 OR ClassID = 13;
WHERE NOT ClassID = 12;
WHERE Marks BETWEEN 50 AND 75;
WHERE ClassID IN (12, 13, 14);
WHERE Name LIKE 'K%';
WHERE Email IS NULL;
```

---
## 6. Sorting, Grouping, and Aggregate Functions

```sql
SELECT Name, Marks
FROM Student
ORDER BY Marks DESC;

SELECT ClassID, COUNT(*) AS StudentCount
FROM Student
GROUP BY ClassID;

SELECT ClassID, AVG(Marks) AS AverageMarks
FROM Student
GROUP BY ClassID
HAVING AVG(Marks) >= 75;
```

| Function | Meaning |
|----------|---------|
| `COUNT()` | Count rows |
| `SUM()` | Total |
| `AVG()` | Average |
| `MIN()` | Minimum |
| `MAX()` | Maximum |

> `WHERE` filters rows before grouping. `HAVING` filters groups after `GROUP BY`.

---
## 7. JOINs

> [!INFO] When & Why to Use JOINs
> Use `JOIN` when you need data spread across **multiple related tables** (e.g., student info in one table, class info in another). It combines rows based on a related column (usually `PRIMARY KEY` ↔ `FOREIGN KEY`). Without JOINs, you'd have to query tables separately and match manually.

```sql
-- INNER JOIN: matching records only
SELECT Student.Name, Class.ClassName
FROM Student
INNER JOIN Class ON Student.ClassID = Class.ClassID;

-- LEFT JOIN: all records from left table
SELECT Student.Name, Class.ClassName
FROM Student
LEFT JOIN Class ON Student.ClassID = Class.ClassID;

-- RIGHT JOIN: all records from right table
SELECT Student.Name, Class.ClassName
FROM Student
RIGHT JOIN Class ON Student.ClassID = Class.ClassID;

-- FULL OUTER JOIN: all records from both tables (matched + unmatched both sides)
SELECT Student.Name, Class.ClassName
FROM Student
FULL OUTER JOIN Class ON Student.ClassID = Class.ClassID;

-- CROSS JOIN: Cartesian product (every row paired with every row — no ON clause)
SELECT Student.Name, Class.ClassName
FROM Student
CROSS JOIN Class;

-- SELF JOIN: table joined to itself (useful for hierarchical/parent-child data)
SELECT A.Name AS StudentName, B.Name AS PeerName
FROM Student A
INNER JOIN Student B ON A.ClassID = B.ClassID AND A.StudentID <> B.StudentID;
```

---
## 8. Quick Practice

```sql
-- Create table
CREATE TABLE Teacher (
    TeacherID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Subject VARCHAR(30),
    Salary DECIMAL(10,2)
);

-- Insert record
INSERT INTO Teacher (TeacherID, Name, Subject, Salary)
VALUES (1, 'Nimal', 'ICT', 75000.00);

-- Select condition
SELECT Name
FROM Student
WHERE Marks > 80;
```

---
## Flashcards

#flashcards

What are the main DDL commands in SQL? :: `CREATE`, `ALTER`, `DROP`, and `TRUNCATE`.

What is the purpose of `TRUNCATE`? :: It removes all rows from a table while keeping the table structure.

What is the difference between `DROP`, `TRUNCATE`, and `DELETE`? :: `DROP` removes the whole table; `TRUNCATE` removes all rows but keeps the table; `DELETE` removes selected/all rows and is DML.

What is the difference between `WHERE` and `HAVING`? :: `WHERE` filters rows before grouping; `HAVING` filters groups after `GROUP BY`.

Name five SQL aggregate functions. :: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()`.

What does `INNER JOIN` return? :: Only records with matching values in both joined tables.

What is the difference between `CHAR(n)` and `VARCHAR(n)`? :: `CHAR(n)` is **fixed-length** (always uses n bytes, pads with spaces); `VARCHAR(n)` is **variable-length** (uses only needed bytes + 1-2 overhead).

When would you use `DECIMAL(p,s)` instead of `FLOAT`/`DOUBLE`? :: For **exact** numeric values (e.g., money) — `DECIMAL` avoids floating-point rounding errors.

What does `AUTO_INCREMENT` (or `IDENTITY`) do? :: Automatically generates a unique sequential integer for new rows (commonly used for surrogate primary keys).

Name three date/time data types and their formats. :: `DATE` (YYYY-MM-DD), `TIME` (HH:MM:SS), `DATETIME` (YYYY-MM-DD HH:MM:SS).
