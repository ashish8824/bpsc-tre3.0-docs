# 📅 BPSC TRE 4.0 — DAY 29 COMPLETE STUDY MODULE
### Time Complexity & Big-O Notation + Current Affairs: ISRO Missions
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Time Complexity & Big-O Notation — Core Concepts, Notations, Algorithm Analysis
> - Afternoon (1 hr): Current Affairs — ISRO Missions & India's Space Journey
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Time Complexity & Big-O Notation — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is Time Complexity?

### Real-Life Analogy — The Library Search:

Imagine you have to find a **specific book** in a library.

**Method 1 — Small library (10 books, unsorted):**
You check every single book one by one until you find it.
→ More books = more time. Time grows with size.

**Method 2 — Large library (10,000 books, sorted alphabetically):**
You open to the MIDDLE, check if you need the left half or right half, eliminate half each time.
→ Even with 10,000 books, you find it in ~14 steps!

This difference in *how time grows with input size* is called **Time Complexity**.

### Formal Definition:
**Time Complexity** is a measure of the **amount of time an algorithm takes to run** as a function of the **size of its input (n)**.

> ⚠️ IMPORTANT: Time complexity does NOT measure actual clock time (seconds/milliseconds).
> It measures **how the number of operations grows** as input size n increases.
> This makes it machine-independent and universally comparable.

### Why Is It Important?

```
Imagine sorting 1,000,000 records:

Algorithm A (O(n²)):   1,000,000² = 10¹² operations → ~11.5 days on a fast computer!
Algorithm B (O(n log n)): 1,000,000 × 20 = 20,000,000 ops → ~0.02 seconds!

Same data. Same computer. DRASTICALLY different results.
This is WHY time complexity matters.
```

### 🎯 PYQ FACT: Time complexity is a function of INPUT SIZE (n), not actual time.

---

## 🔷 SECTION 2: Best Case, Average Case, Worst Case

Every algorithm can behave differently depending on the **nature of the input**.

### Example: Searching for a value in an array [5, 3, 8, 1, 9, 2, 7]

```
SCENARIO:  Find value 'x' in array of n elements using Linear Search

BEST CASE:    x = 5  (first element!)
              → Only 1 comparison needed
              → Time = Ω(1)

AVERAGE CASE: x = somewhere in the middle
              → Approximately n/2 comparisons
              → Time = Θ(n/2) ≈ Θ(n)

WORST CASE:   x = 7  (last element) OR x is not in array
              → n comparisons needed
              → Time = O(n)
```

### Diagram — Three Cases:

```
Input Array: [5, 3, 8, 1, 9, 2, 7]   Target: ?

Best Case:   [X, _, _, _, _, _, _]    Found at position 1  → 1 step
             ^
             Found immediately!

Average Case:[_, _, _, X, _, _, _]    Found at position 4  → n/2 steps
                       ^
                       Middle

Worst Case:  [_, _, _, _, _, _, X]    Found at last position → n steps
                                ^
                                OR not found at all!
```

### Summary Table:

| Case | When | Notation | Meaning |
|------|------|----------|---------|
| Best Case | Most favorable input | Ω (Big-Omega) | Lower bound |
| Average Case | Random/typical input | Θ (Big-Theta) | Tight bound |
| Worst Case | Most unfavorable input | O (Big-O) | Upper bound |

### 🚨 PYQ TRAP #1: "Big-O = Worst Case" Confusion
> Big-O notation defines an UPPER BOUND — it can describe best, average, OR worst case.
> But by CONVENTION, when we say "Big-O of an algorithm," we almost always mean the worst case.
> Example: Linear Search worst case = O(n). But technically, linear search best case is also O(1) in Big-O terms.
> **EXAM ANSWER: Big-O represents WORST CASE by convention.**

---

## 🔷 SECTION 3: Asymptotic Notations — The Mathematical Language

"Asymptotic" means: what happens as n → ∞ (approaches infinity)?

---

### 📌 BIG-O NOTATION — O (Upper Bound / Worst Case)

**Definition:** f(n) = O(g(n)) means the function f(n) grows **no faster than** g(n).
g(n) is the UPPER BOUND for f(n).

```
Mathematical: f(n) ≤ c × g(n)  for all n ≥ n₀
              (for some constants c > 0 and n₀ > 0)

In simple words: "In the worst case, the algorithm takes AT MOST this much time."

Example:
  f(n) = 3n + 5
  We say: f(n) = O(n)
  
  Why? 3n + 5 ≤ 4n  for all n ≥ 5  (just use c=4, n₀=5)
  The 3 (coefficient) and 5 (constant) are IGNORED.
  Only the DOMINANT TERM matters → n
```

**Visual Representation:**
```
Time
 |                    /  ← c·g(n) = upper boundary
 |                   /  
 |               ---/   ← f(n) = actual function
 |           ---/
 |       ---/
 +-------------------> n
 
 f(n) always stays BELOW c·g(n) after some point n₀
 This is what Big-O means!
```

---

### 📌 BIG-OMEGA NOTATION — Ω (Lower Bound / Best Case)

**Definition:** f(n) = Ω(g(n)) means f(n) grows **at least as fast as** g(n).
g(n) is the LOWER BOUND.

```
Mathematical: f(n) ≥ c × g(n)  for all n ≥ n₀

In simple words: "In the BEST case, the algorithm takes AT LEAST this much time."
                 "The algorithm CANNOT do better than this."

Example:
  f(n) = 3n + 5
  We say: f(n) = Ω(n)
  
  Why? 3n + 5 ≥ 1×n  for all n ≥ 1
  The function grows AT LEAST as fast as n.
```

**Visual Representation:**
```
Time
 |               ---    ← f(n) = actual function
 |           ---/
 |       ---/
 |  /---/              ← c·g(n) = lower boundary
 | /
 +-------------------> n
 
 f(n) always stays ABOVE c·g(n) after some point n₀
```

---

### 📌 BIG-THETA NOTATION — Θ (Tight Bound / Both Bounds)

**Definition:** f(n) = Θ(g(n)) means f(n) grows at the **same rate** as g(n).
g(n) is both the upper AND lower bound.

```
Mathematical: c₁ × g(n) ≤ f(n) ≤ c₂ × g(n)  for all n ≥ n₀

In simple words: "The algorithm ALWAYS takes approximately this much time — in all cases."
                 f(n) is 'sandwiched' between c₁g(n) and c₂g(n)

Example:
  f(n) = 3n + 5
  We say: f(n) = Θ(n)
  
  Why? 1×n ≤ 3n+5 ≤ 4n  for all n ≥ 5
  It's bounded from BOTH sides.
```

**Visual Representation:**
```
Time
 |                /   ← c₂·g(n) = upper boundary
 |            ---/    ← f(n) = actual function (sandwiched!)
 |        ---/ /
 |    ---/    /       ← c₁·g(n) = lower boundary
 |   /
 +-------------------> n
 
 f(n) is 'sandwiched' between the two boundaries — TIGHT BOUND!
```

---

### Three Notations — Side-by-Side Comparison:

```
ANALOGY using SPEED:

Big-O (O):      "I will arrive in AT MOST 2 hours"   → Upper bound, optimistic guarantee
Big-Omega (Ω):  "I will arrive in AT LEAST 30 min"   → Lower bound, pessimistic guarantee
Big-Theta (Θ):  "I will arrive in 1 to 1.5 hours"    → Tight, realistic estimate

MATHEMATICAL RELATIONSHIP:
  If f(n) = O(g(n)) AND f(n) = Ω(g(n))
  Then f(n) = Θ(g(n))
  
  Θ is the MOST PRECISE notation — it captures both bounds simultaneously.
```

| Notation | Type | Meaning | Memory Trick |
|----------|------|---------|--------------|
| O (Big-O) | Upper bound | At most / no worse than | **O**h no, worst case! |
| Ω (Big-Omega) | Lower bound | At least / no better than | **Ω**mega minimum |
| Θ (Big-Theta) | Tight bound | Exactly / same rate | **Θ**ight squeeze |

