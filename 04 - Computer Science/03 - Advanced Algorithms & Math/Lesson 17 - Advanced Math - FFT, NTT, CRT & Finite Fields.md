---
title: Lesson 17 - Advanced Math - FFT, NTT, CRT & Finite Fields
subject: Computer Science
unit: 17
competency: Implement polynomial multiplication via FFT/NTT, apply CRT, and reason about finite field arithmetic
tags:
  - Computer-Science
  - Competitive-Programming
  - FFT
  - NTT
  - CRT
  - FiniteFields
  - AdvancedMath
  - Flashcards
---
---
# :LiBook: Lesson 17: Advanced Math — FFT, NTT, CRT & Finite Fields

> [!ABSTRACT] Scope
> Master the advanced mathematical machinery used in high-level competitive programming and systems programming: polynomial multiplication via FFT/NTT, the Chinese Remainder Theorem, finite field arithmetic, and Newton's method for fast division.

> [!WARNING] Prerequisites
> Before studying this lesson, be comfortable with [[03 - Advanced Algorithms & Math/Lesson 08 - Number Theory & Modular Arithmetic|Lesson 08 — Number Theory & Modular Arithmetic]] (binary exponentiation, modular inverses, Sieve of Eratosthenes).

---

## 1. Fast Fourier Transform (FFT) — Polynomial Multiplication in $O(N \log N)$

### 1.1 The Problem

**Naive polynomial multiplication** of two polynomials of degree $N$ takes $O(N^2)$ time (each coefficient of $A$ multiplied with each coefficient of $B$).

FFT reduces this to $O(N \log N)$ by:
1. **Evaluate** both polynomials at $N$ special points (roots of unity) — $O(N \log N)$.
2. **Pointwise multiply** the evaluations — $O(N)$.
3. **Interpolate** (Inverse FFT) back to coefficient form — $O(N \log N)$.

### 1.2 Where FFT Appears in CP

- Multiplying large numbers (BigInt multiplication).
- Counting convolutions: "How many ways can values from array $A$ and array $B$ sum to $k$?"
- String matching with wildcards.
- Generating functions.

### 1.3 FFT Implementation (Complex Numbers)

```cpp
#include <bits/stdc++.h>
using namespace std;

using cd = complex<double>;
const double PI = acos(-1.0);

// In-place iterative FFT
// 'invert' = false for forward FFT, true for inverse FFT
void fft(vector<cd>& a, bool invert) {
    int n = a.size();
    if (n == 1) return;

    // Bit-reversal permutation
    for (int i = 1, j = 0; i < n; i++) {
        int bit = n >> 1;
        for (; j & bit; bit >>= 1) j ^= bit;
        j ^= bit;
        if (i < j) swap(a[i], a[j]);
    }

    // Butterfly operations
    for (int len = 2; len <= n; len <<= 1) {
        double ang = 2 * PI / len * (invert ? -1 : 1);
        cd wlen(cos(ang), sin(ang)); // Primitive root of unity

        for (int i = 0; i < n; i += len) {
            cd w(1);
            for (int j = 0; j < len / 2; j++) {
                cd u = a[i + j];
                cd v = a[i + j + len / 2] * w;
                a[i + j] = u + v;
                a[i + j + len / 2] = u - v;
                w *= wlen;
            }
        }
    }

    if (invert) {
        for (auto& x : a) x /= n;
    }
}

// Multiply two polynomials given as coefficient vectors
// Returns coefficient vector of the product
vector<long long> multiplyPolynomials(const vector<int>& a, const vector<int>& b) {
    vector<cd> fa(a.begin(), a.end()), fb(b.begin(), b.end());

    int n = 1;
    while (n < (int)(a.size() + b.size())) n <<= 1;
    fa.resize(n);
    fb.resize(n);

    fft(fa, false); // Forward FFT
    fft(fb, false);

    for (int i = 0; i < n; i++) fa[i] *= fb[i]; // Pointwise multiply

    fft(fa, true); // Inverse FFT

    vector<long long> result(n);
    for (int i = 0; i < n; i++) {
        result[i] = llround(fa[i].real()); // Round to nearest integer
    }
    // Trim trailing zeros
    while (result.size() > 1 && result.back() == 0) result.pop_back();
    return result;
}
```

