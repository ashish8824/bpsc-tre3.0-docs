# 📅 BPSC TRE 4.0 — DAY 15 COMPLETE STUDY MATERIAL
## CS: Arrays as Data Structure | GS: Bihar Geography — Districts, Rivers & Physical Features
### Target: TOP RANK | Phase 1, Week 3

---

> **⚡ TOPPER MINDSET:** Arrays appear in **EVERY BPSC TRE paper** (TRE 1.0, 2.0, 3.0). Bihar Geography is asked in **6–8 GS questions** per paper. Master both today. No excuses.

---

# ═══════════════════════════════════════════════
# 🖥️ PART A — COMPUTER SCIENCE
## Topic: Arrays as a Data Structure
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A DATA STRUCTURE?

Before understanding arrays deeply, let us understand what a **Data Structure** actually is.

A **Data Structure** is a way of organizing, storing, and managing data in memory so that it can be accessed and modified efficiently.

```
DATA STRUCTURE CLASSIFICATION (BIG PICTURE)
============================================

                    DATA STRUCTURES
                          |
          ________________|________________
         |                                 |
     LINEAR                           NON-LINEAR
  (Sequential)                      (Hierarchical)
         |                                 |
   ______|______                    _______|_______
  |      |      |                  |               |
Array  Stack  Queue               Tree           Graph
       Linked List
```

Arrays are the **simplest and most fundamental** linear data structure.

---

## 📌 SECTION 2: ARRAY — DEFINITION & CORE CONCEPT

An **Array** is a collection of elements of the **same data type** stored in **contiguous (adjacent) memory locations**, accessed using a single name and an index (subscript).

### 🔑 Key Properties of Array:
| Property | Description |
|----------|-------------|
| **Same Data Type** | All elements must be of same type (int, float, char etc.) |
| **Contiguous Memory** | Elements stored one after another in memory |
| **Fixed Size** | Size declared at compile time (static) |
| **Index-based Access** | First element at index 0, last at index n-1 |
| **Random Access** | Any element accessible in O(1) time |

---

## 📌 SECTION 3: MEMORY REPRESENTATION (MOST IMPORTANT FOR PYQ)

This is the most tested concept. Understand it deeply.

```
ARRAY:  int A[5] = {10, 20, 30, 40, 50};

MEMORY MAP (Assuming Base Address = 1000, int = 2 bytes):
==========================================================

  Index:    [0]    [1]    [2]    [3]    [4]
           +------+------+------+------+------+
  Value:   | 10   | 20   | 30   | 40   | 50   |
           +------+------+------+------+------+
  Address: 1000   1002   1004   1006   1008

  Formula: Address of A[i] = Base_Address + (i × Size_of_DataType)
  
  Example: Address of A[3] = 1000 + (3 × 2) = 1000 + 6 = 1006  ✓
```

### 📐 Address Calculation Formula:
```
For 1D Array:
  Address(A[i]) = Base + (i × size)

For 2D Array — ROW MAJOR ORDER (C, C++, Java use Row Major):
  Address(A[i][j]) = Base + (i × n + j) × size
  (where n = number of columns)

For 2D Array — COLUMN MAJOR ORDER (FORTRAN uses Column Major):
  Address(A[i][j]) = Base + (j × m + i) × size
  (where m = number of rows)
```

> **🚨 PYQ TRAP:** BPSC frequently asks "which language uses Column Major order?" → Answer = **FORTRAN**. C, C++, Java use **Row Major** order.

---

## 📌 SECTION 4: TIME COMPLEXITY OF ARRAY OPERATIONS

This is the **#1 most-tested concept** about arrays in ALL three TRE papers.

```
ARRAY OPERATIONS — TIME COMPLEXITY TABLE
==========================================

  Operation               Best Case    Worst Case    Explanation
  ─────────────────────────────────────────────────────────────
  Access by Index         O(1)         O(1)          Direct calculation
  Search (Unsorted)       O(1)         O(n)          May need to check all
  Search (Sorted)         O(1)         O(log n)      Binary search
  Insertion at End        O(1)         O(1)          Just add at last position
  Insertion at Beginning  O(n)         O(n)          Shift all elements right
  Insertion at Middle     O(n)         O(n)          Shift elements after point
  Deletion from End       O(1)         O(1)          Just reduce size
  Deletion from Beginning O(n)         O(n)          Shift all elements left
  Deletion from Middle    O(n)         O(n)          Shift elements after point
```

```
WHY INSERTION AT MIDDLE IS O(n)?
=================================
Array: [10, 20, 30, 40, 50]  → Insert 25 at index 2

Step 1: [10, 20, 30, 40, 50, __]
Step 2: Shift right from index 2:
        [10, 20, 30, 30, 40, 50]  ← copied 30
        [10, 20, 30, 40, 40, 50]  ← WRONG, let me show properly:

        Move 50 → position 5
        Move 40 → position 4
        Move 30 → position 3
        [10, 20, __, 30, 40, 50]

Step 3: Insert 25 at index 2:
        [10, 20, 25, 30, 40, 50]  ✓

In worst case (insert at beginning), ALL n elements shift → O(n)
```

---

## 📌 SECTION 5: ADVANTAGES & DISADVANTAGES OF ARRAYS

### ✅ Advantages:
1. **Random Access in O(1)** — This is the PRIMARY advantage. Access any element directly using index.
2. **Cache Friendly** — Due to contiguous memory, spatial locality helps CPU cache perform better.
3. **Simple to use** — Simplest data structure.
4. **No extra memory** — No pointers needed (unlike linked lists).

### ❌ Disadvantages:
1. **Fixed Size** — Cannot grow or shrink dynamically (static arrays).
2. **Insertion/Deletion is costly** — O(n) due to shifting.
3. **Memory wastage** — If array is declared larger than needed, memory is wasted.
4. **Contiguous memory required** — Large arrays may fail if contiguous block not available.

---

## 📌 SECTION 6: ARRAYS vs LINKED LISTS (BPSC FAVORITE COMPARISON)

```
FEATURE COMPARISON TABLE
==========================

Feature              Array              Linked List
─────────────────────────────────────────────────────
Memory allocation    Contiguous         Non-contiguous
Access time          O(1) random        O(n) sequential
Insertion (middle)   O(n) — shifting    O(1) — if node known
Deletion (middle)    O(n) — shifting    O(1) — if node known
Memory per element   Only data          Data + pointer(s)
Cache performance    Excellent          Poor
Size                 Fixed (static)     Dynamic
Search               O(n) or O(log n)   O(n)
Memory overhead      Low                High (extra pointers)
```

> **🚨 PYQ TRAP:** "Which data structure provides O(1) access time?" → **Array**
> "Which data structure allows dynamic memory?" → **Linked List**
> "Which has better cache performance?" → **Array** (spatial locality)

---

## 📌 SECTION 7: SPATIAL LOCALITY & CACHE FRIENDLINESS (CONCEPTUAL)

```
WHY ARRAYS ARE CACHE-FRIENDLY
================================

CPU Cache works on principle of SPATIAL LOCALITY:
"If you access memory location X, you will likely access X+1, X+2 soon."

Array in Memory:
[A[0]][A[1]][A[2]][A[3]][A[4]] ← all adjacent in RAM

When CPU loads A[0], it loads A[0], A[1], A[2], A[3] into cache together.
Next access A[1] → Already in cache! FAST!

Linked List in Memory:
[Node1]....[Node3].....[Node2].....[Node4]  ← scattered in RAM

When CPU loads Node1, Node2, 3, 4 are NOT in cache.
Each access = cache miss = SLOW!

RESULT: Arrays run faster in practice even for same complexity algorithms
```

---

## 📌 SECTION 8: SPARSE MATRIX (HIGH-FREQUENCY PYQ TOPIC)

A **Sparse Matrix** is a matrix where the number of **zero elements is more than non-zero elements**.

### Definition:
- A matrix of size m × n is called sparse if:
  `Number of zeros > (m × n) / 2`
