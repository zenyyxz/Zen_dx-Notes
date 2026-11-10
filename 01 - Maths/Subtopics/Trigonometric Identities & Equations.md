---
title: Trigonometric Identities & Equations Guide
subject: AL Combined Maths
subtopic: Trigonometry
tags:
  - AL-Maths
  - Subtopic
  - Trigonometry
  - Identities
  - Flashcards
---
# :LiCompass: Subtopic: Trigonometric Identities & Equations Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 07 - Trigonometric Functions, Identities & Equations|Lesson 07 — Trigonometric Functions, Identities & Equations]]

> [!ABSTRACT] Core Focus
> Full proofs of compound angle identities, $t = \tan(\theta/2)$ substitution technique, sum-to-product transformations, $R$-form mastery, inverse trig, and step-by-step equation solving algorithms.

---

## 1. Proof of $\sin(A + B)$

**Using the unit circle / area method** (A/L syllabus approach):

Consider a right-angled triangle construction on the unit circle. For angles $A$ and $B$ where $A, B, A+B \in [0°, 90°]$:

Draw angle $A$ from the x-axis, then angle $B$ from that ray. Drop perpendiculars to form two triangles. Using:
$$\text{Area of whole} = \text{Area}_1 + \text{Area}_2$$

A cleaner proof uses the matrix rotation approach:

Rotating by $A$ then by $B$ is the same as rotating by $A+B$:
$$\begin{pmatrix}\cos(A+B) \\ \sin(A+B)\end{pmatrix} = \begin{pmatrix}\cos A & -\sin A \\ \sin A & \cos A\end{pmatrix}\begin{pmatrix}\cos B \\ \sin B\end{pmatrix}$$

Reading off the second row:
$$\sin(A+B) = \sin A\cos B + \cos A\sin B \quad \checkmark$$

Reading off the first row:
$$\cos(A+B) = \cos A\cos B - \sin A\sin B \quad \checkmark$$

---

## 2. Deriving All Double Angle Formulas

**$\sin 2A$** — set $B = A$ in $\sin(A+B)$:
$$\sin 2A = \sin A\cos A + \cos A\sin A = 2\sin A\cos A$$

**Three forms of $\cos 2A$** — set $B = A$ in $\cos(A+B)$:
$$\cos 2A = \cos^2 A - \sin^2 A$$

Replace $\sin^2 A$ using $\sin^2 A = 1 - \cos^2 A$:
$$\cos 2A = \cos^2 A - (1 - \cos^2 A) = 2\cos^2 A - 1$$

Replace $\cos^2 A$ using $\cos^2 A = 1 - \sin^2 A$:
$$\cos 2A = (1 - \sin^2 A) - \sin^2 A = 1 - 2\sin^2 A$$

**$\tan 2A$** — set $B = A$ in $\tan(A+B)$:
$$\tan 2A = \frac{\tan A + \tan A}{1 - \tan A\cdot\tan A} = \frac{2\tan A}{1-\tan^2 A}$$

**Rearranging** (crucial for integration & equation solving):
$$\cos^2 A = \frac{1+\cos 2A}{2}, \qquad \sin^2 A = \frac{1-\cos 2A}{2}$$

---

## 3. Deriving Triple Angle Formulas

**$\sin 3A = \sin(2A + A)$**:
$$= \sin 2A\cos A + \cos 2A\sin A$$
$$= (2\sin A\cos A)\cos A + (1-2\sin^2 A)\sin A$$
$$= 2\sin A\cos^2 A + \sin A - 2\sin^3 A$$
$$= 2\sin A(1-\sin^2 A) + \sin A - 2\sin^3 A$$
$$= 2\sin A - 2\sin^3 A + \sin A - 2\sin^3 A$$
$$\boxed{\sin 3A = 3\sin A - 4\sin^3 A}$$

**$\cos 3A = \cos(2A + A)$**:
$$= \cos 2A\cos A - \sin 2A\sin A$$
$$= (2\cos^2 A - 1)\cos A - 2\sin A\cos A\cdot\sin A$$
$$= 2\cos^3 A - \cos A - 2\cos A\sin^2 A$$
$$= 2\cos^3 A - \cos A - 2\cos A(1-\cos^2 A)$$
$$\boxed{\cos 3A = 4\cos^3 A - 3\cos A}$$

---

## 4. The Half-Angle $t$-Substitution in Full

Let $t = \tan(\theta/2)$. Then using the double angle formulas with half-angle $\theta/2$:

$$\sin\theta = \frac{2t}{1+t^2}, \qquad \cos\theta = \frac{1-t^2}{1+t^2}, \qquad \tan\theta = \frac{2t}{1-t^2}$$

Also: $d\theta = \dfrac{2\,dt}{1+t^2}$ (useful in integration).

**Worked Example** — Solve $5\sin\theta - 12\cos\theta = 4$, $0 \leq \theta \leq 2\pi$:

Substitute $t = \tan(\theta/2)$:
$$5\cdot\frac{2t}{1+t^2} - 12\cdot\frac{1-t^2}{1+t^2} = 4$$

