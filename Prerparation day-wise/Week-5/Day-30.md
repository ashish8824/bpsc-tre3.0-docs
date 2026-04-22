# 📅 BPSC TRE 4.0 — DAY 30 COMPLETE STUDY MODULE
### Sorting Algorithms (Bubble, Selection, Insertion) + Current Affairs: G20 & G7
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Sorting Algorithms — Bubble, Selection, Insertion (Concepts + Dry Runs)
> - Afternoon (1 hr): Current Affairs — G20 & G7: Structure, Members, India's Role
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Sorting Algorithms — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is Sorting?

### Real-Life Analogy — The Classroom Attendance:

Imagine a teacher has **30 student answer sheets** with roll numbers all jumbled up:
`[15, 3, 28, 1, 9, 22, ...]`

To return sheets efficiently, the teacher needs them in ORDER:
`[1, 2, 3, 4, 5, 6, ...]`

The process of arranging these in a specific order is called **SORTING**.

### Another Analogy — Playing Cards:
When you pick up a hand of cards in a card game:
- You **look at each card** and **place it in the right position** among cards already in your hand
- This is exactly how **Insertion Sort** works!

### Formal Definition:
**Sorting** is the process of arranging data elements in a specific **order** (ascending or descending) so that searching, accessing, and processing becomes efficient.

### Why is Sorting Important?
```
1. FASTER SEARCHING   → Binary Search only works on SORTED data
2. DATA PROCESSING    → Reports, rankings, leaderboards need sorted data
3. DUPLICATE REMOVAL  → Easier to find duplicates in sorted arrays
4. DATABASE QUERIES   → ORDER BY in SQL sorts records
5. MERGE OPERATIONS   → Merging two sorted arrays is O(n), unsorted = O(n²)
6. FOUNDATION         → Many algorithms REQUIRE sorted input to work correctly
```

### Key Sorting Terminology:
```
IN-PLACE:     Sorting done within the ORIGINAL array — no extra array needed
              Space = O(1) extra (only a few variables like temp, i, j)

STABLE:       If two elements have EQUAL values, their ORIGINAL ORDER is preserved
              Example: If arr = [3a, 1, 3b, 2] (3a and 3b both equal 3)
              Stable sort result:   [1, 2, 3a, 3b]  ← 3a still before 3b
              Unstable sort result: [1, 2, 3b, 3a]  ← ORDER COULD CHANGE

COMPARISON-BASED: Sorting by comparing pairs of elements
              (All three algorithms today are comparison-based)

PASSES:       One complete scan through the array = one pass
```

### 🚨 PYQ TRAP #1: Stable vs Unstable
> Stability matters when sorting **records with multiple fields**.
> Example: Sorting students first by marks, then by name — stability ensures the name-sorted order is preserved when re-sorting by marks.
> For primitive data (just numbers), stability doesn't matter practically, but it's an exam concept!

---

## 🔷 SECTION 2: BUBBLE SORT

### Concept — The Bubbling Analogy:

Imagine **bubbles in water** — heavy bubbles (larger numbers) **sink to the bottom** while **light bubbles float to the top**. In each pass, the LARGEST unsorted element "bubbles up" to its correct position at the end.

```
Real-Life Analogy: Sorting People by Height in a Line
  People: [Short, Tall, Medium, Very Tall, Average]
  
  Round 1: Compare adjacent pairs, swap if left > right
            TALLEST person ends up at the rightmost position!
  Round 2: SECOND TALLEST moves to second-from-right position
  ...and so on until everyone is in order.
```

### Algorithm:
```
Bubble Sort (array arr, size n):
  for i = 0 to n-2:                    // n-1 passes
      for j = 0 to n-2-i:              // shrinks because last i elements are sorted
          if arr[j] > arr[j+1]:
              SWAP(arr[j], arr[j+1])   // bring larger element forward
```

### Step-by-Step Dry Run — Array: [64, 34, 25, 12, 22]

```
INITIAL ARRAY: [64, 34, 25, 12, 22]
n = 5, so we need at most 4 passes.
In each pass, largest unsorted element moves to the RIGHT end.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 1 (i=0): Compare all adjacent pairs
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Start:       [64, 34, 25, 12, 22]

Step j=0:    Compare 64 and 34 → 64 > 34 → SWAP
             [34, 64, 25, 12, 22]
              ^^  ^^

Step j=1:    Compare 64 and 25 → 64 > 25 → SWAP
             [34, 25, 64, 12, 22]
                  ^^  ^^

Step j=2:    Compare 64 and 12 → 64 > 12 → SWAP
             [34, 25, 12, 64, 22]
                      ^^  ^^

Step j=3:    Compare 64 and 22 → 64 > 22 → SWAP
             [34, 25, 12, 22, 64]
                          ^^  ^^

After Pass 1: [34, 25, 12, 22, 64]
                                ^^
                          64 is now in CORRECT POSITION (last)!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 2 (i=1): Only compare first 4 elements
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Start:       [34, 25, 12, 22, 64]

Step j=0:    Compare 34 and 25 → 34 > 25 → SWAP
             [25, 34, 12, 22, 64]

Step j=1:    Compare 34 and 12 → 34 > 12 → SWAP
             [25, 12, 34, 22, 64]

Step j=2:    Compare 34 and 22 → 34 > 22 → SWAP
             [25, 12, 22, 34, 64]

After Pass 2: [25, 12, 22, 34, 64]
                              ^^  ^^
                    34 and 64 are now CORRECTLY PLACED!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 3 (i=2): Only compare first 3 elements
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Start:       [25, 12, 22, 34, 64]

Step j=0:    Compare 25 and 12 → 25 > 12 → SWAP
             [12, 25, 22, 34, 64]

Step j=1:    Compare 25 and 22 → 25 > 22 → SWAP
             [12, 22, 25, 34, 64]

After Pass 3: [12, 22, 25, 34, 64]
                  ^^  ^^  ^^  ^^
               22, 25, 34, 64 — last 3 correctly placed!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 4 (i=3): Only compare first 2 elements
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Start:       [12, 22, 25, 34, 64]

Step j=0:    Compare 12 and 22 → 12 < 22 → NO SWAP

After Pass 4: [12, 22, 25, 34, 64]  ← FULLY SORTED! ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS SUMMARY TABLE:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pass | Array After Pass          | Sorted Portion
-----|---------------------------|---------------
  0  | [64, 34, 25, 12, 22]      | (none)
  1  | [34, 25, 12, 22, 64]      | [64]
  2  | [25, 12, 22, 34, 64]      | [34, 64]
  3  | [12, 22, 25, 34, 64]      | [22, 25, 34, 64]
  4  | [12, 22, 25, 34, 64]      | FULLY SORTED
```

### Optimized Bubble Sort (With Early Exit):
```
A KEY OPTIMIZATION: If no swap happens in an entire pass,
the array is ALREADY SORTED — we can STOP!

Optimized Algorithm:
  for i = 0 to n-2:
      swapped = false
      for j = 0 to n-2-i:
          if arr[j] > arr[j+1]:
              swap(arr[j], arr[j+1])
              swapped = true
      if swapped == false:
          BREAK  ← No swaps = already sorted!

EFFECT ON ALREADY SORTED ARRAY [1, 2, 3, 4, 5]:
  Pass 1: No swaps → swapped = false → BREAK!
  Only 1 pass needed → O(n) time!
  This is WHY Bubble Sort's BEST CASE = O(n)
```

