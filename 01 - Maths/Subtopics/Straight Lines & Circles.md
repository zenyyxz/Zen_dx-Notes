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
> Straight lines (distance, ratio theorem, line forms, parametric, point-to-line distance, parallel-line distance, angle, family of lines); circles (standard forms, tangency $p=r$, chord of contact, chord midpoint, radical axis, orthogonal circles $2g_1g_2+2f_1f_2=c_1+c_2$, director circle, relative positions, locus problems).

---

> [!QUICKREF] 5 Most-Used Formulas
> $$d = \frac{\vert Ax_1+By_1+C \vert}{\sqrt{A^2+B^2}} \quad \text{(point-to-line)}$$
> $$\tan\theta = \left\vert\frac{m_1-m_2}{1+m_1m_2}\right\vert \quad \text{(angle)}$$
> $$P\left(\frac{mx_2+nx_1}{m+n},\frac{my_2+ny_1}{m+n}\right) \quad \text{(section formula)}$$
> $$\frac{\vert A h+B k+C \vert}{\sqrt{A^2+B^2}} = r \quad \text{(tangency)}$$
> $$2g_1g_2+2f_1f_2 = c_1+c_2 \quad \text{(orthogonal circles)}$$

---

## :LiRuler: Section 1 — Straight Lines

### Distance Between Two Points
Points $A(x_1, y_1)$ and $B(x_2, y_2)$:
$$AB = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$

---

### Ratio Theorem (Section Formula)
Point $P$ dividing $AB$ in ratio $m:n$:

> [!NOTE] Internal vs External
> - **Internal**: both $m,n > 0$
> - **External**: one is negative

**Internal division** ($m, n > 0$):
$$P\left(\frac{mx_2 + nx_1}{m+n}, \frac{my_2 + ny_1}{m+n}\right)$$

**External division** ($m \neq n$, one negative):
$$P\left(\frac{mx_2 - nx_1}{m-n}, \frac{my_2 - ny_1}{m-n}\right)$$

**Midpoint** ($m = n$):
$$M\left(\frac{x_1 + x_2}{2}, \frac{y_1 + y_2}{2}\right)$$

---

### Line Forms

> [!NOTE] Key Forms
> Pick the form that uses the given data.

**General Form:** $Ax + By + C = 0 \quad (A, B \neq 0)$

**Slope-Intercept:** $y = mx + c$ with $m = -\frac{A}{B},\; c = -\frac{C}{B}$

**Point-Slope:** $y - y_1 = m(x - x_1)$

**Two-Point:** $\frac{y - y_1}{y_2 - y_1} = \frac{x - x_1}{x_2 - x_1}$

**Intercept:** $\frac{x}{a} + \frac{y}{b} = 1$

---

### Parametric Form (Using Parameter $t$)
Line through $A(x_1, y_1)$ with direction $(\cos\theta, \sin\theta)$:
$$\frac{x - x_1}{\cos\theta} = \frac{y - y_1}{\sin\theta} = t$$
$$\Rightarrow x = x_1 + t\cos\theta, \quad y = y_1 + t\sin\theta$$

> [!TIP] Usage
> - $t$ = signed distance from $A$ to point $P(x,y)$
> - Use to find points at a given distance or solve intersection with curves.

**Normal Form:** $x\cos\alpha + y\sin\alpha = p$
- $p$ = perpendicular distance from origin
- $\alpha$ = angle of perpendicular with +ve $x$-axis

---

### Shortest Distance from Point to Line
$$d = \frac{\vert Ax_1 + By_1 + C \vert}{\sqrt{A^2 + B^2}}$$

> [!IMPORTANT]
> This is **perpendicular** distance. Any other line from point to line is longer.

---

### Distance Between Two Parallel Lines
Lines $Ax + By + C_1 = 0$ and $Ax + By + C_2 = 0$:
$$d = \frac{\vert C_1 - C_2 \vert}{\sqrt{A^2 + B^2}}$$

---

