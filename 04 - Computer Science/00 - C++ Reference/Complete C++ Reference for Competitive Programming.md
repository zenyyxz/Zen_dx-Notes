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

#### 3. `constexpr` (Compile-Time Constant)
While `const` means "I promise not to change this at runtime," `constexpr` means "this value is known at **compile time**." 
It forces the compiler to evaluate expressions during compilation, which can drastically improve runtime performance.

```cpp
// Evaluated at compile-time! No runtime overhead.
constexpr int factorial(int n) {
    return n <= 1 ? 1 : (n * factorial(n - 1));
}

// Constant expressions for sizes
constexpr int MAX_N = 100005;
int dp[MAX_N]; // ✅ Valid array size because MAX_N is known at compile time

int main() {
    constexpr int val = factorial(5); // val becomes 120 at compile time
    // constexpr int runtime_val = get_input(); // ❌ Error: get_input() happens at runtime
}
```

> [!TIP] `const` vs `constexpr`
> Use `constexpr` whenever you know the value before the program even runs (like array sizes, math constants, or simple precomputed formulas). Use `const` for values that are initialized at runtime but shouldn't change afterward (like function parameters).

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

### 1.9 Smart Pointers & Memory Ownership (`unique_ptr`, `shared_ptr`, `weak_ptr`)

In traditional C, dynamic memory allocation uses `malloc`/`free`. In traditional C++, `new`/`delete` is used. However, raw dynamic memory allocation is error-prone:
- If you forget `delete`, you get a **Memory Leak**.
- If you call `delete` twice on the same pointer, you get a **Double Free Crash**.
- If you access memory after deleting it, you get a **Dangling Pointer**.

Modern C++ (C++11 standard and later) introduced **Smart Pointers** (in header `<memory>`). Smart pointers wrap raw heap pointers and automatically free memory when the smart pointer goes out of scope (**RAII**: Resource Acquisition Is Initialization).

| Smart Pointer | Ownership Model | Copyable? | Overhead | Use Case |
| :--- | :--- | :--- | :--- | :--- |
| `std::unique_ptr<T>` | Exclusive (Single Owner) | ❌ No (Move-only) | ⚡ Zero overhead (same as raw pointer) | Trees, Graphs, Nodes, Factory objects |
| `std::shared_ptr<T>` | Shared (Reference Counted) | ✅ Yes | Small (Control block & atomic counter) | Shared graphs, assets, resource caches |
| `std::weak_ptr<T>` | Non-owning Observer | ✅ Yes | Small | Breaking cyclic references in `shared_ptr` |

---

#### 1. `std::unique_ptr<T>` (Exclusive Ownership)
`unique_ptr` ensures that **only one pointer owns the heap memory at any given time**. When `unique_ptr` goes out of scope, it automatically calls `delete`.

```cpp
#include <iostream>
#include <memory>
using namespace std;

struct Node {
    int val;
    unique_ptr<Node> left;  // Node exclusively owns its children!
    unique_ptr<Node> right;

    Node(int v) : val(v), left(nullptr), right(nullptr) {}
};

int main() {
    // Preferred creation helper (C++14): std::make_unique<T>(constructor_args...)
    auto root = make_unique<Node>(10);
    root->left = make_unique<Node>(5);
    root->right = make_unique<Node>(15);

    cout << "Root value: " << root->val << '\n';       // 10
    cout << "Left child: " << root->left->val << '\n'; // 5

    // unique_ptr CANNOT be copied!
    // auto copy_root = root; // ❌ Compiler error! Copy constructor is deleted.

    // unique_ptr CAN be moved (transferring ownership)
    unique_ptr<Node> moved_root = move(root); // 'root' is now nullptr, 'moved_root' owns the memory!
    if (root == nullptr) {
        cout << "Original root is now null after move!\n";
    }

    // Memory is automatically deleted here when 'moved_root' goes out of scope! No 'delete' needed.
}
```

---

#### 2. `std::shared_ptr<T>` (Shared Ownership)
Multiple `shared_ptr` instances can point to the exact same heap memory. It maintains an internal **Reference Counter**. Memory is deleted only when the last `shared_ptr` pointing to it is destroyed.

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    // Creation helper: std::make_shared<T>(constructor_args...)
    shared_ptr<int> p1 = make_shared<int>(42);
    cout << "Use count: " << p1.use_count() << '\n'; // 1 owner

    {
        shared_ptr<int> p2 = p1; // Copying is allowed! Reference count increases.
        cout << "Use count: " << p1.use_count() << '\n'; // 2 owners (p1 and p2)
        cout << "*p2 = " << *p2 << '\n';                  // 42
    } // 'p2' goes out of scope here! Reference count decreases back to 1.

    cout << "Use count after p2 scope ends: " << p1.use_count() << '\n'; // 1 owner

    // Heap integer (42) is automatically deleted here when p1 goes out of scope.
}
```

---

#### 3. `std::weak_ptr<T>` (Breaking Cyclic References)
If two `shared_ptr` objects point to each other (e.g. parent points to child, child points to parent), their reference count will **never reach zero**, causing a memory leak! A `weak_ptr` observes a `shared_ptr` object without increasing its reference count.

```cpp
#include <iostream>
#include <memory>
using namespace std;

