# 📅 BPSC TRE 4.0 — DAY 33 COMPLETE STUDY MODULE
### NP-Completeness & Algorithm Design Paradigms + Bihar GK: Industries & Economy
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): NP-Completeness, P vs NP, Algorithm Design Paradigms (Greedy, DP, D&C)
> - Afternoon (1 hr): Bihar GK — Industries, Economy, Key Products & Locations
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 NP-Completeness & Algorithm Design Paradigms — Deep Conceptual Guide

---

## 🔷 SECTION 1: Complexity Classes — The Foundation

### Real-Life Analogy — The Lock and Key Problem:

**Solving a problem (P):**
You need to OPEN a lock. With the key in hand, you try it → door opens in seconds.
This is FAST and EFFICIENT → **Polynomial time** solution.

**Verifying a solution (NP):**
Someone shows you a combination "4-7-2-9" and claims it opens the safe.
You try it → yes it opens. You VERIFIED it quickly, even if you couldn't FIND the combo yourself.

**The hard problem (NP-Complete):**
You're given a lock with 1000 digits (each 0-9) and no key.
Finding the right combination by brute force = 10^1000 tries.
But if GIVEN a solution, verifying it takes just 1 try.
**Finding is hard. Verifying is easy.**

---

### What is a Problem's "Complexity"?

```
In computer science, we ask:
"How does the TIME required to solve this problem GROW with input size n?"

POLYNOMIAL TIME (tractable/feasible problems):
  Time grows as n^k for some constant k
  Examples: n, n², n³, n^100 — all polynomial
  These are PRACTICALLY SOLVABLE for large n (at some k)
  
EXPONENTIAL TIME (intractable problems):
  Time grows as 2^n, n!, 10^n, etc.
  For n=100: 2^100 ≈ 10^30 operations → IMPOSSIBLE even on fastest computers
  These grow so fast they become UNSOLVABLE in reasonable time
```

---

## 🔷 SECTION 2: THE P CLASS — Polynomial Time

### Definition:
```
P = Class of decision problems solvable by a deterministic algorithm
    in POLYNOMIAL TIME (O(n^k) for some constant k)

"P" stands for POLYNOMIAL

A problem is in P if there EXISTS an efficient algorithm to SOLVE it.

DECISION PROBLEM: Has a YES/NO answer
  "Is there a path from A to B in this graph?" → YES or NO
  "Is this number prime?" → YES or NO
  "Is this array sorted?" → YES or NO
```

### Examples of Problems in P (Solvable in Polynomial Time):
```
PROBLEM                           | ALGORITHM          | COMPLEXITY
----------------------------------|--------------------|-----------
Sorting an array                  | Merge Sort         | O(n log n)
Finding shortest path (graph)     | Dijkstra's algo    | O(n² or n log n)
Searching a sorted array          | Binary Search      | O(log n)
Matrix multiplication             | Standard algorithm | O(n³)
Determining if number is prime    | Miller-Rabin test  | O(k log²n)
Finding maximum subarray sum      | Kadane's algorithm | O(n)
Linear programming                | Simplex method     | Polynomial avg
Minimum spanning tree             | Kruskal/Prim       | O(n log n)
Network flow (max flow)           | Ford-Fulkerson     | Polynomial
```

### Key Insight:
```
P problems are those that can be SOLVED EFFICIENTLY.
"Efficiently" in CS = polynomial time = practical for large inputs.

P is the "EASY" class — problems we know how to solve quickly.
```

---

## 🔷 SECTION 3: THE NP CLASS — Non-deterministic Polynomial Time

### Definition:
```
NP = Class of decision problems where a proposed solution can be
     VERIFIED in POLYNOMIAL TIME by a deterministic algorithm.

"NP" stands for Non-deterministic Polynomial time
(NOT "Non-Polynomial"! This is the #1 misconception!)

A problem is in NP if:
  → Given a CANDIDATE SOLUTION (called a "certificate")
  → We can VERIFY whether it is correct in polynomial time
```

### The Crucial Distinction:
```
P:   Problems we can SOLVE in polynomial time
NP:  Problems we can VERIFY a given solution in polynomial time

SOLVING   ≠   VERIFYING

Example — Jigsaw Puzzle:
  SOLVING: Starting from scratch, find how to assemble 1000 pieces → HARD
  VERIFYING: Given a completed puzzle, check if all pieces fit → EASY (just check each piece)

Example — Sudoku:
  SOLVING: Fill a 9×9 Sudoku grid (hard, tries many combinations)
  VERIFYING: Given a completed Sudoku, check if valid → Easy (scan rows, cols, boxes)
```

### Key Relationships:
```
FUNDAMENTAL RELATIONSHIP:
  Every problem in P is ALSO in NP
  Because: If you can SOLVE a problem efficiently, you can also VERIFY efficiently
            (just solve it and compare with the candidate solution!)

  P ⊆ NP   (P is a SUBSET of NP)

  ┌─────────────────────────────────────┐
  │                NP                   │
  │  ┌─────────────────────────┐        │
  │  │            P            │        │
  │  │  (solvable efficiently) │        │
  │  └─────────────────────────┘        │
  │  (verifiable efficiently,           │
  │   but may not be solvable fast)     │
  └─────────────────────────────────────┘

THE BIG OPEN QUESTION: Does P = NP?
  Most computer scientists BELIEVE P ≠ NP
  But it has NEVER been proven either way!
  This is one of the Millennium Prize Problems ($1,000,000 reward!)
```

### 🚨 PYQ TRAP #1: "NP means Not Polynomial"
> NP does NOT mean "Not Polynomial"!
> NP = Non-deterministic Polynomial time (problems VERIFIABLE in polynomial time)
> The confusion arises because NP-Hard/NP-Complete problems ARE hard to SOLVE,
> but "NP" itself refers to VERIFICATION, not difficulty of solving.
> **Exam answer: NP problems are VERIFIABLE (not necessarily solvable) in polynomial time.**

---

## 🔷 SECTION 4: NP-COMPLETE — The Hardest Problems in NP

### Definition:
```
NP-COMPLETE = Problems that are:
  (1) IN NP — their solutions can be VERIFIED in polynomial time
  (2) NP-HARD — at least as hard as EVERY problem in NP
                (every NP problem can be REDUCED to it in polynomial time)

Think of NP-Complete problems as:
  "The HARDEST problems in the NP class"
  "Universal problems — if you solve one, you solve them all!"
```

### The Magic of Reducibility:
```
REDUCTION: Problem A reduces to Problem B means:
  "If we can solve B efficiently, we can also solve A efficiently"
  
  A →(reduces to)→ B
  
  If B is easy → A is easy
  If A is hard → B must be hard too!

NP-COMPLETENESS DISCOVERY:
  1971: Stephen Cook proved SAT (Boolean Satisfiability) is NP-Complete
        (Called "Cook's Theorem" — first NP-Complete problem ever identified!)
  1972: Richard Karp showed 21 more classic problems are NP-Complete
        (All reduce to each other!)

THE KEY IMPLICATION:
  If you find a polynomial-time algorithm for ANY NP-Complete problem
  → you have proven P = NP
  → ALL NP problems become solvable in polynomial time
  → This would revolutionise computing, cryptography, and science!
```

