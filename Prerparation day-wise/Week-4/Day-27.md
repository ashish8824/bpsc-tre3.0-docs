# 📅 BPSC TRE 4.0 — DAY 27 COMPLETE STUDY MODULE
### Graph Basics, BFS & DFS + Biology — Ginger, Yeast & Plant Biology
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Graph Basics, Representations, BFS & DFS
> - Afternoon (1 hr): Biology — Ginger (Rhizome), Yeast (Budding), Plant Classification
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Graph Basics, BFS & DFS — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Graph?

### Real-Life Analogy 1 — Social Network:
```
Think of INSTAGRAM or FACEBOOK:
  → Each USER = a VERTEX (node)
  → Each FRIENDSHIP/FOLLOW = an EDGE

Facebook (mutual friendship):
  If A is friends with B → B is also friends with A
  → UNDIRECTED graph (friendship goes both ways)

Twitter/Instagram (follower):
  A can follow B without B following A
  → DIRECTED graph (follow goes one way)

Social network AS A GRAPH:
    [Rahul]——[Priya]——[Amit]
       |         |
    [Sonia]    [Ravi]

Vertices: {Rahul, Priya, Amit, Sonia, Ravi}
Edges: {Rahul-Priya, Priya-Amit, Rahul-Sonia, Priya-Ravi}
```

### Real-Life Analogy 2 — Road Map (GPS):
```
Think of GOOGLE MAPS:
  → Each CITY = a VERTEX
  → Each ROAD between cities = an EDGE
  → Distance on road = WEIGHT of edge

    [Patna]——400km——[Delhi]
      |                |
    200km            300km
      |                |
    [Gaya]——500km——[Lucknow]

This is a WEIGHTED, UNDIRECTED graph.
BFS finds the shortest route between cities (in unweighted version).
```

### Formal Definition:
A **Graph G = (V, E)** consists of:
- **V** = set of **Vertices** (also called Nodes or Points)
- **E** = set of **Edges** (also called Links or Arcs)

Each edge connects a **pair of vertices**.

```
Graph G = (V, E):
  V = {A, B, C, D, E}
  E = {(A,B), (A,C), (B,D), (C,D), (D,E)}

      A
     / \
    B   C
     \ /
      D
      |
      E
```

---

## 🔷 SECTION 2: Graph Terminology

### Key Terms:

**VERTEX (Node):** A fundamental unit. Every object/entity.

**EDGE:** Connection between two vertices.

**ADJACENT VERTICES:** Two vertices connected by an edge.
```
If edge (A, B) exists → A and B are adjacent (neighbours).
```

**DEGREE of a vertex:** Number of edges incident to it.
```
In undirected graph:
  Degree of A = number of edges FROM/TO A

In directed graph:
  IN-DEGREE = number of edges COMING IN
  OUT-DEGREE = number of edges GOING OUT

Graph:  A → B → C → A (cycle)
        In-degree of B = 1 (from A)
        Out-degree of B = 1 (to C)
```

**PATH:** Sequence of vertices where each consecutive pair is connected by an edge.

**CYCLE:** A path that starts and ends at the SAME vertex.
```
A — B — C — A  is a cycle (length 3)
```

**CONNECTED GRAPH:** There exists a PATH between every pair of vertices.
```
CONNECTED:           DISCONNECTED:
A — B — C            A — B    C — D
    |                         (no path from A to C)
    D
All vertices reachable       Two separate components
```

**WEIGHTED GRAPH:** Edges have numerical values (weights/costs).
```
    A ——5—— B
    |        |
    3        2
    |        |
    C ——1—— D
Edge weights = distances, costs, times, etc.
```

### 🚨 PYQ TRAP #1: Degree Sum
```
HANDSHAKING LEMMA:
Sum of degrees of ALL vertices = 2 × Number of edges

Because each edge contributes to the degree of TWO vertices.

Example: Graph with 4 vertices and 5 edges
  Sum of all degrees = 2 × 5 = 10

Implication: In ANY graph, the number of vertices with ODD degree is EVEN.
```

---

## 🔷 SECTION 3: Types of Graphs

### Type 1: UNDIRECTED GRAPH
```
Edges have NO direction. (A-B) means both A→B AND B→A.

      A
     / \
    B   C
     \ /
      D

Used for: Social networks (mutual friendship), roads (two-way), chemical bonds
```

### Type 2: DIRECTED GRAPH (DIGRAPH)
```
Edges have DIRECTION (arrows). (A→B) means ONLY A to B, NOT B to A.

    A ——→ B
    ↑     ↓
    D ←—— C

Used for: Twitter follow, web page links, task dependencies, one-way roads
```

### Type 3: WEIGHTED GRAPH
```
Edges have numerical WEIGHTS.

    A ——5—— B ——2—— C
            |
            3
            |
            D

Used for: Road distances, flight costs, network latency
```

### Type 4: COMPLETE GRAPH (Kₙ)
```
Every vertex is connected to EVERY other vertex.

K₄ (complete graph, 4 vertices):
    A ——— B
    |  \/ |
    |  /\ |
    C ——— D

Number of edges in Kₙ = n(n-1)/2

K₄: 4×3/2 = 6 edges
K₅: 5×4/2 = 10 edges
```

### Type 5: CYCLIC vs ACYCLIC
```
CYCLIC: Contains at least one cycle.
  A → B → C → A   (cycle: A→B→C→A)

ACYCLIC: Contains NO cycles.
  Trees are acyclic connected graphs!

DAG = Directed Acyclic Graph (used in task scheduling, dependency resolution)
```

---

## 🔷 SECTION 4: Graph Representation — Adjacency Matrix

### What is an Adjacency Matrix?
A **2D array** of size V × V (where V = number of vertices).
- `matrix[i][j] = 1` if edge exists between vertex i and vertex j
- `matrix[i][j] = 0` if no edge exists

### Example Graph:
```
Graph (undirected, 4 vertices):
    0 ——— 1
    |   / |
    |  /  |
    2 ——— 3

Vertices: {0, 1, 2, 3}
Edges: {0-1, 0-2, 1-2, 1-3, 2-3}
```

### Adjacency Matrix:
```
     0   1   2   3
  ┌───┬───┬───┬───┐
0 │ 0 │ 1 │ 1 │ 0 │   Row 0: connected to 1 and 2
  ├───┼───┼───┼───┤
1 │ 1 │ 0 │ 1 │ 1 │   Row 1: connected to 0, 2, and 3
  ├───┼───┼───┼───┤
2 │ 1 │ 1 │ 0 │ 1 │   Row 2: connected to 0, 1, and 3
  ├───┼───┼───┼───┤
3 │ 0 │ 1 │ 1 │ 0 │   Row 3: connected to 1 and 2
  └───┴───┴───┴───┘

For UNDIRECTED graph: matrix is SYMMETRIC (matrix[i][j] = matrix[j][i])
For WEIGHTED graph: store weight instead of 1
```

### Properties:
```
SPACE: O(V²) — always V×V matrix regardless of edges
CHECK if edge exists: O(1) — just look up matrix[i][j]
FIND all neighbours of v: O(V) — scan the entire row
SUITABLE for: Dense graphs (many edges), small graphs

DISADVANTAGE: Wastes memory for sparse graphs
  If V = 1000, matrix size = 1000×1000 = 1,000,000 cells
  Even if only 1,500 edges → most cells are 0 (wasted!)
```

