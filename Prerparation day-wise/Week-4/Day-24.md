# 📅 BPSC TRE 4.0 — DAY 24 COMPLETE STUDY MODULE
### Trees & Binary Trees + Physics — Bernoulli's Principle
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Trees & Binary Trees — Terminology, Types, Traversals, BFS vs DFS
> - Afternoon (1 hr): Physics — Bernoulli's Principle (concept, formula, applications)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Trees & Binary Trees — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Tree?

### Real-Life Analogy — The Family Tree:
```
Imagine your FAMILY TREE:
                    [Great-grandparent]          ← ROOT (top ancestor)
                           |
               ┌───────────┴───────────┐
          [Grandfather]           [Grandmother]  ← Children of root
               |
        ┌──────┴──────┐
      [Dad]         [Uncle]                      ← Siblings (same parent)
        |
    ┌───┴───┐
 [You]   [Sibling]                               ← LEAVES (no children)
```

This is EXACTLY how a Tree data structure works:
- One ancestor at the top (ROOT)
- Every person has exactly ONE parent (except root)
- A person can have multiple children
- People with no children = LEAVES
- Connections between people = EDGES

### Formal Definition:
A **Tree** is a **non-linear hierarchical data structure** consisting of nodes connected by edges, where:
1. There is exactly **ONE root node** (top of tree)
2. Every non-root node has exactly **ONE parent**
3. There are **NO cycles** (no loops — you can't travel in circles)
4. There is exactly **ONE path** between any two nodes

```
VALID TREE:              NOT A TREE (has a cycle):
      A                         A
     / \                       / \
    B   C                     B   C
   / \                         \ /
  D   E                         D    ← D has TWO parents! (cycle)
```

### Tree vs Linked List vs Array:
```
Array:       [10][20][30][40][50]   → Linear, contiguous
Linked List: 10→20→30→40→NULL      → Linear, non-contiguous
Tree:              10               → Hierarchical, branching
                  /  \
                20    30
               / \      \
              40  50     60         → Multiple children possible
```

---

## 🔷 SECTION 2: Tree Terminology — The Vocabulary of Exams

### Complete Terminology Diagram:
```
                         A          ← ROOT (level 0, depth 0)
                        / \
                       B   C        ← Level 1
                      / \   \
                     D   E   F      ← Level 2
                    / \
                   G   H            ← Level 3 (LEAF nodes: G, H, E, F)
```

### Term-by-Term Explanation:

**ROOT:**
```
The topmost node of the tree.
Has NO parent.
In the diagram above: A is the root.
A tree has EXACTLY ONE root.
```

**NODE:**
```
Each element/data point in the tree.
Above: A, B, C, D, E, F, G, H are all nodes.
Total nodes = 8.
```

**EDGE:**
```
The connection/link between a parent and child node.
Above: A-B, A-C, B-D, B-E, C-F, D-G, D-H are all edges.
Total edges = 7 = (Total nodes - 1) = 8 - 1 = 7

🚨 KEY FORMULA: In a tree with n nodes → edges = n - 1 (ALWAYS)
```

**PARENT and CHILD:**
```
If A is connected to B (and A is above B):
  A = PARENT of B
  B = CHILD of A

In diagram:
  A is parent of B and C
  B is parent of D and E
  D is parent of G and H
```

**SIBLING:**
```
Nodes that share the SAME parent.
In diagram:
  B and C are siblings (parent = A)
  D and E are siblings (parent = B)
  G and H are siblings (parent = D)
```

**LEAF NODE (External Node):**
```
A node with NO children (degree = 0).
In diagram: G, H, E, F are leaf nodes.
Also called "external nodes" or "terminal nodes".
```

**INTERNAL NODE:**
```
A node with AT LEAST ONE child.
In diagram: A, B, C, D are internal nodes.
```

**DEGREE OF A NODE:**
```
Number of children a node has.

Node A: children = B, C → degree = 2
Node B: children = D, E → degree = 2
Node C: children = F    → degree = 1
Node D: children = G, H → degree = 2
Node E: no children     → degree = 0 (leaf)
Node F: no children     → degree = 0 (leaf)

DEGREE OF TREE = maximum degree among all nodes
In this tree, max degree = 2 → Degree of tree = 2
```

**HEIGHT OF A NODE:**
```
Number of edges on the LONGEST path from that node to a LEAF.
(Measure going DOWN from the node)

Height of G = 0  (G is a leaf — no edges below)
Height of D = 1  (D → G: one edge)
Height of B = 2  (B → D → G: two edges)
Height of A = 3  (A → B → D → G: three edges)

HEIGHT OF TREE = Height of the ROOT = 3 (in above example)
```

**DEPTH OF A NODE:**
```
Number of edges on path from ROOT to that node.
(Measure going UP to root)

Depth of A = 0  (A is root)
Depth of B = 1  (root → B: one edge)
Depth of D = 2  (root → B → D: two edges)
Depth of G = 3  (root → B → D → G: three edges)

DEPTH OF TREE = Depth of deepest node = 3 (in above example)
```

### 🚨 PYQ TRAP #1: Height vs Depth
```
Height: measured from node DOWN to deepest leaf
Depth:  measured from ROOT UP to the node

Height of tree = Depth of tree (both equal maximum level)
But height/depth of INDIVIDUAL NODES are different!

Height of root = Height of tree
Depth of deepest leaf = Height of tree

Some textbooks define Height as number of NODES (not edges):
  Height of single node = 1 (node-based counting)
  Height of single node = 0 (edge-based counting)
  ← Exams usually use EDGE-based counting, but watch for context!
```

**LEVEL:**
```
Level of root = 0 (or 1 — both conventions used in exams!)
Level increases by 1 as you go down.

Level 0: A
Level 1: B, C
Level 2: D, E, F
Level 3: G, H

🚨 PYQ TRAP: Some books count root as Level 1 (not Level 0).
If exam says "root is at Level 1", then:
  Number of nodes at Level k = 2^(k-1) for perfect binary tree
If exam says "root is at Level 0", then:
  Number of nodes at Level k = 2^k
```

**PATH:**
```
Sequence of nodes connected by edges.
Path from A to H: A → B → D → H
Length of this path = 3 edges (or 4 nodes)
```

**SUBTREE:**
```
Any node and all its descendants form a SUBTREE.
In diagram:
  Subtree rooted at B: {B, D, E, G, H}
  Subtree rooted at D: {D, G, H}
  Every leaf node is itself a subtree (of size 1).
```

### 🚨 PYQ TRAP #2: Important Formulas
```
1. Edges in tree with n nodes = n - 1
2. Maximum nodes at level k (0-indexed) = 2^k
3. Maximum nodes in binary tree of height h = 2^(h+1) - 1
4. In a full binary tree with n internal nodes: leaves = n + 1
5. Maximum number of leaves in binary tree of height h = 2^h
```

---

## 🔷 SECTION 3: Binary Tree — Definition and Concept

### What is a Binary Tree?
A **Binary Tree** is a tree where **each node has AT MOST 2 children**, called:
- **Left child** (goes to the left)
- **Right child** (goes to the right)

```
BINARY TREE (max 2 children per node):

         10
        /  \
       20   30
      / \     \
     40  50   60

Node 10: has left child 20 and right child 30
Node 30: has only right child 60 (no left child — that's OK in binary tree!)
Nodes 40, 50, 60: are leaves

"AT MOST 2 children" means 0, 1, or 2 children are all valid.
```

### Binary Tree Node Structure:
```cpp
struct Node {
    int data;
    Node* left;    // pointer to left child (NULL if no left child)
    Node* right;   // pointer to right child (NULL if no right child)
};
```

```
Visual node:
         ┌──────┬──────┬──────┐
         │ LEFT │ DATA │RIGHT │
         │ ptr  │      │ ptr  │
         └──────┴──────┴──────┘
```

---

## 🔷 SECTION 4: Types of Binary Trees — The Most Tested Topic

### Type 1: FULL BINARY TREE (Strictly Binary Tree)

**Definition:** Every node has either **0 or 2 children** — NEVER exactly 1 child.

```
FULL Binary Tree:
         1
        / \
       2   3
      / \
     4   5

Node 1: 2 children ✓
Node 2: 2 children ✓
Node 3: 0 children (leaf) ✓
Node 4: 0 children (leaf) ✓
Node 5: 0 children (leaf) ✓
→ FULL Binary Tree ✓

NOT a Full Binary Tree:
         1
        / \
       2   3
      /
     4
Node 2 has ONLY 1 child (just left, no right) → NOT FULL ✗
```

**Key Property of Full Binary Tree:**
```
If a full binary tree has:
  L = number of leaf nodes (external)
  I = number of internal nodes

Then: L = I + 1   ← EXAM FORMULA!

Example above: L = 3 (nodes 3, 4, 5), I = 2 (nodes 1, 2)
Verify: 3 = 2 + 1 ✓
```

### 🚨 PYQ TRAP #3: Full vs Complete
> "Full" = every node has 0 or 2 children (about CHILDREN COUNT)
> "Complete" = all levels filled except last, last level filled LEFT to RIGHT
> These are DIFFERENT properties. A tree can be full but not complete, or complete but not full!

---

### Type 2: COMPLETE BINARY TREE

**Definition:** All levels are **completely filled** EXCEPT possibly the last level, which is filled **from LEFT to RIGHT** (no gaps allowed on the left).

```
COMPLETE Binary Tree:
         1
        / \
       2   3
      / \ /
     4  5 6

All of level 0 filled: {1} ✓
All of level 1 filled: {2, 3} ✓
Level 2: {4, 5, 6} — filled left to right ✓ (even if not full)
→ COMPLETE Binary Tree ✓

NOT Complete (gap on left before right):
         1
        / \
       2   3
        \
         5
Node 2 has a right child but NO LEFT child → gap on left → NOT COMPLETE ✗

NOT Complete:
         1
        / \
       2   3
      /     \
     4       6
Node 3 has only RIGHT child before left child → fills from right → NOT COMPLETE ✗
```

**Why Complete Binary Trees Matter:**
```
HEAP data structure = Complete Binary Tree!
Array representation of binary tree = efficient only for Complete BT!
Because complete BT has no gaps, it can be stored in an array:
  Node at index i → left child at 2i+1, right child at 2i+2
  Node at index i → parent at (i-1)/2
```

---

### Type 3: PERFECT BINARY TREE

**Definition:** ALL internal nodes have **exactly 2 children** AND **all leaf nodes are at the SAME level**.

```
PERFECT Binary Tree (height = 2):
         1
        / \
       2   3
      / \ / \
     4  5 6  7

Level 0: 1 node (2^0 = 1) ✓
Level 1: 2 nodes (2^1 = 2) ✓
Level 2: 4 nodes (2^2 = 4) ✓ — ALL leaves at same level ✓
→ PERFECT Binary Tree ✓
```

**Key Properties of Perfect Binary Tree:**
```
Height h → Total nodes = 2^(h+1) - 1

Height 0: 1 node         (2^1 - 1 = 1)
Height 1: 3 nodes        (2^2 - 1 = 3)
Height 2: 7 nodes        (2^3 - 1 = 7)
Height 3: 15 nodes       (2^4 - 1 = 15)

Number of leaf nodes = 2^h
Number of internal nodes = 2^h - 1
Total nodes = 2 × (internal nodes) + 1

A perfect binary tree is BOTH full AND complete.
```

---

### Type 4: BALANCED BINARY TREE

**Definition:** For EVERY node, the height difference between its left subtree and right subtree is **at most 1**.

```
BALANCED Binary Tree:
         1
        / \
       2   3
      /
     4
Height of left subtree of 1 = 2 (1→2→4)
Height of right subtree of 1 = 1 (1→3)
Difference = |2 - 1| = 1 → BALANCED ✓

Height of left subtree of 2 = 1 (2→4)
Height of right subtree of 2 = 0 (no right child)
Difference = |1 - 0| = 1 → BALANCED ✓

NOT Balanced:
         1
        /
       2
      /
     3
Height difference at node 1: left=2, right=0 → |2-0| = 2 > 1 → UNBALANCED ✗
```

**Why Balanced Trees Matter:**
```
Balanced BST → search, insert, delete = O(log n)
Unbalanced BST (skewed) → worst case = O(n) (degenerates to linked list!)

AVL Tree = Self-balancing BST (maintains balance after every insert/delete)
Red-Black Tree = Another self-balancing BST (used in Java's TreeMap)
```

---

### Type 5: SKEWED BINARY TREE

```
LEFT-SKEWED:          RIGHT-SKEWED:
    1                     1
   /                       \
  2                         2
 /                           \
3                             3
All nodes have only          All nodes have only
LEFT children                RIGHT children

Worst case for BST operations → O(n) instead of O(log n)
Essentially degenerates into a Linked List!
```

---

### Binary Tree Types — Comparison Table:

| Type | Condition | Shape | Special Property |
|------|-----------|-------|-----------------|
| **Full** | Every node has 0 or 2 children | Irregular | Leaves = Internal + 1 |
| **Complete** | All levels filled left-to-right | Compact | Array storage efficient; Heap |
| **Perfect** | All leaves at same level, all internal nodes have 2 children | Symmetric triangle | 2^(h+1)-1 nodes |
| **Balanced** | Height diff ≤ 1 for every node | Roughly equal | O(log n) operations |
| **Skewed** | All nodes have only 1 child | Like a list | O(n) degenerate |

---

## 🔷 SECTION 5: Tree Traversals — The Heart of the Exam

### What is Traversal?
Visiting EVERY node in the tree EXACTLY ONCE in a specific order.

### THE MASTER TREE FOR ALL TRAVERSALS:
```
            A
           / \
          B   C
         / \   \
        D   E   F
```

We will find all four traversal orders on this same tree.

---

### TRAVERSAL 1: PREORDER — Root → Left → Right

**"PRE" = ROOT COMES FIRST (before left and right)**

**Algorithm (Recursive):**
```
Preorder(node):
  1. Visit ROOT (print it)
  2. Recursively traverse LEFT subtree (Preorder)
  3. Recursively traverse RIGHT subtree (Preorder)
```

**Step-by-Step on our tree:**
```
            A               ← Step 1: Visit A → print A
           / \
          B   C
         / \   \
        D   E   F

Preorder(A):
  print A
  → Go LEFT: Preorder(B)
      print B
      → Go LEFT: Preorder(D)
          print D
          → Go LEFT: Preorder(NULL) → return
          → Go RIGHT: Preorder(NULL) → return
          ← back to B
      → Go RIGHT: Preorder(E)
          print E
          → Go LEFT: NULL → return
          → Go RIGHT: NULL → return
          ← back to B
      ← back to A
  → Go RIGHT: Preorder(C)
      print C
      → Go LEFT: Preorder(NULL) → return
      → Go RIGHT: Preorder(F)
          print F
          → Go LEFT: NULL → return
          → Go RIGHT: NULL → return

PREORDER RESULT: A → B → D → E → C → F
```

**Visual Preorder Path:**
```
            A(1)
           / \
        B(2)  C(5)
        / \     \
      D(3) E(4)  F(6)

Numbers show the ORDER of visiting.
Preorder: A, B, D, E, C, F
```

**Memory Trick: "ROOT first → American Reading (Left to Right but Root pops up first)"**

---

### TRAVERSAL 2: INORDER — Left → Root → Right

**"IN" = ROOT COMES IN THE MIDDLE (between left and right)**

**Algorithm (Recursive):**
```
Inorder(node):
  1. Recursively traverse LEFT subtree (Inorder)
  2. Visit ROOT (print it)
  3. Recursively traverse RIGHT subtree (Inorder)
```

**Step-by-Step on our tree:**
```
Inorder(A):
  → Go LEFT: Inorder(B)
      → Go LEFT: Inorder(D)
          → Go LEFT: NULL → return
          print D                 ← D is printed
          → Go RIGHT: NULL → return
      print B                     ← B is printed
      → Go RIGHT: Inorder(E)
          → Go LEFT: NULL → return
          print E                 ← E is printed
          → Go RIGHT: NULL → return
  print A                         ← A is printed
  → Go RIGHT: Inorder(C)
      → Go LEFT: NULL → return
      print C                     ← C is printed
      → Go RIGHT: Inorder(F)
          → Go LEFT: NULL → return
          print F                 ← F is printed

INORDER RESULT: D → B → E → A → C → F
```

**Visual Inorder Path:**
```
            A(4)
           / \
        B(2)  C(5)
        / \     \
      D(1) E(3)  F(6)

Inorder: D, B, E, A, C, F
```

### 🚨 PYQ TRAP #4 — INORDER OF BST = SORTED ORDER
> **If the tree is a Binary Search Tree (BST), Inorder traversal gives SORTED output (ascending order).**
> This is the single most important property of BST inorder traversal.
> Example: BST with values 5, 3, 7, 1, 4 → Inorder = 1, 3, 4, 5, 7 (sorted!)

---

### TRAVERSAL 3: POSTORDER — Left → Right → Root

**"POST" = ROOT COMES LAST (after left and right)**

**Algorithm (Recursive):**
```
Postorder(node):
  1. Recursively traverse LEFT subtree (Postorder)
  2. Recursively traverse RIGHT subtree (Postorder)
  3. Visit ROOT (print it) ← ROOT IS ALWAYS LAST
```

**Step-by-Step on our tree:**
```
Postorder(A):
  → Go LEFT: Postorder(B)
      → Go LEFT: Postorder(D)
          → NULL, → NULL
          print D
      → Go RIGHT: Postorder(E)
          → NULL, → NULL
          print E
      print B
  → Go RIGHT: Postorder(C)
      → Go LEFT: NULL
      → Go RIGHT: Postorder(F)
          → NULL, → NULL
          print F
      print C
  print A

POSTORDER RESULT: D → E → B → F → C → A
```

**Visual Postorder Path:**
```
            A(6)
           / \
        B(3)  C(5)
        / \     \
      D(1) E(2)  F(4)

Postorder: D, E, B, F, C, A
```

**Why Postorder is Used:**
```
DELETION of tree: Delete children BEFORE parent (postorder ensures this)
Expression trees: Evaluating mathematical expressions
Directory deletion: Delete files in folder BEFORE deleting folder itself
```

---

### TRAVERSAL 4: LEVEL-ORDER (BFS — Breadth-First Search)

**Visit nodes LEVEL BY LEVEL, from top to bottom, left to right.**

**Algorithm (uses a QUEUE):**
```
Level-Order(root):
  1. Enqueue root
  2. While queue is NOT empty:
      a. Dequeue front node → print it
      b. If it has left child → Enqueue left child
      c. If it has right child → Enqueue right child
```

**Step-by-Step on our tree:**
```
            A
           / \
          B   C
         / \   \
        D   E   F

Queue State:
Start:    [A]
Step 1:   Dequeue A → print A → Enqueue B, C    Queue: [B, C]
Step 2:   Dequeue B → print B → Enqueue D, E    Queue: [C, D, E]
Step 3:   Dequeue C → print C → Enqueue F       Queue: [D, E, F]
Step 4:   Dequeue D → print D → no children     Queue: [E, F]
Step 5:   Dequeue E → print E → no children     Queue: [F]
Step 6:   Dequeue F → print F → no children     Queue: []
Queue empty → STOP

LEVEL-ORDER RESULT: A → B → C → D → E → F
```

**Visual Level-Order:**
```
Level 0:    A(1)
Level 1:  B(2) C(3)
Level 2: D(4) E(5) F(6)

Order: A, B, C, D, E, F
```

---

### ALL FOUR TRAVERSALS ON SAME TREE — SUMMARY:
```
Tree:
            A
           / \
          B   C
         / \   \
        D   E   F

PREORDER  (Root→L→R): A, B, D, E, C, F
INORDER   (L→Root→R): D, B, E, A, C, F
POSTORDER (L→R→Root): D, E, B, F, C, A
LEVEL-ORDER (BFS):    A, B, C, D, E, F
```

---

### Master Traversal Comparison Table:

| Traversal | Order | Data Structure Used | Key Use Case |
|-----------|-------|--------------------|-|
| **Preorder** | Root → Left → Right | Stack (implicit recursion) | Copy tree; Prefix expressions |
| **Inorder** | Left → Root → Right | Stack (implicit recursion) | Sorted output from BST |
| **Postorder** | Left → Right → Root | Stack (implicit recursion) | Delete tree; Postfix expressions |
| **Level-order** | Level by level | **QUEUE** | Shortest path; BFS applications |

### 🚨 PYQ TRAP #5: BFS uses Queue, DFS uses Stack
```
Level-Order = BFS (Breadth-First Search) → uses QUEUE
Preorder, Inorder, Postorder = DFS (Depth-First Search) → use STACK (via recursion)

If asked: "Which traversal uses a Queue?"
Answer: Level-Order (BFS)

If asked: "Which traversal visits nodes level by level?"
Answer: Level-Order (BFS)
```

---

## 🔷 SECTION 6: BFS vs DFS — Key Differences

### BFS — Breadth-First Search:
```
Strategy: Explore ALL neighbors at current depth before going deeper
          (Like exploring all rooms on floor 1 before floor 2)
Data Structure: QUEUE (FIFO — First In First Out)
Traversal type: Level-Order

Visual path on tree:
    1 → 2 → 3 → 4 → 5 → 6 → 7
    (level by level, left to right)
```

### DFS — Depth-First Search:
```
Strategy: Go as DEEP as possible on one path before backtracking
          (Like going all the way down one corridor before trying another)
Data Structure: STACK (explicit or via recursion call stack)
Traversal types: Preorder, Inorder, Postorder

Visual path on tree (Preorder DFS):
    1 → 2 → 4 → 5 → 3 → 6 → 7
    (go deep into left subtree first)
```

### BFS vs DFS Comparison:

| Feature | BFS | DFS |
|---------|-----|-----|
| Data Structure | Queue | Stack (or recursion) |
| Order | Level by level | Branch by branch |
| Memory | More (stores all level nodes) | Less (only current path) |
| Finds shortest path? | YES (in unweighted graphs) | NO (not guaranteed) |
| Complete? | Yes (always finds solution if exists) | Yes (in finite trees) |
| Optimal? | Yes (for unweighted shortest path) | No |
| Tree Traversal | Level-Order | Pre/In/Postorder |
| Use case | Shortest path, web crawling, social networks | Maze solving, topological sort, tree operations |

---

## 🔷 SECTION 7: Recursive Nature of Trees

### Every Tree is Made of Subtrees:
```
A tree is RECURSIVE by nature — every subtree is itself a tree!

            A               ← Full tree rooted at A
           / \
          B   C             ← Subtree rooted at B + Subtree rooted at C
         / \   \
        D   E   F

Subtree rooted at B:        Subtree rooted at D:
      B                           D
     / \                         (leaf — just D itself)
    D   E

This recursive structure is WHY tree algorithms are naturally recursive.
```

### Why Recursion Works Perfectly for Trees:
```
Base case: If node == NULL → return
Recursive case: Process left subtree, process right subtree

Inorder(node):              ← same algorithm works for ANY subtree!
  if node == NULL: return
  Inorder(node.left)
  print(node.data)
  Inorder(node.right)
```

---

## 🔷 SECTION 8: Common PYQ Scenarios — Worked Examples

### PYQ Scenario 1: Given traversals, find the tree

**Given:** Preorder = A, B, D, E, C, F | Inorder = D, B, E, A, C, F
**Find:** The binary tree.

```
Method:
Step 1: First element of Preorder = ROOT = A
Step 2: Find A in Inorder: D, B, E | A | C, F
        LEFT of A in Inorder = {D, B, E} → left subtree
        RIGHT of A in Inorder = {C, F} → right subtree
Step 3: Preorder of left subtree = B, D, E (next 3 in preorder)
        Root of left = B (first of B,D,E in preorder)
Step 4: Find B in {D, B, E}: D | B | E
        LEFT of B = {D}, RIGHT of B = {E}
Step 5: Preorder of right subtree = C, F
        Root of right = C, its right = F

Result:
         A
        / \
       B   C
      / \   \
     D   E   F   ✓ (matches our original tree!)
```

### PYQ Scenario 2: Count nodes at each level
```
For a Perfect Binary Tree of height h:
  Level 0: 1 node  (= 2^0)
  Level 1: 2 nodes (= 2^1)
  Level 2: 4 nodes (= 2^2)
  Level k: 2^k nodes

Total nodes = 2^0 + 2^1 + ... + 2^h = 2^(h+1) - 1
```

### 🚨 PYQ TRAP #6: "Randomized Traversal" Does NOT Exist
> The four standard traversals are: Preorder, Inorder, Postorder, Level-Order.
> There is NO such thing as "Randomized Traversal" of a binary tree.
> If this appears as an option in MCQ, it is a TRAP — select the correct traversal instead.

---

## 🔷 SECTION 9: Complete Mind Map — Trees

```
                         TREE
                           |
          ┌────────────────┼────────────────┐
          |                |                |
     TERMINOLOGY      BINARY TREE      TRAVERSALS
          |                |                |
   Root, Node, Edge   Types:          4 Types:
   Parent, Child      Full            Preorder (R-L-R)
   Sibling, Leaf      Complete        Inorder (L-R-R)
   Degree, Height     Perfect         Postorder (L-R-R)
   Depth, Level       Balanced        Level-Order (BFS)
                      Skewed               |
   KEY FORMULA:            |         Uses STACK: Pre/In/Post
   edges = nodes - 1  KEY PROPS:    Uses QUEUE: Level-Order
                      Full: L=I+1        |
                      Perfect:      BST Inorder = Sorted
                      2^(h+1)-1     BFS = Level-Order
```

---

# PART 2: GENERAL STUDIES
## ⚗️ Physics — Bernoulli's Principle

---

## 🔷 SECTION 1: What is Bernoulli's Principle?

### The Core Idea — Speed and Pressure Trade-Off:
**"When the speed of a fluid INCREASES, its pressure DECREASES; and when speed DECREASES, pressure INCREASES."**

Think of it as a **conservation law for flowing fluids** — if a fluid speeds up, it "pays" for that speed by reducing its pressure.

### Real-Life Intuition — The Garden Hose:
```
Imagine a garden hose flowing with water.
You press your thumb over the opening (making it narrower):
  → Water SPEEDS UP (shoots further)
  → Pressure at the thumb region DECREASES (you don't feel high pressure)

This is Bernoulli's Principle!
WHERE SPEED IS HIGH → PRESSURE IS LOW
WHERE SPEED IS LOW  → PRESSURE IS HIGH
```

### Who Discovered It?
```
Daniel Bernoulli (1700–1782)
Swiss mathematician and physicist
Published in "Hydrodynamica" (1738)
Based on: Conservation of Energy applied to fluid flow
```

---

## 🔷 SECTION 2: Bernoulli's Equation — Basic Understanding

### The Formula:
```
P + ½ρv² + ρgh = constant

Where:
P   = pressure at a point (in Pascals)
ρ   = density of fluid (kg/m³) — rho
v   = velocity of fluid at that point (m/s)
g   = acceleration due to gravity (9.8 m/s²)
h   = height of the point above reference level (meters)
½ρv² = kinetic energy per unit volume
ρgh  = potential energy per unit volume

The equation means: AT ANY POINT in the fluid:
Pressure energy + Kinetic energy + Potential energy = CONSTANT

So if v increases (fluid speeds up) → P must DECREASE (pressure drops)
And if v decreases (fluid slows down) → P must INCREASE (pressure rises)
```

### Simplified Version (for same height — horizontal flow):
```
P₁ + ½ρv₁² = P₂ + ½ρv₂²

If v₂ > v₁ (fluid speeds up at point 2)
Then P₂ < P₁ (pressure must be lower at point 2)

THIS IS THE EXAM CORE — speed up = pressure down!
```

### Conditions for Bernoulli's Principle:
```
1. IDEAL FLUID: non-viscous (no friction between fluid layers)
2. INCOMPRESSIBLE: density doesn't change (liquids, not gases ideally)
3. STEADY FLOW: velocity at each point doesn't change with time (laminar flow)
4. STREAMLINE FLOW: fluid flows in smooth, parallel paths (no turbulence)
```

### 🚨 PYQ TRAP #1: Bernoulli's Condition
> Bernoulli's Principle applies to **ideal, incompressible, non-viscous fluids** in **steady, streamlined flow**.
> Real fluids (water, air) are approximations. The principle gives approximate results for real fluids.

---

## 🔷 SECTION 3: Continuity Equation (Partners with Bernoulli)

### The Continuity Equation:
```
A₁v₁ = A₂v₂

Where:
A = cross-sectional area of the pipe/channel
v = velocity of fluid

This means: What goes IN must come OUT (conservation of mass)

If pipe NARROWS (A₂ < A₁):
  Then v₂ > v₁ (fluid speeds up in narrow section)
  And by Bernoulli: P₂ < P₁ (pressure decreases in narrow section)
```

**Visual — The Venturi Effect:**
```
Wide pipe:             Narrow pipe:           Wide again:
   v = slow                v = FAST               v = slow
   P = HIGH                P = LOW                P = HIGH
   ────────────     ═══════════════════     ────────────
   →→→→→→→→→→→     → → → → → → → → →      →→→→→→→→→→→
   ────────────     ═══════════════════     ────────────
   Area = A₁              Area = A₂               Area = A₁
   (large)                (small)                  (large)
   A₁v₁ = A₂v₂ → v₂ = (A₁/A₂)v₁ → v₂ >> v₁ when A₂ << A₁
```

---

## 🔷 SECTION 4: Real-Life Applications of Bernoulli's Principle

### Application 1: AIRPLANE WING (LIFT) — Most Important!
```
Cross-section of airplane wing (AEROFOIL):

         _______curved top_______
        /                        \     ← AIR SPEEDS UP (longer path)
       /  - - - - - - - - - - -  \    ← LOW PRESSURE above wing
      |                            |
       \  ________________________/   ← AIR SLOWS DOWN (shorter path)
                flat bottom            ← HIGH PRESSURE below wing

How it works:
  → Wing is curved on TOP and flat on BOTTOM
  → Air travelling over the TOP takes a LONGER path → must go FASTER
  → Air below takes a SHORTER path → goes SLOWER
  → By Bernoulli: faster air = LOWER pressure (above wing)
  → Slower air = HIGHER pressure (below wing)
  → Pressure difference: HIGH below, LOW above = NET UPWARD FORCE
  → This upward force = LIFT (keeps the plane in the air!)

KEY CONCEPT: LIFT = Pressure below > Pressure above (due to Bernoulli)
```

### 🚨 PYQ TRAP #2: Airplane Wing
> The airplane wing is **curved on top** (not bottom). This is the AEROFOIL shape.
> Curved top → longer path for air → higher speed → LOWER PRESSURE above
> Flat bottom → shorter path → lower speed → HIGHER PRESSURE below
> Net effect = LIFT force pushing wing UP

---

### Application 2: VENTURI METER (Measuring Flow Speed)
```
A device that uses narrowing in a pipe to measure fluid velocity.

Wide        Narrow        Wide
section     section      section
|           |  |          |
|   →→→     |→→|  →→→     |
|           |  |          |
P₁ high     P₂ low      P₁ high

By measuring the pressure DIFFERENCE (P₁ - P₂),
we can calculate the flow velocity.
Used in: industrial pipelines, carburettors, water treatment.
```

### Application 3: ATOMIZER / PERFUME SPRAY
```
Squeeze the bulb → air rushes FAST over the tube opening
Fast air above tube opening = LOW PRESSURE above
Normal atmospheric pressure at the liquid surface = HIGH PRESSURE
Pressure difference pushes liquid UP the tube → liquid gets sprayed!

Same principle: Insecticide spray pumps, perfume atomizers, paint spray guns
```

### Application 4: BUNSEN BURNER
```
When gas flows rapidly through the narrow jet of a Bunsen burner:
→ Gas moves FAST → LOW PRESSURE at jet region
→ Atmospheric pressure (HIGH) pushes AIR into the burner through side vents
→ Gas + Air mixture = efficient combustion (better burning!)
```

### Application 5: CARBURETOR (Internal Combustion Engine)
```
Petrol engines:
→ Air flows through narrow section (venturi) of carburetor
→ High speed air = LOW PRESSURE in narrow section
→ Low pressure sucks petrol from fuel chamber into airstream
→ Petrol-air mixture sent to engine cylinders
Modern fuel-injection engines replaced carburetors, but the principle was fundamental.
```

### Application 6: CURVE BALL IN CRICKET/FOOTBALL
```
Spinning ball in sports (Magnus Effect — related to Bernoulli):
→ Spinning ball drags air with it on one side
→ One side: spin direction + flow direction = VERY FAST air = LOW PRESSURE
→ Other side: spin direction AGAINST flow = SLOW air = HIGH PRESSURE
→ Pressure difference pushes ball toward the LOW PRESSURE side
→ Ball curves in flight!

Bowlers in cricket use "swing bowling" using this effect.
```

### Application 7: ROOF BLOWING OFF IN STORMS
```
Strong wind over roof → HIGH speed air = LOW PRESSURE above roof
Inside house: air is relatively still = NORMAL (HIGH) PRESSURE
Pressure inside > Pressure above roof
→ NET UPWARD FORCE on roof → roof can be blown off in storms!

This is WHY flat roofs are more vulnerable than sloped roofs in storms.
```

### Application 8: FILTER PUMP / WATER EJECTOR
```
Fast-moving water passes through a narrow nozzle:
→ High speed = Low pressure at nozzle
→ Atmospheric pressure pushes air/fluid from a connected vessel
→ Used to create partial vacuum in laboratories
```

---

## 🔷 SECTION 5: Bernoulli's vs Related Concepts

### Torricelli's Theorem (Special Case of Bernoulli):
```
When a container has a hole at the bottom:
The velocity of efflux (water coming out) = √(2gh)

Where h = height of water above the hole.

This is Bernoulli's equation applied to a tank with a hole.
At top surface: P = atmospheric, v ≈ 0
At hole: P = atmospheric, v = ?
→ ½ρv² = ρgh → v = √(2gh)
```

### Magnus Effect (Extension of Bernoulli):
```
When a ROTATING object moves through a fluid:
One side: rotation + flow = faster air = LOW PRESSURE
Other side: rotation against flow = slower air = HIGH PRESSURE
→ Object curves toward the LOW PRESSURE side

Applications:
→ Cricket/Football curve balls (swing, swerve)
→ Tennis topspin
→ Rotor ships (Flettner rotors)
```

### Coandă Effect:
```
A fluid jet attaches itself to a nearby curved surface and follows its curvature.
Related to Bernoulli — fast fluid near curved surface = low pressure.
Used in: Aircraft flaps, industrial processes.
```

---

## 🔷 SECTION 6: Bernoulli's Principle — Memory Tricks

### The Golden Rule:
```
FAST FLOW → LOW PRESSURE
SLOW FLOW → HIGH PRESSURE

Memory Trick: "FAST = FALLS (pressure falls when speed rises)"
or: "Speed Up = Squeeze (pressure squeezed out)"
```

### Applications Memory Trick — "AVBCR":
```
A = Airplane (lift — most important!)
V = Venturi meter (flow measurement)
B = Bunsen burner (air mixing)
C = Carburetor / Cricket (curve ball)
R = Roof blowing off (storms)
+ Perfume spray / Atomizer
```

### Formula Memory:
```
P + ½ρv² + ρgh = constant

Think: PRESSURE + KINETIC + POTENTIAL = CONSTANT
       (pressure energy + KE/volume + PE/volume = constant)
       
If KE goes UP → P must go DOWN (to keep the constant, constant!)
```

---

## 🔷 SECTION 7: Bernoulli's Concept Diagram

```
BERNOULLI'S PRINCIPLE — FLUID IN A PIPE:

HIGH PRESSURE                    LOW PRESSURE               HIGH PRESSURE
SLOW FLOW                        FAST FLOW                  SLOW FLOW
   │                                  │                          │
   ▼                                  ▼                          ▼
────────────────        ══════════════════════        ────────────────
→→ → → → → → →        →→→→→→→→→→→→→→→→→→→→         → → → → → → →→
────────────────        ══════════════════════        ────────────────
   ▲                         ▲                             ▲
WIDE pipe               NARROW pipe                    WIDE pipe
Area = A₁               Area = A₂ (< A₁)               Area = A₁
Speed = v₁ (slow)       Speed = v₂ (fast)              Speed = v₁ (slow)

Continuity: A₁v₁ = A₂v₂
Bernoulli: P₁ > P₂ (where v₁ < v₂)
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Tree Terminology, Binary Tree Types, Traversals, BFS vs DFS

---

**Q1.** What is the number of edges in a tree with n nodes?
(A) n
(B) n + 1
(C) n - 1
(D) More than one of the above
(E) None of the above

---

**Q2.** In a Binary Tree, each node can have at most how many children?
(A) 1
(B) 3
(C) 2
(D) More than one of the above
(E) None of the above

---

**Q3.** Which traversal of a Binary Search Tree gives nodes in SORTED (ascending) order?
(A) Preorder
(B) Postorder
(C) Inorder
(D) More than one of the above
(E) None of the above

---

**Q4.** Which data structure is used in Level-Order (BFS) traversal of a binary tree?
(A) Stack
(B) Priority Queue
(C) Queue
(D) More than one of the above
(E) None of the above

---

**Q5.** A node with NO children is called:
(A) Root node
(B) Internal node
(C) Leaf node
(D) More than one of the above
(E) None of the above

---

**Q6.** In Preorder traversal, the ROOT is visited:
(A) After left subtree
(B) After right subtree
(C) Before left and right subtrees
(D) More than one of the above
(E) None of the above

---

**Q7.** A Full Binary Tree has how many leaf nodes if it has 6 internal nodes?
(A) 6
(B) 5
(C) 7
(D) More than one of the above
(E) None of the above

---

**Q8.** Consider the tree:
```
    1
   / \
  2   3
 / \
4   5
```
What is the Postorder traversal?
(A) 1, 2, 4, 5, 3
(B) 4, 2, 5, 1, 3
(C) 4, 5, 2, 3, 1
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the MAXIMUM number of nodes in a Perfect Binary Tree of height 3?
(A) 7
(B) 15
(C) 14
(D) More than one of the above
(E) None of the above

---

**Q10.** In a Complete Binary Tree, if a node is at index i (0-indexed in array), its LEFT child is at index:
(A) 2i
(B) 2i + 1
(C) 2i + 2
(D) More than one of the above
(E) None of the above

---

**Q11.** Which binary tree type is used internally by a HEAP data structure?
(A) Full Binary Tree
(B) Complete Binary Tree
(C) Perfect Binary Tree
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the Inorder traversal of the following tree?
```
      4
     / \
    2   6
   / \ / \
  1  3 5  7
```
(A) 4, 2, 1, 3, 6, 5, 7
(B) 1, 2, 3, 4, 5, 6, 7
(C) 1, 3, 2, 5, 7, 6, 4
(D) More than one of the above
(E) None of the above

---

**Q13.** BFS (Breadth-First Search) traversal of a tree visits nodes:
(A) Depth first — going deep into one branch before others
(B) Level by level — all nodes at same depth before going deeper
(C) In sorted order always
(D) More than one of the above
(E) None of the above

---

**Q14.** The depth of the root node in a tree is:
(A) 1
(B) Equal to the height of tree
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q15.** Which traversal is used to COPY a binary tree (creating an exact duplicate)?
(A) Inorder
(B) Postorder
(C) Preorder
(D) More than one of the above
(E) None of the above

---

**Q16.** A binary tree where the height difference between left and right subtrees is MORE than 1 for some node is called:
(A) Perfect Binary Tree
(B) Complete Binary Tree
(C) Unbalanced (Skewed) Binary Tree
(D) More than one of the above
(E) None of the above

---

**Q17.** In DFS traversal using explicit Stack, which traversal naturally results from pushing RIGHT child before LEFT child?
(A) Inorder
(B) Postorder
(C) Preorder
(D) More than one of the above
(E) None of the above

---

**Q18.** The number of leaf nodes in a Perfect Binary Tree of height h is:
(A) 2^(h-1)
(B) 2^h
(C) 2^(h+1) - 1
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is NOT a standard tree traversal method?
(A) Preorder
(B) Inorder
(C) Randomized traversal
(D) More than one of the above
(E) None of the above

---

**Q20.** In Postorder traversal, which node is visited LAST?
(A) The leftmost leaf
(B) The rightmost leaf
(C) The root
(D) More than one of the above
(E) None of the above

---

**Q21.** Consider: Preorder = D, B, A, C, F, E, G | Inorder = A, B, C, D, E, F, G
What is the ROOT of the tree?
(A) A
(B) B
(C) D
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following statements about a Complete Binary Tree is TRUE?
(A) All leaf nodes must be at the same level
(B) Every node must have exactly 2 children
(C) The last level is filled from LEFT to RIGHT with no gaps before filled positions
(D) More than one of the above
(E) None of the above

---

**Q23.** The Preorder traversal of a tree visits nodes in which order?
(A) Left → Root → Right
(B) Left → Right → Root
(C) Root → Left → Right
(D) More than one of the above
(E) None of the above

---

**Q24.** A binary tree with n leaf nodes and all internal nodes having exactly 2 children has how many internal nodes?
(A) n
(B) n - 1
(C) n + 1
(D) More than one of the above
(E) None of the above

---

**Q25.** For BFS vs DFS on the same tree:
(A) BFS uses more memory than DFS in general (when tree is wide)
(B) DFS always finds the shortest path
(C) BFS and DFS always visit the same number of nodes in same order
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Physics — Bernoulli's Principle

---

**Q26.** Bernoulli's Principle states that for an ideal fluid in flow, as fluid speed INCREASES:
(A) Pressure also increases
(B) Pressure decreases
(C) Pressure remains constant
(D) More than one of the above
(E) None of the above

---

**Q27.** Which scientist formulated the principle relating fluid speed and pressure?
(A) Isaac Newton
(B) Daniel Bernoulli
(C) Archimedes
(D) More than one of the above
(E) None of the above

---

**Q28.** The lift force on an airplane wing is PRIMARILY explained by:
(A) Newton's Second Law of Motion
(B) Archimedes' Principle
(C) Bernoulli's Principle
(D) More than one of the above
(E) None of the above

---

**Q29.** On an airplane wing, the pressure is LOWER on which surface?
(A) The flat bottom surface
(B) The curved top surface
(C) Both surfaces have equal pressure
(D) More than one of the above
(E) None of the above

---

**Q30.** Bernoulli's Principle is based on the conservation of:
(A) Momentum
(B) Mass
(C) Energy
(D) More than one of the above
(E) None of the above

---

**Q31.** The Continuity Equation A₁v₁ = A₂v₂ implies that when a pipe narrows:
(A) Fluid velocity decreases
(B) Fluid velocity increases
(C) Fluid velocity stays the same
(D) More than one of the above
(E) None of the above

---

**Q32.** Which of the following is NOT a condition for the applicability of Bernoulli's Principle?
(A) Fluid must be incompressible
(B) Flow must be turbulent
(C) Fluid must be non-viscous
(D) More than one of the above
(E) None of the above

---

**Q33.** In a perfume atomizer (spray bottle), the liquid is lifted because:
(A) The rubber bulb directly pushes the liquid up
(B) Rapid air flow above the tube creates low pressure, and atmospheric pressure pushes liquid up
(C) The bottle heats the liquid causing it to evaporate
(D) More than one of the above
(E) None of the above

---

**Q34.** The Bernoulli's equation for horizontal flow (same height) is:
(A) P + ρgh = constant
(B) P + ½ρv² = constant
(C) ½ρv² + ρgh = constant
(D) More than one of the above
(E) None of the above

---

**Q35.** Which device uses Bernoulli's Principle to MEASURE the flow speed of fluids in a pipe?
(A) Barometer
(B) Manometer
(C) Venturi meter
(D) More than one of the above
(E) None of the above

---

**Q36.** When a storm blows, a roof may be blown off because:
(A) High-speed wind above the roof creates low pressure, while inside pressure is relatively high
(B) The wind directly pushes the roof upward from below
(C) Gravity reverses during high-speed winds
(D) More than one of the above
(E) None of the above

---

**Q37.** The Magnus Effect in cricket (swing bowling) is related to which principle?
(A) Newton's Third Law only
(B) Archimedes' Principle
(C) Bernoulli's Principle
(D) More than one of the above
(E) None of the above

---

**Q38.** In a Bunsen burner, air is drawn in when gas flows through the narrow jet because:
(A) The gas is lighter than air
(B) Fast-moving gas creates low pressure, which draws air in from the sides
(C) Air is heated by the gas and expands into the burner
(D) More than one of the above
(E) None of the above

---

**Q39.** Bernoulli's Principle best applies to which type of fluid flow?
(A) Turbulent flow
(B) Compressible flow
(C) Steady, streamlined (laminar) flow
(D) More than one of the above
(E) None of the above

---

**Q40.** The Torricelli's theorem (v = √2gh) is a special case of:
(A) Newton's Law of Gravitation
(B) Archimedes' Principle
(C) Bernoulli's Principle
(D) More than one of the above
(E) None of the above

---

**Q41.** In Bernoulli's equation P + ½ρv² + ρgh = constant, the term ½ρv² represents:
(A) Pressure energy per unit volume
(B) Potential energy per unit volume
(C) Kinetic energy per unit volume
(D) More than one of the above
(E) None of the above

---

**Q42.** A filter pump (laboratory suction pump) works on the principle of:
(A) Pascal's Law
(B) Bernoulli's Principle — fast water jet creates low pressure to suck gas
(C) Boyle's Law
(D) More than one of the above
(E) None of the above

---

**Q43.** In a carburetor, petrol is drawn into the airstream because:
(A) A pump forces petrol into the air
(B) Fast-moving air through the venturi creates low pressure which sucks in petrol
(C) Petrol is lighter than air and naturally rises
(D) More than one of the above
(E) None of the above

---

**Q44.** Which statement correctly explains why two parallel ships moving in the same direction tend to ATTRACT each other?
(A) Gravitational force between the ships
(B) Faster water between ships creates lower pressure, pushing ships inward
(C) Magnetic force from the steel hulls
(D) More than one of the above
(E) None of the above

---

**Q45.** The density symbol ρ (rho) in Bernoulli's equation refers to:
(A) Pressure of the fluid
(B) Density of the fluid
(C) Radius of the flow pipe
(D) More than one of the above
(E) None of the above

---

**Q46.** What happens to the pressure in a fluid when it flows from a wide pipe into a narrower pipe?
(A) Pressure increases
(B) Pressure decreases
(C) Pressure remains unchanged
(D) More than one of the above
(E) None of the above

---

**Q47.** Daniel Bernoulli published his principle in which book?
(A) Principia Mathematica
(B) Hydrodynamica
(C) Mechanica
(D) More than one of the above
(E) None of the above

---

**Q48.** In the full Bernoulli equation P + ½ρv² + ρgh = constant, ρgh represents:
(A) Kinetic energy per unit volume
(B) Static pressure
(C) Potential energy per unit volume
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following applications does NOT primarily rely on Bernoulli's Principle?
(A) Airplane wing lift
(B) Perfume atomizer spray
(C) Hydraulic jack (press)
(D) More than one of the above
(E) None of the above

---

**Q50.** The shape of an aircraft wing designed to generate lift is called:
(A) Parabola
(B) Aerofoil
(C) Ellipse
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
| 1 | (C) | Edges = nodes - 1 (fundamental tree property) |
| 2 | (C) | Binary Tree: AT MOST 2 children per node |
| 3 | (C) | Inorder of BST = sorted ascending |
| 4 | (C) | Level-Order / BFS uses QUEUE |
| 5 | (C) | Leaf = node with no children (degree 0) |
| 6 | (C) | Preorder: Root FIRST, then left, then right |
| 7 | (C) | Full BT: Leaves = Internal + 1 = 6 + 1 = 7 |
| 8 | (C) | Postorder: 4,5,2,3,1 (Left→Right→Root) |
| 9 | (B) | Perfect BT height 3: 2^(3+1)-1 = 2^4-1 = 15 |
| 10 | (B) | Left child of i = 2i+1 (0-indexed) |
| 11 | (B) | Heap = Complete Binary Tree |
| 12 | (B) | BST with 1-7, Inorder = 1,2,3,4,5,6,7 (sorted) |
| 13 | (B) | BFS = level by level |
| 14 | (C) | Depth of root = 0 (root has no edges above it) |
| 15 | (C) | Preorder (root first) — create root before children |
| 16 | (C) | Height diff > 1 = unbalanced/skewed |
| 17 | (C) | Stack: push right first → pop left first → Preorder result |
| 18 | (B) | Leaves in perfect BT of height h = 2^h |
| 19 | (C) | "Randomized traversal" does NOT exist |
| 20 | (C) | Postorder: root is ALWAYS last |
| 21 | (C) | First element of Preorder = ROOT = D |
| 22 | (C) | Complete BT: last level filled left to right, no gaps |
| 23 | (C) | Preorder = Root → Left → Right |
| 24 | (B) | Full BT: Internal nodes = Leaf nodes - 1 = n - 1 |
| 25 | (A) | BFS stores all nodes at current level → more memory for wide trees |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Bernoulli: speed UP → pressure DOWN |
| 27 | (B) | Daniel Bernoulli (1738, Hydrodynamica) |
| 28 | (C) | Airplane lift = Bernoulli's Principle |
| 29 | (B) | Curved top → faster air → LOWER pressure on top |
| 30 | (C) | Bernoulli = Conservation of Energy for fluids |
| 31 | (B) | Narrow pipe → smaller A → larger v (A₁v₁=A₂v₂) |
| 32 | (B) | Turbulent flow → Bernoulli does NOT apply (needs laminar) |
| 33 | (B) | Fast air above tube = low pressure → atm pressure lifts liquid |
| 34 | (B) | For horizontal flow (h same): P + ½ρv² = constant |
| 35 | (C) | Venturi meter measures fluid flow speed |
| 36 | (A) | Fast wind above = low pressure above; inside = high pressure → upward force |
| 37 | (C) | Magnus Effect (spinning ball) = Bernoulli based |
| 38 | (B) | Fast gas = low pressure → draws air in from sides |
| 39 | (C) | Bernoulli applies to steady, laminar (streamlined) flow |
| 40 | (C) | Torricelli's theorem = special case of Bernoulli |
| 41 | (C) | ½ρv² = kinetic energy per unit volume |
| 42 | (B) | Filter pump: fast water jet creates low pressure → suction |
| 43 | (B) | Venturi/carburetor: fast air = low pressure → sucks petrol |
| 44 | (B) | Water between ships moves faster → lower pressure → ships pushed together |
| 45 | (B) | ρ (rho) = density of the fluid |
| 46 | (B) | Narrow pipe → faster flow → LOWER pressure (Bernoulli) |
| 47 | (B) | Bernoulli published in "Hydrodynamica" (1738) |
| 48 | (C) | ρgh = potential energy per unit volume |
| 49 | (C) | Hydraulic jack works on Pascal's Law (pressure transmission), NOT Bernoulli |
| 50 | (B) | Aircraft wing shape = AEROFOIL |

---
---

# 🔁 DAY 24 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Trees & Binary Trees

### Key Terminology One-Liners:
```
Root:     Topmost node; exactly ONE root per tree; has no parent
Leaf:     Node with NO children (degree = 0)
Degree:   Number of children a node has
Height:   Longest path from node DOWN to a leaf (measured in edges)
Depth:    Path from ROOT DOWN to the node (measured in edges)
Depth of root = 0; Height of leaf = 0
Edges in tree = Nodes - 1 (ALWAYS)
Level of root = 0 (edge-counting convention)
```

### Binary Tree Types — Quick Rules:
```
FULL:      Every node has 0 OR 2 children (never 1). Leaves = Internal + 1.
COMPLETE:  All levels full except possibly last; last level fills LEFT→RIGHT.
PERFECT:   All leaves at same level; ALL internal nodes have 2 children.
           Total nodes = 2^(h+1) - 1. Leaf nodes = 2^h.
BALANCED:  Height diff of left & right subtrees ≤ 1 at EVERY node.
SKEWED:    All nodes have only 1 child → degenerates to linked list.

HIERARCHY: Perfect ⊂ Complete (perfect is a special complete)
           Perfect ⊂ Full (perfect is a special full)
           A tree can be Full but NOT Complete; Complete but NOT Full.
```

### Four Traversals — The ONE Table You Must Know:
```
Traversal   | Order          | Data Struct | Key Use
------------|----------------|-------------|----------------------------------
Preorder    | Root→Left→Right| Stack(recur)| Copy tree; Prefix expressions
Inorder     | Left→Root→Right| Stack(recur)| SORTED output from BST ← KEY!
Postorder   | Left→Right→Root| Stack(recur)| Delete tree; Postfix expressions
Level-Order | Level by level | QUEUE       | BFS; shortest path
```

### On tree: A(root) → B,C → D,E,F (B has D,E; C has F):
```
Preorder:   A B D E C F
Inorder:    D B E A C F
Postorder:  D E B F C A
Level-Order:A B C D E F
```

### BFS vs DFS:
```
BFS: QUEUE, level-by-level, finds shortest path in unweighted graphs
DFS: STACK (recursion), branch-by-branch, preorder/inorder/postorder
```

### Critical Formulas:
```
Edges in tree             = n - 1
Max nodes at level k      = 2^k (0-indexed)
Perfect BT total nodes    = 2^(h+1) - 1
Perfect BT leaf nodes     = 2^h
Full BT: Leaves           = Internal nodes + 1
Left child of node i      = 2i+1 (0-indexed array)
Right child of node i     = 2i+2 (0-indexed array)
```

### 3 Biggest PYQ Traps:
```
TRAP 1: Inorder of BST = SORTED (ascending) — most tested fact
TRAP 2: BFS uses QUEUE; DFS uses STACK — always tested
TRAP 3: "Randomized traversal" = does NOT exist — choose real traversal
```

---

## ⚡ RAPID FIRE — Bernoulli's Principle

### The Golden Rule:
```
FAST FLUID → LOW PRESSURE
SLOW FLUID → HIGH PRESSURE
Speed and Pressure are INVERSELY related in a flowing fluid.
```

### Formula:
```
P + ½ρv² + ρgh = constant (along a streamline)
For horizontal flow: P + ½ρv² = constant
P = pressure, ρ = density, v = velocity, g = 9.8 m/s², h = height
½ρv² = KE/volume,  ρgh = PE/volume
```

### Conditions (Must Know):
```
→ Ideal fluid (non-viscous, no friction)
→ Incompressible (constant density)
→ Steady flow (velocity constant at each point)
→ Streamlined / Laminar flow (NOT turbulent)
```

### Top 7 Applications:
```
1. AIRPLANE WING → Curved top = fast air = LOW pressure above; net LIFT upward
2. VENTURI METER → Narrow section = fast flow = low pressure → measures flow speed
3. ATOMIZER/SPRAY → Fast air above tube = low pressure → liquid sucked up and sprayed
4. BUNSEN BURNER → Fast gas = low pressure → air drawn in for combustion
5. CARBURETOR → Fast air = low pressure → petrol sucked into engine
6. ROOF IN STORM → Fast wind above = low pressure above roof; inside pressure lifts roof
7. CRICKET SWING → Spinning ball (Magnus Effect) — one side fast = low pressure → curves
```

### Bernoulli vs Related Laws:
```
Pascal's Law:       Pressure in enclosed fluid transmitted equally everywhere (hydraulic jack)
Archimedes:         Buoyancy = weight of displaced fluid (NOT Bernoulli)
Torricelli:         v = √(2gh) for fluid from a hole — SPECIAL CASE of Bernoulli
Hydraulic Jack/Press: Pascal's Law (NOT Bernoulli) ← PYQ TRAP!
```

### Memory Trick — AVBCR:
```
A = Airplane lift
V = Venturi meter
B = Bunsen burner
C = Carburetor/Cricket ball
R = Roof in storm
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Tree: edges = nodes-1; Perfect BT: 2^(h+1)-1 total nodes, 2^h leaves; Full BT: Leaves = Internal + 1
2. Inorder of BST = SORTED output; Postorder visits ROOT LAST; Level-Order uses QUEUE (BFS)
3. BFS = QUEUE = Level-by-Level; DFS = STACK = Branch-by-Branch (Pre/In/Post are DFS)
4. Bernoulli: FAST flow = LOW pressure; SLOW flow = HIGH pressure; based on conservation of energy
5. Airplane lift = curved top → faster air → low pressure above; flat bottom → slow air → high pressure below → net upward lift

---

*Next: Day 25 — Stack Data Structure (LIFO, Array & LL implementation, Applications: Expression evaluation, Infix/Postfix conversion) | GS: Indian History — Harappan & Vedic Civilization*
