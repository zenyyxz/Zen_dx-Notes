---
title: Friction & Rigid Body Dynamics Guide
subject: AL Combined Maths
subtopic: Statics
tags:
  - AL-Maths
  - Subtopic
  - Friction
  - Equilibrium
  - Flashcards
---
# :LiLoaderPinwheel: Subtopic: Friction & Rigid Body Dynamics Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 12 - Statics, Friction & Rigid Body Equilibrium|Lesson 12 — Statics, Friction & Rigid Body Equilibrium]]

> [!ABSTRACT] Core Focus
> Mathematical laws of limiting friction, angle of repose, cone of friction, least pulling force on rough inclined planes, complete algebraic analysis of ladder and rod equilibrium, and tipping vs. slipping criteria.

---

## 1. Laws of Limiting Friction & The Cone of Friction

### 1.1 Coulomb's Laws of Dry Friction
1. **Direction**: Friction opposes the impending relative motion of the contacting surfaces.
2. **Magnitude**:
   - In static equilibrium: $F \le \mu R$
   - In **limiting equilibrium** (impending motion): $F = \mu R$
   - In kinetic motion: $F_k = \mu_k R$ (where $\mu_k \le \mu$)
3. **Independence**: Limiting friction is independent of the apparent area of contact and, over reasonable ranges, independent of velocity.

### 1.2 Angle of Friction $\lambda$
Let the normal reaction be $R$ and the frictional force be $F$. The total reaction exerted by the surface is:
$$\vec{S} = \vec{R} + \vec{F}$$
The magnitude of the total reaction is $S = \sqrt{R^2 + F^2}$.

Let $\phi$ be the angle between total reaction $\vec{S}$ and the normal reaction $\vec{R}$:
$$\tan\phi = \frac{F}{R}$$
As the applied force increases, $\phi$ increases until limiting equilibrium is attained, at which point $\phi = \lambda$:
$$\tan\lambda = \frac{F_L}{R} = \frac{\mu R}{R} \implies \boxed{\mu = \tan\lambda}$$

The total reaction at limiting equilibrium is:
$$S_{\max} = \sqrt{R^2 + (\mu R)^2} = R\sqrt{1 + \mu^2} = R\sec\lambda$$

### 1.3 The Cone of Friction
The **cone of friction** is a right circular cone having:
- Vertex at the point of contact
- Axis along the normal reaction $\vec{R}$
- Semi-vertical angle equal to the angle of friction $\lambda$

**Equilibrium Criterion**: The body remains in equilibrium if and only if the line of action of the total reaction $\vec{S}$ lies **inside or on the surface** of the cone of friction ($\phi \le \lambda$).

---

## 2. Equilibrium on Rough Inclined Planes

Consider a body of weight $W$ on a rough plane inclined at angle $\alpha$ to the horizontal ($\mu = \tan\lambda$).

### 2.1 The Angle of Repose
If the body rests on the plane under its own weight alone:
- Component down plane: $W\sin\alpha$
- Normal reaction: $R = W\cos\alpha$
- Friction required: $F = W\sin\alpha$

For equilibrium without slipping:
$$F \le \mu R \implies W\sin\alpha \le \mu W\cos\alpha \implies \tan\alpha \le \mu \implies \tan\alpha \le \tan\lambda \implies \alpha \le \lambda$$
The maximum inclination at which a body rests in equilibrium under gravity alone is the **angle of repose**, which equals the **angle of friction** $\lambda$.

### 2.2 Least Force to Drag a Body Up a Rough Inclined Plane
Let force $P$ be applied at angle $\theta$ above the inclined plane to pull the body up:
- Normal resolution ($\uparrow$): $R + P\sin\theta = W\cos\alpha \implies R = W\cos\alpha - P\sin\theta$
- Along plane ($\nearrow$): $P\cos\theta = W\sin\alpha + \mu R = W\sin\alpha + \mu(W\cos\alpha - P\sin\theta)$
- Substitute $\mu = \frac{\sin\lambda}{\cos\lambda}$:
  $$P\cos\theta\cos\lambda + P\sin\theta\sin\lambda = W\sin\alpha\cos\lambda + W\cos\alpha\sin\lambda$$
  $$P\cos(\theta - \lambda) = W\sin(\alpha + \lambda)$$
  $$\boxed{P = \frac{W\sin(\alpha + \lambda)}{\cos(\theta - \lambda)}}$$