> [!WARNING] Floating-Point Precision
> FFT uses `complex<double>`, which introduces rounding errors. For coefficients up to $\approx 10^{15}$, results can become inaccurate. When exact integer arithmetic is required, use **NTT** instead.

---

## 2. Number Theoretic Transform (NTT) — Exact Integer FFT

### 2.1 Why NTT?

NTT is FFT performed over a **finite field** $\mathbb{Z}_p$ (integers modulo a prime $p$) instead of complex numbers. This gives:
- **Exact integer arithmetic** — no floating-point errors.
- All operations are modular multiplications — fast and precise.

### 2.2 NTT-Friendly Primes

NTT requires a prime $p$ such that $p - 1$ is divisible by a large power of 2 (so we can find primitive roots of unity of order $2^k$).

| NTT Prime $p$ | $p - 1$ Factorization | Primitive Root $g$ | Max Transform Size $2^k$ |
| :--- | :--- | :--- | :--- |
| $998244353$ | $2^{23} \times 7 \times 17$ | $3$ | $2^{23} \approx 8.4 \times 10^6$ |
| $985661441$ | $2^{23} \times \ldots$ | $3$ | $2^{23}$ |
| $469762049$ | $2^{26} \times 7$ | $3$ | $2^{26}$ |

> [!TIP] The Magic Number
> $998244353$ is the most common NTT modulus in competitive programming. If a problem says "output answer modulo $998244353$", it's a strong hint that NTT/polynomial multiplication is involved!

### 2.3 NTT Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

const long long MOD = 998244353;
const long long G = 3; // Primitive root of MOD

long long binpow(long long a, long long b, long long mod) {
    a %= mod;
    long long res = 1;
    while (b > 0) {
        if (b & 1) res = res * a % mod;
        a = a * a % mod;
        b >>= 1;
    }
    return res;
}

void ntt(vector<long long>& a, bool invert) {
    int n = a.size();
    if (n == 1) return;

    // Bit-reversal permutation
    for (int i = 1, j = 0; i < n; i++) {
        int bit = n >> 1;
        for (; j & bit; bit >>= 1) j ^= bit;
        j ^= bit;
        if (i < j) swap(a[i], a[j]);
    }

    for (int len = 2; len <= n; len <<= 1) {
        long long w = invert ? binpow(G, MOD - 1 - (MOD - 1) / len, MOD)
                             : binpow(G, (MOD - 1) / len, MOD);

        for (int i = 0; i < n; i += len) {
            long long wn = 1;
            for (int j = 0; j < len / 2; j++) {
                long long u = a[i + j];
                long long v = a[i + j + len / 2] * wn % MOD;
                a[i + j] = (u + v) % MOD;
                a[i + j + len / 2] = (u - v + MOD) % MOD;
                wn = wn * w % MOD;
            }
        }
    }

    if (invert) {
        long long n_inv = binpow(n, MOD - 2, MOD);
        for (auto& x : a) x = x * n_inv % MOD;
    }
}

