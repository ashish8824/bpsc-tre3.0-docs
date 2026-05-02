# 📅 BPSC TRE 4.0 — DAY 84: THEORY OF COMPUTATION + LOW-LEVEL LANGUAGES + GS REVISION
### Week 13 — AI, IoT, Emerging Tech & Theory of Computation
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — Turing Machine, Halting Problem, Finite Automata, Languages
> - Afternoon (1 hr): GS — Mixed Revision (Maths + History + Science PYQ shortcuts)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 Theory of Computation + Low-Level Languages — All Concepts, One Place

---

## 🔷 TOPIC 1: What is Theory of Computation?

```
THEORY OF COMPUTATION (TOC)
════════════════════════════════════════════════════════

= The study of WHAT PROBLEMS can be solved by a computer,
  HOW EFFICIENTLY they can be solved, and WHAT MODELS
  of computation exist

THREE MAIN BRANCHES:
  ┌────────────────────────────────────────────────────────┐
  │ 1. AUTOMATA THEORY                                     │
  │    → Studies abstract computational machines           │
  │    → Finite Automata (DFA, NFA), Pushdown Automata,   │
  │      Turing Machines                                   │
  ├────────────────────────────────────────────────────────┤
  │ 2. FORMAL LANGUAGE THEORY                              │
  │    → Studies classes of languages (Regular,            │
  │      Context-Free, Context-Sensitive, Recursively      │
  │      Enumerable)                                       │
  │    → Chomsky Hierarchy                                 │
  ├────────────────────────────────────────────────────────┤
  │ 3. COMPUTABILITY THEORY                                │
  │    → Studies which problems CAN or CANNOT be solved    │
  │    → Decidable vs Undecidable problems                 │
  │    → Halting Problem                                   │
  └────────────────────────────────────────────────────────┘

WHY STUDY TOC?
  → Understand fundamental LIMITS of computers
  → Design compilers and interpreters
  → Understand what is "computable"
```

---

## 🔷 TOPIC 2: Chomsky Hierarchy — Language Classification

### The Four Types of Languages:
```
CHOMSKY HIERARCHY — Language Classification
════════════════════════════════════════════════════════

Noam Chomsky classified ALL formal languages into 4 types.
Think of it as NESTED BOXES — each inner type is a subset of outer:

  ┌──────────────────────────────────────────────────────────┐
  │  TYPE 0: RECURSIVELY ENUMERABLE LANGUAGES                │
  │  (Most powerful — accepted by Turing Machine)            │
  │                                                          │
  │   ┌──────────────────────────────────────────────────┐  │
  │   │  TYPE 1: CONTEXT-SENSITIVE LANGUAGES             │  │
  │   │  (Accepted by Linear Bounded Automaton)          │  │
  │   │                                                  │  │
  │   │   ┌──────────────────────────────────────────┐  │  │
  │   │   │  TYPE 2: CONTEXT-FREE LANGUAGES (CFL)    │  │  │
  │   │   │  (Accepted by Pushdown Automaton — PDA)  │  │  │
  │   │   │                                          │  │  │
  │   │   │   ┌──────────────────────────────────┐  │  │  │
  │   │   │   │  TYPE 3: REGULAR LANGUAGES        │  │  │  │
  │   │   │   │  (Accepted by Finite Automaton    │  │  │  │
  │   │   │   │   — DFA or NFA)                   │  │  │  │
  │   │   │   │  (Most RESTRICTED / Simplest)     │  │  │  │
  │   │   │   └──────────────────────────────────┘  │  │  │
  │   │   └──────────────────────────────────────────┘  │  │
  │   └──────────────────────────────────────────────────┘  │
  └──────────────────────────────────────────────────────────┘

TYPE  NAME                  GRAMMAR     AUTOMATON           EXAMPLE LANGUAGE
────────────────────────────────────────────────────────────────────────────
3     Regular               Regular     Finite Automaton    a*b* , (ab)*
                            Grammar     (DFA / NFA)         Email patterns
2     Context-Free          CFG         Pushdown Automaton  aⁿbⁿ (n≥1)
                                        (PDA)               Programming lang
                                                            syntax
1     Context-Sensitive     CSG         Linear Bounded      aⁿbⁿcⁿ (n≥1)
                                        Automaton (LBA)
0     Recursively           Unrestricted Turing Machine     ANY computable
      Enumerable            Grammar                         language
────────────────────────────────────────────────────────────────────────────

MEMORY TRICK — "Real Computers Process Tasks":
  Regular → Context-Free → Context-Sensitive → Recursively Enumerable
  (from MOST restricted to LEAST restricted)
  (from SIMPLEST to MOST POWERFUL)

PYQ FACTS:
  "Regular languages accepted by Finite Automata (DFA/NFA)" = TRUE ✅
  "Context-Free languages accepted by Pushdown Automaton" = TRUE ✅
  "Most powerful grammar = Unrestricted (Type 0)" = TRUE ✅
  "Programming language syntax = Context-Free Grammar" ← important!
```

---

## 🔷 TOPIC 3: Finite Automata — DFA and NFA

### What is Finite Automaton?
```
FINITE AUTOMATON (FA)
════════════════════════════════════════════════════════

DEFINITION:
  = An abstract machine that:
    → Has a FINITE number of STATES
    → Reads an INPUT STRING symbol by symbol
    → Changes state based on current state + input symbol
    → ACCEPTS or REJECTS the string at the end

COMPONENTS (5-tuple): M = (Q, Σ, δ, q₀, F)
  Q  = Finite set of STATES
  Σ  = ALPHABET (set of input symbols)
  δ  = TRANSITION FUNCTION (current state + input → next state)
  q₀ = INITIAL/START STATE (where we begin)
  F  = Set of FINAL/ACCEPTING STATES

SIMPLE EXAMPLE — DFA accepting strings ending in 'b':
  Alphabet Σ = {a, b}

  STATE DIAGRAM:
  
       a                    b
   ┌───────┐           ┌───────────────┐
   │       │           │               │
   ▼   a   │     b     ▼       a       │
  →[q₀]───────────►((q₁))───────►[q₀]
   START              ACCEPT
   (not ended in b)   (ended in b!)

  States: q₀ = "last symbol was NOT b" (or start)
          q₁ = "last symbol WAS b" ← ACCEPT STATE (double circle)

  Reading "aab":
    Start at q₀
    Read 'a' → stay q₀ (transition: q₀ on a → q₀)
    Read 'a' → stay q₀
    Read 'b' → go to q₁ (transition: q₀ on b → q₁)
    End at q₁ = ACCEPT STATE → STRING ACCEPTED ✅

  Reading "aba":
    Start at q₀
    Read 'a' → stay q₀
    Read 'b' → go to q₁
    Read 'a' → go back to q₀
    End at q₀ = NOT ACCEPT STATE → STRING REJECTED ❌
```

### DFA vs NFA:
```
DFA vs NFA — Key Differences
════════════════════════════════════════════════════════

              DFA                        NFA
              (Deterministic FA)         (Non-deterministic FA)
──────────────────────────────────────────────────────────────────
Transitions   EXACTLY ONE transition     CAN have MULTIPLE
              for each (state, input)    transitions for same
              combination                (state, input) — OR ZERO
──────────────────────────────────────────────────────────────────
ε-transitions NOT ALLOWED                ALLOWED (move without
              (no empty transitions)     reading any input)
──────────────────────────────────────────────────────────────────
Acceptance    One path; deterministic    ACCEPTS if ANY path
                                         leads to accept state
──────────────────────────────────────────────────────────────────
Implementation Easier to implement       Harder to implement
               (directly usable)         (needs conversion)
──────────────────────────────────────────────────────────────────
Power         SAME power as NFA          SAME power as DFA
              (both accept Regular       ← IMPORTANT!
               Languages only!)
──────────────────────────────────────────────────────────────────

PYQ KEY FACT: "DFA and NFA have EQUAL computational power"
              Both accept EXACTLY the Regular Languages ← tested!
              "NFA is more powerful than DFA" → FALSE
              Every NFA can be converted to an equivalent DFA!

DIAGRAM — DFA vs NFA on same input:

DFA: Each state has exactly 1 arrow per input symbol
  [q0] --a--> [q1] --b--> [q2]   (one path only)

NFA: State can have 0, 1, or multiple arrows per input symbol
  [q0] --a--> [q1]
         \--a--> [q2]    (two transitions on 'a' from q0 — allowed!)
```

---

## 🔷 TOPIC 4: Pushdown Automaton (PDA)

