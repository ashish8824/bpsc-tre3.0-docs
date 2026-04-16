# 📅 BPSC TRE 4.0 — DAY 13 COMPLETE STUDY MODULE
### C++ Output Prediction & Core Concepts + Bihar History: Rajendra Prasad
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Output prediction, bitwise ops, struct/class, friend functions
> - Afternoon (1 hr): Rajendra Prasad — life, struggle, Presidency
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 C++ Output Prediction & Core Concepts

---

# ═══════════════════════════════════════
# TOPIC A: OUTPUT PREDICTION
# ═══════════════════════════════════════

## 🔷 SECTION 1: Pre-increment vs Post-increment

### The Golden Rule:
```
Pre-increment  (++i):  INCREMENT FIRST, then USE the value
Post-increment (i++):  USE the value FIRST, then INCREMENT

Same rule applies to decrement:
Pre-decrement  (--i):  DECREMENT FIRST, then USE
Post-decrement (i--):  USE the value FIRST, then DECREMENT
```

### Visual Explanation:
```
int i = 5;

++i → (i becomes 6) → expression value = 6
i++ → expression value = 5 → (i becomes 6)

MEMORY TABLE for ++i:
┌─────────┬──────────────────────────┐
│  Step   │  What Happens            │
├─────────┼──────────────────────────┤
│ Before  │  i = 5                   │
│ ++i     │  i → 6, use value 6      │
│ After   │  i = 6                   │
└─────────┴──────────────────────────┘

MEMORY TABLE for i++:
┌─────────┬──────────────────────────┐
│  Step   │  What Happens            │
├─────────┼──────────────────────────┤
│ Before  │  i = 5                   │
│ i++     │  use value 5, i → 6      │
│ After   │  i = 6                   │
└─────────┴──────────────────────────┘
```

### Code Examples — Dry Run:

#### Example 1 (Basic):
```cpp
int i = 5;
cout << i++;    // Output: 5  (prints 5, THEN i becomes 6)
cout << i;      // Output: 6  (i is now 6)
cout << ++i;    // Output: 7  (i becomes 7 FIRST, then printed)
cout << i;      // Output: 7
```

**Dry Run Table:**
| Line | Expression | Value Printed | i after |
|------|-----------|---------------|---------|
| 1 | i = 5 | — | 5 |
| 2 | i++ | 5 | 6 |
| 3 | i | 6 | 6 |
| 4 | ++i | 7 | 7 |
| 5 | i | 7 | 7 |

#### Example 2 (Assignment):
```cpp
int a = 10;
int b = a++;    // b gets 10, THEN a becomes 11
int c = ++a;    // a becomes 12 FIRST, c gets 12
cout << a << " " << b << " " << c;
// Output: 12 10 12
```

**Dry Run Table:**
| Line | Action | a | b | c |
|------|--------|---|---|---|
| Start | int a=10 | 10 | — | — |
| int b=a++ | b=10, a increments | 11 | 10 | — |
| int c=++a | a increments, c=12 | 12 | 10 | 12 |
| Output | 12 10 12 | — | — | — |

#### Example 3 (Function Call — Exam Trap!):
```cpp
int i = 5;
cout << i++ + ++i;
```

**⚠️ UNDEFINED BEHAVIOR WARNING:**
```
In C++, modifying a variable MORE THAN ONCE between sequence points
is UNDEFINED BEHAVIOR.
i++ + ++i modifies i twice (i++ and ++i) without a sequence point.
The result is UNDEFINED — compiler may produce any output!

Different compilers may give:
GCC: 12   Clang: 11   MSVC: 11

→ EXAM APPROACH: If such a question appears in BPSC,
  the expected answer is usually 11 (most compilers left-to-right)
  BUT the correct academic answer is "Undefined Behavior"
```

#### Example 4 (in Loop — Very Common Exam Pattern):
```cpp
int i = 0;
while (i++ < 3) {
    cout << i << " ";
}
// Let's dry run:
```

**Dry Run Table:**
| Iteration | Condition check (i++) | Value of i during check | i after check | Print i | Continue? |
|-----------|----------------------|------------------------|---------------|---------|-----------|
| 1 | 0++ < 3 → 0 < 3 = true | 0 (old value) | 1 | 1 | Yes |
| 2 | 1++ < 3 → 1 < 3 = true | 1 | 2 | 2 | Yes |
| 3 | 2++ < 3 → 2 < 3 = true | 2 | 3 | 3 | Yes |
| 4 | 3++ < 3 → 3 < 3 = false | 3 | 4 | — | No |

**Output: `1 2 3`**

#### Example 5 (i++ vs ++i in for loop):
```cpp
// Post-increment in for loop (standard):
for (int i = 0; i < 3; i++) {
    cout << i << " ";
}
// Output: 0 1 2

// Pre-increment in for loop (same result for simple loops):
for (int i = 0; i < 3; ++i) {
    cout << i << " ";
}
// Output: 0 1 2
// For simple loop counters, both give same result!
// Pre-increment is slightly more efficient (no temp copy needed)
```

### 🚨 PYQ TRAP #1:
```cpp
int x = 5;
int y = x++ * ++x;
// Step 1: x++ → use 5, x becomes 6
// Step 2: ++x → x becomes 7, use 7
// y = 5 * 7 = 35? OR x = 7 in both? → UNDEFINED BEHAVIOR!
// Exam answer varies — read the options carefully
// If "undefined behavior" is an option, choose that!
```

---

## 🔷 SECTION 2: Boolean Values in Expressions

### Core Rules:
```
In C++:
  false = 0
  true  = 1 (or any non-zero value)

When printing bool:
  cout << true;   → prints 1
  cout << false;  → prints 0

Comparison operators return bool (0 or 1):
  cout << (5 > 3);   → 1 (true)
  cout << (5 < 3);   → 0 (false)
  cout << (5 == 5);  → 1 (true)
```

### Examples:
```cpp
int a = 5, b = 3;
cout << (a > b);         // Output: 1
cout << (a == b);        // Output: 0
cout << (a != b);        // Output: 1
cout << (a > b) + 1;     // Output: 2  (1 + 1 = 2)
cout << (a < b) + 10;    // Output: 10 (0 + 10 = 10)

bool flag = true;
cout << flag;            // Output: 1
cout << !flag;           // Output: 0
cout << flag + 5;        // Output: 6  (1 + 5 = 6)
```

