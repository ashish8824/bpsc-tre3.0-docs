# 📅 BPSC TRE 4.0 — DAY 68: OS INTRODUCTION + INDIAN CONSTITUTION
### Week 11 Begins — OS Types, Process States, Interrupts & Secondary Memory
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — OS Types, Time-sharing, Process States, Interrupts
> - Afternoon (1 hr): GS — Indian Constitution: Preamble + Fundamental Rights
> - Evening (1.5 hrs): Solve all 50 MCQs
> - Night (30 min): Read the Night Revision Sheet

---

# PART 1: CS CONCEPT NOTES
## 📘 Operating Systems — Introduction & Fundamentals

---

## 🔷 TOPIC 1: What is an Operating System?

```
OPERATING SYSTEM = System software that acts as
                   INTERFACE between USER and HARDWARE

OS Core Functions:
  1. Process Management    → scheduling, execution
  2. Memory Management     → RAM allocation / deallocation
  3. File Management       → create, delete, read, write files
  4. Device Management     → controls I/O devices
  5. Security & Protection → user access control

KERNEL = CORE part of OS
       = always resident in memory
       = manages all resources

KEY: OS = resource manager (manages CPU, memory, I/O devices)
```

---

## 🔷 TOPIC 2: Types of Operating Systems — THE Exam Topic

```
TYPE              HOW IT WORKS                               KEY FACT / PYQ TRAP
──────────────────────────────────────────────────────────────────────────────────
Batch OS          Jobs grouped into batches; no user         No user interaction
                  interaction during execution               during execution

Time-sharing OS   Multiple users share CPU in small          MARKS BEGINNING OF
                  time slices (time quantum)                 COMPUTER COMMUNICATIONS
                  ← TRE 1.0 Q41 — HIGH PROBABILITY!         ← PYQ TRAP

Real-time OS      Responds within guaranteed time            Hard RTOS = missed deadline
(RTOS)            Hard RTOS: strict deadline (e.g., pacemaker)  = system failure
                  Soft RTOS: deadline missed = degraded      Used in embedded systems
                  performance (e.g., video streaming)

Embedded OS       Designed for specific hardware             e.g., washing machine,
                  Limited memory, single function            smartwatch, ATM kiosks

Network OS        Manages network resources; provides        e.g., Windows Server,
                  file sharing across a network              Novell NetWare

Distributed OS    Manages multiple CPUs appearing as         Transparent to user —
                  single system to the user                  looks like one computer

Multi-programming Multiple programs loaded in memory;        Maximizes CPU utilization
                  CPU switches when one waits for I/O        (CPU never idle)

Multi-tasking     Multiple tasks running concurrently        = time-sharing in practice
                  on a single CPU via time slicing

Multi-processing  Multiple CPUs (processors) working         True parallel execution
                  simultaneously                             (actual parallelism)
──────────────────────────────────────────────────────────────────────────────────

PYQ TRAP #1: Time-sharing OS → marks the BEGINNING of COMPUTER COMMUNICATIONS
PYQ TRAP #2: Multi-programming ≠ Multi-processing
             Multi-programming = one CPU, multiple programs in memory
             Multi-processing  = multiple CPUs, true parallelism
PYQ TRAP #3: Real-time OS is used in EMBEDDED SYSTEMS (e.g., pacemaker, missile systems)
```

---

## 🔷 TOPIC 3: Process vs Program vs Thread

```
PROGRAM   = Passive entity — just code stored on DISK
            A set of instructions; does NOT execute by itself

PROCESS   = Active entity — program IN EXECUTION
            Has: code + data + stack + heap + PCB
            Created when program starts running

THREAD    = Lightweight process
            Shares: code section + data section (of same process)
            Does NOT share: STACK (each thread has its own stack!)
            ← PYQ TRAP: threads share code+data, NOT stack

PROCESS CONTROL BLOCK (PCB):
  = Data structure maintained by OS for each process
  Contains: Process ID, State, Program Counter, CPU registers,
            Memory limits, Open files, Priority

KEY COMPARISONS:
  Program → stored on disk, no execution
  Process → executing program, in RAM, has PCB
  Thread  → unit within process, shares process memory
```

---

## 🔷 TOPIC 4: Process States — THE 5-State Diagram

```
        ┌──────────────────────────────────────────────────────────┐
        │           PROCESS STATE TRANSITION DIAGRAM               │
        └──────────────────────────────────────────────────────────┘

              admit              dispatch
  NEW ──────────────► READY ──────────────► RUNNING
                       ▲                      │    │
                       │     interrupt        │    │ exit
               I/O     │◄─────────────────────┘    │
              complete │                           ▼
                       │                      TERMINATED
               WAITING ◄── I/O or event wait ──────┘
                              (from RUNNING)

STATES:
  NEW        → Process just created; not yet ready to run
  READY      → Process loaded in RAM, waiting for CPU time
  RUNNING    → Process currently being executed by CPU
  WAITING    → Process waiting for I/O or an event (BLOCKED)
               ← also called BLOCKED state
  TERMINATED → Process finished execution; resources released

TRANSITIONS (PYQ-tested):
  NEW → READY:      OS admits the process (loaded into memory)
  READY → RUNNING:  CPU scheduler dispatches it
  RUNNING → READY:  Timer interrupt (time slice expired)
  RUNNING → WAITING:Process requests I/O (waits for completion)
  WAITING → READY:  I/O completes / event occurs
  RUNNING → TERMINATED: Process finishes or is killed

KEY TRAP: A process goes NEW → READY → RUNNING (never NEW → RUNNING directly!)
KEY TRAP: WAITING ≠ READY — waiting = blocked on I/O; ready = waiting for CPU only
```

