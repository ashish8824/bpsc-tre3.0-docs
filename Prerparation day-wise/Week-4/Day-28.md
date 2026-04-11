# 📅 DAY 28 — BPSC TRE 4.0 COMPLETE REVISION + PRACTICE
## CS MEGA REVISION: Linked Lists + Trees + BST + Red-Black + Graphs (Days 22–27)
## GS MEGA REVISION: Biology + Physics Basics + Chemistry Basics (Science Revision)

> **🔁 REVISION DAY — Phase 1 | Week 4 Complete**
> **Day 28 of 170 | This is your MOST IMPORTANT day — Consolidate everything!**
> **Format:** 25 CS MCQs + 25 GS MCQs | Full BPSC 5-option format | Answers at END ONLY

---

# ════════════════════════════════════════════════════════
# PART A — CS MEGA REVISION
# ALL Topics: Days 22–27 | Linked Lists | Trees | BST
#             Red-Black Trees | Spanning Trees | Graphs
# ════════════════════════════════════════════════════════

---

## 🔗 MODULE 1: LINKED LISTS — COMPLETE REVISION

### Types of Linked Lists at a Glance:

```
┌──────────────────────────────────────────────────────────────────┐
│                   THREE TYPES OF LINKED LISTS                     │
├──────────────────┬────────────────────────────────────────────────┤
│ SINGLY (SLL)     │  [Data|Next] → [Data|Next] → [Data|NULL]      │
│                  │  One direction only (forward)                   │
│                  │  Each node: data + 1 pointer                   │
├──────────────────┼────────────────────────────────────────────────┤
│ DOUBLY (DLL)     │  NULL←[Prev|Data|Next]↔[Prev|Data|Next]→NULL  │
│                  │  Two directions (forward + backward)            │
│                  │  Each node: data + 2 pointers                  │
├──────────────────┼────────────────────────────────────────────────┤
│ CIRCULAR (CLL)   │  [Data|Next] → [Data|Next] → [Data|Next] ↩    │
│                  │  Last node points BACK to first node            │
│                  │  No NULL pointer at end                        │
└──────────────────┴────────────────────────────────────────────────┘
```

### Operations Complexity Table (MEMORIZE!):

```
┌───────────────────────────┬────────────┬───────────┬────────────┐
│ Operation                 │ SLL        │ DLL       │ Array      │
├───────────────────────────┼────────────┼───────────┼────────────┤
│ Access by index           │ O(n) ❌    │ O(n) ❌  │ O(1) ✅   │
│ Insert at BEGINNING       │ O(1) ✅   │ O(1) ✅  │ O(n) ❌   │
│ Insert at END             │ O(n)       │ O(n)      │ O(1)       │
│ Insert at END (with tail) │ O(1)       │ O(1)      │ O(1)       │
│ Delete from BEGINNING     │ O(1)       │ O(1)      │ O(n)       │
│ Delete from END           │ O(n) ❌    │ O(1) ✅  │ O(1)       │
│ Delete from MIDDLE        │ O(n)       │ O(n)      │ O(n)       │
│ Search                    │ O(n)       │ O(n)      │ O(n)/O(lgn)│
│ Memory per node           │ 1 pointer  │ 2 pointers│ None extra │
└───────────────────────────┴────────────┴───────────┴────────────┘

KEY INSIGHT: DLL can delete from END in O(1) because prev pointer
             lets you directly access previous node!
             SLL needs O(n) to find the second-to-last node.
```

### Linked List Key PYQ Facts:

```
╔══════════════════════════════════════════════════════════════════╗
║  LINKED LIST — TOPPER MUST-KNOW FACTS                           ║
╠══════════════════════════════════════════════════════════════════╣
║ 1. NO random access in LL (unlike arrays)                       ║
║ 2. SLL: insert at beginning = O(1), at end = O(n)              ║
║ 3. DLL: HARDER to implement than SLL (more pointers)           ║
║ 4. DLL: delete from end = O(1) (advantage over SLL)            ║
║ 5. Circular LL: last node's next ≠ NULL (points to head)       ║
║ 6. Deque best implemented using DLL (O(1) both ends)           ║
║ 7. LL advantages over array: Dynamic size, easy insert/delete  ║
║ 8. LL disadvantage: No random access, extra pointer memory     ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## 🌳 MODULE 2: TREES — COMPLETE REVISION

### Tree Terminology Quick Reference:

```
                    A          ← ROOT (level 0, depth 0)
                   / \
                  B   C        ← Level 1, depth 1
                 / \    \
                D   E    F     ← Level 2, depth 2 (LEAVES: D, E, F)
               /
              G                ← Level 3, depth 3 (LEAF)

HEIGHT of tree = 3 (longest path from root to leaf = A→B→D→G)
HEIGHT of node A = 3
DEPTH of node G = 3
DEGREE of B = 2 (two children: D and E)
DEGREE of C = 1 (one child: F)
DEGREE of D = 1 (one child: G)
LEAF nodes: D(NO! has child G), E, F, G ← only E, F, G are leaves
INTERNAL nodes: A, B, C, D
```

### Binary Tree Types:

```
FULL BINARY TREE:          COMPLETE BINARY TREE:
Every node has 0 or 2      All levels full except last,
children (never 1)         last level filled LEFT to RIGHT

        1                           1
       / \                         / \
      2   3     ✅               2   3     ✅
     / \   \                    / \ /
    4   5   6   ❌            4  5 6
              (node 3 has 1 child — violates Full BT)


PERFECT BINARY TREE:       BALANCED BINARY TREE:
All leaves at same level,  Height difference between left
completely filled          and right subtree ≤ 1 (at every node)

        1
       / \
      2   3      ✅ (Perfect)
     / \ / \
    4  5 6  7
```

### Tree Traversals — MUST MASTER:

```
TREE:            A
                / \
               B   C
              / \
             D   E

PREORDER  (Root → Left → Right):  A B D E C
INORDER   (Left → Root → Right):  D B E A C  ← BST: gives sorted order!
POSTORDER (Left → Right → Root):  D E B C A
LEVEL-ORDER (BFS):                A B C D E

MEMORY TRICK:
  PRE = ROOT comes first (PREFIX)
  IN  = ROOT comes IN the middle
  POST= ROOT comes last (POSTFIX/SUFFIX)
```

### Number of Binary Trees:

```
UNLABELLED Binary Trees with n nodes = Catalan Number C(n)
C(n) = (2n)! / ((n+1)! × n!)

C(0) = 1   (empty tree)
C(1) = 1
C(2) = 2
C(3) = 5
C(4) = 14  ← MOST ASKED IN BPSC!
C(5) = 42

So: 4 nodes → 14 distinct binary trees/BSTs
```

---

## 🔍 MODULE 3: BST — COMPLETE REVISION

### BST Property (Golden Rule):

```
FOR EVERY NODE in a BST:
  ALL nodes in LEFT subtree  < current node
  ALL nodes in RIGHT subtree > current node

Example Valid BST:          Example INVALID BST:
        8                           8
       / \                         / \
      3   10                      3   10
     / \    \                    / \    \
    1   6    14                 1   6    14
       / \                         / \
      4   7                       4  12  ← 12 > 8 but in left subtree!
                                         This VIOLATES BST property
