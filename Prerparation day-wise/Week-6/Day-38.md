# 📅 BPSC TRE 4.0 — DAY 38 COMPLETE STUDY MODULE
### ER Model & Relational Model + Black Soil & Cotton Belt (Geography)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): ER Model & Relational Model — Entities, Attributes, Relationships, Diagrams, Conversion
> - Afternoon (1 hr): Geography — Black Soil (Regur), Cotton Belt, Regions, Characteristics
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 ER Model & Relational Model — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is the ER Model?

### Real-Life Analogy — The Blueprint Before the Building:

Before constructing a building, an architect draws a **blueprint** — a detailed plan showing rooms, walls, doors, and how everything connects. Nobody builds without a blueprint.

A database is a complex structure. Before writing a single line of SQL, a database designer draws an **ER Diagram** — the blueprint of the database.

> **ER Model (Entity-Relationship Model) is a high-level conceptual data model used to describe the STRUCTURE of a database — what data exists, and how different pieces of data are RELATED to each other.**

### Why ER Model Exists:
```
THE PROBLEM: A hospital wants to build a database.
  → Patients, Doctors, Medicines, Appointments, Wards...
  → How do you decide which tables to make?
  → How do they connect?
  → What data goes in each table?
  
WITHOUT ER MODEL: Jump straight to coding → chaos, mistakes, redesigns
WITH ER MODEL:    Draw the diagram first → clear plan → clean database

ER MODEL = DESIGN TOOL (not the actual database!)
           It helps you VISUALISE before you IMPLEMENT.
```

### Who Proposed ER Model?
```
PROPOSED BY: Peter Chen (1976)
PAPER TITLE: "The Entity-Relationship Model: Toward a Unified View of Data"
YEAR:        1976

🎯 PYQ FACT: ER Model was proposed by Peter Chen in 1976.
```

---

## 🔷 SECTION 2: Three Core Components of ER Model

The ER Model has exactly THREE fundamental building blocks:

```
         ER MODEL
        /    |    \
       /     |     \
  ENTITY  ATTRIBUTE  RELATIONSHIP
  "What"   "Detail"   "Connection"
  (thing)  (property)  (association)
```

---

## 🔷 SECTION 3: ENTITIES

### Definition:
> **An Entity is any real-world OBJECT or THING that has an independent existence and about which we want to store data.**

### Real-World Examples:
```
HOSPITAL DATABASE:
  Entity: PATIENT    → a real patient who exists
  Entity: DOCTOR     → a real doctor who exists
  Entity: WARD       → a real ward in the hospital
  Entity: MEDICINE   → a real medicine product

SCHOOL DATABASE:
  Entity: STUDENT    → a real enrolled student
  Entity: TEACHER    → a real teaching staff member
  Entity: COURSE     → a real course being taught
  Entity: CLASSROOM  → a real physical room

LIBRARY DATABASE:
  Entity: BOOK       → a real book on the shelf
  Entity: MEMBER     → a real library member
  Entity: BRANCH     → a real library branch location
```

### Entity Set vs Entity Instance:
```
ENTITY SET = The entire COLLECTION (like the table itself)
ENTITY INSTANCE = One specific object (like one row)

Example:
  STUDENT (entity set) = all students enrolled
  "Ravi Kumar, Roll No 101, CS dept" = one ENTITY INSTANCE

ANALOGY:
  Entity Set  = Template/Blueprint of a class of objects
  Instance    = One specific object of that class
  
  Like: "STUDENT" is the class definition
        Ravi Kumar is one object of that class
```

---

### TYPE 1: STRONG ENTITY

```
STRONG ENTITY = An entity that has its OWN Primary Key.
                It can EXIST INDEPENDENTLY — does not need
                another entity to define its identity.

SYMBOL IN ER DIAGRAM: Rectangle (single border)
  ┌───────────┐
  │  STUDENT  │
  └───────────┘

EXAMPLES:
  STUDENT  → has Roll Number (own PK) → strong
  DOCTOR   → has DoctorID (own PK) → strong
  PRODUCT  → has ProductID (own PK) → strong
  EMPLOYEE → has EmployeeID (own PK) → strong

KEY CHARACTERISTIC:
  Can be deleted without affecting other entities' existence.
  Has a unique identifier of its own.
```

---

### TYPE 2: WEAK ENTITY

```
WEAK ENTITY = An entity that CANNOT be uniquely identified
               by its OWN attributes alone.
               It DEPENDS on another entity (its "owner" or
               "identifying entity") for its existence and identity.

SYMBOL IN ER DIAGRAM: Double Rectangle (double border)
  ╔═══════════════╗
  ║  DEPENDENT    ║  ← double border = weak entity
  ╚═══════════════╝

CLASSIC EXAMPLE:
  EMPLOYEE and DEPENDENT (family members of employee)
  
  An employee's DEPENDENT (child/spouse):
    → Has: Name, Age, Relationship
    → But: "Priya, age 5, daughter" could be Ravi's daughter
              AND also be Aman's daughter!
    → Without knowing WHICH employee she belongs to,
      we CANNOT uniquely identify her!
    → She DEPENDS on EMPLOYEE for identity.

ANOTHER EXAMPLE:
  ORDER and ORDER_ITEM:
    → ORDER_ITEM has: Item Number (1, 2, 3...)
    → "Item Number 1" exists in EVERY order!
    → Without the parent OrderID, Item 1 is ambiguous.
    → ORDER_ITEM depends on ORDER.

RULES FOR WEAK ENTITY:
  1. Must have a "strong entity" as its owner/identifier
  2. Connected to its owner by an IDENTIFYING RELATIONSHIP
  3. Has a PARTIAL KEY (discriminator) — uniquely identifies
     it WITHIN the context of its owner
  4. Full key = Owner's PK + Partial Key
```

### Strong vs Weak Entity Comparison:
```
┌──────────────────────────┬──────────────────────────────────────┐
│      STRONG ENTITY       │           WEAK ENTITY                │
├──────────────────────────┼──────────────────────────────────────┤
│ Has its OWN primary key  │ No primary key of its own            │
├──────────────────────────┼──────────────────────────────────────┤
│ Exists independently     │ Depends on strong entity to exist    │
├──────────────────────────┼──────────────────────────────────────┤
│ Single rectangle in ER   │ Double rectangle in ER diagram       │
├──────────────────────────┼──────────────────────────────────────┤
│ Example: EMPLOYEE        │ Example: DEPENDENT (of employee)     │
│ Example: STUDENT         │ Example: ORDER_ITEM (of ORDER)       │
│ Example: PRODUCT         │ Example: ROOM (of HOTEL BOOKING?)    │
├──────────────────────────┼──────────────────────────────────────┤
│ Can be deleted freely    │ If owner deleted → weak entity       │
│                          │ is also deleted (CASCADE)            │
└──────────────────────────┴──────────────────────────────────────┘
```

### 🎯 PYQ FACT: A Weak Entity depends on a Strong Entity for its existence and identity. It has a Partial Key, not a full Primary Key.

---

## 🔷 SECTION 4: ATTRIBUTES

### Definition:
> **An Attribute is a PROPERTY or CHARACTERISTIC of an entity that we want to store in the database.**

```
ENTITY: STUDENT
ATTRIBUTES: Roll Number, Name, Date of Birth, Age, Email, Phone, Department

Each attribute describes one aspect of the entity.
Roll Number describes "which student", Name describes "what they're called", etc.
```

### ER Diagram Symbol: Oval (ellipse)
```
    ┌───────────┐
    │  STUDENT  │ ← Entity (rectangle)
    └─────┬─────┘
          │
    ┌─────┴───────────────────────────────┐
    │     │        │          │           │
  (RollNo) (Name) (Email)  (Phone)  (DateOfBirth)
  ← Ovals/Ellipses for attributes
```

---

### TYPE 1: SIMPLE (ATOMIC) ATTRIBUTE

```
DEFINITION: An attribute that CANNOT be divided further into meaningful parts.
            It is the most basic, indivisible unit of data.

EXAMPLES:
  → Roll Number     (101 — just a number, can't be divided further)
  → Employee ID     (E001 — atomic identifier)
  → Marks           (85 — just a score)
  → Gender          (Male/Female — simple value)
  → Age             (25 — a number)
  → Account Number  (123456789 — atomic)

ER SYMBOL: Simple oval
    ( RollNo )
```

---

### TYPE 2: COMPOSITE ATTRIBUTE

```
DEFINITION: An attribute that CAN be divided into smaller meaningful sub-parts.
            Each sub-part has its own meaning and can be stored separately.

CLASSIC EXAMPLE: NAME
  "Ravi Kumar Sharma" can be divided into:
  → First Name:  Ravi
  → Middle Name: Kumar
  → Last Name:   Sharma
  
  Why divide? So you can search by Last Name, sort by First Name, etc.

OTHER EXAMPLES:
  ADDRESS → HouseNo + Street + City + State + PIN Code
  DATE    → Day + Month + Year
  PHONE   → Country Code + Area Code + Number

ER SYMBOL: Oval with sub-ovals attached
    
            ( Name )
           /    |    \
    (FirstName) (MI) (LastName)

            ( Address )
         /      |      \
    (Street)  (City)  (PinCode)

🎯 PYQ FACT: Composite Attribute = can be broken into sub-attributes with their own meaning.
```

---

### TYPE 3: DERIVED ATTRIBUTE

