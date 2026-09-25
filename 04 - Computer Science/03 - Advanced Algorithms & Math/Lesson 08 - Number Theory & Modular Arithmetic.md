---
title: Lesson 08 - Number Theory & Modular Arithmetic
subject: Computer Science
unit: 08
competency: Apply modular arithmetic rules, implement prime sieves, modular exponentiation, combinatorics, and modular inverses
tags:
  - Computer-Science
  - Competitive-Programming
  - NumberTheory
  - Math
  - ModularArithmetic
  - Flashcards
---
---
# :LiBook: Lesson 08: Number Theory & Modular Arithmetic

> [!ABSTRACT] Scope
> Master modular arithmetic from the ground up: rules of mod operations, common traps, prime sieves, binary exponentiation, modular inverses, and modular combinatorics ($n \choose r$ mod $p$).

> [!TIP] Advanced Topics
> For FFT, NTT, CRT, finite fields, and matrix exponentiation, see [[03 - Advanced Algorithms & Math/Lesson 17 - Advanced Math - FFT, NTT, CRT & Finite Fields|Lesson 17 — Advanced Math]].

---

## 1. Modular Arithmetic — Core Rules & Traps

### 1.1 The Basic Identities

All contest modular arithmetic is built on these four rules:

$$
(a + b) \bmod m = \big((a \bmod m) + (b \bmod m)\big) \bmod m
$$

$$
(a - b) \bmod m = \big((a \bmod m) - (b \bmod m) + m\big) \bmod m
$$

$$
(a \times b) \bmod m = \big((a \bmod m) \times (b \bmod m)\big) \bmod m
$$

$$
\frac{a}{b} \bmod m = \big(a \times b^{-1}\big) \bmod m \quad \text{(requires modular inverse, see §4)}
$$

> [!WARNING] Subtraction Can Go Negative!
> In C++, `-3 % 7` evaluates to `-3`, not `4`. **Always add `m` before taking mod** when subtraction is involved:
> ```cpp
> long long safe_sub = ((a % mod) - (b % mod) + mod) % mod;
> ```

### 1.2 The Modular Arithmetic Cheat Sheet

```cpp
const long long MOD = 1e9 + 7;

long long mod_add(long long a, long long b) {
    return ((a % MOD) + (b % MOD)) % MOD;
}

long long mod_sub(long long a, long long b) {
    return ((a % MOD) - (b % MOD) + MOD) % MOD; // +MOD prevents negatives!
}

long long mod_mul(long long a, long long b) {
    return ((a % MOD) * (b % MOD)) % MOD;
}
```

### 1.3 Common Beginner Traps

| Trap | Example | Fix |
| :--- | :--- | :--- |
| Negative mod result | `(-3) % 7 == -3` in C++ | `((a % m) + m) % m` |
| Overflow in multiplication | `a * b` overflows `long long` when both are near $10^{18}$ | Use `__int128` or split: `(a % m) * (b % m) % m` |
| Forgetting to mod intermediate results | `sum += a[i]` accumulates without mod | `sum = (sum + a[i]) % mod` at every step |
| Division is NOT `(a / b) % m` | `(a / b) % m` gives wrong answer | `(a * modInverse(b, m)) % m` |

---

## 2. Sieve of Eratosthenes (Prime Generation)

Find all primes up to $N$ in $O(N \log \log N)$ time:

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<bool> is_prime;
vector<int> primes;

void sieve(int n) {
    is_prime.assign(n + 1, true);
    is_prime[0] = is_prime[1] = false;

    for (int p = 2; p * p <= n; p++) {
        if (is_prime[p]) {
            for (int i = p * p; i <= n; i += p) {
                is_prime[i] = false;
            }
        }
    }

    for (int p = 2; p <= n; p++) {
        if (is_prime[p]) primes.push_back(p);
    }
}
```

---

## 3. Fast Binary Exponentiation $O(\log B)$

Calculate $(A^B) \pmod M$ efficiently using repeated squaring:

```cpp
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
```

---

## 4. Modular Inverse

### 4.1 Via Fermat's Little Theorem (Prime Modulus Only)

For a **prime** modulus $M$:

$$A^{-1} \equiv A^{M-2} \pmod M$$

```cpp
long long modInverse(long long a, long long mod) {
    return binpow(a, mod - 2, mod);
}

