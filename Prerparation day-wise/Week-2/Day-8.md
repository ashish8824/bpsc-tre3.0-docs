# 📅 DAY-8 — BPSC TRE 4.0 TOPPER GUIDE
## CS: C++ Basics — Variables, Data Types, Naming Rules, sizeof(), Scope, Header Files
## GS: Modern Indian History — Overview (Freedom Struggle Essentials)

> **Topper Target:** Score 23+/25 in CS and 23+/25 in GS practice sets today.
> **Option (D) Alert:** 20–25% answers in BPSC TRE are "More than one of the above" — never skip it!

---

# ═══════════════════════════════════════════════
# 🖥️ PART 1: COMPUTER SCIENCE
## C++ Basics — Variables, Data Types, Naming, sizeof(), Scope, Header Files
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: VARIABLE NAMING RULES IN C++

### What is a Variable?
A variable is a **named memory location** that stores a value which can change during program execution.

```
Memory:
┌─────────────────────────────────────────────────┐
│  Variable name → acts as label for memory cell   │
│                                                   │
│   int age = 25;                                   │
│       ↑           ↑                               │
│    name (label)  value stored in memory           │
└─────────────────────────────────────────────────┘
```

---

### ✅ VALID Naming Rules — The "CAN DO" List

| Rule | Example |
|------|---------|
| Can start with a **letter (a-z, A-Z)** | `int age;` ✅ |
| Can start with an **underscore `_`** | `int _count;` ✅ |
| Can contain **digits (0-9)** — but NOT at start | `int age25;` ✅ |
| Can contain **underscore** anywhere | `int my_name;` ✅ |
| Can be of **any length** | `int totalNumberOfStudents;` ✅ |
| **Case sensitive** — `Age` ≠ `age` ≠ `AGE` | All three are different variables ✅ |

---

### ❌ INVALID Naming Rules — The "CANNOT DO" List

| Rule Violated | Invalid Example | Why Invalid |
|---------------|----------------|-------------|
| **Cannot start with a digit** | `123Variable` ❌ | Starts with '1' |
| **Cannot have spaces** | `my variable` ❌ | Space not allowed |
| **Cannot use special chars** (except `_`) | `my-var`, `my@var` ❌ | `-` and `@` not allowed |
| **Cannot be a keyword** | `int`, `float`, `class` ❌ | Reserved by C++ |
| **Cannot use `$` sign** | `my$var` ❌ | Not allowed in C++ |

---

### 🎯 PYQ TRAP — Most Tested Rule

```
Q: Which of the following is a VALID C++ variable name?
(A) 123Variable    ← INVALID (starts with digit)
(B) my variable    ← INVALID (has space)
(C) int            ← INVALID (keyword)
(D) _myVar         ← VALID ✅
(E) my-var         ← INVALID (hyphen not allowed)

Answer: (D)
```

**Memory Trick:** "Variables must start like names — with a letter or underscore, never a number."

---

## 📌 SECTION 2: DATA TYPES IN C++

### Primary / Fundamental Data Types

```
┌─────────────────────────────────────────────────────────────────────┐
│                    C++ DATA TYPES                                    │
│                                                                      │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐           │
│   │   int    │  │  float   │  │  double  │  │   char   │           │
│   │ 4 bytes  │  │ 4 bytes  │  │ 8 bytes  │  │ 1 byte   │           │
│   │Whole nos.│  │Decimals  │  │More prec.│  │Single chr│           │
│   └──────────┘  └──────────┘  └──────────┘  └──────────┘           │
│                                                                      │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐                          │
│   │   bool   │  │   void   │  │  wchar_t │                          │
│   │ 1 byte   │  │ 0 bytes  │  │ 2-4 bytes│                          │
│   │true/false│  │No value  │  │Wide char │                          │
│   └──────────┘  └──────────┘  └──────────┘                          │
└─────────────────────────────────────────────────────────────────────┘
```

### Data Type Size Table (Most PYQ-Tested)

| Data Type | Size (typical 32-bit) | Range | Example |
|-----------|----------------------|-------|---------|
| `int` | **4 bytes** | -2,147,483,648 to 2,147,483,647 | `int x = 5;` |
| `short int` | **2 bytes** | -32,768 to 32,767 | `short x = 100;` |
| `long int` | **4 or 8 bytes** | Larger than int | `long x = 100000L;` |
| `float` | **4 bytes** | 6-7 decimal digits precision | `float x = 3.14f;` |
| `double` | **8 bytes** | 15-16 decimal digits precision | `double x = 3.14;` |
| `char` | **1 byte** | -128 to 127 (or 0 to 255) | `char c = 'A';` |
| `bool` | **1 byte** | true or false (1 or 0) | `bool flag = true;` |
| `void` | **0 bytes** | No value | Return type only |

### Type Modifiers

| Modifier | Effect | Example |
|----------|--------|---------|
| `signed` | Can store +ve and -ve | `signed int x;` (default) |
| `unsigned` | Only +ve values, doubles range | `unsigned int x;` |
| `short` | Smaller size | `short int x;` |
| `long` | Larger size | `long int x;` |

---

### 🎯 PYQ Trick: float vs double

```
float  → 4 bytes → ~7 significant digits → single precision
double → 8 bytes → ~15 significant digits → double precision

Q: Which data type provides MORE precision?
Answer: double
```

---

## 📌 SECTION 3: `sizeof()` OPERATOR — A PYQ GOLDMINE

### What is `sizeof()`?
`sizeof()` is a **compile-time unary operator** that returns the size (in bytes) of a data type or variable.

### 🔴 CRITICAL PYQ FACT: sizeof() does NOT EVALUATE expressions!

```cpp
int x = 5;
cout << sizeof(x++);   // Output: 4 (size of int)
                       // x is STILL 5 after this line!
                       // x++ is NOT executed!
```

**Why?** Because `sizeof()` is evaluated at **compile time**, not runtime. The expression inside is never actually run.

### More Examples:

```cpp
sizeof(int)       → 4
sizeof(char)      → 1
sizeof(double)    → 8
sizeof(float)     → 4
sizeof(bool)      → 1

int arr[10];
sizeof(arr)       → 40   (10 × 4 bytes)
sizeof(arr[0])    → 4    (just one element)

// Number of elements in array:
int n = sizeof(arr) / sizeof(arr[0]);  // = 40/4 = 10
```

