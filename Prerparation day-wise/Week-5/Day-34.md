# 📅 DAY-34 — BPSC TRE 4.0 STUDY FILE
## CS: DSA Full PYQ Special (All Topics) | GS: Bihar GK — Geography
### 🎯 Target: TOPPER RANK | Phase 1 → Week 5

---

> **📌 TODAY'S BATTLE PLAN**
> - **Morning (1.5 hrs):** CS — Deep revision of ALL DSA topics with PYQ-focused theory
>   Focus areas: Catalan numbers, Circular Queue, Infix/Postfix, BST, Linked Lists, Sorting, Hashing
> - **Afternoon (1 hr):** GS — Bihar Geography: Physical features, Rivers, Districts, National Parks, Climate
> - **Evening (1 hr):** Solve all 50 MCQs from this file (attempt BEFORE checking answers)
> - **Night (30 min):** Write 5-bullet summary from memory — NEVER SKIP THIS

---

> ⚡ **WHY TODAY IS SPECIAL:** Day-34 is a PYQ Special — every concept here has directly appeared in TRE 1.0, TRE 2.0, or TRE 3.0. This day separates toppers from average candidates.

---

# 🖥️ PART A: COMPUTER SCIENCE — DSA FULL PYQ SPECIAL

## All DSA Topics: Deep Revision with PYQ Focus

---

## 🔷 MODULE 1: STACK — Complete Revision

### 1.1 What is a Stack?

```
STACK = LIFO (Last In, First Out)
        Like a stack of plates — you add and remove from TOP only
```

**ASCII Diagram:**
```
        |   |  ← TOP of stack
        | 30|  ← Last pushed, first to be popped
        | 20|
        | 10|  ← First pushed, last to be popped
        |___|
        
PUSH 40:         POP:
        | 40|         |   |  ← 40 is removed
        | 30|         | 30|
        | 20|         | 20|
        | 10|         | 10|
        |___|         |___|
```

### 1.2 Stack Operations — Time Complexity

| Operation | Time Complexity | Description |
|-----------|-----------------|-------------|
| Push | O(1) | Add element at top |
| Pop | O(1) | Remove element from top |
| Peek/Top | O(1) | View top element without removing |
| isEmpty | O(1) | Check if stack is empty |
| isFull | O(1) | Check if stack is full (array-based) |
| Search | O(n) | Search for an element |

### 1.3 Stack — OVERFLOW and UNDERFLOW

```
OVERFLOW  = Push when stack is FULL
             Condition: top == MAX_SIZE - 1
             
UNDERFLOW = Pop when stack is EMPTY
             Condition: top == -1
```

> ⚠️ **PYQ TRAP:** Before PUSH → check OVERFLOW. Before POP → check UNDERFLOW.

### 1.4 Stack Applications — THE MOST TESTED TOPIC

**✅ CORRECT Stack Applications (These ARE stack applications):**
1. **String Reversal** — push all chars, pop to reverse
2. **Expression Evaluation** — evaluate postfix expressions
3. **Infix → Postfix/Prefix conversion** — uses stack
4. **Balancing of Parentheses/Symbols** — uses stack
5. **Recursion** — function call stack (system stack)
6. **Backtracking** — maze solving, game trees
7. **Browser back button** — history stored as stack
8. **Undo operation** — in text editors

**❌ NOT a Stack Application:**
- Asynchronous data transfer → uses **QUEUE**
- CPU Scheduling → uses **QUEUE**
- Printer spooling → uses **QUEUE**
- BFS (Breadth-First Search) → uses **QUEUE**

> ⚠️ **PYQ FACT (TRE 1.0 + 2.0 repeated):** "Which is NOT an application of Stack?"
> Answer → Asynchronous data transfer (uses Queue, not Stack)

> ⚠️ **PYQ FACT (TRE 1.0 + 2.0):** "Recursion uses which data structure internally?"
> Answer → **STACK** (function call stack)

---

## 🔷 MODULE 2: INFIX / POSTFIX / PREFIX — Conversion

### 2.1 Notation Types

```
INFIX:   A + B         (operator BETWEEN operands) — human-readable
POSTFIX: A B +         (operator AFTER operands)  — Reverse Polish
PREFIX:  + A B         (operator BEFORE operands) — Polish Notation
```

### 2.2 Why Convert? (PYQ Context)

- Computers evaluate **Postfix** expressions more efficiently (no parentheses needed, no precedence rules)
- Conversion uses **STACK**
- Time complexity of conversion: **O(N)**

### 2.3 Operator Precedence (For Conversion — MUST KNOW)

```
PRECEDENCE (High to Low):
  ^   (Exponentiation) — Highest
  * / (Multiplication, Division)
  + - (Addition, Subtraction) — Lowest
  
Associativity:
  ^   → Right to Left
  * / → Left to Right
  + - → Left to Right
```

### 2.4 Infix to Postfix — Step-by-Step Algorithm

```
Algorithm:
  1. Create empty stack and result string
  2. Scan infix expression left to right:
     a. If operand (A,B,C...) → add to result directly
     b. If '(' → push to stack
     c. If ')' → pop and add to result until '(' is found; discard '('
     d. If operator:
        - While stack not empty AND top has >= precedence:
          pop and add to result
        - Push current operator
  3. Pop remaining stack elements to result
```

### 2.5 Worked Example — Practice These! (PYQ Type)

**Example 1:** Convert A + B * C - D to Postfix

```
Expression: A + B * C - D

Step | Symbol | Stack   | Result
-----|--------|---------|--------
1    | A      | empty   | A
2    | +      | +       | A
3    | B      | +       | AB
4    | *      | + *     | AB         (* has higher precedence than +)
5    | C      | + *     | ABC
6    | -      | -       | ABC*+      (- <= +, so pop +; - <= *, so pop *; push -)
7    | D      | -       | ABC*+D
End  | (pop)  | empty   | ABC*+D-

Postfix: A B C * + D -
```

**Example 2:** Convert (A + B) * C to Postfix

```
Step | Symbol | Stack   | Result
-----|--------|---------|--------
1    | (      | (       | 
2    | A      | (       | A
3    | +      | ( +     | A
4    | B      | ( +     | AB
5    | )      | empty   | AB+        (pop until '(', add '+', discard '(')
6    | *      | *       | AB+
7    | C      | *       | AB+C
End  | (pop)  | empty   | AB+C*

Postfix: A B + C *
```

> ⭐ **PYQ KEY FACT:** Infix to Postfix time complexity = **O(N)**. Uses STACK.

---

## 🔷 MODULE 3: QUEUE — Complete Revision

### 3.1 Queue = FIFO

```
QUEUE = FIFO (First In, First Out)
        Like a line at ticket counter — first person in line is served first

FRONT (Deletion end)          REAR (Insertion end)
     ↓                              ↓
  [10] [20] [30] [40] [50]
   ↑                    ↑
First in               Last in (will be last out)
```

### 3.2 Queue Operations

| Operation | Action | Check Before |
|-----------|--------|-------------|
| Enqueue (Insert) | Add at REAR | Check **OVERFLOW** (isFull) |
| Dequeue (Delete) | Remove from FRONT | Check **UNDERFLOW** (isEmpty) |