---

## 🔷 SECTION 5: Graph Representation — Adjacency List

### What is an Adjacency List?
An **array of lists** where each index stores the **list of neighbours** of that vertex.

### Same Example Graph:
```
Graph:
    0 ——— 1
    |   / |
    |  /  |
    2 ——— 3

Adjacency List:
  0: [1, 2]         → vertex 0 is connected to 1 and 2
  1: [0, 2, 3]      → vertex 1 is connected to 0, 2, and 3
  2: [0, 1, 3]      → vertex 2 is connected to 0, 1, and 3
  3: [1, 2]         → vertex 3 is connected to 1 and 2

Visual:
  0 → [1] → [2] → NULL
  1 → [0] → [2] → [3] → NULL
  2 → [0] → [1] → [3] → NULL
  3 → [1] → [2] → NULL
```

### Properties:
```
SPACE: O(V + E) — only stores actual edges, not all V² possibilities
CHECK if edge exists: O(degree of vertex) — scan the list
FIND all neighbours: O(degree) — just read the list
SUITABLE for: Sparse graphs (few edges), large graphs

ADVANTAGE: Much more memory-efficient for sparse graphs
  1000 vertices, 1500 edges: stores 1000 + 2×1500 = 4000 entries
  vs adjacency matrix: 1,000,000 entries!
```

---

## 🔷 SECTION 6: Adjacency Matrix vs Adjacency List — Comparison

```
MASTER COMPARISON TABLE:

Feature              | Adjacency Matrix      | Adjacency List
---------------------|----------------------|------------------
Space complexity     | O(V²)                | O(V + E)
Check edge (u,v)?    | O(1) — instant       | O(degree of u)
Find all neighbours  | O(V) — scan row      | O(degree of u)
Add a vertex         | O(V²) — resize matrix| O(1)
Add an edge          | O(1)                 | O(1)
Remove an edge       | O(1)                 | O(degree)
Best for             | DENSE graphs         | SPARSE graphs
Memory efficiency    | Poor for sparse      | Excellent
Used when            | V is small; many edges| V is large; few edges
BFS/DFS complexity   | O(V²)                | O(V + E)
```

### 🚨 PYQ TRAP #2: When to Use Which?
```
DENSE graph: E ≈ V² (many edges, nearly complete) → Adjacency MATRIX
SPARSE graph: E << V² (few edges) → Adjacency LIST

Example:
  Road network (1000 cities, 1500 roads): SPARSE → use Adjacency List
  Social network where everyone knows everyone: DENSE → Matrix acceptable
  
DEFAULT CHOICE: Adjacency List is preferred for most real-world graphs
                because real-world graphs are usually SPARSE.
```

---

## 🔷 SECTION 7: BFS — Breadth-First Search

### The Core Idea:
**"Explore all NEIGHBOURS first, before going deeper."**

Like ripples spreading from a stone thrown in water — first reaches nearest points, then farther points level by level.

```
WAVE ANALOGY:
  Start at vertex S (like stone dropped in water)
  Wave 1: All vertices 1 edge away from S
  Wave 2: All vertices 2 edges away from S
  Wave 3: All vertices 3 edges away from S
  ...
```

### BFS Algorithm:
```
BFS(Graph G, start vertex s):
  1. Create an empty QUEUE Q
  2. Mark s as VISITED
  3. Enqueue s into Q
  4. While Q is NOT empty:
       a. Dequeue front vertex u from Q
       b. PROCESS u (print/store it)
       c. For each UNVISITED neighbour v of u:
            → Mark v as VISITED
            → Enqueue v into Q
```

### Step-by-Step BFS Example:
```
Graph:
    A ——— B ——— E
    |     |
    C ——— D

Adjacency List:
  A: [B, C]
  B: [A, D, E]
  C: [A, D]
  D: [B, C]
  E: [B]

BFS starting from A:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Step 1: Queue=[A], Visited={A}
        Dequeue A → Process A → print "A"
        Neighbours of A: B (unvisited), C (unvisited)
        Enqueue B, Enqueue C
        Queue=[B, C], Visited={A, B, C}

Step 2: Queue=[B, C]
        Dequeue B → Process B → print "B"
        Neighbours of B: A (visited), D (unvisited), E (unvisited)
        Enqueue D, Enqueue E
        Queue=[C, D, E], Visited={A, B, C, D, E}

Step 3: Queue=[C, D, E]
        Dequeue C → Process C → print "C"
        Neighbours of C: A (visited), D (visited)
        Nothing to enqueue
        Queue=[D, E]

Step 4: Queue=[D, E]
        Dequeue D → Process D → print "D"
        Neighbours of D: B (visited), C (visited)
        Nothing to enqueue
        Queue=[E]

Step 5: Queue=[E]
        Dequeue E → Process E → print "E"
        Neighbours of E: B (visited)
        Nothing to enqueue
        Queue=[]

Queue EMPTY → BFS COMPLETE

BFS ORDER: A → B → C → D → E
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Queue State Diagram:
```
Step  |  Action         | Queue State     | Output
------|-----------------|-----------------|-------
Start | Enqueue A       | [A]             |
  1   | Dequeue A       | []              | A
      | Enqueue B, C    | [B, C]          |
  2   | Dequeue B       | [C]             | B
      | Enqueue D, E    | [C, D, E]       |
  3   | Dequeue C       | [D, E]          | C
      | (nothing new)   | [D, E]          |
  4   | Dequeue D       | [E]             | D
      | (nothing new)   | [E]             |
  5   | Dequeue E       | []              | E
      | Queue empty     |   DONE          |

RESULT: A, B, C, D, E  (level-by-level)
Level 0: A
Level 1: B, C  (1 edge from A)
Level 2: D, E  (2 edges from A)
```

### BFS Properties:
```
DATA STRUCTURE: QUEUE (FIFO — First In, First Out)
TRAVERSAL: Level by level (closest vertices first)
SPACE: O(V) — worst case all vertices in queue
TIME: O(V + E) with adjacency list; O(V²) with matrix

APPLICATIONS:
  1. SHORTEST PATH in UNWEIGHTED graphs (minimum number of edges)
  2. Level-order traversal of trees
  3. Finding all connected components
  4. Web crawling (visiting web pages level by level)
  5. Social network friend suggestions (friends of friends)
  6. GPS/Map routing (unweighted roads)
  7. Bipartite graph checking
```

---

## 🔷 SECTION 8: DFS — Depth-First Search

### The Core Idea:
**"Go as DEEP as possible along one path before backtracking."**

Like exploring a maze — go down one corridor completely, hit a dead end, come back, try another corridor.

```
MAZE ANALOGY:
  You explore a maze.
  At each junction, pick a direction and GO.
  Keep going until you hit a DEAD END.
  Then BACKTRACK to the last junction.
  Try another unexplored direction.
  Repeat until all paths explored.