- In other words, more than **half the elements are zero**.

```
EXAMPLE OF SPARSE MATRIX:
===========================

    0  0  3  0
    0  0  0  0
    4  0  0  0
    0  0  5  0

Total elements = 4 × 4 = 16
Non-zero elements = 3
Zero elements = 13

Since 13 > 16/2 = 8 → It IS a Sparse Matrix ✓

DENSE MATRIX (opposite of sparse):
    1  2  3
    4  5  6
    7  8  9
All elements non-zero → Dense Matrix
```

### Why does Sparse Matrix matter?
- **Storing a 1000×1000 sparse matrix** normally = 1,000,000 memory locations.
- If only 100 elements are non-zero, we waste memory on 999,900 zeros!
- **Solution: Sparse Matrix Representation** — Store only non-zero elements.

### Sparse Matrix Representation Methods:
```
Method 1: TRIPLET REPRESENTATION (Array of (row, col, value))
==============================================================
Matrix:
    0  0  3  0
    0  0  0  0
    4  0  0  0
    0  0  5  0

Triplet representation:
Row   Col   Value
  0     2       3
  2     0       4
  3     2       5

Only 3 rows stored instead of 16 elements! Memory saved = 81%

Method 2: LINKED LIST REPRESENTATION
=====================================
Each non-zero element stored as node: (row, col, value, next_pointer)
```

---

## 📌 SECTION 9: TYPES OF ARRAYS (PYQ-TESTED)

### 1. One-Dimensional Array (1D)
```
int arr[5] = {10, 20, 30, 40, 50};
Linear arrangement, single subscript
```

### 2. Two-Dimensional Array (2D)
```
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
Rows and columns, two subscripts
Used for: matrices, grids, tables
```

### 3. Multi-Dimensional Array
```
int arr[2][3][4];  // 3D array
2 × 3 × 4 = 24 elements total
```

### 4. Dynamic Array
```
int* arr = new int[n];  // C++ dynamic allocation
Size determined at runtime, not compile time
Example: vector<int> in C++ STL
```

---

## 📌 SECTION 10: ARRAY SORTING — COMPLEXITY QUICK REFERENCE

| Sorting Algorithm | Best Case | Average Case | Worst Case | Stable? |
|------------------|-----------|--------------|------------|---------|
| Bubble Sort | O(n) | O(n²) | O(n²) | Yes |
| Selection Sort | O(n²) | O(n²) | O(n²) | No |
| Insertion Sort | O(n) | O(n²) | O(n²) | Yes |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | Yes |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | No |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | No |

> **🚨 PYQ TRAP:** "Which sorting algorithm has worst case O(n log n)?" → **Merge Sort** and **Heap Sort**
> "Which is best for nearly sorted array?" → **Insertion Sort** (O(n) best case)

---

## 📌 SECTION 11: SEARCHING IN ARRAYS

### Linear Search:
```
Compare each element one by one
Time: O(n) worst case
Works on: Sorted AND unsorted arrays
Space: O(1)
```

### Binary Search:
```
Array MUST be sorted
Divide array into half each time

Algorithm:
  low = 0, high = n-1
  while (low <= high):
    mid = (low + high) / 2
    if arr[mid] == key: return mid
    if arr[mid] < key: low = mid + 1
    else: high = mid - 1

Time: O(log n)
Space: O(1) iterative, O(log n) recursive
```

```
BINARY SEARCH EXAMPLE:
=======================
Array: [10, 20, 30, 40, 50, 60, 70]
Search for: 40

Step 1: low=0, high=6, mid=3 → arr[3]=40 → FOUND! ✓

Steps for searching 60:
Step 1: low=0, high=6, mid=3 → arr[3]=40 < 60 → low=4
Step 2: low=4, high=6, mid=5 → arr[5]=60 → FOUND! ✓
```

---

## 📌 SECTION 12: ARRAY PYQs FROM TRE 1.0, 2.0, 3.0

### 🔴 PYQ Type 1 — Access Time
**Q:** What is the time complexity to access the k-th element of an array?
**A:** O(1) — Random access using index.

### 🔴 PYQ Type 2 — Insertion
**Q:** What is the time complexity of inserting an element at the beginning of an array of n elements?
**A:** O(n) — All elements must be shifted right by one position.

### 🔴 PYQ Type 3 — Cache Performance
**Q:** Arrays are more cache-friendly than linked lists. Why?
**A:** Arrays store elements in contiguous memory (spatial locality). When one element is loaded into cache, neighboring elements are also loaded, reducing cache misses.

### 🔴 PYQ Type 4 — Address Calculation
**Q:** An array starts at memory address 2000. Each element takes 4 bytes. What is the address of element at index 5?
**A:** 2000 + (5 × 4) = 2000 + 20 = **2020**

### 🔴 PYQ Type 5 — Sparse Matrix
**Q:** A matrix is called sparse if ___
**A:** Number of zeros > (m × n) / 2 [i.e., majority of elements are zero]

---

## 📌 SECTION 13: WHEN TO USE ARRAY vs OTHER DS

```
USE ARRAY WHEN:                    AVOID ARRAY WHEN:
═══════════════════════════════    ════════════════════════════════
✓ Size is fixed/known              ✗ Frequent insertions/deletions
✓ Frequent random access needed    ✗ Size keeps changing
✓ Cache performance matters        ✗ Memory is limited and size unknown
✓ Simple sequential storage        ✗ Need to insert at front frequently
✓ Implementation of other DS       ✗ Large sparse data
  (Stack, Queue, Heap)
```

---

## 📌 SECTION 14: IMPORTANT FORMULAS SUMMARY

```
╔══════════════════════════════════════════════════════════════╗
║          ARRAY FORMULA QUICK REFERENCE                       ║
╠══════════════════════════════════════════════════════════════╣
║ 1D Address: Base + (i × size)                               ║
║ 2D Row Major: Base + (i×n + j) × size                      ║
║ 2D Col Major: Base + (j×m + i) × size                      ║
║ Array size: last_index - first_index + 1                    ║
║ Sparse condition: zeros > (m×n)/2                           ║
║ Access time: O(1)                                           ║
║ Insert/Delete at middle: O(n)                               ║
║ Insert/Delete at end: O(1)                                  ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 🔑 CS TOPPER QUICK REVISION BULLETS

1. **Main advantage of array = Random Access in O(1)**
2. **Main disadvantage = Fixed size + O(n) insertion/deletion**
3. **C, C++, Java = Row Major Order** | **FORTRAN = Column Major Order**
4. **Sparse Matrix = zeros > half of total elements**
5. **Arrays are cache-friendly** due to contiguous memory (spatial locality)
6. **Binary search requires SORTED array** — time O(log n)
7. **Insertion at beginning = O(n)** (worst case, must shift all)
8. **Insertion at end = O(1)** (best case, no shifting)
9. **Array vs Linked List:** Array = random access, LL = dynamic size
10. **Delete from NULL pointer = safe** (no crash) — carry-forward from Day 9

---

---

# ═══════════════════════════════════════════════
# 🗺️ PART B — GENERAL STUDIES
## Topic: Bihar Geography — Districts, Rivers, Physical Features & Economy
# ═══════════════════════════════════════════════

---

> **⚡ BPSC TRE FACT:** Bihar Geography questions appear in **4–6 GS questions** per paper. Examiner loves: rivers of Bihar, districts, Ganga's direction, tributaries, physical divisions, minerals. Master all of it today!

---

## 📌 SECTION 1: BIHAR — BASIC FACTS (MUST MEMORIZE)

```
╔══════════════════════════════════════════════════════════════╗
║               BIHAR AT A GLANCE                              ║
╠══════════════════════════════════════════════════════════════╣
║ Capital           : Patna                                    ║
║ Area              : 94,163 sq km (13th largest state)        ║
║ Total Districts   : 38 districts                             ║
║ Divisions         : 9 divisions                              ║
║ Rajya Sabha seats : 16                                       ║
║ Lok Sabha seats   : 40                                       ║
║ Vidhan Sabha seats: 243                                      ║
║ State Language    : Hindi (also Maithili — 8th Schedule)     ║
║ State Animal      : Gaur (Indian Bison)                      ║
║ State Bird        : House Sparrow (Gauriya)                  ║
║ State Tree        : Peepal (Sacred Fig)                      ║
║ State Flower      : Kachnar (Bauhinia)                       ║
║ Formation Day     : November 1, 1956 (Reorganization)        ║
║                     (Jharkhand separated: November 15, 2000) ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 📌 SECTION 2: PHYSICAL DIVISIONS OF BIHAR

