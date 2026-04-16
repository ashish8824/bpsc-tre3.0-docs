# 📅 BPSC TRE 4.0 — DAY 20 COMPLETE STUDY MODULE
### Priority Queue & Queue Applications + Indian Polity — Constitution Basics
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Priority Queue, Binary Heap, Operations, OS Queue Concepts, Applications
> - Afternoon (1 hr): Indian Polity — Constitution Basics
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Priority Queue & Queue Applications — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Priority Queue?

### Real-Life Analogy — Hospital Emergency:
```
NORMAL QUEUE (FIFO):
  Patient 1 (minor cold)    → arrived first → served first
  Patient 2 (broken arm)    → arrived second → served second
  Patient 3 (heart attack!) → arrived third → served THIRD??

  This is WRONG for emergencies! We need priority-based service.

PRIORITY QUEUE:
  Patient 3 (heart attack!) → HIGHEST priority → served FIRST
  Patient 2 (broken arm)    → MEDIUM priority → served SECOND
  Patient 1 (minor cold)    → LOWEST priority → served LAST

  Regardless of arrival order — PRIORITY determines service order!
```

### Other Real-Life Priority Queue Examples:
```
1. Airport boarding: First class → Business → Economy (despite arrival order)
2. Operating System: High-priority process gets CPU first
3. Emergency services: Critical calls handled before routine ones
4. Traffic management: Ambulances override normal signal cycles
5. Print queue: "Urgent" print jobs jump ahead of normal jobs
```

### Formal Definition:
A **Priority Queue** is an abstract data type where each element has a **priority value** associated with it, and elements are served based on their priority — **not their insertion order**. Element with the **highest priority** is dequeued first.

---

## 🔷 SECTION 2: Normal Queue vs Priority Queue

```
Feature              Normal Queue         Priority Queue
──────────────────────────────────────────────────────────
Order principle      FIFO                 Priority-based
Insertion            At rear              Based on priority
Deletion             From front (FIFO)    Highest priority first
Use case             Waiting lines        Scheduling, algorithms
Data structure       Array/Linked List    Heap (most efficient)
Access pattern       Ordered by time      Ordered by priority
```

### 🚨 PYQ TRAP #1: Priority Queue is NOT FIFO
> A Priority Queue does NOT follow FIFO. Two elements with the SAME priority may be served in FIFO order (tie-breaking), but generally, the data structure guarantees that the **highest (or lowest) priority element is always at the front**.

---

## 🔷 SECTION 3: Types of Priority Queue

### Type 1: Min-Priority Queue (Min-Heap based)
```
MINIMUM element has HIGHEST priority
→ Smallest value = served first

Example: Elements {5, 2, 8, 1, 9}
  Min-PQ dequeue order: 1 → 2 → 5 → 8 → 9
  (smallest first)

Use cases: Dijkstra's shortest path, Prim's MST,
           Task scheduling with shortest time first
```

### Type 2: Max-Priority Queue (Max-Heap based)
```
MAXIMUM element has HIGHEST priority
→ Largest value = served first

Example: Elements {5, 2, 8, 1, 9}
  Max-PQ dequeue order: 9 → 8 → 5 → 2 → 1
  (largest first)

Use cases: CPU scheduling (highest priority process first),
           Huffman coding, emergency room (most critical first)
```

---

## 🔷 SECTION 4: Binary Heap — The Best Implementation

### Why Use a Heap?
```
Priority Queue can be implemented using:
  1. Unsorted Array:  Insert O(1), Delete O(n) — slow delete
  2. Sorted Array:    Insert O(n), Delete O(1) — slow insert
  3. Linked List:     Insert O(n), Delete O(1) — slow insert
  4. Binary HEAP:     Insert O(log n), Delete O(log n) — EFFICIENT!

Binary Heap is the standard and most efficient implementation.
```

### What is a Binary Heap?
```
A Binary Heap is a COMPLETE BINARY TREE that satisfies the HEAP PROPERTY.

TWO KEY PROPERTIES:
1. SHAPE PROPERTY: Must be a COMPLETE binary tree
   → All levels filled EXCEPT possibly the last
   → Last level filled from LEFT to RIGHT (no gaps)

2. HEAP PROPERTY:
   Min-Heap: Parent ≤ ALL its children (root = minimum)
   Max-Heap: Parent ≥ ALL its children (root = maximum)
```

### Complete Binary Tree — What It Means:
```
COMPLETE binary tree (valid for heap):
          10
         /  \
       15    20
      / \   /
    25  35 30
    ← last level filled LEFT to RIGHT, no gaps ✅

NOT complete (invalid for heap):
          10
         /  \
       15    20
      /     /
    25     30
    ← gap at index [3] (15's right child missing) ❌
```

---

## 🔷 SECTION 5: Min-Heap and Max-Heap Diagrams

### Min-Heap Structure:
```
In a MIN-HEAP: Every parent ≤ its children
Root = MINIMUM element

Example: Min-Heap with elements 1, 3, 5, 7, 9, 4, 2:

                  1          ← ROOT (minimum element)
                /   \
              3       2
            /   \   /   \
           7     9 4     5

Heap property check:
  1 ≤ 3 ✅   1 ≤ 2 ✅
  3 ≤ 7 ✅   3 ≤ 9 ✅
  2 ≤ 4 ✅   2 ≤ 5 ✅
All parents ≤ children → Valid Min-Heap!

Array representation (level-order): [1, 3, 2, 7, 9, 4, 5]
Index:                                0  1  2  3  4  5  6
```

### Max-Heap Structure:
```
In a MAX-HEAP: Every parent ≥ its children
Root = MAXIMUM element

Example: Max-Heap with elements 9, 7, 5, 3, 1, 4, 8:

                  9          ← ROOT (maximum element)
                /   \
              7       8
            /   \   /   \
           3     1 4     5

Heap property check:
  9 ≥ 7 ✅   9 ≥ 8 ✅
  7 ≥ 3 ✅   7 ≥ 1 ✅
  8 ≥ 4 ✅   8 ≥ 5 ✅
All parents ≥ children → Valid Max-Heap!

Array representation (level-order): [9, 7, 8, 3, 1, 4, 5]
Index:                                0  1  2  3  4  5  6
```

