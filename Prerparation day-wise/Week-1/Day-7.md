# 📅 BPSC TRE 4.0 — DAY 7: GRAND REVISION
## CS: OOP Week 1 Complete Revision (Days 1–6) | GS: Quick Maths Full Revision
### 🎯 Target: TOPPER RANK | Phase 1 — Week 1 FINAL DAY | Exam Score: 130+/150

---

> **Topper Mindset for Day 7:**
> Revision is NOT re-reading. Revision is RECALLING under pressure.
> Today, before reading any section, first TRY to recall it on your own.
> If you can recall → you own it. If you cannot → read it and drill it again.
> The 50 MCQs at the end simulate BPSC TRE exam pressure. Attempt them strictly.

---

# ════════════════════════════════════════════════
# 🗺️ MASTER MAP — OOP WEEK 1 AT A GLANCE
# (Everything covered in Days 1–6 in one visual)
# ════════════════════════════════════════════════

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    OOP WEEK 1 — COMPLETE MIND MAP                           │
│                                                                             │
│                         ┌──────────────┐                                   │
│                         │     OOP      │                                   │
│                         └──────┬───────┘                                   │
│              ┌──────────┬──────┴───────┬──────────┐                        │
│              │          │             │          │                         │
│         PILLAR 1    PILLAR 2      PILLAR 3    PILLAR 4                     │
│        Encapsula-  Abstraction   Inheritance  Polymor-                     │
│           tion                               phism                         │
│              │          │             │          │                         │
│         ┌────┴───┐  ┌───┴────┐   ┌───┴────┐  ┌──┴─────┐                  │
│         │Access  │  │Abstract│   │5 Types │  │Compile │                   │
│         │Specif. │  │Class   │   │+ Diamond│  │+Runtime│                  │
│         │pub/pri/│  │Interf. │   │Problem  │  │OL vs OR│                  │
│         │prot    │  │Concrete│   │Virtual  │  │vtable  │                  │
│         └────────┘  └────────┘   │Inherit. │  └────────┘                  │
│                                  └─────────┘                               │
│                                                                             │
│    ┌─────────────────────────────────────────────────────────┐             │
│    │              CONSTRUCTORS & DESTRUCTORS                 │             │
│    │  Default | Parameterized | Copy | Initializer List      │             │
│    │  Destructor | Virtual Destructor | Order in Inheritance │             │
│    │  Deep Copy vs Shallow Copy                              │             │
│    └─────────────────────────────────────────────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — TOPIC 1: THE 4 PILLARS OF OOP
# ════════════════════════════════════════════════

## 📌 R1.1 — THE 4 PILLARS (DAY 1 RECALL)

```
┌────────────────┬───────────────────────────────────────────────────────────┐
│   PILLAR       │  ONE-LINE DEFINITION + REAL EXAMPLE                       │
├────────────────┼───────────────────────────────────────────────────────────┤
│ ENCAPSULATION  │ Wrapping DATA + METHODS in one unit (class) + hiding data │
│                │ Example: ATM machine — you press buttons but can't see    │
│                │ the internal circuit. Data is hidden, interface exposed.  │
├────────────────┼───────────────────────────────────────────────────────────┤
│ ABSTRACTION    │ Hiding IMPLEMENTATION details, showing only INTERFACE     │
│                │ Example: TV remote — you press POWER, don't care how it  │
│                │ sends IR signal. Abstract class/interface = remote.       │
├────────────────┼───────────────────────────────────────────────────────────┤
│ INHERITANCE    │ Deriving a new class from an existing class (IS-A)        │
│                │ Example: Dog IS-A Animal. Dog inherits eat(), sleep()     │
│                │ from Animal and adds its own bark().                      │
├────────────────┼───────────────────────────────────────────────────────────┤
│ POLYMORPHISM   │ Same name → many forms; one interface, multiple behaviours│
│                │ Example: Animal.sound() → Dog says "bark", Cat says "meow"│
│                │ Same method call, different execution at runtime.         │
└────────────────┴───────────────────────────────────────────────────────────┘
```

### 🚨 EXAM TRAP — Encapsulation vs Abstraction:
| Feature | Encapsulation | Abstraction |
|---------|--------------|-------------|
| Focus | HIDING DATA | HIDING IMPLEMENTATION |
| How? | Access specifiers (private/protected) | Abstract classes + interfaces |
| Example | `private int salary` | `abstract void calculatePay()` |
| Goal | Data security/protection | Complexity reduction |

---

## 📌 R1.2 — CLASS vs OBJECT (DAY 1 RECALL)

```
┌──────────────────────────────────────────────────────────────────┐
│   CLASS                          OBJECT                          │
│   ─────                          ──────                          │
│   Blueprint / Template           Actual instance / entity        │
│   Defined once                   Created many times              │
│   No memory allocated            Memory allocated                │
│   Example: "Car" (concept)       Example: my_car (specific car)  │
│                                                                  │
│   class Car {                    Car my_car;  ← Object           │
│     string brand;                Car your_car;                   │
│     int speed;                   Car taxi;                       │
│   };                             All are OBJECTS of class Car    │
└──────────────────────────────────────────────────────────────────┘
```

### Instance Variable vs Class Variable:
| Feature | Instance Variable | Class Variable (Static) |
|---------|------------------|------------------------|
| Storage | Each object gets its OWN copy | ONE shared copy for ALL objects |
| Keyword | Normal declaration | `static` keyword |
| Example | `int age` | `static int count` |
| Access | `obj.age` | `ClassName::count` or `obj.count` |

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — TOPIC 2: ENCAPSULATION & ACCESS SPECIFIERS
# ════════════════════════════════════════════════

## 📌 R2.1 — ACCESS SPECIFIERS (DAY 2 RECALL)

```
┌───────────────────────────────────────────────────────────────────────────┐
│              ACCESS SPECIFIER VISIBILITY TABLE                            │
│                                                                           │
│  Location          │  private  │  protected  │  public                   │
│  ──────────────────┼───────────┼─────────────┼────────                   │
│  Same class        │    ✅     │     ✅      │   ✅                      │
│  Derived class     │    ❌     │     ✅      │   ✅                      │
│  Outside class     │    ❌     │     ❌      │   ✅                      │
│                                                                           │
│  MEMORY HOOK:                                                             │
│  private   = "Only me" (same class only)                                 │
│  protected = "Me + my children" (same + derived)                         │
│  public    = "Everyone" (no restriction)                                  │
└───────────────────────────────────────────────────────────────────────────┘
```

### C++ struct vs class — CRITICAL EXAM FACT:
```
struct MyStruct {          class MyClass {
  int x;    // PUBLIC        int x;    // PRIVATE by default!
};                         };

KEY: struct default = PUBLIC | class default = PRIVATE
```

---

## 📌 R2.2 — ABSTRACT CLASS vs INTERFACE (DAY 2 RECALL)

