# 📅 DAY 12 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
### CS Topic: Exception Handling & Inline Functions | GS Topic: Quit India Movement 1942
**Target: TOP RANK | Prepared for Prag | Phase 1 — Week 2**

---

> **⚡ TOPPER MINDSET FOR TODAY:**
> Exception Handling (`try-catch-throw`) and Inline Functions are **confirmed PYQ topics**
> from TRE 1.0, 2.0 & 3.0 — they appear as direct concept questions AND output-prediction traps.
> Quit India Movement = **"Do or Die"** — highest-scoring Modern History topic in Bihar GS exams.
> Learn both cold today → guaranteed 4–6 marks secured in actual exam.

---

# ═══════════════════════════════════════════
# PART A — COMPUTER SCIENCE
## Exception Handling & Inline Functions — Complete Guide
# ═══════════════════════════════════════════

---

## 🔷 SECTION 1: EXCEPTION HANDLING

---

### 1.1 WHAT IS AN EXCEPTION?

In a program, an **exception** is an **unexpected/abnormal event** that occurs during runtime and disrupts the normal flow of execution.

```
NORMAL PROGRAM FLOW:           EXCEPTION OCCURS:
Statement 1                    Statement 1
Statement 2        VS          Statement 2  ← divide by zero HERE!
Statement 3                    ↓
Statement 4                    PROGRAM CRASHES ❌ (if not handled)
                               OR
                               Exception Handler takes over ✅ (if handled)
```

**Examples of exceptions:**
- Division by zero → `std::runtime_error`
- Array index out of bounds
- File not found
- Memory allocation failure (`std::bad_alloc`)
- Stack overflow from infinite recursion

---

### 1.2 THE THREE KEYWORDS: `try`, `catch`, `throw`

```
┌─────────────────────────────────────────────────────────┐
│  EXCEPTION HANDLING — THREE PILLARS                     │
│                                                         │
│  TRY     → Block where exception MAY occur             │
│  THROW   → Statement that RAISES/SIGNALS the exception │
│  CATCH   → Block that HANDLES the exception            │
└─────────────────────────────────────────────────────────┘
```

### Basic Syntax:

```cpp
try {
    // Code that might cause an exception
    // If something goes wrong, use THROW
    throw value;        // throws an exception
}
catch (type variable) {
    // Code to HANDLE the exception
    // Executes ONLY if matching exception was thrown
}
```

---

### 1.3 COMPLETE FLOW DIAGRAM

```
Program reaches try block
         │
         ▼
   Execute statements in try
         │
    Exception?
    /         \
  NO           YES
  │             │
  │             ▼
  │        throw executes
  │             │
  │             ▼
  │     Matching catch found?
  │        /          \
  │      YES           NO
  │       │             │
  │       ▼             ▼
  │  Execute catch   Program terminates
  │  block           (std::terminate called)
  │       │
  ▼       ▼
  Continue execution after try-catch block
```

---

### 1.4 SIMPLE EXAMPLE — DIVISION BY ZERO

```cpp
#include <iostream>
using namespace std;

int divide(int a, int b) {
    if (b == 0) {
        throw "Division by zero error!";  // throw a string
    }
    return a / b;
}

int main() {
    try {
        cout << divide(10, 2) << endl;   // Output: 5
        cout << divide(8, 0) << endl;    // throws exception!
        cout << "This line never runs";  // SKIPPED after throw
    }
    catch (const char* msg) {            // catches string exceptions
        cout << "Caught: " << msg;       // Output: Caught: Division by zero error!
    }
    cout << "\nProgram continues...";    // This DOES execute
    return 0;
}

/*
OUTPUT:
5
Caught: Division by zero error!
Program continues...
*/
```

> **🎯 KEY INSIGHT:** After `throw`, control immediately jumps to the matching `catch` block. Any statements between `throw` and the end of `try` are **SKIPPED**.

---

### 1.5 MULTIPLE CATCH BLOCKS

You can have **multiple catch blocks** to handle different types of exceptions:

```cpp
#include <iostream>
using namespace std;

int main() {
    int choice = 2;   // Try changing this to 1, 2, or 3

    try {
        if (choice == 1)
            throw 100;          // throws int
        else if (choice == 2)
            throw 3.14;         // throws double
        else
            throw "Error!";     // throws string
    }
    catch (int e) {
        cout << "Integer exception: " << e;    // prints if int thrown
    }
    catch (double e) {
        cout << "Double exception: " << e;     // prints if double thrown
    }
    catch (const char* e) {
        cout << "String exception: " << e;     // prints if string thrown
    }

    return 0;
}

/* When choice = 2:
OUTPUT: Double exception: 3.14
*/
```

**Rule:** Catch blocks are checked **in order from top to bottom**. The FIRST matching one executes.

```
IMPORTANT ORDER RULE:
catch(int)    ← checked FIRST
catch(double) ← checked if int didn't match
catch(...)    ← catches EVERYTHING (must be LAST)
```

---

### 1.6 CATCH-ALL: `catch(...)`

The special syntax `catch(...)` catches **ALL types** of exceptions:

```cpp
try {
    throw 42;           // throws int
}
catch (...) {           // three dots = catch EVERYTHING
    cout << "Some exception occurred!";
}
// Output: Some exception occurred!
```

> **🎯 PYQ CRITICAL:** `catch(...)` with **three dots** catches ALL exception types. It should be placed as the **LAST catch block** — otherwise it will catch everything and prevent specific handlers from running.

```cpp
// CORRECT ORDER:
try { ... }
catch (int e)  { ... }     // specific first
catch (char* e) { ... }    // specific
catch (...) { ... }        // catch-all LAST ✅

// WRONG ORDER (compiler warning/error):
try { ... }
catch (...) { ... }        // catch-all FIRST ❌ — unreachable code below
catch (int e) { ... }      // NEVER reached!
```

---

### 1.7 RE-THROWING AN EXCEPTION

You can **re-throw** the current exception to pass it to an outer catch block:

```cpp
void innerFunction() {
    try {
        throw 100;          // throw original exception
    }
    catch (int e) {
        cout << "Inner caught: " << e << endl;  // handles partially
        throw;                                   // RE-THROW to outer
    }
}

int main() {
    try {
        innerFunction();
    }
    catch (int e) {
        cout << "Outer caught: " << e << endl;  // handles finally
    }
    return 0;
}

/*
OUTPUT:
Inner caught: 100
Outer caught: 100
*/
```

> **🎯 PYQ FACT:** `throw;` (without any value) inside a catch block **re-throws** the current exception to the next enclosing catch block.

