# 📅 BPSC TRE 4.0 — DAY 25 COMPLETE STUDY MODULE
### Binary Search Tree (BST) + Physics — Electrical Power
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): BST — Definition, Properties, Operations, Complexity, Catalan Numbers
> - Afternoon (1 hr): Physics — Electrical Power (Formulas, Units, Applications)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Binary Search Tree (BST) — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Binary Search Tree?

### Real-Life Analogy — The Dictionary Search:
```
Imagine a DICTIONARY with 1000 pages.
You want to find the word "Mango".

BRUTE FORCE (like an unsorted list):
  Open page 1, read every word... page 2... page 3...
  → Worst case: read all 1000 pages → O(n)

SMART SEARCH (like a BST):
  Open the MIDDLE page (~page 500).
  "Mango" comes AFTER the middle word?
    → Search only the RIGHT half (pages 500–1000)
  "Mango" comes BEFORE the middle word?
    → Search only the LEFT half (pages 1–500)
  Each step HALVES the search space → O(log n)

A BST IS that dictionary — it organises data so every search
decision eliminates HALF the remaining possibilities.
```

### Formal Definition:
A **Binary Search Tree (BST)** is a Binary Tree where for **every node**:
- All values in the **LEFT subtree** are **LESS THAN** the node's value
- All values in the **RIGHT subtree** are **GREATER THAN** the node's value
- This property holds **RECURSIVELY** for every node in the tree

```
BST Property at EVERY node:

         [NODE]
        /       \
  [LEFT         [RIGHT
  subtree]       subtree]
  ALL values     ALL values
  < NODE         > NODE
```

### A Valid BST:
```
           8
          / \
         3   10
        / \    \
       1   6    14
          / \   /
         4   7 13

Check BST property at EACH node:
  Node 8:  left subtree {3,1,6,4,7} all < 8 ✓
           right subtree {10,14,13} all > 8 ✓
  Node 3:  left {1} < 3 ✓, right {6,4,7} > 3 ✓
  Node 10: left = none, right {14,13} > 10 ✓
  Node 6:  left {4} < 6 ✓, right {7} > 6 ✓
  Node 14: left {13} < 14 ✓, right = none ✓
→ VALID BST ✓
```

---

## 🔷 SECTION 2: Binary Tree vs BST — The Core Difference

```
BINARY TREE:              BINARY SEARCH TREE:
     5                           8
    / \                         / \
   9   2      ← random        3   10
  / \                        / \    \
 1   7                      1   6   14

Binary Tree:               BST:
- Each node has ≤ 2 children  - Each node has ≤ 2 children
- NO ordering rule            - LEFT < ROOT < RIGHT at every node
- Search: O(n)                - Search: O(log n) average
- Inorder: any order          - Inorder: SORTED ascending
```

