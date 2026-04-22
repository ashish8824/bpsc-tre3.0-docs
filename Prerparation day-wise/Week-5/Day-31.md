# 📅 BPSC TRE 4.0 — DAY 31 COMPLETE STUDY MODULE
### Merge Sort & Quick Sort (Divide & Conquer) + Current Affairs: Banking & UPI System
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Merge Sort & Quick Sort — Divide & Conquer, Dry Runs, Complexity
> - Afternoon (1 hr): Current Affairs — Banking System & UPI
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Merge Sort & Quick Sort — Deep Conceptual Guide

---

## 🔷 SECTION 1: Divide & Conquer Paradigm — The Foundation

### Real-Life Analogy — The Tournament Bracket:

Imagine a **chess tournament with 16 players**:
- Direct competition (everyone vs everyone) = 16×15/2 = 120 matches
- Instead: DIVIDE into 8 pairs → winners play → repeat until one champion

The tournament approach = Divide & Conquer.
**Break the big problem into smaller, manageable sub-problems.**

### Another Analogy — Counting a Large Crowd:
```
Problem: Count 1,000,000 people in a stadium
Brute force: One person counts all → takes forever!

Divide & Conquer approach:
  Split into 10 sections of 100,000
  Each section-leader splits into 10 sub-sections of 10,000
  Each sub-section splits into 10 groups of 1,000
  ...until groups are small enough to count quickly
  Then COMBINE all counts: bottom-up addition

Total work is MUCH LESS because sub-problems are independent!
```

### The Three Steps of Divide & Conquer:

```
╔══════════════════════════════════════════════════════════╗
║         DIVIDE & CONQUER — THREE SACRED STEPS           ║
╠══════════════════════════════════════════════════════════╣
║                                                          ║
║  STEP 1: DIVIDE                                          ║
║    → Break the problem into SMALLER sub-problems         ║
║    → Usually: split array/problem into halves            ║
║    → Continues RECURSIVELY until base case reached       ║
║                                                          ║
║  STEP 2: CONQUER                                         ║
║    → SOLVE each sub-problem INDEPENDENTLY                ║
║    → Base case: sub-problem small enough to solve trivially ║
║    → Recursive case: apply same strategy to sub-problem  ║
║                                                          ║
║  STEP 3: COMBINE                                         ║
║    → MERGE results of sub-problems                       ║
║    → Build solution to original problem from sub-solutions ║
║    → This step's cost varies by algorithm                ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝

Classic Applications of D&C:
  → Merge Sort   (divide array, sort halves, MERGE)
  → Quick Sort   (PARTITION around pivot, sort partitions)
  → Binary Search (divide search space in half each time)
  → Strassen's Matrix Multiplication
  → Tower of Hanoi
```

### Recursion — The Engine of D&C:

```
Recursion = A function that CALLS ITSELF on smaller inputs

BASE CASE: The stopping condition (when sub-problem is trivially solved)
           In sorting: array of size 0 or 1 is already sorted!

RECURSIVE CASE: The function calls itself with smaller input

Example — Factorial:
  factorial(n) = n × factorial(n-1)  ← recursive case
  factorial(0) = 1                   ← base case

Without base case → INFINITE LOOP (stack overflow)!

D&C RECURSION PATTERN:
  solve(problem):
    if problem is small enough:     ← BASE CASE
        solve directly and return
    else:                           ← RECURSIVE CASE
        sub1 = smaller piece 1
        sub2 = smaller piece 2
        result1 = solve(sub1)       ← DIVIDE + CONQUER
        result2 = solve(sub2)       ← DIVIDE + CONQUER
        return combine(result1, result2)  ← COMBINE
```

### 🎯 PYQ FACT: Both Merge Sort AND Quick Sort use Divide & Conquer, but their approaches differ fundamentally:
```
Merge Sort: Does HEAVY WORK at COMBINE step (merging)
            DIVIDE is easy (just split in half)

Quick Sort: Does HEAVY WORK at DIVIDE step (partitioning)
            COMBINE is trivial (nothing to do after partition)
```

---

## 🔷 SECTION 2: MERGE SORT — The Reliable Workhorse

### Concept — The "Split and Merge" Strategy:

```
Real-Life: Two sorted decks of cards merged into one sorted deck
  Deck A: [2, 5, 8, 11]    Deck B: [3, 6, 9, 12]
  
  Compare top cards: 2 < 3 → take 2 from A → Result: [2]
  Compare top cards: 5 > 3 → take 3 from B → Result: [2, 3]
  Compare top cards: 5 < 6 → take 5 from A → Result: [2, 3, 5]
  ...continue until both decks empty
  Final: [2, 3, 5, 6, 8, 9, 11, 12]
  
This MERGE operation is the heart of Merge Sort!
```

### Algorithm — Top-Down Merge Sort:

```
mergeSort(arr, left, right):
    if left >= right:            ← BASE CASE: single element or empty
        return

    mid = (left + right) / 2    ← DIVIDE: find middle index

    mergeSort(arr, left, mid)    ← CONQUER: sort left half
    mergeSort(arr, mid+1, right) ← CONQUER: sort right half

    merge(arr, left, mid, right) ← COMBINE: merge two sorted halves
```

### The MERGE Function — Step by Step:

```
merge(arr, left, mid, right):
  Create two temporary arrays:
    L[] = arr[left..mid]       ← copy left half
    R[] = arr[mid+1..right]    ← copy right half

  i = 0  (pointer for L)
  j = 0  (pointer for R)
  k = left  (pointer for arr)

  WHILE both L and R have elements:
    if L[i] <= R[j]:           ← ≤ makes it STABLE!
        arr[k] = L[i]
        i++
    else:
        arr[k] = R[j]
        j++
    k++

  Copy remaining elements of L (if any) into arr
  Copy remaining elements of R (if any) into arr
```

### Complete Step-by-Step Dry Run — Array: [38, 27, 43, 3, 9, 82, 10]

```
INITIAL: [38, 27, 43, 3, 9, 82, 10]
         Indices: 0   1   2  3  4   5   6

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PHASE 1: DIVIDE (Recursive splitting — top-down)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Level 0:   [38, 27, 43, 3, 9, 82, 10]
                        |
            ┌───────────┴───────────┐
            |                       |
Level 1: [38, 27, 43]         [3, 9, 82, 10]
              |                       |
         ┌────┴────┐           ┌──────┴──────┐
         |          |           |              |
Level 2:[38]    [27, 43]    [3, 9]       [82, 10]
                  |               |               |
              ┌───┴───┐       ┌───┴───┐       ┌───┴───┐
              |         |     |         |     |         |
Level 3:    [27]      [43]  [3]       [9]  [82]      [10]

BASE CASES REACHED: Each sub-array has 1 element → already sorted!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PHASE 2: MERGE (Combining — bottom-up)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Level 3 → Level 2 MERGES:

MERGE [27] and [43]:
  Compare 27 and 43: 27 < 43 → take 27
  Only 43 remains → take 43
  Result: [27, 43] ✅

MERGE [3] and [9]:
  Compare 3 and 9: 3 < 9 → take 3
  Only 9 remains → take 9
  Result: [3, 9] ✅

MERGE [82] and [10]:
  Compare 82 and 10: 10 < 82 → take 10
  Only 82 remains → take 82
  Result: [10, 82] ✅

After Level 2 merges:
  [38]    [27, 43]    [3, 9]    [10, 82]

Level 2 → Level 1 MERGES:

MERGE [38] and [27, 43]:
  i→[38], j→[27,43]
  Compare 38 and 27: 27 < 38 → take 27 → Result: [27]
  Compare 38 and 43: 38 < 43 → take 38 → Result: [27, 38]
  Only [43] remains → take 43 → Result: [27, 38, 43] ✅

MERGE [3, 9] and [10, 82]:
  i→[3,9], j→[10,82]
  Compare 3 and 10: 3 < 10 → take 3  → Result: [3]
  Compare 9 and 10: 9 < 10 → take 9  → Result: [3, 9]
  Only [10, 82] remains → take both  → Result: [3, 9, 10, 82] ✅

After Level 1 merges:
  [27, 38, 43]    [3, 9, 10, 82]

Level 1 → Level 0 FINAL MERGE:

MERGE [27, 38, 43] and [3, 9, 10, 82]:
  Compare 27 and 3:  3 < 27  → take 3  → [3]
  Compare 27 and 9:  9 < 27  → take 9  → [3, 9]
  Compare 27 and 10: 10 < 27 → take 10 → [3, 9, 10]
  Compare 27 and 82: 27 < 82 → take 27 → [3, 9, 10, 27]
  Compare 38 and 82: 38 < 82 → take 38 → [3, 9, 10, 27, 38]
  Compare 43 and 82: 43 < 82 → take 43 → [3, 9, 10, 27, 38, 43]
  Only [82] remains → take 82           → [3, 9, 10, 27, 38, 43, 82] ✅

FINAL SORTED ARRAY: [3, 9, 10, 27, 38, 43, 82] ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VISUAL SUMMARY — The Full Recursion Tree:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

                [38,27,43,3,9,82,10]        ← LEVEL 0
                        ↕ split/merge
        [38,27,43]              [3,9,82,10]  ← LEVEL 1
             ↕                       ↕
    [38]  [27,43]           [3,9]  [82,10]  ← LEVEL 2
           ↕                  ↕       ↕
         [27][43]           [3][9] [82][10] ← LEVEL 3 (base)

MERGE BACK:
         [27,43]          [3,9]  [10,82]
    [27,38,43]                [3,9,10,82]
              [3,9,10,27,38,43,82]
```

