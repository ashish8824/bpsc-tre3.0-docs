# 📅 BPSC TRE 4.0 — DAY 21 COMPLETE REVISION MODULE
### REVISION DAY: Arrays + Stack + Queue (Days 15–20) + GS Geography & Polity
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS Master Revision — Arrays, Stack, Queue, Circular Queue, Deque, Priority Queue
> - Afternoon (1 hr): GS Master Revision — Bihar Geography, Eastern Ghats, Plateau, Monsoon, Constitution
> - Evening (1 hr): Solve all 50 Mixed PYQ MCQs (25 CS + 25 GS)
> - Night (30 min): Write YOUR personal top 10 traps in a notebook

---

# PART 1: CS MASTER REVISION
## ⚡ WEEK 3 RAPID RECALL — Arrays, Stacks, Queues

---

## 🔷 MODULE 1: ARRAYS — One-Line Concepts

```
WHAT:     Fixed-size, contiguous memory, homogeneous elements
ACCESS:   O(1) — address CALCULATED (Base + i×size), NOT searched
INSERT end: O(1) — no shifting needed
INSERT mid: O(n) — elements after insertion point must shift RIGHT
DELETE end: O(1) — just reduce counter
DELETE mid: O(n) — elements after deletion point shift LEFT
TRAVERSE:   O(n) — visit each element once
SEARCH unsorted: O(n) | SEARCH sorted (binary): O(log n)
FIND max/min:    O(n) — must check every element
```

### Array Address Formulas:
```
1D: arr[i] = Base + (i × sizeof(datatype))
2D Row-Major (C++ default): arr[i][j] = Base + (i×cols + j) × size
2D Column-Major (FORTRAN):  arr[i][j] = Base + (j×rows + i) × size

Array name = pointer to base address = &arr[0]
arr[i] ≡ *(arr + i)  ← equivalent expressions
```

### Sparse Matrix:
```
SPARSE when: zero elements > (m × n) / 2  (more than HALF are zero)
Storage: Triplet (row, col, value) — only non-zero elements stored
```

### Spatial Locality:
```
Arrays = CONTIGUOUS memory → neighboring elements load together in CPU cache
→ CACHE-FRIENDLY (fewer cache misses)
Linked List = scattered memory → NOT cache-friendly
```

### Arrays vs Linked Lists — Quick Decide:
```
USE ARRAY WHEN:              USE LINKED LIST WHEN:
✓ Fast random access needed  ✓ Size changes dynamically
✓ Size known and fixed       ✓ Frequent mid-insertions/deletions
✓ Binary search needed       ✓ Random access NOT needed
✓ Cache performance matters  ✓ Memory allocation flexibility
```

---

## 🔷 MODULE 2: STACK — One-Line Concepts

```
WHAT:  LIFO (Last In, First Out) — last pushed = first popped
ANALOGY: Plate stack — add/remove from TOP only
POINTER: top (single pointer, starts at -1)
EMPTY:  top == -1
FULL:   top == MAX - 1
ALL ops: O(1) — Push, Pop, Peek, isEmpty, isFull
```

### Stack Operations — Pseudocode Snapshots:
```
PUSH:  if(top==MAX-1)→OVERFLOW; else top++; stack[top]=value
POP:   if(top==-1)→UNDERFLOW; else value=stack[top]; top--; return value
PEEK:  if(top==-1)→EMPTY; else return stack[top]  (top unchanged!)
```

### Stack Applications — COMPLETE LIST:
```
✅ Recursion (call stack — MOST IMPORTANT)
✅ Infix→Postfix/Prefix conversion
✅ Postfix/Prefix evaluation
✅ Parenthesis/Symbol balancing
✅ DFS (Depth-First Search)
✅ Undo/Redo operations
✅ Browser back button
✅ Tower of Hanoi (recursion)

❌ Asynchronous data transfer → QUEUE (biggest PYQ trap)
❌ BFS → QUEUE
❌ CPU scheduling → QUEUE
❌ Print spooling → QUEUE
```

---

## 🔷 MODULE 3: EXPRESSION CONVERSION — One-Line Concepts

### Three Expression Types:
```
INFIX:   A + B       Operator BETWEEN operands (humans write this)
POSTFIX: A B +       Operator AFTER operands (Reverse Polish Notation)
PREFIX:  + A B       Operator BEFORE operands (Polish Notation)

Postfix/Prefix = NO brackets needed, NO precedence rules during evaluation
```

### Operator Precedence (HIGH → LOW):
```
^ (right assoc) > * / % (left assoc) > + - (left assoc)
Parentheses override everything
```

### Infix → Postfix Algorithm (5 Rules):
```
1. Operand      → directly to OUTPUT
2. '('          → PUSH onto stack
3. ')'          → POP until '('; discard both parentheses
4. Operator     → POP while top has equal/higher precedence → PUSH current
                  (for ^: only pop if STRICTLY higher precedence)
5. End of input → POP ALL remaining stack elements to output
```

### Infix → Prefix (3 Steps):
```
Step 1: Reverse input (swap '(' ↔ ')')
Step 2: Apply postfix algorithm
Step 3: Reverse result
```

### Quick Conversion Table:
```
A + B * C      → Postfix: A B C * +    → Prefix: + A * B C
(A + B) * C    → Postfix: A B + C *    → Prefix: * + A B C
A ^ B ^ C      → Postfix: A B C ^ ^    → Prefix: ^ A ^ B C
A * B + C * D  → Postfix: A B * C D * + → Prefix: + * A B * C D
```

### Postfix Evaluation:
```
Scan L→R: operand→PUSH; operator→POP b(right), POP a(left), PUSH (a OP b)
TRAP: First pop = RIGHT operand; second pop = LEFT operand
Time complexity of conversion = O(N)
```

---

## 🔷 MODULE 4: QUEUE — One-Line Concepts