```

### DFS Algorithm (Recursive):
```
DFS(Graph G, vertex u, visited[]):
  1. Mark u as VISITED
  2. PROCESS u (print/store it)
  3. For each UNVISITED neighbour v of u:
       → DFS(G, v, visited)   ← Recurse deeply!
```

### DFS Algorithm (Iterative — using explicit Stack):
```
DFS(Graph G, start vertex s):
  1. Create empty STACK S
  2. Push s onto S
  3. While S is NOT empty:
       a. Pop vertex u from S
       b. If u is NOT visited:
            → Mark u as VISITED
            → PROCESS u (print it)
            → For each neighbour v of u:
                 If v is NOT visited → Push v onto S
```

### Step-by-Step DFS Example (SAME graph as BFS):
```
Graph:
    A ——— B ——— E
    |     |
    C ——— D

Adjacency List:
  A: [B, C]
  B: [A, D, E]
  C: [A, D]
  D: [B, C]
  E: [B]

DFS starting from A (recursive, visit in order given):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DFS(A):
  Mark A visited, print A
  Neighbours of A: B, C
  Visit B (first unvisited neighbour):
    DFS(B):
      Mark B visited, print B
      Neighbours of B: A(visited), D, E
      Visit D:
        DFS(D):
          Mark D visited, print D
          Neighbours of D: B(visited), C
          Visit C:
            DFS(C):
              Mark C visited, print C
              Neighbours of C: A(visited), D(visited)
              No unvisited neighbours → RETURN (backtrack)
          ← back to D, no more unvisited → RETURN (backtrack)
      ← back to B, visit E:
        DFS(E):
          Mark E visited, print E
          Neighbours of E: B(visited)
          No unvisited neighbours → RETURN (backtrack)
      ← back to B, no more unvisited → RETURN
  ← back to A, C is already visited → DONE

DFS ORDER: A → B → D → C → E
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Call Stack Visualization:
```
Time:  1    2    3    4    5    5    4    3    6    3
Action: A→  B→   D→   C→  ret  ret  ret  E→  ret  ret
Stack: [A] [A,B] [A,B,D] [A,B,D,C] [A,B,D] [A,B] [A,B] [A,B,E] [A,B] [A]

PATH TRACED (going deep first):
A → B → D → C → (backtrack to D) → (backtrack to B) → E → (backtrack all)
```

### DFS Properties:
```
DATA STRUCTURE: STACK (explicitly or via RECURSION call stack)
TRAVERSAL: Goes deep before wide (branch-first)
SPACE: O(V) — worst case all vertices on stack
TIME: O(V + E) with adjacency list

APPLICATIONS:
  1. CYCLE DETECTION in graphs
  2. TOPOLOGICAL SORTING (ordering tasks with dependencies)
  3. Finding CONNECTED COMPONENTS
  4. MAZE SOLVING (find any path)
  5. Detecting articulation points and bridges
  6. Solving puzzles (e.g., Sudoku, N-Queens)
  7. Finding strongly connected components (Kosaraju's, Tarjan's)
  8. Path finding (not shortest, but finds A path)
```

---

## 🔷 SECTION 9: BFS vs DFS — The Master Comparison

```
SIDE-BY-SIDE COMPARISON ON SAME GRAPH:

Graph:
    A ——— B ——— E
    |     |
    C ——— D

BFS from A: A, B, C, D, E   (level-by-level: closest first)
DFS from A: A, B, D, C, E   (depth-first: go deep before coming back)

WHY DIFFERENT? BFS explores all at same distance first.
               DFS dives deep into one branch first.
```

### Master Comparison Table:

| Feature | BFS | DFS |
|---------|-----|-----|
| Data Structure | **QUEUE** (FIFO) | **STACK** (LIFO) or Recursion |
| Traversal style | Level by level | Branch by branch (deep first) |
| Space (worst case) | O(V) — wide trees | O(V) — deep trees |
| Time complexity | O(V + E) | O(V + E) |
| Finds shortest path? | **YES** (unweighted graphs) | NO |
| Detects cycles? | Yes (can be done) | **YES** (more naturally) |
| Topological sort? | No | **YES** |
| Memory usage | More (all level nodes) | Less (just current path) |
| Complete for finite? | Yes | Yes |
| Backtracking? | No | **YES** |
| Implementation | Usually iterative (queue) | Recursive or iterative (stack) |
| Best for | Shortest path, nearest friend | Cycle detect, topo sort, maze |

### 🚨 PYQ TRAP #3: BFS Finds Shortest Path
```
BFS gives the SHORTEST PATH (fewest edges) in an UNWEIGHTED graph.
DFS does NOT guarantee shortest path.

For WEIGHTED graphs, use Dijkstra's Algorithm (not covered today).

If someone says "DFS finds shortest path" → WRONG.
If someone says "BFS uses Stack" → WRONG (BFS uses QUEUE).
If someone says "DFS uses Queue" → WRONG (DFS uses STACK).
```

---

## 🔷 SECTION 10: Complete BFS vs DFS Visual Trace

### Graph for Both Traces:
```
         1
        / \
       2   3
      / \   \
     4   5   6
```

**BFS Traversal (starting at 1):**
```
Queue progression:
[1] → Dequeue 1, Enqueue 2,3 → [2,3]
[2,3] → Dequeue 2, Enqueue 4,5 → [3,4,5]
[3,4,5] → Dequeue 3, Enqueue 6 → [4,5,6]
[4,5,6] → Dequeue 4 → [5,6]
[5,6] → Dequeue 5 → [6]
[6] → Dequeue 6 → []

BFS: 1, 2, 3, 4, 5, 6   (Level 0→1→2 order)
```

**DFS Traversal (starting at 1, go left first):**
```
Call stack:
DFS(1): print 1, go to 2
  DFS(2): print 2, go to 4
    DFS(4): print 4, no children → return
  DFS(2): go to 5
    DFS(5): print 5, no children → return
  DFS(2): done → return
DFS(1): go to 3
  DFS(3): print 3, go to 6
    DFS(6): print 6, no children → return
  DFS(3): done → return

DFS: 1, 2, 4, 5, 3, 6   (goes deep left first)
```

---

## 🔷 SECTION 11: Applications in Depth

### BFS Application — Shortest Path:
```
Find minimum edges to get from A to E:

    A ——— B ——— D
    |           |
    C ——————————E

BFS from A:
  Level 0: {A}
  Level 1: {B, C}        (distance 1 from A)
  Level 2: {D} from B;   (distance 2 from A)
           {E} from C    (distance 2 from A)
  Level 3: {E} from D    (distance 3 — already visited at level 2!)

Shortest path A→E = 2 edges (A→C→E)
BFS NATURALLY finds this because it explores level by level!
```

### DFS Application — Cycle Detection:
```
DFS can detect if a graph has a BACK EDGE (edge to an ancestor in DFS tree).
A back edge = CYCLE exists.

In DFS, maintain "currently in stack" set:
  If DFS visits a node already in the current stack → CYCLE found!

Graph with cycle:  A → B → C → A
DFS from A:
  Visit A (push to stack: {A})
  Visit B (stack: {A,B})
  Visit C (stack: {A,B,C})
  Visit A → A is already in stack! → CYCLE DETECTED!
```

