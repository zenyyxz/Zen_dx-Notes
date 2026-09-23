---
title: Lesson 05 - Operating Systems
subject: AL ICT
unit: 05
competency: Uses operating systems to manage the functionality of computers
tags:
  - AL-ICT
  - Lesson-05
  - OperatingSystem
  - ProcessManagement
  - MemoryManagement
  - Flashcards
---
# :LiBook: Lesson 05: Operating Systems

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Need for OS & Key Functions
> - Types of Operating Systems
> - Process Management & State Transition Diagram
> - CPU Scheduling Algorithms (FCFS, SJF, Round Robin)
> - Memory Management (Paging, Segmentation, Virtual Memory)
> - File Management & User Interfaces (CLI vs GUI)

---
## 1. Role & Key Functions of an Operating System

An **Operating System (OS)** is system software that acts as an interface between computer hardware and the user/application software.

### Core OS Functions:
1. **Process Management**: Creating, scheduling, and terminating processes; CPU allocation.
2. **Memory Management**: Allocation/deallocation of RAM; virtual memory management.
3. **File Management**: Organizing directories, access control, file allocation.
4. **Device / IO Management**: Managing hardware devices via Device Drivers.
5. **Security & Protection**: User authentication, file permissions, resource protection.

---
## 2. Types of Operating Systems

- **Batch OS**: Jobs with similar needs are grouped and executed sequentially without interactive user intervention.
- **Multiprogramming OS**: Keeps multiple programs in main memory simultaneously to maximize CPU utilization.
- **Time-Sharing / Multitasking OS**: CPU switches rapidly between multiple tasks using time slots (time quanta), providing interactive multi-user experience.
- **Real-Time OS (RTOS)**: Guarantees processing within strict time constraints (e.g., medical devices, missile control).
- **Multi-User OS**: Allows multiple users to access system resources concurrently.

---
## 3. Process Management & CPU Scheduling

A **Process** is a program in execution.

> [!INFO] Deep Dive Note
> For PCB fields, 5-state process transitions, and step-by-step CPU scheduling examples, read: [[Subtopics/OS Process & Memory Management|OS Process & Memory Management Guide]].

`New` $\rightarrow$ `Ready` $\rightleftarrows$ `Running` $\rightarrow$ `Terminated` (or `Running` $\rightarrow$ `Waiting/Blocked` $\rightarrow$ `Ready`).

### CPU Scheduling Algorithms:
- **FCFS (First-Come, First-Served)**: Non-preemptive; jobs executed in arrival order (convoy effect).
- **SJF (Shortest Job First)**: Non-preemptive or preemptive; selects task with smallest execution time (optimal average wait time).
- **Round Robin (RR)**: Preemptive; allocates fixed **Time Quantum** to each process in cyclic order.

---
## 4. Memory Management & Virtual Memory

### Fragmentation Quick Reference
| Type | Cause | Where It Happens | Solution |
|------|-------|------------------|----------|
| **Internal** | Fixed-size allocation units (blocks/frames/pages) larger than requested memory | **Paging**, Fixed Partitioning | Use smaller page/frame size (trade-off: larger page table) |
| **External** | Variable-size allocations leave scattered small free holes | **Segmentation**, Dynamic Partitioning, Contiguous Allocation | **Compaction** (relocate processes), or use **Paging** / Segmented Paging |

> [!TIP] Remember
> - **Internal** = *Inside* the allocated block (wasted space *within* a frame/page)
> - **External** = *Outside* / *between* allocated blocks (free memory fragmented into unusable holes)

- **Contiguous Allocation**: Fixed or dynamic partitioning (suffers from internal/external fragmentation).
- **Paging**: Non-contiguous allocation. Divides physical memory into fixed-size **Frames** and logical memory into same-sized **Pages**. Uses a **Page Table**. Eliminates external fragmentation (only internal).
- **Segmentation**: Divides memory into variable-length logical segments based on user programs (functions, arrays). Suffers from external fragmentation.
- **Virtual Memory**: Technique allowing execution of processes larger than physical RAM by loading pages into RAM on demand (**Demand Paging**) and swapping inactive pages to secondary storage (swap space).

---
## 5. File System & User Interfaces

- **File Management**: File naming, extensions, access attributes, hierarchical directory tree structures. How the *media* retrieves a record: [[Subtopics/Sequential Direct & Random Access|Sequential vs Direct vs Random Access]].
- **CLI (Command Line Interface)**: Text-based interface; low resource overhead, powerful for scripting (e.g., Linux shell, MS-DOS).
- **GUI (Graphical User Interface)**: Uses WIMP (Windows, Icons, Menus, Pointer); user-friendly, higher resource demand.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is an Operating System? :: System software that acts as an interface between computer hardware and the user/applications, managing hardware resources and execution.

What is a Process Control Block (PCB)? :: A data structure in the OS containing all information about a specific process (PID, state, CPU registers, memory pointers).

Name the 5 states in the standard Process State Model. :: 1. New, 2. Ready, 3. Running, 4. Waiting (Blocked), 5. Terminated.
<!--SR:!2026-08-04,4,270-->

What is the difference between Preemptive and Non-Preemptive CPU scheduling? :: Preemptive scheduling allows the OS to forcibly interrupt a running process (e.g., Round Robin); Non-Preemptive scheduling lets a process run until it voluntarily yields or terminates (e.g., FCFS).
<!--SR:!2026-08-01,1,230-->

What is Paging in memory management? :: A memory management scheme that divides logical memory into fixed-size Pages and physical memory into fixed-size Frames.
<!--SR:!2026-09-08,10,270-->

What is Virtual Memory? :: A technique that allows a computer to execute processes larger than physical RAM by storing portions of data on secondary storage and loading pages on demand.
<!--SR:!2026-10-02,15,290-->

What is Page Fault? :: An interrupt raised when a program accesses a page that is not currently loaded into physical RAM.
<!--SR:!2026-08-03,3,250-->