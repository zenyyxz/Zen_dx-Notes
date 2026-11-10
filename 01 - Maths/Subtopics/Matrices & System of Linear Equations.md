---
title: Matrices & Systems of Equations Guide
subject: AL Combined Maths
subtopic: Algebra
tags:
  - AL-Maths
  - Subtopic
  - Matrices
  - LinearSystems
  - Flashcards
---
# :LiGrid3x3: Subtopic: Matrices & Systems of Equations Guide

> [!NOTE] Parent Lesson
> This is a companion guide to [[../Lesson 11 - Matrices & Determinants|Lesson 11 — Matrices & Determinants]]

> [!ABSTRACT] Core Focus
> Complete step-by-step $3 \times 3$ inverse computation algorithm, cofactor matrices, adjoint verification, solving 3-variable linear systems via $X = A^{-1}B$ and Cramer's Rule, matrix equations, and powers of square matrices.

---

## 1. Step-by-Step Algorithm: Inverting a $3 \times 3$ Matrix

To invert a $3 \times 3$ matrix $A = \begin{pmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{pmatrix}$:

```
Step 1: Compute Determinant det(A)
        Expand along row 1 (or any convenient row/col with zeros).
        If det(A) = 0 → STOP. Matrix is singular; no inverse exists.

Step 2: Calculate all 9 Minors M_ij
        M_ij is the 2 × 2 determinant obtained by deleting row i and col j.

Step 3: Construct the Cofactor Matrix C
        Apply the checkerboard sign pattern:
        C_ij = (-1)^(i+j) M_ij
        Pattern: [ +  -  + ]
                 [ -  +  - ]
                 [ +  -  + ]

Step 4: Form the Adjoint Matrix adj(A)
        Transpose the cofactor matrix: adj(A) = Cᵀ.
        (Row 1 of C becomes Col 1 of adj(A), etc.)

Step 5: Multiply by 1/det(A)
        A⁻¹ = (1/det A) · adj(A)

Step 6: Verification Check
        Verify that A · A⁻¹ = I (or test one diagonal element).
```

### Full Worked Example of $3 \times 3$ Inversion

Find $A^{-1}$ for:
$$A = \begin{pmatrix} 1 & 2 & 1 \\ 2 & 1 & 0 \\ 1 & 1 & 2 \end{pmatrix}$$

#### Step 1: Determinant
Expand along row 2 (contains a zero):
$$\det(A) = -2\begin{vmatrix} 2 & 1 \\ 1 & 2 \end{vmatrix} + 1\begin{vmatrix} 1 & 1 \\ 1 & 2 \end{vmatrix} - 0 = -2(4 - 1) + 1(2 - 1) = -2(3) + 1(1) = -6 + 1 = -5$$
Since $\det(A) = -5 \neq 0$, $A^{-1}$ exists.

#### Step 2 & 3: Cofactors
$$\begin{aligned}
C_{11} &= +\begin{vmatrix} 1 & 0 \\ 1 & 2 \end{vmatrix} = 2 - 0 = 2 \\
C_{12} &= -\begin{vmatrix} 2 & 0 \\ 1 & 2 \end{vmatrix} = -(4 - 0) = -4 \\
C_{13} &= +\begin{vmatrix} 2 & 1 \\ 1 & 1 \end{vmatrix} = 2 - 1 = 1 \\
C_{21} &= -\begin{vmatrix} 2 & 1 \\ 1 & 2 \end{vmatrix} = -(4 - 1) = -3 \\
C_{22} &= +\begin{vmatrix} 1 & 1 \\ 1 & 2 \end{vmatrix} = 2 - 1 = 1 \\
C_{23} &= -\begin{vmatrix} 1 & 2 \\ 1 & 1 \end{vmatrix} = -(1 - 2) = 1 \\
C_{31} &= +\begin{vmatrix} 2 & 1 \\ 1 & 0 \end{vmatrix} = 0 - 1 = -1 \\
C_{32} &= -\begin{vmatrix} 1 & 1 \\ 2 & 0 \end{vmatrix} = -(0 - 2) = 2 \\
C_{33} &= +\begin{vmatrix} 1 & 2 \\ 2 & 1 \end{vmatrix} = 1 - 4 = -3
\end{aligned}$$

The Cofactor Matrix $C$:
$$C = \begin{pmatrix} 2 & -4 & 1 \\ -3 & 1 & 1 \\ -1 & 2 & -3 \end{pmatrix}$$

#### Step 4: Adjoint Matrix $\text{adj}(A) = C^T$
$$\text{adj}(A) = \begin{pmatrix} 2 & -3 & -1 \\ -4 & 1 & 2 \\ 1 & 1 & -3 \end{pmatrix}$$

#### Step 5: Inverse Matrix
$$A^{-1} = -\frac{1}{5}\begin{pmatrix} 2 & -3 & -1 \\ -4 & 1 & 2 \\ 1 & 1 & -3 \end{pmatrix} = \frac{1}{5}\begin{pmatrix} -2 & 3 & 1 \\ 4 & -1 & -2 \\ -1 & -1 & 3 \end{pmatrix}$$

#### Step 6: Quick Check
$$A \cdot \text{adj}(A) = \begin{pmatrix} 1 & 2 & 1 \\ 2 & 1 & 0 \\ 1 & 1 & 2 \end{pmatrix}\begin{pmatrix} 2 & -3 & -1 \\ -4 & 1 & 2 \\ 1 & 1 & -3 \end{pmatrix} = \begin{pmatrix} 2-8+1 & -3+2+1 & -1+4-3 \\ 4-4+0 & -6+1+0 & -2+2+0 \\ 2-4+2 & -3+1+2 & -1+2-6 \end{pmatrix} = \begin{pmatrix} -5 & 0 & 0 \\ 0 & -5 & 0 \\ 0 & 0 & -5 \end{pmatrix} = -5 I \quad \checkmark$$

---

## 2. Solving a $3 \times 3$ System Using Matrix Inversion

Solve the system:
$$\begin{aligned}
x + 2y + z &= 4 \\
2x + y &= 1 \\
x + y + 2z &= 5
\end{aligned}$$

In matrix form $AX = B$:
$$\begin{pmatrix} 1 & 2 & 1 \\ 2 & 1 & 0 \\ 1 & 1 & 2 \end{pmatrix}\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 4 \\ 1 \\ 5 \end{pmatrix}$$

Notice coefficient matrix is $A$ from Section 1 above! Since $\det(A) = -5 \neq 0$:
$$X = A^{-1}B = \frac{1}{5}\begin{pmatrix} -2 & 3 & 1 \\ 4 & -1 & -2 \\ -1 & -1 & 3 \end{pmatrix}\begin{pmatrix} 4 \\ 1 \\ 5 \end{pmatrix}$$
$$\begin{pmatrix} x \\ y \\ z \end{pmatrix} = \frac{1}{5}\begin{pmatrix} -2(4) + 3(1) + 1(5) \\ 4(4) - 1(1) - 2(5) \\ -1(4) - 1(1) + 3(5) \end{pmatrix} = \frac{1}{5}\begin{pmatrix} -8 + 3 + 5 \\ 16 - 1 - 10 \\ -4 - 1 + 15 \end{pmatrix} = \frac{1}{5}\begin{pmatrix} 0 \\ 5 \\ 10 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \\ 2 \end{pmatrix}$$

**Solution**: $x = 0, \; y = 1, \; z = 2$.

---

## 3. Cramer's Rule for $3 \times 3$ Systems

Given system:
$$\begin{aligned}
a_1 x + b_1 y + c_1 z &= d_1 \\
a_2 x + b_2 y + c_2 z &= d_2 \\
a_3 x + b_3 y + c_3 z &= d_3
\end{aligned}$$

Define determinants:
$$\Delta = \begin{vmatrix} a_1 & b_1 & c_1 \\ a_2 & b_2 & c_2 \\ a_3 & b_3 & c_3 \end{vmatrix}, \quad \Delta_x = \begin{vmatrix} d_1 & b_1 & c_1 \\ d_2 & b_2 & c_2 \\ d_3 & b_3 & c_3 \end{vmatrix}, \quad \Delta_y = \begin{vmatrix} a_1 & d_1 & c_1 \\ a_2 & d_2 & c_2 \\ a_3 & d_3 & c_3 \end{vmatrix}, \quad \Delta_z = \begin{vmatrix} a_1 & b_1 & d_1 \\ a_2 & b_2 & d_2 \\ a_3 & b_3 & d_3 \end{vmatrix}$$

### Mathematical Derivation of Cramer's Rule
Consider the matrix equation $AX = B$. We know:
$$\text{adj}(A) \cdot AX = \text{adj}(A) \cdot B$$
$$(\det A \cdot I) X = \text{adj}(A) \cdot B$$
$$\det A \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} C_{11} & C_{21} & C_{31} \\ C_{12} & C_{22} & C_{32} \\ C_{13} & C_{23} & C_{33} \end{pmatrix}\begin{pmatrix} d_1 \\ d_2 \\ d_3 \end{pmatrix}$$

