# 📅 DAY 27 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## CS Topic: Graph Theory — BFS, DFS, Representations, Applications & Algorithms
## GS Topic: Biology — Plant Kingdom (Ginger, Yeast, Fungi, Algae) + Botany Deep Dive

> **Target:** TOP RANK | Phase 1 — Foundation | Week 4
> **Day 27 of 170 | April–September 2026**
> **Format:** 25 CS MCQs + 25 GS MCQs in BPSC 5-option format | Answers ONLY at the END

---

# ═══════════════════════════════════════════════════
# PART A — COMPUTER SCIENCE
# GRAPH THEORY: Basics | Representations | BFS | DFS | Applications | Algorithms
# ═══════════════════════════════════════════════════

---

## 🔷 SECTION 1: WHAT IS A GRAPH?

A **Graph G = (V, E)** is a data structure consisting of:
- **V** = Set of **Vertices** (also called Nodes)
- **E** = Set of **Edges** (connections between vertices)

**Real World Examples:**
- Social Network: People = vertices, Friendship = edges
- Google Maps: Cities = vertices, Roads = edges
- Internet: Routers = vertices, Cables = edges
- Circuit: Components = vertices, Wires = edges

---

## 🔷 SECTION 2: TYPES OF GRAPHS

```
┌─────────────────────────────────────────────────────────────────┐
│                    GRAPH TYPES                                   │
├─────────────────────────┬───────────────────────────────────────┤
│  UNDIRECTED GRAPH        │  DIRECTED GRAPH (Digraph)             │
│                          │                                       │
│   A ─── B                │   A ──→ B                            │
│   │     │                │   │     ↑                            │
│   C ─── D                │   ↓     │                            │
│                          │   C ──→ D                            │
│  Edge (A,B) = Edge (B,A) │  Edge (A,B) ≠ Edge (B,A)            │
│  Symmetric edges         │  Direction MATTERS                    │
│  Example: Facebook friend│  Example: Twitter follow,            │
│           roads (2-way)  │           one-way roads              │
├─────────────────────────┴───────────────────────────────────────┤
│  WEIGHTED GRAPH             │  UNWEIGHTED GRAPH                  │
│  Edges have values/costs    │  Edges have no weight              │
│  Example: Road distances,   │  Example: Friendship network       │
│           flight costs      │                                    │
├─────────────────────────────┴──────────────────────────────────┤
│  CONNECTED GRAPH            │  DISCONNECTED GRAPH                │
│  Every vertex reachable     │  Some vertices NOT reachable       │
│  from every other vertex    │  from others                       │
└─────────────────────────────────────────────────────────────────┘
```

### Important Graph Terms:

```
DEGREE OF A VERTEX:
  Undirected: Number of edges connected to it
  Directed:   In-degree  = edges COMING IN to vertex
              Out-degree = edges GOING OUT from vertex
  
  Example:
       A ──→ B ──→ C
             ↑
             D
  
  For B: In-degree = 2 (from A and D), Out-degree = 1 (to C)

PATH: Sequence of vertices connected by edges
CYCLE: Path that starts and ends at same vertex
SIMPLE PATH: Path with no repeated vertices

DENSE GRAPH:  Many edges (close to maximum)
SPARSE GRAPH: Few edges (much less than maximum)
```

**Maximum edges possible:**
- Undirected graph with n vertices: **n(n-1)/2**
- Directed graph with n vertices: **n(n-1)**
- Complete graph (all possible edges): denoted **Kn**

---

## 🔷 SECTION 3: GRAPH REPRESENTATIONS

There are TWO main ways to store a graph in memory:

### 3.1 Adjacency Matrix

A 2D array where `matrix[i][j] = 1` if there is an edge between vertex i and j, else `0`.

**Example Graph:**
```
    1
   / \
  2   3
   \ /
    4

Vertices: {1, 2, 3, 4}
Edges: {(1,2), (1,3), (2,4), (3,4)}
```

**Adjacency Matrix:**
```
     1   2   3   4
  ┌──────────────────┐
1 │  0   1   1   0  │
2 │  1   0   0   1  │
3 │  1   0   0   1  │
4 │  0   1   1   0  │
  └──────────────────┘

Note: Matrix is SYMMETRIC for undirected graph
```

**Adjacency Matrix — PROS and CONS:**
```
✅ ADVANTAGES:
   → O(1) to check if edge (i,j) exists
   → Simple to implement
   → Good for DENSE graphs

❌ DISADVANTAGES:
   → O(V²) space — even for sparse graphs (WASTEFUL!)
   → O(V) time to find all neighbours of a vertex
   → Adding/removing vertex is expensive
```

---

### 3.2 Adjacency List

An array of linked lists. `list[i]` contains all vertices adjacent to vertex i.

**Same graph using Adjacency List:**
```
1 → [2, 3]
2 → [1, 4]
3 → [1, 4]
4 → [2, 3]

Visual:
1 ──→ 2 ──→ 3 ──→ NULL
2 ──→ 1 ──→ 4 ──→ NULL
3 ──→ 1 ──→ 4 ──→ NULL
4 ──→ 2 ──→ 3 ──→ NULL
```

**Adjacency List — PROS and CONS:**
```
✅ ADVANTAGES:
   → O(V + E) space — EFFICIENT for sparse graphs
   → O(degree) time to find all neighbours
   → Good for SPARSE graphs

❌ DISADVANTAGES:
   → O(degree) to check if specific edge exists
   → Slightly complex to implement
```

### Comparison Table — BPSC Favourite!

```
┌────────────────────┬─────────────────┬─────────────────────┐
│ Operation          │ Adj. Matrix      │ Adj. List            │
├────────────────────┼─────────────────┼─────────────────────┤
│ Space              │ O(V²)            │ O(V + E)             │
│ Check edge (u,v)   │ O(1)             │ O(degree of u)       │
│ Find all neighbors │ O(V)             │ O(degree of u)       │
│ Add vertex         │ O(V²) rebuild    │ O(1)                 │
│ Add edge           │ O(1)             │ O(1)                 │
│ Best for           │ Dense graphs     │ Sparse graphs        │
│ Used in            │ Floyd-Warshall   │ BFS, DFS, Dijkstra  │
└────────────────────┴─────────────────┴─────────────────────┘
```

**KEY PYQ FACT:** Adjacency Matrix space = O(V²). Adjacency List space = O(V+E). For a graph with 1000 vertices and 1000 edges — Adjacency LIST is MUCH more memory efficient.

---

## 🔷 SECTION 4: BFS — BREADTH FIRST SEARCH

### What is BFS?

BFS explores a graph **level by level** — visiting all neighbours of a vertex before moving deeper.

**Think of it like:** Dropping a stone in water — ripples spread outward in concentric circles.

```
BFS ORDER of Exploration:

        1
       / \
      2   3         Level 0: Visit 1
     / \   \        Level 1: Visit 2, 3
    4   5   6       Level 2: Visit 4, 5, 6

BFS Order: 1 → 2 → 3 → 4 → 5 → 6
```

### BFS uses QUEUE (FIFO):

```
ALGORITHM:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. Start: Put starting vertex in Queue, mark VISITED
2. While Queue is NOT empty:
     a. DEQUEUE a vertex u
     b. PROCESS u (print/record it)
     c. For each unvisited neighbour v of u:
          → Mark v as VISITED
          → ENQUEUE v
3. Done when Queue is empty
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Data Structure Used: QUEUE (FIFO)
```

### BFS Step-by-Step Trace (Detailed Example):

