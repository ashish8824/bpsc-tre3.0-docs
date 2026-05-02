# 📅 BPSC TRE 4.0 — DAY 55 COMPLETE STUDY MODULE
### Compiler Theory + Languages + OS Concepts (CS) + India & Bihar Geography (GS)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Compiler Theory + Programming Languages + OS extras — all PYQ-tested facts
> - Afternoon (1 hr): India & Bihar Geography — story-based + every PYQ fact
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 Compiler Theory + Programming Languages + System Software

> **Day 55 Context:** Compiler Theory appeared in **TRE 1.0 Q44** as a three-statement question where all three were correct → Answer = D. Programming language classifications (PASCAL, FORTRAN, COBOL, BASIC) appear 1–2 times per paper. Open source, OS concepts, and Turing machine are low-frequency but high-certainty when they appear. Today covers all of them in one sitting.

---

## 🔷 BLOCK 1: System Software — The Full Translator Family

```
SYSTEM SOFTWARE = Programs that manage computer hardware and support other software
               = The "behind the scenes" layer between hardware and user applications

Types of system software:
  1. Operating System  → manages all resources
  2. Language translators (Compiler, Interpreter, Assembler)
  3. Linker
  4. Loader
  5. Device drivers
  6. Utility programs
```

---

## 🔷 BLOCK 2: Language Translators — Deep Comparison

### The Four Translators:

```
════════════════════════════════════════════════════════════
COMPILER
════════════════════════════════════════════════════════════
What it does: Translates the ENTIRE source program into
              object code / machine code IN ONE GO (AT ONCE)
Input:        SOURCE PROGRAM (high-level language code)   ← PYQ
Output:       OBJECT CODE (machine/binary code)           ← PYQ
Execution:    NOT involved in execution (only translation) ← PYQ

TRE 1.0 Q44 — ALL THREE of these statements are TRUE: ← PYQ EXACT QUESTION
  Statement 1: Compiler takes source program as input
  Statement 2: Compiler produces object code as output
  Statement 3: Compiler is not involved in execution of the program
  Answer = D (More than one of the above) — ALL THREE ARE CORRECT

Error handling:
  → Lists ALL errors AFTER scanning the complete program
  → Program does not run until ALL errors are fixed

Speed advantage:
  → After compilation, COMPILED program runs FASTER than interpreted
  → Because translation already done; machine code runs directly

Examples of compiled languages:
  → C, C++, Java (to bytecode), Fortran, Pascal

════════════════════════════════════════════════════════════
INTERPRETER
════════════════════════════════════════════════════════════
What it does: Translates and EXECUTES program LINE BY LINE
              (does NOT produce separate object code)
Input:        Source code
Output:       Direct execution (no separate object file)

Key differences from compiler:
  → Translates ONE LINE at a time, executes it, then moves to next
  → Stops at FIRST ERROR (shows error immediately)
  → Slower execution (re-translates every time the program runs)
  → No separate object file produced

Examples of interpreted languages:
  → Python (traditional mode), JavaScript, Ruby, BASIC
  → PHP (server-side)

════════════════════════════════════════════════════════════
ASSEMBLER
════════════════════════════════════════════════════════════
What it does: Translates ASSEMBLY LANGUAGE → MACHINE CODE
Input:        Assembly language program (mnemonics: MOV, ADD, JMP)
Output:       Machine code (binary)

Assembly language = LOW-LEVEL programming language ← PYQ
  → Uses mnemonics (symbolic codes) instead of binary
  → One assembly instruction = one machine code instruction
  → Machine-dependent (different for each processor family)

════════════════════════════════════════════════════════════
LINKER
════════════════════════════════════════════════════════════
What it does: COMBINES multiple object files into one executable
Input:        Multiple .obj / object files
Output:       Executable (.exe) file

Why needed:
  → Large programs are written in multiple files
  → Each file is compiled separately into object code
  → Linker joins all object files + library functions into ONE executable

Types:
  Static linker  → copies all library code into executable
  Dynamic linker → links libraries at RUNTIME (DLL, .so files)

════════════════════════════════════════════════════════════
LOADER
════════════════════════════════════════════════════════════
What it does: LOADS the executable into MEMORY for execution
Input:        Executable file
Output:       Program running in memory

Function:
  → Allocates memory space for the program
  → Copies the executable from disk into RAM
  → Transfers control to the program's starting address
  → OS handles loading when you double-click a program
```

### 🚨 PYQ TRAP #1 — TRE 1.0 Q44 (The Compiler Question):
> All THREE statements about compiler are correct:
> (1) Input = source program; (2) Output = object code; (3) Not involved in execution.
> Answer = **D (More than one of the above)** — this is the exact trap.
> Students who know only one or two facts choose A, B, or C — but ALL THREE are correct.

### The Translation Pipeline:
```
SOURCE CODE (.c, .java, .py)
        ↓ COMPILER/INTERPRETER
OBJECT CODE (.obj, .class)
        ↓ LINKER
EXECUTABLE (.exe, .out)
        ↓ LOADER
RUNNING PROGRAM (in RAM)
```

---

## 🔷 BLOCK 3: Programming Languages — PYQ Classifications

### High-Level vs Low-Level:
```
LOW-LEVEL LANGUAGES:
  1. Machine Language  → pure binary (0s and 1s); directly executed by CPU
  2. Assembly Language → mnemonics; one step above binary; ASSEMBLER translates it ← PYQ

HIGH-LEVEL LANGUAGES:
  → English-like syntax; machine-independent; easier to read and write
  → Need compiler or interpreter to translate
  → Examples: C, C++, Java, Python, COBOL, FORTRAN, Pascal, BASIC
```

### Language-Purpose Classifications: ← All PYQ-Tested

