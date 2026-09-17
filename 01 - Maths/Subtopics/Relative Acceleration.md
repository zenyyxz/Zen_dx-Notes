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
#  Subtopic: Relative Acceleration Guide

> [!ABSTRACT] Core Focus
> Dot notation ($\dot{x}$, $\ddot{x}$), relative acceleration ($\mathbf{a}_{A/B} = \mathbf{a}_A - \mathbf{a}_B$), and applications to the two combined‑maths lessons: **Pulley systems** and **Movable wedges**.

---

## 1. Dot Notation — What $\dot{x}$ and $\ddot{x}$ Mean

In dynamics problems, displacement is often written as $x(t)$.  
The dot notation gives the time derivatives compactly:

| Notation | Meaning | Typical physical meaning |
|----------|---------|--------------------------|
| $\dot{x}$ | $\displaystyle \dot{x} = \frac{dx}{dt}$ | **Velocity** — rate of change of displacement |
| $\ddot{x}$ | $\displaystyle \ddot{x} = \frac{d^2x}{dt^2} = \frac{d}{dt}(\dot{x})$ | **Acceleration** — rate of change of velocity |
| $\dddot{x}$ | $\displaystyle \dddot{x} = \frac{d^3x}{dt^3}$ | **Jerk** — rarely needed in basic mechanics |

**Why it matters for this topic**:  
When analysing **pulleys** or **wedges**, the motion of each body is expressed as a function $x(t)$ or $s(t)$.  Differentiating the geometric constraint twice produces the **relative acceleration** relation between the bodies.  Using $\dot{x}$ and $\ddot{x}$ keeps the derivation clean.

---

## 2. Relative Acceleration

### 2.1 Definition (Vector Form)

If $A$ and $B$ are two particles moving in the same reference frame:

$$\mathbf{a}_{A/B} = \mathbf{a}_A - \mathbf{a}_B = \ddot{\mathbf{r}}_A - \ddot{\mathbf{r}}_B$$

* $\mathbf{a}_A = \ddot{\mathbf{r}}_A$ is the absolute acceleration of $A$.  
* $\mathbf{a}_B = \ddot{\mathbf{r}}_B$ is the absolute acceleration of $B$.  
* $\mathbf{a}_{A/B}$ is the **acceleration of $A$ relative to $B$**.

### 2.2 Scalar (One‑Dimensional) Form

If the motion is along a straight line (common in pulley and wedge problems):

$$\ddot{x}_{A/B} = \ddot{x}_A - \ddot{x}_B$$

This is simply the difference of the two absolute accelerations.

---

## 3. Application — Pulley Systems

The *Pulleys* lesson treats masses connected by light inextensible strings passing over smooth pulleys.

**Key idea**:  
Write the constraint equation relating the positions of the masses, then differentiate **twice** to get the relative‑acceleration relation.

### Example — Two masses on a single string

Let $x_1$ be the downward displacement of $m_1$ and $x_2$ the upward displacement of $m_2$.  
The string length is constant, so:

$$x_1 + x_2 = \text{constant}$$

Differentiate twice:

$$\dot{x}_1 + \dot{x}_2 = 0 \quad \Rightarrow \quad \dot{x}_1 = -\dot{x}_2$$
$$\ddot{x}_1 + \ddot{x}_2 = 0 \quad \Rightarrow \quad \ddot{x}_1 = -\ddot{x}_2$$

The result $\ddot{x}_1 = -\ddot{x}_2$ is the **relative acceleration** statement: the magnitudes are equal and opposite.  
Substitute into $F = m\ddot{x}$ for each mass and solve the simultaneous equations.

---

## 4. Application — Movable Wedges

The *Wedges* lesson treats a block sliding on a wedge that is itself free to move horizontally.

**Key idea**:  
Define two coordinates:

* $x$ — horizontal displacement of the wedge.
* $s$ — displacement of the block **relative to the wedge** (down the slope).

The block’s **absolute** acceleration is the vector sum of the wedge’s acceleration and the block’s acceleration relative to the wedge:

$$\mathbf{a}_{\text{block}} = \ddot{x}\,\hat{\mathbf{i}} + \ddot{s}\,\hat{\mathbf{t}}$$

where $\hat{\mathbf{i}}$ is horizontal and $\hat{\mathbf{t}}$ points down the wedge face.

**Relative acceleration link**:  
Differentiating the geometric contact constraint (e.g. $y = s \sin\alpha - x \tan\alpha$ or similar, depending on the problem geometry) gives a linear relation such as:

$$\ddot{s} = -k\,\ddot{x}$$

where $k$ is a constant that depends on the wedge angle.  
This expresses how the wedge’s motion influences the block’s **relative acceleration** down the slope.  Use it together with Newton’s second law on both bodies to solve for the unknown accelerations.

---

## :LiRocket: Flashcards

#flashcards

What does $\dot{x}$ represent in kinematics? :: $\dot{x} = \frac{dx}{dt}$ — the **velocity** (first derivative of displacement).

What does $\ddot{x}$ represent in kinematics? :: $\ddot{x} = \frac{d^2x}{dt^2}$ — the **acceleration** (second derivative of displacement, rate of change of velocity).

State the vector equation for the acceleration of $A$ relative to $B$. :: $\mathbf{a}_{A/B} = \mathbf{a}_A - \mathbf{a}_B = \ddot{\mathbf{r}}_A - \ddot{\mathbf{r}}_B$.

In a simple two‑mass pulley system with string constraint $x_1 + x_2 = \text{const}$, what is the relative‑acceleration relation? :: $\ddot{x}_1 = -\ddot{x}_2$ (equal magnitudes, opposite directions).

In a movable wedge problem, how is the block’s absolute acceleration expressed? :: $\mathbf{a}_{\text{block}} = \ddot{x}_{\text{wedge}}\,\hat{\mathbf{i}} + \ddot{s}_{\text{rel}}\,\hat{\mathbf{t}}$ — wedge acceleration plus relative acceleration down the slope.

---

> [!TIP] Next steps for problem solving
> 1. Set up the **constraint equation** relating the coordinates of the bodies.
> 2. Differentiate **twice** to obtain the $\ddot{x}_{A/B}$ or $\ddot{s}_{\text{rel}}$ relation.
> 3. Apply $F = m\ddot{x}$ (or $F = m\mathbf{a}$) to each body individually.
> 4. Solve the resulting simultaneous equations for the unknown accelerations and forces.