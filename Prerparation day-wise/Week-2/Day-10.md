# 📅 BPSC TRE 4.0 — DAY 10 COMPLETE STUDY MODULE
### C++ Arrays (Complete) + Non-Cooperation Movement 1920–22
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): C++ Arrays — 1D, 2D, strings, pointers, is_array(), rank()
> - Afternoon (1 hr): Non-Cooperation Movement — story-based deep understanding
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 C++ Arrays — Complete Deep Dive

---

## 🔷 SECTION 1: What is an Array? (The Foundation)

### Real-Life Analogy — The Train Compartments:
```
Imagine a train with numbered compartments:
Compartment 1, Compartment 2, Compartment 3 ... Compartment 10

→ All compartments are of the SAME type (same size, same train)
→ They are arranged in a CONTINUOUS sequence
→ Each compartment has a unique NUMBER (its address/index)
→ You access any compartment directly by its number

Array = A train of compartments storing the SAME type of data,
        arranged sequentially in memory, each accessed by index.
```

### Technical Definition:
> An **array** is a collection of elements of the **same data type**, stored in **contiguous memory locations**, accessed using an **index**.

### Why Arrays?
```
Without arrays:
  int mark1 = 80, mark2 = 75, mark3 = 90, mark4 = 65, mark5 = 88;
  → Need 5 separate variable names
  → Impossible to loop through them

With arrays:
  int marks[5] = {80, 75, 90, 65, 88};
  → One name, indexed access
  → Easy to loop: for(int i=0; i<5; i++) cout << marks[i];
```

---

## 🔷 SECTION 2: Array Declaration & Initialization

### Syntax:
```
data_type  array_name [size];
```

### Examples of Declaration:
```cpp
int arr[10];          // array of 10 integers (uninitialized)
float scores[5];      // array of 5 floats
char name[20];        // array of 20 characters (string)
double prices[100];   // array of 100 doubles
```

### Initialization at Declaration:
```cpp
// Method 1: Full initialization
int arr[5] = {10, 20, 30, 40, 50};

// Method 2: Partial initialization (rest filled with 0)
int arr[5] = {10, 20};      // arr = {10, 20, 0, 0, 0}

// Method 3: All zeros
int arr[5] = {0};           // arr = {0, 0, 0, 0, 0}
int arr[5] = {};            // same — all zeros

// Method 4: Size inferred from initializer list
int arr[] = {10, 20, 30};   // size automatically = 3

// Method 5: Individual assignment
int arr[3];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
```

### 🚨 PYQ TRAP #1 — Correct Array Declaration Syntax:
```cpp
int array[10];    // ✅ CORRECT — standard C++ array declaration
int array(10);    // ❌ WRONG — this looks like a function call
int[10] array;    // ❌ WRONG — type and size must come before name
10 int array[];   // ❌ WRONG — completely wrong syntax
```
> **The correct format is always: `data_type array_name[size];`**

---

## 🔷 SECTION 3: Indexing — 0-Based System

### The Golden Rule:
```
Array indexing in C++ starts at 0 (ZERO-BASED INDEXING)

For array of size n:
  First element  → index 0       = arr[0]
  Second element → index 1       = arr[1]
  ...
  Last element   → index n-1     = arr[n-1]
```

### Memory Visualization of `int arr[5] = {10, 20, 30, 40, 50}`:
```
Index:     [0]    [1]    [2]    [3]    [4]
           ┌──────┬──────┬──────┬──────┬──────┐
Value:     │  10  │  20  │  30  │  40  │  50  │
           └──────┴──────┴──────┴──────┴──────┘
Address:   1000   1004   1008   1012   1016
           ↑
           arr (base address)

Each int takes 4 bytes → addresses differ by 4
arr[i] is at address: base_address + (i × sizeof(int))
arr[0] → 1000 + (0 × 4) = 1000
arr[2] → 1000 + (2 × 4) = 1008
arr[4] → 1000 + (4 × 4) = 1016
```

### 🚨 PYQ TRAP #2 — Off-by-One Error:
```cpp
int arr[5];         // valid indices: 0, 1, 2, 3, 4
arr[5] = 10;        // ❌ OUT OF BOUNDS — index 5 doesn't exist!
                    // C++ does NOT check bounds — no error at compile time
                    // Results in UNDEFINED BEHAVIOR at runtime

// The last valid index is ALWAYS n-1, where n is the array size
```

### Array Name = Base Address:
```cpp
int arr[5] = {10, 20, 30, 40, 50};
cout << arr;      // prints base address (e.g., 0x7ffe1000)
cout << &arr[0];  // same base address!
// arr == &arr[0] — array name IS the address of its first element
```

---

## 🔷 SECTION 4: 1D Arrays — Complete Operations

### Traversal (Most Common Exam Code):
```cpp
int arr[5] = {10, 20, 30, 40, 50};

// Forward traversal:
for (int i = 0; i < 5; i++) {
    cout << arr[i] << " ";
}
// Output: 10 20 30 40 50

// Using pointer-style access (equivalent):
for (int i = 0; i < 5; i++) {
    cout << *(arr + i) << " ";    // same as arr[i]
}
```

### sizeof() with Arrays:
```cpp
int arr[5];
cout << sizeof(arr);              // Output: 20 (5 × 4 bytes)
cout << sizeof(arr[0]);           // Output: 4 (one int)
cout << sizeof(arr)/sizeof(int);  // Output: 5 (number of elements)
cout << sizeof(arr)/sizeof(arr[0]); // Output: 5 (same, more robust)
```

### 🚨 PYQ TRAP #3 — sizeof() with Passed Array:
```cpp
void printSize(int arr[]) {
    cout << sizeof(arr);  // ⚠️ Output: 4 or 8 (size of POINTER, not array!)
}
// When an array is passed to a function, it DECAYS into a pointer
// sizeof() inside the function gives pointer size, NOT array size
// To get array size inside a function, pass size as separate argument
```

---

