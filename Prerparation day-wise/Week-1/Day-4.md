# 🎯 BPSC TRE 4.0 — DAY 4 COMPLETE STUDY MATERIAL
## Virtual Inheritance & Diamond Problem (CS) + Number System Basics (GS Maths)
### Target: TOP RANK | Prepared from PYQ Analysis of TRE 1.0, 2.0, 3.0

---

> **📌 DAY 4 OVERVIEW**
> - **Morning (1.5 hrs):** CS — Virtual Inheritance, Diamond Problem, Virtual Functions, Overloading vs Overriding
> - **Afternoon (1 hr):** GS Maths — Number System (Divisibility, HCF/LCM, Types of Numbers)
> - **Evening (1 hr):** 25 PYQ-style MCQs (CS + GS combined)
> - **Night (30 min):** Write 5-bullet summary in your notebook

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 🖥️ PART 1 — COMPUTER SCIENCE (Morning: 1.5 hrs)
# Virtual Inheritance, Diamond Problem, Virtual Functions
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

## 📌 SECTION 1.1 — THE DIAMOND PROBLEM (Most Important!)

### What Is the Diamond Problem?

The Diamond Problem occurs in **multiple inheritance** when:
- Two classes B and C both inherit from class A
- A fourth class D inherits from BOTH B and C

This creates **ambiguity** — D gets TWO copies of A's data.

```
DIAMOND PROBLEM DIAGRAM:
════════════════════════

         ┌─────────┐
         │  Class A │   ← The "top" — has some data/function
         │  int x=5 │
         └────┬────┘
              │
     ┌────────┴────────┐
     │                 │
  ┌──▼──┐           ┌──▼──┐
  │  B  │           │  C  │   ← B and C BOTH inherit from A
  └──┬──┘           └──┬──┘
     │                 │
     └────────┬────────┘
              │
         ┌────▼────┐
         │  Class D │   ← D inherits from BOTH B and C
         └─────────┘

RESULT WITHOUT virtual:
D has TWO copies of A's data:
  → D::B::A::x  (one copy through B)
  → D::C::A::x  (another copy through C)

When D tries to access x → AMBIGUITY → COMPILE ERROR!
```

### Real-Life Analogy:

Imagine you are writing a letter. You have two parents — your father got his handwriting from your grandfather, your mother ALSO got handwriting from the same grandfather. You (child) inherit from both parents. If you ask "whose handwriting style should I use?" — **confusion!** That's the diamond problem.

---

### Code Example — Diamond Problem WITHOUT Virtual Inheritance:

```cpp
#include <iostream>
using namespace std;

class A {
public:
    int x;
    A() { x = 10; }
    void show() { cout << "A::show() x = " << x << endl; }
};

class B : public A {   // B inherits A
};

class C : public A {   // C also inherits A
};

class D : public B, public C {   // D inherits B AND C
// D now has TWO copies of A:
//   D::B::A  and  D::C::A
};

int main() {
    D obj;
    // obj.show();   // ❌ ERROR! Ambiguous — which show() to call?
    // obj.x = 5;    // ❌ ERROR! Ambiguous — which x?
    
    obj.B::show();   // ✅ Must specify path
    obj.C::show();   // ✅ Must specify path
    return 0;
}
```

**Output of `obj.B::show()`:** `A::show() x = 10`
**Output of `obj.C::show()`:** `A::show() x = 10`

> **⚠️ EXAM TRAP:** Without virtual, `obj.show()` gives **compile error** (ambiguity), not runtime error.

---

## 📌 SECTION 1.2 — VIRTUAL INHERITANCE (The Solution)

### What is Virtual Inheritance?

**Virtual inheritance** ensures that only **ONE copy** of the base class exists in the derived class, no matter how many paths lead to it.

```
VIRTUAL INHERITANCE DIAGRAM:
════════════════════════════

         ┌─────────┐
         │  Class A │   ← Only ONE copy of A exists
         │  int x=5 │
         └────┬────┘
              │
     ┌────────┴────────┐
     │                 │
  ┌──▼──┐           ┌──▼──┐
  │  B  │ (virtual) │  C  │ (virtual)  ← Both inherit A VIRTUALLY
  └──┬──┘           └──┬──┘
     │                 │
     └────────┬────────┘
              │
         ┌────▼────┐
         │  Class D │   ← D has only ONE copy of A now ✅
         └─────────┘
```

### Syntax of Virtual Inheritance:

```cpp
class B : virtual public A {   // ← keyword 'virtual' before 'public'
    // ...
};

class C : virtual public A {   // ← same here
    // ...
};

class D : public B, public C { // Normal inheritance for D
    // D now has only ONE copy of A
};
```

> **🔑 KEY RULE:** The `virtual` keyword is placed in the **INTERMEDIATE classes** (B and C), NOT in class A or D.

### Complete Working Example:

```cpp
#include <iostream>
using namespace std;

class A {
public:
    int x;
    A() { x = 10; }
    void show() { cout << "A::show() x = " << x << endl; }
};

class B : virtual public A {    // virtual inheritance
};

class C : virtual public A {    // virtual inheritance
};

class D : public B, public C {  // no ambiguity now
};

int main() {
    D obj;
    obj.show();      // ✅ Works! Only ONE copy of A
    obj.x = 50;      // ✅ Works! Only ONE x
    obj.show();      // Output: A::show() x = 50
    return 0;
}
```

**Output:**
```
A::show() x = 10
A::show() x = 50
```

---

## 📌 SECTION 1.3 — VIRTUAL FUNCTIONS

### What is a Virtual Function?

A **virtual function** is a member function in the base class that can be **overridden** in derived class and the correct version is called at **runtime** (not compile time).

> **Simple meaning:** The program decides WHICH function to call while running (runtime), not while compiling.

### Syntax:

```cpp
class Base {
public:
    virtual void display() {    // ← 'virtual' keyword
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() {            // Overrides Base's display
        cout << "Derived display" << endl;
    }
};

int main() {
    Base *ptr;           // Base class pointer
    Derived obj;
    ptr = &obj;          // pointer points to derived object
    
    ptr->display();      // ← Calls DERIVED's display (runtime polymorphism)
    return 0;
}
```

**Output:** `Derived display`

> **Without virtual:** `ptr->display()` would print `Base display` (wrong! compile-time binding)
> **With virtual:** `ptr->display()` prints `Derived display` (correct! runtime binding)

---

### Virtual Function Rules (PYQ Trap Points):

```
┌─────────────────────────────────────────────────────┐
│           VIRTUAL FUNCTION RULES                    │
├─────────────────────────────────────────────────────┤
│ 1. virtual keyword only in BASE class declaration   │
│ 2. CANNOT be static (static = no object needed)     │
│ 3. CANNOT be constructor (constructor not virtual)  │
│ 4. CAN be destructor (virtual destructor important) │
│ 5. Accessed through BASE class pointer/reference    │
│ 6. Resolved at RUNTIME (dynamic dispatch)           │
└─────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 1.4 — PURE VIRTUAL FUNCTION & ABSTRACT CLASS

### Pure Virtual Function

A **pure virtual function** has NO body (no implementation) in the base class. It forces derived classes to PROVIDE their own implementation.

### Syntax:

```cpp
class Shape {
public:
    virtual double area() = 0;    // ← "= 0" makes it PURE virtual
    virtual void draw() = 0;      // another pure virtual
};
```

> **🔑 Syntax to memorize:** `virtual returnType functionName() = 0;`
> The `= 0` does NOT mean "return 0". It means "no implementation".

### Abstract Class

A class that has **at least one pure virtual function** is called an **Abstract Class**.

```
┌──────────────────────────────────────────────┐
│           ABSTRACT CLASS RULES               │
├──────────────────────────────────────────────┤
│ ✅ Has at least ONE pure virtual function    │
│ ✅ Can have non-virtual functions too        │
│ ✅ Can have constructors                     │
│ ❌ CANNOT create objects of abstract class   │
│ ❌ Derived class MUST implement all PVFs     │
│    (or else derived class is also abstract!) │
└──────────────────────────────────────────────┘
```

### Example:

```cpp
class Shape {           // Abstract class
public:
    virtual double area() = 0;   // Pure virtual
    void printInfo() {           // Normal function — allowed
        cout << "I am a shape" << endl;
    }
};

class Circle : public Shape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    double area() {    // MUST provide implementation
        return 3.14 * radius * radius;
    }
};

int main() {
    // Shape s;        // ❌ ERROR! Cannot create abstract class object
    Circle c(5.0);     // ✅ OK — Circle is concrete
    cout << c.area();  // 78.5
    return 0;
}
```

---

### Virtual vs Pure Virtual — Key Comparison Table:

```
┌────────────────┬─────────────────────┬──────────────────────────┐
│   Property     │  Virtual Function   │  Pure Virtual Function   │
├────────────────┼─────────────────────┼──────────────────────────┤
│ Has body?      │ YES (has default)   │ NO (= 0)                 │
│ Must override? │ No (optional)       │ YES (mandatory)          │
│ Class type?    │ Concrete class      │ Abstract class           │
│ Object of class│ Can create          │ CANNOT create            │
│ Syntax         │ virtual f() { }     │ virtual f() = 0;         │
│ Called         │ At runtime          │ Only in derived class    │
└────────────────┴─────────────────────┴──────────────────────────┘
```

---

## 📌 SECTION 1.5 — OVERRIDE KEYWORD (C++11)

### What is `override`?

The `override` keyword explicitly tells the compiler: "I am intentionally overriding a base class virtual function."

```cpp
class Base {
public:
    virtual void show() { cout << "Base" << endl; }
};

class Derived : public Base {
public:
    void show() override {   // ← 'override' confirms this overrides Base::show()
        cout << "Derived" << endl;
    }
    
