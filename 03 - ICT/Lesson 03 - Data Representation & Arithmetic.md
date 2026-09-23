---
title: Lesson 03 - Data Representation & Computer Arithmetic
subject: AL ICT
unit: 03
competency: Investigates how instructions and data are represented in computers and exploit them in arithmetic and logic operations
tags:
  - AL-ICT
  - Lesson-03
  - NumberSystems
  - TwosComplement
  - CharacterEncoding
  - Flashcards
---
#  Lesson 03: Data Representation & Computer Arithmetic

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide & PDF Reference)
> - Evolution & History of Number Systems (Tally Marks, Hieroglyphs, Babylonian, Roman, Hindu-Arabic)
> - Positional vs. Non-Positional Number Systems (Base/Radix, MSD/LSD)
> - The 4 Core Positional Systems (Decimal, Binary, Octal, Hexadecimal) & Computer Applications
> - Conversions (Integer & Fractional, Base $N$, Direct 3-bit / 4-bit Grouping)
> - Signed Number Representation (Sign-Magnitude, 1's Complement, 2's Complement)
> - Binary & Hexadecimal Arithmetic, 2's Complement Subtraction & Overflow Detection
> - Character Encoding Systems (BCD, EBCDIC, ASCII Standard & Extended, Unicode UTF-8/16/32)

---
## 1. Evolution & History of Number Systems

A **Number System** is a structured set of symbols (digits) and rules used to record quantities, represent values, and perform arithmetic calculations.

>[!note]
Tally Marks --> Egyptian Hieroglyphs --> Babylonian Base-60 --> Roman Numerals --> Hindu-Arabic Base-10

### Historical Milestones:
1. **Tally Marks (Base 1)**:
   - Earliest counting method using vertical strokes (`||||`).
   - Still used today for counting election votes, tracking attendance, and sports scores.
   - *Limitation*: Inefficient and unusable for large numbers.
2. **Egyptian Numerals (Hieroglyphs)**:
   - Used distinct symbols for units ($1$), tens ($10$), hundreds ($100$), thousands ($1,000$), etc.
3. **Babylonian Numerals (Base-60 / Sexagesimal)**:
   - Developed base-60 system. 60 was chosen because it is highly divisible by $2, 3, 4, 5, 6, 10, 12, 15, 20, 30, \text{ and } 60$, making fractions easier to calculate. (Legacy survives in 60 seconds/minute, 60 minutes/hour, $360^\circ$ circle).
4. **Mayan Numerals (Base-20 / Vigesimal)**:
   - Used a shell for zero, a dot for 1, and a bar for 5.
5. **Roman Numerals (Non-Positional System)**:
   - Symbols: $I(1), V(5), X(10), L(50), C(100), D(500), M(1000)$.
   - *Limitations*: Lacks a symbol for zero, lacks place value concept, calculations ($+,-,\times,\div$) were extremely complex.
6. **Hindu-Arabic System & Zero (Base-10 Positional System)**:
   - Indian mathematician **Brahmagupta (628 CE)** first formally defined **zero ($0$)** as a number and established rules for zero arithmetic.
   - Replaced Roman numerals worldwide due to its compact place-value notation and ease of calculation.

---
## 2. Positional vs. Non-Positional Number Systems

| Parameter              | Positional Number System                                                           | Non-Positional Number System                                         |
| :--------------------- | :--------------------------------------------------------------------------------- | :------------------------------------------------------------------- |
| **Definition**         | Value of a digit depends on its **face value** and its **position (place value)**. | Value of a symbol is fixed regardless of its position in the number. |
| **Base / Radix ($r$)** | Has a fixed base $r$ (e.g., Base 10, Base 2).                                      | No base or fixed radix.                                              |
| **Zero Symbol**        | Contains a symbol for zero ($0$) to act as a placeholder.                          | No symbol for zero ($0$).                                            |
| **Arithmetic**         | Simple, fast, and structured ($+,-,\times,\div$).                                  | Complex, cumbersome, and hard to automate.                           |
| **Examples**           | Decimal, Binary, Octal, Hexadecimal.                                               | Roman Numerals ($I, V, X$), Tally Marks.                             |

### Key Terminology:
- **Base / Radix ($r$)**: Total number of unique digits/symbols used in the system.
- **Place Value**: Weight assigned to a position ($r^{\text{position}}$).
- **MSD (Most Significant Digit)**: Leftmost digit carrying the highest place-value weight.
- **LSD (Least Significant Digit)**: Rightmost digit carrying the lowest place-value weight.

---
## 3. The Four Core Positional Systems & Computer Applications