---

## 🔷 SECTION 6: Heap Array Representation & Index Formulas

### Storing Heap in an Array (0-indexed):
```
For a node at index i:
  Left child  = index (2i + 1)
  Right child = index (2i + 2)
  Parent      = index (i - 1) / 2   (integer division)

Example: Array [10, 20, 15, 40, 30, 50, 25]
  Index:         0    1   2   3   4   5   6

  Node at index 1 (value 20):
    Left child  = 2*1+1 = 3 → value 40
    Right child = 2*1+2 = 4 → value 30
    Parent      = (1-1)/2 = 0 → value 10

  Node at index 2 (value 15):
    Left child  = 2*2+1 = 5 → value 50
    Right child = 2*2+2 = 6 → value 25
    Parent      = (2-1)/2 = 0 → value 10
```

### 🚨 PYQ TRAP #2: Index Formulas (0-indexed)
```
LEFT CHILD of node at i  = 2i + 1
RIGHT CHILD of node at i = 2i + 2
PARENT of node at i      = (i-1)/2   [integer division]

Some books use 1-indexed (root at index 1):
LEFT CHILD = 2i
RIGHT CHILD = 2i + 1
PARENT = i/2
```

---

## 🔷 SECTION 7: Heap Operations

### Operation 1: INSERT (Enqueue in Priority Queue)

```
Algorithm: HEAP INSERT (for Min-Heap)
Step 1: Add new element at the END of the array (last position)
Step 2: "Heapify Up" (also called "Bubble Up" or "Sift Up"):
        Compare new element with its PARENT
        If new element < parent (for min-heap): SWAP
        Repeat until heap property is restored or root is reached
Time Complexity: O(log n)  ← because tree height = log n
```

### INSERT Dry Run (Min-Heap): Insert 2 into existing heap

```
Before insert: Min-Heap = [4, 7, 6, 10, 9]
                    4
                  /   \
                7       6
              /   \
            10     9

Step 1: Add 2 at end (index 5):
  [4, 7, 6, 10, 9, 2]
                    4
                  /   \
                7       6
              /   \   /
            10     9 2    ← 2 added here (index 5)

Step 2: Heapify Up:
  Index 5 (value 2), Parent = index (5-1)/2 = 2 (value 6)
  2 < 6 → SWAP indices 5 and 2:
  [4, 7, 2, 10, 9, 6]
                    4
                  /   \
                7       2      ← 2 moved up
              /   \   /
            10     9 6

  Now index 2 (value 2), Parent = index (2-1)/2 = 0 (value 4)
  2 < 4 → SWAP indices 2 and 0:
  [2, 7, 4, 10, 9, 6]
                    2          ← 2 is now ROOT
                  /   \
                7       4
              /   \   /
            10     9 6

  Now at root → STOP. Heap property restored. ✅
Final Min-Heap: [2, 7, 4, 10, 9, 6]
```

---

### Operation 2: DELETE (Dequeue — always removes root)

```
Algorithm: HEAP DELETE (always removes ROOT = min in Min-Heap)
Step 1: Store root value (this is the answer)
Step 2: Move LAST element to ROOT position
Step 3: Remove last element (reduce heap size by 1)
Step 4: "Heapify Down" (also called "Sift Down" or "Bubble Down"):
        Compare root with its CHILDREN
        Swap with the SMALLER child (for min-heap)
        Repeat until heap property restored or leaf reached
Time Complexity: O(log n)
```

### DELETE Dry Run (Min-Heap): Delete minimum from [2, 7, 4, 10, 9, 6]

```
Before: Min-Heap [2, 7, 4, 10, 9, 6]
                    2         ← ROOT to delete
                  /   \
                7       4
              /   \   /
            10     9 6

Step 1: Store answer = 2 (root = minimum)
Step 2: Move last element (6) to root:
  [6, 7, 4, 10, 9]
                    6         ← 6 placed at root
                  /   \
                7       4
              /   \
            10     9

Step 3: Heapify Down from root:
  Root (index 0, value 6):
    Left child = index 1 (value 7)
    Right child = index 2 (value 4)
    Smallest child = index 2 (value 4)
    6 > 4 → SWAP root and index 2:
  [4, 7, 6, 10, 9]
                    4         ← heap property improving
                  /   \
                7       6
              /   \
            10     9

  Now at index 2 (value 6):
    Left child = index 5 → doesn't exist
    Right child = index 6 → doesn't exist
    LEAF NODE → STOP

Final Min-Heap: [4, 7, 6, 10, 9]   RETURNED: 2 ✅
```

---

### Operation 3: PEEK (Get highest priority without removal)
```
PEEK: Simply return arr[0] (root)
Time Complexity: O(1)  ← always the root

For Min-Heap: arr[0] = minimum element
For Max-Heap: arr[0] = maximum element
```

---

## 🔷 SECTION 8: Time Complexity Summary

```
Operation          Binary Heap     Sorted Array    Unsorted Array
──────────────────────────────────────────────────────────────────
Insert             O(log n)        O(n)            O(1)
Delete (max/min)   O(log n)        O(1)            O(n)
Peek (max/min)     O(1)            O(1)            O(n)
Search             O(n)            O(log n)        O(n)
Build heap from n  O(n)            —               —
  elements

Heap is the BEST balanced choice: O(log n) for both insert and delete
```

### 🚨 PYQ TRAP #3: Build Heap Complexity
> Building a heap from n elements using repeated insertion = O(n log n)
> But using the **Floyd's Build-Heap algorithm** = **O(n)** — more efficient!
> Both answers may appear in questions — Floyd's method = O(n).

---

## 🔷 SECTION 9: Applications of Priority Queue

