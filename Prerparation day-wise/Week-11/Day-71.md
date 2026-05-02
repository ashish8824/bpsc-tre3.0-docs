# 📅 BPSC TRE 4.0 — DAY 70: SEGMENTATION + VIRTUAL MEMORY + COMPACTION
### Week 11 — Segmentation, Compaction, External Fragmentation, Virtual Memory, Thrashing, Buffer Registers
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — Segmentation, Compaction, Fragmentation Types, Virtual Memory, Thrashing, Buffer Registers
> - Afternoon (1 hr): GS — Geography: India's Water Resources (Rivers, Dams, Irrigation, Groundwater)
> - Evening (1.5 hrs): Solve all 50 MCQs
> - Night (30 min): Read the Night Revision Sheet

---

# PART 1: CS CONCEPT NOTES
## 📘 Memory Management — Segmentation, Compaction, Virtual Memory (Complete Deep Dive)

---

## 🔷 TOPIC 1: SEGMENTATION — What It Is and Why It Exists

```
THE PROBLEM PAGING DOESN'T SOLVE:
════════════════════════════════════════════════════════════════════

In paging, a process is divided into EQUAL-SIZED pages.
But a programmer thinks of a program in LOGICAL UNITS:
  → Code section (instructions)
  → Data section (variables, arrays)
  → Stack section (function calls, local variables)
  → Heap section (dynamic memory with new/malloc)
  → Symbol table, libraries, etc.

These logical units are NOT equal in size.
Paging breaks them arbitrarily — a page might contain part of
code and part of data, which is logically WRONG.

SEGMENTATION SOLVES THIS:
  → Divide memory into VARIABLE-SIZE logical units called SEGMENTS
  → Each segment = one logical unit (code, data, stack, heap)
  → Each segment has its own SIZE and BASE ADDRESS
  → The programmer/program sees memory in logical terms

════════════════════════════════════════════════════════════════════

DEFINITION:
  SEGMENTATION = A memory management technique that divides
                 a process into VARIABLE-SIZE logical segments
                 (code, data, stack, heap, symbol table, etc.)
                 based on the LOGICAL STRUCTURE of the program

KEY FACTS:
  → Page size = FIXED (always same for all pages)
  → Segment size = VARIABLE (each segment is different size)
  → Segmentation = closer to how a programmer views memory
  → Paging = closer to how hardware views memory
```

---

## 🔷 TOPIC 2: SEGMENT TABLE — How Segmentation Works

```
SEGMENT TABLE = per-process data structure maintained by OS
                Maps each segment number to its base address and limit

SEGMENT TABLE ENTRY STRUCTURE:
════════════════════════════════════════════════════════════════════

  ┌─────────────────┬────────────────┬──────────────────────────┐
  │ Segment Number  │  Base Address  │  Limit (Length/Size)     │
  └─────────────────┴────────────────┴──────────────────────────┘

  Base  = starting PHYSICAL address where segment begins in RAM
  Limit = SIZE of the segment (length in bytes)
          ← PYQ TRAP: "Segment base = STARTING ADDRESS in physical memory"

════════════════════════════════════════════════════════════════════

EXAMPLE SEGMENT TABLE:

  Segment │  Base Address  │  Limit (Size)
  ────────┼────────────────┼──────────────
     0    │    1400        │    400       ← code segment: 400 bytes at address 1400
     1    │    6300        │    100       ← data segment: 100 bytes at address 6300
     2    │    4300        │    400       ← stack segment: 400 bytes at address 4300
     3    │    3200        │    1100      ← heap segment: 1100 bytes at address 3200

NOTICE: Segments are at different physical addresses (1400, 6300, 4300, 3200)
        NOT consecutive — scattered in physical memory
        But each segment is CONTIGUOUS within itself

ADDRESS TRANSLATION IN SEGMENTATION:
════════════════════════════════════════════════════════════════════

  Logical Address = [Segment Number s | Offset d]

  Step 1: Use segment number s → look up Segment Table
  Step 2: Check: d < Limit? If YES → valid, continue. If NO → SEGMENT FAULT!
  Step 3: Physical Address = Base[s] + d

  ┌─────────────────────────────────────────────────────────────┐
  │  Logical Address: [Segment Number s | Offset d]             │
  │         ↓ (use s to index segment table)                    │
  │  Segment Table: s → Base Address b, Limit L                 │
  │         ↓ Check: d < L? (valid offset?)                     │
  │  Physical Address = b + d                                   │
  └─────────────────────────────────────────────────────────────┘

  SEGMENT FAULT = Access beyond segment boundary (d ≥ Limit)
                = OS raises an exception (protection violation)

════════════════════════════════════════════════════════════════════

WORKED EXAMPLE:
  Segment Table:
    Seg 0: Base = 219, Limit = 600
    Seg 1: Base = 2300, Limit = 14
    Seg 2: Base = 90, Limit = 100

  Q: Find physical address for logical address (1, 10):
    Segment 1: Base = 2300, Limit = 14
    Check: offset 10 < 14? YES (valid)
    Physical = 2300 + 10 = 2310

  Q: Find physical address for logical address (1, 20):
    Segment 1: Base = 2300, Limit = 14
    Check: offset 20 < 14? NO (20 ≥ 14 → SEGMENT FAULT!)
```

---

## 🔷 TOPIC 3: PAGING vs SEGMENTATION — MASTER COMPARISON

```
FEATURE              PAGING                      SEGMENTATION
────────────────────────────────────────────────────────────────────
Division unit        Fixed-size PAGES            Variable-size SEGMENTS
Size of units        ALL same size               Each segment different size
Based on             Physical convenience        Logical structure of program
Programmer view      No (transparent)            YES (matches programmer's view)
External frag        ELIMINATED (no ext. frag)   CAN OCCUR (variable sizes)
Internal frag        YES (last page partial)     NO (segments are exact size)
Lookup table         Page Table                  Segment Table
Table entry has      Frame Number                Base Address + Limit
Protection           Difficult (page cuts        Easy (per-segment permissions)
                     across logical units)
Sharing              Difficult                   Easy (share entire segment)
Address format       [Page number | Offset]      [Segment number | Offset]
Offset range         Fixed (page size - 1)       Variable (limit - 1)
Fault type           PAGE FAULT (valid bit = 0)  SEGMENT FAULT (offset ≥ limit)
PYQ TRAP             Segment base = STARTING     Page size = ALWAYS FIXED
                     ADDRESS in physical memory
────────────────────────────────────────────────────────────────────

COMBINED: SEGMENTED PAGING
  → Modern OS use BOTH together
  → Each segment is divided into pages
  → Combines logical organization (segmentation) + physical flexibility (paging)
  → Used in: Intel x86 architecture (originally), modern Linux/Windows
```

---

## 🔷 TOPIC 4: FRAGMENTATION — THE COMPLETE PICTURE

