# 📅 BPSC TRE 4.0 — DAY 37 COMPLETE STUDY MODULE
### DBMS Keys (Primary, Foreign, Super, Candidate, Composite, Unique) + Birsa Munda & Revolutionary Movements Revision
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): DBMS Keys — All Types, Differences, Constraints, PYQ Traps
> - Afternoon (1 hr): History — Birsa Munda (deep dive) + Revision of Anushilan Samiti & Ghadar Party
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 DBMS Keys — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Key? — The Foundation

### Real-Life Analogy — The Aadhaar Card:

Every Indian has an **Aadhaar Number** — a unique 12-digit number. No two Indians share the same Aadhaar number. It uniquely identifies you among 1.4 billion people.

In a database table, a **Key** does exactly the same job — it uniquely identifies each row (record) in a table.

```
REAL WORLD           →    DATABASE EQUIVALENT
────────────────────────────────────────────────
Aadhaar Number       →    Primary Key (unique ID for each row)
PAN Card Number      →    Another Candidate Key
Mobile Number        →    Yet another Candidate Key (unique but can be NULL)
Name                 →    NOT a key (two people can have the same name!)
```

### Formal Definition:
> **A Key is an attribute (or a set of attributes) that uniquely identifies each row (tuple) in a database table.**

### Why Are Keys Needed?

```
PROBLEM WITHOUT KEYS:

STUDENT TABLE:
┌──────────────┬─────────┬───────────┬──────┐
│     Name     │ Course  │   City    │ Marks│
├──────────────┼─────────┼───────────┼──────┤
│  Ravi Kumar  │   CS    │  Patna    │  85  │
│  Ravi Kumar  │   CS    │  Patna    │  85  │  ← DUPLICATE ROW!
│  Priya Singh │  Math   │  Muzaffarpur│ 90 │
└──────────────┴─────────┴───────────┴──────┘

Which "Ravi Kumar" do we update? Which do we delete?
→ AMBIGUITY! The system cannot distinguish between them.

SOLUTION: Add a KEY column (like Roll Number):
┌─────────┬──────────────┬─────────┬───────────┬──────┐
│ Roll No │     Name     │ Course  │   City    │ Marks│
├─────────┼──────────────┼─────────┼───────────┼──────┤
│   101   │  Ravi Kumar  │   CS    │  Patna    │  85  │
│   102   │  Ravi Kumar  │   CS    │  Patna    │  85  │  ← Now distinguishable!
│   103   │  Priya Singh │  Math   │  Muzaffarpur│ 90 │
└─────────┴──────────────┴─────────┴───────────┴──────┘
Now Roll No 101 and 102 are clearly different students!
```

### The Big Picture — Key Hierarchy:

```
ALL POSSIBLE COMBINATIONS that can uniquely identify a row
                        ↓
                   SUPER KEYS
            (all unique-identifying sets)
                        ↓
               CANDIDATE KEYS
           (minimal super keys — can't remove any attribute)
                        ↓
     ┌─────────────────┬────────────────────────────┐
     ↓                 ↓                            ↓
PRIMARY KEY      ALTERNATE KEYS              (Remaining candidate
(ONE chosen      (remaining candidate         keys not chosen)
from candidates) keys)

FOREIGN KEY → special key that LINKS two tables
COMPOSITE KEY → key made of MULTIPLE attributes combined
UNIQUE KEY → like primary key but allows NULL
```

---

## 🔷 SECTION 2: SUPER KEY

### Definition:
> **A Super Key is any attribute (or set of attributes) that can UNIQUELY IDENTIFY each row in a table.**
> It may contain EXTRA attributes that are not strictly necessary for uniqueness.

### Working Example:

```
STUDENTS TABLE:
┌─────────┬──────────────┬────────────┬──────────────┬──────┐
│ Roll No │     Name     │   Email    │    Phone     │ Marks│
├─────────┼──────────────┼────────────┼──────────────┼──────┤
│   101   │  Ravi Kumar  │ r@mail.com │ 9876543210   │  85  │
│   102   │  Priya Singh │ p@mail.com │ 9876543211   │  90  │
│   103   │  Aman Gupta  │ a@mail.com │ 9876543212   │  78  │
└─────────┴──────────────┴────────────┴──────────────┴──────┘

VALID SUPER KEYS (all uniquely identify a row):
  {Roll No}                            ← unique alone
  {Email}                              ← unique alone
  {Phone}                              ← unique alone
  {Roll No, Name}                      ← unique (has extra: Name is not needed!)
  {Roll No, Email}                     ← unique (both together, but Roll No alone works)
  {Roll No, Name, Email}               ← unique (many extra attributes)
  {Roll No, Name, Email, Phone, Marks} ← ALL attributes — still uniquely identifies!

NOT a valid super key:
  {Name}  ← NOT unique (two "Ravi Kumar" could exist)
  {Marks} ← NOT unique (multiple students can score 85)
  {City}  ← NOT unique (many students from same city)

KEY INSIGHT: A super key may have redundant attributes.
             Remove some and it STILL remains unique.
```

### 🎯 PYQ FACT: A Super Key is the BROADEST category. Every Primary Key, Candidate Key is also a Super Key. But not every Super Key is a Candidate Key or Primary Key.

---

## 🔷 SECTION 3: CANDIDATE KEY

### Definition:
> **A Candidate Key is a MINIMAL Super Key — a super key from which you CANNOT remove any attribute without losing uniqueness.**

### The "Minimal" Concept Explained:

```
FROM THE SUPER KEYS ABOVE:
  {Roll No, Name}  → Super Key, but if we remove Name → {Roll No} still unique!
                     So {Roll No, Name} is NOT minimal → NOT a candidate key.

  {Roll No}        → Super Key, and if we remove Roll No → {} nothing left!
                     Cannot remove anything → IT IS MINIMAL → CANDIDATE KEY ✓

  {Email}          → Super Key, minimal → CANDIDATE KEY ✓

  {Phone}          → Super Key, minimal → CANDIDATE KEY ✓

CANDIDATE KEYS for this table:
  → {Roll No}     ← can uniquely identify alone, nothing to remove
  → {Email}       ← can uniquely identify alone
  → {Phone}       ← can uniquely identify alone

RULE: Candidate Key = Super Key − (all super keys with unnecessary attributes)
      Only the "bare minimum" sets that still uniquely identify rows.
```

### Super Key vs Candidate Key:

```
┌──────────────────────────────────────────────────────────────────┐
│            SUPER KEY vs CANDIDATE KEY                             │
├──────────────────────────────┬───────────────────────────────────┤
│          SUPER KEY           │         CANDIDATE KEY             │
├──────────────────────────────┼───────────────────────────────────┤
│ Any set that uniquely        │ Minimal set that uniquely         │
│ identifies rows              │ identifies rows                   │
├──────────────────────────────┼───────────────────────────────────┤
│ May have EXTRA attributes    │ No extra attributes — removing    │
│ (redundant ones)             │ any attribute loses uniqueness    │
├──────────────────────────────┼───────────────────────────────────┤
│ {Roll No, Name} — valid      │ {Roll No, Name} — NOT candidate   │
│ super key                    │ (Roll No alone is sufficient)     │
├──────────────────────────────┼───────────────────────────────────┤
│ Every Candidate Key IS a     │ Every Candidate Key is a          │
│ Super Key                    │ Minimal Super Key                 │
├──────────────────────────────┼───────────────────────────────────┤
│ Can be INFINITE in number    │ LIMITED in number (finite)        │
└──────────────────────────────┴───────────────────────────────────┘

RELATIONSHIP:
  All Candidate Keys are Super Keys.
  NOT all Super Keys are Candidate Keys.
  
  SUPER KEY ⊃ CANDIDATE KEY  (Candidate Key is a subset of Super Keys)
```

### 🎯 PYQ FACT: A Candidate Key is always a Minimal Super Key. If you can remove any attribute and it still uniquely identifies — it's NOT a Candidate Key, just a Super Key.

---

## 🔷 SECTION 4: PRIMARY KEY

### Definition:
> **A Primary Key is ONE Candidate Key chosen by the database designer to be the OFFICIAL identifier of rows in a table.**

### Rules of Primary Key (ALL ARE PYQ TRAPS!):

```
RULE 1: A table can have ONLY ONE Primary Key.
        (But it can have multiple Candidate Keys — only one is "chosen" as primary)

RULE 2: Primary Key value CANNOT be NULL.
        (Every row MUST have a value for the primary key column)

RULE 3: Primary Key values must be UNIQUE.
        (No two rows can have the same primary key value)

RULE 4: Primary Key is CHOSEN from Candidate Keys.
        (If there are 3 candidate keys, the designer picks 1 as primary)

RULE 5: Primary Key values should NOT change over time.
        (Stable identifier — Roll No is better than Name which can change)
```

### Visual Example:

```
STUDENTS TABLE:
┌──────────┬──────────────┬────────────┬──────────────┬──────┐
│ Roll No  │     Name     │   Email    │    Phone     │ Marks│
│ [PK] 🔑  │              │            │              │      │
├──────────┼──────────────┼────────────┼──────────────┼──────┤
│   101    │  Ravi Kumar  │ r@mail.com │ 9876543210   │  85  │
│   102    │  Priya Singh │ p@mail.com │ 9876543211   │  90  │
│  NULL    │  Aman Gupta  │ a@mail.com │ 9876543212   │  78  │ ← INVALID! NULL not allowed
│   101    │  Kiran Verma │ k@mail.com │ 9876543213   │  92  │ ← INVALID! Duplicate PK
└──────────┴──────────────┴────────────┴──────────────┴──────┘

EXPLANATION:
  Roll No = PRIMARY KEY (chosen from candidates: Roll No, Email, Phone)
  Row 3: Roll No = NULL → REJECTED by DBMS (PK cannot be NULL!)
  Row 4: Roll No = 101 (already exists) → REJECTED (PK must be UNIQUE!)
```

### Choosing a Good Primary Key:

```
GOOD Primary Keys:
  ✅ Roll Number (students)   → never changes, always unique
  ✅ Employee ID              → assigned by company, never repeats
  ✅ Aadhaar Number           → government-assigned, universally unique
  ✅ Account Number           → bank-assigned, unique per account
  ✅ ISBN (books)             → unique per book edition
  ✅ Auto-increment integer   → system generates 1, 2, 3, 4... automatically

BAD Primary Keys (and why):
  ❌ Name              → multiple people can have same name
  ❌ Phone Number      → can change, can be shared
  ❌ Email             → can change when company changes
  ❌ Date of Birth     → multiple people born same day
  ❌ City/Address      → many people in same city
```

---

## 🔷 SECTION 5: FOREIGN KEY

### Definition:
> **A Foreign Key is an attribute in one table that REFERENCES the Primary Key of another table. It is used to LINK two tables and enforce referential integrity.**

### Real-Life Analogy — The Library System:

```
Think of a library:
  BOOKS table has a column "LibrarianID" (who added the book).
  LIBRARIANS table has "LibrarianID" as its primary key.
  
  The "LibrarianID" in BOOKS table is a FOREIGN KEY.
  It points to a LIBRARIAN who actually exists.
  You can't have a book added by Librarian #999 if librarian #999 doesn't exist!
```

### Two-Table Example — Students and Departments:

```
DEPARTMENTS Table:
┌────────┬──────────────────────┬───────────┐
│ DeptID │     DeptName         │   HOD     │
│  [PK]🔑│                      │           │
├────────┼──────────────────────┼───────────┤
│   CS   │  Computer Science    │  Dr. Rao  │
│  Math  │  Mathematics         │  Dr. Jha  │
│  Phys  │  Physics             │  Dr. Gupta│
└────────┴──────────────────────┴───────────┘

STUDENTS Table:
┌─────────┬──────────────┬──────┬────────┐
│ Roll No │     Name     │Marks │ DeptID │
│  [PK]🔑 │              │      │  [FK]🔗│
├─────────┼──────────────┼──────┼────────┤
│   101   │  Ravi Kumar  │  85  │   CS   │ ← Refers to DeptID 'CS' in DEPARTMENTS
│   102   │  Priya Singh │  90  │  Math  │ ← Refers to DeptID 'Math'
│   103   │  Aman Gupta  │  78  │   CS   │ ← Refers to DeptID 'CS'
│   104   │  Kiran Verma │  92  │  Bio   │ ← INVALID! 'Bio' doesn't exist in DEPARTMENTS!
└─────────┴──────────────┴──────┴────────┘

ARROW DIAGRAM:
STUDENTS.DeptID  ──────────→  DEPARTMENTS.DeptID
    (Foreign Key)                  (Primary Key)

RULE: Foreign Key value MUST either:
  (a) Match an existing Primary Key value in the referenced table, OR
  (b) Be NULL (foreign key CAN be NULL, unlike primary key!)
```

### Properties of Foreign Key:

```
PROPERTY 1: Foreign Key REFERENCES the Primary Key of ANOTHER table.
             (Usually; technically it can reference any UNIQUE key)

PROPERTY 2: Foreign Key CAN be NULL.
             (Meaning: this row has no department assigned yet — valid!)

PROPERTY 3: Foreign Key ENFORCES Referential Integrity.
             (Can't have a student in dept 'Bio' if 'Bio' dept doesn't exist)

PROPERTY 4: Multiple Foreign Keys can exist in one table.
             (A table can have many columns referencing other tables)

PROPERTY 5: Foreign Key can reference the SAME TABLE (self-referencing).
             Example: EMPLOYEE table where ManagerID references EmployeeID
             in the same EMPLOYEE table!
             
             EMPLOYEES:
             ┌────────────┬───────────┬───────────┐
             │ EmployeeID │   Name    │ ManagerID │
             │   [PK]     │           │   [FK]    │
             ├────────────┼───────────┼───────────┤
             │    E01     │  Ravi     │  NULL     │ ← CEO has no manager
             │    E02     │  Priya    │   E01     │ ← Priya's manager is Ravi
             │    E03     │  Aman     │   E01     │ ← Aman's manager is Ravi
             └────────────┴───────────┴───────────┘
```

### Referential Integrity:

```
REFERENTIAL INTEGRITY = The rule that a Foreign Key value must match
                        a Primary Key value in the referenced table
                        (or be NULL).

WHAT HAPPENS WHEN VIOLATED?
  → DBMS REJECTS the operation!
  
EXAMPLE VIOLATIONS:
  
  INSERT violation:
    Try to add student with DeptID = 'Bio' when 'Bio' doesn't exist.
    → DBMS: REJECTED! Foreign key constraint violated.
  
  DELETE violation:
    Try to DELETE the 'CS' department when CS students exist.
    → DBMS: REJECTED! (or CASCADE — delete all CS students too)
  
  UPDATE violation:
    Try to change DeptID 'CS' to 'CompSci' in DEPARTMENTS.
    → DBMS: REJECTED! (or CASCADE UPDATE — updates all references)

CASCADING OPTIONS (what happens when parent row is changed/deleted):
  ON DELETE CASCADE   → Delete child rows when parent deleted
  ON DELETE SET NULL  → Set FK to NULL when parent deleted
  ON DELETE RESTRICT  → Prevent deletion if children exist (default)
  ON UPDATE CASCADE   → Update FK values when PK changes
```

---

## 🔷 SECTION 6: COMPOSITE KEY

### Definition:
> **A Composite Key is a key made up of TWO OR MORE attributes that together uniquely identify a row. No single attribute alone is sufficient.**

### When Do We Need Composite Keys?

```
SCENARIO: A student can enroll in MULTIPLE courses.
          A course can have MULTIPLE students.
          (Many-to-Many relationship)

ENROLLMENT Table:
┌─────────┬────────────┬────────┬───────────┐
│ Roll No │  CourseID  │ Marks  │   Grade   │
├─────────┼────────────┼────────┼───────────┤
│   101   │    CS101   │   85   │     A     │
│   101   │    Math101 │   90   │     A+    │  ← Same Roll No, different course!
│   102   │    CS101   │   78   │     B+    │  ← Same CourseID, different student!
│   102   │    Math101 │   88   │     A     │
└─────────┴────────────┴────────┴───────────┘

Can Roll No alone be Primary Key? NO! — Roll No 101 appears twice.
Can CourseID alone be Primary Key? NO! — CS101 appears twice.

SOLUTION: Composite Key = {Roll No + CourseID}
  → (101, CS101) — UNIQUE ✓
  → (101, Math101) — UNIQUE ✓
  → (102, CS101) — UNIQUE ✓
  → (102, Math101) — UNIQUE ✓
  
  Together they uniquely identify each enrollment!
```

### Visual Representation:

```
ENROLLMENT TABLE with COMPOSITE KEY:

┌─────────┬────────────┬────────┬───────────┐
│ Roll No │  CourseID  │ Marks  │   Grade   │
│  [CK1]  │   [CK2]   │        │           │
│ ════════╧════════════ (Composite PK) ════ │
├─────────┼────────────┼────────┼───────────┤
│   101   │    CS101   │   85   │     A     │
│   101   │   Math101  │   90   │     A+    │
│   102   │    CS101   │   78   │     B+    │
└─────────┴────────────┴────────┴───────────┘

COMPOSITE KEY = {Roll No} + {CourseID} together

Other examples of Composite Keys:
  → {Flight Number + Date} for FLIGHT BOOKINGS
  → {Employee ID + Project ID} for PROJECT ASSIGNMENTS
  → {OrderID + ProductID} for ORDER ITEMS
  → {SenderID + ReceiverID + Date} for MESSAGES
```