```
┌──────────────────────────────────────────────────────────────────────┐
│   ABSTRACT CLASS                    INTERFACE (in C++)               │
│   ──────────────                    ──────────────────               │
│   Has AT LEAST ONE pure             ALL methods are pure virtual     │
│   virtual function                  No data members                  │
│                                                                      │
│   Can have:                         Only has:                        │
│   - Regular methods ✅              - Pure virtual methods           │
│   - Data members ✅                 - No implementation              │
│   - Constructors ✅                                                  │
│   - Pure virtual methods ✅                                          │
│                                                                      │
│   CANNOT instantiate directly!      CANNOT instantiate directly!     │
│                                                                      │
│   Syntax (C++):                                                      │
│   virtual void show() = 0;    ← Pure virtual function               │
│   (= 0 makes it pure)                                                │
│                                                                      │
│   EXAM FACT: Abstract class must have AT LEAST ONE pure virtual fn  │
│   EXAM FACT: A class with ALL pure virtual functions = Interface     │
└──────────────────────────────────────────────────────────────────────┘
```

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — TOPIC 3: INHERITANCE (DAYS 3–4)
# ════════════════════════════════════════════════

## 📌 R3.1 — 5 TYPES OF INHERITANCE WITH DIAGRAMS

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    5 TYPES OF INHERITANCE                                  │
│                                                                            │
│  TYPE 1: SINGLE           TYPE 2: MULTIPLE         TYPE 3: MULTILEVEL     │
│  ─────────────            ────────────────         ─────────────────────  │
│      A                     A       B                    A                  │
│      │                      \     /                     │                  │
│      B                        C                         B                  │
│                                                         │                  │
│  B inherits A            C inherits A AND B             C                  │
│  Simplest type           JAVA: NOT allowed!        C→B→A chain             │
│                          C++: Allowed              grandparent             │
│                                                                            │
│  TYPE 4: HIERARCHICAL     TYPE 5: HYBRID                                  │
│  ────────────────────     ─────────────                                   │
│           A               A      B                                        │
│          / \               \    /                                          │
│         B   C               C                                             │
│         │                   │                                              │
│  Multiple derived           D                                              │
│  from ONE base         Mix of multiple                                     │
│                        types; can cause                                    │
│                        DIAMOND PROBLEM!                                    │
└────────────────────────────────────────────────────────────────────────────┘
```

### Syntax — MUST KNOW:
```cpp
// C++ Syntax:
class Derived : access_specifier Base { };
class Dog : public Animal { };        // public inheritance
class Dog : private Animal { };       // private inheritance
class Dog : protected Animal { };     // protected inheritance

// Java Syntax:
class Dog extends Animal { }          // extends keyword
class Dog implements Runnable { }     // implements for interface

// EXAM TRAP: C++ uses colon ':' | Java uses 'extends'
```

### What is NOT inherited:
```
❌ Constructors
❌ Destructors
❌ Friend functions
❌ Overloaded operators (=, new, delete)
❌ private members (accessible via protected/public methods, but not directly)
```

---

## 📌 R3.2 — DIAMOND PROBLEM & VIRTUAL INHERITANCE (DAY 4)

```
┌──────────────────────────────────────────────────────────────────────┐
│                   THE DIAMOND PROBLEM                                │
│                                                                      │
│          class A { void show(); }                                    │
│               A                                                      │
│              / \                                                     │
│             B   C         B and C both inherit A                    │
│              \ /                                                     │
│               D           D inherits BOTH B and C                   │
│                                                                      │
│  PROBLEM: D has TWO copies of A's members!                          │
│           D.show() → AMBIGUOUS! Which show()? B's or C's?           │
│                                                                      │
│  SOLUTION: Virtual Inheritance                                       │
│  ─────────────────────────────                                       │
│  class B : virtual public A { };                                    │
│  class C : virtual public A { };                                    │
│  class D : public B, public C { };                                  │
│                                                                      │
│  Now D has only ONE copy of A's members — no ambiguity!             │
│                                                                      │
│  EXAM FACT: Virtual inheritance → use 'virtual' keyword in B and C  │
│  EXAM FACT: Diamond problem only occurs in multiple inheritance      │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 R3.3 — INHERITANCE ACCESS RULES

```
┌──────────────────────────────────────────────────────────────────────────┐
│        HOW ACCESS CHANGES IN DERIVED CLASS                               │
│                                                                          │
│  Base Member  │ public inherit.│ protected inherit.│ private inherit.   │
│  ─────────────┼────────────────┼───────────────────┼──────────────────  │
│  public       │   public       │    protected      │   private          │
│  protected    │   protected    │    protected      │   private          │
│  private      │   NOT inherit. │    NOT inherit.   │   NOT inherit.     │
│                                                                          │
│  MEMORY HOOK: Inheritance access = Min(base access, inherit type)       │
│  public + protected inheritance = protected (take the stricter one)     │
└──────────────────────────────────────────────────────────────────────────┘
```

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — TOPIC 4: POLYMORPHISM (DAY 5)
# ════════════════════════════════════════════════

## 📌 R4.1 — TWO TYPES OF POLYMORPHISM

```
┌────────────────────────────────────────────────────────────────────────┐
│                   POLYMORPHISM                                         │
│                         │                                              │
│              ┌──────────┴───────────┐                                  │
│              │                      │                                  │
│    COMPILE-TIME (Static)         RUNTIME (Dynamic)                     │
│    ─────────────────────         ───────────────────                   │
│    Resolved at COMPILE time      Resolved at RUNTIME                   │
│    Faster execution              Slightly slower (vtable)              │
│    No virtual functions          Requires virtual functions            │
│              │                              │                          │
│      ┌───────┴───────┐             ┌────────┴───────┐                  │
│      │               │             │                │                  │
│  Method           Operator     Method           vtable/vptr            │
│  Overloading      Overloading  Overriding        mechanism             │
│                                                                        │
│  SAME NAME,       REDEFINE     SAME NAME,         Virtual              │
│  different args   operators    same signature,    function             │
│  SAME class       in class     DIFFERENT class    table                │
└────────────────────────────────────────────────────────────────────────┘
```

## 📌 R4.2 — OVERLOADING vs OVERRIDING (EXAM FAVOURITE)

```
┌────────────────────────────────────────────────────────────────────────┐
│  Feature           │  OVERLOADING              │  OVERRIDING            │
│  ──────────────────┼───────────────────────────┼───────────────────── │
│  Where?            │  SAME class               │  DIFFERENT classes    │
│                    │                           │  (base + derived)     │
│  Signature         │  DIFFERENT parameters     │  SAME signature       │
│  Return type       │  Can differ               │  Must be same (or     │
│                    │                           │  covariant)           │
│  Resolved when?    │  Compile time             │  Run time             │
│  Keyword needed?   │  None                     │  virtual in base      │
│  Example           │  add(int), add(float)     │  Animal.sound() vs    │
│                    │  Both in same class       │  Dog.sound()          │
│  Type              │  Compile-time polymorphism│  Runtime polymorphism │
└────────────────────────────────────────────────────────────────────────┘
```

## 📌 R4.3 — VIRTUAL FUNCTION vs PURE VIRTUAL FUNCTION

