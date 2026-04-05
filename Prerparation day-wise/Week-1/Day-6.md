# 📅 BPSC TRE 4.0 — DAY 6 COMPLETE STUDY MATERIAL
## CS Topic: Constructors & Destructors | GS Topic: Maths — LCM & HCF
### 🎯 Target: TOPPER RANK | Phase 1 — Week 1 | OOP Series

---

> **Topper Tip:** Day 6 covers one of the most exam-favourite OOP sub-topics. Constructors appear in **every TRE paper** — either directly (output prediction) or conceptually. Read each section carefully, understand the diagrams, then attempt ALL 50 MCQs on your own before looking at answers.

---

# ═══════════════════════════════════════════
# 🟥 PART 1 — COMPUTER SCIENCE
# CONSTRUCTORS & DESTRUCTORS
# ═══════════════════════════════════════════

## 📌 SECTION 1.1 — WHAT IS A CONSTRUCTOR?

A **Constructor** is a special member function that is **automatically called when an object is created**.

### Rules — MUST MEMORISE FOR EXAM:
| Rule | Description |
|------|-------------|
| Same name as class | Constructor name = Class name |
| No return type | NOT even `void` — absolutely nothing |
| Called automatically | No need to call it manually |
| Can be overloaded | Multiple constructors allowed |
| Cannot be virtual | Constructors are NEVER virtual |
| Cannot be static | Constructors are NOT static |
| Cannot be inherited | Derived class cannot inherit constructor |
| Can use `this` pointer | Yes, allowed |

---

## 📌 SECTION 1.2 — TYPES OF CONSTRUCTORS

### ┌──────────────────────────────────────────────────────────────────┐
### │              CONSTRUCTOR FAMILY TREE                            │
### │                                                                  │
### │                    CONSTRUCTOR                                   │
### │                         │                                        │
### │           ┌─────────────┼─────────────────┐                     │
### │           │             │                 │                      │
### │       DEFAULT      PARAMETERIZED        COPY                    │
### │    (no arguments)  (with arguments)  (object as arg)            │
### └──────────────────────────────────────────────────────────────────┘

---

### TYPE 1: DEFAULT CONSTRUCTOR

- Takes **no parameters**
- Compiler creates one automatically if you define NO constructor
- If you define ANY constructor, the compiler does NOT auto-create a default one

```cpp
class Student {
public:
    string name;
    int age;
    
    // DEFAULT CONSTRUCTOR
    Student() {
        name = "Unknown";
        age = 0;
        cout << "Default constructor called" << endl;
    }
};

int main() {
    Student s1;    // Default constructor called automatically
    return 0;
}
```

**Output:** `Default constructor called`

---

### TYPE 2: PARAMETERIZED CONSTRUCTOR

- Takes **one or more parameters**
- Used to initialize object with specific values at creation time
- Supports **Constructor Overloading**

```cpp
class Student {
public:
    string name;
    int age;
    
    // PARAMETERIZED CONSTRUCTOR
    Student(string n, int a) {
        name = n;
        age = a;
        cout << "Parameterized: " << name << ", " << age << endl;
    }
};

int main() {
    Student s1("Prag", 25);       // Direct initialization
    Student s2 = Student("Raj", 22);  // Copy initialization
    return 0;
}
```

**Output:**
```
Parameterized: Prag, 25
Parameterized: Raj, 22
```

---

### TYPE 3: COPY CONSTRUCTOR

- Takes a **reference to an object of the same class** as parameter
- Used to create a new object as a **copy of an existing object**
- Signature: `ClassName(const ClassName& obj)`

```cpp
class Student {
public:
    string name;
    int age;
    
    Student(string n, int a) {       // Parameterized
        name = n; age = a;
    }
    
    // COPY CONSTRUCTOR
    Student(const Student& s) {
        name = s.name;
        age = s.age;
        cout << "Copy constructor called" << endl;
    }
};

int main() {
    Student s1("Prag", 25);
    Student s2(s1);         // Copy constructor called
    Student s3 = s1;        // Also calls Copy constructor (NOT assignment operator)
    return 0;
}
```

**Output:**
```
Copy constructor called
Copy constructor called
```

---

### 🚨 EXAM TRAP: COPY CONSTRUCTOR vs ASSIGNMENT OPERATOR

```cpp
Student s2(s1);     // → COPY CONSTRUCTOR (new object created)
Student s3 = s1;    // → COPY CONSTRUCTOR (new object created, NOT assignment)
s3 = s1;            // → ASSIGNMENT OPERATOR (s3 already existed before this line)
```

**Key Rule:** If a **new object is being created** → Copy Constructor
If an **existing object is being assigned** → Assignment Operator

---

## 📌 SECTION 1.3 — DEEP COPY vs SHALLOW COPY

This is a HIGH-FREQUENCY concept. Understand it well.

### ┌────────────────────────────────────────────────────────────────┐
### │    SHALLOW COPY (Default)          DEEP COPY (Custom)         │
### │                                                                │
### │  Object A    Object B           Object A     Object B         │
### │  ┌──────┐   ┌──────┐           ┌──────┐    ┌──────┐         │
### │  │ ptr  │──►│ DATA │           │ ptr  │──► │COPY  │         │
### │  └──────┘   └──────┘           └──────┘    │OF    │         │
### │  │ ptr  │──►│      │           ┌──────┐    │DATA  │         │
### │  └──────┘   └──────┘           │ ptr  │──► └──────┘         │
### │                                └──────┘                      │
### │  BOTH pointers point to        Each has its OWN copy of data │
### │  the SAME memory!              → Safe! No conflict            │
### └────────────────────────────────────────────────────────────────┘

