# 📅 BPSC TRE 4.0 — DAY 14 COMPLETE STUDY MATERIAL
## CS Topic: REVISION WEEK — C++ Complete (Days 8–13) + PYQ Masterclass
## GS Topic: Maths Revision (Profit & Loss, Ratio, Averages) + Modern India Quick Recap

> **Day 14 is your POWER DAY.**
> This is not "new learning" — this is CONSOLIDATION.
> Every topper knows: revision beats new reading 3:1 in exam performance.
> Today you will see ALL C++ Week topics together, spot the connections, and solve
> a full set of PYQ-pattern questions to lock in your score advantage.

---

# ═══════════════════════════════════════════════════════════════════
# 🖥️ PART A — COMPUTER SCIENCE REVISION
# Complete C++ Week (Days 8–13) — All Topics in One Place
# ═══════════════════════════════════════════════════════════════════

---

## 📌 MASTER REVISION MAP — C++ WEEK AT A GLANCE

```
╔═══════════════════════════════════════════════════════════════════════╗
║               C++ WEEK TOPICS — DAYS 8 to 13                        ║
╠══════════════╦════════════════════════════════════════════════════════╣
║  Day 8       ║  Variables, Data Types, Naming Rules, sizeof()        ║
║  Day 9       ║  Pointers, new/delete, Dangling pointer, nullptr      ║
║  Day 10      ║  Arrays, String as char array, is_array(), rank()     ║
║  Day 11      ║  File Handling: ios::in/out/trunc/app/binary          ║
║  Day 12      ║  Exception Handling (try/catch/throw), Inline funcs   ║
║  Day 13      ║  Output Prediction, Bitwise ops, struct vs class, ::  ║
╚══════════════╩════════════════════════════════════════════════════════╝
```

---

## 📌 SECTION 1: DAY 8 RECAP — VARIABLES, DATA TYPES, NAMING RULES

### Variable Naming Rules — The 4 Laws:

```
LAW 1: CANNOT start with a digit
       ✗ 123abc    ✗ 9variable    ✗ 1st_name
       ✓ abc123    ✓ variable9    ✓ first_name

LAW 2: CANNOT have spaces
       ✗ my variable    ✗ first name
       ✓ my_variable    ✓ firstName

LAW 3: Only letters, digits, and underscore (_) allowed
       ✗ my-var    ✗ my@var    ✗ my#var    ✗ my.var
       ✓ my_var    ✓ myVar     ✓ _private

LAW 4: CANNOT be a C++ keyword
       ✗ int    ✗ class    ✗ return    ✗ void    ✗ for
       ✓ myInt  ✓ myClass  ✓ returnVal
```

### Invalid Variable Names — PYQ Favorites:

```
Variable Name        Valid/Invalid?    Reason
─────────────────────────────────────────────────────────
123Variable          INVALID          Starts with digit
my variable          INVALID          Contains space
int                  INVALID          Reserved keyword
_value               VALID            _ is allowed as first char
value_1              VALID            _ and digit allowed
My$Name              INVALID          $ not allowed in C++
__hidden             VALID            Multiple underscores OK
2ndTry               INVALID          Starts with digit
```

### Data Types + sizeof() Sizes:

```
Type          Size (typical)    Range
──────────────────────────────────────────────────────
char          1 byte            -128 to 127
unsigned char 1 byte            0 to 255
short         2 bytes           -32768 to 32767
int           4 bytes           -2,147,483,648 to 2,147,483,647
long          4 or 8 bytes      depends on platform
long long     8 bytes           very large range
float         4 bytes           ~6-7 decimal digits precision
double        8 bytes           ~15-16 decimal digits precision
bool          1 byte            0 (false) or 1 (true)
pointer       4 (32-bit) or     stores memory address
              8 bytes (64-bit)
```

### sizeof() — The "Does NOT Evaluate" Rule:

```cpp
int x = 5;
sizeof(x++);     // x is STILL 5 after this! sizeof does not execute x++
cout << x;       // Output: 5 (NOT 6)

// sizeof returns SIZE of TYPE, not value:
sizeof(int)      → 4
sizeof(double)   → 8
sizeof(char)     → 1
sizeof(int[10])  → 40  (10 elements × 4 bytes each)
```

### Header Files:

```
User-defined header files  → use .h extension   → #include "myheader.h"
Standard library headers   → no extension in C++ → #include <iostream>
Old C-style headers        → .h extension       → #include <stdio.h>
```

---

## 📌 SECTION 2: DAY 9 RECAP — POINTERS COMPLETE MASTERY

### Pointer Basics:

```cpp
int value = 42;
int* ptr = &value;    // ptr stores the ADDRESS of value

// & = "address of" operator
// * = "dereference" operator (go to the address)

cout << value;   // 42        (the actual value)
cout << &value;  // 0x7ffd... (the memory address)
cout << ptr;     // 0x7ffd... (same address, stored in ptr)
cout << *ptr;    // 42        (value AT the address ptr points to)
```

### Pointer Types — Visual Memory Diagram:

```
MEMORY LAYOUT:
─────────────────────────────────────────────────────────

Address:   1000    1004    1008    1012
           ┌───┐   ┌───┐   ┌───┐   ┌───┐
Value:     │42 │   │1000│  │ ? │   │ ? │
           └───┘   └───┘   └───┘   └───┘
Variable:  value   ptr    (other)  (other)

ptr = 1000 (stores address of 'value')
*ptr = 42  (value stored AT address 1000)
```

### NULL Pointer — Critical PYQ Rule:

```cpp
int* ptr = NULL;      // C style (NULL = 0)
int* ptr2 = nullptr;  // C++11 style (preferred)

// KEY EXAM FACT:
delete ptr;    // WHERE ptr = NULL → SAFE! NO CRASH. Does nothing.
               // This compiles AND executes successfully.

// WHY? Because the C++ standard guarantees:
// "delete applied to null pointer has no effect"
```

### delete vs delete[] — Must Distinguish:

```
┌──────────────────┬──────────────────────────────────────┐
│    delete        │    delete[]                          │
├──────────────────┼──────────────────────────────────────┤
│ For single object│ For arrays allocated with new[]      │
│ new T            │ new T[n]                             │
│ Calls destructor │ Calls destructor for EACH element    │
│ once             │                                      │
└──────────────────┴──────────────────────────────────────┘

CORRECT USAGE:
int* single = new int;        → delete single;    ✓
int* arr = new int[10];       → delete[] arr;     ✓

WRONG USAGE (Undefined Behavior):
int* arr = new int[10];       → delete arr;       ✗ WRONG
int* single = new int;        → delete[] single;  ✗ WRONG
```

### new vs malloc — Key Differences:

```
╔═══════════════════╦══════════════════════════════════════╗
║   new (C++)       ║   malloc (C)                        ║
╠═══════════════════╬══════════════════════════════════════╣
║ Operator          ║ Function                            ║
║ Calls constructor ║ Does NOT call constructor           ║
║ Returns correct   ║ Returns void* (needs casting)       ║
║ typed pointer     ║                                     ║
║ Throws exception  ║ Returns NULL on failure             ║
║ on failure        ║                                     ║
╚═══════════════════╩══════════════════════════════════════╝
```

