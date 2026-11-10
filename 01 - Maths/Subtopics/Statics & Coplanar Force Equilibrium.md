---
title: Statics & Coplanar Force Equilibrium Guide
subject: AL Combined Maths
subtopic: Statics
tags:
  - AL-Maths
  - Subtopic
  - Statics
  - Lami
  - Equilibrium
  - Flashcards
---
# :LiScale: Subtopic: Statics & Coplanar Force Equilibrium Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 12 - Statics, Friction & Rigid Body Equilibrium|Lesson 12 — Statics, Friction & Rigid Body Equilibrium]]

> [!ABSTRACT] Core Focus
> Detailed geometric proofs of Lami's theorem, 3-force concurrency theorem, the $m:n$ cotangent theorem, Varignon's principle of moments, like/unlike parallel forces, and pin-jointed light framework analysis.

---

## 1. Geometric Proof of Lami's Theorem

### Statement
If three coplanar forces $\vec{P}, \vec{Q}, \vec{R}$ acting at a single point $O$ maintain equilibrium, then:
$$\frac{P}{\sin\alpha} = \frac{Q}{\sin\beta} = \frac{R}{\sin\gamma}$$
where $\alpha = \angle(\vec{Q}, \vec{R})$, $\beta = \angle(\vec{P}, \vec{R})$, and $\gamma = \angle(\vec{P}, \vec{Q})$.

### Proof
Let the lines of action of the three forces meet at $O$.
1. Since the system is in equilibrium, the vector sum is zero:
   $$\vec{P} + \vec{Q} + \vec{R} = \vec{0}$$
2. By the **Triangle of Forces**, these vectors can be represented by the directed sides of a triangle $ABC$, where $\vec{AB} = \vec{P}$, $\vec{BC} = \vec{Q}$, and $\vec{CA} = \vec{R}$.
3. Exterior angles at vertices $A, B, C$:
   - The angle between $\vec{P}$ and $\vec{Q}$ is $\gamma$, so the exterior angle at $B$ is $180^\circ - \angle ABC = 180^\circ - \gamma$ (or $\angle ABC = 180^\circ - \gamma$).
   - Similarly, $\angle BCA = 180^\circ - \alpha$.
   - $\angle CAB = 180^\circ - \beta$.
4. Applying the **Sine Rule** to $\triangle ABC$:
   $$\frac{AB}{\sin(\angle BCA)} = \frac{BC}{\sin(\angle CAB)} = \frac{CA}{\sin(\angle ABC)}$$
   $$\frac{P}{\sin(180^\circ - \alpha)} = \frac{Q}{\sin(180^\circ - \beta)} = \frac{R}{\sin(180^\circ - \gamma)}$$
5. Using the identity $\sin(180^\circ - \theta) = \sin\theta$:
   $$\boxed{\frac{P}{\sin\alpha} = \frac{Q}{\sin\beta} = \frac{R}{\sin\gamma}} \quad \checkmark$$

---

## 2. The Three-Force Concurrency Theorem

### Theorem
If a rigid body is in equilibrium under the action of three coplanar forces, and no two of these forces are parallel, then the lines of action of all three forces must pass through a single common point.

### Rigorous Proof
Let the three coplanar forces be $\vec{F}_1, \vec{F}_2, \vec{F}_3$.
1. Since $\vec{F}_1$ and $\vec{F}_2$ are coplanar and not parallel, their lines of action must intersect at some point $P$ in their plane.
2. The moment of force $\vec{F}_1$ about $P$ is zero, because its line of action passes through $P$: $M_P(\vec{F}_1) = 0$.
3. The moment of force $\vec{F}_2$ about $P$ is zero, because its line of action passes through $P$: $M_P(\vec{F}_2) = 0$.
4. For rigid body equilibrium, the algebraic sum of the moments of all forces about **any point** in the plane must be zero:
   $$\sum M_P = M_P(\vec{F}_1) + M_P(\vec{F}_2) + M_P(\vec{F}_3) = 0$$
   $$0 + 0 + M_P(\vec{F}_3) = 0 \implies M_P(\vec{F}_3) = 0$$
5. For $M_P(\vec{F}_3) = F_3 \cdot d = 0$ (where $F_3 \neq 0$), the perpendicular distance $d$ from $P$ to the line of action of $\vec{F}_3$ must be zero.
6. Therefore, the line of action of $\vec{F}_3$ must also pass through $P$. $\quad \checkmark$

---

## 3. The $m : n$ Cotangent Theorem (Full Proof)

Let $D$ be a point on the base $BC$ of $\triangle ABC$ dividing it such that $\frac{BD}{DC} = \frac{m}{n}$. Let $\angle ADB = \theta$, $\angle ADC = 180^\circ - \theta$.

### Part 1: In terms of base angles $B$ and $C$
In $\triangle ABD$, applying the Sine Rule:
$$\frac{BD}{\sin\angle BAD} = \frac{AD}{\sin B} \implies BD = \frac{AD\sin(\theta - B)}{\sin B} = AD(\sin\theta\cot B - \cos\theta)$$

