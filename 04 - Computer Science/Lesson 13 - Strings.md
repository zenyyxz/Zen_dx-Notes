---
title: Lesson 13 - Strings
subject: Computer Science
unit: 13
competency: Apply efficient string preprocessing and understand common string structures
tags:
  - Computer-Science
  - Competitive-Programming
  - Strings
  - KMP
  - Trie
  - Flashcards
---
---
# :LiBook: Lesson 13: Strings

> [!ABSTRACT] Scope
> String problems often require detecting repeated patterns faster than comparing every pair of substrings. Learn the language features first, then reusable preprocessors.

---
## 1. Basic C++ String Work

```cpp
string s;
cin >> s;
reverse(s.begin(), s.end());

string part = s.substr(l, len); // creates a copy
int pos = s.find("abc");        // string::npos if absent
```

For many queries, repeatedly creating substrings can be too slow. Prefer indices or preprocessing.

---
## 2. Prefix Function (KMP)

`pi[i]` is the length of the longest proper prefix of `s[0..i]` that is also a suffix of it.

```cpp
vector<int> prefixFunction(const string& s) {
    int n = (int)s.size();
    vector<int> pi(n);
    for (int i = 1; i < n; i++) {
        int j = pi[i - 1];
        while (j > 0 && s[i] != s[j]) j = pi[j - 1];
        if (s[i] == s[j]) j++;
        pi[i] = j;
    }
    return pi;
}
```

It runs in $O(n)$. It is used for pattern matching and detecting borders/repetition.

---
## 3. Trie Idea

A trie stores strings by shared prefixes. Each path from the root spells a prefix; mark nodes that finish a word. It is useful for dictionary/prefix-query problems, though memory use can be high.

---
## 4. Hashing Caution

Rolling hashes can compare substrings quickly after preprocessing, but collisions are possible. In contests, use robust parameters or two hashes when collision risk matters; never treat a probabilistic hash as a mathematical proof when exact correctness is required.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What does the prefix function value `pi[i]` represent? :: The length of the longest proper prefix of `s[0..i]` that is also a suffix of it.

What time complexity does the KMP prefix-function computation have? :: $O(n)$.

What does a trie share between stored strings? :: Their common prefixes.
