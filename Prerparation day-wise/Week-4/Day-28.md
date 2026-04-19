# 📅 BPSC TRE 4.0 — DAY 28 COMPLETE REVISION MODULE
### DSA Mega-Revision (Day 22–27) + GS Revision + 50 PYQ-Level MCQs
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1 hr): CS Revision — Linked Lists + Trees + BST
> - Mid-Morning (1 hr): CS Revision — Balanced Trees + Graphs + BFS/DFS
> - Afternoon (45 min): GS Revision — Polity + Biology + Physics
> - Evening (1 hr): Solve all 50 PYQ-level MCQs
> - Night (30 min): "Last 1-hour before exam" ultra-crisp card review

---

# PART 1: CS MEGA-REVISION
## 📘 Day 22–27 — All DSA Topics at a Glance

---

## ⚡ BLOCK 1: LINKED LISTS (Day 22–23)

---

### 🔷 Singly Linked List (SLL) — Crisp Rules

```
STRUCTURE: HEAD → [data|next] → [data|next] → [data|NULL]
           HEAD = pointer to first node
           NULL = end of list
           Memory: NON-CONTIGUOUS (nodes scattered in RAM)

NODE: struct Node { int data; Node* next; };
```

**Complexity Quick-Fire:**
```
Operation              | Time  | Reason
-----------------------|-------|------------------------------------
Access/Search          | O(n)  | Must traverse from HEAD (no random access)
Insert at BEGINNING    | O(1)  | Only 2 pointer changes → NO traversal
Insert at END (no tail)| O(n)  | Must traverse to find last node
Insert at END (tail)   | O(1)  | Direct access via tail pointer
Insert at MIDDLE       | O(n)  | Traverse to position k-1
Delete at BEGINNING    | O(1)  | Advance HEAD (no traversal)
Delete at END          | O(n)  | Traverse to second-to-last node
Delete at MIDDLE       | O(n)  | Traverse to position k-1
Traversal/Length       | O(n)  | Visit all n nodes
```

**Middle Insert — Critical Order:**
```
ALWAYS: newNode.next = curr.next  ← FIRST (connect new to rest)
        curr.next = newNode       ← SECOND (connect prev to new)
Wrong order → rest of list LOST permanently!
```

**Memory Overhead:** SLL: [data | next_ptr] = data + 1 pointer per node.

---

### 🔷 Doubly Linked List (DLL) — Crisp Rules

```
STRUCTURE: NULL ← [prev|data|next] ↔ [prev|data|next] → NULL
           HEAD.prev = NULL (first node)
           TAIL.next = NULL (last node)
           NODE: prev + data + next (3 fields)
```

**DLL KEY ADVANTAGE over SLL:**
```
End deletion: O(1) in DLL (TAIL.prev gives second-to-last directly)
              O(n) in SLL (must traverse to second-to-last)

End deletion O(1) IS THE MOST TESTED DLL FACT.
```

**Middle Insert — 4 Pointer Updates:**
```
1. newNode.next = nextNode
2. newNode.prev = prevNode
3. prevNode.next = newNode
4. nextNode.prev = newNode
(4 updates in DLL vs 2 in SLL)
```

**Deque with DLL:** All 4 operations (insert/delete front/rear) = O(1).

---

### 🔷 Circular Linked List (CLL) — Crisp Rules

```
CSLL: HEAD → [d|→] → [d|→] → [d|→] ─── (last.next = HEAD, no NULL)
CDLL: HEAD ↔ [←|d|→] ↔ [←|d|→] ↔ (circular + bidirectional)
```

**CLL Key Rules:**
```
→ Last node's NEXT = HEAD (not NULL) — no NULL pointer exists in any node
→ Traversal ends when curr == HEAD (not curr == NULL)
→ curr == NULL → INFINITE LOOP (most common CLL mistake!)
→ Used for: Round-robin CPU scheduling, circular buffers
```

---

### 🔷 SLL vs DLL vs CLL — One Master Table

```
Feature           | SLL              | DLL                | CLL (Singly)
------------------|------------------|--------------------|------------------
Pointers/node     | 1 (next)         | 2 (prev+next)      | 1 (next)
NULL at end?      | YES              | YES (both ends)    | NO
Backward travel   | ✗ NOT POSSIBLE   | ✓ YES              | ✗ NOT POSSIBLE
End deletion      | O(n)             | O(1) ← KEY!        | O(n)
Memory/node       | LEAST            | MOST               | LEAST (same as SLL)
Insert begin      | O(1)             | O(1)               | O(1) with tail ptr
Deque support     | POOR             | EXCELLENT ← KEY!   | POOR
Use case          | Simple lists     | Music player, undo | Round-robin, buffer
No cycle?         | YES (ends NULL)  | YES (ends NULL)    | NO (it IS a circle)
```

---

## ⚡ BLOCK 2: TREES (Day 24)

---

### 🔷 Tree Terminology — One-Line Each

```
ROOT:      Topmost node, NO parent, exactly 1 per tree
LEAF:      Node with NO children (degree = 0)
EDGE:      Connection between parent and child
DEGREE:    Number of CHILDREN of a node
HEIGHT:    Edges from node DOWN to deepest leaf (height of leaf = 0)
DEPTH:     Edges from ROOT DOWN to the node (depth of root = 0)
LEVEL:     Same as depth (root at level 0 or 1 depending on convention)
SUBTREE:   Any node + all its descendants
SIBLINGS:  Nodes sharing the SAME parent
```

**Key Formulas:**
```
Edges in tree          = n - 1    (n = total nodes; ALWAYS TRUE)
Max nodes at level k   = 2^k      (0-indexed; for Binary Tree)
Perfect BT total nodes = 2^(h+1) - 1  (h = height)
Perfect BT leaf nodes  = 2^h
Full BT: Leaves        = Internal nodes + 1
Left child of node i   = 2i + 1  (0-indexed array)
Right child of node i  = 2i + 2  (0-indexed array)
Parent of node i       = (i-1)/2
```

---

### 🔷 Binary Tree Types — 5 Rules in 5 Lines

```
FULL:      Every node has 0 OR 2 children (NEVER 1). Leaves = Internal + 1.
COMPLETE:  All levels filled EXCEPT possibly last; last fills LEFT→RIGHT.
PERFECT:   All leaves at SAME level; all internal nodes have 2 children.
           A perfect BT is BOTH full AND complete.
BALANCED:  |Height(left) - Height(right)| ≤ 1 at EVERY node.
SKEWED:    All nodes have only 1 child → degenerates to linked list → O(n).
```

