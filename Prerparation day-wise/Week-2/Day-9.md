# 📅 BPSC TRE 4.0 — DAY 9 COMPLETE STUDY MODULE
### C++ Pointers (Complete) + Champaran Satyagraha 1917
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): C++ Pointers — all concepts with memory diagrams
> - Afternoon (1 hr): Champaran Satyagraha — story-based deep understanding
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 C++ Pointers — Complete Deep Dive

---

## 🔷 SECTION 1: What is a Pointer? (The Foundation)

### Real-Life Analogy — The Hotel Room:
```
Imagine a large hotel building (= computer memory).
Each room has a unique room number (= memory address).
The GUEST inside the room (= actual data/value).
A NOTEPAD where you write someone's room number (= pointer variable).

Pointer = A variable that stores the ROOM NUMBER (address),
          NOT the guest (value) itself.
```

### Technical Definition:
> A **pointer** is a variable that stores the **memory address** of another variable.

### Why Pointers Matter (Exam Context):
- Dynamic memory allocation (`new`/`delete`)
- Passing large data to functions efficiently
- Building data structures (linked lists, trees)
- Direct memory manipulation

---

## 🔷 SECTION 2: Memory Layout — The Visual Core

### How Variables are Stored in Memory:
```
MEMORY (simplified view):
┌─────────┬──────────────┬──────────────┐
│ Address │   Variable   │    Value     │
├─────────┼──────────────┼──────────────┤
│  1000   │   int x = 5  │      5       │
│  1004   │   int y = 10 │     10       │
│  1008   │  int* p = ?  │    1000      │  ← p stores ADDRESS of x
│  1012   │     ...      │     ...      │
└─────────┴──────────────┴──────────────┘

p is a pointer. It holds the value 1000 (= address of x).
*p gives us the value at address 1000, which is 5.
```

---

## 🔷 SECTION 3: The Two Key Operators

### Operator 1: `&` — Address-of Operator
> `&variable` gives the **memory address** of that variable.

```cpp
int x = 5;
cout << x;    // Output: 5       (the value)
cout << &x;   // Output: 1000    (the address, e.g. 0x7ffe1234)
```

### Operator 2: `*` — Dereference Operator (Indirection)
> `*pointer` gives the **value stored at** the address the pointer holds.

```cpp
int x = 5;
int* p = &x;   // p holds address of x

cout << p;     // Output: 1000   (address stored in p)
cout << *p;    // Output: 5      (value at that address = x)
```

### The & vs * Summary:
```
&x  →  "Give me the ADDRESS of x"
*p  →  "Give me the VALUE at the address stored in p"

& and * are INVERSE operations:
  *(&x) == x       (address then dereference = original value)
  &(*p) == p       (dereference then address = original pointer)
```

---

## 🔷 SECTION 4: Pointer Declaration & Initialization

### Syntax:
```
data_type * pointer_name;
```

### Examples:
```cpp
int*   p;       // pointer to int
float* fptr;    // pointer to float
char*  cptr;    // pointer to char
double* dptr;   // pointer to double

// The * can go with the type OR the name — both are valid:
int* p;         // Style 1 (recommended)
int *p;         // Style 2 (also valid)
```

### Initialization:
```cpp
int x = 42;
int* p = &x;    // p now points to x

// Visualization:
// x:  [42] at address 2000
// p:  [2000]  ← stores address of x
```

### Multiple Pointer Declaration Trap:
```cpp
int* p, q;     // ⚠️ TRAP! p is a pointer, q is a plain int
int *p, *q;    // ✅ CORRECT: both p and q are pointers
```

### 🚨 PYQ TRAP #1:
> `int* p, q;` declares ONE pointer (p) and ONE integer (q).
> To declare two pointers: `int *p, *q;`

---

## 🔷 SECTION 5: NULL Pointer — C vs C++11

### What is a NULL Pointer?
A pointer that does **not point to any valid memory location**.

```
NULL pointer = a pointer that stores address 0 (or null address)
            = "this pointer points to nothing right now"
```

### NULL vs nullptr:

| Feature | `NULL` (C / old C++) | `nullptr` (C++11 onwards) |
|---------|---------------------|--------------------------|
| Type | Integer constant (0) | Pointer type (std::nullptr_t) |
| Header | `<cstdlib>` or `<cstring>` | Built-in keyword (no header) |
| Type safety | Can accidentally assign to int | Cannot assign to int — safer |
| Recommended | Old code only | **Use this in modern C++** |

```cpp
// Old style (C):
int* p = NULL;      // p = 0 internally

// Modern C++ (C++11+):
int* p = nullptr;   // type-safe null pointer
```

### 🚨 PYQ TRAP #2 — The Most Important Pointer Trap:
```cpp
int* p = NULL;
delete p;      // ✅ VALID — NO error, NO crash
               // Deleting a NULL pointer is a safe no-op
               // It does absolutely nothing — no exception, no crash
```
> **"Deleting a NULL pointer is always safe in C++."**
> This is one of the most asked facts in BPSC TRE PYQs!

### Uninitialized Pointer Danger:
```cpp
int* p;        // ⚠️ DANGEROUS — p has garbage address
*p = 10;       // UNDEFINED BEHAVIOR — writing to random memory
               // Can crash the program or corrupt data!

// Always initialize pointers:
int* p = nullptr;  // Safe — points to nothing
```

---

## 🔷 SECTION 6: Dynamic Memory Allocation — `new` and `delete`

