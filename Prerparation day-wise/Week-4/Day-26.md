# 📅 BPSC TRE 4.0 — DAY 26 COMPLETE STUDY MODULE
### Red-Black Trees, Balanced Trees & Spanning Trees + Biology — Reproduction
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Balanced Trees, Red-Black Trees, AVL Trees, Spanning Trees
> - Afternoon (1 hr): Biology — Reproduction (Asexual & Sexual)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Red-Black Trees, Balanced Trees & Spanning Trees — Deep Conceptual Guide

---

## 🔷 SECTION 1: The Problem — Why Balanced Trees Were Invented

### Recall: The BST Worst-Case Problem
```
When we insert elements into a BST in SORTED order:
Insert: 1, 2, 3, 4, 5, 6, 7

1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
           \
            7

This is a RIGHT-SKEWED tree.
HEIGHT = n - 1 = 6

Search for 7:
  Compare 1 → go right
  Compare 2 → go right
  Compare 3 → go right
  ...7 comparisons for 7 nodes = O(n)

It has degenerated into a LINKED LIST!
Every BST advantage (O(log n)) is LOST.
```

### The Root Cause:
```
BST search time = O(height of tree)

Balanced BST:  height ≈ log₂(n) → O(log n) ✓
Skewed BST:    height = n - 1   → O(n)     ✗

SOLUTION: Keep the tree balanced at ALL TIMES
→ Self-Balancing Trees: AVL Tree, Red-Black Tree, B-Tree

These trees AUTOMATICALLY restructure themselves
after every insertion or deletion to maintain low height.
```

---

## 🔷 SECTION 2: What is a Balanced Tree?

### Definition:
A tree is **balanced** if the height difference between the left and right subtrees of **every node** is bounded (usually ≤ 1 for strict balance).

```
BALANCED TREE:                UNBALANCED TREE:
         5                           5
        / \                         /
       3   7      ← level diff =1  3
      / \ / \                      /
     2  4 6  8                    2
                                  /
Height of left subtree of 5 = 2  1
Height of right subtree of 5 = 2
Difference = 0 → BALANCED ✓     Height diff at root = 3 vs 0 = 3 → UNBALANCED ✗
```

### Why Balance Matters:
```
For n = 1,000,000 nodes:

BALANCED TREE:  height ≈ log₂(1,000,000) ≈ 20
                Search = ~20 comparisons

SKEWED TREE:    height = 999,999
                Search = up to 1,000,000 comparisons

DIFFERENCE: 20 vs 1,000,000 comparisons — 50,000× FASTER when balanced!
```

---

## 🔷 SECTION 3: AVL Tree — Strictly Balanced BST

### What is an AVL Tree?
Named after its inventors: **Adelson-Velsky and Landis** (1962).
The FIRST self-balancing BST ever invented.

### AVL Tree Properties:
```
1. It is a BST (left < root < right at every node)
2. BALANCE FACTOR (BF) of EVERY node must be -1, 0, or +1

Balance Factor (BF) = Height(left subtree) - Height(right subtree)

BF = -1: Right subtree is taller by 1 → OK ✓
BF =  0: Both subtrees same height → OK ✓
BF = +1: Left subtree is taller by 1 → OK ✓
BF = ±2: VIOLATION → tree must be ROTATED to fix
```

### AVL Balance Factor Example:
```
VALID AVL TREE:                NOT VALID AVL TREE:
         4 [BF=0]                       4 [BF=2] ← VIOLATION!
        / \                            /
    2[BF=0] 6[BF=-1]              2 [BF=1]
    / \       \                   /
  1[0] 3[0]   7[0]            1 [BF=0]
BF at 4: h(left)=2, h(right)=2 → 0 ✓
BF at 6: h(left)=0, h(right)=1 → -1 ✓   BF at 4: h(left)=2, h(right)=0 → 2 ✗
```

### AVL Rotations — Concept Only (No Coding):
```
When BF becomes ±2, we perform ROTATIONS to fix:

4 ROTATION TYPES:
1. LEFT ROTATION   (LL case reversed → single right rotation)
2. RIGHT ROTATION  (RR case → single left rotation)
3. LEFT-RIGHT (LR) → double rotation: first left, then right
4. RIGHT-LEFT (RL) → double rotation: first right, then left

After rotation, the tree is restructured to be balanced again.
The BST property is PRESERVED after rotation.

For BPSC exam: Know the 4 names + that rotations maintain BST property.
No need to perform rotations — just know they exist and why.
```

### AVL Tree Complexity:
```
All operations: O(log n) — ALWAYS (never degenerates)

Because AVL maintains strict balance (BF ≤ 1),
height ≤ 1.44 × log₂(n+2) — always O(log n)
```

---

## 🔷 SECTION 4: Red-Black Tree — The Industry Standard

### What is a Red-Black Tree?
A **Red-Black Tree (RB Tree)** is a **self-balancing BST** where every node is coloured either **RED** or **BLACK**, and a specific set of colour rules ensures the tree stays approximately balanced.

### Real-Life Analogy — Traffic Lights in a City:
```
Imagine a city where traffic lights are either RED or BLACK.
The city has rules:
  → Certain sequences of lights are not allowed
  → Every route from start to end passes through the same
    number of black lights

These rules CONSTRAIN the city layout so no route
becomes excessively long. Similarly, Red-Black Tree rules
CONSTRAIN the tree so no path becomes too long.
```

### The 5 Red-Black Tree Properties:
```
Property 1: EVERY node is either RED or BLACK.

Property 2: The ROOT is always BLACK.

Property 3: All NULL (leaf) pointers are considered BLACK.
            (External/sentinel nodes are BLACK)

Property 4: No two consecutive RED nodes.
            (RED node's parent and children must be BLACK)
            = No RED-RED parent-child pair allowed.

Property 5: Every path from any node to its descendant NULL leaves
            must contain the SAME number of BLACK nodes.
            (Black-Height is uniform across all paths)
```

### Visual Red-Black Tree:
```
            7(B)
           /    \
         3(R)   18(R)
         / \    /  \
       2(B) 4(B)10(B) 22(B)
                  \
                  11(R)

B = BLACK, R = RED

Check all 5 properties:
✓ Property 1: Every node is R or B
✓ Property 2: Root (7) is BLACK
✓ Property 3: All NULLs treated as BLACK
✓ Property 4: No R-R pair: 3(R)'s parent 7(B)✓; 18(R)'s parent 7(B)✓;
              11(R)'s parent 10(B)✓
✓ Property 5: Path 7→3→2→NULL: B,B,B = 3 blacks
              Path 7→3→4→NULL: B,R,B,B... count only BLACK: 7,3(R skip),4,NULL = 3 blacks
              Path 7→18→10→11→NULL: 7(B),18(R skip),10(B),11(R skip),NULL(B) = 3 blacks
              All paths = same black count ✓
→ VALID Red-Black Tree ✓
```