```
WHAT:  FIFO (First In, First Out) — first enqueued = first dequeued
ANALOGY: Bank line — join from REAR, served from FRONT
POINTERS: TWO: front AND rear (both start at -1)
EMPTY:  front == -1
FULL:   rear == MAX - 1 (linear queue)
ALL ops: O(1) — Enqueue, Dequeue, Peek, isEmpty, isFull
```

### Queue Operations — Pseudocode:
```
ENQUEUE: if(rear==MAX-1)→OVERFLOW; if(front==-1)front=0; rear++; q[rear]=val
DEQUEUE: if(front==-1)→UNDERFLOW;
         val=q[front];
         if(front==rear){front=-1;rear=-1;}  ← last element: reset both
         else front++;
         return val
```

### Linear Queue Problem:
```
rear==MAX-1 → reports OVERFLOW even when front has moved forward
→ Slots at beginning are WASTED (false overflow)
→ SOLUTION: CIRCULAR QUEUE
```

### Queue Applications:
```
✅ BFS (Breadth-First Search)
✅ CPU Scheduling (FCFS, Round Robin)
✅ Print Spooler
✅ Asynchronous data transfer (producer-consumer buffer)
✅ Interrupt handling in OS
✅ Traffic management

❌ Recursion → Stack
❌ DFS → Stack
❌ Symbol balancing → Stack
❌ Undo operations → Stack
```

---

## 🔷 MODULE 5: CIRCULAR QUEUE — All Critical Formulas

```
WHAT: Circular queue solves linear queue's false overflow problem
      rear wraps around using MODULO arithmetic

FORMULAS — MEMORIZE PERFECTLY:
  Empty:         front == -1  (initial state)
  Full:          (rear + 1) % SIZE == front   ← MOST ASKED
  Enqueue rear:  rear = (rear + 1) % SIZE
  Dequeue front: front = (front + 1) % SIZE
  DeleteRear:    rear = (rear - 1 + SIZE) % SIZE  ← (+SIZE avoids negative)
  Elements count:(rear - front + SIZE) % SIZE
  Max capacity:  SIZE - 1 (NOT SIZE — 1 slot reserved!)

After last element dequeued: reset front = -1, rear = -1

Also called: RING BUFFER
Use case:    Round Robin scheduling, keyboard buffer, audio streaming
```

---

## 🔷 MODULE 6: DEQUE — One-Line Concepts

```
WHAT: Double-Ended Queue — insert & delete from BOTH ends
ALL 4 ops: insertFront, insertRear, deleteFront, deleteRear → O(1)
Can simulate BOTH Stack and Queue

INPUT-RESTRICTED:   Insert REAR only; Delete BOTH ends
OUTPUT-RESTRICTED:  Delete FRONT only; Insert BOTH ends

Best implementation: DOUBLY LINKED LIST
  → deleteRear in Singly LL = O(N)   ← KEY PYQ TRAP
  → deleteRear in Doubly LL = O(1)
```

---

## 🔷 MODULE 7: PRIORITY QUEUE — One-Line Concepts

```
WHAT: Elements served by PRIORITY (not insertion order)
Min-Heap: Root = MINIMUM; parent ≤ children
Max-Heap: Root = MAXIMUM; parent ≥ children
SHAPE: Complete Binary Tree (last level left-to-right)

INDEX FORMULAS (0-indexed):
  Left child  = 2i + 1
  Right child = 2i + 2
  Parent      = (i - 1) / 2

TIME COMPLEXITY:
  Insert (heapify up):   O(log n)
  Delete (heapify down): O(log n)
  Peek (root):           O(1)
  Build heap (Floyd's):  O(n)

APPLICATIONS:
  Dijkstra's → Min-Heap
  Huffman Coding → Min-Heap
  CPU Priority Scheduling → Max-Heap
  Prim's MST → Min-Heap

OS QUEUES:
  Job Queue   → All submitted processes (long-term scheduler)
  Ready Queue → In RAM, waiting for CPU (short-term scheduler)
  Device Queue→ Waiting for specific I/O device
```

---

## 📊 MASTER COMPARISON TABLES

### Table 1: Stack vs Queue vs Deque

```
Feature          Stack (LIFO)    Queue (FIFO)    Deque
──────────────────────────────────────────────────────
Principle        LIFO            FIFO            Both ends
Pointers         1 (top)         2 (front,rear)  2 (front,rear)
Insert at front  YES (push)      NO              YES
Insert at rear   NO              YES (enqueue)   YES
Delete at front  YES (pop)       YES (dequeue)   YES
Delete at rear   NO              NO              YES
Order preserved  REVERSED        SAME order      Depends
BFS/DFS          DFS             BFS             Either
Recursion        YES             NO              NO
Undo/Backtrack   YES             NO              YES
```

### Table 2: Linear Queue vs Circular Queue

```
Feature              Linear Queue        Circular Queue
──────────────────────────────────────────────────────────
Memory reuse         NO (false overflow)  YES
Full condition       rear == MAX-1        (rear+1)%SIZE == front
Empty condition      front == -1          front == -1
Rear update formula  rear++               rear = (rear+1)%SIZE
Max elements         MAX                  SIZE - 1
Applications         Simple FIFO          Buffers, Round Robin
```

### Table 3: Queue vs Priority Queue

```
Feature              Queue (normal)      Priority Queue
──────────────────────────────────────────────────────────
Order principle      FIFO                Priority-based
Insertion            At rear             By priority
Deletion             Front (FIFO)        Highest priority first
Implementation       Array/LL            Binary Heap
Insert complexity    O(1)                O(log n)
Delete complexity    O(1)                O(log n)
Use case             BFS, scheduling     Dijkstra's, Huffman
```

### Table 4: Time Complexity — MASTER SUMMARY