Looking at the first entry:
$$(\det A) x = d_1 C_{11} + d_2 C_{21} + d_3 C_{31}$$
The expression on the right is precisely the column-1 cofactor expansion of determinant $\Delta_x$!
Therefore:
$$(\det A) x = \Delta_x \implies x = \frac{\Delta_x}{\Delta} \quad (\Delta \neq 0)$$
Similarly:
$$y = \frac{\Delta_y}{\Delta}, \qquad z = \frac{\Delta_z}{\Delta}$$

---

## 4. Matrix Polynomials & Cayley-Hamilton Relations

For any $2 \times 2$ matrix $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$:
$$\text{trace}(A) = a + d, \qquad \det(A) = ad - bc$$

### Characteristic Relation
The matrix satisfies its own characteristic equation:
$$A^2 - (\text{trace } A)A + (\det A)I = O$$

**Proof**:
$$A^2 = \begin{pmatrix} a & b \\ c & d \end{pmatrix}\begin{pmatrix} a & b \\ c & d \end{pmatrix} = \begin{pmatrix} a^2+bc & b(a+d) \\ c(a+d) & bc+d^2 \end{pmatrix}$$
$$-(a+d)A = \begin{pmatrix} -a^2-ad & -b(a+d) \\ -c(a+d) & -ad-d^2 \end{pmatrix}$$
$$(\det A)I = \begin{pmatrix} ad-bc & 0 \\ 0 & ad-bc \end{pmatrix}$$
Adding these three matrices gives $\begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix} = O$. $\quad \checkmark$