Bihar is divided into **3 major physical divisions**:

```
PHYSICAL DIVISIONS OF BIHAR
==============================

        NEPAL (NORTH)
             |
  ┌──────────────────────┐
  │  NORTH BIHAR PLAINS  │  ← Terai region, highly fertile
  │  (Gangetic Plain)    │     Flooded by rivers from Nepal
  └──────────┬───────────┘
             │
        River GANGA (flows W to E)
             │
  ┌──────────────────────┐
  │  SOUTH BIHAR PLAINS  │  ← Less fertile than North Bihar
  │  (Gangetic Plain)    │     Son, Punpun rivers here
  └──────────┬───────────┘
             │
  ┌──────────────────────┐
  │  CHOTANAGPUR PLATEAU │  ← (Now in Jharkhand after 2000)
  │  (Southern Uplands)  │     Mineral rich region
  └──────────────────────┘

        JHARKHAND (SOUTH)
```

### Key Physical Facts:
- Bihar lies in the **Middle Gangetic Plain**
- Bihar is a **landlocked state** — no coastline
- Entire Bihar lies in the **Indo-Gangetic Plain**
- Altitude is **very low** — mostly 50–100 meters above sea level
- **Terai region** in North Bihar — marshy, forested strip near Nepal border

---

## 📌 SECTION 3: RIVER GANGA IN BIHAR (HIGHEST PYQ FREQUENCY)

```
RIVER GANGA'S JOURNEY THROUGH BIHAR
======================================

Entry Point: Buxar (western Bihar)
         ↓
         flows WEST TO EAST
         ↓
    Patna (State Capital on south bank of Ganga)
         ↓
    Hajipur (on north bank — confluence of Gandak + Ganga)
         ↓
    Munger
         ↓
    Bhagalpur (famous for silk — Tussar silk)
         ↓
Exit Point: Near Jharkhand/West Bengal border

Total length of Ganga in Bihar: ~445 km

KEY FACT: Ganga flows from WEST to EAST in Bihar
KEY FACT: Patna is on the SOUTH bank of Ganga
KEY FACT: Hajipur is on the NORTH bank of Ganga
```

> **🚨 PYQ TRAP:** "In which direction does the Ganga flow in Bihar?" → **West to East**
> "Patna is situated on which bank of Ganga?" → **South bank**

---

## 📌 SECTION 4: RIVERS OF BIHAR — COMPLETE MAP

Bihar has a rich river network. Rivers come from two sources:
1. **From Nepal (Himalayan rivers)** — flow south into Ganga (North Bihar rivers)
2. **From Chotanagpur Plateau (Peninsular rivers)** — flow north into Ganga (South Bihar rivers)

```
RIVERS OF BIHAR — COMPLETE CHART
===================================

NORTH BIHAR RIVERS (flow from North → South into Ganga)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
River       | Origin          | Joins Ganga at    | Special Feature
────────────|─────────────────|───────────────────|──────────────────────
Gandak      | Nepal           | Hajipur/Sonepur   | Also called Narayani
Kosi        | Nepal/Tibet     | Kursela (Katihar) | "Sorrow of Bihar"
Bagmati     | Nepal           | Near Katra        | Flood-prone
Kamla-Balan | Nepal           | Jhanjharpur area  | Small river
Mahananda   | Darjeeling Hills| Manihari (Katihar)| Also flows in WB
Burhi Gandak| Nepal foothills | Khagaria          | Old channel of Gandak

SOUTH BIHAR RIVERS (flow from South → North into Ganga)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
River       | Origin              | Joins Ganga at  | Special Feature
────────────|─────────────────────|─────────────────|─────────────────────
Son         | Amarkantak (MP)     | Arrah/Patna     | Largest in S. Bihar
Punpun      | Chotanagpur Plateau | Near Fatuha     | Near Patna
Falgu       | Chotanagpur Plateau | Near Gaya       | Associated with Gaya
Sone (Son)  | Amarkantak (MP/CG)  | Near Patna      | Major tributary
Phalgu      | Hazaribagh plateau  | Gaya            | Lord Buddha meditated
```

---

## 📌 SECTION 5: KOSI — "SORROW OF BIHAR" (HIGH PYQ)

The **Kosi River** is called the **"Sorrow of Bihar"** because it causes devastating floods every year.

```
KOSI RIVER — KEY FACTS
========================
Origin     : Himalaya/Tibet — Seven headstreams (Sapta Koshi)
Length     : ~729 km (total), ~260 km in Bihar
Joins Ganga: At Kursela (Katihar district)
Width      : Spreads 120–150 km wide during floods
Problem    : Changes course frequently (shifted 100+ km westward in 200 years)
             Deposits huge amount of silt — raises riverbed
             Causes floods affecting 2 crore people

Districts most affected: Supaul, Saharsa, Madhepura, Darbhanga, Purnia

Dam        : Kosi Barrage at Bhimnagar (India-Nepal border, 1963)
Project    : Kosi Project — flood control + irrigation
```

> **🚨 PYQ:** "Which river is called the 'Sorrow of Bihar'?" → **Kosi**
> "The Kosi is also known as?" → **Sapta Koshi / Koshi**
> "Where does Kosi join Ganga?" → **Kursela in Katihar district**

---

## 📌 SECTION 6: GANDAK RIVER (PYQ FAVORITE)

```
GANDAK RIVER — KEY FACTS
==========================
Also called  : Narayani (in Nepal), Shaligram River
Origin       : Himalaya (Nepal/Tibet border)
Joins Ganga  : At Sonepur/Hajipur (on Ganga's north bank)
Famous for   : Sonepur Mela held at Gandak-Ganga confluence
               (Largest cattle fair in Asia — held on Kartik Purnima)
Districts    : West Champaran, East Champaran, Muzaffarpur, Vaishali

Dam          : Gandak Barrage at Valmiki Nagar
               (Also called Vallabh Sagar)
Irrigation   : Gandak Canal irrigates North Bihar + UP + Nepal
```

> **🚨 PYQ:** "Sonepur Mela is held at the confluence of?" → **Ganga and Gandak**
> "What is Gandak called in Nepal?" → **Narayani**

---

## 📌 SECTION 7: SON RIVER (SOUTH BIHAR'S MOST IMPORTANT RIVER)

```
SON RIVER — KEY FACTS
=======================
Origin       : Amarkantak Hills (MP/Chhattisgarh border)
Also called  : Hiranyavaha, Sona
Joins Ganga  : Near Arrah / Koilwar bridge area (west of Patna)
Length       : ~784 km (total), ~230 km in Bihar
Tributaries  : Rihand, North Koel, Gopat, Banas

Famous       : Son River Valley — rich in coal deposits
               Rihand Dam on its tributary
Diamond      : Son river valley has diamond deposits
               Bhagirathi (Son) → mentioned in Puranas
               
Basin        : Covers Rohtas, Aurangabad, Arwal, Gaya districts
```

---

## 📌 SECTION 8: BIHAR'S 38 DISTRICTS — DIVISIONAL MAP

Bihar has **9 Divisions** containing **38 Districts** total.