```
DEFINITION: An attribute whose VALUE CAN BE CALCULATED or DERIVED
            from another attribute. It is NOT stored directly in the database
            — it is computed on demand.

WHY? Storing derived data wastes space and causes inconsistency.
     Better to calculate it when needed!

CLASSIC EXAMPLE:
  STUDENT entity:
    DateOfBirth = 15 November 1999  → STORED (base attribute)
    Age = Current Year - Birth Year → DERIVED (calculated, not stored)
  
  If Age were stored:
    → It would become WRONG every year!
    → Someone would need to update it manually
    → Better to CALCULATE from DateOfBirth each time

OTHER EXAMPLES:
  → TotalMarks: derived from individual subject marks
  → TenureYears: derived from JoiningDate and CurrentDate
  → TotalPrice: derived from Quantity × UnitPrice
  → BMI: derived from Height and Weight

ER SYMBOL: DASHED oval (key distinguisher!)
    
    (- - - - - -)
    (   Age    )   ← dashed oval = derived attribute
    (- - - - - -)

🎯 PYQ FACT: Derived Attribute uses a DASHED oval in ER diagrams.
             It is calculated from stored attributes, not stored itself.
```

---

### TYPE 4: MULTIVALUED ATTRIBUTE

```
DEFINITION: An attribute that can have MULTIPLE VALUES for a single entity.
            One entity → more than one value for this attribute.

CLASSIC EXAMPLE:
  STUDENT entity:
    Phone Number → A student might have:
      - Personal mobile: 9876543210
      - Home phone: 0612-2345678
      - WhatsApp number: 9123456789
    → MULTIPLE phone numbers → Multivalued attribute!

OTHER EXAMPLES:
  EMPLOYEE:
    Skills → {Java, Python, SQL, Machine Learning}
    → An employee can have many skills
  
  PERSON:
    Email → {work@company.com, personal@gmail.com}
    → One person, multiple emails
  
  BOOK:
    Authors → {Author1, Author2, Author3}
    → A book can have multiple authors

ER SYMBOL: DOUBLE oval (two concentric ovals)
    
    ((  Phone  ))   ← double oval = multivalued attribute

HOW IS IT STORED IN DATABASE?
  → Can't store in a single column (violates 1NF!)
  → Solution: Create a SEPARATE TABLE
    STUDENT_PHONE (RollNo [FK], PhoneNumber)
    One row per phone number per student.

🎯 PYQ FACT: Multivalued Attribute uses a DOUBLE oval in ER diagrams.
```

### All Attribute Types — Summary:
```
┌──────────────────┬──────────────────────────┬──────────────────────┐
│  ATTRIBUTE TYPE  │       DEFINITION         │    ER SYMBOL         │
├──────────────────┼──────────────────────────┼──────────────────────┤
│ Simple/Atomic    │ Cannot be divided further │ Single oval          │
│                  │                          │ ( RollNo )           │
├──────────────────┼──────────────────────────┼──────────────────────┤
│ Composite        │ Can be divided into       │ Oval with sub-ovals  │
│                  │ meaningful sub-parts      │ (Name)→(First)(Last) │
├──────────────────┼──────────────────────────┼──────────────────────┤
│ Derived          │ Calculated from another   │ Dashed/dotted oval   │
│                  │ stored attribute          │ (- Age -)            │
├──────────────────┼──────────────────────────┼──────────────────────┤
│ Multivalued      │ Can have multiple values  │ Double oval          │
│                  │ per entity                │ (( Phone ))          │
└──────────────────┴──────────────────────────┴──────────────────────┘

MEMORY TRICK: "SCDM" — Simple, Composite, Derived, Multivalued
              Simple=Single oval | Composite=Sub-ovals | Derived=Dashed | Multi=Double
```

---

## 🔷 SECTION 5: RELATIONSHIPS

### Definition:
> **A Relationship is an ASSOCIATION or CONNECTION between two or more entities.**

```
EXAMPLE:
  STUDENT entity ←—ENROLLED IN—→ COURSE entity
  DOCTOR entity  ←—TREATS—→      PATIENT entity
  EMPLOYEE entity ←—WORKS IN—→   DEPARTMENT entity

ER SYMBOL: Diamond shape
    ┌─────────────┐    ◇          ┌─────────────┐
    │   STUDENT   │——(ENROLLED)——│   COURSE    │
    └─────────────┘              └─────────────┘
```

---

### DEGREE OF RELATIONSHIP (Number of Entities Involved):

#### UNARY (Degree 1) — Self-Relationship:
```
DEFINITION: A relationship between instances of the SAME entity set.
            One entity type relates to itself.

EXAMPLE: EMPLOYEE "manages" EMPLOYEE
  → An employee can be a MANAGER of other employees
  → Both manager and subordinate are from the EMPLOYEE entity
  
  ┌─────────────┐
  │  EMPLOYEE   │◄─────────────────┐
  └──────┬──────┘                  │
         │                         │
         └──────(MANAGES)──────────┘
         (connects back to itself)

OTHER EXAMPLES:
  → PERSON "is married to" PERSON
  → COURSE "is prerequisite of" COURSE
  → PRODUCT "is part of" PRODUCT (bill of materials)
```

#### BINARY (Degree 2) — Most Common:
```
DEFINITION: A relationship between TWO different entity sets.
            This is the most common type in real databases.

EXAMPLE: STUDENT ——(ENROLLED IN)——→ COURSE
         DOCTOR ——(TREATS)——→ PATIENT
         EMPLOYEE ——(WORKS IN)——→ DEPARTMENT

    ┌─────────────┐         ┌─────────────┐
    │   STUDENT   │◇ENROLLS│   COURSE    │
    └─────────────┘         └─────────────┘

🎯 PYQ FACT: Binary relationships are the MOST COMMON degree in ER diagrams.
```

#### TERNARY (Degree 3):
```
DEFINITION: A relationship among THREE different entity sets simultaneously.
            All three entities participate together.

EXAMPLE: DOCTOR prescribes MEDICINE to PATIENT
  → The prescription involves all 3: a specific DOCTOR 
    prescribing a specific MEDICINE to a specific PATIENT
  → It's not just DOCTOR-MEDICINE (without knowing which patient)
  → It's not just MEDICINE-PATIENT (without knowing which doctor)
  → All three together form one meaningful unit!

         ┌──────────┐
         │  DOCTOR  │
         └────┬─────┘
              │
         ┌────┴──────────┐
         │  PRESCRIBES   │ ← Ternary relationship
         └────┬──────┬───┘
              │      │
    ┌─────────┴─┐  ┌─┴──────────┐
    │ MEDICINE  │  │  PATIENT   │
    └───────────┘  └────────────┘
```

---

## 🔷 SECTION 6: CARDINALITY OF RELATIONSHIPS

### Definition:
> **Cardinality specifies how many instances of one entity can be associated with how many instances of another entity.**

---

### 1:1 (ONE-TO-ONE):
```
DEFINITION: One instance of Entity A is associated with AT MOST one instance of Entity B.

EXAMPLE: PERSON ——(HAS)——→ PASSPORT
  → One person has at most ONE passport
  → One passport belongs to at most ONE person

         PERSON          HAS           PASSPORT
    ┌───────────┐    ┌──────────┐   ┌───────────┐
    │  Ravi     │────│    1:1   │───│ P-101     │
    │  Priya    │    └──────────┘   │ P-102     │
    │  Aman     │                   │ P-103     │
    └───────────┘                   └───────────┘
    Each person has exactly ONE passport; each passport has ONE owner.

OTHER EXAMPLES:
  → EMPLOYEE ——(HAS)——→ EMPLOYEE_PROFILE (one-to-one profile)
  → COUNTRY ——(HAS CAPITAL)——→ CITY (one country, one capital)
  → HUSBAND ——(MARRIED TO)——→ WIFE (in monogamous marriage)
```

---

### 1:N (ONE-TO-MANY):
```
DEFINITION: One instance of Entity A can be associated with MANY instances of Entity B,
            but each instance of B is associated with AT MOST ONE instance of A.

EXAMPLE: DEPARTMENT ——(HAS)——→ EMPLOYEE
  → One department can have MANY employees
  → Each employee belongs to ONLY ONE department

    DEPARTMENT               HAS                 EMPLOYEES
    ┌──────────┐         ┌────────────┐       ┌────────────┐
    │ CS Dept  │────────→│            │──────→│ Ravi       │
    │          │         │    1:N     │──────→│ Priya      │
    │          │         │            │──────→│ Aman       │
    ├──────────┤         └────────────┘       ├────────────┤
    │Math Dept │────────────────────────────→ │ Kavya      │
    └──────────┘                              └────────────┘
    CS Dept → Ravi, Priya, Aman (many employees)
    Ravi → only CS Dept (one department)

OTHER EXAMPLES:
  → TEACHER ——(TEACHES)——→ STUDENT (one teacher, many students)
  → COUNTRY ——(HAS)——→ CITY (one country, many cities)
  → ORDER ——(CONTAINS)——→ ORDER_ITEMS (one order, many items)
  → PARENT ——(HAS)——→ CHILD (one parent, many children)
```

---

