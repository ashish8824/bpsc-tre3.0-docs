# 📅 BPSC TRE 4.0 — DAY 32 COMPLETE STUDY MODULE
### Searching Algorithms & Hashing + Current Affairs: Nobel Prize Winners
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Searching Algorithms (Linear, Binary) + Hashing — Concepts, Dry Runs, Collision
> - Afternoon (1 hr): Nobel Prize Winners — Fields, Indian Winners, Key Facts
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Searching Algorithms & Hashing — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is Searching?

### Real-Life Analogy — Finding a Friend in a City:

**Scenario A — Random City (Unsorted):**
Your friend could be at any of 1000 addresses, all randomly listed.
You have no choice but to check address #1, then #2, then #3...
→ This is **LINEAR SEARCH** — check every element until found.

**Scenario B — Phone Directory (Sorted alphabetically):**
You open the directory to the MIDDLE.
Last name starts with 'T' — you need 'R' → go to the LEFT half.
Open THAT middle again → keep halving until found!
→ This is **BINARY SEARCH** — eliminate half the search space each step.

**Scenario C — Library Index (Hash-based):**
The library has an INDEX at the back.
You look up "Tree" → Index says "Page 247".
Go DIRECTLY to page 247 — no searching at all!
→ This is **HASHING** — direct access via a computed address.

---

## 🔷 SECTION 2: LINEAR SEARCH

### Concept:
Check each element of the array **one by one**, from the first to the last,
until the target element is found or the entire array is scanned.

```
NO PRECONDITION: Works on BOTH sorted and unsorted arrays.
SIMPLE: Easiest search to implement.
SEQUENTIAL: Always starts from the beginning.
```

### Algorithm:
```
linearSearch(arr, n, target):
    for i = 0 to n-1:
        if arr[i] == target:
            return i          ← FOUND at index i
    return -1                 ← NOT FOUND
```

### Step-by-Step Dry Run:
```
Array: [15, 3, 28, 1, 9, 22, 7]    n = 7
Target: 22

Index:   0   1   2   3  4   5   6
Array: [15,  3, 28,  1, 9, 22,  7]

Step 1: i=0 → arr[0]=15 ≠ 22 → CONTINUE
Step 2: i=1 → arr[1]=3  ≠ 22 → CONTINUE
Step 3: i=2 → arr[2]=28 ≠ 22 → CONTINUE
Step 4: i=3 → arr[3]=1  ≠ 22 → CONTINUE
Step 5: i=4 → arr[4]=9  ≠ 22 → CONTINUE
Step 6: i=5 → arr[5]=22 = 22 → FOUND! Return index 5 ✅

If target = 100:
  Steps 1-7: All 7 comparisons made, none match → return -1

Visual scan:
[15 → 3 → 28 → 1 → 9 → 22✓]  ← stops here
         or
[15 → 3 → 28 → 1 → 9 → 22 → 7 → NOT FOUND]
```

### Complexity Analysis:
```
BEST CASE:    Target at FIRST position → 1 comparison → O(1)
AVERAGE CASE: Target somewhere in middle → n/2 comparisons → O(n)
WORST CASE:   Target at LAST position OR not in array → n comparisons → O(n)

SPACE: O(1) — no extra memory needed

KEY PROPERTIES:
  → Works on unsorted AND sorted arrays
  → Simple to implement
  → Inefficient for large datasets
  → Useful for small arrays or single searches
```

### 🚨 PYQ TRAP #1: Linear Search Best Case
> Best case for Linear Search = O(1), NOT O(n)!
> It occurs when the target is at the **very first position**.
> Most people say "Linear Search is O(n)" — that's the worst/average case.
> For a precise exam answer: Best = O(1), Worst = Average = O(n).

---

## 🔷 SECTION 3: BINARY SEARCH

### Concept — The Bisection Method:

**PRECONDITION: Array MUST be SORTED (ascending or descending).**

In each step, compare target with the **MIDDLE element**:
- If `target == middle` → FOUND!
- If `target < middle` → Search LEFT half (eliminate right half)
- If `target > middle` → Search RIGHT half (eliminate left half)

Each step **eliminates HALF** the remaining elements.
For n=1,000,000 elements: at most 20 steps! (log₂1,000,000 ≈ 20)

### The Key Formula:
```
mid = (low + high) / 2

where:
  low  = starting index of current search range
  high = ending index of current search range
  mid  = middle index (integer division)

ALTERNATIVE (avoids integer overflow):
  mid = low + (high - low) / 2
  (preferred in competitive programming to prevent overflow)
```

### Algorithm — Iterative Version:
```
binarySearch(arr, n, target):
    low = 0
    high = n - 1

    while low <= high:
        mid = (low + high) / 2

        if arr[mid] == target:
            return mid          ← FOUND

        else if arr[mid] < target:
            low = mid + 1       ← Search RIGHT half (eliminate left)

        else:
            high = mid - 1      ← Search LEFT half (eliminate right)

    return -1                   ← NOT FOUND
```

### Algorithm — Recursive Version:
```
binarySearch(arr, low, high, target):
    if low > high:
        return -1               ← BASE CASE: search space empty

    mid = (low + high) / 2

    if arr[mid] == target:
        return mid              ← FOUND

    else if arr[mid] < target:
        return binarySearch(arr, mid+1, high, target)  ← Right half

    else:
        return binarySearch(arr, low, mid-1, target)   ← Left half
```

### Complete Step-by-Step Dry Run:

```
Array (sorted): [2, 5, 8, 12, 16, 23, 38, 45, 56, 72]
Indices:          0  1  2   3   4   5   6   7   8   9
n = 10

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEARCH 1: Find target = 23
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STEP 1: low=0, high=9
  mid = (0+9)/2 = 4
  arr[4] = 16
  16 < 23 → target is in RIGHT half
  low = mid+1 = 5

  [2, 5, 8, 12, 16, 23, 38, 45, 56, 72]
   0  1  2   3   4   5   6   7   8   9
   ←——————————× ELIMINATED ×——→  ↑low
   (left half eliminated)

STEP 2: low=5, high=9
  mid = (5+9)/2 = 7
  arr[7] = 45
  45 > 23 → target is in LEFT half
  high = mid-1 = 6

  [_, _, _, _, _, 23, 38, 45, 56, 72]
                   5   6   7   8   9
                  ↑low       ↑high×
                            (right eliminated)

STEP 3: low=5, high=6
  mid = (5+6)/2 = 5
  arr[5] = 23
  23 == 23 → FOUND at index 5! ✅

Total comparisons: 3 (for n=10, log₂10 ≈ 3.3 → max 4 steps)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEARCH 2: Find target = 10 (NOT in array)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STEP 1: low=0, high=9, mid=4, arr[4]=16
  16 > 10 → go LEFT → high = 3

STEP 2: low=0, high=3, mid=1, arr[1]=5
  5 < 10 → go RIGHT → low = 2

STEP 3: low=2, high=3, mid=2, arr[2]=8
  8 < 10 → go RIGHT → low = 3

STEP 4: low=3, high=3, mid=3, arr[3]=12
  12 > 10 → go LEFT → high = 2

STEP 5: low=3 > high=2 → STOP → return -1 (NOT FOUND) ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BINARY SEARCH ELIMINATION VISUAL:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

n = 16 elements, target somewhere:

Step 1: 16 elements → check mid → 8 elements remain
Step 2:  8 elements → check mid → 4 elements remain
Step 3:  4 elements → check mid → 2 elements remain
Step 4:  2 elements → check mid → 1 element remains
Step 5:  1 element  → check mid → FOUND or NOT FOUND

Total steps = log₂16 = 4 (or 5 at most)
Compare to Linear Search: up to 16 steps!

GENERAL: n elements → at most ⌈log₂(n+1)⌉ comparisons
```

### Why O(log n)?