    // void shwo() override;  // ← COMPILE ERROR! 'shwo' doesn't match any Base virtual
    //                               Without 'override', it would silently create new function
};
```

> **Why use override?** It catches **spelling mistakes** at compile time. Without it, a typo creates a NEW function instead of overriding — a silent bug.

---

## 📌 SECTION 1.6 — OVERLOADING vs OVERRIDING (PYQ Favourite!)

### Method Overloading (Compile-time Polymorphism)

**Same function name, different parameters** in the **SAME class**.

```cpp
class Calculator {
public:
    int add(int a, int b) { return a + b; }           // version 1
    double add(double a, double b) { return a + b; }  // version 2
    int add(int a, int b, int c) { return a+b+c; }    // version 3
};
```

**Which version to call is decided at COMPILE TIME** based on argument types.

### Method Overriding (Runtime Polymorphism)

**Same function name, same parameters** in **DIFFERENT classes** (parent-child).

```cpp
class Animal {
public:
    virtual void sound() { cout << "Generic sound" << endl; }
};

class Dog : public Animal {
public:
    void sound() { cout << "Woof!" << endl; }   // Overrides Animal::sound()
};

class Cat : public Animal {
public:
    void sound() { cout << "Meow!" << endl; }   // Overrides Animal::sound()
};
```

**Which version to call is decided at RUNTIME** based on actual object type.

### Overloading vs Overriding — Comparison Table:

```
┌──────────────────┬──────────────────────┬──────────────────────┐
│    Property      │    Overloading       │     Overriding       │
├──────────────────┼──────────────────────┼──────────────────────┤
│ Same class?      │ YES                  │ NO (different class) │
│ Parameters       │ DIFFERENT            │ SAME (must match)    │
│ Return type      │ Can differ           │ Should be same       │
│ When decided?    │ Compile time         │ Runtime              │
│ Polymorphism type│ Static (Compile)     │ Dynamic (Runtime)    │
│ Inheritance req? │ Not required         │ Required             │
│ virtual needed?  │ No                   │ Yes (in base class)  │
│ Also called      │ Ad-hoc polymorphism  │ Subtype polymorphism │
└──────────────────┴──────────────────────┴──────────────────────┘
```

---

## 📌 SECTION 1.7 — VTABLE AND VPTR (Conceptual Understanding)

### How Does Runtime Polymorphism Work Internally?

```
HOW VIRTUAL FUNCTIONS ARE RESOLVED INTERNALLY:
═══════════════════════════════════════════════

When a class has virtual functions, the compiler creates:

1. VTABLE (Virtual Table):
   ┌──────────────────────────────┐
   │  Base Class VTABLE           │
   │  ┌────┬──────────────────┐   │
   │  │ [0]│ → Base::show()  │   │
   │  │ [1]│ → Base::draw()  │   │
   │  └────┴──────────────────┘   │
   └──────────────────────────────┘
   
   ┌──────────────────────────────┐
   │  Derived Class VTABLE        │
   │  ┌────┬──────────────────┐   │
   │  │ [0]│ → Derived::show()│  ← Overridden!
   │  │ [1]│ → Base::draw()  │   ← Not overridden, uses Base
   │  └────┴──────────────────┘   │
   └──────────────────────────────┘

2. VPTR (Virtual Pointer):
   Every object has a hidden VPTR that points to its class's VTABLE
   
   Base object's vptr → Base VTABLE
   Derived object's vptr → Derived VTABLE

RESULT: When you call ptr->show() via a Base pointer pointing to 
        a Derived object, the VPTR directs to Derived VTABLE → 
        Derived::show() is called. This is runtime polymorphism!
```

> **Exam note:** VTABLE = class-level (one per class). VPTR = object-level (one per object). You don't need to write code for this; just understand the concept.

---

## 📌 SECTION 1.8 — VIRTUAL DESTRUCTOR (Very Important!)

### Why is Virtual Destructor Needed?

```cpp
class Base {
public:
    Base() { cout << "Base created" << endl; }
    ~Base() { cout << "Base destroyed" << endl; }  // Not virtual!
};

class Derived : public Base {
public:
    Derived() { cout << "Derived created" << endl; }
    ~Derived() { cout << "Derived destroyed" << endl; }
};

int main() {
    Base *ptr = new Derived();  // Base pointer to Derived object
    delete ptr;                 // ← PROBLEM!
    return 0;
}
```

**Output WITHOUT virtual destructor:**
```
Base created
Derived created
Base destroyed       ← Only Base destructor called! Derived destructor SKIPPED!
                        This causes MEMORY LEAK
```

**Output WITH virtual destructor:**
```cpp
virtual ~Base() { cout << "Base destroyed" << endl; }  // Make it virtual
```
```
Base created
Derived created
Derived destroyed   ← Derived destructor called FIRST
Base destroyed      ← Then Base destructor called
```

> **🔑 RULE:** Whenever you have virtual functions in a class (i.e., you expect to use base pointer to delete derived objects), ALWAYS make the destructor virtual.

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 📐 PART 2 — GS MATHS (Afternoon: 1 hr)
# NUMBER SYSTEM BASICS
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

## 📌 SECTION 2.1 — TYPES OF NUMBERS (Foundation)

```
NUMBER TYPES HIERARCHY:
═══════════════════════

                     All Numbers
                          │
          ┌───────────────┴───────────────┐
          │                               │
       REAL                          IMAGINARY
       Numbers                       (√-1 etc.)
          │
    ┌─────┴─────┐
    │           │
