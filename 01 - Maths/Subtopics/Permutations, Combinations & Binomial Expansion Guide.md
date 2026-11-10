---
title: Permutations, Combinations & Binomial Expansion Guide
subject: AL Combined Maths
subtopic: Algebra
tags:
  - AL-Maths
  - Subtopic
  - Permutations
  - Combinations
  - BinomialTheorem
  - CountingMethods
  - Flashcards
---

# :LiBinary: Subtopic: Permutations, Combinations & Binomial Expansion Guide

> [!ABSTRACT] Core Focus (NIE Teacher's Guide — Grade 13, Competencies 22 & 24)
> Rigorous algebraic proofs of Pascal's identity, formal induction proof of the Binomial Theorem, advanced grouping and gap problem-solving techniques for permutations, and step-by-step evaluation of binomial coefficients and independent terms.

> [!NOTE] Parent Lesson
> [[../Lesson 06 - Permutations, Combinations & Binomial Expansion|Lesson 06 — Permutations, Combinations & Binomial Expansion]]

---

## 1. Rigorous Algebraic Proofs

### 1.1 Proof of Pascal's Identity
**Theorem**: For any positive integers $n$ and $r$ ($1 \le r \le n$):
$$\binom{n}{r} + \binom{n}{r-1} = \binom{n+1}{r}$$

**Algebraic Proof**:
By definition of combinations:
$$\binom{n}{r} = \frac{n!}{r!(n-r)!} \quad \text{and} \quad \binom{n}{r-1} = \frac{n!}{(r-1)!(n - r + 1)!}$$

Combine over a common denominator.
Note that $r! = r \cdot (r-1)!$ and $(n - r + 1)! = (n - r + 1) \cdot (n - r)!$.
The least common denominator is $r! (n - r + 1)!$:
$$\begin{aligned}
\binom{n}{r} + \binom{n}{r-1} &= \frac{n!(n - r + 1)}{r!(n - r + 1)(n - r)!} + \frac{n! \cdot r}{r \cdot (r-1)!(n - r + 1)!} \\
&= \frac{n!(n - r + 1)}{r!(n - r + 1)!} + \frac{n! \cdot r}{r!(n - r + 1)!} \\
&= \frac{n![(n - r + 1) + r]}{r!(n - r + 1)!} \\
&= \frac{n!(n + 1)}{r!(n + 1 - r)!} \\
&= \frac{(n + 1)!}{r!((n + 1) - r)!} \\
&= \binom{n+1}{r} \quad \blacksquare
\end{aligned}$$

---

### 1.2 Proof of the Binomial Theorem by Mathematical Induction
**Theorem**: For all $n \in \mathbb{Z}^+$:
$$(a + b)^n = \sum_{r=0}^n \binom{n}{r} a^{n-r} b^r$$

**Proof**:
Let $P(n)$ be the proposition that the identity holds.

* **Base Step ($n = 1$)**:
  $$\text{LHS} = (a + b)^1 = a + b$$
  $$\text{RHS} = \binom{1}{0} a^1 b^0 + \binom{1}{1} a^0 b^1 = 1 \cdot a + 1 \cdot b = a + b$$
  Since $\text{LHS} = \text{RHS}$, $P(1)$ is true.

* **Inductive Hypothesis**:
  Assume $P(k)$ is true for an arbitrary integer $k \ge 1$:
  $$(a + b)^k = \sum_{r=0}^k \binom{k}{r} a^{k-r} b^r = \binom{k}{0} a^k + \binom{k}{1} a^{k-1}b + \dots + \binom{k}{k} b^k$$

* **Inductive Step ($n = k + 1$)**:
  Multiply $(a + b)^k$ by $(a + b)$:
  $$(a + b)^{k+1} = (a + b) (a + b)^k = (a + b) \left[ \sum_{r=0}^k \binom{k}{r} a^{k-r} b^r \right]$$
  $$= a \left[ \sum_{r=0}^k \binom{k}{r} a^{k-r} b^r \right] + b \left[ \sum_{r=0}^k \binom{k}{r} a^{k-r} b^r \right]$$
  $$= \sum_{r=0}^k \binom{k}{r} a^{k+1-r} b^r + \sum_{r=0}^k \binom{k}{r} a^{k-r} b^{r+1}$$
  Expand and group terms with matching powers $a^{k+1-r} b^r$:
  $$= \binom{k}{0} a^{k+1} + \sum_{r=1}^k \left[ \binom{k}{r} + \binom{k}{r-1} \right] a^{k+1-r} b^r + \binom{k}{k} b^{k+1}$$
  Using Pascal's identity $\binom{k}{r} + \binom{k}{r-1} = \binom{k+1}{r}$, and noting that $\binom{k}{0} = \binom{k+1}{0} = 1$ and $\binom{k}{k} = \binom{k+1}{k+1} = 1$:
  $$= \binom{k+1}{0} a^{k+1} + \sum_{r=1}^k \binom{k+1}{r} a^{k+1-r} b^r + \binom{k+1}{k+1} b^{k+1} = \sum_{r=0}^{k+1} \binom{k+1}{r} a^{k+1-r} b^r$$
  Thus, $P(k+1)$ is true whenever $P(k)$ is true.

* **Conclusion**:
  By the principle of mathematical induction, the theorem is true for all $n \in \mathbb{Z}^+$. $\blacksquare$

---

## 2. Advanced Permutation Problem Patterns

### 2.1 The Grouping (Tie) Method
**Problem**: In how many ways can 4 boys and 3 girls be seated in a row if all 3 girls must sit together?

**Solution**:
1. Treat the 3 girls as a **single block** $(G_1, G_2, G_3)$.
2. Now we have 4 boys + 1 girl-block = **5 items** to arrange in a row:
   $$\text{Ways to arrange 5 items} = 5! = 120$$
3. Within their block, the 3 girls can be arranged among themselves in:
   $$3! = 6 \text{ ways}$$
4. By the multiplication principle:
   $$\text{Total ways} = 5! \times 3! = 120 \times 6 = \boxed{720}$$

---

### 2.2 The Gap Method (Separation Problem)
**Problem**: In how many ways can 4 boys and 3 girls be seated in a row if no two girls may sit together?

**Solution**:
1. Seat the unrestricted individuals (the 4 boys) first in a row:
   $$\text{Ways to arrange 4 boys} = 4! = 24$$
2. The 4 boys create **5 gaps** (including both ends):
   $$\_ \; B_1 \; \_ \; B_2 \; \_ \; B_3 \; \_ \; B_4 \; \_$$
3. To ensure no two girls are adjacent, each girl must occupy a distinct gap.
   Select and arrange 3 gaps from the 5 available gaps for the 3 girls:
   $$^5P_3 = \frac{5!}{(5-3)!} = \frac{120}{2} = 60 \text{ ways}$$
4. By the multiplication principle:
   $$\text{Total ways} = 4! \times ^5P_3 = 24 \times 60 = \boxed{1440}$$

---

### 2.3 Letters of a Word with Repeated Letters
**Problem**: Find the number of distinct permutations of the letters of the word **MATHEMATICS**. How many begin with M and end with S?

**Solution**:
1. Total letters in MATHEMATICS = $11$.
   Letter frequencies: M: 2, A: 2, T: 2, H: 1, E: 1, I: 1, C: 1, S: 1.
   $$\text{Total permutations} = \frac{11!}{2! \, 2! \, 2!} = \frac{39,916,800}{8} = \boxed{4,989,600}$$
2. Beginning with M and ending with S:
   Fix M at the first position and S at the last position.
   Remaining 9 letters to arrange: M (1), A (2), T (2), H (1), E (1), I (1), C (1).
   $$\text{Restricted permutations} = \frac{9!}{1! \, 2! \, 2!} = \frac{362,880}{4} = \boxed{90,720}$$

---

## 3. Binomial Expansion Worked Problems

### 3.1 Term Independent of $x$
**Problem**: Find the term independent of $x$ in the expansion of $\left(2x^2 - \frac{1}{x}\right)^9$.

**Solution**:
1. General term $T_{r+1}$ for $(a + b)^n$ with $a = 2x^2$, $b = -x^{-1}$, $n = 9$:
   $$T_{r+1} = \binom{9}{r} (2x^2)^{9-r} (-x^{-1})^r$$
   $$= \binom{9}{r} 2^{9-r} (x^2)^{9-r} (-1)^r x^{-r}$$
   $$= \binom{9}{r} (-1)^r 2^{9-r} x^{18 - 2r - r} = \binom{9}{r} (-1)^r 2^{9-r} x^{18 - 3r}$$
2. For the term independent of $x$, set the exponent of $x$ to $0$:
   $$18 - 3r = 0 \implies 3r = 18 \implies r = 6$$
3. Since $r = 6$ is an integer ($0 \le 6 \le 9$), the term is $T_7$:
   $$T_7 = \binom{9}{6} (-1)^6 2^{9-6} = \binom{9}{3} (1) 2^3 = \frac{9 \times 8 \times 7}{3 \times 2 \times 1} \times 8 = 84 \times 8 = \boxed{672}$$

---

### 3.2 Greatest Coefficient in an Expansion
**Problem**: Find the greatest binomial coefficient in $(1 + x)^{10}$.

**Solution**:
The coefficients are $\binom{10}{r}$ for $r = 0, 1, \dots, 10$.
Since $n = 10$ is even, the maximum occurs at the central term $r = \frac{n}{2} = 5$:
$$\text{Greatest coefficient} = \binom{10}{5} = \frac{10 \times 9 \times 8 \times 7 \times 6}{5 \times 4 \times 3 \times 2 \times 1} = \boxed{252}$$

---

## 4. Problem-Solving Strategy Guide

| Question Type | Primary Technique | Essential Check |
|---|---|---|
| Order matters (arranging people, digits, words) | Permutations ($^nP_r$ or $\frac{n!}{p!q!}$) | Are items distinct or repeated? |
| Order does not matter (selecting teams, committees) | Combinations ($^nC_r$) | Is order relevant to the outcome? |
| Specific items must stay together | Block / Grouping Method | Multiply by internal arrangements of the block |
| Specific items must be separated | Gap Method | Arrange unrestricted items first to create gaps |
| Term independent of $x$ | Set exponent in $T_{r+1}$ equal to 0 | Must yield an integer $r \in [0, n]$ |
| Coefficient identities | Substitute $x = 1$ or $x = -1$ into $(1 + x)^n$ | Compare real/imaginary parts if complex |

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Prove Pascal's Identity $\binom{n}{r} + \binom{n}{r-1} = \binom{n+1}{r}$ algebraically. :: Express with common denominator $r!(n-r+1)!$: $\frac{n!(n-r+1) + n!r}{r!(n-r+1)!} = \frac{n!(n+1)}{r!(n+1-r)!} = \frac{(n+1)!}{r!(n+1-r)!} = \binom{n+1}{r}$.

How is the grouping (block) method applied when $k$ specific objects must be together in a linear permutation of $n$ objects? :: Treat the $k$ objects as 1 combined unit; arrange the $(n - k + 1)$ items in $(n - k + 1)!$ ways, then multiply by $k!$ for the internal arrangements of the block: $(n - k + 1)! \times k!$.

How is the gap method applied when $k$ items must not be adjacent among $m$ unrestricted items? :: Arrange the $m$ unrestricted items first in $m!$ ways, creating $(m + 1)$ available gaps. Then place the $k$ restricted items into these gaps in $^{m+1}P_k$ ways: $m! \times ^{m+1}P_k$.

How many distinct permutations can be formed from the letters of the word 'STATISTICS'? :: Total 10 letters: S: 3, T: 3, A: 1, I: 2, C: 1. Permutations $= \frac{10!}{3! \, 3! \, 2!} = \frac{3,628,800}{6 \times 6 \times 2} = 50,400$.

What is the general term $T_{r+1}$ in the expansion of $\left(x^2 - \frac{2}{x}\right)^n$? :: $T_{r+1} = \binom{n}{r} (x^2)^{n-r} \left(-\frac{2}{x}\right)^r = \binom{n}{r} (-2)^r x^{2n - 3r}$.

How do you find the term independent of $x$ in $\left(x^2 - \frac{2}{x}\right)^n$? :: Set the power of $x$ to zero: $2n - 3r = 0 \implies r = \frac{2n}{3}$. If $r$ is an integer, compute $T_{r+1}$; if not, no independent term exists.

What is the sum of coefficients in the expansion of $(2x - 3y)^5$? :: Substitute $x = 1, y = 1$: $(2(1) - 3(1))^5 = (-1)^5 = -1$.

What is the inductive step in proving the Binomial Theorem $(a + b)^n = \sum_{r=0}^n \binom{n}{r} a^{n-r} b^r$? :: Multiply the hypothesis $(a + b)^k$ by $(a + b)$, expand into two sums, and combine like powers $a^{k+1-r}b^r$ using Pascal's identity $\binom{k}{r} + \binom{k}{r-1} = \binom{k+1}{r}$.

In how many ways can a committee of 3 men and 2 women be chosen from 7 men and 5 women? :: $\binom{7}{3} \times \binom{5}{2} = \frac{7 \times 6 \times 5}{3 \times 2 \times 1} \times \frac{5 \times 4}{2 \times 1} = 35 \times 10 = 350$.

What is the number of circular permutations of 6 distinct persons around a round table? :: $(6 - 1)! = 5! = 120$.

Why is the number of arrangements of beads on a necklace $\frac{(n-1)!}{2}$? :: Because flipping the necklace over makes clockwise and counter-clockwise arrangements identical, halving the $(n-1)!$ circular arrangements.

What is the greatest term in the expansion of $(1 + x)^n$ if $x = 1$? :: The middle term(s), which have the greatest binomial coefficient: $\binom{n}{n/2}$ if $n$ is even, or $\binom{n}{\frac{n-1}{2}}$ and $\binom{n}{\frac{n+1}{2}}$ if $n$ is odd.
