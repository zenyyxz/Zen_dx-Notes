---
title: Impulse & Elastic Collisions Guide
subject: AL Combined Maths
subtopic: Dynamics
tags:
  - AL-Maths
  - Subtopic
  - Collisions
  - Restitution
  - Impulse
  - Flashcards
---
# :LiBrickWallFire: Subtopic: Impulse & Elastic Collisions Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 14 - Work, Power, SHM, Collisions & Probability|Lesson 14 — Work, Power, SHM, Collisions & Probability]]

> [!ABSTRACT] Core Focus
> Mathematical derivations of direct and oblique impacts of smooth spheres, Newton's experimental law of restitution, rigorous algebraic proof of kinetic energy loss, rebound from fixed surfaces, and successive multi-body collisions.

---

## 1. Direct Impact of Two Smooth Spheres

Consider two smooth spheres $A$ and $B$ of masses $m_1$ and $m_2$ moving along their line of centres on a smooth horizontal table with initial velocities $u_1$ and $u_2$ ($u_1 > u_2$). Let $v_1$ and $v_2$ be their final velocities after impact.

### 1.1 Fundamental Equations
1. **Conservation of Linear Momentum**:
   $$m_1 u_1 + m_2 u_2 = m_1 v_1 + m_2 v_2$$
2. **Newton's Law of Restitution**:
   $$v_2 - v_1 = e(u_1 - u_2)$$
   where $e$ is the coefficient of restitution ($0 \le e \le 1$).

### 1.2 Explicit Velocity Formulas
Multiply Newton's law by $m_2$ and add to the momentum equation:
$$m_1 v_1 + m_2 v_1 + m_2 e(u_1 - u_2) = m_1 u_1 + m_2 u_2$$
$$(m_1 + m_2)v_1 = m_1 u_1 + m_2 u_2 - m_2 e(u_1 - u_2)$$
$$\boxed{v_1 = \frac{(m_1 - e m_2)u_1 + m_2(1 + e)u_2}{m_1 + m_2}}$$

Similarly, multiplying by $m_1$ and subtracting:
$$\boxed{v_2 = \frac{m_1(1 + e)u_1 + (m_2 - e m_1)u_2}{m_1 + m_2}}$$

---

## 2. Rigorous Proof of Kinetic Energy Loss

### Theorem
In the direct impact of two smooth spheres of masses $m_1$ and $m_2$ with initial velocities $u_1$ and $u_2$, the loss of kinetic energy is:
$$\Delta E_k = \frac{1}{2}\left(\frac{m_1 m_2}{m_1 + m_2}\right)(1 - e^2)(u_1 - u_2)^2$$

### Proof
Initial kinetic energy: $E_{ki} = \frac{1}{2}m_1 u_1^2 + \frac{1}{2}m_2 u_2^2$.  
Final kinetic energy: $E_{kf} = \frac{1}{2}m_1 v_1^2 + \frac{1}{2}m_2 v_2^2$.  
The loss in kinetic energy is:
$$\Delta E_k = E_{ki} - E_{kf} = \frac{1}{2}m_1(u_1^2 - v_1^2) + \frac{1}{2}m_2(u_2^2 - v_2^2)$$
$$= \frac{1}{2}m_1(u_1 - v_1)(u_1 + v_1) + \frac{1}{2}m_2(u_2 - v_2)(u_2 + v_2)$$

From Conservation of Momentum:
$$m_1(u_1 - v_1) = m_2(v_2 - u_2) = J \quad (\text{the internal impulse exchanged})$$
Therefore:
$$\Delta E_k = \frac{1}{2}J(u_1 + v_1) - \frac{1}{2}J(u_2 + v_2) = \frac{1}{2}J\big[(u_1 - u_2) + (v_1 - v_2)\big]$$

From Newton's Law of Restitution, $v_1 - v_2 = -e(u_1 - u_2)$. Substituting:
$$\Delta E_k = \frac{1}{2}J\big[(u_1 - u_2) - e(u_1 - u_2)\big] = \frac{1}{2}J(1 - e)(u_1 - u_2)$$

Now express impulse $J$ in terms of initial velocities:
$$v_2 - v_1 = \left(u_2 + \frac{J}{m_2}\right) - \left(u_1 - \frac{J}{m_1}\right) = (u_2 - u_1) + J\left(\frac{1}{m_1} + \frac{1}{m_2}\right)$$
Equating to $e(u_1 - u_2)$:
$$J\left(\frac{m_1 + m_2}{m_1 m_2}\right) = (1 + e)(u_1 - u_2) \implies J = \left(\frac{m_1 m_2}{m_1 + m_2}\right)(1 + e)(u_1 - u_2)$$