### DFS Application — Topological Sort:
```
Used for TASK ORDERING with dependencies.

Example: Course prerequisites
  Math → Physics → Engineering
  Math must be done BEFORE Physics
  Physics must be done BEFORE Engineering

Model as DAG (Directed Acyclic Graph):
  Math → Physics → Engineering

DFS + Post-order gives TOPOLOGICAL SORT:
  Visit Math (no prereqs first) → Physics → Engineering
  TOPO ORDER: Math, Physics, Engineering

RULE: A vertex appears AFTER all its dependencies.
```

---

## 🔷 SECTION 12: Important Graph Algorithms Overview

```
ALGORITHM            | PURPOSE                      | METHOD
---------------------|------------------------------|------------------
BFS                  | Shortest path (unweighted)   | Queue
DFS                  | Cycle detection, topo sort   | Stack/Recursion
Dijkstra's           | Shortest path (weighted)     | Min-Heap + Greedy
Bellman-Ford         | Shortest path (neg. weights) | Dynamic Programming
Floyd-Warshall       | All-pairs shortest path      | Dynamic Programming
Kruskal's            | Minimum Spanning Tree        | Sort edges + Union-Find
Prim's               | Minimum Spanning Tree        | Min-Heap + Greedy
Topological Sort     | Task ordering (DAG)          | DFS or Kahn's (BFS)
```

### 🚨 PYQ TRAP #4: Greedy, DP, Divide & Conquer Are NOT Graph Traversals
```
Graph TRAVERSAL algorithms: BFS and DFS
  → They visit vertices in a specific order

Graph TRAVERSAL ≠ Algorithmic PARADIGMS:
  GREEDY algorithms: Make locally optimal choice at each step
    (Dijkstra's, Kruskal's, Prim's ARE greedy — but they're not traversals)
  DYNAMIC PROGRAMMING: Solve subproblems, cache results
    (Floyd-Warshall is DP)
  DIVIDE & CONQUER: Split problem into smaller subproblems
    (Merge Sort, QuickSort are D&C)

If exam asks "which is a graph TRAVERSAL technique?"
  Answer: BFS or DFS only
  NOT: Greedy, DP, Divide & Conquer, Backtracking
```

---

## 🔷 SECTION 13: Graph Summary Mind Map

```
                         GRAPH G = (V, E)
                               |
            ┌──────────────────┼─────────────────┐
            |                  |                 |
        TYPES            REPRESENTATION       TRAVERSAL
            |                  |                 |
    Directed/Undirected   Adj. Matrix         BFS          DFS
    Weighted/Unweighted   → O(V²) space    → Queue      → Stack/Recursion
    Connected/Disconn.    → O(1) edge chk  → Level-by-  → Deep first
    Cyclic/Acyclic                         level        → Backtracks
    Complete (Kₙ)         Adj. List        → Shortest   → Cycle detect
                          → O(V+E) space   path         → Topo sort
                          → O(degree) chk
                          → Sparse graphs

KEY FORMULAS:
  Complete graph Kₙ: n(n-1)/2 edges
  Spanning tree: N-1 edges
  Sum of degrees = 2 × E
  BFS/DFS time: O(V+E) with adj list
```

---

# PART 2: GENERAL STUDIES
## 🌿 Biology — Ginger, Yeast & Plant Biology Deep Dive

---

## 🔷 SECTION 1: Ginger — The Underground Champion

### What is Ginger?
**Ginger** (Zingiber officinale) is a flowering plant whose **underground stem (rhizome)** is widely used as a spice, medicine, and food.

### Ginger's Botanical Classification:
```
Kingdom:    Plantae (Plants)
Division:   Angiosperms (Flowering plants)
Class:      Monocotyledons (Monocots)
Order:      Zingiberales
Family:     Zingiberaceae (Ginger family)
Genus:      Zingiber
Species:    Z. officinale

What we eat: The RHIZOME (underground stem)
             → The horizontal, underground, fleshy stem
             → Also called: "Ginger root" (common misnomer)
             → NOT actually a root — it's a MODIFIED STEM
```

### What is a Rhizome?
```
RHIZOME = A horizontally growing UNDERGROUND STEM

How to identify it's a STEM (not a root):
  1. Has NODES and INTERNODES (like any stem)
  2. Has SCALE LEAVES at nodes
  3. Has BUDS at nodes (can sprout new shoots upward and roots downward)
  4. Grows HORIZONTALLY underground

Compare: TRUE ROOT has no nodes, no buds, no scale leaves.

Visual structure of ginger rhizome:
         ↑ New shoot (grows above ground)
   ─────●───────●───────●─────────
        │node   │       │
        ▼ Fibrous roots (grow downward from nodes)

The ● symbols = NODES (where buds and roots arise)
```

### Ginger as Vegetative Propagation:
```
Ginger is propagated VEGETATIVELY — using rhizome pieces (not seeds!).

How farmers grow ginger:
  1. Take a piece of ginger rhizome with at least ONE NODE (eye/bud)
  2. Plant it in moist soil
  3. The bud at the node sprouts → new shoot grows upward
  4. Roots grow downward from the node
  5. New rhizome develops underground → harvest after 8-10 months

This is ASEXUAL REPRODUCTION via vegetative propagation.
Offspring = genetically IDENTICAL to parent.

Other examples of RHIZOMES:
  → Turmeric (Haldi) — Curcuma longa
  → Lotus (Nelumbo) — aquatic plant, horizontal rhizome
  → Ferns — many species have rhizomes
  → Grass — some grasses spread via rhizomes
```

### Modified Stems — The Complete Picture:
```
UNDERGROUND MODIFIED STEMS:

1. RHIZOME: Horizontal underground stem with nodes
   Examples: GINGER, TURMERIC, FERN, LOTUS
   ─────────●─────────●──── (horizontal)

2. TUBER: Swollen tip of underground stem; no distinct nodes ring
   Examples: POTATO (eyes = nodes!), Jimikand (yam)
   Potato "eyes" are actually NODES with buds!
         ●●●
        ●   ●
         ●●●   (rounded, swollen)

3. BULB: Very short disc-like stem surrounded by fleshy scale leaves
   Examples: ONION, GARLIC, LILY
            ))))   (fleshy layers around central stem)

4. CORM: Vertical underground stem; solid (not hollow like bulb)
   Examples: Colocasia (Arbi/Taro), Crocus, Gladiolus
   
ABOVE GROUND MODIFIED STEMS:

5. STOLON (Runner): Horizontal stem growing ON the surface
   Examples: STRAWBERRY, Oxalis, Grass
   Plant ──●── Plant ──●── Plant (horizontal above ground)

6. TENDRIL: Modified stem for climbing
   Examples: Cucumber, Pumpkin, Passion flower
```

### 🚨 PYQ TRAP #1: Ginger is a Rhizome (Stem, NOT Root)
```
Common questions:
Q: "Ginger is a ___?" → Answer: Rhizome (underground stem/modified stem)
Q: "Which part of ginger plant is used as spice?" → Answer: Rhizome
Q: "Ginger reproduces by ___?" → Answer: Vegetative propagation (via rhizome)
Q: "Ginger is a root/stem/leaf?" → Answer: STEM (specifically rhizome)

TRAP: Many people call it "ginger root" — it is NOT a ROOT.
It is an underground STEM (rhizome).

Easy memory: "GINGER has GIRTH like a stem and NODES like a stem"
```

