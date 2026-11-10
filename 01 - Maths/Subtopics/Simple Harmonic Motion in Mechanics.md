---
title: Simple Harmonic Motion in Mechanics Guide
subject: AL Combined Maths
subtopic: Dynamics
tags:
  - AL-Maths
  - Subtopic
  - SHM
  - ElasticString
  - HookeLaw
  - Flashcards
---
# :LiTimer: Subtopic: Simple Harmonic Motion in Mechanics Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 14 - Work, Power, SHM, Collisions & Probability|Lesson 14 — Work, Power, SHM, Collisions & Probability]]

> [!ABSTRACT] Core Focus
> Mathematical differential equation $\ddot{x} = -\omega^2 x$, kinematic equations, auxiliary circle method, horizontal elastic strings, vertical elastic string oscillations, equilibrium position derivations, and slack string motion under gravity.

---

## 1. Kinematics of Simple Harmonic Motion

A particle executes Simple Harmonic Motion (SHM) when its acceleration along a straight line is directed toward a fixed point $O$ and is directly proportional to its displacement $x$ from $O$:
$$\ddot{x} = -\omega^2 x \quad (\omega > 0)$$

### 1.1 Velocity as a Function of Position
Using the calculus identity $a = v\frac{dv}{dx}$:
$$v\frac{dv}{dx} = -\omega^2 x \implies \int v\,dv = -\omega^2 \int x\,dx \implies \frac{1}{2}v^2 = -\frac{1}{2}\omega^2 x^2 + C$$

Let $a$ be the **amplitude** (maximum displacement from $O$). At the turning points $x = \pm a$, the velocity is zero ($v = 0$):
$$0 = -\frac{1}{2}\omega^2 a^2 + C \implies C = \frac{1}{2}\omega^2 a^2$$
$$\boxed{v^2 = \omega^2(a^2 - x^2)} \iff v = \pm \omega\sqrt{a^2 - x^2}$$

- **Maximum speed**: $v_{\max} = \omega a$ (at centre $x = 0$).
- **Maximum acceleration**: $\text{accel}_{\max} = \omega^2 a$ (at endpoints $x = \pm a$).

### 1.2 Displacement as a Function of Time
From $v = \frac{dx}{dt} = \omega\sqrt{a^2 - x^2}$:
$$\int \frac{dx}{\sqrt{a^2 - x^2}} = \omega \int dt \implies \sin^{-1}\!\left(\frac{x}{a}\right) = \omega t + \epsilon$$
$$\boxed{x = a\sin(\omega t + \epsilon)}$$
- If timing starts from centre $O$ ($x = 0$ at $t = 0$): $\epsilon = 0 \implies x = a\sin(\omega t)$.
- If timing starts from extreme point ($x = a$ at $t = 0$): $\epsilon = \frac{\pi}{2} \implies x = a\cos(\omega t)$.

### 1.3 Period & Frequency
The motion repeats whenever the phase increases by $2\pi$:
$$\omega T = 2\pi \implies \boxed{T = \frac{2\pi}{\omega}}$$
$$\text{Frequency: } f = \frac{1}{T} = \frac{\omega}{2\pi}$$
Notice the period $T$ is **completely independent of amplitude $a$** (isochronous property of SHM).

---

## 2. The Auxiliary Circle Method

Consider a reference circle of radius $a$ centered at $O$. A point $P'$ moves around the circle counter-clockwise with constant angular speed $\omega$.
- The projection $P$ of $P'$ onto the horizontal diameter executes pure Simple Harmonic Motion:
  $$x = a\cos(\omega t)$$
  $$\dot{x} = -a\omega\sin(\omega t) = -v_{\text{circle}}\sin(\omega t)$$
  $$\ddot{x} = -a\omega^2\cos(\omega t) = -\omega^2 x$$

> [!TIP] Time Calculation Shortcut
> The time taken to travel between any two positions $x_1$ and $x_2$ corresponds to the angle $\Delta\theta$ subtended by the arc on the auxiliary circle:
> $$t = \frac{\Delta\theta}{\omega} = \frac{\Delta\theta}{2\pi} T$$

---

## 3. Horizontal Elastic String System

A particle of mass $m$ is attached to one end of a light elastic string of natural length $l_0$ and modulus of elasticity $\lambda$. The other end is fixed at point $A$ on a smooth horizontal table.

