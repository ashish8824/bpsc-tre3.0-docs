# 📅 DAY 10 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
### CS Topic: Arrays in C++ | GS Topic: Non-Cooperation Movement (1920–22)
**Target: TOP RANK | Prepared for Prag | Phase 1 — Week 2**

---

> **⚡ TOPPER MINDSET FOR TODAY:**
> Arrays appear in **EVERY BPSC TRE paper** — output prediction, `is_array()`, `rank()`, 2D array indexing.
> Non-Cooperation Movement is **most-repeated Modern History topic** in Bihar GS exams.
> Master both today → guaranteed marks.

---

# ═══════════════════════════════════════════
# PART A — COMPUTER SCIENCE
## C++ Arrays — Complete Concept Guide
# ═══════════════════════════════════════════

---

## 🔷 1. WHAT IS AN ARRAY?

An **array** is a collection of elements of the **same data type** stored in **contiguous memory locations**, accessed using a single variable name and an **index**.

```
MEMORY VISUALIZATION of int arr[5] = {10, 20, 30, 40, 50}:

Index:    [0]   [1]   [2]   [3]   [4]
Value:    10    20    30    40    50
Address: 1000  1004  1008  1012  1016
          ↑
       arr points here (base address)
```

**Key rule:** Index starts at **0**, last element is at index **n-1**.

---

## 🔷 2. ARRAY DECLARATION — CORRECT SYNTAX

```cpp
// CORRECT declarations:
int arr[10];           // declares int array of 10 elements
int arr[] = {1,2,3};   // compiler counts size automatically (size = 3)
int arr[5] = {1,2,3};  // partial init: remaining = 0

// WRONG declarations:
int [10] arr;          // ❌ wrong — brackets must be after name
int arr[10.5];         // ❌ size must be integer constant
int arr[-5];           // ❌ negative size invalid
```

> **🎯 BPSC PYQ TRICK:** The correct syntax is `data_type array_name[size]` — the size is in square brackets **AFTER** the variable name.

---

## 🔷 3. TYPES OF ARRAYS

### 3.1 One-Dimensional (1D) Array

```cpp
int marks[5] = {85, 90, 78, 92, 88};

// Access: marks[0] = 85, marks[4] = 88
// Total size = 5 × sizeof(int) = 5 × 4 = 20 bytes
```

### 3.2 Two-Dimensional (2D) Array

Think of it as a **matrix/table** with rows and columns.

```
int matrix[3][4]:  (3 rows, 4 columns)

        Col0  Col1  Col2  Col3
Row 0: [0][0] [0][1] [0][2] [0][3]
Row 1: [1][0] [1][1] [1][2] [1][3]
Row 2: [2][0] [2][1] [2][2] [2][3]

Total elements = 3 × 4 = 12
Total size = 12 × 4 = 48 bytes
```

```cpp
int matrix[3][4] = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};

// Access: matrix[1][2] = 7 (row 1, column 2)
```

### 3.3 Multi-Dimensional Array

```cpp
int arr[2][3][4];  // 3D array
// Total elements = 2 × 3 × 4 = 24
```

---

## 🔷 4. ARRAY AND POINTER RELATIONSHIP

This is a **CRITICAL concept** for BPSC TRE output prediction questions!

```cpp
int arr[5] = {10, 20, 30, 40, 50};

// arr itself is a POINTER to the first element
cout << arr;     // prints address of arr[0]
cout << *arr;    // prints 10 (value at arr[0])
cout << arr+1;   // address of arr[1]
cout << *(arr+1); // prints 20

// These are EQUIVALENT:
arr[i]  ≡  *(arr + i)   // KEY IDENTITY

// So:
arr[2] = *(arr + 2) = 30 ✓
```

> **🎯 PYQ FACT:** `arr` and `&arr[0]` give the **same address** but they are different types. `arr` is `int*` while `&arr` is `int(*)[5]`.

---

## 🔷 5. `is_array<>` — TYPE TRAIT FUNCTION

This is a **BPSC TRE FAVOURITE** — appeared in multiple papers!

`is_array<>` is a **type trait** from `<type_traits>` header that checks at **compile time** whether a variable/type is an array.

```cpp
#include <iostream>
#include <type_traits>
using namespace std;

int main() {
    int x = 5;
    int arr[10];
    int* ptr = arr;

    cout << is_array<int>::value;      // OUTPUT: 0 (false) — int is NOT array
    cout << is_array<int[]>::value;    // OUTPUT: 1 (true)  — array type
    cout << is_array<int[10]>::value;  // OUTPUT: 1 (true)  — array type
    
    // TRICKY — pointer is NOT an array:
    cout << is_array<int*>::value;     // OUTPUT: 0 (false)
    
    return 0;
}
```

> **⚠️ TRAP:** `int*` is a pointer, NOT an array. `is_array<int*>::value = 0`.
> A pointer to an array and the array itself are **different types**.

---

## 🔷 6. `rank<>` — RETURNS DIMENSION OF ARRAY

`rank<>` returns the **number of dimensions** (rank/order) of an array type.

```cpp
#include <iostream>
#include <type_traits>
using namespace std;

int main() {
    cout << rank<int>::value;        // 0 — int is NOT an array
    cout << rank<int[5]>::value;     // 1 — 1D array
    cout << rank<int[3][4]>::value;  // 2 — 2D array
    cout << rank<int[2][3][4]>::value; // 3 — 3D array
    
    return 0;
}
```