> ⚠️ **PYQ KEY (Repeated TRE 1.0 + 2.0):**
> Before deletion from Queue → check **UNDERFLOW**
> Before insertion into Queue → check **OVERFLOW**

### 3.3 Linear Queue Overflow Problem

```
LINEAR QUEUE PROBLEM:
  Even when elements are dequeued from front,
  that space CANNOT be reused.
  
  [  ] [  ] [30] [40] [50]
   ↑              ↑    ↑
  Wasted!        front  rear
  
  When rear = MAX_SIZE - 1, we get "overflow"
  even though front slots are empty!
  
SOLUTION: CIRCULAR QUEUE
```

### 3.4 Circular Queue — THE MOST TESTED QUEUE TOPIC

```
CIRCULAR QUEUE:
  Last position connects back to first position
  Forms a RING → Also called RING BUFFER
  
  [50] [  ] [  ] [30] [40]
    ↑                    ↑
   rear               front
  
  Advantages: No memory wastage (reuses freed positions)
```

**Circular Queue Conditions:**

```
EMPTY CONDITION:  front = rear = -1
                  OR front == (rear + 1) % SIZE

FULL CONDITION:   (rear + 1) % SIZE == front

Insert (Enqueue): rear = (rear + 1) % SIZE
Delete (Dequeue): front = (front + 1) % SIZE
```

> ⭐ **PYQ FACT (TRE 1.0 + 2.0 REPEATED):**
> - Circular Queue = **Ring Buffer**
> - Empty condition: **front = rear = -1**
> - Created to solve: **Memory wastage in linear queue**

### 3.5 Deque (Double-Ended Queue)

```
DEQUE = Insert and Delete from BOTH ends

  Front end ← [10] [20] [30] [40] → Rear end
  Insert/Delete               Insert/Delete
  
Types:
  Input-restricted Deque:  Insert only at ONE end (Rear)
  Output-restricted Deque: Delete only from ONE end (Front)
```

> ⚠️ **PYQ TRAP:** Delete from REAR in Deque with SINGLY Linked List = **O(N)**
> (You need to traverse to find second-to-last node)
> With DOUBLY Linked List = **O(1)**

### 3.6 Priority Queue

```
PRIORITY QUEUE: Elements served based on PRIORITY, not order of arrival

Best implementation: BINARY HEAP
  Min-Heap: Smallest element has highest priority (served first)
  Max-Heap: Largest element has highest priority (served first)
  
Applications:
  - Dijkstra's algorithm
  - Huffman Coding
  - CPU scheduling (Priority scheduling)
  - A* search algorithm
```

> ⭐ **PYQ FACT:** Priority Queue best implemented with **Binary Heap**.

---

## 🔷 MODULE 4: LINKED LIST — Complete Revision

### 4.1 Types of Linked Lists

```
SINGLY LINKED LIST:
  [Data|Next] → [Data|Next] → [Data|Next] → NULL
   Node 1         Node 2         Node 3
   
DOUBLY LINKED LIST:
  NULL ← [Prev|Data|Next] ↔ [Prev|Data|Next] ↔ [Prev|Data|Next] → NULL
  
CIRCULAR LINKED LIST:
  [Data|Next] → [Data|Next] → [Data|Next] → (back to first node)
```

### 4.2 Operations Comparison

| Operation | Singly LL | Doubly LL | Array |
|-----------|-----------|-----------|-------|
| Access by index | O(n) | O(n) | **O(1)** |
| Insert at beginning | O(1) | O(1) | O(n) |
| Insert at end | O(n) | O(1) with tail | O(1) amortized |
| Delete at beginning | O(1) | O(1) | O(n) |
| Delete at end | O(n) | **O(1)** with tail | O(1) |
| Search | O(n) | O(n) | O(n) |

### 4.3 Key Facts — PYQ Focus

> ⭐ **PYQ FACTS:**
> 1. Linked List = **NO random access** (no index-based O(1) access like arrays)
> 2. Doubly LL is **HARDER to implement** than Singly LL (more pointers to manage)
> 3. Advantage of Linked List over Array = **Dynamic size** (grows/shrinks at runtime)
> 4. Disadvantage = **Extra memory** for pointer field + no random access
> 5. Circular LL last node points **back to FIRST node** (not to NULL)

---

## 🔷 MODULE 5: TREES — Complete Revision

### 5.1 Tree Terminology — Must Know All

```
           A          ← ROOT (no parent)
          / \
         B   C        ← Level 1
        / \   \
       D   E   F      ← Level 2 (D, E, F)
      /
     G                ← Level 3

ROOT = A
LEAVES = D (no, has child G), E, F, G (nodes with no children)
Wait — corrected:
LEAVES = E, F, G  (nodes with no children)
PARENT of D = B
CHILDREN of B = D, E
HEIGHT of tree = 3 (levels 0,1,2,3 = 4 levels, height=3)
DEGREE of B = 2 (has 2 children)
```

**Key Terms:**
| Term | Definition |
|------|-----------|
| Root | Topmost node; has no parent |
| Leaf | Node with no children (degree = 0) |
| Height | Length of longest path from root to leaf |
| Depth | Length of path from root to that node |
| Degree | Number of children a node has |
| Level | Root is at Level 0 (or Level 1 in some books) |

### 5.2 Types of Binary Trees

```
FULL BINARY TREE:
  Every node has 0 or 2 children (never 1 child)
  
       A
      / \
     B   C
    / \
   D   E

COMPLETE BINARY TREE:
  All levels fully filled EXCEPT possibly last level
  Last level filled from LEFT to RIGHT
  
       A
      / \
     B   C
    / \  /
   D   E F

PERFECT BINARY TREE:
  All internal nodes have 2 children AND all leaves at same level
  
       A
      / \
     B   C
    / \ / \
   D  E F  G

BALANCED BINARY TREE:
  Height difference between left & right subtree ≤ 1 for every node
  (AVL Tree is an example)
```

### 5.3 Tree Traversals — THE #1 EXAM TOPIC

```
Three main traversals:

PREORDER  (Root → Left → Right):
  Visit root FIRST, then left subtree, then right subtree
  
INORDER   (Left → Root → Right):
  Visit left subtree FIRST, then root, then right subtree
  NOTE: For BST, Inorder gives SORTED output! ⭐
  
POSTORDER (Left → Right → Root):
  Visit left and right subtrees FIRST, then root
  Used for: Deleting tree, evaluating expression trees

LEVEL ORDER (BFS — Level by Level):
  Uses QUEUE to traverse level by level
```

**Worked Example:**
```
        1
       / \
      2   3
     / \   \
    4   5   6

PREORDER:    1, 2, 4, 5, 3, 6
INORDER:     4, 2, 5, 1, 3, 6
POSTORDER:   4, 5, 2, 6, 3, 1
LEVEL ORDER: 1, 2, 3, 4, 5, 6
```

> ⭐ **PYQ FACT (Repeated ALL 3 papers):** 
> "Randomized Traversal" = **DOES NOT EXIST**
> Valid traversals: Preorder, Inorder, Postorder, Level-order ONLY

> ⭐ **PYQ FACT:** Inorder traversal of BST = **Sorted order** (ascending)

---

## 🔷 MODULE 6: BINARY SEARCH TREE (BST) — Complete Revision

### 6.1 BST Property — ALL THREE MUST HOLD