### The Venn Diagram of Complexity Classes:
```
Current understanding (assuming P ≠ NP):

┌─────────────────────────────────────────────────────────────┐
│                      NP-HARD                                 │
│  ┌────────────────────────────────────────────────────────┐  │
│  │                       NP                               │  │
│  │   ┌──────────────────────────┐  ┌──────────────────┐  │  │
│  │   │         P                │  │   NP-Complete    │  │  │
│  │   │ (Easy: solvable fast)    │  │  (Hardest in NP) │  │  │
│  │   │ Sorting, Shortest Path,  │  │  TSP, SAT,       │  │  │
│  │   │ Matrix Mult, Searching   │  │  3-COLOR, CLIQUE │  │  │
│  │   └──────────────────────────┘  └──────────────────┘  │  │
│  │                                                         │  │
│  │ (All problems VERIFIABLE in polynomial time)            │  │
│  └────────────────────────────────────────────────────────┘  │
│  (Problems at LEAST as hard as NP-Complete;                  │
│   may not even be in NP — e.g., Halting Problem)             │
└─────────────────────────────────────────────────────────────┘

NP-Complete = (NP) ∩ (NP-Hard) = the OVERLAP region
```

---

## 🔷 SECTION 5: Classic NP-Complete Problems

### 1. SAT (Boolean Satisfiability Problem) — The FIRST NP-Complete

```
PROBLEM: Given a Boolean formula (with AND, OR, NOT operations),
         is there an assignment of TRUE/FALSE to variables that
         makes the WHOLE formula TRUE?

EXAMPLE:
  Formula: (x₁ OR x₂) AND (NOT x₁ OR x₃) AND (NOT x₂ OR NOT x₃)
  
  Try x₁=TRUE, x₂=FALSE, x₃=TRUE:
    (T OR F) AND (F OR T) AND (T OR F)
    = T AND T AND T = TRUE ✅
  
  This assignment SATISFIES the formula → YES answer.
  
  Finding this assignment for large formulas = NP-Complete
  Verifying a given assignment = O(n) = easy!

WHY IMPORTANT:
  First proven NP-Complete problem (Cook, 1971)
  Many real-world problems reduce to SAT:
    → Circuit design verification
    → AI planning
    → Software testing (finding bugs)
    → Cryptographic analysis
```

### 2. Travelling Salesman Problem (TSP) — The Famous NP-Complete

```
PROBLEM: Given n cities and distances between all pairs of cities,
         find the SHORTEST POSSIBLE TOUR that:
         → Visits EACH CITY EXACTLY ONCE
         → Returns to the STARTING CITY

EXAMPLE with 4 cities (A, B, C, D):

        A
       / \
    10/   \20
     /     \
    B───15───C
     \     /
    25\   /30
       \ /
        D

Possible tours (starting from A):
  A→B→C→D→A: 10+15+30+20 = 75
  A→B→D→C→A: 10+25+30+20 = 85
  A→C→B→D→A: 20+15+25+20 = 80
  A→C→D→B→A: 20+30+25+10 = 85
  A→D→B→C→A: 20+25+15+20 = 80
  A→D→C→B→A: 20+30+15+10 = 75 (same as first — reverse tour)

For n=4 cities: (4-1)!/2 = 3 distinct tours
For n=20 cities: 19!/2 ≈ 6 × 10^16 tours → IMPOSSIBLE by brute force!
For n=100 cities: effectively IMPOSSIBLE today

VERIFICATION (easy): Given a specific tour, calculate its total length → O(n)
FINDING (hard): Try all (n-1)!/2 possible tours → exponential!

REAL-WORLD APPLICATIONS:
  → Delivery route optimization (Amazon, FedEx, Zomato!)
  → Circuit board drilling (minimize drill movement)
  → DNA sequencing
  → Telescope pointing (minimize slewing time)

🎯 PYQ FACT: TSP is NP-Complete (NOT just "hard" — specifically NP-Complete).
              For n cities: (n-1)!/2 possible tours.
              Brute force = O(n!) — exponential, impractical for large n.
```

### 3. Knapsack Problem (0/1 Knapsack) — NP-Complete

```
PROBLEM: Given items with weights and values, and a knapsack with
         weight limit W, find the maximum value you can carry.
         Each item can be taken (1) or NOT taken (0) — no fractions.

EXAMPLE:
  Items: {(weight=2, value=3), (weight=3, value=4), (weight=4, value=5), (weight=5, value=6)}
  W = 5 (maximum weight limit)
  
  Option 1: Items 1+2 = weight 5, value 7 ✅
  Option 2: Items 1+3 = weight 6 > 5 ❌
  Option 3: Item 4 alone = weight 5, value 6
  Best: Option 1 → value = 7

For n items: 2^n possible subsets to try → NP-Complete (decision version)
With DP: O(nW) solution — PSEUDO-polynomial (polynomial in W, but W can be exponential in bits)

🎯 PYQ NOTE: 0/1 Knapsack is NP-Complete. Fractional Knapsack is NOT (solvable by Greedy in O(n log n)).
```

### 4. Graph Coloring — NP-Complete

```
PROBLEM (k-coloring): Can we color a graph's vertices using k colors
                       such that no two adjacent vertices share the same color?

For k=2: EASY (O(n+m)) — just check if graph is bipartite!
For k=3: NP-COMPLETE!

REAL APPLICATION:
  Map coloring (no two adjacent countries same color)
  Register allocation in compilers
  Exam scheduling (no student has two exams at same time)
```

### 5. Clique Problem — NP-Complete

```
PROBLEM: Does a graph contain a CLIQUE of size k?
         (A clique = subset of vertices where every pair is connected)

Example: In a social network, does any group of k people all know each other?
Finding such a group in a large graph = NP-Complete
Verifying a given group is a clique = O(k²) = polynomial = easy
```

---

## 🔷 SECTION 6: NP-HARD — Beyond NP

```
NP-HARD = Problems that are AT LEAST AS HARD as NP-Complete problems
          BUT may NOT be in NP themselves (solution may not be verifiable in poly time)

NP-Hard problems include:
  → All NP-Complete problems (NP-Complete ⊆ NP-Hard)
  → Plus problems HARDER than NP-Complete

HALTING PROBLEM:
  Given a program and input, will the program eventually STOP (halt)?
  This is NP-Hard (actually UNDECIDABLE — no algorithm can solve it!)
  → Proven by Alan Turing (1936) — Turing's famous Undecidability result.

TSP OPTIMIZATION:
  "Find the SHORTEST tour" (not just "is there a tour shorter than k?")
  The OPTIMIZATION version of TSP is NP-Hard (but technically not NP, because
  the solution — a specific tour length — is hard to bound)

NP-HARD vs NP-COMPLETE:
  Every NP-Complete problem is NP-Hard.
  NOT every NP-Hard problem is NP-Complete.
  NP-Complete = NP-Hard ∩ NP  (must be BOTH NP-Hard AND IN NP)
```

### Quick Classification Summary:
```
PROBLEM                          | CLASS      | WHY
---------------------------------|------------|-----------------------------
Shortest Path (Dijkstra)         | P          | O(n²) algorithm exists
Sorting                          | P          | O(n log n) exists
Binary Search                    | P          | O(log n) exists
Boolean SAT                      | NP-Complete| Cook's theorem (1971)
Travelling Salesman (decision)   | NP-Complete| Reduces from Hamiltonian path
0/1 Knapsack (decision)          | NP-Complete| Classic NP-C problem
Graph 3-Coloring                 | NP-Complete| Reduces from SAT
Clique                           | NP-Complete| Classic NP-C problem
Halting Problem                  | NP-Hard    | UNDECIDABLE — no algorithm!
TSP (optimization, no bound)     | NP-Hard    | Harder than NP-Complete TSP
```

### 🚨 PYQ TRAP #2: Shortest Path is NOT NP-Complete!
> Shortest path problems (finding minimum distance between two nodes) are in **class P**.
> Dijkstra's algorithm solves it in O(n²) or O(n log n).
> LONGEST PATH problem IS NP-Complete (finding the longest simple path).
> **Exam trap**: Don't confuse SHORTEST PATH (easy, P) with LONGEST PATH or TSP (hard, NP-C).