```
FRAGMENTATION = WASTED MEMORY
             = A PROBLEM (NOT a technique, NOT a solution!)
             ← DIRECT BPSC PYQ TRAP: "Fragmentation is a memory management TECHNIQUE"
             → WRONG! Fragmentation is a PROBLEM that memory management tries to SOLVE.

════════════════════════════════════════════════════════════════════

TYPE 1: INTERNAL FRAGMENTATION
════════════════════════════════════════════════════════════════════

DEFINITION: Wasted memory INSIDE an allocated block/page
            Memory is allocated but PARTIALLY UNUSED

WHEN DOES IT OCCUR?
  → Fixed-size allocation (paging, fixed partition allocation)
  → Process doesn't fill the entire allocated block

VISUAL EXAMPLE:
  Process needs 13KB, Page size = 4KB

  ┌────────────────────┐
  │ Page 0 = 4KB ████  │  ← fully used
  ├────────────────────┤
  │ Page 1 = 4KB ████  │  ← fully used
  ├────────────────────┤
  │ Page 2 = 4KB ████  │  ← fully used
  ├────────────────────┤
  │ Page 3 = 4KB       │
  │  [1KB █ | 3KB ░░░] │  ← 1KB used, 3KB WASTED = INTERNAL FRAGMENTATION
  └────────────────────┘

CAUSE:   Fixed-size page/partition allocation
FOUND:   PAGING, Fixed Partition Allocation
SOLUTION: Use SMALLER page/block sizes (reduces waste but increases table size)

MAXIMUM internal fragmentation per process = page_size - 1

════════════════════════════════════════════════════════════════════

TYPE 2: EXTERNAL FRAGMENTATION
════════════════════════════════════════════════════════════════════

DEFINITION: Free memory EXISTS but is SCATTERED in NON-CONTIGUOUS chunks
            A process can't load even though TOTAL free memory is sufficient

WHEN DOES IT OCCUR?
  → Variable-size allocation (segmentation, variable partition allocation)
  → Processes loaded and removed in different orders leave "holes"

VISUAL EXAMPLE:
  ┌─────────────────────────────────────────────────────┐
  │ [Process A: 20MB] [FREE: 10MB] [Process B: 30MB]    │
  │ [FREE: 15MB] [Process C: 25MB] [FREE: 8MB]          │
  └─────────────────────────────────────────────────────┘

  Total free = 10 + 15 + 8 = 33 MB
  Process D needs 25 MB of CONTIGUOUS memory → CANNOT LOAD!
  Even though 33 MB is free, no single block is 25 MB.

  These 3 "holes" are external fragmentation.

CAUSE:   Variable-size allocation (loads and removals create holes)
FOUND:   SEGMENTATION, Variable Partition Allocation, Contiguous Allocation
SOLUTION: COMPACTION (move processes together to merge all free space)
         Also: NON-CONTIGUOUS ALLOCATION (paging eliminates it)

════════════════════════════════════════════════════════════════════

FRAGMENTATION SUMMARY TABLE:

FEATURE            INTERNAL FRAG            EXTERNAL FRAG
───────────────────────────────────────────────────────────────────
Location           INSIDE allocated block   BETWEEN allocated blocks
Memory state       Allocated but unused     Free but non-contiguous
Cause              Fixed-size allocation    Variable-size allocation
Present in         Paging                   Segmentation
NOT present in     Segmentation             Paging
Solution           Smaller page size        Compaction / Paging
Both present in    Fixed partition          —
                   (internal per partition,
                    but also external between
                    partitions)
───────────────────────────────────────────────────────────────────

★ KEY PYQ TRAP: Fragmentation = PROBLEM (not a technique)
★ KEY PYQ TRAP: Paging = no external frag; Segmentation = no internal frag
```

---

## 🔷 TOPIC 5: COMPACTION — SOLUTION TO EXTERNAL FRAGMENTATION

```
COMPACTION = A memory management technique that RELOCATES
             all active processes in memory to ONE END,
             consolidating ALL free memory into a SINGLE
             LARGE CONTIGUOUS BLOCK

════════════════════════════════════════════════════════════════════

BEFORE COMPACTION:
  ┌─────────────────────────────────────────────────────┐
  │ [Process A] [FREE: 10MB] [Process B] [FREE: 15MB]   │
  │ [Process C] [FREE: 8MB]                             │
  └─────────────────────────────────────────────────────┘
  Total free = 33 MB (scattered in 3 holes)
  A 25 MB process CANNOT load.

AFTER COMPACTION:
  ┌─────────────────────────────────────────────────────┐
  │ [Process A] [Process B] [Process C] [FREE: 33MB]    │
  └─────────────────────────────────────────────────────┘
  All free memory merged into ONE block = 33 MB
  Now a 25 MB process CAN load!

════════════════════════════════════════════════════════════════════

COMPACTION KEY FACTS:
  ★ Compaction = solution to EXTERNAL fragmentation ← most tested
  ★ Compaction = shifts ALL processes → ONE contiguous block at one end
  ★ All free memory → consolidated into ONE SINGLE LARGE BLOCK ← exact PYQ phrase
  ★ Compaction does NOT solve internal fragmentation
  ★ Compaction is EXPENSIVE:
     → Must copy entire processes to new locations
     → Must update all base addresses (pointers/addresses change)
     → Takes CPU time and memory bandwidth
  ★ Requires DYNAMIC RELOCATION (base register updated during compaction)

WHY IS COMPACTION EXPENSIVE?
  → Imagine moving all furniture in a house to one room.
  → Every process must be PHYSICALLY COPIED to a new location in RAM.
  → All internal addresses (pointers, return addresses) must be adjusted.
  → While compaction runs, the system is essentially FROZEN.
  → That's why modern OS prefer PAGING (which naturally avoids ext. frag)
    over compaction (which is slow and costly).

COMPACTION vs PAGING (as solution to external fragmentation):
  ─────────────────────────────────────────────────────────────
  COMPACTION:  OS physically moves processes → slow, costly
  PAGING:      No movement needed → pages stored anywhere (non-contiguous)
               Solves external frag AUTOMATICALLY by design → preferred!
  ─────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 6: VIRTUAL MEMORY — COMPLETE EXPLANATION

```
THE PROBLEM:
  → A process may require MORE memory than physically available in RAM.
  → Without virtual memory: process simply CANNOT run if RAM is full.
  → With virtual memory: process CAN run even if not entirely in RAM!

════════════════════════════════════════════════════════════════════

DEFINITION:
  VIRTUAL MEMORY = A technique that allows execution of processes
                   that are NOT COMPLETELY LOADED in physical memory (RAM).
                   The OS uses secondary storage (disk) as an extension of RAM.

KEY INSIGHT:
  → At any given moment, a process only needs a SMALL PART of its code.
  → Example: An editing software has thousands of functions.
    When you type text, only the "text input" function is being executed.
    The "spell check", "print", "format" functions sit idle.
  → So keep only the CURRENTLY NEEDED pages in RAM.
  → Store the rest on DISK (swap space / page file).
  → Load from disk to RAM ONLY WHEN NEEDED (on page fault).

HOW VIRTUAL MEMORY WORKS:
════════════════════════════════════════════════════════════════════

VIRTUAL ADDRESS SPACE:
  ┌──────────────────────────────────┐
  │  Process Virtual Address Space   │
  │  (can be MUCH larger than RAM)   │
  │                                  │
  │  Page 0  ─────► Frame 3 (RAM)    │
  │  Page 1  ─────► Frame 7 (RAM)    │
  │  Page 2  ─────► ON DISK          │← valid bit = 0
  │  Page 3  ─────► Frame 1 (RAM)    │
  │  Page 4  ─────► ON DISK          │← valid bit = 0
  │  Page 5  ─────► ON DISK          │← valid bit = 0
  └──────────────────────────────────┘

  Only Pages 0, 1, 3 are in RAM.
  Pages 2, 4, 5 are on disk (swap space).
  If the process tries to access Page 2 → PAGE FAULT → OS loads it from disk.

SWAP SPACE:
  → A reserved area on disk that acts as overflow for RAM.
  → Pages evicted from RAM go to swap space.
  → Called: swap partition (Linux), page file/pagefile.sys (Windows).
  → Disk is 1,000,000× slower than RAM → too much swapping = THRASHING.

BENEFITS OF VIRTUAL MEMORY:
  1. Process size can EXCEED physical RAM size
  2. MORE processes can run simultaneously (each has partial pages in RAM)
  3. Programs don't need to manage memory manually
  4. Protection: each process has its own virtual address space

════════════════════════════════════════════════════════════════════

LOGICAL vs PHYSICAL vs VIRTUAL ADDRESS:

  LOGICAL ADDRESS  = Address generated by CPU for a running process
                   = Relative to process start (what the program sees)
  PHYSICAL ADDRESS = Actual RAM address (what the hardware sees)
  VIRTUAL ADDRESS  = Address in the virtual address space
                   = In most contexts, LOGICAL ADDRESS = VIRTUAL ADDRESS
                     (terms are used interchangeably in most OS textbooks)

  MMU (Memory Management Unit):
  = Hardware component that translates logical (virtual) addresses
    to physical addresses at runtime
  = Contains the TLB; performs page table lookups
```

---

## 🔷 TOPIC 7: THRASHING — THE MOST DANGEROUS VIRTUAL MEMORY PROBLEM

```
SETUP — WHAT LEADS TO THRASHING?
════════════════════════════════════════════════════════════════════

Normal working:
  → Process runs → occasionally gets page fault → OS loads page → continues.
  → This is normal demand paging — acceptable performance.

Too many processes / too little RAM:
  → OS tries to run many processes simultaneously.
  → Each process gets very few frames (not enough for its WORKING SET).
  → Process constantly generates page faults.
  → OS keeps loading pages from disk → evicting other pages → loading again.
  → Process spends MORE TIME HANDLING PAGE FAULTS than actually executing.

════════════════════════════════════════════════════════════════════

DEFINITION:
  THRASHING = A condition where a process (or the entire system) spends
              MORE TIME SWAPPING PAGES IN AND OUT OF MEMORY than
              actually executing useful instructions.
              = Excessive paging activity that drastically reduces performance.

CAUSE OF THRASHING:
  → Too many processes competing for too few physical memory frames
  → Each process's WORKING SET (pages it actively needs) doesn't fit in RAM
  → OS keeps evicting pages that are immediately needed again
  → Page fault rate becomes extremely high

