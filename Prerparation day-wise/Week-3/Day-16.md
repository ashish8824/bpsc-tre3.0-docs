# 📅 BPSC TRE 4.0 — DAY 16 COMPLETE STUDY MODULE
### Stack Data Structure (LIFO) + Bihar Geography — Rohtas & Bhagalpur Districts
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Stack — LIFO, Operations, Implementation, Applications
> - Afternoon (1 hr): Bihar Geography — Rohtas & Bhagalpur Districts
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Stack Data Structure — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Stack?

### Real-Life Analogy — The Plate Stack:
Imagine a **stack of plates in a cafeteria**:
- Plates are placed on top of each other
- You always **add a new plate on TOP**
- You always **take a plate from the TOP**
- You CANNOT pull a plate from the middle or bottom
- The **last plate placed** is the **first plate taken** → LIFO

```
Stack of Plates:
                    ← You can ONLY add/remove here (TOP)
        ┌─────────┐
        │ Plate 4 │  ← added LAST, removed FIRST
        ├─────────┤
        │ Plate 3 │
        ├─────────┤
        │ Plate 2 │
        ├─────────┤
        │ Plate 1 │  ← added FIRST, removed LAST
        └─────────┘
          (BOTTOM)
```

### Other Real-Life Examples of Stack:
```
1. Browser "Back" button → pages stored in a stack; back = pop
2. Undo (Ctrl+Z) in editors → each action pushed; undo = pop
3. Pile of books → add on top, remove from top
4. Function call stack → nested function calls (recursion!)
5. Stack of trays in a cafeteria
6. CD/DVD in a spindle → top disc taken first
```

### Formal Definition:
A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle — the element inserted LAST is the element removed FIRST. All insertions and deletions happen at ONE end, called the **TOP** of the stack.

---

## 🔷 SECTION 2: LIFO Principle — The Core Concept

### LIFO = Last In, First Out:
```
Think of it this way:
  PUSH order: A → B → C → D   (D pushed last)
  POP order:  D → C → B → A   (D popped first)

The stack REVERSES the order of insertion.
This is its most important property.
```

### LIFO vs FIFO (Stack vs Queue):
```
STACK = LIFO (Last In, First Out)
  → Like a plate stack: last plate added = first removed
  → One end for BOTH insert and delete (TOP)

QUEUE = FIFO (First In, First Out)
  → Like a ticket line: first person = first served
  → Two ends: REAR for insert, FRONT for delete
```

### 🚨 PYQ TRAP #1 — The Most Common Confusion:
> **Recursion → uses STACK (internally)**
> **Asynchronous data transfer → uses QUEUE (NOT stack)**
> This is the single most tested distinction in BPSC TRE CS section.

---

## 🔷 SECTION 3: Stack Representation Using Array

### How a Stack Looks in Memory:
```
Stack using array of size 5:

Index:   0      1      2      3      4
       ┌──────┬──────┬──────┬──────┬──────┐
       │  10  │  20  │  30  │  __  │  __  │
       └──────┴──────┴──────┴──────┴──────┘
                        ↑
                      top = 2
                   (points to last inserted element)

Stack contents (top to bottom): 30, 20, 10
Top element = arr[top] = arr[2] = 30
Stack size (used) = top + 1 = 3
```

### The `top` Pointer:
```
INITIAL STATE (empty stack):
top = -1   ← Convention: -1 means stack is EMPTY

After pushing 10:
top = 0    arr[0] = 10

After pushing 20:
top = 1    arr[1] = 20

After pushing 30:
top = 2    arr[2] = 30

After popping:
top = 1    (30 is logically removed)

After popping:
top = 0    (20 is logically removed)

After popping:
top = -1   (stack is EMPTY again)
```

### 🚨 PYQ TRAP #2: Initial value of `top`
> When a stack is empty, `top = -1` (not 0, not null).
> This is the standard convention used in all C/C++ array implementations.
> `top == -1` → stack is empty (isEmpty condition)

---

## 🔷 SECTION 4: Stack Operations — Complete Guide

### Overview of All Operations:

| Operation | Action | Condition Check | Time Complexity |
|-----------|--------|----------------|----------------|
| **Push** | Insert element at top | Check if FULL first | O(1) |
| **Pop** | Remove element from top | Check if EMPTY first | O(1) |
| **Peek / Top** | View top element (no removal) | Check if EMPTY first | O(1) |
| **isEmpty** | Is stack empty? | top == -1 | O(1) |
| **isFull** | Is stack full? | top == MAX-1 | O(1) |

**ALL stack operations are O(1)** — this is a critical exam fact.

---

### Operation 1: PUSH (Insertion)

```
Algorithm:
PUSH(stack, MAX_SIZE, top, value):
  Step 1: Check if stack is full → if top == MAX_SIZE - 1 → OVERFLOW, stop
  Step 2: Increment top → top = top + 1
  Step 3: Insert → stack[top] = value
  Step 4: Done

Pseudocode:
void push(int stack[], int &top, int MAX, int value) {
    if (top == MAX - 1) {
        cout << "Stack Overflow!";
        return;
    }
    top++;
    stack[top] = value;
}
```

### DRY RUN — Push Operations Step by Step:
```
Stack size MAX = 4. Push: 10, 20, 30, 40

INITIAL:  top = -1
          [  _  |  _  |  _  |  _  ]

PUSH 10:  top becomes 0; stack[0] = 10
          [ 10  |  _  |  _  |  _  ]  top→0

PUSH 20:  top becomes 1; stack[1] = 20
          [ 10  | 20  |  _  |  _  ]  top→1

PUSH 30:  top becomes 2; stack[2] = 30
          [ 10  | 20  | 30  |  _  ]  top→2

PUSH 40:  top becomes 3; stack[3] = 40
          [ 10  | 20  | 30  | 40  ]  top→3

PUSH 50 (attempt):
          top == MAX-1 == 3 → STACK OVERFLOW! Element NOT inserted.
```