**Hierarchy:** Perfect ⊂ Complete; Perfect ⊂ Full.

---

### 🔷 Tree Traversals — The 4 Orders

**Master Tree for Traversals:**
```
         A
        / \
       B   C
      / \   \
     D   E   F
```

```
PREORDER  (Root→L→R):  A, B, D, E, C, F   [Root FIRST]
INORDER   (L→Root→R):  D, B, E, A, C, F   [Root MIDDLE]
POSTORDER (L→R→Root):  D, E, B, F, C, A   [Root LAST]
LEVEL-ORDER (BFS):     A, B, C, D, E, F   [Level by level]
```

**Traversal Memory Tricks:**
```
PRE-order:   ROOT comes BEFORE (PRE) children
IN-order:    ROOT comes IN the middle (left-ROOT-right)
POST-order:  ROOT comes AFTER (POST) children / Root is ALWAYS LAST
LEVEL-order: Uses QUEUE; visits level 0, then 1, then 2...
```

**Critical BST Rule:** INORDER of BST = SORTED ASCENDING ORDER.
**BFS uses QUEUE; DFS (Pre/In/Post) uses STACK (recursion).**

---

## ⚡ BLOCK 3: BINARY SEARCH TREE (Day 25)

---

### 🔷 BST — 10 Essential Rules

```
RULE 1: ALL values in LEFT subtree < node value (GLOBAL, not just direct child)
RULE 2: ALL values in RIGHT subtree > node value (GLOBAL, not just direct child)
RULE 3: Inorder traversal → SORTED ASCENDING output (most tested BST fact)
RULE 4: First element of Preorder = ROOT of BST
RULE 5: Sorted insertion → SKEWED tree → O(n) worst case
RULE 6: Balanced BST → O(log n) for search/insert/delete
RULE 7: MINIMUM = leftmost node (keep going left until NULL)
RULE 8: MAXIMUM = rightmost node (keep going right until NULL)
RULE 9: Inorder Successor = smallest in RIGHT subtree = leftmost in right subtree
RULE 10: Inorder Predecessor = largest in LEFT subtree = rightmost in left subtree
```

**Deletion Cases:**
```
CASE 1: Leaf node → simply remove
CASE 2: One child → replace node with its child
CASE 3: Two children → replace with INORDER SUCCESSOR (or predecessor)
```

**Complexity:**
```
             Balanced BST    Skewed BST
Search:      O(log n)        O(n)
Insert:      O(log n)        O(n)
Delete:      O(log n)        O(n)
Inorder:     O(n)            O(n)   (always O(n) — must visit all)
```

**Catalan Numbers (Number of distinct BSTs with n nodes):**
```
n:    1   2   3    4    5    6
C(n): 1   2   5   14   42  132

C(4) = 14 ← MEMORISE THIS FOR EXAM
Formula: C(n) = (2n)! / [(n+1)! × n!]
```

---

## ⚡ BLOCK 4: BALANCED TREES & RED-BLACK (Day 26)

---

### 🔷 AVL Tree — 5 Rules

```
RULE 1: AVL = BST + Balance Factor (BF) constraint
RULE 2: BF = Height(left) - Height(right) at EVERY node
RULE 3: Valid BF = -1, 0, or +1 (any BF of ±2 → violation)
RULE 4: Violation → ROTATION to fix (4 types: LL, RR, LR, RL)
RULE 5: All operations O(log n) ALWAYS (height ≤ 1.44 log₂n)
```

### 🔷 Red-Black Tree — 5 Properties (MEMORISE)

```
P1: Every node is RED or BLACK
P2: ROOT is always BLACK ← most tested
P3: All NULL leaf pointers = BLACK
P4: No two consecutive RED nodes (no R-R parent-child)
P5: All paths from any node to NULL descendants have SAME number of BLACK nodes
    (Black-Height = uniform across all paths)

Max height ≤ 2 × log₂(n+1) → O(log n) guaranteed
New inserted node = RED (then fix violations if any)
Max 2 rotations per INSERT; max 3 rotations per DELETE
```

**AVL vs Red-Black:**
```
                AVL               Red-Black
Balance:        STRICT (BF ≤ 1)  APPROXIMATE (2×black-height)
Search:         FASTER            Slightly slower
Insert/Delete:  SLOWER            FASTER (fewer rotations)
Used in:        Read-heavy apps   Java TreeMap, C++ STL, Linux kernel
Invented:       1962              1972
```

---

### 🔷 Spanning Tree

```
DEFINITION: Subgraph with ALL N vertices, EXACTLY N-1 edges, NO cycles, CONNECTED
KEY FORMULA: Graph with N vertices → Spanning tree has N-1 edges
Cayley's Formula: Complete graph Kₙ has n^(n-2) spanning trees

MST = Minimum total weight spanning tree
Kruskal's: Sort edges, add cheapest non-cycle edge → O(E log E) → SPARSE graphs
Prim's:    Grow from vertex, add cheapest connecting edge → O(E log V) → DENSE graphs
Both: GREEDY approach
MST may NOT be unique (if edge weights are equal)
```

---

## ⚡ BLOCK 5: GRAPHS + BFS + DFS (Day 27)

---

### 🔷 Graph Basics — Quick Reference

```
Graph G = (V, E): V = vertices, E = edges
Undirected: A-B means A→B and B→A
Directed (Digraph): A→B means only one way
Weighted: Edges have numerical values
Complete Kₙ: n(n-1)/2 edges; n^(n-2) spanning trees
Handshaking Lemma: Σ(all degrees) = 2E (sum of ALL vertex degrees = 2× edges)
DAG = Directed Acyclic Graph (no cycles; used for task scheduling)
Connected: path between every pair of vertices
```

**Representations:**
```
Adjacency Matrix: V×V array; O(V²) space; O(1) edge check; DENSE graphs
Adjacency List:   O(V+E) space; O(degree) edge check; SPARSE graphs (DEFAULT)
```

---

### 🔷 BFS vs DFS — The Ultimate Comparison

```
Feature            | BFS                      | DFS
-------------------|--------------------------|---------------------------
Data Structure     | QUEUE (FIFO)             | STACK (LIFO) / Recursion
Traversal          | Level by level           | Deep first, then backtrack
Space              | O(V)                     | O(V)
Time               | O(V+E)                   | O(V+E)
Shortest path?     | YES (unweighted only)    | NO
Cycle detection?   | Yes                      | YES (primary/natural)
Topological sort?  | No                       | YES
Backtracking?      | No                       | YES
Best application   | Shortest path, crawling  | Cycle detect, topo sort
Tree traversal     | Level-Order              | Pre/In/Postorder
```