### 🚨 PYQ TRAP #2 — Common Confusion:
```cpp
int x = 0;
if (x = 5) {             // ASSIGNMENT (=), not comparison (==)!
    cout << "True";      // Output: True
}
// x = 5 assigns 5 to x, then evaluates to 5 (non-zero = true)
// This is a LOGIC BUG but NOT a compile error!

int x = 5;
if (x == 5) { cout << "Equal"; }  // ✅ Comparison
if (x = 0)  { cout << "True"; }   // ⚠️ Assignment! Assigns 0 to x, evaluates to 0 (false)
```

---

## 🔷 SECTION 3: Operator Precedence & Associativity

### Quick Precedence Table (High to Low):
```
HIGHEST PRECEDENCE
  ()         → Parentheses
  ++, --     → Post-increment/decrement (right to left for prefix)
  !, ~       → Logical NOT, Bitwise NOT (unary, right-to-left)
  *, /, %    → Multiplication, Division, Modulus
  +, -       → Addition, Subtraction
  <<, >>     → Bitwise Shift
  <, <=, >, >= → Relational
  ==, !=     → Equality
  &          → Bitwise AND
  ^          → Bitwise XOR
  |          → Bitwise OR
  &&         → Logical AND
  ||         → Logical OR
  =, +=, -=  → Assignment (right-to-left)
LOWEST PRECEDENCE
```

### Memory Trick for Precedence:
```
"Please Remember My Actions And Other Logic: Always Assign"
P  = Parentheses
R  = Relations (<, >, <=, >=)
M  = Multiplicative (*, /, %)
A  = Additive (+, -)
A  = And Bitwise (&)
O  = Or Bitwise (|)
L  = Logical (&&, ||)
A  = Assign (=)
```

### Associativity:
```
Left-to-right:  Most operators (arithmetic, relational, bitwise)
Right-to-left:  Assignment (=, +=), Unary operators (!, ~, ++prefix)
```

### Example:
```cpp
int x = 2 + 3 * 4;
// 3 * 4 = 12 (higher precedence)
// 2 + 12 = 14
// x = 14

int y = (2 + 3) * 4;
// (2+3) = 5 (parentheses first)
// 5 * 4 = 20
// y = 20
```

---

## 🔷 SECTION 4: Bitwise Operators — The Exam Goldmine

### Overview of All Bitwise Operators:
```
&   = Bitwise AND
|   = Bitwise OR
^   = Bitwise XOR (exclusive OR)
~   = Bitwise NOT (one's complement)
<<  = Left Shift
>>  = Right Shift
```

### The Truth Tables:
```
AND (&):         OR (|):         XOR (^):
A  B  A&B        A  B  A|B       A  B  A^B
0  0   0         0  0   0        0  0   0
0  1   0         0  1   1        0  1   1
1  0   0         1  0   1        1  0   1
1  1   1         1  1   1        1  1   0

NOT (~):
A   ~A
0    1
1    0
```

### Memory Tricks:
```
AND  (&)  → "Both must be 1" → 1 & 1 = 1 only
OR   (|)  → "At least one 1" → 0 | 1 = 1
XOR  (^)  → "Exactly one 1" → different = 1, same = 0
NOT  (~)  → "Flip everything"
```

---

### Bitwise AND (`&`) — Examples:
```cpp
int a = 12, b = 10;
// 12 = 1100 (binary)
// 10 = 1010 (binary)
// &  = 1000 = 8

cout << (a & b);   // Output: 8

Step-by-step:
  12 = 1 1 0 0
  10 = 1 0 1 0
  &  = 1 0 0 0 = 8 ✓
```

**Common Bitwise AND Use:**
```cpp
// Check if a number is odd or even:
if (n & 1) cout << "Odd";    // last bit is 1 → odd
else       cout << "Even";   // last bit is 0 → even

// Examples:
5 & 1 = 101 & 001 = 001 = 1  → Odd
6 & 1 = 110 & 001 = 000 = 0  → Even
```

---

### Bitwise OR (`|`) — Examples:
```cpp
int a = 12, b = 10;
// 12 = 1100
// 10 = 1010
// |  = 1110 = 14

cout << (a | b);   // Output: 14

Step-by-step:
  12 = 1 1 0 0
  10 = 1 0 1 0
  |  = 1 1 1 0 = 14 ✓
```

---

### Bitwise XOR (`^`) — Examples:
```cpp
int a = 12, b = 10;
// 12 = 1100
// 10 = 1010
// ^  = 0110 = 6

cout << (a ^ b);   // Output: 6

Step-by-step:
  12 = 1 1 0 0
  10 = 1 0 1 0
  ^  = 0 1 1 0 = 6 ✓
```

**XOR Trick — Swap Without Temp Variable (Classic Interview/Exam Question):**
```cpp
int a = 5, b = 3;
a = a ^ b;    // a = 5^3 = 6
b = a ^ b;    // b = 6^3 = 5  (original a)
a = a ^ b;    // a = 6^5 = 3  (original b)
// Now: a = 3, b = 5 — swapped!

Key XOR property: a ^ a = 0 (any number XOR itself = 0)
                  a ^ 0 = a (any number XOR 0 = itself)
```

### 🚨 PYQ TRAP #3 — XOR Self-Cancellation:
```cpp
int x = 7;
x = x ^ x;
cout << x;   // Output: 0
// Any number XOR itself = 0 (always!)
// 7 = 0111, 7 = 0111, XOR = 0000 = 0
```

---

### Bitwise NOT (`~`) — One's Complement:
```cpp
int a = 5;
cout << ~a;   // Output: -6

// Why -6?
// 5 in binary (32-bit): 0000...00000101
// ~5 flips all bits:   1111...11111010
// This is -6 in two's complement representation!

// RULE: ~n = -(n+1) for signed integers
// ~5  = -6
// ~0  = -1
// ~-1 = 0
```

### 🚨 PYQ TRAP #4 — Bitwise NOT result:
```
~n = -(n + 1)
~5 = -6, ~0 = -1, ~(-5) = 4, ~7 = -8
This formula must be memorized!
```

---

### Left Shift (`<<`) and Right Shift (`>>`):
```
Left Shift  (a << n):  Multiply by 2^n
Right Shift (a >> n):  Divide by 2^n (integer division)
```