| Feature | Shallow Copy | Deep Copy |
|---------|-------------|-----------|
| What is copied? | Only pointer value (address) | Actual data at that address |
| Memory | Same memory shared | Separate memory allocated |
| Problem | Deleting one corrupts other | Safe to delete independently |
| Used when | No dynamic memory | Class has pointers/dynamic members |
| Default copy constructor | Shallow | Must write custom for Deep |

**Exam Fact:** Default (compiler-generated) copy constructor does **SHALLOW COPY**.
For classes with pointers, you must write a custom copy constructor for **DEEP COPY**.

---

## 📌 SECTION 1.4 — CONSTRUCTOR INITIALIZER LIST

A more efficient way to initialize members, especially for `const` and `reference` members:

```cpp
class Student {
    string name;
    const int rollNo;   // const member — MUST be initialized in initializer list
public:
    // INITIALIZER LIST syntax: ClassName(params) : member1(val1), member2(val2)
    Student(string n, int r) : name(n), rollNo(r) {
        // body
    }
};
```

**Exam Fact:** `const` data members and `reference` members **MUST** be initialized using the initializer list. They CANNOT be assigned inside the constructor body.

---

## 📌 SECTION 1.5 — DESTRUCTOR

A **Destructor** is a special member function called automatically when an object goes out of scope or is deleted.

### Rules — MUST MEMORISE:
| Rule | Description |
|------|-------------|
| Same name as class, with `~` | `~ClassName()` |
| No parameters | NEVER takes arguments |
| No return type | Not even void |
| Only ONE per class | Cannot be overloaded |
| Called automatically | When object's lifetime ends |
| Can be virtual | YES — unlike constructors! |
| Should be virtual in base class | Best practice for polymorphism |

```cpp
class Student {
public:
    string name;
    
    Student(string n) : name(n) {
        cout << "Constructor: " << name << " created" << endl;
    }
    
    ~Student() {
        cout << "Destructor: " << name << " destroyed" << endl;
    }
};

int main() {
    Student s1("Prag");
    Student s2("Raj");
    return 0;    // Both destructors called automatically here
}
```

**Output:**
```
Constructor: Prag created
Constructor: Raj created
Destructor: Raj destroyed    ← LIFO order! Last created, first destroyed
Destructor: Prag destroyed
```

**Key Pattern:** Objects are destroyed in **reverse order** of creation — **LIFO (Last In, First Out)**.

---

## 📌 SECTION 1.6 — VIRTUAL DESTRUCTOR (HIGH PRIORITY!)

This is a classic exam question topic.

```cpp
class Base {
public:
    Base() { cout << "Base Constructor\n"; }
    ~Base() { cout << "Base Destructor\n"; }    // NOT virtual — PROBLEM!
};

class Derived : public Base {
public:
    Derived() { cout << "Derived Constructor\n"; }
    ~Derived() { cout << "Derived Destructor\n"; }
};

int main() {
    Base* ptr = new Derived();  // Polymorphism
    delete ptr;                 // Which destructor is called?
}
```

**Without virtual:**
```
Output: Base Constructor → Derived Constructor → Base Destructor
```
**Derived destructor is NEVER called → Memory Leak!**

**With `virtual ~Base()`:**
```
Output: Base Constructor → Derived Constructor → Derived Destructor → Base Destructor
```

**Exam Rule:** If a class is used as a base class with dynamic memory, ALWAYS make the destructor `virtual`.

---

## 📌 SECTION 1.7 — ORDER OF CONSTRUCTOR/DESTRUCTOR IN INHERITANCE

This is asked directly in BPSC TRE PYQs — memorise this diagram:

### ┌──────────────────────────────────────────────────────────────┐
### │  INHERITANCE: Order of Constructor/Destructor Calls         │
### │                                                              │
### │  class A → class B → class C  (multilevel)                  │
### │                                                              │
### │  CONSTRUCTION ORDER:     DESTRUCTION ORDER:                 │
### │  A() called first        C() destroyed first                │
### │  B() called second   →   B() destroyed second               │
### │  C() called last         A() destroyed last                 │
### │                                                              │
### │  Rule: Base FIRST → Derived LAST (construction)             │
### │  Rule: Derived FIRST → Base LAST (destruction)              │
### └──────────────────────────────────────────────────────────────┘

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
A Constructor
B Constructor
C Constructor
C Destructor
B Destructor
A Destructor
```

---

## 📌 SECTION 1.8 — KEY EXAM FACTS SUMMARY (Quick Revision Table)

| Topic | Exam-Ready Fact |
|-------|----------------|
| Constructor name | Same as class name |
| Constructor return type | NONE (not even void) |
| Can constructor be virtual? | NO |
| Can destructor be virtual? | YES (and should be for base classes) |
| How many destructors per class? | ONLY ONE — cannot be overloaded |
| Default constructor | Compiler provides IF no constructor defined |
| Copy constructor trigger | New object from existing object |
| Assignment operator trigger | Existing object assigned from another |
| Object creation order | Declared first → created first |
| Object destruction order | LIFO — last created, first destroyed |
| Destructor in inheritance | Base last, Derived first |
| Constructor in inheritance | Base first, Derived last |
| `const` member initialization | Only in initializer list |
| Shallow vs Deep copy | Default = Shallow; Pointer classes need Deep |

---

## 📌 SECTION 1.9 — CONSTRUCTOR OVERLOADING

Multiple constructors in the same class with **different parameter lists**:

```cpp
class Rectangle {
    int length, width;
public:
    Rectangle() : length(0), width(0) {}               // Default
    Rectangle(int l) : length(l), width(l) {}           // Square
    Rectangle(int l, int w) : length(l), width(w) {}    // Full
    
    int area() { return length * width; }
};

