# 📅 BPSC TRE 4.0 — DAY 3 COMPLETE STUDY MATERIAL
## CS: Inheritance (Part 1) — Concepts, Types & Syntax | GS: Ratio & Proportion (Maths)
### 🎯 Target: TOP RANK | Prepared from PYQ Analysis of TRE 1.0, 2.0, 3.0

---

> **Today's Goal:** Master Inheritance so deeply that ANY question from TRE 4.0 on this topic becomes a guaranteed correct answer. Inheritance appeared in ALL 3 previous papers (TRE 1.0, 2.0, 3.0). It is a TOP-2 ranked topic by PYQ frequency.

---

## ⏰ TIME-BLOCKED SCHEDULE FOR TODAY

| Time Slot | Duration | Activity |
|-----------|----------|----------|
| Morning Session | 1.5 hrs | CS: Inheritance — Full Concept Study (this document) |
| Afternoon Session | 1 hr | GS: Ratio & Proportion (this document) |
| Evening Session | 1 hr | Solve all 20 PYQ-style MCQs at end of this file |
| Night Session | 30 min | Write 5 bullet summary in your notebook |

---

---

# 🖥️ PART 1: COMPUTER SCIENCE
# INHERITANCE — The Complete Masterclass

---

## 🔑 SECTION 1.1 — WHAT IS INHERITANCE?

### Definition (Exam-Ready)
> **Inheritance** is the OOP mechanism by which one class (called the **derived class** or **child class**) acquires the **properties and behaviours** (fields and methods) of another class (called the **base class** or **parent class**).

### The Golden Rule — IS-A Relationship
Inheritance always models an **IS-A** relationship.

| Correct Use of Inheritance | Wrong Use of Inheritance |
|---------------------------|--------------------------|
| Dog IS-A Animal ✅ | Car HAS-A Engine ❌ (use composition instead) |
| Teacher IS-A Person ✅ | Student HAS-A Book ❌ |
| SavingsAccount IS-A BankAccount ✅ | Library HAS-A Book ❌ |

> 📌 **PYQ Trap:** BPSC TRE has asked "Which relationship does inheritance implement?" → Answer: **IS-A relationship** (not HAS-A, which is composition)

### Why Do We Use Inheritance?
1. **Code Reusability** — Write once in parent, use in all children
2. **Method Overriding** — Child can redefine parent behaviour
3. **Extensibility** — Add new features without touching existing code
4. **Polymorphism** — Required for runtime polymorphism (Day 5 topic)

---

## 🔑 SECTION 1.2 — C++ SYNTAX OF INHERITANCE (Most PYQ-Tested)

```cpp
class Base {
    // parent class
};

class Derived : access_specifier Base {
    // child class
};
```

### The Three Access Modes in Inheritance

| Syntax | Access Mode | Effect on inherited members |
|--------|-------------|----------------------------|
| `class D : public B` | Public Inheritance | public→public, protected→protected, private→inaccessible |
| `class D : protected B` | Protected Inheritance | public→protected, protected→protected, private→inaccessible |
| `class D : private B` | Private Inheritance | public→private, protected→private, private→inaccessible |

> 📌 **Default access** in C++ inheritance: **private** (if no access specifier written)
> 📌 In **Java** there is NO access specifier in inheritance — it uses `extends` keyword

### C++ vs Java Syntax Comparison (DIRECT PYQ TOPIC)

```cpp
// C++ Syntax — Uses COLON (:)
class Animal {
public:
    void eat() { cout << "Eating"; }
};

class Dog : public Animal {    // ← COLON, then access specifier
public:
    void bark() { cout << "Barking"; }
};
```

```java
// Java Syntax — Uses EXTENDS keyword
class Animal {
    void eat() { System.out.println("Eating"); }
}

class Dog extends Animal {    // ← extends keyword, NO access specifier
    void bark() { System.out.println("Barking"); }
}
```

> ⚠️ **Critical PYQ Fact:**
> - C++ uses **colon (`:`)** with an access specifier
> - Java uses **`extends`** keyword (NO access specifier, always public inheritance)
> - Java does NOT support multiple inheritance of classes (only through interfaces)
> - C++ DOES support multiple inheritance of classes

---

## 🔑 SECTION 1.3 — WHAT IS INHERITED? WHAT IS NOT?

### ✅ What IS Inherited (Child gets these from Parent):
- Public member functions
- Protected member functions
- Public data members
- Protected data members
- Nested class definitions

### ❌ What is NOT Inherited (Child does NOT get these):
| What is NOT Inherited | Reason |
|-----------------------|--------|
| **Constructors** | Each class must define its own constructor |
| **Destructor** | Each class has its own destructor |
| **Private members** | Private = only accessible within the same class |
| **Friend functions** | Friendship is not inherited |
| **Operator= (assignment operator)** | Must be explicitly defined in derived class |
| **Static members** | Not inherited but accessible via class name |