```
PUSHDOWN AUTOMATON (PDA)
════════════════════════════════════════════════════════

= A Finite Automaton WITH a STACK (extra memory)
= Recognizes CONTEXT-FREE LANGUAGES (Type 2)
= More powerful than DFA/NFA (which have no stack)

DIAGRAM:
  ┌─────────────────────────────────────────────────────┐
  │                  PDA                                │
  │                                                     │
  │  INPUT TAPE:  a  a  b  b  (reading left to right)  │
  │               ↑                                     │
  │          READ HEAD                                  │
  │               │                                     │
  │         ┌─────┴──────┐                             │
  │         │   FINITE   │                             │
  │         │  CONTROL   │◄──────── States (q0,q1...)  │
  │         │ (like DFA) │                             │
  │         └─────┬──────┘                             │
  │               │ push/pop                           │
  │               ▼                                    │
  │            ┌─────┐                                 │
  │            │  S  │ ← TOP of stack                  │
  │            ├─────┤                                 │
  │            │  A  │                                 │
  │            ├─────┤                                 │
  │            │  A  │                                 │
  │            └─────┘ STACK (infinite memory)         │
  └─────────────────────────────────────────────────────┘

WHY PDA CAN RECOGNIZE aⁿbⁿ (but DFA CANNOT):
  Language: {ab, aabb, aaabbb, ...} — equal number of a's and b's

  PDA STRATEGY:
    → READ each 'a' → PUSH 'A' onto stack
    → READ each 'b' → POP 'A' from stack
    → If stack EMPTY when all input read → ACCEPT
    → If stack not empty or pops from empty → REJECT

  DFA CANNOT do this because:
    DFA has NO MEMORY (no stack) to COUNT how many a's were read!
    DFA has only FINITE states → cannot count infinitely

PYQ FACT: "PDA = FA + Stack" ← clean definition to remember!
          "PDA recognizes Context-Free Languages" = TRUE ✅
```

---

## 🔷 TOPIC 5: Turing Machine — The Most Important Machine

### What is a Turing Machine?
```
TURING MACHINE (TM)
════════════════════════════════════════════════════════

= Proposed by ALAN TURING (1936) ← inventor's name is PYQ!
= A theoretical computing machine that is the
  MOST POWERFUL model of computation
= Can simulate ANY algorithm that any computer can run
= Accepts RECURSIVELY ENUMERABLE LANGUAGES (Type 0)

COMPONENTS OF TURING MACHINE:
════════════════════════════════════════════════════════

  ┌─────────────────────────────────────────────────────────────────┐
  │                     TURING MACHINE                              │
  │                                                                 │
  │  INFINITE TAPE:                                                 │
  │  ┌───┬───┬───┬───┬───┬───┬───┬───┬───┬───┐                    │
  │  │ B │ a │ a │ b │ b │ B │ B │ B │ B │...│  (B = blank)       │
  │  └───┴───┴───┴───┴───┴───┴───┴───┴───┴───┘                    │
  │            ↑                                                    │
  │      READ/WRITE HEAD                                           │
  │      (can move LEFT or RIGHT, can READ and WRITE)              │
  │            │                                                    │
  │     ┌──────┴───────┐                                           │
  │     │    FINITE    │ ←── STATE REGISTER (current state)        │
  │     │    CONTROL   │                                           │
  │     │ (set of states│                                          │
  │     │  + transitions│                                          │
  │     └──────────────┘                                           │
  └─────────────────────────────────────────────────────────────────┘

COMPONENTS (7-tuple): M = (Q, Σ, Γ, δ, q₀, B, F)
  Q  = Finite set of STATES
  Σ  = INPUT ALPHABET (symbols in input)
  Γ  = TAPE ALPHABET (all symbols on tape; Σ ⊆ Γ)
  δ  = TRANSITION FUNCTION
  q₀ = START STATE
  B  = BLANK SYMBOL (on empty tape cells)
  F  = SET OF FINAL/ACCEPTING STATES

KEY DIFFERENCE FROM DFA/PDA:
  → TM has INFINITE TAPE (unlimited memory)
  → Read/Write head can move BOTH LEFT and RIGHT
  → Can WRITE on the tape (DFA/PDA only read)
  → Can do infinitely complex computations
```

### Turing Machine — PYQ Critical Facts:
```
TURING MACHINE — WHAT IT HAS vs WHAT IT DOES NOT HAVE
════════════════════════════════════════════════════════

WHAT A TURING MACHINE HAS: ✅
  ✅ INFINITE TAPE (for reading, writing, storage)
  ✅ READ/WRITE HEAD (can both read and write on tape)
  ✅ STATE REGISTER (stores current state)
  ✅ TRANSITION FUNCTION δ (rules for movement)
  ✅ BLANK SYMBOL B (marks empty cells)
  ✅ Can move head LEFT and RIGHT

WHAT A TURING MACHINE DOES NOT HAVE: ❌
  ❌ SEPARATE OUTPUT TAPE ← PYQ TRAP! ← MOST TESTED!
     The TM uses the SAME tape for input, working, and output
     There is NO separate "output tape"

  ❌ RANDOM ACCESS MEMORY (RAM) — it has a tape, not RAM
  ❌ Multiple heads by default (standard TM has ONE head)

PYQ FACT: "Turing Machine does NOT have an output tape" ← TESTED!
          "Turing Machine has a separate output tape" → FALSE ← TRAP!

HOW TM WORKS (transition):
  δ(current_state, tape_symbol) = (new_state, write_symbol, direction)

  Example: δ(q0, a) = (q1, X, R)
  Meaning: In state q0, reading 'a' →
           → Go to state q1
           → WRITE 'X' on tape (replacing 'a')
           → Move head RIGHT

TM ACCEPTS a string if it reaches a FINAL STATE (halts in accept)
TM REJECTS if it halts in a non-final state OR loops forever
```

---

## 🔷 TOPIC 6: Halting Problem — Undecidable! ← PYQ STAR

```
HALTING PROBLEM
════════════════════════════════════════════════════════

THE QUESTION:
  "Given any program P and any input I, will P HALT
   (terminate/stop) when run on I, or will it run FOREVER?"

ALAN TURING'S ANSWER (1936):
  = The Halting Problem is UNDECIDABLE
  = There is NO ALGORITHM that can always correctly determine
    whether an arbitrary program will halt or loop forever

WHAT "UNDECIDABLE" MEANS:
  ┌────────────────────────────────────────────────────────┐
  │ DECIDABLE problem:                                     │
  │   → There EXISTS an algorithm that always gives        │
  │     YES or NO answer in finite time                    │
  │   → Example: "Is this number even?" = DECIDABLE        │
  │              (always finishes with yes/no answer)      │
  ├────────────────────────────────────────────────────────┤
  │ UNDECIDABLE problem:                                   │
  │   → NO algorithm can always give a correct YES/NO      │
  │     answer for ALL inputs in finite time               │
  │   → The Halting Problem = UNDECIDABLE                  │
  │   → Some inputs might work, but NO GENERAL algorithm   │
  │     works for ALL programs                             │
  └────────────────────────────────────────────────────────┘

PROOF IDEA (Diagonalization — simplified):
  Assume a magic program HALT(P, I) exists that solves it.
  
  Build a PARADOX program:
  PARADOX(P):
    if HALT(P, P) says "halts"  → LOOP FOREVER
    if HALT(P, P) says "loops"  → HALT immediately
  
  Now run PARADOX(PARADOX):
    If HALT says "halts"  → PARADOX loops → CONTRADICTION!
    If HALT says "loops"  → PARADOX halts → CONTRADICTION!
  
  → CONTRADICTION proves no such HALT program can exist!
  → Therefore: HALTING PROBLEM IS UNDECIDABLE ✅

IS IT NP? NO!
  NP = class of problems solvable in Nondeterministic Polynomial time
  Undecidable = NOT SOLVABLE AT ALL (worse than NP!)
  
  HIERARCHY:
  P ⊆ NP ⊆ PSPACE ⊆ ... ⊆ Decidable ⊆ Undecidable
  (Halting Problem is OUTSIDE the decidable category entirely)

PYQ FACTS:
  "Halting Problem = UNDECIDABLE" ← TESTED! ← #1 fact to remember
  "Halting Problem = NP problem" → FALSE ← common trap!
  "Halting Problem is solvable by some algorithm" → FALSE
  "Halting Problem proved by Alan Turing (1936)" = TRUE ✅

PRACTICAL IMPACT:
  → Antivirus software CANNOT perfectly detect all viruses
    (proving a program is malicious is undecidable in general)
  → IDEs cannot perfectly tell you if your program has infinite loop
  → We use HEURISTICS (best guesses) instead of perfect algorithms
```

---

## 🔷 TOPIC 7: Decidable vs Undecidable Problems

