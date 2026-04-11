# 📅 DAY 20 — BPSC TRE 4.0 TOPPER STUDY MATERIAL
## CS: Priority Queue, Heaps & Queue Applications | GS: Indian Constitution Basics
### 🎯 Phase 1 — Week 3 | Target: TOP RANK

---

> **⚠️ BPSC EXAM FORMAT REMINDER:**
> Every question = 5 options → **(A) (B) (C) (D) (E)**
> **Option D = "More than one of the above"**
> **Option E = "None of the above"**
> 📌 20–25% of answers are D or E — NEVER skip them mentally!

---

# ══════════════════════════════════════════════════
# 🖥️ COMPUTER SCIENCE — PRIORITY QUEUE, HEAPS & QUEUE APPLICATIONS
# ══════════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A PRIORITY QUEUE?

### The Core Concept

A **Normal Queue (FIFO)** serves elements in order of **arrival time**.
A **Priority Queue** serves elements in order of their **PRIORITY** — not arrival time.

```
NORMAL QUEUE (FIFO):
Arrived First → Served First (like a bank queue)

CUSTOMER 1 (arrived 9:00 AM)
CUSTOMER 2 (arrived 9:05 AM)   → CUSTOMER 1 is served first (arrival order)
CUSTOMER 3 (arrived 9:10 AM)

─────────────────────────────────────────────────────────

PRIORITY QUEUE:
Highest Priority → Served First (like a hospital emergency)

PATIENT A — Minor Injury   (Priority: 3 — LOW)
PATIENT B — Heart Attack   (Priority: 1 — CRITICAL) → Patient B served FIRST!
PATIENT C — Broken Leg     (Priority: 2 — HIGH)

Even though Patient A arrived first, Patient B (heart attack) is treated first!
```

### Priority Queue — Key Rules:

```
┌─────────────────────────────────────────────────────────────┐
│               PRIORITY QUEUE — FUNDAMENTAL RULES            │
├─────────────────────────────────────────────────────────────┤
│ 1. Each element has an associated PRIORITY VALUE            │
│ 2. Element with HIGHEST PRIORITY is dequeued FIRST          │
│ 3. If two elements have SAME priority → FIFO order          │
│ 4. Priority can be: Numerical (1 = highest) or              │
│    Custom-defined (CRITICAL > HIGH > LOW)                   │
└─────────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 2: IMPLEMENTATION OPTIONS — WHICH IS BEST?

### Comparison of all implementations:

```
┌────────────────────────────────────────────────────────────────────┐
│        PRIORITY QUEUE — IMPLEMENTATION COMPARISON                  │
├──────────────────────┬──────────────┬──────────────┬──────────────┤
│ Structure Used       │ Insert       │ Delete-Max   │ Space        │
├──────────────────────┼──────────────┼──────────────┼──────────────┤
│ Unsorted Array       │ O(1)         │ O(N)         │ O(N)         │
│ Sorted Array         │ O(N)         │ O(1)         │ O(N)         │
│ Unsorted Linked List │ O(1)         │ O(N)         │ O(N)         │
│ Sorted Linked List   │ O(N)         │ O(1)         │ O(N)         │
│ ★ BINARY HEAP ★      │ O(log N)     │ O(log N)     │ O(N)         │
│ Fibonacci Heap       │ O(1) amort.  │ O(log N)     │ O(N)         │
└──────────────────────┴──────────────┴──────────────┴──────────────┘

⭐ BINARY HEAP = BEST IMPLEMENTATION for Priority Queue
   WHY? Balanced performance for BOTH insert AND delete
        Neither too slow for insert NOR too slow for delete
```

### ⚡ KEY PYQ FACT:
```
Q: "What is the BEST data structure to implement a Priority Queue?"
A: BINARY HEAP

This has appeared in TRE 1.0, 2.0, and 3.0 papers!
Do NOT say: Array, Linked List, Stack, or BST (they are wrong/suboptimal)
```

---

## 📌 SECTION 3: BINARY HEAP — DEEP DIVE

### What is a Binary Heap?

```
BINARY HEAP PROPERTIES:
┌─────────────────────────────────────────────────────────────┐
│ 1. It is a COMPLETE BINARY TREE                             │
│    (All levels filled except possibly the last,             │
│     and last level filled from LEFT to RIGHT)               │
│                                                             │
│ 2. HEAP PROPERTY must be maintained:                        │
│    → MAX-HEAP: Parent ≥ Both Children (always)              │
│    → MIN-HEAP: Parent ≤ Both Children (always)              │
└─────────────────────────────────────────────────────────────┘
```

### MAX-HEAP Visual:

```
MAX-HEAP EXAMPLE (Parent is always LARGER):

                   [100]              ← ROOT (Maximum element)
                  /     \
               [80]     [90]
              /    \    /   \
           [30]  [60] [50] [70]
           /  \
         [20] [25]

RULE: Every parent ≥ its children
→ 100 ≥ 80, 90   ✓
→ 80 ≥ 30, 60    ✓
→ 90 ≥ 50, 70    ✓
→ 30 ≥ 20, 25    ✓

The MAXIMUM element is ALWAYS at the ROOT!
When we delete → we always remove from ROOT (top)
```

### MIN-HEAP Visual:

```
MIN-HEAP EXAMPLE (Parent is always SMALLER):

                    [5]               ← ROOT (Minimum element)
                  /     \
               [10]     [15]
              /    \    /   \
           [30]  [40] [20] [25]
           /  \
         [50] [60]

RULE: Every parent ≤ its children
→ 5 ≤ 10, 15     ✓
→ 10 ≤ 30, 40    ✓
→ 15 ≤ 20, 25    ✓

The MINIMUM element is ALWAYS at the ROOT!
```

### Array Representation of Heap:

```
A heap is stored as an ARRAY (no need for pointers!)

MAX-HEAP Tree:          Array Storage:
     [100]              Index: [0]  [1]  [2]  [3]  [4]  [5]  [6]
    /      \            Value: [100][80] [90] [30] [60] [50] [70]
  [80]    [90]
  /  \    /  \          FORMULAS for 0-based indexing:
[30][60] [50][70]       ┌─────────────────────────────────────────┐
                        │ Left Child of node at i  = 2i + 1       │
                        │ Right Child of node at i = 2i + 2       │
                        │ Parent of node at i      = (i-1) / 2    │
                        └─────────────────────────────────────────┘

For 1-based indexing:
Left child = 2i | Right child = 2i+1 | Parent = i/2
```

---

## 📌 SECTION 4: HEAP OPERATIONS — HOW IT WORKS

### Insert Operation (HEAPIFY UP / Sift Up):

```
INSERT 85 into the MAX-HEAP:

STEP 1: Add at the END (maintain complete binary tree property)

                   [100]
                  /     \
               [80]     [90]
              /    \    /   \
           [30]  [60] [50] [70]
           /
         [85] ← Inserted here

STEP 2: COMPARE with parent; if larger → SWAP (Heapify Up)
        85 > 30? YES → SWAP

                   [100]
                  /     \
               [80]     [90]
              /    \    /   \
           [85]  [60] [50] [70]
           /
         [30]

STEP 3: Continue comparing 85 with its NEW parent (80)
        85 > 80? YES → SWAP

                   [100]
                  /     \
               [85]     [90]
              /    \    /   \
           [80]  [60] [50] [70]
           /
         [30]

STEP 4: Compare 85 with root (100)
        85 > 100? NO → STOP. Heap property restored!

Time Complexity: O(log N) — height of heap tree
```

### Delete (Extract Max) Operation (HEAPIFY DOWN / Sift Down):

```
DELETE MAX from MAX-HEAP:

STEP 1: Remove the ROOT (100), Replace with LAST element (30)

                    [30]         ← replaced by last element
                  /     \
               [85]     [90]
              /    \    /   \
           [80]  [60] [50] [70]

STEP 2: HEAPIFY DOWN — Compare with children, swap with larger
        30 vs children (85, 90): 90 is largest → SWAP 30 and 90

                    [90]
                  /     \
               [85]     [30]
              /    \    /   \
           [80]  [60] [50] [70]

STEP 3: Continue: 30 vs children (50, 70): 70 > 50 → SWAP 30 and 70

                    [90]
                  /     \
               [85]     [70]
              /    \    /   \
           [80]  [60] [50] [30]

