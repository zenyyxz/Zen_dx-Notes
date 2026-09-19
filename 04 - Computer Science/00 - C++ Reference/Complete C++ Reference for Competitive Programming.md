---
title: Complete C++ Reference for Competitive Programming
subject: Computer Science
tags:
  - Computer-Science
  - Competitive-Programming
  - Cpp
  - Reference
  - STL
  - CheatSheet
---

# Complete C++ Reference for Competitive Programming

> [!ABSTRACT] Overview & Purpose
> This document serves as a complete, single-source reference for C++ tailored specifically for **Competitive Programming (CP)**. Whether you are refreshing basic C++ syntax or building towards Codeforces, AtCoder, and CSES contests, this guide bridges core programming fundamentals with contest-level performance and STL mastery.

---

## 1. C++ Language Core

### 1.1 Data Types & Memory Limits

In competitive programming, selecting the right integer type is critical to avoid **Integer Overflow** (which results in `Wrong Answer`).

| Type | Size (typical) | Range / Limits | Typical CP Use Case |
| :--- | :--- | :--- | :--- |
| `bool` | 1 byte | `true` (1) or `false` (0) | Flags, visited states |
| `char` | 1 byte | ASCII characters ('a'-'z', '0'-'9') | Character processing |
| `int` | 4 bytes | $\approx -2 \times 10^9$ to $+2 \times 10^9$ ($\pm 2147483647$) | Indices, counts under $10^9$ |
| `long long` | 8 bytes | $\approx -9 \times 10^{18}$ to $+9 \times 10^{18}$ | Accumulative sums, products |
| `double` | 8 bytes | 53-bit precision (~15-17 decimal digits) | Floating-point geometry |
| `long double` | 12-16 bytes | High precision floating point | Strict geometry problems |

> [!WARNING] The Number One Beginner Trap: Implicit Integer Overflow
> ```cpp
> int a = 1000000;
> int b = 1000000;
> long long ans = a * b; // ❌ BUG: a * b is evaluated as 'int' BEFORE assignment, causing overflow!
> long long safe_ans = 1LL * a * b; // ✅ CORRECT: '1LL' forces the multiplication to be done in 'long long'.
> ```

---

### 1.2 Control Flow & Range Loops

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> nums = {10, 20, 30, 40};

    // Standard index-based loop (use when index is needed)
    for (int i = 0; i < (int)nums.size(); ++i) {
        cout << "Index " << i << ": " << nums[i] << '\n';
    }

    // Modern C++ Range-based loop (read-only)
    for (int x : nums) {
        cout << x << ' ';
    }
    cout << '\n';

    // Range-based loop by reference (modifies original elements without copying)
    for (int &x : nums) {
        x *= 2;
    }
}
```

---

### 1.3 Functions & Pass-by-Value vs Pass-by-Reference

In CP, passing large objects (like `std::vector` or `std::string`) by value creates a **copy** of the entire data structure, which causes **Time Limit Exceeded (TLE)**.

```cpp
// ❌ SLOW: Copies entire vector of size N (O(N) time and memory overhead per call!)
void processSlow(vector<int> v) {
    // ...
}

// ✅ FAST: Passes reference to original memory (O(1) overhead)
void processFast(const vector<int>& v) {
    // 'const' prevents unintended modifications while keeping it O(1)
}

// ✅ MUTABLE REFERENCE: Allows function to modify original vector
void updateVector(vector<int>& v) {
    v.push_back(42);
}
```

---

### 1.4 Memory Model, Pointers & References

Understanding memory layout helps demystify data structures like Linked Lists, Trees, and Graphs.

```cpp
int x = 10;
int* ptr = &x;  // 'ptr' holds the memory address of 'x'
int& ref = x;   // 'ref' is an alias for 'x' (same memory location)

cout << x << '\n';     // 10
cout << &x << '\n';    // Memory address (e.g., 0x7ffd...)
cout << ptr << '\n';   // Same memory address
cout << *ptr << '\n';  // Dereference operator: gets value at address (10)

*ptr = 25;             // Changes x to 25
cout << x << '\n';     // 25
```

---

### 1.5 Structs & Custom Data Types for Contests

```cpp
struct Point {
    int x, y;
    
    // Custom Constructor
    Point(int x = 0, int y = 0) : x(x), y(y) {}

