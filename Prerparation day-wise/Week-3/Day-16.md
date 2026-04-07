# 📅 BPSC TRE 4.0 — DAY 16 COMPLETE STUDY MATERIAL
## CS: Stack Data Structure | GS: Bihar Geography — Economy, Rohtas, Bhagalpur & Key Districts
### Target: TOP RANK | Phase 1, Week 3

---

> **⚡ TOPPER MINDSET:** Stack appeared in **ALL 3 previous TRE papers** combined 20+ times.
> It is tested in EVERY single BPSC TRE CS section. Mastering Stack = guaranteed marks.
> Bihar Economy + District facts = 4-6 GS questions per paper. Double win today!

---

# ═══════════════════════════════════════════════════
# 🖥️  PART A — COMPUTER SCIENCE
##  Topic: Stack — The Complete Guide
# ═══════════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A STACK? — REAL LIFE ANALOGY

A **Stack** is a linear data structure that follows the **LIFO principle** — **Last In, First Out**.

The last element inserted is the first one to be removed.

```
REAL LIFE ANALOGIES FOR STACK
================================

1. STACK OF PLATES in a cafeteria:
   ┌─────────┐
   │ Plate 5 │ ← LAST placed = FIRST taken (TOP)
   ├─────────┤
   │ Plate 4 │
   ├─────────┤
   │ Plate 3 │
   ├─────────┤
   │ Plate 2 │
   ├─────────┤
   │ Plate 1 │ ← FIRST placed = LAST taken (BOTTOM)
   └─────────┘
   You always ADD and REMOVE from the TOP only!

2. UNDO button in MS Word:
   Type 'H' → Type 'e' → Type 'l' → Type 'l' → Type 'o'
   Stack: [H, e, l, l, o]  ← 'o' is on top
   Press CTRL+Z (Undo):  removes 'o' first  → "Hell"
   Press CTRL+Z again:   removes last 'l'   → "Hel"
   LIFO order! Last typed = first undone ✓

3. BROWSER BACK BUTTON:
   Visit Page1 → Page2 → Page3
   Stack: [Page1, Page2, Page3]
   Click Back: goes to Page2 (removes Page3 first)
   Click Back again: goes to Page1
```

---

## 📌 SECTION 2: LIFO PRINCIPLE — VISUALIZED

```
LIFO = LAST IN, FIRST OUT
===========================

Push 10:     Push 20:     Push 30:     Pop:         Pop:
┌────┐       ┌────┐       ┌────┐       ┌────┐       ┌────┐
│    │       │    │       │ 30 │←TOP   │    │       │    │
│    │       │ 20 │←TOP   │ 20 │       │ 20 │←TOP   │    │
│ 10 │←TOP   │ 10 │       │ 10 │       │ 10 │       │ 10 │←TOP
└────┘       └────┘       └────┘       └────┘       └────┘
top=0        top=1        top=2        top=1        top=0
             (30 was last pushed → 30 is first popped)

RULE: TOP pointer always points to the most recently inserted element
```

---

## 📌 SECTION 3: STACK OPERATIONS — ALL 5 (PYQ-TESTED)

A Stack supports exactly **5 standard operations**:

```
STACK OPERATIONS
==================

Operation   | What it does                  | Complexity
────────────|-------------------------------|───────────
PUSH(x)     | Insert element x at the TOP   | O(1)
POP()       | Remove element from TOP       | O(1)
PEEK/TOP()  | View TOP element (no remove)  | O(1)
isEmpty()   | Check if stack is empty       | O(1)
isFull()    | Check if stack is full        | O(1)

ALL operations run in O(1) time — this is the biggest advantage of Stack!
```

### PUSH Operation:
```
PUSH Algorithm:
================
Step 1: Check if stack is FULL (top == MAX_SIZE - 1)
        If YES → OVERFLOW error (cannot push)
Step 2: If NOT full → top = top + 1
Step 3: stack[top] = element
Step 4: Done!

C++ Code:
void push(int stack[], int &top, int element, int MAX) {
    if (top == MAX - 1) {
        cout << "Stack Overflow!";
        return;
    }
    top++;
    stack[top] = element;
}
```

### POP Operation:
```
POP Algorithm:
===============
Step 1: Check if stack is EMPTY (top == -1)
        If YES → UNDERFLOW error (nothing to pop)
Step 2: If NOT empty → element = stack[top]
Step 3: top = top - 1
Step 4: Return element

C++ Code:
int pop(int stack[], int &top) {
    if (top == -1) {
        cout << "Stack Underflow!";
        return -1;
    }
    int element = stack[top];
    top--;
    return element;
}
```

### Overflow and Underflow:
```
OVERFLOW:  Trying to PUSH onto a FULL stack
           Condition: top == MAX_SIZE - 1

UNDERFLOW: Trying to POP from an EMPTY stack
           Condition: top == -1

Initial empty stack: top = -1
Stack with 1 element: top = 0
Stack with n elements: top = n - 1
```

---

## 📌 SECTION 4: STACK USING ARRAY — COMPLETE IMPLEMENTATION

```
STACK IMPLEMENTATION WITH ARRAY
==================================

Array-based Stack (size = 5):

Initial State:
  stack[] = [_, _, _, _, _]
  top = -1   ← Indicates EMPTY stack

After PUSH(10):
  stack[] = [10, _, _, _, _]
  top = 0

After PUSH(20):
  stack[] = [10, 20, _, _, _]
  top = 1

After PUSH(30):
  stack[] = [10, 20, 30, _, _]
  top = 2

After POP() → returns 30:
  stack[] = [10, 20, _, _, _]
  top = 1

After PEEK() → returns 20 (no removal):
  stack[] = [10, 20, _, _, _]
  top = 1   (unchanged)

Full Stack (MAX=3):
  stack[] = [10, 20, 30]
  top = 2  (= MAX-1 = 3-1 = 2) → OVERFLOW if push again!
```

### KEY FACTS for BPSC:
```
╔════════════════════════════════════════════════════╗
║  EMPTY STACK  : top == -1                          ║
║  FULL STACK   : top == MAX_SIZE - 1                ║
║  STACK SIZE   : top + 1 elements currently         ║
║  ALL OPERATIONS: O(1) time, O(n) space             ║
╚════════════════════════════════════════════════════╝
```

---

## 📌 SECTION 5: APPLICATIONS OF STACK (MOST TESTED IN PYQ)

This is the **#1 most asked topic** about Stack in BPSC TRE. You must memorize ALL applications.

```
APPLICATIONS OF STACK
========================

✅ IS a Stack Application:               ❌ NOT a Stack Application:
──────────────────────────────────────   ─────────────────────────────────────
1. Recursion (function call stack)        Asynchronous data transfer → QUEUE
2. Expression evaluation (postfix)        CPU scheduling → QUEUE
3. Infix → Postfix conversion             Breadth First Search (BFS) → QUEUE
4. Infix → Prefix conversion             Printer spooling → QUEUE
5. Balancing of parentheses/symbols      Level order tree traversal → QUEUE
6. Undo/Redo in text editors
7. Browser back/forward button
8. Backtracking (maze solving)
9. String reversal
10. Tower of Hanoi
11. Depth First Search (DFS) uses Stack
12. Memory management (function calls)
```

### Why Recursion uses Stack?
```
RECURSION AND STACK
=====================
When a function calls itself, the system needs to remember:
- Return address (where to go back)
- Local variables
- Parameters

These are stored in "ACTIVATION RECORDS" pushed onto the CALL STACK.

Example: factorial(3)
  factorial(3) → PUSHED onto call stack
    factorial(2) → PUSHED onto call stack
      factorial(1) → PUSHED onto call stack
        BASE CASE: return 1
      factorial(1) POPPED → returns 1 to factorial(2)
    factorial(2) POPPED → returns 2 to factorial(3)
  factorial(3) POPPED → returns 6

LIFO ORDER! Each function returns in reverse order of calls.
```

---

## 📌 SECTION 6: BALANCING OF PARENTHESES — STEP BY STEP

This is one of the most classic Stack applications asked in BPSC.

```
PROBLEM: Check if brackets are balanced
Input: { [ ( ) ] }
=========================================

Algorithm:
  FOR each character in expression:
    IF opening bracket → PUSH onto stack
    IF closing bracket → POP from stack, check if it matches

TRACE for "{ [ ( ) ] }":

  Char  | Action         | Stack State
  ──────|────────────────|─────────────────
  {     | PUSH {         | {
  [     | PUSH [         | { [
  (     | PUSH (         | { [ (
  )     | POP → gets (   | { [     match! ✓
  ]     | POP → gets [   | {       match! ✓
  }     | POP → gets {   | empty   match! ✓
  End   | Stack empty?   | YES → BALANCED ✓

Result: BALANCED!

For "{ [ ( ] ) }":
  Char  | Action         | Stack State
  ──────|────────────────|─────────────────
  {     | PUSH {         | {
  [     | PUSH [         | { [
  (     | PUSH (         | { [ (
  ]     | POP → gets (   | { [    NO MATCH! ( ≠ ]
  
Result: NOT BALANCED! ✗
```

