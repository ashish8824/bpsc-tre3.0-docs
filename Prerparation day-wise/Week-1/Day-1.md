# 📅 DAY 1 — OOP Fundamentals: What, Why & The 4 Pillars
### BPSC TRE 4.0 | Computer Science Teacher (Class 11–12)
**Phase 1 | Week 1 | CS Topic: OOP Basics | GS Topic: Maths — Percentage Basics**

---

> 🎯 **Day 1 Goal:** Understand OOP from scratch — deeply enough that ANY question from this topic in the exam becomes easy. By the end of today, you will know every concept, every trap question, and every PYQ pattern related to OOP fundamentals.

---

## ⏱️ TODAY'S SCHEDULE

| Time Slot | Duration | Activity |
|-----------|----------|----------|
| Morning | 1.5 hrs | This entire CS document (read + understand) |
| Afternoon | 1 hr | GS: Percentage, Profit & Loss basics |
| Evening | 1 hr | Solve the 25 PYQ Practice Questions at the end |
| Night | 30 min | Write 5 bullet points from memory in your notebook |

---

# PART 1: THE FOUNDATION — WHAT IS OOP?

## 1.1 Procedural Programming vs Object-Oriented Programming

Before understanding OOP, you must understand WHY it was invented. Let's compare:

### Procedural Programming (The Old Way)
- Programs are written as a sequence of instructions (procedures/functions)
- Data and functions are **separate** — data flows from function to function
- Language examples: C, Pascal, COBOL, FORTRAN

**Real-world analogy:** Imagine a factory where:
- Raw materials (data) are kept in a separate warehouse
- Workers (functions) fetch materials, process them, and return them
- Anyone can access the warehouse — no security!

**Problems with procedural approach:**
1. Data is openly accessible — security risk
2. As programs grow, it becomes hard to manage
3. Code reuse is difficult
4. Changes in data structure break many functions

### Object-Oriented Programming (The Modern Way)
- Program is modeled as a collection of **objects**
- Each object contains BOTH data AND the functions that operate on it
- Data is hidden inside objects — can only be accessed through defined methods
- Language examples: C++, Java, Python, C#

**Real-world analogy:** Imagine objects like a **car**:
- A car has attributes (color, speed, fuel) → these are **data**
- A car has behaviors (start, stop, accelerate) → these are **methods/functions**
- You (the user) don't need to know HOW the engine works — you just press the accelerator

---

## 1.2 Key Terminology: Class and Object

### CLASS — The Blueprint
- A **class** is a template or blueprint that defines what an object will look like and how it will behave
- It defines the **structure** (attributes) and **behavior** (methods)
- A class by itself does NOT occupy memory (except for static members)

```cpp
// Example of a Class in C++
class Student {
    // Data members (attributes)
    int rollNumber;
    string name;
    float marks;

    // Member functions (behavior)
    void display() {
        cout << "Name: " << name << ", Marks: " << marks;
    }
};
```

### OBJECT — The Instance
- An **object** is a specific **instance** of a class
- When you create an object, memory is allocated
- Many objects can be created from the same class — each has its own data

```cpp
// Creating objects from the Student class
Student s1;   // Object 1 — has its own rollNumber, name, marks
Student s2;   // Object 2 — separate data from s1
Student s3;   // Object 3
```

**Real-world example:**
- **Class** = Architectural blueprint of a house
- **Object** = The actual house built from that blueprint
- You can build 100 houses (objects) from 1 blueprint (class), each with different paint colors, furniture, etc.

### Instance Variables vs Class Variables

| Feature | Instance Variable | Class Variable (Static) |
|---------|------------------|------------------------|
| Memory | Each object gets its own copy | ONE copy shared by ALL objects |
| Declaration | Without `static` keyword | With `static` keyword |
| Access | Through object | Through class name |
| Example | `int rollNumber;` | `static int totalStudents;` |

```cpp
class Student {
    int rollNumber;         // Instance variable — each student has own roll number
    static int totalCount;  // Class variable — one count for ALL students
};
```

**Key Exam Fact:** Static variables belong to the CLASS, not to any specific object.

---

# PART 2: THE 4 PILLARS OF OOP

