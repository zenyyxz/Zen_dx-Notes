---
title: Projectiles & Kinematics Guide
subject: AL Combined Maths
subtopic: Dynamics
tags:
  - AL-Maths
  - Subtopic
  - Projectiles
  - Kinematics
  - RelativeMotion
  - Flashcards
---
# :LiBowArrow: Subtopic: Projectiles & Kinematics Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 13 - Dynamics, Kinematics & Projectiles|Lesson 13 — Dynamics, Kinematics & Projectiles]]

> [!ABSTRACT] Core Focus
> Mathematical derivations of projectile trajectory equations, quadratic in $\tan\theta$ and dual firing trajectories, envelope Parabola of Safety, range on inclined planes, perpendicular impact conditions, and 2D relative velocity shortest approach problems.

---

## 1. Full Trajectory Derivation & Dual Angles of Projection

### 1.1 Trajectory Equation Derivation
Let a particle be projected from the origin $(0, 0)$ with speed $u$ at angle $\theta$ to the horizontal:
$$x = (u\cos\theta)t \implies t = \frac{x}{u\cos\theta}$$
$$y = (u\sin\theta)t - \frac{1}{2}gt^2$$

Substituting $t$:
$$y = (u\sin\theta)\left(\frac{x}{u\cos\theta}\right) - \frac{1}{2}g\left(\frac{x}{u\cos\theta}\right)^2 = x\tan\theta - \frac{gx^2}{2u^2\cos^2\theta}$$
Since $\sec^2\theta = 1 + \tan^2\theta$:
$$y = x\tan\theta - \frac{gx^2}{2u^2}(1 + \tan^2\theta)$$

Rearranging as a quadratic in $T = \tan\theta$:
$$\boxed{\left(\frac{gx^2}{2u^2}\right)\tan^2\theta - x\tan\theta + \left(y + \frac{gx^2}{2u^2}\right) = 0}$$

### 1.2 Dual Firing Angles to Hit a Fixed Target $(X, Y)$
If a target at $(X, Y)$ is within maximum range, the quadratic in $\tan\theta$ has two real roots $\tan\theta_1$ and $\tan\theta_2$:
- **Sum of roots**: $\tan\theta_1 + \tan\theta_2 = \frac{X}{\frac{gX^2}{2u^2}} = \frac{2u^2}{gX}$
- **Product of roots**: $\tan\theta_1\tan\theta_2 = \frac{Y + \frac{gX^2}{2u^2}}{\frac{gX^2}{2u^2}} = 1 + \frac{2u^2 Y}{gX^2}$

> [!NOTE] Angle Bisection Property
> The line connecting the origin to target $(X, Y)$ makes angle $\phi = \arctan(Y/X)$ with the horizontal.
> Consider:
> $$\tan(\theta_1 + \theta_2) = \frac{\tan\theta_1 + \tan\theta_2}{1 - \tan\theta_1\tan\theta_2} = \frac{\frac{2u^2}{gX}}{1 - \left(1 + \frac{2u^2 Y}{gX^2}\right)} = \frac{\frac{2u^2}{gX}}{-\frac{2u^2 Y}{gX^2}} = -\frac{X}{Y} = -\cot\phi = \tan(90^\circ + \phi)$$
> Therefore:
> $$\theta_1 + \theta_2 = 90^\circ + \phi \implies \frac{\theta_1 + \theta_2}{2} = 45^\circ + \frac{\phi}{2}$$
> The angle bisector of the two firing directions also bisects the angle between the target line and the vertical!

---

## 2. Derivation of the Parabola of Safety

For the quadratic in $\tan\theta$ to possess real roots, its discriminant must be non-negative:
$$\Delta = B^2 - 4AC \ge 0$$
$$(-X)^2 - 4\left(\frac{gX^2}{2u^2}\right)\left(Y + \frac{gX^2}{2u^2}\right) \ge 0$$
$$X^2 - \frac{2gX^2 Y}{u^2} - \frac{g^2 X^4}{u^4} \ge 0$$

Dividing by $X^2 > 0$:
$$1 - \frac{2gY}{u^2} - \frac{g^2 X^2}{u^4} \ge 0$$
$$\frac{2gY}{u^2} \le 1 - \frac{g^2 X^2}{u^4}$$
$$\boxed{Y \le \frac{u^2}{2g} - \frac{gX^2}{2u^2}}$$

The boundary equation is the **Parabola of Safety**:
$$y = \frac{u^2}{2g} - \frac{gx^2}{2u^2}$$
Every projectile fired from the origin with speed $u$ in any direction in the vertical plane remains entirely on or inside this bounding parabola. Any point strictly outside this envelope cannot be hit.

---

## 3. Projectiles on an Inclined Plane

Let an inclined plane make angle $\beta$ with the horizontal. A particle is projected from a point on the plane with speed $u$ at an angle $\alpha$ to the horizontal ($\alpha > \beta$).