### 🚨 PYQ TRAP: Composite Key is NOT necessarily a Primary Key:
```
A Composite Key refers to any key made of multiple attributes.
If that composite key is chosen as the primary key, it becomes a
COMPOSITE PRIMARY KEY.

The term "composite key" describes the STRUCTURE (multi-attribute),
not the TYPE (primary/foreign/etc).
```

---

## 🔷 SECTION 7: UNIQUE KEY

### Definition:
> **A Unique Key ensures that all values in a column (or combination of columns) are unique — BUT unlike the Primary Key, it CAN contain NULL values.**

### Unique Key vs Primary Key — The Critical Difference:

```
┌──────────────────────────┬────────────────────────────────────────┐
│       PRIMARY KEY        │            UNIQUE KEY                  │
├──────────────────────────┼────────────────────────────────────────┤
│ Only ONE per table       │ Multiple unique keys allowed per table │
├──────────────────────────┼────────────────────────────────────────┤
│ CANNOT be NULL           │ CAN be NULL                           │
│ (NULL is not allowed)    │ (but NULL only once — NULL ≠ NULL!)   │
├──────────────────────────┼────────────────────────────────────────┤
│ Automatically creates    │ Also creates an index (but not the     │
│ clustered index          │ clustered/primary index)               │
├──────────────────────────┼────────────────────────────────────────┤
│ Main identifier of row   │ Additional uniqueness constraint,      │
│                          │ not the "main" identifier              │
├──────────────────────────┼────────────────────────────────────────┤
│ Cannot be duplicate      │ Cannot be duplicate (except NULL!)     │
├──────────────────────────┼────────────────────────────────────────┤
│ Example: Roll No         │ Example: Email, Phone Number           │
└──────────────────────────┴────────────────────────────────────────┘
```

### Why Does NULL Behavior Matter?

```
NULL in databases means "unknown" or "not provided."

NULL ≠ NULL in SQL! (Two NULLs are NOT equal to each other)

UNIQUE KEY with NULL:
  Email column (UNIQUE KEY):
  ┌──────────────────┐
  │     Email        │
  ├──────────────────┤
  │  r@mail.com      │  → Unique ✓
  │  p@mail.com      │  → Unique ✓
  │  NULL            │  → Allowed! (student hasn't provided email)
  │  NULL            │  → ALSO Allowed! (another student, also no email)
  │  r@mail.com      │  → REJECTED! Duplicate non-NULL value
  └──────────────────┘

Why are TWO NULLs allowed in Unique Key?
  Because NULL means "unknown" — two unknowns can't be compared.
  They could potentially be different values!

PRIMARY KEY with NULL:
  Roll No column (PRIMARY KEY):
  ┌──────────────────┐
  │    Roll No       │
  ├──────────────────┤
  │     101          │  → Valid ✓
  │     NULL         │  → REJECTED! Primary key cannot be NULL
  └──────────────────┘
```

---

## 🔷 SECTION 8: ALTERNATE KEY

### Definition:
> **Alternate Keys are all Candidate Keys that were NOT chosen as the Primary Key.**

```
EXAMPLE:
  Candidate Keys: {Roll No}, {Email}, {Phone}
  Primary Key chosen: {Roll No}
  
  Alternate Keys: {Email}, {Phone}
  (They could have been primary key, but weren't chosen)
  
  ALTERNATE KEY = CANDIDATE KEY − PRIMARY KEY

These are still enforced as UNIQUE constraints in the database!
They just aren't the "official" primary identifier.
```

---

## 🔷 SECTION 9: Complete Keys Comparison — Master Reference Table

```
┌──────────────┬────────────────────────┬──────────────┬──────────────────────────┐
│   KEY TYPE   │       DEFINITION       │  NULL ALLOWED│      EXAMPLE             │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Super Key    │ Any set that uniquely  │ Not applicable│ {Roll No}, {Roll No,Name}│
│              │ identifies rows        │ (set-based)  │ {Email, Phone}, etc.     │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Candidate Key│ Minimal super key      │ No           │ {Roll No}, {Email},      │
│              │ (nothing removable)    │ (usually)    │ {Phone}                  │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Primary Key  │ ONE chosen candidate   │ NO — never   │ Roll No (chosen from     │
│              │ key; main identifier   │              │ candidate keys)          │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Foreign Key  │ References PK of       │ YES — allowed│ DeptID in STUDENTS       │
│              │ another table          │              │ refs DeptID in DEPTS     │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Composite Key│ Two or more attributes │ Depends on   │ {Roll No + CourseID}     │
│              │ combined as a key      │ key type     │ in ENROLLMENT            │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Unique Key   │ Ensures uniqueness;    │ YES — allowed│ Email column with        │
│              │ NOT the primary ID     │ (multiple NULLs│ UNIQUE constraint       │
├──────────────┼────────────────────────┼──────────────┼──────────────────────────┤
│ Alternate Key│ Candidate keys NOT     │ No           │ Email, Phone (when       │
│              │ chosen as PK           │ (usually)    │ Roll No is chosen as PK) │
└──────────────┴────────────────────────┴──────────────┴──────────────────────────┘
```

---

## 🔷 SECTION 10: Visual Diagram — Primary Key & Foreign Key Relationship

```
TWO-TABLE RELATIONSHIP DIAGRAM:

DEPARTMENTS Table                    STUDENTS Table
─────────────────────────           ─────────────────────────────────────────
│ DeptID [PK🔑] │ DeptName │        │ RollNo [PK🔑]│ Name  │ DeptID [FK🔗] │
├───────────────┼──────────┤        ├──────────────┼───────┼───────────────┤
│     CS        │ Comp Sci │◄──────┐│     101      │ Ravi  │      CS       │
│    Math       │ Maths    │◄────┐ ││     102      │ Priya │     Math      │
│    Phys       │ Physics  │     │ ││     103      │ Aman  │      CS       │
└───────────────┴──────────┘     │ │└──────────────┴───────┴───────────────┘
                                  │ │                                ↑
                                  │ │                                │
                                  └─┼────────────────────────────────┘
                                    │ STUDENTS.DeptID → DEPARTMENTS.DeptID
                                    │ (Foreign Key → Primary Key)

ARROW DIRECTION:  FK Table ──→ PK Table
                  (Child)       (Parent)

RULES ENFORCED:
  → Can't add student with DeptID not in DEPARTMENTS
  → Can't delete a department that has students
  → Primary Key (DeptID in DEPARTMENTS) = unique, not null
  → Foreign Key (DeptID in STUDENTS) = can be null (student not yet assigned)
```

---

## 🔷 SECTION 11: Key Relationships Diagram

```
                    ┌─────────────────────────────────────┐
                    │         ALL ATTRIBUTES               │
                    │  (Name, Age, Roll No, Email, Phone) │
                    └──────────────────┬──────────────────┘
                                       │ Some subsets uniquely identify rows
                                       ▼
                    ┌─────────────────────────────────────┐
                    │           SUPER KEYS                │
                    │  {Roll No}, {Email}, {Phone},       │
                    │  {Roll No, Name}, {Roll No, Email}, │
                    │  {All attributes}, etc.             │
                    └──────────────────┬──────────────────┘
                                       │ Remove redundant attributes
                                       ▼
                    ┌─────────────────────────────────────┐
                    │         CANDIDATE KEYS              │
                    │  {Roll No}, {Email}, {Phone}        │
                    │  (MINIMAL — can't remove anything!) │
                    └─────────────┬───────────────────────┘
                                  │
              ┌───────────────────┼─────────────────────┐
              ▼                   │                     ▼
  ┌──────────────────┐            │         ┌──────────────────────┐
  │   PRIMARY KEY    │            │         │    ALTERNATE KEYS    │
  │  {Roll No}       │            │         │  {Email}, {Phone}    │
  │  (ONE chosen)    │            │         │  (remaining ones)    │
  └──────────────────┘            │         └──────────────────────┘
                                  │
              ┌───────────────────┼─────────────────────┐
              ▼                   ▼                     ▼
  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
  │   FOREIGN KEY    │  │  COMPOSITE KEY   │  │   UNIQUE KEY     │
  │ (links tables)   │  │ (multi-attribute)│  │ (unique, can NULL)│
  └──────────────────┘  └──────────────────┘  └──────────────────┘
```

---

## 🔷 SECTION 12: Common PYQ Patterns and Traps

