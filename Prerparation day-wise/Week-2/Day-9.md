# 📅 DAY-9 — BPSC TRE 4.0 TOPPER GUIDE
## CS: Pointers in C++ — &, *, NULL, delete/delete[], Dangling, new vs malloc
## GS: Champaran Satyagraha 1917 (Deep Dive) + Non-Cooperation Movement + Civil Disobedience

> **Topper Target:** Score 23+/25 in CS and 23+/25 in GS practice sets today.
> **⚠️ Option (D) Alert:** ~20–25% answers in BPSC TRE are "More than one of the above" — NEVER skip it!
> **⚠️ Bihar Focus:** Champaran is a BPSC-favourite topic — expect 1–2 direct questions every paper!

---

# ═══════════════════════════════════════════════════════
# 🖥️ PART 1: COMPUTER SCIENCE
## POINTERS IN C++ — Complete Topper Guide
# ═══════════════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A POINTER? — The Foundation

### Real-World Analogy:
> Think of **RAM memory** as a row of post-office boxes, each with an **address** (like 1001, 1002, 1003...).
> A **normal variable** stores a VALUE in a box.
> A **pointer variable** stores the **ADDRESS (number)** of another box.

```
MEMORY LAYOUT DIAGRAM
═══════════════════════════════════════════════════════════════
Address:   1000     1001     1002     1003     1004
           ┌────┐   ┌────┐   ┌────┐   ┌────┐   ┌────┐
Value:     │ 25 │   │1000│   │    │   │    │   │    │
           └────┘   └────┘   └────┘   └────┘   └────┘
            ↑          ↑
           int x=25   int* ptr = &x
           (stores 25) (stores ADDRESS of x = 1000)
═══════════════════════════════════════════════════════════════

int x = 25;       → variable x, value = 25, address = 1000
int* ptr = &x;    → pointer ptr, value = 1000 (address of x)
*ptr = 25         → dereference: get value AT address 1000
```

---

## 📌 SECTION 2: POINTER OPERATORS — The Two Key Operators

### Operator 1: `&` — Address-of Operator

```cpp
int x = 25;
cout << x;    // Output: 25         (value stored in x)
cout << &x;   // Output: 0x61ff08   (memory address of x — hex format)
```

- `&` placed BEFORE a variable → gives its **memory address**
- Also used in references: `int& ref = x;` (different use!)

### Operator 2: `*` — Dereference Operator (also Declaration Operator)

```cpp
int x = 25;
int* ptr = &x;    // * in DECLARATION: means "ptr is a pointer to int"

cout << ptr;      // Output: 0x61ff08 (address stored in ptr)
cout << *ptr;     // Output: 25       (* in EXPRESSION: go to that address, get value)

*ptr = 100;       // Change value AT that address → x is now 100!
cout << x;        // Output: 100
```

### Visual Diagram:
```
int x = 25;
int* ptr = &x;

ptr  ──────────────────→  x
[stores address of x]     [value: 25]

*ptr means: "follow the arrow and get the value" = 25
*ptr = 100 means: "follow the arrow and SET the value to 100"
```

---

## 📌 SECTION 3: DECLARATION SYNTAX — Common Mistakes

```cpp
// CORRECT ways to declare pointer:
int* ptr;       // * attached to type (recommended style)
int *ptr;       // * attached to variable name (both mean same)
int * ptr;      // space on both sides (also valid)

// IMPORTANT: Multiple declarations on ONE line
int* p, q;      // p is pointer to int; q is just int (NOT a pointer!)
int *p, *q;     // BOTH p and q are pointers to int ✅

// POINTER TO DIFFERENT TYPES:
char* cptr;     // pointer to char
float* fptr;    // pointer to float
double* dptr;   // pointer to double
void* vptr;     // void pointer (can point to any type)
```

### 🎯 PYQ TRAP:
```
Q: In declaration "int* p, q;", which variables are pointers?
Answer: Only p is a pointer. q is a plain int.
The * belongs to p, not to the type int.
```

---

## 📌 SECTION 4: NULL POINTER — PYQ Critical

### What is a NULL Pointer?
A pointer that does **not point to any valid memory location**.

```cpp
// In C (old style):
int* ptr = NULL;      // NULL is macro defined as 0

// In C++11 and later (PREFERRED):
int* ptr = nullptr;   // nullptr is a keyword (type-safe)

// Check if pointer is null:
if (ptr == NULL) { ... }     // C style
if (ptr == nullptr) { ... }  // C++11 style
if (!ptr) { ... }            // Also works
```

### 🔴 SUPER CRITICAL PYQ FACT:

```
╔══════════════════════════════════════════════════════════════╗
║  delete ptr;   where ptr = NULL                              ║
║                                                              ║
║  RESULT: Compiles and executes SUCCESSFULLY — NO CRASH!      ║
║                                                              ║
║  Deleting a NULL pointer is a safe no-operation (no-op).    ║
║  It is guaranteed by the C++ standard.                       ║
╚══════════════════════════════════════════════════════════════╝

This is directly from BPSC TRE PYQ — asked multiple times!
```

### Why is this safe?
The C++ standard guarantees: "The expression `delete (void*)0` has no effect."

```cpp
int* ptr = NULL;
delete ptr;       // ✅ SAFE! No crash. Does nothing.
delete ptr;       // ✅ Still safe! Deleting NULL again = fine.

int* ptr2 = new int(5);
delete ptr2;      // ✅ Frees memory
delete ptr2;      // ❌ DANGER! Double delete = undefined behavior (ptr2 now dangling)
```

---

## 📌 SECTION 5: `new` and `delete` — Dynamic Memory Allocation

### Allocating Memory with `new`:

```
STACK vs HEAP DIAGRAM
══════════════════════════════════════════════════════════════
  STACK (automatic memory)      HEAP (dynamic memory)
  ──────────────────────        ──────────────────────
  int x = 5;                    int* p = new int(5);
  Created automatically         Created with new
  Destroyed automatically       Must be freed with delete
  when scope ends               else → MEMORY LEAK!
  
  Fast access                   Slightly slower
  Limited size (~1-8 MB)        Much larger (GBs)
══════════════════════════════════════════════════════════════
```

### `new` for Single Object:

```cpp
int* ptr = new int;          // Allocates int on heap (garbage value)
int* ptr = new int(42);      // Allocates int on heap, initializes to 42
int* ptr = new int();        // Allocates int on heap, initializes to 0

// Use it:
*ptr = 100;
cout << *ptr;   // 100

// Free it:
delete ptr;     // Frees single object
ptr = nullptr;  // Good practice: set to null after delete
```

### `new[]` for Arrays:

```cpp
int* arr = new int[10];      // Allocates array of 10 ints on heap
int* arr = new int[10]();    // Allocates AND initializes all to 0

// Use it:
arr[0] = 5;
arr[9] = 99;

// Free it:
delete[] arr;    // ⚠️ MUST use delete[] for arrays, NOT delete!
arr = nullptr;   // Good practice
```

---

## 📌 SECTION 6: `delete` vs `delete[]` — PYQ CRITICAL DISTINCTION

```
╔══════════════════════════════════════════════════════════════╗
║              delete  vs  delete[]                            ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  delete ptr;                                                 ║
║  • Used for SINGLE object allocated with new                 ║
║  • Calls destructor ONCE for that object                     ║
║  • Example: int* p = new int(5);  →  delete p;              ║
║                                                              ║
║  delete[] arr;                                               ║
║  • Used for ARRAY allocated with new[]                       ║
║  • Calls destructor for EACH element                         ║
║  • Example: int* a = new int[10];  →  delete[] a;           ║
║                                                              ║
║  MISMATCH = UNDEFINED BEHAVIOR:                              ║
║  new     → delete[]   ❌  undefined behavior                 ║
║  new[]   → delete     ❌  undefined behavior (memory leak)   ║
╚══════════════════════════════════════════════════════════════╝
```