vector<long long> multiplyNTT(vector<long long> a, vector<long long> b) {
    int result_size = a.size() + b.size() - 1;
    int n = 1;
    while (n < result_size) n <<= 1;
    a.resize(n); b.resize(n);

    ntt(a, false);
    ntt(b, false);
    for (int i = 0; i < n; i++) a[i] = a[i] * b[i] % MOD;
    ntt(a, true);

    a.resize(result_size);
    return a;
}
```

---

## 3. Chinese Remainder Theorem (CRT)

### 3.1 The Idea

Given a system of simultaneous congruences with **pairwise coprime** moduli:

$$x \equiv r_1 \pmod{m_1}$$
$$x \equiv r_2 \pmod{m_2}$$
$$\vdots$$
$$x \equiv r_k \pmod{m_k}$$

CRT guarantees a **unique** solution $x$ modulo $M = m_1 \cdot m_2 \cdots m_k$.

### 3.2 CP Use Cases

- Reconstructing a large answer from results computed under different primes (e.g., NTT with multiple primes for arbitrary modulus).
- Solving systems of modular equations.
- Hash collision reduction (using multiple hash bases).

### 3.3 CRT for Two Congruences

Given $x \equiv r_1 \pmod{m_1}$ and $x \equiv r_2 \pmod{m_2}$ where $\gcd(m_1, m_2) = 1$:

$$x = r_1 + m_1 \cdot \frac{r_2 - r_1}{m_1} \pmod{m_1 \cdot m_2}$$

where $\frac{1}{m_1}$ means the modular inverse of $m_1$ modulo $m_2$.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Extended Euclidean Algorithm: finds x, y such that a*x + b*y = gcd(a, b)
long long extgcd(long long a, long long b, long long& x, long long& y) {
    if (b == 0) {
        x = 1; y = 0;
        return a;
    }
    long long x1, y1;
    long long g = extgcd(b, a % b, x1, y1);
    x = y1;
    y = x1 - (a / b) * y1;
    return g;
}

// CRT for two congruences: x ≡ r1 (mod m1), x ≡ r2 (mod m2)
// Returns {solution, combined_modulus} or {-1, -1} if no solution
pair<long long, long long> crt2(long long r1, long long m1, long long r2, long long m2) {
    long long x, y;
    long long g = extgcd(m1, m2, x, y);

    if ((r2 - r1) % g != 0) return {-1, -1}; // No solution

    long long lcm = m1 / g * m2;
    long long diff = (r2 - r1) / g;
    long long shift = diff % (m2 / g) * (x % (m2 / g)) % (m2 / g);
    long long ans = (r1 + m1 * shift) % lcm;
    if (ans < 0) ans += lcm;
    return {ans, lcm};
}

// General CRT for k congruences
// remainders[] and moduli[] must have the same size
pair<long long, long long> crt(const vector<long long>& remainders, const vector<long long>& moduli) {
    long long cur_r = remainders[0], cur_m = moduli[0];
    for (int i = 1; i < (int)remainders.size(); i++) {
        auto [new_r, new_m] = crt2(cur_r, cur_m, remainders[i], moduli[i]);
        if (new_m == -1) return {-1, -1};
        cur_r = new_r;
        cur_m = new_m;
    }
    return {cur_r, cur_m};
}
```

---

## 4. Finite Fields — A Conceptual Note

### 4.1 What Is a Finite Field?

A **finite field** $\mathbb{F}_p$ (also written $\text{GF}(p)$ or $\mathbb{Z}/p\mathbb{Z}$) is the set of integers $\{0, 1, 2, \ldots, p-1\}$ where $p$ is prime, equipped with addition and multiplication **modulo $p$**.

Key properties that make modular arithmetic "work" in CP:

| Property | Meaning | Why It Matters |
| :--- | :--- | :--- |
| **Closure** | $a + b \pmod p$ and $a \cdot b \pmod p$ stay in $\{0, \ldots, p-1\}$ | Results never exceed the modulus |
| **Additive Inverse** | Every $a$ has $-a \equiv p - a$ | Subtraction works: $(a - b + p) \bmod p$ |
| **Multiplicative Inverse** | Every $a \ne 0$ has $a^{-1} \equiv a^{p-2}$ (Fermat) | Division works: $a / b \equiv a \cdot b^{p-2}$ |
| **Associativity & Commutativity** | Same rules as regular arithmetic | Rearranging terms is safe |
| **Distributive Law** | $a \cdot (b + c) = a \cdot b + a \cdot c$ | Expanding products works as expected |

### 4.2 Why $10^9 + 7$ and $998244353$?

| Modulus | Why It's Chosen |
| :--- | :--- |
| $10^9 + 7$ ($1000000007$) | Largest prime below $10^9$ that fits in 32-bit `int`. Product of two values fits in 64-bit `long long`. |
| $998244353$ | NTT-friendly prime ($p - 1 = 2^{23} \times 119$). Enables exact polynomial multiplication. |

### 4.3 Extension: $\text{GF}(p^k)$ — Finite Fields of Prime Power Order

