# 📅 BPSC TRE 4.0 — DAY 76: ADDRESSING MODES + BIHAR FREEDOM FIGHTERS
### Week 12 — Computer Architecture + Software Engineering
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — Addressing Modes + IA-32 Flags
> - Afternoon (1 hr): GS — Freedom Fighters of Bihar (High BPSC Probability)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 Addressing Modes + IA-32 Flags — All Concepts, One Place

---

## 🔷 TOPIC 1: What is an Addressing Mode?

### Definition:
```
Addressing Mode = The METHOD used by the CPU to find/access
                  the OPERAND (data) needed for an instruction.

Every CPU instruction has TWO parts:
  ┌──────────────────────────────────────────────┐
  │  INSTRUCTION = OPCODE  +  OPERAND(S)         │
  │               (what    )  (data or           │
  │                to do   )   address of data)  │
  └──────────────────────────────────────────────┘

Addressing Mode answers: WHERE IS the operand?
  → In the instruction itself?   → IMMEDIATE
  → At a direct memory address?  → DIRECT / ABSOLUTE
  → Address of an address?       → INDIRECT
  → In a register?               → REGISTER
  → Register holds the address?  → REGISTER INDIRECT
```

---

## 🔷 TOPIC 2: All Addressing Modes — Complete Reference

### MODE 1 — Immediate Addressing:
```
IMMEDIATE ADDRESSING
─────────────────────────────────────────────────────────
Definition: The OPERAND is present DIRECTLY in the
            instruction itself (not in memory or register)

Syntax:     MOV R1, #5     ← operand IS the number 5
            ADD R1, #100   ← add 100 directly

How it works:
  Instruction: [ OPCODE | OPERAND VALUE ]
                            ↑
                    data is RIGHT HERE

SPEED:    FASTEST (no extra memory access needed)
FLEXIBLE: Least flexible (operand fixed at compile time)
USE CASE: Loading constants, initializing values

MOST COMMON addressing mode in CPU instruction sets ← PYQ FACT

EXAMPLE:
  MOV AX, 10   → AX = 10 (10 is the immediate operand)
```

### MODE 2 — Direct (Absolute) Addressing:
```
DIRECT / ABSOLUTE ADDRESSING
─────────────────────────────────────────────────────────
Definition: The instruction contains the ACTUAL MEMORY
            ADDRESS of the operand

Syntax:     MOV R1, [2000]   ← go to address 2000, get the data
            ADD X Y          ← X and Y are memory addresses

How it works:
  Instruction: [ OPCODE | ADDRESS (e.g. 2000) ]
                              ↓
                    Go to memory location 2000
                              ↓
                    Fetch operand from there

SPEED:    One memory access required
EXAMPLE:  ADD X Y  ← this format = ABSOLUTE / DIRECT addressing

KEY PYQ FACT:
  "ADD X Y" instruction format = ABSOLUTE (Direct) Addressing ← tested!
```

### MODE 3 — Indirect Addressing:
```
INDIRECT ADDRESSING
─────────────────────────────────────────────────────────
Definition: The instruction contains an address that
            POINTS TO ANOTHER ADDRESS which holds the operand
            (Address of an Address)

How it works:
  Instruction: [ OPCODE | ADDRESS1 ]
                              ↓
              Fetch from ADDRESS1 → get ADDRESS2
                              ↓
              Fetch from ADDRESS2 → get OPERAND

  ANALOGY: "Go to locker 100. Inside locker 100 is a note
            that says 'your item is in locker 250'.
            Go to locker 250 to get your item."

SPEED:    TWO memory accesses required (slowest among basic modes)
USE CASE: Accessing arrays, pointers, data structures
EXAMPLE:  If [1000] = 2000 and [2000] = 75
          Then indirect addressing via 1000 gives operand = 75
```

### MODE 4 — Register Addressing:
```
REGISTER ADDRESSING
─────────────────────────────────────────────────────────
Definition: The operand is stored directly in a REGISTER
            (no memory access at all)

Syntax:     ADD R1, R2      ← both operands are in registers
            MOV AX, BX     ← operand BX is a register

How it works:
  Instruction: [ OPCODE | REGISTER NAME ]
                              ↓
                    Fetch directly from register

SPEED:    Very FAST (registers are inside CPU — fastest memory)
USE CASE: Arithmetic operations on register values
EXAMPLE:  ADD AX, BX → AX = AX + BX (both are registers)
```

### MODE 5 — Register Indirect Addressing:
```
REGISTER INDIRECT ADDRESSING
─────────────────────────────────────────────────────────
Definition: A REGISTER holds the MEMORY ADDRESS of the operand
            (not the operand itself — just its address)

Syntax:     MOV R1, [R2]    ← R2 has the address; go there, get data
            ADD AX, [BX]   ← BX holds address of the operand

How it works:
  Instruction: [ OPCODE | REGISTER (e.g. BX) ]
                              ↓
              BX contains memory address (e.g. 5000)
                              ↓
              Fetch operand from memory address 5000

SPEED:    One memory access (faster than indirect, but one access needed)
USE CASE: Array traversal with pointer arithmetic
EXAMPLE:  If BX = 5000 and [5000] = 99
          Then ADD AX, [BX] adds 99 to AX
```

---

## 🔷 TOPIC 3: Addressing Modes — Master Comparison Table

```
MODE              OPERAND LOCATION            SPEED      KEY EXAMPLE
──────────────────────────────────────────────────────────────────────
Immediate         IN the instruction itself   Fastest    MOV R1, #5
Direct/Absolute   Memory address given        1 access   ADD X Y ← PYQ!
Indirect          Address of address          2 accesses [address → address → data]
Register          In a register               Very fast  ADD R1, R2
Register Indirect Register holds address      1 access   MOV R1, [R2]
──────────────────────────────────────────────────────────────────────

MOST COMMON addressing mode = IMMEDIATE  ← PYQ TRAP
"ADD X Y" format             = ABSOLUTE (Direct) ← PYQ TRAP
Slowest (most accesses)      = INDIRECT
No memory access at all      = REGISTER (fastest after immediate)
```