---

## 🔷 TOPIC 5: Types of Interrupts — EXAM TRAP

```
INTERRUPT = Signal to CPU to PAUSE current task and handle
            a higher-priority event

TYPES OF INTERRUPTS:
──────────────────────────────────────────────────────────────────
Hardware Interrupt    Caused by external devices (keyboard, mouse,
                      disk, timer, NIC) sending signal to CPU
                      e.g., "key pressed", "disk read complete"

Software Interrupt    Caused by running programs (system calls)
                      e.g., program requests OS service
                      (divide by zero error, segfault)

Trap (Exception)      Special software interrupt — caused by ERROR
                      or exceptional condition in user program
                      e.g., division by zero, invalid memory access
                      = "synchronous interrupt" ← also called this

Maskable Interrupt    Can be IGNORED or DELAYED by CPU
                      (CPU can disable it temporarily)

Non-Maskable (NMI)    CANNOT be ignored by CPU
                      Used for critical events (power failure, hardware error)
──────────────────────────────────────────────────────────────────

#1 PYQ TRAP: "Memory interrupt" does NOT exist!
             If you see "Memory interrupt" as an option → it is WRONG
             ← TRE exam tested this directly

VALID types to remember: Hardware, Software, Trap, Maskable, Non-Maskable
INVALID / DOES NOT EXIST: "Memory interrupt"
```

---

## 🔷 TOPIC 6: Secondary Memory — Organization Type

```
MEMORY HIERARCHY (fastest to slowest):
  Registers > Cache (L1/L2/L3) > RAM (Primary) > Secondary Memory

SECONDARY MEMORY:
  = Long-term / permanent storage
  = Non-volatile (data persists when power off)
  = Examples: HDD, SSD, USB drive, optical discs
  = Much slower than RAM but much larger capacity

SECONDARY MEMORY ORGANIZATION = LOGICAL (not physical/structural)
   ← This is a direct PYQ trap
   ← "Physical organization of secondary memory" is NOT the correct term
   ← Correct answer = LOGICAL organization

WHY LOGICAL?
  OS treats secondary memory in terms of FILES and DIRECTORIES
  (logical structures) — not in terms of physical sectors/tracks
  The FILE SYSTEM provides logical organization to secondary memory

TYPES OF MEMORY (Quick Comparison):
──────────────────────────────────────────────────────────────────
Primary Memory (RAM):    Volatile, fast, directly accessible by CPU
Secondary Memory (HDD):  Non-volatile, slow, stores files long-term
Cache Memory:            Fastest, costliest, bridges CPU-RAM speed gap
Virtual Memory:          Extends RAM using secondary storage (HDD/SSD)
──────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 7: Batch OS vs Time-sharing — Deep Comparison

```
FEATURE           BATCH OS               TIME-SHARING OS
──────────────────────────────────────────────────────────────────
User interaction  None during job        Continuous (interactive)
Response time     Hours/minutes          Seconds (fast)
CPU use           Sequential jobs        Round-robin time slices
User count        Single job at a time   Multiple simultaneous users
Resource sharing  No                     Yes
Error feedback    After job ends         Immediate
Historical role   Early mainframes       Marks beginning of
                                         COMPUTER COMMUNICATIONS ←PYQ
Examples          Early payroll systems  Unix, Windows multi-user
──────────────────────────────────────────────────────────────────

REMEMBER: Time-sharing = BEGINNING OF COMPUTER COMMUNICATIONS
          This exact fact appeared in TRE 1.0 Q41
```

---

## 📊 OS INTRODUCTION — MASTER TRAP TABLE

```
TOPIC              CORRECT FACT                       COMMON TRAP
───────────────────────────────────────────────────────────────────────────
Time-sharing OS    Marks beginning of computer         Students write "batch OS"
                   communications                      for first OS type

Memory interrupt   DOES NOT EXIST                      Students mark it as valid
                   ← not a valid interrupt type        interrupt type

Secondary memory   LOGICAL organization                Students write "physical"
                   (not physical/structural)           or "structural"

Multi-programming  One CPU, multiple jobs in memory    Students confuse with
                   (maximizes CPU use)                 multi-processing

Multi-processing   Multiple CPUs working in parallel   Students confuse with
                   (true parallel execution)           multi-programming

Process states     5 states: New→Ready→Running         Students think process
                   →Waiting→Terminated                 can skip Ready state

Thread             Shares code+data; NOT stack          Students say thread
                   Each thread has its own stack       shares everything

RTOS               Hard RTOS = strict deadline          Students confuse hard
                   Soft RTOS = degraded on miss         and soft RTOS

Kernel             Core of OS; always in memory        Students confuse with
                                                       entire OS
───────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS CONCEPT NOTES
## 🏛️ Indian Constitution — Preamble + Fundamental Rights

---