### M:N (MANY-TO-MANY):
```
DEFINITION: MANY instances of Entity A can be associated with MANY instances of Entity B.

EXAMPLE: STUDENT ——(ENROLLED IN)——→ COURSE
  → One student can enroll in MANY courses
  → One course can have MANY students

    STUDENTS              ENROLLED IN            COURSES
    ┌────────┐            ┌─────────┐          ┌─────────┐
    │ Ravi   │────────────│         │──────────│ CS101   │
    │        │     ╲      │   M:N   │      ╱   │         │
    │ Priya  │──────╲─────│         │─────╱────│ Math101 │
    │        │       ╲    └─────────┘    ╱     │         │
    │ Aman   │────────╲────────────────╱───────│ Phys101 │
    └────────┘         (criss-cross connections)└─────────┘
    
    Ravi → CS101, Math101, Phys101
    CS101 → Ravi, Priya, Aman
    → Many-to-many!

HOW TO HANDLE M:N IN RELATIONAL DATABASE:
  → Cannot be directly represented in two tables!
  → SOLUTION: Create an INTERMEDIATE (JUNCTION) TABLE
  
  ENROLLMENT TABLE:
  ┌────────────┬────────────┬───────┬───────┐
  │ RollNo[FK] │CourseID[FK]│ Marks │ Grade │
  ├────────────┼────────────┼───────┼───────┤
  │    101     │   CS101    │  85   │   A   │
  │    101     │  Math101   │  90   │  A+   │
  │    102     │   CS101    │  78   │  B+   │
  └────────────┴────────────┴───────┴───────┘
  Primary Key = {RollNo + CourseID} = COMPOSITE KEY

OTHER M:N EXAMPLES:
  → DOCTOR ——(TREATS)——→ PATIENT (many doctors, many patients)
  → ACTOR ——(ACTS IN)——→ MOVIE
  → SUPPLIER ——(SUPPLIES)——→ PRODUCT
```

### Cardinality Summary:
```
┌───────────┬──────────────────────────────┬──────────────────────┐
│CARDINALITY│          MEANING             │    REAL EXAMPLE      │
├───────────┼──────────────────────────────┼──────────────────────┤
│   1 : 1   │ One ↔ One                    │ Person ↔ Passport    │
├───────────┼──────────────────────────────┼──────────────────────┤
│   1 : N   │ One → Many                   │ Dept → Employees     │
│           │ (many belong to one)         │ Parent → Children    │
├───────────┼──────────────────────────────┼──────────────────────┤
│   M : N   │ Many ↔ Many                  │ Students ↔ Courses   │
│           │ (requires junction table)    │ Actors ↔ Movies      │
└───────────┴──────────────────────────────┴──────────────────────┘
```

---

## 🔷 SECTION 7: PARTICIPATION CONSTRAINTS

### Definition:
> **Participation Constraints specify whether ALL instances of an entity must participate in a relationship, or only SOME.**

---

### TOTAL PARTICIPATION:
```
DEFINITION: EVERY instance of the entity MUST participate in the relationship.
            "No entity left behind."

NOTATION IN ER DIAGRAM: Double line (=====)

EXAMPLE: EMPLOYEE ═══(WORKS FOR)═══ DEPARTMENT
  → EVERY employee MUST work for some department
  → An employee cannot exist in the company without belonging to a department!
  → Total participation of EMPLOYEE in WORKS FOR

EMPLOYEE entity:
  Ravi    → must be in some department ✓
  Priya   → must be in some department ✓
  Aman    → must be in some department ✓
  NO employee exists without a department!
  → TOTAL participation

ER NOTATION:
  ┌──────────────┐                     ┌──────────────┐
  ║  EMPLOYEE   ║═════(WORKS FOR)═════│  DEPARTMENT  │
  └──────────────┘                     └──────────────┘
  Double line on EMPLOYEE side = total participation
```

### PARTIAL PARTICIPATION:
```
DEFINITION: SOME instances of the entity may NOT participate in the relationship.
            Not all instances are required to be part of the relationship.

NOTATION IN ER DIAGRAM: Single line (——)

EXAMPLE: EMPLOYEE ——(MANAGES)—— DEPARTMENT
  → NOT every employee is a manager
  → Some employees are regular staff (don't manage anything)
  → Only SOME employees participate in MANAGES relationship
  → Partial participation of EMPLOYEE in MANAGES

ER NOTATION:
  ┌──────────────┐                     ┌──────────────┐
  │  EMPLOYEE   │────(MANAGES)─────────│  DEPARTMENT  │
  └──────────────┘                     └──────────────┘
  Single line = partial participation (some employees, not all, are managers)
```

---

## 🔷 SECTION 8: Complete ER Diagram Example — School Database

```
SCHOOL DATABASE ER DIAGRAM:

Legend:
  Rectangle (─┐)   = Strong Entity
  Dbl Rectangle (═╗) = Weak Entity
  Oval ( )         = Simple Attribute
  Dashed Oval (- -) = Derived Attribute
  Double Oval (( )) = Multivalued Attribute
  Diamond ◇        = Relationship
  Dbl Diamond ◈    = Identifying Relationship (for weak entity)
  ==== Double line = Total Participation
  ──── Single line = Partial Participation

                    ( Name )   ( Email )   (( Phone ))
                        \          |          /
                         \         |         /
        (- Age -)         ┌────────┴────────┐         ( Marks )
               \          │    STUDENT      │               \
                └──────── │   [Roll No*]   │                │
                           └────────┬───────┘                │
                                    ║                         │
                                    ║ (total participation)   │
                                    ║                         │
                               ◇ENROLLED◇─── (Semester) ────┘
                                    │
                                    │ (partial participation)
                           ┌────────┴────────┐
                           │    COURSE       │
                           │  [CourseID*]    │
                           └────────┬────────┘
                         /          |          \
                    (Title)     (Credits)    (Department)

Separately:
                           ┌────────────────┐
                           │    TEACHER     │
                           │  [TeacherID*]  │
                           └───────┬────────┘
                                   │
                              ◇TEACHES◇ (1:N)
                                   │
                           ┌───────┴────────┐
                           │    COURSE      │
                           └────────────────┘

    ┌──────────────────┐        ┌────────────────┐
    ║  DEPENDENT      ║◈═══════│   EMPLOYEE     │
    ║ [Emp_ID+Dep_Name]║        │  [EmployeeID*] │
    ╚══════════════════╝        └────────────────┘
       Weak Entity                Strong Entity

* = Primary Key attribute (underlined in ER notation)
```

---

## 🔷 SECTION 9: RELATIONAL MODEL

### Definition:
> **The Relational Model is a way of REPRESENTING data as a collection of TABLES (relations), where each table has rows (tuples) and columns (attributes).**

### Key Terminology:
```
┌──────────────────────┬───────────────────────────────────────────────────┐
│    FORMAL TERM       │           MEANING / INFORMAL TERM                 │
├──────────────────────┼───────────────────────────────────────────────────┤
│ RELATION             │ TABLE (a 2D structure with rows and columns)       │
├──────────────────────┼───────────────────────────────────────────────────┤
│ TUPLE                │ ROW (one complete record in a table)               │
├──────────────────────┼───────────────────────────────────────────────────┤
│ ATTRIBUTE            │ COLUMN (one property/field in the table)           │
├──────────────────────┼───────────────────────────────────────────────────┤
│ DOMAIN               │ Set of all valid values an attribute can take      │
│                      │ (like a constraint on data type and range)         │
├──────────────────────┼───────────────────────────────────────────────────┤
│ DEGREE               │ Number of ATTRIBUTES (columns) in a relation       │
├──────────────────────┼───────────────────────────────────────────────────┤
│ CARDINALITY          │ Number of TUPLES (rows) in a relation              │
├──────────────────────┼───────────────────────────────────────────────────┤
│ SCHEMA               │ Structure/definition of a table (blueprint)        │
│                      │ → Doesn't change often                            │
├──────────────────────┼───────────────────────────────────────────────────┤
│ INSTANCE             │ Actual data in the table at a specific moment      │
│                      │ → Changes with every insert/delete/update         │
├──────────────────────┼───────────────────────────────────────────────────┤
│ METADATA             │ Data ABOUT data (schema, structure, constraints)   │
└──────────────────────┴───────────────────────────────────────────────────┘
```

### Visual Example — Relational Table:
```
STUDENTS RELATION (TABLE):

         DEGREE = 5 (5 columns/attributes)
              ↓
         ┌──────────┬──────────────┬──────────┬─────────┬───────┐
         │ Roll No  │     Name     │  Email   │  Dept   │ Marks │
SCHEMA → ├──────────┼──────────────┼──────────┼─────────┼───────┤ ← ATTRIBUTE NAMES
         │   101    │  Ravi Kumar  │ r@m.com  │   CS    │  85   │ ← TUPLE 1
         │   102    │  Priya Singh │ p@m.com  │  Math   │  90   │ ← TUPLE 2
         │   103    │  Aman Gupta  │ a@m.com  │   CS    │  78   │ ← TUPLE 3
         └──────────┴──────────────┴──────────┴─────────┴───────┘
                                                           ↑
                                            CARDINALITY = 3 (3 rows)

DOMAIN EXAMPLES:
  RollNo domain:  Positive integers (101, 102, 103, ...)
  Marks domain:   Integers from 0 to 100
  Dept domain:    {CS, Math, Phys, Chem, Bio, ...}
  Email domain:   Valid email format strings
```

