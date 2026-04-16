# 📅 BPSC TRE 4.0 — DAY 12 COMPLETE STUDY MODULE
### C++ Exception Handling & Inline Functions + Quit India Movement 1942
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Exception Handling (try/catch/throw) + Inline Functions
> - Afternoon (1 hr): Quit India Movement — story-based deep understanding
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 C++ Exception Handling & Inline Functions

---

# ═══════════════════════════════════
# TOPIC A: EXCEPTION HANDLING
# ═══════════════════════════════════

## 🔷 SECTION 1: What is an Exception? (The Foundation)

### Real-Life Analogy — The ATM Machine:
```
Normal Flow (no exception):
  You insert card → Enter PIN → Withdraw money → Done ✅

Exceptional Flow (exception occurs):
  You insert card → Enter PIN → Machine says "Insufficient Balance!"
  → Normal flow BREAKS
  → Error must be HANDLED
  → You get an error message instead of cash

In programming:
  "Exception" = an UNEXPECTED event during program execution
                that DISRUPTS the normal flow of the program

Without exception handling:
  → Program CRASHES with an ugly error
  → No useful message to the user
  → Data may be corrupted

With exception handling:
  → Error is CAUGHT gracefully
  → User sees a meaningful message
  → Program can continue or shut down safely
```

### Technical Definition:
> An **exception** is a runtime error or unexpected condition that interrupts the normal execution of a program. Exception handling is the mechanism to **detect, signal, and respond** to these conditions.

### Types of Errors in C++ (Context):
```
Compile-time errors → Syntax mistakes → Fixed before running
Runtime errors      → Happen during execution → Handled by exceptions
Logic errors        → Wrong logic → Must be found by testing

Exception handling deals with RUNTIME ERRORS.
```

---

## 🔷 SECTION 2: The Three Keywords — try, catch, throw

### The Core Mechanism:
```
THROW  = "Something went wrong! I'm signalling the error"
TRY    = "Watch this block of code — it might throw an exception"
CATCH  = "If an exception was thrown, handle it here"
```

### Syntax:
```cpp
try {
    // Code that might throw an exception
    // If something goes wrong, throw is used
    throw exceptionValue;    // signals the exception
}
catch (ExceptionType variable) {
    // Code to handle the exception
    // This block runs if throw threw ExceptionType
}
```

### Simple Example — Division by Zero:
```cpp
#include <iostream>
using namespace std;

int divide(int a, int b) {
    if (b == 0) {
        throw "Division by zero error!";   // throw a string
    }
    return a / b;
}

int main() {
    try {
        int result = divide(10, 0);        // this will throw
        cout << result;                    // NEVER reached
    }
    catch (const char* msg) {             // catches string exception
        cout << "Error: " << msg;         // Output: Error: Division by zero error!
    }
    cout << "Program continues...";       // This IS reached
    return 0;
}
```

### Flow of Control — Visual:
```
EXCEPTION HANDLING FLOW:
════════════════════════════════════════════════════════

Program starts → Enters try block
                     │
                     ▼
            Executes statements
                     │
            ┌────────┴─────────┐
            │                  │
    No exception           Exception thrown
            │                  │
            ▼                  ▼
    try block completes    Stack unwinds
    (catch skipped)        Matching catch found?
            │                  │
            │            ┌─────┴──────┐
            │            │            │
            │         YES: catch    NO: terminate()
            │         executes      called (crash)
            │            │
            └────────────┤
                         │
                  Code AFTER
                  try-catch block
                  continues

════════════════════════════════════════════════════════
```

---

## 🔷 SECTION 3: throw — Signalling Exceptions

### What Can Be Thrown?
```cpp
// You can throw ANY type in C++:
throw 42;                     // throw int
throw 3.14;                   // throw double
throw "Error message";        // throw string literal (const char*)
throw std::string("Error");   // throw std::string
throw std::runtime_error("msg"); // throw exception object (best practice)

// Throw custom class objects:
class MyException {
public:
    string message;
    MyException(string m) : message(m) {}
};
throw MyException("Custom error");
```

### throw in a Function:
```cpp
void checkAge(int age) {
    if (age < 0) throw -1;         // throw int
    if (age > 150) throw "Too old"; // throw string
    cout << "Valid age: " << age;
}
```

### 🚨 PYQ TRAP #1 — throw outside try:
```cpp
// If throw is executed OUTSIDE a try block (or no matching catch):
// → terminate() is called
// → Program crashes (abnormal termination)

// If throw is inside try but NO matching catch exists:
// → Exception propagates up the call stack
// → If STILL no catch found → terminate() called
```

---

## 🔷 SECTION 4: catch — Handling Exceptions

### Basic catch Syntax:
```cpp
catch (int e) {
    cout << "Integer exception: " << e;
}

catch (const char* e) {
    cout << "String exception: " << e;
}

catch (double e) {
    cout << "Double exception: " << e;
}
```

### Multiple catch Blocks:
```cpp
try {
    int choice = 2;
    if (choice == 1) throw 100;         // throw int
    if (choice == 2) throw 3.14;        // throw double
    if (choice == 3) throw "Error!";    // throw string
}
catch (int e) {
    cout << "Caught int: " << e;
}
catch (double e) {
    cout << "Caught double: " << e;    // THIS executes (choice==2)
}
catch (const char* e) {
    cout << "Caught string: " << e;
}
```

### 🚨 PYQ TRAP #2 — Multiple catch order:
```cpp
// WRONG ORDER — derived class after base class:
try {
    throw std::runtime_error("msg");
}
catch (std::exception& e) {    // BASE class — catches EVERYTHING
    cout << "Exception caught";
}
catch (std::runtime_error& e) { // ⚠️ NEVER REACHED — already caught above!
    cout << "Runtime error";
}

// CORRECT ORDER — derived (specific) before base (general):
try {
    throw std::runtime_error("msg");
}
catch (std::runtime_error& e) { // specific first
    cout << "Runtime error";   // THIS executes
}
catch (std::exception& e) {    // general fallback
    cout << "Some exception";
}

// RULE: Most specific (derived) catch blocks FIRST,
//       Most general (base class) catch blocks LAST
```

---

## 🔷 SECTION 5: catch(...) — The Catch-All Handler

### Syntax and Usage:
```cpp
try {
    throw 42;    // could throw anything
}
catch (...) {    // catches EVERYTHING regardless of type
    cout << "Some exception caught — type unknown";
}
```