### PYQ-Style Question:

```
int a = 3;
int result = sizeof(a = 7 + 3);
cout << a;            // Output: 3 (NOT 10!)
cout << result;       // Output: 4 (size of int)

Explanation: sizeof() does NOT execute 'a = 7 + 3'
             a remains 3!
```

---

## 📌 SECTION 4: SCOPE OF VARIABLES

### Types of Scope

```
┌─────────────────────────────────────────────────────────────┐
│                   SCOPE OF VARIABLES                         │
│                                                              │
│  ┌──────────────────────┐   ┌──────────────────────────┐   │
│  │    LOCAL VARIABLE     │   │    GLOBAL VARIABLE        │   │
│  │                      │   │                          │   │
│  │ • Declared inside {}  │   │ • Declared outside all   │   │
│  │ • Only accessible     │   │   functions              │   │
│  │   within that block   │   │ • Accessible everywhere  │   │
│  │ • Created when block  │   │ • Default value = 0      │   │
│  │   starts              │   │ • Lives for entire       │   │
│  │ • Destroyed when      │   │   program duration       │   │
│  │   block ends          │   │                          │   │
│  └──────────────────────┘   └──────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### Code Example — Scope in Action:

```cpp
#include <iostream>
using namespace std;

int globalVar = 100;   // GLOBAL — accessible everywhere

void myFunction() {
    int localVar = 50; // LOCAL — only inside myFunction()
    cout << globalVar; // ✅ Can access global
    cout << localVar;  // ✅ Can access local
}

int main() {
    cout << globalVar; // ✅ Can access global
    // cout << localVar; // ❌ ERROR! localVar not in scope here!
    
    {
        int blockVar = 10; // Block scope variable
        cout << blockVar;  // ✅ Inside block — OK
    }
    // cout << blockVar; // ❌ ERROR! blockVar destroyed after }
    
    return 0;
}
```

### When Local and Global have SAME NAME:

```cpp
int x = 100;  // global

int main() {
    int x = 50;   // local — SHADOWS the global x
    cout << x;    // Output: 50 (local takes priority)
    cout << ::x;  // Output: 100 (:: is scope resolution operator)
    return 0;
}
```

**PYQ Trick:** `::` (scope resolution operator) is used to access the **global variable** when a local variable has the same name.

---

### Types of Storage Classes (Related to Scope):

| Storage Class | Keyword | Scope | Lifetime | Default Value |
|---------------|---------|-------|----------|---------------|
| Automatic | `auto` | Local block | Till block ends | Garbage |
| Register | `register` | Local block | Till block ends | Garbage |
| Static | `static` | Local block | Entire program | 0 |
| External | `extern` | Global | Entire program | 0 |

### Static Variable — PYQ Important:

```cpp
void counter() {
    static int count = 0;  // initialized only ONCE
    count++;
    cout << count;
}

int main() {
    counter();   // Output: 1
    counter();   // Output: 2
    counter();   // Output: 3
    // static variable retains its value between function calls!
}
```

---

## 📌 SECTION 5: HEADER FILES — PYQ IMPORTANT

### What are Header Files?
Header files contain **declarations of functions, classes, macros** that you want to use in your program.

```
┌─────────────────────────────────────────────────────────────┐
│                    HEADER FILES                              │
│                                                              │
│  Standard Library Headers        User-defined Headers        │
│  (come with compiler)            (made by programmer)        │
│                                                              │
│  #include <iostream>             #include "myfile.h"         │
│  #include <cmath>                                            │
│  #include <string>               Use DOUBLE QUOTES ""        │
│  #include <algorithm>            Use .h extension            │
│                                                              │
│  Use ANGLE BRACKETS <>                                       │
│  No .h extension needed                                      │
└─────────────────────────────────────────────────────────────┘
```

### Key Header Files and What They Contain:

| Header File | Contains | Used For |
|-------------|----------|----------|
| `<iostream>` | cin, cout, cerr | Input/Output |
| `<cmath>` | sqrt(), pow(), sin(), log() | Math functions |
| `<cstring>` | strlen(), strcpy(), strcmp() | String operations |
| `<cstdlib>` | malloc(), free(), rand(), exit() | Memory, random |
| `<algorithm>` | sort(), find(), max(), min() | Algorithms |
| `<vector>` | vector class | Dynamic arrays |
| `<fstream>` | ifstream, ofstream, fstream | File operations |

### 🎯 PYQ CRITICAL FACT:

```
User-defined header files use:
✅ .h extension          →  #include "myheader.h"
✅ Double quotes ""      →  tells compiler to search in current directory first
✅ .hpp extension also valid for C++ user headers

Standard library headers:
✅ Angle brackets < >   →  #include <iostream>
✅ No extension needed in modern C++
❌ Old style: #include <iostream.h>  (deprecated in modern C++)
```

---

## 📌 SECTION 6: TYPE CONVERSION / TYPE CASTING

### Implicit (Automatic) Type Conversion:

```cpp
int x = 5;
double y = x;   // int → double automatically
                // y = 5.0 (implicit conversion)

// Hierarchy: char < int < float < double
// Lower type is automatically promoted to higher type in expressions
```

### Explicit Type Conversion (Type Casting):

```cpp
double pi = 3.14159;
int approx = (int)pi;    // C-style cast → approx = 3 (decimal truncated!)
int approx2 = int(pi);   // Function-style cast → same result

// C++ Style Casts:
static_cast<int>(pi);    // Most common — compile-time check
```

### PYQ-Style:

```
int x = 7, y = 2;
double result = x / y;   // What is result?

Answer: 2.0  (NOT 3.5!)
Reason: Both x and y are int → integer division happens FIRST → 7/2 = 3
        Then 3 is stored as double → 3.0

To get 3.5:
double result = (double)x / y;  // Cast first, then divide
```

---

## 📌 SECTION 7: INPUT / OUTPUT IN C++

```
┌─────────────────────────────────────────────────────────────┐
│                    I/O OPERATORS                             │
│                                                              │
│   cin  >> variable    →  EXTRACTION operator >>             │
│                          Reads FROM keyboard INTO variable   │
│                                                              │
│   cout << value       →  INSERTION operator <<              │
│                          Puts value INTO output stream       │
│                                                              │
│   cerr << "error"     →  Error output (not buffered)        │
│   clog << "log"       →  Log output (buffered)              │
└─────────────────────────────────────────────────────────────┘
```

### Cascading:

```cpp
// Multiple inputs:
cin >> a >> b >> c;    // reads a, then b, then c