```
      ^ y (perpendicular to plane)
      |
      |   /
      |  /  Trajectory
      | /
      |/_______________> x (along plane)
     / β
    /_________ horizontal
```

### 3.1 Equations Along and Perpendicular to the Plane
Decompose gravity $g$ into components:
- Along the plane ($\swarrow$): $a_x = -g\sin\beta$
- Perpendicular to the plane ($\searrow$): $a_y = -g\cos\beta$

Initial velocity components:
- Along the plane: $u_x = u\cos(\alpha - \beta)$
- Perpendicular to the plane: $u_y = u\sin(\alpha - \beta)$

### 3.2 Time of Flight on the Plane
The particle returns to the plane when $y = 0$:
$$y = u_y t - \frac{1}{2}a_y t^2 = [u\sin(\alpha - \beta)]t - \frac{1}{2}(g\cos\beta)t^2 = 0$$
$$T = \frac{2u\sin(\alpha - \beta)}{g\cos\beta}$$

### 3.3 Range Up the Plane
The distance $R$ traveled along the plane in time $T$:
$$R = u_x T - \frac{1}{2}(g\sin\beta)T^2$$
$$R = [u\cos(\alpha - \beta)]\left[\frac{2u\sin(\alpha - \beta)}{g\cos\beta}\right] - \frac{1}{2}g\sin\beta\left[\frac{2u\sin(\alpha - \beta)}{g\cos\beta}\right]^2$$
Factoring out $\frac{2u^2\sin(\alpha - \beta)}{g\cos^2\beta}$:
$$R = \frac{2u^2\sin(\alpha - \beta)}{g\cos^2\beta}\big[\cos(\alpha - \beta)\cos\beta - \sin(\alpha - \beta)\sin\beta\big]$$
Using compound angle formula $\cos(A+B) = \cos A\cos B - \sin A\sin B$:
$$R = \frac{2u^2\sin(\alpha - \beta)\cos\alpha}{g\cos^2\beta}$$
Using product-to-sum identity $2\cos\alpha\sin(\alpha-\beta) = \sin(2\alpha - \beta) - \sin\beta$:
$$\boxed{R = \frac{u^2}{g\cos^2\beta}\big[\sin(2\alpha - \beta) - \sin\beta\big]}$$

### 3.4 Condition for Perpendicular Impact
If the projectile strikes the inclined plane **at right angles**, its velocity component parallel to the plane at impact must be zero ($v_x = 0$):
$$v_x = u_x - (g\sin\beta)T = 0 \implies u\cos(\alpha - \beta) = g\sin\beta\left[\frac{2u\sin(\alpha - \beta)}{g\cos\beta}\right]$$
$$\cos(\alpha - \beta) = 2\tan\beta\sin(\alpha - \beta)$$
$$\cot(\alpha - \beta) = 2\tan\beta \iff \tan(\alpha - \beta) = \frac{1}{2}\cot\beta$$

---

## 4. Shortest Distance of Approach in 2D Relative Motion

### Step-by-Step Problem Solving Method
1. **Choose an Observer**: Fix one body (say $B$) as stationary at its initial position.
2. **Find Initial Relative Position**:
   $$\vec{r}_0 = \vec{r}_A(0) - \vec{r}_B(0)$$
3. **Find Relative Velocity**:
   $$\vec{u} = \vec{v}_A - \vec{v}_B$$
4. **Draw the Relative Motion Diagram**:
   - Plot $B$ at the origin $(0, 0)$.
   - Plot $A$'s initial relative position at point $P_0$.
   - Draw a ray from $P_0$ in the direction of relative velocity vector $\vec{u}$.
   - Drop a perpendicular from $B$ onto this ray, meeting it at $N$.
5. **Compute Distances**:
   - Shortest distance: $d_{\min} = BN = r_0 \sin\theta$ (where $\theta$ is the angle between $\vec{P_0 B}$ and $\vec{u}$).
   - Time to closest approach: $t_{\min} = \frac{P_0 N}{|\vec{u}|} = \frac{r_0 \cos\theta}{|\vec{u}|}$.

### Worked Example: Ship Approach
Ship $A$ is $10\text{ km}$ due North of ship $B$. Ship $A$ steams due East at $12\text{ km/h}$, while ship $B$ steams due North at $16\text{ km/h}$. Find the shortest distance between them and the time taken.

1. **Velocities**:
   - $\vec{v}_A = 12\hat{\mathbf{i}}\text{ km/h}$
   - $\vec{v}_B = 16\hat{\mathbf{j}}\text{ km/h}$