### Dangling Pointer:

```cpp
int* ptr = new int(5);
delete ptr;            // Memory is freed
// ptr still holds the old address — it is now a DANGLING POINTER
cout << *ptr;          // UNDEFINED BEHAVIOR — accessing freed memory!

// FIX: Set to nullptr after delete
delete ptr;
ptr = nullptr;         // Now it's a safe null pointer
```

### Pointer Arithmetic:

```cpp
int arr[] = {10, 20, 30, 40, 50};
int* p = arr;       // Points to arr[0] = 10

p++;                // Now points to arr[1] = 20 (moved 4 bytes forward)
cout << *p;         // Output: 20

p + 2;              // Points to arr[3] = 40 (2 elements forward from arr[1])
cout << *(p + 2);   // Output: 40
```

---

## 📌 SECTION 3: DAY 10 RECAP — ARRAYS IN C++

### Array Declaration and Access:

```cpp
int array[5];              // Declares array of 5 ints (index 0 to 4)
int array[5] = {1,2,3,4,5}; // With initialization
int array[] = {1,2,3,4,5};  // Size inferred = 5

// CORRECT: int array[10];  ← This exact syntax appeared in PYQ!
// Index:   0   1   2  ... n-1  (NOT 1 to n)
// Last element: array[n-1]  NOT array[n]
```

### Array Size Functions:

```
is_array<T>()    →  Checks if T is an array type (returns true/false)
rank<T>::value   →  Returns number of dimensions of array T
                    1D array → rank = 1
                    2D array → rank = 2

Example:
  int arr[3][4];
  rank<decltype(arr)>::value = 2   (it is 2-dimensional)
```

### String as char Array — PYQ TRAP:

```cpp
char s1[] = "Hello";
char s2[] = "World";

// Can you do this?
char s3[] = s1 + s2;    // ✗ COMPILE ERROR — cannot use + with char arrays!
string result = s1 + s2; // ✗ Still error — s1 is char[], not std::string

// CORRECT ways to concatenate char arrays:
strcat(s1, s2);          // ✓ Using strcat function (modifies s1)

// If you use std::string:
string str1 = "Hello";
string str2 = "World";
string str3 = str1 + str2;  // ✓ Works fine for std::string objects
```

### 2D Arrays:

```cpp
int matrix[3][4];    // 3 rows, 4 columns
// Access: matrix[row][col]
// matrix[0][0] = first element
// matrix[2][3] = last element

// Memory: stored ROW by ROW (row-major order in C++)
```

---

## 📌 SECTION 4: DAY 11 RECAP — FILE HANDLING COMPLETE

### File Stream Classes:

```
ifstream   → Input file stream  (reading from file)
ofstream   → Output file stream (writing to file)
fstream    → Both input AND output
```

### File Modes — THE COMPLETE TABLE (Memorize!):

```
╔══════════════╦══════════════════════════════════════════════════════╗
║ Mode         ║ Meaning / Effect                                    ║
╠══════════════╬══════════════════════════════════════════════════════╣
║ ios::in      ║ Open for READING                                    ║
║ ios::out     ║ Open for WRITING (creates file if not exists)       ║
║ ios::trunc   ║ TRUNCATE file to zero length when opened ⭐         ║
║ ios::app     ║ APPEND — write at END of file only                  ║
║ ios::binary  ║ Open in BINARY mode (not text mode)                 ║
║ ios::ate     ║ Move to END of file on opening                      ║
╚══════════════╩══════════════════════════════════════════════════════╝

⭐ ios::trunc = "truncate" = file becomes EMPTY (zero length) on opening
```

### Combining File Modes:

```cpp
// Modes can be combined with | (bitwise OR):
fstream f;
f.open("data.txt", ios::in | ios::out);        // Read AND write
f.open("data.txt", ios::out | ios::trunc);     // Write + truncate
f.open("data.txt", ios::out | ios::app);       // Write + append
f.open("data.bin", ios::in | ios::binary);     // Binary reading
```

### File Operations:

```cpp
ofstream outFile;
outFile.open("test.txt");         // Open file
outFile << "Hello World";          // Write to file
outFile.close();                   // Close file

ifstream inFile("test.txt");       // Open for reading
string line;
getline(inFile, line);             // Read a line
while(!inFile.eof()) { ... }      // Loop until End of File
inFile.close();
```

### Turbo C++ Shortcut (PYQ Fact):

```
Ctrl + F9  =  Compile AND Run in Turbo C++
This exact shortcut has appeared in BPSC TRE PYQs!
```

---

## 📌 SECTION 5: DAY 12 RECAP — EXCEPTION HANDLING + INLINE FUNCTIONS

### Exception Handling Flow:

```
NORMAL FLOW:                    EXCEPTION FLOW:
                                
try {                           try {
    code...          ──────►        code...
    risky code                      risky code  ──► THROWS exception
    more code                       (skipped)
}                               }
catch(type e) {                 catch(type e) {
    (skipped)                       CAUGHT here! ◄──
}                               }
continue...                     continue after catch...
```

### Syntax — Complete:

```cpp
try {
    int a = 10, b = 0;
    if(b == 0) throw "Division by zero!";  // throw statement
    cout << a/b;
}
catch(const char* msg) {         // catch specific type
    cout << "Error: " << msg;    // handles char* exceptions
}
catch(int e) {                   // catch int exceptions
    cout << "Int error: " << e;
}
catch(...) {                     // catch ALL exceptions (catch-all)
    cout << "Unknown error";
}
```

### Multiple Catch — Order Matters:

```
⚠️ RULE: More specific catches FIRST, general catch (...) LAST
         If catch(...) is first, it catches everything — other catches unreachable!

CORRECT ORDER:
try { ... }
catch(int e) { ... }        // specific first
catch(string e) { ... }     // specific second
catch(...) { ... }          // general LAST ✓

WRONG ORDER:
try { ... }
catch(...) { ... }          // catches EVERYTHING — below catches never reached!
catch(int e) { ... }        // DEAD CODE ✗
```

### Inline Functions:

```
WHAT:  Function expanded at the call point (no function call overhead)
HOW:   Compiler replaces function call with function body
USE:   ONLY for SMALL, SIMPLE functions

╔══════════════════════════╦═══════════════════════════════════╗
║ USE inline when:         ║ DO NOT use inline when:           ║
╠══════════════════════════╬═══════════════════════════════════╣
║ Function is 1-3 lines    ║ Function is large/complex         ║
║ Called very frequently   ║ Contains loops                    ║
║ No loops or complex code ║ Contains recursion                ║
║ Access cost matters      ║ Contains static variables         ║
╚══════════════════════════╩═══════════════════════════════════╝
```

```cpp
inline int square(int x) {   // inline keyword
    return x * x;             // Simple, small function
}

// When called: square(5)
// Compiler replaces it with: 5 * 5  (directly substituted)
// No function call overhead!
```

### Inline vs Normal Function:

```
NORMAL FUNCTION:              INLINE FUNCTION:
main() calls square()         main() has 5*5 directly
  → jump to square            No jumping needed
  → compute                   Computed right there
  → return to main            Faster execution
  → continue                  But code size increases
```

---

## 📌 SECTION 6: DAY 13 RECAP — OUTPUT PREDICTION MASTER SUMMARY