### Angle Between Two Lines
$$\tan \theta = \left\vert\frac{m_1 - m_2}{1 + m_1 m_2}\right\vert$$

> [!WARNING] Perpendicular Check
> - **Parallel:** $m_1 = m_2$ (or $A_1B_2 = A_2B_1$)
> - **Perpendicular:** $m_1 m_2 = -1$ (derived from $\tan\theta \to \infty \Rightarrow 1+m_1m_2=0$)
> - In general form: $A_1A_2 + B_1B_2 = 0$

---

### Family of Lines Through Intersection
Lines $L_1$ and $L_2$ intersect at $P$:
$$L_1 + \lambda L_2 = 0$$
- $\lambda \in \mathbb{R}$ gives all lines through $P$ except $L_2$

---



## :LiCircle: Section 2 — Circles

### Standard Forms

> [!NOTE] Complete the Square First
> General form: $x^2+y^2+2gx+2fy+c=0$ → Centre $(-g,-f)$, Radius $\sqrt{g^2+f^2-c}$ (must be $>0$ for real circle).

| Form | Equation | Centre | Radius |
|------|----------|--------|--------|
| **Centre-Radius** | $(x-h)^2+(y-k)^2=r^2$ | $(h,k)$ | $r$ |
| **General** | $x^2+y^2+2gx+2fy+c=0$ | $(-g,-f)$ | $\sqrt{g^2+f^2-c}$ |
| **Diameter Form** | $(x-x_1)(x-x_2)+(y-y_1)(y-y_2)=0$ | Midpoint | $\frac{1}{2}\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}$ |

---

### Parametric Form
$$x = h + r\cos\theta, \quad y = k + r\sin\theta, \quad \theta \in [0, 2\pi)$$

---

> [!SUMMARY]+ Collapsible: All Circle Equations
> *Click to expand*
>
> - Circle: $(x-h)^2+(y-k)^2 = r^2$
> - General: $x^2+y^2+2gx+2fy+c=0$
> - Diameter: $(x-x_1)(x-x_2)+(y-y_1)(y-y_2)=0$
> - Parametric: $(h+r\cos\theta, k+r\sin\theta)$
> - Real condition: $g^2+f^2-c > 0$

---

## 3. Tangency Condition ($p = r$)

$$\frac{\vert A h + B k + C \vert}{\sqrt{A^2 + B^2}} = r$$

### Tangent at Point $P(x_1, y_1)$
For $x^2+y^2+2gx+2fy+c=0$:
$$xx_1 + yy_1 + g(x+x_1) + f(y+y_1) + c = 0$$

Simplified for $x^2+y^2=r^2$: $xx_1+yy_1=r^2$

### Tangent with Slope $m$ to $x^2+y^2=r^2$
$$y = mx \pm r\sqrt{1+m^2}$$

### Length of Tangent from $P(x_1,y_1)$
$$PT = \sqrt{x_1^2+y_1^2+2gx_1+2fy_1+c} = \sqrt{S_{11}}$$

---

## 4. Chord & Chord of Contact

### Chord of Contact (from external point $P$)
$$T = 0 \quad \text{where} \quad xx_1+yy_1+g(x+x_1)+f(y+y_1)+c=0$$

### Chord with Midpoint $M(x_1,y_1)$
$$T = S_{11}$$

### Polar of Point $P$
Same as chord of contact: $T = 0$

---

## 5. Intersection of Circles

$$S_1 - S_2 = 0 \Rightarrow 2(g_1-g_2)x + 2(f_1-f_2)y + (c_1-c_2) = 0$$
- **Radical Axis**: perpendicular to line of centres; equal power locus.

### Family of Circles Through Intersection
$$S_1 + \lambda S_2 = 0 \quad (\lambda \neq -1)$$
- $\lambda = -1$ gives the radical axis.

---

## 6. Orthogonal Circles

> [!IMPORTANT]
> Two circles intersect orthogonally iff tangents at intersection points are perpendicular.

$$2g_1g_2 + 2f_1f_2 = c_1 + c_2$$