---

## 📌 SECTION 7: STRING REVERSAL USING STACK

```
REVERSE A STRING USING STACK
==============================
Input string: "BPSC"

Step 1: PUSH all characters
  PUSH B → stack: [B]
  PUSH P → stack: [B, P]
  PUSH S → stack: [B, P, S]
  PUSH C → stack: [B, P, S, C]   ← C is at TOP

Step 2: POP all characters
  POP → C
  POP → S
  POP → P
  POP → B

Result: "CSPR" Wait — "CPSR"... Let me redo:
Input: "BPSC"
  PUSH B, P, S, C
  POP: C, S, P, B → Output = "CSPB"

Actually for "BPSC":
  Push: B, P, S, C (in that order)
  Pop (LIFO): C first, then S, then P, then B
  Result: "CSPB" ✓ (reversed string)

KEY CONCEPT: LIFO reverses the order → Perfect for string reversal!
```

---

## 📌 SECTION 8: INFIX, POSTFIX, PREFIX — INTRO (PREVIEW FOR DAY 17)

```
EXPRESSION NOTATIONS
======================

INFIX   : Operator is BETWEEN operands     →  A + B
POSTFIX : Operator is AFTER operands       →  A B +  (Reverse Polish)
PREFIX  : Operator is BEFORE operands      →  + A B  (Polish Notation)

Example: A + B * C

INFIX   :  A + B * C
POSTFIX :  A B C * +
PREFIX  :  + A * B C

Why convert? Computers evaluate POSTFIX more easily (no parentheses needed).
Stack is used for ALL conversion algorithms.

THIS IS DAY 17's MAIN TOPIC — Just remember the names today!
```

---

## 📌 SECTION 9: TOWER OF HANOI — RECURSION + STACK (PYQ)

```
TOWER OF HANOI
================
Problem: Move n disks from rod A to rod C using rod B as helper.
Rules:
  1. Move only ONE disk at a time
  2. NEVER place larger disk on smaller disk

For n disks:
  Minimum moves = 2^n - 1

Examples:
  n=1: 2^1 - 1 = 1 move
  n=2: 2^2 - 1 = 3 moves
  n=3: 2^3 - 1 = 7 moves
  n=4: 2^4 - 1 = 15 moves
  n=10: 2^10 - 1 = 1023 moves

BPSC PYQ: "Minimum number of moves to solve Tower of Hanoi with n disks?"
Answer: 2^n - 1

This uses RECURSION internally → which uses STACK!
```

---

## 📌 SECTION 10: STACK vs QUEUE — KEY DIFFERENCE (BPSC TRAP)

```
STACK vs QUEUE COMPARISON
===========================

Feature          | STACK              | QUEUE
─────────────────|--------------------|──────────────────────
Principle        | LIFO               | FIFO (First In First Out)
Insert at        | TOP                | REAR
Delete from      | TOP                | FRONT
Applications     | Recursion, DFS,    | BFS, CPU scheduling,
                 | Undo, Backtracking | Printer spool, I/O
Symbol balancing | STACK ✓            | Queue ✗
Async data xfer  | Stack ✗            | QUEUE ✓
Call stack       | STACK ✓            | Queue ✗

MEMORY AID:
  STACK = "Stack of plates" → TOP only
  QUEUE = "Queue at a ticket counter" → Enter at back, exit at front
```

---

## 📌 SECTION 11: DFS USES STACK — BFS USES QUEUE (PYQ TRAP)

```
GRAPH TRAVERSAL
=================

DFS (Depth First Search):
  → Uses STACK (explicitly or via recursion)
  → Goes DEEP into graph first
  → Backtracks when stuck
  → Like exploring a maze — go deep, then backtrack

BFS (Breadth First Search):
  → Uses QUEUE
  → Explores all neighbors at current level first
  → Like spreading water → level by level

PYQ: "Which data structure is used in BFS?" → QUEUE
     "Which data structure is used in DFS?" → STACK
     "Which traversal uses recursion (Stack)?" → DFS
```

---

## 📌 SECTION 12: STACK — C++ STL (Standard Template Library)

```
C++ STL STACK
==============
#include <stack>
using namespace std;

stack<int> s;

s.push(10);    // Insert 10
s.push(20);    // Insert 20
s.push(30);    // Insert 30

s.top()        // Returns 30 (peek — no removal)
s.pop()        // Removes 30
s.size()       // Returns current size (2 now)
s.empty()      // Returns true if empty, false otherwise

After above:
s.top() → 20

NOTE: In C++ STL stack, there is NO peek() → use top()
      pop() does NOT return the element (unlike most textbook versions)
```

---

## 📌 SECTION 13: STACK MEMORY REPRESENTATION

```
STACK IN MEMORY (Array-based, MAX=5)
=====================================

Index:    0     1     2     3     4
         ┌─────┬─────┬─────┬─────┬─────┐
Stack:   │ 10  │ 20  │ 30  │     │     │
         └─────┴─────┴─────┴─────┴─────┘
                            ↑
                        top = 2
                        (3 elements: 10, 20, 30)

LOW address                             HIGH address
(Bottom)                                (Top grows here)

BPSC KEY FACT: Stack grows from LOW address to HIGH address
               (In memory, stack typically grows DOWNWARD in actual OS)
               But for exam: TOP is where new elements go
```

---

## 📌 SECTION 14: QUICK FORMULA REFERENCE — STACK

```
╔═══════════════════════════════════════════════════════════╗
║              STACK QUICK REFERENCE                        ║
╠═══════════════════════════════════════════════════════════╣
║ Empty condition  : top == -1                              ║
║ Full condition   : top == MAX_SIZE - 1                    ║
║ Push             : top++; stack[top] = x                  ║
║ Pop              : x = stack[top]; top--                  ║
║ Peek             : return stack[top] (no change to top)   ║
║ All operations   : O(1) time                              ║
║ Space complexity : O(n)                                   ║
║ Tower of Hanoi   : 2^n - 1 moves                          ║
║ LIFO principle   : Last In First Out                      ║
║ DFS uses         : STACK                                  ║
║ BFS uses         : QUEUE                                  ║
╚═══════════════════════════════════════════════════════════╝
```

---

## 🔑 CS TOPPER QUICK REVISION BULLETS

1. **Stack = LIFO** (Last In, First Out)
2. **Empty stack condition: top = -1**; Full stack: top = MAX_SIZE - 1
3. **OVERFLOW** = Push on full stack | **UNDERFLOW** = Pop from empty stack
4. **All Stack operations = O(1)** time complexity
5. **Recursion uses STACK** (call stack / activation records)
6. **DFS uses STACK**, BFS uses QUEUE
7. **Symbol balancing (brackets) uses STACK**
8. **Asynchronous data transfer uses QUEUE** — NOT stack
9. **Tower of Hanoi: minimum moves = 2^n - 1**
10. **String reversal uses Stack** (LIFO reverses order)
11. **Infix to Postfix conversion uses Stack** (Day 17 detail)
12. **C++ STL Stack:** top() for peek, pop() to remove, push() to insert

---

---

# ═══════════════════════════════════════════════════
# 🗺️  PART B — GENERAL STUDIES
##  Bihar Geography Part 2: Economy, Important Districts
##  (Rohtas, Bhagalpur, Gaya, Nalanda, Champaran & More)
##  + Bihar Polity & Government Basics
# ═══════════════════════════════════════════════════

---

> **⚡ BPSC TRE FACT:** After Bihar Geography basics (Day 15), today we go DEEPER.
> District-specific questions, Bihar's economy, industries, government — all tested!

---

## 📌 SECTION 1: ROHTAS DISTRICT — COMPLETE PROFILE (HIGH PYQ)

Rohtas is one of the most historically and economically important districts of Bihar.