### Visual Summary Diagram:
```
WHERE IS THE OPERAND?
─────────────────────
IMMEDIATE:
  [OPCODE | 42 ]   ← operand 42 is right here in instruction

DIRECT:
  [OPCODE | 2000] → [Memory 2000: 42]   ← one memory fetch

INDIRECT:
  [OPCODE | 1000] → [Memory 1000: 2000] → [Memory 2000: 42]
                                           ← two memory fetches

REGISTER:
  [OPCODE | R1  ]   ← R1 (inside CPU) already holds 42

REGISTER INDIRECT:
  [OPCODE | R1  ] → R1 = 2000 → [Memory 2000: 42]   ← one fetch
```

---

## 🔷 TOPIC 4: IA-32 Processor Flags

### What Are Flags?
```
FLAGS = Single-bit status indicators in the CPU
        They are set (1) or cleared (0) after operations
        Used for CONDITIONAL branching (if/else, loops)

Stored in: EFLAGS register (in IA-32 / x86 architecture)
```

### Status Flags (Set by ALU after operations):
```
FLAG    NAME            SET WHEN
────────────────────────────────────────────────────────────
CF      Carry Flag      Carry/borrow out of most significant bit
ZF      Zero Flag       Result = 0 after operation ← very common
SF      Sign Flag       Result is NEGATIVE (MSB = 1)
OF      Overflow Flag   Signed arithmetic overflow occurred
PF      Parity Flag     Result has even number of 1 bits

MOST IMPORTANT: ZF (Zero Flag) — used in comparisons and loops
```

### IA-32 Conditional / Control Flags — PYQ TOPIC:
```
These are the FLAGS provided as CONDITIONAL flags in IA-32
(BPSC TRE tested these — memorize the three!)

FLAG    NAME                    PURPOSE
────────────────────────────────────────────────────────────
TF      TRAP FLAG               Single-step execution (debug mode)
                                If TF=1, CPU executes one instruction
                                then generates a debug interrupt

IF      INTERRUPT FLAG          Controls maskable interrupts
                                IF=1 → interrupts are ENABLED
                                IF=0 → interrupts are DISABLED

IOPL    I/O PRIVILEGE LEVEL     Controls I/O access privilege
                                2-bit field (values 0–3)
                                Determines which privilege ring
                                can execute I/O instructions

KEY PYQ FACT:
  IA-32 conditional flags = TF, IF, IOPL  ← memorize exactly these three!
```

### Complete IA-32 EFLAGS Register Overview:
```
BIT POSITION    FLAG    TYPE
─────────────────────────────────────────────
0               CF      Status (Carry)
2               PF      Status (Parity)
4               AF      Status (Auxiliary Carry)
6               ZF      Status (Zero)
7               SF      Status (Sign)
8               TF      Control / Conditional ← PYQ
9               IF      Control / Conditional ← PYQ
10–11           IOPL    Control / Conditional ← PYQ
11              OF      Status (Overflow)
14              NT      System (Nested Task)
─────────────────────────────────────────────
STATUS flags   → set by ALU after arithmetic/logical ops
CONTROL flags  → control CPU behavior (TF, IF, IOPL)
```

---

## 🔷 TOPIC 5: Additional Architecture Facts (PYQ-Tested)

### Instruction Formats:
```
Zero-Address Instruction:
  → Operands on STACK (no address field in instruction)
  → Example: PUSH, POP in stack machines

One-Address Instruction:
  → One operand in instruction; second operand = ACCUMULATOR (ACC)
  → Example: ADD 5000 → ACC = ACC + Memory[5000]

Two-Address Instruction:
  → Two operands; result in one of them
  → Example: ADD R1, R2 → R1 = R1 + R2

Three-Address Instruction:
  → Three operands (source1, source2, destination separate)
  → Example: ADD R1, R2, R3 → R3 = R1 + R2 (RISC-style)
```

### RISC vs CISC:
```
FEATURE        RISC                       CISC
────────────────────────────────────────────────────────────
Full form      Reduced Instruction Set    Complex Instruction Set
               Computer                  Computer
Instructions   Simple, fixed-length       Complex, variable-length
Registers      More registers             Fewer registers
Memory access  Load/Store ONLY            Any instruction can access
Addressing     Fewer modes                Many modes
Clock cycles   1 cycle per instruction    Multiple cycles
Examples       ARM, MIPS, PowerPC         Intel x86, IA-32
Key trait      Simple hardware            Complex hardware, simpler code

PYQ TRAP: RISC = fewer instruction types (NOT more!)
          RISC has MORE registers (NOT fewer!)
```

---

## 📊 CS MASTER COMPARISON TABLE

```
ADDRESSING MODE   OPERAND IS...              PYQ TRIGGER
────────────────────────────────────────────────────────────────
Immediate         In the instruction itself  Most common mode
Direct/Absolute   At the given address       "ADD X Y" format ← PYQ!
Indirect          At address-of-address      Two memory accesses
Register          In a register              No memory access
Register Indirect Register holds the address One memory access
────────────────────────────────────────────────────────────────

IA-32 FLAG  TYPE       FUNCTION
────────────────────────────────────────────────────────────────
TF          Control    Trap/single-step debug
IF          Control    Enable/disable maskable interrupts
IOPL        Control    I/O privilege level (2-bit, 0–3)
ZF          Status     Set when result = 0
CF          Status     Set when carry/borrow occurs
SF          Status     Set when result is negative
OF          Status     Set when signed overflow occurs
────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## 🏛️ Freedom Fighters of Bihar — Complete Coverage

---

## 🔷 MASTER TIMELINE — BIHAR FREEDOM FIGHTERS

```
BIHAR FREEDOM FIGHTERS — CHRONOLOGICAL ORDER
════════════════════════════════════════════════════════════════

