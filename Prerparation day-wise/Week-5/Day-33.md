# 📅 DAY-33 — BPSC TRE 4.0 STUDY FILE
## CS: NP-Completeness & Algorithm Paradigms | GS: Bihar GK — Industries & Economy
### 🎯 Target: TOPPER RANK | Phase 1 → Week 5

---

> **📌 TODAY'S BATTLE PLAN**
> - **Morning (1.5 hrs):** CS — NP-Completeness, P vs NP, Algorithm Paradigms (Greedy, DP, D&C, Backtracking)
> - **Afternoon (1 hr):** GS — Bihar Economy: Agriculture, Industries, Schemes, Economic Facts
> - **Evening (1 hr):** Solve all 50 MCQs (25 CS + 25 GS) from this file
> - **Night (30 min):** Write 5-bullet summary from memory — NEVER skip this

---

# 🖥️ PART A: COMPUTER SCIENCE

## NP-Completeness & Algorithm Paradigms

---

## 🔷 SECTION 1: P vs NP — The Million Dollar Problem

### 1.1 What is a "Problem" in Computer Science?

A **computational problem** asks: given an input, produce a correct output.

**Two types we care about:**
- **Decision Problem:** Answer is YES or NO. Example: "Is there a path of length ≤ k from A to B?"
- **Optimization Problem:** Find the BEST solution. Example: "Find the shortest path from A to B."

> 💡 **Why decision problems?** Complexity theory mostly works with decision problems because YES/NO is simpler to analyze formally.

---

### 1.2 Class P (Polynomial Time)

```
P = Problems solvable in O(n^k) time for some constant k
    (Polynomial time = Efficient = Fast)
```

**Simple Rule:** If you can SOLVE it in polynomial time → it's in P.

**Examples of P Problems:**
| Problem | Algorithm | Time Complexity |
|---------|-----------|-----------------|
| Sorting | Merge Sort | O(n log n) |
| Shortest Path | Dijkstra's | O(V² or E log V) |
| Matrix Multiplication | Strassen | O(n^2.81) |
| Binary Search | Binary Search | O(log n) |
| Minimum Spanning Tree | Kruskal's/Prim's | O(E log V) |
| Maximum Flow | Ford-Fulkerson | O(VE²) |

> ⚠️ **KEY PYQ FACT:** Shortest Path = POLYNOMIAL (P class). It is NOT NP-Complete. This is a very common trap in BPSC exams!

---

### 1.3 Class NP (Non-deterministic Polynomial Time)

```
NP = Problems where a given solution (certificate) can be
     VERIFIED in polynomial time
```

**DO NOT confuse:** NP does NOT mean "Non-Polynomial" or "Not Polynomial"!

**Memory Trick:**
- P → Can be **Solved** fast
- NP → Can be **Verified** fast

**ASCII Diagram — P and NP Relationship:**

```
+----------------------------------+
|              NP                  |
|   +--------------------------+   |
|   |           P              |   |
|   |  (All P problems are     |   |
|   |   also in NP)            |   |
|   +--------------------------+   |
|                                  |
|   NP-Complete problems are at    |
|   the boundary of NP (hardest)   |
+----------------------------------+
```

**Examples of NP Problems:**
- Travelling Salesman Problem (TSP) — given a solution, verify if it's ≤ k? → YES/NO → verifiable in O(n)
- Boolean Satisfiability (SAT)
- Hamiltonian Cycle
- Graph Coloring
- Subset Sum
- Knapsack

---

### 1.4 NP-Complete (NPC)

```
A problem is NP-Complete if:
  1. It is IN NP (can be verified in polynomial time)
  2. Every other NP problem can be REDUCED to it in polynomial time
     (i.e., it is NP-Hard)
```

**Think of NP-Complete as:** The HARDEST problems inside NP. If you solve one NP-Complete problem efficiently, you solve ALL of NP!

**ASCII Diagram — Full Picture:**

```
+------------------------------------------------+
|                  NP-Hard                       |
|  +------------------------------------------+ |
|  |                  NP                       | |
|  |  +------------------------------------+  | |
|  |  |           NP-Complete              |  | |
|  |  |  (Intersection of NP and NP-Hard)  |  | |
|  |  +------------------------------------+  | |
|  |                                          | |
|  |  +--------+                              | |
|  |  |   P    |  (P ⊆ NP)                   | |
|  |  +--------+                              | |
|  +------------------------------------------+ |
+------------------------------------------------+
```

---

### 1.5 The P = NP Question

**The Famous Unsolved Problem:**
- Is P equal to NP?
- If yes → Every NP-Complete problem could be solved efficiently!
- Currently: P ≠ NP (believed but NOT proven)
- Clay Mathematics Institute has listed it as one of the **Millennium Prize Problems** (prize: $1 million)

---

### 1.6 Complete List of NP-Complete Problems (BPSC PYQ Favourites)