### 🚨 PYQ TRAP #3 — catch(...) placement:
```cpp
// catch(...) MUST always be the LAST catch block:
try {
    throw "hello";
}
catch (...) {           // ❌ WRONG — placed first
    cout << "Catch all";
}
catch (const char* e) { // ⚠️ NEVER REACHED
    cout << e;
}

// CORRECT:
try {
    throw "hello";
}
catch (const char* e) { // specific types first
    cout << e;          // THIS executes
}
catch (...) {           // ✅ catch-all LAST
    cout << "Catch all fallback";
}
```

### Why catch(...) is Useful:
```
1. When you don't know what type of exception might be thrown
2. As a safety net to prevent program crash from uncaught exceptions
3. For cleanup code (logging, releasing resources)
```

---

## 🔷 SECTION 6: Rethrowing Exceptions

### What is Rethrowing?
> Catching an exception in one handler and then **throwing it again** to be caught by an outer handler.

### Syntax:
```cpp
try {
    try {
        throw 100;              // inner throw
    }
    catch (int e) {
        cout << "Inner catch: " << e << endl;
        throw;                  // RETHROW — no argument needed!
                                // re-throws the SAME exception (100)
    }
}
catch (int e) {
    cout << "Outer catch: " << e << endl;  // Output: Outer catch: 100
}
```

### 🚨 PYQ TRAP #4 — throw vs throw e:
```cpp
catch (int e) {
    throw;    // ✅ Rethrows ORIGINAL exception (same object, no copy)
              // Preserves exception type (important for polymorphism)

    throw e;  // ⚠️ Creates a NEW copy of e and throws it
              // May cause slicing if e is a derived class object!
}
// For rethrowing, ALWAYS use bare "throw;" without argument
```

### When to Rethrow?
```
→ When current catch can partially handle the error
→ When logging or recording the error before passing it up
→ When outer function must also know about the error
→ In cleanup operations that need to propagate errors
```

---

## 🔷 SECTION 7: Stack Unwinding

### What Happens When Exception is Thrown?
```
Stack unwinding = the process of destroying local objects
                  and exiting functions as the exception
                  propagates back through the call stack

Example:
  main() calls func1()
  func1() calls func2()
  func2() calls func3()
  func3() throws exception

Without matching catch in func3:
  → func3 exits (local objects destroyed)
  → func2 exits (local objects destroyed)
  → func1 exits (local objects destroyed)
  → main() has the catch → exception is caught here

This UNWINDING ensures destructors are called for local objects!
```

```
STACK UNWINDING VISUAL:
main()  ←── catch block here
  │
  └── func1()
        │
        └── func2()
               │
               └── func3()  ← throw happens here
                   ↑ unwind (func3 exits)
               ↑ unwind (func2 exits)
          ↑ unwind (func1 exits)
     catch in main() catches the exception
```

---

## 🔷 SECTION 8: Standard Exception Classes

### C++ Standard Exception Hierarchy:
```
std::exception (base — in <stdexcept>)
├── std::logic_error
│   ├── std::invalid_argument
│   ├── std::domain_error
│   ├── std::length_error
│   └── std::out_of_range
├── std::runtime_error
│   ├── std::overflow_error
│   ├── std::underflow_error
│   └── std::range_error
├── std::bad_alloc          (thrown by new on failure)
├── std::bad_cast           (thrown by dynamic_cast)
└── std::bad_typeid         (thrown by typeid on null pointer)
```

### 🚨 PYQ TRAP #5 — bad_alloc:
```cpp
try {
    int* p = new int[1000000000];  // request huge memory
}
catch (std::bad_alloc& e) {        // catches memory allocation failure
    cout << "Memory allocation failed: " << e.what();
}
// new throws std::bad_alloc when memory is insufficient
// malloc returns NULL (no exception) — key difference!
```

---

## 🔷 SECTION 9: Exception Handling Complete Example
```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

double safeDivide(double a, double b) {
    if (b == 0)
        throw std::runtime_error("Division by zero");
    return a / b;
}

int main() {
    try {
        cout << safeDivide(10, 2) << endl;    // Output: 5
        cout << safeDivide(10, 0) << endl;    // throws!
        cout << "This line never runs" << endl;
    }
    catch (std::runtime_error& e) {
        cout << "Runtime error: " << e.what() << endl;
        // Output: Runtime error: Division by zero
    }
    catch (...) {
        cout << "Unknown exception caught" << endl;
    }
    cout << "Program ends normally" << endl;
    return 0;
}
```

---

# ═══════════════════════════════════
# TOPIC B: INLINE FUNCTIONS
# ═══════════════════════════════════

## 🔷 SECTION 10: What is an Inline Function?

### The Problem — Function Call Overhead:
```
Every time a function is called in C++, the CPU must:
  1. Save current state (registers, return address) → push to stack
  2. Jump to function code location in memory
  3. Execute function code
  4. Restore saved state → pop from stack
  5. Jump back to where function was called

This overhead is TINY for large functions (worth it).
But for very SMALL functions (1-2 lines), this overhead
can be LARGER than the actual work done!

Example: A function that just adds two numbers:
int add(int a, int b) { return a + b; }
The "return a+b" takes 1 step.
The call overhead takes 5 steps.
→ 5 steps of overhead for 1 step of work = inefficient!
```

### The Solution — Inline Function:
```
Inline function = "Don't call the function — just INSERT the
                  function's code directly at the call site"

The COMPILER replaces the function call with the actual code.
No call overhead. No stack operations. Just the code runs.

Think of it as: COPY-PASTE the function body at every call point
```

### Real-Life Analogy:
```
Without inline (regular function):
  Recipe says: "Make the sauce using Recipe #47 on page 82"
  → You stop, go to page 82, make sauce, come back
  → Time wasted travelling between pages

With inline function:
  Recipe has the sauce instructions printed RIGHT HERE:
  "Add 2 tbsp tomato paste, 1 tsp salt, stir for 2 min"
  → No page-flipping needed — everything is right here!
```

---

## 🔷 SECTION 11: Syntax and Usage

### Declaring an Inline Function:
```cpp
// keyword 'inline' before return type:
inline int add(int a, int b) {
    return a + b;
}

inline int square(int x) {
    return x * x;
}

inline void greet() {
    cout << "Hello!";
}
```

### How the Compiler Handles It:
```cpp
// Source code:
inline int square(int x) { return x * x; }

int main() {
    int a = square(5);   // call to inline function
    int b = square(3);   // another call
}

// What compiler generates (conceptually):
int main() {
    int a = 5 * 5;       // code SUBSTITUTED directly (no call!)
    int b = 3 * 3;       // code SUBSTITUTED again
}
// The function square() is "inlined" = inserted at call site
```