---

### 1.8 STANDARD EXCEPTION CLASSES

C++ provides built-in exception classes from `<stdexcept>` and `<exception>`:

```
std::exception (BASE CLASS)
       │
       ├── std::runtime_error    → errors detectable only at runtime
       │         ├── std::overflow_error
       │         ├── std::underflow_error
       │         └── std::range_error
       │
       ├── std::logic_error      → errors in program logic
       │         ├── std::invalid_argument
       │         ├── std::out_of_range
       │         └── std::length_error
       │
       └── std::bad_alloc        → memory allocation failure (new fails)
```

```cpp
#include <stdexcept>
#include <iostream>
using namespace std;

int main() {
    try {
        throw runtime_error("File not found");
    }
    catch (exception& e) {         // catch by reference to base class
        cout << e.what();          // .what() returns error message
    }
    // Output: File not found
}
```

> **🎯 PYQ FACT:** The `.what()` method of `std::exception` returns a C-string (const char*) describing the exception.

---

### 1.9 EXCEPTION HANDLING — KEY RULES SUMMARY

```
┌─────────────────────────────────────────────────────────────────┐
│              EXCEPTION HANDLING RULES — MEMORIZE!               │
├─────────────────────────────────────────────────────────────────┤
│ 1. If no exception occurs → catch blocks are SKIPPED           │
│ 2. If exception is thrown → remaining try code is SKIPPED      │
│ 3. catch blocks checked in ORDER (top to bottom)               │
│ 4. catch(...) catches ALL types — must be LAST                 │
│ 5. throw; (no value) = RE-THROW current exception              │
│ 6. If no catch matches → std::terminate() is called            │
│ 7. Objects created in try are DESTROYED when exception thrown  │
│    (Stack unwinding)                                            │
│ 8. try-catch can be NESTED inside each other                   │
└─────────────────────────────────────────────────────────────────┘
```

---

### 1.10 NESTED TRY-CATCH BLOCKS

```cpp
int main() {
    try {                                    // OUTER try
        cout << "Outer try" << endl;
        try {                                // INNER try
            throw 10;                        // throws int
        }
        catch (int e) {                      // INNER catch
            cout << "Inner caught: " << e << endl;
            throw;                           // re-throws to OUTER catch
        }
    }
    catch (int e) {                          // OUTER catch
        cout << "Outer caught: " << e << endl;
    }
    return 0;
}

/*
OUTPUT:
Outer try
Inner caught: 10
Outer caught: 10
*/
```

---

## 🔷 SECTION 2: INLINE FUNCTIONS

---

### 2.1 THE PROBLEM: FUNCTION CALL OVERHEAD

Every time a regular function is called, the CPU performs several operations:

```
REGULAR FUNCTION CALL OVERHEAD:
─────────────────────────────────────────────────────────
1. Save current state (registers, return address) → PUSH onto stack
2. Jump to function code location in memory
3. Execute function body
4. Restore saved state → POP from stack
5. Return to call point
─────────────────────────────────────────────────────────
For SMALL functions called thousands of times:
→ The OVERHEAD can be MORE expensive than the function itself!
```

---

### 2.2 THE SOLUTION: INLINE FUNCTIONS

An **inline function** tells the compiler to **substitute the function body** directly at each call point — eliminating the overhead:

```
WITHOUT inline:                    WITH inline:
─────────────────                  ──────────────────────────────
main() {                           main() {
  int r = square(5);   →  CALL →    int r = 5 * 5;  // substituted!
  ...                               ...
}                                  }

int square(int x) {                (function body pasted here)
  return x * x;
}
```

### Syntax:

```cpp
// Declare inline function with 'inline' keyword BEFORE return type:
inline int square(int x) {
    return x * x;
}

int main() {
    int a = square(5);   // compiler replaces with: int a = 5 * 5;
    int b = square(3);   // compiler replaces with: int b = 3 * 3;
    cout << a << " " << b;   // Output: 25 9
}
```

---

### 2.3 VISUAL COMPARISON

```
NORMAL FUNCTION:                   INLINE FUNCTION:
─────────────────────────          ─────────────────────────────
CODE in memory:                    CODE in memory:
main:                              main:
  push registers                     a = 5 * 5;      ← body pasted
  call square_func ──────┐           b = 3 * 3;      ← body pasted
  pop registers          │           print a, b;
  ...                    │
square_func:    ←────────┘         (No separate square_func exists!)
  return x * x

→ SLOWER (overhead)                → FASTER (no overhead)
→ SMALLER code size                → LARGER code size (body duplicated)
```

---

### 2.4 WHEN COMPILER IGNORES `inline`

The `inline` keyword is a **REQUEST** to the compiler, not a command. The compiler **ignores** the `inline` request when:

```
COMPILER IGNORES inline WHEN:
──────────────────────────────────────────────────────────
❌ Function is TOO LARGE / COMPLEX
❌ Function contains LOOPS (for, while, do-while)
❌ Function contains SWITCH statements
❌ Function is RECURSIVE
❌ Function contains STATIC variables
❌ Function is called via POINTER TO FUNCTION
❌ Function contains goto statements
──────────────────────────────────────────────────────────
✅ IDEAL for inline: Small, simple, frequently-called functions
   (1–3 lines, no loops, no recursion)
```

> **🎯 PYQ GOLD FACT:** Inline functions are NOT suitable for large, complex functions. The compiler may IGNORE the inline keyword for recursive functions or functions with loops. This is a DIRECT exam question.

---

### 2.5 INLINE vs REGULAR FUNCTION — COMPARISON TABLE

```
┌────────────────────┬──────────────────────┬──────────────────────┐
│ Feature            │ Regular Function     │ Inline Function      │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Overhead           │ Has call overhead    │ NO overhead          │
│ Speed              │ Slower               │ Faster               │
│ Code size          │ Smaller              │ Larger (body copies) │
│ Used for           │ All functions        │ Small, simple only   │
│ Recursion          │ Yes                  │ NOT recommended      │
│ Loops inside       │ Yes                  │ Compiler may ignore  │
│ `inline` keyword   │ Not used             │ Required             │
│ Evaluated at       │ Runtime              │ Compile time         │
└────────────────────┴──────────────────────┴──────────────────────┘
```

---

### 2.6 INLINE FUNCTION WITH CLASS

Inline functions inside a class definition are **automatically inline** (no keyword needed):

