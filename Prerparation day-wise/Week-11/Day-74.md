# 📅 BPSC TRE 4.0 — DAY 74: COMPLETE OS REVISION + FULL GS REVISION
### Week 11 Final Day — Every OS concept from Days 68–73 + GS Master Revision (History + Geography + Science + Maths)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (2 hrs): CS — Complete OS Rapid Revision (Days 68–73, ALL topics, crisp format)
> - Afternoon (1 hr): GS — Full GS Rapid Revision (History + Geography + Science + Maths shortcuts)
> - Evening (1.5 hrs): Solve all 50 MCQs (25 OS PYQ + 25 GS PYQ)
> - Night (30 min): Read the Night Revision Sheet

---

# PART 1: CS COMPLETE REVISION
## 📘 Operating Systems — ALL Topics from Days 68–73

---

## 🔷 UNIT A: OS TYPES + PROCESS STATES (Day 68)

```
OS TYPES — MASTER TABLE:
════════════════════════════════════════════════════════════════════

OS TYPE           KEY FACT                              PYQ TRAP
─────────────────────────────────────────────────────────────────
Batch OS          No user interaction during execution   NOT time-sharing
Time-sharing OS   Multiple users share CPU via slices    MARKS BEGINNING OF
                  → Round Robin scheduling               COMPUTER COMMUNICATIONS
                  ← TRE 1.0 DIRECT PYQ!                 ← exact phrase to memorize
Real-time OS      Hard RTOS = strict deadline            Pacemaker, missile = Hard
(RTOS)            (missed = SYSTEM FAILURE)              RTOS not Soft RTOS
Embedded OS       Designed for specific device           ATM, washing machine,
                  (limited memory, single function)      smartwatch
Distributed OS    Multiple CPUs appear as ONE system     User sees ONE computer
Multi-programming Multiple jobs in RAM, ONE CPU          ≠ multi-processing
Multi-processing  Multiple CPUs (true parallelism)       ≠ multi-programming
─────────────────────────────────────────────────────────────────

★ Time-sharing = beginning of COMPUTER COMMUNICATIONS ← TRE 1.0 exact PYQ
★ Multi-programming (1 CPU) ≠ Multi-processing (multiple CPUs)

════════════════════════════════════════════════════════════════════

OS KEY DEFINITIONS:
  KERNEL = Core of OS; ALWAYS in memory; manages all resources
  PCB    = Process Control Block; stores all process info (PID, state, PC, registers)
  MMU    = Memory Management Unit; translates logical → physical addresses

PROCESS STATES (5-state model):
  NEW → READY → RUNNING → WAITING / TERMINATED
  INVALID transition: NEW → RUNNING directly (must go through READY)
  RUNNING → READY:   Timer interrupt (time slice expired, preemption)
  RUNNING → WAITING: Process requests I/O operation
  WAITING → READY:   I/O completes / event occurs
  WAITING ≠ READY:   WAITING = blocked on I/O; READY = waiting for CPU only

INTERRUPTS:
  VALID types:   Hardware, Software, Trap (exception), Maskable, Non-Maskable (NMI)
  INVALID type:  "Memory interrupt" ← DOES NOT EXIST ← direct PYQ trap
  NMI = Non-Maskable Interrupt = CANNOT be ignored by CPU
  Trap = caused by program ERROR (division by zero, invalid memory access)
```

---

## 🔷 UNIT B: PAGING (Day 69)

```
PAGING CORE CONCEPTS:
════════════════════════════════════════════════════════════════════

  PAGE  = fixed-size block of LOGICAL (virtual) memory
  FRAME = fixed-size block of PHYSICAL memory (RAM)
  PAGE SIZE = FRAME SIZE (always equal — fundamental rule!)

PAGE OFFSET BITS (MEMORIZE ALL):
  ┌────────────────────────────────────────────────────────────┐
  │  Page Size     │  2^n = Size   │  Offset Bits  │           │
  │  ─────────────────────────────────────────────           │
  │  1 KB (1024)   │  2¹⁰ = 1024  │    10 bits    │           │
  │  2 KB (2048)   │  2¹¹ = 2048  │    11 bits    │           │
  │  4 KB (4096)   │  2¹² = 4096  │    12 bits    │ ← MOST    │
  │  8 KB (8192)   │  2¹³ = 8192  │    13 bits    │   TESTED  │
  │  16 KB         │  2¹⁴         │    14 bits    │           │
  └────────────────────────────────────────────────────────────┘
  ★ 4KB page → 12-bit offset ← single most tested paging fact in BPSC

ADDRESS TRANSLATION:
  Logical address = [Page Number p | Offset d]
  Physical address = [Frame Number f | Offset d]
  OFFSET d is NEVER changed during translation — only p→f

TLB (Translation Lookaside Buffer):
  ★ TLB = organized as ASSOCIATIVE CACHE ← TRE 1.0 exact PYQ phrase
  ★ TLB hit  = 1 memory access (fast — frame from TLB)
  ★ TLB miss = 2 memory accesses (page table in RAM + data)
  ★ TLB = parallel (associative) lookup — all entries searched simultaneously
  ★ TLB = near/inside CPU; Page Table = in MAIN MEMORY (RAM)

PAGE FAULT:
  Valid bit = 0 → page NOT in RAM → PAGE FAULT interrupt raised
  OS loads page from SWAP SPACE (disk) → updates page table → restarts instruction
  Page fault is EXPENSIVE (disk access = millions of ns)

INTERNAL FRAGMENTATION:
  = Wasted space INSIDE last allocated page
  = Paging CAUSES internal fragmentation
  = Paging ELIMINATES external fragmentation
  Smaller page size → less internal fragmentation (but larger page table)

BELADY'S ANOMALY:
  = More frames → MORE page faults (in FIFO replacement only!)
  = LRU and OPT do NOT suffer from Belady's anomaly

DEMAND PAGING:
  = Pages loaded ONLY when accessed (on page fault)
  = How modern OS (Linux, Windows) actually works

INVERTED PAGE TABLE:
  = Indexed by FRAME NUMBER (not page number)
  = ONE table for entire system (not one per process)

EAT (Effective Access Time with TLB):
  EAT = h × m + (1-h) × 2m  (h=hit ratio, m=RAM access time)
  Example: h=90%, m=100ns → EAT = 0.9×100 + 0.1×200 = 110 ns
```

---

## 🔷 UNIT C: SEGMENTATION + FRAGMENTATION + VIRTUAL MEMORY (Day 70)

```
SEGMENTATION:
════════════════════════════════════════════════════════════════════
  = Variable-size segments (code, data, stack, heap)
  = Each segment: BASE (starting physical address) + LIMIT (size)

  ★ SEGMENT BASE = STARTING PHYSICAL ADDRESS ← direct PYQ phrase
  ★ SEGMENT LIMIT = SIZE of segment (NOT an address)
  ★ Segment fault = offset ≥ Limit (access beyond boundary)
  Physical address = Segment Base + Offset (only if offset < Limit)

PAGING vs SEGMENTATION:
  PAGING:       FIXED size; NO external frag; YES internal frag
  SEGMENTATION: VARIABLE size; YES external frag; NO internal frag

FRAGMENTATION (THE PROBLEM, NOT A TECHNIQUE):
  ★ Fragmentation = PROBLEM — NEVER say "technique" or "solution"!
  ← THIS IS A DIRECT BPSC PYQ TRAP: students say "fragmentation is a technique"

  INTERNAL FRAGMENTATION:
    = Wasted space INSIDE allocated block (paging, fixed partitions)
    = Allocated but unused memory
    = Solution: smaller page/block size

  EXTERNAL FRAGMENTATION:
    = Free memory exists but is SCATTERED non-contiguously
    = Process can't load despite total free memory being sufficient
    = Solution: COMPACTION or PAGING

COMPACTION:
  ★ Shifts ALL active processes to ONE END of memory
  ★ ALL free memory consolidates into ONE SINGLE LARGE BLOCK ← exact phrase
  ★ Solution to EXTERNAL fragmentation
  ★ EXPENSIVE: must copy all processes + update all addresses
  ★ PAGING is PREFERRED over compaction (no copying needed)

VIRTUAL MEMORY:
  = Process can execute even if LARGER than available physical RAM
  = Only ACTIVE pages need to be in RAM (rest on disk = swap space)
  = Linux: swap partition; Windows: pagefile.sys

THRASHING:
  ★ = EXCESSIVE PAGING ACTIVITY ← exact BPSC PYQ phrase
  ★ Process spends MORE TIME swapping pages than executing
  ★ Cause: too many processes, too few frames (working set doesn't fit in RAM)
  ★ CPU utilization DROPS SHARPLY when thrashing begins
  ★ Solution: Working Set Model / Page Fault Frequency / reduce multiprogramming

BUFFER REGISTERS:
  ★ = Overcome the DIFFERENCE IN DATA TRANSFER SPEED between devices ← exact phrase
  ★ Fast device (CPU) writes to buffer → continues other work
  ★ Slow device (disk) reads from buffer at its own pace
  ★ Buffer ≠ Cache: Buffer = data in transit (speed mismatch); Cache = stores for reuse

MEMORY-MAPPED I/O:
  ★ I/O and memory SHARE THE SAME address space ← TRE 1.0 exact PYQ
  ★ Uses normal LOAD/STORE instructions (no special IN/OUT needed)
  ★ I/O-mapped I/O = SEPARATE address spaces + special IN/OUT instructions
```

