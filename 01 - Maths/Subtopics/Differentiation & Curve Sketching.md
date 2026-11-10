---
title: Differentiation & Curve Sketching Guide
subject: AL Combined Maths
subtopic: Calculus
tags:
  - AL-Maths
  - Subtopic
  - Differentiation
  - CurveSketching
  - Flashcards
---
# :LiTrendingUp: Subtopic: Differentiation & Curve Sketching Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 08 - Differential Calculus & Applications|Lesson 08 — Differential Calculus & Applications]]

> [!ABSTRACT] Core Focus
> Asymptote analysis (vertical, horizontal, oblique), 7-step curve sketching algorithm, L'Hôpital's Rule, optimisation worked problems, and second-order parametric differentiation.

---

## 1. Asymptotes

**Vertical Asymptotes** — occur where denominator $= 0$ (and numerator $\neq 0$):
$$x = a \text{ is a vertical asymptote if } \lim_{x \to a^\pm} f(x) = \pm\infty$$

**Horizontal Asymptotes** — behaviour as $x \to \pm\infty$:
$$y = L \text{ is a horizontal asymptote if } \lim_{x \to \pm\infty} f(x) = L$$

For rational functions $\dfrac{P(x)}{Q(x)}$:
- $\deg P < \deg Q$: horizontal asymptote $y = 0$
- $\deg P = \deg Q$: horizontal asymptote $y = \dfrac{\text{leading coeff of }P}{\text{leading coeff of }Q}$
- $\deg P > \deg Q$: **no** horizontal asymptote (oblique or higher instead)

**Oblique Asymptotes** — when $\deg P = \deg Q + 1$, perform polynomial long division:
$$f(x) = ax + b + \frac{r(x)}{Q(x)} \implies y = ax + b \text{ is the oblique asymptote}$$

**Worked Example** — Find asymptotes of $f(x) = \dfrac{x^2+1}{x-1}$:

- **Vertical**: $x = 1$ (denominator = 0, numerator = 2 ≠ 0)
- **Oblique**: divide: $\dfrac{x^2+1}{x-1} = x+1 + \dfrac{2}{x-1}$, so $y = x+1$ is oblique asymptote

---

## 2. The 7-Step Curve Sketching Algorithm

```
Step 1: Domain
        Find all x where f(x) is defined. State restrictions.

Step 2: Symmetry
        Even: f(-x) = f(x) → symmetric about y-axis
        Odd:  f(-x) = -f(x) → symmetric about origin

Step 3: Intercepts
        y-intercept: set x = 0, find f(0)
        x-intercepts: solve f(x) = 0

Step 4: Asymptotes
        Vertical, horizontal, oblique (see Section 1)

Step 5: First Derivative f'(x)
        Find critical points (f'(x) = 0 or undefined)
        Determine intervals of increase (f' > 0) and decrease (f' < 0)

Step 6: Second Derivative f''(x)
        Find inflection points (f''(x) = 0 with sign change)
        Concave up: f'' > 0; Concave down: f'' < 0
        Classify stationary points (max/min)

Step 7: Sketch
        Plot intercepts, asymptotes, stationary points, inflection points
        Draw smooth curve through all features
```

**Worked Example** — Sketch $f(x) = \dfrac{x}{x^2-1}$:

1. **Domain**: $x \neq \pm 1$, i.e., $(-\infty,-1)\cup(-1,1)\cup(1,\infty)$
2. **Symmetry**: $f(-x) = \dfrac{-x}{x^2-1} = -f(x)$ → **odd** (symmetric about origin)
3. **Intercepts**: $f(0) = 0$ (passes through origin)
4. **Asymptotes**: Vertical: $x = 1$, $x = -1$; Horizontal: $y = 0$ (deg numerator < denominator)
5. **$f'(x)$**: $f'(x) = \dfrac{(x^2-1) - x(2x)}{(x^2-1)^2} = \dfrac{-x^2-1}{(x^2-1)^2} = \dfrac{-(x^2+1)}{(x^2-1)^2}$

   Since $x^2+1 > 0$ always, $f'(x) < 0$ everywhere in domain → **strictly decreasing** on each interval. No stationary points.

6. **$f''(x)$**: $f''(x) = \dfrac{2x(x^2+3)}{(x^2-1)^3}$ — inflection at $x = 0$ (sign change since denominator changes sign)
7. **Sketch**: Three branches; decreasing on each; inflection at origin.

---

## 3. L'Hôpital's Rule — Full Treatment

**When applicable**: $\lim_{x\to a}\dfrac{f(x)}{g(x)}$ gives $\dfrac{0}{0}$ or $\dfrac{\infty}{\infty}$.

**Rule**: $\displaystyle\lim_{x\to a}\frac{f(x)}{g(x)} = \lim_{x\to a}\frac{f'(x)}{g'(x)}$ (if the right limit exists).