### Common Exam Question:

```cpp
int* arr = new int[5];
// ... use arr ...

// Which is correct to free this?
(A) delete arr;      // ❌ Wrong! Memory leak / undefined behavior
(B) delete[] arr;    // ✅ Correct!
(C) free(arr);       // ❌ Wrong! free() is for malloc, not new
```

---

## 📌 SECTION 7: `new` vs `malloc()` — KEY DIFFERENCES (PYQ Tested)

```
╔═══════════════════════════════════════════════════════════════════╗
║              new  vs  malloc                                       ║
╠═══════════╦═══════════════════════════╦══════════════════════════╣
║  Feature  ║         new               ║        malloc            ║
╠═══════════╬═══════════════════════════╬══════════════════════════╣
║ Language  ║ C++ operator              ║ C function               ║
║ Header    ║ None needed               ║ <cstdlib> / <stdlib.h>   ║
║ Syntax    ║ int* p = new int(5);      ║ int* p=(int*)malloc(4);  ║
║Constructor║ ✅ CALLS constructor      ║ ❌ Does NOT call         ║
║Destructor ║ delete calls destructor   ║ free() doesn't call      ║
║Return Type║ Exact type (int*)         ║ void* (needs casting)    ║
║On Failure ║ throws bad_alloc exception║ returns NULL             ║
║Dealloc    ║ delete / delete[]         ║ free()                   ║
║Resize     ║ ❌ Not directly           ║ ✅ realloc() available   ║
╚═══════════╩═══════════════════════════╩══════════════════════════╝

🎯 KEY PYQ FACT:
"new" INVOKES the CONSTRUCTOR → used in OOP with classes
"malloc" does NOT invoke constructor → just allocates raw memory
```

### Code Comparison:

```cpp
// Using new (C++ way):
MyClass* obj = new MyClass();   // constructor IS called ✅
delete obj;                      // destructor IS called ✅

// Using malloc (C way):
MyClass* obj = (MyClass*)malloc(sizeof(MyClass));  // constructor NOT called ❌
free(obj);                                          // destructor NOT called ❌
```

---

## 📌 SECTION 8: POINTER ARITHMETIC

### Rules of Pointer Arithmetic:

```cpp
int arr[] = {10, 20, 30, 40, 50};
int* ptr = arr;     // ptr points to arr[0] (address = 1000, say)

cout << *ptr;       // Output: 10  (value at arr[0])

ptr++;              // ptr now points to arr[1] (address = 1004)
                    // Because int = 4 bytes, ptr moves by 4 bytes!
cout << *ptr;       // Output: 20

ptr += 2;           // ptr moves 2 × 4 = 8 bytes forward → arr[3]
cout << *ptr;       // Output: 40
```

### Diagram:

```
arr:  [10] [20] [30] [40] [50]
addr: 1000  1004  1008  1012  1016
       ↑
      ptr (initially)
       
After ptr++:
arr:  [10] [20] [30] [40] [50]
addr: 1000  1004  1008  1012  1016
             ↑
            ptr (now at 1004)

ptr++ does NOT mean address+1, it means address + sizeof(type)
For int: address + 4
For char: address + 1
For double: address + 8
```

### Valid Pointer Arithmetic Operations:

| Operation | Valid? | Meaning |
|-----------|--------|---------|
| `ptr + n` | ✅ | Move n elements forward |
| `ptr - n` | ✅ | Move n elements backward |
| `ptr++` | ✅ | Move to next element |
| `ptr--` | ✅ | Move to previous element |
| `ptr1 - ptr2` | ✅ | Number of elements between |
| `ptr1 + ptr2` | ❌ | INVALID — adding two pointers |
| `ptr * 2` | ❌ | INVALID — multiplication |

---

## 📌 SECTION 9: DANGLING POINTER — PYQ Important

### What is a Dangling Pointer?
A pointer that **points to memory that has been freed/deleted** or **gone out of scope**.

```
DANGLING POINTER — 3 SCENARIOS:

Scenario 1: Using after delete
─────────────────────────────
int* ptr = new int(5);
delete ptr;           // memory freed
*ptr = 10;            // ❌ DANGLING! ptr points to freed memory
                      // Undefined behavior — may crash or corrupt data

Scenario 2: Returning local variable address
───────────────────────────────────────────
int* getPointer() {
    int x = 10;       // local variable
    return &x;        // ❌ x destroyed when function returns!
}                     // Pointer now dangles!

Scenario 3: Variable goes out of scope
──────────────────────────────────────
int* ptr;
{
    int x = 5;
    ptr = &x;         // ptr points to x
}                     // x is destroyed here (out of scope)
*ptr = 10;            // ❌ DANGLING! x no longer exists
```

### Prevention — Best Practice:

```cpp
int* ptr = new int(5);
delete ptr;
ptr = nullptr;        // ✅ Set to null after delete!
                      // Now if you accidentally use ptr:
if (ptr != nullptr) { // This check will catch it
    *ptr = 10;
}
```

---

## 📌 SECTION 10: VOID POINTER — Special Type

```cpp
void* vptr;     // Can point to ANY data type — no type information

int x = 5;
float f = 3.14;

vptr = &x;      // ✅ void pointer can hold address of int
vptr = &f;      // ✅ void pointer can hold address of float

// BUT: Cannot dereference directly!
// *vptr = 10;  ❌ ERROR! Type unknown

// Must cast first:
int* iptr = (int*)vptr;
cout << *iptr;  // ✅ Now works
```

### Uses of void pointer:
- Generic functions (like `memcpy`, `malloc` return `void*`)
- Generic data structures

---

## 📌 SECTION 11: POINTER TO POINTER (Double Pointer)

```cpp
int x = 5;
int* ptr = &x;      // ptr stores address of x
int** pptr = &ptr;  // pptr stores address of ptr

cout << x;          // 5
cout << *ptr;       // 5    (go to address in ptr)
cout << **pptr;     // 5    (go to address in pptr, then again dereference)
cout << *pptr;      // address of x (= ptr's value)

// DIAGRAM:
// pptr → ptr → x
// **pptr = *ptr = x = 5
```

---

## 📌 SECTION 12: REFERENCE vs POINTER — PYQ Distinction

```
╔═══════════════════════════════════════════════════════════════════╗
║           POINTER  vs  REFERENCE                                   ║
╠════════════════════════╦══════════════════════════════════════════╣
║       POINTER          ║         REFERENCE                        ║
╠════════════════════════╬══════════════════════════════════════════╣
║ int* ptr = &x;         ║ int& ref = x;                            ║
║ Can be NULL            ║ Cannot be NULL (must bind to variable)   ║
║ Can be reassigned      ║ Cannot be reassigned after binding       ║
║ Has its own address    ║ Shares address with original variable    ║
║ Needs * to dereference ║ Used like normal variable                ║
║ Can point to array     ║ Cannot "point to" arrays                 ║
╚════════════════════════╩══════════════════════════════════════════╝
```

---

## 📌 COMPLETE POINTER DIAGRAM — Day 9 Master Summary

