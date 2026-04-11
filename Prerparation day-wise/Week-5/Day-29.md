# 📅 DAY 29 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## 🎯 CS: Big-O Notation & Time Complexity Analysis | GS: ISRO Missions & Space Science

> **Target:** Score 25/25 in CS + 25/25 in GS | **Exam Readiness Level: TOPPER MODE**
> **Date:** Day 29 of 170-Day Plan | **Phase:** Phase 1 — Foundation

---

# ═══════════════════════════════════════════
# 🖥️ PART A: COMPUTER SCIENCE
## Topic: Big-O Notation, Time & Space Complexity
# ═══════════════════════════════════════════

---

## 📖 SECTION 1: WHAT IS COMPLEXITY ANALYSIS?

When we write an algorithm, two questions matter most:

1. **How FAST does it run?** → **Time Complexity**
2. **How much MEMORY does it use?** → **Space Complexity**

We use **Asymptotic Notations** to express these without tying them to specific hardware or input size.

---

## 📖 SECTION 2: THE THREE ASYMPTOTIC NOTATIONS

### 🔴 Big-O Notation → O(f(n)) — UPPER BOUND

```
Definition: f(n) = O(g(n))
Meaning: In the WORST CASE, the algorithm will NOT run
         slower than g(n) × some constant.

Informal: "My algorithm will take AT MOST this long."
```

**EXAM TRAP:** Big-O = WORST CASE upper bound. It does NOT describe average case!

Example: Linear search on array of n elements
- Best case: Element found at index 0 → O(1)
- Worst case: Element at last position or not found → O(n)
- **Big-O = O(n)** (we use WORST CASE)

---

### 🟡 Big-Omega Notation → Ω(f(n)) — LOWER BOUND

```
Definition: f(n) = Ω(g(n))
Meaning: In the BEST CASE, the algorithm will take AT LEAST
         g(n) time.

Informal: "My algorithm will take AT LEAST this long."
```

Example: Sorting any array requires at least O(n log n) comparisons
→ All comparison-based sorting: Ω(n log n)

---

### 🟢 Big-Theta Notation → Θ(f(n)) — TIGHT BOUND

```
Definition: f(n) = Θ(g(n))
Meaning: The algorithm runs in EXACTLY g(n) time (both upper
         and lower bounds are the same).

Informal: "My algorithm takes EXACTLY this long (on average)."
```

Example: Merge Sort always takes n log n → Θ(n log n)

---

### ⚡ QUICK MEMORY TRICK

```
O   = Oh no, WORST case!      (upper bound)
Ω   = Omega is the END (best) (lower bound)
Θ   = Theta = TIGHT (exact)   (tight bound)

  Best ←————————————→ Worst
  Ω              Θ        O
```

---

## 📖 SECTION 3: COMPLEXITY HIERARCHY (MOST IMPORTANT!)

```
FASTEST                                         SLOWEST
   |                                               |
   ↓                                               ↓
O(1) → O(log n) → O(√n) → O(n) → O(n log n) → O(n²) → O(n³) → O(2ⁿ) → O(n!)
```

### Visual Comparison Table

| Notation | Name | Example | n=10 operations |
|----------|------|---------|-----------------|
| O(1) | Constant | Array index access | 1 |
| O(log n) | Logarithmic | Binary search | ~3 |
| O(√n) | Square root | Checking prime | ~3 |
| O(n) | Linear | Linear search | 10 |
| O(n log n) | Linearithmic | Merge sort | ~33 |
| O(n²) | Quadratic | Bubble sort | 100 |
| O(n³) | Cubic | Matrix multiply | 1000 |
| O(2ⁿ) | Exponential | Fibonacci recursive | 1024 |
| O(n!) | Factorial | Permutations | 3628800 |

---

## 📖 SECTION 4: ALGORITHM COMPLEXITIES — MUST MEMORIZE TABLE

### 🔥 MOST ASKED IN BPSC TRE PYQs

| Algorithm | Best Case | Average Case | Worst Case | Space |
|-----------|-----------|--------------|------------|-------|
| **Linear Search** | O(1) | O(n) | O(n) | O(1) |
| **Binary Search** | O(1) | O(log n) | O(log n) | O(1) |
| **Bubble Sort** | O(n)* | O(n²) | O(n²) | O(1) |
| **Selection Sort** | O(n²) | O(n²) | O(n²) | O(1) |
| **Insertion Sort** | O(n) | O(n²) | O(n²) | O(1) |
| **Merge Sort** | O(n log n) | O(n log n) | O(n log n) | O(n) |
| **Quick Sort** | O(n log n) | O(n log n) | O(n²) | O(log n) |
| **Heap Sort** | O(n log n) | O(n log n) | O(n log n) | O(1) |
| **Radix Sort** | O(nk) | O(nk) | O(nk) | O(n+k) |
| **Infix→Postfix** | O(n) | O(n) | O(n) | O(n) |
| **Stack Push/Pop** | O(1) | O(1) | O(1) | O(1) |
| **Queue Enqueue/Dequeue** | O(1) | O(1) | O(1) | O(1) |

*Bubble sort best case O(n) only with optimized version (flag check)

---

## 📖 SECTION 5: HOW TO CALCULATE TIME COMPLEXITY — STEP BY STEP

### Rule 1: Simple Statement = O(1)
```cpp
int x = 5;          // O(1)
x = x + 1;         // O(1)
cout << arr[i];    // O(1) — array access is O(1)
```

### Rule 2: Single Loop = O(n)
```cpp
for (int i = 0; i < n; i++) {
    cout << arr[i];   // O(1) × n iterations = O(n)
}
```

### Rule 3: Nested Loop = O(n²)
```cpp
for (int i = 0; i < n; i++) {          // n times
    for (int j = 0; j < n; j++) {      // n times
        cout << arr[i][j];              // O(1)
    }
}
// Total = n × n × O(1) = O(n²)
```