VISUAL EFFECT ON CPU UTILIZATION:
  ════════════════════════════════════════════════════════════
  CPU                        THRASHING
  Utilization                ZONE
      │                    ╱╲
  100%│               ╱╲  ╱  ╲
      │          ╱╲  ╱   ╲╱   ╲
      │     ╱╲  ╱   ╲              ← CPU util DROPS sharply
      │    ╱   ╲╱                    (CPU waits for page I/O)
   0% └──────────────────────────►
      0    5    10   15   20      Number of processes

  As more processes added: CPU utilization first INCREASES (more work done)
  Then DECREASES sharply (processes spend all time on page faults)
  = This sudden drop = THRASHING ZONE

════════════════════════════════════════════════════════════════════

HOW TO PREVENT/DETECT THRASHING:
  1. WORKING SET MODEL:
     → Working Set = the set of pages a process needs at any given time
     → OS tracks working set of each process
     → Only run a process if its ENTIRE working set can be loaded in RAM
     → If total working set > available RAM → suspend some processes

  2. PAGE FAULT FREQUENCY (PFF):
     → Monitor page fault rate of each process
     → Too HIGH page fault rate → process needs more frames (give more)
     → Too LOW page fault rate → process has too many frames (take some away)
     → If can't give more frames → SUSPEND the process

  3. REDUCE MULTIPROGRAMMING:
     → Fewer processes simultaneously → each gets more frames
     → Reduces page fault rate → eliminates thrashing

  4. INCREASE RAM:
     → More physical memory → less swapping needed