### Why is Merge Sort O(n log n)?

```
LEVELS OF RECURSION:
  Array of n elements → halved each level → log₂n levels total

WORK PER LEVEL:
  At EACH level, the total number of elements being merged = n
  (No element is processed more than once per level)
  Work per level = O(n)

TOTAL WORK:
  O(n) per level × log₂n levels = O(n log n)

VISUAL — Work at Each Level (n=8):
  Level 3: 8 single elements   → 0 merge work (base cases)
  Level 2: Merge 4 pairs       → 8 total elements merged = O(8)
  Level 1: Merge 2 groups of 4 → 8 total elements merged = O(8)
  Level 0: Merge 2 groups of 4 → 8 total elements merged = O(8)
  
  Total = 3 levels × O(8) = 3 × O(n) = O(n log n) [since log₂8 = 3] ✓

IMPORTANT: ALL THREE CASES (best, avg, worst) = O(n log n)
  Why? Merge Sort ALWAYS splits evenly (it doesn't depend on input order!)
  The split is ALWAYS at the midpoint — predictable and consistent.
```

### Complexity Summary for Merge Sort:

```
Best Case:    O(n log n)  ← Same as worst — always consistent!
Average Case: O(n log n)
Worst Case:   O(n log n)
Space:        O(n)        ← Auxiliary array for merging — NOT in-place!
Stable:       YES         ← L[i] <= R[j] condition preserves equal element order
Recursive:    YES         ← Uses function call stack O(log n) for recursion
```

### 🚨 PYQ TRAP #1: Merge Sort Space Complexity
> Merge Sort requires O(n) extra space for the temporary arrays during merging.
> This makes it NOT in-place (unlike Bubble, Selection, Insertion which are O(1)).
> The recursion stack itself uses O(log n) space, but auxiliary merge arrays use O(n).
> **Total space = O(n)**. This is Merge Sort's main DISADVANTAGE.

---

## 🔷 SECTION 3: QUICK SORT — The Speed Champion

### Concept — The "Pivot and Partition" Strategy:

```
Real-Life Analogy — The Teacher Distributing Papers:
  Papers need to be sorted by roll number.
  
  Teacher picks a "reference paper" (PIVOT) with roll number = 25.
  
  "Everyone with roll < 25, go LEFT side."
  "Everyone with roll > 25, go RIGHT side."
  "Roll 25 is now in its CORRECT final position!"
  
  Now REPEAT this process for LEFT side and RIGHT side independently.
  
This is Quick Sort! The pivot ALWAYS ends up in its CORRECT POSITION after partitioning.
```

### Key Insight — Why It Works:

```
After partitioning:
  [elements < pivot] [PIVOT] [elements > pivot]
         ↑                          ↑
   Need sorting                Need sorting
   (recurse left)             (recurse right)
         ↑
   PIVOT is DONE — never moves again!

Each element becomes a pivot ONCE, ending up in its final position.
```

### Algorithm:

```
quickSort(arr, low, high):
    if low < high:                          ← BASE CASE: low >= high (0 or 1 elements)
        pivotIdx = partition(arr, low, high) ← DIVIDE: partition and find pivot's position
        quickSort(arr, low, pivotIdx - 1)    ← CONQUER: sort left of pivot
        quickSort(arr, pivotIdx + 1, high)   ← CONQUER: sort right of pivot
        ← No COMBINE step needed! (array is sorted in-place)

partition(arr, low, high):   ← Lomuto Partition Scheme
    pivot = arr[high]         ← Choose LAST element as pivot (common choice)
    i = low - 1               ← i tracks boundary of "elements less than pivot"
    
    for j = low to high-1:
        if arr[j] <= pivot:
            i++
            SWAP(arr[i], arr[j])    ← Move small element to left side
    
    SWAP(arr[i+1], arr[high])  ← Place pivot in correct position
    return i+1                 ← Return pivot's final index
```

### Complete Step-by-Step Dry Run — Array: [10, 80, 30, 90, 40, 50, 70]

```
INITIAL: [10, 80, 30, 90, 40, 50, 70]
          0   1   2   3   4   5   6

pivot = arr[high] = arr[6] = 70
i = low - 1 = -1

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PARTITION STEP (First call: low=0, high=6, pivot=70):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

j=0: arr[0]=10 <= pivot=70 → i++ (i=0) → SWAP arr[0] and arr[0]
     Array: [10, 80, 30, 90, 40, 50, 70]  (no visible change)
      i=0   j=0

j=1: arr[1]=80 > pivot=70  → NO action
     Array: [10, 80, 30, 90, 40, 50, 70]
      i=0

j=2: arr[2]=30 <= pivot=70 → i++ (i=1) → SWAP arr[1] and arr[2]
     Array: [10, 30, 80, 90, 40, 50, 70]
                ^^  ^^  ← swapped

j=3: arr[3]=90 > pivot=70  → NO action

j=4: arr[4]=40 <= pivot=70 → i++ (i=2) → SWAP arr[2] and arr[4]
     Array: [10, 30, 40, 90, 80, 50, 70]
                     ^^      ^^  ← swapped

j=5: arr[5]=50 <= pivot=70 → i++ (i=3) → SWAP arr[3] and arr[5]
     Array: [10, 30, 40, 50, 80, 90, 70]
                         ^^      ^^  ← swapped

Final step: SWAP arr[i+1]=arr[4] with arr[high]=arr[6] (pivot)
     Array: [10, 30, 40, 50, 70, 90, 80]
                             ^^      ←  70 is now in CORRECT POSITION!
                            (idx=4)

pivotIdx = 4  ← 70 is at index 4

PARTITION RESULT:
  [10, 30, 40, 50]  |  [70]  |  [90, 80]
  indices 0-3            4       indices 5-6
  (all < 70)          PIVOT     (all > 70)
  (need sorting)      FIXED!    (need sorting)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RECURSIVE BREAKDOWN (Visualization):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Call 1: quickSort([10,30,40,50,70,90,80], 0, 6)
  partition → pivot=70 goes to index 4
  Array: [10,30,40,50, 70, 90,80]

  Call 2: quickSort([10,30,40,50], 0, 3)
    pivot=50 → goes to index 3
    Array: [10,30,40, 50, ...]
    
    Call 4: quickSort([10,30,40], 0, 2)
      pivot=40 → goes to index 2
      Array: [10,30, 40, ...]
      
      Call 7: quickSort([10,30], 0, 1)
        pivot=30 → goes to index 1
        Array: [10, 30, ...]
        Calls quickSort([10], 0, 0) → BASE CASE
        Calls quickSort([], 2, 1) → BASE CASE (low > high)
      
      Call 8: quickSort([], 3, 2) → BASE CASE
    
    Call 5: quickSort([], 4, 3) → BASE CASE

  Call 3: quickSort([90,80], 5, 6)
    pivot=80 → 80 goes to index 5
    SWAP 90 and 80: Array: [..., 80, 90]
    Call 6: quickSort([90], 6, 6) → BASE CASE

FINAL SORTED ARRAY: [10, 30, 40, 50, 70, 80, 90] ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RECURSION TREE:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

         [10,30,40,50,70,90,80]  pivot=70
                   /        \
        [10,30,40,50]       [90,80]  pivot=50 / pivot=80
              /               \
        [10,30,40]            [80,90]
            /
         [10,30]  pivot=30
          /   \
        [10]  [ ]    ← base cases
```