```cpp
class Rectangle {
private:
    int length, width;
public:
    Rectangle(int l, int w) : length(l), width(w) {}

    // This is AUTOMATICALLY inline (defined inside class):
    int area() {
        return length * width;
    }

    // This is NOT inline (only declared inside, defined outside):
    int perimeter();
};

// Defined outside — needs explicit inline keyword:
inline int Rectangle::perimeter() {
    return 2 * (length + width);
}
```

> **🎯 PYQ FACT:** A function defined **inside a class definition** is **automatically treated as inline** by the compiler, even without the `inline` keyword.

---

### 2.7 MACRO vs INLINE FUNCTION

This is a **classic BPSC comparison question**:

```
MACRO (#define):               INLINE FUNCTION:
──────────────────────         ─────────────────────────────
#define SQUARE(x) x*x          inline int square(int x) {
                                    return x*x;
                               }

MACRO TRAP:                    INLINE SAFE:
SQUARE(2+3) → 2+3*2+3 = 11!   square(2+3) → (2+3)*(2+3) = 25 ✓
(WRONG ANSWER)                 (CORRECT)

No type checking               Has type checking ✅
Processed by preprocessor      Processed by compiler ✅
Can cause side effects         No side effects ✅
```

> **🎯 KEY ADVANTAGE of inline over macro:** Inline functions have **type checking** and are **safer** than macros because they follow proper C++ evaluation rules.

---

### 2.8 COMPLETE EXAMPLE — try, catch, throw + inline together

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

// Inline function for safe division
inline double safeDivide(double a, double b) {
    if (b == 0)
        throw invalid_argument("Cannot divide by zero!");
    return a / b;
}

int main() {
    double results[3];
    double num[] = {10, 20, 15};
    double den[] = {2, 0, 3};

    for (int i = 0; i < 3; i++) {
        try {
            results[i] = safeDivide(num[i], den[i]);
            cout << "Result[" << i << "] = " << results[i] << endl;
        }
        catch (invalid_argument& e) {
            cout << "Error at index " << i << ": " << e.what() << endl;
            results[i] = 0;
        }
    }
    return 0;
}

/*
OUTPUT:
Result[0] = 5
Error at index 1: Cannot divide by zero!
Result[2] = 5
*/
```

---

### 2.9 MASTER QUICK REFERENCE — CS DAY 12

```
EXCEPTION HANDLING:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
try        → code that MAY throw an exception
throw      → RAISES the exception
catch(T e) → HANDLES exception of type T
catch(...) → catches ALL types (must be LAST)
throw;     → RE-THROWS current exception (no value)
.what()    → returns error message string
terminate()→ called when no catch matches
Stack unwinding → objects destroyed when exception thrown

INLINE FUNCTIONS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
inline keyword → REQUEST to compiler (not a command)
Purpose        → eliminates function call overhead
Good for       → SMALL, SIMPLE, frequently-called
Bad for        → loops, recursion, switch, large code
Auto-inline    → functions defined INSIDE class
Advantage over → macros: type safety, no side effects
```

---

# ═══════════════════════════════════════════
# CS PRACTICE QUESTIONS — 25 MCQs
## Exception Handling & Inline Functions | BPSC TRE Pattern
# ═══════════════════════════════════════════

> **📌 INSTRUCTIONS:** Attempt ALL 25 questions first. Answers are placed AFTER the GS section (after Q50). Use a piece of paper to cover the answer key!

---

**Q1.** In C++ exception handling, which keyword is used to RAISE (signal) an exception?

(A) `catch`
(B) `try`
(C) `throw`
(D) More than one of the above is correct
(E) None of the above

---

**Q2.** What is the purpose of the `try` block in C++ exception handling?

(A) It handles the exception after it is thrown
(B) It encloses the code that might generate an exception
(C) It terminates the program when an exception occurs
(D) More than one of the above is correct
(E) None of the above

---

**Q3.** What is the output of the following C++ code?
```cpp
try {
    throw 10;
    cout << "A";
}
catch (int e) {
    cout << "B" << e;
}
cout << "C";
```
(A) `ABC`
(B) `A B10 C`
(C) `B10C`
(D) More than one of the above is correct
(E) None of the above

---

**Q4.** What does `catch(...)` mean in C++ exception handling?

(A) It catches exceptions of type `char*` only
(B) It is a syntax error
(C) It catches ALL types of exceptions (catch-all handler)
(D) More than one of the above is correct
(E) None of the above

---

**Q5.** Where should `catch(...)` (catch-all) be placed relative to other catch blocks?

(A) First — before all other catch blocks
(B) Last — after all other specific catch blocks
(C) It can be placed anywhere
(D) More than one of the above is correct
(E) None of the above

---

**Q6.** What happens when `throw;` is used inside a catch block (without any value)?

(A) It throws a new integer exception with value 0
(B) It terminates the program immediately
(C) It re-throws the current (same) exception to the next enclosing catch
(D) More than one of the above is correct
(E) None of the above

---

**Q7.** What will be the output of the following code?
```cpp
try {
    throw 3.14;
}
catch (int e) {
    cout << "INT";
}
catch (double e) {
    cout << "DOUBLE";
}
catch (...) {
    cout << "ALL";
}
```
(A) `INT`
(B) `ALL`
(C) `DOUBLE`
(D) More than one of the above is correct
(E) None of the above

---

**Q8.** If an exception is thrown inside a `try` block and NO matching `catch` block is found, what happens?

(A) The exception is silently ignored
(B) The program continues to the next statement after the try-catch
(C) `std::terminate()` is called and the program ends
(D) More than one of the above is correct
(E) None of the above

---

**Q9.** Which method of `std::exception` returns a string describing the exception?

(A) `message()`
(B) `what()`
(C) `describe()`
(D) More than one of the above is correct
(E) None of the above

---

**Q10.** Consider the following code. What is the output?
```cpp
try {
    try {
        throw 100;
    }
    catch (int e) {
        cout << "Inner: " << e << " ";
        throw;
    }
}
catch (int e) {
    cout << "Outer: " << e;
}
```
(A) `Inner: 100`
(B) `Outer: 100`
(C) `Inner: 100 Outer: 100`
(D) More than one of the above is correct
(E) None of the above

---

**Q11.** What is an **inline function** in C++?

(A) A function that is always executed inside the `main()` function
(B) A function whose body is substituted at every call point by the compiler
(C) A function that runs in parallel with other functions
(D) More than one of the above is correct
(E) None of the above

---

**Q12.** What is the PRIMARY advantage of using inline functions?

(A) They reduce code size
(B) They eliminate function call overhead, making execution faster
(C) They allow recursion more efficiently
(D) More than one of the above is correct
(E) None of the above

---

**Q13.** Which of the following functions is BEST suited to be declared as inline?

(A) A recursive function to compute Fibonacci numbers
(B) A function with a `while` loop that reads file data
(C) A small function `int cube(int x) { return x*x*x; }`
(D) More than one of the above is correct
(E) None of the above

---

**Q14.** Under which of the following conditions will the compiler IGNORE the `inline` request?

(A) The function contains a loop
(B) The function is recursive
(C) The function is very large and complex
(D) More than one of the above is correct
(E) None of the above

---

**Q15.** A function defined **inside a class definition** in C++ is:

(A) Always private and cannot be called outside
(B) Automatically treated as inline by the compiler
(C) Required to use the `inline` keyword explicitly
(D) More than one of the above is correct
(E) None of the above

---

**Q16.** What is the MAIN difference between an inline function and a `#define` macro in C++?