### 🚨 PYQ TRAP #1: All BSTs Are Binary Trees, Not Vice Versa
> Every BST is a Binary Tree (it satisfies binary tree definition).
> NOT every Binary Tree is a BST (random values don't satisfy LEFT < ROOT < RIGHT).
> BST is a SPECIAL CASE of Binary Tree with an ordering constraint.

---

## 🔷 SECTION 3: BST Search Operation — Step-by-Step

### Algorithm:
```
Search(root, key):
  1. If root == NULL → key NOT FOUND (return false)
  2. If root.data == key → FOUND! (return true)
  3. If key < root.data → search in LEFT subtree
  4. If key > root.data → search in RIGHT subtree
```

### Visual Search for key = 6 in BST:
```
BST:
           8
          / \
         3   10
        / \    \
       1   6    14

Step 1: Start at ROOT = 8
        6 < 8 → Go LEFT to node 3

Step 2: At node 3
        6 > 3 → Go RIGHT to node 6

Step 3: At node 6
        6 == 6 → FOUND! ✓

Path taken: 8 → 3 → 6 (only 3 comparisons for 6 nodes!)
```

### Visual Search for key = 5 (NOT in tree):
```
Step 1: At 8 → 5 < 8 → Go LEFT to 3
Step 2: At 3 → 5 > 3 → Go RIGHT to 6
Step 3: At 6 → 5 < 6 → Go LEFT to... NULL!
        NULL → NOT FOUND ✗

Only 3 comparisons to confirm 5 is absent!
```

### Why Search is O(log n) in Balanced BST:
```
At each step, we ELIMINATE roughly HALF the remaining nodes:
  Start: n nodes to search
  After step 1: n/2 nodes
  After step 2: n/4 nodes
  After step 3: n/8 nodes
  ...
  After k steps: n/2^k nodes

When n/2^k = 1 → k = log₂(n) → search stops
→ O(log n) comparisons total

Example: n = 1000 nodes
  Binary search: ~10 comparisons (log₂(1000) ≈ 10)
  Linear search: up to 1000 comparisons
```

---

## 🔷 SECTION 4: BST Insertion — Step-by-Step

### Algorithm:
```
Insert(root, key):
  1. If root == NULL → create new node with key → return it (new root or subtree)
  2. If key < root.data → Insert in LEFT subtree
  3. If key > root.data → Insert in RIGHT subtree
  4. If key == root.data → DUPLICATE (either ignore or handle as per policy)
```

### Build a BST by Inserting: 8, 3, 10, 1, 6, 14, 4, 7

**Step 1: Insert 8** (first element = ROOT)
```
    8
```

**Step 2: Insert 3** → 3 < 8 → go LEFT
```
    8
   /
  3
```

**Step 3: Insert 10** → 10 > 8 → go RIGHT
```
    8
   / \
  3   10
```

**Step 4: Insert 1** → 1 < 8 → LEFT → 1 < 3 → LEFT of 3
```
    8
   / \
  3   10
 /
1
```

**Step 5: Insert 6** → 6 < 8 → LEFT → 6 > 3 → RIGHT of 3
```
    8
   / \
  3   10
 / \
1   6
```

**Step 6: Insert 14** → 14 > 8 → RIGHT → 14 > 10 → RIGHT of 10
```
    8
   / \
  3   10
 / \    \
1   6    14
```

**Step 7: Insert 4** → 4 < 8 → LEFT → 4 > 3 → RIGHT → 4 < 6 → LEFT of 6
```
    8
   / \
  3   10
 / \    \
1   6    14
   /
  4
```

**Step 8: Insert 7** → 7 < 8 → LEFT → 7 > 3 → RIGHT → 7 > 6 → RIGHT of 6
```
    8
   / \
  3   10
 / \    \
1   6    14
   / \
  4   7
```

**Final BST:**
```
           8                ← Root
          / \
         3   10             ← Level 1
        / \    \
       1   6    14          ← Level 2
          / \   /
         4   7 13           ← Level 3 (13 inserted after 14 would go here)
```

### 🚨 PYQ TRAP #2: Insertion Order Matters!
```
The SAME SET of numbers can build DIFFERENT BSTs depending on insertion order!

Insert order: 8, 3, 10, 1, 6 → Balanced-ish BST (as above)

Insert order: 1, 3, 6, 8, 10 → RIGHT-SKEWED BST:
1
 \
  3
   \
    6
     \
      8
       \
        10
This is a DEGENERATE BST = Linked List! Search = O(n) not O(log n)!
```

---

## 🔷 SECTION 5: BST Deletion — Three Cases

### Case 1: Delete a LEAF NODE (no children) — Simplest
```
Delete node 4 from BST:
         8
        / \
       3   10
      / \    \
     1   6    14
        / \
       4   7        ← Delete 4 (leaf)

Just REMOVE it and set parent's pointer to NULL:
         8
        / \
       3   10
      / \    \
     1   6    14
          \
           7        ← 4 is gone; 6's left pointer = NULL
```

### Case 2: Delete a node with ONE child
```
Delete node 10 (has only right child 14):
         8
        / \
       3   10       ← Delete 10
      / \    \
     1   6    14    ← 14 is 10's only child

Replace 10 with its child 14:
         8
        / \
       3   14       ← 14 takes 10's position
      / \
     1   6
          \
           7
```

### Case 3: Delete a node with TWO children — Most Complex
```
Delete node 3 (has two children: 1 and 6):
         8
        / \
       3   10       ← Delete 3 (has children 1 and 6)
      / \    \
     1   6    14
        / \
       4   7

Two replacement strategies:
  (a) INORDER SUCCESSOR: The SMALLEST node in the RIGHT subtree
      Inorder successor of 3 = smallest in {6,4,7} = 4
  (b) INORDER PREDECESSOR: The LARGEST node in the LEFT subtree
      Inorder predecessor of 3 = largest in {1} = 1

Using Inorder Successor (4):
  1. Find inorder successor = 4
  2. Copy 4's value to node 3's position
  3. Delete 4 from its original position (now a leaf or 1 child)

Result:
         8
        / \
       4   10       ← 4 replaced 3
      / \    \
     1   6    14
          \
           7        ← 4 was removed from here
```

### 🚨 PYQ TRAP #3: Inorder Successor Definition
> **Inorder Successor** of a node = the NEXT node in INORDER traversal
>   = SMALLEST node in the RIGHT subtree
>   = LEFTMOST node in the RIGHT subtree
>
> **Inorder Predecessor** of a node = the PREVIOUS node in INORDER traversal
>   = LARGEST node in the LEFT subtree
>   = RIGHTMOST node in the LEFT subtree

---

## 🔷 SECTION 6: BST Complexity Analysis

### Time Complexity Table:

| Operation | Best Case | Average Case | Worst Case |
|-----------|-----------|-------------|------------|
| Search | O(1) | O(log n) | O(n) |
| Insert | O(1) | O(log n) | O(n) |
| Delete | O(log n) | O(log n) | O(n) |
| Inorder Traversal | O(n) | O(n) | O(n) |

### When is Worst Case O(n)?
```
WORST CASE = SKEWED TREE (all nodes in one direction)

Right-Skewed BST (inserting sorted: 1,2,3,4,5):
1
 \
  2
   \
    3
     \
      4
       \
        5

Search for 5:
  1 → 2 → 3 → 4 → 5 = 5 comparisons for 5 nodes = O(n)
  No different from searching a LINKED LIST!

WHY O(n)? Tree HEIGHT = n (equals number of nodes)
In balanced tree: height = O(log n) → operations O(log n)
In skewed tree: height = O(n) → operations O(n)
```

### Height Determines Speed:
```
BALANCED BST (height ≈ log n):
         4
        / \
       2   6         Height = 2 ≈ log₂(7) ≈ 2.8 ✓
      / \ / \
     1  3 5  7
     → Search = O(log n) ← FAST

SKEWED BST (height = n-1):
1 → 2 → 3 → 4 → 5 → 6 → 7
     Height = 6 = n-1
     → Search = O(n) ← SLOW (same as linked list)
```

### 🚨 PYQ TRAP #4: Average vs Worst Case
> BST average case = O(log n) for a random set of insertions.
> BST worst case = O(n) when elements inserted in SORTED (ascending or descending) order.
> Sorted insertion → completely skewed tree → O(n) all operations.
> Solution: Use SELF-BALANCING BSTs (AVL Tree, Red-Black Tree) → always O(log n).

---

## 🔷 SECTION 7: Inorder Traversal of BST = Sorted Output

### The Most Important BST Property for Exams:
```
INORDER TRAVERSAL of any BST gives elements in ASCENDING SORTED ORDER.

Why? Because Inorder visits: Left → Root → Right
In a BST: Left < Root < Right
So Inorder visits: smaller → medium → larger → sorted!

Example BST:
           8
          / \
         3   10
        / \    \
       1   6    14
          / \
         4   7

Inorder (Left→Root→Right):
  Go left to 3, go left to 1 → print 1
  Back to 3 → print 3
  Go right to 6, go left to 4 → print 4
  Back to 6 → print 6
  Go right to 7 → print 7
  Back to 8 → print 8
  Go right to 10 → print 10
  Go right to 14 → print 14

INORDER: 1, 3, 4, 6, 7, 8, 10, 14
         ↑ PERFECTLY SORTED! ↑
```

### Application: Tree Sort
```
Algorithm:
  Step 1: Insert all elements into a BST → O(n log n) average
  Step 2: Inorder traversal → outputs sorted array → O(n)
  Total: O(n log n) — same complexity as Merge Sort!

This is called TREE SORT.
```

---

## 🔷 SECTION 8: Preorder and Postorder of BST

### Preorder of BST (Root → Left → Right):
```
BST:
       8
      / \
     3   10
    / \    \
   1   6    14

Preorder: 8, 3, 1, 6, 10, 14

Use: Preorder of BST can be used to RECONSTRUCT the SAME BST.
     If you insert elements in Preorder order into an empty BST,
     you get the SAME tree back!

Preorder = [8, 3, 1, 6, 10, 14]
Insert 8 → root
Insert 3 → left of 8
Insert 1 → left of 3
Insert 6 → right of 3
Insert 10 → right of 8
Insert 14 → right of 10
→ SAME BST ✓
```

### 🚨 PYQ TRAP #5: Preorder Reconstructs BST
> Preorder traversal of a BST can uniquely reconstruct the original BST (insert in preorder order).
> Inorder alone cannot reconstruct a BST (it only gives sorted values, not structure).
> Preorder + Inorder together can reconstruct any Binary Tree (not just BST).

---

## 🔷 SECTION 9: Catalan Numbers — Number of Distinct BSTs

### The Question:
**"How many structurally distinct BSTs can be built with n distinct keys?"**

### Answer — Catalan Number Formula:
```
C(n) = (2n)! / [(n+1)! × n!]

Or recursively:
C(n) = Σ C(i-1) × C(n-i) for i = 1 to n
C(0) = 1 (empty tree)
C(1) = 1

Catalan Numbers:
n = 0 → C(0) = 1
n = 1 → C(1) = 1
n = 2 → C(2) = 2
n = 3 → C(3) = 5
n = 4 → C(4) = 14   ← MOST EXAM-TESTED VALUE
n = 5 → C(5) = 42
n = 6 → C(6) = 132
```

### WHY C(n) = Number of BSTs with n nodes:

**For n = 3, keys = {1, 2, 3}:**
```
Root = 1:          Root = 2:        Root = 3:
  1                    2                  3
   \                  / \                /
    2                1   3              2
     \                               /
      3                             1

Root=1, left=∅, right has {2,3}:
  Right subtree of 1 with {2,3} → 2 structures (C(2)=2)
  → 2 trees with root 1

Root=2, left={1}, right={3}:
  Only 1 structure → 1 tree

Root=3, left has {1,2}, right=∅:
  Left subtree of 3 with {1,2} → 2 structures (C(2)=2)
  → 2 trees with root 3

TOTAL = 2 + 1 + 2 = 5 = C(3) ✓
```

**For n = 4, C(4) = 14** (exam-tested — just memorise!)

### Visual Proof for n = 2 (C(2) = 2):
```
Keys {1, 2} → 2 distinct BSTs:

BST 1 (root=1):    BST 2 (root=2):
  1                    2
   \                  /
    2                1
```

### 🚨 PYQ TRAP #6: Catalan vs Count of Binary Trees
```
Number of distinct STRUCTURALLY DIFFERENT Binary Trees with n nodes = C(n) = (2n)!/(n+1)!n!

Number of distinct BSTs with n LABELED nodes (keys 1 to n) = C(n)
  → Same formula! Because for BST, key arrangement is fixed by BST property
    once structure is fixed.

Number of distinct LABELED Binary Trees (any arrangement) = n! × C(n)
  → Structure × key permutations

EXAM ASKS: "How many distinct BSTs with n=4?" → Answer: 14 (C(4))
```

### Catalan Numbers Quick Reference:
```
n:    0   1   2   3    4    5    6
C(n): 1   1   2   5   14   42  132

TRICK: "1, 1, 2, 5, 14, 42, 132..."
        Each is roughly 3× the previous one.
        C(4) = 14 ← must memorise for exam
```

---

## 🔷 SECTION 10: Balanced BST — AVL Trees (Brief Introduction)

### Why Self-Balancing Trees Were Needed:
```
Problem: If we insert sorted data into BST → skewed tree → O(n) operations
Solution: SELF-BALANCING BSTs — automatically maintain O(log n) height

AVL Tree (Adelson-Velsky and Landis, 1962):
  - First self-balancing BST
  - Balance Factor = Height(left subtree) - Height(right subtree)
  - For every node: balance factor must be -1, 0, or +1
  - If balance factor becomes ±2 after insert/delete → ROTATION performed

Red-Black Tree:
  - Less strict balancing (used in Java's TreeMap, C++ STL map)
  - Faster insertion/deletion than AVL (fewer rotations)

For BPSC exam:
  Know: AVL tree = self-balancing BST, Balance Factor = -1/0/+1
  Know: AVL operations = O(log n) always (no worst case O(n))
```

### Balance Factor Diagram:
```
BALANCED (AVL valid):    UNBALANCED (needs rotation):
      4                         4
     / \                       /
    2   6                     2
   / \   \                   /
  1   3   7                 1
BF(4) = 2-1 = 1 ✓          BF(4) = 2-0 = 2 ✗ → rotate!
BF(2) = 1-1 = 0 ✓
BF(6) = 0-1 = -1 ✓
```

---

## 🔷 SECTION 11: BST PYQ Scenarios — Common Exam Questions

### Scenario 1: Identify if a given tree is a valid BST
```
Check the GLOBAL property — not just parent-child:

     5
    / \
   1   4
      / \
     3   6

Is this a BST?
  Node 5: left {1} < 5 ✓, right {4,3,6} — but 4 < 5? Let's check...
  Node 4: BUT 4 is in the RIGHT subtree of 5, so 4 SHOULD be > 5!
  4 < 5 → VIOLATION! ✗

COMMON TRAP: People only check parent-child pairs.
Always check that ENTIRE LEFT subtree < node and ENTIRE RIGHT subtree > node.
```

### Scenario 2: Find the inorder successor
```
BST:
           8
          / \
         3   10
        / \    \
       1   6    14
          / \
         4   7

Find inorder successor of 6:
  Inorder of BST: 1, 3, 4, 6, 7, 8, 10, 14
  Next after 6 = 7
  → Inorder successor of 6 = 7
  
  Method: Go RIGHT from 6 → find LEFTMOST node
    Right of 6 = 7 → no left child → 7 is inorder successor ✓

Find inorder successor of 8:
  Next after 8 = 10
  Method: Go RIGHT from 8 → 10 → go LEFT... no left child of 10
    → 10 is inorder successor ✓
```

### Scenario 3: Height of BST given n nodes
```
Minimum height of BST with n nodes (balanced):
  h_min = ⌊log₂(n)⌋
  Example: n=7 → h_min = floor(log₂7) = floor(2.8) = 2

Maximum height of BST with n nodes (skewed):
  h_max = n - 1
  Example: n=7 → h_max = 6 (completely skewed)
```

---

## 🔷 SECTION 12: BST Mind Map — Visual Summary

```
                    BINARY SEARCH TREE
                            |
        ┌───────────────────┼─────────────────────┐
        |                   |                     |
  BST PROPERTY         OPERATIONS           IMPORTANT CONCEPTS
        |                   |                     |
  Left < Root < Right   Search O(log n)     Catalan Numbers:
  (EVERY node, not       Insert O(log n)    n=4 → 14 distinct BSTs
   just root!)           Delete O(log n)
        |                   |               Worst case = Skewed
  Inorder = Sorted      Worst case O(n):    tree (sorted insertion)
  (KEY FACT!)           Skewed tree
                            |               AVL Tree = Self-balancing
                       Deletion Cases:      BF = -1, 0, or +1
                       1. Leaf → remove
                       2. 1 child → replace
                       3. 2 children → inorder successor
```

---

# PART 2: GENERAL STUDIES
## ⚡ Physics — Electrical Power

---

## 🔷 SECTION 1: What is Electrical Power?

### The Core Idea:
**Electrical Power** is the rate at which electrical energy is consumed (or produced) by a device.

**In simple words:** How FAST does a device use electricity?

### Real-Life Intuition:
```
A 100W bulb and a 40W bulb are both switched on for 1 hour.
The 100W bulb:
  → Uses MORE electricity per second
  → Is BRIGHTER (converts more energy to light per second)
  → Will cost MORE on your electricity bill

"100W" means the bulb consumes 100 Joules of energy every SECOND.
```

### Basic Formula:
```
Power (P) = Energy (E) / Time (t)

Electrical Power = Work done by electric current per unit time

Unit of Power = Watt (W)
1 Watt = 1 Joule per second = 1 J/s

Named after: James Watt (Scottish inventor, steam engine)
```

---

## 🔷 SECTION 2: Three Key Formulas of Electrical Power

### Formula 1: P = V × I (Voltage × Current)
```
P = V × I

Where:
P = Power (in Watts, W)
V = Voltage / Potential Difference (in Volts, V)
I = Current (in Amperes, A)

Derivation:
  Power = Energy/Time = (Charge × Voltage) / Time
        = (Q/t) × V = I × V = VI

Example:
  A device operates at 220V and draws 2A current.
  P = 220 × 2 = 440 W
```

### Formula 2: P = I²R (Current squared × Resistance)
```
P = I²R

Where R = Resistance (in Ohms, Ω)

Derivation from P = VI and Ohm's Law (V = IR):
  P = VI = (IR) × I = I²R

Example:
  A resistor of 10Ω carries a current of 3A.
  P = 3² × 10 = 9 × 10 = 90 W

USE THIS when: Current (I) and Resistance (R) are given.
This is also the formula for HEAT generated in a resistor!
```

### Formula 3: P = V²/R (Voltage squared ÷ Resistance)
```
P = V²/R

Derivation from P = VI and Ohm's Law (I = V/R):
  P = VI = V × (V/R) = V²/R

Example:
  A device has resistance 50Ω and operates at 100V.
  P = 100² / 50 = 10000 / 50 = 200 W

USE THIS when: Voltage (V) and Resistance (R) are given.
```

### The Three Formulas Together:
```
┌─────────────────────────────────────────────┐
│                                             │
│    P = V × I    ← Use when V and I known   │
│    P = I² × R   ← Use when I and R known   │
│    P = V² / R   ← Use when V and R known   │
│                                             │
└─────────────────────────────────────────────┘

These come from combining:
  P = VI with Ohm's Law V = IR

All three are EQUALLY valid — use based on given data.
```

### Memory Trick — "VIR Triangle":
```
     P
    / \
   V   I
    \ /
     R

Ohm's Law: V = IR
Power (1): P = VI
Power (2): P = I²R   (substitute V=IR into P=VI)
Power (3): P = V²/R  (substitute I=V/R into P=VI)

Or remember: "PIV" → P = IV, then the two derived forms
```

---

## 🔷 SECTION 3: Units of Electrical Power and Energy

### Watt (W):
```
1 Watt = 1 Joule per second (1 J/s)
1 kilowatt (kW) = 1000 Watts
1 megawatt (MW) = 1,000,000 Watts = 10⁶ W
1 gigawatt (GW) = 10⁹ Watts

Typical power consumption:
  LED bulb:      5–10 W
  Tube light:    40 W
  Ceiling fan:   75 W
  Refrigerator:  150–200 W
  Air conditioner: 1000–2000 W (1–2 kW)
  Microwave:     800–1200 W
  Electric kettle: 1500–2000 W
  Electric iron: 1000–2000 W
```

### Kilowatt-Hour (kWh) — The Billing Unit:
```
Electricity bills are charged in kWh (kilowatt-hours) = 1 UNIT of electricity

1 kWh = 1 kilowatt × 1 hour = 1000 W × 3600 s = 3,600,000 J = 3.6 × 10⁶ J

Example:
  A 100W bulb runs for 10 hours.
  Energy = 100W × 10h = 1000 Wh = 1 kWh = 1 UNIT

If electricity costs ₹5 per unit:
  Cost = 1 unit × ₹5 = ₹5

  For a 2kW AC running 8 hours/day:
  Energy per day = 2 kW × 8 h = 16 kWh = 16 units
  Cost per day = 16 × ₹5 = ₹80
```

### Horsepower (HP):
```
1 HP = 746 Watts ≈ 0.746 kW

Used for: Motors, engines, pumps
Example: A 1 HP water pump = 746 W ≈ 0.75 kW
```

---

## 🔷 SECTION 4: Ohm's Law Review (Foundation for Power)

### Ohm's Law:
```
V = I × R

Where:
V = Voltage (Volts, V)
I = Current (Amperes, A)
R = Resistance (Ohms, Ω)

Stated: The current through a conductor is directly proportional
        to the voltage across it (at constant temperature).

VIR Triangle:
     V
    / \
   I   R

Cover what you want to find:
  Cover V → V = I × R
  Cover I → I = V / R
  Cover R → R = V / I
```

---

## 🔷 SECTION 5: Important Electrical Power Concepts

### Series vs Parallel Circuits — Power:
```
SERIES CIRCUIT:                    PARALLEL CIRCUIT:
R₁ and R₂ in series               R₁ and R₂ in parallel

Total R = R₁ + R₂                 1/R = 1/R₁ + 1/R₂
Same CURRENT through all           Same VOLTAGE across all
Total power = I²(R₁+R₂)           Total power = V²/R₁ + V²/R₂

In series: higher R → more power   In parallel: lower R → more power
           P = I²R (same I)                      P = V²/R (same V)

IMPORTANT:
  Series: P ∝ R (more resistance = more power wasted as heat)
  Parallel: P ∝ 1/R (less resistance = more power consumed)
```

### 🚨 PYQ TRAP #1: Series vs Parallel Power
```
Two bulbs rated 40W and 100W connected in:

SERIES: Same current flows through both.
  P = I²R → Higher R = higher power
  40W bulb has HIGHER resistance than 100W at same voltage.
  (Because P = V²/R → for same V, lower P means higher R)
  So 40W bulb GLOWS BRIGHTER in series! (counterintuitive!)

PARALLEL: Same voltage across both.
  P = V²/R → Lower R = higher power
  100W bulb has LOWER resistance → glows BRIGHTER in parallel.
  (Normal household scenario — bulbs in parallel, 100W is brighter)
```

### Joule's Law of Heating:
```
H = I² × R × t

Where H = Heat produced (Joules)
This is the HEAT version of P = I²R.

Applications:
  → Electric heater (deliberately generates heat)
  → Fuse wire (melts when I² R exceeds limit → circuit breaks)
  → Electric iron, electric kettle
  → Filament of incandescent bulb
```

### Power Rating of Appliances:
```
Every appliance has two ratings:
  POWER: e.g., 60W, 100W, 1500W
  VOLTAGE: e.g., 220V (in India)

If you connect a 220V appliance to 110V:
  P = V²/R
  At 110V: P = (110)²/R = half the normal power
  Appliance works at HALF power → dim bulb, slow heater

If you connect 110V appliance to 220V:
  P = (220)²/R = 4× the rated power
  Appliance overheats → may burn out/explode!
```

---

## 🔷 SECTION 6: Numerical Examples (Exam-Focused)

### Example 1: Basic Power Calculation
```
A current of 2A flows through a 10Ω resistor. Find power.
P = I²R = (2)² × 10 = 4 × 10 = 40 W
```

### Example 2: Using P = V²/R
```
A device operates at 240V with resistance 120Ω.
P = V²/R = (240)² / 120 = 57,600 / 120 = 480 W
```

### Example 3: Energy and Cost
```
A 1500W heater runs for 2 hours. Cost = ₹6 per unit (kWh).
Energy = 1500W × 2h = 3000 Wh = 3 kWh = 3 units
Cost = 3 × ₹6 = ₹18
```

### Example 4: Current from Power and Voltage
```
A 100W bulb operates at 200V. Find current.
P = VI → I = P/V = 100/200 = 0.5 A
```

### Example 5: Resistance from Power and Voltage
```
A 60W bulb operates at 220V. Find its resistance.
P = V²/R → R = V²/P = (220)²/60 = 48,400/60 ≈ 807 Ω
```

---

## 🔷 SECTION 7: Formula Summary Table

```
┌────────────────────────────────────────────────────────────────┐
│              ELECTRICAL POWER — FORMULA CARD                   │
├──────────────┬───────────────────────────┬────────────────────┤
│ Formula      │ Given                     │ Find               │
├──────────────┼───────────────────────────┼────────────────────┤
│ P = VI       │ Voltage + Current         │ Power              │
│ P = I²R      │ Current + Resistance      │ Power / Heat       │
│ P = V²/R     │ Voltage + Resistance      │ Power              │
│ I = P/V      │ Power + Voltage           │ Current            │
│ R = V²/P     │ Voltage + Power           │ Resistance         │
│ V = P/I      │ Power + Current           │ Voltage            │
│ H = I²Rt     │ Current+Resistance+Time   │ Heat generated     │
│ E = Pt       │ Power + Time              │ Energy (Joules)    │
│ E(kWh) = Pt  │ Power(kW) + Time(hours)   │ Energy units       │
├──────────────┼───────────────────────────┼────────────────────┤
│ 1 kWh = 3.6×10⁶ J │ 1 HP = 746 W        │ 1 W = 1 J/s       │
└────────────────────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 8: Applications & Real-Life Connection

| Application | Principle | Formula Used |
|-------------|-----------|-------------|
| Electric fuse | Melts when heat (I²Rt) exceeds threshold | P = I²R |
| Power transmission at high voltage | At high V, current I = P/V is LOW → less heat loss I²R | P = I²R (to minimize) |
| Electric heater | Deliberately converts electrical energy to heat | H = I²Rt |
| MCB (Miniature Circuit Breaker) | Trips when current exceeds rated value | P = I²R |
| Efficiency of motor | Output mechanical power / Input electrical power × 100% | P = VI |
| Solar panel rating | Rated in Watts peak (Wp) | P = VI |

### 🚨 PYQ TRAP #2: Power Transmission Uses High Voltage
```
FACT: Electricity is transmitted at HIGH VOLTAGE (11kV, 33kV, 132kV, 400kV)

WHY? To minimize energy loss in transmission wires.
  Power to transmit: P = constant
  P = VI → at high V, current I = P/V is SMALL
  Heat loss = I²R → small I → very SMALL heat loss!

If transmitted at LOW voltage:
  I must be LARGE (since P = VI and P is constant)
  Heat loss = I²R → large I → HUGE energy loss as heat in wires!

TRANSFORMERS:
  Step-UP transformer: Increases voltage for transmission (reduces I → reduces loss)
  Step-DOWN transformer: Decreases voltage for home use (220V for India)
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: BST Properties, Operations, Traversals, Complexity, Catalan Numbers

---

**Q1.** In a Binary Search Tree, for any node, which of the following is ALWAYS true?
(A) Left child > node > right child
(B) Left subtree values < node value < right subtree values
(C) Root is always the smallest element
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the time complexity of searching in a BALANCED Binary Search Tree with n nodes?
(A) O(n)
(B) O(n²)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the WORST CASE time complexity of searching in a Binary Search Tree?
(A) O(log n)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q4.** When does a BST degenerate to O(n) search time?
(A) When elements are inserted in random order
(B) When elements are inserted in sorted (ascending or descending) order
(C) When the tree has an odd number of nodes
(D) More than one of the above
(E) None of the above

---

**Q5.** The Inorder traversal of a Binary Search Tree produces:
(A) Values in reverse sorted order
(B) Values in the order of insertion
(C) Values in ascending sorted order
(D) More than one of the above
(E) None of the above

---

**Q6.** How many structurally distinct BSTs can be formed with 4 distinct keys?
(A) 5
(B) 42
(C) 14
(D) More than one of the above
(E) None of the above

---

**Q7.** What is the Catalan Number C(3)? (Number of distinct BSTs with 3 nodes)
(A) 3
(B) 14
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q8.** Consider BST with insertions: 5, 3, 7, 1, 4. What is the Inorder traversal?
(A) 5, 3, 7, 1, 4
(B) 1, 3, 4, 5, 7
(C) 5, 3, 1, 4, 7
(D) More than one of the above
(E) None of the above

---

**Q9.** Which traversal of a BST is used to reconstruct the SAME BST if elements are reinserted in that order?
(A) Inorder
(B) Postorder
(C) Preorder
(D) More than one of the above
(E) None of the above

---

**Q10.** The INORDER SUCCESSOR of a node in a BST is:
(A) The parent of the node
(B) The largest node in the left subtree
(C) The smallest node in the right subtree
(D) More than one of the above
(E) None of the above

---

**Q11.** In a BST with n nodes, what is the MINIMUM possible height (balanced case)?
(A) n - 1
(B) n/2
(C) ⌊log₂(n)⌋
(D) More than one of the above
(E) None of the above

---

**Q12.** In a BST with n nodes, what is the MAXIMUM possible height (skewed case)?
(A) log₂(n)
(B) n - 1
(C) n/2
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following trees is a valid BST?
```
(A)     5          (B)     5          (C)     5
       / \                / \                / \
      3   7              7   3              3   8
     / \                                   / \
    2   4                                 2   6
```
(A) Only Tree A
(B) Only Tree B
(C) Both A and C
(D) More than one of the above
(E) None of the above

---

**Q14.** What happens when you insert elements in descending order (10, 9, 8, 7, 6) into a BST?
(A) A balanced BST is formed
(B) A right-skewed BST is formed
(C) A left-skewed BST is formed
(D) More than one of the above
(E) None of the above

---

**Q15.** Which self-balancing BST uses a "Balance Factor" of -1, 0, or +1?
(A) Red-Black Tree
(B) B-Tree
(C) AVL Tree
(D) More than one of the above
(E) None of the above

---

**Q16.** In a BST deletion, when the node to be deleted has TWO children, which replacement strategy is used?
(A) Replace with the root of the right subtree only
(B) Replace with either inorder successor or inorder predecessor
(C) Delete both children first, then delete the node
(D) More than one of the above
(E) None of the above

---

**Q17.** The following is NOT a valid BST (identify the violation):
```
       10
      /  \
     5    15
    / \
   3   12
```
(A) 12 is in the left subtree of 10, but 12 > 10 → violation
(B) 5 is too small to be left child of 10
(C) 15 has no children → violation
(D) More than one of the above
(E) None of the above

---

**Q18.** For BST with keys 1, 2, 3 (in that insertion order), the tree formed is:
(A) Balanced BST with 2 as root
(B) Left-skewed BST
(C) Right-skewed BST with 1 as root
(D) More than one of the above
(E) None of the above

---

**Q19.** What is C(5) — the number of distinct BSTs with 5 nodes?
(A) 14
(B) 132
(C) 42
(D) More than one of the above
(E) None of the above

---

**Q20.** The INORDER PREDECESSOR of a node in a BST is:
(A) The smallest node in the right subtree
(B) The largest node in the left subtree
(C) The parent of the node
(D) More than one of the above
(E) None of the above

---

**Q21.** In a BST, where would you find the MINIMUM value?
(A) The root node
(B) The rightmost node
(C) The leftmost node
(D) More than one of the above
(E) None of the above

---

**Q22.** What is the time complexity of finding the minimum element in a balanced BST?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q23.** Tree Sort using a BST has what average time complexity?
(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q24.** The Catalan Number formula C(n) = (2n)! / [(n+1)! × n!] gives for n=2:
(A) 3
(B) 5
(C) 2
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following statements about BST is CORRECT?
(A) BST always has O(log n) search regardless of structure
(B) A BST with n nodes always has height ⌊log₂n⌋
(C) The inorder traversal of a BST gives elements in sorted ascending order
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Physics — Electrical Power

---

**Q26.** The SI unit of electrical power is:
(A) Joule
(B) Ampere
(C) Watt
(D) More than one of the above
(E) None of the above

---

**Q27.** The formula for electrical power in terms of voltage (V) and current (I) is:
(A) P = V / I
(B) P = V + I
(C) P = V × I
(D) More than one of the above
(E) None of the above

---

**Q28.** The formula P = I²R is derived by combining P = VI with:
(A) Faraday's Law
(B) Ohm's Law (V = IR)
(C) Coulomb's Law
(D) More than one of the above
(E) None of the above

---

**Q29.** A resistor of 5Ω carries a current of 4A. What is the power dissipated?
(A) 20 W
(B) 40 W
(C) 80 W
(D) More than one of the above
(E) None of the above

---

**Q30.** 1 kilowatt-hour (kWh) is equal to how many Joules?
(A) 1000 J
(B) 3.6 × 10⁵ J
(C) 3.6 × 10⁶ J
(D) More than one of the above
(E) None of the above

---

**Q31.** A 100W bulb is connected to 200V supply. What current flows through it?
(A) 20 A
(B) 2 A
(C) 0.5 A
(D) More than one of the above
(E) None of the above

---

**Q32.** Why is electricity transmitted over long distances at HIGH voltage?
(A) High voltage increases the speed of transmission
(B) High voltage reduces current, thereby reducing I²R heat losses in wires
(C) High voltage makes the wire more conductive
(D) More than one of the above
(E) None of the above

---

**Q33.** The unit of electrical energy commonly used in electricity bills is:
(A) Joule (J)
(B) Watt (W)
(C) Kilowatt-hour (kWh)
(D) More than one of the above
(E) None of the above

---

**Q34.** A device operates at 110V and has resistance 55Ω. What is the power?
(A) 110 W
(B) 440 W
(C) 220 W
(D) More than one of the above
(E) None of the above

---

**Q35.** 1 Horsepower (HP) is approximately equal to:
(A) 500 Watts
(B) 746 Watts
(C) 1000 Watts
(D) More than one of the above
(E) None of the above

---

**Q36.** Joule's Law of Heating states that the heat generated H = I²Rt. If current is DOUBLED (resistance and time constant), heat becomes:
(A) Double
(B) Triple
(C) Four times
(D) More than one of the above
(E) None of the above

---

**Q37.** A 2kW air conditioner runs for 5 hours. How many units (kWh) of electricity does it consume?
(A) 2.5 units
(B) 7 units
(C) 10 units
(D) More than one of the above
(E) None of the above

---

**Q38.** Two bulbs rated 40W and 100W are connected in PARALLEL to 220V mains. Which glows brighter?
(A) The 40W bulb
(B) The 100W bulb
(C) Both glow equally bright
(D) More than one of the above
(E) None of the above

---

**Q39.** Two bulbs rated 40W and 100W are connected in SERIES. Which glows brighter?
(A) The 100W bulb (lower resistance)
(B) The 40W bulb (higher resistance)
(C) Both glow equally bright
(D) More than one of the above
(E) None of the above

---

**Q40.** The formula P = V²/R is obtained by combining P = VI with:
(A) V = IR (substituting I = V/R)
(B) V = Q/C (capacitor equation)
(C) P = Fv (mechanical power)
(D) More than one of the above
(E) None of the above

---

**Q41.** Which of the following household appliances consumes the MOST power during normal operation?
(A) LED bulb (10W)
(B) Ceiling fan (75W)
(C) Air conditioner (1500W)
(D) More than one of the above
(E) None of the above

---

**Q42.** A fuse wire melts due to excessive current because of which principle?
(A) P = VI — high voltage burns the fuse
(B) H = I²Rt — excessive current generates too much heat
(C) Bernoulli's Principle — high flow rate breaks the wire
(D) More than one of the above
(E) None of the above

---

**Q43.** The resistance of a 100W, 200V bulb is:
(A) 200 Ω
(B) 400 Ω
(C) 100 Ω
(D) More than one of the above
(E) None of the above

---

**Q44.** Power is defined as:
(A) Force × displacement
(B) Energy / Time
(C) Mass × acceleration
(D) More than one of the above
(E) None of the above

---

**Q45.** In which of the following does electrical energy get converted PRIMARILY into heat energy?
(A) Electric motor
(B) Electric bulb (incandescent)
(C) Electric heater
(D) More than one of the above
(E) None of the above

---

**Q46.** If voltage across a resistor is doubled (resistance constant), the power consumed:
(A) Doubles
(B) Becomes 4 times (P = V²/R)
(C) Halves
(D) More than one of the above
(E) None of the above

---

**Q47.** The Step-UP transformer used in power transmission:
(A) Decreases voltage and increases current
(B) Increases voltage and decreases current
(C) Increases both voltage and current
(D) More than one of the above
(E) None of the above

---

**Q48.** A 60W bulb is switched on for 10 hours. Energy consumed in kWh is:
(A) 600 kWh
(B) 0.6 kWh
(C) 6 kWh
(D) More than one of the above
(E) None of the above

---

**Q49.** Who is the unit of power "Watt" named after?
(A) Nikola Tesla
(B) James Watt
(C) Alessandro Volta
(D) More than one of the above
(E) None of the above

---

**Q50.** In SERIES connection, if resistance R is increased (current I is constant), power P = I²R will:
(A) Decrease
(B) Stay the same
(C) Increase
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
| 1 | (B) | BST: left subtree ALL < node, right subtree ALL > node |
| 2 | (C) | Balanced BST search = O(log n) |
| 3 | (C) | Worst case (skewed tree) = O(n) |
| 4 | (B) | Sorted insertion → skewed tree → O(n) |
| 5 | (C) | Inorder of BST = ascending sorted order |
| 6 | (C) | C(4) = 14 (Catalan number for n=4) |
| 7 | (C) | C(3) = 5 |
| 8 | (B) | Inorder always gives sorted: 1,3,4,5,7 |
| 9 | (C) | Inserting Preorder sequence recreates same BST |
| 10 | (C) | Inorder successor = smallest in RIGHT subtree |
| 11 | (C) | Min height (balanced) = floor(log₂n) |
| 12 | (B) | Max height (skewed) = n-1 |
| 13 | (C) | A: valid BST ✓; C: valid BST ✓; B: 7 and 3 swapped, violates BST |
| 14 | (C) | Descending insertion → left-skewed (each new element smaller → goes left) |
| 15 | (C) | AVL Tree uses Balance Factor of -1, 0, or +1 |
| 16 | (B) | Replace with inorder successor OR inorder predecessor |
| 17 | (A) | 12 > 10 but 12 is in LEFT subtree of 10 → violation |
| 18 | (C) | 1→2(right of 1)→3(right of 2): right-skewed with root 1 |
| 19 | (C) | C(5) = 42 |
| 20 | (B) | Inorder predecessor = largest in LEFT subtree |
| 21 | (C) | Minimum = leftmost node (keep going left until NULL) |
| 22 | (B) | Go left until NULL: height steps = O(log n) for balanced BST |
| 23 | (B) | Insert n elements O(n log n) + inorder O(n) = O(n log n) |
| 24 | (C) | C(2) = (4)!/[3! × 2!] = 24/(6×2) = 24/12 = 2 |
| 25 | (C) | Inorder = sorted is the guaranteed BST property |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | SI unit of power = Watt (W) |
| 27 | (C) | P = V × I (basic power formula) |
| 28 | (B) | Ohm's Law V=IR → P=VI=(IR)×I=I²R |
| 29 | (C) | P = I²R = 4² × 5 = 16 × 5 = 80 W |
| 30 | (C) | 1 kWh = 1000 × 3600 = 3.6 × 10⁶ J |
| 31 | (C) | I = P/V = 100/200 = 0.5 A |
| 32 | (B) | High V → low I → I²R heat loss minimized |
| 33 | (C) | Electricity bills in kWh (units) |
| 34 | (C) | P = V²/R = (110)²/55 = 12100/55 = 220 W |
| 35 | (B) | 1 HP = 746 W |
| 36 | (C) | H = I²Rt → double I → (2I)²Rt = 4I²Rt = 4× original |
| 37 | (C) | E = 2kW × 5h = 10 kWh = 10 units |
| 38 | (B) | Parallel: same V, P=V²/R; 100W has lower R → more power → brighter |
| 39 | (B) | Series: same I, P=I²R; 40W has higher R (as rated lower at same V) → brighter |
| 40 | (A) | P=VI, substitute I=V/R: P=V×(V/R)=V²/R |
| 41 | (C) | AC at 1500W consumes most power |
| 42 | (B) | Fuse melts due to H=I²Rt — excessive current generates too much heat |
| 43 | (B) | R = V²/P = (200)²/100 = 40000/100 = 400 Ω |
| 44 | (B) | Power = Energy / Time |
| 45 | (C) | Electric heater converts electrical energy primarily to heat |
| 46 | (B) | P = V²/R → double V → P becomes 4V²/R = 4× original |
| 47 | (B) | Step-UP: increases voltage, decreases current (P=VI constant) |
| 48 | (B) | E = 60W × 10h = 600 Wh = 0.6 kWh |
| 49 | (B) | Watt named after James Watt (Scottish inventor) |
| 50 | (C) | P = I²R; R increases, I constant → P increases proportionally |

---
---

# 🔁 DAY 25 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Binary Search Tree (BST)

### The ONE Rule That Defines BST:
```
For EVERY node in BST:
  ALL values in LEFT subtree  <  node value
  ALL values in RIGHT subtree >  node value

This is GLOBAL — applies to every node, not just root!
(Most exam traps violate this for a deeper node)
```

### Complexity Quick Reference:
```
Operation    | Balanced BST | Skewed BST  | Why skewed = O(n)
-------------|--------------|-------------|-------------------
Search       | O(log n)     | O(n)        | Height = n → n comparisons
Insert       | O(log n)     | O(n)        | Traverse full height
Delete       | O(log n)     | O(n)        | Traverse full height
Inorder      | O(n)         | O(n)        | Must visit all nodes

Skewed BST happens when: Sorted (ascending or descending) data inserted
Solution: Use AVL Tree (Balance Factor -1/0/+1 → always O(log n))
```

### The 3 Traversal Key Facts:
```
INORDER  (L→Root→R): SORTED output from BST ← most tested!
PREORDER (Root→L→R): First element = ROOT; Reinserting in preorder = same BST
POSTORDER(L→R→Root): Root is ALWAYS LAST

Inorder of BST = ascending sorted order = ALWAYS TRUE
```

### Deletion — 3 Cases:
```
Case 1: Leaf node       → Simply remove
Case 2: One child       → Replace with that child
Case 3: Two children    → Replace with INORDER SUCCESSOR (smallest in right subtree)
                          OR INORDER PREDECESSOR (largest in left subtree)

Inorder Successor  = leftmost node in RIGHT subtree
Inorder Predecessor = rightmost node in LEFT subtree
```

### Catalan Numbers — MUST MEMORISE:
```
n:    1   2   3    4    5    6
C(n): 1   2   5   14   42  132

C(4) = 14 ← THE exam answer for "distinct BSTs with 4 nodes"
C(3) = 5  ← Second most asked
C(n) = (2n)! / [(n+1)! × n!]

REMEMBER: 1, 2, 5, 14, 42... (roughly triple each time)
```

### 4 BST PYQ Traps:
```
TRAP 1: BST property is GLOBAL (all of left subtree < node, not just left child)
TRAP 2: Sorted insertion → skewed tree → O(n) worst case (not O(log n)!)
TRAP 3: Inorder traversal gives SORTED output — most asked BST fact
TRAP 4: Preorder sequence → inserting in that order → SAME BST reconstructed
```

### BST Min and Max:
```
MINIMUM = leftmost node (keep going left until NULL)
MAXIMUM = rightmost node (keep going right until NULL)
Both are O(log n) in balanced BST, O(n) in skewed BST
```

---

## ⚡ RAPID FIRE — Electrical Power

### THE Power Formula Triangle:
```
         P
        / \
       V   I
        \ /
         R (from Ohm's Law)

P = V×I     (given V and I)
P = I²×R    (given I and R)  ← also = Heat generated per second
P = V²/R    (given V and R)

From Ohm's Law: V = I×R → I = V/R → R = V/I
```

### Units Reference:
```
Power:   Watt (W) = Joule/second = J/s
Energy:  Joule (J) or kilowatt-hour (kWh)
1 kWh   = 1000 W × 3600 s = 3.6 × 10⁶ J = 1 "unit" in electricity bill
1 HP    = 746 W
Voltage: Volt (V)
Current: Ampere (A)
Resistance: Ohm (Ω)
```

### Key Effects and Applications:
```
P = I²R → more I through resistance → more heat (Joule heating)
  → Fuse wire melts (safety device) → MCB trips
  → Electric heater, electric iron, kettle all use this

P = V²/R → appliance at rated voltage works at rated power
  → Over-voltage (2× voltage) → 4× power → burns out!
  → Under-voltage (half voltage) → ¼ power → weak performance

Series circuit: same I → higher R = higher power = brighter bulb
Parallel circuit: same V → lower R = higher power = brighter bulb
```

### Power Transmission:
```
HIGH VOLTAGE transmission → LOW CURRENT → LOW I²R losses in wire
Step-UP transformer at power station (increases V, decreases I)
Step-DOWN transformer at substation (decreases V to 220V for homes)
```

### 3 Calculation Templates:
```
1. Find current: I = P/V
   "100W, 200V bulb" → I = 100/200 = 0.5A

2. Find resistance: R = V²/P
   "60W, 220V bulb" → R = (220)²/60 = 48400/60 ≈ 807Ω

3. Find energy cost: E(kWh) = P(kW) × t(hours)
   "2kW AC, 5 hours" → E = 2×5 = 10 kWh = 10 units
```

### PYQ Traps — Power:
```
TRAP 1: 40W bulb in SERIES glows BRIGHTER than 100W (higher R, same I)
TRAP 2: 100W bulb in PARALLEL glows BRIGHTER than 40W (lower R, same V)
TRAP 3: Fuse melts due to H=I²Rt — heat, NOT voltage
TRAP 4: Power unit = Watt; Energy unit = kWh (for billing) — don't mix
TRAP 5: Doubling voltage → 4× power (P∝V²); Doubling current → 4× power (P∝I²)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. BST: ALL left subtree values < node < ALL right subtree values (GLOBAL rule, not just parent-child)
2. Inorder of BST = sorted ascending; Preorder first element = root; C(4)=14 distinct BSTs with 4 nodes
3. BST worst case O(n) when sorted data inserted (skewed tree); balanced BST = O(log n); AVL tree always O(log n)
4. Electrical Power: P=VI=I²R=V²/R; doubling V → 4× power; doubling I → 4× power (both squared relations)
5. Series: same I → higher R bulb brighter (P=I²R); Parallel: same V → lower R bulb brighter (P=V²/R); transmission at high V to minimize I²R loss

---

*Next: Day 26 — Heaps (Max Heap, Min Heap, Heapify, Heap Sort) | GS: Indian History — Harappan & Vedic Civilization*