**BFS Step-By-Step:** Enqueue start → While queue not empty: dequeue, process, enqueue unvisited neighbours.
**DFS Step-By-Step:** Call DFS(u) → mark visited → for each unvisited neighbour v: call DFS(v).

---

### 🔷 Complexity Summary — All Data Structures

```
Data Structure  | Access  | Search  | Insert (best) | Delete (best)
----------------|---------|---------|---------------|---------------
Array           | O(1)    | O(n)    | O(1) at end   | O(1) at end
SLL             | O(n)    | O(n)    | O(1) at begin | O(1) at begin
DLL             | O(n)    | O(n)    | O(1) at begin | O(1) at end!
BST (balanced)  | O(log n)| O(log n)| O(log n)      | O(log n)
AVL/RB Tree     | O(log n)| O(log n)| O(log n)      | O(log n)
Graph (BFS/DFS) | O(V+E)  | O(V+E)  | O(1)          | O(V+E)
```

---

# PART 2: GS MEGA-REVISION
## 🏛️ Day 22–27 — Polity + Science Complete Revision

---

## ⚡ BLOCK 6: FUNDAMENTAL RIGHTS (Day 22)

---

### Quick Reference Table:

```
Part III, Articles 12–35 | Justiciable (courts enforce) | Borrowed from: US Bill of Rights

RIGHT                      ARTICLES    KEY FACT
---------------------------|-----------|----------------------------------------
Right to Equality          | 14–18     | Art.17: Untouchability abolished (punishable)
Right to Freedom           | 19–22     | Art.19: 6 freedoms (was 7; 19(1)(f) removed)
Right against Exploitation | 23–24     | Art.24: No child labour below 14 in hazardous
Right to Religion          | 25–28     | Art.25: Profess+Practise+Propagate religion
Cultural & Educational     | 29–30     | Art.30: Minorities establish educational institutions
Right to Const. Remedies   | Art.32    | "Heart and Soul" — Ambedkar
```

**Article 19 — 6 Freedoms (after removing 19(1)(f) by 44th Amendment):**
```
19(1)(a): Freedom of SPEECH & EXPRESSION ← most tested
19(1)(b): ASSEMBLE peacefully without arms
19(1)(c): Form ASSOCIATIONS and UNIONS
19(1)(d): MOVE freely throughout India
19(1)(e): RESIDE and SETTLE anywhere in India
19(1)(g): PRACTISE any profession/trade/business

REMOVED: 19(1)(f) = Right to acquire/hold/dispose property (44th Amendment 1978)
```

**5 Writs — "H M P C Q":**
```
H = Habeas Corpus  → Release illegally detained person
M = Mandamus       → Direct public authority to perform duty
P = Prohibition    → Stop inferior court from exceeding jurisdiction
C = Certiorari     → Quash order of inferior court
Q = Quo Warranto  → Challenge authority to hold public office
```

**Emergency Rules:**
```
Articles 20 & 21 → CANNOT be suspended even during National Emergency (44th Amendment)
Article 19 freedoms → CAN be suspended during National Emergency
Article 32 → CAN be suspended under Article 359
Article 226 (HC writs) → CANNOT be suspended
```

**Critical Article Facts:**
```
Art.12:  Defines "State" (FRs protect against the State)
Art.13:  Laws violating FRs = VOID (Judicial Review)
Art.17:  Untouchability abolished — unique: applies to private persons too
Art.20:  Ex-post facto law; Double Jeopardy; Self-incrimination — 3 protections
Art.21:  Life & Personal Liberty (most expansive FR — includes privacy, livelihood)
Art.21A: Free education 6-14 years (86th Amendment 2002 → RTE Act 2009)
Art.22:  Arrested → inform grounds; lawyer; produce before magistrate within 24 hrs
Art.44:  Uniform Civil Code (DPSP, not FR — very frequently confused!)
```

---

## ⚡ BLOCK 7: DPSP (Day 23)

---

```
Part IV, Articles 36–51 | NON-Justiciable | Borrowed from: IRISH CONSTITUTION (1937)
Goal: WELFARE STATE | Positive duties on the State | Harmony with FRs (Minerva Mills 1980)

TYPE          ARTICLES       KEY CONTENT
--------------|--------------|-----------------------------------------------
SOCIALIST     | 38,39,39A,   | Equal pay (39d), free legal aid (39A),
              | 41,42,43,43A | living wage (43), workers in mgmt (43A)
GANDHIAN      | 40,43,43B,   | Village Panchayats (40), cow protection (48),
              | 46,47,48     | prohibition of liquor (47), SC/ST welfare (46)
LIBERAL-INT   | 44,48A,49,   | UCC (44), environment (48A), nat. monuments (49),
              | 50,51        | Judiciary-Executive separation (50), world peace (51)
```

**Must-Know DPSP Articles:**
```
Art.39(d): EQUAL PAY for equal work ← most tested DPSP
Art.40:    Village PANCHAYATS ← most Gandhian principle
Art.44:    UNIFORM CIVIL CODE (most controversial)
Art.47:    Raise nutrition + PROHIBIT LIQUOR
Art.48:    Protect COWS + modernise agriculture
Art.48A:   ENVIRONMENT protection (added 42nd Amendment 1976)
Art.50:    Separate JUDICIARY from EXECUTIVE
Art.51:    INTERNATIONAL PEACE
```

**Amendment-DPSP Links:**
```
42nd Amendment 1976: Added Art.39A (free legal aid), 43A (workers), 48A (environment)
44th Amendment 1978: Added Art.38(2) — minimise inequality
97th Amendment 2011: Added Art.43B — cooperative societies
```

**FR vs DPSP — One-Line:**
```
FR = Justiciable, Negative duties, American origin, Part III, Art.12–35
DPSP = Non-justiciable, Positive duties, Irish origin, Part IV, Art.36–51
```

---

## ⚡ BLOCK 8: BIOLOGY REVISION (Day 26–27)

---

### Asexual Reproduction Methods:

```
METHOD          | ORGANISM (Examples)         | Key Feature
----------------|-----------------------------|---------------------------------
Binary Fission  | AMOEBA, Bacteria            | Parent splits into 2 EQUAL halves
Budding         | YEAST, HYDRA                | Outgrowth detaches from parent
Fragmentation   | SPIROGYRA, Planaria         | Fragment grows into new organism
Spore Formation | RHIZOPUS (bread mould)      | Spores dispersed, germinate
Vegetative Prop.| Potato (tuber), Ginger      | Vegetative parts → new plants
Regeneration    | PLANARIA, Starfish, Hydra   | Lost parts regrow completely
```

