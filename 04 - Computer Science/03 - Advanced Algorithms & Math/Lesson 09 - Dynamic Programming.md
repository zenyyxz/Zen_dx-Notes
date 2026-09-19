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
> Dynamic programming (DP) stores answers to repeated subproblems. The difficult part is not coding—it is defining exactly what each state means.

---
## 1. A DP Recipe

1. Define `dp[state]` in one precise sentence.
2. Find the final state(s) that answer the problem.
3. List the last decision before each state.
4. Write the transition from smaller states.
5. Set base cases.
6. Check time: number of states × work per transition.

---
## 2. Example: Maximum Non-Adjacent Sum

Let `dp[i]` be the maximum sum using the first `i` elements (`a[0]` through `a[i-1]`) with no adjacent picks.

$$
dp[i]=\max(dp[i-1],\ dp[i-2]+a[i-1]).
$$

```cpp
vector<long long> dp(n + 1, 0);
if (n >= 1) dp[1] = max(0, a[0]);
for (int i = 2; i <= n; i++) {
    dp[i] = max(dp[i - 1], dp[i - 2] + a[i - 1]);
}
cout << dp[n] << '\n';
```

The two choices are exhaustive: either element `i-1` is skipped, or it is chosen and the previous one must be skipped.

---
## 3. Memoisation vs Tabulation

- **Memoisation:** recursive, calculate a state only when needed.
- **Tabulation:** iterative, fill states in dependency order.

Use whichever makes dependencies clearer. In C++, iterative DP avoids recursion-depth issues for large state spaces.

---
## 4. Common DP Shapes

- `dp[i]`: prefixes, paths, one-dimensional processes.
- `dp[i][j]`: grids, two strings, intervals.
- `dp[mask]`: subsets; feasible only for small (n).
- `dp[node][state]`: trees or graphs with a local state.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the first thing to write for a DP solution? :: A precise sentence defining what each DP state represents.

What causes DP to be useful? :: Overlapping subproblems whose answers can be stored and reused.

How do you estimate DP complexity? :: Number of states multiplied by the work needed for each transition.