### What is Dynamic Memory?
```
STACK memory  = automatically managed, limited size, local variables
HEAP memory   = manually managed, larger, for dynamic allocation (new/delete)
```

### The `new` Operator:
```cpp
// Syntax:
pointer = new data_type;          // allocate 1 element
pointer = new data_type[size];    // allocate array

// Examples:
int* p = new int;          // allocates 1 int on heap
int* arr = new int[10];    // allocates array of 10 ints on heap
*p = 25;                   // store value at allocated memory
```

```
HEAP MEMORY after: int* p = new int;
┌──────────────────────────────────────────┐
│ HEAP                                     │
│ Address 5000: [garbage/25 after *p=25]   │ ← allocated by new
└──────────────────────────────────────────┘

STACK:
│ p: [5000]   │  ← p stores the heap address
```

### The `delete` Operator:
```cpp
// For single object:
delete p;        // frees the memory allocated by new

// For array:
delete[] arr;    // frees memory allocated by new[]
```

### 🚨 PYQ TRAP #3 — delete vs delete[]:
```cpp
int* p = new int;        // single object
delete p;                // ✅ CORRECT
delete[] p;              // ❌ WRONG (undefined behavior)

int* arr = new int[10];  // array
delete[] arr;            // ✅ CORRECT
delete arr;              // ❌ WRONG (undefined behavior — memory leak)
```

> **Rule**: `new` → `delete` | `new[]` → `delete[]`
> Mixing them = **undefined behavior** = guaranteed exam trap!

### Full Example:
```cpp
#include <iostream>
using namespace std;

int main() {
    // Allocate single int
    int* p = new int;
    *p = 100;
    cout << *p << endl;    // Output: 100
    delete p;              // Free memory
    p = nullptr;           // Good practice: reset to null after delete

    // Allocate array
    int* arr = new int[5];
    for (int i = 0; i < 5; i++)
        arr[i] = i * 10;
    delete[] arr;          // Must use delete[]
    arr = nullptr;

    return 0;
}
```

---

## 🔷 SECTION 7: `new` vs `malloc` — The Classic Comparison

| Feature | `new` (C++) | `malloc` (C) |
|---------|------------|-------------|
| Language | C++ only | C and C++ |
| Returns | Typed pointer (e.g., `int*`) | `void*` (requires cast) |
| Constructor call | **YES — calls constructor** | **NO — does not call constructor** |
| Destructor call | YES (via `delete`) | NO (via `free`) |
| On failure | Throws `std::bad_alloc` exception | Returns `NULL` |
| Header needed | None (built-in keyword) | `<cstdlib>` |
| Paired with | `delete` / `delete[]` | `free()` |
| Size calculation | Automatic | Manual (`sizeof(type) * n`) |

```cpp
// new — automatic size, calls constructor:
int* p1 = new int(5);     // allocates and initializes to 5
                          // constructor called (for objects)

// malloc — manual size, no constructor:
int* p2 = (int*)malloc(sizeof(int));  // cast required
*p2 = 5;                              // manual initialization
free(p2);                             // must use free, NOT delete
```

### 🚨 PYQ TRAP #4 — The Constructor Difference:
> `new` **calls the constructor** of the object being created.
> `malloc` does NOT — it only allocates raw memory.
> For C++ classes/objects, ALWAYS use `new`, not `malloc`.

### 🚨 PYQ TRAP #5 — Mixing new/free or malloc/delete:
```cpp
int* p = new int;
free(p);          // ❌ WRONG — new must be paired with delete
                  // Undefined behavior!

int* q = (int*)malloc(sizeof(int));
delete q;         // ❌ WRONG — malloc must be paired with free
                  // Undefined behavior!
```

---

## 🔷 SECTION 8: Pointer Arithmetic

### Core Rule:
When you increment/decrement a pointer, it moves by the **size of the data type** it points to.

```cpp
int arr[] = {10, 20, 30, 40, 50};
int* p = arr;   // p points to arr[0] = 10

cout << *p;     // Output: 10
p++;            // p moves forward by sizeof(int) = 4 bytes
cout << *p;     // Output: 20
p++;
cout << *p;     // Output: 30
```

### Memory View of Pointer Arithmetic:
```
Address:  1000   1004   1008   1012   1016
Value:    [10]   [20]   [30]   [40]   [50]
           ↑      ↑      ↑
           p     p+1   p+2
          (p++)  (p++)

p points to address 1000 (value 10)
p+1 points to address 1004 (value 20) — moves by 4 (sizeof int)
p+2 points to address 1008 (value 30)
```

### Pointer Arithmetic Operations:
```cpp
int* p = arr;

p + n    // move n elements forward
p - n    // move n elements backward
p++      // move to next element
p--      // move to previous element
p1 - p2  // number of elements between two pointers (same array)

// Valid:
int* q = p + 3;   // q points 3 ints ahead of p
int diff = q - p; // diff = 3

// INVALID operations on pointers:
p1 + p2;   // ❌ Cannot add two pointers
p * 2;     // ❌ Cannot multiply pointer by scalar
p / 2;     // ❌ Cannot divide pointer
```

### 🚨 PYQ TRAP #6 — Pointer size:
```cpp
int* p;
double* d;
char* c;

sizeof(p) == sizeof(d) == sizeof(c)  // ALL EQUAL!
// Size of ANY pointer = 4 bytes (32-bit) or 8 bytes (64-bit)
// Pointer size depends on system architecture, NOT the data type it points to
```

---

## 🔷 SECTION 9: Dangling Pointer

### What is a Dangling Pointer?
> A pointer that points to **memory that has been freed/deallocated** or that has gone out of scope.