### Complexity Analysis:
```
WORST CASE: Reverse-sorted array [5, 4, 3, 2, 1]
  Pass 1: 4 comparisons, 4 swaps
  Pass 2: 3 comparisons, 3 swaps
  Pass 3: 2 comparisons, 2 swaps
  Pass 4: 1 comparison, 1 swap
  Total = 4+3+2+1 = 10 = n(n-1)/2 ≈ n²/2 → O(n²)

BEST CASE: Already sorted [1, 2, 3, 4, 5] with OPTIMIZATION
  Only 1 pass (n-1 comparisons, 0 swaps) → O(n)
  WITHOUT optimization: still O(n²) passes even if no swaps happen

AVERAGE CASE: O(n²)
SPACE: O(1) — only temp variable for swap
STABLE: YES — equal elements are never swapped
```

### 🚨 PYQ TRAP #2: Bubble Sort Best Case
> Standard Bubble Sort (without optimization flag) = O(n²) even for sorted input.
> OPTIMIZED Bubble Sort (with swap flag) = O(n) for already-sorted input.
> **Exam answer: Best case O(n) refers to the OPTIMIZED version.**

---

## 🔷 SECTION 3: SELECTION SORT

### Concept — The "Find Minimum and Place" Strategy:

Imagine you're **organizing books on a shelf by page count**:
1. Scan all books → find the THINNEST book → place it at position 1
2. Scan remaining books → find next THINNEST → place it at position 2
3. Repeat until all placed

This is exactly **Selection Sort** — each pass SELECTS the minimum and places it correctly.

```
Key Idea: In pass i, find the MINIMUM element from arr[i..n-1]
          and SWAP it with arr[i].
          After k passes, first k elements are correctly sorted.
```

### Algorithm:
```
Selection Sort (array arr, size n):
  for i = 0 to n-2:
      minIdx = i                        // Assume current position has minimum
      for j = i+1 to n-1:              // Scan rest of array
          if arr[j] < arr[minIdx]:
              minIdx = j               // Update minimum index
      SWAP(arr[i], arr[minIdx])        // Place minimum at position i
```

### Step-by-Step Dry Run — Array: [64, 25, 12, 22, 11]

```
INITIAL ARRAY: [64, 25, 12, 22, 11]
n = 5, so we need 4 passes.
Each pass places the MINIMUM of the unsorted part at the front.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 1 (i=0): Find minimum in [64, 25, 12, 22, 11]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
minIdx = 0 (arr[0] = 64)

Scan j=1: arr[1]=25 < arr[0]=64 → minIdx = 1
Scan j=2: arr[2]=12 < arr[1]=25 → minIdx = 2
Scan j=3: arr[3]=22 > arr[2]=12 → minIdx stays 2
Scan j=4: arr[4]=11 < arr[2]=12 → minIdx = 4

Minimum = arr[4] = 11 → SWAP arr[0] and arr[4]
Before swap: [64, 25, 12, 22, 11]
After  swap: [11, 25, 12, 22, 64]
              ^^                ^^
After Pass 1: [11, 25, 12, 22, 64]
               ^^
               11 is in CORRECT POSITION!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 2 (i=1): Find minimum in [25, 12, 22, 64]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
minIdx = 1 (arr[1] = 25)

Scan j=2: arr[2]=12 < arr[1]=25 → minIdx = 2
Scan j=3: arr[3]=22 > arr[2]=12 → minIdx stays 2
Scan j=4: arr[4]=64 > arr[2]=12 → minIdx stays 2

Minimum = arr[2] = 12 → SWAP arr[1] and arr[2]
Before swap: [11, 25, 12, 22, 64]
After  swap: [11, 12, 25, 22, 64]
                  ^^  ^^
After Pass 2: [11, 12, 25, 22, 64]
               ^^  ^^
               11, 12 are CORRECTLY PLACED!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 3 (i=2): Find minimum in [25, 22, 64]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
minIdx = 2 (arr[2] = 25)

Scan j=3: arr[3]=22 < arr[2]=25 → minIdx = 3
Scan j=4: arr[4]=64 > arr[3]=22 → minIdx stays 3

Minimum = arr[3] = 22 → SWAP arr[2] and arr[3]
Before swap: [11, 12, 25, 22, 64]
After  swap: [11, 12, 22, 25, 64]
                      ^^  ^^
After Pass 3: [11, 12, 22, 25, 64]
               ^^  ^^  ^^
               11, 12, 22 CORRECTLY PLACED!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 4 (i=3): Find minimum in [25, 64]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
minIdx = 3 (arr[3] = 25)

Scan j=4: arr[4]=64 > arr[3]=25 → minIdx stays 3

Minimum = arr[3] = 25 → SWAP arr[3] with itself (no change)

After Pass 4: [11, 12, 22, 25, 64]  ← FULLY SORTED! ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS SUMMARY TABLE:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pass | Min Found | Swapped With | Array After Pass
-----|-----------|--------------|---------------------------
  1  |    11     |  arr[0]=64   | [11, 25, 12, 22, 64]
  2  |    12     |  arr[1]=25   | [11, 12, 25, 22, 64]
  3  |    22     |  arr[2]=25   | [11, 12, 22, 25, 64]
  4  |    25     |  arr[3]=25   | [11, 12, 22, 25, 64]
```

### Complexity Analysis:
```
ALL CASES: O(n²) — ALWAYS!
  Why? The inner loop ALWAYS scans the full unsorted portion.
  Even if the array is already sorted, Selection Sort still scans everything
  because it doesn't know it's sorted — it just looks for the minimum!

  Pass 1: n-1 comparisons
  Pass 2: n-2 comparisons
  ...
  Pass n-1: 1 comparison
  Total = (n-1) + (n-2) + ... + 1 = n(n-1)/2 → O(n²)

SWAPS: At most n-1 swaps (one per pass) — MINIMUM number of swaps!
       This is Selection Sort's KEY ADVANTAGE for write-heavy operations

SPACE: O(1) — in-place

STABLE? NO (in standard implementation)
  WHY? When you swap the minimum to position i, you may displace an equal element.
  Example: [3a, 3b, 1] → find min=1 at pos 2 → swap with pos 0
           Result: [1, 3b, 3a] ← 3b comes before 3a (ORDER CHANGED!)
```

### 🚨 PYQ TRAP #3: Selection Sort — Always O(n²)
> Selection Sort performs the SAME number of comparisons regardless of input.
> Even if the array is ALREADY SORTED, it still does O(n²) comparisons.
> This makes it LESS efficient than optimized Bubble Sort or Insertion Sort for nearly-sorted data.
> BUT it does at most n-1 swaps — good for situations where WRITES are expensive!

---

## 🔷 SECTION 4: INSERTION SORT

### Concept — The Card Player Analogy:

Imagine you're **picking up playing cards** one by one:
- You already hold: [2, 5, 8] (sorted in hand)
- You pick up new card: 4
- You SLIDE 8 right, SLIDE 5 right, INSERT 4 in correct position
- Hand becomes: [2, 4, 5, 8]

This is exactly **Insertion Sort** — maintain a sorted portion and INSERT each new element at the right place.

```
Key Idea: Divide array into SORTED (left) and UNSORTED (right) parts.
          Pick first element of unsorted part.
          INSERT it into the correct position in the sorted part.
          Sorted part grows by 1 each pass.
```