### Pre/Post Increment Quick Reference:

```
++x  →  increment FIRST, use later  →  value used = (x+1)
x++  →  use FIRST, increment later  →  value used = x (original)

int a = 5;
cout << ++a;  → Output: 6  (a is now 6)
cout << a++;  → Output: 6  (prints 6, then a becomes 7)
cout << a;    → Output: 7
```

### Bitwise Quick Reference Table:

```
OPERATION    SYMBOL    RULE                        EXAMPLE (5 op 3)
──────────────────────────────────────────────────────────────────
AND            &       Both 1 → 1                  0101 & 0011 = 0001 = 1
OR             |       At least one 1 → 1           0101 | 0011 = 0111 = 7
XOR            ^       Exactly one 1 → 1            0101 ^ 0011 = 0110 = 6
NOT            ~       Flip all bits                ~5 = -6  (formula: ~n = -(n+1))
Left Shift     <<      n << k = n × 2^k             5 << 2 = 20
Right Shift    >>      n >> k = n ÷ 2^k             20 >> 2 = 5
```

### struct vs class — THE ONE RULE:

```
╔════════════════════════════════════════════════════════╗
║  struct → DEFAULT ACCESS = PUBLIC                      ║
║  class  → DEFAULT ACCESS = PRIVATE                     ║
║  THIS IS THE ONLY DIFFERENCE IN C++                    ║
╚════════════════════════════════════════════════════════╝
```

---

## 📌 SECTION 7: COMPLETE PYQ-PATTERN OUTPUT PREDICTION PROBLEMS

### Problem Set 1 — Variable Names:

Which of the following are VALID C++ variable names?
```
a) 2value     → INVALID (starts with digit)
b) value_2    → VALID ✓
c) _myVar     → VALID ✓
d) my-value   → INVALID (hyphen not allowed)
e) float      → INVALID (reserved keyword)
f) Float      → VALID ✓ (C++ is case-sensitive; Float ≠ float)
```

### Problem Set 2 — Pointer Operations:

```cpp
// Q: What is the output?
int a = 10;
int* p = &a;
*p = 20;
cout << a;
// Answer: 20
// Why: *p = 20 changes the value AT the address p points to (which is a)
```

```cpp
// Q: What happens here?
int* ptr = NULL;
delete ptr;
cout << "Done";
// Answer: Output is "Done" — no crash!
// Why: delete on NULL pointer is safe; does nothing; program continues
```

### Problem Set 3 — File Modes:

```
Q: Which file mode TRUNCATES the file to zero when opened?
A: ios::trunc

Q: Which mode adds content at the END of the file?
A: ios::app

Q: Can modes be combined? How?
A: Yes, using | operator: ios::in | ios::out | ios::binary
```

### Problem Set 4 — Exception Handling:

```cpp
// Q: What is the output?
try {
    throw 42;
}
catch(string s) {
    cout << "String: " << s;
}
catch(int e) {
    cout << "Int: " << e;
}
// Answer: Int: 42
// Why: throw 42 throws an int; first catch expects string (no match); second catches int ✓
```

### Problem Set 5 — Inline Functions:

```
Q: Which of the following functions is SUITABLE for inlining?
A) A function with a for loop running 1000 times     → NOT suitable
B) A function that returns x*x (one line)            → SUITABLE ✓
C) A recursive function                              → NOT suitable
D) A function with 50 lines of code                 → NOT suitable
```

---

## 📌 SECTION 8: COMMON MISTAKES TABLE — BPSC TOPPER WARNING

```
╔══════════════════════════════════════════╦════════════════════════════════════════════╗
║  WRONG BELIEF (Trap)                     ║  CORRECT FACT                              ║
╠══════════════════════════════════════════╬════════════════════════════════════════════╣
║ delete NULL crashes                      ║ delete NULL = SAFE, does nothing           ║
║ delete arr and delete[] arr are same     ║ Must use delete[] for array                ║
║ ios::trunc adds to end                   ║ ios::app adds to end; trunc = truncate     ║
║ sizeof() evaluates expression            ║ sizeof() does NOT execute/evaluate         ║
║ struct and class are completely same     ║ ONLY difference = default access specifier ║
║ Inline functions for large functions     ║ Inline for SMALL, SIMPLE functions ONLY    ║
║ catch(...) can come first                ║ catch(...) must come LAST                  ║
║ 123variable is valid                     ║ INVALID — starts with digit                ║
║ new and malloc both call constructors    ║ ONLY new calls constructor; malloc does NOT ║
║ Dangling pointer = NULL pointer          ║ Dangling = points to freed memory; NOT null ║
╚══════════════════════════════════════════╩════════════════════════════════════════════╝
```

---

# ═══════════════════════════════════════════════════════════════════
# 🏛️ PART B — GENERAL STUDIES REVISION
# Maths (Profit/Loss, Ratio, Averages) + Modern India Recap
# ═══════════════════════════════════════════════════════════════════

---

## 📌 SECTION 9: MATHS REVISION — PROFIT & LOSS (High BPSC Frequency)

### Core Terminology:

```
CP  = Cost Price    (what you paid to buy)
SP  = Selling Price (what you sold for)
MP  = Marked Price  (price on label/tag)

Profit = SP - CP     (when SP > CP)
Loss   = CP - SP     (when CP > SP)

Profit% = (Profit / CP) × 100
Loss%   = (Loss / CP) × 100   ← ALWAYS calculated on CP, not SP!
```

### Formulas in One Place:

```
SP = CP × (100 + Profit%) / 100       [when profit]
SP = CP × (100 - Loss%) / 100         [when loss]

CP = SP × 100 / (100 + Profit%)       [find CP from SP with profit]
CP = SP × 100 / (100 - Loss%)         [find CP from SP with loss]

Discount  = MP - SP
Discount% = (Discount / MP) × 100     ← Discount always on MP!

SP = MP × (100 - Discount%) / 100
```

### Solved Examples (PYQ Level):

**Example 1:**
An article bought for ₹800 is sold at 25% profit. Find SP.
```
SP = 800 × (100 + 25) / 100
   = 800 × 125 / 100
   = 800 × 1.25
   = ₹1000
```

**Example 2:**
An article sold for ₹900 with 10% loss. Find CP.
```
SP = CP × (100 - Loss%) / 100
900 = CP × 90 / 100
CP = 900 × 100 / 90
CP = ₹1000
```

**Example 3 (Tricky — PYQ Pattern):**
A shopkeeper marks an article 40% above CP and gives 20% discount. Profit or loss?
```
Let CP = 100
MP = 100 + 40% of 100 = 140
SP = MP - 20% of MP = 140 - 28 = 112

Profit = 112 - 100 = 12
Profit% = 12%

TRICK FORMULA:  Net % = m - d - (m×d)/100
where m = markup%, d = discount%
= 40 - 20 - (40×20)/100 = 20 - 8 = 12%  ✓
```

**Example 4 (Two articles sold at same price):**
Two articles sold at ₹1200 each. One at 20% profit, other at 20% loss. Overall?
```
When SP is SAME and profit% = loss%, ALWAYS a net loss!
Net Loss% = (common %)² / 100 = (20)² / 100 = 4%

CP of first  = 1200 × 100/120 = ₹1000
CP of second = 1200 × 100/80  = ₹1500
Total CP = 2500; Total SP = 2400; Loss = ₹100; Loss% = 4% ✓
```