```cpp
int a = 5;    // 5 = 0000 0101

cout << (a << 1);   // 5 × 2^1 = 10  →  0000 1010
cout << (a << 2);   // 5 × 2^2 = 20  →  0001 0100
cout << (a << 3);   // 5 × 2^3 = 40  →  0010 1000

cout << (a >> 1);   // 5 ÷ 2^1 = 2   →  0000 0010 (floor)
cout << (a >> 2);   // 5 ÷ 2^2 = 1   →  0000 0001

// Rule: a << n = a * (2^n)
//       a >> n = a / (2^n)  [integer division]
```

### Visual Left Shift:
```
5 = 0 1 0 1  (4-bit representation)
     ↓
5 << 1 = 1 0 1 0 = 10   (shift all bits left, fill with 0)
5 << 2 = 0 1 0 0 = 20   (shift 2 positions left)
```

### Complete Bitwise Table for a=5, b=3:
```
a = 5 = 0101
b = 3 = 0011

Operation  Result (binary)  Decimal
─────────────────────────────────────
a & b      0001             1
a | b      0111             7
a ^ b      0110             6
~a         ...11111010      -6
a << 1     1010             10
a >> 1     0010             2
```

---

## 🔷 SECTION 5: Recursive Functions — Basics & Segfault

### What is Recursion?
```
A function that calls ITSELF is recursive.
Every recursive function needs:
  1. Base case  → stops recursion (no more calls)
  2. Recursive case → calls itself with smaller problem
```

### Example — Factorial:
```cpp
int factorial(int n) {
    if (n == 0) return 1;    // base case
    return n * factorial(n-1); // recursive case
}
```

**Dry Run for factorial(4):**
```
factorial(4)
  = 4 * factorial(3)
       = 3 * factorial(2)
            = 2 * factorial(1)
                 = 1 * factorial(0)
                      = 1  [base case]
                 = 1 * 1 = 1
            = 2 * 1 = 2
       = 3 * 2 = 6
  = 4 * 6 = 24
```

### 🚨 PYQ TRAP #5 — Missing Base Case → Segmentation Fault:
```cpp
// WITHOUT base case:
int factorial(int n) {
    return n * factorial(n-1);   // no base case!
}
// This creates INFINITE RECURSION
// Stack overflow → SEGMENTATION FAULT (runtime crash)
// Not a compile error — crashes only at runtime!

// WITH correct base case:
int factorial(int n) {
    if (n <= 0) return 1;        // base case prevents infinite recursion
    return n * factorial(n-1);
}
```

### What is a Segmentation Fault?
```
Segmentation Fault = accessing memory that doesn't belong to the program

Causes:
1. Missing base case in recursion (stack overflow)
2. Dereferencing NULL pointer
3. Array out of bounds access (sometimes)
4. Writing to read-only memory

NOTE: Segfault is a RUNTIME error, not a compile error.
```

---

## 🔷 SECTION 6: struct vs class in C++

### Core Difference — Default Access:
```
struct: Default access = PUBLIC
class:  Default access = PRIVATE
```

### Comparison Table:

| Feature | `struct` | `class` |
|---------|---------|---------|
| Default access | **public** | **private** |
| Can have methods | Yes | Yes |
| Can have constructors | Yes | Yes |
| Supports inheritance | Yes | Yes |
| Supports access specifiers | Yes | Yes |
| Usage convention | Simple data groups | Full OOP entities |

### Code Example:
```cpp
struct Point {
    int x;    // PUBLIC by default
    int y;    // PUBLIC by default
};

class Circle {
    int radius;      // PRIVATE by default
public:
    int getRadius() { return radius; }
};

int main() {
    Point p;
    p.x = 5;        // ✅ Works — x is public

    Circle c;
    // c.radius = 5; // ❌ Error — radius is private
    int r = c.getRadius(); // ✅ Works through public method
}
```

### 🚨 PYQ TRAP #6:
```cpp
struct MyStruct {
    int a;    // public (default)
    int b;    // public (default)
};

class MyClass {
    int a;    // PRIVATE (default)
    int b;    // PRIVATE (default)
};
```
> **The ONLY fundamental difference between struct and class in C++ is the default access specifier.**
> struct = public by default | class = private by default

### Inheritance Default Access:
```cpp
struct A : B { };         // Default: public inheritance
class A : B { };          // Default: private inheritance
```

---

## 🔷 SECTION 7: Friend Functions

### What is a Friend Function?
```
A friend function is a NON-MEMBER function that has access to
the PRIVATE and PROTECTED members of a class.

Real-life analogy:
  Your house (class) has private rooms.
  A "friend" has a spare key (friend declaration).
  That friend can enter private rooms — but is NOT a member of the household.
```

### Declaration Syntax:
```cpp
class Box {
private:
    double width;
public:
    Box(double w) : width(w) {}
    friend double getWidth(Box b);   // friend declaration inside class
};

// Definition outside class — no scope resolution needed!
double getWidth(Box b) {
    return b.width;    // ✅ Can access PRIVATE member width!
}

int main() {
    Box b(5.5);
    cout << getWidth(b);   // Output: 5.5
}
```

### Key Properties of Friend Functions:

| Property | Details |
|----------|---------|
| Declared with `friend` | Inside the class body |
| Defined | OUTSIDE the class (no class scope) |
| Accesses | private AND protected members |
| Is it a member? | **NO** — not a member of the class |
| Called how? | Like a regular function — no object.method |
| Inheritable? | **NO** — friendship is NOT inherited |
| Reciprocal? | **NO** — if A is friend of B, B is NOT friend of A |

### 🚨 PYQ TRAP #7:
```
Friend function is NOT a member function.
It is called WITHOUT using an object: getWidth(b), NOT b.getWidth()
Friendship is NOT inherited.
Friendship is NOT symmetric (one-way only).
```

### Friend Class Example:
```cpp
class Y;   // forward declaration

class X {
    int a = 10;
    friend class Y;   // Y is a friend of X
};

class Y {
public:
    void showA(X obj) {
        cout << obj.a;   // ✅ Can access X's private member
    }
};
```

---

## 🔷 SECTION 8: Scope Resolution Operator `::`

### Uses of `::`:

#### 1. Access global variable (when shadowed by local):
```cpp
int x = 100;    // global

void func() {
    int x = 50;         // local — shadows global
    cout << x;          // prints 50 (local)
    cout << ::x;        // prints 100 (global — scope resolution)
}
```