---

### Operation 2: POP (Deletion)

```
Algorithm:
POP(stack, top):
  Step 1: Check if stack is empty → if top == -1 → UNDERFLOW, stop
  Step 2: Store value → value = stack[top]
  Step 3: Decrement top → top = top - 1
  Step 4: Return value

Pseudocode:
int pop(int stack[], int &top) {
    if (top == -1) {
        cout << "Stack Underflow!";
        return -1;
    }
    int value = stack[top];
    top--;
    return value;
}
```

### DRY RUN — Pop Operations Step by Step:
```
Stack state: [ 10 | 20 | 30 | 40 ]  top = 3

POP():    value = stack[3] = 40; top becomes 2
          [ 10 | 20 | 30 |  _ ]  top→2  returned: 40

POP():    value = stack[2] = 30; top becomes 1
          [ 10 | 20 |  _ |  _ ]  top→1  returned: 30

POP():    value = stack[1] = 20; top becomes 0
          [ 10 |  _ |  _ |  _ ]  top→0  returned: 20

POP():    value = stack[0] = 10; top becomes -1
          [  _ |  _ |  _ |  _ ]  top→-1  returned: 10

POP() (attempt):
          top == -1 → STACK UNDERFLOW! Cannot pop.
```

---

### Operation 3: PEEK / TOP (View without Removal)

```
Algorithm:
PEEK(stack, top):
  Step 1: Check if empty → if top == -1 → "Stack is empty", stop
  Step 2: Return stack[top] WITHOUT changing top

Pseudocode:
int peek(int stack[], int top) {
    if (top == -1) {
        cout << "Stack is empty!";
        return -1;
    }
    return stack[top];  // top is NOT decremented
}

KEY DIFFERENCE from POP:
Peek → reads top element, top stays same
Pop  → reads AND removes top element, top decreases by 1
```

---

### Operation 4: isEmpty

```
bool isEmpty(int top) {
    return (top == -1);  // true if empty
}

Condition: top == -1 → EMPTY
```

### Operation 5: isFull

```
bool isFull(int top, int MAX) {
    return (top == MAX - 1);  // true if full
}

Condition: top == MAX - 1 → FULL
(If MAX = 5, stack is full when top == 4)
```

---

## 🔷 SECTION 5: Overflow and Underflow

### Stack Overflow:
```
OVERFLOW occurs when:
  → You try to PUSH into a FULL stack
  → Condition: top == MAX_SIZE - 1
  → Action: Print error "Stack Overflow", do NOT push

Analogy: Trying to place another plate when the stack is already
         touching the ceiling — physically impossible!

Real-world example: Stack Overflow in programs = recursion so deep
that the call stack runs out of memory (famous website stackover flow.com!)
```

### Stack Underflow:
```
UNDERFLOW occurs when:
  → You try to POP from an EMPTY stack
  → Condition: top == -1
  → Action: Print error "Stack Underflow", do NOT pop

Analogy: Trying to take a plate from an empty stand — nothing to take!
```

### 🚨 PYQ TRAP #3: Overflow vs Underflow Conditions
```
Check before PUSH → Overflow condition: top == MAX - 1
Check before POP  → Underflow condition: top == -1
```

---

## 🔷 SECTION 6: Complete Stack State Diagram

```
Empty Stack            After PUSH(A)         After PUSH(B)
 ┌───────┐              ┌───────┐              ┌───────┐
 │       │              │       │              │   B   │ ← top
 │       │              │       │              ├───────┤
 │       │  top=-1       │       │              │   A   │
 │       │    ──PUSH(A)→ │   A   │ ← top        └───────┘ top=1
 └───────┘              └───────┘ top=0

After PUSH(C)          After POP()           After POP()
 ┌───────┐              ┌───────┐              ┌───────┐
 │   C   │ ← top        │       │              │       │
 ├───────┤   ──POP()──→ │   B   │ ← top ─────→ │   A   │ ← top
 │   B   │              ├───────┤              └───────┘ top=0
 ├───────┤              │   A   │  top=1
 │   A   │              └───────┘
 └───────┘ top=2        returned C            returned B
```

---

## 🔷 SECTION 7: Applications of Stack

### 1. Recursion — THE MOST IMPORTANT APPLICATION

```
When a function calls itself, the system uses a STACK internally:

void countdown(int n) {
    if (n == 0) return;
    countdown(n-1);        ← recursive call
    cout << n;
}

countdown(3) call sequence:
PUSH: countdown(3)
PUSH: countdown(2)
PUSH: countdown(1)
PUSH: countdown(0) → BASE CASE → returns
POP:  countdown(1) → prints 1
POP:  countdown(2) → prints 2
POP:  countdown(3) → prints 3

Output: 1 2 3 (reversal! — because stack reverses order)
```

### Call Stack Visual:
```
System Stack during countdown(3):

  ┌──────────────┐
  │ countdown(0) │ ← top (most recent call, returns first)
  ├──────────────┤
  │ countdown(1) │
  ├──────────────┤
  │ countdown(2) │
  ├──────────────┤
  │ countdown(3) │ ← bottom (first call, returns last)
  └──────────────┘

"Stack Overflow" error = too many recursive calls → call stack fills up
```

### 2. Expression Evaluation & Conversion

