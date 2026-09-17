---
title: Von Neumann Architecture & Computer Registers
subject: AL ICT
subtopic: Computer Architecture
tags:
  - AL-ICT
  - Subtopic
  - VonNeumann
  - CPU
  - Registers
---
# :LiBrain: Subtopic: Von Neumann Architecture & Registers

> [!ABSTRACT] Core Focus
> Detailed breakdown of the **Von Neumann Architecture**, CPU internal registers, fetch-decode-execute machine cycle, and the **Von Neumann Bottleneck**.

---
## 1. Key Principles of Von Neumann Architecture

1. **Stored Program Concept**: Both instructions and data are stored together in the **same physical primary memory (RAM)**.
2. **Sequential Execution**: Instructions are fetched and executed sequentially one after another unless interrupted by branch instructions.
3. **Single System Bus**: Shared data and address bus for memory access.

---
## 2. CPU Internal Registers

Registers are small, high-speed storage locations located directly inside the CPU:

- **Program Counter (PC)**: Holds the memory address of the **next instruction** to be fetched and executed. Automatically incremented after fetching.
- **Memory Address Register (MAR)**: Holds the memory address currently being read from or written to memory via the address bus.
- **Memory Data Register (MDR) / Memory Buffer Register (MBR)**: Holds the data or instruction fetched from memory or waiting to be written to memory via the data bus.
- **Instruction Register (IR)**: Holds the current instruction while it is being decoded by the Control Unit.
- **Accumulator (ACC)**: Holds the intermediate arithmetic and logical results produced by the ALU.

---
## 3. The Fetch-Decode-Execute Machine Cycle

``` mermaid
flowchart LR
    A[Fetch Instruction] --> B[Decode Instruction]
    B --> C[Execute Instruction]
    C --> D[Store Result]
    D -->|Next Instruction| A
```

### Detailed Steps:
1. **Fetch Step**:
   - PC value is copied to MAR (`MAR <- PC`).
   - Control Unit sends a Read command on the Control Bus.
   - Instruction from memory location specified by MAR is loaded into MDR via Data Bus (`MDR <- Memory[MAR]`).
   - Instruction is copied from MDR to IR (`IR <- MDR`).
   - PC is incremented to point to the next instruction (`PC <- PC + 1`).
2. **Decode Step**:
   - Control Unit decodes the opcode stored in IR.
3. **Execute Step**:
   - ALU executes opcode using operands stored in registers or memory.
4. **Store / Writeback Step**:
   - Results are written back to Accumulator (ACC) or RAM.

---
## 4. The Von Neumann Bottleneck

> [!WARNING] The Von Neumann Bottleneck
> Because data and instructions share the **same system bus**, the CPU cannot fetch an instruction AND read/write data at the same time. The speed of data transfer between CPU and RAM limits execution speed.
> 
> **Solutions**: Modern CPUs use **Cache Memory (L1, L2, L3)** and **Harvard Architecture** principles (separate instruction and data caches).