```
BIHAR — 9 DIVISIONS AND THEIR DISTRICTS
==========================================

1. PATNA Division (5 districts)
   → Patna, Nalanda, Bhojpur, Rohtas, Buxar, Kaimur

   Wait — Patna Division has: Patna, Nalanda, Bhojpur, Rohtas, Buxar, Kaimur
   (6 districts)

2. MAGADH Division (5 districts)
   → Gaya, Jehanabad, Arwal, Nawada, Aurangabad

3. MUNGER Division (6 districts)
   → Munger, Lakhisarai, Khagaria, Begusarai, Jamui, Sheikhpura

4. BHAGALPUR Division (2 districts)
   → Bhagalpur, Banka

5. PURNEA Division (4 districts)
   → Purnia, Katihar, Araria, Kishanganj

6. KOSI Division (3 districts)
   → Saharsa, Supaul, Madhepura

7. DARBHANGA Division (3 districts)
   → Darbhanga, Madhubani, Samastipur

8. MUZAFFARPUR (TIRHUT) Division (6 districts)
   → Muzaffarpur, East Champaran, West Champaran,
     Sitamarhi, Sheohar, Vaishali

9. SARAN Division (3 districts)
   → Saran, Siwan, Gopalganj

TOTAL = 38 DISTRICTS ✓
```

---

## 📌 SECTION 9: IMPORTANT DISTRICTS OF BIHAR (PYQ-TESTED)

```
DISTRICT       | KEY FACTS
───────────────|─────────────────────────────────────────────────
Patna          | Capital, on south bank of Ganga, largest city
Gaya           | Hindu pilgrimage — Vishnupad Temple, BodhGaya nearby
Bodh Gaya      | (In Gaya district) — Buddha attained enlightenment
               | UNESCO World Heritage Site — Mahabodhi Temple
Nalanda        | Ancient Nalanda University (destroyed 1193 by Bakhtiyar Khilji)
               | UNESCO World Heritage Site
Rajgir         | Capital of Magadha, glass bridge, hot springs
Vaishali       | Birthplace of Mahavira (Jain Tirthankara)
               | World's first republic (Lichchhavi Mahajanapada)
Champaran      | Gandhi's first Satyagraha (1917) — Champaran Satyagraha
Muzaffarpur    | Famous for Shahi Litchi (GI Tag)
Bhagalpur      | Silk City — Tussar (Kosa) Silk, vikramshila university ruins
Sonepur        | Largest cattle fair in Asia (Sonepur Mela — Hajipur area)
Motihari       | George Orwell (author of Animal Farm) was born here!
Buxar          | Battle of Buxar (1764) — decisive British victory
Rohtas         | Rohtasgarh Fort — medieval period
Sitamarhi      | Birthplace of Sita (as per Hindu tradition)
Darbhanga      | Cultural capital of Mithila region
Madhubani      | Famous for Madhubani/Mithila paintings (GI Tag)
Kishanganj     | Called "Mini Kashmir" of Bihar, tea plantation
```

---

## 📌 SECTION 10: BIHAR'S CLIMATE & RAINFALL

```
BIHAR CLIMATE
==============
Type        : Tropical Monsoon Climate (Modified Continental)

Seasons:
  1. Summer   (March–June)     : 35–45°C, hot and dry
  2. Monsoon  (July–September) : SW Monsoon, 80% of annual rainfall
  3. Autumn   (October–Nov)    : Retreating monsoon, mild
  4. Winter   (December–Feb)   : 5–15°C, cold and foggy

Annual Rainfall : 1000–1500 mm (average ~1200 mm)
Highest Rainfall: Kishanganj district (near Darjeeling hills) ~2000mm+
Lowest Rainfall : Rohtas/Kaimur/Aurangabad (southern plateau) ~700mm

Rain Distribution:
  North Bihar > South Bihar (rivers from Nepal bring moisture)
  Eastern Bihar > Western Bihar

FOG: Bihar faces severe fog in winter — especially Dec–Jan
     Affects Patna, Muzaffarpur, Darbhanga
```

---

## 📌 SECTION 11: BIHAR'S SOIL TYPES

```
SOIL TYPES IN BIHAR
====================

1. ALLUVIAL SOIL (most common — 90%+ of Bihar)
   ├── New Alluvial (Khadar): Near riverbanks, very fertile
   │   → Suitable for: Rice, Wheat, Sugarcane, Vegetables
   └── Old Alluvial (Bhangar): Away from rivers, less fertile
       → Contains kankar (calcium carbonate nodules)

2. TERAI SOIL (North Bihar — near Nepal border)
   → Marshy, high moisture, dense forests once
   → Now converted to agricultural land
   → Good for: Rice, Sugarcane

3. LATERITE SOIL (Southern Bihar/Plateau areas)
   → Found in Rohtas, Kaimur, Aurangabad, Jamui
   → Red in color, iron-rich, acidic
   → Poor fertility for crops
   → Good for: Mango, Jackfruit

4. SANDY SOIL (Desert-type, western Bihar)
   → Found near Kaimur/Rohtas
   → Low water retention
```

---

## 📌 SECTION 12: BIHAR'S AGRICULTURE — KEY CROPS (PYQ)

```
CROP PRODUCTION IN BIHAR
==========================

KHARIF CROPS (Sown Jun–Jul, Harvested Oct–Nov):
→ Rice (Paddy) — #1 crop, North Bihar
→ Maize — Bihar is major maize producer
→ Arhar (Pigeonpea/Toor dal)
→ Sugarcane — Champaran, Muzaffarpur, Saran
→ Jute — Kosi region, North Bihar

RABI CROPS (Sown Oct–Nov, Harvested Mar–Apr):
→ Wheat — South Bihar (Patna, Rohtas, Bhojpur)
→ Maize (some varieties)
→ Potato — Nalanda is major potato producer

SPECIAL CROPS / GI TAGGED PRODUCTS:
→ Shahi Litchi (Muzaffarpur) — GI Tag ✓
→ Katarni Rice (Bhagalpur) — GI Tag ✓ 
→ Makhana (Fox nut/Lotus seed) — Darbhanga, Madhubani, Sitamarhi
   Bihar produces 90%+ of world's Makhana!
→ Madhubani Painting — GI Tag ✓
→ Sikki Grass Craft — GI Tag ✓
→ Bhagalpuri Silk (Tussar) — GI Tag ✓

KEY FACT: Bihar is India's largest producer of MAKHANA (Fox Nut)
KEY FACT: Bihar is India's 2nd largest producer of VEGETABLES
```

---

## 📌 SECTION 13: MINERALS IN BIHAR

> **Note:** After Jharkhand's formation (2000), most minerals went to Jharkhand. Bihar now has limited minerals.

```
MINERALS FOUND IN BIHAR
=========================
District          | Mineral
──────────────────|──────────────────────────────
Rohtas, Kaimur    | Limestone (for cement)
Rohtas            | Pyrite (iron sulfide)
Munger            | Mica
Jamui             | Gold traces, Copper
Aurangabad        | Graphite
Nawada            | Building stone (granite)
Son River Valley  | Sand, Gravel (construction)

IMPORTANT: Bihar has NO significant coal deposits (Jharkhand has coal)
           Bihar has NO significant iron ore (Jharkhand has iron ore)
```

---

## 📌 SECTION 14: IMPORTANT DAMS & PROJECTS IN BIHAR

```
MAJOR DAMS/BARRAGES IN BIHAR
==============================

Dam/Barrage          | River    | District/Location  | Purpose
─────────────────────|──────────|--------------------|──────────────────
Gandak Barrage        | Gandak   | Valmiki Nagar      | Irrigation, Flood
(Vallabh Sagar)       |          | (W. Champaran)     | control
Kosi Barrage          | Kosi     | Bhimnagar          | Flood control
                      |          | (Supaul, Nepal border)|
Sone Barrage          | Son      | Dehri-on-Sone      | Irrigation
                      |          | (Rohtas)            |
Bagmati Barrage       | Bagmati  | Dheng              | Flood control
Adhwara Barrage       | Adhwara  | Sitamarhi          | Irrigation
Kamla Barrage         | Kamla    | Jhanjharpur (Madhubani)| Flood control
```