## 🔷 SECTION 5: 2D Arrays — Matrix Representation

### Declaration:
```cpp
data_type array_name[rows][columns];
int matrix[3][4];   // 3 rows, 4 columns = 12 elements
```

### Memory Layout (Row-Major Order in C++):
```
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

Visual as a matrix:
    Col 0  Col 1  Col 2
Row 0: [1]    [2]    [3]
Row 1: [4]    [5]    [6]
Row 2: [7]    [8]    [9]

How it's stored in memory (ROW-MAJOR ORDER):
┌───┬───┬───┬───┬───┬───┬───┬───┬───┐
│ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │
└───┴───┴───┴───┴───┴───┴───┴───┴───┘
 [0][0][0][1][0][2][1][0][1][1][1][2][2][0][2][1][2][2]

C++ stores row by row: row 0 first, then row 1, then row 2.
This is called ROW-MAJOR ORDER.
```

### Accessing 2D Array Elements:
```cpp
cout << matrix[1][2];   // Row 1, Col 2 → value 6
cout << matrix[0][0];   // Row 0, Col 0 → value 1
cout << matrix[2][2];   // Row 2, Col 2 → value 9

// Traversal:
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        cout << matrix[i][j] << " ";
    }
    cout << endl;
}
```

### sizeof() with 2D Arrays:
```cpp
int matrix[3][4];
cout << sizeof(matrix);            // 3 × 4 × 4 = 48 bytes
cout << sizeof(matrix[0]);         // 4 × 4 = 16 bytes (one row)
cout << sizeof(matrix[0][0]);      // 4 bytes (one element)
```

### 🚨 PYQ TRAP #4 — Row vs Column:
```cpp
int a[3][4];  // 3 rows, 4 columns → NOT 4 rows, 3 columns!
              // First bracket = ROWS, Second bracket = COLUMNS
              // Total elements = 3 × 4 = 12
```

### Address Calculation for 2D Array:
```
Address of a[i][j] = base_address + (i × columns + j) × sizeof(type)
For a[2][3] in int matrix[4][5]:
= base + (2×5 + 3) × 4
= base + 13 × 4
= base + 52
```

---

## 🔷 SECTION 6: Arrays and Pointers — The Connection

### Key Relationship:
```cpp
int arr[5] = {10, 20, 30, 40, 50};
int* p = arr;     // p points to arr[0] — no & needed!

// These are EQUIVALENT:
arr[i]      ==  *(arr + i)     // array notation = pointer arithmetic
p[i]        ==  *(p + i)       // pointer can use array notation too
&arr[i]     ==  arr + i        // address of element = base + offset
```

### Visual Equivalence:
```
arr[0] = *(arr+0) = *(p+0) = p[0] = 10
arr[1] = *(arr+1) = *(p+1) = p[1] = 20
arr[2] = *(arr+2) = *(p+2) = p[2] = 30
```

### Important Difference — Array vs Pointer:
```cpp
int arr[5];    // arr is a CONSTANT pointer — cannot reassign
int* p = arr;  // p is a regular pointer — can reassign

p++;    // ✅ Valid — p now points to arr[1]
arr++;  // ❌ INVALID — cannot increment array name!
        // arr is a fixed address — it's the array's identity
```

### 🚨 PYQ TRAP #5:
> Array name acts like a **constant pointer** to the first element.
> You CANNOT do `arr++` or `arr = anotherArray`.
> But you CAN do `*(arr+1)` or `arr[1]` — these don't change arr itself.

---

## 🔷 SECTION 7: Strings as Character Arrays

### What is a String in C++?
```cpp
// C-style string = char array with null terminator '\0' at the end
char name[] = "Bihar";
// Internally stored as:
// ['B']['i']['h']['a']['r']['\0']
//  [0]  [1]  [2]  [3]  [4]  [5]
// Size needed = length of string + 1 (for '\0')
```

### Declaring Char Arrays:
```cpp
char str1[] = "Hello";          // size = 6 (5 chars + '\0')
char str2[10] = "World";        // size = 10 (5 chars + '\0' + 4 unused)
char str3[5] = {'H','i','\0'};  // explicit initialization
```

### The Null Terminator `\0`:
```
'H'  'e'  'l'  'l'  'o'  '\0'
 0    1    2    3    4     5   ← indices
                              ↑
                     NULL terminator marks end of string
                     ASCII value of '\0' = 0
```

### String Functions (Important for Exam):
```cpp
#include <cstring>

strlen(str)           // length of string (excludes '\0')
strcpy(dest, src)     // copy src to dest
strcat(dest, src)     // append src to end of dest
strcmp(s1, s2)        // compare: 0 if equal, <0 if s1<s2, >0 if s1>s2
strchr(str, ch)       // find first occurrence of ch in str
strstr(s1, s2)        // find s2 inside s1
```

### 🚨 PYQ TRAP #6 — The Most Tested String Trap:
```cpp
char s1[] = "Hello";
char s2[] = "World";

// ATTEMPT to concatenate using +:
string result = s1 + s2;   // ❌ COMPILE ERROR for char arrays!
                            // '+' operator NOT defined for char arrays

// WHY? s1 and s2 are arrays → they decay to pointers
//      pointer + pointer = INVALID (cannot add two pointers!)
//      Even if one is a char array and the other is a literal:
// s1 + " World"  → this actually adds the pointer value of s1 
//                  to an integer (pointer arithmetic) — NOT concatenation!

// CORRECT WAY:
strcat(s1, s2);   // ✅ Use strcat() for char array concatenation
// OR use C++ std::string:
string str1 = "Hello", str2 = "World";
string result = str1 + str2;  // ✅ Works for std::string objects
```

### char array vs std::string:
| Feature | `char[]` (C-style) | `std::string` (C++) |
|---------|-------------------|-------------------|
| Concatenation | Use `strcat()` | Use `+` operator |
| Length | `strlen()` | `.length()` or `.size()` |
| Comparison | `strcmp()` | `==` operator |
| Memory | Fixed size | Dynamic |
| Header | `<cstring>` | `<string>` |

