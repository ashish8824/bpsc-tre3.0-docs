# 📚 DAY 2 — BPSC TRE 4.0 TOPPER STUDY GUIDE
## CS Topic: Encapsulation & Abstraction | GS Topic: Profit & Loss (Mathematics)
### 🎯 Target: TOP RANK in BPSC TRE 4.0

---

> **Mentor's Message for Day 2:**
> You cleared Bihar STET. Your fundamentals are better than 80% of candidates.
> Today we go DEEP into two CS pillars that appear in EVERY TRE paper.
> Remember: In BPSC TRE, Option (D) = "More than one of the above" is correct ~20–25% of the time.
> So you must know ALL aspects of a topic — not just one fact.

---

## 📋 TODAY'S SCHEDULE

| Time Slot | Activity | Duration |
|-----------|----------|----------|
| Morning | CS — Encapsulation & Abstraction (concepts + examples) | 1.5 hrs |
| Afternoon | GS — Profit & Loss (formulas + tricks + practice) | 1 hr |
| Evening | CS Practice MCQs (PYQ-style) | 1 hr |
| Night | Write 5-bullet revision notes from memory | 30 min |

---

# 🖥️ PART A: COMPUTER SCIENCE
## Topic: Encapsulation & Abstraction
### Weight: Part of OOP unit = ~16 questions in TRE 4.0

---

## 🔷 SECTION 1: ENCAPSULATION

### 1.1 What is Encapsulation? (The Simple Explanation)

Imagine your **mobile phone**. You press the volume button and the volume changes. You do NOT need to know:
- How the speaker circuit works
- What electrical signal is generated
- How the software processes the keypress

You just press the button → result happens. The internal complexity is **hidden** from you. This is encapsulation in real life.

**In programming:**
> Encapsulation = Bundling **data (variables)** and **methods (functions)** that work on the data into a **single unit called a CLASS**, and **restricting direct access** to some components.

### 1.2 Two Components of Encapsulation

```
ENCAPSULATION = DATA HIDING + DATA BINDING
```

| Component | Meaning | Example |
|-----------|---------|---------|
| **Data Hiding** | Restricting access to internal data | Making `salary` variable private |
| **Data Binding** | Wrapping data + functions together | Class contains both variables and methods |

### 1.3 Access Specifiers — The Heart of Encapsulation

This is HIGH-FREQUENCY in BPSC TRE. You MUST know all three perfectly.

```cpp
class BankAccount {
private:           // ← PRIVATE: only accessible within this class
    double balance;
    string accountNo;

protected:         // ← PROTECTED: accessible within class + child classes
    string holderName;

public:            // ← PUBLIC: accessible from anywhere
    void deposit(double amount) {
        balance += amount;   // Can access private member here
    }
    
    double getBalance() {    // Getter method — controlled access
        return balance;
    }
};
```

### 1.4 Access Specifier Rules — MUST MEMORISE

| Access Specifier | Same Class | Child Class | Outside Class |
|-----------------|-----------|-------------|---------------|
| **private** | ✅ YES | ❌ NO | ❌ NO |
| **protected** | ✅ YES | ✅ YES | ❌ NO |
| **public** | ✅ YES | ✅ YES | ✅ YES |

### 1.5 PYQ TRAP: struct vs class Default Access in C++

> **This has appeared in TRE 1.0 and TRE 2.0!**

```cpp
struct Student {
    int roll;    // Default: PUBLIC in struct
    string name; // Default: PUBLIC in struct
};

class Teacher {
    int id;      // Default: PRIVATE in class
    string name; // Default: PRIVATE in class
};
```

**KEY FACT:** The ONLY difference between `struct` and `class` in C++ is the **default access specifier**.
- `struct` → default access = **PUBLIC**
- `class` → default access = **PRIVATE**

### 1.6 Why Encapsulation is Important

Real exam questions ask WHY — so understand the benefits:

1. **Security** — Private data cannot be accidentally changed from outside
2. **Flexibility** — Internal implementation can change without affecting outside code
3. **Reusability** — Well-encapsulated classes can be reused safely
4. **Data Integrity** — Only validated data passes through setter methods

### 1.7 Getters and Setters — The Controlled Access Pattern

```cpp
class Employee {
private:
    int salary;     // Private — cannot be accessed directly

public:
    // GETTER — reads the value safely
    int getSalary() {
        return salary;
    }
    
    // SETTER — validates before setting value
    void setSalary(int s) {
        if (s > 0) {           // Validation!
            salary = s;
        } else {
            cout << "Invalid salary!";
        }
    }
};

int main() {
    Employee e;
    // e.salary = -5000;    ← COMPILE ERROR! Private member
    e.setSalary(50000);     ← OK! Setter validates
    cout << e.getSalary();  ← Prints 50000
}
```

### 1.8 Friend Functions — The Exception to Encapsulation

```cpp
class Box {
private:
    double length;

public:
    Box(double l) : length(l) {}
    
    // Friend function declaration
    friend double getVolume(Box b);
};

// Friend function CAN access private members
double getVolume(Box b) {
    return b.length * b.length * b.length;  // Can access private 'length'
}
```

**KEY FACT:** A `friend` function is NOT a member of the class but CAN access private/protected members.

---

## 🔷 SECTION 2: ABSTRACTION

### 2.1 What is Abstraction? (The Simple Explanation)

When you drive a car:
- You know: steering wheel turns → car turns
- You do NOT know: how the hydraulic steering pump works, gear ratios, fuel injection timing

The car gives you a **simple interface** (steering, pedals) and **hides the complex mechanism**. This is abstraction.

**In programming:**
> Abstraction = **Showing only ESSENTIAL features** to the user and **hiding unnecessary implementation details**.

### 2.2 Encapsulation vs Abstraction — The Most Confusing Difference

This is a **PYQ trap question**. Candidates confuse these two constantly.

| Feature | Encapsulation | Abstraction |
|---------|--------------|-------------|
| **Focus** | HOW to hide data | WHAT to show to user |
| **Level** | Implementation level | Design level |
| **Achieved by** | Access specifiers (private/public) | Abstract classes and interfaces |
| **Purpose** | Data protection | Reducing complexity |
| **Example** | Making `salary` private | Defining `calculatePay()` without implementation |

**Simple Memory Trick:**
- **Encapsulation** = **CAPSULE** = putting things inside a protective capsule (hiding data)
- **Abstraction** = **Abstract Art** = showing only the essence, hiding details

### 2.3 Abstract Class in C++ — CRITICAL TOPIC

> **This appeared in TRE 2.0 and TRE 3.0. Expect it in TRE 4.0.**

**Definition:** A class that has at least ONE **pure virtual function** is called an **Abstract Class**.

```cpp
class Shape {                        // Abstract class
public:
    virtual double area() = 0;       // ← Pure virtual function (= 0 makes it pure)
    virtual void draw() = 0;         // ← Another pure virtual function
    
    void printInfo() {               // ← Regular (non-pure) method — allowed!
        cout << "This is a shape";
    }
};

class Circle : public Shape {        // Concrete class (inherits from abstract)
public:
    double radius;
    
    double area() override {         // MUST implement pure virtual functions
        return 3.14 * radius * radius;
    }
    
    void draw() override {
        cout << "Drawing circle";
    }
};
```

### 2.4 Rules for Abstract Classes — ALL must be memorised

| Rule | Example |
|------|---------|
| Cannot create an object of abstract class | `Shape s;` → **COMPILE ERROR** |
| Can create pointer/reference of abstract class | `Shape* s = new Circle();` → **VALID** |
| Child class MUST implement all pure virtual functions OR it also becomes abstract | If Circle doesn't implement `area()`, Circle also becomes abstract |
| Abstract class CAN have constructors | Used when child class objects are created |
| Abstract class CAN have regular (non-pure) functions | `printInfo()` above is valid |
| A class with ALL pure virtual functions = **Interface** (conceptually) | Common in Java design |