```
Operation        Array   Stack  Queue  Circular Q  Heap(PQ)
──────────────────────────────────────────────────────────────
Access by index  O(1)    O(1)   O(1)   O(1)         —
Insert at end    O(1)    O(1)   O(1)   O(1)         O(log n)
Insert at middle O(n)    —      —      —            —
Delete at end    O(1)    O(1)   —      —            —
Delete at front  O(n)    —      O(1)   O(1)         —
Delete max/min   O(n)    —      —      —            O(log n)
Peek max/min     O(n)    O(1)*  O(1)*  O(1)*        O(1)
Traverse         O(n)    O(n)   O(n)   O(n)         O(n)
Search           O(n)    O(n)   O(n)   O(n)         O(n)
Build from n     —       —      —      —            O(n)
*top/front peek
```

---

## 🚨 TOP 15 PYQ TRAPS — CS (Days 15–20)

```
TRAP 1:  Array access O(1) because address CALCULATED, not searched
TRAP 2:  sizeof() does NOT evaluate expression; sizeof(x++) → x unchanged
TRAP 3:  Sparse matrix: zero elements > m×n/2 (not "all zeros")
TRAP 4:  Asynchronous data transfer → QUEUE (NOT Stack!)
TRAP 5:  Stack top starts at -1 (not 0)
TRAP 6:  bool = 1 BYTE (not 1 bit)
TRAP 7:  Postfix evaluation: first pop = RIGHT operand, not left
TRAP 8:  ^ is RIGHT-associative; A^B^C = A^(B^C) → postfix: A B C ^ ^
TRAP 9:  Parentheses NEVER appear in postfix or prefix output
TRAP 10: Circular Queue max elements = SIZE-1 (not SIZE)
TRAP 11: (rear+1)%SIZE == front → FULL (not rear == front)
TRAP 12: deleteRear in Singly Linked List = O(N) (not O(1)!)
TRAP 13: Heap shape = COMPLETE binary tree (not full, not perfect)
TRAP 14: Build heap from n elements using Floyd's = O(n) (not O(n log n))
TRAP 15: Ready Queue in OS ≠ always FIFO; can be Priority Queue
```

---
---

# PART 2: GS MASTER REVISION
## ⚡ GEOGRAPHY & POLITY RAPID RECALL (Days 15–20)

---

## 🔷 GS MODULE 1: Bihar Geography — Rivers Quick Recall

### North Bihar Rivers (Himalayan — PERENNIAL, FLOOD-PRONE):
```
River         Districts              Special Fact
────────────────────────────────────────────────────────────────
Ganga         Buxar→Patna→Bhagalpur  Enters Bihar at BUXAR; Patna on SOUTH bank
Kosi          Supaul→Saharsa→Katihar "SORROW OF BIHAR" — course changes; 2008 flood
Gandak        W.Champaran→Vaishali   Meets Ganga at HAJIPUR; Valmiki Tiger Reserve
Bagmati       Sitamarhi→Darbhanga    Sacred; Sitamarhi connection (Sita's birthplace myth)
Kamla-Balan   Madhubani              Madhubani painting region
Mahananda     Kishanganj→Katihar     Tea gardens in Kishanganj
Burhi Gandak  Muzaffarpur            Separate from Gandak (smaller)
```

### South Bihar Rivers (Peninsular — SEASONAL):
```
Son     → Amarkantak (MP) → meets Ganga near Patna south bank; "Sone" = Gold
Punpun  → Jharkhand → Gaya, Patna area
Falgu   → Gaya → Sacred (underground flow; "cursed river")
```

### Most Flood-Prone: "SSMD + Champaran"
```
Supaul + Saharsa + Madhepura (Kosi floods) + Darbhanga + W/E Champaran (Gandak)
```

### Bihar Agriculture Specials:
```
Muzaffarpur → Shahi Litchi (GI tag)
Hajipur (Vaishali) → Banana capital
Darbhanga/Katihar → Makhana (80–90% world production, GI tag 2022)
Kishanganj → Tea gardens
Bhagalpur → Tussar (Kosa) silk (GI tag)
```

---

## 🔷 GS MODULE 2: Rohtas & Bhagalpur Quick Recall

### ROHTAS (7 Must-Know):
```
1. HQ = Sasaram
2. Sher Shah Suri tomb = Sasaram (octagonal, in middle of lake)
3. Grand Trunk Road + Rupee currency = Sher Shah Suri (born near Sasaram)
4. Amjhor = Asia's LARGEST Pyrite (iron sulphide) deposit
5. Son river enters Bihar at Rohtas (Indrapuri Barrage)
6. Rice Bowl of Bihar (paddy + wheat, Son canal irrigation)
7. Dalmianagar = Cement + Paper industry
```

### BHAGALPUR (7 Must-Know):
```
1. Silk City of India → Tussar (Kosa) silk → GI tag
2. Tussar silkworms eat Arjun + Sal trees (NOT mulberry)
3. Vikramshila University ruins (Pala king Dharmapala built; Bakhtiyar Khilji destroyed 1203 CE)
4. Sultanganj = Ganga flows NORTHWARD + Kanwar Yatra start
5. NTPC Kahalgaon = Bihar's only thermal power plant
6. Vikramshila Gangetic Dolphin Sanctuary (national aquatic animal)
7. Ancient Anga Mahajanapada capital (Champa)
```

---

## 🔷 GS MODULE 3: Eastern Ghats Quick Recall

