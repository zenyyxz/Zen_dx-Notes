---
title: Python Control & Data Structures Guide
subject: AL ICT
subtopic: Programming
tags:
  - AL-ICT
  - Subtopic
  - Python
  - DataStructures
  - Algorithms
---
# Subtopic: Python Control & Data Structures Guide

> [!ABSTRACT] Core Focus
> Data types, List/Tuple/Dictionary manipulation, conditional logic, loops, custom function definitions, and file handling operations in Python.

---
## 1. Python Data Structures Comparison

| Data Structure | Syntax | Mutable? | Ordered? | Allows Duplicates? |
| :--- | :--- | :---: | :---: | :---: |
| **List** | `[1, 2, 3]` | Yes | Yes | Yes |
| **Tuple** | `(1, 2, 3)` | No (Immutable) | Yes | Yes |
| **Dictionary** | `{"a": 1, "b": 2}` | Yes (Keys unique) | Yes (3.7+) | Values: Yes |
| **Set** | `{1, 2, 3}` | Yes | No | No |

---
## 2. Key Code Examples

### A. List Operations:
```python
numbers = [10, 20, 30]
numbers.append(40)        # Add to end: [10, 20, 30, 40]
numbers.insert(1, 15)     # Insert at index 1: [10, 15, 20, 30, 40]
val = numbers.pop()       # Removes and returns last element (40)
print(numbers[0:2])       # Slicing: [10, 15]
```

### B. Dictionary Operations:
```python
student = {"id": 101, "name": "Kamal", "marks": 85}
print(student["name"])    # Access value: Kamal
student["grade"] = "A"    # Add key-value pair
for key, value in student.items():
    print(key, ":", value)
```

### C. File Handling (Reading and Writing):
```python
# Writing to a text file
file = open("results.txt", "w")
file.write("Kamal,85
Nimal,92
")
file.close()

# Reading line-by-line using with context manager
with open("results.txt", "r") as file:
    for line in file:
        data = line.strip().split(",")
        print(f"Name: {data[0]}, Marks: {data[1]}")
```