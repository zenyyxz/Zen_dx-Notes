---
title: Integration Techniques & Area and Volume
subject: AL Combined Maths
subtopic: Calculus
tags:
  - AL-Maths
  - Subtopic
  - Integration
  - DefiniteIntegrals
  - IBP
  - U-Substitution
---

# :LiFunctionSquare: Subtopic — Integration Techniques, Area & Volume

> [!ABSTRACT] Syllabus Scope
> Integration by substitution (trigonometric, algebraic, rationalising), integration by parts (ILATE / priority rules), standard integral formulas, properties of definite integrals, and applications to area between curves and volumes of revolution.

---

## 1. Standard Integral Formulas

Quick-reference table for antiderivatives used throughout calculus.

| Function $f(x)$ | Integral $\int f(x)\,dx$ | Function $f(x)$ | Integral $\int f(x)\,dx$ |
|:---|:---|:---|:---|
| $\sin x$ | $-\cos x + C$ | $\csc x$ | $-\ln\lvert \csc x + \cot x\rvert + C$ |
| $\cos x$ | $\sin x + C$ | $\sec x$ | $\ln\lvert \sec x + \tan x\rvert + C$ |
| $\tan x$ | $\ln\lvert \sec x\rvert + C$ | $x^{n}$ $(n\neq -1)$ | $\frac{x^{n+1}}{n+1} + C$ |
| $\sec^2 x$ | $\tan x + C$ | $\frac{1}{a^2+x^2}$ $(a>0)$ | $\frac{1}{a}\tan^{-1}\!\left(\frac{x}{a}\right) + C$ |
| $\csc^2 x$ | $-\cot x + C$ | $e^{ax}$ $(a\ne0)$ | $\frac{1}{a}e^{ax} + C$ |
| $\sec x \tan x$ | $\sec x + C$ | $\cot x \csc x$ | $-\csc x + C$ |
| $e^x$ | $e^x + C$ | $\frac{1}{\sqrt{a^2-x^2}}$ $(a>0)$ | $\sin^{-1}\!\left(\frac{x}{a}\right) + C$ |
| $e^{c}$ (const.) | $e^{c}\,x + C$ | $\frac{1}{x}$ | $\ln\lvert x\rvert + C$ |
| $a^{x}$ $(a>0,\ a\ne1)$ | $\frac{a^{x}}{\ln a} + C$ | | |

> [!NOTE] Reduction-style results
> - $\int \sin^2 x \,dx = \frac{x}{2} - \frac{\sin 2x}{4} + C = \frac{x - \sin x\cos x}{2} + C$
> - $\int \cos^2 x \,dx = \frac{x}{2} + \frac{\sin 2x}{4} + C = \frac{x + \sin x\cos x}{2} + C$
> - General exponential: $\int a^{bx}\,dx = \frac{a^{bx}}{b\ln a} + C$ for $a>0$, $a\ne1$, and $b\ne0$.
> - Reduction formulas apply for $\int \sin^n x \,dx$ and $\int \cos^n x \,dx$ when $n$ is a positive integer.

---

## 2. Integral Theorems & Properties

Core rules that allow decomposition and simplification before integrating.

1. **Constant multiple**: $\int k\,f(x)\,dx = k \int f(x)\,dx$
2. **Sum / Difference**: $\int [f(x) \pm g(x)]\,dx = \int f(x)\,dx \pm \int g(x)\,dx$
3. **Constant addition**: $\int [f(x) + k]\,dx = \int f(x)\,dx + kx$
4. **Linear argument (scaling)**: $\int f(ax+b)\,dx = \frac{1}{a}F(ax+b) + C$ for $a\ne0$, where $F'=f$
5. **Derivative inverse**: $\int f'(x)\,dx = f(x) + C$; specifically $\int \frac{f'(x)}{f(x)}\,dx = \ln|f(x)| + C$
6. **Power of composite (U-substitution / power rule)**: $\int [f(x)]^{n}\,f'(x)\,dx = \frac{[f(x)]^{n+1}}{n+1} + C$ for $n \neq -1$

---

## 3. Integration by Substitution (U‑Substitution)

### 3.1 Standard Trigonometric Substitutions

Used when the integrand contains a quadratic expression under a root or in a rational form.