```
MATHEMATICAL PROOF:
  After k steps, remaining elements = n / 2^k
  Search ends when remaining elements = 1:
    n / 2^k = 1
    2^k = n
    k = log₂n

  Therefore: Binary Search ≈ log₂n steps = O(log n)

CONCRETE NUMBERS:
  n = 8:         log₂8    =  3 steps
  n = 1024:      log₂1024 = 10 steps
  n = 1,000,000: log₂10⁶ ≈ 20 steps
  n = 1 BILLION: log₂10⁹ ≈ 30 steps  ← Only 30 comparisons!
```

### Complexity Summary for Binary Search:
```
Best Case:    O(1)     — target is exactly at mid in first step
Average Case: O(log n)
Worst Case:   O(log n) — target at extreme end or not present
Space (iterative): O(1) — only low, high, mid variables
Space (recursive): O(log n) — recursion stack depth
```

### 🚨 PYQ TRAP #2: Binary Search on Unsorted Array
> Binary Search **CANNOT** be applied to unsorted arrays.
> If array is unsorted → either sort first (O(n log n)) then search O(log n),
> OR use Linear Search directly O(n).
> For a ONE-TIME search on unsorted data: Linear Search is BETTER (no sorting needed)!
> For MULTIPLE searches: Sort once then use Binary Search repeatedly.

---

## 🔷 SECTION 4: LINEAR vs BINARY SEARCH — Master Comparison

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Feature            | Linear Search    | Binary Search
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Input requirement  | Unsorted/Sorted  | MUST BE SORTED
Best Case          | O(1)             | O(1)
Average Case       | O(n)             | O(log n)
Worst Case         | O(n)             | O(log n)
Space              | O(1)             | O(1) iter / O(log n) recur
Data Structure     | Array or LL      | Array only (random access)
Implementation     | Very simple      | Moderate
Suitable for       | Small/unsorted   | Large sorted datasets
One-time search    | Preferred        | Sort first = overhead
Repeated search    | Less efficient   | Highly efficient after sorting
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Growth Comparison:
```
n elements:        Linear Search    Binary Search
n =         10:    10 comparisons   4 comparisons
n =        100:   100 comparisons   7 comparisons
n =      1,000: 1,000 comparisons  10 comparisons
n =  1,000,000: 1,000,000 compare  20 comparisons
n = 1,000,000,000: 1 BILLION       30 comparisons

THE GAP IS ENORMOUS for large n — this is the power of O(log n)!
```

---

## 🔷 SECTION 5: HASHING — Direct Access Data Structure

### Concept — The Book Index Analogy:

Imagine a **textbook with 1000 pages** and an **index at the back**:
- To find "Binary Tree" → check index → "Page 247" → go directly!
- No need to scan 1000 pages one by one.
- The INDEX is the **hash table**, and the page number is the **hash value**.

```
Another Analogy — Locker System at a Gym:
  100 lockers numbered 0-99
  Each member has a locker number based on their ID:
    locker = memberID % 100   ← This is the HASH FUNCTION!
  
  Member 1257 → 1257 % 100 = 57 → goes to Locker 57 DIRECTLY
  Member 1357 → 1357 % 100 = 57 → SAME locker! → COLLISION!
  
  The locker system = HASH TABLE
  The rule "ID % 100" = HASH FUNCTION
  Two members wanting same locker = COLLISION
```

### Formal Definitions:

```
HASH FUNCTION h(key):
  A function that converts a KEY (data) into an INDEX (address)
  in the hash table.
  
  Properties of a good hash function:
    1. DETERMINISTIC: Same key always gives same hash value
    2. UNIFORM: Distributes keys evenly across the table
    3. FAST: O(1) to compute
    4. MINIMIZE COLLISIONS: Rarely assigns same index to different keys

HASH TABLE:
  An array of SIZE m (called table size or bucket count)
  Each slot/position is called a BUCKET
  Elements stored at arr[h(key)]

SIMPLE EXAMPLE:
  Table size: m = 10 (buckets 0-9)
  Hash function: h(key) = key % m = key % 10
  
  Insert keys: 15, 25, 37, 48, 72, 56
  
  h(15) = 15 % 10 = 5 → Store at bucket 5
  h(25) = 25 % 10 = 5 → COLLISION with 15! (both map to 5)
  h(37) = 37 % 10 = 7 → Store at bucket 7
  h(48) = 48 % 10 = 8 → Store at bucket 8
  h(72) = 72 % 10 = 2 → Store at bucket 2
  h(56) = 56 % 10 = 6 → Store at bucket 6
  
  Hash Table:
  Index: [0]  [1]  [2]  [3]  [4]  [5]  [6]  [7]  [8]  [9]
  Value:  —    —   72    —    —   15   56   37   48    —
                        (15 and 25 both want slot 5 → COLLISION!)
```

### Hash Table Operations — Average Case O(1):
```
SEARCH (lookup):
  1. Compute h(key)
  2. Go to table[h(key)]
  3. Check if element is there → O(1) average

INSERT:
  1. Compute h(key)
  2. Go to table[h(key)]
  3. Insert element → O(1) average

DELETE:
  1. Compute h(key)
  2. Go to table[h(key)]
  3. Remove element → O(1) average

WHY AVERAGE O(1)? Because hash function gives DIRECT address!
No searching — just compute and go.
```

---

## 🔷 SECTION 6: COLLISION — The Problem and Solutions

### What is a Collision?

```
COLLISION: When two DIFFERENT keys produce the SAME hash value.

Example: h(key) = key % 10
  h(15) = 5
  h(25) = 5  ← COLLISION! 15 and 25 both hash to 5

COLLISION IS INEVITABLE (Pigeonhole Principle):
  If you have MORE KEYS than BUCKETS, at least one bucket must hold multiple keys.
  Even with a perfect hash function, collisions occur in practice.

Example: 100 possible keys, 10 buckets
  At minimum, some buckets must hold ~10 keys each.
  By Birthday Paradox: with just 23 elements in 365 buckets,
  probability of collision exceeds 50%!
```

### Collision Resolution Method 1: CHAINING (Separate Chaining)

```
IDEA: Each bucket holds a LINKED LIST of all keys that hash to that bucket.
      When collision occurs — just ADD to the linked list at that bucket.

VISUAL EXAMPLE:
  Hash function: h(key) = key % 7
  Insert: 50, 700, 76, 85, 92, 73, 101

  h(50)  = 50  % 7 = 1
  h(700) = 700 % 7 = 0
  h(76)  = 76  % 7 = 6
  h(85)  = 85  % 7 = 1  ← COLLISION with 50! (both → bucket 1)
  h(92)  = 92  % 7 = 1  ← COLLISION again! (→ bucket 1)
  h(73)  = 73  % 7 = 3
  h(101) = 101 % 7 = 3  ← COLLISION with 73! (both → bucket 3)

  Hash Table with Chaining:
  
  Bucket 0: [700] → NULL
  Bucket 1: [50] → [85] → [92] → NULL   ← Chain of 3 elements!
  Bucket 2: NULL
  Bucket 3: [73] → [101] → NULL         ← Chain of 2 elements!
  Bucket 4: NULL
  Bucket 5: NULL
  Bucket 6: [76] → NULL

SEARCH in chaining:
  Find 92:
    Compute h(92) = 1 → go to Bucket 1
    Scan linked list: 50 ≠ 92, 85 ≠ 92, 92 = 92 → FOUND!
    
PROPERTIES of Chaining:
  → Easy to implement
  → No limit on number of elements (linked list grows)
  → Search/Insert: O(1) average; O(n) worst case (all in one chain)
  → Uses extra memory for pointers
  → Java's HashMap uses chaining (with balanced BST/TreeMap for long chains)
```

### Collision Resolution Method 2: OPEN ADDRESSING

