# 📅 DAY 24 — BPSC TRE 4.0 TOPPER GUIDE
## CS: Trees — Basic Concepts & Binary Tree (Complete) | GS: Physics — Fluids, Bernoulli's Principle & Related Laws
### Phase 1 | Week 4 | Target: TOP RANK

---

> **🎯 Today's Targets:**
> - CS: Master ALL tree terminology, binary tree types, and ALL traversals with worked examples
> - GS: Master Physics — Pressure, Bernoulli's Principle, Pascal's Law, Archimedes' Principle + broader Physics laws
> - Solve: 25 CS + 25 GS PYQ-style questions (answers ONLY at the very end)
> - Special focus: "Randomized traversal" DOES NOT EXIST — BPSC trap!

---

# ═══════════════════════════════════════════════
# 🖥️ PART 1: COMPUTER SCIENCE
## TREES — COMPLETE TOPPER GUIDE
## Basic Concepts → Binary Tree → All Traversals
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A TREE?

A **Tree** is a **non-linear, hierarchical data structure** consisting of **nodes** connected by **edges**.

```
REAL WORLD ANALOGY:
         CEO                    ← ROOT (top of hierarchy)
        /    \
      VP1     VP2               ← INTERNAL NODES
     /   \      \
   Mgr1  Mgr2  Mgr3             ← INTERNAL NODES
   /  \
 Emp1 Emp2                      ← LEAF NODES (no children)
```

```
FORMAL TREE STRUCTURE:

              A               ← Root
            /   \
           B     C            ← Children of A (Level 1)
          / \   / \
         D   E F   G          ← Level 2
        / \
       H   I                  ← Level 3 (Leaves: E,F,G,H,I)
```

> 🔑 **KEY PROPERTY:** A tree with **N nodes** has exactly **N-1 edges**.
> This is a GUARANTEED PYQ fact — memorize it!

---

## 📌 SECTION 2: TREE TERMINOLOGY — EVERY TERM EXPLAINED

### The Reference Tree (used throughout this section):

```
              A               ← ROOT
            /   \
           B     C
          / \     \
         D   E     F
        /
       G
```

---

### Term 1: ROOT
```
Definition: The topmost node with NO parent.
Example: A is the root (it has no parent above it)
Every tree has EXACTLY ONE root.
```

---

### Term 2: NODE
```
Definition: Each element in a tree.
Example: A, B, C, D, E, F, G are all nodes.
Total nodes = 7
```

---

### Term 3: EDGE
```
Definition: Connection/link between a parent and child node.
Example: A→B, A→C, B→D, B→E, C→F, D→G are edges.
Total edges = 6 = (7 nodes - 1) = N-1
```

---

### Term 4: PARENT
```
Definition: A node that has one or more children.
Example:
  A is parent of B and C
  B is parent of D and E
  C is parent of F
  D is parent of G
```

---

### Term 5: CHILD
```
Definition: A node that has a parent.
Example:
  B and C are children of A
  D and E are children of B
  F is child of C
  G is child of D
```

---

### Term 6: LEAF NODE (also called External Node)
```
Definition: A node with NO children (degree = 0).
Example: E, F, G are leaf nodes
         (none of them have children)

MNEMONIC: Like leaves on a real tree — at the ends, no branches
```

---

### Term 7: INTERNAL NODE (also called Non-leaf Node)
```
Definition: A node with at least ONE child.
Example: A, B, C, D are internal nodes
         (all have at least one child)
```

---

### Term 8: DEGREE OF A NODE
```
Definition: Number of CHILDREN a node has.
Example (from our tree):
  Degree(A) = 2  (children: B, C)
  Degree(B) = 2  (children: D, E)
  Degree(C) = 1  (child: F)
  Degree(D) = 1  (child: G)
  Degree(E) = 0  (no children → leaf)
  Degree(F) = 0  (no children → leaf)
  Degree(G) = 0  (no children → leaf)

Degree of TREE = Maximum degree of any node = 2 (for node A or B)
```

---

### Term 9: DEGREE OF A TREE
```
Definition: Maximum degree (max children) among all nodes.
Example: In our tree, max degree = 2 (nodes A and B have 2 children)
∴ Degree of tree = 2
```

---

### Term 10: DEPTH OF A NODE
```
Definition: Number of EDGES from ROOT to that node.
           (Root has depth 0)

Example:
  Depth(A) = 0  (it IS the root)
  Depth(B) = 1  (A→B = 1 edge)
  Depth(C) = 1  (A→C = 1 edge)
  Depth(D) = 2  (A→B→D = 2 edges)
  Depth(E) = 2  (A→B→E = 2 edges)
  Depth(F) = 2  (A→C→F = 2 edges)
  Depth(G) = 3  (A→B→D→G = 3 edges)
```

> ⚠️ **CONFUSION ALERT:** Some books define depth starting at 1 (root = depth 1).
> BPSC standard: Root depth = 0. Watch the question carefully.

---

### Term 11: HEIGHT OF A NODE
```
Definition: Number of EDGES on LONGEST PATH from that node to a LEAF.
           (Leaf has height 0)

Example:
  Height(G) = 0  (G is a leaf)
  Height(E) = 0  (E is a leaf)
  Height(F) = 0  (F is a leaf)
  Height(D) = 1  (D→G = 1 edge)
  Height(B) = 2  (B→D→G = 2 edges — longest path from B)
  Height(C) = 1  (C→F = 1 edge)
  Height(A) = 3  (A→B→D→G = 3 edges — longest path from A)
```

---

### Term 12: HEIGHT OF A TREE
```
Definition: Height of the ROOT node = longest path from root to any leaf.

Example: Height of tree = Height(A) = 3
         (The path A→B→D→G has 3 edges)

ALTERNATIVE DEFINITION (some books):
  Height = number of NODES on longest path = 4 (A,B,D,G)

⚠️ BPSC typically uses: Height = number of EDGES = 3
```

---

### Term 13: LEVEL OF A NODE
```
Definition: Level = Depth + 1  (if root is at level 1)
         OR Level = Depth       (if root is at level 0)

Most common convention (root at level 1):
  Level(A) = 1  (root)
  Level(B) = 2
  Level(C) = 2
  Level(D) = 3
  Level(E) = 3
  Level(F) = 3
  Level(G) = 4
```

---

### Term 14: SIBLINGS
```
Definition: Nodes that share the SAME parent.
Example:
  B and C are siblings (both children of A)
  D and E are siblings (both children of B)
```

---

### Term 15: ANCESTOR & DESCENDANT
```
ANCESTOR of a node = All nodes on path from ROOT to that node
DESCENDANT of a node = All nodes in the subtree rooted at that node

Example:
  Ancestors of G = {D, B, A}  (path from root to G)
  Descendants of B = {D, E, G}  (entire subtree under B)
```

---

### Term 16: SUBTREE
```
Definition: Any node + all its descendants form a subtree.
Example:
  Subtree rooted at B:
       B
      / \
     D   E
    /
   G
```

---

### Term 17: FOREST
```
Definition: Collection of DISJOINT trees (no shared nodes/edges).
If you remove the root of a tree → it becomes a FOREST of subtrees.

Example: Remove A from our tree → Forest of {B's subtree, C's subtree}
```

---

## 📌 SECTION 3: SUMMARY DIAGRAM — ALL TERMS AT A GLANCE

```
                    A          ← ROOT (Level 1, Depth 0, Height 3)
                  /   \
                 B     C       ← Level 2, Depth 1
PARENT of D,E → B              
                / \     \
               D   E     F    ← Level 3, Depth 2
              /    ↑     ↑
CHILD of B → D   LEAF  LEAF   
            /
           G                  ← Level 4, Depth 3, LEAF, Height 0

EDGES: A-B, A-C, B-D, B-E, C-F, D-G = 6 edges = (7 nodes - 1)
LEAVES: E, F, G
INTERNAL: A, B, C, D
DEGREE of A = 2, DEGREE of B = 2, DEGREE of C = 1, DEGREE of D = 1
HEIGHT of tree = 3
```

---

## 📌 SECTION 4: BINARY TREE — THE MOST IMPORTANT TREE

A **Binary Tree** is a tree where each node has **AT MOST 2 children** (left child and right child).

