---
title: Lesson 12 - Range-Query Data Structures
subject: Computer Science
unit: 12
competency: Support repeated array updates and range queries using Fenwick and segment trees
tags:
  - Computer-Science
  - Competitive-Programming
  - DataStructures
  - FenwickTree
  - SegmentTree
  - Flashcards
---
---
# :LiBook: Lesson 12: Range-Query Data Structures

> [!ABSTRACT] Scope
> Prefix sums are ideal for static arrays. When values change between queries, use a data structure that updates and queries in logarithmic time.

---
## 1. Fenwick Tree (Binary Indexed Tree)

Use a Fenwick tree for prefix sums with point updates.

```cpp
struct Fenwick {
    int n;
    vector<long long> bit;
    Fenwick(int n) : n(n), bit(n + 1, 0) {}

    void add(int i, long long delta) { // 0-indexed external index
        for (++i; i <= n; i += i & -i) bit[i] += delta;
    }
    long long sumPrefix(int i) {       // sum [0, i)
        long long ans = 0;
        for (; i > 0; i -= i & -i) ans += bit[i];
        return ans;
    }
    long long sum(int l, int r) { return sumPrefix(r) - sumPrefix(l); }
};
```

Both update and query take $O(\log n)$.

---
## 2. Segment Tree Idea

A segment tree stores information for intervals. It can answer operations such as sum, minimum, maximum, or GCD over a range, usually with point updates in $O(\log n)$.

Use a segment tree when the operation is associative and a Fenwick tree is insufficient—for example, range minimum with updates.

---
## 3. Choose the Simplest Sufficient Tool

| Array situation | Tool |
| :--- | :--- |
| no updates, range sums | prefix sums |
| point updates, range sums | Fenwick tree |
| point updates, range min/max/GCD | segment tree |
| offline queries that can be reordered | consider sorting / Mo's algorithm later |

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

When are prefix sums insufficient? :: When values change between range queries.

What operations does a Fenwick tree support efficiently? :: Point updates and prefix/range sum queries, each in $O(\log n)$.

When is a segment tree more flexible than a Fenwick tree? :: For associative range operations such as minimum, maximum, or GCD with updates.