### Three Causes of Dangling Pointers:

#### Cause 1: Deleting without resetting to NULL:
```cpp
int* p = new int(10);
delete p;     // Memory freed — heap memory is now "garbage"
// p still holds the old address (1000)
// p is now a DANGLING POINTER
*p = 20;      // ⚠️ UNDEFINED BEHAVIOR — accessing freed memory!

// FIX:
delete p;
p = nullptr;  // Reset to null — no longer dangling
```

#### Cause 2: Pointer to local variable after function returns:
```cpp
int* getDanglingPointer() {
    int local = 42;   // local variable on stack
    return &local;    // ⚠️ Returns address of local variable
}                     // local is DESTROYED when function ends

int* p = getDanglingPointer();
cout << *p;   // ⚠️ UNDEFINED BEHAVIOR — local is gone!
```

#### Cause 3: Multiple pointers, one deletes:
```cpp
int* p1 = new int(10);
int* p2 = p1;    // both point to same memory
delete p1;       // memory freed
p1 = nullptr;    // p1 is now safe
// p2 still holds the old address — p2 is now DANGLING!
*p2 = 20;        // ⚠️ UNDEFINED BEHAVIOR
```

### Dangling vs Wild Pointer:
```
Dangling Pointer = pointer to FREED/DESTROYED memory
                 = was valid, now invalid

Wild Pointer     = UNINITIALIZED pointer
                 = never pointed anywhere valid
                 = int* p; (no assignment)
```

---

## 🔷 SECTION 10: Pointer to Pointer (Double Pointer)

```cpp
int x = 5;
int* p = &x;     // p points to x
int** pp = &p;   // pp points to p

cout << x;    // 5      (direct value)
cout << *p;   // 5      (dereference p)
cout << **pp; // 5      (dereference twice)
cout << p;    // 1000   (address of x)
cout << *pp;  // 1000   (value of p = address of x)
cout << pp;   // 2000   (address of p)
```

```
Memory:
Address 1000: [5]      ← x
Address 2000: [1000]   ← p  (stores address of x)
Address 3000: [2000]   ← pp (stores address of p)
```

---

## 🔷 SECTION 11: void Pointer (Generic Pointer)

```cpp
void* ptr;          // Can point to any data type
int x = 10;
float f = 3.14;

ptr = &x;           // ✅ Valid — void* can hold int address
ptr = &f;           // ✅ Valid — void* can hold float address

// But you CANNOT dereference void* directly:
// cout << *ptr;    // ❌ Error — must cast first
cout << *(int*)ptr;   // ✅ Cast then dereference
```

### Key Facts about void*:
- Used in `malloc()` — returns `void*`
- Used for generic/type-independent code
- **Cannot be dereferenced without casting**
- **Cannot perform pointer arithmetic** on void*

---

## 📊 VISUAL SUMMARY — Pointer Concepts

```
POINTER COMPLETE MAP
│
├── Declaration:   int* p;
├── Initialization: p = &x;
│
├── Operators:
│   ├── & (address-of): &x → gives address
│   └── * (dereference): *p → gives value at address
│
├── Special Values:
│   ├── NULL (old C style) = 0
│   └── nullptr (C++11) = type-safe null
│
├── Dynamic Memory:
│   ├── new int     → delete p
│   ├── new int[n]  → delete[] arr
│   ├── malloc()    → free()
│   └── new calls constructor; malloc does NOT
│
├── Arithmetic:
│   ├── p++, p--, p+n = moves by sizeof(type)
│   ├── p1 - p2 = element difference
│   └── sizeof(any pointer) = 4 or 8 bytes
│
└── Problems:
    ├── Dangling: points to freed memory
    ├── Wild: uninitialized pointer
    └── Memory leak: new without delete
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Champaran Satyagraha 1917 — Story-Based Deep Dive

---

## 🔷 THE STORY BEGINS: Bihar's Indigo Fields

### Setting the Scene — Late 19th Century Bihar:
```
Location: Champaran district, Bihar (now split into East & West Champaran)
Problem: British planters forcing farmers to grow INDIGO
System: "TINKATHIA SYSTEM"
```

### What was the Tinkathia System?
```
"Teen" (3) + "Katha" (unit of land measurement) = Tinkathia

Every farmer had to grow indigo on 3/20 (3 katha per bigha) of their land.
The farmer had NO CHOICE — it was a contractual obligation to the British planter.
Indigo fetched LOW prices (fixed by the planter, not market).
Farmers were LOSING money but were forced to continue.
```

### Why was Indigo Profitable for British but Devastating for Farmers?
```
British Indigo Planter:
  → Paid farmers almost nothing for indigo
  → Exported indigo dye to Europe at huge profit
  → Had colonial government support

Champaran Farmer:
  → Forced to grow indigo INSTEAD of food crops
  → Got paid below market rate
  → No legal recourse — any protest meant eviction
  → Debt slavery became common
```

---

## 🔷 THE CALL FOR HELP — RAJ KUMAR SHUKLA

### Enter Raj Kumar Shukla:
```
Who: A poor indigo farmer from Champaran
What he did: Traveled to various INC sessions seeking help
             He met Gandhi at the 1916 Lucknow Congress session
His plea: "Please come to Champaran and see our suffering"
Gandhi's initial response: "I know nothing about indigo cultivation"
Shukla's persistence: He followed Gandhi from Lucknow to Kanpur
                      to Ahmedabad to Calcutta — for months!