This is the MOST important section for BPSC TRE. These 4 pillars appear in EVERY paper. Memorize them with deep understanding.

```
┌─────────────────────────────────────────────────────┐
│              THE 4 PILLARS OF OOP                   │
│                                                     │
│  1. ENCAPSULATION  →  Data Hiding + Binding         │
│  2. ABSTRACTION    →  Hide Implementation           │
│  3. INHERITANCE    →  Code Reusability (IS-A)       │
│  4. POLYMORPHISM   →  Many Forms                    │
└─────────────────────────────────────────────────────┘
```

---

## PILLAR 1: ENCAPSULATION — Wrapping Data + Methods Together

### What is Encapsulation?
Encapsulation means **wrapping data (variables) and the methods (functions) that operate on that data together into a single unit called a class.**

It also involves **restricting direct access** to some of an object's components — this is called **data hiding**.

### Real-World Analogy
Think of a **medicine capsule**:
- Inside the capsule: medicine (data)
- The capsule itself: controls HOW the medicine enters your body (methods)
- You don't directly touch the medicine — you go through the capsule

Or think of your **bank account**:
- Your balance is hidden (private data)
- You can only access it through defined methods: deposit(), withdraw(), checkBalance()
- The bank doesn't let you directly modify the balance variable!

### Access Specifiers — The Tools of Encapsulation

| Access Specifier | Within Class | Within Package/Derived Class | Outside Class |
|-----------------|--------------|------------------------------|---------------|
| **private** | ✅ YES | ❌ NO | ❌ NO |
| **protected** | ✅ YES | ✅ YES | ❌ NO |
| **public** | ✅ YES | ✅ YES | ✅ YES |

```cpp
class BankAccount {
private:
    double balance;      // Hidden from outside — only accessible within class
    string password;

protected:
    string accountNumber;  // Accessible in derived classes (like SavingsAccount)

public:
    void deposit(double amount) {      // Accessible to everyone
        balance += amount;
    }

    double getBalance() {              // Controlled access to private data
        return balance;
    }
};

// OUTSIDE the class:
BankAccount myAccount;
myAccount.balance = 1000000;  // ❌ ERROR! balance is private
myAccount.deposit(1000);      // ✅ Works! deposit() is public
```

### Benefits of Encapsulation
1. **Data Security** — Private data cannot be directly modified
2. **Control** — You decide HOW data is accessed and modified
3. **Maintainability** — Change internal implementation without affecting external code
4. **Flexibility** — Add validation inside setter methods

**PYQ Trap:** Encapsulation = Data Hiding + Binding of data and functions. Don't confuse it with Abstraction.

---

## PILLAR 2: ABSTRACTION — Hiding Complexity

### What is Abstraction?
Abstraction means **showing only the ESSENTIAL features** to the user and **hiding the internal implementation details**.

- **Show WHAT an object does, not HOW it does it**
- Focus on the interface, hide the implementation

### Real-World Analogy
Think of a **TV remote**:
- You press "Volume Up" → the TV volume increases
- Do you know HOW the remote sends infrared signals? How the TV decodes them? NO!
- You only see the interface (buttons) — implementation is hidden

Or think of **driving a car**:
- You press the accelerator → car moves faster
- You don't know about fuel injection, combustion cycles, etc.
- The complexity is abstracted away from you

### Abstraction vs Encapsulation — The Critical Difference

| Feature | Encapsulation | Abstraction |
|---------|--------------|-------------|
| Purpose | Hiding DATA from direct access | Hiding IMPLEMENTATION complexity |
| Focus | HOW data is protected | WHAT interface is exposed |
| Implementation | Access specifiers (private, public) | Abstract classes, Interfaces |
| Real example | Private variables with getters/setters | Remote control buttons |

> **Memory trick:** 
> - **En**capsulation = **En**closing (wrapping) data + methods together
> - **Ab**straction = **Ab**stracting away (hiding) complexity

### Abstract Class in C++
- An abstract class has at least **one pure virtual function**
- It CANNOT be instantiated (you cannot create objects of an abstract class)
- It serves as a blueprint for derived classes