```
Types of expressions:
  Infix:   A + B       (operator between operands — what humans write)
  Postfix: A B +       (operator AFTER operands — computer-friendly)
  Prefix:  + A B       (operator BEFORE operands)

Stack is used for:
  → Converting Infix to Postfix
  → Evaluating Postfix expressions
  → Converting Infix to Prefix

Example: Infix (A + B) * C → Postfix: A B + C *
This conversion uses a STACK to hold operators temporarily.
```

### 3. Parenthesis Balancing (Symbol Matching)

```
Check if brackets are balanced in: {[()]}

Algorithm uses STACK:
Step 1: Scan characters left to right
Step 2: If opening bracket: ( { [ → PUSH onto stack
Step 3: If closing bracket: ) } ] → POP from stack and check match
Step 4: If mismatch or stack underflows → UNBALANCED
Step 5: If stack empty at end → BALANCED

Example: {[()]}
  { → PUSH  → stack: {
  [ → PUSH  → stack: { [
  ( → PUSH  → stack: { [ (
  ) → POP   → popped (, matches ) ✅ → stack: { [
  ] → POP   → popped [, matches ] ✅ → stack: {
  } → POP   → popped {, matches } ✅ → stack: (empty)
  End: stack empty → BALANCED ✅

Example: {(}
  { → PUSH  → stack: {
  ( → PUSH  → stack: { (
  } → POP   → popped (, does NOT match } ❌ → UNBALANCED
```

### 4. Backtracking / Undo Operations

```
Applications:
→ Browser "Back" button: each URL pushed; back = pop
→ Ctrl+Z (Undo): each action pushed; undo = pop last action
→ Maze solving: store path; dead end = pop and try another
→ Game backtracking: store game states; revert = pop
```

### 5. Function Call Management

```
When any function is called (not just recursive):
→ Return address pushed on stack
→ Parameters pushed on stack
→ Local variables stored on stack
→ On return: all popped and previous context restored

This is the PROGRAM STACK (or CALL STACK)
```

---

## 🔷 SECTION 8: Non-Applications of Stack — EXAM TRAP

### What is NOT a Stack Application:

| Task | Data Structure Used | Why |
|------|---------------------|-----|
| Asynchronous data transfer between processes | **QUEUE** | FIFO — first data sent = first processed |
| CPU Scheduling (Round Robin) | **QUEUE** | FIFO — processes wait in order |
| Print spooler | **QUEUE** | First document sent = first printed |
| BFS (Breadth-First Search) | **QUEUE** | Level-by-level traversal |
| DFS (Depth-First Search) | **STACK** | Go deep, backtrack |
| Recursion | **STACK** | Call stack is LIFO |
| Undo/Redo | **STACK** | Last action undone first |
| Balancing brackets | **STACK** | LIFO matching |

### 🚨 PYQ TRAP #4 — The MOST ASKED QUESTION:
> "Which of the following is NOT an application of Stack?"
> Answer: **Asynchronous data transfer** — this uses QUEUE, not Stack.
>
> Full list of STACK applications for exam:
> 1. Recursion / Function call management
> 2. Expression evaluation and conversion (Infix↔Postfix↔Prefix)
> 3. Parenthesis / Symbol balancing
> 4. Backtracking (maze, DFS)
> 5. Undo operations (text editors)
> 6. Browser back navigation
> 7. Tower of Hanoi

---

## 🔷 SECTION 9: Time & Space Complexity Summary

```
Operation        Time Complexity    Space Complexity
─────────────────────────────────────────────────────
Push             O(1)               O(1)
Pop              O(1)               O(1)
Peek/Top         O(1)               O(1)
isEmpty          O(1)               O(1)
isFull           O(1)               O(1)
─────────────────────────────────────────────────────
Overall Stack    O(1) all ops       O(n) for n elements

KEY FACT: ALL stack operations are O(1)
This is because we always work at ONE fixed end (TOP)
No traversal is ever needed.
```

### 🚨 PYQ TRAP #5: Why all operations O(1)?
> Because stack only adds/removes from the TOP — a fixed known position. No searching, no shifting. Direct access to top via the `top` pointer.

---

## 🔷 SECTION 10: Stack vs Queue — Complete Comparison

```
Feature          STACK                      QUEUE
─────────────────────────────────────────────────────────
Principle        LIFO (Last In, First Out)  FIFO (First In, First Out)
Real example     Plate stack                Ticket counter line
Ends used        ONE end (TOP)              TWO ends (FRONT & REAR)
Insert           PUSH (at top)              ENQUEUE (at rear)
Delete           POP (from top)             DEQUEUE (from front)
Empty check      top == -1                  front == -1 or front > rear
Full check       top == MAX-1               rear == MAX-1
Applications     Recursion, Undo, DFS,      BFS, CPU scheduling,
                 Expression eval            Async transfer, print spooler
```

---

## 📊 VISUAL SUMMARY — Stack Mind Map

```
                        STACK (LIFO)
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
     OPERATIONS         OVERFLOW &          APPLICATIONS
          │             UNDERFLOW                │
    Push  O(1)               │           Recursion (call stack)
    Pop   O(1)       Overflow: PUSH       Expression eval
    Peek  O(1)       into FULL stack      Parenthesis balance
    isEmpty O(1)     (top==MAX-1)         Undo/Backtrack
    isFull  O(1)                          DFS traversal
          │          Underflow: POP       Browser back button
     top pointer     from EMPTY stack                │
     starts at -1    (top==-1)         NOT applications:
                                       Async transfer → QUEUE
                                       CPU scheduling → QUEUE
```

---
---

# PART 2: GENERAL STUDIES
## 🗺️ Bihar Geography — Rohtas & Bhagalpur Districts

---