> 📌 **PYQ Fact:** "Which of the following is NOT inherited by a derived class?" → **Constructors and Destructors** are the most commonly tested answer.

### Practical Example:
```cpp
class Person {
private:
    int age;          // NOT inherited (private)
protected:
    string name;      // Inherited (protected)
public:
    void greet() { }  // Inherited (public)
    Person() { }      // Constructor — NOT inherited
    ~Person() { }     // Destructor — NOT inherited
};

class Student : public Person {
public:
    // Can access name (protected) ✅
    // Cannot access age (private) ❌
    // greet() is available ✅
    // Person() constructor is NOT inherited ❌
    
    Student() {
        name = "Raj";    // OK — protected member
        // age = 18;     // ERROR — private member of Person
    }
};
```

---

## 🔑 SECTION 1.4 — THE 5 TYPES OF INHERITANCE (With Diagrams)

### TYPE 1: SINGLE INHERITANCE
> One parent → One child

```
    Animal
       |
      Dog
```

```cpp
class Animal { };
class Dog : public Animal { };  // Single Inheritance
```

**Key Point:** Simplest form. No ambiguity issues. Most common in real programs.

---

### TYPE 2: MULTIPLE INHERITANCE (C++ only, NOT in Java)
> One child → Multiple parents

```
  Animal    Pet
     \      /
       Dog
```

```cpp
class Animal { public: void breathe(); };
class Pet    { public: void playWithOwner(); };
class Dog : public Animal, public Pet { };  // Multiple Inheritance
```

**Key Point:**
- **C++ supports** multiple inheritance
- **Java does NOT support** multiple inheritance of classes
- Java achieves it through **interfaces** using `implements`
- Multiple inheritance can create the **Diamond Problem** (covered in Day 4)

---

### TYPE 3: MULTILEVEL INHERITANCE
> A → B → C (chain)

```
  Grandparent
       |
     Parent
       |
     Child
```

```cpp
class Grandparent { public: void cook(); };
class Parent : public Grandparent { public: void drive(); };
class Child : public Parent { public: void study(); };
// Child has: cook() + drive() + study()
```

**Key Point:** Child can access all public/protected members going all the way up the chain.

**Memory Trick:** Think of it as **generations**: Grandfather → Father → Son

---

### TYPE 4: HIERARCHICAL INHERITANCE
> One parent → Multiple children

```
     Animal
    /   |   \
  Dog  Cat  Bird
```

```cpp
class Animal { public: void breathe(); };
class Dog  : public Animal { public: void bark(); };
class Cat  : public Animal { public: void meow(); };
class Bird : public Animal { public: void fly(); };
```

**Key Point:** All children share the same parent. No ambiguity between siblings (Dog can't access Cat's methods).

---

### TYPE 5: HYBRID INHERITANCE
> A combination of two or more types of inheritance

```
       A
      / \
     B   C
      \ /
       D
```

This is the combination of hierarchical + multiple inheritance. This leads to the famous **Diamond Problem** (Day 4 topic).

```cpp
class A { };
class B : public A { };
class C : public A { };
class D : public B, public C { };  // Hybrid — D gets A's copy TWICE!
```

**Key Point:** Hybrid inheritance causes the diamond problem. Solved using **virtual inheritance** (Day 4).

---

## 🔑 SECTION 1.5 — ACCESS SPECIFIER RULES IN INHERITANCE (CRUCIAL FOR PYQs)

### The Master Table — Memorise This!

| Member in Base Class | Public Inheritance → Access in Derived | Protected Inheritance → Access in Derived | Private Inheritance → Access in Derived |
|---------------------|----------------------------------------|------------------------------------------|----------------------------------------|
| **public** member | **public** | **protected** | **private** |
| **protected** member | **protected** | **protected** | **private** |
| **private** member | **NOT accessible** | **NOT accessible** | **NOT accessible** |

### Understanding this with an ATM Example:
```cpp
class BankAccount {
public:
    double balance;          // public
protected:
    string accountNumber;    // protected
private:
    string secretPin;        // private
};

class SavingsAccount : public BankAccount {
    // balance → public (still public)
    // accountNumber → protected (still protected)
    // secretPin → NOT accessible (private stays out)
};

class PremiumAccount : protected BankAccount {
    // balance → protected (downgraded from public)
    // accountNumber → protected (stays protected)
    // secretPin → NOT accessible
};

class TemporaryAccount : private BankAccount {
    // balance → private (downgraded from public)
    // accountNumber → private (downgraded from protected)
    // secretPin → NOT accessible
};
```

