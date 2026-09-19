---
title: Lesson 16 - Hash Tables & Hash Maps
subject: Computer Science
unit: 16
competency: Explain bucket collision resolution, map performance, and implement custom anti-hack hash functions
tags:
  - Computer-Science
  - Competitive-Programming
  - HashTables
  - UnorderedMap
  - AntiHack
  - Flashcards
---
---
# :LiBook: Lesson 16: Hash Tables & Hash Maps

> [!ABSTRACT] Scope
> Master hash table mechanics, collision resolution strategies (separate chaining vs open addressing), and custom hash functions to prevent Codeforces $O(N^2)$ hash-hack attacks.

---
## 1. Hash Table Mechanics: `std::map` vs `std::unordered_map`

| Container | Implementation | Average Time | Worst Case Time | Ordered Keys? |
| :--- | :--- | :--- | :--- | :--- |
| `std::map` | Red-Black Tree (BST) | $O(\log N)$ | $O(\log N)$ | ✅ Yes (Sorted) |
| `std::unordered_map` | Hash Table | $O(1)$ | $O(N)$ (Collisions!) | ❌ No (Unordered) |

---
## 2. Codeforces Anti-Hack Custom Hash

Standard GCC `std::unordered_map` uses an identity hash for integers (`hash<int>()(x) = x`). In Codeforces, adversaries can create test cases that force all keys into the exact same hash bucket, causing your solution to run in $O(N^2)$ and hit **Time Limit Exceeded (TLE)**!

**Fix**: Use a randomized custom hash struct using `std::chrono`.

```cpp
#include <iostream>
#include <unordered_map>
#include <chrono>
using namespace std;

// Custom Anti-Hack Hash for Integer Keys
struct custom_hash {
    static uint64_t splitmix64(uint64_t x) {
        // High quality 64-bit mixer function
        x += 0x9e3779b97f4a7c15;
        x = (x ^ (x >> 30)) * 0xbf58476d1ce4e5b9;
        x = (x ^ (x >> 27)) * 0x94d049bb133111eb;
        return x ^ (x >> 31);
    }

    size_t operator()(uint64_t x) const {
        static const uint64_t FIXED_RANDOM = 
            chrono::steady_clock::now().time_since_epoch().count();
        return splitmix64(x + FIXED_RANDOM);
    }
};

int main() {
    // Anti-Hack Safe Unordered Map
    unordered_map<long long, int, custom_hash> safe_map;

    safe_map[1000000000LL] = 1;
    cout << "Value: " << safe_map[1000000000LL] << '\n';
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why can standard `std::unordered_map<int, int>` be hacked to $O(N^2)$ on Codeforces? :: Because standard GCC hash uses identity hash function, allowing targeted test cases to cause $O(N)$ hash bucket collisions per operation.

What fixes the Codeforces $O(N^2)$ unordered_map hack? :: Passing a `custom_hash` functor with a randomized seed (`chrono::steady_clock`).

What is the worst-case time complexity of `std::map` vs `std::unordered_map`? :: `std::map` is guaranteed $O(\log N)$ worst-case, while un-customized `std::unordered_map` is $O(N)$ worst-case.