## 🔷 WHY THIS MATTERS FOR BPSC TRE:
- Rohtas and Bhagalpur are among Bihar's most economically and historically significant districts
- Bhagalpur's silk industry + Rohtas's agriculture/minerals appear frequently
- Both have important river connections tested in geography questions

---

## 🔷 ROHTAS DISTRICT — COMPLETE PROFILE

### Basic Facts:
```
Headquarters:   Sasaram
Division:       Patna Division
Location:       South-western Bihar, bordering Jharkhand & UP
Area:           3,847 sq km
Rivers:         Son (main), Koel (minor), Durgawati, North Koel

BOUNDARIES:
North → Bhojpur (Arrah)
East  → Aurangabad
South → Jharkhand (Palamu)
West  → Uttar Pradesh (Varanasi & Mirzapur)
```

### Son River — Rohtas Connection:
```
Son river enters Bihar at Rohtas district (Indrapuri Barrage)
Indrapuri Barrage → important irrigation project on Son
Son flows east through Rohtas → Bhojpur before joining Ganga

Significance:
→ Son river provides IRRIGATION to Rohtas farmland
→ Son Command Area = major agricultural region
→ Rohtas = one of Bihar's major PADDY/RICE producing districts
```

### Agricultural Importance:
```
Rohtas = "RICE BOWL" of Bihar (also called granary of Bihar)
→ Major crops: Paddy (rice), Wheat, Maize
→ Fertile alluvial + red-laterite soil mix
→ Son canal irrigation → extensive paddy cultivation
→ Also: vegetables, pulses, oilseeds

Key fact: Rohtas ranks among TOP rice-producing districts of Bihar
```

### Mineral Resources:
```
Rohtas has SIGNIFICANT MINERAL WEALTH (unlike most of north Bihar):
→ Limestone: Extensive deposits → Cement industry
→ Bauxite: Small deposits
→ Pyrite: Amjhor (Rohtas) has Asia's LARGEST pyrite deposit ← EXAM IMPORTANT!
→ Granite: Stone quarries

DALMIAPURAM / DALMIANAGAR:
→ Located in Rohtas on the Son river bank
→ Major cement manufacturing hub
→ Has one of the LARGEST cement plants in Bihar
→ Also: paper mills, textile industries
```

### 🚨 PYQ TRAP: Amjhor Pyrite
> **Amjhor** (in Rohtas district) contains **Asia's largest deposit of pyrite** (iron sulphide). This is a very specific Bihar fact with high BPSC probability.

### Historical & Cultural Importance:
```
SASARAM (District HQ of Rohtas):
→ Tomb of SHER SHAH SURI — one of the greatest examples of
  Afghan/Mughal architecture in India
→ Sher Shah Suri (real name: Farid Khan) was born near Sasaram
→ He built the GRAND TRUNK ROAD (Sadak-e-Azam) from Kolkata to Peshawar
→ He defeated Mughal Emperor Humayun twice (Chausa 1539, Kannauj 1540)
→ The octagonal tomb in Sasaram stands in the middle of a lake — stunning

ROHTASGARH FORT:
→ Ancient fort on a plateau in Rohtas (Kaimur hills)
→ Used by Sher Shah Suri and later other rulers
→ Historical, archaeological importance
→ Part of Kaimur wildlife sanctuary area

BATTLE OF CHAUSA (1539):
→ Fought between Sher Shah Suri and Humayun
→ Location: Near Buxar / Rohtas area (Chausa, on Son river)
→ Sher Shah won → established Sur Empire
```

### 🚨 PYQ TRAP: Sher Shah Suri
> Sher Shah Suri built the **Grand Trunk Road** — one of Asia's oldest and longest roads, connecting Chittagong (Bangladesh) to Kabul (Afghanistan). He also introduced the **Rupiya (Rupee)** currency system. Born near **Sasaram, Rohtas, Bihar**.

---

## 🔷 BHAGALPUR DISTRICT — COMPLETE PROFILE

### Basic Facts:
```
Headquarters:   Bhagalpur city
Division:       Bhagalpur Division
Location:       Eastern Bihar, on Ganga river
Rivers:         Ganga (main — flows through city), Champa, Chandan

BOUNDARIES:
North → Purnia, Saharsa
East  → Banka, Jharkhand
South → Jharkhand
West  → Munger

FAMOUS NAME: "Silk City of India" / "Silk City of Bihar"
             also: "Ang Pradesh" (ancient name — Kingdom of Anga)
```

### Bhagalpur Silk — THE #1 EXAM FACT:
```
TUSSAR SILK (Kosa Silk):
→ Bhagalpur is the SILK CAPITAL OF INDIA (informal name)
→ Produces Tussar silk (also called Tassar or Kosa silk)
→ Made from Antheraea mylitta silkworm (wild silk moth — not mulberry)
→ Bhagalpur Silk got GEOGRAPHICAL INDICATION (GI) TAG
→ Major export item from Bihar

Where Bhagalpur silk comes from:
→ Silkworms feed on Arjun and Sal trees (NOT mulberry — unlike Mysore silk)
→ Silk production cottage industry employs thousands of weavers
→ Major markets: Nathnagar area of Bhagalpur

DIFFERENCE from other silk:
Bhagalpur (Tussar) → wild silkworm → coarser texture → golden-brown colour
Mysore / Varanasi  → mulberry silkworm → finer texture → smooth/white/bright
```

### 🚨 PYQ TRAP: Bhagalpur Silk
> Bhagalpur produces **Tussar (Kosa) silk**, NOT mulberry silk.
> Tussar silkworms feed on **Arjun and Sal trees** (not mulberry).
> Bhagalpur Silk has GI tag.
> Bhagalpur is called the **"Silk City of India"**.

