---
id: LC-0002
title: Add Two Numbers
platform: LeetCode
difficulty: Medium
patterns:
  - Linked-List
  - Elementary-Math-Simulation
  - Dummy-Head
tags:
  - CP-Problem
  - LeetCode
  - LinkedList
  - Math
date_solved: 2026-10-18
status: Solved
---
# :LiCode: LC-0002: Add Two Numbers

> [!ABSTRACT] Problem Summary
> - **Source Link**: [LeetCode 2 - Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)
> - **Constraints**:
>   - Number of nodes in each list is in range $[1, 100]$.
>   - $0 \le \text{Node.val} \le 9$.
>   - Numbers are guaranteed to have no leading zeros (except $0$ itself).
>   - Stored in **reverse order** (head is the least significant / units digit).
> - **Goal**: Add the two numbers and return the sum as a reversed linked list.

---

## 1. The Mental Model: Elementary School Addition

Because the digits are stored in **reverse order**, the heads of `l1` and `l2` are already the **units digit** ($10^0$). This means we do not need to reverse the lists; we can just simulate addition on paper from left to right:

```text
    l1:  2 -> 4 -> 3    (represents 342)
  + l2:  5 -> 6 -> 4    (represents 465)
  -------------------
  Sum:   7 -> 0 -> 8    (represents 807, because 342 + 465 = 807)
```

At each position:
1. $\text{total} = \text{val}_1 + \text{val}_2 + \text{carry}$
2. Current digit to save $= \text{total} \pmod{10}$
3. New carry $= \lfloor \text{total} / 10 \rfloor$

---

## 2. Common Pitfalls & Traps

> [!WARNING] The Number One Trap: Converting to Integer First
> A common beginner instinct is:
> 1. Traverse `l1` to get `342`.
> 2. Traverse `l2` to get `465`.
> 3. Add `342 + 465 = 807`.
> 4. Convert `807` into a linked list.
> 
> **Why this fails:** Each list can have up to **100 digits**!
> In C++, `long long` maxes out at $\approx 9 \times 10^{18}$ (only 18–19 digits). A 100-digit number will cause immediate integer overflow. You **must** perform digit-by-digit simulation.

> [!TIP] The "Dummy Head" Technique
> When building a linked list dynamically, managing the very first node (`head`) is awkward because `head` starts as `nullptr`.
> 
> **Solution:** Create a dummy node on the stack:
> ```cpp
> ListNode dummy(0);
> ListNode* tail = &dummy;
> ```
> Append all new nodes to `tail->next`, and advance `tail`. At the end, simply return `dummy.next`!

---

## 3. Optimal Solution (One-Pass Simulation)

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */

class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode dummy(0);          // Dummy head to anchor the result list
        ListNode* tail = &dummy;    // Pointer to the current end of the result
        int carry = 0;              // Carry value from the previous column

        // Keep looping as long as either list has digits, OR a leftover carry exists
        while (l1 != nullptr || l2 != nullptr || carry != 0) {
            int sum = carry;

            if (l1 != nullptr) {
                sum += l1->val;
                l1 = l1->next;
            }

            if (l2 != nullptr) {
                sum += l2->val;
                l2 = l2->next;
            }

            carry = sum / 10;                     // New carry for next column
            tail->next = new ListNode(sum % 10);  // Store only the units digit
            tail = tail->next;
        }

        return dummy.next;  // Actual head of the resulting list
    }
};
```

### Complexity Analysis:
- **Time Complexity:** $O(\max(N, M))$ where $N$ and $M$ are the lengths of `l1` and `l2`. We visit each node at most once.
- **Space Complexity:** $O(\max(N, M))$ to allocate the new linked list nodes.

---

## 4. Edge Cases Handled Automatically
1. **Lists of Unequal Length:** e.g. `[9, 9]` and `[1]` ($99 + 1 = 100$). The loop continues until both `nullptr` are reached.
2. **Final Carry:** e.g. `[5]` + `[5]` = `[0, 1]`. The condition `carry != 0` ensures an extra node for the final carry is created even after both lists are exhausted.
3. **Single Zero:** `[0]` + `[0]` = `[0]`.

---

## 5. Connected Theory & Vault Notes
- [[04 - Computer Science/02 - Core Data Structures & Strings/Lesson 15 - Linked Lists & Pointers|Lesson 15 - Linked Lists & Pointers]] — Node representation, traversal, and pointer manipulation.
- [[04 - Computer Science/00 - C++ Reference/Complete C++ Reference for Competitive Programming#1.6 Pointers & References|Complete C++ Reference (Pointers & References)]] — Struct pointers and arrow operators (`->`).

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why does converting linked lists to integers fail in LC-0002 (Add Two Numbers)? :: The linked list can contain up to 100 nodes (100 digits), which vastly exceeds the limit of C++ `long long` (~19 digits), causing integer overflow.

Why is the "dummy head" pattern used when constructing a linked list? :: It avoids writing special-case conditional logic (`if (head == nullptr)`) to initialize the first node; you append to `tail` and return `dummy.next`.

What is the condition in LC-0002's `while` loop to cleanly handle unequal list lengths and the final carry? :: `while (l1 != nullptr || l2 != nullptr || carry != 0)`.