```
┌─────────────────────────────────────────────────────────────────────┐
│  VIRTUAL FUNCTION              │  PURE VIRTUAL FUNCTION              │
│  ─────────────────             │  ─────────────────────              │
│  Has a body (implementation)   │  NO body; ends with = 0            │
│  Can be overridden (optional)  │  MUST be overridden in derived      │
│  Base class is concrete        │  Makes base class ABSTRACT          │
│  CAN instantiate base class    │  CANNOT instantiate base class      │
│                                │                                     │
│  Syntax:                       │  Syntax:                            │
│  virtual void show() {         │  virtual void show() = 0;           │
│    cout << "Base";             │  ← No body here!                   │
│  }                             │                                     │
│                                │                                     │
│  EXAM FACT: If derived class   │  EXAM FACT: = 0 at end makes it    │
│  doesn't override, base        │  pure virtual. One such fn makes    │
│  version is called             │  the whole class ABSTRACT           │
└─────────────────────────────────────────────────────────────────────┘
```

## 📌 R4.4 — vtable and vptr (CONCEPT — EXAM ASKED IN TRE 3.0)

```
┌──────────────────────────────────────────────────────────────────────┐
│  VTABLE (Virtual Function Table)                                     │
│  ─────────────────────────────                                       │
│  A TABLE maintained by compiler for every class with virtual fns     │
│  Contains: Function pointers to each virtual function                │
│                                                                      │
│  VPTR (Virtual Pointer)                                              │
│  ─────────────────────                                               │
│  Each OBJECT has a hidden pointer (vptr) that points to its class's  │
│  vtable. Set during object construction.                             │
│                                                                      │
│  HOW RUNTIME POLYMORPHISM WORKS:                                     │
│  1. Base* ptr = new Derived();                                       │
│  2. ptr points to Derived object (which has Derived's vptr)          │
│  3. ptr->show() → compiler looks up vptr → finds vtable → calls     │
│     the Derived class's show() — NOT Base's                          │
│                                                                      │
│  This is why virtual functions enable RUNTIME polymorphism           │
└──────────────────────────────────────────────────────────────────────┘
```

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — TOPIC 5: CONSTRUCTORS & DESTRUCTORS (DAY 6)
# ════════════════════════════════════════════════

## 📌 R5.1 — COMPLETE CONSTRUCTOR FAMILY

```
┌──────────────────────────────────────────────────────────────────────┐
│             CONSTRUCTOR COMPARISON TABLE                             │
│                                                                      │
│  Type          │ Signature              │ When called               │
│  ──────────────┼────────────────────────┼──────────────────────────  │
│  Default       │ ClassName()            │ Object created w/o args    │
│  Parameterized │ ClassName(int a, ...)  │ Object created with args   │
│  Copy          │ ClassName(const C& o)  │ New object from old object │
│                                                                      │
│  CONSTRUCTOR RULES — MUST KNOW:                                      │
│  ✅ Same name as class                                               │
│  ✅ No return type (not even void)                                   │
│  ✅ Called automatically                                             │
│  ✅ Can be overloaded                                                │
│  ❌ Cannot be virtual                                                │
│  ❌ Cannot be static                                                 │
│  ❌ Not inherited by derived class                                   │
└──────────────────────────────────────────────────────────────────────┘
```

## 📌 R5.2 — ORDER IN INHERITANCE (MOST ASKED IN PYQs)

```
┌──────────────────────────────────────────────────────────────────────┐
│   MULTILEVEL: class A → class B : A → class C : B                   │
│                                                                      │
│   Object of C created:              Object of C destroyed:          │
│   ─────────────────────             ─────────────────────           │
│        A() called ← first                ~C() called ← first        │
│        B() called ← second               ~B() called ← second       │
│        C() called ← last                 ~A() called ← last         │
│                                                                      │
│   RULE: Constructors = Base FIRST (top-down in hierarchy)            │
│   RULE: Destructors  = Derived FIRST (bottom-up, LIFO order)         │
│                                                                      │
│   MEMORY HOOK:                                                       │
│   "Foundation before walls before roof"   → Construction            │
│   "Roof removed first, then walls, then foundation" → Destruction    │
└──────────────────────────────────────────────────────────────────────┘
```

## 📌 R5.3 — DEEP vs SHALLOW COPY QUICK RECAP

```
SHALLOW COPY (Default):            DEEP COPY (Custom):
Object A ──ptr──► [DATA]           Object A ──ptr──► [DATA]
Object B ──ptr──► [DATA]           Object B ──ptr──► [COPY OF DATA]
          ↑ SAME location!                    ↑ SEPARATE location!

PROBLEM: Delete A → DATA freed → B's ptr is dangling = CRASH!
FIX: Write custom copy constructor doing Deep Copy (new allocation)
```

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — MASTER TRAP TABLE
# (All Conceptual Traps from OOP Week 1)
# ════════════════════════════════════════════════

```
┌──────────────────────────────────────────────────────────────────────────┐
│              ⚠️ OOP EXAM TRAPS — NEVER GET THESE WRONG                  │
│                                                                          │
│  TRAP STATEMENT                  │  CORRECT FACT                        │
│  ───────────────────────────────┼─────────────────────────────────────  │
│  struct members are private      │  struct default = PUBLIC              │
│  by default                      │  class default = PRIVATE              │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Abstract class has ALL pure     │  Abstract = AT LEAST ONE pure virtual │
│  virtual functions               │  ALL pure virtual = Interface         │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Constructors can be virtual     │  Constructors CANNOT be virtual       │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Destructors cannot be virtual   │  Destructors CAN and SHOULD be       │
│                                  │  virtual in base classes              │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Multiple destructors per class  │  Only ONE destructor per class        │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Java supports multiple          │  Java does NOT support multiple       │
│  inheritance via classes         │  inheritance via classes              │
│                                  │  (only via interfaces)                │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Overloading = runtime           │  Overloading = COMPILE time           │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Overriding = compile time       │  Overriding = RUNTIME                 │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Student s2 = s1 calls           │  If s2 is NEW → Copy Constructor      │
│  assignment operator             │  If s2 EXISTED → Assignment Operator  │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  Friend function is a member     │  Friend function is NOT a member of   │
│  of the class                    │  the class; it can ACCESS private     │
│                                  │  members but is NOT part of class     │
│  ─────────────────────────────── │ ─────────────────────────────────    │
│  C++ uses 'extends' for          │  C++ uses ':' (colon)                 │
│  inheritance                     │  Java uses 'extends'                  │
└──────────────────────────────────────────────────────────────────────────┘
```

---

# ════════════════════════════════════════════════
# 🟥 CS REVISION — OPERATOR OVERLOADING QUICK FACTS
# ════════════════════════════════════════════════

## 📌 R6.1 — OPERATOR OVERLOADING (DAY 5 TOPIC)

```
What CAN be overloaded:   +, -, *, /, %, <, >, ==, !=, [], (), <<, >>
What CANNOT be overloaded: ::, .*, ., ?:, sizeof, typeid

Rules:
✅ At least one operand must be a user-defined type
✅ Overloaded operator function: operator keyword + symbol
✅ Cannot change number of operands
✅ Cannot change precedence or associativity

Syntax:
ReturnType operator symbol (parameters) { }
Example:
Complex operator + (const Complex& c) {
    return Complex(real + c.real, imag + c.imag);
}
```