```

### BST Operations Complexity:

```
┌─────────────────┬───────────────────────────────────┐
│ Operation       │ Time Complexity                    │
├─────────────────┼───────────────────────────────────┤
│ Search          │ O(log n) average | O(n) worst*     │
│ Insert          │ O(log n) average | O(n) worst*     │
│ Delete          │ O(log n) average | O(n) worst*     │
│ Find Min/Max    │ O(h) where h = height              │
│ Inorder traversal│ O(n) — gives sorted output!       │
└─────────────────┴───────────────────────────────────┘
*Worst case = skewed tree (like inserting 1,2,3,4,5 in order)
```

### BST Deletion — 3 Cases:

```
CASE 1: Delete LEAF node (no children)
  → Simply remove it
  Example: Delete 4 from BST → just remove 4

CASE 2: Delete node with ONE child
  → Replace node with its only child
  Example: Delete node with only right child
           → right child takes its place

CASE 3: Delete node with TWO children
  → Replace with INORDER SUCCESSOR (smallest node in right subtree)
     OR INORDER PREDECESSOR (largest node in left subtree)
  Example: Delete 3 from BST with children 1 and 6
           → Replace 3 with inorder successor (4, smallest in right)
```

---

## 🔴 MODULE 4: RED-BLACK TREE + AVL — COMPLETE REVISION

### Red-Black Tree — 5 Properties Flash Card:

```
┌─────────────────────────────────────────────────────────┐
│            RED-BLACK TREE: 5 RULES                       │
│                                                         │
│  Rule 1: Every node is RED or BLACK                     │
│  Rule 2: ROOT is always BLACK                           │
│  Rule 3: Every NIL (leaf) is BLACK                      │
│  Rule 4: RED node → both children must be BLACK         │
│           (No two consecutive RED nodes!)               │
│  Rule 5: All paths root→NIL have SAME black count       │
│           (Black Height is constant)                    │
└─────────────────────────────────────────────────────────┘

New node inserted → Coloured RED first, then fix violations
Root always becomes BLACK (even if recoloured)
```

### AVL Tree Flash Card:

```
Balance Factor (BF) = Height(Left) − Height(Right)
Valid: BF = -1, 0, or +1
Invalid: BF = -2 or +2 → Rotation needed!

4 Types of Rotations:
  LL Rotation → Right rotate
  RR Rotation → Left rotate
  LR Rotation → Left rotate then Right rotate
  RL Rotation → Right rotate then Left rotate
```

### AVL vs Red-Black — Exam Summary:

```
┌────────────────┬──────────────────┬─────────────────────┐
│                │ AVL Tree          │ Red-Black Tree       │
├────────────────┼──────────────────┼─────────────────────┤
│ Balance type   │ Strictly balanced │ Loosely balanced     │
│ Search speed   │ Faster            │ Slightly slower      │
│ Insert/Delete  │ More rotations    │ Fewer rotations      │
│ Best for       │ Read-heavy        │ Write-heavy          │
│ Used in        │ Databases         │ Linux kernel,        │
│                │                   │ Java TreeMap/TreeSet  │
│ Height max     │ 1.44 log(n)       │ 2 log(n+1)           │
└────────────────┴──────────────────┴─────────────────────┘
```

---

## 🌐 MODULE 5: SPANNING TREE + HEAP — REVISION

### Spanning Tree Formula:

```
N vertices → EXACTLY N-1 edges (always!)

Minimum Spanning Tree (MST) algorithms:
  Kruskal's: Sort all edges → add min weight (avoid cycles) → O(E log E)
  Prim's:    Grow from vertex → add nearest vertex → O(E log V)
  Both are GREEDY algorithms!

Cayley's Formula: Complete graph Kn has n^(n-2) spanning trees
  K4 → 4^(4-2) = 16 spanning trees
```

### Heap Revision:

```
HEAP = Complete Binary Tree + Heap Property
  Max-Heap: Parent ≥ Children (root = maximum)
  Min-Heap: Parent ≤ Children (root = minimum)

Array representation (0-based index i):
  Left child  = 2i + 1
  Right child = 2i + 2
  Parent      = (i-1)/2

Get Max (Max-Heap) = O(1) — just return root!
Insert/Delete     = O(log n)
Build Heap        = O(n)  ← NOT O(n log n)!
Heap Sort         = O(n log n)
```

---

## 🔷 MODULE 6: GRAPH THEORY — REVISION

### Graph Big Picture:

```
GRAPH = Vertices (V) + Edges (E)

Directed graph: edge (u,v) ≠ edge (v,u) — one way
Undirected:     edge (u,v) = edge (v,u) — two way

Max edges (undirected): n(n-1)/2
Max edges (directed):   n(n-1)

REPRESENTATIONS:
  Adjacency Matrix: O(V²) space | O(1) edge check
  Adjacency List:   O(V+E) space | O(deg) edge check

TRAVERSALS:
  BFS → QUEUE → Level by level → Shortest path (unweighted)
  DFS → STACK → Depth first  → Cycle detection, Topo sort

BOTH BFS and DFS: O(V+E) time, O(V) space
```

### Algorithm Paradigms vs Traversals (TRAP TOPIC):

```
TRAVERSAL METHODS (not paradigms):
  ✅ BFS (Breadth First Search)
  ✅ DFS (Depth First Search)

ALGORITHM DESIGN PARADIGMS (not traversals):
  ✅ Greedy — Dijkstra, Kruskal, Prim
  ✅ Dynamic Programming — Floyd-Warshall, Bellman-Ford
  ✅ Divide & Conquer — Merge Sort, Quick Sort, Binary Search
  ✅ Backtracking — N-Queens, Sudoku