```
IDEA: All elements stored IN THE HASH TABLE ITSELF — no external lists.
      On collision, PROBE for another empty slot in the table.
      Three probing strategies:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2a. LINEAR PROBING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
If slot h(key) is occupied, try:
  h(key)+1, h(key)+2, h(key)+3, ...
  (wrap around using modulo)

Probe sequence: (h(key) + i) % m   for i = 0, 1, 2, ...

EXAMPLE: Table size = 10, h(key) = key % 10
  Insert 15 → h(15)=5 → Slot 5 empty → store at 5
  Insert 25 → h(25)=5 → Slot 5 OCCUPIED → try slot 6 → empty → store at 6
  Insert 35 → h(35)=5 → Slot 5 OCCUPIED → try 6 (occupied) → try 7 → store at 7

  Table: [_, _, _, _, _, 15, 25, 35, _, _]
                          0   1   2
                          (Linear probing filled slots 5,6,7)

PROBLEM: PRIMARY CLUSTERING
  Consecutive occupied slots grow into long "clusters"
  Performance degrades as table fills up

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2b. QUADRATIC PROBING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Probe sequence: (h(key) + i²) % m   for i = 0, 1, 2, ...
Try: h+0, h+1, h+4, h+9, h+16, ...

Reduces primary clustering but may miss some slots (SECONDARY CLUSTERING)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2c. DOUBLE HASHING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Probe sequence: (h(key) + i × h₂(key)) % m
Uses a SECOND hash function h₂(key) to compute step size

Best among open addressing — minimizes both primary and secondary clustering
Most complex to implement

COMPARISON of Open Addressing Methods:
  Linear Probing:    Simple; primary clustering problem
  Quadratic Probing: Reduces clustering; may cycle back
  Double Hashing:    Best; eliminates clustering; complex
```

---

## 🔷 SECTION 7: LOAD FACTOR

```
LOAD FACTOR (λ or α) = n / m

where:
  n = number of elements currently in hash table
  m = size (capacity) of hash table

INTERPRETATION:
  λ = 0.1 → Table is 10% full → very few collisions → fast
  λ = 0.5 → Table is 50% full → moderate collisions → acceptable
  λ = 0.75 → Table is 75% full → Java HashMap rehashes at this point!
  λ = 1.0 → Table is 100% full → many collisions → slow
  λ > 1.0 → Only possible with chaining (not open addressing)

PERFORMANCE vs LOAD FACTOR:
  Low λ  → Few collisions → O(1) average search (ideal)
  High λ → Many collisions → approaches O(n) in worst case

REHASHING:
  When load factor exceeds threshold, create a NEW LARGER TABLE
  and RE-INSERT all elements using new hash function.
  Java HashMap: rehashes when λ > 0.75 (default)
  New size: typically doubled (next prime above 2m)

🎯 PYQ FACT: Java HashMap's default load factor is 0.75 (75%).
             This balances time and space efficiency.
```

---

## 🔷 SECTION 8: Hashing — Complexity Summary

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Operation      | Average Case | Worst Case | Condition
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Insert         | O(1)         | O(n)       | All keys in 1 bucket
Search         | O(1)         | O(n)       | Chain traversal
Delete         | O(1)         | O(n)       | Chain traversal
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Worst case only when ALL keys hash to SAME bucket!
With good hash function → average case O(1) is reliable.
```

---

## 🔷 SECTION 9: MASTER COMPARISON — Search Techniques

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Property          | Linear    | Binary    | Hash Table
                  | Search    | Search    | (Hashing)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Best Case         | O(1)      | O(1)      | O(1)
Average Case      | O(n)      | O(log n)  | O(1)  ← BEST!
Worst Case        | O(n)      | O(log n)  | O(n)  (bad hash fn)
Space             | O(1)      | O(1)      | O(n)  (for table)
Sorted Required?  | NO        | YES       | NO
Implementation    | Simple    | Moderate  | Complex
Ordered output?   | YES       | YES       | NO (unordered)
Works on LL?      | YES       | NO        | N/A
Use for range     | YES       | YES       | NO
  queries?
Best for          | Small/    | Large     | Frequent
                  | unsorted  | sorted    | lookups
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

WHEN TO USE WHICH:
→ Need simple search, small data, or single search → LINEAR SEARCH
→ Data is sorted, large, multiple searches needed → BINARY SEARCH
→ Need FASTEST possible search/insert/delete, order unimportant → HASHING
→ Need to maintain sorted order → LINEAR or BINARY (not hashing)
→ Range queries (find all elements between x and y) → BINARY SEARCH (not hashing)
```

### 🚨 PYQ TRAP #3: Hashing vs Binary Search for "Fastest Search"
> For average case: **Hash Table wins** with O(1) vs Binary Search's O(log n).
> But Binary Search is **predictable** (always O(log n)), while Hash Table's worst case is O(n).
> Hashing cannot support RANGE QUERIES or SORTED ORDER output.
> **Exam answer: Hash Table provides the BEST average case O(1) for search.**

### 🚨 PYQ TRAP #4: Applications of Each
```
Use HASHING for:
  → Database indexing (exact key lookups)
  → Spell checkers (word exists? yes/no)
  → Password storage (storing hashed passwords)
  → Caching (key-value stores like memcached)
  → Symbol tables in compilers

Use BINARY SEARCH for:
  → Sorted telephone directory lookup
  → Finding insertion position in sorted array
  → Searching in sorted database with range queries
  → Version control (git bisect uses binary search!)

Use LINEAR SEARCH for:
  → Tiny arrays (n < 10)
  → Unsorted data with single search
  → Linked list traversal
```

---

# PART 2: GENERAL STUDIES
## 🏆 Nobel Prize Winners — Comprehensive Guide

---

## 🔷 SECTION 1: What is the Nobel Prize?

```
NOBEL PRIZE:
  Founded by: Alfred Nobel (Swedish inventor of dynamite)
  Year established: 1895 (in Alfred Nobel's will)
  First awarded: 1901
  Administered by: Nobel Foundation, Stockholm, Sweden

ALFRED NOBEL:
  Born: 21 October 1833, Stockholm, Sweden
  Died: 10 December 1896
  Invention: Dynamite (1867) — made him wealthy
  Concern: That his invention caused destruction, he created the Nobel Peace Prize
  Nobel Prizes are awarded annually on 10 December — his death anniversary

SIX PRIZE CATEGORIES:
  1. Physics
  2. Chemistry
  3. Physiology or Medicine
  4. Literature
  5. Peace
  6. Economic Sciences (full name: Sveriges Riksbank Prize — NOT in original will!)
  
🎯 PYQ: Economics Prize was added in 1969 — it is NOT one of the original 5 prizes!
         The original 5 prizes began in 1901. Economics was added much later.

PRIZE DETAILS:
  Awarded by:   Royal Swedish Academy of Sciences (Physics, Chemistry, Economics)
                Nobel Assembly at Karolinska Institute (Medicine)
                Swedish Academy (Literature)
                Norwegian Nobel Committee (Peace — given in OSLO, Norway, not Stockholm!)
  Prize amount: ~10 million Swedish Kronor (~₹8 crore) per prize
  Maximum recipients per prize: 3 people in one year
```

### 🎯 PYQ FACT: Peace Prize is given in OSLO (Norway), all others in STOCKHOLM (Sweden).

---

## 🔷 SECTION 2: Indian Nobel Prize Winners

### COMPLETE LIST — ALL INDIAN NOBEL LAUREATES:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Name                | Year | Field        | Reason/Key Work
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Rabindranath Tagore | 1913 | Literature   | Gitanjali (Song Offerings)
C.V. Raman          | 1930 | Physics      | Raman Effect (light scattering)
Har Gobind Khorana  | 1968 | Medicine     | Genetic code interpretation
Mother Teresa       | 1979 | Peace        | Work with the poor in Calcutta
Subramanyan         |      |              |
  Chandrasekhar     | 1983 | Physics      | Chandrasekhar Limit (white dwarfs)
Amartya Sen         | 1998 | Economics    | Welfare economics, social choice
V.S. Naipaul        | 2001 | Literature   | Born in Trinidad, Indian heritage
Venkatraman         |      |              |
  Ramakrishnan      | 2009 | Chemistry    | Structure of ribosome
