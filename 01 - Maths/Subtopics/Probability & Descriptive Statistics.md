---
title: Probability & Descriptive Statistics Guide
subject: AL Combined Maths
subtopic: Probability
tags:
  - AL-Maths
  - Subtopic
  - Probability
  - Statistics
---
# :LiDices: Subtopic: Probability & Descriptive Statistics Guide

> [!ABSTRACT] Core Focus
> Addition and multiplication laws of probability, conditional probability, Bayes' theorem, discrete/continuous random variables, expectation, variance, standard deviation, common distributions, and descriptive statistics measures.

---

## 1. Basic Probability Laws

### Addition Law
For any two events $A$ and $B$:
$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
- **Mutually exclusive events**: $P(A \cap B) = 0 \Rightarrow P(A \cup B) = P(A) + P(B)$

### Multiplication Law
$$P(A \cap B) = P(A) \cdot P(B | A) = P(B) \cdot P(A | B)$$
- **Independent events**: $P(A \cap B) = P(A) \cdot P(B)$
- **Complement rule**: $P(A') = 1 - P(A)$

---

## 2. Conditional Probability

$$P(A | B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0$$

**Key properties:**
- $0 \le P(A | B) \le 1$
- $P(A' | B) = 1 - P(A | B)$
- $P(A_1 \cup A_2 | B) = P(A_1 | B) + P(A_2 | B) - P(A_1 \cap A_2 | B)$

---

## 3. Total Probability Theorem

If $\{A_1, A_2, \dots, A_n\}$ is a partition of the sample space ($A_i$ mutually exclusive and exhaustive):
$$P(B) = \sum_{i=1}^n P(B | A_i) P(A_i)$$

---

## 4. Bayes' Theorem

$$P(A_i | B) = \frac{P(B | A_i) P(A_i)}{\sum_{j=1}^n P(B | A_j) P(A_j)}$$

**Applications:** Medical testing, spam filtering, machine learning classification.

---

## 5. Discrete Random Variables

### Probability Mass Function (PMF)
$P(X = x) = p(x)$ where $\sum_x p(x) = 1$ and $p(x) \ge 0$.

### Expectation (Mean)
$$E(X) = \mu = \sum_x x \cdot p(x)$$

### Variance
$$\text{Var}(X) = \sigma^2 = E[(X - \mu)^2] = E(X^2) - [E(X)]^2 = \sum_x (x - \mu)^2 p(x)$$

### Standard Deviation
$$\sigma = \sqrt{\text{Var}(X)}$$

### Properties of Expectation & Variance
| Property | Formula |
|----------|---------|
| $E(aX + b)$ | $aE(X) + b$ |
| $\text{Var}(aX + b)$ | $a^2 \text{Var}(X)$ |
| $E(X + Y)$ | $E(X) + E(Y)$ |
| $\text{Var}(X + Y)$ | $\text{Var}(X) + \text{Var}(Y)$ (if independent) |

---

## 6. Continuous Random Variables

### Probability Density Function (PDF)
$f(x) \ge 0$, $\int_{-\infty}^{\infty} f(x) \, dx = 1$

$$P(a \le X \le b) = \int_a^b f(x) \, dx$$

### Cumulative Distribution Function (CDF)
$$F(x) = P(X \le x) = \int_{-\infty}^x f(t) \, dt$$

### Expectation & Variance
$$E(X) = \int_{-\infty}^{\infty} x f(x) \, dx$$
$$\text{Var}(X) = \int_{-\infty}^{\infty} (x - \mu)^2 f(x) \, dx = E(X^2) - \mu^2$$

---

## 7. Common Discrete Distributions

### Binomial Distribution $X \sim B(n, p)$
- $n$ independent Bernoulli trials, success probability $p$
- PMF: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \dots, n$
- $E(X) = np$
- $\text{Var}(X) = np(1-p)$

### Poisson Distribution $X \sim \text{Po}(\lambda)$
- Events occurring randomly at average rate $\lambda$ per unit
- PMF: $P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}, \quad k = 0, 1, 2, \dots$
- $E(X) = \lambda$
- $\text{Var}(X) = \lambda$
- **Approximation**: $B(n, p) \approx \text{Po}(np)$ when $n$ large, $p$ small ($n > 50, np < 5$)

### Geometric Distribution $X \sim \text{Geo}(p)$
- Number of trials until first success
- PMF: $P(X = k) = (1-p)^{k-1}p, \quad k = 1, 2, \dots$
- $E(X) = \frac{1}{p}$
- $\text{Var}(X) = \frac{1-p}{p^2}$

---

## 8. Common Continuous Distributions

### Normal Distribution $X \sim N(\mu, \sigma^2)$
- PDF: $f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$
- Standard normal: $Z = \frac{X - \mu}{\sigma} \sim N(0, 1)$
- $E(X) = \mu$, $\text{Var}(X) = \sigma^2$
- **Empirical rule**: 68-95-99.7% within 1, 2, 3 $\sigma$ of $\mu$
- **Normal approximation to binomial**: $B(n, p) \approx N(np, np(1-p))$ when $np > 5$ and $n(1-p) > 5$ (use continuity correction)

### Exponential Distribution $X \sim \text{Exp}(\lambda)$
- Time between events in Poisson process
- PDF: $f(x) = \lambda e^{-\lambda x}, \quad x \ge 0$
- $E(X) = \frac{1}{\lambda}$, $\text{Var}(X) = \frac{1}{\lambda^2}$
- **Memoryless property**: $P(X > s + t | X > s) = P(X > t)$

### Uniform Distribution $X \sim U(a, b)$
- PDF: $f(x) = \frac{1}{b-a}, \quad a \le x \le b$
- $E(X) = \frac{a+b}{2}$
- $\text{Var}(X) = \frac{(b-a)^2}{12}$

---

## 9. Descriptive Statistics

### Measures of Central Tendency
| Measure | Formula (Ungrouped) | Formula (Grouped) |
|---------|---------------------|-------------------|
| **Mean** | $\bar{x} = \frac{\sum x_i}{n}$ | $\bar{x} = \frac{\sum f_i x_i}{\sum f_i}$ |
| **Median** | Middle value (ordered) | $L + \frac{\frac{n}{2} - F}{f} \times c$ |
| **Mode** | Most frequent value | $L + \frac{f_1 - f_0}{2f_1 - f_0 - f_2} \times c$ |

### Measures of Dispersion
| Measure | Formula |
|---------|---------|
| **Range** | $x_{\max} - x_{\min}$ |
| **Variance** | $s^2 = \frac{\sum (x_i - \bar{x})^2}{n-1}$ (sample) |
| **Standard Deviation** | $s = \sqrt{s^2}$ |
| **Interquartile Range (IQR)** | $Q_3 - Q_1$ |
| **Mean Absolute Deviation** | $\frac{\sum |x_i - \bar{x}|}{n}$ |

### Measures of Position
- **Quartiles**: $Q_1$ (25%), $Q_2$ = Median (50%), $Q_3$ (75%)
- **Percentiles**: $P_k$ = value below which $k\%$ of data falls
- **Z-score**: $z = \frac{x - \bar{x}}{s}$ (standardized value)

### Skewness & Kurtosis
- **Pearson's skewness**: $\frac{3(\bar{x} - \text{Median})}{s}$
- **Moment skewness**: $\frac{\frac{1}{n}\sum(x_i - \bar{x})^3}{s^3}$
- **Kurtosis**: Measures tail heaviness (normal = 3, excess kurtosis = 0)

---

## 10. Linear Combinations of Random Variables

If $X_1, X_2, \dots, X_n$ are independent:
$$E\left(\sum a_i X_i\right) = \sum a_i E(X_i)$$
$$\text{Var}\left(\sum a_i X_i\right) = \sum a_i^2 \text{Var}(X_i)$$

**Sum of independent normals**: $\sum X_i \sim N\left(\sum \mu_i, \sum \sigma_i^2\right)$

**Sample mean**: $\bar{X} = \frac{1}{n}\sum X_i \sim N\left(\mu, \frac{\sigma^2}{n}\right)$ (Central Limit Theorem for large $n$)

---

## 11. Key Exam Tips

> [!TIP] Exam Technique
> - **Always define events/random variables clearly** before calculating
> - **Check independence** before using $P(A \cap B) = P(A)P(B)$
> - **Use continuity correction** for normal approximation to discrete distributions
> - **State distribution assumptions** (e.g., "assuming $X \sim B(n,p)$...")
> - **For Bayes' theorem**: Draw a tree diagram or table to organize $P(A_i)$ and $P(B|A_i)$
> - **Descriptive stats**: Distinguish between population ($\sigma$) and sample ($s$) formulas
> - **CLT applies** when $n \ge 30$ or population is normal

---

## 12. Summary of Distribution Parameters

| Distribution | Parameters | Mean | Variance | Support |
|--------------|------------|------|----------|---------|
| Binomial | $n, p$ | $np$ | $np(1-p)$ | $0, 1, \dots, n$ |
| Poisson | $\lambda$ | $\lambda$ | $\lambda$ | $0, 1, 2, \dots$ |
| Geometric | $p$ | $1/p$ | $(1-p)/p^2$ | $1, 2, \dots$ |
| Normal | $\mu, \sigma^2$ | $\mu$ | $\sigma^2$ | $(-\infty, \infty)$ |
| Exponential | $\lambda$ | $1/\lambda$ | $1/\lambda^2$ | $[0, \infty)$ |
| Uniform | $a, b$ | $(a+b)/2$ | $(b-a)^2/12$ | $[a, b]$ |