## 🔷 MASTER FACTS: INDIAN CONSTITUTION

```
CONSTITUTION QUICK FACTS
══════════════════════════════════════════════════════════════════

Constituent Assembly:
  → First met:       December 9, 1946
  → President of CA: Dr. Rajendra Prasad (Bihar's son!) ← BPSC HIGH PRIORITY
  → Chairman, Drafting Committee: Dr. B.R. Ambedkar

Constitution:
  → Adopted:         November 26, 1949 (Constitution Day)
  → Came into force: January 26, 1950 (Republic Day)

  → Original: 395 Articles | 8 Schedules | 22 Parts
  → Current:  ~470 Articles| 12 Schedules| 25 Parts (after amendments)

Borrowed from:
  → UK:        Parliamentary system, Rule of Law, Writs
  → USA:       Fundamental Rights, Judicial Review, Impeachment,
                Preamble idea, Supreme Court
  → Ireland:   DPSP (Directive Principles of State Policy)
  → Canada:    Federal system with strong Centre
  → Australia: Concurrent List, Joint sitting of Parliament
  → Germany:   Emergency provisions
  → USSR:      Fundamental Duties, 5-year plans (historical)
  → South Africa: Amendment procedure (Article 368)

══════════════════════════════════════════════════════════════════
```

---

## 🔷 THE PREAMBLE — Word by Word

```
PREAMBLE TEXT (Memorize structure):

"WE, THE PEOPLE OF INDIA, having solemnly resolved to constitute
India into a SOVEREIGN SOCIALIST SECULAR DEMOCRATIC REPUBLIC
and to secure to all its citizens:

JUSTICE      — Social, Economic and Political
LIBERTY      — of thought, expression, belief, faith and worship
EQUALITY     — of status and of opportunity
FRATERNITY   — assuring the dignity of the individual and the
                unity and integrity of the Nation

DO HEREBY ADOPT, ENACT AND GIVE TO OURSELVES THIS CONSTITUTION"

KEY FACTS:
  → "SOCIALIST" and "SECULAR" were added by 42nd Amendment (1976)
  → "UNITY OF THE NATION" → changed to "UNITY AND INTEGRITY" by 42nd Amendment
  → "WE, THE PEOPLE" = ultimate authority = POPULAR SOVEREIGNTY
  → Enacted: November 26, 1949
  → Preamble = NOT enforceable in court (NOT a Fundamental Right)
  → Preamble = part of Constitution (Kesavananda Bharati case, 1973)
  → Preamble can be AMENDED (Kesavananda Bharati case established this)

WHAT INDIA IS CALLED:
  → SOVEREIGN  = no external authority controls India
  → SOCIALIST  = equal distribution of wealth (added 1976)
  → SECULAR    = no state religion; all religions equal (added 1976)
  → DEMOCRATIC = government by elected representatives
  → REPUBLIC   = elected head of state (President, not hereditary king)
```

---

## 🔷 FUNDAMENTAL RIGHTS — Part III (Articles 12–35)

```
FUNDAMENTAL RIGHTS — 6 CATEGORIES
══════════════════════════════════════════════════════════════════

RIGHT 1: RIGHT TO EQUALITY (Articles 14–18)
  Art 14: Equality before law + Equal protection of law
  Art 15: No discrimination on grounds of religion, race,
          caste, sex, place of birth
  Art 16: Equality of opportunity in public employment
  Art 17: ABOLITION OF UNTOUCHABILITY ← PYQ trap (not just banned)
  Art 18: Abolition of titles (except military/academic)

RIGHT 2: RIGHT TO FREEDOM (Articles 19–22)
  Art 19: 6 freedoms (SIR CAPS mnemonic):
    → Speech and expression
    → Peaceful assembly (without arms)
    → Association / union formation
    → Free movement throughout India
    → Residence and settlement anywhere in India
    → Practice any profession / trade / business
  Art 20: Protection against arbitrary conviction
          (no double jeopardy, no ex-post-facto law,
           no self-incrimination)
  Art 21: RIGHT TO LIFE AND PERSONAL LIBERTY ← Most litigated FR
          → includes right to privacy (K.S. Puttaswamy, 2017)
          → includes right to livelihood, right to health
  Art 21A: RIGHT TO EDUCATION (6–14 years) ← added by 86th Amendment (2002)
  Art 22: Protection against arbitrary arrest and detention

RIGHT 3: RIGHT AGAINST EXPLOITATION (Articles 23–24)
  Art 23: Prohibition of human trafficking and forced labour
          (begar = forced labour without payment ← PYQ word)
  Art 24: No child labour in factories/mines (under 14 years)
          ← BPSC tests this age: UNDER 14

RIGHT 4: RIGHT TO FREEDOM OF RELIGION (Articles 25–28)
  Art 25: Freedom of conscience and free profession/practice of religion
  Art 26: Freedom to manage religious affairs
  Art 27: No tax compulsion for promoting a religion
  Art 28: No religious instruction in State-funded institutions

RIGHT 5: CULTURAL AND EDUCATIONAL RIGHTS (Articles 29–30)
  Art 29: Right of minorities to conserve their culture/language/script
  Art 30: Right of minorities to establish and administer
          educational institutions

RIGHT 6: RIGHT TO CONSTITUTIONAL REMEDIES (Article 32)
  Art 32: Dr. Ambedkar called it "HEART AND SOUL OF THE CONSTITUTION"
          → Right to move Supreme Court for enforcement of FRs
          → CANNOT be suspended except during national emergency
          → Grantor of all other rights (if no Art 32, FRs are useless)

══════════════════════════════════════════════════════════════════
```

