# 📅 DAY 32 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## 🎯 CS: Searching Algorithms (Linear, Binary, Jump) + Hashing
## 🌍 GS: Nobel Prize Winners + Important National & International Awards

> **Target:** Score 25/25 in CS + 25/25 in GS | **Exam Readiness: TOPPER MODE**
> **Day 32 of 170 | Phase 1 — Foundation | Week 5 — Algorithms**

---

# ═══════════════════════════════════════════════════════
# 🖥️ PART A: COMPUTER SCIENCE
## SEARCHING ALGORITHMS + HASHING
### Linear Search | Binary Search | Jump Search | Hashing & Hash Tables
# ═══════════════════════════════════════════════════════

---

## 📖 CS SECTION 1: WHY SEARCHING MATTERS

Searching is the most fundamental operation in computing.
Every database query, every website lookup, every autocomplete uses searching.

```
SEARCHING ALGORITHMS LANDSCAPE:

  ┌────────────────────────────────────────────────────────┐
  │              SEARCHING ALGORITHMS                      │
  ├─────────────────────────┬──────────────────────────────┤
  │  Sequential / Linear    │  Interval / Divide-Based     │
  │  ─────────────────────  │  ──────────────────────────  │
  │  • Linear Search O(n)   │  • Binary Search O(log n)    │
  │    (works on unsorted)  │    (needs SORTED array)      │
  │                         │  • Jump Search O(√n)         │
  │                         │  • Interpolation Search      │
  │                         │  • Exponential Search        │
  ├─────────────────────────┴──────────────────────────────┤
  │              HASHING — O(1) Average Case               │
  │  (neither sequential nor interval — uses hash function)│
  └────────────────────────────────────────────────────────┘

WHEN TO USE WHAT:
  Unsorted data             → Linear Search
  Sorted array, one search  → Binary Search
  Sorted array, many search → Binary Search
  Frequent insert/delete/search → Hash Table
```

---

## 📖 CS SECTION 2: LINEAR SEARCH — COMPLETE ANALYSIS

### 💡 Core Idea
> **"Check EACH element one by one from start to end until the target is found or all elements are checked."**

### Step-by-Step Example

```
Array: [64, 34, 25, 12, 22, 11, 90]   Target: 22

Step 1: Check arr[0] = 64  →  64 ≠ 22  → Continue
Step 2: Check arr[1] = 34  →  34 ≠ 22  → Continue
Step 3: Check arr[2] = 25  →  25 ≠ 22  → Continue
Step 4: Check arr[3] = 12  →  12 ≠ 22  → Continue
Step 5: Check arr[4] = 22  →  22 = 22  → FOUND! ✓ Return index 4

If target was 99:
  Check all 7 elements → NOT FOUND (return -1)
```

### Algorithm
```
LinearSearch(arr, n, target):
  for i = 0 to n-1:
    if arr[i] == target:
      return i          ← found at index i
  return -1             ← not found
```

### Complexity Analysis

```
┌────────────────┬───────────────────────────────────────────┐
│ Case           │ Complexity                                │
├────────────────┼───────────────────────────────────────────┤
│ Best Case      │ O(1) — target is at FIRST position       │
│ Average Case   │ O(n) — target somewhere in middle        │
│ Worst Case     │ O(n) — target is LAST or NOT PRESENT     │
│ Space          │ O(1) — no extra space needed             │
├────────────────┼───────────────────────────────────────────┤
│ Sorted needed? │ NO ✓ — works on ANY array                │
│ Works on LL?   │ YES ✓ — sequential access                │
└────────────────┴───────────────────────────────────────────┘
```

### When is Linear Search PREFERRED?
```
Use Linear Search when:
  ✓ Array is small (n < 10–20)
  ✓ Array is UNSORTED (can't use binary search)
  ✓ Only ONE search needed (not worth sorting first)
  ✓ Data structure doesn't support random access (linked list)
  ✓ Searching for all occurrences (not just first)
```

---

## 📖 CS SECTION 3: BINARY SEARCH — DEEP DIVE

### 💡 Core Idea
> **"Compare target with the MIDDLE element. If equal → found. If smaller → search LEFT half. If larger → search RIGHT half. Repeat until found or search space is empty."**

### CRITICAL PREREQUISITE
```
⚠️  BINARY SEARCH REQUIRES SORTED ARRAY  ⚠️
    This is the MOST ASKED BPSC TRE fact about Binary Search!
```

### Step-by-Step Example

```
Sorted Array: [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
Indices:        0  1  2   3   4   5   6   7   8   9
Target: 23

PASS 1:
  low=0, high=9
  mid = (0+9)/2 = 4
  arr[4] = 16
  23 > 16 → Search RIGHT half
  low = mid+1 = 5

  [2, 5, 8, 12, 16, | 23, 38, 56, 72, 91]
                      ↑──────────────────↑
                     low=5              high=9

PASS 2:
  low=5, high=9
  mid = (5+9)/2 = 7
  arr[7] = 56
  23 < 56 → Search LEFT half
  high = mid-1 = 6

  [23, 38, 56, ...]
   ↑────↑
  low=5 high=6

PASS 3:
  low=5, high=6
  mid = (5+6)/2 = 5
  arr[5] = 23
  23 = 23 → FOUND at index 5! ✓

Total comparisons: 3 (for n=10, log₂(10) ≈ 3.3)
```

### Algorithm — Iterative Version (Preferred)
```
BinarySearch_Iterative(arr, n, target):
  low = 0
  high = n - 1
  while low <= high:
    mid = (low + high) / 2      ← floor division
    if arr[mid] == target:
      return mid                 ← FOUND
    else if arr[mid] < target:
      low = mid + 1              ← search RIGHT
    else:
      high = mid - 1             ← search LEFT
  return -1                      ← NOT FOUND
```

### Algorithm — Recursive Version
```
BinarySearch_Recursive(arr, low, high, target):
  if low > high:
    return -1                    ← base case: not found
  mid = (low + high) / 2
  if arr[mid] == target:
    return mid
  else if arr[mid] < target:
    return BinarySearch_Recursive(arr, mid+1, high, target)
  else:
    return BinarySearch_Recursive(arr, low, mid-1, target)
```

### Complexity Analysis

```
┌────────────────┬────────────────────────────────────────────┐
│ Case           │ Complexity                                 │
├────────────────┼────────────────────────────────────────────┤
│ Best Case      │ O(1) — target is at MIDDLE position       │
│ Average Case   │ O(log n)                                   │
│ Worst Case     │ O(log n) — target not present/at end      │
│ Space (iter.)  │ O(1) — iterative version                  │
│ Space (recur.) │ O(log n) — recursion stack depth          │
├────────────────┼────────────────────────────────────────────┤
│ Sorted needed? │ YES ⚠️ — MANDATORY prerequisite           │
└────────────────┴────────────────────────────────────────────┘
```

### Why O(log n)? — Visual Proof

```
Each step HALVES the search space:

n elements → n/2 → n/4 → n/8 → ... → 1

After k steps: n / 2^k = 1
Therefore: k = log₂(n)

For n = 1000: log₂(1000) ≈ 10 steps  (vs 1000 for linear!)
For n = 1,000,000: log₂(10⁶) ≈ 20 steps (vs 1,000,000 for linear!)
```

### 🔥 PYQ TRAPS on Binary Search