// Multiple outputs:
cout << "a=" << a << " b=" << b << endl;
```

### endl vs "\n":

| Feature | `endl` | `"\n"` |
|---------|--------|--------|
| Purpose | Newline + flush buffer | Newline only |
| Speed | Slower (flushes) | Faster |
| Use in exams | Both produce newline | Both produce newline |

---

## 📌 SECTION 8: FILE I/O MODES — PYQ TESTED

```cpp
#include <fstream>

// Open modes:
ios::in     → Open for reading
ios::out    → Open for writing (creates file, erases existing content)
ios::app    → Append — writes at END of file (preserves existing content)
ios::trunc  → Truncate — erases existing content (default with ios::out)
ios::binary → Binary mode
ios::ate    → Opens and moves to END of file
```

### PYQ Diagram — File Modes:

```
ios::out         ios::app          ios::in
┌──────────┐    ┌──────────┐    ┌──────────┐
│ FILE.TXT │    │ FILE.TXT │    │ FILE.TXT │
│ [erased] │    │ Hello    │    │ Hello    │
│ new data │    │ new data │    │ (read)   │
└──────────┘    └──────────┘    └──────────┘
Existing data   Data appended   Data read,
DESTROYED       at end          not modified
```

### PYQ Trick:

```
Q: Which mode preserves existing file content when writing?
Answer: ios::app (append mode)

Q: Which mode is used to read a file?
Answer: ios::in

Q: Default mode for ofstream?
Answer: ios::out (creates/overwrites file)
```

---

## 📌 SECTION 9: CONSTANTS IN C++

### Ways to Define Constants:

```cpp
// Method 1: const keyword (PREFERRED in C++)
const int MAX = 100;     // Cannot be changed after initialization
const double PI = 3.14159;

// Method 2: #define preprocessor directive (C-style)
#define MAX 100          // No type, no semicolon, text replacement

// Method 3: constexpr (C++11 — evaluated at compile time)
constexpr int SIZE = 256;
```

### Difference: const vs #define

| Feature | `const` | `#define` |
|---------|---------|-----------|
| Type checking | ✅ Has type | ❌ No type |
| Debugger visible | ✅ Yes | ❌ No |
| Scope | ✅ Block scope | ❌ File scope |
| Can be pointer | ✅ Yes | ❌ No |
| Memory | Stored in memory | Text substitution |

---

## 📌 QUICK REVISION DIAGRAM — Day 8 CS Summary

```
C++ BASICS — TOPPER MIND MAP
═══════════════════════════════════════════════════════════
                      C++ BASICS
                          │
      ┌───────────────────┼────────────────────┐
      ↓                   ↓                    ↓
  VARIABLES           DATA TYPES           SCOPE
  ─────────          ──────────          ─────────
  • Must start        • int = 4 bytes     • Local: inside {}
    with letter       • char = 1 byte     • Global: outside all
    or underscore     • float = 4 bytes   • Static: retains value
  • No spaces         • double = 8 bytes  • :: for global access
  • No special        • bool = 1 byte
    chars except _    • void = no value
  • Case sensitive
      │
      ↓
  sizeof()
  ─────────
  • Does NOT evaluate
    expressions inside
  • Compile-time op
  • sizeof(int) = 4

      ↓
  HEADER FILES
  ─────────────
  • Standard: <> angle brackets
  • User-defined: "" double quotes
  • User files use .h extension
═══════════════════════════════════════════════════════════
```

---
---
---

# ═══════════════════════════════════════════════
# 🇮🇳 PART 2: GENERAL STUDIES
## Modern Indian History — Freedom Struggle Overview
## (Bihar Focus + National Movement Key Facts)
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: THE BIG PICTURE — FREEDOM STRUGGLE TIMELINE

```
MODERN INDIAN HISTORY — KEY TIMELINE
══════════════════════════════════════════════════════════════════
1757  ← Battle of Plassey → British power begins in India
1857  ← First War of Independence (Revolt of 1857)
1885  ← Indian National Congress (INC) founded
1905  ← Partition of Bengal → Swadeshi Movement
1906  ← Muslim League founded (Dhaka)
1907  ← Surat Split — INC divides into Moderates & Extremists
1915  ← Gandhi returns to India from South Africa
1916  ← Lucknow Pact — INC + Muslim League
1917  ← Champaran Satyagraha (Gandhi's FIRST civil disobedience)
1919  ← Rowlatt Act + Jallianwala Bagh Massacre
1920  ← Non-Cooperation Movement
1922  ← Chauri Chaura → Gandhi withdraws Non-Cooperation
1923  ← Swaraj Party formed (C.R. Das + Motilal Nehru)
1927  ← Simon Commission (NO Indian member)
1929  ← Lahore Session → Purna Swaraj resolution
1930  ← Civil Disobedience Movement + Dandi March
1930  ← Round Table Conferences
1935  ← Government of India Act 1935
1940  ← August Offer; Pakistan Resolution (Lahore)
1942  ← Quit India Movement
1946  ← Cabinet Mission Plan
1947  ← Independence (Aug 15) + Partition
══════════════════════════════════════════════════════════════════
```

---

## 📌 SECTION 2: REVOLT OF 1857 — PYQ TESTED FACTS

### Key Facts about 1857 Revolt:

| Aspect | Fact |
|--------|------|
| Other names | Sepoy Mutiny (British), First War of Independence |
| Who called it "First War of Independence"? | **V.D. Savarkar** (in his book) |
| Immediate cause | Greased cartridges (pig + cow fat) — Enfield rifles |
| Started at | **Meerut** (May 10, 1857) |
| Leader at Delhi | **Bahadur Shah Zafar II** |
| Leader at Kanpur | **Nana Sahib** |
| Leader at Jhansi | **Rani Lakshmibai** |
| Leader at Lucknow | **Begum Hazrat Mahal** |
| Leader at Bihar/Arrah | **Kunwar Singh** (Jagdispur) |
| Why it failed | Lack of unified leadership; confined to North India |
| Result | End of East India Company rule → British Crown |

### Bihar in 1857:

```
Kunwar Singh
    │
    ├── Age: 80+ years during revolt (still fought!)
    ├── Place: Jagdispur, Arrah district, Bihar
    ├── Fought British and won battles
    └── Died: April 26, 1858 (after crossing river with wounded arm)
```