### Algorithm:
```
Insertion Sort (array arr, size n):
  for i = 1 to n-1:                   // Start from second element
      key = arr[i]                    // Element to be inserted
      j = i - 1                       // Compare with sorted portion
      while j >= 0 AND arr[j] > key:
          arr[j+1] = arr[j]           // Shift element right
          j = j - 1
      arr[j+1] = key                  // Insert key at correct position
```

### Step-by-Step Dry Run — Array: [12, 11, 13, 5, 6]

```
INITIAL ARRAY: [12, 11, 13, 5, 6]
Sorted part starts with just [12] (first element).
Each pass picks next element and inserts it into sorted part.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 1 (i=1): Insert arr[1]=11 into sorted part [12]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
key = 11
j = 0 (comparing with arr[0]=12)

arr[0]=12 > key=11 → SHIFT: arr[1] = arr[0] = 12
[12, 12, 13, 5, 6]   j = -1

j = -1 → EXIT while loop
Insert key: arr[j+1] = arr[0] = 11

After Pass 1: [11, 12, 13, 5, 6]
               ^^^^^
               [11, 12] is SORTED!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 2 (i=2): Insert arr[2]=13 into sorted part [11, 12]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
key = 13
j = 1 (comparing with arr[1]=12)

arr[1]=12 < key=13 → NO SHIFT, EXIT while loop immediately
Insert key: arr[j+1] = arr[2] = 13 (already in place!)

After Pass 2: [11, 12, 13, 5, 6]
               ^^^^^^^^^^^
               [11, 12, 13] SORTED (no change, key was already correct)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 3 (i=3): Insert arr[3]=5 into sorted part [11, 12, 13]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
key = 5
j = 2 (comparing with arr[2]=13)

arr[2]=13 > key=5 → SHIFT: arr[3] = arr[2] = 13
[11, 12, 13, 13, 6]   j = 1

arr[1]=12 > key=5 → SHIFT: arr[2] = arr[1] = 12
[11, 12, 12, 13, 6]   j = 0

arr[0]=11 > key=5 → SHIFT: arr[1] = arr[0] = 11
[11, 11, 12, 13, 6]   j = -1

j = -1 → EXIT while loop
Insert key: arr[j+1] = arr[0] = 5

After Pass 3: [5, 11, 12, 13, 6]
               ^^^^^^^^^^^^^^^
               [5, 11, 12, 13] SORTED!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS 4 (i=4): Insert arr[4]=6 into sorted part [5, 11, 12, 13]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
key = 6
j = 3 (comparing with arr[3]=13)

arr[3]=13 > key=6 → SHIFT: arr[4] = arr[3] = 13
[5, 11, 12, 13, 13]   j = 2

arr[2]=12 > key=6 → SHIFT: arr[3] = arr[2] = 12
[5, 11, 12, 12, 13]   j = 1

arr[1]=11 > key=6 → SHIFT: arr[2] = arr[1] = 11
[5, 11, 11, 12, 13]   j = 0

arr[0]=5 < key=6 → NO SHIFT, EXIT while loop
Insert key: arr[j+1] = arr[1] = 6

After Pass 4: [5, 6, 11, 12, 13]  ← FULLY SORTED! ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS SUMMARY TABLE:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pass | Key  | Sorted Part After Insertion
-----|------|-----------------------------
  0  |  —   | [12]                        (initial)
  1  |  11  | [11, 12]
  2  |  13  | [11, 12, 13]
  3  |   5  | [5, 11, 12, 13]
  4  |   6  | [5, 6, 11, 12, 13]  ✅
```

### Complexity Analysis:
```
BEST CASE: Already sorted array [1, 2, 3, 4, 5]
  For each element, inner while loop IMMEDIATELY exits (arr[j] ≤ key)
  Only 1 comparison per pass → n-1 comparisons total → O(n)
  This is Insertion Sort's MAJOR ADVANTAGE!

WORST CASE: Reverse-sorted array [5, 4, 3, 2, 1]
  For element at position i, must shift ALL i previous elements
  Total shifts = 1 + 2 + ... + (n-1) = n(n-1)/2 → O(n²)

AVERAGE CASE: O(n²)

SPACE: O(1) — in-place (only 'key' and 'j' variables)

STABLE: YES — equal elements are never swapped past each other
  (the while condition is arr[j] > key, NOT >=, so equal elements stay in order)

COMPARISON WITH BUBBLE:
  Both O(n) best, O(n²) worst
  Insertion Sort is FASTER in practice for nearly-sorted data
  Insertion Sort has fewer comparisons on average
```

### 🚨 PYQ TRAP #4: Insertion Sort Best Case
> Insertion Sort has the SAME best case as optimized Bubble Sort → O(n)
> BUT Insertion Sort is generally FASTER in practice because it does fewer comparisons and is cache-friendly (works on consecutive array elements)
> **For nearly-sorted data, Insertion Sort is the PREFERRED choice among O(n²) algorithms!**

---

## 🔷 SECTION 5: Comparison of All Three Algorithms

### Master Comparison Table:

| Property | Bubble Sort | Selection Sort | Insertion Sort |
|----------|-------------|----------------|----------------|
| **Best Case** | O(n)* | O(n²) | O(n) |
| **Average Case** | O(n²) | O(n²) | O(n²) |
| **Worst Case** | O(n²) | O(n²) | O(n²) |
| **Space** | O(1) | O(1) | O(1) |
| **Stable?** | ✅ YES | ❌ NO | ✅ YES |
| **In-Place?** | ✅ YES | ✅ YES | ✅ YES |
| **Swaps (worst)** | O(n²) | O(n) | O(n²) |
| **Comparisons** | O(n²) | O(n²) | O(n²) |
| **Best for** | Nearly sorted data | Min writes | Nearly sorted / Online sorting |
| **Adaptive?** | ✅ YES (optimized) | ❌ NO | ✅ YES |

*Optimized version with swap flag

### Deep Comparison — Visual Summary:

```
STABILITY EXPLAINED:
  Array: [(3,A), (1,B), (3,C), (2,D)]  ← tuples: (value, original label)
  Want to sort by VALUE only.

  STABLE SORT result:   [(1,B), (2,D), (3,A), (3,C)]  ← A still before C
  UNSTABLE SORT result: [(1,B), (2,D), (3,C), (3,A)]  ← ORDER CHANGED!

  Bubble Sort:    STABLE ✅  (only swaps adjacent — equal elements never crossed)
  Insertion Sort: STABLE ✅  (only shifts past GREATER elements, stops at equal)
  Selection Sort: UNSTABLE ❌ (long-distance swaps can displace equal elements)

ADAPTIVITY EXPLAINED (can take advantage of existing order):
  Bubble Sort (optimized): If sorted → exits early → O(n)
  Insertion Sort:          If sorted → inner while exits immediately → O(n)
  Selection Sort:          ALWAYS scans full remaining array → NEVER benefits
```

### When to Use Which:

```
USE BUBBLE SORT when:
  → Data is ALMOST sorted (few elements out of place)
  → Simplicity of code is priority
  → Educational purposes / understanding concepts

USE SELECTION SORT when:
  → MINIMIZING WRITE operations is critical (flash memory, disk I/O)
  → Only n-1 swaps GUARANTEED regardless of input
  → Memory WRITE is expensive but READ is cheap

USE INSERTION SORT when:
  → Data arrives ONE ELEMENT AT A TIME (online sorting)
  → Array is NEARLY SORTED
  → Small arrays (n < 50) — fast in practice due to simplicity
  → Building a sorted array incrementally (e.g., playing cards scenario)
```