```
KEY WORD: DISCONTINUOUS (most important exam fact)
Coast:    Eastern coast (Coromandel) / Bay of Bengal
States:   "OATT" = Odisha, AP, Telangana, Tamil Nadu
Highest:  Mahendragiri (Odisha) ~1,501 m
Meet:     Eastern + Western Ghats meet at NILGIRI HILLS
Rivers:   "My Great King Came" = Mahanadi → Godavari → Krishna → Kaveri
Forests:  Tropical DRY DECIDUOUS (NOT evergreen)

EASTERN vs WESTERN GHATS:
  Eastern = DISCONTINUOUS, Lower, Drier, Bay of Bengal, Mahendragiri
  Western = CONTINUOUS, Higher, Wetter, Arabian Sea, Anamudi (2,695m)
  Western = UNESCO World Heritage + Global Biodiversity Hotspot

KEY LANDMARKS:
  Simlipal (Odisha) = Tiger Reserve + Biosphere Reserve
  Nagarjunasagar-Srisailam (AP/TG) = Largest tiger reserve by area
  Papi Hills (Godavari gorge through Eastern Ghats)
  Doddabetta = highest in Nilgiri Hills (2,637 m)
```

---

## 🔷 GS MODULE 4: Peninsular Plateau Quick Recall

### Structure:
```
Narmada DIVIDES Peninsular Plateau:
  NORTH → Central Highlands (Malwa, Chota Nagpur, Bundelkhand)
  SOUTH → Deccan Plateau (Maharashtra, Karnataka, AP, TN)
```

### 5 Must-Know Facts:
```
1. Narmada + Tapi = ONLY west-flowing peninsular rivers
   → Rift valley origin → NO DELTA → ESTUARY at mouth
2. Narmada + Son = SAME origin (Amarkantak) → OPPOSITE directions
3. Chota Nagpur = "Mineral Heartland" (Coal, Iron, Copper, Mica, Uranium)
   → Jaduguda (Jharkhand) = India's FIRST uranium mine
4. Regur (Black Cotton) Soil = Deccan Trap basalt weathering → good for Cotton
5. Godavari = "Dakshin Ganga" = LONGEST peninsular river
```

### Key Peaks:
```
Dhupgarh (1,350 m) = highest in Satpura = highest in MP
Parasnath (1,350 m) = highest in Jharkhand (sacred Jain site)
Pachmarhi = only hill station in MP (Satpura range)
```

### River Nicknames:
```
Godavari → Dakshin Ganga, Vridha Ganga    Kaveri → Ponni (Tamil)
Narmada  → Life Line of Madhya Pradesh    Son → "Sone" (gold)
```

---

## 🔷 GS MODULE 5: Monsoon System Quick Recall

```
SW MONSOON (June–Sept):
  → 75–80% of India's total annual rainfall
  → Onset: June 1 = Kerala → June 20-25 = Bihar → July 1 = Delhi
  → Retreat starts: Rajasthan (Sept 1) → complete by Nov 15
  → Two branches:
      Arabian Sea → hits Western Ghats first
      Bay of Bengal → hits NE India, Bihar, UP, Delhi
  → Bihar source = Bay of Bengal branch

NE MONSOON (Oct–Dec):
  → Affects Tamil Nadu MAINLY (gets rain while rest of India is dry)
  → Tamil Nadu = only state with BOTH SW + NE monsoon

WETTEST: Mawsynram (Meghalaya) → BoB branch + funnel hills
DRIEST:  Rajasthan (Thar Desert)
Rain shadow: East side of Western Ghats = Deccan Plateau = DRY

CROPS:
  Kharif: June–July sow; Sept–Oct harvest → Rice, Maize, Cotton
  Rabi:   Oct–Nov sow; March–April harvest → Wheat, Mustard, Gram
```

---

## 🔷 GS MODULE 6: Indian Constitution Quick Recall

```
KEY DATES:
  Dec 9, 1946   → Constituent Assembly first meeting
  Nov 26, 1949  → Constitution ADOPTED (Constitution Day)
  Jan 26, 1950  → Constitution came into FORCE (Republic Day)

KEY PEOPLE:
  Dr. Rajendra Prasad (BIHAR!) → President of Constituent Assembly + First President
  Dr. B.R. Ambedkar → Chairman of Drafting Committee

KEY FACTS:
  Longest written constitution in the world
  Original: 395 articles, 8 schedules, 22 parts
  2 years, 11 months, 18 days to draft

SOURCES: UK=Parliament, USA=FRs+Judicial Review, Ireland=DPSP, Canada=Federal+Residuary
         USSR=Fundamental Duties, Australia=Concurrent List

6 FUNDAMENTAL RIGHTS (post-1978):
  Equality (14-18) | Freedom (19-22) | Against Exploitation (23-24)
  Religion (25-28) | Cultural/Education (29-30) | Constitutional Remedies (32)

DPSP (Part IV, Art 36-51):
  → Non-justiciable (cannot sue govt) | from Ireland | Welfare State goal

42nd Amendment 1976: "Socialist" + "Secular" added to Preamble; Fundamental Duties added
44th Amendment 1978: Right to Property REMOVED from FRs → now legal right (Art 300A)
86th Amendment 2002: Right to Education (Art 21A) for 6-14 year olds added

7th Schedule: Union List (97), State List (66), Concurrent List (52)
8th Schedule: 22 Scheduled Languages (Maithili added 2003 — 92nd Amendment)
Residuary Powers → UNION (not States, unlike USA)
Art 32 = "Heart and Soul" (Dr. Ambedkar's words)
```

---

## 🚨 TOP 15 PYQ TRAPS — GS (Days 15–20)