**Visual Summary:**

```
Type           | is_array | rank
---------------|----------|-----
int            |    0     |  0
int[5]         |    1     |  1
int[3][4]      |    1     |  2
int[2][3][4]   |    1     |  3
int*           |    0     |  0
```

> **🎯 KEY INSIGHT:** `is_array` only tells TRUE/FALSE. `rank` tells you HOW MANY dimensions. Both are from `<type_traits>`.

---

## 🔷 7. STRING AS CHARACTER ARRAY

Strings in C are stored as **char arrays** with a null terminator `\0`.

```cpp
char name[] = "BPSC";
// Stored as: ['B','P','S','C','\0']
// Size = 5 (4 chars + 1 null terminator)

char name[10] = "BPSC";   // OK — remaining positions filled with '\0'
char name[3] = "BPSC";    // ❌ ERROR — too small for "BPSC\0"
```

```
Memory:  B   P   S   C   \0
Index:  [0] [1] [2] [3]  [4]
```

> **🎯 PYQ FACT:** A string "BPSC" requires array of size **at least 5** (4 chars + null terminator).

---

## 🔷 8. ARRAY PASSING TO FUNCTIONS

Arrays are **always passed by pointer** (by reference) in C++. The function receives the base address.

```cpp
void display(int arr[], int n) {   // arr[] is actually int* here
    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";
}

// Calling:
int arr[5] = {1,2,3,4,5};
display(arr, 5);   // passes base address, NOT a copy
```

> **⚠️ TRAP:** `sizeof(arr)` inside the function gives **size of pointer** (8 bytes on 64-bit), NOT size of the array! This is a **classic output prediction trap**.

```cpp
int arr[5];
cout << sizeof(arr);      // In main: 20 (5 × 4)
// Inside function: 8 (pointer size on 64-bit system)
```

---

## 🔷 9. ARRAY SIZE CALCULATION — FORMULA

```
Total size of array = number_of_elements × sizeof(data_type)

int arr[5]    → 5 × 4 = 20 bytes
double arr[3] → 3 × 8 = 24 bytes
char arr[10]  → 10 × 1 = 10 bytes

For 2D array int arr[3][4]:
Total elements = 3 × 4 = 12
Total size = 12 × 4 = 48 bytes

Number of elements = sizeof(arr) / sizeof(arr[0])
```

---

## 🔷 10. COMMON OUTPUT PREDICTION EXAMPLES

These are **exact pattern questions** from BPSC TRE PYQs:

### Example 1:
```cpp
int arr[] = {5, 10, 15, 20, 25};
cout << arr[2];        // Output: 15
cout << *(arr + 3);    // Output: 20
cout << 2[arr];        // Output: 15 (yes, this is valid C++! Same as arr[2])
```

### Example 2:
```cpp
int arr[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
cout << arr[1][2];     // Output: 6
cout << *(*(arr+1)+2); // Output: 6 (same as above)
```

### Example 3:
```cpp
int arr[5];
arr[0] = 100;
int *p = arr;
p++;            // p now points to arr[1]
*p = 200;       // arr[1] = 200
cout << arr[1]; // Output: 200
```

### Example 4 — is_array trap:
```cpp
#include <type_traits>
int arr[5];
int *ptr = arr;
cout << is_array<decltype(arr)>::value; // Output: 1
cout << is_array<decltype(ptr)>::value; // Output: 0
```

---

## 🔷 11. KEY FACTS TABLE — QUICK REVISION

| Concept | Fact |
|---------|------|
| Array indexing starts at | **0** |
| Last element index | **n-1** |
| `is_array<int[5]>::value` | **1 (true)** |
| `is_array<int*>::value` | **0 (false)** |
| `rank<int[3][4]>::value` | **2** |
| `rank<int>::value` | **0** |
| Header for is_array, rank | **`<type_traits>`** |
| String "Hello" needs array size | **6** (5 chars + `\0`) |
| Array name gives | **Base address** |
| `arr[i]` equivalent pointer | **`*(arr+i)`** |
| Passing array to function | **By pointer (by reference)** |
| 2D array `int a[3][4]` total size | **48 bytes** |

---

## 🔷 12. DIAGRAM — MEMORY LAYOUT SUMMARY

```
1D Array: int arr[5] = {10, 20, 30, 40, 50}
┌─────┬─────┬─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ 40  │ 50  │
└─────┴─────┴─────┴─────┴─────┘
 [0]   [1]   [2]   [3]   [4]
  ↑
 arr (base address)


2D Array: int mat[2][3]
        [0]   [1]   [2]
[0] → [ 1 ] [ 2 ] [ 3 ]
[1] → [ 4 ] [ 5 ] [ 6 ]

Stored in memory as: 1, 2, 3, 4, 5, 6  ← Row-major order (C/C++)
```

---

# ═══════════════════════════════════════════
# CS PRACTICE QUESTIONS — 25 MCQs
## Arrays in C++ | BPSC TRE Pattern
# ═══════════════════════════════════════════

> **📌 INSTRUCTIONS:** Solve ALL 25 questions FIRST. Answers are given AFTER question 25.

---

