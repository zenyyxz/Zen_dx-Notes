---
title: Competitive Programming & LeetCode - Map of Concepts (MOC)
subject: Computer Science
level: Problem Solving / Contest Practice
tags:
  - CP-Problems
  - LeetCode
  - MOC
  - Index
  - SpacedRepetition
---
# :LiCode: Problem Solutions & Upsolving Hub (MOC)

> [!ABSTRACT] Overview & Philosophy
> A centralized log of competitive programming and LeetCode problems solved. Each problem note documents:
> 1. **Initial First Attempt** — the raw intuition, brute-force or sub-optimal implementation, and its constraints/bottlenecks.
> 2. **Key Insight ("Aha!" Moment)** — the theoretical shift or algorithmic pattern that unlocks efficiency.
> 3. **Optimal Solution** — high-performance C++ implementation with asymptotic complexity analysis.
> 4. **Vault Cross-Links** — connecting practice problems directly to core CS theory notes.

---

## :LiListFilter: Problem Index

| ID | Problem Title | Platform | Difficulty | Core Pattern | Attempts | Note Link |
| :---: | :--- | :---: | :---: | :--- | :---: | :---: |
| **LC-0001** | Two Sum | LeetCode | Easy | Hash Map / Complement Lookup | $O(N^2) \to O(N)$ | [[04 - Problem Solutions/LC-0001 - Two Sum\|LC-0001 - Two Sum]] |
| **LC-0002** | Add Two Numbers | LeetCode | Medium | Linked List / Digit Simulation / Dummy Head | $O(\max(N,M))$ | [[04 - Problem Solutions/LC-0002 - Add Two Numbers\|LC-0002 - Add Two Numbers]] |

---

## :LiLayers: Topic & Pattern Breakdown

### 1. Arrays & Hashing
- [[04 - Problem Solutions/LC-0001 - Two Sum|LC-0001: Two Sum]] — Complements via `unordered_map` ($O(N)$ time, $O(N)$ space).
- *Theory Link:* [[04 - Computer Science/02 - Core Data Structures & Strings/Lesson 16 - Hash Tables & Hash Maps|Lesson 16 - Hash Tables & Hash Maps]]

### 2. Linked Lists
- [[04 - Problem Solutions/LC-0002 - Add Two Numbers|LC-0002: Add Two Numbers]] — Digit-by-digit simulation with dummy head ($O(\max(N,M))$).
- *Theory Link:* [[04 - Computer Science/02 - Core Data Structures & Strings/Lesson 15 - Linked Lists & Pointers|Lesson 15 - Linked Lists & Pointers]]

### 3. Two Pointers & Sliding Windows
- *(Upcoming problems)*
- *Theory Link:* [[04 - Computer Science/01 - C++ Foundations & Algorithmic Paradigms/Lesson 05 - Prefix Sums, Two Pointers & Sliding Windows|Lesson 05 - Prefix Sums, Two Pointers & Sliding Windows]]

### 4. Binary Search
- *(Upcoming problems)*
- *Theory Link:* [[04 - Computer Science/01 - C++ Foundations & Algorithmic Paradigms/Lesson 04 - Sorting, Searching & Binary Search|Lesson 04 - Sorting, Searching & Binary Search]]

---

## :LiWorkflow: The 4-Step Upsolving Habit

1. **Understand & Brute Force First:** Always formulate a brute force approach first. If you cannot solve it naively, you do not understand the problem yet.
2. **Analyze Constraints:** Check $N$. If $N \le 10^4$, $O(N^2)$ might squeak by. If $N \ge 10^5$, you strictly need $O(N)$ or $O(N \log N)$.
3. **Optimize with Data Structures & Invariants:** Identify what redundant work the brute force is doing (repeated scans, re-calculating sums) and eliminate it using hash maps, two pointers, prefix sums, or heaps.
4. **Log & Review Flashcards:** Save the problem note in this folder and review the spaced repetition flashcards weekly.