    // Custom Comparison Operator (for sorting or std::set)
    bool operator<(const Point& other) const {
        if (x != other.x) return x < other.x;
        return y < other.y;
    }
};

// Usage
Point p1(3, 4);
Point p2(1, 5);
if (p2 < p1) {
    cout << "p2 comes before p1\n";
}
```

---

### 1.6 C++ Type Casting Operators

In C, type casting is written as `(type)value` (e.g. `(double)a / b`). In modern C++, explicit cast operators are preferred because they are type-checked at compile time, explicit in intent, and safer.

| Cast Operator | Purpose | Code Example |
| :--- | :--- | :--- |
| `static_cast<T>(expr)` | Safe, compile-time checked conversion between compatible types (e.g., `int` to `double`, `int` to `long long`). | `double avg = static_cast<double>(sum) / n;` |
| `reinterpret_cast<T>(expr)` | Low-level bit reinterpretation of pointer types or integral memory addresses. | `uintptr_t addr = reinterpret_cast<uintptr_t>(ptr);` |
| `const_cast<T>(expr)` | Adds or strips away `const` or `volatile` qualifiers from a variable. | `int* mutable_p = const_cast<int*>(const_p);` |
| `dynamic_cast<T>(expr)` | Safe runtime downcasting in polymorphic class hierarchies (requires virtual functions). | `Derived* d = dynamic_cast<Derived*>(base_ptr);` |

#### Code Examples

```cpp
// 1. static_cast (Most common in CP and general C++)
int a = 7, b = 2;
double ratio = static_cast<double>(a) / b; // 3.5 instead of integer division 3

long long big_val = 1000000000000LL;
int truncated = static_cast<int>(big_val % 1000000007); // Explicit narrowing conversion

// 2. reinterpret_cast (Low-level memory/pointer manipulation)
int val = 0x12345678;
char* byte_ptr = reinterpret_cast<char*>(&val); // Inspect raw memory bytes

// 3. const_cast (Removing constness)
const char* msg = "hello";
char* mutable_msg = const_cast<char*>(msg);
```

> [!TIP] Contest Tip
> In Competitive Programming, use `static_cast<double>(a) / b` or `1.0 * a / b` to force floating-point division and avoid accidental integer truncation!

---

### 1.7 Const Correctness (`const` parameters, return values & `func() const {}`)

The `const` keyword specifies immutability. Understanding where `const` is placed is essential for clean C++ design.

#### 1. Const Function Parameters & Return Types
```cpp
// Parameter: 's' cannot be modified inside the function (and avoids copying!)
void printString(const string& s) {
    // s += "!"; // ❌ Compiler error! 's' is read-only.
    cout << s << '\n';
}

// Return Value: Returns a read-only reference to internal vector
const vector<int>& getScores() const {
    return scores;
}
```

#### 2. Member Function Constness (`void func() const {}`)
When a member function is marked `const` **after** the parameter list (e.g. `void show() const {}`), it promises that calling this method **will not alter any member variables of the struct/class** (`this` pointer is treated as `const ClassName*`).

```cpp
struct Student {
    string name;
    int score;

    // Const member function: Promises not to modify 'name' or 'score'
    void displayInfo() const {
        // score += 5; // ❌ Compiler error! Cannot mutate member variables inside const function.
        cout << name << ": " << score << '\n';
    }

    // Non-const member function: Can modify state
    void addBonus(int points) {
        score += points; // ✅ Allowed
    }
};

void processStudent(const Student& s) {
    s.displayInfo(); // ✅ OK: displayInfo() is declared 'const'
    // s.addBonus(10); // ❌ Compiler error! Cannot call non-const method on a const object/reference!
}
```

> [!IMPORTANT] Why operator< Needs `const` in Structs
> When defining `bool operator<(const Point& other) const {}` for `std::set` or `std::sort`, the trailing `const` is **required** because `std::set` holds its elements as `const` objects so you cannot accidentally corrupt the BST ordering!

---

### 1.8 Default & Deleted Functions (`= default`, `= delete`)

Introduced in modern C++ (C++11), these keywords explicitly control compiler-generated special member functions (constructors, destructors, copy/move operators).

#### 1. `= default`: Explicit Compiler-Generated Default Constructor
When you define a custom constructor (e.g., `Point(int x, int y)`), the compiler **stops** automatically generating the default zero-argument constructor (`Point()`). Using `= default` tells the compiler to generate its standard default constructor.

```cpp
struct Vector3D {
    double x = 0.0;
    double y = 0.0;
    double z = 0.0;

