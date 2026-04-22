# 📅 BPSC TRE 4.0 — DAY 39 COMPLETE STUDY MODULE
### Normalization (1NF, 2NF, 3NF, BCNF) + India's Climate Zones (Geography)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Normalization — Functional Dependencies, Anomalies, 1NF to BCNF
> - Afternoon (1 hr): Geography — India's Climate Zones, Monsoon, Seasons, Factors
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Normalization in DBMS — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is Normalization?

### Real-Life Analogy — The Messy School Register:

Imagine a school teacher maintains ONE giant register with all information:

```
MESSY REGISTER (unnormalized):
┌────┬──────┬────────────┬────────────────┬──────────┬────────┬────────┐
│Roll│ Name │  Courses   │    Teachers    │ TeacherPh│ Marks  │ Grade  │
├────┼──────┼────────────┼────────────────┼──────────┼────────┼────────┤
│101 │ Ravi │CS101,Math1 │Dr.Rao,Dr.Jha   │9876,9877 │85,90   │A,A+    │
│102 │Priya │CS101,Phys1 │Dr.Rao,Dr.Gupta │9876,9878 │90,88   │A+,A    │
│101 │ Ravi │CS101       │Dr.Rao          │9876      │85      │A       │
└────┴──────┴────────────┴────────────────┴──────────┴────────┴────────┘

PROBLEMS:
→ Multiple values in one cell (CS101, Math1 in Courses column)
→ Ravi appears TWICE (duplicate data!)
→ If Dr.Rao changes his phone: must update EVERY row where CS101 appears!
→ If we delete Ravi: we LOSE Dr.Rao's phone number too!
→ Cannot add a new teacher until a student is enrolled in their course!
```

**Normalization is the process of REORGANISING this messy data into clean, structured tables — eliminating redundancy and preventing anomalies.**

### Formal Definition:
> **Normalization is the process of organising a database to reduce data redundancy and improve data integrity by decomposing tables into smaller, well-structured tables while preserving data.**

### Who Proposed Normalization?
```
PROPOSED BY: E.F. Codd (Edgar Frank Codd) — same person who proposed Relational Model
YEAR: 1970 (1NF, 2NF, 3NF); BCNF added later by Codd & Boyce
```

---

## 🔷 SECTION 2: Why Normalization? — The Three Anomalies

Before learning normal forms, understand WHY we need them — the three database anomalies:

### Original Unnormalized Table:
```
STUDENT_COURSE table (bad design):
┌────────┬──────────┬──────────┬─────────────┬───────────────┬────────────┐
│ StdID  │ StdName  │CourseID  │ CourseName  │ InstructorID  │  Marks     │
├────────┼──────────┼──────────┼─────────────┼───────────────┼────────────┤
│  101   │  Ravi    │  CS101   │ Data Structs│    I01        │   85       │
│  101   │  Ravi    │  CS201   │ Algorithms  │    I02        │   90       │
│  102   │  Priya   │  CS101   │ Data Structs│    I01        │   78       │
│  103   │  Aman    │  CS201   │ Algorithms  │    I02        │   92       │
└────────┴──────────┴──────────┴─────────────┴───────────────┴────────────┘
```

### ANOMALY 1: UPDATE ANOMALY
```
PROBLEM: "Data Structures" course is renamed to "DSA".
→ Must update EVERY row where CS101 appears!
→ Row 1: CS101 → "DSA"
→ Row 3: CS101 → "DSA"
→ If ONE row is missed → INCONSISTENCY!

TABLE AFTER PARTIAL UPDATE (INCONSISTENT STATE):
│  101   │  Ravi    │  CS101   │ DSA         │    I01        │   85  ← updated
│  101   │  Ravi    │  CS201   │ Algorithms  │    I02        │   90
│  102   │  Priya   │  CS101   │ Data Structs│    I01        │   78  ← NOT updated!
│  103   │  Aman    │  CS201   │ Algorithms  │    I02        │   92

→ CS101 now has TWO different names — DATA INCONSISTENCY!
This is the UPDATE ANOMALY.
```

### ANOMALY 2: INSERT ANOMALY
```
PROBLEM: A new course "OS" (CS301) is created, but NO student is enrolled yet.
→ We CANNOT add it to this table!
→ StdID would be NULL (no student)
→ But StdID is part of the primary key → PRIMARY KEY CANNOT BE NULL!
→ We are BLOCKED from inserting the new course.

Trying to insert:
│  NULL  │  NULL    │  CS301   │ Oper. Sys   │    I03        │  NULL │
                ↑
         REJECTED! Primary key cannot be NULL.

This is the INSERT ANOMALY — can't add data without unrelated data.
```

### ANOMALY 3: DELETE ANOMALY
```
PROBLEM: Student Aman (103) drops out and we delete his record.
→ Aman is the ONLY student in CS201.
→ When we delete Aman's row → we ALSO LOSE CS201's information!
→ We lose: CourseName "Algorithms", InstructorID I02

After deleting Aman (103):
│  101   │  Ravi    │  CS101   │ Data Structs│    I01        │   85
│  101   │  Ravi    │  CS201   │ Algorithms  │    I02        │   90
│  102   │  Priya   │  CS101   │ Data Structs│    I01        │   78
← CS201's "Algorithms" information still exists above (Ravi is in it)
← But if we delete ALL CS201 rows... that course data is GONE.

This is the DELETE ANOMALY — deleting one thing accidentally deletes another.
```

### Summary of Anomalies:
```
┌─────────────────┬───────────────────────────────────────────────────────┐
│    ANOMALY      │                     MEANING                           │
├─────────────────┼───────────────────────────────────────────────────────┤
│ Update Anomaly  │ Updating data in one place leaves other copies        │
│                 │ inconsistent (must update all copies, miss one = bad)  │
├─────────────────┼───────────────────────────────────────────────────────┤
│ Insert Anomaly  │ Cannot insert new data without including unrelated    │
│                 │ data (blocked by primary key constraints)             │
├─────────────────┼───────────────────────────────────────────────────────┤
│ Delete Anomaly  │ Deleting one piece of data accidentally deletes       │
│                 │ another unrelated piece of information                │
└─────────────────┴───────────────────────────────────────────────────────┘

NORMALIZATION SOLVES ALL THREE by separating data into focused tables.
```

---

## 🔷 SECTION 3: Functional Dependency — The Foundation

### Definition:
> **A Functional Dependency A → B means: if we know the value of A, we can determine the value of B uniquely. A is called the DETERMINANT; B is the DEPENDENT.**

### Reading A → B:
```
A → B is read as:
  "A determines B"
  OR "B is functionally dependent on A"
  OR "Knowing A tells us B"

ANALOGY: 
  Aadhaar Number → Person's Name
  (Knowing the Aadhaar number, you can find exactly one person's name)
  
  Name → Aadhaar Number? 
  NOT necessarily! Two people can have the same name.
  So Name does NOT determine Aadhaar Number.
```

### Examples from a Table:
```
STUDENT table:
┌────────┬──────────┬────────┬─────────────┬────────┐
│ StdID  │ StdName  │  City  │ CourseID    │ Marks  │
├────────┼──────────┼────────┼─────────────┼────────┤
│  101   │  Ravi    │ Patna  │   CS101     │   85   │
│  101   │  Ravi    │ Patna  │   Math101   │   90   │
│  102   │  Priya   │ Delhi  │   CS101     │   78   │
└────────┴──────────┴────────┴─────────────┴────────┘

Functional Dependencies:
  StdID → StdName     ✓ (knowing 101 → always "Ravi")
  StdID → City        ✓ (knowing 101 → always "Patna")
  CourseID → CourseName ✓ (CS101 → always "Data Structures")
  {StdID, CourseID} → Marks ✓ (knowing both → exactly one mark)
  
  StdName → StdID     ✗ (two students could have same name)
  City → StdID        ✗ (many students from same city)
  Marks → StdID       ✗ (many students could score same marks)
```

---

### TYPE 1: FULL FUNCTIONAL DEPENDENCY

```
DEFINITION: Attribute B is FULLY functionally dependent on A if:
  → B depends on ALL attributes of A (the entire key)
  → Removing ANY attribute from A destroys the dependency

EXAMPLE with Composite Key {StdID, CourseID}:

  {StdID, CourseID} → Marks  ← FULL dependency
  
  WHY FULL?
  → Marks depends on BOTH StdID AND CourseID together.
  → StdID alone → can't determine Marks (one student has DIFFERENT marks in different courses)
  → CourseID alone → can't determine Marks (different students score differently)
  → ONLY {StdID + CourseID} TOGETHER → uniquely determines Marks
  → Therefore: FULL dependency ✓
```

### TYPE 2: PARTIAL FUNCTIONAL DEPENDENCY