### 🚨 PYQ TRAP #1: Counting Black-Height
```
BLACK HEIGHT = number of BLACK nodes on any path from root to NULL leaf
(NOT counting the root itself in some definitions — check context)

The KEY RULE: ALL paths from any node to NULL descendants
have the SAME number of BLACK nodes.

This UNIFORM black count is what ensures approximate balance!
```

---

## 🔷 SECTION 5: Why Red-Black Tree Stays Balanced — The Intuition

### How Colour Rules Prevent Imbalance:
```
The CRUCIAL insight is Property 5 (equal black-height on all paths):

If all paths have the SAME number of black nodes (say, k black nodes):
  Shortest possible path: all BLACK nodes → length = k
  Longest possible path:  alternating RED-BLACK → length = 2k
  (RED node must be followed by BLACK due to Property 4)

So: longest path ≤ 2 × shortest path

This means the tree is APPROXIMATELY balanced:
  Max height ≤ 2 × min height
  Max height ≤ 2 × log₂(n+1)
  → Height is always O(log n) ← Guaranteed!
```

### Red-Black vs AVL:
```
STRICTNESS:
  AVL Tree:    STRICTLY balanced (BF ≤ 1 at every node)
  RB Tree:     APPROXIMATELY balanced (longest path ≤ 2× shortest)
  AVL is MORE balanced than Red-Black tree.

ROTATION COUNT:
  AVL Tree:    Up to O(log n) rotations per insert/delete
  RB Tree:     At most 2 rotations per insert; at most 3 per delete

PERFORMANCE:
  AVL Tree:    Faster SEARCH (more balanced → shorter height)
  RB Tree:     Faster INSERT/DELETE (fewer rotations)

USE CASES:
  AVL Tree:    Read-heavy applications (databases with frequent lookups)
  RB Tree:     Write-heavy applications (frequent insert/delete)

REAL WORLD USE:
  Java TreeMap, TreeSet     → Red-Black Tree (internally)
  C++ STL map, set          → Red-Black Tree (internally)
  Linux kernel (CFS)        → Red-Black Tree
  Java HashMap (bucket)     → Red-Black Tree (Java 8+)
```

---

## 🔷 SECTION 6: Complete Comparison — BST vs AVL vs Red-Black

```
Comparison Table:

Feature              | BST (plain)     | AVL Tree        | Red-Black Tree
---------------------|-----------------|-----------------|------------------
Type                 | Self-organizing | Self-balancing  | Self-balancing
Balance condition    | None            | BF ≤ 1 strictly | Black-height equal
Height guarantee     | O(n) worst      | O(log n) always | O(log n) always
Search complexity    | O(n) worst      | O(log n)        | O(log n)
Insert complexity    | O(n) worst      | O(log n)        | O(log n)
Delete complexity    | O(n) worst      | O(log n)        | O(log n)
Rotations on insert  | 0               | O(log n)        | ≤ 2
Rotations on delete  | 0               | O(log n)        | ≤ 3
Strictly balanced?   | No              | YES             | No (approximately)
Colour property      | No              | No              | YES (R/B)
Invented year        | 1960            | 1962            | 1972
Real-world use       | Teaching        | Read-heavy      | Java, C++ STL, Linux
```

### 🚨 PYQ TRAP #2: AVL vs Red-Black
```
"Which tree is MORE strictly balanced?"
Answer: AVL Tree (BF ≤ 1 everywhere)

"Which tree is used in Java's TreeMap and C++ STL map?"
Answer: Red-Black Tree

"Which self-balancing tree requires FEWER rotations for insert/delete?"
Answer: Red-Black Tree (at most 2 rotations per insert)

"What colours are used in a Red-Black Tree?"
Answer: RED and BLACK (only 2 colours — no other colours!)

"What must the ROOT of a Red-Black Tree always be?"
Answer: BLACK
```

---

## 🔷 SECTION 7: Introduction to Graphs

### What is a Graph?
A **Graph** is a non-linear data structure consisting of:
- **Vertices (V)** — the nodes/points
- **Edges (E)** — the connections between vertices

```
Graph with 5 vertices:

    A ——— B
    |  \  |
    |   \ |
    D ——— C
          |
          E

Vertices: {A, B, C, D, E}
Edges: {A-B, A-C, A-D, B-C, C-D, C-E}
```

### Types of Graphs:
```
UNDIRECTED GRAPH:    Edges have NO direction
                     A — B means both A→B and B→A

DIRECTED GRAPH:      Edges have direction (arrows)
                     A → B means only A to B (not B to A)

WEIGHTED GRAPH:      Edges have weights/costs
                     A --5-- B (5 = distance, cost, etc.)

UNWEIGHTED GRAPH:    Edges have no weight (just connected or not)

CONNECTED GRAPH:     There is a PATH between EVERY pair of vertices
                     You can reach any node from any other node.

DISCONNECTED GRAPH:  Some vertices have no path to others
```

### Tree vs Graph:
```
TREE:                      GRAPH:
- Special case of graph    - General structure
- N nodes, N-1 edges       - Any number of edges
- NO cycles                - CAN have cycles
- ONE path between nodes   - MULTIPLE paths possible
- Always connected         - May or may not be connected
- Hierarchical             - Non-hierarchical (flat)

ALL TREES ARE GRAPHS, but NOT all graphs are trees.
```

---

## 🔷 SECTION 8: Spanning Tree — Core Concept

### What is a Spanning Tree?
```
Given a CONNECTED, UNDIRECTED graph G with N vertices,
a SPANNING TREE is a subgraph that:

1. Contains ALL N vertices of G
2. Uses EXACTLY N-1 edges
3. Has NO cycles (it's a TREE)
4. Connects ALL vertices (it's connected = "spanning")

"Spanning" = it spans (covers/includes) all vertices.
"Tree" = no cycles, connected, N-1 edges.
```

### Visual Example — Graph to Spanning Tree:
```
ORIGINAL GRAPH (5 vertices, 7 edges):

    A ——1—— B
    |  \    |
    3   2   4
    |    \  |
    D ——5—— C ——6—— E
    
Edges: A-B(1), A-C(2), A-D(3), B-C(4), C-D(5), C-E(6), D-E(7) [if exists]
This graph has CYCLES (e.g., A-B-C-A is a cycle).

ONE possible SPANNING TREE (remove edges to eliminate cycles):
    A ——1—— B
    |
    3
    |
    D ——5—— C ——6—— E

Edges used: A-B, A-D, D-C, C-E = 4 edges
N = 5 vertices → N-1 = 4 edges ✓
No cycle ✓
All vertices connected ✓
→ VALID SPANNING TREE ✓
```