**Least Force $P_{\min}$**:
$P$ is minimized when the denominator $\cos(\theta - \lambda) = 1 \implies \theta = \lambda$:
$$\boxed{P_{\min} = W\sin(\alpha + \lambda)}$$
*(The least force must be inclined at an angle equal to the angle of friction $\lambda$ to the plane)*.

---

## 3. The Classic Ladder Problem

A uniform ladder $AB$ of length $2a$ and weight $W$ rests with foot $A$ on a rough horizontal floor (coefficient $\mu_1$) and top $B$ against a rough vertical wall (coefficient $\mu_2$), inclined at angle $\theta$ to the horizontal.

```
      B | wall (rough μ₂)
        | \
        |  \
        |   \
        |    \  Ladder of length 2a, weight W
        |     \
      __|______\ A floor (rough μ₁)
```

### Forces Acting on the Ladder
- At foot $A$: Normal reaction $R_1$ (vertical $\uparrow$), Friction $F_1 = \mu_1 R_1$ (horizontal towards wall $\to$)
- At top $B$: Normal reaction $R_2$ (horizontal away from wall $\leftarrow$), Friction $F_2 = \mu_2 R_2$ (vertical upward along wall $\uparrow$)
- At midpoint $G$: Weight $W$ (vertically downward $\downarrow$)

### Governing Equilibrium Equations
1. **Horizontal Resolution ($\to$)**:
   $$F_1 - R_2 = 0 \implies R_2 = F_1 = \mu_1 R_1$$
2. **Vertical Resolution ($\uparrow$)**:
   $$R_1 + F_2 - W = 0 \implies R_1 + \mu_2 R_2 = W$$
   Substitute $R_2 = \mu_1 R_1$:
   $$R_1(1 + \mu_1\mu_2) = W \implies R_1 = \frac{W}{1 + \mu_1\mu_2}, \qquad R_2 = \frac{\mu_1 W}{1 + \mu_1\mu_2}$$
3. **Moments About Foot $A$ ($\circlearrowleft$)**:
   $$R_2(2a\sin\theta) + F_2(2a\cos\theta) - W(a\cos\theta) = 0$$
   Divide by $a\cos\theta$:
   $$2 R_2\tan\theta + 2 F_2 = W$$
   Substitute $F_2 = \mu_2 R_2$:
   $$2 R_2(\tan\theta + \mu_2) = W$$
   Substitute $R_2 = \frac{\mu_1 W}{1 + \mu_1\mu_2}$:
   $$2 \left(\frac{\mu_1 W}{1 + \mu_1\mu_2}\right)(\tan\theta + \mu_2) = W$$
   $$2\mu_1(\tan\theta + \mu_2) = 1 + \mu_1\mu_2$$
   $$2\mu_1\tan\theta = 1 - \mu_1\mu_2$$
   $$\boxed{\tan\theta = \frac{1 - \mu_1\mu_2}{2\mu_1}}$$

### Special Case: Smooth Wall ($\mu_2 = 0$)
When the vertical wall is smooth ($\mu_2 = 0$):
$$\boxed{\tan\theta = \frac{1}{2\mu_1}}$$
For equilibrium to be possible, the ladder's inclination must satisfy $\tan\theta \ge \frac{1}{2\mu_1}$.

---

## 4. Tipping vs. Slipping (Toppling Criteria)

Consider a uniform solid rectangular block of mass $m$ (weight $W = mg$), width $b$, and height $h$ resting on a rough horizontal floor ($\mu$). A horizontal force $P$ is applied at the top edge ($y = h$).

### 4.1 Slipping Analysis
The maximum static friction resisting motion is $F_{\max} = \mu R = \mu W$.
Slipping begins when:
$$P > \mu W \implies P_{\text{slip}} = \mu W$$