---

# ════════════════════════════════════════════════
# 🟦 GS REVISION — QUICK MATHS: ALL TOPICS
# (Days 1–6 GS Coverage: %, P&L, Ratio, Number, Avg, LCM/HCF)
# ════════════════════════════════════════════════

## 📌 GS1 — PERCENTAGE (Day 1 GS)

```
┌─────────────────────────────────────────────────────────────────┐
│  PERCENTAGE FORMULAS                                            │
│                                                                 │
│  X% of Y = (X × Y) / 100                                       │
│  A is what % of B = (A/B) × 100                                 │
│  % increase = (Increase / Original) × 100                       │
│  % decrease = (Decrease / Original) × 100                       │
│                                                                 │
│  SUCCESSIVE % CHANGES:                                          │
│  Two changes of a% and b%: Net = a + b + ab/100                │
│  (Use + for increase, - for decrease)                           │
│                                                                 │
│  EXAMPLES:                                                       │
│  10% increase then 10% decrease = 10 + (-10) + (10×-10)/100     │
│  = 0 + (-1) = -1% → Net DECREASE of 1%                         │
│                                                                 │
│  20% increase then 25% decrease = 20 + (-25) + (20×-25)/100    │
│  = -5 + (-5) = -10% → Net decrease of 10%                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS2 — PROFIT & LOSS (Day 2 GS)

```
┌──────────────────────────────────────────────────────────────────┐
│  PROFIT & LOSS MASTER FORMULAS                                   │
│                                                                  │
│  CP = Cost Price (what you pay to buy)                           │
│  SP = Selling Price (what you sell at)                           │
│  MP = Marked Price (listed/printed price)                        │
│                                                                  │
│  Profit = SP – CP       (when SP > CP)                           │
│  Loss = CP – SP         (when CP > SP)                           │
│  Profit% = (Profit / CP) × 100                                   │
│  Loss% = (Loss / CP) × 100          ← Always on CP!             │
│                                                                  │
│  SP = CP × (100 + Profit%) / 100                                 │
│  SP = CP × (100 – Loss%) / 100                                   │
│  CP = SP × 100 / (100 + Profit%)                                 │
│  CP = SP × 100 / (100 – Loss%)                                   │
│                                                                  │
│  Discount = MP – SP                                              │
│  Discount% = (Discount / MP) × 100   ← Always on MP!            │
│                                                                  │
│  TRICK — If item sold at x% loss same as at ₹y more:            │
│  CP = y × 100 / (2x)   [symmetric loss/gain problems]           │
└──────────────────────────────────────────────────────────────────┘
```

**Shortcut — Multiplier Method:**
```
Gain 20% → SP = CP × 120/100 = CP × 1.2
Loss 15% → SP = CP × 85/100 = CP × 0.85
Discount 10% on MP → SP = MP × 0.9
```

---

## 📌 GS3 — RATIO & PROPORTION (Day 3 GS)

```
┌─────────────────────────────────────────────────────────────────┐
│  RATIO & PROPORTION RULES                                       │
│                                                                 │
│  Ratio a:b = a/b                                                │
│  Proportion: a:b :: c:d means ad = bc (cross multiplication)    │
│                                                                 │
│  If a:b = 3:4 and b:c = 5:6, find a:b:c:                       │
│  Make b common: a:b = 15:20, b:c = 20:24 → a:b:c = 15:20:24   │
│                                                                 │
│  PARTNERSHIP:                                                    │
│  Profit shared in ratio of (Capital × Time)                     │
│  A: ₹10,000 for 12 months, B: ₹15,000 for 8 months            │
│  Ratio = (10000×12) : (15000×8) = 120000 : 120000 = 1:1       │
│                                                                 │
│  MIXTURE RULE (Alligation):                                     │
│  Mix items at prices A and B to get mean price M:               │
│  Ratio = (B–M) : (M–A)                                         │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS4 — NUMBER SYSTEM (Day 4 GS)

```
┌─────────────────────────────────────────────────────────────────┐
│  DIVISIBILITY RULES                                             │
│  2: Last digit even                                             │
│  3: Sum of digits divisible by 3                                │
│  4: Last 2 digits divisible by 4                                │
│  5: Last digit 0 or 5                                           │
│  6: Divisible by BOTH 2 and 3                                   │
│  8: Last 3 digits divisible by 8                                │
│  9: Sum of digits divisible by 9                                │
│  11: (Sum of odd position digits – Sum of even) divisible by 11 │
│                                                                 │
│  NUMBER TYPES:                                                   │
│  Natural: 1, 2, 3...      Whole: 0, 1, 2, 3...                 │
│  Integer: ...-2,-1,0,1,2  Rational: p/q form (q≠0)             │
│  Prime: exactly 2 factors (2, 3, 5, 7, 11, 13, 17, 19, 23...) │
│  1 is NOT prime! (only 1 factor)                                │
│  Smallest prime = 2 (only even prime)                           │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS5 — AVERAGES (Day 5 GS)

```
┌─────────────────────────────────────────────────────────────────┐
│  AVERAGE FORMULAS                                               │
│                                                                 │
│  Average = Sum of all values / Number of values                 │
│  Sum = Average × Number of values                               │
│                                                                 │
│  If one value WRONG by error x:                                 │
│  New average = Old average ± (x / n)                           │
│                                                                 │
│  Average speed:                                                 │
│  If same DISTANCE at speeds S1 and S2:                          │
│  Avg speed = 2S1S2 / (S1 + S2)   ← Harmonic mean, NOT (S1+S2)/2│
│                                                                 │
│  Consecutive numbers average:                                   │
│  1 to n → Average = (n+1)/2                                    │
│  1,2,...n → Average = (n+1)/2                                   │
│  First n odd numbers → Average = n                              │
│  First n even numbers → Average = n+1                          │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS6 — LCM & HCF RAPID REVISION (Day 6 GS)