---

## 🔷 SECTION 2: Turmeric (Haldi) — Ginger's Close Relative

```
Turmeric = Curcuma longa
Underground part = RHIZOME (same as ginger)
Family = Zingiberaceae (same as ginger!)
Propagation = Vegetative (rhizome pieces)
Active compound = CURCUMIN (gives yellow colour, anti-inflammatory)
Uses: Spice, medicine, antiseptic, religious ceremonies (haldi in weddings)

Both Ginger and Turmeric:
  → Belong to family Zingiberaceae
  → Have RHIZOMES (underground stems)
  → Reproduced vegetatively
  → Used as spices in Indian cuisine
```

---

## 🔷 SECTION 3: Yeast — The Unicellular Fungus

### What is Yeast?
**Yeast** (Saccharomyces cerevisiae) is a unicellular (single-celled) **FUNGUS** belonging to the kingdom **Fungi**.

### Yeast Classification:
```
Kingdom:    Fungi
Division:   Ascomycota (Sac fungi)
Class:      Saccharomycetes
Genus:      Saccharomyces
Species:    S. cerevisiae (baker's/brewer's yeast)

Structure:
  → Single-celled (unicellular)
  → Has a nucleus (EUKARYOTE)
  → Cell wall made of CHITIN (not cellulose like plants)
  → Oval to round shape, 5-10 micrometres
  → Can live with or without oxygen (facultative anaerobe)
```

### Yeast Reproduction — BUDDING:
```
Process of Budding in Yeast:
  1. Parent yeast cell grows a small PROTRUSION (bud) on its surface
  2. The NUCLEUS of parent divides (mitosis)
  3. One nucleus moves into the BUD
  4. The bud grows larger
  5. A CELL WALL forms between parent and bud
  6. The bud DETACHES (or may remain temporarily attached)
  7. New yeast cell is born → identical to parent

Visual:
  Parent cell:   (○)
  Bud appears:   (○)(·)
  Bud grows:     (○)(○)
  Bud detaches:  (○)  (○)   ← Two separate yeast cells

RATE: Under ideal conditions, yeast can bud every 90-120 minutes!
Result: EXPONENTIAL growth — one cell → 2 → 4 → 8 → 16...
```

### Yeast Fermentation — Most Important Exam Topic:
```
FERMENTATION = Yeast converts GLUCOSE (sugar) into:
  → ETHANOL (alcohol) + CARBON DIOXIDE gas + Energy

Equation:
  C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ + Energy
  (Glucose) → (Ethanol/Alcohol) + (Carbon dioxide)

This process is ANAEROBIC (without oxygen).
Also called ANAEROBIC RESPIRATION.

Applications of Yeast Fermentation:

BAKING (bread making):
  Yeast added to dough → ferments sugars → CO₂ produced
  CO₂ bubbles get trapped in dough → dough RISES (becomes fluffy)
  Ethanol evaporates during baking
  RESULT: Light, airy bread with holes

BREWING (beer/wine):
  Yeast added to fruit juice/grain → ferments sugars
  ETHANOL produced = alcohol in beer, wine
  CO₂ produced = bubbles in beer (carbonation)

IDLI/DOSA (Indian food):
  Batter fermented by yeast and bacteria → dough rises → soft idli/dosa

VINEGAR production (by bacteria, not yeast — common confusion!)
  Acetic acid bacteria + ethanol → ACETIC ACID (vinegar)
```

### 🚨 PYQ TRAP #2: Yeast Key Facts
```
YEAST IS:
  ✓ Unicellular FUNGUS (not bacteria, not plant)
  ✓ Eukaryote (has nucleus)
  ✓ Reproduces by BUDDING
  ✓ Kingdom: FUNGI (not Monera/Protista)
  ✓ Used in BREAD making (CO₂ raises dough)
  ✓ Used in ALCOHOL fermentation (produces ethanol)
  ✓ Cell wall: CHITIN

YEAST IS NOT:
  ✗ A bacterium (bacteria = prokaryotes; yeast = eukaryote)
  ✗ A plant (no chlorophyll, no photosynthesis)
  ✗ Reproducing by binary fission (that's bacteria/Amoeba)
```

---

## 🔷 SECTION 4: Fermentation vs Respiration — Comparison

```
AEROBIC RESPIRATION:
  Glucose + Oxygen → CO₂ + Water + LOTS of Energy (38 ATP)
  C₆H₁₂O₆ + 6O₂ → 6CO₂ + 6H₂O + 38 ATP
  Location: Mitochondria
  Organisms: Most living things (humans, animals, plants)

ANAEROBIC RESPIRATION (FERMENTATION in yeast):
  Glucose (no oxygen) → Ethanol + CO₂ + LESS Energy (2 ATP)
  C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ + 2 ATP
  Location: Cytoplasm (no mitochondria needed)
  Organisms: Yeast, some bacteria, muscle cells (lactic acid)

LACTIC ACID FERMENTATION (in muscle cells):
  Glucose → Lactic Acid + Energy (2 ATP)
  Occurs: During intense exercise when O₂ supply is insufficient
  Result: Muscle cramps, burning sensation
```

---

## 🔷 SECTION 5: Other Fungi — Brief Classification

```
KINGDOM FUNGI:
  → Multicellular (mostly) or unicellular (yeast)
  → HETEROTROPHIC (cannot make own food — no chlorophyll)
  → Cell wall: CHITIN
  → Reproduce by: SPORES (mostly)
  → Mode of nutrition: Absorptive (secrete enzymes, absorb nutrients)

Types of Fungi based on nutrition:
  SAPROPHYTES: Feed on dead/decaying organic matter
    Examples: Rhizopus (bread mould), Agaricus (mushroom)
  PARASITES: Feed on living organisms (cause disease)
    Examples: Puccinia (wheat rust), Ustilago (smut)
  MUTUALISTS: Live in beneficial partnership
    Examples: Mycorrhizae (fungi + plant roots), Lichen (fungi + algae)

KEY FUNGI for BPSC exam:
  Yeast (Saccharomyces) → budding, fermentation
  Rhizopus → spore formation (bread mould)
  Penicillium → produces PENICILLIN (antibiotic!) — discovered by Alexander Fleming
  Agaricus → mushroom (edible, saprophyte)
  Puccinia → wheat rust (parasite, causes crop disease)
```

### 🚨 PYQ TRAP #3: Penicillin from Fungus
```
PENICILLIN (first antibiotic) was discovered from PENICILLIUM fungus.
Discovered by: Alexander Fleming (1928) — accidentally noticed mould killing bacteria.
Used to treat: Bacterial infections (pneumonia, strep throat, syphilis)
IMPORTANT: Penicillin is from a FUNGUS, not a bacterium.
```

---

## 🔷 SECTION 6: Plant Reproduction Methods — Comprehensive Summary