```
ROHTAS DISTRICT — KEY FACTS
==============================
Division     : Patna Division
Location     : South-western Bihar
Border       : Jharkhand (south), UP (west)
River        : Son river flows through it
Headquarters : Sasaram (Rohtas HQ = Sasaram)

HISTORICAL SIGNIFICANCE:
→ Rohtasgarh Fort — medieval fort, one of India's strongest
  Built by: Sher Shah Suri (Farid Khan) used it as treasury
  Location: On Kaimur hills, 450 meters high
  Significance: Never captured by enemy — impregnable fort!

→ SASARAM — Capital of Sher Shah Suri's empire
  Tomb of Sher Shah Suri: GRAND MUGHAL-STYLE TOMB in Sasaram
  Built: 1545 AD | Architect: Aliwal Khan
  It is grander than Humayun's tomb (Delhi)!
  It stands in the middle of a lake — stunningly beautiful

→ Sher Shah Suri was born in Narnaul (Haryana)
  But his capital and tomb are in SASARAM, Bihar!

ECONOMIC SIGNIFICANCE:
→ Cement industry — Limestone deposits → Cement plants
  Dalmia Bharat Cement (Dalmianagar, Rohtas) — major plant
  ACC Cement, JK Cement — plants in Rohtas
  Rohtas = Bihar's CEMENT capital

→ DALMIANAGAR — Famous for:
  Cement, Paper, Sugar, Rayon (artificial silk) factories
  Was a major industrial township

MINERALS:
→ Limestone (most important)
→ Pyrite (iron sulfide — used in sulfuric acid)
→ Coal traces

SON RIVER: Flows through Rohtas → Arrah → joins Ganga
DURGAWATI DAM: On Durgawati river (tributary of Son) in Rohtas
```

> **🚨 PYQ:** "Tomb of Sher Shah Suri is located at?" → **Sasaram (Rohtas)**
> "Which district is known for cement industry in Bihar?" → **Rohtas**
> "Rohtasgarh Fort is on which hills?" → **Kaimur Hills**

---

## 📌 SECTION 2: KAIMUR DISTRICT — NEIGHBORING ROHTAS

```
KAIMUR DISTRICT
================
Division     : Patna Division
HQ           : Bhabua
Famous for   : Kaimur Wildlife Sanctuary
               Karakat — important town
               Telhar Falls (Karakat)
               Mundeshwari Temple (one of India's oldest active temples)

Mundeshwari Temple:
→ Located on Kaura hills, Kaimur
→ Dedicated to Shiva and Shakti
→ Dated 625 AD (some say earlier) — possibly India's oldest temple still in use
→ Archaeological Survey of India protected monument

Kaimur Plateau:
→ Extension of Vindhya range
→ Limestone deposits
→ Forested — tigers, leopards
```

---

## 📌 SECTION 3: BHAGALPUR DISTRICT — COMPLETE PROFILE (HIGH PYQ)

```
BHAGALPUR DISTRICT — KEY FACTS
================================
Division     : Bhagalpur Division
Location     : Eastern Bihar, on south bank of Ganga
HQ           : Bhagalpur city
Nickname     : "Silk City" / "City of Silk"

SILK INDUSTRY (Most Important):
→ Famous for TUSSAR SILK (also called Kosa/Eri silk)
→ Tussar silk = wild silk from Antheraea mylitta (moth)
→ Bhagalpuri silk sarees are world-famous
→ Has GI (Geographical Indication) Tag
→ NHDC and Silk Board support silk industry here

VIKRAMSHILA UNIVERSITY RUINS:
→ Located at Antichak village, Bhagalpur district
→ Founded by: Dharampala (Pala dynasty king), ~8th century AD
→ Was a major Buddhist university (rival of Nalanda)
→ Destroyed by Bakhtiyar Khilji, 1203 AD
→ Now an Archaeological Survey of India site

VIKRAMSHILA DOLPHIN SANCTUARY:
→ 50 km stretch of Ganga, Bhagalpur
→ Protects: Gangetic River Dolphin (Platanista gangetica)
→ India's National Aquatic Animal = Gangetic River Dolphin
→ India's FIRST dolphin sanctuary

GANGA BRIDGE:
→ Vikramshila Setu: Connects Bhagalpur to Naugachia
→ Important road connectivity

HISTORY:
→ Ancient name: Champa (capital of Anga Mahajanapada)
→ Anga was one of the 16 Mahajanapadas
→ Karna (from Mahabharata) was king of Anga kingdom
```

> **🚨 PYQ:** "Bhagalpur is famous for which industry?" → **Silk (Tussar Silk)**
> "Vikramshila University was founded by?" → **Dharampala (Pala dynasty)**
> "India's National Aquatic Animal?" → **Gangetic River Dolphin**

---

## 📌 SECTION 4: GAYA & BODH GAYA — COMPLETE PROFILE (HIGH PYQ)

```
GAYA DISTRICT — KEY FACTS
===========================
Division     : Magadh Division
HQ           : Gaya city
Famous for   : Hindu pilgrimage + Buddhist pilgrimage

HINDU SIGNIFICANCE:
→ VISHNUPAD TEMPLE: On Falgu river bank
  Temple: Dedicated to Lord Vishnu's footprint
  Very sacred — Hindus perform PIND DAAN (death rituals) here
  One of India's most important pilgrimage sites

→ FALGU RIVER flows through Gaya
  Associated with Ramayana — Sita cursed the Falgu river
  River appears dry on surface but water flows beneath

→ PITRIPAKSHA MELA (Shraddh Mela):
  Biggest annual fair in Gaya
  Lakhs come for Pind Daan during Pitripaksha (Shraddha period)
  15-day fair — huge religious event

BODH GAYA (within Gaya district):
→ Siddhartha Gautama attained enlightenment under Bodhi Tree
  (Ficus religiosa / Peepal tree) in 528 BC
→ MAHABODHI TEMPLE: UNESCO World Heritage Site (2002)
→ Bodhi Tree: Descendant of original Peepal tree still exists
→ International Buddhist center — pilgrims from Thailand, Japan, Sri Lanka
→ INTERNATIONAL AIRPORT at Gaya (flights from Southeast Asia)
→ Mahabodhi Society of India founded here by Anagarika Dharmapala

OTHER GAYA FACTS:
→ Rubber Institute of India (Kottayam in Kerala, not Gaya — don't confuse)
→ Gaya connects to NH-83 (Patna-Gaya)
→ Coal deposits in southern Gaya (Jehanabad border)
```

> **🚨 PYQ:** "Where did Gautama Buddha attain enlightenment?" → **Bodh Gaya (under Bodhi Tree)**
> "Mahabodhi Temple is a UNESCO World Heritage Site in?" → **Bodh Gaya, Gaya district**
> "Pind Daan is performed at?" → **Gaya (Vishnupad Temple, on Falgu river)**

---

## 📌 SECTION 5: NALANDA DISTRICT — ANCIENT UNIVERSITY (HIGH PYQ)

```
NALANDA DISTRICT — KEY FACTS
==============================
Division     : Magadh Division
HQ           : Biharsharif
Famous for   : Ancient Nalanda University (World Heritage Site)

NALANDA UNIVERSITY (Ancient):
→ Founded: ~5th century AD (Gupta period)
   Some say Kumaragupta I founded it (~415–455 AD)
→ Peak period: 5th–12th century AD
→ One of world's FIRST residential universities
→ Students: 10,000+ students, 2,000 teachers
→ Subjects: Buddhism, Vedas, Logic, Grammar, Medicine, Astronomy
→ Famous visitors:
   Hiuen Tsang (Chinese scholar, 7th century) — spent 12 years
   I-Tsing (another Chinese pilgrim)
   Atisha Dipankara (went from here to Tibet)

DESTRUCTION:
→ Destroyed by: BAKHTIYAR KHILJI in 1193 AD
   He burnt the library — "Dharmaganja" (Dharma Treasure)
   Library was so large it burnt for 3 months!
   This was the end of ancient Nalanda

UNESCO RECOGNITION:
→ Nalanda Mahavihara ruins: UNESCO World Heritage Site (2016)

NEW NALANDA UNIVERSITY (MODERN):
→ Re-established in 2010 by Indian Parliament (Nalanda University Act)
→ Located near original site
→ International university with foreign faculty
→ Inaugurated campus: 2024 (PM Modi inaugurated)

RAJGIR (in Nalanda district):
→ Ancient capital of Magadha Kingdom
→ First Buddhist Council held here (487 BC, after Buddha's death)
→ Ratna Giri, Vipula, Vaibhara — five hills of Rajgir
→ Hot springs (Brahma Kund) — mineral water, pilgrims
→ Glass bridge (skywalk) — modern tourist attraction
→ Vishwa Shanti Stupa (Peace Pagoda)
→ Cyclopean wall — world's oldest stone wall
```

> **🚨 PYQ:** "Nalanda University was destroyed by?" → **Bakhtiyar Khilji (1193 AD)**
> "First Buddhist Council was held at?" → **Rajgir (Rajagriha)**
> "Hiuen Tsang visited which Indian university?" → **Nalanda University**

---

## 📌 SECTION 6: VAISHALI DISTRICT — WORLD'S FIRST REPUBLIC