(A) Inline functions are slower than macros
(B) Inline functions perform type checking; macros do not
(C) Macros are more reliable and safer than inline functions
(D) More than one of the above is correct
(E) None of the above

---

**Q17.** The `inline` keyword in C++ is:

(A) A mandatory command — the compiler MUST inline the function
(B) A REQUEST/HINT to the compiler; the compiler may choose to ignore it
(C) Used only for member functions of a class
(D) More than one of the above is correct
(E) None of the above

---

**Q18.** What will the following code output?
```cpp
inline int add(int a, int b) {
    return a + b;
}
int main() {
    int x = add(3, 4);
    int y = add(10, 20);
    cout << x << " " << y;
}
```
(A) `3 10`
(B) `7 30`
(C) Compile error — inline functions cannot be used in main
(D) More than one of the above is correct
(E) None of the above

---

**Q19.** Which of the following is/are TRUE about inline functions?

(A) They increase the code size (binary size) because the body is duplicated at each call
(B) They are evaluated at compile time (body inserted at compile time)
(C) They are faster than regular functions because there is no call overhead
(D) More than one of the above is correct
(E) None of the above

---

**Q20.** Consider this macro: `#define SQUARE(x) x*x`
What is `SQUARE(2+3)`?

(A) 25
(B) 11
(C) 10
(D) More than one of the above is correct
(E) None of the above

---

**Q21.** What is the output of the following code?
```cpp
int main() {
    try {
        cout << "Start" << endl;
        throw "Error!";
        cout << "Middle" << endl;
    }
    catch (const char* msg) {
        cout << msg << endl;
    }
    cout << "End" << endl;
    return 0;
}
```
(A) `Start Middle Error! End`
(B) `Start End`
(C) `Start Error! End`
(D) More than one of the above is correct
(E) None of the above

---

**Q22.** Which standard C++ header file contains classes like `runtime_error`, `logic_error`, `invalid_argument`?

(A) `<exception>`
(B) `<error>`
(C) `<stdexcept>`
(D) More than one of the above is correct
(E) None of the above

---

**Q23.** What is "stack unwinding" in the context of exception handling?

(A) A technique to increase stack size dynamically
(B) The process of destroying local objects in reverse order when an exception is thrown
(C) A method to find which catch block matches the thrown exception
(D) More than one of the above is correct
(E) None of the above

---

**Q24.** How does exception handling in C++ affect performance in the **normal** (no exception) case?

(A) It significantly slows down the program even when no exception occurs
(B) Modern compilers implement zero-cost exception handling — minimal overhead when no exception is thrown
(C) It always doubles the execution time
(D) More than one of the above is correct
(E) None of the above

---

**Q25.** Which of the following statements about exception handling AND inline functions is/are CORRECT?

(A) `catch(...)` with three dots catches all exception types and should be last
(B) Inline functions with loops are generally NOT honored by the compiler
(C) `throw;` (without a value) re-throws the current exception
(D) More than one of the above is correct
(E) None of the above

---

---

# ═══════════════════════════════════════════════════════
# PART B — GENERAL STUDIES
## Quit India Movement 1942 — Complete Guide
# ═══════════════════════════════════════════════════════

---

## 🔶 1. BACKGROUND — WHY 1942?

By 1942, India's freedom struggle had reached a **critical turning point**. Several factors made this moment explosive:

```
CHAIN OF EVENTS LEADING TO QUIT INDIA (1942):
══════════════════════════════════════════════════════════

1939 → World War II begins
     → Viceroy Linlithgow declares India at war WITHOUT consulting
       Indian leaders → Congress outraged!
     → Congress ministers resign from provincial governments

1940 → Muslim League's "Pakistan Resolution" at Lahore
     → Jinnah's "Two-Nation Theory" gaining ground

1941 → Japan enters WWII; advancing toward India
     → Subhas Chandra Bose escapes India → forms INA in Southeast Asia

March 1942 → CRIPPS MISSION (Sir Stafford Cripps)
           → British offer: Dominion Status AFTER the war
           → Gandhi called it "a post-dated cheque on a failing bank"
           → Congress rejected it

August 1942 → QUIT INDIA MOVEMENT launched
```

> **🎯 BPSC KEY FACT:** Gandhi called the Cripps Mission offer "a **post-dated cheque on a failing bank**." This rejection led directly to the Quit India Movement.

---

## 🔶 2. THE WARDHA RESOLUTION — DECISION TO LAUNCH

```
Location: Wardha (Gandhi's Sevagram Ashram, Maharashtra)
Date: July 14, 1942
What happened: Congress Working Committee passed the "Quit India" resolution

Key decision:
→ Demand British IMMEDIATELY quit India
→ If refused → launch mass civil disobedience
→ Gandhi to lead the movement
```

---

## 🔶 3. THE BOMBAY SESSION — "DO OR DIE"

```
Location: Gowalia Tank Maidan, Bombay (now August Kranti Maidan)
Date: August 8, 1942 — ALL INDIA CONGRESS COMMITTEE (AICC) meeting
Result: QUIT INDIA RESOLUTION passed unanimously

Gandhi's immortal speech:
"Here is a mantra, a short one, that I give you.
You may imprint it on your hearts and let every breath of yours
give expression to it. The mantra is:
DO OR DIE.
We shall either free India or die in the attempt!"
```

> **🎯 BPSC DIRECT FACT:** The Quit India Resolution was passed on **August 8, 1942** at **Gowalia Tank Maidan, Bombay** (August Kranti Maidan). Gandhi gave the "**Do or Die**" speech here.

---

## 🔶 4. AUGUST 9, 1942 — THE GREAT ARREST