```cpp
// Abstract class — has at least one pure virtual function
class Shape {
public:
    virtual double area() = 0;    // Pure virtual function — "= 0" makes it pure
    virtual void draw() = 0;      // Pure virtual function

    void display() {              // Regular function — can have implementation
        cout << "This is a shape";
    }
};

// Concrete class — implements all pure virtual functions
class Circle : public Shape {
    double radius;
public:
    double area() {               // Must implement all pure virtual functions
        return 3.14 * radius * radius;
    }
    void draw() {
        cout << "Drawing circle";
    }
};

// Shape s;      ❌ ERROR! Cannot instantiate abstract class
Circle c;        // ✅ Works! Circle is concrete (all pure virtuals implemented)
```

**Key PYQ Facts:**
1. Abstract class = at least ONE pure virtual function
2. A class with ALL pure virtual functions = **Interface** (in concept)
3. Pure virtual function syntax: `virtual returnType funcName() = 0;`
4. Abstract class CANNOT be instantiated

---

## PILLAR 3: INHERITANCE — Code Reusability

### What is Inheritance?
Inheritance allows a class (derived/child) to **inherit properties and behaviors** from another class (base/parent). It models the **IS-A relationship**.

- Promotes **code reusability** — don't rewrite what already exists
- Child class inherits all public and protected members of parent class

### Real-World Analogy
Think of a biological family:
- Parent has properties: eyes, hands, DNA
- Child INHERITS these properties automatically
- Child can also have its OWN additional properties: skills, hobbies

Or in software:
- Vehicle class: has speed, fuel, move()
- Car IS-A Vehicle → inherits speed, fuel, move()
- Car also has its own: numberOfDoors, airConditioning()

### Types of Inheritance

```
1. SINGLE INHERITANCE
   A → B
   (B inherits from A only)

2. MULTIPLE INHERITANCE (C++ supports, Java doesn't)
   A   B
    ↘ ↙
     C
   (C inherits from both A and B)

3. MULTILEVEL INHERITANCE
   A → B → C
   (C inherits from B, which inherits from A)

4. HIERARCHICAL INHERITANCE
       A
      ↙ ↘
     B   C
   (Both B and C inherit from A)

5. HYBRID INHERITANCE (Combination of above types)
```

### Inheritance Syntax

**C++ Syntax:**
```cpp
class Base {
public:
    void baseMethod() {
        cout << "Base method";
    }
};

class Derived : public Base {     // ":" with access specifier
    // Inherits baseMethod()
};

// Access specifier in inheritance:
class D1 : public Base   { };   // public members remain public in D1
class D2 : private Base  { };   // public members become private in D2
class D3 : protected Base{ };   // public members become protected in D3
```

**Java Syntax:**
```java
class Base {
    void baseMethod() {
        System.out.println("Base method");
    }
}

class Derived extends Base {     // "extends" keyword in Java
    // Inherits baseMethod()
}
```

**Key PYQ Fact:** C++ uses `:` (colon), Java uses `extends`. This is frequently tested!

### What IS and IS NOT Inherited

| Inherited | NOT Inherited |
|-----------|--------------|
| Public methods | Constructors |
| Protected methods | Destructors |
| Public variables | Private members (they exist but are inaccessible) |
| Protected variables | Friend functions |

### The Diamond Problem (Important for PYQ!)

```
        A
       ↙ ↘
      B   C
       ↘ ↙
        D
```

When class D inherits from both B and C, and both inherit from A → D gets **TWO copies of A**. This is ambiguous!

**Solution:** Virtual Inheritance

```cpp
class A {
public:
    int data;
};

class B : virtual public A { };   // virtual keyword
class C : virtual public A { };   // virtual keyword

class D : public B, public C {    // D gets only ONE copy of A
};
```

**Key PYQ Fact:** Virtual inheritance solves the diamond problem. `virtual` keyword is used in BASE classes (B and C), not in D.

---

## PILLAR 4: POLYMORPHISM — Many Forms

### What is Polymorphism?
Polymorphism means **"many forms"** — the ability of an object to take different forms or for a function to behave differently in different contexts.

**Greek:** Poly (many) + Morph (form)

### Types of Polymorphism

```
POLYMORPHISM
     │
     ├── Compile-time (Static) Polymorphism
     │        ├── Method Overloading
     │        └── Operator Overloading
     │
     └── Runtime (Dynamic) Polymorphism
              └── Method Overriding (via Virtual Functions)
```