```
VAISHALI DISTRICT — KEY FACTS
===============================
Division     : Muzaffarpur (Tirhut) Division
HQ           : Hajipur
Famous for   : World's First Republic + Jainism's Mahavira

HAJIPUR:
→ On NORTH bank of Ganga (opposite Patna)
→ Mahatma Gandhi Setu connects Hajipur to Patna
→ Junction of Ganga and Gandak rivers
→ Railway junction (Hajipur Jn.)
→ Famous for: Banana (Chita banana) cultivation

VAISHALI (town):
→ Capital of LICHCHHAVI Republic (Vajji Confederacy)
→ World's FIRST democratic republic (6th century BC)
→ "Vaishali" → one of world's first functional republics
→ The Lichchhavis had an elected assembly (Sabhas)

MAHAVIRA (Jainism):
→ Born at Kundagram, VAISHALI (599 BC)
→ 24th and last Tirthankara of Jainism
→ Real name: Vardhamana
→ Attained Moksha (liberation) at Pawapuri (Nalanda district)
→ Pawapuri is the Jain equivalent of Bodh Gaya

BUDDHA:
→ Buddha delivered his LAST SERMON at Vaishali
→ He announced his approaching Parinirvana here
→ Ananda Stupa (contains Buddha's relics) at Vaishali

ASHOKA PILLAR at Vaishali:
→ One of the best preserved Ashoka Pillars
→ Single lion capital (NOT four lions like Sarnath)
→ Made of polished sandstone

BANANA: Hajipur is famous for → "Chita" (local banana variety)
```

> **🚨 PYQ:** "World's first republic was?" → **Vaishali (Lichchhavi/Vajji)**
> "Birthplace of Mahavira?" → **Kundagram, Vaishali**
> "Mahavira attained Moksha at?" → **Pawapuri (Nalanda district)**

---

## 📌 SECTION 7: CHAMPARAN — GANDHI'S FIRST SATYAGRAHA

```
CHAMPARAN DISTRICTS — KEY FACTS
=================================
There are TWO Champaran districts:

1. WEST CHAMPARAN (Pashchim Champaran):
   HQ: Bettiah
   Famous: Valmiki National Park (Bihar's only Tiger Reserve)
            Gandhi's Champaran Satyagraha (1917)
            Bettiah Raj (historical kingdom)
            Valmikingaar Wildlife Sanctuary
            Border: Nepal (north), Gandak river (east)

2. EAST CHAMPARAN (Purvi Champaran):
   HQ: Motihari
   Famous: George Orwell (author of "Animal Farm" & "1984") born here!
            Gandhi's Champaran Satyagraha started here
            Bapudham Motihari (Gandhi memorial)
            Sugarcane farming and sugar mills

CHAMPARAN SATYAGRAHA (1917):
→ Gandhi's FIRST Satyagraha in India
→ Issue: Tinkathia system (farmers forced to grow indigo on 3/20 of land)
→ British planters forced farmers to grow indigo
→ Gandhi arrived: April 10, 1917
→ Result: Champaran Agrarian Act (1917) — Tinkathia system abolished
→ This gave Gandhi confidence for future national movements

KEY PEOPLE in Champaran Satyagraha:
→ Gandhi, Rajendra Prasad, J.B. Kripalani, Mahadev Desai
→ All came to Champaran to support farmers
```

> **🚨 PYQ:** "Gandhi's first Satyagraha in India?" → **Champaran Satyagraha (1917)**
> "What was the Tinkathia system?" → Farmers forced to grow indigo on 3/20 of land
> "George Orwell was born in?" → **Motihari, East Champaran, Bihar**

---

## 📌 SECTION 8: MUZAFFARPUR DISTRICT

```
MUZAFFARPUR DISTRICT — KEY FACTS
===================================
Division     : Tirhut (Muzaffarpur) Division
Location     : North Bihar, on Gandak + Bagmati rivers
Famous for   : SHAHI LITCHI (most important!)

SHAHI LITCHI:
→ Muzaffarpur is called "LITCHI KINGDOM" of India
→ Shahi Litchi has GI (Geographical Indication) Tag
→ Best quality litchi in the world — fleshy, sweet
→ Season: May–June
→ Exported to UAE, UK, Netherlands, Germany
→ Muzaffarpur litchi is used in premium products

OTHER FACTS:
→ Second largest city of Bihar
→ Tirhut is a cultural region — Muzaffarpur is its capital
→ Brajkishore Prasad (freedom fighter) — from Muzaffarpur
→ Surya Narayan Singh (UP CM) connection
→ Chandrakishore Prasad — famous from Bihar
→ L.N. Mithila University — located at Darbhanga (nearby)

FLOODS:
→ Muzaffarpur is frequently flooded by Gandak and Bagmati rivers
→ Major flood-affected district
```

---

## 📌 SECTION 9: BIHAR'S ECONOMY — KEY INDUSTRIES

```
BIHAR'S INDUSTRIAL PROFILE
============================

Bihar is primarily an AGRICULTURAL STATE.
Industrial development is limited compared to other states.

MAJOR INDUSTRIES:
1. SUGAR INDUSTRY:
   → Bihar = major sugarcane producer
   → Sugar mills in: Champaran (W & E), Saran, Muzaffarpur, Darbhanga
   → After separation from Jharkhand, sugar became #1 industry
   → Sugarcane → Sugar + Molasses → Alcohol/Ethanol

2. CEMENT INDUSTRY:
   → Concentrated in ROHTAS district
   → Limestone deposits in Kaimur/Rohtas → Cement plants
   → Plants: Dalmia Bharat, ACC, JK Cement (all in Rohtas)
   → Dalmianagar industrial township

3. SILK INDUSTRY:
   → BHAGALPUR = Silk City (Tussar silk)
   → GI tagged Bhagalpuri silk sarees
   → Traditional cottage industry

4. JUTE INDUSTRY:
   → Kosi region (Saharsa, Supaul, Darbhanga)
   → Bihar = jute producing state (smaller than West Bengal)

5. FOOD PROCESSING:
   → Litchi processing (Muzaffarpur)
   → Makhana (Fox nut) processing (Darbhanga, Madhubani, Sitamarhi)
   → Potato chips/processing (Nalanda)
   → Banana (Hajipur)

6. LEATHER INDUSTRY:
   → Muzaffarpur has some leather work
   → Small-scale cottage industry

7. BISCUIT/BAKERY:
   → Patna has several biscuit factories (Parle, etc.)

INDUSTRIAL CORRIDORS:
→ Patna-Gaya Industrial Corridor (proposed)
→ Amritsar-Kolkata Industrial Corridor passes through Bihar
   (through Patna, Gaya, Danapur area)
```

---

## 📌 SECTION 10: BIHAR'S FAMOUS PERSONALITIES (PYQ-TESTED)

```
FAMOUS PERSONALITIES FROM BIHAR
==================================

POLITICAL:
→ Dr. Rajendra Prasad      : 1st President of India (born: Ziradei, Siwan)
→ Jayaprakash Narayan (JP) : "Lok Nayak" — born Sitab Diara, Saran
                              Led JP Movement (1974) against emergency
→ Karpoori Thakur          : Former CM Bihar, "Jan Nayak"
                              Bharat Ratna 2024 (posthumously)
→ Babu Jagjivan Ram        : Born Chandwa, Bhojpur district
                              Deputy PM of India

LITERATURE/ART:
→ Vidyapati                : Medieval poet, Maithili language
                              "Shakespeare of Mithila"
→ Ramdhari Singh Dinkar    : "Rashtriya Kavi" (National Poet)
                              Born: Begusarai | Works: Rashmirathi, Urvashi
                              Jnanpith Award winner
→ Phagu Chauhan            : 29th Governor of Bihar (2019)

SCIENCE:
→ Aryabhata                : Ancient mathematician (from Pataliputra)
                              Calculated value of π (pi), heliocentric theory
→ Mahendra Lal Sircar      : Scientist, founded Indian Association for
                              Cultivation of Science

FREEDOM FIGHTERS from Bihar:
→ Kunwar Singh             : Led 1857 revolt in Bihar (Jagdishpur, Bhojpur)
→ Gandhi's key Bihar associates: Rajendra Prasad, J.B. Kripalani
```

> **🚨 PYQ:** "First President of India?" → **Dr. Rajendra Prasad** (from Siwan, Bihar)
> "Lok Nayak = ?" → **Jayaprakash Narayan** (born Saran, Bihar)
> "Rashtriya Kavi Ramdhari Singh Dinkar was from?" → **Begusarai, Bihar**

---

## 📌 SECTION 11: BIHAR GOVERNMENT — POLITY BASICS