RATIONAL    IRRATIONAL
  (p/q)     (√2, π, e)
    │
┌───┴───┐
│       │
INTEGER  FRACTION
   │
┌──┴──┐
│     │
NEG   NON-NEGATIVE (Whole)
       │
    ┌──┴──┐
    0    NATURAL
         (1,2,3...)
```

### Key Definitions:

| Type | Definition | Examples |
|------|-----------|---------|
| **Natural Numbers (N)** | Counting numbers starting from 1 | 1, 2, 3, 4... |
| **Whole Numbers (W)** | Natural + Zero | 0, 1, 2, 3... |
| **Integers (Z)** | Whole + Negative | ...-2, -1, 0, 1, 2... |
| **Rational (Q)** | Can be written as p/q (q≠0) | 1/2, 3, -5, 0.75 |
| **Irrational** | Cannot be written as p/q | √2, √3, π, e |
| **Real Numbers (R)** | Rational + Irrational | All of the above |
| **Prime Numbers** | Divisible only by 1 and itself | 2, 3, 5, 7, 11, 13... |
| **Composite Numbers** | More than 2 factors | 4, 6, 8, 9, 10... |
| **Co-prime numbers** | HCF = 1 (no common factor) | (8, 15), (9, 16) |

> **⚠️ EXAM TRAPS:**
> - 1 is **NEITHER prime NOR composite**
> - 2 is the **ONLY even prime number**
> - 0 is a **whole number but NOT natural number**
> - √2 = 1.41421... is **irrational** (never-ending, non-repeating)
> - 0.333... = 1/3 is **rational** (repeating decimal = rational)

---

## 📌 SECTION 2.2 — DIVISIBILITY RULES (Most Asked in Exams!)

```
┌────────────────────────────────────────────────────────────┐
│                DIVISIBILITY RULES TABLE                    │
├────────┬───────────────────────────────────────────────────┤
│ Div by │ Rule                                              │
├────────┼───────────────────────────────────────────────────┤
│   2    │ Last digit is 0, 2, 4, 6, or 8 (even)            │
│   3    │ Sum of all digits divisible by 3                  │
│   4    │ Last TWO digits divisible by 4                    │
│   5    │ Last digit is 0 or 5                              │
│   6    │ Divisible by BOTH 2 and 3                         │
│   7    │ Double last digit, subtract from rest; repeat     │
│   8    │ Last THREE digits divisible by 8                  │
│   9    │ Sum of all digits divisible by 9                  │
│  10    │ Last digit is 0                                   │
│  11    │ (Sum of odd-position digits) - (Sum of even)      │
│        │ result = 0 or divisible by 11                    │
│  12    │ Divisible by BOTH 3 and 4                         │
│  25    │ Last TWO digits divisible by 25 (or 00, 25, 50, 75)|
└────────┴───────────────────────────────────────────────────┘
```

### Quick Practice:

**Q: Is 132 divisible by 11?**
- Odd positions (1st, 3rd): 1 + 2 = 3
- Even positions (2nd): 3
- Difference: 3 - 3 = 0 → ✅ YES, divisible by 11

**Q: Is 4728 divisible by 8?**
- Last 3 digits: 728
- 728 ÷ 8 = 91 ✅ YES

**Q: Is 3456 divisible by 9?**
- Sum: 3+4+5+6 = 18
- 18 ÷ 9 = 2 ✅ YES

---

## 📌 SECTION 2.3 — HCF & LCM (Always in Exam!)

### HCF (Highest Common Factor) = GCD

**HCF = The LARGEST number that divides BOTH numbers exactly**

#### Method 1: Prime Factorization

```
Find HCF of 36 and 48:

36 = 2 × 2 × 3 × 3 = 2² × 3²
48 = 2 × 2 × 2 × 2 × 3 = 2⁴ × 3¹

HCF = Take LOWEST power of COMMON factors
    = 2² × 3¹ = 4 × 3 = 12

✅ HCF(36, 48) = 12
```

#### Method 2: Division Method (Euclid's Algorithm)

```
Find HCF(48, 36):

Step 1: 48 ÷ 36 = 1 remainder 12
Step 2: 36 ÷ 12 = 3 remainder  0
           ↑
       Remainder = 0, so HCF = 12 ✅
```

---

### LCM (Least Common Multiple)

**LCM = The SMALLEST number that is divisible by BOTH numbers**

#### Formula:

```
        Number 1 × Number 2
LCM = ─────────────────────────
            HCF
```

**OR using Prime Factorization:**
Take **HIGHEST power** of all prime factors.

```
Find LCM of 36 and 48:

36 = 2² × 3²
48 = 2⁴ × 3¹

LCM = Take HIGHEST power of ALL factors
    = 2⁴ × 3² = 16 × 9 = 144