### Type 1: Compile-Time Polymorphism (Static Binding)

The decision of WHICH function to call is made at **compile time**.

#### Method Overloading
Same function name, different parameter lists:

```cpp
class Calculator {
public:
    int add(int a, int b) {           // Version 1: two integers
        return a + b;
    }

    double add(double a, double b) {   // Version 2: two doubles
        return a + b;
    }

    int add(int a, int b, int c) {    // Version 3: three integers
        return a + b + c;
    }
};

Calculator calc;
calc.add(2, 3);         // Calls version 1 → 5
calc.add(2.5, 3.5);     // Calls version 2 → 6.0
calc.add(1, 2, 3);      // Calls version 3 → 6
```

**Rules for overloading:** Functions must differ in:
1. Number of parameters, OR
2. Type of parameters, OR
3. Order of parameters

**Cannot overload** based only on return type!

#### Operator Overloading
Define how operators work for user-defined types:

```cpp
class Point {
    int x, y;
public:
    Point(int x, int y) : x(x), y(y) {}

    Point operator+(Point p) {        // Overloading the + operator
        return Point(x + p.x, y + p.y);
    }
};

Point p1(1, 2), p2(3, 4);
Point p3 = p1 + p2;   // Uses our overloaded + operator → (4, 6)
```

### Type 2: Runtime Polymorphism (Dynamic Binding)

The decision of WHICH function to call is made at **runtime**. Achieved through **virtual functions**.

#### Method Overriding
Child class provides its own implementation of a method already in parent class:

```cpp
class Animal {
public:
    virtual void sound() {            // virtual keyword enables runtime polymorphism
        cout << "Some generic sound";
    }
};

class Dog : public Animal {
public:
    void sound() {                    // Overrides parent's sound()
        cout << "Woof!";
    }
};

class Cat : public Animal {
public:
    void sound() {                    // Overrides parent's sound()
        cout << "Meow!";
    }
};

// Runtime Polymorphism in action:
Animal* ptr;
Dog d;
Cat c;

ptr = &d;
ptr->sound();    // Calls Dog's sound() → "Woof!" (decided at runtime!)

ptr = &c;
ptr->sound();    // Calls Cat's sound() → "Meow!" (decided at runtime!)
```

**HOW does runtime polymorphism work internally?**
- When a class has virtual functions, the compiler creates a **vtable** (Virtual Table)
- Each object has a hidden pointer called **vptr** (Virtual Pointer) pointing to the vtable
- At runtime, the correct function is located via vtable lookup

### Overloading vs Overriding — The Critical Difference

| Feature | Overloading | Overriding |
|---------|-------------|------------|
| Type | Compile-time polymorphism | Runtime polymorphism |
| Occurrence | SAME class, same name, different parameters | PARENT-CHILD classes, same name, same parameters |
| Binding | Static (early) binding | Dynamic (late) binding |
| `virtual` needed | NO | YES (in parent) |
| Inheritance | NOT required | REQUIRED |

**Key PYQ Exam Trick:**
- **Compile-time** = Overloading = Static binding = Early binding
- **Runtime** = Overriding = Dynamic binding = Late binding = **requires virtual functions**

---

# PART 3: WHY OOP? — Benefits

| Benefit | Explanation |
|---------|-------------|
| **Reusability** | Inheritance allows reusing code — write once, use many times |
| **Modularity** | Code divided into objects — easier to understand and manage |
| **Data Security** | Encapsulation protects data from unauthorized access |
| **Maintainability** | Changes to one object don't break others |
| **Flexibility** | Polymorphism allows same interface for different types |
| **Scalability** | Easy to add new objects without changing existing code |

---

# PART 4: PURE OOP LANGUAGES

A **pure OOP language** requires that EVERYTHING be an object and the language must support all 4 pillars.

**Examples of pure OOP:** Smalltalk, Ruby (debated)

**NOT pure OOP:**
- **C++** — not pure OOP (has primitive data types outside classes, global functions)
- **Java** — not fully pure (has primitive types like int, char outside classes)
- **Python** — mostly OOP but allows non-OOP style

**Key PYQ question format:** "Which is NOT a feature of pure OOP?" → The answer usually points to something that violates one of the 4 pillars or allows non-OOP constructs.