### 1. Dijkstra's Shortest Path Algorithm
```
Problem: Find shortest path from source to all other nodes in a graph

How Priority Queue is used:
  → Maintain a Min-Priority Queue of (distance, node) pairs
  → Always process the node with MINIMUM distance first (greedy choice)
  → Guarantees optimal shortest path

Time complexity with Min-Heap: O((V + E) log V)
Without heap (simple array): O(V²)
```

### 2. Huffman Coding (Data Compression)
```
Problem: Compress data by assigning shorter codes to frequent characters

How Priority Queue is used:
  → Build a Min-Priority Queue of character frequencies
  → Repeatedly extract TWO minimum-frequency elements
  → Combine them into a new node (sum frequency)
  → Insert combined node back
  → Builds Huffman tree bottom-up

Result: Variable-length prefix-free code (characters with higher
        frequency get shorter binary codes)
Example: In "AAAAABBBCC", 'A' gets shortest code
```

### 3. CPU Scheduling (Preemptive Priority Scheduling)
```
OS maintains processes in a Max-Priority Queue:
  → Process with HIGHEST priority gets CPU next
  → If a higher-priority process arrives, it PREEMPTS the current one
  → Lower-priority processes wait in the queue

Example:
  P1: priority 3 (running)
  P2: priority 7 arrives → P2 PREEMPTS P1 → CPU goes to P2
  P1 waits in the queue
```

### 4. Prim's Minimum Spanning Tree Algorithm
```
Finds minimum spanning tree of a weighted graph:
  → Uses Min-Priority Queue to always pick the minimum weight edge
  → Greedy approach similar to Dijkstra's
```

### 5. Event-Driven Simulation
```
Simulate real-world events ordered by time:
  → Events stored in Min-PQ by timestamp
  → Always process the EARLIEST event next
  → Used in network simulation, games, OS simulation
```

---

## 🔷 SECTION 10: Queue in Operating System

### Types of Queues in OS:

```
OS maintains multiple queues to manage processes:

1. JOB QUEUE (Long-term Queue):
   → All processes in the system (submitted but not yet loaded)
   → Long-term scheduler selects processes from here
   → Decides which jobs get into MAIN MEMORY
   → Controls DEGREE OF MULTIPROGRAMMING

2. READY QUEUE:
   → Processes that are in MAIN MEMORY and ready to execute
   → Waiting for CPU time
   → Short-term scheduler (CPU scheduler) picks from here
   → Usually a Priority Queue or FIFO queue
   → Maintained as linked list typically

3. DEVICE QUEUE (I/O Queue):
   → Processes waiting for a specific I/O device
   → Each device has its OWN device queue
   → When I/O completes → process moves to Ready Queue

FLOW: New Process → Job Queue → Ready Queue → CPU
                                          ↕ (I/O request)
                                    Device Queue
                                          ↓
                                   (I/O complete)
                                          ↓
                                    Ready Queue
```

### 🚨 PYQ TRAP #4: Ready Queue is NOT always FIFO
> The Ready Queue holds processes ready for CPU. It can be implemented as:
> - FIFO queue (for FCFS scheduling)
> - Priority Queue (for Priority scheduling)
> - Multiple queues (for Multilevel Queue scheduling)
> The term "Ready Queue" refers to the data structure, not necessarily a FIFO structure.

---

## 📊 VISUAL SUMMARY — Priority Queue & Heap

```
PRIORITY QUEUE
      │
      ├── Min-Priority Queue → Min-Heap → Root = MINIMUM
      │                       Insert: O(log n) [heapify up]
      │                       Delete: O(log n) [heapify down]
      │                       Peek:   O(1)     [return root]
      │
      └── Max-Priority Queue → Max-Heap → Root = MAXIMUM

HEAP PROPERTIES:
  Shape: Complete Binary Tree (last level left-to-right)
  Min-Heap: Parent ≤ Children (everywhere)
  Max-Heap: Parent ≥ Children (everywhere)

INDEX FORMULAS (0-indexed array):
  Left child:  2i + 1
  Right child: 2i + 2
  Parent:      (i-1)/2

APPLICATIONS:
  Dijkstra's Algorithm → Min-Heap
  Huffman Coding → Min-Heap
  CPU Scheduling → Max-Heap (highest priority first)
  Prim's MST → Min-Heap
  OS Ready Queue → Priority Queue

NON-APPLICATIONS of Priority Queue:
  Balancing symbols → Stack
  Expression conversion → Stack
  BFS → Simple Queue (not priority)
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Indian Polity — Constitution Basics

---

## 🔷 WHY THIS MATTERS FOR BPSC TRE:
- Indian Constitution basics appear in EVERY GS section
- Fundamental Rights, Directive Principles, and key features = very high frequency
- Bihar-related constitutional facts have extra BPSC probability

---

## 🔷 WHAT IS A CONSTITUTION?

```
A Constitution is the SUPREME LAW of a country.
It defines:
  → The structure of the government (Parliament, Executive, Judiciary)
  → Fundamental rights of citizens
  → Duties and limitations of the government
  → Relationship between the Union and States
  → How laws are made and amended

India's Constitution: WRITTEN, SUPREME, and ENFORCEABLE by courts
```

---

## 🔷 IMPORTANT FACTS — INDIAN CONSTITUTION

```
Constituent Assembly:
  → Set up under the Cabinet Mission Plan of 1946
  → First meeting: December 9, 1946
  → Dr. Rajendra Prasad (Bihar!) elected President of Constituent Assembly
  → Dr. B.R. Ambedkar: Chairman of Drafting Committee
  → Total members: 299 (at time of signing)
  → Took: 2 years, 11 months, 18 days to draft

Adoption & Enforcement:
  → Adopted: November 26, 1949 ("Constitution Day" / "Samvidhan Diwas")
  → Came into force: January 26, 1950 ("Republic Day")
  → Why Jan 26? → January 26, 1930 = Poorna Swaraj (Complete Independence) Declaration day