### Why Quick Sort is O(n log n) Average but O(n²) Worst?

```
AVERAGE CASE — Balanced Partitions:
  Best scenario: pivot ALWAYS splits array into roughly EQUAL halves
  
  Level 0: 1 partition of n elements          → n work
  Level 1: 2 partitions of n/2 each           → n total work
  Level 2: 4 partitions of n/4 each           → n total work
  ...
  Total levels = log n → Total work = n × log n = O(n log n)

  [n elements]
       |
   [n/2][n/2]       ← balanced!
   / \    / \
[n/4][n/4][n/4][n/4] ← each level does O(n) total work

WORST CASE — Always Picks Min or Max as Pivot:
  When pivot is always the SMALLEST element (or largest):
  Array: [1, 2, 3, 4, 5] — sorted, pivot = last element = 5
  
  Call 1: partition of 5 elements → pivot=5 at end
          Left: [1,2,3,4] (n-1 elements), Right: []
  Call 2: partition of 4 elements → pivot=4 at end
          Left: [1,2,3] (n-2 elements), Right: []
  ...
  
  [1,2,3,4,5]         ← 5 elements, 4 comparisons
      |
  [1,2,3,4]  [5]      ← 4 elements, 3 comparisons
      |
  [1,2,3]    [4]      ← 3 elements, 2 comparisons
  ...
  
  Total = 4+3+2+1 = n(n-1)/2 = O(n²)
  This is DEGENERATE — one partition always empty!

VISUAL — Worst Case Tree:
  [5 elements]  → pivot at end
       |
  [4 elements]  → pivot at end
       |
  [3 elements]  → pivot at end
       |
  [2 elements]  → pivot at end
       |
  [1 element]   ← base case
  
  LOOKS LIKE A LINKED LIST, not a tree → O(n²)!
```

### When Does Worst Case Occur?

```
Worst case for Quick Sort (O(n²)):
  1. Array is ALREADY SORTED (ascending) + last element as pivot
  2. Array is SORTED IN REVERSE + last element as pivot
  3. All elements are EQUAL
  4. Pivot is always the minimum or maximum element

How to AVOID worst case:
  → Random pivot selection (randomized Quick Sort)
  → Median-of-three pivot (pick median of first, middle, last)
  → Three-way partitioning (for arrays with many duplicates)
```

### Complexity Summary for Quick Sort:

```
Best Case:    O(n log n)  ← pivot always splits evenly
Average Case: O(n log n)  ← expected for random input
Worst Case:   O(n²)       ← degenerate partitioning!
Space:        O(log n)    ← recursion stack (in-place for array!)
Stable:       NO          ← long-distance swaps disturb equal elements
Recursive:    YES
In-place:     YES         ← no auxiliary array needed!
```

### 🚨 PYQ TRAP #2: Quick Sort Worst Case Input
> Quick Sort's worst case is O(n²) when the pivot selection is poor.
> For a **sorted array with last element as pivot**, Quick Sort degrades to O(n²).
> This is counter-intuitive — a "sorted" input is the WORST case for naive Quick Sort!
> **Solution: Random pivot or median-of-three pivot selection avoids this.**

---

## 🔷 SECTION 4: Merge Sort vs Quick Sort — Master Comparison

### Side-by-Side Comparison Table:

| Property | Merge Sort | Quick Sort |
|----------|------------|------------|
| **Paradigm** | Divide & Conquer | Divide & Conquer |
| **Best Case** | O(n log n) | O(n log n) |
| **Average Case** | O(n log n) | O(n log n) |
| **Worst Case** | O(n log n) | O(n²) |
| **Space** | O(n) — auxiliary array | O(log n) — recursion stack |
| **In-Place?** | ❌ NO | ✅ YES |
| **Stable?** | ✅ YES | ❌ NO |
| **Heavy Work** | COMBINE (merge) step | DIVIDE (partition) step |
| **Performance** | Consistent, predictable | Faster in practice |
| **Cache** | Poor (random access) | Good (sequential access) |
| **Preferred for** | Linked lists, stable sort needed | Arrays, general-purpose |
| **Recursion depth** | O(log n) always | O(log n) avg; O(n) worst |

### The Key Philosophical Difference:

```
MERGE SORT — "Easy Split, Hard Merge":
  DIVIDE:  Always split EXACTLY in half → trivial, O(1)
  CONQUER: Sort each half recursively
  COMBINE: Carefully merge two sorted halves → O(n) work

  Think of it as: "I'll worry about sorting LATER when I merge"

QUICK SORT — "Hard Split, Easy Combine":
  DIVIDE:  Intelligently PARTITION around pivot → O(n) work per level
  CONQUER: Sort each partition recursively
  COMBINE: NOTHING! Partitions are already in-place → O(1)

  Think of it as: "I'll do all the smart work UPFRONT in partitioning"
```

### Why Quick Sort is Usually FASTER in Practice (Despite Same Big-O)?

```
1. CACHE EFFICIENCY: Quick Sort accesses array elements sequentially
                     Merge Sort uses auxiliary arrays → cache misses

2. CONSTANTS: Quick Sort's hidden constant factor is smaller
              O(n log n) with constant 1 vs O(n log n) with constant 2

3. IN-PLACE: Quick Sort doesn't allocate extra memory
             Merge Sort allocates O(n) extra → malloc/free overhead

4. BRANCH PREDICTION: CPU can predict Quick Sort's patterns better

RESULT: Quick Sort is ~2-3x faster than Merge Sort in practice
        on typical in-memory data, despite same asymptotic complexity.

BUT: When worst case matters → Merge Sort is safer!
```

---

## 🔷 SECTION 5: Other Important Sorting Algorithms (Brief)

### HEAP SORT → O(n log n), NOT Stable

```
Based on: Binary Heap data structure
Algorithm:
  Step 1: BUILD MAX-HEAP from array → O(n)
  Step 2: Repeatedly EXTRACT MAX element:
          - Swap root (max) with last element
          - Reduce heap size by 1
          - Heapify down to restore heap property
          - Repeat until empty
  
Time:  O(n log n) — ALWAYS (best, avg, worst)
Space: O(1) — in-place!
Stable: NO — heap operations cause non-local swaps

COMPARISON with Merge Sort:
  Same O(n log n) time, BUT O(1) space (unlike Merge Sort's O(n))
  However NOT stable (unlike Merge Sort)
  Slower in practice than Quick Sort (poor cache behavior)

KEY EXAM FACT: Heap Sort = O(n log n) + O(1) space + Unstable
               Merge Sort = O(n log n) + O(n) space + Stable
```