1857    KUNWAR SINGH
        → Jagdishpur, BHOJPUR district, Bihar
        → Led 1857 revolt in Bihar at age ~80 (folk hero!)
        → Defeated British forces at Jagdishpur
        → Died April 26, 1858 — battle wound
        → Called "Lion of 1857" / "Veer Kunwar Singh"
        → His brother AMAR SINGH continued the revolt after him

1905    SWADESHI MOVEMENT BEGINS IN BIHAR
        → Partition of Bengal triggered Bihar's involvement

1907    SACHINDRA NATH SANYAL
        → Anushilan Samiti branch in Patna (1913)
        → Revolutionary nationalist

1912    BIHAR PROVINCE created (separated from Bengal)

1915    GANDHI RETURNS TO INDIA
        → Rajendra Prasad meets Gandhi first in Patna

1917    CHAMPARAN SATYAGRAHA ← HIGHEST BPSC PRIORITY
        RAJENDRA PRASAD
        → Born December 3, 1884, ZERADEI, SIWAN, BIHAR
        → Received Gandhi in Patna for Champaran
        → Organized Bihar's participation
        → Later: First President of India

        RAJ KUMAR SHUKLA
        → Indigo farmer from Champaran
        → BROUGHT GANDHI to Champaran (persistent request)
        → Key facilitator — without him, no Champaran Satyagraha

        SHEIKH GULAB
        → Supported Champaran movement

1920    NON-COOPERATION MOVEMENT — BIHAR

1921    RAJENDRA PRASAD founded BIHAR VIDYAPEETH
        → Alternative national university during NCM
        → Patna, Bihar
        → Symbol of educational non-cooperation

        SWAMI VIDYANAND
        → Led Bihar PEASANTS in Non-Cooperation Movement
        → Key NCM leader in Bihar

1921    BIHAR SOCIALIST PARTY
        → Founded by PHULAN PRASAD VARMA + JAYAPRAKASH NARAYAN
        → JP = from Sitabdiara, Saran, Bihar

1930    CIVIL DISOBEDIENCE — BIHAR
        RAJENDRA PRASAD arrested and imprisoned

1931    GAYA SESSION OF INC (1922)
        → Presided by CHITTARANJAN DAS (C.R. Das)

1934    BIHAR EARTHQUAKE + POLITICAL CONTEXT
        → Rajendra Prasad led relief work — cemented Bihar identity

1940    JAYAPRAKASH NARAYAN (JP)
        → From SITABDIARA, SARAN, BIHAR
        → Co-founder Bihar Socialist Party
        → Underground Quit India Movement leader

1942    QUIT INDIA MOVEMENT — BIHAR SPECIAL
        JAYAPRAKASH NARAYAN (JP)
        → Led underground freedom struggle
        → ESCAPED HAZARIBAGH CENTRAL JAIL — November 9, 1942
        → Organized guerrilla resistance across Bihar

        RAJENDRA PRASAD
        → Imprisoned at BANKIPUR JAIL, PATNA
        → Continued resistance

        ARUNA ASAF ALI (born in Kalka, active in Bihar)
        → Hoisted Congress flag at Gowalia Tank, Bombay (Aug 9, 1942)

1946    RAJENDRA PRASAD
        → Elected President of CONSTITUENT ASSEMBLY (December 9, 1946)

1950    RAJENDRA PRASAD
        → Became FIRST PRESIDENT OF INDIA (January 26, 1950)
        → Served 2 terms, 12 years (longest serving)
        → BHARAT RATNA 1962 (while still President!)
        → Died February 28, 1963, SADAQAT ASHRAM, PATNA

════════════════════════════════════════════════════════════════
```

---

## 🔷 TRIBAL & PEASANT REVOLT LEADERS OF BIHAR

```
TRIBAL REVOLTS — BIHAR / JHARKHAND (then undivided Bihar)

BIRSA MUNDA (1875–1900)
→ Ulgulan (Great Tumult) movement — 1899–1900
→ Tribe: MUNDA tribe, Chota Nagpur Plateau (now Jharkhand)
→ Demanded: return of tribal lands; end to exploitation
→ Religious-political movement ("Birsait" religion)
→ Arrested 1900, died in Ranchi jail, June 9, 1900 (age ~25)
→ Commander-in-Chief of his army: GAYA MUNDA
→ Called "Dharti Aaba" (Father of the Earth) by his followers
→ Birthday November 15 = Jharkhand Statehood Day (2000)

SIDHU & KANHU MURMU
→ Led SANTHAL REBELLION — 1855–56
→ FIRST major tribal revolt in undivided Bihar
→ Santhal Pargana region (now Jharkhand)
→ Against British exploitation and moneylenders
→ Both were hanged

TANA BHAGAT MOVEMENT (1914)
→ Leader: JATRA BHAGAT (Oraon tribe, Chota Nagpur)
→ TRIBAL movement (NOT Dalit, NOT peasant — common trap!)
→ Non-violent, spiritual + political resistance
→ Demanded end to exploitation of tribals
→ Became part of Gandhi's NCM later

CHRONOLOGICAL ORDER OF TRIBAL REVOLTS (memorize!):
  Santhal Rebellion (1855–56)
  → Birsa Munda / Ulgulan (1899–1900)
  → Tana Bhagat (1914)