```
British government's response was SWIFT:

August 9, 1942 (the very next morning!):
→ Operation Thunderbolt
→ Gandhi arrested at 5:00 AM from Birla House, Bombay
→ Taken to AGA KHAN PALACE, Pune (place of detention, not a jail)
→ Kasturba Gandhi (wife) also arrested and detained
→ Kasturba died in Aga Khan Palace on February 22, 1944
→ Gandhi's secretary Mahadev Desai also died there (August 15, 1942)

All Congress leaders arrested:
→ Jawaharlal Nehru → Ahmednagar Fort
→ Sardar Vallabhbhai Patel → Ahmednagar Fort
→ Maulana Abul Kalam Azad → Ahmednagar Fort
→ C. Rajagopalachari (Rajaji) → did NOT join (opposed the movement)
```

> **🎯 CRITICAL BPSC FACT:** Gandhi was detained in **Aga Khan Palace, Pune** (not a regular jail). He was released on **May 6, 1944** due to ill health.

---

## 🔶 5. "UNDERGROUND MOVEMENT" — LEADERS WHO ESCAPED

Since all top leaders were arrested, the movement was led by those who managed to escape:

```
UNDERGROUND LEADERS:
──────────────────────────────────────────────────
Jayaprakash Narayan (JP)    → escaped Hazaribagh Jail
                            → became central figure of underground
Aruna Asaf Ali              → hoisted Congress flag at Gowalia Tank
                            → "Heroine of the 1942 movement"
                            → went underground, operated secretly
Ram Manohar Lohia           → underground operations, radio broadcasts
Sucheta Kripalani           → underground work
Usha Mehta                  → operated secret Congress Radio (August 14–Nov 12, 1942)
                              from a secret location in Bombay
```

> **🎯 BPSC SPECIAL:** **Aruna Asaf Ali** hoisted the Congress flag at Gowalia Tank Maidan on August 9, 1942, after Gandhi was arrested. She is called the "**Grand Old Lady of Indian independence**" and "heroine of Quit India."
>
> **Usha Mehta** ran a secret **Congress Radio** from Bombay, broadcasting nationalist messages.

---

## 🔶 6. SPREAD OF THE MOVEMENT — MASS UPRISING

The Quit India Movement became the **most violent** of Gandhi's movements (despite his non-violent intentions):

```
FORMS OF PROTEST ACROSS INDIA:
─────────────────────────────────────────────────
• Hartals (strikes) — shops, factories, transport shut
• Cutting of telegraph wires
• Destruction of railway tracks and stations
• Attacks on government buildings, police stations
• Parallel governments set up in many areas
• Students left colleges and schools
• Peasants refused to pay taxes
```

### Parallel Governments (Parallel Administrations):

| Place | Leader | Period |
|-------|--------|--------|
| **Ballia (UP)** | Chittu Pandey | August 1942 |
| **Satara (Maharashtra)** | Nana Patil | 1943–1945 (longest — "Prati Sarkar") |
| **Tamluk (Bengal/Midnapur)** | Satish Samanta | 1942–1944 |
| **Bhimavaram (Andhra)** | – | Brief period |

> **🎯 PYQ FACT:** The **Satara parallel government** (Prati Sarkar) in Maharashtra under Nana Patil was the **longest-lasting** parallel government during Quit India — it ran until 1945!

---

## 🔶 7. BRITISH REPRESSION

```
BRITISH CRACKDOWN — FACTS:
─────────────────────────────────────────────────────
• Over 100,000 people arrested
• 60,000–70,000 jailed (largest mass arrest in Indian history)
• 1,000+ killed in police/military firing
• Newspapers censored; press freedom suspended
• Military rule imposed in many areas
• Ahmedabad, Bombay, Poona, Patna — heavily repressed
• Bihar and UP saw maximum unrest
```

---

## 🔶 8. ROLE OF SUBHAS CHANDRA BOSE & INA

Simultaneously with Quit India, **Subhas Chandra Bose** was building a parallel liberation force:

```
INA (Indian National Army) TIMELINE:
─────────────────────────────────────────────────────
1941 → Bose escapes India (disguised as Pathan)
     → Goes to Germany; meets Hitler; forms first Indian Legion

1943 → Goes to Southeast Asia via submarine
     → Joins Rash Behari Bose's Indian Independence League

Oct 21, 1943 → Bose establishes "AZAD HIND" government in Singapore
              → Declares India provisionally FREE
              → "Jai Hind!" becomes battle cry
              → "Give me blood, I will give you freedom!"

1944-45 → INA soldiers fight alongside Japanese army
         → Battle of Imphal-Kohima (1944) — reached India's border
         → Hoisted Indian flag on Indian soil (Moirang, Manipur)

1945 → Japan defeated; INA collapses
     → August 18, 1945 → Bose dies in air crash (Taipei, Taiwan)

INA Officers put on Trial (Delhi, 1945-46):
→ "Red Fort Trial" / "INA Trials"
→ Bhulabhai Desai, Jawaharlal Nehru, Tej Bahadur Sapru defended them
→ Sparked MASSIVE public sympathy
→ Led to RIN (Royal Indian Navy) Mutiny, February 1946
```

> **🎯 BPSC KEY FACTS:**
> - Bose's slogan: **"Give me blood, I will give you freedom!"** and **"Jai Hind!"**
> - Azad Hind Government declared: **October 21, 1943** in **Singapore**
> - INA's women's regiment was called **"Rani of Jhansi Regiment"**
> - Bose's title: **"Netaji"**

---

## 🔶 9. END OF QUIT INDIA AND ROAD TO INDEPENDENCE

```
SEQUENCE OF EVENTS TOWARD INDEPENDENCE:
═════════════════════════════════════════════════════════════

1942-44 → Quit India Movement runs
May 1944 → Gandhi released (Aga Khan Palace)
1945 → WWII ends; Labour Party wins in Britain (Clement Attlee)
Feb 1946 → Royal Indian Navy (RIN) Mutiny — British realize
           Indian armed forces can no longer be trusted
1946 → Cabinet Mission Plan (May 1946)
     → Interim Government formed (September 1946)
     → Nehru as Vice President

June 3, 1947 → Mountbatten Plan (Partition announced)
August 14, 1947 → Pakistan Independence
August 15, 1947 → INDIA INDEPENDENT! 🇮🇳
```

---

## 🔶 10. SIGNIFICANCE OF QUIT INDIA MOVEMENT

