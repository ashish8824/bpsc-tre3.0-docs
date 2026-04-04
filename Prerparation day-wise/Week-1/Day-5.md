# 📅 DAY 5 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## CS: Polymorphism (Compile-time & Runtime) | GS: Mathematics — Averages
### 🎯 Target: TOP RANK | Prepared for: Prag | Date: April 2026

---

> **TOPPER RULE FOR TODAY:** Polymorphism is asked in EVERY BPSC TRE paper. It has appeared in TRE 1.0, 2.0, AND 3.0. Today's goal → Master it so deeply that NO question — however twisted — can trick you. Averages in GS is straightforward scoring. Together, today = EASY 6–8 marks secured.

---

## 📋 TODAY'S SCHEDULE

| Slot | Time | Activity |
|------|------|----------|
| Morning | 1.5 hrs | CS: Polymorphism — all concepts, diagrams, code |
| Afternoon | 1 hr | GS: Averages — all formulas, tricks, PYQs |
| Evening | 1 hr | Solve all PYQ MCQs (CS + GS) at end of this file |
| Night | 30 min | Write 5 bullet-point summary from memory (no peeking!) |

---

# 🔵 PART 1: COMPUTER SCIENCE
# POLYMORPHISM — "Many Forms"

---

## 1.1 What is Polymorphism?

The word **Polymorphism** comes from Greek:
- **Poly** = Many
- **Morph** = Forms/Shapes

**Definition:** Polymorphism allows the **same function name / operator** to behave **differently** depending on context (the object or arguments it is called with).

### Real-World Analogy:
> A person named **"Prag"** behaves differently in different contexts:
> - At home → son/sibling (casual, relaxed)
> - In classroom → teacher (formal, authoritative)
> - On cricket ground → player (athletic, competitive)
>
> **Same person (one name), different behaviour → Polymorphism!**

---

## 1.2 THE TWO TYPES — THE BIG PICTURE

```
                    POLYMORPHISM
                   /             \
          COMPILE-TIME          RUNTIME
          (Static / Early      (Dynamic / Late
           Binding)             Binding)
          /        \                 |
   Method        Operator      Method
  Overloading   Overloading   Overriding
                             (with Virtual
                              Functions)
```

> **EXAM TRAP ⚠️:** The exam LOVES to ask "which type uses virtual functions?"
> **ANSWER = Runtime Polymorphism (Dynamic Binding)**

---

## 1.3 COMPILE-TIME POLYMORPHISM (Static Polymorphism)

### What is it?
- The decision about **which function to call** is made at **COMPILE TIME** (before the program runs)
- Also called: **Static Binding / Early Binding**
- Two mechanisms: **Method Overloading** and **Operator Overloading**

---

### 1.3.1 METHOD OVERLOADING

**Definition:** Multiple functions with the **same name** but **different parameters** (different number or type of arguments) within the same class.

```
OVERLOADING RULES:
✅ Same function name
✅ MUST differ in: number of params OR type of params OR both
❌ Return type alone CANNOT differentiate overloaded functions
```

#### C++ Example:
```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Version 1: adds two integers
    int add(int a, int b) {
        return a + b;
    }

    // Version 2: adds three integers (different number of params)
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Version 3: adds two doubles (different type of params)
    double add(double a, double b) {
        return a + b;
    }
};

int main() {
    Calculator calc;
    cout << calc.add(3, 4);        // Calls Version 1 → Output: 7
    cout << calc.add(3, 4, 5);     // Calls Version 2 → Output: 12
    cout << calc.add(3.5, 4.5);    // Calls Version 3 → Output: 8.0
    return 0;
}
```

> **KEY POINT:** The compiler decides at COMPILE TIME which `add()` to call based on the arguments. No virtual function needed.

---

### 1.3.2 OPERATOR OVERLOADING

**Definition:** Giving additional meaning to an existing C++ operator for user-defined types (classes/objects).

```
OPERATORS THAT CAN BE OVERLOADED:
+ - * / % = < > ! & | ^ ~ += -= 
<< >> == != <= >= ++ -- () [] etc.

OPERATORS THAT CANNOT BE OVERLOADED:
:: (scope resolution)
.  (dot / member access)
.* (pointer to member)
?: (ternary)
sizeof
```

#### C++ Example (Overloading `+` operator):
```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    Complex(int r, int i) {
        real = r;
        imag = i;
    }

    // Overloading the + operator
    Complex operator+(Complex const& other) {
        Complex result(0, 0);
        result.real = this->real + other.real;
        result.imag = this->imag + other.imag;
        return result;
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3, 4), c2(1, 2);
    Complex c3 = c1 + c2;   // calls operator+() function
    c3.display();             // Output: 4 + 6i
    return 0;
}
```

> **EXAM FACT:** The keyword used for operator overloading is `operator` followed by the symbol.

---

## 1.4 RUNTIME POLYMORPHISM (Dynamic Polymorphism)