---

## 🔷 WRITS — THE 5 CONSTITUTIONAL WRITS

```
WRITS (issued by SC under Art 32, HC under Art 226):

WRIT              MEANING / LITERAL TRANSLATION     PURPOSE
──────────────────────────────────────────────────────────────────────
Habeas Corpus     "You may have the body"            Release illegally
                                                     detained person
                                                     ← most important for
                                                     personal liberty

Mandamus          "We command"                       Command public
                                                     official to perform
                                                     legal duty

Prohibition       "To forbid"                        Prevent lower court
                                                     from exceeding
                                                     jurisdiction

Certiorari        "To be certified"                  Quash/review order
                                                     of lower court

Quo Warranto      "By what authority"                Challenge authority
                                                     of person holding
                                                     public office
──────────────────────────────────────────────────────────────────────

MEMORY TRICK: H-M-P-C-Q → "Hungry Men Prefer Chicken Quiche"
Habeas | Mandamus | Prohibition | Certiorari | Quo Warranto

KEY FACTS:
  → Habeas Corpus = available against both private AND public authority
  → Mandamus = NOT issued against private individuals or President/Governor
  → Prohibition = issued ONLY to judicial/quasi-judicial bodies
  → Certiorari = issued to judicial/quasi-judicial bodies (corrects errors)
  → Quo Warranto = issued against persons holding public office
```

---

## 🔷 KEY ARTICLES — BPSC EXAM FREQUENCY

```
ARTICLE    SUBJECT                                        EXAM FREQUENCY
──────────────────────────────────────────────────────────────────────────
Art 1      India = "Union of States" (not federation)    ★★★
Art 12     Definition of "State" for FR purposes         ★★★
Art 14     Equality before law                           ★★★
Art 17     Abolition of untouchability                   ★★★★ (PYQ)
Art 19     6 Freedoms (SIR CAPS)                         ★★★★ (PYQ)
Art 21     Right to life and personal liberty            ★★★★★ (MOST)
Art 21A    Right to Education (6-14 years, 86th Amend.)  ★★★★
Art 24     No child labour under 14 years                ★★★★
Art 32     Constitutional remedies (Heart & Soul)        ★★★★★ (PYQ)
Art 44     Uniform Civil Code (DPSP)                     ★★★
Art 51A    Fundamental Duties (42nd Amendment 1976)      ★★★
Art 112    Union Budget / Annual Financial Statement      ★★
Art 324    Election Commission of India                  ★★★
Art 356    President's Rule (Art 356 = State Emergency)  ★★★★
Art 368    Constitutional Amendment procedure            ★★★
──────────────────────────────────────────────────────────────────────────

FUNDAMENTAL DUTIES (Art 51A):
  → Added by: 42nd Amendment, 1976
  → Recommended by: Swaran Singh Committee
  → Number: 10 duties originally; 11th added by 86th Amendment (2002)
  → 11th duty: "provide education opportunities to children aged 6–14"
  → These are NOT justiciable (cannot be enforced in court)

DPSP vs FUNDAMENTAL RIGHTS:
  DPSP = non-justiciable (Part IV, Art 36–51) → state goals
  FRs  = justiciable (Part III, Art 12–35) → enforceable in court
  If conflict: FRs generally prevail (but Art 31C gives some DPSP precedence)
```

---

## 🔷 AMENDMENTS — TOP 5 FOR BPSC

```
AMENDMENT   YEAR   KEY CHANGE
──────────────────────────────────────────────────────────────────
42nd        1976   Added "Socialist" + "Secular" to Preamble
                   Added Fundamental Duties (Art 51A)
                   "Unity of Nation" → "Unity AND INTEGRITY"

44th        1978   Right to Property removed from FRs
                   (became legal right under Art 300A)
                   Restored some provisions changed by 42nd

73rd        1992   Panchayati Raj — Constitutional status
                   3-tier system (village / block / district)

74th        1992   Urban Local Bodies — Constitutional status
                   Municipalities, Municipal Corporations

86th        2002   Art 21A: Free & compulsory education (6–14 yrs)
                   Added 11th Fundamental Duty
──────────────────────────────────────────────────────────────────

PYQ TRAP: Right to Property was originally Article 19(1)(f) and Article 31
          → Removed as Fundamental Right by 44th Amendment (1978)
          → Now a LEGAL RIGHT under Article 300A (not a FR anymore!)

PYQ TRAP: "Socialist" and "Secular" in Preamble = 42nd Amendment (1976)
          NOT part of the original 1950 Constitution
```

---

## 🔷 BIHAR-SPECIFIC CONSTITUTIONAL FACTS