### Underground Modified Stems:
```
RHIZOME → Ginger, Turmeric (horizontal underground stem with nodes)
TUBER   → Potato (swollen tip; "eyes" = nodes with buds)
BULB    → Onion, Garlic (fleshy scale leaves around disc-like stem)
CORM    → Colocasia/Arbi (solid vertical underground stem)
STOLON  → Strawberry (horizontal ABOVE-GROUND runner)
```

**Ginger PYQ Rule:** Ginger = RHIZOME = underground STEM (NOT root). Most call it "ginger root" — this is WRONG.

### Yeast Key Facts:
```
Kingdom: FUNGI | Unicellular | Eukaryote | Chitin cell wall
Reproduction: BUDDING (not binary fission)
Fermentation: C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ (ANAEROBIC)
Uses: Bread (CO₂ raises dough), Beer/Wine (ethanol produced)
```

### Human Reproduction Quick Facts:
```
Fertilisation: In FALLOPIAN TUBE (not uterus!) ← PYQ trap
Implantation: Endometrium of UTERUS
Gestation: ~9 months (38–40 weeks)
Ovulation: ~Day 14 of menstrual cycle (triggered by LH surge)
Gametes: Sperm(n) + Egg(n) → Zygote(2n)
Meiosis produces gametes; Mitosis drives growth after fertilisation
Placenta: Nourishes foetus + acts as barrier
```

---

## ⚡ BLOCK 9: PHYSICS REVISION (Day 24–25)

---

### Bernoulli's Principle:
```
RULE: FAST FLUID → LOW PRESSURE | SLOW FLUID → HIGH PRESSURE
Formula: P + ½ρv² + ρgh = constant (along a streamline)
Simplified (horizontal): P + ½ρv² = constant
Applies to: Ideal, incompressible, non-viscous, steady, laminar flow

TOP APPLICATIONS:
  Airplane wing:    Curved top → fast air → low pressure above → LIFT
  Venturi meter:    Narrow section → fast flow → measure flow speed
  Perfume spray:    Fast air → low pressure → sucks liquid up
  Bunsen burner:    Fast gas → low pressure → draws in air
  Roof in storm:    Fast wind above → low pressure → roof lifted off
  Cricket swing:    Magnus Effect → spinning ball → curve

TRAP: Hydraulic jack = PASCAL'S LAW (not Bernoulli!)
      Torricelli's theorem (v=√2gh) = special case of Bernoulli
```

### Electrical Power:
```
THREE FORMULAS:
  P = V × I    (given Voltage and Current)
  P = I² × R   (given Current and Resistance) ← Heat/Joule heating
  P = V² / R   (given Voltage and Resistance)

UNITS: Power = Watt (W) | Energy = kWh (billing unit)
1 kWh = 3.6 × 10⁶ J = 1 "UNIT" on electricity bill
1 HP = 746 W

SERIES vs PARALLEL — THE PYQ TRAP:
  Series (same I):   40W bulb has HIGHER R → glows BRIGHTER (P=I²R, more R = more P)
  Parallel (same V): 100W bulb has LOWER R → glows BRIGHTER (P=V²/R, less R = more P)

TRANSMISSION: High voltage → Low current → Low I²R loss in wires
Step-UP transformer: ↑V, ↓I | Step-DOWN: ↓V to 220V for homes

KEY CALCULATIONS:
  Find I: I = P/V
  Find R: R = V²/P
  Find energy: E(kWh) = P(kW) × t(hours)
  Doubling V → 4× power (P∝V²)
  Doubling I → 4× power (P∝I²)
```

---

# PART 3: VISUAL REVISION TABLES

---

## 📊 TABLE 1: All Linked List Operations at a Glance

```
┌─────────────────────────┬─────────┬─────────┬──────────┐
│ Operation               │   SLL   │   DLL   │  CSLL    │
├─────────────────────────┼─────────┼─────────┼──────────┤
│ Access by index         │  O(n)   │  O(n)   │  O(n)    │
│ Search                  │  O(n)   │  O(n)   │  O(n)    │
│ Insert at BEGINNING     │  O(1)   │  O(1)   │  O(1)*   │
│ Insert at END (tail)    │  O(1)*  │  O(1)   │  O(1)*   │
│ Insert at END (no tail) │  O(n)   │  O(n)   │  O(n)    │
│ Insert at MIDDLE        │  O(n)   │  O(n)   │  O(n)    │
│ Delete at BEGINNING     │  O(1)   │  O(1)   │  O(1)*   │
│ Delete at END (tail)    │  O(n)   │ O(1)!!! │  O(n)    │
│ Delete at MIDDLE        │  O(n)   │  O(n)   │  O(n)    │
│ Backward traversal      │   ✗     │   ✓     │   ✗      │
│ Pointers per node       │    1    │    2    │    1     │
│ NULL in list?           │   YES   │  YES    │   NO     │
└─────────────────────────┴─────────┴─────────┴──────────┘
* = requires tail pointer
DLL DELETE AT END = O(1) is the KEY ADVANTAGE
```

---

## 📊 TABLE 2: Binary Tree Types Comparison

```
┌──────────────┬──────────────────────────────┬──────────────────────────────┐
│ Type         │ Defining Condition            │ Key Property / Formula       │
├──────────────┼──────────────────────────────┼──────────────────────────────┤
│ Full         │ Every node: 0 or 2 children   │ Leaves = Internal nodes + 1  │
│ Complete     │ All levels full except last;  │ Used by HEAP; array storage  │
│              │ last filled left→right        │ efficient                    │
│ Perfect      │ All leaves same level; all    │ Total nodes = 2^(h+1) - 1   │
│              │ internal have 2 children      │ Leaves = 2^h                 │
│ Balanced     │ |BF| ≤ 1 at EVERY node        │ O(log n) operations          │
│ Skewed       │ All nodes have 1 child only   │ Height = n-1 → O(n) ops      │
└──────────────┴──────────────────────────────┴──────────────────────────────┘
```

---

## 📊 TABLE 3: Tree Traversal Output (Same Tree)