### Finding Higher Powers and Inverses
From $A^2 - (\text{trace } A)A + (\det A)I = O$:
1. **Finding $A^{-1}$ without computing adjoint**:
   Multiply by $A^{-1}$:
   $$A - (\text{trace } A)I + (\det A)A^{-1} = O \implies A^{-1} = \frac{1}{\det A}\big( (\text{trace } A)I - A \big)$$
2. **Finding higher powers $A^n$**:
   Multiply by $A$:
   $$A^3 = (\text{trace } A)A^2 - (\det A)A$$
   Substitute $A^2$ to express $A^3$ purely as a linear combination $\alpha A + \beta I$.

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the relationship between the cofactor $C_{ij}$ and the minor $M_{ij}$ of a matrix? :: $C_{ij} = (-1)^{i+j} M_{ij}$. <!--SR:!2026-11-20,1,230-->

How is the adjoint matrix $\text{adj}(A)$ obtained from the cofactor matrix $C$? :: By transposing the cofactor matrix: $\text{adj}(A) = C^T$. <!--SR:!2026-11-20,1,230-->

State the formula for $A^{-1}$ in terms of the adjoint and determinant. :: $A^{-1} = \frac{1}{\det(A)}\text{adj}(A)$, provided $\det(A) \neq 0$. <!--SR:!2026-11-21,2,250-->

What is the result of multiplying a row of matrix $A$ with the cofactors of a different row? :: It equals zero: $\sum_{k=1}^n a_{ik} C_{jk} = 0$ for $i \neq j$. <!--SR:!2026-11-21,2,250-->

State the characteristic equation satisfied by any $2 \times 2$ matrix $A$. :: $A^2 - (\text{trace } A)A + (\det A)I = O$. <!--SR:!2026-11-22,3,250-->

How can $A^{-1}$ be written in terms of $A$, $I$, trace, and determinant for a $2 \times 2$ matrix? :: $A^{-1} = \frac{1}{\det A}\big((\text{trace } A)I - A\big)$. <!--SR:!2026-11-22,3,250-->

State Cramer's Rule for a 3-variable system $AX = B$. :: $x = \frac{\Delta_x}{\Delta}$, $y = \frac{\Delta_y}{\Delta}$, $z = \frac{\Delta_z}{\Delta}$ where $\Delta = \det A \neq 0$. <!--SR:!2026-11-23,4,250-->

How is $\Delta_x$ constructed in Cramer's Rule? :: By replacing the first column (coefficients of $x$) in determinant $\Delta$ with the constants column $B$. <!--SR:!2026-11-23,4,250-->

What happens to the solutions of $AX = B$ if $\det A = 0$ and $\text{adj}(A) \cdot B \neq O$? :: The system is inconsistent and has **no solution**. <!--SR:!2026-11-24,5,250-->

What happens to the solutions of $AX = B$ if $\det A = 0$ and $\text{adj}(A) \cdot B = O$? :: The system is dependent and has **infinitely many solutions** (or may be inconsistent in special geometric cases). <!--SR:!2026-11-24,5,250-->

State the reversal rule for the inverse of product $ABC$. :: $(ABC)^{-1} = C^{-1} B^{-1} A^{-1}$. <!--SR:!2026-11-25,6,250-->

What is the trace of a square matrix? :: The sum of the elements along the main diagonal: $\text{trace}(A) = \sum_{i=1}^n a_{ii}$. <!--SR:!2026-11-25,6,250-->

If $\det A = 3$ for a $3 \times 3$ matrix $A$, what is $\det(\text{adj } A)$? :: $\det(\text{adj } A) = (\det A)^{n-1} = 3^{3-1} = 3^2 = 9$. <!--SR:!2026-11-26,7,250-->

If $A$ is an invertible symmetric matrix ($A^T = A$), is $A^{-1}$ also symmetric? :: Yes, because $(A^{-1})^T = (A^T)^{-1} = A^{-1}$. <!--SR:!2026-11-26,7,250-->