```
BIHAR CONNECTION TO CONSTITUTION
══════════════════════════════════════════════════════════════════

Rajendra Prasad:
  → Born: Zeradei, Siwan, BIHAR
  → President of Constituent Assembly (Dec 9, 1946)
  → Signed the Constitution: November 26, 1949
  → First President of India: January 26, 1950
  → Served TWO TERMS (12 years) = Longest serving President

Bihar's Political History:
  → Bihar split: November 15, 2000 → Jharkhand carved out
  → Bihar State Day: March 22 (Bihar Diwas)
  → Bihar Governor's role: Article 153–167

Preamble and Bihar:
  → "We, the People" — Rajendra Prasad (Bihar) presided when adopted

══════════════════════════════════════════════════════════════════
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED PYQ + CONCEPT MCQs — Day 68 (CS + GS)

---

### COMPUTER SCIENCE — 25 MCQs (OS Introduction)

---

**Q1.** Which type of Operating System marks the BEGINNING OF COMPUTER COMMUNICATIONS?
(A) Batch Operating System
(B) Real-time Operating System
(C) Time-sharing Operating System
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is NOT a valid type of interrupt in a computer system?
(A) Hardware Interrupt
(B) Software Interrupt
(C) Memory Interrupt
(D) More than one of the above
(E) None of the above

---

**Q3.** The organization of secondary memory is best described as:
(A) Physical organization
(B) Structural organization
(C) Logical organization
(D) More than one of the above
(E) None of the above

---

**Q4.** In which process state does a process wait for completion of an I/O operation?
(A) Ready
(B) Running
(C) Waiting (Blocked)
(D) More than one of the above
(E) None of the above

---

**Q5.** What is the difference between multi-programming and multi-processing?
(A) Multi-programming = multiple CPUs; Multi-processing = multiple jobs in memory
(B) Multi-programming = multiple jobs in memory with one CPU; Multi-processing = multiple CPUs
(C) Both are exactly the same concept
(D) More than one of the above
(E) None of the above

---

**Q6.** Which part of the Operating System always remains in main memory during execution?
(A) Shell
(B) Kernel
(C) Compiler
(D) More than one of the above
(E) None of the above

---

**Q7.** What does PCB stand for and what does it contain?
(A) Program Counter Block — contains only the program counter register
(B) Process Control Block — contains process ID, state, registers, memory info
(C) Processor Cache Buffer — contains recently used instructions
(D) More than one of the above
(E) None of the above

---

**Q8.** A thread within a process shares which of the following with other threads of the SAME process?
(A) Stack only
(B) Code section and Data section
(C) Stack, Code section, and Data section (everything)
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following transitions in the process state diagram is INVALID?
(A) New → Ready
(B) Ready → Running
(C) New → Running (directly, skipping Ready)
(D) More than one of the above
(E) None of the above

---

**Q10.** Which OS type is used in a pacemaker (heart implant device)?
(A) Time-sharing OS
(B) Batch OS
(C) Hard Real-time OS
(D) More than one of the above
(E) None of the above

---

**Q11.** What is the CORRECT sequence of process state transitions from creation to termination?
(A) New → Running → Ready → Waiting → Terminated
(B) New → Ready → Running → Terminated (or via Waiting)
(C) Ready → New → Running → Waiting → Terminated
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following CORRECTLY defines an operating system?
(A) A program that translates high-level language to machine code
(B) System software acting as interface between user and hardware
(C) Hardware component that manages CPU operations directly
(D) More than one of the above
(E) None of the above

---

**Q13.** A Trap (exception) interrupt is caused by:
(A) An external device like a keyboard or mouse
(B) An error or exceptional condition in the running program
(C) A network packet arriving at the NIC
(D) More than one of the above
(E) None of the above

---

**Q14.** Which type of interrupt CANNOT be ignored or delayed by the CPU?
(A) Maskable Interrupt
(B) Software Interrupt
(C) Non-Maskable Interrupt (NMI)
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the key difference between a Program and a Process?
(A) A program is active; a process is passive and stored on disk
(B) A program is passive (stored on disk); a process is a program in execution
(C) There is no difference — program and process are the same thing
(D) More than one of the above
(E) None of the above

---

**Q16.** In a time-sharing operating system, the CPU is shared among multiple users using:
(A) Priority queues only
(B) Round-robin scheduling with time slices
(C) Batch processing sequence
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following is TRUE about the WAITING (BLOCKED) state of a process?
(A) The process is waiting for the CPU to become available
(B) The process is waiting for an I/O operation or event to complete
(C) The process has finished execution and is being cleaned up
(D) More than one of the above
(E) None of the above

---

**Q18.** Secondary memory is characterized by which of the following?
(A) Volatile — data lost when power is off
(B) Fastest memory in the system hierarchy
(C) Non-volatile — data persists even when power is off
(D) More than one of the above
(E) None of the above

---

**Q19.** Which scheduling algorithm is typically used in time-sharing operating systems?
(A) First Come First Served (FCFS)
(B) Shortest Job First (SJF)
(C) Round Robin (RR)
(D) More than one of the above
(E) None of the above

---

**Q20.** Multi-programming operating systems maximize which resource?
(A) Disk space utilization
(B) CPU utilization
(C) Network bandwidth
(D) More than one of the above
(E) None of the above

---

**Q21.** What happens when a process moves from RUNNING to READY state?
(A) The process has requested an I/O operation
(B) The process has been preempted (e.g., timer interrupt — time slice expired)
(C) The process has completed execution
(D) More than one of the above
(E) None of the above

---

**Q22.** In which type of OS are jobs processed in groups WITHOUT user interaction during execution?
(A) Time-sharing OS
(B) Distributed OS
(C) Batch OS
(D) More than one of the above
(E) None of the above

---

**Q23.** Each thread in a process has its own separate:
(A) Code section
(B) Data section
(C) Stack
(D) More than one of the above
(E) None of the above

---

**Q24.** A distributed operating system manages:
(A) A single CPU with multiple programs in memory
(B) Multiple CPUs appearing as a single system to the user
(C) Multiple users sharing a single machine through time slices
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is the CORRECT description of the KERNEL?
(A) A utility program that compiles source code
(B) The core part of the OS that manages resources and always stays in memory
(C) An application layer that handles user interface only
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs (Indian Constitution)

---

**Q26.** The Constituent Assembly of India first met on which date?
(A) January 26, 1950
(B) November 26, 1949
(C) December 9, 1946
(D) More than one of the above
(E) None of the above

---

**Q27.** Who was the Chairman of the Drafting Committee of the Indian Constitution?
(A) Dr. Rajendra Prasad
(B) Jawaharlal Nehru
(C) Dr. B.R. Ambedkar
(D) More than one of the above
(E) None of the above

---

**Q28.** The words "SOCIALIST" and "SECULAR" were added to the Preamble by which Constitutional Amendment?
(A) 44th Amendment (1978)
(B) 42nd Amendment (1976)
(C) 73rd Amendment (1992)
(D) More than one of the above
(E) None of the above

---

**Q29.** Article 21A (Right to Education for children aged 6–14) was added by which amendment?
(A) 42nd Amendment, 1976
(B) 73rd Amendment, 1992
(C) 86th Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q30.** Dr. B.R. Ambedkar called which Article the "Heart and Soul of the Constitution"?
(A) Article 14 (Right to Equality)
(B) Article 21 (Right to Life)
(C) Article 32 (Right to Constitutional Remedies)
(D) More than one of the above
(E) None of the above

---

**Q31.** Article 17 of the Indian Constitution deals with:
(A) Abolition of titles
(B) Abolition of untouchability
(C) Equal protection of law
(D) More than one of the above
(E) None of the above

---

**Q32.** The Right to Property was removed as a Fundamental Right by which amendment?
(A) 42nd Amendment (1976)
(B) 44th Amendment (1978)
(C) 86th Amendment (2002)
(D) More than one of the above
(E) None of the above

---

**Q33.** Which writ is issued to command a public official to perform a legal duty?
(A) Habeas Corpus
(B) Mandamus
(C) Quo Warranto
(D) More than one of the above
(E) None of the above

---

**Q34.** "Habeas Corpus" literally means:
(A) By what authority
(B) We command
(C) You may have the body
(D) More than one of the above
(E) None of the above

---

**Q35.** Which of the following is CORRECTLY matched as a Fundamental Right under Article 19?
(A) Right to move the Supreme Court for enforcement of FRs
(B) Freedom of speech and expression
(C) Abolition of forced labour (begar)
(D) More than one of the above
(E) None of the above

---

**Q36.** The Fundamental Duties were added to the Constitution by which Amendment and on whose recommendation?
(A) 44th Amendment; Nanavati Committee
(B) 42nd Amendment; Swaran Singh Committee
(C) 86th Amendment; Verma Committee
(D) More than one of the above
(E) None of the above

---

**Q37.** The Indian Constitution was adopted on:
(A) January 26, 1950 (Republic Day)
(B) August 15, 1947 (Independence Day)
(C) November 26, 1949 (Constitution Day)
(D) More than one of the above
(E) None of the above

---

**Q38.** Article 24 of the Indian Constitution prohibits employment of children below which age in factories and mines?
(A) 12 years
(B) 14 years
(C) 18 years
(D) More than one of the above
(E) None of the above

---

**Q39.** The concept of Directive Principles of State Policy (DPSP) was borrowed from which country's constitution?
(A) USA
(B) UK
(C) Ireland
(D) More than one of the above
(E) None of the above

---

**Q40.** Which writ is used to challenge the authority of a person holding a public office?
(A) Certiorari
(B) Prohibition
(C) Quo Warranto
(D) More than one of the above
(E) None of the above

---

**Q41.** Bihar's connection to the Indian Constitution includes which of the following?
(A) Dr. Rajendra Prasad (from Siwan, Bihar) was President of Constituent Assembly
(B) Dr. Rajendra Prasad signed the Constitution on November 26, 1949
(C) Dr. Rajendra Prasad became First President of India on January 26, 1950
(D) More than one of the above
(E) None of the above

---

**Q42.** The Preamble of the Indian Constitution is:
(A) Not part of the Constitution and cannot be amended
(B) Part of the Constitution and can be amended (Kesavananda Bharati case)
(C) Enforceable in a court of law as a Fundamental Right
(D) More than one of the above
(E) None of the above

---

**Q43.** The concept of Judicial Review in India was borrowed from:
(A) Ireland
(B) UK
(C) USA
(D) More than one of the above
(E) None of the above

---

**Q44.** "Begar" as referred to in Article 23 means:
(A) Child labour in factories
(B) Forced labour without payment
(C) Human trafficking for bonded labour
(D) More than one of the above
(E) None of the above

---

**Q45.** Which DPSP article directs the state to secure a Uniform Civil Code for citizens?
(A) Article 40
(B) Article 44
(C) Article 48
(D) More than one of the above
(E) None of the above

---

**Q46.** The Right to Constitutional Remedies under Article 32 can be suspended during:
(A) Financial Emergency (Article 360)
(B) State Emergency / President's Rule (Article 356)
(C) National Emergency (Article 352)
(D) More than one of the above
(E) None of the above

---

**Q47.** The Preamble declares India as a REPUBLIC. What does this mean?
(A) India has a parliamentary system of government
(B) India has an elected (non-hereditary) head of state — the President
(C) India has no official religion
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following Fundamental Rights CANNOT be suspended even during a National Emergency?
(A) Right to Freedom of Speech (Article 19)
(B) Right to Move Freely (Article 19)
(C) Right to Life and Personal Liberty (Article 21)
(D) More than one of the above
(E) None of the above

---

**Q49.** The provision of Concurrent List in the Indian Constitution was borrowed from which country?
(A) USA
(B) Australia
(C) Ireland
(D) More than one of the above
(E) None of the above

---

**Q50.** MATCH THE FOLLOWING — Article and its correct subject:
```
Article      Subject
1. Art 19    A. Abolition of untouchability
2. Art 17    B. 6 Freedoms including speech, movement, profession
3. Art 32    C. No child labour (under 14) in factories/mines
4. Art 24    D. Right to Constitutional Remedies
```
(A) 1-B, 2-A, 3-D, 4-C
(B) 1-A, 2-B, 3-C, 4-D
(C) 1-D, 2-C, 3-B, 4-A
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 1  | (C)    | Time-sharing OS = beginning of computer communications (TRE 1.0 PYQ) |
| 2  | (C)    | "Memory interrupt" does NOT exist — it is not a valid type |
| 3  | (C)    | Secondary memory = LOGICAL organization (not physical/structural) |
| 4  | (C)    | WAITING (Blocked) state = process waiting for I/O/event |
| 5  | (B)    | Multi-programming = one CPU + multiple jobs; Multi-processing = multiple CPUs |
| 6  | (B)    | KERNEL = core of OS, always resides in memory |
| 7  | (B)    | PCB = Process Control Block; contains process ID, state, registers, memory info |
| 8  | (B)    | Threads share code + data sections; EACH thread has own stack |
| 9  | (C)    | New → Running directly is INVALID; must go New → Ready → Running |
| 10 | (C)    | Pacemaker = Hard Real-time OS (strict deadline = system failure) |
| 11 | (B)    | New → Ready → Running → Terminated (with possible detour via Waiting) |
| 12 | (B)    | OS = system software acting as interface between user and hardware |
| 13 | (B)    | Trap = caused by error/exceptional condition in running program |
| 14 | (C)    | Non-Maskable Interrupt (NMI) = cannot be ignored by CPU |
| 15 | (B)    | Program = passive (on disk); Process = active program in execution |
| 16 | (B)    | Time-sharing uses round-robin scheduling with time slices |
| 17 | (B)    | WAITING = waiting for I/O or event (NOT waiting for CPU — that's READY) |
| 18 | (C)    | Secondary memory = non-volatile (data persists without power) |
| 19 | (C)    | Round Robin = standard for time-sharing OS |
| 20 | (B)    | Multi-programming maximizes CPU utilization (CPU never stays idle) |
| 21 | (B)    | Running → Ready = timer interrupt / time slice expired (preemption) |
| 22 | (C)    | Batch OS = jobs processed in groups WITHOUT user interaction |
| 23 | (C)    | Each thread has its OWN STACK (does NOT share stack) |
| 24 | (B)    | Distributed OS = multiple CPUs appearing as ONE system to user |
| 25 | (B)    | Kernel = core of OS; manages resources; always stays in memory |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 26 | (C)    | Constituent Assembly first met: December 9, 1946 |
| 27 | (C)    | Dr. B.R. Ambedkar = Chairman, Drafting Committee |
| 28 | (B)    | 42nd Amendment (1976) added "Socialist" + "Secular" to Preamble |
| 29 | (C)    | 86th Amendment (2002) added Art 21A — Right to Education |
| 30 | (C)    | Art 32 = "Heart and Soul" per Ambedkar — Right to Constitutional Remedies |
| 31 | (B)    | Article 17 = Abolition of Untouchability |
| 32 | (B)    | 44th Amendment (1978) removed Right to Property from FRs |
| 33 | (B)    | Mandamus = "We command" — directs public official to perform legal duty |
| 34 | (C)    | Habeas Corpus = "You may have the body" (release unlawfully detained person) |
| 35 | (B)    | Art 19 includes freedom of speech and expression (one of 6 freedoms) |
| 36 | (B)    | 42nd Amendment, 1976; Swaran Singh Committee recommended FDs |
| 37 | (C)    | Constitution ADOPTED: November 26, 1949 (not Jan 26 which is enforcement) |
| 38 | (B)    | Art 24 = no child labour under 14 years in factories/mines |
| 39 | (C)    | DPSP borrowed from IRELAND (not USA or UK) |
| 40 | (C)    | Quo Warranto = challenges authority of person holding public office |
| 41 | (D)    | All 3 facts about Rajendra Prasad (Bihar) and Constitution are correct |
| 42 | (B)    | Preamble = part of Constitution; CAN be amended (Kesavananda Bharati 1973) |
| 43 | (C)    | Judicial Review borrowed from USA |
| 44 | (B)    | Begar = forced labour WITHOUT payment (Art 23 prohibits it) |
| 45 | (B)    | Art 44 = Uniform Civil Code (DPSP) |
| 46 | (C)    | Art 32 can be suspended ONLY during NATIONAL EMERGENCY (Art 352) |
| 47 | (B)    | Republic = elected head of state (President, not hereditary king) |
| 48 | (C)    | Art 21 (Right to Life) CANNOT be suspended even during National Emergency |
| 49 | (B)    | Concurrent List borrowed from AUSTRALIA |
| 50 | (A)    | Art 19=6 Freedoms(B); Art 17=Untouchability(A); Art 32=Remedies(D); Art 24=Child Labour(C) |

---
---

# 🔁 NIGHT REVISION SHEET
## 📌 Day 68 — Ultra-Crisp "Last 30 Minutes Before Sleep"

---

### ⚡ CS — OS INTRODUCTION: 15 MUST-KNOW FACTS

```
OS TYPES:
1.  Time-sharing OS → marks BEGINNING OF COMPUTER COMMUNICATIONS ← TRE 1.0 PYQ
2.  Batch OS → no user interaction during job execution
3.  Hard RTOS → missed deadline = system FAILURE (e.g., pacemaker)
4.  Distributed OS → multiple CPUs appear as ONE system to user
5.  Multi-programming = 1 CPU + multiple jobs in memory (maximize CPU use)
6.  Multi-processing = multiple CPUs (true parallel execution)