---

## 🔷 SECTION 7: ALGORITHM DESIGN PARADIGMS

### The Three Major Paradigms:

```
Three fundamental strategies for solving problems:

1. GREEDY: Make the LOCALLY BEST choice at each step
           Hope that local optima → global optimum
           FAST but not always OPTIMAL

2. DYNAMIC PROGRAMMING (DP): Break into overlapping subproblems
                              Solve each subproblem ONCE, store results
                              OPTIMAL but may use more memory

3. DIVIDE & CONQUER (D&C): Break into INDEPENDENT subproblems
                            Solve recursively, COMBINE results
                            No reuse of subproblem solutions
```

---

### ✅ PARADIGM 1: GREEDY ALGORITHM

### Concept:
```
At each step, make the choice that looks BEST RIGHT NOW
without reconsidering previous choices.

The greedy algorithm is like a person who:
  → Always takes the BIGGEST piece of cake at a party
  → Never trades back or reconsiders
  → Hopes this leads to eating the most total cake

This works WONDERFULLY for some problems.
It FAILS miserably for others (TSP, Knapsack 0/1, etc.)
```

### Real-Life Analogy — The Change-Giving Problem:
```
Give ₹93 change using fewest coins: ₹50, ₹20, ₹10, ₹5, ₹2, ₹1

GREEDY APPROACH:
  Step 1: Biggest coin ≤ 93 is ₹50 → TAKE ₹50 → Remaining: ₹43
  Step 2: Biggest coin ≤ 43 is ₹20 → TAKE ₹20 → Remaining: ₹23
  Step 3: Biggest coin ≤ 23 is ₹20 → TAKE ₹20 → Remaining: ₹3
  Step 4: Biggest coin ≤ 3 is ₹2   → TAKE ₹2  → Remaining: ₹1
  Step 5: Biggest coin ≤ 1 is ₹1   → TAKE ₹1  → Remaining: ₹0

  Result: 50+20+20+2+1 = ₹93 using 5 coins ✅

GREEDY WORKS HERE because Indian coin system is "canonical"
(each coin is a multiple or factor of others in a nice way)

GREEDY FAILS for unusual coin systems:
  Coins: {1, 3, 4}. Make change for 6.
  Greedy: 4+1+1 = 3 coins
  Optimal: 3+3 = 2 coins ← Greedy gives WRONG answer!
```

### Examples Where Greedy Works:
```
FRACTIONAL KNAPSACK:
  Problem: Maximize value; can take fractions of items
  Greedy: Sort by value/weight ratio; take highest ratio first
  → OPTIMAL! (greedy works because fractions allowed)
  Time: O(n log n) for sorting

ACTIVITY SELECTION:
  Problem: Select maximum non-overlapping activities
  Greedy: Always pick activity that ends EARLIEST
  → OPTIMAL!

HUFFMAN CODING:
  Problem: Assign variable-length codes to minimize total code length
  Greedy: Always merge two lowest-frequency nodes
  → OPTIMAL!

MINIMUM SPANNING TREE:
  Prim's Algorithm: Greedy — always add cheapest edge connecting tree to new vertex → OPTIMAL
  Kruskal's Algorithm: Greedy — always add cheapest edge not creating cycle → OPTIMAL

DIJKSTRA'S SHORTEST PATH:
  Greedy: Always explore closest unvisited vertex → OPTIMAL for non-negative edges
```

### When Greedy FAILS:
```
0/1 KNAPSACK:
  Can't take fractions → greedy (highest ratio) doesn't guarantee optimal
  Counterexample:
    Capacity=10, Items: (w=6,v=10), (w=5,v=7), (w=5,v=7)
    Greedy by value/weight: 10/6=1.67, 7/5=1.4
    Takes item 1 (w=6,v=10), can't fit both item 2&3 (w=10 total)
    Greedy: v=10
    Optimal: items 2+3 → v=14 ← much better!

SHORTEST PATH with negative edges: Dijkstra (greedy) fails!
TSP: Nearest-neighbor greedy gives bad tours (30-40% worse than optimal)
```

---

### ✅ PARADIGM 2: DYNAMIC PROGRAMMING (DP)

### Concept:
```
Break problem into OVERLAPPING SUBPROBLEMS.
Solve each subproblem ONCE.
Store results (MEMOIZATION) to avoid recomputation.

TWO KEY PROPERTIES required for DP:
  1. OPTIMAL SUBSTRUCTURE:
     Optimal solution of larger problem contains
     optimal solutions of smaller subproblems.
     "The best way to reach New Delhi via Patna =
      best path to Patna + best path Patna→Delhi"

  2. OVERLAPPING SUBPROBLEMS:
     Same smaller subproblems are solved MULTIPLE TIMES.
     Example: Fibonacci fib(5) = fib(4) + fib(3)
              fib(4) = fib(3) + fib(2)
              fib(3) appears TWICE → overlapping!
```

### The Classic Example — Fibonacci with DP:
```
WITHOUT DP (naive recursion):
  fib(5) = fib(4) + fib(3)
  fib(4) = fib(3) + fib(2)
  fib(3) = fib(2) + fib(1)
  ...
  fib(3) computed MULTIPLE TIMES → O(2^n) — exponential!

WITH DP (memoization):
  Store fib(i) once computed:
  fib[0] = 0
  fib[1] = 1
  fib[2] = 1
  fib[3] = 2
  fib[4] = 3
  fib[5] = 5

  Each value computed ONCE → O(n) time, O(n) space → massive improvement!

DP APPROACHES:
  TOP-DOWN (Memoization): Recursion + cache results
  BOTTOM-UP (Tabulation): Fill table iteratively from base cases up
```

### Famous DP Problems:
```
PROBLEM                    | DP APPROACH               | COMPLEXITY
---------------------------|---------------------------|-------------
Fibonacci Numbers          | Bottom-up table           | O(n)
0/1 Knapsack               | 2D table (items × weight) | O(n×W)
Longest Common Subsequence | 2D table (LCS)            | O(m×n)
Matrix Chain Multiplication| Interval DP               | O(n³)
Floyd-Warshall (all-pairs) | 3D table                  | O(n³)
Edit Distance (Levenshtein)| 2D table                  | O(m×n)
Rod Cutting Problem        | 1D table                  | O(n²)
Coin Change (minimum coins)| 1D table                  | O(amount×n)
Longest Increasing Subseq  | 1D table                  | O(n²)
```

---

### ✅ PARADIGM 3: DIVIDE & CONQUER (D&C) — Recap

```
(Covered in detail in Day 31 — brief recap)

CONCEPT: Break into INDEPENDENT subproblems (no overlap),
         solve recursively, COMBINE results.

KEY DIFFERENCE FROM DP:
  D&C: Subproblems are INDEPENDENT — no overlap
       Each subproblem solved separately, not reused
  DP:  Subproblems OVERLAP — same sub-problem appears many times
       Solutions stored and reused

EXAMPLES:
  Merge Sort: T(n) = 2T(n/2) + O(n) → O(n log n)
  Quick Sort: T(n) = 2T(n/2) + O(n) avg → O(n log n)
  Binary Search: T(n) = T(n/2) + O(1) → O(log n)
  Strassen's Matrix Mult: T(n) = 7T(n/2) + O(n²) → O(n^2.81)
```

---

## 🔷 SECTION 8: MASTER COMPARISON TABLE — All Three Paradigms

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Property        | Greedy          | Dynamic Prog.   | Divide & Conquer
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Core Idea       | Local optimum   | Overlapping     | Independent
                | at each step    | subproblems +   | subproblems;
                |                 | store results   | combine
