---
title: Karnaugh Maps & Boolean Simplification
subject: AL ICT
subtopic: Digital Logic
tags:
  - AL-ICT
  - Subtopic
  - K-Map
  - BooleanSimplification
  - LogicGates
---
# Subtopic: Karnaugh Maps (K-Maps) & Boolean Simplification

> [!ABSTRACT] Core Focus
> Step-by-step methodology for constructing 2, 3, and 4-variable K-maps, Gray code cell positioning, grouping rules, and deriving minimal Sum-of-Products (SOP) expressions.

---
## 1. What is a Karnaugh Map?

A **K-Map** is a graphical method for simplifying Boolean expressions into minimal **Sum of Products (SOP)** form without needing algebraic manipulation.

### Cell Positioning & Gray Code Ordering:
Adjacent cells in a K-Map differ by **only 1 bit** (Gray code: `00, 01, 11, 10`).

---
## 2. 3-Variable K-Map Layout (Variables A, B, C)

Rows represent variable $A$ (`0, 1`); Columns represent variables $BC$ (`00, 01, 11, 10`).

| $A \backslash BC$ | 00 ($\overline{B}\overline{C}$) | 01 ($\overline{B}C$) | 11 ($BC$) | 10 ($B\overline{C}$) |
| :---: | :---: | :---: | :---: | :---: |
| **0 ($\overline{A}$)** | $m_0$ | $m_1$ | $m_3$ | $m_2$ |
| **1 ($A$)** | $m_4$ | $m_5$ | $m_7$ | $m_6$ |

---
## 3. 4-Variable K-Map Layout (Variables A, B, C, D)

Rows represent $AB$ (`00, 01, 11, 10`); Columns represent $CD$ (`00, 01, 11, 10`).

| $AB \backslash CD$ | 00 ($\overline{C}\overline{D}$) | 01 ($\overline{C}D$) | 11 ($CD$) | 10 ($C\overline{D}$) |
| :---: | :---: | :---: | :---: | :---: |
| **00 ($\overline{A}\overline{B}$)** | $m_0$ | $m_1$ | $m_3$ | $m_2$ |
| **01 ($\overline{A}B$)** | $m_4$ | $m_5$ | $m_7$ | $m_6$ |
| **11 ($AB$)** | $m_{12}$ | $m_{13}$ | $m_{15}$ | $m_{14}$ |
| **10 ($A\overline{B}$)** | $m_8$ | $m_9$ | $m_{11}$ | $m_{10}$ |

---
## 4. K-Map Grouping Rules

1. Groups must contain **$2^n$ adjacent 1-cells** ($1, 2, 4, 8, 16$).
2. Make groups as **large as possible** to eliminate the maximum number of variables.
3. Groups can **wrap around edges** (top-to-bottom, left-to-right).
4. Every 1-cell must be included in at least one group (overlapping is allowed).
5. Variables that change value ($0 \rightarrow 1$) within a group are **eliminated**.

---
## 5. Worked Example (3-Variable K-Map)

Given minterms: $F(A, B, C) = \Sigma m(1, 3, 5, 7)$

1. Populate K-Map cells $m_1, m_3, m_5, m_7$ with `1`.
2. Observe column $BC = 01$ and $BC = 11$. Group all 4 ones in a single quad group ($m_1, m_3, m_5, m_7$).
3. Variable $A$ changes from $0$ to $1 \rightarrow$ eliminated. Variable $B$ changes from $0$ to $1 \rightarrow$ eliminated. Variable $C = 1$ remains constant.
4. **Simplified Result**: $F = C$.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is a Karnaugh map used for? :: To simplify Boolean expressions graphically into a minimal Sum-of-Products (SOP) expression.

What code orders K-map rows and columns? :: Gray code: 00, 01, 11, 10 — adjacent cells differ by only one bit.

How many cells does an n-variable K-map have? :: 2^n cells.

In a 3-variable K-map, what labels the rows and columns? :: Rows: A (0, 1); columns: BC in Gray order (00, 01, 11, 10).

In a 4-variable K-map, what labels the rows and columns? :: Rows: AB; columns: CD; both in Gray order.

What sizes can a K-map group have? :: Powers of 2: 1, 2, 4, 8 or 16 adjacent 1-cells.

Why should groups be as large as possible? :: A larger group eliminates more variables, giving a simpler expression.

How many variables does a group of 2^k cells eliminate? :: k variables; the remaining variables stay constant.

Can K-map groups wrap around the edges? :: Yes; top/bottom and left/right edges are treated as adjacent.

Can groups overlap, and must every 1 be covered? :: Yes, groups may overlap; every 1-cell must be in at least one group.

What is a Sum-of-Products (SOP) expression? :: An OR of AND terms, for example $AB + \overline{A}C$.

For $F(A,B,C)=\Sigma m(1,3,5,7)$, what is the simplified expression? :: $F = C$.

Why must K-map cells use Gray code instead of normal binary order? :: So adjacent cells differ by one bit, allowing a group to eliminate the variable that changes.