```
BINARY TREE RULES:
  ✓ Max 2 children per node
  ✓ Children are distinguished as LEFT and RIGHT
  ✓ An empty tree is also a valid binary tree
  ✓ A single node (no children) = valid binary tree
```

### Binary Tree Node in C++:
```cpp
struct Node {
    int data;
    Node* left;   // left child
    Node* right;  // right child
};
```

### Binary Tree Node in Java:
```java
class Node {
    int data;
    Node left;   // left child
    Node right;  // right child
    Node(int d) { data = d; left = null; right = null; }
}
```

### Example Binary Tree:
```
          1
        /   \
       2     3
      / \   /
     4   5 6
```

---

## 📌 SECTION 5: TYPES OF BINARY TREES — CRITICAL FOR BPSC

### Type 1: FULL BINARY TREE (also called Strict/Proper)

```
RULE: Every node has EITHER 0 OR 2 children.
      NO node has exactly 1 child.

FULL (Correct):        NOT FULL (Wrong):
        1                      1
      /   \                  /   \
     2     3                2     3
    / \   / \              /
   4   5 6   7            4
↑ Every node has 0 or 2 children
```

> 🔑 **Formula for Full Binary Tree:**
> If there are **n** leaf nodes → there are **n-1** internal nodes.
> Total nodes = 2n - 1 (always ODD number of nodes)

---

### Type 2: COMPLETE BINARY TREE

```
RULE: All levels are COMPLETELY FILLED except POSSIBLY the LAST level.
      Last level nodes are FILLED FROM LEFT TO RIGHT.

COMPLETE (Correct):     NOT COMPLETE (Wrong):
        1                       1
      /   \                   /   \
     2     3                 2     3
    / \   /                 / \     \
   4   5 6               4   5      6
↑ Last level filled      ↑ Last level not left-to-right
  left to right

KEY: Heap is always a Complete Binary Tree!
     Array representation works best for Complete Binary Trees.
```

---

### Type 3: PERFECT BINARY TREE

```
RULE: ALL INTERNAL nodes have EXACTLY 2 children.
      ALL LEAF nodes are at the SAME level.
      
PERFECT (All levels full):
              1             ← Level 1: 1 node
            /   \
           2     3          ← Level 2: 2 nodes
          / \   / \
         4   5 6   7        ← Level 3: 4 nodes (ALL leaves)

FORMULA:
  Total nodes = 2^h - 1  (where h = height, counting levels)
  For h=3: 2³ - 1 = 7 nodes
  
  OR: If h = number of levels, nodes = 2^h - 1
  Nodes at level k = 2^(k-1)
  Leaf nodes in perfect tree of height h = 2^(h-1)
```

---

### Type 4: BALANCED BINARY TREE

```
RULE: Height difference between LEFT and RIGHT subtrees of EVERY node ≤ 1

BALANCED:              UNBALANCED (Skewed):
      1                      1
    /   \                     \
   2     3                     2
  / \   / \                     \
 4   5 6   7                     3
↑ Height diff = 0               ↑ Height diff = 2 (right much deeper)

AVL Tree = a self-balancing BST (always balanced)
Height of balanced tree = O(log n)
Height of skewed tree = O(n) ← worst case!
```

---

### Type 5: DEGENERATE (SKEWED) BINARY TREE

```
LEFT SKEWED:          RIGHT SKEWED:
    1                     1
   /                       \
  2                         2
 /                           \
3                             3
/                               \
4                                 4

ALL nodes have only ONE child.
HEIGHT = n-1 (for n nodes) ← WORST CASE!
Essentially becomes a LINKED LIST in structure.
```

---

### QUICK COMPARISON TABLE:

```
┌──────────────────┬─────────────────────────────────────────┐
│   TYPE           │           RULE / KEY FACT               │
├──────────────────┼─────────────────────────────────────────┤
│ Full BT          │ Every node: 0 or 2 children (never 1)   │
│ Complete BT      │ All filled except last; last = left→right│
│ Perfect BT       │ All internal: 2 children; all leaves same│
│                  │ level; nodes = 2^h - 1                  │
│ Balanced BT      │ |height(left) - height(right)| ≤ 1      │
│ Degenerate BT    │ Each node has only 1 child (like a list) │
└──────────────────┴─────────────────────────────────────────┘
```

---

## 📌 SECTION 6: BINARY TREE TRAVERSALS — THE HEART OF BPSC CS

Traversal = visiting EVERY node of the tree EXACTLY ONCE.

### There are EXACTLY 4 standard traversals:

```
1. PREORDER  (Root → Left → Right)    ← DLR
2. INORDER   (Left → Root → Right)    ← LDR
3. POSTORDER (Left → Right → Root)    ← LRD
4. LEVEL-ORDER (BFS — level by level) ← uses QUEUE
```

> ⚠️ **BPSC TRAP:** "Randomized traversal" or "Spiral traversal" are NOT standard traversals.
> Only Preorder, Inorder, Postorder, and Level-order are standard.
> This has appeared in multiple TRE papers!

---

### Reference Tree for ALL Traversal Examples:

```
           1
         /   \
        2     3
       / \   / \
      4   5 6   7
```

---

### Traversal 1: PREORDER — Root → Left → Right (DLR)

```
MNEMONIC: "ROOT FIRST" — visit root before children
          DLR = Data → Left → Right

ALGORITHM:
  preorder(node):
      if node is NULL: return
      print node.data        ← Visit ROOT first
      preorder(node.left)    ← Then LEFT subtree
      preorder(node.right)   ← Then RIGHT subtree

TRACE on our tree:
  Visit 1 (root) → print 1
  Go LEFT → Visit 2 → print 2
  Go LEFT of 2 → Visit 4 → print 4
  Go LEFT of 4 → NULL → return
  Go RIGHT of 4 → NULL → return
  Back to 2, Go RIGHT → Visit 5 → print 5
  ...continue...
  Go RIGHT of 1 → Visit 3 → print 3
  ...

PREORDER RESULT: 1, 2, 4, 5, 3, 6, 7
```

---

### Traversal 2: INORDER — Left → Root → Right (LDR)

```
MNEMONIC: "ROOT IN MIDDLE" — left, then root, then right
          LDR = Left → Data → Right

ALGORITHM:
  inorder(node):
      if node is NULL: return
      inorder(node.left)     ← Visit LEFT subtree first
      print node.data        ← Then ROOT
      inorder(node.right)    ← Then RIGHT subtree

TRACE on our tree:
  Go LEFT of 1 → go to 2
  Go LEFT of 2 → go to 4
  Go LEFT of 4 → NULL → return
  Print 4
  Go RIGHT of 4 → NULL → return
  Print 2
  Go RIGHT of 2 → go to 5
  Go LEFT of 5 → NULL → return
  Print 5
  Go RIGHT of 5 → NULL → return
  Print 1 (root of whole tree)
  Go RIGHT of 1 → go to 3
  ...

INORDER RESULT: 4, 2, 5, 1, 6, 3, 7

⭐ SPECIAL FACT: Inorder traversal of a BST gives SORTED (ascending) output!
```

---

### Traversal 3: POSTORDER — Left → Right → Root (LRD)

```
MNEMONIC: "ROOT LAST" — visit root after all children
          LRD = Left → Right → Data

ALGORITHM:
  postorder(node):
      if node is NULL: return
      postorder(node.left)   ← LEFT subtree first
      postorder(node.right)  ← Then RIGHT subtree
      print node.data        ← ROOT last

TRACE on our tree:
  Keep going left... reach 4 (leftmost)
  Go LEFT of 4 → NULL
  Go RIGHT of 4 → NULL
  Print 4
  ...
  Go RIGHT of 2 → reach 5
  Print 5
  Print 2 (after both children done)
  ...similarly for right subtree...
  Print 1 last (root is always last in postorder)

POSTORDER RESULT: 4, 5, 2, 6, 7, 3, 1

⭐ SPECIAL FACT: Root is ALWAYS LAST in postorder traversal.
⭐ Used in: Expression tree evaluation, deleting a tree (delete children before parent)
```

---

### Traversal 4: LEVEL-ORDER (Breadth-First Search / BFS)