Substitute $J$ back into the energy loss equation:
$$\Delta E_k = \frac{1}{2}\left[\left(\frac{m_1 m_2}{m_1 + m_2}\right)(1 + e)(u_1 - u_2)\right](1 - e)(u_1 - u_2)$$
$$\Delta E_k = \frac{1}{2}\left(\frac{m_1 m_2}{m_1 + m_2}\right)(1 - e)(1 + e)(u_1 - u_2)^2$$
$$\boxed{\Delta E_k = \frac{1}{2}\left(\frac{m_1 m_2}{m_1 + m_2}\right)(1 - e^2)(u_1 - u_2)^2} \quad \checkmark$$

---

## 3. Impact with a Fixed Plane (Smooth Surface)

A smooth sphere of mass $m$ strikes a fixed rigid plane with velocity $\vec{u}$ at incident angle $\alpha$ to the normal:
- Component along normal: $u_n = u\cos\alpha$
- Component parallel to surface: $u_t = u\sin\alpha$

### Rebound Characteristics
Since the surface is smooth, no tangential impulse acts ($J_t = 0$):
$$v_t = u_t = u\sin\alpha$$
Along the normal, Newton's law gives:
$$v_n = e u_n = e u\cos\alpha$$

- **Rebound Speed**:
  $$v = \sqrt{v_t^2 + v_n^2} = u\sqrt{\sin^2\alpha + e^2\cos^2\alpha}$$
- **Rebound Angle $\theta$ to the Normal**:
  $$\tan\theta = \frac{v_t}{v_n} = \frac{u\sin\alpha}{e u\cos\alpha} = \frac{1}{e}\tan\alpha \implies \boxed{\tan\theta = \frac{\tan\alpha}{e}}$$
  Since $0 < e \le 1$, $\tan\theta \ge \tan\alpha \implies \theta \ge \alpha$ (the rebound trajectory is deflected away from the normal toward the plane).
- **Impulse on the Plane**:
  $$J = m(v_n - (-u_n)) = m(1 + e)u\cos\alpha$$

---

## 4. Oblique Impact of Two Smooth Spheres

Let spheres $A$ and $B$ (masses $m_1, m_2$) collide obliquely. Choose coordinate axes such that the line of centres at the moment of impact is the $x$-axis, and the common tangent plane is the $y$-axis.

Initial velocities:
- $\vec{u}_1 = u_1\cos\alpha_1\hat{\mathbf{i}} + u_1\sin\alpha_1\hat{\mathbf{j}}$
- $\vec{u}_2 = u_2\cos\alpha_2\hat{\mathbf{i}} + u_2\sin\alpha_2\hat{\mathbf{j}}$

### Equations of Motion
1. **Along the $y$-axis (Common Tangent)**:
   Since spheres are smooth, no tangential forces act:
   $$v_{1y} = u_{1y} = u_1\sin\alpha_1$$
   $$v_{2y} = u_{2y} = u_2\sin\alpha_2$$
2. **Along the $x$-axis (Line of Centres)**:
   Normal components follow the exact 1D collision equations:
   $$m_1 v_{1x} + m_2 v_{2x} = m_1 u_{1x} + m_2 u_{2x}$$
   $$v_{2x} - v_{1x} = e(u_{1x} - u_{2x})$$

The final speeds and directions are obtained by vector addition:
$$v_1 = \sqrt{v_{1x}^2 + v_{1y}^2}, \qquad \tan\theta_1 = \frac{v_{1y}}{v_{1x}}$$
$$v_2 = \sqrt{v_{2x}^2 + v_{2y}^2}, \qquad \tan\theta_2 = \frac{v_{2y}}{v_{2x}}$$

---

## 5. Successive Collisions (Row of Spheres)

Three identical smooth spheres $A, B, C$ of equal mass $m$ rest in a line on a smooth horizontal table. Sphere $A$ is projected toward $B$ with speed $u$. The coefficient of restitution between any two spheres is $e$.

1. **Collision between $A$ and $B$**:
   Since $m_1 = m_2 = m$ and $u_2 = 0$:
   $$v_A = \frac{1 - e}{2}u, \qquad v_B = \frac{1 + e}{2}u$$
2. **Collision between $B$ and $C$**:
   $B$ now moves with speed $u' = v_B = \frac{1+e}{2}u$ and strikes stationary $C$:
   $$v_B' = \frac{1 - e}{2}u' = \left(\frac{1 - e}{2}\right)\left(\frac{1 + e}{2}\right)u = \frac{1 - e^2}{4}u$$
   $$v_C = \frac{1 + e}{2}u' = \left(\frac{1 + e}{2}\right)^2 u$$
