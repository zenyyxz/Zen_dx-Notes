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

> [!TIP] Deep Dive Reference
> For a complete C++ language guide covering pointers, memory ownership (`unique_ptr`), casting, `const` functions, and STL containers, consult [[00 - C++ Reference/Complete C++ Reference for Competitive Programming|Complete C++ Reference for Competitive Programming]].

---
## 1. A Minimal Contest Program

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false); // Decouples C++ streams from C stdio for faster cin/cout.
    cin.tie(nullptr);             // Stops cin from flushing cout before every input operation.

    int n;
    if (cin >> n) {
        cout << 1LL * n * n << '\n';
    }
}
```

- `#include <bits/stdc++.h>` includes the entire standard library at once (supported on GCC).
- `ios::sync_with_stdio(false); cin.tie(nullptr);` makes `cin`/`cout` as fast as `scanf`/`printf`.
- End output with `\n`, not `endl`; `endl` forces an unnecessary stream flush after every line.

---
## 2. Fundamental Types & Constraints

| Type | Size | Range / Bounds | Typical CP Use Case |
| :--- | :--- | :--- | :--- |
| `int` | 32-bit | $-2 \times 10^9$ to $+2 \times 10^9$ | Indices, counts under $10^9$ |
| `long long` | 64-bit | $-9 \times 10^{18}$ to $+9 \times 10^{18}$ | Accumulative sums, products |
| `double` | 64-bit | ~15-17 decimal digits precision | Floating-point geometry |
| `string` | Dynamic | Memory bound | Text processing, string manipulation |
| `bool` | 8-bit | `true` (1) or `false` (0) | Condition flags, visitation arrays |

> [!WARNING] Implicit Integer Overflow
> In `int a = 1e6, b = 1e6; long long x = a * b;`, `a * b` is evaluated as an `int` **before** assignment, overflowing into a negative number. Write `1LL * a * b` to promote the operation to `long long`.

---
## 3. Control Flow & Modular Functions

```cpp
#include <bits/stdc++.h>
using namespace std;

long long gcd(long long a, long long b) {
    while (b != 0) {
        long long r = a % b;
        a = b;
        b = r;
    }
    return a;
}

void solve() {
    long long a, b;
    cin >> a >> b;
    if (a == b) cout << "equal\n";
    else cout << "GCD: " << gcd(a, b) << '\n';
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t = 1;
    cin >> t;
    while (t--) {
        solve();
    }
}
```

Break logic into small, modular functions (e.g., `solve()`). It reduces variable scope conflicts across multiple test cases.

---
## 4. Standard Contest Starter Template

```cpp
#include <bits/stdc++.h>
using namespace std;

// Type Aliases
using ll = long long;
using pii = pair<int, int>;
using vi = vector<int>;
using vll = vector<ll>;

void solve() {
    // Read one testcase input and output answer
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t = 1;
    // cin >> t; // Uncomment if input specifies number of testcases
    while (t--) {
        solve();
    }
    return 0;
}
```

Keep your starter template small and clean. Avoid huge, unmaintainable macro headers.

---
## 5. Debugging Checklist & Compilation Flags

- **Input Reading**: Ensure you read all input values in exact order.
- **Variable Reset**: Re-initialize global arrays/vectors inside `solve()` for every test case.
- **Array Bounds**: Check for 0-based vs 1-based indexing errors.
- **Local Compilation**: Compile locally with warnings enabled:
  ```bash
  g++ -std=c++17 -O2 -Wall -Wextra -Wshadow solution.cpp -o solution
  ```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why use `long long` in contest programs? :: It stores integers up to $\approx 9 \times 10^{18}$, preventing overflow in large sums and products.

What does `cin.tie(nullptr)` help with? :: It removes automatic flushing of `cout` before `cin` operations, improving I/O speed.

Why is `1LL * a * b` safer than `a * b` when `a` and `b` are `int`? :: It promotes the multiplication to `long long` before the operation takes place.