### Schema vs Instance:
```
SCHEMA = The "blueprint" or structure definition

  STUDENTS (RollNo: INT, Name: VARCHAR(50), Email: VARCHAR(100), 
            Dept: VARCHAR(20), Marks: INT)
  
  This defines WHAT data goes where — but has no actual data.
  Schema = PERMANENT (changes only when table structure changes)

INSTANCE = The actual data at a specific point in time

  At 10 AM:                          At 10:05 AM (new student added):
  ┌───┬──────┬───┐                   ┌───┬──────┬───┐
  │101│ Ravi │85 │                   │101│ Ravi │85 │
  │102│Priya │90 │                   │102│Priya │90 │
  └───┴──────┴───┘                   │103│ Aman │78 │
                                     └───┴──────┴───┘
  Instance = DYNAMIC (changes constantly)

ANALOGY:
  Schema   = Recipe (ingredients, method — fixed)
  Instance = Dish prepared today (actual food — different each time)
```

### Metadata:
```
METADATA = "Data about Data"

Examples of Metadata:
  → Table name: "STUDENTS"
  → Number of columns: 5
  → Column names: RollNo, Name, Email, Dept, Marks
  → Data types: INT, VARCHAR, etc.
  → Constraints: PK = RollNo, NOT NULL, etc.
  → Number of rows: 3
  → Date last modified: 2024-01-15

WHAT IS NOT METADATA:
  → The actual student names (Ravi, Priya) = DATA
  → The actual marks (85, 90) = DATA
  
ANALOGY: Metadata = the label on a food package (ingredients list, weight, 
         expiry date — ABOUT the food, not the food itself)

🎯 PYQ FACT: Metadata = data about data. The database schema IS metadata.
```

---

## 🔷 SECTION 10: ER Model vs Relational Model

```
┌───────────────────────┬──────────────────────────┬──────────────────────────┐
│       FEATURE         │       ER MODEL            │    RELATIONAL MODEL      │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Purpose               │ DESIGN / CONCEPTUAL tool  │ IMPLEMENTATION model     │
│                       │ (blueprint)               │ (actual database)        │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Stage                 │ Before database creation  │ After ER design          │
│                       │ (planning stage)          │ (building stage)         │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Representation        │ ER Diagrams               │ Tables (Relations)       │
│                       │ (graphical)               │ (mathematical)           │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Main Components       │ Entities, Attributes,     │ Relations, Tuples,       │
│                       │ Relationships             │ Attributes, Domains      │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Proposed By           │ Peter Chen (1976)         │ E.F. Codd (1970)         │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Language              │ None (diagrammatic)       │ SQL / Relational Algebra │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Relationship handling │ Diamond shapes in diagram │ Junction/Bridge tables   │
│                       │ (explicit in diagram)     │ (for M:N)               │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Weak Entity           │ Shown as double rectangle │ Gets composite PK        │
│                       │ with double diamond       │ (own partial + owner PK) │
├───────────────────────┼──────────────────────────┼──────────────────────────┤
│ Level of Abstraction  │ HIGH (conceptual)         │ LOGICAL (closer to impl) │
└───────────────────────┴──────────────────────────┴──────────────────────────┘

🎯 PYQ FACT: ER Model was proposed by Peter Chen (1976).
             Relational Model was proposed by E.F. Codd (1970).
```

---

## 🔷 SECTION 11: ER to Relational Model Conversion — Flowchart

```
CONVERSION RULES:

STEP 1: STRONG ENTITY → TABLE
────────────────────────────────
  Each strong entity becomes ONE table.
  Attributes → columns.
  Primary Key attribute → Primary Key column.
  
  STUDENT entity → STUDENT(RollNo, Name, Email, Dept, Marks)
  COURSE entity  → COURSE(CourseID, Title, Credits)

STEP 2: WEAK ENTITY → TABLE (with composite PK)
────────────────────────────────────────────────
  Weak entity becomes a table.
  Include: owner's PK (as FK) + weak entity's partial key = COMPOSITE PK
  
  DEPENDENT (weak) of EMPLOYEE (strong):
  DEPENDENT(EmpID[FK], DepName, Age, Relationship)
  Composite PK = {EmpID + DepName}

STEP 3: COMPOSITE ATTRIBUTE → INDIVIDUAL COLUMNS
─────────────────────────────────────────────────
  Break composite attribute into its sub-attributes.
  Name → FirstName, MiddleName, LastName (separate columns)
  Address → Street, City, State, PinCode (separate columns)

STEP 4: MULTIVALUED ATTRIBUTE → SEPARATE TABLE
───────────────────────────────────────────────
  Cannot store multiple values in one column!
  Create new table with: entity's PK (FK) + the multivalued attribute
  
  STUDENT has (( Phone )):
  STUDENT_PHONE(RollNo[FK], PhoneNumber)
  PK = {RollNo + PhoneNumber}

STEP 5: DERIVED ATTRIBUTE → NOT STORED
─────────────────────────────────────────
  Derived attributes are NOT included as columns.
  They are calculated on-the-fly when needed.
  
  Age (derived from DateOfBirth) → NOT stored; compute when needed.

STEP 6: 1:1 RELATIONSHIP → MERGE or ADD FK
───────────────────────────────────────────
  Option A: Merge both entities into ONE table
  Option B: Add PK of one entity as FK in the other
  
  PERSON ——1:1——PASSPORT:
  Either: PERSON(PersonID, Name, PassportNo)  [PassportNo as FK]
  Or:     PASSPORT(PassportNo, IssueDate, PersonID[FK])

STEP 7: 1:N RELATIONSHIP → ADD FK to MANY side
─────────────────────────────────────────────────
  Add the PK of the "ONE" side as FK in the "MANY" side table.
  
  DEPARTMENT ——1:N——EMPLOYEE:
  DEPARTMENT(DeptID, DeptName)
  EMPLOYEE(EmpID, Name, DeptID[FK])   ← DeptID added to EMPLOYEE (many side)

STEP 8: M:N RELATIONSHIP → NEW TABLE
──────────────────────────────────────
  Create a new JUNCTION table.
  Junction table has: PK of Entity A (FK) + PK of Entity B (FK)
  Composite PK = {FK_A + FK_B}
  Also include any relationship attributes.
  
  STUDENT ——M:N——COURSE (via ENROLLED_IN with Marks, Semester):
  ENROLLMENT(RollNo[FK], CourseID[FK], Marks, Semester)
  Composite PK = {RollNo + CourseID}
```

### Visual Conversion Flowchart:
```
START: ER Diagram
          │
          ▼
    ┌─────────────┐
    │ Strong      │──────→ Create TABLE with all attributes
    │ Entity?     │         PK attribute = PK column
    └─────────────┘
          │
          ▼
    ┌─────────────┐
    │ Weak        │──────→ Create TABLE with owner's PK (FK) + partial key
    │ Entity?     │         Composite PK = {owner PK + partial key}
    └─────────────┘
          │
          ▼
    ┌─────────────┐
    │ Attribute   │
    │ Type?       │
    │             │──── Simple → Direct column
    │             │──── Composite → Multiple sub-columns
    │             │──── Derived → DON'T store, calculate
    │             │──── Multivalued → Separate TABLE
    └─────────────┘
          │
          ▼
    ┌─────────────┐
    │ Relationship│
    │ Cardinality?│
    │             │──── 1:1 → Merge or add FK
    │             │──── 1:N → Add FK to Many side
    │             │──── M:N → New junction table
    └─────────────┘
          │
          ▼
    Relational Schema (Tables) COMPLETE!
```

---

## 🔷 SECTION 12: Common PYQ Patterns and Traps

```
TRAP 1: "Metadata means the main data in a database"
  → FALSE! Metadata = DATA ABOUT DATA (structure, schema, definitions)
           The actual student names/marks = DATA (not metadata)

TRAP 2: "In relational model, tuple means column"
  → FALSE! Tuple = ROW; Attribute = COLUMN; Relation = TABLE

TRAP 3: "A weak entity has its own Primary Key"
  → FALSE! Weak entity has only a PARTIAL KEY.
           Full identification needs owner's PK + partial key.

TRAP 4: "Derived attribute is stored in the database"
  → FALSE! Derived attributes are CALCULATED, not stored.
           Age is derived from DateOfBirth — only DoB is stored.

TRAP 5: "Multivalued attribute is stored as one column"
  → FALSE! Multivalued attributes require a SEPARATE TABLE.
           Storing multiple values in one column violates 1NF.

TRAP 6: "Binary relationship involves more than two entities"
  → FALSE! Binary = EXACTLY TWO entities.
           Unary = 1, Binary = 2, Ternary = 3.

TRAP 7: "M:N relationship can be directly represented as two tables"
  → FALSE! M:N REQUIRES a junction/bridge/intermediate table.

TRAP 8: "ER Model and Relational Model are the same thing"
  → FALSE! ER Model = CONCEPTUAL design tool (diagrams).
           Relational Model = LOGICAL implementation (tables).

TRAP 9: "Degree of a relation = number of rows"
  → FALSE! Degree = number of COLUMNS.
           Cardinality = number of ROWS.

TRAP 10: "ER Model was proposed by E.F. Codd"
  → FALSE! ER Model = Peter Chen (1976).
           Relational Model = E.F. Codd (1970).
```

---

# PART 2: GENERAL STUDIES
## 🌍 Geography — Black Soil (Regur) & Cotton Belt

---

## 🔷 SECTION 1: What is Black Soil?

### Real-Life Analogy:

Imagine you're baking. You need a dough that stretches, holds moisture, is sticky, and is hard to work with when wet — but holds shape when dry. That's exactly what Black Soil does with water. It's the "sticky dough" of Indian soils.

