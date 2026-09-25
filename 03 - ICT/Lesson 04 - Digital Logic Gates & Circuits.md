---
title: Lesson 04 - Digital Logic Gates & Circuits
subject: AL ICT
unit: 04
competency: Uses logic gates to design basic digital circuits and devices
tags:
  - AL-ICT
  - Lesson-04
  - LogicGates
  - BooleanAlgebra
  - KarnaughMap
  - CombinationalLogic
  - Flashcards
---
# :LiBook: Lesson 04: Digital Logic Gates & Circuits

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Basic Gates (AND, OR, NOT) & Universal Gates (NAND, NOR) & XOR/XNOR
> - Laws of Boolean Algebra & De Morgan's Theorems
> - Karnaugh Maps (K-Maps) for Boolean Simplification
> - Combinational Logic Circuits (Adders, Decoders, Encoders, MUX)
> - Sequential Logic & Flip-Flops concept

---
## 1. Logic Gates Summary

|   Gate   |                     Boolean Expression                      | Truth Table Summary                                 | Symbol Concept       |
| :------: | :---------------------------------------------------------: | :-------------------------------------------------- | :------------------- |
| **AND**  |                       $F = A \cdot B$                       | Output is 1 **only if all inputs are 1**.           | D-shape              |
|  **OR**  |                         $F = A + B$                         | Output is 1 **if at least one input is 1**.         | Curved shield        |
| **NOT**  |                     $F = \overline{A}$                      | Inverts input ($0 \rightarrow 1, 1 \rightarrow 0$). | Triangle with bubble |
| **NAND** |                 $F = \overline{A \cdot B}$                  | Inverted AND (0 only if all inputs are 1).          | AND with bubble      |
| **NOR**  |                   $F = \overline{A + B}$                    | Inverted OR (1 only if all inputs are 0).           | OR with bubble       |
| **XOR**  |      $F = A \oplus B = A\overline{B} + \overline{A}B$       | Output is 1 if inputs are **different**.            | Double-curved OR     |
| **XNOR** | $F = \overline{A \oplus B} = AB + \overline{A}\overline{B}$ | Output is 1 if inputs are **identical**.            | XOR with bubble      |

> [!IMPORTANT] Universal Gates
> **NAND** and **NOR** are called **Universal Gates** because any digital logic circuit can be designed using only NAND gates or only NOR gates.

---
## 2. Laws of Boolean Algebra & De Morgan's Laws

- **Identity Laws**: $A \cdot 1 = A$, $A + 0 = A$
- **Null / Dominance Laws**: $A \cdot 0 = 0$, $A + 1 = 1$
- **Idempotent Laws**: $A \cdot A = A$, $A + A = A$
- **Inverse / Complement Laws**: $A \cdot \overline{A} = 0$, $A + \overline{A} = 1$
- **Double Negation**: $\overline{\overline{A}} = A$
- **Commutative Laws**: $A \cdot B = B \cdot A$, $A + B = B + A$
- **Associative Laws**: $(A \cdot B) \cdot C = A \cdot (B \cdot C)$, $(A + B) + C = A + (B + C)$
- **Distributive Laws**: $A \cdot (B + C) = AB + AC$, $A + (B \cdot C) = (A + B)(A + C)$
- **Absorption Laws**: $A + AB = A$, $A(A + B) = A$, $A + \overline{A}B = A + B$

> [!KEY-CONCEPT] De Morgan's Theorems
> 1. $\overline{A \cdot B} = \overline{A} + \overline{B}$ (NAND equals OR with inverted inputs)
> 2. $\overline{A + B} = \overline{A} \cdot \overline{B}$ (NOR equals AND with inverted inputs)

---
## 3. Minterms and Maxterms

Minterms and maxterms give a standard way to write Boolean functions directly from a truth table. They are also used to label K-map cells.

| Term | Definition | Rule for a row of the truth table | Canonical form |
| :--- | :--- | :--- | :--- |
| **Minterm** ($m_i$) | A **product (AND) term** that contains every input variable exactly once. It has a value of `1` for **exactly one** input combination. | Write a variable **uncomplemented** when its input is `1`, and **complemented** when its input is `0`. | Add (OR) the minterms for every row where $F = 1$: $F = \Sigma m(\ldots)$ — canonical **SOP**. |
| **Maxterm** ($M_i$) | A **sum (OR) term** that contains every input variable exactly once. It has a value of `0` for **exactly one** input combination. | Write a variable **complemented** when its input is `1`, and **uncomplemented** when its input is `0`. | Multiply (AND) the maxterms for every row where $F = 0$: $F = \Pi M(\ldots)$ — canonical **POS**. |

### Example

For the input row $A B C = 1\ 0\ 1$ (binary $101_2 = 5$):

- The **minterm** is $m_5 = A\overline{B}C$. It is `1` only when $A=1$, $B=0$, and $C=1$.
- The **maxterm** is $M_5 = (\overline{A} + B + \overline{C})$. It is `0` only for that same input combination.

> [!TIP] Remember
> A minterm describes an output-`1` row, while a maxterm describes an output-`0` row. The subscript is the decimal value of the input combination when the variables are ordered consistently (for example, $ABC$).

---
## 3A. Quick SOP ↔ POS Conversion (Double-Complement Toggle)

When you have a Boolean expression in one canonical form and need the other **fast**:

### Method 1: Index Complement (Canonical Forms Only)
- **SOP → POS**: $F = \Sigma m(\text{indices})$ → $F = \Pi M(\text{all missing indices from } 0 \text{ to } 2^n-1)$
- **POS → SOP**: $F = \Pi M(\text{indices})$ → $F = \Sigma m(\text{all missing indices from } 0 \text{ to } 2^n-1)$

### Method 2: Double-Complement + De Morgan's (Works on Any Expression)
1. Double-complement the function: $F = \overline{\overline{F}}$
2. Apply De Morgan's Theorem to the **inner** complement
3. Simplify double negations ($\overline{\overline{X}} = X$)

**Example — SOP to POS:**
$$
F = A\overline{B} + \overline{A}B \quad \text{(XOR as SOP)}
$$
$$
\overline{F} = \overline{A\overline{B} + \overline{A}B}
$$
$$
\overline{F} = (\overline{A} + B)(A + \overline{B}) \quad \text{(De Morgan's 1st Law)}
$$
$$
F = \overline{(\overline{A} + B)(A + \overline{B})}
$$
For **canonical POS**, just use the maxterms from the 0-rows of the truth table, or use the missing indices from Method 1.

### Method 3: K-Map (Visual & Reliable)
- Plot the function on a K-map
- **For SOP**: Group the **1s** → write product terms
- **For POS**: Group the **0s** → write sum terms → AND them together

> [!TIP] Remember
> Grouping 0s in a K-map directly yields POS. Variable = 0 → uncomplemented in sum term; Variable = 1 → complemented in sum term.

---

## 4. Karnaugh Maps (K-Maps)

K-Maps visually simplify Boolean expressions into **Sum of Products (SOP)** form without algebraic manipulation.

> [!INFO] Deep Dive Note
> For 2, 3, and 4-variable K-map layout, Gray code ordering, and step-by-step grouping examples, read: [[Subtopics/Karnaugh Maps & Boolean Simplification|Karnaugh Maps & Boolean Simplification Guide]].

---
## 5. Combinational Logic Circuits

A **Combinational Circuit** is a circuit whose ==output depends **solely on current inputs** (no memory).==
<!--SR:!2026-09-29,4,270-->

### A. Half Adder
Adds two 1-bit binary numbers ($A, B$):
- $Sum(S) = A \oplus B$
- $Carry(C) = A \cdot B$
### B. Full Adder
Adds three 1-bit binary numbers ($A, B, C_{in}$):
- $Sum(S) = A \oplus B \oplus C_{in}$
- $CarryOut(C_{out}) = AB + C_{in}(A \oplus B)$
### C. Decoder & Encoder & Multiplexer (MUX)
- **Decoder**: Converts an $n$-bit binary input into $2^n$ unique output lines (e.g., 2-to-4 decoder).
- **Encoder**: Converts $2^n$ input lines into an $n$-bit binary output code.
- **Multiplexer (MUX)**: Selects one of $2^n$ input data lines and routes it to a single output line using $n$ selection lines.

---
## 6. Sequential Logic Circuits

A **Sequential Circuit**'s ==output depends on **both current inputs and past states (memory)**.==
- Built using **Flip-Flops** (SR, D, JK, T Flip-Flops).
  - **Flip-Flop**: An **edge-triggered bistable circuit** that stores **1 bit**; changes state only on a clock transition.
- Controlled by a **Clock Signal**.
- Used to construct CPU registers, counters, and RAM memory cells.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why are NAND and NOR gates called Universal Gates? :: Because any Boolean function or basic logic gate can be implemented using exclusively NAND gates or exclusively NOR gates.
<!--SR:!2026-09-29,4,270-->

State De Morgan's First Law. :: $\overline{A \cdot B} = \overline{A} + \overline{B}$.

State De Morgan's Second Law. :: $\overline{A + B} = \overline{A} \cdot \overline{B}$.
<!--SR:!2026-10-01,14,290-->

What is the Boolean expression for the output of an XOR gate with inputs A and B? :: $F = A \oplus B = A\overline{B} + \overline{A}B$.
<!--SR:!2026-09-29,4,270-->

What is the Boolean simplified result of $A + \overline{A}B$? :: $A + B$ (Absorption Law).

What is a minterm? :: An AND (product) term containing every variable exactly once; it is 1 for exactly one truth-table input combination. For a row, use an uncomplemented variable for input 1 and a complemented variable for input 0.
<!--SR:!2026-09-29,4,270-->

What is a maxterm? :: An OR (sum) term containing every variable exactly once; it is 0 for exactly one truth-table input combination. For a row, use a complemented variable for input 1 and an uncomplemented variable for input 0.

What are the Boolean expressions for Sum and Carry in a Half Adder? :: $Sum = A \oplus B$, $Carry = A \cdot B$.
<!--SR:!2026-09-29,4,270-->

What is the key structural difference between Combinational and Sequential logic circuits? :: Combinational circuits output depends only on current inputs (no memory); Sequential circuits output depends on current inputs and past state (has memory).
<!--SR:!2026-09-29,4,270-->

What is the function of a Multiplexer (MUX)? :: It selects one data signal from multiple ($2^n$) input lines and routes it to a single output line based on $n$ select lines.
<!--SR:!2026-09-29,4,270-->