Subproblems     | None (just one  | OVERLAPPING     | INDEPENDENT
                | greedy choice)  | (reused)        | (not reused)
Optimal always? | NOT always      | YES (if optimal | YES (if
                | (problem-depend)| substructure)   | correctly combined)
Memory          | O(1) extra      | O(n) or O(n²)   | O(log n) stack
                | (usually)       | (table storage) | (recursion)
Speed           | Fastest         | Moderate        | Moderate-fast
Reconsiders?    | NO              | YES (implicitly | NO
                |                 | via table)      |
Classic algos   | Dijkstra, Prim, | Fibonacci, 0/1  | Merge Sort,
                | Kruskal,        | Knapsack, LCS,  | Quick Sort,
                | Huffman,        | Floyd-Warshall, | Binary Search,
                | Fractional      | Edit Distance   | Strassen's
                | Knapsack        |                 |
When to use     | Greedy choice   | Problem has     | Problem splits
                | property holds  | optimal sub-    | naturally into
                | (usually proven)| structure +     | independent
                |                 | overlapping     | halves
                |                 | subproblems     |
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Decision Flowchart — Which Paradigm to Use?

```
START: Problem to solve
          |
          v
Can you make ONE greedy choice that
leads to optimal solution?
          |              |
         YES             NO
          |              |
    GREEDY algo          v
    (fast, simple)  Do subproblems OVERLAP
                    (same sub-problems repeat)?
                         |              |
                        YES             NO
                         |              |
                      DYNAMIC      DIVIDE & CONQUER
                   PROGRAMMING     (independent
                   (store and       subproblems,
                    reuse results)   recurse + combine)
```

### 🚨 PYQ TRAP #3: Greedy vs DP for Knapsack
```
FRACTIONAL KNAPSACK → GREEDY (can take fractions → sort by ratio, greedy works!)
0/1 KNAPSACK        → DYNAMIC PROGRAMMING (cannot take fractions → greedy fails!)

This is ONE OF THE MOST TESTED DISTINCTIONS in algorithm exams!
The word "0/1" means binary choice (take it all or not at all).
The word "fractional" means you can take any fraction.
```

### 🚨 PYQ TRAP #4: Dijkstra's Algorithm Classification
```
Dijkstra's Shortest Path = GREEDY algorithm
  (Always explores the nearest unvisited vertex — greedy choice)
  Works for NON-NEGATIVE edge weights
  FAILS for negative edge weights

Bellman-Ford Shortest Path = DYNAMIC PROGRAMMING
  Works for NEGATIVE edge weights (but not negative cycles)
  Slower: O(V×E) vs Dijkstra's O(V²)

EXAM ANSWER: Dijkstra = GREEDY; Bellman-Ford = DP
```

---

# PART 2: GENERAL STUDIES
## 🏭 Bihar GK — Industries & Economy

---

## 🔷 SECTION 1: Bihar's Economic Profile

### Overview:
```
Bihar's Economy Type:    Primarily AGRARIAN (agriculture-based)
GDP Contribution:        Bihar contributes ~4% of India's GDP
Per Capita Income:       One of the LOWEST among Indian states
Population:              ~13 crore (3rd most populous state)
Literacy Rate:           ~70% (lower than national average of ~77%)
GSDP Growth:             One of the FASTEST growing state economies
                         (12-14% GSDP growth rate in recent years!)

PRIMARY SECTOR: Agriculture employs ~75% of Bihar's workforce
                Contributes ~22% of Bihar's GSDP

KEY CHALLENGE: Despite fast GSDP growth, per capita income remains low
               because population is very large and diverse development needed
```

### 🎯 PYQ FACT: Bihar is one of India's fastest-growing state economies by GSDP growth rate but has one of the lowest per capita incomes due to its large population.

---

## 🔷 SECTION 2: Agriculture — Bihar's Backbone

### Major Crops and Producing Districts:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CROP          | MAJOR DISTRICTS/REGIONS           | SEASON
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RICE (Paddy)  | Rohtas, Kaimur, Buxar,            | Kharif
              | Nalanda, Patna, Bhojpur            |
WHEAT         | Rohtas, Kaimur, Buxar, Bhojpur,   | Rabi
              | Champaran, Vaishali               |
MAIZE         | Kosi region, Madhubani, Samastipur | Kharif
SUGARCANE     | Champaran (East & West),          | Year-round
              | Muzaffarpur, Vaishali, Saran       |
POTATO        | Nalanda, Vaishali, Samastipur,    | Rabi
              | Patna                             |
ONION         | Patna, Nalanda, Vaishali           | Rabi
LITCHI        | Muzaffarpur (WORLD FAMOUS!)        | Summer
              | Sitamarhi, Vaishali, Sheohar       |
MANGO         | Darbhanga, Bhagalpur, Saharsa      | Summer
BANANA        | Vaishali, Hajipur, Muzaffarpur     | Year-round
LENTILS(Dal)  | Saran, Siwan, Gopalganj            | Rabi
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 🎯 PYQ SPECIAL: Muzaffarpur Litchi
```
MUZAFFARPUR LITCHI:
  → Muzaffarpur is WORLD FAMOUS for its SHAHI LITCHI
  → One of India's most significant litchi production centres
  → Bihar produces approximately 40% of India's total litchi production
  → GI TAG: Shahi Litchi of Muzaffarpur has Geographical Indication (GI) tag
  → Litchi exported to Middle East, Europe, UK
  → Litchi season: May-June

OTHER FAMOUS GI PRODUCTS OF BIHAR:
  → Champaran Sattu (from Champaran)
  → Katarni Rice (from Rohtas, Bhojpur area — fragrant variety)
  → Jardalu Mango (from Bhagalpur — GI tagged)
  → Magahi Paan (betel leaf from Magadh region — Nalanda, Patna)
  → Sujani Embroidery (Bhusura village, Muzaffarpur)
  → Madhubani Painting (Madhubani district — UNESCO heritage recognition)
  → Sikki Grass Craft (North Bihar)
  → Bhagalpuri Silk (Bhagalpur — detailed below)
```

---

## 🔷 SECTION 3: Key Industries in Bihar

### 1. SILK INDUSTRY — Bhagalpur (Most Important!)

```
BHAGALPUR SILK:
  City:         Bhagalpur (on banks of Ganga, Bhagalpur district)
  Nickname:     "SILK CITY" of India
  Type:         TUSSAR SILK (also called Kosa silk / wild silk)
                Made from Antheraea mylitta silkworm (feeds on Arjun/Saja trees)
  Specialty:    Natural GOLDEN/TAWNY colour — unique texture — NOT smooth like mulberry silk
  
  WHY BHAGALPUR?
  → Dense forests of Arjun and Saja trees (silkworm food source)
  → Ganga river — ideal climate and humidity for silk production
  → Centuries-old tradition of silk weaving (mentioned in Mughal records)
  → Bhagalpur weavers (mostly Ansari community) have hereditary expertise

  PRODUCTS: Sarees, kurtas, dupattas — popular across India and in export
  
  BHAGALPURI SILK CHARACTERISTICS:
  → NATURAL TEXTURE — slightly rough (unlike smooth mulberry silk)
  → EARTH TONES — golden, brown, beige (natural dye-like colours)
  → DURABLE and BREATHABLE
  → UNIQUE SHEEN — iridescent finish
  
  GI TAG: Bhagalpur Silk has GI (Geographical Indication) tag
  EXPORT: Significant export to Japan, Germany, USA, UK
  
  GOVERNMENT SUPPORT:
  → Silk City project under National Textile Policy
  → Central Silk Board has offices in Bhagalpur
  → Silk Park developed to modernise industry

🎯 PYQ MOST TESTED: Bhagalpur = "Silk City of India" = TUSSAR SILK production.
```