int main() {
    Rectangle r1;           // 0 × 0 = 0
    Rectangle r2(5);        // 5 × 5 = 25 (square)
    Rectangle r3(4, 6);     // 4 × 6 = 24
    return 0;
}
```

---

## 📌 SECTION 1.10 — QUICK MEMORY HOOKS 🧠

| Concept | Memory Hook |
|---------|------------|
| Constructor has no return type | "C for Creator — creates, doesn't return" |
| Destructor can be virtual | "D for Destroyer — can be overridden" |
| Only 1 destructor | "Death comes once — no overloading" |
| Copy constructor = new object | "Copy makes a NEW person" |
| Assignment = existing object | "Assignment gives job to existing person" |
| Constructor order = Base first | "Parents born before children" |
| Destructor order = Derived first | "Children retire before parents" |

---

---

# ═══════════════════════════════════════════
# 🟦 PART 2 — GENERAL STUDIES (GS/GK)
# MATHEMATICS: LCM & HCF
# ═══════════════════════════════════════════

## 📌 SECTION 2.1 — HCF (Highest Common Factor)

**Also called:** GCD (Greatest Common Divisor), GCF (Greatest Common Factor)

**Definition:** The **largest number** that divides ALL the given numbers exactly (without remainder).

### Method 1: Prime Factorization
**HCF = Product of COMMON prime factors with LOWEST powers**

**Example:** Find HCF of 12 and 18
```
12 = 2² × 3¹
18 = 2¹ × 3²

Common factors: 2 and 3
Take LOWEST powers: 2¹ × 3¹ = 6

HCF(12, 18) = 6 ✓
```

### Method 2: Division Method (Euclidean Algorithm)
Divide larger by smaller → if remainder ≠ 0, divide previous divisor by remainder → repeat until remainder = 0. Last divisor = HCF.

**Example:** HCF(48, 18)
```
48 ÷ 18 = 2, remainder 12
18 ÷ 12 = 1, remainder 6
12 ÷ 6  = 2, remainder 0

HCF = 6 ✓
```

---

## 📌 SECTION 2.2 — LCM (Lowest Common Multiple)

**Definition:** The **smallest number** that is divisible by ALL the given numbers.

### Method 1: Prime Factorization
**LCM = Product of ALL prime factors with HIGHEST powers**

**Example:** Find LCM of 12 and 18
```
12 = 2² × 3¹
18 = 2¹ × 3²

ALL factors with HIGHEST powers: 2² × 3² = 4 × 9 = 36

LCM(12, 18) = 36 ✓
```

### Method 2: Division Method (for multiple numbers)
```
Find LCM of 4, 6, 12:

2 | 4  6  12
2 | 2  3   6
3 | 1  3   3
  | 1  1   1

LCM = 2 × 2 × 3 = 12 ✓
```

---

## 📌 SECTION 2.3 — GOLDEN RELATIONSHIP

### ┌──────────────────────────────────────────────────────────────┐
### │                 MASTER FORMULA                               │
### │                                                              │
### │     HCF × LCM = Product of the TWO numbers                 │
### │                                                              │
### │  ⚠️ THIS FORMULA WORKS ONLY FOR TWO NUMBERS!               │
### │                                                              │
### │  If HCF = H, LCM = L, Numbers = A and B:                   │
### │       H × L = A × B                                         │
### │       A = (H × L) / B                                       │
### │       B = (H × L) / A                                       │
### └──────────────────────────────────────────────────────────────┘

**Example:** HCF of two numbers = 4, LCM = 48, one number = 12. Find the other.
```
Other = (HCF × LCM) / Known = (4 × 48) / 12 = 192 / 12 = 16 ✓
```

---

## 📌 SECTION 2.4 — KEY PROPERTIES (Exam Favourite Rules)

### Property Set A:
| Property | Statement |
|----------|-----------|
| HCF ≤ both numbers | HCF is always ≤ smaller number |
| LCM ≥ both numbers | LCM is always ≥ larger number |
| HCF divides LCM | LCM is always a multiple of HCF |
| Co-prime numbers | HCF = 1; LCM = Product of the numbers |

### Property Set B — "When numbers are multiples":
```
If one number is a multiple of another:
HCF = Smaller number
LCM = Larger number

Example: HCF(4, 12) = 4, LCM(4, 12) = 12
```

### Property Set C — "Fractions":
```
HCF of fractions = HCF of Numerators / LCM of Denominators
LCM of fractions = LCM of Numerators / HCF of Denominators

Example: HCF(2/3, 4/9) = HCF(2,4) / LCM(3,9) = 2/9
         LCM(2/3, 4/9) = LCM(2,4) / HCF(3,9) = 4/3
```

---

## 📌 SECTION 2.5 — APPLICATION PROBLEMS (High Exam Frequency)

### Problem Type 1: "Largest container" / "Maximum equal groups"
**Use HCF** when: Splitting into maximum EQUAL groups, largest tile, largest container

> **Model:** Three containers hold 36L, 48L, and 60L. What is the largest equal measure that can fill all three exactly?
> HCF(36, 48, 60) = 12 litres ✓

### Problem Type 2: "Minimum number of days/items"
**Use LCM** when: First time things coincide, minimum time for cycles to repeat, traffic lights

> **Model:** Two bells ring every 15 min and 20 min. After ringing together at 6 AM, when do they ring together again?
> LCM(15, 20) = 60 min → 7:00 AM ✓

### Problem Type 3: "Greatest number that divides… leaving remainder r"
```
Greatest number dividing A, B, C leaving remainder r:
= HCF(A-r, B-r, C-r)

Example: Greatest number dividing 25, 37, 55 leaving remainder 1 each:
= HCF(24, 36, 54) = 6 ✓
```

### Problem Type 4: "Least number divisible by… leaving remainder r"
```
Least number = LCM(A, B, C) + r

Example: Least number that when divided by 4, 6, 8 leaves remainder 3:
= LCM(4, 6, 8) + 3 = 24 + 3 = 27 ✓
```

### Problem Type 5: "Leaving different remainders"
```
Least number that when divided by A, B, C leaves remainders r1, r2, r3:
Check: If (A - r1) = (B - r2) = (C - r3) = k (same difference)