Fields of order $p^k$ (e.g., $\text{GF}(2^8)$ used in AES encryption, CRC checksums) are built using **polynomial arithmetic** modulo an irreducible polynomial over $\mathbb{F}_p$. You won't encounter these often in standard CP, but they appear in:
- Cryptography (AES, Reed-Solomon error correction).
- Hashing schemes.
- Advanced combinatorics over $\text{GF}(2)$ (XOR-based linear algebra).

---

## 5. Newton-Raphson Method — Fast Division & Square Roots

### 5.1 The Idea

Newton-Raphson iteratively refines an approximation to the root of $f(x) = 0$ using:

$$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$

Each iteration approximately **doubles** the number of correct digits (quadratic convergence).

### 5.2 Computing $\frac{1}{D}$ (Reciprocal) Without Division

To compute $\frac{1}{D}$, solve $f(x) = \frac{1}{x} - D = 0$. Newton's iteration becomes:

$$x_{n+1} = x_n \cdot (2 - D \cdot x_n)$$

This uses **only multiplication and subtraction** — no division hardware needed! This is how CPUs and BigInt libraries implement fast division internally.

```cpp
// Newton-Raphson reciprocal approximation (floating-point)
double newtonReciprocal(double D, int iterations = 50) {
    double x = 1.0 / D; // Initial guess (or use a rough estimate)
    for (int i = 0; i < iterations; i++) {
        x = x * (2.0 - D * x); // Each iteration doubles precision
    }
    return x;
}
```

### 5.3 Integer Square Root via Newton's Method

Compute $\lfloor \sqrt{N} \rfloor$ for large $N$ without floating-point errors:

```cpp
long long isqrt(long long n) {
    if (n < 0) return -1;
    if (n < 2) return n;
    long long x = sqrt((double)n); // Initial guess from floating-point

    // Newton-Raphson refinement in integer arithmetic
    while (x * x > n) {
        x = (x + n / x) / 2;
    }
    // Edge case: check x+1
    while ((x + 1) * (x + 1) <= n) {
        x++;
    }
    return x;
}
```

> [!TIP] When to Use Newton's Method in CP
> - **Integer square root** for values near $10^{18}$ where `sqrt()` loses precision.
> - **BigInt division** in custom BigInteger libraries.
> - **Polynomial inversion** modulo $x^n$ using NTT (advanced generating functions).

---

## 6. Other Essential Topics for the Obsessed C++ Programmer

### 6.1 Euler's Totient Function $\phi(n)$

$\phi(n)$ counts integers in $[1, n]$ that are coprime to $n$.

$$\phi(n) = n \prod_{p \mid n} \left(1 - \frac{1}{p}\right)$$

```cpp
long long euler_totient(long long n) {
    long long result = n;
    for (long long p = 2; p * p <= n; p++) {
        if (n % p == 0) {
            while (n % p == 0) n /= p;
            result -= result / p;
        }
    }
    if (n > 1) result -= result / n;
    return result;
}
```

**Euler's Theorem**: $a^{\phi(m)} \equiv 1 \pmod m$ when $\gcd(a, m) = 1$. This generalises Fermat's Little Theorem to composite moduli.

### 6.2 Extended Euclidean Algorithm (Full)

Finds $x, y$ such that $ax + by = \gcd(a, b)$. Essential for modular inverse when modulus is **not prime**.

```cpp
// Returns gcd(a, b) and sets x, y such that a*x + b*y = gcd(a, b)
long long extgcd(long long a, long long b, long long& x, long long& y) {
    if (b == 0) { x = 1; y = 0; return a; }
    long long x1, y1;
    long long g = extgcd(b, a % b, x1, y1);
    x = y1;
    y = x1 - (a / b) * y1;
    return g;
}

// Modular inverse using ExtGCD (works for any coprime modulus, not just primes)
long long modInverseExt(long long a, long long mod) {
    long long x, y;
    long long g = extgcd(a, mod, x, y);
    if (g != 1) return -1; // No inverse exists
    return (x % mod + mod) % mod;
}
```

### 6.3 Matrix Exponentiation — Recurrences in $O(K^3 \log N)$