| Expression | Substitution | Derivative relation |
|:---|:---|:---|
| $\sqrt{a^2 - x^2}$ | $x = a\sin\theta$ | $dx = a\cos\theta\,d\theta$ |
| $a^2 + x^2$ | $x = a\tan\theta$ | $dx = a\sec^2\theta\,d\theta$ |
| $\sqrt{x^2 - a^2}$ | $x = a\sec\theta$ | $dx = a\sec\theta\tan\theta\,d\theta$ |
### 3.2 Additional Substitution Rules

> [!KEY-CONCEPT] Choosing $u$ and $t$
> If $f'(x)$ appears in the integrand, set $u = f(x)$. For a definite integral, either transform the limits into the new variable or substitute back before applying the original limits. For rational expressions $\frac{P(x)}{Q(x)}$ with quadratic denominators, complete the square or use partial fractions first.

**Trigonometric / rational forms:**

- $\int \frac{dx}{a+b\cos x}$, $\int \frac{dx}{a+b\sin x}$, or $\int \frac{\sin x\,dx}{a+b\sin x}$: use $t = \tan\left(\frac{x}{2}\right)$.
- $\int \frac{dx}{a+b\cos^2 x}$ or $\int \frac{dx}{a+b\sin^2 x}$: use $t = \tan x$.

**Syllabus substitution patterns (Grade 13):**

- $\int \sin^m x \,dx$ ($m$ odd positive): $t = \cos x$, $dt = -\sin x\,dx$.
- $\int \cos^m x \,dx$ ($m$ odd positive): $t = \sin x$, $dt = \cos x\,dx$.
- $\int \sin^m x \cos^n x \,dx$ ($m, n$ positive integers): strip the odd power and substitute.
- $\int \frac{dx}{a\cos x + b\sin x + c}$: $t = \tan\left(\frac{x}{2}\right)$.
- $\int \frac{dx}{a\cos^2 x + b\sin^2 x + c}$: $t = \tan x$.
- $\int \sqrt{a^2 - x^2}\,dx$ or $\int \frac{dx}{\sqrt{a^2 - x^2}}$: $x = a\sin\theta$ or $x = a\cos\theta$.
- $\int \frac{dx}{\sqrt{a^2 + x^2}}$: $x = a\tan\theta$.
- $\int \frac{dx}{\sqrt{x^2 - a^2}}$: $x = a\sec\theta$.
- $\int \frac{dx}{(px+q)\sqrt{ax+b}}$: $t^2 = ax+b$ (so $t = \sqrt{ax+b}$).
- $\int \frac{dx}{(px+q)\sqrt{ax^2+bx+c}}$: $px+q = \frac{1}{t}$.

**Radical / quadratic forms:**

- $\int \sqrt{a^2+x^2}\,dx$ or $\int \frac{dx}{\sqrt{a^2+x^2}}$: $x = a\tan\theta$.
- $\int \sqrt{a^2-x^2}\,dx$ or $\int \frac{dx}{\sqrt{a^2-x^2}}$: $x = a\sin\theta$.
- $\int \sqrt{x^2-a^2}\,dx$ or $\int \frac{dx}{\sqrt{x^2-a^2}}$: $x = a\sec\theta$.
- If integrand contains $\sqrt{b-x}$ with a linear factor (e.g. $\frac{x-a}{\sqrt{b-x}}$): substitute $t^2 = b-x$ (so $t = \sqrt{b-x}$).
- For $\frac{1}{(x+a)\sqrt{x-b}}$ or similar rational-root forms: substitute $t = \sqrt{x-b}$ (or $t = \sqrt{x+b}$ as appropriate).
- For $\frac{1}{(x+a)\sqrt{x^2+b^2}}$: substitute $t = \frac{1}{x+a}$ (rationalising substitution).

### 3.3 Trigonometric Identities for Integration (Syllabus 16.5)

> [!KEY-CONCEPT] Power-reduction & odd/even rules
> Use double-angle formulas to reduce powers. If the exponent is odd, strip one factor and substitute the rest.

**Basic identity results:**
- $\int \tan x \,dx = -\ln|\cos x| + C = \ln|\sec x| + C$
- $\int \cot x \,dx = \ln|\sin x| + C$
- $\int \sec x \,dx = \ln|\sec x + \tan x| + C$
- $\int \csc x \,dx = -\ln|\csc x + \cot x| + C$