Kailash Satyarthi   | 2014 | Peace        | Children's rights, anti-child labour
Abhijit Banerjee    | 2019 | Economics    | Experimental approach to poverty
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🔷 SECTION 3: Detailed Profiles — Top Exam Priority

---

### 🌟 1. RABINDRANATH TAGORE (1913) — LITERATURE

```
Full Name:    Rabindranath Tagore
Born:         7 May 1861, Calcutta (now Kolkata), Bengal
Died:         7 August 1941
Nobel Year:   1913
Field:        Literature

WHY AWARDED:
  For "Gitanjali" (Song Offerings) — a collection of deeply spiritual poems
  Translated into English by Tagore himself
  Swedish Academy praised his "profoundly sensitive, fresh and beautiful verse"

KEY FACTS:
  ✅ FIRST ASIAN to win the Nobel Prize (in any field)
  ✅ FIRST NON-EUROPEAN Nobel Prize winner in Literature
  ✅ Indian National Anthem: "Jana Gana Mana" — written by Tagore
  ✅ Bangladesh National Anthem: "Amar Sonar Bangla" — also written by Tagore!
     (One person wrote national anthems of TWO countries!)
  ✅ Called "Gurudev" — revered as a poet, philosopher, painter, musician
  ✅ Founded Visva-Bharati University at Shantiniketan, West Bengal (1921)
  ✅ Knighthood: Received from British (1915) but RETURNED it in 1919
     (Protest against Jallianwala Bagh Massacre)

MAJOR WORKS:
  Gitanjali (1910 Bengali; 1912 English translation)
  Gora, Ghare-Baire (The Home and the World)
  Rabindra Sangeet — unique genre of ~2,230 songs

🎯 PYQ MOST TESTED: First Asian Nobel laureate; wrote national anthems
                    of BOTH India AND Bangladesh.
```

---

### 🌟 2. C.V. RAMAN (1930) — PHYSICS

```
Full Name:    Sir Chandrasekhara Venkata Raman
Born:         7 November 1888, Tiruchirapalli, Tamil Nadu
Died:         21 November 1970
Nobel Year:   1930
Field:        Physics

WHY AWARDED:
  Discovery of the RAMAN EFFECT (1928)
  When light passes through a transparent material,
  some scattered light changes its WAVELENGTH (frequency).
  This change in wavelength provides a "fingerprint" of the material.

THE RAMAN EFFECT EXPLAINED:
  Normal scattering: light bounces off molecule, wavelength unchanged (Rayleigh scattering)
  Raman scattering: light interacts with molecule's vibrations → wavelength CHANGES
  
  This discovery was made using simple equipment — a mercury lamp and sunlight!
  Announced on: 28 February 1928

KEY FACTS:
  ✅ FIRST INDIAN to win Nobel Prize in Science
  ✅ FIRST ASIAN to win Nobel in Physics
  ✅ 28 February celebrated as NATIONAL SCIENCE DAY (day of Raman Effect discovery)
  ✅ Founded: Raman Research Institute, Bengaluru (1948)
  ✅ Also founder of Indian Academy of Sciences (1934)
  ✅ Awarded Bharat Ratna in 1954
  ✅ Application: Raman spectroscopy used in medicine, chemistry, forensics today

RAMAN EFFECT APPLICATIONS:
  → Identifying chemical compounds
  → Cancer detection (non-invasive)
  → Authentication of precious gems
  → Food quality testing
  → Pharmaceutical drug analysis

🎯 PYQ MOST TESTED: National Science Day = 28 February (Raman Effect discovery)
                    First Indian to win Nobel in Science.
```

---

### 🌟 3. MOTHER TERESA (1979) — PEACE

```
Full Name:    Anjezë Gonxhe Bojaxhiu (Mother Teresa)
Born:         26 August 1910, Skopje (now North Macedonia — then Ottoman Empire)
Died:         5 September 1997, Calcutta
Nobel Year:   1979
Field:        Peace

WHY AWARDED:
  "For work undertaken in the struggle to overcome poverty and distress,
  which also constitutes a threat to peace."
  Decades of service to the poorest of the poor in Calcutta.

KEY FACTS:
  ✅ Born in Skopje (now capital of North Macedonia) to Albanian parents
     → NOT born in India! But spent most of her life in India
  ✅ Came to India: 1929 (to teach at Loreto School, Calcutta)
  ✅ Founded: Missionaries of Charity (1950) in Calcutta
  ✅ The organisation runs orphanages, hospices, schools across 130+ countries
  ✅ Indian citizenship: Became Indian citizen
  ✅ Bharat Ratna: Awarded in 1980 (the year after Nobel)
  ✅ Beatified: 2003 (by Pope John Paul II)
  ✅ Canonised (made Saint): 4 September 2016 (by Pope Francis)
     → Now officially "Saint Teresa of Calcutta"
  ✅ NOTABLE: She REFUSED to invite media to visit her operations for first 20 years!

🎯 PYQ TRAP: Mother Teresa was born in Skopje (North Macedonia), NOT India!
             She was Albanian by ethnicity, Indian by citizenship.
             Missionaries of Charity founded in 1950.
```

---

### 🌟 4. AMARTYA SEN (1998) — ECONOMICS

```
Full Name:    Amartya Kumar Sen
Born:         3 November 1933, Santiniketan, West Bengal
Nobel Year:   1998
Field:        Economic Sciences

WHY AWARDED:
  "For his contributions to welfare economics"
  Specifically: Arrow's impossibility theorem extension,
                Theory of social choice and collective welfare,
                Famine analysis, Human Development Index (HDI)

KEY CONTRIBUTIONS:
  ✅ FAMINE ANALYSIS: Showed that famines are NOT caused by food shortage
     but by DISTRIBUTION FAILURES (people lack entitlement/access to food)
     Classic work: "Poverty and Famines" (1981)
     Used Bengal Famine 1943 as case study: food was available, but poor couldn't afford it!
  
  ✅ HDI (Human Development Index):
     Contributed to creation of UNDP's HDI (along with Mahbub ul Haq)
     HDI measures: GDP per capita + Education + Life expectancy
     (Goes beyond pure economic growth to measure human well-being)
  
  ✅ CAPABILITY APPROACH:
     Development = freedom to lead lives people value
     Poverty = deprivation of basic capabilities, not just income
  
  ✅ GENDER INEQUALITY research: "Missing Women" theory
     Showed systematic discrimination causes fewer women in Asia than expected

HONOURS:
  Bharat Ratna (1999 — year after Nobel)
  Lamont University Professor at Harvard University
  Former Master, Trinity College, Cambridge
  President: International Economic Association

🎯 PYQ TESTED: Famine theory (distribution not shortage), HDI, Welfare Economics
               "Poverty and Famines" is his most cited work.
```

---

### 🌟 5. HAR GOBIND KHORANA (1968) — MEDICINE

```
Full Name:    Har Gobind Khorana
Born:         9 January 1922, Raipur (now in Pakistan — British India)
Died:         9 November 2011
Nobel Year:   1968
Field:        Physiology or Medicine (shared with Robert Holley and Marshall Nirenberg)

WHY AWARDED:
  For interpretation of the GENETIC CODE and its function in protein synthesis
  Showed how the sequence of nucleotides in DNA determines the amino acid
  sequence in proteins (the code of life!)
  
KEY FACTS:
  ✅ Born in Raipur, Punjab (now in Pakistan)
  ✅ Became American citizen — worked at University of Wisconsin, then MIT
  ✅ First person to chemically synthesise an oligonucleotide
  ✅ Pioneered work on DNA and RNA structure
  ✅ Shared Nobel with Holley and Nirenberg

🎯 PYQ: Khorana won for MEDICINE (not Chemistry), for genetic code work.
```

---

### 🌟 6. SUBRAHMANYAN CHANDRASEKHAR (1983) — PHYSICS