### 2.5 Pure Virtual Function vs Virtual Function

> **This exact distinction appears in PYQs.**

```cpp
class Animal {
public:
    // VIRTUAL FUNCTION — has a body, can be overridden
    virtual void sound() {
        cout << "Some animal sound";
    }
    
    // PURE VIRTUAL FUNCTION — no body (= 0), MUST be overridden
    virtual void breathe() = 0;
};

class Dog : public Animal {
public:
    void sound() override {     // Optional to override (virtual has default)
        cout << "Woof!";
    }
    
    void breathe() override {   // MANDATORY to override (pure virtual)
        cout << "Dog breathes";
    }
};
```

| Feature | Virtual Function | Pure Virtual Function |
|---------|-----------------|----------------------|
| Syntax | `virtual void func() { }` | `virtual void func() = 0;` |
| Has body? | YES | NO |
| Must be overridden? | No (optional) | YES (mandatory) |
| Makes class abstract? | No | YES |
| Object of class? | Can create | Cannot create |

### 2.6 Interface vs Abstract Class

> **Java concept that appears in BPSC TRE (OOP questions)**

```java
// INTERFACE in Java — all methods are public abstract by default
interface Printable {
    void print();       // Pure abstract by default
    void scan();        // Pure abstract by default
}

// ABSTRACT CLASS in Java — mix of abstract and concrete
abstract class Document {
    abstract void format();      // Must be overridden
    void open() {                // Can be used as-is
        System.out.println("Opening document");
    }
}
```

| Feature | Interface | Abstract Class |
|---------|-----------|----------------|
| Methods | All abstract (Java 7) | Mix of abstract + concrete |
| Variables | Only constants (public static final) | Can have instance variables |
| Multiple inheritance | A class can implement multiple interfaces | Only one abstract class |
| Keyword | `implements` | `extends` |

### 2.7 Real PYQ Scenario — How Questions Are Asked

**PYQ Style Question (TRE 2.0 Pattern):**
"Which of the following statements about abstract class is/are CORRECT?
(A) An abstract class cannot have any method with a body
(B) You can create objects of an abstract class
(C) A class becomes abstract when it has at least one pure virtual function
(D) More than one of the above
(E) None of the above"

**Answer: (C)**
- (A) is WRONG — abstract class CAN have regular methods
- (B) is WRONG — cannot create objects
- (C) is CORRECT ✓

---

## 🔷 SECTION 3: HOW ENCAPSULATION & ABSTRACTION WORK TOGETHER

### Complete Example — ATM Machine

```cpp
// ABSTRACTION: User sees only withdraw(), checkBalance()
// They don't see HOW money is dispensed internally

class ATM {
private:
    // ENCAPSULATION: These details are hidden
    double cashInMachine;
    string atmId;
    bool validatePin(int pin) {   // Internal validation — hidden
        return (pin == 1234);     // Simplified
    }
    
public:
    // ABSTRACTION: Simple interface for the user
    bool withdraw(double amount, int pin) {
        if (!validatePin(pin)) {
            cout << "Wrong PIN!";
            return false;
        }
        if (amount > cashInMachine) {
            cout << "Insufficient cash in ATM";
            return false;
        }
        cashInMachine -= amount;
        cout << "Please collect " << amount;
        return true;
    }
    
    double checkBalance() {
        return cashInMachine;
    }
};
```

**The insight:**
- **Encapsulation** makes `cashInMachine` and `validatePin()` private (data hiding)
- **Abstraction** gives the user only `withdraw()` and `checkBalance()` (complexity hiding)

---

## 🔷 SECTION 4: GS — MATHEMATICS
## Topic: Profit & Loss
### Weight: Appears in EVERY TRE paper — 2-3 questions guaranteed

---

## 💰 PROFIT & LOSS — COMPLETE MASTER GUIDE

### 4.1 Basic Definitions — Learn These First

