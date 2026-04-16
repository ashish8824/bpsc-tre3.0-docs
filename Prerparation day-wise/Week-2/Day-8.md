# 📅 BPSC TRE 4.0 — DAY 8 COMPLETE STUDY MODULE
### C++ Basics: Variables, Data Types, Naming Rules + Modern Indian History — Overview
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): C++ Variables, Data Types, Naming Rules, sizeof, Scope, Header Files
> - Afternoon (1 hr): Modern Indian History — Overview
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 C++ Basics — Variables, Data Types, Naming Rules

---

## 🔷 SECTION 1: What is a Variable?

### Real-Life Analogy:
Think of a variable as a **labelled storage box**.
- The **label** is the variable name (e.g., `age`)
- The **box size** depends on the data type (e.g., int = 4 bytes)
- The **content** is the value stored (e.g., 25)

```
Variable Declaration in C++:
┌─────────────────────────────────────┐
│  data_type  variable_name = value;  │
│  int        age           = 25;     │
└─────────────────────────────────────┘
```

### Memory Visualization:
```
Memory Address:  1000   1001   1002   1003
                ┌──────────────────────────┐
int age = 25:   │  0  │  0  │  0  │  25  │  ← 4 bytes for int
                └──────────────────────────┘
                       variable name "age" points here
```

---

## 🔷 SECTION 2: Variable Naming Rules (EXAM GOLDMINE)

### ✅ VALID Naming Rules:
```
Rule 1: Can use letters (A-Z, a-z), digits (0-9), underscore (_)
Rule 2: MUST start with a letter OR underscore (_)
Rule 3: CANNOT start with a digit
Rule 4: NO spaces allowed
Rule 5: NO special characters except underscore (_)
Rule 6: Case-sensitive: 'Age' ≠ 'age' ≠ 'AGE'
Rule 7: Cannot use C++ reserved/keywords
Rule 8: No length limit (practically), but keep reasonable
```

### 📊 VALID vs INVALID — Master Table:

| Variable Name | Valid/Invalid | Reason |
|---------------|---------------|--------|
| `age` | ✅ VALID | Letters only |
| `_age` | ✅ VALID | Starts with underscore |
| `age_1` | ✅ VALID | Letters + digit + underscore |
| `Age` | ✅ VALID | Case-sensitive, but valid |
| `_123` | ✅ VALID | Starts with underscore |
| `__score` | ✅ VALID | Multiple underscores allowed |
| `MAX_SIZE` | ✅ VALID | All caps + underscore |
| `123age` | ❌ INVALID | Starts with digit |
| `123Variable` | ❌ INVALID | Starts with digit ← **PYQ TRAP** |
| `my age` | ❌ INVALID | Contains space |
| `my-age` | ❌ INVALID | Hyphen is not allowed |
| `int` | ❌ INVALID | Reserved keyword |
| `float` | ❌ INVALID | Reserved keyword |
| `my@var` | ❌ INVALID | @ is special character |
| `2sum` | ❌ INVALID | Starts with digit |

### 🚨 PYQ TRAP #1:
> **Q: Which of the following is a valid variable name?**
> `123abc` → INVALID (digit start)
> `_123abc` → **VALID** (underscore start)
>
> Many students confuse these. Underscore at start = VALID!

### 🚨 PYQ TRAP #2:
> **C++ is case-sensitive.**
> `int Score = 10;` and `int score = 10;` are TWO DIFFERENT variables.
> Both can exist in the same program without conflict.

### 📋 Reserved Keywords (Cannot be used as variable names):
```
int     float   double  char    bool    void
if      else    while   for     do      switch
case    break   return  class   public  private
protected new   delete  virtual struct  namespace
```

---

## 🔷 SECTION 3: Data Types in C++ (Deep Dive)

### The Big Picture:
```
DATA TYPES IN C++
├── Primitive (Built-in)
│   ├── int      → whole numbers
│   ├── float    → decimal (single precision)
│   ├── double   → decimal (double precision)
│   ├── char     → single character
│   ├── bool     → true/false
│   └── void     → no value
├── Derived
│   ├── array
│   ├── pointer
│   └── function
└── User-Defined
    ├── class
    ├── struct
    ├── union
    └── enum
```

### 📊 Master Data Types Table (Memorize This!):

| Data Type | Size (bytes) | Range | Format Specifier |
|-----------|-------------|-------|-----------------|
| `char` | 1 | -128 to 127 | %c |
| `unsigned char` | 1 | 0 to 255 | %c |
| `short int` | 2 | -32,768 to 32,767 | %hd |
| `int` | **4** | -2,147,483,648 to 2,147,483,647 | %d |
| `unsigned int` | 4 | 0 to 4,294,967,295 | %u |
| `long int` | 4 or 8 | system-dependent | %ld |
| `long long int` | **8** | very large range | %lld |
| `float` | **4** | 6–7 decimal digits precision | %f |
| `double` | **8** | 15–16 decimal digits precision | %lf |
| `long double` | 12 or 16 | platform-dependent | %Lf |
| `bool` | **1** | 0 (false) or 1 (true) | %d |
| `void` | 0 | No value | — |

### 🚨 IMPORTANT: Default sizes on most 32-bit systems:
```
char   = 1 byte
int    = 4 bytes
float  = 4 bytes
double = 8 bytes
bool   = 1 byte
```

### Deep Dive: Each Data Type

#### 1. `int` — Integer Type
```cpp
int marks = 95;      // Whole number, no decimal
int negative = -50;  // Can be negative
int zero = 0;
// Range: -2,147,483,648 to +2,147,483,647 (on 32-bit)
// Size: 4 bytes (on most systems)
```

#### 2. `float` — Single Precision Decimal
```cpp
float pi = 3.14f;         // 'f' suffix recommended for float
float temp = 36.6f;
// Precision: ~6-7 significant digits
// Size: 4 bytes
// ⚠️ Precision issue: 0.1 + 0.2 ≠ 0.3 exactly (floating point error)
```