```
DECIDABLE vs UNDECIDABLE — EXAMPLES TABLE
════════════════════════════════════════════════════════

DECIDABLE (algorithm always gives YES/NO):
  ┌──────────────────────────────────────────────────────┐
  │ Problem                      │ Why Decidable?        │
  ├──────────────────────────────┼───────────────────────┤
  │ Is string in Regular Lang?   │ Run DFA; always halts │
  │ Is string in CFL?            │ Run CYK algorithm     │
  │ Is this integer prime?       │ Trial division works  │
  │ Does DFA accept empty lang?  │ Check reachability    │
  │ Are two DFAs equivalent?     │ Intersection/complement│
  └──────────────────────────────┴───────────────────────┘

UNDECIDABLE (no algorithm can always solve):
  ┌──────────────────────────────────────────────────────┐
  │ Problem                      │ Notes                 │
  ├──────────────────────────────┼───────────────────────┤
  │ HALTING PROBLEM ← #1 PYQ!   │ Proved by Turing 1936 │
  │ Does TM accept all strings?  │ Undecidable           │
  │ Are two TMs equivalent?      │ Undecidable           │
  │ Post Correspondence Problem  │ Classic undecidable   │
  │ Does CFG generate all strings│ Undecidable           │
  └──────────────────────────────┴───────────────────────┘

PYQ CLASSIFICATION TRAP:
  "Is a problem being undecidable same as being NP-hard?" → NO!
  Undecidable = cannot be solved at all
  NP-hard     = hard but may be solvable (just slow)
  
  Halting Problem = Undecidable (NOT NP, NOT NP-hard)
```

---

## 🔷 TOPIC 8: Low-Level Languages ← PYQ

### Machine Language:
```
MACHINE LANGUAGE (1st Generation Language / 1GL)
════════════════════════════════════════════════════════

DEFINITION:
  = The LOWEST LEVEL programming language
  = Uses BINARY CODE (0s and 1s) DIRECTLY
  = The ONLY language a computer's CPU understands DIRECTLY

EXAMPLE:
  Human wants: Add two numbers
  Machine language: 10110000 01100001 (binary instruction)

CHARACTERISTICS (ALL PYQ-TESTED — answer is D for all three!):
  ┌────────────────────────────────────────────────────────┐
  │ 1. MACHINE DEPENDENT                                   │
  │    → Programs written for one CPU (e.g., Intel x86)   │
  │      will NOT run on another CPU (e.g., ARM)           │
  │    → Cannot be transferred between different hardware  │
  ├────────────────────────────────────────────────────────┤
  │ 2. DIFFICULT TO PROGRAM                                │
  │    → Programmer must write in binary/hex               │
  │    → Extremely tedious and error-prone                 │
  │    → Very hard to understand and maintain              │
  ├────────────────────────────────────────────────────────┤
  │ 3. ERROR PRONE                                         │
  │    → Easy to make mistakes with binary digits          │
  │    → Very hard to debug (find errors)                  │
  │    → No error checking tools available                 │
  └────────────────────────────────────────────────────────┘

PYQ MEGA FACT:
  "Machine language is machine-dependent AND difficult to program
   AND error-prone" → ALL THREE → ANSWER = (D) ← TESTED IN BPSC TRE!

ADVANTAGES (few):
  → Fastest execution (CPU executes directly, no translation)
  → No translation overhead
  → Full hardware control
```

### Assembly Language:
```
ASSEMBLY LANGUAGE (2nd Generation Language / 2GL)
════════════════════════════════════════════════════════

DEFINITION:
  = LOW-LEVEL programming language that uses
    MNEMONICS (short readable codes) instead of binary
  = Each mnemonic corresponds to ONE machine instruction
  = Translated to machine code by an ASSEMBLER

EXAMPLE:
  Assembly:  MOV AX, 5    (Move value 5 into register AX)
             ADD AX, BX   (Add BX to AX)
             MOV [100], AX (Store AX in memory address 100)

  vs Machine: 10111000 00000101
              00000011 11000011

ASSEMBLY LANGUAGE CHARACTERISTICS:
  ✅ LOW-LEVEL language (like machine language, close to hardware)
  ✅ Uses MNEMONICS (MOV, ADD, SUB, JMP, CMP, PUSH, POP)
  ✅ Still MACHINE DEPENDENT (different CPUs have different mnemonics)
  ✅ Translated by ASSEMBLER (not compiler, not interpreter)
  ✅ Faster than high-level languages (but slower than machine code)
  ✅ Used for: Device drivers, OS kernel, embedded systems

COMMON MNEMONICS:
  MOV = Move data between registers/memory
  ADD = Addition
  SUB = Subtraction
  MUL = Multiplication
  DIV = Division
  JMP = Jump (unconditional goto)
  CMP = Compare two values
  PUSH= Push value onto stack
  POP = Pop value from stack
  INT = Interrupt

PYQ FACT: "Assembly language = LOW-LEVEL language" ← tested!
          "Assembly language uses mnemonics" = TRUE ✅
          "Assembly is translated by ASSEMBLER" ← tested!
          (NOT by compiler — assembler is the correct term)
```

### Language Generation Comparison:
```
PROGRAMMING LANGUAGE GENERATIONS — COMPARISON
════════════════════════════════════════════════════════

GEN  NAME              EXAMPLE          TRANSLATOR    LEVEL
─────────────────────────────────────────────────────────────────
1GL  Machine Language  10110000 01100001 None needed   Lowest
                       (pure binary)    (CPU directly  (hardest
                                         executes)      for humans)
─────────────────────────────────────────────────────────────────
2GL  Assembly Language MOV AX, 5        ASSEMBLER      Low
                       ADD BX, CX       (translates    (still
                       (mnemonics)      mnemonics to   hardware-
                                        binary)        close)
─────────────────────────────────────────────────────────────────
3GL  High-Level        C, C++, Java,    COMPILER or    High
     Languages         Python, COBOL    INTERPRETER    (human-
                       (English-like                   readable)
                        syntax)
─────────────────────────────────────────────────────────────────
4GL  Very High-Level   SQL, MATLAB,     Built-in       Very High
     Languages         R, SAS           engine         (domain
                       (domain-                        specific)
                        specific)
─────────────────────────────────────────────────────────────────
5GL  AI/Logic-based    Prolog, LISP,    AI engine      Highest
     Languages         OPS5             (logic-based)  (closest to
                       (constraint-                    natural
                        based)                         language)
─────────────────────────────────────────────────────────────────

TRANSLATOR TYPES:
  Assembler   = translates ASSEMBLY → MACHINE code ← PYQ!
  Compiler    = translates HIGH-LEVEL → MACHINE code (WHOLE program at once)
  Interpreter = translates HIGH-LEVEL → MACHINE code (LINE BY LINE)

PYQ FACTS:
  "Assembly language translator = ASSEMBLER" ← tested!
  "Compiler translates whole program at once" ← Day 54 PYQ!
  "Interpreter translates line by line" ← Day 54 PYQ!
```

---

## 🔷 TOPIC 9: Special Language Facts — PYQ Targeted

```
SPECIFIC LANGUAGE PYQ FACTS
════════════════════════════════════════════════════════

PASCAL:
  = Best language for writing STRUCTURED code ← PYQ!
  = Designed by Niklaus Wirth (1968–1970)
  = Strong typing; good for teaching structured programming
  = Used to teach programming fundamentals

FORTRAN:
  = FORmula TRANslation
  = FIRST high-level programming language ← PYQ!
  = Best for SCIENTIFIC and MATHEMATICAL computations ← PYQ!
  = Still used in meteorology, physics simulations

COBOL:
  = Common Business Oriented Language
  = Best for BUSINESS data processing ← PYQ!
  = Reads like English sentences
  = Still used in banking, finance systems

BASIC:
  = Beginner's All-purpose Symbolic Instruction Code
  = Best for BEGINNERS ← PYQ!
  = Simple, easy to learn

LISP:
  = List Processing language
  = Used in ARTIFICIAL INTELLIGENCE ← PYQ!
  = One of oldest AI languages

PROLOG:
  = PROgramming in LOGic
  = Logic programming language
  = Used in AI and expert systems ← PYQ!

QUICK REFERENCE TABLE:
  ┌───────────────────────────────────────────────────┐
  │ Language  │ Best Known For          │ PYQ Fact    │
  ├───────────┼─────────────────────────┼─────────────┤
  │ PASCAL    │ STRUCTURED code ← ★    │ Niklaus Wirth│
  │ FORTRAN   │ SCIENTIFIC computing ← ★│ FIRST HLL!  │
  │ COBOL     │ BUSINESS processing ← ★│ Reads like  │
  │           │                         │ English      │
  │ BASIC     │ BEGINNERS ← ★          │ Easy to learn│
  │ LISP      │ AI / List processing ← ★│ Old AI lang │
  │ PROLOG    │ Logic programming / AI  │ Expert sys  │
  │ C         │ System programming      │ Portable    │
  │ SQL       │ Database queries (4GL)  │ RDBMS       │
  └───────────┴─────────────────────────┴─────────────┘

PYQ TRAP: "FORTRAN = best for beginners" → FALSE (= BASIC)
          "BASIC = scientific computing" → FALSE (= FORTRAN)
          "PASCAL = AI language" → FALSE (= LISP/PROLOG)
          "COBOL = structured code" → FALSE (= PASCAL)
```

