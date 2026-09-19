---
title: Lesson 02 - Complexity, Correctness & Debugging
subject: Computer Science
unit: 02
competency: Estimate whether an algorithm fits time/memory constraints and prove correctness
tags:
  - Computer-Science
  - Competitive-Programming
  - Complexity
  - Correctness
  - Flashcards
---
---
# :LiBook: Lesson 02: Complexity, Correctness & Debugging

> [!ABSTRACT] Scope
> A correct algorithm that is too slow or uses too much memory fails. Learn to read constraints, estimate time and memory limits, and verify correctness before writing code.

---
## 1. Time Limits & Operation Rules of Thumb

In competitive programming, standard time limits are **1.0 to 2.0 seconds**, which corresponds to roughly **$10^8$ operations per second** in C++.

| Constraint $N$ | Max Allowed Complexity | Common Algorithms |
| :--- | :--- | :--- |
| $N \le 10$–$12$ | $O(N!)$ or $O(N^2 2^N)$ | Permutations, TSP Dynamic Programming |
| $N \le 20$–$22$ | $O(2^N \cdot N)$ | Bitmask DP, Subset Generation |
| $N \le 500$ | $O(N^3)$ | Floyd-Warshall, Matrix Multiplication |
| $N \le 3000$–$5000$ | $O(N^2)$ | 2D Dynamic Programming, Nested Loops |
| $N \le 10^5$–$3 \times 10^5$ | $O(N \log N)$ or $O(N \sqrt{N})$ | Sorting, Segment Trees, Mo's Algorithm |
| $N \le 10^6$–$10^7$ | $O(N)$ | Linear Scans, Prefix Sums, Sieve |
| $N \ge 10^9$ | $O(\log N)$ or $O(1)$ | Binary Search, Math / Formula Solutions |

---
## 2. Memory Limit Mathematics

Standard contest memory limit is **256 MB**.

$$\text{256 MB} = 256 \times 1024 \times 1024 \text{ bytes} \approx 2.68 \times 10^8 \text{ bytes}$$

| Data Type | Size per Element | Maximum Array Capacity in 256 MB |
| :--- | :--- | :--- |
| `int` / `float` | 4 bytes | $\approx 6.7 \times 10^7$ elements (e.g. $8000 \times 8000$ 2D array) |
| `long long` / `double` | 8 bytes | $\approx 3.3 \times 10^7$ elements |
| `bool` / `char` | 1 byte | $\approx 2.6 \times 10^8$ elements |

> [!WARNING] Memory Trap: Vector Overhead & Recursion Stack
> Creating `vector<int> adj[100000]` has dynamic pointer overhead per vector. Deep recursion can also cause Stack Overflow if stack depth exceeds limit ($\approx 10^5$ frames).

---
## 3. Counting Nested Work & Amortized Complexity

```cpp
// ❌ O(N^2) Nested Loop
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        work();
    }
}

// ✅ O(N) Two Pointers (Amortized Analysis)
int j = 0;
for (int i = 0; i < n; i++) {
    while (j < n && condition(i, j)) {
        j++; // 'j' only advances forward, moving at most N times total across ALL iterations!
    }
}
```

---
## 4. Correctness: Proofs & Invariants

To guarantee an algorithm is correct:
1. **Claim**: State the target output.
2. **Invariant**: Identify a property that remains true before and after every loop iteration.
3. **Termination**: Show why the loop or recursion must end.
4. **Conclusion**: Verify that when the loop ends, the invariant proves the output is correct.

*Example*: Binary Search invariant — *"The target value is strictly contained within the active range $[L, R]$."*

---
## 5. Contest Debugging Checklist

- **Independent Test Cases**: Reset all global arrays, sets, and counters at the start of each test case.
- **Index Bounds**: Verify 0-indexed vs 1-indexed boundaries ($0 \le i < n$).
- **Overflow Check**: Check if intermediate products exceed $2 \times 10^9$ (`use 1LL`).
- **Edge Cases**: Test $N = 1$, empty arrays, all-identical values, maximum values ($10^9$).

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Roughly how many operations can C++ execute within a 1.0 second time limit? :: Approximately $10^8$ operations.

How many 4-byte `int` elements can be safely stored within a 256 MB memory limit? :: Approximately $6.7 \times 10^7$ integers.

What is a loop invariant? :: A logical statement that holds true before and after every iteration, used to prove algorithm correctness.