---

## 📌 SECTION 3: INDIAN NATIONAL CONGRESS (INC)

| Fact | Detail |
|------|--------|
| Founded | **1885** |
| Founded by | **A.O. Hume** (retired British civil servant) |
| First session | **Bombay** (December 1885) |
| First President | **W.C. Bonnerjee** (Womesh Chandra Bonnerjee) |
| "Grand Old Man of India" | **Dadabhai Naoroji** |
| First Indian President of INC | W.C. Bonnerjee |

### INC Splits — Moderates vs Extremists:

```
                    INC (before 1907)
                         │
        ┌────────────────┴─────────────────┐
        ↓                                  ↓
   MODERATES                          EXTREMISTS
   ──────────                         ──────────
   Gopal Krishna Gokhale              Bal Gangadhar Tilak
   Dadabhai Naoroji                   Bipin Chandra Pal
   M.G. Ranade                        Lala Lajpat Rai
                                      (Lal-Bal-Pal trio)
   Method: Petitions,                 Method: Mass agitation,
   prayers, memorials                 Swaraj, Swadeshi
   to British

   Surat Split (1907) → Two factions separate
```

---

## 📌 SECTION 4: GANDHI AND SATYAGRAHA MOVEMENTS

### Gandhi's Timeline in India:

| Year | Event |
|------|-------|
| 1915 | Returned from South Africa |
| 1917 | **Champaran Satyagraha** (Bihar) — First civil disobedience |
| 1918 | Kheda Satyagraha (Gujarat) — farmers' cause |
| 1919 | Rowlatt Act protest + Khilafat issue |
| 1920 | Non-Cooperation Movement |
| 1922 | Withdraws NCM after Chauri Chaura violence |
| 1930 | Civil Disobedience + **Dandi March** |
| 1942 | Quit India Movement — "Do or Die" |

---

### 🎯 CHAMPARAN SATYAGRAHA 1917 — BPSC Bihar PYQ Focus

```
╔══════════════════════════════════════════════════════════╗
║           CHAMPARAN SATYAGRAHA (1917)                    ║
║                                                          ║
║  Location: Champaran, Bihar                              ║
║  Issue: Tinkathia System — Indigo farmers forced to      ║
║         cultivate indigo on 3/20th of their land         ║
║  Gandhi's role: FIRST visit to Bihar; first              ║
║         civil disobedience in India                      ║
║  Who invited Gandhi: Rajkumar Shukla (indigo farmer)     ║
║  Key associate: Rajendra Prasad (later President)        ║
║  Result: Champaran Agrarian Act 1918 passed              ║
║         Tinkathia system abolished                       ║
╚══════════════════════════════════════════════════════════╝
```

---

## 📌 SECTION 5: KEY MOVEMENTS — DETAIL

### Non-Cooperation Movement (1920–22):

| Aspect | Detail |
|--------|--------|
| Started | September 1920 |
| Slogan | Swaraj within a year |
| Methods | Boycott of British goods, schools, courts, titles |
| Ended | February 1922 |
| Why ended | **Chauri Chaura** incident (Feb 5, 1922) — mob burned police station |
| INC Session 1922 (Gaya) | President: **Chittaranjan Das** |

### Civil Disobedience Movement (1930):

| Aspect | Detail |
|--------|--------|
| Started | March 12, 1930 |
| Famous event | **Dandi March** (Salt Satyagraha) |
| Distance | 240 miles, 24 days |
| Reached Dandi | April 6, 1930 |
| Associates | Sarojini Naidu, C. Rajagopalachari |
| Suspended | Gandhi-Irwin Pact (March 1931) |

### Quit India Movement (1942):

| Aspect | Detail |
|--------|--------|
| Started | August 8–9, 1942 |
| Resolution | Bombay session of INC |
| Slogan | **"Do or Die"** (Karo ya Maro) |
| Gandhi arrested | August 9, 1942 |
| Radio announcements | **Aruna Asaf Ali** (hoisted flag at Gowalia Tank) |
| Underground leader | **JP Narayan** (Jayaprakash Narayan) — Bihar |

---

## 📌 SECTION 6: JALLIANWALA BAGH 1919 — PYQ Tested

| Aspect | Detail |
|--------|--------|
| Date | **April 13, 1919** (Baisakhi day) |
| Location | Amritsar, Punjab |
| Responsible | General **O'Dwyer** ordered; **General Dyer** executed |
| Viceroy at the time | **Lord Chelmsford** |
| Who demanded public apology? | **Rabindranath Tagore** (returned knighthood) |
| How many killed? | ~400 officially; estimates say 1000+ |

---

## 📌 SECTION 7: KEY PERSONALITIES — QUICK REFERENCE

### National Leaders:

| Leader | Key Association |
|--------|----------------|
| Bal Gangadhar Tilak | "Swaraj is my birthright"; Home Rule League; "Lokmanya" |
| Lala Lajpat Rai | "Punjab Kesari"; died after lathi charge during Simon Commission protest |
| Bipin Chandra Pal | "Thundering Voice of India"; Extremist |
| Gopal Krishna Gokhale | Gandhi's political guru; Moderate |
| Subhas Chandra Bose | "Netaji"; INA (Indian National Army) |
| Bhagat Singh | Executed March 23, 1931; "Inquilab Zindabad" |
| V.D. Savarkar | Founded **Abhinav Bharat** (London); first called 1857 as War of Independence |

### Bihar-Specific Leaders (HIGH PRIORITY for BPSC):

| Leader | Contribution |
|--------|-------------|
| **Rajendra Prasad** | With Gandhi in Champaran; First President of India |
| **Jayaprakash Narayan (JP)** | Socialist leader; Bihar Socialist Party; Quit India underground hero |
| **Kunwar Singh** | 1857 revolt hero of Bihar (Jagdispur, Arrah) |
| **Sachindra Nath Sanyal** | Founded **Anushilan Samiti Patna** (1913) |
| **Phulan Prasad Varma** | Co-founded Bihar Socialist Party with JP |
| **Swami Sahajanand Saraswati** | Founded AIKS (All India Kisan Sabha) Bihar branch 1936 |
| **Gaya Munda** | Commander-in-Chief of Birsa Munda's army |

---