### The Golden Formula:
```
For a graph with N vertices:
SPANNING TREE has exactly N - 1 EDGES

This is the MOST tested fact about spanning trees.

Example:
  Graph with 10 vertices → Spanning tree has 9 edges
  Graph with 100 vertices → Spanning tree has 99 edges
  Graph with 7 vertices → Spanning tree has 6 edges
```

### How Many Spanning Trees Can a Graph Have?
```
A graph can have MULTIPLE spanning trees (different edge selections).

For a COMPLETE graph Kₙ (every vertex connected to every other):
Number of spanning trees = n^(n-2)   ← Cayley's Formula

K₄ (complete graph with 4 vertices) = 4^(4-2) = 4² = 16 spanning trees
K₃ (triangle) = 3^(3-2) = 3^1 = 3 spanning trees

For BPSC exam: Just know the formula N-1 edges and Cayley's n^(n-2).
```

---

## 🔷 SECTION 9: Minimum Spanning Tree (MST) — Introduction

### What is MST?
In a **WEIGHTED graph**, a **Minimum Spanning Tree** is the spanning tree whose **total edge weight is MINIMUM** among all possible spanning trees.

```
WEIGHTED GRAPH (5 vertices):

    A ——1—— B
    |  \    |
    3   2   4
    |    \  |
    D ——5—— C ——6—— E

All possible spanning trees and their costs:
  Tree 1: A-B(1) + A-C(2) + A-D(3) + C-E(6) = 12
  Tree 2: A-B(1) + A-C(2) + C-D(5) + C-E(6) = 14
  Tree 3: A-B(1) + A-D(3) + A-C(2) + C-E(6) = 12  ← MINIMUM (tied)
  ...

MST = the spanning tree with MINIMUM total weight.
MST of this graph would use the cheapest edges possible.
```

### MST Algorithms (Know Names, Not Code):
```
1. KRUSKAL'S ALGORITHM:
   Strategy: Sort all edges by weight → greedily pick cheapest edge
             that does NOT form a cycle → repeat until N-1 edges picked.
   Uses: UNION-FIND (Disjoint Set Union) data structure
   Complexity: O(E log E)
   Good for: SPARSE graphs (few edges)

2. PRIM'S ALGORITHM:
   Strategy: Start from any vertex → always add the cheapest edge
             connecting the current tree to a new vertex.
   Uses: Priority Queue / Min-Heap
   Complexity: O(E log V) with min-heap
   Good for: DENSE graphs (many edges)

Both algorithms always produce a CORRECT MST.
For BPSC: Know algorithm names, strategies, complexities.
```

### MST Applications:
```
→ Network design: Cheapest way to connect N cities with telephone/internet cables
→ Circuit design: Minimum wire to connect all components
→ Water supply: Minimum pipeline to connect all towns
→ Power grid: Minimum cable to connect all substations
→ Transportation: Minimum road cost to connect all villages
```

### 🚨 PYQ TRAP #3: Spanning Tree Key Facts
```
FACT 1: Spanning tree has N-1 edges (N = number of vertices)
FACT 2: Spanning tree has NO cycle
FACT 3: Spanning tree is always CONNECTED
FACT 4: A graph can have MULTIPLE spanning trees
FACT 5: MST may NOT be unique (if multiple edges have same weight)
FACT 6: Kruskal = sort edges (good for sparse); Prim = grow from vertex (good for dense)
FACT 7: Both Kruskal and Prim use GREEDY approach

TRAP: "Minimum Spanning Tree is unique" → NOT always true!
      If two edges have the same weight, there may be multiple MSTs.
```

---

## 🔷 SECTION 10: Complete Comparison — Tree Types Summary

```
ALL TREE TYPES — MASTER REFERENCE TABLE:

Type              | Balance | Ordering  | Key Feature                | Use Case
------------------|---------|-----------|----------------------------|------------------
Binary Tree       | No      | No        | At most 2 children/node    | Hierarchy representation
BST               | No      | Yes(L<R<R)| Ordered; O(log n) avg      | Searching, sorting
AVL Tree          | Strict  | Yes       | BF ≤ 1; O(log n) always   | Read-heavy databases
Red-Black Tree    | Approx  | Yes       | R/B colours; 2 rot/insert  | Java TreeMap, C++ STL
B-Tree            | Yes     | Yes       | Multiple keys/node         | Database indices
Spanning Tree     | N/A     | N/A       | N-1 edges; no cycle; all V | Network design
Min Spanning Tree | N/A     | Weighted  | Min total weight           | Cheapest network
```

---

## 🔷 SECTION 11: PYQ Patterns — Common Exam Questions

### Pattern 1: Identify valid Red-Black Tree
```
Question: A tree has these properties — is it a valid RB Tree?
  Root = Black ✓
  New node inserted as Red ✓
  No consecutive Red nodes ✓
  All paths to NULL have same Black count ✓
  → VALID ✓

Watch for: Root coloured Red → INVALID
           Two consecutive Red nodes → INVALID
           Different black counts on different paths → INVALID
```

### Pattern 2: Spanning tree edge count
```
"A graph with 8 vertices has a spanning tree. How many edges?"
Answer: 8 - 1 = 7 edges

"A spanning tree has 12 edges. How many vertices?"
Answer: 12 + 1 = 13 vertices
```

### Pattern 3: AVL balance factor
```
"A node has left subtree height 3 and right subtree height 1.
 What is the balance factor? Is it valid for AVL?"

BF = 3 - 1 = 2
Valid AVL: BF must be -1, 0, or +1
2 is NOT valid → tree needs rotation → NOT a valid AVL node
```

### Pattern 4: Number of spanning trees
```
"How many spanning trees does K₄ (complete graph with 4 vertices) have?"
Cayley's formula: n^(n-2) = 4^(4-2) = 4² = 16
Answer: 16 spanning trees
```

---

## 🔷 SECTION 12: CS Concept Mind Map

```
              SELF-BALANCING TREES & GRAPHS
                           |
           ┌───────────────┼────────────────┐
           |               |                |
        AVL TREE      RED-BLACK TREE    SPANNING TREE
           |               |                |
   BF = -1,0,+1      5 Properties:     N-1 edges
   Strict balance     1. R or B         No cycles
   More rotations     2. Root = BLACK   All vertices
   Faster search      3. NULL = BLACK   connected
   O(log n) always    4. No R-R parent  |
                      5. Same Black-Ht  MST:
                      Approx balanced   Kruskal (sparse)
                      Fewer rotations   Prim (dense)
                      O(log n) always   Both = Greedy
```

---

# PART 2: GENERAL STUDIES
## 🧬 Biology — Reproduction

---

## 🔷 SECTION 1: What is Reproduction?

### Definition:
**Reproduction** is the biological process by which organisms produce NEW individuals (offspring) of the SAME species. It is one of the **fundamental characteristics of living organisms**.