THRASHING KEY FACTS (PYQ SUMMARY):
  ★ Thrashing = caused by EXCESSIVE PAGING ACTIVITY ← exact PYQ phrase
  ★ Thrashing = process spends MORE TIME paging THAN executing
  ★ Cause = too many processes, too few frames (working set doesn't fit)
  ★ Solution = Working Set Model OR Page Fault Frequency control
  ★ Thrashing was mentioned in Day 73 context too — same definition applies

════════════════════════════════════════════════════════════════════

PAGE REPLACEMENT ALGORITHMS (brief revision from Day 69):
  FIFO:   Replace page that entered memory FIRST (longest in memory)
          → Simple; suffers from Belady's Anomaly
  LRU:    Replace page that was LEAST RECENTLY USED
          → Better performance; no Belady's Anomaly; complex implementation
  OPT:    Replace page that will NOT be used for LONGEST TIME in future
          → Best performance; impossible to implement (needs future knowledge)
          → Used as benchmark to compare other algorithms
  CLOCK:  Approximate LRU using a reference bit and circular buffer
          → Used in many practical OS (Linux, Windows)
```

---

## 🔷 TOPIC 8: BUFFER REGISTERS — OVERLOOKED PYQ TOPIC

```
CONTEXT — SPEED MISMATCH PROBLEM:
════════════════════════════════════════════════════════════════════

Different hardware devices operate at VERY DIFFERENT speeds:
  CPU (GHz) >> RAM (hundreds of MHz) >> Disk (milliseconds) >> Network (seconds)

Example speed comparison:
  CPU processes instruction: 1 nanosecond (10⁻⁹ seconds)
  RAM access:                100 nanoseconds
  SSD access:                100,000 nanoseconds (0.1 ms)
  HDD access:                10,000,000 nanoseconds (10 ms)
  Keyboard input:            Seconds (human typing speed)

PROBLEM: If CPU must WAIT each time it sends data to a slow device, 
         the CPU is IDLE most of the time → WASTED performance.

════════════════════════════════════════════════════════════════════

DEFINITION:
  BUFFER REGISTER = A temporary storage area (memory) used to
                    HOLD DATA while it is being transferred between
                    two devices that operate at DIFFERENT SPEEDS.

  MAIN PURPOSE = Overcome the DIFFERENCE IN DATA TRANSFER SPEED
                 between two communicating devices
                 ← EXACT PYQ PHRASE — memorize this!

════════════════════════════════════════════════════════════════════

HOW IT WORKS:
  FAST DEVICE (CPU) → writes data to buffer (fast) → continues other work
  SLOW DEVICE (Disk) → reads from buffer at its own pace (slow)

  Without buffer:   CPU sends data → WAITS for slow device → CPU idle
  With buffer:      CPU sends data to buffer (fast) → CPU continues
                    Slow device reads from buffer independently

  ┌────────────────────────────────────────────────────┐
  │                                                    │
  │  CPU ──► writes to BUFFER REGISTER ──► reads ─► Disk│
  │  (fast)  (temporary storage)          (slow)       │
  │                                                    │
  │  CPU doesn't wait — it moves on after writing!    │
  └────────────────────────────────────────────────────┘

════════════════════════════════════════════════════════════════════

REAL-WORLD EXAMPLES:
  → Keyboard buffer: stores keystrokes while OS is busy; reads later
  → Printer buffer (spool): stores print job; printer reads at its pace
  → Network buffer: stores incoming packets; CPU processes when ready
  → Audio buffer: stores audio samples; speaker plays at steady rate
  → Disk buffer (disk cache): RAM that buffers disk reads/writes

BUFFER vs CACHE (IMPORTANT DISTINCTION):
  BUFFER:  Temporary storage for data IN TRANSIT between two devices
           Used ONCE — data flows through it from source to destination
           Purpose: overcome SPEED DIFFERENCE
           Example: pipe between two processes of different speeds

  CACHE:   Stores FREQUENTLY USED data for FASTER FUTURE ACCESS
           Data can be reused multiple times
           Purpose: avoid repeated slow access to original source
           Example: TLB (caches page table entries), CPU L1/L2/L3 cache

  ★ PYQ TRAP: Buffer registers = overcome DIFFERENCE IN DATA TRANSFER SPEED
             Do NOT say "buffer = cache" — they are DIFFERENT!

════════════════════════════════════════════════════════════════════

TYPES OF BUFFERING:
  Single Buffering:   One buffer used; producer fills → consumer empties
                      Simple but inefficient (one can't work while other does)

  Double Buffering:   Two buffers alternating
                      While consumer processes buffer 1, producer fills buffer 2
                      Better throughput; reduces idle time

  Circular Buffering: Multiple buffers in a ring
                      Used in audio, video streaming, I/O management
```

---

## 🔷 TOPIC 9: MEMORY MANAGEMENT TECHNIQUES — COMPLETE COMPARISON TABLE

```
ALL MEMORY MANAGEMENT TECHNIQUES — MASTER TABLE
════════════════════════════════════════════════════════════════════

TECHNIQUE        UNIT       FIXED/VAR  EXT. FRAG  INT. FRAG  MAIN BENEFIT
─────────────────────────────────────────────────────────────────────────────
Fixed Partition  Partition  Fixed      YES         YES         Simple
Variable Part.   Partition  Variable   YES         NO          Better fit
Paging           Page       Fixed      NO          YES         No ext. frag
Segmentation     Segment    Variable   YES         NO          Logical view
Seg + Paging     Segment    Both       NO          Small       Best of both
Virtual Memory   Page       Fixed      NO          YES         Larger process
─────────────────────────────────────────────────────────────────────────────

PROBLEM vs SOLUTION vs TECHNIQUE:
  FRAGMENTATION    = PROBLEM ← PYQ direct trap (never say "technique")
  COMPACTION       = SOLUTION (to external fragmentation)
  PAGING           = TECHNIQUE (also solves external fragmentation)
  VIRTUAL MEMORY   = TECHNIQUE (extends effective memory)
  THRASHING        = PROBLEM (result of too much virtual memory use)

════════════════════════════════════════════════════════════════════

HOW VARIOUS TECHNIQUES RELATE:
  ┌─────────────────────────────────────────────────────────────┐
  │                                                             │
  │  External Fragmentation (PROBLEM)                           │
  │    → Solved by: Compaction (expensive)                      │
  │    → Prevented by: Paging (preferred)                       │
  │                                                             │
  │  Internal Fragmentation (PROBLEM)                           │
  │    → Reduced by: Smaller page/block size                    │
  │    → Eliminated by: Segmentation (exact-size segments)      │
  │                                                             │
  │  Process too large for RAM (PROBLEM)                        │
  │    → Solved by: Virtual Memory (demand paging)              │
  │                                                             │
  │  Virtual Memory used too aggressively → Thrashing (PROBLEM) │
  │    → Solved by: Working Set Model / Page Fault Frequency    │
  │                                                             │
  └─────────────────────────────────────────────────────────────┘
```

---

## 🔷 TOPIC 10: MEMORY MAPPED I/O vs I/O MAPPED I/O (BONUS PYQ TOPIC)

```
MEMORY-MAPPED I/O:
  → I/O device registers share the SAME address space as main memory
  → CPU uses normal LOAD/STORE instructions to access I/O devices
  → No special I/O instructions needed
  → Simpler programming but uses some of the memory address space
  ← TRE 1.0 PYQ: "Memory-mapped I/O = I/O and memory SHARE SAME address space"

I/O MAPPED I/O (PORT-MAPPED I/O):
  → I/O devices have a SEPARATE address space from memory
  → CPU uses special I/O instructions (IN/OUT) to access devices
  → Memory addresses are NOT used up by I/O device registers
  → More complex but keeps memory address space clean

COMPARISON:
  ─────────────────────────────────────────────────────────────
  FEATURE             MEMORY-MAPPED I/O      I/O MAPPED I/O
  Address space       SHARED (memory + I/O)  SEPARATE for I/O
  CPU instructions    Normal LOAD/STORE       Special IN/OUT
  Address space use   Some used by I/O       Memory space clean
  Example             Most modern systems     x86 legacy I/O ports
  ─────────────────────────────────────────────────────────────
  ★ PYQ EXACT PHRASE: Memory-mapped I/O = I/O and memory SHARE SAME address space
```

---

## 📊 CS DAY 70 — MASTER TRAP TABLE

```
TOPIC                    CORRECT FACT                         COMMON TRAP
──────────────────────────────────────────────────────────────────────────────
Fragmentation            It is a PROBLEM                      Students say it's a
                         NOT a technique or solution          "memory management technique"

Compaction               Shifts ALL processes to ONE end      Students say compaction
                         → ALL free memory in ONE BLOCK        "fragments memory" or
                         = solution to EXTERNAL fragmentation  "splits memory"

External fragmentation   Free memory is SCATTERED             Students confuse with
                         Process CANNOT load despite enough    internal fragmentation
                         total free memory

Internal fragmentation   Wasted space INSIDE allocated block  Students confuse with
                         Last page not fully used             external fragmentation

Paging vs Segmentation   Paging = NO ext. frag, YES int. frag Both have fragmentation
                         Segmentation = YES ext. frag, NO int.

Segment base address     STARTING PHYSICAL ADDRESS of segment Students say "segment size"
                         ← direct PYQ exam phrase

Segment Limit            SIZE of the segment (NOT address)    Students confuse limit
                                                              with a physical address

Virtual memory           Allows process LARGER than RAM       Students say virtual memory
                         to execute partially                 means "backup RAM"

Thrashing                Excessive PAGING ACTIVITY            Students say "excessive
                         Process spends more time paging      memory usage" (too vague)
                         than executing                       or "CPU overload"

Buffer register          Overcomes DIFFERENCE IN DATA         Students say "buffer =
                         TRANSFER SPEED between devices       increases speed" (vague)

Memory-mapped I/O        I/O and memory SHARE SAME address    Students say "separate
                         space                                address space"

Compaction vs Paging     Both solve external fragmentation;   Students say compaction
(as solutions)           Paging is PREFERRED (no copying),    is always preferred
                         Compaction is expensive (copies all)
──────────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS CONCEPT NOTES
## 🌊 India's Water Resources — Complete Deep Dive
### (Geography: Rivers, Dams, Irrigation, Groundwater, Water Problems)

---

## 🔷 TOPIC 1: INDIA'S RIVER SYSTEMS — OVERVIEW

```
INDIA'S RIVER CLASSIFICATION:
════════════════════════════════════════════════════════════════════

TYPE 1: HIMALAYAN RIVERS (Perennial = flow throughout year)
  → Source: Himalayan glaciers and snowfields
  → Flow: Year-round (even in dry season — glaciers melt)
  → Type: Young rivers — actively eroding (deep V-shaped valleys)
  → Characteristic: High sediment load → fertile plains
  → Examples: Ganga, Yamuna, Indus, Brahmaputra, Sutlej, Beas, Ravi

TYPE 2: PENINSULAR RIVERS (Non-perennial / Seasonal)
  → Source: Rainfall (monsoon-dependent)
  → Flow: Only during and after monsoon season
  → Type: Old rivers — lower gradient, wider valleys
  → Direction: MOST flow WESTWARD (from Western Ghats to Arabian Sea)
               BUT Godavari, Krishna, Kaveri, Mahanadi flow EASTWARD
  → Examples: Narmada, Tapi (westward), Godavari, Krishna (eastward)

KEY DIVIDES:
  → Vindhya + Satpura ranges = divide Ganga basin from Deccan drainage
  → Western Ghats = water divide between rivers flowing to Arabian Sea vs Bay of Bengal
  → Continental Divide = high ridge separating river basins

════════════════════════════════════════════════════════════════════

HIMALAYAN vs PENINSULAR RIVERS — COMPARISON:

FEATURE          HIMALAYAN RIVERS        PENINSULAR RIVERS
──────────────────────────────────────────────────────────────────
Source           Glacier + snowmelt      Rainfall only
Flow type        PERENNIAL (year-round)  SEASONAL (monsoon-fed)
Age              Young (still cutting)   Old (mature, lower gradient)
Valley type      Deep V-shaped (gorge)   Shallow, wide, flat
Sediment         HIGH (young rivers)     Lower (old rivers)
Course           Long, meandering        Shorter
Examples         Ganga, Yamuna, Indus    Godavari, Krishna, Narmada
Bihar rivers     Ganga, Gandak, Kosi,    —
                 Sone, Bagmati, Ghaghra
──────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 2: MAJOR RIVERS — KEY EXAM FACTS

```
GANGA RIVER SYSTEM:
════════════════════════════════════════════════════════════════════
  Origin:       Gangotri Glacier, Uttarakhand (Gaumukh = cow's mouth)
  Length:       ~2525 km (longest river in India)
  Tributaries:
    LEFT BANK:  Gomti, Ghaghra (Saryu), Gandak, Kosi ← Bihar rivers!
    RIGHT BANK: Yamuna, Son (Sone), Damodar
  Enters Bay of Bengal via Sunderbans (world's largest delta)
  Bihar = major state through which Ganga flows (Patna is on Ganga)

IMPORTANT BIHAR RIVERS:
  KOSI:         "Sorrow of Bihar" = extreme flooding; rises in Nepal
                Highly shifting course (meanders widely)
                Joins Ganga near Kursela, Bihar
  GANDAK:       Joins Ganga at Hajipur (near Patna)
  SONE:         Right bank tributary; meets Ganga near Patna
  GHAGHRA:      Also called Saryu; meets Ganga in UP (near Bihar border)
  BAGMATI:      Joins Kosi; flows through Nepal and Bihar
  PUNPUN:       Small river, joins Ganga south of Patna

  ← BPSC loves Bihar rivers — always memorize which bank tributaries are on

════════════════════════════════════════════════════════════════════

BRAHMAPUTRA SYSTEM:
  Origin:      Tibet (called Tsangpo in Tibet)
  Enters India: Arunachal Pradesh (called Dihang)
  Joins:       Joins tributaries → becomes Brahmaputra in Assam
  Exits India: Bangladesh (called Jamuna → merges with Ganga → Padma)
  Feature:     One of India's LARGEST RIVERS by discharge and width
               ANTECEDENT river — older than Himalayas (cut through as
               mountains rose)

INDUS SYSTEM (western):
  Origin:      Tibet (Mansarovar Lake area)
  Flows:       Through Ladakh → Pakistan
  Tributaries: Jhelum, Chenab, Ravi, Beas, Sutlej (5 rivers = Punjab)
  Treaty:      Indus Waters Treaty (1960) — India + Pakistan

GODAVARI (Peninsular):
  Longest peninsular river = Godavari (NOT Ganga — Ganga is total India)
  Origin: Nashik (Western Ghats, Maharashtra)
  Direction: Flows EAST → Bay of Bengal
  Called: "Vriddha Ganga" (Old Ganga)

NARMADA:
  Direction: Flows WEST → Arabian Sea (through rift valley, not delta)
  Flows through: Madhya Pradesh, Gujarat
  Divides: Vindhya range (north) from Deccan Plateau (south)
  Feature: Flows in a RIFT VALLEY (tectonic depression) — NOT erosion valley

TAPI (TAPTI):
  Direction: Flows WEST → Arabian Sea
  Origin: Betul plateau, MP → flows through Gujarat
  Like Narmada but south of it

════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 3: MAJOR DAMS AND RIVERS — BPSC EXAM TABLE

```
MAJOR DAMS OF INDIA:
════════════════════════════════════════════════════════════════════

DAM NAME          RIVER        STATE               KEY FACT
──────────────────────────────────────────────────────────────────
Tehri Dam         Bhagirathi   Uttarakhand         Tallest dam in India
                               (joins Alaknanda     (260m high, rock-fill)
                               = Ganga)

Bhakra Nangal     Sutlej       Punjab/HP border     One of largest gravity dams
                                                    (known as "Temple of Modern India"
                                                    — Nehru's quote)

Hirakud Dam       Mahanadi     Odisha               Longest dam in India
                                                    (25.79 km total length)

Nagarjuna Sagar   Krishna      Andhra Pradesh/      World's largest masonry dam
                               Telangana border     (when built)

Sardar Sarovar    Narmada      Gujarat              Narmada Valley Project;
(Narmada Dam)                                       major controversy (NBA movement
                                                    — Medha Patkar)

Tungabhadra       Tungabhadra  Karnataka +          Important for Karnataka/AP
                               Andhra Pradesh       irrigation

Koyna Dam         Koyna        Maharashtra          Caused earthquake after filling
                                                    (reservoir-induced seismicity)

Rihand Dam        Rihand       Uttar Pradesh        Creates Govind Vallabh Pant Sagar
(Govind Vallabh                                     reservoir (large)
Pant Dam)

Farakka Barrage   Ganga        West Bengal          Controls flow to Bangladesh
                                                    (India-Bangladesh water dispute)
──────────────────────────────────────────────────────────────────

IMPORTANT PREFIXES (Nehru's quotes on dams):
  "These are the TEMPLES OF MODERN INDIA" = Bhakra Nangal Dam (Nehru)
  ← BPSC frequently tests this quote

BIHAR DAMS:
  → Gandak Barrage (Valmiki Nagar, Bihar/Nepal border) — Gandak river
  → Sone Barrage (near Dehri-on-Sone) — Sone river
  → North Kosi Canal headwork — Kosi river (at Hanuman Nagar, Nepal border)
```

---

## 🔷 TOPIC 4: IRRIGATION IN INDIA

```
IRRIGATION = Artificial supply of water to agricultural land

TYPES OF IRRIGATION:
════════════════════════════════════════════════════════════════════

1. CANAL IRRIGATION:
   → Channels dug from rivers to fields
   → Most common in: North India (Indo-Gangetic plain)
   → Best for: Flat terrain
   → States: Uttar Pradesh, Punjab, Haryana (most canal-irrigated)
   → Network: India has world's largest canal irrigation network
   → Types:
     Inundation canals: take water when river floods (seasonal)
     Perennial canals: take water throughout year (from dams)

2. WELL / TUBE WELL IRRIGATION:
   → Extract groundwater from wells or tube wells
   → Most widely used irrigation method in INDIA overall
   → Best for: Areas with good groundwater (alluvial plains)
   → States: UP, Bihar, Haryana, Punjab, Rajasthan
   → Tube wells pump water electrically; very widespread

3. TANK IRRIGATION:
   → Small reservoirs created by earthen bunds to store rainwater
   → Most common in: SOUTH INDIA (Deccan Plateau)
   → States: Tamil Nadu, Andhra Pradesh, Karnataka
   → Reason: Peninsula rivers are seasonal; tanks store monsoon water

════════════════════════════════════════════════════════════════════

IRRIGATION IN INDIA — KEY FACTS:
  → Most irrigated land: UTTAR PRADESH (by absolute area)
  → Highest % of land irrigated: PUNJAB (nearly all agriculture irrigated)
  → Tube well irrigation = most common method in INDIA
  → Canal irrigation = most common in PUNJAB, HARYANA (north)
  → Tank irrigation = most common in SOUTH INDIA
  → Bihar irrigation: Heavily dependent on groundwater (tube wells)
                     Canal irrigation from Gandak, Sone, Kosi systems

TYPES OF IRRIGATION EFFICIENCY:
  Drip Irrigation = Most water-efficient (water at plant roots directly)
  Sprinkler = Moderate efficiency
  Flood/furrow = Least efficient (high water loss to evaporation)
```

---

## 🔷 TOPIC 5: GROUNDWATER — CRITICAL WATER RESOURCE

```
GROUNDWATER = Water stored underground in AQUIFERS

AQUIFER = Porous rock/sand layer that holds + transmits groundwater
  → Unconfined aquifer: open at top, recharged by rainfall directly
  → Confined aquifer: trapped between impermeable layers (artesian)

INDIA'S GROUNDWATER SITUATION:
  → India is the WORLD'S LARGEST GROUNDWATER USER
    (uses ~25% of global groundwater extraction)
  → Agriculture accounts for ~90% of all groundwater use in India
  → Tube well revolution (1960s-70s) enabled Green Revolution in Punjab, UP
  → But overextraction = GROUNDWATER TABLE FALLING in many states

WATER TABLE = Level below which ground is saturated with water
  → Rising water table: waterlogging, soil salinization → bad for crops
  → Falling water table: wells run dry, agriculture fails → bad trend
  → Critical overexploited states: Punjab, Haryana, Rajasthan, Delhi

WATER SCARCITY IN INDIA:
  → RAINFED agriculture = ~60% of India's total cropped area
  → IRRIGATED agriculture = ~40% of cropped area but produces ~55% of output
  → Per capita water availability is DECLINING:
    1950: ~5000 cubic meters/person/year
    Now:  ~1500 cubic meters/person/year (approaching water stress threshold)

WATERSHED MANAGEMENT:
  → Watershed = area drained by a single river/stream system
  → Watershed management = protect and conserve catchment areas
  → Prevents soil erosion, maintains groundwater recharge
  → Government schemes: PMKSY (Pradhan Mantri Krishi Sinchayee Yojana)
```

---

## 🔷 TOPIC 6: WATER ISSUES — DISPUTES AND POLICIES

```
INTER-STATE WATER DISPUTES (BPSC-tested):
════════════════════════════════════════════════════════════════════

KAVERI DISPUTE:
  States:  Karnataka vs Tamil Nadu
  Issue:   Sharing Kaveri River water for agriculture
  Status:  Kaveri Water Disputes Tribunal; Supreme Court orders

KRISHNA RIVER DISPUTE:
  States:  Andhra Pradesh vs Karnataka vs Telangana vs Maharashtra
  Issue:   Allocation of Krishna water for irrigation

NARMADA DISPUTE:
  States:  Madhya Pradesh vs Gujarat vs Maharashtra vs Rajasthan
  Project: Sardar Sarovar Dam on Narmada
  Issue:   Displacement of people (Narmada Bachao Andolan — Medha Patkar)

INDUS WATERS TREATY (1960):
  Countries: India and Pakistan
  Mediator:  World Bank
  Terms:     India gets: Sutlej, Beas, Ravi (Eastern rivers)
             Pakistan gets: Indus, Jhelum, Chenab (Western rivers)

FARAKKA BARRAGE DISPUTE:
  Countries: India and Bangladesh
  Issue:     Farakka Barrage diverts Ganga water → reduces flow to Bangladesh
  Status:    Ganga Water Treaty (1996) between India and Bangladesh

════════════════════════════════════════════════════════════════════

WATERLOGGING AND SOIL SALINITY:
  → Over-irrigation → water table rises → waterlogging
  → Waterlogged soil: roots can't breathe → crop failure
  → Salinization: evaporation leaves salt deposits → white crusty soil → useless
  → Solutions: drainage canals, drip irrigation, crop rotation

WATER HARVESTING (Traditional methods):
  Kund/Kundis:  Rajasthan — underground cisterns for rainwater
  Baolis:       Rajasthan, Gujarat — step wells
  Johads:       Rajasthan — earthen dams/ponds
  Ponds/Tanks:  South India — tank irrigation tradition
  Kul:          Himachal Pradesh — canal from glaciers/streams
  ← BPSC: traditional water harvesting = Rajasthan specialty (kund, baoli, johad)
```

---

## 🔷 TOPIC 7: BIHAR AND WATER — HIGH BPSC PROBABILITY

```
BIHAR'S WATER RESOURCES PROFILE:
════════════════════════════════════════════════════════════════════

RIVERS IN BIHAR:
  → 13 major rivers flow through Bihar
  → GANGA = the main river; flows east through center of Bihar
  → Major tributaries joining Ganga in Bihar:
    Northern tributaries (Nepal origin, left bank):
      Gandak (joins at Hajipur)
      Bagmati (joins Kosi)
      Kosi (joins near Kursela) = SORROW OF BIHAR ← must know
      Mahananda (flows through Kishanganj, Bihar)
    Southern tributaries (right bank):
      Sone (Son) = joins near Arrah/Patna area
      Punpun = joins Ganga south of Patna

KOSI RIVER — MOST TESTED:
  → Called "Sorrow of Bihar" (Bihar ka Shok) ← exact phrase
  → Rises in Tibet/Nepal Himalayas
  → Carries ENORMOUS sediment → deposits on plains → CONSTANTLY SHIFTS course
  → Has shifted westward by ~120 km over last 200 years!
  → Causes devastating floods EVERY YEAR in North Bihar
  → Districts affected: Supaul, Saharsa, Madhepura, Darbhanga, Muzaffarpur
  → Kosi High Dam proposal = still controversial (partly in Nepal)
  → Kosi Barrage at Hanuman Nagar (Nepal) controls some flow

GANDAK RIVER:
  → Also called Narayani (in Nepal)
  → Joins Ganga at HAJIPUR (Vaishali district, Bihar) ← tested
  → Gandak Project = hydropower + irrigation dam at Valmiki Nagar
  → Important for North Bihar irrigation

SONE (SON) RIVER:
  → Only major SOUTH BANK (peninsular) tributary in Bihar
  → Origin: Amarkantak plateau (MP)
  → Joins Ganga near Patna/Arrah area
  → Sone barrage at Dehri-on-Sone = important irrigation source

FLOODS IN BIHAR:
  → Bihar = MOST FLOOD-PRONE state in India
  → About 76% of North Bihar is flood-prone
  → Cause: Himalayan rivers carry high sediment → raise riverbeds → overflow
  → About 17% of India's total flood-prone area is in Bihar alone
  → Most devastating floods: Kosi (1954, 2008 were particularly destructive)
  → 2008 Kosi flood: Kosi changed course suddenly → massive disaster

WATERWAYS IN BIHAR:
  → National Waterway 1 (NW-1) = Ganga river = Allahabad to Haldia
  → Patna is on National Waterway 1
  → Inland water transport being developed on Ganga in Bihar

════════════════════════════════════════════════════════════════════
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED PYQ + CONCEPT MCQs — Day 70 (CS + GS)

---

### COMPUTER SCIENCE — 25 MCQs (Segmentation, Compaction, Virtual Memory, Thrashing)

---

**Q1.** Which of the following statements about FRAGMENTATION is CORRECT?
(A) Fragmentation is a memory management technique to improve performance
(B) Fragmentation is a PROBLEM — wasted memory — not a technique
(C) Fragmentation is a solution to the external memory problem
(D) More than one of the above
(E) None of the above

---

**Q2.** COMPACTION in memory management means:
(A) Dividing a process into fixed-size pages and storing them non-contiguously
(B) Shifting ALL active processes to ONE end of memory so ALL free memory forms ONE LARGE BLOCK
(C) Replacing the least recently used page when memory is full
(D) More than one of the above
(E) None of the above

---

**Q3.** What problem does COMPACTION SOLVE?
(A) Internal fragmentation (wasted space inside pages)
(B) Page fault rate (too many disk accesses)
(C) External fragmentation (scattered free memory)
(D) More than one of the above
(E) None of the above

---

**Q4.** The SEGMENT BASE in a segmentation system refers to:
(A) The size (length) of the segment
(B) The STARTING ADDRESS of the segment in physical memory
(C) The logical starting address of the segment
(D) More than one of the above
(E) None of the above

---

**Q5.** THRASHING in an operating system is caused by:
(A) Too many processes with too few frames — excessive page swapping
(B) A disk scheduling algorithm that causes starvation of some requests
(C) Buffer overflow due to insufficient cache size
(D) More than one of the above
(E) None of the above

---

**Q6.** In SEGMENTATION, which type of fragmentation CAN occur?
(A) Internal fragmentation only
(B) Both internal and external fragmentation
(C) External fragmentation (because segments are variable size)
(D) More than one of the above
(E) None of the above

---

**Q7.** What does a SEGMENT TABLE entry contain?
(A) Frame number and valid bit only
(B) Base address (starting physical address) and LIMIT (size of segment)
(C) Page number and offset for each segment
(D) More than one of the above
(E) None of the above

---

**Q8.** VIRTUAL MEMORY allows:
(A) Execution of processes that are LARGER than available physical RAM
(B) Replacing RAM entirely with secondary storage
(C) Eliminating the need for a page table
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following CORRECTLY describes EXTERNAL FRAGMENTATION?
(A) Memory wasted INSIDE allocated pages because the process doesn't fill them
(B) Free memory that is SCATTERED in non-contiguous chunks — a process can't load despite enough total free memory
(C) Memory lost because the segment table is too large
(D) More than one of the above
(E) None of the above

---

**Q10.** BUFFER REGISTERS are used in computer systems primarily to:
(A) Permanently store frequently accessed data
(B) Overcome the DIFFERENCE IN DATA TRANSFER SPEED between devices
(C) Cache page table entries for faster address translation
(D) More than one of the above
(E) None of the above

---

**Q11.** A SEGMENT FAULT occurs when:
(A) A process tries to access a page that is not in RAM (valid bit = 0)
(B) A process tries to access a segment with an offset GREATER than or equal to the segment's LIMIT
(C) Two segments have the same base address
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following is TRUE about PAGING versus SEGMENTATION?
(A) Both paging and segmentation cause external fragmentation
(B) Paging causes internal fragmentation; Segmentation can cause external fragmentation
(C) Segmentation causes internal fragmentation; Paging causes external fragmentation
(D) More than one of the above
(E) None of the above

---

**Q13.** In a virtual memory system, pages that are NOT in RAM are stored in:
(A) CPU registers
(B) Cache memory
(C) Swap space on secondary storage (disk)
(D) More than one of the above
(E) None of the above

---

**Q14.** Thrashing causes CPU utilization to:
(A) Increase dramatically — processes compete for CPU
(B) Stay constant — CPU stays busy with page faults
(C) DROP sharply — CPU spends all time waiting for page I/O
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following is the BEST solution to external fragmentation?
(A) Using larger page sizes
(B) Compaction (shifting processes) or using Paging (non-contiguous allocation)
(C) Increasing the number of segments per process
(D) More than one of the above
(E) None of the above

---

**Q16.** In MEMORY-MAPPED I/O:
(A) I/O devices have a SEPARATE address space from main memory
(B) I/O devices and main memory SHARE THE SAME address space
(C) I/O operations require special IN/OUT instructions
(D) More than one of the above
(E) None of the above

---

**Q17.** In segmentation, the PHYSICAL ADDRESS is calculated as:
(A) Frame number + Offset (same as paging)
(B) Segment BASE + Offset (where offset < Limit)
(C) Segment number × Offset
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following CORRECTLY differentiates a BUFFER from a CACHE?
(A) Buffer = permanent storage; Cache = temporary storage
(B) Buffer = data in transit between two devices (speed difference); Cache = stores frequently used data for reuse
(C) Buffer and cache are the same — both store data temporarily
(D) More than one of the above
(E) None of the above

---

**Q19.** The WORKING SET MODEL is used to:
(A) Calculate the optimal page size for a process
(B) Prevent thrashing by tracking the active pages a process needs
(C) Sort processes by priority for CPU scheduling
(D) More than one of the above
(E) None of the above

---

**Q20.** Compaction is described as EXPENSIVE because:
(A) It requires purchasing additional hardware
(B) It must physically copy ALL processes to new locations AND update all addresses
(C) It increases the size of the page table significantly
(D) More than one of the above
(E) None of the above

---

**Q21.** In segmentation, if a process has segments of sizes: 100B, 400B, 200B, 300B, what is the total memory EXACTLY allocated?
(A) 1200 bytes with 0 internal fragmentation
(B) 2048 bytes with 848 bytes wasted
(C) 1000 bytes with rounding up to next power of 2
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following CORRECTLY describes DEMAND PAGING?
(A) All pages of a process are loaded into RAM before execution begins
(B) Pages are loaded into RAM ONLY when they are actually accessed
(C) Pages are pre-loaded in batches before they are needed
(D) More than one of the above
(E) None of the above

---

**Q23.** The PRIMARY ADVANTAGE of SEGMENTATION over paging is:
(A) Segmentation completely eliminates all types of fragmentation
(B) Segmentation matches the programmer's logical view of memory (code, data, stack)
(C) Segmentation is faster than paging due to smaller lookup tables
(D) More than one of the above
(E) None of the above

---

**Q24.** After COMPACTION, all free memory is consolidated into:
(A) Multiple small equally-sized blocks distributed throughout RAM
(B) Exactly two blocks: one at start and one at end of RAM
(C) ONE SINGLE LARGE CONTIGUOUS BLOCK
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is TRUE about INTERNAL FRAGMENTATION?
(A) It occurs because free memory is scattered between processes
(B) It is caused by VARIABLE-SIZE allocation where holes are left between processes
(C) It occurs because a process doesn't fill the entire last allocated page/block
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs (India's Water Resources + Bihar Geography)

---

**Q26.** Which of the following rivers is called the "Sorrow of Bihar"?
(A) Gandak
(B) Sone
(C) Kosi
(D) More than one of the above
(E) None of the above

---

**Q27.** The LONGEST PENINSULAR RIVER of India is:
(A) Krishna
(B) Narmada
(C) Godavari
(D) More than one of the above
(E) None of the above

---

**Q28.** Which of the following rivers flows through a RIFT VALLEY (tectonic valley)?
(A) Ganga
(B) Brahmaputra
(C) Narmada
(D) More than one of the above
(E) None of the above

---

**Q29.** The HIRAKUD DAM is built on which river?
(A) Godavari
(B) Mahanadi
(C) Krishna
(D) More than one of the above
(E) None of the above

---

**Q30.** "These are the TEMPLES OF MODERN INDIA" — Jawaharlal Nehru said this about:
(A) IITs and IIMs (educational institutions)
(B) Bhakra Nangal Dam (Sutlej river)
(C) Nuclear power plants
(D) More than one of the above
(E) None of the above

---

**Q31.** Himalayan rivers are described as PERENNIAL because:
(A) They flow only during the monsoon season
(B) They receive water from glaciers and snowmelt throughout the year
(C) They are fed by rainfall from the Western Ghats
(D) More than one of the above
(E) None of the above

---

**Q32.** The Gandak River joins the Ganga at which location in Bihar?
(A) Patna
(B) Hajipur
(C) Kursela
(D) More than one of the above
(E) None of the above

---

**Q33.** The INDUS WATERS TREATY (1960) was signed between India and Pakistan. Under this treaty, which rivers were allocated to INDIA?
(A) Indus, Jhelum, Chenab (western rivers)
(B) Sutlej, Beas, Ravi (eastern rivers)
(C) Ganga, Yamuna, Brahmaputra
(D) More than one of the above
(E) None of the above

---

**Q34.** Which of the following is the MOST COMMON irrigation method in India overall?
(A) Canal irrigation
(B) Tank irrigation (South India)
(C) Well / Tube well irrigation
(D) More than one of the above
(E) None of the above

---

**Q35.** TANK IRRIGATION is MOST prevalent in which part of India?
(A) North India (Gangetic plains)
(B) South India (Deccan Plateau — Tamil Nadu, AP, Karnataka)
(C) Northeast India
(D) More than one of the above
(E) None of the above

---

**Q36.** The FARAKKA BARRAGE was built on which river and for what purpose?
(A) Ganga; to divert water to flush Kolkata port + control flow to Bangladesh
(B) Brahmaputra; to control flooding in Assam
(C) Mahanadi; to irrigate Odisha's agricultural land
(D) More than one of the above
(E) None of the above

---

**Q37.** About what PERCENTAGE of North Bihar is FLOOD-PRONE?
(A) 25%
(B) 50%
(C) 76%
(D) More than one of the above
(E) None of the above

---

**Q38.** Which water harvesting structure is MOST ASSOCIATED with Rajasthan's traditional water conservation?
(A) Ponds and tanks (earthen reservoirs)
(B) Kund, Baoli, and Johad (underground cisterns, step wells, earthen dams)
(C) Check dams and percolation tanks
(D) More than one of the above
(E) None of the above

---

**Q39.** The GODAVARI river is also known as:
(A) "Ganga of the South"
(B) "Vriddha Ganga" (Old Ganga) ← also called Dakshin Ganga
(C) "Sorrow of India"
(D) More than one of the above
(E) None of the above

---

**Q40.** India is the world's LARGEST user of groundwater. Approximately what percentage of India's groundwater use goes to AGRICULTURE?
(A) 50%
(B) 70%
(C) 90%
(D) More than one of the above
(E) None of the above

---

**Q41.** The NARMADA BACHAO ANDOLAN was associated with which protest leader?
(A) Anna Hazare
(B) Medha Patkar
(C) Sunderlal Bahuguna
(D) More than one of the above
(E) None of the above

---

**Q42.** The SONE (Son) River is a TRIBUTARY of the GANGA from which bank?
(A) Left bank (northern tributary)
(B) Right bank (southern/peninsular tributary)
(C) It is not a tributary — it merges with Yamuna first
(D) More than one of the above
(E) None of the above

---

**Q43.** The TALLEST DAM in India is:
(A) Bhakra Dam (Sutlej)
(B) Hirakud Dam (Mahanadi)
(C) Tehri Dam (Bhagirathi, Uttarakhand)
(D) More than one of the above
(E) None of the above

---

**Q44.** WATERLOGGING in agricultural land is primarily caused by:
(A) Insufficient rainfall during the Kharif season
(B) Over-irrigation leading to rise in water table
(C) Excessive use of chemical fertilizers
(D) More than one of the above
(E) None of the above

---

**Q45.** DRIP IRRIGATION is significant because:
(A) It delivers water in large quantities quickly for maximum crop growth
(B) It is the MOST WATER-EFFICIENT irrigation method (water delivered directly to roots)
(C) It is only suitable for paddy (rice) cultivation
(D) More than one of the above
(E) None of the above

---

**Q46.** National Waterway 1 (NW-1), which passes through Bihar (Patna), follows which river?
(A) Brahmaputra
(B) Mahanadi
(C) Ganga (from Allahabad/Prayagraj to Haldia)
(D) More than one of the above
(E) None of the above

---

**Q47.** The BRAHMAPUTRA River is called by what name in TIBET?
(A) Jamuna
(B) Dihang
(C) Tsangpo
(D) More than one of the above
(E) None of the above

---

**Q48.** The KOSI RIVER is known for which characteristic that earned it the title "Sorrow of Bihar"?
(A) It has extremely fast current that erodes riverbanks
(B) It constantly SHIFTS its course (has shifted ~120 km westward) causing devastating floods
(C) It carries toxic pollutants from Nepal industries
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following CORRECTLY identifies the drainage pattern of Indian rivers?
(A) Most peninsular rivers flow WESTWARD toward the Arabian Sea
(B) Godavari, Krishna, Kaveri, and Mahanadi flow EASTWARD toward the Bay of Bengal
(C) Narmada and Tapi flow WESTWARD toward the Arabian Sea
(D) More than one of the above
(E) None of the above

---

**Q50.** MATCH THE FOLLOWING — Dam and its River:
```
Dam                  River
1. Tehri Dam         A. Mahanadi
2. Hirakud Dam       B. Sutlej
3. Bhakra Nangal     C. Narmada (Gujarat)
4. Sardar Sarovar    D. Bhagirathi (Uttarakhand)
```
(A) 1-D, 2-A, 3-B, 4-C
(B) 1-A, 2-D, 3-C, 4-B
(C) 1-B, 2-C, 3-A, 4-D
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt ALL 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 1  | (B)    | Fragmentation = PROBLEM (wasted memory), NOT a technique ← direct PYQ trap |
| 2  | (B)    | Compaction = shift ALL processes to ONE end → ALL free memory in ONE LARGE BLOCK |
| 3  | (C)    | Compaction solves EXTERNAL fragmentation (scattered free memory) |
| 4  | (B)    | Segment BASE = STARTING PHYSICAL ADDRESS of segment ← exact PYQ phrase |
| 5  | (A)    | Thrashing = too many processes, too few frames → excessive page swapping |
| 6  | (C)    | Segmentation can cause EXTERNAL fragmentation (variable-size allocation) |
| 7  | (B)    | Segment table entry = Base address + Limit (size) |
| 8  | (A)    | Virtual memory allows process LARGER than RAM to execute (partially loaded) |
| 9  | (B)    | External frag = free memory scattered non-contiguously; total OK but no contiguous block |
| 10 | (B)    | Buffer registers = overcome DIFFERENCE IN DATA TRANSFER SPEED ← exact PYQ phrase |
| 11 | (B)    | Segment fault = offset ≥ Limit (going beyond segment boundary) |
| 12 | (B)    | Paging → internal frag (last page); Segmentation → external frag (variable size) |
| 13 | (C)    | Pages not in RAM stored in SWAP SPACE on disk (page file, swap partition) |
| 14 | (C)    | Thrashing = CPU utilization DROPS sharply (CPU waits for disk I/O constantly) |
| 15 | (B)    | Compaction (expensive) or Paging (preferred) both solve external fragmentation |
| 16 | (B)    | Memory-mapped I/O = I/O and memory SHARE THE SAME address space ← TRE 1.0 PYQ |
| 17 | (B)    | Physical address = Segment BASE + Offset (check offset < Limit first) |
| 18 | (B)    | Buffer = data in transit (speed diff); Cache = stores frequently used data for reuse |
| 19 | (B)    | Working Set Model = prevents thrashing by tracking active pages needed per process |
| 20 | (B)    | Compaction expensive because copies ALL processes to new locations + updates addresses |
| 21 | (A)    | Segmentation = EXACT size allocation; total = 100+400+200+300 = 1000B, 0 internal frag |
| 22 | (B)    | Demand paging = pages loaded ONLY when accessed (on page fault) |
| 23 | (B)    | Segmentation's main advantage = matches programmer's logical view (code/data/stack) |
| 24 | (C)    | After compaction = ONE SINGLE LARGE CONTIGUOUS BLOCK ← exact PYQ phrase |
| 25 | (C)    | Internal frag = process doesn't fill the entire last allocated page/block |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 26 | (C)    | KOSI = "Sorrow of Bihar" — devastating floods, shifting course |
| 27 | (C)    | GODAVARI = longest peninsular river (Ganga is India's longest overall) |
| 28 | (C)    | NARMADA flows through a rift valley (tectonic depression, not erosion) |
| 29 | (B)    | Hirakud Dam = on MAHANADI river, Odisha |
| 30 | (B)    | Nehru said "Temples of Modern India" about BHAKRA NANGAL DAM |
| 31 | (B)    | Himalayan rivers = perennial because glacier + snowmelt feeds them year-round |
| 32 | (B)    | Gandak joins Ganga at HAJIPUR (Vaishali district, Bihar) |
| 33 | (B)    | India got Eastern rivers: Sutlej, Beas, Ravi (Pakistan got western) |
| 34 | (C)    | Tube well / well irrigation = MOST COMMON method in India overall |
| 35 | (B)    | Tank irrigation = most prevalent in SOUTH INDIA (Deccan Plateau) |
| 36 | (A)    | Farakka on Ganga; diverts water to Hooghly (Kolkata port); causes Bangladesh dispute |
| 37 | (C)    | ~76% of North Bihar is flood-prone |
| 38 | (B)    | Rajasthan traditional water harvesting = Kund, Baoli, Johad |
| 39 | (D)    | Godavari = BOTH "Ganga of the South" AND "Vriddha Ganga" — both names used |
| 40 | (C)    | ~90% of India's groundwater use = agriculture |
| 41 | (B)    | Medha Patkar led Narmada Bachao Andolan (NBA) against Sardar Sarovar Dam |
| 42 | (B)    | Sone (Son) = RIGHT BANK tributary (peninsular/southern tributary of Ganga) |
| 43 | (C)    | TEHRI DAM = tallest dam in India (260 metres, Bhagirathi, Uttarakhand) |
| 44 | (B)    | Waterlogging = over-irrigation causes water table to RISE → land stays saturated |
| 45 | (B)    | Drip irrigation = most water-efficient (delivers at roots, minimal evaporation) |
| 46 | (C)    | NW-1 = GANGA (Allahabad/Prayagraj to Haldia); Patna is on this waterway |
| 47 | (C)    | Brahmaputra called TSANGPO in Tibet |
| 48 | (B)    | Kosi constantly SHIFTS its course (~120 km westward shift) → unpredictable floods |
| 49 | (D)    | Options B and C are BOTH correct (Godavari/Krishna/Kaveri = east; Narmada/Tapi = west) |
| 50 | (A)    | Tehri-D(Bhagirathi), Hirakud-A(Mahanadi), Bhakra-B(Sutlej), Sardar Sarovar-C(Narmada) |

---
---

# 🔁 NIGHT REVISION SHEET
## 📌 Day 70 — Ultra-Crisp "Last 30 Minutes Before Sleep"

---

### ⚡ CS — SEGMENTATION + COMPACTION + VM: 20 MUST-KNOW FACTS

```
SEGMENTATION:
1.  Segmentation = variable-size SEGMENTS (code/data/stack/heap)
    Page = FIXED size | Segment = VARIABLE size
2.  Segment Table entry = BASE (starting physical address) + LIMIT (size)
    ← "Segment base = STARTING ADDRESS in physical memory" = exact PYQ
3.  Segment fault = offset ≥ Limit (going beyond boundary)
4.  Physical address = Segment Base + Offset
5.  Segmentation = NO internal frag; CAN have external frag
    Paging = NO external frag; YES internal frag

FRAGMENTATION:
6.  Fragmentation = PROBLEM (not technique, not solution!) ← DIRECT PYQ TRAP
7.  Internal frag = waste INSIDE allocated block (paging, fixed partition)
8.  External frag = free memory scattered non-contiguously (segmentation)

COMPACTION:
9.  Compaction = shifts ALL processes to ONE end → ALL free memory in ONE BLOCK
10. Compaction = solution to EXTERNAL fragmentation
11. Compaction is EXPENSIVE = must physically copy all processes + update addresses
12. Paging is PREFERRED over compaction (no copying needed)

VIRTUAL MEMORY:
13. Virtual memory = process LARGER than RAM can execute (partial load)
14. Pages not in RAM → stored in SWAP SPACE (disk)
15. Page fault → valid bit = 0 → OS loads page from swap → restarts instruction

THRASHING:
16. Thrashing = excessive PAGING ACTIVITY = process spends more time paging than executing
17. Cause = too many processes, too few frames (working set doesn't fit)
18. CPU utilization DROPS sharply when thrashing begins
19. Solution = Working Set Model / Page Fault Frequency / reduce multiprogramming

BUFFER + I/O:
20. Buffer register = overcomes DIFFERENCE IN DATA TRANSFER SPEED ← PYQ exact phrase
21. Memory-mapped I/O = I/O + memory SHARE SAME address space ← TRE 1.0 PYQ
22. Buffer ≠ Cache: Buffer = data in transit; Cache = stores for reuse
```

---

### ⚡ GS — WATER RESOURCES: 15 MUST-KNOW FACTS

```
RIVERS:
1.  Kosi = "SORROW OF BIHAR" — floods Bihar; constantly shifts course (~120km west shift)
2.  Gandak joins Ganga at HAJIPUR ← tested
3.  Sone = RIGHT BANK tributary of Ganga (peninsular, southern)
4.  Godavari = longest PENINSULAR river (also Vriddha Ganga / Ganga of South)
5.  Narmada flows through RIFT VALLEY (not erosion valley) → westward to Arabian Sea
6.  Brahmaputra = TSANGPO in Tibet; Dihang in Arunachal Pradesh

DAMS:
7.  Tehri Dam = TALLEST dam in India (260m, Bhagirathi, Uttarakhand)
8.  Hirakud Dam = LONGEST dam in India (Mahanadi, Odisha)
9.  Bhakra Nangal = "Temples of Modern India" (Nehru); on Sutlej river
10. Sardar Sarovar = Narmada; Narmada Bachao Andolan = Medha Patkar

IRRIGATION:
11. Most common irrigation in INDIA = Tube well / well irrigation
12. Tank irrigation = MOST common in SOUTH INDIA (Deccan)
13. Drip irrigation = most water-EFFICIENT method
14. Punjab = highest % of land irrigated (canal system)

WATER ISSUES:
15. India = world's LARGEST groundwater USER (~25% of global extraction)
    ~90% of India's groundwater = agriculture
16. NW-1 = Ganga (Prayagraj to Haldia) — Patna is on this waterway
17. Indus Waters Treaty (1960) = India (eastern rivers) + Pakistan (western rivers)
    Mediator = World Bank
```

---

### ⚡ TOMORROW — DAY 71 PREVIEW

```
CS:  Disk Scheduling — FCFS, SSTF, SCAN, C-SCAN
     KEY CALCULATION:
     Requests: 98, 183, 37, 122, 14, 124, 65, 67 | Head at 53
     FCFS total movement = |53-98|+|98-183|+|183-37|+... (sum abs differences in order)
     SSTF = always jump to nearest request first

GS:  Indian Geography — Indian Landforms, Plateaus, Coastal Plains
```

---

## 🎯 WEEK 11 PROGRESS TRACKER

```
Day 68: OS Introduction & Types              ✅ DONE
Day 69: Paging (Complete)                    ✅ DONE
Day 70: Segmentation + Virtual Memory        ← TODAY ✅
Day 71: Disk Scheduling (FCFS calculation)
Day 72: I/O Management + File Systems
Day 73: Threads + CPU Scheduling + Deadlocks
Day 74: OS Complete Revision + 25 PYQ MCQs
```

---

*Day 70 Complete | Week 11 of 25 | Phase 2: Depth | Target: TOP 50 RANK*
