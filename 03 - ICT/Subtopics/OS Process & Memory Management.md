---
title: OS Process & Memory Management
subject: AL ICT
subtopic: Operating Systems
tags:
  - AL-ICT
  - Subtopic
  - ProcessManagement
  - Scheduling
  - MemoryManagement
  - Paging
---
# :LiSettings: Subtopic: OS Process & Memory Management

> [!ABSTRACT] Core Focus
> Process Control Block (PCB), 5-state process transition model, CPU scheduling algorithms (Gantt charts), Paging, Segmentation, and Virtual Memory page faults.

---
## 1. Process Control Block (PCB)

The OS stores information about each active process in a **Process Control Block (PCB)** containing:
- **Process ID (PID)**
- **Process State** (New, Ready, Running, Waiting, Terminated)
- **Program Counter (PC)**: Next instruction address
- **CPU Registers** (Accumulators, index registers)
- **Memory Allocation Pointers** (Page tables, segment tables)
- **I/O Status Information** (Allocated devices, open files)

---
## 2. Process 5-State Transition Diagram

``` mermaid
stateDiagram-v2
    [*] --> New
    New --> Ready: Admitted
    
    Ready --> Running: Scheduler Dispatch
    Running --> Terminated: Exit
    
    Running --> Ready: Interrupt / Quantum Expired
    Running --> Waiting: I/O or Event Wait
    Waiting --> Ready: I/O or Event Completion
    
    Terminated --> [*]
```

---
## 3. CPU Scheduling Algorithms & Gantt Chart Example

Consider processes $P_1$ (Burst: 6ms), $P_2$ (Burst: 2ms), $P_3$ (Burst: 1ms) arriving at time $t=0$.

### A. FCFS (First-Come First-Served):
Gantt Chart: 
```mermaid
gantt
    title FCFS CPU Scheduling
    dateFormat X
    axisFormat %s ms
    section Tasks
    P1 : active, p1, 0, 6
    P2 : p2, after p1, 8
    P3 : p3, after p2, 9
```
- Waiting Time: $P_1 = 0$, $P_2 = 6$, $P_3 = 8$.
- **Average Waiting Time**: $(0 + 6 + 8) / 3 = 4.67\text{ ms}$.

### B. SJF (Shortest Job First):
Gantt Chart: 
``` mermaid
gantt
    title SJF CPU Scheduling
    dateFormat X
    axisFormat %s ms
    section Tasks
    P3 : active, p3, 0, 1
    P2 : p2, after p3, 3
    P1 : p1, after p2, 9
```
- Waiting Time: $P_3 = 0$, $P_2 = 1$, $P_1 = 3$.
- **Average Waiting Time**: $(0 + 1 + 3) / 3 = 1.33\text{ ms}$.

---
## 4. CPU Scheduling Algorithms (Continued)

### C. Round Robin (RR) — Quantum = 2ms:
Gantt Chart:
``` mermaid
gantt
    title Round Robin CPU Scheduling (q=2ms)
    dateFormat X
    axisFormat %s ms
    section Tasks
    P1 : active, p1_1, 0, 2
    P2 : p2_1, after p1_1, 4
    P3 : p3_1, after p2_1, 5
    P1 : p1_2, after p3_1, 7
    P1 : p1_3, after p1_2, 9
```
- Waiting Time: $P_1 = 3$, $P_2 = 2$, $P_3 = 4$.
- **Average Waiting Time**: $(3 + 2 + 4) / 3 = 3.00\text{ ms}$.

### D. Priority Scheduling (Lower number = Higher priority):
Assume $P_1$ (Priority 3), $P_2$ (Priority 1), $P_3$ (Priority 2).
Gantt Chart:
``` mermaid
gantt
    title Priority CPU Scheduling
    dateFormat X
    axisFormat %s ms
    section Tasks
    P2 : active, p2, 0, 2
    P3 : p3, after p2, 3
    P1 : p1, after p3, 9
```
- Waiting Time: $P_2 = 0$, $P_3 = 2$, $P_1 = 3$.
- **Average Waiting Time**: $(0 + 2 + 3) / 3 = 1.67\text{ ms}$.

### E. Key Metrics:
| Metric | Formula |
|--------|---------|
| **Turnaround Time** | Completion Time - Arrival Time |
| **Waiting Time** | Turnaround Time - Burst Time |
| **Response Time** | First CPU Start - Arrival Time |

### F. Preemptive vs Non-Preemptive:
- **Preemptive**: OS can interrupt running process (RR, Preemptive SJF/Priority).
- **Non-Preemptive**: Process runs to completion/block (FCFS, Non-preemptive SJF/Priority).

---
## 5. Process Synchronization

### Critical Section Problem:
Requirements: **Mutual Exclusion**, **Progress**, **Bounded Waiting**.