```
TRAP 1: "A table can have multiple Primary Keys"
  → FALSE! A table has ONLY ONE Primary Key.
           But can have multiple CANDIDATE keys, ALTERNATE keys, UNIQUE keys.

TRAP 2: "Primary Key can be NULL"
  → FALSE! Primary Key CANNOT be NULL. EVER.
           UNIQUE KEY can be NULL.
           FOREIGN KEY can be NULL.

TRAP 3: "Foreign Key references the Foreign Key of another table"
  → FALSE! Foreign Key references the PRIMARY KEY of another table.
           (Sometimes it can reference any UNIQUE key, but PK is standard answer)

TRAP 4: "Candidate Key = Primary Key"
  → FALSE! Primary Key is ONE candidate key.
           There can be MULTIPLE candidate keys; only ONE is primary.

TRAP 5: "Super Key and Candidate Key are the same"
  → FALSE! Super Key may have extra (redundant) attributes.
           Candidate Key is MINIMAL — no extra attributes.

TRAP 6: "Unique Key and Primary Key are the same"
  → FALSE! Primary Key: NO NULL, only ONE per table.
           Unique Key: NULL allowed, MULTIPLE per table.

TRAP 7: "Composite Key means Primary Key with multiple tables"
  → FALSE! Composite Key = ONE key made of MULTIPLE ATTRIBUTES in the SAME table.
           Nothing to do with "multiple tables."

TRAP 8: "Removing one attribute from Super Key always makes it invalid"
  → FALSE! That's only true for Candidate Keys.
           Super Keys can have extra attributes — removing extras still leaves it valid.

TRAP 9: "Foreign Key creates a relationship between rows in the SAME table"
  → PARTIALLY TRUE! A Foreign Key CAN self-reference (same table).
                    But typically it links two DIFFERENT tables.

TRAP 10: "A Candidate Key cannot be NULL"
  → Generally TRUE — candidate keys, like primary keys, should not be NULL
    as they are meant to uniquely identify rows.
```

---

# PART 2: GENERAL STUDIES
## ⚔️ History — Birsa Munda: Deep Dive + Revolutionary Movements Revision

---

## 🔷 SECTION 1: BIRSA MUNDA — Complete Story

### Early Life — From Shepherd Boy to Prophet:

```
BORN:      15 November 1875
VILLAGE:   Ulihatu, Khunti district, Chota Nagpur (now Jharkhand)
TRIBE:     Munda (Adivasi community)
FATHER:    Sugana Munda (poor agricultural labourer)
RELIGION:  Born into a family that converted to Christianity
           (his father worked for a German Lutheran missionary)

EDUCATION:
  → Attended a missionary school in Chaibasa
  → Intelligent student; exposed to both Christian and Hindu teachings
  → Later LEFT Christianity → returned to tribal Sarna religion
  → Began synthesising traditional Munda beliefs with reformist ideas

YOUNG BIRSA:
  → Worked as a shepherd
  → Deeply affected by seeing tribal lands being grabbed by moneylenders
  → Witnessed British forest laws stripping tribals of their livelihood
  → By 1895, declared himself a DIVINE MESSENGER of God (Singbonga)
```

### The Four-Pronged Exploitation:

```
WHY DID BIRSA REVOLT? Four forces crushing the Munda tribals:

1. DIKU SYSTEM (Moneylenders):
   "Diku" = outsider/non-tribal in Mundari language
   → Hindu traders and moneylenders came to Chota Nagpur
   → Gave tribals loans at EXTREME interest rates
   → When tribals couldn't repay → seized their ancestral lands
   → Tribals became bonded labourers (BETHEGARI system) on their own land!
   
2. BRITISH FOREST ACTS (1878):
   → Reserved Forests declared — tribals BANNED from entering forests
   → Could no longer collect firewood, fruits, hunt game, graze animals
   → Forests = core of tribal life → suddenly illegal!
   → Tribals lost their PRIMARY source of livelihood overnight
   
3. ZAMINDARI/LANDLORD SYSTEM:
   → Non-tribal landlords (thikadars) given control over tribal lands
   → Tribals had to pay rent for land they had owned for generations
   → Couldn't afford rent → eviction → landlessness
   
4. CHRISTIAN MISSIONARIES:
   → Active conversion campaigns in Chota Nagpur
   → Traditional tribal culture, dances, festivals being eroded
   → Birsa saw this as cultural attack on Munda identity
   
BIRSA'S RESPONSE: "ABUA DIS-OM RE ABUA RAJA" (Our land, our rule!)
```

### Birsa as Dharmical (Religious) Leader:

```
BIRSA'S RELIGIOUS MOVEMENT (1895-1900):

He declared himself the messenger of Singbonga (the Sun God / supreme deity):
  → "Sing" = Sun, "Bonga" = God in Mundari
  
HIS PROCLAMATIONS:
  → Stop paying rent to landlords (they have NO right to our land)
  → Reject alcohol (traditional problem in tribal communities)
  → Stop eating beef (to connect with Hindu communities)
  → Abandon Christian conversion attempts
  → Return to the SARNA religion (original Munda tribal religion)
  → Purify tribal society
  
MIRACLES ATTRIBUTED TO HIM:
  → Claimed to heal the sick
  → Said to make the blind see
  → Followers believed he could stop British bullets with magic!
  
This religious authority was CRUCIAL — it mobilised thousands who might not
have joined a purely political movement.

HE WAS CALLED:
  → "DHARTI ABBA"   = Father of the Earth
  → "BHAGWAN BIRSA" = God Birsa (by followers)
  → "BIRSA BHAGWAN" in tribal songs and oral traditions
```

### First Arrest (1895):

```
FIRST ARREST: 1895
  → British authorities alarmed by Birsa's growing influence
  → Arrested for spreading sedition and inciting tribals
  → Imprisoned for 2 years in Hazaribag Jail (1895-1897)

EFFECT OF IMPRISONMENT:
  → Made him MORE famous — tribals saw him as a martyr
  → Upon release (1897), his following had GROWN!
  → Now moved from purely religious message to ARMED REVOLT
```

### The ULGULAN (1899-1900) — The Great Revolt:

```
ULGULAN = "The Great Tumult" / "The Great Revolt"
           (from Mundari word for disorder/uprising)

PREPARATION (1897-1899):
  → Birsa organised his followers militarily
  → Weapons: bows and arrows, axes, farming tools
  → Strategy: Guerrilla warfare against British forces and landlords
  → Network: Spread across Khunti, Ranchi, Singhbhum districts

THE REVOLT BEGINS (December 1899):
  → Christmas Eve 1899: Birsa's forces attacked missionary churches and 
    police outposts near Khunti
  → January 1900: Armed attacks on British establishments and landlord properties
  → Goal: Drive out British, Diku moneylenders, missionaries from Chota Nagpur
          Establish "Birsa Raj" — Munda self-rule

BRITISH RESPONSE:
  → Deployed large military forces
  → Superior weapons (guns) vs tribal bows and arrows
  → January-February 1900: Systematic crackdown

BATTLE OF DOMBARI HILL (9 January 1900):
  → Major confrontation at Dombari Hill (Khunti)
  → British forces fired upon gathered Mundas
  → Hundreds of tribals killed — the "Jallianwala" of the tribal movement
  → Birsa and remaining followers fled into forests

CAPTURE:
  → Birsa Munda captured on 3 FEBRUARY 1900
  → Location: Jamkopai forest, near Chakradharpur
  → Arrested by British forces; brought to Ranchi Jail
```

### Death and Legacy:

```
DEATH IN PRISON:
  → Died: 9 JUNE 1900 in RANCHI JAIL
  → Official British cause: CHOLERA
  → Tribals (and many historians) believe: POISONED by British
  → Age at death: 25 years
  → Duration of revolt: approximately 6 months (Dec 1899 - Feb 1900)

IMMEDIATE AFTERMATH:
  → Mass trials — hundreds imprisoned, transported
  → Birsa's closest followers sentenced to long terms
  → British shaken by the scale of tribal resistance

LONG-TERM LEGACY:
  
  1. CHOTA NAGPUR TENANCY ACT (1908):
     → DIRECT legislative response to Birsa's movement
     → Prohibited transfer of tribal land to NON-TRIBALS
     → Still in force today in Jharkhand!
     → Considered Birsa's GREATEST legal legacy
  
  2. CHOTANAGPUR TENANCY AMENDMENT:
     → Repeatedly amended to strengthen tribal protections
  
  3. JHARKHAND STATE:
     → Demand for a separate state for Adivasis of Chota Nagpur
     → Jharkhand created on 15 November 2000
     → DATE CHOSEN = Birsa Munda's birthday! (15 November)
  
  4. NATIONAL RECOGNITION:
     → Portrait in Central Hall of INDIAN PARLIAMENT
       (One of very few non-mainstream leaders given this honour)
     → Birsa Munda Airport, Ranchi — named after him
     → Birsa Institute of Technology, Dhanbad — named after him
     → Birsa Agricultural University, Ranchi — named after him
     → His image on Indian currency notes (₹5 coin, postal stamps)
  
  5. INSPIRATION FOR LATER MOVEMENTS:
     → Inspired Jharkhand tribal rights movement
     → Model for tribal self-determination
     → Celebrated as FIRST tribal freedom fighter
```