```
Full Name:    Subrahmanyan Chandrasekhar (Chandra)
Born:         19 October 1910, Lahore (British India)
Died:         21 August 1995
Nobel Year:   1983
Field:        Physics (shared with William Fowler)

WHY AWARDED:
  For theoretical studies of the physical processes important to stellar structure
  and evolution — specifically the CHANDRASEKHAR LIMIT.

CHANDRASEKHAR LIMIT:
  Maximum mass a WHITE DWARF star can have = 1.4 solar masses
  If a star's remnant exceeds this → it collapses into a NEUTRON STAR or BLACK HOLE
  
  Chandra calculated this at AGE 19 on a ship voyage to England (1930)!
  Initially rejected by Sir Arthur Eddington → later proven correct.
  Today, the limit is fundamental to understanding stellar evolution and supernovae.

KEY FACTS:
  ✅ Born in Lahore, now Pakistan
  ✅ Nephew of C.V. Raman (both Indian Nobel laureates!)
  ✅ NASA's Chandra X-ray Observatory named in his honour
  ✅ Worked at University of Chicago from 1937 until death

🎯 PYQ: Chandrasekhar Limit = 1.4 solar masses; nephew of C.V. Raman.
```

---

### 🌟 7. V.S. NAIPAUL (2001) — LITERATURE

```
Full Name:    Sir Vidiadhar Surajprasad Naipaul
Born:         17 August 1932, Chaguanas, Trinidad
Died:         11 August 2018
Nobel Year:   2001
Field:        Literature

WHY AWARDED:
  "For having united perceptive narrative and incorruptible scrutiny in
  works that compel us to see the presence of suppressed histories."

KEY FACTS:
  Born in TRINIDAD (not India) — of Indian descent (his grandfather emigrated from UP)
  British citizen
  Major works: A House for Mr. Biswas, A Bend in the River, India: A Wounded Civilisation

🎯 PYQ: Naipaul is of Indian origin but NOT an Indian citizen — born in Trinidad.
```

---

### 🌟 8. VENKATRAMAN RAMAKRISHNAN (2009) — CHEMISTRY

```
Full Name:    Venkatraman "Venki" Ramakrishnan
Born:         1952, Chidambaram, Tamil Nadu
Nobel Year:   2009
Field:        Chemistry (shared with Thomas Steitz and Ada Yonath)

WHY AWARDED:
  For studies of the STRUCTURE AND FUNCTION OF THE RIBOSOME
  (Ribosomes are the cell's protein factories — decode RNA to make proteins)
  Used X-ray crystallography to map ribosome at atomic detail.

KEY FACTS:
  ✅ Born in Tamil Nadu but works in UK (MRC Laboratory of Molecular Biology, Cambridge)
  ✅ British and American citizen
  ✅ President of the Royal Society (2015-2020)
  ✅ Knighted in 2012 (Sir Venki Ramakrishnan)

🎯 PYQ: Ramakrishnan won Nobel in CHEMISTRY (not Medicine), for ribosome structure.
```

---

### 🌟 9. KAILASH SATYARTHI (2014) — PEACE

```
Full Name:    Kailash Satyarthi
Born:         11 January 1954, Vidisha, Madhya Pradesh
Nobel Year:   2014
Field:        Peace (shared with Malala Yousafzai from Pakistan)

WHY AWARDED:
  For their struggle against the suppression of children and young people
  and for the right of all children to education.

KEY FACTS:
  ✅ BACHPAN BACHAO ANDOLAN (BBA): Movement he founded in 1980
     ("Save Childhood Movement" — rescues children from bonded labour)
  ✅ Has freed over 85,000 children from exploitation and trafficking
  ✅ RUGMARK (now GoodWeave): Label certifying carpets made without child labour
  ✅ Received Nobel jointly with Malala Yousafzai (youngest-ever Nobel laureate)
  ✅ First Indian RESIDENT to receive Nobel Prize since Mother Teresa (1979)
     (Others like Amartya Sen, Khorana, Chandrasekhar were based abroad)

NOTABLE: The 2014 Nobel Peace Prize was shared between an INDIAN (Satyarthi)
         and a PAKISTANI (Malala Yousafzai) — a powerful symbolic gesture.

🎯 PYQ: Bachpan Bachao Andolan; shared Nobel with Malala Yousafzai.
```

---

### 🌟 10. ABHIJIT BANERJEE (2019) — ECONOMICS

```
Full Name:    Abhijit Vinayak Banerjee
Born:         21 February 1961, Mumbai (raised in Calcutta)
Nobel Year:   2019
Field:        Economic Sciences (shared with Esther Duflo and Michael Kremer)

WHY AWARDED:
  "For their experimental approach to alleviating global poverty"
  Used RANDOMISED CONTROL TRIALS (RCTs) — like medical trials — to test
  what actually works in fighting poverty.

KEY FACTS:
  ✅ Married to Esther Duflo (they shared the Nobel together!)
     Esther Duflo = only second woman to win Nobel in Economics
  ✅ Professor at MIT (Massachusetts Institute of Technology)
  ✅ Co-founded J-PAL (Abdul Latif Jameel Poverty Action Lab) at MIT
  ✅ Book: "Poor Economics" (with Esther Duflo) — explains their approach
  ✅ American citizen (of Indian origin)

FAMOUS WORK:
  Used RCTs in villages of India and Africa to test:
  → Do free textbooks improve learning? (often no — teacher quality matters more!)
  → Do deworming tablets improve school attendance? (yes, significantly)
  → What's the best way to distribute aid?

🎯 PYQ: Experimental approach to poverty (RCTs); co-recipient = wife Esther Duflo;
         Founded J-PAL at MIT.
```

---

## 🔷 SECTION 4: Recent Nobel Prize Winners (2020-2024) — Brief Reference

```
YEAR | FIELD     | WINNER(S)                            | REASON
2020 | Peace     | World Food Programme (WFP)           | Efforts to combat hunger
2020 | Literature| Louise Glück (USA)                   | Poetry
2021 | Peace     | Maria Ressa + Dmitry Muratov         | Freedom of press
2021 | Economics | Card, Angrist, Imbens                | Empirical labour economics
2022 | Peace     | Memorial (Russia), Ukraine orgs +    | Civil society, human rights
                   Ales Bialiatski (Belarus)
2022 | Physics   | Aspect, Clauser, Zeilinger           | Quantum entanglement
2023 | Medicine  | Katalin Karikó + Drew Weissman       | mRNA vaccine development (COVID!)
2023 | Literature| Jon Fosse (Norway)                   | Plays and prose
2023 | Economics | Claudia Goldin (USA)                 | Women's labour market outcomes
2024 | Physics   | Hopfield + Hinton                    | Artificial Neural Networks (AI!)
2024 | Chemistry | Baker, Hassabis, Jumper (DeepMind)  | Protein structure prediction (AlphaFold!)
2024 | Peace     | Nihon Hidankyo (Japan)               | Atomic bomb survivors' group
2024 | Economics | Acemoglu, Johnson, Robinson          | Institutions and prosperity

🎯 PYQ 2024 HIGHLIGHT: Nobel Physics 2024 for AI/Neural Networks (Hinton = "Godfather of AI")
                        Nobel Chemistry 2024 for protein structure (AlphaFold by Google DeepMind)
```

---

## 🔷 SECTION 5: Nobel Prize — Quick Reference by Fields

```
PHYSICS NOTABLE:
  Albert Einstein (1921): Photoelectric effect
  Marie Curie (1903): Radioactivity (also Chemistry 1911)
  C.V. Raman (1930): Raman Effect
  Chandrasekhar (1983): Chandrasekhar Limit

CHEMISTRY NOTABLE:
  Ramakrishnan (2009): Ribosome structure

MEDICINE NOTABLE:
  Har Gobind Khorana (1968): Genetic code

LITERATURE NOTABLE:
  Tagore (1913): Gitanjali
  V.S. Naipaul (2001): Narrative works

PEACE NOTABLE:
  Mother Teresa (1979): Work with poor
  Kailash Satyarthi (2014): Child rights

ECONOMICS NOTABLE:
  Amartya Sen (1998): Welfare economics
  Abhijit Banerjee (2019): Poverty experiments
```