**Even powers** (use $\sin^2 x = \frac{1-\cos 2x}{2}$, $\cos^2 x = \frac{1+\cos 2x}{2}$):
- $\int \sin^2 x \,dx = \frac{x}{2} - \frac{\sin 2x}{4} + C$
- $\int \cos^2 x \,dx = \frac{x}{2} + \frac{\sin 2x}{4} + C$
- $\int \tan^2 x \,dx = \tan x - x + C$
- $\int \cot^2 x \,dx = -\cot x - x + C$

**Odd powers:**
- $\int \sin^m x \,dx$ with $m$ odd positive: substitute $t = \cos x$ ($dt = -\sin x \,dx$)
- $\int \cos^m x \,dx$ with $m$ odd positive: substitute $t = \sin x$ ($dt = \cos x \,dx$)
- $\int \sin^m x \cos^n x \,dx$ with $m, n$ positive integers: apply the appropriate odd-strip substitution.

**Higher powers & products:**
- $\int \sin^3 x \,dx = -\cos x + \frac{\cos^3 x}{3} + C$
- $\int \cos^3 x \,dx = \sin x - \frac{\sin^3 x}{3} + C$
- $\int \sin mx \cos nx \,dx$, $\int \cos mx \cos nx \,dx$, $\int \sin mx \sin nx \,dx$: use product-to-sum formulas.

---

## 4. Integration by Parts (IBP)

> [!KEY-CONCEPT] IBP Formula
> $$\int u \,\frac{dv}{dx}\,dx = uv - \int v \,\frac{du}{dx}\,dx \quad\text{or}\quad \int u\,dv = uv - \int v\,du$$

**How to choose $u$ and $dv$:**
- Pick $u$ as the function that simplifies when differentiated. **ILATE** (Inverse trig, Logarithmic, Algebraic, Trigonometric, Exponential) is a useful heuristic—not an inflexible rule.
- Pick $dv$ as the function that is easy to integrate.

Common patterns:
- $\int x\sin x \,dx$ → $u = x$, $dv = \sin x \,dx$
- $\int x e^x \,dx$ → $u = x$, $dv = e^x \,dx$ (may require repeated IBP)
- $\int \ln x \,dx$ → $u = \ln x$, $dv = dx$

---

## 5. Integration of Rational Functions (Quadratic Forms)

### 5.1 Case A — Linear / Quadratic Denominator

For
$$\int \frac{dx}{ax^2+bx+c}, \qquad a\ne0,$$
complete the square or use $\Delta_x = b^2 - 4ac$:

- **$\Delta_x > 0$**: the denominator has two real linear factors; use partial fractions. The result is logarithmic:
  $$\int\frac{dx}{ax^2+bx+c}=\frac{1}{\sqrt{\Delta}}\ln\left|\frac{2ax+b-\sqrt{\Delta}}{2ax+b+\sqrt{\Delta}}\right|+C.$$
- **$\Delta_x = 0$**: the denominator is a perfect square. Complete the square and use the power rule:
  $$\int\frac{dx}{ax^2+bx+c}=-\frac{2}{2ax+b}+C.$$
- **$\Delta_x < 0$**: the denominator has no real roots. Complete the square; the result involves $\tan^{-1}$:
  $$\int\frac{dx}{ax^2+bx+c}=\frac{2}{\sqrt{4ac-b^2}}\tan^{-1}\!\left(\frac{2ax+b}{\sqrt{4ac-b^2}}\right)+C.$$

### 5.2 Case B — Linear Numerator / Quadratic Denominator

If $\int \frac{Ax + B}{ax^2 + bx + c}\,dx$:

- Split into the derivative of the denominator ($\Delta_x$ term) plus a constant remainder.
- The derivative part integrates to $\ln|ax^2 + bx + c|$.
- The remainder is handled by **Case A**.

> [!NOTE] Partial fractions reminder
> When the denominator factorises, decompose $\frac{P(x)}{Q(x)}$ into partial fractions before integrating term-by-term. For this syllabus, $P(x)$ and $Q(x)$ are polynomials of **degree $\leq 4$** (maximum 4 unknown constants).

---

## 6. Definite Integrals