### Timeline of Birsa Munda's Life:

```
1875  Born, 15 November, Ulihatu village, Khunti, Chota Nagpur
      │
1886  Attends missionary school, Chaibasa (age ~11)
      │
1890  Returns from school; witnesses tribal exploitation firsthand
      │
1895  Declares himself DIVINE MESSENGER of Singbonga
      │ British arrest him for sedition
      │ Imprisoned in Hazaribag Jail
      │
1897  RELEASED from jail → following has grown enormously
      │ Shifts from religious to political-military planning
      │
1899  Dec: ULGULAN BEGINS — attacks on churches, police posts
Dec 24│
      │
1900  Jan: Full-scale revolt across Khunti, Ranchi
9 Jan │ BATTLE OF DOMBARI HILL — British massacre of tribals
      │
3 Feb │ BIRSA MUNDA CAPTURED at Jamkopai forest
      │
9 Jun │ DIES IN RANCHI JAIL (official: cholera; age: 25)
      │
1908  CHOTA NAGPUR TENANCY ACT — direct legacy of Ulgulan
      │
2000  JHARKHAND STATE created on 15 November (Birsa's birthday)
```

---

## 🔷 SECTION 2: REVOLUTIONARY MOVEMENTS — QUICK REVISION

### ANUSHILAN SAMITI — Rapid Revision:

```
FOUNDED:    1902, Calcutta
FOUNDERS:   Pramathanath Mitra; Barindra Kumar Ghosh (active leader)
DHAKA BRANCH: 1906, Pulin Bihari Das (most radical branch)
COVER:      Physical training societies (gymnasiums) — hide revolutionary activities

KEY EVENTS:
  → Alipore Bomb Case (1908): Khudiram Bose + Prafulla Chaki
    → Muzaffarpur bomb attack on Magistrate Kingsford (missed target)
    → Prafulla Chaki: killed himself upon arrest
    → Khudiram Bose: HANGED on 11 August 1908, age 18 (youngest martyr!)
    → Aurobindo Ghosh: arrested in Alipore Bomb Case, later ACQUITTED

AUROBINDO GHOSH CONNECTION:
  → Sri Aurobindo = intellectual backing for revolutionary Bengal
  → After acquittal, turned to spiritualism — left politics
  → Established ashram in Pondicherry
  → His younger brother Barindra = active Anushilan member

IDEOLOGY: Hindu religious symbolism + violent resistance + Bankim's "Anandamath"

🎯 PYQ MEMORY TRICK: 
  Anushilan = "Practice" → They "practiced" revolution in gymnasia
  1902 = year of founding (just after Queen Victoria died in 1901)
```

### ABHINAV BHARAT — Rapid Revision:

```
FOUNDED:    1904, Nasik, Maharashtra
FOUNDER:    Vinayak Damodar Savarkar (V.D. Savarkar / Veer Savarkar)
MEANING:    Abhinav = "New/Young" + Bharat = India → "Young India"
INSPIRED BY: Giuseppe Mazzini's "Young Italy" movement

KEY CONTRIBUTIONS:
  → First to demand PURNA SWARAJ (complete independence)
    (Congress at this time only asked for "dominion status"!)
  → Savarkar's book: "The Indian War of Independence, 1857"
    → First to call 1857 a WAR OF INDEPENDENCE (not a mutiny)
  → Connected with India House, London (Shyamji Krishna Varma)
  → Smuggled pistols from Paris via Madame Bhikaji Cama

NASIK CONSPIRACY CASE (1909-1910):
  → Anant Laxman Kanhere (Abhinav Bharat member) assassinated
    A.M.T. Jackson, Collector of Nasik
  → Pistols traced to Savarkar
  → Savarkar arrested in London, tried to escape at Marseilles (CAUGHT)
  → Sentenced: 50 YEARS imprisonment (two consecutive 25-year terms!)
  → Sent to CELLULAR JAIL (KALA PANI), Port Blair, Andaman Islands

CELLULAR JAIL:
  → Also called "Kala Pani" (Black Waters)
  → Most feared punishment in colonial India
  → Today: National Memorial, Port Blair
  → Savarkar's cell can be visited!

🎯 PYQ MEMORY TRICK:
  Abhinav Bharat = ABhi Nav (newly born) India = NEW India Society
  Nasik 1904 = N(4) A(bharat) S(avarkar) I(independence) K(ala Pani)
```

### GHADAR PARTY — Rapid Revision:

```
FOUNDED:    21 April 1913, San Francisco, California, USA
MEANING:    Ghadar = REVOLT / MUTINY (Urdu-Punjabi) — invokes 1857
FOUNDERS:   Sohan Singh Bhakna (President), Har Dayal (intellectual)
HQ:         Astoria, Oregon (later San Francisco)

NEWSPAPER "GHADAR":
  → First issue: 1 NOVEMBER 1913
  → Languages: Punjabi, Urdu, Hindi, Gujarati, Pashto (5+ languages!)
  → Tagline: "Angrezi Raj ka Dushman" (Enemy of British Rule)
  → Distributed FREE — funded by diaspora donations
  → Smuggled into India and British colonies

MEMBERSHIP:
  → Primarily PUNJABI SIKH workers and former soldiers in North America
  → Also Hindus and Muslims — INCLUSIVE, non-communal ideology
  → International network: USA, Canada, Philippines, Fiji, Singapore, Hong Kong

GHADAR MUTINY 1915:
  → CONTEXT: World War I (1914) — Britain fighting Germany
  → PLAN: Return to India, incite Indian soldiers to mutiny against British
  → RETURN: Thousands of Ghadarites sailed back to India (1914-15)
  → FAILURE: INFORMERS revealed plans to British intelligence
  → RESULT: Mass arrests at Indian ports; 42 EXECUTED
    → Including KARTAR SINGH SARABHA (age 19!) — hanged 16 Nov 1915
  → Hundreds more imprisoned, transported to Kala Pani

KARTAR SINGH SARABHA:
  → Youngest major Ghadar revolutionary; 19 years when hanged
  → From Sarabha village, Ludhiana, Punjab
  → Bhagat Singh kept his PHOTO in his pocket at all times!
  → Called him his "Guru" and "ideal"

🎯 PYQ KEY DISTINCTIONS:
  → Ghadar was INTERNATIONAL (not India-based like Anushilan/Abhinav Bharat)
  → Ghadar was NON-COMMUNAL (Sikhs + Hindus + Muslims together!)
  → 1913 = founding year (during Delhi Durbar preparations)
  → Sohan Singh Bhakna = President (not Har Dayal, who was intellectual)
```

---

## 🔷 SECTION 3: Comparison Table — Three Revolutionary Organisations