Original Constitution:
  → 395 Articles, 8 Schedules, 22 Parts
  → Currently (after amendments): ~470+ Articles, 12 Schedules, 25 Parts
  → Preamble: "Soul of the Constitution" (as described by some scholars)
```

### 🚨 PYQ TRAP: Constitution Day vs Republic Day
> **November 26** = Constitution Day (Samvidhan Diwas) — day it was ADOPTED (1949)
> **January 26** = Republic Day — day it came into FORCE (1950)
> Dr. Rajendra Prasad (from **Siwan, Bihar**) = President of Constituent Assembly AND first President of India

---

## 🔷 KEY FEATURES OF INDIAN CONSTITUTION

### 1. Longest Written Constitution:
```
India's Constitution is the LONGEST WRITTEN CONSTITUTION in the world.
(USA has the shortest written constitution — 7 original articles)
Why so long?
  → Borrowed from many countries
  → Single constitution for both Union and States
  → Detailed provisions for governance
  → Separate provisions for Union Territories, Scheduled Areas, etc.
```

### 2. Blend of Rigidity and Flexibility:
```
Some provisions can be amended by SIMPLE MAJORITY (flexible):
  → Creation of new states, changing state names
Some by SPECIAL MAJORITY (rigid):
  → 2/3 of members present + more than 50% of total membership
Some by SPECIAL MAJORITY + RATIFICATION by half the states:
  → Federal provisions (like election of President, Supreme Court)
```

### 3. Federal with Unitary Features:
```
India = "QUASI-FEDERAL" (federal in normal times, unitary in emergencies)

Federal features:
  → Two governments (Union + States)
  → Division of powers (Union List, State List, Concurrent List)
  → Independent judiciary
  → Written constitution

Unitary features:
  → Single citizenship
  → All-India Services (IAS, IPS)
  → Emergency powers (Centre can take over state)
  → Governor appointed by President (not elected)
```

### 4. Parliamentary Form of Government:
```
India follows WESTMINSTER model (like UK):
  → Executive (PM + Cabinet) is responsible to the Legislature
  → President = nominal/constitutional head
  → Prime Minister = real/effective head
  → Can be removed by vote of no confidence
```

### 5. Fundamental Rights (Part III, Articles 12–35):
```
SIX Fundamental Rights:
  1. Right to Equality (Articles 14-18)
  2. Right to Freedom (Articles 19-22)
  3. Right against Exploitation (Articles 23-24)
  4. Right to Freedom of Religion (Articles 25-28)
  5. Cultural and Educational Rights (Articles 29-30)
  6. Right to Constitutional Remedies (Article 32)
  
  NOTE: Originally 7 Fundamental Rights; Right to Property (Article 31)
  was removed by 44th Amendment Act, 1978 → now a legal right (Article 300A)
```

### 🚨 PYQ TRAP: Number of Fundamental Rights
> Original constitution had **7 Fundamental Rights**.
> After the **44th Amendment (1978)**, Right to Property was removed.
> Now there are **6 Fundamental Rights**.
> Right to Education (Article 21A) was added by 86th Amendment (2002) — within Right to Freedom category.

### 6. Directive Principles of State Policy (Part IV, Articles 36–51):
```
DPSP = Guidelines for the government to make laws and policies
→ NOT ENFORCEABLE by courts (unlike Fundamental Rights)
→ Positive obligations on the State
→ Inspired by Irish Constitution (Ireland)
→ Goal: Establish a "Welfare State"

Examples of DPSP:
  → Equal pay for equal work (Article 39d)
  → Free legal aid (Article 39A)
  → Uniform Civil Code (Article 44)
  → Panchayati Raj (Article 40)
  → Protection of environment (Article 48A)

DPSP vs Fundamental Rights:
  FRs = Negative obligations (government should NOT do)
  DPSP = Positive obligations (government SHOULD do)
  FRs = Justiciable (can go to court if violated)
  DPSP = Non-justiciable (cannot sue government directly)
```

### 7. Fundamental Duties (Part IVA, Article 51A):
```
Added by 42nd Amendment Act, 1976 (during Emergency)
Originally 10 duties; 11th added by 86th Amendment (2002)

Examples:
  → To abide by the Constitution and respect national flag/anthem
  → To defend the country
  → To protect natural environment
  → To develop scientific temper
  → To provide education to children (6-14 years) ← 86th Amendment

NOT ENFORCEABLE — but courts use them in interpretation
```

---

## 🔷 SOURCES OF INDIAN CONSTITUTION

```
COUNTRY              PROVISIONS BORROWED
──────────────────────────────────────────────────────────────────
United Kingdom (UK)  Parliamentary govt, Rule of Law, Single citizenship,
                     Cabinet system, Writs, Bicameralism
USA                  Fundamental Rights, Independent Judiciary, Judicial
                     Review, Preamble, Impeachment, VP role
Ireland              Directive Principles of State Policy (DPSP),
                     Method of Presidential election, Nomination of
                     members to Rajya Sabha
Canada               Federal with strong Centre, Residuary powers with Centre,
                     Advisory jurisdiction of Supreme Court
Australia            Concurrent List, Freedom of trade, Joint sitting of
                     Parliament
Germany (Weimar)     Suspension of Fundamental Rights during emergency
South Africa         Amendment procedure (special majority), Election of
                     Rajya Sabha members