## 📌 SECTION 8: REVOLUTIONARY ORGANIZATIONS — PYQ Tested

| Organization | Founded By | Year/Place |
|-------------|-----------|------------|
| Anushilan Samiti (Patna) | **Sachindra Nath Sanyal** | **1913** |
| Abhinav Bharat | **V.D. Savarkar** | **London** |
| Ghadar Party | Lala Har Dayal | **USA (San Francisco)** |
| Hindustan Socialist Republican Association | Bhagat Singh, Chandrashekar Azad | 1928 India |
| Indian National Army (INA) | Rash Behari Bose; Subhas Chandra Bose | Singapore |

---

## 📌 SECTION 9: BIHAR PROVINCIAL CONGRESS COMMITTEE

```
Bihar Provincial Congress Committee (BPCC)
├── Founded: 1908
├── Headquarters: Patna
├── Key Leaders: Rajendra Prasad, JP Narayan, Anugrah Narayan Sinha
└── Role: Coordinated freedom struggle activities in Bihar
```

---

## 📌 SECTION 10: INC SESSIONS — BPSC PYQ Tested

| Year | Place | President | Key Event |
|------|-------|-----------|-----------|
| 1885 | Bombay | W.C. Bonnerjee | First session |
| 1907 | Surat | — | Great Split (Moderates vs Extremists) |
| 1916 | Lucknow | — | Lucknow Pact with Muslim League |
| 1920 | Nagpur | C. Vijayaraghavachariar | Non-Cooperation resolution |
| 1922 | **Gaya** | **Chittaranjan Das** | After Chauri Chaura |
| 1929 | Lahore | **Jawaharlal Nehru** | Purna Swaraj resolution |
| 1931 | Karachi | **Sardar Patel** | Fundamental Rights resolution |

---

## 📌 SECTION 11: PARTITION OF BENGAL + SWADESHI

| Aspect | Detail |
|--------|--------|
| Announced by | Lord **Curzon** |
| Date | **October 16, 1905** |
| Reason | Administrative (real: divide Hindu-Muslim Bengal) |
| Result | Mass protests → **Swadeshi Movement** |
| Annulled | **1911** (Delhi Durbar) |
| Method | Boycott of British goods; use of Indian goods (Swadeshi) |
| Who tied Rakhi (Aug 16, 1905) | **Rabindranath Tagore** — as symbol of Hindu-Muslim unity |

---

## 📌 SECTION 12: MISCELLANEOUS PYQ-READY FACTS

| Question Type | Answer |
|---------------|--------|
| First Bhojpuri film | **Ganga Maiya Tohe Piyari Chadhaibo** (1963) |
| "Vande Mataram" from which book? | **Anandamath** by Bankim Chandra Chattopadhyay |
| Sannyasi Revolt mentioned in | **Anandamath** |
| "Sare Jahan Se Accha" written by | **Allama Iqbal** |
| Indian National Anthem written by | **Rabindranath Tagore** |
| Bardoli Satyagraha led by | **Sardar Vallabhbhai Patel** |
| Home Rule Movement started by | Bal Gangadhar Tilak + Annie Besant (NOT Sarojini Naidu) |
| First woman President of INC | **Annie Besant** (1917) |
| Dandi March companion (famous woman) | **Sarojini Naidu** |
| "Father of Indian Unrest" | Bal Gangadhar Tilak (given by British Viceroy) |
| Speed of electron in hydrogen orbit | c/137 (GS Science PYQ — appears in Physics section) |

---

## 📌 GS QUICK REVISION DIAGRAM

```
MODERN INDIAN HISTORY — KEY FRAMEWORK
══════════════════════════════════════════════════════════
PHASE 1: EARLY RESISTANCE
   1857 Revolt → Kunwar Singh (Bihar) → Bahadur Shah Zafar

PHASE 2: MODERATE PHASE (1885–1905)
   INC founded → W.C. Bonnerjee → Gokhale, Naoroji
   Method: Petitions and prayers

PHASE 3: EXTREMIST + SWADESHI (1905–1919)
   Partition of Bengal (1905) → Swadeshi
   Lal-Bal-Pal → Mass agitation
   Surat Split (1907)

PHASE 4: GANDHI ERA (1915–1942)
   1917: Champaran (Bihar) ← FIRST civil disobedience
   1919: Rowlatt + Jallianwala Bagh (Viceroy: Chelmsford)
   1920: Non-Cooperation → Chauri Chaura → Withdrawn 1922
   1930: Civil Disobedience + Dandi March
   1942: Quit India → JP Narayan underground (Bihar)

PHASE 5: INDEPENDENCE (1947)
   Cabinet Mission → Mountbatten Plan → Independence Aug 15
══════════════════════════════════════════════════════════
```

---
---
---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS
# ═══════════════════════════════════════════════

> **⚠️ INSTRUCTIONS:** Solve ALL questions FIRST before looking at answers.
> Answers are given at the VERY END of this file.
> Cover the answer section while solving!

---

## 💻 CS PRACTICE QUESTIONS (Day 8) — 25 Questions
### Topic: C++ Basics — Variables, Data Types, sizeof(), Scope, Header Files

---

**Q1.** Which of the following is a valid C++ variable name?
- (A) 2myVar
- (B) my var
- (C) _count
- (D) More than one of the above
- (E) None of the above

---

**Q2.** What is the size of `double` data type in C++?
- (A) 2 bytes
- (B) 4 bytes
- (C) 8 bytes
- (D) More than one of the above
- (E) None of the above

---

**Q3.** Consider: `int x = 5; int result = sizeof(x++);`. After this statement, what is the value of `x`?
- (A) 6
- (B) 5
- (C) Undefined behavior
- (D) More than one of the above
- (E) None of the above

---

**Q4.** Which header file is required to use `sqrt()` function in C++?
- (A) `<math.h>` (C-style)
- (B) `<cmath>`
- (C) `<stdlib.h>`
- (D) More than one of the above (A and B both can be used)
- (E) None of the above

---

**Q5.** User-defined header files in C++ use which extension?
- (A) `.cpp`
- (B) `.h`
- (C) `.obj`
- (D) More than one of the above
- (E) None of the above

---

**Q6.** Which of the following are valid C++ keywords that CANNOT be used as variable names?
- (A) `int`
- (B) `class`
- (C) `return`
- (D) More than one of the above
- (E) None of the above

---

