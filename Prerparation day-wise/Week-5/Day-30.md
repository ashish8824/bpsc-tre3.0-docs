# 📅 DAY 30 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## 🎯 CS: Sorting Algorithms — Bubble, Selection & Insertion Sort
## 🌍 GS: G20, G7 & Major International Organisations

> **Target:** Score 25/25 in CS + 25/25 in GS | **Phase 1 — Week 5**
> **Day 30 of 170 | You are 17.6% through your journey — keep going!** 🏆

---

# ══════════════════════════════════════════════════
# 🖥️ PART A — COMPUTER SCIENCE
# Topic: Bubble Sort, Selection Sort & Insertion Sort
# ══════════════════════════════════════════════════

---

## 📖 CS SECTION 1: WHY STUDY SORTING?

Sorting is ONE OF THE MOST TESTED topics in BPSC TRE across all three papers (TRE 1.0, 2.0, 3.0). Questions appear on:
- Time/Space complexity of each algorithm
- Which algorithm is **stable** vs **unstable**
- Which is **in-place** vs **not in-place**
- Behaviour on **already sorted** or **reverse sorted** arrays
- **Best / Average / Worst** case comparisons

All three algorithms today — Bubble, Selection, Insertion — share three properties:
1. **Comparison-based** (they compare elements to decide order)
2. **In-place** (they use O(1) extra memory)
3. **O(n²) worst-case** time complexity

---

## 📖 CS SECTION 2: BUBBLE SORT — COMPLETE MASTERY

### 🔵 Core Idea
> **"Repeatedly compare ADJACENT elements and SWAP them if they are in the wrong order."**
> After each full pass, the **LARGEST unsorted element BUBBLES UP** to its correct position — like a bubble rising in water.

---

### 🔵 Step-by-Step Algorithm

```
Given array: [64, 34, 25, 12, 22]
Goal: Sort in ASCENDING order

PASS 1 — Largest element (64) goes to end:
Step 1: Compare 64 and 34 → 64 > 34 → SWAP → [34, 64, 25, 12, 22]
Step 2: Compare 64 and 25 → 64 > 25 → SWAP → [34, 25, 64, 12, 22]
Step 3: Compare 64 and 12 → 64 > 12 → SWAP → [34, 25, 12, 64, 22]
Step 4: Compare 64 and 22 → 64 > 22 → SWAP → [34, 25, 12, 22, 64] ✓

PASS 2 — Second largest (34) goes to second-last:
Step 1: Compare 34 and 25 → SWAP → [25, 34, 12, 22, 64]
Step 2: Compare 34 and 12 → SWAP → [25, 12, 34, 22, 64]
Step 3: Compare 34 and 22 → SWAP → [25, 12, 22, 34, 64] ✓

PASS 3:
[12, 22, 25, 34, 64] ✓ Done in 3 passes!
```

---

### 🔵 ASCII Diagram — Bubble Sort Visual

```
Original: [64] [34] [25] [12] [22]

Pass 1:
  [64] ←compare→ [34]   SWAP!
  [34] [64] [25] [12] [22]
       [64] ←→  [25]   SWAP!
  [34] [25] [64] [12] [22]
            [64] ←→ [12] SWAP!
  [34] [25] [12] [64] [22]
                 [64]←→[22] SWAP!
  [34] [25] [12] [22] [64]  ← 64 SETTLED ✓

Pass 2: Largest unsettled = 34 bubbles up
  [25] [12] [22] [34] | [64] ← 34 SETTLED ✓

Pass 3:
  [12] [22] [25] | [34] [64] ← 25 SETTLED ✓

Pass 4:
  [12] [22] | [25] [34] [64] ← 22 SETTLED ✓

SORTED: [12] [22] [25] [34] [64] 🎉
```

---

### 🔵 Bubble Sort — Code (C++)

```cpp
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {         // n-1 passes
        bool swapped = false;                 // Optimization flag
        for (int j = 0; j < n-i-1; j++) {   // Unsorted portion
            if (arr[j] > arr[j+1]) {
                swap(arr[j], arr[j+1]);       // Swap adjacent
                swapped = true;
            }
        }
        if (!swapped) break;  // Already sorted — BEST CASE O(n)!
    }
}
```

**KEY INSIGHT:** The `swapped` flag is what makes Best Case O(n). Without it, always O(n²).

---

### 🔵 Bubble Sort Complexity

| Case | Condition | Time | Why |
|------|-----------|------|-----|
| **Best Case** | Already sorted (with flag) | **O(n)** | 1 pass, 0 swaps |
| **Best Case** | Already sorted (NO flag) | **O(n²)** | Still does all comparisons |
| **Average Case** | Random order | **O(n²)** | ~n²/2 comparisons |
| **Worst Case** | Reverse sorted | **O(n²)** | Maximum swaps needed |
| **Space** | Any | **O(1)** | Only temp swap variable |

---

### 🔵 Bubble Sort Properties

```
✅ STABLE: YES
   Equal elements maintain original relative order
   Example: [3a, 2, 3b, 1] → [1, 2, 3a, 3b] (a before b preserved)

✅ IN-PLACE: YES
   Uses O(1) extra memory — only a temp variable for swapping

❌ NOT Divide & Conquer
❌ NOT efficient for large data (O(n²))
✅ Best for: Nearly sorted arrays + Educational purposes
```

---

### 🔵 Number of Comparisons & Swaps

```
For n elements:
- Comparisons: n(n-1)/2  ← this is O(n²)
- Worst-case swaps: n(n-1)/2
- Passes needed: n-1 passes maximum

Example n=5:
- Comparisons = 5×4/2 = 10
- Maximum swaps = 10
```

---

## 📖 CS SECTION 3: SELECTION SORT — COMPLETE MASTERY

### 🟡 Core Idea
> **"Find the MINIMUM element in the unsorted part and PLACE it at the beginning."**
> Unlike Bubble Sort, Selection Sort does FEWER SWAPS — at most n-1 swaps total.

---

### 🟡 Step-by-Step Algorithm

```
Given array: [64, 25, 12, 22, 11]
Goal: Sort in ASCENDING order

PASS 1: Find minimum in [64, 25, 12, 22, 11]
  Minimum = 11 (at index 4)
  Swap 11 with first element (64)
  [11, 25, 12, 22, 64]  ← 11 is in correct position ✓

PASS 2: Find minimum in [25, 12, 22, 64]
  Minimum = 12 (at index 2)
  Swap 12 with first of unsorted (25)
  [11, 12, 25, 22, 64]  ← 12 is in correct position ✓

PASS 3: Find minimum in [25, 22, 64]
  Minimum = 22 (at index 3)
  Swap 22 with 25
  [11, 12, 22, 25, 64]  ← 22 in position ✓

PASS 4: Find minimum in [25, 64]
  Minimum = 25 (already in position)
  No swap needed
  [11, 12, 22, 25, 64]  ← Done! ✓
```