### Why Reproduction is Essential:
```
1. CONTINUATION of species — prevents extinction
2. VARIATION — introduces genetic diversity (in sexual reproduction)
3. HEREDITY — passing traits from parents to offspring
4. EVOLUTION — variations + natural selection = evolution over time

"Reproduction is the ability of an organism to produce
 more organisms similar to itself."
```

### Two Main Types:
```
                   REPRODUCTION
                        |
          ┌─────────────┴──────────────┐
          |                            |
    ASEXUAL REPRODUCTION          SEXUAL REPRODUCTION
    (1 parent only)                (2 parents usually)
    Offspring = genetically        Offspring = genetically
    IDENTICAL to parent            DIFFERENT from parents
    No gametes needed              Requires gametes (egg + sperm)
    Faster                         Slower but creates variation
```

---

## 🔷 SECTION 2: Asexual Reproduction — Types and Examples

### Definition:
Production of offspring from a **SINGLE parent** WITHOUT the involvement of gametes (sex cells). Offspring are genetically **identical** to the parent (clones).

---

### Type 1: BINARY FISSION
```
Definition: Parent cell DIVIDES INTO TWO equal daughter cells.
            The parent essentially splits into two.

Process:
  1. DNA duplicates (replicates)
  2. Cell elongates
  3. Cell divides into two equal halves
  4. Result: 2 identical daughter cells

Found in: PROKARYOTES (organisms without nucleus in cells)

Examples:
  → AMOEBA (most famous example!)
  → Bacteria (E. coli, Salmonella)
  → Paramecium

Visual:
  Parent cell → [SPLIT] → Daughter cell + Daughter cell
      ○        →  [÷]  →      ○        +       ○
```

### 🚨 PYQ TRAP #1: Amoeba Reproduces by Binary Fission
> The most commonly asked question: "Which organism reproduces by binary fission?"
> **Amoeba** reproduces by **binary fission**.
> Bacteria also reproduce by binary fission.
> "Binary" = two; "fission" = splitting.

---

### Type 2: BUDDING
```
Definition: A new organism develops from an OUTGROWTH (bud) on the parent.
            The bud detaches and grows into a new organism.
            Parent remains intact (unlike binary fission).

Process:
  1. Small outgrowth (bud) appears on parent body
  2. Bud grows and develops
  3. Bud detaches from parent
  4. Detached bud grows into a new, complete organism

Found in: Unicellular and some multicellular organisms

Examples:
  → YEAST (most famous example!) — unicellular fungus
  → HYDRA — multicellular aquatic animal
  → Coral — forms colonies by budding

Visual (Hydra):
     Parent       Bud grows      Bud detaches
      |              |                |
     (|)       (|)→bubble       (|)    (new |)
      |              |
    Hydra       Hydra with bud   Two separate Hydra
```

### 🚨 PYQ TRAP #2: Yeast Reproduces by Budding
> **Yeast** reproduces by **budding** (NOT binary fission).
> **Hydra** also reproduces by budding.
> Budding in yeast: The bud grows on the parent yeast cell, gets its nucleus via mitosis, then detaches.
> Common confusion: Binary fission (Amoeba) vs Budding (Yeast) — VERY frequently tested!

---

### Type 3: FRAGMENTATION
```
Definition: Parent organism breaks into FRAGMENTS.
            Each fragment grows into a complete organism.

Examples:
  → SPIROGYRA (filamentous algae) — most famous example!
  → Planaria (flatworm)
  → Starfish (can regenerate from a limb)

Process (Planaria):
  Planaria cut in half → each half regenerates missing parts
  → 2 complete Planaria

Visual:
  [──────whole organism──────]
          ↓ breaks
  [──half──] + [──half──]
       ↓              ↓
  [whole new] + [whole new]
```

### Type 4: SPORE FORMATION (SPORULATION)
```
Definition: Organism produces SPORES — small, light, resistant structures.
            Each spore can germinate into a new organism.

Examples:
  → RHIZOPUS (bread mould) — most common example in biology
  → Ferns, mosses
  → Mucor (another mould)

Process:
  Parent organism → produces sporangium (spore container)
  → sporangium bursts → spores released into air
  → spores land on suitable surface → germinate → new organism

Why spores are special:
  → Very light → dispersed by WIND over long distances
  → Protected by thick wall → survive harsh conditions
  → One parent can produce MILLIONS of spores
```

### Type 5: VEGETATIVE PROPAGATION
```
Definition: Plants reproduce from VEGETATIVE parts (roots, stems, leaves, buds).
            NOT from seeds or spores.

Examples:
  → POTATO → reproduces from tubers (underground stems) — eyes of potato
  → ONION → bulbs
  → GINGER → rhizomes (underground stem)
  → ROSE, SUGARCANE → stem cuttings
  → STRAWBERRY → runners (stolons — horizontal stems on surface)
  → BRYOPHYLLUM → leaves (buds form on leaf margins, fall off, grow into new plants)

This is used in AGRICULTURE extensively:
  Banana, sugarcane, potato = grown from vegetative parts (NOT seeds!)
```

### Type 6: REGENERATION
```
Definition: Some organisms can REGENERATE lost body parts
            or grow an entire new organism from a small fragment.

Examples:
  → PLANARIA (flatworm) — can regenerate a whole organism from any fragment
  → HYDRA — can regenerate from small pieces
  → STARFISH — a limb with part of the centre disc can grow a new starfish

Not all organisms can regenerate:
  → Simpler organisms regenerate better than complex ones
  → Humans can regenerate some tissues (liver!) but not whole organs/limbs
```

---

### Asexual Reproduction — Quick Reference Table:

| Method | Organism (Key Examples) | Key Feature |
|--------|------------------------|-------------|
| Binary Fission | **Amoeba**, Bacteria, Paramecium | One cell splits into TWO equal halves |
| Budding | **Yeast**, **Hydra** | Outgrowth detaches from parent |
| Fragmentation | **Spirogyra**, Planaria, Starfish | Fragment grows into new organism |
| Spore Formation | **Rhizopus** (bread mould), Ferns | Spores dispersed, germinate |
| Vegetative Propagation | **Potato** (tuber), Ginger, Onion | Vegetative parts become new plants |
| Regeneration | **Planaria**, Hydra, Starfish | Lost parts regrow; fragments → whole |

---

## 🔷 SECTION 3: Sexual Reproduction

### Definition:
Reproduction involving **TWO parents** (usually male and female) and the fusion of **gametes** (sex cells) — sperm and egg — to form a **zygote**.

```
MALE parent: produces SPERM (male gamete) — small, motile
FEMALE parent: produces EGG/OVUM (female gamete) — large, non-motile

Fertilization: Sperm + Egg → ZYGOTE (fertilised egg)
Zygote → develops into new organism through cell division
```

