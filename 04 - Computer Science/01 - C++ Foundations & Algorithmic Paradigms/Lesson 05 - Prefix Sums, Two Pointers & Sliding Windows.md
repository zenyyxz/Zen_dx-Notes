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
> Avoid recalculating contiguous array work using 1D/2D Prefix Sums, Two Pointers, and Sliding Windows.

---
## 1. 1D & 2D Prefix Sums

### 1.1 1D Range Sum Queries
Given an array `a` of size $N$, compute range sum $a[L \dots R]$ in $O(1)$ time after $O(N)$ preprocessing.

$$\text{pref}[i] = \sum_{k=0}^{i-1} a[k], \quad \text{Sum}(L \dots R) = \text{pref}[R + 1] - \text{pref}[L]$$

```cpp
vector<long long> pref(n + 1, 0);
for (int i = 0; i < n; i++) pref[i + 1] = pref[i] + a[i];

// Range sum from index L to R (0-indexed, inclusive)
long long range_sum = pref[R + 1] - pref[L];
```

### 1.2 2D Subgrid Sum Queries
Query subgrid sum from $(r_1, c_1)$ to $(r_2, c_2)$ in $O(1)$ time:

$$\text{Sum} = \text{pref}[r_2][c_2] - \text{pref}[r_1-1][c_2] - \text{pref}[r_2][c_1-1] + \text{pref}[r_1-1][c_1-1]$$

```cpp
// Building 2D Prefix Sum Matrix (1-indexed)
vector<vector<long long>> pref(n + 1, vector<long long>(m + 1, 0));
for (int r = 1; r <= n; r++) {
    for (int c = 1; c <= m; c++) {
        pref[r][c] = grid[r-1][c-1] + pref[r-1][c] + pref[r][c-1] - pref[r-1][c-1];
    }
}

// Subgrid query from (r1, c1) to (r2, c2)
long long subgrid_sum = pref[r2][c2] - pref[r1-1][c2] - pref[r2][c1-1] + pref[r1-1][c1-1];
```

---
## 2. Two Pointers Pattern

For sorted arrays, find if two elements sum to `target` in $O(N)$ time:

```cpp
int l = 0, r = n - 1;
while (l < r) {
    long long sum = a[l] + a[r];
    if (sum == target) {
        cout << a[l] << " + " << a[r] << " = " << target << '\n';
        break;
    }
    if (sum < target) l++;
    else r--;
}
```

---
## 3. Sliding Window Pattern

Find the longest contiguous subarray with sum $\le K$ (for non-negative array elements):

```cpp
long long current_sum = 0;
int l = 0, max_len = 0;

for (int r = 0; r < n; r++) {
    current_sum += a[r];
    while (current_sum > k) {
        current_sum -= a[l++];
    }
    max_len = max(max_len, r - l + 1);
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the 1D prefix sum formula for inclusive range sum $a[L \dots R]$? :: `pref[R + 1] - pref[L]`.
<!--SR:!2026-09-26,1,230-->

What is the 2D prefix sum formula for subgrid sum $(r_1, c_1)$ to $(r_2, c_2)$? :: `pref[r2][c2] - pref[r1-1][c2] - pref[r2][c1-1] + pref[r1-1][c1-1]`.
<!--SR:!2026-09-26,1,230-->

Why must elements be non-negative for standard variable-length sliding window? :: Because shrinking the window from the left is guaranteed to decrease (or keep equal) the window sum only when values are non-negative.
<!--SR:!2026-09-26,1,230-->