Least number = LCM(A, B, C) - k

Example: Divided by 5, 6, 7 leaves remainders 4, 5, 6 respectively.
5-4=1, 6-5=1, 7-6=1 → k = 1
LCM(5,6,7) = 210
Answer = 210 - 1 = 209 ✓
```

---

## 📌 SECTION 2.6 — QUICK FORMULA SHEET

```
┌───────────────────────────────────────────────────────┐
│             LCM & HCF — FORMULA CARD                  │
│                                                        │
│  HCF = Common prime factors × Lowest powers           │
│  LCM = All prime factors × Highest powers             │
│                                                        │
│  HCF × LCM = A × B  (for 2 numbers only)             │
│                                                        │
│  HCF of fractions = HCF(N) / LCM(D)                  │
│  LCM of fractions = LCM(N) / HCF(D)                  │
│                                                        │
│  Divide with same remainder r:                        │
│    Greatest divisor = HCF(A-r, B-r, C-r)             │
│                                                        │
│  Least divisible with remainder r:                    │
│    = LCM(A,B,C) + r                                   │
│                                                        │
│  Different remainders, same difference k:             │
│    = LCM(A,B,C) - k                                   │
└───────────────────────────────────────────────────────┘
```

---

---

# ═══════════════════════════════════════════
# 🟩 PART 3 — GENERAL KNOWLEDGE (GK)
# MODERN INDIAN HISTORY — DAY 6 GK SUPPLEMENT
# (Bihar Focus — High Exam Priority)
# ═══════════════════════════════════════════

## 📌 SECTION 3.1 — IMPORTANT MOVEMENTS & FACTS

### Bihar in the Freedom Struggle:

| Event | Year | Key Person | Key Fact |
|-------|------|-----------|---------|
| Champaran Satyagraha | 1917 | Mahatma Gandhi | **First civil disobedience** in India; Gandhi's first in India |
| Champaran Satyagraha | 1917 | Rajendra Prasad | Assisted Gandhi; later became India's 1st President |
| Non-Cooperation Movement | 1920–22 | Gandhi | INC Gaya session 1922 presided by Chittaranjan Das |
| Bihar Provincial Congress | Founded 1908 | — | HQ: Patna |
| Anushilan Samiti Patna | 1913 | Sachindra Nath Sanyal | Revolutionary organisation |
| Bihar Socialist Party | 1931 | Phulan Prasad Varma + Jayaprakash Narayan | JP's first political formation |
| AIKS Bihar | 1936 | Swami Sahajanand Saraswati | All India Kisan Sabha |
| Birsa Munda Revolt | 1899–1900 | Birsa Munda | Commander-in-Chief: **Gaya Munda** |

---

## 📌 SECTION 3.2 — KEY NATIONAL FACTS

| Topic | Fact |
|-------|------|
| First INC Session | 1885, Bombay; President: W.C. Bonnerjee |
| Grand Old Man of India | Dadabhai Naoroji |
| Revolt of 1857 | First called "War of Independence" by V.D. Savarkar |
| Jallianwala Bagh | 1919; Viceroy: Lord Chelmsford; General Dyer ordered firing |
| Abhinav Bharat | Founded in London by V.D. Savarkar |
| Ghadar Party | Established in USA (San Francisco), 1913 |
| Anandamath | Written by Bankim Chandra; mentions Sannyasi Revolt |
| Bardoli Satyagraha | Led by Sardar Vallabhbhai Patel (1928) |
| Home Rule Movement | Annie Besant + Bal Gangadhar Tilak (NOT Sarojini Naidu) |
| Vande Mataram | From Anandamath by Bankim Chandra Chattopadhyay |

---

## 📌 SECTION 3.3 — BIHAR GK FACTS

| Topic | Fact |
|-------|------|
| Bihar population (% of India) | 8.58% |
| District with max paddy production | Rohtas |
| District with max silk textile | Bhagalpur |
| First Bhojpuri film | Ganga Maiya Tohe Piyari Chadhaibo (1963) |
| Bihar state bird | House Sparrow |
| Bihar state animal | Gaur (Indian Bison) |
| Bihar state flower | Kachnar |
| Bihar's longest river | Ganga (flows through Bihar from W to E) |
| Vikramshila University | Located in Bhagalpur, ancient university |
| Nalanda University | Ancient; in Rajgir/Nalanda district |

---

---

# ═══════════════════════════════════════════
# 🧪 PART 4 — PRACTICE MCQs
# ⚠️ SOLVE ALL QUESTIONS BEFORE CHECKING ANSWERS
# ═══════════════════════════════════════════

---

## 📘 COMPUTER SCIENCE — 25 MCQs
### (Constructors, Destructors, OOP — All Levels)

---

**Q1. [LEVEL: Easy]** Which of the following statements about a constructor is CORRECT?

(A) A constructor must have a return type of void
(B) A constructor can be virtual
(C) A constructor is called automatically when an object is created
(D) More than one of the above
(E) None of the above

---

**Q2. [LEVEL: Easy]** How many destructors can a class have in C++?

(A) Zero
(B) Only one
(C) One per constructor
(D) More than one of the above
(E) None of the above

---

**Q3. [LEVEL: Easy]** Which of the following is the correct syntax for a destructor of class `Car`?

(A) `void ~Car()`
(B) `Car~()`
(C) `~Car()`
(D) More than one of the above
(E) None of the above

---

**Q4. [LEVEL: Easy]** A default constructor is one that:

(A) Takes a class object as its parameter
(B) Takes no parameters (or all parameters have default values)
(C) Initializes all variables to zero
(D) More than one of the above
(E) None of the above

---

**Q5. [LEVEL: Easy]** What happens if you do not define any constructor in a C++ class?

(A) Compilation error occurs
(B) Objects cannot be created
(C) Compiler automatically provides a default constructor
(D) More than one of the above
(E) None of the above

---

**Q6. [LEVEL: Medium]** Consider the code:
```cpp
class A { public: A() { cout << "A "; } ~A() { cout << "~A "; } };
class B : public A { public: B() { cout << "B "; } ~B() { cout << "~B "; } };
int main() { B obj; return 0; }
```
What is the output?

(A) A B ~A ~B
(B) B A ~B ~A
(C) A B ~B ~A
(D) More than one of the above
(E) None of the above

---

**Q7. [LEVEL: Medium]** A copy constructor takes which type of argument?

(A) A pointer to an object of the same class
(B) A reference to an object of the same class
(C) An integer value
(D) More than one of the above
(E) None of the above

---

**Q8. [LEVEL: Medium]** When is the copy constructor called?

(A) When `s2 = s1` and s2 was declared earlier
(B) When `Student s2(s1)` is executed
(C) When `Student s2 = s1` and s2 is being created for the first time
(D) More than one of the above — both B and C
(E) None of the above

---

**Q9. [LEVEL: Medium]** Which of the following CANNOT be done with a constructor?

(A) Constructor overloading
(B) Making a constructor virtual
(C) Using default arguments in a constructor
(D) More than one of the above
(E) None of the above

---

**Q10. [LEVEL: Medium]** `const` data members of a class:

(A) Can be initialized in the constructor body using assignment
(B) Must be initialized using the constructor initializer list
(C) Cannot be used in a class at all
(D) More than one of the above
(E) None of the above

---

**Q11. [LEVEL: Medium]** The compiler-provided default copy constructor performs:

(A) Deep copy of all members
(B) Shallow copy of all members
(C) No copy at all
(D) More than one of the above
(E) None of the above

---

**Q12. [LEVEL: Medium]** Which is TRUE about virtual destructors?

(A) A destructor can be made virtual
(B) A virtual destructor ensures proper cleanup in polymorphism
(C) A constructor can also be made virtual
(D) More than one of the above — both A and B
(E) None of the above

---

**Q13. [LEVEL: Medium]** In C++, which of the following is a problem caused by NOT having a virtual destructor in a base class when deleting through a base class pointer?

(A) Compile-time error
(B) Memory leak and undefined behavior due to derived destructor not being called
(C) Segmentation fault during construction
(D) More than one of the above
(E) None of the above

---

**Q14. [LEVEL: Hard]** What is the output of this code?
```cpp
#include<iostream>
using namespace std;
class X {
public:
    X() { cout << "X "; }
    ~X() { cout << "~X "; }
};
class Y : public X {
public:
    Y() { cout << "Y "; }
    ~Y() { cout << "~Y "; }
};
class Z : public Y {
public:
    Z() { cout << "Z "; }
    ~Z() { cout << "~Z "; }
};
int main() {
    Z obj;
    return 0;
}
```

(A) X Y Z ~X ~Y ~Z
(B) Z Y X ~Z ~Y ~X
(C) X Y Z ~Z ~Y ~X
(D) More than one of the above
(E) None of the above

---

**Q15. [LEVEL: Hard]** Which of the following statements about the copy constructor is INCORRECT?

(A) It is called when a function returns an object by value
(B) It is called when passing an object by value to a function
(C) It is always called when using the assignment operator on existing objects
(D) More than one of the above
(E) None of the above

---

**Q16. [LEVEL: Hard]** Consider:
```cpp
class Demo {
    int* data;
public:
    Demo(int val) { data = new int(val); }
    ~Demo() { delete data; }
};
int main() {
    Demo d1(5);
    Demo d2(d1);   // Copy
    return 0;
}
```
What is the problem with this code?

(A) `d1` and `d2` will point to the same memory; deleting both causes double-free error
(B) Compilation error — copy constructor not defined
(C) `d2` will not have any data
(D) More than one of the above
(E) None of the above

---

**Q17. [LEVEL: Hard]** When a class C inherits from B which inherits from A, and an object of C is created:

(A) Only C's constructor is called
(B) A → B → C (constructors in this order)
(C) C → B → A (constructors in this order)
(D) More than one of the above
(E) None of the above

---

**Q18. [LEVEL: Hard]** An object `obj` is created inside a function. When does its destructor get called?

(A) When `delete obj` is explicitly called
(B) When the function returns (object goes out of scope)
(C) At the end of the program
(D) More than one of the above
(E) None of the above

---

**Q19. [LEVEL: PYQ-Style]** Which of the following is TRUE about constructors?

(A) A constructor can be overloaded
(B) A constructor does not have a return type
(C) A constructor is called automatically when an object is created
(D) More than one of the above — A, B, and C are all correct
(E) None of the above

---

**Q20. [LEVEL: PYQ-Style]** Which of the following statements is NOT true about destructors?

(A) A destructor has the same name as the class preceded by `~`
(B) A destructor can be overloaded
(C) A destructor takes no parameters
(D) More than one of the above
(E) None of the above

---

**Q21. [LEVEL: PYQ-Style]** What is the output when the following code executes?
```cpp
class A {
public:
    A() { cout << 1; }
    ~A() { cout << 2; }
};
int main() {
    A a1, a2, a3;
    return 0;
}
```

(A) 123321
(B) 111222
(C) 123123
(D) More than one of the above
(E) None of the above

---

**Q22. [LEVEL: PYQ-Style]** Which of the following is the correct way to write a copy constructor for class `Box`?

(A) `Box(Box obj)`
(B) `Box(Box* obj)`
(C) `Box(const Box& obj)`
(D) More than one of the above — both A and C
(E) None of the above

---

**Q23. [LEVEL: PYQ-Style]** What is the difference between Shallow Copy and Deep Copy?

(A) Shallow copy copies only pointer addresses; Deep copy duplicates the actual data
(B) Shallow copy is done by user; Deep copy is done by compiler
(C) There is no difference
(D) More than one of the above
(E) None of the above

---

**Q24. [LEVEL: Tricky]** If a class has a `virtual` destructor, what does it imply?

(A) The destructor can be called multiple times
(B) When deleting a derived object through a base pointer, the correct destructor is called
(C) The derived class cannot define its own destructor
(D) More than one of the above
(E) None of the above

---

**Q25. [LEVEL: Tricky]** Which of the following features does a constructor share with a regular member function?

(A) Return type
(B) It can be called explicitly with the object name
(C) It can be overloaded
(D) More than one of the above — both B and C
(E) None of the above

---

---

## 📘 GENERAL STUDIES (GS + GK) — 25 MCQs
### (LCM/HCF + Modern Indian History + Bihar GK — All Levels)

---

**Q26. [LEVEL: Easy — Maths]** The HCF of 12 and 30 is:

(A) 2
(B) 6
(C) 12
(D) More than one of the above
(E) None of the above

---

**Q27. [LEVEL: Easy — Maths]** The LCM of 4 and 6 is:

(A) 2
(B) 12
(C) 24
(D) More than one of the above
(E) None of the above

---

**Q28. [LEVEL: Easy — Maths]** HCF × LCM of two numbers equals:

(A) Sum of the two numbers
(B) Difference of the two numbers
(C) Product of the two numbers
(D) More than one of the above
(E) None of the above

---

**Q29. [LEVEL: Easy — GK]** The Champaran Satyagraha of 1917 is historically significant because:

(A) It was Mahatma Gandhi's first satyagraha in India
(B) It was the first civil disobedience movement in India
(C) It involved the indigo farmers of Bihar
(D) More than one of the above — all three are correct
(E) None of the above

---

**Q30. [LEVEL: Easy — GK]** Who was the first President of the Indian National Congress?

(A) Mahatma Gandhi
(B) Dadabhai Naoroji
(C) W.C. Bonnerjee
(D) More than one of the above
(E) None of the above

---

**Q31. [LEVEL: Medium — Maths]** Two numbers have HCF = 9 and LCM = 54. If one number is 27, what is the other?

(A) 9
(B) 18
(C) 27
(D) More than one of the above
(E) None of the above

---

**Q32. [LEVEL: Medium — Maths]** Find the LCM of 2/3, 4/9, and 5/6.

(A) 20/3
(B) 10/3
(C) 20/9
(D) More than one of the above
(E) None of the above

---

**Q33. [LEVEL: Medium — Maths]** What is the greatest number that exactly divides 24, 36, and 60?

(A) 4
(B) 6
(C) 12
(D) More than one of the above
(E) None of the above

---

**Q34. [LEVEL: Medium — Maths]** The greatest number which divides 25, 37, and 55 leaving a remainder of 1 in each case is:

(A) 4
(B) 6
(C) 12
(D) More than one of the above
(E) None of the above

---

**Q35. [LEVEL: Medium — Maths]** Three bells ring at intervals of 12, 15, and 18 minutes respectively. They ring together at 9 AM. When will they next ring together?

(A) 10:00 AM
(B) 10:30 AM
(C) 10:00 AM — after 60 minutes
(D) More than one of the above
(E) None of the above

---

**Q36. [LEVEL: Medium — GK]** The Ghadar Party was established in:

(A) London, England
(B) Berlin, Germany
(C) San Francisco, USA
(D) More than one of the above
(E) None of the above

---

**Q37. [LEVEL: Medium — GK]** Who founded Abhinav Bharat in London?

(A) Bal Gangadhar Tilak
(B) Bipin Chandra Pal
(C) V.D. Savarkar
(D) More than one of the above
(E) None of the above

---

**Q38. [LEVEL: Medium — GK]** The Bardoli Satyagraha (1928) was led by:

(A) Mahatma Gandhi
(B) Jawaharlal Nehru
(C) Sardar Vallabhbhai Patel
(D) More than one of the above
(E) None of the above

---

**Q39. [LEVEL: Medium — GK]** Who presided over the INC session at Gaya in 1922?

(A) Bal Gangadhar Tilak
(B) Chittaranjan Das
(C) Lala Lajpat Rai
(D) More than one of the above
(E) None of the above

---

**Q40. [LEVEL: Medium — Bihar GK]** Which district of Bihar is known for maximum paddy (rice) production?

(A) Patna
(B) Gaya
(C) Rohtas
(D) More than one of the above
(E) None of the above

---

**Q41. [LEVEL: Hard — Maths]** The smallest number which when divided by 5, 6, and 8 leaves a remainder of 3 in each case is:

(A) 123
(B) 243
(C) 483
(D) More than one of the above
(E) None of the above

---

**Q42. [LEVEL: Hard — Maths]** The HCF of two numbers is 11 and their LCM is 7700. If one number is 275, find the other.

(A) 279
(B) 308
(C) 154
(D) More than one of the above
(E) None of the above

---

**Q43. [LEVEL: Hard — Maths]** Find the least number that when divided by 7, 9, and 11 leaves remainders 6, 8, and 10 respectively.

(A) 692
(B) 693
(C) 695
(D) More than one of the above
(E) None of the above

---

**Q44. [LEVEL: Hard — Maths]** HCF of fractions 3/5 and 9/10 is:

(A) 9/10
(B) 3/10
(C) 3/5
(D) More than one of the above
(E) None of the above

---

**Q45. [LEVEL: Hard — GK]** Consider the following statements:
1. The Anushilan Samiti in Patna was founded in 1913 by Sachindra Nath Sanyal
2. Birsa Munda's Commander-in-Chief was Gaya Munda
3. The Bihar Socialist Party was founded by Jayaprakash Narayan and Phulan Prasad Varma

Which are CORRECT?

(A) Only 1
(B) Only 1 and 2
(C) All three — 1, 2, and 3
(D) More than one of the above
(E) None of the above

---

**Q46. [LEVEL: Hard — GK]** The novel "Anandamath" by Bankim Chandra Chattopadhyay refers to which revolt?

(A) Indigo Revolt
(B) Sepoy Mutiny
(C) Sannyasi Revolt
(D) More than one of the above
(E) None of the above

---

**Q47. [LEVEL: PYQ-Style — Maths]** The product of two numbers is 2028 and their HCF is 13. How many such pairs of numbers exist?

(A) 1
(B) 2
(C) 3
(D) More than one of the above
(E) None of the above

---

**Q48. [LEVEL: PYQ-Style — GK]** Bihar's percentage share of India's total population (as per Census 2011) is approximately:

(A) 5.58%
(B) 8.58%
(C) 11.58%
(D) More than one of the above
(E) None of the above

---

**Q49. [LEVEL: PYQ-Style — GK]** The Jallianwala Bagh massacre (1919) occurred during the viceroyalty of:

(A) Lord Curzon
(B) Lord Mountbatten
(C) Lord Chelmsford
(D) More than one of the above
(E) None of the above

---

**Q50. [LEVEL: Tricky — GK]** Which of the following was NOT a feature of the Home Rule Movement?

(A) It demanded self-governance within the British Empire
(B) It was led by Annie Besant and Bal Gangadhar Tilak
(C) Sarojini Naidu was one of its principal leaders
(D) More than one of the above
(E) None of the above

---

---

# ═══════════════════════════════════════════
# ✅ ANSWER KEY
# (Check only AFTER solving all 50 questions)
# ═══════════════════════════════════════════

---

## CS ANSWERS (Q1–Q25)

| Q# | Answer | Topic | Key Explanation |
|----|--------|-------|----------------|
| Q1 | **(C)** | Constructor basics | Constructor has NO return type (A wrong), CANNOT be virtual (B wrong); only (C) is correct |
| Q2 | **(B)** | Destructor | Only ONE destructor per class — cannot be overloaded |
| Q3 | **(C)** | Destructor syntax | Correct syntax: `~Car()` — no return type, tilde prefix, no parameters |
| Q4 | **(B)** | Default constructor | Default constructor = no parameters (or all have defaults). It doesn't guarantee zeroing variables |
| Q5 | **(C)** | Compiler-provided constructor | If NO constructor defined, compiler auto-generates a default one |
| Q6 | **(C)** | Constructor/Destructor order | Base constructor first (A), then Derived (B); destruction is reverse: ~B first, then ~A |
| Q7 | **(B)** | Copy constructor | Copy constructor takes `const ClassName& obj` — a REFERENCE, not a pointer or value |
| Q8 | **(D)** | Copy constructor triggers | Both `Student s2(s1)` and `Student s2 = s1` (when s2 is NEW) call copy constructor |
| Q9 | **(B)** | Constructor restrictions | Constructors CANNOT be virtual. They CAN be overloaded (A ok) and use default args (C ok) |
| Q10 | **(B)** | Const member initialization | `const` members MUST use initializer list — cannot assign in constructor body |
| Q11 | **(B)** | Default copy constructor | Compiler-provided copy constructor does SHALLOW copy (copies pointer values, not pointed data) |
| Q12 | **(D)** | Virtual destructor | A destructor CAN be virtual (A), and virtual destructor ensures proper cleanup (B) — both correct. Constructor CANNOT be virtual (C wrong) |
| Q13 | **(B)** | Non-virtual destructor problem | Without virtual destructor, derived destructor is skipped → memory leak and undefined behavior |
| Q14 | **(C)** | Multilevel inheritance output | Constructors: X→Y→Z (base to derived); Destructors: ~Z→~Y→~X (reverse) |
| Q15 | **(C)** | Copy constructor misconception | When assigning to an EXISTING object (`s2 = s1` where s2 exists), the ASSIGNMENT OPERATOR is called, NOT copy constructor |
| Q16 | **(A)** | Shallow copy danger | Default copy constructor does shallow copy → both `d1.data` and `d2.data` point to same memory → double-free when both destructors run |
| Q17 | **(B)** | Constructor order in multilevel | A → B → C (base class first, derived class last) |
| Q18 | **(B)** | Automatic destructor | Local objects' destructors are called when the function returns (object goes out of scope) |
| Q19 | **(D)** | Constructor features | ALL three: overloaded (A), no return type (B), automatic call (C) — hence D is correct |
| Q20 | **(B)** | Destructor facts | Destructors CANNOT be overloaded — they take no parameters. A destructor is always unique |
| Q21 | **(A)** | Output prediction | 3 constructors called (1,1,1 → prints "111"); then destructors LIFO: a3→a2→a1 (prints "222"). But each constructor prints number of object… wait — class A always prints "1" in constructor and "2" in destructor. So: constructor called 3 times → "111"; destructors in LIFO → "222". Output = "111222". **Correction: Answer is (B) — 111222** |
| Q22 | **(C)** | Copy constructor syntax | Correct syntax: `Box(const Box& obj)` — pass by REFERENCE. Passing by value would cause infinite recursion |
| Q23 | **(A)** | Shallow vs Deep copy | Shallow = copies pointer (address); Deep = duplicates the actual data with new allocation |
| Q24 | **(B)** | Virtual destructor purpose | Virtual destructor ensures correct destructor is called when deleting via base pointer |
| Q25 | **(C)** | Constructor vs regular function | Constructor CAN be overloaded (like regular functions). It CANNOT be called with dot notation normally, and has NO return type |

**⚠️ Correction for Q21:** Class A's constructor outputs "1" and destructor outputs "2". Three objects are created sequentially (three "1"s), then destroyed in LIFO (three "2"s). Output = **111222** → **Answer: (B)**

---

## GS/GK ANSWERS (Q26–Q50)

| Q# | Answer | Topic | Key Explanation |
|----|--------|-------|----------------|
| Q26 | **(B)** | HCF | 12 = 2²×3; 30 = 2×3×5; HCF = 2×3 = **6** |
| Q27 | **(B)** | LCM | LCM(4,6): 4=2², 6=2×3; LCM = 2²×3 = **12** |
| Q28 | **(C)** | HCF×LCM formula | HCF × LCM = Product of the two numbers (for 2 numbers) |
| Q29 | **(D)** | Champaran 1917 | All three statements are correct — first satyagraha in India, first civil disobedience, involved indigo farmers |
| Q30 | **(C)** | INC first president | W.C. Bonnerjee was the first president of INC at its first session in 1885 in Bombay |
| Q31 | **(B)** | HCF × LCM application | Other = (HCF × LCM) / Known = (9 × 54) / 27 = 486/27 = **18** |
| Q32 | **(A)** | LCM of fractions | LCM of fractions = LCM(numerators)/HCF(denominators) = LCM(2,4,5)/HCF(3,9,6) = 20/1 = **20/3** |
| Q33 | **(C)** | HCF application | HCF(24,36,60): 24=2³×3, 36=2²×3², 60=2²×3×5; HCF=2²×3=**12** |
| Q34 | **(B)** | HCF with remainder | Numbers after subtracting remainder: 24,36,54; HCF(24,36,54)=**6** |
| Q35 | **(E)** | LCM bell problem | LCM(12,15,18): 12=2²×3, 15=3×5, 18=2×3²; LCM=2²×3²×5=180 min = 3 hours. Next ring at 12:00 PM (noon), not 10:00 or 10:30. None of options A/B/C is correct → **(E)** |
| Q36 | **(C)** | Ghadar Party | Ghadar Party founded in San Francisco, USA in 1913 |
| Q37 | **(C)** | Abhinav Bharat | Founded by V.D. Savarkar in London |
| Q38 | **(C)** | Bardoli Satyagraha | Led by Sardar Vallabhbhai Patel in 1928 |
| Q39 | **(B)** | INC Gaya session | INC Gaya session 1922 presided by Chittaranjan Das |
| Q40 | **(C)** | Bihar agriculture | Rohtas district has maximum paddy production in Bihar |
| Q41 | **(A)** | LCM with remainder | LCM(5,6,8)=120; Answer = 120+3=123 |
| Q42 | **(B)** | HCF × LCM application | Other = (11 × 7700) / 275 = 84700/275 = **308** |
| Q43 | **(A)** | LCM with different remainders | 7-6=1, 9-8=1, 11-10=1; difference=1; LCM(7,9,11)=693; Answer=693-1=**692** |
| Q44 | **(B)** | HCF of fractions | HCF(3/5, 9/10) = HCF(3,9)/LCM(5,10) = 3/10 |
| Q45 | **(C)** | Bihar freedom struggle | All three statements are historically correct |
| Q46 | **(C)** | Anandamath | Anandamath by Bankim Chandra refers to the Sannyasi Revolt of Bengal |
| Q47 | **(B)** | HCF product pair | 2028 = 13 × 156; Find co-prime pairs: 1×156, 4×39, 12×13 (but check HCF). Co-prime pairs multiplying to 2028/13=156: (1,156) and (4,39). Both have HCF=13 with each other × 13. Answer = **2 pairs** |
| Q48 | **(B)** | Bihar census | Bihar's population is 8.58% of India's total (Census 2011) |
| Q49 | **(C)** | Jallianwala Bagh | Viceroy during 1919 Jallianwala Bagh massacre was Lord Chelmsford |
| Q50 | **(C)** | Home Rule Movement | Sarojini Naidu was NOT a principal leader of Home Rule Movement — it was Annie Besant and Tilak |

---

---

# 📝 DAY 6 — NIGHT REVISION SUMMARY
## Write these 10 points from memory before sleeping

```
CONSTRUCTORS:
1. Constructor: same name as class, NO return type, called automatically
2. Types: Default (no args), Parameterized (with args), Copy (object ref as arg)
3. Copy constructor vs Assignment: NEW object = Copy constructor; EXISTING object = Assignment operator
4. const members MUST be initialized via initializer list
5. Default copy constructor = SHALLOW copy (dangerous for pointer members)