---

## 📌 SECTION 15: IMPORTANT NATIONAL PARKS & WILDLIFE IN BIHAR

```
WILDLIFE SANCTUARIES IN BIHAR
================================

Name                    | District         | Famous For
────────────────────────|──────────────────|─────────────────────
Valmiki National Park   | West Champaran   | Tigers (Project Tiger)
(Valmiki Tiger Reserve) |                  | Bihar's ONLY national park
                        |                  | Also a Tiger Reserve
Udaypur Wildlife        | West Champaran   | Gharial, birds
Sanctuary               |                  |
Bhimbandh Wildlife      | Munger           | Animals, hot springs
Sanctuary               |                  |
Gautam Buddha Wildlife  | Gaya             | Blackbuck, birds
Sanctuary               |                  |
Vikramshila Gangetic    | Bhagalpur        | Gangetic Dolphins
Dolphin Sanctuary       |                  | (India's FIRST dolphin sanctuary)
Kanwarjheel Bird        | Begusarai        | Asia's largest freshwater
Sanctuary               |                  | oxbow lake bird sanctuary
```

> **🚨 PYQ:** "Bihar's only National Park?" → **Valmiki National Park** (West Champaran)
> "India's first dolphin sanctuary?" → **Vikramshila Gangetic Dolphin Sanctuary** (Bhagalpur)
> "Asia's largest freshwater oxbow lake bird sanctuary?" → **Kanwarjheel** (Begusarai)

---

## 📌 SECTION 16: BIHAR — TRANSPORT & CONNECTIVITY

```
IMPORTANT NATIONAL HIGHWAYS IN BIHAR
=======================================
NH-30 : Patna – Mohania (connects to Grand Trunk Road)
NH-31 : Barhi – Dalkhola (goes through Bihar via Patna–Begusarai)
NH-28 : Barauni – Muzaffarpur – Gorakhpur
NH-83 : Patna – Gaya – Dobhi (connects Bodh Gaya)
NH-84 : Patna – Gaya – Sasaram route

IMPORTANT BRIDGES:
→ Mahatma Gandhi Setu (Patna) : 5.75 km — one of India's longest river bridges
                                 Connects Patna to Hajipur over Ganga
→ JP Setu (Patna)             : Jai Prakash Narayan Bridge
→ Vikramshila Setu (Bhagalpur): Connects Bhagalpur to Naugachia
→ Gandhi Setu (Rajendra Bridge): Connects Hajipur to Patna area

IMPORTANT AIRPORTS IN BIHAR:
→ Jay Prakash Narayan International Airport — Patna (Main airport)
→ Gaya Airport — International airport (flights for Buddhist tourists)
→ Darbhanga Airport
→ Muzaffarpur Airport (smaller)

RAILWAYS:
→ Patna is a major railway junction
→ Mughal Sarai (now Pt. Deen Dayal Upadhyay Jn.) is near Bihar in UP
→ Important junctions: Patna, Gaya, Muzaffarpur, Danapur, Katihar
```

---

## 📌 SECTION 17: BIHAR IN HISTORY — GEOGRAPHIC SIGNIFICANCE

```
HISTORICAL IMPORTANCE OF BIHAR'S GEOGRAPHY
============================================

Pataliputra (now PATNA):
→ Capital of Magadha Empire (Maurya, Gupta periods)
→ Founded by Ajatashatru (Haryanka dynasty)
→ Chandragupta Maurya ruled from here
→ One of world's largest cities in ancient times

Rajgir (Rajagriha):
→ Earlier capital of Magadha (before Pataliputra)
→ First Buddhist Council held here (after Buddha's death)
→ Located in rocky hills (natural fortress — Five Hills)

Vaishali:
→ World's first democratic republic (Lichchhavi, 6th century BC)
→ Birthplace of Mahavira (599 BC)
→ Buddha's last sermon delivered here

Bodh Gaya:
→ Mahabodhi Temple — UNESCO World Heritage Site
→ Siddhartha Gautama attained enlightenment here (528 BC)
→ Under Bodhi Tree (Ficus religiosa / Peepal tree)

Nalanda:
→ Ancient world-class university (5th–12th century AD)
→ UNESCO World Heritage Site
→ Destroyed by Bakhtiyar Khilji in 1193 AD
```

---

## 📌 SECTION 18: GS TOPPER QUICK REVISION BULLETS (BIHAR GEOGRAPHY)

1. **Bihar has 38 districts and 9 divisions**
2. **Ganga flows West to East in Bihar; Patna is on SOUTH bank**
3. **Kosi = "Sorrow of Bihar" — joins Ganga at Kursela (Katihar)**
4. **Gandak = Narayani; joins Ganga at Sonepur; Sonepur Mela here**
5. **Son river = largest south Bihar river; from Amarkantak, MP**
6. **Bihar's only National Park = Valmiki National Park (W. Champaran)**
7. **India's 1st dolphin sanctuary = Vikramshila (Bhagalpur)**
8. **Bihar = world's largest Makhana producer (90%+ global share)**
9. **Shahi Litchi (Muzaffarpur) has GI Tag**
10. **Madhubani Painting (Darbhanga/Madhubani) has GI Tag**
11. **Mahatma Gandhi Setu = 5.75 km, connects Patna–Hajipur over Ganga**
12. **Kishanganj = highest rainfall in Bihar; called "Mini Kashmir"**
13. **Bhagalpur = Silk City (Tussar silk)**
14. **Nalanda University destroyed by Bakhtiyar Khilji in 1193 AD**
15. **Vaishali = world's first republic (Lichchhavi)**
16. **Bodh Gaya = UNESCO World Heritage Site; Buddha's enlightenment**
17. **Bihar is landlocked — no sea coast**
18. **Bihar's state animal = Gaur (Indian Bison)**
19. **Kanwarjheel Bird Sanctuary (Begusarai) = Asia's largest freshwater oxbow lake**
20. **After 2000, Jharkhand formed from Bihar — most minerals went to Jharkhand**

---

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 15
## Instructions: Attempt ALL questions BEFORE looking at answers.
## Answers are at the VERY END of this file.
# ═══════════════════════════════════════════════

---

> **⚡ EXAM FORMAT REMINDER:** BPSC TRE uses 5 options:
> (A), (B), (C), (D) More than one of the above, (E) None of the above
> **ALWAYS consider option (D) carefully** — 20–25% answers are (D) or (E)

---

## 🖥️ CS PRACTICE QUESTIONS (Q1–Q25)

---

**Q1.** What is the time complexity of accessing the k-th element of an array?

(A) O(n)
(B) O(log n)
(C) O(k)
(D) More than one of the above
(E) O(1)

---

**Q2.** An array `int A[6]` is stored starting at base address 100. Each integer takes 4 bytes. What is the memory address of element `A[4]`?

(A) 116
(B) 120
(C) 104
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following operations on an array has the BEST time complexity (lowest)?

(A) Insertion at the beginning
(B) Deletion from the middle
(C) Access by index
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the time complexity of inserting an element at the beginning of an array of n elements?

(A) O(1)
(B) O(log n)
(C) O(n log n)
(D) More than one of the above
(E) O(n)

---

**Q5.** A 2D array of size 4×5 is stored in Row Major Order. Base address = 2000. Each element takes 2 bytes. What is the address of element A[2][3]?

(A) 2026
(B) 2046
(C) 2036
(D) More than one of the above
(E) None of the above

---

**Q6.** A matrix of size m×n is called a sparse matrix if:

(A) All elements are zero
(B) Number of zero elements is equal to non-zero elements
(C) Number of zero elements exceeds (m×n)/2
(D) More than one of the above
(E) None of the above

---

**Q7.** Which programming language stores 2D arrays in Column Major Order?

(A) C
(B) C++
(C) Java
(D) More than one of the above
(E) FORTRAN

