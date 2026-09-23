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
  - Flashcards
---
# :LiBrain: Subtopic: Von Neumann Architecture & Registers

> [!ABSTRACT] Core Focus
> Detailed breakdown of the **Von Neumann Architecture**, CPU internal registers, fetch-decode-execute machine cycle, and the **Von Neumann Bottleneck**.

---
## 1. Key Principles of Von Neumann Architecture

1. **Stored Program Concept**: Both instructions and data are stored together in the **same physical primary memory (RAM)**.
2. **Sequential Execution**: Instructions are fetched and executed sequentially one after another unless interrupted by branch instructions.
3. **Single System Bus**: Shared data and address bus for memory access.

``` mermaid
flowchart LR
    CPU[CPU<br/>CU + ALU + Registers] <--> BUS[System Bus<br/>Address / Data / Control]
    BUS <--> MEM[(Main Memory<br/>Instructions + Data)]
    BUS <--> IO[Input / Output]
```

- **Address bus**: one-way CPU -> memory/IO (carries location). Width = max addressable memory.
- **Data bus**: two-way (carries instruction/data). Width = word size.
- **Control bus**: one-way + two-way signals (Read, Write, Clock, Interrupt, Ready).

---
## 2. CPU Internal Registers

Registers are small, high-speed storage locations located directly inside the CPU:

- **Program Counter (PC)**: Holds the memory address of the **next instruction** to be fetched and executed. Automatically incremented after fetching.
- **Memory Address Register (MAR)**: Holds the memory address currently being read from or written to memory via the address bus.
- **Memory Data Register (MDR) / Memory Buffer Register (MBR)**: Holds the data or instruction fetched from memory or waiting to be written to memory via the data bus.
- **Instruction Register (IR)**: Holds the current instruction while it is being decoded by the Control Unit.
- **Accumulator (ACC)**: Holds the intermediate arithmetic and logical results produced by the ALU.
- **Status / Flag register** (helper): Zero, Carry, Negative flags from ALU — CU uses them for branches.

| Register | Owned by | Job in one line |
|---|---|---|
| PC | CU | Tracks next instruction |
| MAR | CU / bus interface | Puts address on address bus |
| MDR | CU / bus interface | Holds data on data bus |
| IR | CU | Holds instruction being decoded |
| ACC | ALU | Holds ALU result |
| Flags | ALU -> CU | Tells CU what happened |

---
## 3. The Fetch-Decode-Execute Machine Cycle

``` mermaid
flowchart LR
    A[Fetch Instruction] --> B[Decode Instruction]
    B --> C[Execute Instruction]
    C --> D[Store Result]
    D -->|Next Instruction| A
```

### Who does what:

| Stage | Boss | Workers | What happens |
|---|---|---|---|
| **Fetch** | **Control Unit** | PC, MAR, MDR, IR + all 3 buses | Get next instruction from RAM into IR, bump PC. No ALU work. |
| **Decode** | **Control Unit** (decoder) | IR | Split opcode vs operands, decide which circuits/registers are needed. |
| **Execute** | **ALU** directed by **CU** | ALU, ACC, Flags, registers / RAM | Do the math/logic or move data. PC already points ahead. |
| **Store / Writeback** | **Control Unit** | ACC, MDR, MAR, RAM | Write ALU result to ACC or RAM. Then loop. |

Clock synchronises every micro-step. One machine cycle = Fetch + Decode + Execute (+ Store).

### Detailed Steps:
1. **Fetch Step (CU + PC/MAR/MDR/IR)**:
   - PC value is copied to MAR (`MAR <- PC`).
   - Control Unit sends a Read command on the Control Bus.
   - Instruction from memory location specified by MAR is loaded into MDR via Data Bus (`MDR <- Memory[MAR]`).
   - Instruction is copied from MDR to IR (`IR <- MDR`).
   - PC is incremented to point to the next instruction (`PC <- PC + 1`).
2. **Decode Step (CU only)**:
   - Control Unit decodes the opcode stored in IR.
   - CU identifies operands (registers, memory address, immediate value) and selects data paths.
3. **Execute Step (ALU led by CU)**:
   - ALU executes opcode using operands stored in registers or memory.
   - CU supplies control signals; ALU sets Flags; result goes to ACC (or temp register).
   - For jumps: CU loads new address into PC instead of sequential increment.
4. **Store / Writeback Step (CU + MDR/MAR)**:
   - Results are written back to Accumulator (ACC) or RAM (`MAR <- dest`, `MDR <- ACC`, Write command).
   - Cycle repeats from Fetch.

> [!TIP] Exam line
> Fetch = CU moves instruction RAM -> IR. Decode = CU interprets IR. Execute = ALU computes. Store = CU writes back. If a question asks "role of CU vs ALU": CU never computes, ALU never fetches.

---
## 4. The Von Neumann Bottleneck

> [!WARNING] The Von Neumann Bottleneck
> Because data and instructions share the **same system bus**, the CPU cannot fetch an instruction AND read/write data at the same time. The speed of data transfer between CPU and RAM limits execution speed.
>
> **Solutions**: Modern CPUs use **Cache Memory (L1, L2, L3)** and **Harvard Architecture** principles (separate instruction and data caches).

Suggested extras worth knowing:
- **Von Neumann vs Harvard**: Von Neumann = one memory + one bus (simple, cheap, bottleneck). Harvard = separate instruction + data memories/buses (faster, complex, used in microcontrollers, plus L1I/L1D caches are Harvard-style).
- **Cache**: tiny fast SRAM next to CPU holding recent instructions/data to avoid bus trips.
- **Pipelining** (idea only): overlap Fetch of instruction N+1 with Execute of N — still Von Neumann, just hides the bottleneck.
- Common trap: MAR/MDR are *not* general-purpose — they are the bus doorway. PC/IR/ACC never touch the bus directly.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the stored program concept? :: Instructions and data share the same primary memory (RAM) and are executed sequentially.

Name the 3 buses and directions. :: Address (CPU->memory, one-way), Data (two-way), Control (commands/interrupts).

What does the PC hold and when does it change? :: Address of next instruction; incremented after Fetch (or overwritten on jump).

What do MAR, MDR, IR, ACC hold? :: MAR = address on bus; MDR = data on bus; IR = current instruction being decoded; ACC = ALU result.

Who runs each stage of Fetch-Decode-Execute-Store? :: Fetch = CU + PC/MAR/MDR/IR; Decode = CU; Execute = ALU led by CU; Store = CU + ACC/MDR/MAR.

Does the ALU ever fetch from RAM? :: No. CU fetches via MAR/MDR into IR; ALU only computes when CU feeds it operands.

What is the Von Neumann Bottleneck? :: Single shared bus means CPU cannot fetch instruction and access data simultaneously; bus speed limits CPU.

Name two cures for the bottleneck. :: Cache (L1/L2/L3) and Harvard-style separate instruction/data paths.

Von Neumann vs Harvard in one line? :: Von Neumann = one memory/bus for all; Harvard = separate instruction and data memories/buses.