### RADIX SORT → O(n·k), Non-Comparison Based

```
Key Insight: Avoids COMPARISONS entirely!
             Sorts digit by digit, from least significant to most significant.

Algorithm: For each digit position (units, tens, hundreds...):
           Use COUNTING SORT (stable) to sort by that digit

Example: Sort [170, 45, 75, 90, 802, 24, 2, 66]

Pass 1 (Units digit):
  [170, 90, 802, 2, 24, 45, 75, 66]
   ^0    ^0   ^2  ^2  ^4  ^5  ^5  ^6

Pass 2 (Tens digit):
  [802, 2, 24, 45, 66, 170, 75, 90]

Pass 3 (Hundreds digit):
  [2, 24, 45, 66, 75, 90, 170, 802] ✅

Time Complexity:
  O(n·k) where k = number of digits (or passes)
  For integers with d digits: O(d·n)
  If d is constant (e.g., 32-bit ints): O(n) effectively!

WHY FASTER THAN COMPARISON SORTS?
  Comparison-based sorting has a LOWER BOUND of Ω(n log n)
  Radix Sort BYPASSES comparisons → can beat this lower bound!
  BUT: Only works for integers / strings (not arbitrary comparison)

Space: O(n + k) — needs counting array
Stable: YES (uses stable counting sort at each step)

🎯 PYQ FACT: Radix Sort is NOT comparison-based.
             Comparison-based sorting lower bound = Ω(n log n).
             Radix Sort can achieve O(n) time complexity.
```

### Complete Sorting Algorithm Reference:

| Algorithm | Best | Average | Worst | Space | Stable | Type |
|-----------|------|---------|-------|-------|--------|------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) | ✅ | Comparison |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) | ❌ | Comparison |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) | ✅ | Comparison |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ | Comparison |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) | ❌ | Comparison |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) | ❌ | Comparison |
| Radix Sort | O(nk) | O(nk) | O(nk) | O(n+k) | ✅ | Non-Comparison |

### 🚨 PYQ TRAP #3: Stable + O(n log n) Simultaneously
```
EXAM QUESTION: "Which sorting algorithm is BOTH stable AND O(n log n) in worst case?"
ANSWER: Merge Sort ONLY (among standard algorithms)

  Merge Sort: Stable ✅ + O(n log n) worst ✅
  Quick Sort: Stable ❌ (though O(n log n) avg)
  Heap Sort:  Stable ❌ (though O(n log n) worst)
  
  Merge Sort is the ONLY standard algorithm that is BOTH stable AND guaranteed O(n log n).
```

### 🚨 PYQ TRAP #4: Lower Bound for Comparison Sorting
```
THEORETICAL LOWER BOUND for comparison-based sorting = Ω(n log n)
This means NO comparison-based algorithm can ALWAYS be better than O(n log n).

Proof idea: Sorting n elements has n! possible orderings.
A binary decision tree needs at least log₂(n!) ≈ n log n leaves.
Therefore, at least n log n comparisons are needed in worst case.

IMPLICATION: Bubble, Insertion, Selection (O(n²)) are suboptimal.
             Merge, Quick, Heap (O(n log n)) are OPTIMAL for comparison sorting.
             Radix, Counting, Bucket (O(n)) bypass by avoiding comparisons!
```

---

## 🔷 SECTION 6: Recursion Tree Analysis

### How to Analyse Merge Sort Recursion:

```
MASTER THEOREM (simplified for exams):
For recurrence: T(n) = aT(n/b) + f(n)

Merge Sort: T(n) = 2T(n/2) + O(n)
  a = 2 (two subproblems)
  b = 2 (each is n/2 size)
  f(n) = O(n) (merge step)
  
  Since f(n) = O(n) = O(n^log_b(a)) = O(n^log_2(2)) = O(n^1) = O(n)
  → This is the "balanced" case → T(n) = O(n log n) ✓

Quick Sort: T(n) = T(n-1) + O(n) [worst case — unbalanced]
  This is the sum: n + (n-1) + (n-2) + ... + 1 = O(n²)
  
  T(n) = 2T(n/2) + O(n) [average case — balanced]
  Same as Merge Sort → O(n log n) ✓
```

---

# PART 2: GENERAL STUDIES
## 💳 Current Affairs — Banking System & UPI: India's Digital Payment Revolution

---

## 🔷 SECTION 1: India's Banking Structure

### Overview of Indian Banking System:

```
APEX BODY: Reserve Bank of India (RBI)
  Founded: 1 April 1935 (under RBI Act, 1934)
  Nationalised: 1 January 1949
  HQ: Mumbai (Central Office)
  Governor (as of 2024): Sanjay Malhotra
                         (Replaced Shaktikanta Das on 11 Dec 2024)
  Role: Central Bank of India — regulates all banks, controls money supply,
        manages foreign exchange, issues currency, acts as banker to government

SCHEDULED BANKS (registered under RBI Act Schedule 2):
  → Public Sector Banks (PSBs): Government owned (> 50% stake)
      Example: SBI, PNB, Bank of Baroda, Union Bank, Canara Bank
  → Private Sector Banks: Privately owned
      Example: HDFC Bank, ICICI Bank, Axis Bank, Kotak Mahindra
  → Foreign Banks: Headquartered abroad, operating in India
      Example: Citibank, HSBC, Standard Chartered
  → Regional Rural Banks (RRBs): Serve rural areas; sponsored by PSBs
  → Small Finance Banks (SFBs): Serve small borrowers, unbanked sections
  → Payments Banks: Accept deposits, offer payments — CANNOT give loans
      Example: Paytm Payments Bank, Airtel Payments Bank, India Post Payments Bank
```

### 🎯 PYQ FACT: Bank Nationalisation
```
1st Round: 14 major banks nationalised on 19 July 1969 (under PM Indira Gandhi)
2nd Round:  6 more banks nationalised on 15 April 1980
Total originally nationalised: 20 banks
Current PSBs: 12 (after mergers — several merged in 2019-2020)
Largest PSB: State Bank of India (SBI)
Largest bank by assets: SBI

SBI was formed by merger of:
  Imperial Bank of India → SBI (1955) + merger of 7 associate banks (2017)
```

---

## 🔷 SECTION 2: Digital Payments Ecosystem

### Evolution of Payments in India:

```
PHASE 1 (Pre-2000): Cash dominant, cheques for large transactions
PHASE 2 (2000-2010): Internet banking, NEFT, RTGS introduced
PHASE 3 (2010-2016): Mobile banking, IMPS launched (2010)
PHASE 4 (2016-present): UPI revolution, Demonetisation boost (Nov 2016)
PHASE 5 (2020-present): COVID-19 accelerates contactless payments
```

### Key Payment Systems — Quick Reference:

| System | Full Form | Settlement | Minimum | Maximum | Timing |
|--------|-----------|-----------|---------|---------|--------|
| **NEFT** | National Electronic Funds Transfer | Batch (hourly) | No min | No limit | 24×7 |
| **RTGS** | Real Time Gross Settlement | Real-time | ₹2 lakh | No limit | 24×7 |
| **IMPS** | Immediate Payment Service | Instant | ₹1 | ₹5 lakh | 24×7 |
| **UPI** | Unified Payments Interface | Instant | ₹1 | ₹1 lakh* | 24×7 |

*UPI limit varies: ₹1 lakh general; ₹2 lakh for some categories; ₹5 lakh for tax/medical