### Memory Trick — Indian Nobel Winners Timeline:
```
"Tagore Really Handled Medicine Carefully And Said Values Reach Beyond Acceptance"

T = Tagore (1913) — Literature
R = Raman (1930) — Physics
H = Har Gobind Khorana (1968) — Medicine
M = Mother Teresa (1979) — Peace
C = Chandrasekhar (1983) — Physics
A = Amartya Sen (1998) — Economics
S = Satyarthi Kailash (wait — V.S.) Naipaul (2001) — Literature
V = Venkatraman Ramakrishnan (2009) — Chemistry
R = (note: repeated V = now use "Reach") Kailash Satyarthi (2014) — Peace
B = Banerjee Abhijit (2019) — Economics
A = (completion)
```

**Simpler trick — Just remember YEARS: 1913, 1930, 1968, 1979, 1983, 1998, 2001, 2009, 2014, 2019**

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Linear Search, Binary Search, Hashing, Collision Resolution

---

**Q1.** What is the WORST CASE time complexity of Linear Search?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q2.** Binary Search can ONLY be applied when:
(A) The array contains only integers
(B) The array is sorted (ascending or descending)
(C) The array has no duplicate elements
(D) More than one of the above
(E) None of the above

---

**Q3.** For Binary Search on a sorted array of 1024 elements, the MAXIMUM number of comparisons needed is:
(A) 1024
(B) 512
(C) 10
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the formula for finding the MIDDLE index in Binary Search?
(A) mid = (low × high) / 2
(B) mid = (low + high) / 2
(C) mid = high - low
(D) More than one of the above
(E) None of the above

---