#### 3. `double` — Double Precision Decimal
```cpp
double pi = 3.141592653589793;  // More precise
double salary = 75000.50;
// Precision: ~15-16 significant digits
// Size: 8 bytes
// PREFERRED over float when high precision needed
```

#### 4. `char` — Character Type
```cpp
char grade = 'A';        // Single character, use single quotes
char letter = 65;        // Stores ASCII value — same as 'A'
char newline = '\n';     // Escape sequences also valid
// Size: 1 byte
// Stores ASCII values internally (0–127 for basic ASCII)
```

**ASCII Table Shortcuts (Exam Important):**
```
'A' = 65,  'Z' = 90
'a' = 97,  'z' = 122
'0' = 48,  '9' = 57
```

#### 5. `bool` — Boolean Type
```cpp
bool isLoggedIn = true;
bool isEmpty = false;
// Only two values: true (1) or false (0)
// Size: 1 byte (even though only 1 bit needed — exam trap!)
// In conditions: 0 = false, any non-zero = true
```

**🚨 PYQ TRAP #3:**
> `bool` takes **1 byte**, NOT 1 bit, even though it only stores 0 or 1.
> This is a very common exam question!

#### 6. `void` — No Type
```cpp
void printHello() {     // Function returns nothing
    cout << "Hello";
}
// void* is a generic pointer (can point to any type)
// Cannot declare: void x;  ← COMPILATION ERROR
```

**🚨 PYQ TRAP #4:**
> You CANNOT declare a variable of type `void`.
> `void x = 5;` → **Compilation Error**
> But `void* ptr;` → **Valid** (void pointer)

---

## 🔷 SECTION 4: sizeof() — The Exam Trap Master

### What is sizeof()?
`sizeof()` is a **compile-time operator** (not a function!) that returns the size in bytes of a data type or variable.

### 🚨 CRITICAL RULE — Most Asked in BPSC PYQs:
```
sizeof() does NOT EVALUATE the expression inside it.
sizeof() only determines the SIZE of the TYPE.
```

### Examples:
```cpp
int a = 5;
cout << sizeof(a);      // Output: 4 (size of int)
cout << sizeof(int);    // Output: 4
cout << sizeof(char);   // Output: 1
cout << sizeof(float);  // Output: 4
cout << sizeof(double); // Output: 8
cout << sizeof(bool);   // Output: 1

// THE TRAP:
int x = 5;
cout << sizeof(x++);    // Output: 4 (size of int)
                        // x is STILL 5 after this!
                        // sizeof does NOT execute x++
```

### sizeof() Trap Visual:
```
Code: sizeof(x++)
      ↓
sizeof looks at TYPE of (x++) → int
sizeof does NOT run x++
sizeof returns: 4
x remains: unchanged (still 5!)

This is the #1 BPSC TRE PYQ trap on sizeof()
```

### sizeof() with Arrays:
```cpp
int arr[5];
cout << sizeof(arr);           // Output: 20 (5 × 4 bytes)
cout << sizeof(arr)/sizeof(int); // Output: 5 (number of elements)
```

### sizeof() with Structures:
```cpp
struct Point {
    int x;   // 4 bytes
    int y;   // 4 bytes
};
cout << sizeof(Point);  // Output: 8 bytes (may vary with padding)
```

---

## 🔷 SECTION 5: Scope of Variables

### What is Scope?
**Scope** = the region of a program where a variable is accessible (visible and usable).

### Types of Scope — Diagram:
```
┌─────────────────────────────────────────────────┐
│ GLOBAL SCOPE                                    │
│ int globalVar = 100;    ← accessible everywhere │
│                                                 │
│  ┌──────────────────────────────────────────┐   │
│  │ FUNCTION SCOPE: main()                   │   │
│  │ int localVar = 10;  ← only inside main() │   │
│  │                                          │   │
│  │  ┌──────────────────────────────────┐    │   │
│  │  │ BLOCK SCOPE: if / for / while    │    │   │
│  │  │ int blockVar = 5; ← only here    │    │   │
│  │  └──────────────────────────────────┘    │   │
│  └──────────────────────────────────────────┘   │
└─────────────────────────────────────────────────┘
```

### 1. Local Variables:
```cpp
void myFunction() {
    int x = 10;   // LOCAL variable
    // x is only accessible inside myFunction()
}
// x is NOT accessible here — compile error if you try
```
- Defined inside a function or block
- Created when function is called, destroyed when function ends
- Stored in **stack memory**
- NOT automatically initialized (contains garbage value)

### 2. Global Variables:
```cpp
int count = 0;   // GLOBAL variable — defined outside all functions

void increment() {
    count++;     // Accessible here ✅
}

int main() {
    count = 5;   // Accessible here ✅
    return 0;
}
```
- Defined outside all functions
- Accessible throughout the entire program
- **Automatically initialized to 0** (for numeric types)
- Stored in **data segment** memory

### 🚨 PYQ TRAP #5: Local vs Global Conflict
```cpp
int x = 100;    // Global x

void demo() {
    int x = 50; // Local x — shadows global x
    cout << x;  // Prints: 50 (local takes priority)
    cout << ::x; // Prints: 100 (:: is scope resolution operator → global)
}
```
> **Scope Resolution Operator `::` accesses the global variable when a local variable has the same name.**

### 3. Block Scope:
```cpp
int main() {
    if (true) {
        int temp = 42;   // Block scope variable
        cout << temp;    // ✅ Works here
    }
    // cout << temp;     // ❌ ERROR — temp is out of scope
    return 0;
}
```

### 🚨 PYQ TRAP #6: Loop variable scope
```cpp
for (int i = 0; i < 5; i++) {
    // i is accessible here
}
// cout << i;  ← ERROR in C++ (i is out of scope outside for loop)
```
In C++ (C++98 and later), `i` in for-loop is strictly local to the loop.

### 4. Function Scope (Labels):
- Labels (used with `goto`) have function scope
- Accessible anywhere within that function