### Inline vs Regular Function — Visual:
```
REGULAR FUNCTION CALL:
main() code...
CALL square(5) ──────────────────────→ [square function]
               ←──────────────────── return 25
main() code continues...

          Stack frame created/destroyed — OVERHEAD!

INLINE FUNCTION:
main() code...
a = 5 * 5;  ← CODE DIRECTLY HERE (no jump, no stack!)
main() code continues...

          No overhead — just the computation!
```

---

## 🔷 SECTION 12: When Inline Works vs When Compiler IGNORES It

### `inline` is a REQUEST, Not a Command:
```
The inline keyword is a HINT/REQUEST to the compiler.
The compiler may IGNORE it and treat the function as regular.

inline keyword = "Please compiler, make this inline"
Compiler may say: "No, it's too complex. I'll ignore that."
```

### When Inline is SUITABLE (Compiler will likely honor):
```
✅ Very short functions (1–3 lines)
✅ Simple computations (add, multiply, compare)
✅ Functions called very frequently in tight loops
✅ Accessor/getter functions in classes
✅ No loops, no recursion, no complex control flow
```

### When Inline is IGNORED by Compiler:
```
❌ Functions with loops (for, while, do-while)
❌ Recursive functions ← VERY IMPORTANT PYQ TRAP
❌ Functions with large bodies (too many lines)
❌ Functions containing static variables
❌ Functions with complex control flow (multiple branches)
❌ Virtual functions (generally — they need runtime dispatch)
❌ Functions whose address is taken (&funcName)
```

### 🚨 PYQ TRAP #6 — Recursive inline:
```cpp
inline int factorial(int n) {  // marked as inline
    if (n <= 1) return 1;
    return n * factorial(n-1); // RECURSIVE call!
}
// Compiler CANNOT inline this — recursion can't be expanded!
// Would require infinite substitution (factorial calls factorial calls...)
// Compiler IGNORES the inline keyword here
// Function is treated as a REGULAR function
```

### 🚨 PYQ TRAP #7 — Inline is compile-time:
```cpp
// Inline expansion happens at COMPILE TIME
// Regular function calls resolved at RUNTIME (linker)
// Inline functions are usually defined in HEADER FILES
// (because compiler needs to see the body at each call site)
```

---

## 🔷 SECTION 13: Advantages and Disadvantages of Inline

### Advantages:
```
✅ Eliminates function call overhead
✅ Faster execution for small, frequently called functions
✅ Compiler can optimize the substituted code better
✅ No stack frame creation/destruction
```

### Disadvantages:
```
❌ CODE BLOAT: Code size INCREASES
   → If inline function called 100 times, its code appears 100 times
   → Regular function: code exists once, called 100 times
   → Trade-off: speed (inline) vs memory (regular)

❌ Not suitable for large functions (bloat outweighs benefit)
❌ Recompilation needed when inline function changes
❌ Debugging can be harder (no single function location)
```

### 🚨 PYQ TRAP #8 — The Size Trade-off:
```
Inline → FASTER execution BUT LARGER code size
Regular → SLOWER execution BUT SMALLER code size

Key insight for exam:
"Inline functions increase code size but decrease execution time"
This trade-off is THE most tested fact about inline functions.
```

---

## 🔷 SECTION 14: Inline Functions in Classes

### Member Functions Defined Inside Class = Automatically Inline:
```cpp
class Rectangle {
public:
    int length, width;

    // Defined inside class = AUTOMATICALLY inline (no keyword needed):
    int area() {
        return length * width;   // ← implicitly inline
    }

    // Defined outside class with inline keyword:
    inline int perimeter();
};

inline int Rectangle::perimeter() {
    return 2 * (length + width);
}
```

### 🚨 PYQ TRAP #9:
> **Member functions defined inside the class body are automatically inline.**
> You don't need to write the `inline` keyword explicitly.
> This is a very commonly tested fact!

---

## 📊 VISUAL SUMMARY — Exception Handling + Inline

```
EXCEPTION HANDLING FLOW:
try { code } → throw X → find matching catch(X) → execute catch
                       → no match found → terminate()
                       → catch(...) → always matches

ORDER RULES:
1. Specific catch blocks BEFORE general ones
2. catch(...) MUST be LAST
3. throw; (bare) = rethrow original | throw e; = rethrow copy

INLINE FUNCTION:
Keyword: inline returnType funcName(params) { small body }
Effect:  Compiler INSERTS code at call site (no function call)
Honored: Short, simple, non-recursive functions
Ignored: Loops, recursion, large body, virtual, static vars
Trade-off: FASTER but LARGER code size
Auto-inline: Member functions defined inside class body
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Quit India Movement (1942) — Story-Based Deep Dive

---

## 🔷 THE BACKGROUND — TWO TRIGGERS

### Background 1: World War II Context (1939–1942)
```
September 1939: WWII begins in Europe
                Britain declares war on Germany

India's position:
→ Viceroy Lord Linlithgow declared India at war with Germany
   WITHOUT CONSULTING Indian leaders — unilaterally!
→ INC was outraged: "India's resources used for Britain's war
   without India's consent"
→ Congress demanded Independence BEFORE supporting war
→ Muslims League: Wanted assurances for Muslims first

Congress Provincial Governments RESIGNED (October 1939):
→ Congress ministries in 7 provinces resigned in protest
→ Muslim League celebrated this as "Day of Deliverance"
   (December 22, 1939) — Jinnah was relieved Congress left power
```

### Background 2: Failure of Cripps Mission — March–April 1942
```
Who: Sir Stafford Cripps (British Labour Party leader)
Why sent: Britain needed Indian support for WWII
          Japan was advancing rapidly (had captured Burma, Singapore)
          Japan was threatening India's eastern border

What Cripps offered:
→ Dominion Status AFTER the war (not immediately)
→ Constituent Assembly to draft India's constitution AFTER war
→ Provinces could opt out of the Indian Union (= accepting partition)

Why Cripps Mission FAILED:
→ Gandhi called it "a post-dated cheque on a crashing bank"
   (= promised payment in future, but the bank might fail first)
→ Congress wanted IMMEDIATE independence, not post-war promises
→ No transfer of real power during war — British kept control
→ Muslim League also unhappy (different reasons)

