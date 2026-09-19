---
title: Lesson 03 - C++ STL & Core Data Structures
subject: Computer Science
unit: 03
competency: Select and apply appropriate STL containers based on operational time complexities
tags:
  - Computer-Science
  - Competitive-Programming
  - STL
  - DataStructures
  - Flashcards
---
---
# :LiBook: Lesson 03: C++ STL & Core Data Structures

> [!ABSTRACT] Scope
> Master the standard containers in C++ (`vector`, `pair`, `set`, `map`, `stack`, `queue`, `priority_queue`). Selecting the right container reduces solution complexity.

> [!TIP] Full Reference
> For deep-dive implementations of STL containers, custom comparators, and hash maps, see [[00 - C++ Reference/Complete C++ Reference for Competitive Programming|Complete C++ Reference for Competitive Programming]].

---
## 1. Quick Complexity Summary

| Container | Internal Structure | Access | Insert/Delete | Find / Search |
| :--- | :--- | :--- | :--- | :--- |
| `std::vector` | Dynamic Array | $O(1)$ | $O(1)$ at end, $O(N)$ middle | $O(N)$ ($O(\log N)$ sorted) |
| `std::set` | Red-Black Tree (BST) | $O(\log N)$ min/max | $O(\log N)$ | $O(\log N)$ |
| `std::map` | Red-Black Tree | $O(\log N)$ key | $O(\log N)$ | $O(\log N)$ |
| `std::priority_queue` | Binary Heap | $O(1)$ top | $O(\log N)$ push/pop | N/A |
| `std::unordered_map` | Hash Table | N/A | $O(1)$ avg, $O(N)$ worst | $O(1)$ avg |

---
## 2. Priority Queues (Max-Heap vs Min-Heap)

```cpp
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

int main() {
    // 1. Max-Heap (Default: largest element on top)
    priority_queue<int> max_pq;
    max_pq.push(10);
    max_pq.push(50);
    max_pq.push(20);
    cout << max_pq.top() << '\n'; // 50
    max_pq.pop();                 // Removes 50

    // 2. Min-Heap (Smallest element on top)
    priority_queue<int, vector<int>, greater<int>> min_pq;
    min_pq.push(10);
    min_pq.push(50);
    min_pq.push(20);
    cout << min_pq.top() << '\n'; // 10
    min_pq.pop();                 // Removes 10
}
```

---
## 3. Pairs, Tuples & Auto-Sorting

`std::pair<T1, T2>` automatically sorts by `.first`, then by `.second`.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<pair<int, int>> events;
    events.push_back({5, 2});
    events.push_back({1, 9});
    events.push_back({5, 1});

    sort(events.begin(), events.end());
    // Result order: {1, 9}, {5, 1}, {5, 2}
    for (auto [time, type] : events) {
        cout << time << " " << type << '\n';
    }
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the time complexity of inserting an element into `std::set` or `std::map`? :: $O(\log N)$ time, as it maintains a balanced binary search tree.

How do you instantiate a Min-Heap in C++ using `std::priority_queue`? :: `priority_queue<int, vector<int>, greater<int>> min_pq;`.

Why are pairs useful for interval sorting in contests? :: Because `std::pair` naturally sorts by its first element, and breaks ties using its second element.
