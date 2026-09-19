---
title: Lesson 03 - C++ STL & Core Data Structures
subject: Computer Science
unit: 03
competency: Select and use standard C++ containers for common contest tasks
tags:
  - Computer-Science
  - Competitive-Programming
  - Cpp
  - STL
  - DataStructures
  - Flashcards
---
---
# :LiBook: Lesson 03: C++ STL & Core Data Structures

> [!ABSTRACT] Scope
> The STL gives you tested implementations. Know what each container stores, its main operations, and their costs.

---
## 1. The Everyday Containers

| Container | Use | Key cost |
| :--- | :--- | :--- |
| `vector<T>` | resizable array | indexing $O(1)$, append amortised $O(1)$ |
| `string` | characters | indexing $O(1)$ |
| `stack<T>` | last in, first out | push/pop/top $O(1)$ |
| `queue<T>` | first in, first out | push/pop/front $O(1)$ |
| `deque<T>` | both ends | push/pop at ends $O(1)$ |
| `set<T>` | sorted unique values | insert/find $O(\log n)$ |
| `map<K,V>` | sorted key-value pairs | insert/find $O(\log n)$ |
| `unordered_map<K,V>` | hash key-value pairs | average insert/find $O(1)$ |
| `priority_queue<T>` | repeatedly get largest value | push/pop $O(\log n)$ |

---
## 2. `vector`, Sorting, and Iterators

```cpp
vector<int> a = {4, 1, 4, 2};
a.push_back(7);
sort(a.begin(), a.end());

for (int x : a) cout << x << ' ';
// 1 2 4 4 7
```

Use `a.begin()` and `a.end()` for STL algorithms. The end iterator points **one past** the final element.

---
## 3. Frequency Counting

```cpp
map<int, int> freq;
for (int x : a) freq[x]++;

for (auto [value, count] : freq) {
    cout << value << " occurs " << count << " times\n";
}
```

For values in a small known range, a `vector<int> freq(maxValue + 1)` is simpler and faster.

---
## 4. Heap: Always Take the Best Available Item

```cpp
priority_queue<int> pq; // max-heap
pq.push(5);
pq.push(2);
pq.push(9);
cout << pq.top(); // 9

priority_queue<int, vector<int>, greater<int>> minHeap;
```

A priority queue is not fully sorted. Only `top()` is guaranteed to be the best element.

---

## 5. Linked List (`std::list`)

`std::list` is a doubly linked list. It does **not** support random access (`O(n)` to reach an element), but insertion and deletion at any known iterator are `O(1)`.

```cpp
list<int> ll = {1, 2, 3};
ll.push_front(0);
ll.push_back(4);
ll.erase(next(ll.begin())); // remove second element
```

Use it when you need frequent insertions/deletions in the middle and never need to index by position.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Which STL container is usually best for a dynamic indexed array? :: `vector`.

What is the difference between `set` and `unordered_set`? :: `set` keeps values sorted with $O(\log n)$ operations; `unordered_set` has average $O(1)$ operations but no sorted order.

What does `priority_queue<int>` return at `top()`? :: The largest stored integer.

What container supports `O(1)` insertion in the middle but not `O(1)` indexing? :: `std::list` (doubly linked list).