### 2. SUGAR INDUSTRY — Champaran & Surroundings

```
SUGARCANE & SUGAR MILLS:
  Leading Districts: East Champaran, West Champaran, Muzaffarpur,
                     Vaishali, Saran, Siwan, Gopalganj
  
  WHY CHAMPARAN?
  → Fertile Terai plains (Indo-Nepal border area)
  → High rainfall and alluvial soil ideal for sugarcane
  → This was site of CHAMPARAN SATYAGRAHA (1917) — Gandhi's first
    major agitation in India was about INDIGO/NEEL, but SUGARCANE
    is now the dominant commercial crop in same region!
  
  MAJOR SUGAR MILLS in Bihar:
  → Harinagar Sugar Mill (West Champaran)
  → Samastipur, Sugauli, Motihari sugar mills
  → Bihar State Sugar Corporation operates many units

  CHALLENGE: Many old mills have closed; Bihar no longer among
             India's top sugar producers (UP leads by far)
             Recent revival efforts under Bihar Industrial Policy

🎯 PYQ: Champaran = sugarcane → sugar mills; also site of Gandhi's first Indian satyagraha
```

### 3. JUTE INDUSTRY — Kosi & Seemanchal Region

```
JUTE PRODUCTION:
  Districts: Darbhanga, Saharsa, Supaul, Madhepura, Araria, Kishanganj
             (Kosi river basin and Seemanchal region)
  
  WHY THIS REGION?
  → High rainfall, humid climate, waterlogged soil ideal for jute
  → Kosi and other rivers provide water for jute retting (soaking)
  
  STATUS: Bihar is India's 3rd largest jute-producing state (after WB and Assam)
  PRODUCTS: Gunny bags, carpet backing, rope, jute yarn, eco-friendly bags
  
  CHALLENGE: Competition from synthetic materials; traditional jute mills declining
             "Green gold" revival as eco-friendly alternatives gain popularity
```

### 4. COAL & MINING — Gaya Region

```
COAL:
  Districts: Gaya, Aurangabad (Daudnagar) — small coal deposits
  Note: Bihar lost major coal reserves to Jharkhand when it was carved out in 2000
  
LIMESTONE & CEMENT:
  Districts: Rohtas, Kaimur (Kaimur Plateau — limestone-rich)
  Major Plant: Banjari Cement Plant (Rohtas), Dalmia Cement
  
MICA:
  Small deposits in Gaya, Nawada districts
  
GLASS SAND:
  Bhojpur district has silica sand deposits

🎯 PYQ NOTE: When Jharkhand was created in 2000, Bihar lost most of its mineral 
             wealth (coal, iron ore, mica). This is WHY Bihar's industry declined post-2000.
```

### 5. FOOD PROCESSING INDUSTRY

```
MAJOR FOOD PROCESSING CLUSTERS:

HAJIPUR (Vaishali):
  → HAJIPUR BANANA processing — Hajipur is famous for bananas!
  → Hajipur is the district HQ of Vaishali
  → APMC (Agricultural Produce Market) — major banana market
  → Food processing units for banana chips, powder

MUZAFFARPUR:
  → Litchi processing, pulp, juice units
  → Makhana (Fox nut) processing — Bihar produces ~90% of India's makhana!

MAKHANA (Fox Nuts / Lotus Seeds):
  → Bihar produces 90%+ of India's Makhana
  → Districts: Darbhanga, Madhubani, Sitamarhi, Saharsa, Supaul
  → Especially DARBHANGA = MAKHANA capital of India!
  → Makhana requires freshwater ponds/lakes → North Bihar wetlands ideal
  → GI TAG: Mithila Makhana has GI tag (2022)
  → Used in religious ceremonies, sweets, health food
  → EXPORT: Growing export market (health food trend globally)

🎯 PYQ GOLD: Bihar produces ~90% of India's Makhana. 
             Darbhanga is Makhana capital.
             Mithila Makhana has GI tag.
```

### 6. LEATHER & FOOTWEAR INDUSTRY

```
MUZAFFARPUR & HAJIPUR:
  → Small leather goods manufacturing
  → Footwear units (small scale)

PATNA:
  → Leather tanning units (historically significant)
  → Now mostly small-scale cottage industry

CHALLENGE: Competition from Agra, Kanpur (major leather hubs of UP)
```

---

## 🔷 SECTION 4: Bihar's Industrial Zones & Special Areas

```
BIADC (Bihar Industrial Area Development Corporation):
  Manages industrial estates and areas in Bihar

MAJOR INDUSTRIAL AREAS:
  → Hajipur (Vaishali): Food processing, leather, electronics
    HAJIPUR INDUSTRIAL AREA = Bihar's FIRST industrial estate!
  → Muzaffarpur: Sugar, food processing
  → Patna: Light manufacturing, printing, pharmaceuticals
  → Bhagalpur: Silk, textile
  → Biharsharif: Small industries
  → Gaya: Tourism-based economy, some food processing
  → Darbhanga: Makhana processing, jute

SPECIAL ECONOMIC FEATURES:
  → Bihta (near Patna): New industrial corridor developing
  → Rajgir: Tourism + eco-resort development
  → Bodh Gaya: Tourism industry (international Buddhist circuit)

PHULWARI SHARIF & BIHTA:
  Industrial corridors under development for electronics and light manufacturing
  Connected to Patna metropolitan area planning
```

---

## 🔷 SECTION 5: Key Economic Initiatives

```
BIHAR INDUSTRIAL INVESTMENT PROMOTION POLICY:
  Offers tax incentives, land allocation for industries
  Focus sectors: Food processing, IT, textiles, tourism

SKILL DEVELOPMENT:
  Bihar Skill Development Mission (BSDM)
  Focus on construction, hospitality, IT, healthcare

7 NISCHAY (Seven Resolves) — CM Nitish Kumar:
  Important governance + economic scheme
  Includes: Bijli Har Ghar Tak, Har Ghar Nal Ka Jal,
            Asphalted Roads, Toilet in Every House,
            Educated Youth, Empowered Youth

AGRICULTURE ROAD MAP:
  Vision documents for agricultural development
  Focus on: Horticulture, fisheries, animal husbandry

JEEVIKA (JEEViKa):
  Bihar Rural Livelihoods Promotion Society
  SHG (Self Help Group) based programme
  One of India's largest SHG programmes — ~1 crore women members!
  Model studied worldwide for poverty alleviation
```

---

## 🔷 SECTION 6: Bihar's Key GI-Tagged Products Summary

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GI-TAGGED PRODUCT       | DISTRICT/REGION     | TYPE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Bhagalpur Silk (Tussar) | Bhagalpur           | Textile
Mithila Madhubani       | Madhubani           | Art/Painting
  Painting              |                     |
Mithila Makhana         | Darbhanga, North    | Food
                        | Bihar wetlands      |
Jardalu Mango           | Bhagalpur           | Agriculture
Shahi Litchi            | Muzaffarpur         | Agriculture
Katarni Rice            | Rohtas, Bhojpur     | Agriculture
Magahi Paan (Betel leaf)| Nalanda, Patna      | Agriculture
Champaran Sattu         | Champaran           | Food
Sujani Embroidery       | Muzaffarpur region  | Craft
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🔷 SECTION 7: Key Bihar Economy Facts for MCQs