```
┌──────────────────┬─────────────────┬──────────────────┬────────────────────┐
│    FEATURE       │ ANUSHILAN SAMITI│  ABHINAV BHARAT  │   GHADAR PARTY     │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Founded          │ 1902            │ 1904             │ 1913               │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Place            │ Calcutta        │ Nasik            │ San Francisco      │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Founder          │ P.N. Mitra;     │ V.D. Savarkar    │ Sohan Singh Bhakna │
│                  │ Barindra Ghosh  │                  │ (Har Dayal = intel)│
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Region           │ Bengal          │ Maharashtra      │ Punjab (diaspora)  │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Base             │ India (Bengal)  │ India+London     │ North America      │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Inspiration      │ Bankim's        │ Mazzini's        │ 1857 Revolt spirit │
│                  │ Anandamath      │ Young Italy      │                    │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Key Event        │ Alipore Bomb    │ Nasik Conspiracy │ Ghadar Mutiny 1915 │
│                  │ Case (1908)     │ (1909)           │ (FAILED)           │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Key Martyr       │ Khudiram Bose   │ Anant Kanhere    │ Kartar Singh       │
│                  │ (age 18, 1908)  │                  │ Sarabha (age 19)   │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Communal?        │ Hindu-leaning   │ Hindu-leaning    │ NON-COMMUNAL       │
│                  │                 │                  │ (Sikh+Hindu+Muslim)│
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Newspaper        │ None (books)    │ None (books)     │ "Ghadar" newspaper │
├──────────────────┼─────────────────┼──────────────────┼────────────────────┤
│ Outcome          │ Suppressed;     │ Savarkar 50 yrs  │ 1915 mutiny failed;│
│                  │ members jailed  │ Kala Pani         │ 42 hanged          │
└──────────────────┴─────────────────┴──────────────────┴────────────────────┘
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: All Types of DBMS Keys, Differences, Constraints

---

**Q1.** A KEY in a database is used to:
(A) Encrypt the database for security
(B) Uniquely identify each row (record) in a table
(C) Connect the database to the internet
(D) More than one of the above
(E) None of the above

---

**Q2.** A SUPER KEY is defined as:
(A) The most important key in the database
(B) Any attribute or set of attributes that can uniquely identify a row (may have redundant attributes)
(C) The key that links two tables
(D) More than one of the above
(E) None of the above

---

**Q3.** A CANDIDATE KEY is:
(A) Any key that could potentially become a primary key in the future
(B) A minimal super key — removing any attribute destroys uniqueness
(C) A key used only in hierarchical databases
(D) More than one of the above
(E) None of the above

---

**Q4.** Which of the following is TRUE about a PRIMARY KEY?
(A) A table can have multiple primary keys
(B) Primary key values can be NULL if the record is incomplete
(C) A table can have only ONE primary key, and it cannot be NULL
(D) More than one of the above
(E) None of the above

---

**Q5.** Consider the STUDENTS table with columns: RollNo, Name, Email, Phone, Marks.
RollNo, Email, and Phone each uniquely identify a student. Which are CANDIDATE KEYS?
(A) Only RollNo (as it was chosen as primary key)
(B) {RollNo, Name} and {Email, Phone}
(C) {RollNo}, {Email}, and {Phone} — all three are candidate keys
(D) More than one of the above
(E) None of the above

---

**Q6.** {RollNo, Name} is a super key in the STUDENTS table because RollNo alone uniquely identifies students. Is {RollNo, Name} also a Candidate Key?
(A) Yes, because it uniquely identifies each row
(B) No, because removing Name still leaves uniqueness — it is NOT minimal
(C) Yes, all super keys are candidate keys
(D) More than one of the above
(E) None of the above

---

**Q7.** A FOREIGN KEY:
(A) Is always the primary key of the same table
(B) References the PRIMARY KEY (or unique key) of another table to maintain relationships
(C) Cannot contain NULL values
(D) More than one of the above
(E) None of the above

---

**Q8.** REFERENTIAL INTEGRITY enforced by a Foreign Key means:
(A) All data must be in alphabetical order
(B) A foreign key value must either match an existing primary key value in the referenced table or be NULL
(C) Foreign keys must be numeric
(D) More than one of the above
(E) None of the above

---

**Q9.** A COMPOSITE KEY is:
(A) A primary key shared between two different tables
(B) A key consisting of two or more attributes that together uniquely identify a row
(C) A key that connects to foreign keys in multiple tables
(D) More than one of the above
(E) None of the above

---

**Q10.** In an ENROLLMENT table with columns (RollNo, CourseID, Marks, Grade), if neither RollNo nor CourseID alone is unique, but their combination is — the primary key should be:
(A) {RollNo} alone
(B) {CourseID} alone
(C) {RollNo, CourseID} as a Composite Primary Key
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following is the KEY DIFFERENCE between a PRIMARY KEY and a UNIQUE KEY?
(A) Primary Key ensures uniqueness; Unique Key does not
(B) Primary Key cannot be NULL and only one allowed per table; Unique Key can be NULL and multiple allowed
(C) Unique Key links two tables; Primary Key does not
(D) More than one of the above
(E) None of the above

---

**Q12.** Can a FOREIGN KEY have a NULL value?
(A) No — foreign key values must always reference an existing primary key
(B) Yes — a NULL foreign key means this record has no associated parent record
(C) Only if the primary key it references is also NULL
(D) More than one of the above
(E) None of the above

---

**Q13.** ALTERNATE KEYS are defined as:
(A) Keys used as alternatives to the primary key in queries
(B) All candidate keys that were NOT chosen as the primary key
(C) Foreign keys that can be used as primary keys in another table
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following statements about SUPER KEYS is CORRECT?
(A) Every Candidate Key is a Super Key, but not every Super Key is a Candidate Key
(B) Every Super Key is a Candidate Key
(C) Super Keys and Candidate Keys are completely different with no overlap
(D) More than one of the above
(E) None of the above

---

**Q15.** In a DEPARTMENTS table with DeptID as Primary Key, and a STUDENTS table with DeptID as Foreign Key, what happens if you try to DELETE a department that still has students?
(A) The department is deleted; students remain with a dangling reference
(B) DBMS enforces referential integrity — either rejects the deletion or cascades the delete
(C) The students table is automatically deleted
(D) More than one of the above
(E) None of the above

---

**Q16.** A table has 5 attributes. How many Super Keys can it theoretically have?
(A) Exactly 5
(B) Exactly 1
(C) Potentially many — any subset of attributes that uniquely identifies rows qualifies
(D) More than one of the above
(E) None of the above

---

**Q17.** Which key type LINKS two tables and maintains their relationship?
(A) Primary Key
(B) Composite Key
(C) Foreign Key
(D) More than one of the above
(E) None of the above

---

**Q18.** Can a table have MORE THAN ONE Candidate Key?
(A) No — each table has exactly one candidate key (the primary key)
(B) Yes — a table can have multiple candidate keys, but only one is chosen as primary
(C) No — candidate keys exist only in theory, not in practice
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is an example of a COMPOSITE KEY?
(A) Roll Number in a Students table (single column, unique)
(B) {Flight Number + Date} in a Flight Bookings table (both needed for uniqueness)
(C) Email address in an accounts table (single, unique column)
(D) More than one of the above
(E) None of the above

---

**Q20.** In an EMPLOYEES table where ManagerID is a Foreign Key referencing EmployeeID in the SAME EMPLOYEES table — this is called:
(A) A Composite Key
(B) A Self-Referencing (Recursive) Foreign Key
(C) A Candidate Key
(D) More than one of the above
(E) None of the above

---

**Q21.** Two students have the same name. To distinguish them, the DBMS uses:
(A) The Name column (since their values are identical, DBMS knows they're different)
(B) A Primary Key (like RollNo or StudentID) that is unique for each student
(C) The DBMS cannot distinguish students with the same name
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following is CORRECT about a UNIQUE KEY?
(A) A table can have only one Unique Key
(B) Unique Key values must never be NULL
(C) A table can have multiple Unique Keys, and they allow NULL values
(D) More than one of the above
(E) None of the above

---

**Q23.** The relationship SUPER KEY ⊃ CANDIDATE KEY means:
(A) All Super Keys are also Candidate Keys
(B) All Candidate Keys are Super Keys, but some Super Keys are NOT Candidate Keys
(C) Candidate Keys and Super Keys are unrelated concepts
(D) More than one of the above
(E) None of the above

---

**Q24.** Consider: A BANK DATABASE has ACCOUNTS table (AccountNo as PK) and TRANSACTIONS table (TransactionID as PK, AccountNo as FK).
If a customer closes their account (AccountNo deleted from ACCOUNTS), what should happen to their transactions in TRANSACTIONS table?
(A) Transactions remain with AccountNo now invalid — creates orphan records (BAD)
(B) DBMS either rejects the deletion of the account (RESTRICT) or deletes all transactions too (CASCADE)
(C) Transactions automatically move to a backup table
(D) More than one of the above
(E) None of the above

---

**Q25.** A student is asked: "Which keys can be NULL?"
The CORRECT answer is:
(A) Primary Key and Candidate Key can be NULL; Foreign Key and Unique Key cannot
(B) Foreign Key and Unique Key can be NULL; Primary Key cannot be NULL
(C) All keys can be NULL in DBMS
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Birsa Munda (Deep Dive) + Anushilan Samiti + Abhinav Bharat + Ghadar Party Revision

---

**Q26.** Birsa Munda was born in which village and district?
(A) Ranchi city, Ranchi district
(B) Ulihatu village, Khunti district, Chota Nagpur
(C) Chakradharpur, Singhbhum district
(D) More than one of the above
(E) None of the above

---

**Q27.** What does "Diku" mean in the context of the Munda tribal society?
(A) A traditional tribal dance form
(B) An outsider/non-tribal (usually moneylenders and traders who exploited tribals)
(C) A type of forest product collected by Mundas
(D) More than one of the above
(E) None of the above

---

**Q28.** The Munda tribal revolt led by Birsa Munda is known as "Ulgulan." What period did it cover?
(A) 1857-1858
(B) 1899-1900
(C) 1919-1920
(D) More than one of the above
(E) None of the above

---

**Q29.** The "Battle of Dombari Hill" during the Ulgulan is historically compared to which other event?
(A) Battle of Plassey — British victory over Indian forces
(B) Jallianwala Bagh Massacre — British firing on unarmed/lightly-armed gathered people
(C) Battle of Panipat — decisive confrontation for territorial control
(D) More than one of the above
(E) None of the above

---

**Q30.** Birsa Munda was first arrested in 1895 and sent to which jail?
(A) Ranchi Jail
(B) Andaman Cellular Jail (Kala Pani)
(C) Hazaribag Jail
(D) More than one of the above
(E) None of the above

---

**Q31.** What was Birsa Munda's PRIMARY religious deity that he claimed to speak for?
(A) Lord Shiva (Hindu deity)
(B) Singbonga (Sun God / supreme deity in Munda tribal religion)
(C) Jesus Christ (Christian God — from his missionary education)
(D) More than one of the above
(E) None of the above

---

**Q32.** The Chota Nagpur Tenancy Act (1908) was a direct legislative consequence of:
(A) The Ghadar Mutiny of 1915
(B) The Santhal Uprising of 1855
(C) Birsa Munda's Ulgulan (1899-1900) — protecting tribal land rights
(D) More than one of the above
(E) None of the above

---

**Q33.** Birsa Munda's image is placed in:
(A) The Red Fort museum in Delhi
(B) The Central Hall of the Indian Parliament
(C) The National Museum in New Delhi
(D) More than one of the above
(E) None of the above

---

**Q34.** Why is 15 November significant both for Birsa Munda and for Jharkhand?
(A) It is the date of Birsa's death and also Independence Day of Jharkhand
(B) It is Birsa Munda's birthday (1875) and also Jharkhand's Foundation Day (2000)
(C) It is the date of the Ulgulan's beginning and Jharkhand's first election
(D) More than one of the above
(E) None of the above

---

**Q35.** Birsa Munda was captured on 3 February 1900 from which location?
(A) Dombari Hill, Khunti
(B) Jamkopai forest, near Chakradharpur
(C) Ranchi city centre
(D) More than one of the above
(E) None of the above

---

**Q36.** The Anushilan Samiti used physical training organisations as a COVER for their activities. What was the name of the famous case that exposed their revolutionary activities?
(A) Chittagong Armoury Raid (1930)
(B) Alipore Bomb Case (1908)
(C) Nasik Conspiracy Case (1909)
(D) More than one of the above
(E) None of the above

---

**Q37.** Khudiram Bose and Prafulla Chaki attempted to bomb whose carriage at Muzaffarpur in 1908?
(A) The Governor of Bengal
(B) District Magistrate Kingsford
(C) The Viceroy of India
(D) More than one of the above
(E) None of the above

---

**Q38.** Sri Aurobindo (Aurobindo Ghosh) was connected to which revolutionary organisation and what was the outcome of his involvement?
(A) Ghadar Party — he was deported to Andaman
(B) Anushilan Samiti — arrested in Alipore Bomb Case but ACQUITTED; then turned to spiritualism
(C) Abhinav Bharat — sentenced to 50 years imprisonment
(D) More than one of the above
(E) None of the above

---

**Q39.** Abhinav Bharat's ideology was primarily inspired by which foreign revolutionary?
(A) Karl Marx — socialist revolution
(B) Vladimir Lenin — Russian Revolution
(C) Giuseppe Mazzini — "Young Italy" movement for Italian independence
(D) More than one of the above
(E) None of the above

---

**Q40.** V.D. Savarkar was arrested in London and tried to escape at which European city?
(A) Paris, France
(B) Marseilles, France (while being transported back to India)
(C) Rome, Italy
(D) More than one of the above
(E) None of the above

---

**Q41.** Who founded the Ghadar Party and what was his role?
(A) Har Dayal — founder and president
(B) Sohan Singh Bhakna — founder and first president; Har Dayal was the intellectual leader
(C) Kartar Singh Sarabha — founder; Sohan Singh Bhakna was intellectual leader
(D) More than one of the above
(E) None of the above

---

**Q42.** The Ghadar newspaper was DISTINCTIVE in that:
(A) It was published only in English for educated elites
(B) It was published in multiple languages (Punjabi, Urdu, Hindi, Gujarati, Pashto) and distributed free of cost
(C) It was published from London and had British government funding
(D) More than one of the above
(E) None of the above

---

**Q43.** The 1915 Ghadar Mutiny was planned to coincide with:
(A) India's Independence Day
(B) World War I — taking advantage of Britain being distracted fighting Germany
(C) The Delhi Durbar celebrations of King George V
(D) More than one of the above
(E) None of the above

---

**Q44.** Kartar Singh Sarabha of the Ghadar Party is specially remembered for:
(A) Writing the most revolutionary pamphlets in the Ghadar newspaper
(B) Being hanged at age 19 in 1915 and being the primary inspiration for Bhagat Singh
(C) Founding the Dhaka Anushilan Samiti
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following correctly states where Birsa Munda DIED?
(A) Cellular Jail, Port Blair, Andaman Islands
(B) Ranchi Jail, on 9 June 1900
(C) Hazaribag Jail, during his second imprisonment
(D) More than one of the above
(E) None of the above

---

**Q46.** The Bethegari system, against which Birsa Munda revolted, was:
(A) A type of tax imposed on tribal religious practices
(B) Forced/bonded labour imposed on tribals by non-tribal landlords
(C) A British educational system for tribal children
(D) More than one of the above
(E) None of the above

---

**Q47.** Match the following correctly:
1. Anushilan Samiti — (i) 1913, San Francisco
2. Abhinav Bharat — (ii) 1902, Calcutta
3. Ghadar Party — (iii) 1904, Nasik

(A) 1-(ii), 2-(iii), 3-(i) — Anushilan=Calcutta, Abhinav=Nasik, Ghadar=SF
(B) 1-(i), 2-(ii), 3-(iii)
(C) 1-(iii), 2-(i), 3-(ii)
(D) More than one of the above
(E) None of the above

---

**Q48.** The BIRSA MUNDA AIRPORT is located in which city?
(A) Dhanbad, Jharkhand
(B) Ranchi, Jharkhand
(C) Patna, Bihar
(D) More than one of the above
(E) None of the above

---

**Q49.** Which statement about the GHADAR PARTY is INCORRECT?
(A) It was founded in 1913 in San Francisco, USA
(B) Its membership was exclusively Sikh — Hindus and Muslims were not members
(C) It published the newspaper "Ghadar" in multiple languages
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following pairs:
I.   Dhaka Anushilan Samiti — Pulin Bihari Das
II.  Abhinav Bharat — V.D. Savarkar — Inspired by Young Italy
III. Ghadar Party — Sohan Singh Bhakna — 1913 — San Francisco
IV.  Birsa Munda — "Dharti Abba" — Munda tribe — CNT Act 1908

How many of the above pairs are CORRECTLY matched?
(A) Only I and II
(B) Only II and III
(C) All four (I, II, III, IV) are correctly matched
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
| 1 | (B) | Key = uniquely identifies each row in a table |
| 2 | (B) | Super Key = any set (including with redundant attributes) that uniquely identifies rows |
| 3 | (B) | Candidate Key = MINIMAL super key — nothing removable |
| 4 | (C) | ONE primary key per table; CANNOT be NULL |
| 5 | (C) | All three (RollNo, Email, Phone) are minimal unique identifiers = candidate keys |
| 6 | (B) | {RollNo, Name} is not minimal — Name is redundant; NOT a candidate key |
| 7 | (B) | Foreign Key references PK of another table for relationships |
| 8 | (B) | Referential Integrity = FK must match existing PK or be NULL |
| 9 | (B) | Composite Key = two or more attributes combined as a key |
| 10 | (C) | Neither alone is unique; combined {RollNo, CourseID} = Composite PK |
| 11 | (B) | PK: no NULL, one per table; Unique Key: NULL allowed, multiple per table |
| 12 | (B) | Foreign Key CAN be NULL (record with no parent association) |
| 13 | (B) | Alternate Keys = all candidate keys NOT chosen as primary key |
| 14 | (A) | All Candidate Keys are Super Keys; not all Super Keys are Candidate Keys |
| 15 | (B) | Referential integrity: DBMS either rejects or cascades the delete |
| 16 | (C) | Any subset of attributes that uniquely identifies rows = super key; many possible |
| 17 | (C) | Foreign Key links two tables and enforces their relationship |
| 18 | (B) | Multiple candidate keys possible; only ONE chosen as primary |
| 19 | (B) | {Flight Number + Date} = classic composite key (both needed together) |
| 20 | (B) | FK referencing same table's PK = self-referencing (recursive) FK |
| 21 | (B) | Primary Key (unique ID) distinguishes rows with identical names |
| 22 | (C) | Multiple Unique Keys allowed per table; NULL values permitted |
| 23 | (B) | All Candidate Keys ⊆ Super Keys; not all Super Keys are minimal |
| 24 | (B) | DBMS enforces referential integrity: RESTRICT or CASCADE |
| 25 | (B) | Foreign Key and Unique Key can be NULL; Primary Key CANNOT |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Ulihatu village, Khunti district, Chota Nagpur |
| 27 | (B) | Diku = outsider/non-tribal exploiter (moneylenders, traders) |
| 28 | (B) | Ulgulan = 1899-1900 (December 1899 to February 1900) |
| 29 | (B) | Dombari Hill = British firing on tribal gathering, compared to Jallianwala |
| 30 | (C) | First arrest 1895 → Hazaribag Jail (NOT Andaman) |
| 31 | (B) | Singbonga = Sun God, supreme deity of Munda tribal religion |
| 32 | (C) | CNT Act 1908 = direct result of Ulgulan to protect tribal land |
| 33 | (B) | Central Hall of Indian Parliament has Birsa's portrait |
| 34 | (B) | 15 November = Birsa's birthday (1875) + Jharkhand Foundation Day (2000) |
| 35 | (B) | Captured at Jamkopai forest, near Chakradharpur |
| 36 | (B) | Alipore Bomb Case (1908) exposed Anushilan's revolutionary activities |
| 37 | (B) | Khudiram Bose attempted to bomb Magistrate Kingsford's carriage |
| 38 | (B) | Aurobindo = Anushilan-linked; acquitted in Alipore case; became spiritual leader |
| 39 | (C) | Savarkar inspired by Giuseppe Mazzini's "Young Italy" movement |
| 40 | (B) | Savarkar tried to escape at Marseilles, France — was caught |
| 41 | (B) | Sohan Singh Bhakna = founder + president; Har Dayal = intellectual backbone |
| 42 | (B) | Multi-language, free distribution, smuggled into India |
| 43 | (B) | Planned for WWI — Britain distracted by Germany; 1914-15 window |
| 44 | (B) | Hanged age 19 (Nov 1915); Bhagat Singh's primary inspiration |
| 45 | (B) | Died in Ranchi Jail, 9 June 1900 |
| 46 | (B) | Bethegari = forced/bonded labour system on tribal lands |
| 47 | (A) | 1-Anushilan=Calcutta(ii); 2-Abhinav=Nasik(iii); 3-Ghadar=SF(i) |
| 48 | (B) | Birsa Munda Airport is in Ranchi, Jharkhand |
| 49 | (B) | Statement B is INCORRECT — Ghadar was NON-COMMUNAL (Sikh+Hindu+Muslim) |
| 50 | (C) | All four pairs are correctly matched |

---
---

# 🔁 DAY 37 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — DBMS Keys

### The Key Hierarchy — One Paragraph:
```
Start with SUPER KEYS (any set of attributes that uniquely identifies rows — 
may have redundant extras). Remove redundant attributes → get CANDIDATE KEYS 
(minimal super keys). Choose ONE candidate key as PRIMARY KEY (cannot be NULL, 
only one per table). Remaining candidate keys = ALTERNATE KEYS. 
FOREIGN KEY links two tables by referencing another table's PK (can be NULL). 
COMPOSITE KEY = multiple attributes combined as one key. 
UNIQUE KEY = unique + can be NULL (unlike PK).
```

### One-Liner Definitions:
```
Super Key:     Any unique-identifying set (may have extras)
Candidate Key: MINIMAL super key (nothing removable without losing uniqueness)
Primary Key:   ONE chosen candidate key; NOT NULL; UNIQUE; only ONE per table
Foreign Key:   References PK of another table; CAN be NULL; enforces referential integrity
Composite Key: Key made of 2+ attributes combined (when no single attribute is unique)
Unique Key:    Ensures uniqueness; CAN be NULL; MULTIPLE per table allowed
Alternate Key: Candidate keys NOT chosen as primary key
```

### Critical Differences — Must Know:
```
PRIMARY KEY vs UNIQUE KEY:
  Primary: Cannot be NULL | Only ONE per table
  Unique:  CAN be NULL   | MULTIPLE per table

