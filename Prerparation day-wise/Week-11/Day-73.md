# 📅 BPSC TRE 4.0 — DAY 73: THREADS + CPU SCHEDULING + DEADLOCKS + EDUCATION POLICY
### Week 11, Day 6 — Process Management Complete | GS: NEP 2020 + RTE + Education in India
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — Threads (share/don't share), CPU Scheduling (FCFS, SJF, Priority, RR with calculations), Context Switch, Deadlocks (all 4 conditions, prevention, avoidance, detection, recovery)
> - Afternoon (1 hr): GS — NEP 2020 + RTE Act + Education structure in India + Bihar education
> - Evening (1.5 hrs): Solve all 50 MCQs (includes Gantt chart problems)
> - Night (30 min): Read the Night Revision Sheet

---

# PART 1: CS CONCEPT NOTES
## 📘 Process Management — Threads, CPU Scheduling, Deadlocks (ZERO GAPS)

---

## 🔷 TOPIC 1: THREADS — WHAT THEY ARE AND WHY THEY EXIST

```
START FROM SCRATCH — WHY THREADS?
════════════════════════════════════════════════════════════════════

A PROCESS is heavy:
  → Has its own address space (virtual memory)
  → Has its own page tables, file handles, signal handlers
  → Creating a new process = copy EVERYTHING = expensive
  → Switching between processes = full context save + TLB flush = expensive

NEED: Can we have multiple execution paths within ONE PROCESS
      that SHARE the process's resources but have their own
      execution flow (stack, registers, PC)?

ANSWER: YES — these are THREADS.

════════════════════════════════════════════════════════════════════

DEFINITION:
  THREAD = A lightweight unit of execution WITHIN a process.
           It is the BASIC UNIT of CPU utilization.
           Multiple threads can co-exist within ONE process,
           sharing the process's resources but executing independently.

ANALOGY:
  PROCESS = A factory building (has walls, electricity, tools — shared infra)
  THREAD  = A worker in that factory (uses shared tools/space, but each
            worker does their own task independently)

════════════════════════════════════════════════════════════════════

WHAT THREADS SHARE vs WHAT THEY DON'T — THE #1 BPSC PYQ FACT:
════════════════════════════════════════════════════════════════════

  Within ONE PROCESS, Thread A and Thread B:

  ┌─────────────────────────────────────────────────────────────┐
  │  SHARED by ALL THREADS of the same process:                 │
  │                                                             │
  │  ✓ CODE SECTION (text segment)                             │
  │    = The actual compiled program instructions               │
  │    = All threads execute from the same code                 │
  │                                                             │
  │  ✓ DATA SECTION                                            │
  │    = Global variables (e.g., int globalCount = 0;)         │
  │    = Static variables                                       │
  │    = If Thread A modifies globalCount, Thread B sees it!   │
  │                                                             │
  │  ✓ HEAP                                                    │
  │    = Dynamically allocated memory (new/malloc)              │
  │    = Objects on heap accessible to all threads              │
  │                                                             │
  │  ✓ OPEN FILES                                              │
  │    = File handles, network sockets, I/O streams             │
  │                                                             │
  │  ✓ PROCESS ID (PID)                                        │
  │    = All threads belong to same process → same PID          │
  │                                                             │
  │  ✓ SIGNAL HANDLERS                                         │
  │    = How the process handles signals (SIGKILL, SIGTERM...)  │
  └─────────────────────────────────────────────────────────────┘

  ┌─────────────────────────────────────────────────────────────┐
  │  EACH THREAD HAS ITS OWN (NOT SHARED):                      │
  │                                                             │
  │  ✗ STACK ← THE #1 PYQ FACT — THREADS DO NOT SHARE STACK   │
  │    = Each thread has its own CALL STACK                     │
  │    = Stores: function frames, local variables, return addrs │
  │    = Thread A's function calls are independent of Thread B  │
  │                                                             │
  │  ✗ PROGRAM COUNTER (PC)                                    │
  │    = Points to current instruction being executed           │
  │    = Thread A may be at line 150; Thread B at line 300      │
  │                                                             │
  │  ✗ CPU REGISTERS                                           │
  │    = Register values when the thread is executing           │
  │    = AX, BX, SP, BP, flags — each thread's snapshot        │
  │                                                             │
  │  ✗ THREAD ID (TID)                                         │
  │    = Unique identifier for each thread within a process     │
  └─────────────────────────────────────────────────────────────┘

★ BPSC EXACT PHRASE: "Threads share CODE SECTION and DATA SECTION"
★ BPSC EXACT PHRASE: "Each thread has its own STACK"
← These are the two phrases that appear verbatim in PYQ questions.
   Do NOT say "threads share everything" or "threads share nothing."
   The exact answer: shares code + data; does NOT share stack.

════════════════════════════════════════════════════════════════════

WHY MUST EACH THREAD HAVE ITS OWN STACK?

  Thread A calls: functionX() which calls functionY()
    → Stack A: [functionY frame] [functionX frame] [main frame]

  Thread B calls: functionM() which calls functionN()
    → Stack B: [functionN frame] [functionM frame] [main frame]

  These are completely INDEPENDENT call chains.
  If they shared one stack:
    → functionX's return address would get overwritten by functionM's frame
    → Program would crash trying to return to wrong memory location
  ∴ Independent stacks are an absolute NECESSITY for independent execution.

════════════════════════════════════════════════════════════════════

THREAD vs PROCESS — COMPLETE COMPARISON TABLE:
  ────────────────────────────────────────────────────────────────
  FEATURE         THREAD                   PROCESS
  ────────────────────────────────────────────────────────────────
  Weight          Lightweight              Heavyweight
  Address space   SHARED (same as process) SEPARATE (own address space)
  Code section    SHARED                   Own copy
  Data section    SHARED                   Own copy
  Stack           OWN (separate)           Own
  Heap            SHARED                   Own
  Creation time   Fast (< 1ms typical)     Slow (several ms typical)
  Context switch  Fast (no TLB flush)      Slow (must flush TLB)
  Communication   Via shared memory        Needs IPC (pipe, socket...)
  Crash impact    Can crash entire process  Isolated (other processes safe)
  ────────────────────────────────────────────────────────────────

BENEFITS OF MULTITHREADING (BPSC-TESTED):
  1. RESPONSIVENESS:  UI thread stays active while worker thread processes
     Example: Browser loads page (worker thread) while URL bar stays responsive (UI thread)
  2. RESOURCE SHARING: Threads share memory → no expensive IPC needed
  3. ECONOMY:         Creating/switching threads much cheaper than processes
  4. SCALABILITY:     On multi-core CPU, different threads run on different cores
                      → TRUE PARALLEL EXECUTION on 4-core = 4 threads simultaneously

TYPES OF THREADS:
  USER-LEVEL THREADS (ULT):
    → Managed by user-space library (not OS kernel)
    → OS sees one process (doesn't know about threads)
    → Fast context switch (no mode switch to kernel)
    → PROBLEM: If one ULT blocks on I/O → ALL ULTs in process block!
      (because OS blocks the entire process)

  KERNEL-LEVEL THREADS (KLT):
    → Managed directly by OS kernel
    → OS schedules each thread individually
    → If one KLT blocks → OTHER threads continue running
    → Slower context switch (kernel mode switch required)
    → Example: Linux threads (pthreads), Windows threads

  MULTITHREADING MODELS:
    MANY-TO-ONE:   Many ULTs → 1 KLT (no true parallelism)
    ONE-TO-ONE:    1 ULT → 1 KLT (true parallelism; most modern OS)
    MANY-TO-MANY:  Many ULTs → Many KLTs (best flexibility)
```

---

## 🔷 TOPIC 2: CONTEXT SWITCH — EVERY DETAIL

```
WHAT IS A CONTEXT SWITCH?
════════════════════════════════════════════════════════════════════

CONTEXT = All information needed to resume a process/thread exactly
          where it left off:
          → Program Counter (which instruction is next)
          → CPU Registers (AX, BX, CX, SP, BP, flags...)
          → Process state (Running → Ready)
          → Memory management info (page table base register)
          → I/O status (open files, pending I/O)

CONTEXT SWITCH = OS SAVES the context of the currently running
                 process/thread into its PCB and LOADS the
                 previously saved context of the next process/thread
                 from its PCB.

════════════════════════════════════════════════════════════════════

STEP-BY-STEP CONTEXT SWITCH:
  ┌──────────────────────────────────────────────────────────────┐
  │  [Process P1 is RUNNING on CPU]                              │
  │       ↓  Timer interrupt fires (or P1 requests I/O)         │
  │  [CPU switches to KERNEL MODE]                              │
  │       ↓                                                      │
  │  [OS SAVES P1's state into P1's PCB]                        │
  │    → PC = 0x401A30, AX = 42, BX = 0, SP = 0xFFFF80...      │
  │    → P1's state changes: Running → Ready (or Waiting)       │
  │       ↓                                                      │
  │  [SCHEDULER selects P2 as next process]                     │
  │       ↓                                                      │
  │  [OS LOADS P2's state from P2's PCB into CPU registers]     │
  │    → PC = 0x502B10 (where P2 left off), AX = 17...         │
  │    → P2's state changes: Ready → Running                    │
  │       ↓                                                      │
  │  [CPU switches back to USER MODE]                           │
  │       ↓                                                      │
  │  [Process P2 RESUMES from exactly where it stopped]         │
  └──────────────────────────────────────────────────────────────┘

PCB (PROCESS CONTROL BLOCK):
  = Data structure OS maintains for EACH process
  = Stores everything about the process:
    • Process ID (PID), Parent PID
    • Process STATE (New/Ready/Running/Waiting/Terminated)
    • Program Counter value
    • CPU Register values
    • Memory limits (base/limit registers, page table pointer)
    • List of open files
    • Priority, scheduling information
    • Accounting information (CPU time used)
  = When context switch happens → PCB is where state is saved/loaded

CONTEXT SWITCH COST:
  → During switch: NO USEFUL WORK is done (pure overhead)
  → Thread switch: FASTER than process switch
    (threads share address space → no page table change → no TLB flush)
  → Process switch: SLOWER (must change page tables, flush TLB)
  → Typical times: Thread switch ~1µs, Process switch ~5–10µs
```

---

## 🔷 TOPIC 3: CPU SCHEDULING — INTRODUCTION + KEY TERMS

```
WHY CPU SCHEDULING EXISTS:
════════════════════════════════════════════════════════════════════

  Multiple processes in READY QUEUE all want the CPU.
  Only ONE process can run on ONE CPU core at a time.
  OS must decide: WHO runs next? FOR HOW LONG?
  This decision = CPU SCHEDULING.

SCHEDULING QUEUES:
  JOB QUEUE:   All processes in the system (including on disk)
  READY QUEUE: Processes in RAM, ready to run (waiting for CPU)
  DEVICE QUEUE: Processes waiting for specific I/O device

SCHEDULERS:
  LONG-TERM (Job Scheduler):  Controls which jobs enter the ready queue
                              (controls DEGREE OF MULTIPROGRAMMING)
  SHORT-TERM (CPU Scheduler): Selects from ready queue → gives CPU
                              (runs very frequently = milliseconds)
  MEDIUM-TERM:                Can SWAP out processes to disk and back
                              (controls memory load)

SCHEDULING CRITERIA (what we optimize for):
  MAXIMIZE:
    → CPU Utilization:  Keep CPU busy as much as possible
    → Throughput:       Number of processes completed per time unit
  MINIMIZE:
    → Turnaround Time:  Time from arrival to completion
    → Waiting Time:     Time spent in ready queue
    → Response Time:    Time from arrival to FIRST response (interactive systems)

KEY TERMS AND FORMULAS (MUST KNOW FOR CALCULATIONS):
════════════════════════════════════════════════════════════════════

  ARRIVAL TIME (AT):      When process enters ready queue
  BURST TIME (BT):        CPU time needed to complete the process
  COMPLETION TIME (CT):   When process finishes and exits

  TURNAROUND TIME (TAT):  TAT = CT − AT
                          (total time from arrival to finish)

  WAITING TIME (WT):      WT = TAT − BT
                               = (CT − AT) − BT
                          (time spent WAITING in ready queue)
                          ← MOST COMMON calculation mistake:
                             Students write WT = CT − BT (WRONG!)
                             Correct: WT = TAT − BT

  RESPONSE TIME:          Time from arrival to FIRST CPU assignment
                          (important for interactive systems)

  AVERAGE TAT = Sum of all TATs / Number of processes
  AVERAGE WT  = Sum of all WTs  / Number of processes

PREEMPTIVE vs NON-PREEMPTIVE:
  NON-PREEMPTIVE: Once CPU given to process → runs until:
                  (a) it finishes, or (b) it requests I/O/blocks
                  OS CANNOT forcibly take CPU away
                  Examples: FCFS, non-preemptive SJF, non-preemptive Priority

  PREEMPTIVE:     OS CAN forcibly take CPU away from running process
                  Happens when: timer expires, higher-priority process arrives
                  Examples: Round Robin, SRTF, preemptive Priority
```

---

## 🔷 TOPIC 4: FCFS — FIRST COME FIRST SERVED (COMPLETE)

```
ALGORITHM RULE:
  Serve processes in the ORDER THEY ARRIVE in the ready queue.
  Non-preemptive: once started, runs to completion (or I/O block).
  Implementation: Simple FIFO queue.

════════════════════════════════════════════════════════════════════
WORKED EXAMPLE 1 (all arrive at t=0):
════════════════════════════════════════════════════════════════════

  Process | AT | BT
  ────────┼────┼────
  P1      |  0 |  4
  P2      |  0 |  3
  P3      |  0 |  5
  P4      |  0 |  2

  FCFS ORDER: P1 → P2 → P3 → P4 (arrival order, all t=0 → use given order)

  GANTT CHART:
  | P1  P1  P1  P1 | P2  P2  P2 | P3  P3  P3  P3  P3 | P4  P4 |
  0               4           7                      12      14

  Process | AT | BT | CT | TAT=CT-AT | WT=TAT-BT
  ────────┼────┼────┼────┼───────────┼──────────
  P1      |  0 |  4 |  4 |     4     |    0
  P2      |  0 |  3 |  7 |     7     |    4
  P3      |  0 |  5 | 12 |    12     |    7
  P4      |  0 |  2 | 14 |    14     |   12

  Average TAT = (4+7+12+14)/4 = 37/4 = 9.25
  Average WT  = (0+4+7+12)/4  = 23/4 = 5.75

════════════════════════════════════════════════════════════════════
WORKED EXAMPLE 2 (different arrival times):
════════════════════════════════════════════════════════════════════

  Process | AT | BT
  ────────┼────┼────
  P1      |  0 |  4
  P2      |  1 |  3
  P3      |  2 |  5

  t=0: P1 arrives → start P1 (BT=4)
  t=1: P2 arrives → but P1 still running (non-preemptive!)
  t=2: P3 arrives → P1 still running
  t=4: P1 finishes. Ready queue: [P2, P3] → FCFS: P2 first (arrived at t=1)
  t=7: P2 finishes → P3 starts
  t=12: P3 finishes

  GANTT: | P1 P1 P1 P1 | P2 P2 P2 | P3 P3 P3 P3 P3 |
          0           4          7                12

  Process | AT | BT | CT | TAT=CT-AT | WT=TAT-BT
  ────────┼────┼────┼────┼───────────┼──────────
  P1      |  0 |  4 |  4 |    4      |    0
  P2      |  1 |  3 |  7 |    6      |    3
  P3      |  2 |  5 | 12 |   10      |    5

  Average TAT = (4+6+10)/3  = 20/3 = 6.67
  Average WT  = (0+3+5)/3   = 8/3  = 2.67

════════════════════════════════════════════════════════════════════

FCFS KEY PROPERTIES:
  ★ NON-PREEMPTIVE
  ★ COMPLETELY FAIR — arrival order always respected
  ★ NO STARVATION — every process eventually gets CPU
  ★ SIMPLE to implement (just a FIFO queue)
  ★ CONVOY EFFECT ← BPSC NAMED WEAKNESS
    = When a long process runs, all shorter processes pile up waiting
    = Like cars stuck behind a slow truck in a single-lane road
    = Short processes suffer even though they need very little CPU time
  ★ WORST average waiting time for mixed short/long workloads
```

---

## 🔷 TOPIC 5: SJF — SHORTEST JOB FIRST (COMPLETE)

```
ALGORITHM RULE:
  Among all processes currently in the ready queue, select the one
  with the SHORTEST BURST TIME (shortest remaining CPU need).
  NON-PREEMPTIVE: selected process runs to completion.
  PREEMPTIVE version = SRTF (Shortest Remaining Time First).

════════════════════════════════════════════════════════════════════
NON-PREEMPTIVE SJF — WORKED EXAMPLE:
════════════════════════════════════════════════════════════════════

  Process | AT | BT
  ────────┼────┼────
  P1      |  0 |  6
  P2      |  2 |  2
  P3      |  4 |  8
  P4      |  6 |  3

  t=0: Ready queue = {P1(6)}. Only P1 → run P1.
  t=2: P2 arrives but P1 still running (non-preemptive) → P1 continues.
  t=4: P3 arrives → P1 still running.
  t=6: P1 FINISHES. P4 arrives same moment.
       Ready queue = {P2(2), P3(8), P4(3)} → SHORTEST = P2(2) → run P2.
  t=8: P2 FINISHES. Ready queue = {P3(8), P4(3)} → SHORTEST = P4(3) → run P4.
  t=11: P4 FINISHES. Ready queue = {P3(8)} → run P3.
  t=19: P3 FINISHES.

  ORDER: P1 → P2 → P4 → P3

  GANTT CHART:
  | P1  P1  P1  P1  P1  P1 | P2  P2 | P4  P4  P4 | P3  P3  P3  P3  P3  P3  P3  P3 |
  0                       6       8           11                                   19

  Process | AT | BT | CT | TAT=CT-AT | WT=TAT-BT
  ────────┼────┼────┼────┼───────────┼──────────
  P1      |  0 |  6 |  6 |     6     |    0
  P2      |  2 |  2 |  8 |     6     |    4
  P3      |  4 |  8 | 19 |    15     |    7
  P4      |  6 |  3 | 11 |     5     |    2

  Average TAT = (6+6+15+5)/4 = 32/4 = 8.0
  Average WT  = (0+4+7+2)/4  = 13/4 = 3.25

  Compare FCFS with same data: avg WT would be much higher (try it!)

════════════════════════════════════════════════════════════════════
PREEMPTIVE SJF = SRTF (Shortest Remaining Time First):
════════════════════════════════════════════════════════════════════

  RULE: At every moment, run the process with SHORTEST REMAINING TIME.
        If a new process arrives with shorter remaining time than the
        currently running process → PREEMPT (stop current, run new one).

  EXAMPLE:
  Process | AT | BT
  P1      |  0 |  8
  P2      |  1 |  4
  P3      |  2 |  9
  P4      |  3 |  5

  t=0: Only P1(remaining=8) → run P1
  t=1: P2 arrives (remaining=4). Compare: P1 remaining=7 vs P2=4 → P2 shorter → PREEMPT P1!
       Run P2.
  t=2: P3 arrives (remaining=9). Compare: P2 remaining=3 vs P3=9 → P2 shorter → P2 continues.
  t=3: P4 arrives (remaining=5). Compare: P2 remaining=2 vs P4=5 → P2 shorter → P2 continues.
  t=5: P2 FINISHES. Remaining: P1(7), P3(9), P4(5) → shortest = P4(5) → run P4.
  t=10: P4 FINISHES. Remaining: P1(7), P3(9) → shortest = P1(7) → run P1.
  t=17: P1 FINISHES. Only P3(9) → run P3.
  t=26: P3 FINISHES.

  GANTT: |P1|P2 P2 P2 P2|P4 P4 P4 P4 P4|P1 P1 P1 P1 P1 P1 P1|P3...P3|
          0  1          5             10                      17      26

════════════════════════════════════════════════════════════════════

SJF KEY PROPERTIES:
  ★ NON-PREEMPTIVE SJF:  Minimum avg wait time among non-preemptive algorithms
  ★ SRTF (preemptive SJF): OVERALL MINIMUM average waiting time (optimal)
  ★ STARVATION POSSIBLE ← just like SSTF disk scheduling!
    Long processes may NEVER get CPU if short ones keep arriving.
  ★ PRACTICAL PROBLEM: Burst time must be KNOWN/ESTIMATED in advance
    (we can't know how long a process will run — must predict using
    exponential averaging of past burst times)
  ★ SRTF = preemptive version (optimal but complex)

  Comparison: SRTF ≤ SJF ≤ FCFS in terms of average waiting time
              (SRTF is best, FCFS is worst)
```

---

## 🔷 TOPIC 6: PRIORITY SCHEDULING (COMPLETE)

```
ALGORITHM RULE:
  Each process assigned a PRIORITY NUMBER.
  CPU given to the process with HIGHEST PRIORITY.
  CONVENTION: Smaller number = HIGHER priority (in most textbooks)
              Priority 1 > Priority 2 > Priority 3 ...
  Can be PREEMPTIVE or NON-PREEMPTIVE.

════════════════════════════════════════════════════════════════════
WORKED EXAMPLE (Non-preemptive, all arrive t=0):
════════════════════════════════════════════════════════════════════

  Process | AT | BT | Priority (1=highest)
  ────────┼────┼────┼──────────────────────
  P1      |  0 |  5 |       3
  P2      |  0 |  3 |       1       ← highest priority
  P3      |  0 |  1 |       4       ← lowest priority
  P4      |  0 |  2 |       2
  P5      |  0 |  4 |       5       ← very low priority

  ORDER (highest priority first): P2(1) → P4(2) → P1(3) → P3(4) → P5(5)

  GANTT:
  | P2 P2 P2 | P4 P4 | P1 P1 P1 P1 P1 | P3 | P5 P5 P5 P5 |
  0         3       5               10   11              15

  Process | CT | TAT=CT-AT | WT=TAT-BT
  ────────┼────┼───────────┼──────────
  P2      |  3 |     3     |    0
  P4      |  5 |     5     |    3
  P1      | 10 |    10     |    5
  P3      | 11 |    11     |   10
  P5      | 15 |    15     |   11

  Average TAT = (3+5+10+11+15)/5 = 44/5 = 8.8
  Average WT  = (0+3+5+10+11)/5  = 29/5 = 5.8

════════════════════════════════════════════════════════════════════

STARVATION IN PRIORITY SCHEDULING:
  PROBLEM: Low-priority processes may NEVER get CPU if higher-priority
           processes keep arriving.
  EXAMPLE: P5 (priority 5, lowest) keeps waiting while priority 1,2,3,4
           processes keep entering the queue → P5 waits indefinitely.

AGING — THE SOLUTION TO STARVATION:
  AGING = Gradually increase the priority of a waiting process over time.
  → Every T time units a process waits → its priority increases by 1
  → Eventually even a priority-5 process becomes priority-1
  → Guaranteed to get CPU eventually → NO indefinite starvation
  ← PYQ: AGING = solution to STARVATION in priority scheduling
  ← Also: AGING is a solution to STARVATION in SJF
    (long-waiting processes get priority boost → eventually scheduled)

PRIORITY INVERSION PROBLEM:
  = A HIGH-PRIORITY process waits for a LOW-PRIORITY process
    because the low-priority process holds a shared resource.
  EXAMPLE:
    P_low (low priority) holds mutex lock on shared data.
    P_high (high priority) needs that mutex → BLOCKS!
    P_medium (medium priority) preempts P_low (more important than P_low)
    → P_high waits for P_low, but P_low can't run because P_medium runs
    → P_high indirectly "inverted" to lower effective priority than P_medium!
  SOLUTION: Priority inheritance (P_low temporarily gets P_high's priority)
  FAMOUS CASE: Mars Pathfinder robot (1997) had priority inversion bug!

PRIORITY vs SJF:
  SJF:      Priority = 1/(burst time) — short jobs have implicit high priority
  Priority: Explicit priority number assigned by user/OS
  Both can starve long/low-priority processes.
  Both solved by aging.
```

---

## 🔷 TOPIC 7: ROUND ROBIN SCHEDULING (COMPLETE)

```
ALGORITHM RULE:
  Each process gets a FIXED TIME QUANTUM (also called TIME SLICE).
  Process runs for at most q time units.
  After q units → PREEMPTED → placed at END of ready queue.
  Next process in queue gets its quantum.
  PREEMPTIVE by design.

  This is THE algorithm used in TIME-SHARING OS.
  ← Connect to Day 68: "Time-sharing OS uses Round Robin scheduling"

════════════════════════════════════════════════════════════════════
WORKED EXAMPLE 1 (Time Quantum q = 2):
════════════════════════════════════════════════════════════════════

  Process | AT | BT
  P1      |  0 |  5
  P2      |  0 |  3
  P3      |  0 |  4
  All arrive at t=0. Initial ready queue: [P1, P2, P3]

  TIME QUANTUM = 2

  t=0→2:  P1 runs 2 units. P1 remaining = 5-2 = 3.
          Queue after: [P2, P3, P1]
  t=2→4:  P2 runs 2 units. P2 remaining = 3-2 = 1.
          Queue after: [P3, P1, P2]
  t=4→6:  P3 runs 2 units. P3 remaining = 4-2 = 2.
          Queue after: [P1, P2, P3]
  t=6→8:  P1 runs 2 units. P1 remaining = 3-2 = 1.
          Queue after: [P2, P3, P1]
  t=8→9:  P2 runs 1 unit (only 1 remaining). P2 FINISHES at t=9. ✓
          Queue after: [P3, P1]
  t=9→11: P3 runs 2 units. P3 remaining = 2-2 = 0. P3 FINISHES at t=11. ✓
          Queue after: [P1]
  t=11→12: P1 runs 1 unit (only 1 remaining). P1 FINISHES at t=12. ✓

  GANTT CHART:
  |P1|P1|P2|P2|P3|P3|P1|P1|P2|P3|P3|P1|
  0  1  2  3  4  5  6  7  8  9 10 11 12

  Process | AT | BT | CT | TAT=CT-AT | WT=TAT-BT
  ────────┼────┼────┼────┼───────────┼──────────
  P1      |  0 |  5 | 12 |    12     |    7
  P2      |  0 |  3 |  9 |     9     |    6
  P3      |  0 |  4 | 11 |    11     |    7

  Average TAT = (12+9+11)/3 = 32/3 = 10.67
  Average WT  = (7+6+7)/3   = 20/3 = 6.67

════════════════════════════════════════════════════════════════════
WORKED EXAMPLE 2 (Time Quantum q = 4):
════════════════════════════════════════════════════════════════════

  Same processes: P1(BT=5), P2(BT=3), P3(BT=4), q=4, all AT=0

  t=0→4:  P1 runs 4 units. P1 remaining = 1. Queue: [P2, P3, P1]
  t=4→7:  P2 runs 3 units (only 3 remaining). P2 FINISHES at t=7. ✓ Queue: [P3, P1]
  t=7→11: P3 runs 4 units. P3 remaining = 0. P3 FINISHES at t=11. ✓ Queue: [P1]
  t=11→12: P1 runs 1 unit. P1 FINISHES at t=12. ✓

  GANTT: |P1  P1  P1  P1|P2  P2  P2|P3  P3  P3  P3|P1|
          0           4          7             11  12

  Process | CT | TAT | WT
  P1      | 12 |  12 |  7
  P2      |  7 |   7 |  4
  P3      | 11 |  11 |  7

  Average TAT = (12+7+11)/3 = 30/3 = 10.0
  Average WT  = (7+4+7)/3   = 18/3 = 6.0

  NOTE: q=4 is BETTER here than q=2 (6.0 vs 6.67 avg WT)
        BUT: q=4 means P2 (short job) finishes at t=7
             With q=2, P2 finishes at t=9 (takes longer for short jobs!)
  This demonstrates: Larger q can help short jobs finish sooner if
  they fit within one quantum.

════════════════════════════════════════════════════════════════════

TIME QUANTUM (q) EFFECT — CRITICAL UNDERSTANDING:
  ────────────────────────────────────────────────────────────────
  VERY SMALL q (e.g., q=1):
    → Many context switches (overhead dominates)
    → System wastes too much time saving/loading PCBs
    → Each process gets tiny slices → interactive feel but poor throughput
    → Extreme: q→0: processes share CPU smoothly (no context switch cost
      in theory) but real overhead is catastrophic

  VERY LARGE q (q > max burst time of any process):
    → Every process COMPLETES within its quantum (no preemption occurs)
    → Behaves EXACTLY LIKE FCFS (arrival order, full run to completion)
    ← PYQ: "Large time quantum → Round Robin degenerates to FCFS"

  OPTIMAL q:
    → Large enough: context switch overhead is small fraction of quantum
    → Small enough: good response time
    → Typical: 10–100 milliseconds in practice
    → Rule of thumb: 80% of bursts should be shorter than q
  ────────────────────────────────────────────────────────────────

ROUND ROBIN KEY PROPERTIES:
  ★ PREEMPTIVE — always preemptive ← exam fact
  ★ TIME QUANTUM based — each process gets equal fixed time slice
  ★ NO STARVATION — every process gets CPU in rotation
  ★ FAIR — equal CPU shares for all processes
  ★ Standard algorithm for TIME-SHARING OS ← connect to Day 68
  ★ Large q → degenerates to FCFS ← PYQ trap
  ★ Small q → high context switch overhead
  ★ Good RESPONSE TIME (every process gets CPU quickly)
  ★ Average turnaround time HIGHER than SJF (doesn't favor short jobs)

ROUND ROBIN ADVANTAGES:          ROUND ROBIN DISADVANTAGES:
  ✓ No starvation                  ✗ Higher avg TAT than SJF
  ✓ Fair CPU sharing               ✗ Context switch overhead
  ✓ Good response time             ✗ Performance sensitive to q
  ✓ Standard for time-sharing OS
```

---

## 🔷 TOPIC 8: CPU SCHEDULING MASTER COMPARISON TABLE

```
ALL ALGORITHMS — COMPLETE MASTER TABLE:
════════════════════════════════════════════════════════════════════

ALGORITHM    PREEMPTIVE?  STARVATION?  CONVOY?  OPTIMAL WT?   KEY FACT
─────────────────────────────────────────────────────────────────────────
FCFS         NO           NO           YES      NO (worst)    Convoy effect
                          (completely  ←named   FCFS=worst    Simple, fair
                           fair)        weakness for mixed    arrival order

SJF          NO           YES          NO       YES (among    Starvation of
(non-preempt) ←long jobs  short jobs  non-preemptive)       long jobs
              may starve  served first

SRTF         YES          YES          NO       YES           Preemptive SJF
(preemptive  ←long jobs  shortest     (globally            = OPTIMAL minimum
 SJF)         may starve  remaining   optimal)             avg wait time

Priority     Both         YES          NO       NO            Starvation fixed
             (preemptive  ←low prio                          by AGING
              or not)      starves

Round Robin  YES          NO           NO       NO            TIME-SHARING OS
(preemptive) ←always     ←always fair          (not         Large q → FCFS
                                                optimal)     Time quantum

─────────────────────────────────────────────────────────────────────────

PERFORMANCE (avg waiting time, best to worst for typical mixed workload):
  SRTF < SJF < RR ≈ Priority < FCFS

STARVATION AFFECTED: SJF, SRTF, Priority (all can starve)
NOT STARVATION:      FCFS (completely fair), Round Robin (rotation = fair)
SOLUTION TO STARVATION: AGING (gradually increase priority with wait time)

════════════════════════════════════════════════════════════════════

COMMON EXAM SCENARIOS:
  "Which gives minimum average waiting time?" → SRTF (preemptive SJF)
  "Which is used in time-sharing OS?" → Round Robin
  "Which suffers from convoy effect?" → FCFS
  "Which can cause starvation?" → SJF, SRTF, Priority
  "Solution to starvation?" → AGING
  "Large time quantum → behaves like?" → FCFS
  "Which is completely non-preemptive and fair?" → FCFS
```

---

## 🔷 TOPIC 9: DEADLOCKS — COMPLETE DEEP DIVE FROM ZERO

```
WHAT IS A DEADLOCK?
════════════════════════════════════════════════════════════════════

SIMPLE SCENARIO:
  Process P1: holds Printer, wants Scanner
  Process P2: holds Scanner, wants Printer

  P1 waits for P2 to release Scanner.
  P2 waits for P1 to release Printer.
  → NEITHER can ever proceed. Both wait FOREVER.
  → This is a DEADLOCK.

FORMAL DEFINITION:
  A SET OF PROCESSES is DEADLOCKED when:
  Each process in the set is BLOCKED, waiting for a resource
  that is HELD BY ANOTHER PROCESS in the same set.
  None of them can ever proceed without external intervention.

RESOURCES:
  = Anything a process needs and must acquire:
    CPU cycles, memory, files, printers, network sockets, mutex locks...
  NON-SHARABLE resources → cause deadlocks
    (only one process can use at a time: printer, mutex lock)
  SHARABLE resources → DON'T cause deadlocks
    (multiple processes can read a read-only file simultaneously)
```

---

## 🔷 TOPIC 10: THE FOUR COFFMAN CONDITIONS FOR DEADLOCK

```
← MOST TESTED DEADLOCK TOPIC IN BPSC — ALL 4 MUST HOLD SIMULTANEOUSLY!
← If ANY ONE condition is absent → DEADLOCK CANNOT OCCUR.

════════════════════════════════════════════════════════════════════

CONDITION 1: MUTUAL EXCLUSION
════════════════════════════════════════════════════════════════════

  WHAT IT MEANS:
    At least one resource is NON-SHARABLE.
    Only ONE process can use it at any given time.
    Other processes must WAIT if it's in use.

  REAL EXAMPLES:
    → A PRINTER: Cannot print two jobs simultaneously. One process
      uses it; others must wait.
    → A MUTEX LOCK: Only one thread can hold it. Others block.
    → A FILE opened for WRITING: One writer at a time.

  NOT MUTUAL EXCLUSION (no deadlock from this resource alone):
    → A READ-ONLY FILE: Multiple processes can read simultaneously.
    → A COUNTER on a multi-processor (atomic operations can allow sharing).

  CAN WE ELIMINATE THIS CONDITION?
    → RARELY. For physical resources (printer, pen drive), mutual exclusion
      is a physical reality — you CANNOT have two processes printing
      to the same printer head simultaneously.
    → For some software resources (read-only data), you CAN make it
      sharable, eliminating mutual exclusion.
    → Generally treated as UNAVOIDABLE for hardware resources.

════════════════════════════════════════════════════════════════════

CONDITION 2: HOLD AND WAIT
════════════════════════════════════════════════════════════════════

  WHAT IT MEANS:
    A process is HOLDING at least one resource AND simultaneously
    WAITING to acquire additional resources currently held by others.
    It does NOT release its held resource while waiting.

  EXAMPLE:
    Process P1 is HOLDING: Printer (already acquired)
    Process P1 is WAITING for: Scanner (held by P2)
    P1 does NOT release the printer while waiting for scanner.
    → HOLD (printer) AND WAIT (scanner) = this condition holds.

  WHY THIS IS DANGEROUS:
    P1 holds printer → P3 cannot print (waiting for printer).
    P1 waits for scanner → P1 is blocked.
    Chain of waiting builds up.

  HOW TO ELIMINATE (PREVENTION):
    OPTION A: "ALL OR NOTHING" — Before a process starts, it must
              REQUEST ALL resources it will EVER need.
              → If all available → grant all → start.
              → If any unavailable → request nothing → wait until all free.
              PROBLEM: Process may hold resources for long time before needing them
                       → poor resource utilization.
              PROBLEM: Process may not know in advance what it needs.

    OPTION B: "RELEASE BEFORE REQUESTING" — A process must release ALL
              currently held resources before requesting new ones.
              → If it needs both printer and scanner: release printer first,
                then request both together.
              PROBLEM: Process loses progress (may need to redo work).
              PROBLEM: Starvation possible if it can never get all resources together.

════════════════════════════════════════════════════════════════════

CONDITION 3: NO PREEMPTION
════════════════════════════════════════════════════════════════════

  WHAT IT MEANS:
    Resources CANNOT be forcibly taken away from a process.
    Once a process acquires a resource, it keeps it until:
    (a) it voluntarily releases it (done using it), or
    (b) the process terminates.
    OS CANNOT snatch a resource from a process holding it.

  EXAMPLE:
    Process P1 holds the PRINTER (printing a 100-page document).
    Even if P2 (high priority) desperately needs the printer,
    OS CANNOT stop P1's print job and give printer to P2.
    P1 must finish printing before releasing the printer.

  ANOTHER EXAMPLE:
    A process holds a MUTEX LOCK on a database record.
    OS cannot forcibly take the lock → other processes using that
    record must wait until the lock is voluntarily released.

  HOW TO ELIMINATE (PREVENTION):
    ALLOW PREEMPTION: If a process holding resources requests
    a resource that's unavailable, OS may:
    → Force the process to RELEASE all its currently held resources.
    → Resources are preempted and given to waiting processes.
    → Preempted process is rolled back and restarted later.

    WORKS WELL FOR: Resources whose state can be easily saved/restored
      → CPU registers (saved in PCB during context switch — we already do this!)
      → Memory pages (can be swapped out)
    DOESN'T WORK FOR: Resources mid-use
      → Printer mid-job (can't "unprint" pages)
      → Database transaction mid-write (would corrupt data)

════════════════════════════════════════════════════════════════════

CONDITION 4: CIRCULAR WAIT
════════════════════════════════════════════════════════════════════

  WHAT IT MEANS:
    A SET of processes {P1, P2, P3, ..., Pn} exists such that:
    P1 waits for a resource held by P2,
    P2 waits for a resource held by P3,
    ...
    Pn waits for a resource held by P1.
    → CIRCULAR CHAIN of waiting — a cycle.

  VISUAL:
  P1 ──(waiting for resource held by)──► P2
  ▲                                       │
  │                                       ▼
  P4 ◄──(waiting for resource held by)── P3

  P1 → P2 → P3 → P4 → P1 (circular!)

  RESOURCE ALLOCATION GRAPH:
    Nodes: Processes (circles) + Resources (squares)
    ASSIGNMENT EDGE: Resource → Process (resource assigned to process)
    REQUEST EDGE:    Process → Resource (process waiting for resource)
    DEADLOCK ↔ CYCLE in resource allocation graph
    (definite deadlock if each resource has ONE instance)

  HOW TO ELIMINATE (PREVENTION — MOST PRACTICAL!):
    IMPOSE TOTAL ORDERING ON RESOURCES:
    → Assign a unique integer number to EVERY resource type.
      Example: R1=1, R2=2, R3=3, R4=4, Printer=5, Scanner=6, etc.
    → RULE: A process can ONLY REQUEST resources in STRICTLY INCREASING
             ORDER of their numbers.
    → If process needs R3 and R1: must request R1 FIRST, then R3.
      CANNOT request R3 first then R1 (would violate increasing order).
    
    WHY THIS PREVENTS CIRCULAR WAIT:
    → Suppose P1 holds R3 and requests R5 (higher → valid)
    → For P2 to cause circular wait, P2 must hold R5 and request R3 (going DOWN)
    → But going DOWN is FORBIDDEN by the ordering rule!
    → No cycle can form because requests can only go UP in resource numbers
    → Therefore CIRCULAR WAIT is IMPOSSIBLE.

    THIS IS THE MOST PRACTICAL DEADLOCK PREVENTION TECHNIQUE:
    ← Used in: Database systems (lock ordering), OS mutex ordering
    ← PYQ: "Most practical way to prevent deadlock = resource ordering"

════════════════════════════════════════════════════════════════════

MEMORY TRICK FOR ALL 4 CONDITIONS:
  "My House Needs Cleaning"
   M      H     N      C
   Mutual Hold  No     Circular
   Exclusion & Wait Preemption Wait

OR: "MHNC" → "Men Have No Conscience" (any mnemonic you like!)

ALL 4 IN ONE TABLE:
  CONDITION          ONE-LINE MEANING                   BREAK BY
  ──────────────────────────────────────────────────────────────────
  Mutual Exclusion   Resource = non-sharable            Make resources sharable
  Hold & Wait        Holds one + waits for more         Request all at once / release first
  No Preemption      Can't forcibly take resource        Allow OS preemption of resources
  Circular Wait      Circular chain of waiting           Resource ordering (most practical)
  ──────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 11: DEADLOCK HANDLING — FOUR STRATEGIES

```
FOUR WAYS TO DEAL WITH DEADLOCKS:
════════════════════════════════════════════════════════════════════

STRATEGY 1: DEADLOCK PREVENTION
════════════════════════════════════════════════════════════════════

  DEFINITION: Design the system so that AT LEAST ONE of the four
              Coffman conditions can NEVER hold.
              → Deadlock is STRUCTURALLY IMPOSSIBLE.

  METHODS:
    Break Mutual Exclusion: Make resources sharable where possible
                            (e.g., read-only access to shared files)
    Break Hold & Wait:      "All or nothing" resource requests
    Break No Preemption:    Allow OS to forcibly take resources
    Break Circular Wait:    Impose strict resource ordering ← BEST

  TRADEOFFS: May reduce system utilization or limit flexibility.

════════════════════════════════════════════════════════════════════

STRATEGY 2: DEADLOCK AVOIDANCE
════════════════════════════════════════════════════════════════════

  DEFINITION: Allow all 4 conditions to potentially hold, but use
              intelligent resource allocation to ensure system NEVER
              enters an UNSAFE STATE.

  KEY CONCEPT — SAFE STATE:
    A state is SAFE if there exists a SAFE SEQUENCE of processes
    such that each process can complete by using remaining resources
    plus resources released by earlier completed processes.

    SAFE STATE ≠ Deadlock-free right now, but GUARANTEES no deadlock
                  will occur in the future if we follow the safe sequence.
    UNSAFE STATE: May or may not lead to deadlock, but we can't guarantee
                  deadlock won't happen. We AVOID entering unsafe states.

  BANKER'S ALGORITHM (Dijkstra):
  ← MOST FAMOUS deadlock avoidance algorithm
  ← Named because it works like a bank: never give out loans that could
    prevent all customers from eventually being served.

  BANK ANALOGY:
    Bank has $10,000 total.
    Customers: A needs max $9K, B needs max $3K, C needs max $7K.
    Currently: A has $3K, B has $2K, C has $2K. (Total used = $7K)
    Available: $10K - $7K = $3K still in bank.

    A still needs: $9K - $3K = $6K more (at most)
    B still needs: $3K - $2K = $1K more (at most)
    C still needs: $7K - $2K = $5K more (at most)

    Available = $3K. Can B finish? $3K ≥ $1K? YES! → B finishes → returns $2K
    Available = $5K. Can C finish? $5K ≥ $5K? YES! → C finishes → returns $7K
    Available = $12K. Can A finish? $12K ≥ $6K? YES! → A finishes.
    SAFE SEQUENCE: B → C → A
    SAFE STATE → bank can loan safely.

  IN OS: Before granting any resource request:
    1. Simulate the allocation (pretend we granted it).
    2. Check if resulting state is SAFE (safe sequence exists).
    3. If SAFE → grant the request.
    4. If UNSAFE → deny the request; make process wait.

  LIMITATION: Requires knowing MAXIMUM RESOURCE NEEDS in advance.
              (processes must declare max needs at process creation time)

════════════════════════════════════════════════════════════════════

STRATEGY 3: DEADLOCK DETECTION + RECOVERY
════════════════════════════════════════════════════════════════════

  DEFINITION: Let deadlocks OCCUR freely. Periodically detect if
              deadlock has occurred. If yes → take recovery action.

  DETECTION:
    → Maintain a RESOURCE ALLOCATION GRAPH (RAG)
    → Periodically run a CYCLE DETECTION algorithm
    → If CYCLE EXISTS in RAG → DEADLOCK DETECTED
    → For single-instance resources: cycle = definite deadlock
    → For multi-instance resources: need reduction algorithm

    HOW OFTEN TO RUN DETECTION?
    → Too frequent → wastes CPU time
    → Too infrequent → deadlock persists too long
    → Heuristic: run when CPU utilization drops unexpectedly

  RECOVERY METHODS:

  OPTION A: PROCESS TERMINATION:
    ABORT ALL: Kill all deadlocked processes immediately.
               → Simple, fast, but all work done by those processes is lost!
    ABORT ONE BY ONE: Kill one process at a time.
               → After each kill, check if deadlock is resolved.
               → If resolved → stop killing.
               → Which process to kill first?
                 → Lowest priority, or fewest resources held,
                   or least total work done (minimizes loss).

  OPTION B: RESOURCE PREEMPTION:
    → Forcibly take resources from some processes (preempt).
    → Give those resources to others to break the deadlock.
    → Preempted processes are rolled back to a safe checkpoint.
    PROBLEMS WITH PREEMPTION:
      • STARVATION: Same process might always be chosen as victim.
        Solution: Limit how many times a process can be preempted.
      • ROLLBACK: Must checkpoint process state periodically
        (expensive in storage and compute).
      • HARD FOR SOME RESOURCES: Can't roll back a half-printed document.

════════════════════════════════════════════════════════════════════

STRATEGY 4: OSTRICH ALGORITHM (IGNORE DEADLOCKS)
════════════════════════════════════════════════════════════════════

  DEFINITION: PRETEND DEADLOCKS DON'T EXIST.
              Do absolutely nothing to prevent, avoid, or detect them.
              If deadlock occurs → let user deal with it (kill task, reboot).

  NAMED AFTER: "Ostrich buries its head in the sand" (ignores problems).

  JUSTIFICATION: In many systems, deadlocks are:
    → Very RARE (occurs maybe once a month or year)
    → The COST of prevention/avoidance is too high for the benefit
    → Prevention reduces throughput; avoidance requires max declarations;
      detection wastes CPU. For rare events, ignoring is cost-effective!

  ← BPSC/EXAM PYQ: "What approach do most practical OS use for deadlock?"
  ← ANSWER: OSTRICH ALGORITHM — they IGNORE it!

  USED BY: Linux, Windows, macOS, and most general-purpose OS.
  HOW USERS DEAL: Task Manager (Windows), kill command (Linux), Force Quit (Mac).

════════════════════════════════════════════════════════════════════

FOUR STRATEGIES COMPARISON TABLE:
  STRATEGY     OVERHEAD  UTILIZATION  PRACTICAL?  KEY CONCEPT
  ─────────────────────────────────────────────────────────────────
  Prevention   Medium    Low          Partially   Break one condition
  Avoidance    High      Medium       Partially   Banker's = safe state
  Detection    Medium    High         Yes         Find cycles; kill/preempt
  Ostrich      ZERO      Highest      YES (most!) Ignore (for rare deadlocks)
  ─────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 12: SYNCHRONIZATION — CRITICAL SECTION PROBLEM

```
THE CRITICAL SECTION PROBLEM:
════════════════════════════════════════════════════════════════════

CRITICAL SECTION (CS):
  = A segment of code that accesses SHARED RESOURCES
    (shared variables, files, data structures, hardware).
  = Must be executed by at most ONE process/thread at a time.
  = If multiple threads enter CS simultaneously → RACE CONDITION!

RACE CONDITION:
  = When the result depends on the ORDER of execution of threads.
  = Non-deterministic → produces different results each run!
  EXAMPLE:
    Thread A: x = x + 1   (x starts as 5)
    Thread B: x = x + 1   (x starts as 5)
    Expected: x = 7 (both increments happen)
    Possible race condition result: x = 6!
    (Both read x=5, both compute x+1=6, both write 6 → lost one increment!)

THREE REQUIREMENTS for correct critical section solution:
  1. MUTUAL EXCLUSION:
     If process Pi is in CS, NO other process can be in CS.
     (Only one at a time.)
  2. PROGRESS:
     If no process is in CS and some want to enter → a process
     MUST be selected to enter WITHOUT indefinite postponement.
     (Selection can't be delayed forever.)
  3. BOUNDED WAITING:
     A process waiting to enter CS must eventually enter.
     There's a finite bound on how many times others can enter
     before this waiting process gets in.
     (No starvation in CS entry.)

════════════════════════════════════════════════════════════════════

SEMAPHORE — THE SOLUTION:
  = An integer variable accessed only through two ATOMIC operations:
    WAIT (P, down) and SIGNAL (V, up)

  WAIT(S):           SIGNAL(S):
    while(S <= 0);     S++;
    S--;

  BINARY SEMAPHORE (MUTEX):
    → Value = 0 or 1 only
    → Protects critical section (lock/unlock)
    → S=1: CS is free; S=0: CS is occupied

  COUNTING SEMAPHORE:
    → Value = any non-negative integer
    → Controls access to pool of N identical resources
    → Initial value = N (number of available resources)
    → Each wait() decrements (takes one resource)
    → Each signal() increments (returns one resource)

  DEADLOCK WITH SEMAPHORES:
    P1: wait(S1), then wait(S2)
    P2: wait(S2), then wait(S1)
    → P1 gets S1, P2 gets S2.
    → P1 waits for S2 (held by P2).
    → P2 waits for S1 (held by P1).
    → DEADLOCK! → Circular wait condition.
    → SOLUTION: Always acquire semaphores in SAME ORDER (resource ordering!)

MUTEX vs SEMAPHORE:
  MUTEX:      = Binary lock with OWNERSHIP
              = Only the thread that locked it can unlock it
              = Strictly for mutual exclusion
  SEMAPHORE:  = No ownership concept
              = Any thread can call signal()
              = Used for both mutual exclusion AND synchronization
              = More general than mutex

MONITOR:
  = High-level synchronization construct (OOP approach)
  = Encapsulates shared data + synchronization procedures
  = Only one process active inside monitor at a time
  = Simpler to use correctly than raw semaphores
  = Used in: Java (synchronized methods), C# (lock keyword)
```

---

## 📊 CS DAY 73 — MASTER TRAP TABLE

```
TOPIC                   CORRECT FACT                          TRAP TO AVOID
──────────────────────────────────────────────────────────────────────────────
Threads share           CODE SECTION + DATA SECTION           "Threads share
                        (BOTH — always this pair)              everything"

Thread stack            Each thread has OWN STACK             "Threads share stack"
                        (NOT shared — critical PYQ fact!)

Context switch during   NO USEFUL WORK is done                "CPU works faster
switch                  (pure overhead)                        during switch"

TAT formula             TAT = CT − AT                         "TAT = CT − BT"
                        ← very commonly confused              (wrong!)

WT formula              WT = TAT − BT = (CT − AT) − BT       "WT = CT − BT"
                        ← most common calculation error!      (wrong!)

FCFS weakness           CONVOY EFFECT ← named PYQ term        "Starvation" (FCFS
                        (long process blocks short ones)        never starves anyone)

SJF weakness            STARVATION of long processes           "Convoy effect"
                        ← same issue as SSTF disk              (that's FCFS)

SRTF                    Optimal MINIMUM average waiting time   "FCFS is optimal"
                        (preemptive SJF)                       or "RR is optimal"

Round Robin + large q   Degenerates to FCFS behavior           "Always better than
                        ← exact PYQ trap                        FCFS regardless of q"

Round Robin starvation  NO STARVATION (rotation = fair)        "RR can starve"
                                                               (it cannot)

Deadlock conditions     ALL 4 must hold SIMULTANEOUSLY         "Any 1 condition
                        (remove ANY ONE → no deadlock)          causes deadlock"

Circular wait fix       Resource ORDERING (most practical)     "Allow preemption"
                        (assign numbers, request increasing)    (that's for no-preemption)

Aging                   Solution to STARVATION in Priority     "Aging solves deadlock"
                        and SJF scheduling                     (it does NOT)

Banker's Algorithm      Deadlock AVOIDANCE                     "Deadlock detection"
                        (checks SAFE STATE before granting)    or "prevention"

Ostrich Algorithm       What REAL OS use (Linux, Windows)      "Real OS use Banker's"
                        = IGNORE deadlocks                     (too expensive)

Priority Inversion      HIGH-priority process waits for        "Normal starvation"
                        LOW-priority process (resource lock)

Binary Semaphore        Value = 0 or 1 ONLY                    "Any integer value"
                        (for mutual exclusion)

Race Condition          Result depends on EXECUTION ORDER       "Always produces wrong
                        (non-deterministic)                     result every time"
──────────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS CONCEPT NOTES
## 📚 Education Policy — NEP 2020 + RTE + Education in India (ZERO GAPS)

---

## 🔷 TOPIC 1: NATIONAL EDUCATION POLICY 2020 — COMPLETE DEEP DIVE

```
NEP 2020 — BACKGROUND AND OVERVIEW:
════════════════════════════════════════════════════════════════════

DATE:         Approved by Union Cabinet on JULY 29, 2020
REPLACES:     National Education Policy 1986 (gap of 34 YEARS)
VISION:       Equitable and vibrant knowledge society
GOAL:         Universal high-quality education by 2030
              India a global knowledge superpower by 2040

DRAFTED BY:   K. KASTURIRANGAN COMMITTEE
  ← BPSC DIRECT PYQ: "NEP 2020 drafted by K. Kasturirangan Committee"
  → K. Kasturirangan = former chairman of ISRO (Indian Space Research Organisation)
  → He chaired the committee that wrote NEP 2020

EARLIER COMMITTEE (for historical context):
  → Kothari Commission (1964–66) → led to NEP 1968
  → NEP 1986 → Modified Plan of Action 1992
  → Subramanian Committee (2016) → initial draft
  → K. Kasturirangan Committee → FINAL NEP 2020

════════════════════════════════════════════════════════════════════

THE 5+3+3+4 STRUCTURE — BIGGEST STRUCTURAL CHANGE:
════════════════════════════════════════════════════════════════════

OLD STRUCTURE (10+2):           NEW STRUCTURE (5+3+3+4):
  10 years school (1–10)
  2 years higher secondary       ┌─────────────────────────────┐
  (11–12)                        │ STAGE 1: FOUNDATIONAL        │
                                 │ Duration: 5 years           │
                                 │ Ages: 3–8 years             │
                                 │ Classes: Pre-school (3 yrs) │
                                 │          + Class 1 & 2      │
                                 │ Method: Play-based,         │
                                 │   activity-based learning   │
                                 │ Includes anganwadi/pre-school│
                                 ├─────────────────────────────┤
                                 │ STAGE 2: PREPARATORY        │
                                 │ Duration: 3 years           │
                                 │ Ages: 8–11 years            │
                                 │ Classes: 3, 4, 5            │
                                 │ Method: Activity-based,     │
                                 │   discovery learning        │
                                 ├─────────────────────────────┤
                                 │ STAGE 3: MIDDLE             │
                                 │ Duration: 3 years           │
                                 │ Ages: 11–14 years           │
                                 │ Classes: 6, 7, 8            │
                                 │ Method: Subject-based       │
                                 │ CODING starts from CLASS 6  │
                                 ├─────────────────────────────┤
                                 │ STAGE 4: SECONDARY          │
                                 │ Duration: 4 years           │
                                 │ Ages: 14–18 years           │
                                 │ Classes: 9, 10, 11, 12      │
                                 │ Method: Flexible subjects   │
                                 │   (no rigid stream division)│
                                 └─────────────────────────────┘

← BPSC: NEP 2020 = 5+3+3+4 (not 10+2)
← BPSC: Coding introduced from CLASS 6
← BPSC: Foundational stage = Pre-school to Class 2 (Age 3–8)

════════════════════════════════════════════════════════════════════

KEY SCHOOL EDUCATION CHANGES (NEP 2020):
════════════════════════════════════════════════════════════════════

1. MEDIUM OF INSTRUCTION — MOTHER TONGUE:
   → Recommended: Mother tongue/regional language as medium
     of instruction up to at least CLASS 5
   → Preferably till CLASS 8 or beyond
   → No student forced to learn in a language they don't understand
   → Multilingual education encouraged
   ← BPSC: Mother tongue medium = at least Class 5 minimum

2. NO RIGID STREAM SEPARATION:
   → OLD: Science / Commerce / Arts = completely separate streams
   → NEW: Students can mix ANY subjects freely
     Example: Study Physics + History + Music + Computer Science together
   → Vocational education integrated from CLASS 6 (coding, carpentry, etc.)
   → Idea: Holistic education, not compartmentalized streams

3. CODING FROM CLASS 6:
   → Coding/computational thinking as part of curriculum from Class 6
   ← BPSC PYQ: Coding from which class? = CLASS 6

4. BOARD EXAMINATIONS:
   → Board exams (Class 10 and Class 12) held TWICE PER YEAR
   → Students can choose their BEST SCORE
   → Focus on testing COMPETENCIES, not rote memorization
   → Modular assessments throughout the year

5. REPORT CARDS — HOLISTIC ASSESSMENT:
   → Not just marks — 360-degree assessment
   → STUDENT self-assessment + peer assessment + teacher assessment
   → Cognitive, affective, psychomotor domains all evaluated
   → No single high-stakes examination defining everything

6. NATIONAL ASSESSMENT CENTRE — PARAKH:
   → PARAKH = Performance Assessment, Review and Analysis of Knowledge
              for Holistic Development
   ← BPSC: PARAKH = National Assessment Centre under NEP 2020

7. EARLY CHILDHOOD CARE AND EDUCATION (ECCE):
   → Major emphasis on pre-school education (Age 3–6)
   → Anganwadis upgraded to provide quality ECCE
   → National curriculum and pedagogical framework for ECCE

════════════════════════════════════════════════════════════════════

KEY HIGHER EDUCATION CHANGES (NEP 2020):
════════════════════════════════════════════════════════════════════

1. 4-YEAR UNDERGRADUATE DEGREE with MULTIPLE EXIT OPTIONS:
   ← BPSC KEY CHANGE: UG = 4 years (was 3 years)

   YEAR 1 EXIT → CERTIFICATE
   YEAR 2 EXIT → DIPLOMA
   YEAR 3 EXIT → BACHELOR'S DEGREE (regular)
   YEAR 4 EXIT → BACHELOR'S DEGREE with RESEARCH (Hons.)

   → If a student leaves after 2 years due to financial/family reasons
     → gets a DIPLOMA (not empty-handed)
   → Can RE-ENTER college later with their credits intact

2. ACADEMIC BANK OF CREDITS (ABC):
   → All credits earned by a student stored DIGITALLY in a bank
   → Credits transferable across institutions
   → Student can take a break and return — credits preserved
   → Encourages lifelong learning + flexibility
   ← BPSC: ABC = store and transfer credits across institutions

3. MPhil ABOLISHED:
   → M.Phil (Master of Philosophy) degree discontinued
   → Students go directly from Master's to Ph.D.
   ← BPSC DIRECT FACT: MPhil abolished = NEP 2020 decision

4. UGC TO BE REPLACED BY HECI:
   → UGC = University Grants Commission (old regulator)
   → Replaced by HECI = Higher Education Commission of India
   → HECI has 4 verticals:
     • NHERC = National Higher Education Regulatory Council (regulation)
     • NAC   = National Accreditation Council (accreditation)
     • HEGC  = Higher Education Grants Council (funding)
     • GEC   = General Education Council (academic standards)
   ← BPSC: UGC replaced by HECI under NEP 2020

5. MULTIDISCIPLINARY EDUCATION:
   → IITs must offer arts, humanities, social sciences
   → IIMs must offer science and technology
   → All universities/colleges → multidisciplinary by 2040
   → Liberal arts education emphasized

6. FOREIGN UNIVERSITIES IN INDIA:
   → Top-ranked foreign universities allowed to set up CAMPUSES in India
   → India's best institutions allowed to offer programs abroad

7. GROSS ENROLLMENT RATIO (GER) TARGETS:
   → School GER: 100% by 2030 (Universal School Education)
   → Higher Education GER: 50% by 2035 (from ~26% in 2020)

════════════════════════════════════════════════════════════════════

NEP 2020 KEY NUMERICAL TARGETS:
  → Education spending:     6% of GDP ← (currently ~3–4%)
  → School GER:             100% by 2030
  → Higher Education GER:   50% by 2035
  → Teachers trained:       All teachers re-trained by 2030
  → 5 crore learners:       Through Open/Distance Learning by 2030

NEP 2020 TECHNOLOGY FOCUS:
  → DIKSHA:  Digital Infrastructure for Knowledge Sharing
             ← online learning platform for teachers & students
  → SWAYAM:  Study Webs of Active Learning for Young Aspiring Minds
             ← free online courses for higher education
  → NPTEL:   National Programme on Technology Enhanced Learning
             ← IIT-led online courses
  → Virtual Labs, AI in education, digital libraries

NEP 2020 TEACHER EDUCATION:
  → By 2030: ALL teachers must have B.Ed qualification
  → 4-year integrated B.Ed introduced
     (after Class 12 → 4 years → both degree + B.Ed)
  → Teacher quality = central focus of NEP
  ← Directly relevant to BPSC TRE (you are one of these teachers!)
```

---

## 🔷 TOPIC 2: RIGHT TO EDUCATION ACT 2009 — COMPLETE

```
RTE ACT — FULL OVERVIEW:
════════════════════════════════════════════════════════════════════

FULL NAME:      The Right of Children to Free and Compulsory
                Education Act, 2009 (RTE Act)
ENACTED:        2009
IN FORCE FROM:  April 1, 2010
BASIS:          Article 21A of Indian Constitution
                (Added by 86th Constitutional Amendment, 2002)

WHAT IT GUARANTEES:
  → FREE and COMPULSORY elementary education for all children
    aged 6 TO 14 YEARS
  ← BPSC: RTE = free education for children aged 6 TO 14 (not 0–6, not 6–18)
  → Government schools: NO fees, NO capitation fees
  → COMPULSORY: Government AND local authorities MUST ensure
    every child of this age is enrolled and attending school

KEY PROVISIONS:
════════════════════════════════════════════════════════════════════

1. 25% RESERVATION IN PRIVATE SCHOOLS:
   → Private UNAIDED schools must reserve 25% of seats
     for children from ECONOMICALLY WEAKER SECTIONS (EWS)
     and DISADVANTAGED GROUPS
   → Government reimburses private schools for these 25% students
   ← BPSC PYQ: RTE private school reservation = 25% for EWS

2. PUPIL-TEACHER RATIO (PTR):
   → PRIMARY (Classes 1–5):      1 teacher per 30 students (1:30)
   → UPPER PRIMARY (Classes 6–8): 1 teacher per 35 students (1:35)
   ← BPSC: Primary PTR = 30:1; Upper Primary = 35:1

3. NO DETENTION POLICY:
   → Original: Child CANNOT be detained (failed/held back) until Class 8
   → Amendment 2019: States CAN conduct examinations in Class 5 and Class 8
     If child fails → given a re-examination → if fails again → MAY be detained
   ← Current position: No automatic detention but exams allowed from Class 5

4. SCHOOL WITHIN WALKING DISTANCE:
   → PRIMARY SCHOOL: Within 1 KM of every habitation
   → UPPER PRIMARY SCHOOL: Within 3 KM of every habitation

5. MIDDAY MEAL:
   → Connected to RTE — nutritional support to retain children in school
   → Cooked midday meal provided in government schools

6. TRAINED TEACHERS:
   → All teachers must have prescribed qualifications (NCTE norms)
   → Teachers without qualification given time to acquire it

7. NO CORPORAL PUNISHMENT:
   → Physical punishment and mental harassment of children PROHIBITED
   → Schools must be child-friendly environments

RTE AND NEP 2020 INTERACTION:
  → RTE: Legal framework (MANDATORY, ENFORCEABLE)
  → NEP: Policy framework (ASPIRATIONAL, GUIDELINES)
  → RTE covers ages 6–14; NEP extends vision to age 3–18
  → NEP 2020 recommends extending RTE provisions to ages 3–6 (pre-school)
    and 14–18 (secondary education)
```

---

## 🔷 TOPIC 3: EDUCATION — CONSTITUTIONAL AND POLICY FRAMEWORK

```
CONSTITUTIONAL PROVISIONS:
════════════════════════════════════════════════════════════════════

ARTICLE 21A: RIGHT TO EDUCATION (Fundamental Right)
  → Added by 86th Amendment, 2002
  → "State shall provide free and compulsory education to all children
    of the age of six to fourteen years"
  → Made FUNDAMENTAL RIGHT (Part III) → enforceable in court

ARTICLE 45 (DPSP):
  → Original provision: "State shall endeavour to provide free and
    compulsory education for all children until they complete age 14"
  → After 86th Amendment: Modified to focus on EARLY CHILDHOOD CARE
    for children below 6 years
  → Now: DPSP for early childhood care + education for under-6

ARTICLE 46 (DPSP):
  → Promotion of educational and economic interests of
    Scheduled Castes, Scheduled Tribes, and other weaker sections
  → State to protect them from social injustice and exploitation

EDUCATION IN CONCURRENT LIST:
  ← BPSC DIRECT FACT: Education = CONCURRENT LIST
  → BOTH Parliament AND State Legislatures can make laws on education
  → Added to Concurrent List by: 42ND AMENDMENT (1976)
    [Before 1976: Education was in STATE LIST]
  ← "Education shifted from State List to Concurrent List by 42nd Amendment 1976"

════════════════════════════════════════════════════════════════════

EDUCATION REGULATORY BODIES IN INDIA:
  BODY        FULL NAME                          REGULATES
  ──────────────────────────────────────────────────────────────────
  UGC         University Grants Commission       Universities, higher education
  AICTE       All India Council for Technical    Technical education (Engg, MBA,
              Education                          Pharmacy, Architecture)
  NMC/MCI     National Medical Commission        Medical education (MBBS, MD...)
  BCI         Bar Council of India               Legal education (LLB, LLM)
  NCTE        National Council for Teacher       TEACHER EDUCATION (B.Ed, D.El.Ed)
              Education                          ← Most relevant for BPSC!
  NCERT       National Council of Educational    Curriculum, textbooks, research
              Research and Training              for school education
  NUEPA/NIEPA National Institute of Educational  Education planning, management
              Planning and Administration
  ──────────────────────────────────────────────────────────────────

NCTE (NATIONAL COUNCIL FOR TEACHER EDUCATION) — BPSC FOCUS:
  → Statutory body established under NCTE Act 1993
  → Sets MINIMUM QUALIFICATION NORMS for teachers
  → Approves teacher education colleges (B.Ed colleges)
  → Frames curriculum for teacher training programs
  → Sets eligibility criteria for teacher recruitment
  → Key qualifications set by NCTE:
    D.El.Ed: Diploma in Elementary Education (for primary teachers)
    B.Ed:    Bachelor of Education (for secondary teachers)
    CTET/TET: Teacher Eligibility Test (mandatory to clear)
  ← BPSC TRE is the Bihar recruitment test AFTER clearing Bihar STET
    (which itself is regulated by NCTE norms)

LITERACY IN INDIA (Census 2011 — most recent for exam use):
  → Overall literacy rate:  74.04%
  → Male literacy:          82.14%
  → Female literacy:        65.46%
  → Highest literacy state: KERALA (~94%)
  → Bihar literacy:         ~63.82% (below national average)
  → Most literate district: Serchhip (Mizoram)

════════════════════════════════════════════════════════════════════

IMPORTANT EDUCATION SCHEMES:
  SCHEME                YEAR    KEY FACT
  ──────────────────────────────────────────────────────────────────
  Midday Meal           1995    Hot cooked meal in schools
  Sarva Shiksha         2001    Universalization of elementary
  Abhiyan (SSA)                 education
  Rashtriya Madhyamik   2009    Quality improvement in secondary
  Shiksha Abhiyan(RMSA)         education
  SAMAGRA SHIKSHA       2018    MERGED SSA + RMSA + Teacher Education
                                (covers Classes 1–12 seamlessly)
  DIKSHA               2017    Digital learning platform
  NEP 2020             2020    Comprehensive education reform
  PM SHRI Schools      2022    Model schools implementing NEP 2020
  ──────────────────────────────────────────────────────────────────
  ← BPSC: Samagra Shiksha = merged SSA + RMSA + Teacher Education

════════════════════════════════════════════════════════════════════

BIHAR EDUCATION — HIGH BPSC PRIORITY:
  → Bihar literacy: ~63.82% (2011 census) < National average 74%
  → Bihar population = 8.58% of India ← BPSC direct PYQ
  → Mukhyamantri Kanya Utthan Yojana: Incentive scheme for girls' education
  → Mukhyamantri Balak/Balika Cycle Yojana: Bicycles for school students
  → Bihar Shiksha Sevi: Education volunteers in rural Bihar schools
  → BPSC TRE 4.0 = Bihar's quality teacher recruitment under NEP goals
  → Bihar has B.Ed colleges regulated by Nalanda Open University, BRABU,
    TMBU, Patna University, etc.
```

---

## 🔷 TOPIC 4: NEP 2020 COMPLETE FACT TABLE FOR MCQs

```
NEP 2020 — EVERY MCQ FACT:
════════════════════════════════════════════════════════════════════

QUESTION                                    ANSWER
──────────────────────────────────────────────────────────────────
NEP 2020 approved by Union Cabinet?        July 29, 2020
Who drafted NEP 2020?                      K. Kasturirangan Committee
K. Kasturirangan was former chairman of?   ISRO
NEP 2020 replaced?                         NEP 1986 (gap = 34 years)
New school structure in NEP 2020?          5+3+3+4 (NOT 10+2)
Foundational stage = which classes?        Pre-school (3 yrs) + Class 1–2
Foundational stage = which ages?           3 to 8 years
Preparatory stage = which classes?         Class 3, 4, 5
Preparatory stage = which ages?            8 to 11 years
Middle stage = which classes?              Class 6, 7, 8
Middle stage = which ages?                 11 to 14 years
Secondary stage = which classes?           Class 9, 10, 11, 12
Secondary stage = which ages?              14 to 18 years
Coding introduced from which class?        CLASS 6
Mother tongue medium till which class?     At least CLASS 5 (preferably 8)
Are streams (Science/Arts/Commerce) rigid? NO — students can mix freely
UG degree duration in NEP 2020?            4 YEARS
1-year UG exit = ?                         CERTIFICATE
2-year UG exit = ?                         DIPLOMA
3-year UG exit = ?                         Bachelor's Degree (regular)
4-year UG exit = ?                         Bachelor's with Research (Hons.)
MPhil abolished?                           YES — NEP 2020
Academic Bank of Credits (ABC)?            Stores/transfers credits digitally
National Assessment Centre in NEP?         PARAKH
PARAKH full form?                          Performance Assessment, Review
                                           and Analysis of Knowledge for
                                           Holistic Development
UGC replaced by?                           HECI (Higher Education Commission
                                           of India)
Education spending target?                 6% of GDP
Higher Education GER target by 2035?       50%
School GER target by 2030?                 100%
Board exams frequency in NEP?              TWICE per year
Digital learning platform in NEP?          DIKSHA
India knowledge superpower target year?    2040
4-year integrated B.Ed after?              Class 12 (directly)

RTE ACT FACTS:
RTE Act enacted year?                      2009
RTE Act in force from?                     April 1, 2010
Constitutional basis?                      Article 21A
86th Amendment added Article 21A in?       2002
Age group covered?                         6 TO 14 years
EWS reservation in private schools?        25% of seats
PTR for Classes 1–5 (primary)?            1 teacher per 30 students (1:30)
PTR for Classes 6–8 (upper primary)?      1 teacher per 35 students (1:35)
No detention originally till?              Class 8 (modified in 2019)
Primary school within how many km?         1 KM of habitation

CONSTITUTIONAL EDUCATION FACTS:
Education is in which list?                CONCURRENT LIST
Moved to Concurrent List by?               42nd Amendment, 1976
NCTE regulates?                            Teacher education (B.Ed, D.El.Ed)
Samagra Shiksha merged which schemes?      SSA + RMSA + Teacher Education
Most literate state in India?              KERALA (~94%)
Bihar literacy (2011 census)?              ~63.82%
Bihar's % of India's population?           8.58%
──────────────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED PYQ + CONCEPT MCQs — Day 73 (CS + GS)

---

### COMPUTER SCIENCE — 25 MCQs (Threads, CPU Scheduling, Deadlocks)

---

**Q1.** Which of the following resources are SHARED by threads belonging to the SAME PROCESS?
(A) Stack and Program Counter
(B) CODE SECTION and DATA SECTION (global variables)
(C) Stack, CPU registers and Thread ID
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is NOT SHARED between threads of the same process?
(A) Code section (program instructions)
(B) Heap (dynamically allocated memory)
(C) STACK — each thread has its OWN separate stack
(D) More than one of the above
(E) None of the above

---

**Q3.** A CONTEXT SWITCH involves which of the following operations?
(A) Creating a new process with a fresh address space
(B) SAVING the state (context) of one process and LOADING the saved state of another
(C) Transferring data from RAM to disk during memory shortage
(D) More than one of the above
(E) None of the above

---

**Q4.** The CONVOY EFFECT is a weakness associated with which CPU scheduling algorithm?
(A) Round Robin (time quantum based)
(B) Shortest Job First (SJF)
(C) FCFS — long processes block shorter ones waiting behind them
(D) More than one of the above
(E) None of the above

---

**Q5.** Which CPU scheduling algorithm gives the MINIMUM AVERAGE WAITING TIME?
(A) FCFS (First Come First Served)
(B) Round Robin with very small time quantum
(C) SRTF (Shortest Remaining Time First — preemptive SJF)
(D) More than one of the above
(E) None of the above

---

**Q6.** Processes P1(BT=4), P2(BT=3), P3(BT=5) all arrive at t=0. Using FCFS, the AVERAGE WAITING TIME is:
(A) 3.00
(B) 3.67
(C) 4.33
(D) More than one of the above
(E) None of the above

---

**Q7.** ROUND ROBIN scheduling is ALWAYS:
(A) Non-preemptive — processes run to completion
(B) PREEMPTIVE — processes run for a fixed time quantum then preempted
(C) Based on process priority numbers
(D) More than one of the above
(E) None of the above

---

**Q8.** ALL FOUR of the following conditions must hold SIMULTANEOUSLY for DEADLOCK to occur. Which set is CORRECT?
(A) Mutual Exclusion, Hold & Wait, No Preemption, Circular Wait
(B) Mutual Exclusion, Starvation, Priority Inversion, Race Condition
(C) Hold & Wait, Circular Wait, Aging, Context Switch
(D) More than one of the above
(E) None of the above

---

**Q9.** AGING is the solution to which problem in CPU scheduling?
(A) Deadlock — circular wait between processes
(B) Thrashing — excessive page swapping
(C) STARVATION — low-priority/long processes never getting CPU time
(D) More than one of the above
(E) None of the above

---

**Q10.** The TURNAROUND TIME (TAT) of a process is calculated as:
(A) Burst Time + Arrival Time
(B) COMPLETION TIME − ARRIVAL TIME (CT − AT)
(C) Completion Time − Burst Time
(D) More than one of the above
(E) None of the above

---

**Q11.** The WAITING TIME (WT) of a process is calculated as:
(A) Completion Time − Burst Time
(B) Completion Time − Arrival Time
(C) TURNAROUND TIME − BURST TIME = (CT − AT) − BT
(D) More than one of the above
(E) None of the above

---

**Q12.** If the TIME QUANTUM in Round Robin is made VERY LARGE (bigger than all burst times), RR behaves like:
(A) Shortest Job First (SJF)
(B) Priority Scheduling
(C) FCFS — each process runs to completion (effectively non-preemptive)
(D) More than one of the above
(E) None of the above

---

**Q13.** The BANKER'S ALGORITHM is associated with:
(A) Deadlock PREVENTION — breaking one of the four conditions
(B) Deadlock AVOIDANCE — checking for safe state before granting resources
(C) Deadlock DETECTION — finding cycles in resource allocation graph
(D) More than one of the above
(E) None of the above

---

**Q14.** CIRCULAR WAIT (deadlock condition) is most PRACTICALLY PREVENTED by:
(A) Making all resources sharable (eliminating mutual exclusion)
(B) Requiring processes to request all resources at once (eliminating hold & wait)
(C) ASSIGNING UNIQUE NUMBERS to resources and requiring requests in INCREASING ORDER
(D) More than one of the above
(E) None of the above

---

**Q15.** What is a SAFE STATE in the context of Banker's Algorithm?
(A) A state where no process is currently blocked or waiting
(B) A state where a SAFE SEQUENCE exists allowing all processes to complete
(C) A state where all resources are currently unallocated and free
(D) More than one of the above
(E) None of the above

---

**Q16.** The OSTRICH ALGORITHM for deadlock handling means:
(A) Killing all deadlocked processes immediately like an ostrich attacks predators
(B) IGNORING deadlocks completely — doing nothing about them
(C) Detecting deadlocks and migrating processes to other CPUs
(D) More than one of the above
(E) None of the above

---

**Q17.** Process P1(AT=0, BT=6, Priority=3), P2(AT=0, BT=3, Priority=1), P3(AT=0, BT=4, Priority=2). Using NON-PREEMPTIVE PRIORITY (1=highest), what is the ORDER of execution?
(A) P1 → P2 → P3
(B) P2 → P3 → P1
(C) P3 → P1 → P2
(D) More than one of the above
(E) None of the above

---

**Q18.** STARVATION in SJF scheduling is caused by:
(A) The CPU quantum expiring too frequently
(B) Long processes may NEVER get CPU when shorter processes keep arriving
(C) Processes losing their priority over time
(D) More than one of the above
(E) None of the above

---

**Q19.** A BINARY SEMAPHORE can have values:
(A) Any positive integer (used to count available resources)
(B) 0 OR 1 ONLY (used for mutual exclusion to protect critical sections)
(C) Only the value 0 (locked state always)
(D) More than one of the above
(E) None of the above

---

**Q20.** HOLD AND WAIT (deadlock condition) means a process:
(A) Requests all needed resources before starting execution
(B) HOLDS at least one resource AND WAITS for additional resources held by others
(C) Releases all held resources before requesting new ones
(D) More than one of the above
(E) None of the above

---

**Q21.** Using ROUND ROBIN with TQ=2, processes P1(AT=0,BT=5), P2(AT=0,BT=3), P3(AT=0,BT=4). What is the COMPLETION TIME of P2?
(A) P2 finishes at t=7
(B) P2 finishes at t=8
(C) P2 finishes at t=9
(D) More than one of the above
(E) None of the above

---

**Q22.** MUTUAL EXCLUSION as a deadlock condition means:
(A) Processes must mutually agree before using a resource
(B) At least one resource is NON-SHARABLE — only one process can use it at a time
(C) Multiple processes can use all resources simultaneously
(D) More than one of the above
(E) None of the above

---

**Q23.** THRASHING in an operating system is caused by:
(A) Too many threads sharing the same stack
(B) EXCESSIVE PAGING ACTIVITY — processes spend more time swapping pages than executing
(C) Too many context switches in Round Robin scheduling
(D) More than one of the above
(E) None of the above

---

**Q24.** The PCB (Process Control Block) stores which of the following?
(A) Process ID, process state, program counter, CPU registers
(B) Only the process ID and arrival time
(C) Only the program counter and stack pointer
(D) More than one of the above
(E) None of the above

---

**Q25.** A RACE CONDITION occurs when:
(A) CPU scheduling algorithm always selects the fastest process
(B) Multiple processes access SHARED DATA concurrently and the RESULT DEPENDS ON EXECUTION ORDER
(C) Two processes race to acquire CPU in a preemptive system
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs (Education Policy)

---

**Q26.** The National Education Policy 2020 (NEP 2020) was drafted by which committee?
(A) Kothari Commission
(B) K. Kasturirangan Committee
(C) Yashpal Committee
(D) More than one of the above
(E) None of the above

---

**Q27.** NEP 2020 was approved by the Union Cabinet on which date?
(A) October 2, 2020
(B) August 15, 2020
(C) July 29, 2020
(D) More than one of the above
(E) None of the above

---

**Q28.** NEP 2020 replaced which earlier National Education Policy?
(A) NEP 1968 (Kothari Commission-based)
(B) NEP 1986 (gap of 34 years)
(C) NEP 2005
(D) More than one of the above
(E) None of the above

---

**Q29.** The NEW SCHOOL STRUCTURE introduced by NEP 2020 is:
(A) 10+2 (unchanged from before)
(B) 6+3+3+2
(C) 5+3+3+4 — Foundational, Preparatory, Middle, Secondary
(D) More than one of the above
(E) None of the above

---

**Q30.** Under NEP 2020, the FOUNDATIONAL STAGE covers:
(A) Class 1 to Class 5 (age 6–11)
(B) Pre-school (3 years) plus Class 1 and Class 2 (age 3–8)
(C) Only the pre-school years (age 3–5)
(D) More than one of the above
(E) None of the above

---

**Q31.** CODING as a subject is introduced from which CLASS under NEP 2020?
(A) Class 1 (from the very beginning)
(B) Class 4
(C) Class 6
(D) More than one of the above
(E) None of the above

---

**Q32.** NEP 2020 recommends MOTHER TONGUE as medium of instruction up to at least:
(A) Class 2 only (foundational stage)
(B) Class 5 (minimum), preferably till Class 8
(C) Class 10 (end of secondary school)
(D) More than one of the above
(E) None of the above

---

**Q33.** Under NEP 2020, the UNDERGRADUATE DEGREE duration is:
(A) 3 years (same as before — no change)
(B) 5 years (like medical and law degrees)
(C) 4 YEARS with multiple exit options (Certificate/Diploma/Degree)
(D) More than one of the above
(E) None of the above

---

**Q34.** What does a student receive upon exiting the undergraduate program after 2 YEARS under NEP 2020?
(A) Certificate
(B) Diploma
(C) Bachelor's degree (regular)
(D) More than one of the above
(E) None of the above

---

**Q35.** The ACADEMIC BANK OF CREDITS (ABC) under NEP 2020 allows students to:
(A) Receive direct loans from banks for education without interest
(B) STORE CREDITS DIGITALLY and TRANSFER them across institutions, enabling flexibility
(C) Convert academic credits into scholarship amounts
(D) More than one of the above
(E) None of the above

---

**Q36.** Which degree was ABOLISHED under NEP 2020?
(A) B.Ed (Bachelor of Education)
(B) MBA (Master of Business Administration)
(C) MPhil (Master of Philosophy)
(D) More than one of the above
(E) None of the above

---

**Q37.** PARAKH, mentioned in NEP 2020, is:
(A) A new scholarship scheme for meritorious students
(B) NATIONAL ASSESSMENT CENTRE — Performance Assessment, Review and Analysis of Knowledge for Holistic Development
(C) A portal for teacher registration and certification
(D) More than one of the above
(E) None of the above

---

**Q38.** Under NEP 2020, Board examinations for Classes 10 and 12 will be held:
(A) Once per year (same as current system)
(B) TWICE PER YEAR (students take the best of two attempts)
(C) Three times per year for maximum flexibility
(D) More than one of the above
(E) None of the above

---

**Q39.** The RIGHT TO EDUCATION ACT provides free and compulsory education for children aged:
(A) 3 to 14 years
(B) 6 TO 14 YEARS
(C) 6 to 18 years
(D) More than one of the above
(E) None of the above

---

**Q40.** Under the RTE Act, PRIVATE UNAIDED schools must reserve seats for EWS children. The percentage reserved is:
(A) 10%
(B) 15%
(C) 25%
(D) More than one of the above
(E) None of the above

---

**Q41.** The CONSTITUTIONAL BASIS for the Right to Education (RTE Act 2009) is:
(A) Article 45 — DPSP for education
(B) Article 21A — added by 86th Amendment (2002)
(C) Article 51A — Fundamental Duties
(D) More than one of the above
(E) None of the above

---

**Q42.** Under the RTE Act, the PUPIL-TEACHER RATIO for PRIMARY school (Classes 1–5) is:
(A) 1 teacher per 25 students
(B) 1 teacher per 30 students (1:30)
(C) 1 teacher per 40 students
(D) More than one of the above
(E) None of the above

---

**Q43.** EDUCATION in India is in which LIST of the Seventh Schedule of the Constitution?
(A) Union List (only Parliament)
(B) State List (only State)
(C) CONCURRENT LIST (both Parliament and States)
(D) More than one of the above
(E) None of the above

---

**Q44.** Education was shifted to the CONCURRENT LIST by which Constitutional Amendment?
(A) 44th Amendment (1978)
(B) 86th Amendment (2002)
(C) 42nd Amendment (1976)
(D) More than one of the above
(E) None of the above

---

**Q45.** NEP 2020 proposes to replace UGC with:
(A) NCTE (National Council for Teacher Education)
(B) HECI (Higher Education Commission of India)
(C) AICTE (All India Council for Technical Education)
(D) More than one of the above
(E) None of the above

---

**Q46.** SAMAGRA SHIKSHA ABHIYAN (2018) was formed by merging which schemes?
(A) Midday Meal Scheme + DIKSHA + PARAKH
(B) Sarva Shiksha Abhiyan (SSA) + Rashtriya Madhyamik Shiksha Abhiyan (RMSA) + Teacher Education
(C) NEP 1986 + RTE 2009 + DIKSHA programs
(D) More than one of the above
(E) None of the above

---

**Q47.** The DIKSHA PLATFORM mentioned in NEP 2020 context is:
(A) A government financial scheme for girls' higher education
(B) A digital learning platform — Digital Infrastructure for Knowledge Sharing — for teachers and students
(C) A centralized teacher transfer portal
(D) More than one of the above
(E) None of the above

---

**Q48.** Bihar's population is approximately what PERCENTAGE of India's total population?
(A) 5.5%
(B) 8.58%
(C) 12.3%
(D) More than one of the above
(E) None of the above

---

**Q49.** MATCH THE FOLLOWING — NEP 2020 stages with correct class ranges:
```
Stage          Class Range / Age
1. Foundational  A. Class 6, 7, 8 (Age 11–14)
2. Preparatory   B. Pre-school + Class 1, 2 (Age 3–8)
3. Middle        C. Class 9, 10, 11, 12 (Age 14–18)
4. Secondary     D. Class 3, 4, 5 (Age 8–11)
```
(A) 1-B, 2-D, 3-A, 4-C
(B) 1-A, 2-B, 3-C, 4-D
(C) 1-C, 2-A, 3-D, 4-B
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following statements about the NCTE (National Council for Teacher Education) is CORRECT?
(A) NCTE directly conducts CTET and all state TETs
(B) NCTE is a statutory body that regulates TEACHER EDUCATION institutions and sets minimum qualification norms for teachers
(C) NCTE was established under the 73rd Constitutional Amendment 1992
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
| 1  | (B)    | Threads share CODE SECTION + DATA SECTION ← exact BPSC PYQ phrase |
| 2  | (C)    | STACK = NOT shared; each thread has its OWN STACK ← PYQ |
| 3  | (B)    | Context switch = SAVE state of one process + LOAD state of another (via PCB) |
| 4  | (C)    | CONVOY EFFECT = FCFS weakness (long process blocks all shorter ones behind it) |
| 5  | (C)    | SRTF (preemptive SJF) = globally optimal minimum average waiting time |
| 6  | (B)    | FCFS P1→P2→P3; WTs: P1=0, P2=4(CT=4+3=7,AT=0,TAT=7,WT=7-3=4), P3=7(CT=12,TAT=12,WT=7); avg=(0+4+7)/3=11/3=3.67 |
| 7  | (B)    | Round Robin = ALWAYS PREEMPTIVE (time quantum based) ← exam fact |
| 8  | (A)    | 4 Coffman conditions: Mutual Exclusion + Hold & Wait + No Preemption + Circular Wait |
| 9  | (C)    | AGING = solution to STARVATION (gradually increases priority of waiting processes) |
| 10 | (B)    | TAT = COMPLETION TIME − ARRIVAL TIME (CT − AT) ← exact formula |
| 11 | (C)    | WT = TAT − BT = (CT − AT) − BT ← most commonly confused formula |
| 12 | (C)    | Large time quantum → RR degenerates to FCFS (processes finish within quantum) ← PYQ |
| 13 | (B)    | Banker's = deadlock AVOIDANCE (checks SAFE STATE before granting resources) |
| 14 | (C)    | Circular wait prevention = resource ORDERING (numbers + increasing-order requests) |
| 15 | (B)    | Safe state = safe sequence EXISTS allowing all processes to eventually complete |
| 16 | (B)    | Ostrich Algorithm = IGNORE deadlocks completely (what real OS do) ← PYQ |
| 17 | (B)    | Priority 1=highest: P2(priority 1) → P3(priority 2) → P1(priority 3) |
| 18 | (B)    | SJF starvation = long processes may NEVER get CPU when short ones keep arriving |
| 19 | (B)    | Binary semaphore = 0 or 1 ONLY (mutex for critical section protection) |
| 20 | (B)    | Hold & Wait = process HOLDS one resource AND WAITS for more from others |
| 21 | (C)    | RR TQ=2: t=0-2(P1), 2-4(P2), 4-6(P3), 6-8(P1), 8-9(P2 finishes, only 1 left) = t=9 |
| 22 | (B)    | Mutual exclusion = resource NON-SHARABLE (only one process at a time) |
| 23 | (B)    | Thrashing = EXCESSIVE PAGING ACTIVITY (process spends more time paging than executing) |
| 24 | (A)    | PCB stores: PID, process state, PC, CPU registers, memory info, file handles, etc. |
| 25 | (B)    | Race condition = shared data access where result DEPENDS ON EXECUTION ORDER |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 26 | (B)    | NEP 2020 drafted by K. KASTURIRANGAN Committee ← direct PYQ fact |
| 27 | (C)    | NEP 2020 approved: July 29, 2020 |
| 28 | (B)    | NEP 2020 replaced NEP 1986 (34-year gap) |
| 29 | (C)    | NEP 2020 = 5+3+3+4 (Foundational + Preparatory + Middle + Secondary) ← key change |
| 30 | (B)    | Foundational = Pre-school (3 yrs) + Class 1–2 = Age 3–8 |
| 31 | (C)    | Coding introduced from CLASS 6 under NEP 2020 |
| 32 | (B)    | Mother tongue: at least Class 5 (minimum), preferably till Class 8 |
| 33 | (C)    | UG = 4 YEARS with multiple exit options under NEP 2020 ← major change |
| 34 | (B)    | 2-year UG exit = DIPLOMA |
| 35 | (B)    | ABC = store and TRANSFER CREDITS DIGITALLY across institutions |
| 36 | (C)    | MPhil ABOLISHED under NEP 2020 (Masters → directly PhD) |
| 37 | (B)    | PARAKH = National Assessment Centre (full form is key) |
| 38 | (B)    | Board exams = TWICE PER YEAR under NEP 2020 |
| 39 | (B)    | RTE = free education for ages 6 TO 14 years |
| 40 | (C)    | RTE private school EWS reservation = 25% of seats |
| 41 | (B)    | Article 21A (86th Amendment 2002) = constitutional basis of RTE |
| 42 | (B)    | PTR for Classes 1–5 = 1:30 (one teacher per 30 students) |
| 43 | (C)    | Education = CONCURRENT LIST (both Parliament and States can legislate) |
| 44 | (C)    | Education moved to Concurrent List by 42nd AMENDMENT (1976) ← PYQ |
| 45 | (B)    | UGC replaced by HECI (Higher Education Commission of India) under NEP |
| 46 | (B)    | Samagra Shiksha = merged SSA + RMSA + Teacher Education (2018) |
| 47 | (B)    | DIKSHA = Digital Infrastructure for Knowledge Sharing |
| 48 | (B)    | Bihar population = 8.58% of India ← direct BPSC PYQ |
| 49 | (A)    | Foundational=B(pre+Cl1-2), Preparatory=D(Cl3-5), Middle=A(Cl6-8), Secondary=C(Cl9-12) |
| 50 | (B)    | NCTE = statutory body regulating teacher education institutions + minimum qualifications |

---
---

# 🔁 NIGHT REVISION SHEET
## 📌 Day 73 — Ultra-Crisp "Last 30 Minutes Before Sleep"

---

### ⚡ CS — THREADS + SCHEDULING + DEADLOCKS: 22 MUST-KNOW FACTS

```
THREADS (PYQ #1 pair — memorize exact phrasing):
1.  Threads SHARE:      CODE SECTION + DATA SECTION ← exact BPSC phrase
2.  Threads DON'T SHARE: STACK — each thread has OWN STACK ← exact phrase
3.  Also own: Program Counter, CPU Registers, Thread ID

SCHEDULING FORMULAS:
4.  TAT = CT − AT          (Turnaround = Completion − Arrival)
5.  WT  = TAT − BT         (Waiting = Turnaround − Burst)
    = (CT − AT) − BT       ← most common exam calculation error!
    WRONG: WT = CT − BT    ← this is the trap

SCHEDULING ALGORITHMS:
6.  FCFS = NON-preemptive | CONVOY EFFECT ← named weakness | NO starvation
7.  SJF  = NON-preemptive | Minimum avg WT | STARVATION possible
8.  SRTF = Preemptive SJF | OPTIMAL minimum avg WT (globally best)
9.  Priority = Preemptive or non | STARVATION → AGING = solution
10. Round Robin = ALWAYS PREEMPTIVE | time quantum | NO starvation
    Large TQ → RR degenerates to FCFS ← PYQ trap
    Used in: TIME-SHARING OS (connect Day 68 + Day 73)

DEADLOCK — 4 CONDITIONS (all 4 MUST hold):
11. MUTUAL EXCLUSION:  Resource non-sharable (1 process at a time)
12. HOLD AND WAIT:     Holds one resource + waits for more
13. NO PREEMPTION:     OS can't forcibly take resource from process
14. CIRCULAR WAIT:     Circular chain P1→P2→P3→...→P1
    Trick: "My House Needs Cleaning" = M-H-N-C

DEADLOCK PREVENTION:
15. Circular wait = MOST PRACTICAL to prevent:
    Resource ORDERING — assign numbers, request in INCREASING order

DEADLOCK STRATEGIES:
16. Prevention = break one condition structurally
17. Avoidance  = Banker's Algorithm — check SAFE STATE before granting
18. Detection  = allow deadlocks, find cycles, kill/preempt to recover
19. Ostrich   = IGNORE IT = what real OS (Linux/Windows) actually use!

SYNC + MISC:
20. Aging      = STARVATION solution (gradually increase priority)
21. Binary semaphore = 0 or 1 = MUTEX (for critical section)
22. Thrashing  = EXCESSIVE PAGING (process spends more time paging than executing)
23. Race condition = shared data + result depends on EXECUTION ORDER
```

---

### ⚡ GS — EDUCATION POLICY: 20 MUST-KNOW FACTS

```
NEP 2020:
1.  NEP 2020 approved: July 29, 2020 | Drafted by: K. KASTURIRANGAN Committee
2.  Replaced: NEP 1986 | New structure: 5+3+3+4 (NOT 10+2)
    5 = Foundational (pre-school to Class 2, Age 3–8)
    3 = Preparatory  (Class 3–5, Age 8–11)
    3 = Middle       (Class 6–8, Age 11–14) ← Coding from Class 6!
    4 = Secondary    (Class 9–12, Age 14–18)
3.  Mother tongue medium: minimum Class 5 (preferably till Class 8)
4.  No rigid streams: Students can mix Science + Arts + Commerce subjects
5.  UG = 4 YEARS: 1yr=Certificate, 2yr=Diploma, 3yr=Bachelor's, 4yr=Bachelor's+Research
6.  MPhil ABOLISHED | ABC = Academic Bank of Credits (store+transfer)
7.  PARAKH = National Assessment Centre
8.  HECI replaces UGC | DIKSHA = digital learning platform
9.  Board exams: TWICE per year | Education spending target: 6% GDP
10. GER target: 100% school by 2030 | 50% higher education by 2035
11. India knowledge superpower target: 2040

RTE ACT:
12. RTE Act 2009; in force April 1, 2010; basis: Article 21A (86th Amend. 2002)
13. Free education for ages 6 TO 14 years
14. Private schools = 25% EWS reservation | PTR: Primary=1:30; Upper Primary=1:35

CONSTITUTIONAL + POLICY:
15. Education = CONCURRENT LIST (moved by 42nd Amendment, 1976)
16. NCTE = regulates teacher education; sets minimum qualification norms
17. Samagra Shiksha (2018) = SSA + RMSA + Teacher Education merged
18. Bihar population = 8.58% of India ← direct BPSC PYQ
19. Most literate state = KERALA (~94%)
20. Bihar literacy = ~63.82% (2011 census, below national 74.04%)
```

---

### ⚡ TOMORROW — DAY 74: OS COMPLETE REVISION

```
Day 74 = OS REVISION ONLY (Days 68–73)
Tick every item after revision:

OS CHECKLIST (from your study plan):
  [ ] Time-sharing OS = beginning of COMPUTER COMMUNICATIONS (Day 68)
  [ ] Fragmentation = PROBLEM — NOT a technique (Day 70)
  [ ] Compaction = shifts processes; ALL free → ONE BLOCK (Day 70)
  [ ] TLB = ASSOCIATIVE CACHE (Day 69)
  [ ] 4KB page → 12-bit offset (2¹²=4096) (Day 69)
  [ ] Thrashing = EXCESSIVE PAGING ACTIVITY (Day 70 + Day 73)
  [ ] Threads share: code + data (NOT stack) (Day 73) ← TODAY
  [ ] FCFS disk scheduling = 640 cylinders (Day 71)
  [ ] Memory-mapped I/O = SHARED address space (Day 72)
  [ ] Polling = PROGRAM-CONTROLLED I/O (checks status flags) (Day 72)
  [ ] Buffer registers = overcome SPEED DIFFERENCE between devices (Day 70)
  [ ] PCI bus = EXTENDS CONNECTIVITY OF PROCESSOR BUS (Day 72)
  [ ] Secondary memory = LOGICAL organization (Day 68 + Day 72)
  [ ] NOT a valid interrupt type: MEMORY INTERRUPT (Day 68)
  [ ] Deadlock = ALL 4 conditions must hold simultaneously (Day 73)
  [ ] Segment BASE = STARTING PHYSICAL ADDRESS (Day 70)
  [ ] Banker's = deadlock AVOIDANCE (Day 73)
  [ ] Ostrich = IGNORE deadlocks (real OS approach) (Day 73)
  [ ] SCAN = ELEVATOR ALGORITHM (Day 71)
  [ ] SSTF starvation / SCAN no starvation (Day 71)
```

---

## 🎯 WEEK 11 COMPLETE — ALL 6 DAYS DONE!

```
Day 68: OS Introduction & Types              ✅ DONE
Day 69: Paging (Complete)                    ✅ DONE
Day 70: Segmentation + Virtual Memory        ✅ DONE
Day 71: Disk Scheduling (Complete)           ✅ DONE
Day 72: I/O Management + File Systems        ✅ DONE
Day 73: Threads + CPU Scheduling + Deadlocks ← TODAY ✅
Day 74: OS Complete Revision (Tomorrow)
```

---

*Day 73 Complete | Week 11 of 25 COMPLETE | Phase 2: Depth | Target: TOP 50 RANK*