### Definition:
> **Black Soil is a type of soil in India characterised by its DARK BLACK colour, HIGH MOISTURE RETENTION capacity, and exceptional suitability for COTTON cultivation. It is also called REGUR SOIL.**

---

## 🔷 SECTION 2: Formation and Origin

```
HOW IS BLACK SOIL FORMED?

SOURCE: Weathering and disintegration of BASALT ROCKS (volcanic/trap rock)
        from the Deccan Plateau's volcanic activity.

PROCESS:
  → Ancient volcanic eruptions deposited LAVA over the Deccan Plateau
  → Over millions of years, lava cooled and became BASALT ROCK
  → Weathering of basalt → BLACK coloured mineral-rich soil
  → The dark colour comes from TITANIFEROUS MAGNETITE (iron-titanium minerals)
    and compounds of ALUMINIUM and IRON

ALSO CALLED:
  → REGUR SOIL (most important name!)
  → COTTON SOIL (because of its use)
  → BLACK COTTON SOIL (most descriptive name)
  → LAVA SOIL or VOLCANIC SOIL (based on origin)
  → TROPICAL CHERNOZEMS (scientific classification)

🎯 PYQ FACT: "Regur" is the most commonly asked name for black soil.
             Origin = weathering of BASALT/VOLCANIC ROCKS.
             The dark colour = TITANIFEROUS MAGNETITE.
```

---

## 🔷 SECTION 3: Characteristics of Black Soil

### 1. MOISTURE RETENTION — The Most Important Feature:
```
BLACK SOIL'S SUPERPOWER: It can HOLD MOISTURE for VERY LONG periods.

WHY? 
  → Contains CLAY minerals — especially MONTMORILLONITE clay
  → Clay particles are extremely fine → large surface area → holds water
  → When wet: SWELLS and becomes STICKY (almost impossible to plough!)
  → When dry: SHRINKS and forms DEEP CRACKS (self-ploughing!)

THE SELF-PLOUGHING PHENOMENON:
  In summer: Black soil dries and cracks → deep fissures in the ground
  In monsoon: Cracks fill with surface soil/organic matter
  → NATURAL self-mixing action!
  
  This is why it's ideal for crops that need moisture during dry spells —
  the soil acts as a natural reservoir!
```

### 2. HIGH CLAY CONTENT:
```
  → 62% clay on average
  → Expansive nature: swells when wet (increases volume)
  → Shrinkage on drying causes characteristic deep cracks
  → Very sticky when moist → difficult for tilling
```

### 3. RICH IN MINERALS:
```
  PRESENT IN ABUNDANCE:
  → Iron (Fe)
  → Aluminium (Al)
  → Calcium Carbonate (CaCO₃) — makes it slightly alkaline
  → Magnesium (Mg)
  → Potassium (K)
  
  DEFICIENT IN:
  → Nitrogen (N) — major deficiency!
  → Phosphorus (P) — deficient
  → Humus/Organic matter — low organic content
  → Zinc

  RESULT: High mineral fertility but low nitrogen → cotton thrives 
          (cotton doesn't need as much nitrogen as cereals)
```

### 4. pH and ALKALINITY:
```
  → pH: 7.2 to 8.5 (NEUTRAL to SLIGHTLY ALKALINE)
  → Contains calcium carbonate → slight alkalinity
  → Not suitable for acidic-loving crops
  → Perfect for cotton (which prefers alkaline to neutral soil)
```

### 5. DEPTH:
```
  → Shallow (30-100 cm) in hilly areas
  → Deep (up to 600 cm / 6 metres!) in valley and basin areas
  → Depth = key indicator of fertility and water retention
```

### 6. COLOUR:
```
  → Deep BLACK to BROWNISH BLACK in deep layers
  → Lighter (grey-brown) in shallow layers
  → Darker = more fertile (more iron-titanium compounds)
```

### 7. SELF-PLOUGHING:
```
  UNIQUE FEATURE: When dry, black soil develops wide deep cracks.
  → Organic matter falls into these cracks
  → When it rains, cracks close → organic matter mixed inside
  → This is called SELF-PLOUGHING or "self-mulching"
  
  🎯 PYQ FACT: Self-ploughing / self-mulching is a UNIQUE characteristic
               of Black Soil (Regur soil).
```

---

## 🔷 SECTION 4: Geographical Distribution

### Where is Black Soil Found in India?
```
CORE REGION (Deccan Plateau — most extensive):
  → MAHARASHTRA (largest area under black soil)
  → MADHYA PRADESH (Malwa Plateau)
  → GUJARAT (Saurashtra, Kutch, Ahmedabad, Broach districts)
  → ANDHRA PRADESH (Krishna, Godavari deltas — upper parts)
  → TELANGANA (Rayalaseema, Nalgonda, Warangal)
  → KARNATAKA (northern districts — Bidar, Raichur, Dharwad)
  → RAJASTHAN (southeastern districts — Kota, Bundi, Jhalawar)
  → TAMIL NADU (parts of Coimbatore, Tiruchirapalli)
  → JHARKHAND and CHHATTISGARH (small pockets)
```

### Black Soil Distribution Map (Text Representation):
```
INDIA — BLACK SOIL REGIONS

              RAJASTHAN
              (SE corner - Kota)
                    │
    ┌───────────────┼─────────────────┐
    │    GUJARAT    │  MADHYA PRADESH │
    │  (Saurashtra) │  (Malwa Plateau)│
    │               │                 │
    └───────┬───────┘                 │
            │      MAHARASHTRA        │
            │   (LARGEST REGION)      │
            │  Nashik, Pune, Nagpur   │
            │  Aurangabad, Solapur    │
            └──────────┬──────────────┘
                       │
            ┌──────────┴──────────┐
            │      TELANGANA      │
            │       ANDHRA        │
            └──────────┬──────────┘
                       │
                  KARNATAKA
               (Northern districts)

Maharashtra = LARGEST AREA under black soil in India
```

### Area Coverage:
```
  → Covers approximately 5.46 LAKH square kilometres
  → About 16-17% of India's total geographical area
  → Second largest soil type after alluvial soil
  → Sometimes described as spreading over "6 lakh sq km" in different sources
```

---

## 🔷 SECTION 5: Why is Black Soil Perfect for Cotton?

```
COTTON REQUIREMENTS:          BLACK SOIL PROVIDES:
─────────────────────         ──────────────────────────────────────
High temperatures           ✅ Deccan Plateau = hot, dry climate
Low-to-moderate rainfall    ✅ 50-100 cm rainfall — perfect
Moisture during dry spell   ✅ Retains moisture through dry season
Well-drained but moist      ✅ Deep cracks drain excess; clay holds enough
Alkaline/neutral pH         ✅ pH 7.2-8.5 (slightly alkaline)
Iron-rich soil              ✅ Rich in iron compounds
Long growing season         ✅ Moisture retention extends the season

RESULT: Black soil IS cotton soil — the fit is almost perfect.

🎯 PYQ FACT: Black soil = COTTON soil. Cotton cultivation = KHARIF crop
             grown extensively in Maharashtra, Gujarat, MP on black soil.
```

---

## 🔷 SECTION 6: The Cotton Belt of India

```
THE COTTON BELT = Regions where COTTON is predominantly grown on BLACK SOIL

PRIMARY COTTON BELT STATES:
  1. MAHARASHTRA — Vidarbha, Marathwada regions
     → Nagpur, Akola, Amravati, Aurangabad = "Cotton City" regions
     → Vidarbha = largest cotton-growing region in India
  
  2. GUJARAT — Saurashtra peninsula, Ahmedabad, Vadodara
     → Surat = major textile/cotton city
     → Gujarat = often India's #1 in cotton production recently
  
  3. MADHYA PRADESH — Malwa Plateau
     → Indore, Ujjain, Dewas = cotton trading hubs
     
  4. TELANGANA — Warangal, Adilabad, Karimnagar
  
  5. ANDHRA PRADESH — Guntur, Kurnool
  
  6. RAJASTHAN — Sriganganagar, Hanumangarh (northwest; under irrigation)
  
  7. PUNJAB & HARYANA — under canal irrigation (non-black soil, irrigated cotton)
  
  8. KARNATAKA — Dharwad, Bellary
  
  9. TAMIL Nadu — Coimbatore (known as "Manchester of South India"!)

COIMBATORE = "Manchester of South India"
MUMBAI (historically) = "Cottonopolis of India" / "Manchester of India"
```

---

## 🔷 SECTION 7: Black Soil vs Other Soil Types

```
┌──────────────┬───────────────┬──────────────────┬──────────────────────┐
│   FEATURE    │  BLACK SOIL   │  ALLUVIAL SOIL   │    RED SOIL          │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Other names  │ Regur, Cotton │ Khadar, Bhangar  │ Laterite (related)   │
│              │ soil, Regur   │                  │                      │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Origin       │ Volcanic/Basalt│ River deposits   │ Iron-rich, leaching  │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Location     │ Deccan Plateau│ Indo-Gangetic     │ Eastern & Southern   │
│              │ Maharashtra,  │ Plains; river     │ Plateau, Tamil Nadu, │
│              │ Gujarat, MP   │ deltas            │ AP, Odisha           │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Moisture     │ HIGH          │ Moderate          │ LOW (porous)         │
│ Retention    │ retention     │                   │                      │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Best crop    │ Cotton        │ Rice, Wheat,      │ Millets, Pulses      │
│              │               │ Sugarcane         │                      │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Colour       │ Deep Black    │ Light Brown/Grey  │ Reddish-Brown        │
│ reason       │ Iron-titanium │ Mineral deposits  │ Iron oxide           │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Area         │ 2nd largest   │ LARGEST soil type │ 3rd largest          │
│              │ (~16%)        │ in India (~40%)   │                      │
├──────────────┼───────────────┼──────────────────┼──────────────────────┤
│ Special      │ Self-ploughing│ Most fertile      │ Rich in iron;        │
│ feature      │ (cracks when  │ (formed by rivers)│ poor in lime,        │
│              │ dry)          │                   │ humus, nitrogen      │
└──────────────┴───────────────┴──────────────────┴──────────────────────┘
```