### Rule 4: Loop that halves = O(log n)
```cpp
int i = n;
while (i > 1) {
    i = i / 2;   // Dividing by 2 each time → O(log n)
}
```

### Rule 5: Loop in Loop — Different bounds
```cpp
for (int i = 0; i < n; i++) {      // n times
    for (int j = 0; j < i; j++) {  // i times (0,1,2,...,n-1)
        // total = 0+1+2+...+(n-1) = n(n-1)/2 = O(n²)
    }
}
```

### Rule 6: Adding vs Multiplying
```cpp
// SEQUENTIAL code → ADD complexities
for (int i=0; i<n; i++) { }   // O(n)
for (int j=0; j<n; j++) { }   // O(n)
// Total = O(n) + O(n) = O(n)  [drop constants, take dominant]

// NESTED code → MULTIPLY complexities
for (int i=0; i<n; i++) {     // O(n)
    for (int j=0; j<n; j++) {}// O(n)
}
// Total = O(n) × O(n) = O(n²)
```

---

## 📖 SECTION 6: BINARY SEARCH — DETAILED ANALYSIS

Binary Search is one of the MOST frequently asked topics in BPSC TRE.

### Prerequisites
- Array MUST be SORTED
- Works by repeatedly halving the search space

### Algorithm
```
Given sorted array A[0..n-1], search for target T:

Step 1: low = 0, high = n-1
Step 2: mid = (low + high) / 2
Step 3: If A[mid] == T → FOUND, return mid
Step 4: If T < A[mid] → high = mid - 1 (search LEFT half)
Step 5: If T > A[mid] → low = mid + 1 (search RIGHT half)
Step 6: Repeat until low > high → NOT FOUND
```

### ASCII Diagram — Binary Search on [2, 5, 8, 12, 16, 23, 38, 56] searching for 23

```
Array: [2,  5,  8,  12, 16, 23, 38, 56]
Index:  0   1   2   3   4   5   6   7

PASS 1:
low=0, high=7, mid=3
A[3]=12, target=23
23 > 12 → search RIGHT → low = mid+1 = 4

[2,  5,  8,  12, |16, 23, 38, 56|]
                   ↑              ↑
                  low            high

PASS 2:
low=4, high=7, mid=5
A[5]=23, target=23
23 == 23 → FOUND at index 5! ✓

Total: 2 comparisons for n=8
log₂(8) = 3, so worst case needs ≤ 3 comparisons
```

### Time Complexity Derivation

```
After each step, the search space HALVES:
Start:    n elements
Pass 1:   n/2 elements
Pass 2:   n/4 elements
Pass k:   n/2^k elements

When n/2^k = 1 → k = log₂(n)

Therefore: Binary Search = O(log n)
```

---

## 📖 SECTION 7: SPACE COMPLEXITY

Space complexity = total memory used by algorithm

### Types of Space
1. **Fixed/Auxiliary Space** — for variables, constants (independent of n)
2. **Variable Space** — depends on input size n

### Common Examples

| Algorithm | Space Complexity | Reason |
|-----------|-----------------|--------|
| Binary Search (iterative) | O(1) | Only uses 3 variables (low, high, mid) |
| Binary Search (recursive) | O(log n) | Recursion stack depth = log n |
| Merge Sort | O(n) | Needs temporary array of size n |
| Quick Sort | O(log n) avg | Recursion stack |
| Bubble Sort | O(1) | In-place, no extra memory |
| DFS (Graph) | O(V) | Stack/recursion stores vertices |
| BFS (Graph) | O(V) | Queue stores vertices |

---

## 📖 SECTION 8: MASTER THEOREM (For Recursive Algorithms)

The Master Theorem solves recurrences of the form:
```
T(n) = aT(n/b) + f(n)

Where:
a = number of subproblems
b = factor by which problem size is reduced
f(n) = cost of dividing and combining
```

### Three Cases

```
Compare f(n) with n^(log_b a):

Case 1: f(n) = O(n^(log_b a - ε))  → T(n) = Θ(n^(log_b a))
Case 2: f(n) = Θ(n^(log_b a))      → T(n) = Θ(n^(log_b a) × log n)
Case 3: f(n) = Ω(n^(log_b a + ε))  → T(n) = Θ(f(n))
```

### Applied Examples

**Merge Sort:** T(n) = 2T(n/2) + O(n)
- a=2, b=2, f(n)=n
- n^(log₂ 2) = n^1 = n
- f(n) = n = Θ(n^1) → Case 2
- **T(n) = Θ(n log n)** ✓

**Binary Search:** T(n) = T(n/2) + O(1)
- a=1, b=2, f(n)=1
- n^(log₂ 1) = n^0 = 1
- f(n) = 1 = Θ(1) → Case 2
- **T(n) = Θ(log n)** ✓

---

## 📖 SECTION 9: TRICKY CONCEPTS & COMMON EXAM TRAPS

### Trap 1: Big-O vs Average Case
```
❌ WRONG: "Binary search is O(1) because sometimes it finds in first step"
✅ RIGHT: Binary search is O(log n) — Big-O is WORST CASE
```

### Trap 2: Nested Loops with Different Variables
```cpp
for (int i=0; i<m; i++) {
    for (int j=0; j<n; j++) { }
}
// Complexity = O(m×n), NOT O(n²)
// Only O(n²) if both loops run n times
```

### Trap 3: Log Base Doesn't Matter in Big-O
```
O(log₂ n) = O(log₃ n) = O(log n)
Because: log₂(n) = log₃(n) / log₃(2) = constant × log₃(n)
Constants are dropped in Big-O!
```

