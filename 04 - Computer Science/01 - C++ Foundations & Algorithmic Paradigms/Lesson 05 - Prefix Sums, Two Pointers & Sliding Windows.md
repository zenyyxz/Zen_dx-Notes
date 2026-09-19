---
title: Lesson 05 - Prefix Sums, Two Pointers & Sliding Windows
subject: Computer Science
unit: 05
competency: Transform repeated array-range work into linear or constant-time queries
tags:
  - Computer-Science
  - Competitive-Programming
  - Arrays
  - PrefixSums
  - TwoPointers
  - Flashcards
---
---
# :LiBook: Lesson 05: Prefix Sums, Two Pointers & Sliding Windows

> [!ABSTRACT] Scope
> Many array problems look quadratic because they ask about subarrays. Learn three patterns that avoid recalculating the same work.

---
## 1. Prefix Sums

Define `pref[i]` as the sum of the first `i` elements, with `pref[0] = 0`.

```cpp
vector<long long> pref(n + 1, 0);
for (int i = 0; i < n; i++) {
    pref[i + 1] = pref[i] + a[i];
}

// Sum of a[l], a[l+1], ..., a[r], inclusive:
long long sum = pref[r + 1] - pref[l];
```

Build once in $O(n)$; answer each fixed range-sum query in $O(1)$.

---
## 2. Two Pointers

For a sorted array, find whether two values sum to `target`:

```cpp
int l = 0, r = n - 1;
while (l < r) {
    long long sum = a[l] + a[r];
    if (sum == target) {
        cout << "yes\n";
        break;
    }
    if (sum < target) l++;
    else r--;
}
```

The decision to move a pointer is justified by sorted order. Each pointer moves at most $n$ times, so this is $O(n)$.

---
## 3. Sliding Window

For positive numbers, find the longest subarray whose sum is at most `k`:

```cpp
long long sum = 0;
int l = 0, best = 0;
for (int r = 0; r < n; r++) {
    sum += a[r];
    while (sum > k) sum -= a[l++];
    best = max(best, r - l + 1);
}
```

> [!WARNING] Important
> This particular shrinking-window logic needs non-negative values. With negative values, shrinking may not make the sum smaller in the way the proof needs.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

How do you find the inclusive range sum from index `l` to `r` using prefix sums? :: `pref[r + 1] - pref[l]`.

Why is a two-pointer scan often $O(n)$? :: Each pointer moves in only one direction and therefore advances at most $n$ times.

When is the usual sum-based sliding window safe? :: When elements are non-negative, so removing from the left cannot increase the sum.