```
Agriculture sector employs: ~75% of Bihar's workforce
Makhana production share:   ~90% of India's total (Bihar dominates!)
Litchi production share:    ~40% of India's total
Silk type at Bhagalpur:     TUSSAR silk (not mulberry, not eri)
"Silk City" of India:       BHAGALPUR
"Makhana Capital":          DARBHANGA
Banana district:            HAJIPUR (Vaishali)
Litchi capital:             MUZAFFARPUR
Sugarcane belt:             Champaran region
Jute region:                Kosi basin (Darbhanga, Saharsa, Supaul)
Minerals Bihar LOST in 2000: Coal, iron ore, mica → went to JHARKHAND
Largest SHG programme:      JEEVIKA — Bihar's women SHG (~1 crore members)
First industrial estate:    Hajipur Industrial Area
Bihar GSDP growth rate:     Among India's fastest (12-14% in recent years)
Per capita income:          Among India's lowest
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: P vs NP, NP-Complete, Greedy, DP, Divide & Conquer

---

**Q1.** What does "NP" stand for in computational complexity?
(A) Non-Polynomial
(B) Not Possible
(C) Non-deterministic Polynomial time
(D) More than one of the above
(E) None of the above

---

**Q2.** A problem is in class P if:
(A) It can be VERIFIED in polynomial time
(B) It can be SOLVED in polynomial time
(C) It requires exponential time to solve
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following is the correct relationship between P and NP?
(A) P and NP are completely separate — no overlap
(B) NP is a subset of P
(C) P is a subset of NP (P ⊆ NP)
(D) More than one of the above
(E) None of the above

---

**Q4.** NP-Complete problems are defined as problems that are:
(A) In NP but NOT solvable in polynomial time
(B) In NP AND at least as hard as every other problem in NP (NP-Hard)
(C) Outside both P and NP
(D) More than one of the above
(E) None of the above

---

**Q5.** Which of the following is the FIRST problem proven to be NP-Complete?
(A) Travelling Salesman Problem (TSP)
(B) Graph Coloring
(C) Boolean Satisfiability Problem (SAT)
(D) More than one of the above
(E) None of the above

---

**Q6.** The Travelling Salesman Problem (TSP) with n cities has how many possible tours (starting and ending at same city)?
(A) n! tours
(B) n² tours
(C) (n-1)!/2 distinct tours
(D) More than one of the above
(E) None of the above

---

**Q7.** Shortest Path finding (e.g., Dijkstra's algorithm) belongs to which complexity class?
(A) NP-Complete
(B) NP-Hard but not NP-Complete
(C) P (solvable in polynomial time)
(D) More than one of the above
(E) None of the above

---

**Q8.** If someone proves P = NP, the immediate consequence would be:
(A) All NP-Complete problems become solvable in polynomial time
(B) All NP-Complete problems become harder to solve
(C) Only TSP becomes easier — other problems unaffected
(D) More than one of the above
(E) None of the above

---

**Q9.** The GREEDY algorithm paradigm is best described as:
(A) Solving problems by storing results of subproblems
(B) Dividing problems into independent halves
(C) Making the locally optimal choice at each step, hoping to find global optimum
(D) More than one of the above
(E) None of the above

---

**Q10.** The 0/1 Knapsack problem should be solved using which paradigm?
(A) Greedy (sort by value/weight ratio)
(B) Divide & Conquer
(C) Dynamic Programming
(D) More than one of the above
(E) None of the above

---

**Q11.** The FRACTIONAL Knapsack problem is best solved using:
(A) Dynamic Programming
(B) Greedy (sort by value/weight ratio and take greedily)
(C) Backtracking
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following is NOT an example of a Greedy algorithm?
(A) Dijkstra's shortest path
(B) Kruskal's minimum spanning tree
(C) Floyd-Warshall all-pairs shortest path
(D) More than one of the above
(E) None of the above

---

**Q13.** Dynamic Programming requires which TWO key properties?
(A) Greedy choice property AND optimal substructure
(B) Optimal substructure AND overlapping subproblems
(C) Independent subproblems AND greedy choice
(D) More than one of the above
(E) None of the above

---

**Q14.** The key difference between Divide & Conquer and Dynamic Programming is:
(A) D&C uses recursion; DP does not
(B) D&C subproblems are INDEPENDENT; DP subproblems OVERLAP
(C) D&C is always faster than DP
(D) More than one of the above
(E) None of the above

---

**Q15.** Naive recursive Fibonacci is O(2^n). With Dynamic Programming it becomes:
(A) O(n log n)
(B) O(n²)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q16.** Dijkstra's algorithm uses which paradigm and works correctly under which condition?
(A) DP; works for all edge weights including negative
(B) Greedy; works ONLY for non-negative edge weights
(C) D&C; works for all graphs
(D) More than one of the above
(E) None of the above

---

**Q17.** Bellman-Ford algorithm for shortest path is classified as:
(A) Greedy
(B) Dynamic Programming
(C) Divide & Conquer
(D) More than one of the above
(E) None of the above

---

**Q18.** NP-Hard problems differ from NP-Complete in that:
(A) NP-Hard problems must be in NP
(B) NP-Hard problems are at least as hard as NP-Complete but may NOT be in NP
(C) NP-Hard problems are easier than NP-Complete
(D) More than one of the above
(E) None of the above

---

**Q19.** The Halting Problem is an example of:
(A) A P problem (solvable efficiently)
(B) An NP-Complete problem
(C) An NP-Hard and UNDECIDABLE problem
(D) More than one of the above
(E) None of the above

---

**Q20.** Huffman Coding (optimal prefix-free encoding) uses which paradigm?
(A) Dynamic Programming
(B) Divide & Conquer
(C) Greedy (always merge two lowest-frequency nodes)
(D) More than one of the above
(E) None of the above

---

**Q21.** The P vs NP question (whether P equals NP) is:
(A) Proven to be true (P = NP)
(B) Proven to be false (P ≠ NP)
(C) One of the unsolved Millennium Prize Problems ($1 million reward)
(D) More than one of the above
(E) None of the above

---

**Q22.** In verification of NP problems, the candidate solution is called a:
(A) Witness or Certificate
(B) Heuristic
(C) Approximation
(D) More than one of the above
(E) None of the above

---

**Q23.** The Activity Selection Problem (maximise number of non-overlapping activities) is solved optimally by:
(A) Dynamic Programming
(B) Greedy (select activity with earliest finish time first)
(C) Divide & Conquer
(D) More than one of the above
(E) None of the above

---

**Q24.** The LONGEST PATH problem in a graph (finding the longest simple path) belongs to:
(A) P class (solvable by Dijkstra-type algorithm)
(B) Same class as Shortest Path (P)
(C) NP-Complete class (unlike Shortest Path which is in P)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which algorithm paradigm is used by the Floyd-Warshall all-pairs shortest path algorithm?
(A) Greedy
(B) Divide & Conquer
(C) Dynamic Programming
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Bihar GK: Industries, Economy, Key Products & Locations

---

**Q26.** Bhagalpur is known as the "Silk City" of India. What TYPE of silk is primarily produced there?
(A) Mulberry Silk
(B) Tussar (Kosa) Silk
(C) Eri Silk
(D) More than one of the above
(E) None of the above

---

**Q27.** Approximately what percentage of India's Makhana (Fox Nut) production comes from Bihar?
(A) About 30%
(B) About 60%
(C) About 90%
(D) More than one of the above
(E) None of the above

---

**Q28.** Which district is known as the MAKHANA capital of India?
(A) Muzaffarpur
(B) Darbhanga
(C) Samastipur
(D) More than one of the above
(E) None of the above

---

**Q29.** Muzaffarpur is world-famous for producing which fruit?
(A) Jardalu Mango
(B) Shahi Litchi
(C) Katarni Rice
(D) More than one of the above
(E) None of the above

---

**Q30.** The Champaran Satyagraha (1917), Gandhi's first major agitation in India, was related to forced cultivation of which crop?
(A) Sugarcane
(B) Cotton
(C) Indigo (Neel)
(D) More than one of the above
(E) None of the above

---

**Q31.** Bihar lost most of its mineral wealth (coal, iron ore, mica) when which new state was carved out in 2000?
(A) Uttarakhand
(B) Chhattisgarh
(C) Jharkhand
(D) More than one of the above
(E) None of the above

---

**Q32.** Which GI-tagged traditional ART FORM originates from Bihar's Mithila region?
(A) Warli Painting
(B) Madhubani (Mithila) Painting
(C) Pattachitra
(D) More than one of the above
(E) None of the above

---

**Q33.** The Jardalu Mango, famous for its distinctive flavour, is primarily associated with which district of Bihar?
(A) Muzaffarpur
(B) Patna
(C) Bhagalpur
(D) More than one of the above
(E) None of the above

---

**Q34.** Which district of Bihar is famous for BANANA cultivation and has a major banana market?
(A) Vaishali (Hajipur)
(B) Bhagalpur
(C) Rohtas
(D) More than one of the above
(E) None of the above

---

**Q35.** The jute-producing belt of Bihar is primarily concentrated in which region?
(A) Champaran and Muzaffarpur in West Bihar
(B) Kosi basin (Darbhanga, Saharsa, Supaul, Madhepura)
(C) Gaya and Nalanda in South Bihar
(D) More than one of the above
(E) None of the above

---

**Q36.** Which is Bihar's FIRST industrial estate?
(A) Bihta Industrial Area (near Patna)
(B) Muzaffarpur Industrial Area
(C) Hajipur Industrial Area (Vaishali)
(D) More than one of the above
(E) None of the above

---

**Q37.** Bihar's JEEVIKA programme is known for:
(A) Setting up large factories for heavy industry
(B) Being one of India's largest Self Help Group (SHG) programmes for women's livelihood
(C) Building industrial corridors between cities
(D) More than one of the above
(E) None of the above

---

**Q38.** Katarni Rice, known for its aroma and thin grain, is primarily grown in which districts of Bihar?
(A) East Champaran and Muzaffarpur
(B) Rohtas and Bhojpur region
(C) Darbhanga and Saharsa
(D) More than one of the above
(E) None of the above

---

**Q39.** The Mithila Makhana received its Geographical Indication (GI) tag in which year?
(A) 2019
(B) 2022
(C) 2015
(D) More than one of the above
(E) None of the above

---

**Q40.** Cement production in Bihar is primarily based in which district due to limestone availability?
(A) Bhagalpur
(B) Muzaffarpur
(C) Rohtas (Kaimur Plateau region)
(D) More than one of the above
(E) None of the above

---

**Q41.** What approximately is Bihar's share in India's total LITCHI production?
(A) About 10-15%
(B) About 25-30%
(C) About 40%
(D) More than one of the above
(E) None of the above

---

**Q42.** The Magahi Paan (betel leaf) is associated with which region of Bihar?
(A) Mithila region (North Bihar)
(B) Magadh region (Nalanda, Patna, Gaya)
(C) Bhojpur region (West Bihar)
(D) More than one of the above
(E) None of the above

---

**Q43.** Which primary sector employs approximately 75% of Bihar's workforce?
(A) Manufacturing and Industry
(B) Agriculture
(C) Services and IT
(D) More than one of the above
(E) None of the above

---

**Q44.** Bihar is one of India's fastest-growing economies by GSDP growth rate. Despite this, per capita income remains low primarily because of:
(A) Poor agricultural production
(B) Very large population making per capita calculation small despite growth
(C) Lack of natural resources
(D) More than one of the above
(E) None of the above

---

**Q45.** The Champaran district's significance in Bihar's agriculture is primarily related to:
(A) Makhana production
(B) Silk weaving
(C) Sugarcane cultivation (Terai plains)
(D) More than one of the above
(E) None of the above

---

**Q46.** Silkworms used for Bhagalpur's Tussar silk production feed on which trees?
(A) Mulberry trees (Shehtu)
(B) Arjun and Saja trees (forest trees)
(C) Castor and Eri trees
(D) More than one of the above
(E) None of the above

---

**Q47.** The famous SUJANI embroidery craft of Bihar is associated with which area?
(A) Bhagalpur
(B) Muzaffarpur region (Bhusura village)
(C) Patna Sahib
(D) More than one of the above
(E) None of the above

---

**Q48.** Bihar's famous Sattu (roasted gram flour) is especially associated with which district?
(A) Rohtas
(B) Nalanda
(C) Champaran (GI-tagged Champaran Sattu)
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following statements about Bihar's economy is CORRECT?
(A) Bihar is India's highest per capita income state
(B) Bihar's GSDP growth rate is among India's highest, but per capita income is among the lowest
(C) Bihar's economy is primarily industry-based rather than agriculture-based
(D) More than one of the above
(E) None of the above

---

**Q50.** The BODH GAYA and RAJGIR areas of Bihar are primarily important for which type of economic activity?
(A) Heavy industry and mining
(B) Silk and textile production
(C) Tourism (Buddhist and heritage tourism)
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
| 1 | (C) | NP = Non-deterministic Polynomial time (NOT "Not Polynomial") |
| 2 | (B) | P = solvable in polynomial time; NP = verifiable in polynomial time |
| 3 | (C) | P ⊆ NP: every P problem is also in NP (can verify by solving) |
| 4 | (B) | NP-Complete = In NP + NP-Hard (every NP problem reduces to it) |
| 5 | (C) | SAT (Boolean Satisfiability) — Cook's theorem, 1971 |
| 6 | (C) | (n-1)!/2 distinct tours for TSP with n cities |
| 7 | (C) | Shortest path (Dijkstra) = P; polynomial time algorithm exists |
| 8 | (A) | P=NP → ALL NP-Complete problems become polynomial → all NP solved |
| 9 | (C) | Greedy = locally optimal choice at each step |
| 10 | (C) | 0/1 Knapsack = DP (greedy fails because no fractions allowed) |
| 11 | (B) | Fractional Knapsack = Greedy (sort by value/weight ratio) |
| 12 | (C) | Floyd-Warshall = DP (not Greedy; Dijkstra and Kruskal ARE greedy) |
| 13 | (B) | DP requires: optimal substructure + overlapping subproblems |
| 14 | (B) | D&C = independent subproblems; DP = overlapping subproblems |
| 15 | (C) | DP Fibonacci = O(n) vs naive O(2^n) — massive improvement |
| 16 | (B) | Dijkstra = Greedy; only non-negative edge weights (negative fails!) |
| 17 | (B) | Bellman-Ford = Dynamic Programming (relaxation = DP concept) |
| 18 | (B) | NP-Hard = at least as hard as NP-C, but may NOT be in NP class |
| 19 | (C) | Halting Problem = NP-Hard AND Undecidable (no algorithm can solve!) |
| 20 | (C) | Huffman Coding = Greedy (merge two lowest-frequency nodes always) |
| 21 | (C) | P vs NP = unsolved Millennium Prize Problem ($1,000,000 reward) |
| 22 | (A) | A proposed solution in NP is called a "witness" or "certificate" |
| 23 | (B) | Activity Selection = Greedy (earliest finish time first) = optimal |
| 24 | (C) | Longest Path = NP-Complete; Shortest Path = P (key contrast!) |
| 25 | (C) | Floyd-Warshall = Dynamic Programming (builds solution via sub-paths) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Bhagalpur produces TUSSAR (Kosa/wild) silk from Antheraea mylitta worm |
| 27 | (C) | Bihar produces ~90% of India's Makhana — dominates completely |
| 28 | (B) | Darbhanga = Makhana capital; North Bihar wetlands ideal for lotus/makhana |
| 29 | (B) | Muzaffarpur = world-famous SHAHI LITCHI; GI tagged |
| 30 | (C) | Champaran Satyagraha 1917 = against INDIGO (neel) forced cultivation |
| 31 | (C) | Jharkhand carved from Bihar in 2000 — took coal, iron, mica with it |
| 32 | (B) | Madhubani (Mithila) Painting — UNESCO-recognised; GI tagged |
| 33 | (C) | Jardalu Mango = Bhagalpur district; GI tagged |
| 34 | (A) | Vaishali (Hajipur) = famous for bananas; Hajipur banana market |
| 35 | (B) | Kosi basin (Darbhanga, Saharsa, Supaul) = jute belt of Bihar |
| 36 | (C) | Hajipur Industrial Area (Vaishali) = Bihar's first industrial estate |
| 37 | (B) | JEEViKa = Bihar's massive SHG programme (~1 crore women members) |
| 38 | (B) | Katarni Rice = Rohtas and Bhojpur area; GI tagged fragrant variety |
| 39 | (B) | Mithila Makhana received GI tag in 2022 |
| 40 | (C) | Rohtas (Kaimur Plateau) = limestone → cement (Dalmia, Banjari plants) |
| 41 | (C) | Bihar ≈ 40% of India's litchi production |
| 42 | (B) | Magahi Paan = Magadh region (Nalanda, Patna, Gaya); GI tagged |
| 43 | (B) | Agriculture employs ~75% of Bihar's workforce |
| 44 | (B) | Large population base makes per capita income low despite GSDP growth |
| 45 | (C) | Champaran = Terai plains + sugarcane; also Gandhi's Satyagraha site |
| 46 | (B) | Tussar silk worms (Antheraea mylitta) feed on Arjun and Saja trees |
| 47 | (B) | Sujani embroidery = Bhusura village area, Muzaffarpur region |
| 48 | (C) | Champaran Sattu = GI tagged product from Champaran |
| 49 | (B) | Fast GSDP growth + lowest per capita income = Bihar's economic paradox |
| 50 | (C) | Bodh Gaya + Rajgir = Buddhist/Heritage TOURISM economy |

---
---

# 🔁 DAY 33 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — NP-Completeness & Algorithm Paradigms

### P vs NP vs NP-Complete (The Holy Trinity):
```
P:           SOLVABLE in polynomial time (O(n^k))
             Examples: Sorting, Shortest Path, Binary Search, Matrix Mult