In $\triangle ACD$, applying the Sine Rule:
$$\frac{CD}{\sin\angle CAD} = \frac{AD}{\sin C} \implies CD = \frac{AD\sin(180^\circ - (\theta + C))}{\sin C} = \frac{AD\sin(\theta + C)}{\sin C} = AD(\sin\theta\cot C + \cos\theta)$$

Taking the ratio $\frac{BD}{CD} = \frac{m}{n}$:
$$\frac{m}{n} = \frac{\sin\theta\cot B - \cos\theta}{\sin\theta\cot C + \cos\theta}$$
$$m(\sin\theta\cot C + \cos\theta) = n(\sin\theta\cot B - \cos\theta)$$
Dividing both sides by $\sin\theta$:
$$m\cot C + m\cot\theta = n\cot B - n\cot\theta$$
$$(m + n)\cot\theta = n\cot B - m\cot C \quad \text{or} \quad \boxed{(m + n)\cot\theta = m\cot B - n\cot C}$$

### Part 2: In terms of vertex angles $\alpha = \angle BAD$ and $\beta = \angle CAD$
Similarly, expressing $BD$ and $CD$ using $\angle ADB = \theta$:
$$(m + n)\cot\theta = n\cot\alpha - m\cot\beta$$

---

## 4. Like & Unlike Parallel Forces

### 4.1 Like Parallel Forces
Two parallel forces $P$ and $Q$ acting in the **same direction**:
- **Resultant**: $R = P + Q$ (same direction)
- **Position of Resultant**: Lies between $P$ and $Q$ at point $C$ dividing line segment $AB$ internally in inverse proportion to the forces:
  $$P \cdot AC = Q \cdot CB \iff \frac{AC}{CB} = \frac{Q}{P}$$

### 4.2 Unlike Parallel Forces ($P \neq Q$)
Two parallel forces $P$ and $Q$ acting in **opposite directions** (assume $P > Q$):
- **Resultant**: $R = P - Q$ (in direction of larger force $P$)
- **Position of Resultant**: Lies outside the segment $AB$, beyond the larger force $P$, dividing $AB$ externally:
  $$P \cdot AC = Q \cdot BC$$

*Note*: When $P = Q$ in opposite directions, $R = 0$ and the system reduces to a pure **couple** of moment $P \cdot d$.

---

## 5. Method of Joints for Light Pin-Jointed Frameworks

A framework is statically determinate when its rods $m$ and joints $j$ satisfy $m = 2j - 3$.

### Step-by-Step Procedure
1. **Global Equilibrium**: Treat the entire truss as a single rigid body.
   - Solve $\sum F_x = 0$, $\sum F_y = 0$, $\sum M = 0$ to find external support reactions.
2. **Select Starting Joint**: Find a joint with at most **two unknown member forces**.
3. **Isolate the Joint**: Draw the free-body diagram of the pin joint.
   - Standard convention: Assume all member forces are **Tension** ($T$, pulling away from the pin).
   - If calculated force is positive $(+)$, member is in **Tension**.
   - If calculated force is negative $(-)$, member is in **Thrust / Compression**.
4. **Apply Joint Equilibrium**:
   $$\sum F_x = 0, \qquad \sum F_y = 0$$
5. **Propagate**: Move to adjacent joints until all rod tensions and thrusts are determined.

### Worked Example: Triangular Truss
Three equal light rods of length $a$ form equilateral triangle $ABC$, smoothly jointed at vertices. The truss rests horizontally on supports at $A$ and $B$, with a downward vertical load $W$ applied at vertex $C$.

1. **Reactions at supports**: By symmetry, $R_A = R_B = \frac{W}{2}$.
2. **Equilibrium at Joint $A$**:
   - Let $T_1$ be tension in horizontal rod $AB$, and $C_1$ be compression in rod $AC$ (angle with horizontal $= 60^\circ$).
   - Vertical resolution ($\uparrow$): $R_A - C_1\sin 60^\circ = 0 \implies \frac{W}{2} - C_1\frac{\sqrt{3}}{2} = 0 \implies C_1 = \frac{W}{\sqrt{3}}$ (Thrust in $AC$).
   - Horizontal resolution ($\to$): $T_1 - C_1\cos 60^\circ = 0 \implies T_1 = \frac{W}{\sqrt{3}}\cdot\frac{1}{2} = \frac{W}{2\sqrt{3}}$ (Tension in $AB$).
3. **By symmetry**: Thrust in $BC = C_1 = \frac{W}{\sqrt{3}}$.

---

## 6. Centroid Calculations for Composite Bodies

The position of the centre of gravity $\bar{x}$ of a body composed of parts with weights $W_1, W_2, \dots$ and centroids $x_1, x_2, \dots$ is determined by taking moments of weight about a reference axis:
$$(\sum W_i)\bar{x} = \sum W_i x_i \implies \bar{x} = \frac{W_1 x_1 + W_2 x_2 + \cdots}{W_1 + W_2 + \cdots}$$