### 🎯 PYQ FACTS:
```
NEFT: Introduced 2005; operated in hourly batches; now 24×7 (from Dec 2019)
RTGS: For HIGH VALUE transactions (min ₹2 lakh); Real-Time = instant settlement
IMPS: Launched November 2010 by NPCI; First INSTANT interbank payment system
UPI: Launched April 2016 by NPCI; Built on IMPS infrastructure
```

---

## 🔷 SECTION 3: UPI — Unified Payments Interface

### What is UPI?

```
UPI = Unified Payments Interface

Developer:  NPCI (National Payments Corporation of India)
Launched:   11 April 2016 (soft launch); widespread adoption from 2017
Regulator:  Reserve Bank of India (RBI) — oversight
Operated by: NPCI (under guidance of RBI and IBA)

Core Idea: A SINGLE INTERFACE that connects all banks through one mobile application
           No need to share bank account number or IFSC code!
           Uses VPA (Virtual Payment Address) — like "yourname@bankname"
```

### What is NPCI?

```
NPCI = National Payments Corporation of India
Type: Not-for-profit company under Companies Act
Established: 2008 (incorporated December 2008)
Promoted by: RBI + IBA (Indian Banks' Association)
HQ: Mumbai

NPCI's Products/Systems:
  → UPI (Unified Payments Interface)
  → IMPS (Immediate Payment Service)
  → RuPay (Indian debit/credit card network — Indian alternative to Visa/Mastercard)
  → FASTag (Electronic toll collection)
  → NACH (National Automated Clearing House — bulk transfers)
  → BHIM App (Bharat Interface for Money)
  → Aadhaar-enabled Payment System (AePS)
```

### How UPI Works — Step by Step:

```
ACTORS:
  Payer (Sender)          → Has UPI app (PhonePe, GPay, BHIM, Paytm, etc.)
  Payee (Receiver)        → Has UPI VPA or QR code
  Payer's Bank (PSP)      → Payment Service Provider (remitting bank)
  Payee's Bank            → Beneficiary bank
  NPCI                    → Central switch — routes the transaction
  
UPI TRANSACTION FLOW:

Step 1: INITIATE
  Payer opens UPI app on smartphone
  Enters payee's VPA (e.g., "shop@upi") OR scans QR code OR enters phone number
  Enters amount and optional remarks

Step 2: AUTHENTICATE
  Payer enters 4-6 digit UPI PIN
  (Linked to debit card — set up once during registration)

Step 3: REQUEST SENT
  App sends request to Payer's Bank's UPI system

Step 4: NPCI ROUTES
  Payer's Bank sends transaction to NPCI (central switch)
  NPCI identifies Payee's bank from VPA

Step 5: VERIFICATION
  NPCI verifies account existence and balance with Payer's bank
  Routes to Payee's bank

Step 6: SETTLEMENT
  Money debited from Payer's account
  Money credited to Payee's account
  BOTH receive instant notification

Step 7: CONFIRMATION
  "Transaction Successful" message on app
  UTR (Unique Transaction Reference) number generated

TOTAL TIME: ~1-3 seconds end-to-end!

UPI FLOW DIAGRAM:
  [PAYER's PHONE]
       |  UPI PIN entered
       ↓
  [PAYER's BANK / PSP]  ←→  [NPCI SWITCH]  ←→  [PAYEE's BANK]
       ↓                                              ↓
  Debit payer's account                   Credit payee's account
       ↓                                              ↓
  SMS/Notification ←←←←←←←←←←←←←←←← SMS/Notification
```

### VPA — Virtual Payment Address:

```
VPA = Virtual Payment Address (also called UPI ID)
Format: username@bankhandle

Examples:
  rahul@sbi         (SBI UPI ID)
  priya@paytm       (Paytm)
  shop@ybl          (Yes Bank / PhonePe uses @ybl)
  user@oksbi        (Google Pay uses @oksbi, @okicici, etc.)
  merchant@upi      (Generic merchant VPA)

ADVANTAGE: User never shares bank account number or IFSC!
           VPA is an ALIAS — maps to actual bank account behind the scenes.
```

### Key Features of UPI:

```
✅ 24×7×365 availability — works even on bank holidays
✅ Instant fund transfer — real-time settlement
✅ No sharing of bank details — VPA acts as alias
✅ Multi-bank account linking — one app, multiple accounts
✅ Collect/Pull payments — payee can request money from payer
✅ QR code payments — scan and pay
✅ Bill splitting — split bills among groups
✅ Scheduled payments — set future-dated transfers
✅ Low cost — very low transaction fees (often zero for users)
✅ Interoperable — works across all banks and payment apps
✅ UPI Lite — offline small payments up to ₹500 per transaction
✅ UPI 123PAY — for feature phones (no internet required!)
✅ UPI ONE WORLD — for foreign visitors to India (pre-paid wallet UPI)
```

### BHIM App — The Government UPI App:

```
BHIM = Bharat Interface for Money
Launched: 30 December 2016 (by PM Narendra Modi)
Developer: NPCI
Named after: Dr. B.R. Ambedkar (BHIM = initials)
Purpose: Government-promoted simple UPI app accessible to all
Feature: Works on basic smartphones; Hindi and other language support
```

### 🎯 PYQ FACTS about UPI:
```
UPI Launched:        11 April 2016 (by NPCI)
BHIM Launched:       30 December 2016
Developer:           NPCI (National Payments Corporation of India)
Regulated by:        RBI
Standard limit:      ₹1 lakh per transaction
Based on:            IMPS infrastructure
VPA format:          username@bankhandle
Annual Volume (2023-24): Over 131 billion transactions
Value (2023-24):     ₹199+ lakh crore (~$2.4 trillion)
Countries with UPI:  Singapore, UAE, Bhutan, Nepal, Sri Lanka, France, UK, etc.
India's UPI share:   India processes ~46% of global real-time payment transactions!
```

---

## 🔷 SECTION 4: RuPay — India's Own Card Network

```
RuPay = Rupee + Payment (blend word)
Developer: NPCI
Launched: 2012
Purpose: Indian domestic card network — alternative to Visa, Mastercard, AMEX
Used on: Debit cards, Credit cards, Prepaid cards

KEY FACTS:
  RuPay cards for PM Jan Dhan Yojana beneficiaries
  Accepted on: ATMs, PoS terminals, e-commerce in India
  International acceptance expanding (now works in Bhutan, Singapore, UAE, etc.)
  Lower transaction fees than Visa/Mastercard → benefits merchants
  Government promotes RuPay for sovereignty (data stays in India!)
  
🎯 PYQ: RuPay is India's domestic card network developed by NPCI.
         It competes with Visa and Mastercard.
```

---

## 🔷 SECTION 5: Demonetisation & Digital Push

```
DEMONETISATION: 8 November 2016
  PM Narendra Modi announced withdrawal of ₹500 and ₹1000 notes
  Objectives: Curb black money, counterfeit currency, push digital payments
  New notes: ₹500 (redesigned) and ₹2000 introduced
  
IMPACT ON DIGITAL PAYMENTS:
  → Massive surge in UPI adoption (BHIM launched same month!)
  → Paytm wallets grew from 17 million to 177 million users in weeks
  → UPI transactions jumped from millions to billions
  → Permanently changed India's payment culture
  
NOTE: ₹2000 notes were WITHDRAWN from circulation in May 2023
      (Not demonetised — they remained legal tender but called back)
```

---

## 🔷 SECTION 6: Key Banking Terms for MCQs