```
BIHAR GOVERNMENT STRUCTURE
============================

TYPE: Parliamentary Democracy (Bicameral Legislature)

LEGISLATURE:
→ Vidhan Sabha (Lower House):
  Seats: 243 | Elected by people
  Leader: Chief Minister
  
→ Vidhan Parishad (Upper House):
  Seats: 75 | Partially elected, partially nominated
  Chairman: Vidhan Parishad Chairman
  Bihar is one of FEW states with BOTH houses

CURRENT POLITICAL:
→ Capital: Patna
→ Governor: Appointed by President of India
→ Current CM: Nitish Kumar (JD-U) [verify with latest data]

HIGH COURT:
→ Patna High Court: Established 1916
   Jurisdiction: Bihar AND Jharkhand (shared after 2000)
   Actually: After 2000, Jharkhand HC was formed separately
   Patna HC now handles Bihar only

IMPORTANT CONSTITUTIONAL ARTICLES FOR BIHAR:
→ Art 153: Governor of State
→ Art 163: Council of Ministers in State
→ Art 164: CM appointed by Governor
→ Art 168: Legislature of States
→ Art 170: Composition of Vidhan Sabha
→ Art 171: Composition of Vidhan Parishad

PANCHAYATI RAJ IN BIHAR:
→ 3-tier system: Gram Panchayat → Panchayat Samiti → Zila Parishad
→ 73rd Constitutional Amendment (1992) provides basis
→ Bihar has 8,386+ Gram Panchayats
→ Reservation for women: 50% (Bihar gives 50% to women in PRI)
   Bihar increased women's reservation to 50% — one of highest in India!
```

---

## 📌 SECTION 12: MITHILA REGION — CULTURAL GEOGRAPHY (PYQ)

```
MITHILA REGION
================
Area: Northern Bihar + parts of Nepal
Cultural identity: Maithili language, Madhubani art

DISTRICTS IN MITHILA:
→ Darbhanga (Cultural capital of Mithila)
→ Madhubani (Art capital)
→ Sitamarhi (Birthplace of Sita)
→ Muzzafarpur
→ Samastipur
→ Begusarai (partially)

DARBHANGA:
→ L.N. Mithila University (B.R.A. Bihar University is another major uni)
→ Kamla river passes through
→ Famous for: Darbhanga Raj (zamindari family) — had huge palaces
→ Darbhanga Airport (recently expanded)
→ Music: Maithili folk music tradition

MADHUBANI PAINTING:
→ Originated in Madhubani district (Mithila region)
→ Also called: MITHILA PAINTING
→ Characters: Hindu gods, nature, folk stories
→ Colors: Natural pigments (turmeric, cow dung, flowers)
→ Medium: Cloth, paper, walls (originally on mud walls)
→ Famous Mithila artists: Sita Devi, Ganga Devi, Baua Devi
→ GI Tag: Madhubani Painting has Geographical Indication Tag
→ Now used in: Sarees, pottery, objects (beyond walls)

SITAMARHI:
→ Believed to be birthplace of Sita (Ramayana)
→ Janaki temple (dedicated to Sita)
→ Bagmati river flows through
→ Famous for: Vivah Panchami Mela (marriage of Rama and Sita)

MAKHANA (FOX NUT):
→ Grown in: Darbhanga, Madhubani, Sitamarhi, Supaul districts
→ Bihar = 90%+ of world Makhana production
→ GI Tag for Mithila Makhana
→ Aquatic crop — grows in water (ponds, lakes)
→ Nutritional: High protein, low fat — superfood
→ Used in: Kheer, prasad, snacks, namkeen
→ Exported to: USA, UK, Australia, Gulf countries
```

---

## 📌 SECTION 13: IMPORTANT FAIRS & FESTIVALS OF BIHAR (PYQ)

```
MAJOR FAIRS AND FESTIVALS
===========================

Fair/Festival         | Location           | When           | Significance
──────────────────────|────────────────────|────────────────|──────────────────────
Sonepur Mela          | Sonepur (Vaishali) | Kartik Purnima | Largest cattle fair in Asia
                      |                    | (Nov)          | Ganga-Gandak confluence
Pitripaksha Mela      | Gaya               | Pitripaksha    | Pind Daan, 15 days
                      |                    | (Sep-Oct)      | Hindu funeral rites
Chhath Puja           | Across Bihar       | Kartik         | Sun worship, Bihar's
                      |                    | (Oct-Nov)      | most important festival!
Vivah Panchami Mela   | Sitamarhi          | Aghan Panchami | Rama-Sita marriage
Boudh Mahotsav        | Bodh Gaya          | Nov-Dec        | Buddhist pilgrimage
Rajgir Mahotsav       | Rajgir             | October        | Cultural festival
Mithila Mahotsav      | Madhubani/         | Jan-Feb        | Mithila art and culture
                      | Darbhanga          |                |

CHHATH PUJA — Most Important Bihar Festival:
→ Sun God (Surya) and Chhathi Maiya (Usha) worshipped
→ Unique: Rituals performed AT RIVERBANKS/WATER BODIES
→ No idol worship — direct sun worship
→ 4-day festival (fasting, bathing in Ganga/ponds)
→ Known for: Setting sun (Sandhya Arghya) and Rising sun (Usha Arghya)
→ UNESCO Intangible Cultural Heritage (being considered)
→ Celebrated by Bihari diaspora worldwide — even in Fiji!
```

---

## 📌 SECTION 14: GS TOPPER QUICK REVISION BULLETS

1. **Rohtas = Bihar's cement capital; Tomb of Sher Shah Suri at Sasaram**
2. **Bhagalpur = Silk City (Tussar silk, GI Tag); Vikramshila University ruins here**
3. **Buddha attained enlightenment at Bodh Gaya; Mahabodhi Temple = UNESCO WHSite**
4. **Nalanda University destroyed by Bakhtiyar Khilji (1193 AD); ruins = UNESCO WHSite**
5. **Vaishali = World's first republic (Lichchhavi); Mahavira born here**
6. **Gandhi's 1st Satyagraha = Champaran (1917), tinkathia system**
7. **Muzaffarpur = Litchi Kingdom (Shahi Litchi, GI Tag)**
8. **Bihar's most important festival = CHHATH PUJA (Sun worship)**
9. **Sonepur Mela = Asia's largest cattle fair, Ganga-Gandak confluence**
10. **Makhana (Fox Nut) = Bihar produces 90% of world's supply, GI Tag**
11. **Rajendra Prasad = 1st President of India, from Siwan, Bihar**
12. **JP Narayan = "Lok Nayak", from Saran, Bihar**
13. **Ramdhari Singh Dinkar = National Poet, from Begusarai, Bihar**
14. **Rajgir = First Buddhist Council (487 BC) held here**
15. **Patna High Court established 1916 — one of oldest in India**
16. **Bihar Vidhan Parishad has 75 seats; Vidhan Sabha has 243 seats**
17. **Bihar = 50% women's reservation in Panchayati Raj (one of highest)**
18. **Rohtasgarh Fort on Kaimur Hills — never captured by enemy**
19. **Mundeshwari Temple (Kaimur) = possibly India's oldest active temple**
20. **Vikramshila University founded by Dharampala (Pala dynasty)**

---

---

# ═══════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 16
## ⚠️ Attempt ALL 50 questions FIRST. Answers are at the VERY END!
## DO NOT peek at answers before attempting!
# ═══════════════════════════════════════════════════

---

> **BPSC TRE 5-Option Format:**
> (A), (B), (C), (D) More than one of the above, (E) None of the above

---

## 🖥️ CS PRACTICE QUESTIONS — STACK (Q1–Q25)

---

**Q1.** Which principle does a Stack data structure follow?

(A) FILO — First In Last Out
(B) FIFO — First In First Out
(C) LILO — Last In Last Out
(D) More than one of the above
(E) LIFO — Last In First Out

---

**Q2.** What condition indicates that a stack implemented using an array is EMPTY?

(A) top == 0
(B) top == MAX_SIZE
(C) top == 1
(D) More than one of the above
(E) top == -1

---

**Q3.** Which of the following is/are APPLICATIONS of Stack?

(A) Recursion (function call management)
(B) Balancing of parentheses
(C) Infix to Postfix conversion
(D) More than one of the above
(E) None of the above

---

**Q4.** What is STACK OVERFLOW?

(A) Popping from an empty stack
(B) Accessing a stack element by index
(C) Searching in a stack
(D) More than one of the above
(E) Pushing onto a full stack

---

**Q5.** What is the time complexity of PUSH and POP operations on a stack?

(A) O(n)
(B) O(log n)
(C) O(n²)
(D) More than one of the above
(E) O(1)

---

**Q6.** Which data structure is used INTERNALLY by Recursion?

(A) Queue
(B) Array
(C) Linked List
(D) More than one of the above
(E) Stack