### Flowchart — How Sorting Algorithms Work:

```
START: Unsorted Array arr[0..n-1]
           |
    ┌──────┴──────┐
    |  Choose     |
    | Algorithm   |
    └──────┬──────┘
           |
   ┌───────┼───────┐
   |       |       |
BUBBLE  SELECT  INSERT
SORT    SORT    SORT
   |       |       |
   v       v       v
Compare  Find    Pick
adjacent MIN in  next key
pairs   unsorted from
& swap  portion  unsorted
if out  & swap   & INSERT
of order to front in sorted
   |       |    part by
   |       |    shifting
   |       |       |
   └───────┴───────┘
           |
   After n-1 passes:
           |
    SORTED ARRAY ✅
```

### Complexity Growth — Visual:

```
For n=10:   O(n) = 10,  O(n²) = 100
For n=100:  O(n) = 100, O(n²) = 10,000
For n=1000: O(n) = 1000, O(n²) = 1,000,000

The GAP WIDENS as n grows — that's why efficient algorithms matter!

         Worst-case operations
         |
100,000  |                        **    n² (Bubble/Select/Insert worst)
         |                   **
 10,000  |              **
         |         **
  1,000  |    **
         | **                     +++   n (Insertion/Bubble best)
   100   |++++++++++++++++++++++++
         +-------------------------> n
         0   100   200   300
```

### 🚨 PYQ TRAP #5: All Three are O(n²) Average — But Different in Practice
```
EXAM QUESTION: "Which sorting algorithm is most efficient for nearly-sorted data?"
WRONG ANSWER:  "All are O(n²) so all are equal"
CORRECT ANSWER: "Insertion Sort — it exits inner loop early when element is in place → O(n) best case"

EXAM QUESTION: "Which sorting algorithm does minimum swaps?"
ANSWER: Selection Sort — at most O(n) swaps (one per pass)

EXAM QUESTION: "Which O(n²) sorting algorithms are stable?"
ANSWER: Bubble Sort and Insertion Sort (NOT Selection Sort)
```

---

## 🔷 SECTION 6: Important Concepts — Stable vs In-Place

### In-Place Sorting:
```
IN-PLACE: Uses O(1) EXTRA space (only constant variables)
  All three (Bubble, Selection, Insertion) = IN-PLACE ✅

NOT IN-PLACE: Uses O(n) extra space
  Merge Sort = NOT in-place (needs auxiliary array)
  
EXAM COMPARISON:
Algorithm     | In-Place | Extra Space
--------------|----------|------------
Bubble Sort   |    ✅    |    O(1)
Selection Sort|    ✅    |    O(1)
Insertion Sort|    ✅    |    O(1)
Merge Sort    |    ❌    |    O(n)
Quick Sort    |    ✅    |    O(log n) recursion stack
```

### Stable Sorting — Detailed:
```
STABLE algorithms maintain RELATIVE ORDER of EQUAL ELEMENTS:
  ✅ Bubble Sort    → Adjacent comparison: equal elements NEVER swapped
  ✅ Insertion Sort → Stops before equal elements: uses arr[j] > key (strict >)
  ❌ Selection Sort → Swaps minimum to front — may disturb equal elements
  ✅ Merge Sort     → Stable (takes from left subarray first when equal)
  ❌ Quick Sort     → Generally unstable (depends on partition scheme)
  ❌ Heap Sort      → Unstable

TRICK: "Bubble and Insertion keep order; Selection and Quick/Heap may disturb it"
```

### 🚨 PYQ TRAP #6: Why Insertion Sort is Stable
> Insertion Sort is stable because the condition is `arr[j] > key` (strictly greater than).
> When `arr[j] == key`, the while loop STOPS, and key is inserted AFTER all equal elements.
> If the condition were `>=` instead of `>`, it would become UNSTABLE.
> This subtle detail is sometimes tested in advanced questions!

---

# PART 2: GENERAL STUDIES
## 🌍 Current Affairs — G20 & G7: Global Governance Forums

---

## 🔷 SECTION 1: What is G7?

### Definition & Background:
```
G7 = Group of Seven
Type: Informal forum of 7 major advanced economies
Founded: 1975 (as G6; became G7 in 1976 when Canada joined)
No permanent secretariat (rotating presidency)

ORIGINAL PURPOSE: Coordinate economic policy after 1973 oil crisis
                  Discuss global economic challenges among major economies
```

### G7 Member Countries (PERFECT MEMORY TRICK):
```
The 7 Members → "U Can France Get Italy Just Canada"

U = United States of America
C = Canada
F = France
G = Germany
I = Italy
J = Japan
UK = United Kingdom

+ European Union (EU) is a NON-ENUMERATED member (special status, not counted in "7")
```

### G7 Quick Facts:
```
Members:          7 countries + EU (special status)
GDP Share:        ~45% of global GDP
Population:       ~10% of world population
Headquarters:     No permanent HQ (rotates)
Current format:   Annual Summit + ministerial meetings
Presidency:       Rotates annually among members
Recent Summits:
  2023: Hiroshima, Japan (May 2023)
  2024: Fasano, Italy (June 2024) — G7 Italia Presidency
  2025: Kananaskis, Canada (June 2025) — Canadian Presidency
```

### What does G7 discuss?
```
1. Global economic coordination and monetary policy
2. Climate change and clean energy transition
3. Global security threats (terrorism, cybersecurity)
4. Health crises and pandemic preparedness
5. Democratic values and rule of law
6. Support for Ukraine (recently prominent)
7. Artificial intelligence governance
8. Supply chain resilience (post-COVID, semiconductor focus)
```

### 🎯 PYQ FACT: Russia was SUSPENDED from G8 in 2014!
```
The group was G8 (including Russia) from 1998 to 2014.
After Russia annexed Crimea in 2014, it was suspended.
G8 → became G7 again.
Russia has NOT been reinstated despite calls in some quarters.
```

---

## 🔷 SECTION 2: What is G20?

### Definition & Background:
```
G20 = Group of Twenty
Type: International forum of major economies (developed + developing)
Founded: 1999 (finance ministers/central bank governors level)
         Upgraded to Leaders Summit level in 2008 (after global financial crisis)
Permanent Secretariat: None (Troika system — Past, Present, Future presidencies)
```

### G20 Member Countries (19 + EU):
```
MEMORY TRICK: ABCCC FGIJK MRRSS TUSA

A = Argentina
B = Brazil  
C = Canada
C = China
C = Croatia (NOT a member — skip this one!)

Better trick by regions:

AMERICAS (4):    Argentina, Brazil, Canada, USA, Mexico (5 actually)
EUROPE (4+EU):   France, Germany, Italy, UK + European Union
ASIA-PACIFIC (6): Australia, China, India, Indonesia, Japan, South Korea
MIDDLE EAST/AFRICA (2): Saudi Arabia, South Africa, Turkey/Türkiye
RUSSIA:          Russia (still a member, unlike G7)

COMPLETE LIST (19 countries + EU = 20):
1. Argentina        11. Mexico
2. Australia        12. Russia
3. Brazil           13. Saudi Arabia
4. Canada           14. South Africa
5. China            15. South Korea
6. France           16. Türkiye (Turkey)
7. Germany          17. United Kingdom
8. India            18. United States
9. Indonesia        19. European Union (represents all EU nations)
10. Italy           + African Union (AU) added as permanent member in 2023!
11. Japan
```