```
Tree:
         A
        / \
       B   C
      / \   \
     D   E   F

Traversal  | Output          | Data Structure | Key Use
-----------|-----------------|----------------|----------------------------
Preorder   | A,B,D,E,C,F     | Stack (recursion)| Copy tree; Root FIRST
Inorder    | D,B,E,A,C,F     | Stack (recursion)| SORTED output from BST
Postorder  | D,E,B,F,C,A     | Stack (recursion)| Delete tree; Root LAST
Level-Order| A,B,C,D,E,F     | QUEUE          | BFS; level by level
```

---

## 📊 TABLE 4: BST at a Glance

```
┌─────────────────────────────────────────────────────────────────┐
│ BST PROPERTY: Left subtree < Root < Right subtree (GLOBALLY!)   │
│ INORDER of BST = SORTED ASCENDING (most tested!)                │
│ Sorted insertion → SKEWED tree → O(n) worst case                │
│ C(4) = 14 distinct BSTs with 4 nodes                            │
├───────────────────────────────────────────────────────────────┬─┤
│ Inorder Successor  = smallest in RIGHT subtree                 │ │
│ Inorder Predecessor = largest in LEFT subtree                  │ │
└───────────────────────────────────────────────────────────────┴─┘

Deletion: Leaf→remove | 1 child→replace | 2 children→inorder successor
```

---

## 📊 TABLE 5: Self-Balancing Trees

```
┌──────────────┬─────────────────┬────────────────┬────────────────────────┐
│ Feature      │ Plain BST       │ AVL Tree       │ Red-Black Tree         │
├──────────────┼─────────────────┼────────────────┼────────────────────────┤
│ Balance      │ None            │ BF ≤ 1 strict  │ Black-height equal     │
│ Height       │ O(n) worst      │ O(log n) always│ O(log n) always        │
│ Search       │ O(n) worst      │ Faster (strict)│ Slightly slower        │
│ Insert       │ O(n) worst      │ O(log n)       │ O(log n), ≤2 rotations │
│ Delete       │ O(n) worst      │ O(log n)       │ O(log n), ≤3 rotations │
│ Colour       │ No              │ No             │ RED or BLACK           │
│ Root colour  │ N/A             │ N/A            │ Always BLACK           │
│ Used in      │ Teaching        │ Read-heavy     │ Java TreeMap, STL, Linux│
└──────────────┴─────────────────┴────────────────┴────────────────────────┘
```

---

## 📊 TABLE 6: BFS vs DFS

```
┌──────────────┬──────────────────────────┬──────────────────────────────┐
│ Feature      │ BFS                      │ DFS                          │
├──────────────┼──────────────────────────┼──────────────────────────────┤
│ Structure    │ QUEUE (FIFO)             │ STACK (LIFO) / Recursion     │
│ Style        │ Level by level           │ Branch by branch (deep first)│
│ Shortest path│ YES (unweighted graphs)  │ NO                           │
│ Cycle detect │ Yes                      │ YES (primary use)            │
│ Topo sort    │ No                       │ YES                          │
│ Time         │ O(V+E)                   │ O(V+E)                       │
│ Space        │ O(V)                     │ O(V)                         │
│ Applications │ GPS, social network,     │ Maze, cycle detect,          │
│              │ web crawl, bipartite     │ topo sort, puzzle solve      │
└──────────────┴──────────────────────────┴──────────────────────────────┘
```

---

## 📊 TABLE 7: GS Quick-Reference

```
┌────────────────────────┬──────────────────────────────────────────────────┐
│ TOPIC                  │ KEY FACT (ONE LINE)                               │
├────────────────────────┼──────────────────────────────────────────────────┤
│ Fundamental Rights     │ Part III, 12–35, JUSTICIABLE, 6 rights           │
│ Art.21 during Emergency│ Art.20 & 21 CANNOT be suspended                  │
│ 5 Writs               │ H-M-P-C-Q (Habeas, Mandamus, Prohibit, Cert, QW) │
│ Art.32                 │ "Heart & Soul" of Constitution (Ambedkar)        │
│ DPSP                   │ Part IV, 36–51, NON-justiciable, Irish origin    │
│ Art.39(d)              │ Equal pay for equal work (DPSP)                  │
│ Art.44                 │ Uniform Civil Code (DPSP, not FR!)               │
│ Art.48A                │ Environment (42nd Amendment 1976)                │
│ Amoeba                 │ Binary fission                                   │
│ Yeast                  │ Budding + Kingdom Fungi                          │
│ Ginger                 │ Rhizome = underground STEM (not root!)           │
│ Potato                 │ Tuber (not rhizome)                              │
│ Yeast fermentation     │ Glucose → Ethanol + CO₂ (anaerobic)             │
│ Penicillin             │ From Penicillium fungus (Alexander Fleming 1928) │
│ Bernoulli              │ Fast fluid = LOW pressure                        │
│ Airplane lift          │ Curved top → fast air → low pressure → lift     │
│ Pascal's Law           │ Hydraulic jack (NOT Bernoulli)                   │
│ Series bulbs           │ 40W brighter than 100W (higher R, same I)        │
│ Parallel bulbs         │ 100W brighter than 40W (lower R, same V)         │
│ Power transmission     │ High voltage → low current → low I²R loss       │
└────────────────────────┴──────────────────────────────────────────────────┘
```

---

# PART 4: 50 PYQ-LEVEL PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 Mixed PYQ Questions (Day 22–27)

---

**Q1.** In a Singly Linked List, inserting a node at the BEGINNING has time complexity O(1) because:
(A) The list is always sorted
(B) Only pointer updates are needed — no traversal required
(C) The first node is always empty (reserved)
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following operations is O(1) in DLL but O(n) in SLL?
(A) Insert at beginning
(B) Search for a value
(C) Delete from END (with tail pointer)
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the CORRECT termination condition when traversing a Circular Singly Linked List?
(A) curr != NULL
(B) curr.next != NULL
(C) curr != HEAD (back to starting node)
(D) More than one of the above
(E) None of the above

---

**Q4.** The formula for total nodes in a PERFECT Binary Tree of height h is:
(A) 2^h
(B) 2^(h+1)
(C) 2^(h+1) - 1
(D) More than one of the above
(E) None of the above

---

**Q5.** Consider the tree:
```
     5
    / \
   3   8
  / \   \
 1   4   9
```
What is the INORDER traversal?
(A) 5, 3, 8, 1, 4, 9
(B) 1, 3, 4, 5, 8, 9
(C) 1, 4, 3, 5, 9, 8
(D) More than one of the above
(E) None of the above

---

**Q6.** The above tree (Q5) — is it a valid BST?
(A) No, because 8 is greater than 5
(B) No, because the tree is not perfectly balanced
(C) Yes — all left subtree values < node < all right subtree values for every node
(D) More than one of the above
(E) None of the above

