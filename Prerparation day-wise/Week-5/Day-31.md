# 📅 DAY 31 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## 🎯 CS: Merge Sort, Quick Sort, Heap Sort, Radix Sort (Divide & Conquer)
## 🌍 GS: UPI, Banking System, RBI & Indian Financial System

> **Target:** Score 25/25 in CS + 25/25 in GS | **Exam Readiness: TOPPER MODE**
> **Day 31 of 170 | Phase 1 — Foundation | Week 5 — Algorithms & Sorting Part 2**

---

# ═══════════════════════════════════════════════════════
# 🖥️ PART A: COMPUTER SCIENCE
## SORTING ALGORITHMS — PART 2
### Divide & Conquer: Merge Sort | Quick Sort | Heap Sort | Radix Sort
# ═══════════════════════════════════════════════════════

---

## 📖 CS SECTION 1: DIVIDE & CONQUER PARADIGM

Before learning Merge Sort and Quick Sort, understand the **STRATEGY** behind them.

```
DIVIDE & CONQUER — 3 Steps:

  ┌──────────────────────────────────────────────────┐
  │  STEP 1: DIVIDE                                  │
  │  Break the problem into SMALLER sub-problems     │
  │  (usually into 2 halves)                         │
  ├──────────────────────────────────────────────────┤
  │  STEP 2: CONQUER                                 │
  │  Solve each sub-problem RECURSIVELY              │
  │  (base case: size 1 array is already sorted)     │
  ├──────────────────────────────────────────────────┤
  │  STEP 3: COMBINE                                 │
  │  Merge / Combine the solutions                   │
  │  of sub-problems into final answer               │
  └──────────────────────────────────────────────────┘

KEY IDEA: A problem of size n is easier than size n/2,
          which is easier than size n/4, and so on...
          until we reach size 1 (trivially solved).
```

### Algorithms Using Divide & Conquer:
```
Divide & Conquer Algorithms:
  ✓ Merge Sort         ← Today
  ✓ Quick Sort         ← Today
  ✓ Binary Search      ← Day 29
  ✓ Strassen's Matrix Multiplication
  ✓ Karatsuba Multiplication
  ✓ Closest Pair of Points
```

---

## 📖 CS SECTION 2: MERGE SORT — COMPLETE ANALYSIS

### 💡 Core Idea
> **"DIVIDE the array into two halves, RECURSIVELY sort both halves, then MERGE the two sorted halves."**

The heavy work is in the **MERGE** step. Dividing is trivial.

---

### Step-by-Step Example

**Array:** `[38, 27, 43, 3, 9, 82, 10]`

```
DIVIDE PHASE — Split until single elements:
───────────────────────────────────────────

Level 0:  [38, 27, 43, 3, 9, 82, 10]
               /               \
Level 1: [38, 27, 43]      [3, 9, 82, 10]
            /    \              /       \
Level 2: [38]  [27,43]      [3,9]    [82,10]
                /   \       /   \    /    \
Level 3:      [27] [43]   [3]  [9] [82] [10]

All single elements ← BASE CASE (already sorted)

MERGE PHASE — Merge sorted pairs back up:
──────────────────────────────────────────

Level 3→2: [27,43]  [3,9]  [10,82]
           ↑ merge ↑ merge  ↑ merge

Level 2→1: [27,38,43]    [3,9,10,82]
            ↑ merge          ↑ merge

Level 1→0: [3, 9, 10, 27, 38, 43, 82]  ← SORTED! ✓
```

---

### The MERGE Operation (Most Important!)

```
Merging two sorted arrays: [27,38,43] and [3,9,10,82]

Left:   [27, 38, 43]    → pointer i = 0
Right:  [ 3,  9, 10, 82] → pointer j = 0
Result: []

Step 1: L[0]=27 vs R[0]=3  → 3 < 27  → take 3    → Result: [3]
Step 2: L[0]=27 vs R[1]=9  → 9 < 27  → take 9    → Result: [3,9]
Step 3: L[0]=27 vs R[2]=10 → 10 < 27 → take 10   → Result: [3,9,10]
Step 4: L[0]=27 vs R[3]=82 → 27 < 82 → take 27   → Result: [3,9,10,27]
Step 5: L[1]=38 vs R[3]=82 → 38 < 82 → take 38   → Result: [3,9,10,27,38]
Step 6: L[2]=43 vs R[3]=82 → 43 < 82 → take 43   → Result: [3,9,10,27,38,43]
Step 7: Left exhausted, take remaining from Right  → Result: [3,9,10,27,38,43,82] ✓
```

### Algorithm (Pseudocode)
```
MergeSort(arr, left, right):
  if left < right:                    ← base case: single element
    mid = (left + right) / 2
    MergeSort(arr, left, mid)         ← sort left half
    MergeSort(arr, mid+1, right)      ← sort right half
    Merge(arr, left, mid, right)      ← merge both halves

Merge(arr, left, mid, right):
  Create temp arrays L[] and R[]
  Copy left half to L[], right half to R[]
  i=0, j=0, k=left
  while i < len(L) AND j < len(R):
    if L[i] <= R[j]:  arr[k++] = L[i++]
    else:             arr[k++] = R[j++]
  Copy remaining elements of L[] or R[]
```

### Complexity Analysis

```
Recurrence: T(n) = 2T(n/2) + O(n)
                   ↑           ↑
             2 sub-problems   merge cost
             of size n/2

Master Theorem: Case 2 → T(n) = O(n log n)

TREE VISUALIZATION:
  Level 0: 1 problem of size n     → cost = n
  Level 1: 2 problems of size n/2  → cost = 2 × n/2 = n
  Level 2: 4 problems of size n/4  → cost = 4 × n/4 = n
  ...
  Level k: 2^k problems of size 1  → cost = n
  Total levels = log₂(n)
  Total cost = n × log₂(n) = O(n log n)
```

### Complexity Summary Table

```
┌──────────────┬────────────────────────────────────────────┐
│ Case         │ Time Complexity                            │
├──────────────┼────────────────────────────────────────────┤
│ Best Case    │ O(n log n)  ← SAME for all cases!         │
│ Average Case │ O(n log n)                                 │
│ Worst Case   │ O(n log n)                                 │
│ Space        │ O(n)  ← needs extra array for merging!    │
├──────────────┼────────────────────────────────────────────┤
│ Stable?      │ YES ✓ (equal elements: left before right) │
│ In-Place?    │ NO ✗  (needs O(n) auxiliary space)        │
│ D&C?         │ YES ✓                                      │
└──────────────┴────────────────────────────────────────────┘
```

### 🔥 KEY EXAM FACTS — Merge Sort
```
1. ONLY sort guaranteed O(n log n) in ALL cases
2. NOT in-place → needs O(n) extra memory (EXAM TRAP!)
3. STABLE sort → preserves relative order of equal elements
4. External sorting — used when data doesn't fit in RAM
   (can sort data from disk, merge chunks)
5. Preferred over Quick Sort when:
   → Stable sort is required
   → Worst-case guarantee needed
   → Sorting linked lists (no random access needed)
```

---

## 📖 CS SECTION 3: QUICK SORT — COMPLETE ANALYSIS

### 💡 Core Idea
> **"CHOOSE a PIVOT element. PARTITION the array so all elements < pivot come before it, and all elements > pivot come after it. RECURSIVELY sort both sides."**

The pivot ends up in its FINAL CORRECT POSITION after partitioning.

---

### Step-by-Step Example (Lomuto Partition — last element as pivot)

**Array:** `[10, 7, 8, 9, 1, 5]`, Pivot = last element = 5

```
INITIAL: [10, 7, 8, 9, 1, 5]
                              ↑ pivot = 5

PARTITION PROCESS:
  i = -1  (tracks boundary of "less than pivot" zone)
  j scans from 0 to n-2

  j=0: arr[0]=10, 10 > 5 → skip (don't swap)
  j=1: arr[1]=7,   7 > 5 → skip
  j=2: arr[2]=8,   8 > 5 → skip
  j=3: arr[3]=9,   9 > 5 → skip
  j=4: arr[4]=1,   1 ≤ 5 → i++, swap arr[i] and arr[j]
       i=0, swap arr[0] and arr[4]
       Array becomes: [1, 7, 8, 9, 10, 5]

  End of scan: swap arr[i+1] with pivot (arr[n-1])
  swap arr[1] with arr[5]
  Array becomes: [1, 5, 8, 9, 10, 7]
                     ↑
              PIVOT 5 is in FINAL position! ✓

Left of 5:  [1]    → already sorted (single element)
Right of 5: [8, 9, 10, 7] → recursively sort

RECURSE on [8, 9, 10, 7], pivot = 7:
  Partition: [7] placed at correct position
  Left: []  Right: [8, 9, 10] → recurse again...

FINAL: [1, 5, 7, 8, 9, 10] ✓
```

