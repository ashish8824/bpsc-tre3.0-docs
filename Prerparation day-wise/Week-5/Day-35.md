# 📅 DAY-35 — BPSC TRE 4.0 STUDY FILE
## CS: FULL DSA GRAND REVISION (Day 15–34) | GS: Full GS Revision — History + Maths
### 🎯 Phase 1 — Week 5 FINAL DAY | TARGET: TOPPER RANK

---

> **📌 DAY-35 SPECIAL — GRAND REVISION DAY**
> Today is the MOST IMPORTANT day of Week 5.
> Every fact here has appeared in TRE 1.0, TRE 2.0, or TRE 3.0 papers.
> This is your LAST CHANCE to fix gaps before moving to DBMS (Week 6).
>
> - **Morning (1.5 hrs):** Complete DSA Grand Revision — ALL topics, ALL traps, ALL formulas
> - **Afternoon (1 hr):** GS Full Revision — Modern Indian History + Mathematics
> - **Evening (1 hr):** 50 MCQs (25 CS + 25 GS) — ATTEMPT ALL before checking answers
> - **Night (30 min):** Write the complete DSA checklist from MEMORY — no peeking

---

# 🖥️ PART A: COMPUTER SCIENCE — FULL DSA GRAND REVISION

## The Ultimate Revision Roadmap (Day 15 → Day 34)

---

## 🔷 CHAPTER 1: ARRAYS — The Foundation

### 1.1 Core Properties

```
ARRAY = Fixed-size, contiguous memory, same data type

Memory Layout:
  Address: 1000  1004  1008  1012  1016
           [10]  [20]  [30]  [40]  [50]
  Index:    [0]   [1]   [2]   [3]   [4]

Access arr[2] = 1000 + (2 × 4) = 1008 → Direct! → O(1)
```

| Operation | Time | Explanation |
|-----------|------|-------------|
| Access by index | **O(1)** | Direct address calculation |
| Search (unsorted) | O(n) | Linear scan |
| Search (sorted) | O(log n) | Binary search |
| Insert at end | O(1) | Just place at index n |
| Insert at middle | O(n) | Shift elements right |
| Delete at middle | O(n) | Shift elements left |

> ⭐ **TOPPER FACT:** The MAIN ADVANTAGE of arrays = **Random access in O(1)** using index. This is why arrays are preferred over linked lists when frequent access is needed.

### 1.2 Sparse Matrix

```
SPARSE MATRIX = Matrix where zero elements > (m × n)/2
                (More than half the elements are zero)

Example (4×4 matrix — 10 zeros out of 16 = 62.5% zeros):
  0  0  0  3
  0  5  0  0
  0  0  0  7
  0  0  0  0
  → This is SPARSE (store only non-zero values to save space)
  
Storage methods: COO (Coordinate), CSR (Compressed Sparse Row)
```

---

## 🔷 CHAPTER 2: STACK — The LIFO Master

### 2.1 Complete Properties Snapshot

```
STACK = LIFO (Last In First Out)
        Operations only at ONE end = TOP

        PUSH (add)    POP (remove)
             ↓             ↑
         ┌───────┐
         │  50   │  ← TOP (most recently added)
         │  40   │
         │  30   │
         │  20   │
         │  10   │  ← Bottom (first added, last removed)
         └───────┘

State: isEmpty → top == -1
       isFull  → top == MAX_SIZE - 1
```

### 2.2 The Complete Application Map

```
STACK APPLICATIONS ✅          NOT STACK ❌
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
String Reversal                 Asynchronous data transfer → QUEUE
Expression Evaluation           CPU Scheduling → QUEUE
Infix → Postfix/Prefix          Printer Spooling → QUEUE
Balancing Parentheses/Symbols   BFS Traversal → QUEUE
RECURSION (most tested!)        Job Scheduling → QUEUE
Backtracking                    Process Management → QUEUE
Browser Back button
Undo operation in editors
```

> ⭐ **PYQ DIRECT (TRE 1.0 + TRE 2.0 BOTH asked this):**
> "Recursion uses which data structure?" → **STACK**
> "Asynchronous data transfer uses which data structure?" → **QUEUE**

### 2.3 Infix → Postfix Conversion — The Complete Algorithm

```
OPERATOR PRECEDENCE (Higher number = Higher priority):
  ^ (Exponent)    → Priority 3, Right-to-Left associative
  * /             → Priority 2, Left-to-Right
  + -             → Priority 1, Left-to-Right
  ( )             → Special (bracket handling)

ALGORITHM:
  For each symbol in infix:
  ┌─────────────────────────────────────────────────────┐
  │ Operand (A,B,1,2...)  → Write to output directly    │
  │ '('                   → Push to stack               │
  │ ')'                   → Pop & output until '('      │
  │ Operator (+,-,*,/)    → Pop operators with >=       │
  │                         precedence, then push self  │
  └─────────────────────────────────────────────────────┘
  At end: Pop ALL remaining stack elements to output

TIME COMPLEXITY: O(N)
```

**Worked PYQ Example:**
```
Convert: (A + B) * (C - D) to Postfix

Token | Action              | Stack   | Output
------|---------------------|---------|----------
(     | Push (              | (       |
A     | Output              | (       | A
+     | Push +              | ( +     | A
B     | Output              | ( +     | AB
)     | Pop till (: pop +   | empty   | AB+
*     | Push *              | *       | AB+
(     | Push (              | * (     | AB+
C     | Output              | * (     | AB+C
-     | Push -              | * ( -   | AB+C
D     | Output              | * ( -   | AB+CD
)     | Pop till (: pop -   | *       | AB+CD-
End   | Pop all: pop *      | empty   | AB+CD-*

POSTFIX: A B + C D - *    ✓
```

---

## 🔷 CHAPTER 3: QUEUE — The FIFO Master

### 3.1 All Queue Types — Side by Side

```
LINEAR QUEUE:
  FRONT→[10][20][30][40]←REAR
  Problem: After dequeue, front spaces WASTED

CIRCULAR QUEUE (Ring Buffer):
  [40][  ][  ][10][20][30]
    ↑                ↑
   rear            front
  Advantage: Reuses freed positions → No wastage

DEQUE (Double-Ended Queue):
  ←[10][20][30][40]→
  Insert/Delete at BOTH ends

PRIORITY QUEUE:
  Elements served by PRIORITY not order
  Best implemented: Binary Heap
```

### 3.2 Circular Queue — The #1 PYQ Topic

```
CIRCULAR QUEUE CONDITIONS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
EMPTY:  front = rear = -1
FULL:   (rear + 1) % SIZE == front
INSERT: rear = (rear + 1) % SIZE
DELETE: front = (front + 1) % SIZE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Also known as: RING BUFFER
Created to solve: Memory wastage in linear queue
```

> ⭐ **PYQ REPEATED FACT:** Circular Queue empty = **front = rear = -1**

### 3.3 Deque Special Case

```
DEQUE implemented with SINGLY Linked List:
  Delete from REAR → O(N)    ← PYQ TRAP!
  (Must traverse to find second-to-last node)
  
DEQUE implemented with DOUBLY Linked List:
  Delete from REAR → O(1)    ← Fast!
  (prev pointer allows direct access)
```

---

## 🔷 CHAPTER 4: LINKED LIST — All Types Compared

### 4.1 Visual Comparison