DON'T MIX THESE UP IN EXAM!
```

---

## 📊 MASTER COMPLEXITY TABLE (Days 22–27 — Full Summary)

```
┌────────────────────────┬──────────────┬─────────────┬─────────────┐
│ Data Structure/Algo    │ Search/Access│ Insert      │ Delete      │
├────────────────────────┼──────────────┼─────────────┼─────────────┤
│ Array (sorted)         │ O(log n)     │ O(n)        │ O(n)        │
│ Singly Linked List     │ O(n)         │ O(1) front  │ O(n)        │
│ Doubly Linked List     │ O(n)         │ O(1) front  │ O(1) both   │
│ BST (average)          │ O(log n)     │ O(log n)    │ O(log n)    │
│ BST (worst/skewed)     │ O(n)         │ O(n)        │ O(n)        │
│ AVL Tree               │ O(log n)     │ O(log n)    │ O(log n)    │
│ Red-Black Tree         │ O(log n)     │ O(log n)    │ O(log n)    │
│ Min/Max Heap           │ O(n)         │ O(log n)    │ O(log n)    │
│ Hash Table (average)   │ O(1)         │ O(1)        │ O(1)        │
│ BFS / DFS (graph)      │ O(V+E)       │ —           │ —           │
│ Dijkstra               │ O((V+E)logV) │ —           │ —           │
└────────────────────────┴──────────────┴─────────────┴─────────────┘
```

---

## 🔑 CS QUICK REVISION — 30 MUST-KNOW FACTS

```
╔══════════════════════════════════════════════════════════════════╗
║        DAY 28 CS — 30 TOPPER FACTS (Revise All!)               ║
╠══════════════════════════════════════════════════════════════════╣
║ 1.  LL has NO random access (arrays do)                         ║
║ 2.  DLL delete from end = O(1), SLL delete from end = O(n)     ║
║ 4.  Circular LL: last node's next → HEAD (not NULL)            ║
║ 5.  Deque best with DLL (O(1) both ends)                       ║
║ 6.  Tree traversals: Pre, In, Post, Level-order (4 types)      ║
║ 7.  Inorder of BST → sorted ascending output                   ║
║ 8.  C(4) = 14 distinct BSTs from 4 keys (Catalan number)      ║
║ 9.  BST property: Left < Root < Right (for ALL nodes)          ║
║ 10. BST worst case: O(n) for skewed tree                       ║
║ 11. RB Tree: root = BLACK, new node = RED                       ║
║ 12. RB Tree: no two consecutive RED nodes                       ║
║ 13. AVL: |BF| ≤ 1; violation at BF = ±2                       ║
║ 14. AVL more strictly balanced than RB Tree                    ║
║ 15. Spanning tree: N vertices → N-1 edges (always)             ║
║ 16. K4 spanning trees: 4^(4-2) = 16                            ║
║ 17. Heap: complete binary tree + heap property                 ║
║ 18. Get max from Max-Heap = O(1) (just read root)              ║
║ 19. Build Heap = O(n) NOT O(n log n)                           ║
║ 20. BFS → QUEUE | DFS → STACK                                  ║
║ 21. BFS = shortest path (unweighted graphs)                    ║
║ 22. DFS = cycle detection, topological sort                    ║
║ 23. Adj Matrix = O(V²) space | Adj List = O(V+E) space        ║
║ 24. Greedy/DP/D&C = paradigms NOT traversals                   ║
║ 25. Dijkstra: shortest path, +ve weights only, greedy         ║
║ 26. Bellman-Ford: negative weights, DP approach                ║
║ 27. Floyd-Warshall: ALL pairs shortest path, O(V³)             ║
║ 28. Topological sort: only on DAG (Directed Acyclic Graph)     ║
║ 29. Kruskal's + Prim's = Greedy MST algorithms                 ║
║ 30. Eulerian circuit: all vertices must have EVEN degree       ║
╚══════════════════════════════════════════════════════════════════╝
```

---

# ════════════════════════════════════════════════════════
# PART B — GS MEGA REVISION
# Science: Biology + Physics + Chemistry Basics
# (Covering all GS science studied up to Day 27)
# ════════════════════════════════════════════════════════

---

## ⚛️ MODULE 7: PHYSICS REVISION — HIGH-FREQUENCY TOPICS

### Newton's Laws of Motion:

```
┌────────────────────────────────────────────────────────────────┐
│               NEWTON'S THREE LAWS                               │
├────────────────┬───────────────────────────────────────────────┤
│ FIRST LAW      │ Law of INERTIA                                │
│ (Inertia)      │ "An object at rest stays at rest, an object   │
│                │  in motion stays in motion, UNLESS acted upon │
│                │  by an external force"                         │
│                │ Example: Passenger jerks backward when bus    │
│                │          suddenly starts                       │
├────────────────┼───────────────────────────────────────────────┤
│ SECOND LAW     │ F = ma  (Force = mass × acceleration)         │
│ (F = ma)       │ "Force = rate of change of momentum"          │
│                │ Unit of Force: NEWTON (N) = kg⋅m/s²           │
│                │ Example: Heavy truck needs more force to stop  │
├────────────────┼───────────────────────────────────────────────┤
│ THIRD LAW      │ "Every action has an equal and opposite       │
│ (Action-       │  reaction"                                     │
│  Reaction)     │ Forces act on DIFFERENT objects               │
│                │ Example: Rocket propulsion, gun recoil        │
│                │          Swimming (push water back → go fwd)  │
└────────────────┴───────────────────────────────────────────────┘
```

### Important Physics Laws & Principles:

```
BERNOULLI'S PRINCIPLE:
  "Faster fluid flow → Lower pressure"
  Applications: Aeroplane wings (lift), carburetor, Venturi meter,
                atomizer/spray, curve ball in cricket

ARCHIMEDES' PRINCIPLE:
  "Upward buoyant force = weight of fluid displaced"
  Explains: Why ships float, why balloons rise
  Application: Designing ships, submarines, hydrometers

PASCAL'S PRINCIPLE:
  "Pressure applied to enclosed fluid transmits equally in all directions"
  Application: HYDRAULIC MACHINES (brake, jack, press)
  Example: Car brakes — small force → large force on wheels

HOOKE'S LAW (Elasticity):
  F = kx (Force = spring constant × extension)
  Valid only within ELASTIC LIMIT

OHMS LAW (Electricity):
  V = IR (Voltage = Current × Resistance)
  P = VI = I²R = V²/R (Power)