3. **Condition for $A$ to collide with $B$ a second time**:
   $A$ will strike $B$ again if and only if $v_A > v_B'$:
   $$\frac{1 - e}{2}u > \frac{1 - e^2}{4}u \iff 2(1 - e) > 1 - e^2 \iff 2 > 1 + e \iff e < 1$$
   Since $e < 1$ for all real inelastic collisions, **$A$ will always overtake and collide with $B$ a second time**!

---

## 6. Ballistic Pendulum & Impulse on Suspended Bodies

A bullet of mass $m$ is fired horizontally with speed $u$ into a stationary wooden block of mass $M$ suspended by a light inextensible cord of length $L$. The bullet embeds itself in the block.

### 6.1 Collision Stage (Non-Conservative Impact)
Since the impact duration $\Delta t \to 0$, external forces (gravity, string tension) impart negligible horizontal impulse.
By **Conservation of Horizontal Linear Momentum**:
$$m u = (m + M)V \implies \boxed{V = \left(\frac{m}{m + M}\right)u}$$

The loss of mechanical kinetic energy during this embedding impact is:
$$\Delta E_k = \frac{1}{2}m u^2 - \frac{1}{2}(m + M)V^2 = \frac{1}{2}\left(\frac{m M}{m + M}\right)u^2$$

### 6.2 Swing Stage (Conservative Motion)
After the impact, the combined body of mass $(m + M)$ swings upward like a simple pendulum, conserving mechanical energy:
$$\frac{1}{2}(m + M)V^2 = (m + M)g h \implies \boxed{h = \frac{V^2}{2g} = \frac{m^2 u^2}{2g(m + M)^2}}$$

The maximum angular deflection $\theta_{\max}$ of the cord is given by:
$$h = L(1 - \cos\theta_{\max}) \implies \cos\theta_{\max} = 1 - \frac{h}{L}$$

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State Newton's Law of Restitution for direct collision of two spheres. :: $v_2 - v_1 = -e(u_2 - u_1) = e(u_1 - u_2)$ where $e \in [0, 1]$. <!--SR:!2026-11-20,1,230-->

What is the loss of kinetic energy $\Delta E_k$ in the direct impact of two masses $m_1, m_2$? :: $\Delta E_k = \frac{1}{2}\left(\frac{m_1 m_2}{m_1 + m_2}\right)(1 - e^2)(u_1 - u_2)^2$. <!--SR:!2026-11-20,1,230-->

What is the condition for kinetic energy to be conserved in a collision? :: The collision must be perfectly elastic ($e = 1$). <!--SR:!2026-11-21,2,250-->

If a smooth sphere strikes a fixed smooth wall at angle $\alpha$ to the normal, what is the rebound angle $\theta$ to the normal? :: $\tan\theta = \frac{\tan\alpha}{e}$. <!--SR:!2026-11-21,2,250-->

What happens to the tangential velocity of a smooth sphere striking a smooth plane? :: It remains unchanged ($v_t = u_t$) because smooth surfaces cannot exert tangential impulses. <!--SR:!2026-11-22,3,250-->

What is the impulse exerted on a fixed wall by a mass $m$ rebounding with normal coefficient $e$ and incident normal speed $u_n$? :: $J = m(1 + e)u_n$. <!--SR:!2026-11-22,3,250-->

When two identical masses ($m_1 = m_2$) undergo a perfectly elastic head-on collision ($e = 1$), what happens to their velocities? :: They exchange velocities completely ($v_1 = u_2$ and $v_2 = u_1$). <!--SR:!2026-11-23,4,250-->

In an oblique collision between two smooth spheres, along which direction is linear momentum conserved for each sphere individually? :: Along the common tangent plane (perpendicular to the line of centers). <!--SR:!2026-11-23,4,250-->

In an oblique collision of smooth spheres, along which direction is Newton's Law of Restitution applied? :: Along the line of centers at the moment of impact. <!--SR:!2026-11-24,5,250-->

What is the final velocity of two coalescing bodies of masses $m_1, m_2$ after completely inelastic collision ($e = 0$)? :: $v = \frac{m_1 u_1 + m_2 u_2}{m_1 + m_2}$. <!--SR:!2026-11-24,5,250-->

For three identical spheres $A, B, C$ in a line with $B, C$ at rest, when does $A$ strike $B$ a second time after $B$ hits $C$? :: $A$ strikes $B$ a second time for any $e < 1$. <!--SR:!2026-11-25,6,250-->

What is the physical interpretation of impulse $\vec{J}$ in terms of momentum? :: Impulse equals the change in linear momentum: $\vec{J} = \Delta\vec{p} = m\vec{v} - m\vec{u}$. <!--SR:!2026-11-25,6,250-->

If a ball drops from height $h$ onto a floor of restitution $e$, what is the height reached after the $n$-th bounce? :: $h_n = e^{2n} h$. <!--SR:!2026-11-26,7,250-->