### 🚨 PYQ TRAP #2: Which notation for which case?
```
If an algorithm's complexity is SAME in all cases (best, avg, worst):
  → Use Θ (tight bound) — e.g., Θ(n) for traversing an array

If best ≠ worst case:
  → Use Ω for best, O for worst, Θ for average

Quick Sort: Best = Ω(n log n), Average = Θ(n log n), Worst = O(n²)
Merge Sort: ALL cases = Θ(n log n)  ← Consistent, so Θ works!
```

---

## 🔷 SECTION 4: Common Time Complexities — From Fastest to Slowest

### The Complexity Hierarchy (ORDER OF GROWTH):

```
FASTEST                                                          SLOWEST
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!)

THINK OF IT AS A RACE:
  O(1)      — Usain Bolt (always instant)
  O(log n)  — Olympic sprinter (nearly instant, barely affected by n)
  O(n)      — Average jogger (grows steadily)
  O(n log n)— Slightly tired jogger
  O(n²)     — Someone walking backward
  O(2ⁿ)    — Someone crawling
  O(n!)     — Someone asleep
```

---

### O(1) — CONSTANT TIME

**Meaning:** The algorithm takes the SAME amount of time regardless of input size.

```
EXAMPLE: Access array element by index
  arr[0] → instant   (n = 10)
  arr[0] → instant   (n = 1,000,000)
  The index directly gives the memory address!

CODE EXAMPLE:
  int x = arr[5];     // Always exactly 1 operation
  return arr[0];      // Always exactly 1 operation

MORE EXAMPLES OF O(1):
  - Push/Pop on a Stack (array or linked list with pointer)
  - Insertion at beginning of Singly Linked List
  - Checking if a number is odd/even
  - Hash table lookup (average case)
  - Finding min/max when pointer is maintained
```

**Growth Rate:**
```
n =    10 → Steps = 1
n =   100 → Steps = 1
n =  1000 → Steps = 1
n = 10000 → Steps = 1
→ FLAT LINE — completely unaffected by n
```

---

### O(log n) — LOGARITHMIC TIME

**Meaning:** Each step HALVES (or reduces by a factor) the remaining work.
The problem size shrinks by a CONSTANT FACTOR each step.

```
EXAMPLE: Binary Search on sorted array [1,3,5,7,9,11,13,15]
  Find 11:
  
  Step 1: Check middle = 7.  11 > 7  → Eliminate left half
          Remaining: [9, 11, 13, 15]  (4 elements from 8)
  
  Step 2: Check middle = 11. Found!
  
  For n = 8 elements: only 3 steps needed! (log₂8 = 3)
  For n = 1,000,000:  only 20 steps! (log₂1,000,000 ≈ 20)

This is the POWER of logarithmic growth!
```

**Why log BASE 2?**
```
In most CS problems, we HALVE the input each step → base 2 logarithm
2^steps = n
steps = log₂(n)

n = 8:        2³ = 8    → log₂8 = 3 steps
n = 1024:     2¹⁰ = 1024 → log₂1024 = 10 steps
n = 1,000,000: 2²⁰ ≈ 10⁶  → ~20 steps
```

**Growth Rate:**
```
n =         8 → Steps = 3
n =        64 → Steps = 6
n =      1024 → Steps = 10
n = 1,000,000 → Steps = 20
→ GROWS VERY SLOWLY — nearly flat!
```

---

### O(n) — LINEAR TIME

**Meaning:** Time grows proportionally to input size. Double the input → double the time.

```
EXAMPLE: Linear Search — find value x in unsorted array
  For n = 10: up to 10 comparisons
  For n = 100: up to 100 comparisons
  
CODE EXAMPLE:
  for (int i = 0; i < n; i++) {     // n iterations
      if (arr[i] == target) return i;
  }

OTHER O(n) EXAMPLES:
  - Traversing an array/linked list
  - Finding max/min in unsorted array
  - Counting elements matching a condition
  - Infix to Postfix conversion (each character processed once)
  - Printing all elements
```

**Growth Rate:**
```
n =    10 → Steps = 10
n =   100 → Steps = 100
n =  1000 → Steps = 1000
→ STRAIGHT LINE — proportional growth
```

---

### O(n log n) — LINEARITHMIC TIME

**Meaning:** Slightly worse than linear, but much better than quadratic.
Typical of efficient sorting algorithms that use divide and conquer.

```
EXAMPLE: Merge Sort
  Step 1: DIVIDE array into halves (log n levels of division)
  Step 2: MERGE sorted halves (O(n) work at each level)
  
  Total: n × log n operations

  For n = 1,000,000:
    O(n²) = 10¹² operations (~hours)
    O(n log n) = 20,000,000 operations (~milliseconds!)
  
VISUAL — Merge Sort Tree (n = 8):
            [8 elements]           Level 0 (merge 8)
           /             \
      [4 elem]         [4 elem]    Level 1 (merge 4+4)
      /     \          /     \
  [2 elem] [2 elem] [2 elem] [2 elem]  Level 2
  /\ /\   /\ /\   /\ /\   /\ /\
 1  1 ... (leaves)                Level 3

3 levels = log₂8 = 3
Each level does n = 8 operations
Total = 3 × 8 = 24 = n log n operations
```

**OTHER O(n log n) EXAMPLES:**
```
- Merge Sort
- Heap Sort
- Quick Sort (average case)
- FFT (Fast Fourier Transform)
- Some tree operations
```

---

### O(n²) — QUADRATIC TIME

**Meaning:** Time grows as the SQUARE of input size. Double the input → 4× the time.
Typical of nested loops where each loop runs n times.

```
EXAMPLE: Bubble Sort
  
  CODE:
  for (int i = 0; i < n; i++) {      // Outer loop: n times
      for (int j = 0; j < n-1; j++) { // Inner loop: n-1 times
          if (arr[j] > arr[j+1]) swap(arr[j], arr[j+1]);
      }
  }
  
  For n = 5:   5 × 5 = 25 comparisons
  For n = 100: 100 × 100 = 10,000 comparisons
  For n = 1000: 1000 × 1000 = 1,000,000 comparisons!

VISUAL — Nested Loop Pattern:
  Outer i=0: Inner runs n times: × × × × ×
  Outer i=1: Inner runs n times: × × × × ×
  Outer i=2: Inner runs n times: × × × × ×
  ...
  Total = n × n = n² operations
```

**OTHER O(n²) EXAMPLES:**
```
- Bubble Sort, Selection Sort, Insertion Sort
- Simple matrix multiplication (naive)
- Checking all pairs in an array
- Finding duplicate elements (brute force)
```

**Growth Rate:**
```
n =  10 → Steps = 100
n = 100 → Steps = 10,000
n = 1000 → Steps = 1,000,000
→ GROWS VERY FAST — curve steepens rapidly
```

---

### O(2ⁿ) — EXPONENTIAL TIME

**Meaning:** Each new element DOUBLES the number of operations.
Extremely slow — impractical for large n.

```
EXAMPLE: Recursive Fibonacci (naive)
  
  fib(n) = fib(n-1) + fib(n-2)
  
  For fib(5):
              fib(5)
            /        \
        fib(4)       fib(3)
       /     \      /     \
    fib(3) fib(2) fib(2) fib(1)
    /   \
  fib(2) fib(1)
  
  Each level DOUBLES the nodes → 2^n total calls

GROWTH:
  n = 10  → 2^10 = 1,024 operations
  n = 30  → 2^30 = 1,073,741,824 (~1 billion!) operations
  n = 50  → 2^50 = 1,125,899,906,842,624 (~quadrillion!) operations
```

**OTHER EXAMPLES:**
```
- Solving Tower of Hanoi: O(2ⁿ)
- Generating all subsets of a set
- Brute-force password cracking
- Some dynamic programming problems (unoptimized)
```

---

### Complexity Comparison Table — The Master Reference:

| Complexity | Name | n=10 | n=100 | n=1000 | Typical Algorithm |
|------------|------|------|-------|--------|-------------------|
| O(1) | Constant | 1 | 1 | 1 | Array index access |
| O(log n) | Logarithmic | 3 | 7 | 10 | Binary Search |
| O(n) | Linear | 10 | 100 | 1,000 | Linear Search, Traversal |
| O(n log n) | Linearithmic | 33 | 664 | 9,966 | Merge Sort, Heap Sort |
| O(n²) | Quadratic | 100 | 10,000 | 1,000,000 | Bubble Sort, Selection Sort |
| O(2ⁿ) | Exponential | 1,024 | 10³⁰ | 10³⁰¹ | Naive Fibonacci, Subset generation |