SUPER KEY vs CANDIDATE KEY:
  Super:     May have extra attributes (not minimal)
  Candidate: Strictly minimal — remove anything = loses uniqueness

CANDIDATE KEY vs PRIMARY KEY:
  Candidate: Multiple can exist
  Primary:   ONLY ONE chosen from candidates

FOREIGN KEY vs PRIMARY KEY:
  Foreign:  References another table's PK | CAN be NULL
  Primary:  Main identifier of own table  | CANNOT be NULL
```

### PYQ Traps — 10 One-Liners:
```
✅ Only ONE Primary Key per table (but multiple candidate keys!)
✅ Primary Key CANNOT be NULL — ever!
✅ Unique Key CAN be NULL (multiple NULLs allowed too!)
✅ Foreign Key REFERENCES the PRIMARY KEY of another table (not foreign key)
✅ Foreign Key CAN be NULL
✅ Candidate Key is always MINIMAL — {RollNo, Name} where RollNo alone works = NOT candidate key
✅ Every Candidate Key IS a Super Key; not every Super Key is a Candidate Key
✅ Composite Key = MULTIPLE ATTRIBUTES in ONE table (not multiple tables!)
✅ Alternate Key = Candidate Keys - Primary Key
✅ Referential Integrity: FK must match existing PK value OR be NULL
```

---

## ⚡ RAPID FIRE — Birsa Munda & Revolutionary Movements

### Birsa Munda — 10 Must-Know Facts:
```
1. Born:       15 November 1875, Ulihatu, Khunti, Chota Nagpur
2. Tribe:      Munda (Adivasi)
3. Called:     "Dharti Abba" (Father of the Earth) + "Bhagvan Birsa"
4. Singbonga:  Supreme deity he claimed to speak for (Sun God)
5. Revolt:     ULGULAN = 1899-1900 (Dec 1899 - Feb 1900)
6. Battle:     Dombari Hill (9 Jan 1900) — compared to Jallianwala
7. Captured:   3 February 1900 at Jamkopai forest
8. Died:       9 June 1900, Ranchi Jail (age 25; officially "cholera")
9. Legacy:     CNT Act 1908 — tribal land protection (still in force!)
10. Honour:    Portrait in Parliament; Birsa Munda Airport, Ranchi;
               Jharkhand Foundation Day = 15 November (his birthday)