| Term | Definition | Example |
|------|-----------|---------|
| **Cost Price (CP)** | Price at which item is BOUGHT | You buy a pen for ₹10 |
| **Selling Price (SP)** | Price at which item is SOLD | You sell it for ₹12 |
| **Profit** | When SP > CP | SP - CP = ₹2 profit |
| **Loss** | When CP > SP | CP - SP = Loss |
| **Marked Price (MP)** | Price written on tag/label | Tag says ₹15 |
| **Discount** | Reduction from Marked Price | 20% off on ₹15 = ₹3 off |

### 4.2 THE MASTER FORMULAS — Memorise All

```
PROFIT = SP - CP         (when SP > CP)
LOSS = CP - SP           (when CP > SP)

PROFIT% = (Profit / CP) × 100
LOSS% = (Loss / CP) × 100

SP = CP × (100 + Profit%) / 100    [when profit]
SP = CP × (100 - Loss%) / 100      [when loss]

CP = SP × 100 / (100 + Profit%)    [find CP from SP and profit%]
CP = SP × 100 / (100 - Loss%)      [find CP from SP and loss%]

SP = MP × (100 - Discount%) / 100  [after discount]
```

> **CRITICAL RULE:** Profit% and Loss% are ALWAYS calculated on **COST PRICE**, not Selling Price.
> This is the most common mistake candidates make!

### 4.3 Solved Examples — Step by Step (BPSC TRE Level)

---

**EXAMPLE 1 (Basic):**
A shopkeeper buys a book for ₹120 and sells it for ₹150. Find profit%.

**Solution:**
- CP = ₹120, SP = ₹150
- Profit = SP - CP = 150 - 120 = ₹30
- Profit% = (30/120) × 100 = **25%**

---

**EXAMPLE 2 (Find SP from Profit%):**
A trader bought goods for ₹800 and wants 15% profit. At what price should he sell?

**Solution:**
- CP = ₹800, Profit% = 15%
- SP = CP × (100 + 15) / 100
- SP = 800 × 115 / 100 = **₹920**

---

**EXAMPLE 3 (Find CP from SP and Profit%):**
By selling a chair for ₹1,100, a person gains 10%. What was the cost price?

**Solution:**
- SP = ₹1,100, Profit% = 10%
- CP = SP × 100 / (100 + Profit%)
- CP = 1100 × 100 / 110 = **₹1,000**

---

**EXAMPLE 4 (Two-step: Discount then Profit — TRE 2.0 type):**
A shopkeeper marks an article at ₹500 and gives 10% discount. He still makes 12.5% profit. Find Cost Price.

**Solution:**
- MP = ₹500, Discount = 10%
- SP = 500 × (100 - 10) / 100 = 500 × 90/100 = ₹450
- SP = ₹450, Profit% = 12.5%
- CP = SP × 100 / (100 + Profit%)
- CP = 450 × 100 / 112.5 = **₹400**

---

**EXAMPLE 5 (Loss scenario):**
A bicycle is sold for ₹1,440 at a loss of 10%. What was the cost price?

**Solution:**
- SP = ₹1,440, Loss% = 10%
- CP = SP × 100 / (100 - Loss%)
- CP = 1440 × 100 / 90 = **₹1,600**

---

### 4.4 SHORTCUT TRICKS — For Speed in Exam

**Trick 1: Multiplying Factor Method**
- 20% profit → Multiply CP by 1.20 to get SP
- 15% loss → Multiply CP by 0.85 to get SP
- 25% profit → SP = 1.25 × CP

**Trick 2: Successive Discounts**
Two successive discounts of a% and b%:
```
Equivalent single discount = a + b - (ab/100)
```
Example: 20% then 10% discount:
= 20 + 10 - (20×10/100) = 30 - 2 = **28% total discount**

**Trick 3: If same price but one sold at x% profit and other at x% loss:**
```
Net result = Loss of (x²/100)%
```
Example: Two items each at ₹1000, one at 10% profit, other at 10% loss:
Net Loss% = 10²/100 = 1% loss (this is always a LOSS)