---

## 🔷 SECTION 8: `is_array()` and `rank()` Functions

### `is_array()` — Type Trait Function:
```cpp
#include <type_traits>

int arr[5];
int x = 10;

cout << is_array<int[5]>::value;  // Output: 1 (true) — it IS an array
cout << is_array<int>::value;     // Output: 0 (false) — not an array
cout << is_array<int*>::value;    // Output: 0 (false) — pointer, not array
```

> **`is_array<T>::value`** returns:
> - `1` (true) if T is an array type
> - `0` (false) if T is not an array type
> It is a **compile-time** type checking tool from `<type_traits>`

### `rank()` — Dimension of Array:
```cpp
#include <type_traits>

int arr1D[5];
int arr2D[3][4];
int arr3D[2][3][4];

cout << rank<int[5]>::value;       // Output: 1 (1-dimensional array)
cout << rank<int[3][4]>::value;    // Output: 2 (2-dimensional array)
cout << rank<int[2][3][4]>::value; // Output: 3 (3-dimensional array)
cout << rank<int>::value;          // Output: 0 (not an array)
```

> **`rank<T>::value`** returns the **number of dimensions** of the array type T.
> - 1D array → rank 1
> - 2D array → rank 2
> - Non-array type → rank 0

### 🚨 PYQ TRAP #7:
```cpp
// is_array checks if the TYPE is an array
// It does NOT check if a variable "looks like" an array
// int* p = new int[5];
// is_array<decltype(p)>::value → 0 (false! — p is a pointer, not array)
// Even though p points to array memory, its TYPE is int*, not array type
```

---

## 🔷 SECTION 9: Passing Arrays to Functions

### How Array Passing Works:
```cpp
// When you pass an array to a function, it DECAYS to a pointer:
void printArray(int arr[], int n) {   // arr is actually int* here
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
}

// These function signatures are IDENTICAL:
void func(int arr[], int n)    // looks like array
void func(int* arr, int n)     // IS a pointer
void func(int arr[10], int n)  // size is IGNORED — still pointer

// Call:
int myArr[5] = {1, 2, 3, 4, 5};
printArray(myArr, 5);   // passes base address of myArr
```

### 🚨 PYQ TRAP #8 — Modification Through Function:
```cpp
void modify(int arr[]) {
    arr[0] = 999;    // THIS MODIFIES THE ORIGINAL ARRAY!
}
// Arrays are passed by reference (pointer to original memory)
// Unlike regular variables, NO COPY is made
// Changes inside function affect the original array
```

---

## 🔷 SECTION 10: Array Initialization — Special Cases

### Default Values:
```cpp
// Global array:
int globalArr[5];    // All elements = 0 (automatic zero-init)

// Local array:
int localArr[5];     // All elements = GARBAGE (uninitialized)

// Local with partial init:
int arr[5] = {1, 2};  // arr = {1, 2, 0, 0, 0}
                       // Remaining elements = 0 (not garbage!)
```

### Variable Length Arrays (VLA):
```cpp
int n = 5;
int arr[n];     // ⚠️ VLA — valid in C99 and some compilers (GCC)
                // NOT part of standard C++11/14/17
                // May not work on all compilers
                // Exam usually tests standard arrays
```

---

## 📊 VISUAL SUMMARY — Complete Array Map

```
C++ ARRAYS — COMPLETE STRUCTURE
│
├── 1D Array: int arr[5]
│   ├── Index: 0 to n-1 (0-based)
│   ├── Memory: Contiguous
│   ├── sizeof(arr) = n × sizeof(type)
│   └── arr == &arr[0] == base address
│
├── 2D Array: int mat[r][c]
│   ├── Row-major storage in C++
│   ├── Access: mat[i][j]
│   ├── sizeof(mat) = r × c × sizeof(type)
│   └── Address of mat[i][j] = base + (i×c + j)×sizeof(type)
│
├── String (char array)
│   ├── char str[] = "Hello" → 6 bytes (5 + '\0')
│   ├── '+' for char arrays → COMPILE ERROR
│   └── Use strcat() for concatenation
│
├── Array-Pointer Relationship
│   ├── arr[i] == *(arr + i)
│   ├── arr is CONSTANT pointer (cannot do arr++)
│   └── When passed to function → DECAYS to pointer
│
└── Type Traits
    ├── is_array<T>::value → 1 (array) or 0 (not array)
    └── rank<T>::value → number of dimensions (0 if not array)
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Non-Cooperation Movement (1920–22) — Story-Based Deep Dive

---

## 🔷 THE BACKGROUND — WHY THE MOVEMENT WAS BORN

### Three Triggers That Built the Fire:

#### Trigger 1: Rowlatt Act — February 1919
```
British Government passed the Rowlatt Act
→ Allowed imprisonment WITHOUT trial
→ No appeal, no lawyer, no jury
→ Indians called it: "No Daleel, No Vakeel, No Appeal"
→ Gandhi called it the "Black Act"
→ Nationwide hartal (strike) called: April 6, 1919
```

#### Trigger 2: Jallianwala Bagh Massacre — April 13, 1919
```
Date: April 13, 1919 (Baisakhi Day — a major harvest festival)
Place: Jallianwala Bagh, Amritsar, Punjab
What happened:
  → Thousands gathered peacefully to protest Rowlatt Act
  → General Reginald Dyer ordered troops to open fire
     WITHOUT any warning
  → Exits were blocked — people had no escape
  → Firing continued for ~10 minutes, 1650 rounds fired
  → Official death toll: 379 (actual estimated: 1000+)
  → Hundreds jumped into the well inside the garden

Aftermath:
  → Rabindranath Tagore returned his Knighthood in protest
  → Michael O'Dwyer (Lt. Governor of Punjab) supported Dyer
  → Udham Singh later assassinated O'Dwyer in 1940 in London
    (to avenge Jallianwala Bagh)
