---
title: Lesson 13 - Strings
subject: Computer Science
unit: 13
competency: Process strings using polynomial hashing, KMP prefix functions, and Tries
tags:
  - Computer-Science
  - Competitive-Programming
  - Strings
  - StringHashing
  - KMP
  - Flashcards
---
---
# :LiBook: Lesson 13: Strings

> [!ABSTRACT] Scope
> Master string pattern matching techniques: Polynomial Rolling Hashing, KMP Prefix Function, and Trie data structures.

---
## 1. Polynomial Rolling Hashing

Polynomial Hashing maps a string $S$ to an integer hash value in $O(N)$ time, enabling $O(1)$ substring equality comparisons:

$$\text{hash}(S) = \left( \sum_{i=0}^{N-1} S[i] \cdot p^i \right) \pmod M$$

Typically, $p = 31$ (for lowercase) or $p = 53$ (for mixed case), and $M = 10^9+7$ or $10^9+9$.

```cpp
#include <iostream>
#include <string>
#include <vector>
using namespace std;

struct StringHash {
    int n;
    long long p = 31;
    long long mod = 1e9 + 7;
    vector<long long> pref, p_pow;

    StringHash(const string& s) : n(s.length()), pref(n + 1, 0), p_pow(n + 1, 1) {
        for (int i = 0; i < n; i++) {
            p_pow[i + 1] = (p_pow[i] * p) % mod;
            pref[i + 1] = (pref[i] + (s[i] - 'a' + 1) * p_pow[i]) % mod;
        }
    }

    // Get hash of substring s[l...r] (0-indexed, inclusive)
    long long getHash(int l, int r) {
        long long res = (pref[r + 1] - pref[l] + mod) % mod;
        return res; // Note: Multiply by p_pow[N - l] if matching relative powers
    }
};
```

---
## 2. KMP Prefix Function ($\pi$-array)

The **Prefix Function** $\pi[i]$ is the length of the longest proper prefix of $S[0 \dots i]$ that is also a suffix of $S[0 \dots i]$. Computed in $O(N)$ time.

```cpp
vector<int> prefixFunction(const string& s) {
    int n = s.length();
    vector<int> pi(n, 0);
    for (int i = 1; i < n; i++) {
        int j = pi[i - 1];
        while (j > 0 && s[i] != s[j]) {
            j = pi[j - 1];
        }
        if (s[i] == s[j]) j++;
        pi[i] = j;
    }
    return pi;
}
```

---
## 3. Trie (Prefix Tree)

```cpp
struct TrieNode {
    TrieNode* children[26] = {nullptr};
    bool is_end = false;
};

void insertTrie(TrieNode* root, const string& word) {
    TrieNode* curr = root;
    for (char c : word) {
        int idx = c - 'a';
        if (!curr->children[idx]) {
            curr->children[idx] = new TrieNode();
        }
        curr = curr->children[idx];
    }
    curr->is_end = true;
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What does KMP prefix function $\pi[i]$ store? :: The length of the longest proper prefix of $S[0 \dots i]$ that is also a suffix of $S[0 \dots i]$.

What prime base $p$ is commonly used for lowercase ASCII polynomial string hashing? :: $p = 31$ (or $p = 131$).

What is the query time complexity for checking if a word of length $L$ exists in a Trie? :: $O(L)$ time.