---

## 🔷 UNIT D: DISK SCHEDULING (Day 71)

```
DISK STRUCTURE:
════════════════════════════════════════════════════════════════════
  SECTOR   = smallest unit of storage (typically 512 bytes or 4KB)
  TRACK    = concentric circle on platter
  CYLINDER = same track number across ALL platters
  SEEK TIME = head moves to correct TRACK = MOST significant time component

DISK SCHEDULING GOAL: Minimize TOTAL HEAD MOVEMENT (seek time)
FORMULA: Total = Σ |position[i+1] - position[i]| (sum of absolute differences)

THE STANDARD BPSC PROBLEM:
  Requests: 98, 183, 37, 122, 14, 124, 65, 67 | Head: 53 | Disk: 0-199

  ┌──────────────────────────────────────────────────────────────┐
  │ ALGORITHM  │ TOTAL MOVEMENT │  KEY FACT                     │
  ├────────────┼────────────────┼───────────────────────────────┤
  │ FCFS       │ 640 cylinders  │ Most fair, WORST performance   │
  │ SSTF       │ 236 cylinders  │ Best performance, STARVATION   │
  │ SCAN       │ 331 cylinders  │ ELEVATOR ALGORITHM             │
  │ C-SCAN     │ 382 cylinders  │ More UNIFORM wait times        │
  │ LOOK       │ 299 cylinders  │ SCAN to last request, not end  │
  │ C-LOOK     │ 322 cylinders  │ C-SCAN to first request        │
  └──────────────────────────────────────────────────────────────┘

★ FCFS total = 640 ← memorize for BPSC
★ SSTF = best performance BUT STARVATION possible ← most tested weakness
★ SCAN = ELEVATOR ALGORITHM ← must know nickname
★ LOOK = SCAN but only to last REQUEST (not disk end) = better than SCAN
★ C-SCAN = one direction only → JUMP back → more UNIFORM wait times
★ Large-to-small performance: SSTF < LOOK < C-LOOK < SCAN < C-SCAN < FCFS

STARVATION: SSTF (yes, far requests may never be served)
NO STARVATION: FCFS, SCAN, C-SCAN, LOOK, C-LOOK (all sweep entire disk)
SSD: NO seek time or rotational latency (no moving parts → disk scheduling less critical)
```

---

## 🔷 UNIT E: I/O MANAGEMENT + FILE SYSTEMS (Day 72)

```
THREE I/O METHODS — MASTER COMPARISON:
════════════════════════════════════════════════════════════════════

  ┌────────────────────────────────────────────────────────────────┐
  │ METHOD          │ CPU ROLE              │ INTERRUPTS │ BEST FOR│
  ├─────────────────┼───────────────────────┼────────────┼─────────┤
  │ Polling         │ Busy-wait loop        │ 0          │ Fast    │
  │ (Programmed I/O)│ checks STATUS FLAGS   │            │ devices │
  │                 │ ← BPSC exact phrase   │            │         │
  ├─────────────────┼───────────────────────┼────────────┼─────────┤
  │ Interrupt-driven│ Device notifies CPU   │ 1 per byte │ Medium  │
  │ I/O             │ CPU does other work   │            │ speed   │
  ├─────────────────┼───────────────────────┼────────────┼─────────┤
  │ DMA             │ BYPASSES CPU          │ 1 per BLOCK│ Fast/   │
  │                 │ DMA controller does   │ ← not byte │ large   │
  │                 │ entire transfer       │            │ transfers│
  └────────────────────────────────────────────────────────────────┘

★ Polling = Program-controlled I/O = REPEATEDLY CHECKS STATUS FLAGS ← TRE 1.0 PYQ
★ DMA = BYPASSES CPU ← key phrase; only 1 interrupt per block
★ Cycle Stealing = DMA takes memory bus temporarily from CPU

ADDRESS SPACE (I/O):
★ Memory-mapped I/O = SHARED address space (I/O + memory together) ← TRE 1.0 PYQ
★ I/O-mapped I/O   = SEPARATE address spaces; uses IN/OUT instructions

BUS:
★ PCI bus = EXTENDS CONNECTIVITY OF PROCESSOR BUS ← BPSC exact PYQ phrase
★ PCI = Peripheral Component Interconnect
★ USB = Universal Serial Bus

SPOOLING:
  = Simultaneous Peripheral Operations OnLine
  = Disk-based queue (e.g., printer spool)
  = Processes don't wait for slow printer → dump to spool → continue

FILE SYSTEMS:
  ★ Secondary memory = LOGICAL organization ← BPSC PYQ
  ★ File system types: NTFS, FAT32, HFS+ = ALL VALID ← BPSC PYQ
  ★ File operations: Create, Delete, Rename = ALL VALID ← BPSC PYQ
    (not just read/write — all operations are valid)
  
  NTFS:  Windows standard; journaling ✓; encryption ✓; files >4GB ✓
  FAT32: Max file size = 4GB (cannot store files >4GB!) ← key limitation
  ext4:  Linux standard; journaling ✓
  HFS+:  macOS (older); replaced by APFS

  FILE ALLOCATION:
  Contiguous: consecutive blocks; fast; EXTERNAL fragmentation problem
  Linked:     linked list; no frag; SLOW random access ← main weakness
  Indexed:    index block; good random access; inode in Unix/Linux

  JOURNALING = log of changes BEFORE making them → crash recovery
  FAT32 does NOT have journaling ← crash risk
```

---

## 🔷 UNIT F: THREADS + CPU SCHEDULING + DEADLOCKS (Day 73)

```
THREADS — #1 BPSC PYQ PAIR (memorize exact phrasing):
════════════════════════════════════════════════════════════════════

★ Threads SHARE:      CODE SECTION + DATA SECTION ← exact BPSC phrase
★ Threads DON'T SHARE: STACK (each has OWN STACK) ← exact BPSC phrase
  Also own: Program Counter, CPU Registers, Thread ID

WHY own stack: Thread's function calls are independent →
  stacks cannot be shared or return addresses get overwritten → crash

CONTEXT SWITCH:
  = SAVE state of running process (into PCB) + LOAD state of next process
  = During switch: NO useful work done (pure overhead)
  = Thread switch FASTER than process switch (shared address space, no TLB flush)

════════════════════════════════════════════════════════════════════

CPU SCHEDULING — FORMULAS (MUST KNOW):
  TAT = CT − AT                  (Turnaround = Completion − Arrival)
  WT  = TAT − BT = (CT−AT) − BT  (Waiting = Turnaround − Burst)
  ← Common trap: students write WT = CT − BT (WRONG!)

ALGORITHM MASTER TABLE:
  ┌────────────────────────────────────────────────────────────────┐
  │ ALGORITHM    │ PREEMPTIVE? │ STARVATION? │ KEY WEAKNESS       │
  ├──────────────┼─────────────┼─────────────┼────────────────────┤
  │ FCFS         │ NO          │ NO          │ CONVOY EFFECT      │
  │ SJF          │ NO          │ YES         │ Starvation long    │
  │ SRTF         │ YES         │ YES         │ Complex, starvation│
  │ Priority     │ Both        │ YES         │ Starvation→AGING   │
  │ Round Robin  │ YES (always)│ NO          │ High TAT vs SJF    │
  └────────────────────────────────────────────────────────────────┘

★ SRTF = optimal minimum average waiting time (preemptive SJF)
★ FCFS = Convoy Effect ← named weakness
★ SJF/Priority starvation → AGING = solution
★ RR: Large TQ → degenerates to FCFS ← PYQ trap
★ RR: NO starvation (rotation = fair for everyone)
★ RR = standard algorithm for TIME-SHARING OS

════════════════════════════════════════════════════════════════════

DEADLOCKS — 4 CONDITIONS (ALL must hold simultaneously):
  ┌────────────────────────────────────────────────────────────────┐
  │ 1. MUTUAL EXCLUSION  = resource non-sharable (1 at a time)    │
  │ 2. HOLD AND WAIT     = holds one + waits for more             │
  │ 3. NO PREEMPTION     = can't forcibly take resource from proc  │
  │ 4. CIRCULAR WAIT     = circular chain P1→P2→P3→P1            │
  └────────────────────────────────────────────────────────────────┘

  Memory trick: "My House Needs Cleaning" = M-H-N-C

DEADLOCK PREVENTION (break one condition):
  Circular Wait = MOST PRACTICAL: resource ordering (increasing numbers)
  Hold & Wait   = request all at once; or release before requesting new

DEADLOCK STRATEGIES:
  Prevention: structurally eliminate one condition
  Avoidance:  BANKER'S ALGORITHM → check SAFE STATE before granting
  Detection:  allow deadlocks; detect cycles; kill/preempt to recover
  Ostrich:    IGNORE IT ← what real OS (Linux, Windows) actually use!

★ Banker's Algorithm = deadlock AVOIDANCE (checks SAFE STATE)
★ Ostrich Algorithm = IGNORE deadlocks = used by most real OS

OTHER:
★ Thrashing = EXCESSIVE PAGING ACTIVITY (not scheduling related)
★ Aging = STARVATION solution (gradually increase priority)
★ Binary semaphore = 0 or 1 = MUTEX (for critical section)
★ Race condition = shared data + result depends on execution ORDER
```