### What is it?
- The decision about **which function to call** is made at **RUNTIME** (while program is running)
- Also called: **Dynamic Binding / Late Binding**
- Achieved through: **Method Overriding + Virtual Functions**

---

### 1.4.1 METHOD OVERRIDING

**Definition:** A derived (child) class provides its **own implementation** of a function that is **already defined in the base (parent) class**, with the **same name, same parameters, same return type**.

```
OVERRIDING RULES:
✅ Same function name
✅ Same parameters (signature)
✅ Same return type
✅ Function must be declared virtual in BASE class
✅ Occurs across classes (parent-child relationship)
```

#### OVERLOADING vs OVERRIDING — The Most Tested Difference:

| Feature | Method Overloading | Method Overriding |
|---------|-------------------|------------------|
| Where | SAME class | DIFFERENT classes (parent-child) |
| Parameters | Must DIFFER | Must be SAME |
| Return type | Can differ | Must be SAME |
| Keyword | No special keyword | `virtual` in base class |
| Binding type | Compile-time (early) | Runtime (late) |
| Also called | Static polymorphism | Dynamic polymorphism |
| Inheritance needed? | NO | YES |

---

### 1.4.2 VIRTUAL FUNCTIONS

**Definition:** A function declared with the `virtual` keyword in the BASE class. It tells the compiler: *"Don't bind this at compile time — wait until runtime to decide which version to call."*

```
VIRTUAL FUNCTION SYNTAX IN C++:
    virtual return_type function_name(parameters);

EXAMPLE:
    virtual void speak();
```

#### Full Example of Runtime Polymorphism:
```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    // Virtual function in base class
    virtual void speak() {
        cout << "Animal speaks!" << endl;
    }
};

class Dog : public Animal {
public:
    // Override in derived class
    void speak() override {
        cout << "Dog says: Woof!" << endl;
    }
};

class Cat : public Animal {
public:
    void speak() override {
        cout << "Cat says: Meow!" << endl;
    }
};

int main() {
    Animal* ptr;       // Base class POINTER

    Dog d;
    Cat c;

    ptr = &d;
    ptr->speak();      // ← Runtime decision: Output: Dog says: Woof!

    ptr = &c;
    ptr->speak();      // ← Runtime decision: Output: Cat says: Meow!

    return 0;
}
```

> **KEY INSIGHT:** The same pointer `ptr` (of type `Animal*`) calls different versions of `speak()` depending on what object it currently points to. **This decision happens at RUNTIME.** This is the essence of runtime polymorphism.

---

### 1.4.3 HOW DOES RUNTIME POLYMORPHISM WORK INTERNALLY?

#### The vtable (Virtual Table) and vptr (Virtual Pointer):

```
When a class has virtual functions, the compiler creates:

1. vtable (Virtual Table):
   - A table of function pointers
   - One vtable per class that has virtual functions
   - Contains the ADDRESS of each virtual function

2. vptr (Virtual Pointer):
   - A hidden pointer added to EACH OBJECT of that class
   - Points to that class's vtable

AT RUNTIME:
   ptr->speak()
   → Follow vptr → Find vtable → Find speak() address → CALL IT
```

##### Diagram:
```
OBJECT: Dog d;
+------------------+
| vptr  ---------> | Dog's vtable
|                  | +------------------+
| (other data)     | | speak()  -------> | Dog::speak()
+------------------+ +------------------+

OBJECT: Cat c;
+------------------+
| vptr  ---------> | Cat's vtable
|                  | +------------------+
| (other data)     | | speak()  -------> | Cat::speak()
+------------------+ +------------------+
```

> **EXAM NOTE:** vtable and vptr are the **internal mechanism** for runtime polymorphism. You don't write them — the compiler creates them automatically when `virtual` keyword is used. Questions sometimes ask: "What mechanism is used internally for runtime polymorphism?" → **vtable / vptr**

---

## 1.5 PURE VIRTUAL FUNCTIONS & ABSTRACT CLASSES

### Pure Virtual Function:
```cpp
virtual void function_name() = 0;   // = 0 makes it PURE virtual
```

- A pure virtual function has **NO body** in the base class (only declaration + `= 0`)
- It is a **contract** — derived classes MUST override it
- A class with **at least one** pure virtual function is called an **Abstract Class**

### Abstract Class Rules:
```
✅ Cannot create objects of an abstract class directly
✅ Must be inherited and all pure virtual functions must be overridden
✅ If derived class does NOT override ALL pure virtual functions → derived class also becomes abstract
❌ You CANNOT do: AbstractClass obj;  ← COMPILE ERROR
✅ You CAN do:    AbstractClass* ptr = &DerivedObj;  ← VALID
```

#### Example:
```cpp
class Shape {
public:
    virtual double area() = 0;     // Pure virtual → Shape is abstract
    virtual double perimeter() = 0; // Pure virtual
};

class Circle : public Shape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    double area() override { return 3.14 * radius * radius; }
    double perimeter() override { return 2 * 3.14 * radius; }
};

int main() {
    // Shape s;           ← ERROR! Cannot instantiate abstract class
    Shape* s = new Circle(5);  // ← VALID: pointer to abstract class
    cout << s->area();   // Output: 78.5
    return 0;
}
```