```
C++ POINTERS — COMPLETE TOPPER MIND MAP
══════════════════════════════════════════════════════════════════

                         POINTER
                            │
        ┌───────────────────┼───────────────────┐
        ↓                   ↓                   ↓
   DECLARATION          OPERATORS           TYPES
   ──────────           ─────────           ─────
   int* ptr;            & → address of      NULL ptr
   int *ptr;            * → dereference     Void ptr
   int * ptr;           :: → scope          Dangling ptr
   (all same!)          resolution          Wild ptr
                                            Double ptr **

        ↓                   ↓                   ↓
   new/malloc           delete/free         ARITHMETIC
   ──────────           ──────────          ──────────
   new → calls ctor     delete → 1 obj      ptr++ → +sizeof(T)
   malloc → no ctor     delete[] → array    ptr+n → n×sizeof(T)
   returns typed ptr    free → for malloc   ptr1-ptr2 → count
   throws on fail       NULL delete = safe  ptr1+ptr2 = INVALID

═══════════════════════════════════════════════════════════════════

🔴 TOP 5 PYQ FACTS:
1. delete NULL_ptr → SAFE (no crash, no-op)
2. new calls constructor; malloc does NOT
3. new[] → must use delete[] (mismatch = undefined behavior)
4. sizeof(int*) = 4 bytes (32-bit) or 8 bytes (64-bit) — NOT sizeof(int)
5. Dangling pointer = points to freed/out-of-scope memory
```

---
---
---

# ═══════════════════════════════════════════════════════
# 🇮🇳 PART 2: GENERAL STUDIES
## Champaran Satyagraha 1917 (Deep Dive) + Non-Cooperation Movement + Civil Disobedience
## (Bihar-Focus — BPSC High Priority!)
# ═══════════════════════════════════════════════════════

---

## 📌 SECTION 1: CHAMPARAN SATYAGRAHA 1917 — COMPLETE DEEP DIVE

### Background — Why Champaran?

```
CHAMPARAN CONTEXT DIAGRAM
══════════════════════════════════════════════════════════════════
LOCATION: Champaran district, Bihar (now split into East & West)

COLONIAL SYSTEM: TINKATHIA SYSTEM
  ┌────────────────────────────────────────────────────────┐
  │  Total land = 20 kathas                                │
  │  3 kathas (3/20th) MUST be used for indigo             │
  │  by every farmer — FORCED by British planters          │
  │  Farmers got very LOW prices for indigo                │
  │  Could NOT refuse — had no legal protection            │
  └────────────────────────────────────────────────────────┘

Why "Tinkathia"?
  "Teen" = 3 in Hindi
  "Katha" = unit of land measurement
  So "Tinkathia" = 3 kathas compulsory indigo on 20 katha land
══════════════════════════════════════════════════════════════════
```

### Gandhi Comes to Champaran — The Story:

| Step | Event |
|------|-------|
| 1916 | Rajkumar Shukla (indigo farmer) meets Gandhi at Lucknow INC session |
| Jan 1917 | Shukla persuades Gandhi to visit Champaran |
| April 1917 | Gandhi arrives at Champaran |
| British order | Gandhi ordered to leave by District Collector |
| Gandhi's response | REFUSED to leave → announced trial willingly |
| Public response | Massive crowds gathered in Gandhi's support |
| Government backed down | Cancelled the order against Gandhi |
| Investigation | Gandhi conducted his own fact-finding survey |
| Key associates | **Rajendra Prasad**, Brij Kishore, Mazharul Haque |
| Result | **Champaran Agrarian Act 1918** passed |
| Outcome | Tinkathia system ABOLISHED |

### 🎯 BPSC HIGH-PRIORITY FACTS:

```
╔══════════════════════════════════════════════════════════════╗
║            CHAMPARAN SATYAGRAHA — MUST REMEMBER             ║
╠══════════════════════════════════════════════════════════════╣
║  Year: 1917                                                  ║
║  Location: Champaran, Bihar                                  ║
║  Issue: Tinkathia system (forced indigo cultivation)         ║
║  Who invited Gandhi: RAJKUMAR SHUKLA                         ║
║  Gandhi's associate: RAJENDRA PRASAD (later India's          ║
║                       first President!)                      ║
║  Significance: Gandhi's FIRST Civil Disobedience in India    ║
║               Gandhi's FIRST visit to Bihar                  ║
║               First use of Satyagraha technique in India     ║
║  Result: Champaran Agrarian Act 1918                         ║
║         Tinkathia system abolished                           ║
╚══════════════════════════════════════════════════════════════╝
```

### What is Satyagraha?

```
SATYAGRAHA = Satya (Truth) + Agraha (Insistence)
           = "Truth-Force" or "Soul-Force"

Principles:
├── Non-violence (Ahimsa)
├── Civil disobedience — break unjust laws willingly
├── Accept punishment without complaint
├── No hatred toward opponent
└── Win by moral force, not physical force

Gandhi first used Satyagraha in SOUTH AFRICA (Natal, 1893)
Gandhi's FIRST Satyagraha IN INDIA = Champaran (1917)
```

---

## 📌 SECTION 2: KHEDA AND AHMEDABAD SATYAGRAHAS (1918)

### Kheda Satyagraha (1918):

| Aspect | Detail |
|--------|--------|
| Location | Kheda district, Gujarat |
| Issue | Crop failure → farmers demanded revenue waiver |
| British rule | If crop < 1/4 of normal, revenue could be waived |
| British stance | Refused waiver despite poor harvest |
| Gandhi's method | Revenue non-payment campaign |
| Key associate | **Sardar Vallabhbhai Patel** (in his first major movement!) |
| Result | Government suspended revenue collection |

### Ahmedabad Mill Strike (1918):

| Aspect | Detail |
|--------|--------|
| Issue | Mill workers' wage dispute (demanded 35% hike) |
| Gandhi's method | FIRST HUNGER STRIKE by Gandhi in India |
| Result | Mill owners agreed to 35% wage hike |
| Significance | Gandhi's first use of hunger strike (fast) as weapon |

---

## 📌 SECTION 3: ROWLATT ACT (1919) — Trigger for Mass Movement

```
ROWLATT ACT — BLACK LAW (as Gandhi called it)
══════════════════════════════════════════════════════════════

Official Name: Anarchical and Revolutionary Crimes Act, 1919
Based on: Rowlatt Committee report (chaired by Justice Rowlatt)

Provisions:
┌──────────────────────────────────────────────────────────┐
│ • Political suspects could be arrested WITHOUT warrant   │
│ • Could be tried WITHOUT jury                            │
│ • Could be imprisoned WITHOUT trial                      │
│ Nickname: "No appeal, no Vakil, no Dalil" (No lawyer,   │
│           no appeal, no argument)                        │
└──────────────────────────────────────────────────────────┘

Gandhi's Response:
├── Called it a "Black Law"
├── Called for hartal (general strike) on April 6, 1919
├── Nationwide protests
└── This set the stage for Jallianwala Bagh massacre
```

---

## 📌 SECTION 4: JALLIANWALA BAGH MASSACRE — 1919

### Complete Facts:

```
JALLIANWALA BAGH — APRIL 13, 1919
══════════════════════════════════════════════════════════════════

Date: April 13, 1919 (Baisakhi festival day)
Place: Jallianwala Bagh, Amritsar, Punjab

Context: Dr. Satya Pal and Saifuddin Kitchlew (local leaders)
         were arrested → people gathered to protest peacefully

The Massacre:
┌──────────────────────────────────────────────────────────────┐
│ General Reginald Dyer ordered troops to fire on crowd        │
│ WITHOUT warning, WITHOUT asking to disperse                   │
│ Exits were blocked — people couldn't escape                  │
│ ~1,650 rounds fired                                          │
│ Official death count: 379 (Hunter Commission)               │
│ Actual estimates: 1,000+                                     │
│ Hundreds jumped into well inside garden to escape           │
└──────────────────────────────────────────────────────────────┘

Key People:
├── Governor: Michael O'Dwyer (who approved Dyer's actions)
├── General: Reginald Dyer (gave firing orders)
├── Viceroy: LORD CHELMSFORD ← (BPSC PYQ Answer!)
├── Secretary of State: Edwin Montagu

Reactions:
├── Rabindranath Tagore: Returned knighthood in protest
├── Gandhi: Returned Kaiser-i-Hind gold medal
├── Udham Singh: Later assassinated Michael O'Dwyer in London (1940)
══════════════════════════════════════════════════════════════════
```