---

## 🔷 SECTION 8: Memory Tricks for Black Soil

```
MEMORY TRICK 1 — "RCMDG" (states with major black soil):
  R = Rajasthan (SE corner)
  C = Cotton = Maharashtra (largest)
  M = MP (Malwa)
  D = Deccan = AP, Telangana, Karnataka
  G = Gujarat (Saurashtra)

MEMORY TRICK 2 — Characteristics: "CHAMPS":
  C = Clay-rich (expansive)
  H = High moisture retention
  A = Alkaline (slightly)
  M = Minerals (iron, calcium, magnesium rich)
  P = Poor in nitrogen
  S = Self-ploughing (cracks when dry)

MEMORY TRICK 3 — Black Soil Names:
  "REAL Cotton Gives Black Volcano Tropical Soil"
  R = Regur (official name)
  C = Cotton soil
  G = Given by Basalt/volcanic origin
  B = Black in colour
  V = Volcanic soil
  T = Tropical Chernozems
  S = Self-ploughing

MEMORY TRICK 4 — Origin:
  BASALT → BASALT WEATHERS → BLACK SOIL
  "Black comes from Basalt"
```

---

## 🔷 SECTION 9: Key PYQ Facts for Quick Revision

```
🎯 Black Soil = REGUR SOIL = BLACK COTTON SOIL
🎯 Origin: Weathering of BASALT/VOLCANIC rocks (Deccan Traps)
🎯 Colour: Dark colour from TITANIFEROUS MAGNETITE
🎯 Best crop: COTTON (that's why it's "cotton soil")
🎯 Clay mineral: MONTMORILLONITE (responsible for shrink-swell)
🎯 Self-ploughing: Unique feature — cracks in dry season, closes in monsoon
🎯 Rich in: Iron, calcium, magnesium, potassium, aluminium
🎯 Poor in: NITROGEN, Phosphorus, organic matter
🎯 pH: 7.2-8.5 (neutral to slightly alkaline)
🎯 Largest area: MAHARASHTRA (also Vidarbha = largest cotton belt)
🎯 Total area: ~5-6 lakh sq km (about 16% of India)
🎯 Coimbatore = "Manchester of South India" (cotton)
🎯 Mumbai = historically "Manchester of India" (cotton mills)
🎯 Gujarat = recently India's leading cotton producer
🎯 Black Soil = 2nd most extensive (after alluvial)
🎯 MONTMORILLONITE = expands when wet, shrinks when dry
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: ER Model, Relational Model, Entity Types, Attributes, Relationships, Conversion

---

**Q1.** The ER Model (Entity-Relationship Model) was proposed by:
(A) E.F. Codd in 1970
(B) Peter Chen in 1976
(C) Edgar Dijkstra in 1968
(D) More than one of the above
(E) None of the above

---

**Q2.** In an ER diagram, a WEAK ENTITY is represented by:
(A) A single rectangle
(B) A diamond shape
(C) A double rectangle (double border)
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following correctly describes a STRONG ENTITY?
(A) An entity with a very large number of records
(B) An entity that has its own Primary Key and exists independently
(C) An entity that connects two other entities in the ER diagram
(D) More than one of the above
(E) None of the above

---

**Q4.** "Age" attribute in a STUDENT entity is typically represented as a DERIVED attribute because:
(A) Age is not important for database purposes
(B) Age cannot be calculated mathematically
(C) Age can be computed from DateOfBirth — storing it leads to stale data
(D) More than one of the above
(E) None of the above

---

**Q5.** A MULTIVALUED ATTRIBUTE in an ER diagram is represented by:
(A) A dashed/dotted oval
(B) A double oval (two concentric ovals)
(C) A rectangle with double border
(D) More than one of the above
(E) None of the above

---

**Q6.** The "Address" attribute of a student is divided into Street, City, State, and PinCode. What type of attribute is "Address"?
(A) Simple attribute
(B) Derived attribute
(C) Composite attribute
(D) More than one of the above
(E) None of the above

---

**Q7.** In the Relational Model, a TUPLE refers to:
(A) A column in the table
(B) A row (one complete record) in a relation
(C) A data type constraint on an attribute
(D) More than one of the above
(E) None of the above

---

**Q8.** The DEGREE of a relation refers to:
(A) The number of rows (tuples) in the relation
(B) The number of columns (attributes) in the relation
(C) The level of normalisation of the table
(D) More than one of the above
(E) None of the above

---

**Q9.** CARDINALITY of a relation refers to:
(A) The number of primary keys in the table
(B) The number of columns in the table
(C) The number of rows (tuples) in the relation at a given time
(D) More than one of the above
(E) None of the above

---

**Q10.** METADATA in a database context means:
(A) The main business data stored in tables (customer names, order amounts)
(B) Data about data — structure, schema, column names, constraints
(C) The backup copy of the database
(D) More than one of the above
(E) None of the above

---

**Q11.** In a binary relationship DEPARTMENT ——(EMPLOYS)——→ EMPLOYEE with cardinality 1:N, which table gets the Foreign Key added to it?
(A) DEPARTMENT (the "ONE" side)
(B) EMPLOYEE (the "MANY" side)
(C) A new junction table is created for 1:N relationships
(D) More than one of the above
(E) None of the above

---

**Q12.** A TERNARY relationship involves:
(A) Three attributes of the same entity
(B) Three different entity sets participating together in one relationship
(C) Three Primary Keys in the same table
(D) More than one of the above
(E) None of the above

---

**Q13.** How is a MANY-TO-MANY (M:N) relationship handled in the Relational Model?
(A) One entity's table gets a foreign key to the other entity's table
(B) Both tables merge into a single large table
(C) A new junction/bridge table is created with FKs to both entity tables
(D) More than one of the above
(E) None of the above

---

**Q14.** The DOMAIN of an attribute in the Relational Model refers to:
(A) The geographic region where the data originates
(B) The complete set of all valid values the attribute can take
(C) The name given to the table containing this attribute
(D) More than one of the above
(E) None of the above

---

**Q15.** A WEAK ENTITY is correctly characterised by which of the following?
(A) It has its own complete Primary Key
(B) It has only a PARTIAL KEY and depends on a Strong Entity for full identification
(C) It exists independently without needing any other entity
(D) More than one of the above
(E) None of the above

---

**Q16.** In converting a MULTIVALUED ATTRIBUTE to the Relational Model:
(A) It is stored as multiple values separated by commas in one column
(B) It is stored in a new separate table with the entity's PK as a Foreign Key
(C) It is converted into a derived attribute and calculated on demand
(D) More than one of the above
(E) None of the above

---

**Q17.** What is the SCHEMA of a database table?
(A) The actual data (rows) currently stored in the table
(B) The structural definition — column names, data types, constraints — that rarely changes
(C) The backup copy made at a specific time
(D) More than one of the above
(E) None of the above

---

**Q18.** A UNARY (recursive) relationship in an ER diagram means:
(A) A relationship involving exactly one entity type and another entity type
(B) A relationship where an entity relates to itself (e.g., EMPLOYEE manages EMPLOYEE)
(C) A relationship with only one attribute
(D) More than one of the above
(E) None of the above

---

**Q19.** TOTAL PARTICIPATION of an entity in a relationship means:
(A) Some instances of the entity participate; others don't
(B) Every single instance of the entity must participate in the relationship
(C) The relationship covers all possible cardinality types
(D) More than one of the above
(E) None of the above

---

**Q20.** In the ER diagram, a DERIVED ATTRIBUTE is shown with:
(A) A double oval
(B) A dashed/dotted oval
(C) A rectangle
(D) More than one of the above
(E) None of the above

---

**Q21.** What is the CORRECT relationship between ER Model and Relational Model?
(A) They are the same; both are used at the implementation stage
(B) ER Model is the conceptual design stage; Relational Model is the logical/implementation stage that follows
(C) Relational Model is older and ER Model replaced it
(D) More than one of the above
(E) None of the above

---

**Q22.** When converting a WEAK ENTITY "DEPENDENT" (with partial key "DepName") that belongs to EMPLOYEE (PK: EmpID), what is the Primary Key of the DEPENDENT table?
(A) Only DepName (the partial key)
(B) Only EmpID (the owner's PK)
(C) Composite {EmpID + DepName} together
(D) More than one of the above
(E) None of the above

---

**Q23.** INSTANCE of a database differs from SCHEMA in that:
(A) Instance is permanent; Schema changes with every update
(B) Schema is the fixed structure definition; Instance is the actual data at a given point in time
(C) They refer to the same concept — just different terms
(D) More than one of the above
(E) None of the above

---

**Q24.** The Relational Model was proposed by:
(A) Peter Chen in 1976
(B) E.F. Codd in 1970
(C) Charles Bachman in 1969
(D) More than one of the above
(E) None of the above

---

**Q25.** A company has EMPLOYEE and PROJECT entities with an M:N relationship "WORKS_ON" (with attribute: HoursPerWeek). In the Relational Model, this becomes:
(A) EMPLOYEE table gets ProjectID as Foreign Key
(B) PROJECT table gets EmpID as Foreign Key
(C) A new WORKS_ON table: {EmpID[FK], ProjectID[FK], HoursPerWeek} with composite PK {EmpID, ProjectID}
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Black Soil (Regur), Cotton Belt, Regions, Characteristics

---

**Q26.** Black Soil in India is also known as:
(A) Laterite Soil
(B) Regur Soil
(C) Alluvial Soil
(D) More than one of the above
(E) None of the above

---

**Q27.** Black Soil is primarily formed by weathering of which type of rock?
(A) Granite and gneiss
(B) Basalt / volcanic (trap) rock — Deccan Traps
(C) Limestone and marble
(D) More than one of the above
(E) None of the above

---

**Q28.** The dark black colour of Black Soil is mainly due to:
(A) High organic matter and humus content
(B) Presence of titaniferous magnetite (iron-titanium compounds)
(C) High concentration of coal and carbon particles
(D) More than one of the above
(E) None of the above

---

**Q29.** What is the MOST IMPORTANT characteristic of Black Soil that makes it ideal for cotton cultivation?
(A) Very high nitrogen content
(B) High moisture-retaining capacity (stays moist through dry periods)
(C) Highly acidic pH that cotton prefers
(D) More than one of the above
(E) None of the above

---

**Q30.** Which Indian state has the LARGEST area under Black Soil?
(A) Gujarat
(B) Madhya Pradesh
(C) Maharashtra
(D) More than one of the above
(E) None of the above

---

**Q31.** "Self-ploughing" is a unique feature of Black Soil. This refers to:
(A) The soil that can be ploughed without any tools due to its softness
(B) The soil developing deep cracks when dry, which fill with organic matter, then close during monsoon — natural soil mixing
(C) The soil's ability to remove weeds automatically
(D) More than one of the above
(E) None of the above

---

**Q32.** Black Soil is DEFICIENT in which of the following nutrients?
(A) Iron and Calcium
(B) Nitrogen and Phosphorus
(C) Potassium and Magnesium
(D) More than one of the above
(E) None of the above

---

**Q33.** The clay mineral primarily responsible for the expansive nature (swelling and shrinking) of Black Soil is:
(A) Kaolinite
(B) Montmorillonite
(C) Illite
(D) More than one of the above
(E) None of the above

---

**Q34.** Black Soil is found predominantly in the:
(A) Indo-Gangetic Plains — Bihar, UP, Punjab
(B) Deccan Plateau — Maharashtra, Madhya Pradesh, Gujarat, AP
(C) Eastern Highlands — Jharkhand, Odisha, West Bengal
(D) More than one of the above
(E) None of the above

---

**Q35.** The pH of Black Soil is generally:
(A) Highly acidic (below 5)
(B) Neutral to slightly alkaline (7.2 to 8.5)
(C) Strongly alkaline (above 9)
(D) More than one of the above
(E) None of the above

---

**Q36.** Which city is known as the "Manchester of South India" due to its cotton textile industry, largely supported by surrounding black soil cotton cultivation?
(A) Hyderabad
(B) Bangalore
(C) Coimbatore
(D) More than one of the above
(E) None of the above

---

**Q37.** Which of the following correctly describes why Black Soil is also called "Cotton Soil"?
(A) Black soil is the only soil type in India that can produce cotton
(B) Cotton is the most important and most suitable crop for this soil type due to its moisture retention, alkaline nature, and mineral composition
(C) Cotton roots are responsible for creating the black colour of the soil
(D) More than one of the above
(E) None of the above

---

**Q38.** The Vidarbha region in Maharashtra is significant in the context of Black Soil because:
(A) It has the highest concentration of alluvial soil in Maharashtra
(B) It is the largest cotton-growing region in India, situated on black soil
(C) It is where black soil is being converted to alluvial soil
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following states is NOT typically associated with Black Soil (Regur)?
(A) Maharashtra
(B) Gujarat
(C) West Bengal
(D) More than one of the above
(E) None of the above

---

**Q40.** Black Soil is also referred to as "Tropical Chernozems." What does this comparison indicate?
(A) Black Soil is frozen like Siberian Chernozems
(B) Black Soil resembles the dark, fertile Chernozem soils of Russia's grasslands in colour and moisture properties, adapted to tropical India
(C) Chernozem is a type of black soil found only in China
(D) More than one of the above
(E) None of the above

---

**Q41.** Arrange the following soil types by their approximate AREA COVERAGE in India, from LARGEST to SMALLEST:
1. Alluvial Soil
2. Black Soil (Regur)
3. Red Soil
4. Laterite Soil

(A) 1 → 2 → 3 → 4
(B) 2 → 1 → 4 → 3
(C) 1 → 3 → 2 → 4
(D) More than one of the above
(E) None of the above

---

**Q42.** Black Soil is well-suited for which KHARIF crop besides cotton?
(A) Wheat and mustard (Rabi crops)
(B) Jowar (Sorghum) and Groundnuts
(C) Tea and coffee
(D) More than one of the above
(E) None of the above

---

**Q43.** The black soil region of India largely coincides with the:
(A) Himalayan foothill zone
(B) Deccan Trap (volcanic basalt lava flow) region
(C) Thar Desert region
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following characteristics of Black Soil is INCORRECT?
(A) It has high clay content and retains moisture well
(B) It is very rich in Nitrogen — the most abundant nutrient
(C) It develops deep cracks during the dry season
(D) More than one of the above
(E) None of the above

---

**Q45.** The Black Soil region gets average rainfall of approximately:
(A) Less than 25 cm (arid zone)
(B) 50 to 100 cm per year
(C) More than 200 cm (high rainfall zone)
(D) More than one of the above
(E) None of the above

---

**Q46.** "Khadar" and "Bhangar" are sub-types of which soil?
(A) Black Soil
(B) Red Soil
(C) Alluvial Soil
(D) More than one of the above
(E) None of the above

---

**Q47.** Gujarat has emerged as a leading cotton-producing state in recent years. The type of soil predominantly supporting cotton cultivation in Gujarat is:
(A) Alluvial soil in the river deltas
(B) Black soil (Regur) in Saurashtra and other regions
(C) Laterite soil in coastal areas
(D) More than one of the above
(E) None of the above

---

**Q48.** Black Soil is difficult to till (plough) under which condition?
(A) When completely dry — soil is too hard and cracked
(B) When wet — becomes extremely sticky and heavy (plastic-like)
(C) During the post-monsoon period — soil is infested with pests
(D) More than one of the above
(E) None of the above

---

**Q49.** Which is the correct sequence of the states having the most significant Black Soil coverage?
(A) Bihar → Uttar Pradesh → Jharkhand
(B) Maharashtra → Madhya Pradesh → Gujarat → Andhra Pradesh
(C) Kerala → Tamil Nadu → Karnataka
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following statements about Black Soil:
I.   Black Soil is also known as Regur soil and is ideal for cotton cultivation.
II.  It is formed by weathering of basalt rocks and gets its colour from titaniferous magnetite.
III. Black Soil is deficient in nitrogen but rich in iron, calcium, and magnesium.
IV.  The self-ploughing property of black soil is due to its clay expanding and contracting with moisture.

How many of the above statements are CORRECT?
(A) Only I and II
(B) Only I, II, and III
(C) All four — I, II, III, and IV — are correct
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ DO NOT LOOK UNTIL YOU HAVE ATTEMPTED ALL 50 QUESTIONS

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (B) | ER Model = Peter Chen, 1976 (Relational Model = E.F. Codd, 1970) |
| 2 | (C) | Weak entity = double rectangle (double border) in ER diagram |
| 3 | (B) | Strong entity = has own PK; exists independently |
| 4 | (C) | Derived attribute (Age) computed from DateOfBirth to avoid stale stored data |
| 5 | (B) | Multivalued = double oval (two concentric ovals) |
| 6 | (C) | Address → Street, City, State, PinCode = composite attribute (divisible) |
| 7 | (B) | Tuple = ROW (one complete record) in a relation |
| 8 | (B) | Degree = number of COLUMNS/attributes in a relation |
| 9 | (C) | Cardinality = number of ROWS/tuples in a relation |
| 10 | (B) | Metadata = data about data = schema, structure, constraints |
| 11 | (B) | In 1:N, FK added to MANY side (EMPLOYEE gets DeptID as FK) |
| 12 | (B) | Ternary = THREE different entity sets in one relationship |
| 13 | (C) | M:N requires new junction/bridge table with FKs to both entities |
| 14 | (B) | Domain = complete set of all valid values an attribute can take |
| 15 | (B) | Weak entity = only partial key; needs owner's PK for full ID |
| 16 | (B) | Multivalued → separate table (entity PK as FK + the attribute) |
| 17 | (B) | Schema = structure definition (column names, types, constraints); rarely changes |
| 18 | (B) | Unary = entity relates to itself (EMPLOYEE manages EMPLOYEE) |
| 19 | (B) | Total participation = EVERY instance must be in the relationship |
| 20 | (B) | Derived attribute = dashed/dotted oval in ER diagram |
| 21 | (B) | ER = conceptual design first; Relational = logical/implementation stage that follows |
| 22 | (C) | Weak entity PK = Composite {owner PK + partial key} = {EmpID + DepName} |
| 23 | (B) | Schema = fixed structure; Instance = current data that changes constantly |
| 24 | (B) | Relational Model = E.F. Codd, 1970 (NOT Peter Chen who did ER in 1976) |
| 25 | (C) | M:N with attribute → junction table WORKS_ON with composite PK |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Black Soil = Regur Soil (most important alternative name) |
| 27 | (B) | Formed from weathering of BASALT/volcanic rock (Deccan Traps) |
| 28 | (B) | Dark colour = titaniferous magnetite (iron-titanium compounds) |
| 29 | (B) | High moisture retention = key feature matching cotton's dry-spell needs |
| 30 | (C) | Maharashtra has the LARGEST area under black soil |
| 31 | (B) | Self-ploughing = cracks in dry season fill with organic matter, close in monsoon |
| 32 | (B) | Deficient in Nitrogen and Phosphorus (rich in iron, calcium, magnesium) |
| 33 | (B) | Montmorillonite clay = responsible for swelling/shrinking behaviour |
| 34 | (B) | Black soil = Deccan Plateau region (Maharashtra, MP, Gujarat, AP) |
| 35 | (B) | Black soil pH = 7.2 to 8.5 (neutral to slightly alkaline) |
| 36 | (C) | Coimbatore = "Manchester of South India" (cotton textile hub) |
| 37 | (B) | Cotton = most suitable crop due to moisture retention, alkalinity, minerals |
| 38 | (B) | Vidarbha (Maharashtra) = largest cotton-growing region in India |
| 39 | (C) | West Bengal is NOT associated with black soil (alluvial dominant) |
| 40 | (B) | Tropical Chernozems = resembles Russia's fertile dark grassland soils |
| 41 | (A) | Alluvial (largest ~40%) > Black (~16%) > Red (~18%) > Laterite — but standard answer: 1→2→3→4 |
| 42 | (B) | Jowar and Groundnuts also grown on black soil (Kharif crops) |
| 43 | (B) | Black soil coincides with Deccan Trap (volcanic basalt) region |
| 44 | (B) | Statement B is INCORRECT — Black soil is DEFICIENT in Nitrogen (not rich) |
| 45 | (B) | Black soil region = 50-100 cm rainfall (moderate) |
| 46 | (C) | Khadar (new alluvial, near river) and Bhangar (old alluvial) = sub-types of Alluvial Soil |
| 47 | (B) | Gujarat's cotton = black soil in Saurashtra region |
| 48 | (B) | Black soil is extremely sticky and difficult to till when WET |
| 49 | (B) | Major black soil states: Maharashtra → MP → Gujarat → AP |
| 50 | (C) | All four statements I, II, III, and IV are correct |

---
---

# 🔁 DAY 38 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — ER Model

### Core Definitions:
```
ER MODEL:   Conceptual design tool; visualises database structure before building.
            Proposed by PETER CHEN (1976).