```
Graph:
    A ─── B ─── E
    │     │
    C ─── D

Adjacency List:
A: [B, C]
B: [A, D, E]
C: [A, D]
D: [B, C]
E: [B]

Start BFS from A:

Step 1: Queue=[A], Visited={A}
Step 2: Dequeue A → Process A
        Neighbors of A: B(unvisited), C(unvisited)
        Queue=[B,C], Visited={A,B,C}
Step 3: Dequeue B → Process B
        Neighbors of B: A(visited), D(unvisited), E(unvisited)
        Queue=[C,D,E], Visited={A,B,C,D,E}
Step 4: Dequeue C → Process C
        Neighbors of C: A(visited), D(visited)
        Queue=[D,E], No new additions
Step 5: Dequeue D → Process D
        All neighbors visited
        Queue=[E]
Step 6: Dequeue E → Process E
        Queue=[] → DONE

BFS Order: A → B → C → D → E
```

### BFS Applications:

```
┌─────────────────────────────────────────────────────┐
│              BFS APPLICATIONS                        │
├─────────────────────────────────────────────────────┤
│ 1. SHORTEST PATH in unweighted graphs               │
│    (BFS guarantees minimum number of edges)         │
│                                                     │
│ 2. Web Crawlers (search engines)                    │
│    (Explore links level by level)                   │
│                                                     │
│ 3. Social Network (find people within K hops)       │
│    (Facebook "People You May Know")                 │
│                                                     │
│ 4. Broadcasting in networks                         │
│    (Send message to all reachable nodes)            │
│                                                     │
│ 5. Finding CONNECTED COMPONENTS                     │
│                                                     │
│ 6. Bipartite Graph checking                         │
│    (Can we 2-colour the graph?)                     │
└─────────────────────────────────────────────────────┘
```

### BFS Complexity:

```
Time:  O(V + E)  — visit each vertex once, explore each edge once
Space: O(V)      — for visited array and queue
```

---

## 🔷 SECTION 5: DFS — DEPTH FIRST SEARCH

### What is DFS?

DFS explores a graph by going as **deep as possible** along each path before backtracking.

**Think of it like:** Exploring a maze — go as far as you can, hit a dead end, backtrack, try another path.

```
DFS ORDER of Exploration:

        1
       / \
      2   3         DFS goes DEEP first
     / \   \
    4   5   6

DFS Order (from 1, left first): 1 → 2 → 4 → 5 → 3 → 6
(Goes all the way down before visiting siblings)
```

### DFS uses STACK (LIFO):

DFS can be implemented two ways:
1. **Explicitly using a Stack**
2. **Recursively** (function call stack acts as implicit stack)

```
ALGORITHM (Recursive):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DFS(vertex u, visited[]):
   1. Mark u as VISITED
   2. PROCESS u (print/record it)
   3. For each unvisited neighbour v of u:
        → DFS(v, visited)   ← Recursive call!
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Data Structure Used: STACK (explicit or recursive call stack)
```

### DFS Step-by-Step Trace (Same Graph):

```
Graph:
    A ─── B ─── E
    │     │
    C ─── D

Start DFS from A (visit in alphabetical order):

DFS(A): Mark A visited → Process A
  DFS(B): Mark B visited → Process B
    DFS(D): Mark D visited → Process D
      DFS(C): Mark C visited → Process C
        A already visited, D already visited → RETURN
      → RETURN to D → no more unvisited neighbors → RETURN
    DFS(E): Mark E visited → Process E
      B already visited → RETURN
    → RETURN to B → no more unvisited → RETURN
  A already visited, C already visited → RETURN
  → RETURN to A → no more unvisited → DONE

DFS Order: A → B → D → C → E
```

### DFS Applications:

```
┌─────────────────────────────────────────────────────┐
│              DFS APPLICATIONS                        │
├─────────────────────────────────────────────────────┤
│ 1. CYCLE DETECTION in graphs                        │
│    (If we revisit a visited node → cycle exists)    │
│                                                     │
│ 2. TOPOLOGICAL SORTING                              │
│    (Ordering of tasks with dependencies)            │
│                                                     │
│ 3. Finding STRONGLY CONNECTED COMPONENTS           │
│    (Kosaraju's and Tarjan's algorithms)             │
│                                                     │
│ 4. MAZE SOLVING                                     │
│    (Explore all paths)                              │
│                                                     │
│ 5. Path finding (not necessarily shortest)          │
│                                                     │
│ 6. Detecting BRIDGES and ARTICULATION POINTS       │
└─────────────────────────────────────────────────────┘
```

### DFS Complexity:

```
Time:  O(V + E)  — same as BFS
Space: O(V)      — for visited array and stack/recursion depth
```

---

## 🔷 SECTION 6: BFS vs DFS — COMPLETE COMPARISON

```
┌────────────────────┬─────────────────────┬──────────────────────┐
│ Feature            │ BFS                  │ DFS                   │
├────────────────────┼─────────────────────┼──────────────────────┤
│ Full Form          │ Breadth First Search │ Depth First Search    │
│ Data Structure     │ QUEUE (FIFO)         │ STACK (LIFO)          │
│                    │                      │ or Recursion          │
│ Exploration Style  │ Level by Level       │ One path at a time    │
│ Goes...            │ Wide first           │ Deep first            │
│ Shortest Path?     │ YES (unweighted)     │ NOT guaranteed        │
│ Memory Usage       │ More (stores level)  │ Less (recursion)      │
│ Cycle Detection    │ Yes                  │ Yes (better!)         │
│ Topological Sort   │ No                   │ YES                   │
│ Connected Check    │ Yes                  │ Yes                   │
│ Time Complexity    │ O(V + E)             │ O(V + E)              │
│ Space Complexity   │ O(V)                 │ O(V)                  │
│ Use for            │ Shortest path,       │ Cycle detection,      │
│                    │ Web crawlers         │ Topological sort      │
└────────────────────┴─────────────────────┴──────────────────────┘
```

**⭐ BPSC MOST-ASKED FACTS:**
- BFS uses **QUEUE** | DFS uses **STACK**
- BFS finds **shortest path** in unweighted graph
- DFS used for **topological sorting**
- Both have time complexity **O(V + E)**

---

## 🔷 SECTION 7: TOPOLOGICAL SORTING

### What is it?

Topological Sort is a **linear ordering of vertices** in a **Directed Acyclic Graph (DAG)** such that for every directed edge (u → v), vertex **u comes before v** in the ordering.

**Only works on DAG (Directed Acyclic Graph — no cycles!)**

```
Example: Course Prerequisites

   Math 101 ──→ Math 201 ──→ Math 301
      │                         ↑
      └──→ CS 101 ──→ CS 201 ──┘
      
Topological Order: Math 101 → CS 101 → Math 201 → CS 201 → Math 301
(You must take prerequisites FIRST)

Another valid order: Math 101 → Math 201 → CS 101 → CS 201 → Math 301
(Multiple valid topological orderings possible!)
```