---

### Quick Sort — Partition Diagram (Hoare vs Lomuto)

```
TWO PARTITION SCHEMES:

LOMUTO (simpler, used above):
  → Pivot = LAST element
  → One pointer i for "less than" zone
  → Moves from left to right

HOARE (original, slightly more efficient):
  → Pivot = FIRST element
  → Two pointers i (left) and j (right) moving toward each other
  → Swap when i finds element > pivot and j finds element < pivot
  → Terminates when i and j cross
```

---

### Quick Sort Complexity — The Crucial Cases

```
BEST CASE: Pivot always splits array into EQUAL halves
  → T(n) = 2T(n/2) + O(n) → O(n log n)
  (same recurrence as Merge Sort!)

AVERAGE CASE: Random pivot → O(n log n)

WORST CASE: Pivot is always SMALLEST or LARGEST element
  → Happens on SORTED or REVERSE-SORTED array with bad pivot choice
  → T(n) = T(0) + T(n-1) + O(n) → O(n²)

WORST CASE TREE (when pivot = always min):
  n → (0) + (n-1) → (0) + (n-2) → ...
  Cost: n + (n-1) + (n-2) + ... + 1 = n(n+1)/2 = O(n²)
```

### Avoiding Worst Case
```
Solutions to avoid O(n²) worst case:
  1. RANDOM PIVOT selection (most common)
  2. MEDIAN-OF-THREE pivot (choose median of first, mid, last)
  3. IntroSort (used by C++ STL) = Quick Sort + Heap Sort fallback
```

### Quick Sort Complexity Table

```
┌──────────────┬─────────────────────────────────────────────────┐
│ Case         │ Time Complexity                                 │
├──────────────┼─────────────────────────────────────────────────┤
│ Best Case    │ O(n log n)                                      │
│ Average Case │ O(n log n)                                      │
│ Worst Case   │ O(n²) — sorted/reverse-sorted with bad pivot   │
│ Space        │ O(log n) avg — recursion stack depth           │
│              │ O(n) worst case — recursion stack              │
├──────────────┼─────────────────────────────────────────────────┤
│ Stable?      │ NO ✗ — swapping can change relative order      │
│ In-Place?    │ YES ✓ — sorts within original array            │
│ D&C?         │ YES ✓                                          │
└──────────────┴─────────────────────────────────────────────────┘
```

### 🔥 KEY EXAM FACTS — Quick Sort
```
1. FASTEST in practice on average (small constants in O(n log n))
2. In-Place (unlike Merge Sort) → preferred in memory-constrained systems
3. NOT stable (unlike Merge Sort)
4. Worst case O(n²) on SORTED input with first/last element as pivot
5. Used by: C++ STL sort(), many standard library implementations
6. Cache-friendly: operates on contiguous memory (better CPU performance)
```

---

## 📖 CS SECTION 4: MERGE SORT vs QUICK SORT — MASTER COMPARISON

```
┌──────────────────┬──────────────────────┬──────────────────────┐
│ Property         │ MERGE SORT           │ QUICK SORT           │
├──────────────────┼──────────────────────┼──────────────────────┤
│ Paradigm         │ Divide & Conquer     │ Divide & Conquer     │
│ Best Case        │ O(n log n)           │ O(n log n)           │
│ Average Case     │ O(n log n)           │ O(n log n)           │
│ Worst Case       │ O(n log n) ← ALWAYS │ O(n²) ← CAN HAPPEN  │
│ Space            │ O(n) extra           │ O(log n) stack       │
│ In-Place?        │ NO ✗                 │ YES ✓                │
│ Stable?          │ YES ✓                │ NO ✗                 │
│ External Sort?   │ YES ✓ (disk sorting) │ NO ✗                 │
│ Linked Lists?    │ Better               │ Worse                │
│ Cache behavior   │ Less cache-friendly  │ More cache-friendly  │
│ Practical speed  │ Slower in practice   │ Faster in practice   │
│ Key operation    │ MERGE (combine)      │ PARTITION (divide)   │
└──────────────────┴──────────────────────┴──────────────────────┘

BPSC EXAM RULE:
  "When asked which is ALWAYS O(n log n)?" → MERGE SORT
  "Which has O(n²) worst case?" → QUICK SORT
  "Which needs extra O(n) space?" → MERGE SORT
  "Which is in-place?" → QUICK SORT
  "Which is stable?" → MERGE SORT
```

---

## 📖 CS SECTION 5: HEAP SORT — COMPLETE ANALYSIS

### 💡 Core Idea
> **"Build a MAX HEAP from the array. Then repeatedly extract the maximum element (root) and place it at the end."**

### Binary Heap Recap (needed for Heap Sort)

```
MAX HEAP property: parent ≥ children (root = maximum)
MIN HEAP property: parent ≤ children (root = minimum)

Heap as Array:
  Parent of node i = (i-1)/2
  Left child of i  = 2i + 1
  Right child of i = 2i + 2

  Array: [16, 14, 10, 8, 7, 9, 3, 2, 4, 1]
  Tree visualization:
              16
            /    \
          14      10
         /  \    /  \
        8    7  9    3
       / \ /
      2  4 1
```

### Heap Sort — Two Phases

```
PHASE 1: BUILD MAX HEAP
  → Start from last non-leaf node: (n/2 - 1)
  → Apply HEAPIFY (sift-down) for each node from bottom to root
  → After phase 1: root = maximum element
  → Time: O(n) — (not O(n log n)! building heap is linear)

PHASE 2: EXTRACT MAX REPEATEDLY
  → Swap root (max) with LAST element
  → Reduce heap size by 1
  → Heapify root (restore heap property)
  → Repeat n-1 times
  → Time: O(n log n)

TOTAL: O(n) + O(n log n) = O(n log n)
```

### Example on [4, 10, 3, 5, 1]

```
STEP 1 — Build Max Heap:
  Input: [4, 10, 3, 5, 1]
  After heapify: [10, 5, 3, 4, 1]  (max heap built)

STEP 2 — Extract max and heapify:
  Swap root(10) with last(1): [1, 5, 3, 4, | 10]
  Heapify: [5, 4, 3, 1, | 10]

  Swap root(5) with last(1): [1, 4, 3, | 5, 10]
  Heapify: [4, 1, 3, | 5, 10]

  Swap root(4) with last(3): [3, 1, | 4, 5, 10]
  Heapify: [3, 1, | 4, 5, 10]

  Swap root(3) with last(1): [1, | 3, 4, 5, 10]
  Done!

FINAL: [1, 3, 4, 5, 10] ✓
```

### Heap Sort Complexity Table

```
┌──────────────┬────────────────────────────────────────┐
│ Case         │ Time Complexity                        │
├──────────────┼────────────────────────────────────────┤
│ Best Case    │ O(n log n)                             │
│ Average Case │ O(n log n)                             │
│ Worst Case   │ O(n log n)                             │
│ Space        │ O(1) — in-place!                      │
├──────────────┼────────────────────────────────────────┤
│ Stable?      │ NO ✗                                   │
│ In-Place?    │ YES ✓                                  │
│ D&C?         │ NO ✗ (uses Heap data structure)        │
└──────────────┴────────────────────────────────────────┘
```

### 🔥 KEY EXAM FACTS — Heap Sort
```
1. O(n log n) in ALL cases (like Merge Sort) BUT In-Place (like Quick Sort)
2. NOT stable
3. NOT Divide & Conquer (uses heap data structure approach)
4. Building heap alone takes O(n) — better than O(n log n) insertion!
5. Heapify operation on a single node = O(log n)
6. Priority Queue uses Heap internally
```

---

## 📖 CS SECTION 6: RADIX SORT — NON-COMPARISON SORT

### 💡 Core Idea
> **"Sort digits by digit position. Start from LEAST SIGNIFICANT DIGIT (LSD) to MOST SIGNIFICANT DIGIT (MSD)."**

This is NOT a comparison sort — it never asks "is A > B?"