ENTITY:     Real-world object/thing we store data about.
ATTRIBUTE:  Property/characteristic of an entity.
RELATIONSHIP: Association between two or more entities. Symbol = Diamond.
```

### Entity Types:
```
STRONG ENTITY: Has own PK; exists independently. Symbol = Single rectangle.
WEAK ENTITY:   No own PK; partial key only; depends on strong entity.
               Symbol = Double rectangle. Full key = Owner PK + Partial key.
```

### Attribute Types — The 4 Types:
```
SIMPLE:      Indivisible. Symbol = single oval. Example: RollNo, Age.
COMPOSITE:   Can be divided. Symbol = oval with sub-ovals. Example: Name, Address.
DERIVED:     Calculated from another attribute. Symbol = DASHED oval. Example: Age from DoB.
MULTIVALUED: Multiple values per entity. Symbol = DOUBLE oval. Example: Phone, Skills.
             → Stored in SEPARATE TABLE in Relational Model.
```

### Relationship Types:
```
DEGREE:
  Unary (1) = entity relates to itself (EMPLOYEE manages EMPLOYEE)
  Binary (2) = two entities — MOST COMMON
  Ternary (3) = three entities together

CARDINALITY:
  1:1 = Person ↔ Passport
  1:N = Dept → Employees (FK goes to MANY side!)
  M:N = Students ↔ Courses (needs JUNCTION TABLE!)