---

### Growth Curve Visual (ASCII Graph):

```
Operations
    |
10⁶ |                                          *** O(2ⁿ)
    |                                   *****
    |                             *****
10⁴ |                       *****              *** O(n²)
    |               *+*+*+*+
    |       *+*+*+*+                           +++ O(n log n)
10² |   *+*+
    | *                                        *** O(n)
    |.......................................    ... O(log n)
  1 |___________________________________        --- O(1)
    +---+---+---+---+---+---+---+----->
    2   4   8   16  32  64  128       n

Key:
  ---  O(1)       → Flat line
  ...  O(log n)   → Very gentle rise
  *    O(n)       → Straight diagonal
  +    O(n log n) → Slightly curved
  **   O(n²)      → Steep parabola
  ***  O(2ⁿ)      → Rocket launch upward
```

---

## 🔷 SECTION 5: How to Calculate Time Complexity — Step-by-Step Rules

### RULE 1: Count the DOMINANT OPERATION (basic operation)

The operation that is executed most frequently is what we count.
```
For searching → count comparisons
For sorting   → count comparisons + swaps
For arithmetic → count arithmetic operations
```

### RULE 2: Ignore Constants and Lower-Order Terms

```
f(n) = 5n + 3     → O(n)      [drop 5, drop 3]
f(n) = 3n² + 7n   → O(n²)     [drop 3, drop 7n — lower order]
f(n) = 100        → O(1)      [constant]
f(n) = 2n² + 5n + 100 → O(n²) [dominant term = n²]

WHY? Because as n→∞, smaller terms become negligible:
  For n = 1000: 3n² = 3,000,000 vs 7n = 7,000
  The 7n is less than 0.3% of the total — negligible!
```

### RULE 3: Single Loop Analysis

```
for (int i = 0; i < n; i++) {     // runs n times
    operation();                   // O(1) each
}
Total = n × O(1) = O(n)

for (int i = 0; i < n; i += 2) {  // runs n/2 times
    operation();
}
Total = n/2 × O(1) = O(n)         // Drop the constant 1/2!

for (int i = 1; i < n; i *= 2) {  // runs log₂n times
    operation();
}
Total = log n × O(1) = O(log n)   // Multiplication = logarithm!
```

### RULE 4: Nested Loop Analysis

```
for (int i = 0; i < n; i++) {      // n times
    for (int j = 0; j < n; j++) {  // n times EACH outer iteration
        operation();
    }
}
Total = n × n = O(n²)

for (int i = 0; i < n; i++) {
    for (int j = 0; j < i; j++) {  // j < i, not j < n!
        operation();
    }
}
Total = 0 + 1 + 2 + ... + (n-1) = n(n-1)/2 = O(n²)  [still O(n²)!]

for (int i = 0; i < n; i++) {
    for (int j = 0; j < 100; j++) {  // CONSTANT inner loop!
        operation();
    }
}
Total = n × 100 = 100n = O(n)     // Constant × n = O(n)!
```

### RULE 5: Sequential Code — Addition Rule

```
Statement A → O(n)
Statement B → O(n²)
Statement C → O(1)

Total = O(n) + O(n²) + O(1) = O(n²)  [dominant term wins!]

RULE: For SEQUENTIAL code, take the MAXIMUM.
```

### RULE 6: Nested Code — Multiplication Rule

```
Outer loop: O(n)
Inner loop: O(n)
TOGETHER:   O(n) × O(n) = O(n²)

RULE: For NESTED code, MULTIPLY.
```

### Step-by-Step Example — Complete Analysis:

```java
void example(int[] arr, int n) {
    // Block 1: Single statements
    int x = arr[0];          // O(1)
    int y = arr[n-1];        // O(1)
    
    // Block 2: Single loop
    for (int i = 0; i < n; i++) {   // O(n)
        System.out.println(arr[i]);
    }
    
    // Block 3: Nested loops
    for (int i = 0; i < n; i++) {         // O(n)
        for (int j = 0; j < n; j++) {     // O(n)
            System.out.println(arr[i] + arr[j]); // O(1)
        }
    }
}

Analysis:
Block 1: O(1) + O(1) = O(1)
Block 2: O(n)
Block 3: O(n) × O(n) × O(1) = O(n²)

Total = O(1) + O(n) + O(n²)
      = O(n²)     ← Dominant term
```

### 🚨 PYQ TRAP #3: Logarithmic Loops
```
for (int i = 1; i <= n; i *= 2)   → O(log n)   [multiplied by 2 each step]
for (int i = n; i >= 1; i /= 2)   → O(log n)   [divided by 2 each step]
for (int i = 1; i <= n; i *= 3)   → O(log₃ n) = O(log n)  [base doesn't matter!]

KEY INSIGHT: Any base logarithm = O(log n) because log bases differ by a constant.
```

---

## 🔷 SECTION 6: Algorithm Complexity Examples — Exam Focus

### 1. LINEAR SEARCH → O(n)

```
Algorithm: Search for 'key' in arr[0..n-1]
  for i = 0 to n-1:
      if arr[i] == key: return i
  return -1

ANALYSIS:
  Best Case (Ω):    key found at first position → 1 comparison → Ω(1)
  Average Case (Θ): key found at middle → n/2 comparisons → Θ(n)
  Worst Case (O):   key at last position OR not found → n comparisons → O(n)
  
EXAM ANSWER: Time Complexity of Linear Search = O(n)
```

### 2. BINARY SEARCH → O(log n)

```
PRECONDITION: Array MUST be sorted!

Algorithm: Search for 'key' in sorted arr[low..high]
  while low <= high:
      mid = (low + high) / 2
      if arr[mid] == key: return mid
      else if arr[mid] < key: low = mid + 1   // Search right half
      else: high = mid - 1                    // Search left half
  return -1

ANALYSIS:
  Each iteration: HALVES the search space
  Steps = log₂n
  
  Best Case:  O(1) — key found at middle immediately
  Worst Case: O(log n) — key at extreme end or not found
  
VISUALIZATION for n = 16:
  Start: 16 elements
  Step 1: 8 elements remain
  Step 2: 4 elements remain
  Step 3: 2 elements remain
  Step 4: 1 element remains → found or not found
  = 4 steps = log₂16 = 4 ✓

🎯 PYQ FACT: Binary search REQUIRES sorted array. On unsorted → must sort first!
```

### 3. BUBBLE SORT → O(n²)

```
Algorithm: Repeatedly compare adjacent elements and swap if out of order
  for i = 0 to n-1:
      for j = 0 to n-2-i:
          if arr[j] > arr[j+1]: swap(arr[j], arr[j+1])

ANALYSIS:
  Outer loop: n iterations
  Inner loop: n-1, n-2, ..., 1 iterations (decreasing)
  Total comparisons = (n-1) + (n-2) + ... + 1 = n(n-1)/2 ≈ n²/2 = O(n²)
  
  Best Case:  O(n) — with OPTIMIZED version checking if any swap happened
  Worst Case: O(n²) — array sorted in reverse order
  Space:      O(1) — in-place sorting

MEMORY TABLE:
  n = 5:    5×4/2 = 10 comparisons
  n = 10:   10×9/2 = 45 comparisons
  n = 100:  100×99/2 ≈ 5000 comparisons
  n = 1000: ≈ 500,000 comparisons
```

### 4. MERGE SORT → O(n log n)

```
Algorithm: Divide and Conquer
  mergeSort(arr):
      if len(arr) <= 1: return arr
      mid = len(arr) / 2
      left = mergeSort(arr[0..mid])       // Divide
      right = mergeSort(arr[mid+1..end])  // Divide
      return merge(left, right)           // Conquer: O(n) merge

ANALYSIS:
  Number of levels = log₂n (halving each time)
  Work per level = O(n) (merging all elements at each level)
  Total = n × log n = O(n log n)
  
  Best Case:  O(n log n) — always same! (unlike Quick Sort)
  Worst Case: O(n log n) — consistent!
  Space:      O(n) — requires extra array for merging

🎯 PYQ FACT: Merge Sort is STABLE and ALWAYS O(n log n) — not affected by input order!
```