Compute the $N$-th term of a linear recurrence (e.g. Fibonacci) in $O(K^3 \log N)$ time where $K$ is the recurrence order.

```cpp
using Matrix = vector<vector<long long>>;
const long long MOD = 1e9 + 7;

Matrix multiply(const Matrix& A, const Matrix& B) {
    int n = A.size();
    Matrix C(n, vector<long long>(n, 0));
    for (int i = 0; i < n; i++)
        for (int k = 0; k < n; k++) if (A[i][k])
            for (int j = 0; j < n; j++)
                C[i][j] = (C[i][j] + A[i][k] * B[k][j]) % MOD;
    return C;
}

Matrix matpow(Matrix M, long long p) {
    int n = M.size();
    Matrix result(n, vector<long long>(n, 0));
    for (int i = 0; i < n; i++) result[i][i] = 1; // Identity matrix
    while (p > 0) {
        if (p & 1) result = multiply(result, M);
        M = multiply(M, M);
        p >>= 1;
    }
    return result;
}

// Example: Fibonacci F(n) in O(log n)
long long fibonacci(long long n) {
    if (n <= 1) return n;
    Matrix M = {{1, 1}, {1, 0}};
    Matrix result = matpow(M, n - 1);
    return result[0][0]; // F(n)
}
```

### 6.4 Möbius Function & Inclusion-Exclusion

The Möbius function $\mu(n)$:
- $\mu(1) = 1$
- $\mu(n) = 0$ if $n$ has a squared prime factor
- $\mu(n) = (-1)^k$ if $n$ is a product of $k$ distinct primes

Used in **Möbius inversion** to convert between summatory functions — the algebraic backbone of many "count coprime pairs" problems.

```cpp
vector<int> mobius;

void computeMobius(int n) {
    mobius.assign(n + 1, 0);
    mobius[1] = 1;
    vector<int> primes;
    vector<bool> is_composite(n + 1, false);

    for (int i = 2; i <= n; i++) {
        if (!is_composite[i]) {
            primes.push_back(i);
            mobius[i] = -1;
        }
        for (int p : primes) {
            if (1LL * i * p > n) break;
            is_composite[i * p] = true;
            if (i % p == 0) {
                mobius[i * p] = 0; // Squared factor
                break;
            }
            mobius[i * p] = -mobius[i];
        }
    }
}
```

---

## 7. Karatsuba Multiplication — Fast Multiplication in $O(N^{1.58})$

### 7.1 The Idea
Karatsuba multiplication is a divide-and-conquer algorithm that multiplies two large numbers (or polynomials) faster than the standard $O(N^2)$ algorithm. It reduces the number of recursive multiplications from 4 to 3.

Given two large polynomials (or numbers represented in some base) $X$ and $Y$ of degree $N$:
1. Split them in half:
   $X = X_1 \cdot B + X_0$
   $Y = Y_1 \cdot B + Y_0$
   (where $B$ is the split point, e.g., $x^{N/2}$).

2. A naive multiplication requires 4 products:
   $X \cdot Y = X_1 Y_1 \cdot B^2 + (X_1 Y_0 + X_0 Y_1) \cdot B + X_0 Y_0$

3. **Karatsuba's trick**: Compute only 3 products!
   Let $P_1 = X_1 \cdot Y_1$
   Let $P_2 = X_0 \cdot Y_0$
   Let $P_3 = (X_1 + X_0) \cdot (Y_1 + Y_0)$

   Then the middle term $(X_1 Y_0 + X_0 Y_1)$ is simply $P_3 - P_1 - P_2$.

By replacing one multiplication with additions/subtractions, the recurrence becomes $T(N) = 3T(N/2) + O(N)$, which resolves to $O(N^{\log_2 3}) \approx O(N^{1.58})$.

### 7.2 Implementation (Polynomials)
Here is how you'd implement Karatsuba for polynomial multiplication. For BigInt, the logic is identical, just with carrying.