---

**Q7.** How many structurally distinct Binary Search Trees can be constructed using 4 distinct keys?
(A) 5
(B) 42
(C) 14
(D) More than one of the above
(E) None of the above

---

**Q8.** Inserting elements in ASCENDING order into a BST results in:
(A) A perfectly balanced BST
(B) A right-skewed BST with O(n) search time
(C) A complete BST
(D) More than one of the above
(E) None of the above

---

**Q9.** Which self-balancing BST requires at most 2 rotations per insertion?
(A) AVL Tree
(B) B-Tree
(C) Red-Black Tree
(D) More than one of the above
(E) None of the above

---

**Q10.** In a Red-Black Tree, which of the following is ALWAYS true?
(A) The root is RED
(B) No two adjacent nodes can be BLACK
(C) All paths from a node to NULL descendant leaves have the same number of BLACK nodes
(D) More than one of the above
(E) None of the above

---

**Q11.** A spanning tree of a graph with 9 vertices has how many edges?
(A) 9
(B) 10
(C) 8
(D) More than one of the above
(E) None of the above

---

**Q12.** Which algorithm finds the Minimum Spanning Tree by sorting edges and greedily adding the cheapest non-cycle edge?
(A) Prim's Algorithm
(B) Dijkstra's Algorithm
(C) Kruskal's Algorithm
(D) More than one of the above
(E) None of the above

---

**Q13.** BFS traversal uses a QUEUE because:
(A) Queues are faster than stacks
(B) FIFO order ensures all nodes at current level are processed before going deeper
(C) Queues support random access
(D) More than one of the above
(E) None of the above

---

**Q14.** DFS on a directed graph is primarily used for:
(A) Finding shortest path
(B) Level-order traversal
(C) Cycle detection and topological sorting
(D) More than one of the above
(E) None of the above

---

**Q15.** For a graph with V = 100 vertices stored as an Adjacency Matrix, the space required is:
(A) O(V) = O(100)
(B) O(V + E)
(C) O(V²) = O(10,000)
(D) More than one of the above
(E) None of the above

---

**Q16.** The INORDER SUCCESSOR of the root node 8 in a BST (with right subtree containing 10, 9, 14) is:
(A) 14 (largest in right)
(B) 10 (root of right subtree)
(C) 9 (smallest / leftmost in right subtree)
(D) More than one of the above
(E) None of the above

---

**Q17.** In POSTORDER traversal, which node is ALWAYS visited last?
(A) The leftmost leaf
(B) The rightmost node
(C) The ROOT
(D) More than one of the above
(E) None of the above

---

**Q18.** AVL Tree's balance factor is defined as:
(A) Height(right) - Height(left)
(B) Height(left) + Height(right)
(C) Height(left) - Height(right)
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following correctly states the HANDSHAKING LEMMA?
(A) Every graph has an even number of vertices
(B) The number of edges equals the number of vertices minus one
(C) The sum of degrees of all vertices equals twice the number of edges
(D) More than one of the above
(E) None of the above

---

**Q20.** In a Doubly Linked List, inserting at the MIDDLE requires how many pointer updates?
(A) 2 (same as SLL)
(B) 3
(C) 4 (newNode.next, newNode.prev, prevNode.next, nextNode.prev)
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following is NOT a standard binary tree traversal?
(A) Inorder
(B) Postorder
(C) Randomized Order
(D) More than one of the above
(E) None of the above

---

**Q22.** The time and space complexity of both BFS and DFS on a graph with V vertices and E edges (using adjacency list) is:
(A) Time O(V²), Space O(V)
(B) Time O(V+E), Space O(V)
(C) Time O(V log V), Space O(E)
(D) More than one of the above
(E) None of the above

---

**Q23.** A Full Binary Tree has 7 internal nodes. How many leaf nodes does it have?
(A) 6
(B) 14
(C) 8
(D) More than one of the above
(E) None of the above

---

**Q24.** The Red-Black Tree property that ENSURES approximate balance is:
(A) Root is always Black
(B) New nodes are inserted as Red
(C) All paths from any node to NULL descendants have the same number of Black nodes
(D) More than one of the above
(E) None of the above

---

**Q25.** Given: Preorder traversal = [10, 5, 2, 7, 15, 12, 20] of a BST.
What is the ROOT of this BST?
(A) 2
(B) 5
(C) 10
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 Mixed PYQ Questions (Day 22–27)

---

**Q26.** Which of the following Articles CANNOT be suspended even during a National Emergency under Article 352?
(A) Articles 14 and 19
(B) Articles 19 and 21
(C) Articles 20 and 21
(D) More than one of the above
(E) None of the above

---

**Q27.** Dr. B.R. Ambedkar described which Article as the "Heart and Soul" of the Constitution?
(A) Article 21 (Right to Life)
(B) Article 14 (Right to Equality)
(C) Article 32 (Right to Constitutional Remedies)
(D) More than one of the above
(E) None of the above

---

**Q28.** The writ of HABEAS CORPUS is issued to:
(A) Direct a public authority to perform a legal duty
(B) Secure release of a person illegally detained
(C) Quash an illegal order of an inferior court
(D) More than one of the above
(E) None of the above

---

**Q29.** Directive Principles of State Policy are described as "fundamental in governance" by which Article?
(A) Article 36
(B) Article 38
(C) Article 37
(D) More than one of the above
(E) None of the above

---

**Q30.** The Uniform Civil Code is mentioned in which Article of the Constitution?
(A) Article 40 (Village Panchayats)
(B) Article 51 (International Peace)
(C) Article 44 (DPSP)
(D) More than one of the above
(E) None of the above

---

**Q31.** Article 48A (Environment protection) was added to the Constitution by:
(A) 44th Amendment, 1978
(B) 86th Amendment, 2002
(C) 42nd Amendment, 1976
(D) More than one of the above
(E) None of the above

---

**Q32.** Which of the following is a GANDHIAN Directive Principle?
(A) Equal pay for equal work (Art.39d)
(B) International peace (Art.51)
(C) Organisation of Village Panchayats (Art.40)
(D) More than one of the above
(E) None of the above

---

**Q33.** The Right to Property was removed as a Fundamental Right by which Amendment?
(A) 42nd Constitutional Amendment, 1976
(B) 44th Constitutional Amendment, 1978
(C) 86th Constitutional Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q34.** Which organism reproduces by BUDDING?
(A) Amoeba
(B) Spirogyra
(C) Yeast and Hydra
(D) More than one of the above
(E) None of the above