---

## 📌 SECTION 10: MATHS REVISION — RATIO & PROPORTION

### Key Concepts:

```
Ratio a:b means "for every a parts, there are b parts"
a:b = a/b (fractions)

Proportion: a:b = c:d  means  a/b = c/d  means  a×d = b×c
(Cross multiplication rule)
```

### Types of Proportion:

```
DIRECT PROPORTION:    If A ↑ then B ↑ (more workers → more work done)
INVERSE PROPORTION:   If A ↑ then B ↓ (more workers → less days needed)
```

### Dividing in a Ratio:

```
Amount X divided in ratio a:b:c

Share of a = X × a/(a+b+c)
Share of b = X × b/(a+b+c)
Share of c = X × c/(a+b+c)
```

### Solved Example:

**Example:** ₹1500 is divided among A, B, C in ratio 2:3:5. Find each share.
```
Total parts = 2+3+5 = 10

A's share = 1500 × 2/10 = ₹300
B's share = 1500 × 3/10 = ₹450
C's share = 1500 × 5/10 = ₹750

Check: 300 + 450 + 750 = 1500 ✓
```

---

## 📌 SECTION 11: MATHS REVISION — AVERAGES

### Formulas:

```
Average = Sum of all items / Number of items

Sum = Average × Number of items    ← Most useful rearrangement!

If average of n items = A, and one item x is added:
New average = (n×A + x) / (n+1)

If average of n items = A, and one item x is removed:
New average = (n×A - x) / (n-1)
```

### Solved Examples:

**Example 1:**
Average of 5 numbers is 40. If one number 60 is removed, new average?
```
Sum of 5 numbers = 5 × 40 = 200
Sum after removing 60 = 200 - 60 = 140
New average = 140 / 4 = 35
```

**Example 2 (PYQ Pattern):**
Average age of class of 30 students is 14 years. If teacher's age 44 is included, new average?
```
Sum of students' ages = 30 × 14 = 420
New sum = 420 + 44 = 464
New count = 31
New average = 464/31 = 14.97 ≈ 15 years (approximately)
```

---

## 📌 SECTION 12: MATHS REVISION — PERCENTAGES

### Key Formulas:

```
X% of Y = (X/100) × Y = XY/100

% increase = (New - Old)/Old × 100
% decrease = (Old - New)/Old × 100

If a value increases by X%, new value = Old × (1 + X/100)
If a value decreases by X%, new value = Old × (1 - X/100)
```

### Important Fraction-Percentage Equivalents (Memorize!):

```
1/2  = 50%       1/3  = 33.33%    1/4  = 25%
1/5  = 20%       1/6  = 16.67%    1/7  = 14.28%
1/8  = 12.5%     1/9  = 11.11%    1/10 = 10%
1/11 = 9.09%     1/12 = 8.33%     3/4  = 75%
2/3  = 66.67%    3/5  = 60%       4/5  = 80%
```

### Successive Percentage Change:

```
Two successive changes: first by a%, then by b%
Net change = a + b + (a×b)/100  %

Example: 20% increase then 10% decrease
= 20 + (-10) + (20 × (-10))/100
= 20 - 10 - 2 = 8% net increase
```

---

## 📌 SECTION 13: MODERN INDIA — QUICK RECAP TABLE (All Key Events)

### Freedom Struggle Events — Rapid Revision:

```
YEAR    EVENT                               KEY PERSON / PLACE
──────────────────────────────────────────────────────────────────────
1857    Revolt of 1857 / 1st War Indep.     Mangal Pandey (Barrackpore)
                                            Rani Lakshmibai (Jhansi)
                                            Nana Sahib (Kanpur)
1885    INC Founded                         A.O. Hume, W.C. Banerjee (1st Pres)
1905    Partition of Bengal                 Lord Curzon (Viceroy)
1906    Muslim League Founded               Dhaka
1907    Surat Split                         Moderates vs Extremists
1916    Lucknow Pact                        Congress + Muslim League unite
1917    Champaran Satyagraha               Gandhi + Rajendra Prasad ⭐ BIHAR
1919    Rowlatt Act + Jallianwala Bagh      Gen. Dyer, 379+ killed
1920    Khilafat + Non-Cooperation          Gandhi; withdrew 1922 (Chauri Chaura)
1929    Lahore Session "Purna Swaraj"       Nehru as Congress President
1930    Dandi March / Salt Satyagraha       March 12 – April 6; 241 miles
1931    Gandhi-Irwin Pact                   Suspended Civil Disobedience
1942    Quit India Movement                 "Do or Die"; Aug 8; Gowalia Tank
1947    Independence                        August 15; Nehru 1st PM
1950    Constitution enacted                January 26; Rajendra Prasad 1st Pres
```

---

## 📌 SECTION 14: REVOLT OF 1857 — COMPLETE DETAIL (GS High Weight)

### Causes:

```
IMMEDIATE CAUSE:
  Enfield rifle cartridges greased with cow and pig fat
  Soldiers had to BITE the cartridge → both Hindus and Muslims outraged

MILITARY CAUSES:
  • General Service Enlistment Act — cross seas (taboo for Hindus)
  • Discrimination in promotion and pay
  • British officers' disrespect for Indian soldiers

POLITICAL CAUSES:
  • Doctrine of Lapse (Dalhousie) — annexed states (Jhansi, Satara, Nagpur)
  • Removal of Nawab of Awadh (Wajid Ali Shah) on pretext of misgovernment
  • Mughal Emperor Bahadur Shah Zafar's position threatened

ECONOMIC CAUSES:
  • Drain of Wealth theory (Dadabhai Naoroji)
  • Indian artisans destroyed by cheap British goods
  • Heavy taxation of peasants

SOCIAL CAUSES:
  • Fear of Christianization — missionary activities
  • Introduction of railways, telegraph seen as threat to tradition
  • Abolition of practices like sati — seen as interference
```

### Key Centers and Leaders:

```
CENTER              LEADER
──────────────────────────────────────────────────────────
Barrackpore         Mangal Pandey (FIRST spark — March 29, 1857)
Delhi               Bahadur Shah Zafar II (nominal leader; Mughal Emperor)
Jhansi              Rani Lakshmibai ("Best man among the mutineers" — Hugh Rose)
Kanpur (Cawnpore)   Nana Sahib, Tantia Tope
Lucknow             Begum Hazrat Mahal (Nawab's wife)
Bihar (Jagdishpur)  Kunwar Singh (old but fierce warrior)
Bareilly            Khan Bahadur Khan
Faizabad            Maulvi Ahmadullah
```

### Kunwar Singh — Bihar's Hero of 1857:

```
• Zamindar of Jagdishpur, Bhojpur district, Bihar
• 80 years old when he joined the revolt — still fought bravely!
• Led uprising in Arrah (Bihar) and Azamgarh (UP)
• Defeated British forces multiple times
• Died fighting in April 1858
• Bihar's most prominent freedom fighter of 1857
• His birthday: 13 November — celebrated in Bihar
```

### Nature and Outcome of Revolt:

```
CALLED BY:           TERM USED:
British historians → "Sepoy Mutiny" (limited rebellion by soldiers)
V.D. Savarkar      → "First War of Independence" (1909, in his book)
Indian historians  → Also called India's First Independence War

OUTCOME:
  • Revolt suppressed by September 1858
  • Bahadur Shah Zafar exiled to Rangoon (Burma) — died 1862
  • Rani Lakshmibai died fighting (June 17, 1858, Gwalior)
  • British Crown took over from East India Company
  • East India Company dissolved; Queen Victoria became Empress of India
  • Governor General became Viceroy (first: Lord Canning)
```

---

## 📌 SECTION 15: SOCIO-RELIGIOUS REFORM MOVEMENTS (High GS Frequency)

### Reform Movements Table:

```
MOVEMENT / ORGANISATION    FOUNDER              YEAR    KEY WORK
──────────────────────────────────────────────────────────────────────────────
Brahmo Samaj               Raja Ram Mohan Roy   1828    Against sati, child marriage
                                                        Got Sati abolished (1829)
Arya Samaj                 Dayananda Saraswati  1875    "Back to Vedas"; opposed idol worship
Ramakrishna Mission        Vivekananda          1897    Service to humanity = service to God
Prarthana Samaj            Atmaram Pandurang    1867    Maharashtra; social reform
Theosophical Society       H.P. Blavatsky       1875    Annie Besant later president
                           H.S. Olcott                  HQ: Adyar, Chennai
Satyashodhak Samaj         Jyotiba Phule        1873    Against caste discrimination
Aligarh Movement           Sir Syed Ahmad Khan  1875    Muslim education; MAO College
Young Bengal Movement      Henry Vivian Derozio 1820s   Rationalism; free thinking
Singh Sabha Movement        —                   1873    Sikh reform movement
```

### Raja Ram Mohan Roy — Father of Modern India:

```
Born: 1772 in Radhanagar, Bengal
Died: 1833 in Bristol, England

KEY ACHIEVEMENTS:
1. Founded Brahmo Samaj (1828) — first modern reform society
2. Campaigned against SATI → Led to Bengal Sati Regulation, 1829
   (Lord Bentinck was Governor General when sati was abolished)
3. Supported widow remarriage
4. Fought against child marriage, polygamy
5. Promoted English education and Western science
6. Founded "Sambad Kaumudi" (newspaper in Bengali)
7. Title: "Father of Indian Renaissance" / "Father of Modern India"
```

---

## 📌 SECTION 16: IMPORTANT ACTS OF BRITISH INDIA (Exam Staple)

```
ACT                         YEAR    KEY PROVISIONS
──────────────────────────────────────────────────────────────────────────
Regulating Act              1773    First Act to regulate East India Company
                                    Created position of Governor General (Warren Hastings first)
Pitt's India Act            1784    Board of Control established; dual control
Charter Act                 1813    Company's monopoly over trade ended (except China tea)
Charter Act                 1833    Company became purely administrative; law codification
Govt of India Act           1858    Crown Rule; Company dissolved; Viceroy created
Indian Councils Act         1861    Legislative councils with Indian members
Indian Councils Act         1892    More Indian members; budget discussion allowed
Morley-Minto Reforms        1909    Separate electorates for Muslims (communal virus planted)
Montagu-Chelmsford          1919    Dyarchy introduced; provincial autonomy partial
Govt of India Act           1935    Provincial autonomy full; Federal structure proposed;
                                    All-India Federation (never implemented)
Independence Act            1947    India + Pakistan as two dominions from Aug 15, 1947
```

---

## 📌 SECTION 17: BHARAT RATNA — COMPLETE LIST (Exam Favorites)

### First Bharat Ratna Recipients:

```
Year    Recipient                   Field
────────────────────────────────────────────────────────
1954    C. Rajagopalachari          Statesman (First Governor General of India)
1954    S. Radhakrishnan            Philosopher, President (Teacher's Day = Sep 5)
1954    C.V. Raman                  Physicist (Raman Effect; Nobel 1930)
1955    Bhagwan Das                 Philosopher
1955    M. Visvesvaraya             Engineer (Karnataka — Engineer's Day Sep 15)
1955    Jawaharlal Nehru            Prime Minister
1957    Govind Ballabh Pant         Statesman (UP); India's Home Minister
1958    D.H. Lawrence               ...
1961    Purushottam Das Tandon      Freedom Fighter
1962    Dr. Rajendra Prasad         1st President of India ⭐ BIHAR
1963    Dr. Zakir Husain            Educationist, President of India
1963    P.V. Kane                   Sanskrit Scholar
```

### Bihar / Bihar-Connected Bharat Ratna:

```
Name                Year    Connection
────────────────────────────────────────────────────────────
Dr. Rajendra Prasad 1962    Born Siwan, Bihar; 1st President ⭐
Jayaprakash Narayan 1999    Born Saran, Bihar; Loknayak ⭐
Bismillah Khan      2001    Born Dumraon (Buxar), Bihar ⭐
```

---

## 📌 SECTION 18: GEOGRAPHY — BIHAR COMPLETE FACTS

### Bihar — Physical Geography:

```
Location:     Eastern India; 24°20'N – 27°31'N, 83°19'E – 88°17'E
Area:         94,163 sq km (13th largest state)
Districts:    38 districts (as of 2024)
Divisions:    9 divisions
Capital:      Patna (on south bank of Ganga)
Bihar Day:    22 March (formed 1912 when separated from Bengal)
```

### Bihar Rivers:

```
River          Source                 Flows into     Special Note
───────────────────────────────────────────────────────────────────────
Ganga          Gangotri Glacier       Bay of Bengal  Divides Bihar N-S
Sone           Amarkantak Plateau     Ganga          Major south-bank river
Gandak         Nepal Himalayas        Ganga           
Kosi           Nepal (Himalayas)      Ganga           "Sorrow of Bihar" ⭐
Bagmati        Nepal (Shivpuri)       Ganga           
Mahananda      Darjeeling Hills       Ganga           
Punpun         Palamu Hills           Ganga          Sacred river (Pitrapaksha)
Falgu          Hazaribagh             Ganga          Near Gaya (pilgrim site)
```

### Important Bihar Facts for BPSC:

```
FACT                                          ANSWER
──────────────────────────────────────────────────────────────────────
Bihar's population % of India                 8.58%
Most populous district                        Patna
Highest paddy production district             Rohtas ⭐
Highest silk textile district                 Bhagalpur ⭐
"Silk City" of Bihar                          Bhagalpur
"Lichchi City" of Bihar                       Muzaffarpur
First state to have caste-based survey        Bihar (2023 caste survey)
Bihar's state tree                            Peepal (Ashoka officially)
Bihar's state bird                            House Sparrow (Gauriya)
Bihar's state animal                          Gaur (Indian Bison)
Bihar's state flower                          Kachnar (Bauhinia)
Bihar's state fish                            Mango Fish (Mangur)
"Sorrow of Bihar" river                       Kosi ⭐
India's first President                       Dr. Rajendra Prasad (Bihar) ⭐
Bihar's first Chief Minister                  Srikrishna Sinha (1946)
Highest point in Bihar                        Somasur (880m) in Kaimur range
```