### Why Sexual Reproduction Produces Variation:
```
Each gamete has HALF the normal chromosome number (n, haploid):
  Sperm: n chromosomes
  Egg:   n chromosomes
  Zygote: n + n = 2n (diploid — full chromosome count)

MEIOSIS (cell division for gamete formation):
  During meiosis, chromosomes are mixed up randomly
  → Each gamete is UNIQUE (different combination of genes)
  → Offspring receive one set from father + one set from mother
  → Offspring is DIFFERENT from both parents

This variation is crucial for:
  → ADAPTATION to changing environments
  → EVOLUTION (variation + natural selection)
  → Resistance to diseases (genetically diverse population)
```

### Types of Fertilization:
```
INTERNAL FERTILIZATION:
  Sperm fertilises egg INSIDE the female's body.
  → Most mammals (humans, dogs, cows)
  → Birds (hen), Reptiles
  Advantage: Better protection for the embryo

EXTERNAL FERTILIZATION:
  Sperm and egg meet OUTSIDE the body (in water).
  → Most FISH (release eggs + sperm into water)
  → FROGS (amplexus — external fertilization in water)
  → Aquatic animals generally
  Advantage: Can produce millions of gametes at once
  Disadvantage: Most gametes wasted; offspring less protected
```

---

## 🔷 SECTION 4: Human Reproduction — High-Level Overview

### Male Reproductive System:
```
KEY ORGANS:
  TESTES (singular: testis):
    → Produce SPERM (spermatogenesis)
    → Produce TESTOSTERONE (male sex hormone)
    → Located in SCROTUM (outside body — cooler temperature for sperm production)

  EPIDIDYMIS: Sperm mature and are stored here

  VAS DEFERENS: Tube carrying sperm from testis to urethra

  SEMINAL VESICLES + PROSTATE GLAND: Produce fluid that nourishes sperm
    Together = SEMEN (sperm + fluid)

  URETHRA + PENIS: Passage for semen (and urine — separate functions)
```

### Female Reproductive System:
```
KEY ORGANS:
  OVARIES (pair):
    → Produce EGG/OVUM (oogenesis)
    → Produce OESTROGEN and PROGESTERONE (female sex hormones)
    → OVULATION: Release of one egg per month (~day 14 of menstrual cycle)

  FALLOPIAN TUBES (Oviducts):
    → Carry egg from ovary to uterus
    → FERTILISATION typically occurs here (in the fallopian tube)

  UTERUS (Womb):
    → Site of IMPLANTATION (fertilised egg implants in uterine wall)
    → FOETUS develops here during 9 months of pregnancy
    → Inner lining = ENDOMETRIUM (sheds during menstruation if no fertilisation)

  VAGINA: Birth canal; receives sperm during intercourse

  CERVIX: Opening between uterus and vagina
```

### Fertilisation to Birth:
```
Ovulation → Egg released from ovary into fallopian tube
    ↓
Fertilisation → Sperm meets egg in fallopian tube → ZYGOTE formed
    ↓
Cleavage → Zygote divides repeatedly (mitosis) → MORULA → BLASTOCYST
    ↓
Implantation → Blastocyst implants in ENDOMETRIUM of uterus (day ~7)
    ↓
Embryo development → 8 weeks (embryonic stage)
    ↓
Foetal development → Week 9 to birth (foetal stage)
    ↓
Birth (Parturition) → after ~9 months (38–40 weeks)
    ↓
Neonatal period → newborn (neonate)

PLACENTA: Organ connecting foetus to uterus wall
  → Provides oxygen and nutrients to foetus
  → Removes carbon dioxide and wastes from foetus
  → Acts as a barrier (but some substances cross — alcohol, drugs, some viruses)
```

### 🚨 PYQ TRAP #3: Fertilisation Location
> Fertilisation occurs in the **FALLOPIAN TUBE** (oviduct), NOT in the uterus.
> The fertilised egg (zygote) then travels to the uterus for implantation.
> Ectopic pregnancy = dangerous condition where zygote implants in fallopian tube.

---

## 🔷 SECTION 5: Menstrual Cycle — Simplified

```
MENSTRUAL CYCLE: Monthly hormonal cycle in females (average ~28 days)

Day 1–5:   MENSTRUATION
           Endometrium (uterine lining) sheds (if no fertilisation)
           Bleeding occurs

Day 6–13:  FOLLICULAR PHASE
           Follicle in ovary develops
           Oestrogen levels rise
           Endometrium rebuilds

Day 14:    OVULATION
           Egg released from ovary (most fertile day)
           LH surge triggers ovulation

Day 15–28: LUTEAL PHASE
           Corpus luteum forms → releases Progesterone
           Endometrium thickens (prepares for possible implantation)
           If NO fertilisation → Progesterone drops → menstruation starts (Day 1 again)

Hormones involved:
  FSH (Follicle Stimulating Hormone) → stimulates follicle development
  LH (Luteinising Hormone) → triggers ovulation
  Oestrogen → rebuilds endometrium; secondary sexual characters
  Progesterone → maintains endometrium after ovulation; maintains pregnancy
```

---

## 🔷 SECTION 6: Sexually Transmitted Infections (STIs) — Brief Mention

```
Infections spread through sexual contact:
  → HIV/AIDS: Human Immunodeficiency Virus → destroys immune system
  → Syphilis: Bacterial (Treponema pallidum)
  → Gonorrhoea: Bacterial (Neisseria gonorrhoeae)
  → Hepatitis B: Viral → liver infection

IMPORTANT: HIV transmitted by blood, unprotected sex, mother to child
HIV does NOT spread by: casual contact, coughing, mosquito bites
```

---

## 🔷 SECTION 7: Asexual vs Sexual Reproduction — Master Comparison

| Feature | Asexual Reproduction | Sexual Reproduction |
|---------|---------------------|---------------------|
| Parents needed | 1 parent | Usually 2 (male + female) |
| Gametes | NOT required | Required (sperm + egg) |
| Offspring genetics | Identical to parent (clones) | Different from parents |
| Speed | FAST | SLOWER |
| Variation | No variation (clones) | YES — genetic variation |
| Energy | Less energy | More energy |
| Adaptability | Poor (no variation) | Good (variation helps) |
| Evolution support | None | YES — drives evolution |
| Examples | Amoeba, Yeast, Hydra, Bacteria | Humans, most animals, plants |

---

## 🔷 SECTION 8: Biology Memory Tricks

### "BFSVVR" for Asexual Reproduction Types:
```
B = Binary Fission    (Amoeba, Bacteria)
F = Fragmentation     (Spirogyra, Planaria)
S = Spore formation   (Rhizopus — bread mould)
V = Vegetative prop.  (Potato, Ginger)
V = Vegetative (budding - starts with a growth)
R = Regeneration      (Planaria, Starfish)
+ Budding             (Yeast, Hydra)
```