---

**Q7.** Which of the following is NOT an application of Stack?

(A) String reversal
(B) Undo operation in text editor
(C) Asynchronous data transfer between processes
(D) More than one of the above
(E) None of the above

---

**Q8.** In a stack of size MAX = 5, after pushing elements 10, 20, 30, 40, 50, what is the value of 'top'?

(A) 5
(B) 3
(C) 0
(D) More than one of the above
(E) 4

---

**Q9.** Elements are pushed onto a stack in the order: 5, 10, 15, 20. What will be the output when ALL elements are popped one by one?

(A) 5, 10, 15, 20
(B) 20, 10, 15, 5
(C) 5, 15, 10, 20
(D) More than one of the above
(E) 20, 15, 10, 5

---

**Q10.** For the Tower of Hanoi problem with n = 4 disks, the minimum number of moves required is:

(A) 8
(B) 16
(C) 4
(D) More than one of the above
(E) 15

---

**Q11.** Which traversal algorithm uses a STACK (either explicitly or via recursion)?

(A) BFS (Breadth First Search)
(B) Level Order Traversal
(C) DFS (Depth First Search)
(D) More than one of the above
(E) None of the above

---

**Q12.** The PEEK (or TOP) operation in a stack:

(A) Removes the top element and returns it
(B) Inserts a new element at top
(C) Checks if stack is empty
(D) More than one of the above
(E) Returns the top element WITHOUT removing it

---

**Q13.** What happens when you try to POP from an empty stack?

(A) Stack Overflow
(B) The stack returns 0
(C) The stack returns NULL
(D) More than one of the above
(E) Stack Underflow

---

**Q14.** Which of the following correctly describes the order of operations when checking brackets for "{[()]}"?

(A) All brackets are pushed; LIFO order ensures proper matching
(B) Opening brackets are pushed; closing brackets trigger POP and match
(C) Queue is used to match opening and closing brackets
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the output of the following stack operations?
Push(1), Push(2), Push(3), Pop(), Push(4), Pop(), Pop()

(A) 3, 4, 2
(B) 1, 2, 3
(C) 3, 2, 1
(D) More than one of the above
(E) 4, 3, 1

---

**Q16.** In C++ STL, which method is used to view the top element of a stack WITHOUT removing it?

(A) peek()
(B) pop()
(C) front()
(D) More than one of the above
(E) top()

---

**Q17.** Which condition indicates a FULL stack (array-based, size MAX)?

(A) top == -1
(B) top == 0
(C) top == 1
(D) More than one of the above
(E) top == MAX - 1

---

**Q18.** A string "BPSC" is pushed character by character onto a stack. What is the output when all characters are popped?

(A) BPSC
(B) CPBS
(C) SCPB
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following applications uses QUEUE and NOT Stack?

(A) Undo-Redo in text editor
(B) Expression evaluation (postfix)
(C) CPU scheduling (Round Robin)
(D) More than one of the above
(E) None of the above

---

**Q20.** In a recursive function, each function call creates an ACTIVATION RECORD. These records are stored in:

(A) Heap memory (dynamic)
(B) Hard disk
(C) Queue
(D) More than one of the above
(E) Call Stack (Stack memory)

---

**Q21.** Consider the stack operations: Push(A), Push(B), Pop(), Push(C), Push(D), Pop(), Pop(). What are the popped elements in order?

(A) B, C, D
(B) A, B, C
(C) B, D, C
(D) More than one of the above
(E) None of the above

---

**Q22.** Tower of Hanoi with 3 disks requires minimum _____ moves:

(A) 6
(B) 9
(C) 3
(D) More than one of the above
(E) 7

---

**Q23.** Which of the following statement(s) about Stack is/are TRUE?

(A) Insertion in Stack is called PUSH
(B) Deletion from Stack is called POP
(C) Stack follows LIFO principle
(D) More than one of the above
(E) None of the above

---

**Q24.** Backtracking in maze-solving uses which data structure?

(A) Queue
(B) Array
(C) Linked List
(D) More than one of the above
(E) Stack

---

**Q25.** What is the correct sequence for PUSH operation before inserting element x in an array-based stack?

(A) Check UNDERFLOW, then insert
(B) Check OVERFLOW, increment top, then insert x at stack[top]
(C) Insert x first, then increment top
(D) More than one of the above
(E) None of the above

---

---

## 🗺️ GS PRACTICE QUESTIONS — BIHAR (Q26–Q50)

---

**Q26.** The Tomb of Sher Shah Suri is located in which city/district of Bihar?

(A) Patna
(B) Gaya
(C) Munger
(D) More than one of the above
(E) Sasaram (Rohtas district)

---

**Q27.** Bhagalpur is famous for which type of silk?

(A) Mulberry Silk
(B) Muga Silk
(C) Eri Silk
(D) More than one of the above
(E) Tussar (Tussah/Kosa) Silk

---

**Q28.** The ancient Vikramshila University was founded by which ruler?

(A) Ashoka (Maurya dynasty)
(B) Chandragupta II (Gupta dynasty)
(C) Harshavardhana
(D) More than one of the above
(E) Dharampala (Pala dynasty)

---

**Q29.** The Mahabodhi Temple at Bodh Gaya was granted UNESCO World Heritage Site status in which year?

(A) 1986
(B) 2016
(C) 1993
(D) More than one of the above
(E) 2002

---

**Q30.** The ancient Nalanda University was destroyed by which invader?

(A) Mahmud of Ghazni
(B) Timur (Tamerlane)
(C) Muhammad bin Qasim
(D) More than one of the above
(E) Bakhtiyar Khilji (1193 AD)

---

**Q31.** Vaishali (Bihar) is historically significant as:

(A) The world's first democratic republic (Lichchhavi Mahajanapada)
(B) Birthplace of Mahavira, 24th Tirthankara of Jainism
(C) Place where Buddha delivered his last sermon
(D) More than one of the above
(E) None of the above

---

**Q32.** The Champaran Satyagraha of 1917 was related to:

(A) Salt tax protest
(B) Forced cultivation of indigo (Tinkathia system)
(C) Non-payment of land revenue
(D) More than one of the above
(E) None of the above

---

**Q33.** Which city is known as the "Litchi Kingdom" of India and produces Shahi Litchi with a GI Tag?

(A) Bhagalpur
(B) Gaya
(C) Patna
(D) More than one of the above
(E) Muzaffarpur

---

**Q34.** Bihar's most important festival, Chhath Puja, is associated with the worship of:

(A) Lord Shiva
(B) Lord Vishnu
(C) Goddess Durga
(D) More than one of the above
(E) Sun God (Surya)

---

**Q35.** The First Buddhist Council after the death of Gautama Buddha was held at:

(A) Bodh Gaya
(B) Sarnath
(C) Vaishali
(D) More than one of the above
(E) Rajgir (Rajagriha)

---

**Q36.** Who was the first President of India, born in Bihar?

(A) Jawaharlal Nehru
(B) S. Radhakrishnan
(C) V.V. Giri
(D) More than one of the above
(E) Dr. Rajendra Prasad

---

**Q37.** Bihar produces approximately what percentage of the world's Makhana (Fox Nut)?

(A) 40%
(B) 60%
(C) 75%
(D) More than one of the above
(E) Over 90%

---