```

#### Trigger 3: Khilafat Movement — 1919–1924
```
Background:
  → In WWI, Britain promised to protect the Ottoman Caliph
    (the spiritual head of Sunni Islam worldwide)
  → After WWI, Britain helped dismantle the Ottoman Empire
  → Indian Muslims felt betrayed — Caliph was being humiliated

Khilafat Movement:
  → Led by: Ali Brothers (Muhammad Ali and Shaukat Ali)
  → Goal: Protect the Caliph, oppose British policy
  → Gandhi saw an opportunity:
    → United Hindu-Muslim opposition against British
    → Merged Khilafat cause with Non-Cooperation

Result: Hindu-Muslim UNITY — the most powerful political
        alliance in Indian independence struggle
```

---

## 🔷 THE LAUNCH — CALCUTTA SESSION & NAGPUR SESSION

### Calcutta Special Session — September 1920:
```
Congress held a SPECIAL SESSION (not the regular annual session)
Location: Calcutta
President: Lala Lajpat Rai
Gandhi proposed: Non-Cooperation Movement
Passed: Resolution for gradual Non-Cooperation
Key decision: Start boycott of councils, titles, schools, courts
```

### Nagpur Session — December 1920:
```
Location: Nagpur (largest Congress session till that time)
Significance: FORMALLY ADOPTED Non-Cooperation programme
              Changed Congress structure significantly:
              → Provincial Congress Committees formed
              → Membership fee reduced to 4 annas (to include poor)
              → Hindi adopted as official language of Congress work
```

---

## 🔷 THE PROGRAMME — WHAT WAS NON-COOPERATION?

### Phase 1: Surrender of Titles and Honours
```
Indians were asked to:
→ Return titles given by the British (Rai Bahadur, Khan Bahadur, etc.)
→ Give up positions in nominated bodies
→ Boycott government functions

Notable: Many prominent Indians returned their titles
```

### Phase 2: Boycott of Institutions
```
Government schools and colleges boycotted
→ National institutions to be set up instead
→ Kashi Vidyapeeth, Jamia Millia Islamia, Bihar Vidyapeeth set up
   (these were alternative national educational institutions)

Law courts boycotted
→ Indian arbitration courts set up as alternative

Legislative councils boycotted
→ No participation in British-run governance
```

### Phase 3: Swadeshi (Economic Boycott)
```
→ Boycott of foreign (British) cloth — very powerful symbolism
→ Promotion of Khadi (handspun cloth)
→ Boycott of foreign goods in general
→ Gandhi and spinning wheel (charkha) became the symbol
   of economic self-reliance
```

### Phase 4: Civil Disobedience (Planned but not reached)
```
This was the FINAL planned phase
→ Mass refusal to pay taxes
→ Was NEVER REACHED because movement was
  SUSPENDED after Chauri Chaura incident
```

---

## 🔷 THE TIMELINE — NON-COOPERATION MOVEMENT

```
NON-COOPERATION MOVEMENT: KEY EVENTS
══════════════════════════════════════════════════════

April 13, 1919
   │  Jallianwala Bagh Massacre
   │
April-May 1919
   │  Rowlatt Act protests, Gandhi-led hartals
   │
September 1920
   │  Calcutta Special Congress Session
   │  Gandhi proposes Non-Cooperation
   │  Lala Lajpat Rai presides
   │
December 1920
   │  Nagpur Congress Session
   │  Non-Cooperation formally adopted
   │  Congress restructured
   │
1920–1921
   │  Boycott phase: schools, courts, titles, foreign cloth
   │  Khilafat + Non-Cooperation merged
   │  Ali Brothers campaign across India
   │  Massive hartals and demonstrations
   │  Gandhi tours India — mass mobilization
   │
December 1921
   │  Prince of Wales visits India
   │  Massive boycott of his tour
   │  Hartals all over India
   │
Early 1922
   │  Movement reaches peak intensity
   │  Government considers arresting Gandhi
   │
February 1, 1922
   │  Gandhi writes to Viceroy: "Will launch mass Civil
   │  Disobedience in Bardoli, Gujarat if demands not met"
   │
February 5, 1922 ← THE TURNING POINT
   │  CHAURI CHAURA INCIDENT — MOVEMENT SUSPENDED
   │
March 1922
   │  Gandhi arrested — tried for sedition
   │  Sentenced to 6 years (released 1924 due to illness)
```

---

## 🔷 CHAURI CHAURA — THE EVENT THAT ENDED EVERYTHING

### What Happened:
```
Date: February 5, 1922
Place: Chauri Chaura village, Gorakhpur district, Uttar Pradesh

Sequence of Events:
1. Volunteers were conducting a peaceful protest march
2. Police tried to stop the march and fired tear gas
3. Crowd retaliated — pelted stones at police
4. Police fired into the crowd — some protesters killed
5. Enraged crowd cornered the police at the police station
6. Crowd SET FIRE to the police station
7. 22 POLICEMEN were burned alive inside
```

### Gandhi's Response — Immediate and Absolute:
```
Gandhi's reaction:
→ Shocked and devastated by the violence
→ Declared 5-day fast in penance
→ IMMEDIATELY SUSPENDED the Non-Cooperation Movement

Gandhi's reasoning (very important for exam):
"A non-violent movement CANNOT continue when it turns violent.
We must first train our people for non-violence.
I would rather delay independence by years than win
it through violence."
```

### Reactions to Suspension:
```
Leaders who SUPPORTED Gandhi's suspension:
→ Motilal Nehru (reluctantly)

Leaders who were ANGRY at suspension:
→ Subhas Chandra Bose: "A great disservice to the nation"
→ C.R. Das: Strongly opposed; later founded Swaraj Party (1923)
→ Motilal Nehru: Co-founded Swaraj Party
→ Young Jawaharlal Nehru: Initially disappointed
```

---

## 🔷 OUTCOMES AND SIGNIFICANCE

### Direct Outcomes:
```
✅ Mass political awakening — millions participated for first time
✅ Established Gandhi as undisputed leader of India
✅ Hindu-Muslim unity achieved (briefly) under Khilafat merger
✅ National educational institutions established
   (Kashi Vidyapeeth, Jamia Millia Islamia, Bihar Vidyapeeth)