✅ LCM(36, 48) = 144

Verify: 36 × 48 / 12 = 1728 / 12 = 144 ✅
```

---

### Key HCF-LCM Formulas for Exam:

```
┌─────────────────────────────────────────────────────────┐
│               HCF × LCM = Product of two numbers        │
│               HCF × LCM = a × b                         │
│                                                         │
│  LCM is always ≥ HCF                                    │
│  HCF always divides LCM exactly                         │
│  HCF of fractions = HCF of numerators / LCM of denoms  │
│  LCM of fractions = LCM of numerators / HCF of denoms  │
└─────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 2.4 — NUMBER SYSTEM PROBLEMS (Exam Pattern)

### Type 1: Find the Number

**Problem:** A number when divided by 3 gives remainder 1, and when divided by 5 gives remainder 3. Find the smallest such number.

**Solution using Chinese Remainder Theorem (simple approach):**
```
Numbers leaving remainder 1 when divided by 3: 1, 4, 7, 10, 13, 16, 19, 22...
Numbers leaving remainder 3 when divided by 5: 3, 8, 13, 18, 23...

Common number = 13 ✅
Answer: 13
```

### Type 2: Bell Problem (LCM Application)

**Problem:** Three bells ring at intervals of 6, 8, and 12 minutes. If they ring together at 8:00 AM, when will they next ring together?

```
LCM(6, 8, 12):
6 = 2 × 3
8 = 2³
12 = 2² × 3
LCM = 2³ × 3 = 24 minutes

They ring together again at 8:24 AM ✅
```

### Type 3: Tiles/Area Problem (HCF Application)

**Problem:** Find the largest square tile that can cover a floor of 12m × 8m without cutting.

```
HCF(12, 8):
12 = 2² × 3
8 = 2³
HCF = 2² = 4 meters

Tile size = 4m × 4m ✅
```

---

## 📌 SECTION 2.5 — IMPORTANT NUMBER PROPERTIES

### Perfect Numbers:
A number where sum of its proper divisors = the number itself.
- 6: divisors 1+2+3 = 6 ✅
- 28: divisors 1+2+4+7+14 = 28 ✅

### Armstrong Numbers (Narcissistic):
A number equal to sum of cubes of its digits.
- 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153 ✅
- 370 = 3³ + 7³ + 0³ = 27 + 343 + 0 = 370 ✅

### Palindrome Numbers:
Same forwards and backwards.
- 121, 1331, 12321

### Fibonacci Numbers:
Each number = sum of previous two.
- 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55...

---

## 📌 SECTION 2.6 — REMAINDER THEOREM TRICKS

### Power Remainders (Most Tricky — Exam Favourite!):

**Problem:** What is the remainder when 7¹⁰⁰ is divided by 6?

**Trick: Cyclicity Method**
```
7 ÷ 6 = remainder 1
7² ÷ 6 = 49 ÷ 6 = remainder 1
7³ ÷ 6 = 343 ÷ 6 = remainder 1
Pattern: 7^n ÷ 6 always gives remainder 1

Therefore 7¹⁰⁰ ÷ 6 → remainder = 1 ✅
```

**Problem:** What is the remainder when 2¹⁰ is divided by 3?

```
2¹ ÷ 3 = remainder 2
2² ÷ 3 = 4 ÷ 3 = remainder 1
2³ ÷ 3 = 8 ÷ 3 = remainder 2
2⁴ ÷ 3 = 16 ÷ 3 = remainder 1
Pattern: Even power → remainder 1; Odd power → remainder 2

2¹⁰ → even power → remainder = 1 ✅
```

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 📝 PART 3 — 25 PYQ-STYLE PRACTICE QUESTIONS
# (CS: 15 + GS Maths: 10)
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

> **Instructions:** Options follow BPSC TRE format:
> - **(A), (B), (C)** = individual options
> - **(D)** = "More than one of the above" (means multiple are correct)
> - **(E)** = "None of the above"
> Attempt all questions before checking answers!

---

## 🖥️ CS QUESTIONS (Q1–Q15)

---

**Q1.** The diamond problem in C++ occurs when:

(A) A class has more than one constructor  
(B) A derived class inherits from two base classes which both inherit from a common base  
(C) A class has both virtual and non-virtual functions  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** To resolve the diamond problem, the `virtual` keyword is placed in:

(A) Class A (the top-most base class)  
(B) Class D (the bottom-most derived class)  
(C) Classes B and C (the intermediate classes)  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** Which of the following is the CORRECT syntax for a pure virtual function in C++?

(A) `virtual void func();`  
(B) `void func() = 0;`  
(C) `virtual void func() = 0;`  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** Which of the following statements about an abstract class is/are TRUE?

(A) An abstract class must have at least one pure virtual function  
(B) You cannot create an object of an abstract class  
(C) An abstract class can have a constructor  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** Consider the code:
```cpp
class A { public: virtual void f() = 0; };
class B : public A { };
int main() { B obj; }
```
What happens when this code is compiled?

