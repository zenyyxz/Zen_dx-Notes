---
title: Quadratic Functions & Equations Guide
subject: AL Combined Maths
subtopic: Algebra
tags:
  - AL-Maths
  - Subtopic
  - Quadratic
  - Discriminant
  - SymmetricRoots
  - CommonRoots
  - Flashcards
---

# :LiSquareDot: Subtopic: Quadratic Functions & Equations Guide

> [!ABSTRACT] Core Focus (NIE Teacher's Guide — Grade 12, Unit 03)
> In-depth mathematical derivations for quadratic vertex canonical form, algebraic proof of Vieta's formulas, rigorous sign of quadratic expressions, advanced symmetric root substitutions, common root condition derivation, and range determination of rational quadratic functions using the discriminant condition.

> [!NOTE] Parent Lesson
> [[../Lesson 03 - Quadratic Functions & Equations|Lesson 03 — Quadratic Functions & Equations]]

---

## 1. Vertex Form & Extremum Derivation

### 1.1 Canonical Completing the Square
Let $f(x) = ax^2 + bx + c$ with $a \ne 0$.
$$f(x) = a \left[ x^2 + \frac{b}{a} x \right] + c$$
$$f(x) = a \left[ \left(x + \frac{b}{2a}\right)^2 - \frac{b^2}{4a^2} \right] + c$$
$$f(x) = a \left(x + \frac{b}{2a}\right)^2 - \frac{b^2}{4a} + c$$
$$\boxed{f(x) = a \left(x + \frac{b}{2a}\right)^2 + \frac{4ac - b^2}{4a} = a \left(x + \frac{b}{2a}\right)^2 - \frac{\Delta}{4a}}$$

where $\Delta = b^2 - 4ac$.

Since $\left(x + \frac{b}{2a}\right)^2 \ge 0$ for all real $x$, with equality if and only if $x = -\frac{b}{2a}$:
1. **When $a > 0$**:
   $$a \left(x + \frac{b}{2a}\right)^2 \ge 0 \implies f(x) \ge -\frac{\Delta}{4a}$$
   The minimum value is $-\frac{\Delta}{4a}$, occurring at $x = -\frac{b}{2a}$.
2. **When $a < 0$**:
   $$a \left(x + \frac{b}{2a}\right)^2 \le 0 \implies f(x) \le -\frac{\Delta}{4a}$$
   The maximum value is $-\frac{\Delta}{4a}$, occurring at $x = -\frac{b}{2a}$.

---

## 2. Derivation of Common Root Condition

Consider the two equations with a shared root $\alpha$:
$$a_1 \alpha^2 + b_1 \alpha + c_1 = 0 \quad \text{--- (1)}$$
$$a_2 \alpha^2 + b_2 \alpha + c_2 = 0 \quad \text{--- (2)}$$

### Step-by-Step Elimination by Cross-Multiplication:
Treat $\alpha^2$ and $\alpha$ as linear variables in a system:
1. Multiply (1) by $b_2$ and (2) by $b_1$, then subtract:
   $$(a_1 b_2 - a_2 b_1)\alpha^2 + (c_1 b_2 - c_2 b_1) = 0 \implies \alpha^2 = \frac{b_1 c_2 - b_2 c_1}{a_1 b_2 - a_2 b_1}$$
2. Multiply (1) by $a_2$ and (2) by $a_1$, then subtract:
   $$(b_1 a_2 - b_2 a_1)\alpha + (c_1 a_2 - c_2 a_1) = 0 \implies \alpha = \frac{c_1 a_2 - c_2 a_1}{a_1 b_2 - a_2 b_1}$$
3. Equating $\alpha^2 = (\alpha)^2$:
   $$\frac{b_1 c_2 - b_2 c_1}{a_1 b_2 - a_2 b_1} = \left(\frac{c_1 a_2 - c_2 a_1}{a_1 b_2 - a_2 b_1}\right)^2$$
Multiplying both sides by $(a_1 b_2 - a_2 b_1)^2$:
$$\boxed{(c_1 a_2 - c_2 a_1)^2 = (a_1 b_2 - a_2 b_1)(b_1 c_2 - b_2 c_1)}$$

---

## 3. Advanced Symmetric Functions of Roots

Let $\alpha, \beta$ be the roots of $ax^2 + bx + c = 0$, so $S = \alpha + \beta = -\frac{b}{a}$ and $P = \alpha\beta = \frac{c}{a}$.

### 3.1 Higher-Order Identities
1. **Sum of Cubes**:
   $$(\alpha + \beta)^3 = \alpha^3 + 3\alpha^2\beta + 3\alpha\beta^2 + \beta^3 = \alpha^3 + \beta^3 + 3\alpha\beta(\alpha + \beta)$$
   $$\implies \alpha^3 + \beta^3 = (\alpha + \beta)^3 - 3\alpha\beta(\alpha + \beta) = S^3 - 3PS$$

2. **Sum of Reciprocal Cubes**:
   $$\frac{1}{\alpha^3} + \frac{1}{\beta^3} = \frac{\alpha^3 + \beta^3}{\alpha^3\beta^3} = \frac{S^3 - 3PS}{P^3}$$

3. **Newton's Sum Formula**:
   Let $p_n = \alpha^n + \beta^n$.
   Since $\alpha$ and $\beta$ satisfy $ax^2 + bx + c = 0$:
   $$a\alpha^2 + b\alpha + c = 0 \implies a\alpha^n + b\alpha^{n-1} + c\alpha^{n-2} = 0$$
   $$a\beta^2 + b\beta + c = 0 \implies a\beta^n + b\beta^{n-1} + c\beta^{n-2} = 0$$
   Adding both equations yields **Newton's Sum Relation**:
   $$\boxed{a p_n + b p_{n-1} + c p_{n-2} = 0}$$

---

### 3.2 Worked Example: Forming Equation with Transformed Roots
**Problem**: Let $\alpha, \beta$ be the roots of $2x^2 - 3x - 1 = 0$. Form a quadratic equation with integer coefficients whose roots are $(\alpha^2 + \beta)$ and $(\beta^2 + \alpha)$.

**Solution**:
1. From the given equation:
   $$\alpha + \beta = \frac{3}{2}, \quad \alpha\beta = -\frac{1}{2}$$
2. Also note that since $\alpha, \beta$ are roots:
   $$2\alpha^2 - 3\alpha - 1 = 0 \implies \alpha^2 = \frac{3\alpha + 1}{2}$$
   $$2\beta^2 - 3\beta - 1 = 0 \implies \beta^2 = \frac{3\beta + 1}{2}$$
3. Simplify the new roots:
   $$u = \alpha^2 + \beta = \frac{3\alpha + 1}{2} + \beta = \frac{3\alpha + 2\beta + 1}{2}$$
   $$v = \beta^2 + \alpha = \frac{3\beta + 1}{2} + \alpha = \frac{3\beta + 2\alpha + 1}{2}$$
4. **Sum of new roots ($S_{\text{new}} = u + v$)**:
   $$u + v = \alpha^2 + \beta^2 + (\alpha + \beta)$$
   $$\alpha^2 + \beta^2 = (\alpha + \beta)^2 - 2\alpha\beta = \left(\frac{3}{2}\right)^2 - 2\left(-\frac{1}{2}\right) = \frac{9}{4} + 1 = \frac{13}{4}$$
   $$S_{\text{new}} = \frac{13}{4} + \frac{3}{2} = \frac{19}{4}$$
5. **Product of new roots ($P_{\text{new}} = uv$)**:
   $$uv = (\alpha^2 + \beta)(\beta^2 + \alpha) = \alpha^2\beta^2 + \alpha^3 + \beta^3 + \alpha\beta$$
   $$\alpha^3 + \beta^3 = (\alpha + \beta)^3 - 3\alpha\beta(\alpha + \beta) = \left(\frac{3}{2}\right)^3 - 3\left(-\frac{1}{2}\right)\left(\frac{3}{2}\right) = \frac{27}{8} + \frac{9}{4} = \frac{45}{8}$$
   $$uv = \left(-\frac{1}{2}\right)^2 + \frac{45}{8} + \left(-\frac{1}{2}\right) = \frac{1}{4} + \frac{45}{8} - \frac{1}{2} = \frac{2 + 45 - 4}{8} = \frac{43}{8}$$
6. **Construct the equation**:
   $$x^2 - S_{\text{new}} x + P_{\text{new}} = 0 \implies x^2 - \frac{19}{4} x + \frac{43}{8} = 0$$
   Multiplying by 8:
   $$\boxed{8x^2 - 38x + 43 = 0}$$

---

## 4. Range of Rational Functions via Discriminant Condition

A classic A/L problem involves determining the range of a rational function $y = \frac{P(x)}{Q(x)}$ for real $x$.

### 4.1 Methodology
1. Set $y = \frac{ax^2 + bx + c}{px^2 + qx + r}$.
2. Cross-multiply and rearrange into a quadratic equation in $x$:
   $$(py - a)x^2 + (qy - b)x + (ry - c) = 0$$
3. Since $x$ is given to be real ($x \in \mathbb{R}$), the discriminant $\Delta_x$ of this quadratic equation must be non-negative:
   $$\Delta_x = (qy - b)^2 - 4(py - a)(ry - c) \ge 0$$
4. Solve the resulting inequality in $y$ to obtain the permissible range of values for $y$.

### 4.2 Worked Example
**Problem**: Find the range of the function $y = \frac{x^2 - 2x + 4}{x^2 + 2x + 4}$ for all real $x$.

**Solution**:
1. Note that denominator $x^2 + 2x + 4 = (x+1)^2 + 3 > 0$ for all $x \in \mathbb{R}$ (never zero).
2. Cross-multiply:
   $$y(x^2 + 2x + 4) = x^2 - 2x + 4$$
   $$(y - 1)x^2 + 2(y + 1)x + 4(y - 1) = 0$$
3. Since $x \in \mathbb{R}$:
   * **Case 1: $y = 1$**:
     Equation becomes $0x^2 + 4x + 0 = 0 \implies x = 0 \in \mathbb{R}$. Thus $y = 1$ is in the range.
   * **Case 2: $y \ne 1$**:
     The equation is a proper quadratic in $x$. Since $x$ is real, $\Delta_x \ge 0$:
     $$\Delta_x = [2(y + 1)]^2 - 4(y - 1)[4(y - 1)] \ge 0$$
     $$4(y + 1)^2 - 16(y - 1)^2 \ge 0$$
     Divide by 4:
     $$(y + 1)^2 - 4(y - 1)^2 \ge 0$$
     Factorize using difference of two squares:
     $$[(y + 1) - 2(y - 1)][(y + 1) + 2(y - 1)] \ge 0$$
     $$(-y + 3)(3y - 1) \ge 0$$
     Multiply by $-1$ (reverse inequality):
     $$(y - 3)(3y - 1) \le 0$$
     $$\frac{1}{3} \le y \le 3$$
4. Since $y = 1$ lies inside $\left[\frac{1}{3}, 3\right]$:
   $$\boxed{\text{Range: } y \in \left[\frac{1}{3}, 3\right]}$$

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Derive the vertex form of $f(x) = ax^2 + bx + c$. :: $f(x) = a\left(x + \frac{b}{2a}\right)^2 - \frac{\Delta}{4a}$, where $\Delta = b^2 - 4ac$.

What are the coordinates of the turning point of $y = ax^2 + bx + c$ and when is it a minimum versus a maximum? :: Vertex is $\left(-\frac{b}{2a}, -\frac{\Delta}{4a}\right)$; minimum when $a > 0$ (parabola opens up), maximum when $a < 0$ (parabola opens down).

State the algebraic condition for two quadratic equations $a_1 x^2 + b_1 x + c_1 = 0$ and $a_2 x^2 + b_2 x + c_2 = 0$ to have a common root. :: $(c_1 a_2 - c_2 a_1)^2 = (a_1 b_2 - a_2 b_1)(b_1 c_2 - b_2 c_1)$.

How do you find the common root $\alpha$ between $a_1 x^2 + b_1 x + c_1 = 0$ and $a_2 x^2 + b_2 x + c_2 = 0$? :: $\alpha = \frac{c_1 a_2 - c_2 a_1}{a_1 b_2 - a_2 b_1}$.

State Newton's sum formula for the powers of roots $p_n = \alpha^n + \beta^n$ of $ax^2 + bx + c = 0$. :: $a p_n + b p_{n-1} + c p_{n-2} = 0$.

How do you find the range of a rational quadratic function $y = \frac{ax^2+bx+c}{px^2+qx+r}$ for real $x$? :: Rearrange into quadratic form $(py - a)x^2 + (qy - b)x + (ry - c) = 0$ and impose the real root condition $\Delta_x \ge 0$.

Express $\alpha^4 + \beta^4$ in terms of $S = \alpha + \beta$ and $P = \alpha\beta$. :: $\alpha^4 + \beta^4 = (S^2 - 2P)^2 - 2P^2$.

What are the conditions for the roots of $ax^2 + bx + c = 0$ to both be negative? :: $\Delta = b^2 - 4ac \ge 0$, $\alpha + \beta = -\frac{b}{a} < 0$, and $\alpha\beta = \frac{c}{a} > 0$.

Why is $\Delta > 0$ automatically satisfied when the roots of $ax^2 + bx + c = 0$ have opposite signs? :: Because opposite signs mean $\alpha\beta = \frac{c}{a} < 0 \implies ac < 0$, which makes $-4ac > 0$, guaranteeing $\Delta = b^2 - 4ac > 0$.

If $\alpha, \beta$ are the roots of $ax^2 + bx + c = 0$, what is the equation whose roots are $\alpha^2, \beta^2$? :: $a^2 x^2 - (b^2 - 2ac)x + c^2 = 0$.

What is the geometric meaning when the discriminant of $ax^2 + bx + c = 0$ is zero ($\Delta = 0$)? :: The parabola $y = ax^2 + bx + c$ touches the $x$-axis at exactly one point (its vertex), meaning the equation has two coincident real roots.

Under what condition are the roots of $ax^2 + bx + c = 0$ rational (assuming $a, b, c \in \mathbb{Q}$)? :: When the discriminant $\Delta = b^2 - 4ac$ is the square of a rational number.