Can be applied repeatedly when $\dfrac{0}{0}$ or $\dfrac{\infty}{\infty}$ persists.

**Other indeterminate forms** — convert first:

| Form | Conversion |
|---|---|
| $0 \cdot \infty$ | Write as $\dfrac{0}{1/\infty}$ or $\dfrac{\infty}{1/0}$ |
| $\infty - \infty$ | Combine fractions, then apply |
| $1^\infty$, $0^0$, $\infty^0$ | Take $\ln$: $\lim \ln f = \lim \ln(\cdot)$, then exponentiate |

**Worked Examples**:

$$\lim_{x\to 0}\frac{\sin 3x}{x} \xrightarrow{\text{L'H}} \lim_{x\to 0}\frac{3\cos 3x}{1} = 3$$

$$\lim_{x\to 1}\frac{\ln x}{x-1} \xrightarrow{\text{L'H}} \lim_{x\to 1}\frac{1/x}{1} = 1$$

$$\lim_{x\to\infty}\frac{x^2}{e^x} \xrightarrow{\text{L'H}} \lim_{x\to\infty}\frac{2x}{e^x} \xrightarrow{\text{L'H}} \lim_{x\to\infty}\frac{2}{e^x} = 0$$

$$\lim_{x\to 0^+} x\ln x = \lim_{x\to 0^+}\frac{\ln x}{1/x} \xrightarrow{\text{L'H}} \lim_{x\to 0^+}\frac{1/x}{-1/x^2} = \lim_{x\to 0^+}(-x) = 0$$

---

## 4. Optimisation — Worked Problems

### Problem 1: Minimum Surface Area Cylinder

A cylinder of fixed volume $V$ must have minimum surface area. Find the optimal $h$ and $r$.

Volume: $V = \pi r^2 h \Rightarrow h = \dfrac{V}{\pi r^2}$

Surface area: $S = 2\pi r^2 + 2\pi r h = 2\pi r^2 + \dfrac{2V}{r}$

$$\frac{dS}{dr} = 4\pi r - \frac{2V}{r^2} = 0 \implies r^3 = \frac{V}{2\pi} \implies r = \left(\frac{V}{2\pi}\right)^{1/3}$$

Then $h = \dfrac{V}{\pi r^2} = 2r$ → **optimal cylinder has height = diameter**.

$\dfrac{d^2S}{dr^2} = 4\pi + \dfrac{4V}{r^3} > 0$ ✓ (minimum confirmed)

### Problem 2: Closest Point on Parabola to a Given Point

Find the point on $y = x^2$ closest to $(3, 0)$.

Distance squared: $D = (x-3)^2 + x^4$

$$\frac{dD}{dx} = 2(x-3) + 4x^3 = 0$$

By inspection or Newton's method: $x \approx 1.265$ (solve numerically for exact exam problems, or for $x=1$: $D = 4+1 = 5$; for $x=1.5$: $D = 2.25+5.0625 = 7.31$... try $x=1$).

For A/L purposes, **set up the equation** and verify with the second derivative test.

### Problem 3: Maximum Area Rectangle in Semicircle

Semicircle of radius $r$; rectangle inscribed with base on diameter.

Let half-width $= x$. Height $= \sqrt{r^2-x^2}$. Area $= 2x\sqrt{r^2-x^2}$.

$$\frac{dA}{dx} = 2\sqrt{r^2-x^2} + 2x\cdot\frac{-x}{\sqrt{r^2-x^2}} = \frac{2(r^2-2x^2)}{\sqrt{r^2-x^2}} = 0$$

$r^2 - 2x^2 = 0 \Rightarrow x = \dfrac{r}{\sqrt{2}}$

Maximum area $= 2\cdot\dfrac{r}{\sqrt{2}}\cdot\dfrac{r}{\sqrt{2}} = r^2$

---

## 5. Rate of Change Problems

**Related rates**: Two quantities $x$ and $y$ both depend on time $t$. Use chain rule:
$$\frac{dy}{dt} = \frac{dy}{dx}\cdot\frac{dx}{dt}$$

**Worked Example** — A ladder 5 m long leans against a wall. The foot slides out at 1 m/s. How fast is the top sliding down when the foot is 3 m from the wall?

$x^2 + y^2 = 25$. Differentiate w.r.t. $t$: $2x\dfrac{dx}{dt} + 2y\dfrac{dy}{dt} = 0$

At $x = 3$: $y = 4$. $\dfrac{dx}{dt} = 1$. So: $6(1) + 8\dfrac{dy}{dt} = 0 \Rightarrow \dfrac{dy}{dt} = -\dfrac{3}{4}$ m/s.

The top slides **down** at $\dfrac{3}{4}$ m/s.

---

## 6. Proving Derivative Formulas

**Derivative of $\ln x$** from first principles:
$$\frac{d}{dx}[\ln x] = \lim_{h\to 0}\frac{\ln(x+h)-\ln x}{h} = \lim_{h\to 0}\frac{1}{h}\ln\!\left(1+\frac{h}{x}\right)$$
$$= \lim_{h\to 0}\frac{1}{x}\cdot\frac{x}{h}\ln\!\left(1+\frac{h}{x}\right) = \frac{1}{x}\lim_{u\to 0}\frac{\ln(1+u)}{u} = \frac{1}{x}\cdot 1 = \frac{1}{x}$$

**Derivative of $\tan^{-1}x$** via implicit differentiation:

Let $y = \tan^{-1}x$, so $\tan y = x$. Differentiate implicitly: $\sec^2 y\dfrac{dy}{dx} = 1$

$\dfrac{dy}{dx} = \dfrac{1}{\sec^2 y} = \dfrac{1}{1+\tan^2 y} = \dfrac{1}{1+x^2}$ ✓

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State the 4 steps to find and classify stationary points. :: 1) Find $f'(x)$; 2) Solve $f'(x)=0$; 3) Find $f''(x)$ at each point; 4) $f''>0$: min, $f''<0$: max, $f''=0$: use sign test. <!--SR:!2026-11-20,1,230-->

What is the condition for a vertical asymptote at $x=a$? :: Denominator $= 0$ at $x=a$ and numerator $\neq 0$; and $\lim_{x\to a}|f(x)| = \infty$. <!--SR:!2026-11-21,2,250-->

For a rational function $P/Q$ with $\deg P = \deg Q$, what is the horizontal asymptote? :: $y = \dfrac{\text{leading coefficient of }P}{\text{leading coefficient of }Q}$ <!--SR:!2026-11-22,3,250-->

When does a rational function have an oblique asymptote? :: When $\deg P = \deg Q + 1$; find it by polynomial long division. <!--SR:!2026-11-22,3,250-->

State L'Hôpital's Rule and when to apply it. :: For $\frac{0}{0}$ or $\frac{\infty}{\infty}$: $\lim\frac{f}{g} = \lim\frac{f'}{g'}$ (if the right-hand limit exists). <!--SR:!2026-11-23,4,250-->

What are the 3 indeterminate forms that need conversion before L'Hôpital? :: $0\cdot\infty$, $\infty-\infty$, and $1^\infty$/$0^0$/$\infty^0$ (take $\ln$ for the last three). <!--SR:!2026-11-23,4,250-->

Evaluate $\lim_{x\to 0}x\ln x$. :: $0$ (write as $\frac{\ln x}{1/x}$, apply L'Hôpital to get $\lim(-x) = 0$). <!--SR:!2026-11-24,5,250-->

What does $f''(x) > 0$ tell you about the curve? :: The curve is **concave upward** (shaped like a cup; lies above its tangent lines). <!--SR:!2026-11-24,5,250-->

What is a point of inflection and how do you find it? :: Where concavity changes; find by solving $f''(x) = 0$ and verifying sign change of $f''$ on either side. <!--SR:!2026-11-25,6,250-->

Prove $\frac{d}{dx}[\tan^{-1}x] = \frac{1}{1+x^2}$. :: Let $y = \tan^{-1}x$, so $\tan y = x$. Implicit diff: $\sec^2 y \cdot \frac{dy}{dx} = 1$; then $\frac{dy}{dx} = \frac{1}{\sec^2 y} = \frac{1}{1+\tan^2 y} = \frac{1}{1+x^2}$. <!--SR:!2026-11-25,6,250-->

For a cylinder of fixed volume $V$, what is the optimal ratio $h:r$ for minimum surface area? :: $h = 2r$ (height equals diameter). <!--SR:!2026-11-26,7,250-->

State the related rates formula for two quantities $x$, $y$ depending on time $t$. :: $\frac{dy}{dt} = \frac{dy}{dx}\cdot\frac{dx}{dt}$ (chain rule applied to time). <!--SR:!2026-11-26,7,250-->

For $f(x) = \frac{x}{x^2-1}$, is the function odd, even, or neither? :: **Odd**: $f(-x) = \frac{-x}{x^2-1} = -f(x)$, so symmetric about the origin. <!--SR:!2026-11-27,8,250-->

How do you differentiate $y = a^x$ where $a > 0$? :: Write $y = e^{x\ln a}$, then $\frac{dy}{dx} = e^{x\ln a}\cdot\ln a = a^x\ln a$. <!--SR:!2026-11-27,8,250-->

What is the second parametric derivative $\frac{d^2y}{dx^2}$ formula? :: $\dfrac{d^2y}{dx^2} = \dfrac{\frac{d}{dt}\!\left(\frac{dy}{dx}\right)}{\frac{dx}{dt}}$ <!--SR:!2026-11-28,9,250-->