(A) Compiles successfully, no output  
(B) Runtime error when object is created  
(C) Compile error: B is still abstract (did not implement f())  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** Which of the following is/are TRUE about virtual functions?

(A) A constructor can be declared virtual  
(B) A destructor can be declared virtual  
(C) A static function can be declared virtual  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** What is the output of the following code?
```cpp
#include <iostream>
using namespace std;
class A {
public:
    virtual void show() { cout << "A" << endl; }
};
class B : public A {
public:
    void show() { cout << "B" << endl; }
};
int main() {
    A *ptr = new B();
    ptr->show();
    return 0;
}
```

(A) A  
(B) B  
(C) Compile error  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** The `override` keyword in C++11:

(A) Forces the function to override a base class function  
(B) Generates a compile error if no matching virtual function found in base class  
(C) Helps detect typos in function names during overriding  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** Method OVERLOADING differs from method OVERRIDING in that overloading:

(A) Occurs in different classes (parent-child)  
(B) Occurs in the SAME class with different parameter lists  
(C) Requires the virtual keyword  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** Which of the following is an example of RUNTIME polymorphism?

(A) Function overloading with different parameter types  
(B) A virtual function being called through a base class pointer  
(C) Operator overloading  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** Regarding VTABLE (Virtual Table), which statement is correct?

(A) Each object of a class with virtual functions has its own VTABLE  
(B) Each CLASS with virtual functions has one VTABLE; each object has a VPTR pointing to it  
(C) VTABLE is stored in the stack memory  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** Consider:
```cpp
class Base {
public:
    ~Base() { cout << "Base destructor" << endl; }
};
class Derived : public Base {
public:
    ~Derived() { cout << "Derived destructor" << endl; }
};
int main() {
    Base *ptr = new Derived();
    delete ptr;
    return 0;
}
```
What is the output?

(A) Derived destructor → Base destructor  
(B) Base destructor only  
(C) Derived destructor only  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** What is the correct syntax for virtual inheritance in C++?

(A) `class B : public virtual A { };`  
(B) `class B : virtual public A { };`  
(C) `class B : virtual A { };`  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** If class A has one pure virtual function and two normal virtual functions, then:

(A) Class A is abstract  
(B) Objects of class A cannot be created  
(C) Derived classes must implement only the pure virtual function to become concrete  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** Which statement about method overloading in C++ is FALSE?

(A) Two overloaded functions can have different return types  
(B) Two overloaded functions must have different parameter lists  
(C) Two functions that differ ONLY in return type are overloaded  
(D) More than one of the above  
(E) None of the above  

---

## 📐 GS MATHS QUESTIONS (Q16–Q25)

---

**Q16.** Which of the following is NOT a prime number?

(A) 2  
(B) 7  
(C) 91  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** The HCF of 120 and 144 is:

(A) 12  
(B) 24  
(C) 48  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** LCM × HCF = ?

(A) Sum of the two numbers  
(B) Difference of the two numbers  
(C) Product of the two numbers  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** Which number is divisible by 11?

(A) 121  
(B) 1342  
(C) 1012  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** Three bells ring at intervals of 4, 6, and 8 minutes. They first ring together at 12:00 noon. At what time will they ring together again?

(A) 12:12 PM  
(B) 12:20 PM  
(C) 12:24 PM  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** The number 1 is:

(A) A prime number  
(B) A composite number  
(C) Neither prime nor composite  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** What is the remainder when 3¹⁰⁰ is divided by 4?

(A) 0  
(B) 1  
(C) 3  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** HCF of two fractions p/q and r/s is:

(A) (HCF of p, r) / (LCM of q, s)  
(B) (LCM of p, r) / (HCF of q, s)  
(C) (HCF of p, r) × (HCF of q, s)  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** Which of the following is an Armstrong number?

(A) 153  
(B) 370  
(C) 121  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** The sum of first n natural numbers formula is:

(A) n(n+1)/2  
(B) n(n+1)(2n+1)/6  
(C) [n(n+1)/2]²  
(D) More than one of the above  
(E) None of the above  

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# ✅ DETAILED ANSWERS WITH EXPLANATIONS
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

## CS ANSWERS

**Q1. Answer: (B)**
The diamond problem specifically occurs in multiple inheritance when B and C both inherit from A, and D inherits from both B and C — creating two copies of A in D.

---

**Q2. Answer: (C)**
The `virtual` keyword must be placed in the inheritance declarations of the INTERMEDIATE classes (B and C), not in A or D. Syntax: `class B : virtual public A { };`

---

**Q3. Answer: (C)**
Pure virtual function syntax is exactly: `virtual void func() = 0;`
- Option (A) is just a virtual function (has body expected), not pure virtual.
- Option (B) is wrong — `= 0` alone without virtual doesn't make it pure virtual.

---