### 🎯 PYQ SPECIAL: African Union Joins G20!
```
At the G20 New Delhi Summit (2023), the AFRICAN UNION (AU) was admitted as a
PERMANENT member of G20, making the effective count G21 in some frameworks.
This was a major diplomatic achievement pushed by India during its presidency.
AU represents 55 African nations.
This was the BIGGEST structural change to G20 since the EU's inclusion.
```

### G20 Quick Facts:
```
Members:          19 countries + EU (+ AU as permanent from 2023)
GDP Share:        ~85% of global GDP
Trade Share:      ~75% of global trade
Population:       ~67% of world population
Annual Meeting:   Leaders Summit (Heads of State/Government)
Working Groups:   Finance Track + Sherpa Track
Host Rotation:    Annual rotating presidency
```

### G20 Structure — How It Works:
```
PRESIDENCY: One member country holds presidency for 1 year
            Hosts all G20 meetings, sets the agenda

TROIKA: Three consecutive presidencies work together for continuity
  Past Presidency → Current Presidency → Incoming Presidency
  India 2023 → Brazil 2024 → South Africa 2025 (Troika)

TRACKS:
  Finance Track: Finance Ministers + Central Bank Governors
  Sherpa Track:  Personal envoys of leaders (coordinate policy)

WORKING GROUPS: Digital Economy, Agriculture, Climate, Health,
                Education, Infrastructure, Trade, Energy, etc.
```

---

## 🔷 SECTION 3: INDIA and G20 — 2023 Summit

### India's G20 Presidency (December 2022 — November 2023):
```
Theme:        "Vasudhaiva Kutumbakam" — "One Earth · One Family · One Future"
              (Taken from Maha Upanishad — ancient Sanskrit text)
Logo:         Lotus flower + globe (Earth as a lotus petal)
Mascot:       None officially (lotus symbolic)

Presidency Period: 1 December 2022 to 30 November 2023
Summit:       New Delhi, Bharat Mandapam, 9-10 September 2023

🌟 KEY OUTCOMES OF INDIA'S G20 PRESIDENCY:
  ✅ African Union admitted as PERMANENT G20 member (HISTORIC!)
  ✅ New Delhi Declaration adopted by CONSENSUS (all 20 members agreed)
  ✅ Global Biofuels Alliance (GBA) launched — India's initiative
  ✅ One Future Alliance for DPI (Digital Public Infrastructure) — UPI, Aadhaar model
  ✅ Corruption issues, debt restructuring for developing nations discussed
  ✅ Vasudhaiva Kutumbakam ethos — developing nation concerns prominently featured
  ✅ 200+ G20 meetings across 60+ Indian cities!
  ✅ Jan Bhagidari (people's participation) — G20 taken to grassroots level

PM Modi chaired the Leaders' Summit.
Called India's "moment" in multilateral diplomacy.
```

### 🎯 PYQ FACT: New Delhi Declaration
```
The New Delhi Declaration 2023 was significant because:
→ It was adopted by CONSENSUS (all 20 members + AU agreed)
→ Previous summit (Bali 2022) had difficulty due to Russia-Ukraine war language
→ India's diplomatic success: found language acceptable to ALL parties
→ Referred to Russia-Ukraine as "war in Ukraine" rather than "Russian aggression"
```

### G20 Presidency Timeline (Recent):
```
Year | Country    | Theme/Notes
2019 | Japan       | "Human-centred Future Society" (Osaka Summit)
2020 | Saudi Arabia| "Realizing Opportunities of 21st Century" (Virtual, COVID)
2021 | Italy       | "People, Planet, Prosperity" (Rome)
2022 | Indonesia   | "Recover Together, Recover Stronger" (Bali)
2023 | INDIA ★    | "Vasudhaiva Kutumbakam" (New Delhi) — AU joins!
2024 | Brazil      | "Building a Just World and a Sustainable Planet" (Rio)
2025 | South Africa| "Solidarity, Equality, Sustainability"
2026 | USA         | (upcoming)
```

---

## 🔷 SECTION 4: G7 vs G20 — Key Differences

### Comparison Table:

| Feature | G7 | G20 |
|---------|-----|-----|
| **Full Name** | Group of Seven | Group of Twenty |
| **Members** | 7 countries + EU | 19 countries + EU + AU (2023) |
| **Founded** | 1975 | 1999 (leaders level: 2008) |
| **GDP Representation** | ~45% of global GDP | ~85% of global GDP |
| **Population** | ~10% of world | ~67% of world |
| **Nature** | Exclusive club of rich nations | Broader; includes emerging economies |
| **Developing Nations?** | NO | YES (India, China, Brazil, etc.) |
| **Secretariat** | None (rotating) | None (rotating Troika) |
| **Russia?** | Suspended (2014) | STILL a member |
| **China?** | NOT a member | YES, member since founding |
| **India?** | NOT a member | YES, founding member |
| **Binding Decisions?** | NO (non-binding forum) | NO (non-binding forum) |
| **Focus** | Advanced economy policy | Global economic governance |

### 🎯 PYQ TRAP: Key Difference — China and India
```
China = G20 member, NOT G7 member
India = G20 member, NOT G7 member (invited as guest sometimes)
Russia = G20 member, SUSPENDED from G7 (was G8 until 2014)
USA = Member of BOTH G7 and G20
France, Germany, Italy, UK, Japan, Canada = Members of BOTH
```

---

## 🔷 SECTION 5: Other Important Global Forums (Bonus)

```
G77:      Group of 77 developing nations (actually 134 now, name unchanged)
          Founded: 1964; Largest intergovernmental organization of developing nations
          India is a member

BRICS:    Brazil, Russia, India, China, South Africa
          Expanded in 2024: Saudi Arabia, UAE, Egypt, Ethiopia, Iran joined
          Now: BRICS+ (10 members from 2024)

SCO:      Shanghai Cooperation Organisation
          India full member since 2017
          Focuses on security, economic, political cooperation in Eurasia

Commonwealth: 56 member nations; mostly former British territories
              India is a founding member (since 1947)
              HQ: Marlborough House, London

ASEAN:    10 Southeast Asian nations; India has "Dialogue Partner" status
```

---

## 🔷 SECTION 6: G20 & G7 — Quick Recall Facts for MCQs

```
✅ G20 represents ~85% of world GDP and ~75% of world trade
✅ G7 founded in 1975 (as G6); Canada joined in 1976 → G7
✅ G8 existed 1998-2014 (Russia included); Russia suspended after Crimea annexation
✅ G20 elevated to Heads of State level in 2008 (after global financial crisis)
✅ India hosted G20 in 2023; Theme = "Vasudhaiva Kutumbakam"
✅ African Union became PERMANENT G20 member at New Delhi Summit 2023
✅ New Delhi Declaration 2023 adopted by consensus
✅ Global Biofuels Alliance launched during India's G20 presidency
✅ Troika = Past + Present + Future presidencies of G20
✅ G20 has NO binding power — all decisions are voluntary/diplomatic
✅ G7 also has NO binding power — coordination forum only
✅ Next G20 after India: Brazil 2024, South Africa 2025, USA 2026
✅ G20 Sherpa = personal envoy who does preparatory work before Leaders' Summit
```

### Memory Trick — G7 Members:
```
"US Can Fight Germany, Italy, Japan, UK"
U = United States
C = Canada  
F = France
G = Germany
I = Italy
J = Japan
UK = United Kingdom
```