```
PASCAL:
  Purpose: Best for writing STRUCTURED CODE ← PYQ exact phrase
  Designer: Niklaus Wirth (1970)
  Features: Strong typing, structured programming (no GOTO jumps)
            Enforces clean code structure
  Used for: Teaching programming discipline, early software development
  ⚠️ PYQ: "Which language is best for writing structured programs?" → PASCAL

FORTRAN (Formula Translation):
  Purpose: SCIENTIFIC and ENGINEERING computing ← PYQ
  Designed: 1957 by IBM (John Backus) — oldest high-level language
  Features: Excellent for numerical/mathematical computation
            Array and matrix operations
  Used for: Weather forecasting, physics simulation, engineering calculations
  ⚠️ PYQ: "Which language is used for scientific and engineering problems?" → FORTRAN

COBOL (Common Business-Oriented Language):
  Purpose: BUSINESS DATA PROCESSING ← PYQ
  Designed: 1959 (Grace Hopper team)
  Features: English-like syntax; handles large data files
            File processing, payroll, banking systems
  Used for: Banking systems, insurance, government data processing
  Still runs: 90%+ of ATM transactions worldwide run COBOL!
  ⚠️ PYQ: "Which language is used for business data processing?" → COBOL

BASIC (Beginners' All-purpose Symbolic Instruction Code):
  Purpose: BEGINNERS' programming language ← PYQ
  Designed: 1964 by Kemeny and Kurtz (Dartmouth College)
  Features: Easy to learn; interactive; simple syntax
  Used for: Teaching programming to beginners
  ⚠️ PYQ: "Which language was designed for beginners?" → BASIC

C:
  Purpose: SYSTEM PROGRAMMING and general-purpose ← PYQ
  Features: Low-level memory control; fast; portable
  Used for: Operating systems (Unix/Linux written in C), drivers, embedded

C++:
  Purpose: OBJECT-ORIENTED programming (extends C) ← PYQ
  Features: OOP + procedural; 4th generation language

Java:
  Purpose: Platform-independent, object-oriented
  "Write once, run anywhere" — JVM (Java Virtual Machine)
  4th generation language
```

### 🚨 PYQ TRAP #2:
> **PASCAL = structured code** (not scientific, not business, not beginners).
> **FORTRAN = scientific/engineering** (not PASCAL, not COBOL).
> **COBOL = business data processing** (not FORTRAN, not BASIC).
> **BASIC = beginners** (not PASCAL — Pascal is for structured, not beginner).
> These four are each other's most common distractors.

---

## 🔷 BLOCK 4: Open Source Software

```
OPEN SOURCE SOFTWARE:
  = Software where the SOURCE CODE is:
    ✅ Available to VIEW ← PYQ
    ✅ Available to MODIFY ← PYQ
    ✅ Available to REDISTRIBUTE (share with others) ← PYQ
  ← All THREE are the definition of open source ← TRE tested "all three" format!

Examples of open source software:
  → Linux (OS), Android (OS — based on Linux)
  → Firefox (browser), LibreOffice (office suite)
  → Python, PHP (programming languages)
  → MySQL, PostgreSQL (databases)
  → VLC Media Player

CLOSED SOURCE (Proprietary) software:
  → Source code NOT available (you can only use the compiled program)
  → Examples: Windows, Microsoft Office, Photoshop, macOS

FREE SOFTWARE vs OPEN SOURCE:
  Free software (GNU/FSF definition) = four freedoms: run, study, modify, distribute
  Open source = similar but emphasises developer collaboration over philosophy
  In practice: largely overlapping concepts (often called "FOSS" = Free and Open Source)

⚠️ PYQ TRAP: "Open source means ___?"
             All three: view + modify + redistribute
             NOT just "free to use" (that's freeware, different concept)
             NOT just "view" (must also allow modify and redistribute)
```

---

## 🔷 BLOCK 5: Operating System Concepts — Remaining PYQ Facts

### Time Sharing and Computer Communications:
```
TIME SHARING:
  = Multiple users share ONE computer simultaneously
  = CPU rapidly switches between users (each gets a time slice)
  = Users feel they have the computer to themselves

TIME SHARING marks the beginning of COMPUTER COMMUNICATIONS ← PYQ exact phrase
  → First time multiple users could interact with a computer remotely
  → Led to: terminals, networks, eventually the internet

TYPES OF OPERATING SYSTEMS:
  Batch OS        → Jobs collected, processed in batches; no user interaction
  Time-sharing OS → Multiple interactive users simultaneously
  Real-time OS    → RTOS; guaranteed response within a fixed time (aircraft, missiles)
  Embedded OS     → Inside devices (microwave, washing machine, car ECU)
  Network OS      → Manages network resources (file servers)
  Distributed OS  → Manages multiple interconnected computers as one system
```

### Turing Machine:
```
TURING MACHINE components: ← PYQ — one component is a wrong option planted
  ✅ TAPE with read/write head (infinite tape divided into cells)
  ✅ HEAD (read/write head that moves left or right)
  ✅ STATE REGISTER (stores current state of the machine)
  ✅ TRANSITION FUNCTION (rules: given state + symbol → new state + write + move)

  ❌ "OUTPUT TAPE" = NOT a component ← PYQ WRONG OPTION
     There is only ONE tape (the input/work/output tape is the same)

HALTING PROBLEM:
  = "Given a program and input, will the program halt (finish) or run forever?"
  = UNDECIDABLE (NOT computable) ← PYQ
  = Alan Turing proved no algorithm can solve this for all programs
```

### Process Management Quick Facts:
```
TYPES OF INTERRUPTS:
  ✅ Hardware interrupt (from devices — keyboard, mouse, disk)
  ✅ Software interrupt (from programs — system calls)
  ✅ Trap (internal error or special instruction)
  ❌ "Memory interrupt" = NOT a valid type ← PYQ wrong option

THREAD:
  = Lightweight process; smallest unit of execution
  A thread shares with other threads in the SAME PROCESS: ← PYQ
    ✅ Code section
    ✅ Data section
    (Each thread has its own stack and registers)
```

### Memory Management:
```
PAGE (virtual memory):
  = Fixed-size block of virtual memory ← PYQ definition

PAGE OFFSET BITS for 4KB page:
  4KB = 4 × 1024 = 4096 bytes = 2¹² bytes
  → Page offset needs 12 bits ← PYQ calculation

TLB (Translation Lookaside Buffer):
  = Organised as ASSOCIATIVE CACHE ← PYQ exact phrase
  = High-speed cache for recent virtual-to-physical address translations

THRASHING:
  = Caused by excessive paging activity ← PYQ
  = CPU spends more time swapping pages than executing actual work
  = Happens when too many processes compete for too little RAM
```

### CPU and Architecture:
```
BRAIN OF COMPUTER = CPU (Central Processing Unit) ← PYQ
CONTROL UNIT generates: CONTROL SIGNALS ← PYQ exact phrase
                        (signals that coordinate all CPU operations)

ADDRESSING MODES:
  Immediate addressing = operand is in the instruction itself ← most common ← PYQ
  Direct addressing    = instruction contains address of operand
  Indirect addressing  = instruction contains address that holds the address of operand
  ADD X Y format       = ABSOLUTE addressing ← PYQ

KEYSTROKE TO BITS: ASCII standard ← PYQ
  ASCII = American Standard Code for Information Interchange
  Maps characters to 7-bit binary numbers
```