```
TRAP 1: "Binary search is O(1)" → WRONG. O(log n) worst case.
TRAP 2: "Binary search works on any array" → WRONG. Needs SORTED.
TRAP 3: "Recursive binary search uses O(1) space" → WRONG. O(log n) stack.
TRAP 4: "Binary search beats hashing" → WRONG. Hash Table: O(1) avg.
CORRECT: Binary search = O(log n), Hash Table = O(1) average for search.
```

---

## 📖 CS SECTION 4: JUMP SEARCH — EXAM BONUS TOPIC

### 💡 Core Idea
> **"Jump ahead by √n steps. Once you overshoot the target, do Linear Search backwards in that block."**

```
Array (sorted): [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
n = 12, √n ≈ 3 (block size = 3)
Target: 55

JUMP PHASE:
  Check arr[0] = 0   → 0 < 55 → jump
  Check arr[3] = 2   → 2 < 55 → jump
  Check arr[6] = 8   → 8 < 55 → jump
  Check arr[9] = 34  → 34 < 55 → jump
  Check arr[12] → OUT OF BOUNDS → stop jumping

LINEAR SEARCH PHASE:
  Search from arr[9] to arr[11]:
  arr[9]=34, arr[10]=55 → FOUND at index 10! ✓
```

### Complexity: O(√n)
```
√n < n but √n > log n
O(log n) < O(√n) < O(n)
Binary Search faster, but Jump Search works for some specific cases
(e.g., when backward step is expensive)
```

---

## 📖 CS SECTION 5: HASHING — THE O(1) SEARCH TECHNIQUE

### 💡 Core Idea
> **"Use a HASH FUNCTION to convert a key into an array INDEX. Store the value at that index. To search, compute the same index and retrieve directly — no scanning needed!"**

This gives **O(1) average** for Insert, Delete, Search — the FASTEST possible!

### How Hashing Works

```
HASH FUNCTION: h(key) = key % TABLE_SIZE

Example: TABLE_SIZE = 7, Insert keys: [50, 700, 76, 85, 92, 73, 101]

h(50)  = 50  % 7 = 1    → Store 50  at index 1
h(700) = 700 % 7 = 0    → Store 700 at index 0
h(76)  = 76  % 7 = 6    → Store 76  at index 6
h(85)  = 85  % 7 = 1    → COLLISION! (1 already has 50)
h(92)  = 92  % 7 = 1    → COLLISION! (1 already has 50)
h(73)  = 73  % 7 = 3    → Store 73  at index 3
h(101) = 101 % 7 = 3    → COLLISION! (3 already has 73)

HASH TABLE (before collision handling):
  Index: [0]    [1]    [2]   [3]    [4]   [5]   [6]
  Value: [700]  [50]   [ ]  [73]    [ ]   [ ]   [76]
                 ↑ where do 85 and 92 go? → COLLISION PROBLEM!
```

---

## 📖 CS SECTION 6: HASH COLLISION — RESOLUTION TECHNIQUES

A **collision** occurs when two different keys hash to the SAME index.

### Technique 1: CHAINING (Separate Chaining)

```
IDEA: Each index holds a LINKED LIST of all keys that hash to it.

TABLE_SIZE = 7, Keys: [50, 700, 76, 85, 92, 73, 101]

Index  |  Chain
──────────────────────────────
  0    →  [700] → NULL
  1    →  [50] → [85] → [92] → NULL   (all hash to 1)
  2    →  NULL
  3    →  [73] → [101] → NULL         (both hash to 3)
  4    →  NULL
  5    →  NULL
  6    →  [76] → NULL

ADVANTAGE:
  ✓ Simple to implement
  ✓ Table never "full" (can always add to chain)
  ✓ Deletion is easy

DISADVANTAGE:
  ✗ Extra memory for pointers in linked list
  ✗ Cache performance poor (linked list not contiguous)
  ✗ Worst case O(n) if all keys hash to same slot
```

### Technique 2: OPEN ADDRESSING (Linear Probing)

```
IDEA: All elements stored IN the hash table itself.
      If index is occupied, probe NEXT available slot.

LINEAR PROBING: h(key, i) = (h(key) + i) % TABLE_SIZE
                where i = probe number (0, 1, 2, ...)

TABLE_SIZE = 7, Insert: 50, 700, 76, 85, 92, 73, 101

h(50)  = 1 → Index 1 empty → store 50
h(700) = 0 → Index 0 empty → store 700
h(76)  = 6 → Index 6 empty → store 76
h(85)  = 1 → Index 1 OCCUPIED (50)
           → try (1+1)%7 = 2 → empty → store 85
h(92)  = 1 → Index 1 OCCUPIED (50)
           → try 2 → OCCUPIED (85)
           → try 3 → empty → store 92
h(73)  = 3 → Index 3 OCCUPIED (92)
           → try 4 → empty → store 73
h(101) = 3 → Index 3 OCCUPIED (92)
           → try 4 OCCUPIED (73) → try 5 → store 101

FINAL TABLE:
  [0]=700, [1]=50, [2]=85, [3]=92, [4]=73, [5]=101, [6]=76

PROBLEM: PRIMARY CLUSTERING — keys pile up in clusters
         causing longer probe sequences
```

### Technique 3: QUADRATIC PROBING

```
h(key, i) = (h(key) + i²) % TABLE_SIZE

Probes: +1², +2², +3², ... = +1, +4, +9, ...
ADVANTAGE: Reduces primary clustering
DISADVANTAGE: Secondary clustering still possible
```

### Technique 4: DOUBLE HASHING

```
h(key, i) = (h1(key) + i × h2(key)) % TABLE_SIZE

Uses SECOND hash function as step size
ADVANTAGE: Best uniform distribution, no clustering
DISADVANTAGE: More computation needed
```

---

## 📖 CS SECTION 7: LOAD FACTOR — THE CRITICAL METRIC

```
LOAD FACTOR (α) = n / m

Where:
  n = number of elements stored in hash table
  m = total number of slots (table size)

Examples:
  n=7, m=10 → α = 0.7 (70% full)
  n=10, m=10 → α = 1.0 (100% full — resize needed!)
  n=15, m=10 → α = 1.5 (ONLY possible with chaining)

SIGNIFICANCE OF LOAD FACTOR:
  α close to 0: Table mostly empty, waste of memory
  α = 0.7:      Generally IDEAL for open addressing
  α > 0.7:      Performance DEGRADES significantly
  α > 1.0:      Only possible with CHAINING
                (impossible with open addressing)

REHASHING:
  When α exceeds threshold → create LARGER table
  (typically 2× size) → re-insert all elements
  Cost of rehashing: O(n)
```

---

## 📖 CS SECTION 8: HASH TABLE COMPLEXITY ANALYSIS

```
┌───────────────────┬────────────────┬────────────────────────┐
│ Operation         │ Average Case   │ Worst Case             │
├───────────────────┼────────────────┼────────────────────────┤
│ Search            │ O(1)           │ O(n) — all at one slot │
│ Insert            │ O(1)           │ O(n)                   │
│ Delete            │ O(1)           │ O(n)                   │
├───────────────────┼────────────────┼────────────────────────┤
│ Space             │ O(n)           │ O(n)                   │
└───────────────────┴────────────────┴────────────────────────┘

WHY O(1) AVERAGE?
  With a good hash function and low load factor (α ≤ 0.7),
  expected number of collisions per operation is bounded by
  a constant → O(1) expected time.

WHY O(n) WORST CASE?
  If ALL n keys hash to the same slot → chaining becomes
  a list of n elements → O(n) to search through.
```