```

### The Persistent Plea — Timeline:
```
December 1916 → Shukla meets Gandhi at Lucknow Congress session
                Gandhi says "I cannot promise, I know nothing of Champaran"
↓
Shukla follows Gandhi to Kanpur, Ahmedabad, everywhere
↓
Gandhi finally agrees: "I will come to see for myself"
↓
April 1917 → Gandhi arrives at Patna first
             (Rajendra Prasad helps receive him in Patna)
↓
Gandhi reaches Motihari (Champaran) on April 15, 1917
```

---

## 🔷 GANDHI IN CHAMPARAN — THE ARRIVAL & IMMEDIATE CRISIS

### Gandhi Arrives — First Obstacle:
```
April 15, 1917: Gandhi reaches Motihari, Champaran
↓
District Magistrate issues notice:
"You are ordered to leave Champaran immediately"
↓
Gandhi's response: "I REFUSE to leave. I will disobey the order."
"I will accept the consequences."
↓
Government summons Gandhi to court
↓
THOUSANDS of farmers crowd the courthouse
Government realizes: enforcing this will cause massive unrest
↓
Government WITHDRAWS the case
↓
This was Gandhi's FIRST ACT OF CIVIL DISOBEDIENCE IN INDIA
```

> **Significance**: Gandhi showed that peaceful non-compliance with unjust orders can force the government to back down. This became the template for all future Satyagrahas.

---

## 🔷 THE INVESTIGATION — GANDHI'S METHODOLOGY

### Gandhi's Approach (Revolutionary for the Time):
```
Step 1: Systematic fact-finding
        → Interviewed hundreds of farmers door-to-door
        → Documented every case of exploitation
        → Collected evidence methodically