**Algorithms for Topological Sort:**
1. **DFS-based** (Kahn's variant using DFS finish times)
2. **Kahn's Algorithm** (uses in-degree and BFS/Queue)

**KEY PYQ FACT:** Topological sort is possible ONLY on **DAG (no cycles)**. Uses DFS. Result is **NOT unique** (multiple valid orderings possible).

---

## 🔷 SECTION 8: ALGORITHM PARADIGMS (BPSC TRAP TOPIC!)

BPSC frequently asks: "Which of the following is a graph traversal method?"

```
┌─────────────────────────────────────────────────────────────┐
│       ALGORITHM DESIGN PARADIGMS (NOT Traversals!)          │
│                                                             │
│  1. GREEDY Algorithm                                        │
│     → Make locally optimal choice at each step             │
│     → Example: Kruskal's MST, Prim's MST, Dijkstra         │
│     → Does NOT always give global optimum                  │
│                                                             │
│  2. DYNAMIC PROGRAMMING (DP)                                │
│     → Break problem into subproblems, store results         │
│     → Example: Floyd-Warshall, Fibonacci, Knapsack          │
│     → Memoization + Optimal Substructure                   │
│                                                             │
│  3. DIVIDE AND CONQUER                                      │
│     → Divide problem into smaller parts, solve, combine     │
│     → Example: Merge Sort, Quick Sort, Binary Search        │
│                                                             │
│  4. BACKTRACKING                                            │
│     → Try all possibilities, undo bad choices              │
│     → Example: N-Queens, Sudoku Solver                     │
└─────────────────────────────────────────────────────────────┘

BFS and DFS are TRAVERSAL METHODS — not algorithm paradigms!
Greedy, DP, Divide & Conquer are PARADIGMS — not traversals!
```

---

## 🔷 SECTION 9: DIJKSTRA'S ALGORITHM (Shortest Path — Weighted)

BFS finds shortest path in **unweighted** graphs. For **weighted** graphs, use **Dijkstra's Algorithm**.

```
DIJKSTRA'S ALGORITHM:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. Set distance of source = 0, all others = INFINITY
2. Use Min-Heap (Priority Queue)
3. Pick vertex with MINIMUM distance
4. Update distances of its unvisited neighbours
5. Repeat until all vertices processed
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Data Structure: MIN-HEAP (Priority Queue)
Time Complexity: O((V + E) log V) with binary heap
Works on: NON-NEGATIVE weighted graphs only!

⚠️ LIMITATION: Does NOT work with NEGATIVE edge weights
   (Use Bellman-Ford for negative weights)
```

**KEY PYQ COMPARISON:**

| Algorithm | Works On | Finds | Paradigm |
|-----------|----------|-------|---------|
| BFS | Unweighted | Shortest path | Traversal |
| Dijkstra | +ve Weighted | Shortest path | Greedy |
| Bellman-Ford | Any weight | Shortest path | DP |
| Floyd-Warshall | Any weight | All pairs shortest | DP |
| Kruskal's | Weighted | MST | Greedy |
| Prim's | Weighted | MST | Greedy |

---

## 🔷 SECTION 10: SPECIAL GRAPH TYPES

```
┌──────────────────────────────────────────────────────────────┐
│  SPECIAL GRAPH TYPES — Quick Reference                        │
├───────────────────┬──────────────────────────────────────────┤
│ Bipartite Graph   │ Vertices can be divided into 2 sets;     │
│                   │ Edges ONLY between sets (not within)     │
│                   │ Has NO odd-length cycles                 │
│                   │ Can always be 2-coloured                 │
├───────────────────┼──────────────────────────────────────────┤
│ Complete Graph Kn │ Every vertex connected to every other    │
│                   │ Edges = n(n-1)/2                         │
│                   │ K4 has 6 edges, K5 has 10 edges          │
├───────────────────┼──────────────────────────────────────────┤
│ Tree              │ Connected + Acyclic + N-1 edges          │
│                   │ (Special case of graph)                  │
├───────────────────┼──────────────────────────────────────────┤
│ DAG               │ Directed Acyclic Graph                   │
│                   │ No directed cycles                       │
│                   │ Used for topological sort                │
├───────────────────┼──────────────────────────────────────────┤
│ Eulerian Graph    │ Contains an Eulerian Circuit:            │
│                   │ Path that visits every EDGE exactly once │
│                   │ Condition: All vertices have EVEN degree │
├───────────────────┼──────────────────────────────────────────┤
│ Hamiltonian Graph │ Contains path visiting every VERTEX once │
│                   │ (NP-Complete problem!)                   │
└───────────────────┴──────────────────────────────────────────┘
```

---

## 🔷 SECTION 11: CONNECTED COMPONENTS

```
A connected component is a maximal set of vertices such that
there is a path between every pair of vertices in the set.

Example of Graph with 3 connected components:

  Component 1:    Component 2:    Component 3:
    A ─── B          D               F ─── G
    │                                      │
    C                                      H

DFS or BFS can find all connected components:
  → Run DFS from any unvisited vertex
  → All vertices reached = one component
  → Increment component count
  → Find next unvisited vertex, repeat

Algorithm Time: O(V + E)
```

---

## 🔑 SECTION 12: CS QUICK REVISION BULLETS

```
╔═══════════════════════════════════════════════════════╗
║          DAY 27 CS — TOPPER QUICK REVISION            ║
╠═══════════════════════════════════════════════════════╣
║ 1. BFS → QUEUE | DFS → STACK                         ║
║ 2. BFS = shortest path (unweighted)                   ║
║ 3. DFS = cycle detection, topological sort            ║
║ 4. Adjacency Matrix: O(V²) space, O(1) edge check    ║
║ 5. Adjacency List: O(V+E) space, O(deg) edge check   ║
║ 6. BFS and DFS: Time = O(V+E), Space = O(V)          ║
║ 7. Greedy/DP/D&C = paradigms, NOT traversals!        ║
║ 8. Dijkstra: shortest path, +ve weights, Greedy      ║
║ 9. Topological sort: only on DAG, uses DFS           ║
║ 10. Bipartite: 2 vertex sets, no odd cycles          ║
║ 11. Eulerian circuit: all vertices even degree       ║
║ 12. Bellman-Ford handles negative edge weights       ║
╚═══════════════════════════════════════════════════════╝
```

---

# ═══════════════════════════════════════════════════
# PART B — GENERAL SCIENCE (BIOLOGY / BOTANY)
# Plant Kingdom: Ginger, Yeast, Fungi, Algae, Bacteria
# + Full Plant Biology for BPSC
# ═══════════════════════════════════════════════════

---

## 🌿 SECTION 13: FIVE KINGDOM CLASSIFICATION

R.H. Whittaker (1969) proposed the **Five Kingdom Classification**:

```
┌────────────────────────────────────────────────────────────────┐
│                  FIVE KINGDOMS                                  │
├──────────────┬────────────┬────────────────────────────────────┤
│ Kingdom      │ Cell Type  │ Examples                           │
├──────────────┼────────────┼────────────────────────────────────┤
│ MONERA       │ Prokaryote │ Bacteria, Blue-green algae         │
│              │ (No nucleus│ (Cyanobacteria)                    │
│              │  no organl.)│                                   │
├──────────────┼────────────┼────────────────────────────────────┤
│ PROTISTA     │ Eukaryote  │ Amoeba, Paramecium, Euglena,      │
│              │ Unicellular│ Diatoms, Spirogyra                 │
├──────────────┼────────────┼────────────────────────────────────┤
│ FUNGI        │ Eukaryote  │ Mushroom, Yeast, Molds (Rhizopus) │
│              │ Heterotroph│ Penicillium, Aspergillus           │
├──────────────┼────────────┼────────────────────────────────────┤
│ PLANTAE      │ Eukaryote  │ Mosses, Ferns, Gymnosperms,       │
│              │ Autotroph  │ Angiosperms (flowering plants)     │
│              │ Cell wall  │                                    │
├──────────────┼────────────┼────────────────────────────────────┤
│ ANIMALIA     │ Eukaryote  │ Insects, Fish, Amphibians,        │
│              │ Heterotroph│ Reptiles, Birds, Mammals           │
│              │ No cell wall│                                   │
└──────────────┴────────────┴────────────────────────────────────┘
```

**KEY PYQ FACT:** Bacteria belong to Kingdom **MONERA** (Prokaryotes — no membrane-bound nucleus). Yeast is a **Fungus**, not a plant. Amoeba is **Protista**.

---

## 🍄 SECTION 14: FUNGI — DETAILED STUDY (BPSC High Frequency!)

### What are Fungi?

Fungi are **eukaryotic, heterotrophic** organisms. They **cannot make their own food** (no chlorophyll). They absorb nutrients from dead/living organic matter.

```
┌─────────────────────────────────────────────────────────────┐
│              CHARACTERISTICS OF FUNGI                        │
├─────────────────────────────────────────────────────────────┤
│ Cell wall: Made of CHITIN (not cellulose like plants)       │
│ Food:      Heterotrophic (absorptive nutrition)             │
│ Chlorophyll: ABSENT (cannot photosynthesize)                │
│ Body:      Made of Hyphae → network = Mycelium             │
│ Reproduction: Spores (asexual) + sexual                     │
│ Mode of life: Saprophytic (dead matter) OR                  │
│               Parasitic (living host) OR                    │
│               Symbiotic (with algae → Lichen!)             │
└─────────────────────────────────────────────────────────────┘
```

### Important Fungi — BPSC Must Know:

```
┌──────────────────┬──────────────────────────────────────────┐
│ Fungus           │ Importance / Key Fact                     │
├──────────────────┼──────────────────────────────────────────┤
│ YEAST            │ Unicellular fungus                        │
│ (Saccharomyces   │ Reproduces by BUDDING                     │
│  cerevisiae)     │ Used in: Bread making (fermentation)      │
│                  │          Beer/Wine making                  │
│                  │ Converts GLUCOSE → ALCOHOL + CO₂          │
│                  │ (Anaerobic fermentation)                   │
│                  │ Also used in baking (CO₂ makes dough rise)│
├──────────────────┼──────────────────────────────────────────┤
│ RHIZOPUS         │ Common bread mould (black mould)          │
│ (Rhizopus        │ Reproduces by SPORES                      │
│  stolonifer)     │ Sporangia = black dots on bread           │
│                  │ Saprophyte (grows on dead matter)         │
├──────────────────┼──────────────────────────────────────────┤
│ PENICILLIUM      │ Source of PENICILLIN antibiotic           │
│                  │ Discovered by Alexander Fleming (1928)   │
│                  │ Blue-green mould on citrus fruits         │
│                  │ First antibiotic ever discovered!        │
├──────────────────┼──────────────────────────────────────────┤
│ ASPERGILLUS      │ Used in industrial enzyme production      │
│                  │ Some species cause diseases               │
│                  │ Used to make soy sauce, citric acid      │
├──────────────────┼──────────────────────────────────────────┤
│ MUSHROOM         │ Edible fungus (Agaricus bisporus)         │
│ (Agaricus)       │ Has cap, stalk structure                  │
│                  │ Rich in protein                           │
├──────────────────┼──────────────────────────────────────────┤
│ LICHEN           │ SYMBIOSIS of Fungus + Algae               │
│                  │ Fungus provides water/minerals            │
│                  │ Algae provides food (photosynthesis)      │
│                  │ Pioneer organism on bare rocks            │
│                  │ Used as pollution indicator               │
└──────────────────┴──────────────────────────────────────────┘
```

---

## 🌱 SECTION 15: GINGER — A COMPLETE STORY (Bihar Context!)

Bihar is a major producer of Ginger! BPSC frequently asks about Ginger.

```
GINGER (Zingiber officinale)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Scientific Name: Zingiber officinale
Family:          Zingiberaceae

WHAT WE EAT: Underground RHIZOME (Modified Stem)
             → NOT a root! (Common misconception)
             → A rhizome is a HORIZONTAL underground stem
             → Has nodes and internodes (proves it's a stem)
             → Stores food (starch)

REPRODUCTION: Vegetative propagation by RHIZOME
             → Cut rhizome pieces → each grows new plant
             → This is ASEXUAL reproduction (clones)

ACTIVE COMPOUND: Gingerol (gives pungent taste)
                 Zingerone, Shogaols

MEDICINAL USES:
  → Treats nausea, vomiting, morning sickness
  → Anti-inflammatory properties
  → Digestive aid
  → Treats cold and cough (common in Bihar homes!)
  → Dried ginger = Sonth/Saunth (used in Ayurveda)

ECONOMIC IMPORTANCE:
  → India = World's largest producer of Ginger
  → Bihar, Kerala, Karnataka = major producing states
  → Used in cooking, medicine, tea
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Rhizome vs Root — KEY DISTINCTION:**
```
RHIZOME (Modified Stem):          ROOT:
→ Has NODES and INTERNODES        → NO nodes/internodes
→ Has scale leaves (buds)         → NO leaves/buds
→ Grows HORIZONTALLY underground  → Grows VERTICALLY downward
→ Stores FOOD (carbohydrates)     → Absorbs water/minerals
→ Examples: Ginger, Turmeric,     → Examples: Carrot (root),
            Lotus, Fern            Radish (taproot)
```

---

## 🧫 SECTION 16: BACTERIA — FULL DETAILS

```
BACTERIA (Kingdom MONERA)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TYPE: Prokaryote (no membrane-bound nucleus)
SIZE: 1-10 micrometers (visible only under microscope)
CELL WALL: Peptidoglycan (murein)

SHAPES OF BACTERIA:
  Coccus    → Spherical (e.g., Streptococcus)
  Bacillus  → Rod-shaped (e.g., E. coli, TB bacteria)
  Spirillum → Spiral (e.g., Treponema — causes Syphilis)
  Vibrio    → Comma-shaped (e.g., Vibrio cholerae)

REPRODUCTION:
  → Binary Fission (asexual)
  → FASTEST reproducing organism
  → E. coli divides every 20 minutes!
  → In ideal conditions: 1 bacterium → millions in hours

USEFUL BACTERIA:
  Lactobacillus → Curd/yogurt making (converts milk → curd)
  Rhizobium     → Nitrogen fixation in legume roots
  Bacillus       → Decomposers (recycle nutrients)
  Streptomyces  → Source of Streptomycin antibiotic

HARMFUL BACTERIA:
  Mycobacterium tuberculosis → Tuberculosis (TB)
  Vibrio cholerae            → Cholera
  Salmonella typhi           → Typhoid
  Clostridium tetani         → Tetanus
  Yersinia pestis            → Plague (Black Death)

GRAM STAINING:
  Gram Positive: Thick peptidoglycan → Stains PURPLE
  Gram Negative: Thin peptidoglycan  → Stains PINK/RED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🌊 SECTION 17: ALGAE — KEY FACTS

```
ALGAE (mainly Kingdom PROTISTA, some in MONERA)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
→ Have CHLOROPHYLL → can PHOTOSYNTHESIZE
→ Most are AQUATIC (fresh water or marine)
→ No true roots, stem, or leaves (thallophytes)
→ Called "PLANT KINGDOM'S PIONEERS"

TYPES BY COLOUR:
  GREEN ALGAE (Chlorophyceae):
    → Spirogyra (freshwater), Chlamydomonas, Ulva
    → Chlorophyll a and b (green)
    → Ancestor of land plants!
    
  RED ALGAE (Rhodophyceae):
    → Polysiphonia, Gracilaria
    → Found in deep waters
    → Used to make AGAR (laboratory culture medium)
    
  BROWN ALGAE (Phaeophyceae):
    → Laminaria (Kelp), Fucus, Sargassum
    → Marine algae
    → Source of ALGINIC ACID (used in ice cream, toothpaste!)

IMPORTANT ALGAE PRODUCTS:
  Agar       → From Red algae → Used in culture media
  Alginic acid → From Brown algae → Food thickener
  Carrageenan → From Red algae → Ice cream, jellies
  Chlorella   → Green algae → Food supplement (protein rich)
  Spirulina   → Blue-green alga → Superfood, protein

BLUE-GREEN ALGAE (Cyanobacteria) = Kingdom MONERA (Prokaryote!)
  → Nostoc, Anabaena, Oscillatoria
  → Fix NITROGEN from atmosphere
  → Anabaena in Azolla → Natural biofertilizer for rice fields!
  → Cause water bloom (algal bloom) → Water pollution indicator
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🌸 SECTION 18: PLANT HORMONES (PGRs — Plant Growth Regulators)

BPSC asks about plant hormones almost every exam!

```
┌──────────────────────────────────────────────────────────────────┐
│                    PLANT HORMONES                                 │
├───────────────┬──────────────────────────────────────────────────┤
│ AUXIN (IAA)   │ Produced at shoot TIP                           │
│               │ Effect: Cell elongation, apical dominance        │
│               │ Bends stem toward LIGHT (phototropism)          │
│               │ HIGH concentration → inhibits root growth        │
│               │ Used in: Rooting powders, weedkillers           │
├───────────────┼──────────────────────────────────────────────────┤
│ GIBBERELLIN   │ Produced in: Young leaves, seeds                │
│ (GA)          │ Effect: Stem elongation, seed germination        │
│               │ Breaks SEED DORMANCY                            │
│               │ Promotes FLOWERING (long-day plants)            │
│               │ Used in: Brewing industry, seedless grapes      │
├───────────────┼──────────────────────────────────────────────────┤
│ CYTOKININ     │ Produced in: Roots                              │
│               │ Effect: Cell DIVISION (cytokinesis)             │
│               │ Delays AGEING (senescence) of leaves            │
│               │ Promotes lateral bud growth                     │
│               │ Used in: Tissue culture                        │
├───────────────┼──────────────────────────────────────────────────┤
│ ABSCISIC ACID │ Called "STRESS HORMONE" or "Dormancy hormone"   │
│ (ABA)         │ Effect: Closes STOMATA (during drought!)        │
│               │ Promotes seed dormancy                          │
│               │ Promotes leaf FALL (abscission)                 │
│               │ INHIBITORY hormone (opposite of Gibberellin)   │
├───────────────┼──────────────────────────────────────────────────┤
│ ETHYLENE      │ ONLY GASEOUS plant hormone                      │
│               │ Effect: Ripening of FRUITS                      │
│               │ Promotes AGEING                                 │
│               │ Promotes leaf fall                              │
│               │ Used to: Artificially ripen mangoes, bananas   │
│               │ Calcium carbide → releases acetylene →         │
│               │ mimics ethylene → artificial ripening          │
└───────────────┴──────────────────────────────────────────────────┘
```

**KEY PYQ TRICK:** 
- **GIBBERELLIN** breaks dormancy → promotes germination
- **ABSCISIC ACID** promotes dormancy → inhibits germination
- They are OPPOSITES!
- Ethylene is the ONLY **gaseous** hormone

---

## 🌳 SECTION 19: PHOTOSYNTHESIS — DEEP DIVE

```
PHOTOSYNTHESIS EQUATION:
6CO₂ + 6H₂O + Light Energy → C₆H₁₂O₆ + 6O₂
                                (Glucose)

WHERE: Chloroplasts (in MESOPHYLL cells of leaves)
CHLOROPHYLL: Green pigment that absorbs light
             Absorbs RED and BLUE light best
             REFLECTS GREEN light → plants look green!

TWO STAGES:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LIGHT REACTIONS (Light-dependent, in THYLAKOID membrane):
  → Needs: LIGHT, Water
  → Products: ATP, NADPH, O₂ (oxygen released here!)
  → Water is SPLIT (photolysis of water)
  → Photosystems I and II involved

DARK REACTIONS / CALVIN CYCLE (Light-independent, in STROMA):
  → Needs: ATP, NADPH (from light reactions), CO₂
  → Products: GLUCOSE (C₆H₁₂O₆)
  → CO₂ is FIXED here (combined into organic molecules)
  → Doesn't need light directly (but needs products of light rxn)
  → Named after Melvin Calvin (Nobel Prize 1961)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FACTORS AFFECTING PHOTOSYNTHESIS:
  Light intensity, CO₂ concentration, Temperature,
  Water availability, Chlorophyll content
```

---

## 🌾 SECTION 20: IMPORTANT PLANTS — BPSC SPECIAL

```
┌─────────────────────────────────────────────────────────────────┐
│          PLANTS WITH SPECIAL IMPORTANCE FOR BPSC               │
├───────────────────┬─────────────────────────────────────────────┤
│ PLANT             │ KEY FACTS                                    │
├───────────────────┼─────────────────────────────────────────────┤
│ GINGER            │ Rhizome (modified stem), vegetative reprod  │
│ (Zingiber         │ Active: Gingerol, Zingiber family           │
│  officinale)      │ India = largest producer                    │
├───────────────────┼─────────────────────────────────────────────┤
│ TURMERIC          │ Rhizome (modified stem), like ginger        │
│ (Curcuma longa)   │ Active: Curcumin (anti-inflammatory)        │
│                   │ Yellow colour from Curcumin                 │
│                   │ Also called "Indian Gold"                   │
├───────────────────┼─────────────────────────────────────────────┤
│ TULSI             │ Holy Basil — Ocimum sanctum/tenuiflorum    │
│                   │ Medicinal: Antibacterial, antifungal        │
│                   │ Sacred in Hinduism                         │
│                   │ Bihar: Widely grown in courtyards          │
├───────────────────┼─────────────────────────────────────────────┤
│ NEEM              │ Azadirachta indica                          │
│                   │ Active: Azadirachtin (insecticide)          │
│                   │ Uses: Pesticide, medicine, toothbrush       │
│                   │ Bihar: Panchpatthi neem toothbrush famous  │
├───────────────────┼─────────────────────────────────────────────┤
│ BANANA            │ Pseudostem (NOT a true stem — leaf bases)  │
│                   │ Reproduces by suckers (vegetative)         │
│                   │ Fruit: Berry (botanically!)                 │
├───────────────────┼─────────────────────────────────────────────┤
│ POTATO            │ Tuber (modified stem), NOT root            │
│                   │ Eyes of potato = nodes (prove it's stem)   │
│                   │ C.F.: Sweet potato = tuberous ROOT          │
├───────────────────┼─────────────────────────────────────────────┤
│ ONION             │ Bulb (modified stem + leaves)              │
│                   │ Fleshy leaves store food                   │
└───────────────────┴─────────────────────────────────────────────┘
```

---

## 🌍 SECTION 21: ECOLOGY — FOOD CHAIN & ENERGY FLOW

```
FOOD CHAIN:
Sun → Producers → Primary Consumers → Secondary Consumers → Tertiary

Example:
Grass → Grasshopper → Frog → Snake → Eagle

TROPHIC LEVELS:
Level 1: PRODUCERS (Plants, Algae — make own food)
Level 2: PRIMARY CONSUMERS (Herbivores — eat plants)
Level 3: SECONDARY CONSUMERS (Carnivores — eat herbivores)
Level 4: TERTIARY CONSUMERS (Top carnivores)
Level 5: DECOMPOSERS (Fungi, Bacteria — break down dead matter)

10% ENERGY RULE (Lindemann's Law):
→ Only 10% energy transfers to next trophic level
→ 90% lost as heat at each level

Example: 1000 kcal in grass
  → Grasshopper gets: 100 kcal (10%)
  → Frog gets:         10 kcal (10% of 100)
  → Snake gets:         1 kcal (10% of 10)
  → Eagle gets:       0.1 kcal (10% of 1)

WHY SHORT FOOD CHAINS?
→ Because energy is lost at each level
→ Longer chains = less energy available at top
→ Maximum 4-5 trophic levels practical
```

---

## 🔑 SECTION 22: GS QUICK REVISION BULLETS

```
╔═══════════════════════════════════════════════════════╗
║          DAY 27 GS — TOPPER QUICK REVISION            ║
╠═══════════════════════════════════════════════════════╣
║ 1. Yeast: Unicellular FUNGUS, reproduces by BUDDING  ║
║ 2. Ginger: RHIZOME (modified stem), NOT a root       ║
║ 3. Fungi cell wall: CHITIN (not cellulose)           ║
║ 4. Lichen = Fungus + Algae (symbiosis)               ║
║ 5. Penicillin source: Penicillium (discovered 1928)  ║
║ 6. Bacteria: PROKARYOTE, binary fission              ║
║ 7. Rhizobium: Nitrogen fixation in legume roots      ║
║ 8. Ethylene = only GASEOUS plant hormone             ║
║ 9. Abscisic Acid = stress hormone, closes stomata    ║
║ 10. Gibberellin = breaks seed dormancy               ║
║ 11. Auxin = cell elongation, phototropism            ║
║ 12. 10% energy law = Lindemann's law                ║
║ 13. Agar = from Red algae                            ║
║ 14. Anabaena in Azolla = nitrogen-fixing rice biofert║
║ 15. Decomposers = Fungi + Bacteria                   ║
╚═══════════════════════════════════════════════════════╝
```

---

# ═══════════════════════════════════════════════════
# PRACTICE QUESTIONS — DAY 27
# ═══════════════════════════════════════════════════

> ⚠️ **STRICT RULE:**
> Attempt ALL 50 questions BEFORE looking at the answers.
> Answers are ONLY at the very end of this document.
> Cover the answer section while practising!

---

## 📘 SECTION I: COMPUTER SCIENCE QUESTIONS (Q1–Q25)
### Topic: Graph Theory — BFS, DFS, Representations, Applications

---

**Q1.** Which data structure does BFS (Breadth First Search) use internally for traversal?

(A) Stack
(B) Array
(C) Queue
(D) More than one of the above (Queue and Stack both used)
(E) None of the above

---

**Q2.** Which data structure does DFS (Depth First Search) use internally for traversal?

(A) Queue
(B) Priority Queue
(C) Stack (or Recursion — call stack)
(D) More than one of the above
(E) None of the above

---

**Q3.** Consider the following statements about BFS:

(i) BFS finds the shortest path in an UNWEIGHTED graph
(ii) BFS uses QUEUE data structure
(iii) BFS explores nodes level by level

Which statements are CORRECT?

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q4.** Which of the following is/are GRAPH TRAVERSAL methods?

(A) Greedy Algorithm
(B) Dynamic Programming
(C) Divide and Conquer
(D) More than one of the above (BFS and DFS)
(E) BFS and DFS — these are the traversal methods

---

**Q5.** The space complexity of storing a graph using an ADJACENCY MATRIX for V vertices is:

(A) O(V)
(B) O(V + E)
(C) O(V²)
(D) More than one of the above
(E) None of the above

---

**Q6.** The space complexity of storing a graph using an ADJACENCY LIST for V vertices and E edges is:

(A) O(V²)
(B) O(V × E)
(C) O(V + E)
(D) More than one of the above
(E) None of the above

---

**Q7.** In a directed graph, vertex A has edges: A→B, A→C, D→A. What is the IN-DEGREE and OUT-DEGREE of vertex A?

(A) In-degree = 2, Out-degree = 1
(B) In-degree = 1, Out-degree = 2
(C) In-degree = 2, Out-degree = 2
(D) More than one of the above
(E) None of the above

---

**Q8.** Topological sorting is applicable ONLY to which type of graph?

(A) Undirected Connected Graph
(B) Complete Graph
(C) Directed Acyclic Graph (DAG)
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following correctly describes an Adjacency Matrix representation?

(A) matrix[i][j] = 1 if edge exists between i and j, else 0
(B) It takes O(1) time to check if an edge between two vertices exists
(C) For undirected graphs, the matrix is symmetric
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q10.** Dijkstra's algorithm finds the shortest path in a weighted graph. However, it FAILS when:

(A) The graph has many vertices
(B) The graph has negative edge weights
(C) The graph is undirected
(D) More than one of the above
(E) None of the above

---

**Q11.** The time complexity of BFS and DFS on a graph with V vertices and E edges is:

(A) O(V²)
(B) O(V × E)
(C) O(V + E)
(D) More than one of the above (it varies)
(E) None of the above

---

**Q12.** Which algorithm should be used to find the SHORTEST PATH when edge weights can be NEGATIVE?

(A) Dijkstra's Algorithm
(B) Prim's Algorithm
(C) Bellman-Ford Algorithm
(D) More than one of the above
(E) Kruskal's Algorithm

---

**Q13.** In which application is BFS specifically better than DFS?

(A) Cycle detection
(B) Topological sorting
(C) Finding shortest path in unweighted graph
(D) More than one of the above (BFS is better for all these)
(E) Detecting strongly connected components

---

**Q14.** Consider a graph with 6 vertices (A,B,C,D,E,F). Starting BFS from A with adjacency: A:[B,C], B:[D,E], C:[F]. What is the BFS traversal order?

(A) A→B→D→E→C→F
(B) A→B→C→D→E→F
(C) A→C→F→B→D→E
(D) More than one of the above (multiple valid orders)
(E) None of the above

---

**Q15.** Which of the following is TRUE about a BIPARTITE GRAPH?

(A) It contains no odd-length cycles
(B) Its vertices can be divided into two disjoint sets
(C) It can always be 2-coloured (coloured with 2 colours such that no two adjacent vertices share same colour)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q16.** In DFS, the order vertices are FINISHED (all neighbours explored) gives which result if reversed?

(A) BFS order
(B) Level-order traversal
(C) Topological sort order (for a DAG)
(D) More than one of the above
(E) None of the above

---

**Q17.** Which algorithm paradigm does Kruskal's MST algorithm follow?

(A) Dynamic Programming
(B) Divide and Conquer
(C) Greedy
(D) More than one of the above
(E) Backtracking

---

**Q18.** An Eulerian Circuit exists in an undirected graph if and only if:

(A) Every vertex has an even degree AND the graph is connected
(B) Every vertex has an odd degree
(C) The graph has no cycles
(D) More than one of the above
(E) None of the above

---

**Q19.** In adjacency list representation, finding all NEIGHBOURS of a vertex v takes time proportional to:

(A) O(V) in all cases
(B) O(E) in all cases
(C) O(degree of v)
(D) More than one of the above
(E) O(1) always

---

**Q20.** Floyd-Warshall algorithm is used for:

(A) Finding shortest path from single source
(B) Finding minimum spanning tree
(C) Finding shortest paths between ALL pairs of vertices
(D) More than one of the above
(E) Finding topological order

---

**Q21.** In a connected undirected graph with V vertices and E edges, which of the following statements is/are TRUE?

(i) E ≥ V - 1 (must have at least V-1 edges to be connected)
(ii) If E = V - 1, it is a TREE
(iii) E can be at most V(V-1)/2

(A) Only (i)
(B) Only (i) and (iii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q22.** For a complete graph K5 (5 vertices, all pairs connected), how many edges does it have?

(A) 5
(B) 8
(C) 10
(D) More than one of the above
(E) 20

---

**Q23.** DFS is used internally in which of the following algorithms?

(A) Topological Sort (Kahn's method)
(B) Prim's MST
(C) Kosaraju's Strongly Connected Components algorithm
(D) More than one of the above
(E) None of the above

---

**Q24.** A graph in which every pair of distinct vertices is connected by a unique EDGE is called:

(A) Bipartite Graph
(B) Sparse Graph
(C) Complete Graph
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following statements about graph representations is/are CORRECT?

(i) Adjacency Matrix is better for DENSE graphs
(ii) Adjacency List is better for SPARSE graphs
(iii) Adjacency Matrix allows O(1) edge existence check

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (i) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

## 🌿 SECTION II: GENERAL SCIENCE (BIOLOGY) QUESTIONS (Q26–Q50)
### Topic: Fungi, Yeast, Ginger, Plant Kingdom, Algae, Bacteria, Plant Hormones, Ecology

---

**Q26.** Yeast is classified under which Kingdom?

(A) Plantae
(B) Protista
(C) Monera
(D) More than one of the above
(E) Fungi

---

**Q27.** Yeast reproduces by which method?

(A) Binary Fission
(B) Fragmentation
(C) Budding
(D) More than one of the above (budding and binary fission both)
(E) Spore formation

---

**Q28.** What is the underground part of GINGER that we commonly use called?

(A) Taproot
(B) Tuber
(C) Rhizome (modified stem)
(D) More than one of the above
(E) Corm

---

**Q29.** The key difference proving that GINGER's underground part is a STEM (not a root) is:

(A) It stores water
(B) It grows underground
(C) It has NODES and INTERNODES (and scale leaves)
(D) More than one of the above
(E) It is edible

---

**Q30.** Which antibiotic was derived from the fungus Penicillium, and who discovered it?

(A) Streptomycin — discovered by Selman Waksman (1943)
(B) Penicillin — discovered by Alexander Fleming (1928)
(C) Tetracycline — discovered by Benjamin Duggar (1945)
(D) More than one of the above
(E) None of the above

---

**Q31.** LICHEN is a symbiotic association between which two organisms?

(A) Algae and Bacteria
(B) Fungi and Bacteria
(C) Fungi and Algae
(D) More than one of the above
(E) Plants and Fungi

---

**Q32.** The cell wall of FUNGI is made of:

(A) Cellulose (like plants)
(B) Chitin
(C) Peptidoglycan (like bacteria)
(D) More than one of the above
(E) None of the above

---

**Q33.** Which of the following BACTERIA is responsible for NITROGEN FIXATION in the ROOT NODULES of leguminous plants (like pea, bean, soybean)?

(A) Lactobacillus
(B) E. coli (Escherichia coli)
(C) Rhizobium
(D) More than one of the above
(E) None of the above

---

**Q34.** Blue-Green Algae (Cyanobacteria) belong to which Kingdom?

(A) Plantae
(B) Protista
(C) Monera (Prokaryotes)
(D) More than one of the above
(E) Fungi

---

**Q35.** AGAR, used as a culture medium in laboratories, is obtained from:

(A) Green Algae
(B) Brown Algae
(C) Red Algae
(D) More than one of the above
(E) Blue-green Algae

---

**Q36.** Which plant hormone is responsible for RIPENING OF FRUITS and is the ONLY GASEOUS hormone?

(A) Auxin
(B) Gibberellin
(C) Cytokinin
(D) More than one of the above
(E) Ethylene

---

**Q37.** Abscisic Acid (ABA) is called the "STRESS HORMONE" because:

(A) It promotes fruit ripening under stress
(B) It closes the STOMATA during drought/water stress, and promotes seed dormancy
(C) It causes cell division under stress
(D) More than one of the above
(E) None of the above

---

**Q38.** GIBBERELLIN plant hormone primarily:

(A) Promotes closure of stomata
(B) Causes leaf fall and fruit drop
(C) Breaks seed dormancy and promotes stem elongation
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following statements about PHOTOSYNTHESIS is/are CORRECT?

(i) It occurs in CHLOROPLASTS
(ii) OXYGEN is released during the LIGHT REACTIONS (from splitting of water)
(iii) GLUCOSE is produced in the DARK REACTIONS (Calvin Cycle)

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q40.** According to LINDEMANN'S 10% ENERGY RULE, if grass has 10,000 kcal of energy, how much energy is available to a FROG that feeds on grasshoppers (which feed on grass)?

(A) 1000 kcal
(B) 100 kcal
(C) 10 kcal
(D) More than one of the above
(E) None of the above

---

**Q41.** The scientific name of TURMERIC is:

(A) Zingiber officinale
(B) Ocimum sanctum
(C) Curcuma longa
(D) More than one of the above
(E) Azadirachta indica

---

**Q42.** Bacteria reproduce primarily by:

(A) Budding
(B) Binary Fission
(C) Spore formation
(D) More than one of the above (binary fission and spore formation)
(E) Fragmentation

---

**Q43.** Which of the following pairs is CORRECT regarding plant reproduction by modified stems?

(A) Potato → Rhizome
(B) Ginger → Tuber
(C) Onion → Bulb (modified stem with fleshy leaves)
(D) More than one of the above
(E) None of the above

---

**Q44.** SPIRULINA is:

(A) A type of algae used as a protein-rich food supplement
(B) A fungus used to make penicillin
(C) A bacterium used in nitrogen fixation
(D) More than one of the above
(E) None of the above

---

**Q45.** ANABAENA found in AZOLLA (a water fern) is important in rice farming because:

(A) It produces pesticides
(B) It fixes atmospheric NITROGEN → acts as biofertilizer for rice
(C) It prevents fungal diseases in rice
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following is TRUE about FUNGI?

(i) Fungi are heterotrophs — they cannot make their own food
(ii) Fungi body is made of thread-like HYPHAE; network called MYCELIUM
(iii) Some fungi (like Lichen) live in symbiosis with algae

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q47.** Gram staining divides bacteria into two groups. Gram-POSITIVE bacteria:

(A) Have thin peptidoglycan and stain pink/red
(B) Have thick peptidoglycan and stain purple
(C) Are always harmful to humans
(D) More than one of the above
(E) None of the above

---

**Q48.** The active compound GINGEROL found in Ginger is responsible for:

(A) Its yellow colour
(B) Its sweet taste
(C) Its pungent (spicy/hot) taste and smell
(D) More than one of the above
(E) None of the above

---

**Q49.** In a food chain: Grass → Grasshopper → Frog → Snake → Eagle. At which TROPHIC LEVEL does the FROG sit?

(A) First trophic level
(B) Second trophic level
(C) Third trophic level
(D) More than one of the above
(E) Fourth trophic level

---

**Q50.** Which of the following is the CORRECT scientific name / kingdom grouping?

(A) Yeast — Kingdom Plantae (unicellular plant)
(B) Mushroom — Kingdom Fungi (Agaricus bisporus)
(C) Amoeba — Kingdom Monera (prokaryote)
(D) More than one of the above
(E) All of the above are wrong

---

# ═══════════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 27
# (Open ONLY after attempting ALL 50 questions!)
# ═══════════════════════════════════════════════════

---

## COMPUTER SCIENCE ANSWERS (Q1–Q25)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q1  | **(C) Queue** | BFS uses QUEUE (FIFO) — visits level by level |
| Q2  | **(C) Stack** | DFS uses STACK (LIFO) or recursive call stack |
| Q3  | **(D) More than one** | ALL THREE statements about BFS are correct |
| Q4  | **(E)** | BFS and DFS are traversal methods. Greedy/DP/D&C are paradigms NOT traversals — classic BPSC trap! |
| Q5  | **(C) O(V²)** | Adjacency Matrix always uses V×V = V² space |
| Q6  | **(C) O(V+E)** | Adjacency List: V lists + E total entries = O(V+E) |
| Q7  | **(B)** | A has 1 edge coming IN (D→A) → In-degree=1; 2 edges going OUT (A→B, A→C) → Out-degree=2 |
| Q8  | **(C) DAG** | Topological sort ONLY works on Directed Acyclic Graphs |
| Q9  | **(D) More than one** | ALL THREE descriptions of Adjacency Matrix are correct |
| Q10 | **(B)** | Dijkstra FAILS with negative edge weights — use Bellman-Ford instead |
| Q11 | **(C) O(V+E)** | Both BFS and DFS: Time = O(V+E) for adjacency list |
| Q12 | **(C) Bellman-Ford** | Only Bellman-Ford handles negative weights |
| Q13 | **(C)** | BFS guarantees shortest path in unweighted graphs — DFS does NOT |
| Q14 | **(B) A→B→C→D→E→F** | BFS visits level by level: A(level 0), B,C(level 1), D,E,F(level 2) |
| Q15 | **(D) More than one** | ALL THREE properties of bipartite graphs are correct |
| Q16 | **(C) Topological sort** | Reverse of DFS finish times = valid topological order for DAG |
| Q17 | **(C) Greedy** | Kruskal's is a Greedy algorithm (always picks min weight edge) |
| Q18 | **(A)** | Eulerian Circuit: all even degrees AND connected — both conditions required |
| Q19 | **(C) O(degree of v)** | Adjacency list: each list has entries equal to degree of that vertex |
| Q20 | **(C)** | Floyd-Warshall = ALL pairs shortest path — O(V³) DP algorithm |
| Q21 | **(D) More than one** | ALL THREE statements about connected graphs are correct |
| Q22 | **(C) 10** | K5: n(n-1)/2 = 5×4/2 = 10 edges |
| Q23 | **(C) Kosaraju's** | Kosaraju's SCC algorithm uses DFS twice; Kahn's uses BFS/Queue |
| Q24 | **(C) Complete Graph** | Complete graph = every pair of vertices connected by unique edge |
| Q25 | **(D) More than one** | ALL THREE statements about graph representations are correct |

---

## GENERAL SCIENCE (BIOLOGY) ANSWERS (Q26–Q50)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q26 | **(E) Fungi** | Yeast = unicellular FUNGUS. NOT a plant or protist! |
| Q27 | **(C) Budding** | Yeast reproduces by BUDDING — small bud grows off parent |
| Q28 | **(C) Rhizome** | Ginger underground part = RHIZOME (modified horizontal stem) |
| Q29 | **(C)** | Nodes + internodes + scale leaves = PROOF it is a stem, not a root |
| Q30 | **(B)** | Penicillin from Penicillium, discovered by Alexander Fleming 1928 |
| Q31 | **(C) Fungi + Algae** | Lichen = Fungi (body/structure) + Algae (food via photosynthesis) |
| Q32 | **(B) Chitin** | Fungi cell wall = CHITIN. Plants = cellulose. Bacteria = peptidoglycan |
| Q33 | **(C) Rhizobium** | Rhizobium in root nodules of legumes fixes atmospheric nitrogen |
| Q34 | **(C) Monera** | Blue-green algae (Cyanobacteria) = PROKARYOTES → Kingdom Monera |
| Q35 | **(C) Red Algae** | AGAR obtained from Red Algae (Gelidium, Gracilaria) |
| Q36 | **(E) Ethylene** | Ethylene = fruit ripening + only GASEOUS plant hormone |
| Q37 | **(B)** | ABA closes stomata during drought → water conservation; promotes dormancy |
| Q38 | **(C)** | Gibberellin = breaks seed dormancy + stem elongation (OPPOSITE of ABA) |
| Q39 | **(D) More than one** | ALL THREE photosynthesis statements are correct |
| Q40 | **(B) 100 kcal** | 10,000 (grass) → 1,000 (grasshopper, 10%) → 100 (frog, 10%) |
| Q41 | **(C) Curcuma longa** | Turmeric = Curcuma longa. Ginger = Zingiber officinale |
| Q42 | **(B) Binary Fission** | Bacteria primarily reproduce by binary fission (cell splits into 2) |
| Q43 | **(C) Onion → Bulb** | Potato=tuber, Ginger=rhizome, Onion=BULB (fleshy leaf bases around stem) |
| Q44 | **(A)** | Spirulina = Blue-green alga (Cyanobacterium), protein-rich superfood |
| Q45 | **(B)** | Anabaena in Azolla fixes N₂ → biofertilizer for rice paddy fields |
| Q46 | **(D) More than one** | ALL THREE statements about Fungi are correct |
| Q47 | **(B)** | Gram POSITIVE = thick peptidoglycan = stains PURPLE. Gram Negative = pink |
| Q48 | **(C)** | Gingerol = responsible for ginger's pungent/spicy taste |
| Q49 | **(C) Third trophic level** | Grass=1st, Grasshopper=2nd, Frog=3rd, Snake=4th, Eagle=5th |
| Q50 | **(B)** | Mushroom (Agaricus bisporus) = Fungi ✓. Yeast=Fungi (not Plantae), Amoeba=Protista (not Monera) |

---

## 📊 SCORE EVALUATION

```
┌────────────────────────────────────────────┐
│  CS Score  (Q1–25):   _____ / 25           │
│  GS Score  (Q26–50):  _____ / 25           │
│  TOTAL:               _____ / 50           │
├────────────────────────────────────────────┤
│  48–50: TOPPER LEVEL 🏆                   │
│  43–47: Excellent — On Track ✅            │
│  35–42: Good — Revise Weak Areas           │
│  25–34: Re-read Concept Notes 📖           │
│  Below 25: Full re-read before next test   │
└────────────────────────────────────────────┘
```

---

## 🎯 TOPPER TIPS — DAY 27 TRAP ANALYSIS

### CS Traps Today:
```
TRAP 1 (Q4): "Which are graph TRAVERSAL methods?"
→ Greedy, DP, Divide & Conquer are PARADIGMS not traversals!
→ BFS and DFS are traversals. Don't confuse!

TRAP 2 (Q7): In-degree vs Out-degree
→ IN-degree = edges ARRIVING at vertex (arrows pointing IN)
→ OUT-degree = edges LEAVING vertex (arrows pointing OUT)
→ Draw the diagram to be sure!

TRAP 3 (Q10): Dijkstra's limitation
→ "Dijkstra works on all weighted graphs" = WRONG
→ Fails on NEGATIVE weights → Use Bellman-Ford

TRAP 4 (Q14): BFS order
→ BFS = level by level. A→(B,C)→(D,E,F)
→ Not deep first like A→B→D→E→C→F (that's DFS)
```

### GS Traps Today:
```
TRAP 1 (Q26, Q50): Yeast classification
→ "Yeast is a plant" = WRONG
→ Yeast is a FUNGUS (unicellular)

TRAP 2 (Q28, Q29): Ginger's underground part
→ "Ginger has a root underground" = WRONG
→ It is a RHIZOME (modified stem) — proved by nodes/internodes

TRAP 3 (Q34): Blue-green algae kingdom
→ "Blue-green algae belong to Plantae" = WRONG
→ They are PROKARYOTES → Kingdom MONERA

TRAP 4 (Q43): Potato vs Sweet Potato
→ Potato = TUBER (modified STEM) — eyes are nodes
→ Sweet Potato = tuberous ROOT — different!
```

### Option D Pattern (Today):
Questions where "More than one of the above" was correct: Q3, Q9, Q15, Q21, Q25, Q39, Q46

**LESSON:** When you see 3 statements (i), (ii), (iii), always evaluate ALL before choosing. BPSC frequently makes ALL three correct to trap students who stop at first correct answer.

---

## 📝 NIGHT REVISION — Write from memory (5 things):

1. BFS uses ______ | DFS uses ______
2. Topological sort works only on ______
3. Adjacency Matrix space = ______ | Adjacency List space = ______
4. Yeast belongs to Kingdom ______ | reproduces by ______
5. Ginger underground part = ______ (type: ______) | Lichen = ______ + ______

**Answers:** 1. Queue, Stack | 2. DAG | 3. O(V²), O(V+E) | 4. Fungi, Budding | 5. Rhizome (modified stem), Fungi + Algae

---

*Day 27 of 170 Complete — BPSC TRE 4.0 | Target: TOP RANK*
*CS: Graphs, BFS, DFS, Representations, Dijkstra, Topological Sort*
*GS: Fungi, Yeast, Ginger, Bacteria, Algae, Plant Hormones, Ecology*