```
PLANT REPRODUCTION:
        |
   ┌────┴────┐
ASEXUAL    SEXUAL
   |
   ├── Vegetative Propagation
   │     ├── Rhizome: Ginger, Turmeric, Lotus, Fern
   │     ├── Tuber:   Potato, Jimikand
   │     ├── Bulb:    Onion, Garlic
   │     ├── Corm:    Colocasia (Arbi), Crocus
   │     ├── Stolon:  Strawberry, Oxalis
   │     └── Leaf:    Bryophyllum (leaf buds)
   │
   ├── Spore Formation
   │     ├── Ferns, Mosses
   │     ├── Rhizopus (bread mould)
   │     └── Mucor
   │
   └── Fragmentation
         └── Spirogyra, algae
```

---

## 🔷 SECTION 7: Memory Tricks — Biology

### Underground Modified Stems — "GRIT-BC":
```
G = Ginger → Rhizome
R = Rhizome (Turmeric too!)
I = (same)
T = Tuber → Potato
B = Bulb → Onion, Garlic
C = Corm → Colocasia (Arbi)
```

### Yeast Memory Points — "FUBEK":
```
F = Fungi (kingdom)
U = Unicellular
B = Budding (reproduction)
E = Eukaryote (has nucleus)
K = chitin cell wall (Kitin)
```

