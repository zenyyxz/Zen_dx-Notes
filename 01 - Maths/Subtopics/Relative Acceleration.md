---
title: Relative Acceleration Guide
subject: AL Combined Maths
subtopic: Dynamics
unit: 13 (Extra / Deep Dive)
competency: Understands relative acceleration, dot notation, and applications to connected particles (pulleys and movable wedges)
tags:
  - AL-Maths
  - Subtopic
  - Dynamics
  - RelativeAcceleration
  - Pulleys
  - Wedges
  - Flashcards
---
# :LiZap: Subtopic: Relative Acceleration Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 13 - Dynamics, Kinematics & Projectiles|Lesson 13 — Dynamics, Kinematics & Projectiles]]

> [!ABSTRACT] Core Focus
> Dot notation ($\dot{x}$, $\ddot{x}$), vector relative acceleration ($\mathbf{a}_{A/B} = \mathbf{a}_A - \mathbf{a}_B$), string length constraint differentiation in complex pulley systems, and full dynamical equations for movable wedges.

---

## 1. Dot Notation — What $\dot{x}$ and $\ddot{x}$ Mean

In dynamics problems, displacement is often written as $x(t)$.  
The dot notation gives time derivatives compactly:

| Notation | Meaning | Typical physical meaning |
|---|---|---|
| $\dot{x}$ | $\displaystyle \dot{x} = \frac{dx}{dt}$ | **Velocity** — rate of change of displacement |
| $\ddot{x}$ | $\displaystyle \ddot{x} = \frac{d^2x}{dt^2} = \frac{d}{dt}(\dot{x})$ | **Acceleration** — rate of change of velocity |
| $\dddot{x}$ | $\displaystyle \dddot{x} = \frac{d^3x}{dt^3}$ | **Jerk** — rate of change of acceleration |

**Why it matters for this topic**:  
When analysing **pulleys** or **wedges**, the motion of each body is expressed as a coordinate function $x(t)$ or $s(t)$. Differentiating the geometric constraint twice produces the **relative acceleration** relation between the bodies. Using $\dot{x}$ and $\ddot{x}$ keeps the algebraic derivation clean and rigorous.

---

## 2. Relative Acceleration Principles

### 2.1 Definition (Vector Form)
If $A$ and $B$ are two particles moving in the same reference frame:
$$\mathbf{a}_{A/B} = \mathbf{a}_A - \mathbf{a}_B = \ddot{\mathbf{r}}_A - \ddot{\mathbf{r}}_B$$

* $\mathbf{a}_A = \ddot{\mathbf{r}}_A$ is the absolute acceleration of $A$.  
* $\mathbf{a}_B = \ddot{\mathbf{r}}_B$ is the absolute acceleration of $B$.  
* $\mathbf{a}_{A/B}$ is the **acceleration of $A$ relative to $B$**.

### 2.2 Scalar (One-Dimensional) Form
If motion is along a straight line:
$$\ddot{x}_{A/B} = \ddot{x}_A - \ddot{x}_B$$

### 2.3 Non-Inertial Reference Frames & Pseudo-Forces
When analyzing the motion of particle $A$ from a reference frame fixed to an accelerating body $B$ (acceleration $\mathbf{a}_B$):
$$m_A \mathbf{a}_{A/B} = \mathbf{F}_{\text{real}} - m_A \mathbf{a}_B$$
where $-m_A \mathbf{a}_B$ is the inertial fictitious force (pseudo-force).

---

## 3. Application — Pulley Systems & String Constraints

The *Pulleys* module treats masses connected by light inextensible strings passing over smooth fixed and movable pulleys.

### 3.1 Single String Over a Fixed Pulley
Let $x_1$ be the downward displacement of mass $m_1$ and $x_2$ the downward displacement of mass $m_2$ measured from the fixed axle level.
The string length $L$ is constant:
$$x_1 + x_2 = L - (\text{pulley arc constant})$$

Differentiating with respect to time $t$ twice:
$$\dot{x}_1 + \dot{x}_2 = 0 \implies \dot{x}_1 = -\dot{x}_2$$
$$\ddot{x}_1 + \ddot{x}_2 = 0 \implies \ddot{x}_1 = -\ddot{x}_2$$
The accelerations are equal in magnitude and opposite in direction ($a_1 = -a_2$).