**Q7.** What will be the output of the following code?
```cpp
int a = 10;
{
    int a = 20;
    cout << a;
}
cout << a;
```
- (A) 10 10
- (B) 20 10
- (C) 20 20
- (D) More than one of the above
- (E) None of the above

---

**Q8.** What is the output of `sizeof(char)`?
- (A) 2
- (B) 4
- (C) 1
- (D) More than one of the above
- (E) None of the above

---

**Q9.** Which of the following is used to include a standard library header file in C++?
- (A) `#include "iostream"`
- (B) `#include <iostream>`
- (C) `import iostream`
- (D) More than one of the above
- (E) None of the above

---

**Q10.** What is the default value of an uninitialized **global** integer variable in C++?
- (A) Garbage value
- (B) -1
- (C) 0
- (D) More than one of the above
- (E) None of the above

---

**Q11.** Consider this code:
```cpp
void counter() {
    static int n = 0;
    n++;
    cout << n << " ";
}
int main() { counter(); counter(); counter(); }
```
What is the output?
- (A) 1 1 1
- (B) 0 1 2
- (C) 1 2 3
- (D) More than one of the above
- (E) None of the above

---

**Q12.** Which operator is used to access a global variable when a local variable has the same name?
- (A) `.` (dot operator)
- (B) `->` (arrow operator)
- (C) `::` (scope resolution operator)
- (D) More than one of the above
- (E) None of the above

---

**Q13.** Which of the following data types can hold the value `true` or `false`?
- (A) `int`
- (B) `bool`
- (C) `char`
- (D) More than one of the above
- (E) None of the above

---

**Q14.** What is the output of the following code?
```cpp
int x = 7, y = 2;
float result = x / y;
cout << result;
```
- (A) 3.5
- (B) 3
- (C) 3.0
- (D) More than one of the above
- (E) None of the above

---

**Q15.** Which of the following are characteristics of a `static` local variable?
- (A) It is initialized only once
- (B) It retains its value between function calls
- (C) Its default value is 0
- (D) More than one of the above
- (E) None of the above

---

**Q16.** What is the output size of `int arr[5]` using `sizeof(arr)`?
- (A) 5
- (B) 10
- (C) 20
- (D) More than one of the above
- (E) None of the above

---

**Q17.** Which C++ file I/O mode appends data at the end of an existing file without destroying its contents?
- (A) `ios::out`
- (B) `ios::in`
- (C) `ios::app`
- (D) More than one of the above
- (E) None of the above

---

**Q18.** Which of the following variable names is **INVALID** in C++?
- (A) `_total`
- (B) `Total_marks`
- (C) `123abc`
- (D) More than one of the above
- (E) None of the above

---

**Q19.** `sizeof()` operator in C++ is evaluated at:
- (A) Runtime
- (B) Compile time
- (C) Link time
- (D) More than one of the above
- (E) None of the above

---

**Q20.** Which of the following is the correct way to include a user-defined header file named `mylib.h`?
- (A) `#include <mylib.h>`
- (B) `#include "mylib.h"`
- (C) `#include mylib.h`
- (D) More than one of the above
- (E) None of the above

---

**Q21.** What is the output of this code?
```cpp
int a = 10;
int b = sizeof(a = 50);
cout << a << " " << b;
```
- (A) 50 4
- (B) 10 4
- (C) 10 2
- (D) More than one of the above
- (E) None of the above

---

**Q22.** Which of the following correctly declares a constant in C++?
- (A) `const int MAX = 100;`
- (B) `#define MAX 100`
- (C) `constexpr int MAX = 100;`
- (D) More than one of the above
- (E) None of the above

---

**Q23.** The `>>` operator in `cin >> x` is called:
- (A) Insertion operator
- (B) Extraction operator
- (C) Shift operator
- (D) More than one of the above
- (E) None of the above

---

**Q24.** Which of the following are true about the `void` data type?
- (A) It represents absence of a value
- (B) It is used as a return type for functions that return nothing
- (C) You cannot declare a variable of type `void`
- (D) More than one of the above
- (E) None of the above

---

**Q25.** In C++, which of the following is NOT a valid way to initialize a variable?
- (A) `int x = 5;`
- (B) `int x(5);`
- (C) `int x{5};`
- (D) More than one of the above
- (E) None of the above (All are valid)

---
---

## 🇮🇳 GS PRACTICE QUESTIONS (Day 8) — 25 Questions
### Topic: Modern Indian History — Freedom Struggle

---

**Q26.** The First War of Independence (1857) was first described as such by:
- (A) Bal Gangadhar Tilak
- (B) Mahatma Gandhi
- (C) V.D. Savarkar
- (D) More than one of the above
- (E) None of the above

---

**Q27.** Who was the first President of the Indian National Congress (INC)?
- (A) Dadabhai Naoroji
- (B) Gopal Krishna Gokhale
- (C) W.C. Bonnerjee
- (D) More than one of the above
- (E) None of the above

---

**Q28.** The Champaran Satyagraha of 1917 was related to:
- (A) Salt tax
- (B) Forced cultivation of indigo — Tinkathia system
- (C) Zamindari system
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Who invited Mahatma Gandhi to Champaran?
- (A) Rajendra Prasad
- (B) Rajkumar Shukla
- (C) JP Narayan
- (D) More than one of the above
- (E) None of the above

---

**Q30.** The Non-Cooperation Movement was withdrawn by Gandhi because of:
- (A) Dandi March
- (B) Jallianwala Bagh massacre
- (C) Chauri Chaura incident
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Who founded the Anushilan Samiti in Patna in 1913?
- (A) Bhagat Singh
- (B) Sachindra Nath Sanyal
- (C) V.D. Savarkar
- (D) More than one of the above
- (E) None of the above

---

**Q32.** The Ghadar Party was established in:
- (A) England
- (B) Canada
- (C) USA
- (D) More than one of the above
- (E) None of the above

---

**Q33.** Who was the Viceroy of India during the Jallianwala Bagh massacre (1919)?
- (A) Lord Curzon
- (B) Lord Chelmsford
- (C) Lord Mountbatten
- (D) More than one of the above
- (E) None of the above

---

**Q34.** The Abhinav Bharat society was founded by:
- (A) Lala Lajpat Rai
- (B) V.D. Savarkar
- (C) Bal Gangadhar Tilak
- (D) More than one of the above
- (E) None of the above

---