```
MNEMONIC: "Level by level, left to right"
Uses a QUEUE data structure

ALGORITHM:
  level_order(root):
      if root is NULL: return
      queue.enqueue(root)
      while queue is not empty:
          node = queue.dequeue()
          print node.data
          if node.left ≠ NULL: queue.enqueue(node.left)
          if node.right ≠ NULL: queue.enqueue(node.right)

TRACE on our tree:
  Queue: [1]
  Dequeue 1, print 1 → Queue: [2, 3]
  Dequeue 2, print 2 → Queue: [3, 4, 5]
  Dequeue 3, print 3 → Queue: [4, 5, 6, 7]
  Dequeue 4, print 4 → Queue: [5, 6, 7]
  Dequeue 5, print 5 → Queue: [6, 7]
  Dequeue 6, print 6 → Queue: [7]
  Dequeue 7, print 7 → Queue: []

LEVEL-ORDER RESULT: 1, 2, 3, 4, 5, 6, 7
(Visits nodes level by level — like reading a tree left-to-right, top-to-bottom)
```

---

### MASTER TRAVERSAL SUMMARY TABLE:

```
┌─────────────┬────────────────────────┬──────────────────────────┐
│  TRAVERSAL  │      ORDER             │   RESULT (our tree)      │
├─────────────┼────────────────────────┼──────────────────────────┤
│ Preorder    │ Root → Left → Right    │ 1, 2, 4, 5, 3, 6, 7     │
│ Inorder     │ Left → Root → Right    │ 4, 2, 5, 1, 6, 3, 7     │
│ Postorder   │ Left → Right → Root    │ 4, 5, 2, 6, 7, 3, 1     │
│ Level-order │ Level by level (BFS)   │ 1, 2, 3, 4, 5, 6, 7     │
└─────────────┴────────────────────────┴──────────────────────────┘
```

> 🔑 **MEMORY TRICK:**
> Pre = Root is **Pre**first (before children)
> In = Root is **In** the middle
> Post = Root is **Post** last (after children)

---

## 📌 SECTION 7: TRAVERSAL ON A DIFFERENT TREE — PRACTICE

Let's trace all traversals on this tree:

```
        A
       / \
      B   C
     /     \
    D       E
```

```
PREORDER (Root-Left-Right):
  Visit A → go left → B → go left → D → go right → NULL
  Back → go right of B → NULL
  Back to A → go right → C → go left → NULL
  go right → E
  Result: A, B, D, C, E

INORDER (Left-Root-Right):
  Go all left: A→B→D
  D has no left → Print D
  Print B
  B's right → NULL
  Print A
  A's right → C → C has no left
  Print C
  C's right → E → Print E
  Result: D, B, A, C, E

POSTORDER (Left-Right-Root):
  Go left all way to D → Print D
  B has no right → Print B
  Go right of A → C → go right → E
  Print E → Print C → Print A
  Result: D, B, E, C, A

LEVEL-ORDER:
  Level 1: A
  Level 2: B, C
  Level 3: D, E
  Result: A, B, C, D, E
```

---

## 📌 SECTION 8: IMPORTANT TREE FORMULAS (BPSC EXAM)

```
┌────────────────────────────────────────────────┬────────────────────┐
│           FORMULA                              │    CONDITION       │
├────────────────────────────────────────────────┼────────────────────┤
│ N nodes → N-1 edges (ANY tree)                 │ Always true        │
│ Perfect BT height h: nodes = 2^h - 1           │ h = num of levels  │
│ Full BT: leaf nodes = internal nodes + 1       │ Full BT only       │
│ Complete BT: height = ⌊log₂n⌋                  │ n = num of nodes   │
│ Max nodes at level k = 2^(k-1)                 │ Level starts at 1  │
│ Max nodes in BT of height h = 2^h - 1          │ Perfect BT         │
│ Min nodes in BT of height h = h + 1            │ Skewed BT          │
│ Inorder of BST → sorted output                 │ BST only           │
└────────────────────────────────────────────────┴────────────────────┘
```

---

## 📌 SECTION 9: EXPRESSION TREE — IMPORTANT APPLICATION

Trees are used to represent arithmetic expressions:

```
Expression: (A + B) * (C - D)

Expression Tree:
          *
        /   \
       +     -
      / \   / \
     A   B C   D

POSTORDER gives POSTFIX:  A B + C D - *
INORDER gives INFIX:      A + B * C - D  (with brackets issues)
PREORDER gives PREFIX:    * + A B - C D
```

> ⚠️ **PYQ FACT:** Postorder traversal of an expression tree gives POSTFIX (Reverse Polish Notation).
> This connects Trees ↔ Stack (from Day 17) — expect combined questions!

---

## 📌 SECTION 10: PROPERTIES QUICK-FIRE (MEMORIZE!)

| # | Property | Answer |
|---|----------|--------|
| 1 | Tree with N nodes has __ edges | N-1 |
| 2 | Max children in binary tree | 2 |
| 3 | Perfect BT of height 3: total nodes | 15 (2⁴-1) |
| 4 | Inorder of BST gives | Sorted (ascending) order |
| 5 | Root in Postorder is | ALWAYS last |
| 6 | Root in Preorder is | ALWAYS first |
| 7 | BFS traversal uses | QUEUE |
| 8 | DFS traversal uses | STACK (or recursion) |
| 9 | Traversal that does NOT exist | Randomized traversal |
| 10 | Heap must be a | Complete Binary Tree |
| 11 | Full BT: leaves = internal + | 1 |
| 12 | Skewed tree height (n nodes) | n-1 |

---

# ═══════════════════════════════════════════════
# 📚 PART 2: GENERAL STUDIES
## PHYSICS — FLUIDS, PRESSURE, BERNOULLI'S PRINCIPLE
## + LAWS OF MOTION, SOUND, LIGHT, HEAT (BPSC COMPLETE)
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: PRESSURE — THE FOUNDATION

```
PRESSURE = Force / Area

Unit: Pascal (Pa) = N/m²
      1 atmosphere (atm) = 101,325 Pa ≈ 10⁵ Pa
      1 bar = 10⁵ Pa

KEY FACT: Pressure INCREASES with depth in a fluid.
          Pressure at depth h = ρgh
          where ρ = density, g = 9.8 m/s², h = depth
```

> ⚠️ **PYQ TRAP:** Pressure depends on DEPTH and DENSITY, NOT on the shape of the container.
> "Hydrostatic paradox" — same height of liquid gives same pressure at the bottom regardless of container shape.

---

## 📌 SECTION 2: PASCAL'S LAW — Complete Explanation

```
PASCAL'S LAW:
"Pressure applied to a CONFINED FLUID is transmitted 
 EQUALLY in ALL directions throughout the fluid."

                    F₁        F₂
                    ↓          ↑
               ┌────┴──────────┴────┐
               │    FLUID           │
               └───────────────────┘
                    A₁         A₂

FORMULA: P₁ = P₂
         F₁/A₁ = F₂/A₂
         
So: F₂ = F₁ × (A₂/A₁)
    If A₂ >> A₁ → F₂ >> F₁ (force multiplication!)
```

### Applications of Pascal's Law:

```
APPLICATIONS:
1. HYDRAULIC JACK/LIFT
   Small force on small piston → Large force on large piston
   Used to lift cars in garages

2. HYDRAULIC BRAKES (in cars)
   Foot pressure on pedal → Equal pressure to all 4 wheels

3. HYDRAULIC PRESS
   Used in industries to press/shape metals

4. BLOOD PRESSURE
   Heart pumps blood → pressure transmitted through blood vessels
```

> ⚠️ **BPSC PYQ:** "Hydraulic brakes work on which principle?"
> **Answer: Pascal's Law**

---

## 📌 SECTION 3: ARCHIMEDES' PRINCIPLE

```
ARCHIMEDES' PRINCIPLE:
"When a body is partially or fully immersed in a fluid, 
 it experiences an UPWARD FORCE (BUOYANT FORCE / UPTHRUST)
 equal to the WEIGHT OF FLUID DISPLACED."

                ┌──────────┐
                │  Object  │  ← Weight (W) acting DOWN
                │  in      │
                │  water   │  ← Buoyant force (FB) acting UP
                └──────────┘

Buoyant Force (FB) = Weight of displaced fluid
                   = ρ_fluid × V_displaced × g

CONDITIONS:
  FB > W → Object FLOATS (less dense than fluid)
  FB = W → Object is in EQUILIBRIUM (neutral buoyancy, like submarines)
  FB < W → Object SINKS (more dense than fluid)
```