### Memory Trick — G20 has what G7 doesn't:
```
"The BRICS are in G20 but NOT G7"
B = Brazil ✓ G20 only
R = Russia ✓ G20, SUSPENDED from G7
I = India ✓ G20 only
C = China ✓ G20 only
S = South Africa ✓ G20 only
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Bubble Sort, Selection Sort, Insertion Sort

---

**Q1.** What is the WORST CASE time complexity of Bubble Sort?
(A) O(n log n)
(B) O(n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q2.** Which sorting algorithm is considered STABLE among the following?
(A) Selection Sort
(B) Quick Sort
(C) Insertion Sort
(D) More than one of the above (Bubble Sort and Insertion Sort are both stable)
(E) None of the above

---

**Q3.** The BEST CASE time complexity of Insertion Sort (for an already sorted array) is:
(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q4.** In Selection Sort, what is selected in each pass?
(A) The maximum element, placed at the end
(B) The minimum element from the unsorted part, placed at the correct position
(C) Two adjacent elements are compared and swapped
(D) More than one of the above
(E) None of the above

---

**Q5.** After the FIRST PASS of Bubble Sort on array [5, 3, 8, 1, 2], which element will be in its CORRECT (final) position?
(A) 5 (smallest)
(B) 1 (smallest)
(C) 8 (largest)
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the BEST CASE time complexity of Selection Sort?
(A) O(n)
(B) O(n log n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following sorting algorithms performs the MINIMUM number of swaps?
(A) Bubble Sort
(B) Insertion Sort
(C) Selection Sort
(D) More than one of the above
(E) None of the above

---

**Q8.** Insertion Sort works BEST on which type of input?
(A) Randomly shuffled array
(B) Reverse-sorted array
(C) Nearly sorted or already sorted array
(D) More than one of the above
(E) None of the above

---

**Q9.** For array [64, 34, 25, 12, 22], how many PASSES does Bubble Sort need to sort it completely (at most)?
(A) 5
(B) 3
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is TRUE about all three algorithms — Bubble Sort, Selection Sort, and Insertion Sort?
(A) All are stable
(B) All use O(1) extra space (in-place)
(C) All have O(n) best case
(D) More than one of the above
(E) None of the above

---

**Q11.** In Insertion Sort, the inner while loop condition is `arr[j] > key`. Why is it strictly GREATER THAN (not >=)?
(A) To improve time complexity
(B) To maintain STABILITY — equal elements are not shifted, preserving original order
(C) To reduce number of comparisons
(D) More than one of the above
(E) None of the above

---

**Q12.** After 3 passes of SELECTION SORT on [64, 25, 12, 22, 11], the array will be:
(A) [11, 12, 22, 25, 64]
(B) [11, 12, 25, 22, 64]
(C) [11, 12, 22, 25, 64]
(D) More than one of the above
(E) None of the above

---

**Q13.** What is the TOTAL number of comparisons in the WORST CASE for Bubble Sort on n elements?
(A) n × (n-1)
(B) n(n-1)/2
(C) n²
(D) More than one of the above
(E) None of the above

---

**Q14.** Selection Sort is preferred when:
(A) Data is nearly sorted
(B) Memory WRITE operations are expensive and minimizing swaps is crucial
(C) Data is already sorted
(D) More than one of the above
(E) None of the above

---

**Q15.** Which sorting algorithm can be optimized to terminate EARLY if the array becomes sorted mid-way?
(A) Selection Sort
(B) Insertion Sort and Bubble Sort (both are adaptive)
(C) Only Quick Sort
(D) More than one of the above
(E) None of the above

---

**Q16.** How many swaps does SELECTION SORT perform in the WORST CASE for n elements?
(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q17.** For the array [1, 2, 3, 4, 5] (already sorted), which algorithm will take the MOST time comparatively?
(A) Insertion Sort (optimized)
(B) Bubble Sort (optimized with swap flag)
(C) Selection Sort
(D) More than one of the above (Insertion and Bubble both O(n); Selection is O(n²))
(E) None of the above

---

**Q18.** In INSERTION SORT, what operation is performed to make space for the 'key' element?
(A) Elements are swapped in pairs repeatedly
(B) Elements GREATER than key are SHIFTED one position to the right
(C) The array is divided into two halves
(D) More than one of the above
(E) None of the above

---

**Q19.** Consider array [3, 1, 4, 1, 5]. After ONE pass of Bubble Sort, which is the array?
(A) [1, 3, 4, 1, 5]
(B) [1, 1, 3, 4, 5]
(C) [1, 3, 1, 4, 5]
(D) More than one of the above
(E) None of the above

---

**Q20.** Which sorting algorithm(s) among the three studied today work on the principle of "finding the correct position for each element by comparison with already-sorted elements"?
(A) Bubble Sort
(B) Selection Sort
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q21.** In the worst case (reverse-sorted array), which statement is CORRECT about the number of SWAPS?
(A) Bubble Sort and Insertion Sort both do O(n²) swaps; Selection Sort does O(n) swaps
(B) All three do O(n²) swaps in worst case
(C) Insertion Sort does O(n) swaps in all cases
(D) More than one of the above
(E) None of the above

---

**Q22.** Selection Sort is UNSTABLE because:
(A) It uses nested loops
(B) It performs O(n²) comparisons
(C) Long-distance swaps can change the relative order of equal elements
(D) More than one of the above
(E) None of the above

---

**Q23.** For ONLINE SORTING (elements arrive one by one and must be sorted after each arrival), which algorithm is most naturally suited?
(A) Bubble Sort
(B) Selection Sort
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q24.** What is the space complexity of Insertion Sort?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider the following TRICKY scenario: Array [5, 5, 5, 5] (all elements equal).
Which sorting algorithm(s) will perform ZERO swaps?
(A) Only Selection Sort (no minimum to swap)
(B) Only Insertion Sort
(C) All three — Bubble, Selection, and Insertion (no swaps needed for equal elements)
(D) More than one of the above (both Bubble and Insertion do zero swaps; Selection does a "swap with itself")
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: G20 & G7 — Structure, Members, India's Role

---

**Q26.** The G7 was originally founded in which year and as which group?
(A) 1975, as G7 (with all 7 members from start)
(B) 1975, as G6 (Canada joined in 1976)
(C) 1999, as G7
(D) More than one of the above
(E) None of the above

---

**Q27.** Which of the following countries is a member of G7 but NOT a member of G20?
(A) France
(B) Canada
(C) None — all G7 countries are also G20 members
(D) More than one of the above
(E) None of the above

---

**Q28.** Which organization/country was SUSPENDED from the G8 in 2014, reducing it back to G7?
(A) China
(B) Russia
(C) India
(D) More than one of the above
(E) None of the above

---

**Q29.** The G20 represents approximately what percentage of global GDP?
(A) 45%
(B) 60%
(C) 85%
(D) More than one of the above
(E) None of the above

---

**Q30.** What was the THEME of India's G20 Presidency (2023)?
(A) "One World, One Health"
(B) "Vasudhaiva Kutumbakam — One Earth, One Family, One Future"
(C) "People, Planet, Prosperity"
(D) More than one of the above
(E) None of the above

---

**Q31.** At which G20 Summit was the African Union (AU) admitted as a PERMANENT member?
(A) Bali Summit, Indonesia (2022)
(B) Rome Summit, Italy (2021)
(C) New Delhi Summit, India (2023)
(D) More than one of the above
(E) None of the above

---

**Q32.** The G20 was elevated to Heads of State/Government level (Leaders Summit) in which year?
(A) 1999
(B) 2008 (after global financial crisis)
(C) 2014
(D) More than one of the above
(E) None of the above

---

**Q33.** Which of the following is a member of G20 but NOT a member of G7?
(A) Japan
(B) United Kingdom
(C) China
(D) More than one of the above (China, India, Brazil, Russia, South Africa, etc.)
(E) None of the above

---

**Q34.** The term "TROIKA" in G20 refers to:
(A) The three largest economies — USA, China, EU
(B) The combination of Past, Present, and Future G20 Presidencies for continuity
(C) Three working groups — Finance, Trade, Development
(D) More than one of the above
(E) None of the above

---

**Q35.** Which major initiative was launched by India during its G20 Presidency specifically related to bioenergy?
(A) International Solar Alliance (ISA)
(B) Global Biofuels Alliance (GBA)
(C) Mission LiFE (Lifestyle for Environment)
(D) More than one of the above
(E) None of the above

---

**Q36.** The theme "Vasudhaiva Kutumbakam" is derived from which source?
(A) Bhagavad Gita
(B) Arthashastra by Chanakya
(C) Maha Upanishad (ancient Sanskrit text)
(D) More than one of the above
(E) None of the above

---

**Q37.** Which country held the G20 Presidency BEFORE India (2022)?
(A) Italy
(B) Saudi Arabia
(C) Indonesia
(D) More than one of the above
(E) None of the above

---

**Q38.** The G20 accounts for approximately what percentage of WORLD TRADE?
(A) 45%
(B) 75%
(C) 90%
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following is NOT a member of G20?
(A) Indonesia
(B) South Korea
(C) Pakistan
(D) More than one of the above
(E) None of the above

---

**Q40.** The G20 New Delhi Declaration 2023 was historically significant because:
(A) It created a permanent G20 secretariat in New Delhi
(B) It was adopted by CONSENSUS — all members agreed (despite Russia-Ukraine tensions)
(C) It announced sanctions against Russia
(D) More than one of the above
(E) None of the above

---

**Q41.** Which country held the G20 Presidency in 2024 (year AFTER India)?
(A) South Africa
(B) USA
(C) Brazil
(D) More than one of the above
(E) None of the above

---

**Q42.** The G20 Summit 2023 was held at which venue in New Delhi?
(A) Vigyan Bhawan
(B) Bharat Mandapam
(C) Rashtrapati Bhawan
(D) More than one of the above
(E) None of the above

---

**Q43.** G7 countries collectively account for approximately what share of global GDP?
(A) 85%
(B) 65%
(C) 45%
(D) More than one of the above
(E) None of the above

---

**Q44.** The G20 Sherpa is:
(A) The Finance Minister's representative
(B) The Head of State's personal envoy who coordinates policy before the Leaders' Summit
(C) A technical expert on climate issues only
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following is CORRECT about both G7 and G20?
(A) Both have permanent secretariats
(B) Both have legally binding decisions on member countries
(C) Both are informal forums with NO binding power; decisions are voluntary
(D) More than one of the above
(E) None of the above

---

**Q46.** The G20 was originally created in 1999 primarily to:
(A) Coordinate military alliances after Cold War
(B) Address global financial stability and economic coordination after the 1997-98 Asian financial crisis
(C) Replace the United Nations
(D) More than one of the above
(E) None of the above

---

**Q47.** Which BRICS nation is also a G7 member?
(A) India
(B) China
(C) None — no BRICS nation is a G7 member
(D) More than one of the above
(E) None of the above

---

**Q48.** Under India's G20 Presidency, how many meetings were organised across India?
(A) Around 20 meetings
(B) Around 100 meetings
(C) Over 200 meetings across 60+ cities
(D) More than one of the above
(E) None of the above

---

**Q49.** The concept of "Jan Bhagidari" (People's Participation) was associated with which event?
(A) India's BRICS Presidency 2021
(B) India's G20 Presidency 2023
(C) India's SCO Chairmanship 2023
(D) More than one of the above
(E) None of the above

---

**Q50.** G20 2025 is being hosted by:
(A) USA
(B) South Africa
(C) Indonesia
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
| 1 | (C) | Bubble Sort worst = O(n²) — reverse sorted, n(n-1)/2 comparisons |
| 2 | (D) | BOTH Bubble Sort AND Insertion Sort are stable (not just one) |
| 3 | (C) | Insertion Sort best = O(n) — inner while exits immediately for sorted input |
| 4 | (B) | Selection Sort selects MINIMUM from unsorted part, swaps to front |
| 5 | (C) | After first pass, LARGEST element (8) bubbles to the last position |
| 6 | (C) | Selection Sort is ALWAYS O(n²) — no best case improvement |
| 7 | (C) | Selection Sort: at most O(n) swaps — one per pass |
| 8 | (C) | Insertion Sort excels on nearly/already sorted data → O(n) |
| 9 | (C) | n-1 = 5-1 = 4 passes maximum needed for n=5 elements |
| 10 | (B) | All three are IN-PLACE with O(1) extra space (not all stable, not all O(n) best) |
| 11 | (B) | Strict > preserves stability — stops when equal element found |
| 12 | (C) | After 3 passes of Selection Sort: [11, 12, 22, 25, 64] — first 3 positions correct |
| 13 | (B) | Total comparisons = n(n-1)/2 — sum of 1+2+...+(n-1) |
| 14 | (B) | Selection Sort does only O(n) swaps — preferred for expensive write operations |
| 15 | (B) | Insertion Sort and optimized Bubble Sort are both adaptive — can exit early |
| 16 | (C) | Selection Sort: exactly n-1 swaps in worst case → O(n) |
| 17 | (C) | Selection Sort is O(n²) always; Insertion and Bubble = O(n) for sorted input |
| 18 | (B) | Elements greater than key are shifted right to make space |
| 19 | (C) | [3,1,4,1,5]: compare 3>1→swap:[1,3,4,1,5]; 3<4:no swap; 4>1→swap:[1,3,1,4,5]; 4<5:no swap. Result: [1,3,1,4,5] |
| 20 | (C) | Insertion Sort — picks each element and finds its correct spot in sorted part |
| 21 | (A) | Bubble & Insertion: O(n²) swaps worst; Selection: O(n) swaps (at most n-1) |
| 22 | (C) | Long-distance swaps (swap min to front) can displace equal elements |
| 23 | (C) | Insertion Sort naturally handles one new element at a time — ideal for online sorting |
| 24 | (C) | Insertion Sort uses O(1) extra space — in-place algorithm |
| 25 | (D) | Bubble: no adjacent swap (equal); Insertion: no shift (not strictly greater); Selection: swaps element with ITSELF (arr[i] with arr[i]) — technically a "swap" |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | G6 in 1975 (USA, UK, France, Germany, Italy, Japan); Canada joined 1976 → G7 |
| 27 | (C) | All G7 nations (USA, Canada, France, Germany, Italy, Japan, UK) are ALSO G20 members |
| 28 | (B) | Russia suspended from G8 in 2014 after annexing Crimea → back to G7 |
| 29 | (C) | G20 = ~85% of global GDP |
| 30 | (B) | Vasudhaiva Kutumbakam — One Earth, One Family, One Future |
| 31 | (C) | African Union joined as permanent member at New Delhi G20 Summit, Sept 2023 |
| 32 | (B) | Leaders Summit level started 2008 (Washington D.C.) after financial crisis |
| 33 | (D) | Many: China, India, Brazil, Russia, South Africa, Indonesia, Saudi Arabia, etc. |
| 34 | (B) | Troika = Past, Present, Future presidencies for continuity in G20 |
| 35 | (B) | Global Biofuels Alliance (GBA) launched during India's 2023 G20 Presidency |
| 36 | (C) | Maha Upanishad — "Vasudhaiva Kutumbakam" = "The world is one family" |
| 37 | (C) | Indonesia held G20 Presidency in 2022 (Bali Summit) |
| 38 | (B) | G20 = ~75% of world trade |
| 39 | (C) | Pakistan is NOT a G20 member (despite being a major economy) |
| 40 | (B) | New Delhi Declaration adopted by consensus — diplomatic achievement |
| 41 | (C) | Brazil held G20 Presidency in 2024 (Rio de Janeiro Summit) |
| 42 | (B) | Bharat Mandapam, Pragati Maidan, New Delhi |
| 43 | (C) | G7 = ~45% of global GDP (smaller share than G20's 85%) |
| 44 | (B) | Sherpa = personal envoy of Head of State; coordinates policy before summit |
| 45 | (C) | Both G7 and G20 are INFORMAL forums — no binding decisions, no enforcement |
| 46 | (B) | G20 created 1999 to coordinate response to 1997-98 Asian financial crisis |
| 47 | (C) | No BRICS member (Brazil, Russia, India, China, South Africa) is in G7 |
| 48 | (C) | 200+ meetings across 60+ Indian cities under India's G20 Presidency |
| 49 | (B) | Jan Bhagidari was India's approach to making G20 a mass movement in 2023 |
| 50 | (B) | South Africa holds G20 Presidency in 2025 |

---
---

# 🔁 DAY 30 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Sorting Algorithms

### The Master Summary Table:
```
Algorithm    | Best    | Average | Worst  | Space | Stable | Swaps (worst)
-------------|---------|---------|--------|-------|--------|---------------
Bubble Sort  | O(n)*   | O(n²)   | O(n²)  | O(1)  | ✅ YES | O(n²)
Selection Sort| O(n²)  | O(n²)   | O(n²)  | O(1)  | ❌ NO  | O(n) ← KEY!
Insertion Sort| O(n)   | O(n²)   | O(n²)  | O(1)  | ✅ YES | O(n²)

