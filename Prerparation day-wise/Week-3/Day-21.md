# 📅 DAY 21 — BPSC TRE 4.0 TOPPER STUDY MATERIAL
## 🔁 REVISION DAY: Arrays + Stack + Queue (Days 15–20) | GS: India & Bihar Geography
### 🎯 Phase 1 — Week 3 Complete | Target: TOPPER RANK

---

> **⚠️ BPSC EXAM FORMAT REMINDER:**
> Every question = 5 options → **(A) (B) (C) (D) (E)**
> **Option D = "More than one of the above"**
> **Option E = "None of the above"**
> 📌 20–25% of answers are D or E. NEVER mark these blindly — verify each statement!

---

> 🏆 **DAY 21 GOAL:** Consolidate everything from Days 15–20.
> Today you don't learn NEW topics — you MASTER what you already studied.
> A revision day done right is worth 5 new topic days.
> Target on today's 50 questions: **45+ / 50**

---

# ══════════════════════════════════════════════════════
# 🖥️ CS MEGA REVISION — ARRAYS, STACK, QUEUE (Days 15–20)
# ══════════════════════════════════════════════════════

---

## 📌 MASTER CONCEPT 1: ARRAYS AS DATA STRUCTURE

### Quick Visual Recap:

```
ARRAY — CONTIGUOUS MEMORY STORAGE:

 Index:  [0]   [1]   [2]   [3]   [4]   [5]   [6]
 Value:  [10]  [25]  [30]  [45]  [60]  [75]  [90]
          ↑                                    ↑
      Base addr                           Base + 6×(size)
      (arr[0])

★ KEY PROPERTY: Elements stored in CONSECUTIVE memory locations
★ ACCESS: arr[i] = Base_Address + i × (size_of_element)
★ Random access in O(1) — just calculate address!
```

### Arrays — Complete Complexity Table:

```
┌─────────────────────────────────────────────────────────────────┐
│              ARRAY OPERATIONS — TIME COMPLEXITY                 │
├──────────────────────────────┬────────────────┬─────────────────┤
│ Operation                    │ Time           │ Why?            │
├──────────────────────────────┼────────────────┼─────────────────┤
│ Access by index (arr[i])     │ O(1) ★ BEST!   │ Direct formula  │
│ Search (unsorted array)      │ O(N)           │ Must check all  │
│ Search (sorted — binary)     │ O(log N)       │ Divide & conquer│
│ Insertion at END             │ O(1) amortized │ Just add at end │
│ Insertion at BEGINNING       │ O(N)           │ Shift all right │
│ Insertion at MIDDLE (index i)│ O(N)           │ Shift N-i elem. │
│ Deletion at END              │ O(1)           │ Just reduce size│
│ Deletion at BEGINNING        │ O(N)           │ Shift all left  │
│ Deletion at MIDDLE           │ O(N)           │ Shift elements  │
└──────────────────────────────┴────────────────┴─────────────────┘

★ MAIN ADVANTAGE of Array = Random Access in O(1)
★ MAIN DISADVANTAGE = Fixed size; costly insert/delete in middle
```

### Sparse Matrix — PYQ Fact:

```
SPARSE MATRIX:
→ A matrix where MOST elements are ZERO
→ Official definition: Zero elements > (M × N) / 2
  (More than half of elements are zero)

Example (4×4 matrix):
[0]  [0]  [0]  [5]
[0]  [0]  [3]  [0]
[0]  [0]  [0]  [0]
[7]  [0]  [0]  [0]

Only 3 non-zero elements out of 16 → SPARSE MATRIX!
Store efficiently using: Triplet form (row, col, value)
```

---

## 📌 MASTER CONCEPT 2: STACK — COMPLETE REVISION

### Stack Visual:

```
STACK — LIFO (Last In, First Out):

 PUSH →        POP ←
              ┌─────┐
              │  50 │ ← TOP (last pushed, first popped)
              ├─────┤
              │  30 │
              ├─────┤
              │  10 │
              ├─────┤
              │  20 │ ← BOTTOM (first pushed, last popped)
              └─────┘

Real world: Stack of plates — you add on top, take from top!
```

### Stack Operations & Conditions:

```
┌──────────────────────────────────────────────────────────────────┐
│                STACK COMPLETE REFERENCE                         │
├─────────────────────┬────────────────────────────────────────── │
│ Operation           │ Description                               │
├─────────────────────┼───────────────────────────────────────────┤
│ PUSH(item)          │ Insert at TOP; check OVERFLOW first       │
│ POP()               │ Remove from TOP; check UNDERFLOW first    │
│ PEEK / TOP          │ View TOP element WITHOUT removing         │
│ isEmpty()           │ Returns true if stack is empty            │
│ isFull()            │ Returns true if stack is full             │
├─────────────────────┼───────────────────────────────────────────┤
│ OVERFLOW Condition  │ top == MAX_SIZE - 1 (stack is full)       │
│ UNDERFLOW Condition │ top == -1 (stack is empty)                │
└─────────────────────┴───────────────────────────────────────────┘
```

### Stack Applications — THE DEFINITIVE LIST:

```
✅ CORRECT Applications of STACK:
┌─────────────────────────────────────────────────────────────────┐
│ 1. RECURSION — Function calls stored in call stack             │
│ 2. EXPRESSION EVALUATION — Infix to Postfix/Prefix             │
│ 3. BACKTRACKING — Maze solving, undo operations               │
│ 4. STRING REVERSAL — Push all chars, pop them out             │
│ 5. BALANCING SYMBOLS — (), {}, [] matching                    │
│ 6. BROWSER BACK BUTTON — History stored in stack              │
│ 7. FUNCTION CALL MANAGEMENT — Return addresses                │
└─────────────────────────────────────────────────────────────────┘

❌ NOT Applications of Stack (BPSC TRAP!):
→ Asynchronous data transfer between processes → That's QUEUE!
→ BFS (Breadth First Search) → That's QUEUE!
→ CPU Scheduling → That's QUEUE!
→ Printer Spooling → That's QUEUE!
```

### Infix → Postfix Conversion (PYQ Hotspot!):

```
INFIX TO POSTFIX CONVERSION — USES STACK:

OPERATOR PRECEDENCE (High to Low):
^ (Exponent) > * / (Multiply/Divide) > + - (Add/Subtract)

EXAMPLE: Convert A + B * C - D to Postfix

Step-by-step using Stack:

Token  Stack    Output      Action
─────  ─────    ──────      ──────
  A    []       A           Operand → directly to output
  +    [+]      A           Operator → push to stack
  B    [+]      A B         Operand → output
  *    [+ *]    A B         * has higher prec than + → push
  C    [+ *]    A B C       Operand → output
  -    [−]      A B C * +   - lower prec: pop * and + → push -
  D    [−]      A B C * + D Operand → output
 END   []       A B C*+D-   Pop remaining: pop -

POSTFIX: A B C * + D -
Verify: A + (B*C) - D  ✓

TIME COMPLEXITY of Infix to Postfix: O(N)
```

---

## 📌 MASTER CONCEPT 3: QUEUE — COMPLETE REVISION

### All Queue Types at a Glance:

```
┌──────────────────────────────────────────────────────────────────┐
│                   QUEUE FAMILY TREE                             │
│                                                                 │
│                        QUEUE                                    │
│                    (FIFO concept)                               │
│                   /      |       \          \                   │
│           Linear     Circular   Deque   Priority                │
│           Queue      Queue              Queue                   │
│           (Simple)  (Ring Buffer)      (Binary Heap)            │
│                          |                                      │
│                    Input-Restricted                             │
│                    Output-Restricted                            │
└──────────────────────────────────────────────────────────────────┘
```

### Linear Queue:

```
LINEAR QUEUE — FIFO (First In, First Out):

ENQUEUE →  [10][20][30][40][50]  → DEQUEUE
           REAR               FRONT
         (insert here)      (delete here)

Real world: Bank queue — first person to join leaves first!

OVERFLOW:  rear == MAX_SIZE - 1 (queue full)
UNDERFLOW: front == -1 OR front > rear (queue empty)

⚠️ FALSE OVERFLOW PROBLEM:
After some dequeues, front moves right.
Positions 0,1,2... become empty but CANNOT be reused.
Solution: CIRCULAR QUEUE!
```