### ARCHIMEDES' DISCOVERY — The Story:
```
King Hiero asked if his crown was pure gold.
Archimedes got in the bath → water overflowed.
He realized volume of water displaced = volume of his body!
He ran out shouting "EUREKA!" (I have found it!)
He could now measure volume of any irregular shape
and thus determine density and purity of gold.
```

### Laws of Floatation:
```
LAW 1: A floating body displaces fluid equal to its own WEIGHT
LAW 2: Centre of buoyancy is directly below centre of gravity of floating body

WHY IRON SHIP FLOATS but IRON NAIL SINKS?
  Nail: Dense, small volume → FB < Weight → sinks
  Ship: Hollow, displaces MUCH more water → FB = Weight → floats
  The SHAPE matters — ships are hollow to displace more water
```

> ⚠️ **BPSC PYQ:** "When a body floats, the weight of water displaced is ___"
> **Answer: Equal to the weight of the body** (not the volume!)

---

## 📌 SECTION 4: BERNOULLI'S PRINCIPLE — MOST IMPORTANT

```
BERNOULLI'S PRINCIPLE (1738, Daniel Bernoulli):
"In a STREAMLINED flow of an IDEAL fluid, the TOTAL ENERGY 
 per unit volume is CONSTANT throughout the flow."

BERNOULLI'S EQUATION:
P + ½ρv² + ρgh = constant

Where:
  P    = pressure
  ρ    = density of fluid
  v    = velocity of fluid
  g    = gravitational acceleration
  h    = height

KEY INSIGHT:
When VELOCITY INCREASES → PRESSURE DECREASES
When VELOCITY DECREASES → PRESSURE INCREASES

"High speed → Low pressure"
"Low speed → High pressure"
```

### Visual of Bernoulli's Principle:

```
Wide pipe (slow) → Narrow pipe (fast) → Wide pipe (slow)
    ↓                    ↓                    ↓
 Low velocity         High velocity        Low velocity
 High pressure        LOW PRESSURE         High pressure

─────────────────────────────────────────────────────────
    Wide          Narrow (venturi)          Wide
──────────┐   ┌──────────────────┐   ┌───────────────────
          │   │                  │   │
          │   │  ──────────────► │   │
          └───┘                  └───┘
  P high       P LOW (fast flow)       P high
```

---

### Applications of Bernoulli's Principle:

```
APPLICATION 1: AEROPLANE WING (LIFT)
  Top of wing = curved (longer path) → air moves FASTER → LOW PRESSURE
  Bottom of wing = flat (shorter path) → air moves SLOWER → HIGH PRESSURE
  
  Low P (top)                 ← ← ← (lift direction)
  ────────────────────────────────
  ══════════════════════════════  ← Wing shape
  ────────────────────────────────
  High P (bottom)
  
  Net upward force = LIFT
  This is why planes can fly!

APPLICATION 2: VENTURI METER
  Narrow tube → faster fluid → lower pressure
  Used to MEASURE FLOW RATE of fluids in pipes
  Used in carburetors of engines

APPLICATION 3: ATOMIZER / SPRAY BOTTLE / PERFUME PUMP
  Fast air over narrow tube → low pressure above liquid
  Atmospheric pressure pushes liquid UP → spray!
  Used in: Insecticide sprays, perfume bottles, paint sprayers

APPLICATION 4: CRICKET BALL SWING
  Rough side vs smooth side of cricket ball
  Air moves faster over smooth side → lower pressure there
  Ball curves toward the rough side (swing!)

APPLICATION 5: MAGNUS EFFECT (Spinning ball)
  A spinning ball curves in the direction of spin (football curve, cricket spin)
  Higher velocity on one side → lower pressure → curve

APPLICATION 6: BUNSEN BURNER
  Fast gas through small jet → low pressure → air is sucked in → good combustion

APPLICATION 7: BLOWING BETWEEN TWO PAPER SHEETS
  Blow air between two hanging sheets → they COME TOGETHER (don't separate!)
  High velocity air between sheets → low pressure → atmospheric pressure pushes them together

APPLICATION 8: ROOFTOPS BLOW OFF IN STORMS
  Wind speed is HIGH on top → low pressure above roof
  Atmospheric pressure inside house = higher
  Net upward force → roof flies off!
```

---

## 📌 SECTION 5: NEWTON'S LAWS OF MOTION

```
NEWTON'S FIRST LAW (Law of Inertia):
"A body continues in its state of rest or uniform motion in a 
 straight line unless acted upon by an external force."

  INERTIA = resistance to change in state
  More mass = more inertia
  Examples: Passengers jerk forward when bus brakes (inertia of motion)
            Cloth table trick (inertia of rest — dishes stay put)

NEWTON'S SECOND LAW (Law of Force):
  F = ma
  Force = mass × acceleration
  Unit: Newton (N) = kg⋅m/s²
  
  Momentum (p) = mv
  F = dp/dt (rate of change of momentum)

NEWTON'S THIRD LAW (Action-Reaction):
"For every action, there is an equal and opposite reaction."
  
  Examples:
  → Rocket propulsion: exhaust gas goes down → rocket goes up
  → Swimming: push water backward → move forward
  → Gun recoil: bullet goes forward → gun kicks back
  → Walking: push ground backward → move forward
```

---

## 📌 SECTION 6: SOUND WAVES — KEY FACTS

```
SOUND:
  Type: Longitudinal wave (compression and rarefaction)
  Speed in air: 343 m/s at 20°C (approximately 330-340 m/s)
  Speed: SOLID > LIQUID > GAS
  Cannot travel in VACUUM (needs medium)
  Frequency: 20 Hz to 20,000 Hz (human hearing range)

INFRASOUND: < 20 Hz (below human hearing)
  → Produced by: earthquakes, elephants, whales
  
ULTRASOUND: > 20,000 Hz (above human hearing)
  → Used in: SONAR, medical imaging (USG), cleaning jewellery,
    detecting cracks in metals, echolocation (bats)

DOPPLER EFFECT:
  When source and observer are in relative motion,
  perceived frequency CHANGES.
  Source approaching → frequency INCREASES (higher pitch)
  Source moving away → frequency DECREASES (lower pitch)
  Examples: Ambulance siren changing pitch, police radar gun,
            weather forecasting (Doppler radar)

ECHO: Reflected sound
  Minimum distance for echo = 17 metres (at 20°C)
  Time for echo = 0.1 seconds minimum
  (Because sound takes 1/10 sec to travel 34m = 17m there + 17m back)

SONAR = Sound Navigation And Ranging
  Uses ultrasound to detect underwater objects
  Used in submarines, measuring ocean depth
```

---

## 📌 SECTION 7: LIGHT — KEY FACTS

```
LIGHT:
  Type: Transverse electromagnetic wave
  Speed in vacuum: 3 × 10⁸ m/s (c)
  Can travel in VACUUM (unlike sound)

REFLECTION OF LIGHT:
  Angle of incidence = Angle of reflection
  Incident ray, reflected ray, normal → in same plane

REFRACTION (Snell's Law):
  n₁ sin θ₁ = n₂ sin θ₂
  Light bends when going from one medium to another
  
  Optical density increases → speed decreases → bends toward normal
  Denser medium (glass) → slower light → bends toward normal

TOTAL INTERNAL REFLECTION:
  Light going from denser to rarer medium at angle > critical angle
  → Light reflects back completely (no refraction)
  Applications: Optical fibre, diamond sparkle, mirage

OPTICAL FIBRE:
  Uses total internal reflection
  Light travels through glass fibre even around bends
  Used in: Internet cables, medical endoscopy

DISPERSION (Rainbow/Prism):
  White light = combination of 7 colors (VIBGYOR)
  Prism separates them because different colors have different speeds
  VIOLET bends MOST, RED bends LEAST
  
  V I B G Y O R
  Violet (most bent) → Indigo → Blue → Green → Yellow → Orange → Red (least bent)
```

---

## 📌 SECTION 8: HEAT & THERMODYNAMICS