```

---

## 🔷 REVOLUTIONARY NATIONALISTS FROM BIHAR

```
PERSON                KEY FACT
────────────────────────────────────────────────────────────────
Phulan Prasad Varma   Co-founded Bihar Socialist Party with JP (1934)
Sachindra Nath Sanyal Founded Anushilan Samiti Patna branch (1913)
                      Later founded Hindustan Republican Association (HRA)
                      Helped connect Bihar to pan-India revolution network
Gaya Munda            Commander-in-Chief of Birsa Munda's forces
Jatra Bhagat          Leader of Tana Bhagat movement (Oraon tribe, 1914)
Sidhu & Kanhu         Led Santhal Rebellion (1855–56) — FIRST tribal revolt
Veer Kunwar Singh     Led 1857 revolt in Bihar; Jagdishpur, Bhojpur
Amar Singh            Brother of Kunwar Singh; continued revolt after him
────────────────────────────────────────────────────────────────
```

---

## 🔷 BIHAR-SPECIFIC POLITICAL INSTITUTIONS

```
INSTITUTION                 FOUNDER / YEAR         SIGNIFICANCE
────────────────────────────────────────────────────────────────
Bihar Provincial Congress   1908, Patna            First organized Congress in Bihar
Bihar Vidyapeeth            Rajendra Prasad, 1921  Alternative univ. during NCM
Bihar Socialist Party       JP + Phulan Prasad     1934; linked to underground QIM
                            Varma
Anushilan Samiti Patna      Sachindra Nath Sanyal  1913; revolutionary organization
────────────────────────────────────────────────────────────────
```

---

## 🔷 PEOPLE & THEIR #1 EXAM FACT — BIHAR

```
PERSON                 SINGLE MOST IMPORTANT FACT FOR BPSC
─────────────────────────────────────────────────────────────────
Kunwar Singh           Led 1857 revolt in Bihar | Jagdishpur, BHOJPUR
Raj Kumar Shukla       Brought Gandhi to Champaran (indigo farmer)
Rajendra Prasad        Born Zeradei, Siwan | Bihar Vidyapeeth 1921 |
                       First President | 12 years | Bharat Ratna 1962
JP (Jayaprakash)       Born Sitabdiara, SARAN | Hazaribagh jail escape
                       November 9, 1942 | Bihar Socialist Party
Birsa Munda            Ulgulan 1899–1900 | Dharti Aaba | Munda tribe
Sidhu & Kanhu          Santhal Rebellion 1855–56 (FIRST tribal revolt)
Tana Bhagat            TRIBAL movement (Oraon, 1914) — NOT Dalit/peasant
Swami Vidyanand        Led Bihar PEASANTS in NCM
Phulan Prasad Varma    Co-founded Bihar Socialist Party with JP
Sachindra Nath Sanyal  Anushilan Samiti Patna (1913)
Amar Singh             Brother of Kunwar Singh; continued 1857 revolt
─────────────────────────────────────────────────────────────────
```

---

## 🔷 KEY DATES — BIHAR FREEDOM STRUGGLE

```
DATE              EVENT
────────────────────────────────────────────────────────
1855–56           Santhal Rebellion (Sidhu & Kanhu Murmu)
1857              Kunwar Singh leads Bihar revolt (Jagdishpur, Bhojpur)
1858 (Apr 26)     Kunwar Singh dies from battle wounds
1884 (Dec 3)      Rajendra Prasad born at Zeradei, Siwan
1899–1900         Birsa Munda's Ulgulan movement
1900 (Jun 9)      Birsa Munda dies in Ranchi jail
1908              Bihar Provincial Congress formed (Patna)
1912              Bihar Province separated from Bengal
1913              Anushilan Samiti Patna (Sachindra Nath Sanyal)
1914              Tana Bhagat movement begins (Jatra Bhagat)
1917 (Apr 15)     Gandhi arrives Motihari, Champaran
                  Rajendra Prasad received Gandhi in Patna
1921              Bihar Vidyapeeth founded (Rajendra Prasad)
1921              Swami Vidyanand leads Bihar peasants in NCM
1934              Bihar Socialist Party (JP + Phulan Prasad Varma)
1942 (Aug 9)      Rajendra Prasad arrested → Bankipur Jail, Patna
1942 (Nov 9)      JP ESCAPES HAZARIBAGH JAIL ← HIGH PROBABILITY
1946 (Dec 9)      Rajendra Prasad elected CA President
1950 (Jan 26)     Rajendra Prasad = First President of India
1962              Rajendra Prasad — Bharat Ratna (while still President!)
1963 (Feb 28)     Rajendra Prasad dies at Sadaqat Ashram, Patna
────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 76 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** In which addressing mode is the OPERAND present directly inside the instruction itself?
(A) Direct addressing
(B) Register addressing
(C) Immediate addressing
(D) More than one of the above
(E) None of the above

---

**Q2.** The instruction format `ADD X Y` where X and Y are memory locations corresponds to which addressing mode?
(A) Immediate addressing
(B) Indirect addressing
(C) Absolute (Direct) addressing
(D) More than one of the above
(E) None of the above

---

**Q3.** Which addressing mode requires TWO memory accesses to fetch the operand?
(A) Direct addressing
(B) Indirect addressing
(C) Register indirect addressing
(D) More than one of the above
(E) None of the above

---

**Q4.** In register indirect addressing, the register contains:
(A) The operand value directly
(B) The memory ADDRESS of the operand
(C) The instruction opcode
(D) More than one of the above
(E) None of the above

---

**Q5.** Which is the MOST COMMON addressing mode used in CPU instruction sets?
(A) Direct addressing
(B) Indirect addressing
(C) Immediate addressing
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following IA-32 flags is used for single-step (debug) execution?
(A) IF (Interrupt Flag)
(B) CF (Carry Flag)
(C) TF (Trap Flag)
(D) More than one of the above
(E) None of the above

---