```
BST RULE:
  1. Left child < Parent node (for ALL nodes in left subtree)
  2. Right child > Parent node (for ALL nodes in right subtree)
  3. BOTH left and right subtrees are also BSTs (recursive property)

Example:
        8
       / \
      3   10
     / \    \
    1   6    14
       / \   /
      4   7 13

Check: 1 < 3 ✓, 6 > 3 ✓, 4 < 6 ✓, 7 > 6 ✓
       3 < 8 ✓, 10 > 8 ✓, 14 > 10 ✓, 13 < 14 ✓
```

### 6.2 BST Operations

| Operation | Average Case | Worst Case (Skewed) |
|-----------|-------------|---------------------|
| Search | O(log n) | O(n) |
| Insert | O(log n) | O(n) |
| Delete | O(log n) | O(n) |

**Skewed BST:** When all nodes go to one side (like a linked list) → height = n → all operations become O(n).

### 6.3 Catalan Numbers — C(n) = Number of Distinct BSTs

**This is a DIRECT PYQ question — know the formula AND the value for n=4!**

```
Formula: C(n) = (2n)! / ((n+1)! × n!)

Values:
  C(0) = 1
  C(1) = 1
  C(2) = 2
  C(3) = 5
  C(4) = 14  ← MOST ASKED IN BPSC!
  C(5) = 42

For n=4 keys: C(4) = (8)! / (5! × 4!) = 40320 / (120 × 24) = 40320 / 2880 = 14
```

> ⭐ **PYQ DIRECT QUESTION:** "How many distinct BSTs can be formed from 4 keys?"
> Answer = **14** (Catalan number C(4))

### 6.4 Red-Black Tree (Self-Balancing BST)

**Properties:**
```
1. Every node is RED or BLACK
2. Root is always BLACK
3. Every leaf (NULL) is BLACK
4. If a node is RED → both its children are BLACK
5. All paths from any node to its leaf-descendants have equal BLACK nodes

KEY RULE FOR PYQ:
  New ROOT node = BLACK
  New non-root node = RED
```

> ⭐ **PYQ FACT (TRE 2.0):** In a Red-Black Tree: new root = BLACK, new non-root = RED

---

## 🔷 MODULE 7: SORTING ALGORITHMS — Full Comparison

### 7.1 Complete Sorting Algorithms Table

| Algorithm | Best | Average | Worst | Space | Stable | Paradigm |
|-----------|------|---------|-------|-------|--------|----------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) | ✅ Yes | Comparison |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) | ❌ No | Comparison |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) | ✅ Yes | Comparison |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ Yes | **D&C** |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) | ❌ No | **D&C** |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) | ❌ No | Binary Heap |
| Radix Sort | O(nk) | O(nk) | O(nk) | O(n+k) | ✅ Yes | Non-comparison |
| Counting Sort | O(n+k) | O(n+k) | O(n+k) | O(k) | ✅ Yes | Non-comparison |

### 7.2 Key Facts for PYQ

> ⭐ **MUST KNOW:**
> 1. **Merge Sort** = O(n log n) in **ALL** cases — guaranteed!
> 2. **Quick Sort** = O(n²) in **WORST** case (when pivot is always min/max)
> 3. **Bubble Sort** = **O(n) best case** (already sorted — with optimization)
> 4. **Selection Sort** = O(n²) **ALWAYS** (no optimization possible)
> 5. **Radix Sort** = **Non-comparison** based → can be O(n)
> 6. Both Merge Sort and Quick Sort use **Divide and Conquer**
> 7. Merge Sort = **NOT in-place** (needs O(n) extra space)
> 8. Heap Sort = **In-place** (O(1) extra space)

```
STABLE vs UNSTABLE:
  STABLE: Equal elements maintain their relative order
  Stable = Bubble, Insertion, Merge, Counting, Radix
  Unstable = Selection, Quick, Heap
  
  Memory trick: "Big Isles Make Countries Rich"
  Bubble, Insertion, Merge, Counting, Radix = Stable
```

---

## 🔷 MODULE 8: SEARCHING & HASHING

### 8.1 Searching Algorithms

| Algorithm | Time Complexity | Requirement | Space |
|-----------|-----------------|-------------|-------|
| Linear Search | O(n) | Works on unsorted | O(1) |
| Binary Search | O(log n) | **MUST be sorted** | O(1) |
| Jump Search | O(√n) | Must be sorted | O(1) |

### 8.2 Binary Search — Step-by-Step

```
Array: [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
       Index: 0  1  2   3   4   5   6   7   8   9
Search for: 23

Step 1: low=0, high=9, mid = (0+9)/2 = 4
        arr[4] = 16 < 23 → search RIGHT half
        
Step 2: low=5, high=9, mid = (5+9)/2 = 7
        arr[7] = 56 > 23 → search LEFT half
        
Step 3: low=5, high=6, mid = (5+6)/2 = 5
        arr[5] = 23 = target → FOUND at index 5!
        
Number of comparisons: 3 = log₂(10) ≈ 3.32 → O(log n) ✓
```

> ⭐ **PYQ FACT:** Binary search requires **SORTED array**. Time = O(log N).

### 8.3 Hashing — Key Concepts

```
HASH TABLE:
  Key → Hash Function → Index → Value stored here
  
  Example:
  Key = "John"
  Hash(John) = sum of ASCII values % table_size = index
  Store value at that index → O(1) access!

COLLISION: Two keys map to same index
  
Collision Resolution:
  1. Chaining: Each index has a linked list of all colliding elements
  2. Open Addressing:
     - Linear Probing: Try next index (index+1, index+2...)
     - Quadratic Probing: Try index+1², index+2², index+3²...
     - Double Hashing: Use second hash function
     
LOAD FACTOR = n/m (n = elements, m = table size)
  Low load factor → fewer collisions → faster
```

> ⭐ **PYQ FACT:** Hash Table provides **O(1) average** time for search, insert, delete. Best data structure for frequent operations on large datasets.

---

## 🔷 MODULE 9: GRAPHS — Key Facts

### 9.1 Graph Basics

```
GRAPH = V (vertices/nodes) + E (edges)

DIRECTED GRAPH (Digraph): Edges have direction A → B
UNDIRECTED GRAPH: Edges have no direction A — B

REPRESENTATIONS:
1. Adjacency Matrix: V×V matrix (1 if edge, 0 if not)
   Space: O(V²)
   
2. Adjacency List: Each vertex has list of its neighbors
   Space: O(V + E)
   Better for sparse graphs
```

### 9.2 Graph Traversals — BFS and DFS

```
BFS (Breadth-First Search):
  Uses: QUEUE
  Explores: Level by level (all neighbors first)
  Application: Shortest path in UNWEIGHTED graph
  Time: O(V + E)

DFS (Depth-First Search):
  Uses: STACK (or recursion)
  Explores: Goes deep first
  Application: Cycle detection, Topological sort, SCC
  Time: O(V + E)
```

> ⭐ **PYQ FACT:** 
> BFS uses **QUEUE** | DFS uses **STACK**
> Greedy/DP/D&C = algorithm **PARADIGMS**, NOT graph traversals

### 9.3 Spanning Tree

