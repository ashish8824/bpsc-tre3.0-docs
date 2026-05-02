# 📅 BPSC TRE 4.0 — DAY 75: CPU ARCHITECTURE + MATHS SHORTCUTS REVISION
### Week 12 — Computer Architecture + Software Engineering
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — CPU Architecture: ALU, Control Unit, Registers, Cache, Memory Hierarchy, ASCII
> - Afternoon (1 hr): GS — Maths Shortcuts Revision (Percentages, Profit/Loss, Averages, Ratio/Proportion)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 CPU Architecture — All Concepts, One Place

---

## 🔷 TOPIC 1: CPU — The Brain of the Computer

### What is the CPU?
```
CPU = Central Processing Unit = "Brain" of the computer

Function: Fetch → Decode → Execute → Store (FDES cycle)

  FETCH    → Get instruction from RAM
  DECODE   → Understand what operation to perform
  EXECUTE  → Perform the operation (via ALU / CU)
  STORE    → Write result back to register / memory
```

### CPU Internal Structure — ASCII Diagram:
```
┌─────────────────────────────────────────────────────┐
│                      CPU                            │
│                                                     │
│   ┌───────────────────┐   ┌─────────────────────┐  │
│   │   Control Unit    │   │        ALU          │  │
│   │      (CU)         │   │  (Arithmetic &      │  │
│   │                   │   │   Logic Unit)       │  │
│   │  Generates        │   │                     │  │
│   │  CONTROL SIGNALS  │   │  + − × ÷            │  │
│   │                   │   │  AND OR NOT XOR     │  │
│   └────────┬──────────┘   └──────────┬──────────┘  │
│            │                         │              │
│            └──────────┬──────────────┘              │
│                       │                             │
│              ┌────────▼────────┐                    │
│              │   REGISTERS     │                    │
│              │ (Fastest Memory)│                    │
│              │ PC, IR, ACC,    │                    │
│              │ MAR, MDR, SP    │                    │
│              └─────────────────┘                    │
│                                                     │
│   ┌─────────────────────────────────────────────┐  │
│   │       CACHE  (L1 → L2 → L3)                 │  │
│   │  Faster than RAM; stores recently used data  │  │
│   └─────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## 🔷 TOPIC 2: ALU — Arithmetic Logic Unit

### What ALU Does:
```
ALU = Arithmetic Logic Unit

TWO types of operations:
  ARITHMETIC  → Addition, Subtraction, Multiplication, Division
  LOGICAL     → AND, OR, NOT, XOR, NAND, NOR, comparison (<, >, =)

KEY PYQ TRAP:
  ALU performs BOTH arithmetic AND logical operations
  → "ALU performs only arithmetic operations"       = FALSE ← TRAP!
  → "ALU performs arithmetic and logical operations" = TRUE  ✅