---

## 📖 CS SECTION 9: HASH FUNCTIONS — PROPERTIES & EXAMPLES

### Properties of a Good Hash Function

```
IDEAL HASH FUNCTION:
  1. DETERMINISTIC: Same key ALWAYS produces same hash
  2. UNIFORM: Keys spread evenly across all indices
  3. FAST: O(1) to compute
  4. MINIMIZE COLLISIONS: Different keys → different indices

COMMON HASH FUNCTIONS:
  1. Division Method:    h(k) = k % m     ← most common
  2. Multiplication:    h(k) = ⌊m(kA mod 1)⌋  (A ≈ 0.618)
  3. Mid-Square:        Square the key, take middle digits
  4. Folding:           Split key into parts, add them

CHOOSING TABLE SIZE:
  → Use PRIME numbers as table size
  → Reduces clustering and improves uniformity
  → Example: Use 7, 11, 13, 17, 19 (not 8, 10, 12)
```

---

## 📖 CS SECTION 10: SEARCH ALGORITHMS — MASTER COMPARISON TABLE

```
┌──────────────────┬──────────┬──────────┬──────────┬────────┬──────────────┐
│ Algorithm        │ Best     │ Average  │ Worst    │ Space  │ Sorted?      │
├──────────────────┼──────────┼──────────┼──────────┼────────┼──────────────┤
│ Linear Search    │ O(1)     │ O(n)     │ O(n)     │ O(1)   │ NOT needed   │
│ Binary Search    │ O(1)     │ O(log n) │ O(log n) │ O(1)   │ REQUIRED ⚠️ │
│ Jump Search      │ O(1)     │ O(√n)    │ O(√n)    │ O(1)   │ REQUIRED ⚠️ │
│ Hash Table       │ O(1)     │ O(1)     │ O(n)     │ O(n)   │ NOT needed   │
├──────────────────┼──────────┼──────────┼──────────┼────────┼──────────────┤
│ BST Search       │ O(log n) │ O(log n) │ O(n)     │ O(1)   │ BST property │
│ Balanced BST     │ O(log n) │ O(log n) │ O(log n) │ O(1)   │ AVL/RB Tree  │
└──────────────────┴──────────┴──────────┴──────────┴────────┴──────────────┘

EXAM RULE: "For FREQUENT insert/delete/search → Hash Table (O(1) avg)"
           "For SORTED data with one search → Binary Search (O(log n))"
           "For unsorted, small data → Linear Search"
```

---

## 📖 CS SECTION 11: REAL-WORLD APPLICATIONS OF HASHING

```
WHERE HASHING IS USED IN REAL LIFE:

  1. DATABASES:
     → Index lookup (find row by primary key in O(1))
     → HashMap in Java, dict in Python

  2. PASSWORD STORAGE:
     → Passwords stored as HASHES (MD5, SHA-256)
     → Never store plain passwords!
     → Even server can't reverse the hash

  3. COMPILERS:
     → Symbol tables (variable name → memory address)

  4. CACHES:
     → CPU cache, DNS cache use hash tables

  5. BLOCKCHAIN:
     → SHA-256 hash for block verification

  6. DUPLICATE DETECTION:
     → Check if element already seen in O(1)

  7. SPELL CHECKERS:
     → Dictionary stored as hash set for O(1) lookup

  8. PYTHON dict / JAVA HashMap:
     → Underlying implementation = Hash Table
```

---

## 📖 CS SECTION 12: TRICKY PYQ PATTERNS

### Pattern 1: Hash Table vs Binary Search
```
Q: "Which data structure gives O(1) average for search, insert, delete?"
A: Hash Table (not Binary Search Tree, not array)

Q: "Binary Search is better than Hash Table for searching" → FALSE
   Hash Table: O(1) avg | Binary Search: O(log n)
   Exception: Hash Table has O(n) WORST case; BST O(log n) guaranteed
```

### Pattern 2: Collision Resolution Order
```
Q: "Which collision resolution technique keeps all data IN the table?"
A: Open Addressing (Linear Probing, Quadratic Probing, Double Hashing)
   Chaining uses EXTERNAL linked lists (outside the table)
```

### Pattern 3: Load Factor Threshold
```
Q: "When should a hash table be rehashed?"
A: When load factor exceeds ~0.7 for open addressing
   For chaining, higher load factors (>1) are tolerable
```

### Pattern 4: Linear Probing vs Chaining
```
Q: "Which collision resolution has PRIMARY CLUSTERING problem?"
A: Linear Probing

Q: "Which allows load factor > 1?"
A: Chaining (not open addressing)
```

---

# ═══════════════════════════════════════════════════════
# 📝 CS PRACTICE QUESTIONS — 25 MCQs
## (Answers consolidated at END — attempt ALL before checking!)
# ═══════════════════════════════════════════════════════

---

**Q1.** What is the WORST-CASE time complexity of Binary Search?

(A) O(1)
(B) O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q2.** Binary Search can only be applied when the input array is:

(A) Stored in a linked list
(B) Unsorted
(C) Sorted
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the AVERAGE-CASE time complexity of searching in a Hash Table with a good hash function?