---

### 🟡 ASCII Diagram — Selection Sort Visual

```
Array: [64] [25] [12] [22] [11]

Pass 1: Scan ALL → Find MIN = 11
        ┌──────────────────────┐
        │  Scan: 64>25>12>11 ← MIN
        └──────────────────────┘
        Swap index 0 (64) ↔ index 4 (11)
        [11] [25] [12] [22] [64]
         ✓ FIXED

Pass 2: Scan [25, 12, 22, 64] → Find MIN = 12
        Swap index 1 (25) ↔ index 2 (12)
        [11] [12] [25] [22] [64]
              ✓ FIXED

Pass 3: Scan [25, 22, 64] → Find MIN = 22
        Swap index 2 (25) ↔ index 3 (22)
        [11] [12] [22] [25] [64]
                   ✓ FIXED

Pass 4: Scan [25, 64] → Find MIN = 25
        Already in position → No swap
        [11] [12] [22] [25] [64]
                        ✓ FIXED

SORTED: [11] [12] [22] [25] [64] 🎉
```

---

### 🟡 Selection Sort — Code (C++)

```cpp
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {
        int minIdx = i;                        // Assume first is minimum
        for (int j = i+1; j < n; j++) {
            if (arr[j] < arr[minIdx]) {
                minIdx = j;                    // Found smaller element
            }
        }
        if (minIdx != i) {
            swap(arr[i], arr[minIdx]);         // Place minimum at front
        }
    }
}
```

---

### 🟡 Selection Sort Complexity

| Case | Time | Why |
|------|------|-----|
| **Best Case** | **O(n²)** | ALWAYS scans full unsorted portion |
| **Average Case** | **O(n²)** | No shortcut possible |
| **Worst Case** | **O(n²)** | Same as always |
| **Space** | **O(1)** | In-place |

**CRITICAL EXAM POINT:** Selection Sort is O(n²) in ALL cases — no optimization possible. It does NOT have an O(n) best case like Bubble Sort!

---

### 🟡 Selection Sort Properties

```
❌ STABLE: NO (in standard implementation)
   Example: [3a, 3b, 1] → after pass 1: [1, 3b, 3a]
   3a and 3b swapped! ← Not stable

✅ IN-PLACE: YES — O(1) space

✅ MINIMUM SWAPS: At most n-1 swaps
   → Best when WRITE OPERATIONS are costly (e.g., flash memory)

❌ NOT efficient for large datasets
✅ Best when: Memory writes are expensive (swaps are costly)
```

---

### 🟡 Number of Comparisons

```
Selection Sort ALWAYS makes exactly:
n(n-1)/2 comparisons regardless of input

For n=5: 4+3+2+1 = 10 comparisons ALWAYS
This is why it's ALWAYS O(n²) — no early termination!
```

---

## 📖 CS SECTION 4: INSERTION SORT — COMPLETE MASTERY

### 🟢 Core Idea
> **"Pick each element one by one and INSERT it into its CORRECT position in the already-sorted portion."**
> Think of it like sorting playing cards — you pick one card at a time and slide it into the right place.

---

### 🟢 Step-by-Step Algorithm

```
Given array: [12, 11, 13, 5, 6]

Start: Sorted portion = [12]  Unsorted = [11, 13, 5, 6]

Step 1: Pick 11
  Compare with 12 → 11 < 12 → Shift 12 right
  Insert 11 at position 0
  Array: [11, 12, 13, 5, 6]  ✓

Step 2: Pick 13
  Compare with 12 → 13 > 12 → No shift needed
  13 stays in place
  Array: [11, 12, 13, 5, 6]  ✓

Step 3: Pick 5
  Compare with 13 → 5 < 13 → Shift 13 right → [11, 12, _, 13, 6]
  Compare with 12 → 5 < 12 → Shift 12 right → [11, _, 12, 13, 6]
  Compare with 11 → 5 < 11 → Shift 11 right → [_, 11, 12, 13, 6]
  Insert 5 at position 0
  Array: [5, 11, 12, 13, 6]  ✓

Step 4: Pick 6
  Compare with 13 → Shift → [5, 11, 12, _, 13]
  Compare with 12 → Shift → [5, 11, _, 12, 13]
  Compare with 11 → Shift → [5, _, 11, 12, 13]
  Compare with 5  → 6 > 5  → Stop!
  Insert 6 at position 1
  Array: [5, 6, 11, 12, 13]  ✓ SORTED!
```

---

### 🟢 ASCII Diagram — Insertion Sort Visual

```
Playing Card Analogy:

Start:   |12| 11  13   5   6
          ↑ sorted

Pass 1:  Pick 11
         |12| → shift right
         Insert 11 before 12
         |11  12| 13   5   6
          ↑↑ sorted

Pass 2:  Pick 13
         13 > 12 → no shift
         |11  12  13|  5   6
          ↑↑↑ sorted

Pass 3:  Pick 5
         Shift 13, 12, 11 all right
         Insert 5 at front
         | 5  11  12  13|  6
          ↑↑↑↑ sorted

Pass 4:  Pick 6
         Shift 13, 12, 11 right
         6 > 5 → stop
         Insert 6 after 5
         | 5   6  11  12  13|
          ↑↑↑↑↑ sorted = DONE! 🎉
```

---

### 🟢 Insertion Sort — Code (C++)

```cpp
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];         // Element to be inserted
        int j = i - 1;

        // Shift elements greater than key to one position right
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;         // Insert key in correct position
    }
}
```

---

### 🟢 Insertion Sort Complexity

| Case | Condition | Time | Why |
|------|-----------|------|-----|
| **Best Case** | Already sorted | **O(n)** | Inner while loop never executes |
| **Average Case** | Random | **O(n²)** | ~n²/4 shifts on average |
| **Worst Case** | Reverse sorted | **O(n²)** | Maximum shifts every time |
| **Space** | Any | **O(1)** | In-place, only 'key' variable |

---

### 🟢 Insertion Sort Properties

```
✅ STABLE: YES
   Equal elements maintain original relative order

✅ IN-PLACE: YES — O(1) space

✅ ONLINE ALGORITHM: YES
   Can sort data as it arrives (no need to have all data first)

✅ ADAPTIVE: YES
   Performs fewer operations on nearly-sorted arrays

✅ Best for: Small arrays, Nearly sorted data, Online sorting
```

---

## 📖 CS SECTION 5: SIDE-BY-SIDE COMPARISON — THE MASTER TABLE

This is the MOST IMPORTANT table for BPSC TRE. Memorize it completely!

