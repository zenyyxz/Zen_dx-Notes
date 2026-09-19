---
title: Lesson 04 - Sorting, Searching & Binary Search
subject: Computer Science
unit: 04
competency: Implement binary search on discrete ranges and monotonic predicate functions
tags:
  - Computer-Science
  - Competitive-Programming
  - Searching
  - BinarySearch
  - Sorting
  - Flashcards
---
---
# :LiBook: Lesson 04: Sorting, Searching & Binary Search

> [!ABSTRACT] Scope
> Master array sorting, built-in binary search functions (`lower_bound`, `upper_bound`), and the Binary Search on Answer technique.

---
## 1. Built-in STL Binary Search Functions

Binary search functions require the input container to be **sorted**.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> a = {1, 3, 3, 5, 7, 9};

    // 1. Check existence: O(log N)
    bool found = binary_search(a.begin(), a.end(), 5); // true

    // 2. lower_bound: First element >= target
    auto it1 = lower_bound(a.begin(), a.end(), 3);
    int idx1 = distance(a.begin(), it1); // Index 1

    // 3. upper_bound: First element > target
    auto it2 = upper_bound(a.begin(), a.end(), 3);
    int idx2 = distance(a.begin(), it2); // Index 3

    // Count occurrences of 3: upper_bound - lower_bound
    int count = distance(it1, it2); // 2
}
```

---
## 2. Binary Search on Answer Template

When a problem asks to find the *maximum minimum* or *minimum maximum* value, check if the feasibility function `check(x)` is **monotonic** (`TTTTFFFF` or `FFFFTTTT`).

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Monotonic Predicate Function
bool check(long long val, int k, const vector<int>& a) {
    // Return true if 'val' is achievable, false otherwise
    int count = 0;
    for (int x : a) {
        count += x / val;
    }
    return count >= k;
}

long long solveBinarySearch(int k, const vector<int>& a) {
    long long low = 1, high = 1e18;
    long long ans = -1;

    while (low <= high) {
        long long mid = low + (high - low) / 2; // Prevents overflow

        if (check(mid, k, a)) {
            ans = mid;       // 'mid' is feasible; record answer
            low = mid + 1;   // Try to find a larger feasible value
        } else {
            high = mid - 1;  // 'mid' is too large; reduce search space
        }
    }
    return ans;
}
```

> [!WARNING] Overflow Avoidance
> Avoid writing `mid = (low + high) / 2;` because `low + high` can overflow `long long` when bounds are around $10^{18}$. Always use `mid = low + (high - low) / 2;`.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the difference between `lower_bound` and `upper_bound`? :: `lower_bound` returns an iterator to the first element $\ge$ target, while `upper_bound` returns an iterator to the first element strictly $>$ target.

What property must a problem possess to apply Binary Search on Answer? :: Monotonicity — the predicate function `check(x)` must transition cleanly from `true` to `false` (or `false` to `true`).

Why write `low + (high - low) / 2` instead of `(low + high) / 2`? :: To prevent integer overflow when `low + high` exceeds the maximum capacity of the integer type.