// Division under mod: (a / b) % mod
long long modDivide(long long a, long long b, long long mod) {
    return a % mod * modInverse(b, mod) % mod;
}
```

### 4.2 Via Extended GCD (Any Coprime Modulus)

Works when modulus is **not** necessarily prime, as long as $\gcd(a, m) = 1$:

```cpp
long long extgcd(long long a, long long b, long long& x, long long& y) {
    if (b == 0) { x = 1; y = 0; return a; }
    long long x1, y1;
    long long g = extgcd(b, a % b, x1, y1);
    x = y1;
    y = x1 - (a / b) * y1;
    return g;
}

long long modInverseExt(long long a, long long mod) {
    long long x, y;
    long long g = extgcd(a, mod, x, y);
    if (g != 1) return -1; // No inverse exists
    return (x % mod + mod) % mod;
}
```

---

## 5. GCD & LCM

```cpp
#include <numeric>

// C++17 built-in
long long g = __gcd(a, b);             // or std::gcd(a, b)
long long l = a / __gcd(a, b) * b;    // Divide first to avoid overflow!
```

> [!WARNING] LCM Overflow Trap
> Never write `a * b / gcd(a, b)` — the product `a * b` can overflow `long long`. Always divide first: `a / gcd(a, b) * b`.

---

## 6. Modular Combinatorics — $\binom{n}{r} \bmod p$

Many CP problems ask for counts modulo a prime. You need to compute $\binom{n}{r} = \frac{n!}{r!(n-r)!}$ under modulo.

### 6.1 Precompute Factorials & Inverse Factorials

```cpp
const int MAXN = 2e6 + 5;
const long long MOD = 1e9 + 7;

long long fact[MAXN], inv_fact[MAXN];

void precompute() {
    fact[0] = 1;
    for (int i = 1; i < MAXN; i++) {
        fact[i] = fact[i - 1] * i % MOD;
    }
    inv_fact[MAXN - 1] = binpow(fact[MAXN - 1], MOD - 2, MOD);
    for (int i = MAXN - 2; i >= 0; i--) {
        inv_fact[i] = inv_fact[i + 1] * (i + 1) % MOD;
    }
}

// nCr mod p in O(1) after O(N) precomputation
long long nCr(int n, int r) {
    if (r < 0 || r > n) return 0;
    return fact[n] % MOD * inv_fact[r] % MOD * inv_fact[n - r] % MOD;
}
```

> [!TIP] Inverse Factorial Trick
> Instead of computing $N$ separate modular inverses ($O(N \log M)$ total), compute **only** `inv_fact[MAXN-1]` via `binpow`, then fill backwards: `inv_fact[i] = inv_fact[i+1] * (i+1) % MOD`. This gives all inverse factorials in $O(N)$ time.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the time complexity of the Sieve of Eratosthenes up to $N$? :: $O(N \log \log N)$ time.
<!--SR:!2026-09-26,1,230-->

How do you perform division $\frac{A}{B} \pmod M$ when $M$ is prime? :: Multiply $A$ by the modular inverse of $B$: $(A \cdot B^{M-2}) \pmod M$.
<!--SR:!2026-09-26,1,230-->

What is the time complexity of binary exponentiation $(A^B) \pmod M$? :: $O(\log B)$ time.

Why must you write `((a % m) - (b % m) + m) % m` instead of `(a - b) % m` in C++? :: Because C++ modulo can return negative values for negative operands, so adding `m` before the final mod ensures a non-negative result.

Why write `a / gcd(a, b) * b` instead of `a * b / gcd(a, b)` for LCM? :: Dividing first prevents intermediate overflow of the product `a * b`.
<!--SR:!2026-09-26,1,230-->

How do you compute $\binom{n}{r} \bmod p$ in $O(1)$ per query? :: Precompute `fact[]` and `inv_fact[]` arrays in $O(N)$ time, then $\binom{n}{r} = \text{fact}[n] \cdot \text{inv\_fact}[r] \cdot \text{inv\_fact}[n-r] \bmod p$.
<!--SR:!2026-09-26,1,230-->

When should you use Extended GCD instead of Fermat's Little Theorem for modular inverse? :: When the modulus $m$ is **not prime** — Fermat's theorem only works for prime moduli, while ExtGCD works for any modulus where $\gcd(a, m) = 1$.
<!--SR:!2026-09-26,1,230-->