---

## 📌 SECTION 19: SCIENCE QUICK REVISION (Physics + Biology PYQ Facts)

### Physics PYQ Facts:

```
FACT                                           ANSWER
──────────────────────────────────────────────────────────────────────
Bernoulli's principle application              Spray bottle, airplane wing
Speed of electron in 1st orbit of H           c/137 (c = speed of light)
Stefan-Boltzmann law                           Energy ∝ T⁴
Convex lens placed in water                    Still convex; focal length INCREASES
Frequency when light changes medium            Frequency UNCHANGED; wavelength changes
Electrical power formula                       P = I²R = V²/R = VI
Resistance in parallel: two equal R           Half of one R (R/2)
Sound cannot travel through                    Vacuum
Loudest sound unit                             Decibel (dB)
ISS orbiting altitude (approx)                 400 km above Earth
```

### Biology PYQ Facts:

```
FACT                                           ANSWER
──────────────────────────────────────────────────────────────────────
Photoperiodism discovered by                   Garner and Allard
Ginger is what type of modified stem           Underground stem (rhizome) — has nodes
Asexual reproduction by budding                Yeast (fungus)
Anther contains                                Pollen grains (male gametes)
Diaphragm during normal inhalation             Flattens (contracts)
Most important for immunity                    Lymphocytes (white blood cells)
Antacid used for                               Indigestion / acidity
Vas deferens is                                Male organ (carries sperm)
Silent Valley is in                            Kerala (rare biodiversity spot)
Blood groups discovered by                     Karl Landsteiner (Nobel 1930)
```

---

# ═══════════════════════════════════════════════════════════════════
# ✏️ PRACTICE QUESTIONS — DAY 14
# ═══════════════════════════════════════════════════════════════════

> ⚠️ **INSTRUCTIONS:**
> Attempt ALL 50 questions FIRST.
> ANSWERS are at the VERY END. Do not scroll down before attempting.
> Time yourself: Target 40 minutes for 50 questions (48 seconds each).

---

# 💻 SECTION A — COMPUTER SCIENCE (25 Questions)

### CS-Q1.
Which of the following is a VALID C++ variable name?
(A) 2myVar  
(B) my-Var  
(C) _myVar  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q2.
What is the output of the following code?
```cpp
int x = 5;
int y = sizeof(x++);
cout << x;
```
(A) 6  
(B) 4  
(C) 5  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q3.
`delete ptr` where `ptr = NULL` in C++ will:
(A) Cause runtime crash  
(B) Cause compile error  
(C) Execute successfully without any error  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q4.
`new` operator in C++ differs from `malloc()` in that:
(A) `new` is a function; `malloc` is an operator  
(B) `new` calls the constructor; `malloc` does not  
(C) `new` returns void*; `malloc` returns typed pointer  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q5.
For an array declared as `int arr[5]`, what is the index of the LAST element?
(A) 5  
(B) 4  
(C) 0  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q6.
Which file mode in C++ TRUNCATES the file to zero length when opened?
(A) `ios::app`  
(B) `ios::ate`  
(C) `ios::trunc`  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q7.
What happens when you execute: `char s1[]="Hello"; char s2[]="World"; cout << s1+s2;`?
(A) Output: HelloWorld  
(B) Output: Hello World  
(C) Compile error  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q8.
Which of the following is the correct order for multiple catch blocks?
(A) General `catch(...)` first, then specific types  
(B) Specific types first, then general `catch(...)` last  
(C) Order does not matter for catch blocks  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q9.
Inline functions in C++ are BEST used for:
(A) Large, complex functions to improve speed  
(B) Functions containing loops and recursion  
(C) Small, simple functions called frequently  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q10.
Which of the following statements about a DANGLING pointer is CORRECT?
(A) It is a pointer initialized to NULL  
(B) It is a pointer that points to freed/deallocated memory  
(C) It is a pointer that has never been initialized  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q11.
The shortcut key `Ctrl+F9` in Turbo C++ is used for:
(A) Save file  
(B) Open file  
(C) Compile and Run  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q12.
User-defined header files in C++ use which extension?
(A) `.cpp`  
(B) `.cc`  
(C) `.h`  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q13.
When is `delete[]` used instead of `delete` in C++?
(A) When deleting a single object  
(B) When deleting an array allocated with `new[]`  
(C) When deleting a NULL pointer  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q14.
What is the output?
```cpp
int a = 4, b = 6;
int c = a++ + ++b;
cout << c << " " << a << " " << b;
```
(A) 10 5 7  
(B) 11 5 7  
(C) 10 4 7  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q15.
Which of the following variable names is INVALID in C++?
(A) `_value`  
(B) `Float` (capital F)  
(C) `for`  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q16.
What is the value of `~0` (bitwise NOT of 0) in C++?
(A) 0  
(B) 1  
(C) -1  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q17.
The `ios::app` file mode:
(A) Truncates the file to zero  
(B) Opens file and writes at the end only  
(C) Opens file in binary mode  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q18.
`is_array()` function in C++ is used to:
(A) Return the number of elements in an array  
(B) Check whether a variable is of array type  
(C) Sort the array elements  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q19.
Which of the following is the purpose of `catch(...)` in C++?
(A) Catch only integer exceptions  
(B) Catch only string exceptions  
(C) Catch ALL types of exceptions  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q20.
What does the `rank()` template in C++ return for a 2D array?
(A) Total number of elements  
(B) Number of dimensions (2 for 2D array)  
(C) Number of rows  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q21.
In C++, `&` when used with a variable name (e.g., `&x`) means:
(A) Bitwise AND  
(B) Address-of operator (returns memory address)  
(C) Reference to variable  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q22.
A pointer `p` points to integer `x`. After `delete p`, what should you do to avoid dangling pointer?
(A) `p = 0;`  
(B) `p = NULL;`  
(C) `p = nullptr;`  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q23.
What is the output of the following code?
```cpp
int* p = nullptr;
delete p;
cout << "OK";
```
(A) Compile error  
(B) Runtime crash  
(C) OK  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q24.
Which of the following C++ file stream classes is used for BOTH reading AND writing?
(A) `ifstream`  
(B) `ofstream`  
(C) `fstream`  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q25.
When `throw` is used without an expression inside a catch block, it:
(A) Throws a new default exception  
(B) Re-throws the currently caught exception  
(C) Terminates the program  
(D) More than one of the above  
(E) None of the above  

---

# 🏛️ SECTION B — GENERAL STUDIES (25 Questions)