**Geometric:** $d^2 = r_1^2 + r_2^2$ where $d$ = distance between centres.

---

## 7. Circle & Line Intersection

Substitute $y=mx+c$ into circle → quadratic in $x$.

> [!NOTE] Discriminant $\Delta$
> - $\Delta > 0$: secant (2 points)
> - $\Delta = 0$: tangent (1 point)
> - $\Delta < 0$: no intersection

---

## 8. Relative Position of Two Circles

Centres $C_1(-g_1,-f_1)$, $C_2(-g_2,-f_2)$; radii $r_1, r_2$; distance $d=C_1C_2$.

| Position | Condition | Common Tangents |
|----------|-----------|-----------------|
| One inside other, no touch | $d < \vert r_1 - r_2 \vert$ | 0 |
| Internal tangency | $d = \vert r_1 - r_2 \vert$ | 1 |
| Intersecting at two points | $\vert r_1 - r_2 \vert < d < r_1 + r_2$ | 2 |
| External tangency | $d = r_1 + r_2$ | 3 |
| Separate (outside each other) | $d > r_1 + r_2$ | 4 |

---

## 9. Director Circle

Locus of points from which perpendicular tangents can be drawn.

For $x^2+y^2=r^2$:
$$x^2+y^2 = 2r^2$$

For $(x-h)^2+(y-k)^2=r^2$:
$$(x-h)^2+(y-k)^2 = 2r^2$$

---

## 10. Important Locus Problems

> [!SUMMARY]+ Collapsible: Locus Summary
>
> - **Parallel chords** (slope $m$): Diameter $\perp$ to chords
> - **Chords through fixed $P$**: Circle with $OP$ as diameter
> - **Chords of constant length $2l$**: Concentric circle radius $\sqrt{r^2-l^2}$
> - **Constant power**: Concentric circle $x^2+y^2=k$
> - **$PA:PB = k$** (Apollonius): Circle (except $k=1$ → perpendicular bisector)

---

## 11. Exam Technique Reminders

> [!TIP] Exam Strategy
> - Complete the square for centre/radius
> - Use $p=r$ for tangency (fastest)
> - Family of lines: $L_1+\lambda L_2=0$
> - Family of circles: $S_1+\lambda S_2=0$
> - Orthogonal: $2g_1g_2+2f_1f_2=c_1+c_2$
> - Chord of contact / Polar: both $T=0$
> - Radical axis: $S_1-S_2=0$ (straight line)
> - Director circle: $x^2+y^2=2r^2$

---

## :LiChartNoAxesColumn: 12. Summary of Key Formulas

| Concept | Formula |
|---------|---------|
| Distance between two points | $\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}$ |
| Internal division ($m:n$) | $\left(\frac{mx_2+nx_1}{m+n},\frac{my_2+ny_1}{m+n}\right)$ |
| Midpoint | $\left(\frac{x_1+x_2}{2},\frac{y_1+y_2}{2}\right)$ |
| Distance point to line | $\frac{\vert Ax_1+By_1+C \vert}{\sqrt{A^2+B^2}}$ |
| Distance between parallel lines | $\frac{\vert C_1-C_2 \vert}{\sqrt{A^2+B^2}}$ |
| Angle between lines | $\tan\theta = \left\vert\frac{m_1-m_2}{1+m_1m_2}\right\vert$ |
| Perpendicular lines (slope) | $m_1m_2 = -1$ |
| Perpendicular lines (general) | $A_1A_2+B_1B_2 = 0$ |
| Circle centre (general) | $(-g, -f)$ |
| Circle radius (general) | $\sqrt{g^2+f^2-c}$ |
| Tangent at $(x_1,y_1)$ | $T=0$ |
| Chord of contact | $T=0$ |
| Chord with midpoint $M$ | $T=S_{11}$ |
| Radical axis | $S_1-S_2=0$ |
| Orthogonal circles | $2g_1g_2+2f_1f_2=c_1+c_2$ |
| Director circle | $x^2+y^2=2r^2$ |
| Length of tangent | $\sqrt{S_{11}}$ |