### The "Never Goes Up" Rule
Private members NEVER become accessible through inheritance, regardless of access mode. They are always inaccessible in derived class (but ARE present in memory — they're just hidden).

---

## 🔑 SECTION 1.6 — CONSTRUCTOR ORDER IN INHERITANCE

### Very Important PYQ Topic!

**Rule:** In inheritance, constructors execute from **Base to Derived** (top-down).
Destructors execute in **reverse order** — from **Derived to Base** (bottom-up).

```cpp
class A {
public:
    A() { cout << "A Constructor\n"; }
    ~A() { cout << "A Destructor\n"; }
};

class B : public A {
public:
    B() { cout << "B Constructor\n"; }
    ~B() { cout << "B Destructor\n"; }
};

class C : public B {
public:
    C() { cout << "C Constructor\n"; }
    ~C() { cout << "C Destructor\n"; }
};

int main() {
    C obj;
    return 0;
}
```

**Output:**
```
A Constructor     ← Base first
B Constructor     ← Then middle
C Constructor     ← Derived last
C Destructor      ← Reverse: Derived first
B Destructor
A Destructor      ← Base last
```

> 📌 **PYQ Trap:** "In which order are constructors called in multilevel inheritance?" → **Base class first, derived class last**

---

## 🔑 SECTION 1.7 — PROTECTED ACCESS SPECIFIER — THE MOST IMPORTANT FOR INHERITANCE

### Why `protected` exists:
- `public` = anyone can access (too open)
- `private` = only same class can access (too restricted — child can't access)
- `protected` = **same class + child classes** can access (PERFECT for inheritance)

```cpp
class Shape {
protected:
    double area;    // child classes can access this
private:
    double secret;  // ONLY Shape can access this
public:
    void show() { cout << area; }
};

class Circle : public Shape {
public:
    void calculate(double r) {
        area = 3.14 * r * r;   // ✅ OK — protected member
        // secret = 0;         // ❌ ERROR — private member
    }
};
```

---

## 🔑 SECTION 1.8 — REAL-WORLD INHERITANCE HIERARCHY (Complete Example)

```cpp
// ==========================================
// SCHOOL MANAGEMENT SYSTEM
// ==========================================

class Person {
protected:
    string name;
    int age;
public:
    Person(string n, int a) : name(n), age(a) {}
    void introduce() {
        cout << "I am " << name << ", age " << age << endl;
    }
};

class Employee : public Person {
protected:
    int employeeID;
    double salary;
public:
    Employee(string n, int a, int id, double sal)
        : Person(n, a), employeeID(id), salary(sal) {}
    void showSalary() {
        cout << "Salary: " << salary << endl;
    }
};

class Teacher : public Employee {
private:
    string subject;
public:
    Teacher(string n, int a, int id, double sal, string sub)
        : Employee(n, a, id, sal), subject(sub) {}
    void teach() {
        cout << name << " teaches " << subject << endl;
        // name → inherited from Person through Employee (protected) ✅
        // salary → inherited from Employee (protected) ✅
    }
};

// Teacher IS-A Employee IS-A Person  (Multilevel Inheritance)

int main() {
    Teacher t("Prag", 30, 101, 50000, "Computer Science");
    t.introduce();    // inherited from Person
    t.showSalary();   // inherited from Employee
    t.teach();        // own method
    return 0;
}
```

---

## 🔑 SECTION 1.9 — IMPORTANT TERMS QUICK REFERENCE

| Term | Meaning |
|------|---------|
| Base Class | Parent class; whose properties are inherited |
| Derived Class | Child class; inherits from base class |
| Super Class | Java term for parent class (same as base class) |
| Sub Class | Java term for child class (same as derived class) |
| IS-A Relationship | What inheritance models |
| HAS-A Relationship | What composition/aggregation models (NOT inheritance) |
| `extends` | Java keyword for inheritance |
| `:` (colon) | C++ syntax for inheritance |
| `super()` | Java keyword to call parent constructor |
| Overriding | Redefining parent's method in child class |
| Hiding | When child class has same-named static method as parent (Java) |

---

## 🔑 SECTION 1.10 — JAVA vs C++ INHERITANCE: EXAM COMPARISON TABLE

| Feature | C++ | Java |
|---------|-----|------|
| Keyword | `:` (colon) | `extends` |
| Multiple inheritance (classes) | ✅ Supported | ❌ NOT supported (use interfaces) |
| Multiple inheritance (interfaces) | ✅ (via virtual) | ✅ (via `implements`) |
| Default inheritance access | private | Always public |
| Call parent constructor | Initializer list: `Derived() : Base() {}` | `super()` in constructor body |
| `super` keyword | Not available (use `Base::method()`) | Available as `super.method()` |
| Override keyword | `override` (C++11, optional) | `@Override` annotation |
| Final class (no subclassing) | `final` keyword (C++11) | `final` keyword |

---

## 📋 DAY 3 — CS REVISION BULLETS (Write These in Your Notebook Tonight)

```
1. Inheritance = IS-A relationship. Composition = HAS-A relationship.
2. C++ uses colon (:), Java uses extends. Java has NO access specifier in inheritance.
3. NOT inherited: Constructors, Destructors, Private members, Friend functions.
4. 5 types: Single, Multiple, Multilevel, Hierarchical, Hybrid.
5. Java = NO multiple inheritance of classes (use interfaces with 'implements').
6. Constructor order: Base first → Derived last. Destructor: Derived first → Base last.
7. Protected = accessible in same class + child classes (not outside).
8. Public inheritance: public stays public, protected stays protected, private stays inaccessible.
9. Private inheritance: public and protected both become private.
10. Hybrid inheritance → Diamond Problem → Solved by virtual inheritance (Day 4).
```

---
---

# 📐 PART 2: GENERAL STUDIES — MATHEMATICS
# RATIO & PROPORTION — Complete Masterclass for BPSC TRE

---

> **Why This Topic?** Ratio & Proportion appears in EVERY BPSC TRE paper under the Maths section (8 questions/paper). It also forms the base for Profit & Loss, Partnership, Mixtures, and many other GS topics. Mastering this = free marks every time.

---

## 📘 SECTION 2.1 — RATIO: FOUNDATIONS

### Definition
A **ratio** is a comparison of two quantities of the same kind by division.

If A = 30 and B = 20, then ratio A : B = 30/20 = **3 : 2**

### Key Vocabulary
| Term | Meaning |
|------|---------|
| Antecedent | The FIRST term of the ratio (3 in 3:2) |
| Consequent | The SECOND term of the ratio (2 in 3:2) |
| Equivalent ratios | Ratios that are equal: 2:3 = 4:6 = 6:9 |
| Duplicate ratio | Square of a ratio: Duplicate of 3:4 = 9:16 |
| Sub-duplicate ratio | Square root of a ratio: Sub-duplicate of 9:16 = 3:4 |
| Triplicate ratio | Cube of a ratio: Triplicate of 2:3 = 8:27 |
| Inverse ratio | If ratio is a:b, inverse is b:a |

### Important Properties
1. Ratio has **no units** — it's a pure number
2. Ratio is only between quantities of the **same type**
3. Multiplying or dividing both terms by the same number does NOT change the ratio
   - 2:3 = 4:6 = 6:9 = 10:15 (all same ratio)
4. Order matters: 3:2 ≠ 2:3

---

## 📘 SECTION 2.2 — PROPORTION

### Definition
When two ratios are **equal**, they are said to be in **proportion**.

**a : b = c : d** can be written as **a : b :: c : d** (read as "a is to b as c is to d")

Here: a and d are called **EXTREMES**, b and c are called **MEANS**

### The Fundamental Property of Proportion
> **Product of Extremes = Product of Means**
> a × d = b × c

**Example:**
Is 2 : 3 :: 8 : 12 a valid proportion?
- Product of extremes = 2 × 12 = 24
- Product of means = 3 × 8 = 24
- 24 = 24 ✅ → YES, it's a proportion

---

## 📘 SECTION 2.3 — TYPES OF PROPORTION

### Type 1: Direct Proportion (Direct Variation)
When one quantity increases, the other also increases **proportionally**.

**Formula:** y = kx (where k is a constant)
**Or:** y₁/x₁ = y₂/x₂

**Real Examples:**
- More workers → more work done (in same time)
- More speed → more distance (in same time)
- More items → more cost

**Example Problem:**
If 5 kg of rice costs ₹200, what is the cost of 8 kg?

Using direct proportion: 200/5 = x/8
→ x = (200 × 8)/5 = **₹320**

---

### Type 2: Inverse Proportion (Indirect Variation / Inverse Variation)
When one quantity increases, the other **decreases** proportionally.

**Formula:** xy = k (constant)
**Or:** x₁y₁ = x₂y₂

**Real Examples:**
- More workers → less time to finish work
- More speed → less time for same distance
- More pipes → less time to fill tank

**Example Problem:**
10 workers can build a wall in 6 days. How many days for 15 workers?

Using inverse proportion: 10 × 6 = 15 × x
→ x = 60/15 = **4 days**

---

## 📘 SECTION 2.4 — FOUR TYPES OF PROPORTIONAL VALUES

### Fourth Proportional
If a : b = c : x, find x → x = (b × c)/a

**Example:** Find the fourth proportional to 3, 4, 9
3 : 4 = 9 : x
→ x = (4 × 9)/3 = **12**

---

### Third Proportional
If a : b = b : x, find x → x = b²/a

**Example:** Find the third proportional to 4 and 8
4 : 8 = 8 : x
→ x = (8 × 8)/4 = **16**

---

### Mean Proportional (Geometric Mean)
If a : x = x : b, find x → x = √(a × b)

**Example:** Find the mean proportional of 4 and 16
x = √(4 × 16) = √64 = **8**

Verification: 4 : 8 = 8 : 16 ✅ (both = 1:2)

---

## 📘 SECTION 2.5 — RATIO PROBLEMS: STANDARD TYPES

### TYPE A: Finding Unknown in a Ratio

**Problem:** The ratio of A to B is 3:5. If A = 24, find B.
**Solution:** 3/5 = 24/B → B = (24 × 5)/3 = **40**

---

### TYPE B: Distributing a Sum in a Given Ratio

**Problem:** Divide ₹840 between A and B in the ratio 3:4.
**Solution:**
- Total parts = 3 + 4 = 7
- A's share = (3/7) × 840 = ₹360
- B's share = (4/7) × 840 = ₹480
- Check: 360 + 480 = 840 ✅

---

### TYPE C: Three-Person Distribution

**Problem:** Divide ₹1200 among A, B, C in the ratio 2:3:5.
**Solution:**
- Total parts = 2 + 3 + 5 = 10
- A = (2/10) × 1200 = ₹240
- B = (3/10) × 1200 = ₹360
- C = (5/10) × 1200 = ₹600

---

### TYPE D: Ratio Changes After Addition/Removal

**Problem:** Ages of A and B are in ratio 3:5. After 4 years, the ratio becomes 5:7. Find current ages.

**Solution (Using Algebra):**
Let current ages: A = 3x, B = 5x

After 4 years: (3x + 4)/(5x + 4) = 5/7

Cross multiply: 7(3x + 4) = 5(5x + 4)
21x + 28 = 25x + 20
8 = 4x
x = 2

Therefore: A = 3×2 = **6 years**, B = 5×2 = **10 years**

---

### TYPE E: Comparing Multiple Ratios (Bring to Same Form)

**Problem:** A:B = 2:3 and B:C = 4:5. Find A:B:C.

**Solution:** Make B equal in both ratios.
A:B = 2:3 → Multiply by 4 → A:B = 8:12
B:C = 4:5 → Multiply by 3 → B:C = 12:15

Therefore A:B:C = **8:12:15**

---

### TYPE F: Partnership Problems (Uses Ratio)

**Problem:** A invests ₹3000, B invests ₹5000. They earn a profit of ₹4000. How is it divided?

**Solution:** Profit divided in ratio of investment = 3000:5000 = 3:5
A's profit = (3/8) × 4000 = ₹1500
B's profit = (5/8) × 4000 = ₹2500

---

## 📘 SECTION 2.6 — SHORTCUT TRICKS FOR BPSC TRE

### Trick 1: The Fraction Method (Fastest for distribution)
Instead of finding parts, directly calculate each person's share:
If ratio is a:b:c, then each share = (own ratio/sum of all ratios) × total

---

### Trick 2: Cross-Multiplication (For proportions)
a:b = c:x → x = (b × c)/a — always do this mentally

---

### Trick 3: Ratio Comparison
To compare a:b and c:d — cross multiply:
If ad > bc → a:b > c:d
If ad < bc → a:b < c:d

Example: Compare 3:5 and 4:7
3×7 = 21, 4×5 = 20
21 > 20 → 3:5 > 4:7

---

### Trick 4: Combining Ratios (Important for 3-person problems)
A:B = p:q and B:C = r:s → A:B:C = (p×r):(q×r):(q×s)

Example: A:B = 2:3, B:C = 3:4 → A:B:C = (2×3):(3×3):(3×4) = 6:9:12 = **2:3:4**
(when B terms are same, just write directly: 2:3:4)

---

## 📘 SECTION 2.7 — PROPORTION IN MIXING (ALLIGATION — BONUS TOPIC)

**Alligation Rule:** Used to find the ratio in which two ingredients must be mixed.

```
Mean value (d)
    /       \
Cheaper (c)  Dearer (e)
    \         /
  (e-d)     (d-c)
```

Ratio = (e - d) : (d - c)

**Example:** In what ratio must water (₹0/litre) and milk (₹30/litre) be mixed to get a mixture worth ₹20/litre?

- Cheaper = 0, Dearer = 30, Mean = 20
- Ratio = (30-20) : (20-0) = 10:20 = **1:2**

So mix water and milk in 1:2 ratio.

---

## 📘 SECTION 2.8 — RATIO & PROPORTION FORMULA SHEET

```
┌─────────────────────────────────────────────────────────────────┐
│                   RATIO & PROPORTION FORMULAS                   │
├─────────────────────────────────────────────────────────────────┤
│ Basic Ratio: a:b = a/b                                          │
│ Proportion: a:b::c:d → a×d = b×c                               │
│ Fourth proportional to a,b,c → x = bc/a                        │
│ Third proportional to a,b → x = b²/a                           │
│ Mean proportional of a,b → x = √(ab)                           │
│ If a:b = p:q → a = (p/(p+q))×(a+b), b = (q/(p+q))×(a+b)      │
│ Duplicate ratio of a:b = a²:b²                                  │
│ Sub-duplicate ratio of a:b = √a:√b                              │
│ Triplicate ratio of a:b = a³:b³                                 │
│ Compounded ratio of a:b and c:d = ac:bd                         │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 DAY 3 — GS REVISION BULLETS (Write in Notebook Tonight)

```
1. Ratio is comparison by division. No units.
2. Proportion: a:b::c:d means ad = bc (Extremes × Extremes = Means × Means)
3. Direct proportion: both increase together (y/x = constant)
4. Inverse proportion: one increases, other decreases (xy = constant)
5. Mean proportional of a and b = √(ab)
6. Third proportional to a, b = b²/a
7. To combine ratios A:B and B:C → make B value equal first
8. In distribution, each share = (own part / total parts) × total amount
9. Ratio changes with age problems: use algebra with variable x
10. Alligation: ratio = (dearer - mean) : (mean - cheaper)
```

---
---

# 📝 PRACTICE MCQs — DAY 3
## 20 PYQ-Pattern Questions (BPSC TRE Style, 5 Options: A/B/C/D/E)

> **Instructions:**
> - Option (D) = **More than one of the above** (could mean A+B, B+C, A+C, or A+B+C)
> - Option (E) = **None of the above**
> - Attempt all 20. Then check answers below with explanations.

---

### SECTION A: CS — INHERITANCE (Q1–12)

---

**Q1.** Which keyword is used in Java for implementing inheritance?

(A) extends  
(B) inherits  
(C) implements  
(D) More than one of the above  
(E) None of the above

---

**Q2.** Which of the following is NOT inherited by a derived class in C++?

(A) Public member functions  
(B) Private member functions  
(C) Protected data members  
(D) More than one of the above  
(E) None of the above

---

**Q3.** Which type of inheritance does NOT exist in Java?

(A) Single inheritance  
(B) Multilevel inheritance  
(C) Multiple inheritance using classes  
(D) More than one of the above  
(E) None of the above

---

**Q4.** In C++, the default access specifier for inheritance (when nothing is written) is:

(A) public  
(B) protected  
(C) private  
(D) More than one of the above  
(E) None of the above

---

**Q5.** Consider this C++ code:
```cpp
class A { };
class B : public A { };
class C : public A { };
class D : public B, public C { };
```
What type of inheritance is this?

(A) Multiple inheritance  
(B) Multilevel inheritance  
(C) Hybrid inheritance  
(D) More than one of the above  
(E) None of the above

---

**Q6.** In multilevel inheritance (A→B→C), when an object of C is created, which constructor is called FIRST?

(A) Constructor of C  
(B) Constructor of B  
(C) Constructor of A  
(D) More than one of the above  
(E) None of the above

---

**Q7.** Which of the following correctly defines the IS-A relationship?

(A) A Car HAS-A Engine  
(B) A Dog IS-A Animal  
(C) A Student HAS-A Pen  
(D) More than one of the above  
(E) None of the above

---

**Q8.** In public inheritance in C++, a protected member of the base class becomes _____ in the derived class.

(A) public  
(B) protected  
(C) private  
(D) More than one of the above  
(E) None of the above

---

**Q9.** Which of the following is true about private inheritance in C++?

(A) All public members of base become public in derived  
(B) All public members of base become private in derived  
(C) Private members of base become accessible in derived  
(D) More than one of the above  
(E) None of the above

---

**Q10.** Which inheritance type allows a single parent class to have multiple child classes?

(A) Multiple inheritance  
(B) Multilevel inheritance  
(C) Hierarchical inheritance  
(D) More than one of the above  
(E) None of the above

---

**Q11.** In C++, constructors are called in inheritance in which order?

(A) Derived class first, then base class  
(B) Base class first, then derived class  
(C) Random order — depends on compiler  
(D) More than one of the above  
(E) None of the above

---

**Q12.** Which of the following correctly represents C++ inheritance syntax?

(A) `class B extends A { }`  
(B) `class B : public A { }`  
(C) `class B inherits A { }`  
(D) More than one of the above  
(E) None of the above

---

### SECTION B: GS MATHS — RATIO & PROPORTION (Q13–20)

---

**Q13.** Divide ₹720 among A, B, and C in the ratio 2:3:4. What is B's share?

(A) ₹160  
(B) ₹240  
(C) ₹320  
(D) More than one of the above  
(E) None of the above

---

**Q14.** If a:b = 3:4 and b:c = 8:9, find a:c.

(A) 2:3  
(B) 1:3  
(C) 3:9  
(D) More than one of the above  
(E) None of the above

---

**Q15.** 12 men can complete a task in 15 days. In how many days will 9 men complete the same task?

(A) 18 days  
(B) 20 days  
(C) 24 days  
(D) More than one of the above  
(E) None of the above

---

**Q16.** Find the mean proportional between 9 and 25.

(A) 15  
(B) 17  
(C) 34  
(D) More than one of the above  
(E) None of the above

---

**Q17.** A:B = 2:3, B:C = 5:7. What is A:B:C?

(A) 10:15:21  
(B) 2:3:7  
(C) 10:21:35  
(D) More than one of the above  
(E) None of the above

---

**Q18.** The ages of Ravi and Rani are in ratio 5:3. After 6 years, ratio becomes 7:5. What is Ravi's current age?

(A) 15 years  
(B) 18 years  
(C) 20 years  
(D) More than one of the above  
(E) None of the above

---

**Q19.** Find the fourth proportional to 3, 7, and 15.

(A) 35  
(B) 5  
(C) 45  
(D) More than one of the above  
(E) None of the above

---

**Q20.** In what ratio must Type A tea (₹80/kg) and Type B tea (₹120/kg) be mixed to get a mixture worth ₹96/kg?

(A) 1:2  
(B) 2:1  
(C) 3:2  
(D) More than one of the above  
(E) None of the above

---

---

# ✅ ANSWER KEY WITH DETAILED EXPLANATIONS

---

**Q1. Answer: (A)**
Java uses `extends` keyword for class inheritance.
`implements` is used for interfaces in Java.
`inherits` is not a keyword in any major language.
"More than one" is wrong because only ONE correct keyword exists.

---

**Q2. Answer: (D) — More than one of the above [B and C are NOT inherited... wait — read carefully]**

Actually: Private member functions (B) are NOT inherited (they exist in derived but are inaccessible). Protected data members (C) ARE inherited.

**Correct Answer: (A) Private member functions** → Option **(B) alone** is what is NOT inherited.
Wait — let us be precise:

- **Public member functions (A)** → ARE inherited ✅
- **Private member functions (B)** → NOT inherited/accessible ✅ ← this is not inherited
- **Protected data members (C)** → ARE inherited ✅

**Answer: (B)** — Private member functions are NOT accessible in derived class.

> 📌 Note: Also constructors and destructors are NOT inherited, but they weren't given as options here.

---

**Q3. Answer: (C)**
Java does NOT support multiple inheritance of classes. Single inheritance (A) and multilevel inheritance (B) are fully supported in Java. Only multiple inheritance through classes is absent — Java uses interfaces (`implements`) instead.

---

**Q4. Answer: (C) — private**
When no access specifier is written in C++ inheritance, it defaults to **private**.
Example: `class B : A { }` is same as `class B : private A { }`

---

**Q5. Answer: (C) — Hybrid inheritance**
This is a combination of hierarchical (A and B, A and C both derive from A) and multiple inheritance (D derives from both B and C). The resulting diamond shape = Hybrid. This also leads to the Diamond Problem.

---

**Q6. Answer: (C) — Constructor of A**
In multilevel inheritance A→B→C, when C's object is created:
- First: A's constructor
- Then: B's constructor
- Last: C's constructor
Base class constructor is ALWAYS called first.

---

**Q7. Answer: (B)**
"Dog IS-A Animal" correctly demonstrates the IS-A relationship that inheritance models.
Options A and C describe HAS-A relationships (composition). Only B is correct.

---

**Q8. Answer: (B) — protected**
In PUBLIC inheritance, a protected member of the base class remains **protected** in the derived class. Public members remain public. Private members are inaccessible.

---

**Q9. Answer: (B)**
In PRIVATE inheritance, ALL public and protected members of base become **private** in the derived class. Private members of base remain inaccessible (C is wrong). So correct answer is B.

---

**Q10. Answer: (C) — Hierarchical inheritance**
Hierarchical = one parent → many children. This is the correct definition.
Multiple inheritance = one child ← many parents (opposite).
Multilevel = chain (A→B→C).

---

**Q11. Answer: (B) — Base class first, then derived class**
Constructor order: Base → Derived (top-down in hierarchy)
Destructor order: Derived → Base (bottom-up, reverse)
This is a GUARANTEED topic in BPSC TRE exams.

---

**Q12. Answer: (B) — `class B : public A { }`**
C++ uses colon `:` with access specifier for inheritance.
`extends` is Java syntax (A is wrong). `inherits` is not valid (C is wrong).

---

**Q13. Answer: (B) — ₹240**
Ratio 2:3:4 → Total parts = 9
B's share = (3/9) × 720 = (1/3) × 720 = **₹240**

---

**Q14. Answer: (A) — 2:3**
a:b = 3:4 and b:c = 8:9
Make b equal: LCM of 4 and 8 = 8
a:b = 3:4 × 2 = 6:8
b:c = 8:9
Therefore a:c = 6:9 = **2:3**

---

**Q15. Answer: (B) — 20 days**
More men → fewer days = Inverse proportion
12 × 15 = 9 × x
x = 180/9 = **20 days**

---

**Q16. Answer: (A) — 15**
Mean proportional of 9 and 25 = √(9 × 25) = √225 = **15**
Verify: 9:15 = 15:25 = 3:5 ✅

---

**Q17. Answer: (A) — 10:15:21**
A:B = 2:3, B:C = 5:7
Make B equal: LCM(3,5) = 15
A:B = 2:3 × 5 = 10:15
B:C = 5:7 × 3 = 15:21
A:B:C = **10:15:21**

---

**Q18. Answer: (A) — 15 years**
Let Ravi = 5x, Rani = 3x
After 6 years: (5x+6)/(3x+6) = 7/5
5(5x+6) = 7(3x+6)
25x + 30 = 21x + 42
4x = 12 → x = 3
Ravi's age = 5×3 = **15 years**

---

**Q19. Answer: (A) — 35**
Fourth proportional to a, b, c = bc/a
= (7 × 15)/3 = 105/3 = **35**

---

**Q20. Answer: (A) — 1:2**
Using Alligation:
Type A (₹80), Type B (₹120), Mean (₹96)
Ratio = (120-96) : (96-80) = 24 : 16 = **3:2**

Wait — let us verify: (3×80 + 2×120)/(3+2) = (240+240)/5 = 480/5 = ₹96 ✅

**Answer: (E) — None of the above** (correct ratio is 3:2, which is NOT in options A or B)

> 📌 **This is exactly how BPSC TRE tricks you** — option C says 3:2 but the question has it as Type A:Type B. Wait — option (C) is 3:2.

Re-reading options: (A) 1:2, (B) 2:1, **(C) 3:2** ← This IS correct.

**Final Answer: (C) — 3:2**

---

---

# 🧠 TOPPER TIPS — DAY 3 SPECIAL

## For Inheritance Questions:
1. **Always check syntax carefully** — colon vs extends, access specifier placement
2. **Private members are the trap** — they exist in derived class memory but are inaccessible. Don't confuse "not inherited" with "not in memory"
3. **Java multiple inheritance** — always remember Java doesn't support it for classes; only for interfaces
4. **Constructor order** — draw a quick mental diagram: arrows pointing up = constructor call direction (from bottom-up through the hierarchy means calling from top to bottom)
5. **For "more than one correct" questions** — in IS-A vs HAS-A, only IS-A is inheritance; be careful

## For Ratio & Proportion Questions:
1. **Alligation is a shortcut** — learn it well for mixing problems
2. **Mean proportional = √(ab)** — remember this formula exactly
3. **Age ratio problems** — always set up as 5x and 3x, then form equation from after-years condition
4. **Combining ratios** — always make the common term equal first using LCM
5. **Distribution problems** — always add ratio terms to get total parts first

---

# 📊 DAY 3 SELF-ASSESSMENT

After completing today, rate yourself:

| Topic | Confidence (1-10) | Questions Correct | Target |
|-------|------------------|-------------------|--------|
| Inheritance Types | | /12 | 10/12 |
| C++/Java Syntax | | included | |
| Ratio Basics | | /8 | 7/8 |
| **Total Day 3** | | /20 | **17/20** |

If score < 14/20 → Revise the sections where you got wrong answers before tomorrow.

---

# 🔁 QUICK REVISION FLASHCARDS (Night Study — 30 Minutes)

```
FLASHCARD 1: C++ Inheritance syntax?
→ class Derived : access Base { }

FLASHCARD 2: Java Inheritance syntax?
→ class Derived extends Base { }

FLASHCARD 3: Java supports multiple inheritance?
→ NO for classes. YES for interfaces (implements)

FLASHCARD 4: What is NOT inherited?
→ Constructors, Destructors, Private members, Friend functions

FLASHCARD 5: Constructor call order in inheritance?
→ Base first, Derived last (top to bottom)

FLASHCARD 6: Destructor call order?
→ Derived first, Base last (reverse of constructors)

FLASHCARD 7: IS-A vs HAS-A?
→ IS-A = inheritance; HAS-A = composition

FLASHCARD 8: 5 types of inheritance?
→ Single, Multiple, Multilevel, Hierarchical, Hybrid

FLASHCARD 9: Diamond problem from which inheritance type?
→ Hybrid (Multiple + Hierarchical)

FLASHCARD 10: Mean proportional of a and b?
→ √(ab)

FLASHCARD 11: Fourth proportional to a, b, c?
→ bc/a

FLASHCARD 12: Third proportional to a, b?
→ b²/a

FLASHCARD 13: Direct proportion formula?
→ y/x = constant (k)

FLASHCARD 14: Inverse proportion formula?
→ xy = constant (k)

FLASHCARD 15: Alligation ratio formula?
→ (Dearer − Mean) : (Mean − Cheaper)
```

---

*📅 Day 3 Complete | Next: Day 4 — Virtual Inheritance & Diamond Problem (CS) + Number System (GS)*
*BPSC TRE 4.0 Study Plan | Target: TOP RANK*