**Trick 4: When SP is given as fraction of CP:**
- SP = (5/4) × CP → Profit = (1/4) of CP → Profit% = 25%
- SP = (3/4) × CP → Loss = (1/4) of CP → Loss% = 25%

### 4.5 Special PYQ Types for BPSC TRE

**Type 1 — "False Weight" questions:**
A shopkeeper uses a false weight. He sells at CP but uses 900g weight for 1000g.
- He appears to make 0% profit but actually...
- Profit% = (True Weight - False Weight) / False Weight × 100
- = (1000 - 900) / 900 × 100 = **11.11%**

**Type 2 — "Dishonest Dealer" approach:**
Earn x% profit even while appearing to give x% discount → uses false measures.

**Type 3 — Comparing two transactions:**
"A sells to B at 20% profit. B sells to C at 10% loss. If C pays ₹2,160, find A's cost price."
- C's price = B's SP = ₹2,160
- B bought at: 2160 × 100 / (100-10) = 2160 × 100/90 = ₹2,400 (B's CP = A's SP)
- A's CP = 2400 × 100 / (100+20) = 2400 × 100/120 = **₹2,000**

---

# 📝 PRACTICE MCQs — CS: Encapsulation & Abstraction

## 🔴 BPSC TRE PYQ-STYLE QUESTIONS (With Answer Key)

---

**Q1.** In C++, which access specifier allows access from within the class AND its derived (child) classes, but NOT from outside?

(A) public  
(B) private  
(C) protected  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) protected**
*Explanation: protected = class itself + child classes. public = everywhere. private = only within class.*

---

**Q2.** A class that has at least one pure virtual function is called:

(A) Virtual class  
(B) Abstract class  
(C) Interface class  
(D) More than one of the above  
(E) None of the above  

**Answer: (B) Abstract class**
*Explanation: Having at least one pure virtual function (`virtual void f() = 0;`) makes a class abstract.*

---

**Q3.** Which of the following statement(s) about abstract classes in C++ is/are CORRECT?

(A) You cannot create an object of an abstract class  
(B) An abstract class cannot have any data members  
(C) A pointer of abstract class type can be created  
(D) More than one of the above  
(E) None of the above  

**Answer: (D) More than one of the above**
*Explanation: Both (A) and (C) are correct. Abstract classes CAN have data members — (B) is wrong.*

---

**Q4.** What is the default access specifier for members of a `struct` in C++?

(A) private  
(B) protected  
(C) public  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) public**
*Explanation: In C++, `struct` defaults to public access. `class` defaults to private access. This is the ONLY difference.*

---

**Q5.** Which of the following BEST describes the concept of Encapsulation?

(A) Hiding the implementation details from the user  
(B) Bundling data and methods into a single unit and restricting access to some components  
(C) Showing only essential features to the user  
(D) More than one of the above  
(E) None of the above  

**Answer: (B)**
*Explanation: Encapsulation = bundling + restricting access (data hiding + data binding). Option (A) describes Abstraction. Option (C) also describes Abstraction.*

---

**Q6.** Consider the following C++ code:
```cpp
class Shape {
public:
    virtual double area() = 0;
    void display() { cout << "Shape"; }
};

Shape s;
```
What happens when you try to create `Shape s`?

(A) It creates an object with area = 0  
(B) It gives a runtime error  
(C) It gives a compile-time error  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) compile-time error**
*Explanation: Shape is abstract (has pure virtual function). You cannot instantiate abstract classes. Error at compile time.*

---

**Q7.** Which of the following CANNOT be done with an abstract class?

(A) Declaring a pointer to it  
(B) Creating an object of it  
(C) Writing a constructor for it  
(D) More than one of the above  
(E) None of the above  

**Answer: (B) Creating an object of it**
*Explanation: Pointers — allowed. Constructor — allowed (called by derived class). Only creating an OBJECT (instance) is prohibited.*

---