---

## 🔷 TOPIC 10: Compiler vs Interpreter vs Assembler

```
COMPILER vs INTERPRETER vs ASSEMBLER
════════════════════════════════════════════════════════

ASSEMBLER:
  Input:   Assembly language code (mnemonics)
  Output:  Machine code (binary)
  Method:  Translates ENTIRE assembly program
  Used by: Assembly language programs
  Speed:   Fast (direct mapping: 1 mnemonic = 1 machine instruction)

COMPILER:
  Input:   High-level language (C, C++, Java source code)
  Output:  Machine code or intermediate code
  Method:  Translates ENTIRE PROGRAM at ONCE before execution
  Used by: C, C++, FORTRAN, PASCAL
  Speed:   Faster execution (translated beforehand)
  Error:   Shows ALL errors after complete scan

INTERPRETER:
  Input:   High-level language code
  Output:  Executes each line immediately
  Method:  Translates and executes LINE BY LINE
  Used by: Python, JavaScript, BASIC, PHP
  Speed:   Slower (translates while running)
  Error:   Stops at FIRST error encountered

DIAGRAM:
  SOURCE CODE
      │
      ├──── ASSEMBLER ──────► machine code (from assembly)
      │
      ├──── COMPILER ───────► machine code (all at once)
      │                       then execute
      │
      └──── INTERPRETER ───► execute line by line
                             (no separate machine code file)

COMPARISON TABLE:
  Feature        │ Compiler        │ Interpreter
  ───────────────┼─────────────────┼─────────────────────
  Translation    │ Whole program   │ Line by line
  Speed          │ Faster execution│ Slower execution
  Error display  │ All errors at   │ Stops at first error
                 │ end of scan     │
  Output file    │ Creates object  │ No separate object
                 │ file (.exe)     │ file
  Examples       │ C, C++, FORTRAN │ Python, JS, BASIC

PYQ FACTS:
  "Compiler = whole program at once" ← tested (Day 54 + today)
  "Interpreter = line by line" ← tested
  "Assembler = translates assembly code" ← tested
  "Python uses interpreter" = TRUE
  "C uses compiler" = TRUE
```

---

## 🔷 TOPIC 11: Regular Expressions

```
REGULAR EXPRESSIONS — Quick Reference
════════════════════════════════════════════════════════

DEFINITION:
  = A formal notation to DESCRIBE REGULAR LANGUAGES
  = Pattern matching — defines a SET of strings

BASIC OPERATORS:
  ┌────────────────────────────────────────────────────────┐
  │ Operator │ Meaning              │ Example             │
  ├──────────┼──────────────────────┼─────────────────────┤
  │ *        │ Kleene Star          │ a* = {ε, a, aa, aaa}│
  │          │ Zero or more times   │ (ε = empty string)  │
  ├──────────┼──────────────────────┼─────────────────────┤
  │ +        │ One or more times    │ a+ = {a, aa, aaa}   │
  │          │ (at least once)      │ (no empty string!)  │
  ├──────────┼──────────────────────┼─────────────────────┤
  │ ?        │ Zero or one time     │ a? = {ε, a}         │
  │          │ (optional)           │                     │
  ├──────────┼──────────────────────┼─────────────────────┤
  │ |        │ OR / Union           │ a|b = {a, b}        │
  ├──────────┼──────────────────────┼─────────────────────┤
  │ .        │ Concatenation        │ ab = {ab} only      │
  ├──────────┼──────────────────────┼─────────────────────┤
  │ []       │ Character class      │ [ab] = a or b       │
  └──────────┴──────────────────────┴─────────────────────┘

EXAMPLES:
  (a|b)*    = all strings of a's and b's (including empty)
  a*b*      = zero or more a's followed by zero or more b's
  (ab)+     = "ab", "abab", "ababab", ...
  [0-9]+    = one or more digits

PYQ FACT: Regular Expressions describe REGULAR LANGUAGES
          Regular Expressions are equivalent to DFA/NFA in power
```

---

## 📊 CS MASTER COMPARISON TABLE — Day 84

```
CONCEPT               KEY FACT                              COMMON TRAP
──────────────────────────────────────────────────────────────────────────
Chomsky Type 3        REGULAR language; DFA/NFA accepts it  "FA accepts CFL"=FALSE
Chomsky Type 2        CONTEXT-FREE; PDA accepts it          "DFA accepts CFL"=FALSE
Chomsky Type 0        RECURSIVELY ENUMERABLE; TM accepts it Most powerful
DFA vs NFA            EQUAL power; both accept Regular Lang  "NFA > DFA"=FALSE
PDA                   FA + STACK; accepts CFL               "PDA = TM"=FALSE
Turing Machine        Alan Turing; most powerful; infinite  "TM has output tape"
                      tape; read/write head                  → FALSE ← PYQ trap!
TM components         Tape, R/W head, State register,        "Output tape exists"
                      Transition function                     = FALSE
Halting Problem       UNDECIDABLE ← PYQ!                    "Halting = NP"=FALSE
                      No algorithm can always solve it       "Halting = decidable"=FALSE
Machine Language      Machine-dependent + difficult +        "Machine lang = portable"
                      error-prone → ALL THREE → Answer D     = FALSE
Assembly Language     LOW-LEVEL; uses mnemonics;             "Assembly = compiled"
                      translated by ASSEMBLER                = FALSE (= assembled!)
PASCAL                Best for STRUCTURED code ← PYQ!       "PASCAL = AI"=FALSE
FORTRAN               SCIENTIFIC computing; FIRST HLL ← PYQ "FORTRAN = beginners"=FALSE
COBOL                 BUSINESS processing ← PYQ!            "COBOL = structured"=FALSE
BASIC                 BEGINNERS ← PYQ!                      "BASIC = scientific"=FALSE
LISP                  AI / List processing ← PYQ!           "LISP = business"=FALSE
Compiler              WHOLE program at once                  "Compiler=line by line"
Interpreter           LINE BY LINE                          "Interpreter=all at once"
Assembler             Translates ASSEMBLY → MACHINE code     "Assembler=compiler"=FALSE
──────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## 📚 Mixed GS Revision — Maths + History + Science Shortcuts

---

## 🔷 GS TOPIC 1: Maths Shortcuts (PYQ Targeted)

```
MATHS SHORTCUTS — RAPID REVISION
════════════════════════════════════════════════════════

PERCENTAGE SHORTCUTS:
  x% of y = y% of x  ← VERY useful trick!
  Example: 8% of 50 = 50% of 8 = 4 (much easier!)

  % CHANGE formula = (New - Old) / Old × 100

  If price increases by r%, to restore original:
  % decrease needed = r/(100+r) × 100

  If price decreases by r%, to restore original:
  % increase needed = r/(100-r) × 100

PROFIT & LOSS:
  Profit %  = (Profit / CP) × 100
  Loss %    = (Loss / CP) × 100
  SP = CP × (100 + Profit%) / 100
  CP = SP × 100 / (100 + Profit%)

  SHORTCUT: If article sold at x% profit and y% loss:
  Net result = if (x > y) = profit of (x-y)%? NO!
  Correct formula: Net % = x - y - (xy/100)

SIMPLE INTEREST (SI):
  SI = (P × R × T) / 100
  Where P = Principal, R = Rate%, T = Time (years)
  Amount = P + SI

COMPOUND INTEREST (CI):
  Amount A = P(1 + R/100)^T
  CI = A - P

  CI vs SI (same P, R, T):
  CI > SI always (for T > 1 year)
  CI - SI for 2 years = P(R/100)²

RATIO & PROPORTION:
  If a:b = c:d → a×d = b×c (cross multiply)
  Mean proportion of a and b = √(ab)

  MIXTURE ALLIGATION:
  ┌──────────────────────────────────────────────┐
  │ Cheap    │  Mean   │  Expensive              │
  │  C       │   m     │    E                    │
  │          │         │                         │
  │          (E - m) : (m - C) = ratio to mix    │
  └──────────────────────────────────────────────┘

HCF & LCM:
  HCF × LCM = Product of two numbers
  (for TWO numbers only)

  HCF of fractions = HCF of numerators / LCM of denominators
  LCM of fractions = LCM of numerators / HCF of denominators