*Optimized Bubble Sort with swap flag only
```

### Core Concepts — One-Liners:
```
Bubble Sort:   Compare ADJACENT pairs; LARGEST bubbles to end each pass
               Optimized: add swap flag → O(n) best case for sorted input
               
Selection Sort: Find MINIMUM in unsorted part; SWAP to front each pass
               ALWAYS O(n²) — no early exit possible
               MINIMUM SWAPS = at most n-1 swaps (KEY ADVANTAGE)
               
Insertion Sort: Pick each element; INSERT at correct position by shifting
               BEST for nearly-sorted data; STABLE; good for online sorting
```

### PYQ Critical Points:
```
✅ STABLE:   Bubble Sort ✓  |  Insertion Sort ✓  |  Selection Sort ✗
✅ IN-PLACE: All three = O(1) space
✅ BEST CASE O(n): Bubble (optimized) and Insertion ONLY — NOT Selection
✅ WORST CASE: All three = O(n²)
✅ MIN SWAPS: Selection Sort = O(n) — at most n-1 swaps
✅ MAX SWAPS: Bubble and Insertion both O(n²) in worst case
✅ Selection Sort: SAME complexity in ALL cases (best = avg = worst = O(n²))
✅ Insertion Sort: ADAPTIVE — benefits from sorted/nearly-sorted input
✅ After k passes of Bubble Sort: k largest elements are in CORRECT position (from right)
✅ After k passes of Selection Sort: k smallest elements are in CORRECT position (from left)
```

### Common Traps:
```
TRAP 1: "All three have O(n) best case" → WRONG! Selection Sort = always O(n²)
TRAP 2: "Selection Sort is stable" → WRONG! It's UNSTABLE
TRAP 3: "Bubble Sort best = O(n) always" → WRONG! Only with swap flag optimization
TRAP 4: "Insertion Sort does few swaps" → Bubble-like shifting; O(n²) shifts in worst case
TRAP 5: After FIRST PASS of Bubble Sort → LARGEST element reaches last position
         After FIRST PASS of Selection Sort → SMALLEST element reaches first position
