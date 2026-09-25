---
title: Lesson 12 - Range-Query Data Structures
subject: Computer Science
unit: 12
competency: Implement Fenwick Trees and Segment Trees for dynamic range queries and point updates
tags:
  - Computer-Science
  - Competitive-Programming
  - FenwickTree
  - SegmentTree
  - DataStructures
  - Flashcards
---
---
# :LiBook: Lesson 12: Range-Query Data Structures

> [!ABSTRACT] Scope
> Prefix sums handle static arrays ($O(1)$ query, $O(N)$ update). For dynamic arrays requiring point updates and range queries in $O(\log N)$ time, use Fenwick Trees or Segment Trees.

---
## 1. Binary Indexed Tree (Fenwick Tree)

A Fenwick tree supports **Point Addition** and **Prefix Sum Queries** in $O(\log N)$ time with $O(N)$ space. Uses 1-indexed operations with bitwise lowbit (`idx & -idx`).

```cpp
#include <iostream>
#include <vector>
using namespace std;

struct FenwickTree {
    int n;
    vector<long long> tree;

    FenwickTree(int n) : n(n), tree(n + 1, 0) {}

    // Add 'val' to 1-indexed element 'idx': O(log N)
    void add(int idx, long long val) {
        for (; idx <= n; idx += idx & -idx) {
            tree[idx] += val;
        }
    }

    // Query prefix sum from 1 to 'idx': O(log N)
    long long query(int idx) {
        long long sum = 0;
        for (; idx > 0; idx -= idx & -idx) {
            sum += tree[idx];
        }
        return sum;
    }

    // Range sum query [l, r] (1-indexed, inclusive): O(log N)
    long long queryRange(int l, int r) {
        return query(r) - query(l - 1);
    }
};
```

---
## 2. Segment Tree (Point Update, Range Query)

Segment Trees support flexible range operations (Sum, Min, Max, GCD) in $O(\log N)$ time.

```cpp
#include <iostream>
#include <vector>
using namespace std;

struct SegmentTree {
    int n;
    vector<long long> tree;

    SegmentTree(int n) : n(n), tree(4 * n, 0) {}

    void build(const vector<int>& a, int node, int start, int end) {
        if (start == end) {
            tree[node] = a[start];
            return;
        }
        int mid = start + (end - start) / 2;
        build(a, 2 * node, start, mid);
        build(a, 2 * node + 1, mid + 1, end);
        tree[node] = tree[2 * node] + tree[2 * node + 1];
    }

    // Point Update: set a[idx] = val
    void update(int node, int start, int end, int idx, long long val) {
        if (start == end) {
            tree[node] = val;
            return;
        }
        int mid = start + (end - start) / 2;
        if (idx <= mid) update(2 * node, start, mid, idx, val);
        else update(2 * node + 1, mid + 1, end, idx, val);
        tree[node] = tree[2 * node] + tree[2 * node + 1];
    }

    // Range Query: sum from [l, r]
    long long query(int node, int start, int end, int l, int r) {
        if (r < start || end < l) return 0; // Out of range
        if (l <= start && end <= r) return tree[node]; // Completely inside
        int mid = start + (end - start) / 2;
        return query(2 * node, start, mid, l, r) + query(2 * node + 1, mid + 1, end, l, r);
    }
};
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the time complexity of point updates and range queries in a Fenwick Tree? :: $O(\log N)$ time for both operations.

What bitwise trick isolates the lowest set bit in a Fenwick Tree index? :: `idx & -idx`.
<!--SR:!2026-09-26,1,230-->

How much memory array size should be allocated for a recursive Segment Tree on $N$ elements? :: $4N$ size array.