```
TRAP 1:  Kosi = "Sorrow of Bihar" — course changes + floods (NOT because it's small)
TRAP 2:  Narmada + Son = SAME SOURCE (Amarkantak) → flow OPPOSITE directions
TRAP 3:  Narmada/Tapi = RIFT VALLEY → estuary (NO delta)
TRAP 4:  Eastern Ghats = DISCONTINUOUS; Western Ghats = CONTINUOUS
TRAP 5:  Highest Eastern Ghats = Mahendragiri (Odisha); Highest WG = Anamudi (Kerala)
TRAP 6:  Bhagalpur silk = TUSSAR (not mulberry); feeds on Arjun+Sal trees
TRAP 7:  Amjhor (Rohtas) = Asia's LARGEST pyrite deposit (not bauxite!)
TRAP 8:  NE Monsoon = Tamil Nadu (Oct-Dec); SW Monsoon = June 1 Kerala onset
TRAP 9:  Mawsynram = wettest (not Cherrapunji — both in Meghalaya)
TRAP 10: Constitution ADOPTED Nov 26 ≠ came into force Jan 26 (different dates!)
TRAP 11: "Socialist"+"Secular" = NOT original Preamble; added 42nd Amendment 1976
TRAP 12: FRs = 6 (Right to Property removed 1978 by 44th Amendment)
TRAP 13: DPSP = NON-JUSTICIABLE (not enforceable in courts)
TRAP 14: Residuary powers → UNION (not States, unlike USA)
TRAP 15: Art 32 = Constitutional Remedies = "Heart and Soul" (Ambedkar's quote)
```

---

# PART 3: MIXED PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 Mixed PYQ MCQs (Days 15–20)

---

**Q1.** What is the main advantage of arrays over linked lists?
(A) Dynamic size
(B) Efficient insertion in middle
(C) O(1) random access using index
(D) More than one of the above
(E) None of the above

---

**Q2.** A 5×6 matrix has 22 zero elements. Is it a sparse matrix?
(A) No, because not all elements are zero
(B) Yes, because 22 > (5×6)/2 = 15
(C) No, because the matrix needs to be square
(D) More than one of the above
(E) None of the above

---

**Q3.** In a Stack, after pushing 5 elements into an array-based stack (initially empty), what is the value of `top`?
(A) 5
(B) 4
(C) -1
(D) More than one of the above
(E) None of the above

---

**Q4.** Which of the following uses STACK internally?
(A) CPU job scheduling
(B) Print spooler
(C) Recursive function calls
(D) More than one of the above
(E) None of the above

---

**Q5.** Convert the infix expression `(A + B) * (C - D)` to Postfix:
(A) A B + C D - *
(B) * + A B - C D
(C) A + B * C - D
(D) More than one of the above
(E) None of the above

---

**Q6.** Evaluate the Postfix expression `6 2 3 + * 5 -`:
(A) 25
(B) 35
(C) 25
(D) More than one of the above
(E) None of the above

---

**Q7.** In the Infix to Postfix conversion algorithm, when we encounter a RIGHT parenthesis `)`, we:
(A) Push it onto the stack
(B) Pop all operators until LEFT parenthesis is found and discard both parentheses
(C) Clear the entire stack
(D) More than one of the above
(E) None of the above

---

**Q8.** In a Queue, if front=3 and rear=7 (linear queue, MAX=10), how many elements are in the queue?
(A) 4
(B) 5
(C) 7
(D) More than one of the above
(E) None of the above

---

**Q9.** Which statement is TRUE about Circular Queue?
(A) It can store exactly SIZE elements
(B) It uses (rear+1)%SIZE to wrap rear around
(C) It has the same false overflow problem as linear queue
(D) More than one of the above
(E) None of the above

---

**Q10.** In a Circular Queue of SIZE=7, if front=5 and rear=3, how many elements does it contain?
(A) 2
(B) 3
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q11.** An Input-Restricted Deque:
(A) Allows insertion only from the rear; deletion from both ends
(B) Allows deletion only from the front; insertion from both ends
(C) Allows insertion and deletion from both ends without restriction
(D) More than one of the above
(E) None of the above

---

**Q12.** In a Min-Heap, which operation is performed after INSERTING a new element?
(A) Heapify Down (sift down from root)
(B) Heapify Up (new element bubbles up toward root)
(C) Rebuild the entire heap from scratch
(D) More than one of the above
(E) None of the above

---

**Q13.** For a heap array (0-indexed), what is the RIGHT child index of the node at index 3?
(A) 7
(B) 8
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following is the CORRECT full condition for a Circular Queue?
(A) rear == SIZE - 1
(B) front == rear
(C) (rear + 1) % SIZE == front
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the time complexity of the Heapify-Down operation after deleting root from a heap of n elements?
(A) O(1)
(B) O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q16.** Which algorithm uses a Min-Priority Queue (Min-Heap) to find the shortest path in a weighted graph?
(A) BFS
(B) DFS
(C) Dijkstra's Algorithm
(D) More than one of the above
(E) None of the above

---

**Q17.** The "Ready Queue" in an Operating System is maintained by:
(A) Long-term scheduler
(B) Short-term scheduler (CPU Scheduler)
(C) Medium-term scheduler
(D) More than one of the above
(E) None of the above

---

**Q18.** In a Max-Heap, which of the following is NOT guaranteed?
(A) The root is the maximum element
(B) Every parent ≥ its children
(C) The array is sorted in descending order
(D) More than one of the above
(E) None of the above

---

**Q19.** The `deleteRear()` operation in a Deque implemented with a SINGLY Linked List has time complexity:
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q20.** Polish Notation is another name for:
(A) Postfix expression
(B) Infix expression
(C) Prefix expression
(D) More than one of the above
(E) None of the above

---