DESTRUCTORS:
6. Destructor: ~ClassName(), no params, no return type, ONLY ONE per class
7. Destructor CAN be virtual (unlike constructor); SHOULD be virtual in base classes
8. Constructor order: Base → Derived; Destructor order: Derived → Base (LIFO)

LCM & HCF:
9. HCF = common factors × lowest powers; LCM = all factors × highest powers
10. HCF × LCM = Product of two numbers; HCF of fractions = HCF(N)/LCM(D)
```

---

## ⏰ TODAY'S TIME PLAN:
| Slot | Duration | Activity |
|------|----------|---------|
| Morning | 1.5 hrs | Read CS Part 1 + 2 (Constructors & Destructors) |
| Afternoon | 1 hr | Read GS Part 2 + GK Part 3 (LCM/HCF + History) |
| Evening | 1 hr | Solve all 50 MCQs (without peeking at answers!) |
| Night | 30 min | Check answers → Review mistakes → Write Night Summary |

---

## 🏆 TOPPER TARGETS FOR TODAY:
- Score **20+/25** in CS MCQs
- Score **20+/25** in GS/GK MCQs
- Note down every question you got wrong — these are your weak points
- If you scored < 18 in CS: Re-read Sections 1.6 and 1.7 (virtual destructor + order)
- If you scored < 18 in GS: Re-read LCM with different remainders (Section 2.5)

---

*Day 6 Complete | Next: Day 7 — REVISION DAY for all OOP Week 1 + PYQ Mock Test*
*Phase 1, Week 1 | Total PYQs solved by Day 6: 50+ | Stay consistent! 🎯*