**Q38.** The Sonepur Mela (Asia's largest cattle fair) is held at the confluence of which two rivers?

(A) Ganga and Kosi
(B) Son and Ganga
(C) Gandak and Son
(D) More than one of the above
(E) Ganga and Gandak

---

**Q39.** Jayaprakash Narayan (JP), known as "Lok Nayak," was born in which district of Bihar?

(A) Patna
(B) Muzaffarpur
(C) Darbhanga
(D) More than one of the above
(E) Saran (Sitab Diara village)

---

**Q40.** The Rohtasgarh Fort is situated on which hills?

(A) Rajmahal Hills
(B) Vindhya Hills
(C) Shivalik Hills
(D) More than one of the above
(E) Kaimur Hills

---

**Q41.** Which district of Bihar is known for Madhubani Painting (Mithila Art) that has a GI Tag?

(A) Sitamarhi
(B) Vaishali
(C) Bhagalpur
(D) More than one of the above
(E) Madhubani

---

**Q42.** The Falgu River (associated with Hindu pilgrimage) flows through which city of Bihar?

(A) Patna
(B) Muzaffarpur
(C) Vaishali
(D) More than one of the above
(E) Gaya

---

**Q43.** Bihar's state legislature consists of:

(A) Only Vidhan Sabha (unicameral)
(B) Vidhan Sabha + Rajya Sabha
(C) Only Vidhan Parishad
(D) More than one of the above
(E) Vidhan Sabha + Vidhan Parishad (bicameral)

---

**Q44.** The National Aquatic Animal of India, protected at Vikramshila Sanctuary in Bhagalpur, is:

(A) Irrawaddy Dolphin
(B) Dugong
(C) Blue Whale
(D) More than one of the above
(E) Gangetic River Dolphin

---

**Q45.** Which of the following is/are GI (Geographical Indication) Tagged products from Bihar?

(A) Shahi Litchi (Muzaffarpur)
(B) Madhubani Painting (Madhubani)
(C) Bhagalpuri Silk (Bhagalpur)
(D) More than one of the above
(E) None of the above

---

**Q46.** The poet Ramdhari Singh "Dinkar," also called "Rashtriya Kavi" (National Poet), belonged to which district of Bihar?

(A) Patna
(B) Darbhanga
(C) Muzaffarpur
(D) More than one of the above
(E) Begusarai (Simaria village)

---

**Q47.** Mahavira, the 24th Tirthankara of Jainism, attained Moksha (liberation) at:

(A) Vaishali
(B) Bodh Gaya
(C) Rajgir
(D) More than one of the above
(E) Pawapuri (Nalanda district)

---

**Q48.** Bihar's CEMENT industry is primarily concentrated in which district?

(A) Patna
(B) Gaya
(C) Muzaffarpur
(D) More than one of the above
(E) Rohtas (Dalmianagar/Sasaram area)

---

**Q49.** The Patna High Court was established in the year:

(A) 1947
(B) 1950
(C) 1935
(D) More than one of the above
(E) 1916

---

**Q50.** Which of the following statements about Bihar are CORRECT?

(A) Bihar has 50% reservation for women in Panchayati Raj Institutions
(B) Bihar has a bicameral legislature (Vidhan Sabha + Vidhan Parishad)
(C) Rajendra Prasad, India's first President, was born in Bihar
(D) More than one of the above
(E) None of the above

---

---

# ═══════════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 16
### ⚠️ SCROLL DOWN ONLY AFTER ATTEMPTING ALL 50 QUESTIONS!
# ═══════════════════════════════════════════════════

---

```
╔═══╦═══════╦═══╦═══════╦═══╦═══════╦═══╦═══════╦═══╦═══════╗
║ Q ║ ANS   ║ Q ║ ANS   ║ Q ║ ANS   ║ Q ║ ANS   ║ Q ║ ANS   ║
╠═══╬═══════╬═══╬═══════╬═══╬═══════╬═══╬═══════╬═══╬═══════╣
║ 1 ║  (E)  ║ 11║  (C)  ║ 21║  (C)  ║ 31║  (D)  ║ 41║  (E)  ║
║ 2 ║  (E)  ║ 12║  (E)  ║ 22║  (E)  ║ 32║  (B)  ║ 42║  (E)  ║
║ 3 ║  (D)  ║ 13║  (E)  ║ 23║  (D)  ║ 33║  (E)  ║ 43║  (E)  ║
║ 4 ║  (E)  ║ 14║  (B)  ║ 24║  (E)  ║ 34║  (E)  ║ 44║  (E)  ║
║ 5 ║  (E)  ║ 15║  (A)  ║ 25║  (B)  ║ 35║  (E)  ║ 45║  (D)  ║
║ 6 ║  (E)  ║ 16║  (E)  ║ 26║  (E)  ║ 36║  (E)  ║ 46║  (E)  ║
║ 7 ║  (C)  ║ 17║  (E)  ║ 27║  (E)  ║ 37║  (E)  ║ 47║  (E)  ║
║ 8 ║  (E)  ║ 18║  (C)  ║ 28║  (E)  ║ 38║  (E)  ║ 48║  (E)  ║
║ 9 ║  (E)  ║ 19║  (C)  ║ 29║  (E)  ║ 39║  (E)  ║ 49║  (E)  ║
║10 ║  (E)  ║ 20║  (E)  ║ 30║  (E)  ║ 40║  (E)  ║ 50║  (D)  ║
╚═══╩═══════╩═══╩═══════╩═══╩═══════╩═══╩═══════╩═══╩═══════╝
```

---

## 📖 DETAILED EXPLANATIONS

---

### CS EXPLANATIONS:

**Q1 → (E) LIFO**
Stack follows LIFO — Last In, First Out. The most recently inserted element is the first to be removed. Note: FILO (First In Last Out) means the same thing as LIFO, so technically (A) and (E) both mean the same. However, the standard accepted name is **LIFO**, so (E) is the expected answer in BPSC.

**Q2 → (E) top == -1**
In an array-based stack, the `top` variable is initialized to -1 (meaning no elements). When top = -1, the stack is empty.

**Q3 → (D) More than one**
All three: (A) Recursion, (B) Balancing of parentheses, (C) Infix to Postfix conversion — are ALL valid stack applications. So the answer is (D).

**Q4 → (E) Pushing onto a FULL stack**
Overflow = pushing onto a stack that has no more space (top == MAX-1). Underflow is the opposite (popping empty stack).

**Q5 → (E) O(1)**
Both PUSH and POP only modify the `top` pointer and access one element — constant time regardless of stack size.

**Q6 → (E) Stack**
Recursion internally uses the **call stack** (also called function call stack or runtime stack). Each recursive call pushes an activation record onto the stack.

**Q7 → (C) Asynchronous data transfer between processes**
Asynchronous data transfer uses **QUEUE** (FIFO), not Stack. All others (string reversal, undo) are Stack applications.

**Q8 → (E) 4**
MAX = 5, so indices are 0, 1, 2, 3, 4. After pushing 5 elements, top = 4 (= MAX - 1 = 5 - 1 = 4). Stack is now full.

**Q9 → (E) 20, 15, 10, 5**
Push order: 5 → 10 → 15 → 20 (20 is at top). Pop order (LIFO): 20 first, then 15, then 10, then 5.

**Q10 → (E) 15**
Formula: 2^n - 1 = 2^4 - 1 = 16 - 1 = **15 moves**.

**Q11 → (C) DFS**
DFS uses a Stack (either an explicit stack or recursion which internally uses stack). BFS uses Queue. Level Order Traversal uses Queue.

**Q12 → (E) Returns the top element WITHOUT removing it**
PEEK/TOP operation only reads the top element. It does NOT modify the stack. This is how UNDO previews the last action before undoing.

**Q13 → (E) Stack Underflow**
Popping from an empty stack (top == -1) causes **Stack Underflow** — a runtime error.

**Q14 → (B)**
The correct algorithm: Opening brackets `{`, `[`, `(` are PUSHED; when closing bracket `)`, `]`, `}` is encountered, POP and check if it matches. If yes → continue; if no → unbalanced.

**Q15 → (A) 3, 4, 2**
Let's trace:
- Push(1): Stack [1], top=0
- Push(2): Stack [1,2], top=1
- Push(3): Stack [1,2,3], top=2
- Pop(): Removes 3, **output: 3**. Stack [1,2], top=1
- Push(4): Stack [1,2,4], top=2
- Pop(): Removes 4, **output: 4**. Stack [1,2], top=1
- Pop(): Removes 2, **output: 2**. Stack [1], top=0
Output sequence: **3, 4, 2** → Answer (A) ✓

**Q16 → (E) top()**
In C++ STL `stack<T>`, the method to peek (view without removing) is `top()`. There is no `peek()` method in C++ STL stack.

**Q17 → (E) top == MAX - 1**
Full condition: top has reached the last valid index (MAX - 1). If MAX = 5, full when top = 4.

**Q18 → (C) SCPB**
Push: B → P → S → C (C is at top). Pop (LIFO): C, S, P, B → Output string: "CSPB"

**Q19 → (C) CPU scheduling (Round Robin)**
CPU scheduling uses Queue (FIFO). Undo-Redo uses Stack. Expression evaluation uses Stack. So (C) is NOT a stack application.

**Q20 → (E) Call Stack (Stack memory)**
Activation records (local variables, return addresses, parameters) for each recursive call are stored in the Call Stack — which is a stack data structure in memory.

**Q21 → (C) B, D, C**
Trace:
- Push(A): [A]
- Push(B): [A, B]
- Pop(): removes B → **output: B**. [A]
- Push(C): [A, C]
- Push(D): [A, C, D]
- Pop(): removes D → **output: D**. [A, C]
- Pop(): removes C → **output: C**. [A]
Output: B, D, C → Answer (C) ✓

**Q22 → (E) 7**
2^3 - 1 = 8 - 1 = **7 moves** for 3 disks.

**Q23 → (D) More than one**
All three statements (A), (B), and (C) are correct:
- Push = insertion ✓
- Pop = deletion ✓
- LIFO = Stack's principle ✓
Answer is (D).

**Q24 → (E) Stack**
Backtracking algorithms (maze solving, N-Queens, Sudoku) use Stack. You explore one path, push states; when stuck, pop and backtrack.

**Q25 → (B)**
Correct PUSH sequence: 1) Check OVERFLOW (is stack full?), 2) Increment top (top++), 3) Insert x at stack[top]. Option (B) correctly describes this order.