For uniform laminas of constant surface density $\sigma$, weight is proportional to area $A$:
$$\bar{x} = \frac{A_1 x_1 + A_2 x_2}{A_1 + A_2}$$

### Removed (Truncated) Portions
When a portion of area $A_2$ (centroid at $x_2$) is removed from a larger lamina of area $A_1$ (centroid at $x_1$):
$$\bar{x} = \frac{A_1 x_1 - A_2 x_2}{A_1 - A_2}$$

### Worked Example: T-Shaped Lamina
A uniform T-shaped lamina consists of a horizontal flange (rectangle $6\text{ cm} \times 2\text{ cm}$) joined symmetrically to a vertical web (rectangle $2\text{ cm} \times 8\text{ cm}$). Find the distance of the centroid from the top edge.

1. **Flange**: Area $A_1 = 6 \times 2 = 12\text{ cm}^2$; centroid $y_1 = 1\text{ cm}$ below top edge.
2. **Web**: Area $A_2 = 2 \times 8 = 16\text{ cm}^2$; centroid $y_2 = 2 + \frac{8}{2} = 6\text{ cm}$ below top edge.
3. **Total Area**: $A = 12 + 16 = 28\text{ cm}^2$.
4. **Taking Moments about top edge**:
   $$\bar{y} = \frac{A_1 y_1 + A_2 y_2}{A_1 + A_2} = \frac{12(1) + 16(6)}{28} = \frac{12 + 96}{28} = \frac{108}{28} = \frac{27}{7} \approx 3.86\text{ cm}$$
The centroid lies on the line of symmetry, $\frac{27}{7}\text{ cm}$ below the top edge.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State Lami's theorem and the condition under which it is applicable. :: $\frac{P}{\sin\alpha} = \frac{Q}{\sin\beta} = \frac{R}{\sin\gamma}$; applicable to three concurrent coplanar forces in static equilibrium. <!--SR:!2026-11-20,1,230-->

Prove why three non-parallel coplanar forces keeping a rigid body in equilibrium must be concurrent. :: The first two non-parallel forces intersect at $P$ with zero moment. For total moment $\sum M_P = 0$, the third force must also have zero moment about $P$, meaning its line of action passes through $P$. <!--SR:!2026-11-20,1,230-->

What is the $m : n$ cotangent theorem in terms of base angles $B$ and $C$? :: $(m + n)\cot\theta = m\cot B - n\cot C$. <!--SR:!2026-11-21,2,250-->

What is the $m : n$ cotangent theorem in terms of vertex angles $\alpha$ and $\beta$? :: $(m + n)\cot\theta = n\cot\alpha - m\cot\beta$. <!--SR:!2026-11-21,2,250-->

What is the magnitude and position of the resultant of two like parallel forces $P$ and $Q$ acting at $A$ and $B$? :: Magnitude $R = P + Q$; acts at point $C$ between $A$ and $B$ such that $P \cdot AC = Q \cdot CB$. <!--SR:!2026-11-22,3,250-->

What is the resultant of two equal and opposite parallel forces $P$ separated by distance $d$? :: Resultant force is zero ($R = 0$); the system constitutes a couple of moment $C = P \cdot d$. <!--SR:!2026-11-22,3,250-->

What condition must the number of members $m$ and joints $j$ satisfy for a plane framework to be statically determinate? :: $m = 2j - 3$. <!--SR:!2026-11-23,4,250-->

In truss analysis, how is a compressive member (strut) distinguished from a tensile member (tie)? :: A tie (tension) pulls away from the joint; a strut (thrust/compression) pushes into the joint. <!--SR:!2026-11-23,4,250-->

State Varignon's Theorem for coplanar forces. :: The algebraic sum of the moments of concurrent coplanar forces about any point equals the moment of their resultant about that same point. <!--SR:!2026-11-24,5,250-->

If a system of forces in a plane reduces to a couple $G \neq 0$, can it be further balanced by a single force? :: No, a couple can only be balanced by another equal and opposite couple. <!--SR:!2026-11-24,5,250-->

What are the 3 independent equilibrium equations for a rigid body in a plane? :: $\sum F_x = 0$, $\sum F_y = 0$, and $\sum M_O = 0$ about any chosen point $O$. <!--SR:!2026-11-25,6,250-->

In the Triangle of Forces, if vectors representing three forces form a closed cycle, what does this signify? :: The three forces are concurrent and in static equilibrium ($\sum \vec{F} = \vec{0}$). <!--SR:!2026-11-25,6,250-->

Why are pin-jointed framework members assumed to carry only axial forces? :: Because the rods are assumed light and the pin joints are smooth, meaning no moments or transverse forces can be transmitted across the joints. <!--SR:!2026-11-26,7,250-->