```
REPO RATE:     Rate at which RBI lends to commercial banks
               (Higher repo rate → banks borrow less → less money in economy → controls inflation)
               Current (2024): 6.5% (after RBI rate decisions in recent MPC meetings)

REVERSE REPO:  Rate at which RBI borrows from commercial banks
               (Parked funds earn this rate)
               Phased out — now replaced by SDF (Standing Deposit Facility) rate

CRR:           Cash Reserve Ratio — % of NDTL banks must keep as CASH with RBI
               (Not used for lending — sits idle with RBI)

SLR:           Statutory Liquidity Ratio — % of NDTL banks must hold in:
               → Cash + Gold + Government securities
               (Can earn interest — different from CRR)

PLR/MCLR:      Prime Lending Rate / Marginal Cost of Funds-Based Lending Rate
               Base rate below which banks cannot normally lend

MPC:           Monetary Policy Committee — sets Repo Rate
               Headed by RBI Governor; meets every 2 months

NDTL:          Net Demand and Time Liabilities (total deposits of bank)
               CRR and SLR are calculated as % of NDTL

NPA:           Non-Performing Asset — loan where interest/principal unpaid for 90+ days

NBFC:          Non-Banking Financial Company — provides loans but CANNOT accept demand deposits
               Example: LIC Housing Finance, Muthoot Finance, Bajaj Finance
```

---

## 🔷 SECTION 7: India as Global UPI Leader