---

**Q35.** Ginger is classified as which type of plant structure?
(A) Root (taproot)
(B) Tuber (underground stem)
(C) Rhizome (underground modified stem)
(D) More than one of the above
(E) None of the above

---

**Q36.** Yeast is classified in which Kingdom?
(A) Plantae
(B) Monera (bacteria)
(C) Fungi
(D) More than one of the above
(E) None of the above

---

**Q37.** The fermentation equation for yeast produces:
(A) Glucose and water
(B) Ethanol and carbon dioxide (anaerobic)
(C) Lactic acid and water
(D) More than one of the above
(E) None of the above

---

**Q38.** In bread making, the dough RISES because yeast:
(A) Produces oxygen that inflates the dough
(B) Produces CO₂ that gets trapped in the dough during fermentation
(C) Produces ethanol that creates hollow spaces
(D) More than one of the above
(E) None of the above

---

**Q39.** Fertilisation in humans typically occurs in:
(A) The uterus (womb)
(B) The ovary
(C) The fallopian tube (oviduct)
(D) More than one of the above
(E) None of the above

---

**Q40.** Bernoulli's Principle states that in fluid flow:
(A) Pressure increases when fluid speed increases
(B) Pressure decreases when fluid speed increases
(C) Pressure and speed are independent of each other
(D) More than one of the above
(E) None of the above

---

**Q41.** The lift force on an airplane wing is generated because:
(A) The engine pushes air downward creating lift
(B) Curved wing top creates faster airflow → lower pressure above; flat bottom creates higher pressure → net upward lift
(C) The wing is heavier than air, creating vacuum
(D) More than one of the above
(E) None of the above

---

**Q42.** Two bulbs rated 40W and 100W are connected in SERIES to a power supply. Which glows BRIGHTER?
(A) The 100W bulb (it has higher rated power)
(B) The 40W bulb (it has higher resistance; same current flows → more P=I²R)
(C) Both glow equally
(D) More than one of the above
(E) None of the above

---

**Q43.** The formula for electrical power in terms of voltage V and resistance R is:
(A) P = V × R
(B) P = V / R
(C) P = V² / R
(D) More than one of the above
(E) None of the above

---

**Q44.** Electricity is transmitted at HIGH VOLTAGE primarily to:
(A) Make electricity travel faster through wires
(B) Reduce current (I = P/V), thereby minimising I²R heat losses in transmission wires
(C) Increase the energy content of electricity
(D) More than one of the above
(E) None of the above

---

**Q45.** Rhizopus (bread mould) reproduces asexually by:
(A) Budding
(B) Binary fission
(C) Spore formation
(D) More than one of the above
(E) None of the above

---

**Q46.** The Article that prohibits the State from compelling payment of taxes for promotion of any religion is:
(A) Article 25
(B) Article 26
(C) Article 27
(D) More than one of the above
(E) None of the above

---

**Q47.** Which writ is used to challenge a person's right to hold a public office?
(A) Mandamus
(B) Certiorari
(C) Quo Warranto
(D) More than one of the above
(E) None of the above

---

**Q48.** 1 kilowatt-hour (kWh) is equal to:
(A) 1000 Joules
(B) 3.6 × 10⁵ Joules
(C) 3.6 × 10⁶ Joules
(D) More than one of the above
(E) None of the above

---

**Q49.** Penicillin, the first antibiotic, was discovered from:
(A) Yeast (Saccharomyces)
(B) Penicillium (a mould/fungus), discovered by Alexander Fleming
(C) Bacteria (E. coli)
(D) More than one of the above
(E) None of the above

---

**Q50.** The Hydraulic Jack (hydraulic press) works on the principle of:
(A) Bernoulli's Principle
(B) Archimedes' Principle
(C) Pascal's Law
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
| 1 | (B) | Insert at beginning = only 2 pointer changes, no traversal |
| 2 | (C) | DLL end delete = O(1) via TAIL.prev; SLL = O(n) |
| 3 | (C) | CLL traversal ends when curr == HEAD |
| 4 | (C) | Perfect BT: 2^(h+1) - 1 total nodes |
| 5 | (B) | BST inorder always sorted: 1,3,4,5,8,9 |
| 6 | (C) | Yes — valid BST: left<root<right holds at every node |
| 7 | (C) | C(4) = 14 Catalan number |
| 8 | (B) | Ascending insertion → right-skewed → O(n) |
| 9 | (C) | Red-Black Tree: ≤2 rotations per insert |
| 10 | (C) | Black-height uniformity = Property 5 of RB Tree |
| 11 | (C) | Spanning tree: 9 vertices → 9-1 = 8 edges |
| 12 | (C) | Kruskal's = sort edges, add cheapest non-cycle |
| 13 | (B) | FIFO Queue ensures level-by-level processing |
| 14 | (C) | DFS: cycle detection + topological sorting |
| 15 | (C) | Adjacency Matrix: always V² = 100² = 10,000 cells |
| 16 | (C) | Inorder successor = smallest in right subtree = 9 |
| 17 | (C) | Postorder: root is ALWAYS LAST |
| 18 | (C) | BF = Height(left) - Height(right) |
| 19 | (C) | Handshaking: Σ degrees = 2E |
| 20 | (C) | DLL middle insert = 4 pointer updates |
| 21 | (C) | "Randomized Order" = NOT a real traversal |
| 22 | (B) | Both BFS and DFS: Time O(V+E), Space O(V) |
| 23 | (C) | Full BT: Leaves = Internal + 1 = 7 + 1 = 8 |
| 24 | (C) | Equal black-height ensures approximate balance |
| 25 | (C) | First element of Preorder = ROOT = 10 |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Art.20 & 21 = cannot be suspended (44th Amendment) |
| 27 | (C) | Art.32 = "Heart and Soul" (Ambedkar) |
| 28 | (B) | Habeas Corpus = release of illegally detained |
| 29 | (C) | Art.37 = DPSP fundamental in governance |
| 30 | (C) | Art.44 = Uniform Civil Code (DPSP) |
| 31 | (C) | 42nd Amendment 1976 added Art.48A |
| 32 | (C) | Art.40 = Village Panchayats = most Gandhian |
| 33 | (B) | 44th Amendment 1978 removed property as FR |
| 34 | (C) | Yeast + Hydra → budding |
| 35 | (C) | Ginger = RHIZOME (underground modified STEM) |
| 36 | (C) | Yeast = Kingdom FUNGI |
| 37 | (B) | Glucose → Ethanol + CO₂ (yeast anaerobic fermentation) |
| 38 | (B) | CO₂ from fermentation trapped → dough rises |
| 39 | (C) | Fertilisation in FALLOPIAN TUBE |
| 40 | (B) | Bernoulli: speed↑ → pressure↓ |
| 41 | (B) | Curved top → fast air → low pressure above → lift |
| 42 | (B) | Series: same I; 40W has higher R → P=I²R more → brighter |
| 43 | (C) | P = V²/R (from P=VI and I=V/R) |
| 44 | (B) | High V → low I → low I²R transmission losses |
| 45 | (C) | Rhizopus (bread mould) = spore formation |
| 46 | (C) | Art.27 = no tax for religion promotion |
| 47 | (C) | Quo Warranto = challenge to public office authority |
| 48 | (C) | 1 kWh = 1000 W × 3600 s = 3.6 × 10⁶ J |
| 49 | (B) | Penicillin from Penicillium fungus (Fleming 1928) |
| 50 | (C) | Hydraulic jack = Pascal's Law (not Bernoulli!) |