### Circular Queue Complete Reference:

```
CIRCULAR QUEUE (RING BUFFER):

         [INDEX 0]
        /          \
   [INDEX 5]      [INDEX 1]
      |                |
   [INDEX 4]      [INDEX 2]
        \          /
         [INDEX 3]

rear = (rear + 1) % SIZE    ← THIS creates the circular wrap!
front = (front + 1) % SIZE

┌────────────────────────────────────────────────────────────────┐
│         CIRCULAR QUEUE CONDITIONS — MUST MEMORIZE             │
├──────────────────────────┬─────────────────────────────────────┤
│ Condition                │ Formula                             │
├──────────────────────────┼─────────────────────────────────────┤
│ EMPTY                    │ front == rear == -1                 │
│ FULL                     │ (rear + 1) % SIZE == front          │
│ Enqueue (insert at rear) │ rear = (rear + 1) % SIZE            │
│ Dequeue (delete at front)│ front = (front + 1) % SIZE          │
│ One element remains      │ front == rear (but ≠ -1)            │
│ After last dequeue       │ Reset: front = rear = -1            │
└──────────────────────────┴─────────────────────────────────────┘

WHY CIRCULAR QUEUE? → Avoids MEMORY WASTAGE / False Overflow
ALSO CALLED? → RING BUFFER
```

### Deque — Double-Ended Queue:

```
DEQUE (Double-Ended Queue):

     Insert ←→ [F][E][D][C][B][A] ←→ Delete
     Delete ←→                   ←→ Insert

BOTH ends support INSERT and DELETE!

TWO TYPES:
┌────────────────────────────────────────────────────────────────┐
│ Input-Restricted Deque  │ Insert at ONE end only              │
│                         │ Delete from BOTH ends               │
├────────────────────────────────────────────────────────────────┤
│ Output-Restricted Deque │ Insert from BOTH ends               │
│                         │ Delete from ONE end only            │
└────────────────────────────────────────────────────────────────┘

★ KEY COMPLEXITY TRAP:
Delete from REAR in Singly Linked List = O(N)  ← PYQ!
Delete from REAR in Doubly Linked List = O(1)
(SLL has no backward pointer; must traverse entire list)
```

### Priority Queue:

```
PRIORITY QUEUE:
→ Served by PRIORITY, not arrival order
→ BEST IMPLEMENTATION: Binary Heap
→ Min-Heap: Minimum element served first
→ Max-Heap: Maximum element served first

┌────────────────────────────────────────────────────────────────┐
│ Binary Heap Properties:                                        │
│ • Complete Binary Tree                                         │
│ • Max-Heap: Parent ≥ both children (root = MAX)               │
│ • Min-Heap: Parent ≤ both children (root = MIN)               │
│ • Insert: O(log N) via Heapify Up                             │
│ • Delete: O(log N) via Heapify Down                           │
│ • Build heap: O(N)                                            │
└────────────────────────────────────────────────────────────────┘

Applications:
• Dijkstra's algorithm → Min-Heap
• Huffman coding → Min-Heap  
• CPU Priority Scheduling → Max-Heap
• Round Robin → Circular Queue (NOT Priority Queue!)
```

---

## 📌 MASTER CONCEPT 4: ULTIMATE COMPARISON TABLE

```
┌─────────────────────────────────────────────────────────────────────────┐
│            THE ULTIMATE REVISION TABLE — STACK vs ALL QUEUES            │
├────────────────┬──────────┬──────────┬──────────┬──────────┬────────────┤
│ Feature        │ Stack    │ Linear Q │ Circ. Q  │ Deque    │ Priority Q │
├────────────────┼──────────┼──────────┼──────────┼──────────┼────────────┤
│ Order          │ LIFO     │ FIFO     │ FIFO     │ Both     │ Priority   │
│ Insert at      │ Top      │ Rear     │ Rear     │ Both     │ Any        │
│ Delete from    │ Top      │ Front    │ Front    │ Both     │ Highest    │
│ Overflow cond. │ top=MAX-1│rear=MAX-1│(r+1)%S=f │ Both full│ Heap full  │
│ Underflow cond.│ top=-1   │front=-1  │f=r=-1    │ Both empy│ Heap empty │
│ Also called    │ —        │ —        │Ring Buffer│ —       │ —          │
│ Best impl.     │ Array/LL │ Array/LL │ Array    │ DLL      │ Binary Heap│
│ OS Use         │ Call stk │ Job queue│ Round    │ Thread   │ Priority   │
│                │          │          │ Robin    │ sched.   │ scheduling │
│ Real example   │ Undo btn │ Bank Q   │ Traffic  │ Browser  │ Hospital   │
│                │          │          │ light    │ history  │ emergency  │
└────────────────┴──────────┴──────────┴──────────┴──────────┴────────────┘
```

---

## 📌 MASTER CONCEPT 5: COMMON PYQ TRAPS — REVISION CHECKLIST

```
┌─────────────────────────────────────────────────────────────────────────┐
│                TOP PYQ TRAPS — ARRAYS, STACK, QUEUE                     │
├──────────────────────────────────┬──────────────────────────────────────┤
│ WRONG (common mistake)           │ CORRECT FACT                         │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Before deletion from queue,      │ Check UNDERFLOW                      │
│ check overflow                   │ (is queue empty?)                    │
├──────────────────────────────────┼──────────────────────────────────────┤
│ BFS uses Stack                   │ BFS uses QUEUE                       │
│                                  │ DFS uses STACK                       │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Circular Queue created for       │ Created to avoid MEMORY WASTAGE      │
│ faster access                    │ / False Overflow                     │
├──────────────────────────────────┼──────────────────────────────────────┤
│ front == rear means EMPTY        │ front == rear means ONE ELEMENT      │
│ in circular queue                │ EMPTY is front == rear == -1         │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Recursion uses Queue             │ Recursion uses STACK                 │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Priority Queue best with sorted  │ BINARY HEAP is the best              │
│ array                            │                                      │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Deque rear deletion in SLL =O(1) │ O(N) — no backward pointer           │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Heap Sort is STABLE              │ Heap Sort is NOT stable              │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Array insertion is O(1)          │ Only at END is O(1); middle = O(N)   │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Balancing symbols uses Queue     │ Balancing symbols uses STACK         │
└──────────────────────────────────┴──────────────────────────────────────┘
```

---

## 📌 MASTER CONCEPT 6: FORMULA FLASH SHEET

```
╔══════════════════════════════════════════════════════════════════════╗
║           CS FORMULA FLASH SHEET — DAY 21 REVISION                  ║
╠══════════════════════════════════════════════════════════════════════╣
║ ARRAY:                                                               ║
║   Address of arr[i] = Base + i × element_size                       ║
║   Array access = O(1) | Insertion middle = O(N)                     ║
║   Sparse Matrix: zero elements > (M×N)/2                            ║
╠══════════════════════════════════════════════════════════════════════╣
║ STACK:                                                               ║
║   OVERFLOW: top == MAX_SIZE - 1                                      ║
║   UNDERFLOW: top == -1                                               ║
║   Infix to Postfix: O(N) using Stack                                 ║
╠══════════════════════════════════════════════════════════════════════╣
║ CIRCULAR QUEUE:                                                      ║
║   FULL: (rear + 1) % SIZE == front                                   ║
║   EMPTY: front == rear == -1                                         ║
║   Enqueue: rear = (rear + 1) % SIZE                                  ║
║   Dequeue: front = (front + 1) % SIZE                                ║
╠══════════════════════════════════════════════════════════════════════╣
║ BINARY HEAP:                                                         ║
║   Height of heap: ⌊log₂N⌋                                           ║
║   Left child (0-indexed): 2i + 1                                     ║
║   Right child (0-indexed): 2i + 2                                    ║
║   Parent (0-indexed): (i-1) / 2                                      ║
║   Insert = O(log N) | Delete = O(log N) | Build = O(N)              ║
╠══════════════════════════════════════════════════════════════════════╣
║ SORTING USING HEAPS:                                                 ║
║   Heap Sort: O(N log N) time, O(1) space, NOT stable                ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

# ══════════════════════════════════════════════════════
# 🌏 GS REVISION — INDIA & BIHAR GEOGRAPHY
# ══════════════════════════════════════════════════════
> Reference: Lucent GK — Section 3 (Geography, Pages 157–238) + BPSC PYQ Analysis

---

## 📌 GS SECTION 1: INDIA — PHYSICAL FEATURES

### The 5 Major Physical Divisions of India:

```
INDIA'S PHYSICAL DIVISIONS:

╔══════════════════════════════════════════════════════════════════════╗
║                    INDIA — NORTH TO SOUTH                          ║
╠═══════════════════╦══════════════════════════════════════════════════╣
║ 1. HIMALAYAN      ║ Northern boundary of India                      ║
║    MOUNTAINS      ║ Young fold mountains (youngest in world!)       ║
║                   ║ 3 parallel ranges:                              ║
║                   ║  • Himadri (Greater Himalayas) — highest        ║
║                   ║  • Himachal (Lesser Himalayas) — hill stations  ║
║                   ║  • Shiwalik (Outer Himalayas) — foothills       ║
╠═══════════════════╬══════════════════════════════════════════════════╣
║ 2. NORTHERN       ║ Formed by sediment from Himalayan rivers        ║
║    PLAINS         ║ Also called Indo-Gangetic Plains                ║
║    (Gangetic      ║ Most fertile region of India                    ║
║     Plains)       ║ Bihar lies in this zone!                        ║
╠═══════════════════╬══════════════════════════════════════════════════╣
║ 3. PENINSULAR     ║ Old, hard rock (part of Gondwana Land)          ║
║    PLATEAU        ║ Deccan Plateau — most of South India            ║
║                   ║ Malnad region = hilly part of Karnataka         ║
╠═══════════════════╬══════════════════════════════════════════════════╣
║ 4. COASTAL        ║ East Coast (Coromandel + Northern Circars)      ║
║    PLAINS         ║ West Coast (Konkan + Malabar)                   ║
║                   ║ Western = narrow | Eastern = wider/deltas       ║
╠═══════════════════╬══════════════════════════════════════════════════╣
║ 5. ISLANDS        ║ Andaman & Nicobar (Bay of Bengal)               ║
║                   ║ Lakshadweep (Arabian Sea)                       ║
╚═══════════════════╩══════════════════════════════════════════════════╝
```

### Key Mountain Peaks — PYQ Direct Questions:

```
┌────────────────────────────────────────────────────────────────────┐
│              IMPORTANT MOUNTAIN PEAKS — INDIA                     │
├───────────────────────────┬───────────────────────────────────────┤
│ Peak                      │ Details                               │
├───────────────────────────┼───────────────────────────────────────┤
│ K2 (Godwin Austen)        │ 2nd highest in world (8,611 m)        │
│                           │ In Pakistan-occupied Kashmir          │
│                           │ NOT in India proper                   │
├───────────────────────────┼───────────────────────────────────────┤
│ Kangchenjunga             │ Highest peak IN INDIA (8,586 m)       │
│                           │ Sikkim–Nepal border                   │
│                           │ 3rd highest in the world              │
├───────────────────────────┼───────────────────────────────────────┤
│ Nanda Devi                │ Highest peak entirely IN INDIA        │
│                           │ (7,816 m) — Uttarakhand               │
├───────────────────────────┼───────────────────────────────────────┤
│ Mt. Everest               │ WORLD'S HIGHEST (8,849 m)             │
│                           │ Nepal–Tibet border (NOT in India)     │
├───────────────────────────┼───────────────────────────────────────┤
│ Mahendragiri              │ Highest peak of EASTERN GHATS         │
│                           │ In Odisha (Gajapati district)         │
├───────────────────────────┼───────────────────────────────────────┤
│ Anai Mudi                 │ Highest peak of South India           │
│                           │ Western Ghats, Kerala (2,695 m)       │
└───────────────────────────┴───────────────────────────────────────┘

BPSC TRAP: "Highest peak IN INDIA" → Kangchenjunga
           "Highest peak ENTIRELY in India" → Nanda Devi
           (Kangchenjunga is on Sikkim-Nepal border)
```

---

## 📌 GS SECTION 2: INDIAN RIVERS — COMPLETE GUIDE

### River Systems of India:

```
INDIA'S RIVER SYSTEMS:

╔═══════════════════════════════════════════════════════════════════╗
║              HIMALAYAN RIVERS (Perennial — year-round flow)      ║
╠═══════════════╦══════════════════════════════════════════════════ ║
║ INDUS SYSTEM  ║ Indus, Jhelum, Chenab, Ravi, Beas, Sutlej       ║
║               ║ Mostly in Pakistan (after partition)             ║
║               ║ Indus water treaty: India + Pakistan (1960)      ║
╠═══════════════╬══════════════════════════════════════════════════ ║
║ GANGA SYSTEM  ║ Ganga = NATIONAL RIVER of India                  ║
║               ║ Originates: Gangotri Glacier (Uttarakhand)       ║
║               ║ TRIBUTARIES from North (Left bank):              ║
║               ║  Yamuna, Ghaghra, Gandak, Kosi, Mahananda       ║
║               ║ TRIBUTARIES from South (Right bank):             ║
║               ║  Son, Damodar, Chambal, Ken, Betwa              ║
║               ║ Ganga flows through: UP → Bihar → WB → Bay       ║
╠═══════════════╬══════════════════════════════════════════════════ ║
║ BRAHMAPUTRA   ║ Originates in: Tibet (called Tsangpo in Tibet)   ║
║               ║ Enters India through Arunachal Pradesh           ║
║               ║ Major tributary: Teesta                          ║
║               ║ Forms ISLAND: Majuli (world's largest river isl.)║
╚═══════════════╩══════════════════════════════════════════════════ ║

╔═══════════════════════════════════════════════════════════════════╗
║         PENINSULAR RIVERS (Seasonal — rain dependent)            ║
╠═══════════════╦══════════════════════════════════════════════════ ║
║ WEST FLOWING  ║ Narmada, Tapi/Tapti (flow into Arabian Sea)     ║
║               ║ Flow through RIFT VALLEYS (not regular valleys)  ║
║               ║ Narmada: longest W-flowing river, MP+Gujarat    ║
╠═══════════════╬══════════════════════════════════════════════════ ║
║ EAST FLOWING  ║ Mahanadi, Godavari, Krishna, Kaveri             ║
║               ║ Flow into Bay of Bengal                          ║
║               ║ Form DELTAS at mouth                             ║
╚═══════════════╩══════════════════════════════════════════════════ ║
```

### River PYQ Facts:

```
┌────────────────────────────────────────────────────────────────────┐
│             RIVER FACTS — HIGH BPSC PYQ VALUE                     │
├─────────────────────────────────────────────────────────────────── │
│ Longest river in India: Ganga (approx. 2,525 km)                  │
│ Longest peninsular river: Godavari ("Dakshin Ganga")               │
│ Sacred river: Ganga (National River)                               │
│ Narmada flows in: RIFT VALLEY (not typical valley)                │
│ Majuli island: Brahmaputra river, Assam (world's largest river isl)│
│ Sundarbans delta: Ganga + Brahmaputra (Bangladesh + WB)           │
│ Damodar river: "Sorrow of Bengal" (floods Bengal)                  │
│ Kosi river: "Sorrow of Bihar" (floods Bihar annually)              │
│ Tsangpo (Tibet) = Brahmaputra (India) — SAME RIVER!               │
└────────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS SECTION 3: SOIL TYPES IN INDIA — PYQ EVERY EXAM!

```
┌─────────────────────────────────────────────────────────────────────┐
│              SOIL TYPES OF INDIA — COMPLETE TABLE                  │
├──────────────────┬────────────────────────────────────────────────  │
│ Soil Type        │ Key Facts for BPSC                              │
├──────────────────┼─────────────────────────────────────────────────┤
│ ALLUVIAL ★       │ Most widespread soil in India                   │
│                  │ Found in: Northern Plains (Bihar! UP! Punjab!)  │
│                  │ Most FERTILE soil                               │
│                  │ Old alluvial = Bhangar; New = Khadar            │
│                  │ Best for: Rice, Wheat, Sugarcane, Jute          │
├──────────────────┼─────────────────────────────────────────────────┤
│ BLACK/REGUR ★    │ Also called COTTON SOIL (best for cotton!)      │
│                  │ Found in: Deccan Plateau (Maharashtra, MP, AP)  │
│                  │ High moisture retention                          │
│                  │ Rich in: Iron, Calcium, Potassium               │
│                  │ Also found in: Karnataka, Gujarat               │
├──────────────────┼─────────────────────────────────────────────────┤
│ RED SOIL         │ Red color due to IRON OXIDE (Fe₂O₃)            │
│                  │ Found in: Tamil Nadu, Odisha, parts of AP       │
│                  │ Less fertile; good for: Millet, Tobacco         │
├──────────────────┼─────────────────────────────────────────────────┤
│ LATERITE         │ Formed by leaching in high rainfall areas       │
│                  │ Found in: Kerala, Karnataka, NE India           │
│                  │ Rich in: Iron and Aluminium (after leaching)    │
│                  │ Poor in: Nitrogen, Phosphorus                   │
│                  │ Good for: Tea, Coffee, Cashew                   │
├──────────────────┼─────────────────────────────────────────────────┤
│ DESERT/ARID      │ Found in: Rajasthan (Thar), Gujarat             │
│                  │ Sandy, low moisture, low organic matter         │
│                  │ Limited agriculture; some millets grown         │
├──────────────────┼─────────────────────────────────────────────────┤
│ MOUNTAIN SOIL    │ Found in: Himalayan states (HP, UK, J&K)        │
│                  │ Thin layer, not very fertile                    │
│                  │ Good for: Apple, Tea, Coniferous forests        │
└──────────────────┴─────────────────────────────────────────────────┘

BPSC TRAP: "Black soil found in which states?"
Answer: Maharashtra (most), MP, AP, Karnataka, Gujarat
→ Option D (more than one) is usually correct here!
```

---

## 📌 GS SECTION 4: BIHAR — COMPREHENSIVE GEOGRAPHY (HIGH BPSC VALUE!)

### Bihar — Basic Facts:

```
┌─────────────────────────────────────────────────────────────────────┐
│                   BIHAR — COMPLETE GK PROFILE                      │
├─────────────────────────────────────────────────────────────────────┤
│ State Formation: November 1, 2000 (Jharkhand separated from Bihar) │
│ State Capital: PATNA (on the banks of Ganga)                       │
│ Ancient name of Patna: PATALIPUTRA                                  │
│ Rajdhani: Patna | Official Language: Hindi (Maithili also official)│
├─────────────────────────────────────────────────────────────────────┤
│ LOCATION:                                                           │
│ Latitude: 24°20'N to 27°31'N                                       │
│ Longitude: 83°19'E to 88°17'E                                      │
│ Borders: Nepal (North), WB (East), Jharkhand (South), UP (West)   │
├─────────────────────────────────────────────────────────────────────┤
│ AREA: 94,163 sq km (12th largest state by area)                    │
│ POPULATION: ~104 million (Census 2011)                             │
│ Bihar's % of India's population: 8.58% ← PYQ DIRECT!             │
│ Population Density: 1,106/sq km (highest in India!)               │
├─────────────────────────────────────────────────────────────────────┤
│ DIVISIONS: 9 divisions, 38 districts                               │
│ NEW districts formed in 2023: Increased to 38                     │
│ LARGEST DISTRICT: Paschim Champaran (by area)                      │
│ SMALLEST DISTRICT: Sheohar (by area)                               │
│ MOST POPULOUS DISTRICT: Patna                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Bihar's Rivers — PYQ Hotspot:

```
BIHAR'S RIVERS:

                  NEPAL
    ┌─────────────────────────────────────┐
    │                                     │
    │  Gandak  Kosi  Bagmati  Mahananda  │  ← Enter from Nepal
    │    ↓      ↓      ↓        ↓        │
    │    ↓      ↓      ↓        ↓        │  BIHAR
    │         GANGA (flows E→W)          │
    │              ↑                     │
    │             Son  ← from Jharkhand  │
    └─────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│            BIHAR'S IMPORTANT RIVERS                             │
├──────────────┬────────────────────────────────────────────────── │
│ River        │ Key Facts                                         │
├──────────────┼─────────────────────────────────────────────────  │
│ GANGA ★      │ Main river; flows E-W across Bihar               │
│              │ Enters Bihar at Buxar; exits at Rajmahal (WB)    │
│              │ National river of India                           │
├──────────────┼─────────────────────────────────────────────────  │
│ KOSI ★       │ "Sorrow of Bihar" — floods annually              │
│              │ Comes from Nepal; changes course frequently      │
│              │ Flows through: Supaul, Madhepura, Saharsa        │
│              │ Joins Ganga near: Kursela (Katihar)              │
├──────────────┼─────────────────────────────────────────────────  │
│ GANDAK ★     │ Also called Narayani / Sadanira                  │
│              │ Originates in Nepal                               │
│              │ Joins Ganga at: Hajipur (Vaishali district)      │
├──────────────┼─────────────────────────────────────────────────  │
│ BAGMATI      │ Flows through: Sitamarhi, Muzaffarpur            │
│              │ Joins Kosi near Badlaghat                         │
├──────────────┼─────────────────────────────────────────────────  │
│ KAMLA-BALAN  │ Flows through Madhubani, Darbhanga               │
│              │ Also called Kamla river                           │
├──────────────┼─────────────────────────────────────────────────  │
│ SON ★        │ Flows from RIGHT (south) bank of Ganga           │
│              │ Originates in Amarkantak (MP)                     │
│              │ Joins Ganga near: Arrah / Patna area             │
│              │ Important for: Irrigation in South Bihar         │
├──────────────┼─────────────────────────────────────────────────  │
│ FALGU        │ Flows through Gaya (sacred river)                │
│              │ Associated with Pitru Paksha rituals at Gaya     │
│              │ Mostly dry in surface (underground flow)         │
├──────────────┼─────────────────────────────────────────────────  │
│ MAHANANDA    │ Easternmost river of Bihar                        │
│              │ Flows through Kishanganj, Purnia                 │
└──────────────┴─────────────────────────────────────────────────  │
```

---

## 📌 GS SECTION 5: BIHAR — DISTRICTS & AGRICULTURE (PYQ DIRECT!)

```
┌──────────────────────────────────────────────────────────────────────┐
│        BIHAR DISTRICTS — AGRICULTURE & PRODUCTION PYQ FACTS        │
├──────────────────────────────┬───────────────────────────────────── │
│ Category                     │ District                             │
├──────────────────────────────┼─────────────────────────────────────┤
│ MAX PADDY production ★       │ ROHTAS district ← PYQ DIRECT!      │
│ MAX SILK TEXTILE (Tussar) ★  │ BHAGALPUR district ← PYQ DIRECT!   │
│   (Bhagalpur silk famous!)   │ Also called "Silk City of India"    │
├──────────────────────────────┼─────────────────────────────────────┤
│ MAX WHEAT production         │ West Champaran (Paschim Champaran)  │
├──────────────────────────────┼─────────────────────────────────────┤
│ MAX MAKHANA production       │ Darbhanga, Madhubani (North Bihar)  │
│ (Lotus seeds / Fox nuts)     │ Bihar = 80% of India's Makhana!     │
├──────────────────────────────┼─────────────────────────────────────┤
│ MAX LITCHI production        │ Muzaffarpur (Shahi Litchi — GI tag) │
│ (GI tagged variety)          │ Bihar = world's 2nd largest litchi  │
├──────────────────────────────┼─────────────────────────────────────┤
│ MAX HONEY production         │ West Champaran (Valmiki area)       │
├──────────────────────────────┼─────────────────────────────────────┤
│ HIGHEST RAINFALL district    │ KISHANGANJ (NE Bihar, near Bengal)  │
├──────────────────────────────┼─────────────────────────────────────┤
│ LOWEST RAINFALL area         │ Gaya, Jehanabad (South Bihar)       │
├──────────────────────────────┼─────────────────────────────────────┤
│ MAX FLOOD-PRONE area         │ North Bihar (Kosi belt — Supaul,    │
│                              │ Madhepura, Saharsa, Darbhanga)      │
└──────────────────────────────┴─────────────────────────────────────┘
```

---

## 📌 GS SECTION 6: INDIA GEOGRAPHY — PYQ DIRECT FACTS

### Physical Geography Facts:

```
┌──────────────────────────────────────────────────────────────────────┐
│         INDIA PHYSICAL GEOGRAPHY — MUST-KNOW BPSC FACTS            │
├──────────────────────────────────────────────────────────────────────┤
│ Total area of India: 3,287,263 sq km (7th largest in world)        │
│ India's land boundary: ~15,200 km                                   │
│ India's coastline: ~7,516 km                                        │
│ Southernmost point: Indira Point, Andaman & Nicobar Islands         │
│ Northernmost point: Siachen Glacier, Ladakh (J&K)                  │
│ Westernmost point: Ghuar Mota, Gujarat                              │
│ Easternmost point: Kibithu, Arunachal Pradesh                       │
├──────────────────────────────────────────────────────────────────────┤
│ Tropic of Cancer passes through 8 states:                           │
│ Gujarat, Rajasthan, MP, Chhattisgarh, Jharkhand, WB, Tripura,      │
│ Mizoram                                                             │
│ MEMORY: "Gujarat Rajasthan Mein Chhattisgarhiyon Jhumte Wale        │
│          Tripuriyas Milenge" → GR MC JW TM                         │
├──────────────────────────────────────────────────────────────────────┤
│ Largest state by area: Rajasthan (3,42,239 sq km)                  │
│ Smallest state by area: Goa (3,702 sq km)                          │
│ Most populous state: UP (Uttar Pradesh)                             │
│ Highest population DENSITY state: Bihar (1,106/sq km) ★           │
│ Lowest population density: Arunachal Pradesh                        │
│ Highest urbanization: GOA (most urbanized state) ← PYQ!           │
│ Highest literacy: Kerala (94%)                                      │
│ Lowest literacy: Bihar (~61%) — was lowest for long                │
├──────────────────────────────────────────────────────────────────────┤
│ GHATS COMPARISON:                                                    │
│ Western Ghats: Longer, higher, continuous, windward side = rain     │
│ Eastern Ghats: Shorter, lower, discontinuous, lower rainfall        │
│ Highest in W. Ghats: Anai Mudi (Kerala) = 2,695 m                  │
│ Highest in E. Ghats: Mahendragiri (Odisha) = 1,501 m               │
│ East-West Corridor highway: Porbandar to Silchar                    │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS SECTION 7: IMPORTANT PASSES — PYQ LEVEL

```
┌──────────────────────────────────────────────────────────────────────┐
│                    IMPORTANT MOUNTAIN PASSES                        │
├──────────────────────┬────────────────────────────────────────────── │
│ Pass                 │ Location & Importance                         │
├──────────────────────┼─────────────────────────────────────────────  │
│ ZOJI LA              │ J&K — connects Srinagar to Leh               │
│                      │ Most strategic Himalayan pass                 │
├──────────────────────┼─────────────────────────────────────────────  │
│ ROHTANG PASS         │ Himachal Pradesh (Manali–Lahaul area)         │
│                      │ Now tunnel: Atal Tunnel                       │
├──────────────────────┼─────────────────────────────────────────────  │
│ SHIPKI LA            │ Himachal Pradesh — connects India to Tibet    │
├──────────────────────┼─────────────────────────────────────────────  │
│ NATHU LA             │ Sikkim — India–China trade route             │
│                      │ Reopened in 2006 for trade                   │
├──────────────────────┼─────────────────────────────────────────────  │
│ BOLAN PASS           │ Pakistan (formerly British India)             │
│                      │ Route from India to Afghanistan               │
├──────────────────────┼─────────────────────────────────────────────  │
│ PALAKKAD GAP         │ Western Ghats — between Tamil Nadu & Kerala  │
│                      │ Only major break in Western Ghats            │
│                      │ (Important for transport & climate)          │
└──────────────────────┴─────────────────────────────────────────────  │
```

---

## 📌 GS SECTION 8: LANDFORMS & GEOGRAPHY TERMS — PYQ DIRECT

```
LANDFORMS YOU MUST KNOW:

┌──────────────────────────────────────────────────────────────────────┐
│              LANDFORM TYPES (by agent of formation)                 │
├──────────────────────┬────────────────────────────────────────────── │
│ Agent                │ Landforms formed                              │
├──────────────────────┼─────────────────────────────────────────────  │
│ RIVER action         │ Delta, Floodplain, Gorge, Meander, Oxbow lake│
│                      │ Waterfall, Alluvial fan                       │
├──────────────────────┼─────────────────────────────────────────────  │
│ GLACIER action       │ Cirque, Moraine, Fjord, Glacial trough       │
│                      │ U-shaped valley (glacial), Horn               │
├──────────────────────┼─────────────────────────────────────────────  │
│ WIND action          │ Sand dune, Loess, Yardang (mushroom rock)    │
│                      │ Barchans (crescent-shaped dunes)              │
├──────────────────────┼─────────────────────────────────────────────  │
│ UNDERGROUND          │ Stalactite (hangs from ceiling)               │
│ WATER                │ Stalagmite (rises from floor)                 │
│                      │ Karst topography, Limestone caves             │
└──────────────────────┴─────────────────────────────────────────────  │

MEMORY: STALACTITE vs STALAGMITE
"stalaCtite has a C like Ceiling — it hangs DOWN"
"stalagMite has an M like Mountain — it grows UP"

BPSC PYQ: "Stalactites and Stalagmites are formed by ___?"
Answer: Underground water (not rivers, not glaciers)
```

---

## 📌 GS SECTION 9: GS QUICK-FIRE FACTS — 30 MUST-KNOW GEOGRAPHY FACTS

```
┌──────────────────────────────────────────────────────────────────────┐
│        30 GEOGRAPHY RAPID-FIRE FACTS (PYQ Level — Bihar Focus)     │
├──────────────────────────────────────────────────────────────────────┤
│  1. Bihar population % of India = 8.58% (PYQ DIRECT!)             │
│  2. Bihar highest population density = 1,106/sq km                 │
│  3. Kosi = "Sorrow of Bihar" (floods annually)                     │
│  4. Bihar's Rohtas district = MAX paddy production                 │
│  5. Bihar's Bhagalpur = MAX silk textile ("Silk City")             │
│  6. Bihar's Muzaffarpur = famous for Shahi Litchi (GI tag)         │
│  7. Bihar's Kishanganj = highest rainfall district                 │
│  8. Patna ancient name = Pataliputra                               │
│  9. Ganga enters Bihar at Buxar                                    │
│ 10. Gandak joins Ganga at Hajipur                                  │
│ 11. Malnad region = Karnataka Plateau (hilly part)                 │
│ 12. South Peninsular Upland = part of GONDWANA LAND               │
│ 13. Highest peak Eastern Ghats = Mahendragiri (Odisha)            │
│ 14. East-West Corridor = Silchar to Porbandar highway             │
│ 15. Black soil found in Karnataka AND Gujarat (both!)             │
│ 16. Most urbanized state = GOA (not Maharashtra)                  │
│ 17. India's highest population density state = Bihar              │
│ 18. Stalactites formed by: Underground water (not rivers)         │
│ 19. Largeststate by area = Rajasthan                              │
│ 20. Smallest state by area = Goa                                   │
│ 21. SW Monsoon withdrawal from Hyderabad = 1st October            │
│ 22. Mawsynram = highest rainfall in India (Meghalaya)             │
│ 23. Sundarbans delta = Ganga + Brahmaputra                        │
│ 24. Tsangpo (Tibet) = Brahmaputra in India                        │
│ 25. Anai Mudi = highest peak of South India (Western Ghats)       │
│ 26. Narmada flows in a RIFT VALLEY (not normal valley)            │
│ 27. Alluvial soil = MOST widespread + MOST FERTILE in India       │
│ 28. Laterite soil good for Tea, Coffee, Cashew                    │
│ 29. Majuli = world's largest river island (Brahmaputra, Assam)    │
│ 30. Zoji La pass = connects Srinagar to Leh (J&K)                │
└──────────────────────────────────────────────────────────────────────┘
```

---

# ══════════════════════════════════════════════════════
# 📝 DAY 21 PRACTICE QUESTIONS
# ══════════════════════════════════════════════════════

> ⚠️ **TOPPER'S RULE: Solve ALL 50 questions FIRST — no peeking!**
> The answer key is ONLY at the very end of this document.
> This is a REVISION day — target score: **45+ out of 50!**
> Option D = "More than one of the above" | Option E = "None of the above"

---

## 🖥️ CS QUESTIONS (Q1–Q25): Arrays, Stack, Queue Revision

---

**Q1.** The main advantage of using an Array over a Linked List is:
- (A) Dynamic size — can grow as needed
- (B) Efficient insertion and deletion in the middle
- (C) Random access in O(1) time using index
- (D) More than one of the above
- (E) None of the above

---

**Q2.** What is a SPARSE MATRIX?
- (A) A matrix with more non-zero elements than zero elements
- (B) A matrix where zero elements are more than half of total elements
- (C) A matrix where all elements are zero
- (D) More than one of the above
- (E) None of the above

---

**Q3.** The OVERFLOW condition for a Stack implemented using an array is:
- (A) top == -1
- (B) top == 0
- (C) top == MAX_SIZE - 1
- (D) More than one of the above
- (E) None of the above

---

**Q4.** Which of the following is/are CORRECT applications of a STACK?
- (A) Recursion (function call management)
- (B) Balancing of parentheses and symbols
- (C) Expression evaluation (Infix to Postfix)
- (D) More than one of the above
- (E) None of the above

---

**Q5.** Which of the following is NOT an application of Stack?
- (A) String reversal
- (B) Backtracking in maze problems
- (C) Asynchronous data transfer between two processes
- (D) More than one of the above
- (E) None of the above

---

**Q6.** The time complexity of converting Infix to Postfix expression using a Stack is:
- (A) O(N²)
- (B) O(N log N)
- (C) O(N)
- (D) More than one of the above
- (E) None of the above

---

**Q7.** Convert the infix expression A + B * C to Postfix:
- (A) A B + C *
- (B) A B C * +
- (C) A + B C *
- (D) More than one of the above
- (E) None of the above

---

**Q8.** Before performing a DEQUEUE operation on a Queue, which condition MUST be checked?
- (A) OVERFLOW (is queue full?)
- (B) UNDERFLOW (is queue empty?)
- (C) Both Overflow and Underflow
- (D) More than one of the above
- (E) None of the above

---

**Q9.** The OVERFLOW condition for a Linear Queue is:
- (A) front == -1
- (B) front == rear
- (C) rear == MAX_SIZE - 1
- (D) More than one of the above
- (E) None of the above

---

**Q10.** A Circular Queue is also known as:
- (A) Double Queue
- (B) Ring Buffer
- (C) Priority Buffer
- (D) More than one of the above
- (E) None of the above

---

**Q11.** The FULL condition for a Circular Queue of size N is:
- (A) rear == N - 1
- (B) front == rear
- (C) (rear + 1) % N == front
- (D) More than one of the above
- (E) None of the above

---

**Q12.** In a Circular Queue, the EMPTY condition is:
- (A) front == 0 and rear == 0
- (B) front == -1 and rear == -1
- (C) front == rear and both are positive
- (D) More than one of the above
- (E) None of the above

---

**Q13.** After performing a Dequeue from a Circular Queue that had exactly ONE element, what should front and rear be set to?
- (A) front = 0, rear = 0
- (B) front = -1, rear = -1
- (C) front = rear = SIZE - 1
- (D) More than one of the above
- (E) None of the above

---

**Q14.** The PRIMARY reason for using a Circular Queue instead of a Linear Queue is:
- (A) Faster search time
- (B) To avoid memory wastage / false overflow problem
- (C) To allow insertion at both ends
- (D) More than one of the above
- (E) None of the above

---

**Q15.** In a Deque (Double-Ended Queue):
- (A) Insertion is allowed at both front and rear
- (B) Deletion is allowed at both front and rear
- (C) It stands for Double-Ended Queue
- (D) More than one of the above
- (E) None of the above

---

**Q16.** In an INPUT-RESTRICTED Deque:
- (A) Insertion is allowed at ONE end only
- (B) Deletion is allowed at both ends
- (C) Output is also restricted to one end
- (D) More than one of the above
- (E) None of the above

---

**Q17.** The time complexity of deleting from the REAR in a Deque implemented with a SINGLY LINKED LIST is:
- (A) O(1)
- (B) O(log N)
- (C) O(N)
- (D) More than one of the above
- (E) None of the above

---

**Q18.** Which of the following correctly states the LIFO and FIFO principles?
- (A) Stack = LIFO (Last In, First Out)
- (B) Queue = FIFO (First In, First Out)
- (C) Deque = can implement both LIFO and FIFO
- (D) More than one of the above
- (E) None of the above

---

**Q19.** Which data structure does an Operating System use for ROUND ROBIN CPU scheduling?
- (A) Stack
- (B) Priority Queue (Binary Heap)
- (C) Circular Queue
- (D) More than one of the above
- (E) None of the above

---

**Q20.** The BEST implementation for a Priority Queue is:
- (A) Sorted Array
- (B) Binary Heap
- (C) Sorted Linked List
- (D) More than one of the above
- (E) None of the above

---

**Q21.** In a MAX-HEAP, which of the following statements is CORRECT?
- (A) The maximum element is always at the root
- (B) Every parent node is greater than or equal to its children
- (C) It is a Complete Binary Tree
- (D) More than one of the above
- (E) None of the above

---

**Q22.** Which algorithm uses BFS (Breadth First Search) for traversal, and which data structure does BFS use?
- (A) BFS uses Stack
- (B) BFS uses Queue
- (C) DFS uses Stack
- (D) More than one of the above
- (E) None of the above

---

**Q23.** What is the time complexity of accessing an element at index i in an Array?
- (A) O(N)
- (B) O(log N)
- (C) O(1)
- (D) More than one of the above
- (E) None of the above

---

**Q24.** Which of the following SORTING algorithms uses a HEAP data structure?
- (A) Merge Sort
- (B) Heap Sort
- (C) Bubble Sort
- (D) More than one of the above
- (E) None of the above

---

**Q25.** A Queue is being used in which of the following REAL-WORLD scenarios?
- (A) Printer spooling (print jobs lined up in order)
- (B) CPU scheduling (process waiting for CPU)
- (C) Keyboard buffer (keystrokes stored in order)
- (D) More than one of the above
- (E) None of the above

---

## 🌏 GS QUESTIONS (Q26–Q50): India & Bihar Geography

---

**Q26.** Which river is known as the "Sorrow of Bihar"?
- (A) Gandak
- (B) Son
- (C) Kosi
- (D) More than one of the above
- (E) None of the above

---

**Q27.** Bihar's population as a percentage of India's total population (Census 2011) is approximately:
- (A) 6.25%
- (B) 10.50%
- (C) 8.58%
- (D) More than one of the above
- (E) None of the above

---

**Q28.** Which district of Bihar is the LARGEST PRODUCER of paddy (rice)?
- (A) Patna
- (B) Muzaffarpur
- (C) Rohtas
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Bhagalpur in Bihar is famous for:
- (A) Shahi Litchi production
- (B) Makhana (Fox nut) production
- (C) Silk textile (Tussar silk) production
- (D) More than one of the above
- (E) None of the above

---

**Q30.** The Gandak river joins the Ganga at:
- (A) Patna
- (B) Hajipur (Vaishali district)
- (C) Buxar
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Which of the following correctly identifies the SOIL TYPE found in the Northern Plains of India (including Bihar)?
- (A) Black soil (Regur)
- (B) Laterite soil
- (C) Alluvial soil
- (D) More than one of the above
- (E) None of the above

---

**Q32.** Black soil (Regur soil) is known as COTTON SOIL because:
- (A) It is the best soil for growing cotton
- (B) It retains moisture well, ideal for cotton cultivation
- (C) It is found mainly in the Deccan Plateau region
- (D) More than one of the above
- (E) None of the above

---

**Q33.** The highest peak of the EASTERN GHATS is:
- (A) Anai Mudi
- (B) Doddabetta
- (C) Mahendragiri
- (D) More than one of the above
- (E) None of the above

---

**Q34.** The "Malnad" region refers to:
- (A) The coastal plain of Kerala
- (B) The hilly plateau region of Karnataka
- (C) The Deccan plateau of Maharashtra
- (D) More than one of the above
- (E) None of the above

---

**Q35.** The East-West Corridor highway in India connects:
- (A) Porbandar to Silchar
- (B) Srinagar to Kanyakumari
- (C) Mumbai to Kolkata
- (D) More than one of the above
- (E) None of the above

---

**Q36.** The Narmada river is different from most Indian rivers because:
- (A) It flows from east to west (not east)
- (B) It flows through a rift valley
- (C) It drains into the Arabian Sea
- (D) More than one of the above
- (E) None of the above

---

**Q37.** Stalactites and Stalagmites are formed by the action of:
- (A) River water (fluvial action)
- (B) Glacial action
- (C) Underground water (groundwater / limestone dissolution)
- (D) More than one of the above
- (E) None of the above

---

**Q38.** Which Indian state has the HIGHEST POPULATION DENSITY?
- (A) Uttar Pradesh
- (B) West Bengal
- (C) Bihar
- (D) More than one of the above
- (E) None of the above

---

**Q39.** The Tropic of Cancer (23.5°N) passes through which of the following Indian states?
- (A) Gujarat
- (B) Madhya Pradesh
- (C) Jharkhand
- (D) More than one of the above
- (E) None of the above

---

**Q40.** The ancient name of PATNA (capital of Bihar) is:
- (A) Vaishali
- (B) Rajgir
- (C) Pataliputra
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Which river flows through GAYA (Bihar), associated with Pitru Paksha rituals?
- (A) Ganga
- (B) Son
- (C) Falgu
- (D) More than one of the above
- (E) None of the above

---

**Q42.** The most URBANIZED STATE in India is:
- (A) Maharashtra
- (B) Tamil Nadu
- (C) Goa
- (D) More than one of the above
- (E) None of the above

---

**Q43.** Which of the following correctly identifies the LARGEST state by area in India?
- (A) Madhya Pradesh
- (B) Maharashtra
- (C) Rajasthan
- (D) More than one of the above
- (E) None of the above

---

**Q44.** The world's LARGEST RIVER ISLAND, Majuli, is located in which river?
- (A) Ganga
- (B) Brahmaputra
- (C) Godavari
- (D) More than one of the above
- (E) None of the above

---

**Q45.** Which district of Bihar is known for the HIGHEST RAINFALL?
- (A) Patna
- (B) Gaya
- (C) Kishanganj
- (D) More than one of the above
- (E) None of the above

---

**Q46.** Which of the following rivers flow from EAST to WEST (unlike most Indian rivers)?
- (A) Narmada
- (B) Tapi (Tapti)
- (C) Mahanadi
- (D) More than one of the above
- (E) None of the above

---

**Q47.** LATERITE soil is best suited for growing which of the following crops?
- (A) Wheat and Rice
- (B) Cotton
- (C) Tea, Coffee, and Cashew
- (D) More than one of the above
- (E) None of the above

---

**Q48.** The Brahmaputra River is known by which name in TIBET?
- (A) Tsangpo
- (B) Teesta
- (C) Dihang
- (D) More than one of the above
- (E) None of the above

---

**Q49.** Which of the following statements about Bihar's geography is/are CORRECT?
- (A) Bihar borders Nepal to the North
- (B) Bihar has 38 districts (as of 2023)
- (C) Paschim Champaran is the largest district by area
- (D) More than one of the above
- (E) None of the above

---

**Q50.** The Son River, which flows through Bihar, originates in:
- (A) Nepal
- (B) Uttarakhand
- (C) Amarkantak (Madhya Pradesh)
- (D) More than one of the above
- (E) None of the above

---
---

# ══════════════════════════════════════════════════════
# ✅ ANSWER KEY WITH EXPLANATIONS — DAY 21
# ══════════════════════════════════════════════════════

> 🔴 **CHECK ONLY AFTER ATTEMPTING ALL 50 QUESTIONS!**
> Revision day target = 45+ out of 50. Be honest about your score!

---

## 🖥️ CS ANSWERS (Q1–Q25)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q1 | **(C)** | Main advantage of Array = Random Access O(1). Dynamic size = LL's advantage. Middle insertion is O(N) for array (disadvantage). |
| Q2 | **(B)** | Sparse Matrix: zero elements > (M×N)/2. More than HALF the elements are zero. |
| Q3 | **(C)** | Stack OVERFLOW: top == MAX_SIZE - 1 (full). UNDERFLOW: top == -1 (empty). |
| Q4 | **(D)** | All three (A, B, C) are correct Stack applications. D = More than one. |
| Q5 | **(C)** | Asynchronous data transfer = QUEUE application, NOT Stack. (A) and (B) ARE stack applications. |
| Q6 | **(C)** | Infix to Postfix = O(N). Each element processed once through the stack. Direct PYQ from TRE 1.0, 2.0. |
| Q7 | **(B)** | A + B * C → B*C first (higher precedence) → result is A B C * + |
| Q8 | **(B)** | Before DEQUEUE → check UNDERFLOW (empty?). Before ENQUEUE → check OVERFLOW. This is a REPEATED PYQ trap! |
| Q9 | **(C)** | Linear Queue OVERFLOW: rear == MAX_SIZE - 1. This is when the rear pointer reaches end of array. |
| Q10 | **(B)** | Circular Queue = Ring Buffer. This is a direct PYQ synonym tested multiple times. |
| Q11 | **(C)** | Circular Queue FULL: (rear + 1) % N == front. The modulo formula is the key. |
| Q12 | **(B)** | EMPTY condition: front == -1 AND rear == -1. NOT front == rear (that means 1 element). |
| Q13 | **(B)** | After last dequeue → queue is empty → reset front = -1, rear = -1 (empty state). |
| Q14 | **(B)** | Circular Queue created to avoid MEMORY WASTAGE / False Overflow. Not faster search or both-end insert. |
| Q15 | **(D)** | All three statements (A, B, C) about Deque are correct. D = More than one. |
| Q16 | **(D)** | Both (A) and (B) are correct for Input-Restricted Deque. (C) is WRONG — output is NOT restricted. D = More than one (A and B only). |
| Q17 | **(C)** | Singly LL rear deletion = O(N). Must traverse whole list to find second-last node. |
| Q18 | **(D)** | All three (A, B, C) are correct. Deque can implement both LIFO (use one end) and FIFO (use both). D = More than one. |
| Q19 | **(C)** | Round Robin = Circular Queue. Each process gets a fixed time slice, then moves to back of circular queue. |
| Q20 | **(B)** | BINARY HEAP is the BEST for Priority Queue. O(log N) for both insert and delete. |
| Q21 | **(D)** | All three (A, B, C) correctly describe Max-Heap. D = More than one. |
| Q22 | **(D)** | Both (B) and (C) are correct: BFS uses Queue, DFS uses Stack. D = More than one. (A) is WRONG. |
| Q23 | **(C)** | Array element access = O(1). Direct address calculation: Base + i × element_size. |
| Q24 | **(B)** | Heap Sort uses Binary Heap. Merge Sort uses divide & conquer (merging). Bubble Sort uses comparisons. |
| Q25 | **(D)** | All three (A, B, C) are correct Queue applications. D = More than one. |

---

## 🌏 GS ANSWERS (Q26–Q50)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q26 | **(C)** | Kosi = "Sorrow of Bihar." Changes course frequently, floods North Bihar annually. |
| Q27 | **(C)** | Bihar = 8.58% of India's population (Census 2011). PYQ DIRECT question! |
| Q28 | **(C)** | ROHTAS district = highest paddy production in Bihar. PYQ DIRECT! |
| Q29 | **(C)** | Bhagalpur = Tussar Silk (Silk City of India). Muzaffarpur = Litchi. Darbhanga = Makhana. |
| Q30 | **(B)** | Gandak joins Ganga at HAJIPUR (Vaishali district), not Patna. Important Bihar geography fact! |
| Q31 | **(C)** | Northern Plains including Bihar = ALLUVIAL SOIL (most fertile, most widespread). |
| Q32 | **(D)** | All three (A, B, C) statements about Black (Cotton) soil are correct. D = More than one. |
| Q33 | **(C)** | Mahendragiri (Odisha) = highest peak of Eastern Ghats. Anai Mudi = Western Ghats. |
| Q34 | **(B)** | Malnad = hilly plateau/upland region of Karnataka. PYQ DIRECT from TRE papers! |
| Q35 | **(A)** | East-West Corridor = Porbandar (Gujarat) to Silchar (Assam). PYQ DIRECT from TRE analysis! |
| Q36 | **(D)** | All three (A, B, C) are correct about Narmada — it flows W, in rift valley, into Arabian Sea. D = More than one. |
| Q37 | **(C)** | Stalactites/Stalagmites formed by UNDERGROUND WATER dissolving limestone. PYQ DIRECT! |
| Q38 | **(C)** | Bihar has India's HIGHEST population density (1,106/sq km) as per Census 2011. |
| Q39 | **(D)** | All three (A: Gujarat, B: MP, C: Jharkhand) have Tropic of Cancer passing through them. D = More than one. |
| Q40 | **(C)** | Patna's ancient name = PATALIPUTRA (capital of Mauryan Empire). |
| Q41 | **(C)** | Falgu River flows through Gaya. Sacred for Pitru Paksha. Mostly has underground flow. |
| Q42 | **(C)** | GOA is India's most urbanized state (highest % of urban population). PYQ DIRECT! |
| Q43 | **(C)** | RAJASTHAN is India's largest state by area (3,42,239 sq km). MP was largest before 2000. |
| Q44 | **(B)** | Majuli island = Brahmaputra river, Assam = world's largest river island. |
| Q45 | **(C)** | KISHANGANJ = highest rainfall district in Bihar (NE corner, near Bengal border). |
| Q46 | **(D)** | Both Narmada (A) and Tapi/Tapti (B) flow from EAST to WEST. Mahanadi flows East. D = More than one. |
| Q47 | **(C)** | Laterite soil good for Tea, Coffee, Cashew (Kerala, Karnataka, NE India). NOT wheat/rice or cotton. |
| Q48 | **(A)** | Brahmaputra is called TSANGPO in Tibet. (Dihang = name in Arunachal Pradesh). |
| Q49 | **(D)** | All three (A, B, C) statements about Bihar's geography are correct. D = More than one. |
| Q50 | **(C)** | Son River originates at AMARKANTAK in Madhya Pradesh (not Nepal or Uttarakhand). |

---

## 📊 DAY 21 REVISION SCORE TRACKER:

```
┌────────────────────────────────────────────────────────────────┐
│                DAY 21 — REVISION PERFORMANCE                   │
├─────────────────────┬──────────────────────────────────────────┤
│ CS (Q1–Q25)         │ ______ / 25                              │
│ GS (Q26–Q50)        │ ______ / 25                              │
│ TOTAL               │ ______ / 50                              │
├─────────────────────┴──────────────────────────────────────────┤
│ 48–50 → LEGEND Level 🏆 Absolutely topper material!           │
│ 45–47 → TOPPER Level ✅ You're on track for top 10 rank!     │
│ 40–44 → EXCELLENT ✅ Minor gaps — re-read weak sections       │
│ 35–39 → GOOD ⚠️ Revisit Circular Queue conditions & Bihar GK  │
│ Below 35 → NEEDS WORK ❌ Go back to Days 15–20 concepts       │
├────────────────────────────────────────────────────────────────┤
│ D/E ANSWER COUNT:                                              │
│ CS D answers: Q4,Q15,Q18,Q21,Q22,Q25 (+ partial in Q16)      │
│ GS D answers: Q32,Q36,Q39,Q46,Q49                             │
│ If D/E wrong 4+ times → Practice identifying all statements   │
└────────────────────────────────────────────────────────────────┘
```

---

## 🌙 NIGHT REVISION — WRITE FROM MEMORY (No cheating!):

```
CS (write all without looking):
1. STACK OVERFLOW condition: _________ | UNDERFLOW: _________
2. Circular Queue FULL: _________ | EMPTY: _________
3. Circular Queue also called: _________
4. Recursion uses: _________ data structure
5. Priority Queue BEST implementation: _________
6. BFS uses: _________ | DFS uses: _________
7. Deque delete from rear (Singly LL) = O(___)

GS (write all without looking):
1. "Sorrow of Bihar" = _________
2. Bihar % of India's population = _________
3. Rohtas = max _________ | Bhagalpur = max _________
4. Kishanganj = highest _________ in Bihar
5. Gandak meets Ganga at _________
6. Patna ancient name = _________
7. Highest population density state = _________
8. Mahendragiri = highest peak of _________
```

---

## ⚡ DAY 21 COMPLETE CHECKLIST

**CS Revision:**
- [ ] Re-read Array complexity table (O(1) access, O(N) middle insert)
- [ ] Revised Stack LIFO, overflow/underflow, applications list
- [ ] Confirmed all Circular Queue conditions (full, empty, enqueue, dequeue)
- [ ] Confirmed Deque types (Input-Restricted vs Output-Restricted)
- [ ] Recalled Priority Queue = Binary Heap implementation
- [ ] Memorized all PYQ traps (check underflow before dequeue, etc.)

**GS Revision:**
- [ ] India's 5 physical divisions memorized
- [ ] Bihar rivers: Kosi, Gandak, Son, Falgu, Mahananda
- [ ] Bihar agriculture: Rohtas (paddy), Bhagalpur (silk), Muzaffarpur (litchi)
- [ ] Bihar's 8.58% population fact
- [ ] Soil types: Alluvial (N.Plains), Black (Deccan), Laterite (SW India)
- [ ] Key peaks: Kangchenjunga, Mahendragiri, Anai Mudi
- [ ] Bihar density = India's highest

**Practice:**
- [ ] Attempted all 50 questions before looking at answers
- [ ] Score: ______ / 50

---

> 🎯 **DAY 22 PREVIEW:** Linked Lists (Singly & Doubly) | GS: Indian Polity — Fundamental Rights
> **Come back tomorrow: "Day-22"** 🔁
> You have now completed Week 3 of Phase 1 — WELL DONE! 🏆

---
*Day 21 | BPSC TRE 4.0 Topper Study Plan | Phase 1 — Week 3 Complete*
*CS: REVISION — Arrays, Stack, Queue, Circular Queue, Deque, Priority Queue*
*GS: REVISION — India Geography + Bihar Geography (Districts, Rivers, Agriculture)*
*Prepared for: TOPPER RANK | Bihar Public Service Commission Teacher Recruitment Exam 4.0*