---

# PART 5: CONSTRUCTORS & DESTRUCTORS (Preview)

Since constructors are often tested with OOP basics:

### Constructors
- Special method with **same name as class**
- **No return type** (not even void)
- Automatically called when object is created
- Purpose: Initialize the object

```cpp
class Student {
    int rollNo;
    string name;
public:
    Student() {                         // Default constructor
        rollNo = 0;
        name = "Unknown";
    }

    Student(int r, string n) {          // Parameterized constructor
        rollNo = r;
        name = n;
    }

    Student(Student& s) {               // Copy constructor
        rollNo = s.rollNo;
        name = s.name;
    }
};

Student s1;             // Calls default constructor
Student s2(101, "Ram"); // Calls parameterized constructor
Student s3(s2);         // Calls copy constructor
```

### Destructors
- Same name as class but prefixed with **~** (tilde)
- No parameters, no return type
- **Only ONE destructor** per class (cannot be overloaded)
- Automatically called when object goes out of scope or `delete` is used

```cpp
class Student {
public:
    ~Student() {    // Destructor
        cout << "Student object destroyed";
    }
};
```

**Order of calls in inheritance:**
- Constructor: Parent first → then Child
- Destructor: Child first → then Parent (REVERSE order)

---

# PART 6: QUICK REVISION — KEY FACTS TABLE

| Concept | Key Fact to Remember |
|---------|---------------------|
| OOP vs Procedural | OOP combines data + functions; Procedural keeps them separate |
| Class | Blueprint — no memory (except static) |
| Object | Instance — has memory |
| Encapsulation | Data hiding + wrapping data & methods in class |
| Abstraction | Hiding implementation, showing interface |
| Abstract class | At least ONE pure virtual function; cannot instantiate |
| Pure virtual function | `virtual void func() = 0;` |
| Inheritance | IS-A relationship; code reusability |
| C++ inheritance | Uses `:` (colon) |
| Java inheritance | Uses `extends` |
| Diamond problem | Solved by virtual inheritance |
| Polymorphism | Compile-time (overloading) + Runtime (overriding) |
| Runtime polymorphism | Requires `virtual` keyword |
| Constructor | Same name as class, no return type, called on object creation |
| Destructor | `~ClassName()`, only ONE, called on object destruction |
| struct vs class (C++) | struct default = PUBLIC; class default = PRIVATE |

---

# PART 7: CONCEPTUAL TRAPS — DON'T FALL FOR THESE!

These are actual exam traps from PYQ analysis. Read each one carefully:

### Trap 1: "Abstraction and Encapsulation are the same thing"
❌ WRONG! They are different:
- Encapsulation = WRAPPING data + methods together (implementation level)
- Abstraction = HIDING complexity from user (design level)

### Trap 2: "Only NAND is a universal gate"
(This will come in Digital Electronics — remember: BOTH NAND and NOR are universal)

### Trap 3: "An abstract class cannot have any concrete (implemented) methods"
❌ WRONG! Abstract class CAN have concrete methods. It just must have AT LEAST ONE pure virtual function.

### Trap 4: "Java supports multiple inheritance through classes"
❌ WRONG! Java does NOT support multiple inheritance through classes. Java supports it through **interfaces**.

### Trap 5: "Private members are NOT inherited"
This is a TRICKY one:
- Private members ARE inherited (they exist in the derived class)
- But they are NOT accessible (directly) in the derived class
- They are accessible through the base class's public/protected methods

### Trap 6: "struct and class are completely different in C++"
❌ NOT completely different! In C++, struct and class are ALMOST identical. The only difference:
- **struct** default access = **public**
- **class** default access = **private**

---

# PART 8: GS TOPIC — PERCENTAGE BASICS

*(Quick 20-minute session)*

## Percentage Formulas

| Formula | Expression |
|---------|-----------|
| Percentage | (Part / Whole) × 100 |
| Value from % | (Percentage × Whole) / 100 |
| % increase | [(New - Old) / Old] × 100 |
| % decrease | [(Old - New) / Old] × 100 |

## Quick Examples

**Q:** A student scored 45 out of 60. What is the percentage?
**A:** (45/60) × 100 = **75%**

