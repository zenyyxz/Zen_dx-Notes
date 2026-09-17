---
title: Vectors & Equations of Motion Guide
subject: AL Physics
subtopic: Mechanics
tags:
  - AL-Physics
  - Subtopic
  - Vectors
  - Kinematics
  - ProjectileMotion
---

# 🚀 Subtopic: Vectors & Equations of Motion Guide

> [!ABSTRACT] Core Focus
> Resolution of vectors, relative velocity, 1D and 2D kinematic equations, and full derivation of Projectile Motion parameters.

---

## 1. Vector Resolution & Relative Velocity

For a vector $\mathbf{A}$ at angle $\theta$ to the horizontal:
$$A_x = A \cos\theta, \quad A_y = A \sin\theta, \quad |\mathbf{A}| = \sqrt{A_x^2 + A_y^2}$$

### Relative Velocity:
Velocity of object $A$ relative to object $B$:
$$\mathbf{v}_{A/B} = \mathbf{v}_A - \mathbf{v}_B$$

---

## 2. Projectile Motion Derivations

Initial launch speed $u$ at angle $\theta$ above horizontal ($a_x = 0, a_y = -g$):

1. **Time of Flight ($T$)**:
   Set vertical displacement $s_y = 0$:
   $$0 = (u \sin\theta) T - rac{1}{2} g T^2 \implies T = rac{2u\sin\theta}{g}$$
2. **Maximum Height ($H_{\max}$)**:
   Set vertical velocity $v_y = 0$:
   $$0 = (u \sin\theta)^2 - 2g H_{\max} \implies H_{\max} = rac{u^2 \sin^2\theta}{2g}$$
3. **Horizontal Range ($R$)**:
   $$R = u_x \cdot T = (u \cos\theta) \left(rac{2u\sin\theta}{g}ight) = rac{u^2 \sin 2\theta}{g}$$
   Max range occurs at launch angle $\theta = 45^\circ$.