Multiply through by $(1+t^2)$:
$$10t - 12(1-t^2) = 4(1+t^2)$$
$$10t - 12 + 12t^2 = 4 + 4t^2$$
$$8t^2 + 10t - 16 = 0$$
$$4t^2 + 5t - 8 = 0$$

Using the quadratic formula: $t = \dfrac{-5 \pm \sqrt{25+128}}{8} = \dfrac{-5 \pm \sqrt{153}}{8}$

$t_1 \approx 0.925 \Rightarrow \theta = 2\arctan(0.925) \approx 1.35$ rad

$t_2 \approx -2.175 \Rightarrow \theta = 2\arctan(-2.175) \approx -2.00$ rad $\to$ add $2\pi \approx 4.28$ rad

> **Check $\theta = \pi$**: $5(0) - 12(-1) = 12 \neq 4$. So $\theta = \pi$ is not a solution. ✓

---

## 5. Product-to-Sum: Full Set & Derivation Strategy

**Derivation** — Add and subtract the two compound cosine formulas:

$\cos(A-B) + \cos(A+B) = 2\cos A\cos B \Rightarrow \cos A\cos B = \tfrac{1}{2}[\cos(A-B)+\cos(A+B)]$

$\cos(A-B) - \cos(A+B) = 2\sin A\sin B \Rightarrow \sin A\sin B = \tfrac{1}{2}[\cos(A-B)-\cos(A+B)]$

Similarly from sine compound formulas:

$\sin(A+B) + \sin(A-B) = 2\sin A\cos B \Rightarrow \sin A\cos B = \tfrac{1}{2}[\sin(A+B)+\sin(A-B)]$

$\sin(A+B) - \sin(A-B) = 2\cos A\sin B \Rightarrow \cos A\sin B = \tfrac{1}{2}[\sin(A+B)-\sin(A-B)]$

---

## 6. $R$-Form: Full Method and Variants

**Variant 1**: $a\sin\theta + b\cos\theta = R\sin(\theta + \alpha)$

Expand RHS: $R\sin\theta\cos\alpha + R\cos\theta\sin\alpha$

Compare: $R\cos\alpha = a$ and $R\sin\alpha = b$

So: $R = \sqrt{a^2+b^2}$, $\tan\alpha = b/a$

**Variant 2**: $a\sin\theta - b\cos\theta = R\sin(\theta - \alpha)$ (both $a, b > 0$)

Expand: $R\sin\theta\cos\alpha - R\cos\theta\sin\alpha$

Compare: $R\cos\alpha = a$, $R\sin\alpha = b$; same $R$, same $\alpha$.

**Variant 3**: $a\cos\theta + b\sin\theta = R\cos(\theta - \beta)$

Expand: $R\cos\theta\cos\beta + R\sin\theta\sin\beta$

Compare: $R\cos\beta = a$, $R\sin\beta = b$; $R = \sqrt{a^2+b^2}$, $\tan\beta = b/a$.

**Worked Example** — Find max/min of $f(\theta) = 3\cos\theta - 4\sin\theta$:

$R = \sqrt{9+16} = 5$; write as $5\cos(\theta + \alpha)$ where $\tan\alpha = 4/3$.

Maximum $= 5$ (when $\theta + \alpha = 0$, i.e., $\theta = -\alpha$)

Minimum $= -5$ (when $\theta + \alpha = \pi$)

---

## 7. Step-by-Step Algorithm: Solving Trig Equations

```
Step 1: Identify the type
        - Single function (sin, cos, tan): go to general solution
        - Quadratic in one function: factor or use quadratic formula
        - Mixed functions: use identities to reduce to single type
        - R-form: convert, then solve

Step 2: Reduce to form sin θ = k, cos θ = k, or tan θ = k

Step 3: Find principal value α = arcsin(k), arccos(k), or arctan(k)

Step 4: Write general solution:
        sin: θ = nπ + (-1)ⁿα
        cos: θ = 2nπ ± α  
        tan: θ = nπ + α

Step 5: If range specified, substitute n = 0, ±1, ±2, ...
        and keep only solutions in range

Step 6: Verify each solution in the original equation
```

**Worked Example** — Solve $\sin\theta + \sin 3\theta = \cos\theta + \cos 3\theta$ for $0 \leq \theta < 2\pi$:

**LHS**: $\sin 3\theta + \sin\theta = 2\sin 2\theta\cos\theta$ (sum-to-product)

**RHS**: $\cos 3\theta + \cos\theta = 2\cos 2\theta\cos\theta$ (sum-to-product)

Equation becomes: $2\sin 2\theta\cos\theta = 2\cos 2\theta\cos\theta$

$2\cos\theta(\sin 2\theta - \cos 2\theta) = 0$

**Case 1**: $\cos\theta = 0 \Rightarrow \theta = \pi/2, 3\pi/2$

**Case 2**: $\sin 2\theta = \cos 2\theta \Rightarrow \tan 2\theta = 1 \Rightarrow 2\theta = n\pi + \pi/4$