---

## 📊 CS RAPID FIRE — Today's 1-Line Recall Table

| Concept | Key Fact |
|---------|----------|
| Compiler input | Source program |
| Compiler output | Object code |
| Compiler + execution | NOT involved in execution |
| TRE 1.0 Q44 | All 3 compiler statements correct → Answer D |
| Interpreter | Translates line by line; stops at first error |
| Assembler | Assembly language → machine code |
| Linker | Combines object files → executable |
| Loader | Loads executable into memory |
| Assembly language | LOW-LEVEL programming language |
| PASCAL | Best for **structured code** |
| FORTRAN | Scientific and engineering computing |
| COBOL | Business data processing |
| BASIC | Beginners' programming |
| Open source | View + Modify + Redistribute (all three) |
| Time sharing | Marks beginning of **computer communications** |
| Turing machine wrong component | "Output tape" (does NOT exist) |
| Halting problem | Undecidable / NOT computable |
| "Memory interrupt" | NOT a valid interrupt type |
| Thread shares | Code section + data section (same process) |
| 4KB page offset | 12 bits (2¹² = 4096) |
| TLB | Organised as associative cache |
| Thrashing | Excessive paging activity |
| Brain of computer | CPU |
| Control unit generates | Control signals |
| Most common addressing | Immediate addressing |
| Keystroke → bits | ASCII standard |

---
---

# PART 2: GENERAL STUDIES
## 🗺️ India & Bihar Geography — Complete PYQ-Focused Deep Dive

> **Why Day 55?** Geography is 6–8 marks per BPSC TRE paper — **almost entirely factual recall**. Every single question is either "which district/state has X" or "what is the height/location of Y." These are the easiest GS marks if you've memorised the facts, and the most frustrating to lose if you haven't. Today: every geography PYQ fact, story-linked for maximum retention.

---

## 🔷 SECTION 1: BIHAR — Specific Facts

### Bihar Demographics:
```
Bihar's share of India's population: 8.58% ← PYQ exact figure
  → Bihar is the 3rd most populous state in India (after UP and Maharashtra)
  → One of the most densely populated states (high density, small area)

Bihar area: approximately 94,163 sq km
  → 12th largest state by area
  → Located in eastern India; landlocked (no sea coast)
```

### Bihar Agriculture — District-wise:
```
MAXIMUM PADDY (rice) PRODUCTION in Bihar:
  → ROHTAS DISTRICT ← PYQ exact answer
  → Located in southwest Bihar; fertile plains; irrigated by Sone river
  → Rohtas is also known for: Rohtasgarh Fort (historical)

MAXIMUM SILK PRODUCTION in Bihar:
  → BHAGALPUR DISTRICT ← PYQ exact answer
  → Bhagalpur is called "SILK CITY" of India ← important contextual fact
  → Famous for Tussar silk (a specific variety of wild silk)
  → Located on the banks of River Ganga in eastern Bihar

Other Bihar agriculture facts:
  → Bihar is a major producer of: vegetables, litchi, makhana (fox nuts)
  → Muzaffarpur = famous for LITCHI (India's litchi capital)
  → Darbhanga = Mithila region; Madhubani painting
  → Mithila Makhana (from North Bihar) = GI tag
```

### Bihar Administrative Facts:
```
Bihar districts: 38 (after 2001 separation from Jharkhand)
  → Originally 55 districts before Jharkhand separated in 2000
Bihar divisions: 9 (Patna, Magadha, Nalanda, Munger, Bhagalpur,
                    Purnia, Kosi, Darbhanga, Tirhut, Saran)

Capital:          PATNA (also called Pataliputra — historic capital of Mauryan empire!)
Longest river:    GANGA (flows east to west through the centre of Bihar)
Important rivers: Son, Gandak, Koshi (the "Sorrow of Bihar"), Bagmati, Budhi Gandak

Koshi river:
  → Called "SORROW OF BIHAR" ← PYQ
  → Reason: Changes course frequently; causes devastating floods
  → Originates in Nepal (Himalayas)
```

---

## 🔷 SECTION 2: INDIA — Physical Geography

### Major Physiographic Divisions:
```
India has SIX physiographic divisions:
  1. The Himalayan Mountains (North)
  2. The Northern Plains (Indo-Gangetic Plain)
  3. The Peninsular Plateau (Deccan)
  4. The Indian Desert (Thar Desert, Rajasthan)
  5. The Coastal Plains (East + West coasts)
  6. The Islands (Andaman + Lakshadweep)
```

### The Peninsular Plateau — PYQ Facts:
```
PENINSULAR PLATEAU (DECCAN PLATEAU):
  → Part of GONDWANA LAND (ancient supercontinent) ← PYQ
  → South Peninsular Upland = part of Gondwana Land ← PYQ exact phrase
  → Made of very old, hard crystalline rocks (Precambrian)
  → Average elevation: 600–900 metres

The plateau is divided by:
  → Narmada river valley → Northern Deccan / Central Highlands (Malwa, Vindhya)
                         → Southern Deccan Plateau proper

WESTERN GHATS (Sahyadri):
  → Run along the western edge of Deccan Plateau (Maharashtra to Kerala)
  → Average elevation: 1000–1500 m
  → Highest peak: ANAMUDI (2695 m) in Kerala ← India's highest peak south of Himalayas
  → Receives heavy orographic rainfall (windward side)
  → Biodiversity hotspot

EASTERN GHATS:
  → Lower, discontinuous ranges along eastern coast
  → Average elevation: 600 m (much lower than Western Ghats)
  → Highest peak: MAHENDRAGIRI (1501 m) in Odisha ← PYQ exact fact
  → Cut by rivers: Mahanadi, Godavari, Krishna, Kaveri
```

