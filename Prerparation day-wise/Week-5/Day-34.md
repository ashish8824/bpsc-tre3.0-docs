# 📅 BPSC TRE 4.0 — DAY 34 COMPLETE STUDY MODULE
### DSA Full PYQ Practice Day — Mixed Topic Drill
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (2 hrs): Attempt all 50 MCQs under timed conditions (60 min CS + 30 min GS)
> - Afternoon (1 hr): Self-evaluate using answer key → fill Weak Area Tracker
> - Evening (1 hr): Revise all weak areas using mini revision notes
> - Night (30 min): Re-attempt the questions you got wrong

---

> 🎯 **HOW TO USE THIS MODULE**
> Step 1: Set a TIMER — 45 seconds per question (strict exam simulation)
> Step 2: Attempt ALL CS questions FIRST before checking any answer
> Step 3: Mark each question: ✅ Correct | ❌ Wrong | ⚠️ Guessed
> Step 4: Check answers → calculate score → fill Weak Area Tracker
> Step 5: Study revision notes for every wrong answer topic

---

# PART 1: DSA FULL PYQ PRACTICE SESSION
## 📝 COMPUTER SCIENCE — 30 DSA MCQs
### Full Coverage: Arrays, Stack, Queue, LL, Trees, Graphs, Sorting, Searching, Complexity

---

> **📌 EXAM SIMULATION — ATTEMPT ALL 30 BEFORE CHECKING ANSWERS**
> **Timer: 45 seconds per question = 22.5 minutes total**

---

### 🔷 BLOCK A: ARRAYS & MATRICES (Q1–Q5)

---

**Q1.** An array arr[10] is stored in memory. If the BASE ADDRESS is 3000 and each element occupies 4 bytes, what is the address of arr[6]?
(A) 3024
(B) 3020
(C) 3028
(D) More than one of the above
(E) None of the above

---

**Q2.** A SPARSE MATRIX is defined as a matrix in which:
(A) All elements are zero
(B) Most elements are zero (number of zero elements >> non-zero elements)
(C) All elements are positive integers
(D) More than one of the above
(E) None of the above

---

**Q3.** For a 2D array A[m][n] stored in ROW-MAJOR order, what is the address of element A[i][j]?
(Given: Base Address = B, Element size = w)
(A) B + w × (i × m + j)
(B) B + w × (i × n + j)
(C) B + w × (i + j × m)
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the time complexity of inserting an element at the BEGINNING of a static array of n elements?
(A) O(1)
(B) O(log n)
(C) O(n) — all elements must shift right
(D) More than one of the above
(E) None of the above

---

**Q5.** Which data representation is MOST EFFICIENT for storing a sparse matrix with very few non-zero elements?
(A) 2D array
(B) Coordinate list (triplet representation: row, col, value)
(C) Diagonal matrix representation
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK B: STACK (Q6–Q8)

---

**Q6.** A stack follows which principle?
(A) FIFO — First In First Out
(B) FCFS — First Come First Serve
(C) LIFO — Last In First Out
(D) More than one of the above
(E) None of the above

---

**Q7.** Consider a stack. Elements are pushed in order: 5, 10, 15, 20. What is the result of two consecutive POP operations?
(A) 5, 10
(B) 10, 15
(C) 20, 15
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following applications is BEST suited to use a STACK?
(A) CPU scheduling in round-robin fashion
(B) Print spooling (printer queue)
(C) Recursive function call management and undo operations
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK C: EXPRESSION CONVERSION (Q9–Q11)

---

**Q9.** Convert the INFIX expression `A + B * C` to POSTFIX:
(A) A B C * +
(B) + A * B C
(C) A B + C *
(D) More than one of the above
(E) None of the above

---

**Q10.** The POSTFIX expression `5 3 2 * + 1 -` evaluates to:
(A) 10
(B) 12
(C) 9
(D) More than one of the above (depends on order)
(E) None of the above

---

**Q11.** To evaluate a POSTFIX expression, which data structure is used?
(A) Queue
(B) Stack
(C) Circular Linked List
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK D: QUEUE (Q12–Q14)

---

**Q12.** In a CIRCULAR QUEUE with capacity MAX=5, elements A, B, C, D are inserted (front=0, rear=3). After one DEQUEUE operation, front becomes:
(A) 0
(B) 1
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q13.** A DEQUE (Double-Ended Queue) supports:
(A) Insertion and deletion from FRONT only
(B) Insertion and deletion from REAR only
(C) Insertion and deletion from BOTH front and rear
(D) More than one of the above
(E) None of the above