### Synchronization Tools:
- **Mutex Lock**: Binary lock (acquire/release).
- **Semaphore**: Integer variable with `wait()` (P) and `signal()` (V) operations.
  - *Counting Semaphore*: Multiple resources.
  - *Binary Semaphore*: Mutex equivalent (0 or 1).
- **Monitor**: High-level construct with condition variables (`wait`, `signal`).

### Classic Problems:
- **Producer-Consumer** (Bounded Buffer)
- **Readers-Writers**
- **Dining Philosophers**

---
## 6. Deadlocks

### Necessary Conditions (Coffman):
1. **Mutual Exclusion**
2. **Hold and Wait**
3. **No Preemption**
4. **Circular Wait**

### Handling Strategies:
- **Prevention**: Negate one condition (e.g., request all resources at once).
- **Avoidance**: Banker's Algorithm (safe state detection).
- **Detection & Recovery**: Resource-allocation graph + rollback/kill.
- **Ignorance**: Ostrich algorithm (most OSs).

---
## 7. Memory Management

### Memory Allocation Schemes:
| Scheme | Description | Fragmentation |
|--------|-------------|---------------|
| **Contiguous** | Single partition per process | External |
| **Fixed Partitioning** | Pre-defined partitions | Internal |
| **Dynamic Partitioning** | Partitions created at load time | External |
| **Paging** | Fixed-size pages/frames | Internal only |
| **Segmentation** | Variable-size segments (logical units) | External |
| **Segmented Paging** | Segments divided into pages | Internal only |

### Allocation Algorithms (Dynamic Partitioning):
- **First-Fit**: First hole large enough.
- **Best-Fit**: Smallest sufficient hole.
- **Worst-Fit**: Largest hole.

### Fragmentation:
- **Internal**: Wasted space within allocated block (Paging).
- **External**: Free memory scattered in small blocks (Segmentation, Dynamic Partitioning).
- **Compaction**: Shuffle memory to combine free space (requires dynamic relocation).

### Paging Architecture:
Logical address divided into **Page Number ($p$)** and **Page Offset ($d$)**.
``` mermaid
flowchart LR
    subgraph Logical Address
        p[Page Number p]
        d1[Offset d]
    end

    p --> PT[Page Table]
    PT --> f[Frame Number f]

    subgraph Physical Address
        f
        d2[Offset d]
    end
```

---
## 8. Segmentation

Logical address = **Segment Number ($s$)** + **Offset ($d$)**.
``` mermaid
flowchart LR
    subgraph Logical Address
        s[Segment Number s]
        d1[Offset d]
    end

    s --> ST[Segment Table]
    ST --> base[Base Address]
    ST --> limit[Limit/Length]

    base --> PA((Physical Address))
    d1 --> PA
    PA --> calc[Base + Offset]
```
- Segment Table entry: **Base** (start physical address) + **Limit** (length).
- Protection bits: Read/Write/Execute per segment.
- Supports sharing (code segments) and dynamic growth (stack/heap).

---
## 9. Virtual Memory

### Demand Paging (recap):
- Pages loaded only when needed.
- **Page Fault** rate critical for performance.

### Page Replacement Algorithms:
Reference string: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5 (3 frames)

| Algorithm | Page Faults | Description |
|-----------|-------------|-------------|
| **FIFO** | 9 | Replace oldest page |
| **Optimal (OPT)** | 7 | Replace page used farthest in future |
| **LRU** | 8 | Replace least recently used |
| **Clock (Second Chance)** | ~8 | FIFO with reference bit |

### Belady's Anomaly:
FIFO can have **more page faults with more frames**.

### Thrashing:
- Process spends more time paging than executing.
- Cause: **Sum of working sets > Physical memory**.
- Solution: **Working Set Model**, **Page Fault Frequency (PFF)** control, **Swap out** processes.

### Working Set Model:
- Set of pages referenced in last $\Delta$ time window.
- Keep working set in memory to prevent thrashing.

---
## 10. Summary Cheat Sheet

| Topic | Key Points |
|-------|------------|
| **PCB** | PID, State, PC, Registers, Memory ptrs, I/O info |
| **5 States** | New $\leftrightarrow$ Ready $\leftrightarrow$ Running $\leftrightarrow$ Waiting $\rightarrow$ Terminated |
| **Scheduling** | FCFS, SJF, RR, Priority (Preemptive/Non-preemptive) |
| **Metrics** | Turnaround, Waiting, Response Time |
| **Sync** | Mutex, Semaphore, Monitor; Producer-Consumer, Readers-Writers |
| **Deadlock** | 4 Conditions; Prevention, Avoidance (Banker's), Detection |
| **Memory** | Contiguous, Paging, Segmentation, Segmented Paging |
| **Allocation** | First/Best/Worst Fit |
| **Virtual Mem** | Demand Paging, Page Fault, Replacement (FIFO, LRU, OPT), Thrashing |
| **Replacement** | LRU $\approx$ OPT; FIFO suffers Belady's Anomaly |