```
DEFINITION: Attribute B is PARTIALLY functionally dependent on composite key A if:
  → B depends on ONLY PART of the composite key (not the whole key)
  → B can be determined by a PROPER SUBSET of the composite key

EXAMPLE with Composite Key {StdID, CourseID}:

  {StdID, CourseID} → StdName  ← PARTIAL dependency!
  
  WHY PARTIAL?
  → StdName depends on ONLY StdID (not CourseID)!
  → Ravi's name is "Ravi" regardless of which course he's in.
  → StdID ALONE → determines StdName
  → The CourseID part is UNNECESSARY for determining StdName
  → Therefore: PARTIAL dependency (depends on only PART of the key)
  
  {StdID, CourseID} → CourseName  ← ALSO PARTIAL!
  → CourseID ALONE → determines CourseName (CS101 → always "Data Structures")
  → StdID is unnecessary for determining CourseName

RESULT: Partial dependencies CAUSE 2NF violations.
        Eliminating partial dependencies = achieving 2NF.
```

### TYPE 3: TRANSITIVE FUNCTIONAL DEPENDENCY

```
DEFINITION: A → B → C is a transitive dependency if:
  → A determines B
  → B determines C
  → But B is NOT a candidate key (B is not a primary identifier)
  → Therefore A "indirectly" determines C through B

  FORMAL: If A → B and B → C, then A → C (transitively)

EXAMPLE:
  STUDENT table: StdID → DeptID → DeptHeadName
  
  StdID → DeptID      (student belongs to a department — direct)
  DeptID → DeptHeadName  (department has a head — direct)
  
  Therefore: StdID → DeptHeadName (TRANSITIVE — through DeptID)
  
  DeptHeadName depends on DeptID (not directly on StdID).
  But it "transitively" depends on StdID.
  
  WHY IS THIS A PROBLEM?
  → Many students in CS dept → DeptHeadName "Dr. Rao" stored MANY TIMES
  → If Dr. Rao changes → update all student rows (UPDATE ANOMALY!)
  → DeptHeadName should be in DEPARTMENT table, NOT STUDENT table!

RESULT: Transitive dependencies CAUSE 3NF violations.
        Eliminating transitive dependencies = achieving 3NF.
```

### Dependency Types — Summary:
```
┌──────────────────┬──────────────────────────────────────────────────────┐
│  DEPENDENCY TYPE │                DEFINITION                             │
├──────────────────┼──────────────────────────────────────────────────────┤
│ Full             │ B depends on the ENTIRE composite key                │
│                  │ {StdID, CourseID} → Marks                            │
├──────────────────┼──────────────────────────────────────────────────────┤
│ Partial          │ B depends on PART of the composite key only          │
│                  │ {StdID, CourseID} → StdName (only needs StdID)       │
│                  │ ← Violation of 2NF!                                  │
├──────────────────┼──────────────────────────────────────────────────────┤
│ Transitive       │ A → B → C where B is not a candidate key            │
│                  │ StdID → DeptID → DeptHeadName                        │
│                  │ ← Violation of 3NF!                                  │
└──────────────────┴──────────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 4: FIRST NORMAL FORM (1NF)

### Rule of 1NF:
> **A table is in 1NF if and only if:**
> 1. All attribute values are ATOMIC (indivisible — no multi-valued cells)
> 2. No repeating groups (each column stores ONE value per row)
> 3. Each column has a SINGLE DATA TYPE
> 4. Each row is UNIQUE (has a primary key)

### What Violates 1NF?

```
VIOLATION 1: Multi-valued attributes in one cell
┌────────┬──────────┬─────────────────────┬────────────────┐
│ StdID  │ StdName  │      Courses        │   Phones       │
├────────┼──────────┼─────────────────────┼────────────────┤
│  101   │  Ravi    │  CS101, Math101     │ 9876, 0612-234 │  ← VIOLATION!
│  102   │  Priya   │  CS101              │ 9877           │
└────────┴──────────┴─────────────────────┴────────────────┘
"CS101, Math101" in one cell = NOT atomic = NOT 1NF!

VIOLATION 2: Repeating groups (separate columns for same type of data)
┌────────┬──────────┬──────────┬──────────┬──────────┐
│ StdID  │ StdName  │ Course1  │ Course2  │ Course3  │
├────────┼──────────┼──────────┼──────────┼──────────┤
│  101   │  Ravi    │  CS101   │  Math101 │  NULL    │  ← VIOLATION!
│  102   │  Priya   │  CS101   │  NULL    │  NULL    │
└────────┴──────────┴──────────┴──────────┴──────────┘
Course1, Course2, Course3 = repeating groups = NOT 1NF!
```

### Converting to 1NF:

```
BEFORE (not 1NF):
┌────────┬──────────┬─────────────────────┬────────┐
│ StdID  │ StdName  │      Courses        │ Marks  │
├────────┼──────────┼─────────────────────┼────────┤
│  101   │  Ravi    │  CS101, Math101     │ 85,90  │
│  102   │  Priya   │  CS101              │ 78     │
└────────┴──────────┴─────────────────────┴────────┘

AFTER converting to 1NF (separate row for each value):
┌────────┬──────────┬──────────┬────────┐
│ StdID  │ StdName  │ CourseID │ Marks  │
├────────┼──────────┼──────────┼────────┤
│  101   │  Ravi    │  CS101   │   85   │  ← One row, one course, one mark
│  101   │  Ravi    │  Math101 │   90   │  ← Separate row for second course
│  102   │  Priya   │  CS101   │   78   │
└────────┴──────────┴──────────┴────────┘
Primary Key = {StdID, CourseID} (composite)
All cells now have ATOMIC values ✓