### Summary Table:

| Scope Type | Where Defined | Where Accessible | Memory | Default Value |
|-----------|---------------|-----------------|--------|---------------|
| Local | Inside function/block | Only inside that block | Stack | Garbage |
| Global | Outside all functions | Entire program | Data segment | 0 / null |
| Block | Inside { } block | Only inside { } | Stack | Garbage |
| Function | Inside function (labels) | Entire function | — | — |

---

## 🔷 SECTION 6: Header Files

### What is a Header File?
A header file contains **declarations** of functions, classes, constants, and macros that can be shared across multiple source files.

### Types of Header Files:

```
HEADER FILES
├── Standard (Pre-defined) Header Files
│   ├── No .h extension in modern C++
│   ├── Example: #include <iostream>
│   ├── Surrounded by angle brackets < >
│   └── Come with the C++ standard library
│
└── User-Defined Header Files
    ├── Have .h extension
    ├── Example: #include "mymath.h"
    ├── Surrounded by double quotes " "
    └── Created by the programmer
```

### Standard Header Files — Exam Important List:

| Header File | Purpose |
|-------------|---------|
| `<iostream>` | Input/Output (cin, cout) |
| `<fstream>` | File handling (ifstream, ofstream) |
| `<string>` | String operations |
| `<cmath>` | Math functions (sqrt, pow, sin, cos) |
| `<cstdlib>` | General utilities (rand, malloc, free) |
| `<cstring>` | C-style string functions (strcpy, strlen) |
| `<vector>` | STL vector |
| `<algorithm>` | sort, find, etc. |
| `<ctime>` | Time functions |
| `<cassert>` | Assertions |

### Syntax Difference — KEY EXAM POINT:
```cpp
#include <iostream>      // Standard: angle brackets, NO .h
#include "myHeader.h"    // User-defined: double quotes, WITH .h
```

### 🚨 PYQ TRAP #7: Old C headers in C++
```
Old C-style:    #include <stdio.h>    ← C style (with .h)
Modern C++:     #include <cstdio>     ← C++ style (no .h, 'c' prefix)

Both work in C++, but modern C++ prefers the <cstdio> form.
```

### 🚨 PYQ TRAP #8:
> **User-defined header files use `.h` extension and double quotes.**
> `#include "mylib.h"` — the compiler searches the **current directory first**, then the system directories.
> `#include <iostream>` — searches **system directories only**.

### What goes in a Header File?
```
✅ Function declarations (prototypes)
✅ Class definitions
✅ Constants (#define, const)
✅ Macro definitions
✅ Inline function definitions
✅ Template definitions

❌ Function definitions (should be in .cpp file to avoid multiple definition errors)
❌ Global variable definitions (use extern declaration instead)
```

---

## 🔷 SECTION 7: Type Modifiers

These modify the behavior of basic data types:

| Modifier | Effect |
|----------|--------|
| `signed` | Can hold negative values (default for int) |
| `unsigned` | Only non-negative values; doubles the positive range |
| `short` | Reduces size (2 bytes for int) |
| `long` | Increases size |

### Example:
```cpp
unsigned int x = 300;  // Range: 0 to 4,294,967,295
short int y = 100;     // Range: -32,768 to 32,767
long long int z = 1000000000LL;  // Very large numbers
```

### 🚨 PYQ TRAP #9: unsigned overflow
```cpp
unsigned int x = 0;
x = x - 1;
// NOT -1! Wraps around to 4,294,967,295 (max unsigned int)
// This is called "unsigned integer wrap-around"
```

---

## 📊 VISUAL SUMMARY — C++ Data Types Mind Map

```
                    C++ VARIABLES
                         │
          ┌──────────────┼──────────────┐
          │              │              │
     NAMING RULES    DATA TYPES       SCOPE
          │              │              │
    ┌─────┴─────┐   ┌────┴────┐    ┌───┴───┐
  Valid      Invalid int    char  Local  Global
  _age       123age  float  bool  ↓      ↓
  myVar      my-age  double void  Stack  Data
  MAX        int     ...        Segment
                     │
                  sizeof()
                     │
              Returns SIZE only
              Does NOT evaluate
              expression inside
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Modern Indian History — Overview (Timeline-Based)

---

## 🔷 WHY THIS MATTERS FOR BPSC TRE:
- GS section has 40 questions; History typically 6–8 questions
- Modern History questions are very PYQ-heavy
- Bihar-specific events have HIGH probability of appearance

---

## 🔷 MODERN INDIAN HISTORY — ERA OVERVIEW

### Timeline Framework:
```
1600       1757      1857       1885      1905      1919      1942   1947
  │          │         │          │         │         │         │      │
East       Battle   Revolt     INC      Partition  Rowlatt  Quit   Indep-
India      of       of 1857   founded  of Bengal  Act /    India  endence
Company    Plassey  (Sepoy                         Jalian-  Move-
formed             Mutiny)                         wala     ment
                                                   Bagh