### Key Organism–Method Pairs (MOST TESTED):
```
AMOEBA      → Binary FISSION
YEAST       → BUDDING
HYDRA       → BUDDING (also sexual reproduction)
SPIROGYRA   → FRAGMENTATION
RHIZOPUS    → SPORE formation (bread mould)
PLANARIA    → REGENERATION and fragmentation
POTATO      → Vegetative propagation (tubers)
BANANA      → Vegetative propagation (suckers)
BACTERIA    → Binary fission
```

### Human Reproduction Quick Facts:
```
Fertilisation:   IN FALLOPIAN TUBE
Implantation:    IN UTERUS (endometrium)
Gestation:       ~9 months (38–40 weeks)
Gametes:         Sperm (n) + Egg (n) → Zygote (2n)
Meiosis:         Produces gametes (haploid, n)
Mitosis:         Growth and development after fertilisation
Ovulation:       ~Day 14 of menstrual cycle
Menstrual cycle: ~28 days
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Balanced Trees, Red-Black Trees, AVL Trees, Spanning Trees, Graph Basics

---

**Q1.** What is the maximum balance factor allowed at any node in an AVL Tree?
(A) 0
(B) 2
(C) 1 (BF can be -1, 0, or +1)
(D) More than one of the above
(E) None of the above

---

**Q2.** In a Red-Black Tree, what colour must the ROOT always be?
(A) Red
(B) Either Red or Black
(C) Black
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following is a property of a Red-Black Tree?
(A) Every node is either Red or Black, and no two consecutive Red nodes exist
(B) Every node must be Black
(C) The height must be exactly log₂(n)
(D) More than one of the above
(E) None of the above

---

**Q4.** In a spanning tree of a graph with N vertices, the number of edges is:
(A) N
(B) N + 1
(C) N - 1
(D) More than one of the above
(E) None of the above

---

**Q5.** A spanning tree has 11 edges. How many vertices does the graph have?
(A) 10
(B) 11
(C) 12
(D) More than one of the above
(E) None of the above

---

**Q6.** Which self-balancing BST is used internally by Java's TreeMap and C++ STL map?
(A) AVL Tree
(B) B-Tree
(C) Red-Black Tree
(D) More than one of the above
(E) None of the above

---

**Q7.** AVL Tree is MORE strictly balanced than Red-Black Tree because:
(A) AVL uses Red and Black colours
(B) AVL requires balance factor of -1, 0, or +1 at EVERY node
(C) AVL Tree has more nodes than Red-Black Tree
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the maximum number of rotations needed to fix an AVL Tree after a single insertion?
(A) 1 rotation always
(B) At most 2 rotations (double rotation in LR or RL case)
(C) O(log n) rotations in worst case
(D) More than one of the above
(E) None of the above

---

**Q9.** In a Red-Black Tree, all NULL (leaf) pointers are treated as:
(A) Red nodes
(B) Black nodes
(C) Null colour (neither)
(D) More than one of the above
(E) None of the above

---

**Q10.** Which MST algorithm is more suitable for SPARSE graphs (few edges)?
(A) Prim's Algorithm
(B) Dijkstra's Algorithm
(C) Kruskal's Algorithm
(D) More than one of the above
(E) None of the above

---

**Q11.** The property "all paths from any node to its NULL descendants have the same number of Black nodes" is called:
(A) Balance Factor
(B) Black-Height property
(C) Rotation property
(D) More than one of the above
(E) None of the above

---

**Q12.** A complete graph K₅ has how many spanning trees? (Use Cayley's formula: n^(n-2))
(A) 25
(B) 125
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following CANNOT be true of a valid AVL Tree?
(A) A node with BF = 0
(B) A node with BF = 1
(C) A node with BF = 2
(D) More than one of the above
(E) None of the above

---

**Q14.** The difference between a TREE and a GRAPH is:
(A) Trees have weighted edges; graphs do not
(B) Trees have no cycles and exactly N-1 edges; graphs can have cycles
(C) Trees can have disconnected components; graphs cannot
(D) More than one of the above
(E) None of the above

---

**Q15.** In Red-Black Tree insertion, a new node is always initially coloured:
(A) Black
(B) Either colour randomly
(C) Red
(D) More than one of the above
(E) None of the above

---

**Q16.** Which algorithm finds the Minimum Spanning Tree by GROWING a tree from a single starting vertex?
(A) Kruskal's Algorithm
(B) Dijkstra's Algorithm
(C) Prim's Algorithm
(D) More than one of the above
(E) None of the above

---

**Q17.** A node in an AVL tree has left subtree height 4 and right subtree height 2. What is its balance factor?
(A) -2
(B) 2
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q18.** The maximum height of a Red-Black Tree with n nodes is bounded by:
(A) n - 1
(B) 2 × log₂(n+1)
(C) log₂(n) / 2
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is TRUE about Minimum Spanning Tree?
(A) MST is always unique for any graph
(B) MST contains all edges of the original graph
(C) MST has minimum total edge weight among all spanning trees of the graph
(D) More than one of the above
(E) None of the above

---

**Q20.** The time complexity of Kruskal's Algorithm is:
(A) O(V²)
(B) O(E log E)
(C) O(V log V)
(D) More than one of the above
(E) None of the above

---

**Q21.** Which tree type uses ROTATIONS to maintain balance after insertions?
(A) Regular Binary Search Tree (BST)
(B) Heap
(C) Both AVL Tree and Red-Black Tree
(D) More than one of the above
(E) None of the above

---

**Q22.** A spanning tree of a graph:
(A) Contains all edges of the original graph
(B) May have cycles if the graph has cycles
(C) Includes all vertices and has no cycle, with exactly N-1 edges
(D) More than one of the above
(E) None of the above

---

**Q23.** In a connected undirected graph with 7 vertices, a spanning tree would have:
(A) 7 edges
(B) 5 edges
(C) 6 edges
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following statements about Red-Black Trees and AVL Trees is CORRECT?
(A) AVL Tree has faster insertion/deletion than Red-Black Tree
(B) Red-Black Tree has faster search than AVL Tree
(C) Red-Black Tree has faster insertion/deletion; AVL Tree has faster search
(D) More than one of the above
(E) None of the above

---

**Q25.** The inventors of the AVL Tree are:
(A) Kruskal and Prim
(B) Adelson-Velsky and Landis
(C) Red and Black (fictitious)
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Biology — Reproduction

---

**Q26.** Which organism reproduces by BINARY FISSION?
(A) Yeast
(B) Hydra
(C) Amoeba
(D) More than one of the above
(E) None of the above

---

**Q27.** Which organism reproduces by BUDDING?
(A) Amoeba
(B) Spirogyra
(C) Yeast
(D) More than one of the above
(E) None of the above

---

**Q28.** In budding (as in Hydra), which of the following is correct?
(A) The parent splits into two equal halves
(B) A new organism develops from an outgrowth on the parent body
(C) The parent produces spores
(D) More than one of the above
(E) None of the above

---

**Q29.** Spirogyra reproduces by which method of asexual reproduction?
(A) Budding
(B) Binary fission
(C) Fragmentation
(D) More than one of the above
(E) None of the above

---

**Q30.** Bread mould (Rhizopus) reproduces asexually by:
(A) Budding
(B) Regeneration
(C) Spore formation
(D) More than one of the above
(E) None of the above

---

**Q31.** Fertilisation in humans occurs in which part of the female reproductive system?
(A) Uterus (womb)
(B) Ovary
(C) Fallopian tube (oviduct)
(D) More than one of the above
(E) None of the above

---

**Q32.** The fusion of sperm and egg is called:
(A) Ovulation
(B) Fertilisation
(C) Implantation
(D) More than one of the above
(E) None of the above

---

**Q33.** Offspring produced by asexual reproduction are:
(A) Genetically different from the parent
(B) Always larger than the parent
(C) Genetically identical (clones) to the parent
(D) More than one of the above
(E) None of the above

---

**Q34.** Which of the following plants reproduces vegetatively from TUBERS?
(A) Ginger (rhizome)
(B) Onion (bulb)
(C) Potato
(D) More than one of the above
(E) None of the above

---

**Q35.** Ovulation in humans occurs approximately on which day of the menstrual cycle?
(A) Day 1
(B) Day 28
(C) Day 14
(D) More than one of the above
(E) None of the above

---

**Q36.** The developing baby is nourished in the womb through which organ?
(A) Fallopian tube
(B) Cervix
(C) Placenta
(D) More than one of the above
(E) None of the above

---

**Q37.** Which of the following is an advantage of SEXUAL reproduction over asexual reproduction?
(A) It is faster
(B) It requires only one parent
(C) It produces genetic variation, enabling adaptation and evolution
(D) More than one of the above
(E) None of the above

---

**Q38.** Planaria (flatworm) can reproduce by:
(A) Budding only
(B) Spore formation
(C) Regeneration and fragmentation
(D) More than one of the above
(E) None of the above

---

**Q39.** External fertilisation is characteristic of:
(A) Most mammals
(B) Birds
(C) Most fish and frogs
(D) More than one of the above
(E) None of the above

---

**Q40.** The process by which gametes (sperm and egg) are produced is called:
(A) Mitosis
(B) Meiosis
(C) Binary fission
(D) More than one of the above
(E) None of the above

---

**Q41.** HIV is mainly transmitted through:
(A) Mosquito bites
(B) Casual contact (handshakes)
(C) Unprotected sexual contact and contaminated blood
(D) More than one of the above
(E) None of the above

---

**Q42.** Bryophyllum reproduces vegetatively through:
(A) Tubers
(B) Runners (stolons)
(C) Leaf buds (buds on leaf margins)
(D) More than one of the above
(E) None of the above

---

**Q43.** The male gamete in humans is:
(A) Egg (ovum)
(B) Zygote
(C) Sperm
(D) More than one of the above
(E) None of the above

---

**Q44.** Which hormone triggers OVULATION in the female menstrual cycle?
(A) FSH (Follicle Stimulating Hormone)
(B) Progesterone
(C) LH (Luteinising Hormone) surge
(D) More than one of the above
(E) None of the above

---

**Q45.** The fertilised egg (zygote) IMPLANTS in which structure?
(A) Fallopian tube
(B) Ovary
(C) Endometrium of the uterus
(D) More than one of the above
(E) None of the above

---

**Q46.** Banana plants are commercially propagated using:
(A) Seeds
(B) Spores
(C) Suckers (vegetative propagation)
(D) More than one of the above
(E) None of the above

---

**Q47.** Which of the following statements about asexual reproduction is CORRECT?
(A) It always requires two parents
(B) It involves meiosis to produce gametes
(C) Offspring are genetically identical to the parent
(D) More than one of the above
(E) None of the above

---

**Q48.** Sperm are produced in the:
(A) Epididymis
(B) Prostate gland
(C) Testes
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following organisms reproduces by BOTH asexual and sexual methods?
(A) Amoeba (binary fission only)
(B) Bacteria (binary fission only)
(C) Hydra (budding + sexual)
(D) More than one of the above
(E) None of the above

---

**Q50.** The endometrium is the inner lining of which organ?
(A) Ovary
(B) Fallopian tube
(C) Uterus
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
| 1 | (C) | AVL: BF must be -1, 0, or +1 (magnitude ≤ 1) |
| 2 | (C) | Red-Black Tree Property 2: Root is always BLACK |
| 3 | (A) | R or B colour + no two consecutive Red nodes |
| 4 | (C) | Spanning tree: N vertices → N-1 edges |
| 5 | (C) | Edges = N-1 → 11 = N-1 → N = 12 vertices |
| 6 | (C) | Java TreeMap, C++ STL map = Red-Black Tree |
| 7 | (B) | AVL: strict BF ≤ 1 at every node |
| 8 | (C) | AVL needs up to O(log n) rotations — multiple nodes may need rebalancing |
| 9 | (B) | Property 3: All NULL pointers = BLACK |
| 10 | (C) | Kruskal = edge-based = good for sparse graphs |
| 11 | (B) | Black-Height property = same black count on all paths |
| 12 | (B) | K₅: n^(n-2) = 5^(5-2) = 5³ = 125 |
| 13 | (C) | BF = 2 violates AVL condition (|BF| must be ≤ 1) |
| 14 | (B) | Tree: no cycles, N-1 edges; Graph: can have cycles |
| 15 | (C) | New nodes inserted as RED in Red-Black Tree |
| 16 | (C) | Prim's grows from a vertex; Kruskal's sorts edges globally |
| 17 | (B) | BF = h(left) - h(right) = 4 - 2 = 2 (violation!) |
| 18 | (B) | RB Tree max height ≤ 2 × log₂(n+1) |
| 19 | (C) | MST = minimum total weight spanning tree (may not be unique) |
| 20 | (B) | Kruskal's: O(E log E) for sorting edges |
| 21 | (C) | Both AVL and Red-Black Tree use rotations |
| 22 | (C) | Spanning tree: all vertices, no cycle, N-1 edges |
| 23 | (C) | 7 vertices → 7-1 = 6 edges in spanning tree |
| 24 | (C) | RB: faster insert/delete (fewer rotations); AVL: faster search (stricter balance) |
| 25 | (B) | AVL = Adelson-Velsky and Landis (1962) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Amoeba → binary fission |
| 27 | (C) | Yeast → budding (classic example) |
| 28 | (B) | Budding: outgrowth forms, grows, detaches |
| 29 | (C) | Spirogyra → fragmentation |
| 30 | (C) | Rhizopus (bread mould) → spore formation |
| 31 | (C) | Fertilisation in FALLOPIAN TUBE (oviduct) |
| 32 | (B) | Sperm + Egg fusion = FERTILISATION |
| 33 | (C) | Asexual = clones = genetically identical |
| 34 | (C) | Potato → tubers (underground stems) |
| 35 | (C) | Ovulation ≈ Day 14 of menstrual cycle |
| 36 | (C) | Placenta nourishes the developing baby |
| 37 | (C) | Sexual reproduction creates genetic variation |
| 38 | (C) | Planaria: regeneration + fragmentation |
| 39 | (C) | Most fish and frogs: external fertilisation in water |
| 40 | (B) | Meiosis produces gametes (haploid cells) |
| 41 | (C) | HIV: unprotected sex, contaminated blood, mother-to-child |
| 42 | (C) | Bryophyllum: leaf buds (buds on leaf margins fall and grow) |
| 43 | (C) | Male gamete = sperm |
| 44 | (C) | LH surge triggers ovulation (around Day 14) |
| 45 | (C) | Zygote implants in endometrium of uterus |
| 46 | (C) | Banana: suckers (vegetative propagation) |
| 47 | (C) | Asexual: one parent, no gametes, genetically identical offspring |
| 48 | (C) | Sperm produced in TESTES |
| 49 | (C) | Hydra: budding (asexual) + sexual reproduction |
| 50 | (C) | Endometrium = inner lining of UTERUS |

---
---

# 🔁 DAY 26 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Trees (Balanced, Red-Black, AVL, Spanning)

### AVL Tree — Quick Rules:
```
= Strictly balanced BST (first self-balancing BST, invented 1962)
Balance Factor (BF) = Height(left) - Height(right)
Valid BF at every node: -1, 0, or +1
If BF = ±2 → ROTATION needed (4 types: LL, RR, LR, RL)
All operations: O(log n) ALWAYS
AVL height ≤ 1.44 × log₂(n) — always O(log n)
```

### Red-Black Tree — The 5 Properties:
```
1. Every node is RED or BLACK
2. ROOT is always BLACK
3. NULL/leaf nodes are BLACK
4. No two consecutive RED nodes (no R-R parent-child)
5. All paths from any node to NULL → SAME number of BLACK nodes