### Example: Sort [170, 45, 75, 90, 802, 24, 2, 66]

```
STEP 1: Sort by ONES digit (LSD):
  Input:  [170, 45, 75, 90, 802, 24, 2, 66]
  Ones:     0    5   5   0    2   4  2   6
  Sorted: [170, 90, 802, 2, 24, 45, 75, 66]
              ↑─────↑    ↑──↑                (grouped by ones digit)

STEP 2: Sort by TENS digit:
  Input:  [170, 90, 802, 2, 24, 45, 75, 66]
  Tens:     7    9    0  0   2   4   7   6
  Sorted: [802, 2, 24, 45, 66, 170, 75, 90]

STEP 3: Sort by HUNDREDS digit:
  Input:  [802, 2, 24, 45, 66, 170, 75, 90]
  Hundreds: 8   0   0   0   0    1   0   0
  Sorted: [2, 24, 45, 66, 75, 90, 170, 802] ✓
```

### Radix Sort Complexity

```
d = number of digits, n = number of elements
k = range of each digit (0-9, so k=10)

Time:  O(d × (n + k))
       ≈ O(n) when d is constant (fixed-size integers)

Space: O(n + k)

Stable?    YES ✓ (uses stable counting sort for each digit pass)
In-Place?  NO ✗
D&C?       NO ✗ (NOT comparison based)
```

### 🔥 KEY EXAM FACT — Radix Sort
```
Radix Sort achieves O(n) — beats the O(n log n) lower bound
for COMPARISON sorts!
This is possible because it does NOT use comparisons.

LOWER BOUND THEOREM: Any comparison-based sort requires
                     at least Ω(n log n) comparisons.
Radix, Counting, Bucket sort bypass this by not comparing!
```

---

## 📖 CS SECTION 7: GRAND MASTER TABLE — ALL SORTING ALGORITHMS

```
┌───────────────┬──────────┬────────────┬──────────┬───────┬────────┬────────┐
│ Algorithm     │ Best     │ Average    │ Worst    │ Space │ Stable │In-Place│
├───────────────┼──────────┼────────────┼──────────┼───────┼────────┼────────┤
│ Bubble Sort   │ O(n)*    │ O(n²)      │ O(n²)    │ O(1)  │ YES    │ YES    │
│ Selection Sort│ O(n²)    │ O(n²)      │ O(n²)    │ O(1)  │ NO     │ YES    │
│ Insertion Sort│ O(n)     │ O(n²)      │ O(n²)    │ O(1)  │ YES    │ YES    │
│ Merge Sort    │ O(nlogn) │ O(nlogn)   │ O(nlogn) │ O(n)  │ YES    │ NO     │
│ Quick Sort    │ O(nlogn) │ O(nlogn)   │ O(n²)    │O(logn)│ NO     │ YES    │
│ Heap Sort     │ O(nlogn) │ O(nlogn)   │ O(nlogn) │ O(1)  │ NO     │ YES    │
│ Radix Sort    │ O(nk)    │ O(nk)      │ O(nk)    │O(n+k) │ YES    │ NO     │
│ Counting Sort │ O(n+k)   │ O(n+k)     │ O(n+k)   │O(n+k) │ YES    │ NO     │
└───────────────┴──────────┴────────────┴──────────┴───────┴────────┴────────┘
* Bubble Sort best case O(n) only with flag optimization
```

---

## 📖 CS SECTION 8: TRICKY EXAM PATTERNS & PYQ ANALYSIS

### Pattern 1: "Which sort is ALWAYS O(n log n)?"
```
Correct answers: Merge Sort AND Heap Sort
(Both guarantee O(n log n) in ALL cases)

Quick Sort is NOT always O(n log n) → O(n²) worst case
```

### Pattern 2: "Which sort is O(n log n) AND In-Place AND NOT Stable?"
```
Answer: HEAP SORT
(Merge Sort = O(n log n) but NOT in-place)
(Quick Sort = in-place but worst case O(n²))
(Heap Sort = O(n log n) + in-place + NOT stable)
```

### Pattern 3: "Which sort is D&C?"
```
Merge Sort — YES
Quick Sort — YES
Heap Sort  — NO (uses heap, not divide & conquer)
```

### Pattern 4: Quick Sort Worst Case Trigger
```
Quick Sort is O(n²) when array is:
  ✓ Already sorted (ascending) with first/last pivot
  ✓ Reverse sorted with first/last pivot
  ✓ All elements identical

Quick Sort is O(n log n) when:
  ✓ Random pivot selection
  ✓ Array is randomly shuffled
```

### Pattern 5: External Sorting
```
"Which sort is suitable for EXTERNAL sorting (data on disk)?"
Answer: MERGE SORT
Because: It reads data sequentially (no random access)
         Can merge sorted chunks from disk efficiently
Quick Sort needs random access → NOT suitable for external sort
```

---

## 📖 CS SECTION 9: LOWER BOUND FOR SORTING

```
FUNDAMENTAL THEOREM:
Any comparison-based sorting algorithm needs at least
Ω(n log n) comparisons in the worst case.

PROOF IDEA: Decision tree has n! leaves (all permutations).
  A binary tree with n! leaves has height ≥ log₂(n!)
  By Stirling's approximation: log₂(n!) ≈ n log₂(n)
  Therefore: Ω(n log n) comparisons needed.

IMPLICATION:
  → Merge Sort and Heap Sort are OPTIMAL comparison sorts!
  → Quick Sort is optimal on average.
  → To beat O(n log n), you MUST use non-comparison sort
    (Radix, Counting, Bucket).
```

---

## 📖 CS SECTION 10: MEMORY TRICKS FOR EXAM

```
SORTING MEMORY AIDS:
━━━━━━━━━━━━━━━━━━━

"M.Q.H. are the FASTER three" (Merge, Quick, Heap → O(n log n))

Among M.Q.H.:
  M = Merge   → Stable, NOT in-place, D&C, External OK
  Q = Quick   → NOT stable, In-place, D&C, Worst O(n²)
  H = Heap    → NOT stable, In-place, NOT D&C, Always O(nlogn)

"Only Merge is Stable among the fast three"
"Only Merge needs extra O(n) space"
"Only Quick can degrade to O(n²)"
"Heap = O(n log n) + In-place but NOT D&C"

Non-comparison sorts (break O(n log n) barrier):
  Radix, Counting, Bucket → O(n) but require special conditions
```

---

# ═══════════════════════════════════════════════════════
# 📝 CS PRACTICE QUESTIONS — 25 MCQs
## (Answers consolidated at END — attempt ALL before checking!)
# ═══════════════════════════════════════════════════════

---

**Q1.** Which sorting algorithm uses the Divide & Conquer paradigm AND guarantees O(n log n) time complexity in ALL cases (best, average, worst)?

