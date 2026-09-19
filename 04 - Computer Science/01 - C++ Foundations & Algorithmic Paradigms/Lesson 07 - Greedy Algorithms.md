---
title: Lesson 07 - Greedy Algorithms
subject: Computer Science
unit: 07
competency: Recognise, implement, and justify locally optimal choices
tags:
  - Computer-Science
  - Competitive-Programming
  - Greedy
  - Proof
  - Flashcards
---
---
# :LiBook: Lesson 07: Greedy Algorithms

> [!ABSTRACT] Scope
> A greedy algorithm makes the best-looking choice now and never revisits it. It is powerful only when a proof shows that choice is safe.

---
## 1. The Greedy Question

Before coding, ask:

> Can an optimal solution always be changed so that it makes my greedy choice first?

If yes, use an **exchange argument**: take any optimal solution, replace its first conflicting choice with the greedy one, and show the replacement does not make it worse.

---
## 2. Interval Scheduling

To select the maximum number of non-overlapping intervals, choose the interval that finishes earliest among available intervals.

```cpp
sort(v.begin(), v.end(), [](auto a, auto b) {
    return a.second < b.second;
});

int chosen = 0;
int lastEnd = INT_MIN;
for (auto [start, end] : v) {
    if (start >= lastEnd) {
        chosen++;
        lastEnd = end;
    }
}
```

Why it works: replacing the first chosen interval of an optimal solution by an interval that ends no later cannot reduce the room left for later intervals.

---
## 3. Greedy Red Flags

Do not trust a greedy idea merely because it passes samples. Be suspicious when:

- a local choice changes future costs in complex ways;
- choices interact through a global constraint;
- you cannot write an exchange argument or invariant.

Many such problems are dynamic programming instead.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What must accompany a greedy algorithm? :: A proof that the local greedy choice can be part of an optimal solution.

What is an exchange argument? :: A proof that replaces a choice in an optimal solution with the greedy choice without worsening it.

What interval order gives the classic maximum-count interval scheduling algorithm? :: Increasing finishing time.