```
SPANNING TREE:
  A tree that includes ALL vertices of the graph
  with MINIMUM edges (no cycles)
  
  If graph has N vertices:
  Spanning tree has exactly N-1 edges

MINIMUM SPANNING TREE (MST):
  Spanning tree with minimum total edge weight
  Algorithms: Kruskal's (Greedy) and Prim's (Greedy)
```

> ⭐ **PYQ FACT:** Spanning tree with N vertices always has exactly **N-1 edges**.

---

## 🔷 MODULE 10: BIG-O AND COMPLEXITY — Quick Reference

### Common Complexity Values — MUST MEMORIZE

```
OPERATION                    | TIME COMPLEXITY
-----------------------------|------------------
Array access by index        | O(1)
Stack push/pop               | O(1)
Queue enqueue/dequeue        | O(1)
Hash table search (avg)      | O(1)
Binary Search                | O(log n)
Infix to Postfix conversion  | O(n)
Linear Search                | O(n)
Insertion in Linked List     | O(n) at end, O(1) at start
BST search (average)         | O(log n)
BST search (worst/skewed)    | O(n)
Merge Sort                   | O(n log n) — all cases
Quick Sort                   | O(n log n) avg, O(n²) worst
Bubble/Selection/Insertion   | O(n²) worst
Matrix Multiplication (naive)| O(n³)
Floyd-Warshall               | O(V³)
BFS/DFS                      | O(V + E)
```

> ⭐ **PYQ DIRECT:** Big-O represents the **UPPER BOUND** (worst case) of an algorithm.
> Big-Ω = lower bound | Big-Θ = tight bound

---

## 🔷 QUICK FIRE REVISION — ALL DSA TRAPS

```
TRAP SHEET — Memorize before the exam:

1. Recursion uses → STACK
2. BFS uses → QUEUE
3. DFS uses → STACK
4. Infix to Postfix uses → STACK, Time = O(N)
5. Circular Queue empty → front = rear = -1
6. Circular Queue full → (rear + 1) % SIZE == front
7. Circular Queue also called → RING BUFFER
8. Delete from REAR of singly LL Deque → O(N) NOT O(1)
9. BST Inorder traversal → SORTED output
10. C(4) Catalan number → 14 distinct BSTs
11. Red-Black tree new root → BLACK
12. Red-Black tree new non-root → RED
13. Spanning tree N vertices → N-1 edges
14. "Randomized Traversal" → DOES NOT EXIST
15. Priority Queue best implemented → Binary HEAP
16. Merge Sort → STABLE, D&C, NOT in-place
17. Quick Sort → UNSTABLE, D&C, IN-PLACE
18. Binary Search → requires SORTED array
19. Hash Table → O(1) average search
20. Doubly LL → HARDER to implement than Singly LL
```

---

# 🌍 PART B: GENERAL STUDIES — BIHAR GEOGRAPHY

---

## 🔶 SECTION 1: Bihar — Physical Geography

### 1.1 Location and Boundaries

```
BIHAR — LOCATION:
  Latitude:  24°20'N to 27°31'N
  Longitude: 83°19'E to 88°17'E
  
BOUNDARIES:
  North  → Nepal (international border)
  South  → Jharkhand
  East   → West Bengal
  West   → Uttar Pradesh
  
AREA: ~94,163 sq km (13th largest state)
CAPITAL: Patna
```

### 1.2 Physical Divisions of Bihar

```
BIHAR = Two major physical divisions:

┌─────────────────────────────────────────────────────┐
│              NORTH BIHAR (Gangetic Plains)           │
│  Flat, alluvial, highly fertile, flood-prone         │
│  Rivers from Nepal (Himalayan origin)                │
│  Kosi, Gandak, Bagmati, Mahananda, Kamla            │
├─────────────────────────────────────────────────────┤
│                    GANGA RIVER                        │
│              (Divides Bihar in two)                  │
├─────────────────────────────────────────────────────┤
│              SOUTH BIHAR                             │
│  Plateau fringe, less fertile, fewer floods          │
│  Rivers from peninsular plateau                      │
│  Son, Punpun, Falgu, Panchane                       │
└─────────────────────────────────────────────────────┘
```

---

## 🔶 SECTION 2: Rivers of Bihar — MOST TESTED TOPIC

### 2.1 North Bihar Rivers (Himalayan Origin — Perennial)

| River | Origin | Enters Bihar From | Key Fact |
|-------|--------|-------------------|----------|
| **Gandak** | Nepal Himalayas | Champaran | Triveni Sangam at Hajipur |
| **Burhi Gandak** | Someshwar hills | Muzaffarpur | Older course of Gandak |
| **Bagmati** | Nepal (Mahabharat range) | Sitamarhi | Floods Muzaffarpur, Samastipur |
| **Kamla-Balan** | Nepal | Madhubani | Madhubani district flooding |
| **Kosi** | Nepal (7 rivers merge) | Supaul | **"Sorrow of Bihar"** — changes course |
| **Mahananda** | Darjeeling hills | Kishanganj | Easternmost river of Bihar |

> ⭐ **SUPER PYQ FACT:** **Kosi = "Sorrow of Bihar"**
> - Changes course frequently (shifted ~110 km westward over 200 years)
> - Kosi is joined by 7 tributaries: Sun Kosi, Tamur, Arun etc.
> - Eastern Kosi Embankment was built to control floods

### 2.2 South Bihar Rivers (Peninsular Origin — Semi-perennial)

| River | Origin | Key Fact |
|-------|--------|----------|
| **Son** | Amarkantak plateau (MP) | Most important south Bihar river; joins Ganga near Patna |
| **Punpun** | Chotanagpur plateau | Joins Ganga near Fatuha (Patna) |
| **Falgu** | Chotanagpur | Flows through **Gaya** — sacred for Pitru Paksha; dries up in summer |
| **Panchane** | Chotanagpur | Munger area |

> ⭐ **PYQ FACT:** **Falgu River (Gaya)** = famous for **Pitru Paksha** ancestor worship
> Son River = most important river of south Bihar

### 2.3 The Ganga in Bihar

```
GANGA IN BIHAR:
  Enters: Buxar (from UP border)
  Exits: Rajmahal (into West Bengal)
  Length in Bihar: ~445 km
  
  Important confluence points:
  - Son + Ganga → Near Patna (Arrah-Dinapur)
  - Gandak + Ganga → Hajipur/Sonpur (Triveni Sangam)
  - Punpun + Ganga → Fatuha area
  
  Sacred Ghats in Patna:
  - Patna Sahib Ghat (near Guru Gobind Singh birthplace)
  - Gandhi Ghat, Mahendru Ghat
```

---

## 🔶 SECTION 3: Districts, Divisions and Administrative Geography

### 3.1 Key Administrative Facts

| Fact | Detail |
|------|--------|
| **Total Districts** | 38 |
| **Total Divisions** | 9 |
| **State Capital** | Patna |
| **Largest District (Area)** | West Champaran |
| **Smallest District (Area)** | Sheohar |
| **Most Populous District** | Patna |
| **Least Populous District** | Sheohar |
| **Highest Population Density** | Sheohar |
| **Highest Literacy** | Rohtas |
| **Lowest Literacy** | Purnia / Kishanganj |
| **Maximum Paddy Production** | Rohtas |
| **Maximum Silk Production** | Bhagalpur |