```
SINGLY LINKED LIST:
  HEAD→[D|→][D|→][D|→][D|→NULL]
       Traversal: ONE direction only

DOUBLY LINKED LIST:
  HEAD→[←|D|→]↔[←|D|→]↔[←|D|→]↔[←|D|NULL]
       Traversal: BOTH directions
       Extra: prev pointer in each node
       HARDER to implement ← PYQ fact!

CIRCULAR SINGLY LINKED LIST:
  [D|→][D|→][D|→][D|→]
   ↑_________________________↑
   Last node points back to FIRST

CIRCULAR DOUBLY LINKED LIST:
  Most flexible; used in OS for process scheduling
```

### 4.2 Operation Complexity Comparison

| Operation | Array | Singly LL | Doubly LL |
|-----------|-------|-----------|-----------|
| Access by index | **O(1)** | O(n) | O(n) |
| Insert at beginning | O(n) | **O(1)** | **O(1)** |
| Insert at end | O(1)* | O(n) | **O(1)** with tail |
| Delete at beginning | O(n) | **O(1)** | **O(1)** |
| Delete at end | O(1)* | O(n) | **O(1)** with tail |
| Search | O(n) | O(n) | O(n) |
| Memory | Less | More (1 ptr/node) | Most (2 ptrs/node) |

> ⭐ **PYQ KEY FACTS:**
> 1. Linked List's main advantage over Array = **Dynamic size** (no fixed capacity)
> 2. Linked List's main disadvantage = **No random access** (must traverse from head)
> 3. Doubly LL = **HARDER** to implement than Singly LL

---

## 🔷 CHAPTER 5: TREES — Complete Hierarchy

### 5.1 Full Terminology Reference

```
          A          ← ROOT (Level 0)
         / \
        B   C        ← Level 1
       / \   \
      D   E   F      ← Level 2
         /
        G            ← Level 3 (LEAF - no children)

TERMS:
  Root        = A (no parent)
  Leaves      = D, F, G (no children) 
  Internal    = A, B, C, E (have children)
  Height      = 3 (longest root-to-leaf path)
  Depth of E  = 2 (distance from root)
  Degree of B = 2 (has 2 children: D, E)
  Siblings    = B and C (same parent)
```

### 5.2 Types of Binary Trees

```
1. FULL (Strict) Binary Tree:
   Every node has 0 or 2 children
   ✓ Valid:     A          ✗ Invalid:  A
               / \                    /
              B   C                  B
             / \
            D   E

2. COMPLETE Binary Tree:
   All levels full EXCEPT last; last filled LEFT to RIGHT
   ✓ Valid:     A          ✗ Invalid:  A
               / \                   / \
              B   C                 B   C
             / \  /                  \
            D   E F                   E

3. PERFECT Binary Tree:
   ALL internal nodes have 2 children + ALL leaves at same level
        A
       / \
      B   C
     / \ / \
    D  E F  G

4. BALANCED Binary Tree:
   |Height(left) - Height(right)| ≤ 1 for EVERY node
   AVL Tree is a balanced BST
```

### 5.3 Tree Traversals — The Ultimate Summary

```
Given tree:
          1
         / \
        2   3
       / \   \
      4   5   6

┌────────────┬─────────────────────────┬─────────────────────┐
│ Traversal  │ Order                   │ Result              │
├────────────┼─────────────────────────┼─────────────────────┤
│ PREORDER   │ ROOT → Left → Right     │ 1, 2, 4, 5, 3, 6   │
│ INORDER    │ Left → ROOT → Right     │ 4, 2, 5, 1, 3, 6   │
│ POSTORDER  │ Left → Right → ROOT     │ 4, 5, 2, 6, 3, 1   │
│ LEVEL ORDER│ Level by Level (BFS)    │ 1, 2, 3, 4, 5, 6   │
└────────────┴─────────────────────────┴─────────────────────┘

Memory Trick:
  PRE-order = ROOT comes first (PREfirst)
  IN-order  = ROOT comes IN the middle
  POST-order = ROOT comes LAST (POST = after)
```

> ⭐ **PYQ TRAP:** "Randomized traversal" is NOT a valid tree traversal. It does NOT exist!
> ⭐ **PYQ FACT:** Inorder traversal of BST = **Sorted ascending order**

### 5.4 Deriving Traversals from One Traversal

**A very common BPSC PYQ type — Practice this!**

```
Given PREORDER: 5, 3, 1, 4, 7, 6, 8

Step 1: First element of Preorder = ROOT = 5

Step 2: Find 5 in Inorder (must have Inorder):
        Inorder: 1, 3, 4, 5, 6, 7, 8
        Elements LEFT of 5 in Inorder: {1, 3, 4} = Left subtree
        Elements RIGHT of 5 in Inorder: {6, 7, 8} = Right subtree

Step 3: Build the BST:
                5
               / \
              3   7
             / \ / \
            1  4 6  8

PREORDER:  5, 3, 1, 4, 7, 6, 8  ✓
INORDER:   1, 3, 4, 5, 6, 7, 8  ✓ (sorted!)
POSTORDER: 1, 4, 3, 6, 8, 7, 5
```

---

## 🔷 CHAPTER 6: BST + RED-BLACK TREE

### 6.1 BST — 3 Properties (ALL MUST HOLD)

```
BST RULE — ALL THREE must be true simultaneously:

Property 1: For every node X:
            ALL nodes in LEFT subtree < X
            
Property 2: For every node X:
            ALL nodes in RIGHT subtree > X
            
Property 3: Left subtree and Right subtree are ALSO valid BSTs
            (Recursive definition!)

VALID BST:           INVALID BST:
        8                    8
       / \                  / \
      3   10                3   10
     / \    \              / \    \
    1   6    14           1   12   14  ← 12 > 8, should be in right subtree!
       / \   /                        ← This is NOT a valid BST
      4   7 13
```

### 6.2 BST Operations Complexity

| Operation | Average (Balanced) | Worst (Skewed) |
|-----------|-------------------|----------------|
| Search | O(log n) | O(n) |
| Insert | O(log n) | O(n) |
| Delete | O(log n) | O(n) |

```
SKEWED BST (worst case — like a linked list):
  1
   \
    2
     \
      3
       \
        4  → Height = n → All operations O(n)

BALANCED BST (best case):
      2
     / \
    1   3  → Height = log n → All operations O(log n)
```

### 6.3 Catalan Number — C(4) = 14

```
Formula: C(n) = (2n)! / ((n+1)! × n!)

Verification for n=4:
  C(4) = 8! / (5! × 4!)
       = 40320 / (120 × 24)
       = 40320 / 2880
       = 14  ✓

VALUES TO MEMORIZE:
  C(0) = 1
  C(1) = 1
  C(2) = 2
  C(3) = 5
  C(4) = 14  ← BPSC FAVOURITE!
  C(5) = 42
```

### 6.4 Red-Black Tree — Color Rules

```
RED-BLACK TREE RULES:
  1. Every node = RED or BLACK
  2. ROOT = always BLACK
  3. Every NULL leaf = BLACK
  4. RED node → both children must be BLACK
  5. All paths from node to NULL have same BLACK node count

PYQ RULE:
  New ROOT node inserted → Color = BLACK
  New non-root node → Color = RED (initially; may change on rotation)
```

---

## 🔷 CHAPTER 7: GRAPHS — Key Concepts

### 7.1 Graph Representations

```
GRAPH: G = (V, E)  where V = vertices, E = edges

Given graph:
  A — B — C
  |       |
  D ——————

ADJACENCY MATRIX (4×4):
     A  B  C  D
  A [0  1  0  1]
  B [1  0  1  0]
  C [0  1  0  1]
  D [1  0  1  0]
  Space: O(V²); Good for dense graphs

ADJACENCY LIST:
  A: [B, D]
  B: [A, C]
  C: [B, D]
  D: [A, C]
  Space: O(V+E); Good for sparse graphs
```