STEP 4: 30 has no children → STOP. Heap property restored!

Time Complexity: O(log N)
```

---

## 📌 SECTION 5: MIN-HEAP vs MAX-HEAP — WHEN TO USE WHICH?

```
┌─────────────────────────────────────────────────────────────────┐
│               MIN-HEAP vs MAX-HEAP                              │
├──────────────────────┬───────────────────┬──────────────────────┤
│ Feature              │ MIN-HEAP           │ MAX-HEAP             │
├──────────────────────┼───────────────────┼──────────────────────┤
│ Root contains        │ MINIMUM element    │ MAXIMUM element      │
│ Heap property        │ Parent ≤ children  │ Parent ≥ children    │
│ Delete removes       │ Minimum first      │ Maximum first        │
│ Used when            │ Find smallest item │ Find largest item    │
│ Application          │ Dijkstra's algo    │ HeapSort (ascending) │
│                      │ Prim's algorithm   │                      │
│ Priority Queue       │ Low value = high   │ High value = high    │
│ Interpretation       │ priority (e.g.,    │ priority             │
│                      │ hospital: 1=critical)│                   │
└──────────────────────┴───────────────────┴──────────────────────┘
```

---

## 📌 SECTION 6: HEAP SORT — USING HEAP TO SORT

### How Heap Sort Works:

```
HEAP SORT — 2 PHASES:

PHASE 1: BUILD A MAX-HEAP from the input array
         Time: O(N)

PHASE 2: EXTRACT MAX repeatedly (N times)
         Each extraction: O(log N)
         Place extracted element at end of array

TOTAL TIME: O(N log N)
SPACE: O(1) — in-place sorting!

EXAMPLE: Sort [5, 3, 8, 1, 9, 2]

Build Max-Heap: [9, 5, 8, 1, 3, 2]
Extract 9 → [8, 5, 2, 1, 3, | 9]   ← 9 placed at end
Extract 8 → [5, 3, 2, 1, | 8, 9]
Extract 5 → [3, 1, 2, | 5, 8, 9]
Extract 3 → [2, 1, | 3, 5, 8, 9]
Extract 2 → [1, | 2, 3, 5, 8, 9]
Extract 1 → [1, 2, 3, 5, 8, 9] ← SORTED! ✓
```

### ⚡ KEY FACTS TO REMEMBER:

```
┌──────────────────────────────────────────────────────────────┐
│          HEAP SORT FACTS (PYQ Level)                        │
├─────────────────────────────────────────────────────────────┤
│ Time Complexity:    O(N log N)  — Best, Worst, Average       │
│ Space Complexity:   O(1)        — In-place!                  │
│ Stability:          NOT stable (equal elements may reorder)  │
│ Best for:           Large datasets where O(N log N) needed   │
│                     and O(1) space is important              │
│ Comparison:         Uses comparisons (comparison-based sort) │
└──────────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 7: REAL-WORLD APPLICATIONS OF PRIORITY QUEUE

```
┌──────────────────────────────────────────────────────────────────┐
│          PRIORITY QUEUE APPLICATIONS (PYQ Hotspot!)             │
├────────────────────────┬─────────────────────────────────────────┤
│ Application            │ How Priority Queue is Used              │
├────────────────────────┼─────────────────────────────────────────┤
│ 1. Dijkstra's          │ Always process the NEAREST (minimum     │
│    Shortest Path       │ distance) unvisited node first          │
│    Algorithm           │ → Uses MIN-HEAP                         │
├────────────────────────┼─────────────────────────────────────────┤
│ 2. Prim's MST          │ Always pick edge with MINIMUM weight    │
│    Algorithm           │ → Uses MIN-HEAP                         │
├────────────────────────┼─────────────────────────────────────────┤
│ 3. Huffman Coding      │ Always merge two nodes with LOWEST      │
│    (Data Compression)  │ frequency first → Uses MIN-HEAP         │
├────────────────────────┼─────────────────────────────────────────┤
│ 4. CPU Scheduling      │ Process with highest priority runs first │
│    (Priority           │ → Uses MAX-HEAP or custom heap          │
│    Scheduling)         │                                         │
├────────────────────────┼─────────────────────────────────────────┤
│ 5. A* Search           │ Explore most promising path first       │
│    Algorithm           │ → Uses MIN-HEAP (f = g + h)             │
├────────────────────────┼─────────────────────────────────────────┤
│ 6. Hospital Emergency  │ Critical patients treated first         │
│    Triage              │ → Real-world analogy                    │
└────────────────────────┴─────────────────────────────────────────┘
```

---

## 📌 SECTION 8: QUEUE APPLICATIONS IN OS (Operating System)

```
QUEUES IN OPERATING SYSTEM:

┌─────────────────────────────────────────────────────────────────┐
│              OS QUEUE TYPES                                     │
├──────────────────┬──────────────────────────────────────────────┤
│ Queue Type       │ Description                                  │
├──────────────────┼──────────────────────────────────────────────┤
│ Job Queue        │ All processes submitted to system            │
│                  │ (waiting to be loaded into memory)           │
├──────────────────┼──────────────────────────────────────────────┤
│ Ready Queue      │ Processes in memory, ready to execute        │
│                  │ Waiting for CPU time                         │
├──────────────────┼──────────────────────────────────────────────┤
│ Device Queue     │ Processes waiting for I/O device             │
│                  │ (printer, disk, etc.)                        │
├──────────────────┼──────────────────────────────────────────────┤
│ Round Robin      │ Uses CIRCULAR QUEUE — equal time slices      │
│ CPU Scheduling   │ for each process                             │
└──────────────────┴──────────────────────────────────────────────┘

MEMORY AID:
Job Queue → NEW processes (outer)
Ready Queue → IN memory, waiting for CPU
Device Queue → Waiting for I/O
```

---

## 📌 SECTION 9: COMPLETE COMPARISON — STACK, QUEUE, PRIORITY QUEUE, DEQUE

```
┌──────────────────────────────────────────────────────────────────────┐
│           MASTER COMPARISON: ALL QUEUE-TYPE STRUCTURES               │
├─────────────────┬──────────┬────────────┬────────────┬──────────────┤
│ Feature         │ Stack    │ Queue      │ Priority Q │ Deque        │
├─────────────────┼──────────┼────────────┼────────────┼──────────────┤
│ Order Principle │ LIFO     │ FIFO       │ Priority   │ Both ends    │
│ Insert at       │ Top      │ Rear       │ Any pos.   │ Front/Rear   │
│ Delete from     │ Top      │ Front      │ Highest    │ Front/Rear   │
│ Best Impl.      │ Array/LL │ Array/LL   │ Bin. Heap  │ DLL          │
│ Main Use        │Recursion │ Scheduling │ Dijkstra   │ Sliding Wndw │
│ OS Use          │Function  │ Ready/Job  │ Priority   │ Thread       │
│                 │calls     │ queue      │ scheduling │ scheduling   │
└─────────────────┴──────────┴────────────┴────────────┴──────────────┘
```

---

## 📌 SECTION 10: ALL QUEUE TYPES — MASTER SUMMARY

```
ALL TYPES OF QUEUES — BPSC TOPPER REFERENCE:

1. SIMPLE / LINEAR QUEUE
   → FIFO, Insertion at rear, Deletion at front
   → Problem: Memory wastage (false overflow)

2. CIRCULAR QUEUE (Ring Buffer)
   → Solves memory wastage problem
   → Full: (rear+1)%SIZE == front
   → Empty: front == rear == -1

3. DOUBLE-ENDED QUEUE (DEQUE)
   → Insert/Delete from BOTH ends
   → Input-Restricted: Insert at ONE end
   → Output-Restricted: Delete from ONE end

4. PRIORITY QUEUE
   → Served based on PRIORITY, not arrival order
   → Best Implementation: BINARY HEAP
   → Min-Heap (smallest first) or Max-Heap (largest first)

5. CIRCULAR DEQUE
   → Combination of Circular Queue + Deque features

★ BPSC TRAP QUESTION:
Q: "Which queue is best implemented using Binary Heap?"
A: Priority Queue (ONLY Priority Queue — not Deque, not Circular Queue!)
```