### 3.2 Movable Pulley System (2:1 Mechanical Advantage)
Consider mass $m_1$ hanging from a fixed pulley by a string, which then loops under a movable pulley supporting mass $m_2$ and is anchored to a ceiling.
Let $x_1$ be the downward position of $m_1$, and $x_2$ be the downward position of the movable pulley ($m_2$).
The string length constraint is:
$$x_1 + 2x_2 = \text{constant}$$

Differentiating twice with respect to time:
$$\ddot{x}_1 + 2\ddot{x}_2 = 0 \implies \ddot{x}_1 = -2\ddot{x}_2$$
When $m_2$ moves downward with acceleration $a$, $m_1$ must accelerate upward with acceleration $2a$.

**Equation of Motion**:
- For $m_1$ ($\downarrow$): $m_1 g - T = m_1 \ddot{x}_1 = m_1(-2a)$
- For $m_2$ ($\downarrow$): $m_2 g - 2T = m_2 \ddot{x}_2 = m_2 a$
- Solving simultaneously eliminates tension $T$ to give the exact acceleration $a$.

---

## 4. Application — Movable Wedges

A block of mass $m$ slides on a smooth wedge of mass $M$ and inclination $\alpha$, which is free to slide horizontally on a smooth table.

### 4.1 Coordinate Definition & Constraint
Define two independent coordinates:
- $X$ — horizontal displacement of the wedge to the left ($\ddot{X} = F$).
- $s$ — displacement of the block **relative to the wedge** down the inclined face ($\ddot{s} = f'$).

### 4.2 Absolute Acceleration Components of Block $m$
$$\vec{a}_m = \vec{a}_{\text{wedge}} + \vec{a}_{\text{rel}} = (-F\hat{\mathbf{i}}) + (f'\cos\alpha\hat{\mathbf{i}} - f'\sin\alpha\hat{\mathbf{j}}) = (f'\cos\alpha - F)\hat{\mathbf{i}} - (f'\sin\alpha)\hat{\mathbf{j}}$$

### 4.3 Setting Up Newton's Second Law
Let $R$ be the normal reaction between the block and the wedge face, and $N$ be the normal reaction from the table on the wedge.

1. **For the Wedge $M$ (Horizontal $\leftarrow$)**:
   $$R\sin\alpha = M F \implies F = \frac{R\sin\alpha}{M}$$
2. **For the Block $m$ (Perpendicular to Wedge Face $\nwarrow$)**:
   $$m g \cos\alpha - R = m a_{\perp} = m(F\sin\alpha)$$
   $$R = m(g\cos\alpha - F\sin\alpha)$$
3. **For the Block $m$ (Parallel to Wedge Face $\swarrow$)**:
   $$m g \sin\alpha = m a_{\parallel} = m(f' - F\cos\alpha)$$
   $$f' = g\sin\alpha + F\cos\alpha$$

### 4.4 Explicit Algebraic Solution
Substitute $R = \frac{M F}{\sin\alpha}$ into the normal equation:
$$\frac{M F}{\sin\alpha} = m g \cos\alpha - m F\sin\alpha$$
$$M F + m F\sin^2\alpha = m g \sin\alpha\cos\alpha$$
$$\boxed{F = \frac{m g \sin\alpha\cos\alpha}{M + m\sin^2\alpha}}$$

The relative acceleration down the slope is:
$$\boxed{f' = g\sin\alpha\left(1 + \frac{m\cos^2\alpha}{M + m\sin^2\alpha}\right) = \frac{(M + m)g\sin\alpha}{M + m\sin^2\alpha}}$$

---

## 5. Connected Particles on an Inclined Plane with Pulley

A classic A/L mechanics configuration involves mass $m_1$ on an inclined plane of angle $\alpha$ connected by a light inextensible string passing over a smooth pulley at the top of the incline to a vertically hanging mass $m_2$.

### 5.1 Smooth Inclined Plane
Let the system accelerate with $m_2$ descending with acceleration $a$. The string constraint gives:
$$a_1 = a_2 = a$$

Equations of motion:
- For $m_2$ ($\downarrow$): $m_2 g - T = m_2 a$
- For $m_1$ (up the incline $\nearrow$): $T - m_1 g \sin\alpha = m_1 a$

Adding the two equations:
$$(m_1 + m_2)a = (m_2 - m_1\sin\alpha)g \implies \boxed{a = \left(\frac{m_2 - m_1\sin\alpha}{m_1 + m_2}\right)g}$$
Tension in the string:
$$\boxed{T = \frac{m_1 m_2(1 + \sin\alpha)}{m_1 + m_2}g}$$

### 5.2 Rough Inclined Plane (Coefficient of Friction $\mu$)
- Normal reaction: $R = m_1 g \cos\alpha$.
- Friction force opposing motion: $F = \mu R = \mu m_1 g \cos\alpha$.
- **If $m_2$ moves downwards**:
  $$a = \left(\frac{m_2 - m_1(\sin\alpha + \mu\cos\alpha)}{m_1 + m_2}\right)g$$
- **If $m_1$ moves downwards**:
  $$a = \left(\frac{m_1(\sin\alpha - \mu\cos\alpha) - m_2}{m_1 + m_2}\right)g$$
- **Condition for static equilibrium**:
  $$m_1(\sin\alpha - \mu\cos\alpha) \le m_2 \le m_1(\sin\alpha + \mu\cos\alpha)$$

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What does $\dot{x}$ represent in kinematics? :: $\dot{x} = \frac{dx}{dt}$ — the **velocity** (first derivative of displacement).
<!--SR:!2026-09-29,4,270-->

What does $\ddot{x}$ represent in kinematics? :: $\ddot{x} = \frac{d^2x}{dt^2}$ — the **acceleration** (second derivative of displacement, rate of change of velocity).
<!--SR:!2026-09-29,4,270-->

State the vector equation for the acceleration of $A$ relative to $B$. :: $\mathbf{a}_{A/B} = \mathbf{a}_A - \mathbf{a}_B = \ddot{\mathbf{r}}_A - \ddot{\mathbf{r}}_B$.

In a simple two‑mass pulley system with string constraint $x_1 + x_2 = \text{const}$, what is the relative‑acceleration relation? :: $\ddot{x}_1 = -\ddot{x}_2$ (equal magnitudes, opposite directions).
<!--SR:!2026-09-29,4,270-->

In a movable wedge problem, how is the block’s absolute acceleration expressed? :: $\mathbf{a}_{\text{block}} = \ddot{x}_{\text{wedge}}\,\hat{\mathbf{i}} + \ddot{s}_{\text{rel}}\,\hat{\mathbf{t}}$ — wedge acceleration plus relative acceleration down the slope.
<!--SR:!2026-09-26,1,230-->

For a movable pulley system with string constraint $x_1 + 2x_2 = L$, what is the relation between accelerations $\ddot{x}_1$ and $\ddot{x}_2$? :: $\ddot{x}_1 + 2\ddot{x}_2 = 0 \implies \ddot{x}_1 = -2\ddot{x}_2$. <!--SR:!2026-11-20,1,230-->

What is the fictitious (pseudo) force acting on a particle of mass $m$ observed from a reference frame accelerating with $\vec{a}_0$? :: $\vec{F}_{\text{pseudo}} = -m\vec{a}_0$. <!--SR:!2026-11-20,1,230-->

In a movable smooth wedge system (mass $M$, angle $\alpha$, block mass $m$), what horizontal force accelerates the wedge? :: The horizontal component of the normal reaction from the block: $F_{\text{net}} = R\sin\alpha = MF$. <!--SR:!2026-11-21,2,250-->

What is the component of absolute acceleration of a block sliding with relative acceleration $f'$ down a wedge accelerating horizontally with $F$? :: Parallel to slope: $f' - F\cos\alpha$; perpendicular to slope: $F\sin\alpha$. <!--SR:!2026-11-21,2,250-->

Why does a light inextensible string have the same tension throughout its length when passing over smooth pulleys? :: Because the string and pulleys are assumed massless and frictionless, requiring no net torque or force to accelerate. <!--SR:!2026-11-22,3,250-->

State the Virtual Work / Tension-Acceleration reciprocal relation for an inextensible string system. :: $\sum T_i \cdot a_i = 0$ (the sum of products of string tensions and mass accelerations is zero). <!--SR:!2026-11-22,3,250-->

If the wedge mass $M \to \infty$ in the movable wedge problem, what does relative acceleration $f'$ simplify to? :: $f' \to g\sin\alpha$ (standard motion on a fixed inclined plane). <!--SR:!2026-11-23,4,250-->

What is the general 4-step algorithm for solving connected particle dynamics problems? :: 1) Set up coordinate system; 2) Differentiate string/contact constraints twice; 3) Write $F = ma$ for each body; 4) Solve simultaneous equations. <!--SR:!2026-11-23,4,250-->