### GS-Q1.
An article bought for ₹500 is sold at 20% profit. What is the Selling Price?
(A) ₹520  
(B) ₹600  
(C) ₹580  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q2.
An article is sold for ₹720 at a loss of 10%. Find the Cost Price.
(A) ₹792  
(B) ₹648  
(C) ₹800  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q3.
₹2400 is divided among A, B, C in ratio 1:2:3. What is C's share?
(A) ₹400  
(B) ₹800  
(C) ₹1200  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q4.
Average of 6 numbers is 50. If one number 80 is removed, what is the new average?
(A) 44  
(B) 46  
(C) 48  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q5.
A shopkeeper marks price 50% above cost and gives 20% discount. What is profit/loss %?
(A) 20% profit  
(B) 30% profit  
(C) 20% loss  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q6.
The IMMEDIATE cause of the Revolt of 1857 was:
(A) Doctrine of Lapse  
(B) Greased cartridges of the Enfield rifle  
(C) Abolition of sati  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q7.
Who was the leader of the 1857 Revolt in Bihar (Jagdishpur)?
(A) Mangal Pandey  
(B) Nana Sahib  
(C) Kunwar Singh  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q8.
The first spark of the 1857 Revolt was fired at:
(A) Meerut  
(B) Barrackpore  
(C) Delhi  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q9.
V.D. Savarkar described the Revolt of 1857 as:
(A) Sepoy Mutiny  
(B) First War of Indian Independence  
(C) A Civil Rebellion  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q10.
The Brahmo Samaj was founded by:
(A) Dayananda Saraswati  
(B) Swami Vivekananda  
(C) Raja Ram Mohan Roy  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q11.
The abolition of Sati (1829) took place under which Governor General?
(A) Lord Dalhousie  
(B) Lord Curzon  
(C) Lord William Bentinck  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q12.
The Arya Samaj was founded by:
(A) Swami Vivekananda  
(B) Dayananda Saraswati  
(C) Raja Ram Mohan Roy  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q13.
The Ramakrishna Mission was founded by:
(A) Ramakrishna Paramahamsa  
(B) Swami Vivekananda  
(C) Raja Ram Mohan Roy  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q14.
Which river is known as the "Sorrow of Bihar"?
(A) Gandak  
(B) Ganga  
(C) Kosi  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q15.
Which district of Bihar is known for the HIGHEST production of silk textile?
(A) Rohtas  
(B) Patna  
(C) Bhagalpur  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q16.
Bihar was formally separated from Bengal Presidency on:
(A) 1 April 1912  
(B) 22 March 1912  
(C) 15 August 1947  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q17.
The state bird of Bihar is:
(A) Peacock  
(B) House Sparrow (Gauriya)  
(C) Crane  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q18.
Which district of Bihar is known for maximum paddy (rice) production?
(A) Muzaffarpur  
(B) Bhagalpur  
(C) Rohtas  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q19.
The first Governor General of India after the Crown took control in 1858 was:
(A) Lord Dalhousie  
(B) Lord Canning  
(C) Lord Curzon  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q20.
The Regulating Act (1773) was significant because it:
(A) Dissolved the East India Company  
(B) Created the position of Governor General of India  
(C) Introduced dyarchy in provinces  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q21.
What is 25% of 640?
(A) 150  
(B) 160  
(C) 170  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q22.
The Theosophical Society's headquarters in India is located at:
(A) Varanasi  
(B) Adyar, Chennai  
(C) Kolkata  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q23.
Which of the following is correct regarding photoperiodism?
(A) It was discovered by Darwin  
(B) It was discovered by Garner and Allard  
(C) It refers to response of plants to temperature  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q24.
Ginger is botanically classified as:
(A) Root  
(B) Fruit  
(C) Underground stem (rhizome)  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q25.
Which of the following persons from Bihar received the Bharat Ratna?
(A) Dr. Rajendra Prasad  
(B) Jayaprakash Narayan  
(C) Bismillah Khan  
(D) More than one of the above  
(E) None of the above  

---

# ═══════════════════════════════════════════════════════════════════
# 📝 ANSWER KEY — DAY 14
# ═══════════════════════════════════════════════════════════════════

> ✅ Check only after attempting ALL 50. Be honest with yourself!

---

## 💻 CS ANSWERS

| Q# | Answer | Detailed Explanation |
|----|--------|---------------------|
| CS-Q1 | (C) _myVar | `_myVar` starts with underscore — VALID. `2myVar` starts with digit — INVALID. `my-Var` has hyphen — INVALID. |
| CS-Q2 | (C) 5 | `sizeof(x++)` does NOT evaluate x++. x remains 5. y = sizeof(int) = 4, but x is still 5. |
| CS-Q3 | (C) | `delete NULL` is safe — C++ standard guarantees no crash. Does nothing. |
| CS-Q4 | (B) | `new` calls constructor; `malloc` does not. `new` is an operator; `malloc` is a function. `new` returns typed pointer; `malloc` returns void*. |
| CS-Q5 | (B) 4 | Array indices 0 to n-1. For size 5: indices 0,1,2,3,4. Last = arr[4]. |
| CS-Q6 | (C) ios::trunc | `ios::trunc` truncates (empties) the file. `ios::app` appends at end. `ios::ate` moves to end. |
| CS-Q7 | (C) Compile error | `char[]` arrays cannot be concatenated with `+`. This gives a compile error. |
| CS-Q8 | (B) | Specific types first, `catch(...)` last. Otherwise `catch(...)` eats all exceptions. |
| CS-Q9 | (C) | Inline functions: small, simple, frequently-called. NOT for loops/recursion/large functions. |
| CS-Q10 | (B) | Dangling pointer = points to memory that has been freed (deleted). NOT a null pointer. |
| CS-Q11 | (C) | Ctrl+F9 = Compile and Run in Turbo C++. Classic PYQ fact. |
| CS-Q12 | (C) .h | User-defined headers use `.h`. Standard headers use no extension in C++. |
| CS-Q13 | (B) | `delete[]` is for arrays allocated with `new[]`. Mixing them = undefined behavior. |
| CS-Q14 | (B) 11 5 7 | `a++ `uses 4 then a=5; `++b` makes b=7 then uses 7; c = 4+7 = 11. a=5, b=7. |
| CS-Q15 | (C) for | `for` is a reserved keyword — INVALID. `_value` and `Float` (capital F) are valid. |
| CS-Q16 | (C) -1 | ~0 = -(0+1) = -1. Using formula ~n = -(n+1). |
| CS-Q17 | (B) | `ios::app` opens file and moves write position to end, appending data. |
| CS-Q18 | (B) | `is_array()` checks whether a variable/type is of array type. Returns true/false. |
| CS-Q19 | (C) | `catch(...)` is the catch-all handler — catches ANY type of exception. |
| CS-Q20 | (B) | `rank` returns number of dimensions. 2D array → rank = 2. |
| CS-Q21 | (D) More than one | When used with variable, `&` can be address-of operator OR reference depending on context. Both B and C are valid uses! |
| CS-Q22 | (D) More than one | `p = 0`, `p = NULL`, `p = nullptr` — all set pointer to null and prevent dangling. All are valid. |
| CS-Q23 | (C) OK | `delete nullptr` is completely safe; prints "OK". No crash. |
| CS-Q24 | (C) fstream | `ifstream` = read only. `ofstream` = write only. `fstream` = both read and write. |
| CS-Q25 | (B) | `throw;` (without expression) inside a catch block re-throws the current exception. |

---

## 🏛️ GS ANSWERS