| Problem | Description | PYQ Relevance |
|---------|-------------|---------------|
| **Travelling Salesman Problem (TSP)** | Visit all cities exactly once, return to start, minimize distance | ⭐⭐⭐ Very High |
| **Boolean Satisfiability (SAT)** | First ever NP-Complete problem (Cook's theorem, 1971) | ⭐⭐⭐ Very High |
| **Hamiltonian Cycle** | Visit every vertex exactly once and return to start | ⭐⭐ High |
| **Graph Coloring** | Color graph using k colors, no adjacent same color | ⭐⭐ High |
| **Subset Sum** | Find a subset with sum = target | ⭐⭐ High |
| **Vertex Cover** | Find min set of vertices covering all edges | ⭐ Medium |
| **Clique Problem** | Find clique of size k | ⭐ Medium |
| **3-SAT** | 3-variable boolean satisfiability | ⭐⭐ High |

> ⚠️ **CRITICAL PYQ TRAP:** 
> - Shortest Path → **P** (Dijkstra's algorithm)  
> - Longest Path → **NP-Complete**  
> - Minimum Spanning Tree → **P** (Kruskal's, Prim's)  
> - Hamiltonian Cycle → **NP-Complete**

---

### 1.7 NP-Hard (Bonus Concept)

```
NP-Hard = At least as hard as NP-Complete
         (May not even be in NP itself)
```

**Example:** Halting Problem = NP-Hard but NOT in NP (it's undecidable — cannot be verified in polynomial time).

---

## 🔷 SECTION 2: Algorithm Paradigms — The 4 Big Strategies

### 2.1 Overview of Algorithm Design Paradigms

```
ALGORITHM PARADIGMS
├── Greedy Algorithm
├── Dynamic Programming (DP)
├── Divide and Conquer (D&C)
└── Backtracking
```

These are **methods of thinking** — not specific algorithms. A paradigm tells you HOW to approach a problem.

---

### 2.2 Greedy Algorithm

**Core Idea:** At every step, make the **locally optimal choice** hoping to reach the globally optimal solution.

```
Greedy Strategy:
  Step 1: Identify the "greedy choice" (best option at this moment)
  Step 2: Make that choice (irreversible)
  Step 3: Reduce problem to smaller subproblem
  Step 4: Repeat until done
```

**When does Greedy work?** Only when the problem has:
1. **Greedy Choice Property** — locally optimal = globally optimal
2. **Optimal Substructure** — optimal solution contains optimal sub-solutions

**Classic Greedy Problems:**

| Problem | Greedy Choice | Correct? |
|---------|--------------|----------|
| Activity Selection | Choose earliest finishing time | ✅ YES |
| Minimum Spanning Tree | Pick cheapest edge (Kruskal/Prim) | ✅ YES |
| Huffman Coding | Merge two smallest frequency nodes | ✅ YES |
| Dijkstra's Shortest Path | Pick closest unvisited vertex | ✅ YES (no negative edges) |
| Fractional Knapsack | Pick item with max value/weight ratio | ✅ YES |
| 0/1 Knapsack | Pick most valuable items first | ❌ NO (need DP) |
| TSP | Visit nearest unvisited city | ❌ NO (approximate only) |

**Memory Trick for Greedy:**
> "Greedy is SELFISH — always takes the best it can see RIGHT NOW, never looks back."

---

### 2.3 Dynamic Programming (DP)

**Core Idea:** Break the problem into **overlapping subproblems**, solve each once, store results (memoization/tabulation).

**Two Key Properties Required:**
1. **Optimal Substructure:** Optimal solution to problem = composed of optimal solutions to subproblems
2. **Overlapping Subproblems:** Same subproblems are computed multiple times (unlike D&C)

```
DP Approaches:
  1. Top-Down (Memoization): 
     - Recursion + Cache
     - Solve big problem, recursively break down
     - Store results in array/hash map
     
  2. Bottom-Up (Tabulation):  
     - Iterative
     - Solve smallest subproblems first
     - Build up to big problem
```

**ASCII Diagram — Fibonacci with DP:**
```
WITHOUT DP (Exponential):
fib(5)
├── fib(4)          ← computed TWICE
│   ├── fib(3)      ← computed THRICE
│   │   ├── fib(2)
│   │   └── fib(1)
│   └── fib(2)
└── fib(3)          ← REPEATED WORK!
    ├── fib(2)
    └── fib(1)

WITH DP (Linear):
fib(1)=1, fib(2)=1, fib(3)=2, fib(4)=3, fib(5)=5
Each value computed EXACTLY ONCE → O(n)
```

**Classic DP Problems:**

| Problem | Time Complexity | Space |
|---------|-----------------|-------|
| Fibonacci (DP) | O(n) | O(n) or O(1) |
| 0/1 Knapsack | O(n×W) | O(n×W) |
| Longest Common Subsequence (LCS) | O(m×n) | O(m×n) |
| Matrix Chain Multiplication | O(n³) | O(n²) |
| Floyd-Warshall (All-pairs shortest path) | O(V³) | O(V²) |
| Bellman-Ford | O(VE) | O(V) |
| Edit Distance | O(m×n) | O(m×n) |

> ⚠️ **PYQ KEY FACT:** 0/1 Knapsack uses DP (NOT greedy). Fractional Knapsack uses Greedy.

---

### 2.4 Divide and Conquer (D&C)

**Core Idea:** Divide the problem into **non-overlapping** subproblems, solve independently, combine results.

```
D&C Template:
  1. DIVIDE: Split problem into smaller subproblems
  2. CONQUER: Solve subproblems recursively
  3. COMBINE: Merge solutions to get final answer
```

**Key Difference from DP:**
- D&C → Subproblems are **INDEPENDENT** (no overlap)
- DP → Subproblems are **OVERLAPPING** (share computation)

**Classic D&C Algorithms:**

| Algorithm | Time Complexity | Stable? |
|-----------|-----------------|---------|
| Merge Sort | O(n log n) — always | ✅ Yes |
| Quick Sort | O(n log n) avg, O(n²) worst | ❌ No |
| Binary Search | O(log n) | — |
| Strassen's Matrix Multiplication | O(n^2.81) | — |
| Closest Pair of Points | O(n log n) | — |

> ⚠️ **PYQ KEY FACT:** Both Merge Sort AND Quick Sort are Divide & Conquer algorithms.

---

### 2.5 Backtracking

**Core Idea:** Build solution incrementally; **abandon (backtrack)** a path as soon as you detect it cannot lead to a valid solution.

```
Backtracking Template:
  1. Choose a candidate solution step
  2. Check if it satisfies constraints
  3. If YES → continue deeper
  4. If NO → BACKTRACK (undo the choice, try next)
  5. Repeat until complete solution found (or all options exhausted)
```

**ASCII Diagram — N-Queens Backtracking:**
```
         Q . . .        ← Place Queen at (0,0)
         . . Q .        ← Place Queen at (1,2)
         . . . .        ← Can't place → BACKTRACK
         . . . .
         
         ↓ Try next position...
         
         Q . . .
         . . . Q        ← Place Queen at (1,3)
         . Q . .        ← Place Queen at (2,1)
         . . . .        ← Continue...
```

**Classic Backtracking Problems:**

| Problem | Description |
|---------|-------------|
| N-Queens | Place N queens on N×N board, none attacking |
| Sudoku Solver | Fill grid satisfying constraints |
| Hamiltonian Cycle | Visit all vertices exactly once |
| Graph Coloring | Color graph with minimum colors |
| Rat in a Maze | Find path from source to destination |
| Subset Sum | Find all subsets summing to target |

> ⚠️ **PYQ KEY FACT:** Backtracking is used for NP-Complete problems (like Graph Coloring, Hamiltonian Cycle). It is a brute-force with pruning.

---

### 2.6 Comparison Table — All 4 Paradigms

| Feature | Greedy | Dynamic Programming | Divide & Conquer | Backtracking |
|---------|--------|---------------------|------------------|--------------|
| **Strategy** | Locally optimal choice | Solve + store subproblems | Split → Solve → Merge | Try all + prune |
| **Subproblems** | Sequential | Overlapping | Non-overlapping | All possibilities |
| **Guarantees optimal?** | Not always | Yes (if properties hold) | Yes | Yes (but slow) |
| **Typical complexity** | O(n log n) | O(n²) or O(n³) | O(n log n) | Exponential |
| **Key examples** | Activity Selection, Huffman, Dijkstra, MST | Knapsack, LCS, Floyd-Warshall | Merge Sort, Quick Sort, Binary Search | N-Queens, Sudoku, Hamiltonian |

---

### 2.7 Branch and Bound (Bonus — For Hard Questions)

**Used for:** NP-Hard optimization problems (TSP, 0/1 Knapsack with large n)

**Concept:**
- Like Backtracking, but uses BOUNDS to prune more aggressively
- Calculates upper/lower bound at each node
- If bound is worse than current best → prune that branch

---

## 🔷 SECTION 3: Important Algorithms & Their Paradigm Classification

| Algorithm | Paradigm | Time Complexity |
|-----------|----------|-----------------|
| Dijkstra's Shortest Path | Greedy | O(V² or E log V) |
| Prim's MST | Greedy | O(V² or E log V) |
| Kruskal's MST | Greedy | O(E log E) |
| Huffman Coding | Greedy | O(n log n) |
| Activity Selection | Greedy | O(n log n) |
| Merge Sort | D&C | O(n log n) |
| Quick Sort | D&C | O(n log n) avg |
| Binary Search | D&C | O(log n) |
| Fibonacci (DP) | DP | O(n) |
| 0/1 Knapsack | DP | O(nW) |
| LCS | DP | O(mn) |
| Floyd-Warshall | DP | O(V³) |
| Bellman-Ford | DP | O(VE) |
| Matrix Chain | DP | O(n³) |
| N-Queens | Backtracking | O(n!) |
| Sudoku | Backtracking | Exponential |
| Hamiltonian Cycle | Backtracking | O(n!) |

> 🏆 **TOPPER TIP:** In PYQs, you may be asked "Which algorithm paradigm does X use?" Learn the table above by heart.

---

## 🔷 SECTION 4: Quick Revision — NP & Complexity Key Facts

```
MUST MEMORIZE — NP FACTS:
════════════════════════════════════════════════════════
1. P ⊆ NP  (every P problem is also in NP)
2. NP-Complete = in NP AND NP-Hard
3. First NP-Complete problem = Boolean Satisfiability (SAT) — proved by Stephen Cook (1971)
4. TSP = NP-Complete
5. Shortest Path (Dijkstra's) = POLYNOMIAL (NOT NP-Complete)
6. Hamiltonian Cycle = NP-Complete | Eulerian Cycle = POLYNOMIAL
7. Graph Coloring (k≥3) = NP-Complete
8. 2-Coloring (bipartite check) = POLYNOMIAL (O(V+E) using BFS/DFS)
9. Longest Path = NP-Complete | Shortest Path = Polynomial
10. P = NP? → UNSOLVED (Millennium Prize Problem)
════════════════════════════════════════════════════════
```

---

# 🌍 PART B: GENERAL STUDIES — BIHAR GK

## Bihar Economy, Industries & Development

---

## 🔶 SECTION 1: Bihar — Economic Overview

Bihar is one of India's **most populous** and **fastest-growing** states. Understanding Bihar's economy is essential for BPSC exams as 5–8 questions directly test Bihar-specific facts.

### 1.1 Key Economic Facts — Bihar

| Indicator | Fact |
|-----------|------|
| **State GDP Rank** | Among lower-middle income states; growing rapidly post-bifurcation |
| **Capital** | Patna (also financial capital) |
| **Bifurcation** | Jharkhand carved out in **2000** (mineral-rich areas went to Jharkhand) |
| **Primary sector** | Agriculture dominates (~70% population dependent) |
| **GSDP Growth** | Among fastest-growing states in recent years (10–12% GSDP growth) |
| **Literacy Rate** | ~70% (Census 2011); improving with education schemes |
| **Per Capita Income** | One of the lowest among major states |
| **Main reason for poverty** | Loss of mineral-rich Jharkhand, flooding, lack of industries |

> ⚠️ **PYQ KEY FACT:** After Jharkhand's creation in 2000, Bihar lost its mineral wealth (coal, iron ore, bauxite). This is a frequently tested fact in BPSC.

---

## 🔶 SECTION 2: Agriculture in Bihar

Bihar's economy is fundamentally **agriculture-based**. Know these facts cold.

### 2.1 Major Crops of Bihar

| Crop | Season | Key Districts |
|------|--------|---------------|
| **Paddy (Rice)** | Kharif | North Bihar — Darbhanga, Muzaffarpur, Champaran |
| **Wheat** | Rabi | Central & South Bihar |
| **Maize** | Kharif | Kosi region — world-famous **Biharsharif Maize** |
| **Sugarcane** | Kharif+Rabi | Champaran, Saran, Muzaffarpur |
| **Makhana (Fox Nut)** | — | **Darbhanga, Madhubani, Saharsa** — Bihar produces **95% of world's Makhana** |
| **Litchi** | — | **Muzaffarpur** — famous for Shahi Litchi (GI Tag) |
| **Mango** | — | Hajipur, Darbhanga (Malda variety) |
| **Potato** | Rabi | Nalanda, Patna |
| **Banana** | — | Hajipur — famous variety |

> ⭐ **SUPER IMPORTANT BPSC FACTS:**
> - Bihar produces **~95% of India's Makhana** (Fox Nut) — GI Tag given
> - **Shahi Litchi of Muzaffarpur** has GI Tag (Geographical Indication)
> - **Hajipur Banana** is famous
> - **Champaran** is known for indigo cultivation historically AND sugarcane today

### 2.2 Agricultural Zones of Bihar

```
NORTH BIHAR (Gangetic Plains):
  - High rainfall, fertile soil
  - Rice, Sugarcane, Makhana, Litchi, Jute
  - Flood-prone (Kosi, Gandak, Bagmati rivers)

SOUTH BIHAR (Plateau fringe):
  - Less rainfall, mixed crops
  - Wheat, Maize, Vegetables
  - More industrialized than North Bihar
```

### 2.3 Important Agricultural Facts

- **Bihar Agricultural University:** Sabour, Bhagalpur (established 2010)
- **ICAR Research Centre:** Patna
- **Land holdings:** Mostly small/marginal (below 2 hectares)
- **Green Revolution impact:** Wheat production increased significantly in south Bihar
- **Bihar flood:** World's most flood-affected state per area; Kosi River called "Sorrow of Bihar"

---

## 🔶 SECTION 3: Industries in Bihar

### 3.1 Pre-Bifurcation vs Post-Bifurcation Industrial Status

```
BEFORE 2000 (With Jharkhand):
  ✅ Steel industry (Bokaro, Jamshedpur)
  ✅ Coal mines (Jharia, Raniganj adjacent)
  ✅ Mineral processing
  ✅ Heavy industries

AFTER 2000 (Without Jharkhand):
  ❌ Lost all mineral-based industries
  Bihar became largely de-industrialized
  Focus shifted to: Agro-based, Small-scale, Services
```

### 3.2 Major Industries of Present-Day Bihar

| Industry | Location | Details |
|----------|----------|---------|
| **Sugar Industry** | Champaran, Saran, Muzaffarpur | Largest agro-industry in Bihar; Bihar has several large sugar mills |
| **Textile / Silk** | Bhagalpur | Famous for **Bhagalpuri Silk (Tussar Silk)** — GI Tag |
| **Leather Industry** | Muzaffarpur, Patna | Shoe manufacturing |
| **Paper Industry** | Muzaffarpur | Paper mills |
| **Cement** | Rohtas (Dalmianagar) | **Dalmia Cement** at Dalmianagar is historic |
| **Glass Industry** | Bhagalpur, Sahibganj | |
| **Jute** | North Bihar (Darbhanga, Purnea) | |
| **Makhana Processing** | Darbhanga, Madhubani | Value-added processing |
| **IT/Software** | Patna | Emerging IT sector |

> ⭐ **BPSC PYQ FAVOURITE:**
> - **Bhagalpuri Silk (Tassar/Tussar)** = most famous industry with GI Tag
> - **Dalmianagar** (Rohtas) = cement + chemical industry hub
> - **Sugar** = largest agro-based industry in Bihar

### 3.3 GI Tags of Bihar (Very Important for PYQ!)

| Product | District |
|---------|---------|
| Shahi Litchi | Muzaffarpur |
| Bhagalpuri Silk (Tassar) | Bhagalpur |
| Makhana | Darbhanga region |
| Katarni Rice | Bhagalpur, Banka |
| Jardalu Mango | Bhagalpur |
| Silao Khaja (sweet) | Nalanda |
| Bihar Madhubani Painting | Madhubani |

---

## 🔶 SECTION 4: Major Industrial Areas & BIADA

### 4.1 BIADA — Bihar Industrial Area Development Authority

- **Full form:** Bihar Industrial Area Development Authority
- **Purpose:** Develop industrial zones, attract investment
- **Major industrial areas:**
  - **Hajipur Industrial Area** (Vaishali) — largest in Bihar
  - **Muzaffarpur Industrial Area**
  - **Bihta (Patna)** — emerging hub
  - **Dalmianagar** — Rohtas (chemicals, cement)
  - **Barauni** — oil refinery + fertilizers

### 4.2 Key Industries at Specific Locations

```
BARAUNI (Begusarai):
  - Indian Oil Corporation (IOC) Refinery
  - HPCL/Barauni Refinery — one of Bihar's most important industries
  - BFCL (Barauni Fertilizer and Chemicals Ltd)
  
HAJIPUR (Vaishali):
  - EPIP (Export Promotion Industrial Park)
  - Hajipur Industrial Area
  - Food processing industries
  
PATNA:
  - Capital city, service sector
  - Leather, Printing, Glass
  
DALMIANAGAR (Rohtas):
  - Dalmia Cement
  - Chemical industries
```

> ⭐ **SUPER IMPORTANT:** **Barauni Oil Refinery (IOC)** = most important heavy industry in Bihar. It was established in **1964** as Indo-Soviet collaboration!

---

## 🔶 SECTION 5: Bihar Government Schemes & Economic Development

### 5.1 Seven Nishchay (Saat Nishchay) — Flagship Programme

Bihar government launched **7 Nishchay (Resolutions)** for development:

| Nishchay | Focus |
|----------|-------|
| Aarthik Hal, Yuvaon ko Bal | Unemployment allowance to youth |
| Aarakshit Rozgar, Mahilaon ka Adhikar | 35% reservation for women in government jobs |
| Har Ghar Bijli (Lagatar) | Electricity to every household |
| Har Ghar Nal Ka Jal | Piped water to every house |
| Ghar Tak Pakki Gali-Naali | Paved roads to every house |
| Shauchalay Nirman, Ghar ka Samman | Toilet construction |
| Avsar Badhe, Aage Padhe | Higher education opportunities |

### 5.2 Important Bihar-specific Economic Schemes

| Scheme | Purpose |
|--------|---------|
| **Mukhyamantri Udyami Yojana** | ₹10 lakh loan to SC/ST/women entrepreneurs (50% grant, 50% loan) |
| **Bihar Startup Policy** | Promote startups in Bihar |
| **Jivikas (Bihar Rural Livelihoods Project)** | Women's SHG-based poverty reduction — highly successful |
| **BRLPS** | Bihar Rural Livelihoods Promotion Society |
| **Har Khet Sinchai** | Irrigation to every farm |
| **PMGSY** | Pradhan Mantri Gram Sadak Yojana — rural roads |

> ⭐ **PYQ KEY:** **Jeevika (BRLPS)** — Bihar's flagship rural livelihood programme through Self Help Groups — often asked in BPSC!

---

## 🔶 SECTION 6: Transport Infrastructure in Bihar

| Type | Key Facts |
|------|----------|
| **Railways** | East Central Railway HQ at **Hajipur** |
| **Airports** | Patna Airport (Jay Prakash Narayan International), Gaya Airport (international — Buddhist Circuit), Darbhanga Airport (recently upgraded) |
| **Highways** | NH-19 (Grand Trunk Road passes through Bihar), NH-31 (Patna-Kolkata direction) |
| **Bridges** | Mahatma Gandhi Setu (Patna) over Ganga — one of Asia's longest road bridges; Vikramshila Setu (Bhagalpur) |
| **Rivers** | Ganga (main), Gandak, Kosi, Bagmati, Son, Punpun, Budhi Gandak |

> ⭐ **PYQ FACT:** 
> - East Central Railway HQ = **Hajipur** (Vaishali)
> - Mahatma Gandhi Setu = 5.575 km — one of India's longest river bridges
> - Gaya airport serves Buddhist pilgrims (Bodhgaya nearby)

---

## 🔶 SECTION 7: Bihar — Important Economic Statistics

| Parameter | Detail |
|-----------|--------|
| **State Animal** | Gaur (Indian Bison) |
| **State Bird** | House Sparrow (Gauraya) |
| **State Tree** | Peepal (Sacred Fig) |
| **State Flower** | Kachnar (Bauhinia variegata) |
| **GSDP** | Growing at ~10–11% per year (one of highest in India) |
| **Highest literacy district** | Rohtas |
| **Lowest literacy district** | Purnia/Kishanganj |
| **Most populous district** | Patna |
| **Largest district by area** | West Champaran |
| **Highest population density** | Sheohar |
| **Ganga length in Bihar** | ~445 km |
| **Total districts** | 38 districts |
| **Total divisions** | 9 divisions |

---

## 🔶 SECTION 8: Mining and Natural Resources of Bihar

> **Post-Jharkhand bifurcation context is essential here!**

**Bihar now has very limited minerals compared to pre-2000:**

| Mineral/Resource | Location in Bihar |
|-----------------|------------------|
| **Pyrite** | Rohtas (Amjhore — largest pyrite deposit in Asia!) |
| **China Clay (Kaolin)** | Bhagalpur, Munger |
| **Mica** | Nawada, Jamui, Munger |
| **Bauxite** | Munger region |
| **Glass Sand** | Bhagalpur |
| **Limestone** | Rohtas, Kaimur |

> ⭐ **VERY IMPORTANT PYQ FACT:** **Amjhore (Rohtas)** has India's (and Asia's) largest **Pyrite deposits**. This is a classic BPSC question!

---

## 🔶 SECTION 9: Power Sector in Bihar

| Power Station | Location | Type |
|--------------|----------|------|
| Barauni Thermal Power Station | Begusarai | Thermal |
| Kanti Thermal Power Station | Muzaffarpur | Thermal |
| Muzaffarpur Thermal Power Station | Muzaffarpur | Thermal |
| NTPC Nabinagar | Aurangabad | Thermal (large capacity) |
| North Koel Reservoir | Palamu (Jharkhand-border) | Hydro |

> Bihar faces severe power shortage; major focus of government is improving power infrastructure (Har Ghar Bijli scheme).

---

## 🔶 SECTION 10: Rivers and Irrigation in Bihar

### Major Rivers of Bihar:

```
NORTH BIHAR RIVERS (originate in Nepal/Himalayas):
  Gandak → enters at Champaran
  Burhi Gandak → Muzaffarpur
  Bagmati → Sitamarhi
  Kamla → Madhubani
  Kosi → Supaul (called "Sorrow of Bihar" — changes course frequently)
  Mahananda → Kishanganj

SOUTH BIHAR RIVERS (originate in Peninsular plateau):
  Son → Shahdabad (Arrah area) — most important south Bihar river
  Punpun → Patna area
  Falgu → Gaya (sacred river for Pitru-paksha ritual)
  Panchane → Munger
```

> ⭐ **PYQ FACTS:**
> - **Kosi = Sorrow of Bihar** (most devastating flood river)
> - **Falgu River** at Gaya is famous for **Pitru Paksha (ancestor worship)**
> - **Son River** = main river of south Bihar, a tributary of Ganga

---

## 🔶 SECTION 11: Bihar Tourism & Culture (Economic Angle)

| Place | Significance |
|-------|-------------|
| **Bodhgaya** | Where Buddha attained enlightenment — top foreign tourist destination in Bihar |
| **Nalanda** | Ancient university (UNESCO World Heritage Site) |
| **Vaishali** | Lord Mahavira's birthplace; first republic of world |
| **Rajgir** | Ancient city; hot springs; wildlife sanctuary |
| **Pawapuri** | Lord Mahavira's last rites site |
| **Vikramshila** | Ancient Buddhist university site |
| **Patna Sahib** | Birthplace of Guru Gobind Singh |

> ⭐ **Buddhist Circuit Tourism:** Bodhgaya → Rajgir → Nalanda = major foreign exchange earner for Bihar. Gaya airport gets direct international flights.

---

# 📝 PRACTICE QUESTIONS

---

# 🖥️ PART A — CS MCQs (25 Questions)

### Topic: NP-Completeness & Algorithm Paradigms
### Format: 5-option BPSC style (A/B/C/D = More than one of the above / E = None of the above)
### Difficulty: Easy → Medium → Hard → PYQ-Style → Tricky

---

**Q1.** Which of the following correctly defines Class P in computational complexity?

(A) Problems that can be verified in polynomial time  
(B) Problems that cannot be solved in polynomial time  
(C) Problems that can be solved in polynomial time  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** The abbreviation NP in complexity theory stands for:

(A) Non-Polynomial  
(B) Not Possible  
(C) Non-deterministic Polynomial time  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** Which of the following is an application of the Greedy algorithm?

(A) Huffman Coding  
(B) Dijkstra's Shortest Path  
(C) Kruskal's Minimum Spanning Tree  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** Which sorting algorithm uses the Divide and Conquer paradigm?

(A) Bubble Sort  
(B) Insertion Sort  
(C) Selection Sort  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** The 0/1 Knapsack problem is best solved using which algorithm paradigm?

(A) Greedy  
(B) Dynamic Programming  
(C) Divide and Conquer  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** Which of the following is/are NP-Complete problems?

(A) Travelling Salesman Problem (Decision version)  
(B) Boolean Satisfiability (SAT)  
(C) Hamiltonian Cycle  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** Dijkstra's shortest path algorithm belongs to which class of problems?

(A) NP-Complete  
(B) NP-Hard  
(C) Polynomial (Class P)  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** Which of the following properties MUST hold for Dynamic Programming to be applicable?

(A) Greedy Choice Property  
(B) Optimal Substructure  
(C) Overlapping Subproblems  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** The N-Queens problem is solved using which algorithm paradigm?

(A) Greedy  
(B) Dynamic Programming  
(C) Backtracking  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** Which of the following statements about P and NP is TRUE?

(A) P = NP has been proven  
(B) P ⊆ NP  
(C) NP ⊆ P  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** The FIRST problem ever proven to be NP-Complete was:

(A) Travelling Salesman Problem  
(B) Graph Coloring  
(C) Boolean Satisfiability (SAT)  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** In Backtracking, when a partial solution is found to be invalid, what happens?

(A) The algorithm terminates  
(B) The algorithm goes forward and tries next element  
(C) The algorithm abandons that path and tries another (backtracks)  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** Merge Sort has a time complexity of:

(A) O(n²) in all cases  
(B) O(n log n) in all cases  
(C) O(n) in best case  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Which of the following problems can be solved in POLYNOMIAL time?

(A) Hamiltonian Cycle  
(B) Graph 2-Coloring (Bipartite checking)  
(C) Travelling Salesman Problem  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** Floyd-Warshall algorithm for all-pairs shortest path uses which paradigm?

(A) Greedy  
(B) Divide and Conquer  
(C) Dynamic Programming  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** Huffman Coding produces:

(A) Fixed-length codes for all characters  
(B) Variable-length codes; frequent characters get shorter codes  
(C) Random-length codes  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** Which of the following is TRUE about NP-Complete problems?

(A) They can be solved in polynomial time  
(B) Every NP problem can be reduced to an NP-Complete problem in polynomial time  
(C) They are outside the class NP  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** The key difference between Divide and Conquer and Dynamic Programming is:

(A) D&C uses recursion; DP does not  
(B) D&C solves overlapping subproblems; DP solves non-overlapping ones  
(C) D&C solves non-overlapping subproblems; DP solves overlapping ones  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** Activity Selection Problem (scheduling maximum non-overlapping activities) is solved by:

(A) Selecting activity with earliest START time  
(B) Selecting activity with minimum DURATION  
(C) Selecting activity with earliest FINISH time  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** Quick Sort has a WORST case time complexity of:

(A) O(n log n)  
(B) O(n²)  
(C) O(n)  
(D) More than one of the above  
(E) None of the above  

---

**Q21 (PYQ-Style).** In BPSC TRE 2.0, the following was asked: Which algorithm is NOT a Greedy algorithm?

(A) Dijkstra's algorithm  
(B) Prim's algorithm  
(C) Bellman-Ford algorithm  
(D) More than one of the above  
(E) None of the above  

---

**Q22 (PYQ-Style).** Consider a problem: "Given a graph G and integer k, does G have a Hamiltonian Cycle of length ≤ k?" This problem is:

(A) In class P  
(B) In class NP  
(C) Neither P nor NP  
(D) More than one of the above  
(E) None of the above  

---

**Q23 (PYQ-Style).** The Longest Path problem in a general graph is:

(A) Solvable in polynomial time  
(B) NP-Hard  
(C) Same as Shortest Path in complexity  
(D) More than one of the above  
(E) None of the above  

---

**Q24 (Tricky).** Which of the following statements is/are CORRECT about Greedy algorithms?

(A) Greedy always gives optimal solution  
(B) Fractional Knapsack can be solved optimally by Greedy  
(C) 0/1 Knapsack can be solved optimally by Greedy  
(D) More than one of the above  
(E) None of the above  

---

**Q25 (Tricky).** A problem X is NP-Hard. Which of the following MUST be true?

(A) X is in class NP  
(B) X is at least as hard as every problem in NP  
(C) X can be solved in polynomial time  
(D) More than one of the above  
(E) None of the above  

---

# 🌍 PART B — GS/GK MCQs (25 Questions)

### Topic: Bihar Economy, Industries & Development
### Format: 5-option BPSC style (A/B/C/D = More than one of the above / E = None of the above)
### Difficulty: Easy → Medium → Hard → PYQ-Style → Tricky

---

**Q26.** Bihar was bifurcated and Jharkhand was carved out in which year?

(A) 1999  
(B) 2000  
(C) 2001  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** Which of the following is called the "Sorrow of Bihar"?

(A) Son River  
(B) Ganga River  
(C) Kosi River  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** Bihar produces approximately what percentage of India's total Makhana (Fox Nut)?

(A) 50%  
(B) 70%  
(C) 95%  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** Which district of Bihar is most famous for Shahi Litchi with GI Tag?

(A) Darbhanga  
(B) Muzaffarpur  
(C) Patna  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** The Headquarters of East Central Railway (ECR) is located at:

(A) Patna  
(B) Muzaffarpur  
(C) Hajipur  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** Bhagalpuri Silk (Tassar Silk) has received which recognition?

(A) National Award  
(B) UNESCO Heritage Tag  
(C) Geographical Indication (GI) Tag  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** The Barauni Oil Refinery in Bihar is managed by:

(A) HPCL  
(B) Indian Oil Corporation (IOC)  
(C) BPCL  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** Which of the following is Bihar's State Animal?

(A) Tiger  
(B) Elephant  
(C) Gaur (Indian Bison)  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** The largest pyrite deposit in Asia is located at:

(A) Jharia, Bihar  
(B) Amjhore, Rohtas district, Bihar  
(C) Dalmianagar, Rohtas  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** The Mahatma Gandhi Setu (road bridge) is built over which river?

(A) Son River at Patna  
(B) Ganga River at Patna  
(C) Gandak River  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** Which of the following cities is known as the "Silk City" of Bihar?

(A) Patna  
(B) Muzaffarpur  
(C) Bhagalpur  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** The Falgu River, associated with Pitru Paksha rituals, flows through which Bihar city?

(A) Patna  
(B) Gaya  
(C) Nalanda  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** The Barauni Oil Refinery was established in:

(A) 1954  
(B) 1964  
(C) 1975  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** Which of the following is Bihar's largest district by area?

(A) Patna  
(B) Rohtas  
(C) West Champaran  
(D) More than one of the above  
(E) None of the above  

---

**Q40 (PYQ-Style).** Jeevika (BRLPS) is primarily associated with:

(A) Providing bank loans to farmers  
(B) Promoting women's Self Help Groups for rural livelihoods  
(C) Building roads in rural Bihar  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** Nalanda University (ancient) has been declared a UNESCO World Heritage Site. The modern Nalanda University is located in:

(A) Patna  
(B) Rajgir, Nalanda district  
(C) Gaya  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** Under the 'Saat Nishchay' programme of Bihar, "Har Ghar Bijli" aims at:

(A) Providing a light bulb to every house  
(B) Providing continuous electricity to every household in Bihar  
(C) Building solar panels in every district  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** Katarni Rice, which has received a GI Tag, is associated with which district?

(A) Darbhanga  
(B) Bhagalpur  
(C) Muzaffarpur  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** The Bihar Agricultural University is located at:

(A) Patna  
(B) Sabour, Bhagalpur  
(C) Muzaffarpur  
(D) More than one of the above  
(E) None of the above  

---

**Q45 (PYQ-Style).** Which of the following airport(s) in Bihar serve international flights?

(A) Patna (Jay Prakash Narayan International Airport)  
(B) Gaya International Airport  
(C) Darbhanga Airport  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** The total number of districts in Bihar (as of 2024) is:

(A) 35  
(B) 38  
(C) 40  
(D) More than one of the above  
(E) None of the above  

---

**Q47 (Tricky).** Hajipur Industrial Area is located in which district of Bihar?

(A) Patna  
(B) Vaishali  
(C) Muzaffarpur  
(D) More than one of the above  
(E) None of the above  

---

**Q48 (Tricky).** Which of the following is NOT an agro-based industry of Bihar?

(A) Sugar Industry  
(B) Makhana Processing  
(C) Steel Manufacturing  
(D) More than one of the above  
(E) None of the above  

---

**Q49 (Tricky).** Under Mukhyamantri Udyami Yojana, an SC/ST entrepreneur gets financial assistance of:

(A) ₹5 lakh (100% grant)  
(B) ₹10 lakh (50% grant + 50% loan)  
(C) ₹20 lakh (30% grant + 70% loan)  
(D) More than one of the above  
(E) None of the above  

---

**Q50 (Tricky).** "Silao Khaja" which has a GI Tag is associated with which district?

(A) Muzaffarpur  
(B) Nalanda  
(C) Vaishali  
(D) More than one of the above  
(E) None of the above  

---

---

# ✅ ANSWER KEY

> **Solve all 50 questions BEFORE looking here!**

---

## CS Answers (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q1 | **(C)** | P = solvable in polynomial time. (A) is definition of NP |
| Q2 | **(C)** | NP = Non-deterministic Polynomial time. Common misconception: it does NOT mean "Not Polynomial" |
| Q3 | **(D)** | Huffman Coding, Dijkstra's, Kruskal's — ALL three are Greedy algorithms |
| Q4 | **(E)** | Bubble, Insertion, Selection are NOT D&C. D&C sorts = Merge Sort, Quick Sort (not listed here) |
| Q5 | **(B)** | 0/1 Knapsack = Classic DP problem. Fractional Knapsack = Greedy |
| Q6 | **(D)** | TSP (decision), SAT, Hamiltonian Cycle — ALL are NP-Complete |
| Q7 | **(C)** | Dijkstra's = Polynomial (P class). Very common PYQ trap: Shortest Path ≠ NP-Complete |
| Q8 | **(D)** | DP requires BOTH Optimal Substructure AND Overlapping Subproblems |
| Q9 | **(C)** | N-Queens = classic Backtracking problem |
| Q10 | **(B)** | P ⊆ NP is true. P=NP is NOT proven. NP ⊆ P is not established |
| Q11 | **(C)** | SAT (Boolean Satisfiability) = first NP-Complete problem (Cook's theorem, 1971) |
| Q12 | **(C)** | Backtracking abandons invalid path and tries another → key defining characteristic |
| Q13 | **(B)** | Merge Sort = O(n log n) in ALL cases (best, average, worst) — this is its advantage |
| Q14 | **(B)** | Graph 2-Coloring (bipartite check) = Polynomial using BFS/DFS. Hamiltonian Cycle and TSP are NP-Complete |
| Q15 | **(C)** | Floyd-Warshall uses DP (fills a matrix bottom-up) |
| Q16 | **(B)** | Huffman = variable-length; frequent chars → shorter codes. This is the whole point! |
| Q17 | **(B)** | Every NP problem can be reduced to NP-Complete in polynomial time — that's the definition |
| Q18 | **(C)** | D&C = non-overlapping subproblems. DP = overlapping subproblems. This is the KEY difference |
| Q19 | **(C)** | Greedy choice for Activity Selection = earliest FINISH time (not start time, not duration) |
| Q20 | **(B)** | Quick Sort worst case = O(n²) — happens when pivot is always min/max element |
| Q21 | **(C)** | Bellman-Ford is Dynamic Programming, NOT Greedy. Dijkstra's and Prim's are Greedy |
| Q22 | **(B)** | Hamiltonian Cycle is in NP — a given solution can be verified in polynomial time |
| Q23 | **(B)** | Longest Path in general graph = NP-Hard (Shortest Path = P — they are DIFFERENT!) |
| Q24 | **(B)** | Fractional Knapsack → Greedy optimal. 0/1 Knapsack → Greedy NOT optimal (needs DP). So only B is correct |
| Q25 | **(B)** | NP-Hard means at least as hard as every problem in NP. NP-Hard problems may NOT be in NP |

---

## GS Answers (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q26 | **(B)** | Jharkhand formed on **15 November 2000** from Bihar |
| Q27 | **(C)** | Kosi River = "Sorrow of Bihar" due to frequent devastating floods and course changes |
| Q28 | **(C)** | Bihar produces ~95% of India's Makhana; Darbhanga region is the hub |
| Q29 | **(B)** | Muzaffarpur's Shahi Litchi has GI Tag — extremely famous |
| Q30 | **(C)** | East Central Railway HQ = **Hajipur** (Vaishali district) |
| Q31 | **(C)** | Bhagalpuri Silk (Tassar) has GI Tag |
| Q32 | **(B)** | Barauni Refinery = **Indian Oil Corporation (IOC)** |
| Q33 | **(C)** | Bihar State Animal = **Gaur (Indian Bison)** |
| Q34 | **(B)** | Amjhore (Rohtas) = largest pyrite deposits in Asia — classic BPSC question |
| Q35 | **(B)** | Mahatma Gandhi Setu spans the **Ganga at Patna** (5.575 km long) |
| Q36 | **(C)** | **Bhagalpur** = Silk City of Bihar (famous for Tussar/Tassar silk) |
| Q37 | **(B)** | **Gaya** — Falgu River; famous for Pitru Paksha (ancestor worship rituals) |
| Q38 | **(B)** | Barauni Refinery established **1964** as Indo-Soviet collaboration |
| Q39 | **(C)** | **West Champaran** = largest district of Bihar by area |
| Q40 | **(B)** | Jeevika (BRLPS) = women's SHG-based rural livelihoods programme |
| Q41 | **(B)** | Modern Nalanda University is at **Rajgir, Nalanda district** |
| Q42 | **(B)** | Har Ghar Bijli = continuous electricity supply to every household |
| Q43 | **(B)** | Katarni Rice GI Tag → **Bhagalpur** (also Banka) |
| Q44 | **(B)** | Bihar Agricultural University = **Sabour, Bhagalpur** |
| Q45 | **(D)** | Both Patna AND Gaya airports handle international flights (Gaya serves Buddhist pilgrims) |
| Q46 | **(B)** | Bihar has **38 districts** |
| Q47 | **(B)** | Hajipur is in **Vaishali** district (not Patna, though close to Patna) |
| Q48 | **(C)** | Steel manufacturing is NOT agro-based and Bihar doesn't have it (Jharkhand does) |
| Q49 | **(B)** | Mukhyamantri Udyami Yojana = ₹10 lakh (50% grant + 50% loan) for SC/ST/women |
| Q50 | **(B)** | Silao Khaja GI Tag → **Nalanda** district (Silao is a town in Nalanda) |

---

# 🌟 TOPPER'S REVISION NOTES — Day 33

## ⚡ CS Quick Revision (5 Points)
1. **P** = Solvable in polynomial time | **NP** = Verifiable in polynomial time | **P ⊆ NP**
2. **NP-Complete** = In NP + NP-Hard | Examples: TSP, SAT, Hamiltonian Cycle, Graph Coloring
3. **Shortest Path = P** (Dijkstra's) | **Longest Path = NP-Hard** — Remember this contrast!
4. **Greedy** = Local optimal (Activity Selection, Huffman, Dijkstra, Kruskal, Prim, Fractional Knapsack) | **DP** = Overlapping subproblems (0/1 Knapsack, LCS, Floyd-Warshall)
5. **D&C** = Non-overlapping → Merge Sort, Quick Sort, Binary Search | **Backtracking** = Pruned exhaustive → N-Queens, Sudoku, Hamiltonian Cycle

## ⚡ GS Quick Revision (5 Points)
1. **Jharkhand bifurcation: 2000** — Bihar lost minerals; now agro-economy dominant
2. **Kosi = Sorrow of Bihar** | **Amjhore (Rohtas) = Largest Pyrite in Asia**
3. **GI Tags:** Shahi Litchi (Muzaffarpur), Bhagalpuri Silk (Bhagalpur), Makhana (Darbhanga), Katarni Rice (Bhagalpur), Silao Khaja (Nalanda), Jardalu Mango (Bhagalpur)
4. **Barauni Refinery (IOC, 1964)** | **ECR HQ = Hajipur** | **Bihar has 38 districts**
5. **Jeevika = women SHG scheme** | **Bihar produces 95% India's Makhana** | **West Champaran = largest district**

---

## 📌 Traps to Avoid in the Actual Exam

| Trap | Correct Answer |
|------|---------------|
| NP means "Not Polynomial" | ❌ Wrong → NP = Non-deterministic Polynomial (verifiable in poly time) |
| Shortest Path = NP-Complete | ❌ Wrong → Shortest Path = POLYNOMIAL (P class) |
| Quick Sort = O(n log n) always | ❌ Wrong → Quick Sort WORST case = O(n²) |
| 0/1 Knapsack = Greedy | ❌ Wrong → 0/1 Knapsack = Dynamic Programming |
| Bellman-Ford = Greedy | ❌ Wrong → Bellman-Ford = Dynamic Programming |
| Hajipur is in Patna district | ❌ Wrong → Hajipur is in Vaishali district |
| Makhana = Bihar produces 50% | ❌ Wrong → Bihar produces ~95% of India's Makhana |
| ECR HQ = Patna | ❌ Wrong → ECR HQ = Hajipur |
| Katarni Rice = Muzaffarpur | ❌ Wrong → Katarni Rice = Bhagalpur |

---

> **🏆 Daily Target:** Finish all 50 MCQs, score your answers, review only what you got wrong. Write the 5-point summary from memory TONIGHT.
>
> **Next Up → Day 34:** DSA Full PYQ Practice Session (Catalan Numbers, Circular Queue, Expression Conversion focus)

---
*BPSC TRE 4.0 | Phase 1 — Week 5 | Day 33 of 170*