    // Compiler generates standard default constructor: Vector3D()
    Vector3D() = default;

    // Custom constructor
    Vector3D(double x, double y, double z) : x(x), y(y), z(z) {}
};

// Usage
Vector3D v1;           // Uses = default constructor (x=0.0, y=0.0, z=0.0)
Vector3D v2(1, 2, 3);  // Uses custom constructor
```

#### 2. `= delete`: Disabling Functions / Constructors
`= delete` explicitly forbids a function or constructor from being called.

```cpp
struct DisjointSetUnion {
    vector<int> parent;
    
    DisjointSetUnion(int n) : parent(n) {}

    // Prevent accidental copying of large DSU data structure!
    DisjointSetUnion(const DisjointSetUnion&) = delete;            // Copy constructor deleted
    DisjointSetUnion& operator=(const DisjointSetUnion&) = delete; // Copy assignment deleted
};

DisjointSetUnion dsu1(100);
// DisjointSetUnion dsu2 = dsu1; // ❌ Compiler error: copy constructor is deleted!
```

---

## 2. Modern C++ Contest Template & Fast I/O

```cpp
#include <bits/stdc++.h> // Includes all standard C++ headers at once
using namespace std;

// Common Type Aliases
using ll = long long;
using pii = pair<int, int>;
using vi = vector<int>;
using vll = vector<long long>;

// Fast I/O Routine
void fast_io() {
    ios::sync_with_stdio(false); // Disables synchronization between C and C++ standard streams
    cin.tie(nullptr);            // Unties cin from cout (stops auto-flushing cout before cin)
}

void solve() {
    // Write your solution per test case here
    int n;
    if (!(cin >> n)) return;
    cout << n * 2 << '\n'; // Prefer '\n' over std::endl (endl forces a stream flush)
}

int main() {
    fast_io();
    
    int t = 1;
    // cin >> t; // Uncomment if problem contains multiple test cases
    while (t--) {
        solve();
    }
    return 0;
}
```

---

## 3. C++ Standard Template Library (STL) Master Guide

### 3.1 Dynamic Arrays (`std::vector`)

`std::vector` is the workhorse container of competitive programming.

```cpp
#include <vector>
using namespace std;

// 1. Initialization
vector<int> a;                   // Empty vector
vector<int> b(5, 0);             // Vector of size 5 filled with 0s: [0, 0, 0, 0, 0]
vector<vector<int>> grid(n, vector<int>(m, -1)); // 2D vector N x M initialized to -1

// 2. Core Operations
a.push_back(10);     // Append 10 to back: O(1) amortized
a.pop_back();        // Remove last element: O(1)
int sz = a.size();   // Number of elements: O(1)
a.clear();           // Removes all elements: O(N)
bool emp = a.empty(); // Check if empty: O(1)

// 3. Access
int first = a.front(); // First element
int last = a.back();   // Last element
int val = a[0];        // Index access: O(1)
```

---

### 3.2 Pairs & Tuples (`std::pair`, `std::tuple`)

```cpp
#include <utility>
#include <tuple>
using namespace std;

// Pair: Holds two values of arbitrary types
pair<int, string> p = {1, "codeforces"};
cout << p.first << " " << p.second << '\n';

// Pairs sort automatically by first element, then by second element!
vector<pair<int, int>> pts = {{3, 5}, {1, 2}, {3, 1}};
sort(pts.begin(), pts.end()); // Result: {{1, 2}, {3, 1}, {3, 5}}

// Tuple: Holds 3 or more elements
tuple<int, int, int> t = {10, 20, 30};
auto [x, y, z] = t; // C++17 Structured Binding
```

---

### 3.3 Strings (`std::string`)

```cpp
#include <string>
using namespace std;

string s = "hello";
s += " world";             // Concatenation: O(N)
char c = s[0];              // Access character: O(1)
string sub = s.substr(0, 5); // Substring from index 0 of length 5: "hello"

// String conversions
int num = 123;
string num_str = to_string(num); // "123"
int val = stoi("456");           // 456
long long ll_val = stoll("1000000000000");