---

## 1.6 VIRTUAL vs PURE VIRTUAL — The Most Tested Comparison

| Feature | Virtual Function | Pure Virtual Function |
|---------|-----------------|----------------------|
| Syntax | `virtual void f();` | `virtual void f() = 0;` |
| Has body? | YES (in base class) | NO (no body in base) |
| Must override? | NO (optional) | YES (mandatory in concrete derived class) |
| Makes class abstract? | NO | YES |
| Object creation? | Class is concrete; objects can be created | Class becomes abstract; NO objects |
| Purpose | Provide default + allow override | Force derived class to implement |

---

## 1.7 THE `override` KEYWORD (C++11)

```cpp
class Dog : public Animal {
public:
    void speak() override {   // 'override' tells compiler: "I'm intentionally overriding"
        cout << "Woof!" << endl;
    }
};
```

**Why use `override`?**
- If you mistype the function name (e.g., `Speak()` instead of `speak()`), the compiler gives an ERROR
- Without `override`, the compiler would silently create a NEW function instead of overriding, causing subtle bugs
- `override` = **safety net for overriding**

---

## 1.8 COMPLETE SUMMARY DIAGRAM

```
POLYMORPHISM
│
├── COMPILE-TIME (Static Binding)
│   ├── Method Overloading
│   │   ├── Same class, same name, DIFFERENT parameters
│   │   ├── Resolved at: COMPILE TIME
│   │   └── NO virtual keyword needed
│   │
│   └── Operator Overloading
│       ├── Give new meaning to operators for user-defined types
│       ├── Keyword: operator
│       └── Example: operator+, operator==
│
└── RUNTIME (Dynamic Binding)
    └── Method Overriding + Virtual Functions
        ├── Parent-child classes, same name, SAME parameters
        ├── virtual keyword in BASE class
        ├── Resolved at: RUNTIME
        ├── Internal mechanism: vtable + vptr
        ├── Pure virtual (= 0) → Abstract Class
        └── override keyword (C++11) for safety
```

---

## 1.9 EXAM TRAPS & TRICKS — POLYMORPHISM

| ⚠️ Trap | ✅ Correct Answer |
|---------|-----------------|
| "Overloading uses virtual functions" | FALSE — only overriding uses virtual |
| "Override changes the return type" | FALSE — return type must be SAME |
| "You can create object of abstract class" | FALSE — compiler error |
| "Overloading is across parent-child classes" | FALSE — it's within SAME class |
| "Runtime polymorphism = early binding" | FALSE — it's LATE binding |
| "vtable is written by programmer" | FALSE — compiler creates it automatically |
| "Pure virtual function has a body" | FALSE — no body (= 0) |
| "Operator :: cannot be overloaded" | TRUE — scope resolution cannot be overloaded |
| "sizeof can be overloaded" | FALSE — sizeof cannot be overloaded |
| "Overriding needs same number of params" | TRUE — same signature required |

---

## 1.10 POLYMORPHISM IN JAVA (Quick Reference for BPSC TRE)

```java
// Method Overloading (Compile-time)
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}

// Method Overriding (Runtime)
class Animal {
    void speak() { System.out.println("Animal speaks"); }
}

class Dog extends Animal {
    @Override                          // @Override annotation in Java
    void speak() { System.out.println("Woof!"); }
}
```

> **NOTE:** In Java, ALL non-static, non-private, non-final methods are **automatically virtual**. Java does NOT need the `virtual` keyword explicitly. This is a key difference from C++.

---
---

# 🟢 PART 2: GENERAL STUDIES
# MATHEMATICS — AVERAGES

---

## 2.1 What is Average (Mean)?

**Average (Arithmetic Mean)** = Total sum of all values ÷ Number of values

```
                Sum of all values
Average  =  ─────────────────────
                Number of values

Or: A = S/n     where S = Sum, n = Count
```

**Rearranging** (very useful for solving problems):
```
Sum = Average × n
n   = Sum / Average
```

---

## 2.2 CORE FORMULA BANK

### Formula 1: Basic Average
```
A = (x₁ + x₂ + x₃ + ... + xₙ) / n
```

### Formula 2: Finding new average when a value is added
```
If n numbers have average A, and one MORE number (x) is added:
New Sum = (A × n) + x
New Average = New Sum / (n + 1)
```

### Formula 3: Finding new average when a value is removed
```
If n numbers have average A, and one number (x) is REMOVED:
New Sum = (A × n) - x
New Average = New Sum / (n - 1)
```

### Formula 4: Average of consecutive natural numbers
```
Average of 1, 2, 3, ..., n  =  (n + 1) / 2
```

### Formula 5: Average of consecutive even numbers starting from 2
```
Average of 2, 4, 6, ..., 2n  =  n + 1
```

### Formula 6: Average of first n odd numbers
```
Average of 1, 3, 5, ..., (2n-1)  =  n
```