$\theta = n\pi/2 + \pi/8$: in $[0,2\pi)$: $\theta = \pi/8, 5\pi/8, 9\pi/8, 13\pi/8$

**All solutions**: $\pi/8, \pi/2, 5\pi/8, 9\pi/8, 3\pi/2, 13\pi/8$

---

## 8. Inverse Trig: Key Identities & Worked Problems

**Composition identities** (crucial for A/L):
$$\sin(\sin^{-1}x) = x, \quad \sin^{-1}(\sin\theta) = \theta \text{ only if } \theta \in [-\pi/2, \pi/2]$$
$$\cos(\cos^{-1}x) = x, \quad \cos^{-1}(\cos\theta) = \theta \text{ only if } \theta \in [0, \pi]$$

**Worked Example** — Prove $\tan^{-1}(1/2) + \tan^{-1}(1/3) = \pi/4$:

Let $\alpha = \tan^{-1}(1/2)$ and $\beta = \tan^{-1}(1/3)$.

$$\tan(\alpha + \beta) = \frac{\tan\alpha + \tan\beta}{1 - \tan\alpha\tan\beta} = \frac{1/2 + 1/3}{1 - (1/2)(1/3)} = \frac{5/6}{5/6} = 1$$

Since $\alpha, \beta \in (0, \pi/4)$, we have $\alpha + \beta \in (0, \pi/2)$, so $\tan^{-1}(1) = \pi/4$. ✓

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Prove $\sin(A+B) = \sin A\cos B + \cos A\sin B$ — which method gives the clearest proof? :: Rotation matrix: rotate point $(\cos B, \sin B)$ by angle $A$; reading the $y$-coordinate gives the formula directly. <!--SR:!2026-11-20,1,230-->

What are the three forms of $\cos 2A$? :: $\cos^2 A - \sin^2 A = 2\cos^2 A - 1 = 1 - 2\sin^2 A$ <!--SR:!2026-11-21,2,250-->

State $\sin 3A$ in terms of $\sin A$ only. :: $3\sin A - 4\sin^3 A$ <!--SR:!2026-11-22,3,250-->

State $\cos 3A$ in terms of $\cos A$ only. :: $4\cos^3 A - 3\cos A$ <!--SR:!2026-11-22,3,250-->

Write $\sin A\cos B$ as a sum. :: $\tfrac{1}{2}[\sin(A+B) + \sin(A-B)]$ <!--SR:!2026-11-23,4,250-->

Write $\cos A\cos B$ as a sum. :: $\tfrac{1}{2}[\cos(A-B) + \cos(A+B)]$ <!--SR:!2026-11-23,4,250-->

Write $\sin P + \sin Q$ as a product. :: $2\sin\!\left(\tfrac{P+Q}{2}\right)\cos\!\left(\tfrac{P-Q}{2}\right)$ <!--SR:!2026-11-24,5,250-->

Write $\cos P - \cos Q$ as a product. :: $-2\sin\!\left(\tfrac{P+Q}{2}\right)\sin\!\left(\tfrac{P-Q}{2}\right)$ <!--SR:!2026-11-24,5,250-->

For $t = \tan(\theta/2)$, what is $\sin\theta$ in terms of $t$? :: $\dfrac{2t}{1+t^2}$ <!--SR:!2026-11-25,6,250-->

For $t = \tan(\theta/2)$, what is $\cos\theta$ in terms of $t$? :: $\dfrac{1-t^2}{1+t^2}$ <!--SR:!2026-11-25,6,250-->

What caution must you take when using the $t$-substitution? :: The substitution misses $\theta = \pi$ (where $t \to \infty$). Always check $\theta = \pi$ separately in the original equation. <!--SR:!2026-11-26,7,250-->

For $a\sin\theta + b\cos\theta = R\sin(\theta+\alpha)$, what is $R$ and $\tan\alpha$? :: $R = \sqrt{a^2+b^2}$, $\tan\alpha = b/a$ <!--SR:!2026-11-26,7,250-->

Prove $\tan^{-1}(1/2) + \tan^{-1}(1/3) = \pi/4$ — key step? :: $\tan(\alpha+\beta) = \frac{1/2+1/3}{1-(1/2)(1/3)} = \frac{5/6}{5/6} = 1$, and since $\alpha+\beta \in (0,\pi/2)$, it equals $\pi/4$. <!--SR:!2026-11-27,8,250-->

Solve $\sin\theta + \sin 3\theta = \cos\theta + \cos 3\theta$ — key factoring step? :: Apply sum-to-product to both sides: $2\sin 2\theta\cos\theta = 2\cos 2\theta\cos\theta$, then factor $2\cos\theta(\sin 2\theta - \cos 2\theta) = 0$. <!--SR:!2026-11-27,8,250-->

What is the range of $\tan^{-1}x$? :: $\left(-\dfrac{\pi}{2}, \dfrac{\pi}{2}\right)$ (open interval — excludes the endpoints) <!--SR:!2026-11-28,9,250-->