INTERRUPTS:
7.  "Memory interrupt" → DOES NOT EXIST ← direct PYQ trap
8.  Valid types: Hardware, Software, Trap, Maskable, Non-Maskable
9.  NMI (Non-Maskable Interrupt) → CANNOT be ignored by CPU
10. Trap = caused by program error (division by zero, segfault)

PROCESS:
11. 5 states: New → Ready → Running → Waiting / Terminated
12. New → Running DIRECTLY is INVALID (must pass through Ready)
13. Running → Ready: time slice expired (timer interrupt)
14. Running → Waiting: process requests I/O

MEMORY + THREADS:
15. Secondary memory → LOGICAL organization (not physical/structural)
16. Thread shares: code + data | Does NOT share: STACK (own stack per thread)
17. Kernel = core of OS; always stays in main memory
18. PCB = Process Control Block (process ID, state, registers, memory info)
```

---

### ⚡ GS — CONSTITUTION: 15 MUST-KNOW FACTS

```
KEY DATES:
1.  CA first met: December 9, 1946
2.  Constitution ADOPTED: November 26, 1949 (Constitution Day)
3.  Constitution IN FORCE: January 26, 1950 (Republic Day)

KEY PEOPLE:
4.  CA President: Dr. Rajendra Prasad (Siwan, BIHAR) ← BPSC priority
5.  Drafting Committee Chairman: Dr. B.R. Ambedkar