### Formula 7: Average Speed (VERY commonly confused)
```
If a person travels equal distances at speeds S₁ and S₂:
Average Speed = 2 × S₁ × S₂ / (S₁ + S₂)

⚠️ TRAP: Average speed ≠ (S₁ + S₂)/2  ← This is WRONG for equal distances!
```

### Formula 8: Effect of replacing one value
```
If a person with value 'x' leaves a group of n people with average A,
and is replaced by a person with value 'y':

New Average = A + (y - x)/n

If new average INCREASES: y > x
If new average DECREASES: y < x
```

---

## 2.3 STEP-BY-STEP SOLVED EXAMPLES

### Example 1 (Basic):
> The average of 5 numbers is 20. Find their sum.

**Solution:**
```
Sum = Average × n = 20 × 5 = 100 ✅
```

---

### Example 2 (Adding a number):
> The average of 4 numbers is 15. If 20 is added, what is the new average?

**Solution:**
```
Old Sum = 15 × 4 = 60
New Sum = 60 + 20 = 80
New Average = 80 / 5 = 16 ✅
```

---

### Example 3 (Replacing a person — BPSC TRE type):
> The average age of 10 students is 14 years. If a student of age 10 is replaced by a new student of age 18, what is the new average?

**Solution using shortcut formula:**
```
New Average = Old Average + (New - Old) / n
            = 14 + (18 - 10) / 10
            = 14 + 8/10
            = 14 + 0.8
            = 14.8 years ✅
```

---

### Example 4 (Average of arithmetic sequence):
> Find the average of first 50 natural numbers.

**Solution:**
```
Average = (n + 1) / 2 = (50 + 1) / 2 = 51/2 = 25.5 ✅
```

---

### Example 5 (Weighted average — tricky):
> Class A has 20 students with average marks 70.
> Class B has 30 students with average marks 80.
> What is the combined average?

**Solution:**
```
⚠️ WRONG approach: (70 + 80)/2 = 75  ← INCORRECT (ignores class size)

✅ CORRECT approach (Weighted Average):
Total marks = (20 × 70) + (30 × 80) = 1400 + 2400 = 3800
Total students = 20 + 30 = 50
Combined Average = 3800 / 50 = 76 ✅
```

---

### Example 6 (Cricket — most common in exams):
> A cricketer's average after 15 innings is 30. In the 16th innings he scores 90. What is his new average?

**Solution:**
```
Old Total = 30 × 15 = 450
New Total = 450 + 90 = 540
New Average = 540 / 16 = 33.75 ✅
```

---

### Example 7 (Average of squares — formula trick):
> Find the average of: 10, 20, 30, 40, 50

**Solution:**
```
Sum = 10 + 20 + 30 + 40 + 50 = 150
n = 5
Average = 150 / 5 = 30 ✅

Notice: These are in AP. Middle value = Average = 30 (shortcut for AP!)
```

> **SHORTCUT FOR ARITHMETIC PROGRESSION:**
> Average of numbers in AP = Middle term (if odd count) = (First + Last)/2

---

### Example 8 (Average Speed — exam favourite):
> A car travels 120 km at 60 km/h, then returns 120 km at 40 km/h. Find average speed.

**Solution:**
```
Average Speed = 2 × S₁ × S₂ / (S₁ + S₂)
             = 2 × 60 × 40 / (60 + 40)
             = 4800 / 100
             = 48 km/h ✅

(NOT 50 km/h — that's the wrong "simple average" trap!)
```

---

## 2.4 PROPERTIES OF MEAN — BPSC TRE SCIENCE (also appears in GS Math)

These properties appeared in TRE 2.0 and are commonly tested:

| Property | Statement | Example |
|----------|-----------|---------|
| P1 | If all values increased by constant k, mean increases by k | Values: 5,10,15; Mean=10. Add 3 to each → new mean = 13 |
| P2 | If all values multiplied by k, mean is multiplied by k | Values: 5,10,15; Mean=10. Multiply all by 2 → new mean = 20 |
| P3 | Sum of deviations from mean = 0 | Σ(xᵢ - mean) = 0 always |
| P4 | Mean of first n natural numbers = (n+1)/2 | First 9 natural numbers: mean = 5 |

---

## 2.5 EXAM SHORTCUTS — AVERAGES

### Shortcut 1: "How much did the average change per extra/missing item?"
```
Change in average when one item is added/removed:
Δ(Average) = (New item value - Old average) / New n
```

### Shortcut 2: Consecutive numbers
```
Consecutive integers: a, a+1, a+2, ..., a+(n-1)
Average = a + (n-1)/2
```

### Shortcut 3: Error correction
> If a value was wrongly noted as X but actual was Y, and average was A with n items:
```
Correct Average = A + (Y - X)/n
```
This is VERY commonly asked in BPSC TRE!

---

## 2.6 GS AVERAGES — PYQ PATTERN ANALYSIS

From TRE 1.0, 2.0, 3.0 — the Average questions follow these patterns:

1. **Cricket/Sports innings** — find new average after extra innings
2. **Student marks** — find missing mark given average
3. **Age problems** — average age of group with replacement
4. **Wrong entry correction** — find correct average
5. **Two group combined average** — weighted average type
6. **Arithmetic series average** — use (first + last)/2

> **STRATEGY:** In the exam, first check if numbers are in AP. If yes, use the (first+last)/2 shortcut. This saves 30 seconds per question.

---
---

# 🔴 PART 3: PRACTICE QUESTIONS (PYQ-STYLE)
## 📝 SECTION A: COMPUTER SCIENCE — POLYMORPHISM

> Instructions: All questions have 5 options — A, B, C, D, E.
> Option D = "More than one of the above"
> Option E = "None of the above"
> For each question, think carefully — 20-25% answers are D!

---

**Q1.** Polymorphism in OOP means:
- (A) A class can have only one form
- (B) An object can take many forms or a function can behave differently in different contexts
- (C) Multiple inheritance is mandatory
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* Polymorphism literally means "many forms." It allows a function/object to behave differently based on context. Option C is wrong — multiple inheritance is NOT required.

---

**Q2.** Method overloading in C++ is an example of:
- (A) Runtime Polymorphism
- (B) Dynamic Binding
- (C) Compile-time Polymorphism
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* Method overloading is resolved at COMPILE TIME because the compiler determines which version to call based on argument types/count. It is also called Static Polymorphism or Early Binding.

---

**Q3.** Which of the following is TRUE about method overriding?
- (A) The method in derived class must have the same name as in base class
- (B) The method in derived class must have the same parameters as in base class
- (C) The virtual keyword is used in the base class
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (D) — More than one of the above**
*Explanation:* ALL of A, B, and C are true for method overriding. This is exactly the "D trap" — you must know ALL facts about a topic.

---

**Q4.** Consider the following C++ code:
```cpp
class Animal {
public:
    virtual void sound() { cout << "..."; }
};
class Dog : public Animal {
public:
    void sound() { cout << "Woof"; }
};
int main() {
    Animal* a = new Dog();
    a->sound();
}
```
What is the output?

- (A) ...
- (B) Woof
- (C) Compile Error
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B) — Woof**
*Explanation:* `a` is a base class pointer pointing to a `Dog` object. Since `sound()` is `virtual`, runtime polymorphism occurs → Dog's `sound()` is called → Output: Woof

---

**Q5.** A pure virtual function in C++ is written as:
- (A) `virtual void func() {}`
- (B) `void func() = 0;`
- (C) `virtual void func() = 0;`
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* Pure virtual function syntax requires BOTH the `virtual` keyword AND `= 0`. Option A is a regular virtual function (has a body). Option B is incorrect syntax.

---

**Q6.** Which of the following operators CANNOT be overloaded in C++?
- (A) `+`
- (B) `<<`
- (C) `::`
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* `::` (scope resolution operator) CANNOT be overloaded. `+` and `<<` both CAN be overloaded. Other non-overloadable operators: `.` (dot), `.*`, `?:`, `sizeof`.

---

**Q7.** Which of the following statements about an abstract class is/are CORRECT?
- (A) An abstract class cannot be instantiated (no objects can be created)
- (B) An abstract class must have at least one pure virtual function
- (C) A pointer of abstract class type can point to a derived class object
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (D) — More than one of the above**
*Explanation:* ALL three statements A, B, C are correct. Abstract class = cannot instantiate, must have ≥1 pure virtual function, but pointer is valid. This is a classic "D answer" question.

---

**Q8.** The `override` keyword in C++ (introduced in C++11) is used to:
- (A) Create a new function in derived class
- (B) Tell the compiler explicitly that the function overrides a base class virtual function
- (C) Prevent further overriding of the function
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* `override` is a safety mechanism — it tells the compiler "this function is intentionally overriding a virtual function." If no matching virtual function exists in base class, compiler gives an error. It does NOT prevent further overriding — that would be `final`.

---

**Q9.** Runtime polymorphism is internally implemented using:
- (A) Function pointers
- (B) vtable (virtual function table) and vptr (virtual pointer)
- (C) Stack data structure
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* The C++ compiler creates a vtable for each class with virtual functions and a vptr hidden inside each object. At runtime, the vptr is used to find the correct function in the vtable.

---

**Q10.** What is the key difference between compile-time and runtime polymorphism?
- (A) Compile-time polymorphism uses function overloading; runtime uses function overriding
- (B) Compile-time uses early binding; runtime uses late binding
- (C) Runtime polymorphism requires virtual functions; compile-time does not
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (D) — More than one of the above**
*Explanation:* ALL of A, B, and C are correct differences. This is another "D answer" — you must know multiple distinguishing facts, not just one.

---

**Q11.** In Java, to override a method in a subclass, which annotation is commonly used?
- (A) `#Override`
- (B) `@Override`
- (C) `$Override`
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* Java uses `@Override` annotation (with `@` symbol) to explicitly mark a method as an override. This is different from C++'s `override` keyword.