```
✅ WHY QUIT INDIA WAS A TURNING POINT:
──────────────────────────────────────────────────────────────
1. Showed British they COULD NOT hold India indefinitely
2. Largest mass uprising since 1857 Revolt
3. Demonstrated that ordinary Indians (not just leaders) wanted freedom
4. Parallel governments proved Indians could self-govern
5. International attention — especially from USA (Roosevelt pressured Churchill)
6. Along with INA trials and RIN Mutiny → British realized they MUST leave
7. Women played unprecedented role (Aruna Asaf Ali, Usha Mehta, Sucheta Kripalani)
```

---

## 🔶 11. IMPORTANT PEOPLE — ALL IN ONE TABLE

| Person | Role |
|--------|------|
| **Mahatma Gandhi** | Launched QIM; "Do or Die"; detained in Aga Khan Palace |
| **Jawaharlal Nehru** | Imprisoned in Ahmednagar Fort |
| **Aruna Asaf Ali** | Hoisted Congress flag; "Heroine of 1942" |
| **Usha Mehta** | Ran secret Congress Radio from Bombay |
| **Jayaprakash Narayan** | Led underground movement after escaping jail |
| **Ram Manohar Lohia** | Underground operations |
| **Nana Patil** | Led Satara Prati Sarkar (parallel govt — longest) |
| **Chittu Pandey** | Led Ballia parallel government |
| **Subhas Chandra Bose** | INA; Azad Hind government (parallel) |
| **Kasturba Gandhi** | Died in Aga Khan Palace (Feb 22, 1944) |
| **Lord Linlithgow** | Viceroy who ordered mass arrests |
| **Stafford Cripps** | Led Cripps Mission (rejected by Gandhi) |

---

## 🔶 12. KEY DATES — RAPID FIRE MEMORIZATION

```
July 14, 1942    → Wardha Resolution — CWC decides to launch QIM
August 8, 1942   → Quit India Resolution at Gowalia Tank Maidan, Bombay
                   Gandhi's "Do or Die" speech
August 9, 1942   → Gandhi arrested → Aga Khan Palace, Pune
                   Aruna Asaf Ali hoists Congress flag
Aug 14–Nov 1942  → Usha Mehta's secret Congress Radio broadcasts
August 15, 1942  → Mahadev Desai (Gandhi's secretary) dies in Aga Khan Palace
Feb 22, 1944     → Kasturba Gandhi dies in Aga Khan Palace
May 6, 1944      → Gandhi released due to health
Oct 21, 1943     → Azad Hind Government formed in Singapore (Bose)
Aug 18, 1945     → Bose dies in Taipei (air crash)
Feb 1946         → RIN Mutiny
Aug 15, 1947     → India INDEPENDENT!
```

---

## 🔶 13. COMPARISON OF THREE MAJOR GANDHI MOVEMENTS

| Feature | Non-Cooperation (1920) | Civil Disobedience (1930) | Quit India (1942) |
|---------|----------------------|--------------------------|------------------|
| Launched | August 1, 1920 | March 12, 1930 | August 8, 1942 |
| Key symbol | Khadi | Salt | "Do or Die" |
| Cause | Rowlatt + Jallianwala | Simon + Salt Tax | Cripps rejection + WWII |
| How ended | Chauri Chaura → suspended | Gandhi-Irwin Pact | WWII end + arrests |
| Violence | Minimal → 1 incident | Minimal | Widespread |
| Muslim unity | Strong (Khilafat) | Moderate | Weak (Jinnah opposed) |
| Govt response | Moderate | Moderate | Harshest (1 lakh arrested) |
| Key hero | Ali Brothers | Sarojini Naidu | Aruna Asaf Ali |

---

# ═══════════════════════════════════════════
# GS PRACTICE QUESTIONS — 25 MCQs
## Quit India Movement 1942 | BPSC TRE Pattern
# ═══════════════════════════════════════════

> **📌 INSTRUCTIONS:** Attempt ALL 25 questions first. Answers are placed AFTER question 50 below.

---

**Q26.** The Quit India Resolution was passed by the All India Congress Committee on:

(A) July 14, 1942
(B) August 9, 1942
(C) August 8, 1942
(D) More than one of the above is correct
(E) None of the above

---

**Q27.** At which place was the Quit India Resolution passed?

(A) Wardha, Maharashtra
(B) Gowalia Tank Maidan, Bombay (now August Kranti Maidan)
(C) Sabarmati Ashram, Ahmedabad
(D) More than one of the above is correct
(E) None of the above

---

**Q28.** Gandhi's famous "Do or Die" slogan was associated with which movement?

(A) Non-Cooperation Movement (1920)
(B) Civil Disobedience Movement (1930)
(C) Quit India Movement (1942)
(D) More than one of the above is correct
(E) None of the above

---

**Q29.** After his arrest on August 9, 1942, Gandhi was detained in:

(A) Cellular Jail, Andaman
(B) Yerwada (Yeravda) Jail, Pune
(C) Aga Khan Palace, Pune
(D) More than one of the above is correct
(E) None of the above

---

**Q30.** The Cripps Mission (1942) was rejected by Gandhi. What did he call the British offer?

(A) "A sword aimed at India's heart"
(B) "A post-dated cheque on a failing bank"
(C) "A poisoned gift"
(D) More than one of the above is correct
(E) None of the above

---

**Q31.** Who hoisted the Congress flag at Gowalia Tank Maidan on August 9, 1942, after Gandhi was arrested?

(A) Sarojini Naidu
(B) Kasturba Gandhi
(C) Aruna Asaf Ali
(D) More than one of the above is correct
(E) None of the above

---

**Q32.** Usha Mehta is remembered in the Quit India Movement for:

(A) Leading the underground movement in Bihar
(B) Running a secret Congress Radio from Bombay (August–November 1942)
(C) Hoisting the Congress flag at Gowalia Tank
(D) More than one of the above is correct
(E) None of the above

---

**Q33.** The longest-lasting parallel government (Prati Sarkar) during the Quit India Movement was established at:

(A) Ballia, Uttar Pradesh
(B) Tamluk, Bengal
(C) Satara, Maharashtra
(D) More than one of the above is correct
(E) None of the above

---

**Q34.** Who led the Satara Prati Sarkar (parallel government) during the Quit India Movement?

(A) Chittu Pandey
(B) Satish Samanta
(C) Nana Patil
(D) More than one of the above is correct
(E) None of the above

---

**Q35.** Subhas Chandra Bose established the Azad Hind Government on:

(A) August 15, 1942
(B) October 21, 1943
(C) January 26, 1943
(D) More than one of the above is correct
(E) None of the above