NP:          VERIFIABLE in polynomial time (given solution, can check quickly)
             P ⊆ NP (every P problem is also NP)
             NP ≠ "Not Polynomial" — COMMON EXAM TRAP!

NP-Complete: IN NP + EVERY NP problem REDUCES to it
             "Hardest problems in NP"
             Examples: SAT, TSP, 0/1 Knapsack, 3-Coloring, Clique

NP-Hard:     At LEAST as hard as NP-Complete — but may NOT be IN NP
             Examples: Halting Problem (undecidable!), TSP optimization version

HIERARCHY:   P ⊆ NP ⊆ NP-Hard
             NP-Complete = NP ∩ NP-Hard
```

### Algorithm Paradigm One-Liners:
```
GREEDY:  Local best choice → (hopefully) global best
         FAST; NOT always optimal
         Works: Dijkstra, Kruskal, Prim, Huffman, Fractional Knapsack, Activity Selection
         Fails: 0/1 Knapsack, TSP (greedy gives bad tours)

DP:      Optimal substructure + Overlapping subproblems → store and reuse
         OPTIMAL; uses more memory (O(n) or O(n²) table)
         Works: Fibonacci O(n), 0/1 Knapsack O(nW), LCS, Floyd-Warshall, Edit Distance

D&C:     Independent subproblems; recurse + combine
         No reuse of subproblem results (unlike DP)
         Works: Merge Sort O(n log n), Quick Sort, Binary Search O(log n)