```
INTERNATIONAL UPI EXPANSION:
  Countries where UPI accepted (as of 2024):
  → Singapore (SGQR), UAE, Bahrain, Oman, Qatar, Kuwait
  → France (Eiffel Tower accepts UPI!), UK
  → Bhutan (first country to adopt UPI interface, 2021)
  → Nepal, Sri Lanka, Malaysia, Thailand
  → Mauritius
  
G20 CONTEXT:
  India pushed UPI as a model for Global Digital Public Infrastructure (DPI)
  at G20 2023 Summit
  "One Future Alliance" for DPI — sharing India's digital stack with world

UPI GLOBAL STATS (2023-24):
  → India = ~46% of global real-time payment transactions
  → More real-time payments than USA + China + UK + Germany COMBINED!
  → UPI processed 131+ billion transactions in FY2024
  
AWARDS:
  → RBI and NPCI received Bank for International Settlements (BIS) recognition
  → UPI called one of the world's most successful payment systems
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Divide & Conquer, Merge Sort, Quick Sort, Heap Sort, Radix Sort

---

**Q1.** Which of the following correctly describes the THREE steps of Divide & Conquer?
(A) Divide, Debug, Deploy
(B) Divide, Conquer, Combine
(C) Split, Sort, Merge
(D) More than one of the above
(E) None of the above

---

**Q2.** Merge Sort's WORST CASE time complexity is:
(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q3.** Quick Sort's WORST CASE time complexity occurs when:
(A) The array is already sorted and pivot = last element
(B) The array has all equal elements
(C) Both A and B lead to worst case
(D) More than one of the above (A, B, and any case where pivot is always min/max)
(E) None of the above

---

**Q4.** Which of the following sorting algorithms is STABLE among these options?
(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q5.** The SPACE complexity of Merge Sort is:
(A) O(1) — in-place
(B) O(log n) — recursion only
(C) O(n) — auxiliary array required
(D) More than one of the above
(E) None of the above

---

**Q6.** In Merge Sort, the HEAVY work (most computational effort) happens at which step?
(A) Divide step — splitting array into halves
(B) Combine step — merging two sorted halves
(C) Both equally
(D) More than one of the above
(E) None of the above

---

**Q7.** In Quick Sort, which step involves the HEAVY computational work?
(A) Divide (Partition) step — placing pivot correctly
(B) Combine step — merging sorted partitions
(C) Conquer step — after recursion
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the BEST CASE time complexity of Quick Sort?
(A) O(n)
(B) O(n²)
(C) O(n log n)
(D) More than one of the above
(E) None of the above

---

**Q9.** After one PARTITION step in Quick Sort with pivot = last element on array [10, 80, 30, 90, 40, 50, 70], the pivot (70) ends up at which position?
(A) Position 3 (0-indexed)
(B) Position 4 (0-indexed)
(C) Position 5 (0-indexed)
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following correctly describes Merge Sort's time complexity across ALL cases?
(A) Best O(n), Average O(n log n), Worst O(n²)
(B) Best O(n log n), Average O(n log n), Worst O(n log n)
(C) Best O(n log n), Average O(n log n), Worst O(n²)
(D) More than one of the above
(E) None of the above

---

**Q11.** Quick Sort is generally FASTER than Merge Sort in practice because:
(A) Quick Sort has better Big-O notation
(B) Quick Sort has better cache performance and no auxiliary memory allocation
(C) Quick Sort is stable and Merge Sort is not
(D) More than one of the above
(E) None of the above

---

**Q12.** The recurrence relation T(n) = 2T(n/2) + O(n) corresponds to which algorithm?
(A) Quick Sort worst case
(B) Merge Sort (and Quick Sort average case)
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q13.** Heap Sort has which combination of properties?
(A) Stable + O(n log n) + O(1) space
(B) Not stable + O(n log n) + O(1) space
(C) Stable + O(n log n) + O(n) space
(D) More than one of the above
(E) None of the above

---

**Q14.** Which sorting algorithm can achieve O(n) time complexity under the right conditions?
(A) Merge Sort
(B) Quick Sort
(C) Radix Sort
(D) More than one of the above (Radix Sort and Counting Sort — non-comparison based)
(E) None of the above

---

**Q15.** The theoretical lower bound for comparison-based sorting algorithms is:
(A) O(n)
(B) O(n²)
(C) Ω(n log n)
(D) More than one of the above
(E) None of the above

---

**Q16.** In Merge Sort, the condition `if (L[i] <= R[j])` (using <=) rather than `<` ensures:
(A) Faster execution
(B) Stability — equal elements from left subarray are taken first
(C) Less memory usage
(D) More than one of the above
(E) None of the above

---

**Q17.** Quick Sort is described as an IN-PLACE sorting algorithm primarily because:
(A) It sorts in O(1) time
(B) It does not require auxiliary arrays for sorting — rearranges within original array
(C) It always achieves O(n log n) complexity
(D) More than one of the above
(E) None of the above

---

**Q18.** Merge Sort is preferred over Quick Sort for sorting a LINKED LIST because:
(A) Merge Sort works with O(1) extra space on linked lists
(B) Quick Sort needs random access (index-based), which linked lists don't efficiently support
(C) Merge Sort is unstable and linked lists need instability
(D) More than one of the above (A and B are both valid reasons)
(E) None of the above

---

**Q19.** Both Merge Sort and Quick Sort use which algorithmic paradigm?
(A) Greedy Algorithm
(B) Dynamic Programming
(C) Divide and Conquer
(D) More than one of the above
(E) None of the above

---

**Q20.** Which sorting algorithm is BOTH stable AND has guaranteed O(n log n) in worst case?
(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q21.** In Quick Sort's worst case scenario, the recursion tree resembles:
(A) A balanced binary tree with O(log n) levels
(B) A skewed tree (like a linked list) with O(n) levels
(C) A complete binary tree with exactly n leaves
(D) More than one of the above
(E) None of the above

---

**Q22.** Radix Sort differs from Merge/Quick/Heap Sort in a fundamental way — what is it?
(A) Radix Sort is slower in all cases
(B) Radix Sort does NOT use comparisons to sort
(C) Radix Sort requires more memory
(D) More than one of the above
(E) None of the above

---

**Q23.** What is the space complexity of Quick Sort due to its recursion stack (average case)?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q24.** The COMBINE step in Quick Sort is:
(A) Merging two sorted subarrays
(B) Non-existent / trivial (O(1)) — partitions are already in correct relative positions
(C) Partitioning around pivot
(D) More than one of the above
(E) None of the above

---

**Q25.** For sorting 1 million records where STABILITY is required and input may be nearly sorted, which is the BEST choice?
(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: UPI, NPCI, Banking System, Digital Payments

---

**Q26.** UPI stands for:
(A) Universal Payment Interface
(B) Unified Payments Interface
(C) United Payment Initiative
(D) More than one of the above
(E) None of the above

---

**Q27.** UPI was developed and is operated by:
(A) Reserve Bank of India (RBI)
(B) State Bank of India (SBI)
(C) NPCI (National Payments Corporation of India)
(D) More than one of the above
(E) None of the above

---

**Q28.** NPCI was established in which year?
(A) 2005
(B) 2008
(C) 2016
(D) More than one of the above
(E) None of the above

---

**Q29.** UPI was officially launched in which year?
(A) 2014
(B) 2016
(C) 2018
(D) More than one of the above
(E) None of the above

---

**Q30.** What is a VPA (Virtual Payment Address) in UPI?
(A) A 16-digit bank account number used for UPI transactions
(B) A unique identifier (e.g., user@bank) that acts as an alias for a bank account
(C) A physical card used for UPI payments
(D) More than one of the above
(E) None of the above

---

**Q31.** BHIM app (Bharat Interface for Money) was launched on:
(A) 11 April 2016
(B) 8 November 2016
(C) 30 December 2016
(D) More than one of the above
(E) None of the above

---

**Q32.** The BHIM app is named after which personality?
(A) Bhimrao Ramji Ambedkar
(B) Bhim Singh Rawat
(C) Bhimsen Joshi
(D) More than one of the above
(E) None of the above

---

**Q33.** For which type of transactions is RTGS used?
(A) Small retail transactions below ₹1000
(B) High-value transactions (minimum ₹2 lakh) with real-time settlement
(C) Bulk salary payments
(D) More than one of the above
(E) None of the above

---

**Q34.** Which of the following is India's DOMESTIC card payment network, developed as an alternative to Visa and Mastercard?
(A) FASTag
(B) RuPay
(C) NACH
(D) More than one of the above
(E) None of the above

---

**Q35.** The Reserve Bank of India was established on:
(A) 15 August 1947
(B) 1 April 1935
(C) 26 January 1950
(D) More than one of the above
(E) None of the above

---

**Q36.** IMPS (Immediate Payment Service) was launched by NPCI in which year?
(A) 2016
(B) 2005
(C) 2010
(D) More than one of the above
(E) None of the above

---

**Q37.** The standard per-transaction limit for UPI payments is:
(A) ₹10,000
(B) ₹50,000
(C) ₹1 lakh (₹1,00,000)
(D) More than one of the above
(E) None of the above

---

**Q38.** India's first wave of bank nationalisation (14 banks) occurred in which year?
(A) 1955
(B) 1969
(C) 1980
(D) More than one of the above
(E) None of the above

---

**Q39.** Which payment system involves the HIGHEST minimum transaction amount?
(A) IMPS
(B) UPI
(C) RTGS (minimum ₹2 lakh)
(D) More than one of the above
(E) None of the above

---

**Q40.** NPCI was promoted by:
(A) Only the RBI
(B) Only the Government of India's Finance Ministry
(C) RBI and IBA (Indian Banks' Association) jointly
(D) More than one of the above
(E) None of the above

---

**Q41.** UPI 123PAY is designed for:
(A) High-net-worth individuals making large transactions
(B) Feature phone users without internet access
(C) International UPI users outside India
(D) More than one of the above
(E) None of the above

---

**Q42.** Which country was the FIRST to adopt India's UPI interface internationally?
(A) Singapore
(B) UAE
(C) Bhutan
(D) More than one of the above
(E) None of the above

---

**Q43.** The Repo Rate is the rate at which:
(A) Commercial banks lend to RBI
(B) RBI lends to commercial banks (short-term)
(C) Banks lend to retail customers
(D) More than one of the above
(E) None of the above

---

**Q44.** CRR (Cash Reserve Ratio) is the percentage of a bank's NDTL that must be:
(A) Invested in government securities
(B) Kept as CASH with the RBI (earns no interest)
(C) Lent to priority sector borrowers
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following is a Payments Bank (cannot give loans, only accepts deposits and provides payments)?
(A) HDFC Bank
(B) Axis Bank
(C) India Post Payments Bank
(D) More than one of the above
(E) None of the above

---

**Q46.** India's demonetisation, which gave a major boost to digital payments, was announced on:
(A) 26 November 2016
(B) 8 November 2016
(C) 30 December 2016
(D) More than one of the above
(E) None of the above

---

**Q47.** UPI LITE is designed for:
(A) Transactions above ₹1 lakh
(B) Small offline transactions up to ₹500 per transaction
(C) International money transfers
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following is a product of NPCI?
(A) FASTag (electronic toll collection)
(B) RuPay card network
(C) BHIM UPI app
(D) More than one of the above (all three are NPCI products)
(E) None of the above

---

**Q49.** India processes what approximate share of global real-time payment transactions (as of 2023-24)?
(A) About 10-15%
(B) About 25-30%
(C) About 45-50%
(D) More than one of the above
(E) None of the above

---

**Q50.** NACH (National Automated Clearing House) is primarily used for:
(A) Real-time single high-value transfers
(B) Bulk/recurring payments like salary, EMI, dividends, pensions
(C) International wire transfers
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
| 1 | (B) | Divide, Conquer, Combine — the three canonical D&C steps |
| 2 | (B) | Merge Sort = O(n log n) in ALL cases — best, avg, and worst |
| 3 | (D) | Worst case when pivot is always min or max: sorted array, reverse-sorted, all-equal |
| 4 | (C) | Merge Sort is stable; Quick Sort and Heap Sort are NOT |
| 5 | (C) | Merge Sort requires O(n) auxiliary array for merging sub-arrays |
| 6 | (B) | Combine (merge) step is where Merge Sort does its heavy work — O(n) per level |
| 7 | (A) | Partition (Divide) step does heavy work in Quick Sort — O(n) per level |
| 8 | (C) | Quick Sort best = O(n log n) — pivot always splits evenly |
| 9 | (B) | After partitioning [10,80,30,90,40,50,70] with pivot=70, it goes to index 4 |
| 10 | (B) | Merge Sort = O(n log n) in ALL three cases — the defining characteristic |
| 11 | (B) | Cache performance (sequential access) + no auxiliary array allocation |
| 12 | (B) | T(n) = 2T(n/2) + O(n) is Merge Sort's recurrence; same for Quick Sort avg case |
| 13 | (B) | Heap Sort: Not stable + O(n log n) all cases + O(1) in-place |
| 14 | (D) | Both Radix Sort O(nk) and Counting Sort O(n+k) can achieve near-linear time |
| 15 | (C) | Lower bound Ω(n log n) — proven via decision tree argument |
| 16 | (B) | Using <= ensures left subarray elements come first for equal values → stability |
| 17 | (B) | In-place means sorting within original array without auxiliary O(n) memory |
| 18 | (D) | Both A (O(1) extra space for linked list merge) and B (no random access) correct |
| 19 | (C) | Both Merge Sort and Quick Sort use Divide and Conquer paradigm |
| 20 | (C) | Merge Sort = only standard algorithm that is BOTH stable AND guaranteed O(n log n) |
| 21 | (B) | Worst case: degenerate partition → skewed tree with O(n) levels (like linked list) |
| 22 | (B) | Radix Sort is non-comparison based — sorts by digit/character position |
| 23 | (B) | Quick Sort avg recursion depth = O(log n) for balanced partitions |
| 24 | (B) | Quick Sort has NO combine step — partitions are in-place, nothing to merge |
| 25 | (C) | Merge Sort: stable (required) + O(n log n) always (safe for large data) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | UPI = Unified Payments Interface |
| 27 | (C) | NPCI developed and operates UPI; RBI regulates but doesn't operate |
| 28 | (B) | NPCI incorporated December 2008 |
| 29 | (B) | UPI launched 11 April 2016 (soft launch by RBI Governor Raghuram Rajan) |
| 30 | (B) | VPA = unique alias like user@bank, hiding actual account details |
| 31 | (C) | BHIM launched 30 December 2016 by PM Modi |
| 32 | (A) | BHIM = Bharat Interface for Money; named after Dr. B.R. Ambedkar |
| 33 | (B) | RTGS = Real Time Gross Settlement; minimum ₹2 lakh; for high-value |
| 34 | (B) | RuPay = India's domestic card network by NPCI (Rupee + Payment) |
| 35 | (B) | RBI established 1 April 1935 under RBI Act 1934 |
| 36 | (C) | IMPS launched November 2010 by NPCI — India's first instant payment |
| 37 | (C) | Standard UPI limit = ₹1 lakh per transaction |
| 38 | (B) | 14 banks nationalised on 19 July 1969 under PM Indira Gandhi |
| 39 | (C) | RTGS minimum = ₹2 lakh; IMPS and UPI minimum = ₹1 |
| 40 | (C) | NPCI promoted jointly by RBI + IBA (Indian Banks' Association) |
| 41 | (B) | UPI 123PAY = for feature/basic phones; works without internet/smartphone |
| 42 | (C) | Bhutan was first country to adopt UPI-like interface (2021) |
| 43 | (B) | Repo Rate = rate at which RBI lends short-term to commercial banks |
| 44 | (B) | CRR = cash kept with RBI; earns zero interest; controls liquidity |
| 45 | (C) | India Post Payments Bank = Payments Bank; cannot lend money |
| 46 | (B) | Demonetisation announced 8 November 2016 by PM Modi |
| 47 | (B) | UPI Lite = offline small payments up to ₹500 per transaction |
| 48 | (D) | FASTag, RuPay, and BHIM app are ALL NPCI products |
| 49 | (C) | India processes ~46% of global real-time transactions (FY2024 data) |
| 50 | (B) | NACH = bulk/recurring payments (salary, EMI, pension, dividends) |

---
---

# 🔁 DAY 31 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Divide & Conquer + Sorting

### D&C Three Steps (Memorise the ORDER):
```
1. DIVIDE   → Break problem into smaller sub-problems (often halves)
2. CONQUER  → Solve each sub-problem recursively (base case = trivially small)
3. COMBINE  → Merge solutions of sub-problems into solution for original problem