```

### Three Revolutionary Organisations — Flash Card:
```
ANUSHILAN SAMITI (1902, Calcutta):
  → P.N. Mitra, Barindra Ghosh; Dhaka branch: Pulin Bihari Das (1906)
  → Cover: gymnasiums/physical training
  → Key event: Alipore Bomb Case (1908) — Khudiram Bose hanged at 18

ABHINAV BHARAT (1904, Nasik):
  → V.D. Savarkar; inspired by Mazzini's Young Italy
  → First to say 1857 = "War of Independence"
  → Nasik Conspiracy (1909): Savarkar → 50 yrs → Cellular Jail (Kala Pani)

GHADAR PARTY (1913, San Francisco):
  → Sohan Singh Bhakna (president), Har Dayal (intellect)
  → Newspaper "Ghadar": multilingual, free, tagline = "Angrezi Raj ka Dushman"
  → Non-communal: Sikh+Hindu+Muslim together (unique feature!)
  → 1915 mutiny FAILED (informers); 42 hanged; Kartar Singh Sarabha (age 19)
  → Kartar Singh Sarabha = Bhagat Singh's idol
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Key hierarchy**: Super Key ⊃ Candidate Key → Primary Key (one, no NULL); Alternate Keys = remaining candidates; Foreign Key = links tables (can be NULL); Unique Key = unique but allows NULL.
2. **PK vs Unique Key**: Primary Key = ONE per table + CANNOT be NULL; Unique Key = MULTIPLE per table + CAN be NULL — this is the most tested distinction!
3. **Composite Key**: Two or more attributes combined as a key when NO single attribute alone uniquely identifies a row (example: {RollNo + CourseID} in Enrollment table).
4. **Birsa Munda**: Born 15 Nov 1875; Ulgulan 1899-1900; Dharti Abba; captured 3 Feb 1900; died Ranchi Jail 9 Jun 1900 (age 25); legacy = CNT Act 1908; 15 Nov = Jharkhand Day.
5. **Revolutionary trio**: Anushilan 1902 Calcutta (Khudiram 18 yrs, Alipore); Abhinav Bharat 1904 Nasik (Savarkar, 50 yrs, Kala Pani); Ghadar 1913 San Francisco (Sohan Singh Bhakna, Kartar Singh Sarabha 19 yrs, non-communal).

---

## 📅 DAY 38 PREVIEW — What's Coming Next:
**CS**: ER Model (Entity-Relationship Model) — Entities, Attributes (simple, composite, derived, multi-valued), Relationships, ER Diagrams, Cardinality (1:1, 1:N, M:N), Participation Constraints (Total vs Partial), Weak Entities, ER to Relational mapping
**GS**: Indian Polity — Fundamental Rights (Articles 12-35): Right to Equality (14-18), Right to Freedom (19-22), Right Against Exploitation (23-24), Right to Freedom of Religion (25-28), Cultural & Educational Rights (29-30), Right to Constitutional Remedies (32)

---

*🚀 Day 37 of 170 — You're 21.7% through. DBMS Keys are a foundational topic — every advanced DBMS concept (normalization, ER Model, SQL joins) builds on what you learned today. Master the key distinctions now to make everything easier later!*