### 3.2 Bihar's 9 Administrative Divisions and Districts

| Division | Key Districts |
|----------|--------------|
| **Patna** | Patna, Nalanda, Bhojpur, Buxar, Rohtas, Kaimur |
| **Magadha** | Gaya, Jehanabad, Nawada, Arwal |
| **Shahabad** | (Part of Patna division) |
| **Munger** | Munger, Jamui, Lakhisarai, Sheikhpura, Khagaria, Begusarai |
| **Bhagalpur** | Bhagalpur, Banka |
| **Purnea** | Purnea, Kishanganj, Araria, Katihar |
| **Kosi** | Saharsa, Supaul, Madhepura |
| **Darbhanga** | Darbhanga, Madhubani, Samastipur |
| **Muzaffarpur** | Muzaffarpur, Sitamarhi, Sheohar, Vaishali |
| **Saran** | Saran, Siwan, Gopalganj |
| **Tirhut** | West Champaran, East Champaran |

---

## 🔶 SECTION 4: Climate and Soil of Bihar

### 4.1 Climate

```
Bihar has HUMID SUBTROPICAL CLIMATE (Koppen: Cwa)

SEASONS IN BIHAR:
┌──────────────┬───────────────────────────────────────┐
│ Season       │ Period & Feature                      │
├──────────────┼───────────────────────────────────────┤
│ Winter       │ November–February; cold, foggy        │
│              │ NE trade winds; very little rain       │
├──────────────┼───────────────────────────────────────┤
│ Summer/Hot   │ March–June; very hot, dry winds (Loo) │
│              │ Temperature 35°C–45°C                 │
├──────────────┼───────────────────────────────────────┤
│ Monsoon      │ June–September; SW Monsoon             │
│              │ 80–90% of annual rainfall              │
│              │ North Bihar gets more rain (1200mm+)  │
├──────────────┼───────────────────────────────────────┤
│ Post-Monsoon │ October–November; NE monsoon retreats │
└──────────────┴───────────────────────────────────────┘

Average annual rainfall: 1000–1200 mm
Highest rainfall: North Bihar (Kishanganj ~1500mm)
Lowest rainfall: South Bihar districts
```

### 4.2 Soil Types in Bihar

| Soil Type | Location | Crops |
|-----------|----------|-------|
| **Alluvial Soil (Diara)** | Ganga flood plains, North Bihar | Rice, Wheat, Sugarcane — most fertile |
| **Terai Soil** | Champaran, Sitamarhi (Nepal border) | Dense forest, Rice |
| **Older Alluvial (Bhangar)** | Upland areas | Wheat, Gram |
| **Newer Alluvial (Khadar)** | River banks, flood plains | Rice, Jute, Vegetables |
| **Red Soil** | Jamui, Nawada, Banka, Munger (south Bihar fringe) | Millets, Groundnut |
| **Laterite Soil** | Small patches — Banka, Jamui | Poor fertility |

> ⭐ **PYQ FACT:** Most of Bihar = **Alluvial soil** (extremely fertile). South Bihar fringe = Red Soil.

---

## 🔶 SECTION 5: Forests & Wildlife — Bihar

### 5.1 Forest Cover

- Bihar has one of the **lowest forest cover percentages** in India
- Forest cover: ~7% of total area (national average ~24%)
- Most forests in: **Kaimur, Rohtas, Jamui, Munger, West Champaran**

### 5.2 Wildlife Sanctuaries and National Parks of Bihar

| Name | Type | District | Key Animal |
|------|------|---------|------------|
| **Valmiki National Park** | National Park | West Champaran | Tiger (Project Tiger), Elephant, Rhino |
| **Valmiki Wildlife Sanctuary** | Wildlife Sanctuary | West Champaran | Tiger, Leopard |
| **Rajgir Wildlife Sanctuary** | Wildlife Sanctuary | Nalanda | Leopard, Bear, various birds |
| **Udaypur Wildlife Sanctuary** | Wildlife Sanctuary | West Champaran | Various mammals |
| **Gautam Buddha Wildlife Sanctuary** | Wildlife Sanctuary | Gaya | Gaur (State Animal) |
| **Bhimbandh Wildlife Sanctuary** | Wildlife Sanctuary | Munger | Leopard |
| **Kusheshwar Asthan** | Bird Sanctuary | Darbhanga | Migratory birds |
| **Nagi Dam Bird Sanctuary** | Bird Sanctuary | Jamui | Migratory birds |
| **Nakti Dam Bird Sanctuary** | Bird Sanctuary | Jamui | Birds |

> ⭐ **BPSC KEY FACTS:**
> - **Valmiki National Park** = only National Park of Bihar (West Champaran)
> - It's part of **Project Tiger** (Valmiki Tiger Reserve)
> - **Kusheshwar Asthan** (Darbhanga) = famous for migratory Siberian birds in winter
> - **Vikramshila Gangetic Dolphin Sanctuary** is located near Bhagalpur — protects Gangetic Dolphins!

---

## 🔶 SECTION 6: Important Lakes and Water Bodies

| Lake/Water Body | Location | Significance |
|-----------------|----------|-------------|
| **Kanwar Jheel (Kabar Tal)** | Begusarai | Asia's largest freshwater oxbow lake; Ramsar Site |
| **Udaipur Tal** | Vaishali | |
| **Kusheshwar Asthan** | Darbhanga | Migratory birds |
| **Anupam Tal** | Nalanda | |

> ⭐ **PYQ FACT:** **Kanwar Jheel (Kabar Tal)** in Begusarai = Asia's largest freshwater **oxbow lake**. Declared a **Ramsar Wetland** site.

---

## 🔶 SECTION 7: Historical-Geographical Places of Bihar

| Place | District | Historical Significance |
|-------|---------|------------------------|
| **Patna (Pataliputra)** | Patna | Capital of Maurya Empire, Gupta Empire |
| **Nalanda** | Nalanda | Ancient Buddhist university (5th–12th century AD) |
| **Rajgir (Rajagriha)** | Nalanda | Capital of Magadha; Buddha taught here; hot springs |
| **Bodhgaya** | Gaya | Buddha attained enlightenment under Bodhi tree |
| **Pawapuri** | Nalanda | Lord Mahavira attained Moksha (Nirvana) here |
| **Vaishali** | Vaishali | Birthplace of Lord Mahavira; world's first republic |
| **Vikramshila** | Bhagalpur | Ancient Buddhist university (Pala period) |
| **Champaran** | W+E Champaran | Champaran Satyagraha (1917) by Gandhi |
| **Sonepur** | Saran | World's largest cattle fair (Sonepur Mela) |
| **Buxar** | Buxar | Battle of Buxar (1764) |

> ⭐ **PYQ FACTS:**
> - **Vaishali** = first democratic republic in the world (Lichchavi clan)
> - **Bodhgaya** = UNESCO World Heritage Site (Mahabodhi Temple)
> - **Sonepur Mela** = world's largest cattle/animal fair (held on Kartik Purnima)
> - **Rajgir** = has hot water springs (Brahmakund)

---

## 🔶 SECTION 8: Geography — Key Statistical Facts (Quick Reference)