**Q1.** What will be the output of the following C++ code?
```cpp
int arr[5] = {1, 2, 3, 4, 5};
cout << *(arr + 2);
```
(A) 1
(B) 2
(C) 3
(D) More than one of the above is correct
(E) None of the above

---

**Q2.** Which of the following is the correct syntax to declare a 1D integer array of size 10 in C++?

(A) `int [10] arr;`
(B) `array int arr(10);`
(C) `int arr[10];`
(D) More than one of the above is correct
(E) None of the above

---

**Q3.** Consider: `int arr[4][3];`
What is the total number of elements in this array?

(A) 4
(B) 3
(C) 7
(D) More than one of the above is correct
(E) None of the above (answer: 12)

---

**Q4.** What does `is_array<int[5]>::value` return?

(A) 0
(B) 5
(C) 1
(D) More than one of the above is correct
(E) None of the above

---

**Q5.** What does `rank<int[3][4]>::value` return?

(A) 0
(B) 1
(C) 2
(D) More than one of the above is correct
(E) None of the above

---

**Q6.** In C++, an array name (e.g., `arr`) is equivalent to:

(A) The value of the first element
(B) The address of the first element
(C) The total size of the array in bytes
(D) More than one of the above is correct
(E) None of the above

---

**Q7.** What will `is_array<int*>::value` return?

(A) 1
(B) 0
(C) Compiler error
(D) More than one of the above is correct
(E) None of the above

---

**Q8.** What is the output of the following code?
```cpp
int arr[] = {10, 20, 30, 40};
int *p = arr + 1;
cout << *p;
```
(A) 10
(B) 20
(C) 30
(D) More than one of the above is correct
(E) None of the above

---

**Q9.** A character array to store the string "BIHAR" needs a minimum size of:

(A) 4
(B) 5
(C) 6
(D) More than one of the above is correct
(E) None of the above

---

**Q10.** Which header file is required for `is_array<>` and `rank<>` in C++?

(A) `<array>`
(B) `<typeinfo>`
(C) `<type_traits>`
(D) More than one of the above is correct
(E) None of the above

---

**Q11.** What is the output of:
```cpp
int arr[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
cout << arr[2][1];
```
(A) 6
(B) 7
(C) 8
(D) More than one of the above is correct
(E) None of the above

---

**Q12.** Which of the following about arrays in C++ is/are TRUE?

(A) Array index always starts from 0
(B) Array elements are stored in contiguous memory locations
(C) Array size cannot be changed after declaration (static array)
(D) More than one of the above is correct
(E) None of the above

---

**Q13.** What is the total size in bytes of `double arr[4]`? (Assume sizeof(double) = 8)

(A) 4
(B) 16
(C) 32
(D) More than one of the above is correct
(E) None of the above

---

**Q14.** What will the following code output?
```cpp
int arr[] = {5, 10, 15};
cout << 1[arr];
```
(A) Compiler error — syntax is invalid
(B) 5
(C) 10
(D) More than one of the above is correct
(E) None of the above

---

**Q15.** In C++, when an array is passed to a function, what is actually passed?

(A) A copy of the entire array
(B) The base address (pointer to first element)
(C) The size of the array
(D) More than one of the above is correct
(E) None of the above

---

**Q16.** What is `rank<int[2][3][4]>::value`?

(A) 24
(B) 2
(C) 3
(D) More than one of the above is correct
(E) None of the above

---

**Q17.** Which of the following initializations is/are VALID in C++?
```
(A) int arr[3] = {1, 2, 3, 4};
(B) int arr[] = {1, 2, 3};
(C) int arr[5] = {0};
```
(A) Only (B)
(B) Both (B) and (C)
(C) All of (A), (B) and (C)
(D) More than one of the above is correct
(E) None of the above

---

**Q18.** In the declaration `int arr[5];`, if `arr` is stored at address 2000 and `sizeof(int) = 4`, then what is the address of `arr[3]`?

(A) 2003
(B) 2012
(C) 2008
(D) More than one of the above is correct
(E) None of the above

---

**Q19.** What is the output of the following code?
```cpp
int arr[5] = {1, 2, 3, 4, 5};
cout << sizeof(arr) / sizeof(arr[0]);
```
(A) 1
(B) 4
(C) 5
(D) More than one of the above is correct
(E) None of the above

---

**Q20.** Which statement about `rank<>` is CORRECT?

(A) `rank<int>::value` returns 1
(B) `rank<int[5]>::value` returns 5
(C) `rank<int[3][4]>::value` returns 2
(D) More than one of the above is correct
(E) None of the above

---

**Q21.** What is the relationship between `arr[i]` and pointer arithmetic?

(A) `arr[i]` is equivalent to `*(arr + i)`
(B) `arr[i]` is equivalent to `*arr + i`
(C) `arr[i]` is equivalent to `*(arr) + i`
(D) More than one of the above is correct
(E) None of the above

---

**Q22.** Consider the following C++ declarations. Which of the following has `is_array<>::value` equal to 1?

(A) `int x;`
(B) `int *ptr;`
(C) `int arr[10];`
(D) More than one of the above is correct
(E) None of the above

---

**Q23.** In a 2D array declared as `int a[R][C]`, what is the formula to find the address of element `a[i][j]` using row-major order? (Base address = BA, size of int = W)