### 7.2 BFS vs DFS — Side by Side

```
BFS (Breadth-First Search)        DFS (Depth-First Search)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Uses: QUEUE                       Uses: STACK (or recursion)
Explores: Level by level          Explores: Goes deep first
Result: Shortest path (unweighted) Result: Cycle detection, Topological sort
Time: O(V + E)                    Time: O(V + E)
Space: O(V)                       Space: O(V)

BFS traversal order for:          DFS traversal order for:
        A                                 A
       / \                               / \
      B   C            →BFS: A,B,C,D,E,F   →DFS: A,B,D,E,C,F
     / \   \
    D   E   F
```

### 7.3 Spanning Tree

```
SPANNING TREE:
  Subgraph that connects ALL vertices with MINIMUM edges
  
  For N vertices:
  Spanning tree has N-1 edges (always!)
  
  Example: 5 vertices → Spanning tree has 4 edges

MINIMUM SPANNING TREE (MST):
  Spanning tree with minimum total edge weight
  Algorithms: Kruskal's and Prim's (both Greedy)

SPANNING TREE vs MST:
  Multiple spanning trees possible for same graph
  MST = unique spanning tree with minimum total weight
```

---

## 🔷 CHAPTER 8: SORTING — The Grand Comparison

### 8.1 Master Sorting Table

```
┌─────────────┬───────────┬───────────┬───────────┬────────┬────────┬──────────┐
│ Algorithm   │ Best      │ Average   │ Worst     │ Space  │ Stable │ Paradigm │
├─────────────┼───────────┼───────────┼───────────┼────────┼────────┼──────────┤
│ Bubble      │ O(n)      │ O(n²)     │ O(n²)     │ O(1)   │ YES ✓  │ Compare  │
│ Selection   │ O(n²)     │ O(n²)     │ O(n²)     │ O(1)   │ NO ✗   │ Compare  │
│ Insertion   │ O(n)      │ O(n²)     │ O(n²)     │ O(1)   │ YES ✓  │ Compare  │
│ Merge Sort  │ O(n log n)│ O(n log n)│ O(n log n)│ O(n)   │ YES ✓  │ D&C      │
│ Quick Sort  │ O(n log n)│ O(n log n)│ O(n²)     │O(log n)│ NO ✗   │ D&C      │
│ Heap Sort   │ O(n log n)│ O(n log n)│ O(n log n)│ O(1)   │ NO ✗   │ Heap     │
│ Radix Sort  │ O(nk)     │ O(nk)     │ O(nk)     │ O(n+k) │ YES ✓  │ Non-comp │
│ Counting    │ O(n+k)    │ O(n+k)    │ O(n+k)    │ O(k)   │ YES ✓  │ Non-comp │
└─────────────┴───────────┴───────────┴───────────┴────────┴────────┴──────────┘
```

### 8.2 Critical PYQ Facts About Sorting

```
BPSC MOST-TESTED SORTING FACTS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. Merge Sort = O(n log n) in ALL cases → GUARANTEED
2. Quick Sort = O(n²) WORST case (sorted input + bad pivot)
3. Quick Sort worst case: Already sorted array!
4. Bubble Sort best case = O(n) (only with optimization/flag)
5. Selection Sort = O(n²) ALWAYS (no optimization possible)
6. Merge Sort = NOT in-place (needs O(n) extra space)
7. Heap Sort = IN-PLACE (O(1) extra space)
8. Merge Sort + Quick Sort = BOTH Divide & Conquer
9. Radix Sort = NON-COMPARISON based (can beat O(n log n) lower bound)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STABLE SORTING (Equal elements maintain original order):
  STABLE   = Bubble, Insertion, MERGE, Counting, Radix
  UNSTABLE = Selection, Quick, Heap
  
  Memory trick: "Big Iguanas Make Cute Rabbits" = Stable
  (Bubble, Insertion, Merge, Counting, Radix)
```

---

## 🔷 CHAPTER 9: SEARCHING & HASHING

### 9.1 Binary Search — Full Trace

```
Array: [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
        0    1   2   3   4   5   6   7   8    9
Search: 70

Round 1: low=0, high=9, mid=4 → arr[4]=50 < 70 → go RIGHT
Round 2: low=5, high=9, mid=7 → arr[7]=80 > 70 → go LEFT  
Round 3: low=5, high=6, mid=5 → arr[5]=60 < 70 → go RIGHT
Round 4: low=6, high=6, mid=6 → arr[6]=70 = 70 → FOUND! ✓

Comparisons: 4 = approximately log₂(10) ≈ 3.32 → O(log n)

REQUIREMENT: Array MUST be sorted!
```

### 9.2 Hashing — Collision Handling

```
HASH TABLE:
  key → hash(key) → index → value

COLLISION = Two keys hash to same index

METHODS TO RESOLVE:
  
  1. CHAINING (Open Hashing):
     Each slot has a linked list
     [0] → [A] → [D] → NULL
     [1] → [B] → NULL
     [2] → [C] → [E] → NULL
     
  2. OPEN ADDRESSING (Closed Hashing):
     All entries stored in table itself
     a) Linear Probing:    try (h+1)%n, (h+2)%n...
     b) Quadratic Probing: try (h+1²)%n, (h+2²)%n...
     c) Double Hashing:    try (h + i×h₂(k))%n

LOAD FACTOR (α) = n/m  (n=elements, m=table size)
  α close to 0 → Few collisions → Fast
  α close to 1 → Many collisions → Slow
```

> ⭐ **PYQ FACT:** Hash Table = best for **O(1) average** search, insert, delete.

---

## 🔷 CHAPTER 10: COMPLEXITY & NP — Quick Reference

### 10.1 Big-O Cheat Sheet

```
FASTEST                                              SLOWEST
  O(1) → O(log n) → O(n) → O(n log n) → O(n²) → O(2ⁿ) → O(n!)

OPERATION                       │ COMPLEXITY
────────────────────────────────┼───────────────
Array/Hash access               │ O(1)
Stack push/pop                  │ O(1)
Queue enqueue/dequeue           │ O(1)
Binary Search                   │ O(log n)
Infix → Postfix conversion      │ O(n)
Linear Search                   │ O(n)
BST search (balanced)           │ O(log n)
BST search (skewed)             │ O(n)
Merge Sort (all cases)          │ O(n log n)
Quick Sort (avg)                │ O(n log n)
Quick Sort (worst)              │ O(n²)
Bubble/Selection/Insertion(worst)│ O(n²)
Floyd-Warshall                  │ O(V³)
BFS / DFS                       │ O(V + E)
```

### 10.2 P vs NP Quick Reference

```
CLASS P:
  Problems SOLVABLE in polynomial time
  Examples: Sorting, Binary Search, Shortest Path (Dijkstra's), MST

CLASS NP:
  Problems VERIFIABLE in polynomial time
  Examples: TSP, SAT, Hamiltonian Cycle, Graph Coloring

NP-COMPLETE:
  Hardest in NP; every NP problem reduces to it
  Examples: TSP, SAT (first NPC by Cook 1971), Hamiltonian Cycle

CRITICAL PAIRS (PYQ TRAP):
  Shortest Path       → P (polynomial!)
  Longest Path        → NP-Hard
  Eulerian Cycle      → P (O(V+E))
  Hamiltonian Cycle   → NP-Complete
  2-Coloring          → P (bipartite check)
  3-Coloring (k≥3)    → NP-Complete
  MST                 → P (Kruskal/Prim)
  TSP optimization    → NP-Complete
```