### 3.1 Equation of Motion
Let the particle be pulled to extension $x$ from natural length position $O$:
- Tension: $T = \frac{\lambda x}{l_0}$ (by Hooke's Law, directed toward $A$)
- Equation of motion:
  $$m\ddot{x} = -T = -\frac{\lambda x}{l_0} \implies \ddot{x} = -\left(\frac{\lambda}{m l_0}\right)x$$
This is SHM about $O$ with:
$$\omega = \sqrt{\frac{\lambda}{m l_0}}, \qquad T = 2\pi\sqrt{\frac{m l_0}{\lambda}}$$

### 3.2 Energy Method
Total mechanical energy:
$$E = E_k + E_e = \frac{1}{2}m v^2 + \frac{\lambda x^2}{2l_0} = \text{constant}$$
At the extreme position $x = a$, $v = 0$, so $E = \frac{\lambda a^2}{2l_0}$.
$$\frac{1}{2}m v^2 + \frac{\lambda x^2}{2l_0} = \frac{\lambda a^2}{2l_0} \implies v^2 = \frac{\lambda}{m l_0}(a^2 - x^2)$$
Matching $v^2 = \omega^2(a^2 - x^2)$ confirms $\omega^2 = \frac{\lambda}{m l_0}$.

---

## 4. Vertical Elastic String & Slack String Dynamics

A particle of mass $m$ hangs vertically from a fixed support $A$ by a light elastic string of natural length $l_0$ and modulus $\lambda$.

### 4.1 Equilibrium Position
Let $O$ be the static equilibrium position, where string extension is $e$:
$$T_0 = m g \implies \frac{\lambda e}{l_0} = m g \implies \boxed{e = \frac{m g l_0}{\lambda}}$$

### 4.2 Equation of Motion Displaced from Equilibrium
Measure downward displacement $x$ from equilibrium position $O$:
- Total extension of string: $X = e + x$
- Downward equation of motion:
  $$m\ddot{x} = m g - T = m g - \frac{\lambda(e + x)}{l_0} = m g - \frac{\lambda e}{l_0} - \frac{\lambda x}{l_0}$$
Since $m g - \frac{\lambda e}{l_0} = 0$:
$$m\ddot{x} = -\frac{\lambda x}{l_0} \implies \boxed{\ddot{x} = -\left(\frac{\lambda}{m l_0}\right)x}$$
The motion is pure SHM about the **equilibrium position $O$** (not the natural length level), with period:
$$T = 2\pi\sqrt{\frac{m l_0}{\lambda}}$$

### 4.3 Slack String Dynamics ($a > e$)
Suppose the mass is pulled downward to a distance $d$ below $O$ and released from rest (so amplitude $a = d$).

1. **Case 1: $a \le e$ (Taut String)**:
   The mass never rises above the natural length level ($x = -e$). The string remains in tension throughout the entire cycle. The motion is pure uninterrupted SHM with period $T = 2\pi\sqrt{\frac{m l_0}{\lambda}}$.

2. **Case 2: $a > e$ (Slack String Motion)**:
   When the particle ascends above $O$ past $x = -e$, extension becomes zero and the string becomes **slack** ($T = 0$).
   - **Phase 1 (SHM)**: From lowest point $x = a$ up to natural length level $x = -e$.
     Velocity at $x = -e$:
     $$v_1^2 = \omega^2(a^2 - e^2)$$
     Time in SHM: Angle on auxiliary circle from $\theta = -\frac{\pi}{2}$ to $\sin\phi = \frac{e}{a}$.
   - **Phase 2 (Free Flight under Gravity)**: Once the string is slack, the particle moves under gravity alone with downward acceleration $g$:
     $$\text{Additional height climbed: } h = \frac{v_1^2}{2g} = \frac{\omega^2(a^2 - e^2)}{2g}$$
     Since $\omega^2 = \frac{\lambda}{m l_0} = \frac{g}{e}$:
     $$h = \frac{(g/e)(a^2 - e^2)}{2g} = \frac{a^2 - e^2}{2e}$$
     Time of free flight under gravity: $t_{\text{gravity}} = 2\frac{v_1}{g}$.
   - **Total Periodic Time**:
     $$T_{\text{total}} = 2 t_{\text{SHM}} + t_{\text{gravity}}$$

---

## 5. Mass Attached Between Two Identical Elastic Strings

A particle of mass $m$ is connected between two identical light elastic strings, each of natural length $l_0$ and modulus $\lambda$. The outer ends are fixed to points $A$ and $B$ on a smooth horizontal table separated by distance $2L > 2l_0$.

### 5.1 Equilibrium Position
At the midpoint $O$ between $A$ and $B$, each string has initial extension $e = L - l_0$.
Initial tension in each string:
$$T_0 = \frac{\lambda(L - l_0)}{l_0}$$

### 5.2 Longitudinal Oscillations
Let the particle be displaced by distance $x$ from $O$ along line $AB$ ($x < L - l_0$ so neither string becomes slack):
- Extension of string $A$: $e + x$
- Extension of string $B$: $e - x$
- Tensions:
  $$T_A = \frac{\lambda(e + x)}{l_0}, \qquad T_B = \frac{\lambda(e - x)}{l_0}$$
- Net restoring force toward $O$:
  $$F_{\text{net}} = T_B - T_A = \frac{\lambda}{l_0}\big[(e - x) - (e + x)\big] = -\frac{2\lambda x}{l_0}$$
- Equation of motion:
  $$m\ddot{x} = -\frac{2\lambda x}{l_0} \implies \boxed{\ddot{x} = -\left(\frac{2\lambda}{m l_0}\right)x}$$
This is Simple Harmonic Motion with angular frequency and period:
$$\omega = \sqrt{\frac{2\lambda}{m l_0}}, \qquad T = 2\pi\sqrt{\frac{m l_0}{2\lambda}}$$

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State the standard differential equation defining Simple Harmonic Motion. :: $\ddot{x} = -\omega^2 x$ (acceleration is directed toward centre and proportional to displacement). <!--SR:!2026-11-20,1,230-->

What is the velocity-displacement relation in SHM with amplitude $a$ and angular frequency $\omega$? :: $v^2 = \omega^2(a^2 - x^2)$. <!--SR:!2026-11-20,1,230-->

What is the period $T$ of SHM with equation $\ddot{x} = -\omega^2 x$? :: $T = \frac{2\pi}{\omega}$. <!--SR:!2026-11-21,2,250-->

State the formula for maximum speed $v_{\max}$ and maximum acceleration $a_{\max}$ in SHM. :: $v_{\max} = \omega a$ (at centre $x = 0$); $a_{\max} = \omega^2 a$ (at extremes $x = \pm a$). <!--SR:!2026-11-21,2,250-->

What is the expression for $\omega^2$ for a mass $m$ attached to a horizontal elastic string of natural length $l_0$ and modulus $\lambda$? :: $\omega^2 = \frac{\lambda}{m l_0}$. <!--SR:!2026-11-22,3,250-->

What is the equilibrium extension $e$ of a mass $m$ suspended vertically from an elastic string ($l_0, \lambda$)? :: $e = \frac{m g l_0}{\lambda}$. <!--SR:!2026-11-22,3,250-->

About what point does vertical elastic string oscillation execute SHM? :: About the equilibrium position $O$ (where extension is $e = \frac{mgl_0}{\lambda}$), NOT the natural length level. <!--SR:!2026-11-23,4,250-->

When does a vertically oscillating elastic string become slack? :: When the amplitude $a$ is greater than the equilibrium extension $e$ ($a > e$). <!--SR:!2026-11-23,4,250-->

What type of motion does a particle execute when the elastic string becomes slack? :: Free motion under gravity with constant downward acceleration $g$. <!--SR:!2026-11-24,5,250-->

How is the time to move between two displacements in SHM found using the auxiliary circle? :: $t = \frac{\Delta\theta}{\omega}$ where $\Delta\theta$ is the angle traversed on the auxiliary circle of radius $a$. <!--SR:!2026-11-24,5,250-->

What is the expression for Elastic Potential Energy stored in an elastic string of extension $x$? :: $E_e = \frac{\lambda x^2}{2l_0}$. <!--SR:!2026-11-25,6,250-->

Does the period of a simple harmonic oscillator depend on its amplitude? :: No, the period $T = \frac{2\pi}{\omega}$ is independent of amplitude (isochronism). <!--SR:!2026-11-25,6,250-->

If a particle in SHM is at displacement $x = a/2$, what fraction of its maximum speed is its current speed? :: $\frac{v}{v_{\max}} = \frac{\omega\sqrt{a^2 - (a/2)^2}}{\omega a} = \frac{\sqrt{3}}{2} \approx 86.6\%$. <!--SR:!2026-11-26,7,250-->