PYQ TRAP: "HCF × LCM = product of numbers" → TRUE only for TWO numbers
```

---

## 🔷 GS TOPIC 2: History — Freedom Struggle Rapid Revision

```
MODERN HISTORY — RAPID REVISION (PYQ-focused)
════════════════════════════════════════════════════════

NON-COOPERATION MOVEMENT (1920–1922):
  Started by: GANDHI (after Jallianwala Bagh 1919 + Khilafat issue)
  Ended due to: CHAURI CHAURA incident (Feb 1922)
                (mob burned police station killing 22 policemen)
  Bihar's role: Swami Vidyanand led Bihar peasants ← PYQ!
  
CIVIL DISOBEDIENCE MOVEMENT (1930–1934):
  Started by: GANDHI (Dandi March / Salt March — March 1930)
  Dandi March: 12 March 1930 → Gandhi walked 241 miles to Dandi
               to make salt (breaking British salt law)
  Round Table Conferences: 3 RTCs (1930, 1931, 1932)
  Gandhi-Irwin Pact: March 1931 (suspended CDM temporarily)
  
QUIT INDIA MOVEMENT (1942):
  August 8, 1942 — Bombay session of INC
  Slogan: "Do or Die" (Gandhi's call)
  British response: Arrested ALL Congress leaders immediately
  Largest mass movement of India's freedom struggle ← PYQ!
  
INA (Indian National Army):
  Founded by: MOHAN SINGH (1942) ← PYQ! (NOT Bose initially)
  Reorganized by: SUBHASH CHANDRA BOSE (1943)
  Slogan: "Dilli Chalo" (March to Delhi)
  Women's wing: "Rani of Jhansi Regiment"

INC SESSIONS (IMPORTANT):
  1885: First INC session — Bombay; President: W.C. BONNERJEE ← PYQ!
  1906: Calcutta session — "Swaraj" declared as goal (first time)
  1907: Surat Split — Moderates vs Extremists split
  1916: Lucknow session — Reunion of Moderates + Extremists
        Lucknow Pact (INC + Muslim League) ← PYQ!
  1920: Nagpur session — Gandhi takes control; Non-Cooperation adopted
  1922: Gaya session — President: CHITTARANJAN DAS ← PYQ!
  1929: Lahore session — "Purna Swaraj" (Complete Independence)
        Nehru = President; January 26 = Independence Day declared
  
REVOLUTIONARY ORGANIZATIONS:
  Ghadar Party: Founded 1913, SAN FRANCISCO (USA) ← PYQ!
  Abhinav Bharat (London): Founded by V.D. SAVARKAR ← PYQ!
  Anushilan Samiti (Patna, 1913): Sachindra Nath Sanyal ← PYQ!
  
IMPORTANT DATES:
  Jallianwala Bagh Massacre: 13 April 1919 (Baisakhi day)
  Montagu-Chelmsford Reforms: 1919
  Simon Commission: 1927 (boycotted — "Simon Go Back")
  Poona Pact: 1932 (Gandhi + Ambedkar — depressed classes reservation)
```

---

## 🔷 GS TOPIC 3: Science Quick Revision

```
SCIENCE REVISION — DAY 84 SHORTCUTS
════════════════════════════════════════════════════════

PHYSICS QUICK HITS:
  Newton's Laws:
    1st Law: Body at rest stays at rest (Inertia)
    2nd Law: F = ma (Force = mass × acceleration) ← PYQ!
    3rd Law: Every action has equal + opposite reaction

  Work = Force × Displacement × cos θ
  Power = Work / Time = Force × velocity
  Energy = ½mv² (Kinetic) | mgh (Potential)

  PRESSURE:
    Liquid pressure = ρgh (density × gravity × height)
    Deeper in liquid → MORE pressure ← PYQ!

  SOUND:
    Speed in air = 343 m/s (at 20°C)
    Faster in SOLIDS > Liquids > Gases ← PYQ!
    Ultrasound = frequency > 20,000 Hz
    Infrasound = frequency < 20 Hz
    Human hearing range = 20 Hz to 20,000 Hz

  OPTICS:
    Concave mirror = converging mirror
    Convex mirror  = diverging mirror (used in vehicles — wider view)
    Real image = inverted; formed by concave mirror/convex lens
    Virtual image = erect; formed by convex mirror/concave lens

CHEMISTRY QUICK HITS:
  Acid properties:
    → Tastes sour; turns blue litmus RED
    → pH < 7 (lower = more acidic)
    → HCl = hydrochloric acid (stomach acid)
    → H₂SO₄ = sulfuric acid (strongest lab acid)

  Base properties:
    → Tastes bitter; turns red litmus BLUE
    → pH > 7 (higher = more basic/alkaline)
    → NaOH = sodium hydroxide (caustic soda)

  Neutralization: Acid + Base → Salt + Water ← PYQ!
  Antacid = BASE that neutralizes stomach acid ← Day 80 PYQ!

  pH SCALE:
    0──────────7──────────14
    Acid     Neutral    Base/Alkali
    (pH 7 = PURE WATER = NEUTRAL) ← PYQ!

BIOLOGY REVISION:
  Blood groups: A, B, AB, O
  Universal DONOR = O (negative) ← PYQ!
  Universal RECIPIENT = AB (positive) ← PYQ!
  
  Vitamins:
    Vitamin A = Vision; deficiency = Night blindness ← PYQ!
    Vitamin B12 = Anemia (pernicious anemia)
    Vitamin C = Scurvy; in citrus fruits
    Vitamin D = Bone health; deficiency = Rickets ← PYQ!
    Vitamin E = Antioxidant; fertility
    Vitamin K = Blood clotting ← PYQ!

  Fat-soluble vitamins: A, D, E, K  (ADEK) ← PYQ!
  Water-soluble vitamins: B complex, C

  Human heart:
    4 chambers: 2 atria + 2 ventricles
    Right side: Deoxygenated blood
    Left side: Oxygenated blood ← PYQ!
    Normal heart rate: 60–100 bpm
```

---

## 📊 GS MASTER SHORTCUT TABLE — Day 84

```
TOPIC                  KEY FACT                              TRAP
──────────────────────────────────────────────────────────────────────
Non-Cooperation        Started 1920; ended Chauri Chaura     "Ended by Jallianwala
Movement               1922 (Feb)                            Bagh" = FALSE
Dandi March            12 March 1930; 241 miles to Dandi     "1929" = FALSE
Quit India             8 August 1942; "Do or Die"; Bombay    "1940" or "Lahore"=FALSE
INA Founder            MOHAN SINGH ← PYQ!                    "Bose founded INA" =
                                                              WRONG (reorganized)
First INC session      1885; Bombay; W.C. BONNERJEE          "Calcutta" = FALSE
Gaya INC 1922          President = CHITTARANJAN DAS           "Nehru" = FALSE
Lahore INC 1929        "Purna Swaraj"; Nehru president;      "1930" = FALSE
                        Jan 26 = Independence Day
Ghadar Party           1913; SAN FRANCISCO, USA               "London" = FALSE
Universal blood donor  O (negative)                           "AB" = FALSE
Universal recipient    AB (positive)                          "O" = FALSE
Vitamin A              Night blindness                        "Scurvy" = WRONG (C)
Vitamin C              Scurvy (citrus fruits)                 "Rickets" = WRONG (D)
Vitamin D              Rickets (bone deficiency)              "Night blindness"=WRONG
Vitamin K              Blood clotting                        "Wound healing"=imprecise
Fat-soluble vitamins   A, D, E, K (ADEK)                     "C is fat-soluble"=FALSE
Sound speed order      Solid > Liquid > Gas                   "Gas fastest"=FALSE
pH neutral water       pH = 7                                 "pH 0 = neutral"=FALSE
Newton's 2nd Law       F = ma                                 "F = mv"=FALSE
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 84 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** According to Chomsky Hierarchy, REGULAR LANGUAGES are accepted by:
(A) Pushdown Automaton (PDA)
(B) Turing Machine
(C) FINITE AUTOMATON (DFA or NFA)
(D) More than one of the above
(E) None of the above

---

**Q2.** CONTEXT-FREE LANGUAGES (Type 2 in Chomsky Hierarchy) are accepted by:
(A) Finite Automaton (DFA/NFA)
(B) Turing Machine only
(C) PUSHDOWN AUTOMATON (PDA)
(D) More than one of the above
(E) None of the above

---

**Q3.** In Chomsky Hierarchy, which grammar type is the MOST POWERFUL (can describe most complex languages)?
(A) Regular Grammar (Type 3)
(B) Context-Free Grammar (Type 2)
(C) Unrestricted Grammar / Type 0 (Recursively Enumerable)
(D) More than one of the above
(E) None of the above

---

**Q4.** The COMPUTATIONAL POWER of DFA (Deterministic Finite Automaton) compared to NFA is:
(A) NFA is more powerful — can accept languages DFA cannot
(B) DFA is more powerful — NFA is just an approximation
(C) EQUAL — both DFA and NFA accept exactly the REGULAR LANGUAGES
(D) More than one of the above
(E) None of the above

---

**Q5.** A Pushdown Automaton (PDA) is essentially:
(A) A Turing Machine with limited tape
(B) An NFA with infinite memory
(C) A FINITE AUTOMATON with a STACK (extra memory)
(D) More than one of the above
(E) None of the above

---

**Q6.** A Turing Machine was proposed by:
(A) Charles Babbage
(B) John von Neumann
(C) ALAN TURING (1936)
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following components does a standard Turing Machine possess?
(A) Infinite Tape + Read/Write Head + State Register
(B) Transition Function + Blank Symbol + Finite set of States
(C) Both (A) and (B) above
(D) More than one of the above
(E) None of the above

---

**Q8.** A Turing Machine does NOT have which of the following?
(A) An infinite tape
(B) A read/write head
(C) A SEPARATE OUTPUT TAPE
(D) More than one of the above
(E) None of the above

---

**Q9.** The HALTING PROBLEM is classified as:
(A) A decidable problem (solvable by some algorithm in finite time)
(B) An NP-complete problem
(C) UNDECIDABLE — no algorithm can always correctly solve it
(D) More than one of the above
(E) None of the above

---

**Q10.** What does it mean for the Halting Problem to be UNDECIDABLE?
(A) It takes very long to solve but eventually terminates
(B) It can only be solved by quantum computers
(C) NO algorithm exists that can always correctly determine if an arbitrary program halts or loops
(D) More than one of the above
(E) None of the above

---

**Q11.** The Halting Problem was proved UNDECIDABLE by:
(A) Charles Babbage using mechanical computation
(B) John von Neumann in computer architecture
(C) ALAN TURING in 1936 using diagonalization argument
(D) More than one of the above
(E) None of the above

---

**Q12.** Machine Language (1GL) is characterized as:
(A) Machine-independent and easy to port across platforms
(B) High-level and human-readable
(C) MACHINE-DEPENDENT, DIFFICULT TO PROGRAM, and ERROR-PRONE
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following statements about Machine Language are TRUE?
```
1. It is machine-dependent
2. It is difficult to program
3. It is error-prone
```
(A) Only statement 1
(B) Only statements 1 and 2
(C) All three statements are true
(D) More than one of the above
(E) None of the above

---

**Q14.** Assembly Language is classified as a:
(A) High-level language (3GL) like C and Java
(B) Very high-level language (4GL) like SQL
(C) LOW-LEVEL language (2GL) that uses MNEMONICS
(D) More than one of the above
(E) None of the above

---

**Q15.** Assembly language programs are translated into machine code by:
(A) A Compiler
(B) An Interpreter
(C) An ASSEMBLER
(D) More than one of the above
(E) None of the above

---

**Q16.** Which programming language is BEST SUITED for writing STRUCTURED code?
(A) BASIC
(B) FORTRAN
(C) PASCAL
(D) More than one of the above
(E) None of the above

---

**Q17.** FORTRAN (Formula Translation) is primarily used for:
(A) Business data processing
(B) Beginner programming exercises
(C) SCIENTIFIC and MATHEMATICAL computations
(D) More than one of the above
(E) None of the above

---

**Q18.** FORTRAN holds which historical distinction among high-level languages?
(A) It was the FIRST high-level programming language created
(B) It was designed specifically for artificial intelligence
(C) It introduced object-oriented programming concepts
(D) More than one of the above
(E) None of the above

---

**Q19.** COBOL (Common Business Oriented Language) is best suited for:
(A) Scientific computing and mathematical simulations
(B) Artificial intelligence and expert systems
(C) BUSINESS DATA PROCESSING (reads like English sentences)
(D) More than one of the above
(E) None of the above

---

**Q20.** BASIC programming language was designed primarily for:
(A) Scientific research applications
(B) Business financial systems
(C) BEGINNERS learning to program
(D) More than one of the above
(E) None of the above

---

**Q21.** LISP programming language is primarily associated with:
(A) Business data processing like COBOL
(B) Structured programming like PASCAL
(C) ARTIFICIAL INTELLIGENCE and LIST PROCESSING
(D) More than one of the above
(E) None of the above

---

**Q22.** A COMPILER differs from an INTERPRETER in that:
(A) Compiler translates line-by-line; interpreter translates the whole program
(B) Both translate line-by-line but compiler is faster
(C) Compiler translates the WHOLE program AT ONCE; interpreter translates LINE BY LINE
(D) More than one of the above
(E) None of the above

---

**Q23.** The language aⁿbⁿ (strings with equal number of a's followed by b's, e.g., ab, aabb, aaabbb) is:
(A) A Regular Language — accepted by DFA
(B) A Recursively Enumerable Language — accepted by Turing Machine only
(C) A CONTEXT-FREE LANGUAGE — accepted by Pushdown Automaton (PDA)
(D) More than one of the above
(E) None of the above

---

**Q24.** In the Chomsky Hierarchy, programming language SYNTAX (grammar rules) is typically described by:
(A) Regular Grammar (Type 3)
(B) Unrestricted Grammar (Type 0)
(C) CONTEXT-FREE GRAMMAR (Type 2 — CFG)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following CORRECTLY matches the translator to what it translates?
(A) Assembler → High-level to Machine; Compiler → Assembly to Machine
(B) Interpreter → Whole program at once; Assembler → line by line
(C) Assembler → Assembly to Machine; Compiler → High-level to Machine (whole program)
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Mixed Revision — Maths + History + Science

---

**Q26.** The NON-COOPERATION MOVEMENT (1920) was withdrawn by Gandhi due to:
(A) The Jallianwala Bagh massacre
(B) Signing of the Gandhi-Irwin Pact
(C) CHAURI CHAURA incident (February 1922) where a mob burned a police station
(D) More than one of the above
(E) None of the above

---

**Q27.** Gandhi's DANDI MARCH (Salt March) began on:
(A) 26 January 1930
(B) 8 August 1930
(C) 12 March 1930 (walked to Dandi to make salt, breaking British law)
(D) More than one of the above
(E) None of the above

---

**Q28.** The QUIT INDIA MOVEMENT was launched on:
(A) 26 January 1942
(B) 15 August 1942
(C) 8 August 1942 (Bombay session; "Do or Die" slogan)
(D) More than one of the above
(E) None of the above

---

**Q29.** The INDIAN NATIONAL ARMY (INA) was originally FOUNDED by:
(A) Subhash Chandra Bose
(B) Bhagat Singh
(C) MOHAN SINGH (1942) — Bose reorganized it in 1943
(D) More than one of the above
(E) None of the above

---

**Q30.** The FIRST SESSION of the Indian National Congress (INC) was held in:
(A) Calcutta, 1886; President: Dadabhai Naoroji
(B) Delhi, 1885; President: Bal Gangadhar Tilak
(C) BOMBAY (Mumbai), 1885; President: W.C. BONNERJEE
(D) More than one of the above
(E) None of the above

---

**Q31.** The INC Session of 1929 at LAHORE is famous for:
(A) Declaring "Swaraj" (self-rule) as the first goal
(B) The Surat Split between Moderates and Extremists
(C) Declaring "PURNA SWARAJ" (Complete Independence); Nehru as President; January 26 as Independence Day
(D) More than one of the above
(E) None of the above

---

**Q32.** The GHADAR PARTY was founded in:
(A) London, England in 1905
(B) Berlin, Germany in 1915
(C) SAN FRANCISCO, USA in 1913
(D) More than one of the above
(E) None of the above

---

**Q33.** A shopkeeper buys a shirt for ₹400 and sells it at 25% profit. What is the selling price?
(A) ₹480
(B) ₹520
(C) ₹500
(D) More than one of the above
(E) None of the above

---

**Q34.** Simple Interest on ₹1000 at 10% per annum for 2 years is:
(A) ₹100
(B) ₹210
(C) ₹200
(D) More than one of the above
(E) None of the above

---

**Q35.** The UNIVERSAL BLOOD DONOR (can donate to all blood groups) is:
(A) Blood group AB positive
(B) Blood group A negative
(C) BLOOD GROUP O NEGATIVE
(D) More than one of the above
(E) None of the above

---

**Q36.** Deficiency of VITAMIN D causes:
(A) Night blindness
(B) Scurvy
(C) RICKETS (soft/weak bones in children)
(D) More than one of the above
(E) None of the above

---

**Q37.** Which of the following vitamins are FAT-SOLUBLE?
(A) Vitamins B and C
(B) Vitamins C and D
(C) Vitamins A, D, E, and K (ADEK)
(D) More than one of the above
(E) None of the above

---

**Q38.** Speed of SOUND is FASTEST in:
(A) Air (gas)
(B) Water (liquid)
(C) SOLID materials (fastest in solids > liquids > gases)
(D) More than one of the above
(E) None of the above

---

**Q39.** The pH of PURE WATER at 25°C is:
(A) 0 (strongly acidic)
(B) 14 (strongly basic)
(C) 7 (NEUTRAL)
(D) More than one of the above
(E) None of the above

---

**Q40.** NEWTON'S SECOND LAW of motion states:
(A) Every action has an equal and opposite reaction
(B) A body in motion stays in motion (Inertia)
(C) FORCE = MASS × ACCELERATION (F = ma)
(D) More than one of the above
(E) None of the above

---

**Q41.** In human circulation, the LEFT side of the heart carries:
(A) Deoxygenated blood (from body to lungs)
(B) Mixed blood from both lungs and body
(C) OXYGENATED blood (from lungs to body)
(D) More than one of the above
(E) None of the above

---

**Q42.** Deficiency of VITAMIN A causes:
(A) Scurvy (bleeding gums)
(B) Rickets (soft bones)
(C) NIGHT BLINDNESS (inability to see in dim light)
(D) More than one of the above
(E) None of the above

---

**Q43.** NEUTRALIZATION reaction (Acid + Base) produces:
(A) Acid + Hydrogen gas
(B) Base + Carbon dioxide
(C) SALT + WATER
(D) More than one of the above
(E) None of the above

---

**Q44.** The HCF and LCM of two numbers are 6 and 120 respectively. If one number is 24, the other number is:
(A) 20
(B) 36
(C) 30
(D) More than one of the above
(E) None of the above

---

**Q45.** The UNIVERSAL BLOOD RECIPIENT (can receive from all blood groups) is:
(A) Blood group O positive
(B) Blood group B negative
(C) BLOOD GROUP AB POSITIVE
(D) More than one of the above
(E) None of the above

---

**Q46.** The JALLIANWALA BAGH MASSACRE occurred on:
(A) 13 April 1919 (Baisakhi day) — ordered by General Dyer
(B) 13 April 1918 — during World War I
(C) 1 August 1920 — launch of Non-Cooperation Movement
(D) More than one of the above
(E) None of the above

---

**Q47.** VITAMIN C deficiency causes:
(A) Night blindness
(B) Beriberi
(C) SCURVY (bleeding gums, weak immunity; found in citrus fruits)
(D) More than one of the above
(E) None of the above

---

**Q48.** A CONVEX MIRROR is used in vehicle rear-view mirrors because:
(A) It forms a real, enlarged image for better visibility
(B) It has a longer focal length than plane mirrors
(C) It forms a VIRTUAL, DIMINISHED image providing a WIDER field of view
(D) More than one of the above
(E) None of the above

---

**Q49.** The INC SESSION OF 1922 at GAYA had which leader as President?
(A) Mahatma Gandhi
(B) Jawaharlal Nehru
(C) CHITTARANJAN DAS
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY matches the language with its purpose?
(A) PASCAL → Structured code; FORTRAN → Scientific computing; BASIC → Beginners
(B) COBOL → Business processing; LISP → AI; BASIC → Beginners
(C) Both (A) and (B) above are correct
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                                   |
|----|--------|-------------------------------------------------------------------------------------|
| 1  | (C)    | Regular Languages → accepted by Finite Automaton (DFA/NFA) ← Chomsky Type 3        |
| 2  | (C)    | Context-Free Languages → accepted by Pushdown Automaton (PDA) ← Type 2             |
| 3  | (C)    | Type 0 / Unrestricted Grammar = most powerful; accepted by Turing Machine           |
| 4  | (C)    | DFA and NFA have EQUAL power — both accept exactly Regular Languages                |
| 5  | (C)    | PDA = Finite Automaton + STACK (extra memory)                                       |
| 6  | (C)    | Turing Machine proposed by ALAN TURING in 1936                                      |
| 7  | (D)    | TM has: Infinite tape, R/W head, State register, Transition function → ALL → (D)    |
| 8  | (C)    | TM does NOT have a SEPARATE OUTPUT TAPE ← #1 PYQ trap! Uses same tape              |
| 9  | (C)    | Halting Problem = UNDECIDABLE ← most important TOC fact!                            |
| 10 | (C)    | Undecidable = NO algorithm can always correctly solve for ALL inputs                |
| 11 | (C)    | Halting Problem proved UNDECIDABLE by ALAN TURING in 1936                           |
| 12 | (C)    | Machine Language = machine-dependent + difficult + error-prone → ALL THREE          |
| 13 | (D)    | All three statements TRUE → Answer (D) ← classic BPSC TRE answer!                  |
| 14 | (C)    | Assembly Language = LOW-LEVEL (2GL) using MNEMONICS                                 |
| 15 | (C)    | Assembly language translated by ASSEMBLER (not compiler/interpreter)                |
| 16 | (C)    | PASCAL = best for STRUCTURED code ← PYQ!                                            |
| 17 | (C)    | FORTRAN = SCIENTIFIC and MATHEMATICAL computations ← PYQ!                          |
| 18 | (A)    | FORTRAN = FIRST high-level programming language ever created ← PYQ!                |
| 19 | (C)    | COBOL = BUSINESS DATA PROCESSING ← PYQ!                                             |
| 20 | (C)    | BASIC = designed for BEGINNERS ← PYQ!                                               |
| 21 | (C)    | LISP = ARTIFICIAL INTELLIGENCE + LIST PROCESSING ← PYQ!                            |
| 22 | (C)    | Compiler = whole program at once; Interpreter = line by line ← PYQ!                |
| 23 | (C)    | aⁿbⁿ = Context-Free Language; accepted by PDA (DFA cannot count!)                   |
| 24 | (C)    | Programming language SYNTAX described by Context-Free Grammar (CFG) ← important!   |
| 25 | (C)    | Assembler→Assembly to Machine; Compiler→High-level to Machine (whole program) ✅    |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                              |
|----|--------|--------------------------------------------------------------------------------|
| 26 | (C)    | Non-Cooperation withdrawn due to CHAURI CHAURA incident (Feb 1922) ← PYQ!     |
| 27 | (C)    | Dandi March started 12 March 1930 ← PYQ!                                      |
| 28 | (C)    | Quit India Movement = 8 August 1942; "Do or Die"; Bombay ← PYQ!               |
| 29 | (C)    | INA FOUNDED by MOHAN SINGH (1942) — Bose reorganized later ← PYQ!             |
| 30 | (C)    | First INC session = Bombay 1885; President W.C. BONNERJEE ← PYQ!              |
| 31 | (C)    | Lahore 1929 = Purna Swaraj + Nehru president + Jan 26 = Independence Day       |
| 32 | (C)    | Ghadar Party = SAN FRANCISCO, USA, 1913 ← PYQ!                                |
| 33 | (C)    | SP = 400 × 125/100 = 400 × 1.25 = ₹500                                        |
| 34 | (C)    | SI = (1000 × 10 × 2)/100 = ₹200                                                |
| 35 | (C)    | Universal DONOR = O NEGATIVE ← PYQ!                                            |
| 36 | (C)    | Vitamin D deficiency = RICKETS ← PYQ!                                          |
| 37 | (C)    | Fat-soluble = A, D, E, K (ADEK) ← PYQ!                                        |
| 38 | (C)    | Sound fastest in SOLIDS > Liquids > Gases ← PYQ!                              |
| 39 | (C)    | Pure water pH = 7 (NEUTRAL) ← PYQ!                                            |
| 40 | (C)    | Newton's 2nd Law = F = ma ← PYQ!                                               |
| 41 | (C)    | LEFT heart = OXYGENATED blood (from lungs to body) ← PYQ!                     |
| 42 | (C)    | Vitamin A deficiency = NIGHT BLINDNESS ← PYQ!                                 |
| 43 | (C)    | Acid + Base → SALT + WATER (neutralization) ← PYQ!                            |
| 44 | (C)    | HCF × LCM = Product; 6 × 120 = 720; 720/24 = 30 ← verify: HCF(24,30)=6 ✅    |
| 45 | (C)    | Universal RECIPIENT = AB POSITIVE ← PYQ!                                       |
| 46 | (A)    | Jallianwala Bagh = 13 April 1919 (Baisakhi); General Dyer ← PYQ!              |
| 47 | (C)    | Vitamin C deficiency = SCURVY ← PYQ!                                           |
| 48 | (C)    | Convex mirror in vehicles = virtual, diminished image; WIDER field of view      |
| 49 | (C)    | Gaya INC 1922 President = CHITTARANJAN DAS ← PYQ!                              |
| 50 | (D)    | BOTH (A) and (B) match correctly → Answer = (D) ← Answer D pattern!           |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (TOC + Languages)

```
CHOMSKY HIERARCHY:
1.  Type 3 = Regular Language → FINITE AUTOMATON (DFA/NFA)
2.  Type 2 = Context-Free Language → PUSHDOWN AUTOMATON (PDA)
3.  Type 1 = Context-Sensitive → Linear Bounded Automaton
4.  Type 0 = Recursively Enumerable → TURING MACHINE (most powerful)
5.  Programming language SYNTAX = Context-Free Grammar (CFG)
    Memory trick: Regular → CF → CS → RE (inner to outer box)

FINITE AUTOMATA:
6.  DFA = NFA in POWER (both accept exactly Regular Languages) ← PYQ!
    "NFA is more powerful than DFA" → FALSE
7.  PDA = FA + STACK; recognizes Context-Free Languages
8.  aⁿbⁿ = CFL (DFA CANNOT accept — needs counting!)

TURING MACHINE:
9.  Proposed by ALAN TURING (1936)
10. Components: Infinite Tape, R/W Head, State Register,
    Transition Function, Blank Symbol
11. TM does NOT have a SEPARATE OUTPUT TAPE ← #1 PYQ trap!
12. R/W head can move LEFT or RIGHT (unlike DFA — right only)
13. TM accepts Recursively Enumerable Languages (most powerful)

HALTING PROBLEM:
14. UNDECIDABLE ← most important TOC fact! ← PYQ!
15. Proved by ALAN TURING (1936)
16. "Halting Problem = NP problem" → FALSE (it's UNDECIDABLE!)
17. Undecidable = no algorithm can ALWAYS correctly solve for all inputs

MACHINE LANGUAGE (1GL):
18. Machine-dependent + difficult to program + error-prone
    → ALL THREE true → Answer = (D) ← PYQ!
19. Fastest execution (CPU runs directly, no translation needed)

ASSEMBLY LANGUAGE (2GL):
20. LOW-LEVEL language; uses MNEMONICS (MOV, ADD, SUB, JMP)
21. Translated by ASSEMBLER (NOT compiler, NOT interpreter) ← PYQ!
22. Machine-dependent (different CPU families have different mnemonics)

LANGUAGE PURPOSES:
23. PASCAL   = STRUCTURED code ← PYQ!
24. FORTRAN  = SCIENTIFIC computing; FIRST high-level language ← PYQ!
25. COBOL    = BUSINESS processing ← PYQ!
26. BASIC    = BEGINNERS ← PYQ!
27. LISP     = ARTIFICIAL INTELLIGENCE ← PYQ!
28. PROLOG   = Logic programming / AI / Expert systems

TRANSLATORS:
29. Compiler    = WHOLE program at once → faster execution
    Interpreter = LINE BY LINE → slower; stops at first error
    Assembler   = Assembly → Machine code
30. Python = Interpreter; C/C++ = Compiler; Assembly = Assembler
```

---

### ⚡ GS — 25 MUST-KNOW MIXED FACTS

```
HISTORY:
1.  Non-Cooperation 1920 → withdrawn: CHAURI CHAURA (Feb 1922) ← PYQ!
2.  Dandi March = 12 March 1930; Gandhi; 241 miles ← PYQ!
3.  Quit India = 8 August 1942; "Do or Die"; Bombay ← PYQ!
4.  INA FOUNDED = MOHAN SINGH (1942); REORGANIZED = Bose (1943) ← PYQ!
5.  First INC = 1885; Bombay; W.C. BONNERJEE ← PYQ!
6.  Lahore INC 1929 = Purna Swaraj + Nehru + Jan 26 ← PYQ!
7.  Gaya INC 1922 = Chittaranjan Das (president) ← PYQ!
8.  Ghadar Party = San Francisco, USA, 1913 ← PYQ!
9.  Jallianwala Bagh = 13 April 1919; General Dyer ← PYQ!

SCIENCE:
10. Universal DONOR = O negative; Universal RECIPIENT = AB positive ← PYQ!
11. Vitamin A = Night blindness ← PYQ!
12. Vitamin C = Scurvy (citrus fruits) ← PYQ!
13. Vitamin D = Rickets (bone) ← PYQ!
14. Vitamin K = Blood clotting ← PYQ!
15. Fat-soluble = A, D, E, K (ADEK); Water-soluble = B, C ← PYQ!
16. Sound: Solid > Liquid > Gas (speed order) ← PYQ!
17. Newton's 2nd Law = F = ma ← PYQ!
18. Pure water pH = 7 (neutral) ← PYQ!
19. LEFT heart = OXYGENATED blood ← PYQ!
20. Acid + Base = Salt + Water (neutralization) ← PYQ!
21. Convex mirror = wider field of view (vehicles) ← PYQ!

MATHS:
22. SI = PRT/100; Compound gives MORE interest than simple (T>1yr)
23. HCF × LCM = product of TWO numbers (only for two numbers!)
24. HCF of fractions = HCF(numerators)/LCM(denominators)
25. Profit % = (Profit/CP) × 100; SP = CP × (100 + P%)/100
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
CHOMSKY TYPE  LANGUAGE CLASS      AUTOMATON              EXAMPLE
────────────────────────────────────────────────────────────────────
Type 3         Regular             DFA / NFA              a*b*, (ab)*
Type 2         Context-Free (CFL)  PDA (FA + Stack)       aⁿbⁿ
Type 1         Context-Sensitive   Linear Bounded Aut.    aⁿbⁿcⁿ
Type 0         Recursively Enum.   Turing Machine         Any TM language
────────────────────────────────────────────────────────────────────

LANGUAGE       BEST FOR            FIRST/SPECIAL FACT
────────────────────────────────────────────────────────────────────
PASCAL         STRUCTURED code     Niklaus Wirth designed it
FORTRAN        SCIENTIFIC          FIRST high-level language!
COBOL          BUSINESS            Reads like English
BASIC          BEGINNERS           Easiest to learn
LISP           AI / Lists          One of oldest AI languages
PROLOG         Logic / AI          Constraint-based programming
────────────────────────────────────────────────────────────────────

TRANSLATOR     INPUT               OUTPUT          METHOD
────────────────────────────────────────────────────────────────────
Assembler      Assembly (mnemonics) Machine code   One-to-one mapping
Compiler       High-level source    Machine code   Whole program at once
Interpreter    High-level source    Direct execution Line by line
────────────────────────────────────────────────────────────────────

VITAMIN   DEFICIENCY DISEASE     SOLUBILITY   FOOD SOURCE
────────────────────────────────────────────────────────────────────
A         Night blindness         Fat          Carrots, liver
C         Scurvy                  Water        Citrus fruits
D         Rickets                 Fat          Sunlight, fish
K         Poor blood clotting     Fat          Leafy greens
B12       Pernicious anemia       Water        Meat, dairy
────────────────────────────────────────────────────────────────────
```

---

## 🎯 DAY 84 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   Theory of Computation — Chomsky Hierarchy (4 types with automata) |
      Finite Automata: DFA vs NFA (equal power — both = Regular Languages) |
      PDA = FA + Stack (recognizes Context-Free Languages) |
      Turing Machine — Alan Turing 1936; components; NO separate output tape ← PYQ |
      Halting Problem = UNDECIDABLE (not NP!) ← PYQ |
      Machine Language: machine-dependent + difficult + error-prone → ALL → (D) ← PYQ |
      Assembly Language: LOW-LEVEL; mnemonics; translated by ASSEMBLER ← PYQ |
      Language purposes: PASCAL=structured, FORTRAN=scientific (first HLL!),
      COBOL=business, BASIC=beginners, LISP=AI ← all PYQ |
      Compiler=whole program; Interpreter=line by line; Assembler=assembly→machine

GS:   History — Non-Cooperation/Chauri Chaura, Dandi March 12 March 1930,
      Quit India 8 Aug 1942, INA founder=Mohan Singh, first INC=1885 Bonnerjee,
      Lahore 1929=Purna Swaraj, Gaya 1922=Chittaranjan Das, Ghadar=San Francisco |
      Science — Vitamins (A/C/D/K deficiencies), fat-soluble ADEK,
      Universal donor O-, recipient AB+, F=ma, sound order, pH=7 neutral |
      Maths — SI/CI formulas, Profit/Loss, HCF×LCM=product (two numbers)

NEXT: Day 85 — Web Technologies (HTML/CSS/JS structure vs styling vs behavior) +
      Cybersecurity (Virus vs Worm vs Trojan vs Ransomware, Phishing, Firewall)
      GS: Awards & Recognitions
```

---

*Day 84 of 170 | Phase 2: Depth | Week 13: AI, IoT, Emerging Tech & Theory of Computation*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