### 5. INFIX TO POSTFIX → O(n)

```
Algorithm: Using a stack
  for each character in infix expression:
      if operand: add to output
      if operator: handle with stack (push/pop based on precedence)
      if '(': push to stack
      if ')': pop until '(' found

ANALYSIS:
  Each character is processed EXACTLY ONCE → n operations
  Each character pushed/popped at most ONCE → O(1) per character
  Total = O(n) × O(1) = O(n)
  
  Space = O(n) for the stack (in worst case, all operators queued)
  
EXAMPLE: A + B * C - D
  n = 9 characters → processes each once → O(9) = O(n)
```

### Algorithm Complexity Quick Reference:

| Algorithm | Best Case | Average Case | Worst Case | Space |
|-----------|-----------|--------------|------------|-------|
| Linear Search | O(1) | O(n) | O(n) | O(1) |
| Binary Search | O(1) | O(log n) | O(log n) | O(1) |
| Bubble Sort | O(n)* | O(n²) | O(n²) | O(1) |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) |
| Infix to Postfix | O(n) | O(n) | O(n) | O(n) |

*Optimized Bubble Sort with early exit flag

### 🚨 PYQ TRAP #4: Quick Sort Worst Case
> Quick Sort worst case O(n²) occurs when the pivot is always the **smallest or largest element** (i.e., on a sorted/reverse-sorted array with naive pivot selection).
> This makes it O(n²) in the worst case — DESPITE being O(n log n) on average.
> That's why Merge Sort is preferred when guaranteed performance is needed.

### 🚨 PYQ TRAP #5: Stability of Sorting Algorithms
```
STABLE sorting algorithms (maintain relative order of equal elements):
  ✅ Merge Sort    → Stable
  ✅ Bubble Sort   → Stable
  ✅ Insertion Sort → Stable
  ❌ Quick Sort    → NOT stable (in standard implementation)
  ❌ Heap Sort     → NOT stable
  ❌ Selection Sort → NOT stable
```

---

## 🔷 SECTION 7: Flowchart for Calculating Time Complexity

```
START
  |
  v
Identify the BASIC OPERATION (what we count: comparisons, swaps, etc.)
  |
  v
Is the code SEQUENTIAL (one after another)?
  |              |
 YES             NO
  |              |
  v              v
Add complexities  Is it NESTED (loop inside loop)?
Take MAXIMUM       |                |
                  YES               NO
                   |                |
                   v                v
             MULTIPLY the     Analyze as
             loop complexities  single structure
                   |
                   v
Does any loop HALVE the input each step?
  |              |
 YES             NO
  |              |
O(log n)      Does loop run n times?
              |              |
             YES             NO (constant)
              |              |
             O(n)           O(1)
  |
  v
Ignore CONSTANTS and LOWER-ORDER terms
  |
  v
RESULT: Time Complexity in Big-O notation
  |
  v
END
```

---

## 🔷 SECTION 8: Common PYQ Patterns and Traps Summary

```
TRAP 1: f(n) = 3n² + 2n + 100 → O(n²)  [drop 3, drop 2n, drop 100]
TRAP 2: Loop with i *= 2      → O(log n) [NOT O(n)!]
TRAP 3: Nested loops (both n) → O(n²)   [NOT O(2n)!]
TRAP 4: Loop with i *= 2, i *= 2 (two such) nested → O(log n × log n) = O(log²n)
TRAP 5: Constants inside: O(n + 100) = O(n), NOT O(n+100)
TRAP 6: O(n) + O(log n) = O(n)  [take dominant]
TRAP 7: Binary Search = O(log n) ALWAYS needs SORTED input
TRAP 8: Merge Sort space = O(n), Quick Sort space = O(log n) — space matters!
TRAP 9: Big-O (O) ≠ always worst case — it's upper bound; convention = worst case
TRAP 10: log₂n and log₃n are BOTH O(log n) — base doesn't matter in Big-O!
```

---

# PART 2: GENERAL STUDIES
## 🚀 Current Affairs — ISRO Missions: India's Space Journey

---

## 🔷 SECTION 1: Introduction to ISRO

```
ISRO = Indian Space Research Organisation
Founded: 15 August 1969
Headquarters: Bengaluru, Karnataka
Current Chairman (as of 2024): S. Somanath
                               (Earlier: K. Sivan, before him A.S. Kiran Kumar)
Parent Ministry: Department of Space, Government of India
Main Launch Centre: Satish Dhawan Space Centre (SDSC), Sriharikota, Andhra Pradesh
Liquid Propulsion: LPSC, Thiruvananthapuram
Space Applications: SAC, Ahmedabad
Remote Sensing: NRSC, Hyderabad
```

### 🎯 PYQ FACT: ISRO was established on 15 August 1969 by Vikram Sarabhai, the "Father of India's Space Programme."

---

## 🔷 SECTION 2: India's Major Launch Vehicles

| Vehicle | Full Form | Purpose | Payload (LEO) |
|---------|-----------|---------|---------------|
| **SLV** | Satellite Launch Vehicle | First Indian rocket (1979) | ~40 kg |
| **ASLV** | Augmented SLV | Augmented version | ~150 kg |
| **PSLV** | Polar Satellite Launch Vehicle | Workhorse of ISRO | ~3800 kg (LEO) |
| **GSLV** | Geo-Synchronous Launch Vehicle | Heavy satellites | ~5000 kg (GTO) |
| **GSLV Mk III / LVM3** | Launch Vehicle Mark 3 | Heaviest operational | ~10,000 kg (LEO) |
| **SSLV** | Small Satellite Launch Vehicle | Small/nano satellites | ~500 kg (LEO) |

### 🎯 PYQ FACT: PSLV is called India's "workhorse rocket." It has launched 50+ consecutive missions successfully, including Chandrayaan-1, MOM (Mangalyaan), and hundreds of foreign satellites.

### 🎯 PYQ FACT: GSLV Mk III (LVM3) uses India's first indigenously developed **cryogenic engine** (CE-20). It carried Chandrayaan-2, Chandrayaan-3, and OneWeb satellites.

---

## 🔷 SECTION 3: Landmark ISRO Missions — Chronological Overview

---

### 🛰️ ARYABHATA (1975) — India's First Satellite
```
Launch Year: 19 April 1975
Launcher:   Soviet Kosmos-3M rocket (from USSR)
Named After: Ancient Indian mathematician Aryabhata
Significance: FIRST Indian satellite ever launched
Experiments: X-ray astronomy, solar neutrons, ionospheric studies
🎯 PYQ: Aryabhata was launched by USSR (Soviet rocket), NOT by an Indian rocket.
```

---

### 🌍 ROHINI (1980) — First Indian Orbit by Indian Rocket
```
Year: 18 July 1980
Launcher: SLV-3 (India's first launch vehicle)
Significance: FIRST satellite launched by an INDIAN rocket
🎯 PYQ: SLV-3 was developed under leadership of A.P.J. Abdul Kalam.
        Rohini = first successful orbital mission by Indian rocket.
```

---

### 🌙 CHANDRAYAAN-1 (2008) — India's First Moon Mission
```
Launch Date: 22 October 2008
Launcher:    PSLV-C11
Mission Type: Lunar orbiter + Moon Impact Probe (MIP)
Key Achievements:
  ✅ Confirmed PRESENCE OF WATER/ICE on the Moon (with NASA's M3 instrument)
  ✅ First Indian mission to reach another celestial body
  ✅ Launched 11 scientific instruments from 6 countries
  ✅ Moon Impact Probe crash-landed on South Pole region
  
🎯 PYQ: Chandrayaan-1 DISCOVERED WATER MOLECULES on the Moon's surface.
        This is its most-tested achievement!
```

---