struct Person {
    string name;
    shared_ptr<Person> friend_ptr;  // Owning reference
    weak_ptr<Person> weak_friend;   // Non-owning reference (prevents cycles)

    Person(string n) : name(n) {}
};

int main() {
    auto alice = make_shared<Person>("Alice");
    auto bob = make_shared<Person>("Bob");

    alice->weak_friend = bob; // Doesn't increase Bob's reference count

    // Accessing object from weak_ptr: convert to shared_ptr via .lock()
    if (shared_ptr<Person> temp = alice->weak_friend.lock()) {
        cout << "Alice's friend is: " << temp->name << '\n';
    } else {
        cout << "Friend no longer exists!\n";
    }
}
```

---

> [!NOTE] Smart Pointers vs Competitive Programming Strategy
> * In **Software Engineering**, smart pointers (`unique_ptr` / `shared_ptr`) are the gold standard for resource safety.
> * In **Competitive Programming**, allocation overhead matters. For speed and zero overhead, competitive programmers often use:
>   1. `std::vector` (handles dynamic memory automatically).
>   2. Flat global arrays / Node pools (`int left_child[MAXN]`, `int right_child[MAXN]`) instead of pointers.
>   3. `std::unique_ptr` when creating recursive tree nodes dynamically without manual `delete`.

---

### 1.10 The `static` Keyword — Four Different Uses

`static` is one of the most overloaded keywords in C++. Its meaning depends entirely on **where** it is written.

| Context | Meaning |
| :--- | :--- |
| `static` inside a **function** | Variable persists across calls — only initialized once |
| `static` at **file/global scope** | Limits symbol visibility to the current translation unit (`.cpp` file) |
| `static` on a **class/struct member variable** | One shared copy across all instances |
| `static` on a **class/struct member function** | Can be called without an instance, has no `this` pointer |

---

#### 1. `static` Local Variable (Persistent Across Function Calls)

A `static` local variable is initialized **only once** (the first time the function is called) and retains its value between subsequent calls. It lives in the global memory segment, not on the stack.

```cpp
#include <iostream>
using namespace std;

int callCount() {
    static int count = 0; // Initialized to 0 exactly once, never reset!
    count++;
    return count;
}

int main() {
    cout << callCount() << '\n'; // 1
    cout << callCount() << '\n'; // 2
    cout << callCount() << '\n'; // 3
}
```

> [!TIP] CP Use Case: Memoization Cache
> In Competitive Programming, `static` local variables are sometimes used inside functions to cache lookup tables (like precomputed factorials) that should only be built once.

---

#### 2. `static` at File/Global Scope (Internal Linkage)

When placed at global scope or in the global namespace, `static` restricts the symbol to the **current `.cpp` file only** (internal linkage). Other files cannot see or link against it.

```cpp
// file_a.cpp
static int helper_value = 42; // Only visible inside file_a.cpp

static void helperFunction() { // Only callable from file_a.cpp
    // ...
}
```

This is less commonly needed since `static` at global scope has largely been superseded by **anonymous namespaces** in modern C++.

---

#### 3. `static` Class/Struct Member Variable (Shared Across All Instances)

A `static` member variable belongs to the **class itself**, not to any individual object instance. All instances share the same single copy.

```cpp
#include <iostream>
using namespace std;

struct Counter {
    static int total_count; // Declared inside struct (one copy for all instances!)
    int id;

    Counter() {
        total_count++;
        id = total_count;
    }
};

int Counter::total_count = 0; // Must be defined OUTSIDE the struct

int main() {
    Counter a, b, c;
    cout << a.id << '\n';           // 1
    cout << b.id << '\n';           // 2
    cout << Counter::total_count << '\n'; // 3 (accessed via class name)
}
```

---

#### 4. `static` Member Function (No `this` Pointer)

A `static` member function belongs to the **class** rather than any specific instance. It **cannot access** non-static member variables (because there is no `this` pointer).

```cpp
#include <iostream>
using namespace std;

