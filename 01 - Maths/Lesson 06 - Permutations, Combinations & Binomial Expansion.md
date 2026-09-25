---
title: Lesson 06 - Permutations, Combinations & Binomial Expansion
subject: AL Combined Maths
unit: 06
competency: Uses fundamental counting principles, permutations, combinations, and the binomial theorem
tags:
  - AL-Maths
  - Lesson-06
  - Permutations
  - Combinations
  - BinomialTheorem
  - Flashcards
---
# Lesson 06: Permutations, Combinations & Binomial Expansion

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Fundamental Principle of Counting (Multiplication Rule & Addition Rule)
> - **Permutations ($^nP_r$)**: Arranging $r$ objects from $n$ distinct objects: $^nP_r = \frac{n!}{(n-r)!}$
> - Circular Permutations: $(n-1)!$
> - Permutations with Identical Objects: $\frac{n!}{p! q! r!}$
> - **Combinations ($^nC_r$)**: Selecting $r$ objects from $n$ distinct objects: $^nC_r = \binom{n}{r} = \frac{n!}{r!(n-r)!}$
> - Properties: $^nC_r = ^nC_{n-r}$, $^nC_r + ^nC_{r-1} = ^{n+1}C_r$ (Pascal's Identity)
> - **Binomial Theorem** for positive integer exponent $n$:
>   $$(a + b)^n = \sum_{r=0}^n \binom{n}{r} a^{n-r} b^r$$
> - General Term $T_{r+1} = \binom{n}{r} a^{n-r} b^r$. Binomial expansion for rational index $(1 + x)^n$.

---
## 1. Permutations & Combinations Summary

| Concept | Formula | Key Condition / Application |
| :--- | :--- | :--- |
| **Linear Permutation** | $^nP_r = \frac{n!}{(n-r)!}$ | Order **matters** (arrangements). |
| **Identical Objects** | $\frac{n!}{p! q! r!}$ | $p, q, r$ objects are identical. |
| **Circular Permutation** | $(n-1)!$ | Arranging $n$ objects in a circle. |
| **Combination** | $^nC_r = \frac{n!}{r!(n-r)!}$ | Order **does NOT matter** (selections). |

---
## 2. Binomial Expansion Formulas

$$(a + b)^n = \binom{n}{0} a^n + \binom{n}{1} a^{n-1}b + \binom{n}{2} a^{n-2}b^2 + \dots + \binom{n}{n} b^n$$

- **General Term ($T_{r+1}$)**: $T_{r+1} = \binom{n}{r} a^{n-r} b^r$
- **Sum of Coefficients**: $\sum_{r=0}^n \binom{n}{r} = 2^n$

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State the formula for $^nP_r$ and $^nC_r$. :: $^nP_r = \frac{n!}{(n-r)!}$ and $^nC_r = \frac{n!}{r!(n-r)!}$.

State Pascal's Identity for combinations. :: $^nC_r + ^nC_{r-1} = ^{n+1}C_r$.
<!--SR:!2026-09-26,1,230-->

What is the number of distinct circular permutations of $n$ distinct objects? :: $(n-1)!$.
<!--SR:!2026-09-26,1,230-->

What is the general term $T_{r+1}$ in the binomial expansion of $(a + b)^n$? :: $T_{r+1} = \binom{n}{r} a^{n-r} b^r$.

What is the sum of all binomial coefficients $\sum_{r=0}^n \binom{n}{r}$? :: $2^n$.
<!--SR:!2026-09-26,1,230-->