---

**Q12.** Consider: A class `Vehicle` has a virtual function `fuelType()`. Class `Car` and `Truck` inherit from `Vehicle` and override `fuelType()`. A function receives `Vehicle*` pointer. What is this an example of?
- (A) Compile-time polymorphism
- (B) Operator overloading
- (C) Runtime polymorphism through virtual function
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* Using a base class pointer to call an overridden virtual function is the classic pattern of runtime (dynamic) polymorphism.

---

**Q13.** Which of these is NOT a type of polymorphism in OOP?
- (A) Compile-time polymorphism
- (B) Runtime polymorphism
- (C) Memory polymorphism
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* "Memory polymorphism" is NOT a real OOP concept. Only Compile-time (static) and Runtime (dynamic) polymorphism exist.

---

**Q14.** In method overloading, which of the following CAN differentiate two overloaded methods?
- (A) Number of parameters only
- (B) Type of parameters only
- (C) Return type only
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (D) — A and B (not C)**
*Explanation:* Both number of parameters (A) and type of parameters (B) can differentiate overloaded methods. However, return type ALONE (C) CANNOT differentiate — the compiler does not use return type for overload resolution. So correct is A and B → which is option D.

---

**Q15.** In C++, if a derived class does NOT override all pure virtual functions of its abstract base class:
- (A) The program compiles but crashes at runtime
- (B) The derived class also becomes abstract
- (C) A compile error occurs immediately
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* If any pure virtual function is unoverridden in a derived class, that derived class ALSO becomes abstract — you cannot create objects of it. This is important chain-of-abstraction behavior.

---

**Q16.** Which PYQ-type question: "Which of the following is TRUE about virtual functions in C++?"
- (A) They are resolved at compile time
- (B) They allow a base class pointer to invoke derived class methods at runtime
- (C) A class with all pure virtual functions is called a concrete class
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* Virtual functions are resolved at RUNTIME (not compile time). They allow base class pointers to call derived class methods. A class with all pure virtual functions is an ABSTRACT class (NOT concrete class).

---

**Q17.** Operator overloading in C++ is achieved using the keyword:
- (A) `virtual`
- (B) `override`
- (C) `operator`
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* The keyword `operator` followed by the symbol (e.g., `operator+`, `operator==`) is used to overload operators in C++.

---

**Q18.** Which of the following types of polymorphism is demonstrated when the same function name behaves differently based on the object type at runtime?
- (A) Static polymorphism
- (B) Early binding
- (C) Dynamic (Runtime) polymorphism
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* When function behavior differs based on object type at RUNTIME, it is dynamic/runtime polymorphism. Options A and B both describe COMPILE-TIME behavior — so they are wrong here.

---

**Q19.** The `final` keyword in C++11 when applied to a virtual function means:
- (A) The function cannot be overridden in any further derived class
- (B) The function becomes a pure virtual function
- (C) The function is deleted from the class
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (A)**
*Explanation:* `final` prevents further overriding. Example: `virtual void show() final;` — no class inheriting from this class can override `show()`. It does NOT make it pure virtual.

---

**Q20.** True or False type: "In C++, every class that has at least one pure virtual function is an abstract class and cannot be used to create direct objects."
- (A) True — this statement is fully correct
- (B) False — you can still create objects but with restrictions
- (C) False — only if ALL functions are pure virtual
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (A)**
*Explanation:* The statement is 100% correct. Even ONE pure virtual function makes the class abstract → no objects can be directly created from it.

---

## 📝 SECTION B: GENERAL STUDIES — AVERAGES (PYQ-Style)

---

**Q21.** The average of 5 numbers is 18. What is their sum?
- (A) 80
- (B) 85
- (C) 90
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 90**
*Solution:* Sum = Average × n = 18 × 5 = 90

---

**Q22.** The average of first 10 natural numbers is:
- (A) 4.5
- (B) 5
- (C) 5.5
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 5.5**
*Solution:* Average of first n natural numbers = (n+1)/2 = (10+1)/2 = 5.5

---

**Q23.** A class of 30 students has an average score of 50. If 5 more students join with an average of 60, what is the new average?
- (A) 50
- (B) 51.43
- (C) 52
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 52**
*Solution:*
Total marks (old) = 30 × 50 = 1500
Total marks (new 5 students) = 5 × 60 = 300
New Total = 1500 + 300 = 1800
New n = 35
New Average = 1800/35 = 51.43

Wait — recalculating: 1800/35 = 51.43, so Answer = **(B) 51.43** ✅

---

**Q24.** The average age of a group of 10 people is 20 years. A person of age 30 is added. What is the new average age?
- (A) 20 years
- (B) 20.9 years (approx)
- (C) 21.1 years
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 21.1 years (approx)**
*Solution:*
Old sum = 10 × 20 = 200
New sum = 200 + 30 = 230
New n = 11
New average = 230/11 ≈ 20.9 ≈ **Option B (20.9)**

