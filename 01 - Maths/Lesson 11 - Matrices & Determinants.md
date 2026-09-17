---
title: Lesson 11 - Matrices & Determinants
subject: AL Combined Maths
unit: 11
competency: Performs matrix operations, evaluates determinants, finds inverse matrices, and solves systems of linear equations
tags:
  - AL-Maths
  - Lesson-11
  - Matrices
  - Determinants
  - InverseMatrix
  - Flashcards
---
# :LiBook: Lesson 11: Matrices & Determinants

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Matrix Algebra: Addition, Scalar Multiplication, Matrix Multiplication (Row-by-Column rule)
> - Transpose of Matrix $A^T$ ($(AB)^T = B^T A^T$)
> - **Determinants**: $\det(A) = |A|$ for $2 \times 2$ and $3 \times 3$ matrices
> - **Inverse Matrix ($A^{-1}$)**:
>   - $A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$ (where $A$ is non-singular $\det(A) \ne 0$)
>   - For $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$, $A^{-1} = \frac{1}{ad - bc} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$
> - Solving System of Linear Equations $A X = B \implies X = A^{-1} B$ or Cramer's Rule.

---
## 1. 2x2 Matrix Inverse & System Solving

For matrix $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$:
$$\det(A) = ad - bc$$
$$A^{-1} = \frac{1}{ad - bc} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix} \quad (\text{provided } ad - bc \ne 0)$$

For system $A X = B$:
$$\begin{pmatrix} a & b \\ c & d \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} e \\ f \end{pmatrix} \implies \begin{pmatrix} x \\ y \end{pmatrix} = A^{-1} \begin{pmatrix} e \\ f \end{pmatrix}$$

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

State the inverse formula for a 2x2 matrix $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$. :: $A^{-1} = \frac{1}{ad - bc} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$ (provided $\det A = ad - bc \ne 0$).

What is a non-singular matrix? :: A square matrix whose determinant is non-zero ($\det A \ne 0$), meaning its inverse exists.

State the transpose reversal rule for matrix multiplication $(A B)^T$. :: $(A B)^T = B^T A^T$.

State the inverse reversal rule for matrix multiplication $(A B)^{-1}$. :: $(A B)^{-1} = B^{-1} A^{-1}$.

How is a system of linear equations $A X = B$ solved using matrix inversion? :: $X = A^{-1} B$ (provided $\det A \ne 0$).