**Q35.** The INC session held at Gaya in 1922 was presided over by:
- (A) Jawaharlal Nehru
- (B) Mahatma Gandhi
- (C) Chittaranjan Das
- (D) More than one of the above
- (E) None of the above

---

**Q36.** Which of the following leaders were associated with the founding of Bihar Socialist Party?
- (A) Phulan Prasad Varma
- (B) Jayaprakash Narayan
- (C) Swami Sahajanand Saraswati
- (D) More than one of the above
- (E) None of the above

---

**Q37.** The Partition of Bengal was announced by Lord:
- (A) Wellesley
- (B) Dalhousie
- (C) Curzon
- (D) More than one of the above
- (E) None of the above

---

**Q38.** The first Bhojpuri film was:
- (A) Nadiya Ke Paar
- (B) Ganga Maiya Tohe Piyari Chadhaibo
- (C) Hum Hain Rahi Pyar Ke
- (D) More than one of the above
- (E) None of the above

---

**Q39.** The novel "Anandamath" written by Bankim Chandra Chattopadhyay mentions:
- (A) Champaran Satyagraha
- (B) Sannyasi Revolt
- (C) Quit India Movement
- (D) More than one of the above
- (E) None of the above

---

**Q40.** Who was the Commander-in-Chief of Birsa Munda's army?
- (A) Sidhu
- (B) Gaya Munda
- (C) Kanhu
- (D) More than one of the above
- (E) None of the above

---

**Q41.** The Quit India Movement (1942) was launched from:
- (A) Calcutta
- (B) Delhi
- (C) Bombay (Gowalia Tank Maidan)
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Who hoisted the Indian flag at Gowalia Tank during Quit India Movement?
- (A) Sarojini Naidu
- (B) Aruna Asaf Ali
- (C) Vijay Lakshmi Pandit
- (D) More than one of the above
- (E) None of the above

---

**Q43.** The Bihar Provincial Congress Committee was founded in:
- (A) 1905
- (B) 1908
- (C) 1915
- (D) More than one of the above
- (E) None of the above

---

**Q44.** Who was the leader of 1857 revolt in Bihar (Jagdispur)?
- (A) Mangal Pandey
- (B) Bahadur Shah Zafar
- (C) Kunwar Singh
- (D) More than one of the above
- (E) None of the above

---

**Q45.** The Dandi March (Salt Satyagraha) began on:
- (A) January 26, 1930
- (B) March 12, 1930
- (C) August 9, 1942
- (D) More than one of the above
- (E) None of the above

---

**Q46.** The "Grand Old Man of India" was:
- (A) Gopal Krishna Gokhale
- (B) W.C. Bonnerjee
- (C) Dadabhai Naoroji
- (D) More than one of the above
- (E) None of the above

---

**Q47.** The Bardoli Satyagraha was led by:
- (A) Mahatma Gandhi
- (B) Jawaharlal Nehru
- (C) Sardar Vallabhbhai Patel
- (D) More than one of the above
- (E) None of the above

---

**Q48.** Rabindranath Tagore returned his knighthood in protest against:
- (A) Partition of Bengal (1905)
- (B) Jallianwala Bagh massacre (1919)
- (C) Non-Cooperation Movement
- (D) More than one of the above
- (E) None of the above

---

**Q49.** All India Kisan Sabha Bihar branch was founded in 1936 by:
- (A) Rajendra Prasad
- (B) JP Narayan
- (C) Swami Sahajanand Saraswati
- (D) More than one of the above
- (E) None of the above

---

**Q50.** The Home Rule Movement was associated with which leaders?
- (A) Bal Gangadhar Tilak
- (B) Annie Besant
- (C) Sarojini Naidu
- (D) More than one of the above (A and B)
- (E) None of the above

---
---
---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY
# ═══════════════════════════════════════════════

> **STOP! Do not read below until you have answered ALL 50 questions!**

---

## 💻 CS ANSWERS (Q1–Q25)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q1 | **(C)** | `_count` is valid — starts with underscore. `2myVar` starts with digit (invalid). `my var` has space (invalid). |
| Q2 | **(C)** | `double` = **8 bytes** (15–16 significant digits). `float` = 4 bytes. |
| Q3 | **(B)** | `sizeof()` does NOT evaluate `x++`. x remains **5**. This is the most important PYQ fact about sizeof(). |
| Q4 | **(D)** | Both `<math.h>` (C-style) and `<cmath>` (C++ style) can be used — **more than one correct**. |
| Q5 | **(B)** | User-defined headers use `.h` extension. Standard C++ headers use no extension. |
| Q6 | **(D)** | `int`, `class`, AND `return` are ALL keywords — **more than one correct**. |
| Q7 | **(B)** | Inner block's `a` (=20) shadows outer. Prints 20, then block ends, outer `a` (=10) prints. Output: **20 10**. |
| Q8 | **(C)** | `sizeof(char)` = **1 byte** (always, by C++ standard). |
| Q9 | **(B)** | Standard headers use angle brackets: `#include <iostream>`. Double quotes are for user-defined files. |
| Q10 | **(C)** | Global variables are automatically initialized to **0** in C++. Local variables have garbage values. |
| Q11 | **(C)** | Static variable `n` retains its value. Calls: n=1, n=2, n=3. Output: **1 2 3**. |
| Q12 | **(C)** | `::` is the **scope resolution operator** used to access global variable when local has same name. |
| Q13 | **(D)** | `bool` directly stores true/false. `int` can also hold 0/1 (used as bool). In C, `char` too — **more than one** technically correct, but `bool` is the designed type. |
| Q14 | **(C)** | `x/y` = 7/2 = **3** (integer division). Stored in float → `3.0`. NOT 3.5 (that would need casting). |
| Q15 | **(D)** | Static local variables: initialized once ✅, retain value between calls ✅, default value is 0 ✅ — **ALL three are correct**. |
| Q16 | **(C)** | `sizeof(arr)` = 5 × 4 (sizeof int) = **20 bytes**. |
| Q17 | **(C)** | `ios::app` appends at end without destroying content. `ios::out` destroys existing content. |
| Q18 | **(C)** | `123abc` starts with digit — **INVALID**. `_total` and `Total_marks` are both valid. |
| Q19 | **(B)** | `sizeof()` is a **compile-time** operator — this is why it doesn't evaluate expressions. |
| Q20 | **(B)** | User-defined headers use double quotes: `#include "mylib.h"`. |
| Q21 | **(B)** | `sizeof()` does NOT execute `a = 50`. `a` remains **10**. `b` = sizeof(int) = **4**. Output: `10 4`. |
| Q22 | **(D)** | `const`, `#define`, AND `constexpr` are ALL valid ways — **more than one correct**. |
| Q23 | **(B)** | `>>` with `cin` is the **extraction** operator (extracts from stream into variable). `<<` with `cout` is insertion. |
| Q24 | **(D)** | `void` represents no value ✅, used as return type ✅, cannot declare `void x` ✅ — **all three correct**. |
| Q25 | **(E)** | All three — `= 5`, `(5)`, `{5}` — are valid C++ initialization syntax. Answer is **None of the above** (all are valid). |

