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

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide 5.1-5.4)
> - 5.1 OS need, evolution, functions, classification
> - 5.2 File/directory management, allocation, defrag, formatting
> - 5.3 Process management, interrupts, states, PCB, context switch, schedulers
> - 5.4 Memory management (MMU, paging, virtual memory) + I/O (drivers, spooling)

---

## 1. Role, Evolution & Key Functions of an Operating System

An **Operating System (OS)** is system software that provides a virtual machine (hides hardware), manages resources (tracks/grants permissions), and executes applications. Interface between hardware and user/applications.

### Evolution

1. **No OS (1940s-50s)**: serial processing, single user, direct hardware via lights/switches. Idle during I/O.
2. **Simple Batch**: jobs on magnetic tape, run one-by-one, output to tape then print. No direct hardware access, uniprogramming, high response time.
3. **Multiprogrammed Batch (3rd gen)**: memory partitioned for multiple programs; when one waits for I/O, CPU switches. Keeps CPU ~100% busy. Core of modern OS.
4. **Time-Sharing**: minimise response time, context switching, illusion of concurrent execution, quick response.

### Core OS Functions:
1. **Providing interfaces / abstractions**: directories, files, data to user.
2. **Process Management**: creating, scheduling, terminating processes; CPU allocation (traffic controller).
3. **Resource Management**: memory, I/O devices, storage.
4. **Security & Protection**: authentication, permissions, resource protection.
5. **Device / IO Management**: via Device Drivers, spooling.

## 2. Types of Operating Systems

NIE classifies by **users** and **tasks**:

- **By users**: Single-user (one at a time) vs Multi-user (many at same/different time).
- **By tasks**: Single-task (one program) vs Multi-task (many programs).
- **Single user – single task**: one user, one task (e.g. MS-DOS).
- **Single user – multi task**: one user, many programs (e.g. Windows, Linux desktop).
- **Multi user – multi task**: many users concurrently (e.g. Unix server).
- **Multi-threading**: thread = subprocess; parallel sub-process execution for performance.
- **Real-Time OS (RTOS)**: precise, predictable response; costly downtime / safety (medical, missile).
- **Time-Sharing**: CPU time shared among users/apps; quick response, less idle. Distinct from multiprogramming (which maximises CPU use, not interactivity).

> [!INFO] Multiprogramming vs Time-Sharing
> Multiprogramming keeps many programs in memory to avoid CPU idle. Time-sharing rapidly switches to give interactive response. multiprogramming needs scheduling; time-sharing needs context switching.

---
## 3. Process Management & CPU Scheduling

A **Process** is a program in execution. A program may have many processes. Needs: PID, code, data, context (PC, priority, I/O state).

- **Types**: I/O-bound (much I/O) vs CPU-bound (much computation).
- **Creation reasons**: new batch job, user starts program, OS service, running program spawns another.
- **OS tasks at creation**: assign PID, allocate PCB, allocate memory/I/O, set state to Ready, queue it.
- **Termination reasons**: normal exit, time-limit exceeded, resource unavailable, execution/memory error, OS/parent request, parent terminated. OS reclaims resources.
- **Program vs Process**: program = static code on disk; process = dynamic execution with PCB, state, resources.

### Interrupts & Handling

**Interrupt** = event altering execution sequence (timer expiry, OS call, I/O completion). Asynchronous, unpredictable. Example: disk signals completion.

Handling: CPU is slower than I/O wait, so OS saves current process state (in PCB), runs another process. On I/O done, device interrupts, OS restores original process.

> [!INFO] Deep Dive Note
> For PCB fields, 5-state + 7-state diagrams, long/medium/short schedulers, and FCFS/SJF/RR worked examples, read: [[Subtopics/OS Process & Memory Management|OS Process & Memory Management Guide]].

### States & Transitions

Syllabus expects **seven-state model** (suspended states for swapping):

`New` -> `Ready` <-> `Running` -> `Terminated`, plus `Running` -> `Waiting/Blocked` -> `Ready`, plus `Suspended Ready / Suspended Blocked` for swapped-out processes.

Simplified 5-state: `New` $\rightarrow$ `Ready` $\rightleftarrows$ `Running` $\rightarrow$ `Terminated` (or `Running` $\rightarrow$ `Waiting` $\rightarrow$ `Ready`).