### Hunter Commission:
- Formed to investigate the massacre
- Found General Dyer guilty but he was NOT tried in court
- British gave him a sword of honour and collected money for him → outrage in India

---

## 📌 SECTION 5: NON-COOPERATION MOVEMENT (1920–22)

### Why was NCM launched?

```
TRIGGERS FOR NON-COOPERATION MOVEMENT:
                    │
      ┌─────────────┼───────────────┐
      ↓             ↓               ↓
  Jallianwala   Khilafat Issue   Congress
  Bagh 1919     (1919-20)        Discontent
  
  What is Khilafat Issue?
  ┌──────────────────────────────────────────────┐
  │ Ottoman Caliph = religious head of Muslims   │
  │ After WWI, Ottoman Empire was dismembered    │
  │ Indian Muslims wanted to protect the Caliph  │
  │ Gandhi supported Khilafat → Hindu-Muslim     │
  │ unity strategy                               │
  │ Leaders: Ali Brothers (Shaukat Ali +         │
  │          Mohammad Ali)                       │
  └──────────────────────────────────────────────┘
```

### NCM — Full Detail:

| Aspect | Detail |
|--------|--------|
| Launched | September 1920 (Calcutta special session) |
| Formally adopted | December 1920 (Nagpur session) |
| Slogan | **"Swaraj within one year"** |
| Combined with | **Khilafat Movement** (Hindu-Muslim unity) |

### Methods of NCM:

```
NON-COOPERATION METHODS — 4 LEVELS:
══════════════════════════════════════════════════════

Level 1: Surrendering titles and honours
└── Hundreds returned British titles and medals

Level 2: Boycott of civil institutions
└── Government schools, colleges, courts, elections

Level 3: Boycott of foreign goods
└── Burn foreign cloth; use Swadeshi (Indian) products
└── Charkha (spinning wheel) promoted by Gandhi

Level 4: Resignation from government services
└── Government employees asked to resign

Constructive Programme:
└── Set up national schools (like Jamia Millia Islamia)
└── Promotion of khadi (handspun cloth)
└── Panchayat courts
══════════════════════════════════════════════════════
```

### Chauri Chaura Incident — Why Movement Was Withdrawn:

```
CHAURI CHAURA — FEBRUARY 5, 1922
══════════════════════════════════════════════════════════

Location: Chauri Chaura, Gorakhpur, Uttar Pradesh

What happened:
├── Protesters marching peacefully
├── Police opened fire on protesters
├── Angry mob ATTACKED and SET FIRE to police station
└── 22 policemen BURNED TO DEATH inside

Gandhi's reaction:
├── Was deeply shocked and grieved
├── Said: "God has warned us. Movement must stop."
├── Unilaterally SUSPENDED the Non-Cooperation Movement
└── February 12, 1922: Movement officially called off

Reaction of other leaders:
├── Jawaharlal Nehru (in prison): "Were we to stop every time 
│   some people do something violent?"
├── Subhas Chandra Bose: Strongly disagreed with suspension
└── Most leaders felt withdrawal was premature

Gandhi's reasoning:
└── Movement must be NON-VIOLENT — violence anywhere = 
    movement morally invalid; must restart with pure spirit
══════════════════════════════════════════════════════════
```

### After NCM — Swaraj Party:

| Aspect | Detail |
|--------|--------|
| Formed by | C.R. Das + Motilal Nehru (1923) |
| Strategy | Council entry — enter legislatures to obstruct British |
| Conflict | With Gandhi's "no-changers" who wanted to stay out |
| Result | Some success in obstruction; dissolved by 1926 |

---

## 📌 SECTION 6: CIVIL DISOBEDIENCE MOVEMENT (1930) — Deep Dive

### Why 1930?

```
CONTEXT FOR CDM:
├── Simon Commission (1927): No Indian member → boycotted
├── Nehru Report (1928): Draft constitution by Indians
├── Lahore Session (Dec 1929): Purna Swaraj (Complete Independence)
│   President: Jawaharlal Nehru
│   Resolution: January 26, 1930 = Independence Day (celebrated)
└── Gandhi sent 11 demands to Viceroy Irwin → ignored
```

### Dandi March — The Salt Satyagraha:

```
DANDI MARCH — MARCH 12 TO APRIL 6, 1930
══════════════════════════════════════════════════════════════════

Start: Sabarmati Ashram, Ahmedabad
End:   Dandi (coastal village), Gujarat
Distance: ~240 miles (388 km)
Duration: 24 days
Marchers: Gandhi + 78 selected volunteers

Why SALT?
┌──────────────────────────────────────────────────────────────┐
│ British Salt Laws = government monopoly on salt              │
│ Indians couldn't make/sell salt without license and tax      │
│ Salt = every Indian needs it (rich/poor/Hindu/Muslim)       │
│ Salt = perfect symbol: simple, universal, unjust tax         │
└──────────────────────────────────────────────────────────────┘

April 6, 1930:
└── Gandhi reached Dandi, picked up salt from seashore
└── Broke the Salt Law deliberately
└── "With this, I am shaking the foundations of the British Empire"

Impact:
├── Spread everywhere — salt made across coastal India
├── Dharasana Salt Works raid: C. Rajagopalachari
├── Northwest Frontier: Khan Abdul Ghaffar Khan
│   ("Frontier Gandhi" — Khudai Khidmatgar/Red Shirts)
├── Women's mass participation (Sarojini Naidu was key)
└── International attention — reported by foreign press
══════════════════════════════════════════════════════════════════
```

### Gandhi-Irwin Pact (March 1931):

