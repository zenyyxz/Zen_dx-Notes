---
title: Lesson 09 - Dynamic Programming
subject: Computer Science
unit: 09
competency: Define states and transitions to reuse solutions of overlapping subproblems
tags:
  - Computer-Science
  - Competitive-Programming
  - DynamicProgramming
  - DP
  - Flashcards
---
---
# :LiBook: Lesson 09: Dynamic Programming

> [!ABSTRACT] Scope
> Dynamic Programming (DP) optimizes recursive problems by storing solutions to overlapping subproblems. Master state definitions, transitions, and space optimizations.

---
## 1. The 5-Step DP Design Framework

1. **State Definition**: Define `dp[i]` (or `dp[i][j]`) in one clear sentence.
2. **Base Cases**: Set starting values (e.g. `dp[0] = 0`).
3. **Transition Relation**: Express state `dp[i]` in terms of smaller states.
4. **Order of Computation**: Ensure subproblem states are computed before dependent states (Tabulation vs Memoisation).
5. **Final Answer Location**: Identify which state stores the final answer.

---
## 2. Classic Example 1: 0/1 Knapsack Problem

**Problem**: Select items with weight $W_i$ and value $V_i$ to maximize total value within capacity $C$.

**State**: `dp[w]` = Maximum value achievable with exact total weight capacity $w$.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int knapsack01(int capacity, const vector<int>& weights, const vector<int>& values) {
    int n = weights.size();
    // 1D Space-Optimized DP array
    vector<int> dp(capacity + 1, 0);

    for (int i = 0; i < n; i++) {
        // Traverse backwards to prevent using the same item multiple times!
        for (int w = capacity; w >= weights[i]; w--) {
            dp[w] = max(dp[w], dp[w - weights[i]] + values[i]);
        }
    }
    return dp[capacity];
}
```

---
## 3. Classic Example 2: Coin Change (Minimum Coins)

**State**: `dp[x]` = Minimum number of coins to form sum $x$.

$$\text{dp}[x] = \min_{c \in \text{coins}} (\text{dp}[x - c] + 1)$$

```cpp
int minCoins(int target, const vector<int>& coins) {
    const int INF = 1e9;
    vector<int> dp(target + 1, INF);
    dp[0] = 0; // Base case: 0 coins for sum 0

    for (int x = 1; x <= target; x++) {
        for (int c : coins) {
            if (x - c >= 0) {
                dp[x] = min(dp[x], dp[x - c] + 1);
            }
        }
    }
    return (dp[target] == INF) ? -1 : dp[target];
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why iterate backwards over capacity $W$ in 1D array 0/1 Knapsack DP? :: To ensure each item is used at most once (iterating forwards allows multiple picks of the same item, which solves Unbounded Knapsack instead).

What is the first step when designing a Dynamic Programming solution? :: Define the state `dp[...]` in one precise sentence.

How do you calculate total DP time complexity? :: Total States $\times$ Time per Transition.
