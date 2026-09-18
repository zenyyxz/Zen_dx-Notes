---
title: Straight Lines & Circles Guide
subject: AL Combined Maths
subtopic: Geometry
tags:
  - AL-Maths
  - Subtopic
  - StraightLines
  - Circles
---
# :LiGitGraph: Subtopic: Straight Lines & Circles Guide

> [!ABSTRACT] Core Focus
> Family of lines passing through intersection point, condition of tangency to circle ($p = r$), orthogonal circle intersection condition, and common locus problems.

---

## 1. Straight Lines

### General Form
$$Ax + By + C = 0, \quad (A, B \neq 0)$$

### Slope-Intercept Form
$$y = mx + c \quad \text{where } m = -\frac{A}{B}, \; c = -\frac{C}{B}$$

### Point-Slope Form
$$y - y_1 = m(x - x_1)$$

### Two-Point Form
$$\frac{y - y_1}{y_2 - y_1} = \frac{x - x_1}{x_2 - x_1}$$

### Intercept Form
$$\frac{x}{a} + \frac{y}{b} = 1 \quad \text{(x-intercept } a, \text{ y-intercept } b)$$

### Distance from Point to Line
Perpendicular distance from $P(x_1, y_1)$ to $Ax + By + C = 0$:
$$d = \frac{|Ax_1 + By_1 + C|}{\sqrt{A^2 + B^2}}$$

### Angle Between Two Lines
Lines $y = m_1x + c_1$ and $y = m_2x + c_2$:
$$\tan \theta = \left|\frac{m_1 - m_2}{1 + m_1 m_2}\right|$$
- **Parallel**: $m_1 = m_2$
- **Perpendicular**: $m_1 m_2 = -1$

### Family of Lines Through Intersection
Lines $L_1: A_1x + B_1y + C_1 = 0$ and $L_2: A_2x + B_2y + C_2 = 0$ intersect at $P$.
Family of lines through $P$:
$$L_1 + \lambda L_2 = 0 \quad \text{or} \quad (A_1 + \lambda A_2)x + (B_1 + \lambda B_2)y + (C_1 + \lambda C_2) = 0$$
- $\lambda \in \mathbb{R}$ gives all lines through $P$ except $L_2$ ($\lambda \to \infty$)
- **Special case**: Line through $P$ with slope $m$: substitute $y - y_P = m(x - x_P)$

---

## 2. Circles

### Standard Forms

| Form | Equation | Centre | Radius |
|------|----------|--------|--------|
| **Centre-Radius** | $(x - h)^2 + (y - k)^2 = r^2$ | $(h, k)$ | $r$ |
| **General** | $x^2 + y^2 + 2gx + 2fy + c = 0$ | $(-g, -f)$ | $\sqrt{g^2 + f^2 - c}$ |
| **Diameter Form** | $(x - x_1)(x - x_2) + (y - y_1)(y - y_2) = 0$ | Midpoint | $\frac{1}{2}\sqrt{(x_2-x_1)^2 + (y_2-y_1)^2}$ |

**Condition for real circle**: $g^2 + f^2 - c > 0$

### Parametric Form
$$x = h + r\cos\theta, \quad y = k + r\sin\theta, \quad \theta \in [0, 2\pi)$$

---

## 3. Tangency Condition ($p = r$)

Line $Ax + By + C = 0$ is tangent to circle $(x - h)^2 + (y - k)^2 = r^2$ iff:
$$\frac{|A h + B k + C|}{\sqrt{A^2 + B^2}} = r$$

### Tangent at Point $P(x_1, y_1)$ on Circle
For circle $x^2 + y^2 + 2gx + 2fy + c = 0$:
$$xx_1 + yy_1 + g(x + x_1) + f(y + y_1) + c = 0$$
Simplified for $x^2 + y^2 = r^2$: $xx_1 + yy_1 = r^2$

### Tangent with Slope $m$ to $x^2 + y^2 = r^2$
$$y = mx \pm r\sqrt{1 + m^2}$$

### Length of Tangent from $P(x_1, y_1)$ to Circle
$$PT = \sqrt{x_1^2 + y_1^2 + 2gx_1 + 2fy_1 + c} = \sqrt{S_{11}}$$
where $S = x^2 + y^2 + 2gx + 2fy + c$ and $S_{11} = S(x_1, y_1)$

---

## 4. Chord & Chord of Contact

### Chord of Contact
From external point $P(x_1, y_1)$ to circle $S = 0$:
$$T = 0 \quad \text{where} \quad xx_1 + yy_1 + g(x + x_1) + f(y + y_1) + c = 0$$

### Chord with Given Midpoint $M(x_1, y_1)$
Equation: $T = S_{11}$ (where $S_{11} = S(x_1, y_1)$)

### Polar of Point $P(x_1, y_1)$
Same as chord of contact: $T = 0$