**Q7.** The IA-32 IOPL flag is:
(A) A 1-bit flag that enables/disables interrupts
(B) A 2-bit field that controls I/O privilege level
(C) A flag set when the result of an operation is zero
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following are the IA-32 conditional/control flags? (Select all that apply)
(A) TF, IF, IOPL
(B) CF, ZF, SF
(C) OF, PF, AF
(D) More than one of the above
(E) None of the above

---

**Q9.** The Zero Flag (ZF) in IA-32 is set when:
(A) The result of an operation has a carry
(B) The result of an operation is zero
(C) Signed arithmetic overflow occurs
(D) More than one of the above
(E) None of the above

---

**Q10.** Which addressing mode has NO memory access at all?
(A) Immediate addressing
(B) Direct addressing
(C) Register addressing
(D) More than one of the above
(E) None of the above

---

**Q11.** In RISC architecture compared to CISC:
(A) RISC has more complex instructions and fewer registers
(B) RISC has simpler, fixed-length instructions and more registers
(C) RISC allows any instruction to access memory
(D) More than one of the above
(E) None of the above

---

**Q12.** Which instruction format has NO address field and uses a stack for operands?
(A) One-address instruction
(B) Two-address instruction
(C) Zero-address instruction
(D) More than one of the above
(E) None of the above

---

**Q13.** In a ONE-address instruction machine, where is the second (implied) operand typically stored?
(A) Stack Pointer
(B) Program Counter
(C) Accumulator (ACC)
(D) More than one of the above
(E) None of the above

---

**Q14.** The IF (Interrupt Flag) in IA-32, when set to 0, means:
(A) Interrupts are enabled
(B) Interrupts are disabled (masked)
(C) Single-step execution is active
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following is TRUE about Immediate addressing?
(A) The operand is in a register
(B) The operand is a memory address
(C) The operand is a constant value embedded in the instruction
(D) More than one of the above
(E) None of the above

---

**Q16.** `MOV AX, [BX]` where BX holds a memory address — this is an example of:
(A) Register addressing
(B) Direct addressing
(C) Register indirect addressing
(D) More than one of the above
(E) None of the above

---

**Q17.** The Carry Flag (CF) is set when:
(A) The result of an operation is zero
(B) There is a carry out of or borrow into the most significant bit
(C) The result is negative
(D) More than one of the above
(E) None of the above

---

**Q18.** In the instruction `MOV R1, #25`, the `#25` indicates:
(A) Memory address 25
(B) Register number 25
(C) Immediate operand value 25
(D) More than one of the above
(E) None of the above

---

**Q19.** Which addressing mode is FASTEST for operand access?
(A) Register indirect
(B) Direct
(C) Immediate
(D) More than one of the above
(E) None of the above

---

**Q20.** A three-address instruction like `ADD R1, R2, R3` means:
(A) R1 = R2 + R3 (destination is separate from sources)
(B) R3 = R1 + R2
(C) R1 = R1 + R2 + R3
(D) More than one of the above
(E) None of the above

---

**Q21.** Which architecture type typically uses only Load and Store instructions for memory access?
(A) CISC
(B) RISC
(C) Both equally
(D) More than one of the above
(E) None of the above

---

**Q22.** In indirect addressing, if memory[1000] = 2000 and memory[2000] = 99, then the operand value fetched via address 1000 is:
(A) 1000
(B) 2000
(C) 99
(D) More than one of the above
(E) None of the above

---

**Q23.** The Sign Flag (SF) is set when:
(A) A carry occurs from the MSB
(B) The result of an operation is negative
(C) The result is zero
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following correctly describes CISC compared to RISC?
(A) CISC uses simple, fixed-length instructions
(B) CISC uses complex, variable-length instructions
(C) CISC has more registers than RISC
(D) More than one of the above
(E) None of the above

---

**Q25.** The Overflow Flag (OF) is set when:
(A) An unsigned arithmetic operation produces a carry
(B) A SIGNED arithmetic operation produces a result out of range
(C) The result is zero
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Freedom Fighters of Bihar

---

**Q26.** Kunwar Singh led the revolt of 1857 in Bihar. He belonged to which district?
(A) Patna
(B) Champaran
(C) Bhojpur (Jagdishpur)
(D) More than one of the above
(E) None of the above

---

**Q27.** Who brought Mahatma Gandhi to Champaran to fight against the Tinkathia system?
(A) Rajendra Prasad
(B) Raj Kumar Shukla
(C) Swami Vidyanand
(D) More than one of the above
(E) None of the above

---

**Q28.** JP (Jayaprakash Narayan) escaped from which jail during the Quit India Movement (1942)?
(A) Bankipur Jail, Patna
(B) Yerwada Prison, Pune
(C) Hazaribagh Central Jail
(D) More than one of the above
(E) None of the above

---

**Q29.** Rajendra Prasad was imprisoned at which jail during the Quit India Movement?
(A) Hazaribagh Central Jail
(B) Bankipur Jail, Patna
(C) Cellular Jail, Andaman
(D) More than one of the above
(E) None of the above

---

**Q30.** The Santhal Rebellion (1855–56) was led by:
(A) Birsa Munda and Gaya Munda
(B) Sidhu and Kanhu Murmu
(C) Jatra Bhagat and Tana Bhagat
(D) More than one of the above
(E) None of the above

---

**Q31.** Birsa Munda's movement "Ulgulan" (Great Tumult) took place in which years?
(A) 1857–58
(B) 1899–1900
(C) 1914–15
(D) More than one of the above
(E) None of the above

---

**Q32.** The Tana Bhagat movement (1914) was:
(A) A Dalit movement for land rights
(B) A peasant movement against landlords
(C) A TRIBAL movement (Oraon tribe)
(D) More than one of the above
(E) None of the above

---