```
TEMPERATURE SCALES:
  Celsius → Kelvin: K = °C + 273
  Celsius → Fahrenheit: °F = (9/5)°C + 32
  Absolute zero = 0 K = -273°C (lowest possible temperature)

HEAT TRANSFER:
  CONDUCTION: heat transfer through solids (molecule-to-molecule)
              Example: Metal rod in fire
  CONVECTION: heat transfer through liquids and gases (bulk movement)
              Example: Room heater, sea breeze
  RADIATION: heat transfer without medium (electromagnetic waves)
             Example: Sunlight reaching Earth, microwave oven

SPECIFIC HEAT CAPACITY:
  Amount of heat needed to raise 1 kg of substance by 1°C
  Water has HIGHEST specific heat (4200 J/kg°C)
  This is why: coastal areas have moderate climate,
               water is used as coolant in engines

LAWS OF THERMODYNAMICS:
  0th Law: If A=B in temperature AND B=C in temperature, then A=C
           (Basis of thermometer)
  
  1st Law: Energy cannot be created or destroyed; only converted
           ΔU = Q - W (energy is conserved)
           
  2nd Law: Heat flows naturally from HOT to COLD (not reverse)
           Entropy (disorder) of universe always increases
           No heat engine can be 100% efficient
           
  3rd Law: At absolute zero (0 K), entropy of pure crystal = 0
```

---

## 📌 SECTION 9: ELECTRICITY — KEY FORMULAS

```
OHM'S LAW: V = IR
  V = Voltage (Volts), I = Current (Amperes), R = Resistance (Ohms)

POWER FORMULAS:
  P = VI = I²R = V²/R
  
  PYQ GOLD: If current is doubled (2I):
    Power = (2I)²R = 4I²R = 4P  ← Power becomes 4 times!
    
  If resistance is doubled (2R):
    Power = I²(2R) = 2I²R = 2P  ← Power doubles

SERIES CIRCUIT:
  Same current flows through all
  R_total = R₁ + R₂ + R₃
  Voltage divides

PARALLEL CIRCUIT:
  Same voltage across all
  1/R_total = 1/R₁ + 1/R₂ + 1/R₃
  Current divides
  
  BPSC TRAP: In parallel circuit, total resistance is LESS than smallest individual resistance
```

---

## 📌 SECTION 10: IMPORTANT SCIENTIFIC LAWS — QUICK REFERENCE

| Law | Scientist | Statement |
|-----|-----------|-----------|
| Law of Gravitation | Newton | F = Gm₁m₂/r² |
| Laws of Motion | Newton | F=ma, action-reaction |
| Bernoulli's Principle | Daniel Bernoulli | High velocity → Low pressure |
| Pascal's Law | Blaise Pascal | Pressure transmitted equally in fluids |
| Archimedes' Principle | Archimedes | Buoyant force = weight of displaced fluid |
| Ohm's Law | Georg Ohm | V = IR |
| Snell's Law | Willebrord Snell | n₁sinθ₁ = n₂sinθ₂ |
| Boyle's Law | Robert Boyle | P₁V₁ = P₂V₂ (constant temperature) |
| Charles' Law | Jacques Charles | V₁/T₁ = V₂/T₂ (constant pressure) |
| Hooke's Law | Robert Hooke | F = kx (spring force) |
| Doppler Effect | Christian Doppler | Apparent frequency changes with motion |

---

## 📌 SECTION 11: SCIENTIFIC INSTRUMENTS — BPSC FREQUENCY

```
┌─────────────────────┬────────────────────────────────────────┐
│   INSTRUMENT        │         MEASURES / PURPOSE             │
├─────────────────────┼────────────────────────────────────────┤
│ Barometer           │ Atmospheric pressure                   │
│ Thermometer         │ Temperature                            │
│ Manometer           │ Gas pressure                           │
│ Sphygmomanometer    │ Blood pressure                         │
│ Hygrometer          │ Humidity of air                        │
│ Anemometer          │ Wind speed                             │
│ Seismograph         │ Earthquake intensity                   │
│ Lactometer          │ Purity/density of milk                 │
│ Ammeter             │ Electric current (in series)           │
│ Voltmeter           │ Voltage (in parallel)                  │
│ Galvanometer        │ Small electric current                 │
│ Tachometer          │ Rotational/angular speed               │
│ Altimeter           │ Altitude (height above sea level)      │
│ Speedometer         │ Speed of vehicle                       │
│ Odometer            │ Distance traveled by vehicle           │
│ Calorimeter         │ Heat capacity of substances            │
│ Geiger counter      │ Radioactivity                          │
│ Audiometer          │ Intensity of sound / hearing ability   │
│ Hydrometer          │ Relative density of liquids            │
└─────────────────────┴────────────────────────────────────────┘
```

---

## 📌 SECTION 12: BIHAR-SPECIFIC SCIENCE FACTS

```
BIHAR SCIENCE CONTEXT:
→ Nalanda University (ancient) — had science subjects including Astronomy
→ Aryabhata (born in Pataliputra, Bihar, 476 AD):
   • Calculated value of π (pi) = 3.1416
   • Stated Earth rotates on its axis
   • Calculated Earth's circumference
   • Explained lunar eclipse correctly
   
→ Bihar has Thermal Power Plants using physics of thermodynamics:
   Barauni Thermal Power Station (Begusarai)
   Muzaffarpur Thermal Power Station
   
→ Gandhi Setu (Patna): Longest river bridge in India over Ganga
   Engineering uses principles of pressure, buoyancy, structural design
```

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 1 (CS)
## 25 Questions on Trees & Binary Trees
### ⚠️ SOLVE ALL 25 BEFORE LOOKING AT ANSWERS (AT END)
# ═══════════════════════════════════════════════

---

**Q1.** A tree with 10 nodes has how many edges?
- (A) 10
- (B) 9
- (C) 11
- (D) More than one of the above
- (E) None of the above

---

**Q2.** Which of the following is NOT a standard binary tree traversal?
- (A) Inorder traversal
- (B) Postorder traversal
- (C) Randomized traversal
- (D) More than one of the above
- (E) None of the above

---

**Q3.** In a binary tree, the maximum number of children any node can have is:
- (A) 1
- (B) 2
- (C) Any number
- (D) More than one of the above
- (E) None of the above

---

**Q4.** Inorder traversal of a BINARY SEARCH TREE (BST) gives:
- (A) Reverse sorted (descending) output
- (B) Sorted (ascending) output
- (C) Random output
- (D) More than one of the above
- (E) None of the above

---

**Q5.** In PREORDER traversal, the ROOT is visited:
- (A) Last
- (B) Between left and right subtrees
- (C) First (before all children)
- (D) More than one of the above
- (E) None of the above

---

**Q6.** In POSTORDER traversal, the ROOT is visited:
- (A) First
- (B) Between left and right subtrees
- (C) Last (after all children)
- (D) More than one of the above
- (E) None of the above

---

**Q7.** LEVEL-ORDER traversal uses which auxiliary data structure?
- (A) Stack
- (B) Queue
- (C) Linked List
- (D) More than one of the above
- (E) None of the above

---

**Q8.** Which type of binary tree has EVERY node with EITHER 0 or 2 children (never exactly 1)?
- (A) Complete binary tree
- (B) Perfect binary tree
- (C) Full (Strict) binary tree
- (D) More than one of the above
- (E) None of the above

---

**Q9.** A PERFECT binary tree of height 3 (3 levels below root, 4 levels total) has how many nodes?
- (A) 7
- (B) 15
- (C) 31
- (D) More than one of the above
- (E) None of the above

---

**Q10.** In a COMPLETE binary tree, the last level is:
- (A) Always completely filled
- (B) Filled from LEFT to RIGHT (may not be completely full)
- (C) Filled from RIGHT to LEFT
- (D) More than one of the above
- (E) None of the above

---

**Q11.** Consider this binary tree:
```
      1
     / \
    2   3
   /
  4
```
What is the INORDER traversal?
- (A) 1, 2, 4, 3
- (B) 4, 2, 1, 3
- (C) 4, 2, 3, 1
- (D) More than one of the above
- (E) None of the above

---

**Q12.** For the SAME tree in Q11, what is the PREORDER traversal?
- (A) 1, 2, 4, 3
- (B) 4, 2, 1, 3
- (C) 4, 1, 2, 3
- (D) More than one of the above
- (E) None of the above