### Trap 4: Constant Factors Are Dropped
```
O(3n²) = O(n²)
O(100n) = O(n)
O(n² + n) = O(n²)   [take dominant term]
```

### Trap 5: Quick Sort Worst Case
```
Quick Sort worst case = O(n²) when:
- Pivot is always the smallest or largest element
- This happens on SORTED or REVERSE-SORTED arrays
- Solution: Use random pivot selection
```

### Trap 6: Merge Sort Space
```
Merge Sort is NOT in-place → needs O(n) extra space
Quick Sort IS in-place → O(log n) space (only stack)
This is why Quick Sort is preferred in practice despite worse worst-case
```

---

## 📖 SECTION 10: SORTING ALGORITHM PROPERTIES — EXAM TABLE

| Algorithm | Stable? | In-Place? | Divide & Conquer? | Comparison-Based? |
|-----------|---------|-----------|-------------------|-------------------|
| Bubble Sort | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes |
| Selection Sort | ❌ No | ✅ Yes | ❌ No | ✅ Yes |
| Insertion Sort | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes |
| Merge Sort | ✅ Yes | ❌ No | ✅ Yes | ✅ Yes |
| Quick Sort | ❌ No | ✅ Yes | ✅ Yes | ✅ Yes |
| Heap Sort | ❌ No | ✅ Yes | ❌ No | ✅ Yes |
| Radix Sort | ✅ Yes | ❌ No | ❌ No | ❌ No |
| Counting Sort | ✅ Yes | ❌ No | ❌ No | ❌ No |

**Stable Sort:** Equal elements maintain their ORIGINAL ORDER
**In-Place:** Uses O(1) extra memory (not counting input)

---

## 📖 SECTION 11: RECURRENCE RELATIONS — PRACTICE

| Recurrence | Solution | Algorithm |
|-----------|----------|-----------|
| T(n) = T(n-1) + O(1) | O(n) | Factorial (recursive) |
| T(n) = T(n/2) + O(1) | O(log n) | Binary Search |
| T(n) = T(n-1) + O(n) | O(n²) | Insertion Sort |
| T(n) = 2T(n/2) + O(n) | O(n log n) | Merge Sort |
| T(n) = 2T(n-1) + O(1) | O(2ⁿ) | Tower of Hanoi |
| T(n) = T(n-1) + T(n-2) | O(2ⁿ) | Fibonacci (naive) |

---

## 📖 SECTION 12: PYQ SPECIAL — PREVIOUS YEAR PATTERNS

### From BPSC TRE 1.0, 2.0, 3.0 — High-Frequency Topics:

1. **"Which algorithm has O(n log n) in ALL cases?"** → Merge Sort
2. **"Binary search requires what?"** → Sorted array
3. **"What is Big-O notation?"** → Upper bound of worst case
4. **"Infix to Postfix conversion time complexity?"** → O(N)
5. **"Which sort is stable?"** → Bubble, Insertion, Merge
6. **"Which sort is NOT comparison-based?"** → Radix, Counting
7. **"Quick sort worst case?"** → O(n²) when pivot is min/max

---

# ═══════════════════════════════════════════
# 📝 CS PRACTICE QUESTIONS — 25 MCQs
## (Answers at the END of the document)
# ═══════════════════════════════════════════

---

**Q1.** What does Big-O notation represent in algorithm analysis?

(A) The average-case running time of an algorithm
(B) The best-case running time of an algorithm
(C) The upper bound of the worst-case running time
(D) More than one of the above
(E) None of the above

---

**Q2.** The time complexity of Binary Search on a sorted array of n elements is:

(A) O(n)
(B) O(n²)
(C) O(n log n)
(D) More than one of the above
(E) None of the above

---

**Q3.** Which sorting algorithm has O(n log n) time complexity in ALL three cases (best, average, and worst)?

(A) Quick Sort
(B) Bubble Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q4.** The time complexity of converting an Infix expression to Postfix using a stack is:

(A) O(n²)
(B) O(n log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q5.** What is the WORST-CASE time complexity of Quick Sort?

(A) O(n log n)
(B) O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following sorting algorithms is NOT a comparison-based sort?

(A) Merge Sort
(B) Heap Sort
(C) Radix Sort
(D) More than one of the above
(E) None of the above

---

**Q7.** Consider the following code:
```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i * j;
    }
}
```
What is its time complexity?

(A) O(n)
(B) O(n log n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following correctly represents the complexity hierarchy from FASTEST to SLOWEST?

(A) O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ)
(B) O(log n) < O(1) < O(n) < O(n²) < O(n log n) < O(2ⁿ)
(C) O(1) < O(n) < O(log n) < O(n log n) < O(n²) < O(2ⁿ)
(D) More than one of the above
(E) None of the above

---

**Q9.** Binary Search requires which PREREQUISITE condition?

(A) Array must be of even size
(B) Array must be sorted
(C) Array must not contain duplicates
(D) More than one of the above
(E) None of the above

---

**Q10.** The recurrence relation T(n) = 2T(n/2) + O(n) represents which algorithm?

(A) Binary Search
(B) Quick Sort (average case)
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q11.** What is the SPACE complexity of Merge Sort?

(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q12.** Which sorting algorithm is STABLE AND IN-PLACE?

(A) Merge Sort
(B) Quick Sort
(C) Bubble Sort
(D) More than one of the above
(E) None of the above

---

**Q13.** Big-Theta notation (Θ) represents:

(A) Upper bound of an algorithm
(B) Lower bound of an algorithm
(C) Tight bound — both upper and lower
(D) More than one of the above
(E) None of the above

---

**Q14.** The time complexity of accessing an element in an array by index is:

(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the time complexity of Selection Sort in ALL cases?

(A) O(n) best case, O(n²) worst case
(B) O(n log n) all cases
(C) O(n²) in all cases
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following is TRUE about Big-O notation?

(A) O(3n²) and O(n²) are considered equivalent
(B) O(n² + n) = O(n²) because lower-order terms are dropped
(C) O(log₂ n) = O(log₁₀ n) = O(log n) in Big-O
(D) More than one of the above
(E) None of the above

---

**Q17.** The time complexity of Push and Pop operations in a Stack are respectively:

(A) O(n) and O(1)
(B) O(1) and O(n)
(C) O(1) and O(1)
(D) More than one of the above
(E) None of the above

---

**Q18.** In which case does Quick Sort exhibit its WORST-CASE time complexity of O(n²)?

(A) When the array is randomly shuffled
(B) When the pivot is always chosen as the median
(C) When the pivot is always the smallest or largest element (sorted input)
(D) More than one of the above
(E) None of the above

---

**Q19.** The space complexity of Binary Search when implemented ITERATIVELY (not recursive) is:

(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q20.** Which divide-and-conquer sorting algorithm is NOT in-place?

(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q21.** The Tower of Hanoi problem with n discs has which time complexity?

(A) O(n²)
(B) O(n log n)
(C) O(2ⁿ)
(D) More than one of the above
(E) None of the above

---

**Q22.** For the following loop, what is the time complexity?
```cpp
int i = 1;
while (i < n) {
    i = i * 2;
}
```

(A) O(n)
(B) O(n²)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following algorithms has the BEST time complexity for searching in an unsorted array?

(A) Binary Search — O(log n)
(B) Linear Search — O(n)
(C) Jump Search — O(√n)
(D) More than one of the above
(E) None of the above

---

**Q24.** Bubble Sort with an optimized "early termination" flag has which BEST CASE complexity?

(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q25.** The recurrence T(n) = T(n/2) + O(1) solved by the Master Theorem gives:

(A) O(n)
(B) O(n²)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════
# 🌍 PART B: GENERAL STUDIES
## Topic: ISRO Missions, Space Science & Science & Technology GK
# ═══════════════════════════════════════════

---

## 📖 GS SECTION 1: ISRO — Indian Space Research Organisation

### 🏢 Basic Facts

| Fact | Detail |
|------|--------|
| **Full Form** | Indian Space Research Organisation |
| **Founded** | 1969 |
| **Headquarters** | Bengaluru (Bangalore), Karnataka |
| **Founded by** | Dr. Vikram Sarabhai (Father of Indian Space Programme) |
| **Current Chairman** | S. Somanath (as of 2024–25) |
| **Under Ministry** | Ministry of Space / Department of Space |
| **Parent Agency** | Department of Space, Govt. of India |

---

## 📖 GS SECTION 2: MAJOR ISRO LAUNCH VEHICLES

```
ISRO ROCKET FAMILY:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SLV (Satellite Launch Vehicle)
  └── First Indian launch vehicle, 1979-80
  └── Payload: 40 kg to LEO

ASLV (Augmented SLV)
  └── Retired, limited success

PSLV (Polar Satellite Launch Vehicle) ← MOST IMPORTANT
  └── Workhorse of ISRO
  └── 4 variants: PSLV-G, PSLV-CA, PSLV-XL, PSLV-DL
  └── Most reliable, 50+ successful missions
  └── Used for: IRS, Chandrayaan-1, MOM, Astrosat

GSLV (Geosynchronous Satellite Launch Vehicle)
  └── Mk I, Mk II, Mk III (LVM3)
  └── Uses cryogenic engine
  └── For heavier GEO satellites

LVM3 (Launch Vehicle Mark 3) formerly GSLV Mk III
  └── India's heaviest rocket
  └── Used for Chandrayaan-3, OneWeb launches
```

---

## 📖 GS SECTION 3: MAJOR ISRO MISSIONS — DETAILED

### 🌕 CHANDRAYAAN SERIES (Moon Missions)

| Mission | Year | Key Facts |
|---------|------|-----------|
| **Chandrayaan-1** | 2008 | India's 1st Moon mission; confirmed WATER on Moon; used PSLV-C11 |
| **Chandrayaan-2** | 2019 | Orbiter succeeded; Vikram lander crashed during soft landing; used GSLV Mk III |
| **Chandrayaan-3** | 2023 | India SUCCESSFULLY landed on Moon's SOUTH POLE (Shiv Shakti Point); 4th country to land on Moon; 1st at South Pole; used LVM3 |

**KEY FACT for BPSC:** Chandrayaan-3 landing site = **Shiv Shakti Point** (near South Pole). India is the FIRST country to land near the Moon's South Pole.

---

### 🚀 MANGALYAAN — MARS ORBITER MISSION (MOM)

| Detail | Fact |
|--------|------|
| **Mission Name** | Mars Orbiter Mission (MOM) / Mangalyaan |
| **Launch Year** | 2013 |
| **Reached Mars** | 2014 (September 24, 2014) |
| **India's record** | 1st country to reach Mars in FIRST attempt |
| **India's record 2** | Asia's first successful Mars mission |
| **Cost** | ₹450 crore (~$74 million) — cheapest Mars mission |
| **Launch Vehicle** | PSLV-C25 |
| **Status** | Lost contact in 2022 (battery/solar power issue) |

---

### ☀️ ADITYA-L1 — SUN MISSION

| Detail | Fact |
|--------|------|
| **Mission** | India's first solar mission |
| **Launch** | September 2, 2023 |
| **Destination** | L1 (Lagrange Point 1) between Earth and Sun |
| **L1 Distance** | 1.5 million km from Earth |
| **Reached L1** | January 6, 2024 |
| **Purpose** | Study Sun's corona, solar wind, space weather |
| **Instrument** | VELC (Visible Emission Line Coronagraph) — key instrument |
| **Launch Vehicle** | PSLV-C57 |

**KEY FACT:** L1 Lagrange point allows uninterrupted view of the Sun. India is one of few countries with a dedicated solar mission.

---

### 🌟 ASTROSAT — India's Space Observatory

- India's FIRST dedicated multi-wavelength space observatory
- Launched: **September 28, 2015** by PSLV-C30
- Studies stars, galaxies in UV, X-ray, optical wavelengths simultaneously
- Similar to Hubble Space Telescope concept

---

### 🌍 RECENT ISRO MISSIONS (2023–2024)

| Mission | Year | Significance |
|---------|------|--------------|
| **Chandrayaan-3** | July-Aug 2023 | Moon South Pole landing |
| **Aditya-L1** | Sept 2023 | Solar mission to L1 |
| **XPoSat** | Jan 2024 | X-ray polarimetry; 2nd such mission globally after NASA's |
| **INSAT-3DS** | Feb 2024 | Meteorological satellite; weather forecasting |
| **RLV-TD** | 2023 | Reusable Launch Vehicle Technology Demonstrator |

---

## 📖 GS SECTION 4: IMPORTANT SATELLITES

### Communication Satellites — INSAT Series
- INSAT = Indian National Satellite System
- Joint venture: DoS, DoT, IMD, All India Radio, Doordarshan
- Purpose: Telecommunications, TV broadcasting, weather forecasting

### Earth Observation — IRS Series
- IRS = Indian Remote Sensing satellite
- Used for: Agriculture, water resources, forestry, disaster management
- Operated through PSLV

### Navigation — NavIC (IRNSS)
- NavIC = Navigation with Indian Constellation
- India's own GPS system (like USA's GPS, Russia's GLONASS)
- 7 satellites (3 geostationary + 4 geosynchronous)
- Coverage: India and 1500 km around it
- Launched by: PSLV series

---

## 📖 GS SECTION 5: INDIA'S SPACE ACHIEVEMENTS — FIRSTS & RECORDS

| Achievement | Year | Detail |
|-------------|------|--------|
| First Indian in space | 1984 | Rakesh Sharma, Soyuz T-11 |
| First satellite launch | 1975 | Aryabhata (by USSR rocket) |
| First indigenous launch | 1980 | Rohini satellite via SLV-3 |
| First Mars mission success | 2014 | MOM/Mangalyaan |
| First Moon South Pole landing | 2023 | Chandrayaan-3 |
| First solar mission | 2023 | Aditya-L1 |
| 100th PSLV mission | 2023 | PSLV milestone |
| Record satellites in one launch | 2017 | 104 satellites in one go (PSLV-C37) |

---

## 📖 GS SECTION 6: GAGANYAAN — INDIA'S CREWED SPACE MISSION

```
GAGANYAAN MISSION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Objective: First Indian Human Spaceflight Mission
Target:    3 Indian astronauts (Vyomanauts) to orbit Earth
Duration:  3 days in Low Earth Orbit (400 km altitude)
Vehicle:   LVM3 (GSLV Mk III)
Crew Module: Returns to Bay of Bengal

Vyomanauts selected (IAF pilots):
1. Prashanth Balakrishnan Nair
2. Angad Pratap
3. Ajit Krishnan
4. Shubhanshu Shukla

Test flights: TV-D1 abort test (2023) — SUCCESS
Uncrewed test (Gaganyaan-G1) planned before human mission
```

---

## 📖 GS SECTION 7: SPACE CONCEPTS — EXAM ESSENTIALS

### Types of Orbits

```
LEO (Low Earth Orbit):     160–2000 km      → ISS, remote sensing
MEO (Medium Earth Orbit):  2000–35786 km    → GPS satellites
GEO (Geostationary Orbit): 35786 km (fixed) → TV, weather, communication
SSO (Sun-Synchronous Orbit): Polar orbit    → Remote sensing, mapping
```

**Why GEO = 35,786 km?**
At this height, satellite orbital period = 24 hours = Earth's rotation period → appears stationary from Earth.

### Important Space Science Facts

- **Apogee** = Farthest point from Earth in orbit
- **Perigee** = Nearest point to Earth in orbit
- **Escape Velocity from Earth** = 11.2 km/s
- **1st Artificial Satellite** = Sputnik-1 (USSR, 1957)
- **1st Human in Space** = Yuri Gagarin (USSR, April 12, 1961)
- **1st on Moon** = Neil Armstrong (USA, July 20, 1969)
- **ISS** = International Space Station; 400 km altitude; completed in 2011

---

## 📖 GS SECTION 8: INTERNATIONAL SPACE AGENCIES

| Agency | Country | Full Form |
|--------|---------|-----------|
| **NASA** | USA | National Aeronautics & Space Administration |
| **ISRO** | India | Indian Space Research Organisation |
| **ESA** | Europe | European Space Agency |
| **ROSCOSMOS** | Russia | Russian Space Agency |
| **CNSA** | China | China National Space Administration |
| **JAXA** | Japan | Japan Aerospace Exploration Agency |
| **CSA** | Canada | Canadian Space Agency |

---

## 📖 GS SECTION 9: SCIENCE & TECHNOLOGY — ADDITIONAL GK

### Nuclear Missions / BARC
- **BARC** = Bhabha Atomic Research Centre, Mumbai
- Founded by: Dr. Homi J. Bhabha (Father of Indian Nuclear Programme)
- India's nuclear tests: **Pokhran-I (1974)** — "Smiling Buddha" and **Pokhran-II (1998)** — "Operation Shakti"

### Defence Research
- **DRDO** = Defence Research & Development Organisation, HQ: New Delhi
- **HAL** = Hindustan Aeronautics Limited, HQ: Bengaluru
- HAL Tejas = India's indigenous Light Combat Aircraft (LCA)

### Important Scientific Institutions

| Institution | Location | Focus |
|-------------|----------|-------|
| ISRO | Bengaluru | Space research |
| BARC | Mumbai | Nuclear research |
| DRDO | New Delhi | Defence technology |
| CSIR | New Delhi | Scientific & industrial research |
| ICMR | New Delhi | Medical research |
| ICAR | New Delhi | Agricultural research |
| TIFR | Mumbai | Fundamental research |
| IISc | Bengaluru | Science & engineering |

---

## 📖 GS SECTION 10: BIHAR GK CONNECTION — SCIENCE & SPACE

- **Bihar Science Centre** — Located at Patna, promotes science awareness
- **Aryabhatta** — Born in Bihar (ancient Pataliputra = modern Patna); India's first satellite named after him
- **Nalanda University** — Ancient center of learning in Bihar; had astronomers and mathematicians
- Vikram Sarabhai Space Centre (VSSC) — located in Thiruvananthapuram; designs rockets

---

# ═══════════════════════════════════════════
# 📝 GS PRACTICE QUESTIONS — 25 MCQs
## (Answers at the END of the document)
# ═══════════════════════════════════════════

---

**Q26.** ISRO (Indian Space Research Organisation) was founded in which year?

(A) 1962
(B) 1969
(C) 1975
(D) More than one of the above
(E) None of the above

---

**Q27.** Who is known as the "Father of the Indian Space Programme"?

(A) A.P.J. Abdul Kalam
(B) Homi J. Bhabha
(C) Vikram Sarabhai
(D) More than one of the above
(E) None of the above

---

**Q28.** India's Chandrayaan-3 successfully landed near which point on the Moon?

(A) Apollo Basin
(B) Sea of Tranquility
(C) Shiv Shakti Point (near South Pole)
(D) More than one of the above
(E) None of the above

---

**Q29.** India was the FIRST country in the world to achieve which distinction with Chandrayaan-3?

(A) First country to land on the Moon
(B) First country to land near the Moon's South Pole
(C) First country to send an astronaut to the Moon
(D) More than one of the above
(E) None of the above

---

**Q30.** Mars Orbiter Mission (MOM) / Mangalyaan was India's first Mars mission. Which launch vehicle was used?

(A) GSLV Mk III
(B) PSLV-C25
(C) LVM3
(D) More than one of the above
(E) None of the above

---

**Q31.** India became the first country to successfully reach Mars on the FIRST attempt. In which year did Mangalyaan reach Mars?

(A) 2013
(B) 2015
(C) 2014
(D) More than one of the above
(E) None of the above

---

**Q32.** Aditya-L1, India's first solar mission, was launched to study the Sun from which Lagrange point?

(A) L2 (behind Earth from Sun)
(B) L4 (60° ahead of Earth)
(C) L1 (between Earth and Sun, 1.5 million km from Earth)
(D) More than one of the above
(E) None of the above

---

**Q33.** Which launch vehicle is considered the "Workhorse of ISRO" due to its high reliability and success rate?

(A) GSLV Mk III
(B) SLV
(C) PSLV (Polar Satellite Launch Vehicle)
(D) More than one of the above
(E) None of the above

---

**Q34.** In 2017, ISRO set a world record by launching how many satellites in a single mission (PSLV-C37)?

(A) 54
(B) 83
(C) 104
(D) More than one of the above
(E) None of the above

---

**Q35.** The headquarters of ISRO is located in:

(A) Mumbai
(B) New Delhi
(C) Bengaluru (Bangalore)
(D) More than one of the above
(E) None of the above

---

**Q36.** Gaganyaan is India's:

(A) First Mars exploration mission
(B) First human spaceflight programme
(C) First solar observation mission
(D) More than one of the above
(E) None of the above

---

**Q37.** India's first satellite "Aryabhata" was launched in which year?

(A) 1980
(B) 1969
(C) 1975
(D) More than one of the above
(E) None of the above

---

**Q38.** The first Indian to travel to space was:

(A) Sunita Williams
(B) Kalpana Chawla
(C) Rakesh Sharma
(D) More than one of the above
(E) None of the above

---

**Q39.** NavIC (Navigation with Indian Constellation) is India's own:

(A) Weather forecasting system
(B) Regional navigation satellite system (like GPS)
(C) Remote sensing satellite network
(D) More than one of the above
(E) None of the above

---

**Q40.** Astrosat, India's first dedicated space observatory, was launched in which year?

(A) 2008
(B) 2019
(C) 2015
(D) More than one of the above
(E) None of the above

---

**Q41.** What is the orbital altitude of a Geostationary satellite?

(A) 400 km
(B) 2000 km
(C) 35,786 km
(D) More than one of the above
(E) None of the above

---

**Q42.** Chandrayaan-1 (2008) made a major scientific discovery. What was it?

(A) Found evidence of ancient volcanoes on Moon
(B) Confirmed the presence of water on the Moon
(C) First soft landing on the Moon by India
(D) More than one of the above
(E) None of the above

---

**Q43.** BARC (Bhabha Atomic Research Centre) is located in which city?

(A) New Delhi
(B) Bengaluru
(C) Mumbai
(D) More than one of the above
(E) None of the above

---

**Q44.** India conducted its first nuclear test (Operation Smiling Buddha / Pokhran-I) in which year?

(A) 1998
(B) 1971
(C) 1974
(D) More than one of the above
(E) None of the above

---

**Q45.** The ancient Indian mathematician and astronomer Aryabhata, after whom India's first satellite was named, was born in:

(A) Pataliputra (modern-day Patna, Bihar)
(B) Varanasi
(C) Ujjain
(D) More than one of the above
(E) None of the above

---

**Q46.** XPoSat, launched by ISRO in January 2024, is meant to study:

(A) Solar wind patterns
(B) X-ray polarization of cosmic sources
(C) Earth's magnetic field
(D) More than one of the above
(E) None of the above

---

**Q47.** Which agency developed India's indigenous Light Combat Aircraft "Tejas"?

(A) ISRO
(B) BARC
(C) HAL (Hindustan Aeronautics Limited)
(D) More than one of the above
(E) None of the above

---

**Q48.** The "escape velocity" needed to escape Earth's gravitational field is approximately:

(A) 7.9 km/s
(B) 3 km/s
(C) 11.2 km/s
(D) More than one of the above
(E) None of the above

---

**Q49.** Chandrayaan-3 was launched using which launch vehicle?

(A) PSLV-C57
(B) GSLV Mk II
(C) LVM3 (formerly GSLV Mk III)
(D) More than one of the above
(E) None of the above

---

**Q50.** India's second nuclear test (Operation Shakti / Pokhran-II) happened in which year?

(A) 1995
(B) 2001
(C) 1998
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════════
# 🔑 ANSWER KEY
## (Attempt ALL questions BEFORE looking here!)
# ═══════════════════════════════════════════

---

## ✅ CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| **Q1** | **(C)** | Big-O = upper bound of WORST-CASE running time. NOT average, NOT best. |
| **Q2** | **(E)** | Binary Search = O(log n). None of the given options A/B/C was log n, so answer is E. |
| **Q3** | **(C)** | Merge Sort = O(n log n) in ALL cases (best, average, worst). Quick Sort varies — O(n²) worst. |
| **Q4** | **(E)** | Infix to Postfix = O(N) linear time. None of options A/B/C = O(n). Answer is E = None. |
| **Q5** | **(E)** | Quick Sort worst case = O(n²). Options given were O(n log n), O(n), O(log n) — none correct. |
| **Q6** | **(C)** | Radix Sort is NOT comparison-based. Merge Sort and Heap Sort both are comparison-based. |
| **Q7** | **(C)** | Two nested loops each running n times → O(n) × O(n) = O(n²). |
| **Q8** | **(A)** | Correct order: O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ). |
| **Q9** | **(B)** | Binary Search requires a SORTED array. No requirement on size, duplicates. |
| **Q10** | **(C)** | T(n) = 2T(n/2) + O(n) is the recurrence of Merge Sort, solved to O(n log n). |
| **Q11** | **(C)** | Merge Sort uses extra array of size n → O(n) space. It is NOT in-place. |
| **Q12** | **(C)** | Bubble Sort is STABLE (equal elements maintain order) AND IN-PLACE (O(1) space). Merge Sort is stable but NOT in-place. Quick Sort is in-place but NOT stable. |
| **Q13** | **(C)** | Θ (Big-Theta) = tight bound. Both upper AND lower bounds are the same. O = upper. Ω = lower. |
| **Q14** | **(C)** | Array access by index = O(1) — constant time due to contiguous memory. |
| **Q15** | **(C)** | Selection Sort = O(n²) in ALL cases — it always scans the unsorted portion. No O(n) best case. |
| **Q16** | **(D)** | ALL three statements are TRUE: constants dropped, lower terms dropped, log base doesn't matter. So answer = D (More than one). |
| **Q17** | **(C)** | Stack Push = O(1), Pop = O(1). Both are constant time operations. |
| **Q18** | **(C)** | Quick Sort is O(n²) when pivot = smallest/largest (sorted or reverse-sorted array). |
| **Q19** | **(C)** | Iterative Binary Search only uses 3 variables (low, high, mid) → O(1) space. |
| **Q20** | **(C)** | Merge Sort requires O(n) temporary array → NOT in-place. Quick Sort and Heap Sort are in-place. |
| **Q21** | **(C)** | Tower of Hanoi with n discs requires 2ⁿ-1 moves → O(2ⁿ) exponential. |
| **Q22** | **(C)** | i doubles each iteration (×2). Number of iterations = log₂(n) → O(log n). |
| **Q23** | **(B)** | For UNSORTED array, only Linear Search O(n) works. Binary Search requires sorted. |
| **Q24** | **(C)** | Optimized Bubble Sort with flag check: if no swaps in a pass → already sorted → stop. Best case O(n). |
| **Q25** | **(C)** | T(n) = T(n/2) + O(1) → Master Theorem Case 2 → T(n) = Θ(log n). |

---

## ✅ GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| **Q26** | **(B)** | ISRO founded in 1969 (August 15, 1969). Note: INCOSPAR was formed 1962, but ISRO in 1969. |
| **Q27** | **(C)** | Dr. Vikram Sarabhai = Father of Indian Space Programme. A.P.J. Abdul Kalam = Missile Man. Homi Bhabha = Father of Nuclear Programme. |
| **Q28** | **(C)** | Chandrayaan-3 Vikram lander touched down at "Shiv Shakti Point" near the Moon's South Pole. |
| **Q29** | **(B)** | India is the FIRST country to land near the Moon's South Pole. USA, Russia, China had landed on Moon but NOT at South Pole. |
| **Q30** | **(B)** | Mangalyaan was launched by PSLV-C25 (not GSLV). This is a common TRAP — people assume it needed GSLV. |
| **Q31** | **(C)** | Mangalyaan reached Mars on September 24, 2014, exactly 300 days after launch in November 2013. |
| **Q32** | **(C)** | Aditya-L1 is at Lagrange Point L1 — between Earth and Sun, 1.5 million km from Earth. L2 is on the other side (used by James Webb). |
| **Q33** | **(C)** | PSLV is the "Workhorse of ISRO" — most used and reliable. 50+ successful missions. |
| **Q34** | **(C)** | PSLV-C37 launched 104 satellites in a single mission — world record at that time. |
| **Q35** | **(C)** | ISRO HQ is in Bengaluru (Bangalore), Karnataka. |
| **Q36** | **(B)** | Gaganyaan = India's first human spaceflight programme. Vyomanauts will orbit Earth for 3 days. |
| **Q37** | **(C)** | Aryabhata satellite launched in 1975 (by USSR Kosmos-3M rocket, as India had no rocket then). |
| **Q38** | **(C)** | Rakesh Sharma (IAF) was first Indian in space (1984, Soviet Soyuz T-11). Kalpana Chawla was Indian-American on NASA missions. |
| **Q39** | **(B)** | NavIC = India's Regional Navigation Satellite System. Like GPS (USA), GLONASS (Russia), Galileo (EU). |
| **Q40** | **(C)** | Astrosat launched September 28, 2015 via PSLV-C30. India's first dedicated astronomy satellite. |
| **Q41** | **(C)** | Geostationary orbit = 35,786 km altitude. At this height, orbital period = 24 hours. |
| **Q42** | **(B)** | Chandrayaan-1's Moon Impact Probe (MIP) confirmed water/ice molecules on Moon — major discovery. |
| **Q43** | **(C)** | BARC (Bhabha Atomic Research Centre) is in Mumbai (Trombay area). |
| **Q44** | **(C)** | Pokhran-I / Smiling Buddha = 1974. Pokhran-II / Operation Shakti = 1998. |
| **Q45** | **(A)** | Aryabhata was born in Kusumapura / Pataliputra = modern Patna (Bihar). BIHAR CONNECTION! |
| **Q46** | **(B)** | XPoSat studies X-ray polarization of cosmic bodies like black holes, neutron stars. 2nd such mission globally (NASA's IXPE was 1st). |
| **Q47** | **(C)** | HAL (Hindustan Aeronautics Limited), HQ Bengaluru, developed Tejas LCA. Not ISRO or BARC. |
| **Q48** | **(C)** | Escape velocity from Earth = 11.2 km/s. Orbital velocity (for LEO) = 7.9 km/s. Common TRAP — know both! |
| **Q49** | **(C)** | Chandrayaan-3 launched by LVM3-M4 (LVM3 is former GSLV Mk III). Note: PSLV-C57 = Aditya-L1. |
| **Q50** | **(C)** | Pokhran-II (Operation Shakti) = 1998, under PM Atal Bihari Vajpayee. 5 tests conducted. |

---

# ═══════════════════════════════════════════
# 🏆 DAY 29 — TOPPER'S QUICK REVISION CARD
# ═══════════════════════════════════════════

## ⚡ CS — 10 MUST-REMEMBER FACTS

1. **Big-O** = UPPER BOUND of WORST-CASE time → NOT average case
2. **Complexity order:** O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ)
3. **Binary Search** = O(log n) — requires SORTED array
4. **Merge Sort** = O(n log n) ALL cases, STABLE, NOT in-place (O(n) space)
5. **Quick Sort** = O(n²) worst case (sorted input with bad pivot)
6. **Selection Sort** = O(n²) in ALL cases (no exception)
7. **Infix → Postfix** = O(n) time using STACK
8. **Stack/Queue ops** = O(1) — Push, Pop, Enqueue, Dequeue
9. **T(n) = 2T(n/2) + O(n)** → Merge Sort → O(n log n)
10. **T(n) = T(n/2) + O(1)** → Binary Search → O(log n)

## ⚡ GS — 10 MUST-REMEMBER FACTS

1. **ISRO founded:** 1969 | HQ: **Bengaluru** | Father: **Vikram Sarabhai**
2. **Chandrayaan-3:** 2023 | Landing site: **Shiv Shakti Point** | 1st at Moon's South Pole
3. **Mangalyaan (MOM):** Reached Mars **2014** | 1st country in FIRST attempt | Launch: **PSLV-C25**
4. **Aditya-L1:** 2023 Solar mission | Destination: **L1 Lagrange Point** | 1.5 million km from Earth
5. **PSLV** = Workhorse of ISRO | **PSLV-C37** = 104 satellites world record (2017)
6. **Aryabhata (satellite):** 1975 | First Indian satellite | Named after Bihar's ancient mathematician
7. **Rakesh Sharma:** First Indian in space (1984) | Soviet mission Soyuz T-11
8. **NavIC** = India's GPS | 7 satellites | Covers India + 1500 km
9. **Gaganyaan** = India's first human spaceflight | LVM3 rocket | 3 days in LEO
10. **Escape Velocity = 11.2 km/s** | Orbital Velocity = 7.9 km/s (for LEO)

---

## 📊 Day 29 Self-Assessment

After completing practice questions, rate yourself:

| Category | Questions | My Score | Target |
|----------|-----------|----------|--------|
| CS Basics (Q1-Q8) | 8 | /8 | 7+ |
| CS Advanced (Q9-Q25) | 17 | /17 | 15+ |
| GS ISRO (Q26-Q40) | 15 | /15 | 13+ |
| GS Science & Tech (Q41-Q50) | 10 | /10 | 9+ |
| **TOTAL** | **50** | **/50** | **44+** |

> **Score 44+/50 = Topper Zone** 🏆
> **Score 38-43 = Good, review wrong answers**
> **Score below 38 = Re-read concept section, redo questions tomorrow**

---

## 📝 Tonight's 5-Bullet Summary (Write in Your Notebook!)

1. Big-O = ________ bound of ________ case (fill in blanks from memory)
2. Binary Search complexity = ________, requires ________
3. Merge Sort: Time = ________, Space = ________, Stable? ________
4. Chandrayaan-3 landing site = ________, year = ________
5. ISRO full form = ________, HQ = ________, founded = ________

---

*Day 29 Complete ✅ | Tomorrow: Day 30 — Sorting Algorithms (Bubble, Selection, Insertion)*
*Keep going — you are 29/170 steps closer to TOPPER rank!* 🎯