**Q33.** Bihar Vidyapeeth was founded in 1921 during which freedom movement?
(A) Champaran Satyagraha
(B) Non-Cooperation Movement
(C) Quit India Movement
(D) More than one of the above
(E) None of the above

---

**Q34.** JP (Jayaprakash Narayan) was born in which village and district of Bihar?
(A) Zeradei, Siwan
(B) Motihari, East Champaran
(C) Sitabdiara, Saran
(D) More than one of the above
(E) None of the above

---

**Q35.** Who was the Commander-in-Chief of Birsa Munda's forces?
(A) Sidhu Murmu
(B) Gaya Munda
(C) Jatra Bhagat
(D) More than one of the above
(E) None of the above

---

**Q36.** The Bihar Provincial Congress was formed in which year and city?
(A) 1885, Bombay
(B) 1912, Muzaffarpur
(C) 1908, Patna
(D) More than one of the above
(E) None of the above

---

**Q37.** Who co-founded the Bihar Socialist Party along with Jayaprakash Narayan?
(A) Rajendra Prasad
(B) Phulan Prasad Varma
(C) Sachindra Nath Sanyal
(D) More than one of the above
(E) None of the above

---

**Q38.** Rajendra Prasad was born on which date and at which place?
(A) December 3, 1884, at Zeradei, Siwan, Bihar
(B) January 26, 1884, at Patna, Bihar
(C) December 3, 1880, at Champaran, Bihar
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following correctly ORDERS the tribal revolts chronologically?
(A) Birsa Munda → Santhal → Tana Bhagat
(B) Santhal → Birsa Munda → Tana Bhagat
(C) Tana Bhagat → Santhal → Birsa Munda
(D) More than one of the above
(E) None of the above

---

**Q40.** Birsa Munda is called "Dharti Aaba" which means:
(A) Son of the Soil
(B) Father of the Earth
(C) King of the Tribe
(D) More than one of the above
(E) None of the above

---

**Q41.** When did Kunwar Singh die, and what was the cause?
(A) He was hanged by the British in 1858
(B) He died of a battle wound on April 26, 1858
(C) He died in prison in 1860
(D) More than one of the above
(E) None of the above

---

**Q42.** JP's escape from Hazaribagh Jail took place on which date?
(A) August 9, 1942
(B) November 9, 1942
(C) August 15, 1942
(D) More than one of the above
(E) None of the above

---

**Q43.** Who received Mahatma Gandhi in Patna before the Champaran Satyagraha began?
(A) Raj Kumar Shukla
(B) Swami Vidyanand
(C) Rajendra Prasad
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of these statements about Rajendra Prasad is TRUE?
(A) He was India's first and longest-serving President (12 years, 2 terms)
(B) He received Bharat Ratna in 1962 while still serving as President
(C) He died at Sadaqat Ashram, Patna on February 28, 1963
(D) More than one of the above
(E) None of the above

---

**Q45.** Anushilan Samiti's Patna branch was founded in 1913 by:
(A) Jayaprakash Narayan
(B) Phulan Prasad Varma
(C) Sachindra Nath Sanyal
(D) More than one of the above
(E) None of the above

---

**Q46.** Swami Vidyanand is associated with:
(A) Champaran Satyagraha — brought Gandhi to Bihar
(B) Non-Cooperation Movement — led Bihar peasants
(C) Santhal Rebellion — tribal leader
(D) More than one of the above
(E) None of the above

---

**Q47.** Who continued the 1857 revolt in Bihar after Kunwar Singh?
(A) Raj Kumar Shukla
(B) Amar Singh (brother of Kunwar Singh)
(C) Gaya Munda
(D) More than one of the above
(E) None of the above

---

**Q48.** MATCH THE FOLLOWING — Freedom fighter and their movement:
```
Fighter               Movement
1. Kunwar Singh       A. Ulgulan (Great Tumult) 1899–1900
2. Birsa Munda        B. 1857 Revolt in Bihar (Jagdishpur)
3. Sidhu & Kanhu      C. Champaran — brought Gandhi
4. Raj Kumar Shukla   D. Santhal Rebellion 1855–56
```
(A) 1-B, 2-A, 3-D, 4-C
(B) 1-A, 2-B, 3-C, 4-D
(C) 1-B, 2-D, 3-A, 4-C
(D) More than one of the above
(E) None of the above

---