---

## 📊 OS COMPLETE MASTER TRAP TABLE — ALL 35 TRAPS

```
ALL OS PYQ TRAPS — ONE TABLE:
════════════════════════════════════════════════════════════════════

#   TOPIC                    CORRECT FACT                    TRAP
────────────────────────────────────────────────────────────────────
1   Time-sharing OS          BEGINNING OF COMPUTER COMMS     "Batch OS"
                             ← TRE 1.0 exact PYQ
2   Memory interrupt         DOES NOT EXIST as interrupt type Students mark it valid
3   Fragmentation            = PROBLEM (not technique!)       "technique" or "solution"
4   Compaction result        ALL FREE MEMORY = ONE BLOCK      "many smaller blocks"
5   Compaction solves        EXTERNAL fragmentation           "internal frag"
6   4KB page offset          12 bits (2¹²=4096)              10 or 16 bits
7   8KB page offset          13 bits (2¹³=8192)              12 or 14 bits
8   1KB page offset          10 bits (2¹⁰=1024)              8 or 12 bits
9   TLB organization         ASSOCIATIVE CACHE               "direct-mapped cache"
10  TLB hit                  1 memory access                  "2 accesses"
11  TLB miss                 2 memory accesses                "1 access"
12  Offset in translation    NEVER changes                    "offset also changes"
13  Paging fragmentation     INTERNAL only (last page)        "external" or "both"
14  Segmentation frag        EXTERNAL only (variable sizes)   "internal" or "both"
15  Segment base             STARTING PHYSICAL ADDRESS        "segment size"
16  Segment limit            SIZE of segment                  "ending address"
17  Thrashing                EXCESSIVE PAGING ACTIVITY        "CPU overload"
18  Buffer registers         OVERCOME SPEED DIFFERENCE        "cache" or "increases speed"
19  Virtual memory           Process LARGER than RAM can run  "replaces RAM"
20  Secondary memory org     LOGICAL                          "physical" or "structural"
21  Memory-mapped I/O        SHARED address space             "separate address space"
22  Polling = ?              PROGRAM-CONTROLLED I/O           "interrupt-driven I/O"
23  Polling does?            CHECKS STATUS FLAGS repeatedly   "sends interrupt"
24  DMA does?                BYPASSES CPU for data transfer   "needs CPU per byte"
25  DMA interrupts           1 per BLOCK (not per byte)       "1 per byte"
26  PCI bus                  EXTENDS PROCESSOR BUS            "extends memory bus"
27  FAT32 max file size      4 GB                             "unlimited" or "2TB"
28  File ops: rename?        YES, VALID operation             "not a valid op"
29  FCFS disk                SUM OF ABSOLUTE MOVEMENTS        "product" or "sum of positions"
30  FCFS = 640               For standard BPSC problem        Other numbers
31  SSTF weakness            STARVATION                       "thrashing" or "deadlock"
32  SCAN nickname            ELEVATOR ALGORITHM               "circular scan"
33  Threads share            CODE + DATA section              "everything" or "nothing"
34  Thread stack             OWN STACK (NOT shared)           "shared stack"
35  RR + large TQ            Degenerates to FCFS              "always better than FCFS"
36  Deadlock needs           ALL 4 conditions simultaneously  "any 1 condition"
37  Banker's Algorithm       Deadlock AVOIDANCE               "prevention" or "detection"
38  Ostrich Algorithm        IGNORE deadlocks = real OS use   "Banker's used by real OS"
39  TAT formula              CT − AT                          "CT − BT" (WRONG!)
40  WT formula               TAT − BT = (CT−AT)−BT           "CT − BT" (WRONG!)
41  SRTF optimal?            YES, minimum avg wait time       "FCFS is optimal"
42  Belady's anomaly         FIFO replacement only            "all algorithms"
43  Inverted page table      Indexed by FRAME NUMBER         "page number"
44  Aging solves             STARVATION (not deadlock!)       "aging solves deadlock"
────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS COMPLETE REVISION
## 🏛️ Full GS Master Revision — All Topics Covered in Weeks 1–11

---

## 🔷 GS UNIT A: MATHEMATICS SHORTCUTS (8 Questions Every Paper)

```
PROFIT & LOSS (appears in EVERY paper):
════════════════════════════════════════════════════════════════════
  Profit%  = (Profit / CP) × 100
  Loss%    = (Loss / CP) × 100
  SP = CP × (1 + Profit%/100)  or  CP × (1 − Loss%/100)
  CP = SP × 100/(100 + Profit%)  or  SP × 100/(100 − Loss%)

  SHORTCUT — Mark-up with discount:
  Net profit% = M% − D% − (M% × D%)/100
  where M = markup%, D = discount%

  EXAMPLES:
  Buy at ₹80, Sell at ₹100 → Profit = ₹20, Profit% = (20/80)×100 = 25%
  Buy at ₹100, Sell at ₹80 → Loss = ₹20, Loss% = (20/100)×100 = 20%

════════════════════════════════════════════════════════════════════

RATIO & PROPORTION (every paper):
  a:b = c:d → ad = bc (cross multiplication)
  Mean proportional of a and b = √(ab)
  Third proportional: if a:b = b:x → x = b²/a

WORK & TIME (TRE 1.0 and 2.0):
  Work rate = 1/(days to complete)
  If A takes a days and B takes b days:
  Combined rate = 1/a + 1/b
  Together they finish in: T = ab/(a+b) days

SPEED, DISTANCE, TIME:
  D = S × T  (Distance = Speed × Time)
  Average speed for two equal distances at speeds S1 and S2:
    = 2S1S2/(S1+S2)  (harmonic mean — NOT arithmetic mean!)
  Relative speed: same direction = |S1−S2|; opposite = S1+S2

PERCENTAGES:
  X% of Y = (X/100) × Y
  Successive % changes: (1+a/100)(1+b/100) − 1
  Example: 10% rise then 10% fall = (1.1)(0.9) = 0.99 = 1% net loss

FRACTIONS & DECIMALS:
  Common fractions to memorize:
  1/3 = 0.333...   1/6 = 0.1667   1/7 = 0.1428   1/8 = 0.125
  1/9 = 0.111...   1/11 = 0.0909  3/8 = 0.375     5/8 = 0.625

MENSURATION (TRE 3.0):
  Circle: Area = πr², Circumference = 2πr
  Cylinder: TSA = 2πr(r+h), Volume = πr²h  ← TRE 3.0 PYQ
  Sphere: SA = 4πr², Volume = (4/3)πr³
  Cone: LSA = πrl, TSA = πr(r+l), Volume = (1/3)πr²h
  Triangle: Area = (1/2)×base×height; Heron's: √[s(s-a)(s-b)(s-c)]
  Rectangle: Area = l×b, Perimeter = 2(l+b)