```

---

## 🔷 PERIOD 1: ARRIVAL OF EUROPEANS (1498–1757)

| Year | Event |
|------|-------|
| 1498 | Vasco da Gama reaches India (Calicut) — Portuguese |
| 1510 | Portuguese capture Goa |
| 1600 | British East India Company established |
| 1602 | Dutch East India Company established |
| 1664 | French East India Company established |
| 1690 | Calcutta founded by Job Charnock (British) |

### Key Point:
- Portuguese were the FIRST Europeans to arrive
- British East India Company was a TRADING company initially
- Surat was the FIRST factory (1612) established by British

---

## 🔷 PERIOD 2: ESTABLISHMENT OF BRITISH RULE (1757–1857)

### 2.1 Battle of Plassey — 1757 (MOST ASKED)
```
Clive (British) vs Siraj-ud-Daula (Bengal)
↓
Mir Jafar betrayed Siraj
↓
British victory — foundation of British rule in India
↓
British controlled Bengal's revenue
```
- **Mir Jafar** = traitor who helped British
- After Plassey: British got Zamindari rights in Bengal

### 2.2 Battle of Buxar — 1764
- British (Hector Munro) defeated combined forces of:
  - Mir Qasim (Bengal)
  - Shuja-ud-Daula (Awadh)
  - Shah Alam II (Mughal Emperor)
- **More significant than Plassey** — confirmed British supremacy
- Led to Treaty of Allahabad (1765)

### 🚨 PYQ TRAP: Battle of Plassey (1757) vs Buxar (1764)
> Plassey established British power; Buxar CONFIRMED it.
> Buxar involved 3 rulers; Plassey only 1.

### 2.3 Important Acts:
| Act/Regulation | Year | Significance |
|----------------|------|-------------|
| Regulating Act | 1773 | First step towards parliamentary control over Company |
| Pitt's India Act | 1784 | Dual control — Company + British government |
| Charter Act | 1813 | Ended Company's trade monopoly (except tea and China trade) |
| Charter Act | 1833 | Company's trading powers abolished; became only administrative |
| Charter Act | 1853 | Last charter act; introduced competitive exams for civil services |

---

## 🔷 PERIOD 3: THE REVOLT OF 1857

### Quick Reference:
```
Name: "Revolt of 1857" / "Sepoy Mutiny" / "First War of Independence"
Date Started: May 10, 1857 — Meerut
Trigger: Greased cartridges (pig/cow fat) in Enfield rifles
```

### Spread of Revolt — Key Centers:
| Center | Leader |
|--------|--------|
| Delhi | Bahadur Shah Zafar (last Mughal) |
| Kanpur (Cawnpore) | Nana Sahib |
| Lucknow | Begum Hazrat Mahal |
| Jhansi | Rani Laxmibai |
| Bihar / Jagdishpur | **Kunwar Singh** ← BIHAR FOCUS |
| Bareilly | Khan Bahadur Khan |

### Bihar Connection — BPSC IMPORTANT:
> **Kunwar Singh** (from Jagdishpur, Bhojpur district, Bihar) led the revolt in Bihar.
> He was 80 years old when he fought the British.
> He is a major folk hero of Bihar — very likely to appear in BPSC TRE!

### Results of 1857 Revolt:
- Company rule ended; Crown/British Parliament took over
- Governor-General became **Viceroy** (first: Lord Canning)
- Queen Victoria's Proclamation of 1858

---

## 🔷 PERIOD 4: NATIONAL MOVEMENTS (1885–1947)

### 4.1 Indian National Congress (INC) — Founded 1885
- Founder: **A.O. Hume** (British civil servant)
- First president: **W.C. Banerjee**
- First session: **Bombay, December 1885**

### 🚨 Memory Trick:
> "**A**ll **O**rganizations **H**ave **U**niqueFounders" → A.O. Hume founded INC

### 4.2 Partition of Bengal — 1905
- By Viceroy **Lord Curzon**
- Bengal divided into:
  - East Bengal + Assam (Muslim majority)
  - West Bengal (Hindu majority)
- Led to **Swadeshi Movement** and **Boycott Movement**
- Annulled in **1911** (Delhi Durbar)

### 4.3 Two Factions: Moderates vs Extremists

| Feature | Moderates | Extremists |
|---------|-----------|-----------|
| Leaders | Gopal Krishna Gokhale, Dadabhai Naoroji | Bal Gangadhar Tilak, Lala Lajpat Rai, Bipin Chandra Pal |
| Method | Prayers, petitions, appeals | Mass agitation, passive resistance |
| Goal | Self-governance within British Empire | Complete Swaraj |
| Motto | Slow reform | "Swaraj is my birthright" (Tilak) |

**Memory Trick for Extremists: "Lal-Bal-Pal"**
- **Lal** = Lala Lajpat Rai
- **Bal** = Bal Gangadhar Tilak
- **Pal** = Bipin Chandra Pal

### 4.4 Muslim League Founded — 1906
- Founded at Dhaka
- Promoted separate political identity for Muslims
- Key figure: Nawab Salimullah, Aga Khan

### 4.5 Morley-Minto Reforms — 1909
- Introduced **communal electorate** for Muslims (separate electorates)
- Very significant — sowed seeds of partition

### 4.6 Lucknow Pact — 1916
- Agreement between INC and Muslim League
- Both agreed to work together against British
- Congress accepted separate electorates for Muslims

### 4.7 Home Rule Movement — 1916
- **Bal Gangadhar Tilak**: Indian Home Rule League (Poona, April 1916)
- **Annie Besant**: Home Rule League (Madras, September 1916)
- Inspired by Irish Home Rule Movement
- Goal: Self-governance within British Empire

---

## 🔷 GANDHI ERA (1915–1947) — THE MOST TESTED PERIOD

### Gandhi's Return to India: 1915

### 4.8 Champaran Satyagraha — 1917 (BIHAR FOCUS!)
```
Location: Champaran, Bihar
Issue: Indigo plantation farmers forced under "Tinkathia system"
       (farmers had to grow indigo on 3/20 parts of their land)