```
BIHAR GEOGRAPHY — FLASH CARDS:

1.  Area               → ~94,163 sq km (13th in India)
2.  Population         → ~12.4 crore (Census 2011) — 3rd most populous state
3.  Population % India → ~8.58% of India's population
4.  Population density → ~1106 persons/sq km (2nd highest in India after UP)
5.  Sex ratio          → 918 females per 1000 males (2011)
6.  Literacy rate      → ~61.8% (among lower states)
7.  No. of districts   → 38
8.  No. of divisions   → 9
9.  Total river length → Ganga: ~445 km through Bihar
10. Highest peak       → Kaimur hills (Rohtas) ~300-500m; not very high
11. Largest district   → West Champaran (by area)
12. Smallest district  → Sheohar (by area)
13. Border country     → Nepal (to the North)
14. Border states      → UP (W), Jharkhand (S), West Bengal (E)
15. Annual rainfall    → 1000–1200 mm average
```

---

## 🔶 SECTION 9: India Geography — Quick Facts for GS (PYQ-tested)

| Question Type | Key Fact |
|--------------|----------|
| Highest peak Eastern Ghats | **Mahendragiri** (Odisha) |
| South Peninsular Upland origin | Part of **Gondwana Land** |
| East-West Corridor connects | **Silchar to Porbandar** |
| Black soil found in | **Karnataka + Gujarat** (both correct) |
| Maximum urbanization state | **Goa** |
| Malnad region | **Karnataka Plateau** |
| Stalactites and Stalagmites formed by | **Underground water** action |
| Bihar's population % of India | **8.58%** |
| Bihar's max paddy production district | **Rohtas** |
| SW Monsoon withdrawal from Hyderabad | **1st October** |

---

# 📝 PRACTICE QUESTIONS

---

# 🖥️ PART A — CS MCQs (25 Questions)

### Topic: DSA — Full PYQ Special (All Topics)
### Format: BPSC 5-option (D = More than one / E = None of the above)
### Difficulty: Easy → Medium → Hard → PYQ-Style → Tricky

---

**Q1.** Which data structure is used internally by the operating system to handle function calls in recursion?

(A) Queue  
(B) Array  
(C) Stack  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** In a standard Stack, which of the following operations can be performed in O(1) time?

(A) Push  
(B) Pop  
(C) Peek  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** What is the CORRECT empty condition for a Circular Queue?

(A) rear == -1  
(B) front == -1  
(C) front == rear == -1  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** Which of the following is NOT an application of Stack?

(A) Expression evaluation  
(B) Asynchronous data transfer between processes  
(C) Backtracking algorithms  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** Convert the infix expression A + B * C to postfix. What is the result?

(A) A B C * +  
(B) A B + C *  
(C) + A * B C  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** The Circular Queue is also known as:

(A) Priority Queue  
(B) Ring Buffer  
(C) Deque  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** In a Binary Search Tree (BST), the Inorder traversal of nodes gives which of the following?

(A) Nodes in decreasing order  
(B) Nodes in random order  
(C) Nodes in increasing (sorted) order  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** How many distinct Binary Search Trees can be formed from 4 distinct keys?

(A) 12  
(B) 16  
(C) 14  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** Which traversal of a Binary Tree visits nodes in the order: Left → Root → Right?

(A) Preorder  
(B) Postorder  
(C) Inorder  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** Which of the following is/are correct properties of a Binary Search Tree?

(A) Left child < Parent node  
(B) Right child > Parent node  
(C) Both left and right subtrees are also BSTs  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** Which sorting algorithm has O(n log n) time complexity in ALL cases (best, average, worst)?

(A) Quick Sort  
(B) Bubble Sort  
(C) Merge Sort  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** A Doubly Linked List compared to a Singly Linked List is:

(A) Easier to implement due to bidirectional traversal  
(B) Harder to implement due to extra pointer management  
(C) Uses less memory  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** Before performing a DELETION operation on a Queue, which condition must be checked?

(A) Overflow  
(B) Underflow  
(C) IsFull  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Binary Search algorithm requires the input array to be:

(A) In any order  
(B) Sorted in ascending or descending order  
(C) Stored in a linked list  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** BFS (Breadth-First Search) graph traversal uses which data structure?

(A) Stack  
(B) Queue  
(C) Priority Queue  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** In a Red-Black Tree, when a new node is inserted as the root, its color should be:

(A) Red  
(B) Either Red or Black (no rule)  
(C) Black  
(D) More than one of the above  
(E) None of the above  

---

**Q17 (PYQ-Style).** Which of the following statements about Merge Sort is/are TRUE?

(A) Merge Sort is a stable sorting algorithm  
(B) Merge Sort uses Divide and Conquer paradigm  
(C) Merge Sort requires O(n) extra space (not in-place)  
(D) More than one of the above  
(E) None of the above  

---

**Q18 (PYQ-Style).** In a Spanning Tree with N vertices, how many edges does it contain?

(A) N  
(B) N+1  
(C) N-1  
(D) More than one of the above  
(E) None of the above  

---

**Q19 (PYQ-Style).** The time complexity of Infix to Postfix conversion using Stack is:

(A) O(1)  
(B) O(n²)  
(C) O(n)  
(D) More than one of the above  
(E) None of the above  

---

**Q20 (PYQ-Style).** Which of the following is the BEST data structure to implement a Priority Queue?

(A) Array  
(B) Linked List  
(C) Binary Heap  
(D) More than one of the above  
(E) None of the above  

---

**Q21 (Hard).** The worst case time complexity of Quick Sort occurs when:

(A) The array is already sorted in ascending order  
(B) The pivot is always the median element  
(C) The array is sorted in descending order  
(D) More than one of the above  
(E) None of the above  

---

**Q22 (Hard).** Which of the following correctly identifies the Catalan number C(n) for calculating the number of distinct BSTs from n keys?

(A) C(n) = n!  
(B) C(n) = 2^n  
(C) C(n) = (2n)! / ((n+1)! × n!)  
(D) More than one of the above  
(E) None of the above  

---

**Q23 (Tricky).** Given a BST with Preorder traversal: 5, 3, 1, 4, 7, 6, 8 — what is the Inorder traversal?

(A) 1, 3, 4, 5, 6, 7, 8  
(B) 5, 3, 1, 4, 7, 6, 8  
(C) 1, 4, 3, 6, 8, 7, 5  
(D) More than one of the above  
(E) None of the above  

---

**Q24 (Tricky).** Delete from REAR in a Deque implemented with a Singly Linked List takes:

(A) O(1) time  
(B) O(log n) time  
(C) O(n) time  
(D) More than one of the above  
(E) None of the above  

---

**Q25 (Tricky).** Which of the following statements is/are CORRECT?

(A) Selection Sort is a stable sorting algorithm  
(B) Heap Sort requires O(1) extra space  
(C) Radix Sort is a comparison-based sorting algorithm  
(D) More than one of the above  
(E) None of the above  

---

# 🌍 PART B — GS/GK MCQs (25 Questions)

### Topic: Bihar GK — Geography
### Format: BPSC 5-option (D = More than one / E = None of the above)
### Difficulty: Easy → Medium → Hard → PYQ-Style → Tricky

---

**Q26.** Bihar shares its northern border with:

(A) Uttar Pradesh  
(B) Nepal  
(C) West Bengal  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** Which river is called the "Sorrow of Bihar" due to its frequent and devastating floods?