| System          | Base ($r$) | Allowed Digits / Symbols       | Position Weights | Computer Application / Usage                                                                                                                            |
| :-------------- | :--------: | :----------------------------- | :--------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Decimal**     |     10     | $0, 1, 2, 3, 4, 5, 6, 7, 8, 9$ |      $10^n$      | Everyday human communication and mathematics.                                                                                                           |
| **Binary**      |     2      | $0, 1$                         |      $2^n$       | Fundamental data representation in all digital computer hardware.                                                                                       |
| **Octal**       |     8      | $0, 1, 2, 3, 4, 5, 6, 7$       |      $8^n$       | Legacy shorthand for binary; Unix file permission notation (`chmod 755`).                                                                               |
| **Hexadecimal** |     16     | $0-9, A(10)-F(15)$             |      $16^n$      | Modern binary shorthand, RAM memory addresses (`0x7FFA1234`), HTML color codes (`#FF5733`), IPv6 (`2001:0db8:...`), Windows error codes (`0x0000007B`). |

> [!QUESTION] Why do computers use Binary (Base 2)?
> Computer electronic circuits are built using transistors and bistable switches that operate reliably in **two distinct voltage states**:
> - `0`: OFF state, Low Voltage ($0\text{V} - 0.8\text{V}$), or Absence of signal.
> - `1`: ON state, High Voltage ($2.4\text{V} - 5\text{V}$), or Presence of signal.
> Binary is highly noise-tolerant, physically reliable, and simplifies hardware implementation of Boolean logic.

---
## 4. Comprehensive Conversion Rules

### A. Non-Decimal to Decimal (Positional Expansion Method)
Multiply each digit $d_i$ by its positional weight $r^i$ and sum:
$$\text{Formula: } N_{10} = \sum (d_i \times r^i)$$

> [!EXAMPLE] Worked Examples:
> 1. $(1101.101)_2 = (1 \times 2^3) + (1 \times 2^2) + (0 \times 2^1) + (1 \times 2^0) + (1 \times 2^{-1}) + (0 \times 2^{-2}) + (1 \times 2^{-3}) = 8 + 4 + 0 + 1 + 0.5 + 0 + 0.125 = (13.625)_{10}$
> 2. $(37.4)_8 = (3 \times 8^1) + (7 \times 8^0) + (4 \times 8^{-1}) = 24 + 7 + 0.5 = (31.5)_{10}$
> 3. $(2A.8)_{16} = (2 \times 16^1) + (10 \times 16^0) + (8 \times 16^{-1}) = 32 + 10 + 0.5 = (42.5)_{10}$

---
### B. Decimal to Non-Decimal (Division-Multiplication Method)
- **Integer Part**: Repeated division by target base $r$; record remainders; read from **bottom to top (MSB to LSB)**.
- **Fractional Part**: Repeated multiplication by target base $r$; record integer parts; read from **top to bottom**.

> [!EXAMPLE] Convert $(25.625)_{10}$ to Binary:
> - **Integer (25)**: $25 \div 2 = 12 \text{ r } \mathbf{1}$, $12 \div 2 = 6 \text{ r } \mathbf{0}$, $6 \div 2 = 3 \text{ r } \mathbf{0}$, $3 \div 2 = 1 \text{ r } \mathbf{1}$, $1 \div 2 = 0 \text{ r } \mathbf{1} \longrightarrow (11001)_2$
> - **Fraction (0.625)**: $0.625 \times 2 = \mathbf{1}.25$, $0.25 \times 2 = \mathbf{0}.5$, $0.5 \times 2 = \mathbf{1}.0 \longrightarrow (.101)_2$
> - **Result**: $(25.625)_{10} = (11001.101)_2$

---
### C. Direct Conversions (Binary $\leftrightarrow$ Octal $\leftrightarrow$ Hexadecimal)
- **Binary $\leftrightarrow$ Octal**: Group binary bits in sets of **3 bits** ($2^3 = 8$).
- **Binary $\leftrightarrow$ Hexadecimal**: Group binary bits in sets of **4 bits** ($2^4 = 16$).

>[!note]
Octal Digit  <----(3 bits)---->  Binary Bits  <----(4 bits)---->  Hex Digit

> [!EXAMPLE] Convert $(11010110.1011)_2$:
> - **To Octal**: Group 3 bits from radix point $\rightarrow$ `(011) (010) (110) . (101) (100)` $= (326.54)_8$
> - **To Hexadecimal**: Group 4 bits from radix point $\rightarrow$ `(1101) (0110) . (1011)` $= (D6.B)_{16}$

---
## 5. Signed Binary Number Representation

Computers use fixed $n$-bit registers to represent signed integers (both positive and negative values):