UNIVERSAL LAW OF GRAVITATION:
  F = G × M × m / r²
  G = 6.67 × 10⁻¹¹ N m²/kg²
  g = 9.8 m/s² (on Earth's surface)
```

### Sound & Light Quick Reference:

```
SOUND:
  Speed in air: ~343 m/s (at 20°C)
  Speed in water: ~1500 m/s (faster than air)
  Speed in steel: ~5100 m/s (fastest in solid)
  Sound travels FASTEST in SOLIDS, slowest in GASES
  Ultrasound > 20,000 Hz (used in SONAR, medical imaging)
  Infrasound < 20 Hz (elephants communicate via infrasound)
  Doppler Effect: Source approaching → frequency increases (higher pitch)

LIGHT:
  Speed = 3 × 10⁸ m/s (in vacuum)
  Reflection: Angle of incidence = Angle of reflection
  Refraction: Bending of light when passing between media
  Total Internal Reflection: Light stays in denser medium (fibre optics!)
  Prism: Dispersion → VIBGYOR (Violet to Red)
  Convex lens: Converges light (used in magnifying glass, camera)
  Concave lens: Diverges light (used for myopia correction)
```

### Electricity Key Formulas:

```
OHM'S LAW:     V = IR
POWER:         P = VI = I²R = V²/R
SERIES:        R_total = R₁ + R₂ + R₃  (resistance ADDS UP)
PARALLEL:      1/R_total = 1/R₁ + 1/R₂ + 1/R₃  (resistance REDUCES)

REMEMBER:
Series circuit:  Same CURRENT through all, voltage divides
Parallel circuit: Same VOLTAGE across all, current divides
```

---

## 🧪 MODULE 8: CHEMISTRY REVISION — HIGH-FREQUENCY TOPICS

### Atomic Structure Timeline:

```
DALTON (1808):    Atoms are indivisible solid spheres
                  (Later proven wrong — atoms CAN be divided)

THOMSON (1897):   "Plum Pudding Model"
                  Discovered ELECTRON
                  Atom = positive sphere with electrons embedded

RUTHERFORD (1911): "Nuclear Model" (Gold foil experiment)
                   Most of atom is EMPTY SPACE
                   Dense positive NUCLEUS at centre
                   Discovered PROTON

BOHR (1913):      Electrons orbit nucleus in FIXED ENERGY LEVELS
                  Electrons emit/absorb energy when changing levels
                  Works well for HYDROGEN atom
```

### Periodic Table Key Facts:

```
MENDELEEV (1869): Arranged by ATOMIC MASS (left gaps for undiscovered)
MODERN TABLE:     Arranged by ATOMIC NUMBER (protons)

PERIODS (Horizontal rows): 7 periods total
GROUPS (Vertical columns): 18 groups total

Group 1  = Alkali Metals (Li, Na, K, Rb, Cs, Fr) — highly reactive
Group 2  = Alkaline Earth Metals (Be, Mg, Ca...)
Group 17 = Halogens (F, Cl, Br, I) — most electronegative
Group 18 = Noble Gases (He, Ne, Ar, Kr, Xe) — inert/unreactive
```

### Acids, Bases and Salts:

```
ACIDS:         pH < 7  | Taste sour | Turns blue litmus RED
  Strong acids: HCl (Hydrochloric), H₂SO₄ (Sulphuric), HNO₃ (Nitric)
  Weak acids:   CH₃COOH (Acetic/Vinegar), H₂CO₃ (Carbonic in soda)

BASES:         pH > 7  | Taste bitter | Turns red litmus BLUE
  Strong bases: NaOH (Caustic soda), Ca(OH)₂ (Slaked lime)
  Weak bases:   NH₃ (Ammonia), Mg(OH)₂

NEUTRAL:       pH = 7  | Pure water

pH SCALE: 0 ─────────── 7 ─────────── 14
          More Acid    Neutral    More Alkaline
```

### Important Chemical Compounds (BPSC Favourites!):

```
┌───────────────────────────────────────────────────────────────┐
│ SUBSTANCE          │ CHEMICAL NAME / FORMULA   │ KEY USE      │
├────────────────────┼───────────────────────────┼──────────────┤
│ Common Salt        │ Sodium Chloride (NaCl)    │ Food         │
│ Baking Soda        │ Sodium Bicarbonate        │ Baking, fire │
│                    │ (NaHCO₃)                  │ extinguisher │
│ Washing Soda       │ Sodium Carbonate (Na₂CO₃) │ Cleaning     │
│ Bleaching Powder   │ CaOCl₂                    │ Disinfectant │
│ Plaster of Paris   │ CaSO₄·½H₂O               │ Plastering   │
│ Marble/Limestone   │ Calcium Carbonate (CaCO₃) │ Building     │
│ Vinegar            │ Acetic Acid (CH₃COOH)     │ Preservation │
│ Dry Ice            │ Solid CO₂                 │ Cooling      │
│ Heavy Water        │ D₂O (Deuterium Oxide)     │ Nuclear      │
│ Quartz             │ Silicon Dioxide (SiO₂)    │ Optics       │
└────────────────────┴───────────────────────────┴──────────────┘
```

### Carbon and its Allotropes:

```
ALLOTROPES OF CARBON (same element, different structures):

DIAMOND:
  → Hardest natural substance
  → Each C bonded to 4 others (tetrahedral)
  → Does NOT conduct electricity (no free electrons)
  → Used in: Cutting tools, jewellery

GRAPHITE:
  → Softest form of carbon
  → Layers slide over each other → used as LUBRICANT
  → CONDUCTS electricity (delocalized electrons between layers)
  → Used in: Pencils, electrodes, dry cell

FULLERENE (C₆₀ — Buckminsterfullerene):
  → 60 carbon atoms in soccer-ball shape
  → Discovered 1985 (Nobel Prize 1996)
  → Used in: Nanotechnology, drug delivery
```

---

## 🌿 MODULE 9: BIOLOGY MEGA REVISION

### Five Kingdom Quick Reference:

```
MONERA:   Prokaryotes (no nucleus) → Bacteria, Cyanobacteria
PROTISTA: Eukaryotes, unicellular → Amoeba, Paramecium, Spirogyra
FUNGI:    Eukaryotes, heterotrophic → Yeast (budding), Mushroom, Penicillium
PLANTAE:  Eukaryotes, autotrophic → all plants
ANIMALIA: Eukaryotes, heterotrophic, no cell wall → all animals
```

### Human Biology Quick Revision:

```
DIGESTIVE SYSTEM:
  Mouth → Oesophagus → Stomach → Small Intestine → Large Intestine
  Enzymes:
    Saliva:         Salivary Amylase (starch → maltose)
    Stomach:        Pepsin (protein → peptides), HCl (acid)
    Small Intestine: Lipase (fats), Trypsin (proteins), Amylase
  Absorption: 90% in SMALL INTESTINE (villi increase surface area)
  Liver: Produces BILE (emulsifies fats), detoxification, glycogen storage

CIRCULATORY SYSTEM:
  Heart: 4 chambers (2 auricles + 2 ventricles)
  Left side: oxygenated blood (pulmonary vein → left atrium)
  Right side: deoxygenated blood (vena cava → right atrium)
  Blood components: RBC (oxygen), WBC (immunity), Platelets (clotting), Plasma
  Blood groups: A, B, AB, O (Universal donor: O; Universal recipient: AB)
  Rh factor: Rh+ positive, Rh- negative

RESPIRATORY SYSTEM:
  Breathing rate: 15-18 times/minute (normal adult)
  O₂ enters, CO₂ leaves via diffusion in ALVEOLI
  Diaphragm contracts → chest expands → air enters

EXCRETORY SYSTEM:
  Kidney → Ureter → Urinary Bladder → Urethra
  Nephron: Basic functional unit of kidney
  Urine: 95% water, 2% urea, 2% salts
  Dialysis: artificial kidney for kidney failure patients
```

### Vitamins & Deficiency Diseases (BPSC High Priority!):

```
┌───────────┬─────────────────────────┬──────────────────────────┐
│ VITAMIN   │ CHEMICAL NAME           │ DEFICIENCY DISEASE       │
├───────────┼─────────────────────────┼──────────────────────────┤
│ Vitamin A │ Retinol                 │ Night Blindness,         │
│           │                         │ Xerophthalmia             │
│ Vitamin B1│ Thiamine                │ BERI-BERI                │
│ Vitamin B2│ Riboflavin              │ Cracked lips, sores      │
│ Vitamin B3│ Niacin                  │ PELLAGRA                 │
│ Vitamin B12│ Cyanocobalamin         │ Pernicious Anaemia       │
│ Vitamin C │ Ascorbic Acid           │ SCURVY                   │
│           │ (also called Cevitamic) │ (bleeding gums, joints)  │
│ Vitamin D │ Calciferol              │ RICKETS (children)       │
│           │                         │ Osteomalacia (adults)    │
│ Vitamin E │ Tocopherol              │ Sterility, muscular dist.│
│ Vitamin K │ Phylloquinone           │ Excessive BLEEDING       │
│           │                         │ (slow blood clotting)    │
└───────────┴─────────────────────────┴──────────────────────────┘

Fat-soluble: A, D, E, K  (stored in liver)
Water-soluble: B-complex, C (excreted in urine — need daily intake)
```

### Diseases and Causative Agents:

```
┌──────────────────┬──────────────────────────────────────────────┐
│ DISEASE          │ CAUSATIVE AGENT + KEY FACTS                  │
├──────────────────┼──────────────────────────────────────────────┤
│ Malaria          │ Plasmodium (Protozoan) via female Anopheles  │
│                  │ mosquito. Multiple fission in RBCs           │
│ Dengue           │ Virus (Flavivirus) via Aedes mosquito        │
│ Typhoid          │ Salmonella typhi (Bacterium)                 │
│ Cholera          │ Vibrio cholerae (Bacterium) — rice water stool│
│ Tuberculosis     │ Mycobacterium tuberculosis (Koch's bacillus) │
│ Leprosy          │ Mycobacterium leprae                         │
│ Plague           │ Yersinia pestis (bacterium via rat fleas)    │
│ Rabies           │ Rabies virus — Rhabdovirus                   │
│ HIV/AIDS         │ HIV Virus — attacks CD4 T-lymphocytes        │
│ Polio            │ Poliovirus — affects motor neurons            │
│ COVID-19         │ SARS-CoV-2 (coronavirus)                     │
│ Hepatitis B      │ Hepatitis B Virus — affects LIVER            │
│ Tetanus          │ Clostridium tetani (bacteria, soil)           │
└──────────────────┴──────────────────────────────────────────────┘
```

### Reproduction Quick Revision (Day 26 GS):

```
Fertilization → Fallopian Tube
Sex determination → Father's sperm (X=girl, Y=boy)
Pregnancy test → HCG hormone
Progesterone → "Hormone of pregnancy"
Gestation (human) → 280 days (40 weeks)
Ginger → RHIZOME (modified stem, not root!)
Yeast → BUDDING (unicellular FUNGUS, not plant)
```

---

## 🔑 GS QUICK REVISION — 30 MUST-KNOW SCIENCE FACTS

```
╔══════════════════════════════════════════════════════════════════╗
║        DAY 28 GS — 30 TOPPER SCIENCE FACTS                     ║
╠══════════════════════════════════════════════════════════════════╣
║ 1.  Newton's 3rd Law: Action-Reaction (equal & opposite)        ║
║ 2.  F = ma (Newton's 2nd Law)                                   ║
║ 3.  Bernoulli: faster flow → lower pressure                     ║
║ 4.  Archimedes: buoyant force = weight of fluid displaced       ║
║ 5.  Pascal: pressure transmits equally in enclosed fluid        ║
║ 6.  Sound: fastest in SOLIDS, slowest in GASES                  ║
║ 7.  Ultrasound > 20,000 Hz | Infrasound < 20 Hz                ║
║ 8.  Light speed = 3 × 10⁸ m/s                                  ║
║ 9.  Diamond = hardest, does NOT conduct electricity             ║
║ 10. Graphite = soft, CONDUCTS electricity (pencils, electrodes) ║
║ 11. Baking Soda = NaHCO₃ | Washing Soda = Na₂CO₃              ║
║ 12. pH < 7 = acid | pH > 7 = base | pH = 7 = neutral           ║
║ 13. Universal Donor = O blood group                             ║
║ 14. Universal Recipient = AB blood group                        ║
║ 15. Malaria = Plasmodium (Protozoan), Anopheles mosquito        ║
║ 16. Dengue = Virus, Aedes mosquito                              ║
║ 17. TB = Mycobacterium tuberculosis                             ║
║ 18. Vitamin C deficiency → SCURVY                               ║
║ 19. Vitamin D deficiency → RICKETS (children)                   ║
║ 20. Vitamin B1 deficiency → BERI-BERI                          ║
║ 21. Vitamin K → blood CLOTTING                                  ║
║ 22. Photosynthesis: 6CO₂ + 6H₂O + Light → Glucose + 6O₂      ║
║ 23. O₂ released in LIGHT REACTIONS (photolysis of water)        ║
║ 24. Calvin Cycle (Dark Rxn) → Glucose formed, CO₂ fixed       ║
║ 25. Five Kingdoms: Monera, Protista, Fungi, Plantae, Animalia  ║
║ 26. Yeast = FUNGUS, budding | Amoeba = Protista, binary fission ║
║ 27. Lichen = Fungus + Algae symbiosis                           ║
║ 28. 10% energy law (Lindemann) — only 10% transfers up chain   ║
║ 29. Nephron = functional unit of kidney                         ║
║ 30. Heart: 4 chambers — 2 auricles (atria) + 2 ventricles      ║
╚══════════════════════════════════════════════════════════════════╝
```

---

# ════════════════════════════════════════════════════════
# PRACTICE QUESTIONS — DAY 28
# ════════════════════════════════════════════════════════

> ⚠️ **NON-NEGOTIABLE RULE:**
> Solve ALL 50 questions before checking answers.
> ANSWERS ARE ONLY AT THE VERY END — do NOT scroll down early!
> Time yourself: Target 35 minutes for 50 questions (42 sec each)

---

## 📘 SECTION I: CS QUESTIONS (Q1–Q25)
### Revision: Linked Lists | Trees | BST | Red-Black | Graphs | Complexity

---

**Q1.** Which of the following statements about Singly Linked Lists is/are CORRECT?

(i) Insertion at the beginning takes O(1) time
(ii) Random access by index takes O(1) time
(iii) Insertion at the end takes O(n) time (without a tail pointer)

(A) Only (i)
(B) Only (i) and (iii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q2.** What is the main ADVANTAGE of a Doubly Linked List over a Singly Linked List?

(A) It uses less memory per node
(B) It supports faster random access
(C) It allows O(1) deletion from the END of the list (given a reference to the last node)
(D) More than one of the above
(E) None of the above

---

**Q3.** In a Circular Linked List, the next pointer of the LAST node points to:

(A) NULL
(B) Itself (the last node)
(C) The FIRST (HEAD) node
(D) More than one of the above
(E) None of the above

---

**Q4.** Given this Binary Tree, what is its INORDER traversal?

```
        10
       /  \
      5    20
     / \
    3   7
```

(A) 10, 5, 3, 7, 20
(B) 3, 5, 7, 10, 20
(C) 3, 7, 5, 20, 10
(D) More than one of the above (there are multiple valid inorder traversals)
(E) None of the above

---

**Q5.** For the same tree above, what is its PREORDER traversal?

(A) 3, 5, 7, 10, 20
(B) 3, 7, 5, 20, 10
(C) 10, 5, 3, 7, 20
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following is NOT a valid binary tree traversal method?

(A) Inorder
(B) Preorder
(C) Randomized Order
(D) More than one of the above (Inorder and Preorder are NOT valid)
(E) None of the above (all four options list valid methods)

---

**Q7.** The number of distinct Binary Search Trees (BSTs) that can be formed using the keys {1, 2, 3, 4} is:

(A) 4
(B) 8
(C) 12
(D) More than one of the above
(E) 14

---

**Q8.** Consider inserting the following keys into an initially empty BST in ORDER: 50, 30, 70, 20, 40. What is the INORDER traversal of the resulting BST?

(A) 50, 30, 70, 20, 40
(B) 20, 30, 40, 50, 70
(C) 20, 40, 30, 70, 50
(D) More than one of the above
(E) None of the above

---

**Q9.** In a Red-Black Tree, which of the following is ALWAYS true?

(A) The root node is RED
(B) All leaf (NIL) nodes are RED
(C) A RED node's children must both be BLACK
(D) More than one of the above (A and C are both always true)
(E) None of the above

---

**Q10.** When a new node is inserted into a Red-Black Tree, it is initially coloured:

(A) BLACK
(B) WHITE
(C) RED
(D) More than one of the above (colour depends on position)
(E) None of the above

---

**Q11.** Which of the following balanced tree types is MORE STRICTLY BALANCED and better suited for applications that are READ-HEAVY (many searches, few insertions)?

(A) Red-Black Tree
(B) B-Tree
(C) AVL Tree
(D) More than one of the above
(E) None of the above

---

**Q12.** A connected graph has 9 vertices. Its spanning tree will have exactly how many edges?

(A) 9
(B) 10
(C) 8
(D) More than one of the above
(E) None of the above

---

**Q13.** In a MAX-HEAP stored as an array with 0-based indexing, what is the index of the LEFT CHILD of the element at index 3?

(A) 6
(B) 7
(C) 8
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following statements about BFS and DFS are CORRECT?

(i) BFS uses a QUEUE; DFS uses a STACK (or recursion)
(ii) Both have O(V+E) time complexity
(iii) BFS guarantees shortest path in an UNWEIGHTED graph

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q15.** Greedy, Dynamic Programming, and Divide & Conquer are examples of:

(A) Graph traversal methods
(B) Data structure operations
(C) Algorithm design paradigms
(D) More than one of the above
(E) Sorting algorithms

---

**Q16.** Consider a graph. If we run DFS and a node is encountered that is ALREADY IN THE CURRENT DFS PATH (back edge), what does this indicate?

(A) The graph is disconnected
(B) The graph contains a CYCLE
(C) The graph is bipartite
(D) More than one of the above
(E) None of the above

---

**Q17.** In Adjacency Matrix representation for an undirected graph, if there are V vertices, which of the following is ALWAYS TRUE?

(A) matrix[i][j] = matrix[j][i] (matrix is symmetric)
(B) All diagonal elements matrix[i][i] = 0 (no self-loops)
(C) Space required = O(V²)
(D) More than one of the above (all three are correct for simple undirected graph)
(E) None of the above

---

**Q18.** What is the time complexity of the HEAPIFY operation (fixing heap property from root down) on a heap of n elements?

(A) O(1)
(B) O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q19.** Which traversal of a BST gives keys in DESCENDING (reverse sorted) order?

(A) Preorder
(B) Postorder
(C) Reverse Inorder (Right → Root → Left)
(D) More than one of the above
(E) None of the above

---

**Q20.** The Kruskal's algorithm for finding Minimum Spanning Tree uses which underlying data structure to efficiently detect cycles?

(A) Stack
(B) Queue
(C) Disjoint Set (Union-Find)
(D) More than one of the above
(E) None of the above

---

**Q21.** A full binary tree with n INTERNAL nodes has how many LEAF nodes?

(A) n
(B) n-1
(C) n+1
(D) More than one of the above
(E) 2n

---

**Q22.** In a BST, which node is the INORDER SUCCESSOR of a given node X?

(A) The parent of node X
(B) The rightmost node in the left subtree of X
(C) The leftmost (minimum) node in the right subtree of X
(D) More than one of the above
(E) None of the above

---

**Q23.** Java's TreeMap and TreeSet are internally implemented using:

(A) AVL Tree
(B) B+ Tree
(C) Red-Black Tree
(D) More than one of the above
(E) Hash Table

---

**Q24.** Which of the following correctly describes a COMPLETE BINARY TREE?

(A) Every node has exactly 0 or 2 children
(B) All levels are completely filled with no exceptions
(C) All levels are filled except possibly the last, which is filled from LEFT to RIGHT
(D) More than one of the above
(E) None of the above

---

**Q25.** For a Doubly Linked List, which operations can be done in O(1) time?

(i) Insert at beginning
(ii) Delete from end (given reference to last node)
(iii) Access element at position k (0-based)

(A) Only (i)
(B) Only (i) and (ii)
(C) All three
(D) More than one of the above (same as option B)
(E) None of the above

---

## 🌿 SECTION II: GS (SCIENCE REVISION) QUESTIONS (Q26–Q50)
### Biology + Physics + Chemistry | All science studied so far

---

**Q26.** Newton's First Law of Motion is also known as the Law of:

(A) Gravitation
(B) Conservation of Momentum
(C) Inertia
(D) More than one of the above
(E) None of the above

---

**Q27.** According to Bernoulli's Principle, when the velocity of a fluid INCREASES, its pressure:

(A) Increases
(B) Remains the same
(C) Decreases
(D) More than one of the above
(E) None of the above

---

**Q28.** Which of the following is a correct application of ARCHIMEDES' PRINCIPLE?

(A) A plane flying due to wing shape
(B) A ship floating on water because displaced water's weight equals ship's weight
(C) A hydraulic brake transferring force
(D) More than one of the above
(E) None of the above

---

**Q29.** The speed of sound is MAXIMUM in which medium?

(A) Air (gas)
(B) Water (liquid)
(C) Steel (solid)
(D) More than one of the above
(E) Speed of sound is same in all media

---

**Q30.** Vitamin C deficiency causes which disease?

(A) Rickets
(B) Beri-Beri
(C) Scurvy
(D) More than one of the above
(E) Pellagra

---

**Q31.** Which Vitamin is essential for BLOOD CLOTTING?

(A) Vitamin A
(B) Vitamin C
(C) Vitamin D
(D) More than one of the above
(E) Vitamin K

---

**Q32.** The UNIVERSAL BLOOD DONOR is a person with blood group:

(A) A
(B) AB
(C) O
(D) More than one of the above
(E) B

---

**Q33.** Malaria is caused by which pathogen and transmitted by which vector?

(A) Bacterium (Salmonella); Culex mosquito
(B) Protozoan (Plasmodium); female Anopheles mosquito
(C) Virus (Dengue virus); Aedes mosquito
(D) More than one of the above
(E) None of the above

---

**Q34.** Diamond and Graphite are both forms of Carbon. Which of the following is/are TRUE?

(i) Diamond does NOT conduct electricity; Graphite DOES conduct electricity
(ii) Diamond is the hardest natural substance; Graphite is soft
(iii) Both are allotropes of Carbon

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q35.** Which of the following chemical compounds is Baking Soda?

(A) Na₂CO₃ (Sodium Carbonate)
(B) NaOH (Sodium Hydroxide)
(C) NaHCO₃ (Sodium Bicarbonate)
(D) More than one of the above
(E) None of the above

---

**Q36.** The functional unit of the KIDNEY is:

(A) Alveolus
(B) Neuron
(C) Nephron
(D) More than one of the above
(E) Villus

---

**Q37.** Which gas is released during PHOTOSYNTHESIS?

(A) Carbon dioxide (CO₂)
(B) Nitrogen (N₂)
(C) Oxygen (O₂)
(D) More than one of the above
(E) Hydrogen (H₂)

---

**Q38.** Tuberculosis (TB) is caused by:

(A) A virus
(B) A protozoan (Plasmodium)
(C) A bacterium (Mycobacterium tuberculosis)
(D) More than one of the above
(E) A fungus

---

**Q39.** According to LINDEMANN'S 10% LAW, if 1000 kcal of energy is present in GRASS, how much energy reaches SNAKES in the food chain: Grass → Grasshopper → Frog → Snake?

(A) 100 kcal
(B) 10 kcal
(C) 1 kcal
(D) More than one of the above
(E) None of the above

---

**Q40.** Which of the following is CORRECTLY paired?

(A) Yeast — Kingdom Plantae — reproduces by spore formation
(B) Amoeba — Kingdom Monera — binary fission
(C) Lichen — Fungus + Algae symbiosis — pioneer organism
(D) More than one of the above
(E) None of the above

---

**Q41.** In the Periodic Table, which GROUP contains the NOBLE GASES (inert gases)?

(A) Group 1
(B) Group 17
(C) Group 18
(D) More than one of the above
(E) None of the above

---

**Q42.** Rutherford's gold foil experiment (1911) led to the discovery of:

(A) Electron
(B) Neutron
(C) The nucleus (dense positive centre of atom)
(D) More than one of the above
(E) None of the above

---

**Q43.** Which of the following statements about VITAMINS is/are CORRECT?

(i) Vitamins A, D, E, K are fat-soluble (stored in liver)
(ii) Vitamins B-complex and C are water-soluble
(iii) Vitamin D deficiency causes RICKETS in children

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q44.** Which of the following statements about the HEART is CORRECT?

(A) The left side of the heart carries deoxygenated blood
(B) The right ventricle pumps blood to the lungs (pulmonary circulation)
(C) The heart has 2 chambers (1 atrium + 1 ventricle)
(D) More than one of the above
(E) None of the above

---

**Q45.** In the pH scale, which substance has the LOWEST pH (most acidic)?

(A) Pure water (pH = 7)
(B) Lemon juice (pH ≈ 2)
(C) Battery acid / concentrated H₂SO₄ (pH ≈ 0-1)
(D) More than one of the above
(E) None of the above

---

**Q46.** The Doppler Effect in SOUND occurs when:

(A) Sound travels through water instead of air
(B) A sound source approaches an observer → observed frequency is HIGHER than emitted frequency
(C) Sound is reflected off a surface (echo)
(D) More than one of the above
(E) None of the above

---

**Q47.** Which of the following is the CHEMICAL NAME for Vitamin B12?

(A) Thiamine
(B) Riboflavin
(C) Cyanocobalamin
(D) More than one of the above
(E) Ascorbic Acid

---

**Q48.** Pascal's Law is the working principle behind which of the following?

(A) Aeroplane wings (lift generation)
(B) Hydraulic brakes / hydraulic jack
(C) SONAR (underwater navigation)
(D) More than one of the above
(E) None of the above

---

**Q49.** Which disease is caused by the DENGUE VIRUS and transmitted by which mosquito?

(A) Plasmodium via female Anopheles
(B) Flavivirus via Aedes mosquito
(C) Rabies virus via dog bite
(D) More than one of the above
(E) None of the above

---

**Q50.** In the human digestive system, where does MAXIMUM ABSORPTION of nutrients take place?

(A) Stomach
(B) Large Intestine
(C) Small Intestine (due to villi and microvilli)
(D) More than one of the above
(E) Mouth

---

# ════════════════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 28
# OPEN ONLY AFTER ATTEMPTING ALL 50 QUESTIONS!
# ════════════════════════════════════════════════════════

---

## CS ANSWERS (Q1–Q25)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q1  | **(B) Only (i) and (iii)** | SLL: Insert at beginning=O(1) ✅, Random access=O(n) ❌ (ii is FALSE), Insert at end=O(n) ✅ |
| Q2  | **(C)** | DLL's key advantage over SLL: O(1) deletion from END due to prev pointer |
| Q3  | **(C) First (HEAD) node** | Circular LL: last node's next → HEAD. This makes it circular! |
| Q4  | **(B) 3,5,7,10,20** | Inorder = Left→Root→Right. Traverse: 3,5,7,10,20 (always sorted for BST!) |
| Q5  | **(C) 10,5,3,7,20** | Preorder = Root→Left→Right. Start with Root(10), then left subtree(5,3,7), then right(20) |
| Q6  | **(C) Randomized Order** | "Randomized traversal" does NOT exist! Pre, In, Post, Level-order are valid |
| Q7  | **(E) 14** | Catalan number C(4) = 14. Most asked BPSC fact! |
| Q8  | **(B) 20,30,40,50,70** | Inorder of BST always gives SORTED output regardless of insertion order |
| Q9  | **(C)** | RED node → both children must be BLACK (no consecutive reds). Root is always BLACK (not red as A says) |
| Q10 | **(C) RED** | New node always inserted as RED first, then violations fixed |
| Q11 | **(C) AVL Tree** | AVL is MORE strictly balanced → faster search. Better for read-heavy apps |
| Q12 | **(C) 8 edges** | Spanning tree: N vertices → N-1 edges. 9 vertices → 8 edges |
| Q13 | **(B) 7** | Left child of index i = 2i+1. Left child of index 3 = 2(3)+1 = 7 |
| Q14 | **(D) More than one** | ALL THREE statements about BFS/DFS are correct |
| Q15 | **(C) Algorithm design paradigms** | Greedy, DP, D&C are PARADIGMS. BFS/DFS are traversals — never confuse! |
| Q16 | **(B) Cycle** | If DFS finds a back edge (already-visited node in current path) → CYCLE detected |
| Q17 | **(D) More than one** | ALL THREE properties of adjacency matrix for undirected graph are correct |
| Q18 | **(C) O(log n)** | Heapify (sift down) = O(height) = O(log n) for a heap |
| Q19 | **(C) Reverse Inorder** | Right→Root→Left gives descending order for BST |
| Q20 | **(C) Disjoint Set (Union-Find)** | Kruskal's uses Union-Find to detect if adding an edge creates a cycle |
| Q21 | **(C) n+1** | Full binary tree: n internal nodes → n+1 leaf nodes (always!) |
| Q22 | **(C)** | Inorder Successor = leftmost/minimum node in RIGHT subtree |
| Q23 | **(C) Red-Black Tree** | Java's TreeMap/TreeSet = internally Red-Black Tree |
| Q24 | **(C)** | Complete Binary Tree: all levels full except last, last filled L→R |
| Q25 | **(B) Only (i) and (ii)** | DLL: O(1) insert at beginning ✅, O(1) delete from end ✅. Access by index = O(n) ❌ |

---

## GS (SCIENCE REVISION) ANSWERS (Q26–Q50)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q26 | **(C) Inertia** | Newton's First Law = Law of Inertia |
| Q27 | **(C) Decreases** | Bernoulli: velocity ↑ → pressure ↓ (they are inversely related) |
| Q28 | **(B)** | Archimedes = floating objects. Ship floats because displaced water weight = ship weight |
| Q29 | **(C) Steel (solid)** | Sound travels fastest in SOLIDS > LIQUIDS > GASES |
| Q30 | **(C) Scurvy** | Vitamin C deficiency → SCURVY (bleeding gums, weak joints) |
| Q31 | **(E) Vitamin K** | Vitamin K = blood clotting / coagulation |
| Q32 | **(C) O** | Blood group O = Universal DONOR (can donate to all) |
| Q33 | **(B)** | Malaria = Plasmodium (Protozoan) via female Anopheles mosquito |
| Q34 | **(D) More than one** | ALL THREE statements about Diamond and Graphite are correct |
| Q35 | **(C) NaHCO₃** | Baking Soda = Sodium Bicarbonate = NaHCO₃ |
| Q36 | **(C) Nephron** | Nephron = functional unit of kidney. Alveolus = lungs. Villus = small intestine |
| Q37 | **(C) Oxygen (O₂)** | Photosynthesis releases OXYGEN (from splitting water in light reactions) |
| Q38 | **(C) Bacterium** | TB = Mycobacterium tuberculosis (bacteria, not virus or protozoan) |
| Q39 | **(C) 1 kcal** | 1000 (grass)→100 (grasshopper, 10%)→10 (frog, 10%)→1 (snake, 10%) |
| Q40 | **(C)** | Lichen=Fungus+Algae symbiosis ✅. Yeast=Fungi (not Plantae), Amoeba=Protista (not Monera) |
| Q41 | **(C) Group 18** | Noble/Inert gases = Group 18 (He, Ne, Ar, Kr, Xe, Rn) |
| Q42 | **(C) The nucleus** | Rutherford's gold foil experiment discovered the atomic nucleus in 1911 |
| Q43 | **(D) More than one** | ALL THREE vitamin statements are correct |
| Q44 | **(B)** | RIGHT ventricle → pumps deoxygenated blood to LUNGS. Left side carries oxygenated blood |
| Q45 | **(C) Battery acid** | Battery acid/conc. H₂SO₄ ≈ pH 0-1 (most acidic, lowest pH) |
| Q46 | **(B)** | Doppler: source approaching → frequency appears higher (pitch rises) |
| Q47 | **(C) Cyanocobalamin** | B12 = Cyanocobalamin. B1=Thiamine, B2=Riboflavin, C=Ascorbic Acid |
| Q48 | **(B)** | Pascal's Law → hydraulic machines (brakes, jack, press) |
| Q49 | **(B)** | Dengue = Flavivirus via Aedes mosquito (not Anopheles!) |
| Q50 | **(C) Small Intestine** | Maximum nutrient absorption in small intestine (villi increase surface area ~600x) |

---

## 📊 SCORE EVALUATION

```
┌─────────────────────────────────────────────┐
│  CS Score  (Q1–25):   _____ / 25            │
│  GS Score  (Q26–50):  _____ / 25            │
│  TOTAL:               _____ / 50            │
├─────────────────────────────────────────────┤
│  48–50: TOPPER LEVEL 🏆 — Outstanding!     │
│  43–47: Excellent — On Track ✅             │
│  38–42: Good — Target a few weak spots      │
│  28–37: Needs focused re-revision 📖        │
│  Below 28: Re-read full concept notes       │
└─────────────────────────────────────────────┘
```

---

## 🎯 WEEK 4 COMPLETE — WHAT YOU NOW KNOW

```
╔══════════════════════════════════════════════════════════════════╗
║              WEEK 4 MASTERY CHECKLIST                           ║
╠══════════════════════════════════════════════════════════════════╣
║ CS TOPICS (Days 22–28):                                         ║
║  ✅ Singly, Doubly, Circular Linked Lists                       ║
║  ✅ Binary Trees, Tree Traversals (Pre/In/Post/Level)           ║
║  ✅ BST properties, operations, Catalan numbers                 ║
║  ✅ Red-Black Trees (5 properties) + AVL Trees                  ║
║  ✅ Spanning Trees (N-1 edges) + MST algorithms                 ║
║  ✅ Heaps (Min/Max), array representation, complexity           ║
║  ✅ Graphs: BFS (Queue) + DFS (Stack)                           ║
║  ✅ Algorithm Paradigms vs Traversals                           ║
║  ✅ Dijkstra, Bellman-Ford, Floyd-Warshall                      ║
║                                                                  ║
║ GS TOPICS (Week 3–4):                                           ║
║  ✅ Physics: Newton's Laws, Bernoulli, Archimedes, Pascal       ║
║  ✅ Physics: Sound, Light, Electricity formulae                 ║
║  ✅ Chemistry: Atomic models, Periodic Table, Acids/Bases       ║
║  ✅ Chemistry: Common compounds, Carbon allotropes              ║
║  ✅ Biology: Five Kingdoms, Human Systems                       ║
║  ✅ Biology: Vitamins & Deficiency Diseases                     ║
║  ✅ Biology: Diseases & Causative Agents                        ║
║  ✅ Biology: Reproduction, Plant Hormones, Ecology              ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## 🔥 TRAP ANALYSIS — MOST COMMON BPSC MISTAKES

```
CS TRAPS:
1. "Random access in linked list = O(1)" → FALSE! It's O(n)
2. "C(3) = 14" → FALSE! C(4) = 14, C(3) = 5
3. "Build Heap = O(n log n)" → FALSE! Build Heap = O(n)
4. "BFS uses Stack" → FALSE! BFS uses QUEUE, DFS uses STACK
5. "Greedy is a graph traversal" → FALSE! It's an algorithm paradigm
6. "AVL is less strictly balanced than RB Tree" → FALSE! AVL is MORE strict
7. "Spanning tree with N vertices has N edges" → FALSE! It has N-1 edges
8. "Inorder of any tree gives sorted output" → FALSE! Only for BST!

GS TRAPS:
1. "Yeast is in Kingdom Plantae" → FALSE! Yeast is FUNGI
2. "Ginger grows from roots" → FALSE! Ginger = RHIZOME (stem)
3. "Sound travels fastest in air" → FALSE! Fastest in SOLIDS
4. "Universal recipient = O blood group" → FALSE! AB is universal recipient
5. "Dengue is spread by Anopheles" → FALSE! Dengue = Aedes mosquito
6. "Graphite doesn't conduct electricity" → FALSE! Graphite CONDUCTS
7. "Vitamin D deficiency causes Beri-Beri" → FALSE! B1 deficiency = Beri-Beri
8. "Pascal's Law = flight principle" → FALSE! Pascal = hydraulics; Bernoulli = flight
```

---

## 📝 NIGHT REVISION (Write from memory — 5 min):

1. Traversal orders for this tree: Root=A, Left=B, Right=C → Pre: ___ | In: ___ | Post: ___
2. C(4) = ___ | Spanning tree N vertices = ___ edges
3. BFS uses ___ | DFS uses ___ | Both time = ___
4. Vitamin C deficiency = ___ | Vitamin K role = ___ | Vitamin D deficiency = ___
5. Blood group O = Universal ___ | Blood group AB = Universal ___

**Answers:** 1. Pre:A,B,C | In:B,A,C | Post:B,C,A | 2. 14 | N-1 | 3. Queue, Stack, O(V+E) | 4. Scurvy, blood clotting, Rickets | 5. Donor, Recipient

---

*Day 28 of 170 Complete — Week 4 Done! 🎉 | BPSC TRE 4.0*
*CS Revision: Linked Lists + Trees + BST + RB Tree + Graphs*
*GS Revision: Biology + Physics + Chemistry Science Topics*
*Next: Day 29 — Big-O Notation & Time Complexity Analysis*