**Q4. Answer: (D) — More than one!**
All three (A), (B), and (C) are TRUE:
- (A) ✅ At least one pure virtual function = abstract class
- (B) ✅ Objects of abstract class CANNOT be created
- (C) ✅ Abstract class CAN have a constructor (though you can't directly instantiate it, the constructor is called when derived class object is created)

> **⚠️ This is a typical (D) answer — examiners love testing that abstract classes CAN have constructors!**

---

**Q5. Answer: (C)**
Class B inherits from A but does NOT provide implementation for `f()`. So B is still abstract. Creating `B obj` gives compile error: "cannot declare variable 'obj' to be of abstract type 'B'".

---

**Q6. Answer: (B)**
- (A) ❌ Constructor CANNOT be virtual
- (B) ✅ Destructor CAN (and often SHOULD) be virtual
- (C) ❌ Static function CANNOT be virtual (static = no object needed; virtual = needs object/vptr)
So only (B) is true — answer is (B), not (D).

---

**Q7. Answer: (B)**
Because `show()` in class A is `virtual`, the function call is resolved at RUNTIME. `ptr` points to a `B` object, so `B::show()` is called → output: `B`
This demonstrates **runtime polymorphism**.

---

**Q8. Answer: (D) — More than one!**
All three (A), (B), and (C) are TRUE about the `override` keyword:
- Forces function to be an override ✅
- Compile error if no base virtual matches ✅
- Catches typos at compile time ✅

---

**Q9. Answer: (B)**
Overloading occurs in the SAME class with different parameter lists. 
- (A) is wrong — that's overriding (different classes)
- (C) is wrong — overloading does NOT require virtual

---

**Q10. Answer: (B)**
Runtime polymorphism is achieved specifically through virtual functions called via base class pointers/references.
- (A) Function overloading = compile-time polymorphism ❌
- (C) Operator overloading = compile-time polymorphism ❌
Only (B) is correct.

---

**Q11. Answer: (B)**
Each CLASS has one VTABLE. Each OBJECT has a hidden VPTR (virtual pointer) that points to its class's VTABLE. VTABLE is stored in the **data segment** (not stack).

---

**Q12. Answer: (B)**
Since the Base destructor is NOT virtual, when `delete ptr` is called (ptr is Base type), only `Base destructor` is called. The `Derived destructor` is NEVER called → **memory leak**.
Output: `Base destructor` only.

> **Key lesson:** Always use virtual destructor when using base class pointers to delete derived objects!

---

**Q13. Answer: (D) — More than one!**
Both (A) `class B : public virtual A` and (B) `class B : virtual public A` are valid syntax! The order of `public` and `virtual` doesn't matter. So (D) is correct.

---

**Q14. Answer: (D) — More than one!**
All three are correct:
- (A) ✅ One pure virtual = abstract class
- (B) ✅ Cannot create objects
- (C) ✅ Derived class needs to implement ONLY the pure virtual function(s) to become concrete (normal virtual functions are already implemented in A)

---

**Q15. Answer: (C)**
Two functions that differ ONLY in return type are **NOT** overloaded and will give a compile error. Overloading requires different parameter lists (type, number, or order of parameters). Return type alone is insufficient.

> **Trick:** C++ cannot determine which version to call based only on return type — hence it's NOT valid overloading.

---

## GS MATHS ANSWERS

**Q16. Answer: (C)**
91 = 7 × 13 → NOT prime (has factors other than 1 and itself)
2 and 7 are both prime. So only (C) is "not prime".

---

**Q17. Answer: (B) — 24**
120 = 2³ × 3 × 5
144 = 2⁴ × 3²
HCF = 2³ × 3 = 8 × 3 = 24 ✅

---

**Q18. Answer: (C)**
This is a fundamental formula: **HCF × LCM = Product of two numbers (a × b)**

---

**Q19. Answer: (D) — More than one!**
Check divisibility by 11:
- 121: (1+1) - 2 = 0 ✅ divisible
- 1342: (1+4) - (3+2) = 5-5 = 0 ✅ divisible
- 1012: (1+1) - (0+2) = 2-2 = 0 ✅ divisible
All three are divisible by 11! Answer = (D)

> **This is a classic (D) answer that tricks candidates who stop at first correct option!**

---

**Q20. Answer: (C) — 12:24 PM**
LCM(4, 6, 8):
4 = 2², 6 = 2×3, 8 = 2³
LCM = 2³ × 3 = 24 minutes
12:00 + 24 minutes = 12:24 PM ✅

---

**Q21. Answer: (C)**
1 is **neither prime nor composite**. This is a fundamental math fact that is frequently asked.
- Prime: exactly 2 factors (1 and itself). 1 has only 1 factor.
- Composite: more than 2 factors. 1 doesn't qualify.

---

**Q22. Answer: (B) — 1**
```
3¹ ÷ 4 = remainder 3
3² ÷ 4 = 9 ÷ 4 = remainder 1
3³ ÷ 4 = 27 ÷ 4 = remainder 3
3⁴ ÷ 4 = 81 ÷ 4 = remainder 1

Pattern: ODD power → remainder 3; EVEN power → remainder 1
3¹⁰⁰ → even power → remainder = 1 ✅
```

---

**Q23. Answer: (A)**
HCF of fractions = HCF of numerators / LCM of denominators
LCM of fractions = LCM of numerators / HCF of denominators
These formulas are direct exam questions.

---

**Q24. Answer: (D) — More than one!**
Armstrong numbers: sum of cubes of digits = number
- 153: 1³+5³+3³ = 1+125+27 = 153 ✅
- 370: 3³+7³+0³ = 27+343+0 = 370 ✅
- 121: 1³+2³+1³ = 1+8+1 = 10 ≠ 121 ❌

So (A) and (B) are Armstrong numbers → Answer = (D)

---

**Q25. Answer: (D) — More than one!**
Wait — actually:
- (A) n(n+1)/2 = sum of first n natural numbers ✅
- (B) n(n+1)(2n+1)/6 = sum of SQUARES of first n natural numbers
- (C) [n(n+1)/2]² = sum of CUBES of first n natural numbers

So (A) is the answer to THIS question (sum of first n natural numbers).
BUT if question asked all formulas → (D)
As written "sum of first n natural numbers" → **Answer: (A)**

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 🌟 BONUS: TOPPER-LEVEL TRICKY QUESTIONS
# (These types have appeared in TRE 3.0 — harder difficulty)
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

**BONUS Q1.** Consider this code:
```cpp
class A { public: virtual void f() = 0; void g() { f(); } };
class B : public A { public: void f() { cout << "B::f" << endl; } };
int main() { B obj; obj.g(); }
```
What is the output?

(A) Nothing — compile error  
(B) Nothing — runtime error  
(C) `B::f`  
(D) More than one of the above  
(E) None of the above  

**Answer: (C)**
Explanation: `g()` in class A calls `f()`. When called on a `B` object, the virtual function mechanism ensures that `B::f()` is called (even though `g()` is in class A). This demonstrates that virtual function dispatch works even when called from within the base class! Output: `B::f`

---

**BONUS Q2.** Which statement about virtual inheritance is CORRECT?

(A) Only ONE constructor of the virtual base class is called, regardless of how many paths exist  
(B) The MOST DERIVED class is responsible for calling the virtual base class constructor  
(C) Virtual inheritance increases the object size slightly due to an extra pointer  
(D) More than one of the above  
(E) None of the above  

**Answer: (D)**
All of (A), (B), and (C) are true about virtual inheritance! This is classic (D) answer.

---

**BONUS Q3.** The product of two numbers is 1080. Their HCF is 12. Find their LCM.

(A) 90  
(B) 60  
(C) 120  
(D) More than one of the above  
(E) None of the above  

**Answer: (A)**
HCF × LCM = Product of numbers
12 × LCM = 1080
LCM = 1080/12 = **90** ✅

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 📒 NIGHT REVISION — 5-BULLET SUMMARY
# (Write this in your notebook before sleeping)
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

---

## CS Bullets (Write from memory):
1. **Diamond Problem** = Two parent classes inherit same grandparent → child gets two copies of grandparent
2. **Virtual Inheritance** = `virtual` keyword in INTERMEDIATE classes → ensures only ONE copy of base class
3. **Pure Virtual Function** = `virtual void f() = 0;` → makes class ABSTRACT → cannot create objects
4. **Virtual Function** = Has body in base; called at RUNTIME via base pointer → runtime polymorphism
5. **Overloading** = Same class, different params, COMPILE TIME | **Overriding** = Different classes, same params, RUNTIME

## GS Maths Bullets (Write from memory):
1. **1 is neither prime nor composite** | **2 is the only even prime**
2. **Divisibility by 9** → sum of digits divisible by 9 | **by 11** → alternating digit difference = 0 or 11
3. **HCF × LCM = Product of two numbers** (most important formula)
4. **LCM** = highest powers of all prime factors | **HCF** = lowest powers of common factors
5. **Armstrong**: 153, 370, 371, 407 (know all four for exam)

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 🔗 CONNECTION TO TOMORROW (DAY 5)
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

**Day 5 Topics:**
- CS: **Polymorphism** (both compile-time and runtime in depth) + vtable deep dive
- GS Maths: **Averages** — weighted average, mean properties

**Bridge from Day 4:** Today you learned virtual functions (which enable runtime polymorphism). Tomorrow you'll see the FULL picture of ALL types of polymorphism and how they work together. The vtable/vptr concept you learned today will make Day 5's polymorphism section very easy!

---

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# 📊 TODAY'S SCORE TRACKER
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Section | Questions | Your Score |
|---------|-----------|------------|
| CS MCQs (Q1–Q15) | 15 | ___/15 |
| GS Maths (Q16–Q25) | 10 | ___/10 |
| Bonus Questions | 3 | ___/3 |
| **TOTAL** | **28** | **___/28** |

**Topper Target:** 24+/28 (≥ 85%)

If score < 20, re-read sections where you got wrong and redo those questions tomorrow before starting Day 5.

---

*Day 4 Complete | Study Plan: BPSC TRE 4.0 | Phase 1 Week 1*
*Next: Day 5 — Polymorphism (CS) + Averages (GS)*
*"Virtual inheritance is the diamond cutter — it turns the diamond problem into a diamond victory!"* 💎