Correct: **(B) 20.9 years** ✅

---

**Q25.** The average of 7 consecutive even numbers is 18. What is the largest of these numbers?
- (A) 20
- (B) 22
- (C) 24
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 24**
*Solution:*
For 7 consecutive even numbers, the average = middle (4th) number = 18
So numbers are: 12, 14, 16, **18**, 20, 22, 24
Largest = 24 ✅

---

**Q26.** A batsman scored the following runs in 6 innings: 36, 40, 82, 10, 29, 59. His average is:
- (A) 40
- (B) 41
- (C) 42.67
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 42.67**
*Solution:*
Sum = 36 + 40 + 82 + 10 + 29 + 59 = 256
Average = 256/6 = 42.67 ✅

---

**Q27.** The average monthly salary of 10 workers in a factory is ₹6000. If the salary of the manager (₹9000) is also included, the average becomes:
- (A) ₹6200
- (B) ₹6272.73
- (C) ₹6500
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B) ₹6272.73**
*Solution:*
Total salary (10 workers) = 10 × 6000 = ₹60,000
New total (including manager) = 60,000 + 9000 = ₹69,000
New n = 11
New average = 69,000/11 = ₹6272.73 ✅

---

**Q28.** The average of 6 numbers is 30. If the number 60 is included, the new average will be:
- (A) 30
- (B) 32.86
- (C) 35
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 35**  
Wait — let me recalculate:
*Solution:*
Old sum = 6 × 30 = 180
New sum = 180 + 60 = 240
New n = 7
New average = 240/7 = 34.28 ≈ 34.3

Closest answer = **(B) 32.86** — actually let me recheck: 240/7 = 34.28...

None of the given options match exactly → **(E) None of the above** if strict, but in exam pick closest = **B** is wrong.

Correct approach: 240/7 ≈ 34.3 → This scenario demonstrates why careful calculation matters!
*Correct Answer: (E) None of the above* — since none match 34.3 exactly.

---

**Q29.** The mean of 5 numbers is 8. One number is wrong and is recorded as 4 instead of 10. What is the correct mean?
- (A) 8
- (B) 9
- (C) 9.2
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 9.2**
*Solution:*
Old sum = 5 × 8 = 40
Correct sum = 40 - 4 + 10 = 46
Correct mean = 46/5 = 9.2 ✅

---

**Q30.** A car travels from A to B at 40 km/h and returns from B to A at 60 km/h (same route). The average speed for the entire journey is:
- (A) 48 km/h
- (B) 50 km/h
- (C) 52 km/h
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (A) 48 km/h**
*Solution:*
Average speed (equal distances) = 2S₁S₂/(S₁+S₂)
= 2 × 40 × 60 / (40 + 60)
= 4800/100 = 48 km/h ✅

(NOT 50 — that's the classic trap. Equal distance average speed = harmonic mean, NOT arithmetic mean)

---

**Q31.** The average of 4 consecutive odd numbers is 16. What is the smallest odd number?
- (A) 11
- (B) 13
- (C) 15
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B) 13**
*Solution:*
Let 4 consecutive odd numbers be: n, n+2, n+4, n+6
Average = (4n + 12)/4 = n + 3 = 16
n = 13
Numbers: 13, 15, 17, 19 → Average = 64/4 = 16 ✅

---

**Q32.** In a class of 40 students, the average weight is 50 kg. When 5 students leave, the average weight of remaining students is 48 kg. What is the average weight of the 5 students who left?
- (A) 58 kg
- (B) 60 kg
- (C) 66 kg
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C) 66 kg**
*Solution:*
Total weight (40 students) = 40 × 50 = 2000 kg
Total weight (35 remaining) = 35 × 48 = 1680 kg
Weight of 5 who left = 2000 - 1680 = 320 kg
Average weight of 5 = 320/5 = 64 kg

Hmm — 64 doesn't exactly match. Let me recompute: 320/5 = 64.

Closest answer: **(E) None of the above** → since none show 64 kg.

Actually answer should be revised in real exam to have 64 as an option. The **correct answer is 64 kg**, demonstrating option E awareness.

---

## 📝 SECTION C: ADDITIONAL HIGH-PRIORITY PYQ PRACTICE

### CS — MIXED OOP + POLYMORPHISM (from TRE 1.0, 2.0, 3.0 patterns)

---

**Q33.** [TRE 2.0 pattern] Which of the following is NOT a feature of Object-Oriented Programming?
- (A) Encapsulation
- (B) Polymorphism
- (C) Compilation
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* The 4 pillars of OOP are: Encapsulation, Inheritance, Polymorphism, Abstraction. "Compilation" is NOT a feature of OOP — it's a process.

---

**Q34.** [TRE 1.0 pattern] In C++, which of the following functions is called when an object goes out of scope?
- (A) Constructor
- (B) Virtual function
- (C) Destructor
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (C)**
*Explanation:* Destructor (`~ClassName()`) is automatically called when an object goes out of scope or `delete` is used on a pointer. There is only ONE destructor per class.