---

## 📌 SECTION 11: PYQ ANALYSIS — PRIORITY QUEUE & HEAPS

| PYQ Pattern | Paper | Frequency |
|------------|-------|-----------|
| Priority Queue best impl. = Binary Heap | TRE 1.0, 2.0, 3.0 | VERY HIGH |
| Heap Sort time complexity = O(N log N) | TRE 2.0 | High |
| Dijkstra's uses Priority Queue (Min-Heap) | TRE 3.0 | High |
| Max-Heap root = Maximum element | TRE 1.0 | High |
| Min-Heap root = Minimum element | TRE 2.0 | High |
| Heap property definition | TRE 1.0 | Medium |
| CPU Scheduling using Priority Queue | TRE 2.0 | Medium |

### ⚡ QUICK 10-FACT FLASH CARD — CS DAY 20:

```
1. Priority Queue → served by PRIORITY, not arrival order
2. BEST implementation → BINARY HEAP
3. Max-Heap → ROOT = MAXIMUM element; Parent ≥ Children
4. Min-Heap → ROOT = MINIMUM element; Parent ≤ Children
5. Insert/Delete in Binary Heap → O(log N)
6. Build Heap from N elements → O(N)
7. Heap Sort → O(N log N), in-place, NOT stable
8. Dijkstra's algorithm → uses MIN-HEAP (Priority Queue)
9. Huffman coding → uses MIN-HEAP (Priority Queue)
10. Round Robin OS scheduling → uses CIRCULAR QUEUE
```

---

# ══════════════════════════════════════════════════
# 🏛️ GENERAL STUDIES — INDIAN CONSTITUTION BASICS
# ══════════════════════════════════════════════════
> Reference: Lucent GK — Section 4 (Indian Polity & Constitution, Pages 239–318)

---

## 📌 SECTION 12: THE MAKING OF THE INDIAN CONSTITUTION

### Background — How India Got Its Constitution:

```
TIMELINE OF INDIA'S CONSTITUTIONAL JOURNEY:

1858 → Crown takes over from East India Company
       Queen's Proclamation = first hint of governance

1919 → Government of India Act, 1919
       (Montague-Chelmsford Reforms)
       → Introduced DYARCHY (dual government) in provinces
       → Separate electorate for Muslims (controversial)

1935 → Government of India Act, 1935
       ★ MOST IMPORTANT Pre-Constitution Act ★
       → Provided for ALL-INDIA FEDERATION (never implemented)
       → Provincial autonomy introduced
       → Many provisions adopted in Indian Constitution!
       → India's current constitution largely based on this act

1942 → Cripps Mission (failed — Congress rejected)

1946 → CABINET MISSION PLAN
       → Proposed formation of Constituent Assembly
       → Constituent Assembly was established!

December 9, 1946 → FIRST MEETING of Constituent Assembly
       → Temporary Chairman: Dr. Sachchidananda Sinha
       
December 11, 1946 → Dr. RAJENDRA PRASAD elected permanent President
       → B.R. AMBEDKAR elected Chairman of Drafting Committee

November 26, 1949 → Constitution ADOPTED ★ Constitution Day ★
January 26, 1950  → Constitution CAME INTO FORCE ★ Republic Day ★
```

### ⚡ KEY DATES TO REMEMBER (PYQ HOTSPOT!):

```
┌───────────────────────────────────────────────────────────────┐
│          CONSTITUENT ASSEMBLY — KEY FACTS                     │
├───────────────────────────────────────────────────────────────┤
│ First Meeting: December 9, 1946                               │
│ First Temporary Chairman: Dr. Sachchidananda Sinha            │
│ Permanent President of CA: Dr. Rajendra Prasad               │
│ Chairman of Drafting Committee: Dr. B.R. Ambedkar            │
│   (Father of Indian Constitution)                             │
│ Drafting Committee Members: 7 (Ambedkar + 6 others)          │
│ Total Members of CA: Initially ~389 (later ~299 after Part.)  │
│ Time to draft: 2 years, 11 months, 18 days                    │
│ Constitution Adopted: 26 November 1949                        │
│ Constitution Enforced: 26 January 1950 (Republic Day)        │
│ Total Articles originally: 395 Articles, 8 Schedules         │
│ Currently: 448 Articles, 12 Schedules, 25 Parts               │
└───────────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 13: SOURCES OF THE INDIAN CONSTITUTION

```
WHAT INDIA BORROWED FROM WHICH COUNTRY — THE MASTER TABLE:

┌───────────────────────────────────────────────────────────────────┐
│        SOURCES OF INDIAN CONSTITUTION (PYQ EVERY YEAR!)          │
├─────────────────┬─────────────────────────────────────────────────┤
│ Country         │ Features Borrowed                               │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇬🇧 UNITED       │ • Parliamentary form of government              │
│ KINGDOM (UK)    │ • Rule of Law                                   │
│                 │ • Single citizenship                             │
│                 │ • Bicameral Legislature (Lok Sabha + Rajya Sabha)│
│                 │ • Office of CAG (Comptroller & Auditor General) │
│                 │ • Cabinet system / PM's role                     │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇺🇸 USA          │ • Fundamental Rights ★                          │
│                 │ • Independent Judiciary                          │
│                 │ • Judicial Review                                │
│                 │ • Vice-President's role                         │
│                 │ • Removal of Supreme Court judges               │
│                 │ • Preamble concept (inspiration)                 │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇮🇪 IRELAND      │ • Directive Principles of State Policy ★        │
│                 │ • Nomination of Rajya Sabha members              │
│                 │ • Method of Presidential election               │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇨🇦 CANADA       │ • FEDERAL structure with STRONG CENTRE ★        │
│                 │ • Residuary Powers with Centre                  │
│                 │ • Advisory jurisdiction of Supreme Court        │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇦🇺 AUSTRALIA    │ • Concurrent List ★                             │
│                 │ • Freedom of trade between states               │
│                 │ • Joint sitting of Parliament                   │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇿🇦 SOUTH AFRICA │ • Amendment procedure (Article 368)             │
│                 │ • Election of Rajya Sabha members               │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇷🇺 USSR/Russia  │ • Fundamental DUTIES ★                          │
│                 │ • Ideals of Justice (Social, Economic, Political)│
│                 │   in the Preamble                               │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇩🇪 WEIMAR       │ • Suspension of Fundamental Rights              │
│ GERMANY         │   during Emergency                              │
│                 │ • Emergency provisions concept                  │
├─────────────────┼─────────────────────────────────────────────────┤
│ 🇯🇵 JAPAN        │ • Procedure established by Law                  │
│                 │   (Article 21 — Life and Liberty)               │
└─────────────────┴─────────────────────────────────────────────────┘