STATISTICS (TRE 2.0):
  Mean = Σx/n
  If every value increased by k → new mean = old mean + k
  If every value multiplied by k → new mean = old mean × k
  Median: middle value (sorted)
  Mode: most frequent value
```

---

## 🔷 GS UNIT B: SCIENCE — PHYSICS + BIOLOGY (8 Questions per Paper)

```
PHYSICS — PYQ-TESTED FACTS:
════════════════════════════════════════════════════════════════════

ELECTRICAL:
  Ohm's Law:          V = IR
  Power:              P = VI = I²R = V²/R  ← P = I²R is most tested
  Resistors in series:   R_total = R1 + R2 + R3 (sum)
  Resistors in parallel: 1/R_total = 1/R1 + 1/R2 + 1/R3
  Parallel combination of equal resistors (n resistors each R): R_total = R/n

OPTICS:
  Convex lens in water: still CONVEX, but focal length INCREASES ← TRE PYQ
  Frequency of light: UNCHANGED when light changes medium ← TRE PYQ
  (Wavelength and speed change in different media, but NOT frequency)
  Concave mirror: focal length = R/2 (R = radius of curvature)
  Snell's law: n1 sinθ1 = n2 sinθ2

MECHANICS:
  Bernoulli's principle: faster fluid = lower pressure ← TRE PYQ (spray bottles)
  Stefan's law: E ∝ T⁴ (blackbody radiation) ← TRE PYQ
  Newton's laws: F = ma (second law), equal and opposite (third law)

ATOMIC/MODERN PHYSICS:
  Speed of electron in 1st orbit of hydrogen: v = c/137 ← TRE PYQ exact fact
  (c = speed of light, 137 = fine structure constant ≈ 1/α)

MEASUREMENT:
  Isotropic light source: intensity = candela; flux = lumen ← TRE PYQ
  Light scattering: fog scatters all visible light → appears opaque ← TRE PYQ

════════════════════════════════════════════════════════════════════

BIOLOGY — PYQ-TESTED FACTS:
════════════════════════════════════════════════════════════════════

PHYSIOLOGY:
  Diaphragm in normal respiration: FLATTENS (moves down) ← TRE PYQ
  Immunity: LYMPHOCYTES are most important cells ← TRE PYQ
  Vas deferens: MALE reproductive organ (NOT female) ← PYQ trap
  Antacid: medicine for INDIGESTION (neutralizes excess stomach acid) ← PYQ