Japan                Procedure established by law (Article 21)
France               Republic, Liberty, Equality, Fraternity (Preamble ideals)
Soviet Union (USSR)  Fundamental Duties, Five Year Plans (economic planning)
```

### Memory Trick — Sources:
```
"Uncle Sam (US) gave us Rights and Review
UK gave us Parliament and Rule
Ireland (Ire) gave us DPSP
Canada gave us Centre's power
Australia gave us Concurrent List"
```

---

## 🔷 PREAMBLE OF THE CONSTITUTION

```
"WE, THE PEOPLE OF INDIA, having solemnly resolved to constitute
India into a SOVEREIGN SOCIALIST SECULAR DEMOCRATIC REPUBLIC
and to secure to all its citizens:
JUSTICE, social, economic and political;
LIBERTY of thought, expression, belief, faith and worship;
EQUALITY of status and of opportunity;
and to promote among them all
FRATERNITY assuring the dignity of the individual
and the unity and integrity of the Nation;
IN OUR CONSTITUENT ASSEMBLY this twenty-sixth day of November, 1949,
do HEREBY ADOPT, ENACT AND GIVE TO OURSELVES THIS CONSTITUTION."
```

### Preamble Key Words — What They Mean:
```
SOVEREIGN     → India is free from foreign control; no external authority above it
SOCIALIST     → Added by 42nd Amendment (1976); state ownership + social equality
SECULAR       → Added by 42nd Amendment (1976); no official state religion
DEMOCRATIC    → Government elected by people; people are supreme
REPUBLIC      → Elected head of state (President, not hereditary king)

42nd Amendment 1976 (Indira Gandhi) added:
  → SOCIALIST + SECULAR to Preamble
  → FUNDAMENTAL DUTIES (Part IVA)
  → Changed "Nation" to "Sovereign Socialist Secular Democratic Republic"

NOTE: Berubari Union case (1960) → SC said Preamble is NOT part of Constitution
      Kesavananda Bharati case (1973) → SC reversed → Preamble IS part of Constitution
```

### 🚨 PYQ TRAP: 42nd Amendment
> The words **"Socialist"** and **"Secular"** were NOT in the original Preamble.
> They were added by the **42nd Constitutional Amendment Act, 1976** (during Emergency period under PM Indira Gandhi).

---

## 🔷 IMPORTANT SCHEDULES OF CONSTITUTION

```
SCHEDULE    CONTENT
──────────────────────────────────────────────────────────
1st         Names of States and Union Territories
2nd         Salary of President, Governors, Judges, etc.
3rd         Forms of Oaths and Affirmations
4th         Allocation of seats in Rajya Sabha
5th         Administration of Scheduled Areas and Tribes
6th         Tribal areas in Assam, Meghalaya, Tripura, Mizoram
7th         Union List, State List, Concurrent List (MOST IMPORTANT!)
8th         Languages (22 scheduled languages) ← EXAM IMPORTANT
9th         Laws protected from judicial review (added by 1st Amendment)
10th        Anti-defection law (added by 52nd Amendment 1985)
11th        Panchayati Raj (powers/functions — added by 73rd Amendment)
12th        Municipalities (powers — added by 74th Amendment)
```

### 🚨 PYQ TRAP: 7th Schedule
> The **7th Schedule** contains the three lists:
> - **Union List (List I)**: 97 subjects — only Parliament can make laws (Defence, Foreign, Currency)
> - **State List (List II)**: 66 subjects — only State Legislature (Police, Agriculture, Public Health)
> - **Concurrent List (List III)**: 52 subjects — BOTH Parliament and State can make laws (Education, Marriage, Forests)
> **Residuary powers** (not in any list) → go to **Union** (unlike USA where residuary goes to States)

### 🚨 PYQ TRAP: 8th Schedule Languages
> Originally 14 languages; now **22 scheduled languages** in the 8th Schedule.
> Recently added: Sindhi (1967), Konkani, Manipuri, Nepali (1992),
> Bodo, Dogri, Maithili, Santali (2004 — 92nd Amendment)
> **Maithili** (Bihar's second language) was added in 2004!

---

## 🔷 IMPORTANT ARTICLES — QUICK REFERENCE

```
Article 1    → India = "Union of States" (NOT federation of states)
Article 12   → Definition of "State" for Fundamental Rights
Article 13   → Laws inconsistent with FRs = void
Article 14   → Equality before Law + Equal Protection of Laws
Article 15   → Prohibition of discrimination (race, religion, sex, caste, place)
Article 16   → Equality of opportunity in public employment
Article 17   → Abolition of Untouchability
Article 18   → Abolition of Titles (except military/academic)
Article 19   → Six freedoms (speech, assembly, association, movement, residence, profession)
Article 21   → Right to Life and Personal Liberty (most expansive article!)
Article 21A  → Right to Education (6-14 years) — 86th Amendment 2002
Article 25   → Freedom of Religion
Article 32   → Right to Constitutional Remedies (Dr. Ambedkar: "Heart and Soul of Constitution")
Article 44   → Uniform Civil Code (DPSP)
Article 51A  → Fundamental Duties
Article 72   → President's pardoning power
Article 123  → Presidential ordinances
Article 124  → Establishment of Supreme Court
Article 226  → High Court's power to issue writs
Article 356  → President's Rule in States
Article 370  → (Formerly) Special status of J&K — now abrogated (2019)
```

### Memory Trick for Key Articles:
```
"14 = Equality (1+4=5 fingers = equal)"
"19 = 6 Freedoms (19 sounds like 'nice freedoms')"
"21 = Life (21st birthday = adult life begins)"
"32 = Dr. Ambedkar's favourite (Right to Constitutional Remedies)"
"44 = Uniform Civil Code (44 = uniform, same for all)"
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Priority Queue, Heap, Applications, OS Queues

---

**Q1.** In a Priority Queue, the element served first is:
(A) The element that was inserted first (FIFO)
(B) The element with the highest (or lowest) priority
(C) The element at the middle of the queue
(D) More than one of the above
(E) None of the above

---