### Ganga at Bhagalpur — Special Geography:
```
SULTANGANJ (in Bhagalpur):
→ The Ganga flows NORTHWARD here (unique geographical feature)
→ Devotees collect Gangajal from here for Deoghar (Baidyanath) Kanwar Yatra
→ One of the most important pilgrimage routes (Shravan month)
→ Ajgaivinath temple — ancient Shiva temple on a rocky island in Ganga

VIKRAMSHILA UNIVERSITY (ruins):
→ Located in Antichak village, Bhagalpur district
→ Built by Pala king Dharmapala (8th century CE)
→ Major Buddhist learning center — along with Nalanda and Takshashila
→ Destroyed by Bakhtiyar Khilji in 1203 CE
→ Archaeological remains visible today
→ Very high BPSC probability!
```

### Historical Importance:
```
ANCIENT ANGA MAHAJANAPADA:
→ Bhagalpur region was part of the ancient Anga kingdom
→ One of the 16 Mahajanapadas (mentioned in Buddhist texts)
→ Capital was Champa (near modern Bhagalpur)
→ Later absorbed into Magadha by Bimbisara

COLGONG / KAHALGAON:
→ Kahalgaon (in Bhagalpur district) has Bihar's only THERMAL POWER PLANT
→ National Thermal Power Corporation (NTPC) Kahalgaon
→ Situated on the banks of Ganga
→ One of the largest power plants in eastern India

DOLPHIN SANCTUARY:
→ Vikramshila Gangetic Dolphin Sanctuary
→ Located on Ganga between Sultanganj and Kahalgaon (Bhagalpur)
→ Protects the endangered Gangetic river dolphin
→ Bihar's State Animal = Gaur (Indian Bison) but Gangetic Dolphin = India's National Aquatic Animal
```

### 🚨 PYQ TRAP: Vikramshila Dolphin Sanctuary
> The **Vikramshila Gangetic Dolphin Sanctuary** in Bhagalpur protects India's national aquatic animal — the **Gangetic River Dolphin (Platanista gangetica)**. This is located between Sultanganj and Kahalgaon on the Ganga.

---

## 🔷 COMPARISON TABLE — ROHTAS VS BHAGALPUR

