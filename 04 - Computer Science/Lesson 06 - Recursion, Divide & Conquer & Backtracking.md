---
title: Lesson 06 - Recursion, Divide & Conquer & Backtracking
subject: Computer Science
unit: 06
competency: Model problems recursively and explore small search spaces safely
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
> Recursion solves a problem by solving smaller versions of it. Backtracking systematically tries choices; pruning removes choices that cannot help.

---
## 1. The Three Parts of a Recursive Function

Every recursive function needs:

1. a clear meaning—what does `f(state)` return or do?
2. a base case—when does it stop?
3. progress—why is the next call smaller or closer to the base case?

```cpp
long long power(long long a, long long e) {
    if (e == 0) return 1;
    long long half = power(a, e / 2);
    long long ans = half * half;
    if (e % 2) ans *= a;
    return ans;
}
```

This is divide and conquer: exponentiation takes $O(\log e)$, not $O(e)$.

---
## 2. Backtracking Example: Generate All Subsets

```cpp
void generate(int i, const vector<int>& a, vector<int>& chosen) {
    if (i == (int)a.size()) {
        // use or print chosen
        return;
    }

    generate(i + 1, a, chosen);          // do not choose a[i]
    chosen.push_back(a[i]);               // choose a[i]
    generate(i + 1, a, chosen);
    chosen.pop_back();                    // undo before returning
}
```

There are $2^n$ subsets, so this is for small (n). The `pop_back()` is the “backtrack” step.

---
## 3. Pruning

Prune only when you can prove a branch cannot produce a valid or better answer. Examples:

- a partial sum already exceeds a required limit when all remaining values are non-negative;
- a choice violates a constraint immediately;
- a partial solution is worse than a known answer under a valid bound.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What are the three essentials of recursion? :: A clear state meaning, a base case, and a recursive step that makes progress.

What does backtracking do after exploring a choice? :: It undoes the choice so other branches begin from the correct previous state.

How many subsets does $n$-element set have? :: $2^n$.