### Fermentation Equation Memory:
```
Sugar → Alcohol + CO₂ (think: bread RISES with CO₂; beer has ALCOHOL)
Glucose → Ethanol + Carbon Dioxide
"Yeast eats sugar, breathes out CO₂, and makes alcohol as waste"
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Graph Basics, BFS, DFS, Representation, Applications

---

**Q1.** A graph G = (V, E) consists of which two components?
(A) Vertices and Weights
(B) Vertices and Edges
(C) Nodes and Levels
(D) More than one of the above
(E) None of the above

---

**Q2.** In an UNDIRECTED graph, if vertex A has degree 4, it means:
(A) A has 4 paths to other vertices
(B) A is connected to 4 other vertices
(C) A has 4 levels below it
(D) More than one of the above
(E) None of the above

---

**Q3.** BFS traversal of a graph uses which data structure?
(A) Stack
(B) Priority Queue
(C) Queue
(D) More than one of the above
(E) None of the above

---

**Q4.** DFS traversal of a graph uses which data structure?
(A) Queue
(B) Stack or Recursion
(C) Array
(D) More than one of the above
(E) None of the above

---

**Q5.** BFS gives the SHORTEST PATH in which type of graph?
(A) Weighted directed graph
(B) Unweighted graph (shortest in terms of number of edges)
(C) Complete graph only
(D) More than one of the above
(E) None of the above

---

**Q6.** The time complexity of BFS and DFS using an Adjacency List is:
(A) O(V²)
(B) O(E log V)
(C) O(V + E)
(D) More than one of the above
(E) None of the above

---

**Q7.** What is the space complexity of an Adjacency Matrix for a graph with V vertices?
(A) O(V + E)
(B) O(V)
(C) O(V²)
(D) More than one of the above
(E) None of the above

---

**Q8.** For a SPARSE graph (few edges), which representation is more memory-efficient?
(A) Adjacency Matrix
(B) Incidence Matrix
(C) Adjacency List
(D) More than one of the above
(E) None of the above

---

**Q9.** In a directed graph (digraph), edges have:
(A) No weight
(B) Direction (arrows)
(C) Both direction and weight always
(D) More than one of the above
(E) None of the above

---

**Q10.** The sum of degrees of ALL vertices in an undirected graph with E edges is:
(A) E
(B) E/2
(C) 2E
(D) More than one of the above
(E) None of the above

---

**Q11.** DFS is best suited for which of the following applications?
(A) Finding shortest path in unweighted graph
(B) Level-order traversal
(C) Cycle detection and topological sorting
(D) More than one of the above
(E) None of the above

---

**Q12.** Consider graph: A-B, A-C, B-D, C-D, D-E (undirected).
BFS from A gives which order?
(A) A, B, D, C, E
(B) A, B, C, D, E
(C) A, C, B, D, E
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following is NOT a graph traversal algorithm?
(A) BFS (Breadth First Search)
(B) DFS (Depth First Search)
(C) Divide and Conquer
(D) More than one of the above
(E) None of the above

---

**Q14.** In an undirected complete graph Kₙ, the number of edges is:
(A) n²
(B) n(n-1)
(C) n(n-1)/2
(D) More than one of the above
(E) None of the above

---

**Q15.** Which traversal visits nodes LEVEL BY LEVEL in a graph?
(A) DFS
(B) Topological Sort
(C) BFS
(D) More than one of the above
(E) None of the above

---

**Q16.** To check if an edge (u, v) exists in a graph, which representation is faster?
(A) Adjacency List — O(1)
(B) Adjacency Matrix — O(1)
(C) Both are equally fast O(1)
(D) More than one of the above
(E) None of the above

---

**Q17.** In a DIRECTED graph, the IN-DEGREE of a vertex is:
(A) Number of edges going OUT from it
(B) Number of edges coming IN to it
(C) Total edges connected to it
(D) More than one of the above
(E) None of the above

---

**Q18.** A DAG stands for:
(A) Dense Adjacency Graph
(B) Directed Acyclic Graph
(C) Double Adjacency Graph
(D) More than one of the above
(E) None of the above

---

**Q19.** DFS on a graph detects a CYCLE when:
(A) A vertex is visited twice in different runs
(B) A visited vertex is encountered that is already on the current DFS stack (back edge)
(C) The queue becomes empty
(D) More than one of the above
(E) None of the above

---

**Q20.** Dijkstra's Algorithm finds shortest path in:
(A) Unweighted graphs (same as BFS)
(B) Weighted graphs with non-negative weights
(C) Graphs with negative edge weights
(D) More than one of the above
(E) None of the above

---

**Q21.** BFS is used for "finding friends of friends" in a social network because:
(A) It finds all vertices at equal distance (same level) first
(B) It uses less memory than DFS
(C) It detects cycles in social networks
(D) More than one of the above
(E) None of the above

---

**Q22.** The adjacency list of a graph stores, for each vertex, its:
(A) List of all vertices in the graph
(B) List of adjacent (neighbouring) vertices
(C) List of vertices sorted by degree
(D) More than one of the above
(E) None of the above

---

**Q23.** For a graph with V = 5 vertices and E = 3 edges, the adjacency matrix size is:
(A) 3 × 3
(B) 5 × 3
(C) 5 × 5
(D) More than one of the above
(E) None of the above

---

**Q24.** Which algorithm is used for TOPOLOGICAL SORTING of a Directed Acyclic Graph (DAG)?
(A) BFS only
(B) Prim's Algorithm
(C) DFS (produces topological order via finishing times)
(D) More than one of the above
(E) None of the above

---

**Q25.** In BFS, the visited array/set is necessary to:
(A) Sort vertices alphabetically
(B) Prevent visiting the same vertex more than once (avoid infinite loops in cyclic graphs)
(C) Calculate edge weights
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Biology — Ginger, Yeast, Fermentation, Plant Biology

---

**Q26.** The part of the ginger plant used as a spice is which type of plant structure?
(A) Root
(B) Rhizome (underground modified stem)
(C) Bulb
(D) More than one of the above
(E) None of the above

---

**Q27.** Ginger reproduces by which method?
(A) Spore formation
(B) Binary fission
(C) Vegetative propagation (via rhizome)
(D) More than one of the above
(E) None of the above

---

**Q28.** A rhizome is distinguished from a root because a rhizome has:
(A) Green colour and performs photosynthesis
(B) Nodes, internodes, and scale leaves (stem characteristics)
(C) Root hairs for water absorption
(D) More than one of the above
(E) None of the above

---

**Q29.** Turmeric (Haldi) belongs to which plant family?
(A) Solanaceae (Potato family)
(B) Zingiberaceae (Ginger family)
(C) Liliaceae (Lily family)
(D) More than one of the above
(E) None of the above

---

**Q30.** Yeast belongs to which kingdom?
(A) Plantae
(B) Monera
(C) Fungi
(D) More than one of the above
(E) None of the above

---

**Q31.** Yeast reproduces by which method of asexual reproduction?
(A) Binary fission
(B) Budding
(C) Spore formation
(D) More than one of the above
(E) None of the above

---

**Q32.** Yeast is classified as a:
(A) Prokaryote (no nucleus)
(B) Eukaryote with nucleus and chitin cell wall
(C) Photosynthetic organism
(D) More than one of the above
(E) None of the above

---

**Q33.** During bread making, yeast causes the dough to RISE because:
(A) Yeast produces oxygen that inflates the dough
(B) Yeast ferments sugars and produces CO₂ gas that gets trapped in dough
(C) Yeast produces ethanol that evaporates and creates bubbles
(D) More than one of the above
(E) None of the above

---

**Q34.** The products of yeast fermentation (anaerobic) are:
(A) CO₂ and Water only
(B) Glucose and Oxygen
(C) Ethanol (alcohol) and CO₂
(D) More than one of the above
(E) None of the above

---

**Q35.** Which organism produces PENICILLIN — the first antibiotic?
(A) Penicillium (a fungus)
(B) Yeast (Saccharomyces)
(C) Rhizopus (bread mould)
(D) More than one of the above
(E) None of the above

---

**Q36.** Potato reproduces vegetatively through:
(A) Rhizomes
(B) Bulbs
(C) Tubers
(D) More than one of the above
(E) None of the above

---

**Q37.** Onion reproduces vegetatively through:
(A) Tubers
(B) Bulbs
(C) Rhizomes
(D) More than one of the above
(E) None of the above

---

**Q38.** Strawberry spreads vegetatively through:
(A) Rhizomes (underground horizontal stems)
(B) Tubers
(C) Stolons/Runners (horizontal stems on soil surface)
(D) More than one of the above
(E) None of the above

---

**Q39.** What is the cell wall composition of fungi?
(A) Cellulose (like plants)
(B) Peptidoglycan (like bacteria)
(C) Chitin
(D) More than one of the above
(E) None of the above

---

**Q40.** Bryophyllum reproduces vegetatively from which part?
(A) Roots
(B) Leaves (buds form on leaf margins)
(C) Underground stems
(D) More than one of the above
(E) None of the above

---

**Q41.** Alexander Fleming discovered penicillin when he noticed:
(A) Yeast producing antibiotic compounds
(B) A Penicillium mould killing surrounding bacteria on a culture plate
(C) Bacteria becoming resistant to chemicals
(D) More than one of the above
(E) None of the above

---

**Q42.** Rhizopus (bread mould) reproduces by:
(A) Binary fission
(B) Budding
(C) Spore formation
(D) More than one of the above
(E) None of the above

---

**Q43.** Lactic acid fermentation (in human muscle cells during intense exercise) produces:
(A) Ethanol and CO₂
(B) Lactic acid and a small amount of energy
(C) Glucose and ATP
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following plants has a CORM as its underground modified stem?
(A) Ginger (rhizome)
(B) Potato (tuber)
(C) Colocasia/Arbi (corm)
(D) More than one of the above
(E) None of the above

---

**Q45.** The process of fermentation in yeast is:
(A) Aerobic (requires oxygen)
(B) Anaerobic (does NOT require oxygen)
(C) Can only happen in the presence of sunlight
(D) More than one of the above
(E) None of the above

---

**Q46.** Colocasia (Arbi/Taro) is reproduced vegetatively using:
(A) Rhizomes
(B) Runners
(C) Corms
(D) More than one of the above
(E) None of the above

---

**Q47.** Which of the following pairs is CORRECTLY matched — organism to mode of reproduction?
(A) Yeast → Binary fission; Amoeba → Budding
(B) Amoeba → Binary fission; Yeast → Budding
(C) Spirogyra → Budding; Rhizopus → Binary fission
(D) More than one of the above
(E) None of the above

---

**Q48.** The fermentation equation for yeast is:
C₆H₁₂O₆ → ?
(A) 6CO₂ + 6H₂O
(B) 2C₂H₅OH + 2CO₂
(C) 2CH₃COOH (Lactic acid)
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following is an example of a SAPROPHYTIC fungus?
(A) Puccinia (wheat rust — parasite)
(B) Agaricus (mushroom — decomposes dead matter)
(C) Mycorrhizae (mutualist)
(D) More than one of the above
(E) None of the above

---

**Q50.** Ginger and Turmeric both belong to the same plant family. What is that family?
(A) Solanaceae
(B) Poaceae (Grass family)
(C) Zingiberaceae
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
| 1 | (B) | Graph = Vertices + Edges (G = (V,E)) |
| 2 | (B) | Degree = number of connected vertices (edges) |
| 3 | (C) | BFS uses QUEUE (FIFO) |
| 4 | (B) | DFS uses STACK or Recursion (LIFO) |
| 5 | (B) | BFS = shortest path by edge count in unweighted graphs |
| 6 | (C) | BFS/DFS with adj list = O(V + E) |
| 7 | (C) | Adjacency Matrix always = V × V = O(V²) |
| 8 | (C) | Sparse graph → Adjacency List saves memory O(V+E) |
| 9 | (B) | Directed = edges have direction (may or may not be weighted) |
| 10 | (C) | Handshaking lemma: sum of degrees = 2E |
| 11 | (C) | DFS: cycle detection, topological sort |
| 12 | (B) | BFS explores level by level: A→B,C→D→E |
| 13 | (C) | Divide and Conquer is an algorithmic paradigm, not graph traversal |
| 14 | (C) | Complete graph Kₙ: n(n-1)/2 edges |
| 15 | (C) | BFS = level by level traversal |
| 16 | (B) | Adjacency Matrix: O(1) edge check (direct index lookup) |
| 17 | (B) | In-degree = edges coming IN to vertex |
| 18 | (B) | DAG = Directed Acyclic Graph |
| 19 | (B) | Back edge to current stack path = cycle detected |
| 20 | (B) | Dijkstra's = weighted, non-negative edge weights |
| 21 | (A) | BFS explores same-distance nodes first = friends at same hop |
| 22 | (B) | Adjacency list: for each vertex, stores its neighbour list |
| 23 | (C) | Matrix is always V × V = 5 × 5, regardless of E |
| 24 | (C) | DFS naturally produces topological order (reverse finishing time) |
| 25 | (B) | Visited array prevents revisiting = avoids infinite loops in cycles |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Ginger = rhizome (underground modified STEM, not root) |
| 27 | (C) | Ginger = vegetative propagation via rhizome pieces |
| 28 | (B) | Rhizome has nodes, internodes, scale leaves = stem features |
| 29 | (B) | Turmeric = Zingiberaceae (same as ginger) |
| 30 | (C) | Yeast = Kingdom Fungi |
| 31 | (B) | Yeast = BUDDING (not binary fission!) |
| 32 | (B) | Yeast = eukaryote, nucleus present, chitin cell wall |
| 33 | (B) | CO₂ from fermentation trapped in dough → rises |
| 34 | (C) | Yeast fermentation: Glucose → Ethanol + CO₂ |
| 35 | (A) | Penicillin from Penicillium fungus (Fleming, 1928) |
| 36 | (C) | Potato = tubers (not rhizomes!) |
| 37 | (B) | Onion = bulbs |
| 38 | (C) | Strawberry = stolons/runners (above ground horizontal stems) |
| 39 | (C) | Fungi cell wall = CHITIN (not cellulose, not peptidoglycan) |
| 40 | (B) | Bryophyllum = leaf buds (buds on margins of leaves) |
| 41 | (B) | Fleming: Penicillium mould killing bacteria on culture plate |
| 42 | (C) | Rhizopus (bread mould) = spore formation |
| 43 | (B) | Muscle lactic acid fermentation = Lactic acid + ATP |
| 44 | (C) | Colocasia/Arbi = corm (vertical solid underground stem) |
| 45 | (B) | Yeast fermentation = ANAEROBIC (no oxygen) |
| 46 | (C) | Colocasia propagated by corms |
| 47 | (B) | Correct: Amoeba→binary fission; Yeast→budding |
| 48 | (B) | C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ (yeast fermentation) |
| 49 | (B) | Agaricus (mushroom) = saprophyte (decomposes dead matter) |
| 50 | (C) | Both Ginger and Turmeric = Zingiberaceae family |

---
---

# 🔁 DAY 27 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Graph Basics, BFS & DFS

### Graph Fundamentals:
```
Graph = G(V, E): V = vertices, E = edges
Undirected: A-B means both A→B and B→A
Directed:   A→B means only one way
Weighted:   Edges have numerical values
Complete Kₙ: every vertex connects to every other; edges = n(n-1)/2
Handshaking Lemma: Sum of all degrees = 2 × E
DAG = Directed Acyclic Graph (no cycles, used for task scheduling)
```

### Graph Representations:
```
Adjacency Matrix: V×V array; O(V²) space; O(1) edge check; good for DENSE
Adjacency List:   Array of lists; O(V+E) space; good for SPARSE (DEFAULT CHOICE)
```

### BFS — "B for Breadth, B for Ballot Box (Queue)":
```
Uses: QUEUE (FIFO)
Pattern: Level by level (explore all at distance 1, then 2, then 3...)
Time: O(V + E) with adj list
Space: O(V)
Finds: SHORTEST PATH (fewest edges) in unweighted graph
Applications: Shortest path, web crawling, social network friends-of-friends
```

### DFS — "D for Depth, D for Down-the-stack":
```
Uses: STACK (LIFO) or Recursion
Pattern: Go deep first, backtrack when stuck
Time: O(V + E) with adj list
Space: O(V)
Finds: Cycles, topological order, connected components
Applications: Cycle detection, topological sort, maze solving, puzzle solving
```

### BFS vs DFS — One-Table Summary:
```
Feature    | BFS           | DFS
-----------|---------------|----------------
Structure  | QUEUE         | STACK/Recursion
Style      | Level-by-level| Deep first
Shortest?  | YES (unweighted)| NO
Cycle det? | Yes (indirect)| YES (primary)
Topo sort? | No            | YES
```

### 4 CS PYQ Traps:
```
TRAP 1: BFS uses QUEUE; DFS uses STACK — never swap these!
TRAP 2: Greedy/DP/Divide & Conquer = algorithmic PARADIGMS, NOT traversals
TRAP 3: BFS finds shortest path only in UNWEIGHTED graphs (Dijkstra for weighted)
TRAP 4: Adjacency Matrix always V×V regardless of number of edges
```

---

## ⚡ RAPID FIRE — Ginger, Yeast & Biology

### Underground Modified Stems (Most Tested):
```
RHIZOME  → Ginger, Turmeric, Lotus, Fern (horizontal, has nodes)
TUBER    → Potato (eyes = nodes), Jimikand
BULB     → Onion, Garlic (fleshy scale leaves around central bud)
CORM     → Colocasia/Arbi (solid, vertical)
STOLON   → Strawberry (above ground runners)
LEAF     → Bryophyllum (buds on leaf margins)
```

### Yeast — The 5 Key Facts:
```
1. Kingdom = FUNGI (not bacteria, not plant)
2. Unicellular, Eukaryote, Chitin cell wall
3. Reproduces by BUDDING (not binary fission!)
4. Fermentation: Glucose → Ethanol + CO₂ (anaerobic)
5. Uses: Bread (CO₂ raises dough), Beer/Wine (ethanol)
```

### Fermentation Formula:
```
C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ + 2ATP
(Glucose)  (Ethanol) (CO₂)
= Anaerobic; Occurs in cytoplasm
```

### 4 Biology PYQ Traps:
```
TRAP 1: Ginger = RHIZOME (STEM, not root!) — "ginger root" is misleading
TRAP 2: Yeast = BUDDING (not binary fission — that's Amoeba/Bacteria)
TRAP 3: Penicillin from PENICILLIUM FUNGUS (not bacteria)
TRAP 4: Potato has TUBERS (not rhizomes); Ginger has RHIZOMES (not tubers)
```

### Key Organism-Structure-Reproduction:
```
Amoeba      → Binary fission
Yeast       → Budding + Kingdom Fungi
Hydra       → Budding + Animal
Ginger      → Rhizome + Vegetative propagation
Potato      → Tuber + Vegetative propagation
Onion       → Bulb + Vegetative propagation
Spirogyra   → Fragmentation
Rhizopus    → Spore formation (bread mould)
Planaria    → Regeneration
Strawberry  → Stolon/Runner
Bryophyllum → Leaf buds
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. BFS uses QUEUE → level-by-level → finds shortest path (unweighted); DFS uses STACK → deep first → cycle detection, topological sort
2. BFS/DFS time = O(V+E) with adjacency list; Adj Matrix = O(V²) space; Adj List = O(V+E) space; use list for sparse, matrix for dense
3. Greedy/DP/Divide & Conquer are algorithmic paradigms NOT graph traversals — only BFS and DFS are graph traversals
4. Ginger = RHIZOME (underground STEM, not root!); Potato = TUBER; Onion = BULB; Strawberry = STOLON; Bryophyllum = LEAF BUDS
5. Yeast = Fungi, unicellular, BUDDING (not binary fission!); Fermentation = Glucose→Ethanol+CO₂ (anaerobic); Penicillin from Penicillium fungus

---

*Next: Day 28 — DBMS Introduction (Database concepts, ER model, Relational model, Keys) | GS: Indian History — Harappan & Vedic Civilisation*