MERGE SORT:  Easy Divide (split in half) → Heavy COMBINE (merge two sorted halves)
QUICK SORT:  Heavy DIVIDE (partition around pivot) → No Combine needed!
```

### The Ultimate Sorting Comparison Table:
```
Algorithm    | Best      | Avg      | Worst    | Space    | Stable | In-Place
-------------|-----------|----------|----------|----------|--------|----------
Bubble Sort  | O(n)*     | O(n²)    | O(n²)    | O(1)     | ✅ YES | ✅ YES
Selection    | O(n²)     | O(n²)    | O(n²)    | O(1)     | ❌ NO  | ✅ YES
Insertion    | O(n)      | O(n²)    | O(n²)    | O(1)     | ✅ YES | ✅ YES
Merge Sort   | O(n log n)| O(nlogn) | O(nlogn) | O(n)     | ✅ YES | ❌ NO
Quick Sort   | O(n log n)| O(nlogn) | O(n²)    | O(log n) | ❌ NO  | ✅ YES
Heap Sort    | O(n log n)| O(nlogn) | O(nlogn) | O(1)     | ❌ NO  | ✅ YES
Radix Sort   | O(nk)     | O(nk)    | O(nk)    | O(n+k)   | ✅ YES | ❌ NO

*Optimized Bubble Sort only
```

### PYQ Critical Facts — One Liners:
```
✅ Merge Sort = ONLY algorithm: stable + O(n log n) worst guaranteed
✅ Quick Sort worst = O(n²) on sorted array with last-element pivot
✅ Merge Sort NOT in-place: needs O(n) auxiliary space
✅ Quick Sort IN-PLACE: only O(log n) recursion stack
✅ Heap Sort: O(n log n) all cases + O(1) space BUT unstable
✅ Radix Sort: O(nk) — non-comparison based — can beat Ω(n log n) lower bound
✅ Lower bound for comparison sorting = Ω(n log n) — proven mathematically
✅ D&C recurrence for Merge Sort: T(n) = 2T(n/2) + O(n) → O(n log n)
✅ Quick Sort worst recurrence: T(n) = T(n-1) + O(n) → O(n²)
✅ Merge Sort preferred for LINKED LISTS (no random access needed)
✅ Quick Sort faster in practice (cache, no allocation) despite same Big-O
```

---

## ⚡ RAPID FIRE — Banking & UPI

### NPCI — The Creator of India's Digital Payments:
```
NPCI = National Payments Corporation of India
Founded: 2008 | Promoters: RBI + IBA | HQ: Mumbai
Products: UPI, IMPS, RuPay, FASTag, BHIM, NACH, AePS
```

### UPI Key Dates (Memorise):
```
2008: NPCI established
2010: IMPS launched (November) — India's first instant payment
2012: RuPay card network launched
2016: UPI launched (11 April); BHIM launched (30 December)
2016: Demonetisation (8 November) — massive digital payment boost
2021: Bhutan = first country to adopt UPI internationally
2023: UPI at Eiffel Tower (France) — UPI goes global!
```

### Payment Systems Comparison:
```
System | Speed     | Min Amount | Max Amount | Use Case
-------|-----------|------------|------------|------------------
NEFT   | Batch/hrly| No min     | No limit   | Regular transfers
RTGS   | Instant   | ₹2 lakh    | No limit   | HIGH VALUE only
IMPS   | Instant   | ₹1         | ₹5 lakh    | Retail transfers
UPI    | Instant   | ₹1         | ₹1 lakh*   | Everyday payments
```

### Critical Banking Terms:
```
Repo Rate:  RBI lends TO banks (higher = less money circulated)
CRR:        Cash kept WITH RBI (earns nothing)
SLR:        Held in cash/gold/govt securities (earns interest)
NPA:        Loan unpaid 90+ days (Non-Performing Asset)
NBFC:       Gives loans but CANNOT take demand deposits
Payments Bank: Takes deposits + payments BUT CANNOT GIVE LOANS
```

### India's UPI Global Position:
```
~46% of global real-time payment transactions (FY2024)
131+ billion transactions in FY2024
More than USA + China + UK + Germany combined!
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **D&C Steps**: DIVIDE (split in half) → CONQUER (recursive solve) → COMBINE (merge); Merge Sort does heavy work at COMBINE; Quick Sort at DIVIDE (partition)
2. **Merge Sort**: O(n log n) ALL cases; STABLE; NOT in-place (O(n) space); preferred for linked lists and when stability required
3. **Quick Sort**: O(n log n) avg, O(n²) worst (sorted array + last-element pivot); IN-PLACE O(log n) space; NOT stable; faster in practice
4. **UPI**: Launched April 2016 by NPCI; VPA = user@bank alias; standard limit ₹1 lakh; BHIM launched Dec 2016; India = ~46% global real-time payments
5. **Only Merge Sort** is BOTH stable AND O(n log n) guaranteed worst case — the single most important exam differentiator among sorting algorithms

---

## 📅 DAY 32 PREVIEW — What's Coming Next:
**CS**: Searching Algorithms — Linear Search (analysis), Binary Search (iterative + recursive), Interpolation Search, Comparison of search algorithms
**GS**: Indian Polity — Parliament of India: Lok Sabha, Rajya Sabha, Powers, Sessions, Bills & Legislative Process

---

*🚀 Day 31 of 170 complete — Merge Sort's consistency and Quick Sort's speed are now yours to deploy on exam day!*