---

**Q13.** For the SAME tree in Q11, what is the POSTORDER traversal?
- (A) 4, 2, 1, 3
- (B) 4, 2, 3, 1
- (C) 1, 2, 4, 3
- (D) More than one of the above
- (E) None of the above

---

**Q14.** Which traversal is used to EVALUATE an expression tree (get postfix expression)?
- (A) Preorder traversal
- (B) Inorder traversal
- (C) Postorder traversal
- (D) More than one of the above
- (E) None of the above

---

**Q15.** A node with NO children is called a:
- (A) Root node
- (B) Internal node
- (C) Leaf node
- (D) More than one of the above
- (E) None of the above

---

**Q16.** The HEIGHT of a tree is defined as:
- (A) Number of nodes from root to the deepest leaf
- (B) Number of edges on the longest path from root to a leaf
- (C) Number of levels in the tree
- (D) More than one of the above
- (E) None of the above

---

**Q17.** In a FULL BINARY TREE with 7 leaf nodes, how many internal (non-leaf) nodes are there?
- (A) 6
- (B) 7
- (C) 8
- (D) More than one of the above
- (E) None of the above

---

**Q18.** A SKEWED (degenerate) binary tree with n nodes has height equal to:
- (A) log₂n
- (B) n/2
- (C) n-1
- (D) More than one of the above
- (E) None of the above

---

**Q19.** Which of the following traversals visits nodes in LEVEL-BY-LEVEL order (Breadth-First)?
- (A) Preorder
- (B) Postorder
- (C) Level-order (BFS)
- (D) More than one of the above
- (E) None of the above

---

**Q20.** Which of the following statements about binary tree traversal is TRUE?
- (A) Preorder: Left → Root → Right
- (B) Inorder: Left → Root → Right
- (C) Postorder: Left → Root → Right
- (D) More than one of the above
- (E) None of the above

---

**Q21.** The DEGREE of a tree is defined as:
- (A) Number of nodes in the tree
- (B) Maximum degree (children) of any node in the tree
- (C) Total number of edges in the tree
- (D) More than one of the above
- (E) None of the above

---

**Q22.** Consider a binary tree. If only INORDER and PREORDER traversals are given, can we UNIQUELY reconstruct the original tree?
- (A) No — we need all three traversals
- (B) Yes — two traversals (if one is inorder) are sufficient to uniquely reconstruct
- (C) No — two traversals are never sufficient
- (D) More than one of the above
- (E) None of the above

---

**Q23.** A HEAP is always which type of binary tree?
- (A) Full binary tree
- (B) Perfect binary tree
- (C) Complete binary tree
- (D) More than one of the above
- (E) None of the above

---

**Q24.** Which of the following is TRUE about ANCESTORS of a node in a tree?
- (A) Ancestors are nodes in the left subtree
- (B) Ancestors are all nodes on the path from the root to that node
- (C) Ancestors are the children of that node
- (D) More than one of the above
- (E) None of the above

---

**Q25.** Two nodes are called SIBLINGS if:
- (A) They have the same number of children
- (B) They are at the same depth/level
- (C) They share the same parent node
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 2 (GS)
## 25 Questions on Physics
### ⚠️ SOLVE ALL 25 BEFORE LOOKING AT ANSWERS (AT END)
# ═══════════════════════════════════════════════

---

**Q26.** Bernoulli's Principle states that in a streamlined fluid flow, when velocity of fluid INCREASES, pressure:
- (A) Also increases
- (B) Decreases
- (C) Remains unchanged
- (D) More than one of the above
- (E) None of the above

---

**Q27.** The working principle of a HYDRAULIC JACK (car lift) is based on:
- (A) Archimedes' Principle
- (B) Bernoulli's Principle
- (C) Pascal's Law
- (D) More than one of the above
- (E) None of the above

---

**Q28.** An object immersed in a fluid experiences an UPWARD BUOYANT FORCE equal to:
- (A) Weight of the object
- (B) Weight of the fluid displaced by the object
- (C) Volume of the object
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Why does a heavy iron SHIP float on water while an iron NAIL sinks?
- (A) Ship is made of a different type of iron
- (B) Ship is hollow and displaces water equal to its own weight; nail does not
- (C) Ship moves through water faster
- (D) More than one of the above
- (E) None of the above

---

**Q30.** The LIFT force on an aeroplane wing is explained by:
- (A) Newton's Third Law
- (B) Pascal's Law
- (C) Bernoulli's Principle
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Which of the following CORRECTLY uses Bernoulli's Principle?
- (A) Atomizer / spray bottle
- (B) Venturi meter
- (C) Hydraulic brake
- (D) More than one of the above
- (E) None of the above

---

**Q32.** Newton's FIRST Law of Motion is also called:
- (A) Law of Force
- (B) Law of Inertia
- (C) Law of Action-Reaction
- (D) More than one of the above
- (E) None of the above

---

**Q33.** A gun recoils when fired. This is an example of Newton's:
- (A) First Law
- (B) Second Law
- (C) Third Law
- (D) More than one of the above
- (E) None of the above

---

**Q34.** The speed of SOUND is GREATEST in:
- (A) Air
- (B) Water
- (C) Steel/Solid
- (D) More than one of the above
- (E) None of the above

---

**Q35.** ULTRASOUND has frequency:
- (A) Less than 20 Hz
- (B) Between 20 Hz and 20,000 Hz
- (C) Greater than 20,000 Hz
- (D) More than one of the above
- (E) None of the above

---

**Q36.** SONAR works on the principle of:
- (A) Reflection of light
- (B) Reflection of ultrasound
- (C) Refraction of sound
- (D) More than one of the above
- (E) None of the above

---

**Q37.** When white light passes through a prism, which color is MOST DEVIATED (bent)?
- (A) Red
- (B) Yellow
- (C) Violet
- (D) More than one of the above
- (E) None of the above

---

**Q38.** OPTICAL FIBRE works on the principle of:
- (A) Refraction of light
- (B) Total Internal Reflection of light
- (C) Reflection of light from mirror
- (D) More than one of the above
- (E) None of the above

---

**Q39.** Which instrument is used to measure BLOOD PRESSURE?
- (A) Barometer
- (B) Sphygmomanometer
- (C) Hydrometer
- (D) More than one of the above
- (E) None of the above

---

**Q40.** The formula F = ma represents Newton's:
- (A) First Law
- (B) Second Law
- (C) Third Law
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Which of the following is a correct formula for ELECTRICAL POWER?
- (A) P = VI
- (B) P = I²R
- (C) P = V²/R
- (D) More than one of the above
- (E) None of the above

---

**Q42.** ARYABHATA, the ancient Indian mathematician-astronomer, was born in which region?
- (A) Pataliputra (modern-day Bihar)
- (B) Ujjain (Madhya Pradesh)
- (C) Taxila (Pakistan)
- (D) More than one of the above
- (E) None of the above

---

**Q43.** The DOPPLER EFFECT describes:
- (A) Change in amplitude of sound due to source motion
- (B) Change in apparent frequency of sound due to relative motion between source and observer
- (C) Change in speed of sound in different media
- (D) More than one of the above
- (E) None of the above

---

**Q44.** According to the 2nd Law of Thermodynamics:
- (A) Energy is conserved
- (B) Heat naturally flows from HOT to COLD, not the reverse
- (C) At absolute zero, entropy is zero
- (D) More than one of the above
- (E) None of the above

---

**Q45.** The SI unit of PRESSURE is:
- (A) Newton
- (B) Joule
- (C) Pascal
- (D) More than one of the above
- (E) None of the above

---

**Q46.** Conversion from Celsius to Kelvin: 100°C equals:
- (A) 273 K
- (B) 373 K
- (C) 100 K
- (D) More than one of the above
- (E) None of the above

---

**Q47.** When two paper sheets are suspended parallel and you blow air BETWEEN them, the sheets:
- (A) Move apart (repel each other)
- (B) Come together (attract each other)
- (C) Stay in the same position
- (D) More than one of the above
- (E) None of the above

---