// Read entire line including spaces
string full_line;
getline(cin, full_line);
```

---

### 3.4 Container Adaptors (`stack`, `queue`, `priority_queue`)

#### Stack (LIFO - Last In First Out)
```cpp
#include <stack>
stack<int> st;
st.push(10);      // O(1)
st.push(20);
int top_val = st.top(); // 20
st.pop();         // Removes 20: O(1)
```

#### Queue (FIFO - First In First Out)
```cpp
#include <queue>
queue<int> q;
q.push(10);       // O(1)
q.push(20);
int front_val = q.front(); // 10
q.pop();          // Removes 10: O(1)
```

#### Priority Queue / Heap
```cpp
#include <queue>

// Max-Heap (Default: largest element on top)
priority_queue<int> max_pq;
max_pq.push(30);
max_pq.push(10);
max_pq.push(50);
cout << max_pq.top() << '\n'; // Output: 50
max_pq.pop();                 // Removes 50: O(log N)

// Min-Heap (Smallest element on top)
priority_queue<int, vector<int>, greater<int>> min_pq;
min_pq.push(30);
min_pq.push(10);
cout << min_pq.top() << '\n'; // Output: 10
```

---

### 3.5 Sets & Maps

| Container | Underlying Data Structure | Ordering | Time Complexity |
| :--- | :--- | :--- | :--- |
| `std::set<T>` | Red-Black Tree (Self-balancing BST) | Strictly Sorted | $O(\log N)$ insert/find/erase |
| `std::multiset<T>` | Red-Black Tree | Sorted (Allows Duplicates) | $O(\log N)$ insert/find/erase |
| `std::map<K, V>` | Red-Black Tree | Sorted by Key | $O(\log N)$ insert/find/erase |
| `std::unordered_set<T>` | Hash Table | Unordered | $O(1)$ average, $O(N)$ worst case |
| `std::unordered_map<K,V>`| Hash Table | Unordered | $O(1)$ average, $O(N)$ worst case |

```cpp
#include <set>
#include <map>
#include <unordered_map>
using namespace std;

// --- std::set ---
set<int> s;
s.insert(5);
s.insert(2);
s.insert(5); // Duplicate ignored

if (s.count(2)) { // Returns 1 if present, 0 otherwise: O(log N)
    cout << "2 exists in set\n";
}

// Iterating over set (Elements printed in sorted order: 2 5)
for (int x : s) cout << x << ' ';
cout << '\n';

// --- std::map ---
map<string, int> freq;
freq["apple"] = 3;
freq["banana"] = 5;

for (auto [key, value] : freq) { // C++17 structured binding
    cout << key << ": " << value << '\n';
}

// --- Anti-Hash Collisions Hack for unordered_map ---
// Note: In Codeforces, standard unordered_map can be hacked to O(N) by adversarial test cases.
// Use std::map by default unless performance strictly requires custom-hashed unordered_map.
```

---

## 4. Essential STL Algorithms for CP

```cpp
#include <algorithm>
#include <vector>
#include <numeric> // for std::accumulate
using namespace std;

vector<int> v = {4, 1, 7, 3, 9, 2};

// 1. Sorting
sort(v.begin(), v.end()); // Ascending: [1, 2, 3, 4, 7, 9] (O(N log N))
sort(v.rbegin(), v.rend()); // Descending: [9, 7, 4, 3, 2, 1]

// Custom Comparator (Lambda)
sort(v.begin(), v.end(), [](int a, int b) {
    return a > b; // Descending
});

// 2. Binary Search (Requires sorted array!)
sort(v.begin(), v.end()); // [1, 2, 3, 4, 7, 9]

bool exists = binary_search(v.begin(), v.end(), 4); // true

// lower_bound: Returns iterator to first element >= target
auto it1 = lower_bound(v.begin(), v.end(), 4); 
int idx1 = distance(v.begin(), it1); // Index of 4 (3)

// upper_bound: Returns iterator to first element > target
auto it2 = upper_bound(v.begin(), v.end(), 4); 
int idx2 = distance(v.begin(), it2); // Index of 7 (4)

// 3. Min, Max, Accumulate, Reverse
int min_val = *min_element(v.begin(), v.end());
int max_val = *max_element(v.begin(), v.end());
long long sum = accumulate(v.begin(), v.end(), 0LL); // Sum of all elements
reverse(v.begin(), v.end());                         // Reverse vector in O(N)