---

## 5. Intersection of Circles

### Two Circles
$S_1: x^2 + y^2 + 2g_1x + 2f_1y + c_1 = 0$
$S_2: x^2 + y^2 + 2g_2x + 2f_2y + c_2 = 0$

### Radical Axis
$$S_1 - S_2 = 0 \Rightarrow 2(g_1 - g_2)x + 2(f_1 - f_2)y + (c_1 - c_2) = 0$$
- Line perpendicular to line of centres
- Locus of points with equal power w.r.t. both circles

### Family of Circles Through Intersection
$$S_1 + \lambda S_2 = 0 \quad (\lambda \neq -1)$$
- $\lambda = -1$ gives radical axis (straight line)

---

## 6. Orthogonal Circles

Two circles $S_1 = 0$ and $S_2 = 0$ intersect **orthogonally** iff:
$$2g_1g_2 + 2f_1f_2 = c_1 + c_2$$

**Geometric interpretation**: Tangents at intersection points are perpendicular.
**Equivalently**: $d^2 = r_1^2 + r_2^2$ where $d$ = distance between centres.

---

## 7. Circle & Line Intersection

Line $y = mx + c$ and circle $x^2 + y^2 + 2gx + 2fy + c = 0$:
- Substitute line into circle → quadratic in $x$
- Discriminant $\Delta$:
  - $\Delta > 0$: Two distinct points (secant)
  - $\Delta = 0$: One point (tangent)
  - $\Delta < 0$: No intersection

---

## 8. Relative Position of Two Circles

Centres $C_1(-g_1, -f_1)$, $C_2(-g_2, -f_2)$; radii $r_1, r_2$; distance $d = C_1C_2$.

| Position | Condition | Common Tangents |
|----------|-----------|-----------------|
| One inside other, no touch | $d < |r_1 - r_2|$ | 0 |
| Internal tangency | $d = |r_1 - r_2|$ | 1 |
| Intersecting at two points | $|r_1 - r_2| < d < r_1 + r_2$ | 2 |
| External tangency | $d = r_1 + r_2$ | 3 |
| Separate (outside each other) | $d > r_1 + r_2$ | 4 |

---

## 9. Director Circle

Locus of intersection points of perpendicular tangents to circle $x^2 + y^2 = r^2$:
$$x^2 + y^2 = 2r^2$$

For general circle $(x - h)^2 + (y - k)^2 = r^2$:
$$(x - h)^2 + (y - k)^2 = 2r^2$$

---

## 10. Important Locus Problems

### Locus of Midpoints of Chords
- **Parallel chords** (slope $m$): Diameter perpendicular to chords
- **Chords through fixed point $P$**: Circle with $OP$ as diameter ($O$ = centre)
- **Chords of constant length $2l$**: Concentric circle radius $\sqrt{r^2 - l^2}$

### Locus of Point with Constant Power
Circle concentric with given circle: $x^2 + y^2 = k$

### Locus of Point $P$ such that $PA : PB = k$ (Apollonius Circle)
Circle (except $k = 1$ gives perpendicular bisector)

---

## 11. Key Exam Tips

> [!TIP] Exam Technique
> - **Always complete the square** to find centre/radius from general form
> - **Tangency**: Use $p = r$ (distance from centre = radius) — fastest method
> - **Family of lines**: $L_1 + \lambda L_2 = 0$ — find $\lambda$ using given condition
> - **Family of circles**: $S_1 + \lambda S_2 = 0$ — use condition to find $\lambda$
> - **Orthogonal condition**: Memorise $2g_1g_2 + 2f_1f_2 = c_1 + c_2$
> - **Chord of contact / Polar**: Both use $T = 0$
> - **Radical axis**: $S_1 - S_2 = 0$ (straight line, no $\lambda$)
> - **Director circle**: $x^2 + y^2 = 2r^2$ for perpendicular tangents

---

## 12. Summary of Key Formulas

| Concept | Formula |
|---------|---------|
| Distance point to line | $\frac{|Ax_1 + By_1 + C|}{\sqrt{A^2 + B^2}}$ |
| Angle between lines | $\tan\theta = \left|\frac{m_1 - m_2}{1 + m_1 m_2}\right|$ |
| Circle centre (general) | $(-g, -f)$ |
| Circle radius (general) | $\sqrt{g^2 + f^2 - c}$ |
| Tangent at $(x_1, y_1)$ | $T = 0$ |
| Chord of contact | $T = 0$ |
| Chord with midpoint $M$ | $T = S_{11}$ |
| Radical axis | $S_1 - S_2 = 0$ |
| Orthogonal circles | $2g_1g_2 + 2f_1f_2 = c_1 + c_2$ |
| Director circle | $x^2 + y^2 = 2r^2$ |
| Length of tangent | $\sqrt{S_{11}}$ |