#### 2. Define class member functions outside the class:
```cpp
class Calculator {
public:
    int add(int a, int b);   // declaration inside
};

int Calculator::add(int a, int b) {    // definition outside
    return a + b;
}
```

#### 3. Access static members:
```cpp
class Counter {
public:
    static int count;
};
int Counter::count = 0;      // define static member
Counter::count++;            // access static member
```

#### 4. Access enum or namespace members:
```cpp
namespace MySpace {
    int value = 42;
}
cout << MySpace::value;   // scope resolution with namespace
```

### 🚨 PYQ TRAP #8:
```
:: is the SCOPE RESOLUTION OPERATOR
. is the MEMBER ACCESS OPERATOR (for objects)
-> is the MEMBER ACCESS OPERATOR (for pointers)

Rectangle r;
r.area()          → member function via object
Rectangle::area   → class scope (for static or definition)
ptr->area()       → member function via pointer
```

---

## 📊 VISUAL SUMMARY — All Code Patterns

```
OUTPUT PREDICTION CHEAT SHEET
══════════════════════════════════════════

Pre/Post Increment:
  i=5: cout<<i++  → 5 (prints first, then i=6)
  i=5: cout<<++i  → 6 (increments first, then prints)
  b=a++: b=old a,  a=a+1
  c=++a: a=a+1,   c=new a

Bitwise Quick Reference:
  5 & 3 = 1   (AND:  both 1)
  5 | 3 = 7   (OR:   any 1)
  5 ^ 3 = 6   (XOR:  different)
  ~5    = -6  (NOT:  -(n+1))
  5<<1  = 10  (×2)
  5>>1  = 2   (÷2)

struct vs class:
  struct → public default | class → private default

Friend function:
  NOT a member | has private access | not inherited
  Called: funcName(obj), NOT obj.funcName()

Scope resolution (::):
  global var: ::x
  outside definition: ClassName::method()
  static: ClassName::staticMember
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Bihar History: Dr. Rajendra Prasad

---

## 🔷 WHY RAJENDRA PRASAD MATTERS FOR BPSC TRE

```
Dr. Rajendra Prasad is Bihar's GREATEST son in national politics.
He is featured in:
→ Bihar History questions (certain in BPSC)
→ Constitution/Governance questions (as President)
→ Freedom Movement questions (all three major movements)
→ Often appears in 2-3 questions per BPSC paper

For BPSC TRE, knowing Rajendra Prasad deeply = free marks.
```

---

## 🔷 EARLY LIFE — THE BRILLIANT STUDENT

### Birth and Family:
```
Full name: Dr. Rajendra Prasad
Born: December 3, 1884
Birthplace: Zeradei village, Siwan district, Bihar
Father: Mahadev Sahai (a Sanskrit and Persian scholar)
Mother: Kamleshwari Devi (deeply religious, told young Rajendra the Ramayana)
```

### Academic Excellence — The Topper:
```
Early schooling: At home in Chapra (Saran district)
→ Learned Sanskrit from Maulvi (teacher) as well as Sanskrit scholars
→ Was extraordinarily gifted — remembered things after reading once

Calcutta University entrance exam (1902):
→ First in the entire Calcutta University entrance examination
→ Scholarship of ₹30 per month (enormous for that time!)

Presidency College, Calcutta:
→ Studied under great teachers
→ Graduated with distinction

Calcutta University:
→ MA in Economics — First Class First
→ So brilliant that examiner wrote: "The examinee is better than the examiner"

Law:
→ LL.B., then LL.D. from Allahabad University
→ Doctor of Law — why he is called "Dr."
→ Set up law practice in Calcutta (1911), then moved to Patna (1916)
```

---

## 🔷 ENTRY INTO POLITICS — MEETING GANDHI

### Lucknow Congress Session — 1916:
```
Rajendra Prasad attended the 1916 Lucknow Congress session.
Here he first met Mahatma Gandhi.
This meeting changed his life's direction completely.
```

### Champaran Satyagraha — 1917 (MOST IMPORTANT BIHAR LINK):
```
When Gandhi arrived in Bihar for Champaran (April 1917):
→ Rajendra Prasad was one of the FIRST to receive Gandhi in Patna
→ He joined Gandhi at Champaran, gave up his legal practice
→ Helped investigate the Tinkathia system exploitation
→ Organized legal assistance for farmers
→ Dedicated himself fully to the movement

Later he wrote:
"The Champaran movement was a turning point in my life.
After meeting Gandhi in Champaran, I never returned to law."
```

---

## 🔷 ROLE IN MAJOR FREEDOM MOVEMENTS

### Non-Cooperation Movement (1920–22):
```
→ Gave up his flourishing law practice PERMANENTLY
→ Resigned from the Patna High Court Bar
→ Founded the Bihar Vidyapeeth (1921) in Patna
   → Alternative national university for students who boycotted British institutions
   → Bihar Vidyapeeth still exists today!
→ Organized the NCM across Bihar
→ Arrested multiple times
→ Encouraged Bihar's students to leave British schools and join national education
```

### Civil Disobedience Movement (1930–34):
```
→ Participated actively — arrested and imprisoned
→ Organized salt satyagraha marches across Bihar
→ Led Bihar's boycott of foreign cloth
→ Helped coordinate the movement with Gandhi's Danda March phase
→ Despite being arrested, Bihar's movement continued due to his organizational base
```

### Quit India Movement (1942):
```
→ Arrested in August 1942 along with other major leaders
→ Imprisoned at Bankipur Jail, Patna
→ Even from prison, inspired Bihar's resistance
→ Bankipur Central Jail (now Patna) was his prison during QIM
```

---

## 🔷 ROLE IN CONSTITUENT ASSEMBLY

### Selection as President:
```
Date: December 9, 1946 (first meeting of Constituent Assembly)
Who became President: Dr. Rajendra Prasad — ELECTED PRESIDENT
                      of the Constituent Assembly

Why him?
→ Most respected Congress leader
→ Impeccable integrity — no one questioned his impartiality
→ Symbol of Hindu-Muslim unity (he had worked with all communities)
→ Bihar's most prominent national figure
```

### His Work in the Constituent Assembly:
```
Duration: Constituent Assembly sat for 2 years, 11 months, 18 days
Sessions: 11 sessions
Number of sittings: 166
Total days: December 9, 1946 → November 26, 1949