- **PCB (Process Control Block)**: per-process data — PID, state, program counter, CPU registers, memory info (page/segment tables, limits), I/O status (devices, open files), priority/pointer/accounting.
- **Context Switch**: save/restore registers + PCB to resume later. Pure overhead, affects performance. Enables multitasking.
- **Metrics**: Turnaround = completion-arrival; Waiting = turnaround-burst (time in ready queue); Response = first CPU-arrival; Throughput = processes / time.

### Process Schedulers (syllabus focus):

| Scheduler | Other name | Job |
|---|---|---|
| **Long-term** | Job scheduler | Admits programs to system, controls degree of multiprogramming, mixes CPU/I/O-bound. Slowest. |
| **Medium-term** | Swapping scheduler | Swaps processes main memory <-> secondary storage. Medium speed. |
| **Short-term** | CPU scheduler / dispatcher | Picks next Ready process for CPU. Fastest. |

### CPU Scheduling Algorithms (common examples):
- **FCFS (First-Come, First-Served)**: Non-preemptive; arrival order (convoy effect).
- **SJF (Shortest Job First)**: Preemptive or not; smallest burst first (optimal avg wait).
- **Round Robin (RR)**: Preemptive; fixed **Time Quantum** cyclically.
- Preemptive = OS can interrupt (RR); Non-preemptive = runs till block/exit (FCFS).

---
## 4. Memory Management & Virtual Memory

OS tracks every location, decides who gets how much/when, allocates/deallocates.

- **MMU (Memory Management Unit)**: hardware mapping virtual -> physical. Base + offset: e.g. base `10000` + user `100` = `10100`. User never sees real addresses.
- **Physical Memory**: actual RAM frames.
- **Paging**: logical = pages, physical = fixed frames (512B-8KB). Non-contiguous, page table translates. Internal fragmentation only.
- **Mapping**: OS maps logical to physical at allocation; MMU does runtime translation.
- **Segmentation**: variable logical segments (functions/arrays). External fragmentation.
- **Virtual Memory**: run programs larger than RAM. Pages/frames equal size, load on demand (**Demand Paging**), swap to disk. Goals: larger apps, partial load, higher multiprogramming degree, portability, sharing (read-only code).

### Fragmentation Quick Reference
| Type | Cause | Where It Happens | Solution |
|------|-------|------------------|----------|
| **Internal** | Fixed-size allocation units (blocks/frames/pages) larger than requested memory | **Paging**, Fixed Partitioning | Use smaller page/frame size (trade-off: larger page table) |
| **External** | Variable-size allocations leave scattered small free holes | **Segmentation**, Dynamic Partitioning, Contiguous Allocation | **Compaction** (relocate processes), or use **Paging** / Segmented Paging |

> [!TIP] Remember
> - **Internal** = *Inside* the allocated block (wasted space *within* a frame/page)
> - **External** = *Outside* / *between* allocated blocks (free memory fragmented into unusable holes)

### I/O Device Management
- **Device Driver**: software interface to hardware; depends on both hardware + OS. OS installs appropriate driver per peripheral.
- **Spooling (Simultaneous Peripheral Operations On-Line)**: buffer (memory/disk) holding I/O jobs for slow devices. OS spools, maintains buffer, allows parallel compute + I/O (read tape + write disk + print). Advantage: disk as large buffer, overlap I/O with CPU.

---
## 5. File System & User Interfaces

### Files & Directories

- **File**: named collection of related bytes. Logical view (user: records/pixels/bytes) vs Physical view (OS: possibly non-contiguous blocks).
- **Attributes**: name, type, owner, location, organization (sequential/indexed/random), permissions, dates (created/modified/accessed), size.
- **Types by extension**: executable `.exe`, text `.txt/.docx`, image `.bmp/.png/.jpeg`, video `.vob/.flv`, audio `.wav/.mp3`, compressed `.zip/.rar`.
- **File structure**: format OS understands (text = lines, object = machine blocks).
- **Hierarchy**: directories organise files logically.
- **File systems**: FAT (MS-DOS, File Allocation Table + root at fixed location, 2 copies) vs NTFS (recovery, Unicode, large disks, permissions/encryption). Unix uses indexed allocation.

### File Security

- Passwords + access privileges (read/write/delete per user).
- **Authentication** (OS duty): username/password, user attribute (fingerprint/retina/signature via input device).

### Storage Allocation (how OS gives disk blocks)

