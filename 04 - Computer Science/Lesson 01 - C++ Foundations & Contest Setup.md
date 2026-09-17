---
title: Lesson 01 - C++ Foundations & Contest Setup
subject: Computer Science
unit: 01
competency: Write, run, debug, and explain short C++ programs for programming contests
tags:
  - Computer-Science
  - Competitive-Programming
  - Cpp
  - Fundamentals
  - Flashcards
---
---
# :LiBook: Lesson 01: C++ Foundations & Contest Setup

> [!ABSTRACT] Scope
> Learn enough modern C++ to express contest solutions clearly: fast input/output, variables, loops, functions, containers, and a dependable starting template.

---
## 1. A Minimal Contest Program

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false); // Decouples C++ streams from C stdio for faster cin/cout.
    cin.tie(nullptr);             // Stops cin from flushing cout before every input operation.

    int n;
    cin >> n;
    cout << n * n << '\n';
}
```

- `#include <bits/stdc++.h>` is common in contests; it includes the standard library.
- `ios::sync_with_stdio(false); cin.tie(nullptr);` makes ordinary `cin`/`cout` fast enough for most contests.
- End output with `\n`, not `endl`; `endl` also flushes the stream.

---
## 2. Types You Will Use Often

| Type | Typical use |
| :--- | :--- |
| `int` | indices and values safely within about $2 \times 10^9$ |
| `long long` | sums, products, counts; use when constraints can exceed `int` |
| `double` | numerical geometry or approximation |
| `string` | text |
| `bool` | true/false conditions |

> [!WARNING] Overflow
> In `int a, b; long long x = a * b;`, the multiplication may overflow **before** being stored. Write `1LL * a * b`.

---
## 3. Control Flow and Functions

```cpp
long long gcd(long long a, long long b) {
    while (b != 0) {
        long long r = a % b;
        a = b;
        b = r;
    }
    return a;
}

int main() {
    int t;
    cin >> t;
    while (t--) {
        long long a, b;
        cin >> a >> b;
        if (a == b) cout << "equal\n";
        else cout << gcd(a, b) << '\n';
    }
}
```

Use a function when a piece of logic has a name. It reduces mistakes and lets you test the idea separately.

---
## 4. Useful Starter Template

```cpp
#include <bits/stdc++.h>
using namespace std;

using ll = long long;
using pii = pair<int, int>;

void solve() {
    // Read one test case and print its answer.
}

int main() {
    ios::sync_with_stdio(false); // Decouples C++ streams from C stdio for faster cin/cout.
    cin.tie(nullptr);             // Stops cin from flushing cout before every input operation.

    int t = 1;
    // cin >> t;  // uncomment when input starts with test-case count
    while (t--) solve();
}
```

Keep your template small. Every line should be familiar; copying a huge template you cannot debug is harmful.

---
## 5. Debugging Habits

- Read the exact input format before coding.
- Test the smallest valid input, a boundary case, and a weird-looking case.
- Print intermediate values locally when stuck, then remove them.
- Compile with warnings while learning: `g++ -std=c++17 -Wall -Wextra -Wshadow file.cpp`.
- If a result is wrong, first check indices, overflow, and whether you reset variables for every test case.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why use `long long` in contest programs? :: It stores much larger integers than `int`, preventing overflow in large sums and products.

What does `cin.tie(nullptr)` help with? :: It removes unnecessary automatic flushing of `cout` before input operations, improving I/O speed.

Why is `1LL * a * b` safer than `a * b` when `a` and `b` are `int`? :: It promotes the multiplication to `long long` before it happens.