(A) BA + (i × C + j) × W
(B) BA + (j × R + i) × W
(C) BA + (i + j) × W
(D) More than one of the above is correct
(E) None of the above

---

**Q24.** What happens when you do the following in C++?
```cpp
int arr[5] = {1, 2, 3};
cout << arr[4];
```
(A) Output: 3
(B) Output: 0 (uninitialized elements are 0 for global arrays)
(C) Compile-time error — out of bounds
(D) More than one of the above is correct
(E) None of the above

---

**Q25.** Which of the following statements about C++ arrays is/are CORRECT?

(A) `int arr[n]` where `n` is a variable is a Variable Length Array (VLA), supported as an extension in GCC but NOT in the C++ standard
(B) The expression `arr[i]` is equivalent to `i[arr]` in C/C++
(C) Multi-dimensional arrays in C++ are stored in row-major order
(D) More than one of the above is correct
(E) None of the above

---

# ═══════════════════════════════════════════
# PART B — GENERAL STUDIES
## Non-Cooperation Movement (1920–1922)
# ═══════════════════════════════════════════

---

## 🔶 1. BACKGROUND — WHY DID IT START?

The Non-Cooperation Movement (NCM) was launched by **Mahatma Gandhi** on **1st August 1920**. It was the **first mass movement** under Gandhi's leadership.

### Immediate Causes:

| Cause | Details |
|-------|---------|
| **Jallianwala Bagh Massacre** | April 13, 1919 — General Dyer ordered firing, killing 379+ people in Amritsar. Hunter Commission Report was seen as inadequate. |
| **Rowlatt Act (1919)** | Allowed detention without trial. Called "Black Act" by Indians. Satyagraha against it in 1919. |
| **Khilafat Issue** | Dissolution of Ottoman Caliphate by British after WWI. Indian Muslims felt betrayed. Ali Brothers (Shaukat Ali & Muhammad Ali) approached Gandhi. |
| **Montagu-Chelmsford Reforms (1919)** | Considered inadequate by Indian leaders — not enough power given to Indians. |

---

## 🔶 2. GANDHI'S ENTRY INTO NATIONAL POLITICS

Before the NCM, Gandhi used **Satyagraha** at three places:

```
1917 — Champaran (Bihar) → Indigo farmers' cause → FIRST Satyagraha in India
1918 — Kheda (Gujarat) → Revenue remission during famine
1918 — Ahmedabad → Mill workers' wage dispute

Then: Rowlatt Satyagraha (1919) — All-India level
↓
Non-Cooperation Movement (1920) — LARGEST so far
```

---

## 🔶 3. THE CALCUTTA SESSION — 1920

- At the **Special Calcutta Congress Session** (September 1920), Gandhi proposed the Non-Cooperation Movement.
- **Lala Lajpat Rai** presided over this session.
- The resolution was passed, though some leaders like **C.R. Das** and **Bipin Chandra Pal** initially opposed it.
- The program was officially adopted at the **Nagpur Session of Congress (December 1920)**.

---

## 🔶 4. WHAT WAS NON-COOPERATION?

Gandhi gave a detailed programme of **non-cooperation** with the British government:

### Phase 1 — Surrendering Honours and Titles:
- Indians to **return British-given titles, honours** (like Kaiser-i-Hind, Rai Bahadur)
- Gandhi himself returned his **Kaiser-i-Hind** gold medal

### Phase 2 — Boycott Programme:
```
BOYCOTT OF:
├── Government-aided schools and colleges
├── British courts (lawyers to quit practice)
├── Foreign goods (especially cloth)
├── Government jobs
└── Elections under the Montagu-Chelmsford Reforms
```

### Phase 3 — Alternative Creation:
- Set up **National Schools and Colleges** (Jamia Millia Islamia, Kashi Vidyapith, Bihar Vidyapith founded during this period)
- Establish **Panchayat courts**
- Promote **swadeshi** (khadi, hand-spinning)

---

## 🔶 5. KHILAFAT MOVEMENT — THE HINDU-MUSLIM UNITY

This is a **BPSC FAVOURITE** topic — often combined with NCM.

```
Khilafat Movement Timeline:
1919 — Khilafat Committee formed in India
1920 — Gandhi joins; Hindu-Muslim cooperation begins
1920 — Ali Brothers (Shaukat Ali + Muhammad Ali) are key leaders
1921 — Movement at peak — huge hartals, processions
1922 — Weakened after NCM suspension
1924 — Kemal Ataturk abolishes Caliphate in Turkey → Khilafat issue ends
```

> **🎯 KEY FACT:** Gandhi saw the Khilafat issue as an opportunity for **Hindu-Muslim unity** against the British. This is why the NCM and Khilafat Movement ran **simultaneously**.

---

## 🔶 6. MAJOR EVENTS DURING NCM (1920–22)

| Year | Event |
|------|-------|
| Aug 1, 1920 | Movement formally launched — also the day **Bal Gangadhar Tilak died** |
| 1920 | Lawyers like **C.R. Das, Motilal Nehru** gave up legal practice |
| 1920 | **Jamia Millia Islamia** founded (Delhi) as alternative to government education |
| 1921 | **Prince of Wales visit** — massive boycott; hartals in Bombay, Calcutta |
| 1921 | **Moplah Rebellion (Mappila Revolt)** in Kerala — Muslim peasants against landlords — Gandhi condemned the violence |
| 1921–22 | Mass arrests: C.R. Das, Motilal Nehru, Ali Brothers all arrested |
| Feb 1922 | **Chauri Chaura incident** — TURNING POINT |