---

**Q8.** Which of the following is/are advantages of arrays over linked lists?

(A) Random access in O(1)
(B) Better cache performance due to spatial locality
(C) Dynamic size adjustment
(D) More than one of the above
(E) None of the above

---

**Q9.** Binary Search can be applied to:

(A) Only sorted arrays
(B) Only unsorted arrays
(C) Both sorted and unsorted arrays
(D) More than one of the above
(E) Linked lists only

---

**Q10.** What is the time complexity of Binary Search in the WORST case?

(A) O(n)
(B) O(n²)
(C) O(1)
(D) More than one of the above
(E) O(log n)

---

**Q11.** Which sorting algorithm has O(n) best case time complexity?

(A) Selection Sort
(B) Quick Sort
(C) Insertion Sort
(D) More than one of the above
(E) None of the above

---

**Q12.** Deletion of an element from the END of an array has time complexity:

(A) O(n)
(B) O(n log n)
(C) O(log n)
(D) More than one of the above
(E) O(1)

---

**Q13.** For a 1D array, the address formula for element A[i] where base address = B and size of each element = S is:

(A) B + S
(B) B + (i + 1) × S
(C) B + i × S
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following is a disadvantage of arrays?

(A) Fixed size — cannot resize dynamically
(B) Insertion and deletion require shifting elements (O(n))
(C) Large contiguous memory block required
(D) More than one of the above
(E) None of the above

---

**Q15.** In which data structure scenario should you prefer a Linked List over an Array?

(A) When random access is frequently needed
(B) When the size of data is fixed
(C) When frequent insertion/deletion at arbitrary positions is needed
(D) More than one of the above
(E) None of the above

---

**Q16.** A Sparse Matrix of 100×100 size has only 50 non-zero elements. The most efficient way to store it is:

(A) A normal 2D array
(B) Triplet representation (row, col, value)
(C) Another 100×100 2D array
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following statements about arrays is/are CORRECT?

(A) Array elements are stored in non-contiguous memory locations
(B) Array index starts from 1 in C/C++
(C) Accessing any element takes constant time O(1)
(D) More than one of the above
(E) None of the above

---

**Q18.** An array `char ch[10]` is declared in C++. The `sizeof(ch)` will return:

(A) 1
(B) 20
(C) 4
(D) More than one of the above
(E) 10

---

**Q19.** Which sorting algorithm has O(n log n) complexity in ALL cases (best, average, worst)?

(A) Quick Sort
(B) Insertion Sort
(C) Merge Sort
(D) More than one of the above
(E) Bubble Sort

---

**Q20.** The spatial locality advantage of arrays refers to:

(A) Arrays can store large data
(B) Array elements being in adjacent memory help CPU cache load multiple elements at once
(C) Arrays do not require pointers
(D) More than one of the above
(E) None of the above

---

**Q21.** For a 2D array A[m][n] stored in Row Major Order, the address of element A[i][j] with base B and element size S is:

(A) B + (i × m + j) × S
(B) B + (j × n + i) × S
(C) B + (i × n + j) × S
(D) More than one of the above
(E) None of the above

---

**Q22.** Linear search on an unsorted array of n elements has worst case complexity:

(A) O(1)
(B) O(log n)
(C) O(n log n)
(D) More than one of the above
(E) O(n)

---

**Q23.** Which of the following is TRUE about the time complexity of array operations?

(A) Insertion at beginning = O(1)
(B) Deletion from end = O(1)
(C) Access by index = O(n)
(D) More than one of the above
(E) None of the above

---

**Q24.** A dynamic array (like vector in C++ STL) differs from a static array in that:

(A) Dynamic array has O(n) access time
(B) Dynamic array can resize itself at runtime
(C) Dynamic array uses Column Major storage
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following operations would be SLOWEST on a large array (say n = 10,000 elements)?

(A) Access element at index 5000
(B) Insert element at index 0 (beginning)
(C) Access last element
(D) More than one of the above
(E) None of the above

---

---

## 🗺️ GS PRACTICE QUESTIONS — BIHAR GEOGRAPHY (Q26–Q50)

---

**Q26.** The total number of districts in Bihar (as of 2024) is:

(A) 36
(B) 45
(C) 40
(D) More than one of the above
(E) 38

---

**Q27.** In which direction does the Ganga river flow through Bihar?

(A) North to South
(B) East to West
(C) South to North
(D) More than one of the above
(E) West to East

---

**Q28.** Patna, the capital of Bihar, is situated on which bank of the Ganga?

(A) North bank
(B) West bank
(C) East bank
(D) More than one of the above
(E) South bank

---

**Q29.** Which river is called the "Sorrow of Bihar"?

(A) Gandak
(B) Son
(C) Bagmati
(D) More than one of the above
(E) Kosi

---

**Q30.** The Kosi river joins the Ganga at:

(A) Hajipur
(B) Patna
(C) Munger
(D) More than one of the above
(E) Kursela (Katihar)

---

**Q31.** The Gandak river is also known as:

(A) Koshi
(B) Sone
(C) Falgu
(D) More than one of the above
(E) Narayani

---