### 🔴 MANGALYAAN / MOM (2013) — India's First Mars Mission
```
Full Name:  Mars Orbiter Mission (MOM) / Mangalyaan
Launch:     5 November 2013
Arrival:    24 September 2014 (Mars orbit insertion)
Launcher:   PSLV-C25

KEY FIRSTS:
  ✅ FIRST Mars mission by any Asian country
  ✅ FIRST mission to reach Mars orbit in FIRST ATTEMPT
  ✅ CHEAPEST Mars mission ever — cost ₹450 crore (~$74 million)
     (Cheaper than making the Hollywood film 'Gravity'!)
  ✅ India = 4th country/agency to reach Mars 
     (After USSR, USA, ESA — and FIRST in Asia)

Primary instrument: Methane Sensor for Mars (MSM)
Mission life: Designed for 6 months → lasted 7+ years
Lost contact: 2022

🎯 PYQ: MOM was the FIRST Mars mission to succeed in FIRST ATTEMPT.
        India is the FIRST Asian nation to reach Mars.
        Cost = ~₹450 crore (frequently asked!)
```

---

### 🚀 CHANDRAYAAN-2 (2019) — Moon's South Pole Attempt
```
Launch:     22 July 2019
Launcher:   GSLV Mk III (LVM3)
Mission:    Orbiter + Vikram Lander + Pragyan Rover

OUTCOME:
  ✅ Orbiter: Functioning perfectly, sending data (8-year life)
  ❌ Vikram Lander: Lost contact 2.1 km from surface (hard landing)
  
Vikram's speed at last contact: ~58 m/s (should have been ~2 m/s)
Location: 70.9°S latitude (South Pole region)
  
🎯 PYQ: Chandrayaan-2's orbiter is STILL OPERATIONAL.
        Vikram Lander CRASHED but was not a complete failure — orbiter succeeded.
```

---

### 🌙 CHANDRAYAAN-3 (2023) — Historic South Pole Landing!
```
Launch:     14 July 2023 (from SDSC Sriharikota)
Launcher:   LVM3-M4 (GSLV Mk III)
Landing:    23 August 2023, 6:04 PM IST
Landing Site: Shiv Shakti Point, near Moon's South Pole (69.37°S, 32.35°E)

COMPONENTS:
  → Propulsion Module (stays in orbit)
  → Vikram Lander (soft-landed successfully!)
  → Pragyan Rover (6-wheeled, solar-powered)
  
MAJOR ACHIEVEMENTS:
  ✅ INDIA = FIRST country to SOFT-LAND near the MOON'S SOUTH POLE
  ✅ India = 4th country to achieve soft landing on Moon
     (After USA, USSR, China)
  ✅ Pragyan Rover confirmed PRESENCE OF SULPHUR on Moon's South Pole
  ✅ Also detected: oxygen, iron, calcium, chromium, titanium, manganese
  ✅ Vikram Lander performed a 'hop' experiment — bounced and re-landed!
  
Landing Day: 23 August declared NATIONAL SPACE DAY by PM Modi
Mission Director: P. Veeramuthuvel
ISRO Chairman: S. Somanath

🎯 PYQ MOST IMPORTANT: India is FIRST to land near Moon's South Pole!
🎯 Pragyan confirmed SULPHUR on Moon's South Pole.
🎯 23 August = National Space Day.
```

---

### ☀️ ADITYA-L1 (2023) — India's First Solar Mission
```
Launch:     2 September 2023 (PSLV-C57)
Destination: Sun-Earth Lagrange Point 1 (L1)
Arrived at L1 Orbit: 6 January 2024

What is L1?
  A point in space 1.5 million km from Earth towards the Sun
  Objects here orbit in sync with Earth, providing UNINTERRUPTED view of Sun
  No eclipses, no occultations — continuous solar monitoring!

PAYLOADS (7 total):
  → VELC (Visible Emission Line Coronagraph) — Study solar corona
  → SUIT (Solar Ultraviolet Imaging Telescope) — UV imaging
  → Others study solar wind, particles, magnetic fields

OBJECTIVES:
  ✅ Study solar corona (temperature paradox — corona hotter than surface!)
  ✅ Monitor solar flares and Coronal Mass Ejections (CMEs)
  ✅ Study solar wind — affects Earth's magnetosphere!

🎯 PYQ: Aditya-L1 is India's FIRST solar mission.
🎯 It reached L1 orbit on 6 January 2024.
🎯 L1 = 1.5 million km from Earth toward Sun.
```

---

### 👨‍🚀 GAGANYAAN — India's First Human Spaceflight Mission
```
Status: Under Development (targeted 2025-2026)
Mission: Send 3 Indian astronauts (Vyomnauts) to Low Earth Orbit (400 km)
Launcher: LVM3 (GSLV Mk III)
Duration: 3 days in orbit

KEY MILESTONES ACHIEVED:
  ✅ TV-D1 (Test Vehicle Abort Mission 1): 21 October 2023 — Crew Escape System tested successfully
  ✅ 4 Astronaut candidates trained in Russia (IAF pilots): 
       Gp Capt. Prashanth Balakrishnan Nair, Gp Capt. Ajit Krishnan,
       Gp Capt. Angad Pratap, Wg Cdr Shubhanshu Shukla

  ✅ Shubhanshu Shukla to go to ISS as part of Axiom Mission (2025)
     [He'll be FIRST Indian to board ISS!]

Space Capsule: Named 'Vyommitra' (for half-humanoid robot testing)
Vyommitra = ISRO's space humanoid robot (female) for unmanned missions before human flight

🎯 PYQ: Indian astronaut in space = 'Vyomanaut' (not astronaut/cosmonaut)
🎯 Vyommitra is ISRO's humanoid robot for Gaganyaan.
```

---

### 🌊 OCEANSAT & EARTH OBSERVATION

```
OCEANSAT-3 (2022):
  Launch: 26 November 2022 (PSLV-C54)
  Purpose: Ocean colour monitoring, sea surface temperature, chlorophyll
  Replaced: Oceansat-2

EOS Series (Earth Observation Satellites):
  EOS-01, EOS-02, EOS-04, EOS-06 — various earth observation tasks
  Agriculture, forestry, disaster management, mapping

RISAT (Radar Imaging Satellite): 
  Uses microwave/radar — can image through clouds and at night!
  Used for border surveillance, disaster assessment
```

---

### 🛰️ NAVIGATION: NavIC (Navigation with Indian Constellation)
```
India's own GPS system!
Full Name: Navigation with Indian Constellation
Earlier Name: IRNSS (Indian Regional Navigation Satellite System)
Satellites: 7 operational satellites (NavIC constellation)
Coverage: India + 1500 km surrounding region

Why NavIC?
  USA's GPS can be SWITCHED OFF for non-US territory in wartime
  NavIC = India's INDEPENDENT navigation system for sovereignty

Use Cases: Terrestrial, aerial, marine navigation; disaster management;
           vehicle tracking; mobile phones

🎯 PYQ: NavIC = India's own satellite navigation system (like GPS)
         Coverage = India + 1500 km beyond borders
```

---

### 📡 COMMUNICATION: INSAT & GSAT Series
```
INSAT = Indian National Satellite System
  - Multipurpose geostationary satellite system
  - Weather forecasting, TV broadcasting, telecommunications
  - India's workhorse communication constellation since 1983

GSAT Series: Latest generation communication satellites
  GSAT-20 / CMS-03 (2024): Launched on SpaceX Falcon 9 (first ISRO-SpaceX collab!)
  High throughput satellite for broadband internet across India

🎯 PYQ: INSAT series started in 1983.
```

---

## 🔷 SECTION 4: Recent Highlights (2023-2024)

| Mission | Date | Significance |
|---------|------|--------------|
| Chandrayaan-3 | 23 Aug 2023 | First soft landing near Moon's South Pole |
| Aditya-L1 Launch | 2 Sep 2023 | India's first solar observatory mission |
| TV-D1 (Gaganyaan abort test) | 21 Oct 2023 | Crew escape system validated |
| Aditya-L1 reaches L1 | 6 Jan 2024 | Halo orbit insertion around L1 |
| GSAT-20 / CMS-03 | Nov 2024 | High-throughput comm satellite via SpaceX |
| XPoSat | 1 Jan 2024 | India's first X-ray Polarimetry satellite (New Year's Day!) |

### 🎯 XPoSat — NEW YEAR 2024 LAUNCH!
```
XPoSat = X-ray Polarimeter Satellite
Launch: 1 January 2024 (New Year's Day!)
Purpose: Study X-ray sources in extreme conditions (pulsars, black holes)
India = 2nd country to have dedicated X-ray polarimetry mission (after USA's IXPE)
Launcher: PSLV-C58
```