Max height ≤ 2 × log₂(n+1) → O(log n) guaranteed
New node inserted = RED (then fix violations)
At most 2 rotations per INSERT; 3 per DELETE
```

### AVL vs Red-Black — Key Differences:
```
Feature              AVL               Red-Black
Balance              Strict (BF ≤ 1)   Approximate
Rotations/insert     O(log n)          ≤ 2
Rotations/delete     O(log n)          ≤ 3
Search speed         FASTER            Slightly slower
Insert/delete speed  SLOWER            FASTER
Used in              Read-heavy apps   Java TreeMap, C++ STL, Linux
```

### Spanning Tree — The Formula:
```
Graph: N vertices, any number of edges
Spanning Tree: ALL N vertices + EXACTLY N-1 edges + NO cycles

N vertices → N-1 edges (MOST TESTED FACT)
Multiple spanning trees possible for same graph
Cayley's formula: K_n has n^(n-2) spanning trees

MST (Minimum Spanning Tree):
  Kruskal's: Sort edges → greedily pick cheapest (sparse graphs) O(E log E)
  Prim's:    Grow from vertex (dense graphs) O(E log V)
  Both use GREEDY approach
  MST need NOT be unique (if edge weights are equal)
```

### 4 CS PYQ Traps:
```
TRAP 1: Root of Red-Black Tree = always BLACK (never Red)
TRAP 2: AVL is MORE strictly balanced than Red-Black
TRAP 3: Spanning tree N vertices → N-1 edges (not N edges!)
TRAP 4: MST is NOT always unique (possible multiple MSTs with equal weights)
```

---

## ⚡ RAPID FIRE — Biology (Reproduction)

### Asexual Reproduction — Organism Pairs (Most Tested):
```
AMOEBA      → BINARY FISSION   (cell splits into 2 equal halves)
YEAST       → BUDDING          (outgrowth detaches)
HYDRA       → BUDDING          (also sexual)
SPIROGYRA   → FRAGMENTATION    (breaks into pieces)
RHIZOPUS    → SPORE FORMATION  (bread mould)
PLANARIA    → REGENERATION     (flatworm)
POTATO      → VEGETATIVE PROP  (tubers)
BANANA      → VEGETATIVE PROP  (suckers)
BACTERIA    → BINARY FISSION
BRYOPHYLLUM → VEGETATIVE PROP  (leaf buds)
```

### Asexual vs Sexual — Key Differences:
```
ASEXUAL: 1 parent, no gametes, clones (identical), fast, no variation
SEXUAL:  2 parents, gametes, variation, slower, drives evolution
```

### Human Reproduction Quick Facts:
```
Fertilisation:   Fallopian tube ← NOT uterus (PYQ trap!)
Implantation:    Endometrium of uterus
Gestation:       ~9 months (38–40 weeks)
Ovulation:       ~Day 14 of menstrual cycle
Hormone: LH surge → triggers ovulation
Placenta:        Nourishes foetus; barrier function
Meiosis:         Produces gametes (n chromosomes = haploid)
Mitosis:         Growth and development after fertilisation
```

### 4 Biology PYQ Traps:
```
TRAP 1: Amoeba = binary fission; Yeast = BUDDING (not binary fission)
TRAP 2: Fertilisation in FALLOPIAN TUBE (not uterus!)
TRAP 3: HIV does NOT spread by mosquito bites or casual contact
TRAP 4: Asexual reproduction produces IDENTICAL offspring (not variation)
```

### Memory Trick — "AYHaS-BFS" for Asexual Types:
```
A = Amoeba → Binary Fission
Y = Yeast → Budding (and Hydra)
S = Spirogyra → Fragmentation
B = Bread mould (Rhizopus) → Spore formation
F = Fragmentation also = Planaria
S = Suckers/Tubers = Vegetative (Banana/Potato)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. AVL Tree: BF = -1/0/+1 at every node; strict balance; O(log n) always; Red-Black: root=BLACK, no R-R pairs, equal black-height on all paths; ≤2 rotations per insert
2. Red-Black used in Java TreeMap, C++ STL; AVL faster search; RB faster insert/delete — both O(log n)
3. Spanning tree: N vertices → N-1 edges (no exceptions!); MST: Kruskal (sparse, O(E log E)); Prim (dense); both greedy
4. Amoeba=binary fission; Yeast & Hydra=budding; Spirogyra=fragmentation; Rhizopus=spore formation; Potato=vegetative (tubers)
5. Human fertilisation in FALLOPIAN TUBE (not uterus); implantation in endometrium; ovulation on Day 14; meiosis produces gametes; LH surge triggers ovulation

---

*Next: Day 27 — Graphs (Representations, BFS, DFS, Shortest Path intro) | GS: Indian History — Harappan & Vedic Civilisation*