struct MathUtils {
    static long long power(long long base, long long exp) {
        long long result = 1;
        while (exp > 0) {
            if (exp & 1) result *= base;
            base *= base;
            exp >>= 1;
        }
        return result;
    }
};

int main() {
    // Call static member function without creating an instance!
    cout << MathUtils::power(2, 10) << '\n'; // 1024
}
```

> [!NOTE] Static Member Functions in CP
> This pattern is commonly used to create **utility namespaces** or **factory classes** grouping related helper functions together.

---

### 1.11 The `friend` & `virtual` Keywords

---

#### Part A: `friend` — Granting Private Access

By default, `private` and `protected` members of a class are inaccessible to outside code. The `friend` keyword **explicitly grants** a specific function or another class access to those private members. It is *not* mutual — if A is a friend of B, B is not automatically a friend of A.

**Use Cases**:
- Overloading `operator<<` (stream output) for a class.
- Tightly coupled helper classes (e.g. Iterator accessing a Container's internals).

```cpp
#include <iostream>
using namespace std;

struct Vector2D {
private:
    double x, y; // Private members

public:
    Vector2D(double x, double y) : x(x), y(y) {}

    // Declare the stream output operator as a friend function
    // so it can read private members x and y directly
    friend ostream& operator<<(ostream& os, const Vector2D& v);

    // Declare a friend function that adds two vectors
    friend Vector2D addVectors(const Vector2D& a, const Vector2D& b);
};

// Definition outside the class — has access to private x and y
ostream& operator<<(ostream& os, const Vector2D& v) {
    os << "(" << v.x << ", " << v.y << ")"; // Direct private member access!
    return os;
}

Vector2D addVectors(const Vector2D& a, const Vector2D& b) {
    return Vector2D(a.x + b.x, a.y + b.y); // Direct private member access!
}

int main() {
    Vector2D v1(3.0, 4.0);
    Vector2D v2(1.0, 2.0);

    cout << v1 << '\n';                        // (3, 4)
    cout << addVectors(v1, v2) << '\n';        // (4, 6)
}
```

> [!NOTE] `friend` is not OOP heresy
> `friend` is intentional — it is a **named, auditable grant** of access. It is far better than making members `public` just because one specific function needs them.

---

#### Part B: `virtual` — Runtime Polymorphism & Inheritance

`virtual` enables **runtime polymorphism**: the decision of *which* function implementation to call is made at runtime based on the actual type of the object, not the declared type of the pointer/reference.

**Without `virtual` (Compile-Time Binding)**:
```cpp
struct Shape {
    void area() { cout << "Shape has no area\n"; }
};

struct Circle : Shape {
    void area() { cout << "Area = pi * r^2\n"; }
};

int main() {
    Shape* s = new Circle();
    s->area(); // ❌ Prints "Shape has no area" — wrong! (Pointer is Shape*, so Shape::area() is called)
}
```

**With `virtual` (Runtime Binding)**:
```cpp
#include <iostream>
using namespace std;

struct Shape {
    virtual void area() const {  // 'virtual' marks function for runtime dispatch
        cout << "Shape has no area\n";
    }

    virtual ~Shape() {}  // ⚠️ Always declare virtual destructor in base classes!
};

struct Circle : Shape {
    double radius;
    Circle(double r) : radius(r) {}

    void area() const override {  // 'override' guarantees we are overriding a virtual function
        cout << "Area = " << 3.14159 * radius * radius << '\n';
    }
};

struct Rectangle : Shape {
    double w, h;
    Rectangle(double w, double h) : w(w), h(h) {}

    void area() const override {
        cout << "Area = " << w * h << '\n';
    }
};

int main() {
    Shape* shapes[3];
    shapes[0] = new Circle(5.0);
    shapes[1] = new Rectangle(4.0, 6.0);
    shapes[2] = new Circle(3.0);

    for (int i = 0; i < 3; i++) {
        shapes[i]->area(); // ✅ Correct function called at runtime via vtable!
    }

    for (int i = 0; i < 3; i++) delete shapes[i];
}
```

---

#### `virtual` Vocabulary Table

| Keyword / Feature | Meaning |
| :--- | :--- |
| `virtual void func()` | Enables runtime dispatch via vtable for this function |
| `override` | Asserts that this function overrides a base `virtual` function (compile-time safety check) |
| `virtual ~Base()` | **Virtual destructor** — ensures derived class destructors are called when deleting through a base pointer |
| `= 0` (pure virtual) | `virtual void func() = 0;` — makes the class **abstract** (cannot be instantiated directly) |

```cpp
// Pure Virtual / Abstract Base Class
struct Animal {
    virtual void speak() const = 0; // Pure virtual: no implementation
    virtual ~Animal() {}
};