PLANTS:
  Ginger: UNDERGROUND STEM (rhizome) — has nodes and internodes ← TRE PYQ
  (NOT a root — roots don't have nodes and internodes)
  Photoperiodism: discovered by GARNER and ALLARD ← TRE PYQ
  Anther: contains POLLEN GRAINS ← PYQ (part of stamen in flower)
  Asexual reproduction by BUDDING: YEAST ← TRE PYQ

ECOLOGY:
  Silent Valley (Kerala): rare flora and fauna ← TRE PYQ
  Biodiversity hotspot in India: Indo-Burma region, Western Ghats + Sri Lanka,
  Himalaya, Sundaland

CLASSIFICATION:
  Virus: non-cellular; DNA or RNA; uses host cell machinery
  Bacteria: prokaryote; no nucleus; cell wall present
  Fungi: eukaryote; cell wall = chitin; decomposers
```

---

## 🔷 GS UNIT C: MODERN INDIAN HISTORY (8 Questions per Paper — Bihar Focus)

```
BPSC HIGH-FREQUENCY HISTORY FACTS:
════════════════════════════════════════════════════════════════════

ORGANIZATIONS — FOUNDING FACTS (PYQ-tested):
  INC (1885):           Founded by A.O. HUME; First president: W.C. BANERJEE
                        ← First INC president = W.C. Bonnerjee (also spelled Banerjee)
  Muslim League (1906): Founded at Dhaka
  Ghadar Party:         Founded in USA (San Francisco, 1913) ← TRE PYQ: USA!
  Abhinav Bharat:       Founded in LONDON by V.D. SAVARKAR ← TRE PYQ: London!
  Anushilan Samiti (Patna, 1913): Founded by SACHINDRA NATH SANYAL ← Bihar PYQ
  Bihar Provincial Congress Committee: Founded 1908; HQ Patna ← Bihar PYQ
  Bihar Socialist Party: Founded by PHULAN PRASAD VARMA + JAYAPRAKASH NARAYAN ← Bihar

REVOLT OF 1857:
  First called "War of Independence" by: V.D. SAVARKAR ← TRE PYQ
  Bihar: Led by KUNWAR SINGH (Jagdishpur, Bhojpur)

SPECIFIC LEADERS:
  "Grand Old Man of India":        DADABHAI NAOROJI ← TRE PYQ
  "Punjab Kesari":                  LALA LAJPAT RAI
  "Nightingale of India":           SAROJINI NAIDU
  Bardoli Satyagraha (1928):       SARDAR VALLABHBHAI PATEL ← TRE PYQ
  Home Rule Movement NOT associated with: SAROJINI NAIDU ← TRE PYQ trap
  (Home Rule = Tilak + Annie Besant; Sarojini Naidu ≠ Home Rule)

SESSIONS AND EVENTS:
  INC Gaya Session 1922:       President: CHITTARANJAN DAS (C.R. Das) ← Bihar PYQ
  Jallianwala Bagh 1919:       Viceroy: LORD CHELMSFORD ← PYQ (not Dyer's superior)
  AIKS Bihar 1936:             SWAMI SAHAJANAND SARASWATI ← Bihar farmers movement
  Birsa Munda:                 Commander-in-Chief was GAYA MUNDA ← Bihar tribal PYQ
  First Bhojpuri film:         "GANGA MAIYA TOHE PIYARI CHADHAIBO" (1963) ← Bihar PYQ
  Anandamath (Bankim Chandra): Mentions SANNYASI REVOLT ← TRE PYQ

CHAMPARAN SATYAGRAHA 1917 (HIGHEST BPSC PRIORITY):
  Gandhi arrived Motihari: April 15, 1917
  Who brought Gandhi: RAJ KUMAR SHUKLA (illiterate indigo farmer)
  Who received Gandhi in Patna: DR. RAJENDRA PRASAD
  Tinkathia system: 3/20 of land for forced indigo cultivation
  First Satyagraha IN INDIA (not first ever — South Africa was 1906)
  Champaran Agrarian Act 1918: Tinkathia ABOLISHED + 25% REFUND

MOVEMENTS:
  NCM (1920-22):  Feb 5, 1922 = Chauri Chaura (UP) → Gandhi suspended NCM
  CDM (1930):     Dandi March Mar 12; Gandhi makes salt Apr 6; Gandhi-Irwin Pact Mar 5, 1931
  QIM (1942):     Aug 8 = Resolution; Aug 9 = August Kranti Diwas; Gandhi arrested
                  JP escaped HAZARIBAGH JAIL Nov 9, 1942 ← Bihar

RAJENDRA PRASAD (BIHAR — ULTRA HIGH PRIORITY):
  Born: Dec 3, 1884, ZERADEI, SIWAN, BIHAR
  Founded Bihar Vidyapeeth: 1921 (NCM)
  CA President: Dec 9, 1946
  1st President of India: Jan 26, 1950
  Bharat Ratna: 1962; Died: Feb 28, 1963, Sadaqat Ashram, Patna
```

---

## 🔷 GS UNIT D: GEOGRAPHY — INDIA + BIHAR (6–8 Questions per Paper)

```
BIHAR GEOGRAPHY — DIRECT BPSC PYQ FACTS:
════════════════════════════════════════════════════════════════════
  Bihar population = 8.58% of India's total ← TRE PYQ direct
  Max paddy production in Bihar: ROHTAS DISTRICT ← TRE PYQ
  Max silk textile in Bihar: BHAGALPUR DISTRICT ← TRE PYQ (silk city)
  Kosi = "SORROW OF BIHAR" (constantly shifting course, devastating floods)
  Gandak joins Ganga at: HAJIPUR (Vaishali)
  Sone = RIGHT BANK tributary of Ganga (peninsular origin)
  ~76% of North Bihar = flood-prone
  National Waterway 1 = GANGA (Prayagraj to Haldia) — Patna on NW-1

INDIA GEOGRAPHY — PYQ-TESTED:
  Maximum urbanization state: GOA ← TRE PYQ
  Black soil found in: KARNATAKA + GUJARAT (BOTH) ← TRE PYQ
  Malnad region: KARNATAKA PLATEAU ← TRE PYQ
  South Peninsular Upland: Part of GONDWANA LAND ← TRE PYQ
  Highest peak Eastern Ghats: MAHENDRAGIRI ← TRE PYQ
  East-West Corridor: SILCHAR to PORBANDAR ← TRE PYQ
  Stalactites/Stalagmites: formed by UNDERGROUND WATER (caves) ← PYQ
  Trewartha's classification of India's climate: SUBTROPICAL MONSOON ← PYQ
  SW Monsoon withdrawal from Hyderabad: 1st OCTOBER ← PYQ exact date
  Mawsynram (Meghalaya): HIGHEST average rainfall in the WORLD
  Sundarbans: World's LARGEST DELTA + World's LARGEST MANGROVE FOREST

RIVERS:
  Longest river in India: GANGA (~2525 km)
  Longest peninsular river: GODAVARI = "Vriddha Ganga" / "Dakshin Ganga"
  Narmada: flows WEST through RIFT VALLEY → ESTUARY (not delta)
  Brahmaputra: TSANGPO in Tibet; widest river; Majuli = world's largest river island
  Punjab = "land of 5 rivers": Jhelum, Chenab, Ravi, Beas, Sutlej
  Devprayag: BHAGIRATHI + ALAKNANDA = GANGA
  Prayagraj: GANGA + YAMUNA = Triveni Sangam
  Damodar = "Sorrow of Bengal"

DAMS:
  Tehri Dam: TALLEST in India (260m, Bhagirathi, Uttarakhand)
  Hirakud Dam: LONGEST in India (Mahanadi, Odisha)
  Bhakra Nangal: "Temples of Modern India" (Nehru) — Sutlej river
  Sardar Sarovar: Narmada; Medha Patkar led Narmada Bachao Andolan

IRRIGATION:
  Most common method in India: TUBE WELL / WELL irrigation
  Most common in South India: TANK irrigation (Deccan plateau)
  Most efficient: DRIP irrigation
```

---

## 🔷 GS UNIT E: CONSTITUTION + LOCAL GOVERNMENT (HIGH FREQUENCY)

```
CONSTITUTION ESSENTIALS:
════════════════════════════════════════════════════════════════════
  CA first met: Dec 9, 1946 | Adopted: Nov 26, 1949 | In force: Jan 26, 1950
  CA President: RAJENDRA PRASAD (Bihar!) | Drafting Committee: B.R. AMBEDKAR
  
  "Socialist" + "Secular" in Preamble: added by 42ND AMENDMENT (1976)
  Art 21: Right to Life (most litigated; includes right to privacy since 2017)
  Art 21A: Right to Education (6–14 yrs) — added by 86th Amendment (2002)
  Art 32: "Heart and Soul" (Ambedkar) = Right to Constitutional Remedies
  Art 17: Abolition of UNTOUCHABILITY
  Art 44: Uniform Civil Code (DPSP)

WRITS: Habeas Corpus ("you may have the body") | Mandamus ("we command")
       Certiorari | Prohibition | Quo Warranto ("by what authority")

AMENDMENTS:
  42nd (1976): Socialist + Secular in Preamble; Fundamental Duties (Art 51A)
  44th (1978): Right to Property removed from FRs (now Art 300A — legal right)
  73rd (1992): Panchayati Raj — Part IX + 11th Schedule (29 subjects)
  74th (1992): Urban Local Bodies — Part IX-A + 12th Schedule (18 subjects)
  86th (2002): Art 21A — Right to Education (6–14 years)

PANCHAYATI RAJ (73rd Amendment):
  Effective: APRIL 24, 1993 = National Panchayati Raj Day
  3 tiers: Gram Panchayat → Panchayat Samiti → Zila Parishad
  Women reservation: ≥ 1/3 seats | Bihar: 50% (more than minimum)
  Elections: STATE ELECTION COMMISSION (not ECI)
  Dissolved: fresh election within 6 MONTHS
  First state: RAJASTHAN (Oct 2, 1959, Nagaur, PM Nehru inaugurated)
  Balwant Rai Mehta (1957): first to recommend 3-tier PRIs
  L.M. Singhvi (1986): first to recommend CONSTITUTIONAL STATUS for PRIs
  11th Schedule: 29 subjects for panchayats

URBAN LOCAL BODIES (74th Amendment):
  3 types: Nagar Panchayat → Municipal Council → Municipal Corporation
  Mayor = elected head | Municipal Commissioner = IAS officer (real executive)
  12th Schedule: 18 subjects for urban bodies
```

---

## 🔷 GS UNIT F: EDUCATION POLICY (Day 73)

```
NEP 2020 RAPID REVISION:
════════════════════════════════════════════════════════════════════
  Approved: July 29, 2020 | Drafted by: K. KASTURIRANGAN COMMITTEE
  Replaced: NEP 1986 | New Structure: 5+3+3+4 (not 10+2)
    5 = Foundational (pre-school to Class 2, Age 3–8)
    3 = Preparatory  (Class 3–5, Age 8–11)
    3 = Middle       (Class 6–8, Age 11–14) ← CODING from Class 6
    4 = Secondary    (Class 9–12, Age 14–18)
  Mother tongue medium: at least CLASS 5 (pref. till 8)
  UG = 4 YEARS: 1yr=Certificate, 2yr=Diploma, 4yr=Bachelor's+Research
  MPhil ABOLISHED | ABC = Academic Bank of Credits
  PARAKH = National Assessment Centre
  HECI replaces UGC | DIKSHA = digital platform
  Board exams: TWICE per year | GDP spend target: 6%
  GER higher education target: 50% by 2035

RTE ACT 2009:
  Free education age: 6 TO 14 years | Basis: Article 21A (86th Amend. 2002)
  Private school EWS: 25% reservation
  PTR Primary (Cl 1–5): 1:30 | Upper Primary (Cl 6–8): 1:35
  Education = CONCURRENT LIST (moved by 42nd Amendment 1976)
  NCTE = regulates teacher education (most relevant for BPSC!)
  Bihar population = 8.58% | Bihar literacy = ~63.82%
```

---
---

# PART 3: 50 PRACTICE MCQs — PYQ STYLE
## 📝 25 OS PYQ MCQs + 25 GS PYQ MCQs

---

### COMPUTER SCIENCE — 25 OS PYQ MCQs

---

**Q1.** Which type of Operating System marks the BEGINNING OF COMPUTER COMMUNICATIONS?
(A) Batch Operating System
(B) Distributed Operating System
(C) Time-sharing Operating System
(D) More than one of the above
(E) None of the above

---

**Q2.** FRAGMENTATION in memory management is best described as:
(A) A memory management TECHNIQUE used to improve performance
(B) A memory PROBLEM — wasted or unusable memory (internal or external)
(C) A method to compress files for efficient storage
(D) More than one of the above
(E) None of the above

---

**Q3.** COMPACTION in memory management produces:
(A) Multiple equal-sized free blocks distributed throughout RAM
(B) ALL FREE MEMORY consolidated into ONE SINGLE LARGE CONTIGUOUS BLOCK
(C) Separate free blocks for each process's future use
(D) More than one of the above
(E) None of the above

---

**Q4.** The TLB (Translation Lookaside Buffer) is organized as which type of cache?
(A) Direct-mapped cache
(B) Fully set-associative RAM cache
(C) ASSOCIATIVE CACHE (Content Addressable Memory)
(D) More than one of the above
(E) None of the above

---

**Q5.** For a system with PAGE SIZE = 4 KB, how many OFFSET BITS are needed?
(A) 10 bits (2¹⁰ = 1024 = 1 KB)
(B) 14 bits (2¹⁴ = 16 KB)
(C) 12 bits (2¹² = 4096 = 4 KB)
(D) More than one of the above
(E) None of the above

---

**Q6.** THRASHING in an operating system is caused by:
(A) Too many user interface threads running simultaneously
(B) EXCESSIVE PAGING ACTIVITY — process spends more time swapping pages than executing
(C) Buffer overflow in the file system cache
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following resources are SHARED by threads of the SAME PROCESS?
(A) Stack and CPU registers
(B) CODE SECTION and DATA SECTION
(C) Program Counter and Stack
(D) More than one of the above
(E) None of the above

---

**Q8.** Each thread within a process has its OWN separate:
(A) Code section (program instructions)
(B) Heap (dynamically allocated memory)
(C) STACK (call stack with local variables and return addresses)
(D) More than one of the above
(E) None of the above

---

**Q9.** Using FCFS disk scheduling with request queue: 98, 183, 37, 122, 14, 124, 65, 67 and initial head position 53, the TOTAL HEAD MOVEMENT is:
(A) 236 cylinders
(B) 331 cylinders
(C) 640 cylinders
(D) More than one of the above
(E) None of the above

---

**Q10.** MEMORY-MAPPED I/O means that:
(A) I/O device registers occupy a SEPARATE address space from main memory
(B) Main memory pages are mapped to secondary storage (disk)
(C) I/O DEVICES AND MAIN MEMORY SHARE THE SAME ADDRESS SPACE
(D) More than one of the above
(E) None of the above

---

**Q11.** PROGRAM-CONTROLLED I/O is also known as:
(A) DMA (Direct Memory Access)
(B) Interrupt-driven I/O
(C) POLLING — CPU repeatedly checks STATUS FLAGS of device controller
(D) More than one of the above
(E) None of the above

---

**Q12.** BUFFER REGISTERS are used primarily to:
(A) Cache frequently accessed page table entries for faster translation
(B) Permanently store critical system data in fast memory
(C) OVERCOME THE DIFFERENCE IN DATA TRANSFER SPEED between communicating devices
(D) More than one of the above
(E) None of the above

---

**Q13.** The PCI bus (Peripheral Component Interconnect) is used to:
(A) Directly connect the CPU to main memory (RAM)
(B) Connect two processors in a multiprocessor system
(C) EXTEND THE CONNECTIVITY OF THE PROCESSOR BUS to peripheral devices
(D) More than one of the above
(E) None of the above

---

**Q14.** The ORGANIZATION of SECONDARY MEMORY is best described as:
(A) Physical organization (sectors, tracks, cylinders — hardware layout)
(B) Sequential organization (data stored in strict sequence)
(C) LOGICAL organization (files and directories — long-term storage structure)
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following is NOT a valid type of interrupt?
(A) Hardware interrupt
(B) Software interrupt (trap)
(C) Memory interrupt
(D) More than one of the above
(E) None of the above

---

**Q16.** SSTF (Shortest Seek Time First) disk scheduling may suffer from:
(A) Wild back-and-forth head movement causing convoy effect
(B) Going to the disk end even when no request exists there
(C) STARVATION — requests far from the current head may never be served
(D) More than one of the above
(E) None of the above

---

**Q17.** The SCAN disk scheduling algorithm is also known as:
(A) Circular Scan
(B) ELEVATOR ALGORITHM — moves in one direction, reverses at disk end
(C) Priority-based head movement algorithm
(D) More than one of the above
(E) None of the above

---

**Q18.** For DEADLOCK to occur, which set of conditions must ALL hold SIMULTANEOUSLY?
(A) Mutual Exclusion, Starvation, Aging, Priority Inversion
(B) MUTUAL EXCLUSION, HOLD & WAIT, NO PREEMPTION, CIRCULAR WAIT
(C) Hold & Wait, Circular Wait, Race Condition, Thrashing
(D) More than one of the above
(E) None of the above

---

**Q19.** The BANKER'S ALGORITHM is used for:
(A) Deadlock PREVENTION — ensuring one of the four conditions can never hold
(B) Deadlock DETECTION — finding cycles in the resource allocation graph
(C) Deadlock AVOIDANCE — checking for SAFE STATE before granting resources
(D) More than one of the above
(E) None of the above

---

**Q20.** Which CPU scheduling algorithm is used in TIME-SHARING operating systems?
(A) FCFS — First Come First Served
(B) SJF — Shortest Job First
(C) ROUND ROBIN — preemptive, fixed time quantum for each process
(D) More than one of the above
(E) None of the above

---

**Q21.** AGING is the solution to which scheduling problem?
(A) Deadlock — circular wait among processes
(B) Thrashing — excessive page swapping
(C) STARVATION — low-priority processes never getting CPU time
(D) More than one of the above
(E) None of the above

---

**Q22.** The CONVOY EFFECT is a weakness of which scheduling algorithm?
(A) Round Robin (time quantum based)
(B) SRTF (Shortest Remaining Time First)
(C) FCFS — long processes block all shorter processes waiting behind them
(D) More than one of the above
(E) None of the above

---

**Q23.** Common FILE SYSTEM TYPES include which of the following?
(A) Only NTFS is a valid file system
(B) Only FAT32 is used in modern systems
(C) NTFS, FAT32, AND HFS+ are all valid file system types
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following are VALID FILE OPERATIONS in an operating system?
(A) Only READ and WRITE are valid file operations
(B) Only CREATE and DELETE are valid
(C) CREATE, DELETE, AND RENAME are all valid file operations
(D) More than one of the above
(E) None of the above

---

**Q25.** If the TIME QUANTUM in Round Robin scheduling is made very large (exceeding all process burst times), Round Robin behaves like:
(A) Shortest Job First (SJF)
(B) SRTF (Shortest Remaining Time First)
(C) FCFS — each process runs to completion before the next one begins
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 GS PYQ MCQs (History + Geography + Science + Constitution)

---

**Q26.** The GHADAR PARTY was established in:
(A) London, United Kingdom
(B) Berlin, Germany
(C) San Francisco, USA
(D) More than one of the above
(E) None of the above

---

**Q27.** ABHINAV BHARAT was founded by V.D. Savarkar in which city?
(A) Pune, India
(B) Nasik, India
(C) London, United Kingdom
(D) More than one of the above
(E) None of the above

---

**Q28.** The revolt of 1857 was FIRST CALLED "War of Independence" by:
(A) Bal Gangadhar Tilak
(B) V.D. SAVARKAR
(C) Lala Lajpat Rai
(D) More than one of the above
(E) None of the above

---

**Q29.** "GRAND OLD MAN OF INDIA" is the title given to:
(A) Bal Gangadhar Tilak
(B) Gopal Krishna Gokhale
(C) DADABHAI NAOROJI
(D) More than one of the above
(E) None of the above

---

**Q30.** The BARDOLI SATYAGRAHA (1928) was led by:
(A) Mahatma Gandhi
(B) SARDAR VALLABHBHAI PATEL
(C) Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q31.** The HOME RULE MOVEMENT is NOT associated with which leader?
(A) Bal Gangadhar Tilak
(B) Annie Besant
(C) SAROJINI NAIDU ← NOT associated with Home Rule
(D) More than one of the above
(E) None of the above

---

**Q32.** BIHAR's population is approximately what percentage of India's total population?
(A) 5.5%
(B) 8.58%
(C) 11.2%
(D) More than one of the above
(E) None of the above

---

**Q33.** Maximum PADDY PRODUCTION in Bihar is from which district?
(A) Patna
(B) Bhagalpur
(C) ROHTAS DISTRICT
(D) More than one of the above
(E) None of the above

---

**Q34.** Maximum SILK TEXTILE production in Bihar is associated with which district?
(A) Muzaffarpur
(B) BHAGALPUR (called "Silk City of India")
(C) Gaya
(D) More than one of the above
(E) None of the above

---

**Q35.** BLACK SOIL in India is found in which of the following states?
(A) Karnataka only
(B) Gujarat only
(C) BOTH Karnataka AND Gujarat (among others)
(D) More than one of the above
(E) None of the above

---

**Q36.** The MALNAD REGION is associated with which plateau/area?
(A) Deccan Plateau (Maharashtra)
(B) Chota Nagpur Plateau (Jharkhand)
(C) KARNATAKA PLATEAU
(D) More than one of the above
(E) None of the above

---

**Q37.** HIGHEST PEAK of the Eastern Ghats is:
(A) Anai Mudi
(B) Doddabetta
(C) MAHENDRAGIRI
(D) More than one of the above
(E) None of the above

---

**Q38.** The SW MONSOON WITHDRAWS from Hyderabad around which date?
(A) 1st September
(B) 1st OCTOBER
(C) 1st November
(D) More than one of the above
(E) None of the above

---

**Q39.** STALACTITES and STALAGMITES in caves are formed by:
(A) Wind erosion over millions of years
(B) Volcanic lava cooling underground
(C) UNDERGROUND WATER (calcium carbonate deposition from dripping water)
(D) More than one of the above
(E) None of the above

---

**Q40.** The ELECTRICAL POWER dissipated in a resistor is given by which formula?
(A) P = V + IR
(B) P = V²/IR
(C) P = I²R (also P = VI = V²/R)
(D) More than one of the above
(E) None of the above

---

**Q41.** SPEED OF ELECTRON in the first orbit of the hydrogen atom is:
(A) Equal to the speed of light (c)
(B) c/100 (one hundredth of speed of light)
(C) c/137 (approximately 1/137th of speed of light)
(D) More than one of the above
(E) None of the above

---

**Q42.** PHOTOPERIODISM in plants was discovered by:
(A) Gregor Mendel and Charles Darwin
(B) GARNER and ALLARD
(C) Robert Brown and Joseph Lister
(D) More than one of the above
(E) None of the above

---

**Q43.** GINGER is botanically classified as:
(A) A root (modified root for food storage)
(B) AN UNDERGROUND STEM (rhizome) — has nodes and internodes
(C) A bulb (like onion)
(D) More than one of the above
(E) None of the above

---

**Q44.** Which cells are MOST IMPORTANT for the body's IMMUNITY?
(A) Red blood cells (RBCs)
(B) Platelets
(C) LYMPHOCYTES
(D) More than one of the above
(E) None of the above

---

**Q45.** When a CONVEX LENS is placed in WATER (instead of air), which of the following is TRUE?
(A) The lens becomes concave in water
(B) Focal length decreases (becomes more converging)
(C) IT REMAINS CONVEX but the focal length INCREASES (less converging)
(D) More than one of the above
(E) None of the above

---

**Q46.** The words "SOCIALIST" and "SECULAR" were added to the Preamble of the Indian Constitution by:
(A) 44th Amendment (1978)
(B) 86th Amendment (2002)
(C) 42ND AMENDMENT (1976)
(D) More than one of the above
(E) None of the above

---

**Q47.** Dr. B.R. Ambedkar called which Article the "HEART AND SOUL OF THE CONSTITUTION"?
(A) Article 14 (Right to Equality)
(B) Article 21 (Right to Life and Personal Liberty)
(C) ARTICLE 32 (Right to Constitutional Remedies)
(D) More than one of the above
(E) None of the above

---

**Q48.** NATIONAL PANCHAYATI RAJ DAY is celebrated on:
(A) October 2 (Gandhi Jayanti)
(B) January 26 (Republic Day)
(C) APRIL 24 (date 73rd Amendment came into effect in 1993)
(D) More than one of the above
(E) None of the above

---

**Q49.** The state with MAXIMUM URBANIZATION in India is:
(A) Maharashtra
(B) Delhi
(C) GOA
(D) More than one of the above
(E) None of the above

---

**Q50.** BIRSA MUNDA's Commander-in-Chief during the Ulgulan (Great Tumult) revolt was:
(A) Sidhu Murmu
(B) Tilka Manjhi
(C) GAYA MUNDA
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt ALL 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 1  | (C)    | Time-sharing OS = BEGINNING OF COMPUTER COMMUNICATIONS ← TRE 1.0 PYQ |
| 2  | (B)    | Fragmentation = PROBLEM (wasted memory) — NEVER call it a technique! |
| 3  | (B)    | Compaction → ALL FREE MEMORY in ONE SINGLE LARGE BLOCK ← exact phrase |
| 4  | (C)    | TLB = ASSOCIATIVE CACHE (Content Addressable Memory) ← TRE 1.0 PYQ |
| 5  | (C)    | 4KB = 2¹² = 4096 → 12-bit offset ← single most tested paging fact |
| 6  | (B)    | Thrashing = EXCESSIVE PAGING ACTIVITY ← exact BPSC PYQ phrase |
| 7  | (B)    | Threads share CODE SECTION + DATA SECTION ← exact BPSC phrase |
| 8  | (C)    | Each thread has OWN STACK ← exact BPSC phrase (not shared) |
| 9  | (C)    | FCFS total = 640 cylinders (45+85+146+85+108+110+59+2) ← memorize |
| 10 | (C)    | Memory-mapped I/O = I/O + memory SHARE SAME address space ← TRE 1.0 PYQ |
| 11 | (C)    | Polling = Program-controlled I/O = REPEATEDLY CHECKS STATUS FLAGS ← TRE 1.0 |
| 12 | (C)    | Buffer registers = OVERCOME DIFFERENCE IN DATA TRANSFER SPEED ← exact phrase |
| 13 | (C)    | PCI = EXTENDS CONNECTIVITY OF PROCESSOR BUS ← BPSC exact PYQ phrase |
| 14 | (C)    | Secondary memory = LOGICAL organization ← BPSC PYQ |
| 15 | (C)    | "Memory interrupt" DOES NOT EXIST as a valid interrupt type ← PYQ trap |
| 16 | (C)    | SSTF = STARVATION (far requests may never be served) ← key weakness |
| 17 | (B)    | SCAN = ELEVATOR ALGORITHM ← must-know nickname for BPSC |
| 18 | (B)    | ALL 4: Mutual Exclusion + Hold & Wait + No Preemption + Circular Wait |
| 19 | (C)    | Banker's = deadlock AVOIDANCE (checks SAFE STATE before granting) |
| 20 | (C)    | Round Robin = standard algorithm for TIME-SHARING OS ← Day 68 + 73 connection |
| 21 | (C)    | AGING = solution to STARVATION (gradually increases priority) |
| 22 | (C)    | CONVOY EFFECT = FCFS weakness ← named PYQ term |
| 23 | (C)    | NTFS, FAT32, HFS+ = ALL VALID file system types ← BPSC PYQ |
| 24 | (C)    | Create, Delete, Rename = ALL VALID file operations ← BPSC PYQ |
| 25 | (C)    | Large TQ → Round Robin degenerates to FCFS ← direct PYQ trap |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 26 | (C)    | Ghadar Party = founded in USA (San Francisco, 1913) ← TRE PYQ |
| 27 | (C)    | Abhinav Bharat = LONDON (V.D. Savarkar) ← TRE PYQ |
| 28 | (B)    | 1857 first called "War of Independence" by V.D. SAVARKAR ← TRE PYQ |
| 29 | (C)    | "Grand Old Man of India" = DADABHAI NAOROJI ← TRE PYQ |
| 30 | (B)    | Bardoli Satyagraha = SARDAR VALLABHBHAI PATEL (1928) ← TRE PYQ |
| 31 | (C)    | Sarojini Naidu NOT associated with Home Rule ← TRE PYQ trap |
| 32 | (B)    | Bihar = 8.58% of India's population ← BPSC direct PYQ |
| 33 | (C)    | Max paddy in Bihar = ROHTAS DISTRICT ← TRE PYQ |
| 34 | (B)    | Max silk textile in Bihar = BHAGALPUR ← TRE PYQ ("Silk City") |
| 35 | (C)    | Black soil = BOTH Karnataka AND Gujarat ← TRE PYQ (both is correct!) |
| 36 | (C)    | Malnad region = KARNATAKA PLATEAU ← TRE PYQ |
| 37 | (C)    | Highest peak Eastern Ghats = MAHENDRAGIRI ← TRE PYQ |
| 38 | (B)    | SW Monsoon withdraws Hyderabad = 1st OCTOBER ← TRE PYQ exact date |
| 39 | (C)    | Stalactites/Stalagmites = UNDERGROUND WATER (CaCO₃ deposition) ← PYQ |
| 40 | (C)    | P = I²R (also P=VI=V²/R) ← TRE PYQ formula |
| 41 | (C)    | Speed of electron in H-atom 1st orbit = c/137 ← TRE PYQ exact fact |
| 42 | (B)    | Photoperiodism discovered by GARNER and ALLARD ← TRE PYQ |
| 43 | (B)    | Ginger = UNDERGROUND STEM (rhizome) — has nodes+internodes ← TRE PYQ |
| 44 | (C)    | Most important immunity cells = LYMPHOCYTES ← TRE PYQ |
| 45 | (C)    | Convex lens in water = still convex, focal length INCREASES ← TRE PYQ |
| 46 | (C)    | "Socialist" + "Secular" added by 42nd AMENDMENT (1976) ← Constitutional PYQ |
| 47 | (C)    | Art 32 = "Heart and Soul" (Ambedkar) = Right to Constitutional Remedies |
| 48 | (C)    | National Panchayati Raj Day = APRIL 24 (73rd Amendment effective date) |
| 49 | (C)    | Maximum urbanization = GOA ← TRE PYQ |
| 50 | (C)    | Birsa Munda's Commander-in-Chief = GAYA MUNDA ← Bihar tribal PYQ |

---
---

# 🔁 NIGHT REVISION SHEET
## 📌 Day 74 — THE COMPLETE OS MASTER FLASH CARDS

---

### ⚡ OS MASTER REVISION — 44 MUST-KNOW FACTS (All 6 Days)

```
OS TYPES (Day 68):
1.  Time-sharing OS = BEGINNING OF COMPUTER COMMUNICATIONS ← TRE 1.0 exact PYQ
2.  Multi-programming (1 CPU) ≠ Multi-processing (multiple CPUs)
3.  Memory interrupt = DOES NOT EXIST ← PYQ trap
4.  NMI = Non-Maskable Interrupt = cannot be ignored

PAGING (Day 69):
5.  Page size = Frame size (always equal)
6.  4KB page = 12-bit offset (2¹²=4096) ← MOST tested paging fact
8KB page = 13 bits; 1KB page = 10 bits
7.  TLB = ASSOCIATIVE CACHE ← TRE 1.0 exact phrase
8.  TLB hit = 1 memory access; TLB miss = 2 memory accesses
9.  Offset NEVER changes during address translation (only page→frame)
10. Paging: NO external frag; YES internal frag (last page)
11. Belady's anomaly = FIFO replacement ONLY (more frames → more faults)
12. Demand paging = pages loaded ONLY when accessed (page fault)
13. Inverted page table = indexed by FRAME NUMBER (not page number)

SEGMENTATION + VIRTUAL MEMORY (Day 70):
14. Segment BASE = STARTING PHYSICAL ADDRESS ← direct PYQ phrase
15. Segment LIMIT = SIZE of segment (not address)
16. Segmentation: YES external frag; NO internal frag
17. Fragmentation = PROBLEM (NEVER "technique") ← direct PYQ trap
18. Compaction → ALL FREE MEMORY in ONE BLOCK ← exact phrase
19. Compaction solves EXTERNAL fragmentation; EXPENSIVE
20. Thrashing = EXCESSIVE PAGING ACTIVITY ← exact PYQ phrase
21. Buffer registers = OVERCOME DIFFERENCE IN DATA TRANSFER SPEED ← exact phrase
22. Memory-mapped I/O = SHARED address space ← TRE 1.0 exact phrase

DISK SCHEDULING (Day 71):
23. FCFS total = 640 (standard BPSC problem) ← memorize this number
24. SSTF = best performance BUT STARVATION ← most tested weakness
25. SCAN = ELEVATOR ALGORITHM ← exact nickname
26. LOOK = SCAN but to last request (not disk end) = better than SCAN
27. C-SCAN = more UNIFORM wait times than SCAN
28. Formula: Σ |position[i+1] - position[i]| (sum of absolute differences)

I/O + FILE SYSTEMS (Day 72):
29. Polling = Program-controlled I/O = CHECKS STATUS FLAGS ← TRE 1.0 PYQ
30. DMA = BYPASSES CPU; 1 interrupt per BLOCK (not per byte)
31. PCI bus = EXTENDS CONNECTIVITY OF PROCESSOR BUS ← BPSC exact phrase
32. Secondary memory = LOGICAL organization ← BPSC PYQ
33. File systems: NTFS, FAT32, HFS+ = ALL VALID ← BPSC PYQ
34. File operations: Create, Delete, Rename = ALL VALID ← BPSC PYQ
35. FAT32 max file size = 4 GB (cannot store >4GB files)

THREADS + SCHEDULING + DEADLOCKS (Day 73):
36. Threads SHARE: CODE SECTION + DATA SECTION ← exact BPSC phrase
37. Threads DON'T SHARE: STACK (each has OWN STACK) ← exact phrase
38. TAT = CT − AT; WT = TAT − BT = (CT−AT) − BT ← formulas
39. FCFS weakness = CONVOY EFFECT ← named term
40. SRTF = optimal minimum average waiting time
41. Round Robin = PREEMPTIVE; time quantum; NO starvation
42. Large TQ → RR degenerates to FCFS ← PYQ trap
43. Deadlock = ALL 4 conditions: ME + H&W + NP + CW
44. Banker's = deadlock AVOIDANCE (safe state check)
45. Ostrich = IGNORE deadlocks = what real OS use!
46. Aging = STARVATION solution (not deadlock solution!)
```

---

### ⚡ GS MASTER REVISION — 25 MUST-KNOW FACTS

```
HISTORY:
1.  Ghadar Party = USA | Abhinav Bharat = LONDON (Savarkar)
2.  1857 = "War of Independence" by V.D. SAVARKAR
3.  Grand Old Man = DADABHAI NAOROJI
4.  Bardoli Satyagraha = SARDAR PATEL
5.  Home Rule NOT = Sarojini Naidu (Home Rule = Tilak + Besant)
6.  Bihar SPC founded 1908 | Anushilan Samiti Patna = Sachindra Nath Sanyal
7.  INC Gaya 1922 = President C.R. Das | Viceroy at JWB = Lord Chelmsford

GEOGRAPHY:
8.  Bihar = 8.58% of India | Paddy max = Rohtas | Silk = Bhagalpur
9.  Black soil = Karnataka + Gujarat (BOTH!)
10. Malnad = Karnataka Plateau | Highest East Ghats = Mahendragiri
11. Max urbanization = GOA | SW Monsoon Hyderabad = 1st October
12. Stalactites/Stalagmites = UNDERGROUND WATER
13. Mawsynram = highest rainfall world | Sundarbans = largest delta + mangrove

SCIENCE:
14. P = I²R | c/137 = speed of electron in H orbit
15. Convex lens in water = still convex, focal length INCREASES
16. Frequency unchanged when light changes medium
17. Diaphragm normal respiration = FLATTENS
18. Immunity = LYMPHOCYTES most important
19. Ginger = UNDERGROUND STEM (nodes + internodes)
20. Photoperiodism = GARNER and ALLARD
21. Asexual reproduction budding = YEAST

CONSTITUTION:
22. Art 32 = Heart and Soul (Ambedkar)
23. 42nd Amendment = Socialist + Secular + Fundamental Duties
24. National Panchayati Raj Day = APRIL 24
25. Birsa Munda's Commander-in-Chief = GAYA MUNDA
```

---

### ⚡ TOMORROW — DAY 75 PREVIEW (Week 12 Begins)

```
CS:  CPU Architecture — Components and Functions
     KEY FACTS (directly from study plan):
     → CPU = "Brain" of computer
     → ALU = performs ARITHMETIC and LOGICAL operations
     → Control Unit = generates CONTROL SIGNALS ← PYQ exact phrase
     → Registers = fastest memory (INSIDE CPU)
     → Memory hierarchy: Registers > Cache > RAM > Secondary
     → ASCII = converts KEYSTROKE into corresponding BITS (7-bit code)
     → Cache: L1 (fastest) → L2 → L3 (progressively larger but slower)
     → MUX select lines = log₂(inputs): 8:1 MUX = 3 select lines

GS:  GS Revision — Maths shortcuts (from study plan)
     Profit & Loss, Ratio, Work & Time, Speed-Distance
     All shortcuts already covered in today's GS Unit A!
```

---

## 🎯 WEEK 11 COMPLETE — WEEK 12 BEGINS TOMORROW

```
WEEK 11 COMPLETE:
  Day 68: OS Introduction & Types             ✅
  Day 69: Paging                              ✅
  Day 70: Segmentation + Virtual Memory       ✅
  Day 71: Disk Scheduling                     ✅
  Day 72: I/O Management + File Systems       ✅
  Day 73: Threads + CPU Scheduling + Deadlocks✅
  Day 74: OS Complete Revision + 50 PYQ MCQs  ← TODAY ✅

WEEK 12 BEGINS:
  Day 75: CPU Architecture (ALU, Control Unit, Registers, Cache, ASCII)
  Day 76: Addressing Modes + IA-32 Flags
  Day 77: Memory Types + Buffer Registers
  Day 78: Computer Architecture Numericals
  Day 79: Software Engineering Basics
  Day 80: SDLC + Testing
  Day 81: Week 12 Revision
```

---

*Day 74 Complete | Week 11 FULLY COMPLETE | 6 OS topics mastered | Phase 2: Depth | Target: TOP 50 RANK*
