---
title: Lesson 06 - Recursion, Divide & Conquer & Backtracking
subject: Computer Science
unit: 06
competency: Design recursive state trees, prune invalid search branches, and solve backtracking problems
tags:
  - Computer-Science
  - Competitive-Programming
  - Recursion
  - Backtracking
  - DivideAndConquer
  - Flashcards
---
---
# :LiBook: Lesson 06: Recursion, Divide & Conquer & Backtracking

> [!ABSTRACT] Scope
> Master recursive state-space exploration, Divide & Conquer techniques, and prunings in Backtracking.

---
## 1. Backtracking Template: Subset Generation

Generate all $2^N$ subsets of an array:

```cpp
#include <iostream>
#include <vector>
using namespace std;

void generateSubsets(int idx, int n, vector<int>& current, const vector<int>& a) {
    if (idx == n) {
        // Base Case: Process complete subset
        cout << "{ ";
        for (int x : current) cout << x << " ";
        cout << "}\n";
        return;
    }

    // Option 1: Exclude element a[idx]
    generateSubsets(idx + 1, n, current, a);

    // Option 2: Include element a[idx]
    current.push_back(a[idx]);
    generateSubsets(idx + 1, n, current, a);
    current.pop_back(); // Backtrack state!
}
```

---
## 2. Permutation Generation with Pruning

Generate all $N!$ permutations:

```cpp
void generatePermutations(vector<int>& current, vector<bool>& used, const vector<int>& a) {
    if (current.size() == a.size()) {
        // Process permutation
        return;
    }

    for (int i = 0; i < (int)a.size(); i++) {
        if (used[i]) continue; // Prune used choices

        used[i] = true;
        current.push_back(a[i]);

        generatePermutations(current, used, a);

        current.pop_back(); // Backtrack
        used[i] = false;
    }
}
```

---
## 3. Divide & Conquer Pattern

Divide problem into subproblems, solve recursively, and combine answers (e.g. Merge Sort $O(N \log N)$):

```cpp
long long mergeSort(int l, int r, vector<int>& a) {
    if (l >= r) return 0; // Base case
    int mid = l + (r - l) / 2;
    long long inversions = 0;
    inversions += mergeSort(l, mid, a);
    inversions += mergeSort(mid + 1, r, a);
    // Combine step (merge sorted halves)
    return inversions;
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the fundamental step in Backtracking after returning from a recursive call? :: Restoring the state (e.g., `current.pop_back()` or `used[i] = false`) so other branches start with clean data.

What is the time complexity of generating all subsets vs all permutations of $N$ items? :: Subsets take $O(2^N)$ time, while permutations take $O(N!)$ time.

What are the three core steps of Divide & Conquer? :: Divide the problem into subproblems, Conquer subproblems recursively, and Combine their solutions.