**Q:** Price increased from ₹200 to ₹250. What is % increase?
**A:** [(250 - 200) / 200] × 100 = (50/200) × 100 = **25%**

**Q:** If 30% of a number is 90, find the number.
**A:** Number = (90 × 100) / 30 = **300**

## Shortcut Tricks

| % | Fraction |
|---|---------|
| 10% | 1/10 |
| 20% | 1/5 |
| 25% | 1/4 |
| 33.33% | 1/3 |
| 50% | 1/2 |
| 75% | 3/4 |

---

# PART 9: 25 PRACTICE QUESTIONS (PYQ Style)

*Attempt all questions before checking answers. Time yourself: 25 minutes maximum.*

---

**Q1.** Which of the following is NOT one of the four fundamental pillars of Object-Oriented Programming?

(A) Encapsulation  
(B) Polymorphism  
(C) Compilation  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** In C++, what is the correct syntax for defining a derived class D that publicly inherits from base class B?

(A) `class D extends B { }`  
(B) `class D inherits public B { }`  
(C) `class D : public B { }`  
(D) `class D implements B { }`  
(E) None of the above  

---

**Q3.** Which access specifier in C++ allows access within the same class AND within derived classes, but NOT from outside?

(A) private  
(B) public  
(C) protected  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** A class that has at least one pure virtual function is called:

(A) Virtual class  
(B) Abstract class  
(C) Interface class  
(D) Template class  
(E) None of the above  

---

**Q5.** The diamond problem in multiple inheritance is solved using:

(A) Multiple inheritance  
(B) Virtual functions  
(C) Virtual inheritance  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** Which of the following correctly defines a pure virtual function in C++?

(A) `virtual void func();`  
(B) `void func() = 0;`  
(C) `virtual void func() = 0;`  
(D) `abstract void func();`  
(E) None of the above  

---

**Q7.** What is the output type/result of the following: You have a pointer to an Animal class (with virtual function `sound()`), and at runtime you assign it to a Dog object. What type of polymorphism is this?

(A) Compile-time polymorphism  
(B) Static polymorphism  
(C) Runtime polymorphism  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** Which of the following represents the IS-A relationship in OOP?

(A) Encapsulation  
(B) Polymorphism  
(C) Inheritance  
(D) Abstraction  
(E) None of the above  

---

**Q9.** In C++, the default access specifier for a class (when not mentioned) is:

(A) public  
(B) protected  
(C) private  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** In C++, the default access specifier for a struct (when not mentioned) is:

(A) public  
(B) protected  
(C) private  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** Which of the following is true about constructors in C++?

(A) A constructor can have a return type of void  
(B) A constructor has the same name as the class  
(C) There can be only one constructor per class  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** Method overloading is an example of:

(A) Runtime polymorphism  
(B) Dynamic binding  
(C) Compile-time polymorphism  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** Which of the following CANNOT be inherited from a base class?

(A) Public member functions  
(B) Protected member variables  
(C) Constructors  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Which of the following types of inheritance is NOT supported by Java (through classes)?

(A) Single inheritance  
(B) Multilevel inheritance  
(C) Multiple inheritance  
(D) Hierarchical inheritance  
(E) None of the above  

---

**Q15.** What is encapsulation in OOP?

(A) The ability of a function to take many forms  
(B) Hiding the implementation from the user  
(C) Wrapping data and methods that operate on data into a single unit  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** In object-oriented programming, "abstraction" means:

(A) Combining data and methods into a single class  
(B) Hiding the internal implementation details and showing only the interface  
(C) Allowing one class to inherit from multiple classes  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** Which of the following is NOT true about abstract classes?

(A) Abstract classes can have constructors  
(B) Abstract classes can have concrete methods  
(C) Objects of abstract classes can be created directly  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** In the context of inheritance, if the order of constructor calls is A → B → C (for multilevel inheritance A→B→C), then the order of destructor calls will be:

(A) A → B → C  
(B) C → B → A  
(C) A → C → B  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** Which of the following keywords is used in Java to inherit from a class?

(A) inherits  
(B) implements  
(C) extends  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** A static variable in a class:

(A) Is created for each object separately  
(B) Is shared among all objects of the class  
(C) Cannot be accessed through any object  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** Which of the following is true about runtime polymorphism in C++?

(A) It is achieved through function overloading  
(B) It requires the `virtual` keyword  
(C) The function to be called is determined at compile time  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** How many destructors can a class have in C++?

(A) As many as needed  
(B) Exactly two (with and without parameters)  
(C) Only one  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** Which type of inheritance causes the diamond problem?

(A) Single inheritance  
(B) Multilevel inheritance  
(C) Multiple inheritance  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** The vtable (virtual table) in C++ is used for:

(A) Storing all member variables of a class  
(B) Implementing runtime polymorphism through virtual functions  
(C) Managing memory allocation for objects  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** Which of the following correctly describes the relationship between a class and its objects?

(A) An object is a blueprint; a class is an instance  
(B) A class is a blueprint; an object is an instance  
(C) Both class and object are the same thing  
(D) More than one of the above  
(E) None of the above  

---

# ANSWER KEY WITH EXPLANATIONS

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | C | Compilation is NOT a pillar. The 4 pillars are Encapsulation, Inheritance, Polymorphism, Abstraction |
| 2 | C | C++ syntax: `class D : public B { }` — uses colon, not extends |
| 3 | C | protected = accessible in same class + derived classes, NOT from outside |
| 4 | B | Abstract class = has at least one pure virtual function |
| 5 | C | Virtual inheritance (using `virtual` keyword in base classes) solves diamond problem |
| 6 | C | Pure virtual: `virtual void func() = 0;` — needs both `virtual` AND `= 0` |
| 7 | C | Pointer decides at runtime which function to call → Runtime polymorphism |
| 8 | C | Inheritance = IS-A relationship (Dog IS-A Animal) |
| 9 | C | class default = private |
| 10 | A | struct default = public (ONLY difference from class in C++) |
| 11 | B | Constructor has same name as class; CAN be overloaded; NO return type (not even void) |
| 12 | C | Overloading = compile-time (static) polymorphism |
| 13 | C | Constructors are NOT inherited; destructors are also NOT inherited |
| 14 | C | Java doesn't support multiple inheritance through classes (uses interfaces instead) |
| 15 | C | Encapsulation = wrapping data + methods together; data hiding is a result |
| 16 | B | Abstraction = hiding implementation, showing only interface |
| 17 | C | Abstract class CANNOT be instantiated directly — this is the NOT true statement |
| 18 | B | Destructors call in REVERSE order: C → B → A |
| 19 | C | Java uses `extends` for class inheritance |
| 20 | B | Static variable = ONE copy shared by ALL objects of the class |
| 21 | B | Runtime polymorphism requires `virtual` keyword; function decided at RUNTIME not compile time |
| 22 | C | Only ONE destructor per class (cannot be overloaded — no parameters) |
| 23 | C | Diamond problem occurs with multiple inheritance when same grandparent is inherited twice |
| 24 | B | vtable enables runtime polymorphism by storing pointers to virtual functions |
| 25 | B | Class = blueprint, Object = instance (real entity created from blueprint) |

---

# NIGHT TASK: Write These 5 Points in Your Notebook

Before sleeping, write these from memory (do NOT look at the document):

1. The 4 pillars of OOP are: ________________, ________________, ________________, ________________
2. Difference between Encapsulation and Abstraction: _____________
3. Abstract class in C++ requires: ________________
4. Pure virtual function syntax: ________________
5. Difference between class and struct default access: ________________

---

# TOMORROW: DAY 2 PREVIEW

**Topic:** Encapsulation & Abstraction (Deep Dive)  
**GS Topic:** Maths — Profit & Loss  
**Come back and say "Day-2" for tomorrow's full session!**

---

> 🏆 **Mentor's Note:** You've completed Day 1! OOP is the most tested topic in BPSC TRE (21% of CS paper). The foundation you built today will help you answer 15-17 questions directly in the exam. Remember: in this exam, Option (D) "More than one" is the answer approximately 20-25% of the time — always consider it before marking. See you on Day 2!

---

*Day 1 | Phase 1 | BPSC TRE 4.0 Preparation | April 2026*  
*Based on PYQ Analysis of TRE 1.0, 2.0, and 3.0 papers*