### Real-World Need for Negative Numbers:
- Sub-zero temperatures (e.g., $-15^\circ\text{C}$).
- Financial bank overdrafts (e.g., $-\$500$).
- Sub-sea elevations (e.g., $-430\text{ m}$).

### Comparison of Signed 8-Bit Integer Systems:

| Representation | MSB Meaning | Positive Range ($+25$) | Negative Range ($-25$) | Zero Problem | Subtraction Hardware |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Unsigned** | Value bit ($2^7$) | `00011001` ($+25$) | N/A (Cannot represent negative) | Single Zero | N/A |
| **Sign-Magnitude** | $0 = +$, $1 = -$ | `00011001` | `10011001` | **Dual Zero** ($+0$ = `00000000`, $-0$ = `10000000`) | Requires separate subtractor |
| **1's Complement** | $0 = +$, $1 = -$ | `00011001` | `11100110` (Invert bits) | **Dual Zero** ($+0$ = `00000000`, $-0$ = `11111111`) | End-around carry required |
| **2's Complement** | $0 = +$, $1 = -$ | `00011001` | `11100111` (1's Comp + 1) | **Single Zero** (`00000000`) | Uses addition circuit (Optimal) |

> [!KEY-CONCEPT] 2's Complement Properties
> 1. **Range for $n$ bits**: $-2^{n-1} \text{ to } +2^{n-1} - 1$ (e.g., for 8 bits: $-128 \text{ to } +127$).
> 2. **Key Hardware Advantage**: Subtraction $A - B$ is evaluated as addition $A + (-B)_{\text{2's Comp}}$, eliminating the need for separate CPU subtractor circuits.

> [!TIP] 2's Comp Short Convert (Negative Numbers — Not-Syllabus Extra)
> Scan from **right → left** until first `1`. Keep it + everything right. **Flip everything left**. Add `-`. Example `11111010`: first `1` at bit 1 → `10` kept, `111110` flipped → `000001` → `00000110` = `6` → `-6`.
>
> **Reverse Shortcut: Negative Decimal → 2's Complement (Single Scan)**
> 1. Write the **absolute value** in binary (padded to $n$ bits)
> 2. Scan **right → left** until the **first `1`** (include it)
> 3. **Keep** that `1` and everything to its **right**
> 4. **Flip** every bit to its **left** (0→1, 1→0)
> 
> *Example: $-25_{10}$ in 8-bit* → $+25 = 	exttt{00011001}$
> Scan right→left: first `1` at bit 0 → keep `1`; bits left: `0001100` → flip → `1110011`
> Result: **`11100111`** ✓
> 
> *Why it works:* This single scan **combines** the standard "flip all bits then add 1" into one pass—the `+1` propagates left until it hits the first `0` (which was a `1` before flipping), so everything right of that first `1` stays unchanged.

---
## 6. Binary & Hexadecimal Arithmetic & Overflow

### A. Binary Arithmetic Rules:
- $0 + 0 = 0$
- $0 + 1 = 1$
- $1 + 0 = 1$
- $1 + 1 = 0 \text{ (Carry 1)}$
- $1 + 1 + 1 = 1 \text{ (Carry 1)}$

### B. 2's Complement Subtraction Example (8-Bit):
Evaluate $18_{10} - 25_{10}$:
1. $+18_{10} = \texttt{00010010}_2$
2. $-25_{10} = \texttt{11100111}_2$ (2's complement of $+25$)
3. Add: $\texttt{00010010} + \texttt{11100111} = \texttt{11111001}_2$
4. Verify result: 2's complement of $\texttt{11111001}$ is $-(00000111_2) = -7_{10}$. Correct!

### C. Arithmetic Overflow:
**Overflow** occurs when the result of an arithmetic operation exceeds the maximum representable capacity of the $n$-bit register.

> [!WARNING] Overflow Conditions in 2's Complement
> 1. Adding two **positive** numbers yields a **negative** result (MSB = 1).
> 2. Adding two **negative** numbers yields a **positive** result (MSB = 0).
> 3. **Hardware Rule**: Carry-in to MSB $\neq$ Carry-out of MSB ($\text{Carry}_{in} \oplus \text{Carry}_{out} = 1$).

---
## 7. Character Encoding Systems

Non-numeric data (letters, punctuation, symbols, emojis) must be encoded into binary bit patterns for computer storage and transmission.

>[!note]
>BCD (4-bit) ---> EBCDIC (8-bit) ---> ASCII (7-bit / 8-bit) ---> Unicode (UTF-8 / UTF-16)

### 1. BCD (Binary Coded Decimal):
- Uses **4 bits** to represent each individual decimal digit ($0 - 9$).
- Example: $(59)_{10}$ in BCD = `0101 1001`.

### 2. EBCDIC (Extended Binary Coded Decimal Interchange Code):
- **8-bit** code developed by IBM for mainframes ($2^8 = 256$ characters).

### 3. ASCII (American Standard Code for Information Interchange):
- Developed in 1963 by ANSI; became the universal standard for personal computers and UNIX.
- **Standard ASCII (7-bit)**: Represents $2^7 = 128$ characters (Codes `0` to `127`).
  - **33 Non-printable Control Characters** (Codes `0 - 31` and `127`; e.g., Line Feed `10`, Carriage Return `13`, Escape `27`).
  - **95 Printable Characters** (Codes `32 - 126`; e.g., Space `32`).
- **Extended ASCII (8-bit)**: Represents $2^8 = 256$ characters (Codes `0` to `255`), adding accented letters and graphic symbols.

> [!IMPORTANT] Essential ASCII Codes to Remember for A/L Exams
> - `'0'` = $48_{10} = (00110000)_2 = (30)_{16}$
> - `'A'` = $65_{10} = (01000001)_2 = (41)_{16}$
> - `'a'` = $97_{10} = (01100001)_2 = (61)_{16}$
> - *Note*: Lowercase letters are exactly $32_{10}$ higher than uppercase letters (`'a' - 'A' = 32`).

### 4. Unicode (Universal Encoding Standard):
- **Limitation of ASCII**: Restricted to English characters; cannot represent world languages (Sinhala, Tamil, Chinese, Arabic, Emojis).
- **Unicode**: Universal character encoding standard capable of representing over 140,000 characters from all global scripts.
- **Encodings**:
  - **UTF-8**: Variable-length encoding (1 to 4 bytes per character). **100% backward compatible with ASCII** (ASCII characters `0-127` use exactly 1 byte with identical code values).
  - **UTF-16**: Uses 2 or 4 bytes per character.
  - **UTF-32**: Uses fixed 4 bytes per character.
- Example: Unicode code points written in Hex (e.g., `U+0041` for `'A'`, `U+1F600` for 😀 emoji).

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Why did the Babylonian base-60 number system prove advantageous for calculations? :: Base 60 is highly divisible by many numbers ($2, 3, 4, 5, 6, 10, 12, 15, 20, 30, 60$), simplifying fraction calculations.

What major contribution did mathematician Brahmagupta make to number systems in 628 CE? :: He formally defined zero ($0$) as a number and established mathematical rules for arithmetic involving zero.
<!--SR:!2026-08-04,4,270-->

State 3 major drawbacks of Non-Positional Number Systems like Roman Numerals. :: 1. Lack of a symbol for zero, 2. Absence of place-value notation, 3. Extreme complexity in performing arithmetic calculations.
<!--SR:!2026-09-13,15,290-->

What is the difference between face value and place value of a digit in a positional system? :: Face value is the intrinsic value of the digit itself; place value is the weight assigned to the position of the digit ($r^{\text{position}}$).

Why do digital computers use the Binary number system instead of Decimal? :: Computer electronic circuits operate reliably on two voltage states (High/Low, ON/OFF), making binary highly noise-tolerant and physically reliable.

List 4 modern computer applications of Hexadecimal numbers. :: 1. RAM/CPU memory addresses, 2. HTML/CSS color codes (`#FF5733`), 3. IPv6 addresses, 4. Windows error codes (`0x0000007B`).
<!--SR:!2026-08-04,4,270-->

Convert $(13.625)_{10}$ to Binary. :: $(1101.101)_2$.

Convert $(11010110.1011)_2$ to Hexadecimal. :: $(D6.B)_{16}$.

What are the two major drawbacks of Sign-Magnitude binary representation? :: 1. Dual representation of zero ($+0$ and $-0$), 2. Requires separate hardware circuits for addition and subtraction.
<!--SR:!2026-10-03,16,290-->

What is the range of signed integers that can be stored in an 8-bit register using 2's complement? :: $-128 \text{ to } +127$ (Formula: $-2^{n-1} \text{ to } +2^{n-1} - 1$).
<!--SR:!2026-08-03,3,250-->

What is the 8-bit 2's complement representation of $-25_{10}$? :: `11100111`.

How is arithmetic overflow detected in 2's complement addition? :: When adding two numbers of the same sign produces a result with an opposite sign bit, or when carry-in to MSB differs from carry-out of MSB.

How many non-printable control characters and printable characters exist in standard 7-bit ASCII? :: 33 non-printable control characters and 95 printable characters (Total $2^7 = 128$).
<!--SR:!2026-08-03,3,250-->

What are the decimal ASCII values for `'0'`, `'A'`, and `'a'`? :: `'0'` = 48, `'A'` = 65, `'a'` = 97.