- **Contiguous**: adjacent blocks. Simple, easy access, but size must be known, hard to extend, external fragmentation.
- **Linked**: each block links to next (FAT example). No external fragmentation, grows easily, but many seeks.
- **Indexed**: index table of pointers created at file creation (UNIX example). No external fragmentation, ends at null pointer.

### Defrag & Formatting

- **Fragmentation**: scattered fragments -> unusable small free areas.
- **Defragmentation**: rearrange to combine free space.
- **Secondary storage**: non-volatile for source/exe/data/temp.
- **Disk formatting**: prepare device (low-level medium prep + partitioning to make visible + high-level new file system). High-level delete only removes links — data recoverable until overwritten.
- How the *media* retrieves a record: [[Subtopics/Sequential Direct & Random Access|Sequential vs Direct vs Random Access]].

### Interfaces
- **CLI (Command Line Interface)**: Text-based; low overhead, scripting (Linux shell, MS-DOS).
- **GUI (Graphical User Interface)**: WIMP (Windows, Icons, Menus, Pointer); user-friendly, higher demand.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is an Operating System? :: System software that acts as an interface between computer hardware and the user/applications, managing hardware resources and execution.

What are the 4 stages of OS evolution? :: No OS (serial), Simple Batch (tape), Multiprogrammed Batch (multi-program memory), Time-Sharing (context switch, interactive).

What are the NIE main functions of an OS? :: Providing interfaces/abstractions, process management, resource management, security and protection.

Classify OS by NIE users/tasks. :: Single-single, single-multi, multi-multi, plus multi-threading, real-time, time-sharing.

What is multiprogramming vs time-sharing? :: Multiprogramming maximises CPU use by many in-memory programs; time-sharing minimises response via rapid switching.

What is a file (logical vs physical view)? :: Named bytes; logical = user records/pixels, physical = OS possibly non-contiguous blocks.

List 4 file attributes. :: Name, type/extension, owner, location, organization, permissions, dates, size.

What is FAT vs NTFS? :: FAT = MS-DOS table at fixed location, 2 copies; NTFS = recovery, Unicode, large disks, permissions/encryption.

What are the 3 disk allocation methods with examples? :: Contiguous (adjacent, external frag), Linked (FAT, links, many seeks), Indexed (UNIX, index table).

What is defragmentation? :: Rearranging scattered fragments to eliminate unusable small free areas.

What are the 3 parts of disk formatting? :: Low-level prep, partitioning (visible to OS), high-level new file system.

What is a Process vs Program? :: Program is static code; process is program in execution with PID/PCB/state.

Name I/O-bound vs CPU-bound processes. :: I/O-bound needs much I/O; CPU-bound needs much computation.

What is an interrupt and handling? :: Async event altering execution (I/O done); OS saves state to PCB, runs another, restores on interrupt.

What is a Process Control Block (PCB)? :: A data structure in the OS containing all information about a specific process (PID, state, CPU registers, memory pointers).

Name the 5 states in the standard Process State Model. :: 1. New, 2. Ready, 3. Running, 4. Waiting (Blocked), 5. Terminated.

What extra states does the 7-state model add? :: Suspended Ready and Suspended Blocked for swapped-out processes.

Compare long, short, medium-term schedulers. :: Long (job, admit, slowest), short (CPU/dispatcher, fastest), medium (swapping, middle).

What is the difference between Preemptive and Non-Preemptive CPU scheduling? :: Preemptive scheduling allows the OS to forcibly interrupt a running process (e.g., Round Robin); Non-Preemptive scheduling lets a process run until it voluntarily yields or terminates (e.g., FCFS).

Define turnaround, waiting, response, throughput. :: Turnaround completion-arrival; waiting in ready queue; response first CPU-arrival; throughput procs/time.

What is a context switch? :: Saving/restoring CPU registers + PCB to share CPU; pure overhead.

What is Paging in memory management? :: A memory management scheme that divides logical memory into fixed-size Pages and physical memory into fixed-size Frames.

What is the MMU base-register example? :: Base 10000 + user 100 = physical 10100; user never sees real address.

What is Virtual Memory? :: A technique that allows a computer to execute processes larger than physical RAM by storing portions of data on secondary storage and loading pages on demand.

What is Page Fault? :: An interrupt raised when a program accesses a page that is not currently loaded into physical RAM.

What is spooling and a device driver? :: Spooling = simultaneous peripheral buffer for slow I/O overlap; driver = software interface depending on hardware+OS.
