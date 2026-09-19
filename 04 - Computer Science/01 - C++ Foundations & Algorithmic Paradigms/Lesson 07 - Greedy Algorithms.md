---
title: Lesson 07 - Greedy Algorithms
subject: Computer Science
unit: 07
competency: Formulate greedy choices, prove correctness using exchange arguments, and sort by optimal heuristics
tags:
  - Computer-Science
  - Competitive-Programming
  - Greedy
  - Optimization
  - Flashcards
---
---
# :LiBook: Lesson 07: Greedy Algorithms

> [!ABSTRACT] Scope
> Solve optimization problems by making locally optimal choices at each step. Learn how to justify greedy algorithms with exchange arguments.

---
## 1. The Greedy Strategy & Proof Intuition

A Greedy algorithm makes the choice that looks best right now without looking ahead or undoing past decisions.

To prove a Greedy choice is correct:
- **Exchange Argument**: Assume an optimal solution exists that differs from the greedy solution. Show that swapping a non-greedy choice for the greedy choice yields a solution that is at least as good.

---
## 2. Canonical Example: Interval Scheduling (Activity Selection)

**Problem**: Given $N$ intervals with start time $S_i$ and finish time $F_i$, select the maximum number of non-overlapping intervals.

**Greedy Choice**: Always pick the interval that finishes **earliest** ($F_i$).

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

struct Interval {
    int start, finish;

    // Sort intervals by finish time ascending
    bool operator<(const Interval& other) const {
        return finish < other.finish;
    }
};

int maxNonOverlappingIntervals(vector<Interval>& intervals) {
    sort(intervals.begin(), intervals.end());

    int count = 0;
    int last_finish = -1;

    for (const auto& iv : intervals) {
        if (iv.start >= last_finish) {
            count++;
            last_finish = iv.finish;
        }
    }
    return count;
}
```

> [!TIP] Proof Intuition for Interval Scheduling
> Finishing earlier leaves the maximum possible remaining time for future intervals to fit in!

---
## 3. When Greedy Fails (Coin Change Warning)

- **Greedy Works**: Standard coin denominations $\{1, 5, 10, 25, 100\}$.
- **Greedy Fails**: Non-standard coin denominations $\{1, 3, 4\}$ for target sum $6$. Greedy picks $4 + 1 + 1$ (3 coins), but optimal is $3 + 3$ (2 coins!). Use Dynamic Programming when coin systems lack greedy choice properties.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What heuristic should you sort by to solve the classic Interval Scheduling problem? :: Sort intervals by their **finish time** in ascending order.

What proof technique is commonly used to prove the correctness of a Greedy algorithm? :: The Exchange Argument proof.

Why can Greedy fail on general coin change problems? :: Because locally taking the largest coin denomination may leave a remainder that requires more total coins than a smaller initial coin pick would (requires Dynamic Programming).