PREAMBLE:
6.  "Socialist" + "Secular" = added by 42nd Amendment (1976)
7.  Preamble = Part of Constitution; CAN be amended (Kesavananda Bharati, 1973)
8.  Preamble = NOT enforceable in court

ARTICLES:
9.  Art 17: Abolition of UNTOUCHABILITY
10. Art 21: Right to Life (most litigated; includes privacy after 2017)
11. Art 21A: Right to Education (6–14 yrs) → 86th Amendment, 2002
12. Art 32: "Heart and Soul" (Ambedkar); Constitutional Remedies
            Can be suspended ONLY during National Emergency (Art 352)
13. Art 24: No child labour UNDER 14 years in factories/mines

WRITS:
14. Habeas Corpus = "You may have the body" (release unlawful detention)
    Mandamus = "We command" (public official perform duty)
    Quo Warranto = "By what authority" (challenge public office)

OTHERS:
15. DPSP borrowed from: IRELAND
    Right to Property removed: 44th Amendment (1978) → now Art 300A (legal right)
    Concurrent List borrowed from: AUSTRALIA
    FDs added by: 42nd Amendment (1976) | Swaran Singh Committee
```

---

### ⚡ TOMORROW — DAY 69 PREVIEW

```
CS:  Paging (Page + Frame + Page Table + TLB + offset bits)
     KEY FACT: 4KB page → 12-bit offset (2¹² = 4096)
     TLB = associative cache (not regular cache) ← TRE PYQ

GS:  Indian Constitution — Parliament + Elections
```

---

## 🎯 WEEK 11 PROGRESS TRACKER

```
Day 68: OS Introduction & Types  ← TODAY ✅
Day 69: Paging
Day 70: Segmentation + Virtual Memory + Compaction
Day 71: Disk Scheduling (FCFS calculation)
Day 72: I/O Management + File Systems
Day 73: Threads + CPU Scheduling + Deadlocks
Day 74: OS Complete Revision + 25 PYQ MCQs
```

---

*Day 68 Complete | Week 11 of 25 | Phase 2: Depth | Target: TOP 50 RANK*