---

**Q36.** Where was the Azad Hind Government established by Subhas Chandra Bose?

(A) Berlin, Germany
(B) Tokyo, Japan
(C) Singapore
(D) More than one of the above is correct
(E) None of the above

---

**Q37.** Which famous slogan is associated with Subhas Chandra Bose?

(A) "Do or Die"
(B) "Give me blood, I will give you freedom!"
(C) "Swaraj is my birthright"
(D) More than one of the above is correct
(E) None of the above

---

**Q38.** The women's regiment of the Indian National Army (INA) was named after:

(A) Savitribai Phule
(B) Rani of Jhansi (Rani Lakshmibai)
(C) Kasturba Gandhi
(D) More than one of the above is correct
(E) None of the above

---

**Q39.** Kasturba Gandhi (Gandhi's wife) died during his detention in Aga Khan Palace on:

(A) August 15, 1942
(B) February 22, 1944
(C) May 6, 1944
(D) More than one of the above is correct
(E) None of the above

---

**Q40.** Jayaprakash Narayan (JP) became a central figure of the underground Quit India Movement after:

(A) Escaping from Ahmednagar Fort
(B) Escaping from Hazaribagh Jail
(C) Escaping from Cellular Jail, Andaman
(D) More than one of the above is correct
(E) None of the above

---

**Q41.** The Wardha Resolution (July 14, 1942) was passed by the:

(A) All India Congress Committee (AICC)
(B) Muslim League
(C) Congress Working Committee (CWC)
(D) More than one of the above is correct
(E) None of the above

---

**Q42.** Which of the following leaders was NOT imprisoned during the Quit India Movement?

(A) Jawaharlal Nehru
(B) Sardar Vallabhbhai Patel
(C) C. Rajagopalachari (Rajaji)
(D) More than one of the above is correct
(E) None of the above

---

**Q43.** The Ballia parallel government during Quit India 1942 was led by:

(A) Nana Patil
(B) Ram Manohar Lohia
(C) Chittu Pandey
(D) More than one of the above is correct
(E) None of the above

---

**Q44.** The Royal Indian Navy (RIN) Mutiny of February 1946 was significant because:

(A) It was the last major armed rebellion before independence
(B) It showed the British that the Indian armed forces could no longer be relied upon to maintain colonial rule
(C) It was led by Subhas Chandra Bose from Singapore
(D) More than one of the above is correct
(E) None of the above

---

**Q45.** INA officers were put on trial at the Red Fort, Delhi in 1945–46. Who among the following defended them?

(A) Jawaharlal Nehru
(B) Bhulabhai Desai
(C) Tej Bahadur Sapru
(D) More than one of the above is correct
(E) None of the above

---

**Q46.** Subhas Chandra Bose died on:

(A) August 15, 1945 (India's Independence Day)
(B) August 18, 1945, in a plane crash in Taipei, Taiwan
(C) October 21, 1945, in Singapore
(D) More than one of the above is correct
(E) None of the above

---

**Q47.** Which of the following about the Quit India Movement is/are TRUE?

(A) It was the largest mass uprising in India since the 1857 revolt
(B) Over 1 lakh (100,000) people were arrested
(C) Women like Aruna Asaf Ali and Usha Mehta played leading roles
(D) More than one of the above is correct
(E) None of the above

---

**Q48.** Gandhi was released from Aga Khan Palace on:

(A) February 22, 1944
(B) August 15, 1944
(C) May 6, 1944
(D) More than one of the above is correct
(E) None of the above

---

**Q49.** The INA's famous battle cry / slogan was:

(A) "Do or Die"
(B) "Inqilab Zindabad"
(C) "Jai Hind"
(D) More than one of the above is correct
(E) None of the above

---

**Q50.** Which of the following correctly describes the significance of the Quit India Movement?

(A) It demonstrated to the British that India could not be held indefinitely
(B) Parallel governments in Satara, Ballia, and Tamluk proved Indians could self-govern
(C) International pressure (especially from USA) increased on Britain to free India
(D) More than one of the above is correct
(E) None of the above

---
---
---
---
---

# ═══════════════════════════════════════════════════════
# ✅ ANSWER KEY — CHECKED YOUR OWN ANSWERS FIRST? ✅
# ═══════════════════════════════════════════════════════

---

## CS ANSWERS (Q1–Q25) — Exception Handling & Inline Functions

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| **Q1** | **(C) `throw`** | `throw` is used to RAISE/signal an exception |
| **Q2** | **(B) Encloses code that might generate an exception** | `try` = the guarded region |
| **Q3** | **(C) `B10C`** | `throw 10` skips `cout<<"A"` → catch prints `B10` → then `C` prints (after try-catch) |
| **Q4** | **(C) Catches ALL types** | `catch(...)` with three dots = universal catch-all handler |
| **Q5** | **(B) Last** | `catch(...)` must be LAST; if placed first, specific handlers are unreachable |
| **Q6** | **(C) Re-throws current exception** | `throw;` with no value = re-throw to outer enclosing catch |
| **Q7** | **(C) `DOUBLE`** | `3.14` is a `double`; matching `catch(double)` fires |
| **Q8** | **(C) `std::terminate()` called** | If no matching catch found → `std::terminate()` → program ends |
| **Q9** | **(B) `what()`** | `e.what()` returns the error description string |
| **Q10** | **(C) `Inner: 100 Outer: 100`** | Inner catches and prints, then `throw;` re-throws to outer |
| **Q11** | **(B) Body substituted at call point** | Compiler pastes function body where it is called |
| **Q12** | **(B) Eliminates function call overhead** | Faster execution — no push/pop/jump overhead |
| **Q13** | **(C) `int cube(int x) { return x*x*x; }`** | Small, simple, no loops, no recursion — perfect for inline |
| **Q14** | **(D) More than one** | All three (A), (B), (C) are valid reasons to ignore inline |
| **Q15** | **(B) Automatically treated as inline** | Functions defined inside class body are implicitly inline |
| **Q16** | **(B) Inline functions perform type checking** | Key advantage: type safety + correct operator precedence |
| **Q17** | **(B) A REQUEST/HINT to compiler** | Compiler may choose to ignore `inline` keyword |
| **Q18** | **(B) `7 30`** | `add(3,4)=7`, `add(10,20)=30`; inline works normally |
| **Q19** | **(D) More than one** | All three (A), (B), (C) are TRUE about inline functions |
| **Q20** | **(B) 11** | Macro expansion: `2+3*2+3 = 2+6+3 = 11` (not 25!) — classic trap |
| **Q21** | **(C) `Start Error! End`** | `throw "Error!"` skips "Middle"; catch prints "Error!"; then "End" |
| **Q22** | **(C) `<stdexcept>`** | `runtime_error`, `logic_error`, etc. are in `<stdexcept>` |
| **Q23** | **(B) Destroying local objects in reverse order** | Stack unwinding = cleanup of local objects when exception propagates |
| **Q24** | **(B) Minimal overhead (zero-cost exception handling)** | Modern compilers optimize for no-exception path |
| **Q25** | **(D) More than one** | All three (A), (B), (C) are correct statements |

---

## GS ANSWERS (Q26–Q50) — Quit India Movement 1942

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| **Q26** | **(C) August 8, 1942** | AICC session at Gowalia Tank Maidan; Wardha (July 14) was CWC meeting |
| **Q27** | **(B) Gowalia Tank Maidan, Bombay** | Now called August Kranti Maidan |
| **Q28** | **(C) Quit India Movement (1942)** | "Do or Die" = Gandhi's August 8, 1942 speech |
| **Q29** | **(C) Aga Khan Palace, Pune** | NOT a regular jail — a palace used as detention center |
| **Q30** | **(B) "Post-dated cheque on a failing bank"** | Gandhi's exact famous quote about Cripps Mission |
| **Q31** | **(C) Aruna Asaf Ali** | "Heroine of 1942" — hoisted flag after Gandhi's arrest |
| **Q32** | **(B) Secret Congress Radio** | Broadcast nationalist messages Aug 14 – Nov 12, 1942 |
| **Q33** | **(C) Satara, Maharashtra** | Prati Sarkar — longest lasting parallel government (1943–1945) |
| **Q34** | **(C) Nana Patil** | Led the Satara Prati Sarkar |
| **Q35** | **(B) October 21, 1943** | Azad Hind Government declared in Singapore |
| **Q36** | **(C) Singapore** | Bose declared provisional Azad Hind Govt in Singapore |
| **Q37** | **(B) "Give me blood, I will give you freedom!"** | Bose's most famous slogan |
| **Q38** | **(B) Rani of Jhansi** | Women's regiment of INA = Rani of Jhansi Regiment |
| **Q39** | **(B) February 22, 1944** | Kasturba died in Aga Khan Palace detention |
| **Q40** | **(B) Escaping Hazaribagh Jail** | JP became underground hero after this escape |
| **Q41** | **(C) Congress Working Committee (CWC)** | Wardha = CWC meeting (not full AICC); Aug 8 = AICC |
| **Q42** | **(C) C. Rajagopalachari (Rajaji)** | Rajaji OPPOSED the Quit India Movement and was not imprisoned |
| **Q43** | **(C) Chittu Pandey** | Led Ballia (UP) parallel government, August 1942 |
| **Q44** | **(B) British could not rely on Indian armed forces** | RIN Mutiny was decisive signal for British to leave |
| **Q45** | **(D) More than one** | Nehru, Bhulabhai Desai, AND Sapru all defended INA officers |
| **Q46** | **(B) August 18, 1945 in Taipei, Taiwan** | Plane crash over Taiwan (Japan) |
| **Q47** | **(D) More than one** | All three (A), (B), (C) are TRUE |
| **Q48** | **(C) May 6, 1944** | Released due to failing health (malaria) |
| **Q49** | **(C) "Jai Hind"** | INA's battle cry; Bose made it India's national salute |
| **Q50** | **(D) More than one** | All three (A), (B), (C) are correct about QIM significance |

---

# ═══════════════════════════════════════════
# 📝 NIGHT REVISION — 5 BULLET POINTS EACH
## Write from Memory Before Sleeping
# ═══════════════════════════════════════════

### CS — Exception Handling & Inline:
1. **`try`** = guarded zone; **`throw`** = raises exception; **`catch`** = handles it; after `throw`, remaining `try` code is **SKIPPED**
2. **`catch(...)`** (three dots) = catches ALL types; MUST be the **LAST** catch block
3. **`throw;`** (no value) inside catch = **re-throws** same exception to outer catch block
4. **Inline functions** = body substituted at call point; compiler **IGNORES** inline for loops, recursion, complex functions
5. **Macro trap:** `#define SQUARE(x) x*x` → `SQUARE(2+3)` = 11 (not 25!); inline is safer due to **type checking**

### GS — Quit India Movement:
1. **August 8, 1942** = Quit India Resolution at **Gowalia Tank Maidan, Bombay**; Gandhi's **"Do or Die"** speech
2. **August 9, 1942** = Gandhi arrested → **Aga Khan Palace, Pune** (not a jail!); **Aruna Asaf Ali** hoisted Congress flag
3. **Cripps Mission** = "post-dated cheque on failing bank" (Gandhi); **Satara Prati Sarkar** (Nana Patil) = longest parallel govt
4. **Azad Hind Govt** = Oct 21, 1943, **Singapore**; Bose: "Give me blood, I will give you freedom!"; INA women's wing = **Rani of Jhansi Regiment**
5. **Bihar connection:** Rajendra Prasad + Jayaprakash Narayan (escaped Hazaribagh Jail) — Bihar's freedom fighters in QIM

---

# 📊 DAY 12 PERFORMANCE TRACKER

| Section | Questions | Target Score | My Score |
|---------|-----------|-------------|----------|
| CS — Exception + Inline | 25 | 22+ | _______ |
| GS — Quit India Movement | 25 | 22+ | _______ |
| **Total** | **50** | **44+** | _______ |

**If score < 38/50:** Re-read 🎯 flagged facts; redo wrong questions tomorrow morning.
**If score 38–45/50:** Good performance — review mistakes, proceed to Day 13.
**If score 46–50/50:** TOPPER LEVEL! 🏆 TOP RANK is yours!

---

> **⚡ PREVIEW — DAY 13:**
> CS: Output Prediction Questions (bitwise operators, pre/post increment, struct vs class, scope resolution `::`),
> GS: Bihar History — Rajendra Prasad (first President, Champaran hero, CDM + QIM leader)
> **Today's D-option tally:** Q14, Q19, Q25, Q44, Q45, Q47, Q50 were all "More than one" — that's 7/25 in GS alone!
> Always evaluate ALL options before marking (A), (B), or (C)!

---

*Day 12 Complete | Next → Day 13: Output Prediction + Bihar History (Rajendra Prasad)*
*Phase 1, Week 2 | April 2026 | Target: 130+/150 | BPSC TRE 4.0 TOP RANK*