### 4.2 Tipping (Toppling) Analysis
As $P$ increases, the normal reaction shifts toward the forward edge $O$. At the impending tipping point, the normal reaction $R$ acts entirely at the corner $O$.
Taking moments about corner $O$ ($\circlearrowleft$):
$$P \cdot h - W \cdot \frac{b}{2} = 0 \implies P_{\text{tip}} = W\frac{b}{2h}$$

### 4.3 Comparison & Behavior
- **Slipping occurs before tipping if**:
  $$P_{\text{slip}} < P_{\text{tip}} \iff \mu W < W\frac{b}{2h} \iff \boxed{\mu < \frac{b}{2h}}$$
- **Tipping occurs before slipping if**:
  $$P_{\text{tip}} < P_{\text{slip}} \iff \boxed{\mu > \frac{b}{2h}}$$

### 4.4 Block on Tilting Rough Inclined Plane
When a block of width $b$ and height $h$ is placed on an inclined plane whose angle $\alpha$ is gradually increased:
- Impending **slip** occurs when: $\tan\alpha = \mu$
- Impending **topple** occurs when the line of action of the weight falls outside the base: $\tan\alpha = \frac{b}{h}$
- The block will **slip first** if $\mu < \frac{b}{h}$.
- The block will **topple first** if $\mu > \frac{b}{h}$.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State Coulomb's relation for the force of limiting static friction $F_L$. :: $F_L = \mu R$ where $\mu$ is the coefficient of static friction and $R$ is normal reaction. <!--SR:!2026-11-20,1,230-->

Define the angle of friction $\lambda$ and write its relationship with $\mu$. :: The angle between the total contact reaction and the normal reaction at limiting equilibrium; $\tan\lambda = \mu$. <!--SR:!2026-11-20,1,230-->

What is the magnitude of the total contact reaction $S$ at limiting equilibrium? :: $S = R\sqrt{1+\mu^2} = R\sec\lambda$. <!--SR:!2026-11-21,2,250-->

What is the Cone of Friction? :: A cone of semi-vertical angle $\lambda$ centered around the normal; equilibrium is maintained as long as the resultant reaction lies inside or on this cone. <!--SR:!2026-11-21,2,250-->

What is the Angle of Repose of a rough plane? :: The maximum angle of inclination $\alpha$ at which a body rests on the plane under gravity alone without slipping; $\alpha = \lambda$. <!--SR:!2026-11-22,3,250-->

What is the magnitude and direction of the least force $P$ required to drag a body of weight $W$ up a plane inclined at $\alpha$? :: $P_{\min} = W\sin(\alpha + \lambda)$, inclined at angle $\lambda$ above the plane. <!--SR:!2026-11-22,3,250-->

In the ladder problem on rough ground ($\mu_1$) and smooth wall ($\mu_2 = 0$), what is the critical angle $\theta$ for equilibrium? :: $\tan\theta = \frac{1}{2\mu_1}$. <!--SR:!2026-11-23,4,250-->

In the general ladder problem on rough ground ($\mu_1$) and rough wall ($\mu_2$), what is the critical angle $\theta$ for limiting equilibrium? :: $\tan\theta = \frac{1 - \mu_1\mu_2}{2\mu_1}$. <!--SR:!2026-11-23,4,250-->

For a rectangular block of width $b$ and height $h$ pulled horizontally at the top, when does slipping happen before tipping? :: When $\mu < \frac{b}{2h}$. <!--SR:!2026-11-24,5,250-->

For a block of base $b$ and height $h$ on an inclined plane whose angle is increased, what is the condition for it to topple before slipping? :: It topples first when $\mu > \frac{b}{h}$. <!--SR:!2026-11-24,5,250-->

What direction does the frictional force act when a ladder's foot begins to slip outward away from the wall? :: Horizontally inward towards the wall (opposing the outward motion). <!--SR:!2026-11-25,6,250-->

What is the least horizontal force required to maintain equilibrium of a body of weight $W$ on a rough plane of inclination $\alpha > \lambda$ against sliding down? :: $P = W\tan(\alpha - \lambda)$. <!--SR:!2026-11-25,6,250-->

Does static friction always equal $\mu R$? :: No, $F = \mu R$ only at limiting equilibrium; otherwise $F \le \mu R$ and self-adjusts to balance applied forces. <!--SR:!2026-11-26,7,250-->