Step 2: Built local team
        → Rajendra Prasad (later India's 1st President)
        → Brij Kishore Prasad (lawyer)
        → J.B. Kripalani (accompanied Gandhi)
        → Mazhar-ul-Haq (lawyer, helped Gandhi)

Step 3: Legal challenge
        → Filed cases on behalf of exploited farmers
        → Challenged the Tinkathia system legally

Step 4: Negotiation with Government
        → Government set up a Committee of Inquiry
        → Gandhi was made a member of this committee
```

---

## 🔷 KEY FIGURES — MUST REMEMBER TABLE

| Person | Role/Significance |
|--------|------------------|
| **Raj Kumar Shukla** | Champaran farmer who persuaded Gandhi to come — **the catalyst** |
| **Mahatma Gandhi** | Led the movement; first Satyagraha in India |
| **Rajendra Prasad** | Helped Gandhi in Champaran; later India's 1st President (Bihar!) |
| **Brij Kishore Prasad** | Lawyer who supported the movement |
| **J.B. Kripalani** | Accompanied Gandhi; future Congress President |
| **Mazhar-ul-Haq** | Lawyer-colleague who aided Gandhi |
| **Lord Chelmsford** | Viceroy of India at that time |
| **W.B. Heycock** | District Magistrate who issued expulsion order against Gandhi |

---

## 🔷 TIMELINE — CHAMPARAN SATYAGRAHA

```
1917 CHAMPARAN SATYAGRAHA — KEY DATES
════════════════════════════════════════

December 1916
    │  → Shukla meets Gandhi at Lucknow Congress
    │
April 10, 1917
    │  → Gandhi reaches Patna (Rajendra Prasad receives him)
    │
April 15, 1917
    │  → Gandhi reaches Motihari, Champaran
    │  → Issued expulsion notice by District Magistrate
    │  → Gandhi refuses to leave — FIRST civil disobedience in India
    │
April 18, 1917
    │  → Court summons Gandhi
    │  → Thousands of farmers gather at courthouse
    │  → Government withdraws the case
    │
April–June 1917
    │  → Gandhi conducts detailed investigation
    │  → Interviews hundreds of farmers
    │  → Documents exploitation systematically
    │
June 1917
    │  → Government establishes Champaran Agrarian Committee
    │  → Gandhi is included as a member
    │
1918
    │  → Champaran Agrarian Act passed
       → Tinkathia System ABOLISHED
       → Farmers compensated (25% refund of illegal collections)
       → Farmers FREE to grow whatever they choose
```

---

## 🔷 OUTCOMES AND SIGNIFICANCE

### Immediate Results:
```
✅ Tinkathia System abolished (forced indigo cultivation ended)
✅ Champaran Agrarian Act, 1918 passed
✅ Farmers refunded 25% of illegal exactions by planters
✅ Farmers free to grow food crops instead of indigo
```

### Historical Significance:
```
1. FIRST SATYAGRAHA IN INDIA by Gandhi
   (Gandhi had done Satyagrahas in South Africa before this)

2. FIRST CIVIL DISOBEDIENCE IN INDIA
   (Refusing to obey unjust government order)

3. Proved the Satyagraha model works in India
   → Template for Non-Cooperation, Civil Disobedience, Quit India

4. Built Gandhi's mass connection with Indian peasantry
   → Gandhi understood rural India's suffering firsthand

5. Brought national leaders to Bihar's villages
   → Rajendra Prasad, J.B. Kripalani began their rural work here
```

### Tagore's Recognition:
> Rabindranath Tagore gave Gandhi the title **"MAHATMA"** (Great Soul).
> Though some historians credit this to the Champaran period, others say it was used earlier in South Africa by some.
> For exams: Tagore is most associated with giving Gandhi the title "Mahatma."

---

## 🔷 CHAMPARAN — GEOGRAPHIC & BIHAR FACTS

### Geographic Context:
```
Champaran = "Champa" (a tree) + "Aranya" (forest) = Forest of Champa trees
Location: Northern Bihar, bordering Nepal
Division: Now two districts:
          → East Champaran (Motihari is headquarters)
          → West Champaran (Bettiah is headquarters)

Motihari = the town where Gandhi was first arrested/summoned
Bettiah = town where many European indigo factories were located
```

### Why Bihar Connection is So Strong:
```
1. Champaran is IN Bihar — the movement happened here
2. Rajendra Prasad (Bihar, Siwan) helped Gandhi in Champaran
3. Champaran Satyagraha is Bihar's proudest freedom struggle moment
4. Motihari (East Champaran) has a Gandhi museum today
5. April 15 is celebrated as "Gandhi Arrival Day" in Champaran
```

---

## 🔷 COMPARISON: THREE EARLY GANDHIAN MOVEMENTS

| Feature | Champaran (1917) | Kheda (1918) | Ahmedabad (1918) |
|---------|-----------------|-------------|-----------------|
| Location | Bihar | Gujarat | Gujarat |
| Issue | Forced indigo cultivation (Tinkathia) | Crop failure + revenue demand | Mill workers' wages |
| Gandhi's role | Led investigation + civil disobedience | Supported peasants | First hunger strike |
| Result | Tinkathia abolished, Agrarian Act | Revenue suspended | 35% wage hike |
| Against whom | British indigo planters + Govt | British revenue authorities | Mill owners (Ambalal Sarabhai) |
| Type | Peasant movement | Peasant movement | Labour movement |

### 🚨 PYQ TRAP #7:
> Champaran = **farmers vs indigo planters** (agrarian movement)
> Kheda = **farmers vs government** (revenue remission demand)
> Ahmedabad = **workers vs mill owners** (wage dispute) — Gandhi's first hunger strike

---

## 🔷 MEMORY TRICKS FOR CHAMPARAN

```
CHAMPARAN KEY FACTS — MEMORY AIDS:

"SHUKLA CALLED, GANDHI CAME, TINKATHIA TAMED"
→ Raj Kumar Shukla called Gandhi
→ Gandhi came to Motihari (April 15, 1917)
→ Tinkathia system was abolished (1918)

"15 April = Gandhi in Motihari"
(April 15 is Tax Day in USA — Gandhi arrived to fight an unfair tax-like system)

"3 katha per bigha = Tinkathia"
(Teen = 3 in Hindi → Tinkathia = 3 katha forced cultivation)

CHAMPARAN TEAM: "RAJENDRA + BRIJ + KRIPALANI + MAZHAR"
→ Rajendra Prasad (future President of India!)
→ Brij Kishore Prasad (lawyer)
→ J.B. Kripalani (future Congress President)
→ Mazhar-ul-Haq (lawyer)
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Pointers, new/delete, NULL/nullptr, Arithmetic, Dangling Pointer

---

**Q1.** What is the correct way to declare a pointer to an integer in C++?
(A) `int p*;`
(B) `int* p;`
(C) `pointer int p;`
(D) More than one of the above
(E) None of the above

---

**Q2.** Given `int x = 10; int* p = &x;` — what does `*p` return?
(A) The address of x
(B) The address of p
(C) The value of x, which is 10
(D) More than one of the above
(E) None of the above

---

**Q3.** What happens when you execute `delete ptr;` where `ptr = NULL`?
(A) Runtime error
(B) Segmentation fault
(C) Nothing — it is a safe no-operation
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the key difference between `new` and `malloc`?
(A) `new` calls the constructor; `malloc` does not
(B) `malloc` is only for C; `new` works in C and C++
(C) `new` returns `void*`; `malloc` returns a typed pointer
(D) More than one of the above
(E) None of the above

---

**Q5.** Which of the following correctly allocates an array of 5 integers on the heap?
(A) `int* arr = new int(5);`
(B) `int* arr = new int[5];`
(C) `int arr = new[5] int;`
(D) More than one of the above
(E) None of the above

---

**Q6.** Which operator is used to free heap memory allocated with `new[]`?
(A) `delete`
(B) `free()`
(C) `delete[]`
(D) More than one of the above
(E) None of the above

---

**Q7.** What is a dangling pointer?
(A) A pointer that is not initialized
(B) A pointer that points to memory that has been freed or gone out of scope
(C) A pointer with the value NULL
(D) More than one of the above
(E) None of the above

---

**Q8.** Consider: `int arr[] = {10, 20, 30}; int* p = arr; p++;` — what does `*p` give?
(A) 10
(B) 20
(C) Address of arr[1]
(D) More than one of the above
(E) None of the above

---

**Q9.** What is `nullptr` in C++?
(A) Same as integer 0
(B) A type-safe null pointer constant introduced in C++11
(C) A macro defined in `<cstdlib>`
(D) More than one of the above
(E) None of the above

---

**Q10.** What is the size of a pointer variable on a 32-bit system?
(A) Depends on the data type it points to
(B) Always 2 bytes
(C) Always 4 bytes
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following is CORRECT about `void*` pointer?
(A) It can point to any data type
(B) It can be dereferenced directly without casting
(C) Pointer arithmetic is valid on void*
(D) More than one of the above
(E) None of the above

---

**Q12.** What is a wild pointer in C++?
(A) A pointer that points to freed memory
(B) A pointer that is declared but never initialized
(C) A pointer that stores address 0
(D) More than one of the above
(E) None of the above

---

**Q13.** Consider: `int* p = new int; free(p);` — what is wrong?
(A) `new` should be paired with `delete`, not `free`
(B) `free` is not available in C++
(C) `p` should be cast to `void*` first
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following pointer arithmetic operations is INVALID?
(A) `p++`
(B) `p + 3`
(C) `p1 + p2` (adding two pointers)
(D) More than one of the above
(E) None of the above

---

**Q15.** `int* p, q;` — which of the following is TRUE?
(A) Both p and q are pointers to int
(B) p is a pointer to int; q is a plain integer
(C) q is a pointer to int; p is a plain integer
(D) More than one of the above
(E) None of the above

---

**Q16.** After `int* p = new int(5); delete p; p = nullptr;` — what is the state of p?
(A) p is a dangling pointer
(B) p is a null pointer (safe state)
(C) p still holds the old address
(D) More than one of the above
(E) None of the above

---

**Q17.** What does `new` operator throw when memory allocation fails?
(A) Returns NULL
(B) Returns 0
(C) Throws `std::bad_alloc` exception
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following is TRUE about pointer arithmetic?
(A) `p + 1` advances the pointer by 1 byte always
(B) `p + 1` advances by `sizeof(type)` bytes
(C) `p * 2` is a valid pointer operation
(D) More than one of the above
(E) None of the above

---

**Q19.** Given `int** pp;` — pp is:
(A) A pointer to a pointer to int
(B) A double integer
(C) Invalid syntax in C++
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following creates a memory leak?
(A) `int* p = new int(5); delete p;`
(B) `int* p = new int(5);` (no delete ever called)
(C) `int* p = nullptr; delete p;`
(D) More than one of the above
(E) None of the above

---

**Q21.** What is the output of: `int x=5; int* p=&x; *p=20; cout << x;`
(A) 5
(B) Address of x
(C) 20
(D) More than one of the above
(E) None of the above

---

**Q22.** The `malloc()` function returns which type of pointer?
(A) `int*`
(B) `void*`
(C) `char*`
(D) More than one of the above
(E) None of the above

---

**Q23.** A pointer and the variable it points to are related through:
(A) Same memory address
(B) Pointer stores the address of the variable
(C) They always have the same value
(D) More than one of the above
(E) None of the above

---

**Q24.** Which header is needed for `malloc()` in C++?
(A) `<iostream>`
(B) `<cstdlib>`
(C) `<memory>`
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider `int arr[3]={1,2,3}; int* p=arr; cout << *(p+2);` — output is:
(A) 1
(B) 2
(C) 3
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Champaran Satyagraha 1917

---

**Q26.** The Champaran Satyagraha of 1917 was related to which issue?
(A) Salt tax by the British government
(B) Forced indigo cultivation under the Tinkathia system
(C) Demand for complete independence (Poorna Swaraj)
(D) More than one of the above
(E) None of the above

---

**Q27.** Who persuaded Mahatma Gandhi to visit Champaran?
(A) Rajendra Prasad
(B) Brij Kishore Prasad
(C) Raj Kumar Shukla
(D) More than one of the above
(E) None of the above

---

**Q28.** The Tinkathia system required farmers to grow indigo on what fraction of their land?
(A) 1/5 of land
(B) 3/20 of land (3 katha per bigha)
(C) 1/2 of land
(D) More than one of the above
(E) None of the above

---

**Q29.** When did Gandhi arrive at Motihari, Champaran to begin the Satyagraha?
(A) April 15, 1916
(B) April 15, 1917
(C) December 15, 1917
(D) More than one of the above
(E) None of the above

---

**Q30.** What was Gandhi's response when the District Magistrate ordered him to leave Champaran?
(A) He immediately left and filed a petition
(B) He refused to leave and accepted legal consequences
(C) He organized a violent protest
(D) More than one of the above
(E) None of the above

---

**Q31.** The Champaran Satyagraha is significant because it was:
(A) Gandhi's first Satyagraha in South Africa
(B) Gandhi's first Satyagraha in India
(C) The movement that led to India's independence directly
(D) More than one of the above
(E) None of the above

---

**Q32.** Which of the following leaders assisted Gandhi during the Champaran Satyagraha?
(A) Rajendra Prasad
(B) J.B. Kripalani
(C) Brij Kishore Prasad
(D) More than one of the above
(E) None of the above

---

**Q33.** The Champaran Agrarian Act was passed in:
(A) 1917
(B) 1918
(C) 1920
(D) More than one of the above
(E) None of the above

---

**Q34.** What was the outcome of the Champaran Agrarian Act, 1918?
(A) Complete independence for Champaran farmers
(B) Abolition of Tinkathia system and partial refund to farmers
(C) Transfer of indigo plantations to farmers
(D) More than one of the above
(E) None of the above

---

**Q35.** Motihari, where Gandhi was summoned to court, is the headquarters of which district?
(A) West Champaran
(B) East Champaran
(C) Vaishali
(D) More than one of the above
(E) None of the above

---

**Q36.** Who received Gandhi when he arrived at Patna before going to Champaran?
(A) Raj Kumar Shukla
(B) Rajendra Prasad
(C) Brij Kishore Prasad
(D) More than one of the above
(E) None of the above

---

**Q37.** Raj Kumar Shukla first met Gandhi at which Congress session?
(A) Bombay session, 1915
(B) Lucknow session, 1916
(C) Lahore session, 1929
(D) More than one of the above
(E) None of the above

---

**Q38.** Which title was given to Gandhi, often associated with the Champaran period?
(A) Bapu
(B) Netaji
(C) Mahatma
(D) More than one of the above
(E) None of the above

---

**Q39.** Who is said to have given Gandhi the title "Mahatma"?
(A) Rajendra Prasad
(B) Jawaharlal Nehru
(C) Rabindranath Tagore
(D) More than one of the above
(E) None of the above

---

**Q40.** The name "Champaran" is derived from:
(A) Sanskrit: "champa" (flower) + "aranya" (forest)
(B) Persian words meaning "land of indigo"
(C) A British administrative name
(D) More than one of the above
(E) None of the above

---

**Q41.** Which of the following correctly distinguishes Champaran (1917) from Kheda (1918)?
(A) Champaran was about forced indigo farming; Kheda was about land revenue during crop failure
(B) Both movements were about indigo cultivation
(C) Champaran was in Gujarat; Kheda was in Bihar
(D) More than one of the above
(E) None of the above

---

**Q42.** The Champaran movement strengthened Gandhi's position as a national leader because:
(A) He first successfully defied a government order in India
(B) It demonstrated Satyagraha could work against economic exploitation
(C) It connected Gandhi directly with rural Indian masses
(D) More than one of the above
(E) None of the above

---

**Q43.** Who was the Viceroy of India during the Champaran Satyagraha of 1917?
(A) Lord Curzon
(B) Lord Chelmsford
(C) Lord Irwin
(D) More than one of the above
(E) None of the above

---

**Q44.** The refund given to farmers under the Champaran settlement was approximately:
(A) 50% of illegal collections
(B) 100% refund
(C) 25% of illegal exactions
(D) More than one of the above
(E) None of the above

---

**Q45.** Gandhi's method at Champaran included:
(A) Armed resistance against British planters
(B) Systematic investigation, documentation, and non-violent civil disobedience
(C) A call for immediate boycott of British goods
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following is TRUE about Champaran today?
(A) It is a single undivided district
(B) It is divided into East Champaran (Motihari) and West Champaran (Bettiah)
(C) It is part of Uttar Pradesh
(D) More than one of the above
(E) None of the above

---

**Q47.** Rajendra Prasad's association with Champaran Satyagraha is significant because:
(A) He later became India's first Prime Minister
(B) He later became India's first President — a son of Bihar
(C) He was the one who originally started the movement
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following CHRONOLOGICAL order is CORRECT?
1. Champaran Satyagraha
2. Non-Cooperation Movement
3. Gandhi returns to India
4. Ahmedabad Mill Strike

(A) 3 → 1 → 4 → 2
(B) 1 → 3 → 4 → 2
(C) 3 → 4 → 1 → 2
(D) More than one of the above
(E) None of the above

---

**Q49.** Match the following:
```
Movement            Location
1. Champaran        A. Gujarat (Kheda district)
2. Kheda            B. Bihar
3. Ahmedabad        C. Gujarat (city)
```
(A) 1-B, 2-A, 3-C
(B) 1-A, 2-B, 3-C
(C) 1-C, 2-A, 3-B
(D) More than one of the above
(E) None of the above

---

**Q50.** The Champaran Satyagraha is remembered in Bihar as a landmark event primarily because:
(A) It was the only movement that succeeded under Gandhi
(B) It marked the first time Gandhi led a movement on Indian soil and achieved success for Bihar's farmers
(C) It led directly to Indian Independence
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
| 1 | (B) | `int* p;` is the correct pointer declaration syntax |
| 2 | (C) | `*p` dereferences — gives value of x = 10 |
| 3 | (C) | Deleting NULL pointer is safe no-op in C++ |
| 4 | (A) | new calls constructor; malloc does not |
| 5 | (B) | `new int[5]` allocates array of 5 ints |
| 6 | (C) | `delete[]` pairs with `new[]` |
| 7 | (B) | Dangling = points to freed/out-of-scope memory |
| 8 | (B) | p++ moves to arr[1] whose value is 20 |
| 9 | (B) | nullptr is type-safe null pointer from C++11 |
| 10 | (C) | All pointers = 4 bytes on 32-bit system |
| 11 | (A) | void* can point to any type, but cannot dereference directly |
| 12 | (B) | Wild pointer = declared but never initialized |
| 13 | (A) | new must pair with delete, not free |
| 14 | (C) | Adding two pointers together is invalid |
| 15 | (B) | `int* p, q` — only p is pointer; q is int |
| 16 | (B) | After `p = nullptr`, p is a safe null pointer |
| 17 | (C) | new throws std::bad_alloc on failure |
| 18 | (B) | p+1 advances by sizeof(type) bytes |
| 19 | (A) | `int**` is pointer to pointer to int |
| 20 | (B) | Allocating with new but never deleting = memory leak |
| 21 | (C) | `*p = 20` changes x through pointer; cout << x = 20 |
| 22 | (B) | malloc returns void* |
| 23 | (B) | Pointer stores the address of the variable |
| 24 | (B) | malloc is in `<cstdlib>` |
| 25 | (C) | *(p+2) = arr[2] = 3 |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Tinkathia system — forced indigo cultivation |
| 27 | (C) | Raj Kumar Shukla — the indigo farmer catalyst |
| 28 | (B) | 3 katha per bigha = 3/20 of land |
| 29 | (B) | April 15, 1917 |
| 30 | (B) | Gandhi refused to leave — first civil disobedience in India |
| 31 | (B) | First Satyagraha in India (had done it earlier in South Africa) |
| 32 | (D) | All three: Rajendra Prasad, Kripalani, Brij Kishore Prasad |
| 33 | (B) | Champaran Agrarian Act — 1918 |
| 34 | (B) | Tinkathia abolished + 25% refund |
| 35 | (B) | Motihari = headquarters of East Champaran |
| 36 | (B) | Rajendra Prasad received Gandhi in Patna |
| 37 | (B) | Lucknow Congress session, 1916 |
| 38 | (D) | Both "Bapu" and "Mahatma" are titles for Gandhi |
| 39 | (C) | Rabindranath Tagore gave Gandhi the title "Mahatma" |
| 40 | (A) | Champa (tree/flower) + Aranya (forest) |
| 41 | (A) | Champaran = indigo; Kheda = revenue during crop failure |
| 42 | (D) | All three reasons are correct |
| 43 | (B) | Lord Chelmsford was Viceroy in 1917 |
| 44 | (C) | 25% refund of illegal exactions |
| 45 | (B) | Investigation + documentation + non-violent disobedience |
| 46 | (B) | East Champaran (Motihari) + West Champaran (Bettiah) |
| 47 | (B) | Rajendra Prasad became India's first President |
| 48 | (A) | Gandhi returns 1915 → Champaran 1917 → Ahmedabad 1918 → NCM 1920 |
| 49 | (A) | Champaran-Bihar, Kheda-Gujarat, Ahmedabad-Gujarat city |
| 50 | (B) | First successful Gandhian Satyagraha on Indian soil — Bihar's pride |

---
---

# 🔁 DAY 9 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — C++ Pointers

### Core Concepts — One-Liners:
1. **Pointer** = variable storing address of another variable
2. **`&x`** = address-of x | **`*p`** = value at address stored in p
3. **`int* p, q`** = p is pointer, q is plain int — TRAP!
4. **`delete NULL`** = safe, does nothing, no crash — **#1 PYQ trap**
5. **`new`** calls constructor; **`malloc`** does NOT
6. **`new`** pairs with **`delete`** | **`new[]`** pairs with **`delete[]`** — never mix!
7. **Dangling pointer** = points to freed memory (use `p = nullptr` after delete)
8. **Wild pointer** = uninitialized pointer (never assigned any address)
9. **sizeof(any pointer)** = 4 bytes (32-bit) or 8 bytes (64-bit) — independent of type
10. **`p + 1`** moves by `sizeof(type)` bytes, NOT 1 byte
11. **`p1 + p2`** = INVALID (cannot add two pointers)
12. **`void*`** = generic pointer, cannot dereference without cast
13. **`new` fails** → throws `std::bad_alloc` | **`malloc` fails** → returns NULL
14. **Memory leak** = allocating with `new` but never calling `delete`
15. **`nullptr`** = C++11 type-safe null | **`NULL`** = old C-style integer 0

### Quick Formula Table:
```
Operation          Result
─────────────────────────────────────────────
int* p = &x        p holds address of x
*p                 value of x (through pointer)
p++                moves to next int (4 bytes ahead)
p + n              address of n-th element ahead
p1 - p2            number of elements between p1 and p2
sizeof(p)          4 bytes (32-bit) / 8 bytes (64-bit)
delete NULL        safe, no-op ← EXAM TRAP
new int[5]         allocate 5 ints on heap
delete[] arr       correct way to free array
```

---

## ⚡ RAPID FIRE — Champaran Satyagraha

### Must-Know Facts:
```
Year: 1917
Place: Motihari, Champaran, Bihar
Issue: Tinkathia System (forced indigo on 3/20 land)
Catalyst: Raj Kumar Shukla (indigo farmer)
Gandhi arrived: April 15, 1917
First action: Refused to leave when ordered → first civil disobedience in India
Key team: Rajendra Prasad, Brij Kishore Prasad, J.B. Kripalani, Mazhar-ul-Haq
Result: Champaran Agrarian Act 1918 — Tinkathia abolished, 25% refund
Significance: Gandhi's FIRST Satyagraha IN INDIA
Title: Tagore gave Gandhi title "Mahatma"
```

### Bihar-Specific — Never Forget:
```
→ Champaran is in Bihar (East + West Champaran districts today)
→ Raj Kumar Shukla = Champaran indigo farmer who brought Gandhi
→ Rajendra Prasad (Siwan, Bihar) = helped Gandhi → became India's 1st President
→ Motihari = East Champaran HQ = where Gandhi was summoned to court
→ Highest BPSC probability facts!
```

### Common Exam Traps:
1. Champaran 1917 ≠ Kheda 1918 ≠ Ahmedabad 1918 — three different movements
2. Gandhi's FIRST Satyagraha = South Africa (earlier) | FIRST IN INDIA = Champaran
3. Tinkathia = forced cultivation, NOT a tax
4. Champaran Agrarian Act = 1918, NOT 1917 (movement 1917, act 1918)
5. Raj Kumar Shukla met Gandhi at LUCKNOW session (1916), not Bombay
6. Rajendra Prasad helped in Champaran → later became PRESIDENT (not PM — Nehru was PM)

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. `delete NULL` is always safe in C++ — it's a no-operation with no error
2. `new` calls constructor; `malloc` does NOT — pair `new` with `delete`, `malloc` with `free`
3. Dangling pointer = freed memory still being pointed to; fix with `p = nullptr` after delete
4. Champaran 1917 — Raj Kumar Shukla brought Gandhi; first Satyagraha in India
5. Tinkathia system abolished by Champaran Agrarian Act 1918; 25% refund to farmers

---

*Next: Day 10 — Arrays in C++ + Non-Cooperation Movement 1920*