| Q# | Answer | Detailed Explanation |
|----|--------|---------------------|
| GS-Q1 | (B) ₹600 | SP = CP × (100+P%)/100 = 500 × 120/100 = ₹600. |
| GS-Q2 | (C) ₹800 | CP = SP × 100/(100-L%) = 720 × 100/90 = ₹800. |
| GS-Q3 | (C) ₹1200 | Total parts = 1+2+3=6. C's share = 2400 × 3/6 = ₹1200. |
| GS-Q4 | (A) 44 | Sum = 6×50=300. After removing 80: 300-80=220. New avg = 220/5 = 44. |
| GS-Q5 | (A) 20% profit | Let CP=100. MP=150. SP=150×80/100=120. Profit=20%. Net formula: 50-20-(50×20/100) = 30-10 = 20%. |
| GS-Q6 | (B) | Immediate cause = greased Enfield cartridges (cow + pig fat). Doctrine of Lapse was political cause. |
| GS-Q7 | (C) Kunwar Singh | Zamindar of Jagdishpur, Bhojpur dist. Bihar's hero of 1857. 80 years old! |
| GS-Q8 | (B) Barrackpore | Mangal Pandey fired the first shot at Barrackpore (March 29, 1857). Meerut uprising was May 10. |
| GS-Q9 | (B) | V.D. Savarkar's book (1909): "The Indian War of Independence 1857" — called it First War of Independence. |
| GS-Q10 | (C) | Brahmo Samaj = Raja Ram Mohan Roy (1828). Arya Samaj = Dayananda Saraswati. Ramakrishna Mission = Vivekananda. |
| GS-Q11 | (C) | Lord William Bentinck abolished Sati in 1829. Dalhousie = Doctrine of Lapse. Curzon = Partition of Bengal 1905. |
| GS-Q12 | (B) | Arya Samaj founded by Dayananda Saraswati (1875). "Back to the Vedas" was his slogan. |
| GS-Q13 | (B) | Ramakrishna Mission founded by Swami Vivekananda (1897) in memory of his guru Ramakrishna. |
| GS-Q14 | (C) Kosi | Kosi River = "Sorrow of Bihar" — causes massive floods every year. |
| GS-Q15 | (C) Bhagalpur | Bhagalpur = "Silk City" — highest silk textile production in Bihar. |
| GS-Q16 | (B) 22 March 1912 | Bihar separated from Bengal on 22 March 1912. Bihar Day is celebrated on 22 March. |
| GS-Q17 | (B) House Sparrow | Bihar's state bird = House Sparrow (Gauriya). NOT Peacock (that's India's national bird). |
| GS-Q18 | (C) Rohtas | Rohtas district = highest paddy/rice production in Bihar. Key BPSC Bihar GK fact. |
| GS-Q19 | (B) Lord Canning | First Viceroy of India (1858). Before 1858, he was last Governor General; after = first Viceroy. |
| GS-Q20 | (B) | Regulating Act 1773 = first Act to regulate EIC + created position of Governor General. Warren Hastings was first. |
| GS-Q21 | (B) 160 | 25% of 640 = (25/100) × 640 = 0.25 × 640 = 160. |
| GS-Q22 | (B) Adyar, Chennai | Theosophical Society HQ = Adyar, Chennai (Madras). Founded 1875; Annie Besant was president. |
| GS-Q23 | (B) | Photoperiodism = plant response to day length. Discovered by Garner and Allard. NOT Darwin. NOT temperature (that's vernalization). |
| GS-Q24 | (C) | Ginger = underground stem (rhizome). Has nodes and internodes — proves it's a stem, not root. |
| GS-Q25 | (D) More than one | ALL THREE — Rajendra Prasad (1962), JP Narayan (1999), Bismillah Khan (2001) — are from Bihar and received Bharat Ratna! |

---

# ═══════════════════════════════════════════════════════════════════
# 🌙 NIGHT REVISION — 5+5 BULLET POINTS (Day 14)
# ═══════════════════════════════════════════════════════════════════

## CS — 5 Must-Remember Points:
```
1. VARIABLE RULES: Cannot start with digit; no spaces; only letters/digits/_; no keywords
   Invalid: 123var, my-var, int, for, while, return

2. NULL POINTER DELETE: delete NULL = SAFE (compiles + runs without crash)
   new calls CONSTRUCTOR; malloc does NOT

3. delete vs delete[]: Single object → delete; Array from new[] → delete[]
   Wrong usage = UNDEFINED BEHAVIOR

4. FILE MODES: ios::trunc = EMPTY the file; ios::app = add at END
   Combine modes with | operator: ios::in | ios::out

5. INLINE FUNCTIONS: SMALL and SIMPLE only; NOT for loops/recursion/large code
   catch(...) must be LAST; specific types catch FIRST
```

## GS — 5 Must-Remember Points:
```
1. PROFIT/LOSS: Always calculated on CP. SP = CP×(100±%)÷100
   Same SP, same profit%=loss% → Always net LOSS. Net Loss% = (%²)/100

2. REVOLT 1857: Immediate cause = Enfield cartridge (greased)
   Kunwar Singh = Bihar hero (Jagdishpur, Bhojpur)
   Mangal Pandey = Barrackpore (FIRST spark)
   After 1857: Crown rule; Viceroy created; Lord Canning = first Viceroy

3. REFORM MOVEMENTS: Brahmo Samaj = Ram Mohan Roy (1828)
   Arya Samaj = Dayananda (1875), Ramakrishna Mission = Vivekananda (1897)
   Sati abolished 1829 by Lord Bentinck

4. BIHAR FACTS: Kosi = Sorrow of Bihar; Bhagalpur = Silk City; Rohtas = Paddy
   State bird = House Sparrow; Bihar Day = 22 March; Districts = 38

5. BHARAT RATNA FROM BIHAR: Rajendra Prasad (1962), JP Narayan (1999), Bismillah Khan (2001)
   All three from Bihar — HIGH BPSC probability question!
```

---

# ═══════════════════════════════════════════════════════════════════
# ⚡ TOPPER TIPS — DAY 14
# ═══════════════════════════════════════════════════════════════════

```
CS TIP 1: "delete NULL" and "sizeof(x++)" are the TWO most common
          output prediction traps in BPSC TRE. Both have appeared
          multiple times. Get them 100% right every time.

CS TIP 2: For file modes — remember the EXTREMES:
          trunc = ZERO (completely empty)
          app   = ADDS at end
          in    = READ only
          out   = WRITE only
          Combine with |

CS TIP 3: The D option "More than one of the above" will come for questions
          like "which of these is a valid way to set a dangling pointer to null"
          — because p=0, p=NULL, p=nullptr are ALL valid.

GS TIP 1: BPSC ALWAYS asks Bihar-specific facts. Memorize:
          Rohtas → Paddy
          Bhagalpur → Silk
          Muzaffarpur → Litchi
          Kosi → Sorrow of Bihar
          These 4 appear almost every paper!

GS TIP 2: For profit-loss questions — NEVER calculate on SP.
          The % is always on CP. This single rule solves 80% of questions.

GS TIP 3: In 1857 — differentiate:
          Mangal Pandey → Barrackpore (first spark, March 29)
          Sepoy Revolt → Meerut (May 10, main revolt started)
          Leader Bihar → Kunwar Singh (Jagdishpur, Bhojpur)
          BPSC mixes these up to trick you!
```

---

*Day 14 Complete — C++ Week Revision Mastery | BPSC TRE 4.0*
*Next up: Day 15 — Arrays as Data Structure + Bihar Geography*
*You are now 14 days in. You are building a winning foundation. Keep going! 🎯*