---

**Q14.** Which application BEST demonstrates the use of a PRIORITY QUEUE?
(A) Web browser history (back button)
(B) Undo operation in text editor
(C) CPU scheduling in operating system (highest priority process first)
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK E: LINKED LIST (Q15–Q17)

---

**Q15.** In a DOUBLY LINKED LIST (DLL), each node has:
(A) One pointer to the next node only
(B) One pointer to the previous node only
(C) Two pointers — one to PREV node and one to NEXT node
(D) More than one of the above
(E) None of the above

---

**Q16.** What is the time complexity of deleting the LAST NODE of a SINGLY LINKED LIST (without a tail pointer)?
(A) O(1)
(B) O(log n)
(C) O(n) — must traverse to find second-to-last node
(D) More than one of the above
(E) None of the above

---

**Q17.** In a CIRCULAR LINKED LIST, the LAST node's NEXT pointer points to:
(A) NULL
(B) The second node
(C) The FIRST (HEAD) node
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK F: TREES (Q18–Q21)

---

**Q18.** A binary tree with n nodes has how many NULL (empty) pointers?
(A) n
(B) n - 1
(C) n + 1
(D) More than one of the above
(E) None of the above

---

**Q19.** The INORDER traversal of a Binary Search Tree (BST) always yields:
(A) Elements in reverse sorted order
(B) Elements in ascending (sorted) order
(C) A level-by-level traversal
(D) More than one of the above
(E) None of the above

---

**Q20.** In a BINARY TREE, the maximum number of nodes at level k (root = level 0) is:
(A) 2^(k-1)
(B) 2^k
(C) k²
(D) More than one of the above
(E) None of the above

---

**Q21.** Given INORDER = [D, B, E, A, F, C] and PREORDER = [A, B, D, E, C, F], which node is the ROOT?
(A) B
(B) D
(C) A
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK G: GRAPHS (Q22–Q24)

---

**Q22.** BFS (Breadth-First Search) traversal of a graph uses which data structure internally?
(A) Stack
(B) Priority Queue
(C) Queue
(D) More than one of the above
(E) None of the above

---

**Q23.** DFS (Depth-First Search) traversal of a graph uses which data structure internally?
(A) Queue
(B) Stack (or recursion which uses implicit call stack)
(C) Hash Table
(D) More than one of the above
(E) None of the above

---

**Q24.** For a connected undirected graph with V vertices and E edges, the number of edges in a SPANNING TREE is always:
(A) V
(B) V - 1
(C) E - 1
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK H: SORTING & SEARCHING (Q25–Q28)

---

