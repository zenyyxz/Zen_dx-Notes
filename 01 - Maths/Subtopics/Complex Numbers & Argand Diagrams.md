---
title: Complex Numbers & Argand Diagrams
subject: AL Combined Maths
subtopic: Algebra
tags:
  - AL-Maths
  - Subtopic
  - ComplexNumbers
  - DeMoivre
  - ArgandLoci
  - RootsOfUnity
  - Flashcards
---

# :LiCompass: Subtopic: Complex Numbers & Argand Diagrams Guide

> [!ABSTRACT] Core Focus (NIE Teacher's Guide — Grade 13, Competency 23)
> Complete mathematical derivations: conjugate and modulus properties, induction proof of De Moivre's theorem, algebra of $n$-th roots of unity, geometric derivation of the triangle inequalities, and comprehensive Cartesian-geometric analysis of loci in the Argand plane.

> [!NOTE] Parent Lesson
> [[../Lesson 04 - Complex Numbers|Lesson 04 — Complex Numbers]]

---

## 1. Rigorous Algebraic Proofs of Fundamental Properties

### 1.1 Modulus of Product and Quotient
**Theorem 1**: For any $z_1, z_2 \in \mathbb{C}$, $|z_1 z_2| = |z_1| \cdot |z_2|$.

**Proof**:
Recall that for any complex number $w$, $|w|^2 = w \bar{w}$.
$$|z_1 z_2|^2 = (z_1 z_2) \overline{(z_1 z_2)}$$
Using the property of conjugates $\overline{z_1 z_2} = \bar{z}_1 \bar{z}_2$:
$$|z_1 z_2|^2 = (z_1 z_2)(\bar{z}_1 \bar{z}_2) = (z_1 \bar{z}_1)(z_2 \bar{z}_2) = |z_1|^2 \cdot |z_2|^2$$
Since moduli are non-negative real numbers, taking the principal square root on both sides:
$$\boxed{|z_1 z_2| = |z_1| \cdot |z_2|} \quad \blacksquare$$

**Theorem 2**: For $z_2 \ne 0$, $\left|\frac{z_1}{z_2}\right| = \frac{|z_1|}{|z_2|}$.

**Proof**:
Let $w = \frac{z_1}{z_2} \implies z_1 = w z_2$.
Applying Theorem 1:
$$|z_1| = |w z_2| = |w| \cdot |z_2| \implies |w| = \frac{|z_1|}{|z_2|}$$
$$\boxed{\left|\frac{z_1}{z_2}\right| = \frac{|z_1|}{|z_2|}} \quad \blacksquare$$

---

### 1.2 Triangle Inequality Derivation
**Theorem**: For any $z_1, z_2 \in \mathbb{C}$, $|z_1 + z_2| \le |z_1| + |z_2|$.

**Proof**:
Consider the squared modulus $|z_1 + z_2|^2$:
$$|z_1 + z_2|^2 = (z_1 + z_2)\overline{(z_1 + z_2)} = (z_1 + z_2)(\bar{z}_1 + \bar{z}_2)$$
$$= z_1 \bar{z}_1 + z_1 \bar{z}_2 + \bar{z}_1 z_2 + z_2 \bar{z}_2 = |z_1|^2 + (z_1 \bar{z}_2 + \overline{z_1 \bar{z}_2}) + |z_2|^2$$
Since $w + \bar{w} = 2\text{Re}(w)$ for any $w$:
$$|z_1 + z_2|^2 = |z_1|^2 + 2\text{Re}(z_1 \bar{z}_2) + |z_2|^2$$

Recall that for any complex number $w = u + iv$:
$$\text{Re}(w) = u \le \sqrt{u^2 + v^2} = |w|$$
Therefore, $\text{Re}(z_1 \bar{z}_2) \le |z_1 \bar{z}_2| = |z_1| |\bar{z}_2| = |z_1| |z_2|$.
Substituting this bound:
$$|z_1 + z_2|^2 \le |z_1|^2 + 2|z_1||z_2| + |z_2|^2 = (|z_1| + |z_2|)^2$$
Taking the square root on both sides (both sides being non-negative):
$$\boxed{|z_1 + z_2| \le |z_1| + |z_2|} \quad \blacksquare$$

**Deduction of the Reverse Triangle Inequality**:
Write $z_1 = (z_1 - z_2) + z_2$.
Applying the triangle inequality:
$$|z_1| = |(z_1 - z_2) + z_2| \le |z_1 - z_2| + |z_2| \implies |z_1| - |z_2| \le |z_1 - z_2|$$
Similarly, interchanging $z_1$ and $z_2$:
$$|z_2| - |z_1| \le |z_2 - z_1| = |z_1 - z_2| \implies -(|z_1| - |z_2|) \le |z_1 - z_2|$$
Combining these two inequalities:
$$\boxed{||z_1| - |z_2|| \le |z_1 - z_2|} \quad \blacksquare$$

---

## 2. De Moivre's Theorem & Applications

### 2.1 Extension to Negative Integers
Let $n = -m$ where $m \in \mathbb{Z}^+$.
$$(\cos\theta + i\sin\theta)^n = (\cos\theta + i\sin\theta)^{-m} = \frac{1}{(\cos\theta + i\sin\theta)^m}$$
By the induction proof for positive integers:
$$= \frac{1}{\cos(m\theta) + i\sin(m\theta)} = \frac{\cos(m\theta) - i\sin(m\theta)}{\cos^2(m\theta) + \sin^2(m\theta)} = \cos(m\theta) - i\sin(m\theta)$$
Using symmetry identities $\cos(-x) = \cos x$ and $\sin(-x) = -\sin x$:
$$= \cos(-m\theta) + i\sin(-m\theta) = \cos(n\theta) + i\sin(n\theta) \quad \blacksquare$$

---

### 2.2 The $n$-th Roots of Unity ($z^n = 1$)
To solve $z^n = 1$:
Write $1$ in general polar form:
$$1 = \cos(2k\pi) + i\sin(2k\pi) \quad (k \in \mathbb{Z})$$
Let $z = r(\cos\phi + i\sin\phi)$. By De Moivre's theorem:
$$z^n = r^n(\cos n\phi + i\sin n\phi) = 1[\cos(2k\pi) + i\sin(2k\pi)]$$
Equating moduli and arguments:
$$r^n = 1 \implies r = 1$$
$$n\phi = 2k\pi \implies \phi_k = \frac{2k\pi}{n} \quad (k = 0, 1, 2, \dots, n-1)$$

The $n$ distinct roots are:
$$\boxed{z_k = \cos\left(\frac{2k\pi}{n}\right) + i\sin\left(\frac{2k\pi}{n}\right) = \omega^k}$$
where $\omega = \cos\left(\frac{2\pi}{n}\right) + i\sin\left(\frac{2\pi}{n}\right) = e^{i\frac{2\pi}{n}}$.

**Properties of Roots of Unity**:
1. **Sum of Roots**:
   $$\sum_{k=0}^{n-1} z_k = 1 + \omega + \omega^2 + \dots + \omega^{n-1} = \frac{1 - \omega^n}{1 - \omega} = \frac{1 - 1}{1 - \omega} = 0$$
   $$\boxed{1 + \omega + \omega^2 + \dots + \omega^{n-1} = 0}$$
2. **Geometric Structure**:
   The $n$ roots of unity are vertices of a **regular $n$-sided polygon** inscribed in the unit circle $|z| = 1$, with one vertex always at $z = 1$.

#### Special Case: Cube Roots of Unity ($z^3 = 1$)
Roots are $1, \omega, \omega^2$ where:
$$\omega = \cos\left(\frac{2\pi}{3}\right) + i\sin\left(\frac{2\pi}{3}\right) = -\frac{1}{2} + i\frac{\sqrt{3}}{2}$$
$$\omega^2 = \cos\left(\frac{4\pi}{3}\right) + i\sin\left(\frac{4\pi}{3}\right) = -\frac{1}{2} - i\frac{\sqrt{3}}{2} = \bar{\omega}$$
* $\boxed{1 + \omega + \omega^2 = 0}$
* $\boxed{\omega^3 = 1}$

---

## 3. Geometric Loci Analysis & Worked Problems

### 3.1 Worked Problem 1: Perpendicular Bisector Locus
**Problem**: Find the Cartesian equation of the locus defined by $|z - 2 + i| = |z + 1 - 3i|$ and sketch it on the Argand plane.

**Solution**:
1. Let $z = x + iy$.
   The equation becomes:
   $$|(x - 2) + i(y + 1)| = |(x + 1) + i(y - 3)|$$
2. Square both sides:
   $$(x - 2)^2 + (y + 1)^2 = (x + 1)^2 + (y - 3)^2$$
3. Expand:
   $$(x^2 - 4x + 4) + (y^2 + 2y + 1) = (x^2 + 2x + 1) + (y^2 - 6y + 9)$$
   $$-4x + 2y + 5 = 2x - 6y + 10$$
4. Rearrange:
   $$-6x + 8y - 5 = 0 \implies \boxed{6x - 8y + 5 = 0}$$
5. **Geometric Check**:
   * Point $z_1 = 2 - i \implies (2, -1)$.
   * Point $z_2 = -1 + 3i \implies (-1, 3)$.
   * Midpoint $M = \left(\frac{2 - 1}{2}, \frac{-1 + 3}{2}\right) = \left(\frac{1}{2}, 1\right)$.
     Check on line: $6(1/2) - 8(1) + 5 = 3 - 8 + 5 = 0$ ✓.
   * Slope of $z_1 z_2$: $m = \frac{3 - (-1)}{-1 - 2} = -\frac{4}{3}$.
   * Slope of perpendicular bisector: $m_\perp = -\frac{1}{m} = \frac{3}{4}$.
     Line equation: $y - 1 = \frac{3}{4}\left(x - \frac{1}{2}\right) \implies 4y - 4 = 3x - \frac{3}{2} \implies 6x - 8y + 5 = 0$ ✓.

---

### 3.2 Worked Problem 2: Circular Disk with Extremum Modulus
**Problem**: If $|z - 3 - 4i| \le 2$, find the maximum and minimum values of $|z|$ and the complex numbers at which they occur.

**Solution**:
1. Geometric interpretation:
   $|z - (3 + 4i)| \le 2$ represents a **closed circular disk** with:
   * Center $C = z_0 = 3 + 4i$
   * Radius $R = 2$
2. Distance from origin $O$ to center $C$:
   $$|z_0| = \sqrt{3^2 + 4^2} = 5$$
3. Using the Triangle Inequality:
   $$|z| = |(z - z_0) + z_0| \le |z - z_0| + |z_0| \le 2 + 5 = 7$$
   $$|z| = |z_0 - (z_0 - z)| \ge |z_0| - |z - z_0| \ge 5 - 2 = 3$$
   $$\boxed{|z|_{\text{min}} = 3, \quad |z|_{\text{max}} = 7}$$
4. **Locating the Extremum Points**:
   Both points lie on the line passing through origin $O(0,0)$ and center $C(3,4)$.
   Unit vector along $OC$: $\hat{u} = \frac{3 + 4i}{5}$.
   * Minimum point (closest to origin):
     $$z_{\text{min}} = (|z_0| - R)\hat{u} = (5 - 2)\frac{3 + 4i}{5} = \boxed{\frac{9}{5} + \frac{12}{5}i}$$
   * Maximum point (furthest from origin):
     $$z_{\text{max}} = (|z_0| + R)\hat{u} = (5 + 2)\frac{3 + 4i}{5} = \boxed{\frac{21}{5} + \frac{28}{5}i}$$

---

### 3.3 Worked Problem 3: Ray Locus
**Problem**: Find the Cartesian equation of the locus given by $\text{Arg}(z - 1 - i) = \frac{\pi}{3}$.

**Solution**:
1. Let $z = x + iy$.
   $$z - 1 - i = (x - 1) + i(y - 1)$$
2. Since $\text{Arg}(z - 1 - i) = \frac{\pi}{3}$:
   $$\tan\left(\frac{\pi}{3}\right) = \sqrt{3} \implies \frac{y - 1}{x - 1} = \sqrt{3}$$
   $$\boxed{y - 1 = \sqrt{3}(x - 1)}$$
3. **Domain restriction**:
   Since $\frac{\pi}{3}$ lies in the 1st quadrant, both real and imaginary parts of $(z - 1 - i)$ must be strictly positive:
   $$\boxed{x > 1 \quad \text{and} \quad y > 1}$$
   *(The point $(1, 1)$ is excluded).*

---

## 4. Problem-Solving Summary Reference

| Problem Goal | Mathematical Formula | Geometric Meaning |
|---|---|---|
| Find $|z|_{\text{min}}, |z|_{\text{max}}$ given $|z - z_0| = r$ | $|z|_{\text{max}} = |z_0| + r$, $|z|_{\text{min}} = ||z_0| - r|$ | Distance from origin to closest/furthest point on circle |
| Line through $z_1, z_2$ | $\arg\left(\frac{z - z_1}{z_2 - z_1}\right) = 0 \text{ or } \pi$ | Collinear points |
| Right angle at $z$ subtended by $z_1, z_2$ | $\text{Re}\left(\frac{z - z_1}{z - z_2}\right) = 0$ | Circle with diameter $z_1 z_2$ |
| Roots of unity sum | $\sum_{k=0}^{n-1} \omega^k = 0$ | Centroid of polygon is at the origin |
| Cube roots of unity | $1 + \omega + \omega^2 = 0, \; \omega^3 = 1$ | $120^\circ$ rotational symmetry |

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Prove that $|z_1 z_2| = |z_1||z_2|$ using complex conjugates. :: $|z_1 z_2|^2 = (z_1 z_2)\overline{(z_1 z_2)} = (z_1 \bar{z}_1)(z_2 \bar{z}_2) = |z_1|^2 |z_2|^2$. Taking square roots gives $|z_1 z_2| = |z_1||z_2|$.

Prove the Triangle Inequality $|z_1 + z_2| \le |z_1| + |z_2|$. :: $|z_1 + z_2|^2 = |z_1|^2 + 2\text{Re}(z_1 \bar{z}_2) + |z_2|^2 \le |z_1|^2 + 2|z_1||z_2| + |z_2|^2 = (|z_1| + |z_2|)^2$. Taking square roots gives $|z_1 + z_2| \le |z_1| + |z_2|$.

Deduce the Reverse Triangle Inequality $||z_1| - |z_2|| \le |z_1 - z_2|$ from the triangle inequality. :: $|z_1| = |(z_1 - z_2) + z_2| \le |z_1 - z_2| + |z_2| \implies |z_1| - |z_2| \le |z_1 - z_2|$; swapping $z_1, z_2$ gives $|z_2| - |z_1| \le |z_1 - z_2|$, combining to $||z_1| - |z_2|| \le |z_1 - z_2|$.

What are the solutions to $z^3 = 1$ (cube roots of unity)? :: $1, \omega, \omega^2$, where $\omega = -\frac{1}{2} + i\frac{\sqrt{3}}{2}$ and $\omega^2 = -\frac{1}{2} - i\frac{\sqrt{3}}{2}$.

State the two fundamental algebraic relations satisfied by the complex cube root of unity $\omega$. :: $1 + \omega + \omega^2 = 0$ and $\omega^3 = 1$.

What geometric figure do the $n$-th roots of unity form in the Argand plane? :: A regular $n$-sided polygon inscribed in the unit circle $|z| = 1$ with one vertex at $(1, 0)$ and centroid at the origin.

If $|z - z_0| \le r$, what are the minimum and maximum values of $|z|$ (assuming $|z_0| > r$)? :: $|z|_{\text{min}} = |z_0| - r$ and $|z|_{\text{max}} = |z_0| + r$.

What is the Cartesian equation for the locus $\text{Arg}(z - z_0) = \alpha$? :: $\frac{y - y_0}{x - x_0} = \tan\alpha$ with constraints $(x - x_0) > 0$ if $\alpha \in (-\pi/2, \pi/2)$ and $(x - x_0) < 0$ otherwise, excluding $(x_0, y_0)$.

How do you show that the locus $|z - z_1| = |z - z_2|$ represents the perpendicular bisector of segment $z_1 z_2$? :: By setting $|z - z_1|^2 = |z - z_2|^2$, the squared terms $x^2 + y^2$ cancel, yielding a linear equation in $x$ and $y$ whose slope is negative reciprocal to segment $z_1 z_2$ and passes through its midpoint.

State De Moivre's theorem for negative integers $n = -m$ ($m \in \mathbb{Z}^+$). :: $(\cos\theta + i\sin\theta)^{-m} = \frac{1}{\cos m\theta + i\sin m\theta} = \cos(-m\theta) + i\sin(-m\theta) = \cos n\theta + i\sin n\theta$.

What is the value of $(1 + \omega)(1 + \omega^2)$ where $\omega$ is a complex cube root of unity? :: Since $1 + \omega = -\omega^2$ and $1 + \omega^2 = -\omega$, their product is $(-\omega^2)(-\omega) = \omega^3 = 1$.

What does the equation $\text{Re}\left(\frac{z - z_1}{z - z_2}\right) = 0$ represent geometrically? :: A circle having the line segment joining $z_1$ and $z_2$ as diameter (excluding $z_2$).