MEMORY TRICK for top 4 sources:
UK  → PARLIAMENT + CABINET (UK Parliament is famous!)
USA → FUNDAMENTAL RIGHTS (US Bill of Rights = FR)
IRE → DPSP (Ireland is socialist-leaning!)
CAN → STRONG CENTRE (Canada's federal = PM is powerful!)
```

---

## 📌 SECTION 14: THE PREAMBLE — WORD BY WORD ANALYSIS

```
FULL TEXT OF PREAMBLE:

"WE, THE PEOPLE OF INDIA, having solemnly resolved to constitute 
India into a SOVEREIGN SOCIALIST SECULAR DEMOCRATIC REPUBLIC 
and to secure to all its citizens:

JUSTICE, social, economic and political;
LIBERTY of thought, expression, belief, faith and worship;
EQUALITY of status and of opportunity;
and to promote among them all
FRATERNITY assuring the dignity of the individual and the unity
and integrity of the Nation;

IN OUR CONSTITUENT ASSEMBLY this twenty-sixth day of November, 1949,
do HEREBY ADOPT, ENACT AND GIVE TO OURSELVES THIS CONSTITUTION."
```

### Keyword-by-Keyword Explanation:

```
┌──────────────────────────────────────────────────────────────────┐
│              PREAMBLE KEYWORDS — PYQ HOTSPOT                    │
├─────────────────┬────────────────────────────────────────────────┤
│ Keyword         │ Meaning                                        │
├─────────────────┼────────────────────────────────────────────────┤
│ SOVEREIGN       │ Independent; No external authority above India │
│                 │ India is master of its own affairs              │
├─────────────────┼────────────────────────────────────────────────┤
│ SOCIALIST ★     │ Added by 42nd Amendment (1976)                 │
│                 │ State owns means of production                  │
│                 │ Democratic Socialism (not Communist)            │
├─────────────────┼────────────────────────────────────────────────┤
│ SECULAR ★       │ Added by 42nd Amendment (1976)                 │
│                 │ State has no official religion                  │
│                 │ All religions treated equally                   │
├─────────────────┼────────────────────────────────────────────────┤
│ DEMOCRATIC      │ Government by the people (elected reps)        │
│                 │ Universal Adult Suffrage (18 years+)            │
├─────────────────┼────────────────────────────────────────────────┤
│ REPUBLIC        │ Head of State is ELECTED (not hereditary)      │
│                 │ President is elected, not a king                │
├─────────────────┼────────────────────────────────────────────────┤
│ JUSTICE         │ Social, Economic, and Political Justice        │
│                 │ (from USSR/Soviet constitution)                 │
├─────────────────┼────────────────────────────────────────────────┤
│ LIBERTY         │ Of thought, expression, belief, faith, worship │
├─────────────────┼────────────────────────────────────────────────┤
│ EQUALITY        │ Of status AND opportunity                      │
├─────────────────┼────────────────────────────────────────────────┤
│ FRATERNITY      │ Sense of brotherhood; Dignity of individual    │
└─────────────────┴────────────────────────────────────────────────┘

★ 42nd AMENDMENT (1976) = "Mini Constitution"
  Added: "SOCIALIST" + "SECULAR" + "INTEGRITY" to Preamble
  Passed during: Emergency period (Indira Gandhi government)
  
BPSC TRAP: "Which words were ORIGINALLY in Preamble?"
Answer: Sovereign, Democratic, Republic (original)
        Socialist, Secular, Integrity → added by 42nd Amendment
```

---

## 📌 SECTION 15: FUNDAMENTAL RIGHTS — COMPLETE GUIDE

### Six Fundamental Rights:

```
┌────────────────────────────────────────────────────────────────────┐
│              6 FUNDAMENTAL RIGHTS — ARTICLES 12 TO 35             │
├─────┬────────────────────────────┬──────────────────────────────── │
│ No. │ Right                      │ Key Articles & Points           │
├─────┼────────────────────────────┼─────────────────────────────────┤
│  1  │ Right to EQUALITY          │ Art. 14–18                      │
│     │                            │ 14: Equality before law         │
│     │                            │ 15: No discrimination (race,    │
│     │                            │     religion, sex, caste, place)│
│     │                            │ 16: Equal opportunity in jobs   │
│     │                            │ 17: Abolition of UNTOUCHABILITY │
│     │                            │ 18: Abolition of TITLES         │
├─────┼────────────────────────────┼─────────────────────────────────┤
│  2  │ Right to FREEDOM           │ Art. 19–22                      │
│     │                            │ 19: 6 freedoms (speech, assem., │
│     │                            │     association, movement,      │
│     │                            │     residence, profession)      │
│     │                            │ 20: Protection for offences     │
│     │                            │ 21: Life and personal liberty ★ │
│     │                            │ 21A: Free education (6-14 yrs) │
│     │                            │ 22: Protection against arrest   │
├─────┼────────────────────────────┼─────────────────────────────────┤
│  3  │ Right AGAINST              │ Art. 23–24                      │
│     │ EXPLOITATION               │ 23: Prohibition of traffic in   │
│     │                            │     humans & forced labour      │
│     │                            │ 24: Prohibition of child labour │
│     │                            │     (below 14 yrs in factories) │
├─────┼────────────────────────────┼─────────────────────────────────┤
│  4  │ Right to FREEDOM           │ Art. 25–28                      │
│     │ OF RELIGION                │ 25: Freedom of conscience &     │
│     │                            │     religion                    │
│     │                            │ 26: Freedom to manage religious │
│     │                            │     affairs                     │
│     │                            │ 27: No tax for religion         │
│     │                            │ 28: No religious instruction in │
│     │                            │     state-funded schools        │
├─────┼────────────────────────────┼─────────────────────────────────┤
│  5  │ Cultural &                 │ Art. 29–30                      │
│     │ EDUCATIONAL Rights         │ 29: Protection of minorities    │
│     │                            │ 30: Right of minorities to      │
│     │                            │     establish educational inst. │
├─────┼────────────────────────────┼─────────────────────────────────┤
│  6  │ Right to                   │ Art. 32 ★★                      │
│     │ CONSTITUTIONAL             │ "Heart and Soul of Constitution"│
│     │ REMEDIES                   │ — Dr. B.R. Ambedkar             │
│     │                            │ Right to move SC for enforcement│
└─────┴────────────────────────────┴─────────────────────────────────┘

NOTE: Right to PROPERTY was a Fundamental Right (Art. 31)
      REMOVED by 44th Amendment (1978)
      Now it is only a LEGAL RIGHT (Art. 300A)
```

### The 5 WRITS Under Article 32 & 226:

```
5 WRITS — "WEAPON AGAINST GOVERNMENT" — PYQ EVERY TIME!

┌──────────────────────────────────────────────────────────────────┐
│ Writ Name      │ Meaning          │ Used Against/For             │
├────────────────┼──────────────────┼──────────────────────────────┤
│ HABEAS CORPUS  │ "To have the     │ Against ILLEGAL DETENTION    │
│ ★ MOST COMMON  │ body"            │ Court orders: "Produce the   │
│                │                  │ person before court!"        │
├────────────────┼──────────────────┼──────────────────────────────┤
│ MANDAMUS       │ "We command"     │ To compel public authority   │
│                │                  │ to perform their DUTY        │
├────────────────┼──────────────────┼──────────────────────────────┤
│ PROHIBITION    │ "To forbid"      │ Issued to LOWER COURTS to    │
│                │                  │ STOP acting beyond power     │
├────────────────┼──────────────────┼──────────────────────────────┤
│ CERTIORARI     │ "To be           │ To QUASH orders of lower     │
│                │ certified"       │ courts (bring record up)     │
├────────────────┼──────────────────┼──────────────────────────────┤
│ QUO WARRANTO  │ "By what         │ To challenge person's right  │
│                │ authority?"      │ to hold a PUBLIC OFFICE      │
└────────────────┴──────────────────┴──────────────────────────────┘

MEMORY TRICK: "H M P C Q" → "Hum Mange Police Court Quickly"
 H = Habeas Corpus (illegal detention)
 M = Mandamus (command to do duty)
 P = Prohibition (stop lower court)
 C = Certiorari (quash lower court order)
 Q = Quo Warranto (challenge authority)
```

---

## 📌 SECTION 16: DIRECTIVE PRINCIPLES vs FUNDAMENTAL RIGHTS

```
FUNDAMENTAL RIGHTS (FR) vs DIRECTIVE PRINCIPLES (DPSP):

┌──────────────────────────────────────────────────────────────────┐
│              FR vs DPSP — EXAM READY COMPARISON                 │
├─────────────────────┬────────────────────────────────────────────┤
│ Feature             │ Fundamental Rights    │ DPSP               │
├─────────────────────┼───────────────────────┼────────────────────┤
│ Articles            │ Art. 12–35            │ Art. 36–51         │
│ Nature              │ JUSTICIABLE ★         │ NON-JUSTICIABLE ★  │
│                     │ (Court enforceable)   │ (Not enforceable   │
│                     │                       │  in court)         │
│ Purpose             │ Protect individual    │ Guide STATE policy │
│ Negative/Positive   │ Mostly NEGATIVE       │ Mostly POSITIVE    │
│                     │ (State CANNOT do)     │ (State SHOULD do)  │
│ Borrowed from       │ USA (Bill of Rights)  │ Ireland            │
│ Suspension          │ Can be suspended      │ Always apply       │
│                     │ during Emergency      │                    │
└─────────────────────┴───────────────────────┴────────────────────┘

KEY BPSC FACT:
• DPSP = Non-justiciable = Cannot be enforced in court
• FR = Justiciable = CAN be enforced in court
• But both are important for GOVERNANCE
```

---

## 📌 SECTION 17: FUNDAMENTAL DUTIES (Article 51A)

### 11 Fundamental Duties (Added by 42nd Amendment, 1976):

```
FUNDAMENTAL DUTIES — Article 51A
Originally 10 duties (1976), 11th added by 86th Amendment (2002)

┌──────────────────────────────────────────────────────────────────┐
│                   11 FUNDAMENTAL DUTIES                         │
├──────────────────────────────────────────────────────────────────┤
│ 1. Abide by Constitution, respect its ideals                    │
│ 2. Cherish noble ideals of national struggle                    │
│ 3. Uphold and protect sovereignty, unity, integrity of India    │
│ 4. Defend the country, render national service when called upon │
│ 5. Promote harmony and spirit of brotherhood                    │
│ 6. Value and preserve rich heritage of our composite culture    │
│ 7. Protect and improve natural environment                      │
│ 8. Develop scientific temper, humanism, spirit of inquiry      │
│ 9. Safeguard public property, abjure violence                   │
│ 10. Strive towards excellence in all spheres                    │
│ 11. ★ PROVIDE EDUCATION TO CHILD between 6-14 years (86th Amend)│
└──────────────────────────────────────────────────────────────────┘

NOTE: Fundamental Duties are for CITIZENS ONLY (not foreigners)
      They are MORAL duties — NOT legally enforceable
      Borrowed from: SOVIET (USSR) Constitution
```

---

## 📌 SECTION 18: IMPORTANT CONSTITUTIONAL ARTICLES — PYQ MASTER TABLE

```
┌────────────────────────────────────────────────────────────────────┐
│           MOST IMPORTANT ARTICLES — BPSC TRE PYQ LEVEL            │
├────────────┬───────────────────────────────────────────────────────┤
│ Article    │ Topic                                                  │
├────────────┼────────────────────────────────────────────────────────┤
│ Art. 1     │ India = "Union of States" (not "Federation of States") │
│ Art. 3     │ Parliament can create new states / change boundaries   │
│ Art. 12    │ Definition of "State" (for FR purposes)               │
│ Art. 14    │ Equality before law                                    │
│ Art. 17    │ Abolition of Untouchability                           │
│ Art. 19    │ Six Freedoms (speech, assembly, etc.)                 │
│ Art. 21    │ Right to Life and Personal Liberty ★                  │
│ Art. 21A   │ Free and compulsory education (6-14 yrs) — 86th Amdt │
│ Art. 24    │ Prohibition of child labour                           │
│ Art. 32    │ Right to Constitutional Remedies ★ "Heart & Soul"     │
│ Art. 44    │ Uniform Civil Code (DPSP)                             │
│ Art. 51A   │ Fundamental Duties                                     │
│ Art. 72    │ President's power to grant pardons                    │
│ Art. 76    │ Attorney General of India                              │
│ Art. 108   │ Joint Sitting of Parliament                           │
│ Art. 110   │ Definition of Money Bill                              │
│ Art. 112   │ Annual Financial Statement (Budget)                    │
│ Art. 123   │ President's Ordinance making power                    │
│ Art. 148   │ CAG — Comptroller and Auditor General                 │
│ Art. 226   │ High Court's power to issue writs                     │
│ Art. 243   │ Panchayati Raj (73rd Amendment)                       │
│ Art. 280   │ Finance Commission                                     │
│ Art. 300A  │ Right to Property (legal right, not FR)               │
│ Art. 324   │ Election Commission of India                          │
│ Art. 343   │ Official Language = Hindi (Devanagari script)         │
│ Art. 352   │ National Emergency                                     │
│ Art. 356   │ President's Rule (State Emergency)                    │
│ Art. 360   │ Financial Emergency                                    │
│ Art. 368   │ Amendment of Constitution                             │
└────────────┴────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 19: IMPORTANT CONSTITUTIONAL AMENDMENTS — PYQ HOTSPOT

```
┌────────────────────────────────────────────────────────────────────┐
│        KEY CONSTITUTIONAL AMENDMENTS — MUST MEMORIZE              │
├──────────┬─────────────────────────────────────────────────────── │
│ Amendment│ Year │ Key Change                                       │
├──────────┼──────┼──────────────────────────────────────────────── │
│ 1st      │ 1951 │ Added Schedule 9 (land reform laws protection)   │
│ 7th      │ 1956 │ Reorganization of states on linguistic basis     │
│ 24th     │ 1971 │ Parliament can amend any part of Constitution    │
│ 42nd ★★  │ 1976 │ "MINI CONSTITUTION" — Added Socialist, Secular,  │
│          │      │ Integrity to Preamble; Added Fundamental Duties; │
│          │      │ 10th Schedule (anti-defection) — wait, no...     │
│          │      │ Extended emergency period; weakened judiciary     │
│ 44th ★   │ 1978 │ Removed Right to Property from FRs              │
│          │      │ (Janata govt corrected Emergency excesses)       │
│ 52nd     │ 1985 │ Anti-Defection Law (10th Schedule)               │
│ 61st     │ 1989 │ Voting age reduced: 21 → 18 years               │
│ 73rd ★   │ 1992 │ Panchayati Raj — 3-tier system, 11th Schedule   │
│ 74th ★   │ 1992 │ Urban Local Bodies — 12th Schedule               │
│ 86th ★   │ 2002 │ Free education for 6-14 yrs (Art. 21A, 11th FD) │
│ 91st     │ 2003 │ Limited Council of Ministers to 15% of House    │
│ 101st    │ 2016 │ GST (Goods and Services Tax) introduced          │
│ 103rd    │ 2019 │ 10% reservation for EWS (Economically Weaker)   │
│ 104th    │ 2020 │ SC/ST reservation in legislature extended 10 yrs│
└──────────┴──────┴──────────────────────────────────────────────── │

★★ 42nd Amendment (1976) — THE MOST IMPORTANT FOR BPSC:
   Government: Indira Gandhi government during EMERGENCY
   Called: "MINI CONSTITUTION" because it changed so much
   Key additions to PREAMBLE: Socialist, Secular, Integrity
   Also: Added Fundamental Duties (Art. 51A)
   Also: Curtailed Supreme Court's power
```

---

## 📌 SECTION 20: NATIONAL SYMBOLS OF INDIA — PYQ DIRECT QUESTIONS!

```
┌────────────────────────────────────────────────────────────────────┐
│               NATIONAL SYMBOLS OF INDIA                           │
├──────────────────────┬──────────────────────────────────────────── │
│ Symbol               │ Name / Details                              │
├──────────────────────┼───────────────────────────────────────────  │
│ National Flag        │ Tiranga — Saffron, White, Green             │
│                      │ Ratio: 2:3 | Chakra: 24 spokes              │
│ National Emblem      │ Lion Capital of Ashoka (Sarnath)           │
│                      │ Motto: "Satyameva Jayate" (Mundaka Upanishad│
│ National Anthem      │ "Jana Gana Mana" — Rabindranath Tagore ★   │
│                      │ Duration: 52 seconds                        │
│ National Song        │ "Vande Mataram" — Bankim Chandra Chattopadhyay│
│ National Animal      │ Bengal Tiger (Panthera tigris tigris)       │
│ National Bird        │ Indian Peacock (Pavo cristatus)             │
│ National Flower      │ Lotus (Nelumbo nucifera)                    │
│ National Fruit       │ Mango (Mangifera indica)                    │
│ National Tree        │ Indian Banyan (Ficus benghalensis)          │
│ National River       │ Ganga                                       │
│ National Sport       │ Field Hockey (traditional; NOT cricket)     │
│ National Aquatic     │ River Dolphin (Platanista gangetica)        │
│ Animal               │                                             │
│ National Heritage    │ Indian Elephant                             │
│ Animal               │                                             │
└──────────────────────┴───────────────────────────────────────────  │

★ BPSC TRAP: "National Anthem" vs "National Song"
   National ANTHEM = Jana Gana Mana (Tagore) — sung in 52 seconds
   National SONG = Vande Mataram (Bankim Chandra) — NOT the anthem!
   
★ "Satyameva Jayate" is from: MUNDAKA UPANISHAD (not Rigveda!)
```

---

## 📌 SECTION 21: GS QUICK-FIRE FACTS — 25 MUST-KNOW CONSTITUTION FACTS

```
1. Indian Constitution adopted: 26 November 1949 (Constitution Day)
2. Constitution came into force: 26 January 1950 (Republic Day)
3. Time taken to draft: 2 years, 11 months, 18 days
4. Chairman of Drafting Committee: Dr. B.R. Ambedkar
5. President of Constituent Assembly: Dr. Rajendra Prasad
6. Total Articles originally: 395 | Currently: 448
7. Total Schedules originally: 8 | Currently: 12
8. India's Constitution = Largest Written Constitution in the world
9. "Mini Constitution" = 42nd Amendment (1976)
10. Socialist + Secular added by: 42nd Amendment (1976)
11. Voting age reduced to 18 by: 61st Amendment (1989)
12. Right to Property removed by: 44th Amendment (1978)
13. Fundamental Duties added by: 42nd Amendment (1976) — Art. 51A
14. Free Education (6-14) added by: 86th Amendment (2002) — Art. 21A
15. Panchayati Raj established by: 73rd Amendment (1992)
16. Urban Local Bodies established by: 74th Amendment (1992)
17. GST introduced by: 101st Amendment (2016)
18. Article 32 = "Heart and Soul of Constitution" (Ambedkar)
19. Article 21 = Right to Life and Personal Liberty
20. Habeas Corpus writ = against illegal detention
21. DPSP is NON-JUSTICIABLE (cannot be enforced in court)
22. FR is JUSTICIABLE (can be enforced in court)
23. India borrowed Federal+Strong Centre from: CANADA
24. India borrowed DPSP from: IRELAND
25. India borrowed Fundamental Rights from: USA
```

---

# ══════════════════════════════════════════════════
# 📝 DAY 20 PRACTICE QUESTIONS
# ══════════════════════════════════════════════════

> ⚠️ **GOLDEN RULE: Attempt ALL 50 questions FIRST.**
> **The answer key is ONLY at the very end.**
> Covering answers while solving = ACTUAL exam practice!
> Option D = "More than one of the above" | Option E = "None of the above"

---

## 🖥️ CS QUESTIONS (Q1–Q25): Priority Queue, Heap & Queue Applications

---

**Q1.** Which of the following is the BEST data structure to implement a Priority Queue?
- (A) Sorted Array
- (B) Linked List
- (C) Binary Heap
- (D) More than one of the above
- (E) None of the above

---

**Q2.** In a MAX-HEAP, which element is always present at the ROOT?
- (A) The minimum element
- (B) The average of all elements
- (C) The maximum element
- (D) More than one of the above
- (E) None of the above

---

**Q3.** In a MIN-HEAP, the ROOT contains:
- (A) Maximum element
- (B) Minimum element
- (C) The element inserted first
- (D) More than one of the above
- (E) None of the above

---

**Q4.** The time complexity of INSERTING an element into a Binary Heap is:
- (A) O(1)
- (B) O(N)
- (C) O(log N)
- (D) More than one of the above
- (E) None of the above

---

**Q5.** The time complexity of DELETING the maximum element from a Max-Heap is:
- (A) O(1)
- (B) O(log N)
- (C) O(N)
- (D) More than one of the above
- (E) None of the above

---

**Q6.** Heap Sort has which of the following properties?
- (A) Time complexity: O(N log N)
- (B) It is an in-place sorting algorithm
- (C) It is NOT a stable sort
- (D) More than one of the above
- (E) None of the above

---

**Q7.** Which algorithm uses a MIN-HEAP (Priority Queue) to find the shortest path?
- (A) Bubble Sort
- (B) Dijkstra's Algorithm
- (C) Merge Sort
- (D) More than one of the above
- (E) None of the above

---

**Q8.** In a Binary Heap stored as an array (0-indexed), if a node is at index i, its LEFT child is at index:
- (A) 2i
- (B) 2i + 1
- (C) 2i + 2
- (D) More than one of the above
- (E) None of the above

---

**Q9.** Which of the following is/are correct properties of a Binary Heap?
- (A) It is a Complete Binary Tree
- (B) In Max-Heap: every parent is greater than or equal to its children
- (C) In Min-Heap: every parent is less than or equal to its children
- (D) More than one of the above
- (E) None of the above

---

**Q10.** CPU Scheduling using ROUND ROBIN algorithm employs which data structure?
- (A) Stack
- (B) Priority Queue
- (C) Circular Queue
- (D) More than one of the above
- (E) None of the above

---

**Q11.** In a Priority Queue, if two elements have the SAME PRIORITY, they are served in:
- (A) Reverse order of insertion
- (B) FIFO (First In, First Out) order
- (C) Random order
- (D) More than one of the above
- (E) None of the above

---

**Q12.** Huffman Coding for data compression uses:
- (A) Max-Heap (Priority Queue)
- (B) Min-Heap (Priority Queue)
- (C) Stack
- (D) More than one of the above
- (E) None of the above

---

**Q13.** The time complexity to BUILD a heap from N unsorted elements is:
- (A) O(N log N)
- (B) O(N²)
- (C) O(N)
- (D) More than one of the above
- (E) None of the above

---

**Q14.** A Priority Queue is DIFFERENT from a normal Queue because:
- (A) It serves elements based on priority, not arrival time
- (B) It can serve a later-arriving element before an earlier one
- (C) It is best implemented using Binary Heap
- (D) More than one of the above
- (E) None of the above

---

**Q15.** In OS terminology, which queue holds processes that are in MEMORY and waiting for CPU time?
- (A) Job Queue
- (B) Ready Queue
- (C) Device Queue
- (D) More than one of the above
- (E) None of the above

---

**Q16.** Which of the following CORRECTLY describes a Max-Heap?
- (A) Parent node is always GREATER than or equal to both children
- (B) The tree is a COMPLETE binary tree
- (C) The maximum element is always at root
- (D) More than one of the above
- (E) None of the above

---

**Q17.** Consider a Max-Heap: [50, 30, 40, 10, 20, 35, 38].
After inserting 45, the heap property must be maintained.
What operation is performed?
- (A) Heapify Down (Sift Down)
- (B) Heapify Up (Sift Up / Bubble Up)
- (C) Both Heapify Up and Heapify Down simultaneously
- (D) More than one of the above
- (E) None of the above

---

**Q18.** Prim's algorithm for Minimum Spanning Tree (MST) uses which data structure?
- (A) Stack
- (B) Circular Queue
- (C) Priority Queue (Min-Heap)
- (D) More than one of the above
- (E) None of the above

---

**Q19.** In a Binary Heap stored as array (0-indexed), the PARENT of node at index i is at index:
- (A) i / 2
- (B) (i - 1) / 2
- (C) i - 1
- (D) More than one of the above
- (E) None of the above

---

**Q20.** Which of the following statements about Heap Sort is/are CORRECT?
- (A) Heap Sort uses a heap data structure
- (B) Its time complexity is O(N log N) in all cases (best, worst, average)
- (C) It requires O(1) additional space (in-place)
- (D) More than one of the above
- (E) None of the above

---

**Q21.** Which of the following is NOT an application of Priority Queue?
- (A) Dijkstra's Shortest Path Algorithm
- (B) Balancing of parentheses/symbols in an expression
- (C) Huffman Encoding
- (D) More than one of the above
- (E) None of the above

---

**Q22.** The READY QUEUE in an Operating System holds:
- (A) All processes that have been submitted to the system
- (B) Processes that are loaded in memory, waiting for CPU
- (C) Processes waiting for I/O operations to complete
- (D) More than one of the above
- (E) None of the above

---

**Q23.** Which data structure best represents the hospital emergency triage system where critical patients are treated first?
- (A) Normal Queue (FIFO)
- (B) Stack (LIFO)
- (C) Priority Queue
- (D) More than one of the above
- (E) None of the above

---

**Q24.** In a Binary Heap of N elements, what is the HEIGHT of the tree?
- (A) N
- (B) N/2
- (C) ⌊log₂N⌋
- (D) More than one of the above
- (E) None of the above

---

**Q25.** Which of the following sorting algorithms uses a Heap data structure?
- (A) Merge Sort
- (B) Quick Sort
- (C) Heap Sort
- (D) More than one of the above
- (E) None of the above

---

## 🏛️ GS QUESTIONS (Q26–Q50): Indian Constitution Basics

---

**Q26.** The Indian Constitution was adopted on:
- (A) 26 January 1950
- (B) 15 August 1947
- (C) 26 November 1949
- (D) More than one of the above
- (E) None of the above

---

**Q27.** Who was the Chairman of the Drafting Committee of the Indian Constitution?
- (A) Dr. Rajendra Prasad
- (B) Jawaharlal Nehru
- (C) Dr. B.R. Ambedkar
- (D) More than one of the above
- (E) None of the above

---

**Q28.** The words "SOCIALIST" and "SECULAR" were added to the Preamble by which Amendment?
- (A) 44th Amendment
- (B) 42nd Amendment
- (C) 86th Amendment
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Which of the following features of the Indian Constitution were borrowed from the UNITED KINGDOM?
- (A) Parliamentary form of government
- (B) Rule of Law
- (C) Cabinet system and Prime Minister's role
- (D) More than one of the above
- (E) None of the above

---

**Q30.** FUNDAMENTAL RIGHTS in the Indian Constitution were primarily inspired by the constitution of:
- (A) Ireland
- (B) Canada
- (C) USA
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Directive Principles of State Policy (DPSP) were borrowed from:
- (A) Australia
- (B) Ireland
- (C) South Africa
- (D) More than one of the above
- (E) None of the above

---

**Q32.** Which Article is described by Dr. B.R. Ambedkar as the "Heart and Soul of the Constitution"?
- (A) Article 14
- (B) Article 21
- (C) Article 32
- (D) More than one of the above
- (E) None of the above

---

**Q33.** Which of the following statements about Fundamental Rights and Directive Principles is CORRECT?
- (A) FRs are justiciable; DPSPs are non-justiciable
- (B) DPSPs direct government policy; FRs protect individual rights
- (C) FRs are borrowed from USA; DPSPs from Ireland
- (D) More than one of the above
- (E) None of the above

---

**Q34.** The writ of HABEAS CORPUS is used:
- (A) To challenge a person's claim to a public office
- (B) Against illegal detention to produce the person before court
- (C) To command a public authority to perform its duty
- (D) More than one of the above
- (E) None of the above

---

**Q35.** The voting age in India was reduced from 21 to 18 years by which Constitutional Amendment?
- (A) 42nd Amendment
- (B) 52nd Amendment
- (C) 61st Amendment
- (D) More than one of the above
- (E) None of the above

---

**Q36.** Under Article 21 of the Indian Constitution, which right is protected?
- (A) Right to Equality
- (B) Right to Life and Personal Liberty
- (C) Right to Freedom of Religion
- (D) More than one of the above
- (E) None of the above

---

**Q37.** Panchayati Raj (73rd Amendment, 1992) established which system?
- (A) Two-tier system of local governance
- (B) Three-tier system (village, block/intermediate, district)
- (C) Single-level village panchayat system
- (D) More than one of the above
- (E) None of the above

---

**Q38.** The "SATYAMEVA JAYATE" inscribed below the National Emblem is taken from:
- (A) Rigveda
- (B) Atharvaveda
- (C) Mundaka Upanishad
- (D) More than one of the above
- (E) None of the above

---

**Q39.** The Right to Property was removed from Fundamental Rights by:
- (A) 42nd Amendment (1976)
- (B) 44th Amendment (1978)
- (C) 86th Amendment (2002)
- (D) More than one of the above
- (E) None of the above

---

**Q40.** Which Schedule of the Indian Constitution deals with Panchayati Raj institutions (subjects/powers)?
- (A) 8th Schedule
- (B) 10th Schedule
- (C) 11th Schedule
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Article 21A (Free Education for children aged 6-14 years) was added by:
- (A) 73rd Amendment
- (B) 86th Amendment
- (C) 91st Amendment
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Which of the following is the NATIONAL ANIMAL of India?
- (A) Indian Elephant
- (B) Bengal Tiger
- (C) Indian Lion
- (D) More than one of the above
- (E) None of the above

---

**Q43.** The Indian Constitution is considered the LARGEST written constitution in the world. Which of the following contributed to its length?
- (A) It covers both Union and State administration in detail
- (B) It incorporates many provisions of Government of India Act, 1935
- (C) It deals with both federal and unitary aspects extensively
- (D) More than one of the above
- (E) None of the above

---

**Q44.** Which writ is issued to a lower court or authority to STOP proceedings that are BEYOND its jurisdiction?
- (A) Mandamus
- (B) Certiorari
- (C) Prohibition
- (D) More than one of the above
- (E) None of the above

---

**Q45.** The CONCURRENT LIST in the Indian Constitution was borrowed from:
- (A) USA
- (B) UK
- (C) Australia
- (D) More than one of the above
- (E) None of the above

---

**Q46.** Which of the following is/are correct about the Indian Preamble?
- (A) The Preamble is part of the Constitution (Kesavananda Bharati case)
- (B) Preamble can be amended by Parliament
- (C) "Integrity" was added to Preamble by 42nd Amendment
- (D) More than one of the above
- (E) None of the above

---

**Q47.** Fundamental Duties in Article 51A were added by which amendment and in which year?
- (A) 44th Amendment, 1978
- (B) 42nd Amendment, 1976
- (C) 86th Amendment, 2002
- (D) More than one of the above
- (E) None of the above

---

**Q48.** The National Anthem "Jana Gana Mana" was composed by:
- (A) Bankim Chandra Chattopadhyay
- (B) Subramania Bharati
- (C) Rabindranath Tagore
- (D) More than one of the above
- (E) None of the above

---

**Q49.** Which of the following are EMERGENCY PROVISIONS in the Indian Constitution?
- (A) Article 352 — National Emergency
- (B) Article 356 — President's Rule in State
- (C) Article 360 — Financial Emergency
- (D) More than one of the above
- (E) None of the above

---

**Q50.** Which of the following statements about the Indian Constitution is/are CORRECT?
- (A) India is described as "Union of States" in Article 1 (not "Federation")
- (B) Strong Centre with residuary powers borrowed from Canada
- (C) India has a quasi-federal structure (federal with unitary bias)
- (D) More than one of the above
- (E) None of the above

---
---

# ══════════════════════════════════════════════════
# ✅ ANSWER KEY WITH EXPLANATIONS — DAY 20
# ══════════════════════════════════════════════════

> 🔴 **CHECK ONLY AFTER ATTEMPTING ALL 50 QUESTIONS!**
> Your integrity = your topper journey.

---

## 🖥️ CS ANSWERS (Q1–Q25)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q1 | **(C)** | Binary Heap is the BEST — O(log N) for both insert and delete. Array and LL are O(N) for one of the operations. |
| Q2 | **(C)** | Max-Heap → Root = MAXIMUM element always. Heap property ensures this. |
| Q3 | **(B)** | Min-Heap → Root = MINIMUM element always. Parent ≤ children in Min-Heap. |
| Q4 | **(C)** | Insert in Binary Heap = O(log N) — heapify up traverses height = log N levels. |
| Q5 | **(B)** | Delete max from Max-Heap = O(log N) — heapify down traverses height = log N. |
| Q6 | **(D)** | ALL THREE (A, B, C) are correct about Heap Sort. D = More than one. |
| Q7 | **(B)** | Dijkstra's uses Min-Heap (Priority Queue). NOT Bubble Sort or Merge Sort. |
| Q8 | **(B)** | 0-indexed: Left child of i = 2i + 1. Right child = 2i + 2. |
| Q9 | **(D)** | All three properties (A, B, C) are correct for Binary Heap. D = More than one. |
| Q10 | **(C)** | Round Robin uses CIRCULAR QUEUE (equal time slices in circular fashion). |
| Q11 | **(B)** | Same priority → FIFO order (First In, First Out). This is the tie-breaking rule. |
| Q12 | **(B)** | Huffman Coding uses MIN-HEAP — always merges two LOWEST frequency nodes first. |
| Q13 | **(C)** | Building heap from N elements = O(N). This is a mathematical result (not O(N log N)). |
| Q14 | **(D)** | All three statements (A, B, C) are correct about Priority Queue. D = More than one. |
| Q15 | **(B)** | READY QUEUE = processes in memory waiting for CPU. (Job Queue = not yet loaded.) |
| Q16 | **(D)** | All three (A, B, C) correctly describe Max-Heap. D = More than one. |
| Q17 | **(B)** | INSERT → Heapify UP (Sift Up / Bubble Up). Element added at bottom and bubbled up. |
| Q18 | **(C)** | Prim's MST Algorithm uses Priority Queue (Min-Heap) to always pick minimum weight edge. |
| Q19 | **(B)** | 0-indexed: Parent of node at i = (i-1)/2 using integer division. |
| Q20 | **(D)** | All three statements (A, B, C) about Heap Sort are correct. D = More than one. |
| Q21 | **(B)** | Balancing parentheses/symbols uses STACK, NOT Priority Queue. (A) and (C) do use PQ. |
| Q22 | **(B)** | Ready Queue = processes in MEMORY waiting for CPU time. |
| Q23 | **(C)** | Hospital triage = Priority Queue. Critical patient (highest priority) served first. |
| Q24 | **(C)** | Height of Binary Heap with N elements = ⌊log₂N⌋ (floor of log base 2 of N). |
| Q25 | **(C)** | Heap Sort uses Heap. Merge Sort uses divide-and-conquer. Quick Sort uses partitioning. |

---

## 🏛️ GS ANSWERS (Q26–Q50)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q26 | **(C)** | Constitution ADOPTED: 26 November 1949. Came into FORCE: 26 January 1950. The question asks when adopted = Nov 26. |
| Q27 | **(C)** | Dr. B.R. Ambedkar = Chairman of Drafting Committee = "Father of Indian Constitution." Rajendra Prasad = President of CA. |
| Q28 | **(B)** | 42nd Amendment (1976) added "Socialist," "Secular," and "Integrity" to the Preamble. Called Mini Constitution. |
| Q29 | **(D)** | All three (A, B, C) were borrowed from UK. D = More than one. |
| Q30 | **(C)** | Fundamental Rights primarily from USA (Bill of Rights). NOT Ireland (that's DPSP). |
| Q31 | **(B)** | DPSP borrowed from IRELAND. Australia = Concurrent List. |
| Q32 | **(C)** | Article 32 = Right to Constitutional Remedies = "Heart and Soul" (Ambedkar). Article 21 = Life & Liberty. |
| Q33 | **(D)** | All three statements (A, B, C) are correct about FR vs DPSP. D = More than one. |
| Q34 | **(B)** | Habeas Corpus = against ILLEGAL DETENTION. "Produce the body (person) before court!" |
| Q35 | **(C)** | 61st Amendment (1989) reduced voting age from 21 → 18 years. |
| Q36 | **(B)** | Article 21 = Right to Life and Personal Liberty. Article 14 = Equality. Article 25 = Religion. |
| Q37 | **(B)** | 73rd Amendment established THREE-TIER Panchayati Raj: Village → Block → District. |
| Q38 | **(C)** | "Satyameva Jayate" is from MUNDAKA UPANISHAD (not Rigveda — common BPSC trap!). |
| Q39 | **(B)** | 44th Amendment (1978) removed Right to Property from Fundamental Rights. Now Art. 300A (legal right). |
| Q40 | **(C)** | 11th Schedule = Panchayati Raj (29 subjects). 12th Schedule = Urban Local Bodies. |
| Q41 | **(B)** | 86th Amendment (2002) added Art. 21A (Free Education 6-14 years) + 11th Fundamental Duty. |
| Q42 | **(B)** | Bengal TIGER is the National Animal. Indian Elephant = National Heritage Animal. |
| Q43 | **(D)** | All three statements (A, B, C) explain why Indian Constitution is the longest. D = More than one. |
| Q44 | **(C)** | PROHIBITION = issued to lower court/tribunal to STOP proceedings beyond jurisdiction. |
| Q45 | **(C)** | Concurrent List borrowed from AUSTRALIA. (USA has no Concurrent List concept.) |
| Q46 | **(D)** | All three statements (A, B, C) about the Preamble are correct. D = More than one. |
| Q47 | **(B)** | Fundamental Duties (Art. 51A) added by 42nd Amendment (1976) during Emergency period. |
| Q48 | **(C)** | Jana Gana Mana = Rabindranath Tagore. Vande Mataram = Bankim Chandra Chattopadhyay. |
| Q49 | **(D)** | All three (A: Art.352, B: Art.356, C: Art.360) are Emergency provisions. D = More than one. |
| Q50 | **(D)** | All three statements (A, B, C) about Indian Constitution are correct. D = More than one. |

---

## 📊 YOUR DAY 20 SCORE — TOPPER TRACKER:

```
┌────────────────────────────────────────────────────────────┐
│              DAY 20 PERFORMANCE CARD                       │
├──────────────────────┬─────────────────────────────────────┤
│ CS (Q1–Q25)          │ _____ / 25                          │
│ GS (Q26–Q50)         │ _____ / 25                          │
│ TOTAL                │ _____ / 50                          │
├──────────────────────┴─────────────────────────────────────┤
│ 47–50 → TOPPER Level 🏆 Exceptional! You're top 1%         │
│ 42–46 → Excellent ✅ Rank-worthy performance!              │
│ 35–41 → Good ✅ Work more on D/E option recognition        │
│ 28–34 → Average ⚠️ Re-read concepts; solve again tomorrow  │
│ Below 28 → Needs Fix ❌ Today's concepts need 2nd reading  │
├────────────────────────────────────────────────────────────┤
│ D/E OPTION CHECK:                                          │
│ Questions with D as answer: Q6,Q9,Q16,Q20,Q25 = CS        │
│                              Q29,Q33,Q43,Q46,Q49,Q50 = GS  │
│ If you missed 3+ D/E → spend 10 min identifying the TRAP  │
└────────────────────────────────────────────────────────────┘
```

---

## 🌙 NIGHT REVISION — WRITE THESE FROM MEMORY (5 CS + 5 GS):

```
CS (write without looking):
1. Priority Queue best implementation = ___________
2. Max-Heap: Root = _________ | Min-Heap: Root = _________
3. Insert in Binary Heap time = _____ | Delete = _____
4. Heap Sort time complexity = _____ | Space = _____
5. Dijkstra uses ________ | Huffman uses ________

GS (write without looking):
1. Constitution adopted: ________ | Enforced: ________
2. Chairman of Drafting Committee = ___________
3. 42nd Amendment added ________ and ________ to Preamble
4. Article 32 called "Heart and Soul" because _________
5. Habeas Corpus = ________ | Mandamus = ________
```

---

## ⚡ DAY 20 — TOPPER CHECKLIST

- [ ] Read Priority Queue concept and understood why Binary Heap is best
- [ ] Understood Max-Heap and Min-Heap with visual diagrams
- [ ] Understood Heap operations (Insert = Heapify Up, Delete = Heapify Down)
- [ ] Memorized applications: Dijkstra (Min-Heap), Huffman (Min-Heap), Heap Sort
- [ ] Understood Ready Queue, Job Queue in OS context
- [ ] Read Indian Constitution background (CA, dates, Ambedkar)
- [ ] Memorized sources of Constitution (UK/USA/Ireland/Canada/Australia)
- [ ] Studied Preamble keywords and 42nd Amendment additions
- [ ] Understood FR vs DPSP difference (Justiciable vs Non-justiciable)
- [ ] Memorized 5 Writs with memory trick "H M P C Q"
- [ ] Memorized important Constitutional Articles table
- [ ] Attempted all 50 questions before seeing answers
- [ ] Score: ______ / 50

---

> 🎯 **DAY 21 PREVIEW:** REVISION DAY — Arrays, Stack, Queue (Days 15–20) + 25 Mixed PYQ MCQs
> GS Revision: India Geography (all districts, rivers, climate)
> **Come back tomorrow: "Day-21"** 🔁

---
*Day 20 | BPSC TRE 4.0 Topper Study Plan | Phase 1 — Week 3*
*CS: Priority Queue, Binary Heap & Queue Applications | GS: Indian Constitution Basics*
*Prepared for: TOPPER RANK | Bihar Public Service Commission Teacher Recruitment Exam 4.0*