> [!KEY-CONCEPT] Fundamental Theorem
> If $F'(x) = f(x)$, then:
> $$\int_{a}^{b} f(x)\,dx = \Big[ F(x) \Big]_{a}^{b} = F(b) - F(a)$$

**Properties:**

1. $\int_{a}^{a} f(x)\,dx = 0$
2. $\int_{a}^{b} f(x)\,dx = -\int_{b}^{a} f(x)\,dx$
3. $\int_{a}^{b} f(x)\,dx = \int_{a}^{c} f(x)\,dx + \int_{c}^{b} f(x)\,dx$ (additivity over intervals)
4. $\int_{a}^{b} k\,f(x)\,dx = k \int_{a}^{b} f(x)\,dx$
5. **Symmetry / reflection**: $\int_{0}^{a} f(x)\,dx = \int_{0}^{a} f(a-x)\,dx$
6. If $f$ is **odd**, $\int_{-a}^{a} f(x)\,dx = 0$.
7. If $f$ is **even**, $\int_{-a}^{a} f(x)\,dx = 2\int_{0}^{a} f(x)\,dx$.

---

## 7. Area & Volume by Integration

Quick reference for geometric applications required by the syllabus.

> [!NOTE] Syllabus scope and exam technique
> - **16.8** covers area under a curve and area between two curves.
> - **16.9** covers volume of revolution using $V=\pi\int_a^b[f(x)]^2\,dx$.
> - Even where curve-sketching is not directly assessed, make a quick rough sketch to locate intercepts/intersections and determine which curve is above the other.

**Area under a curve:**
If $y = f(x)$ is non-negative and continuous on $[a,b]$, then:
$$A = \int_{a}^{b} f(x)\,dx$$
If the curve crosses the $x$-axis, split at its roots and use
$$A = \int_a^b |f(x)|\,dx.$$

**Area between two curves:**
If $f(x) \ge g(x)$ on $[a,b]$:
$$A = \int_{a}^{b} \big[f(x) - g(x)\big]\,dx$$
If the curves cross, find their intersection points, split the interval, and use
$$A = \int_a^b |f(x)-g(x)|\,dx.$$

**Volume of revolution (about $x$-axis):**
$$V = \pi \int_{a}^{b} [f(x)]^2\,dx$$

> [!TIP] Extension
> The general cross-section/washer form $V=\int_a^b A(x)\,dx$ is useful, but the stated syllabus formula above is the priority.

---

## :LiRocket: Spaced Repetition Flashcards

#flashcards

What substitution is used for $\sqrt{a^2 - x^2}$? :: $x = a\sin\theta$ <!--SR:!2026-10-10,4,270-->

What substitution is used for $a^2 + x^2$? :: $x = a\tan\theta$ <!--SR:!2026-10-10,4,270-->

What substitution is used for $\sqrt{x^2 - a^2}$? :: $x = a\sec\theta$ <!--SR:!2026-10-10,4,270-->

State the Integration by Parts formula. :: $\int u\,dv = uv - \int v\,du$ <!--SR:!2026-10-08,4,270-->

What does ILATE stand for when choosing $u$ in IBP? :: Inverse trig, Logarithmic, Algebraic, Trigonometric, Exponential <!--SR:!2026-10-08,4,270-->

State the Fundamental Theorem of Definite Integration. :: $\int_{a}^{b} f(x)\,dx = F(b) - F(a)$ where $F'(x) = f(x)$ <!--SR:!2026-10-06,4,270-->

Write the formula for the area between two curves. :: $A = \int_{a}^{b} [f(x) - g(x)]\,dx$ with $f(x) \ge g(x)$ <!--SR:!2026-10-06,4,270-->

Write the formula for volume of revolution about the $x$-axis. :: $V = \pi \int_{a}^{b} [f(x)]^2\,dx$ <!--SR:!2026-10-06,4,270-->

How do you split $\int \frac{Ax+B}{ax^2+bx+c}\,dx$? :: Derivative of denominator gives $\ln|ax^2+bx+c|$; remainder handled like $\int \frac{dx}{ax^2+bx+c}$ <!--SR:!2026-10-04,4,270-->

What is $\int \sin^2 x\,dx$? :: $\frac{x}{2} - \frac{\sin 2x}{4} + C$ or $\frac{x - \sin x\cos x}{2} + C$ <!--SR:!2026-10-04,4,270-->