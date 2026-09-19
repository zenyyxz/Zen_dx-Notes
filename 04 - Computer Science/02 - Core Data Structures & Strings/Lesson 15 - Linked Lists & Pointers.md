---
title: Lesson 15 - Linked Lists & Pointers
subject: Computer Science
unit: 15
competency: Implement linked data structures, manage memory pointers safely, and detect cycles
tags:
  - Computer-Science
  - Competitive-Programming
  - LinkedLists
  - Pointers
  - Flashcards
---
---
# :LiBook: Lesson 15: Linked Lists & Pointers

> [!ABSTRACT] Scope
> Understand node pointer representations, singly/doubly linked lists, cycle detection, and memory ownership.

> [!TIP] Modern C++ Memory Safety
> For software engineering pointer safety and smart pointers (`unique_ptr`, `shared_ptr`), refer to [[00 - C++ Reference/Complete C++ Reference for Competitive Programming#1.9 Smart Pointers & Memory Ownership (`unique_ptr`, `shared_ptr`, `weak_ptr`)|Complete C++ Reference (Smart Pointers)]].

---
## 1. Singly Linked List Node & Operations

```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;

    ListNode(int x) : val(x), next(nullptr) {}
};

// Insert node at head: O(1)
ListNode* insertHead(ListNode* head, int val) {
    ListNode* new_node = new ListNode(val);
    new_node->next = head;
    return new_node;
}

// Traverse and print list: O(N)
void printList(ListNode* head) {
    ListNode* curr = head;
    while (curr != nullptr) {
        cout << curr->val << " -> ";
        curr = curr->next;
    }
    cout << "NULL\n";
}
```

---
## 2. Floyd's Cycle Detection (Fast & Slow Pointers)

Detect if a linked list contains a cycle in $O(N)$ time and $O(1)$ memory.

```cpp
bool hasCycle(ListNode* head) {
    if (!head || !head->next) return false;

    ListNode* slow = head;
    ListNode* fast = head;

    while (fast && fast->next) {
        slow = slow->next;          // Moves 1 step
        fast = fast->next->next;    // Moves 2 steps

        if (slow == fast) {
            return true; // Cycle detected!
        }
    }
    return false; // Reached end, no cycle
}
```

---
## 3. Reversing a Linked List

```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;
    ListNode* curr = head;

    while (curr != nullptr) {
        ListNode* next_temp = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next_temp;
    }
    return prev; // New head of reversed list
}
```

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the space complexity of Floyd's Cycle Detection algorithm? :: $O(1)$ auxiliary space.

How fast do the two pointers move in Floyd's Cycle Detection? :: The `slow` pointer advances 1 step per iteration, while the `fast` pointer advances 2 steps.

What is the time complexity of reversing a singly linked list iteratively? :: $O(N)$ time.