struct Dog : Animal {
    void speak() const override { cout << "Woof!\n"; }
};

// Animal a; // ❌ Cannot instantiate abstract class!
Dog d;
d.speak(); // ✅ "Woof!"
```

> [!WARNING] Always Use `virtual` Destructor in Base Classes
> If a base class destructor is **not** `virtual` and you `delete` a derived object through a base class pointer, only the base class destructor runs — the derived class destructor is **silently skipped**, causing resource leaks!

---

### 1.12 The `inline` Keyword

The `inline` keyword is a suggestion to the compiler to **replace a function call with the actual code** of the function itself. This avoids the overhead of a function call (pushing registers to the stack, jumping, returning) at the cost of slightly increasing the binary size if used everywhere.

#### 1. Functions
For small, frequently called helper functions (like `min`, `max`, or custom math functions), `inline` can provide a micro-optimization in Competitive Programming.

```cpp
// Suggests the compiler physically places `a < b ? a : b` wherever `my_min` is called
inline int my_min(int a, int b) {
    return a < b ? a : b;
}

int main() {
    int x = my_min(5, 10); // Compiler turns this into: int x = (5 < 10) ? 5 : 10;
}
```
> [!NOTE] Modern Compilers are Smart
> Modern C++ compilers (like GCC with `-O2` or `-O3`) automatically inline small functions even if you don't write the `inline` keyword. So while good to know, writing `inline` is rarely strictly necessary for performance today.

#### 2. `inline` Variables (C++17)
In modern C++, `inline` has gained a new, more important meaning for **header-only libraries**. `inline` allows you to define a global variable or static class member in a header file without causing "Multiple Definition" linkage errors when included in multiple `.cpp` files.

```cpp
struct MathUtils {
    // Before C++17: You had to declare this here, and define it outside in exactly one .cpp file
    // With C++17: You can initialize it directly inside the struct!
    inline static const double PI = 3.1415926535;
};
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

What is `std::unique_ptr` in C++ and why can't it be copied? :: `std::unique_ptr` represents exclusive ownership of heap memory; it cannot be copied (its copy constructor is deleted) to prevent duplicate deletion of the same memory, but it can be moved using `std::move()`.

What is the main difference between `std::unique_ptr` and `std::shared_ptr`? :: `std::unique_ptr` has a single exclusive owner with zero overhead, whereas `std::shared_ptr` allows multiple owners using an internal reference counter that deletes memory when count reaches 0.

Why is `std::weak_ptr` used alongside `std::shared_ptr`? :: `std::weak_ptr` observes a `shared_ptr` object without increasing its reference count, preventing cyclic reference memory leaks.

What does `static` mean when applied to a local variable inside a function? :: The variable is initialized only once (the first call) and retains its value between subsequent function calls, living in global memory rather than the stack.

What does `static` mean on a class/struct member variable? :: A single shared copy of that variable is shared across all instances of the class, accessed via `ClassName::variable`.

Why can a `static` member function not access regular (non-static) member variables? :: Because `static` member functions have no `this` pointer — they belong to the class itself, not to any specific object instance.

What does the `friend` keyword do in C++? :: It grants a specific external function or class direct access to a class's `private` and `protected` members.

What is `friend` most commonly used for in C++? :: Overloading stream output (`operator<<`) for custom types, since `operator<<` must be a free function but needs access to private members.

What does `virtual` on a member function enable? :: Runtime polymorphism — the correct overriding function is selected at runtime based on the actual object type, not the static pointer/reference type.

What is the difference between `virtual` and a pure virtual (`= 0`) function? :: A `virtual` function has a default implementation in the base class; a pure virtual function (`= 0`) has no implementation, making the class abstract and impossible to instantiate directly.

Why must base class destructors almost always be `virtual`? :: Without a `virtual` destructor, deleting a derived class through a base class pointer only calls the base destructor — the derived destructor is silently skipped, causing resource leaks.

What does the `override` keyword do? :: It tells the compiler to verify at compile-time that the function is actually overriding a `virtual` function in the base class, catching typos or signature mismatches.

What is the difference between `const` and `constexpr`? :: `const` means a value cannot be changed after initialization (which can happen at runtime), whereas `constexpr` means the value is strictly evaluated at compile time.

What does the `inline` keyword do when applied to a function? :: It suggests to the compiler to replace the function call with the actual code of the function to save function-call overhead, though modern compilers often do this automatically during optimization.