---

### GS EXPLANATIONS:

**Q26 → (E) Sasaram (Rohtas district)**
The magnificent tomb of Sher Shah Suri is in Sasaram. It stands in the middle of a lake and is considered architecturally superior to Humayun's Tomb in Delhi.

**Q27 → (E) Tussar (Tussah/Kosa) Silk**
Bhagalpur is famous for Tussar silk made from the cocoons of Antheraea mylitta silkworm (wild silkworm). This is different from Mulberry silk (Bombyx mori, mainstream), Muga silk (Assam), and Eri silk.

**Q28 → (E) Dharampala (Pala dynasty)**
Vikramshila University was established by King Dharampala of the Pala dynasty in the late 8th century AD. It became a renowned center of Tantric Buddhism.

**Q29 → (E) 2002**
The Mahabodhi Temple Complex at Bodh Gaya was inscribed as a UNESCO World Heritage Site in **2002** (26th session of UNESCO World Heritage Committee, Budapest).

**Q30 → (E) Bakhtiyar Khilji (1193 AD)**
The Turkish military commander Muhammad bin Bakhtiyar Khilji destroyed Nalanda University in 1193 AD, burning its massive library. This was a catastrophic blow to Indian learning.

**Q31 → (D) More than one**
All three are historically correct about Vaishali: (A) World's first republic (Lichchhavi), (B) Mahavira's birthplace, (C) Buddha's last sermon. All three statements are true → (D).

**Q32 → (B) Forced cultivation of indigo (Tinkathia system)**
The Champaran Satyagraha (1917) was specifically against the Tinkathia system where British indigo planters forced farmers to grow indigo on 3/20 (teen katha) of their land under exploitative terms.

**Q33 → (E) Muzaffarpur**
Muzaffarpur is called the "Litchi Kingdom of India." Its Shahi Litchi has a Geographical Indication (GI) Tag, indicating its unique origin and quality.

**Q34 → (E) Sun God (Surya)**
Chhath Puja is a festival of sun worship. Devotees worship the rising and setting sun (Usha and Chhathi Maiya). No idols are used — only sunlight is worshipped.

**Q35 → (E) Rajgir (Rajagriha)**
The First Buddhist Council was held at Rajgir (Rajagriha) in 487 BC, shortly after Buddha's Mahaparinirvana. It was convened by Ajatashatru (Haryanka king) and chaired by Mahakassapa.

**Q36 → (E) Dr. Rajendra Prasad**
Dr. Rajendra Prasad was India's first and longest-serving President (1950–1962). He was born at Ziradei village in Siwan district, Bihar.

**Q37 → (E) Over 90%**
Bihar produces over 90% of the world's Makhana (Fox Nut/Lotus seed). The Mithila region (Darbhanga, Madhubani, Sitamarhi) is the global center of Makhana cultivation.

**Q38 → (E) Ganga and Gandak**
Sonepur Mela is held at Sonepur (Hajipur area), which is at the confluence of the Ganga and Gandak rivers, on the occasion of Kartik Purnima.

**Q39 → (E) Saran (Sitab Diara village)**
Jayaprakash Narayan (JP) was born on October 11, 1902, at Sitab Diara village in Saran district (now partly in UP due to river course change). He is Bihar's most iconic freedom fighter.

**Q40 → (E) Kaimur Hills**
Rohtasgarh Fort is situated on the Kaimur Hills (part of the Vindhya range) at an altitude of about 450 meters. The fort's hilltop location made it virtually impregnable.

**Q41 → (E) Madhubani**
Madhubani Painting is associated with Madhubani district and the broader Mithila cultural zone. It is painted on walls, cloth, and paper using natural colors. GI Tag holder.

**Q42 → (E) Gaya**
The Falgu River flows through Gaya city. The Vishnupad Temple stands on its banks. Hindus perform Pind Daan (funeral rites) on the banks of Falgu at Gaya.

**Q43 → (E) Vidhan Sabha + Vidhan Parishad (bicameral)**
Bihar has a bicameral legislature: Vidhan Sabha (243 seats, lower house) and Vidhan Parishad (75 seats, upper house). Only 6 states in India have Vidhan Parishad (UP, Bihar, Maharashtra, Karnataka, AP, Telangana).

**Q44 → (E) Gangetic River Dolphin**
The Gangetic River Dolphin (Platanista gangetica) is India's National Aquatic Animal. The Vikramshila Gangetic Dolphin Sanctuary in Bhagalpur protects this endangered species.

**Q45 → (D) More than one**
All three have GI Tags: (A) Shahi Litchi ✓, (B) Madhubani Painting ✓, (C) Bhagalpuri Silk ✓. Along with Mithila Makhana, Katarni Rice, etc. Answer is (D).

**Q46 → (E) Begusarai (Simaria village)**
Ramdhari Singh "Dinkar" was born on September 23, 1908, at Simaria village in what is now Begusarai district. He received the Jnanpith Award (1972) for his epic poem "Urvashi."

**Q47 → (E) Pawapuri (Nalanda district)**
Mahavira attained Moksha (Nirvana) at Pawapuri in present-day Nalanda district. Pawapuri is a major Jain pilgrimage site — the Jal Mandir (Water Temple) here is sacred.

**Q48 → (E) Rohtas**
Rohtas district has large limestone deposits in the Kaimur plateau, supporting major cement plants: Dalmia Bharat (Dalmianagar), ACC, JK Cement. Rohtas is Bihar's industrial heartland.

**Q49 → (E) 1916**
Patna High Court was established in 1916 during the British Raj. It is one of the oldest High Courts in India, making it over 100 years old.

**Q50 → (D) More than one**
All three statements are CORRECT:
(A) Bihar has 50% women's reservation in PRIs ✓
(B) Bihar is bicameral (Vidhan Sabha + Parishad) ✓
(C) Rajendra Prasad (1st President) was from Bihar ✓
Answer: (D) More than one.

---

## 📊 SCORE ANALYSIS

```
Score Range    → Status
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
45–50          → 🏆 TOPPER LEVEL — Outstanding! Keep this up!
40–44          → 🥇 Excellent — Close to topper level
35–39          → 🥈 Good — Identify weak topics and revise
30–34          → 🥉 Average — Must revise Sections 5, 6, 7 again
Below 30       → ⚠️ Needs work — Reread notes carefully tonight
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CS Score  /25 : ___
GS Score  /25 : ___
Total     /50 : ___
```

---

## 🌙 NIGHT REVISION — 5-BULLET SUMMARY (Write in your notebook!)

### CS (Stack):
1. **Stack = LIFO** | Empty: top = -1 | Full: top = MAX-1
2. **All operations = O(1)** | Overflow = push on full | Underflow = pop from empty
3. **Recursion uses STACK** | DFS uses Stack | BFS uses QUEUE
4. **Async data transfer = QUEUE** (not Stack) | Symbol balancing = STACK
5. **Tower of Hanoi: 2^n - 1 moves** | String reversal = Stack

### GS (Bihar — Districts):
1. **Rohtas = Cement capital** | Sher Shah Suri's tomb at Sasaram
2. **Bhagalpur = Silk City** | Vikramshila Univ. by Dharampala; India's 1st dolphin sanctuary
3. **Bodh Gaya** = Buddha's enlightenment; **Nalanda** destroyed by Bakhtiyar Khilji (1193)
4. **Vaishali** = World's 1st republic + Mahavira's birthplace
5. **Chhath Puja** = Sun worship — Bihar's #1 festival; Sonepur Mela = Ganga + Gandak

---

## ⏭️ TOMORROW — DAY 17 PREVIEW

```
CS Topic  : Stack — Infix to Postfix/Prefix Conversion
            (The full algorithm, step-by-step trace, operator precedence)
GS Topic  : India Geography — Eastern Ghats, Peninsular Rivers

Day 16 directly feeds into Day 17!
Key to remember from today:
  POSTFIX = operators AFTER operands (A B +)
  PREFIX  = operators BEFORE operands (+ A B)
  Conversion uses STACK — operator precedence matters!
```

---

*Day 16 Complete | Phase 1, Week 3 | BPSC TRE 4.0 Preparation*
*50 Questions Total: 25 CS (Stack) + 25 GS (Bihar Districts & Economy)*
*BPSC 5-option format — always check option (D) carefully!*
*Every day you study is a step closer to that TOP RANK! 🎯*