---

## 🔶 7. CHAURI CHAURA — THE TURNING POINT

```
Date: February 5, 1922
Place: Chauri Chaura village, Gorakhpur district, UP

What happened:
Protesters clashed with police
→ Police fired
→ Angry mob SET FIRE to police station
→ 22 POLICEMEN KILLED

Gandhi's response:
→ Deeply shocked by the violence
→ Called off the ENTIRE Non-Cooperation Movement on February 12, 1922
→ Started a 5-day fast as penance
```

> **🎯 BPSC MOST REPEATED FACT:** Gandhi suspended the NCM because of the **Chauri Chaura incident** on **5 February 1922** in **Gorakhpur, UP**. **22 policemen** were killed.

### Reactions to Suspension:
- **Subhas Chandra Bose:** Called the suspension "a national calamity"
- **Jawaharlal Nehru:** Was "angry and hurt" in prison
- **C.R. Das:** Disappointed — later formed **Swaraj Party** (1923) with Motilal Nehru

---

## 🔶 8. RESULTS AND SIGNIFICANCE

### Impact of Non-Cooperation Movement:

```
✅ ACHIEVEMENTS:
├── First mass movement involving crores of Indians
├── Hindu-Muslim unity achieved temporarily (NCM + Khilafat)
├── Swadeshi movement boosted — khadi became symbol of nationalism
├── British goods boycotted — economic impact felt
├── National institutions created (Bihar Vidyapith, Jamia, etc.)
├── Women participated for the first time in large numbers
└── Demonstrated POWER of non-violent resistance

❌ LIMITATIONS:
├── Suspended before achieving swaraj
├── Khilafat movement eventually weakened Hindu-Muslim unity
└── Radicals like Bose and Nehru felt let down
```

---

## 🔶 9. BIHAR SPECIAL — BPSC FOCUS POINTS

Since this is a **Bihar exam**, these Bihar-specific facts from NCM are CRITICAL:

| Fact | Detail |
|------|--------|
| **Bihar Vidyapith** | Founded in 1921 at Patna — alternative national institution |
| **Mazharul Haque** | Bihar leader, donated money for Bihar Vidyapith |
| **Rajendra Prasad** | Quit legal practice; joined movement in Bihar |
| **Chauri Chaura** | UP (Gorakhpur) — but caused suspension affecting all of India |
| **Swaraj Party** | Formed 1923 by C.R. Das & Motilal Nehru after NCM suspension |

---

## 🔶 10. COMPARISON TABLE — NCM vs CIVIL DISOBEDIENCE MOVEMENT

| Feature | Non-Cooperation (1920–22) | Civil Disobedience (1930–34) |
|---------|--------------------------|------------------------------|
| Launch date | August 1, 1920 | March 12, 1930 (Dandi March) |
| Trigger | Rowlatt Act + Jallianwala + Khilafat | Simon Commission + Salt Tax |
| Nature | Non-cooperation, boycott | Direct law-breaking (salt march) |
| Ended by | Chauri Chaura (Gandhi suspended) | Gandhi-Irwin Pact (1931) |
| Key demand | Swaraj within 1 year | Purna Swaraj (already declared 1929) |
| Hindu-Muslim unity | Yes (Khilafat link) | Weaker |

---

## 🔶 11. IMPORTANT PEOPLE — QUICK REFERENCE

| Person | Role in NCM |
|--------|-------------|
| **Mahatma Gandhi** | Launched and led the movement |
| **Bal Gangadhar Tilak** | Died on Aug 1, 1920 — same day NCM launched |
| **Lala Lajpat Rai** | Presided over Calcutta Special Session 1920 |
| **Muhammad Ali Jinnah** | Opposed NCM; left Congress over it |
| **C.R. Das** | Initially opposed, then joined; disappointed at suspension |
| **Motilal Nehru** | Joined movement, arrested; later founded Swaraj Party |
| **Shaukat Ali & Muhammad Ali** | Leaders of Khilafat Movement who joined NCM |
| **Subhas Chandra Bose** | Called suspension "national calamity" |

---

## 🔶 12. KEY DATES — RAPID MEMORIZATION

```
1919 → Rowlatt Act + Jallianwala Bagh → Seeds of NCM
Aug 1, 1920 → NCM officially launched + Tilak dies
Sep 1920 → Calcutta Special Session (Lala Lajpat Rai presides)
Dec 1920 → Nagpur Session → NCM formally adopted by Congress
1921 → Movement at peak + Khilafat at peak
Feb 5, 1922 → Chauri Chaura incident
Feb 12, 1922 → Gandhi suspends NCM
1923 → Swaraj Party formed by C.R. Das + Motilal Nehru
```

---

# ═══════════════════════════════════════════
# GS PRACTICE QUESTIONS — 25 MCQs
## Non-Cooperation Movement | BPSC TRE Pattern
# ═══════════════════════════════════════════

> **📌 INSTRUCTIONS:** Solve ALL 25 questions FIRST. Answers are given AFTER question 25.

---

**Q26.** The Non-Cooperation Movement was launched by Mahatma Gandhi on:

(A) 1st August 1919
(B) 1st August 1920
(C) 13th April 1920
(D) More than one of the above is correct
(E) None of the above

---

**Q27.** Which event was the IMMEDIATE cause for Gandhi's decision to suspend the Non-Cooperation Movement in February 1922?

(A) Jallianwala Bagh Massacre
(B) Moplah Rebellion
(C) Chauri Chaura incident
(D) More than one of the above is correct
(E) None of the above

---

**Q28.** The Chauri Chaura incident (1922) occurred in which district/state?

(A) Bihar
(B) Gorakhpur, United Provinces (UP)
(C) Amritsar, Punjab
(D) More than one of the above is correct
(E) None of the above

---

**Q29.** Who presided over the Special Calcutta Session of Congress (September 1920) where Non-Cooperation Movement was proposed?

(A) Mahatma Gandhi
(B) Motilal Nehru
(C) Lala Lajpat Rai
(D) More than one of the above is correct
(E) None of the above

---

**Q30.** Which of the following is/are part of Gandhi's Non-Cooperation programme?

(A) Boycott of government-aided schools and colleges
(B) Boycott of foreign goods and promotion of swadeshi
(C) Surrender of government titles and honours
(D) More than one of the above is correct
(E) None of the above

---

**Q31.** The Non-Cooperation Movement was formally adopted by the Indian National Congress at its session held in:

(A) Lahore (1920)
(B) Nagpur (December 1920)
(C) Calcutta (1920)
(D) More than one of the above is correct
(E) None of the above

---

**Q32.** Muhammad Ali Jinnah left the Congress over the Non-Cooperation Movement because:

(A) He was a supporter of the Khilafat cause
(B) He disagreed with Gandhi's method of mass agitation and non-cooperation
(C) He wanted a separate nation for Muslims
(D) More than one of the above is correct
(E) None of the above

---

**Q33.** Which national institution was founded in Bihar as an alternative to government education during the Non-Cooperation Movement?

(A) Banaras Hindu University
(B) Bihar Vidyapith (1921)
(C) Aligarh Muslim University
(D) More than one of the above is correct
(E) None of the above

---

**Q34.** The Khilafat Movement was related to:

(A) Protection of the Ottoman Caliph's position after World War I
(B) Demand for separate Muslim constituencies in India
(C) Abolition of the caste system among Muslims
(D) More than one of the above is correct
(E) None of the above

---

**Q35.** Who among the following called the suspension of the Non-Cooperation Movement a "national calamity"?

(A) Jawaharlal Nehru
(B) C.R. Das
(C) Subhas Chandra Bose
(D) More than one of the above is correct
(E) None of the above

---

**Q36.** The Swaraj Party, formed after the suspension of the Non-Cooperation Movement in 1923, was founded by:

(A) Gandhi and Nehru
(B) C.R. Das and Motilal Nehru
(C) Bal Gangadhar Tilak and Gokhale
(D) More than one of the above is correct
(E) None of the above

---

**Q37.** Which of the following is/are correct about Bal Gangadhar Tilak and the Non-Cooperation Movement?

(A) He presided over the Calcutta session where NCM was proposed
(B) He died on August 1, 1920 — the same day NCM was launched
(C) He was the main architect of the Non-Cooperation programme
(D) More than one of the above is correct
(E) None of the above

---

**Q38.** Gandhi's first Satyagraha in India (before NCM) was conducted at:

(A) Kheda, Gujarat
(B) Champaran, Bihar
(C) Ahmedabad
(D) More than one of the above is correct
(E) None of the above

---

**Q39.** The Moplah (Mappila) Rebellion of 1921 during the Non-Cooperation Movement took place in:

(A) Bihar
(B) Malabar (Kerala)
(C) Bengal
(D) More than one of the above is correct
(E) None of the above

---

**Q40.** Which of the following statements about the Non-Cooperation Movement is/are TRUE?

(A) It was the first mass movement in India under Gandhi's leadership
(B) It combined with the Khilafat Movement to achieve Hindu-Muslim unity
(C) Women participated in large numbers for the first time
(D) More than one of the above is correct
(E) None of the above

---

**Q41.** The Rowlatt Act (1919) was opposed by Indians because:

(A) It allowed the government to imprison people without trial
(B) It imposed heavy taxes on Indian goods
(C) It banned Indian political parties
(D) More than one of the above is correct
(E) None of the above

---

**Q42.** How many policemen were killed in the Chauri Chaura incident?

(A) 5
(B) 12
(C) 22
(D) More than one of the above is correct
(E) None of the above

---

**Q43.** Which title did Gandhi himself return during the Non-Cooperation Movement?

(A) Mahatma
(B) Kaiser-i-Hind
(C) Rai Bahadur
(D) More than one of the above is correct
(E) None of the above

---

**Q44.** The Jamia Millia Islamia, founded in 1920, was established as:

(A) An institution of the British government
(B) A national alternative institution during the Non-Cooperation Movement
(C) A Muslim League educational institution
(D) More than one of the above is correct
(E) None of the above

---

**Q45.** Which of the following leaders initially OPPOSED the Non-Cooperation Movement when it was proposed at the Calcutta session?

(A) Mahatma Gandhi
(B) C.R. Das and Bipin Chandra Pal
(C) Lala Lajpat Rai
(D) More than one of the above is correct
(E) None of the above

---