### 🚨 PYQ TRAP #3:
> Eastern Ghats highest peak = **Mahendragiri** (in Odisha) — NOT Anaimudi (that's Western Ghats).
> South Peninsular Upland = part of **Gondwana Land** (not Tethys Sea, not Himalayan fold).

---

## 🔷 SECTION 3: SPECIFIC REGION FACTS

### Malnad Region:
```
MALNAD = Western Ghats region of KARNATAKA ← PYQ exact answer
       = "Hilly country" in Kannada
       = The plateau/hilly region of Karnataka (Western Ghats eastern slope)

⚠️ PYQ: "Malnad region belongs to which state?"
         Answer: KARNATAKA
         NOT Maharashtra, NOT Kerala (though W.Ghats run through them too)
         Malnad specifically = Karnataka's Western Ghats zone
```

### Black Soil (Regur Soil):
```
BLACK SOIL (Regur / Black Cotton Soil):
  = Formed from BASALTIC (volcanic) LAVA rock
  = Highly FERTILE; retains moisture; swells when wet, cracks when dry
  = Ideal for COTTON cultivation ← hence "black cotton soil"

FOUND IN: ← PYQ KEY ANSWER
  → KARNATAKA ✅
  → GUJARAT ✅
  → Maharashtra (Deccan Trap region) ✅
  → Madhya Pradesh ✅

⚠️ PYQ: "Black soil is found in which states?"
         Options: (A) Karnataka (B) Gujarat (C) Both
         Answer = (D) More than one of the above — BOTH Karnataka AND Gujarat ← PYQ trap
         Karnataka + Gujarat are the most commonly given options;
         both have black soil → Answer D

Why multiple states?
  → The Deccan Trap volcanic rocks extend across Maharashtra, Karnataka, Gujarat, MP
  → All these states have black basaltic soil
```

---

## 🔷 SECTION 4: CLIMATE — PYQ-Tested Facts

### Southwest Monsoon:
```
SOUTHWEST MONSOON:
  → Enters India: KERALA coast (around June 1) — first state to receive monsoon
  → Progresses: Up the western coast and across the country
  → Retreat (WITHDRAWAL) from different locations at different dates:

WITHDRAWAL OF SW MONSOON — PYQ DATES:
  → Rajasthan (northwest India): September 1 (earliest to retreat)
  → HYDERABAD: OCTOBER 1 ← PYQ exact date
  → Retreats progressively southward/southeastward
  → Last to leave: Tamil Nadu coast (December)

NORTHEAST MONSOON:
  → Occurs: October–December
  → Brings rain to: Tamil Nadu, Andhra Pradesh, southeastern India
  → Tamil Nadu gets most of its rain from NE monsoon (not SW monsoon)
```

### India's Climate Classification:
```
TREWARTHA'S CLASSIFICATION:
  → India's climate = SUBTROPICAL MONSOON ← PYQ

KOPPEN'S CLASSIFICATION:
  → Most of India = Aw (Tropical Savanna)
  → Northwest = BWh (Hot Desert)
  → Himalayan region = E (Polar)
```

---

## 🔷 SECTION 5: SOILS OF INDIA

```
TYPES OF SOILS IN INDIA:
  Alluvial soil    → Most fertile; Indo-Gangetic Plain; deposited by rivers
                     Two types: Khadar (new alluvial — near rivers) and Bangar (old alluvial)
  Black soil       → Deccan trap; cotton; Maharashtra, Karnataka, Gujarat, MP
  Red soil         → Weathered crystalline rock; Tamil Nadu, Andhra, Odisha, Jharkhand
  Laterite soil    → Heavy rainfall regions; leached; Karnataka, Kerala, Maharashtra
  Desert soil      → Rajasthan; arid; sandy
  Mountain soil    → Himalayan and hilly regions
  Forest soil      → Dense forest areas

ALLUVIAL SOIL:
  → Covers about 40% of India's total area
  → Most productive soil in India
  → Found in: UP, Bihar, West Bengal, Punjab, Haryana (Indo-Gangetic plain)
  → Bihar has largely alluvial soil ← Bihar-specific fact
```

---

## 🔷 SECTION 6: GEOMORPHOLOGY — Caves and Formations

### Stalactite and Stalagmite:
```
STALACTITE:
  = Rock formation hanging DOWN from cave ceiling
  = "Stalactite holds TIGHT to the ceiling"
  = Formed by calcium carbonate deposits from dripping water

STALAGMITE:
  = Rock formation growing UP from cave floor
  = "Stalagmite MIGHT reach the ceiling"
  = Formed by calcium carbonate deposits from dripping water

HOW BOTH ARE FORMED:
  → Rainwater + CO₂ → weak carbonic acid
  → Dissolves limestone in underground rock
  → Water drips through cracks in cave ceiling
  → Deposits calcium carbonate (CaCO₃) as water evaporates
  → Drip from ceiling → stalactite (hangs down)
  → Drip hits floor → stalagmite (builds up)

FORMED BY: UNDERGROUND WATER (through chemical weathering of limestone) ← PYQ
⚠️ PYQ: "Stalactites and Stalagmites are formed by ___?"
         Answer: Underground water (not wind, not glaciers, not rivers)
```

---

## 🔷 SECTION 7: TRANSPORT CORRIDORS

### East-West Corridor:
```
EAST-WEST CORRIDOR:
  = Part of India's National Highway Development Project (NHDP)
  = Major road connectivity project

CONNECTS: SILCHAR (Assam) ←→ PORBANDAR (Gujarat) ← PYQ exact endpoints
  → Silchar = eastern terminus (Assam, near Bangladesh border)
  → Porbandar = western terminus (Gujarat coast; birthplace of Mahatma Gandhi!)
  → Total length: ~3,640 km (one of India's longest road corridors)

Other corridors for context:
  North-South Corridor: Srinagar (J&K) ↔ Kanyakumari (Tamil Nadu)
  Golden Quadrilateral: Delhi–Mumbai–Chennai–Kolkata (4 mega-cities)

⚠️ PYQ: "East-West Corridor connects which two cities?"
         Answer: SILCHAR and PORBANDAR
         Not Leh-Porbandar; not Guwahati-Mumbai; specifically Silchar-Porbandar
```

---

## 🔷 SECTION 8: SURVEYS AND MAPS

### Survey of India:
```
TOPOGRAPHICAL MAPS OF INDIA:
  Published by: SURVEY OF INDIA ← PYQ
  Headquarters: DEHRADUN (Uttarakhand)
  
Survey of India:
  → India's national mapping organisation
  → Oldest scientific department of India (est. 1767 by the British)
  → Produces: topographic maps, geological maps, cadastral maps
  → Official topographic maps of India at 1:50,000 and 1:250,000 scales

⚠️ PYQ: "Topographical maps of India are published by ___?"
         Answer: SURVEY OF INDIA (not Geological Survey, not Census of India)
         Geological Survey of India = geological maps (rocks, minerals)
         Census of India = population data (not maps)
```

---

## 🔷 SECTION 9: URBANISATION

### Maximum Urbanisation in India:
```
STATE WITH MAXIMUM URBANISATION:
  → GOA ← PYQ
  → Goa has the highest percentage of urban population among Indian states
  → Reason: Tourism-driven economy, small area, high development
  → Urban population % of Goa: ~62% (much higher than national avg ~35%)

⚠️ PYQ: "Which Indian state has the MAXIMUM urbanisation?"
         Answer: GOA (not Maharashtra, not Tamil Nadu — they have more absolute urban people
                 but GOA has the highest PERCENTAGE of urban population)
```

---

## 🔷 SECTION 10: COMPLETE BIHAR GEOGRAPHY MASTER TABLE

| Question | Answer |
|----------|--------|
| Bihar's share of India's population | **8.58%** |
| Bihar's rank in population | 3rd (after UP and Maharashtra) |
| Maximum paddy production in Bihar | **Rohtas** district |
| Maximum silk production in Bihar | **Bhagalpur** district ("Silk City") |
| Bhagalpur silk type | Tussar silk |
| River called "Sorrow of Bihar" | **Koshi** (Kosi) |
| Bihar capital | **Patna** (Pataliputra historically) |
| Bihar number of districts | 38 |
| Famous litchi city of Bihar | Muzaffarpur |

---

## 🔷 SECTION 11: COMPLETE INDIA GEOGRAPHY MASTER TABLE

| Question | Answer |
|----------|--------|
| Eastern Ghats highest peak | **Mahendragiri** (Odisha, 1501 m) |
| Western Ghats highest peak | **Anamudi** (Kerala, 2695 m) |
| South Peninsular Upland = part of | **Gondwana Land** |
| Malnad region = | **Karnataka** (Western Ghats region) |
| Black soil found in | **Karnataka AND Gujarat** (answer D — both) |
| SW monsoon arrives India | Kerala (around June 1) |
| SW monsoon withdrawal at Hyderabad | **October 1** |
| India's climate (Trewartha) | **Subtropical monsoon** |
| Stalactites/Stalagmites formed by | **Underground water** |
| East-West Corridor endpoints | **Silchar (Assam) to Porbandar (Gujarat)** |
| Topographic maps of India | Published by **Survey of India** (Dehradun) |
| Maximum urbanisation state | **Goa** |
| Most fertile soil | Alluvial (covers 40% of India) |
| Black soil = ideal for | Cotton cultivation |
| Khadar vs Bangar | Khadar = new alluvial (near rivers); Bangar = old alluvial |

---

## 🔷 SECTION 12: ADDITIONAL HIGH-PROBABILITY GEOGRAPHY FACTS

### India's Neighbours and Borders:
```
India shares land borders with 7 countries:
  → Pakistan (west), China (north), Nepal (north), Bhutan (northeast),
    Bangladesh (east), Myanmar (east), Afghanistan (northwest — through PoK)

Longest land border: Bangladesh (4,156 km)
Longest coastline: Gujarat (among states)
                   Andaman & Nicobar Islands have longest among UTs/island groups
Southernmost point: Indira Point (Andaman Islands)
Northernmost point: Indira Col (Siachen glacier area, Ladakh)
```

### Important Rivers — Quick Recall:
```
Eastward-flowing rivers (into Bay of Bengal):
  Ganga, Yamuna, Brahmaputra, Mahanadi, Godavari, Krishna, Kaveri

Westward-flowing rivers (into Arabian Sea) ← SMALLER but important:
  Narmada, Tapi (Tapti), Mahi, Sabarmati, Luni

Rivers not joining the sea:
  Luni → ends in Rann of Kutch (salt marshes, Gujarat)

Ganga:
  → Originates: Gangotri glacier (Uttarakhand)
  → Tributaries: Yamuna, Ghagra, Gandak, Koshi, Son, Chambal, Betwa
  → Flows through: Uttarakhand, UP, Bihar, West Bengal → Bay of Bengal

Brahmaputra:
  → Originates in Tibet (called Yarlung Tsangpo there)
  → Enters India through Arunachal Pradesh
  → Flows through Assam → Bangladesh (called Jamuna) → Bay of Bengal
  → Creates LARGEST RIVER ISLAND: Majuli (Assam) ← PYQ
```

### Mountain Passes:
```
Important mountain passes:
  Zoji La    → Jammu & Kashmir; connects Srinagar to Leh
  Rohtang    → Himachal Pradesh; connects Manali to Lahaul-Spiti
  Nathu La   → Sikkim; connects India to Tibet (China)
  Bom Di La  → Arunachal Pradesh; connects Assam to Tawang
  Shipki La  → Himachal Pradesh; India-China border; Sutlej river enters India here
```

### Largest, Longest, Highest in India:
```
Largest state (area):     RAJASTHAN ← PYQ
Smallest state (area):    GOA
Most populous state:      UTTAR PRADESH
Highest peak (India):     KANGCHENJUNGA (8,586 m, Sikkim-Nepal border)
                          ← K2 is higher but in PoK (disputed)
Longest river:            GANGA (within India)
Largest lake (saltwater): CHILIKA LAKE (Odisha) ← PYQ
Largest freshwater lake:  WULAR LAKE (Jammu & Kashmir)
Largest desert:           THAR (Rajasthan + Gujarat)
Largest delta:            SUNDARBANS delta (Ganga-Brahmaputra, West Bengal)
```

---

## 🔷 SECTION 13: MEMORY TRICKS

```
BIHAR AGRICULTURE TRICK:
  "ROHTAS grows RICE, BHAGALPUR makes SILK"
  R-R: Rohtas-Rice | B-B: Bhagalpur-Bhagalpur Silk
  Koshi = SORROW (like "the river causes sorrow with its floods")

EAST-WEST CORRIDOR:
  "SILCHAR in the EAST (Assam) to PORBANDAR in the WEST (Gujarat, Gandhi's birthplace)"
  East = Assam (near Bangladesh) | West = Gujarat (sea coast)

STALACTITE vs STALAGMITE:
  "staLACTite = hangs from CEILING like drops of milk (LACT = milk in Latin)"
  "stalaGMite = GROWS from GROUND (G = Ground)"
  OR: "Stalactite holds TIGHT to the ceiling"

EASTERN GHATS HIGHEST = MAHENDRAGIRI:
  "MAHI (Mahendragiri) is the EASTERN peak" ← both start with Eastern/E sounds
  "ANAI (Anamudi) is in KERALA" ← both contain vowel-heavy sounds

BLACK SOIL = KARNATAKA + GUJARAT (both → answer D):
  "BLACK soil is found in KARNATAKA and GUJARAT — both are 'K' and 'G' states"
  Just remember: the Deccan Trap volcanic lava spread across both

SURVEY OF INDIA = TOPOGRAPHIC MAPS = DEHRADUN:
  "SURVEY in DEHRADUN → where surveyors SURVEY the hills" ← literal image
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topic: Compiler Theory + Programming Languages + OS Concepts

---

**Q1.** A COMPILER takes which of the following as INPUT?
(A) Object code
(B) Machine code (binary)
(C) Source program (high-level language code)
(D) More than one of the above
(E) None of the above

---

**Q2.** A COMPILER produces which of the following as OUTPUT?
(A) Executable (.exe) file directly
(B) Source code in a different language
(C) Object code
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following is TRUE about a COMPILER?
(Statement 1: Takes source program as input)
(Statement 2: Produces object code as output)
(Statement 3: Is not involved in execution of the program)
(A) Only Statement 1 is correct
(B) Only Statements 1 and 2 are correct
(C) Only Statement 3 is correct
(D) More than one of the above
(E) None of the above

---

**Q4.** An INTERPRETER differs from a COMPILER in that:
(A) Interpreter produces faster-running programs than a compiler
(B) Interpreter translates and executes the program line by line
(C) Interpreter produces a separate object file
(D) More than one of the above
(E) None of the above

---

**Q5.** An ASSEMBLER translates:
(A) High-level language to object code
(B) Object code to executable
(C) Assembly language to machine code
(D) More than one of the above
(E) None of the above

---

**Q6.** A LINKER performs which function?
(A) Loads the executable into memory for execution
(B) Translates source code into object code
(C) Combines multiple object files into a single executable
(D) More than one of the above
(E) None of the above

---

**Q7.** A LOADER performs which function?
(A) Translates assembly language to machine code
(B) Combines object files into executable
(C) Loads the executable into memory and starts execution
(D) More than one of the above
(E) None of the above

---

**Q8.** Assembly language is classified as:
(A) A high-level programming language
(B) A fourth-generation language
(C) A low-level programming language
(D) More than one of the above
(E) None of the above

---

**Q9.** PASCAL programming language is best known for being used to write:
(A) Scientific and engineering calculations
(B) Business data processing applications
(C) Structured code (enforces clean program structure)
(D) More than one of the above
(E) None of the above

---

**Q10.** FORTRAN (Formula Translation) programming language is primarily used for:
(A) Teaching beginners how to program
(B) Scientific and engineering computing
(C) Business data processing
(D) More than one of the above
(E) None of the above

---

**Q11.** COBOL (Common Business-Oriented Language) was designed for:
(A) Scientific and mathematical computations
(B) Teaching programming to beginners
(C) Business data processing
(D) More than one of the above
(E) None of the above

---

**Q12.** BASIC (Beginners' All-purpose Symbolic Instruction Code) was designed for:
(A) Scientific and engineering problems
(B) Structured programming with strict data types
(C) Teaching programming to beginners
(D) More than one of the above
(E) None of the above

---

**Q13.** OPEN SOURCE software is defined as software whose source code is available to:
(A) View only (read-only access)
(B) View and use, but not redistribute
(C) View, modify, AND redistribute
(D) More than one of the above
(E) None of the above

---

**Q14.** TIME SHARING in computing is historically significant because it:
(A) Introduced batch processing of jobs
(B) Allowed only one user to use the computer at any time
(C) Marked the beginning of COMPUTER COMMUNICATIONS
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following is NOT a component of a TURING MACHINE?
(A) Tape with read/write head
(B) State register
(C) Output tape (separate from input tape)
(D) More than one of the above
(E) None of the above

---

**Q16.** The HALTING PROBLEM in computer science is:
(A) Solvable using a fast enough computer
(B) Solvable using parallel processing
(C) Undecidable — provably cannot be solved by any algorithm
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following is NOT a valid type of interrupt?
(A) Hardware interrupt
(B) Software interrupt
(C) Memory interrupt
(D) More than one of the above
(E) None of the above

---

**Q18.** A thread shares which of the following with other threads of the SAME PROCESS?
(A) Its own private stack
(B) Its own set of registers
(C) Code section and data section
(D) More than one of the above
(E) None of the above

---

**Q19.** For a page size of 4KB in virtual memory, how many bits are needed for the PAGE OFFSET?
(A) 8 bits
(B) 10 bits
(C) 12 bits
(D) More than one of the above
(E) None of the above

---

**Q20.** TLB (Translation Lookaside Buffer) is organised as:
(A) A sequential list sorted by virtual address
(B) A direct-mapped cache
(C) An associative cache
(D) More than one of the above
(E) None of the above

---

**Q21.** THRASHING in operating systems is caused by:
(A) A virus attack on the CPU
(B) Too many open applications in the GUI
(C) Excessive paging activity (insufficient RAM for active processes)
(D) More than one of the above
(E) None of the above

---

**Q22.** The CONTROL UNIT of a CPU generates:
(A) Arithmetic results for calculations
(B) Clock pulses for timing
(C) Control signals to coordinate all CPU operations
(D) More than one of the above
(E) None of the above

---

**Q23.** When the instruction itself contains the operand value, which addressing mode is used?
(A) Direct addressing
(B) Indirect addressing
(C) Immediate addressing
(D) More than one of the above
(E) None of the above

---

**Q24.** The ASCII standard defines the mapping between:
(A) Binary numbers and memory addresses
(B) Keystrokes / characters and their binary bit patterns
(C) Network packets and IP addresses
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following correctly matches languages with their purpose?
(A) PASCAL → structured code | FORTRAN → scientific | COBOL → business | BASIC → beginners
(B) PASCAL → scientific | FORTRAN → structured | COBOL → beginners | BASIC → business
(C) PASCAL → business | FORTRAN → beginners | COBOL → scientific | BASIC → structured
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### India & Bihar Geography

---

**Q26.** Bihar's share of India's total population is approximately:
(A) 5.8%
(B) 8.58%
(C) 12.5%
(D) More than one of the above
(E) None of the above

---

**Q27.** Which district of Bihar has the MAXIMUM paddy (rice) production?
(A) Patna
(B) Muzaffarpur
(C) Rohtas
(D) More than one of the above
(E) None of the above

---

**Q28.** Bihar's "Silk City" — the district with maximum silk production — is:
(A) Gaya
(B) Darbhanga
(C) Bhagalpur
(D) More than one of the above
(E) None of the above

---

**Q29.** The river known as the "SORROW OF BIHAR" is:
(A) Ganga
(B) Son
(C) Koshi (Kosi)
(D) More than one of the above
(E) None of the above

---

**Q30.** The HIGHEST PEAK of the EASTERN GHATS is:
(A) Anamudi
(B) Doddabetta
(C) Mahendragiri
(D) More than one of the above
(E) None of the above

---

**Q31.** The South Peninsular Upland (Deccan Plateau) is considered part of:
(A) The Tethys Sea sedimentary deposits
(B) The Himalayan fold mountains
(C) Gondwana Land (ancient supercontinent)
(D) More than one of the above
(E) None of the above

---

**Q32.** The MALNAD region refers to the Western Ghats hilly area of which state?
(A) Kerala
(B) Maharashtra
(C) Karnataka
(D) More than one of the above
(E) None of the above

---

**Q33.** BLACK SOIL (Regur soil) is found in which of the following states?
(A) Karnataka
(B) Gujarat
(C) Both Karnataka and Gujarat
(D) More than one of the above
(E) None of the above

---

**Q34.** The SOUTHWEST MONSOON withdraws from HYDERABAD around:
(A) September 1
(B) October 1
(C) November 1
(D) More than one of the above
(E) None of the above

---

**Q35.** According to TREWARTHA'S climate classification, India's climate is best described as:
(A) Tropical wet and dry
(B) Mediterranean
(C) Subtropical monsoon
(D) More than one of the above
(E) None of the above

---

**Q36.** STALACTITES and STALAGMITES found in limestone caves are formed by:
(A) Wind erosion
(B) Glacial deposits
(C) Underground water (chemical weathering of limestone)
(D) More than one of the above
(E) None of the above

---

**Q37.** The EAST-WEST CORRIDOR connects which two cities?
(A) Srinagar (J&K) and Kanyakumari (Tamil Nadu)
(B) Delhi and Mumbai
(C) Silchar (Assam) and Porbandar (Gujarat)
(D) More than one of the above
(E) None of the above

---

**Q38.** TOPOGRAPHICAL MAPS of India are published by:
(A) Geological Survey of India
(B) Census of India
(C) Survey of India (headquartered in Dehradun)
(D) More than one of the above
(E) None of the above

---

**Q39.** Which Indian state has the MAXIMUM URBANISATION (highest percentage of urban population)?
(A) Maharashtra
(B) Tamil Nadu
(C) Goa
(D) More than one of the above
(E) None of the above

---

**Q40.** The LARGEST RIVER ISLAND IN THE WORLD, Majuli, is located in:
(A) West Bengal (in the Ganga river)
(B) Bihar (in the Ganga river)
(C) Assam (in the Brahmaputra river)
(D) More than one of the above
(E) None of the above

---

**Q41.** India's LARGEST STATE by area is:
(A) Madhya Pradesh
(B) Uttar Pradesh
(C) Rajasthan
(D) More than one of the above
(E) None of the above

---

**Q42.** The CHILIKA LAKE, India's largest saltwater lake, is located in:
(A) Andhra Pradesh
(B) West Bengal
(C) Odisha
(D) More than one of the above
(E) None of the above

---

**Q43.** Which of the following rivers flows WESTWARD (into the Arabian Sea)?
(A) Ganga
(B) Godavari
(C) Narmada
(D) More than one of the above
(E) None of the above

---

**Q44.** WULAR LAKE, India's largest freshwater lake, is located in:
(A) Punjab
(B) Himachal Pradesh
(C) Jammu & Kashmir
(D) More than one of the above
(E) None of the above

---

**Q45.** India shares its LONGEST land border with which country?
(A) China
(B) Pakistan
(C) Bangladesh
(D) More than one of the above
(E) None of the above

---

**Q46.** The NATHU LA pass connects India (Sikkim) to:
(A) Nepal
(B) Tibet (China)
(C) Bhutan
(D) More than one of the above
(E) None of the above

---

**Q47.** ALLUVIAL SOIL covers approximately what percentage of India's total area?
(A) 20%
(B) 40%
(C) 60%
(D) More than one of the above
(E) None of the above

---

**Q48.** Muzaffarpur district of Bihar is most famous for production of:
(A) Silk
(B) Paddy (rice)
(C) Litchi
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following statements about KHADAR and BANGAR soils is TRUE?
(A) Khadar = old alluvial soil far from rivers; Bangar = new alluvial near rivers
(B) Khadar = new alluvial soil deposited near rivers; Bangar = old alluvial soil
(C) Both are types of red soil
(D) More than one of the above
(E) None of the above

---

**Q50.** The SUNDARBANS delta, the world's largest delta, is formed by which rivers?
(A) Narmada and Tapi
(B) Godavari and Krishna
(C) Ganga and Brahmaputra
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ Attempt all 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (C) | Compiler input = source program |
| 2 | (C) | Compiler output = object code |
| 3 | (D) | All 3 statements are correct → D ← TRE 1.0 Q44 exact pattern |
| 4 | (B) | Interpreter = line by line translation + execution |
| 5 | (C) | Assembler = assembly language → machine code |
| 6 | (C) | Linker = combines object files → executable |
| 7 | (C) | Loader = loads executable into memory |
| 8 | (C) | Assembly language = LOW-LEVEL |
| 9 | (C) | PASCAL = structured code |
| 10 | (B) | FORTRAN = scientific and engineering computing |
| 11 | (C) | COBOL = business data processing |
| 12 | (C) | BASIC = beginners' programming |
| 13 | (C) | Open source = view + modify + redistribute (all three) |
| 14 | (C) | Time sharing = beginning of computer communications |
| 15 | (C) | "Output tape" does NOT exist in Turing machine |
| 16 | (C) | Halting problem = undecidable |
| 17 | (C) | "Memory interrupt" = NOT a valid interrupt type |
| 18 | (C) | Thread shares code section + data section |
| 19 | (C) | 4KB = 2¹² → 12 bits for page offset |
| 20 | (C) | TLB = organised as associative cache |
| 21 | (C) | Thrashing = excessive paging activity |
| 22 | (C) | Control unit generates control signals |
| 23 | (C) | Operand in instruction = immediate addressing |
| 24 | (B) | ASCII = keystrokes/characters → binary patterns |
| 25 | (A) | Pascal→structured; Fortran→scientific; COBOL→business; BASIC→beginners |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Bihar = 8.58% of India's population |
| 27 | (C) | Rohtas = max paddy in Bihar |
| 28 | (C) | Bhagalpur = Silk City of Bihar |
| 29 | (C) | Koshi = Sorrow of Bihar |
| 30 | (C) | Mahendragiri = highest peak of Eastern Ghats |
| 31 | (C) | South Peninsular Upland = Gondwana Land |
| 32 | (C) | Malnad = Karnataka (Western Ghats region) |
| 33 | (D) | Black soil = both Karnataka AND Gujarat → D |
| 34 | (B) | SW monsoon withdrawal from Hyderabad = October 1 |
| 35 | (C) | Trewartha: India = subtropical monsoon |
| 36 | (C) | Stalactites/Stalagmites = underground water |
| 37 | (C) | East-West Corridor = Silchar (Assam) to Porbandar (Gujarat) |
| 38 | (C) | Topographic maps = Survey of India (Dehradun) |
| 39 | (C) | Maximum urbanisation = GOA |
| 40 | (C) | Majuli = Assam, in Brahmaputra river |
| 41 | (C) | Largest state by area = RAJASTHAN |
| 42 | (C) | Chilika Lake = Odisha (largest saltwater lake) |
| 43 | (C) | Narmada = westward flow (Arabian Sea) |
| 44 | (C) | Wular Lake = Jammu & Kashmir |
| 45 | (C) | Longest land border = Bangladesh (4,156 km) |
| 46 | (B) | Nathu La = connects Sikkim to Tibet (China) |
| 47 | (B) | Alluvial soil = ~40% of India's area |
| 48 | (C) | Muzaffarpur = litchi capital of Bihar |
| 49 | (B) | Khadar = new alluvial (near rivers); Bangar = old alluvial |
| 50 | (C) | Sundarbans delta = Ganga + Brahmaputra |

---
---

# 🔁 DAY 55 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Compiler Theory + Languages + OS

```
COMPILER:
  Input = SOURCE PROGRAM | Output = OBJECT CODE | NOT involved in execution
  TRE 1.0 Q44: All 3 statements correct → Answer = D

TRANSLATORS IN ORDER:
  Source code → COMPILER → Object code → LINKER → Executable → LOADER → Running in RAM
  INTERPRETER = line by line (no object file; stops at first error)
  ASSEMBLER = assembly language → machine code

LANGUAGE PURPOSES:
  PASCAL   = STRUCTURED code ← most tested
  FORTRAN  = SCIENTIFIC + engineering
  COBOL    = BUSINESS data processing
  BASIC    = BEGINNERS
  C        = system programming | C++ = OOP | Java = platform-independent

OPEN SOURCE = VIEW + MODIFY + REDISTRIBUTE (all three)

OS:
  Time sharing = beginning of COMPUTER COMMUNICATIONS
  Turing machine: "output tape" does NOT exist ← wrong option
  Halting problem = UNDECIDABLE
  "Memory interrupt" = NOT a valid type (Hardware/Software/Trap are valid)
  Thread shares: CODE SECTION + DATA SECTION (same process)
  4KB page offset = 12 bits (2¹² = 4096)
  TLB = ASSOCIATIVE CACHE
  Thrashing = excessive PAGING ACTIVITY
  Control unit generates = CONTROL SIGNALS
  Immediate addressing = operand IS in the instruction
  ASCII = keystrokes → binary
```

---

## ⚡ RAPID FIRE — India & Bihar Geography

```
BIHAR:
  Population % of India = 8.58%
  Max paddy = ROHTAS | Max silk = BHAGALPUR (Silk City; Tussar silk)
  Sorrow of Bihar = KOSHI river | Famous litchi = MUZAFFARPUR

INDIA PHYSICAL:
  Eastern Ghats highest = MAHENDRAGIRI (Odisha)
  Western Ghats highest = ANAMUDI (Kerala)
  South Peninsular Upland = GONDWANA LAND
  Malnad = KARNATAKA (Western Ghats region)
  Black soil = KARNATAKA + GUJARAT (Answer D — both!)
  
CLIMATE:
  SW monsoon withdrawal at Hyderabad = OCTOBER 1
  Trewartha's India = SUBTROPICAL MONSOON
  Tamil Nadu gets rain from NE monsoon (not SW)

GEOMORPHOLOGY:
  Stalactites/Stalagmites = formed by UNDERGROUND WATER
  Stalactite = from ceiling | Stalagmite = from floor

TRANSPORT + MAPS:
  East-West Corridor = SILCHAR (Assam) ↔ PORBANDAR (Gujarat)
  Topographic maps = SURVEY OF INDIA (Dehradun)
  Max urbanisation state = GOA

INDIA FIRSTS:
  Largest state (area) = RAJASTHAN
  Largest saltwater lake = CHILIKA (Odisha)
  Largest freshwater lake = WULAR (J&K)
  Largest river island = MAJULI (Assam, Brahmaputra)
  Longest land border = BANGLADESH
  Largest delta = SUNDARBANS (Ganga + Brahmaputra)
  Alluvial soil = 40% of India
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Compiler: input=**source program**, output=**object code**, NOT involved in execution — **all 3 correct → Answer D** (TRE 1.0 Q44)
2. **PASCAL=structured, FORTRAN=scientific, COBOL=business, BASIC=beginners** — these four always distract each other
3. Open source = **view + modify + redistribute** (all three); Time sharing = beginning of **computer communications**
4. Bihar: Max paddy=**Rohtas**, Max silk=**Bhagalpur**, **8.58%** of India's population, Sorrow of Bihar=**Koshi**
5. Eastern Ghats highest=**Mahendragiri**; Black soil=**Karnataka+Gujarat (Answer D)**; E-W Corridor=**Silchar↔Porbandar**; Topographic maps=**Survey of India**

---

*Next: Day 56 — MEGA REVISION DAY: Phase 1 Summary (Days 1–55) + Full Mock Test*
