---
title: Lesson 09 - Programming & Algorithms
subject: AL ICT
unit: 09
competency: Develops algorithms to solve problems and uses python programming language to encode algorithms
tags:
  - AL-ICT
  - Lesson-09
  - Programming
  - Algorithms
  - Python
  - DataStructures
  - Flashcards
---
# :LiBook: Lesson 09: Programming & Algorithms

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Problem Solving & Algorithm Representation (Pseudocode & Flowcharts)
> - Program Translators (Compiler vs Interpreter)
> - Python Fundamentals: Data types, Operators, Control structures
> - Python Data Structures (List, Tuple, Dictionary) & File Handling
> - Searching (Linear, Binary) & Sorting (Bubble Sort) Algorithms

---
## 1. Problem Solving & Flowcharts

An **Algorithm** is a finite sequence of step-by-step instructions to solve a given problem.

### Standard Flowchart Symbols:
- **Oval / Capsule**: Start / End (Terminal).
- **Parallelogram**: Input / Output.
- **Rectangle**: Process (Calculation, assignment).
- **Diamond**: Decision (Conditional branching `Yes/No`).
- **Circle**: Connector.

---
## 2. Program Translators

- **Compiler**: Translates entire source code into machine code object file at once. Faster execution, generates standalone `.exe` (e.g., C, C++).
- **Interpreter**: Translates and executes code line-by-line. Stops at first error; slower execution (e.g., Python, PHP).

---
## 3. Python Syntax & Control Structures

> [!INFO] Deep Dive Note
> For Python data types, List/Tuple/Dict operations, function definitions, and file handling code examples, read: [[Subtopics/Python Control & Data Structures|Python Control & Data Structures Guide]].

### Control Structures:
1. **Sequence**: Step-by-step execution.
2. **Selection**:
```python
if marks >= 75:
    grade = "A"
elif marks >= 65:
    grade = "B"
else:
    grade = "F"
```
3. **Iteration**:
```python
# For-each loop
for i in range(1, 6):
    print(i)

# While loop
count = 0
while count < 5:
    print(count)
    count += 1
```

---
## 4. Searching & Sorting Algorithms

### A. Linear Search:
Checks each element sequentially from index 0 to $N-1$.
- Time Complexity: $O(N)$

### B. Binary Search:
Requires **sorted array**. Compares target with middle element and halves search space repeatedly.
- Time Complexity: $O(\log N)$

### C. Bubble Sort:
Repeatedly steps through list, compares adjacent elements, and swaps them if in wrong order.
- Time Complexity: $O(N^2)$

```python
# Bubble Sort implementation in Python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the difference between a Compiler and an Interpreter? :: A Compiler translates the entire source code into machine code at once prior to execution; an Interpreter translates and executes source code line-by-line at runtime.

Which flowchart symbol is used for Decision making? :: Diamond.

What are the 3 fundamental control structures in programming? :: 1. Sequence, 2. Selection, 3. Iteration.

What is the difference between a Python List and a Tuple? :: A List is mutable (can be modified) and defined using square brackets `[]`; a Tuple is immutable (cannot be modified) and defined using parentheses `()`.

What is the precondition for executing a Binary Search algorithm on an array? :: The array must be sorted in ascending or descending order.

What is the worst-case Time Complexity of Bubble Sort? :: $O(N^2)$.