---

## 🇮🇳 GS ANSWERS (Q26–Q50)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q26 | **(C)** | **V.D. Savarkar** was the first to call 1857 revolt "First War of Independence" in his book. |
| Q27 | **(C)** | **W.C. Bonnerjee** (Womesh Chandra Bonnerjee) was first President of INC (1885 session, Bombay). |
| Q28 | **(B)** | Champaran was about **Tinkathia system** — forced indigo cultivation. Not salt, not zamindari. |
| Q29 | **(B)** | **Rajkumar Shukla**, an indigo farmer, invited Gandhi to Champaran. Rajendra Prasad assisted later. |
| Q30 | **(C)** | Gandhi withdrew NCM due to **Chauri Chaura** (1922) — mob burned police station killing 22 policemen. |
| Q31 | **(B)** | **Sachindra Nath Sanyal** founded Anushilan Samiti Patna in 1913. |
| Q32 | **(C)** | Ghadar Party was founded in **USA** (San Francisco) by Lala Har Dayal in 1913. |
| Q33 | **(B)** | **Lord Chelmsford** was Viceroy during Jallianwala Bagh (1919). Curzon partitioned Bengal (1905). |
| Q34 | **(B)** | **V.D. Savarkar** founded Abhinav Bharat in **London**. |
| Q35 | **(C)** | **Chittaranjan Das** presided the Gaya session 1922. Important Bihar-connection PYQ! |
| Q36 | **(D)** | Bihar Socialist Party founded by **Phulan Prasad Varma AND Jayaprakash Narayan** — **both correct**. |
| Q37 | **(C)** | **Lord Curzon** announced Partition of Bengal in 1905. Dalhousie is known for Doctrine of Lapse. |
| Q38 | **(B)** | **Ganga Maiya Tohe Piyari Chadhaibo** (1963) was the first Bhojpuri film. |
| Q39 | **(B)** | **Anandamath** by Bankim Chandra mentions the **Sannyasi Revolt**. Also source of "Vande Mataram". |
| Q40 | **(B)** | **Gaya Munda** was the Commander-in-Chief of Birsa Munda's army. |
| Q41 | **(C)** | Quit India resolution was passed at **Gowalia Tank Maidan, Bombay** on August 8, 1942. |
| Q42 | **(B)** | **Aruna Asaf Ali** hoisted the Indian National Flag at Gowalia Tank on August 9, 1942. |
| Q43 | **(B)** | Bihar Provincial Congress Committee was founded in **1908** with HQ at Patna. |
| Q44 | **(C)** | **Kunwar Singh** of Jagdispur (Arrah), Bihar was the 1857 revolt hero of Bihar. |
| Q45 | **(B)** | Dandi March began on **March 12, 1930** and reached Dandi on April 6, 1930. |
| Q46 | **(C)** | **Dadabhai Naoroji** is called the "Grand Old Man of India." Gokhale was Gandhi's political guru. |
| Q47 | **(C)** | **Sardar Vallabhbhai Patel** led Bardoli Satyagraha. He earned the title "Sardar" from this. |
| Q48 | **(B)** | Tagore returned his knighthood protesting **Jallianwala Bagh massacre (1919)**. Not Bengal partition. |
| Q49 | **(C)** | **Swami Sahajanand Saraswati** founded AIKS Bihar in 1936. JP Narayan was socialist, not AIKS. |
| Q50 | **(D)** | Home Rule Movement led by **Bal Gangadhar Tilak AND Annie Besant** — **both** are correct. Sarojini Naidu was NOT associated with Home Rule League. Answer is D (More than one). |

---

## 📊 SCORING GUIDE

| Score (out of 25) | Assessment | Action |
|-------------------|------------|--------|
| 23–25 | 🏆 Topper Level | Excellent! Revise wrong ones only |
| 20–22 | ✅ Strong | Review 3–5 weak topics |
| 16–19 | 🔄 Good | Re-read relevant sections above |
| Below 16 | 📖 Needs Work | Re-read full section and retry tomorrow |

**Target: 23+/25 in both CS and GS to stay on topper track!**

---

## 📝 NIGHT REVISION — 5-BULLET SUMMARY (Write from memory before sleeping)

### CS Key Points to Remember:
1. Variable names cannot start with a digit — `123Var` is INVALID
2. `sizeof()` does NOT evaluate expressions — it's a compile-time operator
3. Global variables default to **0**; local variables have **garbage** values
4. User-defined headers use `""` double quotes and `.h` extension
5. `static` local variable: initialized once, retains value, default = 0

### GS Key Points to Remember:
1. Champaran (1917) — first civil disobedience; invited by Rajkumar Shukla; Bihar
2. V.D. Savarkar — first called 1857 "First War of Independence"; founded Abhinav Bharat (London)
3. Ghadar Party — USA; Anushilan Samiti Patna (1913) — Sachindra Nath Sanyal
4. Jallianwala Bagh (1919) — Viceroy: Lord Chelmsford; Tagore returned knighthood
5. Bihar Socialist Party — Phulan Prasad Varma + JP Narayan (BOTH)

---

## ⏭️ PREVIEW: DAY 9

**CS:** Pointers in C++ — `&`, `*`, NULL pointer, `delete`/`delete[]`, dangling pointer, `new` vs `malloc`
**GS:** Champaran Satyagraha 1917 (Deep Dive) + Non-Cooperation Movement details

---

*Day-8 Complete | Phase 1 → Week 2 | BPSC TRE 4.0 Topper Preparation*
*"Every concept mastered today is one more question answered correctly in September 2026."* 🎯