---

## 🔷 THE GRAND DSA CHECKLIST — Complete Before Exam

```
✅ MUST KNOW — MARK EACH AS YOU REVIEW:

STACK:
□ LIFO definition
□ All 4 correct applications (Recursion, Backtracking, Expression eval, Balancing)
□ NOT an application: Asynchronous transfer → Queue
□ Infix-Postfix: uses Stack, time O(N)
□ Overflow/Underflow conditions

QUEUE:
□ FIFO definition
□ Before deletion → check Underflow
□ Before insertion → check Overflow
□ Circular Queue = Ring Buffer
□ Circular Queue empty: front = rear = -1
□ Circular Queue full: (rear+1)%SIZE == front
□ Created to solve: Memory wastage of linear queue
□ Deque: delete from rear with singly LL = O(N)
□ Priority Queue → Binary Heap

LINKED LIST:
□ Singly, Doubly, Circular types
□ No random access (main disadvantage vs array)
□ Doubly LL: HARDER to implement than Singly
□ Dynamic size (main advantage over array)

TREES & BST:
□ Preorder: Root→L→R | Inorder: L→Root→R | Postorder: L→R→Root
□ "Randomized traversal" DOES NOT EXIST
□ Inorder of BST = Sorted order
□ BST: Left < Root < Right (for ALL nodes in subtrees)
□ C(4) = 14 distinct BSTs (Catalan number)
□ Red-Black: new root = BLACK; new non-root = RED
□ Spanning tree N vertices = N-1 edges

SORTING:
□ Merge Sort: O(n log n) ALWAYS, Stable, NOT in-place, D&C
□ Quick Sort: O(n²) WORST, Unstable, in-place, D&C
□ Selection Sort: O(n²) ALWAYS, Unstable
□ Bubble Sort: O(n) BEST case (already sorted), Stable
□ Heap Sort: O(n log n), Unstable, IN-PLACE

SEARCHING & HASHING:
□ Binary Search: O(log n), requires SORTED array
□ Hash Table: O(1) average for all operations
□ Collision: Chaining vs Open Addressing

COMPLEXITY:
□ Big-O = Upper bound (worst case)
□ P = solvable in polynomial | NP = verifiable in polynomial
□ Shortest Path = P | TSP = NP-Complete
□ SAT = first NP-Complete problem (Cook, 1971)
```

---

# 🌍 PART B: GENERAL STUDIES — FULL REVISION (History + Maths)

> **Day-35 GS Goal:** This week we covered Modern Indian History (freedom struggle topics from Days 8–13), India/Bihar Geography (Days 15, 27, 33–34), and Maths (Days 1–7). Today we revise ALL of it deeply.

---

## 🔶 SECTION 1: MODERN INDIAN HISTORY — Complete Revision

### 1.1 Freedom Struggle — Chronological Timeline