**Q32.** The famous Sonepur Mela (Asia's largest cattle fair) is held at the confluence of:

(A) Ganga and Kosi
(B) Ganga and Son
(C) Son and Ghaghara
(D) More than one of the above
(E) Ganga and Gandak

---

**Q33.** Bihar is India's largest producer of which of the following?

(A) Rice
(B) Wheat
(C) Jute
(D) More than one of the above
(E) Makhana (Fox Nut)

---

**Q34.** Which district of Bihar is famous for Tussar silk and has a major silk weaving industry?

(A) Muzaffarpur
(B) Darbhanga
(C) Nalanda
(D) More than one of the above
(E) Bhagalpur

---

**Q35.** Valmiki National Park (Bihar's only national park) is located in which district?

(A) Gaya
(B) Rohtas
(C) Patna
(D) More than one of the above
(E) West Champaran

---

**Q36.** The Vikramshila Gangetic Dolphin Sanctuary (India's FIRST dolphin sanctuary) is located in:

(A) Patna
(B) Muzaffarpur
(C) Vaishali
(D) More than one of the above
(E) Bhagalpur

---

**Q37.** The Shahi Litchi of Bihar, which has a GI Tag, is primarily grown in which district?

(A) Nalanda
(B) Patna
(C) Gaya
(D) More than one of the above
(E) Muzaffarpur

---

**Q38.** The state animal of Bihar is:

(A) Tiger
(B) Elephant
(C) One-horned Rhinoceros
(D) More than one of the above
(E) Gaur (Indian Bison)

---

**Q39.** Mahatma Gandhi Setu in Patna crosses which river?

(A) Son
(B) Punpun
(C) Gandak
(D) More than one of the above
(E) Ganga

---

**Q40.** Which district of Bihar receives the highest annual rainfall?

(A) Patna
(B) Rohtas
(C) Munger
(D) More than one of the above
(E) Kishanganj

---

**Q41.** The Kanwar Jheel (Kabartal) bird sanctuary in Begusarai is notable for being:

(A) India's first bird sanctuary
(B) Asia's largest saltwater lake bird sanctuary
(C) Largest bird sanctuary in Bihar
(D) More than one of the above
(E) Asia's largest freshwater oxbow lake bird sanctuary

---

**Q42.** The Son river originates from:

(A) Nepal Himalayas
(B) Darjeeling Hills
(C) Gangotri Glacier
(D) More than one of the above
(E) Amarkantak Hills (MP/CG border)

---

**Q43.** The Mahabodhi Temple, a UNESCO World Heritage Site, is located in:

(A) Nalanda
(B) Vaishali
(C) Patna
(D) More than one of the above
(E) Bodh Gaya (Gaya district)

---

**Q44.** Which of the following cities/places in Bihar are UNESCO World Heritage Sites?

(A) Bodh Gaya (Mahabodhi Temple)
(B) Nalanda (ancient university ruins)
(C) Rajgir
(D) More than one of the above
(E) None of the above

---

**Q45.** Madhubani Painting (Mithila Art) has been given the GI (Geographical Indication) Tag. It is associated with which district?

(A) Patna
(B) Gaya
(C) Bhagalpur
(D) More than one of the above
(E) Madhubani

---

**Q46.** The state of Jharkhand was carved out from Bihar on:

(A) October 1, 2000
(B) November 1, 2000
(C) January 26, 2000
(D) More than one of the above
(E) November 15, 2000

---

**Q47.** Vaishali is historically significant because:

(A) It was the birthplace of Gautama Buddha
(B) It is considered the world's first republic (Lichchhavi Mahajanapada)
(C) The ancient Nalanda University was located here
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following rivers flows through SOUTH Bihar and originates from the peninsular plateau?

(A) Gandak
(B) Kosi
(C) Bagmati
(D) More than one of the above
(E) Son (Sone)

---

**Q49.** The Kosi Barrage (flood control dam on Kosi river) is located at:

(A) Katihar
(B) Saharsa
(C) Supaul
(D) More than one of the above
(E) Bhimnagar (Bihar-Nepal border)

---

**Q50.** Which of the following statements about Bihar's geography are CORRECT?

(A) Bihar is a landlocked state with no sea coast
(B) Kishanganj is called "Mini Kashmir" of Bihar for its tea plantations
(C) Bihar produces over 90% of the world's Makhana (Fox Nut)
(D) More than one of the above
(E) None of the above

---

---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 15
## (Scroll down only AFTER attempting all 50 questions!)
# ═══════════════════════════════════════════════

---

```
  ╔═══╦═══════╦═══╦═══════╦═══╦═══════╦═══╦═══════╦═══╦═══════╗
  ║ Q ║ ANS   ║ Q ║ ANS   ║ Q ║ ANS   ║ Q ║ ANS   ║ Q ║ ANS   ║
  ╠═══╬═══════╬═══╬═══════╬═══╬═══════╬═══╬═══════╬═══╬═══════╣
  ║ 1 ║  (E)  ║ 11║  (C)  ║ 21║  (C)  ║ 31║  (E)  ║ 41║  (E)  ║
  ║ 2 ║  (A)  ║ 12║  (E)  ║ 22║  (E)  ║ 32║  (E)  ║ 42║  (E)  ║
  ║ 3 ║  (C)  ║ 13║  (C)  ║ 23║  (B)  ║ 33║  (E)  ║ 43║  (E)  ║
  ║ 4 ║  (E)  ║ 14║  (D)  ║ 24║  (B)  ║ 34║  (E)  ║ 44║  (D)  ║
  ║ 5 ║  (A)  ║ 15║  (C)  ║ 25║  (B)  ║ 35║  (E)  ║ 45║  (E)  ║
  ║ 6 ║  (C)  ║ 16║  (B)  ║ 26║  (E)  ║ 36║  (E)  ║ 46║  (E)  ║
  ║ 7 ║  (E)  ║ 17║  (C)  ║ 27║  (E)  ║ 37║  (E)  ║ 47║  (B)  ║
  ║ 8 ║  (D)  ║ 18║  (E)  ║ 28║  (E)  ║ 38║  (E)  ║ 48║  (E)  ║
  ║ 9 ║  (A)  ║ 19║  (C)  ║ 29║  (E)  ║ 39║  (E)  ║ 49║  (E)  ║
  ║10 ║  (E)  ║ 20║  (B)  ║ 30║  (E)  ║ 40║  (E)  ║ 50║  (D)  ║
  ╚═══╩═══════╩═══╩═══════╩═══╩═══════╩═══╩═══════╩═══╩═══════╝
```

---

## 📖 DETAILED EXPLANATIONS

---

### CS EXPLANATIONS:

**Q1 → (E) O(1)**
Array access uses the formula: Address = Base + (i × size). This is a direct calculation — no searching needed. So ANY element is accessed in constant O(1) time. This is the PRIMARY advantage of arrays.

**Q2 → (B) 120**
Address of A[4] = Base + (index × size) = 100 + (4 × 4) = 100 + 16 = **116**
Wait — let me re-check: 100 + (4 × 5)... No.
A[0]=100, A[1]=104, A[2]=108, A[3]=112, A[4]=116, A[5]=120
A[4] = 100 + 4×4 = **116**
> ⚠️ CORRECTION: The answer for Q2 should be (A) 116. Recalculate: Base=100, index=4, size=4 bytes → 100 + 16 = **116**. If you wrote 120, that is A[5].

**Q3 → (C) Access by index**
Access = O(1). Insertion at beginning = O(n). Deletion from middle = O(n). So access by index is fastest.

**Q4 → (E) O(n)**
Inserting at beginning requires all n existing elements to shift right by one position. Hence O(n).

**Q5 → (C) 2036**
Row Major formula: B + (i × n + j) × S
= 2000 + (2 × 5 + 3) × 2
= 2000 + (10 + 3) × 2
= 2000 + 13 × 2
= 2000 + 26 = **2026**
> ⚠️ CORRECTION: 2000 + 26 = **2026**. Answer should be (A) 2026. 

**Q6 → (C)**
A matrix is sparse when number of zero elements exceeds (m×n)/2, i.e., more than half the elements are zero.

**Q7 → (E) FORTRAN**
C, C++, Java — Row Major Order. FORTRAN — Column Major Order. This is a very popular BPSC trap!

**Q8 → (D) More than one**
Both (A) Random access O(1) AND (B) Better cache performance are advantages of arrays over linked lists. Option (C) is WRONG — dynamic size is a linked list advantage, not array.

**Q9 → (A) Only sorted arrays**
Binary search requires the array to be sorted. It cannot work on unsorted arrays.

**Q10 → (E) O(log n)**
Binary search divides the search space in half each time. Worst case = O(log n).

**Q11 → (C) Insertion Sort**
Insertion Sort has O(n) best case when the array is already sorted. Selection Sort is always O(n²). Quick Sort best case is O(n log n).

**Q12 → (E) O(1)**
Deletion from the END requires no shifting. Just decrement the size/index. So it is O(1).

**Q13 → (C) B + i × S**
Standard 1D array address formula: Base + index × element_size.

**Q14 → (D) More than one**
All three — fixed size (A), O(n) insertion/deletion (B), and need for contiguous memory (C) — are genuine disadvantages of arrays.

**Q15 → (C)**
Linked List is better when frequent insertion/deletion at arbitrary positions is needed (O(1) for LL vs O(n) for array). Arrays are better for random access and fixed-size data.

**Q16 → (B) Triplet representation**
For a 100×100 = 10,000 element matrix with only 50 non-zero values, triplet representation stores only 50×3 = 150 values instead of 10,000. Massive memory saving.

**Q17 → (C) Only option C is correct**
(A) is wrong — array elements ARE contiguous. (B) is wrong — C/C++ index starts at 0. (C) is CORRECT — accessing any element is O(1).

**Q18 → (E) 10**
`char ch[10]` allocates 10 characters. `sizeof(char)` = 1 byte. So `sizeof(ch)` = 10 × 1 = **10 bytes**.

**Q19 → (C) Merge Sort**
Merge Sort is always O(n log n) — best, average, and worst cases. Quick Sort worst case is O(n²).

**Q20 → (B)**
Spatial locality means adjacent memory locations are accessed together. CPU cache loads neighboring memory when one location is accessed. Array elements in contiguous memory = multiple elements loaded in one cache fetch = faster execution.

**Q21 → (C) B + (i × n + j) × S**
Row Major formula: Address = Base + (row × number_of_columns + column) × element_size.

**Q22 → (E) O(n)**
Linear search compares each element one by one. Worst case: key is the last element or not found → compare all n elements → O(n).

**Q23 → (B) Deletion from end = O(1)**
(A) is wrong: insertion at beginning = O(n). (B) is CORRECT: deletion from end = O(1). (C) is wrong: access by index = O(1), not O(n).

**Q24 → (B)**
Dynamic arrays (vector in C++) can resize themselves at runtime. Access time is still O(1). They do NOT use column major storage.

**Q25 → (B) Insert at index 0 (beginning)**
Access (A) and (C) are both O(1). Insert at beginning (B) requires shifting ALL 10,000 elements right → O(n). So (B) is the slowest.

---

### GS EXPLANATIONS:

**Q26 → (E) 38**
Bihar has exactly 38 districts organized into 9 divisions.

**Q27 → (E) West to East**
Ganga enters Bihar at Buxar (west) and exits near Jharkhand/WB (east). It flows West to East.

**Q28 → (E) South bank**
Patna is on the SOUTH bank of Ganga. Hajipur is on the NORTH bank. Remember: Hajipur-Patna bridge (Gandhi Setu) crosses Ganga.

**Q29 → (E) Kosi**
The Kosi river is called "Sorrow of Bihar" because it floods massive areas every year, shifts course, and devastates crops and villages.

**Q30 → (E) Kursela (Katihar)**
Kosi joins Ganga at Kursela in Katihar district (northeastern Bihar).

**Q31 → (E) Narayani**
Gandak is called Narayani in Nepal. It is also called Shaligram river (sacred black stones from it are worshipped).

**Q32 → (E) Ganga and Gandak**
Sonepur Mela is held at Sonepur (near Hajipur), which is at the confluence of Ganga and Gandak rivers, on Kartik Purnima.

**Q33 → (E) Makhana (Fox Nut)**
Bihar produces over 90% of the world's Makhana (fox nut/lotus seed). It is a major crop in the Mithila region (Darbhanga, Madhubani, Sitamarhi, Supaul).

**Q34 → (E) Bhagalpur**
Bhagalpur is called the "Silk City" of Bihar. Famous for Tussar (Tussah) or Kosa silk. Bhagalpuri silk has a GI Tag.

**Q35 → (E) West Champaran**
Valmiki National Park (Bihar's ONLY national park and Tiger Reserve) is in West Champaran district, near Nepal border.

**Q36 → (E) Bhagalpur**
Vikramshila Gangetic Dolphin Sanctuary in Bhagalpur district is India's FIRST dolphin sanctuary, protecting the endangered Gangetic river dolphin.

**Q37 → (E) Muzaffarpur**
Muzaffarpur district is famous for Shahi Litchi with GI Tag. It is also called "Litchi Kingdom of India."

**Q38 → (E) Gaur (Indian Bison)**
Bihar's state animal is the Gaur (Indian Bison), found in Valmiki National Park. NOT the tiger!

**Q39 → (E) Ganga**
Mahatma Gandhi Setu (5.75 km long) crosses the Ganga river, connecting Patna (south) to Hajipur (north). It was one of India's longest river bridges when built.

**Q40 → (E) Kishanganj**
Kishanganj (extreme northeastern Bihar, near Darjeeling hills and Bangladesh) gets the highest rainfall (~2000+ mm/year) in Bihar due to its proximity to the Bay of Bengal moisture and Himalayan slopes. Called "Mini Kashmir."

**Q41 → (E)**
Kanwar Jheel (Kabartal wetland) in Begusarai is Asia's largest freshwater oxbow lake and a major bird sanctuary. It was declared a Ramsar site (wetland of international importance) in 2020.

**Q42 → (E) Amarkantak Hills (MP/CG border)**
The Son river (also called Sone) originates from Amarkantak, a plateau in Madhya Pradesh/Chhattisgarh border. It is NOT a Himalayan river.

**Q43 → (E) Bodh Gaya (Gaya district)**
The Mahabodhi Temple complex at Bodh Gaya (in Gaya district) is a UNESCO World Heritage Site. Bodh Gaya is where Siddhartha Gautama attained enlightenment.

**Q44 → (D) More than one**
Both Bodh Gaya (Mahabodhi Temple, 2002) AND Nalanda (Nalanda Mahavihara ruins, 2016) are UNESCO World Heritage Sites in Bihar. So option (D) is correct.

**Q45 → (E) Madhubani**
Madhubani painting (also called Mithila painting) is associated with Madhubani district and the broader Mithila cultural region. It has a GI Tag.

**Q46 → (E) November 15, 2000**
Jharkhand was formed on November 15, 2000 (Birsa Munda's birth anniversary) by carving out 18 southern districts from Bihar. This was under the Bihar Reorganisation Act, 2000.

**Q47 → (B)**
Vaishali is primarily significant for being the world's first democratic republic (Lichchhavi/Vajji Mahajanapada, ~6th century BC). It is also the birthplace of Mahavira (Jain Tirthankara, 599 BC). Buddha was NOT born there (he was born in Lumbini, Nepal). So strictly (B) is the most accurate single answer. Note: Mahavira's birth is also associated with Vaishali — if the option had included that, it would be (D).

**Q48 → (E) Son (Sone)**
Son river originates from Amarkantak (peninsular plateau, MP) and flows through SOUTH Bihar before joining Ganga near Patna/Arrah. The other rivers (Gandak, Kosi, Bagmati) are North Bihar rivers from the Himalayas/Nepal.

**Q49 → (E) Bhimnagar (Bihar-Nepal border)**
The Kosi Barrage (flood control barrage) is at Bhimnagar, on the Bihar-Nepal border, in Supaul district area. Built in 1963 under the Indo-Nepal agreement.

**Q50 → (D) More than one**
All THREE statements (A), (B), and (C) are CORRECT:
- Bihar IS landlocked ✓
- Kishanganj IS called "Mini Kashmir" for tea plantations ✓
- Bihar DOES produce 90%+ of world's Makhana ✓
Hence option (D) — More than one of the above.

---

---

## 📊 YOUR SCORE ANALYSIS

```
Score Range    → Your Status
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
45–50          → 🏆 TOPPER LEVEL — Excellent! Aim for 50/50 tomorrow
40–44          → 🥇 Strong — Review wrong answers carefully
35–39          → 🥈 Good — Re-read weak sections once more
30–34          → 🥉 Average — Revise Day 15 concepts again tonight
Below 30       → ⚠️ Need effort — Reread full notes, redo all questions
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CS Score  /25:  ___
GS Score  /25:  ___
Total     /50:  ___
```

---

## 🌙 NIGHT REVISION — 5-BULLET SUMMARY (Write in your notebook)

### CS (Arrays):
1. Main advantage of Array = **Random Access O(1)** using index
2. Insertion/Deletion at middle = **O(n)** (shifting needed); at end = **O(1)**
3. **C/C++/Java = Row Major** order; **FORTRAN = Column Major** order
4. **Sparse Matrix** = zeros > (m×n)/2 → use triplet representation
5. **Binary Search** needs sorted array; O(log n) — Array is cache-friendly

### GS (Bihar Geography):
1. Bihar = **38 districts, 9 divisions**; Ganga flows **West to East**
2. **Kosi = "Sorrow of Bihar"**; joins Ganga at Kursela (Katihar)
3. **Gandak = Narayani**; Sonepur Mela at Ganga-Gandak confluence
4. **Makhana = Bihar's world-famous product** (90% world share)
5. **Valmiki NP** = Bihar's only National Park (W. Champaran)

---

## ⏭️ TOMORROW — DAY 16 PREVIEW

```
CS Topic  : Stack — LIFO, Operations (Push/Pop), Applications
GS Topic  : Bihar Geography continued — Rohtas, Bhagalpur districts
              + Bihar Economy basics

Stack is built ON TOP of arrays — so today's learning helps tomorrow!
Key fact to remember: Stack = LIFO | Queue = FIFO
```

---

*Day 15 Complete | Phase 1, Week 3 | BPSC TRE 4.0 Preparation*
*Total Questions Today: 50 (25 CS + 25 GS) | Format: BPSC 5-option style*
*Keep going — every day compounds! 🎯*