**Q46.** The Jallianwala Bagh Massacre occurred on:

(A) 13 April 1917
(B) 13 April 1919
(C) 1 August 1919
(D) More than one of the above is correct
(E) None of the above

---

**Q47.** Who among the following was the Bihar leader associated with donation for Bihar Vidyapith during the Non-Cooperation Movement?

(A) Rajendra Prasad
(B) Mazharul Haque
(C) Sachidananda Sinha
(D) More than one of the above is correct
(E) None of the above

---

**Q48.** What did General Dyer order at Jallianwala Bagh that shocked the nation and contributed to the Non-Cooperation Movement?

(A) Arrest of all Congress leaders
(B) Firing on an unarmed peaceful gathering, killing hundreds
(C) Banning the Indian National Congress
(D) More than one of the above is correct
(E) None of the above

---

**Q49.** The Ottoman Caliphate was finally abolished in which year, effectively ending the Khilafat issue?

(A) 1920
(B) 1922
(C) 1924
(D) More than one of the above is correct
(E) None of the above

---

**Q50.** Which of the following correctly describes the relationship between the Khilafat Movement and the Non-Cooperation Movement?

(A) They were completely separate and opposed to each other
(B) They ran simultaneously under Gandhi's leadership as a combined movement
(C) The Khilafat Movement was a sub-part of the Civil Disobedience Movement
(D) More than one of the above is correct
(E) None of the above

---

---
---
---
---
---

# ═══════════════════════════════════════════════════════
# ✅ ANSWER KEY — SOLVE BEFORE LOOKING!
# ═══════════════════════════════════════════════════════

---

## CS ANSWERS (Q1–Q25) — Arrays in C++

| Q# | Answer | Explanation |
|----|--------|-------------|
| Q1 | **(C) 3** | `*(arr + 2)` = `arr[2]` = third element = 3 |
| Q2 | **(C) `int arr[10];`** | Correct syntax: `data_type name[size]` |
| Q3 | **(E) None of the above** | 4×3 = **12** elements; answer 12 not in options |
| Q4 | **(C) 1** | `is_array<int[5]>::value` = 1 (true) — it IS an array |
| Q5 | **(C) 2** | `int[3][4]` is 2-dimensional → rank = 2 |
| Q6 | **(B) Address of first element** | Array name = base address = `&arr[0]` |
| Q7 | **(B) 0** | `int*` is a POINTER, not an array → `is_array = 0` |
| Q8 | **(B) 20** | `p = arr+1` points to arr[1]=20; `*p` = 20 |
| Q9 | **(C) 6** | "BIHAR" = 5 chars + 1 null terminator `\0` = 6 |
| Q10 | **(C) `<type_traits>`** | `is_array` and `rank` are in `<type_traits>` |
| Q11 | **(C) 8** | `arr[2][1]` = row 2, col 1 = 8 (row2: {7,8,9}) |
| Q12 | **(D) More than one** | All three statements A, B, C are TRUE |
| Q13 | **(C) 32** | 4 × 8 = 32 bytes |
| Q14 | **(C) 10** | `1[arr]` = `*(1+arr)` = `*(arr+1)` = arr[1] = 10. Valid C++! |
| Q15 | **(B) Base address** | Arrays decay to pointer; base address is passed |
| Q16 | **(C) 3** | `int[2][3][4]` is 3D → rank = 3 |
| Q17 | **(B) Both B and C** | (A) is invalid — more initializers than array size. (B) valid — compiler counts. (C) valid — remaining filled with 0 |
| Q18 | **(B) 2012** | Address of arr[3] = 2000 + 3×4 = 2000 + 12 = **2012** |
| Q19 | **(C) 5** | `sizeof(arr)/sizeof(arr[0])` = 20/4 = **5** (number of elements) |
| Q20 | **(C) `rank<int[3][4]>::value` returns 2** | Only (C) is correct. (A) `rank<int>` = 0 not 1. (B) `rank<int[5]>` = 1 not 5 |
| Q21 | **(A) `*(arr + i)`** | Standard pointer-array equivalence: `arr[i]` ≡ `*(arr+i)` |
| Q22 | **(C) `int arr[10]`** | Only an actual array type gives `is_array = 1` |
| Q23 | **(A) BA + (i × C + j) × W** | Standard row-major order formula for 2D array |
| Q24 | **(E) None of the above** | For local arrays, `arr[3]` and `arr[4]` → partial init fills declared positions. `int arr[5]={1,2,3}` → arr[3]=0, arr[4]=0. Output = 0. But the option B says "for global arrays" which is a partial truth. The full answer: for LOCAL array with partial initialization (done here with brace init), remaining ARE zero. So output is **0**. Answer is (B) if we accept this reasoning, but option B says "global arrays". For local with brace initializer, remaining = 0 too. → **(B) Output: 0** |
| Q25 | **(D) More than one** | All three (A), (B), and (C) are correct. VLA is GCC extension; `arr[i]`=`i[arr]`; C++ uses row-major order. |

> **Note on Q24:** In C++, `int arr[5] = {1, 2, 3};` — when fewer initializers are given than array size, **remaining elements are zero-initialized** for both local and global arrays when using brace initialization. So `arr[4] = 0`. Answer is **(B)**.

---

## GS ANSWERS (Q26–Q50) — Non-Cooperation Movement