(A) O(log n)
(B) O(n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q4.** In Linear Search, the WORST CASE occurs when:

(A) The target is at the first position
(B) The target is at the middle position
(C) The target is at the last position OR not present in the array
(D) More than one of the above
(E) None of the above

---

**Q5.** Which searching algorithm does NOT require the input array to be sorted?

(A) Binary Search
(B) Jump Search
(C) Linear Search
(D) More than one of the above
(E) None of the above

---

**Q6.** A HASH COLLISION occurs when:

(A) Two identical keys are inserted
(B) The hash table becomes full
(C) Two DIFFERENT keys produce the SAME hash value (index)
(D) More than one of the above
(E) None of the above

---

**Q7.** In the CHAINING method of collision resolution, each hash table slot contains:

(A) A fixed-size array of overflow elements
(B) A linked list of all elements hashing to that slot
(C) Only one element and rejects further inserts
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the LOAD FACTOR of a hash table?

(A) The ratio of successful searches to total searches
(B) The ratio of number of elements (n) to table size (m): α = n/m
(C) The number of collisions per insertion
(D) More than one of the above
(E) None of the above

---

**Q9.** Binary Search on an array of n=1024 elements requires at most how many comparisons in the worst case?

(A) 512
(B) 1024
(C) 10
(D) More than one of the above
(E) None of the above

---

**Q10.** Which collision resolution technique stores ALL elements INSIDE the hash table (no external data structures)?

(A) Chaining (Separate Chaining)
(B) Open Addressing (Linear Probing / Quadratic Probing)
(C) Bucket Hashing
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following is TRUE about Linear Probing as a collision resolution technique?

(A) It eliminates all collisions completely
(B) It uses linked lists to handle overflow
(C) It suffers from PRIMARY CLUSTERING (consecutive occupied slots)
(D) More than one of the above
(E) None of the above

---

**Q12.** For the hash function h(k) = k % 7 with table size 7, what is the hash value of key = 50?

(A) 5
(B) 7
(C) 1
(D) More than one of the above
(E) None of the above

---

**Q13.** The RECURSIVE version of Binary Search has which SPACE COMPLEXITY?

(A) O(1) — same as iterative version
(B) O(n) — stores all elements in stack
(C) O(log n) — recursion call stack depth
(D) More than one of the above
(E) None of the above

---

**Q14.** Which data structure is MOST EFFICIENT for frequent INSERT, DELETE, and SEARCH operations (all three)?

(A) Sorted Array
(B) Binary Search Tree (unbalanced)
(C) Hash Table
(D) More than one of the above
(E) None of the above

---

**Q15.** Jump Search has a time complexity of:

(A) O(n)
(B) O(log n)
(C) O(√n)
(D) More than one of the above
(E) None of the above

---

**Q16.** In Binary Search, the middle index is calculated as mid = (low + high) / 2. For low=3 and high=9, what is mid?

(A) 5
(B) 6
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q17.** DOUBLE HASHING is a collision resolution technique where:

(A) The table size is doubled on every collision
(B) A second hash function determines the probe step size
(C) Two hash tables are used simultaneously
(D) More than one of the above
(E) None of the above

---

**Q18.** What is the WORST-CASE time complexity of searching in a Hash Table?

(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q19.** For which of the following data sizes would Linear Search and Binary Search perform MOST SIMILARLY?

(A) n = 1,000,000
(B) n = 10,000
(C) n = 5 (very small array)
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following searching techniques has time complexity O(log n) in AVERAGE case?

(A) Linear Search
(B) Jump Search
(C) Binary Search
(D) More than one of the above
(E) None of the above

---

**Q21.** REHASHING in hash tables means:

(A) Changing the hash function completely
(B) Creating a larger table and re-inserting all elements
(C) Deleting all elements and restarting
(D) More than one of the above
(E) None of the above

---

**Q22.** In Open Addressing, the LOAD FACTOR can EXCEED 1.0.

(A) TRUE — open addressing can exceed load factor 1.0
(B) FALSE — load factor > 1 is impossible in open addressing
(C) Only possible with prime table sizes
(D) More than one of the above
(E) None of the above

---

**Q23.** Binary Search is preferred over Linear Search when:

(A) Array is unsorted and insertion is frequent
(B) Array is sorted and repeated searches are performed on large data
(C) Only one element needs to be found in an unsorted array
(D) More than one of the above
(E) None of the above

---

**Q24.** Which property makes a good hash function?

(A) It should map all keys to the same index (for easy lookup)
(B) It should be slow to compute to increase security
(C) It should distribute keys uniformly across the hash table
(D) More than one of the above
(E) None of the above

---

**Q25.** TRICKY PYQ: You have a SORTED array and need to search for a value 1 million times. Which is the BEST approach?

(A) Linear Search 1 million times — O(n) per search
(B) Binary Search 1 million times — O(log n) per search
(C) Build a Hash Table first, then search — O(1) per search after O(n) build
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🌍 PART B: GENERAL STUDIES
## NOBEL PRIZE WINNERS + NATIONAL & INTERNATIONAL AWARDS
# ═══════════════════════════════════════════════════════

---

## 📖 GS SECTION 1: NOBEL PRIZE — COMPLETE OVERVIEW

### What is Nobel Prize?

```
NOBEL PRIZE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Founded by: Alfred Nobel (Swedish chemist/inventor of dynamite)
Will signed: November 27, 1895
First awarded: 1901
Administered by: Nobel Foundation, Stockholm, Sweden

6 CATEGORIES:
  1. Physics
  2. Chemistry
  3. Physiology or Medicine
  4. Literature
  5. Peace
  6. Economic Sciences (added 1969 — NOT in original Nobel's will)
     Full name: Sveriges Riksbank Prize in Economic Sciences
               in Memory of Alfred Nobel

AWARDING BODIES:
  Physics:      Royal Swedish Academy of Sciences
  Chemistry:    Royal Swedish Academy of Sciences
  Medicine:     Karolinska Institute, Stockholm
  Literature:   Swedish Academy
  Peace:        Norwegian Nobel Committee (OSLO — different city!)
  Economics:    Royal Swedish Academy of Sciences

NOTE: Peace Prize is awarded in OSLO, Norway (NOT Stockholm)
      All others are in Stockholm, Sweden
```

---

## 📖 GS SECTION 2: INDIANS WHO WON NOBEL PRIZE

```
INDIANS / INDIAN-ORIGIN NOBEL LAUREATES:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. RABINDRANATH TAGORE (1913)
   Category: Literature
   First ASIAN to win Nobel Prize
   Work: "Gitanjali" (Song Offerings)
   Note: Also composed national anthems of India AND Bangladesh

2. C.V. RAMAN (1930)
   Category: Physics
   Discovery: Raman Effect (scattering of light)
   First ASIAN to win Nobel Prize in SCIENCE
   Anniversary: Feb 28 = National Science Day (India)

3. HARGOBIND KHORANA (1968)
   Category: Physiology/Medicine
   Nationality: Indian-born, US citizen
   Work: Genetic code interpretation

4. MOTHER TERESA (1979)
   Category: Peace
   Nationality: Albanian-born, worked in India (India citizen)
   Work: Charity work in Kolkata (Missionaries of Charity)

5. AMARTYA SEN (1998)
   Category: Economic Sciences
   Work: Welfare economics, poverty, famine theory
   "Development as Freedom" — famous book

6. V.S. NAIPAUL (2001)
   Category: Literature
   Nationality: Trinidad-born, Indian-origin
   Work: "A House for Mr Biswas"

7. SUBRAHMANYAN CHANDRASEKHAR (posthumous fame)
   Category: Physics (1983)
   Indian-born, US citizen
   Discovery: Chandrasekhar Limit (stellar evolution)
   NASA's Chandra X-ray Observatory named after him

8. ABHIJIT BANERJEE (2019)
   Category: Economic Sciences
   Nationality: Indian-born; Bengali from West Bengal
   Work: Experimental approach to alleviating global poverty
   Co-winner: Esther Duflo (wife), Michael Kremer
   NOTE: Most recent Indian-origin Nobel winner
```

---

## 📖 GS SECTION 3: RECENT NOBEL PRIZES (2023 & 2024)

### Nobel Prize 2023

```
PHYSICS 2023:
  Pierre Agostini, Ferenc Krausz, Anne L'Huillier
  For: Attosecond pulses of light (studying electron motion)

CHEMISTRY 2023:
  Moungi Bawendi, Louis Brus, Alexei Ekimov
  For: Discovery of quantum dots (used in LED displays, medical imaging)

MEDICINE 2023:
  Katalin Karikó & Drew Weissman
  For: mRNA modifications enabling COVID-19 vaccines (Pfizer-BioNTech, Moderna)

LITERATURE 2023:
  Jon Fosse (Norway)

PEACE 2023:
  Narges Mohammadi (Iran)
  For: Fight against oppression of women in Iran
  (received prize from prison!)

ECONOMICS 2023:
  Claudia Goldin (USA, Harvard)
  For: Women's labour market outcomes and gender pay gap research
  First woman to win solo Economics Nobel
```

### Nobel Prize 2024

```
PHYSICS 2024:
  John Hopfield & Geoffrey Hinton
  For: Foundational discoveries enabling machine learning (neural networks)
  NOTE: Geoffrey Hinton = "Godfather of AI"

CHEMISTRY 2024:
  David Baker, Demis Hassabis, John Jumper
  For: Computational protein design (AlphaFold AI — predicting protein structure)
  NOTE: Demis Hassabis = CEO of Google DeepMind

MEDICINE 2024:
  Victor Ambros & Gary Ruvkun
  For: Discovery of microRNA (gene regulation)

LITERATURE 2024:
  Han Kang (South Korea)
  First South Korean and first Asian woman to win Literature Nobel

PEACE 2024:
  Nihon Hidankyo (Japan)
  Atomic bomb survivors' organisation from Hiroshima & Nagasaki

ECONOMICS 2024:
  Daron Acemoglu, Simon Johnson, James A. Robinson
  For: Studies on institutions and prosperity (Why Nations Fail concept)
```

---

## 📖 GS SECTION 4: BHARAT RATNA — INDIA'S HIGHEST CIVILIAN AWARD

```
BHARAT RATNA:
━━━━━━━━━━━━━
Established: 1954
Highest civilian honour in India
Given for: Exceptional service to nation in any field
Awarded by: President of India
Max per year: 3 (but not mandatory to give each year)
NOT necessarily an Indian citizen (can be foreign)

SHAPE: Pipal leaf with sun + state emblem

RECENT RECIPIENTS:
  2024: Lal Krishna Advani (BJP leader)
        Karpoori Thakur (posthumous) — Bihar's former CM!
        M.S. Swaminathan (posthumous) — Father of Green Revolution
        Chaudhary Charan Singh (posthumous)
        P.V. Narasimha Rao (posthumous)

NOTABLE RECIPIENTS (Historical):
  → C. Rajagopalachari (1954) — first recipient
  → S. Radhakrishnan (1954) — philosopher, President
  → C.V. Raman (1954) — Nobel laureate
  → Jawaharlal Nehru (1955)
  → Indira Gandhi (1971)
  → Mother Teresa (1980)
  → M.G. Ramachandran (MGR) (1988) — film actor/politician
  → Dr. B.R. Ambedkar (1990, posthumous)
  → Nelson Mandela (1990) — foreign national
  → Atal Bihari Vajpayee (2015)
  → Madan Mohan Malaviya (2015, posthumous)

BIHAR CONNECTION: Karpoori Thakur (Jan Nayak) — Bihar's
  beloved CM who championed OBC reservations, received
  Bharat Ratna in 2024 (posthumous).
```

---

## 📖 GS SECTION 5: PADMA AWARDS

```
PADMA AWARDS (Three Categories):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PADMA VIBHUSHAN (2nd highest civilian award)
  → Exceptional and distinguished service
  → One step below Bharat Ratna

PADMA BHUSHAN (3rd highest civilian award)
  → Distinguished service of high order

PADMA SHRI (4th highest civilian award)
  → Distinguished service in any field

COMMON FACTS:
  → Announced on Republic Day (January 26)
  → Awarded in different fields: Art, Education, Literature,
     Science, Sports, Social Work, etc.
  → Any Indian citizen (or foreigner with India connection)
  → NRIs, PIOs can also receive
  → Posthumous awards allowed

IMPORTANT: Padma awards can be declined.
           M.S. Dhoni declined Padma Vibhushan initially.
```

---

## 📖 GS SECTION 6: GALLANTRY AWARDS (MILITARY)

```
MILITARY AWARDS (Wartime):
━━━━━━━━━━━━━━━━━━━━━━━━━━

PARAM VIR CHAKRA (PVC) — HIGHEST MILITARY HONOUR
  → "For most conspicuous bravery in presence of enemy"
  → Only given in WAR conditions
  → Total awarded: 21 (most posthumous)
  → Design: Vajra (Indra's weapon), Hindu/Buddhist motif
  → First recipient: Major Somnath Sharma (1947, posthumous)
  → Most famous: Abdul Hamid (1965 war, single-handedly
                 destroyed multiple Pakistani tanks)

MAHA VIR CHAKRA (MVC) — 2nd highest wartime award

VIR CHAKRA (VC) — 3rd highest wartime award

PEACETIME GALLANTRY:
  ASHOKA CHAKRA → Highest peacetime gallantry
  KIRTI CHAKRA → 2nd highest peacetime
  SHAURYA CHAKRA → 3rd highest peacetime

MEMORY: Wartime = Param, Maha, Vir Chakra
        Peacetime = Ashoka, Kirti, Shaurya Chakra
```

---

## 📖 GS SECTION 7: OTHER IMPORTANT AWARDS

### Jnanpith Award
```
JNANPITH AWARD:
  → India's HIGHEST LITERARY AWARD
  → Given for outstanding contribution to INDIAN literature
  → Given in one of the 22 Scheduled Languages
  → Established: 1961, first given: 1965
  → Award: ₹11 lakh + Vagdevi statuette
  → NOT for English works (must be in Indian language)

Notable recipients:
  → Mahadevi Verma (Hindi)
  → Ramdhari Singh Dinkar (Hindi) — Bihar's POET!
  → Nirala (Hindi)
  → Faiz Ahmed Faiz, Amrita Pritam, etc.
```

### Sahitya Akademi Award
```
SAHITYA AKADEMI:
  → National Academy of Letters
  → Founded: 1954
  → Annual awards for 24 languages (22 scheduled + English + Rajasthani)
  → For "most outstanding books of literary merit"
```

### Dada Saheb Phalke Award
```
DADA SAHEB PHALKE AWARD:
  → Highest award in Indian CINEMA
  → Given by Ministry of Information & Broadcasting
  → Dadasaheb Phalke = Father of Indian Cinema
  → Annual Filmfare-style but government award
  → Recent: Waheeda Rehman (2023), Mithun Chakraborty (2024)
```

---

## 📖 GS SECTION 8: INTERNATIONAL AWARDS

```
OSCAR (Academy Award):
  → Given by: Academy of Motion Picture Arts and Sciences (USA)
  → India's international submissions: Films for Foreign Film category
  → Indian wins:
    Bhanu Athaiya — 1983 (Costume Design, Gandhi film)
    AR Rahman — 2009 (Slumdog Millionaire: Original Score + Song)
    Resul Pookutty — 2009 (Slumdog: Sound Mixing)
    Guneet Monga — 2023 (The Elephant Whisperers — Documentary Short)
    Kartiki Gonsalves — 2023 (The Elephant Whisperers)

MAN BOOKER PRIZE:
  → For best novel written in English, published in UK
  → Indian winners:
    Salman Rushdie — 1981 (Midnight's Children)
    Arundhati Roy — 1997 (The God of Small Things)
    Kiran Desai — 2006 (The Inheritance of Loss)
    Aravind Adiga — 2008 (The White Tiger)

GRAMMY AWARD:
  → Music awards (USA), given by Recording Academy
  → AR Rahman: No Grammy win but Oscar winner

PULITZER PRIZE:
  → For journalism, literature, music (USA)
  → Gobind Behari Lal: First Indian-origin Pulitzer winner (1937)
```

---

## 📖 GS SECTION 9: SPORTS AWARDS (INDIA)

```
KHEL RATNA (formerly Rajiv Gandhi Khel Ratna):
  → India's HIGHEST SPORTS HONOUR
  → Renamed to Major Dhyan Chand Khel Ratna in 2021
  → First recipient: Viswanathan Anand (Chess, 1991-92)

ARJUNA AWARD:
  → For outstanding performance in sports (last 4 years)
  → Given since 1961

DRONACHARYA AWARD:
  → For outstanding COACHES
  → Given since 1985

DHYAN CHAND AWARD:
  → For lifetime contribution to sports
  → Named after legendary hockey player Major Dhyan Chand
  → Given since 2002

RASHTRIYA KHEL PROTSAHAN PURASKAR:
  → For corporates/NGOs promoting sports

TENZING NORGAY NATIONAL ADVENTURE AWARD:
  → For adventure sports achievement
```

---

## 📖 GS SECTION 10: BIHAR GK — AWARDS CONNECTION

```
BIHAR'S NOTABLE AWARD WINNERS:

BHARAT RATNA:
  → Karpoori Thakur (2024, posthumous) — Bihar's "Jan Nayak" CM
  → Dr. Rajendra Prasad — first President of India (from Bihar)
     Received Bharat Ratna 1962

JNANPITH AWARD (Bihar connection):
  → Ramdhari Singh Dinkar — "Rashmirathi", "Urvashi"
     National Poet of India; from Begusarai, Bihar
  → Phaniswarnath Renu — author of "Maila Aanchal" (Bihar's rural life)
     Did NOT win Jnanpith but Padma Shri

PARAM VIR CHAKRA (Bihar connection):
  → Captain Manoj Kumar Pandey (1999, Kargil, posthumous)
     From Sitapur, but honorary mention in Bihar Army tradition

SCIENCE AWARDS:
  → Aryabhata — ancient Bihar mathematician/astronomer
     No modern Nobel but pioneered zero and algebra concepts

SPORTS:
  → Bihar has produced several Arjuna Award winners
     in archery (Jharkhand was part of Bihar until 2000)
```

---

# ═══════════════════════════════════════════════════════
# 📝 GS PRACTICE QUESTIONS — 25 MCQs
## (Answers consolidated at END — attempt ALL before checking!)
# ═══════════════════════════════════════════════════════

---

**Q26.** The Nobel Prize was established based on the will of:

(A) Alexander Graham Bell
(B) Albert Einstein
(C) Alfred Nobel (inventor of dynamite)
(D) More than one of the above
(E) None of the above

---

**Q27.** The Nobel Peace Prize is awarded in which city?

(A) Stockholm, Sweden
(B) Copenhagen, Denmark
(C) Oslo, Norway
(D) More than one of the above
(E) None of the above

---

**Q28.** Who was the FIRST ASIAN to win the Nobel Prize?

(A) C.V. Raman
(B) Rabindranath Tagore
(C) Amartya Sen
(D) More than one of the above
(E) None of the above

---

**Q29.** C.V. Raman won the Nobel Prize in Physics in 1930 for the discovery of:

(A) Nuclear fission
(B) Raman Effect (scattering of light)
(C) Theory of relativity
(D) More than one of the above
(E) None of the above

---

**Q30.** February 28 is celebrated as National Science Day in India to commemorate which event?

(A) Launch of India's first satellite Aryabhata
(B) C.V. Raman's announcement of the Raman Effect in 1928
(C) Birth anniversary of Homi J. Bhabha
(D) More than one of the above
(E) None of the above

---

**Q31.** Amartya Sen won the Nobel Prize in Economic Sciences in 1998. His work was primarily on:

(A) Game theory and Nash equilibrium
(B) Welfare economics, poverty, famine, and social choice theory
(C) Monetary policy and central banking
(D) More than one of the above
(E) None of the above

---

**Q32.** The 2024 Nobel Prize in Physics was awarded for contributions to:

(A) Discovery of quantum dots
(B) Attosecond light pulses
(C) Foundational discoveries enabling machine learning (neural networks)
(D) More than one of the above
(E) None of the above

---

**Q33.** India's HIGHEST CIVILIAN AWARD is:

(A) Padma Vibhushan
(B) Padma Shri
(C) Bharat Ratna
(D) More than one of the above
(E) None of the above

---

**Q34.** Bharat Ratna was conferred (posthumously) in 2024 to Bihar's former Chief Minister. Who was he?

(A) Jagannath Mishra
(B) Karpoori Thakur ("Jan Nayak")
(C) Laloo Prasad Yadav
(D) More than one of the above
(E) None of the above

---

**Q35.** The PARAM VIR CHAKRA is India's:

(A) Highest civilian award
(B) Highest peacetime gallantry award
(C) Highest wartime military gallantry award
(D) More than one of the above
(E) None of the above

---

**Q36.** India's HIGHEST LITERARY AWARD is:

(A) Sahitya Akademi Award
(B) Jnanpith Award
(C) Booker Prize
(D) More than one of the above
(E) None of the above

---

**Q37.** The Nobel Prize in Economic Sciences was NOT part of Alfred Nobel's original will. It was added later in which year?

(A) 1945
(B) 1969
(C) 1985
(D) More than one of the above
(E) None of the above

---

**Q38.** Abhijit Banerjee (Indian-origin) won the Nobel Prize in Economic Sciences in 2019. He is affiliated with which university?

(A) Harvard University, USA
(B) Massachusetts Institute of Technology (MIT), USA
(C) Oxford University, UK
(D) More than one of the above
(E) None of the above

---

**Q39.** The "Dada Saheb Phalke Award" is India's highest award in which field?

(A) Literature
(B) Sports
(C) Cinema
(D) More than one of the above
(E) None of the above

---

**Q40.** The Nobel Prize in Medicine 2023 was awarded to Katalin Karikó and Drew Weissman for:

(A) Discovery of CRISPR gene editing
(B) mRNA modifications enabling COVID-19 vaccine development
(C) Discovery of cancer immunotherapy
(D) More than one of the above
(E) None of the above

---

**Q41.** India's highest SPORTS honour (formerly Rajiv Gandhi Khel Ratna) was renamed in 2021 after which sports legend?

(A) Sachin Tendulkar
(B) Major Dhyan Chand (hockey)
(C) P.T. Usha
(D) More than one of the above
(E) None of the above

---

**Q42.** Who was the first recipient of the Rajiv Gandhi Khel Ratna Award (now Major Dhyan Chand Khel Ratna)?

(A) Sachin Tendulkar
(B) Prakash Padukone
(C) Viswanathan Anand (Chess)
(D) More than one of the above
(E) None of the above

---

**Q43.** Ramdhari Singh Dinkar, the famous Hindi poet from Bihar who wrote "Urvashi" and "Rashmirathi," received which prestigious award?

(A) Dada Saheb Phalke Award
(B) Jnanpith Award
(C) Bharat Ratna
(D) More than one of the above
(E) None of the above

---

**Q44.** The Nobel Peace Prize 2023 was awarded to Narges Mohammadi from which country?

(A) Afghanistan
(B) Iraq
(C) Iran
(D) More than one of the above
(E) None of the above

---

**Q45.** Booker Prize winner Arundhati Roy (1997) wrote which novel that won her the prize?

(A) Midnight's Children
(B) The God of Small Things
(C) The White Tiger
(D) More than one of the above
(E) None of the above

---

**Q46.** The 2024 Nobel Prize in Chemistry was related to which AI-powered technology?

(A) Quantum computing and qubit design
(B) Battery technology and lithium-ion
(C) Protein structure prediction (AlphaFold)
(D) More than one of the above
(E) None of the above

---

**Q47.** Which Indian films won the Oscar (Academy Award) for India?

(A) Lagaan (2002) — Best Foreign Film
(B) The Elephant Whisperers (2023) — Best Documentary Short
(C) RRR (2022) — Best Original Song (Naatu Naatu)
(D) More than one of the above
(E) None of the above

---

**Q48.** The ASHOKA CHAKRA is India's highest award for gallantry in which context?

(A) Wartime operations
(B) Peacetime gallantry / devotion to duty
(C) International peacekeeping missions
(D) More than one of the above
(E) None of the above

---

**Q49.** AR Rahman won two Academy Awards (Oscars) in 2009 for which film?

(A) Jai Ho
(B) Rang De Basanti
(C) Slumdog Millionaire
(D) More than one of the above
(E) None of the above

---

**Q50.** BPSC SPECIAL — Bihar's Dr. Rajendra Prasad, India's first President, received Bharat Ratna in:

(A) 1954 (the first year it was given)
(B) 1960
(C) 1962
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🔑 COMPLETE ANSWER KEY — DAY 32
## ATTEMPT ALL QUESTIONS FIRST!
# ═══════════════════════════════════════════════════════

---

## ✅ CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| **Q1** | **(C)** | Binary Search worst case = O(log n). Occurs when target is not present or at extreme end. NOT O(n) like linear search, NOT O(1) like hash table. |
| **Q2** | **(C)** | Binary Search REQUIRES sorted array — this is its fundamental prerequisite. Without sorting, the halving logic breaks down completely. |
| **Q3** | **(C)** | Hash Table average case = O(1) for search (also insert and delete). This assumes a good hash function and low load factor. |
| **Q4** | **(C)** | Linear Search worst case: target is at LAST index (checks all n elements) OR target is NOT present (checks all n elements and fails). Both give O(n). |
| **Q5** | **(C)** | Linear Search works on UNSORTED arrays. Binary Search and Jump Search REQUIRE sorted input. |
| **Q6** | **(C)** | Hash collision = two DIFFERENT keys produce the SAME hash index. NOT identical keys (those are duplicates, a different issue). |
| **Q7** | **(B)** | Chaining: each slot has a linked list. All keys that hash to the same index are stored in that slot's linked list. |
| **Q8** | **(B)** | Load Factor α = n/m where n = elements stored, m = table size. It measures how "full" the table is. |
| **Q9** | **(C)** | For n=1024: log₂(1024) = log₂(2¹⁰) = 10. Maximum 10 comparisons. Binary search is incredibly efficient for large n. |
| **Q10** | **(B)** | Open Addressing stores ALL elements in the hash table array itself (no external structures). Chaining uses external linked lists. |
| **Q11** | **(C)** | Linear Probing: when collision occurs, probe next consecutive slot. This creates PRIMARY CLUSTERING — long runs of occupied consecutive slots, degrading performance. |
| **Q12** | **(C)** | h(50) = 50 % 7 = 7×7=49, 50-49=1. So 50%7 = 1. |
| **Q13** | **(C)** | Recursive Binary Search: each recursive call adds to the call stack. Max recursion depth = log n (number of times we halve). So O(log n) space. |
| **Q14** | **(C)** | Hash Table: Insert O(1), Delete O(1), Search O(1) average. Sorted array: Insert O(n). BST unbalanced: O(n) worst. Hash Table wins for all three operations combined. |
| **Q15** | **(C)** | Jump Search time complexity = O(√n). It jumps in blocks of size √n. Slower than Binary Search O(log n) but faster than Linear O(n). |
| **Q16** | **(B)** | mid = (low + high) / 2 = (3 + 9) / 2 = 12 / 2 = 6. Integer division: 6. |
| **Q17** | **(B)** | Double Hashing: uses a SECOND hash function to determine the step size for probing. h(k,i) = (h1(k) + i×h2(k)) % m. Reduces clustering better than linear/quadratic. |
| **Q18** | **(C)** | Hash Table WORST case = O(n). Happens when ALL n elements hash to the same slot (pathological hash function or adversarial input). The chain has all n elements → O(n) search. |
| **Q19** | **(C)** | For n=5 (very small): Binary search does ≤ 3 comparisons; Linear does ≤ 5. Difference is trivial. For n=1,000,000 the difference is enormous (20 vs 1,000,000). |
| **Q20** | **(C)** | Binary Search = O(log n) in average and worst case. Linear = O(n). Jump = O(√n). Binary Search is the O(log n) one. |
| **Q21** | **(B)** | Rehashing: when load factor exceeds threshold, create a NEW larger table (usually 2× size), then RE-INSERT all existing elements using the new table's hash function. |
| **Q22** | **(B)** | FALSE. In Open Addressing, load factor CANNOT exceed 1.0 because there is a fixed number of slots and each slot holds exactly one element. When all m slots are full, no more inserts possible. Only Chaining allows α > 1. |
| **Q23** | **(B)** | Binary Search is preferred when: array is SORTED + searches are REPEATED on large data (O(log n) per search vs O(n) linear). Not beneficial for one-time search on small data. |
| **Q24** | **(C)** | Good hash function distributes keys UNIFORMLY across all slots — minimizing collisions and maintaining O(1) average performance. Should be fast O(1) to compute. |
| **Q25** | **(C)** | Best approach for 1 million searches: Build Hash Table first (O(n) one-time cost), then each of the 1 million searches is O(1). Total: O(n) + 1,000,000×O(1). Binary Search would be O(n log n) total (1M × log n). Hash Table wins for very frequent searches. |

---

## ✅ GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| **Q26** | **(C)** | Alfred Nobel — Swedish chemist who invented dynamite (patented 1867). His will (1895) established the prizes to counteract the destructive legacy of his inventions. |
| **Q27** | **(C)** | Nobel Peace Prize = Oslo, Norway. All other Nobel prizes (Physics, Chemistry, Medicine, Literature, Economics) = Stockholm, Sweden. This is a very frequent BPSC exam trap! |
| **Q28** | **(B)** | Rabindranath Tagore won Nobel Prize in Literature in 1913 — first Asian to win any Nobel Prize. C.V. Raman won in 1930 — first Asian in science category. |
| **Q29** | **(B)** | Raman Effect: when light passes through a transparent material, scattered light has different wavelengths. Used in Raman spectroscopy for identifying materials. |
| **Q30** | **(B)** | February 28, 1928: C.V. Raman announced the Raman Effect. National Science Day observed on Feb 28 since 1987 to honour this discovery. |
| **Q31** | **(B)** | Amartya Sen's work: welfare economics (how to measure social welfare), poverty measurement, capability approach, famine analysis (famines caused by distribution failure, not food shortage). |
| **Q32** | **(C)** | 2024 Physics Nobel: John Hopfield & Geoffrey Hinton for foundational discoveries enabling machine learning with artificial neural networks. Hinton = "Godfather of AI." |
| **Q33** | **(C)** | Bharat Ratna is India's highest civilian honour. Padma Vibhushan is 2nd, Padma Bhushan is 3rd, Padma Shri is 4th. |
| **Q34** | **(B)** | Karpoori Thakur ("Jan Nayak") — Bihar's beloved socialist CM who championed OBC/EBC reservation. Received posthumous Bharat Ratna in 2024. BIHAR EXAM FAVOURITE! |
| **Q35** | **(C)** | Param Vir Chakra = highest wartime military gallantry (facing enemy). Ashoka Chakra = highest peacetime gallantry. Bharat Ratna = highest civilian. |
| **Q36** | **(B)** | Jnanpith Award = India's highest literary award (for Indian language literature). Sahitya Akademi is prestigious but lower. Booker is international. |
| **Q37** | **(B)** | Nobel Economics Prize added in 1969 by the Swedish central bank (Sveriges Riksbank). Alfred Nobel's 1895 will only mentioned 5 prizes. |
| **Q38** | **(B)** | Abhijit Banerjee is Ford Foundation International Professor of Economics at MIT (Massachusetts Institute of Technology), Cambridge, USA. |
| **Q39** | **(C)** | Dada Saheb Phalke Award = India's highest recognition in CINEMA. Dadasaheb Phalke (1870-1944) directed India's first full-length feature film "Raja Harishchandra" (1913). |
| **Q40** | **(B)** | 2023 Medicine Nobel: mRNA modifications (specifically nucleoside modification) that enabled stable mRNA vaccines used in Pfizer-BioNTech and Moderna COVID-19 vaccines. |
| **Q41** | **(B)** | Renamed to "Major Dhyan Chand Khel Ratna" in August 2021 after Major Dhyan Chand — legendary Indian hockey player (The Wizard), won three Olympic gold medals. |
| **Q42** | **(C)** | Viswanathan Anand (Chess) was the first recipient of Rajiv Gandhi Khel Ratna in 1991-92. He later won it a 2nd time as well. |
| **Q43** | **(B)** | Ramdhari Singh Dinkar won the Jnanpith Award in 1972 for "Urvashi." He is Bihar's most celebrated Hindi poet. Also received Padma Bhushan and Sahitya Akademi Award. |
| **Q44** | **(C)** | Narges Mohammadi, Iranian human rights activist and women's rights leader, won Nobel Peace Prize 2023 while imprisoned in Iran for her activism. |
| **Q45** | **(B)** | Arundhati Roy's "The God of Small Things" (1997) won the Booker Prize. Midnight's Children = Salman Rushdie (1981). The White Tiger = Aravind Adiga (2008). |
| **Q46** | **(C)** | 2024 Chemistry Nobel: David Baker (protein design) + Demis Hassabis & John Jumper (AlphaFold AI for protein structure prediction). AlphaFold solved the 50-year-old protein folding problem. |
| **Q47** | **(D)** | BOTH B and C are correct: The Elephant Whisperers won Oscar 2023 (Documentary Short), AND Naatu Naatu from RRR won Oscar 2023 (Best Original Song). D = More than one of the above. NOTE: Lagaan (2002) was NOMINATED but did NOT win. |
| **Q48** | **(B)** | Ashoka Chakra = highest peacetime gallantry award. Given for acts of bravery/sacrifice not in face of enemy (accidents, disaster rescue, devotion to duty, etc.). |
| **Q49** | **(C)** | AR Rahman won TWO Oscars for Slumdog Millionaire (2009): Best Original Score + Best Original Song (Jai Ho). Resul Pookutty won Best Sound Mixing for the same film. |
| **Q50** | **(C)** | Dr. Rajendra Prasad received Bharat Ratna in 1962 — the year he left the Presidency. NOT in 1954 (though Bharat Ratna started in 1954, Rajendra Prasad got it in 1962). |

---

# ═══════════════════════════════════════════════════════
# 🏆 DAY 32 — TOPPER'S QUICK REVISION CARD
# ═══════════════════════════════════════════════════════

## ⚡ CS — 12 MUST-REMEMBER FACTS

1. **Binary Search:** O(log n) | REQUIRES sorted array | O(1) space iterative, O(log n) recursive
2. **Linear Search:** O(n) worst | O(1) space | works on ANY array (sorted or unsorted)
3. **Jump Search:** O(√n) | needs sorted | jumps √n steps then linear
4. **Hash Table:** O(1) AVERAGE for search/insert/delete | O(n) worst case
5. **Hash Collision:** two DIFFERENT keys → same index
6. **Chaining:** external linked lists | allows load factor > 1
7. **Open Addressing (Linear Probing):** in-table, no external | load factor CANNOT > 1 | primary clustering
8. **Quadratic Probing:** reduces primary clustering
9. **Double Hashing:** BEST for uniform distribution | two hash functions
10. **Load Factor α = n/m** | Ideal ≤ 0.7 for open addressing
11. **Rehashing:** when α too high → double table size → re-insert all
12. **Best for frequent insert/delete/search:** Hash Table (O(1) avg)

## ⚡ GS — 12 MUST-REMEMBER FACTS

1. **Nobel Prize:** Founded Alfred Nobel | First given 1901 | ALL in Stockholm EXCEPT Peace = Oslo (Norway)
2. **Economics Nobel:** Added 1969, NOT in original will
3. **Tagore:** 1913 Literature | First ASIAN Nobel | Gitanjali
4. **C.V. Raman:** 1930 Physics | Raman Effect | Feb 28 = National Science Day
5. **Amartya Sen:** 1998 Economics | welfare, poverty, famine
6. **Abhijit Banerjee:** 2019 Economics | MIT | poverty research
7. **Bharat Ratna 2024:** Karpoori Thakur (Bihar!) + Narasimha Rao + Charan Singh + Swaminathan + Advani
8. **Param Vir Chakra:** Highest WARTIME gallantry | Ashoka Chakra = highest PEACETIME
9. **Jnanpith:** Highest LITERARY award in India | Indian languages only
10. **Nobel Peace = Oslo (Norway)**, not Stockholm
11. **Slumdog Millionaire 2009:** AR Rahman — 2 Oscars (Score + Song)
12. **Ramdhari Singh Dinkar:** Bihar poet | Jnanpith winner | "Urvashi", "Rashmirathi"

---

## 📊 Day 32 Self-Assessment

| Category | Questions | My Score | Target |
|----------|-----------|----------|--------|
| CS Search Algorithms (Q1-Q13) | 13 | /13 | 12+ |
| CS Hashing (Q14-Q25) | 12 | /12 | 11+ |
| GS Nobel Prize (Q26-Q46) | 21 | /21 | 19+ |
| GS Indian Awards (Q47-Q50) | 4 | /4 | 4 |
| **TOTAL** | **50** | **/50** | **46+** |

> **Score 46+/50 = TOPPER ZONE** 🏆
> **Score 39-45 = Good — review wrong answers tonight**
> **Score below 39 = Re-read concept sections carefully**

---

## 📝 Tonight's 5-Bullet Summary (Write from Memory!)

1. Binary Search needs ______; worst case = ______; iterative space = ______
2. Hash Table: average = ______; worst = ______; collision methods = ______, ______
3. Load Factor formula = ______; threshold for open addressing = ______
4. Nobel Peace Prize city = ______ (NOT Stockholm); Peace 2023 winner = ______
5. Karpoori Thakur = Bihar's ______; received ______ in 2024; C.V. Raman = Feb 28 = ______

---

*Day 32 Complete ✅ | Tomorrow: Day 33 — NP Completeness, Greedy & DP + Bihar GK*
*32/170 steps done — Phase 1 is taking shape! Keep going!* 🎯