(A) Gandak  
(B) Son  
(C) Kosi  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** Valmiki National Park, the only National Park of Bihar, is located in which district?

(A) Gaya  
(B) West Champaran  
(C) Rohtas  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** The Falgu River, famous for Pitru Paksha rituals, flows through which city?

(A) Patna  
(B) Rajgir  
(C) Gaya  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** Which of the following is the largest district of Bihar by area?

(A) Patna  
(B) West Champaran  
(C) Rohtas  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** Asia's largest freshwater oxbow lake, Kanwar Jheel (Kabar Tal), is located in:

(A) Darbhanga  
(B) Muzaffarpur  
(C) Begusarai  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** Kusheshwar Asthan bird sanctuary in Bihar is famous for which type of visitors?

(A) Domestic migratory birds  
(B) Siberian migratory birds in winter  
(C) Resident birds of Bihar  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** The Battle of Buxar (1764) was fought near which town of present-day Bihar?

(A) Patna  
(B) Hajipur  
(C) Buxar  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** Bihar's population as a percentage of India's total population (Census 2011) is approximately:

(A) 5.58%  
(B) 8.58%  
(C) 10.5%  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** Which district of Bihar records the maximum paddy (rice) production?

(A) Patna  
(B) Muzaffarpur  
(C) Rohtas  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** The Vikramshila Gangetic Dolphin Sanctuary is located near which city?

(A) Patna  
(B) Bhagalpur  
(C) Gaya  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** Sonepur Mela, the world's largest cattle fair, is held on which occasion?

(A) Dussehra  
(B) Kartik Purnima  
(C) Makar Sankranti  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** Which physical division of Bihar is more flood-prone?

(A) South Bihar  
(B) North Bihar  
(C) Both equally  
(D) More than one of the above  
(E) None of the above  

---

**Q39 (PYQ-Style).** Which of the following ancient sites is a UNESCO World Heritage Site located in Bihar?

(A) Rajgir  
(B) Vaishali  
(C) Mahabodhi Temple Complex, Bodhgaya  
(D) More than one of the above  
(E) None of the above  

---

**Q40 (PYQ-Style).** Lord Mahavira, the 24th Tirthankara of Jainism, was born in which place in Bihar?

(A) Bodhgaya  
(B) Pawapuri  
(C) Vaishali  
(D) More than one of the above  
(E) None of the above  

---

**Q41 (PYQ-Style).** The Son River originates from which region?

(A) Nepal Himalayas  
(B) Amarkantak plateau, Madhya Pradesh  
(C) Chotanagpur plateau, Jharkhand  
(D) More than one of the above  
(E) None of the above  

---

**Q42 (PYQ-Style).** Triveni Sangam at Hajipur is the confluence of which rivers?

(A) Ganga and Son  
(B) Ganga, Gandak, and a small stream  
(C) Ganga and Kosi  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** Which of the following states does Bihar NOT share its boundary with?

(A) Uttar Pradesh  
(B) Odisha  
(C) Jharkhand  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** The highest literacy district in Bihar is:

(A) Patna  
(B) Muzaffarpur  
(C) Rohtas  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** Hot springs (Brahmakund) in Bihar are located at:

(A) Gaya  
(B) Rajgir (Nalanda district)  
(C) Bodhgaya  
(D) More than one of the above  
(E) None of the above  

---

**Q46 (Hard).** Kanwar Jheel has been listed under which international wetland convention?

(A) CITES  
(B) Ramsar Convention  
(C) Kyoto Protocol  
(D) More than one of the above  
(E) None of the above  

---

**Q47 (Hard).** The dominant soil type in the Gangetic plains of Bihar is:

(A) Red soil  
(B) Laterite soil  
(C) Alluvial soil  
(D) More than one of the above  
(E) None of the above  

---

**Q48 (Tricky).** Which of the following is CORRECT about Vaishali district of Bihar?

(A) It is where Lord Mahavira was born  
(B) It houses the HQ of East Central Railway at Hajipur  
(C) It is considered the seat of world's first republic  
(D) More than one of the above  
(E) None of the above  

---

**Q49 (Tricky).** The East-West Corridor, an important national highway project, connects:

(A) Delhi to Mumbai  
(B) Silchar (Assam) to Porbandar (Gujarat)  
(C) Patna to Kolkata  
(D) More than one of the above  
(E) None of the above  

---

**Q50 (Tricky).** The highest peak of the Eastern Ghats is:

(A) Anaimudi  
(B) Mahendragiri  
(C) Dodabetta  
(D) More than one of the above  
(E) None of the above  

---

---

# ✅ ANSWER KEY

> **🛑 STOP — Have you attempted ALL 50 questions on your own? Only then proceed!**

---

## CS Answers (Q1–Q25)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q1 | **(C)** | Recursion = uses STACK internally (function call stack). PYQ repeated multiple times |
| Q2 | **(D)** | Push, Pop, AND Peek are ALL O(1) operations on a Stack |
| Q3 | **(C)** | Circular Queue empty condition: front = rear = -1. Both must be -1 |
| Q4 | **(B)** | Asynchronous data transfer uses QUEUE, not Stack. Stack does expression eval, backtracking |
| Q5 | **(A)** | A + B*C → * higher precedence → B*C first → A B C * + |
| Q6 | **(B)** | Circular Queue = **Ring Buffer** (PYQ direct — TRE 1.0 + 2.0 repeated) |
| Q7 | **(C)** | BST Inorder traversal = sorted ascending order. Classic PYQ fact |
| Q8 | **(C)** | C(4) = **14** distinct BSTs. Formula: (2n)!/((n+1)!×n!) — must know! |
| Q9 | **(C)** | Inorder = Left → Root → Right. Pre = Root→L→R. Post = L→R→Root |
| Q10 | **(D)** | ALL three are correct BST properties — left < parent, right > parent, subtrees also BSTs |
| Q11 | **(C)** | Merge Sort = O(n log n) always. Quick Sort = O(n²) worst. Bubble = O(n²) worst |
| Q12 | **(B)** | Doubly LL is HARDER to implement (more pointers to maintain). PYQ trap! |
| Q13 | **(B)** | Before deletion from Queue → check UNDERFLOW. Before insertion → check OVERFLOW |
| Q14 | **(B)** | Binary Search requires **SORTED** array (ascending or descending). PYQ fact |
| Q15 | **(B)** | BFS uses QUEUE. DFS uses Stack. Very common PYQ |
| Q16 | **(C)** | Red-Black tree: new root = **BLACK**. New non-root = RED |
| Q17 | **(D)** | All three are correct: Merge Sort is stable, uses D&C, and needs O(n) extra space |
| Q18 | **(C)** | Spanning tree with N vertices = exactly **N-1 edges** |
| Q19 | **(C)** | Infix to Postfix time complexity = **O(n)**. PYQ repeated TRE 2.0 |
| Q20 | **(C)** | Priority Queue best implemented with **Binary Heap** (O(log n) operations) |
| Q21 | **(D)** | Quick Sort worst case = O(n²) when array is already sorted (asc OR desc) — both are worst cases |
| Q22 | **(C)** | Catalan formula: C(n) = (2n)!/((n+1)!×n!) is correct |
| Q23 | **(A)** | Preorder 5,3,1,4,7,6,8 → BST built → Inorder gives sorted: 1,3,4,5,6,7,8 |
| Q24 | **(C)** | Deque delete from REAR with singly LL = **O(n)** (need to find second-to-last node) |
| Q25 | **(B)** | Selection Sort is UNSTABLE. Radix Sort is NON-comparison. Heap Sort = O(1) space ✓ |