**Q8.** What is the difference between a Virtual Function and a Pure Virtual Function?

(A) Virtual function has a body; pure virtual does not (ends in = 0)  
(B) Virtual function must be overridden; pure virtual need not be  
(C) Both can be present in any class and both allow object creation  
(D) More than one of the above  
(E) None of the above  

**Answer: (A)**
*Explanation: Virtual function has a body and overriding is optional. Pure virtual has no body (= 0) and overriding is mandatory.*

---

**Q9.** Abstraction in OOP refers to:

(A) Hiding the internal implementation and showing only the interface  
(B) Combining data and functions into a class  
(C) Calling the same function with different parameters  
(D) More than one of the above  
(E) None of the above  

**Answer: (A)**
*Explanation: Abstraction = showing only what's necessary, hiding HOW it works. (B) is Encapsulation. (C) is Overloading (Polymorphism).*

---

**Q10.** In Java, what keyword is used by a class to inherit from another class?

(A) inherits  
(B) implements  
(C) extends  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) extends**
*Explanation: `extends` is used for class inheritance in Java. `implements` is for implementing interfaces. `inherits` doesn't exist in Java.*

---

**Q11.** Which of the following is/are application(s) of Encapsulation?

(A) A class with all private variables accessed only through public getters/setters  
(B) A function that can work on objects of different types  
(C) A base class pointer that can point to derived class objects  
(D) More than one of the above  
(E) None of the above  

**Answer: (A)**
*Explanation: (A) perfectly describes encapsulation. (B) describes polymorphism. (C) describes virtual functions/runtime polymorphism.*

---

**Q12.** Which statement about `friend` functions in C++ is CORRECT?

(A) A friend function is a member of the class  
(B) A friend function cannot access private members  
(C) A friend function can access private and protected members of the class  
(D) More than one of the above  
(E) None of the above  

**Answer: (C)**
*Explanation: Friend function is NOT a member of the class, but it CAN access private and protected members. This is the key feature.*

---

## 📝 PRACTICE MCQs — GS: Profit & Loss

**Q13.** A trader buys an article for ₹450 and sells it for ₹540. His profit percentage is:

(A) 15%  
(B) 20%  
(C) 22%  
(D) More than one of the above  
(E) None of the above  

**Answer: (B) 20%**
*Solution: Profit = 540 - 450 = ₹90. Profit% = (90/450) × 100 = 20%*

---

**Q14.** A book is sold at 25% profit. If the cost price is ₹240, what is the selling price?

(A) ₹280  
(B) ₹290  
(C) ₹300  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) ₹300**
*Solution: SP = 240 × 125/100 = ₹300*

---

**Q15.** By selling an item for ₹1,080, a person incurs a loss of 10%. What was the cost price?

(A) ₹1,100  
(B) ₹1,150  
(C) ₹1,200  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) ₹1,200**
*Solution: CP = 1080 × 100/(100-10) = 1080 × 100/90 = ₹1,200*

---

**Q16.** A shopkeeper marks his goods 40% above cost price and allows a 20% discount. His profit% is:

(A) 12%  
(B) 14%  
(C) 16%  
(D) More than one of the above  
(E) None of the above  

**Answer: (A) 12%**
*Solution: Let CP = 100. MP = 140. SP = 140 × 80/100 = 112. Profit% = 12%*

---

**Q17.** Two articles are sold at ₹990 each. One at 10% profit and the other at 10% loss. Overall result:

(A) Neither profit nor loss  
(B) Loss of 1%  
(C) Profit of 1%  
(D) More than one of the above  
(E) None of the above  

**Answer: (B) Loss of 1%**
*Solution: Use trick — when same SP with equal profit% and loss%, result is always LOSS. Loss% = 10²/100 = 1%*

---

**Q18.** A man buys 5 pens for ₹8 and sells 8 pens for ₹5. His gain or loss % is:

(A) Gain 11.1%  
(B) Loss 50%  
(C) Loss 60.9%  
(D) More than one of the above  
(E) None of the above  

