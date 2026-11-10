---
title: Sequences, Series & Mathematical Induction Guide
subject: AL Combined Maths
subtopic: Algebra
tags:
  - AL-Maths
  - Subtopic
  - Sequences
  - Series
  - MathematicalInduction
  - MethodOfDifferences
  - Flashcards
---

# :LiListOrdered: Subtopic: Sequences, Series & Mathematical Induction Guide

> [!ABSTRACT] Core Focus (NIE Teacher's Guide — Grade 13, Competencies 19, 20 & 21)
> Complete algebraic derivations of AP/GP sum formulas, algebraic proofs of $\sum r, \sum r^2, \sum r^3$ formulas, full induction proof templates for summation, divisibility, and inequalities, advanced partial fraction telescoping, and convergence evaluation of infinite series.

> [!NOTE] Parent Lesson
> [[../Lesson 05 - Sequences, Series & Mathematical Induction|Lesson 05 — Sequences, Series & Mathematical Induction]]

---

## 1. Derivations of Standard Summation Formulas

### 1.1 Derivation of $\sum_{r=1}^n r^2 = \frac{n(n+1)(2n+1)}{6}$
Consider the identity:
$$(r + 1)^3 - r^3 = 3r^2 + 3r + 1$$

Writing this identity for $r = 1, 2, 3, \dots, n$:
$$\begin{aligned}
r = 1: \quad & 2^3 - 1^3 = 3(1^2) + 3(1) + 1 \\
r = 2: \quad & 3^3 - 2^3 = 3(2^2) + 3(2) + 1 \\
r = 3: \quad & 4^3 - 3^3 = 3(3^2) + 3(3) + 1 \\
\vdots \quad & \quad \vdots \\
r = n: \quad & (n+1)^3 - n^3 = 3(n^2) + 3(n) + 1
\end{aligned}$$

Summing both columns: the left-hand side telescopes to $(n+1)^3 - 1^3$:
$$(n+1)^3 - 1 = 3 \sum_{r=1}^n r^2 + 3 \sum_{r=1}^n r + \sum_{r=1}^n 1$$
$$(n+1)^3 - 1 = 3 \sum_{r=1}^n r^2 + 3 \left[\frac{n(n+1)}{2}\right] + n$$
Expand the left-hand side:
$$(n+1)^3 - 1 = n^3 + 3n^2 + 3n$$
Rearranging for $3 \sum_{r=1}^n r^2$:
$$3 \sum_{r=1}^n r^2 = n^3 + 3n^2 + 3n - \frac{3n(n+1)}{2} - n = n^3 + 3n^2 + 2n - \frac{3n(n+1)}{2}$$
Factor out $n$:
$$= n \left[ n^2 + 3n + 2 - \frac{3(n+1)}{2} \right] = n \left[ (n+1)(n+2) - \frac{3(n+1)}{2} \right]$$
Factor out $(n+1)$:
$$= n(n+1) \left[ n + 2 - \frac{3}{2} \right] = n(n+1) \left( \frac{2n + 1}{2} \right) = \frac{n(n+1)(2n+1)}{2}$$
Dividing by 3:
$$\boxed{\sum_{r=1}^n r^2 = \frac{n(n+1)(2n+1)}{6}} \quad \blacksquare$$

---

### 1.2 Derivation of $\sum_{r=1}^n r^3 = \left[\frac{n(n+1)}{2}\right]^2$
Consider the identity:
$$(r + 1)^4 - r^4 = 4r^3 + 6r^2 + 4r + 1$$
Summing from $r = 1$ to $n$:
$$(n+1)^4 - 1^4 = 4 \sum_{r=1}^n r^3 + 6 \sum_{r=1}^n r^2 + 4 \sum_{r=1}^n r + \sum_{r=1}^n 1$$
Substitute known sums for $\sum r^2, \sum r, \sum 1$:
$$(n+1)^4 - 1 = 4 \sum_{r=1}^n r^3 + 6 \left[\frac{n(n+1)(2n+1)}{6}\right] + 4 \left[\frac{n(n+1)}{2}\right] + n$$
$$(n+1)^4 - 1 = 4 \sum_{r=1}^n r^3 + n(n+1)(2n+1) + 2n(n+1) + n$$
Simplifying and factoring yields:
$$4 \sum_{r=1}^n r^3 = n^2(n+1)^2$$
$$\boxed{\sum_{r=1}^n r^3 = \frac{n^2(n+1)^2}{4} = \left[\frac{n(n+1)}{2}\right]^2} \quad \blacksquare$$

---

## 2. Mathematical Induction Worked Exam Templates

### 2.1 Template 1: Summation Identity
**Proposition**: Prove by mathematical induction that for all $n \in \mathbb{Z}^+$:
$$\sum_{r=1}^n r(r+1) = \frac{n(n+1)(n+2)}{3}$$

**Proof**:
Let $P(n)$ be the proposition: $\sum_{r=1}^n r(r+1) = \frac{n(n+1)(n+2)}{3}$.

* **Base Step ($n = 1$)**:
  $$\text{LHS} = 1(1+1) = 2$$
  $$\text{RHS} = \frac{1(1+1)(1+2)}{3} = \frac{1 \times 2 \times 3}{3} = 2$$
  Since $\text{LHS} = \text{RHS}$, $P(1)$ is true.

* **Inductive Hypothesis**:
  Assume $P(k)$ is true for an arbitrary integer $k \ge 1$:
  $$\sum_{r=1}^k r(r+1) = \frac{k(k+1)(k+2)}{3}$$

* **Inductive Step ($n = k + 1$)**:
  We must prove $P(k+1)$: $\sum_{r=1}^{k+1} r(r+1) = \frac{(k+1)(k+2)(k+3)}{3}$.
  $$\begin{aligned}
  \sum_{r=1}^{k+1} r(r+1) &= \sum_{r=1}^k r(r+1) + (k+1)(k+2) \\
  &= \frac{k(k+1)(k+2)}{3} + (k+1)(k+2) \quad [\text{by inductive hypothesis}] \\
  &= (k+1)(k+2) \left[ \frac{k}{3} + 1 \right] \\
  &= (k+1)(k+2) \left( \frac{k+3}{3} \right) \\
  &= \frac{(k+1)(k+2)(k+3)}{3}
  \end{aligned}$$
  Thus, $P(k+1)$ is true whenever $P(k)$ is true.

* **Conclusion**:
  Since $P(1)$ is true, and $P(k) \implies P(k+1)$, by the principle of mathematical induction, $P(n)$ is true for all $n \in \mathbb{Z}^+$. $\blacksquare$

---

### 2.2 Template 2: Divisibility Statement
**Proposition**: Prove by mathematical induction that $7^n - 1$ is divisible by $6$ for all $n \in \mathbb{Z}^+$.

**Proof**:
Let $P(n)$ be the proposition that $7^n - 1$ is divisible by $6$.

* **Base Step ($n = 1$)**:
  $$7^1 - 1 = 6 = 6(1)$$
  which is divisible by $6$. Hence $P(1)$ is true.

* **Inductive Hypothesis**:
  Assume $P(k)$ is true for $k \ge 1$, so $7^k - 1 = 6M$ for some integer $M \in \mathbb{Z}$.
  Thus, $7^k = 6M + 1$.

* **Inductive Step ($n = k + 1$)**:
  Consider $7^{k+1} - 1$:
  $$7^{k+1} - 1 = 7 \cdot 7^k - 1 = 7(6M + 1) - 1 = 42M + 7 - 1 = 42M + 6 = 6(7M + 1)$$
  Since $M \in \mathbb{Z}$, $(7M + 1)$ is an integer. Thus $7^{k+1} - 1$ is divisible by $6$, and $P(k+1)$ is true.

* **Conclusion**:
  By the principle of mathematical induction, $7^n - 1$ is divisible by $6$ for all $n \in \mathbb{Z}^+$. $\blacksquare$

---

### 2.3 Template 3: Inequality Proof
**Proposition**: Prove by induction that $2^n > n^2$ for all integers $n \ge 5$.

**Proof**:
Let $P(n)$ be the statement $2^n > n^2$.

* **Base Step ($n = 5$)**:
  $$\text{LHS} = 2^5 = 32, \quad \text{RHS} = 5^2 = 25$$
  Since $32 > 25$, $P(5)$ is true.

* **Inductive Hypothesis**:
  Assume $P(k)$ is true for an integer $k \ge 5$: $2^k > k^2$.

* **Inductive Step ($n = k + 1$)**:
  We must prove $2^{k+1} > (k+1)^2 = k^2 + 2k + 1$.
  $$2^{k+1} = 2 \cdot 2^k > 2k^2 = k^2 + k^2$$
  Since $k \ge 5$, $k^2 = k \cdot k \ge 5k = 2k + 3k > 2k + 1$.
  Therefore:
  $$2^{k+1} > k^2 + (2k + 1) = (k+1)^2$$
  Thus $P(k+1)$ is true.

* **Conclusion**:
  By mathematical induction, $2^n > n^2$ for all integers $n \ge 5$. $\blacksquare$

---

## 3. Advanced Method of Differences & Telescoping

### 3.1 Worked Problem: Partial Fractions Telescoping
**Problem**: Find the sum of the series $\sum_{r=1}^n \frac{1}{(2r-1)(2r+1)(2r+3)}$ and deduce its sum to infinity.

**Solution**:
1. Express the general term $U_r$ in partial fractions:
   $$U_r = \frac{1}{(2r-1)(2r+1)(2r+3)}$$
   Notice the difference between the outer factors is $(2r+3) - (2r-1) = 4$.
   $$U_r = \frac{1}{4} \left[ \frac{(2r+3) - (2r-1)}{(2r-1)(2r+1)(2r+3)} \right] = \frac{1}{4} \left[ \frac{1}{(2r-1)(2r+1)} - \frac{1}{(2r+1)(2r+3)} \right]$$
2. Define $V_r = \frac{1}{4(2r-1)(2r+1)}$.
   Then $U_r = V_r - V_{r+1}$ where $V_{r+1} = \frac{1}{4(2r+1)(2r+3)}$.
3. **Telescoping Sum**:
   $$\sum_{r=1}^n U_r = (V_1 - V_2) + (V_2 - V_3) + \dots + (V_n - V_{n+1}) = V_1 - V_{n+1}$$
4. Calculate $V_1$ and $V_{n+1}$:
   $$V_1 = \frac{1}{4(2(1)-1)(2(1)+1)} = \frac{1}{4(1)(3)} = \frac{1}{12}$$
   $$V_{n+1} = \frac{1}{4(2n+1)(2n+3)}$$
   $$\boxed{S_n = \frac{1}{12} - \frac{1}{4(2n+1)(2n+3)}}$$
5. **Sum to Infinity**:
   As $n \to \infty$, $\lim_{n \to \infty} \frac{1}{4(2n+1)(2n+3)} = 0$.
   $$\boxed{S_\infty = \lim_{n \to \infty} S_n = \frac{1}{12}}$$

---

## 4. Problem-Solving Strategy Summary

| Series Structure | Recommended Technique | Result Form |
|---|---|---|
| Polynomial in $r$, e.g. $\sum (3r^2 - 2r + 1)$ | Expand and apply standard power sum formulas $\sum r^2, \sum r, \sum 1$ | Cubic polynomial in $n$ |
| Product of factors $\sum r(r+1)(r+2)$ | Let $V_r = r(r+1)(r+2)(r+3)$, then $U_r = \frac{1}{4}(V_r - V_{r-1})$ | $\frac{1}{4}n(n+1)(n+2)(n+3)$ |
| Reciprocal of products $\sum \frac{1}{(ar+b)(ar+a+b)}$ | Partial fraction split $U_r = V_r - V_{r+1}$ | $V_1 - V_{n+1}$ |
| Alternating signs $(-1)^r$ | Group consecutive pairs or write $r$-th term | Alternating cancellation |
| Induction statement | Identify $P(1), P(k), P(k+1)$ clearly | Complete 3-step proof |

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Derive the formula for $\sum_{r=1}^n r^2$ using the identity $(r+1)^3 - r^3 = 3r^2 + 3r + 1$. :: Summing from $r=1$ to $n$ gives $(n+1)^3 - 1 = 3\sum r^2 + 3\sum r + n$. Substituting $\sum r = \frac{n(n+1)}{2}$ and simplifying gives $\sum r^2 = \frac{n(n+1)(2n+1)}{6}$.

Derive the sum of an Arithmetic Progression $S_n = \frac{n}{2}[2a + (n-1)d]$. :: Write $S_n = a + (a+d) + \dots + l$ and reverse as $S_n = l + (l-d) + \dots + a$. Adding both equations gives $2S_n = n(a+l) = n[2a+(n-1)d]$, so $S_n = \frac{n}{2}[2a + (n-1)d]$.

Derive the sum of a Geometric Progression $S_n = \frac{a(1 - r^n)}{1 - r}$ for $r \ne 1$. :: $S_n = a + ar + \dots + ar^{n-1}$ and $rS_n = ar + ar^2 + \dots + ar^n$. Subtracting yields $(1 - r)S_n = a - ar^n = a(1 - r^n)$, so $S_n = \frac{a(1 - r^n)}{1 - r}$.

Why is the sum to infinity of a GP only valid when $|r| < 1$? :: Because when $|r| < 1$, $\lim_{n \to \infty} r^n = 0$, giving a finite limit $S_\infty = \frac{a}{1 - r}$; if $|r| \ge 1$, $r^n$ does not vanish and the series diverges.

What is the general expression for $\sum_{r=1}^n r(r+1)(r+2)$ using the method of differences? :: Let $V_r = r(r+1)(r+2)(r+3)$, then $V_r - V_{r-1} = 4r(r+1)(r+2) \implies S_n = \frac{1}{4}V_n = \frac{1}{4}n(n+1)(n+2)(n+3)$.

How do you decompose $\frac{1}{r(r+1)(r+2)}$ into the form $V_r - V_{r+1}$? :: Multiply by $[(r+2) - r]/2$: $U_r = \frac{1}{2}\left[\frac{1}{r(r+1)} - \frac{1}{(r+1)(r+2)}\right]$, where $V_r = \frac{1}{2r(r+1)}$.

What is the sum to infinity of $\sum_{r=1}^\infty \frac{1}{(2r-1)(2r+1)}$? :: $U_r = \frac{1}{2}\left[\frac{1}{2r-1} - \frac{1}{2r+1}\right] \implies S_n = \frac{1}{2}\left[1 - \frac{1}{2n+1}\right]$. As $n \to \infty$, $S_\infty = \frac{1}{2}$.

How is the inductive step executed when proving $\sum_{r=1}^n f(r) = F(n)$? :: Add $f(k+1)$ to the inductive hypothesis $F(k)$: verify algebraically that $F(k) + f(k+1) = F(k+1)$.

Prove that the AM of two positive numbers is greater than or equal to their GM. :: $(\sqrt{a} - \sqrt{b})^2 \ge 0 \implies a - 2\sqrt{ab} + b \ge 0 \implies a + b \ge 2\sqrt{ab} \implies \frac{a+b}{2} \ge \sqrt{ab}$.

How is $3^{2n} - 1$ shown to be divisible by 8 using mathematical induction? :: For $n=1$, $3^2 - 1 = 8$ (divisible). Assume $3^{2k} - 1 = 8M$. Then $3^{2(k+1)} - 1 = 9 \cdot 3^{2k} - 1 = 9(8M + 1) - 1 = 72M + 8 = 8(9M + 1)$, which is divisible by 8.

What is the sum $\sum_{r=1}^n (2r - 1)$ of the first $n$ odd positive integers? :: $2\sum r - \sum 1 = 2\left[\frac{n(n+1)}{2}\right] - n = n^2 + n - n = n^2$.

What is the relationship between the convergence of $S_n = V_1 - V_{n+1}$ and the limit of $V_n$? :: The series converges if and only if $\lim_{n \to \infty} V_{n+1} = L$ is finite, in which case $S_\infty = V_1 - L$.