Rajendra Prasad as President:
→ Presided over ALL 166 sittings
→ Maintained order and impartiality throughout
→ Brought together members with vastly different views
→ Signed the Constitution on November 26, 1949

→ November 26 = Constitution Day (Samvidhan Divas)
  (now officially celebrated due to his signing)
```

---

## 🔷 FIRST PRESIDENT OF INDIA

### Election as President:
```
India's independence: August 15, 1947
First President election: January 26, 1950 (same day Constitution enacted)
President-elect: Dr. Rajendra Prasad
Inaugurated: January 26, 1950 — Republic Day

Fun fact: Rajendra Prasad was acting as "President of Constituent Assembly"
from 1946. He was ELECTED as first President TWICE — in 1950 and 1957.
He served two full terms (unique in India's presidential history).
```

### Presidency Details:
```
First President of India: Dr. Rajendra Prasad
Term: January 26, 1950 – May 13, 1962 (12 years and more!)
Two Terms:
  First term:  January 26, 1950 – May 13, 1957
  Second term: May 13, 1957 – May 13, 1962

Significance:
→ Longest serving President of India (12 years)
→ Only President to serve two full terms consecutively
→ As President, he maintained above-party dignity and constitutional propriety
```

### Notable Acts as President:
```
1. Rashtrapati Bhavan practices:
   → He lived very simply in President's House
   → Gave up European-style formal dress at official functions
   → Introduced Indian dress (dhoti, achkan) at state functions

2. Agricultural connection:
   → Would visit Patna and Bihar regularly
   → Maintained his connection with Bihar farmers (his roots)

3. Somnath Temple controversy (1951):
   → Attended the inauguration of reconstructed Somnath Temple
     despite Prime Minister Nehru's objection
   → This was a significant assertion of Presidential independence

4. Bharat Ratna:
   → Awarded Bharat Ratna in 1962 (while still President!)
   → One of only a few Presidents to receive it while in office
```

---

## 🔷 AFTER PRESIDENCY — RETIREMENT AND DEATH

```
May 14, 1962: Rajendra Prasad retired as President
              Moved to Patna Sahib (Bankipur)
              Lived at Sadaqat Ashram, Patna

February 28, 1963: Dr. Rajendra Prasad passed away
                   At Sadaqat Ashram, Patna, Bihar

Legacy:
→ Sadaqat Ashram (Patna) is now a pilgrimage site
→ Bihar Congress uses Sadaqat Ashram as its headquarters
→ Several institutions named after him in Bihar and India:
   → Rajendra Prasad Central Agricultural University, Pusa, Bihar
   → Dr. Rajendra Prasad Government Medical College, Chapra
   → Rajendra Smriti Sangrahalaya (museum in Patna)
```

---

## 🔷 RAJENDRA PRASAD'S WRITINGS (Important for Exam)

| Work | Significance |
|------|-------------|
| *India Divided* (1946) | Against partition — argued for united India |
| *Autobiography* | His personal account of freedom struggle |
| *Champaran ka Satyagrah* | About Champaran movement |
| *Mahatma Gandhi and Bihar* | Gandhi's Bihar connection |
| *At the feet of Mahatma* | His tribute to Gandhi |
| *Satyagrah in Champaran* | First-hand account |

---

## 🔷 TIMELINE — RAJENDRA PRASAD'S LIFE

```
RAJENDRA PRASAD — COMPLETE TIMELINE
═══════════════════════════════════════════════════

Dec 3, 1884   → Born at Zeradei, Siwan, Bihar
1902          → First in Calcutta University entrance exam (scholarship)
1907          → MA in Economics — First Class First
                "Examinee is better than the examiner" remark
1916          → Meets Gandhi at Lucknow Congress session
April 1917    → Champaran Satyagraha — receives Gandhi in Patna
              → Gives up law practice permanently
1920–22       → Non-Cooperation Movement
              → Founds Bihar Vidyapeeth (1921)
1930–34       → Civil Disobedience Movement
              → Arrested, imprisoned
1934          → President of INC (Bombay session)
              → Also President of INC again in 1939
1942          → Quit India Movement — imprisoned at Bankipur Jail
Dec 9, 1946   → Elected President of Constituent Assembly
Nov 26, 1949  → Signs the Constitution
Jan 26, 1950  → Becomes First President of India
1957          → Re-elected President (second term)
1962          → Awarded Bharat Ratna
May 14, 1962  → Retires as President
Feb 28, 1963  → Passes away at Sadaqat Ashram, Patna

═══════════════════════════════════════════════════
```

---

## 🔷 KEY FACTS TABLE — QUICK REVISION

| Category | Fact |
|----------|------|
| Birthdate | December 3, 1884 |
| Birthplace | Zeradei, Siwan, Bihar |
| Death | February 28, 1963, Patna |
| Education | MA Economics (First Class), LL.B., LL.D. |
| Notable exam remark | "Examinee is better than the examiner" |
| First met Gandhi | Lucknow Congress session, 1916 |
| Champaran role | Received Gandhi in Patna; helped investigation |
| NCM contribution | Founded Bihar Vidyapeeth (1921) |
| Constituent Assembly | Elected President, December 9, 1946 |
| Constitution signing | November 26, 1949 |
| First President | January 26, 1950 |
| Presidential terms | Two terms (1950–1962) — longest serving |
| Bharat Ratna | 1962 (while still President!) |
| Retirement home | Sadaqat Ashram, Patna |
| Major book | *India Divided* (1946) |

---

## 🔷 BIHAR INSTITUTIONS CONNECTED TO RAJENDRA PRASAD

```
1. Bihar Vidyapeeth, Patna (1921)
   → Founded by Rajendra Prasad during NCM
   → Alternative national university

2. Rajendra Prasad Central Agricultural University, Pusa
   → Named after him in Samastipur district, Bihar

3. Sadaqat Ashram, Patna
   → His final residence; Bihar INC headquarters now

4. Rajendra Smriti Sangrahalaya
   → Museum dedicated to him in Patna
```

---

## 🔷 MEMORY TRICKS

```
"Zeradei → Siwan → Saran → Bihar → India's First President"
(His journey from a small village to the nation's highest office)

"RAJENDRA = RAJE OF BIHAR" (raje = king in Hindi)
(He was Bihar's greatest contribution to independent India's government)

"December 3 born → January 26 President" (both December/January)
(Born December 3, 1884; became President January 26, 1950)

"12 YEARS as President — LONGEST"
(1950–1962 = 12 years — no other President served this long)

"Bihar Vidyapeeth 1921 = NCM gift to Bihar"
(Rajendra Prasad's concrete contribution during NCM)

"CHAMPARAN → gave up law" (turning point)
"After meeting Gandhi in Champaran, he never returned to law"
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Increment/Decrement, Bitwise, Boolean, struct/class, Friend Functions

---

**Q1.** What is the output of the following code?
```cpp
int i = 5;
cout << i++ << " " << ++i;
```
(A) 5 7
(B) 6 7
(C) 5 6
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the output of:
```cpp
int a = 10;
int b = a++;
int c = ++a;
cout << b << " " << c;
```
(A) 10 11
(B) 10 12
(C) 11 12
(D) More than one of the above
(E) None of the above

---

**Q3.** What is `5 & 3` in C++?
(A) 7
(B) 6
(C) 1
(D) More than one of the above
(E) None of the above

---

**Q4.** What is `5 | 3` in C++?
(A) 1
(B) 7
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q5.** What is `5 ^ 3` in C++?
(A) 7
(B) 1
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q6.** What is `~5` in C++?
(A) -5
(B) -6
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q7.** What is `5 << 2` in C++?
(A) 10
(B) 20
(C) 1
(D) More than one of the above
(E) None of the above

---

**Q8.** What is `20 >> 2` in C++?
(A) 80
(B) 10
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the output of:
```cpp
int x = 7;
cout << (x ^ x);
```
(A) 7
(B) 14
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q10.** Which is the default access specifier in a C++ `struct`?
(A) private
(B) protected
(C) public
(D) More than one of the above
(E) None of the above

---

**Q11.** Which is the default access specifier in a C++ `class`?
(A) public
(B) protected
(C) private
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following is TRUE about a friend function?
(A) It is a member function of the class
(B) It has access to private and protected members of the class
(C) It must be called using an object of the class
(D) More than one of the above
(E) None of the above

---

**Q13.** Is friendship in C++ inherited?
(A) Yes — derived class also gets friend's access
(B) No — friendship is NOT inherited
(C) Only if explicitly declared in derived class
(D) More than one of the above
(E) None of the above

---

**Q14.** What is the output of:
```cpp
int i = 0;
while (i++ < 3) cout << i << " ";
```
(A) 0 1 2
(B) 1 2 3
(C) 0 1 2 3
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the output of:
```cpp
cout << (5 > 3);
cout << (5 < 3);
```
(A) true false
(B) 1 0
(C) 1 -1
(D) More than one of the above
(E) None of the above

---

**Q16.** What is the Scope Resolution Operator in C++?
(A) `.`
(B) `->`
(C) `::`
(D) More than one of the above
(E) None of the above

---

**Q17.** What causes a Segmentation Fault in recursive functions?
(A) Using return statement
(B) Infinite recursion (missing or incorrect base case) — stack overflow
(C) Recursive function with a parameter
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following correctly uses `::` to access a global variable?
```cpp
int x = 100;
void func() { int x = 50; cout << ___; }
```
(A) `x`
(B) `global::x`
(C) `::x`
(D) More than one of the above
(E) None of the above

---

**Q19.** What is the output of `cout << (3 & 1)`?
(A) 0
(B) 1
(C) 3
(D) More than one of the above
(E) None of the above

---

**Q20.** What is the output of:
```cpp
int a = 5, b = 5;
a = a ^ b;
b = a ^ b;
a = a ^ b;
cout << a << " " << b;
```
(A) 0 0
(B) 5 5
(C) 0 5
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following operations does `n & 1` perform?
(A) Divides n by 1
(B) Checks if n is odd (returns 1) or even (returns 0)
(C) Sets the last bit of n to 1
(D) More than one of the above
(E) None of the above

---

**Q22.** What is `~0` in C++?
(A) 0
(B) 1
(C) -1
(D) More than one of the above
(E) None of the above

---

**Q23.** A friend function is declared inside the class with the keyword:
(A) `extern`
(B) `friend`
(C) `public`
(D) More than one of the above
(E) None of the above

---

**Q24.** In C++, what is the difference between `struct` and `class`?
(A) struct cannot have constructors; class can
(B) struct default access is public; class default access is private
(C) struct cannot inherit; class can
(D) More than one of the above
(E) None of the above

---

**Q25.** What is the output of:
```cpp
int x = 4;
cout << (x << 1) << " " << (x >> 1);
```
(A) 8 2
(B) 4 4
(C) 5 3
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Bihar History: Dr. Rajendra Prasad

---

**Q26.** Dr. Rajendra Prasad was born in which village and district of Bihar?
(A) Motihari, East Champaran
(B) Zeradei, Siwan
(C) Sitabdiara, Saran
(D) More than one of the above
(E) None of the above

---

**Q27.** Dr. Rajendra Prasad's date of birth was:
(A) December 3, 1884
(B) January 26, 1884
(C) November 26, 1884
(D) More than one of the above
(E) None of the above

---

**Q28.** The remark "The examinee is better than the examiner" was made about Rajendra Prasad at which examination?
(A) Matriculation examination
(B) MA Economics examination at Calcutta University
(C) LL.B. examination
(D) More than one of the above
(E) None of the above

---

**Q29.** Rajendra Prasad first met Mahatma Gandhi at which Congress session?
(A) Champaran, 1917
(B) Lucknow Congress session, 1916
(C) Nagpur session, 1920
(D) More than one of the above
(E) None of the above

---

**Q30.** During the Champaran Satyagraha (1917), what role did Rajendra Prasad play?
(A) He led the movement independently before Gandhi arrived
(B) He received Gandhi in Patna and assisted in investigating farmer exploitation
(C) He was the District Magistrate who filed a case against Gandhi
(D) More than one of the above
(E) None of the above

---

**Q31.** The Bihar Vidyapeeth was founded by Rajendra Prasad in:
(A) 1917
(B) 1921
(C) 1930
(D) More than one of the above
(E) None of the above

---

**Q32.** Bihar Vidyapeeth was established during which movement?
(A) Champaran Satyagraha
(B) Non-Cooperation Movement
(C) Civil Disobedience Movement
(D) More than one of the above
(E) None of the above

---

**Q33.** Rajendra Prasad was imprisoned at which jail during the Quit India Movement (1942)?
(A) Hazaribagh Central Jail
(B) Bankipur Jail, Patna
(C) Yerwada Prison, Pune
(D) More than one of the above
(E) None of the above

---

**Q34.** Rajendra Prasad was elected President of the Constituent Assembly on:
(A) November 26, 1949
(B) January 26, 1950
(C) December 9, 1946
(D) More than one of the above
(E) None of the above

---

**Q35.** Dr. Rajendra Prasad signed the Constitution of India on:
(A) January 26, 1950
(B) November 26, 1949
(C) August 15, 1947
(D) More than one of the above
(E) None of the above

---

**Q36.** Dr. Rajendra Prasad became the first President of India on:
(A) August 15, 1947
(B) November 26, 1949
(C) January 26, 1950
(D) More than one of the above
(E) None of the above

---

**Q37.** How many terms did Dr. Rajendra Prasad serve as President of India?
(A) One term
(B) Two terms (unique in Indian history)
(C) Three terms
(D) More than one of the above
(E) None of the above

---

**Q38.** For how long did Rajendra Prasad serve as President of India?
(A) 5 years
(B) 7 years
(C) 12 years (1950–1962, two full terms)
(D) More than one of the above
(E) None of the above

---

**Q39.** The Bharat Ratna was awarded to Dr. Rajendra Prasad in:
(A) 1952
(B) 1962
(C) 1963 (posthumously)
(D) More than one of the above
(E) None of the above

---

**Q40.** Dr. Rajendra Prasad passed away at which location in Bihar?
(A) Zeradei, Siwan
(B) Sadaqat Ashram, Patna
(C) Bihar Vidyapeeth, Patna
(D) More than one of the above
(E) None of the above

---

**Q41.** Which of the following books was written by Dr. Rajendra Prasad?
(A) *India Divided*
(B) *Discovery of India*
(C) *Hind Swaraj*
(D) More than one of the above
(E) None of the above

---

**Q42.** In his book *India Divided* (1946), Rajendra Prasad argued for:
(A) Immediate partition of India along religious lines
(B) A united India — against partition
(C) Dominion Status within the British Empire
(D) More than one of the above
(E) None of the above

---

**Q43.** The Rajendra Prasad Central Agricultural University is located in which district of Bihar?
(A) Siwan
(B) Patna
(C) Samastipur (Pusa)
(D) More than one of the above
(E) None of the above

---

**Q44.** Which institution in Bihar was founded by Rajendra Prasad during the Non-Cooperation Movement?
(A) Patna University
(B) Bihar Vidyapeeth
(C) Nalanda Open University
(D) More than one of the above
(E) None of the above

---

**Q45.** Rajendra Prasad attended the Constituent Assembly as its President for how many days?
(A) 100 days
(B) 166 days (166 sittings over about 3 years)
(C) 200 days
(D) More than one of the above
(E) None of the above

---

**Q46.** Which controversy did Rajendra Prasad engage in with Prime Minister Nehru regarding a temple?
(A) He attended the inauguration of Kashi Vishwanath Temple against Nehru's wishes
(B) He attended the inauguration of reconstructed Somnath Temple despite Nehru's objection
(C) He funded the construction of a Ram temple against Nehru's advice
(D) More than one of the above
(E) None of the above

---

**Q47.** Rajendra Prasad was the President of INC (Indian National Congress) in which years?
(A) 1930 and 1940
(B) 1934 and 1939
(C) 1929 and 1942
(D) More than one of the above
(E) None of the above

---

**Q48.** Arrange the following in CORRECT CHRONOLOGICAL ORDER of Rajendra Prasad's life:
1. Becomes First President of India
2. Founds Bihar Vidyapeeth
3. Receives Gandhi in Patna for Champaran
4. Elected President of Constituent Assembly

(A) 3 → 2 → 4 → 1
(B) 2 → 3 → 4 → 1
(C) 3 → 4 → 2 → 1
(D) More than one of the above
(E) None of the above

---

**Q49.** The Sadaqat Ashram in Patna is significant because:
(A) It is where Gandhi lived during Champaran Satyagraha
(B) It was Rajendra Prasad's final residence; now Bihar INC headquarters
(C) It is where the Bihar Vidyapeeth was originally located
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY describes Dr. Rajendra Prasad's contribution to Bihar?
(A) Founded Bihar Vidyapeeth during NCM; received Gandhi for Champaran; Bihar's first President of India
(B) Led the Champaran movement independently without Gandhi's involvement
(C) Founded the Indian National Congress in Bihar
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ Attempt ALL 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (E) | i++ + ++i on same variable = undefined behavior (compiler-dependent; often 5 7 or similar but technically UB) |
| 2 | (B) | b=a++(b=10, a→11); c=++a(a→12, c=12); output: 10 12 |
| 3 | (C) | 5=101, 3=011, AND=001=1 |
| 4 | (B) | 5=101, 3=011, OR=111=7 |
| 5 | (C) | 5=101, 3=011, XOR=110=6 |
| 6 | (B) | ~n = -(n+1); ~5 = -6 |
| 7 | (B) | 5 << 2 = 5 × 4 = 20 |
| 8 | (C) | 20 >> 2 = 20 ÷ 4 = 5 |
| 9 | (C) | Any number XOR itself = 0; 7^7=0 |
| 10 | (C) | struct default = public |
| 11 | (C) | class default = private |
| 12 | (B) | Friend function has access to private/protected members |
| 13 | (B) | Friendship is NOT inherited in C++ |
| 14 | (B) | i++ checks old value: 0<3✓,1<3✓,2<3✓ then prints i=1,2,3 |
| 15 | (B) | Comparison returns 0 or 1; 5>3=1, 5<3=0 |
| 16 | (C) | :: is the scope resolution operator |
| 17 | (B) | Missing base case → infinite recursion → stack overflow → segfault |
| 18 | (C) | ::x accesses the global x |
| 19 | (B) | 3=011, 1=001, AND=001=1 |
| 20 | (B) | XOR swap: a=5^5=0, b=0^5=5, a=0^5=5; output: 5 5 |
| 21 | (B) | n&1 checks last bit: 1=odd, 0=even |
| 22 | (C) | ~0 = -(0+1) = -1 |
| 23 | (B) | `friend` keyword declares a friend function |
| 24 | (B) | The only difference: struct=public default, class=private default |
| 25 | (A) | 4<<1=8, 4>>1=2; output: 8 2 |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Zeradei village, Siwan district, Bihar |
| 27 | (A) | December 3, 1884 |
| 28 | (B) | MA Economics exam — famous examiner's remark |
| 29 | (B) | Lucknow Congress session, 1916 |
| 30 | (B) | Received Gandhi in Patna; helped investigate exploitation |
| 31 | (B) | Bihar Vidyapeeth founded 1921 |
| 32 | (B) | Non-Cooperation Movement (1920–22) |
| 33 | (B) | Bankipur Jail, Patna during Quit India |
| 34 | (C) | December 9, 1946 — first sitting of Constituent Assembly |
| 35 | (B) | November 26, 1949 (Constitution Day) |
| 36 | (C) | January 26, 1950 — Republic Day |
| 37 | (B) | Two terms — unique in Indian presidential history |
| 38 | (C) | 12 years (1950–1962) — longest serving President |
| 39 | (B) | Bharat Ratna 1962 (while still President!) |
| 40 | (B) | Sadaqat Ashram, Patna |
| 41 | (A) | *India Divided* — by Rajendra Prasad |
| 42 | (B) | Argued for united India — against partition |
| 43 | (C) | Rajendra Prasad Central Agricultural University at Pusa, Samastipur |
| 44 | (B) | Bihar Vidyapeeth |
| 45 | (B) | 166 sittings of Constituent Assembly |
| 46 | (B) | Somnath Temple inauguration — despite Nehru's objection |
| 47 | (B) | INC President in 1934 and 1939 |
| 48 | (A) | Champaran(1917) → Bihar Vidyapeeth(1921) → CA President(1946) → President(1950) |
| 49 | (B) | His final residence; now Bihar INC headquarters |
| 50 | (A) | All three achievements correctly stated |

---
---

# 🔁 DAY 13 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — C++ Output Prediction

### Increment/Decrement Rules:
```
i=5: i++  → use 5, THEN i=6  (post: USE then increment)
i=5: ++i  → i=6, use 6        (pre: INCREMENT then use)
i=5: b=i++ → b=5, i=6
i=5: b=++i → i=6, b=6
Loop: while(i++ < 3) checks OLD value, prints NEW value → prints 1,2,3
```

### Bitwise Quick Reference (a=5=0101, b=3=0011):
```
5 & 3 = 0001 = 1    (AND:  both 1 → 1)
5 | 3 = 0111 = 7    (OR:   any 1 → 1)
5 ^ 3 = 0110 = 6    (XOR:  different → 1, same → 0)
~5    = -6           (NOT:  ~n = -(n+1))
~0    = -1
5<<1  = 10          (left shift = ×2)
5<<2  = 20          (×4)
5>>1  = 2           (right shift = ÷2)
n & 1 = odd/even test (1=odd, 0=even)
n ^ n = 0           (XOR self = always 0)
```

### struct vs class (The Only Difference):
```
struct → default = PUBLIC
class  → default = PRIVATE
Both support methods, constructors, inheritance, access specifiers.
```

### Friend Function Rules:
```
→ NOT a member function (no object needed to call it)
→ CAN access private AND protected members
→ Declared inside class with 'friend' keyword
→ Defined OUTSIDE class (no ClassName:: needed)
→ Friendship NOT inherited, NOT reciprocal (one-way)
```

### Scope Resolution `::` Uses:
```
::x                  → global x (when local x shadows it)
ClassName::method    → define method outside class
ClassName::static    → access static member
Namespace::member    → access namespace member
```

### Segmentation Fault:
```
Cause: Infinite recursion (missing base case) → stack overflow
Also: NULL pointer dereference, out-of-bounds (sometimes)
Type: RUNTIME error (not compile-time)
```

---

## ⚡ RAPID FIRE — Rajendra Prasad

### Non-Negotiable Facts:
```
Born:          December 3, 1884 — Zeradei, Siwan, Bihar
Died:          February 28, 1963 — Sadaqat Ashram, Patna
Education:     MA Economics (First), LL.D.
Exam remark:   "Examinee is better than the examiner" (MA Economics)
Met Gandhi:    Lucknow Congress session, 1916
Champaran:     Received Gandhi in Patna; helped investigation; gave up law
Bihar Vidyapeeth: Founded 1921 during Non-Cooperation Movement (still exists!)
QIM prison:    Bankipur Jail, Patna (1942)
CA President:  Elected December 9, 1946
Constitution:  Signed November 26, 1949
1st President: January 26, 1950
Terms:         TWO (1950–1962) — longest serving (12 years)
Bharat Ratna:  1962 (while still President!)
Book:          India Divided (1946) — argued against partition
```

### Bihar-Specific for BPSC:
```
→ FROM Bihar (Siwan) = high BPSC probability
→ Bihar Vidyapeeth (Patna) = his concrete gift to Bihar
→ Sadaqat Ashram (Patna) = his home, now Bihar INC HQ
→ RPKV Pusa (Samastipur) = agricultural university named after him
→ Champaran link = 1917 = received Gandhi = gave up law = everything changed
```

### Common Exam Traps:
1. Birthplace = **Zeradei, Siwan** (NOT Patna, NOT Champaran)
2. Bihar Vidyapeeth = **1921** during **NCM** (NOT 1917, NOT CDM)
3. Bharat Ratna = **1962** while STILL President (not posthumous)
4. Constituent Assembly President elected = **December 9, 1946**
5. Constitution signed = **November 26, 1949** (NOT January 26, 1950)
6. *India Divided* = written by **Rajendra Prasad** (NOT Jawaharlal Nehru)
7. QIM jail = **Bankipur, Patna** (NOT Hazaribagh like JP)

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. `i++` = use then increment; `++i` = increment then use; while(i++ < 3) prints 1,2,3
2. `~n = -(n+1)`: ~5=-6, ~0=-1; `n^n=0`; `5&3=1`, `5|3=7`, `5^3=6`
3. struct = public default; class = private default (ONLY difference!)
4. Friend function: NOT a member, accesses private, NOT inherited, called like regular function
5. Rajendra Prasad: Zeradei Siwan Bihar; Bihar Vidyapeeth 1921; 1st President 1950–1962 (12 yrs); Bharat Ratna 1962

---

*Next: Day 14 — C++ OOP Review: Constructors, Destructors, Virtual Functions + Indian Constitution Overview*
