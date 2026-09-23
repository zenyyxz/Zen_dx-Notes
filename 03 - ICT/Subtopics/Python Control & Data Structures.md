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
> Program structure/comments, I/O/casting, operators, data types, List/Tuple/Dict/String manipulation, conditional logic, loops, custom function definitions/scope, file handling, DB embedding, linear search. Marked Extension is beyond NIE 9.7-9.13.

---
## 1. Python Data Structures Comparison

| Data Structure | Syntax | Mutable? | Ordered? | Allows Duplicates? |
| :--- | :--- | :---: | :---: | :---: |
| **String** | `"hello"` | No | Yes | Yes |
| **List** | `[1, 2, 3]` | Yes | Yes | Yes |
| **Tuple** | `(1, 2, 3)` | No (Immutable) | Yes | Yes |
| **Dictionary** | `{"a": 1, "b": 2}` | Yes (Keys unique) | Yes (3.7+) | Values: Yes |
| **Set** (Extension) | `{1, 2, 3}` | Yes | No | No |

---
## 2. Basics: Structure, I/O, Operators (syllabus 9.7)

```python
# Comments: # line, '''block''', """docstring for funcs"""
PI = 3.14
name = input("Name: ")       # always string
age = int(input("Age: "))    # casting: int(), float(), str()
print("Hi", name, age)
# Primitive: int, float, bool, str
# Operators: + - * / // % ** | == != > < | and or not | & | ^ ~ << >> | in, is | += -=
# Precedence: () > ** > * / // % > + - ; ** right-to-left
```

## 3. Key Code Examples

### A. List Operations:
```python
numbers = [10, 20, 30]
numbers.append(40)        # Add to end: [10, 20, 30, 40]
numbers.insert(1, 15)     # Insert at index 1: [10, 15, 20, 30, 40]
val = numbers.pop()       # Removes and returns last element (40)
print(numbers[0:2])       # Slicing: [10, 15]
```

### B. Strings & Tuples:
```python
s = "hello"
print(s[0], s[1:3], len(s))  # h, el, 5
t = (1, 2, 3)  # immutable, faster
# t[0] = 9  # error
```

### C. Dictionary Operations:
```python
student = {"id": 101, "name": "Kamal", "marks": 85}
print(student["name"])    # Access value: Kamal
student["grade"] = "A"    # Add key-value pair
for key, value in student.items():
    print(key, ":", value)
```

### D. Control + Functions (syllabus 9.8-9.9):
```python
# Selection + repetition + nesting
for i in range(1, 6):
    if i % 2 == 0:
        print(i, "even")

count = 0
while count < 5:
    count += 1

def greet(name="Guest"):
    """Return greeting."""
    return f"Hello, {name}!"
# local vs global: local inside func, global outside; use global x to modify
```

### E. File Handling (Reading and Writing):
```python
# Modes: "w" write, "r" read, "a" append; with auto-closes
with open("results.txt", "w") as file:
    file.write("Kamal,85\nNimal,92\n")

# Reading line-by-line using with context manager
with open("results.txt", "r") as file:
    for line in file:
        data = line.strip().split(",")
        print(f"Name: {data[0]}, Marks: {data[1]}")
```

### F. DB + Search (syllabus 9.12-9.13):
```python
import sqlite3
conn = sqlite3.connect("school.db")
cur = conn.cursor()
cur.execute("INSERT INTO Student VALUES (?, ?)", (101, "Kamal"))
conn.commit()
for row in cur.execute("SELECT * FROM Student"):
    print(row)
conn.close()

def linear_search(arr, target):  # sequential, O(N)
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```
Binary search, sets, recursion, try/except are Extension — not required by 9.10-9.13.