Gandhi's first Satyagraha in India
Result: Champaran Agrarian Act (1918) — protection for farmers
```
> **Bihar-specific fact**: Champaran is now split into East and West Champaran districts.
> Gandhi came to Bihar at the request of **Raj Kumar Shukla** (an indigo farmer).
> **Very high probability in BPSC TRE!**

### 4.9 Kheda Satyagraha — 1918
- Location: Kheda district, Gujarat
- Issue: Crop failure, but British demanded full land revenue
- Gandhi supported farmers demanding revenue remission
- Result: British suspended revenue collection

### 4.10 Ahmedabad Mill Strike — 1918
- Gandhi's first hunger strike
- Mill workers demanded 35% wage hike
- Result: 35% increase granted

### 4.11 Rowlatt Act — 1919
- Allowed imprisonment without trial
- Gandhi called it "Black Act"
- Led to nationwide hartal (April 6, 1919)

### 4.12 Jallianwala Bagh Massacre — April 13, 1919
```
Date: April 13, 1919 (Baisakhi Day)
Location: Amritsar, Punjab
Commander: General Reginald Dyer
Victims: Hundreds killed (official 379, actual much higher)
Context: Crowd gathered to protest Rowlatt Act
Result: Led to Non-Cooperation Movement
```
> **Memory Trick**: 13 April 1919 → Today is April 13, 2026 → exactly 107 years ago!

### Rabindranath Tagore's Response:
- Tagore returned his **Knighthood** in protest

### 4.13 Non-Cooperation Movement — 1920–1922
- Launched by Gandhi at Calcutta session of INC (September 1920)
- Methods: Boycott of schools, courts, foreign goods, government jobs
- **Suspension**: After **Chauri Chaura incident** (February 5, 1922)
  - Chauri Chaura: UP village where crowd burned police station, killed 22 policemen
  - Gandhi suspended movement immediately due to violence

### 4.14 Swaraj Party — 1923
- Founded by **C.R. Das** and **Motilal Nehru**
- They disagreed with Gandhi's suspension of movement
- Goal: Enter councils and obstruct British from within

### 4.15 Simon Commission — 1927–1928
- 7-member all-British commission to review Indian constitution
- No Indian members → Indians protested
- **"Simon Go Back"** slogan
- **Lala Lajpat Rai** injured in police lathi charge during protest in Lahore
- Lala Lajpat Rai later died from injuries → called "Punjab Kesari"

### 4.16 Nehru Report — 1928
- INC's constitutional proposal
- Demanded **Dominion Status** (not full independence)
- Authored by **Motilal Nehru**

### 4.17 Lahore Session — December 1929 (VERY IMPORTANT)
```
President: Jawaharlal Nehru
Resolution: Poorna Swaraj (Complete Independence)
Date: December 31, 1929 — midnight resolution
Result: January 26, 1930 declared as "Independence Day"
        (This is why January 26 is Republic Day)