Key changes:
✅ Each cell has exactly ONE value (atomic)
✅ No multi-valued cells
✅ No repeating column groups
✅ Composite Primary Key: {StdID, CourseID}
```

### 🎯 PYQ FACT: 1NF requires ATOMIC values in every cell. No lists, no sets, no repeating groups in columns.

---

## 🔷 SECTION 5: SECOND NORMAL FORM (2NF)

### Rule of 2NF:
> **A table is in 2NF if and only if:**
> 1. It is already in 1NF
> 2. There are NO PARTIAL DEPENDENCIES — every non-key attribute must depend on the ENTIRE primary key (not just part of it)

### Note: 2NF is only relevant when there is a COMPOSITE primary key!
```
If a table has a SINGLE-ATTRIBUTE primary key → it is automatically in 2NF
(There's no "part" of a single key to have a partial dependency on)
2NF issues arise ONLY with COMPOSITE primary keys.
```

### Identifying Partial Dependencies in our 1NF Table:

```
1NF table (from above):
┌────────┬──────────┬──────────┬──────────────┬─────────────┬────────┐
│ StdID  │ StdName  │ CourseID │  CourseName  │   Teacher   │ Marks  │
├────────┼──────────┼──────────┼──────────────┼─────────────┼────────┤
│  101   │  Ravi    │  CS101   │ Data Structs │  Dr. Rao    │   85   │
│  101   │  Ravi    │  Math101 │ Mathematics  │  Dr. Jha    │   90   │
│  102   │  Priya   │  CS101   │ Data Structs │  Dr. Rao    │   78   │
│  103   │  Aman    │  Math101 │ Mathematics  │  Dr. Jha    │   92   │
└────────┴──────────┴──────────┴──────────────┴─────────────┴────────┘

Primary Key = {StdID, CourseID}

Analyzing each non-key attribute:
  StdName:    depends on StdID alone → PARTIAL DEPENDENCY! ✗
  CourseName: depends on CourseID alone → PARTIAL DEPENDENCY! ✗
  Teacher:    depends on CourseID alone → PARTIAL DEPENDENCY! ✗
  Marks:      depends on {StdID + CourseID} TOGETHER → FULL DEPENDENCY ✓
```

### Converting to 2NF (Remove Partial Dependencies):

**Strategy:** Move partially dependent attributes to their own table based on what they depend on.

```
STEP: Identify groups of partial dependencies:
  Group 1: StdID → StdName  (student info)
  Group 2: CourseID → CourseName, Teacher  (course info)
  Group 3: {StdID, CourseID} → Marks  (enrollment info — keep this)

RESULT: Split into 3 tables:

TABLE 1: STUDENT (StdID determines StdName)
┌────────┬──────────┐
│ StdID  │ StdName  │
│  [PK]  │          │
├────────┼──────────┤
│  101   │  Ravi    │
│  102   │  Priya   │
│  103   │  Aman    │
└────────┴──────────┘

TABLE 2: COURSE (CourseID determines CourseName, Teacher)
┌──────────┬──────────────┬─────────────┐
│ CourseID │  CourseName  │   Teacher   │
│   [PK]   │              │             │
├──────────┼──────────────┼─────────────┤
│  CS101   │ Data Structs │  Dr. Rao    │
│  Math101 │ Mathematics  │  Dr. Jha    │
└──────────┴──────────────┴─────────────┘

TABLE 3: ENROLLMENT ({StdID, CourseID} determines Marks)
┌────────┬──────────┬────────┐
│ StdID  │ CourseID │ Marks  │
│  [FK]  │   [FK]   │        │
│  ════════════════ Composite PK
├────────┼──────────┼────────┤
│  101   │  CS101   │   85   │
│  101   │  Math101 │   90   │
│  102   │  CS101   │   78   │
│  103   │  Math101 │   92   │
└────────┴──────────┴────────┘

✅ No partial dependencies remain!
✅ All non-key attributes depend on the FULL primary key.
```

### Benefits Achieved:
```
BEFORE 2NF (updating "Data Structs" to "DSA"):
→ Had to update every row where CS101 appears → UPDATE ANOMALY risk

AFTER 2NF:
→ CourseName only in COURSE table, one row per course
→ Change "Data Structs" to "DSA" in ONE place → done!
→ UPDATE ANOMALY eliminated!
```

### 🎯 PYQ FACT: 2NF removes PARTIAL DEPENDENCIES. It only applies when there is a composite primary key.

---

## 🔷 SECTION 6: THIRD NORMAL FORM (3NF)

### Rule of 3NF:
> **A table is in 3NF if and only if:**
> 1. It is already in 2NF
> 2. There are NO TRANSITIVE DEPENDENCIES — no non-key attribute should determine another non-key attribute

### Finding Transitive Dependency in 2NF Tables:

```
Let's expand our STUDENT table with more attributes:

STUDENT table after 2NF:
┌────────┬──────────┬────────┬───────────┬──────────────────┐
│ StdID  │ StdName  │ DeptID │ DeptName  │ DeptHeadPhone    │
│  [PK]  │          │        │           │                  │
├────────┼──────────┼────────┼───────────┼──────────────────┤
│  101   │  Ravi    │  CS    │ Comp.Sci  │ 9876543210       │
│  102   │  Priya   │  Math  │Mathematics│ 9876543211       │
│  103   │  Aman    │  CS    │ Comp.Sci  │ 9876543210       │
│  104   │  Kavya   │  CS    │ Comp.Sci  │ 9876543210       │
└────────┴──────────┴────────┴───────────┴──────────────────┘

In 2NF? YES — DeptID, DeptName, DeptHeadPhone all depend on full key (StdID).
         (StdID is a single attribute PK — so no partial dependency possible)

TRANSITIVE DEPENDENCY present?
  StdID → DeptID       (student is in a department — direct)
  DeptID → DeptName    (department has a name — direct)
  DeptID → DeptHeadPhone (department has a head phone — direct)
  
  Therefore: StdID → DeptID → DeptName  (TRANSITIVE!)
             StdID → DeptID → DeptHeadPhone (TRANSITIVE!)
  
  DeptName and DeptHeadPhone depend on DeptID, not directly on StdID.
  They are transitively dependent on StdID through DeptID.
  
  PROBLEMS:
  → "Comp.Sci" and "9876543210" stored MULTIPLE TIMES (rows 101, 103, 104)
  → UPDATE ANOMALY: CS department phone changes → update 3 rows!
  → DELETE ANOMALY: Delete all CS students → lose CS dept info!
```

### Converting to 3NF (Remove Transitive Dependencies):

**Strategy:** Move transitively dependent attributes to their own table.

```
STEP: The culprit is DeptID → DeptName, DeptHeadPhone
      Move department info to its own table!

TABLE 1: STUDENT (no more dept details)
┌────────┬──────────┬────────┐
│ StdID  │ StdName  │ DeptID │
│  [PK]  │          │  [FK]  │
├────────┼──────────┼────────┤
│  101   │  Ravi    │  CS    │
│  102   │  Priya   │  Math  │
│  103   │  Aman    │  CS    │
│  104   │  Kavya   │  CS    │
└────────┴──────────┴────────┘
DeptID is now a FOREIGN KEY (not carrying dept details)

TABLE 2: DEPARTMENT (dept details here — no redundancy)
┌────────┬───────────┬──────────────────┐
│ DeptID │ DeptName  │ DeptHeadPhone    │
│  [PK]  │           │                  │
├────────┼───────────┼──────────────────┤
│  CS    │ Comp.Sci  │ 9876543210       │  ← stored ONCE!
│  Math  │ Maths     │ 9876543211       │  ← stored ONCE!
└────────┴───────────┴──────────────────┘

✅ No transitive dependencies!
✅ DeptName and DeptHeadPhone now depend DIRECTLY on DeptID (their PK)
✅ CS dept phone: stored ONCE → easy to update!
```

### Benefits Achieved:
```
BEFORE 3NF:
→ CS dept info in every CS student row → UPDATE ANOMALY
→ Deleting last CS student → DELETE ANOMALY

AFTER 3NF:
→ CS dept info stored ONCE in DEPARTMENT table
→ Update phone number → change 1 row → done!
→ Deleting all CS students → dept info SAFE in DEPARTMENT table
```

### 🎯 PYQ FACT: 3NF removes TRANSITIVE DEPENDENCIES. A → B → C where B is not a candidate key = transitive dependency.

---

## 🔷 SECTION 7: BOYCE-CODD NORMAL FORM (BCNF)

### Rule of BCNF:
> **A table is in BCNF if and only if:**
> For every functional dependency A → B in the table:
> A must be a SUPER KEY (specifically, a candidate key or superset of it)

### BCNF vs 3NF:
```
3NF RULE:  For A → B, either:
           (a) B is part of the primary key (prime attribute), OR
           (b) A is a super key
           
BCNF RULE: For A → B:
           (a) A MUST be a super key — NO EXCEPTIONS
           
BCNF is STRICTER than 3NF.
Every BCNF table is in 3NF, but NOT every 3NF table is in BCNF.
```

### BCNF Violation Example:
```
TEACHING table:
┌─────────┬─────────┬────────────┐
│ Student │ Subject │  Teacher   │
├─────────┼─────────┼────────────┤
│  Ravi   │  Math   │  Dr. Jha   │
│  Ravi   │  CS     │  Dr. Rao   │
│  Priya  │  Math   │  Dr. Jha   │
│  Aman   │  Math   │  Dr. Kumar │  ← Different teacher for same subject!
└─────────┴─────────┴────────────┘

Assumptions:
  → Each student takes each subject from ONE teacher
  → Each teacher teaches only ONE subject
  → Multiple teachers can teach the same subject
  
FUNCTIONAL DEPENDENCIES:
  {Student, Subject} → Teacher  (PK is composite)
  Teacher → Subject              ← PROBLEM!
  
BCNF CHECK for Teacher → Subject:
  Is "Teacher" a super key? NO! (teacher doesn't uniquely identify a row)
  → Dr. Jha appears for both Ravi and Priya
  → Teacher → Subject means "knowing the teacher determines the subject"
  → But Teacher is NOT a super key!
  → THIS VIOLATES BCNF!
  
Does it violate 3NF?
  Teacher (non-prime) → Subject (prime attribute = part of PK)
  3NF says: if B is prime attribute, A → B is allowed even if A is not a super key.
  → Teacher → Subject: Subject IS prime → 3NF says OK!
  → But BCNF says: A must ALWAYS be a super key → BCNF violated!
  
So this table is in 3NF but NOT in BCNF.
```

### BCNF Conversion:
```
SPLIT the table to remove the BCNF violation:

TABLE 1: TEACHER_SUBJECT (Teacher determines Subject)
┌────────────┬─────────┐
│  Teacher   │ Subject │
│    [PK]    │         │
├────────────┼─────────┤
│  Dr. Jha   │  Math   │
│  Dr. Rao   │  CS     │
│  Dr. Kumar │  Math   │
└────────────┴─────────┘

TABLE 2: STUDENT_TEACHER (Student + Teacher determines the pairing)
┌─────────┬────────────┐
│ Student │  Teacher   │
│  [PK1]  │   [PK2]    │  ← Composite PK
├─────────┼────────────┤
│  Ravi   │  Dr. Jha   │
│  Ravi   │  Dr. Rao   │
│  Priya  │  Dr. Jha   │
│  Aman   │  Dr. Kumar │
└─────────┴────────────┘

✅ In BCNF now — every determinant is a super key in its table.
```

---

## 🔷 SECTION 8: Complete Normalization Flow — Step by Step

### The Full Worked Example (Start to BCNF):

```
INITIAL UNNORMALIZED TABLE (UNF):
┌────────┬──────────┬────────────────────┬──────────────┬───────┐
│ StdID  │ StdName  │ Courses & Teachers │   DeptInfo   │ Marks │
├────────┼──────────┼────────────────────┼──────────────┼───────┤
│  101   │  Ravi    │CS101/Dr.Rao,Mth/Jha│CS/CompSci/Ph1│ 85,90 │
└────────┴──────────┴────────────────────┴──────────────┴───────┘
           ↓ STEP 1: Make atomic (1NF)
           
1NF TABLE:
┌────────┬──────────┬──────────┬──────────────┬────────┬────────┬──────────────┐
│ StdID  │ StdName  │ CourseID │ CourseName   │Teacher │ DeptID │ DeptName     │
│        │          │          │              │        │        │ DeptHeadPhone│
├────────┼──────────┼──────────┼──────────────┼────────┼────────┼──────────────┤
│  101   │  Ravi    │  CS101   │ Data Structs │Dr. Rao │  CS    │Comp/9876     │
│  101   │  Ravi    │  Math101 │ Mathematics  │Dr. Jha │  CS    │Comp/9876     │
│  102   │  Priya   │  CS101   │ Data Structs │Dr. Rao │  Math  │Math/9877     │
└────────┴──────────┴──────────┴──────────────┴────────┴────────┴──────────────┘
PK = {StdID, CourseID}
           ↓ STEP 2: Remove PARTIAL dependencies (2NF)
           
2NF TABLES:
  STUDENT(StdID, StdName, DeptID, DeptName, DeptHeadPhone)
  COURSE(CourseID, CourseName, Teacher)
  ENROLLMENT(StdID[FK], CourseID[FK], Marks)
           ↓ STEP 3: Remove TRANSITIVE dependencies (3NF)
           
3NF TABLES:
  STUDENT(StdID, StdName, DeptID[FK])
  DEPARTMENT(DeptID, DeptName, DeptHeadPhone)
  COURSE(CourseID, CourseName, Teacher)
  ENROLLMENT(StdID[FK], CourseID[FK], Marks)
           ↓ STEP 4: Ensure all determinants are super keys (BCNF)
           
BCNF CHECK: In COURSE table: Teacher → CourseName?
  If Teacher → Subject violates BCNF → split further.
  Otherwise → BCNF achieved.
```

---

## 🔷 SECTION 9: Normal Forms Comparison — Master Table

```
┌─────────┬──────────────────────────────┬───────────────────────────────────────────┐
│   NF    │           RULE               │            WHAT IT REMOVES                │
├─────────┼──────────────────────────────┼───────────────────────────────────────────┤
│   UNF   │ No rules                     │ Starting point — messy data               │
│(Unnorm) │                              │                                           │
├─────────┼──────────────────────────────┼───────────────────────────────────────────┤
│   1NF   │ Atomic values                │ Multi-valued cells, repeating groups       │
│         │ No repeating groups          │ "CS101, Math101" in one cell              │
├─────────┼──────────────────────────────┼───────────────────────────────────────────┤
│   2NF   │ In 1NF                       │ PARTIAL DEPENDENCIES                      │
│         │ + No partial dependency      │ Non-key attr depending on PART of PK      │
│         │   on composite PK            │ (only relevant with composite PK)         │
├─────────┼──────────────────────────────┼───────────────────────────────────────────┤
│   3NF   │ In 2NF                       │ TRANSITIVE DEPENDENCIES                   │
│         │ + No transitive dependency   │ A → B → C where B is not candidate key    │
│         │   (X → Y where Y→Z, Z is    │ "Most practical normal form for RDBMS"    │
│         │   non-key attribute)         │                                           │
├─────────┼──────────────────────────────┼───────────────────────────────────────────┤
│  BCNF   │ In 3NF                       │ Even BCNF violations in 3NF tables        │
│(Boyce-  │ + For every A → B,           │ Every determinant must be a candidate key │
│ Codd)   │   A must be a super key      │ STRONGER version of 3NF                   │
└─────────┴──────────────────────────────┴───────────────────────────────────────────┘
```

### Flowchart: UNF → 1NF → 2NF → 3NF → BCNF

```
START: Unnormalized Table
           │
           ▼
    ┌─────────────────────────────────┐
    │           1NF TEST              │
    │ All values atomic?              │
    │ No repeating groups?            │
    └──────────────┬──────────────────┘
                   │ YES → 1NF achieved
                   ▼
    ┌─────────────────────────────────┐
    │           2NF TEST              │
    │ Composite PK present?           │
    │ If YES: Any non-key attr        │
    │ depend on PART of PK only?      │
    └──────────────┬──────────────────┘
                   │ YES → Partial dependency found
                   │ → Split table: separate partial
                   │   dependents into own table
                   ▼ NO partial deps → 2NF achieved
    ┌─────────────────────────────────┐
    │           3NF TEST              │
    │ Any A → B → C where B is       │
    │ not a candidate key?            │
    └──────────────┬──────────────────┘
                   │ YES → Transitive dependency found
                   │ → Move B and its dependents to
                   │   separate table (B becomes FK)
                   ▼ NO transitive deps → 3NF achieved
    ┌─────────────────────────────────┐
    │          BCNF TEST              │
    │ For every A → B:                │
    │ Is A a super key?               │
    └──────────────┬──────────────────┘
                   │ NO → BCNF violation
                   │ → Decompose further
                   ▼ All A's are super keys → BCNF achieved
    ✅ FULLY NORMALIZED DATABASE
```

---

## 🔷 SECTION 10: PYQ Traps Summary

```
TRAP 1: "Normalization increases redundancy"
  → FALSE! Normalization DECREASES (reduces) redundancy.

TRAP 2: "2NF is applicable even with single-attribute primary key"
  → Partially FALSE! 2NF issues arise specifically with COMPOSITE keys.
    A table with single-attribute PK is automatically 2NF compliant
    (no "part" of a single key to have partial dependency on).

TRAP 3: "3NF is rarely used in practice"
  → FALSE! 3NF is the MOST COMMONLY USED normal form in real databases.
    Most RDBMS designs aim for 3NF as sufficient.

TRAP 4: "BCNF and 3NF are always equivalent"
  → FALSE! Every BCNF table IS in 3NF. But NOT every 3NF is in BCNF.
    BCNF is STRICTER than 3NF.

TRAP 5: "Normalization never causes any data loss"
  → TRUE — Normalization should be LOSSLESS (data can be reconstructed
    by joining the decomposed tables back together).

TRAP 6: "2NF removes transitive dependencies"
  → FALSE! 2NF removes PARTIAL dependencies.
    3NF removes TRANSITIVE dependencies.

TRAP 7: "1NF allows multi-valued cells as long as they are consistent"
  → FALSE! 1NF requires ALL cells to be ATOMIC — no exceptions.

TRAP 8: "If A → B and B → C, then this is always a violation"
  → DEPENDS on B! If B is a candidate key, A → B → C is fine (B is a key).
    Only a violation if B is NOT a candidate key.

TRAP 9: "Normalization is only about primary keys"
  → FALSE! It's about ALL functional dependencies, including those
    involving non-key attributes.

TRAP 10: "Denormalization = making the database worse"
  → NOT NECESSARILY! Denormalization is intentionally introducing
    redundancy for PERFORMANCE (faster queries by avoiding complex joins).
    Used in data warehouses and analytics databases.
```

---

# PART 2: GENERAL STUDIES
## 🌤️ Geography — India's Climate Zones

---

## 🔷 SECTION 1: Overview of India's Climate

### India's Climate Type:
```
INDIA'S CLIMATE = TROPICAL MONSOON CLIMATE (dominant)

WHY "TROPICAL"?
  → Most of India lies between Tropic of Cancer (23.5°N) and Equator
  → High temperatures throughout the year
  → Receives intense solar radiation

WHY "MONSOON"?
  → Seasonal reversal of wind direction (SW in summer, NE in winter)
  → "Monsoon" comes from Arabic word "MAUSIM" (season)
  → Rain brought by Southwest Monsoon (June-September)
  
INDIA'S UNIQUE POSITION:
  → Large landmass (thermal contrast with oceans)
  → Himalayas in the north (block cold winds, trap monsoon)
  → Three water bodies: Arabian Sea (W), Bay of Bengal (E), Indian Ocean (S)
  → Tropic of Cancer passes through 8 states
```

---

## 🔷 SECTION 2: Factors Affecting India's Climate

### Factor 1: LATITUDE
```
EFFECT: Controls the amount of solar radiation received
  → Low latitude (near equator) = More direct sun = HOT
  → High latitude (near poles) = Oblique sun = COLD

INDIA's RANGE: 8°N (Kanyakumari) to 37°N (Ladakh)
  → South India (Kerala, Tamil Nadu) = HOT, near equator
  → North India (Himachal, J&K, Ladakh) = COLD, farther from equator
  → Bihar (25°N) = Moderate to hot; Tropic of Cancer passes nearby

TROPIC OF CANCER (23.5°N) passes through:
  Gujarat → Rajasthan → MP → Chhattisgarh → Jharkhand → 
  West Bengal → Tripura → Mizoram
  (8 states — frequently asked in Bihar exams!)
```

### Factor 2: ALTITUDE
```
EFFECT: Higher altitude = COLDER temperature
        Temperature decreases by ~6.5°C per 1000 metres rise (lapse rate)

EXAMPLES:
  Mumbai (sea level): ~30°C in summer
  Shimla (2200m):     ~15°C in summer (much cooler!)
  Leh-Ladakh (3500m): Can go -30°C in winter!
  
  Ooty, Darjeeling, Mussoorie = "hill stations" because HIGH ALTITUDE
  = cooler temperatures even in tropical India

WHY HIMALAYAS ARE IMPORTANT:
  → Block COLD CENTRAL ASIAN winds from entering India in winter
  → Without Himalayas, North India would be like Central Asia (severe cold)
  → Act as a BARRIER for monsoon clouds (rain on southern side, dry Tibet to north)
```

### Factor 3: DISTANCE FROM THE SEA (Continentality)
```
EFFECT: Areas near sea = MODERATE climate (not too hot, not too cold)
        Areas far from sea = EXTREME climate (very hot in summer, very cold in winter)

WHY?
  Water heats and cools SLOWLY (high specific heat capacity)
  Land heats and cools QUICKLY
  
  Coastal areas: Sea moderates temperatures → moderate climate
  Interior India: No sea influence → temperature extremes

EXAMPLES:
  Mumbai (coastal):   Summer ~33°C, Winter ~22°C  → moderate range
  Delhi (interior):   Summer ~45°C, Winter ~5°C   → extreme range!
  
  "MARITIME INFLUENCE" vs "CONTINENTAL INFLUENCE"
  Bihar (inland) = continental climate = extreme temperatures
```

### Factor 4: MONSOON WINDS
```
EFFECT: Controls when and where it rains!

SOUTHWEST MONSOON (June-September):
  → Blows from Southwest (Arabian Sea + Bay of Bengal) toward land
  → Brings 75-80% of India's annual rainfall!
  → Main crop season: Kharif (June-Oct)
  
  TWO BRANCHES:
  Branch 1: ARABIAN SEA BRANCH
    → Hits Western Ghats first → HEAVY rainfall on western slopes
    → Rain shadow on eastern side (Deccan Plateau gets less rain)
    → Continues to Gujarat, Rajasthan (weaker)
  
  Branch 2: BAY OF BENGAL BRANCH
    → Enters Bengal/Northeast → heavy rainfall in NE India
    → Moves westward along Gangetic Plains (Bihar gets this!)
    → Reaches western India last

NORTHEAST MONSOON (October-December):
  → Blows from Northeast (from land toward sea)
  → Cold, dry wind — NOT a major rainfall carrier for most India
  → EXCEPTION: Tamil Nadu coast gets rain from NE monsoon!
    (When winds cross Bay of Bengal, pick up moisture, rain on Tamil Nadu)
  
  🎯 PYQ: Tamil Nadu gets most rain from NORTHEAST MONSOON (not SW!)
           Rest of India = mainly SW monsoon rain.

MONSOON WORD ORIGIN: Arabic "MAUSIM" = season
```

### Factor 5: OCEAN CURRENTS
```
EFFECT: Warm currents = warmer weather; Cold currents = cooler, foggy

India's relevant currents:
  → WARM INDIAN OCEAN water in summer → evaporation → monsoon formation
  → Bay of Bengal is warm → storms and cyclones in Oct-Nov (post-monsoon)
```

### Factor 6: RELIEF (Mountains, Plateaus)
```
EFFECT: Mountains act as barriers; valleys channel winds

EXAMPLES:
  → Western Ghats: Block Arabian Sea monsoon → wet coast, dry Deccan
  → Himalayas: Block cold winds → protect North India
  → Khasi Hills (Meghalaya): Funnel monsoon → Mawsynram/Cherrapunji
    = WORLD'S WETTEST PLACE (average ~11,000 mm rainfall/year!)
    
🎯 PYQ: Mawsynram (Meghalaya) = currently world's wettest place
         Cherrapunji (Sohra) = second wettest / historically wettest
```

---

## 🔷 SECTION 3: India's Climate Zones / Types

### ZONE 1: TROPICAL RAINFOREST (Hot and Wet)
```
LOCATION: Western Ghats (Kerala, coastal Karnataka, Goa)
          Andaman & Nicobar Islands
          Parts of Northeast India (Assam, Meghalaya, Mizoram)

CHARACTERISTICS:
  → Very high rainfall (200+ cm per year)
  → Very hot and humid
  → Dense evergreen forests
  → Temperature: 25-30°C throughout year
  
SPECIAL: Mawsynram (Meghalaya) gets ~11,000 mm/year — world's wettest!
```

### ZONE 2: TROPICAL SAVANNA (Hot with Seasonal Rain)
```
LOCATION: Deccan Plateau (Maharashtra, Karnataka, AP, Telangana)
          Central India

CHARACTERISTICS:
  → Distinct wet (monsoon) and dry seasons
  → Moderate rainfall (75-150 cm)
  → Temperature: 20-35°C
  → CROPS: Cotton, Jowar (Black soil + Savanna climate)

Bihar mostly falls in this zone.
```

### ZONE 3: SEMI-ARID / TROPICAL STEPPE
```
LOCATION: Parts of Rajasthan (eastern), Karnataka Plateau, 
          Rain shadow areas of Deccan

CHARACTERISTICS:
  → Low rainfall (25-75 cm)
  → Grasslands with scattered trees
  → Hot summers, mild winters
```

### ZONE 4: ARID / DESERT CLIMATE
```
LOCATION: Rajasthan (Thar Desert), Kutch (Gujarat)

CHARACTERISTICS:
  → Extreme temperatures: +50°C in summer, near 0°C in winter nights
  → Very low rainfall (<25 cm per year)
  → Sparse vegetation — scrub, thorny plants, cacti
  
  THAR DESERT = World's 7th largest hot desert
              = Most densely populated desert in the world!
  JAISALMER = Driest city in India
  
🎯 PYQ: India's hot desert = Thar Desert (Rajasthan + parts of Gujarat, Punjab, Haryana)
```

### ZONE 5: HUMID SUBTROPICAL (North Indian Plains)
```
LOCATION: Punjab, Haryana, UP, Bihar, West Bengal (Gangetic Plains)

CHARACTERISTICS:
  → HOT summers: 40-48°C (loo winds — hot dry wind in summer!)
  → COLD winters: 5-15°C (fog, frost in parts of Bihar and UP)
  → Moderate rainfall (60-150 cm) from SW Monsoon
  → Four distinct seasons
  
  BIHAR'S CLIMATE = Humid Subtropical
  → Hot dry summers, monsoon rains (June-September), cool winters
  
🎯 PYQ: LOO = Hot dry summer wind that blows over North India plains
         LOO is associated with: Punjab, Haryana, UP, Bihar, Rajasthan
```

### ZONE 6: MOUNTAIN CLIMATE (Highland / Alpine)
```
LOCATION: Himalayas (J&K, Ladakh, HP, Uttarakhand)
          Northeast hills (Nagaland, Manipur at altitude)

CHARACTERISTICS:
  → Temperature decreases with altitude
  → Below treeline: Temperate forests
  → Above treeline: Alpine meadows (Bugyals)
  → Permanent snow: Himalayan peaks (above 5000m)
  → Very COLD winters (Dras in J&K = coldest inhabited place in India!)
  
DRAS, LADAKH: Sometimes recorded at -45°C! 
              Called the "Ice Box of India" / "Coldest place in India (inhabited)"
```

---

## 🔷 SECTION 4: India's Four Seasons

```
SEASON 1: WINTER (December – February)
  Temperature: Low (5-25°C in plains; below 0°C in hills)
  Wind: NORTHEAST MONSOON (dry, cold from land to sea)
  Rainfall: Western Disturbances → rain/snow in NW India
            Tamil Nadu coast: gets rain from retreating NE monsoon
  
  WESTERN DISTURBANCES: Cold weather systems from Mediterranean region
    → Bring winter rains to Punjab, Haryana, UP, J&K
    → Important for RABI crops (wheat, mustard, barley)!
    
  🎯 Western Disturbances → winter rain → Rabi crops (wheat)

SEASON 2: PRE-MONSOON / SUMMER (March – May)
  Temperature: Extreme heat (40-48°C in North India)
  Notable features:
  → LOO: Hot, dry, dust-laden wind over plains (causes heat stroke)
  → KAL BAISAKHI (Nor'westers): Pre-monsoon thunderstorms in Bengal, 
    Bihar, Assam (called Kalbaisakhi or "Nor'westers")
    → Bring relief from heat; can be violent
    
  🎯 PYQ: Nor'westers / Kalbaisakhi = pre-monsoon storms in Bengal/Bihar/Assam
           Associated with: Tea cultivation in Assam + Jute in Bengal

SEASON 3: MONSOON (June – September)
  The main event! 75-80% of India's annual rainfall.
  SW Monsoon arrives: Kerala ~June 1 → Bihar/UP ~June 20-25 → Delhi ~July 1
  
  ONSET ORDER (approximate):
  Kerala → Karnataka, Goa → Maharashtra → Gujarat, MP, Chhattisgarh →
  Bihar, West Bengal → UP, Rajasthan → Delhi → Punjab → J&K
  
  WITHDRAWAL (retreat) ORDER: Opposite direction
  NW India (September) → Bihar (October) → South India (November-December)
  
  🎯 PYQ: Normal onset date for Kerala = June 1 (± few days)
           Bihar receives SW monsoon: mid-to-late June

SEASON 4: POST-MONSOON / AUTUMN (October – November)
  → SW monsoon retreats
  → NE monsoon begins
  → Bay of Bengal cyclones active! (Oct-Nov = peak cyclone season)
  → Tamil Nadu coasts get NE monsoon rain
  
  🎯 PYQ: Most cyclones hit India's east coast (Andhra, Odisha, Tamil Nadu, West Bengal)
           Peak season: October-November
```

---

## 🔷 SECTION 5: Climate — Key PYQ Facts

```
RAINFALL EXTREMES:
  Highest rainfall: MAWSYNRAM (Meghalaya) — ~11,000 mm/year (world's wettest)
                    Cherrapunji (Sohra) = historically wettest (still among highest)
  Lowest rainfall:  JAISALMER (Rajasthan) — ~20-25 cm/year
  
TEMPERATURE EXTREMES:
  Hottest:   GANGANAGAR, Rajasthan (summer ~50°C recorded)
             (Phalodi, Rajasthan = recently recorded 51°C+)
  Coldest (inhabited): DRAS, Ladakh (-45°C in winter)
  
WINDS:
  LOO = Hot dry wind, North Indian plains, summer
  KALBAISAKHI / NOR'WESTERS = pre-monsoon storms, Bengal/Bihar/Assam
  WESTERN DISTURBANCES = winter rain/snow in NW India (Mediterranean origin)
  MANGO SHOWERS = pre-monsoon showers in Kerala, Karnataka (help mango ripening)
  BLOSSOM SHOWERS = coffee-growing areas of Karnataka (benefit coffee)
  CHERRY BLOSSOMS / ANDHIS = dust storms in Rajasthan summers
  
MONSOON WORD:
  "MONSOON" from Arabic "MAUSIM" = season
  
STATES WITH TROPIC OF CANCER (8 STATES):
  Gujarat → Rajasthan → MP → Chhattisgarh → Jharkhand → 
  West Bengal → Tripura → Mizoram
  
  MEMORY TRICK: "GR MC J BWTM"
  Gujarat, Rajasthan, Madhya Pradesh, Chhattisgarh, Jharkhand, 
  West Bengal, Tripura, Mizoram
  
  OR: "Geeta Roz Mandir Chali Jab Woh The Mein"
```

---

## 🔷 SECTION 6: Bihar's Climate Specifically

```
BIHAR'S CLIMATE = HUMID SUBTROPICAL MONSOON

SEASON-WISE:
  Summer (March-June):
    → Temperature: 35-42°C
    → Loo winds (hot, dry) common in April-May
    → KALBAISAKHI (Nor'westers) bring relief rains in pre-monsoon
    
  Monsoon (June-October):
    → SW Monsoon arrives: mid-to-late June
    → Most rainfall: July-August
    → Annual rainfall: 100-150 cm (North Bihar more than South)
    → North Bihar (close to Nepal, Himalayas) = higher rainfall
    → Floods common in North Bihar (Kosi, Gandak, Bagmati rivers)
    
  Autumn (October-November):
    → Retreating monsoon
    → Temperature starts dropping
    
  Winter (December-February):
    → Temperature: 5-20°C
    → Cold waves from Himalayas
    → Dense fog in December-January
    → Western Disturbances bring occasional rains (beneficial for wheat)

IMPORTANT BIHAR GEOGRAPHY POINTS:
  → North Bihar = Terai region = more rainfall, flood-prone
  → South Bihar = plateau region = less rainfall, drought-prone sometimes
  → Kosi River = "Sorrow of Bihar" (frequent floods in North Bihar)
  → Ganga divides Bihar: North Bihar + South Bihar
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Normalization, Functional Dependencies, Normal Forms, Anomalies

---

**Q1.** Normalization in DBMS is primarily done to:
(A) Increase data redundancy for faster retrieval
(B) Reduce data redundancy and prevent anomalies (insertion, update, deletion)
(C) Increase the number of tables for better security
(D) More than one of the above
(E) None of the above

---

**Q2.** Which anomaly occurs when updating data in one row leaves other rows with the old (incorrect) value?
(A) Insert Anomaly
(B) Delete Anomaly
(C) Update Anomaly
(D) More than one of the above
(E) None of the above

---

**Q3.** The functional dependency A → B means:
(A) A is always less than B
(B) Knowing the value of A uniquely determines the value of B
(C) B determines A (reverse relationship)
(D) More than one of the above
(E) None of the above

---

**Q4.** A table is in FIRST NORMAL FORM (1NF) if:
(A) It has no partial dependencies on the composite primary key
(B) All attribute values are atomic (indivisible) with no multi-valued cells or repeating groups
(C) It has no transitive dependencies
(D) More than one of the above
(E) None of the above

---

**Q5.** Which normal form specifically removes PARTIAL FUNCTIONAL DEPENDENCIES?
(A) 1NF
(B) 2NF
(C) 3NF
(D) More than one of the above
(E) None of the above

---

**Q6.** Consider a table with composite Primary Key {StdID, CourseID}. The attribute "CourseName" depends only on CourseID (not on StdID). This is a:
(A) Full functional dependency
(B) Transitive dependency
(C) Partial dependency — violates 2NF
(D) More than one of the above
(E) None of the above

---

**Q7.** Which normal form specifically removes TRANSITIVE FUNCTIONAL DEPENDENCIES?
(A) 1NF
(B) 2NF
(C) 3NF
(D) More than one of the above
(E) None of the above

---

**Q8.** A → B → C is a transitive dependency. What condition makes this a 3NF violation?
(A) When A is a primary key
(B) When B is NOT a candidate key and C depends on B (not directly on A)
(C) When C is a multivalued attribute
(D) More than one of the above
(E) None of the above

---

**Q9.** BCNF (Boyce-Codd Normal Form) is:
(A) Weaker than 3NF
(B) A stronger version of 3NF where every determinant must be a super key/candidate key
(C) Equivalent to 2NF in all cases
(D) More than one of the above
(E) None of the above

---

**Q10.** A table with a SINGLE-ATTRIBUTE primary key (not composite) is automatically in:
(A) 1NF only
(B) Both 1NF and 2NF (partial dependency impossible with single-attribute PK)
(C) 3NF always
(D) More than one of the above
(E) None of the above

---

**Q11.** Which ANOMALY prevents inserting a new course into the database when no student has enrolled yet?
(A) Update Anomaly
(B) Delete Anomaly
(C) Insert Anomaly
(D) More than one of the above
(E) None of the above

---

**Q12.** Which ANOMALY occurs when deleting a student's record causes the loss of information about a course they were the last student in?
(A) Update Anomaly
(B) Delete Anomaly
(C) Insert Anomaly
(D) More than one of the above
(E) None of the above

---

**Q13.** NORMALIZATION should always be:
(A) LOSSY — some data is sacrificed for better structure
(B) LOSSLESS — all original data can be reconstructed by joining the decomposed tables
(C) PARTIAL — only the most important tables are normalized
(D) More than one of the above
(E) None of the above

---

**Q14.** In the following FDs for table T(A, B, C, D) with PK = {A, B}:
A → C, B → D, {A,B} → D
Which dependency violates 2NF?
(A) {A,B} → D (full dependency)
(B) A → C (partial: C depends only on A, not full composite key)
(C) B → D (this is acceptable)
(D) More than one of the above
(E) None of the above

---

**Q15.** What is "DENORMALIZATION" in databases?
(A) Removing primary keys from tables to speed up queries
(B) Deliberately introducing redundancy into a normalized database to improve query performance
(C) Converting a relational database to a hierarchical database
(D) More than one of the above
(E) None of the above

---

**Q16.** Consider: StdID → DeptID, DeptID → DeptHead. Is this a transitive dependency?
(A) No — StdID determines DeptHead directly so it's fine
(B) Yes — DeptHead depends on DeptID which is a non-key attribute; StdID → DeptID → DeptHead violates 3NF
(C) No — transitive dependencies only occur with composite keys
(D) More than one of the above
(E) None of the above

---

**Q17.** The MOST COMMONLY USED normal form in real-world relational databases is:
(A) 1NF
(B) 2NF
(C) 3NF
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following is TRUE about BCNF?
(A) Every 3NF relation is automatically in BCNF
(B) Every BCNF relation is automatically in 3NF, but not vice versa
(C) BCNF is weaker than 3NF
(D) More than one of the above
(E) None of the above

---

**Q19.** A table has attributes (Employee, Dept, DeptLocation). FDs: Employee → Dept, Dept → DeptLocation. What normal form issue exists?
(A) 1NF violation — DeptLocation has multiple values
(B) 2NF violation — DeptLocation partially depends on composite key
(C) 3NF violation — Employee → Dept → DeptLocation is a transitive dependency
(D) More than one of the above
(E) None of the above

---

**Q20.** Converting from 1NF to 2NF involves:
(A) Removing multi-valued cells by creating new rows
(B) Removing transitive dependencies by splitting tables
(C) Removing partial dependencies by splitting attributes into separate tables based on their minimal determinant
(D) More than one of the above
(E) None of the above

---

**Q21.** A table T(A, B, C) has FDs: A → B, A → C, B → C. Primary key is A. Is there a 3NF violation?
(A) No — A is a primary key and determines everything; no violation
(B) Yes — B → C is a transitive dependency (A → B → C, where B is not a candidate key)
(C) Yes — A → B is a partial dependency
(D) More than one of the above
(E) None of the above

---

**Q22.** Which problem does storing "CourseName" in a STUDENT_COURSE table (with composite PK) create?
(A) Primary key violation
(B) Data redundancy — same CourseName repeated for every student in that course (leads to update anomaly)
(C) Data type mismatch
(D) More than one of the above
(E) None of the above

---

**Q23.** Normalization was proposed by:
(A) Peter Chen in 1976
(B) E.F. Codd in 1970
(C) Charles Bachman in 1969
(D) More than one of the above
(E) None of the above

---

**Q24.** A table is in 2NF. To check for 3NF, we look for:
(A) Cells containing multiple values
(B) Non-key attributes that determine other non-key attributes (transitive dependencies)
(C) Tables without a primary key
(D) More than one of the above
(E) None of the above

---

**Q25.** For BCNF, the rule is: for every functional dependency X → Y in the table:
(A) Y must be a prime attribute (part of candidate key)
(B) X must be a super key (contains a candidate key)
(C) Both X and Y must be part of the primary key
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: India's Climate Zones, Monsoon, Seasons, Factors

---

**Q26.** India's overall climate is classified as:
(A) Tropical Desert climate
(B) Tropical Monsoon climate
(C) Mediterranean climate
(D) More than one of the above
(E) None of the above

---

**Q27.** The word "Monsoon" is derived from which language?
(A) Sanskrit word "Mausa" meaning rain
(B) Arabic word "Mausim" meaning season
(C) Portuguese word "Monçao" meaning wind
(D) More than one of the above
(E) None of the above

---

**Q28.** Which coast of India receives the MAXIMUM rainfall from the SOUTHWEST MONSOON?
(A) Coromandel Coast (Tamil Nadu's eastern coast)
(B) Malabar Coast (Kerala's western coast — Western Ghats face SW monsoon)
(C) Northern coast of Odisha
(D) More than one of the above
(E) None of the above

---

**Q29.** Tamil Nadu receives most of its rainfall from:
(A) Southwest Monsoon (June-September)
(B) Northeast Monsoon (October-December)
(C) Western Disturbances
(D) More than one of the above
(E) None of the above

---

**Q30.** The HOTTEST place in India during summer is generally:
(A) Jaisalmer, Rajasthan
(B) Ganganagar / Phalodi, Rajasthan (temperatures regularly exceed 50°C)
(C) Hyderabad, Telangana
(D) More than one of the above
(E) None of the above

---

**Q31.** "Mawsynram" in Meghalaya receives exceptionally high rainfall primarily because:
(A) It is located near the sea level coastal plain
(B) The funnel-shaped terrain of Khasi Hills channels the Bay of Bengal monsoon winds, forcing them upward
(C) It is in the path of the Northeast Monsoon
(D) More than one of the above
(E) None of the above

---

**Q32.** "LOO" is a weather phenomenon associated with:
(A) Heavy rainfall during the monsoon season in coastal areas
(B) Hot, dry, dust-laden wind blowing over North Indian plains during summer
(C) Cold waves descending from the Himalayas in winter
(D) More than one of the above
(E) None of the above

---

**Q33.** "Western Disturbances" bring rainfall to which part of India during WINTER?
(A) Tamil Nadu and Kerala (southern India)
(B) Northwestern India — Punjab, Haryana, Himachal Pradesh, J&K, UP
(C) Eastern India — West Bengal and Assam
(D) More than one of the above
(E) None of the above

---

**Q34.** The Tropic of Cancer (23.5°N) passes through HOW MANY Indian states?
(A) 6 states
(B) 8 states
(C) 10 states
(D) More than one of the above
(E) None of the above

---

**Q35.** Which of the following Indian states does the Tropic of Cancer NOT pass through?
(A) Madhya Pradesh
(B) Chhattisgarh
(C) Bihar
(D) More than one of the above
(E) None of the above

---

**Q36.** "Kalbaisakhi" (Nor'westers) are associated with:
(A) Winter rains in Rajasthan and Gujarat
(B) Pre-monsoon thunderstorms in West Bengal, Bihar, and Assam (April-May)
(C) Post-monsoon cyclones on the eastern coast
(D) More than one of the above
(E) None of the above

---

**Q37.** The Himalayan mountain range influences India's climate by:
(A) Acting as a barrier to cold Central Asian winds in winter, protecting North India
(B) Trapping monsoon clouds, causing heavy rainfall on the southern slopes
(C) Both A and B are correct
(D) More than one of the above
(E) None of the above

---

**Q38.** The climate of Bihar is best described as:
(A) Tropical Rainforest
(B) Arid Desert
(C) Humid Subtropical Monsoon (hot summers, monsoon rain, cool winters)
(D) More than one of the above
(E) None of the above

---

**Q39.** The DRIEST place in India (lowest annual rainfall) is:
(A) Bikaner, Rajasthan
(B) Jaisalmer, Rajasthan
(C) Leh, Ladakh
(D) More than one of the above
(E) None of the above

---

**Q40.** The retreat of the Southwest Monsoon from India begins from which direction?
(A) From the eastern coast first (Bengal)
(B) From the northwestern part first (Rajasthan, Punjab) in September, moving southeast
(C) From the southern tip (Kerala) first
(D) More than one of the above
(E) None of the above

---

**Q41.** "MANGO SHOWERS" are pre-monsoon showers that help mango ripening. They occur mainly in:
(A) Punjab and Haryana
(B) Kerala and Karnataka (southwestern coastal states)
(C) Bihar and UP
(D) More than one of the above
(E) None of the above

---

**Q42.** Bay of Bengal cyclones are most frequent during which season?
(A) June-July (peak monsoon)
(B) October-November (post-monsoon, retreating monsoon period)
(C) December-January (winter)
(D) More than one of the above
(E) None of the above

---

**Q43.** The factor primarily responsible for the RAIN SHADOW area on the Deccan Plateau (less rain compared to Western Ghats) is:
(A) Distance from the Bay of Bengal
(B) Western Ghats blocking the Arabian Sea branch of the SW Monsoon
(C) Very high altitude of the Deccan Plateau
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following statements about India's climate is INCORRECT?
(A) Tamil Nadu receives most of its rainfall from the Northeast Monsoon
(B) Mawsynram in Meghalaya is one of the world's wettest places
(C) The LOO wind brings cooling relief during the Indian summer
(D) More than one of the above
(E) None of the above

---

**Q45.** North Bihar (like Muzaffarpur, Darbhanga) gets more rainfall than South Bihar because:
(A) North Bihar is near the Bay of Bengal, getting direct sea winds
(B) North Bihar is closer to the Himalayas and Nepal hills, which receive and direct more monsoon rainfall; rivers like Kosi also bring moisture
(C) North Bihar has more forests which attract rainfall
(D) More than one of the above
(E) None of the above

---

**Q46.** "DRAS" in Ladakh is famous for being:
(A) The highest battlefield in the world
(B) One of the coldest inhabited places in India (temperatures below -40°C in winter)
(C) The wettest place in Ladakh
(D) More than one of the above
(E) None of the above

---

**Q47.** The SOUTHWEST MONSOON arrives on the Kerala coast approximately on:
(A) March 1
(B) June 1 (approximately, with normal variations of ± a week)
(C) July 15
(D) More than one of the above
(E) None of the above

---

**Q48.** "Blossom Showers" are associated with which agricultural product?
(A) Rice cultivation in Bihar
(B) Coffee plantations in Karnataka (these showers help coffee flowering)
(C) Wheat cultivation in Punjab
(D) More than one of the above
(E) None of the above

---

**Q49.** The Thar Desert in India is classified as a:
(A) Cold desert (like Ladakh)
(B) Hot desert — world's 7th largest hot desert; also most densely populated desert
(C) Coastal desert (due to proximity to Arabian Sea)
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following statements about Indian climate:
I.   Western Disturbances originate from the Mediterranean region and bring winter rain to NW India.
II.  The Southwest Monsoon is responsible for about 75-80% of India's annual rainfall.
III. Kalbaisakhi / Nor'westers occur in Tamil Nadu and Kerala during June-July.
IV.  The retreating northeast monsoon brings rain to Tamil Nadu coast.

Which statements are CORRECT?
(A) Only I and II
(B) Only I, II, and IV
(C) Only II, III, and IV
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
| 1 | (B) | Normalization = reduce redundancy + prevent insertion/update/delete anomalies |
| 2 | (C) | Update Anomaly = updating one copy leaves others stale/inconsistent |
| 3 | (B) | A → B: knowing A uniquely determines B |
| 4 | (B) | 1NF = atomic values + no repeating groups |
| 5 | (B) | 2NF removes PARTIAL dependencies (from composite key) |
| 6 | (C) | CourseName depends only on CourseID (part of composite key) = partial dependency |
| 7 | (C) | 3NF removes TRANSITIVE dependencies |
| 8 | (B) | Transitive violation = B is NOT a candidate key and C depends on B not directly on A |
| 9 | (B) | BCNF = stronger 3NF; every determinant must be a super key |
| 10 | (B) | Single-attribute PK = automatically 2NF (no partial dependency possible) |
| 11 | (C) | Insert Anomaly = can't add course without student (PK can't be NULL) |
| 12 | (B) | Delete Anomaly = deleting a row loses unrelated info (course details) |
| 13 | (B) | Normalization must be LOSSLESS — data preserved, just better organised |
| 14 | (D) | Both A → C (partial: C needs only A) AND B → D (partial: D needs only B) violate 2NF |
| 15 | (B) | Denormalization = deliberate redundancy for query performance |
| 16 | (B) | StdID → DeptID → DeptHead = transitive dependency; DeptID is non-key → 3NF violation |
| 17 | (C) | 3NF is the most practical and most commonly targeted normal form |
| 18 | (B) | Every BCNF is in 3NF; NOT every 3NF is in BCNF (BCNF is stricter) |
| 19 | (C) | Employee → Dept → DeptLocation = transitive dependency = 3NF violation |
| 20 | (C) | 1NF→2NF = removing partial dependencies by splitting into separate tables |
| 21 | (B) | B → C: B is not a candidate key; A → B → C = transitive = 3NF violation |
| 22 | (B) | CourseName repeats for every student in that course = redundancy = update anomaly risk |
| 23 | (B) | Normalization proposed by E.F. Codd, 1970 (with Relational Model) |
| 24 | (B) | 3NF check = look for non-key → non-key dependencies (transitive) |
| 25 | (B) | BCNF rule: X → Y requires X to be a super key (no exceptions) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | India = Tropical Monsoon climate (dominant classification) |
| 27 | (B) | Monsoon = from Arabic "Mausim" = season |
| 28 | (B) | Malabar Coast (Kerala) gets maximum SW monsoon rain (Western Ghats block/receive it) |
| 29 | (B) | Tamil Nadu = Northeast Monsoon (rest of India mainly SW) |
| 30 | (B) | Ganganagar/Phalodi = regularly highest temperatures in India |
| 31 | (B) | Khasi Hills funnel shape + Bay of Bengal branch = extreme orographic rainfall |
| 32 | (B) | LOO = hot dry wind over North Indian plains in summer |
| 33 | (B) | Western Disturbances → winter rain in NW India (Punjab, HP, J&K, UP) |
| 34 | (B) | 8 states: Gujarat, Rajasthan, MP, Chhattisgarh, Jharkhand, WB, Tripura, Mizoram |
| 35 | (C) | Bihar does NOT lie on the Tropic of Cancer |
| 36 | (B) | Kalbaisakhi = pre-monsoon thunderstorms in Bengal/Bihar/Assam (April-May) |
| 37 | (C) | Himalayas do BOTH: block cold winds AND trap monsoon clouds |
| 38 | (C) | Bihar = Humid Subtropical Monsoon climate |
| 39 | (B) | Jaisalmer = driest city (~20-25 cm/year) |
| 40 | (B) | Monsoon retreats from NW (Rajasthan/Punjab) first in September, moves SE |
| 41 | (B) | Mango Showers = pre-monsoon in Kerala and Karnataka |
| 42 | (B) | Bay of Bengal cyclones peak in October-November (post-monsoon) |
| 43 | (B) | Western Ghats block Arabian Sea branch → rain shadow on Deccan/leeward side |
| 44 | (C) | Statement C is INCORRECT: LOO is HOT, causes heat exhaustion (not cooling!) |
| 45 | (B) | North Bihar closer to Nepal hills = more orographic rainfall; rivers from Nepal |
| 46 | (B) | Dras = one of coldest inhabited places in India (below -40°C in winter) |
| 47 | (B) | SW Monsoon arrives Kerala ~June 1 (normal onset date) |
| 48 | (B) | Blossom Showers = benefit coffee in Karnataka |
| 49 | (B) | Thar = hot desert; world's 7th largest + most densely populated desert |
| 50 | (B) | I ✓ (Western Disturbances = Mediterranean, NW India winter rain) II ✓ (75-80% rain) III ✗ (Kalbaisakhi is Bengal/Bihar, not Tamil Nadu; and April-May not June-July) IV ✓ (NE monsoon rain to Tamil Nadu) → Only I, II, IV correct |

---
---

# 🔁 DAY 39 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Normalization

### Normal Forms — One Line Each:
```
UNF  → Raw messy data (no rules)
1NF  → Make ALL cells ATOMIC (no lists, no repeating columns)
2NF  → Remove PARTIAL dependencies (composite key issue: non-key depends on PART of PK)
3NF  → Remove TRANSITIVE dependencies (A → B → C where B is non-key)
BCNF → Every DETERMINANT must be a SUPER KEY (stricter than 3NF)
```

### Dependency Types in 5 Seconds:
```
FULL:        B depends on ENTIRE composite key → GOOD (keeps in 2NF)
PARTIAL:     B depends on only PART of composite key → 2NF VIOLATION
TRANSITIVE:  A → B → C where B is NOT a candidate key → 3NF VIOLATION
```

### Three Anomalies:
```
INSERT  = Can't add data without unrelated data (e.g., can't add course without student)
UPDATE  = Change in one place must be made in all places → miss one = inconsistency
DELETE  = Deleting one row unintentionally deletes other info (last student in course)
```

### PYQ Trap Summary:
```
✅ 2NF removes PARTIAL (not transitive)
✅ 3NF removes TRANSITIVE (not partial)
✅ Single-attribute PK → automatically 2NF
✅ BCNF ⊂ 3NF (all BCNF is 3NF; not all 3NF is BCNF)
✅ 3NF = most commonly used in real RDBMS
✅ Normalization = LOSSLESS (data always recoverable)
✅ Denormalization = deliberate redundancy for performance
✅ Proposed by E.F. Codd (1970)
```

### Quick Flowchart:
```
1NF: Atomic? → 2NF: Full FD? → 3NF: No transitive? → BCNF: All determinants super keys?
```

---

## ⚡ RAPID FIRE — India's Climate

### Climate Type + Factor Flash:
```
India = TROPICAL MONSOON climate
"Monsoon" = Arabic "MAUSIM" = season
75-80% of India's rain = from SOUTHWEST MONSOON (June-September)
Tamil Nadu exception = gets most rain from NORTHEAST MONSOON

FACTORS: Latitude + Altitude + Distance from Sea + Monsoon + Relief + Ocean Currents
```

### Key Winds:
```
LOO = Hot dry wind, North India plains, summer (kills people — heat stroke!)
KALBAISAKHI / NOR'WESTERS = pre-monsoon storms, Bengal/Bihar/Assam (April-May)
WESTERN DISTURBANCES = Mediterranean origin, winter rain in NW India (rabi crops!)
MANGO SHOWERS = pre-monsoon, Kerala + Karnataka (mango ripening)
BLOSSOM SHOWERS = Karnataka (coffee flowering)
```

### Extremes:
```
Wettest: MAWSYNRAM, Meghalaya (~11,000 mm/year)
Driest:  JAISALMER, Rajasthan (~20-25 cm/year)
Hottest: GANGANAGAR/PHALODI, Rajasthan (50°C+)
Coldest (inhabited): DRAS, Ladakh (-45°C)
```

### Tropic of Cancer — 8 States:
```
Gujarat → Rajasthan → MP → Chhattisgarh → Jharkhand → WB → Tripura → Mizoram

TRICK: "Geeta Roz Mandir Chali Jab Woh The Mein"
Bihar is NOT on Tropic of Cancer (common trap!)
```

### Bihar Climate Quick Facts:
```
Bihar = Humid Subtropical Monsoon
Summer = HOT (35-42°C) + LOO winds + Kalbaisakhi
Monsoon = arrives mid-June, peaks July-August, ~100-150 cm rain
North Bihar = more rain + floods (Kosi = "Sorrow of Bihar")
Winter = cold (5-20°C) + fog + Western Disturbance rains (wheat crop)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Normalization flow**: 1NF (atomic) → 2NF (no partial FD on composite key) → 3NF (no transitive FD: A→B→C where B is non-key) → BCNF (all determinants are super keys); Proposed by E.F. Codd (1970).
2. **Anomalies**: INSERT (can't add without unrelated data), UPDATE (must change all copies), DELETE (lose unrelated data); Normalization eliminates all three.
3. **Key trap**: 2NF = removes PARTIAL; 3NF = removes TRANSITIVE; BCNF is STRICTER than 3NF; not all 3NF is BCNF; single-attribute PK → auto 2NF.
4. **India's climate**: Tropical Monsoon; "Monsoon" from Arabic Mausim; SW monsoon = 75-80% of rain (June-Sep); Tamil Nadu = NE monsoon exception; LOO = hot dry summer wind; Kalbaisakhi = pre-monsoon storms in Bengal/Bihar.
5. **Climate extremes + Bihar**: Mawsynram = wettest; Jaisalmer = driest; Dras = coldest; Phalodi = hottest; Bihar = Humid Subtropical; Tropic of Cancer passes 8 states (NOT Bihar — common trap!).

---

## 📅 DAY 40 PREVIEW — What's Coming Next:
**CS**: SQL Basics — DDL (CREATE, ALTER, DROP), DML (SELECT, INSERT, UPDATE, DELETE), DCL (GRANT, REVOKE), TCL (COMMIT, ROLLBACK), WHERE clause, ORDER BY, GROUP BY, HAVING
**GS**: Indian Polity — Fundamental Rights (Articles 12-35): Right to Equality (14-18), Right to Freedom (19-22), Right Against Exploitation (23-24), Right to Freedom of Religion (25-28), Cultural & Educational Rights (29-30), Right to Constitutional Remedies (Article 32)

---

*🚀 Day 39 of 170 — You're 23% through! Normalization is a high-yield DBMS topic — PYQs consistently ask about 2NF vs 3NF and anomaly types. Nail it now, score big in the exam!*