```

### Top 5 PYQ Traps:
```
TRAP 1: NP ≠ "Not Polynomial" → NP = Non-deterministic Polynomial (VERIFIABLE in poly time)
TRAP 2: Shortest Path = P (Dijkstra); Longest Path = NP-Complete!
TRAP 3: Fractional Knapsack → GREEDY; 0/1 Knapsack → DYNAMIC PROGRAMMING
TRAP 4: Dijkstra = GREEDY (not DP); Bellman-Ford = DP (not Greedy)
TRAP 5: P=NP? → UNSOLVED ($1M Millennium Prize); most believe P≠NP
```

---

## ⚡ RAPID FIRE — Bihar Industries & Economy

### Must-Know Location → Product Map:
```
BHAGALPUR    → TUSSAR SILK ("Silk City of India"); Jardalu Mango (GI)
MUZAFFARPUR  → SHAHI LITCHI (world-famous; GI); ~40% of India's litchi
DARBHANGA    → MAKHANA capital (~90% of India's production; GI: Mithila Makhana)
HAJIPUR      → BANANA; Bihar's FIRST Industrial Estate
CHAMPARAN    → SUGARCANE; Site of Gandhi's first Indian Satyagraha (1917, against INDIGO)
ROHTAS       → KATARNI RICE (GI); CEMENT (limestone from Kaimur Plateau)
KOSI BASIN   → JUTE production (Darbhanga, Saharsa, Supaul)
NALANDA      → MAGAHI PAAN (GI); also famous as ancient university site
MADHUBANI    → MADHUBANI PAINTING (GI; UNESCO recognition)
JHARKHAND    → Where Bihar's COAL and MINERALS went (carved out 2000)
```

### GI-Tagged Products Quick List:
```
Bhagalpuri Silk | Mithila Makhana | Shahi Litchi | Jardalu Mango |
Katarni Rice | Magahi Paan | Madhubani Painting | Champaran Sattu |
Sujani Embroidery
```

### Key Statistics:
```
Makhana: Bihar = ~90% of India → DOMINANT
Litchi: Bihar = ~40% of India → LEADING
Agriculture workforce: ~75% of Bihar's total
GSDP growth: Among India's FASTEST
Per capita income: Among India's LOWEST
JEEVIKA SHG members: ~1 crore women
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **P = solvable efficiently; NP = verifiable efficiently; NP-Complete = hardest in NP (both NP + NP-Hard); NP ≠ "Not Polynomial"** — this is the most exam-tested distinction
2. **Key NP-Complete problems**: SAT (first, 1971 Cook), TSP ((n-1)!/2 tours), 0/1 Knapsack, 3-Coloring, Clique; **NOT NP-Complete**: Shortest Path (P class!)
3. **Paradigm shortcuts**: Greedy → Dijkstra/Kruskal/Huffman/Fractional Knapsack; DP → 0/1 Knapsack/Fibonacci/Floyd-Warshall; D&C → Merge Sort/Binary Search
4. **Bhagalpur = Tussar Silk ("Silk City"); Muzaffarpur = Litchi (40% India); Darbhanga = Makhana (90% India); Hajipur = Banana; Champaran = Sugarcane + Gandhi Satyagraha**
5. **Bihar lost minerals to Jharkhand (2000); Bihar = fast GSDP growth but low per capita; JEEVIKA = ~1 crore women in SHGs; GI tags: Mithila Makhana (2022), Jardalu Mango, Bhagalpur Silk, Magahi Paan**

---

## 📅 DAY 34 PREVIEW — What's Coming Next:
**CS**: Operating Systems — Introduction, Process Management, CPU Scheduling Algorithms (FCFS, SJF, Round Robin, Priority), Process States
**GS**: Bihar GK — History of Bihar: Ancient period (Magadh Empire, Mauryas, Guptas), Medieval period, Bihar in modern history

---

*🚀 Day 33 of 170 complete — NP problems may be unsolvable in polynomial time, but your exam score certainly isn't!*
