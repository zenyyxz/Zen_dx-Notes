---
title: Lesson 08 - Number Theory & Modular Arithmetic
subject: Computer Science
unit: 08
competency: Implement prime sieves, modular exponentiation, GCD, and modular inverses
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
> Master fundamental contest number theory: Sieve of Eratosthenes, Euclidean GCD, Fast Binary Exponentiation, and Modular Inverses.

---
## 1. Sieve of Eratosthenes (Prime Generation)

Find all prime numbers up to $N$ in $O(N \log \log N)$ time:

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
## 2. Fast Binary Exponentiation $O(\log B)$

Calculate $(A^B) \pmod M$ efficiently:

```cpp
long long binpow(long long a, long long b, long long mod) {
    a %= mod;
    long long res = 1;
    while (b > 0) {
        if (b & 1) res = (res * a) % mod;
        a = (a * a) % mod;
        b >>= 1;
    }
    return res;
}
```

---
## 3. Modular Inverse via Fermat's Little Theorem

For a prime modulus $M$, the modular inverse of $A$ modulo $M$ is:

$$A^{-1} \equiv A^{M-2} \pmod M$$

This allows division under modulo: $\frac{A}{B} \pmod M \equiv A \cdot B^{M-2} \pmod M$.

```cpp
long long modInverse(long long a, long long mod) {
    return binpow(a, mod - 2, mod);
}

long long modDivide(long long a, long long b, long long mod) {
    return (a % mod * modInverse(b, mod)) % mod;
}
```

---
## 4. GCD & LCM

```cpp
#include <numeric>

long long gcd(long long a, long long b) {
    return std::gcd(a, b); // C++17 built-in
}

long long lcm(long long a, long long b) {
    return std::lcm(a, b); // C++17 built-in (or: (a / std::gcd(a, b)) * b)
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the time complexity of the Sieve of Eratosthenes up to $N$? :: $O(N \log \log N)$ time.

How do you perform division $\frac{A}{B} \pmod M$ when $M$ is a prime number? :: Multiply $A$ by the modular inverse of $B$: $(A \cdot B^{M-2}) \pmod M$.

What is the time complexity of binary exponentiation $(A^B) \pmod M$? :: $O(\log B)$ time.