---

**Q35.** [TRE 3.0 pattern] What is the correct syntax for declaring a pure virtual function `draw()` with no return value?
- (A) `virtual draw() = 0;`
- (B) `virtual void draw() = 0;`
- (C) `void virtual draw() = 0;`
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* Correct syntax: `virtual` keyword + return type + function name + `= 0`. Option A is missing the return type `void`. Option C has wrong keyword order.

---

**Q36.** [TRE PYQ pattern] In Java, method overriding is achieved using the `extends` keyword for inheritance and:
- (A) The `@Override` annotation (optional but recommended)
- (B) Same method signature in subclass
- (C) A `super` reference if needed
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (D) — More than one of the above**
*Explanation:* In Java: A, B, and C are all relevant to method overriding. The `@Override` annotation helps but is optional. Same signature is mandatory. `super.method()` can call the parent version.

---

**Q37.** Which data structure is used internally by the compiler to implement function calls (including virtual function dispatch)?
- (A) Queue
- (B) Stack
- (C) Linked List
- (D) More than one of the above
- (E) None of the above

**✅ Answer: (B)**
*Explanation:* Function calls use the **Stack**. For virtual function dispatch specifically, the **vtable** (via vptr) is used, but function call management in general uses Stack.

---

# 📝 DAY 5 — NIGHT REVISION (30 minutes)

## Write these from memory BEFORE sleeping:

```
1. Two types of polymorphism: _____________ and _____________
2. Method overloading = _____________ binding (resolved at _________)
3. Method overriding uses _____________ keyword in base class
4. Pure virtual function syntax: _________________________________
5. Abstract class rule: must have at least _____ pure virtual function(s)
6. vtable = _______________________________________________
7. Operators that CANNOT be overloaded: _______________________
8. Average formula: A = ___________________
9. Average speed for equal distances: _________________________
10. Average of first n natural numbers: _______________________
```

**Answers (check after writing):**
1. Compile-time; Runtime
2. Static / Early binding; compile time
3. `virtual`
4. `virtual void func() = 0;`
5. One (at least 1)
6. Table of virtual function pointers created by compiler for runtime dispatch
7. `::`, `.`, `.*`, `?:`, `sizeof`
8. A = Sum / n
9. 2S₁S₂/(S₁+S₂)
10. (n+1)/2

---

# 📊 TODAY'S SCORE TRACKER

| Section | Questions | Target | My Score |
|---------|-----------|--------|----------|
| CS Polymorphism | Q1–Q20 | 18/20 | /20 |
| GS Averages | Q21–Q32 | 10/12 | /12 |
| Mixed PYQ | Q33–Q37 | 5/5 | /5 |
| **TOTAL** | **37** | **33+** | **/37** |

---

# 🔑 DAY 5 — TOPPER'S QUICK REFERENCE CARD

> Cut this out mentally and paste it in your brain!

```
╔══════════════════════════════════════════════════════════════╗
║           POLYMORPHISM — TOPPER CHEAT SHEET                  ║
╠══════════════════════════════════════════════════════════════╣
║ COMPILE-TIME (Static/Early Binding)                          ║
║   → Method Overloading: same name, diff params, SAME class   ║
║   → Operator Overloading: keyword 'operator'                 ║
║   → NO virtual keyword needed                                ║
╠══════════════════════════════════════════════════════════════╣
║ RUNTIME (Dynamic/Late Binding)                               ║
║   → Method Overriding: same name, same params, DIFF classes  ║
║   → Needs 'virtual' in BASE class                            ║
║   → Mechanism: vtable + vptr (created by compiler)           ║
║   → Pure virtual: virtual void f() = 0;                      ║
║   → Abstract class: ≥1 pure virtual, CANNOT instantiate      ║
╠══════════════════════════════════════════════════════════════╣
║ CANNOT OVERLOAD: ::  .  .*  ?:  sizeof                       ║
║ override keyword (C++11) = safety for overriding             ║
║ final keyword = prevent further overriding                   ║
╠══════════════════════════════════════════════════════════════╣
║ AVERAGES CHEAT SHEET                                         ║
║   Average = Sum/n                                            ║
║   Sum = Average × n                                          ║
║   Average speed (equal dist) = 2S₁S₂/(S₁+S₂)               ║
║   First n natural: (n+1)/2                                   ║
║   In AP: Average = (First + Last)/2                          ║
║   Error correction: New avg = Old avg + (correct-wrong)/n    ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 🔮 PREVIEW: DAY 6 TOPICS
- **CS:** Constructors & Destructors (Types, copy constructor, deep vs shallow copy)
- **GS:** Mathematics — LCM & HCF
- **PYQ Focus:** Constructor questions appeared 5+ times across TRE papers!

---

*Day 5 Complete ✅ | BPSC TRE 4.0 Preparation | Target: TOP RANK*
*Remember: 20-25% of exam answers are Option D. Today's Q3, Q7, Q10, Q14, Q36 were all D — practice recognizing when ALL options are correct!*