ALU does NOT:
  ❌ Generate control signals  (that is CU's job)
  ❌ Fetch instructions        (that is CU's job)
  ❌ Store data permanently    (that is memory's job)
```

### ALU One-Liners for Exam:
```
ALU result stored in  → ACCUMULATOR (ACC) register
ALU is part of        → CPU (NOT separate from CPU)
ALU operations        → arithmetic + logical (BOTH — never forget!)
```

---

## 🔷 TOPIC 3: Control Unit (CU)

### What the Control Unit Does:
```
Control Unit = "Manager / Director" of the CPU

PRIMARY FUNCTION:
  → Generates CONTROL SIGNALS  ← #1 PYQ FACT — memorize!
  → Controls all other units of the computer (ALU, memory, I/O)
  → Directs data flow between CPU components

CONTROL SIGNALS:
  → Electronic signals sent to ALU, registers, memory, I/O devices
  → Tell each component WHEN to act and WHAT to do
  → Example: "ALU, add these two numbers now"
             "Memory, send data to register MDR"
             "Output device, display this value"

Control Unit does NOT:
  ❌ Perform arithmetic operations  (ALU does this)
  ❌ Store data                     (registers/memory do this)
  ❌ Provide power to components
```

### CU PYQ Traps:
```
TRAP 1: "Control unit performs logical operations"  → FALSE (ALU does this)
TRAP 2: "Control unit stores frequently used data"  → FALSE (Cache does this)
TRAP 3: What does control unit generate?            → CONTROL SIGNALS ← answer this!
```

---

## 🔷 TOPIC 4: Registers — The Fastest Memory

### What Are Registers?
```
Registers = Tiny, ultra-fast storage locations INSIDE the CPU

FASTEST in the memory hierarchy (faster than cache, RAM, disk)
Size: very small (typically 8, 16, 32, or 64 bits)
Purpose: hold data currently being processed
```

### Important CPU Registers — PYQ Level:
```
REGISTER   FULL NAME                    PURPOSE
────────────────────────────────────────────────────────────────
PC         Program Counter              Holds address of NEXT instruction
IR         Instruction Register         Holds CURRENT instruction being decoded
ACC        Accumulator                  Holds intermediate ALU results
MAR        Memory Address Register      Holds ADDRESS of memory to access
MDR        Memory Data Register         Holds DATA read from / to be written to memory
SP         Stack Pointer                Points to TOP of the stack in memory
PSW/FLAGS  Program Status Word          Holds status flags (zero, carry, overflow)

KEY PYQ TRAP: PC holds address of NEXT instruction (NOT current)
KEY PYQ TRAP: IR holds the CURRENT instruction being decoded
```

### Register Quick Comparison:
```
REGISTER     STORES
PC           Address of NEXT instruction to fetch
IR           The instruction currently being decoded / executed
MAR          Memory ADDRESS (where to read / write)
MDR          Memory DATA (what to read / write)
ACC          ALU result / intermediate computation value
SP           Top of stack address
```

---

## 🔷 TOPIC 5: Cache Memory — L1, L2, L3

### What is Cache?
```
Cache = High-speed memory between CPU and RAM

PURPOSE: Bridge the SPEED GAP between fast CPU and slow RAM
         CPU can access cache much faster than RAM

LEVELS:
  L1 Cache → INSIDE CPU chip; smallest (32–64 KB);   FASTEST
  L2 Cache → near CPU; medium size (256 KB – 1 MB);  fast
  L3 Cache → shared among cores; larger (4–32 MB);   slowest of cache

Speed:   L1 > L2 > L3 > RAM > Secondary Storage

PRINCIPLE: Locality of Reference
  Temporal  → recently used data will likely be used again soon
  Spatial   → data near recently used data will likely be needed soon
```

### Cache Key Facts for PYQ:
```
Cache is FASTER than RAM               ← always true
Cache is INSIDE or very near the CPU   ← L1 is inside the chip
Cache REDUCES average memory access time
Cache hit  = data found in cache     (fast!)
Cache miss = data NOT in cache       → must fetch from RAM (slow)
Cache is VOLATILE (loses data when power off) ← just like RAM
```

---

## 🔷 TOPIC 6: Memory Hierarchy — Master Chart

### The Complete Memory Hierarchy:
```
MEMORY HIERARCHY  (Fastest → Slowest | Smallest → Largest | Costliest → Cheapest)

                    ┌──────────────┐
                    │  REGISTERS   │  ← Fastest | Costliest | Smallest
                    │ (CPU inside) │    access: ~1 CPU cycle
                    └──────┬───────┘
                           │
                    ┌──────▼───────┐
                    │  L1 CACHE    │  ← Inside CPU chip
                    │  (32–64 KB)  │    access: ~4 cycles
                    └──────┬───────┘
                           │
                    ┌──────▼───────┐
                    │  L2 CACHE    │  ← Near CPU
                    │ (256KB–1MB)  │    access: ~10 cycles
                    └──────┬───────┘
                           │
                    ┌──────▼───────┐
                    │  L3 CACHE    │  ← Shared among cores
                    │  (4–32 MB)   │    access: ~40 cycles
                    └──────┬───────┘
                           │
                    ┌──────▼───────┐
                    │     RAM      │  ← Main Memory (VOLATILE)
                    │  (4–64 GB)   │    access: ~100 cycles
                    └──────┬───────┘
                           │
                    ┌──────▼───────┐
                    │  SECONDARY   │  ← HDD / SSD (NON-VOLATILE)
                    │  STORAGE     │    access: millions of cycles
                    │ (TB range)   │    (slowest but permanent)
                    └──────────────┘

EXAM SUMMARY ORDER (memorize!):
Registers > L1 Cache > L2 Cache > L3 Cache > RAM > Secondary Storage
```

### Memory Hierarchy PYQ Traps:
```
TRAP 1: "Registers are the fastest memory"     → TRUE  ✅
TRAP 2: "Cache is faster than RAM"             → TRUE  ✅
TRAP 3: "Secondary memory is volatile"         → FALSE ❌ (it is NON-VOLATILE)
TRAP 4: "RAM is non-volatile"                  → FALSE ❌ (RAM IS VOLATILE)
TRAP 5: Which is fastest?                      → REGISTERS (not cache, not RAM)
TRAP 6: RAM vs Cache                           → Cache is FASTER; RAM is LARGER
```

---

## 🔷 TOPIC 7: ASCII — Keystroke to Bits

### What is ASCII?
```
ASCII = American Standard Code for Information Interchange

PURPOSE: Converts KEYSTROKES (characters) into corresponding BITS
         (digital representation of text characters)

Key facts:
  ASCII is a 7-BIT code → can represent 2⁷ = 128 characters
  Extended ASCII = 8-bit → 256 characters
  ASCII covers: A–Z, a–z, 0–9, punctuation, control characters
```

### ASCII Key Values — PYQ Level:
```
CHARACTER    DECIMAL    BINARY
──────────────────────────────────
'A'          65         100 0001
'B'          66         100 0010
'Z'          90         101 1010
'a'          97         110 0001
'z'          122        111 1010
'0'          48         011 0000
'9'          57         011 1001
SPACE        32         010 0000
NULL         0          000 0000

KEY GAP: 'A'=65, 'a'=97 → difference = 32 (always!)
         Uppercase + 32 = Lowercase
         'A'(65) + 32 = 'a'(97) ← PYQ TRAP!
```

### ASCII PYQ Facts:
```
ASCII = 7-bit code (NOT 8-bit, NOT 6-bit)        ← #1 trap
ASCII converts KEYSTROKE into BITS               ← exact exam language
Extended ASCII = 8-bit
EBCDIC = 8-bit (IBM mainframe standard, different from ASCII)
ANSI = standards body (NOT a character encoding itself)
Unicode = variable-width (UTF-8, UTF-16) — supports all world languages
ASCII is a SUBSET of Unicode
```

---

## 🔷 TOPIC 8: Flynn's Taxonomy — Computer Classification

### Flynn's Taxonomy:
```
TAXONOMY   FULL FORM                             EXAMPLE
────────────────────────────────────────────────────────────────
SISD       Single Instruction Single Data        Traditional single-core CPU
SIMD       Single Instruction Multiple Data      GPU, Vector processors
MISD       Multiple Instruction Single Data      Fault-tolerant systems (rare)
MIMD       Multiple Instruction Multiple Data    Multi-core / multiprocessors

KEY PYQ: Traditional computer     = SISD
         Multiprocessor system    = MIMD
         GPU / vector processor   = SIMD
```

---

## 📊 CS MASTER COMPARISON TABLE

```
COMPONENT         KEY FUNCTION                          COMMON TRAP
──────────────────────────────────────────────────────────────────────
ALU               Arithmetic + Logical operations       NOT only arithmetic!
Control Unit      Generates CONTROL SIGNALS             NOT arithmetic, NOT storage
Registers         Fastest memory, inside CPU            Fastest = Registers (not cache)
PC (Program Ctr)  Address of NEXT instruction           NEXT not current
IR (Instr. Reg.)  CURRENT instruction being decoded     current not next
Cache (L1/L2/L3)  Faster than RAM, near CPU             Volatile (like RAM)
RAM               Main memory, volatile                 Volatile! (loses on power-off)
Secondary Memory  Permanent storage, non-volatile       NON-volatile
ASCII             7-bit, keystroke → bits               7-bit NOT 8-bit
EBCDIC            IBM 8-bit encoding                    Different from ASCII
Cache hit         Data found in cache (fast)            Miss = go to RAM
Flynn SISD        Traditional single CPU                Multiprocessor = MIMD
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## 🔢 Maths Shortcuts — Complete Revision

---

## 🔷 MASTER FORMULA SHEET

### Percentage:
```
FORMULA                              EXAMPLE
──────────────────────────────────────────────────────────
x% of y = (x × y) / 100             15% of 200 = 30
% increase = [(New−Old)/Old] × 100   Old=80, New=100 → 25% increase
% decrease = [(Old−New)/Old] × 100   Old=100, New=80 → 20% decrease

FRACTION ↔ PERCENTAGE CHEAT SHEET (memorize all!):
1/2  = 50%      1/3  = 33.33%   1/4  = 25%
1/5  = 20%      1/6  = 16.67%   1/7  = 14.28%
1/8  = 12.5%    1/9  = 11.11%   1/10 = 10%
1/11 = 9.09%    1/12 = 8.33%    2/3  = 66.67%
3/4  = 75%      3/5  = 60%      2/5  = 40%

SUCCESSIVE % CHANGE SHORTCUT:
  Two successive changes of a% and b%:
  Net change = a + b + (a × b)/100
  Example: +20% then −20% = 20 + (−20) + (20×−20)/100 = −4% (net LOSS!)
```

### Profit & Loss:
```
FORMULA                                       MEMORY AID
────────────────────────────────────────────────────────────────
SP = CP × (100 + Profit%) / 100               SP > CP = Profit
SP = CP × (100 − Loss%)   / 100               SP < CP = Loss
Profit% = [(SP−CP)/CP] × 100
Loss%   = [(CP−SP)/CP] × 100

DISHONEST TRADER SHORTCUT:
  If trader uses FALSE weight of (W−d) instead of W:
  Profit% = [d / (W−d)] × 100
  Example: weighs 900g instead of 1000g:
  Profit% = [100 / 900] × 100 = 11.11%

TWO ITEMS AT SAME SP, ONE PROFIT x%, ONE LOSS x%:
  ALWAYS results in LOSS = x²/100 %
  Example: 2 items each at SP=100, one +10%, one −10%
  Net loss = 10²/100 = 1%   ← BIG TRAP in exams!

MARK-UP & DISCOUNT:
  SP = CP × (1 + Markup/100) × (1 − Discount/100)
  Example: Markup 40%, Discount 25%
  SP = CP × 1.4 × 0.75 = 1.05 × CP → 5% Profit
```

### Simple Interest & Compound Interest:
```
SI = (P × R × T) / 100
CI = P × [(1 + R/100)^T − 1]

CI − SI for 2 years = P × (R/100)²
  Example: P=10000, R=10%: CI−SI = 10000 × 0.01 = ₹100

CI for 2 years = SI + (first year SI × R/100)
```

### Averages:
```
Average = Sum of all values / Number of values

IMPORTANT SHORTCUTS:
  Average of 1 to n natural numbers   = (n+1)/2
  Average of 1 to n even numbers      = n+1
  Average of 1 to n odd numbers       = n
  Average of consecutive numbers      = (First + Last)/2

WEIGHTED AVERAGE:
  = (n1×a1 + n2×a2) / (n1+n2)
  Example: 20 students avg 30 marks + 30 students avg 40 marks
  = (20×30 + 30×40) / 50 = (600+1200)/50 = 36
```

### Ratio & Proportion:
```
PROPORTION: a:b = c:d → a×d = b×c (cross multiply)

MIXTURE RULE (Alligation):
  Two items at prices A and B, mixed to get mean price M:
  Ratio of mixing = (B−M) : (M−A)

  Example: Milk at ₹30/L and ₹20/L mixed to get ₹24/L
  Ratio = (30−24) : (24−20) = 6 : 4 = 3 : 2

COMPOUND RATIO:
  A:B = 2:3 and B:C = 4:5 → A:B:C = 8:12:15 → A:C = 8:15
```

### Time, Speed & Distance:
```
Distance = Speed × Time

Unit conversion:
  km/hr → m/s : multiply by 5/18
  m/s → km/hr : multiply by 18/5

RELATIVE SPEED:
  Same direction       = |S1 − S2|
  Opposite direction   = S1 + S2

TRAIN PROBLEMS:
  Train crosses a POLE / PERSON  = covers its own LENGTH only
  Train crosses a PLATFORM       = covers (Train length + Platform length)

AVERAGE SPEED (equal distances):
  = 2ab / (a+b)   where a, b are speeds for each half
  NOTE: NOT (a+b)/2  ← BIG TRAP!
  Example: 60 km/hr going, 40 km/hr returning
  Avg speed = 2×60×40 / (60+40) = 4800/100 = 48 km/hr
```

### HCF & LCM:
```
HCF × LCM = Product of the two numbers  (ONLY FOR TWO NUMBERS!)

HCF of fractions = HCF of numerators   / LCM of denominators
LCM of fractions = LCM of numerators   / HCF of denominators

IMPORTANT PATTERNS:
  Numbers that leave same remainder r when divided by a, b, c:
  → Answer = LCM(a, b, c) + r

  Numbers that leave remainders each = (divisor − k):
  → Answer = LCM(a, b, c) − k
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 75 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** What is the PRIMARY function of the Control Unit (CU) in a CPU?
(A) Perform arithmetic and logical operations
(B) Store frequently accessed data for faster retrieval
(C) Generate control signals to coordinate other units
(D) More than one of the above
(E) None of the above

---

**Q2.** Which component of the CPU performs BOTH arithmetic AND logical operations?
(A) Control Unit
(B) Program Counter
(C) ALU (Arithmetic Logic Unit)
(D) More than one of the above
(E) None of the above

---

**Q3.** In the memory hierarchy, which is the FASTEST memory?
(A) L1 Cache
(B) RAM
(C) Registers
(D) More than one of the above
(E) None of the above

---

**Q4.** ASCII is a ____-bit character encoding standard.
(A) 8
(B) 6
(C) 7
(D) More than one of the above
(E) None of the above

---

**Q5.** The Program Counter (PC) register holds:
(A) The current instruction being decoded
(B) The address of the NEXT instruction to be fetched
(C) The result of the last ALU operation
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following correctly describes the memory hierarchy from FASTEST to SLOWEST?
(A) RAM → Cache → Registers → Secondary
(B) Registers → Cache → RAM → Secondary
(C) Cache → Registers → RAM → Secondary
(D) More than one of the above
(E) None of the above

---

**Q7.** ASCII converts:
(A) Binary to decimal numbers
(B) Keystrokes into corresponding bits
(C) Images into text
(D) More than one of the above
(E) None of the above

---

**Q8.** Which register holds the CURRENT instruction being decoded by the CPU?
(A) Program Counter (PC)
(B) Memory Address Register (MAR)
(C) Instruction Register (IR)
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following statements about Cache memory is TRUE?
(A) Cache is slower than RAM but faster than secondary storage
(B) Cache is faster than RAM and is non-volatile
(C) Cache is faster than RAM but is volatile
(D) More than one of the above
(E) None of the above

---

**Q10.** The decimal ASCII value of character 'A' is:
(A) 97
(B) 48
(C) 65
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following is FALSE about the ALU?
(A) ALU performs arithmetic operations such as addition and subtraction
(B) ALU generates control signals for other units
(C) ALU performs logical operations such as AND, OR, NOT
(D) More than one of the above
(E) None of the above

---

**Q12.** L1, L2, and L3 refer to:
(A) Levels of RAM
(B) Levels of Cache memory
(C) Levels of secondary storage
(D) More than one of the above
(E) None of the above

---

**Q13.** The MAR (Memory Address Register) stores:
(A) The data read from or to be written to memory
(B) The ADDRESS of the memory location being accessed
(C) The address of the next instruction
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following correctly describes EBCDIC?
(A) A 7-bit standard encoding used in modern PCs
(B) An 8-bit IBM character encoding standard
(C) Another name for Extended ASCII
(D) More than one of the above
(E) None of the above

---

**Q15.** In Flynn's Taxonomy, a traditional single-core CPU is classified as:
(A) MIMD
(B) SIMD
(C) SISD
(D) More than one of the above
(E) None of the above

---

**Q16.** The difference between ASCII values of 'a' and 'A' is:
(A) 16
(B) 32
(C) 64
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following is TRUE about Registers?
(A) Registers are located outside the CPU
(B) Registers are the fastest and smallest memory in the hierarchy
(C) Registers are non-volatile and retain data after power-off
(D) More than one of the above
(E) None of the above

---

**Q18.** The MDR (Memory Data Register) stores:
(A) The address of memory to be accessed
(B) The data that is to be written to or read from memory
(C) The address of the next instruction
(D) More than one of the above
(E) None of the above

---

**Q19.** A GPU (Graphics Processing Unit) is an example of which Flynn's Taxonomy class?
(A) SISD
(B) MISD
(C) SIMD
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following is TRUE about RAM?
(A) RAM is non-volatile — it retains data after power-off
(B) RAM is volatile — it loses data when power is off
(C) RAM is faster than L1 cache
(D) More than one of the above
(E) None of the above

---

**Q21.** The principle that recently used data is likely to be used again is called:
(A) Spatial locality
(B) Sequential locality
(C) Temporal locality
(D) More than one of the above
(E) None of the above

---

**Q22.** MIPS stands for:
(A) Memory Integrated Processing System
(B) Millions of Instructions Per Second
(C) Multiple Instruction Parallel System
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly describes the Stack Pointer (SP) register?
(A) It holds the address of the NEXT instruction to be fetched
(B) It points to the TOP of the stack in memory
(C) It stores the result of the last ALU operation
(D) More than one of the above
(E) None of the above

---

**Q24.** Which cache level is located INSIDE the CPU chip and is the FASTEST cache?
(A) L3 Cache
(B) L2 Cache
(C) L1 Cache
(D) More than one of the above
(E) None of the above

---

**Q25.** In Flynn's Taxonomy, a multiprocessor system is classified as:
(A) SISD
(B) MISD
(C) MIMD
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Maths Shortcuts Revision

---

**Q26.** What is 15% of 480?
(A) 60
(B) 72
(C) 75
(D) More than one of the above
(E) None of the above

---

**Q27.** A shopkeeper buys an item for ₹800 and sells it for ₹1000. What is the profit percentage?
(A) 20%
(B) 25%
(C) 15%
(D) More than one of the above
(E) None of the above

---

**Q28.** Two items are sold at the same selling price of ₹500 each. One at 10% profit, the other at 10% loss. What is the net result on the whole transaction?
(A) No profit, no loss
(B) Net profit of 1%
(C) Net loss of 1%
(D) More than one of the above
(E) None of the above

---

**Q29.** The average of five consecutive odd numbers starting from 11 is:
(A) 13
(B) 15
(C) 17
(D) More than one of the above
(E) None of the above

---

**Q30.** Simple Interest on ₹5000 at 8% per annum for 3 years is:
(A) ₹1000
(B) ₹1200
(C) ₹1500
(D) More than one of the above
(E) None of the above

---

**Q31.** A train 200m long crosses a platform 300m long at 50 km/hr. How long does it take?
(A) 30 seconds
(B) 36 seconds
(C) 40 seconds
(D) More than one of the above
(E) None of the above

---

**Q32.** HCF of 36 and 48 is:
(A) 6
(B) 12
(C) 18
(D) More than one of the above
(E) None of the above

---

**Q33.** LCM of 12 and 18 is:
(A) 216
(B) 36
(C) 72
(D) More than one of the above
(E) None of the above

---

**Q34.** If a price is increased by 20% and then decreased by 20%, the net change is:
(A) No change (0%)
(B) 4% decrease
(C) 4% increase
(D) More than one of the above
(E) None of the above

---

**Q35.** A vessel contains milk and water in ratio 3:1. What percentage is milk?
(A) 25%
(B) 60%
(C) 75%
(D) More than one of the above
(E) None of the above

---

**Q36.** Average speed formula when equal distances are covered at speeds a and b is:
(A) (a + b) / 2
(B) 2ab / (a + b)
(C) ab / (a + b)
(D) More than one of the above
(E) None of the above

---

**Q37.** The average of first 10 natural numbers (1 to 10) is:
(A) 5
(B) 5.5
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q38.** A trader uses 900g weight instead of 1kg (1000g). His profit percentage is approximately:
(A) 10%
(B) 11.11%
(C) 9.09%
(D) More than one of the above
(E) None of the above

---

**Q39.** The product of HCF and LCM of two numbers equals:
(A) Sum of the two numbers
(B) Product of the two numbers
(C) Difference of the two numbers
(D) More than one of the above
(E) None of the above

---

**Q40.** A car travels 120 km at 60 km/hr and returns at 40 km/hr. Average speed for the whole journey is:
(A) 50 km/hr
(B) 48 km/hr
(C) 52 km/hr
(D) More than one of the above
(E) None of the above

---

**Q41.** 1/8 expressed as a percentage is:
(A) 10%
(B) 12%
(C) 12.5%
(D) More than one of the above
(E) None of the above

---

**Q42.** A sum becomes ₹6050 in 2 years at 10% per annum compound interest. What is the principal?
(A) ₹4500
(B) ₹5000
(C) ₹5500
(D) More than one of the above
(E) None of the above

---

**Q43.** Two numbers are in ratio 4:5. Their HCF is 6. What is their LCM?
(A) 100
(B) 120
(C) 180
(D) More than one of the above
(E) None of the above

---

**Q44.** What is the smallest number divisible by 4, 6, and 9?
(A) 36
(B) 72
(C) 108
(D) More than one of the above
(E) None of the above

---

**Q45.** Milk at ₹30/L is mixed with milk at ₹20/L to get a mixture priced at ₹24/L. The ratio of mixing (₹30 : ₹20) is:
(A) 2:3
(B) 3:2
(C) 2:1
(D) More than one of the above
(E) None of the above

---

**Q46.** 30 students have average marks of 40. 20 new students join with average marks of 35. New average of all 50 students is:
(A) 37
(B) 38
(C) 39
(D) More than one of the above
(E) None of the above

---

**Q47.** If A:B = 2:3 and B:C = 4:5, then A:C equals:
(A) 8:15
(B) 2:5
(C) 6:10
(D) More than one of the above
(E) None of the above

---

**Q48.** A shopkeeper marks up price by 40% and gives 25% discount. Profit percentage is:
(A) 10%
(B) 5%
(C) 15%
(D) More than one of the above
(E) None of the above

---

**Q49.** The difference between CI and SI on ₹10000 at 10% for 2 years is:
(A) ₹50
(B) ₹100
(C) ₹200
(D) More than one of the above
(E) None of the above

---

**Q50.** A number when divided by 6, 8, and 12 leaves remainder 5 each time. The smallest such number is:
(A) 24
(B) 29
(C) 48
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                  |
|----|--------|--------------------------------------------------------------------|
| 1  | (C)    | Control Unit's primary job = generate control signals              |
| 2  | (C)    | ALU = Arithmetic Logic Unit — performs BOTH arithmetic + logical   |
| 3  | (C)    | Registers are fastest in memory hierarchy (inside CPU)             |
| 4  | (C)    | ASCII = 7-bit (NOT 8-bit — that is Extended ASCII)                 |
| 5  | (B)    | PC = address of NEXT instruction (not current)                     |
| 6  | (B)    | Registers > Cache > RAM > Secondary = correct hierarchy order      |
| 7  | (B)    | ASCII converts keystrokes into corresponding bits                  |
| 8  | (C)    | IR = Instruction Register = holds current instruction being decoded|
| 9  | (C)    | Cache is faster than RAM AND volatile (loses data at power-off)    |
| 10 | (C)    | 'A' = decimal 65 in ASCII ('a'=97, '0'=48)                         |
| 11 | (B)    | FALSE: ALU does NOT generate control signals (CU does that)        |
| 12 | (B)    | L1, L2, L3 are levels of Cache memory                              |
| 13 | (B)    | MAR = Memory ADDRESS Register = stores the memory address          |
| 14 | (B)    | EBCDIC = IBM 8-bit encoding (different from ASCII)                 |
| 15 | (C)    | Traditional single-core CPU = SISD in Flynn's taxonomy             |
| 16 | (B)    | 'a'=97, 'A'=65, difference = 32 (always!)                          |
| 17 | (B)    | Registers = fastest + smallest; located inside CPU                 |
| 18 | (B)    | MDR = Memory DATA Register = stores data read / written            |
| 19 | (C)    | GPU = vector/parallel processing = SIMD                            |
| 20 | (B)    | RAM is volatile — loses all data when power is switched off        |
| 21 | (C)    | Recently used data likely reused = Temporal locality               |
| 22 | (B)    | MIPS = Millions of Instructions Per Second                         |
| 23 | (B)    | SP = Stack Pointer = points to TOP of the stack in memory          |
| 24 | (C)    | L1 Cache is inside the CPU chip and is the fastest cache level     |
| 25 | (C)    | Multiprocessor = Multiple Instruction Multiple Data = MIMD         |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                       |
|----|--------|-------------------------------------------------------------------------|
| 26 | (B)    | 15% of 480 = (15×480)/100 = 7200/100 = 72                              |
| 27 | (B)    | Profit% = [(1000−800)/800]×100 = 200/800×100 = 25%                     |
| 28 | (C)    | Same SP, same % — one profit one loss → always net loss = x²/100 = 1%  |
| 29 | (B)    | 11,13,15,17,19 → average = (First+Last)/2 = (11+19)/2 = 15             |
| 30 | (B)    | SI = (5000×8×3)/100 = 120000/100 = ₹1200                               |
| 31 | (B)    | Distance=500m; 50km/hr=125/9 m/s; T=500÷(125/9)=500×9/125=36 sec      |
| 32 | (B)    | HCF(36,48): factors of 36=1,2,3,4,6,9,12,36; of 48=...,12,...→ HCF=12 |
| 33 | (B)    | LCM(12,18): 12=2²×3; 18=2×3²; LCM=2²×3²=36                           |
| 34 | (B)    | Successive +20% and −20%: net = 20+(−20)+(20×−20)/100 = −4% (loss)    |
| 35 | (C)    | Milk = 3/(3+1) = 3/4 = 75%                                             |
| 36 | (B)    | Average speed (equal distance) = 2ab/(a+b) NOT (a+b)/2                 |
| 37 | (B)    | Average of 1 to n = (n+1)/2 = (10+1)/2 = 5.5                          |
| 38 | (B)    | Profit% = [100/(1000−100)]×100 = 100/900×100 = 11.11%                  |
| 39 | (B)    | HCF × LCM = Product of the TWO numbers (only for 2 numbers)            |
| 40 | (B)    | Avg speed = 2×60×40/(60+40) = 4800/100 = 48 km/hr                      |
| 41 | (C)    | 1/8 = 0.125 = 12.5%                                                    |
| 42 | (B)    | 6050 = P×(1.1)² = P×1.21 → P = 6050/1.21 = ₹5000                      |
| 43 | (B)    | Numbers = 4×6=24 and 5×6=30; LCM(24,30)=120                            |
| 44 | (A)    | LCM(4,6,9): LCM = 36                                                   |
| 45 | (A)    | Alligation: (30−24):(24−20) = 6:4 = 3:2 → ₹30:₹20 = 2:3               |
| 46 | (B)    | (30×40 + 20×35)/50 = (1200+700)/50 = 1900/50 = 38                      |
| 47 | (A)    | A:B=2:3, B:C=4:5 → A:B:C=8:12:15 → A:C=8:15                           |
| 48 | (B)    | SP = 100×1.4×0.75 = 105 on CP=100 → Profit = 5%                        |
| 49 | (B)    | CI−SI for 2 years = P×(R/100)² = 10000×(0.1)² = ₹100                  |
| 50 | (B)    | LCM(6,8,12)=24; leaves remainder 5 → 24+5 = 29                         |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (CPU Architecture)

```
CPU OVERVIEW:
1.  CPU = "Brain" of computer — Fetch → Decode → Execute → Store
2.  CPU has 3 main parts: ALU, Control Unit, Registers
3.  Cache is also part of CPU subsystem (L1 inside chip)

ALU:
4.  ALU = performs BOTH arithmetic AND logical operations
5.  "ALU does only arithmetic" → FALSE ← classic trap
6.  ALU result stored in ACCUMULATOR (ACC) register

CONTROL UNIT:
7.  Control Unit = generates CONTROL SIGNALS ← most tested fact
8.  CU does NOT perform arithmetic (ALU does)
9.  CU directs data flow across ALL parts of the computer

REGISTERS:
10. Registers = FASTEST memory in entire hierarchy (inside CPU)
11. PC  = address of NEXT instruction (NOT current!)
12. IR  = CURRENT instruction being decoded
13. MAR = Memory ADDRESS (where to read/write)
14. MDR = Memory DATA (what to read/write)
15. ACC = holds ALU result
16. SP  = points to TOP of stack in memory

MEMORY HIERARCHY:
17. Order: Registers > L1 > L2 > L3 > RAM > Secondary Storage
18. RAM = VOLATILE (loses data at power-off)
19. Secondary memory = NON-VOLATILE (permanent)
20. Cache = VOLATILE (like RAM — common trap!)
21. L1 Cache = inside CPU chip = fastest cache = smallest capacity

ASCII:
22. ASCII = 7-bit code (NOT 8-bit!)
23. ASCII converts KEYSTROKE into corresponding BITS
24. 'A'=65, 'a'=97, '0'=48, SPACE=32, NULL=0
25. 'a' − 'A' = 32 (lowercase = uppercase ASCII + 32)
26. EBCDIC = IBM 8-bit encoding (completely different from ASCII)
27. Unicode = superset of ASCII; supports all world languages

CACHE:
28. Cache hit  = data found in cache    → fast
    Cache miss = data NOT in cache      → fetch from RAM (slow)
29. Temporal locality = recently used data used again soon
30. Spatial locality  = nearby data also likely needed

FLYNN'S TAXONOMY:
31. SISD = traditional single CPU   |  MIMD = multiprocessor
    SIMD = GPU / vector processor   |  MISD = rare fault-tolerant
```

---

### ⚡ GS — 30 MUST-KNOW MATHS SHORTCUTS

```
PERCENTAGE:
1.  1/8=12.5%  1/4=25%  1/3=33.33%  3/4=75%  2/3=66.67%
2.  Successive +a% then −a% → net LOSS = a²/100%
    (+20%, −20% = −4% net; NOT zero!)
3.  % increase = [(New−Old)/Old] × 100
4.  % decrease = [(Old−New)/Old] × 100

PROFIT & LOSS:
5.  Profit% = [(SP−CP)/CP] × 100
6.  Loss%   = [(CP−SP)/CP] × 100
7.  Same SP, same % — one profit one loss → net LOSS = x²/100%
8.  Dishonest trader (weighs W−d instead of W):
    Profit% = d/(W−d) × 100
9.  Markup M%, Discount D%: SP = CP × (1+M/100) × (1−D/100)

AVERAGES:
10. Average of 1 to n = (n+1)/2
11. Average of consecutive = (First + Last)/2
12. Weighted avg = (n1×a1 + n2×a2) / (n1+n2)

SI & CI:
13. SI = PRT/100
14. CI−SI for 2 years = P × (R/100)²
    P=10000, R=10% → CI−SI = ₹100
15. CI: A = P × (1 + R/100)^T

HCF & LCM:
16. HCF × LCM = product of TWO numbers (only for 2 numbers!)
17. Leaves same remainder r: answer = LCM + r
18. HCF of fractions = HCF(num)/LCM(den)
    LCM of fractions = LCM(num)/HCF(den)

RATIO & ALLIGATION:
19. Alligation ratio = (Higher−Mean) : (Mean−Lower)
20. A:B=2:3 and B:C=4:5 → A:B:C=8:12:15 → A:C=8:15

TIME, SPEED & DISTANCE:
21. km/hr → m/s: × 5/18  |  m/s → km/hr: × 18/5
22. Avg speed (equal distance) = 2ab/(a+b) — NOT (a+b)/2 ← TRAP!
23. Train × pole = own length only
    Train × platform = own length + platform length
24. Opposite direction relative speed = S1+S2
    Same direction relative speed     = |S1−S2|

MATHS TRAPS (most commonly wrong in BPSC):
25. TRAP 1: Avg speed = (a+b)/2 → WRONG; correct = 2ab/(a+b)
26. TRAP 2: Profit+Loss same rate → "no change" → WRONG; always LOSS
27. TRAP 3: HCF×LCM = product → only for EXACTLY 2 numbers
28. TRAP 4: +20% then −20% = no change → WRONG; = −4%
29. TRAP 5: 1/3 = 33% → WRONG; 1/3 = 33.33% (recurring)
30. TRAP 6: CI−SI = 0 → WRONG; CI always > SI; diff = P(R/100)²
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
COMPONENT      FUNCTION                        COMMON WRONG ANSWER
────────────────────────────────────────────────────────────────────
ALU            Arithmetic + Logical            "Only arithmetic"
Control Unit   Generate control signals        "Perform arithmetic"
Registers      Fastest memory inside CPU       "Cache is fastest"
PC             Address of NEXT instruction     "Current instruction"
IR             CURRENT instruction             "Next instruction"
RAM            Volatile main memory            "Non-volatile"
Secondary      Non-volatile storage            "Volatile"
L1 Cache       Inside CPU, fastest cache       "L3 is fastest"
ASCII          7-bit, keystroke → bits         "8-bit encoding"
EBCDIC         IBM 8-bit encoding              "Same as ASCII"
────────────────────────────────────────────────────────────────────

MATHS FORMULA     CORRECT                     TRAP / WRONG
────────────────────────────────────────────────────────────────────
Avg speed         2ab/(a+b)                   NOT (a+b)/2
+a% then −a%      Net = −a²/100% (LOSS)       NOT "no change"
HCF × LCM         Product of 2 numbers        Only for 2 numbers!
CI − SI (2yr)     P × (R/100)²                Don't compute manually
1/8               12.5%                       NOT 10% or 12%
Same SP ±x%       Net LOSS = x²/100           NOT "no profit no loss"
────────────────────────────────────────────────────────────────────
```

---

## 🎯 DAY 75 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   CPU Architecture — ALU, Control Unit, Registers (PC, IR, MAR, MDR, ACC, SP),
      Cache (L1/L2/L3), Memory Hierarchy, ASCII (7-bit), EBCDIC, Flynn's Taxonomy,
      Temporal/Spatial Locality, MIPS

GS:   Maths Shortcuts — Percentage, Profit/Loss (markup/discount, dishonest trader),
      Averages, Simple Interest, Compound Interest (CI−SI formula),
      HCF/LCM, Ratio/Alligation, Time-Speed-Distance

NEXT: Day 76 — Addressing Modes (Immediate, Direct/Absolute, Indirect, Register,
      Register Indirect) + IA-32 Flags (TF, IF, IOPL)
      GS: History — Freedom Fighters of Bihar
```

---

*Day 75 of 170 | Phase 2: Depth | Week 12: Computer Architecture + Software Engineering*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