✅ Khadi and spinning wheel became national symbols
✅ Congress became a mass organization (not just elite)
✅ Boycott hurt British economically
```

### What Followed:
```
1923: Swaraj Party formed (C.R. Das + Motilal Nehru)
      → Entered legislatures to obstruct British from within

1924: Gandhi released from prison (illness)
      → Period of Hindu-Muslim tensions rise

1928: Simon Commission — "Simon Go Back" protests
      → Lala Lajpat Rai injured, later dies

1929: Lahore Session — Poorna Swaraj declared
      → Next big movement: Civil Disobedience (1930)
```

---

## 🔷 KEY PERSONALITIES — MASTER TABLE

| Person | Role |
|--------|------|
| **Mahatma Gandhi** | Proposed and led NCM; suspended it after Chauri Chaura |
| **Lala Lajpat Rai** | Presided over Calcutta special session (Sept 1920) |
| **Muhammad Ali** | Led Khilafat movement; merged with NCM |
| **Shaukat Ali** | Co-led Khilafat movement (Ali Brothers) |
| **C.R. Das** | Opposed suspension; founded Swaraj Party 1923 |
| **Motilal Nehru** | Co-founded Swaraj Party; authored Nehru Report 1928 |
| **Subhas Chandra Bose** | Called suspension a "great disservice" |
| **Udham Singh** | Avenged JWB — assassinated O'Dwyer in London, 1940 |
| **Rabindranath Tagore** | Returned Knighthood after Jallianwala Bagh |

---

## 🔷 BIHAR CONNECTION — NCM

```
Bihar's participation in Non-Cooperation Movement:
→ Bihar Vidyapeeth established as alternative national institution
  (Students who left government schools enrolled here)
→ Strong participation in boycott of foreign cloth
→ Champaran farmers (from 1917 movement) were already mobilized
→ Gandhi's 1917 Champaran work had created a base in Bihar
→ Rajendra Prasad organized NCM activities in Bihar
```

---

## 🔷 MEMORY TRICKS

```
"ROWLATT → JALLIANWALA → KHILAFAT → NON-COOPERATION"
(The 4 triggers/events in sequence — 1919 → 1919 → 1919 → 1920)

"3 C's of NCM Suspension"
→ CHAURI CHAURA (the incident)
→ CROWD BURNED police station
→ CONGRESS suspended the movement

"NCM = No Cooperation = No School, No Court, No Cloth, No Title"

"CALCUTTA (Sept 1920) → NAGPUR (Dec 1920)"
→ Proposed → Formally adopted

"ALI BROTHERS = Muhammad Ali + Shaukat Ali = KHILAFAT"