(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q2.** Quick Sort has which time complexity in the WORST CASE?

(A) O(n log n)
(B) O(n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the SPACE complexity of Merge Sort?

(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q4.** Heap Sort has which combination of properties?

(A) O(n log n) all cases, Stable, In-Place
(B) O(n log n) all cases, NOT Stable, In-Place
(C) O(n log n) all cases, Stable, NOT In-Place
(D) More than one of the above
(E) None of the above

---

**Q5.** Quick Sort exhibits its WORST CASE of O(n²) when:

(A) Array is randomly shuffled
(B) Pivot is always chosen as the median element
(C) Array is already sorted and pivot = first/last element
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following sorting algorithms is NOT based on the Divide & Conquer strategy?

(A) Merge Sort
(B) Quick Sort
(C) Heap Sort
(D) More than one of the above
(E) None of the above

---

**Q7.** Radix Sort is different from Merge Sort, Quick Sort, and Heap Sort because:

(A) Radix Sort is faster than all others in all cases
(B) Radix Sort does NOT use element comparisons
(C) Radix Sort requires sorted input
(D) More than one of the above
(E) None of the above

---

**Q8.** The recurrence relation T(n) = 2T(n/2) + O(n) describes which sorting algorithm?

(A) Quick Sort (best case)
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q9.** Which sorting algorithm is BEST suited for EXTERNAL SORTING (sorting data stored on disk)?

(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q10.** Among Merge Sort, Quick Sort, and Heap Sort — which one is STABLE?

(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q11.** The LOWER BOUND for any comparison-based sorting algorithm is:

(A) O(n)
(B) O(n²)
(C) Ω(n log n)
(D) More than one of the above
(E) None of the above

---

**Q12.** In Quick Sort, the PARTITION step places the pivot element at:

(A) The beginning of the array
(B) Its CORRECT FINAL position in the sorted array
(C) The middle of the array always
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following sorting algorithms has O(n log n) time complexity AND O(1) extra space AND is NOT a Divide & Conquer algorithm?

(A) Merge Sort
(B) Quick Sort
(C) Heap Sort
(D) More than one of the above
(E) None of the above

---

**Q14.** Merge Sort is preferred over Quick Sort in which situation?

(A) When memory is very limited
(B) When a stable sort is required and worst-case guarantee is needed
(C) When the input is already sorted
(D) More than one of the above
(E) None of the above

---

**Q15.** The time complexity of building a MAX HEAP from n unsorted elements is:

(A) O(n log n)
(B) O(n²)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q16.** Consider the following array: [3, 1, 4, 1, 5, 9, 2, 6]. If Merge Sort is applied, at which LEVEL of recursion does the array first get split into individual elements (arrays of size 1)?

(A) Level 1
(B) Level 2
(C) Level 3
(D) More than one of the above
(E) None of the above

---

**Q17.** In the MERGE operation of Merge Sort, if two equal elements appear (one from left subarray, one from right subarray), which is placed first to maintain stability?

(A) The element from the right subarray
(B) The element from the left subarray
(C) Either can be placed; order doesn't matter
(D) More than one of the above
(E) None of the above

---

**Q18.** Radix Sort's time complexity is O(d × (n + k)). What does 'd' represent?

(A) Number of distinct elements
(B) Number of digits in the maximum element
(C) Depth of recursion
(D) More than one of the above
(E) None of the above

---

**Q19.** Quick Sort on average is FASTER than Merge Sort in practice. The main reason is:

(A) Quick Sort has better worst-case complexity
(B) Quick Sort is cache-friendly and has smaller constant factors in O(n log n)
(C) Quick Sort uses less recursion than Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following statements about Merge Sort is CORRECT?

(A) Merge Sort is an in-place sorting algorithm
(B) Merge Sort has O(n²) worst case time complexity
(C) Merge Sort is stable and has O(n log n) time in all cases
(D) More than one of the above
(E) None of the above

---

**Q21.** What is the TIME COMPLEXITY of a single HEAPIFY operation (fixing one node in a heap)?

(A) O(n)
(B) O(n log n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q22.** Which sorting algorithm achieves O(n) time complexity (linear time), breaking the Ω(n log n) comparison-sort lower bound?

(A) Heap Sort
(B) Merge Sort
(C) Radix Sort
(D) More than one of the above
(E) None of the above

---

**Q23.** In Merge Sort for a linked list, it is preferred over Quick Sort because:

(A) Merge Sort has better worst-case complexity for linked lists
(B) Merge Sort does not require random access; it works with sequential access
(C) Merge Sort uses less memory for linked lists
(D) More than one of the above
(E) None of the above

---

**Q24.** PYQ-STYLE: A sorting algorithm is needed that: (i) uses O(1) extra space, (ii) guarantees O(n log n) in worst case, (iii) is not stable. Which algorithm satisfies ALL three conditions?

(A) Merge Sort
(B) Quick Sort
(C) Heap Sort
(D) More than one of the above
(E) None of the above

---

**Q25.** TRICKY: Both Merge Sort and Heap Sort guarantee O(n log n). Why is Heap Sort generally preferred over Merge Sort in memory-constrained environments?

(A) Heap Sort is a stable algorithm while Merge Sort is not
(B) Heap Sort is in-place (O(1) space) while Merge Sort needs O(n) extra space
(C) Heap Sort is faster than Merge Sort in all cases
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🌍 PART B: GENERAL STUDIES
## UPI, BANKING SYSTEM, RBI & INDIAN FINANCIAL SYSTEM
# ═══════════════════════════════════════════════════════

---

## 📖 GS SECTION 1: UPI — UNIFIED PAYMENTS INTERFACE

### What is UPI?

```
UPI = Unified Payments Interface

Developed by: NPCI (National Payments Corporation of India)
Launched:     April 2016
Regulated by: Reserve Bank of India (RBI)

Definition: A real-time payment system that allows instant
            fund transfer between bank accounts via mobile
            phone using a Virtual Payment Address (VPA).

KEY FEATURES:
  → 24×7 availability (even on holidays)
  → Instant transfer (within seconds)
  → Uses VPA (like name@bank) — no need to share account number
  → Single mobile app can access multiple bank accounts
  → Free for users (no transaction charges)
  → Works across ALL banks in India
```

### UPI Architecture

```
UPI ECOSYSTEM:
  ┌─────────────────────────────────────────────────────┐
  │  NPCI = Central Switch (routes all transactions)    │
  └────────────────────┬────────────────────────────────┘
                       │
        ┌──────────────┼──────────────────┐
        ↓              ↓                  ↓
   Payer's         Payee's           PSP Banks
   Bank            Bank              (Payment Service
                                     Provider)
                                     e.g., PhonePe,
                                     Google Pay, Paytm
```

### UPI Milestones & Statistics
```
2016:  UPI launched by NPCI
2020:  First country to process 2 billion transactions/month
2022:  UPI crossed 7 billion transactions/month
2023:  India topped global real-time payment rankings
2024:  UPI One World (for foreign tourists without Indian SIM)
       UPI Circle (delegate payments)
       UPI-Lite X (offline payments)

International expansion:
  → Bhutan (2021) — first international UPI launch
  → Singapore, UAE, France, UK, Netherlands
  → G20 members recognizing India's DPI (Digital Public Infrastructure)
```

### NPCI — Key Organisation
```
NPCI = National Payments Corporation of India
Founded: 2008
HQ:      Mumbai
Type:    Non-profit organisation under Section 8 (Companies Act)
Owner:   Owned by consortium of banks (RBI + banks)
Products managed by NPCI:
  → UPI (Unified Payments Interface)
  → IMPS (Immediate Payment Service)
  → NEFT (National Electronic Funds Transfer)
  → RTGS (Real Time Gross Settlement)
  → RuPay (India's domestic card network)
  → NACH (National Automated Clearing House)
  → Bharat Bill Payment System (BBPS)
  → FASTag (electronic toll collection)
```

---

## 📖 GS SECTION 2: PAYMENT SYSTEMS COMPARISON

```
┌────────────┬─────────────┬─────────────┬──────────────────────┐
│ System     │ Full Form   │ Speed       │ Key Feature          │
├────────────┼─────────────┼─────────────┼──────────────────────┤
│ NEFT       │ Nat'l Elec. │ Hourly      │ Batch processing     │
│            │ Funds Trans.│ batches     │ Available 24×7 now   │
├────────────┼─────────────┼─────────────┼──────────────────────┤
│ RTGS       │ Real Time   │ Immediate   │ Min ₹2 lakh,         │
│            │ Gross Sett. │             │ large value only     │
├────────────┼─────────────┼─────────────┼──────────────────────┤
│ IMPS       │ Immediate   │ 24×7        │ Mobile, available    │
│            │ Payment Svc │ instant     │ on holidays too      │
├────────────┼─────────────┼─────────────┼──────────────────────┤
│ UPI        │ Unified     │ Instant     │ VPA, multiple banks  │
│            │ Payments    │ 24×7        │ single app           │
├────────────┼─────────────┼─────────────┼──────────────────────┤
│ RuPay      │ India's     │ Instant     │ Domestic card        │
│            │ card network│             │ cheaper than Visa    │
└────────────┴─────────────┴─────────────┴──────────────────────┘
```

---

## 📖 GS SECTION 3: RBI — RESERVE BANK OF INDIA

### Basic Facts

```
RBI = Reserve Bank of India

Founded:     April 1, 1935 (under RBI Act 1934)
HQ:          Mumbai (Maharashtra)
Nationalised: January 1, 1949
Status:      India's CENTRAL BANK
Governor:    Sanjay Malhotra (as of December 2024)
             (succeeded Shaktikanta Das)

MOTTO: "जन कल्याण के लिए राष्ट्र की सेवा में"
       (Serving the nation for the welfare of the people)
```

### Functions of RBI

```
RBI FUNCTIONS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. MONETARY AUTHORITY
   → Controls money supply and credit
   → Sets interest rates (Repo, Reverse Repo)
   → Controls inflation via monetary policy

2. CURRENCY ISSUER
   → Sole authority to issue currency notes
   → EXCEPT ₹1 coin/note (issued by Government of India)
   → Manages currency circulation

3. BANKER TO GOVERNMENT
   → Manages government accounts
   → Issues government securities (G-Secs)
   → Provides overdraft to government

4. BANKER'S BANK (Lender of Last Resort)
   → Banks borrow from RBI during cash shortage
   → Maintains CRR deposits of all banks

5. REGULATOR OF BANKS
   → Issues banking licences
   → Supervises commercial banks
   → Sets prudential norms (NPA classification)

6. FOREIGN EXCHANGE MANAGEMENT
   → Manages India's forex reserves
   → Regulates forex transactions (FEMA)
   → Intervenes in currency market to stabilise ₹

7. DEVELOPMENTAL FUNCTIONS
   → Promotes rural credit (via NABARD)
   → Promotes financial inclusion
```

---

## 📖 GS SECTION 4: MONETARY POLICY TOOLS — MOST ASKED IN BPSC!

```
MONETARY POLICY TOOLS OF RBI:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

QUANTITATIVE TOOLS (affect overall money supply):

┌─────────────────┬──────────────────────────────────────────┐
│ Tool            │ Definition & Effect                      │
├─────────────────┼──────────────────────────────────────────┤
│ REPO RATE       │ Rate at which RBI LENDS to commercial    │
│                 │ banks (short-term, against securities)   │
│                 │ ↑ Repo = less borrowing = less money     │
│                 │   supply = controls inflation            │
├─────────────────┼──────────────────────────────────────────┤
│ REVERSE REPO    │ Rate at which RBI BORROWS from banks     │
│ RATE            │ (banks park excess money with RBI)       │
│                 │ ↑ Reverse Repo = banks park more with    │
│                 │   RBI = less money in market             │
├─────────────────┼──────────────────────────────────────────┤
│ CRR             │ Cash Reserve Ratio — % of deposits banks │
│ (Cash Reserve   │ MUST keep with RBI as CASH               │
│  Ratio)         │ ↑ CRR = less money banks can lend        │
│                 │       = reduces money supply             │
├─────────────────┼──────────────────────────────────────────┤
│ SLR             │ Statutory Liquidity Ratio — % of deposits│
│ (Statutory      │ banks MUST invest in approved securities │
│  Liquidity      │ (G-Secs, gold, cash)                     │
│  Ratio)         │ ↑ SLR = less money banks can lend        │
├─────────────────┼──────────────────────────────────────────┤
│ OMO             │ Open Market Operations — RBI buys/sells  │
│ (Open Market    │ government securities in open market     │
│  Operations)    │ Buy securities = inject money            │
│                 │ Sell securities = absorb money           │
├─────────────────┼──────────────────────────────────────────┤
│ MSF             │ Marginal Standing Facility — emergency   │
│                 │ overnight borrowing by banks from RBI    │
│                 │ Rate > Repo rate (penalty for emergency) │
└─────────────────┴──────────────────────────────────────────┘

MEMORY TRICK:
  "Repo = RBI gives, Reverse Repo = RBI takes"
  "CRR = Cash with RBI, SLR = Securities by bank"
  To INCREASE money supply: ↓ Repo, ↓ CRR, ↓ SLR
  To DECREASE money supply (fight inflation): ↑ Repo, ↑ CRR, ↑ SLR
```

---

## 📖 GS SECTION 5: BANKING SYSTEM IN INDIA

### Structure of Banking in India

```
BANKING SYSTEM IN INDIA:
━━━━━━━━━━━━━━━━━━━━━━━━━━

RBI (Central Bank)
    │
    ├── SCHEDULED BANKS (listed in 2nd Schedule of RBI Act)
    │       │
    │       ├── COMMERCIAL BANKS
    │       │       │
    │       │       ├── Public Sector Banks (PSBs)
    │       │       │     → SBI (largest), PNB, BOB, Canara, etc.
    │       │       │     → Government owns >51%
    │       │       │
    │       │       ├── Private Sector Banks
    │       │       │     → HDFC, ICICI, Axis, Kotak, etc.
    │       │       │
    │       │       └── Foreign Banks (branches in India)
    │       │             → Citibank, HSBC, Standard Chartered
    │       │
    │       ├── COOPERATIVE BANKS
    │       │     → Urban Cooperative Banks (UCBs)
    │       │     → Rural Cooperative Banks
    │       │     → Example: Saraswat Bank
    │       │
    │       └── SMALL FINANCE BANKS & PAYMENTS BANKS
    │             → Small Finance: full banking, focus on small
    │             → Payments Bank: deposits only (max ₹2 lakh),
    │               NO loans (Airtel, Jio, India Post Payments Bank)
    │
    └── NON-SCHEDULED BANKS (not in RBI's 2nd Schedule)
```

### Bank Nationalisation — EXAM FAVOURITE!

```
BANK NATIONALISATION IN INDIA:

FIRST WAVE — 1969 (under PM Indira Gandhi)
  → 14 major commercial banks nationalised
  → Those with deposits > ₹50 crore
  → "Social banking" — reach rural areas
  → Famous speech: Indira Gandhi declared "bank nationalisation"
  → This was part of "Garibi Hatao" era policies

SECOND WAVE — 1980 (under PM Indira Gandhi, second time)
  → 6 more banks nationalised
  → Total: 20 banks nationalised

TOTAL NATIONALISED: 14 + 6 = 20 banks

IMPORTANT: SBI was NOT nationalised in 1969!
  → State Bank of India was created by SBI Act 1955
  → SBI came from Imperial Bank of India (1921)
  → SBI is oldest/largest public sector bank
```

### Key Banking Reforms

```
1991 — NARASIMHAM COMMITTEE (I): Banking sector reforms
  → Reduced CRR and SLR
  → Allowed private banks (HDFC, ICICI founded post-1991)
  → Introduced CAPITAL ADEQUACY RATIO (Basel norms)

1998 — NARASIMHAM COMMITTEE (II): Further reforms
  → Merger of weak banks
  → Improved NPA classification

2014 — JAN DHAN YOJANA (PMJDY)
  → Zero-balance bank accounts for all
  → Financial inclusion mission
  → Linked to Aadhaar + Mobile (JAM Trinity)

2016 — DEMONETISATION
  → ₹500 and ₹1000 notes invalid from November 8, 2016
  → New ₹500 and ₹2000 notes introduced
  → Aim: black money, counterfeiting, cashless economy

2023 — ₹2000 notes withdrawal
  → RBI withdrew ₹2000 notes from circulation (May 2023)
```

---

## 📖 GS SECTION 6: GST & TAXATION

### GST — Goods and Services Tax

```
GST = Goods and Services Tax

Introduced: July 1, 2017 ("One Nation, One Tax, One Market")
Type: Indirect, Destination-based consumption tax
Replaced: VAT, Service Tax, Excise Duty, CST, Entry Tax, etc.
Constitutional basis: 101st Constitutional Amendment (2016)

GST STRUCTURE (Dual GST model):
  CGST = Central GST → collected by Centre
  SGST = State GST → collected by State
  IGST = Integrated GST → on inter-state transactions
         (collected by Centre, then shared with States)

GST COUNCIL:
  → Chaired by: Union Finance Minister
  → Members: State Finance Ministers
  → Voting: 1/3 Centre + 2/3 States needed for decisions
  → Meets periodically to revise rates

GST RATES (Slabs):
  0%  → Essential items (unprocessed food, fresh milk)
  5%  → Basic items (packaged food, medicine)
 12%  → Standard items
 18%  → Most services, electronics
 28%  → Luxury items (cars, tobacco)

SPECIAL:
  3% on GOLD
  Petroleum, alcohol excluded from GST (still under old taxes)
```

---

## 📖 GS SECTION 7: IMPORTANT FINANCIAL REGULATORS

```
┌──────────────┬──────────────────────────────┬──────────────────┐
│ Regulator    │ What it regulates            │ HQ               │
├──────────────┼──────────────────────────────┼──────────────────┤
│ RBI          │ Banks, monetary policy,      │ Mumbai           │
│              │ currency, forex              │                  │
├──────────────┼──────────────────────────────┼──────────────────┤
│ SEBI         │ Securities markets,          │ Mumbai           │
│ (1988/1992)  │ stock exchanges (BSE, NSE),  │                  │
│              │ mutual funds, brokers        │                  │
├──────────────┼──────────────────────────────┼──────────────────┤
│ IRDAI        │ Insurance companies          │ Hyderabad        │
│ (1999)       │ (LIC, private insurers)      │                  │
├──────────────┼──────────────────────────────┼──────────────────┤
│ PFRDA        │ Pension funds (NPS —         │ New Delhi        │
│ (2003/2014)  │ National Pension System)     │                  │
├──────────────┼──────────────────────────────┼──────────────────┤
│ NABARD       │ Agricultural credit,         │ Mumbai           │
│ (1982)       │ rural development            │                  │
├──────────────┼──────────────────────────────┼──────────────────┤
│ NHB          │ Housing finance companies    │ New Delhi        │
│ (1988)       │ (subsidiary of RBI)          │                  │
└──────────────┴──────────────────────────────┴──────────────────┘

MEMORY: "RBI + SEBI + IRDAI + PFRDA = 4 main financial regulators"
```

---

## 📖 GS SECTION 8: KEY ECONOMIC TERMS — QUICK REFERENCE

```
GDP = Gross Domestic Product
    = Total market value of all goods & services produced
      WITHIN a country in a given period
    (includes output by foreign companies in India)

GNP = Gross National Product
    = GDP + Income earned ABROAD by Indians
      - Income earned IN INDIA by foreigners

NNP = Net National Product = GNP - Depreciation
Per Capita Income = NNP / Population

INFLATION: General rise in price level over time
  Measured by: CPI (Consumer Price Index) — for common people
               WPI (Wholesale Price Index) — for bulk goods

FISCAL DEFICIT: Government's total expenditure > Revenue
               (= government borrows this much)
REVENUE DEFICIT: Revenue expenditure > Revenue receipts
CURRENT ACCOUNT DEFICIT: Imports of goods+services > Exports

REPO RATE (current ~6.5%): Rate RBI charges banks for borrowing
REVERSE REPO RATE: Rate banks get for parking money with RBI

CREDIT RATING AGENCIES:
  India: CRISIL, CARE, ICRA
  Global: S&P, Moody's, Fitch

MSME: Micro, Small & Medium Enterprises
  (Major employer, ~45% of industrial production)
```

---

## 📖 GS SECTION 9: IMPORTANT GOVERNMENT SCHEMES — BANKING & FINANCE

```
JAN DHAN YOJANA (PMJDY) — 2014:
  → Zero-balance bank accounts
  → ₹1 lakh accident insurance + ₹30,000 life insurance
  → Overdraft facility of ₹10,000
  → Aadhaar-linked

JAM TRINITY:
  → J = Jan Dhan (bank account)
  → A = Aadhaar (identity)
  → M = Mobile (communication)
  Used for: Direct Benefit Transfer (DBT) to eliminate leakages

MUDRA SCHEME (PMMY) — 2015:
  → Micro Units Development & Refinance Agency
  → Loans for micro-enterprises
  → Three categories:
    Shishu: up to ₹50,000
    Kishore: ₹50,000 to ₹5 lakh
    Tarun: ₹5 lakh to ₹10 lakh

STAND-UP INDIA — 2016:
  → Loans ₹10 lakh to ₹1 crore for SC/ST and women entrepreneurs
  → At least one SC/ST and one woman borrower per bank branch

DIGITAL INDIA — 2015:
  → Flagship programme for digital infrastructure
  → Cashless economy → promoted UPI, RuPay, Aadhaar Pay
```

---

## 📖 GS SECTION 10: BIHAR GK — BANKING & ECONOMY CONNECTION

```
BIHAR BANKING FACTS:

→ Bihar Grameen Bank: Regional Rural Bank in Bihar
→ NABARD: Significant role in Bihar's agriculture credit
→ Bihar State Co-operative Bank: HQ Patna
→ Patna: Major banking hub in Bihar; BSFC (Bihar State
         Financial Corporation)

JAN DHAN IN BIHAR:
→ Bihar among top states in PMJDY account opening
→ Significant unbanked population (financial inclusion drive)

BIHAR ECONOMY:
→ Predominantly agrarian economy
→ Crops: Paddy, Wheat, Maize, Litchi (GI tag product)
→ Muzaffarpur Litchi: GI tag (Geographical Indication)
→ Champaran: Farmers' movement linked to Satyagraha (1917)
→ Growth rate: Bihar among fastest growing states since 2005

DEMONETISATION IMPACT ON BIHAR:
→ Agriculture-heavy economy initially disrupted
→ Accelerated adoption of UPI/BHIM in rural areas
→ BC (Business Correspondent) model expanded
```

---

# ═══════════════════════════════════════════════════════
# 📝 GS PRACTICE QUESTIONS — 25 MCQs
## (Answers consolidated at END — attempt ALL before checking!)
# ═══════════════════════════════════════════════════════

---

**Q26.** UPI (Unified Payments Interface) was developed by which organisation?

(A) Reserve Bank of India (RBI)
(B) State Bank of India (SBI)
(C) National Payments Corporation of India (NPCI)
(D) More than one of the above
(E) None of the above

---

**Q27.** RBI was established under which Act and in which year?

(A) Banking Regulation Act, 1949
(B) RBI Act, 1934 — operational from April 1, 1935
(C) Companies Act, 1956
(D) More than one of the above
(E) None of the above

---

**Q28.** The REPO RATE is defined as:

(A) Rate at which commercial banks lend to each other overnight
(B) Rate at which RBI lends money to commercial banks (short-term)
(C) Rate at which RBI borrows from commercial banks
(D) More than one of the above
(E) None of the above

---

**Q29.** CRR (Cash Reserve Ratio) refers to:

(A) Percentage of deposits banks must invest in government securities
(B) Percentage of deposits banks must keep as CASH with RBI
(C) Minimum capital banks must maintain against risk
(D) More than one of the above
(E) None of the above

---

**Q30.** India's first major bank nationalisation occurred in which year, nationalising 14 banks?

(A) 1955
(B) 1969
(C) 1980
(D) More than one of the above
(E) None of the above

---

**Q31.** GST (Goods and Services Tax) was implemented in India from which date?

(A) April 1, 2016
(B) November 8, 2016
(C) July 1, 2017
(D) More than one of the above
(E) None of the above

---

**Q32.** Which constitutional amendment enabled the implementation of GST in India?

(A) 91st Constitutional Amendment
(B) 101st Constitutional Amendment
(C) 86th Constitutional Amendment
(D) More than one of the above
(E) None of the above

---

**Q33.** SEBI (Securities and Exchange Board of India) is primarily responsible for regulating:

(A) Banking sector and monetary policy
(B) Insurance companies and pension funds
(C) Securities markets, stock exchanges, and mutual funds
(D) More than one of the above
(E) None of the above

---

**Q34.** The headquarters of SEBI is located in:

(A) New Delhi
(B) Chennai
(C) Mumbai
(D) More than one of the above
(E) None of the above

---

**Q35.** The "JAM Trinity" in financial inclusion refers to:

(A) Jan Dhan — Aadhaar — Mobile
(B) Joint Accounts — ATM — Mobile Banking
(C) Jan Dhan — Agriculture — MUDRA
(D) More than one of the above
(E) None of the above

---

**Q36.** Which payment system has a MINIMUM transaction limit of ₹2 lakh and is meant for LARGE VALUE transfers?

(A) NEFT (National Electronic Funds Transfer)
(B) UPI (Unified Payments Interface)
(C) RTGS (Real Time Gross Settlement)
(D) More than one of the above
(E) None of the above

---

**Q37.** MUDRA scheme provides loans to micro-enterprises under three categories. Which is the HIGHEST loan category?

(A) Shishu (up to ₹50,000)
(B) Kishore (₹50,000 to ₹5 lakh)
(C) Tarun (₹5 lakh to ₹10 lakh)
(D) More than one of the above
(E) None of the above

---

**Q38.** The demonetisation of ₹500 and ₹1000 notes was announced on which date?

(A) April 1, 2016
(B) November 8, 2016
(C) July 1, 2017
(D) More than one of the above
(E) None of the above

---

**Q39.** RBI is the regulator for which of the following?

(A) Stock markets (BSE, NSE)
(B) Insurance companies (LIC, etc.)
(C) Commercial banks and monetary policy in India
(D) More than one of the above
(E) None of the above

---

**Q40.** GDP (Gross Domestic Product) is different from GNP (Gross National Product). Which statement is CORRECT?

(A) GNP = GDP minus income earned abroad by Indians
(B) GDP = GNP + net factor income from abroad
(C) GNP = GDP + (income earned abroad by Indians) − (income earned in India by foreigners)
(D) More than one of the above
(E) None of the above

---

**Q41.** RBI's Reverse Repo Rate is the rate at which:

(A) RBI lends to commercial banks
(B) Commercial banks lend to RBI (banks park excess funds with RBI)
(C) Government borrows from RBI
(D) More than one of the above
(E) None of the above

---

**Q42.** SLR (Statutory Liquidity Ratio) requires banks to maintain a portion of their deposits in:

(A) Cash only with RBI
(B) Approved securities (government securities, gold, cash)
(C) Foreign currency reserves
(D) More than one of the above
(E) None of the above

---

**Q43.** NABARD (National Bank for Agriculture and Rural Development) was established in which year?

(A) 1969
(B) 1975
(C) 1982
(D) More than one of the above
(E) None of the above

---

**Q44.** UPI transactions crossed a world record. India processes more real-time digital transactions than any other country. The platform is operated by:

(A) RBI directly
(B) State Bank of India
(C) NPCI (National Payments Corporation of India)
(D) More than one of the above
(E) None of the above

---

**Q45.** Which category of bank is India Post Payments Bank (IPPB)?

(A) Small Finance Bank
(B) Payments Bank (deposits only, no loans)
(C) Regional Rural Bank
(D) More than one of the above
(E) None of the above

---

**Q46.** Muzaffarpur Litchi, a product from Bihar, holds which special recognition?

(A) UNESCO Cultural Heritage recognition
(B) GI Tag (Geographical Indication)
(C) ISO 9001 certification
(D) More than one of the above
(E) None of the above

---

**Q47.** GST Council is chaired by:

(A) Prime Minister of India
(B) RBI Governor
(C) Union Finance Minister
(D) More than one of the above
(E) None of the above

---

**Q48.** PM Jan Dhan Yojana (PMJDY) was launched in which year?

(A) 2012
(B) 2016
(C) 2014
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following is EXCLUDED from GST (not covered under GST)?

(A) Packaged food items
(B) Mobile phone services
(C) Petroleum products and alcohol
(D) More than one of the above
(E) None of the above

---

**Q50.** The IRDAI (Insurance Regulatory and Development Authority of India) is headquartered in:

(A) Mumbai
(B) New Delhi
(C) Hyderabad
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🔑 COMPLETE ANSWER KEY — DAY 31
## ATTEMPT ALL QUESTIONS BEFORE READING THIS!
# ═══════════════════════════════════════════════════════

---

## ✅ CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| **Q1** | **(C)** | Merge Sort: D&C + O(n log n) in ALL cases. Quick Sort is D&C but O(n²) worst case. Heap Sort is always O(n log n) but NOT D&C. So only Merge Sort satisfies BOTH conditions. |
| **Q2** | **(C)** | Quick Sort worst case = O(n²). Occurs when pivot is always min or max (sorted/reverse-sorted input with bad pivot). |
| **Q3** | **(C)** | Merge Sort needs O(n) extra space for the temporary arrays used during merging. This is a major disadvantage vs Quick Sort. |
| **Q4** | **(B)** | Heap Sort = O(n log n) all cases + NOT stable (swapping disrupts relative order of equal elements) + In-Place (O(1) extra space, sorts within the array). |
| **Q5** | **(C)** | Quick Sort worst case: already sorted + first/last element as pivot → unbalanced partition (n-1 and 0 elements each side) → O(n²). Random/median pivot avoids this. |
| **Q6** | **(C)** | Heap Sort uses HEAP data structure, not Divide & Conquer. Merge Sort and Quick Sort are both D&C. |
| **Q7** | **(B)** | Radix Sort is a NON-COMPARISON sort — it sorts by digit positions without ever comparing two elements against each other. This allows it to bypass the Ω(n log n) lower bound for comparison sorts. |
| **Q8** | **(C)** | T(n) = 2T(n/2) + O(n) is the recurrence of Merge Sort. It also describes Quick Sort AVERAGE case, but specifically it models Merge Sort's exact behaviour (always splits into equal halves). Since C is the primary/standard answer, C is correct. |
| **Q9** | **(C)** | Merge Sort is ideal for external sorting because: (1) reads data sequentially, (2) can merge sorted runs from disk files, (3) doesn't need random access. Quick Sort requires random access within the array. |
| **Q10** | **(C)** | Among Merge, Quick, Heap Sort — only MERGE SORT is STABLE. Quick Sort and Heap Sort are NOT stable. |
| **Q11** | **(C)** | The lower bound for comparison-based sorting is Ω(n log n). Proved via decision tree argument (n! permutations require log₂(n!) ≈ n log n height). |
| **Q12** | **(B)** | After Quick Sort's PARTITION step, the chosen pivot is placed in its EXACT FINAL SORTED POSITION. Elements to its left are all smaller, elements to its right are all larger. |
| **Q13** | **(C)** | Heap Sort: O(n log n) all cases ✓, O(1) extra space (in-place) ✓, NOT Divide & Conquer (uses Heap) ✓. Merge Sort: NOT in-place. Quick Sort: O(n²) worst case. |
| **Q14** | **(B)** | Merge Sort preferred when: stable sort required (equal elements maintain order), worst-case guarantee needed (guaranteed O(n log n)), external sorting. Not preferred when memory-constrained. |
| **Q15** | **(C)** | Building a heap (HEAPIFY from bottom up) takes O(n) time — NOT O(n log n) as many assume! This is because lower levels of the tree require fewer operations. Overall: O(n). |
| **Q16** | **(C)** | Array of size 8: Level 0 = 1 array of 8, Level 1 = 2 of 4, Level 2 = 4 of 2, Level 3 = 8 of 1 (single elements). log₂(8) = 3 levels deep. |
| **Q17** | **(B)** | To maintain STABILITY in Merge Sort: when equal elements appear, we take from the LEFT subarray FIRST. This preserves their original relative order. "L[i] <= R[j]" ensures left is taken first for equal elements. |
| **Q18** | **(B)** | In Radix Sort O(d × (n + k)): d = number of digits/passes (e.g., d=3 for 3-digit numbers), n = number of elements, k = range per digit (k=10 for decimal). |
| **Q19** | **(B)** | Quick Sort is faster in practice because: cache-friendly (works on contiguous memory, good spatial locality), smaller constant factors in O(n log n), in-place (no memory allocation overhead). |
| **Q20** | **(C)** | Merge Sort is: STABLE ✓, O(n log n) in all cases ✓, NOT in-place (needs O(n) space). Options A and B are wrong. C is the correct statement. |
| **Q21** | **(C)** | Heapify (fixing one node by sifting it down) takes O(log n) because in the worst case, the element travels from root to leaf, covering the height of the heap = log₂(n). |
| **Q22** | **(C)** | Radix Sort achieves O(n) for fixed-size integers. Counting Sort also achieves O(n+k). These are non-comparison sorts that bypass the Ω(n log n) lower bound. Heap and Merge Sort are O(n log n). |
| **Q23** | **(B)** | For LINKED LISTS, Merge Sort works efficiently with sequential access (no need to jump to index). Quick Sort is inefficient on linked lists because it requires random access for partitioning. Both A and B are relevant, making D possible, but B is the PRIMARY reason. |
| **Q24** | **(C)** | Requirements: O(1) space (in-place) ✓ Heap Sort, Worst O(n log n) ✓ Heap Sort, NOT stable ✓ Heap Sort. Merge Sort: NOT in-place. Quick Sort: O(n²) worst case. Heap Sort satisfies all three. |
| **Q25** | **(B)** | In memory-constrained environments, Heap Sort > Merge Sort because Heap Sort is IN-PLACE (O(1) extra memory) while Merge Sort requires O(n) extra space. Both have the same O(n log n) complexity, so memory is the deciding factor. |

---

## ✅ GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| **Q26** | **(C)** | UPI was developed and is operated by NPCI (National Payments Corporation of India). RBI regulates it, but NPCI built and manages it. |
| **Q27** | **(B)** | RBI Act was passed in 1934, RBI became OPERATIONAL from April 1, 1935. Banking Regulation Act 1949 is a different act (governs commercial banks). |
| **Q28** | **(B)** | Repo Rate = rate at which RBI LENDS to commercial banks (short-term, with securities as collateral). Reverse Repo = RBI BORROWS from banks. |
| **Q29** | **(B)** | CRR = percentage of deposits banks must keep as CASH with RBI. SLR is the one about government securities. CRR earns NO interest for banks. |
| **Q30** | **(B)** | First nationalisation: 1969 (14 banks, PM Indira Gandhi). Second: 1980 (6 more banks). SBI was already public since 1955 — not counted in these. |
| **Q31** | **(C)** | GST was rolled out from July 1, 2017 (midnight of June 30 — special midnight Parliament session). Not 2016. November 8, 2016 was demonetisation. |
| **Q32** | **(B)** | 101st Constitutional Amendment Act 2016 enabled GST by creating Articles 246A (GST), 269A (IGST), and 279A (GST Council). |
| **Q33** | **(C)** | SEBI regulates: securities markets (BSE, NSE), stock brokers, mutual funds, investment advisors. RBI handles banks. IRDAI handles insurance. |
| **Q34** | **(C)** | SEBI HQ is in Mumbai (Bandra Kurla Complex). RBI HQ also Mumbai. IRDAI HQ = Hyderabad. PFRDA = New Delhi. |
| **Q35** | **(A)** | JAM = Jan Dhan (bank account) + Aadhaar (identity verification) + Mobile (digital connectivity). Used for Direct Benefit Transfer to eliminate middlemen. |
| **Q36** | **(C)** | RTGS (Real Time Gross Settlement) has minimum ₹2 lakh transfer limit. It's for large-value, time-critical payments. NEFT and UPI have no such minimum. |
| **Q37** | **(C)** | MUDRA categories: Shishu = up to ₹50,000, Kishore = ₹50,000 to ₹5 lakh, Tarun = ₹5 lakh to ₹10 lakh. Tarun is highest. |
| **Q38** | **(B)** | Demonetisation announced November 8, 2016 (8 PM announcement by PM Modi). Old ₹500 and ₹1000 notes became invalid at midnight. |
| **Q39** | **(C)** | RBI regulates commercial banks (public, private, foreign banks) and sets monetary policy. SEBI handles stock markets. IRDAI handles insurance. |
| **Q40** | **(C)** | GNP = GDP + Net Factor Income from Abroad = GDP + (income earned by Indians abroad) − (income earned by foreigners in India). Option C is the correct formula. |
| **Q41** | **(B)** | Reverse Repo = rate at which commercial banks park their EXCESS funds with RBI. RBI pays this rate. Banks "lend" to RBI at reverse repo rate. |
| **Q42** | **(B)** | SLR requires banks to keep a percentage of their NDTL (Net Demand and Time Liabilities) in approved securities — government securities (G-Secs), gold, or cash. NOT just cash (that's CRR). |
| **Q43** | **(C)** | NABARD was established in 1982 (July 12, 1982) by an Act of Parliament, to promote agriculture credit. HQ: Mumbai. |
| **Q44** | **(C)** | NPCI operates UPI. RBI regulates (oversees) UPI, but does not operate it directly. SBI is just a participating bank. |
| **Q45** | **(B)** | India Post Payments Bank (IPPB) is a Payments Bank — can accept deposits (max ₹2 lakh per customer) but CANNOT give loans or credit. Other payments banks: Airtel, Jio, Fino, etc. |
| **Q46** | **(B)** | Muzaffarpur Litchi (Shahi Litchi) of Bihar received a GI Tag (Geographical Indication tag), protecting its unique identity. GI Tag protects traditional products from a specific region. |
| **Q47** | **(C)** | GST Council is chaired by the Union Finance Minister (currently Nirmala Sitharaman). Members are State Finance Ministers. Centre has 1/3 votes; States together have 2/3 votes. |
| **Q48** | **(C)** | PMJDY (Pradhan Mantri Jan Dhan Yojana) was launched on August 28, 2014 by PM Modi. Not 2012 or 2016. |
| **Q49** | **(C)** | Petroleum products (petrol, diesel, natural gas, ATF) and alcoholic beverages are OUTSIDE GST's scope. They are still taxed by states separately (VAT + central excise). |
| **Q50** | **(C)** | IRDAI HQ is in Hyderabad. RBI = Mumbai. SEBI = Mumbai. PFRDA = New Delhi. NABARD = Mumbai. IRDAI's Hyderabad location is a common exam question. |

---

# ═══════════════════════════════════════════════════════
# 🏆 DAY 31 — TOPPER'S QUICK REVISION CARD
# ═══════════════════════════════════════════════════════

## ⚡ CS — 12 MUST-REMEMBER FACTS

1. **Merge Sort:** D&C + O(n log n) ALL cases + STABLE + NOT in-place (O(n) space)
2. **Quick Sort:** D&C + O(n log n) avg + NOT stable + IN-PLACE + O(n²) worst (sorted input)
3. **Heap Sort:** NOT D&C + O(n log n) ALL cases + NOT stable + IN-PLACE (O(1))
4. **Radix Sort:** NOT comparison-based + O(nk) ≈ O(n) + STABLE + NOT in-place
5. **ONLY Merge Sort is stable** among the O(n log n) sorts
6. **ONLY Merge Sort needs O(n) extra space** among O(n log n) sorts
7. **Heap Sort = Merge's time + Quick's space** (best of both, but not stable)
8. **Lower bound** for comparison sort = Ω(n log n) — proven via decision tree
9. **External sorting** → Use Merge Sort (sequential access, works with disk)
10. **Quick Sort worst case** → sorted input + first/last pivot → O(n²)
11. **Building heap** = O(n) (not O(n log n)!) — common exam trap
12. **Heapify one node** = O(log n)

## ⚡ GS — 12 MUST-REMEMBER FACTS

1. **UPI** developed by NPCI; launched 2016; 24×7 instant payment; VPA-based
2. **NPCI** = National Payments Corporation of India; Mumbai; manages UPI, RuPay, NEFT, RTGS, IMPS
3. **RBI** founded 1935 (RBI Act 1934); HQ Mumbai; nationalised 1949
4. **Repo Rate** = RBI lends to banks | **Reverse Repo** = banks lend to RBI
5. **CRR** = Cash with RBI | **SLR** = Securities by bank
6. **Bank nationalisation:** 14 banks in 1969 + 6 banks in 1980 = 20 total
7. **GST:** July 1, 2017; 101st Amendment; 0/5/12/18/28% slabs; Petroleum EXCLUDED
8. **SEBI** = Securities regulator; Mumbai | **IRDAI** = Insurance regulator; **Hyderabad**
9. **RTGS** = minimum ₹2 lakh | **NEFT** = any amount, hourly | **UPI** = instant, any amount
10. **MUDRA:** Shishu (₹50K) → Kishore (₹5L) → Tarun (₹10L)
11. **JAM = Jan Dhan + Aadhaar + Mobile** → Direct Benefit Transfer
12. **Muzaffarpur Litchi** = Bihar's GI Tag product

---

## 📊 Day 31 Self-Assessment

| Category | Questions | My Score | Target |
|----------|-----------|----------|--------|
| CS Merge + Quick Sort (Q1-Q14) | 14 | /14 | 12+ |
| CS Heap + Radix + Tricky (Q15-Q25) | 11 | /11 | 10+ |
| GS UPI + RBI (Q26-Q39) | 14 | /14 | 12+ |
| GS GST + Banks + Bihar (Q40-Q50) | 11 | /11 | 10+ |
| **TOTAL** | **50** | **/50** | **44+** |

> **Score 44+/50 = TOPPER ZONE** 🏆
> **Score 37-43 = Good — review wrong answers tonight**
> **Score below 37 = Re-read concept sections, retry tomorrow**

---

## 📝 Tonight's 5-Bullet Summary (Write From Memory!)

1. Merge Sort: Time=____, Space=____, Stable?____, D&C?____
2. Quick Sort: Worst case=____, Why?____, In-place?____
3. Heap Sort: All cases=____, Stable?____, D&C?____
4. UPI developed by=____, launched in year=____, operated 24×7? ____
5. Bank nationalisation: ____ banks in ____ + ____ banks in ____ = ____ total

---

*Day 31 Complete ✅ | Tomorrow: Day 32 — Binary Search & Hashing + GS: Nobel Prize Winners*
*30% of Phase 1 done — you are building the topper foundation step by step!* 🎯