```
┌─────────────────────────────────────────────────────────────────┐
│  HCF: Common prime factors × LOWEST powers                      │
│  LCM: All prime factors × HIGHEST powers                        │
│  HCF × LCM = Product of two numbers (for exactly 2 numbers!)   │
│                                                                 │
│  HCF of fractions = HCF(Numerators) / LCM(Denominators)        │
│  LCM of fractions = LCM(Numerators) / HCF(Denominators)        │
│                                                                 │
│  GREATEST divisor with remainder r: HCF(A–r, B–r, C–r)         │
│  LEAST multiple with remainder r: LCM(A,B,C) + r               │
│  Different remainders, same gap k: LCM(A,B,C) – k              │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS7 — GK RAPID FIRE: HISTORY + SCIENCE (Week 1 Coverage)

### Modern Indian History — Key Facts:
| Fact | Detail |
|------|--------|
| First civil disobedience in India | Champaran Satyagraha, 1917 |
| Gandhi's first satyagraha in India | Champaran, Bihar, 1917 |
| First INC President | W.C. Bonnerjee (1885 session, Bombay) |
| Grand Old Man of India | Dadabhai Naoroji |
| Revolt of 1857 first called war of independence by | V.D. Savarkar |
| Abhinav Bharat — founded in London | V.D. Savarkar |
| Ghadar Party — established in USA | Lala Hardayal, San Francisco, 1913 |
| Bihar Provincial Congress Committee founded | 1908, HQ Patna |
| INC Gaya session 1922 president | Chittaranjan Das |
| Jallianwala Bagh 1919 viceroy | Lord Chelmsford |
| Bardoli Satyagraha leader | Sardar Vallabhbhai Patel (1928) |
| AIKS Bihar 1936 | Swami Sahajanand Saraswati |
| Anushilan Samiti Patna 1913 | Sachindra Nath Sanyal |
| Bihar Socialist Party founders | Phulan Prasad Varma + Jayaprakash Narayan |
| Birsa Munda's Commander-in-Chief | Gaya Munda |

### Science Quick Facts (NCERT Level):
| Topic | Key Fact |
|-------|---------|
| Photoperiodism discovered by | Garner and Allard |
| Asexual reproduction by budding | Yeast |
| Ginger is | Underground stem (rhizome) — has nodes & internodes |
| Anther contains | Pollen grains |
| Diaphragm during normal breathing | Flattened (moves down) |
| Vas deferens | Male reproductive organ |
| Immunity — most important cell | Lymphocytes |
| P = I²R formula | Electrical power |
| Convex lens in water | Still converges, but focal length INCREASES |
| Frequency when light changes medium | Unchanged (only speed and wavelength change) |

### Bihar GK:
| Topic | Fact |
|-------|------|
| Bihar population share of India | 8.58% (Census 2011) |
| Max paddy production district | Rohtas |
| Max silk textile district | Bhagalpur |
| First Bhojpuri film | Ganga Maiya Tohe Piyari Chadhaibo (1963) |
| State Bird | House Sparrow |
| State Animal | Gaur (Indian Bison) |
| State Flower | Kachnar |
| Vikramshila University | Bhagalpur district |
| Nalanda University | Nalanda/Rajgir district |

---

# ════════════════════════════════════════════════
# 🧪 PRACTICE MCQs — DAY 7
# ⚠️ ATTEMPT ALL 50 BEFORE CHECKING ANSWERS
# ════════════════════════════════════════════════

---

## 📘 COMPUTER SCIENCE — 25 MCQs
### (OOP Week 1 Full Revision — Mixed All Topics)

---

**Q1. [LEVEL: Easy — Day 1]**
Which of the following is NOT one of the four pillars of Object-Oriented Programming?

(A) Encapsulation
(B) Inheritance
(C) Compilation
(D) More than one of the above
(E) None of the above

---

**Q2. [LEVEL: Easy — Day 2]**
In C++, the default access specifier for members of a `struct` is:

(A) private
(B) protected
(C) public
(D) More than one of the above
(E) None of the above

---

**Q3. [LEVEL: Easy — Day 3]**
Which inheritance type creates an IS-A relationship between a child class and a single parent class?

(A) Multiple Inheritance
(B) Hybrid Inheritance
(C) Single Inheritance
(D) More than one of the above
(E) None of the above

---

**Q4. [LEVEL: Easy — Day 4]**
The diamond problem in multiple inheritance is resolved using:

(A) Friend functions
(B) Virtual inheritance
(C) Abstract classes
(D) More than one of the above
(E) None of the above

---

**Q5. [LEVEL: Easy — Day 5]**
Method overloading is an example of which type of polymorphism?

(A) Runtime polymorphism
(B) Dynamic polymorphism
(C) Compile-time polymorphism
(D) More than one of the above
(E) None of the above

---

**Q6. [LEVEL: Easy — Day 6]**
Which of the following is TRUE about a destructor in C++?

(A) A class can have multiple destructors
(B) A destructor can take parameters
(C) A destructor is called automatically when an object goes out of scope
(D) More than one of the above
(E) None of the above

---

**Q7. [LEVEL: Medium — Day 2]**
Which of the following makes a class ABSTRACT in C++?

(A) Declaring all member functions as private
(B) Declaring at least one pure virtual function
(C) Using the `abstract` keyword before the class
(D) More than one of the above
(E) None of the above

---

**Q8. [LEVEL: Medium — Day 3]**
Which of the following keywords is used for inheritance in JAVA?

(A) inherits
(B) implements (for class-to-class)
(C) extends
(D) More than one of the above
(E) None of the above

---

**Q9. [LEVEL: Medium — Day 4]**
Which of the following statements about virtual functions is CORRECT?

(A) Virtual functions enable compile-time polymorphism
(B) A pure virtual function has no body and is declared with `= 0`
(C) Virtual functions can only be defined in derived classes
(D) More than one of the above
(E) None of the above

---

**Q10. [LEVEL: Medium — Day 5]**
Consider the following:
```cpp
class Animal {
public:
    virtual void sound() { cout << "Generic sound"; }
};
class Dog : public Animal {
public:
    void sound() { cout << "Bark"; }
};
int main() {
    Animal* a = new Dog();
    a->sound();
}
```
What is the output?

(A) Generic sound
(B) Bark
(C) Compilation error
(D) More than one of the above
(E) None of the above

---

**Q11. [LEVEL: Medium — Day 6]**
In C++, when a derived class object goes out of scope, the order of destructor calls is:

(A) Base destructor first, then Derived
(B) Derived destructor first, then Base
(C) Only the Derived destructor is called
(D) More than one of the above
(E) None of the above

---

**Q12. [LEVEL: Medium — Day 2]**
Which access specifier in C++ makes a member accessible within the same class and all derived classes, but NOT outside?

(A) public
(B) private
(C) protected
(D) More than one of the above
(E) None of the above

---

**Q13. [LEVEL: Medium — Day 1]**
What is the difference between a class variable (static variable) and an instance variable?

(A) A class variable is shared among all objects; instance variable is unique per object
(B) Class variable is declared with `static` keyword
(C) Instance variable takes more memory per object than class variable
(D) More than one of the above — A, B, and C are all correct
(E) None of the above

---

**Q14. [LEVEL: Medium — Day 5]**
Which of the following CANNOT be overloaded in C++?

(A) `+` operator
(B) `[]` operator
(C) `::` scope resolution operator
(D) More than one of the above
(E) None of the above

---

**Q15. [LEVEL: Hard — Day 3]**
Consider public inheritance in C++. If a base class has a `protected` member, it appears as which type in the derived class?

(A) private
(B) public
(C) protected
(D) More than one of the above
(E) None of the above

---

**Q16. [LEVEL: Hard — Day 4]**
```cpp
class A { public: void show() { cout << "A"; } };
class B : virtual public A { };
class C : virtual public A { };
class D : public B, public C { };
int main() {
    D obj;
    obj.show();
}
```
What does this code demonstrate and what is the output?

(A) Diamond problem; Compilation error due to ambiguity
(B) Virtual inheritance solving diamond problem; Output: A
(C) Multiple inheritance without virtual; Output: AA
(D) More than one of the above
(E) None of the above

---

**Q17. [LEVEL: Hard — Day 5]**
Which of the following is TRUE about runtime polymorphism?

(A) It is achieved using function overloading
(B) It requires the `virtual` keyword in the base class
(C) It uses a vtable (virtual table) mechanism
(D) More than one of the above — both B and C
(E) None of the above

---

**Q18. [LEVEL: Hard — Day 6]**
What is the output of the following code?
```cpp
class P {
public:
    P() { cout << "P "; }
    ~P() { cout << "~P "; }
};
class Q : public P {
public:
    Q() { cout << "Q "; }
    ~Q() { cout << "~Q "; }
};
int main() {
    P* ptr = new Q();
    delete ptr;
}
```
(Assume destructor of P is NOT virtual)

(A) P Q ~Q ~P
(B) P Q ~P
(C) P Q ~Q
(D) More than one of the above
(E) None of the above

---

**Q19. [LEVEL: Hard — Day 2]**
A class that has ALL its methods as pure virtual functions and NO data members is best described as:

(A) Abstract class
(B) Concrete class
(C) Interface
(D) More than one of the above — both A and C
(E) None of the above

---

**Q20. [LEVEL: PYQ-Style — Day 1]**
Which of the following features is/are characteristic of pure OOP languages?
1. Everything is treated as an object
2. Supports procedural programming style
3. Must support all four OOP pillars

(A) Only 1
(B) Only 1 and 3
(C) Only 2 and 3
(D) More than one of the above
(E) None of the above

---

**Q21. [LEVEL: PYQ-Style — Day 3]**
Which of the following is/are NOT inherited by a derived class in C++?

(A) Constructors
(B) Destructors
(C) Friend functions of base class
(D) More than one of the above — all three are NOT inherited
(E) None of the above

---

**Q22. [LEVEL: PYQ-Style — Day 5]**
What is the difference between method overloading and method overriding?

(A) Overloading happens within same class; Overriding happens across parent-child classes
(B) Overloading is resolved at compile time; Overriding at runtime
(C) Overloading uses same method name with different signatures; Overriding uses same signature in child class
(D) More than one of the above — A, B, and C are all correct
(E) None of the above

---

**Q23. [LEVEL: PYQ-Style — Day 6]**
For which of the following reasons should a destructor be made virtual in a base class?

(A) To allow the destructor to be overloaded in the base class
(B) To ensure the derived class destructor is also called when deleting via base class pointer
(C) To prevent the base class destructor from being called
(D) More than one of the above
(E) None of the above

---

**Q24. [LEVEL: Tricky — Day 4]**
Which of the following is the correct syntax for a pure virtual function in C++?

(A) `virtual void show();`
(B) `void show() = 0;`
(C) `virtual void show() = 0;`
(D) More than one of the above — both B and C
(E) None of the above

---

**Q25. [LEVEL: Tricky — Combined]**
Consider the following statements about OOP in C++:
1. A class with one pure virtual function and several regular functions is abstract
2. A friend function can access private members of the class
3. The `virtual` keyword in C++ enables both compile-time and runtime polymorphism

Which statements are CORRECT?

(A) Only 1
(B) Only 1 and 2
(C) All three
(D) More than one of the above
(E) None of the above

---

---

## 📘 GENERAL STUDIES (GS + GK) — 25 MCQs
### (Maths: All Week 1 Topics + History + Science + Bihar GK)

---

**Q26. [LEVEL: Easy — Percentage]**
What is 15% of 200?

(A) 15
(B) 25
(C) 30
(D) More than one of the above
(E) None of the above

---

**Q27. [LEVEL: Easy — Profit & Loss]**
A shopkeeper buys a pen for ₹40 and sells it for ₹50. What is the profit percentage?

(A) 10%
(B) 20%
(C) 25%
(D) More than one of the above
(E) None of the above

---

**Q28. [LEVEL: Easy — Ratio]**
If A:B = 3:4 and B:C = 2:3, what is A:C?

(A) 1:2
(B) 3:8
(C) 1:4
(D) More than one of the above
(E) None of the above

---

**Q29. [LEVEL: Easy — GK History]**
Who is known as the "Grand Old Man of India"?

(A) Mahatma Gandhi
(B) Gopal Krishna Gokhale
(C) Dadabhai Naoroji
(D) More than one of the above
(E) None of the above

---

**Q30. [LEVEL: Easy — Biology]**
Asexual reproduction by budding is found in which organism?

(A) Amoeba
(B) Yeast
(C) Fern
(D) More than one of the above
(E) None of the above

---

**Q31. [LEVEL: Medium — Percentage]**
A number is increased by 20% and then decreased by 20%. What is the net change?

(A) No change (0%)
(B) 4% increase
(C) 4% decrease
(D) More than one of the above
(E) None of the above

---

**Q32. [LEVEL: Medium — Profit & Loss]**
A trader marks his goods at 25% above cost price and gives a 10% discount. What is his profit percentage?

(A) 10%
(B) 12.5%
(C) 15%
(D) More than one of the above
(E) None of the above

---

**Q33. [LEVEL: Medium — Average]**
The average of 5 numbers is 25. If one number is replaced by 45 instead of 25, what is the new average?

(A) 27
(B) 28
(C) 29
(D) More than one of the above
(E) None of the above

---

**Q34. [LEVEL: Medium — Number System]**
Which of the following numbers is divisible by 11?

(A) 121
(B) 132
(C) 143
(D) More than one of the above — all three are divisible by 11
(E) None of the above

---

**Q35. [LEVEL: Medium — LCM/HCF]**
The LCM of two numbers is 120 and their HCF is 10. If one number is 40, the other is:

(A) 20
(B) 30
(C) 40
(D) More than one of the above
(E) None of the above

---

**Q36. [LEVEL: Medium — History]**
The Non-Cooperation Movement was launched in which year?

(A) 1917
(B) 1919
(C) 1920
(D) More than one of the above
(E) None of the above

---

**Q37. [LEVEL: Medium — Science Physics]**
When light travels from air into water, which of the following remains UNCHANGED?

(A) Speed
(B) Wavelength
(C) Frequency
(D) More than one of the above
(E) None of the above

---

**Q38. [LEVEL: Medium — Bihar GK]**
Which district of Bihar is famous for Tussar (Tasar) silk?

(A) Patna
(B) Rohtas
(C) Bhagalpur
(D) More than one of the above
(E) None of the above

---

**Q39. [LEVEL: Medium — History]**
The Anushilan Samiti was founded in Patna in 1913 by:

(A) Jayaprakash Narayan
(B) Sachindra Nath Sanyal
(C) Swami Sahajanand Saraswati
(D) More than one of the above
(E) None of the above

---

**Q40. [LEVEL: Medium — Science Biology]**
Photoperiodism in plants was discovered by:

(A) Gregor Mendel
(B) Charles Darwin
(C) Garner and Allard
(D) More than one of the above
(E) None of the above

---

**Q41. [LEVEL: Hard — Profit & Loss]**
A man bought two articles for ₹1800 total. He sold the first at 20% profit and the second at 20% loss. If the selling prices of both were equal, find the cost price of the article sold at profit.

(A) ₹600
(B) ₹800
(C) ₹900
(D) More than one of the above
(E) None of the above

---

**Q42. [LEVEL: Hard — Ratio]**
In a partnership, A invests ₹12,000 for 6 months and B invests ₹8,000 for 9 months. In what ratio should profit be divided?

(A) 1:1
(B) 2:1
(C) 1:2
(D) More than one of the above
(E) None of the above

---

**Q43. [LEVEL: Hard — LCM Application]**
Find the least number which when divided by 16, 24, and 36 leaves remainder 7 in each case.

(A) 143
(B) 151
(C) 155
(D) More than one of the above
(E) None of the above

---

**Q44. [LEVEL: Hard — Average]**
A train travels the first 100 km at 50 km/h and the next 100 km at 100 km/h. What is the average speed for the entire journey?

(A) 75 km/h
(B) 66.67 km/h
(C) 80 km/h
(D) More than one of the above
(E) None of the above

---

**Q45. [LEVEL: Hard — History Combined]**
Consider the following pairs:
1. Champaran Satyagraha — 1917 — Bihar
2. Bardoli Satyagraha — 1928 — Gujarat
3. Salt March (Dandi March) — 1930 — Gujarat

How many pairs are CORRECTLY matched?

(A) Only 1
(B) Only 1 and 2
(C) All three
(D) More than one of the above
(E) None of the above

---

**Q46. [LEVEL: Hard — Number Theory]**
What is the smallest 4-digit number divisible by 12, 15, and 18?

(A) 1020
(B) 1080
(C) 1440
(D) More than one of the above
(E) None of the above

---

**Q47. [LEVEL: PYQ-Style — Science]**
Which of the following statements about the human respiratory system is CORRECT?

(A) During inhalation, the diaphragm moves upward
(B) During normal breathing, the diaphragm becomes flattened
(C) Ribs contract inward during inhalation
(D) More than one of the above
(E) None of the above

---

**Q48. [LEVEL: PYQ-Style — Bihar GK]**
Which of the following correctly describes Bihar's demographic significance?

(A) Bihar has the highest population density in India
(B) Bihar accounts for approximately 8.58% of India's population (2011)
(C) Bihar is the smallest state in India by area
(D) More than one of the above
(E) None of the above

---

**Q49. [LEVEL: PYQ-Style — Maths]**
The product of two co-prime numbers is 117. Their HCF is:

(A) 3
(B) 9
(C) 1
(D) More than one of the above
(E) None of the above

---

**Q50. [LEVEL: Tricky — Combined GK]**
Which of the following statements is/are CORRECT about the Indian National Congress?

(A) Its first session was held in Bombay in 1885
(B) Its first president was W.C. Bonnerjee
(C) Dadabhai Naoroji presided over the INC session that first demanded Swaraj (self-rule)

(A-option): Only statement A is correct
(B-option): Statements A and B are correct
(C-option): All three statements A, B, and C are correct
(D) More than one of the above
(E) None of the above

---

---

# ✅ ANSWER KEY
## ⚠️ Check ONLY after completing all 50 questions

---

## CS ANSWERS (Q1–Q25)

| Q# | Answer | Key Explanation |
|----|--------|----------------|
| Q1 | **(C)** | The 4 pillars are: Encapsulation, Inheritance, Polymorphism, Abstraction. "Compilation" is NOT a pillar. |
| Q2 | **(C)** | struct default = **public**; class default = private. This is a classic exam trap. |
| Q3 | **(C)** | Single Inheritance = one child, one parent, IS-A relationship. |
| Q4 | **(B)** | Virtual inheritance using `virtual` keyword in intermediate classes solves the diamond problem. |
| Q5 | **(C)** | Method overloading is resolved at COMPILE TIME = Compile-time (static) polymorphism. |
| Q6 | **(C)** | Destructors have NO parameters (A wrong), cannot be overloaded (A wrong), are called automatically when object goes out of scope (C correct). |
| Q7 | **(B)** | Abstract class requires AT LEAST ONE pure virtual function. C++ has NO `abstract` keyword (unlike Java). |
| Q8 | **(C)** | Java uses `extends` for class inheritance. `implements` is used for interfaces (not class-to-class). |
| Q9 | **(B)** | Pure virtual function has NO body and uses `= 0` syntax. Virtual functions enable RUNTIME (not compile-time) polymorphism. |
| Q10 | **(B)** | `virtual` in base + derived overrides → Runtime polymorphism. `a->sound()` calls Dog's sound via vtable → **Bark** |
| Q11 | **(B)** | Destruction order = Derived FIRST, then Base (LIFO — reverse of construction order). |
| Q12 | **(C)** | `protected` = accessible in same class + derived classes, NOT outside. That's exactly what's described. |
| Q13 | **(D)** | All three statements (A, B, C) are correct about class vs instance variables. Hence D. |
| Q14 | **(C)** | `::` (scope resolution), `.*`, `.`, `?:`, `sizeof`, `typeid` CANNOT be overloaded. `+` and `[]` CAN be overloaded. |
| Q15 | **(C)** | In public inheritance: protected member of base remains **protected** in derived class. |
| Q16 | **(B)** | Virtual inheritance ensures only ONE copy of A exists. `obj.show()` prints "A" — no ambiguity. |
| Q17 | **(D)** | Both B and C are correct: `virtual` keyword is required AND vtable mechanism is used. Option A (overloading) is compile-time, not runtime. |
| Q18 | **(B)** | Without virtual destructor: `delete ptr` calls only Base (P's) destructor via static binding. Output: P Q ~P (Q's destructor is SKIPPED — memory leak!) |
| Q19 | **(D)** | A class with ALL pure virtual functions and no data = **Interface** concept. It IS also abstract (abstract = at least one pure virtual). Both A and C describe it. Hence D. |
| Q20 | **(B)** | Pure OOP languages: everything is object (1 ✅) + must support all 4 pillars (3 ✅). Supporting procedural style (2) is NOT a feature of PURE OOP. |
| Q21 | **(D)** | Constructors, destructors, and friend functions are all NOT inherited. Hence D (all three). |
| Q22 | **(D)** | All three statements (A, B, C) correctly describe the difference — hence D. |
| Q23 | **(B)** | Virtual destructor ensures derived destructor is called when deleting through base pointer → prevents memory leak. |
| Q24 | **(C)** | ONLY `virtual void show() = 0;` is correct pure virtual syntax. Option B (`void show() = 0`) is missing `virtual` — it's NOT a valid pure virtual function. |
| Q25 | **(B)** | Statement 1 ✅ (one pure virtual = abstract). Statement 2 ✅ (friend functions access private). Statement 3 ❌ (`virtual` enables ONLY runtime polymorphism; compile-time uses overloading/templates). |

---

## GS/GK ANSWERS (Q26–Q50)

| Q# | Answer | Key Explanation |
|----|--------|----------------|
| Q26 | **(C)** | 15% of 200 = (15 × 200)/100 = 3000/100 = **30** |
| Q27 | **(C)** | Profit = SP–CP = 50–40 = 10; Profit% = (10/40)×100 = **25%** |
| Q28 | **(A)** | A:B=3:4, B:C=2:3. Make B common: A:B=6:8, B:C=8:12 → A:C = 6:12 = **1:2** |
| Q29 | **(C)** | **Dadabhai Naoroji** = Grand Old Man of India. Gokhale was Gandhi's political mentor. |
| Q30 | **(B)** | **Yeast** reproduces by budding. Amoeba = binary fission. Fern = spores. |
| Q31 | **(C)** | Net % = a + b + ab/100 = 20 + (–20) + (20×–20)/100 = 0 – 4 = **–4% (4% decrease)** |
| Q32 | **(B)** | CP = 100; MP = 125 (25% above CP); Discount 10% → SP = 125×0.9 = 112.5; Profit = 12.5% |
| Q33 | **(C)** | Old sum = 5×25 = 125; New sum = 125 – 25 + 45 = 145; New avg = 145/5 = **29** |
| Q34 | **(D)** | 121: (1+1)–2=0 ✅; 132: (1+2)–3=0 ✅; 143: (1+3)–4=0 ✅. All divisible by 11. Hence D. |
| Q35 | **(B)** | Other = (HCF×LCM)/Known = (10×120)/40 = 1200/40 = **30** |
| Q36 | **(C)** | Non-Cooperation Movement launched by Gandhi in **1920**. (Champaran=1917, Jallianwala=1919) |
| Q37 | **(C)** | When light changes medium, only **frequency** remains unchanged. Speed and wavelength change. |
| Q38 | **(C)** | **Bhagalpur** = "Silk City" of Bihar; famous for Tussar silk. Rohtas = paddy. |
| Q39 | **(B)** | Anushilan Samiti Patna (1913) founded by **Sachindra Nath Sanyal**. |
| Q40 | **(C)** | Photoperiodism (effect of light duration on flowering) discovered by **Garner and Allard** (1920). |
| Q41 | **(B)** | Let CP1=x, CP2=1800–x. SP1 = x×1.2, SP2 = (1800–x)×0.8. Equal SP: 1.2x = 0.8(1800–x) → 1.2x = 1440–0.8x → 2x=1440 → x=**₹800** (sold at 20% profit) |
| Q42 | **(A)** | Profit ratio = (12000×6):(8000×9) = 72000:72000 = **1:1** |
| Q43 | **(B)** | LCM(16,24,36) = 144; Answer = 144 + 7 = **151** |
| Q44 | **(B)** | Same distance at different speeds → Avg speed = 2S1S2/(S1+S2) = 2×50×100/(50+100) = 10000/150 = **66.67 km/h** |
| Q45 | **(C)** | All three are correctly matched: Champaran 1917 Bihar ✅, Bardoli 1928 Gujarat ✅, Salt March/Dandi 1930 Gujarat ✅ |
| Q46 | **(B)** | LCM(12,15,18)=180. Smallest 4-digit multiple: 180×6=1080. ✅ Check: 1080/12=90 ✅, 1080/15=72 ✅, 1080/18=60 ✅ |
| Q47 | **(B)** | During inhalation, diaphragm becomes **flattened** (moves downward, NOT upward). Ribs expand outward (not inward). |
| Q48 | **(B)** | Bihar = 8.58% of India's population (Census 2011). It is NOT highest density (Delhi is) and NOT smallest state. |
| Q49 | **(C)** | Co-prime numbers have HCF = **1** (by definition). If their product = 117, they share no common factor. |
| Q50 | **(C)** | A ✅ (first session Bombay 1885), B ✅ (W.C. Bonnerjee first president), C ✅ (Dadabhai Naoroji's 1906 Calcutta session first demanded Swaraj). All three correct → **(C)** |

---

---

# 📝 DAY 7 — NIGHT REVISION SUMMARY
## Write ALL 15 points from memory without looking:

```
OOP PILLARS (4):
1. Encapsulation = data hiding (access specifiers)
2. Abstraction = implementation hiding (abstract class/interface)
3. Inheritance = IS-A relationship; C++ uses ':', Java uses 'extends'
4. Polymorphism = same name, many forms; Overloading=compile-time, Overriding=runtime