| Feature | Rohtas | Bhagalpur |
|---------|--------|-----------|
| Location | South-west Bihar | East Bihar |
| HQ | Sasaram | Bhagalpur |
| Main River | Son | Ganga |
| Famous For | Paddy/Rice production, Cement | Tussar Silk, Ganga dolphin |
| Key Mineral | Pyrite (Asia's largest — Amjhor) | No major minerals |
| Historical Figure | Sher Shah Suri (Sasaram tomb) | Vikramshila University |
| Power Plant | — | NTPC Kahalgaon (thermal) |
| Key Industry | Cement (Dalmianagar) | Silk weaving |
| GI Product | — | Bhagalpur Silk (Tussar) |
| University/Education | — | Tilkamanjhi Bhagalpur University |
| Special Geography | Son river entry into Bihar | Ganga flows NORTHWARD (Sultanganj) |

---

## 🔷 MEMORY TRICKS

### Rohtas Quick Memory:
```
"ROHTAS = Rice + Ore + History + Tomb + Architecture + Son"
R = Rice/Paddy (rice bowl of Bihar)
O = Ore (Pyrite at Amjhor — Asia's largest)
H = History (Sher Shah Suri)
T = Tomb (Sasaram — Afghan architecture)
A = Architecture (Grand Trunk Road builder)
S = Son river (enters Bihar at Rohtas)
```

### Bhagalpur Quick Memory:
```
"BHAGALPUR = Silk + Buddhist + Ganga + Northward + Dolphin + Power"
S = Silk (Tussar/Kosa — GI tag)
B = Buddhist (Vikramshila University ruins)
G = Ganga flows through it
N = Northward flow at Sultanganj
D = Dolphin Sanctuary (Vikramshila Gangetic)
P = Power Plant (NTPC Kahalgaon)
```

---

## 🔷 KEY FACTS QUICK REFERENCE

### Rohtas Must-Memorize:
1. HQ = Sasaram
2. Sher Shah Suri's tomb = Sasaram (in middle of lake)
3. Amjhor = Asia's largest Pyrite deposit
4. Son river enters Bihar at Rohtas (Indrapuri Barrage)
5. Rice Bowl of Bihar
6. Dalmianagar = cement + paper industry on Son river
7. Rohtasgarh Fort = historical fort in Kaimur hills

### Bhagalpur Must-Memorize:
1. HQ = Bhagalpur city
2. Silk City of India → Tussar silk (GI tag)
3. Vikramshila University ruins (Buddhist, Pala era, destroyed by Bakhtiyar Khilji)
4. Sultanganj → Ganga flows NORTHWARD + Kanwar pilgrimage
5. NTPC Kahalgaon thermal power plant
6. Vikramshila Gangetic Dolphin Sanctuary
7. Ancient Anga Mahajanapada capital (Champa)

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Stack, LIFO, Operations, Overflow/Underflow, Applications

---

**Q1.** What does LIFO stand for in the context of Stack?
(A) Linear In, First Out
(B) Last In, First Out
(C) Last Input, First Output
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the initial value of the `top` pointer in an empty stack (using array implementation)?
(A) 0
(B) 1
(C) -1
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the time complexity of the PUSH operation in a stack?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q4.** A stack OVERFLOW occurs when:
(A) You try to pop from an empty stack
(B) You try to push into a full stack
(C) The top pointer becomes -1
(D) More than one of the above
(E) None of the above

---

**Q5.** A stack UNDERFLOW occurs when:
(A) You try to push into a full stack
(B) You try to pop from an empty stack
(C) The stack contains only one element
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following is the correct condition to check if a stack (using array of size MAX) is FULL?
(A) top == 0
(B) top == MAX
(C) top == MAX - 1
(D) More than one of the above
(E) None of the above

---

**Q7.** Elements are pushed in order: 10, 20, 30, 40. What is the order in which they are popped?
(A) 10, 20, 30, 40
(B) 40, 30, 20, 10
(C) 10, 40, 30, 20
(D) More than one of the above
(E) None of the above

---

**Q8.** What does the PEEK operation do in a stack?
(A) Inserts an element at top
(B) Removes and returns the top element
(C) Returns the top element WITHOUT removing it
(D) More than one of the above
(E) None of the above

---

**Q9.** Which internal data structure does RECURSION use?
(A) Queue
(B) Array
(C) Stack
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is NOT an application of a Stack?
(A) Recursion
(B) Asynchronous data transfer between two processes
(C) Parenthesis matching
(D) More than one of the above
(E) None of the above

---

**Q11.** In a stack of size 5, after pushing elements 1, 2, 3, what is the value of `top`?
(A) 0
(B) 2
(C) 3
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the difference between POP and PEEK in a stack?
(A) Pop adds an element; Peek removes it
(B) Pop removes the top element; Peek only reads it without removing
(C) Both are the same operation
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following correctly uses STACK data structure?
(A) Print job spooler
(B) Process scheduling in OS (Round Robin)
(C) Browser back button
(D) More than one of the above
(E) None of the above

---

**Q14.** The "undo" feature in text editors is implemented using:
(A) Queue
(B) Linked List
(C) Stack
(D) More than one of the above
(E) None of the above

---

**Q15.** Consider a stack with operations: PUSH(5), PUSH(10), POP(), PUSH(15), POP(). What is the top element after all operations?
(A) 5
(B) 15
(C) 10
(D) More than one of the above
(E) None of the above

---

**Q16.** A stack is used to convert:
(A) Array to linked list
(B) Infix expression to Postfix expression
(C) Binary to decimal
(D) More than one of the above
(E) None of the above

---

**Q17.** If a stack of size 3 has elements [A, B, C] with C on top, and we push D, what happens?
(A) D is inserted below C
(B) D replaces C
(C) Stack Overflow — D cannot be pushed
(D) More than one of the above
(E) None of the above

---

**Q18.** What is the space complexity of a stack containing n elements?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q19.** Which data structure is used in DFS (Depth-First Search)?
(A) Queue
(B) Stack
(C) Array
(D) More than one of the above
(E) None of the above

---

**Q20.** For parenthesis matching `{[()]}`, which of the following is TRUE?
(A) A queue is required
(B) A stack is used — opening brackets pushed, closing brackets pop and match
(C) No data structure is needed — just count brackets
(D) More than one of the above
(E) None of the above

---

**Q21.** In an array-based stack implementation, elements are always added and removed from:
(A) Index 0
(B) The middle of the array
(C) The index pointed by `top`
(D) More than one of the above
(E) None of the above

---

**Q22.** What does "Stack Overflow" error mean in a running program?
(A) Arithmetic overflow during calculation
(B) The call stack ran out of memory (usually from deep/infinite recursion)
(C) Integer overflow in a variable
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly defines a STACK?
(A) FIFO linear data structure with two open ends
(B) LIFO linear data structure where insert and delete happen at one end
(C) Non-linear data structure with hierarchical relations
(D) More than one of the above
(E) None of the above

---

**Q24.** Tower of Hanoi problem is solved using:
(A) Queue
(B) Recursion (Stack internally)
(C) Binary Search
(D) More than one of the above
(E) None of the above

---

**Q25.** If elements are pushed in sequence A, B, C, D, E and then we pop twice, what is the top element?
(A) A
(B) C
(C) D
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Bihar Geography — Rohtas & Bhagalpur Districts

---

**Q26.** The district headquarters of Rohtas district in Bihar is:
(A) Rohtas
(B) Dalmianagar
(C) Sasaram
(D) More than one of the above
(E) None of the above

---

**Q27.** Bhagalpur is known as the "Silk City" because of its production of which type of silk?
(A) Mulberry silk
(B) Muga silk
(C) Tussar (Kosa) silk
(D) More than one of the above
(E) None of the above

---

**Q28.** Amjhor in Rohtas district is famous for:
(A) Asia's largest bauxite deposit
(B) Asia's largest pyrite deposit
(C) India's largest coal deposit
(D) More than one of the above
(E) None of the above

---

**Q29.** The tomb of Sher Shah Suri is located in which city?
(A) Patna
(B) Gaya
(C) Sasaram
(D) More than one of the above
(E) None of the above

---

**Q30.** The Son river enters Bihar through which district?
(A) Bhojpur
(B) Rohtas
(C) Aurangabad
(D) More than one of the above
(E) None of the above

---

**Q31.** At which place in Bhagalpur does the Ganga flow in a NORTHWARD direction?
(A) Kahalgaon
(B) Sultanganj
(C) Nathnagar
(D) More than one of the above
(E) None of the above

---

**Q32.** Vikramshila University was built by which Pala dynasty king?
(A) Gopala
(B) Devapala
(C) Dharmapala
(D) More than one of the above
(E) None of the above

---

**Q33.** The NTPC thermal power plant in Bihar is located at:
(A) Barauni (Begusarai)
(B) Kahalgaon (Bhagalpur)
(C) Dalmianagar (Rohtas)
(D) More than one of the above
(E) None of the above

---

**Q34.** Bhagalpur Silk (Tussar) silkworms feed on which trees?
(A) Mulberry
(B) Arjun and Sal trees
(C) Neem and Peepal
(D) More than one of the above
(E) None of the above

---

**Q35.** The Vikramshila Gangetic Dolphin Sanctuary is located in:
(A) Patna district, on the Ganga
(B) Bhagalpur, between Sultanganj and Kahalgaon
(C) Vaishali, near Hajipur
(D) More than one of the above
(E) None of the above

---

**Q36.** Rohtas district is often called the "Rice Bowl" or "Granary" of Bihar because:
(A) It grows only rice and no other crop
(B) Extensive paddy cultivation is supported by Son canal irrigation
(C) It has the highest population of farmers in Bihar
(D) More than one of the above
(E) None of the above

---

**Q37.** Sher Shah Suri was associated with which major historical achievement?
(A) Building the Taj Mahal
(B) Building the Grand Trunk Road and introducing the Rupee currency
(C) Founding the Mughal Empire
(D) More than one of the above
(E) None of the above

---

**Q38.** The ancient Mahajanapada whose capital was Champa (near Bhagalpur) was:
(A) Magadha
(B) Anga
(C) Vajji
(D) More than one of the above
(E) None of the above

---

**Q39.** Bhagalpur Silk received its Geographical Indication (GI) tag, which means:
(A) It can be produced anywhere in India
(B) It is a product specifically tied to the Bhagalpur region
(C) It is exported only to Europe
(D) More than one of the above
(E) None of the above

---

**Q40.** Dalmianagar / Dalmiapuram in Rohtas district is known for:
(A) Silk production
(B) Cement and paper manufacturing
(C) Tea cultivation
(D) More than one of the above
(E) None of the above

---

**Q41.** Rohtasgarh Fort is located in which range of hills?
(A) Vindhya Range
(B) Kaimur Hills
(C) Chota Nagpur Plateau
(D) More than one of the above
(E) None of the above

---

**Q42.** Vikramshila University was destroyed by which invader?
(A) Mahmud of Ghazni
(B) Timur
(C) Bakhtiyar Khilji
(D) More than one of the above
(E) None of the above

---

**Q43.** The Gangetic River Dolphin is significant because:
(A) It is Bihar's state animal
(B) It is India's National Aquatic Animal
(C) It is found only in Bhagalpur
(D) More than one of the above
(E) None of the above

---

**Q44.** What is the Indrapuri Barrage associated with?
(A) Kosi river in Supaul
(B) Son river in Rohtas
(C) Gandak river in Champaran
(D) More than one of the above
(E) None of the above

---

**Q45.** The Kanwar Yatra pilgrimage, where devotees carry Gangajal to Baidyanath Dham (Deoghar), starts from which location?
(A) Patna Ghat
(B) Sultanganj (Bhagalpur)
(C) Hajipur (Vaishali)
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following is a correct statement about Tussar silk produced in Bhagalpur?
(A) It is produced from mulberry-fed silkworms
(B) It has a characteristic golden-brown colour and coarser texture than mulberry silk
(C) It is also called Banarasi silk
(D) More than one of the above
(E) None of the above

---

**Q47.** Rohtas district shares its southern border with:
(A) Uttar Pradesh only
(B) Nepal
(C) Jharkhand
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following is NOT in Bhagalpur district?
(A) Vikramshila University ruins
(B) NTPC Kahalgaon
(C) Amjhor pyrite mines
(D) More than one of the above
(E) None of the above

---

**Q49.** Sher Shah Suri defeated which Mughal emperor to establish the Sur Empire?
(A) Akbar
(B) Babur
(C) Humayun
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following statements about Bhagalpur is CORRECT?
(A) It is located on the northern bank of the Ganga
(B) It is in western Bihar, near Nepal border
(C) It is in eastern Bihar, on the Ganga, known for silk and Vikramshila ruins
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ DO NOT LOOK UNTIL YOU HAVE ATTEMPTED ALL 50 QUESTIONS

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (B) | LIFO = Last In, First Out |
| 2 | (C) | Empty stack: top = -1 |
| 3 | (C) | Push = O(1), always at top |
| 4 | (B) | Overflow = push into full stack |
| 5 | (B) | Underflow = pop from empty stack |
| 6 | (C) | Full when top == MAX - 1 |
| 7 | (B) | LIFO: last pushed (40) is first popped → 40,30,20,10 |
| 8 | (C) | Peek = read top WITHOUT removing |
| 9 | (C) | Recursion uses call stack internally |
| 10 | (B) | Async transfer = QUEUE, not Stack |
| 11 | (B) | Pushed 3 elements (index 0,1,2) → top = 2 |
| 12 | (B) | Pop removes; Peek only reads |
| 13 | (C) | Browser back button = Stack (LIFO) |
| 14 | (C) | Undo uses Stack |
| 15 | (A) | PUSH 5, PUSH 10, POP(10), PUSH 15, POP(15) → top = 5 |
| 16 | (B) | Infix to Postfix uses Stack |
| 17 | (C) | Stack of size 3 already full → Overflow |
| 18 | (C) | n elements need O(n) space |
| 19 | (B) | DFS uses Stack |
| 20 | (B) | Parenthesis matching uses Stack |
| 21 | (C) | Always at index `top` |
| 22 | (B) | Program stack overflow = deep recursion |
| 23 | (B) | LIFO, one end only |
| 24 | (B) | Tower of Hanoi = recursion = Stack |
| 25 | (B) | Pushed A,B,C,D,E → top=E. Pop E, pop D. top = C |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Rohtas HQ = Sasaram |
| 27 | (C) | Bhagalpur = Tussar (Kosa) silk |
| 28 | (B) | Amjhor = Asia's largest pyrite deposit |
| 29 | (C) | Sher Shah tomb = Sasaram |
| 30 | (B) | Son enters Bihar at Rohtas |
| 31 | (B) | Sultanganj — Ganga flows northward |
| 32 | (C) | Dharmapala (Pala king) built Vikramshila |
| 33 | (B) | NTPC = Kahalgaon, Bhagalpur |
| 34 | (B) | Tussar silkworms feed on Arjun & Sal trees |
| 35 | (B) | Dolphin sanctuary = Sultanganj to Kahalgaon, Bhagalpur |
| 36 | (B) | Son canal irrigation supports paddy |
| 37 | (B) | Grand Trunk Road + Rupee currency |
| 38 | (B) | Anga Mahajanapada — capital Champa |
| 39 | (B) | GI tag = product tied to specific geography |
| 40 | (B) | Dalmianagar = cement + paper |
| 41 | (B) | Rohtasgarh Fort = Kaimur Hills |
| 42 | (C) | Bakhtiyar Khilji destroyed Vikramshila (1203 CE) |
| 43 | (B) | Gangetic dolphin = India's National Aquatic Animal |
| 44 | (B) | Indrapuri Barrage = Son river, Rohtas |
| 45 | (B) | Kanwar Yatra starts at Sultanganj, Bhagalpur |
| 46 | (B) | Tussar = golden-brown, coarser than mulberry |
| 47 | (C) | Rohtas south border = Jharkhand |
| 48 | (C) | Amjhor pyrite = Rohtas, NOT Bhagalpur |
| 49 | (C) | Sher Shah defeated Humayun |
| 50 | (C) | Bhagalpur = eastern Bihar, Ganga, silk, Vikramshila |

---
---

# 🔁 DAY 16 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Stack Data Structure

### Core Rules — One-Liners:
1. **LIFO**: Last In = First Out — last pushed is first popped
2. **top = -1**: Initial state = empty stack
3. **Overflow**: Pushing into FULL stack (top == MAX-1)
4. **Underflow**: Popping from EMPTY stack (top == -1)
5. **All operations O(1)**: Push, Pop, Peek, isEmpty, isFull — all constant time
6. **Peek vs Pop**: Peek = read top (no removal); Pop = read AND remove
7. **Recursion uses Stack**: The system call stack is a LIFO structure
8. **NOT Stack**: Asynchronous data transfer → uses QUEUE

### Stack Operations Summary:
```
PUSH:   Check full (top==MAX-1) → top++ → stack[top] = value
POP:    Check empty (top==-1) → value = stack[top] → top-- → return value
PEEK:   Check empty → return stack[top]  (top NOT changed)
isEmpty: return (top == -1)
isFull:  return (top == MAX-1)
```

### Applications of Stack (Must Know All 7):
```
1. Recursion (call stack)
2. Infix → Postfix / Prefix conversion
3. Expression evaluation
4. Parenthesis / Symbol balancing
5. DFS (Depth-First Search)
6. Undo / Backtracking / Browser back
7. Tower of Hanoi
```

### NOT a Stack Application (Exam Trap):
```
❌ Asynchronous data transfer → QUEUE
❌ CPU Scheduling (Round Robin) → QUEUE
❌ BFS → QUEUE
❌ Print spooler → QUEUE
```

### Stack vs Queue — 3-Second Rule:
```
STACK = LIFO = Plates = One end = Recursion/DFS/Undo
QUEUE = FIFO = Queue line = Two ends = Async/BFS/Scheduling
```

---

## ⚡ RAPID FIRE — Bihar Geography: Rohtas & Bhagalpur

### Rohtas Must-Know 7:
```
1. HQ = Sasaram
2. Sher Shah Suri tomb = Sasaram (octagonal, in middle of lake)
3. Grand Trunk Road + Rupee = Sher Shah Suri (from Rohtas)
4. Amjhor = Asia's LARGEST Pyrite deposit
5. Son river enters Bihar at Rohtas (Indrapuri Barrage)
6. Rice Bowl of Bihar (paddy + wheat)
7. Dalmianagar = Cement + Paper industry
```

### Bhagalpur Must-Know 7:
```
1. Silk City of India → Tussar (Kosa) silk → GI tag
2. Tussar silkworms eat Arjun + Sal trees (NOT mulberry)
3. Vikramshila University ruins (Pala era, Dharmapala built it)
4. Vikramshila destroyed by Bakhtiyar Khilji (1203 CE)
5. Sultanganj = Ganga flows NORTHWARD + Kanwar Yatra start
6. NTPC Kahalgaon = Bihar's thermal power plant
7. Vikramshila Gangetic Dolphin Sanctuary (Sultanganj to Kahalgaon)
```

### Key Confusions to Avoid:
```
Rohtas silk?   NO → Bhagalpur has silk
Bhagalpur pyrite? NO → Rohtas (Amjhor) has pyrite
Nalanda University? → Nalanda district (NOT Bhagalpur)
Vikramshila? → Bhagalpur (NOT Nalanda)
Mulberry silk → NOT Bhagalpur → Bhagalpur = Tussar (wild silk)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Stack = LIFO; top starts at -1; Overflow = push when full; Underflow = pop when empty
2. ALL stack operations (push, pop, peek, isEmpty, isFull) = O(1)
3. Recursion uses STACK internally; Asynchronous data transfer uses QUEUE (NOT stack)
4. Rohtas: Sasaram HQ, Sher Shah Suri tomb, Asia's largest pyrite (Amjhor), Rice Bowl, Son river entry
5. Bhagalpur: Silk City (Tussar silk, GI tag), Vikramshila University ruins, NTPC Kahalgaon, Ganga northward flow at Sultanganj

---

*Next: Day 17 — Stack: Expression Conversion (Infix/Postfix/Prefix) + India Geography — Eastern Ghats*