```

### 4.18 Civil Disobedience Movement & Salt March — 1930
```
Date: March 12 – April 6, 1930
Route: Sabarmati Ashram to Dandi (Gujarat coast)
Distance: 241 miles (12 days)
Purpose: To break Salt Law (British monopoly on salt)
April 6, 1930: Gandhi makes salt at Dandi → Civil Disobedience begins
```
- **Gandhi-Irwin Pact (1931)**: Truce between Gandhi and Viceroy Irwin
  - Movement suspended
  - Gandhi attended 2nd Round Table Conference

### 4.19 Round Table Conferences:
| Conference | Year | Gandhi's Participation |
|------------|------|----------------------|
| 1st RTC | 1930 | No (in jail) |
| 2nd RTC | 1931 | Yes |
| 3rd RTC | 1932 | No (in jail) |

### 4.20 Poona Pact — 1932
- Between Gandhi and B.R. Ambedkar
- Context: Communal Award gave separate electorates to Dalits
- Gandhi went on hunger strike against separate electorates for Dalits
- Result: Dalits got reserved seats within general electorate (not separate)

### 4.21 Quit India Movement — August 9, 1942
```
Date: August 9, 1942 — "August Kranti Diwas"
Venue: Bombay (Gowalia Tank Maidan)
Gandhi's call: "Do or Die" (Karo ya Maro)
Leaders arrested: Gandhi, Nehru, Patel — all imprisoned immediately
Underground leaders: Aruna Asaf Ali (hoisted INC flag at Gowalia Tank)
JP (Jayaprakash Narayan) led underground movement
Bihar's role: VERY strong participation — Hazaribagh jail break by JP
```

> **Bihar Connection**: JP (Jayaprakash Narayan) escaped Hazaribagh Central Jail on November 9, 1942 during Quit India Movement. **High BPSC probability!**

### 4.22 INA (Indian National Army) — 1942
- Founded by **Subhas Chandra Bose** (Netaji)
- Earlier started by **Mohan Singh** in 1942
- Bose reorganized it after "Forward Bloc" (1939)
- Azad Hind Fauj slogan: "Jai Hind", "Dilli Chalo"

### 4.23 Cabinet Mission Plan — 1946
- Three-tier federal structure proposed
- Goal: United India with some autonomy to provinces
- Both INC and Muslim League initially accepted, then disputes arose

### 4.24 Independence — 1947
```
August 15, 1947: India's Independence
First PM: Jawaharlal Nehru
First President: Dr. Rajendra Prasad (Bihar's own!)
First Governor-General: Lord Mountbatten
First Indian Governor-General: C. Rajagopalachari (Chakravarti Rajagopalachari)
```

> **Bihar Connection**: **Dr. Rajendra Prasad** — first President of India — was from **Zeradei, Siwan, Bihar**.
> He presided over the Constituent Assembly that drafted the Constitution.
> **Extremely high BPSC probability!**

---

## 🔷 KEY ACTS & THEIR SIGNIFICANCE — MASTER TABLE:

| Act/Event | Year | Key Point |
|-----------|------|-----------|
| Regulating Act | 1773 | First parliamentary oversight |
| Pitt's India Act | 1784 | Board of Control established |
| Government of India Act | 1858 | Company rule ended, Crown took over |
| Indian Councils Act | 1861 | Indians nominated to councils |
| Indian Councils Act | 1892 | Limited elections introduced |
| Morley-Minto Reforms | 1909 | Separate communal electorates |
| Montagu-Chelmsford Reforms | 1919 | Dyarchy introduced |
| Government of India Act | 1935 | Provincial autonomy; All-India federation |
| Indian Independence Act | 1947 | Independence + Partition |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Naming Rules, Data Types, sizeof(), Scope, Header Files

---

**Q1.** Which of the following is a VALID variable name in C++?
(A) `123abc`
(B) `my-var`
(C) `_myVar`
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following variable names is INVALID in C++?
(A) `_123`
(B) `value_1`
(C) `MAX_SIZE`
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the size of `int` data type on a typical 32-bit system in C++?
(A) 1 byte
(B) 2 bytes
(C) 4 bytes
(D) More than one of the above
(E) None of the above

---

**Q4.** Consider: `int x = 5; cout << sizeof(x++);` What is the output?
(A) 5
(B) 6
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q5.** After executing `int x = 5; sizeof(x++);`, what is the value of `x`?
(A) 6
(B) 5
(C) Undefined behavior
(D) More than one of the above
(E) None of the above

---

**Q6.** Which header file is used for input/output operations in C++?
(A) `<stdio.h>`
(B) `<iostream>`
(C) `<fstream>`
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following correctly includes a user-defined header file?
(A) `#include <myheader.h>`
(B) `#include "myheader.h"`
(C) `#include myheader.h`
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the size of `bool` data type in C++?
(A) 1 bit
(B) 1 byte
(C) 4 bytes
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following CANNOT be used as a variable name in C++?
(A) `_int`
(B) `Int`
(C) `int`
(D) More than one of the above
(E) None of the above

---

**Q10.** What is the output of `cout << sizeof(double);` on a typical system?
(A) 4
(B) 6
(C) 8
(D) More than one of the above
(E) None of the above

---

**Q11.** A global variable in C++ is automatically initialized to:
(A) Garbage value
(B) -1
(C) 0 (for numeric types)
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following statements about `void` is correct?
(A) You can declare a `void` variable
(B) `void*` is a valid pointer type
(C) void function must return an int
(D) More than one of the above
(E) None of the above

---

**Q13.** In C++, `char` can store which of the following?
(A) A single character
(B) An ASCII value (integer)
(C) An escape sequence like `'\n'`
(D) More than one of the above
(E) None of the above

---

**Q14.** Which operator is used to access a global variable when a local variable has the same name?
(A) `.` (dot operator)
(B) `->` (arrow operator)
(C) `::` (scope resolution operator)
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the range of `unsigned char` in C++?
(A) -128 to 127
(B) 0 to 255
(C) -256 to 255
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following is TRUE about `sizeof()`?
(A) It is a function
(B) It evaluates the expression inside and returns result
(C) It is a compile-time operator
(D) More than one of the above
(E) None of the above

---

**Q17.** What is the difference between `float` and `double` in C++?
(A) float is 4 bytes; double is 8 bytes
(B) float has less precision than double
(C) double is the default floating point type
(D) More than one of the above
(E) None of the above

---

**Q18.** A variable declared inside a `for` loop in C++ is accessible:
(A) Throughout the entire function
(B) Only within that for loop
(C) Globally, once the loop runs once
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is a valid declaration in C++?
(A) `void x = 10;`
(B) `void* ptr;`
(C) `void func;`
(D) More than one of the above
(E) None of the above

---

**Q20.** `sizeof(int arr[5]) / sizeof(int)` gives:
(A) 4
(B) 5
(C) 20
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following is correct about variable naming in C++?
(A) Variable names are case-insensitive
(B) `score` and `Score` are different variables
(C) Variable names can start with a digit
(D) More than one of the above
(E) None of the above

---

**Q22.** Which standard header file is used for mathematical functions like `sqrt()` in C++?
(A) `<math.h>` only
(B) `<cmath>`
(C) `<algorithm>`
(D) More than one of the above
(E) None of the above

---

**Q23.** What happens when you declare a local variable with the same name as a global variable?
(A) Compilation error
(B) Both variables coexist; local takes priority inside its scope
(C) Global variable is deleted
(D) More than one of the above
(E) None of the above

---

**Q24.** The ASCII value of character `'A'` is:
(A) 97
(B) 65
(C) 48
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following data types can store the value `true` or `false` in C++?
(A) `int`
(B) `bool`
(C) `char`
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Modern Indian History — Overview

---

**Q26.** Who founded the Indian National Congress in 1885?
(A) Bal Gangadhar Tilak
(B) Dadabhai Naoroji
(C) A.O. Hume
(D) More than one of the above
(E) None of the above

---

**Q27.** The Battle of Plassey was fought in:
(A) 1764
(B) 1757
(C) 1775
(D) More than one of the above
(E) None of the above

---

**Q28.** Who was the British commander who won the Battle of Buxar (1764)?
(A) Robert Clive
(B) Hector Munro
(C) Lord Dalhousie
(D) More than one of the above
(E) None of the above

---

**Q29.** The Jallianwala Bagh massacre occurred on:
(A) August 9, 1942
(B) March 12, 1930
(C) April 13, 1919
(D) More than one of the above
(E) None of the above

---

**Q30.** Which freedom fighter is known for leading the revolt of 1857 in Bihar?
(A) Mangal Pandey
(B) Nana Sahib
(C) Kunwar Singh
(D) More than one of the above
(E) None of the above

---

**Q31.** The slogan "Swaraj is my birthright and I shall have it" was given by:
(A) Mahatma Gandhi
(B) Lala Lajpat Rai
(C) Bal Gangadhar Tilak
(D) More than one of the above
(E) None of the above

---

**Q32.** The Champaran Satyagraha (1917) was related to which issue?
(A) Salt tax
(B) Forced indigo cultivation under Tinkathia system
(C) Communal representation
(D) More than one of the above
(E) None of the above

---

**Q33.** The Non-Cooperation Movement was suspended due to:
(A) Gandhi's arrest
(B) Chauri Chaura incident
(C) Partition of Bengal
(D) More than one of the above
(E) None of the above

---

**Q34.** Who was the first President of the Indian National Congress?
(A) A.O. Hume
(B) Dadabhai Naoroji
(C) W.C. Banerjee
(D) More than one of the above
(E) None of the above

---

**Q35.** Which Viceroy was responsible for the Partition of Bengal in 1905?
(A) Lord Mountbatten
(B) Lord Curzon
(C) Lord Dalhousie
(D) More than one of the above
(E) None of the above

---

**Q36.** The Lahore Session of INC (1929) was presided over by:
(A) Mahatma Gandhi
(B) Motilal Nehru
(C) Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q37.** The Dandi March covered a distance of approximately:
(A) 100 miles
(B) 200 miles
(C) 241 miles
(D) More than one of the above
(E) None of the above

---

**Q38.** Who gave the call "Do or Die" during the Quit India Movement?
(A) Subhas Chandra Bose
(B) Jawaharlal Nehru
(C) Mahatma Gandhi
(D) More than one of the above
(E) None of the above

---

**Q39.** The Regulating Act of 1773 was significant because:
(A) It ended East India Company's rule
(B) It was the first step toward parliamentary control of Company
(C) It introduced communal electorates
(D) More than one of the above
(E) None of the above

---

**Q40.** Who among the following is associated with the "Lal-Bal-Pal" trio?
(A) Lala Lajpat Rai, Bal Gangadhar Tilak, Bipin Chandra Pal
(B) Lal Bahadur Shastri, Bal Thackeray, Palaniswami
(C) Leaders of Moderate faction
(D) More than one of the above
(E) None of the above

---

**Q41.** The Poona Pact (1932) was an agreement between:
(A) Gandhi and Lord Irwin
(B) Gandhi and B.R. Ambedkar
(C) Congress and Muslim League
(D) More than one of the above
(E) None of the above

---

**Q42.** Arrange the following events in CHRONOLOGICAL ORDER:
1. Quit India Movement
2. Civil Disobedience Movement
3. Non-Cooperation Movement
4. Partition of Bengal

(A) 4 → 3 → 2 → 1
(B) 3 → 4 → 2 → 1
(C) 4 → 2 → 3 → 1
(D) More than one of the above
(E) None of the above

---

**Q43.** The first session of INC was held in:
(A) Calcutta
(B) Lahore
(C) Bombay
(D) More than one of the above
(E) None of the above

---

**Q44.** Which act introduced the concept of "Dyarchy" in Indian provinces?
(A) Morley-Minto Reforms, 1909
(B) Montagu-Chelmsford Reforms, 1919
(C) Government of India Act, 1935
(D) More than one of the above
(E) None of the above

---

**Q45.** Who invited Gandhi to Bihar for the Champaran Satyagraha?
(A) Rajendra Prasad
(B) Raj Kumar Shukla
(C) Brij Kishore Prasad
(D) More than one of the above
(E) None of the above

---

**Q46.** Vasco da Gama arrived in India at which port?
(A) Mumbai
(B) Surat
(C) Calicut (Kozhikode)
(D) More than one of the above
(E) None of the above

---

**Q47.** The Swaraj Party was founded in 1923 by:
(A) Bal Gangadhar Tilak and Lala Lajpat Rai
(B) C.R. Das and Motilal Nehru
(C) Gandhi and Nehru
(D) More than one of the above
(E) None of the above

---

**Q48.** Rabindranath Tagore returned his knighthood as a protest against:
(A) Partition of Bengal
(B) Rowlatt Act
(C) Jallianwala Bagh Massacre
(D) More than one of the above
(E) None of the above

---

**Q49.** Who was the first Indian Governor-General of independent India?
(A) Jawaharlal Nehru
(B) C. Rajagopalachari
(C) Lord Mountbatten
(D) More than one of the above
(E) None of the above

---

**Q50.** The first President of independent India, Dr. Rajendra Prasad, was from which district of Bihar?
(A) Patna
(B) Bhojpur
(C) Siwan
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ Note: DO NOT look at answers before attempting all 50 questions!

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (C) | _myVar starts with underscore — valid |
| 2 | (E) | All three are valid variable names |
| 3 | (C) | int = 4 bytes on 32-bit system |
| 4 | (C) | sizeof(x++) returns sizeof(int) = 4 |
| 5 | (B) | sizeof does NOT evaluate — x stays 5 |
| 6 | (D) | Both <stdio.h> (C-style) and <iostream> (C++ style) work |
| 7 | (B) | User-defined headers use double quotes |
| 8 | (B) | bool = 1 byte (NOT 1 bit!) |
| 9 | (C) | `int` is a reserved keyword |
| 10 | (C) | double = 8 bytes |
| 11 | (C) | Global numeric variables auto-initialize to 0 |
| 12 | (B) | void* (void pointer) is valid |
| 13 | (D) | char can store all three (char, ASCII int, escape sequence) |
| 14 | (C) | :: scope resolution operator |
| 15 | (B) | unsigned char: 0 to 255 |
| 16 | (C) | sizeof is a compile-time operator, not a function |
| 17 | (D) | All three statements about float vs double are true |
| 18 | (B) | for-loop variable scope is limited to the loop |
| 19 | (B) | void* ptr is valid; void x is not |
| 20 | (B) | sizeof(arr) = 20, sizeof(int) = 4; 20/4 = 5 |
| 21 | (B) | C++ is case-sensitive |
| 22 | (D) | Both <math.h> and <cmath> work in C++ |
| 23 | (B) | Local takes priority; use :: for global |
| 24 | (B) | ASCII of 'A' = 65 |
| 25 | (D) | Both bool (natively) and int (0/non-zero) store true/false |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | A.O. Hume — founder of INC |
| 27 | (B) | Battle of Plassey — 1757 |
| 28 | (B) | Hector Munro — Battle of Buxar 1764 |
| 29 | (C) | April 13, 1919 |
| 30 | (C) | Kunwar Singh — Bihar's hero of 1857 |
| 31 | (C) | Bal Gangadhar Tilak |
| 32 | (B) | Tinkathia system — forced indigo cultivation |
| 33 | (B) | Chauri Chaura incident |
| 34 | (C) | W.C. Banerjee — first INC president |
| 35 | (B) | Lord Curzon |
| 36 | (C) | Jawaharlal Nehru — Lahore 1929 |
| 37 | (C) | 241 miles / 385 km |
| 38 | (C) | Gandhi — "Do or Die" / "Karo ya Maro" |
| 39 | (B) | First step of parliamentary control |
| 40 | (A) | Lala Lajpat Rai, Tilak, Bipin Chandra Pal |
| 41 | (B) | Gandhi and Ambedkar |
| 42 | (A) | 1905 → 1920 → 1930 → 1942 |
| 43 | (C) | Bombay, December 1885 |
| 44 | (B) | Montagu-Chelmsford 1919 — Dyarchy |
| 45 | (B) | Raj Kumar Shukla — indigo farmer |
| 46 | (C) | Calicut (Kozhikode), 1498 |
| 47 | (B) | C.R. Das and Motilal Nehru |
| 48 | (C) | Jallianwala Bagh Massacre |
| 49 | (B) | C. Rajagopalachari (Chakravarti) |
| 50 | (C) | Siwan district, Bihar |

---
---

# 🔁 DAY 8 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — C++ Variables & Data Types

### Variable Naming Rules — One-Liners:
1. **Start**: Letters or underscore only — NEVER a digit
2. **Contains**: Letters, digits, underscore ONLY — no spaces, no special chars
3. **Case-sensitive**: `score` ≠ `Score` ≠ `SCORE` — three different variables
4. **Keywords forbidden**: `int`, `float`, `class` etc. cannot be variable names
5. **_underscore start**: `_age` is VALID, `123age` is INVALID

### Data Types — Size Cheat Sheet:
```
char   = 1 byte   (single character)
bool   = 1 byte   (NOT 1 bit — exam trap!)
short  = 2 bytes
int    = 4 bytes
float  = 4 bytes
double = 8 bytes
long long = 8 bytes
void   = 0 bytes (no value — cannot declare void variable)
```

### sizeof() — The #1 Exam Trap:
- sizeof() is a **compile-time OPERATOR** (not function)
- sizeof() does **NOT execute** the expression inside
- `sizeof(x++)` → returns 4 (for int), and x is **NOT incremented**
- `sizeof(arr) / sizeof(int)` → number of elements in array

### Scope — Quick Rules:
- **Local**: inside { } only, garbage default value, stack memory
- **Global**: everywhere, auto-initialized to 0, data segment memory
- **Same name**: local shadows global; use `::` to access global
- **for-loop variable**: local to loop only (C++ strict)

### Header Files — Key Rule:
- Standard: `#include <iostream>` — angle brackets, NO .h
- User-defined: `#include "myfile.h"` — double quotes, WITH .h

---

## ⚡ RAPID FIRE — Modern Indian History

### Critical Dates:
```
1498 → Vasco da Gama arrives (Calicut)
1600 → British East India Company formed
1757 → Battle of Plassey (Clive vs Siraj — Mir Jafar betrays)
1764 → Battle of Buxar (Munro vs 3 rulers — confirmed British rule)
1857 → First War of Independence (Sepoy Mutiny)
       → Bihar: Kunwar Singh led revolt (Jagdishpur, Bhojpur)
1885 → INC founded by A.O. Hume (Bombay session, W.C. Banerjee president)
1905 → Partition of Bengal (Lord Curzon) → Swadeshi Movement
1906 → Muslim League founded (Dhaka)
1909 → Morley-Minto Reforms (communal electorate begins)
1915 → Gandhi returns to India
1916 → Lucknow Pact (INC + Muslim League agreement)
1917 → Champaran Satyagraha (Bihar — Tinkathia system, Raj Kumar Shukla)
1919 → Rowlatt Act + Jallianwala Bagh (April 13)
1920 → Non-Cooperation Movement launched
1922 → NCM suspended (Chauri Chaura incident)
1929 → Lahore Session — Poorna Swaraj declared (JN presided)
1930 → Civil Disobedience + Dandi March (241 miles)
1932 → Poona Pact (Gandhi + Ambedkar)
1942 → Quit India (Aug 9) — "Do or Die" — JP escaped Hazaribagh jail
1947 → Independence — Nehru (PM), Rajendra Prasad (President — Bihar!)
```

### Bihar-Specific Facts (HIGH PROBABILITY):
1. **Champaran Satyagraha 1917** — Gandhi's first Satyagraha in India — Tinkathia system
2. **Kunwar Singh** — 1857 revolt leader — Jagdishpur, Bhojpur district
3. **JP (Jayaprakash Narayan)** — escaped Hazaribagh jail 1942 — led underground Quit India
4. **Dr. Rajendra Prasad** — first President of India — from Siwan, Bihar

### Memory Tricks:
- **Lal-Bal-Pal** = Lala Lajpat Rai + Bal Gangadhar Tilak + Bipin Chandra Pal (Extremists)
- **A.O. Hume → INC** — British civil servant who ironically founded India's nationalist party
- **Chauri Chaura → NCM Suspended** — violence ended the movement
- **April 13** = Jallianwala Bagh date (same as today's date in April!)
- **January 26** = Republic Day because 1929 Lahore session declared Jan 26 as Independence Day

### Common Exam Traps:
1. Plassey (1757) ≠ Buxar (1764) — different battles, different significance
2. INC founded by A.O. Hume (British!) — not an Indian
3. First President of INC = W.C. Banerjee ≠ A.O. Hume (founder)
4. First RTC = Gandhi NOT present (he was in jail)
5. First Indian GG ≠ First PM — C. Rajagopalachari was GG, Nehru was PM

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. sizeof() is compile-time operator; does NOT evaluate expression inside it
2. bool = 1 byte (not 1 bit); void cannot be used to declare variable
3. Variable names: start with letter/underscore only; case-sensitive; no keywords
4. Champaran 1917 → Bihar → Tinkathia system → Gandhi's first Indian Satyagraha
5. Kunwar Singh (Bihar) + Rajendra Prasad (Bihar's President) = high-priority BPSC facts

---

*Next: Day 9 — Pointers in C++ + Champaran Satyagraha (Deep Dive)*