**Q48.** Which of the following is an application of ARCHIMEDES' PRINCIPLE?
- (A) Designing ships and submarines
- (B) Lactometer to test purity of milk
- (C) Hydrometer to measure density of liquids
- (D) More than one of the above
- (E) None of the above

---

**Q49.** The instrument used to measure WIND SPEED is:
- (A) Hygrometer
- (B) Barometer
- (C) Anemometer
- (D) More than one of the above
- (E) None of the above

---

**Q50.** In a PARALLEL electric circuit, the total resistance is:
- (A) Greater than the largest individual resistance
- (B) Equal to the sum of all individual resistances
- (C) Less than the smallest individual resistance
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY WITH DETAILED EXPLANATIONS
## CS Answers (Q1–Q25) | GS Answers (Q26–Q50)
# ═══════════════════════════════════════════════

---

## 🖥️ CS ANSWERS — TREES & BINARY TREES

---

**A1. → (B) 9**
RULE: A tree with N nodes always has N-1 edges.
10 nodes → 10-1 = 9 edges. This is a fundamental tree property — always true regardless of tree type.

---

**A2. → (C) Randomized traversal**
Standard traversals: Preorder, Inorder, Postorder, Level-order (BFS).
"Randomized traversal" does NOT exist. This is a classic BPSC trap. Options A and B are valid traversals.

---

**A3. → (B) 2**
By definition: Binary tree = each node has AT MOST 2 children.
"Binary" = two. A node can have 0, 1, or 2 children — never more than 2.

---

**A4. → (B) Sorted (ascending) output**
This is a golden fact: Inorder traversal (Left → Root → Right) of a BST gives keys in sorted ascending order. This is because BST property ensures left < root < right at every node.

---

**A5. → (C) First (before all children)**
PREORDER = Root FIRST, then Left, then Right (DLR).
"Pre" means before — root is visited before any children.

---

**A6. → (C) Last (after all children)**
POSTORDER = Left, Right, Root LAST (LRD).
"Post" means after — root is visited after all children.
Root is ALWAYS last in postorder output.

---

**A7. → (B) Queue**
Level-order traversal = BFS (Breadth-First Search).
It uses a QUEUE: enqueue root, dequeue and print, enqueue left child, enqueue right child, repeat.
DFS traversals (Pre/In/Post) use STACK (or recursion which uses call stack).

---

**A8. → (C) Full (Strict) binary tree**
Full BT = every node has 0 or 2 children (never exactly 1).
Complete BT = last level filled left to right (can have 1 child).
Perfect BT = all levels full (also qualifies as full, but the specific definition here is "full").

---

**A9. → (B) 15**
Perfect BT of height h (counting from root): nodes = 2^h - 1.
Here "height 3" means 4 levels (root at level 1): nodes = 2⁴ - 1 = 16 - 1 = 15.
Alternatively, nodes = 1+2+4+8 = 15.

---

**A10. → (B) Filled from LEFT to RIGHT**
Complete binary tree: ALL levels full EXCEPT POSSIBLY the last level.
Last level: nodes are filled strictly LEFT to RIGHT.
There must be no "gaps" — you can't skip left and fill right.

---

**A11. → (B) 4, 2, 1, 3**
Tree: 1 (root), left child 2, right child 3, 2's left child is 4.
INORDER = Left → Root → Right:
- Go left of 1 → reach 2 → go left of 2 → reach 4 → no left child
- Print 4 → return to 2 → Print 2 → no right child of 2
- Return to 1 → Print 1 → go right → reach 3 → Print 3
- Result: 4, 2, 1, 3 ✓

---

**A12. → (A) 1, 2, 4, 3**
PREORDER = Root → Left → Right:
- Print 1 (root) → go left → Print 2 → go left of 2 → Print 4 → no more left
- return → no right of 2 → return to 1 → go right → Print 3
- Result: 1, 2, 4, 3 ✓

---

**A13. → (B) 4, 2, 3, 1**
POSTORDER = Left → Right → Root:
- Go all the way left: reach 4 → Print 4
- No right child of 2 → Print 2
- Go right of 1: reach 3 → Print 3
- Print 1 (root, always last)
- Result: 4, 2, 3, 1 ✓

---

**A14. → (C) Postorder traversal**
Postorder traversal of an expression tree gives POSTFIX (Reverse Polish Notation).
Example: Expression (A+B)*C → Postorder gives: A B + C *
Preorder gives Prefix; Inorder gives Infix (with issues).

---

**A15. → (C) Leaf node**
Leaf node = node with NO children = degree 0.
Also called external node or terminal node.
Root = topmost node. Internal node = has at least one child.

---

**A16. → (B) Number of edges on the longest path from root to a leaf**
Height = edges on longest root-to-leaf path.
A leaf has height 0. Root's height = tree's height.
Option A describes nodes on path (which would be height+1).

---

**A17. → (A) 6**
Full BT formula: number of leaf nodes = number of internal nodes + 1
Therefore: leaf nodes = internal nodes + 1
→ 7 = internal nodes + 1
→ internal nodes = 6 ✓

---

**A18. → (C) n-1**
Skewed tree = all nodes have only one child (like a linked list).
For n nodes: root at top, then n-1 nodes in a chain → height = n-1.
This is the WORST CASE height for a binary tree.

---

**A19. → (C) Level-order (BFS)**
Level-order = visits all nodes at level 1, then all at level 2, etc.
This is Breadth-First Search (BFS) using a Queue.
Pre/In/Postorder are all Depth-First Search (DFS).

---

**A20. → (B) Inorder: Left → Root → Right**
- Preorder = Root → Left → Right (option A says "Left → Root → Right" which is WRONG for preorder)
- Inorder = Left → Root → Right (option B is CORRECT)
- Postorder = Left → Right → Root (not Left → Root → Right)
Answer = (B) only.

---

**A21. → (B) Maximum degree (children) of any node in the tree**
Degree of a node = number of its children.
Degree of a TREE = maximum degree among all nodes.
For a binary tree, degree ≤ 2.

---

**A22. → (B) Yes — two traversals (if one is inorder) are sufficient**
INORDER + PREORDER → uniquely reconstruct the tree.
INORDER + POSTORDER → uniquely reconstruct the tree.
PREORDER + POSTORDER → may NOT be unique (ambiguous cases).
The KEY is that INORDER must be one of the two.

---

**A23. → (C) Complete binary tree**
HEAP (Min-Heap or Max-Heap) is ALWAYS a Complete Binary Tree.
- Complete BT property allows efficient array representation of heap.
- Array index: Parent at i, left child at 2i+1, right child at 2i+2.

---

**A24. → (B) Ancestors are all nodes on the path from the root to that node**
Ancestors = all nodes you pass through going from ROOT to the given node.
Example: For node G in tree A-B-D-G: ancestors of G = {D, B, A}.

---

**A25. → (C) They share the same parent node**
Siblings = nodes with the SAME parent.
Being at same level alone is NOT sufficient (cousins are same level but not siblings).
Example: B and C are siblings if both have A as their parent.

---

## 📚 GS ANSWERS — PHYSICS

---

**A26. → (B) Decreases**
Bernoulli's Principle: P + ½ρv² = constant.
If velocity (v) increases → ½ρv² increases → P must decrease to keep sum constant.
"High velocity → Low pressure" is the key takeaway.

---

**A27. → (C) Pascal's Law**
Hydraulic Jack/Lift: small force on small piston → pressure transmitted equally in all directions (Pascal's Law) → large force on large piston.
F₁/A₁ = F₂/A₂ → F₂ = F₁ × (A₂/A₁).

---

**A28. → (B) Weight of the fluid displaced by the object**
Archimedes' Principle: Buoyant Force = Weight of fluid displaced.
NOT the weight of the object itself (unless the object is floating in equilibrium).

---

**A29. → (B) Ship is hollow and displaces water equal to its own weight; nail does not**
Both are iron (same density) but ship is HOLLOW → large volume → displaces more water → buoyant force = ship's weight → floats.
Nail = solid, small volume → buoyant force < nail's weight → sinks.

---

**A30. → (C) Bernoulli's Principle**
Wing is curved on top (air moves faster = lower pressure) and flat on bottom (air moves slower = higher pressure). Net upward pressure difference = LIFT. This is Bernoulli's Principle at work.

---

**A31. → (D) More than one of the above**
Both Atomizer AND Venturi meter use Bernoulli's Principle:
- Atomizer: fast air jet → low pressure → sucks up liquid ✓
- Venturi meter: narrow section → fast flow → low pressure → measures flow rate ✓
- Hydraulic brake uses PASCAL'S LAW (not Bernoulli's)
So A and B are correct → (D)