**Q5.** In Binary Search, if `arr[mid] < target`, the next step is:
(A) Search the LEFT half: high = mid - 1
(B) Search the RIGHT half: low = mid + 1
(C) Search entire array again
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the BEST CASE time complexity of Binary Search?
(A) O(log n)
(B) O(n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q7.** A hash function h(key) = key % 10 is applied to keys 23, 33, 43, 53. How many COLLISIONS occur?
(A) 0 (no collisions)
(B) 2 collisions (3 keys in same bucket)
(C) 3 collisions (all four keys hash to same bucket — 4 keys, 3 "extra" = 3 collisions)
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the AVERAGE CASE time complexity of searching in a HASH TABLE with a good hash function?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q9.** In CHAINING collision resolution, what data structure is typically used at each bucket?
(A) Stack
(B) Binary Search Tree
(C) Linked List
(D) More than one of the above
(E) None of the above

---

**Q10.** LOAD FACTOR of a hash table is defined as:
(A) Table size / Number of elements (m / n)
(B) Number of elements / Table size (n / m)
(C) Number of collisions / Table size
(D) More than one of the above
(E) None of the above

---

**Q11.** The WORST CASE time complexity of hash table search occurs when:
(A) The table is completely empty
(B) All keys hash to the SAME bucket (one long chain)
(C) The load factor is 0
(D) More than one of the above
(E) None of the above

---

**Q12.** Which collision resolution technique can suffer from PRIMARY CLUSTERING?
(A) Chaining
(B) Double Hashing
(C) Linear Probing
(D) More than one of the above
(E) None of the above

---

**Q13.** In LINEAR PROBING, if h(key) = 5 and slots 5, 6, 7 are occupied, the next probe is:
(A) Slot 4 (go backward)
(B) Slot 8 (continue forward)
(C) Slot 10 (jump by 5)
(D) More than one of the above
(E) None of the above

---

**Q14.** Which searching method is MOST EFFICIENT for a one-time search on an UNSORTED array of 10,000 elements?
(A) Binary Search
(B) Linear Search
(C) Hash-based search
(D) More than one of the above
(E) None of the above

---

**Q15.** Binary Search on a sorted array of n=100 elements requires at most how many comparisons?
(A) 7 (since log₂128 = 7)
(B) 10
(C) 50
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following CANNOT be efficiently implemented using a hash table?
(A) Finding if a key exists (membership test)
(B) Finding all elements in the range [x, y] (range query)
(C) Counting occurrences of elements
(D) More than one of the above
(E) None of the above

---

**Q17.** The SPACE COMPLEXITY of a hash table with n elements and m buckets is:
(A) O(1)
(B) O(log n)
(C) O(n + m) which simplifies to O(n) when m = O(n)
(D) More than one of the above
(E) None of the above

---

**Q18.** Java's HashMap rehashes when the load factor exceeds:
(A) 0.50 (50%)
(B) 1.00 (100%)
(C) 0.75 (75%)
(D) More than one of the above
(E) None of the above

---

**Q19.** Binary Search has a RECURSIVE version and an ITERATIVE version. The SPACE complexity difference is:
(A) Both O(1) — no difference
(B) Iterative: O(1); Recursive: O(log n) due to call stack
(C) Iterative: O(n); Recursive: O(1)
(D) More than one of the above
(E) None of the above

---

**Q20.** Which searching technique does NOT require the data to be sorted?
(A) Binary Search (iterative)
(B) Binary Search (recursive)
(C) Linear Search
(D) More than one of the above (Both A and B require sorted data, so only C doesn't)
(E) None of the above

---

**Q21.** In DOUBLE HASHING (open addressing), the probe sequence uses:
(A) A fixed step of 1 (linear increment)
(B) A quadratic increment (i²)
(C) A second hash function to compute the step size
(D) More than one of the above
(E) None of the above

---

**Q22.** What is the MINIMUM number of comparisons needed to determine that a target is NOT PRESENT in a sorted array of 8 elements using Binary Search?
(A) 8 (must check all)
(B) 1 (can determine in one step)
(C) 3 (log₂8 = 3, though may need 4)
(D) More than one of the above (3 or 4 comparisons needed in worst case)
(E) None of the above

---

**Q23.** The BIRTHDAY PARADOX in the context of hashing means:
(A) Hash tables were invented on someone's birthday
(B) Collisions are more likely than intuitively expected — even with few elements relative to table size
(C) Hash functions must use prime numbers for good distribution
(D) More than one of the above
(E) None of the above

---

**Q24.** Which property is ESSENTIAL for a hash function to be useful?
(A) It must use prime numbers
(B) The same key must ALWAYS produce the same hash value (deterministic)
(C) It must never produce collisions
(D) More than one of the above
(E) None of the above

---

**Q25.** For large datasets requiring FREQUENT insertions, deletions, and exact-key lookups (no range queries), which data structure provides the BEST AVERAGE CASE performance?
(A) Sorted Array (Binary Search)
(B) Unsorted Linked List
(C) Hash Table
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Nobel Prize Winners — Indian Laureates and General Facts

---

**Q26.** The Nobel Prize was established based on the will of:
(A) Albert Einstein
(B) Alfred Nobel
(C) Charles Darwin
(D) More than one of the above
(E) None of the above

---

**Q27.** Rabindranath Tagore won the Nobel Prize in Literature in which year?
(A) 1901
(B) 1913
(C) 1930
(D) More than one of the above
(E) None of the above

---

**Q28.** Tagore won the Nobel Prize for which work?
(A) Ghare-Baire (The Home and the World)
(B) Gitanjali (Song Offerings)
(C) Gora
(D) More than one of the above
(E) None of the above

---

**Q29.** Rabindranath Tagore is UNIQUE because:
(A) He was the first Nobel Prize winner ever
(B) He wrote the national anthems of both India AND Bangladesh
(C) He declined the Nobel Prize
(D) More than one of the above
(E) None of the above

---

**Q30.** C.V. Raman won the Nobel Prize in Physics in 1930 for:
(A) Discovery of the neutron
(B) Photoelectric effect
(C) Raman Effect (scattering of light)
(D) More than one of the above
(E) None of the above

---

**Q31.** India celebrates National Science Day on 28 February because:
(A) It is the birthday of C.V. Raman
(B) It is the day the Raman Effect was discovered (1928)
(C) It is India's first satellite launch date
(D) More than one of the above
(E) None of the above

---

**Q32.** Mother Teresa was born in:
(A) Calcutta, India
(B) Dhaka, Bangladesh
(C) Skopje (present-day North Macedonia)
(D) More than one of the above
(E) None of the above

---

**Q33.** Mother Teresa founded which organisation in Calcutta?
(A) Ramakrishna Mission
(B) Missionaries of Charity
(C) Salvation Army
(D) More than one of the above
(E) None of the above

---

**Q34.** The Nobel Peace Prize is awarded in which city (NOT Stockholm)?
(A) Copenhagen, Denmark
(B) Oslo, Norway
(C) Helsinki, Finland
(D) More than one of the above
(E) None of the above

---

**Q35.** Amartya Sen was awarded the Nobel Prize in Economics in 1998 primarily for his contributions to:
(A) Monetary policy and inflation control
(B) Welfare economics, social choice theory, and famine analysis
(C) International trade and globalisation theory
(D) More than one of the above
(E) None of the above

---

**Q36.** According to Amartya Sen's famine research, what is the PRIMARY cause of famines?
(A) Absolute shortage of food production
(B) Natural disasters like floods or droughts
(C) Failure of food distribution and entitlement (people unable to access food)
(D) More than one of the above
(E) None of the above

---

**Q37.** The Nobel Prize in Economics (Economic Sciences) was first awarded in:
(A) 1901 (along with other Nobel Prizes)
(B) 1969 (it was added later — NOT in Nobel's original will)
(C) 1950
(D) More than one of the above
(E) None of the above

---

**Q38.** Subrahmanyan Chandrasekhar and C.V. Raman share which connection?
(A) Both worked at the same university
(B) Chandrasekhar is C.V. Raman's nephew
(C) Both won Nobel Prize in the same year
(D) More than one of the above
(E) None of the above

---

**Q39.** The Chandrasekhar Limit (1.4 solar masses) is important because it determines:
(A) The speed of light in dense matter
(B) The maximum mass a white dwarf can have before collapsing into a neutron star or black hole
(C) The minimum temperature for nuclear fusion
(D) More than one of the above
(E) None of the above

---

**Q40.** Kailash Satyarthi won the 2014 Nobel Peace Prize. What was the name of his movement?
(A) Narmada Bachao Andolan
(B) Chipko Movement
(C) Bachpan Bachao Andolan
(D) More than one of the above
(E) None of the above

---

**Q41.** Who shared the 2014 Nobel Peace Prize with Kailash Satyarthi?
(A) Wangari Maathai
(B) Malala Yousafzai (from Pakistan)
(C) Aung San Suu Kyi
(D) More than one of the above
(E) None of the above

---

**Q42.** Abhijit Banerjee won the 2019 Nobel Prize in Economics along with his wife. What is her name?
(A) Esther Duflo
(B) Carmen Reinhart
(C) Claudia Goldin
(D) More than one of the above
(E) None of the above

---

**Q43.** Har Gobind Khorana won the Nobel Prize in 1968 in which field?
(A) Chemistry
(B) Physics
(C) Physiology or Medicine
(D) More than one of the above
(E) None of the above

---

**Q44.** Venkatraman Ramakrishnan won the 2009 Nobel Prize in Chemistry for studying:
(A) DNA double helix structure
(B) Structure and function of the ribosome
(C) Synthesis of ATP in mitochondria
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following Indian Nobel laureates was born OUTSIDE present-day India?
(A) Rabindranath Tagore
(B) Amartya Sen
(C) Subrahmanyan Chandrasekhar (born in Lahore, now Pakistan)
(D) More than one of the above (Chandrasekhar born in Lahore; Khorana born in Raipur, now Pakistan; Mother Teresa born in Skopje)
(E) None of the above

---

**Q46.** The Nobel Prize ceremony is held annually on which date?
(A) 21 October (Alfred Nobel's birthday)
(B) 10 December (Alfred Nobel's death anniversary)
(C) 1 January (New Year's Day)
(D) More than one of the above
(E) None of the above

---

**Q47.** Rabindranath Tagore returned his knighthood (given by British) in protest against which event?
(A) Partition of Bengal (1905)
(B) Jallianwala Bagh Massacre (1919)
(C) Simon Commission (1928)
(D) More than one of the above
(E) None of the above

---

**Q48.** The 2024 Nobel Prize in Physics was awarded for work related to:
(A) Quantum entanglement experiments
(B) Artificial Neural Networks and Machine Learning (AI foundations)
(C) Gravitational wave detection
(D) More than one of the above
(E) None of the above

---

**Q49.** J-PAL (Abdul Latif Jameel Poverty Action Lab), which uses randomised controlled trials to fight poverty, was co-founded by which Nobel laureate?
(A) Amartya Sen
(B) Kailash Satyarthi
(C) Abhijit Banerjee
(D) More than one of the above
(E) None of the above

---

**Q50.** Which statement is CORRECT about the Nobel Prize?
(A) A Nobel Prize can be awarded to a maximum of 5 individuals in any field in one year
(B) The Economics Nobel Prize is part of the original 5 prizes established by Alfred Nobel's will
(C) The Nobel Peace Prize is awarded in Oslo, Norway — unlike other prizes given in Stockholm
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
| 1 | (C) | Linear Search worst = O(n) — target at end or not found |
| 2 | (B) | Binary Search ONLY works on sorted arrays — fundamental precondition |
| 3 | (C) | log₂1024 = 10 comparisons maximum |
| 4 | (B) | mid = (low + high) / 2 — standard formula |
| 5 | (B) | arr[mid] < target means target is in RIGHT half → low = mid + 1 |
| 6 | (C) | Best case: target found at MIDDLE on first comparison → O(1) |
| 7 | (C) | All four keys (23,33,43,53) → % 10 = 3, so all go to bucket 3. First is free, next 3 cause collisions → 3 collisions |
| 8 | (C) | Hash table average case search = O(1) — direct address computation |
| 9 | (C) | Each bucket in chaining holds a linked list of colliding elements |
| 10 | (B) | Load factor = n/m (elements/buckets) — measures fullness |
| 11 | (B) | Worst case: all keys in one bucket → linear scan of that chain → O(n) |
| 12 | (C) | Linear Probing: consecutive occupied slots form clusters → primary clustering |
| 13 | (B) | Linear Probing: try next slot = 8 (linear progression: 5,6,7 occupied → try 8) |
| 14 | (B) | For UNSORTED + ONE-TIME search: Linear Search avoids sorting overhead |
| 15 | (A) | log₂100 ≈ 6.6, so at most 7 comparisons (log₂128 = 7 is the ceiling) |
| 16 | (B) | Hash tables cannot efficiently answer range queries [x,y] — no ordering |
| 17 | (C) | Space = O(n+m); when m = O(n), simplifies to O(n) |
| 18 | (C) | Java HashMap default load factor = 0.75; rehashes when exceeded |
| 19 | (B) | Iterative: O(1) space; Recursive: O(log n) call stack |
| 20 | (C) | Only Linear Search works on unsorted data — Binary Search needs sorted array |
| 21 | (C) | Double Hashing uses second hash function h₂(key) as step size |
| 22 | (D) | For n=8, log₂8=3 levels, but finding "not present" needs 3 or 4 comparisons |
| 23 | (B) | Birthday Paradox: collisions happen much sooner than people expect |
| 24 | (B) | Determinism is ESSENTIAL — same key must always give same hash value |
| 25 | (C) | Hash Table: O(1) average for all three operations (insert, delete, search) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Alfred Nobel — Swedish inventor of dynamite; prize named after him |
| 27 | (B) | Tagore won in 1913 — first Asian Nobel laureate |
| 28 | (B) | Gitanjali (Song Offerings) — English translation of Bengali poetry collection |
| 29 | (B) | Tagore wrote national anthems of BOTH India (Jana Gana Mana) and Bangladesh |
| 30 | (C) | Raman Effect = inelastic scattering of light (wavelength change) |
| 31 | (B) | 28 February 1928 = day Raman Effect was announced → National Science Day |
| 32 | (C) | Born in Skopje (now capital of North Macedonia) to Albanian parents |
| 33 | (B) | Missionaries of Charity — founded 1950 in Calcutta |
| 34 | (B) | Nobel Peace Prize given in OSLO, Norway — all others in Stockholm, Sweden |
| 35 | (B) | Welfare economics, social choice, and groundbreaking famine analysis |
| 36 | (C) | Sen showed famines stem from distribution failures, not food shortages |
| 37 | (B) | Economics Nobel started 1969 — NOT in Alfred Nobel's original 1895 will |
| 38 | (B) | Chandrasekhar is C.V. Raman's nephew — both Indian physics Nobel laureates |
| 39 | (B) | Above 1.4 solar masses → white dwarf collapses to neutron star/black hole |
| 40 | (C) | Bachpan Bachao Andolan (Save Childhood Movement) — founded 1980 |
| 41 | (B) | Malala Yousafzai (Pakistan) — youngest Nobel laureate ever |
| 42 | (A) | Esther Duflo — French-American economist; husband-wife Nobel duo |
| 43 | (C) | Khorana won Physiology or Medicine for genetic code interpretation |
| 44 | (B) | Ribosome structure using X-ray crystallography |
| 45 | (D) | Chandrasekhar (Lahore, now Pakistan), Khorana (Raipur, now Pakistan), Mother Teresa (Skopje, North Macedonia) — all three born outside present India |
| 46 | (B) | 10 December — Alfred Nobel's death anniversary (died 1896) |
| 47 | (B) | Jallianwala Bagh Massacre, April 1919 — Tagore returned knighthood in protest |
| 48 | (B) | 2024 Nobel Physics: John Hopfield + Geoffrey Hinton for neural networks/AI |
| 49 | (C) | Abhijit Banerjee co-founded J-PAL at MIT with Esther Duflo |
| 50 | (C) | Peace Prize in Oslo is the KEY distinguishing fact (max 3 per prize, Economics not original) |

---
---

# 🔁 DAY 32 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Searching Algorithms & Hashing

### Search Algorithm Complexity (Memorise All):
```
Algorithm      | Best   | Average  | Worst  | Precondition
---------------|--------|----------|--------|-------------
Linear Search  | O(1)   | O(n)     | O(n)   | None — works on unsorted
Binary Search  | O(1)   | O(log n) | O(log n)| SORTED array required!
Hash Search    | O(1)   | O(1)     | O(n)   | Hash table set up
```

### Binary Search — 5 Iron Rules:
```
Rule 1: Array MUST be sorted — ABSOLUTE REQUIREMENT
Rule 2: Formula: mid = (low + high) / 2
Rule 3: arr[mid] < target → LOW = mid + 1  (go RIGHT)
Rule 4: arr[mid] > target → HIGH = mid - 1 (go LEFT)
Rule 5: low > high → return -1 (not found)
Max comparisons for n elements = ⌈log₂n⌉ + 1
```

### Hashing — Key One-Liners:
```
Hash function:    Converts key → index (address) in O(1)
Collision:        Two keys → same hash value (inevitable!)
Chaining:         Each bucket = linked list of colliding elements
Linear Probing:   On collision, try next slot (primary clustering risk!)
Double Hashing:   Second hash function determines step (best open addressing)
Load Factor λ:    n/m = elements/buckets; Java HashMap rehashes at λ > 0.75
Hash Table ops:   O(1) average for search, insert, delete
Hash Table limit: CANNOT do range queries; NO ordering maintained
```

### Common Exam Traps:
```
TRAP 1: "Binary Search is O(n) worst case" → WRONG! It's O(log n)
TRAP 2: "Hash table is ALWAYS O(1)" → WRONG! Worst case = O(n)
TRAP 3: "Linear Search is always O(n)" → WRONG! Best case = O(1)
TRAP 4: "Binary Search works on unsorted arrays" → WRONG! Must be sorted
TRAP 5: "Load factor > 1 is impossible" → WRONG! Only impossible in open addressing,
         not chaining (chain can grow beyond 1 per bucket)
TRAP 6: For ONE-TIME search on unsorted data → use LINEAR SEARCH (not binary)
         Sorting first would cost O(n log n) — worse than O(n) linear!
```

---

## ⚡ RAPID FIRE — Nobel Prize Winners

### Indian Nobel Laureates — The Complete List (By Year):
```
1913 — TAGORE     — Literature   — Gitanjali — First Asian Nobel
1930 — RAMAN      — Physics      — Raman Effect — First Indian Nobel in Science
1968 — KHORANA    — Medicine     — Genetic code
1979 — TERESA     — Peace        — Missionaries of Charity
1983 — CHANDRASEKHAR — Physics   — Chandrasekhar Limit (1.4 solar masses)
1998 — AMARTYA SEN — Economics  — Welfare economics, famine theory
2001 — NAIPAUL    — Literature   — Born in Trinidad (Indian origin)
2009 — RAMAKRISHNAN — Chemistry — Ribosome structure
2014 — SATYARTHI  — Peace       — Bachpan Bachao Andolan; shared w/Malala
2019 — BANERJEE   — Economics   — Poverty RCTs; co-winner = wife Esther Duflo
```

### Critical PYQ Facts:
```
✅ First ASIAN Nobel: Tagore (1913) — Literature
✅ First INDIAN Nobel in SCIENCE: C.V. Raman (1930) — Physics
✅ National Science Day: 28 February (Raman Effect announcement, 1928)
✅ Tagore wrote anthems of INDIA + BANGLADESH (unique!)
✅ Mother Teresa born in SKOPJE (North Macedonia) — NOT India!
✅ Peace Prize in OSLO (Norway) — ALL others in STOCKHOLM (Sweden)
✅ Economics Nobel since 1969 — NOT in original 5 prizes (Nobel's will = 1895)
✅ Chandrasekhar = C.V. Raman's nephew
✅ Max 3 winners per prize per year
✅ Nobel ceremonies on 10 DECEMBER (Nobel's death anniversary)
✅ Economics Nobel: full name = "Sveriges Riksbank Prize in Economic Sciences"
✅ 2024 Nobel Physics = Hinton + Hopfield for Artificial Neural Networks (AI!)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Binary Search**: sorted array ONLY; mid = (low+high)/2; O(log n) worst case; O(1) best; n=1024 → max 10 comparisons
2. **Hashing**: O(1) average search/insert/delete; collision = two keys → same bucket; chaining = linked list per bucket; load factor = n/m; rehash when λ > 0.75
3. **Search hierarchy**: Hash O(1) avg > Binary O(log n) > Linear O(n); but hash can't do range queries and needs extra space
4. **Indian Nobel firsts**: Tagore 1913 (first Asian); Raman 1930 (first Indian in Science; 28 Feb = National Science Day); Mother Teresa born in Skopje NOT India
5. **Nobel structure**: 6 fields; Economics added 1969 (NOT original); Peace Prize in Oslo; others in Stockholm; ceremony on 10 December; max 3 winners/prize

---

## 📅 DAY 33 PREVIEW — What's Coming Next:
**CS**: Stack Data Structure — Definition, LIFO principle, push/pop operations, applications (expression evaluation, function calls, recursion), array and linked list implementation
**GS**: Indian Constitution — Parliament: Lok Sabha, Rajya Sabha, Powers, Bills, Sessions, Parliamentary Procedures

---

*🚀 Day 32 of 170 complete — Search smarter, not harder. Binary Search in 10 steps. Hash tables in 1 step. Nobel facts in memory!*