```
FREEDOM STRUGGLE TIMELINE (MUST KNOW ALL DATES):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1757  Battle of Plassey — British defeat Siraj-ud-Daula
1764  Battle of Buxar — British defeat Mir Qasim + Nawab of Awadh + Mughal Emperor
1857  Revolt of 1857 (First War of Independence / Sipoy Mutiny)
1885  Indian National Congress (INC) founded — A.O. Hume
1905  Partition of Bengal — Lord Curzon
1906  Muslim League founded — Dhaka
1907  Surat Split (INC divides into Moderates & Extremists)
1909  Morley-Minto Reforms (Indian Councils Act)
1915  Gandhi returns to India from South Africa
1916  Lucknow Pact — Hindu-Muslim unity
1917  Champaran Satyagraha — Gandhi's FIRST civil disobedience in India
1919  Rowlatt Act + Jallianwala Bagh Massacre (April 13)
1920  Non-Cooperation Movement launched
1922  Chauri Chaura incident → Gandhi WITHDRAWS Non-Cooperation
1922  INC Gaya Session (President: Chittaranjan Das)
1927  Simon Commission (all British, no Indians)
1929  Lahore Session — Complete Independence (Purna Swaraj) declared
1930  Civil Disobedience Movement + Dandi March (March 12)
1931  Gandhi-Irwin Pact + Second RTC
1932  Communal Award + Poona Pact (Gandhi's fast)
1935  Government of India Act
1940  Lahore Resolution (Muslim League demands Pakistan)
1942  Quit India Movement ("Do or Die") — August 8-9
1943  INA formed by Subhas Chandra Bose in Singapore
1945  Shimla Conference
1946  Cabinet Mission Plan
1947  Independence — August 15
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 1.2 Champaran Satyagraha (1917) — Bihar's Own Freedom Moment

```
CHAMPARAN SATYAGRAHA 1917:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Who:  Mahatma Gandhi + Rajendra Prasad
      (Rajendra Prasad later became India's 1st President)
      
When: 1917 (exact: April 1917)

Where: Champaran district, Bihar (indigo farmers)

Why:  Tinkathia system — farmers FORCED to grow indigo
      on 3/20 (tinkathi) of their land for British planters
      No fair payment

How Gandhi heard: Rajkumar Shukla brought Gandhi to Bihar

Result:
  - Champaran Agrarian Act passed
  - Tinkathia system abolished
  - Gandhi's 1st Satyagraha IN INDIA
  - Gandhi's first use of civil disobedience in India
  
KEY FACT: This was FIRST application of Satyagraha in India
          (Gandhi had previously used it in South Africa)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 1.3 Major Movements — Quick Reference Card

```
NON-COOPERATION MOVEMENT (1920–22):
  Launched: September 1920 (Calcutta Congress)
  Cause: Rowlatt Act + Jallianwala Bagh (1919)
  Methods: Boycott of British goods/schools/courts/councils
  End: February 1922 — Chauri Chaura (22 police killed)
  Gandhi stopped: "People not ready for nonviolence"

CIVIL DISOBEDIENCE MOVEMENT (1930–34):
  Start: Dandi March — March 12, 1930
  Gandhi walked 241 miles (24 days) from Sabarmati to Dandi
  Made salt → broke Salt Law
  Also called: Salt Satyagraha
  Ended: Gandhi-Irwin Pact (March 1931)
  Resumed after First RTC failure (Jan 1932)

QUIT INDIA MOVEMENT (1942):
  Date: August 8-9, 1942
  Slogan: "Do or Die" (Karo ya Maro)
  Launched at: Gowalia Tank, Bombay (now August Kranti Maidan)
  Gandhi arrested next morning (August 9)
  Mass uprising — most violent of all movements
  Significance: Last major movement before independence
```

### 1.4 Key Leaders and Their Associations

| Leader | Association / Achievement |
|--------|--------------------------|
| **A.O. Hume** | Founded INC (1885) |
| **W.C. Bonnerjee** | First President of INC |
| **Dadabhai Naoroji** | "Grand Old Man of India"; Drain of Wealth theory |
| **Gopal Krishna Gokhale** | Gandhi's political guru; Moderate leader |
| **Bal Gangadhar Tilak** | "Swaraj is my birthright" — Extremist leader |
| **Lala Lajpat Rai** | Punjab Kesari; died after lathi charge (1928) |
| **Bipin Chandra Pal** | Extremist; part of Lal-Bal-Pal trio |
| **V.D. Savarkar** | Founded Abhinav Bharat (London); first to call 1857 "War of Independence" |
| **Bhagat Singh** | Revolutionary; hanged March 23, 1931 |
| **Subhas Chandra Bose** | INA; "Give me blood, I'll give you freedom" |
| **Rajendra Prasad** | Champaran; First President of India |
| **Jayaprakash Narayan** | Bihar Socialist Party; JP Movement (1974) |
| **Swami Sahajanand Saraswati** | AIKS (All India Kisan Sabha) in Bihar, 1936 |

### 1.5 Bihar-Specific Freedom Struggle Facts (PYQ Direct)

| Fact | Answer |
|------|--------|
| Champaran Satyagraha leader | **Gandhi + Rajendra Prasad** |
| Bihar Provincial Congress Committee founded | **1908** |
| INC Gaya Session (1922) President | **Chittaranjan Das** |
| Anushilan Samiti Patna (1913) founder | **Sachindra Nath Sanyal** |
| Bihar Socialist Party founders | **Phulan Prasad Varma + Jayaprakash Narayan** |
| AIKS Bihar 1936 | **Swami Sahajanand Saraswati** |
| First Bhojpuri film | **Ganga Maiya Tohe Piyari Chadhaibo** |
| Birsa Munda's Commander-in-Chief | **Gaya Munda** |
| Ghadar Party established in | **USA (San Francisco, 1913)** |
| Revolt of 1857 — first called "War of Independence" by | **V.D. Savarkar** |

### 1.6 Important Viceroys and Their Events

| Viceroy | Key Event |
|---------|----------|
| **Lord Canning** | Revolt of 1857; first Viceroy after company rule ended |
| **Lord Dalhousie** | Doctrine of Lapse; Railways started; Telegraph |
| **Lord Curzon** | Partition of Bengal (1905) |
| **Lord Minto** | Morley-Minto Reforms (1909) |
| **Lord Chelmsford** | Rowlatt Act + Jallianwala Bagh (1919) |
| **Lord Irwin** | Civil Disobedience; Gandhi-Irwin Pact (1931) |
| **Lord Mountbatten** | Last Viceroy; Partition and Independence (1947) |

### 1.7 Socio-Religious Reform Movements

| Organization | Founder | Year | Key Work |
|-------------|---------|------|----------|
| **Brahmo Samaj** | Raja Ram Mohan Roy | 1828 | Against sati, caste; promoted English education |
| **Arya Samaj** | Dayananda Saraswati | 1875 | "Back to Vedas"; Shuddhi movement |
| **Ramakrishna Mission** | Vivekananda | 1897 | Service + Vedanta philosophy |
| **Aligarh Movement** | Sir Syed Ahmad Khan | 1875 | MAO College → AMU; Muslim education |
| **Prarthana Samaj** | Atmaram Pandurung | 1867 | Maharashtra reform |
| **Satyashodhak Samaj** | Jyotiba Phule | 1873 | Against caste discrimination |
| **Theosophical Society** | Helena Blavatsky (Annie Besant joined) | 1875 | Universal brotherhood |

---

## 🔶 SECTION 2: MATHEMATICS — Complete Revision

### 2.1 Percentage — Core Formulas

```
BASIC DEFINITIONS:
  Percentage = Parts per 100

FORMULAS:
  % of a number:  x% of N = (x/100) × N
  
  What % is A of B:  (A/B) × 100
  
  Percentage Increase:
    New Value = Old × (1 + r/100)
    
  Percentage Decrease:
    New Value = Old × (1 - r/100)
    
  % Change = [(New - Old) / Old] × 100
```

**Example Problems:**
```
Q: 120 is what % of 480?
A: (120/480) × 100 = 25%

Q: A price increases from 200 to 250. % increase?
A: [(250-200)/200] × 100 = (50/200) × 100 = 25%

Q: 40% of 350 = ?
A: (40/100) × 350 = 140
```

### 2.2 Profit & Loss — PYQ Formula Sheet

```
DEFINITIONS:
  CP = Cost Price (buying price)
  SP = Selling Price
  MP = Marked Price (printed price)
  
PROFIT:  SP > CP → Profit = SP - CP
LOSS:    SP < CP → Loss = CP - SP

FORMULAS:
  Profit%  = (Profit / CP) × 100
  Loss%    = (Loss / CP) × 100
  
  SP = CP × (1 + Profit%/100)     [when profit]
  SP = CP × (1 - Loss%/100)       [when loss]
  
  CP = SP / (1 + Profit%/100)     [find CP from SP]
  CP = SP / (1 - Loss%/100)
  
DISCOUNT:
  Discount = MP - SP
  Discount% = (Discount / MP) × 100
  SP = MP × (1 - Discount%/100)
```

**Example Problems:**
```
Q: An item bought for ₹200, sold for ₹250. Profit%?
A: Profit = 50; Profit% = (50/200)×100 = 25%

Q: Cost price ₹500, profit 20%. Find SP.
A: SP = 500 × (1 + 20/100) = 500 × 1.20 = ₹600

Q: SP = ₹360, loss = 10%. Find CP.
A: CP = 360 / (1 - 10/100) = 360 / 0.9 = ₹400

Q: MP = ₹500, discount 20%. SP = ?
A: SP = 500 × (1 - 20/100) = 500 × 0.80 = ₹400
```

### 2.3 Ratio & Proportion — PYQ Formula Sheet

```
RATIO: a:b = a/b
       Simplest form: divide by HCF

PROPORTION: a:b = c:d  (a:b :: c:d)
  → ad = bc  (cross product equal)
  → b = product of means = ad/c

TYPES OF PROPORTION:
  Direct Proportion:   y = kx  (y increases as x increases)
  Inverse Proportion:  y = k/x (y decreases as x increases)

COMPOUND RATIO: (a:b) and (c:d) → ac:bd
DUPLICATE RATIO: a:b → a²:b²
```

**Example Problems:**
```
Q: If 5 workers complete a task in 12 days, how many days
   for 6 workers? (Inverse proportion — more workers, fewer days)
A: Workers × Days = constant = 5 × 12 = 60
   6 × Days = 60 → Days = 10

Q: A:B = 3:5, B:C = 4:7. Find A:B:C.
A: A:B = 3:5, B:C = 4:7
   Make B common: A:B = 12:20, B:C = 20:35
   A:B:C = 12:20:35

Q: Divide ₹720 in ratio 3:4:5
A: Total parts = 12
   Share 1 = (3/12)×720 = 180
   Share 2 = (4/12)×720 = 240
   Share 3 = (5/12)×720 = 300
```

### 2.4 LCM & HCF — Core Methods

```
HCF (Highest Common Factor):
  = Largest number that DIVIDES all given numbers
  Methods: Prime factorization, Division method
  
LCM (Least Common Multiple):
  = Smallest number DIVISIBLE by all given numbers
  
KEY FORMULA:
  HCF × LCM = Product of two numbers
  (HCF × LCM = a × b)    ← for TWO numbers only

STEPS (Prime Factorization):
  HCF = Product of COMMON prime factors (lowest powers)
  LCM = Product of ALL prime factors (highest powers)

Example: HCF and LCM of 12 and 18
  12 = 2² × 3
  18 = 2 × 3²
  HCF = 2¹ × 3¹ = 6      (common factors, lowest powers)
  LCM = 2² × 3² = 36     (all factors, highest powers)
  Verify: 6 × 36 = 216 = 12 × 18 ✓
```

### 2.5 Average — Quick Methods

```
AVERAGE = Sum of all values / Number of values

WEIGHTED AVERAGE:
  WA = (w₁x₁ + w₂x₂ + ... ) / (w₁ + w₂ + ...)

KEY TRICKS:
  If average of n numbers = A, and one number is replaced:
  New sum = (n × A) - old number + new number
  New average = New sum / n
```

**Example:**
```
Q: Average of 5 numbers = 20. One number 14 is replaced by 34.
   New average?
A: Original sum = 5 × 20 = 100
   New sum = 100 - 14 + 34 = 120
   New average = 120/5 = 24
```

### 2.6 Work & Time

```
FORMULA:
  If A can do work in 'a' days → A's rate = 1/a per day
  If B can do work in 'b' days → B's rate = 1/b per day
  Together rate = 1/a + 1/b
  Together time = 1/(1/a + 1/b) = ab/(a+b)
```

**Example:**
```
Q: A completes work in 10 days, B in 15 days.
   Working together, how many days?
A: Together = (10×15)/(10+15) = 150/25 = 6 days

Q: A takes 6 days, B takes 12 days. B leaves 2 days before end.
   Total days taken?
A: Let total = T
   A works T days: T/6
   B works (T-2) days: (T-2)/12
   T/6 + (T-2)/12 = 1
   2T/12 + (T-2)/12 = 1
   (2T + T - 2)/12 = 1
   3T - 2 = 12 → 3T = 14 → T = 14/3 ≈ 4.67 days
```

### 2.7 Number System

```
TYPES OF NUMBERS:
  Natural Numbers: 1, 2, 3, 4, ... (positive, no zero)
  Whole Numbers:   0, 1, 2, 3, 4, ...
  Integers:        ...-2, -1, 0, 1, 2, 3, ...
  Rational:        p/q form (q≠0)
  Irrational:      √2, π, e (cannot be p/q)
  Real:            Rational + Irrational

DIVISIBILITY RULES:
  ÷ 2: Last digit even
  ÷ 3: Sum of digits divisible by 3
  ÷ 4: Last 2 digits divisible by 4
  ÷ 5: Last digit 0 or 5
  ÷ 6: Divisible by 2 AND 3
  ÷ 8: Last 3 digits divisible by 8
  ÷ 9: Sum of digits divisible by 9
  ÷ 11: |Sum of odd-position digits - Sum of even-position digits| = 0 or 11
```

---

## 🔶 SECTION 3: KEY SCIENCE FACTS (GS Revision — Bihar PYQ Focus)

```
PHYSICS (High-frequency BPSC PYQs):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
P = I²R  (Electrical Power formula)
Speed of electron in H orbit = c/137
Bernoulli's principle → Spray bottles (pressure drops as speed increases)
Stefan's law → E ∝ T⁴ (radiation proportional to 4th power of temp)
Frequency unchanged when light passes through different medium
Convex lens in water → still convex but focal length INCREASES

BIOLOGY (High-frequency BPSC PYQs):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Photoperiodism discovered by: Garner and Allard
Ginger = underground stem (has nodes and internodes)
Asexual reproduction by budding: Yeast
Lymphocytes = most important cells for IMMUNITY
Diaphragm during normal respiration: FLATTENED
Anther contains: POLLEN GRAINS
Antacid = medicine for indigestion (acid reflux)
Silent Valley = Kerala (rare biodiversity)
```

---

# 📝 PRACTICE QUESTIONS

---

# 🖥️ PART A — CS MCQs (25 Questions)

### Full DSA Grand Revision — All Topics
### BPSC 5-option format: D = More than one / E = None of the above
### Difficulty: Starts Easy → Hard → PYQ-Style → Tricky

---

**Q1.** What is the primary advantage of an array over a linked list?

(A) Dynamic size  
(B) Ease of insertion  
(C) Random access in O(1) time  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** Which of the following data structures follows LIFO principle?

(A) Queue  
(B) Stack  
(C) Circular Queue  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** Which of the following uses QUEUE as its underlying data structure?

(A) Recursion  
(B) Infix to Postfix conversion  
(C) BFS (Breadth-First Search)  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** The Circular Queue avoids which problem of the Linear Queue?

(A) Overflow  
(B) Memory wastage (unused front positions)  
(C) Underflow  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** In a Binary Search Tree (BST), which traversal gives elements in sorted order?

(A) Preorder  
(B) Postorder  
(C) Inorder  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** The number of distinct BSTs that can be formed using keys {1, 2, 3, 4} is:

(A) 12  
(B) 14  
(C) 16  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** Which of the following sorting algorithms guarantees O(n log n) in the WORST case?

(A) Quick Sort  
(B) Merge Sort  
(C) Bubble Sort  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** Binary Search requires which precondition on the array?

(A) Array must be in heap form  
(B) Array must be sorted  
(C) Array must store integers only  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** Which of the following is a correct statement about STACK?

(A) Recursion uses Stack  
(B) Stack is used in backtracking algorithms  
(C) Infix to Postfix conversion uses Stack  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** Convert (A + B) * C to Postfix. The correct answer is:

(A) A B C + *  
(B) A B + C *  
(C) + A B * C  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** In a Doubly Linked List, deleting the LAST node takes:

(A) O(n) because you must traverse to it  
(B) O(1) because the tail pointer gives direct access  
(C) O(log n) using binary search  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** A spanning tree of a graph with 8 vertices contains exactly how many edges?

(A) 8  
(B) 6  
(C) 7  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** Which of the following is NOT a valid binary tree traversal method?

(A) Preorder  
(B) Randomized traversal  
(C) Level-order  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Which of the following are Divide and Conquer algorithms?

(A) Merge Sort  
(B) Quick Sort  
(C) Binary Search  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** The worst case time complexity of Quick Sort is:

(A) O(n log n)  
(B) O(n)  
(C) O(n²)  
(D) More than one of the above  
(E) None of the above  

---

**Q16 (PYQ-Style).** Before inserting an element into a Queue, which condition must be checked?

(A) Underflow  
(B) Overflow  
(C) Priority  
(D) More than one of the above  
(E) None of the above  

---

**Q17 (PYQ-Style).** The Circular Queue is also called:

(A) Linear Buffer  
(B) Priority Queue  
(C) Ring Buffer  
(D) More than one of the above  
(E) None of the above  

---

**Q18 (PYQ-Style).** In a Red-Black Tree, which color is assigned to a new ROOT node?

(A) Red  
(B) Black  
(C) Either Red or Black depending on parent  
(D) More than one of the above  
(E) None of the above  

---

**Q19 (PYQ-Style).** Which sorting algorithm is both stable AND uses Divide and Conquer?

(A) Quick Sort  
(B) Heap Sort  
(C) Merge Sort  
(D) More than one of the above  
(E) None of the above  

---

**Q20 (PYQ-Style).** Regarding Hash Tables, which of the following is/are TRUE?

(A) Average search time is O(1)  
(B) Collisions are handled by chaining or open addressing  
(C) Load factor affects performance  
(D) More than one of the above  
(E) None of the above  

---

**Q21 (Hard).** Given a BST with Preorder traversal: 10, 5, 2, 8, 15, 12, 20
What is the Postorder traversal?

(A) 2, 8, 5, 12, 20, 15, 10  
(B) 2, 5, 8, 10, 12, 15, 20  
(C) 10, 15, 20, 5, 8, 2, 12  
(D) More than one of the above  
(E) None of the above  

---

**Q22 (Hard).** Which of the following correctly identifies stable sorting algorithms?

(A) Selection Sort and Heap Sort  
(B) Quick Sort and Merge Sort  
(C) Bubble Sort and Merge Sort  
(D) More than one of the above  
(E) None of the above  

---

**Q23 (Tricky).** Dijkstra's Shortest Path algorithm belongs to which complexity class?

(A) NP-Complete  
(B) NP-Hard  
(C) Class P (polynomial)  
(D) More than one of the above  
(E) None of the above  

---

**Q24 (Tricky).** Which of the following is TRUE about Merge Sort?

(A) It is NOT a stable sorting algorithm  
(B) It requires O(n) additional memory space  
(C) Its worst case time complexity is O(n²)  
(D) More than one of the above  
(E) None of the above  

---

**Q25 (Tricky).** The time complexity of converting Infix to Postfix using Stack is:

(A) O(n²)  
(B) O(log n)  
(C) O(n)  
(D) More than one of the above  
(E) None of the above  

---

# 🌍 PART B — GS/GK MCQs (25 Questions)

### Full GS Revision — Modern Indian History + Mathematics
### BPSC 5-option format
### Difficulty: Easy → Hard → PYQ-Style → Tricky

---

**Q26.** The Indian National Congress was founded in the year:

(A) 1882  
(B) 1885  
(C) 1890  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** Who was the FIRST President of the Indian National Congress?

(A) Dadabhai Naoroji  
(B) Gopal Krishna Gokhale  
(C) W.C. Bonnerjee  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** The Champaran Satyagraha of 1917 was Gandhi's first Satyagraha in India. Who invited Gandhi to Champaran?

(A) Jawaharlal Nehru  
(B) Rajkumar Shukla  
(C) Rajendra Prasad  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** The Quit India Movement was launched on:

(A) August 9, 1940  
(B) August 8–9, 1942  
(C) January 26, 1942  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** Who was the Viceroy of India during the Jallianwala Bagh massacre of 1919?

(A) Lord Curzon  
(B) Lord Irwin  
(C) Lord Chelmsford  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** Ghadar Party was established in which country?

(A) United Kingdom  
(B) Canada  
(C) United States of America  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** Who first called the Revolt of 1857 as "First War of Indian Independence"?

(A) Bal Gangadhar Tilak  
(B) Jawaharlal Nehru  
(C) V.D. Savarkar  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** The Brahmo Samaj was founded by:

(A) Dayananda Saraswati  
(B) Swami Vivekananda  
(C) Raja Ram Mohan Roy  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** INC Gaya Session (1922) was presided over by:

(A) Motilal Nehru  
(B) Chittaranjan Das  
(C) Gopal Krishna Gokhale  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** A trader buys a product for ₹800 and sells it at 25% profit. What is the Selling Price?

(A) ₹900  
(B) ₹1000  
(C) ₹1200  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** If 15% of a number is 45, what is the number?

(A) 200  
(B) 250  
(C) 300  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** The HCF of 36 and 48 is:

(A) 6  
(B) 12  
(C) 18  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** The LCM of 8, 12, and 20 is:

(A) 60  
(B) 90  
(C) 120  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** A can complete a work in 12 days, B in 18 days. Working together, they will finish in:

(A) 6.4 days  
(B) 7.2 days  
(C) 8 days  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** The average of five numbers is 30. If one number is 10, the average of the remaining four is:

(A) 32.5  
(B) 35  
(C) 37.5  
(D) More than one of the above  
(E) None of the above  

---

**Q41 (PYQ-Style).** Which of the following is associated with the discovery of photoperiodism?

(A) Watson and Crick  
(B) Darwin and Wallace  
(C) Garner and Allard  
(D) More than one of the above  
(E) None of the above  

---

**Q42 (PYQ-Style).** The electrical power formula is:

(A) P = V/I  
(B) P = I²R  
(C) P = R²I  
(D) More than one of the above  
(E) None of the above  

---

**Q43 (PYQ-Style).** Ginger is an example of:

(A) Aerial root  
(B) Modified leaf  
(C) Underground stem (having nodes and internodes)  
(D) More than one of the above  
(E) None of the above  

---

**Q44 (PYQ-Style).** Abhinav Bharat was founded by V.D. Savarkar in which city?

(A) Paris  
(B) London  
(C) Pune  
(D) More than one of the above  
(E) None of the above  

---

**Q45 (PYQ-Style).** The Non-Cooperation Movement was withdrawn after which incident?

(A) Jallianwala Bagh  
(B) Bardoli Satyagraha  
(C) Chauri Chaura  
(D) More than one of the above  
(E) None of the above  

---

**Q46 (Hard).** Swami Sahajanand Saraswati was associated with which organization in Bihar in 1936?

(A) Bihar Provincial Congress Committee  
(B) All India Kisan Sabha (AIKS)  
(C) Bihar Socialist Party  
(D) More than one of the above  
(E) None of the above  

---

**Q47 (Hard).** If A:B = 2:3 and B:C = 4:5, then A:B:C equals:

(A) 8:12:15  
(B) 2:3:5  
(C) 4:6:10  
(D) More than one of the above  
(E) None of the above  

---

**Q48 (Hard).** A product is marked at ₹1000. A 20% discount is given, then a further 10% discount. What is the final price?

(A) ₹700  
(B) ₹720  
(C) ₹750  
(D) More than one of the above  
(E) None of the above  

---

**Q49 (Tricky).** Bihar Provincial Congress Committee was founded in which year?

(A) 1885  
(B) 1905  
(C) 1908  
(D) More than one of the above  
(E) None of the above  

---

**Q50 (Tricky).** During normal (quiet) respiration, the diaphragm:

(A) Moves upward and becomes dome-shaped  
(B) Flattens and moves downward  
(C) Does not move at all  
(D) More than one of the above  
(E) None of the above  

---

---

# ✅ ANSWER KEY

> **🛑 STOP — Have you attempted ALL 50 questions on your own first? Only then scroll down!**

---

## CS Answers (Q1–Q25)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q1 | **(C)** | Random access O(1) is the main advantage of arrays over linked lists |
| Q2 | **(B)** | Stack = LIFO. Queue/Circular Queue = FIFO |
| Q3 | **(C)** | BFS uses Queue. Recursion and Infix-Postfix use Stack |
| Q4 | **(B)** | Circular Queue eliminates memory wastage of unused front positions in linear queue |
| Q5 | **(C)** | Inorder traversal of BST = elements in sorted (ascending) order |
| Q6 | **(B)** | C(4) = 14 distinct BSTs (Catalan number formula) |
| Q7 | **(B)** | Merge Sort = O(n log n) in ALL cases. Quick Sort = O(n²) worst case |
| Q8 | **(B)** | Binary Search requires SORTED array — non-negotiable requirement |
| Q9 | **(D)** | ALL three are correct: recursion, backtracking, and infix-postfix ALL use Stack |
| Q10 | **(B)** | (A+B)*C → A B + C * (bracket first: A+B = AB+, then *C) |
| Q11 | **(B)** | Doubly LL with tail pointer: delete last = O(1) using prev pointer |
| Q12 | **(C)** | Spanning tree: N vertices → **N-1 edges** → 8 vertices → 7 edges |
| Q13 | **(B)** | "Randomized traversal" DOES NOT EXIST — classic PYQ trap |
| Q14 | **(D)** | Merge Sort, Quick Sort, AND Binary Search are ALL Divide and Conquer |
| Q15 | **(C)** | Quick Sort worst = O(n²) when pivot is always min/max (sorted array) |
| Q16 | **(B)** | Before INSERT into Queue → check OVERFLOW (isFull) |
| Q17 | **(C)** | Circular Queue = Ring Buffer (PYQ repeated TRE 1.0 + 2.0) |
| Q18 | **(B)** | Red-Black tree: new ROOT = BLACK. New non-root = RED |
| Q19 | **(C)** | Merge Sort = Stable + Divide and Conquer. Quick Sort = D&C but UNSTABLE |
| Q20 | **(D)** | All three are true about Hash Tables — O(1) avg, collision handling, load factor matters |
| Q21 | **(A)** | Build BST from Preorder 10,5,2,8,15,12,20 → Postorder = 2,8,5,12,20,15,10 |
| Q22 | **(C)** | Bubble Sort (stable) and Merge Sort (stable) are BOTH stable sorting algorithms |
| Q23 | **(C)** | Dijkstra's = Polynomial (P class). Shortest Path ≠ NP-Complete — very common trap! |
| Q24 | **(B)** | Merge Sort IS stable (A wrong), needs O(n) extra space (B correct), worst = O(n log n) not O(n²) |
| Q25 | **(C)** | Infix → Postfix conversion time = O(n) (processes each character once) |

---

## GS Answers (Q26–Q50)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q26 | **(B)** | INC founded **1885** by A.O. Hume in Bombay |
| Q27 | **(C)** | W.C. Bonnerjee = first INC President (1885 Bombay session) |
| Q28 | **(B)** | **Rajkumar Shukla** (indigo farmer) persuaded Gandhi to come to Champaran |
| Q29 | **(B)** | Quit India Movement = **August 8-9, 1942** at Gowalia Tank, Bombay |
| Q30 | **(C)** | **Lord Chelmsford** = Viceroy during Jallianwala Bagh (April 13, 1919) |
| Q31 | **(C)** | Ghadar Party = **USA** (San Francisco, 1913) by Lala Hardayal |
| Q32 | **(C)** | **V.D. Savarkar** first called 1857 revolt "First War of Indian Independence" |
| Q33 | **(C)** | Brahmo Samaj (1828) = **Raja Ram Mohan Roy**. Arya Samaj = Dayananda |
| Q34 | **(B)** | INC Gaya Session 1922 = President **Chittaranjan Das** |
| Q35 | **(B)** | SP = 800 × 1.25 = **₹1000** |
| Q36 | **(C)** | 15% of N = 45 → N = 45 × 100/15 = **300** |
| Q37 | **(B)** | HCF(36,48): 36=2²×3², 48=2⁴×3 → HCF = 2²×3 = **12** |
| Q38 | **(C)** | LCM(8,12,20): 8=2³, 12=2²×3, 20=2²×5 → LCM = 2³×3×5 = **120** |
| Q39 | **(B)** | Together = (12×18)/(12+18) = 216/30 = **7.2 days** |
| Q40 | **(A)** | Sum = 5×30 = 150; Remaining sum = 150-10 = 140; Avg = 140/4 = **35**... wait: Q asks for avg of remaining 4 = 140/4 = 35. Answer = **(B) 35** |
| Q41 | **(C)** | Photoperiodism discovered by **Garner and Allard** (1920) |
| Q42 | **(B)** | Electrical power = **P = I²R** (also P=VI, P=V²/R, but I²R is most tested) |
| Q43 | **(C)** | Ginger = **underground stem** (rhizome) with nodes and internodes |
| Q44 | **(B)** | Abhinav Bharat founded by V.D. Savarkar in **London** (1906) |
| Q45 | **(C)** | Non-Cooperation Movement withdrawn after **Chauri Chaura** (Feb 1922) |
| Q46 | **(B)** | Swami Sahajanand Saraswati = **All India Kisan Sabha (AIKS)** Bihar 1936 |
| Q47 | **(A)** | A:B=2:3, B:C=4:5. Multiply: A:B=8:12, B:C=12:15. So A:B:C = **8:12:15** |
| Q48 | **(B)** | 1st discount: 1000×0.8=800; 2nd discount: 800×0.9=**₹720** |
| Q49 | **(C)** | Bihar Provincial Congress Committee founded **1908** |
| Q50 | **(B)** | During normal inhalation, diaphragm **flattens and moves downward** (increases chest volume) |

> **Note for Q40:** Answer is **(B) 35** — Sum of 5 = 150, remove 10, remaining 4 sum = 140, avg = 140/4 = 35.

---

# 🌟 TOPPER'S NIGHT REVISION — Day 35 (Write from Memory!)

## ⚡ CS Grand Checklist (Write BEFORE Sleep)

```
Write these 10 lines from MEMORY:
1. LIFO = _____ | FIFO = _____
2. Recursion uses _____ internally
3. BFS uses _____ | DFS uses _____
4. Circular Queue empty condition: _____
5. Circular Queue also called: _____
6. C(4) Catalan = _____
7. Red-Black new root color = _____
8. Inorder of BST = _____
9. Merge Sort worst case = _____ | Quick Sort worst case = _____
10. Spanning tree N vertices = _____ edges
```

## ⚡ GS Grand Checklist

```
Write these from MEMORY:
1. INC founded year = _____ | By = _____
2. First INC President = _____
3. Champaran Satyagraha year = _____ | Who invited Gandhi = _____
4. Quit India Movement date = _____ | Slogan = _____
5. Viceroy during Jallianwala Bagh = _____
6. Ghadar Party country = _____
7. V.D. Savarkar = called 1857 _____
8. Brahmo Samaj founder = _____
9. P = I²R means → _____
10. Ginger is a _____ (type of stem)
```

---

## 📌 THE 20 BIGGEST DSA TRAPS — Final Reminder

```
TRAP → CORRECT ANSWER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Recursion uses Queue         → STACK
BFS uses Stack               → QUEUE
Circular Queue = Priority Q  → RING BUFFER
C(4) = 12                    → 14
Inorder of BST = random      → SORTED ORDER
Red-Black new node = Red     → Root = BLACK; Non-root = Red
"Randomized traversal" exists→ DOES NOT EXIST
Quick Sort = always O(n log n)→ WORST = O(n²)
Merge Sort = in-place         → NOT in-place; O(n) space
Merge Sort = unstable         → STABLE
Heap Sort = stable            → UNSTABLE
Selection Sort = stable       → UNSTABLE
Insertion Sort = unstable     → STABLE
Asynchronous transfer = Stack → QUEUE
Spanning tree = N edges       → N-1 edges
Hash Table = O(n) search      → O(1) average
Linear probe = always O(1)    → O(n) worst
Binary Search on unsorted     → REQUIRES SORTED
Shortest Path = NP-Complete   → CLASS P (polynomial)
Hamiltonian Cycle = P         → NP-COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

> **🏆 WEEK 5 COMPLETE! You have mastered:**
> Phase 1 → Week 5 = DONE ✅
> Topics covered: Arrays, Stacks, Queues, Linked Lists, Trees, BST, Graphs, Sorting, Searching, Hashing, Complexity, NP-Complete, Algorithm Paradigms
>
> **📅 Tomorrow → Day 36 (Week 6 begins):** DBMS Introduction + GS: History — Ghadar Party, Abhinav Bharat
> Get ready for a new chapter — DBMS is worth 12% of the CS paper!

---
*BPSC TRE 4.0 | Phase 1 — Week 5 COMPLETE | Day 35 of 170*
*DSA Chapters Covered: Day 15–35 | Total MCQs Practiced Today: 50*