```
┌─────────────────┬──────────────┬──────────────┬──────────────┐
│  Property       │ BUBBLE SORT  │SELECTION SORT│INSERTION SORT│
├─────────────────┼──────────────┼──────────────┼──────────────┤
│ Best Case       │   O(n)*      │   O(n²)      │   O(n)       │
│ Average Case    │   O(n²)      │   O(n²)      │   O(n²)      │
│ Worst Case      │   O(n²)      │   O(n²)      │   O(n²)      │
│ Space           │   O(1)       │   O(1)       │   O(1)       │
│ Stable?         │   YES ✅     │   NO ❌      │   YES ✅     │
│ In-Place?       │   YES ✅     │   YES ✅     │   YES ✅     │
│ Adaptive?       │   YES (flag) │   NO         │   YES ✅     │
│ Online?         │   NO         │   NO         │   YES ✅     │
│ D & C?          │   NO         │   NO         │   NO         │
│ Min Swaps?      │   NO         │   YES ✅     │   No swaps** │
└─────────────────┴──────────────┴──────────────┴──────────────┘

* Bubble best case O(n) ONLY with optimization flag
** Insertion uses shifts, not swaps
```

---

## 📖 CS SECTION 6: STABILITY — DEEP UNDERSTANDING

**Stable Sort:** When two elements have the SAME VALUE, they appear in the same RELATIVE ORDER in the sorted output as they were in the input.

### Why It Matters — Real Example

```
Input: [(Ram, 85), (Shyam, 90), (Geeta, 85), (Priya, 75)]
Sort by marks (ascending):

STABLE sort result:
  (Priya, 75), (Ram, 85), (Geeta, 85), (Shyam, 90)
  → Ram comes BEFORE Geeta (same as input) ✓

UNSTABLE sort result (possible):
  (Priya, 75), (Geeta, 85), (Ram, 85), (Shyam, 90)
  → Geeta and Ram ORDER MAY CHANGE ✗
```

**Stable Sorts (must remember):** Bubble, Insertion, Merge, Counting, Radix
**Unstable Sorts:** Selection, Quick, Heap

---

## 📖 CS SECTION 7: WHEN TO USE WHICH SORT?

```
Use BUBBLE SORT when:
  → Educational/learning purposes
  → Array is nearly sorted (with flag optimization)
  → n is very small (< 10 elements)

Use SELECTION SORT when:
  → Memory WRITE operations are expensive (flash/EEPROM)
  → Minimizing number of swaps is the goal
  → n is very small

Use INSERTION SORT when:
  → Array is small (n < 50)
  → Array is nearly sorted (very fast in this case)
  → Online sorting (elements arrive one by one)
  → As part of hybrid sorts (TimSort uses it for small subarrays)
```

---

## 📖 CS SECTION 8: TRICKY EXAM QUESTIONS & TRAPS

### Trap 1: Selection Sort Best Case
```
WRONG thinking: "If array is already sorted, Selection Sort is faster"
CORRECT: Selection Sort is ALWAYS O(n²) — it always scans full unsorted portion
```

### Trap 2: Bubble Sort Best Case
```
WRONG: "Bubble sort is always O(n²)"
CORRECT: With optimization flag → O(n) best case
Without flag → O(n²) even for sorted input
```

### Trap 3: Stability of Selection Sort
```
WRONG: "Selection Sort is stable"
CORRECT: Standard Selection Sort is UNSTABLE
Counter-example: [3a, 3b, 1] → after pass 1: swap(3a, 1) → [1, 3b, 3a]
3a and 3b changed relative order → UNSTABLE
```

### Trap 4: Number of Passes
```
For n elements:
- Bubble Sort: at most n-1 passes
- Selection Sort: exactly n-1 passes
- Insertion Sort: n-1 iterations
```

### Trap 5: Comparing with Merge Sort
```
Question: "Which basic O(n²) sort is best for nearly-sorted data?"
Answer: INSERTION SORT (not Bubble, not Selection)
Because: Insertion Sort is adaptive — fewer shifts on nearly-sorted data
```

### Trap 6: Inversion Count
```
Number of SWAPS in Bubble Sort = Number of INVERSIONS in array
An inversion: pair (i,j) where i < j but arr[i] > arr[j]
Example: [3, 1, 2] → inversions = (3,1) and (3,2) = 2 inversions = 2 swaps
```

---

## 📖 CS SECTION 9: PASS-BY-PASS TRACE — EXAM PRACTICE

### Example: Sort [29, 10, 14, 37, 13] using Bubble Sort

```
PASS 1:
  [29,10] → swap → [10,29,14,37,13]
  [29,14] → swap → [10,14,29,37,13]
  [29,37] → no swap → [10,14,29,37,13]
  [37,13] → swap → [10,14,29,13,37]  ← 37 settled

PASS 2:
  [10,14] → no swap
  [14,29] → no swap
  [29,13] → swap → [10,14,13,29,37]  ← 29 settled

PASS 3:
  [10,14] → no swap
  [14,13] → swap → [10,13,14,29,37]  ← 14 settled

PASS 4:
  [10,13] → no swap → DONE!

Final: [10, 13, 14, 29, 37] ✓
```

### Example: Sort [29, 10, 14, 37, 13] using Insertion Sort

```
i=1: key=10, shift 29 → [10, 29, 14, 37, 13]
i=2: key=14, shift 29 → [10, 14, 29, 37, 13]
i=3: key=37, no shift → [10, 14, 29, 37, 13]
i=4: key=13, shift 37,29,14 → [10, 13, 14, 29, 37] ✓
```

---

## 📖 CS SECTION 10: COMPARISON ON SPECIAL INPUTS

| Input Type | Bubble | Selection | Insertion |
|------------|--------|-----------|-----------|
| Already sorted | O(n)* | O(n²) | O(n) ✅ |
| Reverse sorted | O(n²) ← worst | O(n²) | O(n²) ← worst |
| Random | O(n²) | O(n²) | O(n²) |
| Nearly sorted | O(n)* | O(n²) | O(n) ✅ |

*With optimization flag

---

# ═══════════════════════════════════════════
# 📝 CS PRACTICE QUESTIONS — 25 MCQs
## ⚠️ ATTEMPT ALL BEFORE CHECKING ANSWERS AT END!
# ═══════════════════════════════════════════

---

**Q1.** Which of the following sorting algorithms has O(n) best-case time complexity?

(A) Selection Sort
(B) Quick Sort
(C) Insertion Sort (with optimization)
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the time complexity of Selection Sort in its BEST CASE?