```cpp
#include <vector>
#include <algorithm>
using namespace std;

// Adds two polynomials
vector<long long> add_poly(const vector<long long>& a, const vector<long long>& b) {
    vector<long long> res(max(a.size(), b.size()), 0);
    for (size_t i = 0; i < a.size(); ++i) res[i] += a[i];
    for (size_t i = 0; i < b.size(); ++i) res[i] += b[i];
    return res;
}

// Subtracts b from a
vector<long long> sub_poly(const vector<long long>& a, const vector<long long>& b) {
    vector<long long> res(a);
    res.resize(max(a.size(), b.size()), 0);
    for (size_t i = 0; i < b.size(); ++i) res[i] -= b[i];
    return res;
}

vector<long long> karatsuba(const vector<long long>& a, const vector<long long>& b) {
    int n = a.size();
    if (n <= 32) { // Base case: fallback to O(N^2) for small N
        vector<long long> res(a.size() + b.size() - 1, 0);
        for (size_t i = 0; i < a.size(); ++i)
            for (size_t j = 0; j < b.size(); ++j)
                res[i + j] += a[i] * b[j];
        return res;
    }

    int half = n / 2;
    vector<long long> a0(a.begin(), a.begin() + half);
    vector<long long> a1(a.begin() + half, a.end());
    vector<long long> b0(b.begin(), b.begin() + half);
    vector<long long> b1(b.begin() + half, b.end());

    vector<long long> p1 = karatsuba(a1, b1);
    vector<long long> p2 = karatsuba(a0, b0);
    vector<long long> p3 = karatsuba(add_poly(a0, a1), add_poly(b0, b1));

    // mid = p3 - p1 - p2
    vector<long long> mid = sub_poly(sub_poly(p3, p1), p2);

    vector<long long> result(a.size() + b.size() - 1, 0);
    for (size_t i = 0; i < p2.size(); ++i) result[i] += p2[i];
    for (size_t i = 0; i < mid.size(); ++i) result[i + half] += mid[i];
    for (size_t i = 0; i < p1.size(); ++i) result[i + 2 * half] += p1[i];

    return result;
}
```

> [!TIP] Karatsuba vs FFT
> Karatsuba is easier to code than FFT and requires no floating point math or complex NTT primes. It's often used as a fallback for medium-sized multiplications (e.g. $N \approx 10^3$ to $10^4$) where FFT overhead might be large, or as the base case inside FFT implementations!

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What time complexity does FFT/NTT achieve for polynomial multiplication? :: $O(N \log N)$, compared to $O(N^2)$ for naive multiplication.
<!--SR:!2026-09-28,3,250-->

Why is NTT preferred over FFT when exact integer results are needed? :: NTT operates in a finite field (modular arithmetic) with exact integers, while FFT uses floating-point complex numbers which introduce rounding errors.
<!--SR:!2026-09-28,3,250-->

Why is $998244353$ a popular modulus in competitive programming? :: It is an NTT-friendly prime: $998244353 - 1 = 2^{23} \times 119$, allowing NTT transforms of size up to $2^{23}$.

What does the Chinese Remainder Theorem guarantee? :: A unique solution modulo $M = m_1 \cdot m_2 \cdots m_k$ for a system of simultaneous congruences with pairwise coprime moduli.
<!--SR:!2026-09-26,1,230-->

What Newton-Raphson iteration computes $\frac{1}{D}$ using only multiplication and subtraction? :: $x_{n+1} = x_n \cdot (2 - D \cdot x_n)$.

What does Euler's Totient $\phi(n)$ count? :: The number of integers in $[1, n]$ that are coprime to $n$.
<!--SR:!2026-09-26,1,230-->

How can you compute $F(N)$ (Fibonacci) in $O(\log N)$ time? :: Using $2 \times 2$ matrix exponentiation: raise the matrix $\begin{pmatrix} 1 & 1 \\ 1 & 0 \end{pmatrix}$ to the $(N-1)$-th power.
<!--SR:!2026-09-26,1,230-->

What is the time complexity of Karatsuba multiplication, and how does it achieve it? :: It runs in $O(N^{\log_2 3}) \approx O(N^{1.58})$ time by dividing polynomials/numbers into halves and computing 3 recursive products instead of the naive 4.