---

## 🔷 SECTION 5: Key Numbers & Facts — Quick Recall

```
ISRO FOUNDED:         1969 (15 August)
FIRST SATELLITE:      Aryabhata, 1975 (launched by USSR)
FIRST INDIAN ROCKET:  SLV-3, 1980 (Rohini satellite)
PSLV RECORD:          100 satellites in ONE launch (2017, PSLV-C37!)
MOM COST:             ~₹450 crore
CHANDRAYAAN-3 LANDING: 23 August 2023
NATIONAL SPACE DAY:   23 August
ADITYA-L1 at L1:      6 January 2024
ISRO CHAIRMAN (2024): S. Somanath
LAUNCH CENTRE:        Sriharikota, Andhra Pradesh
```

### 🎯 PYQ RECORD: PSLV-C37 launched 104 satellites simultaneously (2017) — WORLD RECORD at that time! 95 were from USA.

---

## 🔷 SECTION 6: ISRO Mission Summary Table

| Mission | Year | Type | Key Achievement |
|---------|------|------|----------------|
| Aryabhata | 1975 | First Indian Satellite | First satellite (launched by USSR) |
| Rohini | 1980 | First Indian Orbital Mission | First launch by Indian rocket (SLV-3) |
| IRS-1A | 1988 | Remote Sensing | India's first operational remote sensing satellite |
| INSAT-2A | 1992 | Communication | Multipurpose geostationary satellite |
| PSLV-C37 | 2017 | Launch Vehicle Record | 104 satellites in one launch (world record!) |
| Chandrayaan-1 | 2008 | Lunar Orbiter | Discovered water on Moon |
| MOM/Mangalyaan | 2013 | Mars Orbiter | First Asian Mars mission; first in first attempt |
| Chandrayaan-2 | 2019 | Lunar Orbiter+Lander | Orbiter operational; lander crashed |
| Chandrayaan-3 | 2023 | Lunar Lander+Rover | First soft landing near South Pole |
| Aditya-L1 | 2023 | Solar Mission | India's first solar observatory at L1 |
| XPoSat | 2024 | X-ray Polarimetry | India's first X-ray polarimeter satellite |
| Gaganyaan | TBD | Human Spaceflight | First Indian human space mission (planned) |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Time Complexity, Big-O/Omega/Theta, Algorithm Analysis

---

**Q1.** What does Time Complexity of an algorithm measure?
(A) The actual time in seconds the algorithm takes to run
(B) The memory used by the algorithm
(C) How the number of operations grows as a function of input size n
(D) More than one of the above
(E) None of the above

---

**Q2.** Which asymptotic notation represents the UPPER BOUND (worst case) of an algorithm's time complexity?
(A) Ω (Big-Omega)
(B) Θ (Big-Theta)
(C) O (Big-O)
(D) More than one of the above
(E) None of the above

---