**Q49.** Birsa Munda died in which jail and in which year?
(A) Bankipur Jail, Patna — 1900
(B) Hazaribagh Jail — 1942
(C) Ranchi Jail — 1900
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following is CORRECTLY matched?
(A) JP — Sitabdiara, Saran, Bihar — escaped Hazaribagh jail Nov 9, 1942
(B) Rajendra Prasad — Zeradei, Siwan, Bihar — First President of India
(C) Kunwar Singh — Jagdishpur, Bhojpur, Bihar — led 1857 revolt
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                         |
|----|--------|---------------------------------------------------------------------------|
| 1  | (C)    | Immediate = operand is directly IN the instruction itself                 |
| 2  | (C)    | "ADD X Y" format = Absolute / Direct addressing (PYQ tested fact)         |
| 3  | (B)    | Indirect = address → address → data = TWO memory accesses                 |
| 4  | (B)    | Register indirect: register holds the MEMORY ADDRESS of operand           |
| 5  | (C)    | Immediate is the most common addressing mode in CPU instruction sets      |
| 6  | (C)    | TF = Trap Flag = enables single-step / debug execution                    |
| 7  | (B)    | IOPL = 2-bit field (values 0–3) controlling I/O privilege level           |
| 8  | (A)    | IA-32 control flags = TF, IF, IOPL (the three conditional flags)          |
| 9  | (B)    | ZF (Zero Flag) is set when result of operation = 0                        |
| 10 | (C)    | Register addressing = operand is in a register = NO memory access         |
| 11 | (B)    | RISC = simple fixed-length instructions + more registers                  |
| 12 | (C)    | Zero-address = no address field; uses STACK for operands                  |
| 13 | (C)    | One-address machine: second implied operand = ACCUMULATOR                 |
| 14 | (B)    | IF=0 means interrupts are DISABLED (masked)                               |
| 15 | (C)    | Immediate = constant value embedded directly in the instruction           |
| 16 | (C)    | MOV AX, [BX] = BX holds address → register indirect addressing           |
| 17 | (B)    | CF (Carry Flag) = carry out of or borrow into the MSB                     |
| 18 | (C)    | #25 notation = immediate operand value 25                                 |
| 19 | (C)    | Immediate is fastest (operand right there, no memory/register access)     |
| 20 | (A)    | ADD R1,R2,R3 → R3 = R1 + R2 in typical RISC three-address format         |
| 21 | (B)    | RISC = Load/Store architecture (only these two access memory)             |
| 22 | (C)    | Indirect: [1000]=2000, [2000]=99 → operand = 99                           |
| 23 | (B)    | SF (Sign Flag) set when result is NEGATIVE (MSB = 1)                      |
| 24 | (B)    | CISC = complex variable-length instructions (opposite of RISC)            |
| 25 | (B)    | OF (Overflow Flag) = SIGNED arithmetic result out of representable range  |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                      |
|----|--------|------------------------------------------------------------------------|
| 26 | (C)    | Kunwar Singh = Jagdishpur, BHOJPUR district — always tested this way   |
| 27 | (B)    | Raj Kumar Shukla = indigo farmer who persistently brought Gandhi       |
| 28 | (C)    | JP escaped HAZARIBAGH CENTRAL JAIL on November 9, 1942                 |
| 29 | (B)    | Rajendra Prasad imprisoned at BANKIPUR JAIL, PATNA during QIM          |
| 30 | (B)    | Santhal Rebellion = SIDHU and KANHU MURMU (1855–56)                    |
| 31 | (B)    | Birsa Munda's Ulgulan = 1899–1900                                      |
| 32 | (C)    | Tana Bhagat = TRIBAL movement (Oraon tribe) — NOT Dalit or peasant     |
| 33 | (B)    | Bihar Vidyapeeth founded 1921 during NON-COOPERATION MOVEMENT          |
| 34 | (C)    | JP born at Sitabdiara, SARAN district, Bihar                           |
| 35 | (B)    | Gaya Munda = Commander-in-Chief of Birsa Munda's forces                |
| 36 | (C)    | Bihar Provincial Congress = 1908, Patna                                |
| 37 | (B)    | Bihar Socialist Party = JP + PHULAN PRASAD VARMA (1934)                |
| 38 | (A)    | Rajendra Prasad = December 3, 1884, Zeradei, SIWAN, Bihar              |
| 39 | (B)    | Santhal(1855) → Birsa Munda(1899) → Tana Bhagat(1914) = correct order  |
| 40 | (B)    | "Dharti Aaba" = Father of the Earth (tribal name for Birsa Munda)      |
| 41 | (B)    | Kunwar Singh died April 26, 1858 from a battle wound (not hanged)      |
| 42 | (B)    | JP's Hazaribagh escape = November 9, 1942                              |
| 43 | (C)    | Rajendra Prasad received Gandhi in Patna (Raj Kumar Shukla brought him)|
| 44 | (D)    | ALL three statements about Rajendra Prasad are correct                 |
| 45 | (C)    | Sachindra Nath Sanyal founded Anushilan Samiti, Patna (1913)           |
| 46 | (B)    | Swami Vidyanand led Bihar PEASANTS in Non-Cooperation Movement         |
| 47 | (B)    | AMAR SINGH (brother of Kunwar Singh) continued Bihar's 1857 revolt     |
| 48 | (A)    | Kunwar Singh-B, Birsa-A, Sidhu/Kanhu-D, Raj Kumar Shukla-C            |
| 49 | (C)    | Birsa Munda died in RANCHI JAIL, 1900                                  |
| 50 | (D)    | ALL three — JP, Rajendra Prasad, Kunwar Singh — all correctly matched  |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (Addressing Modes + IA-32 Flags)

```
ADDRESSING MODES:
1.  Immediate  = operand IN the instruction itself (most common!) ← PYQ
2.  Direct     = instruction gives ACTUAL memory address of operand
3.  Indirect   = instruction gives address of address → 2 memory accesses
4.  Register   = operand in a register (no memory access at all)
5.  Reg.Indirect = register holds the address of operand → 1 memory access

KEY PYQ FACTS:
6.  "ADD X Y" format = ABSOLUTE / DIRECT addressing ← tested!
7.  Most common addressing mode = IMMEDIATE ← tested!
8.  Slowest (most accesses) = INDIRECT (2 accesses)
9.  No memory access at all = REGISTER addressing
10. Speed: Immediate ≈ Register > Register Indirect = Direct > Indirect

IA-32 CONTROL FLAGS (memorize these 3!):
11. TF = Trap Flag     = single-step/debug execution mode
12. IF = Interrupt Flag = IF=1 → interrupts enabled; IF=0 → disabled
13. IOPL = I/O Privilege Level = 2-bit (0–3); controls I/O access

IA-32 STATUS FLAGS (set by ALU):
14. ZF = Zero Flag     = result is 0
15. CF = Carry Flag    = carry out from MSB
16. SF = Sign Flag     = result is negative (MSB=1)
17. OF = Overflow Flag = signed arithmetic overflow
18. PF = Parity Flag   = even number of 1-bits in result

INSTRUCTION FORMATS:
19. Zero-address  = uses STACK; no address field (e.g. PUSH, POP)
20. One-address   = one operand given; second implied = ACCUMULATOR
21. Two-address   = two operands; result replaces one (ADD R1, R2)
22. Three-address = separate dest. and 2 sources (ADD R1, R2, R3)

RISC vs CISC:
23. RISC = simple fixed-length instructions + MORE registers
24. CISC = complex variable-length instructions + fewer registers
25. RISC = Load/Store ONLY for memory access
26. CISC = any instruction can access memory
27. RISC examples = ARM, MIPS | CISC examples = Intel x86, IA-32

EXAM TRAPS:
28. "RISC has more instructions" → WRONG; RISC has fewer, simpler ones
29. "RISC has fewer registers" → WRONG; RISC has MORE registers
30. "Most common mode = Direct" → WRONG; it is IMMEDIATE
```