---
---

# 🎯 PART 5: LAST 1-HOUR BEFORE EXAM — ULTRA-CRISP REVISION CARD

## ⚡ CS — 20 Must-Know Facts

```
1.  SLL insert BEGIN = O(1) | SLL delete END = O(n) | SLL insert/delete MIDDLE = O(n)
2.  DLL delete END = O(1) (TAIL.prev) ← key DLL advantage over SLL
3.  DLL middle insert = 4 pointer updates (SLL = 2)
4.  CLL: last.next = HEAD (NO NULL); traversal ends at curr == HEAD
5.  Tree edges = n - 1 (n = nodes; ALWAYS)
6.  Perfect BT: 2^(h+1)-1 total nodes; 2^h leaves; Full BT: Leaves = Internal+1
7.  Preorder: Root FIRST | Inorder: Root MIDDLE | Postorder: Root LAST (always!)
8.  BFS uses QUEUE; Pre/In/Postorder use STACK; Level-order = BFS
9.  BST: ALL left subtree < node < ALL right subtree (GLOBAL rule!)
10. BST Inorder = SORTED ASCENDING ← #1 most tested BST fact
11. BST worst case O(n) when sorted data inserted → use AVL or RB Tree
12. C(4) = 14 distinct BSTs with 4 nodes (Catalan number)
13. AVL: BF = -1/0/+1; RB: root=BLACK; no R-R pair; equal black-height
14. RB Tree used in Java TreeMap, C++ STL, Linux kernel
15. Spanning tree: N vertices → N-1 edges; Kruskal sparse; Prim dense; both greedy
16. Graph: Σ(degrees) = 2E | Complete Kₙ: n(n-1)/2 edges
17. BFS = shortest path (unweighted); DFS = cycle detection, topological sort
18. Adj Matrix: O(V²) space, O(1) edge check; Adj List: O(V+E) space, default
19. Greedy/DP/Divide & Conquer = algorithmic paradigms, NOT graph traversals
20. BFS/DFS time = O(V+E) with adjacency list
```

## ⚡ GS — 20 Must-Know Facts

```
1.  FR: Part III (12–35); JUSTICIABLE; 6 rights; American origin
2.  DPSP: Part IV (36–51); NON-justiciable; Irish origin; 42nd Amend added 39A,43A,48A
3.  Art.20 & 21 = CANNOT be suspended even during Emergency (44th Amendment 1978)
4.  Art.32 = "Heart & Soul" (Ambedkar); 5 writs: H-M-P-C-Q
5.  Art.19: 6 freedoms (19(1)(f) removed by 44th Amend 1978)
6.  Art.17: Untouchability ABOLISHED (unique: applies to private persons too)
7.  Art.21A: Free education 6–14 years (86th Amendment 2002)
8.  Art.44: UCC = DPSP (not FR!) ← most confused article
9.  Art.39(d): Equal pay for equal work = DPSP (not FR!)
10. Art.40: Village Panchayats = most Gandhian DPSP
11. Art.48A: Environment (42nd Amendment 1976) = Liberal-Intellectual DPSP
12. Amoeba = binary fission; Yeast = BUDDING (not binary fission!); Hydra = budding
13. Ginger = RHIZOME (underground STEM, not root!); Potato = TUBER; Onion = BULB
14. Yeast = Kingdom FUNGI; unicellular; chitin cell wall; eukaryote
15. Fermentation: C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ (anaerobic; bread + beer)
16. Fertilisation in FALLOPIAN TUBE; Implantation in UTERUS (endometrium)
17. Penicillin from Penicillium FUNGUS (Alexander Fleming, 1928)
18. Bernoulli: FAST flow = LOW pressure; Hydraulic jack = PASCAL'S LAW (not Bernoulli!)
19. Airplane wing: curved top = fast air = low pressure above = LIFT force
20. Series bulbs: 40W brighter than 100W; Parallel bulbs: 100W brighter than 40W
```

## ⚡ COMMON TRAPS — NEVER GET THESE WRONG

```
TRAP 1:  CLL traversal — check curr == HEAD (NOT curr == NULL → infinite loop!)
TRAP 2:  BST property is GLOBAL (all of left subtree, not just direct child)
TRAP 3:  BFS uses QUEUE, DFS uses STACK (never swap!)
TRAP 4:  Art.20 & 21 can't be suspended (not Art.19 & 21)
TRAP 5:  Art.44 (UCC) is DPSP, not a Fundamental Right
TRAP 6:  Yeast = BUDDING (not binary fission — Amoeba/bacteria = binary fission)
TRAP 7:  Ginger = RHIZOME (STEM, not root; don't be fooled by "ginger root")
TRAP 8:  Hydraulic jack = Pascal's Law (NOT Bernoulli's Principle)
TRAP 9:  40W bulb brighter in SERIES; 100W brighter in PARALLEL
TRAP 10: Randomized traversal = DOES NOT EXIST (not a real traversal type)
TRAP 11: Catalan C(4) = 14 (NOT 5 or 42)
TRAP 12: Fertilisation in FALLOPIAN TUBE (not uterus)
TRAP 13: Penicillin from FUNGUS (Penicillium), not bacteria
TRAP 14: DLL insert middle = 4 pointer updates (not 2!)
TRAP 15: Sorted BST insertion → right-skewed → O(n), NOT O(log n)
```

---

*Next: Day 29 — DBMS Introduction (Database concepts, ER model, Keys, Normalisation basics) | GS: Indian History — Harappan & Vedic Civilisation*