"SWARAJ PARTY = C.R. DAS + MOTILAL NEHRU (1923)"
→ They disagreed with NCM suspension
→ Decided to enter councils instead
```

---

## 🔷 COMPARISON TABLE — MAJOR GANDHIAN MOVEMENTS

| Feature | Non-Cooperation (1920) | Civil Disobedience (1930) | Quit India (1942) |
|---------|----------------------|--------------------------|------------------|
| Start | Sept 1920 | March 12, 1930 | August 9, 1942 |
| Slogan | — | Salt March / Dandi | "Do or Die" |
| Key method | Boycott | Break salt law | Mass rebellion |
| Ended by | Chauri Chaura violence | Gandhi-Irwin Pact | WWII end + 1947 |
| Gandhi arrested | 1922 (March) | 1930 (May) | 1942 (Aug 9) |
| Outcome | Swaraj Party formed | Pact + RTC 2 | Independence path |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Array Basics, Indexing, 2D Arrays, Strings, is_array(), rank()

---

**Q1.** What is the correct way to declare an array of 10 integers in C++?
(A) `int array(10);`
(B) `int array[10];`
(C) `array int[10];`
(D) More than one of the above
(E) None of the above

---

**Q2.** For an array declared as `int arr[7]`, what is the index of the last element?
(A) 7
(B) 8
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the output of `sizeof(arr)` where `int arr[5]` is declared?
(A) 5
(B) 10
(C) 20
(D) More than one of the above
(E) None of the above

---

**Q4.** Consider: `char s1[] = "Hello"; char s2[] = "World"; string r = s1 + s2;`
What is the result?
(A) r = "HelloWorld"
(B) r = pointer arithmetic result
(C) Compile error — cannot use + with char arrays
(D) More than one of the above
(E) None of the above

---

**Q5.** How is a 2D array stored in memory in C++?
(A) Column-major order
(B) Row-major order
(C) Diagonal order
(D) More than one of the above
(E) None of the above

---

**Q6.** What is `is_array<int[5]>::value` in C++?
(A) 0
(B) 5
(C) 1
(D) More than one of the above
(E) None of the above

---

**Q7.** What does `rank<int[3][4]>::value` return?
(A) 0
(B) 1
(C) 2
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following correctly initializes all elements of an array to zero?
(A) `int arr[5] = {0};`
(B) `int arr[5] = {};`
(C) `int arr[5];` (local array)
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the relationship between `arr[i]` and `*(arr+i)`?
(A) They are different expressions with different results
(B) They are equivalent — both access the i-th element
(C) `arr[i]` is safer; `*(arr+i)` can cause errors
(D) More than one of the above
(E) None of the above

---

**Q10.** In `int arr[5] = {10, 20, 30};`, what is the value of `arr[4]`?
(A) Garbage value
(B) 30
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q11.** What happens when an array is passed to a function in C++?
(A) A complete copy of the array is made
(B) The array decays to a pointer — base address is passed
(C) The function cannot modify the original array
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the size of char array `char str[] = "BPSC";`?
(A) 4 bytes
(B) 5 bytes
(C) 6 bytes
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following is TRUE about array names in C++?
(A) Array name can be incremented using `arr++`
(B) Array name is a constant pointer to the first element
(C) Array name can be reassigned to another array
(D) More than one of the above
(E) None of the above

---

**Q14.** For `int matrix[4][5]`, what is the total number of elements?
(A) 9
(B) 16
(C) 20
(D) More than one of the above
(E) None of the above

---

**Q15.** Which function is used to correctly concatenate two C-style char arrays?
(A) `strcat()`
(B) `strcpy()`
(C) Using `+` operator
(D) More than one of the above
(E) None of the above

---

**Q16.** What is the output of `sizeof(arr)/sizeof(int)` for `int arr[8]`?
(A) 4
(B) 8
(C) 32
(D) More than one of the above
(E) None of the above

---

**Q17.** What is `rank<int>::value` in C++?
(A) 1
(B) 0
(C) Compilation error
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following are equivalent to `arr[3]` for `int arr[]`?
(A) `*(arr + 3)`
(B) `*(3 + arr)`
(C) `3[arr]`
(D) More than one of the above
(E) None of the above

---

**Q19.** For `int arr[5]` declared globally, what is the default value of `arr[2]`?
(A) Garbage value
(B) 0
(C) -1
(D) More than one of the above
(E) None of the above

---

**Q20.** What is the address of `arr[3]` if `arr` is at address 2000 and is `int` type?
(A) 2003
(B) 2006
(C) 2012
(D) More than one of the above
(E) None of the above

---

**Q21.** What is `is_array<int*>::value`?
(A) 1 (pointer to array is still an array)
(B) 0 (pointer is not array type)
(C) 2 (pointer has one dimension)
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following is TRUE about the null terminator `'\0'` in char arrays?
(A) Its ASCII value is 0
(B) It marks the end of the C-style string
(C) It is automatically added when using string literals
(D) More than one of the above
(E) None of the above

---

**Q23.** When you declare `int arr[] = {5, 10, 15, 20}`, what is `sizeof(arr)`?
(A) 4
(B) 8
(C) 16
(D) More than one of the above
(E) None of the above

---

**Q24.** Inside a function receiving `int arr[]` as parameter, `sizeof(arr)` returns:
(A) Total size of the original array
(B) Size of pointer (4 or 8 bytes)
(C) Number of elements
(D) More than one of the above
(E) None of the above

---

**Q25.** Which header file is needed for `is_array` and `rank` in C++?
(A) `<array>`
(B) `<type_traits>`
(C) `<typeinfo>`
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Non-Cooperation Movement 1920–22

---

**Q26.** The Non-Cooperation Movement was formally adopted by the Indian National Congress at which session?
(A) Calcutta Session, September 1920
(B) Nagpur Session, December 1920
(C) Lahore Session, December 1929
(D) More than one of the above
(E) None of the above

---

**Q27.** The Non-Cooperation Movement was called off by Gandhi primarily due to:
(A) Gandhi's arrest by the British
(B) Outbreak of violence at Chauri Chaura
(C) Failure to achieve mass participation
(D) More than one of the above
(E) None of the above

---

**Q28.** The Chauri Chaura incident occurred in:
(A) Bihar
(B) Punjab
(C) Uttar Pradesh (Gorakhpur district)
(D) More than one of the above
(E) None of the above

---

**Q29.** The Khilafat Movement was primarily associated with:
(A) Demand for Hindu religious rights
(B) Protection of the Ottoman Caliph — a cause for Indian Muslims
(C) Demand for separate Muslim electorate
(D) More than one of the above
(E) None of the above

---

**Q30.** Who led the Khilafat Movement in India?
(A) Muhammad Ali Jinnah
(B) Muhammad Ali and Shaukat Ali (Ali Brothers)
(C) Aga Khan
(D) More than one of the above
(E) None of the above

---

**Q31.** Which session of Congress was presided over by Lala Lajpat Rai where Non-Cooperation was first proposed?
(A) Nagpur Session, December 1920
(B) Calcutta Special Session, September 1920
(C) Lucknow Session, 1916
(D) More than one of the above
(E) None of the above

---

**Q32.** How many policemen were killed in the Chauri Chaura incident?
(A) 12
(B) 22
(C) 35
(D) More than one of the above
(E) None of the above

---

**Q33.** The Jallianwala Bagh Massacre occurred on:
(A) April 6, 1919
(B) April 13, 1919
(C) February 5, 1919
(D) More than one of the above
(E) None of the above

---

**Q34.** Who was the British officer responsible for ordering firing at Jallianwala Bagh?
(A) Lord Curzon
(B) Michael O'Dwyer
(C) General Reginald Dyer
(D) More than one of the above
(E) None of the above

---

**Q35.** Rabindranath Tagore protested the Jallianwala Bagh massacre by:
(A) Joining the Non-Cooperation Movement
(B) Returning his Nobel Prize
(C) Returning his Knighthood
(D) More than one of the above
(E) None of the above

---

**Q36.** Which national institution was established in Bihar as an alternative to government educational institutions during the NCM?
(A) Aligarh Muslim University
(B) Bihar Vidyapeeth
(C) Jamia Millia Islamia
(D) More than one of the above
(E) None of the above

---

**Q37.** The Rowlatt Act (1919) was opposed because it:
(A) Imposed heavy taxes on farmers
(B) Allowed imprisonment without trial, no appeal, no lawyer
(C) Divided Bengal into two parts
(D) More than one of the above
(E) None of the above

---

**Q38.** Which of the following leaders founded the Swaraj Party in 1923 AFTER opposing Gandhi's suspension of NCM?
(A) Jawaharlal Nehru and Subhas Chandra Bose
(B) C.R. Das and Motilal Nehru
(C) Lala Lajpat Rai and Bipin Chandra Pal
(D) More than one of the above
(E) None of the above

---

**Q39.** What was the significance of merging the Khilafat Movement with the Non-Cooperation Movement?
(A) It added financial resources to the movement
(B) It created Hindu-Muslim unity against the British
(C) It expanded the movement to South India
(D) More than one of the above
(E) None of the above

---

**Q40.** The Rowlatt Act was also called:
(A) "White Act"
(B) "Black Act"
(C) "Salt Act"
(D) More than one of the above
(E) None of the above

---

**Q41.** Arrange in CORRECT CHRONOLOGICAL ORDER:
1. Chauri Chaura Incident
2. Nagpur Congress Session
3. Jallianwala Bagh Massacre
4. Rowlatt Act

(A) 4 → 3 → 2 → 1
(B) 3 → 4 → 2 → 1
(C) 4 → 2 → 3 → 1
(D) More than one of the above
(E) None of the above

---

**Q42.** Who assassinated Michael O'Dwyer (the Lt. Governor who supported Dyer) in 1940 to avenge Jallianwala Bagh?
(A) Bhagat Singh
(B) Chandrashekhar Azad
(C) Udham Singh
(D) More than one of the above
(E) None of the above

---

**Q43.** During the Non-Cooperation Movement, Gandhi promoted which economic symbol of self-reliance?
(A) Boycott of salt
(B) Khadi and the spinning wheel (charkha)
(C) Boycott of railway travel
(D) More than one of the above
(E) None of the above

---

**Q44.** The Chauri Chaura incident occurred on:
(A) February 5, 1921
(B) February 5, 1922
(C) March 5, 1922
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following statements about the Non-Cooperation Movement is CORRECT?
(A) It directly led to India's independence
(B) It was the first mass movement to involve ordinary Indians across the country
(C) It succeeded in all its goals before being suspended
(D) More than one of the above
(E) None of the above

---

**Q46.** Gandhi was arrested and tried for sedition after the NCM suspension in:
(A) February 1922
(B) March 1922
(C) December 1922
(D) More than one of the above
(E) None of the above

---

**Q47.** The concept of "No Daleel, No Vakeel, No Appeal" was associated with which act?
(A) Government of India Act 1919
(B) Rowlatt Act 1919
(C) Sedition Act 1870
(D) More than one of the above
(E) None of the above

---

**Q48.** MATCH THE FOLLOWING:
```
Event                          Year
1. Jallianwala Bagh            A. 1920 (December)
2. NCM formally adopted        B. 1919 (April)
3. Chauri Chaura               C. 1922 (February)
4. NCM proposed (Calcutta)     D. 1920 (September)
```
(A) 1-B, 2-A, 3-C, 4-D
(B) 1-A, 2-B, 3-D, 4-C
(C) 1-B, 2-D, 3-C, 4-A
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following was NOT a method used during the Non-Cooperation Movement?
(A) Boycott of foreign cloth
(B) Surrender of British-given titles
(C) Armed rebellion against British troops
(D) More than one of the above
(E) None of the above

---

**Q50.** Subhas Chandra Bose's reaction to Gandhi's suspension of the Non-Cooperation Movement was:
(A) Full support — he agreed non-violence must be maintained
(B) He called it a "great disservice to the cause of freedom"
(C) He immediately launched his own movement
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ Attempt all 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (B) | `int array[10];` is correct syntax |
| 2 | (C) | Last index = size - 1 = 7 - 1 = 6 |
| 3 | (C) | sizeof(int arr[5]) = 5 × 4 = 20 bytes |
| 4 | (C) | char arrays: '+' gives compile error |
| 5 | (B) | C++ uses row-major order for 2D arrays |
| 6 | (C) | is_array<int[5]>::value = 1 (true) |
| 7 | (C) | rank<int[3][4]>::value = 2 (2D array) |
| 8 | (D) | Both {0} and {} initialize all elements to 0 |
| 9 | (B) | arr[i] and *(arr+i) are exactly equivalent |
| 10 | (C) | Partial init: remaining elements = 0 (not garbage) |
| 11 | (B) | Array decays to pointer — base address passed |
| 12 | (B) | "BPSC" = 4 chars + '\0' = 5 bytes |
| 13 | (B) | Array name is a constant pointer |
| 14 | (C) | 4 × 5 = 20 elements |
| 15 | (A) | strcat() for char array concatenation |
| 16 | (B) | sizeof(int arr[8]) / sizeof(int) = 32/4 = 8 |
| 17 | (B) | rank<int>::value = 0 (not an array type) |
| 18 | (D) | All three: *(arr+3), *(3+arr), 3[arr] are equivalent |
| 19 | (B) | Global arrays auto-initialize to 0 |
| 20 | (C) | 2000 + 3×4 = 2000 + 12 = 2012 |
| 21 | (B) | Pointer is NOT an array type — returns 0 |
| 22 | (D) | All three statements about '\0' are correct |
| 23 | (C) | 4 elements × 4 bytes = 16 bytes |
| 24 | (B) | Inside function, array parameter → pointer size (4 or 8) |
| 25 | (B) | is_array and rank are in `<type_traits>` |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Nagpur Session December 1920 — formal adoption |
| 27 | (B) | Chauri Chaura violence led Gandhi to suspend |
| 28 | (C) | Chauri Chaura is in Gorakhpur, Uttar Pradesh |
| 29 | (B) | Khilafat = protecting Ottoman Caliph for Indian Muslims |
| 30 | (B) | Ali Brothers — Muhammad Ali and Shaukat Ali |
| 31 | (B) | Calcutta Special Session, September 1920 |
| 32 | (B) | 22 policemen killed at Chauri Chaura |
| 33 | (B) | April 13, 1919 (Baisakhi Day) |
| 34 | (C) | General Reginald Dyer ordered the firing |
| 35 | (C) | Tagore returned his Knighthood |
| 36 | (B) | Bihar Vidyapeeth — established in Bihar |
| 37 | (B) | No trial, no appeal, no lawyer = Black Act |
| 38 | (B) | C.R. Das and Motilal Nehru — Swaraj Party 1923 |
| 39 | (B) | Hindu-Muslim unity — most powerful outcome |
| 40 | (B) | Gandhi called Rowlatt Act the "Black Act" |
| 41 | (A) | Rowlatt(1919) → JWB(1919) → Nagpur(Dec 1920) → Chauri Chaura(1922) |
| 42 | (C) | Udham Singh avenged JWB — killed O'Dwyer in London 1940 |
| 43 | (B) | Khadi and charkha — symbols of NCM |
| 44 | (B) | February 5, 1922 |
| 45 | (B) | First mass movement involving ordinary Indians nationally |
| 46 | (B) | March 1922 — Gandhi arrested and tried |
| 47 | (B) | Rowlatt Act — "No Daleel, No Vakeel, No Appeal" |
| 48 | (A) | JWB-B(1919), Nagpur-A(Dec 1920), Chauri Chaura-C(1922), Calcutta-D(Sept 1920) |
| 49 | (C) | Armed rebellion was NEVER part of NCM — it was non-violent |
| 50 | (B) | Bose called it "great disservice to the cause of freedom" |

---
---

# 🔁 DAY 10 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — C++ Arrays

### Core Facts — One-Liners:
1. **Array** = same type, contiguous memory, 0-based indexing
2. **Correct syntax**: `int arr[10];` — NOT `int arr(10)` or `int[10] arr`
3. **Last valid index** = n-1 for array of size n (accessing n = UNDEFINED BEHAVIOR)
4. **arr[i] == *(arr+i)** — array notation and pointer arithmetic are identical
5. **Array name** = constant pointer to first element — `arr++` is INVALID
6. **sizeof(arr)** = n × sizeof(type); inside function = sizeof(pointer) ← TRAP!
7. **char s1[] + char s2[]** = COMPILE ERROR — use `strcat()` instead
8. **Partial initialization**: `int arr[5]={1,2}` → remaining elements = 0 (not garbage)
9. **Global array** = auto-initialized to 0 | **Local array** = garbage values
10. **Row-major order** = C++ stores 2D arrays row by row in memory
11. **is_array<T>::value** = 1 if T is array type, 0 otherwise (from `<type_traits>`)
12. **rank<T>::value** = number of dimensions (0 for non-array, 1 for 1D, 2 for 2D)
13. **char "BPSC"** = 5 bytes (4 chars + '\0') — always +1 for null terminator
14. **Array passed to function** = decays to pointer, modifications affect original

### Quick Formula Table:
```
Expression                     Result
────────────────────────────────────────────────────────────
sizeof(int arr[n])             n × 4 bytes
sizeof(arr)/sizeof(int)        n (number of elements)
sizeof(arr) inside function    4 or 8 (pointer size!) ← TRAP
arr[i] == *(arr+i)             ALWAYS TRUE
char "Hello" size              6 bytes (5 + '\0')
is_array<int[5]>::value        1
is_array<int*>::value          0
rank<int[3][4]>::value         2
rank<int>::value               0
Address of arr[i]              base + i × sizeof(type)
Address of mat[i][j]           base + (i×cols + j) × sizeof(type)
```

---

## ⚡ RAPID FIRE — Non-Cooperation Movement

### Critical Dates & Facts:
```
1919 (Feb)   → Rowlatt Act passed ("Black Act" — No Daleel No Vakeel No Appeal)
1919 (Apr 6) → Gandhi's hartal against Rowlatt Act
1919 (Apr 13)→ Jallianwala Bagh Massacre (Baisakhi Day, Gen. Dyer, Amritsar)
               → Tagore returned Knighthood in protest