2. **Relative Velocity of $A$ relative to $B$**:
   - $\vec{v}_{A/B} = \vec{v}_A - \vec{v}_B = 12\hat{\mathbf{i}} - 16\hat{\mathbf{j}}\text{ km/h}$
   - Speed: $|\vec{v}_{A/B}| = \sqrt{12^2 + (-16)^2} = \sqrt{144 + 256} = \sqrt{400} = 20\text{ km/h}$
   - Direction: $\tan\alpha = \frac{16}{12} = \frac{4}{3} \implies \sin\alpha = \frac{4}{5}, \; \cos\alpha = \frac{3}{5}$ (bearing South of East).
3. **Initial Relative Position**:
   - $A$ is $10\text{ km}$ North of $B$: $P_0 = (0, 10)$, distance $r_0 = 10\text{ km}$.
   - The line of relative motion makes angle $\theta$ with the line joining $B$ to $P_0$ (North):
     $\theta = 90^\circ - \alpha \implies \sin\theta = \cos\alpha = \frac{3}{5}, \; \cos\theta = \sin\alpha = \frac{4}{5}$.
4. **Calculations**:
   - Shortest distance: $d_{\min} = r_0 \sin\theta = 10 \times \frac{3}{5} = \mathbf{6\text{ km}}$.
   - Distance traveled on relative path: $s_{\text{rel}} = r_0 \cos\theta = 10 \times \frac{4}{5} = 8\text{ km}$.
   - Time to closest approach: $t_{\min} = \frac{s_{\text{rel}}}{|\vec{v}_{A/B}|} = \frac{8}{20} = 0.4\text{ hours} = \mathbf{24\text{ minutes}}$.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Write the quadratic in $\tan\theta$ representing the trajectory of a projectile passing through target $(x, y)$. :: $\left(\frac{gx^2}{2u^2}\right)\tan^2\theta - x\tan\theta + \left(y + \frac{gx^2}{2u^2}\right) = 0$. <!--SR:!2026-11-20,1,230-->

What is the condition on the discriminant of the $\tan\theta$ trajectory quadratic for a target point to be reachable? :: $\Delta \ge 0 \iff y \le \frac{u^2}{2g} - \frac{gx^2}{2u^2}$. <!--SR:!2026-11-20,1,230-->

State the equation of the Parabola of Safety (bounding envelope of all projectile paths). :: $y = \frac{u^2}{2g} - \frac{gx^2}{2u^2}$. <!--SR:!2026-11-21,2,250-->

If $\theta_1$ and $\theta_2$ are the two angles of projection that hit target $(X, Y)$, what is $\tan(\theta_1 + \theta_2)$? :: $\tan(\theta_1 + \theta_2) = -\frac{X}{Y} = -\cot\phi = \tan(90^\circ + \phi)$ where $\phi = \arctan(Y/X)$. <!--SR:!2026-11-21,2,250-->

State the formula for range $R$ of a projectile fired at angle $\alpha$ up a plane inclined at $\beta$. :: $R = \frac{u^2}{g\cos^2\beta}[\sin(2\alpha - \beta) - \sin\beta]$. <!--SR:!2026-11-22,3,250-->

What projection angle $\alpha$ maximizes the range up an inclined plane of inclination $\beta$? :: $\alpha = \frac{\pi}{4} + \frac{\beta}{2}$. <!--SR:!2026-11-22,3,250-->

State the formula for the maximum range up an inclined plane of inclination $\beta$. :: $R_{\max} = \frac{u^2}{g(1 + \sin\beta)}$. <!--SR:!2026-11-23,4,250-->

State the formula for the maximum range down an inclined plane of inclination $\beta$. :: $R_{\max} = \frac{u^2}{g(1 - \sin\beta)}$. <!--SR:!2026-11-23,4,250-->

What is the condition for a projectile to strike an inclined plane of angle $\beta$ perpendicularly? :: $\cot(\alpha - \beta) = 2\tan\beta$ or $\tan(\alpha - \beta) = \frac{1}{2}\cot\beta$. <!--SR:!2026-11-24,5,250-->

In 2D relative velocity, how is the shortest distance of approach $d_{\min}$ found geometrically? :: By fixing one body at the origin and dropping a perpendicular from it to the line of relative velocity drawn from the other body's initial position. <!--SR:!2026-11-24,5,250-->

If ship $A$ is $10\text{ km}$ North of $B$, $A$ moves East at $12\text{ km/h}$, and $B$ moves North at $16\text{ km/h}$, what is $d_{\min}$? :: $6\text{ km}$ (at time $t = 24\text{ minutes}$). <!--SR:!2026-11-25,6,250-->

What is the time of flight $T$ on a plane inclined at $\beta$ when launch angle relative to the horizontal is $\alpha$? :: $T = \frac{2u\sin(\alpha - \beta)}{g\cos\beta}$. <!--SR:!2026-11-25,6,250-->

What is the physical meaning of the focus of the Parabola of Safety? :: The focus of the Parabola of Safety is located at the origin of projection $(0, 0)$. <!--SR:!2026-11-26,7,250-->