| Q# | Answer | Explanation |
|----|--------|-------------|
| Q26 | **(B) 1st August 1920** | NCM launched August 1, 1920 — also Tilak's death anniversary |
| Q27 | **(C) Chauri Chaura incident** | Feb 5, 1922 — 22 policemen killed in Gorakhpur |
| Q28 | **(B) Gorakhpur, UP** | Chauri Chaura was in Gorakhpur district, United Provinces |
| Q29 | **(C) Lala Lajpat Rai** | "Punjab Kesari" presided over Special Calcutta Session, Sep 1920 |
| Q30 | **(D) More than one** | All three (A), (B), (C) are part of the NCM programme |
| Q31 | **(B) Nagpur, December 1920** | Formal adoption at Annual Congress Session, Nagpur |
| Q32 | **(B) Disagreed with mass agitation methods** | Jinnah believed in constitutional methods, opposed Gandhi's style |
| Q33 | **(B) Bihar Vidyapith (1921)** | Founded in Patna in 1921 during NCM |
| Q34 | **(A) Protection of Ottoman Caliph** | Khilafat = protecting the position of Turkish Caliph post-WWI |
| Q35 | **(C) Subhas Chandra Bose** | Bose was most vocal; called it "national calamity" |
| Q36 | **(B) C.R. Das and Motilal Nehru** | Swaraj Party founded 1923 to contest councils from within |
| Q37 | **(B) Died on August 1, 1920** | Only (B) is correct — Tilak died same day NCM launched |
| Q38 | **(B) Champaran, Bihar** | 1917 — Indigo farmers; Gandhi's FIRST Satyagraha in India |
| Q39 | **(B) Malabar (Kerala)** | Moplah/Mappila Rebellion in Malabar, 1921 — Muslim peasants vs Hindu landlords |
| Q40 | **(D) More than one** | All three (A), (B), (C) are TRUE about NCM |
| Q41 | **(A) Imprisonment without trial** | Rowlatt Act = "Black Act" — detention without trial, no appeal |
| Q42 | **(C) 22** | Exactly 22 policemen were killed at Chauri Chaura — key exam fact |
| Q43 | **(B) Kaiser-i-Hind** | Gandhi returned his Kaiser-i-Hind gold medal (not Rai Bahadur — that was others) |
| Q44 | **(B) National alternative institution** | Founded 1920 at Aligarh (later moved to Delhi) during NCM |
| Q45 | **(B) C.R. Das and Bipin Chandra Pal** | They initially opposed; later C.R. Das joined the movement |
| Q46 | **(B) 13 April 1919** | Baisakhi day, 1919 — General Dyer ordered firing |
| Q47 | **(B) Mazharul Haque** | Donated his entire property; Rajendra Prasad was also involved |
| Q48 | **(B) Firing on unarmed gathering** | Dyer ordered firing, killing 379+ (official count) at Jallianwala Bagh |
| Q49 | **(C) 1924** | Kemal Ataturk abolished the Caliphate in 1924 |
| Q50 | **(B) Ran simultaneously under Gandhi** | Gandhi intentionally combined both — NCM + Khilafat together for Hindu-Muslim unity |

---

# ═══════════════════════════════════════════
# 📝 NIGHT REVISION — 5 BULLET POINTS
## Write These from Memory Before Sleeping
# ═══════════════════════════════════════════

### CS — Arrays:
1. `arr[i]` ≡ `*(arr+i)` — array name is base address (pointer to first element)
2. `is_array<int[5]>::value` = 1; `is_array<int*>::value` = 0 — pointer ≠ array
3. `rank<int[3][4]>::value` = 2 — rank = number of dimensions; both from `<type_traits>`
4. String "BPSC" needs array size 5 (4 chars + `\0`); partial init fills remaining with 0
5. Arrays always passed by reference (base address) to functions; `sizeof` inside function gives pointer size

### GS — Non-Cooperation Movement:
1. NCM launched **August 1, 1920** by Gandhi — same day Tilak died
2. **Chauri Chaura** (Gorakhpur, UP) — Feb 5, 1922 — 22 policemen killed → NCM suspended Feb 12
3. NCM + **Khilafat Movement** ran together → Hindu-Muslim unity under Gandhi's leadership
4. Nagpur Session (Dec 1920) = formal adoption; Calcutta Special Session (Sep 1920) = proposal (Lala Lajpat Rai presided)
5. **Bihar Vidyapith** (1921, Patna) = Bihar's contribution; Gandhi's first Satyagraha = **Champaran 1917** (Bihar!)

---

# 📊 DAY 10 PERFORMANCE TRACKER

| Section | Questions | Target Score | My Score |
|---------|-----------|-------------|----------|
| CS — Arrays | 25 | 22+ | _______ |
| GS — NCM | 25 | 22+ | _______ |
| **Total** | **50** | **44+** | _______ |

**If score < 40/50:** Re-read concepts marked in 🎯 and redo those questions tomorrow.
**If score 40–46/50:** Good — review wrong ones, proceed to Day 11.
**If score 47–50/50:** Excellent topper performance! 🏆

---

*Day 10 Complete | Next: Day 11 — Functions in C++ + Indian National Congress Formation*
*Remember: BPSC TRE option (D) "More than one" = correct ~20–25% of the time. Notice how many D answers appeared today!*