---

### ⚡ GS — 30 MUST-KNOW FACTS (Bihar Freedom Fighters)

```
1857 REVOLT:
1.  Kunwar Singh = led Bihar's 1857 revolt | Jagdishpur, BHOJPUR ← always tested
2.  He was ~80 years old — known as folk hero / "Lion of 1857"
3.  Died April 26, 1858 from a battle wound (NOT hanged!)
4.  AMAR SINGH = his brother who continued revolt after him

CHAMPARAN 1917 (BIHAR #1 PRIORITY):
5.  RAJ KUMAR SHUKLA = indigo farmer who BROUGHT Gandhi to Champaran
6.  Gandhi arrived Motihari, April 15, 1917
7.  RAJENDRA PRASAD received Gandhi in Patna
8.  Tinkathia = 3/20 land forced for indigo cultivation

RAJENDRA PRASAD:
9.  Born December 3, 1884 | Zeradei, SIWAN, BIHAR
10. Founded BIHAR VIDYAPEETH 1921 (during NCM)
11. Imprisoned at BANKIPUR JAIL, PATNA during Quit India 1942
12. Elected CA President December 9, 1946
13. First President of India January 26, 1950
14. 2 terms, 12 years — LONGEST SERVING President
15. BHARAT RATNA 1962 (while still President!)
16. Died February 28, 1963, SADAQAT ASHRAM, PATNA

JAYAPRAKASH NARAYAN (JP):
17. Born at SITABDIARA, SARAN, BIHAR
18. Co-founded Bihar Socialist Party (1934) with PHULAN PRASAD VARMA
19. Led underground Quit India Movement
20. ESCAPED HAZARIBAGH CENTRAL JAIL — November 9, 1942 ← PYQ

TRIBAL REVOLTS (chronological — memorize order!):
21. Santhal Rebellion 1855–56 = FIRST tribal revolt | SIDHU & KANHU MURMU
22. Birsa Munda / Ulgulan 1899–1900 | MUNDA tribe | "Dharti Aaba"
23. Birsa Munda died in RANCHI JAIL, 1900
24. GAYA MUNDA = Commander-in-Chief of Birsa's forces
25. Tana Bhagat 1914 = TRIBAL (Oraon tribe) — NOT Dalit NOT peasant ← trap!
26. Order: Santhal(1855) → Birsa(1899) → Tana Bhagat(1914)

OTHER KEY FIGURES:
27. SWAMI VIDYANAND = led Bihar PEASANTS in NCM
28. SACHINDRA NATH SANYAL = Anushilan Samiti Patna (1913)
29. Bihar Provincial Congress = 1908, Patna
30. Bihar Province separated from Bengal = 1912
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
ADDRESSING MODE   WHERE IS OPERAND?          ACCESSES    PYQ TRIGGER
────────────────────────────────────────────────────────────────────
Immediate         In the instruction          0 memory   Most common!
Direct/Absolute   At given memory address     1 memory   "ADD X Y" = this
Indirect          Address → address → data    2 memory   Slowest basic mode
Register          In a register               0 memory   Fastest with no memory
Register Indirect Register holds address      1 memory   MOV R1,[R2]
────────────────────────────────────────────────────────────────────

BIHAR FIGURE    DISTRICT        MOVEMENT / EVENT
────────────────────────────────────────────────────────────────────
Kunwar Singh    Bhojpur         1857 revolt (died of wound Apr 26, 1858)
Rajendra Prasad Siwan (Zeradei) Bihar Vidyapeeth; 1st President; BharatRatna
JP              Saran           Bihar Socialist Party; Hazaribagh escape
Raj K. Shukla   Champaran       Brought Gandhi to Champaran
Birsa Munda     Ranchi (Jharkhand) Ulgulan 1899; Dharti Aaba; Gaya Munda=CiC
Sidhu & Kanhu   Santhal Pargana Santhal Rebellion 1855–56 (FIRST revolt)
Swami Vidyanand Bihar           Led Bihar peasants in NCM
────────────────────────────────────────────────────────────────────
```

---

## 🎯 DAY 76 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   Addressing Modes — Immediate, Direct/Absolute, Indirect,
      Register, Register Indirect | "ADD X Y" = Absolute |
      Most common = Immediate | IA-32 Flags: TF, IF, IOPL (control)
      + ZF, CF, SF, OF (status) | RISC vs CISC | Instruction formats

GS:   Bihar Freedom Fighters — Kunwar Singh, Rajendra Prasad, JP,
      Raj Kumar Shukla, Birsa Munda, Sidhu & Kanhu, Tana Bhagat,
      Swami Vidyanand, Sachindra Nath Sanyal | All key dates

NEXT: Day 77 — Memory Types (SRAM/DRAM, ROM variants, EPROM, EEPROM)
      + Buffer Registers + PCI Bus + ASCII vs EBCDIC
      GS: Biology — Plant Topics
```

---

*Day 76 of 170 | Phase 2: Depth | Week 12: Computer Architecture + Software Engineering*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