ACCESS SPECIFIERS (3):
5. private = same class only
6. protected = same class + derived classes
7. public = everywhere; struct default=public, class default=private

INHERITANCE (3):
8. 5 types: Single, Multiple, Multilevel, Hierarchical, Hybrid
9. Diamond problem → solved by virtual inheritance
10. NOT inherited: constructors, destructors, friend functions

CONSTRUCTORS & DESTRUCTORS (5):
11. Constructor: no return type, cannot be virtual
12. Destructor: only one per class, CAN be virtual, no parameters
13. Constructor order: Base → Derived
14. Destructor order: Derived → Base (LIFO)
15. Default copy constructor = Shallow copy; pointer classes need Deep copy

MATHS FORMULAS:
16. Profit% = (Profit/CP) × 100
17. Avg speed (same distance) = 2S1S2/(S1+S2)
18. % change twice: a + b + ab/100
```

---

## ⏰ DAY 7 TIME PLAN:
| Slot | Duration | Activity |
|------|----------|---------|
| Morning | 1.5 hrs | Re-read Trap Table + all concept diagrams (R1 to R6) |
| Afternoon | 1 hr | Revise GS Maths (GS1–GS6) + GK rapid fire table |
| Evening | 1 hr | Solve all 50 MCQs strictly (NO peeking!) |
| Night | 30 min | Check answers → Score yourself → Write Night Summary (15 points above) |

---

## 🏆 TOPPER SELF-ASSESSMENT SCORECARD — WEEK 1:

| Day | Topic | Target Score | Your Score |
|-----|-------|-------------|-----------|
| Day 1 | OOP 4 Pillars + Class/Object | 8/10 | ___/10 |
| Day 2 | Encapsulation + Abstraction | 8/10 | ___/10 |
| Day 3 | Inheritance Types | 8/10 | ___/10 |
| Day 4 | Virtual Inheritance + Diamond | 8/10 | ___/10 |
| Day 5 | Polymorphism | 8/10 | ___/10 |
| Day 6 | Constructors + Destructors | 8/10 | ___/10 |
| Day 7 | Full Week Revision (today) | 45/50 | ___/50 |

If Day 7 score < 40/50 → Revisit whichever day's topic gave wrong answers and read it again tonight.
If Day 7 score = 45+/50 → You are on TOPPER track. Move to Week 2 (Day 8) with confidence!

---

## 🚀 COMING NEXT — DAY 8:
**CS Topic:** C++ Basics — Variables, Data Types, Naming Rules, sizeof(), Header Files
**GS Topic:** Modern Indian History — Champaran to Non-Cooperation Movement (Bihar Focus)

*Day 7 Complete | OOP Week 1 DONE ✅ | Week 2 starts tomorrow*
*Phase 1 Progress: 7/60 days | Target Score Track: Stay above 80% in daily MCQs*
*You are building exam-ready knowledge — every day counts! 🎯*