**Answer: (C) Loss 60.9%**
*Solution: CP of 1 pen = 8/5 = ₹1.6. SP of 1 pen = 5/8 = ₹0.625. Loss% = (1.6 - 0.625)/1.6 × 100 ≈ 60.9%*

---

**Q19.** If selling price is doubled, the profit triples. What is the original profit percentage?

(A) 50%  
(B) 100%  
(C) 75%  
(D) More than one of the above  
(E) None of the above  

**Answer: (B) 100%**
*Solution: Let CP = x, original SP = x + P. New SP = 2(x+P). New profit = 2(x+P) - x = x + 2P. If x + 2P = 3P → x = P. Profit% = P/x × 100 = 100%*

---

**Q20.** A dishonest shopkeeper sells goods at cost price but uses a 900g weight instead of 1000g. His profit% is:

(A) 10%  
(B) 11.11%  
(C) 9.09%  
(D) More than one of the above  
(E) None of the above  

**Answer: (B) 11.11%**
*Solution: Profit% = (1000 - 900)/900 × 100 = 100/900 × 100 = 11.11%*

---

# 📊 DAY 2 — REVISION NOTES (Write These from Memory Tonight)

Use the blanks below as your self-test. Cover the right column and try to fill in the answers.

| Question | Answer |
|----------|--------|
| What is Encapsulation? | Bundling data + methods; restricting access to some |
| What is Abstraction? | Showing only essential features; hiding implementation |
| Default access in `struct` (C++)? | **public** |
| Default access in `class` (C++)? | **private** |
| What makes a class abstract? | At least ONE pure virtual function |
| Can you create object of abstract class? | **NO** — compile error |
| Can abstract class have constructor? | **YES** |
| Can abstract class have regular methods? | **YES** |
| Pure virtual function syntax? | `virtual void f() = 0;` |
| Can abstract class pointer be created? | **YES** — valid |
| Friend function access level? | Can access private and protected members |
| Profit% formula? | (Profit / CP) × 100 |
| Loss% formula? | (Loss / CP) × 100 |
| SP when 20% profit, CP = 500? | 500 × 120/100 = **₹600** |
| CP when SP = 990, Loss = 10%? | 990 × 100/90 = **₹1,100** |

---

# 🏆 TOPPER TIPS FOR DAY 2

## Understanding Option (D) and (E) for These Topics

From PYQ analysis, here's when to choose (D) "More than one" for Encapsulation/Abstraction questions:

✅ **Choose (D) when question asks about BENEFITS of OOP** — usually 3 benefits apply
✅ **Choose (D) when question asks about "which are valid" about abstract class** — multiple facts may be true
✅ **Choose (E) "None"** carefully — appears when ALL given options are wrong or reversed
❌ **Don't choose (D)** when question asks "which is the BEST definition" — only one best answer

## Common Wrong Answer Traps in OOP Questions

| Trap | Truth |
|------|-------|
| "Abstract class cannot have regular methods" | **WRONG** — it CAN |
| "You can create abstract class objects" | **WRONG** — you CANNOT |
| "struct and class are identical in C++" | **WRONG** — default access differs |
| "Pure virtual = virtual with empty body" | **WRONG** — `= 0` makes it pure, not empty `{}` |
| "Encapsulation and Abstraction are the same" | **WRONG** — different purposes |

---

# 📅 TOMORROW — DAY 3 PREVIEW

**CS Topic:** Inheritance Types (Single, Multiple, Multilevel, Hierarchical, Hybrid)  
**GS Topic:** Ratio & Proportion  
**Ask:** "Day-3 — Teach me all Inheritance types with C++ syntax and Ratio & Proportion"

---

*Day 2 Complete | BPSC TRE 4.0 Preparation | Computer Science Teacher (Class 11-12)*  
*Topics Covered: Encapsulation, Abstraction, Abstract Classes, Pure Virtual Functions, Profit & Loss*  
*PYQ Questions Practiced: 20 (12 CS + 8 GS)*