**Q2.** In a Min-Heap, the ROOT always contains:
(A) The median element
(B) The maximum element
(C) The minimum element
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following is the MOST EFFICIENT implementation of a Priority Queue?
(A) Sorted array
(B) Unsorted linked list
(C) Binary Heap
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the time complexity of INSERT in a Binary Heap?
(A) O(1)
(B) O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q5.** What is the time complexity of DELETE (remove max/min) in a Binary Heap?
(A) O(1)
(B) O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the time complexity of PEEK (get max/min without removing) in a Binary Heap?
(A) O(log n)
(B) O(n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q7.** A Binary Heap must be a:
(A) Full binary tree
(B) Complete binary tree
(C) Perfect binary tree
(D) More than one of the above
(E) None of the above

---

**Q8.** In a Max-Heap, for every node i, which condition must hold?
(A) Value(i) ≤ Value(children)
(B) Value(i) ≥ Value(children)
(C) Value(i) = Value(children)
(D) More than one of the above
(E) None of the above

---

**Q9.** For a node at index i (0-indexed) in a heap array, the LEFT child is at index:
(A) 2i
(B) 2i + 1
(C) i + 1
(D) More than one of the above
(E) None of the above

---

**Q10.** For a node at index i (0-indexed) in a heap array, the PARENT is at index:
(A) i/2
(B) (i-1)/2
(C) i-1
(D) More than one of the above
(E) None of the above

---

**Q11.** Which algorithm uses a Min-Priority Queue to find shortest paths in a graph?
(A) Kruskal's Algorithm
(B) Dijkstra's Algorithm
(C) Floyd-Warshall Algorithm
(D) More than one of the above
(E) None of the above

---

**Q12.** Huffman Coding uses Priority Queue for:
(A) Sorting characters alphabetically
(B) Building a compression tree by repeatedly combining minimum-frequency elements
(C) Finding the longest string
(D) More than one of the above
(E) None of the above

---

**Q13.** The "Ready Queue" in an Operating System contains:
(A) All processes in the system (submitted but not yet started)
(B) Processes in main memory waiting for CPU
(C) Processes waiting for I/O to complete
(D) More than one of the above
(E) None of the above

---

**Q14.** The "Job Queue" in Operating System contains:
(A) Processes waiting for CPU only
(B) All processes that have been submitted but may not yet be in main memory
(C) Completed processes
(D) More than one of the above
(E) None of the above

---

**Q15.** After deleting the root from a heap, which element is placed at the root before heapify-down?
(A) The left child of the root
(B) The right child of the root
(C) The LAST element of the heap
(D) More than one of the above
(E) None of the above

---

**Q16.** Which process is called "Heapify Up" (or Bubble Up)?
(A) Restoring heap property after deletion
(B) Restoring heap property after insertion (new element percolates up)
(C) Sorting the heap
(D) More than one of the above
(E) None of the above

---

**Q17.** The time complexity of BUILDING a heap from n elements using Floyd's method is:
(A) O(n log n)
(B) O(n²)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following is NOT an application of Priority Queue?
(A) Dijkstra's shortest path
(B) Breadth-First Search (BFS)
(C) Huffman Coding
(D) More than one of the above
(E) None of the above

---

**Q19.** In Preemptive Priority Scheduling, when a new higher-priority process arrives:
(A) It waits for the current process to complete
(B) It PREEMPTS the current process and gets CPU
(C) It is placed in the device queue
(D) More than one of the above
(E) None of the above

---

**Q20.** Is a Max-Heap a sorted array?
(A) Yes, always sorted in descending order
(B) No — heap only guarantees parent ≥ children, NOT total ordering
(C) Yes, always sorted in ascending order
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following is a valid Max-Heap?
(A) [10, 20, 30, 40, 50]
(B) [50, 40, 30, 20, 10]
(C) [30, 20, 10, 15, 5]
(D) More than one of the above
(E) None of the above

---

**Q22.** The heap property guarantees that we can find the maximum (in Max-Heap) in:
(A) O(log n)
(B) O(n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q23.** When we delete from a Min-Heap, we always remove:
(A) The last element
(B) The root (minimum element)
(C) A random element
(D) More than one of the above
(E) None of the above

---

**Q24.** Device Queue in OS contains:
(A) Processes ready for CPU
(B) Processes waiting for a specific I/O device to become available
(C) All processes in the system
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following correctly describes a Min-Heap with values [1, 3, 2, 7, 9, 4, 5]?
(A) It is an invalid heap (3 > 2)
(B) It is a valid Min-Heap (every parent ≤ its children)
(C) It is a valid Max-Heap
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Indian Polity — Constitution Basics

---

**Q26.** The Indian Constitution was adopted by the Constituent Assembly on:
(A) January 26, 1950
(B) August 15, 1947
(C) November 26, 1949
(D) More than one of the above
(E) None of the above

---

**Q27.** The Indian Constitution came into FORCE on:
(A) November 26, 1949
(B) January 26, 1950
(C) August 15, 1947
(D) More than one of the above
(E) None of the above

---

**Q28.** Who was the Chairman of the Drafting Committee of the Indian Constitution?
(A) Dr. Rajendra Prasad
(B) Jawaharlal Nehru
(C) Dr. B.R. Ambedkar
(D) More than one of the above
(E) None of the above

---

**Q29.** Who presided over the Constituent Assembly as its President?
(A) Dr. B.R. Ambedkar
(B) Dr. Rajendra Prasad
(C) Sardar Vallabhbhai Patel
(D) More than one of the above
(E) None of the above

---

**Q30.** The Indian Constitution is described as the world's:
(A) Shortest written constitution
(B) Longest written constitution
(C) Oldest constitution
(D) More than one of the above
(E) None of the above

---

**Q31.** The words "Socialist" and "Secular" were added to the Preamble by which amendment?
(A) 44th Amendment, 1978
(B) 42nd Amendment, 1976
(C) 86th Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q32.** Currently, how many Fundamental Rights are guaranteed by the Indian Constitution?
(A) 7
(B) 5
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q33.** Which article of the Constitution was described by Dr. B.R. Ambedkar as the "Heart and Soul of the Constitution"?
(A) Article 14 (Equality)
(B) Article 21 (Right to Life)
(C) Article 32 (Right to Constitutional Remedies)
(D) More than one of the above
(E) None of the above

---

**Q34.** Directive Principles of State Policy (DPSP) are:
(A) Enforceable by courts — citizens can file a case if violated
(B) Non-justiciable guidelines for the government to establish a welfare state
(C) Part of Fundamental Rights
(D) More than one of the above
(E) None of the above

---

**Q35.** The Directive Principles of State Policy were borrowed from which country's constitution?
(A) USA
(B) UK
(C) Ireland
(D) More than one of the above
(E) None of the above

---

**Q36.** The 7th Schedule of the Indian Constitution contains:
(A) The list of Fundamental Rights
(B) The three legislative lists: Union, State, and Concurrent
(C) The names of scheduled languages
(D) More than one of the above
(E) None of the above

---

**Q37.** Which schedule of the Constitution contains the 22 recognized languages?
(A) 6th Schedule
(B) 7th Schedule
(C) 8th Schedule
(D) More than one of the above
(E) None of the above

---

**Q38.** Maithili (a language spoken in Bihar) was included in the 8th Schedule by which amendment?
(A) 71st Amendment
(B) 86th Amendment
(C) 92nd Amendment, 2003
(D) More than one of the above
(E) None of the above

---

**Q39.** Residuary powers (subjects not in any list) in India vest with:
(A) State legislatures
(B) Parliament (Union)
(C) Supreme Court
(D) More than one of the above
(E) None of the above

---

**Q40.** Fundamental Duties were added to the Constitution by:
(A) 44th Amendment Act, 1978
(B) 42nd Amendment Act, 1976
(C) 86th Amendment Act, 2002
(D) More than one of the above
(E) None of the above

---

**Q41.** The Right to Education (Article 21A) for children aged 6–14 years was added by:
(A) 42nd Amendment
(B) 73rd Amendment
(C) 86th Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q42.** Which of the following is a subject in the CONCURRENT LIST (both Parliament and State can legislate)?
(A) Defence (Union List)
(B) Agriculture (State List)
(C) Education
(D) More than one of the above
(E) None of the above

---

**Q43.** The concept of "Judicial Review" in India was borrowed from:
(A) UK
(B) USA
(C) Canada
(D) More than one of the above
(E) None of the above

---

**Q44.** India is described as "Union of States" in Article 1. This term was chosen instead of "Federation" to indicate:
(A) India is a unitary state with no state autonomy
(B) The Union is indestructible; states cannot secede
(C) India has more states than the USA
(D) More than one of the above
(E) None of the above

---

**Q45.** The 10th Schedule of the Constitution deals with:
(A) Panchayati Raj institutions
(B) Anti-Defection Law (added by 52nd Amendment 1985)
(C) Tribal areas administration
(D) More than one of the above
(E) None of the above

---

**Q46.** How long did the Constituent Assembly take to draft the Indian Constitution?
(A) 1 year
(B) 2 years, 11 months, and 18 days
(C) 5 years
(D) More than one of the above
(E) None of the above

---

**Q47.** Which of the following is NOT a Fundamental Right under the Indian Constitution?
(A) Right to Equality
(B) Right to Freedom of Religion
(C) Right to Property
(D) More than one of the above
(E) None of the above

---

**Q48.** The Preamble to the Indian Constitution was interpreted to be PART of the Constitution in which landmark case?
(A) Berubari Union Case (1960)
(B) Kesavananda Bharati Case (1973)
(C) Golaknath Case (1967)
(D) More than one of the above
(E) None of the above

---

**Q49.** Article 356 of the Indian Constitution deals with:
(A) President's pardoning power
(B) Establishment of Supreme Court
(C) President's Rule in States (failure of constitutional machinery)
(D) More than one of the above
(E) None of the above

---

**Q50.** Which country's constitution primarily inspired the concept of DPSP and Fundamental Duties in the Indian Constitution?
(A) USA — Fundamental Rights
(B) Ireland — DPSP; USSR — Fundamental Duties
(C) UK — both DPSP and Fundamental Duties
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
| 1 | (B) | Priority Queue = priority determines service, not arrival order |
| 2 | (C) | Min-Heap root = minimum element |
| 3 | (C) | Binary Heap: O(log n) insert + delete — most balanced |
| 4 | (C) | Insert in heap = O(log n) [heapify up] |
| 5 | (C) | Delete in heap = O(log n) [heapify down] |
| 6 | (C) | Peek = return root = O(1) |
| 7 | (B) | Heap shape property = COMPLETE binary tree |
| 8 | (B) | Max-Heap: parent ≥ all children |
| 9 | (B) | Left child of i (0-indexed) = 2i+1 |
| 10 | (B) | Parent of i (0-indexed) = (i-1)/2 |
| 11 | (B) | Dijkstra's uses Min-Priority Queue |
| 12 | (B) | Huffman: combine min-frequency nodes repeatedly |
| 13 | (B) | Ready Queue = processes in RAM waiting for CPU |
| 14 | (B) | Job Queue = all submitted processes (may not be in RAM yet) |
| 15 | (C) | After delete, LAST element placed at root before heapify-down |
| 16 | (B) | Heapify Up = after insertion, new element bubbles up |
| 17 | (C) | Floyd's Build-Heap = O(n) |
| 18 | (B) | BFS uses simple Queue (not priority queue) |
| 19 | (B) | Preemptive: higher priority process preempts current |
| 20 | (B) | Heap ≠ sorted array; only parent-child relationship guaranteed |
| 21 | (B) | [50,40,30,20,10]: 50≥40,50≥30,40≥20,40≥10,30's children absent → valid Max-Heap |
| 22 | (C) | Max/Min always at root → O(1) |
| 23 | (B) | Delete from Min-Heap = remove root (minimum) |
| 24 | (B) | Device Queue = processes waiting for specific I/O device |
| 25 | (B) | [1,3,2,7,9,4,5]: 1≤3,1≤2,3≤7,3≤9,2≤4,2≤5 → valid Min-Heap |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Adopted: November 26, 1949 (Constitution Day) |
| 27 | (B) | Came into force: January 26, 1950 (Republic Day) |
| 28 | (C) | Dr. B.R. Ambedkar = Chairman of Drafting Committee |
| 29 | (B) | Dr. Rajendra Prasad = President of Constituent Assembly |
| 30 | (B) | India = world's longest written constitution |
| 31 | (B) | 42nd Amendment 1976 added Socialist + Secular to Preamble |
| 32 | (C) | 6 Fundamental Rights (after 44th Amendment removed Right to Property) |
| 33 | (C) | Article 32 = "Heart and Soul" — Dr. Ambedkar's words |
| 34 | (B) | DPSP = non-justiciable, welfare state guidelines |
| 35 | (C) | DPSP borrowed from Ireland |
| 36 | (B) | 7th Schedule = Union, State, Concurrent Lists |
| 37 | (C) | 8th Schedule = 22 scheduled languages |
| 38 | (C) | Maithili added by 92nd Amendment 2003 (effective 2004) |
| 39 | (B) | Residuary powers → Parliament (Union) |
| 40 | (B) | Fundamental Duties added by 42nd Amendment 1976 |
| 41 | (C) | Article 21A (RTE) = 86th Amendment 2002 |
| 42 | (C) | Education = Concurrent List |
| 43 | (B) | Judicial Review = borrowed from USA |
| 44 | (B) | "Union" = indestructible union; states cannot secede |
| 45 | (B) | 10th Schedule = Anti-Defection Law |
| 46 | (B) | 2 years, 11 months, 18 days |
| 47 | (C) | Right to Property removed by 44th Amendment 1978 |
| 48 | (B) | Kesavananda Bharati (1973) = Preamble is part of Constitution |
| 49 | (C) | Article 356 = President's Rule in States |
| 50 | (B) | Ireland → DPSP; USSR → Fundamental Duties |

---
---

# 🔁 DAY 20 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Priority Queue & Heap

### Core Rules:
```
Priority Queue: Highest-priority element served FIRST (NOT FIFO)
Min-Heap: Root = MINIMUM; parent ≤ children everywhere
Max-Heap: Root = MAXIMUM; parent ≥ children everywhere
Shape:    COMPLETE Binary Tree (last level left-to-right, no gaps)
```

### Index Formulas (0-indexed) — Must Memorize:
```
Left child  of node at i: 2i + 1
Right child of node at i: 2i + 2
Parent      of node at i: (i-1)/2  [integer division]
```

### Time Complexity:
```
Operation        Binary Heap    Sorted Array   Unsorted Array
Insert           O(log n)       O(n)           O(1)
Delete (max/min) O(log n)       O(1)           O(n)
Peek (max/min)   O(1)           O(1)           O(n)
Build heap       O(n) [Floyd]   —              —
```

### Applications of Priority Queue:
```
✅ Dijkstra's shortest path → Min-Heap
✅ Huffman Coding → Min-Heap
✅ CPU Scheduling (Priority) → Max-Heap
✅ Prim's MST → Min-Heap
✅ Event-driven simulation → Min-Heap

NOT Priority Queue:
❌ BFS → simple Queue
❌ DFS → Stack
❌ Expression conversion → Stack
```

### OS Queues:
```
Job Queue    → All submitted processes (long-term scheduler)
Ready Queue  → Processes in RAM, waiting for CPU (short-term scheduler)
Device Queue → Processes waiting for specific I/O device
```

---

## ⚡ RAPID FIRE — Indian Constitution

### 5 Core Dates:
```
December 9, 1946  → Constituent Assembly first meeting
November 26, 1949 → Constitution ADOPTED (Constitution Day)
January 26, 1950  → Constitution came into FORCE (Republic Day)
1976 (42nd Amend) → Socialist + Secular added to Preamble; FDs added
2002 (86th Amend) → Right to Education (Article 21A) added
```

### Key People:
```
Dr. Rajendra Prasad (Bihar!) → President of Constituent Assembly + First President
Dr. B.R. Ambedkar → Chairman of Drafting Committee ("Father of Constitution")
```

### 6 Fundamental Rights (Post-1978):
```
1. Right to Equality (14-18)
2. Right to Freedom (19-22)
3. Right Against Exploitation (23-24)
4. Right to Freedom of Religion (25-28)
5. Cultural & Educational Rights (29-30)
6. Right to Constitutional Remedies (32) ← "Heart and Soul"
```

### Key Sources:
```
UK → Parliamentary govt, Rule of Law
USA → Fundamental Rights, Judicial Review
Ireland → DPSP
Canada → Federal + strong Centre, Residuary to Union
Australia → Concurrent List
USSR → Fundamental Duties
42nd Amendment → Socialist, Secular, Fundamental Duties
```

### Key Schedules:
```
7th → Union (97), State (66), Concurrent (52) Lists
8th → 22 Scheduled Languages (Maithili added 2003)
10th → Anti-Defection Law
11th → Panchayati Raj (73rd Amend)
```

### Critical Traps:
```
❌ Preamble: "Socialist" + "Secular" = NOT original (added 1976)
❌ FRs = 6 (not 7, after Right to Property removed 1978)
❌ DPSP = NOT enforceable (unlike Fundamental Rights)
❌ Residuary powers → UNION (not States, unlike USA)
❌ Constitution ADOPTED Nov 26 ≠ came into force Jan 26
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Heap: Complete binary tree; Min-Heap root=min; Max-Heap root=max; Insert/Delete=O(log n); Peek=O(1)
2. Index formulas (0-based): Left=2i+1, Right=2i+2, Parent=(i-1)/2
3. PQ applications: Dijkstra (Min-Heap), Huffman (Min-Heap), CPU Scheduling (Max-Heap)
4. Constitution adopted Nov 26, 1949; came into force Jan 26, 1950; Dr. Ambedkar = Drafting Committee Chair
5. 6 FRs; DPSP = non-justiciable (from Ireland); Socialist+Secular added by 42nd Amendment 1976

---

*Next: Day 21 — REVISION DAY: Arrays, Stacks, Queues Week 3 Complete Review + GS Revision*