```

---

## ⚡ RAPID FIRE — G20 & G7

### G7 Members (Memory trick: "US Can France Get Italy Just UK"):
```
1. United States  4. Germany   7. United Kingdom
2. Canada         5. Italy     + European Union (special status)
3. France         6. Japan
```

### G20 Key Facts:
```
Founded: 1999 (finance level); 2008 (leaders level after financial crisis)
Members: 19 countries + EU + AU (from 2023) = effectively 21 entities
GDP:     ~85% of world GDP
Trade:   ~75% of world trade
```

### India G20 2023 — MUST KNOW:
```
Theme:     "Vasudhaiva Kutumbakam" (One Earth · One Family · One Future)
           Source: Maha Upanishad
Summit:    9-10 September 2023, Bharat Mandapam, New Delhi
Key Win:   African Union became PERMANENT G20 member (HISTORIC!)
Launch:    Global Biofuels Alliance (GBA)
Approach:  Jan Bhagidari — 200+ meetings across 60+ cities
Declaration: New Delhi Declaration — adopted by CONSENSUS
```

### G20 Presidency Timeline:
```
2021: Italy → 2022: Indonesia → 2023: INDIA ★ → 2024: Brazil → 2025: South Africa → 2026: USA
```

### G7 vs G20 — Critical Differences:
```
G7:  Rich nations only (~45% GDP, ~10% population), Russia EXCLUDED (2014)
G20: Rich + Developing (~85% GDP, ~67% population), Russia INCLUDED
Both: NO binding power, NO permanent secretariat, informal forums
China: G20 only (NOT G7)
India: G20 only (NOT G7)
Russia: G20 yes; G7 SUSPENDED since 2014
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Sorting hierarchy**: All three (Bubble, Selection, Insertion) = O(n²) worst/average; but Selection Sort is ALWAYS O(n²) — no best case improvement unlike other two
2. **Stability**: Bubble ✅ Stable | Insertion ✅ Stable | Selection ❌ Unstable — and all three are IN-PLACE O(1) space
3. **Key advantage per algorithm**: Bubble = simplest adaptive; Selection = MINIMUM swaps O(n); Insertion = best for nearly-sorted data and online sorting
4. **India G20 2023**: Theme = Vasudhaiva Kutumbakam; African Union joined as permanent member; New Delhi Declaration by consensus; Global Biofuels Alliance launched
5. **G7 vs G20**: G7 = 7 rich nations (~45% GDP), Russia suspended; G20 = 19+EU+AU (~85% GDP), Russia included; Neither has binding power

---

## 📅 DAY 31 PREVIEW — What's Coming Next:
**CS**: Advanced Sorting Algorithms — Merge Sort (divide & conquer, O(n log n), stable), Quick Sort (partition, O(n log n) avg, O(n²) worst, unstable), Heap Sort
**GS**: Indian Polity — Parliament of India: Lok Sabha, Rajya Sabha, Functions, Sessions, Bills, Parliamentary Procedures

---

*🚀 Day 30 of 170 complete — You're steadily building your exam armour, one algorithm at a time!*
