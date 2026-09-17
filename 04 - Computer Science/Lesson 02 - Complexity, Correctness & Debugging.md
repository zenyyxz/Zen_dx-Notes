---
title: Lesson 02 - Complexity, Correctness & Debugging
subject: Computer Science
unit: 02
competency: Estimate whether an algorithm fits the constraints and justify that it works
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
> A correct algorithm that is too slow still fails. Learn to read constraints, estimate running time, and build a short proof before trusting your code.

---
## 1. Big-O: Growth, Not Stopwatch Time

| Complexity | Usually practical for one test case |
| :--- | :--- |
| $O(1)$, $O(\log n)$ | very large $n$ |
| $O(n)$, $O(n \log n)$ | often up to $10^5$–$10^6$ |
| $O(n\sqrt n)$ | medium constraints |
| $O(n^2)$ | often around $n \le 3000$, context dependent |
| $O(2^n)$ | only small $n$, often $n \le 20$ |

These are rough contest instincts, not laws. Always account for the sum of constraints across test cases.

---
## 2. Count Nested Work

```cpp
for (int i = 0; i < n; i++)       // n times
    for (int j = 0; j < n; j++)   // n times each
        work();
```

This is $O(n^2)$. But this loop is different:

```cpp
int j = 0;
for (int i = 0; i < n; i++) {
    while (j < n && condition(i, j)) j++;
}
```

If `j` never moves backwards, it advances at most $n$ times total, so the whole code is often $O(n)$, not $O(n^2)$.

---
## 3. Correctness: State Why the Answer Is Right

A useful proof structure:

1. **Claim:** say what your algorithm returns.
2. **Invariant:** name something that remains true after every loop step.
3. **Termination:** explain why the loop/recursion ends.
4. **Conclusion:** show the invariant implies the answer is correct.

Example: binary search invariant—“the answer is still inside the current search interval.”

---
## 4. A Debugging Checklist

- Did you process every test case independently?
- Is the array indexed from `0` to `n - 1`?
- Are endpoints included or excluded consistently?
- Can sums/products overflow `int`?
- Does the algorithm work for $n=1$, repeated values, and already-sorted input?
- Did you prove the condition used in a greedy or binary-search solution?

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is Big-O notation used for? :: Describing how an algorithm's time or memory use grows as input size grows.

Why can a nested loop still be $O(n)$? :: If the inner pointer only moves forward a total of at most $n$ times across all outer-loop iterations.

What is a loop invariant? :: A statement that is true before and after every iteration and helps prove correctness.