(A) O(n)
(B) O(n log n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q3.** In Bubble Sort, after completing the k-th pass over an array of n elements, which of the following is guaranteed?

(A) The first k elements are in their final sorted positions
(B) The last k elements are in their final sorted positions
(C) The array is fully sorted
(D) More than one of the above
(E) None of the above

---

**Q4.** Which of the following sorting algorithms is UNSTABLE?

(A) Bubble Sort
(B) Merge Sort
(C) Selection Sort
(D) More than one of the above
(E) None of the above

---

**Q5.** Which sorting algorithm makes the MINIMUM number of swaps (at most n-1 swaps)?

(A) Bubble Sort
(B) Insertion Sort
(C) Selection Sort
(D) More than one of the above
(E) None of the above

---

**Q6.** Insertion Sort is said to be an ONLINE algorithm because:

(A) It works only with internet-connected computers
(B) It can sort elements as they arrive one by one without needing all elements upfront
(C) It uses network sorting
(D) More than one of the above
(E) None of the above

---

**Q7.** For an array of n elements, Bubble Sort (without optimization) makes exactly how many comparisons?

(A) n
(B) n log n
(C) n(n-1)/2
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following sorts is best suited for a NEARLY SORTED array?

(A) Selection Sort
(B) Merge Sort
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q9.** Consider array [5, 3, 8, 2, 1]. After the FIRST PASS of Bubble Sort (ascending), the array becomes:

(A) [1, 3, 5, 2, 8]
(B) [3, 5, 2, 1, 8]
(C) [3, 5, 8, 2, 1]
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is TRUE about Insertion Sort?

(A) It is adaptive — performs better on nearly sorted input
(B) It is stable — equal elements maintain original order
(C) It is in-place — uses O(1) extra space
(D) More than one of the above
(E) None of the above

---

**Q11.** The worst case for Insertion Sort occurs when the input array is:

(A) Already sorted in ascending order
(B) All elements are equal
(C) Sorted in descending (reverse) order
(D) More than one of the above
(E) None of the above

---

**Q12.** Consider sorting array [64, 25, 12, 22, 11] using Selection Sort. After the SECOND PASS, the array is:

(A) [11, 12, 22, 25, 64]
(B) [11, 12, 25, 22, 64]
(C) [11, 12, 64, 22, 25]
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following properties are shared by ALL THREE of: Bubble Sort, Selection Sort, and Insertion Sort?

(A) Stable sorting
(B) O(n) best case complexity
(C) In-place with O(1) space and O(n²) worst case
(D) More than one of the above
(E) None of the above

---

**Q14.** In Bubble Sort, the optimization (using a `swapped` flag) helps achieve O(n) in which case?

(A) When input is reverse sorted
(B) When input is already sorted
(C) When all elements are equal
(D) More than one of the above
(E) None of the above

---

**Q15.** The number of SWAPS performed by Selection Sort on an array of n elements is at most:

(A) n(n-1)/2
(B) n²
(C) n-1
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following sorting algorithms is ADAPTIVE (performs better on partially sorted input)?

(A) Selection Sort
(B) Insertion Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q17.** In Insertion Sort, what is done with the "key" element during each pass?

(A) It is swapped with its adjacent element like Bubble Sort
(B) It is compared with all remaining elements to find minimum
(C) It is compared with sorted portion and shifted to correct position
(D) More than one of the above
(E) None of the above

---

**Q18.** Selection Sort is preferred over Bubble Sort when:

(A) The array is nearly sorted
(B) Memory write operations are very expensive
(C) Stability is required
(D) More than one of the above
(E) None of the above

---

**Q19.** What is the space complexity of Bubble Sort, Selection Sort, and Insertion Sort?

(A) O(n) for all three
(B) O(log n) for all three
(C) O(1) for all three
(D) More than one of the above
(E) None of the above

---

**Q20.** How many passes does Bubble Sort need at MINIMUM to sort array [1, 2, 4, 3, 5]?

(A) 4 passes
(B) 1 pass
(C) 2 passes
(D) More than one of the above
(E) None of the above

---

**Q21.** In Selection Sort, the inner loop always scans the ENTIRE unsorted portion. This is the reason why Selection Sort:

(A) Is stable
(B) Cannot have O(n) best case (always O(n²))
(C) Is a divide-and-conquer algorithm
(D) More than one of the above
(E) None of the above

---

**Q22.** The number of INVERSIONS in array [3, 1, 2] equals the number of swaps Bubble Sort makes. How many inversions does [3, 1, 2] have?

(A) 1
(B) 3
(C) 2
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following algorithms is both STABLE and can achieve O(n) best case?

(A) Selection Sort
(B) Quick Sort
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q24.** For sorting a small array (n ≤ 10) that is nearly sorted, which algorithm gives the BEST practical performance?

(A) Merge Sort
(B) Quick Sort
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q25.** PYQ-Style: Which of the following statements is/are CORRECT?
```
I.  Bubble Sort is a stable, in-place, O(n²) algorithm.
II. Selection Sort always performs O(n²) comparisons regardless of input.
III. Insertion Sort has O(n) best case when array is already sorted.
```

(A) Only I and III
(B) Only II
(C) All of I, II and III are correct
(D) More than one of the above
(E) None of the above

---

# ══════════════════════════════════════════════════
# 🌍 PART B — GENERAL STUDIES
# Topic: G20, G7 & Major International Organisations
# ══════════════════════════════════════════════════

---

## 📖 GS SECTION 1: G20 — GROUP OF TWENTY

### 🌐 What is G20?

```
G20 = Group of Twenty
Type: International Economic Forum (NOT an organisation with permanent treaty)
Members: 19 countries + European Union + African Union (AU added 2023)
Total Members: 21 (as of 2023 — AU joined at India's G20 Summit)
Represents: ~85% of world GDP, ~75% world trade, ~2/3 world population
```

### 🌐 G20 — Key Facts Table

| Fact | Detail |
|------|--------|
| **Founded** | 1999 (Finance Ministers level); 2008 (Heads of State level) |
| **First Summit** | Washington D.C., USA (2008) |
| **India's Presidency** | December 1, 2022 – November 30, 2023 |
| **India's G20 Theme** | "Vasudhaiva Kutumbakam" (One Earth, One Family, One Future) |
| **India's G20 Summit** | New Delhi, September 9-10, 2023 |
| **AU joins G20** | African Union added at India's summit (2023) |
| **Headquarters** | No permanent secretariat (rotating presidency) |
| **Current Presidency** | South Africa (2025) |

---

### 🌐 G20 Member Countries (Memorize for BPSC!)

```
G20 MEMBERS (21 total):

Americas:    USA, Canada, Brazil, Argentina, Mexico
Europe:      Germany, France, Italy, UK, Russia, EU
Asia:        India, China, Japan, South Korea, Indonesia, Saudi Arabia
Africa:      South Africa, African Union (AU — added 2023)
Oceania:     Australia
Turkey:      (bridges Europe-Asia)

Memory Trick for G20:
"US Can Buy Argentina's Mexico — Germany France Italy Rubs EU —
India China Japan Korea Indon Saudi — South Africa AU Australia Turkey"
```

---

### 🌐 India's G20 Presidency — BPSC Special

```
India's G20 2023 highlights:
✅ Theme: "Vasudhaiva Kutumbakam" (from Maha Upanishad)
   Meaning: "The World is One Family"
✅ Logo: Lotus on globe (7 petals = 7 continents)
✅ African Union became the 21st member (permanent)
✅ "Voice of Global South Summit" hosted by India
✅ New Delhi Declaration adopted unanimously
✅ 200+ meetings across 60 Indian cities
✅ One of the most productive G20 summits
✅ India advocated for developing nations' interests
```

---

## 📖 GS SECTION 2: G7 — GROUP OF SEVEN

### 🌐 What is G7?

```
G7 = Group of Seven most advanced industrialized democracies
Type: Informal bloc of major economies
Members: USA, UK, France, Germany, Italy, Canada, Japan + EU (as observer)
Focus: Economic policies, security, climate, health
Represents: ~45% of world GDP
```

### 🌐 G7 Key Facts

| Fact | Detail |
|------|--------|
| **Founded** | 1975 (as G6, Canada joined 1976 → G7) |
| **Russia's status** | Joined → G8; expelled 2014 after Crimea annexation → back to G7 |
| **No permanent secretariat** | Rotating presidency |
| **Recent hosts** | Italy 2024, Canada 2025 |
| **India's role** | Invited as guest, not permanent member |

---

### 🌐 G7 vs G20 — Key Differences

```
┌─────────────────┬──────────────────┬──────────────────┐
│  Feature        │      G7          │      G20         │
├─────────────────┼──────────────────┼──────────────────┤
│ Members         │ 7 countries + EU │ 19+EU+AU = 21    │
│ Focus           │ Industrialized   │ All major        │
│                 │ democracies      │ economies        │
│ India member?   │ NO (guest)       │ YES ✅           │
│ Founded         │ 1975             │ 1999/2008        │
│ Russia          │ Expelled (2014)  │ Still member     │
│ Africa rep      │ None             │ AU (2023+)       │
│ GDP coverage    │ ~45%             │ ~85%             │
└─────────────────┴──────────────────┴──────────────────┘
```

---

## 📖 GS SECTION 3: BRICS

### What is BRICS?

```
BRICS = Brazil, Russia, India, China, South Africa
Type: Economic bloc of emerging economies
Founded: 2006 (as BRIC), 2010 (South Africa joined → BRICS)
Headquarters: No permanent HQ (NDB in Shanghai)

2024 Expansion — New BRICS+ Members:
Egypt, Ethiopia, Iran, UAE, Saudi Arabia joined 2024
Argentina invited but DECLINED to join

NDB = New Development Bank (BRICS Bank)
NDB HQ = Shanghai, China
NDB President: Dilma Rousseff (former Brazil President)
```

---

## 📖 GS SECTION 4: MAJOR INTERNATIONAL ORGANISATIONS — MASTER TABLE

### 🏛️ United Nations & Related

| Organisation | HQ | Founded | Purpose |
|-------------|-----|---------|---------|
| **UN** | New York, USA | 1945 | International peace & security |
| **UN Security Council** | New York | 1945 | 5 permanent members (P5) |
| **UNGA** | New York | 1945 | All 193 members, 1 vote each |
| **WHO** | Geneva, Switzerland | 1948 | Global health |
| **UNESCO** | Paris, France | 1945 | Education, Science, Culture |
| **UNICEF** | New York, USA | 1946 | Children's welfare |
| **FAO** | Rome, Italy | 1945 | Food & Agriculture |
| **ILO** | Geneva | 1919 | Labour standards |
| **UNDP** | New York | 1965 | Development programmes |
| **IMF** | Washington DC | 1944 | Monetary stability |
| **World Bank** | Washington DC | 1944 | Development loans |
| **WTO** | Geneva | 1995 | International trade rules |
| **IAEA** | Vienna, Austria | 1957 | Nuclear energy oversight |

---

### 🏛️ Regional & Economic Organisations

| Organisation | Full Form | HQ | Key Members |
|-------------|-----------|-----|-------------|
| **SAARC** | South Asian Association for Regional Cooperation | Kathmandu, Nepal | India, Pakistan, Bangladesh, Nepal, Sri Lanka, Bhutan, Maldives, Afghanistan |
| **ASEAN** | Association of Southeast Asian Nations | Jakarta, Indonesia | 10 SE Asian nations |
| **NATO** | North Atlantic Treaty Organisation | Brussels, Belgium | USA, UK, France + 30+ members |
| **SCO** | Shanghai Cooperation Organisation | Beijing, China | India, China, Russia, Pakistan + others |
| **OPEC** | Organisation of Petroleum Exporting Countries | Vienna, Austria | Saudi, UAE, Iraq, Iran + others |
| **Commonwealth** | Commonwealth of Nations | London, UK | 56 nations (former British Empire) |
| **AU** | African Union | Addis Ababa, Ethiopia | 55 African nations |
| **OIC** | Organisation of Islamic Cooperation | Jeddah, Saudi Arabia | 57 Muslim-majority nations |
| **EU** | European Union | Brussels, Belgium | 27 member states |
| **APEC** | Asia-Pacific Economic Cooperation | Singapore | 21 Pacific Rim economies |

---

## 📖 GS SECTION 5: UN SECURITY COUNCIL — P5 MEMBERS

```
5 PERMANENT MEMBERS (P5) — have VETO POWER:
1. United States of America (USA)
2. United Kingdom (UK)
3. Russia
4. France
5. China

Memory: "USA UK Russia France China"
Or: "Uncle Raj's Free Crispy Urad dal"
(U-USA, R-Russia, F-France, C-China, U-UK)

Total UNSC members = 15 (5 permanent + 10 rotating non-permanent)
Non-permanent members serve 2-year terms
India has served as NON-PERMANENT member 8 times
India's bid for PERMANENT membership ongoing
```

---

## 📖 GS SECTION 6: INDIA & INTERNATIONAL ORGANISATIONS

```
India is member of:
✅ UN (founding member, 1945)
✅ G20 (member)
✅ BRICS (founding member)
✅ SAARC (founding member)
✅ SCO (joined 2017)
✅ Commonwealth of Nations
✅ WTO
✅ IMF & World Bank
✅ IAEA
✅ Quad (USA, India, Japan, Australia — security dialogue)

India is NOT member of:
❌ G7 (invited as guest sometimes)
❌ NATO
❌ OPEC
❌ OIC (observer status only)
❌ ASEAN (dialogue partner, not full member)
❌ EU
```

---

## 📖 GS SECTION 7: IMPORTANT HEADQUARTERS — MUST MEMORISE

```
CITY          →  ORGANISATION(S)
──────────────────────────────────────────────
New York      → UN, UNICEF, UNDP, NYSE
Washington DC → IMF, World Bank, OAS, World Monetary Fund
Geneva        → WHO, WTO, ILO, UNHCR, Red Cross (ICRC)
Paris         → UNESCO, OECD, Interpol (HQ moved from Paris)
Brussels      → NATO, EU (Parliament in Strasbourg)
Vienna        → IAEA, OPEC, UNIDO
Rome          → FAO, IFAD, WFP
London        → Commonwealth, IMO
Nairobi       → UNEP, UN-Habitat
Kathmandu     → SAARC
Jakarta       → ASEAN
Addis Ababa   → African Union (AU)
Shanghai      → NDB (New Development Bank / BRICS Bank)
Beijing       → SCO (headquarters)
Jeddah        → OIC
Singapore     → APEC Secretariat
```

---

## 📖 GS SECTION 8: CURRENT AFFAIRS — G20 INDIA 2023 SPECIAL

### BPSC-Relevant Facts about India's G20 Presidency

```
Key Events During India's G20 (Dec 2022 – Nov 2023):

1. Theme: "Vasudhaiva Kutumbakam" (Sanskrit: One Earth, One Family, One Future)
2. African Union became PERMANENT G20 member (at India's initiative)
3. Voice of Global South Summit — India championed developing nations
4. Digital Public Infrastructure (DPI) agenda — India promoted UPI, Aadhaar model
5. Green Development Pact signed
6. New Delhi Declaration — adopted by CONSENSUS (all 43 members agreed)
7. India's presidency covered 200+ meetings in 60 cities
8. G20 University Connect — reached 7,500+ universities
9. Launched "Global Biofuels Alliance" 
10. Millet Year promotion — India proposed 2023 as International Year of Millets
```

---

## 📖 GS SECTION 9: BIHAR GK CONNECTION

```
BIHAR & INTERNATIONAL ORGANISATIONS:

→ Nalanda International University:
   - Re-established 2014 at Rajgir, Bihar
   - Ancient Nalanda was a global centre of learning (5th-12th century)
   - Nalanda University was UNESCO recognised

→ G20 Meetings in Bihar:
   - During India's G20 presidency (2023), meetings held across India
   - Development Finance Institution track discussed inclusive growth

→ Bihar's role in SAARC:
   - Patna (Bihar capital) has important trade links with Nepal
   - Nepal is SAARC member sharing border with Bihar
   - India-Nepal trade corridor through Bihar (Raxaul-Kathmandu corridor)

→ International Millet Year 2023:
   - India proposed this at UN
   - Bihar is a significant producer of millets (maize, sorghum, bajra)
```

---

## 📖 GS SECTION 10: IMPORTANT INTERNATIONAL SUMMITS & INDIA

| Summit/Meeting | Year | Host | Key India Outcomes |
|---------------|------|------|-------------------|
| G20 Summit | 2023 | India (New Delhi) | AU joined G20; New Delhi Declaration |
| SCO Summit | 2023 | India (virtual) | India hosted as SCO chair |
| Quad Summit | 2023 | Australia | India-USA-Japan-Australia cooperation |
| COP28 | 2023 | UAE (Dubai) | India's climate pledges |
| BRICS Summit | 2023 | South Africa | BRICS expansion announced |
| G20 Summit | 2024 | Brazil (Rio) | India participated |
| UN Summit of Future | 2024 | New York | India signed Pact for the Future |

---

# ═══════════════════════════════════════════
# 📝 GS PRACTICE QUESTIONS — 25 MCQs
## ⚠️ ATTEMPT ALL BEFORE CHECKING ANSWERS AT END!
# ═══════════════════════════════════════════

---

**Q26.** What was the theme of India's G20 Presidency (2022-2023)?

(A) Unity in Diversity
(B) Vasudhaiva Kutumbakam — One Earth, One Family, One Future
(C) Sustainable Development for All
(D) More than one of the above
(E) None of the above

---

**Q27.** India hosted its G20 Summit in which city and year?

(A) Mumbai, 2022
(B) Bengaluru, 2023
(C) New Delhi, September 2023
(D) More than one of the above
(E) None of the above

---

**Q28.** At India's G20 Summit (2023), which new bloc was granted PERMANENT membership in G20?

(A) ASEAN
(B) SAARC
(C) African Union (AU)
(D) More than one of the above
(E) None of the above

---

**Q29.** How many countries are currently permanent members (P5) of the UN Security Council, each holding VETO power?

(A) 7
(B) 3
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q30.** The headquarters of the World Health Organisation (WHO) is located in:

(A) New York, USA
(B) Paris, France
(C) Geneva, Switzerland
(D) More than one of the above
(E) None of the above

---

**Q31.** SAARC (South Asian Association for Regional Cooperation) headquarters is in:

(A) New Delhi, India
(B) Kathmandu, Nepal
(C) Islamabad, Pakistan
(D) More than one of the above
(E) None of the above

---

**Q32.** Russia was expelled from G8 (which became G7 again) due to which event?

(A) Nuclear weapons testing in 2008
(B) Annexation of Crimea from Ukraine in 2014
(C) Moscow's withdrawal from WTO in 2018
(D) More than one of the above
(E) None of the above

---

**Q33.** G20 represents approximately what percentage of world GDP?

(A) 45%
(B) 60%
(C) 85%
(D) More than one of the above
(E) None of the above

---

**Q34.** The New Development Bank (NDB), also called the BRICS Bank, has its headquarters in:

(A) Beijing, China
(B) Mumbai, India
(C) Shanghai, China
(D) More than one of the above
(E) None of the above

---

**Q35.** Which of the following international organisations has its headquarters in Rome, Italy?

(A) WHO
(B) WTO
(C) FAO (Food and Agriculture Organisation)
(D) More than one of the above
(E) None of the above

---

**Q36.** India joined the Shanghai Cooperation Organisation (SCO) as a FULL member in which year?

(A) 2001
(B) 2010
(C) 2017
(D) More than one of the above
(E) None of the above

---

**Q37.** OPEC (Organisation of Petroleum Exporting Countries) has its headquarters in:

(A) Riyadh, Saudi Arabia
(B) Abu Dhabi, UAE
(C) Vienna, Austria
(D) More than one of the above
(E) None of the above

---

**Q38.** Which of the following is correct about the G7?

(A) India is a permanent G7 member
(B) G7 represents about 85% of world GDP
(C) G7 was founded in 1975 and currently has 7 member nations (USA, UK, France, Germany, Italy, Canada, Japan)
(D) More than one of the above
(E) None of the above

---

**Q39.** UNESCO (United Nations Educational, Scientific and Cultural Organisation) is headquartered in:

(A) Geneva
(B) New York
(C) Paris
(D) More than one of the above
(E) None of the above

---

**Q40.** The "Quad" grouping consists of which four countries?

(A) USA, UK, France, Germany
(B) India, China, Russia, Brazil
(C) USA, India, Japan, Australia
(D) More than one of the above
(E) None of the above

---

**Q41.** BRICS was originally formed as BRIC in 2006. Which country joined LATER to complete BRICS?

(A) Brazil
(B) India
(C) South Africa
(D) More than one of the above
(E) None of the above

---

**Q42.** The International Atomic Energy Agency (IAEA) — which monitors nuclear energy and weapons — is headquartered in:

(A) Geneva, Switzerland
(B) Vienna, Austria
(C) Brussels, Belgium
(D) More than one of the above
(E) None of the above

---

**Q43.** Which international organisation has 193 member states and every member gets ONE vote in the General Assembly?

(A) G20
(B) UN General Assembly (UNGA)
(C) Commonwealth of Nations
(D) More than one of the above
(E) None of the above

---

**Q44.** During India's G20 Presidency in 2023, India launched which new global energy alliance?

(A) International Solar Alliance
(B) Global Biofuels Alliance
(C) Green Hydrogen Alliance
(D) More than one of the above
(E) None of the above

---

**Q45.** ASEAN (Association of Southeast Asian Nations) is headquartered in:

(A) Singapore
(B) Bangkok, Thailand
(C) Jakarta, Indonesia
(D) More than one of the above
(E) None of the above

---

**Q46.** The African Union (AU) has its headquarters in:

(A) Johannesburg, South Africa
(B) Nairobi, Kenya
(C) Addis Ababa, Ethiopia
(D) More than one of the above
(E) None of the above

---

**Q47.** India has served as a NON-PERMANENT member of the UN Security Council approximately how many times?

(A) 3 times
(B) 8 times
(C) 12 times
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following organisations was founded at the Bretton Woods Conference (1944)?

(A) WTO and WHO
(B) NATO and UN
(C) IMF and World Bank
(D) More than one of the above
(E) None of the above

---

**Q49.** The New Delhi Declaration was adopted at India's G20 Summit 2023. This was significant because it was adopted:

(A) With majority vote
(B) By consensus (unanimously by all members)
(C) By only G7 members
(D) More than one of the above
(E) None of the above

---

**Q50.** In 2023, which countries NEWLY joined BRICS (as BRICS expansion was announced)?

(A) Egypt, Ethiopia, Iran, UAE joined in 2024
(B) France, Germany joined BRICS in 2023
(C) Australia and Canada joined BRICS
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════
# 🔑 ANSWER KEY — CHECK ONLY AFTER ATTEMPTING!
## CS Answers (Q1–Q25) + GS Answers (Q26–Q50)
# ═══════════════════════════════════════════

---

## ✅ CS ANSWERS (Q1–Q25)

| Q | Answer | Explanation |
|---|--------|-------------|
| **Q1** | **(D)** | Both Bubble Sort (with flag optimization) AND Insertion Sort have O(n) best case. Selection Sort does NOT. So D = More than one. |
| **Q2** | **(C)** | Selection Sort is ALWAYS O(n²) — even in best case. It always scans the full unsorted portion. |
| **Q3** | **(B)** | In Bubble Sort, after k passes, the LAST k elements are in their FINAL sorted positions (largest elements bubble to end). |
| **Q4** | **(C)** | Selection Sort is UNSTABLE. Bubble Sort and Merge Sort are stable. A classic BPSC trap question. |
| **Q5** | **(C)** | Selection Sort makes at most n-1 swaps — one per pass. Bubble Sort can make O(n²) swaps. |
| **Q6** | **(B)** | Online algorithm = can process elements as they arrive without needing complete data. Insertion sort works on each new element immediately. |
| **Q7** | **(C)** | Bubble Sort comparisons = n(n-1)/2 = (n-1)+(n-2)+...+1 = n(n-1)/2. This is always O(n²). |
| **Q8** | **(C)** | Insertion Sort is best for nearly sorted arrays. It's adaptive — fewer comparisons/shifts needed. |
| **Q9** | **(B)** | [5,3,8,2,1]: Compare 5,3→swap [3,5,8,2,1]; 5,8→no swap; 8,2→swap [3,5,2,8,1]; 8,1→swap → [3,5,2,1,8]. So answer is [3,5,2,1,8]. None of A/B/C match exactly except B=[3,5,2,1,8]. |
| **Q10** | **(D)** | ALL THREE statements about Insertion Sort are correct: adaptive, stable, in-place. Answer = D (More than one). |
| **Q11** | **(C)** | Insertion Sort worst case = reverse sorted. Every element must shift all the way to the front. Maximum O(n²) shifts. |
| **Q12** | **(B)** | Selection Sort on [64,25,12,22,11]: Pass 1 finds min=11, swap with 64 → [11,25,12,22,64]. Pass 2 finds min=12, swap with 25 → [11,12,25,22,64]. |
| **Q13** | **(C)** | All three share: In-place (O(1) space) AND O(n²) worst case. NOT all are stable (Selection isn't). NOT all have O(n) best case (Selection doesn't). So only C is correct for ALL three. |
| **Q14** | **(D)** | Both B (already sorted — 0 swaps) and C (all equal — same as already sorted) give O(n) with the flag. Answer = D (More than one). |
| **Q15** | **(C)** | Selection Sort swaps = at most n-1 (one swap per pass, n-1 passes). This is its key advantage. |
| **Q16** | **(B)** | Insertion Sort is adaptive. Bubble Sort is also somewhat adaptive with flag. Selection Sort is NOT adaptive. Answer is B (Insertion Sort — the primary adaptive sort). |
| **Q17** | **(C)** | Insertion Sort: key is compared with the sorted portion and elements are SHIFTED right until correct position is found. |
| **Q18** | **(B)** | Selection Sort is preferred when write operations are costly — it does minimum swaps (n-1). Not when stability needed (it's unstable). Not for nearly sorted (Insertion is better then). |
| **Q19** | **(C)** | All three are IN-PLACE algorithms — O(1) space. They only use a constant amount of extra memory. |
| **Q20** | **(C)** | [1,2,4,3,5]: Pass 1 will swap 4 and 3 → [1,2,3,4,5]. Pass 2 checks and finds no swaps (flag) → stops. Minimum 2 passes. |
| **Q21** | **(B)** | Because inner loop always scans entire unsorted portion (regardless of order), Selection Sort cannot have O(n) best case — always O(n²). |
| **Q22** | **(C)** | [3,1,2]: Inversions are (3,1) — 3 before 1 but 3>1, and (3,2) — 3 before 2 but 3>2. Total = 2 inversions. |
| **Q23** | **(C)** | Insertion Sort is both STABLE (maintains equal elements order) and has O(n) BEST CASE (already sorted). Selection Sort isn't stable. Quick Sort isn't stable and has O(n²) worst. |
| **Q24** | **(C)** | For small, nearly-sorted arrays, Insertion Sort is the practical winner. Merge Sort and Quick Sort have overhead that makes them slower for tiny n. |
| **Q25** | **(C)** | All three statements I, II, III are correct. Answer = C (All correct). Note: C says "All of I, II, III correct" — this is the answer, not D, because D would be if multiple ANSWER OPTIONS were right. |

---

## ✅ GS ANSWERS (Q26–Q50)

| Q | Answer | Explanation |
|---|--------|-------------|
| **Q26** | **(B)** | India's G20 theme was "Vasudhaiva Kutumbakam" from Maha Upanishad — "The World is One Family." |
| **Q27** | **(C)** | India hosted G20 Leaders' Summit in New Delhi on September 9-10, 2023. |
| **Q28** | **(C)** | At India's initiative, the African Union (AU) — representing 55 African nations — became the 21st permanent G20 member. |
| **Q29** | **(C)** | 5 permanent P5 members with veto: USA, UK, France, Russia, China. |
| **Q30** | **(C)** | WHO HQ = Geneva, Switzerland. Common BPSC question. |
| **Q31** | **(B)** | SAARC HQ = Kathmandu, Nepal. NOT New Delhi! Common trap. |
| **Q32** | **(B)** | Russia was expelled from G8 in 2014 after annexing Crimea (Ukraine). G8 reverted to G7. |
| **Q33** | **(C)** | G20 = ~85% of world GDP. G7 = ~45%. Key difference. |
| **Q34** | **(C)** | NDB (BRICS Bank) HQ = Shanghai, China. NOT Beijing. |
| **Q35** | **(C)** | FAO (Food and Agriculture Organisation) HQ = Rome, Italy. WHO = Geneva. WTO = Geneva. |
| **Q36** | **(C)** | India joined SCO as full member in 2017 at Astana Summit. Pakistan also joined same year. |
| **Q37** | **(C)** | OPEC HQ = Vienna, Austria. Common trick — people think Saudi Arabia. |
| **Q38** | **(C)** | G7 was founded in 1975 with 7 members (USA, UK, France, Germany, Italy, Canada, Japan). India is NOT a permanent G7 member. G7 = ~45% GDP, not 85%. |
| **Q39** | **(C)** | UNESCO HQ = Paris, France. Common BPSC question. |
| **Q40** | **(C)** | Quad = USA, India, Japan, Australia. Security dialogue focused on Indo-Pacific. |
| **Q41** | **(C)** | BRIC was Brazil, Russia, India, China. South Africa joined in 2010 to make BRICS. |
| **Q42** | **(B)** | IAEA HQ = Vienna, Austria (same city as OPEC). |
| **Q43** | **(B)** | UN General Assembly = 193 members, each with 1 vote. G20 is not a UN organ. Commonwealth ≠ 193 members. |
| **Q44** | **(B)** | India launched Global Biofuels Alliance during G20 2023. International Solar Alliance was launched at Paris COP21 in 2015 (earlier). |
| **Q45** | **(C)** | ASEAN HQ = Jakarta, Indonesia. APEC Secretariat = Singapore. |
| **Q46** | **(C)** | African Union HQ = Addis Ababa, Ethiopia. Key for G20 context questions. |
| **Q47** | **(B)** | India has served as non-permanent UNSC member about 8 times. India seeks permanent membership. |
| **Q48** | **(C)** | IMF and World Bank were both founded at Bretton Woods Conference, 1944. WTO came later (1995 from GATT). WHO founded 1948. |
| **Q49** | **(B)** | New Delhi Declaration was notable because it was adopted by CONSENSUS — all members agreed, including on sensitive Russia-Ukraine language. |
| **Q50** | **(A)** | Egypt, Ethiopia, Iran, UAE, Saudi Arabia were invited to join BRICS — they formally joined in 2024. Argentina was also invited but the new government (Milei) declined. |

---

# ═══════════════════════════════════════════
# 🏆 DAY 30 — TOPPER'S QUICK REVISION CARD
# ═══════════════════════════════════════════

## ⚡ CS — 10 MUST-REMEMBER FACTS

1. **Bubble Sort:** O(n) best (WITH flag), O(n²) worst — **STABLE, IN-PLACE**
2. **Selection Sort:** O(n²) in ALL cases (no exceptions) — **UNSTABLE, IN-PLACE, min swaps**
3. **Insertion Sort:** O(n) best (sorted input), O(n²) worst — **STABLE, IN-PLACE, ONLINE, ADAPTIVE**
4. **After k passes of Bubble Sort:** LAST k elements are in final position
5. **After k passes of Selection Sort:** FIRST k elements are in final position
6. **Stable sorts (from today):** Bubble ✅, Insertion ✅, Selection ❌
7. **All three are comparison-based and in-place (O(1) space)**
8. **Number of swaps: Selection Sort ≤ n-1 (minimum among the three)**
9. **Best for nearly-sorted data: INSERTION SORT**
10. **Selection Sort O(n²) because:** inner loop always scans entire unsorted portion

## ⚡ GS — 10 MUST-REMEMBER FACTS

1. **G20 = 21 members** (19 + EU + AU since 2023) | ~85% world GDP
2. **India's G20 theme:** "Vasudhaiva Kutumbakam" | Summit: New Delhi, Sept 2023
3. **African Union** became permanent G20 member at India's summit (2023)
4. **G7 = 7 members** (USA, UK, France, Germany, Italy, Canada, Japan) | ~45% GDP
5. **Russia expelled from G8 in 2014** → reverted to G7
6. **SAARC HQ = Kathmandu** (NOT New Delhi!) | 8 members
7. **WHO = Geneva | UNESCO = Paris | FAO = Rome | IAEA = Vienna | OPEC = Vienna**
8. **NDB (BRICS Bank) = Shanghai** | BRICS = 5 original + new 2024 members
9. **P5 UNSC veto members:** USA, UK, France, Russia, China
10. **India joined SCO in 2017** | India NOT in G7 (only invited as guest)

---

## 📊 Day 30 Self-Assessment

| Category | Questions | My Score | Target |
|----------|-----------|----------|--------|
| Bubble Sort (Q1–Q9) | 9 | /9 | 8+ |
| Selection + Insertion (Q10–Q25) | 16 | /16 | 14+ |
| G20 & G7 (Q26–Q38) | 13 | /13 | 11+ |
| International Orgs (Q39–Q50) | 12 | /12 | 11+ |
| **TOTAL** | **50** | **/50** | **44+** |

> **44+/50 = Topper Zone** 🏆
> **38–43 = Review wrong answers before Day 31**
> **Below 38 = Re-read concept sections tonight**

---

## 📝 Tonight's 5-Bullet Summary (Write in Your Notebook!)

1. Three O(n²) sorts today: _______, _______, _______ — all in-place, comparison-based
2. Only UNSTABLE sort among the three: _______
3. Best case O(n) sort(s): _______ and _______
4. India's G20 theme: _______ | new member added: _______
5. SAARC HQ: _______ | WHO HQ: _______ | OPEC HQ: _______

---

*Day 30 Complete ✅ | Tomorrow: Day 31 — Merge Sort, Quick Sort & Divide and Conquer*
*30 days done. You are building an unshakeable foundation. Keep pushing!* 🎯