**Q21.** The time complexity of building a heap from n elements using Floyd's Build-Heap algorithm is:
(A) O(n log n)
(B) O(n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following correctly identifies the operation where the Circular Queue rear wraps to index 0?
(A) When front reaches index 0
(B) When rear = SIZE - 1 and a new enqueue is attempted with available space
(C) When the queue is empty
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly states the relationship between Stack and Queue?
(A) Both use LIFO principle
(B) Stack uses LIFO, Queue uses FIFO; Stack has 1 pointer, Queue has 2 pointers
(C) Stack has 2 pointers, Queue has 1 pointer
(D) More than one of the above
(E) None of the above

---

**Q24.** `sizeof(x++)` where x is an int. What is returned AND what is x's value after?
(A) Returns 4; x is incremented to original_x + 1
(B) Returns 4; x remains UNCHANGED (sizeof doesn't evaluate)
(C) Returns the value of x; x is incremented
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is TRUE about Postfix expressions?
(A) They require parentheses and precedence rules for evaluation
(B) They require precedence rules during evaluation
(C) They require neither parentheses nor precedence rules for evaluation
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 Mixed PYQ MCQs (Days 15–20)

---

**Q26.** Identify the CORRECT statement about the Kosi river:
(A) It is called "Sorrow of Bihar" because it is a small, unimportant river
(B) It originates in the Vindhya mountains
(C) It is called "Sorrow of Bihar" because of frequent course changes causing massive floods
(D) More than one of the above
(E) None of the above

---

**Q27.** Which of the following rivers does NOT originate from Himalayan/Nepal region?
(A) Kosi
(B) Gandak
(C) Son
(D) More than one of the above
(E) None of the above

---

**Q28.** The Ganga flows NORTHWARD at which location in Bihar?
(A) Hajipur
(B) Sultanganj
(C) Buxar
(D) More than one of the above
(E) None of the above

---

**Q29.** Match correctly: Rohtas → Bhagalpur
(A) Rohtas: Silk; Bhagalpur: Pyrite
(B) Rohtas: Pyrite (Amjhor) + Rice Bowl; Bhagalpur: Tussar Silk + Vikramshila
(C) Rohtas: NTPC; Bhagalpur: Sher Shah Suri tomb
(D) More than one of the above
(E) None of the above

---

**Q30.** Which of the following CORRECTLY distinguishes Eastern and Western Ghats?
(A) Eastern = Continuous; Western = Discontinuous
(B) Eastern = Discontinuous; Western = Continuous; Western = higher + biodiversity hotspot
(C) Both are discontinuous; Eastern is higher
(D) More than one of the above
(E) None of the above

---

**Q31.** Mahendragiri, the highest peak of the Eastern Ghats, is in which state?
(A) Andhra Pradesh
(B) Tamil Nadu
(C) Odisha
(D) More than one of the above
(E) None of the above

---

**Q32.** Anamudi, the highest peak of the Western Ghats, is located in:
(A) Karnataka
(B) Tamil Nadu
(C) Kerala
(D) More than one of the above
(E) None of the above

---

**Q33.** Both the Narmada and Son rivers originate from the SAME place. Where?
(A) Nilgiri Hills
(B) Amarkantak (Vindhya-Satpura junction)
(C) Western Ghats (Sahyadri)
(D) More than one of the above
(E) None of the above

---

**Q34.** Why do Narmada and Tapi rivers NOT form deltas?
(A) They are too short
(B) They flow through rift valleys; their mouths form estuaries not deltas
(C) They are completely dammed before reaching the sea
(D) More than one of the above
(E) None of the above

---

**Q35.** The Chota Nagpur Plateau is called the "Mineral Heartland" of India. Which mineral has its FIRST Indian mine in Jharkhand?
(A) Coal
(B) Iron ore
(C) Uranium (Jaduguda)
(D) More than one of the above
(E) None of the above

---

**Q36.** The Southwest Monsoon normally arrives at Kerala on:
(A) July 1
(B) June 1
(C) June 15
(D) More than one of the above
(E) None of the above

---

**Q37.** Which state receives rainfall from BOTH Southwest AND Northeast Monsoon?
(A) Bihar
(B) Maharashtra
(C) Tamil Nadu
(D) More than one of the above
(E) None of the above

---

**Q38.** The Coromandel Coast (Southeast India) receives most rainfall from:
(A) Southwest (June-September) Monsoon
(B) Northeast (October-December) Monsoon
(C) Western Disturbances
(D) More than one of the above
(E) None of the above

---

**Q39.** Bihar's main source of monsoon rainfall is:
(A) Arabian Sea branch of SW Monsoon
(B) Bay of Bengal branch of SW Monsoon
(C) Northeast Monsoon
(D) More than one of the above
(E) None of the above

---

**Q40.** Which of the following is the CORRECT chronological order of events?
(A) Constitution Day (Nov 26) → Republic Day (Jan 26) — in the same year 1950
(B) Constituent Assembly first met (Dec 1946) → Constitution adopted (Nov 1949) → Enforced (Jan 1950)
(C) Republic Day → Constitution Day (within 1950)
(D) More than one of the above
(E) None of the above

---

**Q41.** Who was the Chairman of the Drafting Committee of the Indian Constitution?
(A) Dr. Rajendra Prasad
(B) Jawaharlal Nehru
(C) Dr. B.R. Ambedkar
(D) More than one of the above
(E) None of the above

---

**Q42.** The words "Socialist" and "Secular" in the Preamble were added by:
(A) 44th Amendment Act, 1978
(B) 42nd Amendment Act, 1976
(C) 86th Amendment Act, 2002
(D) More than one of the above
(E) None of the above

---

**Q43.** Currently, India has how many Fundamental Rights?
(A) 7 (original number)
(B) 6 (after 44th Amendment removed Right to Property)
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q44.** Directive Principles of State Policy are:
(A) Enforceable by courts (justiciable)
(B) Non-enforceable guidelines (non-justiciable) for welfare state
(C) More binding than Fundamental Rights
(D) More than one of the above
(E) None of the above

---

**Q45.** The 7th Schedule of the Constitution divides subjects into three lists. Which list covers EDUCATION?
(A) Union List
(B) State List
(C) Concurrent List
(D) More than one of the above
(E) None of the above

---

**Q46.** Residuary powers (subjects not in any list) belong to:
(A) State legislatures
(B) Both Parliament and State equally
(C) Parliament (Union)
(D) More than one of the above
(E) None of the above

---

**Q47.** Article 32 (Right to Constitutional Remedies) was described by Dr. Ambedkar as:
(A) "The Backbone of the Constitution"
(B) "The Heart and Soul of the Constitution"
(C) "The Foundation of Democracy"
(D) More than one of the above
(E) None of the above

---

**Q48.** Maithili language (Bihar) was added to the 8th Schedule by which constitutional amendment?
(A) 71st Amendment
(B) 86th Amendment 2002
(C) 92nd Amendment 2003
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following is CORRECT about the Indian Constitution?
(A) It is an unwritten constitution like the British
(B) India is described as a "Federation of States" in Article 1
(C) India is described as a "Union of States"; the constitution is written and the world's longest
(D) More than one of the above
(E) None of the above

---

**Q50.** Bihar's Dr. Rajendra Prasad is associated with which of the following (choose all that apply)?
(A) President of Constituent Assembly
(B) First President of India
(C) Born in Siwan district, Bihar
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
| 1 | (C) | O(1) random access = main array advantage |
| 2 | (B) | 22 > (5×6)/2 = 15 → YES sparse |
| 3 | (B) | 5 pushes: top goes -1→0→1→2→3→4 = 4 |
| 4 | (C) | Recursive calls use call stack (LIFO) |
| 5 | (A) | (A+B)*(C-D) → postfix: A B + C D - * |
| 6 | (C) | 6 2 3 + * 5 - = 6*(2+3)-5 = 6*5-5 = 30-5 = 25 |
| 7 | (B) | ')' → pop until '('; discard both brackets |
| 8 | (B) | Elements = rear-front+1 = 7-3+1 = 5 |
| 9 | (B) | Circular uses (rear+1)%SIZE to wrap |
| 10 | (C) | (rear-front+SIZE)%SIZE = (3-5+7)%7 = 5%7 = 5 |
| 11 | (A) | Input-restricted: insert rear only; delete both ends |
| 12 | (B) | Insert → new element at end → Heapify UP |
| 13 | (B) | Right child of 3 = 2×3+2 = 8 |
| 14 | (C) | Full: (rear+1)%SIZE == front |
| 15 | (C) | Heapify-Down = O(log n) (tree height) |
| 16 | (C) | Dijkstra's uses Min-Priority Queue |
| 17 | (B) | Short-term (CPU) scheduler manages Ready Queue |
| 18 | (C) | Heap ≠ sorted; only parent≥child, not total order |
| 19 | (C) | Singly LL deleteRear = O(n) traversal needed |
| 20 | (C) | Polish Notation = Prefix; Reverse Polish = Postfix |
| 21 | (B) | Floyd's Build-Heap = O(n) |
| 22 | (B) | Wrap: when rear=SIZE-1 and space exists → rear=(rear+1)%SIZE=0 |
| 23 | (B) | Stack=LIFO/1pointer; Queue=FIFO/2pointers |
| 24 | (B) | sizeof doesn't evaluate; returns 4 (int size); x unchanged |
| 25 | (C) | Postfix: no brackets, no precedence needed during eval |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Kosi = course changes + massive floods = "Sorrow of Bihar" |
| 27 | (C) | Son originates from Amarkantak (MP) — peninsular origin |
| 28 | (B) | Sultanganj (Bhagalpur) — Ganga flows northward |
| 29 | (B) | Rohtas: Amjhor pyrite + Rice Bowl; Bhagalpur: Tussar silk + Vikramshila |
| 30 | (B) | Eastern=Discontinuous; Western=Continuous+higher+hotspot |
| 31 | (C) | Mahendragiri = Odisha |
| 32 | (C) | Anamudi = Kerala (Western Ghats) |
| 33 | (B) | Amarkantak = source of Narmada (W) + Son (E) |
| 34 | (B) | Rift valley rivers → estuary not delta |
| 35 | (C) | Jaduguda (Jharkhand) = India's first uranium mine |
| 36 | (B) | June 1 = SW Monsoon arrives Kerala |
| 37 | (C) | Tamil Nadu = both SW + NE monsoon |
| 38 | (B) | Coromandel Coast = NE monsoon (Oct-Dec) |
| 39 | (B) | Bihar = Bay of Bengal branch of SW Monsoon |
| 40 | (B) | Dec 1946 → Nov 1949 → Jan 1950 (correct sequence) |
| 41 | (C) | Dr. B.R. Ambedkar = Drafting Committee Chairman |
| 42 | (B) | 42nd Amendment 1976 added Socialist + Secular |
| 43 | (B) | 6 FRs (after 44th Amendment 1978) |
| 44 | (B) | DPSP = non-justiciable welfare state guidelines |
| 45 | (C) | Education = Concurrent List (both Union + State) |
| 46 | (C) | Residuary powers → Parliament (Union) |
| 47 | (B) | "Heart and Soul" = Article 32 (Dr. Ambedkar's quote) |
| 48 | (C) | 92nd Amendment 2003 added Maithili to 8th Schedule |
| 49 | (C) | Written, longest, "Union of States" (Art 1) |
| 50 | (D) | All three are correct (A + B + C) |

---
---

# 🔁 DAY 21 — ULTRA-CRISP FINAL NOTES
## "Last 1-Hour Before Exam" Revision Format

---

## ⚡ CS — 60-SECOND RECALL CARDS

### ARRAYS:
```
Access=O(1), Insert/Del mid=O(n), Insert/Del end=O(1)
Sparse: zero>(m×n)/2 | Spatial locality = cache-friendly
Array name = base address pointer | C++ = Row-Major
```

### STACK:
```
LIFO | top starts -1 | Overflow: top==MAX-1 | Underflow: top==-1
All ops O(1) | Applications: Recursion, Postfix, DFS, Undo, Brackets
NOT stack: Async transfer → Queue
```

### EXPRESSION CONVERSION:
```
Postfix = Reverse Polish | Prefix = Polish
Infix→Postfix: O(N) | No brackets in output
^ = RIGHT associative | Eval: first pop = RIGHT operand
A+B*C-D → postfix: A B C * + D - | prefix: - + A * B C D
```

### QUEUE:
```
FIFO | front+rear both start -1 | Two pointers
Overflow: rear==MAX-1 | Underflow: front==-1
Apps: BFS, Async, Print, CPU FCFS | NOT queue: Recursion, DFS
```

### CIRCULAR QUEUE:
```
Full: (rear+1)%SIZE==front | Empty: front==-1
rear update: (rear+1)%SIZE | front update: (front+1)%SIZE
deleteRear: (rear-1+SIZE)%SIZE | Max elements: SIZE-1
Ring Buffer | Round Robin scheduling
```

### DEQUE:
```
All 4 ops O(1) | Input-restricted: insert rear only
Output-restricted: delete front only | Doubly LL = O(1) deleteRear
Singly LL deleteRear = O(N) ← KEY TRAP
```

### PRIORITY QUEUE / HEAP:
```
Complete binary tree | Min-Heap: root=min | Max-Heap: root=max
Insert=O(logn) | Delete=O(logn) | Peek=O(1) | Build(Floyd)=O(n)
0-indexed: Left=2i+1, Right=2i+2, Parent=(i-1)/2
Dijkstra/Huffman/Prim → Min-Heap | CPU scheduling → Max-Heap
```

---

## ⚡ GS — 60-SECOND RECALL CARDS

### BIHAR RIVERS:
```
Kosi=Sorrow of Bihar | Ganga enters Buxar | Patna on south bank
Ganga flows north at Sultanganj | Son+Narmada = Amarkantak origin
Flood: SSMD+Champaran | Bihar rain = Bay of Bengal branch
```

### ROHTAS + BHAGALPUR:
```
Rohtas: Sasaram, Sher Shah tomb, Amjhor pyrite (Asia's largest), Rice Bowl, Son entry
Bhagalpur: Tussar silk (Arjun+Sal), Vikramshila (Dharmapala→Bakhtiyar Khilji 1203)
           NTPC Kahalgaon, Sultanganj northward Ganga, Dolphin Sanctuary
```

### EASTERN/WESTERN GHATS:
```
Eastern=DISCONTINUOUS, Mahendragiri (Odisha), OATT states, Dry deciduous forests
Western=CONTINUOUS, Anamudi (Kerala 2695m), UNESCO+hotspot, Tropical evergreen
BOTH meet at NILGIRI HILLS | Rivers: Mahanadi→Godavari→Krishna→Kaveri
```

### PENINSULAR PLATEAU:
```
Narmada divides: N=Central Highlands, S=Deccan Plateau
Narmada+Tapi: west-flowing, rift valley, ESTUARY (no delta)
Narmada+Son: SAME source (Amarkantak), OPPOSITE directions
Chota Nagpur=Mineral Heartland | Regur=black cotton soil=basalt
Godavari=Dakshin Ganga=LONGEST peninsular river
```

### MONSOON:
```
SW Monsoon: June 1 Kerala → June 20 Bihar → July 1 Delhi; 75-80% rainfall
NE Monsoon: Oct-Dec → Tamil Nadu only
Mawsynram=wettest | Rajasthan=driest | BoB branch → Bihar
Kharif=Rice(June-July) | Rabi=Wheat(Oct-Nov)
```

### CONSTITUTION:
```
Adopted: Nov 26, 1949 | Enforced: Jan 26, 1950
Rajendra Prasad (BIHAR)=CA President+1st President | Ambedkar=Drafting Chair
6 FRs (44th Amend 1978 removed Property) | DPSP=non-justiciable (Ireland)
42nd Amend 1976: Socialist+Secular+FDs | 92nd Amend 2003: Maithili
7th Schedule=3 Lists | 8th Schedule=22 languages | Residuary→Union
Art 32 = "Heart and Soul" (Ambedkar)
```

---

## 🎯 COMMON MISTAKES TO NEVER MAKE AGAIN:

```
CS:
✗ Never say Async data transfer uses Stack → it uses QUEUE
✗ Never say Circular Queue holds SIZE elements → SIZE-1
✗ Never say Build-Heap is O(n log n) → Floyd's is O(n)
✗ Never say Postfix has brackets → NO brackets in Postfix/Prefix
✗ Never say deleteRear in Singly LL is O(1) → it's O(n)
✗ Never say first popped = left operand → first popped = RIGHT operand

GS:
✗ Never confuse Nov 26 (Adopted) with Jan 26 (Enforced)
✗ Never say Socialist/Secular were in original Preamble → added 1976
✗ Never say India has 7 FRs → it's 6 (after 1978)
✗ Never say DPSP is enforceable → it is NOT
✗ Never say residuary powers go to States → they go to UNION
✗ Never confuse Mahendragiri (Eastern Ghats) with Anamudi (Western Ghats)
✗ Never say Narmada forms a delta → it forms an ESTUARY
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Stack=LIFO(1ptr,top=-1) vs Queue=FIFO(2ptrs,both=-1); Circular full=(rear+1)%SIZE==front; max=SIZE-1
2. Postfix: no brackets, O(N); Heap: O(logn) insert/delete; Floyd build=O(n); Dijkstra→Min-Heap
3. Kosi=Sorrow of Bihar; Sultanganj=Ganga flows north; Amarkantak=source of Narmada+Son
4. Eastern Ghats=Discontinuous(Mahendragiri); Western=Continuous(Anamudi,UNESCO hotspot); Meet at Nilgiri
5. Constitution: Nov26=Adopted; Jan26=Enforced; Ambedkar=DraftChair; 6FRs; Socialist+Secular=42nd Amend 1976

---

*Next: Day 22 — Linked Lists: Singly Linked List — Concepts, Operations, Traversal + GS Bihar Economy & Industry*