---

## GS Answers (Q26–Q50)

| Q | Ans | Key Explanation |
|---|-----|-----------------|
| Q26 | **(B)** | Bihar's northern border = **Nepal**. UP=West, Jharkhand=South, WB=East |
| Q27 | **(C)** | **Kosi** = "Sorrow of Bihar." Son and Gandak don't cause this level of destruction |
| Q28 | **(B)** | Valmiki National Park = **West Champaran** — Bihar's only national park |
| Q29 | **(C)** | Falgu River flows through **Gaya** — famous for Pitru Paksha (ancestor worship) |
| Q30 | **(B)** | **West Champaran** = largest district by area. Sheohar = smallest |
| Q31 | **(C)** | Kanwar Jheel (Kabar Tal) = **Begusarai**. Asia's largest freshwater oxbow lake |
| Q32 | **(B)** | Kusheshwar Asthan = famous for **Siberian migratory birds** in winter season |
| Q33 | **(C)** | Battle of Buxar 1764 was fought at **Buxar** (now a district headquarters) |
| Q34 | **(B)** | Bihar = **8.58%** of India's population (Census 2011) |
| Q35 | **(C)** | **Rohtas** = maximum paddy production in Bihar (PYQ direct) |
| Q36 | **(B)** | Vikramshila Dolphin Sanctuary = **Bhagalpur** (protects Gangetic Dolphins) |
| Q37 | **(B)** | Sonepur Mela = **Kartik Purnima** (October-November). Held at Sonepur, Saran district |
| Q38 | **(B)** | **North Bihar** = more flood-prone (Himalayan rivers bring heavy silt and floods) |
| Q39 | **(C)** | **Mahabodhi Temple Complex, Bodhgaya** = UNESCO World Heritage Site (2002) |
| Q40 | **(C)** | Lord Mahavira born in **Vaishali** (Kundalagrama village). Pawapuri = his moksha place |
| Q41 | **(B)** | Son River originates from **Amarkantak plateau, MP** (NOT Nepal, NOT Jharkhand) |
| Q42 | **(B)** | Triveni Sangam Hajipur = confluence of **Ganga + Gandak** (+ small stream Sarayu) |
| Q43 | **(B)** | Bihar does NOT share boundary with **Odisha**. Jharkhand (S), UP (W), WB (E), Nepal (N) |
| Q44 | **(C)** | **Rohtas** = highest literacy district in Bihar |
| Q45 | **(B)** | Hot springs (Brahmakund) = **Rajgir, Nalanda district** — famous tourist attraction |
| Q46 | **(B)** | Kanwar Jheel = **Ramsar Convention** (international wetland site) |
| Q47 | **(C)** | Gangetic plains of Bihar = predominantly **Alluvial soil** — most fertile |
| Q48 | **(D)** | All three are correct about Vaishali: Mahavira birthplace, ECR HQ at Hajipur, first republic |
| Q49 | **(B)** | East-West Corridor = **Silchar (Assam) to Porbandar (Gujarat)** — PYQ tested |
| Q50 | **(B)** | Highest peak of Eastern Ghats = **Mahendragiri** (1501m, Odisha). Anaimudi = Western Ghats |

---

# 🌟 TOPPER'S REVISION NOTES — Day 34

## ⚡ CS Quick Revision (5 Bullet Points)

1. **Stack (LIFO):** Recursion, Expression eval, Balancing symbols, Backtracking — Asynchronous transfer uses QUEUE not Stack
2. **Circular Queue = Ring Buffer** | Empty: front=rear=-1 | Full: (rear+1)%SIZE==front | Created to eliminate memory wastage
3. **BST:** Inorder=Sorted | C(4)=14 distinct BSTs | Left<Root<Right | All subtrees also BSTs | Red-Black: new root=BLACK
4. **Sorting:** Merge=O(n log n) always, Stable, NOT in-place | Quick=O(n²) worst, Unstable, In-place | Selection=O(n²) always, Unstable
5. **BFS→Queue | DFS→Stack | Infix-Postfix→Stack O(n) | Spanning tree N vertices→N-1 edges | Priority Queue→Binary Heap**

## ⚡ GS Quick Revision (5 Bullet Points)

1. **Bihar borders:** North=Nepal, South=Jharkhand, East=West Bengal, West=UP | 38 districts, 9 divisions
2. **Key rivers:** Kosi=Sorrow of Bihar | Falgu=Gaya (Pitru Paksha) | Son=South Bihar (origin Amarkantak) | Gandak=Hajipur Triveni
3. **Wildlife:** Valmiki NP=West Champaran (only NP) | Kusheshwar Asthan=Siberian birds (Darbhanga) | Kanwar Jheel=Begusarai (Ramsar, Asia's largest oxbow)
4. **Historical sites:** Vaishali=Mahavira birthplace+1st republic | Bodhgaya=UNESCO Heritage | Rajgir=hot springs | Sonepur=world's largest cattle fair (Kartik Purnima)
5. **Statistics:** Bihar=8.58% India population | Largest district=West Champaran | Max paddy=Rohtas | Max literacy=Rohtas | East-West Corridor=Silchar-Porbandar**

---

## 📌 Day-34 Traps to Avoid

| Common Mistake | Correct Answer |
|---------------|---------------|
| BFS uses Stack | ❌ Wrong → BFS uses QUEUE |
| DFS uses Queue | ❌ Wrong → DFS uses STACK |
| C(4) = 12 or 16 | ❌ Wrong → C(4) = **14** |
| Inorder of BST = random | ❌ Wrong → Inorder = **Sorted** |
| Red-Black new node = Red always | ❌ Wrong → New **root** = BLACK; new non-root = Red |
| Quick Sort = O(n log n) always | ❌ Wrong → Worst case = **O(n²)** |
| Merge Sort = in-place | ❌ Wrong → Merge Sort needs **O(n)** extra space |
| Sonepur Mela = Dussehra | ❌ Wrong → **Kartik Purnima** |
| Falgu at Patna | ❌ Wrong → Falgu at **Gaya** |
| Vaishali = Bodhgaya | ❌ Wrong → Vaishali = Mahavira birthplace; Bodhgaya = Buddha's enlightenment |
| Bihar borders Odisha | ❌ Wrong → Bihar does **NOT** border Odisha |
| Son originates Nepal | ❌ Wrong → Son originates from **Amarkantak (MP)** |
| Kanwar Jheel = Darbhanga | ❌ Wrong → Kanwar Jheel = **Begusarai** |

---

> **🏆 Day-34 Goal:** Score 40+/50 in these MCQs. Any wrong answer = re-read that section immediately.
>
> **📅 Tomorrow → Day-35:** Full DSA Revision Quiz — Everything from Day 15–34 will be tested. Prepare the complete DSA checklist tonight!

---
*BPSC TRE 4.0 | Phase 1 — Week 5 | Day 34 of 170 | PYQ Special Session*