1919–1924    → Khilafat Movement (Ali Brothers — protect Ottoman Caliph)
1920 (Sept)  → Calcutta Special Session — NCM PROPOSED (Lala Lajpat Rai presides)
1920 (Dec)   → Nagpur Session — NCM FORMALLY ADOPTED
1920–1922    → Boycott: schools, courts, foreign cloth, titles
1922 (Feb 5) → CHAURI CHAURA — 22 policemen burned alive — UP, Gorakhpur
1922 (Feb)   → Gandhi SUSPENDS NCM immediately
1922 (Mar)   → Gandhi arrested, sentenced 6 years (released 1924)
1923         → Swaraj Party: C.R. Das + Motilal Nehru (disagreed with suspension)
1940         → Udham Singh kills Michael O'Dwyer in London (avenges JWB)
```

### Bihar Connection:
```
→ Bihar Vidyapeeth established (alternative to British schools)
→ Champaran base from 1917 helped NCM mobilization in Bihar
→ Rajendra Prasad organized NCM activities in Bihar
```

### Common Exam Traps:
1. NCM PROPOSED at Calcutta (Sept 1920); FORMALLY ADOPTED at Nagpur (Dec 1920)
2. General Dyer ORDERED firing; Michael O'Dwyer SUPPORTED Dyer (different people!)
3. Tagore returned KNIGHTHOOD (not Nobel Prize) after JWB
4. Chauri Chaura = UP (Gorakhpur), NOT Bihar, Punjab, or Bengal
5. 22 policemen killed at Chauri Chaura (exact number often tested)
6. Swaraj Party formed AGAINST Gandhi's decision — by C.R. Das + Motilal Nehru

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. `char s1[] + char s2[]` = COMPILE ERROR; use `strcat()` for char array concatenation
2. `sizeof(arr)` inside a function = pointer size (4/8), NOT array size — array decays to pointer
3. `is_array<T>::value` checks array type; `rank<T>::value` gives dimensions — both from `<type_traits>`
4. Chauri Chaura (Feb 5, 1922) = UP, 22 policemen burned → Gandhi suspended NCM
5. NCM proposed at Calcutta (Sept 1920); formally adopted at Nagpur (Dec 1920)

---

*Next: Day 11 — File Handling in C++ + Civil Disobedience Movement & Salt March 1930*