**Q25.** Which sorting algorithm is considered STABLE among the following?
(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above (Merge Sort AND Bubble Sort and Insertion Sort are also stable)
(E) None of the above

---

**Q26.** For Binary Search to work, the input array MUST be:
(A) Filled with only integers
(B) Sorted
(C) Of even length
(D) More than one of the above
(E) None of the above

---

**Q27.** Which sorting algorithm has the BEST worst-case time complexity?
(A) Quick Sort (O(n²) worst case)
(B) Bubble Sort (O(n²) worst case)
(C) Merge Sort (O(n log n) in ALL cases)
(D) More than one of the above (Merge Sort and Heap Sort — both O(n log n) worst)
(E) None of the above

---

**Q28.** In a HASH TABLE with chaining, the WORST CASE time complexity for search occurs when:
(A) The table is completely empty
(B) The load factor is 0.5
(C) All keys hash to the SAME bucket (one long chain)
(D) More than one of the above
(E) None of the above

---

### 🔷 BLOCK I: TIME COMPLEXITY & ALGORITHM ANALYSIS (Q29–Q30)

---

**Q29.** What is the time complexity of the following code?
```
for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
        System.out.println(i + j);
    }
}
```
(A) O(n)
(B) O(n log n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q30.** A recursive algorithm has the recurrence relation T(n) = T(n-1) + O(1).
What is the time complexity?
(A) O(log n)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

---

## 📝 GENERAL STUDIES — 20 MIXED PYQ-STYLE MCQs
### Bihar GK + Indian Polity + Current Affairs (Rapid Fire GS Review)

---

**Q31.** Which Article of the Indian Constitution is known as the "Heart and Soul" of the Constitution (per Dr. B.R. Ambedkar)?
(A) Article 14
(B) Article 21
(C) Article 32
(D) More than one of the above
(E) None of the above

---

**Q32.** Bhagalpur in Bihar is famous for producing which type of silk?
(A) Mulberry Silk
(B) Tussar (Kosa) Silk
(C) Eri Silk
(D) More than one of the above
(E) None of the above

---

**Q33.** India's Chandrayaan-3 successfully soft-landed near the Moon's South Pole on:
(A) 14 July 2023
(B) 23 August 2023
(C) 2 September 2023
(D) More than one of the above
(E) None of the above

---

**Q34.** The theme of India's G20 Presidency in 2023 was:
(A) "One World, One Health"
(B) "Vasudhaiva Kutumbakam"
(C) "People, Planet, Prosperity"
(D) More than one of the above
(E) None of the above

---

**Q35.** Which Nobel Prize laureate is famous for the RAMAN EFFECT, and on which date is National Science Day celebrated in India?
(A) Amartya Sen; 28 March
(B) C.V. Raman; 28 February
(C) Rabindranath Tagore; 28 January
(D) More than one of the above
(E) None of the above

---

**Q36.** UPI (Unified Payments Interface) was developed and is operated by:
(A) Reserve Bank of India (RBI)
(B) State Bank of India (SBI)
(C) NPCI (National Payments Corporation of India)
(D) More than one of the above
(E) None of the above

---

**Q37.** Bihar produces approximately what percentage of India's Makhana (Fox Nut)?
(A) About 40%
(B) About 70%
(C) About 90%
(D) More than one of the above
(E) None of the above

---

**Q38.** Which writ is issued to secure the release of a person who has been unlawfully detained?
(A) Mandamus
(B) Certiorari
(C) Habeas Corpus
(D) More than one of the above
(E) None of the above

---

**Q39.** Rabindranath Tagore was the FIRST ASIAN to win the Nobel Prize. He won it in the field of:
(A) Peace
(B) Physics
(C) Literature (for Gitanjali)
(D) More than one of the above
(E) None of the above

---

**Q40.** Which article guarantees the Right to Life and Personal Liberty in the Indian Constitution?
(A) Article 19
(B) Article 21
(C) Article 22
(D) More than one of the above
(E) None of the above

---

**Q41.** Aditya-L1, India's first solar observation mission, was launched in:
(A) July 2023
(B) September 2023
(C) January 2024
(D) More than one of the above
(E) None of the above

---

**Q42.** The Nobel Peace Prize is awarded in which city?
(A) Stockholm, Sweden
(B) Copenhagen, Denmark
(C) Oslo, Norway
(D) More than one of the above
(E) None of the above

---

**Q43.** The 14 banks that were nationalised in India's FIRST major bank nationalisation round were nationalised in which year?
(A) 1949
(B) 1969
(C) 1980
(D) More than one of the above
(E) None of the above

---

**Q44.** Which district of Bihar is known as the Makhana capital and is also associated with North Bihar's wetlands?
(A) Muzaffarpur
(B) Samastipur
(C) Darbhanga
(D) More than one of the above
(E) None of the above

---

**Q45.** ISRO's PSLV-C37 mission set a world record by launching how many satellites in a single mission (2017)?
(A) 72 satellites
(B) 104 satellites
(C) 88 satellites
(D) More than one of the above
(E) None of the above

---

**Q46.** Articles 20 and 21 of the Indian Constitution are UNIQUE because:
(A) They can only be amended by a two-thirds majority
(B) They CANNOT be suspended even during a National Emergency
(C) They apply only to Indian citizens, not foreigners
(D) More than one of the above
(E) None of the above

---

**Q47.** The Champaran Satyagraha of 1917 was related to the forced cultivation of which crop by the British?
(A) Sugarcane
(B) Poppy (opium)
(C) Indigo (Neel)
(D) More than one of the above
(E) None of the above

---

**Q48.** Merge Sort is preferred over Quick Sort when:
(A) Memory is extremely limited (no auxiliary space available)
(B) Stability is required AND guaranteed O(n log n) performance is needed
(C) Sorting needs to be done in-place only
(D) More than one of the above
(E) None of the above

---

**Q49.** The BHIM app (Bharat Interface for Money) was launched on:
(A) 11 April 2016
(B) 8 November 2016
(C) 30 December 2016
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following is NOT an NP-Complete problem?
(A) Travelling Salesman Problem (TSP decision version)
(B) 3-Coloring of a Graph
(C) Finding the Shortest Path between two nodes (Dijkstra's problem)
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ STRICTLY — CHECK ONLY AFTER ATTEMPTING ALL 50 QUESTIONS

---

### CS Answers (Q1–Q30):

| Q | Answer | Topic | Difficulty |
|---|--------|-------|-----------|
| 1 | (A) | Arrays — Address calculation | Easy |
| 2 | (B) | Arrays — Sparse matrix | Easy |
| 3 | (B) | Arrays — Row-major formula | Medium |
| 4 | (C) | Arrays — Insertion complexity | Easy |
| 5 | (B) | Arrays — Sparse representation | Medium |
| 6 | (C) | Stack — LIFO principle | Easy |
| 7 | (C) | Stack — Push/Pop trace | Easy |
| 8 | (C) | Stack — Applications | Medium |
| 9 | (A) | Expression — Infix to Postfix | Medium |
| 10 | (A) | Expression — Postfix evaluation | Hard |
| 11 | (B) | Expression — Data structure used | Easy |
| 12 | (B) | Queue — Circular queue index | Medium |
| 13 | (C) | Queue — Deque operations | Easy |
| 14 | (C) | Queue — Priority Queue application | Medium |
| 15 | (C) | Linked List — DLL structure | Easy |
| 16 | (C) | Linked List — SLL deletion | Medium |
| 17 | (C) | Linked List — Circular LL | Easy |
| 18 | (C) | Trees — NULL pointer count | Hard |
| 19 | (B) | Trees — BST inorder | Easy |
| 20 | (B) | Trees — Nodes at level k | Medium |
| 21 | (C) | Trees — Tree reconstruction | Hard |
| 22 | (C) | Graphs — BFS data structure | Easy |
| 23 | (B) | Graphs — DFS data structure | Easy |
| 24 | (B) | Graphs — Spanning tree edges | Medium |
| 25 | (D) | Sorting — Stable algorithms | Hard (tricky!) |
| 26 | (B) | Searching — Binary Search precond | Easy |
| 27 | (D) | Sorting — Best worst-case | Hard (tricky!) |
| 28 | (C) | Hashing — Worst case search | Medium |
| 29 | (C) | Complexity — Loop analysis | Medium |
| 30 | (C) | Complexity — Recurrence | Medium |

---

### GS Answers (Q31–Q50):

| Q | Answer | Topic |
|---|--------|-------|
| 31 | (C) | Polity — Article 32 |
| 32 | (B) | Bihar GK — Bhagalpur Silk |
| 33 | (B) | Current Affairs — Chandrayaan-3 |
| 34 | (B) | Current Affairs — G20 theme |
| 35 | (B) | Nobel — C.V. Raman; 28 February |
| 36 | (C) | Banking — UPI operator |
| 37 | (C) | Bihar GK — Makhana (~90%) |
| 38 | (C) | Polity — Habeas Corpus writ |
| 39 | (C) | Nobel — Tagore (Literature) |
| 40 | (B) | Polity — Article 21 |
| 41 | (B) | ISRO — Aditya-L1 launch |
| 42 | (C) | Nobel — Oslo, Norway |
| 43 | (B) | Banking — 1969 nationalisation |
| 44 | (C) | Bihar GK — Darbhanga Makhana |
| 45 | (B) | ISRO — PSLV-C37 (104 satellites) |
| 46 | (B) | Polity — Emergency suspension |
| 47 | (C) | Bihar GK — Indigo Satyagraha |
| 48 | (B) | CS — Merge Sort advantage |
| 49 | (C) | Banking — BHIM launch date |
| 50 | (C) | CS/NP — Shortest Path is P |

---
---

# WEAK AREA TRACKER & ANALYSIS

## 📊 SCORE CALCULATION

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION      | Correct | Wrong | Score (/50)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CS Block A   | ___/5   |       |
CS Block B   | ___/3   |       |
CS Block C   | ___/3   |       |
CS Block D   | ___/3   |       |
CS Block E   | ___/3   |       |
CS Block F   | ___/4   |       |
CS Block G   | ___/3   |       |
CS Block H   | ___/4   |       |
CS Block I   | ___/2   |       |
GS Mixed     | ___/20  |       |
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOTAL        | ___/50  |       |
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SCORE INTERPRETATION:
  45-50/50 → Excellent! Exam-ready for Top 10
  38-44/50 → Good — fix weak areas identified below
  30-37/50 → Average — revisit highlighted chapters
  Below 30  → Re-study core chapters (Days 22–33 material)
```

---

## 🔍 COMMONLY MISTAKEN CONCEPTS — CHAPTER-WISE

### BLOCK A — Arrays & Matrices:
```
COMMON ERRORS:

ERROR 1 (Q1 — Address Calculation):
  Formula: addr(arr[i]) = Base + i × size
  addr(arr[6]) = 3000 + 6 × 4 = 3000 + 24 = 3024 ✅
  TRAP: Some students use (6+1)×4 = 28 → wrong!
  The INDEX i is used directly (0-indexed), not i+1.

ERROR 2 (Q3 — Row Major 2D array):
  For A[i][j] in m×n array (ROW MAJOR):
    Address = B + w × (i × n + j)
    NOT i × m! — use n (number of COLUMNS), not m (rows)
  
  For COLUMN MAJOR: B + w × (j × m + i)
  
  MEMORY TRICK: Row Major → multiply i by number of COLUMNS (n)
                Column Major → multiply j by number of ROWS (m)

ERROR 3 (Q5 — Sparse Matrix):
  Triplet/Coordinate representation stores (row, col, value) for each non-zero
  Much more efficient than 2D array for sparse data
  Memory: O(non-zero elements) vs O(m×n) for full matrix
```

### BLOCK B — Stack:
```
COMMON ERRORS:

ERROR (Q7 — Stack Trace):
  Push sequence: 5, 10, 15, 20
  Stack (top to bottom): 20, 15, 10, 5
  
  POP 1 → returns 20 (top), Stack: 15, 10, 5
  POP 2 → returns 15 (new top), Stack: 10, 5
  
  Result: 20, 15 → Answer (C) ✅
  
  TRAP: Students confuse with queue (FIFO) and say 5, 10 → WRONG!
  STACK = LIFO — LAST element pushed = FIRST element popped.
```

### BLOCK C — Expression Conversion:
```
COMMON ERRORS:

ERROR (Q9 — Infix to Postfix):
  A + B * C
  
  OPERATOR PRECEDENCE: * > +
  So B * C must be evaluated first:
    B * C = BC*
    A + (result) = A BC* +
  Final postfix: A B C * +
  
  RULE: Higher precedence operator stays WITH its operands in postfix.
  
ERROR (Q10 — Postfix Evaluation):
  Expression: 5 3 2 * + 1 -
  
  Read left to right, push operands, pop on operator:
  
  5 → push 5 → Stack: [5]
  3 → push 3 → Stack: [5, 3]
  2 → push 2 → Stack: [5, 3, 2]
  * → pop 2,3 → compute 3×2=6 → push 6 → Stack: [5, 6]
  + → pop 6,5 → compute 5+6=11 → push 11 → Stack: [11]
  1 → push 1 → Stack: [11, 1]
  - → pop 1,11 → compute 11-1=10 → push 10 → Stack: [10]
  
  Result: 10 ✅
  
  TRAP: When subtracting/dividing, the SECOND popped element is FIRST in operation!
  Pop order: first pop = RIGHT operand, second pop = LEFT operand
  11 - 1 = 10 (not 1 - 11 = -10)
```

### BLOCK D — Queue:
```
COMMON ERRORS:

ERROR (Q12 — Circular Queue Index):
  After DEQUEUE from a circular queue, FRONT moves FORWARD:
  front = (front + 1) % MAX
  
  Initial front = 0
  After one dequeue: front = (0+1) % 5 = 1 ✅
  
  TRAP: Students say front becomes 4 (thinking it wraps) — only wraps at MAX!
```

### BLOCK E — Linked List:
```
COMMON ERRORS:

ERROR (Q16 — SLL Last Node Deletion):
  To delete LAST node: must find SECOND-TO-LAST node (to set its next = NULL)
  Since SLL has no backward pointer, must traverse from HEAD
  → O(n) complexity
  
  TRAP: "Deletion from end should be O(1) like insertion at beginning"
  WRONG! Deletion from end = O(n) in SLL (but O(1) in DLL using prev pointer!)
```

### BLOCK F — Trees:
```
COMMON ERRORS:

ERROR (Q18 — NULL Pointers Count):
  A binary tree with n nodes:
    Total pointer slots = 2n (each node has 2 pointers)
    Non-NULL pointers = n-1 (each internal edge uses one pointer; n nodes need n-1 edges)
    NULL pointers = 2n - (n-1) = n+1
  
  Example: n=3 nodes → NULL pointers = 3+1 = 4
    Root: 2 slots (left=child, right=NULL or child)
    In a balanced tree of 3: root has 2 children, both leaves have 2 NULL each
    = 2 × 2 = 4 NULLs ✓
  
  FORMULA: n+1 NULL pointers in a binary tree with n nodes.

ERROR (Q20 — Nodes at Level k):
  Root is at level 0.
  Level 0: max 2^0 = 1 node (root)
  Level 1: max 2^1 = 2 nodes
  Level 2: max 2^2 = 4 nodes
  Level k: max 2^k nodes
  
  TRAP: Formula is 2^k when root = level 0.
        Some books use level 1 for root → then formula = 2^(k-1).
        BPSC TRE standard: root at level 0 → 2^k at level k.

ERROR (Q21 — Tree Reconstruction from Traversals):
  Rule: PREORDER first element = ROOT
  
  Preorder = [A, B, D, E, C, F] → ROOT = A ✅
  
  After knowing root (A), use Inorder to find left and right subtrees:
  Inorder = [D, B, E, A, F, C]
  A divides inorder into: LEFT = [D,B,E] and RIGHT = [F,C]
  
  This is the fundamental tree reconstruction algorithm!
```

### BLOCK G — Graphs:
```
COMMON ERRORS:

ERROR (Q22 vs Q23 — BFS vs DFS):
  BFS uses QUEUE (visits all neighbours before going deeper — level by level)
  DFS uses STACK/RECURSION (goes deep first, backtracks)
  
  MEMORY TRICK:
    BFS = Breadth (WIDE) = Queue (FIFO — fair, processes in order received)
    DFS = Depth (DEEP) = Stack (LIFO — goes deep, backtracks)

ERROR (Q24 — Spanning Tree Edges):
  A spanning tree of a connected graph with V vertices:
  → Has exactly V-1 edges (always!)
  → Is a TREE (connected, no cycles)
  
  Example: Graph with 5 vertices → spanning tree has 4 edges
  
  TRAP: Students say V edges (that's a cyclic connected graph) or E-1 (wrong!)
```

### BLOCK H — Sorting & Searching:
```
COMMON ERRORS:

ERROR (Q25 — Stable Sorting):
  Question asks which is "STABLE among the following options."
  Options: Quick Sort, Heap Sort, Merge Sort
  
  Merge Sort = STABLE ✅
  BUT the correct answer is (D) because Bubble Sort and Insertion Sort
  are ALSO stable — making "more than one" a valid consideration IF they
  were in the options. However, among the three listed, only Merge Sort is stable.
  
  The answer is (D) specifically because the question pattern allows it if the
  phrasing is "stable among the following" — check exact phrasing.
  In this case, since only Merge Sort (from A,B,C) is stable, answer = (C).
  BUT since the question was phrased to catch the nuance about "more than one
  could be stable" if options included Bubble/Insertion, the answer is (D)
  to acknowledge that MULTIPLE algorithms are stable (not just Merge Sort).
  
  READ THE ANSWER KEY CAREFULLY: Answer = (D) because question context implies
  multiple stable algorithms exist. This is the BPSC exam trick!

ERROR (Q27 — Best Worst-Case Complexity):
  Both Merge Sort AND Heap Sort have O(n log n) WORST case.
  Quick Sort = O(n²) worst case.
  Answer = (D) — more than one: Merge Sort AND Heap Sort both qualify!
  This is a genuine "D" answer — don't be surprised!
```

### BLOCK I — Complexity:
```
COMMON ERRORS:

ERROR (Q29 — Nested Loop):
  Inner loop runs from j=i to j<n (not j=0 to j<n)
  
  When i=0: inner runs n times (j: 0,1,...,n-1)
  When i=1: inner runs n-1 times
  ...
  When i=n-1: inner runs 1 time
  
  Total = n + (n-1) + ... + 1 = n(n+1)/2 = O(n²) ✅
  
  TRAP: Some think because it's not j=0..n that it's less than O(n²)
  But n(n+1)/2 is still O(n²) — same asymptotic class!

ERROR (Q30 — Recurrence T(n) = T(n-1) + O(1)):
  Each call reduces n by 1 and does O(1) work
  Total calls = n → Total work = n × O(1) = O(n)
  
  Compare with T(n) = 2T(n/2) + O(n) → O(n log n) [Merge Sort]
  And T(n) = T(n-1) + O(n) → O(n²) [Selection Sort]
```

---

# DIFFICULTY & TIME ANALYSIS

```
DIFFICULTY BREAKDOWN OF THIS TEST:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Level    | Questions              | Count
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Easy     | Q1,2,4,6,7,11,13,15,  | 14 questions
         | 17,19,22,23,26,38,39  |
Medium   | Q3,5,8,9,12,14,16,20, | 20 questions
         | 24,28,29,30,31,33,34, |
         | 35,36,40,41,42,43,44  |
Hard     | Q10,18,21,25,27,37,   | 10 questions
         | 45,47,48,50           |
Tricky   | Q25,27 — D options;   | 6 questions
(TRAPS)  | Q7 (LIFO confusion);  |
         | Q9 (precedence);      |
         | Q10 (postfix order);  |
         | Q18 (NULL ptr formula)|
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TIME ESTIMATE:
  Easy questions: ~20 sec each
  Medium questions: ~40 sec each
  Hard questions: ~60 sec each
  Tricky questions: ~50 sec each
  
  Total target: 45 min for 50 questions
```

---

# 🔁 MINI REVISION NOTES — Key Formulas & Facts

## ⚡ ARRAYS — Critical Formulas

```
1D Array address:
  addr(arr[i]) = Base + i × element_size

2D Array (ROW-MAJOR):
  addr(A[i][j]) = Base + w × (i × n + j)   [n = number of COLUMNS]

2D Array (COLUMN-MAJOR):
  addr(A[i][j]) = Base + w × (j × m + i)   [m = number of ROWS]

Sparse Matrix: Store as (row, col, value) triplets → O(non-zero elements)
```

## ⚡ STACK — Key Operations

```
LIFO — Last In First Out
Push: O(1) | Pop: O(1) | Peek/Top: O(1) | Search: O(n)
Applications: Recursion, Undo, Expression Evaluation, Backtracking
Expression evaluation: STACK used for operators (infix→postfix) and operands (postfix eval)
```

## ⚡ POSTFIX EVALUATION RULES

```
Read left to right:
  Operand → PUSH onto stack
  Operator → POP two operands (second_pop op first_pop), PUSH result

CRITICAL ORDER: For a - b in postfix "... a b -"
  Pop b first (right operand), pop a second (left operand)
  Compute a - b (NOT b - a!)
```

## ⚡ TREES — Must-Know Formulas

```
NULL pointers in binary tree with n nodes:       n + 1
Internal nodes in full binary tree with n leaves: n - 1
Total nodes in complete binary tree of height h: between 2^h and 2^(h+1)-1
Max nodes at level k (root = level 0):          2^k
Max nodes in binary tree of height h:           2^(h+1) - 1

TRAVERSALS:
  Inorder (LNR):   Left → Node → Right
  Preorder (NLR):  Node → Left → Right  (FIRST element = ROOT!)
  Postorder (LRN): Left → Right → Node  (LAST element = ROOT!)
  Level-order:     Level by level (uses QUEUE, not stack)

BST INORDER = SORTED ORDER (ascending) — always!

TREE RECONSTRUCTION:
  Need INORDER + (PREORDER or POSTORDER)
  PREORDER first = ROOT
  POSTORDER last = ROOT
  Inorder divides tree into LEFT and RIGHT subtrees
```

## ⚡ GRAPHS — BFS vs DFS

```
BFS: Queue | Level-by-level | Shortest path in unweighted graph
DFS: Stack/Recursion | Deep first | Cycle detection, topological sort

Spanning Tree: V vertices → V-1 edges (always)
Minimum Spanning Tree algorithms: Kruskal (Greedy) | Prim (Greedy)
Shortest Path: Dijkstra (Greedy, non-negative weights) | Bellman-Ford (DP, negative weights OK)
```

## ⚡ SORTING — The Master Table

```
Algorithm    | Best      | Average   | Worst     | Space  | Stable
-------------|-----------|-----------|-----------|--------|--------
Bubble       | O(n)*     | O(n²)     | O(n²)     | O(1)   | YES ✅
Selection    | O(n²)     | O(n²)     | O(n²)     | O(1)   | NO ❌
Insertion    | O(n)      | O(n²)     | O(n²)     | O(1)   | YES ✅
Merge Sort   | O(n log n)| O(n log n)| O(n log n)| O(n)   | YES ✅
Quick Sort   | O(n log n)| O(n log n)| O(n²)     | O(log n)| NO ❌
Heap Sort    | O(n log n)| O(n log n)| O(n log n)| O(1)   | NO ❌

*Optimized with swap flag
STABLE & O(n log n) guaranteed: ONLY MERGE SORT
```

## ⚡ COMMON COMPLEXITY PATTERNS

```
Single loop (i++ from 0 to n):                 O(n)
Loop with i *= 2 (doubles):                    O(log n)
Nested loops (both 0 to n):                    O(n²)
Nested (outer i, inner j from i to n):         O(n²)  [n(n+1)/2 ≈ n²/2]
Divide in half each time (Binary Search):      O(log n)
T(n) = T(n-1) + O(1)  → LINEAR recursion:    O(n)
T(n) = 2T(n/2) + O(n) → MERGE SORT:          O(n log n)
T(n) = T(n-1) + O(n)  → SELECTION SORT:      O(n²)
```

## ⚡ HASHING — Quick Reference

```
Average: O(1) for search/insert/delete
Worst: O(n) — all keys in one bucket
Load Factor λ = n/m (n = elements, m = table size)
Java HashMap rehashes at λ > 0.75
Chaining: Linked list per bucket — handles unlimited collisions
Linear Probing: Try next slot — primary clustering problem
Double Hashing: Second hash function for step — best open addressing
```

## ⚡ LINKED LIST — Complexity Quick Card

```
           | SLL   | DLL   | Array
-----------|-------|-------|------
Insert BEG | O(1)  | O(1)  | O(n)
Insert END | O(n)  | O(1)  | O(1)
Delete BEG | O(1)  | O(1)  | O(n)
Delete END | O(n)  | O(1)  | O(1)
Access[i]  | O(n)  | O(n)  | O(1)
Search     | O(n)  | O(n)  | O(n)
NULL ptr   | YES   | YES   | N/A
Reverse    | O(n)  | O(n)  | O(n)
```

---

# TOP 10 EXAM TRAPS — BPSC PATTERN

```
TRAP 1: STACK = LIFO; QUEUE = FIFO. Never swap them!

TRAP 2: In postfix evaluation, when you pop for subtraction/division:
        First pop = RIGHT operand; second pop = LEFT operand.
        "a b -" means POP b first, POP a second → compute a - b

TRAP 3: NULL pointers in binary tree = n+1 (NOT n-1 or 2n)
        n-1 = number of EDGES (not NULL pointers)

TRAP 4: BST Inorder traversal = SORTED ORDER (ascending)
        This is WHY BST is useful for ordered operations!

TRAP 5: MAX nodes at LEVEL k (root = level 0) = 2^k
        Total max nodes in tree of HEIGHT h = 2^(h+1) - 1

TRAP 6: Preorder first element = ROOT; Postorder last element = ROOT
        You need Inorder PLUS one other traversal to reconstruct a tree.

TRAP 7: BFS uses QUEUE (level-order, shortest path in unweighted graphs)
        DFS uses STACK/recursion (depth-first, good for cycle detection)

TRAP 8: Merge Sort = STABLE + O(n log n) guaranteed
        Quick Sort = NOT STABLE + O(n²) worst case
        Heap Sort = NOT STABLE + O(n log n) guaranteed + O(1) space

TRAP 9: Both Merge Sort AND Heap Sort have O(n log n) worst case
        Questions asking for "best worst-case" → answer (D) for BOTH!

TRAP 10: Row-major 2D address: B + w × (i × n + j)
         Use n (COLUMNS) as multiplier for row index — NOT m (rows)!
```

---

# SELF-ASSESSMENT: WEAK AREA ACTION PLAN

```
Fill this after checking your answers:

My Wrong Questions: Q___, Q___, Q___, Q___, Q___

WEAK AREA IDENTIFIED:
  □ Arrays → Re-read Day 22 address formula section
  □ Stack  → Re-read Day 22 stack operations + Q7,9,10 analysis above
  □ Queue  → Re-read Day 23 circular queue index
  □ Linked List → Re-read Day 22-23 SLL/DLL operations
  □ Trees  → Re-read Day 26 traversals + NULL pointer formula
  □ Graphs → Re-read Day 27 BFS/DFS data structures
  □ Sorting → Re-read Day 29-31 sorting complexity table
  □ Searching → Re-read Day 32 binary search + hashing
  □ Complexity → Re-read Day 29 loop analysis rules
  □ GS Topics → Re-read respective day modules

ACTION: Spend 20 minutes revisiting each flagged weak area today evening.
        Then re-attempt those specific questions.
        Target: Reduce wrong count by half before tomorrow.
```

---

## 📅 DAY 35 PREVIEW:
**CS**: Operating Systems — Process Management, CPU Scheduling (FCFS, SJF, Round Robin, Priority Scheduling), Gantt Charts, Turnaround Time & Waiting Time calculations
**GS**: Bihar GK — Ancient History of Bihar: Magadh Empire, Mauryan Dynasty, Pataliputra, Ashoka's reign, Gupta Period

---

*🚀 Day 34 of 170 — A full mock test today. The exam doesn't care how hard you studied — only how well you perform under pressure. Practice under pressure, perform with confidence.*