| Provision | Detail |
|-----------|--------|
| Signed | March 5, 1931 |
| Between | Gandhi (INC) + Lord Irwin (Viceroy) |
| INC agreed | Suspend Civil Disobedience |
| British agreed | Release political prisoners, allow salt making near coast |
| CDM resumed | 1932 (after Ramsay MacDonald's Communal Award) |
| Significance | First time British negotiated with INC as equals |

### Round Table Conferences:

| Conference | Year | Gandhi attended? | Key Event |
|-----------|------|-----------------|-----------|
| 1st RTC | 1930 | ❌ No (in jail) | INC boycotted |
| 2nd RTC | 1931 | ✅ Yes | Gandhi as sole INC rep; ended without agreement |
| 3rd RTC | 1932 | ❌ No (in jail) | INC absent; Poona Pact (Ambedkar-Gandhi) |

---

## 📌 SECTION 7: QUIT INDIA MOVEMENT (1942) — Bihar Focus

```
QUIT INDIA MOVEMENT — AUGUST 1942
══════════════════════════════════════════════════════════════════

Context: WWII; Cripps Mission (1942) failed
Date: August 8, 1942 (Resolution passed)
      August 9, 1942 (Movement begins; leaders arrested)
Place: All India Congress Committee, Bombay (Gowalia Tank Maidan)
Slogan: "Do or Die" / "Karo ya Maro"
       (Gandhi's call — fight for freedom or die trying)

What happened after leaders were arrested?
├── Underground network took over
├── Railway lines, telegraph wires cut
├── Government buildings attacked
└── Bihar and UP were epicenters of activity

BIHAR IN QUIT INDIA:
╔══════════════════════════════════════════════════════════════╗
║  Jayaprakash Narayan (JP) escaped from Hazaribagh prison    ║
║  Led underground movement from Nepal border areas           ║
║  Set up underground radio "Congress Radio"                  ║
║  Aruna Asaf Ali: Hoisted flag at Gowalia Tank, Bombay      ║
╚══════════════════════════════════════════════════════════════╝

British response:
├── 100,000+ arrested in weeks
├── Press censored
├── Harsh suppression
└── Called it "most serious rebellion since 1857"

Result: Movement suppressed but sowed seeds of final push
══════════════════════════════════════════════════════════════════
```

---

## 📌 SECTION 8: INDIA'S FREEDOM — FINAL STEPS

| Event | Year | Key Detail |
|-------|------|-----------|
| Simla Conference | 1945 | Failed; Muslim League demanded separate electorate |
| Cabinet Mission | 1946 | 3 ministers (Pethick-Lawrence, Stafford Cripps, A.V. Alexander) |
| Direct Action Day | Aug 16, 1946 | Muslim League; Great Calcutta Killings |
| Mountbatten Plan | June 3, 1947 | Partition announced; India + Pakistan |
| Independence | **August 15, 1947** | India independent |
| Partition | August 14–15, 1947 | Pakistan (Aug 14), India (Aug 15) |
| Integration of States | 1947–49 | Sardar Patel's role — "Iron Man of India" |
| Constitution | **January 26, 1950** | India becomes Republic (Republic Day) |

---

## 📌 SECTION 9: SIMON COMMISSION — PYQ Important

```
SIMON COMMISSION (1927)
──────────────────────────────────────────────────────
Appointed by: British Parliament (Lord Birkenhead)
Year appointed: 1927; Arrived in India: 1928
Chair: Sir John Simon
Members: ALL BRITISH — NO INDIAN MEMBER!

Indian reaction:
├── ALL parties boycotted (INC + Muslim League + others)
├── Welcomed with BLACK FLAGS and "Simon Go Back!" slogans
├── Lala Lajpat Rai led protest in Lahore
│   → Police lathi charge on protesters
│   → Lala Lajpat Rai severely beaten
│   → Died weeks later (October 1928)
│   → His death caused massive outrage
│   → Bhagat Singh avenged by killing British officer J.P. Saunders
└── Report submitted 1930 → led to Government of India Act 1935
```

---

## 📌 SECTION 10: KEY VICEROYS AND THEIR EVENTS — PYQ Table

| Viceroy | Period | Key Event Under Them |
|---------|--------|---------------------|
| Lord Dalhousie | 1848–56 | Doctrine of Lapse; Railways; Telegraph |
| Lord Canning | 1856–62 | **Revolt of 1857**; Queen's Proclamation 1858 |
| Lord Lytton | 1876–80 | Vernacular Press Act; Arms Act |
| Lord Rippon | 1880–84 | Ilbert Bill; Local Self Government |
| Lord Curzon | 1899–1905 | **Partition of Bengal 1905** |
| Lord Minto | 1905–10 | Morley-Minto Reforms 1909 |
| Lord Hardinge | 1910–16 | Capital shifted Delhi (1911); **Partition of Bengal annulled** |
| Lord Chelmsford | 1916–21 | **Jallianwala Bagh 1919**; Montagu-Chelmsford Reforms |
| Lord Reading | 1921–26 | Non-Cooperation withdrawn; Chauri Chaura |
| Lord Irwin | 1926–31 | **Dandi March 1930**; Gandhi-Irwin Pact |
| Lord Willingdon | 1931–36 | CDM resumed; Poona Pact |
| Lord Linlithgow | 1936–43 | **Quit India Movement 1942** |
| Lord Mountbatten | 1947 | **Independence + Partition** |

---

## 📌 SECTION 11: IMPORTANT BOOKS AND AUTHORS — GS PYQ

| Book | Author | Significance |
|------|--------|-------------|
| Anandamath | Bankim Chandra Chattopadhyay | Contains "Vande Mataram"; mentions Sannyasi Revolt |
| Discovery of India | Jawaharlal Nehru | Written in Ahmednagar Fort prison (1944) |
| Hind Swaraj | Mahatma Gandhi | Gandhi's vision of Indian civilization (1909) |
| The Indian War of Independence 1857 | V.D. Savarkar | First called 1857 as "War of Independence" |
| Poverty and Un-British Rule in India | Dadabhai Naoroji | "Drain Theory" — wealth drained from India |
| India Wins Freedom | Abul Kalam Azad | Partition memoir (some parts sealed 30 years) |
| Gita Rahasya | Bal Gangadhar Tilak | Written in Mandalay prison |
| Why I am an Atheist | Bhagat Singh | Prison writing |

---

## 📌 SECTION 12: TRICKY PYQ FACTS — MISTAKES TO AVOID

| Wrong Belief | Correct Fact |
|--------------|-------------|
| Rajendra Prasad invited Gandhi to Champaran | **Rajkumar Shukla** invited Gandhi |
| Champaran was about salt | Champaran was about **indigo (Tinkathia system)** |
| CDM = same as NCM | CDM (1930) ≠ NCM (1920) — different movements |
| Sarojini Naidu led Home Rule League | Home Rule League was Tilak + Annie Besant; NOT Sarojini Naidu |
| Viceroy during Jallianwala = Curzon | Correct Viceroy = **Lord Chelmsford** |
| Gandhi withdrew NCM because of Rowlatt Act | NCM withdrawn due to **Chauri Chaura** incident |
| Bihar Provincial Congress founded 1905 | Bihar Provincial Congress founded **1908** |
| First civil disobedience = Dandi March | First civil disobedience = **Champaran 1917** |
| First hunger strike = Quit India | First hunger strike in India = **Ahmedabad Mill Strike 1918** |
| All parties supported Simon Commission | ALL major parties **boycotted** Simon Commission |

---

## 📌 GS QUICK REVISION TABLE

```
FREEDOM STRUGGLE — 3-PHASE TOPPER FRAMEWORK
══════════════════════════════════════════════════════════════════

PHASE 1: GANDHI'S FIRST STEPS IN INDIA (1917–1919)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1917 → Champaran (Bihar) [Rajkumar Shukla; Tinkathia; Rajendra Prasad]
1918 → Kheda [Patel; revenue; first major Patel role]
1918 → Ahmedabad [mill workers; Gandhi's first hunger strike]
1919 → Rowlatt Act → Hartal → Jallianwala Bagh [Viceroy: Chelmsford]

PHASE 2: MASS MOVEMENTS (1920–1934)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1920-22 → Non-Cooperation + Khilafat [Ali Brothers]
           ↓ Withdrawn → Chauri Chaura [22 policemen killed]
1923    → Swaraj Party [C.R. Das + Motilal Nehru]
1927    → Simon Commission boycotted [Lala Lajpat Rai dies]
1929    → Lahore Session: Purna Swaraj [Nehru; Jan 26 = Ind. Day]
1930-31 → Civil Disobedience + Dandi March [Gandhi-Irwin Pact]

PHASE 3: FINAL PUSH (1939–1947)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1942    → Quit India "Do or Die" [JP Narayan underground; Bihar]
1946    → Cabinet Mission
1947    → Independence + Partition [Mountbatten; Aug 15]
══════════════════════════════════════════════════════════════════
```

---
---
---

# ═══════════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 9
# ═══════════════════════════════════════════════════════

> **⚠️ INSTRUCTIONS:**
> ✅ Solve ALL 50 questions FIRST.
> ✅ Scroll to the ANSWER KEY only after attempting every question.
> ✅ Do NOT peek — that's how toppers build real memory!

---

## 💻 CS PRACTICE QUESTIONS — 25 Questions
### Topic: Pointers in C++ — &, *, NULL, delete/delete[], new vs malloc, Dangling

---

**Q1.** What is the output of the following code?
```cpp
int x = 10;
int* ptr = &x;
*ptr = 20;
cout << x;
```
- (A) 10
- (B) 20
- (C) Address of x
- (D) More than one of the above
- (E) None of the above

---

**Q2.** Consider: `int* ptr = NULL; delete ptr;`. What happens?
- (A) Runtime error / segmentation fault
- (B) Compilation error
- (C) Compiles and executes successfully with no crash
- (D) More than one of the above
- (E) None of the above

---

**Q3.** Which of the following is the correct way to allocate an array of 10 integers on the heap?
- (A) `int* arr = new int(10);`
- (B) `int* arr = new int[10];`
- (C) `int arr = malloc(10 * sizeof(int));`
- (D) More than one of the above
- (E) None of the above

---

**Q4.** After using `new[]` to allocate an array, which statement correctly frees the memory?
- (A) `delete arr;`
- (B) `delete[] arr;`
- (C) `free(arr);`
- (D) More than one of the above
- (E) None of the above

---

**Q5.** Which of the following is the KEY difference between `new` and `malloc()`?
- (A) `new` returns a void pointer; `malloc` returns typed pointer
- (B) `new` calls the constructor; `malloc` does not
- (C) `new` is slower than `malloc`
- (D) More than one of the above
- (E) None of the above

---

**Q6.** What is a dangling pointer?
- (A) A pointer that is initialized to NULL
- (B) A pointer that points to freed or out-of-scope memory
- (C) A pointer that stores the address of a pointer
- (D) More than one of the above
- (E) None of the above

---

**Q7.** What will be the output of this code?
```cpp
int arr[] = {5, 10, 15, 20};
int* ptr = arr;
ptr += 2;
cout << *ptr;
```
- (A) 5
- (B) 10
- (C) 15
- (D) More than one of the above
- (E) None of the above

---

**Q8.** In C++11, which keyword is preferred for a null pointer instead of `NULL`?
- (A) `null`
- (B) `nullpointer`
- (C) `nullptr`
- (D) More than one of the above
- (E) None of the above

---

**Q9.** Which of the following pointer operations is INVALID?
- (A) `ptr + 2`
- (B) `ptr - 1`
- (C) `ptr1 + ptr2` (adding two pointers)
- (D) More than one of the above
- (E) None of the above

---

**Q10.** What type of pointer can store the address of ANY data type without type casting?
- (A) `int*`
- (B) `char*`
- (C) `void*`
- (D) More than one of the above
- (E) None of the above

---

**Q11.** Consider this code:
```cpp
int* ptr = new int(5);
delete ptr;
delete ptr;
```
What happens on the second `delete`?
- (A) Nothing — it is safe to delete twice
- (B) Compilation error
- (C) Undefined behavior — double delete is dangerous
- (D) More than one of the above
- (E) None of the above

---

**Q12.** In the declaration `int* p, q;`, which variables are pointers?
- (A) Both p and q
- (B) Only p
- (C) Only q
- (D) More than one of the above
- (E) None of the above

---

**Q13.** What does `&x` represent when x is an int variable?
- (A) Value of x
- (B) Size of x in bytes
- (C) Memory address of x
- (D) More than one of the above
- (E) None of the above

---

**Q14.** Which of the following correctly creates a null pointer in C++11?
- (A) `int* ptr = 0;`
- (B) `int* ptr = NULL;`
- (C) `int* ptr = nullptr;`
- (D) More than one of the above
- (E) None of the above

---

**Q15.** What is the output?
```cpp
int x = 100;
int* ptr = &x;
cout << sizeof(ptr);
```
(Assume 64-bit system)
- (A) 4
- (B) 8
- (C) 100
- (D) More than one of the above
- (E) None of the above

---

**Q16.** Which function is used to deallocate memory allocated by `malloc()`?
- (A) `delete`
- (B) `delete[]`
- (C) `free()`
- (D) More than one of the above
- (E) None of the above

---

**Q17.** What happens when `new` fails to allocate memory?
- (A) Returns NULL
- (B) Returns 0
- (C) Throws `std::bad_alloc` exception
- (D) More than one of the above
- (E) None of the above

---

**Q18.** What does `**ptr` mean when `ptr` is a double pointer (int**)?
- (A) Pointer to a pointer
- (B) Value of the variable pointed to by the pointer pointed to by ptr
- (C) Address of ptr
- (D) More than one of the above
- (E) None of the above

---

**Q19.** Which of the following creates a memory leak?
- (A) `int* p = new int(5); delete p;`
- (B) `int* p = new int(5); p = nullptr;` (without delete)
- (C) `int* p = new int[5]; delete[] p;`
- (D) More than one of the above
- (E) None of the above

---

**Q20.** If `int* ptr = arr` where arr is an array, and we do `ptr++`, by how many bytes does ptr advance? (Assume int = 4 bytes)
- (A) 1 byte
- (B) 2 bytes
- (C) 4 bytes
- (D) More than one of the above
- (E) None of the above

---

**Q21.** A function returns the address of a local variable. The pointer in the calling function is then:
- (A) Valid — local variable still exists
- (B) A dangling pointer — local variable is destroyed
- (C) A null pointer
- (D) More than one of the above
- (E) None of the above

---

**Q22.** Which of the following is TRUE about `void*` (void pointer)?
- (A) It can point to any data type
- (B) It cannot be directly dereferenced without casting
- (C) It is returned by malloc()
- (D) More than one of the above
- (E) None of the above

---

**Q23.** What is the output?
```cpp
int a = 5, b = 10;
int* p = &a;
p = &b;
cout << *p;
```
- (A) 5
- (B) 10
- (C) Address of b
- (D) More than one of the above
- (E) None of the above

---

**Q24.** Which of the following statements about references in C++ is TRUE?
- (A) A reference can be NULL
- (B) A reference can be reassigned to refer to another variable
- (C) A reference must be initialized when declared and cannot be reassigned
- (D) More than one of the above
- (E) None of the above

---

**Q25.** What is the correct way to allocate a 2D array (3 rows, 4 columns) dynamically in C++?
- (A) `int arr = new int[3][4];`
- (B) `int** arr = new int*[3]; for(int i=0; i<3; i++) arr[i] = new int[4];`
- (C) `int* arr = new int[12];` (and use manual indexing)
- (D) More than one of the above (B and C are both valid approaches)
- (E) None of the above

---
---

## 🇮🇳 GS PRACTICE QUESTIONS — 25 Questions
### Topic: Champaran Satyagraha + Non-Cooperation + Civil Disobedience + Key Events

---

**Q26.** The Tinkathia system in Champaran required farmers to cultivate indigo on what fraction of their land?
- (A) 1/4th
- (B) 3/20th
- (C) 1/5th
- (D) More than one of the above
- (E) None of the above

---

**Q27.** Gandhi's first use of the Satyagraha technique WITHIN INDIA was at:
- (A) Dandi (Gujarat)
- (B) Kheda (Gujarat)
- (C) Champaran (Bihar)
- (D) More than one of the above
- (E) None of the above

---

**Q28.** Who was the key associate of Gandhi during the Champaran Satyagraha who later became the first President of India?
- (A) Jawaharlal Nehru
- (B) Rajkumar Shukla
- (C) Rajendra Prasad
- (D) More than one of the above
- (E) None of the above

---

**Q29.** The Non-Cooperation Movement was formally adopted at which INC session?
- (A) Calcutta Session 1920
- (B) Nagpur Session 1920
- (C) Gaya Session 1922
- (D) More than one of the above
- (E) None of the above

---

**Q30.** The Khilafat Movement was connected to which issue?
- (A) Demand for separate electorate for Muslims
- (B) Protection of the Ottoman Caliph after WWI
- (C) Demand for Pakistan
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Which incident caused Gandhi to withdraw the Non-Cooperation Movement in 1922?
- (A) Jallianwala Bagh massacre
- (B) Gandhi's arrest by British
- (C) Chauri Chaura (police station set on fire, 22 policemen killed)
- (D) More than one of the above
- (E) None of the above

---

**Q32.** The Salt Satyagraha (Dandi March) began from:
- (A) Dandi beach, Gujarat
- (B) Sabarmati Ashram, Ahmedabad
- (C) Gandhi's Wardha Ashram
- (D) More than one of the above
- (E) None of the above

---

**Q33.** The Gandhi-Irwin Pact (March 1931) led to:
- (A) India getting independence
- (B) Suspension of Civil Disobedience Movement
- (C) Formation of Pakistan
- (D) More than one of the above
- (E) None of the above

---

**Q34.** Who was the Viceroy of India when the Dandi March took place (1930)?
- (A) Lord Curzon
- (B) Lord Chelmsford
- (C) Lord Irwin
- (D) More than one of the above
- (E) None of the above

---

**Q35.** The Rowlatt Act (1919) was also known as:
- (A) Black Law (by Gandhi)
- (B) "No appeal, no Vakil, no Dalil"
- (C) Anarchical and Revolutionary Crimes Act
- (D) More than one of the above
- (E) None of the above

---

**Q36.** "Do or Die" was the slogan of which movement?
- (A) Non-Cooperation Movement
- (B) Civil Disobedience Movement
- (C) Quit India Movement
- (D) More than one of the above
- (E) None of the above

---

**Q37.** Who led the underground activities during Quit India Movement in Bihar?
- (A) Rajendra Prasad
- (B) Jayaprakash Narayan
- (C) Swami Sahajanand Saraswati
- (D) More than one of the above
- (E) None of the above

---

**Q38.** Rabindranath Tagore returned his knighthood as a protest against:
- (A) Partition of Bengal 1905
- (B) Rowlatt Act 1919
- (C) Jallianwala Bagh Massacre 1919
- (D) More than one of the above
- (E) None of the above

---

**Q39.** The Swaraj Party (1923) was founded by:
- (A) Jawaharlal Nehru and Motilal Nehru
- (B) C.R. Das and Motilal Nehru
- (C) Gandhi and C.R. Das
- (D) More than one of the above
- (E) None of the above

---

**Q40.** The Lahore Session of INC in December 1929 was presided by:
- (A) Mahatma Gandhi
- (B) Jawaharlal Nehru
- (C) Subhas Chandra Bose
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Simon Commission (1927) was boycotted because:
- (A) It proposed partition of India
- (B) It had no Indian member — all members were British
- (C) It banned INC from functioning
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Lala Lajpat Rai died as a result of:
- (A) Imprisonment during Non-Cooperation Movement
- (B) Lathi charge during protest against Simon Commission
- (C) Execution by British
- (D) More than one of the above
- (E) None of the above

---

**Q43.** Which of the following statements about the Champaran Agrarian Act 1918 is correct?
- (A) It introduced the Tinkathia system
- (B) It abolished the Tinkathia system
- (C) It gave land rights to British planters
- (D) More than one of the above
- (E) None of the above

---

**Q44.** The Kheda Satyagraha (1918) was related to:
- (A) Indigo cultivation
- (B) Salt tax
- (C) Revenue demand on failed crops
- (D) More than one of the above
- (E) None of the above

---

**Q45.** At which Round Table Conference did Gandhi represent the INC?
- (A) First Round Table Conference (1930)
- (B) Second Round Table Conference (1931)
- (C) Third Round Table Conference (1932)
- (D) More than one of the above
- (E) None of the above

---

**Q46.** "Poverty and Un-British Rule in India" which proposed the Drain Theory was written by:
- (A) Bal Gangadhar Tilak
- (B) Gopal Krishna Gokhale
- (C) Dadabhai Naoroji
- (D) More than one of the above
- (E) None of the above

---

**Q47.** Which Viceroy's period saw both the Jallianwala Bagh Massacre AND the launch of Non-Cooperation Movement?
- (A) Lord Curzon
- (B) Lord Chelmsford
- (C) Lord Reading
- (D) More than one of the above
- (E) None of the above

---

**Q48.** "Frontier Gandhi" — who had this title?
- (A) Jawaharlal Nehru
- (B) Khan Abdul Ghaffar Khan
- (C) Maulana Abul Kalam Azad
- (D) More than one of the above
- (E) None of the above

---

**Q49.** Sarojini Naidu's role in the Civil Disobedience Movement included:
- (A) Leading the Dharasana Salt Works raid
- (B) Presiding the Lahore INC session
- (C) Founding the Home Rule League
- (D) More than one of the above
- (E) None of the above

---

**Q50.** Which of the following are correctly matched?
```
I.   Champaran Satyagraha — Tinkathia system
II.  Jallianwala Bagh — Lord Chelmsford (Viceroy)
III. Dandi March — Lord Irwin (Viceroy)
IV.  Quit India — Lord Linlithgow (Viceroy)
```
- (A) Only I and II
- (B) Only I, II, and III
- (C) I, II, III, and IV — all correct
- (D) More than one of the above
- (E) None of the above

---
---
---

# ═══════════════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 9
# ═══════════════════════════════════════════════════════

> **⛔ STOP — Do NOT read this until you have attempted all 50 questions!**

---

## 💻 CS ANSWERS (Q1–Q25)

| Q# | Answer | Explanation |
|----|--------|-------------|
| Q1 | **(B)** | `*ptr = 20` dereferences ptr and sets x's value to 20. So `cout << x` prints **20**. |
| Q2 | **(C)** | Deleting a NULL pointer is **guaranteed safe** by C++ standard — no crash, no-op. This is a direct PYQ fact! |
| Q3 | **(B)** | `new int[10]` allocates array of 10 ints. `new int(10)` allocates ONE int with value 10. Option C has wrong type (int instead of int*). |
| Q4 | **(B)** | `delete[] arr` — MUST use `delete[]` for arrays allocated with `new[]`. Using `delete` alone = undefined behavior. |
| Q5 | **(B)** | Key difference: `new` **calls the constructor**; `malloc` does **not**. Both allocate heap memory, but new is type-safe and OOP-aware. |
| Q6 | **(B)** | Dangling pointer = pointer to **freed or out-of-scope memory**. Using it = undefined behavior. |
| Q7 | **(C)** | `ptr` starts at arr[0]=5. `ptr += 2` moves 2 positions forward → arr[2] = **15**. |
| Q8 | **(C)** | `nullptr` is the C++11 keyword. It's type-safe unlike NULL (which is just `0`). |
| Q9 | **(C)** | Adding two pointers (`ptr1 + ptr2`) is **invalid**. Subtracting pointers is valid (gives count). Adding integer to pointer is valid. |
| Q10 | **(C)** | `void*` can store address of **any type** — that's its purpose. But must cast before dereferencing. |
| Q11 | **(C)** | Double delete = **undefined behavior** (potential crash, memory corruption). After first delete, ptr is dangling — second delete is dangerous. |
| Q12 | **(B)** | In `int* p, q;` — only **p** is a pointer. `q` is a plain `int`. The `*` binds to `p`, not to `int`. |
| Q13 | **(C)** | `&x` gives the **memory address** of x. It's the address-of operator. |
| Q14 | **(D)** | All three (`= 0`, `= NULL`, `= nullptr`) create null pointers. `nullptr` is the C++11 preferred way. **More than one correct!** |
| Q15 | **(B)** | On a 64-bit system, ALL pointers are **8 bytes** regardless of the type they point to. (32-bit = 4 bytes). |
| Q16 | **(C)** | `free()` is paired with `malloc()`. `delete` is for `new`. Mixing them = undefined behavior. |
| Q17 | **(C)** | `new` throws **`std::bad_alloc`** exception on failure. `malloc()` returns NULL on failure. |
| Q18 | **(B)** | `**ptr` means double dereference — get the **value of the variable** that the inner pointer points to. |
| Q19 | **(B)** | `int* p = new int(5); p = nullptr;` — memory was allocated but NOT freed. Pointer lost → **memory leak**! |
| Q20 | **(C)** | For `int*`, pointer arithmetic moves by `sizeof(int)` = **4 bytes** per increment. |
| Q21 | **(B)** | When function returns, local variables are destroyed. Pointer to local variable becomes **dangling**. |
| Q22 | **(D)** | `void*` can point to any type ✅, cannot be directly dereferenced ✅, returned by malloc() ✅ — **ALL THREE correct**! |
| Q23 | **(B)** | `p` first points to `a` (=5). Then `p = &b` reassigns pointer to `b` (=10). `*p = 10`. Output: **10**. |
| Q24 | **(C)** | A reference **must be initialized at declaration** and **cannot be reassigned** to another variable. It cannot be NULL. |
| Q25 | **(D)** | Both B (array of pointers) and C (flat array with manual indexing) are valid approaches for 2D dynamic arrays — **more than one correct**. |

---

## 🇮🇳 GS ANSWERS (Q26–Q50)

| Q# | Answer | Explanation |
|----|--------|-------------|
| Q26 | **(B)** | Tinkathia = 3 kathas out of 20 = **3/20th** of land for forced indigo cultivation. |
| Q27 | **(C)** | Gandhi's first Satyagraha IN INDIA = **Champaran, Bihar (1917)**. First Satyagraha globally was in South Africa. |
| Q28 | **(C)** | **Rajendra Prasad** assisted Gandhi in Champaran and later became India's first President. Rajkumar Shukla only invited Gandhi. |
| Q29 | **(B)** | NCM formally adopted at **Nagpur Session, December 1920**. Calcutta special session (Sept 1920) launched it, Nagpur formalized it. |
| Q30 | **(B)** | Khilafat = protection of **Ottoman Caliph** after WWI dismemberment of Ottoman Empire. Gandhi supported it for Hindu-Muslim unity. |
| Q31 | **(C)** | **Chauri Chaura** — mob killed 22 policemen. Gandhi withdrew NCM saying violence violated Satyagraha principles. |
| Q32 | **(B)** | Dandi March started from **Sabarmati Ashram, Ahmedabad** on March 12, 1930. Ended at Dandi beach. |
| Q33 | **(B)** | Gandhi-Irwin Pact → INC agreed to **suspend Civil Disobedience Movement**. British released political prisoners. |
| Q34 | **(C)** | **Lord Irwin** was Viceroy during Dandi March (1930). The Gandhi-Irwin Pact is named after him. |
| Q35 | **(D)** | Rowlatt Act was called "Black Law" ✅, "No appeal, no Vakil, no Dalil" ✅, and officially "Anarchical and Revolutionary Crimes Act" ✅ — **all three correct**! |
| Q36 | **(C)** | "Do or Die" (Karo ya Maro) = slogan of **Quit India Movement (1942)**. |
| Q37 | **(B)** | **Jayaprakash Narayan (JP)** escaped from Hazaribagh jail and led underground Quit India activities in Bihar. |
| Q38 | **(C)** | Tagore returned knighthood protesting **Jallianwala Bagh Massacre (1919)**. NOT Partition of Bengal. |
| Q39 | **(B)** | Swaraj Party = **C.R. Das + Motilal Nehru** (1923). Strategy: enter legislatures to obstruct British from within. |
| Q40 | **(B)** | **Jawaharlal Nehru** presided Lahore INC session (December 1929) — youngest President. Purna Swaraj resolution passed. |
| Q41 | **(B)** | Simon Commission boycotted because **all members were British — no Indian member** included. |
| Q42 | **(B)** | Lala Lajpat Rai was injured in **lathi charge** during Simon Commission protest in Lahore (1928). Died weeks later. Bhagat Singh later avenged his death. |
| Q43 | **(B)** | Champaran Agrarian Act 1918 **abolished the Tinkathia system**. It was the RESULT of the Satyagraha. |
| Q44 | **(C)** | Kheda Satyagraha = about **revenue demand on failed crops**. Farmers couldn't pay; demanded waiver. Sardar Patel's first major role. |
| Q45 | **(B)** | Gandhi attended only the **Second Round Table Conference (1931)** in London. He was in jail during 1st and 3rd. |
| Q46 | **(C)** | **Dadabhai Naoroji** wrote "Poverty and Un-British Rule in India" — proposed the Drain Theory of India's poverty. |
| Q47 | **(B)** | **Lord Chelmsford** (1916–21) was Viceroy during both Jallianwala Bagh (1919) AND the start of Non-Cooperation (1920). |
| Q48 | **(B)** | **Khan Abdul Ghaffar Khan** = "Frontier Gandhi" — led Khudai Khidmatgar (Red Shirts) in North-West Frontier Province. |
| Q49 | **(A)** | **Sarojini Naidu led the Dharasana Salt Works raid** in May 1930 after Gandhi's arrest. She was a key CDM leader. |
| Q50 | **(C)** | All four matchings are CORRECT: Champaran-Tinkathia ✅, Jallianwala-Chelmsford ✅, Dandi-Irwin ✅, Quit India-Linlithgow ✅ → Answer **(C)** which equals D logic but option C says all correct. |

---

## 📊 YOUR SCORE ANALYSIS

| Score Range | Category | What to Do |
|-------------|----------|------------|
| 23–25 | 🏆 **TOPPER LEVEL** | Revise only the ones you got wrong |
| 20–22 | ✅ **STRONG** | Re-read the 3–5 topics you missed |
| 16–19 | 🔄 **DEVELOPING** | Re-read concept sections above |
| Below 16 | 📖 **Needs Work** | Re-read full Day 9 + retry tomorrow |

---

## 📝 NIGHT REVISION — Write These From Memory Before Sleeping

### CS (5 Key Points):
1. `delete NULL_ptr` → SAFE, no crash — guaranteed by C++ standard ⭐
2. `new` calls **constructor**; `malloc` does **NOT** — key OOP difference
3. `new[]` must be freed with `delete[]` — mismatch = undefined behavior
4. Dangling pointer = pointer to freed/destroyed memory — use `ptr = nullptr` after delete
5. `void*` = can point to any type, cannot dereference directly without cast

### GS (5 Key Points):
1. Champaran 1917 — Tinkathia (indigo) — Rajkumar Shukla invited — Rajendra Prasad assisted ⭐
2. NCM withdrawn 1922 — Chauri Chaura — 22 policemen killed in burning police station ⭐
3. Dandi March — March 12, 1930 — Sabarmati to Dandi — Viceroy: Lord Irwin
4. Jallianwala Bagh — April 13, 1919 — Viceroy: Lord Chelmsford — Tagore returned knighthood
5. Quit India — August 9, 1942 — "Do or Die" — JP Narayan underground in Bihar ⭐

---

## ⏭️ PREVIEW: DAY 10

**CS:** Arrays in C++ — declaration, `is_array()`, `rank()`, 1D/2D, string as char array, `+` operator compile error
**GS:** Non-Cooperation Movement full detail + Civil Disobedience deep facts (revision + new angles)

---

*Day-9 Complete ✅ | Phase 1 → Week 2 | BPSC TRE 4.0 Topper Preparation*
*"Pointers and Champaran — both are about understanding what lies BENEATH the surface!"* 🎯