Result of failure:
→ Gandhi and Congress concluded: No compromise possible
→ "British must leave India NOW, during the war"
→ Decision: Launch the most powerful movement yet
```

---

## 🔷 THE DECISION — ALL INDIA CONGRESS COMMITTEE

### Wardha Resolution — July 14, 1942:
```
Location: Wardha, Maharashtra (Gandhi's Sevagram Ashram area)
What: Congress Working Committee passed a resolution
Decision: Launch a mass movement for British withdrawal
Gandhi's language: "An orderly British withdrawal from India"
```

### AICC Session — August 8, 1942:
```
Location: Gowalia Tank Maidan, Bombay
          (Now called "August Kranti Maidan")
Date: August 8, 1942
What happened:
→ All India Congress Committee passed the Quit India Resolution
→ Gandhi delivered his historic "Do or Die" speech
→ The movement was officially LAUNCHED
```

---

## 🔷 GANDHI'S "DO OR DIE" SPEECH — MOST FAMOUS WORDS

### The Historic Call:
```
"Here is a mantra, a short one, that I give you.
You may imprint it on your hearts and let every breath
of yours give expression to it.

The mantra is: 'DO OR DIE'
We shall either free India or die in the attempt."

Original Hindi: "Karo ya Maro"
                Karo = Do | Maro = Die

Gandhi declared:
"I want freedom immediately, this very night, before dawn,
if it can be had."

He also gave other instructions:
→ Every Indian is their own leader now
→ "Do whatever you think is right to get freedom"
→ Non-violence was the ideal but chaos was also acceptable
   (This was a departure — one reason movement became violent)
```

---

## 🔷 THE BRITISH RESPONSE — OPERATION ZERO HOUR

### Arrests Within Hours:
```
August 9, 1942 — early morning (before sunrise):
  → British arrested GANDHI at Birla House, Bombay (now Mumbai)
  → Gandhi taken to Aga Khan Palace, Pune (as prison)
  → Nehru, Patel, Azad, and ALL major Congress leaders arrested
  → Literally overnight — all top leaders in jail!

British strategy: "Decapitate the movement — arrest all leaders
                  before the movement can organize itself"
```

### Gandhi's Imprisonment:
```
Place: Aga Khan Palace, Pune
Duration: August 9, 1942 – May 6, 1944 (nearly 2 years)
Tragedies during imprisonment:
→ Kasturba Gandhi (Gandhi's wife) died in detention — February 22, 1944
→ Gandhi's personal secretary Mahadev Desai died — August 15, 1942
→ Gandhi undertook 21-day fast (February 10 – March 2, 1943)
```

---

## 🔷 THE LEADERLESS MOVEMENT — UNDERGROUND HEROES

### What Happened After Arrests?
```
With all top leaders arrested:
→ Movement became LEADERLESS and SPONTANEOUS
→ People acted on their own without central direction
→ Became more radical and sometimes violent
→ British faced the most widespread uprising since 1857!
```

### Underground Leaders — VERY IMPORTANT FOR BPSC:

#### JP (Jayaprakash Narayan) — BIHAR'S HERO:
```
Full name: Jayaprakash Narayan
Bihar connection: FROM Bihar — born in Sitabdiara, Saran district
Role in Quit India: LED the underground movement
                    Organized secret resistance against British

Most famous act:
→ November 9, 1942: JP ESCAPED from HAZARIBAGH CENTRAL JAIL
→ With 5 other prisoners, he scaled the jail wall and escaped!
→ Became a symbol of resistance and defiance
→ Continued organizing underground movement after escape

Why this matters for BPSC:
→ JP is Bihar's greatest freedom fighter of this period
→ Hazaribagh jail escape = very high BPSC TRE probability
→ JP later became the leader of 1974 Bihar Movement (JP Movement)
```

#### Aruna Asaf Ali:
```
Known as: "Grand Old Lady of the Independence Movement"
         "Heroine of the Quit India Movement"
Famous act: On August 9, 1942 at Gowalia Tank Maidan, Bombay
→ After all leaders were arrested, the crowd was in shock
→ Aruna Asaf Ali came forward and HOISTED THE INDIAN FLAG
→ This defiant act became the most iconic image of Quit India

Background:
→ Wife of Asif Ali (a senior Congress leader)
→ Went underground after hoisting the flag
→ Organized resistance activities for years
→ British put a reward of ₹5,000 on her head
→ Posthumously awarded Bharat Ratna (1997)
```

#### Ram Manohar Lohia:
```
→ Organized underground radio — "Congress Radio"
→ Broadcast from secret locations within Bombay
→ Kept the movement's voice alive when all newspapers were banned
→ Later became a major socialist leader of India
```

#### Sucheta Kripalani:
```
→ Another key underground organizer
→ Worked with Aruna Asaf Ali in Bombay
→ Later became the first female Chief Minister of any Indian state
  (Uttar Pradesh, 1963)
```

---

## 🔷 SPREAD OF THE MOVEMENT — ACROSS INDIA

### Major Centers of Activity:
```
Bihar:
→ MOST INTENSE participation in the entire country
→ JP's escape from Hazaribagh jail
→ Satara (Parallel Government): Nana Patil in Maharashtra
→ Midnapore (Bengal): Tamralipta Jatiya Sarkar (parallel govt)
→ Ballia (UP): "Independent Republic" declared by Chittu Pandey
→ Bihar districts: Government buildings attacked, railways disrupted

Why Bihar stood out:
→ Strong base from Champaran (1917) and NCM
→ JP's leadership and escape galvanized Bihar
→ Peasant militancy already high
→ Slogans: "Angrezi Raj Ka Nash Ho" (Destroy British Rule)
```

### Parallel Governments (Pratyantar Sarkar):
```
Several regions declared "independence" from British:
→ Satara (Maharashtra): "Prati Sarkar" led by Nana Patil
  → Ran for 3+ years! Had its own police, courts, schools
→ Ballia (UP): "Ballia Republic" — lasted days
→ Tamralipta (Bengal Midnapore): Had own Vidyut Bahini (army)
→ These show the DEPTH of Quit India Movement's impact
```

---

## 🔷 QUIT INDIA MOVEMENT TIMELINE

```
QUIT INDIA MOVEMENT — KEY DATES
══════════════════════════════════════════════════

March–April 1942
   │  Cripps Mission — Gandhi calls it "post-dated cheque"
   │  Mission FAILS
   │
July 14, 1942
   │  Wardha Resolution — Congress decides to launch movement
   │
August 8, 1942
   │  AICC Session — Gowalia Tank Maidan, BOMBAY
   │  Quit India Resolution passed
   │  Gandhi gives "Do or Die" speech
   │
August 9, 1942 (early morning) ← "August Kranti Diwas"
   │  Gandhi arrested (taken to Aga Khan Palace, Pune)
   │  ALL major Congress leaders arrested overnight
   │  Aruna Asaf Ali hoists flag at Gowalia Tank Maidan
   │  MOVEMENT BECOMES LEADERLESS
   │
August–December 1942
   │  Widespread protests, sabotage of railways and telegraph
   │  JP leads underground movement
   │  Ram Manohar Lohia runs "Congress Radio"
   │  British use brutal repression
   │
November 9, 1942
   │  JP ESCAPES from HAZARIBAGH CENTRAL JAIL ← Bihar!
   │
August 15, 1942
   │  Mahadev Desai (Gandhi's secretary) dies in detention
   │
February 10 – March 2, 1943
   │  Gandhi's 21-day fast in Aga Khan Palace
   │
February 22, 1944
   │  KASTURBA GANDHI dies in Aga Khan Palace, Pune
   │
May 6, 1944
   │  Gandhi released from prison (on health grounds)
   │
June 1945
   │  All Congress leaders released
   │
1945–1947
   │  Movement's pressure + post-WWII exhaustion of Britain
   │  Leads to independence negotiations
   │
August 15, 1947
   │  INDIA INDEPENDENT
```

---

## 🔷 OUTCOMES AND SIGNIFICANCE

### Why Quit India Failed Immediately:
```
→ Mass arrests decapitated leadership overnight
→ Movement became chaotic and violent without direction
→ British used overwhelming force — 57 battalions deployed
→ 100,000+ people arrested
→ Many killed (official: 1,028; actual much higher)
→ Lasted only ~6 months as organized movement
```

### Why Quit India Succeeded Ultimately:
```
→ Showed British that India could not be governed forever
→ Demonstrated the DEPTH of anti-British feeling
→ Exhausted both Britain and India's colonial relationship
→ Post-WWII Britain was too weak to maintain empire
→ International pressure (USA, others) on Britain
→ INA trials after WWII showed Indian soldiers' loyalty to India
→ Royal Indian Navy Mutiny (1946) showed cracks even in military
```

### Long-term Impact:
```
The Quit India Movement was the LAST major movement before independence.
After QIM → WWII ends (1945) → Labour Party wins in Britain (1945)
→ Clement Attlee becomes PM (more sympathetic to Indian independence)
→ Cabinet Mission (1946) → Mountbatten Plan (1947) → Independence
```

---

## 🔷 KEY PERSONALITIES — MASTER TABLE

| Person | Role |
|--------|------|
| **Mahatma Gandhi** | Launched QIM; "Do or Die" speech; arrested to Aga Khan Palace |
| **Jawaharlal Nehru** | Arrested August 9, 1942; Ahmednagar Fort prison |
| **Aruna Asaf Ali** | Hoisted Congress flag at Gowalia Tank after arrests |
| **JP (Jayaprakash Narayan)** | Led underground movement; ESCAPED Hazaribagh jail (Nov 9, 1942) |
| **Ram Manohar Lohia** | Ran "Congress Radio" underground |
| **Sucheta Kripalani** | Underground organizer; later first woman CM (UP) |
| **Lord Linlithgow** | Viceroy who declared war without consulting Indians |
| **Stafford Cripps** | Led failed Cripps Mission (1942) |
| **Kasturba Gandhi** | Gandhi's wife — died in detention, Aga Khan Palace (Feb 22, 1944) |
| **Nana Patil** | Led Satara Parallel Government (Prati Sarkar) |

---

## 🔷 BIHAR CONNECTION — QUIT INDIA MOVEMENT

```
Bihar's role was the MOST INTENSE of all provinces:

1. JP (Jayaprakash Narayan) — from Sitabdiara, Saran, Bihar
   → Led entire underground movement
   → Escaped Hazaribagh Central Jail (November 9, 1942)

2. Hazaribagh Central Jail — now in Jharkhand (was Bihar then)
   → Site of JP's famous prison escape

3. Mass rural mobilization across Bihar districts

4. Bihar's peasant base (from Champaran → NCM → QIM)
   meant the movement had deep roots here

BPSC exam will almost certainly ask about:
→ JP's escape from Hazaribagh jail
→ JP's connection to Bihar/Saran district
→ August Kranti Diwas (August 9)
```

---

## 🔷 MEMORY TRICKS

```
"CRIPPS FAILED → GANDHI DECIDED → BOMBAY LAUNCHED → ARRESTS NEXT DAY"
(Cripps Mission fail → Wardha Resolution → August 8 AICC → August 9 arrests)

"DO OR DIE = KARO YA MARO"
(Direct Hindi translation — both versions asked in exam)

"Gowalia Tank = August Kranti Maidan"
(Same place, two names — both used in exam questions)

"ARUNA HOISTED the FLAG on August 9"
(While Gandhi was being arrested, Aruna kept the spirit alive)

"JP = JAYAPRAKASH = JAIL BREAK = JHARKHAND (Hazaribagh)"
(The three J's help remember JP's role)

"KASTURBA died in jail February 22, 1944"
(Kasturba = February, 1944 — very emotional, often tested)

"Gandhi in Aga Khan Palace, Pune"
(His specific prison location — don't confuse with other jails)

"RTC 1,2,3 = 1930, 1931, 1932"
"QIM = 1942" (CDM 1930 + 12 years = QIM 1942)
```

---

## 🔷 COMPARISON: NCM vs CDM vs QUIT INDIA

| Feature | NCM (1920–22) | CDM (1930–34) | Quit India (1942) |
|---------|--------------|--------------|-----------------|
| Trigger | JWB + Rowlatt | Simon + Lahore | Cripps failure + WWII |
| Method | Boycott | Break laws | "Do or Die" rebellion |
| Leaders arrested | Gandhi (1922) | Gandhi (1930) | ALL leaders (Aug 9, 1942) |
| Women's role | Limited | Large | Very large |
| Ended by | Chauri Chaura violence | Gandhi-Irwin Pact | WWII + 1945 |
| Bihar connection | Bihar Vidyapeeth | Rajendra Prasad | JP's jail escape |
| Underground leader | None (suspended early) | Aruna Asaf Ali (partial) | JP, Aruna, Lohia |
| Significance | First mass movement | Salt = universal symbol | Last major movement |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Exception Handling (try/catch/throw), Inline Functions

---

**Q1.** What is the purpose of the `try` block in C++ exception handling?
(A) To throw an exception to the operating system
(B) To enclose code that might throw an exception
(C) To catch and handle exceptions
(D) More than one of the above
(E) None of the above

---

**Q2.** Which keyword is used to signal/raise an exception in C++?
(A) `raise`
(B) `signal`
(C) `throw`
(D) More than one of the above
(E) None of the above

---

**Q3.** What is `catch(...)` used for in C++?
(A) Catches only integer exceptions
(B) Catches ALL types of exceptions regardless of type
(C) Is used to rethrow an exception
(D) More than one of the above
(E) None of the above

---

**Q4.** When multiple catch blocks are present, which order should they follow?
(A) Most general (base class) first, most specific (derived) last
(B) Most specific (derived) first, most general (base class) last
(C) Order doesn't matter — compiler handles it
(D) More than one of the above
(E) None of the above

---

**Q5.** Where must `catch(...)` (catch-all handler) be placed?
(A) As the first catch block
(B) As the last catch block
(C) Anywhere — position doesn't matter
(D) More than one of the above
(E) None of the above

---

**Q6.** What happens if an exception is thrown but no matching catch block exists?
(A) Program continues normally ignoring the exception
(B) `terminate()` is called and the program crashes
(C) The exception is silently discarded
(D) More than one of the above
(E) None of the above

---

**Q7.** In exception handling, what does "rethrowing" mean?
(A) Throwing a different exception from a catch block
(B) Catching an exception and throwing it again (same exception)
(C) Throwing an exception inside a nested try block
(D) More than one of the above
(E) None of the above

---

**Q8.** To rethrow the SAME exception from a catch block, which syntax is correct?
(A) `throw e;`
(B) `throw;`
(C) `rethrow;`
(D) More than one of the above
(E) None of the above

---

**Q9.** What exception does `new` throw when memory allocation fails?
(A) `std::memory_error`
(B) `std::bad_alloc`
(C) `std::runtime_error`
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is TRUE about inline functions?
(A) They always reduce code size
(B) The `inline` keyword guarantees the function will be inlined
(C) They eliminate function call overhead by substituting code at call site
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following functions should NOT be made inline?
(A) `int add(int a, int b) { return a+b; }`
(B) A recursive function
(C) `int getX() { return x; }`
(D) More than one of the above
(E) None of the above

---

**Q12.** A member function defined INSIDE a class body in C++ is:
(A) Always virtual
(B) Automatically treated as inline
(C) Always static
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following correctly declares an inline function?
(A) `function inline int add(int a, int b) { return a+b; }`
(B) `inline int add(int a, int b) { return a+b; }`
(C) `int add inline(int a, int b) { return a+b; }`
(D) More than one of the above
(E) None of the above

---

**Q14.** What is the trade-off of using inline functions?
(A) Slower execution but smaller code
(B) Faster execution but larger code (code bloat)
(C) Same speed but better readability
(D) More than one of the above
(E) None of the above

---

**Q15.** Consider: `inline int fact(int n) { return n<=1 ? 1 : n*fact(n-1); }` — what happens?
(A) Works perfectly — inline recursion is fully supported
(B) Compiler ignores the inline hint (cannot inline recursive functions)
(C) Compilation error — inline cannot be used with recursion
(D) More than one of the above
(E) None of the above

---

**Q16.** What is "stack unwinding" in exception handling?
(A) Clearing the stack of all data
(B) Destroying local objects and exiting functions as exception propagates
(C) Reversing the execution order of statements
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following types CAN be thrown using `throw` in C++?
(A) int
(B) std::string
(C) User-defined class objects
(D) More than one of the above
(E) None of the above

---

**Q18.** When inline functions are called multiple times, what effect does it have on code size?
(A) Code size decreases (function body exists once)
(B) Code size increases (function body copied at each call site)
(C) No effect on code size
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following will cause the compiler to IGNORE the inline keyword?
(A) Function containing a `for` loop
(B) Function containing a `static` variable
(C) Function that is recursive
(D) More than one of the above
(E) None of the above

---

**Q20.** Consider the code:
```cpp
try { throw 10; }
catch (double d) { cout << "double"; }
catch (int i) { cout << "int"; }
```
What is the output?
(A) double
(B) int
(C) Compilation error
(D) More than one of the above
(E) None of the above

---

**Q21.** What is the correct base class for all standard C++ exceptions?
(A) `std::error`
(B) `std::exception`
(C) `std::runtime_error`
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following is an advantage of inline functions?
(A) Reduced code size
(B) Reduced execution time (no function call overhead)
(C) Always guaranteed to be faster than regular functions
(D) More than one of the above
(E) None of the above

---

**Q23.** In C++ exception handling, what does `e.what()` return for standard exceptions?
(A) The exception type name
(B) A descriptive error message string
(C) The exception error code
(D) More than one of the above
(E) None of the above

---

**Q24.** If `throw` is used without any argument inside a catch block, it:
(A) Throws a null exception
(B) Rethrows the currently handled exception
(C) Clears the exception
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following statements about inline functions is CORRECT?
(A) inline functions are resolved at runtime
(B) inline functions are expanded at compile time at the call site
(C) inline functions must always be defined in .cpp files
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Quit India Movement 1942

---

**Q26.** The Quit India Movement was launched on:
(A) August 8, 1942 (AICC resolution)
(B) August 9, 1942 (actual launch / arrests)
(C) July 14, 1942 (Wardha Resolution)
(D) More than one of the above
(E) None of the above

---

**Q27.** Gandhi's famous call during the Quit India Movement was:
(A) "Jai Hind"
(B) "Purna Swaraj"
(C) "Do or Die" (Karo ya Maro)
(D) More than one of the above
(E) None of the above

---

**Q28.** Where was the historic AICC session held on August 8, 1942 where the Quit India Resolution was passed?
(A) Wardha, Maharashtra
(B) Gowalia Tank Maidan, Bombay
(C) Lahore
(D) More than one of the above
(E) None of the above

---

**Q29.** After Gandhi's arrest on August 9, 1942, who hoisted the Congress flag at Gowalia Tank Maidan?
(A) Sarojini Naidu
(B) Kasturba Gandhi
(C) Aruna Asaf Ali
(D) More than one of the above
(E) None of the above

---

**Q30.** Gandhi was imprisoned during the Quit India Movement at:
(A) Yerwada Prison, Pune
(B) Aga Khan Palace, Pune
(C) Andaman Cellular Jail
(D) More than one of the above
(E) None of the above

---

**Q31.** The Cripps Mission (1942) failed primarily because:
(A) Cripps demanded complete Indian support for WWII
(B) It offered Dominion Status only AFTER the war, with no immediate transfer of power
(C) It proposed dissolution of INC
(D) More than one of the above
(E) None of the above

---

**Q32.** Gandhi described the Cripps Mission offer as:
(A) "A gift from heaven"
(B) "A post-dated cheque on a crashing bank"
(C) "Too little, too late"
(D) More than one of the above
(E) None of the above

---

**Q33.** JP (Jayaprakash Narayan) escaped from which jail during the Quit India Movement?
(A) Patna Central Jail
(B) Hazaribagh Central Jail
(C) Naini Central Jail, Allahabad
(D) More than one of the above
(E) None of the above

---

**Q34.** When did JP escape from jail during the Quit India Movement?
(A) August 9, 1942
(B) November 9, 1942
(C) December 9, 1942
(D) More than one of the above
(E) None of the above

---

**Q35.** JP (Jayaprakash Narayan) was born in which district of Bihar?
(A) Patna
(B) Saran (Sitabdiara village)
(C) Champaran
(D) More than one of the above
(E) None of the above

---

**Q36.** The underground "Congress Radio" during the Quit India Movement was operated by:
(A) Aruna Asaf Ali
(B) JP (Jayaprakash Narayan)
(C) Ram Manohar Lohia
(D) More than one of the above
(E) None of the above

---

**Q37.** Kasturba Gandhi died during the Quit India Movement period at:
(A) August 9, 1942 — Bombay
(B) February 22, 1944 — Aga Khan Palace, Pune
(C) May 6, 1944 — Yerwada Prison
(D) More than one of the above
(E) None of the above

---

**Q38.** The Wardha Resolution (July 14, 1942) was passed by:
(A) The All India Congress Committee
(B) The Congress Working Committee
(C) The Indian National Army
(D) More than one of the above
(E) None of the above

---

**Q39.** August 9 is celebrated in India as:
(A) Independence Day
(B) August Kranti Diwas (August Revolution Day)
(C) Republic Day
(D) More than one of the above
(E) None of the above

---

**Q40.** The "Satara Parallel Government" (Prati Sarkar) during the Quit India Movement was led by:
(A) JP (Jayaprakash Narayan)
(B) Nana Patil
(C) Aruna Asaf Ali
(D) More than one of the above
(E) None of the above

---

**Q41.** Who was the Viceroy of India when the Quit India Movement was launched?
(A) Lord Irwin
(B) Lord Linlithgow
(C) Lord Mountbatten
(D) More than one of the above
(E) None of the above

---

**Q42.** The Quit India Movement is significant because:
(A) It was Gandhi's first Satyagraha in India
(B) It was the last and most massive mass movement before independence
(C) It directly led to India's independence through negotiation
(D) More than one of the above
(E) None of the above

---

**Q43.** Arrange in CORRECT CHRONOLOGICAL ORDER:
1. Quit India Resolution passed
2. Gandhi arrested
3. Aruna Asaf Ali hoists flag
4. Cripps Mission fails

(A) 4 → 1 → 3 → 2
(B) 4 → 1 → 2 → 3
(C) 1 → 4 → 2 → 3
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following shows Bihar's connection to the Quit India Movement?
(A) Champaran was the site of the Quit India launch
(B) JP led the underground movement and escaped Hazaribagh jail
(C) Gandhi was imprisoned in Patna during the movement
(D) More than one of the above
(E) None of the above

---

**Q45.** Sucheta Kripalani, who was active in the Quit India underground movement, later became significant as:
(A) First woman President of INC
(B) First female Chief Minister of any Indian state (Uttar Pradesh, 1963)
(C) First female Governor of an Indian state
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following is CORRECT about the Cripps Mission?
(A) Sir Stafford Cripps was a French diplomat
(B) Sir Stafford Cripps was a British Labour Party leader sent by Churchill's government
(C) The mission offered immediate independence to India
(D) More than one of the above
(E) None of the above

---

**Q47.** MATCH THE FOLLOWING:
```
Person                    Role in Quit India
1. Aruna Asaf Ali         A. Led underground movement, Hazaribagh escape
2. JP (Jayaprakash)       B. Ran Congress Radio underground
3. Ram Manohar Lohia      C. Hoisted flag at Gowalia Tank after arrests
4. Nana Patil             D. Led Satara Parallel Government
```
(A) 1-C, 2-A, 3-B, 4-D
(B) 1-A, 2-C, 3-D, 4-B
(C) 1-B, 2-D, 3-A, 4-C
(D) More than one of the above
(E) None of the above

---

**Q48.** The Gowalia Tank Maidan in Bombay is also known as:
(A) Azad Maidan
(B) August Kranti Maidan
(C) Shivaji Park
(D) More than one of the above
(E) None of the above

---

**Q49.** The Congress Working Committee passed the Wardha Resolution calling for British withdrawal in:
(A) August 8, 1942
(B) July 14, 1942
(C) March 2, 1942
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following correctly describes the immediate British response to the Quit India Movement on August 9, 1942?
(A) British agreed to negotiate and granted partial independence
(B) All major Congress leaders arrested overnight before the movement could organize
(C) British withdrew from India immediately
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
| 1 | (B) | try block encloses code that might throw |
| 2 | (C) | `throw` keyword raises an exception |
| 3 | (B) | catch(...) catches ALL exception types |
| 4 | (B) | Specific (derived) first, general (base) last |
| 5 | (B) | catch(...) must always be the LAST catch block |
| 6 | (B) | terminate() is called — program crashes |
| 7 | (B) | Rethrow = catch an exception and throw it again |
| 8 | (B) | Bare `throw;` rethrows original exception |
| 9 | (B) | `new` throws std::bad_alloc on failure |
| 10 | (C) | Inline substitutes code at call site — eliminates overhead |
| 11 | (B) | Recursive functions — compiler ignores inline for them |
| 12 | (B) | Member functions defined inside class = automatically inline |
| 13 | (B) | `inline returnType funcName(...)` — inline comes first |
| 14 | (B) | Faster execution but LARGER code (code bloat) |
| 15 | (B) | Compiler ignores inline for recursive functions |
| 16 | (B) | Destroying local objects and exiting functions as exception propagates |
| 17 | (D) | Any type can be thrown: int, string, user-defined objects |
| 18 | (B) | Code bloat — body copied at each call site |
| 19 | (D) | All three: loops, static variables, recursion → inline ignored |
| 20 | (B) | throw 10 is int; int catch matches → "int" |
| 21 | (B) | std::exception is base of all standard exceptions |
| 22 | (B) | Reduced execution time — no function call overhead |
| 23 | (B) | e.what() returns descriptive error message string |
| 24 | (B) | Bare `throw;` rethrows currently handled exception |
| 25 | (B) | Inline functions expanded at COMPILE TIME at call site |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (D) | Both Aug 8 (resolution) and Aug 9 (actual launch + arrests) are valid |
| 27 | (C) | "Do or Die" / "Karo ya Maro" — Gandhi's Quit India call |
| 28 | (B) | Gowalia Tank Maidan, Bombay (now August Kranti Maidan) |
| 29 | (C) | Aruna Asaf Ali hoisted the Congress flag |
| 30 | (B) | Aga Khan Palace, Pune |
| 31 | (B) | Dominion Status only after war, no immediate power transfer |
| 32 | (B) | "Post-dated cheque on a crashing bank" — Gandhi's exact words |
| 33 | (B) | Hazaribagh Central Jail |
| 34 | (B) | November 9, 1942 |
| 35 | (B) | Sitabdiara village, Saran district, Bihar |
| 36 | (C) | Ram Manohar Lohia ran the underground Congress Radio |
| 37 | (B) | February 22, 1944 — Aga Khan Palace, Pune |
| 38 | (B) | Congress Working Committee at Wardha |
| 39 | (B) | August Kranti Diwas (August Revolution Day) |
| 40 | (B) | Nana Patil led Satara Parallel Government (Prati Sarkar) |
| 41 | (B) | Lord Linlithgow was Viceroy in 1942 |
| 42 | (B) | Last and most massive mass movement before independence |
| 43 | (B) | Cripps fails → Resolution Aug 8 → Arrests Aug 9 → Aruna hoists flag Aug 9 |
| 44 | (B) | JP led underground, escaped Hazaribagh jail |
| 45 | (B) | Sucheta Kripalani — first female Chief Minister (UP, 1963) |
| 46 | (B) | Sir Stafford Cripps was a British Labour Party leader |
| 47 | (A) | Aruna-C, JP-A, Lohia-B, Nana Patil-D |
| 48 | (B) | August Kranti Maidan — renamed after QIM |
| 49 | (B) | July 14, 1942 — Wardha Resolution |
| 50 | (B) | All major leaders arrested overnight before movement could organize |

---
---

# 🔁 DAY 12 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Exception Handling

### Core Flow — One-Liners:
1. **try** = watch this code | **throw** = signal error | **catch** = handle error
2. **catch(...)** = catch ALL types — MUST be the LAST catch block
3. **Specific catch before general** — derived class exceptions before base class
4. **Bare `throw;`** = rethrow SAME exception (no copy) | **`throw e;`** = rethrow COPY
5. **No matching catch** → `terminate()` called → program crashes
6. **`new` fails** → throws `std::bad_alloc` | `malloc` fails → returns NULL (different!)
7. **Stack unwinding** = local objects destroyed as exception propagates back up call stack
8. **std::exception** = base class of ALL standard C++ exceptions
9. **`e.what()`** = returns error message string from standard exception

### Exception Order Rule:
```
try { ... }
catch (MostSpecificType e) { }   ← derived class FIRST
catch (MoreGeneralType e) { }    ← base class LATER
catch (...) { }                  ← catch-all LAST (MANDATORY!)
```

---

## ⚡ RAPID FIRE — Inline Functions

### Must-Know Rules:
1. **`inline`** = REQUEST to compiler — not guaranteed to be honored
2. **Inline replaces function call** with actual code at call site (compile time)
3. **Trade-off**: FASTER execution ↔ LARGER code size (code bloat)
4. **Auto-inline**: Member functions defined INSIDE class body = automatically inline
5. **Compiler IGNORES inline for**: recursion, loops, static vars, large body, virtual functions

### Quick Check:
```
Short function (1-3 lines, no loops)?     → ✅ Good for inline
Recursive function?                        → ❌ Inline IGNORED
Contains loop (for/while)?                 → ❌ Inline IGNORED
Defined inside class body?                 → ✅ Already inline (auto)
Called 1000 times per second?              → ✅ Inline is beneficial
Large function (50+ lines)?                → ❌ Code bloat outweighs benefit
```

---

## ⚡ RAPID FIRE — Quit India Movement

### Critical Facts:
```
Date of Resolution: August 8, 1942 — Gowalia Tank Maidan, Bombay
Date of Arrests:    August 9, 1942 (= August Kranti Diwas)
Gandhi's slogan:    "Do or Die" = "Karo ya Maro"
Gandhi's prison:    Aga Khan Palace, Pune
Cripps Mission quote: "Post-dated cheque on a crashing bank"
Aruna Asaf Ali:     Hoisted flag at Gowalia Tank after arrests
JP:                 Led underground; escaped Hazaribagh jail (Nov 9, 1942)
JP birthplace:      Sitabdiara, Saran district, Bihar
Ram Manohar Lohia: Ran "Congress Radio" underground
Kasturba Gandhi:    Died in Aga Khan Palace, Feb 22, 1944
Gowalia Tank:       Now called "August Kranti Maidan"
Wardha Resolution:  July 14, 1942 (CWC decision to launch)
Cripps Mission:     March-April 1942 (failed → triggered QIM)
Viceroy:            Lord Linlithgow
```

### Bihar-Specific — Never Forget:
```
JP = Jayaprakash Narayan = from Sitabdiara, Saran, BIHAR
JP = Escaped HAZARIBAGH CENTRAL JAIL = November 9, 1942
Hazaribagh (now Jharkhand, was Bihar) = Site of JP's famous escape
Bihar had MOST INTENSE participation in entire QIM
```

### Common Exam Traps:
1. QIM **launched August 9** (arrests) — Resolution was August **8**
2. Gowalia Tank = **August Kranti Maidan** — same place, two names
3. JP escaped **Hazaribagh** jail (NOT Patna, NOT Naini)
4. JP escaped **November 9** (NOT August 9)
5. Kasturba died **February 22, 1944** (NOT 1942 or 1943)
6. **Ram Manohar Lohia** ran Congress Radio (NOT JP, NOT Aruna)
7. **Nana Patil** = Satara Parallel Government (NOT JP)
8. Cripps = **Labour Party** (NOT Conservative), sent by Churchill (Conservative PM)

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. catch(...) must ALWAYS be the LAST catch block; specific types come before general ones
2. `inline` is ignored by compiler for recursive functions, functions with loops, and large functions
3. Inline function trade-off: FASTER execution but LARGER code size (code bloat)
4. QIM launched August 9, 1942 — Gandhi arrested to Aga Khan Palace, Pune
5. JP escaped Hazaribagh Central Jail on November 9, 1942 — Bihar's greatest QIM hero

---

*Next: Day 13 — C++ STL (Standard Template Library) Basics + Indian Constitution Overview*