PARTICIPATION:
  Total (double line ====) = EVERY instance must participate
  Partial (single line ──) = Only SOME instances participate
```

### ER to Relational Conversion — Key Rules:
```
Strong Entity → Table (PK attribute = PK column)
Weak Entity   → Table (composite PK = owner PK + partial key)
Simple Attr   → Direct column
Composite     → Multiple sub-columns
Derived       → NOT stored (calculate on demand)
Multivalued   → New separate table (entity PK as FK)
1:1 relation  → Merge or add FK
1:N relation  → FK on MANY side
M:N relation  → New JUNCTION table (composite PK = both FKs)
```

---

## ⚡ RAPID FIRE — Relational Model

### Terminology Quick Map:
```
Relational Model term → Common/Table term:
  RELATION   →  TABLE
  TUPLE      →  ROW
  ATTRIBUTE  →  COLUMN
  DOMAIN     →  Valid values set
  DEGREE     →  Number of COLUMNS
  CARDINALITY → Number of ROWS
  SCHEMA     →  Structure definition (permanent)
  INSTANCE   →  Actual data right now (dynamic)
  METADATA   →  Data ABOUT data (schema = metadata!)
```

### Proposed By:
```
ER Model        = Peter Chen (1976)
Relational Model = E.F. Codd (1970)
```

---

## ⚡ RAPID FIRE — Black Soil

### Black Soil — 10-Point Flash Card:
```
1. Other name:    REGUR soil, Black Cotton Soil, Volcanic/Lava soil
2. Origin:        Weathering of BASALT (volcanic) rocks — Deccan Traps
3. Colour source: TITANIFEROUS MAGNETITE (iron-titanium compound)
4. Key feature:   HIGH MOISTURE RETENTION
5. Clay mineral:  MONTMORILLONITE (swells wet, shrinks dry)
6. Self-ploughing: Cracks in dry season → organic filling → closes in monsoon
7. Best crop:     COTTON (and Jowar, Groundnuts also)
8. Rich in:       Iron, Calcium, Magnesium, Potassium
9. Poor in:       NITROGEN, Phosphorus, Humus
10. pH:           7.2-8.5 (slightly ALKALINE)
```

### State Coverage (Decreasing Order):
```
1. MAHARASHTRA (largest!) → Vidarbha = India's largest cotton belt
2. MADHYA PRADESH → Malwa Plateau
3. GUJARAT → Saurashtra
4. ANDHRA PRADESH + TELANGANA
5. KARNATAKA (northern)
6. RAJASTHAN (southeastern corner)
```

### Key PYQ Geography Facts:
```
✅ Regur = Black soil official name
✅ Self-ploughing = UNIQUE characteristic (only black soil!)
✅ Maharashtra = largest state area under black soil
✅ Vidarbha = largest cotton-growing region in India
✅ Coimbatore = "Manchester of South India"
✅ Mumbai (historically) = "Manchester of India" or "Cottonopolis"
✅ Black soil = 2nd most extensive after ALLUVIAL
✅ Alluvial soil = LARGEST soil type in India (~40%)
✅ Khadar + Bhangar = sub-types of ALLUVIAL soil (NOT black soil!)
✅ Montmorillonite = the specific clay causing expansion-contraction
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **ER Model basics**: Peter Chen (1976); 3 components = Entity + Attribute + Relationship; Strong entity (single rectangle, own PK) vs Weak entity (double rectangle, partial key, depends on strong entity).
2. **Attribute types**: Simple = indivisible; Composite = divisible sub-parts; Derived = DASHED oval, calculated, not stored; Multivalued = DOUBLE oval, stored in separate table.
3. **Cardinality conversion**: 1:N → FK on MANY side; M:N → new junction table with composite PK; Derived attributes NOT stored; Multivalued → separate table.
4. **Relational model terms**: Relation=Table, Tuple=ROW, Attribute=COLUMN, Degree=columns, Cardinality=rows, Schema=structure, Instance=current data, Metadata=data about data; E.F. Codd (1970).
5. **Black soil**: Regur soil; from BASALT; colour = titaniferous magnetite; high moisture retention; self-ploughing (cracks dry, fills monsoon); deficient in NITROGEN; Maharashtra = largest; Montmorillonite clay; cotton crop; pH 7.2-8.5.

---

## 📅 DAY 39 PREVIEW — What's Coming Next:
**CS**: DBMS Normalization — 1NF, 2NF, 3NF (step-by-step with examples), Functional Dependencies, Anomalies (insertion, deletion, update), Why normalization is needed
**GS**: Indian Polity — Fundamental Rights (Articles 12-35): Right to Equality (14-18), Right to Freedom (19-22), Right Against Exploitation (23-24), Right to Freedom of Religion (25-28), Cultural & Educational Rights (29-30), Right to Constitutional Remedies (Article 32 — Dr. Ambedkar's "Heart and Soul" of Constitution)

---

*🚀 Day 38 of 170 — You're 22.4% through. Today you covered two conceptually rich topics. ER diagrams + normalization (tomorrow) together form the foundation of all DBMS questions. Keep going — the momentum is building!*
