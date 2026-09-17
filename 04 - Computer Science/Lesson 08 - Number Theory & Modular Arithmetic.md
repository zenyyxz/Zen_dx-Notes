---
title: Lesson 08 - Number Theory & Modular Arithmetic
subject: Computer Science
unit: 08
competency: Apply core integer algorithms used in contest problems
tags:
  - Computer-Science
  - Competitive-Programming
  - NumberTheory
  - ModularArithmetic
  - Flashcards
---
---
# :LiBook: Lesson 08: Number Theory & Modular Arithmetic

> [!ABSTRACT] Scope
> Learn GCD, LCM, prime sieves, fast exponentiation, and modular arithmetic—the recurring tools behind divisibility and counting problems.

---
## 1. GCD and LCM

Euclid's algorithm uses
$$
\gcd(a,b)=\gcd(b,a\mod b).
$$

```cpp
long long g = gcd(a, b);                 // <numeric>
long long l = a / g * b;                 // divide first to reduce overflow risk
```

---
## 2. Prime Sieve

```cpp
int n = 1'000'000;
vector<bool> isPrime(n + 1, true);
isPrime[0] = isPrime[1] = false;
for (int p = 2; p * p <= n; p++) {
    if (!isPrime[p]) continue;
    for (int x = p * p; x <= n; x += p) isPrime[x] = false;
}
```

The sieve of Eratosthenes preprocesses primes up to $n$ in about $O(n \log \log n)$.

---
## 3. Fast Modular Exponentiation

```cpp
long long modPow(long long a, long long e, long long mod) {
    long long ans = 1 % mod;
    a %= mod;
    while (e > 0) {
        if (e & 1) ans = ans * a % mod;
        a = a * a % mod;
        e >>= 1;
    }
    return ans;
}
```

It computes $(a^e \mod m)$ in $O(\log e)$.

> [!INFO] Modular division
> You cannot ordinarily divide modulo $m$. If $m$ is prime and $(a \not\equiv 0 \pmod m)$, then the inverse is $(a^{m-2} \mod m)$ by Fermat's little theorem.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What recurrence powers Euclid's GCD algorithm? :: $(\gcd(a,b)=\gcd(b,a\mod b))$.

How fast is binary modular exponentiation? :: $O(\log e)$ for exponent $e$.

Why is ordinary division dangerous in modular arithmetic? :: A modular inverse may not exist; division is valid only when the divisor is invertible modulo the modulus.