// 4. Permutations
vector<int> p = {1, 2, 3};
do {
    // Process permutation [1, 2, 3], [1, 3, 2], etc.
} while (next_permutation(p.begin(), p.end()));
```

---

## 5. Bit Manipulation & Fast CP Hacks

Bitwise operations run directly on hardware registers in $O(1)$ time.

```cpp
int a = 5;  // Binary: 0101
int b = 3;  // Binary: 0011

int bit_and = a & b; // 0001 (1)
int bit_or  = a | b; // 0111 (7)
int bit_xor = a ^ b; // 0110 (6)
int bit_not = ~a;    // Bitwise NOT

// Bit Shift Tricks
int shift_left  = (1 << k);  // Calculates 2^k
int shift_right = (n >> k);  // Divides n by 2^k

// Checking if k-th bit is set (0-indexed)
bool is_set = (n & (1 << k)) != 0;

// Setting k-th bit
n |= (1 << k);

// Clearing k-th bit
n &= ~(1 << k);

// Toggling k-th bit
n ^= (1 << k);

// --- GCC Built-in Bit Functions (Extremely Fast!) ---
long long mask = 29; // 11101 in binary

int set_bits = __builtin_popcountll(mask); // Count set bits (1s) -> Output: 4
int leading_zeros = __builtin_clzll(mask);  // Count leading zeros
int trailing_zeros = __builtin_ctzll(mask); // Count trailing zeros
```

---

## 6. Contest Diagnostics & Beginner Roadmap

### 6.1 Understanding Judge Verdicts

* **AC (Accepted)**: Solution passed all test cases within constraints!
* **WA (Wrong Answer)**: Output did not match expected result. Check edge cases ($N=1$, negative numbers, zero, maximum constraints, integer overflow).
* **TLE (Time Limit Exceeded)**: Code took longer than time limit (usually 1.0 or 2.0s). Check time complexity ($O(N^2)$ instead of $O(N \log N)$) or infinite loops.
* **RE (Runtime Error / SIGSEGV)**: Out-of-bounds array access, division by zero, stack overflow (deep recursion).
* **MLE (Memory Limit Exceeded)**: Allocated more RAM than allowed (e.g., creating `int arr[10000][10000]`).

### 6.2 Local Compilation Flags

To catch warnings and memory errors locally before submitting:

```bash
g++ -std=c++17 -O2 -Wall -Wextra -Wshadow -fsanitize=address solution.cpp -o solution
```

### 6.3 Recommended Practice Roadmap

1. **CSES Problem Set** ([cses.fi/problemset](https://cses.fi/problemset)):
   - Complete the **Introductory Problems** and **Sorting and Searching** sections first.
2. **AtCoder Beginner Contests (ABC)** ([atcoder.jp](https://atcoder.jp)):
   - Join weekly live contests. Aim to consistently solve Problems A, B, and C.
3. **Codeforces** ([codeforces.com](https://codeforces.com)):
   - Participate in **Div. 3** and **Div. 4** contests. Upsolve at least 1 problem you couldn't solve during the contest.

---

## 7. Spaced Repetition Flashcards

#flashcards

Why should you pass vectors by `const vector<int>&` in C++ functions? :: To prevent creating a complete copy of the vector, avoiding $O(N)$ time and memory overhead per function call.

What is the difference between `lower_bound` and `upper_bound` in C++ STL? :: `lower_bound` returns an iterator to the first element $\ge$ target value, while `upper_bound` returns an iterator to the first element strictly $>$ target value.

How do you prevent integer overflow when multiplying two `int` variables `a` and `b` into a `long long` variable? :: Multiply by `1LL` first: `long long ans = 1LL * a * b;`.

What does `ios::sync_with_stdio(false); cin.tie(nullptr);` do? :: Disables synchronization between C stdio and C++ streams and unties `cin` from `cout`, making `cin`/`cout` significantly faster for competitive programming.

What is `static_cast<T>(expr)` used for in C++? :: It performs safe, compile-time checked conversions between compatible types (e.g., converting `int` to `double` or `int` to `long long`).

Why do we append `const` to member functions like `void print() const {}`? :: It promises that the function will not modify any member variables of the struct/class, allowing it to be called on `const` objects and references.

What does `= default` do when attached to a constructor? :: It instructs the compiler to generate its standard default implementation for that constructor (useful when custom constructors were declared).

What does `= delete` do when attached to a function or constructor? :: It explicitly forbids the function or constructor from being called, triggering a compile-time error if used (e.g. disabling copy constructors).