**Q3.** For f(n) = 5n² + 3n + 100, what is the Big-O time complexity?
(A) O(5n²)
(B) O(n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the time complexity of the following code?
```
for (int i = 1; i <= n; i *= 2) {
    System.out.println(i);
}
```
(A) O(n)
(B) O(n²)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q5.** What is the WORST CASE time complexity of Binary Search?
(A) O(n)
(B) O(log n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the WORST CASE time complexity of Bubble Sort?
(A) O(n log n)
(B) O(n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following represents the correct ORDER of growth from FASTEST to SLOWEST?
(A) O(1) < O(n) < O(log n) < O(n²) < O(n log n)
(B) O(1) < O(log n) < O(n) < O(n log n) < O(n²)
(C) O(log n) < O(1) < O(n) < O(n²) < O(n log n)
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the time complexity of Infix to Postfix conversion?
(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q9.** Notation Θ (Big-Theta) represents:
(A) Only the worst case
(B) Only the best case
(C) Both upper and lower bound (tight bound)
(D) More than one of the above
(E) None of the above

---

**Q10.** What is the WORST CASE time complexity of Merge Sort?
(A) O(n²)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q11.** What is the time complexity of the following nested loop?
```
for (int i = 0; i < n; i++) {
    for (int j = 0; j < 50; j++) {
        System.out.println(i + j);
    }
}
```
(A) O(n²)
(B) O(50n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q12.** Which sorting algorithm has the SAME time complexity (Θ(n log n)) in ALL cases — best, average, and worst?
(A) Quick Sort
(B) Bubble Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q13.** In Big-O notation, f(n) = O(g(n)) means:
(A) f(n) grows faster than g(n)
(B) f(n) grows at most as fast as g(n) (g(n) is an upper bound)
(C) f(n) and g(n) grow at exactly the same rate
(D) More than one of the above
(E) None of the above

---

**Q14.** What is the time complexity of accessing the k-th element in an ARRAY?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q15.** The BEST CASE time complexity of Linear Search is:
(A) O(n)
(B) O(n/2)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q16.** If an algorithm has time complexity T(n) = 3n² + 5n + 200, which notation correctly represents its lower bound (best case)?
(A) O(n²)
(B) Θ(n)
(C) Ω(n²)
(D) More than one of the above
(E) None of the above

---

**Q17.** What is the time complexity for finding the MAXIMUM element in an unsorted array of n elements?
(A) O(log n) using binary search
(B) O(1) if we know the last element is maximum
(C) O(n) as we must check each element
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following is O(log n) — NOT O(n)?
(A) Linear Search on unsorted array
(B) Traversing a linked list
(C) Binary Search on sorted array
(D) More than one of the above
(E) None of the above

---

**Q19.** What is the WORST CASE time complexity of Quick Sort?
(A) O(n log n)
(B) O(n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

**Q20.** For a function f(n) = Θ(g(n)), which relationship is TRUE?
(A) f(n) = O(g(n)) only
(B) f(n) = Ω(g(n)) only
(C) f(n) = O(g(n)) AND f(n) = Ω(g(n))
(D) More than one of the above
(E) None of the above

---

**Q21.** What is the SPACE complexity of Merge Sort?
(A) O(1) — in-place
(B) O(log n) — for recursion stack
(C) O(n) — requires auxiliary array
(D) More than one of the above
(E) None of the above

---

**Q22.** Which sorting algorithm is called STABLE and has GUARANTEED O(n log n) complexity in all cases?
(A) Quick Sort
(B) Heap Sort
(C) Merge Sort
(D) More than one of the above
(E) None of the above

---

**Q23.** Naive recursive Fibonacci (fib(n) = fib(n-1) + fib(n-2)) has which time complexity?
(A) O(n)
(B) O(n log n)
(C) O(2ⁿ)
(D) More than one of the above
(E) None of the above

---

**Q24.** O(log₂n) and O(log₃n) are:
(A) Different complexities
(B) The same complexity class O(log n)
(C) O(log₃n) is always faster
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider the following:
```
int count = 0;
for (int i = 0; i < n; i++) {        // Loop A
    for (int j = i; j < n; j++) {    // Loop B
        count++;
    }
}
```
What is the time complexity?

(A) O(n)
(B) O(n log n)
(C) O(n²)
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: ISRO Missions, India's Space Programme

---

**Q26.** ISRO was founded on:
(A) 15 August 1947
(B) 15 August 1969
(C) 1 November 1962
(D) More than one of the above
(E) None of the above

---

**Q27.** India's FIRST satellite, Aryabhata, was launched in which year and by which country's rocket?
(A) 1975, India's own SLV
(B) 1975, by USSR (Soviet) rocket
(C) 1980, by USA's rocket
(D) More than one of the above
(E) None of the above

---

**Q28.** Which was the FIRST satellite to be launched by an INDIAN rocket?
(A) Aryabhata
(B) Chandrayaan-1
(C) Rohini (by SLV-3, 1980)
(D) More than one of the above
(E) None of the above

---

**Q29.** Chandrayaan-1's MOST SIGNIFICANT scientific discovery was:
(A) First images of Moon's far side
(B) Confirmation of water molecules on the Moon's surface
(C) Discovery of liquid water under Moon's south pole
(D) More than one of the above
(E) None of the above

---

**Q30.** Mars Orbiter Mission (Mangalyaan) was launched in:
(A) October 2013; reached Mars in September 2014
(B) November 2013; reached Mars in September 2014
(C) November 2013; reached Mars in December 2013
(D) More than one of the above
(E) None of the above

---

**Q31.** India's Mars Orbiter Mission (MOM) is historically significant because:
(A) It was the first mission to land on Mars
(B) It was the first Asian nation's Mars mission and succeeded in the FIRST attempt
(C) It was the cheapest Moon mission ever
(D) More than one of the above
(E) None of the above

---

**Q32.** Chandrayaan-3 successfully soft-landed on the Moon on:
(A) 14 July 2023
(B) 23 August 2023
(C) 2 September 2023
(D) More than one of the above
(E) None of the above

---

**Q33.** Which element was confirmed by Pragyan Rover at the Moon's South Pole for the FIRST TIME?
(A) Water ice
(B) Helium-3
(C) Sulphur
(D) More than one of the above
(E) None of the above

---

**Q34.** With Chandrayaan-3's successful landing, India became the ________ country to achieve a soft landing on the Moon:
(A) Third
(B) Fourth
(C) Second
(D) More than one of the above
(E) None of the above

---

**Q35.** The landing site of Chandrayaan-3's Vikram Lander is named:
(A) Nehru Point
(B) Bharat Tirtha
(C) Shiv Shakti Point
(D) More than one of the above
(E) None of the above

---

**Q36.** Aditya-L1 is India's first mission to study:
(A) The Moon
(B) Mars
(C) The Sun
(D) More than one of the above
(E) None of the above

---

**Q37.** What is the Lagrange Point L1 where Aditya-L1 is stationed?
(A) A point between Moon and Earth where gravity is balanced
(B) A point 1.5 million km from Earth towards the Sun, allowing continuous solar observation
(C) A point in Mars orbit
(D) More than one of the above
(E) None of the above

---

**Q38.** Which ISRO rocket set the WORLD RECORD by launching 104 satellites in a SINGLE mission?
(A) GSLV Mk III
(B) PSLV-C37 (2017)
(C) SSLV-D1
(D) More than one of the above
(E) None of the above

---

**Q39.** PSLV is described as the "workhorse" of ISRO. What does PSLV stand for?
(A) Polar Satellite Launch Vehicle
(B) Powerful Space Launch Vehicle
(C) Primary Satellite Launch Vehicle
(D) More than one of the above
(E) None of the above

---

**Q40.** India's own satellite navigation system, equivalent to GPS, is called:
(A) INSAT
(B) NavIC (Navigation with Indian Constellation)
(C) RISAT
(D) More than one of the above
(E) None of the above

---

**Q41.** XPoSat, launched on 1 January 2024, is India's first satellite for:
(A) Solar observation
(B) X-ray polarimetry (studying pulsars and black holes)
(C) Marine navigation
(D) More than one of the above
(E) None of the above

---

**Q42.** The Gaganyaan mission aims to:
(A) Land an unmanned rover on the Moon
(B) Send Indian astronauts to Low Earth Orbit
(C) Place a satellite at L2 point
(D) More than one of the above
(E) None of the above

---

**Q43.** Indian astronauts in the Gaganyaan programme are called:
(A) Cosmonauts
(B) Astronauts
(C) Vyomnauts
(D) More than one of the above
(E) None of the above

---

**Q44.** Who is known as the "Father of India's Space Programme"?
(A) A.P.J. Abdul Kalam
(B) Vikram Sarabhai
(C) Satish Dhawan
(D) More than one of the above
(E) None of the above

---

**Q45.** The main launch centre of ISRO is located at:
(A) Thiruvananthapuram, Kerala
(B) Sriharikota, Andhra Pradesh
(C) Bengaluru, Karnataka
(D) More than one of the above
(E) None of the above

---

**Q46.** 23 August has been declared as National Space Day by Prime Minister Modi. This date marks:
(A) ISRO's founding day
(B) Chandrayaan-3's successful Moon landing day
(C) India's first satellite launch
(D) More than one of the above
(E) None of the above

---

**Q47.** Which ISRO mission was the FIRST to use the cryogenic engine developed indigenously by India?
(A) PSLV-C11 (Chandrayaan-1)
(B) GSLV-D5 (with indigenous CE-7.5 cryogenic engine)
(C) SLV-3 (Rohini mission)
(D) More than one of the above
(E) None of the above

---

**Q48.** Chandrayaan-2's Vikram Lander was unique for attempting to land near the Moon's South Pole. What was the outcome?
(A) Successfully landed and deployed rover
(B) Lander crashed but orbiter continued operating successfully
(C) Entire mission was aborted
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following correctly matches the ISRO mission with its PRIMARY PURPOSE?
(A) MOM — Study the Moon; Chandrayaan — Study Mars
(B) Aditya-L1 — Study the Sun; MOM — Study Mars; Chandrayaan — Study the Moon
(C) NavIC — Study deep space; RISAT — Study navigation
(D) More than one of the above
(E) None of the above

---

**Q50.** The approximate cost of India's Mangalyaan (MOM) mission was:
(A) ₹4,500 crore
(B) ₹45 crore
(C) ₹450 crore
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
| 1 | (C) | Time complexity = how operations grow with n, NOT actual seconds |
| 2 | (C) | Big-O = upper bound = worst case (by convention) |
| 3 | (C) | 5n² + 3n + 100 → dominant term = n², constants dropped → O(n²) |
| 4 | (C) | i multiplied by 2 each step → log₂n iterations → O(log n) |
| 5 | (B) | Binary Search worst = O(log n) — key at extreme or not found |
| 6 | (C) | Bubble Sort worst = O(n²) — reverse sorted input |
| 7 | (B) | O(1) < O(log n) < O(n) < O(n log n) < O(n²) — standard hierarchy |
| 8 | (C) | Each character processed exactly once → O(n) |
| 9 | (C) | Θ = tight bound = both upper AND lower bound simultaneously |
| 10 | (B) | Merge Sort = Θ(n log n) in ALL cases — worst, avg, best |
| 11 | (C) | Inner loop = 50 (constant!) → n × 50 = 50n = O(n) |
| 12 | (C) | Merge Sort = Θ(n log n) always; Quick Sort's worst = O(n²) |
| 13 | (B) | f(n) = O(g(n)) means f grows AT MOST as fast as g |
| 14 | (C) | Array random access by index = O(1) — direct memory calculation |
| 15 | (C) | Linear Search best = O(1) — target found at very first position |
| 16 | (C) | Ω(n²) = lower bound — algorithm takes AT LEAST n² operations |
| 17 | (C) | Must scan all elements to find max in unsorted array → O(n) |
| 18 | (C) | Binary Search = O(log n); linear search and list traversal = O(n) |
| 19 | (C) | Quick Sort worst = O(n²) when pivot always min/max (sorted array) |
| 20 | (C) | Θ(g) = O(g) AND Ω(g) simultaneously — that's its definition |
| 21 | (C) | Merge Sort needs auxiliary array of size n → O(n) space |
| 22 | (C) | Merge Sort: stable + guaranteed O(n log n) in ALL cases |
| 23 | (C) | Naive Fibonacci makes 2 recursive calls → exponential tree → O(2ⁿ) |
| 24 | (B) | log₂n and log₃n differ only by a constant → same class O(log n) |
| 25 | (C) | Loop B runs (n-i) times; total = n + (n-1) + ... + 1 = n(n+1)/2 → O(n²) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | ISRO founded 15 August 1969 |
| 27 | (B) | Aryabhata, 1975, launched by USSR's Kosmos-3M rocket |
| 28 | (C) | Rohini by SLV-3, July 1980 — first Indian rocket orbital mission |
| 29 | (B) | Chandrayaan-1 confirmed water molecules on Moon surface |
| 30 | (B) | MOM launched 5 November 2013; Mars insertion 24 September 2014 |
| 31 | (B) | First Asian Mars mission; first and only to succeed in FIRST attempt |
| 32 | (B) | Chandrayaan-3 landed 23 August 2023 at 6:04 PM IST |
| 33 | (C) | Pragyan Rover's LIBS confirmed Sulphur on Moon's South Pole |
| 34 | (B) | India = 4th country (after USA, USSR, China) for soft Moon landing |
| 35 | (C) | Landing site named 'Shiv Shakti Point' by PM Modi |
| 36 | (C) | Aditya-L1 = India's first solar (Sun-studying) mission |
| 37 | (B) | L1 = 1.5 million km from Earth toward Sun; unobstructed Sun view |
| 38 | (B) | PSLV-C37 launched 104 satellites on 15 February 2017 |
| 39 | (A) | PSLV = Polar Satellite Launch Vehicle |
| 40 | (B) | NavIC = Navigation with Indian Constellation (India's GPS) |
| 41 | (B) | XPoSat = X-ray Polarimeter Satellite for studying pulsars/black holes |
| 42 | (B) | Gaganyaan = India's first human spaceflight to LEO |
| 43 | (C) | Indian astronauts = Vyomnauts (Vyoma = sky/space in Sanskrit) |
| 44 | (B) | Vikram Sarabhai = Father of India's Space Programme |
| 45 | (B) | SDSC SHAR, Sriharikota, Andhra Pradesh |
| 46 | (B) | 23 August = Chandrayaan-3 landing date = National Space Day |
| 47 | (B) | GSLV-D5 (Jan 2014) = first flight with indigenous cryogenic engine |
| 48 | (B) | Vikram crashed; Chandrayaan-2 orbiter is still active |
| 49 | (B) | Aditya-L1→Sun; MOM→Mars; Chandrayaan→Moon — all correct |
| 50 | (C) | MOM cost ≈ ₹450 crore (~$74 million) — world's cheapest Mars mission |

---
---

# 🔁 DAY 29 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Time Complexity & Big-O

### THE GOLDEN HIERARCHY (Memorise This!):
```
FASTEST ←————————————————————————————→ SLOWEST
 O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!)

Remember: "1 Log N NlogN NN Exp Fact"
```

### Three Notations — One-Line Definitions:
```
O  (Big-O):     UPPER BOUND   → Algorithm takes AT MOST this time (worst case)
Ω  (Big-Omega): LOWER BOUND   → Algorithm takes AT LEAST this time (best case)
Θ  (Big-Theta): TIGHT BOUND   → Algorithm takes EXACTLY this (both bounds)

If f = O(g) AND f = Ω(g) → f = Θ(g)
```

### Common Complexities — Real Examples:
```
O(1):      Array index access, push/pop on stack, linked list begin-insert
O(log n):  Binary Search, balanced BST operations
O(n):      Linear Search, array traversal, Infix→Postfix, linked list traverse
O(n log n): Merge Sort, Heap Sort, Quick Sort (avg)
O(n²):     Bubble/Selection/Insertion Sort, nested loop comparisons
O(2ⁿ):    Naive Fibonacci, Tower of Hanoi, all-subset generation
```

### Calculation Rules (Exam Fast-Track):
```
Rule 1: f(n) = 5n² + 3n + 10 → DROP constants & lower terms → O(n²)
Rule 2: Loop i *= 2 → O(log n)    | Loop i++ → O(n)
Rule 3: NESTED loops → MULTIPLY   | SEQUENTIAL code → take MAX (dominant)
Rule 4: Inner constant loop (j<100) → treat as O(1) → outer loop complexity
Rule 5: O(log n) + O(n) = O(n)    | O(n) × O(n) = O(n²)
Rule 6: log base doesn't matter: O(log₂n) = O(log₃n) = O(log n)
```

### Algorithm Quick Reference:
```
Linear Search:  O(1) best | O(n) worst        [needs: nothing]
Binary Search:  O(1) best | O(log n) worst    [needs: SORTED array!]
Bubble Sort:    O(n) best | O(n²) worst       [stable, in-place]
Merge Sort:     Θ(n log n) ALL cases          [stable, O(n) space]
Quick Sort:     O(n log n) avg | O(n²) worst  [NOT stable, O(log n) space]
Infix→Postfix:  O(n) always                  [uses stack, O(n) space]
```

### PYQ One-Liners:
```
✅ Big-O = WORST CASE by convention (even though it's formally an upper bound)
✅ Merge Sort = ONLY sorting algorithm that is STABLE + ALWAYS O(n log n)
✅ Quick Sort WORST = O(n²) when pivot = first/last element on sorted array
✅ Binary Search REQUIRES sorted input — fails on unsorted!
✅ O(1) exceptions in linked list: insert/delete at BEGINNING only
✅ Θ is the most PRECISE notation (tight bound = best = worst = same rate)
```

---

## ⚡ RAPID FIRE — ISRO Missions

### ISRO Timeline — 5 Most Important Dates:
```
1969: ISRO Founded (15 August)
1975: Aryabhata — India's FIRST satellite (launched by USSR)
1980: Rohini — First satellite by INDIAN rocket (SLV-3)
2008: Chandrayaan-1 — Discovered WATER on Moon
2013: MOM — First Asian Mars mission; First in first attempt
2017: PSLV-C37 — WORLD RECORD 104 satellites in one launch
2023: Chandrayaan-3 — FIRST soft landing near Moon's South Pole (23 Aug)
2023: Aditya-L1 — India's first solar mission (2 Sep)
2024: XPoSat — India's first X-ray polarimetry satellite (1 Jan)
```

### Key Achievements — FIRSTS:
```
FIRST Indian satellite:              Aryabhata (1975) — by USSR rocket
FIRST by Indian rocket:              Rohini (1980) — SLV-3 by APJ Abdul Kalam
FIRST to detect water on Moon:       Chandrayaan-1 (2008)
FIRST Asian Mars mission:            MOM/Mangalyaan (2013)
FIRST Mars mission success in attempt: MOM (2013)
FIRST near South Pole Moon landing:  Chandrayaan-3 (23 Aug 2023)
FIRST solar mission:                 Aditya-L1 (2023)
FIRST X-ray polarimetry satellite:   XPoSat (1 Jan 2024)
```

### Key Numbers (Memorise for MCQs):
```
Chandrayaan-3 landing: 23 August 2023 → National Space Day
MOM cost:              ~₹450 crore (~$74 million)
PSLV-C37 record:       104 satellites in ONE launch (2017)
Aditya-L1 distance:    1.5 million km from Earth (L1 point)
NavIC coverage:        India + 1500 km surrounding region
Gaganyaan altitude:    400 km Low Earth Orbit
Article 21A covers:    Children aged 6–14 years
Chandrayaan-3 landing: 4th country (USA, USSR, China, India)
Pragyan found:         SULPHUR (first confirmed at South Pole!)
```

### Father / Key Persons:
```
Father of India's Space Programme: Vikram Sarabhai
A.P.J. Abdul Kalam:  Led SLV-3 (Rohini, 1980); later President of India
S. Somanath:         Current ISRO Chairman (Chandrayaan-3, Aditya-L1 era)
P. Veeramuthuvel:    Mission Director, Chandrayaan-3
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Complexity hierarchy**: O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) — memorise this order; it appears every year!
2. **Big-O = upper bound = worst case (convention)**; Ω = lower bound = best case; Θ = tight bound (both sides); Merge Sort = Θ(n log n) always
3. **Loop trick**: i *= 2 → O(log n); nested loops (both n) → O(n²); inner constant loop → treat as O(1), outer determines complexity
4. **Chandrayaan-3**: 23 August 2023 = National Space Day; India = FIRST near Moon's South Pole; Pragyan confirmed SULPHUR; 4th country for soft landing
5. **ISRO firsts**: Aryabhata (1975, USSR rocket) = first satellite; Rohini (1980, SLV-3) = first by Indian rocket; MOM (2013) = first Asian Mars, first in first attempt; ₹450 crore cost

---

## 📅 DAY 30 PREVIEW — What's Coming Next:
**CS**: Searching Algorithms — Linear Search (detailed), Binary Search (iterative + recursive), Interpolation Search, Comparison of all search methods
**GS**: Indian Polity — Parliament of India: Structure, Lok Sabha, Rajya Sabha, Functions, Sessions, Bills, Question Hour

---

*🚀 Keep going! Day 29 of 170 — You're 17% through the journey. Consistency compounds.*