---

**A32. → (B) Law of Inertia**
Newton's 1st Law = "Law of Inertia" — body at rest stays at rest; body in motion stays in motion unless external force acts.
2nd Law = "Law of Force" (F=ma).
3rd Law = "Action-Reaction."

---

**A33. → (C) Third Law**
Gun recoil: bullet goes forward (action) → gun kicks backward (reaction). Equal and opposite. This is Newton's Third Law. Rocket propulsion works on the same principle.

---

**A34. → (C) Steel/Solid**
Speed of sound: SOLID > LIQUID > GAS.
In steel: ~5000 m/s; in water: ~1500 m/s; in air: ~343 m/s.
Sound travels fastest in solids because molecules are closely packed.

---

**A35. → (C) Greater than 20,000 Hz**
Human hearing range: 20 Hz to 20,000 Hz.
Infrasound: < 20 Hz (elephants, earthquakes).
Ultrasound: > 20,000 Hz (bats, SONAR, medical imaging).

---

**A36. → (B) Reflection of ultrasound**
SONAR = Sound Navigation And Ranging.
Sends out ultrasound pulses → pulses reflect off underwater objects → measures return time → calculates distance.
Used in submarines, fish detection, ocean depth measurement.

---

**A37. → (C) Violet**
VIBGYOR — in dispersion, violet has shortest wavelength → bends/refracts the most.
Red has longest wavelength → bends the least.
In a rainbow: Red on OUTSIDE (top), Violet on INSIDE (bottom).

---

**A38. → (B) Total Internal Reflection of light**
Optical fibre: light enters at one end, keeps getting totally internally reflected off the glass-air interface → travels along even around curves without loss.
Used in internet cables (broadband), medical endoscopy.

---

**A39. → (B) Sphygmomanometer**
Sphygmomanometer = blood pressure meter (the cuff doctors use on your arm).
Barometer = atmospheric pressure.
Hydrometer = density of liquids.

---

**A40. → (B) Second Law**
F = ma is Newton's Second Law.
Force = mass × acceleration.
Also expressed as F = dp/dt (rate of change of momentum).

---

**A41. → (D) More than one of the above**
ALL THREE are correct formulas for electrical power:
- P = VI (power = voltage × current) ✓
- P = I²R (substitute V = IR) ✓
- P = V²/R (substitute I = V/R) ✓
All are equivalent — different forms for different given quantities.

---

**A42. → (A) Pataliputra (modern-day Bihar)**
Aryabhata (476 AD) was born in Pataliputra (modern Patna, Bihar). He calculated π, stated Earth rotates on its axis, and correctly explained eclipses. This is a high-frequency BPSC Bihar-specific question.

---

**A43. → (B) Change in apparent frequency of sound due to relative motion between source and observer**
Doppler Effect: When source and observer move relative to each other, the observed frequency differs from actual frequency.
Approaching: higher pitch. Receding: lower pitch.
Example: Ambulance siren changes pitch as it passes you.

---

**A44. → (B) Heat naturally flows from HOT to COLD, not the reverse**
Second Law of Thermodynamics: Spontaneous heat transfer is always from hot to cold.
Option A = First Law (energy conservation).
Option C = Third Law (entropy at absolute zero).

---

**A45. → (C) Pascal**
SI unit of pressure = Pascal (Pa) = N/m² (Newtons per square meter).
Named after Blaise Pascal who gave Pascal's Law.
1 atm ≈ 10⁵ Pa.

---

**A46. → (B) 373 K**
Formula: K = °C + 273
100°C + 273 = 373 K
0°C = 273 K (freezing point of water)
100°C = 373 K (boiling point of water)

---

**A47. → (B) Come together (attract each other)**
Bernoulli's Principle: Blowing air between the sheets increases air velocity in the gap → decreases pressure between the sheets.
Atmospheric pressure on the outer sides is higher → pushes sheets INWARD.
Counterintuitive but correct! Always confuses students — good PYQ.

---

**A48. → (D) More than one of the above**
ALL THREE use Archimedes' Principle:
- Ships/submarines: buoyancy design ✓
- Lactometer: measures milk density by how much it sinks (buoyancy) ✓
- Hydrometer: measures liquid density by floating depth ✓
→ Answer = (D)

---

**A49. → (C) Anemometer**
Anemometer = measures wind speed.
Hygrometer = measures humidity.
Barometer = measures atmospheric pressure.

---

**A50. → (C) Less than the smallest individual resistance**
Parallel resistors: 1/R_total = 1/R₁ + 1/R₂ + ...
Adding more parallel paths gives MORE routes for current → LESS total resistance.
Total resistance is ALWAYS less than the smallest individual resistor.
Example: Two 10Ω resistors in parallel → R_total = 5Ω (less than 10Ω).

---

# ═══════════════════════════════════════════════
# 📊 DAY 24 REVISION SUMMARY
## Quick-Recall Flash Points
# ═══════════════════════════════════════════════

---

## 🖥️ CS FLASH CARDS — 12 MUST-REMEMBER FACTS

```
1. N nodes → N-1 edges (ANY tree, always!)
2. Binary tree: max 2 children per node
3. Full BT: every node has 0 or 2 children (NEVER 1)
4. Complete BT: last level filled LEFT TO RIGHT
5. Perfect BT: ALL levels full; nodes = 2^h - 1
6. Balanced BT: height diff between subtrees ≤ 1
7. Preorder = Root FIRST (DLR): 1,2,4,5,3,6,7
8. Inorder = Root MIDDLE (LDR): 4,2,5,1,6,3,7
9. Postorder = Root LAST (LRD): 4,5,2,6,7,3,1
10. Level-order uses QUEUE (BFS)
11. Inorder of BST → SORTED (ascending)
12. "Randomized traversal" = DOES NOT EXIST (PYQ trap!)
```

---

## 📚 GS FLASH CARDS — 12 MUST-REMEMBER FACTS

```
1. Bernoulli: HIGH velocity → LOW pressure
2. Pascal's Law: Hydraulic machines (brakes, jacks, lifts)
3. Archimedes: Buoyant force = weight of DISPLACED fluid
4. Ship floats: hollow shape displaces more water
5. Aeroplane lift: Bernoulli's Principle (curved top wing)
6. Sound speed: Solid > Liquid > Gas
7. Ultrasound > 20,000 Hz; Infrasound < 20 Hz
8. SONAR = ultrasound reflection (submarines)
9. Total Internal Reflection → Optical Fibre
10. Sphygmomanometer = blood pressure instrument
11. Aryabhata born in Pataliputra (Bihar) — calculated π
12. K = °C + 273 (temperature conversion)
```

---

## ⚡ OPTION D TRAPS — WATCH FOR THESE

```
TOPIC                               │ Why D applies
────────────────────────────────────┼─────────────────────────────────
Applications of Bernoulli           │ Multiple (atomizer + venturi meter)
Applications of Archimedes          │ Multiple (ships + lactometer + hydrometer)
Power formulas P = ?                │ All 3 are correct (P=VI, P=I²R, P=V²/R)
What is true about DLL/trees        │ Often multiple true statements
Traversals that exist               │ 4 valid ones; "randomized" = C (single wrong)
```

---

## 🎯 TONIGHT'S 30-MINUTE REVISION TASK

Write from memory (close this file):
1. Draw the tree from Section 2 and label: root, leaf, depth, height, degree, siblings
2. Write Preorder, Inorder, Postorder for a small 7-node perfect tree
3. State Bernoulli's Principle in one line
4. Name 4 applications of Bernoulli's Principle
5. State Pascal's Law and name 2 applications
6. Write the temperature conversion: 37°C = __ K

---

*Day 24 Complete | Next: Day 25 — Binary Search Tree (BST) + Physics (Electricity P=I²R)*
*Score Target Today: 22/25 CS + 22/25 GS = 44/50 minimum*
*Running Total Target: Days 22+23+24 combined = 132/150*
