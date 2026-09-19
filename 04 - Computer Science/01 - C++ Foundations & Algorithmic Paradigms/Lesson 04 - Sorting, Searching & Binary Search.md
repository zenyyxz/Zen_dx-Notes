---
title: Lesson 04 - Sorting, Searching & Binary Search
subject: Computer Science
unit: 04
competency: Use sorting and binary search to reduce search spaces efficiently
tags:
  - Computer-Science
  - Competitive-Programming
  - Sorting
  - BinarySearch
  - Flashcards
---
---
# :LiBook: Lesson 04: Sorting, Searching & Binary Search

> [!ABSTRACT] Scope
> Sorting reveals order. Binary search finds a boundary in a sorted range or in any monotone true/false condition.

---
## 1. Sorting with a Comparator

```cpp
vector<pair<int, int>> intervals;
sort(intervals.begin(), intervals.end(), [](auto x, auto y) {
    if (x.second != y.second) return x.second < y.second;
    return x.first < y.first;
});
```

`sort` costs $O(n \log n)$. A comparator must be consistent: do not use `<=` inside it.

---
## 2. Library Binary Search

For sorted `a`:

```cpp
auto it = lower_bound(a.begin(), a.end(), x); // first value >= x
auto jt = upper_bound(a.begin(), a.end(), x); // first value > x

int first = lower_bound(a.begin(), a.end(), x) - a.begin();
int count = upper_bound(a.begin(), a.end(), x)
          - lower_bound(a.begin(), a.end(), x);
```

---
## 2.5 Basic Binary Search (Manual)

Binary search finds a value in a **sorted** array by repeatedly cutting the range in half. At each step, compare the target `x` to the middle element `a[mid]`:

- If `a[mid] == x` → found it.
- If `a[mid] < x` → the answer must be in the right half (`low = mid + 1`).
- If `a[mid] > x` → the answer must be in the left half (`high = mid - 1`).

This gives $O(\log n)$ time because the range size halves every iteration.

```cpp
int binary_search(vector<int>& a, int x) {
    int low = 0, high = (int)a.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;   // avoid overflow
        if (a[mid] == x) return mid;    // found
        else if (a[mid] < x) low = mid + 1;
        else high = mid - 1;
    }
    return -1; // not found
}
```

**Key invariant:** the answer is always inside `[low, high]`. When `low > high`, it is not present.

---
## 3. Binary Search on the Answer

Use this when you can ask: “Is answer $m$ feasible?” and feasibility changes only once from true to false, or vice versa.

```cpp
long long low = 0, high = 1'000'000'000LL;
while (low < high) {
    long long mid = low + (high - low) / 2;
    if (feasible(mid)) high = mid;      // seek smallest feasible answer
    else low = mid + 1;
}
cout << low << '\n';
```

Before coding, write which side is feasible and state the invariant: the optimal answer is still in `[low, high]`.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What does `lower_bound` return? :: An iterator to the first element that is greater than or equal to the target.

What property is needed for binary search on an answer? :: The feasibility predicate must be monotone across the search range.

Why use `low + (high - low) / 2` for a midpoint? :: It avoids overflow that can occur in `(low + high) / 2`.

What is the time complexity of binary search on a sorted array? :: $O(\log n)$, because the search space halves with every comparison.

What invariant must hold during a manual binary search? :: The target value is always inside the current interval `[low, high]`.
