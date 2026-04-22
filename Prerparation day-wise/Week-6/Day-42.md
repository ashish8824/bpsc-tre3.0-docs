# 📅 BPSC TRE 4.0 — DBMS + SQL COMPLETE REVISION MODULE
### Full DBMS & SQL Revision + Modern Indian History (Bihar Focus)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Revision Session Plan**
> - Phase 1 (2 hrs): DBMS + SQL Full Revision — concept sweep + all PYQ traps
> - Phase 2 (45 min): Modern Indian History + Bihar Focus revision
> - Phase 3 (1 hr): Solve all 50 MCQs under timed conditions
> - Phase 4 (30 min): Mark weak areas, note them for tomorrow

---

# PART 1: DBMS + SQL — COMPLETE REVISION

---

## 🔷 MODULE 1: DBMS CORE CONCEPTS

### What is DBMS?

```
DBMS = Database Management System
     = Software that creates, manages, and controls access to a database

THREE-LINE DEFINITION:
  DATABASE = Structured, organised collection of RELATED data
  DBMS     = Software that manages the database
  DBMS acts as INTERFACE between user/application and the database

USER / APPLICATION
       ↕
     DBMS  ← This is what you interact with (MySQL, Oracle, etc.)
       ↕
   DATABASE ← Actual stored data on disk

EXAMPLES: MySQL, Oracle, PostgreSQL, Microsoft SQL Server, SQLite, MongoDB
NOT DBMS: Google (search engine), Notepad, Excel standalone
```

### Key Features of DBMS:

```
┌─────────────────────────────┬──────────────────────────────────────────────┐
│          FEATURE            │                MEANING                        │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Reduced Redundancy          │ Data stored ONCE; no multiple copies          │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Data Consistency            │ Change once → reflects everywhere             │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Data Security               │ Role-based access; authentication             │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Multi-user Access           │ Concurrent users WITHOUT conflict             │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Data Integrity              │ Constraints ensure valid, accurate data       │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Data Independence           │ Storage changes don't break applications      │
├─────────────────────────────┼──────────────────────────────────────────────┤
│ Backup & Recovery           │ ACID transactions; crash recovery             │
└─────────────────────────────┴──────────────────────────────────────────────┘
```

### DBMS vs File System:

```
┌──────────────────────┬──────────────────────────────┬──────────────────────────────┐
│       FEATURE        │       FILE SYSTEM             │           DBMS               │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Redundancy           │ HIGH (same data in many files)│ LOW (central storage)        │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Inconsistency        │ HIGH (update one, miss others)│ LOW (update once = done)     │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Security             │ POOR (file-level only)        │ STRONG (user roles)          │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Concurrent Access    │ POOR/NONE                     │ MULTI-USER supported         │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Data Integrity       │ No constraints                │ Constraints enforced         │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Query Processing     │ Manual programming needed     │ SQL — simple, powerful       │
└──────────────────────┴──────────────────────────────┴──────────────────────────────┘
```

### 🚨 PYQ TRAPS — DBMS Basics:
```
TRAP 1: "DBMS supports single-user access only" → FALSE!
        DBMS supports MULTI-USER concurrent access. Single-user = limitation of FILE SYSTEM.

TRAP 2: "Google is a DBMS" → FALSE!
        Google is a SEARCH ENGINE. DBMS = software managing structured, controlled database.

TRAP 3: "Database and DBMS are the same thing" → FALSE!
        Database = collection of data; DBMS = software managing it.

TRAP 4: "Decentralized Database" is a standard type → FALSE!
        Correct term = DISTRIBUTED database. "Decentralized" is NOT standard.
```

---

## 🔷 MODULE 2: KEYS IN DBMS

### Key Hierarchy — One Paragraph Mastery:
```
All attribute sets that UNIQUELY IDENTIFY rows = SUPER KEYS (broadest category)
Remove redundant attributes → CANDIDATE KEYS (minimal super keys)
Choose ONE from candidates → PRIMARY KEY (the official identifier)
Remaining candidates → ALTERNATE KEYS
Key that references another table's PK → FOREIGN KEY
Key made of multiple attributes → COMPOSITE KEY
Unique but allows NULL → UNIQUE KEY
```

### All Keys — Master Reference:

```
┌──────────────────┬──────────────────────────────────────────┬──────────────┬──────────────┐
│    KEY TYPE      │            DEFINITION                    │  NULL?       │  COUNT       │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ Super Key        │ Any set that uniquely identifies rows     │ N/A          │ Many         │
│                  │ (may have extra attributes)               │              │              │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ Candidate Key    │ MINIMAL super key (nothing removable)    │ No           │ Multiple     │
│                  │ → each uniquely identifies rows           │              │ possible     │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ PRIMARY KEY      │ ONE chosen candidate key                 │ NO — never!  │ ONLY 1       │
│                  │ Main identifier of rows                   │              │ per table    │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ Foreign Key      │ References PK of another table           │ YES          │ Multiple     │
│                  │ Enforces referential integrity            │ (allowed)    │ possible     │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ Composite Key    │ Key made of 2+ attributes combined       │ Depends      │ One per need │
│                  │ (needed when no single attr is unique)    │              │              │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ Unique Key       │ Ensures uniqueness; like PK              │ YES          │ Multiple     │
│                  │ but NOT the primary identifier            │ (allowed)    │ per table    │
├──────────────────┼──────────────────────────────────────────┼──────────────┼──────────────┤
│ Alternate Key    │ Candidate keys NOT chosen as PK          │ No           │ Multiple     │
└──────────────────┴──────────────────────────────────────────┴──────────────┴──────────────┘
```

### Visual: Primary Key → Foreign Key Relationship:
```
DEPARTMENTS                          STUDENTS
┌────────────────────────┐           ┌─────────────────────────────────┐
│ DeptID [PK 🔑]│DeptName│           │ RollNo [PK 🔑]│Name  │DeptID[FK]│
├────────┼───────────────┤           ├────────────────┼──────┼─────────┤
│  CS    │ Computer Sci  │◄──────────│  101           │ Ravi │   CS    │
│  Math  │ Mathematics   │◄──────────│  102           │Priya │  Math   │
└────────┴───────────────┘           └────────────────┴──────┴─────────┘

STUDENTS.DeptID (FK) → DEPARTMENTS.DeptID (PK)
FK can be NULL (student not yet assigned to dept)
PK cannot be NULL (every dept must have an ID)
```

### 🚨 PYQ TRAPS — Keys:
```
TRAP 1: "A table can have multiple Primary Keys" → FALSE! Only ONE PK per table.
TRAP 2: "Primary Key can be NULL" → FALSE! PK cannot EVER be NULL.
TRAP 3: "Foreign Key references the FK of another table" → FALSE! FK references PK.
TRAP 4: "Unique Key cannot be NULL" → FALSE! Unique Key CAN be NULL (PK cannot).
TRAP 5: "{RollNo, Name} is a Candidate Key when RollNo alone uniquely identifies" → FALSE!
        Must be MINIMAL — {RollNo, Name} is a Super Key, NOT Candidate Key.
TRAP 6: "Full mesh connections = n" → FALSE! Full mesh = n(n-1)/2 connections.
```

---

## 🔷 MODULE 3: ER MODEL & RELATIONAL MODEL

### ER Model Quick Summary:

```
PROPOSED BY: Peter Chen (1976)
PURPOSE:     Conceptual design tool — blueprint BEFORE building the database

THREE COMPONENTS:
  ENTITY      = Real-world object (STUDENT, EMPLOYEE, COURSE)
                Symbol: Rectangle □
  ATTRIBUTE   = Property of entity (Name, Age, Email)
                Symbol: Oval ○
  RELATIONSHIP = Association between entities (ENROLLED IN, WORKS FOR)
                Symbol: Diamond ◇

ENTITY TYPES:
  STRONG = Has own PK; exists independently → Single rectangle
  WEAK   = No own PK; depends on strong entity → Double rectangle ╔╗
           Has PARTIAL KEY; Full ID = Owner PK + Partial Key
```

### Attribute Types Quick Reference:
```
SIMPLE:      Indivisible atomic value → Single oval (RollNo, Age)
COMPOSITE:   Can be divided into parts → Oval with sub-ovals (Name→First/Last)
DERIVED:     Calculated from another → DASHED oval (Age from DateOfBirth)
MULTIVALUED: Multiple values per entity → DOUBLE oval (Phone numbers)
             → Stored in SEPARATE TABLE in Relational Model
```

### Cardinality Types:
```
1:1  → One-to-one   → Person ↔ Passport
1:N  → One-to-many  → Dept → Employees (FK on MANY side!)
M:N  → Many-to-many → Students ↔ Courses (needs JUNCTION TABLE!)
```

### Relational Model Terminology:
```
ER MODEL TERM → RELATIONAL MODEL TERM
Entity       → Table (RELATION)
Row          → TUPLE
Column       → ATTRIBUTE
Valid values → DOMAIN
# of Columns → DEGREE
# of Rows    → CARDINALITY
Fixed structure → SCHEMA (permanent)
Current data    → INSTANCE (changes)
Data about data → METADATA (column names, types, constraints = metadata)
```

### 🚨 PYQ TRAPS — ER & Relational Model:
```
TRAP 1: "Metadata is the actual data stored in tables" → FALSE!
        Metadata = data ABOUT data (schema, column names, constraints).
TRAP 2: "Tuple means column" → FALSE! Tuple = ROW. Attribute = COLUMN.
TRAP 3: "Weak entity has its own Primary Key" → FALSE! Has only PARTIAL KEY.
TRAP 4: "Derived attribute is stored in database" → FALSE! CALCULATED, not stored.
TRAP 5: "Degree of relation = number of rows" → FALSE! Degree = COLUMNS. Cardinality = ROWS.
TRAP 6: "ER Model proposed by E.F. Codd" → FALSE! ER = Peter Chen (1976). 
        Relational Model = E.F. Codd (1970).
```

---

## 🔷 MODULE 4: NORMALIZATION

### Why Normalization?
```
Three anomalies normalization ELIMINATES:
  INSERT ANOMALY  = Can't insert data without unrelated data
  UPDATE ANOMALY  = Updating one place leaves others inconsistent
  DELETE ANOMALY  = Deleting one thing accidentally deletes another

PROPOSED BY: E.F. Codd (1970)
```

### Functional Dependency Types:
```
FULL DEPENDENCY:    B depends on ENTIRE composite key → GOOD (2NF compliant)
PARTIAL DEPENDENCY: B depends on PART of composite key → 2NF VIOLATION
TRANSITIVE DEPENDENCY: A → B → C where B is NOT a candidate key → 3NF VIOLATION
```

### Normal Forms — Master Table:

```
┌──────┬──────────────────────────────────────────┬────────────────────────────────┐
│  NF  │                  RULE                    │         WHAT IT REMOVES        │
├──────┼──────────────────────────────────────────┼────────────────────────────────┤
│ 1NF  │ ALL values are ATOMIC                    │ Multi-valued cells,            │
│      │ No repeating groups                      │ repeating column groups        │
├──────┼──────────────────────────────────────────┼────────────────────────────────┤
│ 2NF  │ In 1NF + No PARTIAL DEPENDENCY           │ Partial FD from non-key attr  │
│      │ (every non-key attr depends on FULL PK)  │ on only PART of composite PK  │
│      │ Only relevant with COMPOSITE PK!          │                               │
├──────┼──────────────────────────────────────────┼────────────────────────────────┤
│ 3NF  │ In 2NF + No TRANSITIVE DEPENDENCY        │ A → B → C where B is non-key  │
│      │ No non-key attr determines another        │ → move B+C to separate table  │
│      │ non-key attr                              │ ← MOST USED in practice!      │
├──────┼──────────────────────────────────────────┼────────────────────────────────┤
│ BCNF │ In 3NF + For every A → B,                │ BCNF violations in 3NF tables │
│      │ A must be a SUPER KEY                    │ (stricter than 3NF)            │
└──────┴──────────────────────────────────────────┴────────────────────────────────┘
```

### Step-by-Step Normalization Quick Example:
```
UNNORMALIZED (UNF):
STUDENT(RollNo, Name, Courses[CS101,Math101], Marks[85,90])
↓
1NF (make atomic):
ENROLLMENT(RollNo, Name, CourseID, Marks)
PK = {RollNo, CourseID}
↓
2NF (remove partial deps):
  Name depends only on RollNo (PARTIAL on composite PK!)
  → STUDENT(RollNo, Name)  + COURSE(CourseID, CourseName) + ENROLLMENT(RollNo, CourseID, Marks)
↓
3NF (remove transitive deps):
  If STUDENT has DeptID → DeptName (transitive: RollNo → DeptID → DeptName)
  → STUDENT(RollNo, Name, DeptID[FK])  +  DEPARTMENT(DeptID, DeptName)
↓
BCNF: check all determinants are super keys → usually 3NF is sufficient!
```

### Normalization Flowchart:
```
Start
  │
  ▼
1NF: All values atomic? → NO → Make each cell have ONE value (split rows)
  │
  ▼  YES
2NF: Composite PK present AND partial FD found? → YES → Move partial deps to own table
  │
  ▼  NO partial deps
3NF: Any A → B → C where B is non-key? → YES → Move B and its deps to separate table
  │
  ▼  NO transitive deps  
BCNF: Any determinant that's not a super key? → YES → Decompose further
  │
  ▼  NO
✅ FULLY NORMALIZED
```

### 🚨 PYQ TRAPS — Normalization:
```
TRAP 1: "2NF removes transitive dependencies" → FALSE! 2NF removes PARTIAL deps.
TRAP 2: "3NF removes partial dependencies" → FALSE! 3NF removes TRANSITIVE deps.
TRAP 3: "BCNF and 3NF are always equivalent" → FALSE! BCNF is STRICTER.
TRAP 4: "Normalization increases data redundancy" → FALSE! DECREASES redundancy.
TRAP 5: "Single-attribute PK needs to check for 2NF" → FALSE! 
        Single-attribute PK → automatically 2NF (no partial dep possible).
TRAP 6: "Normalization causes data loss" → FALSE! Should always be LOSSLESS.
TRAP 7: "Denormalization = making database worse" → FALSE! 
        Denormalization = deliberate redundancy for performance (analytics/DW).
```

---

## 🔷 MODULE 5: SQL COMMANDS — COMPLETE REVISION

### SQL Command Categories:
```
                         SQL COMMANDS
                              │
        ┌─────────────────────┼─────────────────────┐
        │              │              │              │
       DDL            DML            DCL            TCL
  (Definition)    (Manipulation)  (Control)   (Transaction)
  CREATE          SELECT          GRANT          COMMIT
  ALTER           INSERT          REVOKE         ROLLBACK
  DROP            UPDATE                         SAVEPOINT
  TRUNCATE        DELETE
  RENAME
```

### DDL vs DML vs DCL vs TCL Master Table:

```
┌────────────┬──────────────┬────────────────────┬─────────────┬─────────────┐
│  CATEGORY  │   COMMAND    │      PURPOSE        │AUTO-COMMIT? │ ROLLBACK?   │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ DDL        │ CREATE       │ Create structure    │    YES ✓    │     NO ✗    │
│ (Structure)│ ALTER        │ Modify structure    │    YES ✓    │     NO ✗    │
│            │ DROP         │ Delete object       │    YES ✓    │     NO ✗    │
│            │ TRUNCATE     │ Empty table fast    │    YES ✓    │     NO ✗    │
│            │ RENAME       │ Rename object       │    YES ✓    │     NO ✗    │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ DML        │ SELECT       │ Read/query data     │    NO ✗     │    YES ✓    │
│ (Data)     │ INSERT       │ Add rows            │    NO ✗     │    YES ✓    │
│            │ UPDATE       │ Modify rows         │    NO ✗     │    YES ✓    │
│            │ DELETE       │ Remove rows         │    NO ✗     │    YES ✓    │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ DCL        │ GRANT        │ Give permissions    │    YES ✓    │     NO ✗    │
│ (Control)  │ REVOKE       │ Remove permissions  │    YES ✓    │     NO ✗    │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ TCL        │ COMMIT       │ Save permanently    │    N/A      │     NO ✗    │
│(Transaction│ ROLLBACK     │ Undo changes        │    N/A      │     N/A     │
│            │ SAVEPOINT    │ Create checkpoint   │    N/A      │    YES ✓    │
└────────────┴──────────────┴────────────────────┴─────────────┴─────────────┘
```

### DELETE vs TRUNCATE — Most Tested Comparison:

```
┌──────────────────────┬──────────────────────────┬──────────────────────────┐
│       FEATURE        │          DELETE           │         TRUNCATE         │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Category             │ DML                       │ DDL                      │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Can ROLLBACK?        │ YES ✓                     │ NO ✗ (auto-committed!)   │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ WHERE clause?        │ YES ✓ (selective delete)  │ NO ✗ (all rows always)   │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Speed                │ SLOWER (logs each row)    │ FASTER (bulk operation)  │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Table structure?     │ Keeps structure           │ Keeps structure          │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Auto-increment reset │ NO                        │ YES                      │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Triggers?            │ YES — triggers fire       │ NO — triggers don't fire │
└──────────────────────┴──────────────────────────┴──────────────────────────┘

VS DROP:
  DELETE = Remove rows; KEEP structure
  TRUNCATE = Remove all rows; KEEP structure (faster, can't rollback)
  DROP = Remove rows AND structure (both gone forever)
```

### COMMIT vs ROLLBACK:
```
COMMIT:   Permanently SAVES all DML changes. CANNOT be undone by ROLLBACK.
          Analogy: Ctrl+S (saving a document)
          
ROLLBACK: UNDOES all DML changes since last COMMIT (or SAVEPOINT).
          Cannot undo DDL (CREATE, DROP, TRUNCATE — they're auto-committed!)
          Analogy: Ctrl+Z (undo)
          
SAVEPOINT sp1:     Create a named checkpoint.
ROLLBACK TO sp1:   Undo only changes AFTER sp1 was set.
                   Analogy: Save slot in a video game.
```

---

## 🔷 MODULE 6: SQL SELECT — COMPLETE REVISION

### Full SELECT Syntax + Execution Order:
```
WRITE ORDER:                    EXECUTION ORDER:
SELECT ...                  1.  FROM    — identify source table
FROM ...                    2.  WHERE   — filter individual rows  
WHERE ...                   3.  GROUP BY — group filtered rows
GROUP BY ...                4.  HAVING  — filter groups
HAVING ...                  5.  SELECT  — build output columns
ORDER BY ...                6.  DISTINCT — remove duplicate rows
LIMIT ...                   7.  ORDER BY — sort result
                            8.  LIMIT   — cut to N rows

MEMORY: "From Where Groups Have Select Order Limited"
```

### WHERE vs HAVING — Critical Comparison:
```
┌──────────────────────┬──────────────────────────────┬──────────────────────────────┐
│       FEATURE        │            WHERE             │           HAVING             │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ When it runs         │ BEFORE GROUP BY              │ AFTER GROUP BY               │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Works on             │ Individual ROWS              │ GROUPS                       │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Aggregate functions  │ CANNOT use (COUNT, AVG, etc.)│ CAN use aggregates           │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Used with GROUP BY?  │ Not required (independent)   │ Usually WITH GROUP BY        │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Correct use          │ WHERE Marks > 80             │ HAVING COUNT(*) > 2          │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ WRONG use            │ WHERE COUNT(*) > 2 ← ERROR!  │ HAVING RollNo > 100 ← bad    │
└──────────────────────┴──────────────────────────────┴──────────────────────────────┘
```

### SQL Example — All Clauses Together:
```sql
-- Find departments (not Admin) with avg marks > 75,
-- show top 2 by highest avg:

SELECT DeptID, COUNT(*) AS Students, AVG(Marks) AS Avg
FROM STUDENTS
WHERE DeptID != 'Admin'      -- filter rows first
GROUP BY DeptID              -- group remaining rows
HAVING AVG(Marks) > 75       -- filter groups
ORDER BY Avg DESC            -- sort by avg descending
LIMIT 2;                     -- show only top 2
```

---

## 🔷 MODULE 7: AGGREGATE FUNCTIONS

### The 5 Valid Aggregate Functions:
```
┌──────────────┬───────────────────────────────────────┬──────────────────────┐
│   FUNCTION   │               PURPOSE                 │        EXAMPLE        │
├──────────────┼───────────────────────────────────────┼──────────────────────┤
│ COUNT(*)     │ Count ALL rows (includes NULLs)        │ COUNT(*) = 8         │
│ COUNT(col)   │ Count non-NULL values in column        │ COUNT(Email) = 7     │
├──────────────┼───────────────────────────────────────┼──────────────────────┤
│ SUM(col)     │ Total of all values (ignores NULLs)   │ SUM(Marks) = 666     │
├──────────────┼───────────────────────────────────────┼──────────────────────┤
│ AVG(col)     │ Average = SUM/COUNT of non-NULLs      │ AVG(Marks) = 83.25   │
├──────────────┼───────────────────────────────────────┼──────────────────────┤
│ MAX(col)     │ Highest value in column               │ MAX(Marks) = 95      │
├──────────────┼───────────────────────────────────────┼──────────────────────┤
│ MIN(col)     │ Lowest value in column                │ MIN(Marks) = 65      │
└──────────────┴───────────────────────────────────────┴──────────────────────┘

NOT aggregate: COMPUTE (deprecated Sybase extension — NOT standard SQL!)
```

---

## 🔷 MODULE 8: SQL CONSTRAINTS

### All SQL Constraints:
```
┌──────────────────┬──────────────────────────────────────────────────────┐
│   CONSTRAINT     │                    PURPOSE                           │
├──────────────────┼──────────────────────────────────────────────────────┤
│ PRIMARY KEY      │ Unique + NOT NULL; only ONE per table                │
├──────────────────┼──────────────────────────────────────────────────────┤
│ FOREIGN KEY      │ References PK of another table; CAN be NULL         │
├──────────────────┼──────────────────────────────────────────────────────┤
│ UNIQUE           │ All values distinct; NULLs allowed                   │
├──────────────────┼──────────────────────────────────────────────────────┤
│ NOT NULL         │ Column must always have a value                      │
├──────────────────┼──────────────────────────────────────────────────────┤
│ DEFAULT          │ Uses default value if none specified                 │
├──────────────────┼──────────────────────────────────────────────────────┤
│ CHECK            │ Value must satisfy a condition: CHECK(Age >= 18)     │
└──────────────────┴──────────────────────────────────────────────────────┘
```

### 🚨 CRITICAL PYQ TRAPS — SQL (Complete List):

```
COMMAND CATEGORY TRAPS:
✅ TRUNCATE is DDL (NOT DML!) → CANNOT be rolled back
✅ SELECT is DML (NOT DDL!)
✅ GRANT and REVOKE are DCL (NOT DML!)

CLAUSE TRAPS:
✅ ORDER BY default = ASC (ascending) — NOT DESC!
✅ HAVING is used AFTER GROUP BY to filter GROUPS
✅ WHERE cannot use aggregate functions (COUNT, AVG, etc.)
✅ BETWEEN is INCLUSIVE (includes both boundary values)
✅ % = zero or more chars; _ = exactly ONE char (LIKE patterns)
✅ COUNT(*) ≠ COUNT(col): * counts NULLs; col skips NULLs

AGGREGATE TRAPS:
✅ COMPUTE is NOT a valid aggregate function!
✅ Valid aggregates: COUNT, SUM, AVG, MAX, MIN only

CONSTRAINT TRAPS:
✅ UNION is NOT a constraint! (It's a SET OPERATION)
✅ Valid constraints: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, DEFAULT, CHECK

KEY TRAPS:
✅ Only ONE Primary Key per table
✅ Primary Key CANNOT be NULL
✅ Unique Key CAN be NULL
✅ Foreign Key CAN be NULL
✅ Foreign Key references PK (not FK) of another table

TRANSACTION TRAPS:
✅ After COMMIT → ROLLBACK does nothing (changes are permanent)
✅ ROLLBACK cannot undo DDL or DCL (auto-committed)
✅ DDL = Auto-committed = Cannot rollback
✅ DML = Not auto-committed = Can rollback until COMMIT

WITH CLAUSE:
✅ WITH creates TEMPORARY relation (CTE) — not permanently stored
```

---

## 🔷 MODULE 9: DBMS STRUCTURE OVERVIEW FLOWCHART

```
COMPLETE DBMS JOURNEY:

REAL WORLD (Hospital, Bank, School)
           │
           ▼
    REQUIREMENT ANALYSIS
    "What data do we need?"
           │
           ▼
    ER DIAGRAM (Peter Chen, 1976)
    Entities + Attributes + Relationships
    Strong/Weak Entities, Cardinality (1:1, 1:N, M:N)
           │
           ▼
    RELATIONAL MODEL (E.F. Codd, 1970)
    ER → Tables, Tuples, Attributes, Domains
    Schema vs Instance, Metadata
           │
           ▼
    KEYS DEFINED
    Primary Key, Foreign Key, Unique, Composite
    Candidate Keys → choose Primary Key
           │
           ▼
    NORMALIZATION (E.F. Codd, 1970)
    1NF → 2NF → 3NF → BCNF
    Remove: multi-values → partial deps → transitive deps
           │
           ▼
    SQL IMPLEMENTATION
    DDL: CREATE tables (with constraints)
    DML: INSERT data, SELECT queries, UPDATE, DELETE
    DCL: GRANT/REVOKE permissions
    TCL: COMMIT/ROLLBACK transactions
           │
           ▼
    RUNNING DATABASE
    Multi-user access, ACID transactions, Backup & Recovery
```

---

# PART 2: MODERN INDIAN HISTORY — REVISION (Bihar Focus)

---

## 🔷 MODULE 10: CHAMPARAN SATYAGRAHA (1917) — GANDHI'S FIRST

### Background:
```
YEAR: 1917
LOCATION: Champaran district, Bihar (now divided into East + West Champaran)
ISSUE: TINKATHIA SYSTEM / INDIGO CULTIVATION

THE PROBLEM:
  → British planters (NEEL SAHIBS) forced farmers to cultivate INDIGO 
    on 3/20th of their land (Tinkathia = Tin-katha = 3/20th)
  → Farmers given no choice — coerced under contracts
  → Paid very low prices or even forced to pay rents without adequate compensation
  → When synthetic dyes made indigo less profitable, British wanted to 
    CANCEL contracts but demanded "nazrana" (compensation payments) from farmers
  → Farmers were already indebted and being exploited badly

GANDHI'S INVOLVEMENT:
  → Rajkumar Shukla (farmer leader from Champaran) came to Gandhi
  → Met Gandhi at Congress session in Lucknow (1916), convinced him to visit
  → Gandhi arrived in Champaran: APRIL 1917
  → British District Magistrate issued order to leave → Gandhi REFUSED
  → First act of civil disobedience on Indian soil!
  → Gandhi began INVESTIGATION — collected testimonies from hundreds of farmers
  → Govt appointed official commission → Gandhi included as member
```

### Key Outcomes:
```
CHAMPARAN AGRARIAN ACT (1917):
  → Abolished the TINKATHIA system
  → Gave farmers rights over their land
  → Major victory for Gandhi's non-violent movement

SIGNIFICANCE:
  → FIRST Satyagraha by Gandhi in India (he'd done it in South Africa before)
  → Established SATYAGRAHA as an effective political tool in India
  → Gave Gandhi credibility among Indian masses
  → Established strong base in BIHAR
  → Rajendra Prasad (later India's first President) got his start here
  → J.B. Kripalani also participated as Gandhi's helper
```

### Key Personalities — Champaran:
```
RAJKUMAR SHUKLA:  Farmer who brought Gandhi to Champaran
GANDHI:           Led the movement; refused to leave when ordered
RAJENDRA PRASAD:  Participated; later became First President of India
J.B. KRIPALANI:  Gandhi's helper during the investigation
BRIJ KISHORE PRASAD: Important local leader

🎯 PYQ: First Satyagraha by Gandhi in India = CHAMPARAN (1917), Bihar
         Champaran related to INDIGO (not cotton!) plantation issue
         Rajkumar Shukla = farmer who invited Gandhi to Champaran
```

---

## 🔷 MODULE 11: KHEDA SATYAGRAHA (1918)

```
YEAR: 1918
LOCATION: Kheda district, Gujarat (NOT Bihar — but important for Gandhi's timeline)
ISSUE: CROP FAILURE → peasants demanded revenue remission
       Famine conditions; crops failed but British demanded land revenue anyway

GANDHI'S ROLE:
  → Supported by Vallabhbhai Patel (who managed most of the ground work)
  → Convinced farmers to withhold land revenue payments
  → Government eventually gave in — partial concession

SIGNIFICANCE:
  → Vallabhbhai Patel emerged as a major leader (future "Sardar" and India's first Home Minister)
  → Second Satyagraha by Gandhi in India (after Champaran)

🎯 PYQ: Kheda Satyagraha (1918) = Vallabhbhai Patel's rise
```

---

## 🔷 MODULE 12: NON-COOPERATION MOVEMENT (1920-22)

```
YEAR: 1920-1922
CALLED BY: Gandhi at Nagpur Congress session, September 1920
REASONS:
  → Jallianwala Bagh Massacre (13 April 1919) — killing of 1000+ in Amritsar
  → Rowlatt Act (1919) — Black Laws (no trial, indefinite detention)
  → Khilafat issue — British dismantling Ottoman Caliphate (Muslim grievance)

PROGRAMME:
  → Return of British titles and honours
  → Boycott of British-aided schools and colleges
  → Boycott of British courts
  → Boycott of elections under the Montagu-Chelmsford reforms
  → Boycott of foreign goods (Swadeshi — burn foreign cloth!)
  → Refusal to pay taxes (in some areas)

MASS PARTICIPATION — spread across India including Bihar:
  → Students left schools; lawyers left courts
  → Bonfire of foreign clothes in town squares
  → Charkha (spinning wheel) as symbol of self-reliance
  → Khadi became patriotic symbol

WHY WITHDRAWN:
  → CHAURI CHAURA INCIDENT (4 February 1922), Gorakhpur, UP
  → A crowd of protestors attacked and set fire to a police station
  → 22 policemen were killed
  → Gandhi called off the entire movement on 12 February 1922
  → Gandhi believed violence negates the moral basis of movement

🎯 PYQ: Non-Cooperation Movement called off due to CHAURI CHAURA INCIDENT (Feb 4, 1922)
         Chauri Chaura location = Gorakhpur, UP (not Bihar!)
         Movement started = 1920; ended = 1922
```

---

## 🔷 MODULE 13: CIVIL DISOBEDIENCE MOVEMENT (1930-34)

```
KEY EVENT: DANDI MARCH / SALT MARCH (12 March - 6 April 1930)

MARCH:      Gandh marched 241 miles (388 km) from Sabarmati Ashram (Ahmedabad)
            to DANDI (coastal village in Gujarat)
DATE:       12 March 1930 → arrived Dandi 6 April 1930
PURPOSE:    Defy British SALT LAW (making salt was taxed/controlled by British)
            Making salt from seawater = first act of civil disobedience
FOLLOWERS:  Started with 78 followers; thousands joined on the way

WHY SALT?
  → Salt is used by EVERY Indian (rich, poor, high caste, low caste)
  → Salt tax affected ALL people regardless of religion, caste, class
  → Perfect symbol of British exploitation of basic necessities
  → Also: Salt represents FREEDOM — coastal people had made their own for millennia

IMPACT:
  → Mass arrests including Gandhi
  → DHARASANA SALT WORKS RAID (May 1930) — non-violent protestors beaten by police;
    Sarojini Naidu led the march after Gandhi's arrest
  → International media attention → world saw British brutality

GANDHI-IRWIN PACT (5 March 1931):
  → Lord Irwin (Viceroy) negotiated with Gandhi
  → Civil Disobedience suspended
  → Political prisoners released
  → Gandhi permitted to attend Round Table Conference in London (September 1931)

SECOND ROUND TABLE CONFERENCE (1931):
  → Gandhi attended but it was inconclusive (B.R. Ambedkar's separate electorate demand vs Gandhi)
  → Gandhi returned; movement resumed briefly

🎯 PYQ: Dandi March = 12 March 1930; 241 miles; Sabarmati to Dandi (Gujarat)
         Civil Disobedience = 1930; Gandhi-Irwin Pact = 5 March 1931
```

---

## 🔷 MODULE 14: QUIT INDIA MOVEMENT (1942)

```
YEAR: 9 August 1942
CALLED: Bombay Session of Congress; Gowalia Tank Maidan (now August Kranti Maidan)
SLOGAN: "DO OR DIE" (Karo ya Maro) — given by GANDHI
        "QUIT INDIA" — given by YUSUF MEHERALLY (Congress leader)

CONTEXT:
  → World War II ongoing; Japan advancing toward India
  → Cripps Mission (1942) failed — British offered Dominion status AFTER the war
  → Congress rejected it as insufficient
  → Gandhi demanded IMMEDIATE independence

FIRST ARRESTS: Within hours of the August 9 resolution:
  → Gandhi arrested (imprisoned at Aga Khan Palace, Pune)
  → Jawaharlal Nehru, Vallabhbhai Patel, all major leaders arrested
  → Movement became LEADERLESS immediately!

UNDERGROUND MOVEMENT:
  → Ram Manohar Lohia, Aruna Asaf Ali, Jayaprakash Narayan led underground operations
  → Parallel governments (Tamralipta Jatiya Sarkar in Bengal, Balia in UP, Satara in Maharashtra)
  → Radio Free India operated secretly (from Bombay)

SIGNIFICANCE:
  → Though suppressed in months, it sent a clear message: British must leave
  → August 9 = QUIT INDIA DAY (now observed as Kranti Diwas)

🎯 PYQ: Quit India = 1942; Slogan "Do or Die" = GANDHI
         "Quit India" slogan coined by YUSUF MEHERALLY
         Underground leaders: Aruna Asaf Ali, JP Narayan, Ram Manohar Lohia
```

---

## 🔷 MODULE 15: REVOLUTIONARY MOVEMENTS QUICK REVISION

### GHADAR PARTY:
```
FOUNDED:    1913, San Francisco, USA
PRESIDENT:  Sohan Singh Bhakna
INTELLECT:  Har Dayal (intellectual backbone; deported by USA)
NEWSPAPER:  "Ghadar" — multi-language (Punjabi, Urdu, Hindi, Gujarati, Pashto)
            First issue: 1 November 1913; tagline: "Angrezi Raj ka Dushman"
MEMBERSHIP: Primarily PUNJABI SIKH workers abroad; also Hindus and Muslims
            → NON-COMMUNAL organisation (unique feature!)

1915 GHADAR MUTINY:
  → WWI → plan to incite Indian soldiers to mutiny
  → FAILED — betrayed by informers to British intelligence
  → 42 hanged including KARTAR SINGH SARABHA (age 19)
  → Sarabha = Bhagat Singh's idol; Bhagat Singh kept his photo in his pocket!

🎯 PYQ: 1913, San Francisco | Sohan Singh Bhakna | "Ghadar" newspaper | Non-communal
```

### ANUSHILAN SAMITI:
```
FOUNDED:    1902, Calcutta (Kolkata)
FOUNDERS:   Pramathanath Mitra; Barindra Kumar Ghosh
DHAKA BRANCH: 1906, Pulin Bihari Das (most radical)
COVER:      Physical training societies (gymnasiums)

ALIPORE BOMB CASE (1908):
  → Khudiram Bose + Prafulla Chaki → Muzaffarpur bomb attack
  → Target: Magistrate Kingsford (MISSED — killed British ladies instead)
  → Prafulla Chaki: shot himself on arrest
  → Khudiram Bose: HANGED 11 August 1908, age 18 (youngest martyr!)
  → Aurobindo Ghosh: arrested, ACQUITTED; became spiritual leader

🎯 PYQ: 1902, Calcutta | Khudiram Bose (age 18) | Alipore Bomb Case 1908
```

### ABHINAV BHARAT SOCIETY:
```
FOUNDED:    1904, Nasik, Maharashtra
FOUNDER:    Vinayak Damodar Savarkar (V.D. Savarkar / "Veer Savarkar")
MEANING:    "Young India" society
INSPIRED BY: Giuseppe Mazzini's "Young Italy"

KEY CONTRIBUTION: Savarkar's book "The Indian War of Independence, 1857"
                  First to call 1857 a "WAR OF INDEPENDENCE" (not mutiny)

NASIK CONSPIRACY CASE (1909):
  → Anant Laxman Kanhere (linked to Abhinav Bharat) assassinated
    A.M.T. Jackson, District Collector of Nasik
  → Pistols traced to Savarkar

SAVARKAR'S FATE:
  → Arrested in London, escaped at Marseilles — CAUGHT!
  → Sentenced: 50 YEARS imprisonment
  → Imprisoned in CELLULAR JAIL (KALA PANI), Port Blair, Andaman

🎯 PYQ: 1904, Nasik | Savarkar | Mazzini inspiration | 50 yrs Kala Pani
```

---

## 🔷 MODULE 16: Key Dates Quick Reference

```
TIMELINE OF MAJOR EVENTS:
  1857 → First War of Independence (Sepoy Mutiny)
  1885 → Indian National Congress founded (A.O. Hume)
  1897 → Chapekar Brothers assassination (first political murder)
  1899-1900 → Birsa Munda's Ulgulan (Munda tribal revolt)
  1902 → Anushilan Samiti founded (Calcutta)
  1904 → Abhinav Bharat (Nasik, Savarkar)
  1905 → Partition of Bengal (October 16) → Swadeshi Movement
  1908 → Alipore Bomb Case (Khudiram Bose hanged age 18)
  1909 → Nasik Conspiracy Case (Abhinav Bharat)
  1911 → Partition of Bengal ANNULLED; Delhi became capital
  1913 → Ghadar Party founded (San Francisco)
  1915 → Ghadar Mutiny FAILED; 42 hanged
  1915 → Gandhi returned from South Africa
  1916 → Lucknow Pact (Congress-Muslim League)
  1917 → Champaran Satyagraha (Gandhi's FIRST in India)
  1918 → Kheda Satyagraha (Patel's rise)
  1919 → Rowlatt Act; Jallianwala Bagh Massacre (April 13)
  1920 → Non-Cooperation Movement begins
  1922 → Chauri Chaura Incident (Feb 4); NCM called off
  1929 → Lahore Congress; Purna Swaraj declared (Dec 31)
  1930 → Civil Disobedience; Dandi March (March 12)
  1931 → Gandhi-Irwin Pact (March 5)
  1935 → Government of India Act 1935
  1942 → Quit India Movement (August 9); "Do or Die"
  1947 → Independence (August 15); Partition
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Full DBMS + SQL Revision

---

**Q1.** A DBMS (Database Management System) is BEST described as:
(A) A hardware device for storing data
(B) Software that creates, manages, and controls access to a database, acting as interface between user and data
(C) A programming language used to create websites
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is CORRECT about Primary Keys?
(A) A table can have multiple Primary Keys as long as each is unique
(B) A table has ONLY ONE Primary Key, which cannot be NULL
(C) Primary Key and Unique Key are identical in all properties
(D) More than one of the above
(E) None of the above

---

**Q3.** Normalization is primarily done to:
(A) Increase redundancy for faster retrieval
(B) Reduce data redundancy and eliminate insertion, update, and deletion anomalies
(C) Make the database more complex for better security
(D) More than one of the above
(E) None of the above

---

**Q4.** 2NF (Second Normal Form) specifically removes:
(A) Transitive functional dependencies
(B) Multivalued attributes from cells
(C) Partial functional dependencies (where non-key attribute depends on only PART of composite PK)
(D) More than one of the above
(E) None of the above

---

**Q5.** 3NF (Third Normal Form) specifically removes:
(A) Partial functional dependencies on composite key
(B) Transitive functional dependencies (A → B → C where B is not a candidate key)
(C) Multivalued cells (non-atomic values)
(D) More than one of the above
(E) None of the above

---

**Q6.** TRUNCATE command in SQL is classified as:
(A) DML (Data Manipulation Language) — can be rolled back
(B) TCL (Transaction Control Language)
(C) DDL (Data Definition Language) — auto-committed, CANNOT be rolled back
(D) More than one of the above
(E) None of the above

---

**Q7.** The default sorting order of the ORDER BY clause in SQL is:
(A) DESC (Descending)
(B) RANDOM (no specific order)
(C) ASC (Ascending)
(D) More than one of the above
(E) None of the above

---

**Q8.** Which clause is used to filter GROUPS (after GROUP BY) in SQL?
(A) WHERE
(B) DISTINCT
(C) HAVING
(D) More than one of the above
(E) None of the above

---

**Q9.** COMPUTE is presented as an option for aggregate function in an exam. The correct answer is:
(A) COMPUTE is a valid standard SQL aggregate function equivalent to SUM
(B) COMPUTE is NOT a valid standard SQL aggregate function
(C) COMPUTE is a DDL command in advanced SQL
(D) More than one of the above
(E) None of the above

---

**Q10.** UNION in SQL is:
(A) A constraint that enforces uniqueness across two columns
(B) The same as the UNIQUE constraint
(C) A set operation that combines results of two SELECT queries (NOT a constraint)
(D) More than one of the above
(E) None of the above

---

**Q11.** The WITH clause in SQL creates:
(A) A permanent new table in the database
(B) A temporary named result set (Common Table Expression) valid only for that query
(C) A view that other users can access
(D) More than one of the above
(E) None of the above

---

**Q12.** Which statement about COMMIT and ROLLBACK is TRUE?
(A) ROLLBACK can undo a COMMIT if executed immediately after
(B) COMMIT permanently saves changes; after COMMIT, ROLLBACK has no effect
(C) ROLLBACK can undo DDL commands like TRUNCATE and DROP
(D) More than one of the above
(E) None of the above

---

**Q13.** In the Relational Model, which term corresponds to a ROW?
(A) Attribute
(B) Relation
(C) Tuple
(D) More than one of the above
(E) None of the above

---

**Q14.** METADATA in a database context is:
(A) The main business data stored (customer names, balances, marks)
(B) Data about data — structure, schema, column names, constraints
(C) The backup copy stored at a remote location
(D) More than one of the above
(E) None of the above

---

**Q15.** A WEAK ENTITY in the ER Model is characterised by:
(A) Having a very small number of rows
(B) Not having its own Primary Key — depends on a Strong Entity's PK for identification
(C) Having more than one Primary Key
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following is the CORRECT hierarchy of key types (most specific to most general)?
(A) Primary Key ⊂ Candidate Key ⊂ Super Key
(B) Super Key ⊂ Candidate Key ⊂ Primary Key
(C) Candidate Key ⊂ Primary Key ⊂ Super Key
(D) More than one of the above
(E) None of the above

---

**Q17.** Which SQL command removes a table's STRUCTURE and ALL ITS DATA permanently?
(A) DELETE (removes rows; keeps structure)
(B) TRUNCATE (removes all rows fast; keeps structure)
(C) DROP (removes both structure AND data permanently)
(D) More than one of the above
(E) None of the above

---

**Q18.** The following query has an error: SELECT DeptID, COUNT(*) FROM STUDENTS WHERE COUNT(*) > 2 GROUP BY DeptID;
The error is:
(A) GROUP BY cannot be used with COUNT(*)
(B) COUNT(*) cannot be used in WHERE clause — aggregate functions require HAVING
(C) DeptID cannot appear in SELECT along with COUNT(*)
(D) More than one of the above
(E) None of the above

---

**Q19.** A table with a SINGLE-ATTRIBUTE Primary Key is automatically:
(A) In 1NF only (still needs checking for 2NF)
(B) In both 1NF and 2NF (partial dependency impossible with single-attribute PK)
(C) In BCNF automatically
(D) More than one of the above
(E) None of the above

---

**Q20.** A FOREIGN KEY can:
(A) NEVER be NULL under any circumstances
(B) Be NULL (meaning this record has no associated parent record)
(C) Reference the Foreign Key of another table (not the Primary Key)
(D) More than one of the above
(E) None of the above

---

**Q21.** BCNF (Boyce-Codd Normal Form) is DIFFERENT from 3NF in that:
(A) BCNF is weaker — it allows some transitive dependencies
(B) BCNF is STRICTER — every determinant must be a super key (no exceptions)
(C) BCNF and 3NF are exactly equivalent in all cases
(D) More than one of the above
(E) None of the above

---

**Q22.** In an M:N (many-to-many) relationship between STUDENT and COURSE entities in the ER model, conversion to the Relational Model requires:
(A) Adding CourseID as a FK to the STUDENT table
(B) Adding StudentID as a FK to the COURSE table
(C) Creating a new ENROLLMENT junction table with both StudentID and CourseID as composite PK
(D) More than one of the above
(E) None of the above

---

**Q23.** The ER Model was proposed by _____ and the Relational Model by _____:
(A) E.F. Codd (1970) and Peter Chen (1976) respectively
(B) Peter Chen (1976) and E.F. Codd (1970) respectively
(C) Both were proposed by E.F. Codd
(D) More than one of the above
(E) None of the above

---

**Q24.** SELECT DISTINCT City FROM STUDENTS ORDER BY City; returns:
(A) All rows with city values, sorted descending (DESC is default)
(B) Each unique city name listed exactly once, sorted in ascending (A-Z) order
(C) All cities and their student counts
(D) More than one of the above
(E) None of the above

---

**Q25.** Which statement about the difference between DELETE and TRUNCATE is CORRECT?
(A) Both DELETE and TRUNCATE are DDL commands that cannot be rolled back
(B) DELETE is DML (can rollback, allows WHERE); TRUNCATE is DDL (auto-committed, no WHERE, faster)
(C) TRUNCATE can use WHERE clause to selectively delete rows; DELETE cannot
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Modern Indian History + Bihar Focus + Revolutionary Movements

---

**Q26.** Gandhi's FIRST Satyagraha in India was at:
(A) Kheda, Gujarat (1918)
(B) Champaran, Bihar (1917)
(C) Bardoli, Gujarat (1928)
(D) More than one of the above
(E) None of the above

---

**Q27.** The Champaran Satyagraha (1917) was connected to which agricultural practice?
(A) Forced paddy cultivation under the Zamindari system
(B) Forced indigo cultivation under the Tinkathia (3/20th) system
(C) Forced cotton cultivation under the British lease system
(D) More than one of the above
(E) None of the above

---

**Q28.** Who invited Gandhi to Champaran to take up the peasants' cause?
(A) Rajendra Prasad
(B) J.B. Kripalani
(C) Rajkumar Shukla (a farmer from Champaran)
(D) More than one of the above
(E) None of the above

---

**Q29.** The NON-COOPERATION MOVEMENT (1920-22) was called off because of:
(A) Gandhi's arrest and imprisonment in 1921
(B) The Jallianwala Bagh Massacre
(C) The Chauri Chaura Incident (4 February 1922, Gorakhpur, UP)
(D) More than one of the above
(E) None of the above

---

**Q30.** The Dandi March (Salt March) began on:
(A) 12 March 1930, from Sabarmati Ashram, Ahmedabad
(B) 9 August 1942, from Gowalia Tank, Bombay
(C) 1 January 1930, from Lahore
(D) More than one of the above
(E) None of the above

---

**Q31.** The slogan "DO OR DIE" (Karo ya Maro) was given by Gandhi during which movement?
(A) Non-Cooperation Movement (1920)
(B) Civil Disobedience Movement (1930)
(C) Quit India Movement (1942)
(D) More than one of the above
(E) None of the above

---

**Q32.** "QUIT INDIA" as a slogan was coined by:
(A) Mahatma Gandhi
(B) Yusuf Meherally
(C) Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q33.** The Gandhi-Irwin Pact was signed in:
(A) March 1930 (before the Dandi March)
(B) March 1931 (5 March — after the Civil Disobedience began)
(C) August 1942 (before the Quit India Movement)
(D) More than one of the above
(E) None of the above

---

**Q34.** The GHADAR PARTY was founded in 1913 at:
(A) London, England
(B) San Francisco, California, USA
(C) Lahore, Punjab (British India)
(D) More than one of the above
(E) None of the above

---

**Q35.** The FOUNDER-PRESIDENT of the Ghadar Party was:
(A) Har Dayal (intellectual leader)
(B) Kartar Singh Sarabha
(C) Sohan Singh Bhakna
(D) More than one of the above
(E) None of the above

---

**Q36.** The Ghadar Party newspaper "Ghadar" was published in:
(A) Only Punjabi language
(B) Only English, targeting educated elites
(C) Multiple languages: Punjabi, Urdu, Hindi, Gujarati, Pashto (5+ languages)
(D) More than one of the above
(E) None of the above

---

**Q37.** Kartar Singh Sarabha of the Ghadar Party is specially remembered because:
(A) He founded the Ghadar newspaper
(B) He was hanged at age 19 in 1915 and became Bhagat Singh's primary inspiration
(C) He led the Anushilan Samiti's Dhaka branch
(D) More than one of the above
(E) None of the above

---

**Q38.** The Anushilan Samiti was founded in:
(A) 1904, Nasik, Maharashtra
(B) 1913, San Francisco, USA
(C) 1902, Calcutta (Kolkata)
(D) More than one of the above
(E) None of the above

---

**Q39.** Khudiram Bose, the young revolutionary hanged in 1908, was connected with which event?
(A) Nasik Conspiracy (assassination of District Collector Jackson)
(B) Muzaffarpur Bomb Case (attempted bombing of Magistrate Kingsford's carriage)
(C) Ghadar Mutiny of 1915
(D) More than one of the above
(E) None of the above

---

**Q40.** V.D. Savarkar's Abhinav Bharat (1904, Nasik) was inspired by the revolutionary movement of:
(A) Lenin in Russia
(B) Giuseppe Mazzini's "Young Italy" movement
(C) Karl Marx's Communist Manifesto
(D) More than one of the above
(E) None of the above

---

**Q41.** V.D. Savarkar was sentenced to _____ years imprisonment and sent to:
(A) 25 years, Lahore Central Jail
(B) 50 years, Cellular Jail (Kala Pani), Andaman Islands
(C) Life imprisonment, Yeravada Jail, Pune
(D) More than one of the above
(E) None of the above

---

**Q42.** BIRSA MUNDA led the "ULGULAN" tribal revolt in 1899-1900 from the region known as:
(A) Santhal Parganas, Bengal
(B) Chota Nagpur (present-day Jharkhand)
(C) Telangana region, Hyderabad
(D) More than one of the above
(E) None of the above

---

**Q43.** The CHOTA NAGPUR TENANCY ACT (1908) was a direct legislative consequence of:
(A) The Ghadar Mutiny of 1915
(B) The Civil Disobedience Movement
(C) Birsa Munda's Ulgulan (1899-1900) — protecting tribal land rights
(D) More than one of the above
(E) None of the above

---

**Q44.** The Partition of Bengal (1905) was ordered by which Viceroy?
(A) Lord Curzon
(B) Lord Irwin
(C) Lord Minto
(D) More than one of the above
(E) None of the above

---

**Q45.** The Rowlatt Act (1919) was OPPOSED because:
(A) It imposed heavy taxes on salt
(B) It allowed arrest and detention without trial — called "Black Laws"
(C) It divided Bengal on religious lines
(D) More than one of the above
(E) None of the above

---

**Q46.** The Jallianwala Bagh Massacre occurred on:
(A) 4 February 1922 in Gorakhpur, UP
(B) 13 April 1919 in Amritsar, Punjab
(C) 9 August 1942 in Bombay, Maharashtra
(D) More than one of the above
(E) None of the above

---

**Q47.** General Dyer ordered firing at Jallianwala Bagh. Who was the Lieutenant Governor of Punjab who supported this action?
(A) Lord Curzon
(B) Lord Irwin
(C) Michael O'Dwyer
(D) More than one of the above
(E) None of the above

---

**Q48.** The Indian National Congress was founded in 1885 by:
(A) Mahatma Gandhi
(B) Bal Gangadhar Tilak
(C) A.O. Hume (Allan Octavian Hume) with cooperation of Indian leaders
(D) More than one of the above
(E) None of the above

---

**Q49.** The Lucknow Pact (1916) was signed between:
(A) Gandhi and Jinnah
(B) Indian National Congress and Muslim League (to work together)
(C) Bal Gangadhar Tilak and Lord Chelmsford
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following statements:
I.   Champaran Satyagraha (1917) was Gandhi's FIRST Satyagraha in India, against the indigo (Tinkathia) system.
II.  The Quit India Movement (1942) slogan "Do or Die" was given by Gandhi; "Quit India" was coined by Yusuf Meherally.
III. The Non-Cooperation Movement was called off due to the Chauri Chaura Incident (Feb 4, 1922) in Gorakhpur.
IV.  The Ghadar Party (1913, San Francisco) was non-communal, with Sohan Singh Bhakna as its first president.

How many statements are CORRECT?
(A) Only I and III
(B) Only I, II, and III
(C) All four (I, II, III, IV) are correct
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
| 1 | (B) | DBMS = software managing database; interface between user and data |
| 2 | (B) | Only ONE PK per table; PK cannot be NULL |
| 3 | (B) | Normalization = reduce redundancy + eliminate anomalies |
| 4 | (C) | 2NF removes PARTIAL functional dependencies |
| 5 | (B) | 3NF removes TRANSITIVE functional dependencies |
| 6 | (C) | TRUNCATE = DDL = auto-committed = CANNOT rollback |
| 7 | (C) | ORDER BY default = ASC (ascending) |
| 8 | (C) | HAVING filters groups AFTER GROUP BY |
| 9 | (B) | COMPUTE is NOT a valid standard SQL aggregate function |
| 10 | (C) | UNION = set operation (NOT a constraint) |
| 11 | (B) | WITH = CTE = temporary named result set |
| 12 | (B) | After COMMIT → ROLLBACK has no effect; changes permanent |
| 13 | (C) | Tuple = ROW in relational model |
| 14 | (B) | Metadata = data about data = schema, column names, constraints |
| 15 | (B) | Weak entity = no own PK; depends on strong entity |
| 16 | (A) | Primary Key ⊂ Candidate Key ⊂ Super Key (PK is most specific) |
| 17 | (C) | DROP removes BOTH structure and data permanently |
| 18 | (B) | Aggregate functions cannot be in WHERE clause; use HAVING |
| 19 | (B) | Single-attribute PK → automatically 2NF (no partial dep possible) |
| 20 | (B) | Foreign Key CAN be NULL |
| 21 | (B) | BCNF is STRICTER than 3NF (every determinant must be super key) |
| 22 | (C) | M:N → new junction/enrollment table with composite PK |
| 23 | (B) | ER Model = Peter Chen (1976); Relational = E.F. Codd (1970) |
| 24 | (B) | DISTINCT = unique cities; ORDER BY default = ASC (A-Z) |
| 25 | (B) | DELETE = DML (rollback-able, WHERE); TRUNCATE = DDL (auto-committed, no WHERE) |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Champaran 1917 = Gandhi's first Satyagraha in India |
| 27 | (B) | Champaran = forced indigo cultivation (Tinkathia = 3/20th system) |
| 28 | (C) | Rajkumar Shukla = farmer who invited Gandhi to Champaran |
| 29 | (C) | Non-Cooperation called off = Chauri Chaura Incident, Feb 4, 1922 |
| 30 | (A) | Dandi March = 12 March 1930, from Sabarmati Ashram |
| 31 | (C) | "Do or Die" = Quit India Movement (1942) |
| 32 | (B) | "Quit India" slogan coined by Yusuf Meherally |
| 33 | (B) | Gandhi-Irwin Pact = 5 March 1931 |
| 34 | (B) | Ghadar Party = 1913, San Francisco, USA |
| 35 | (C) | Sohan Singh Bhakna = founder-president of Ghadar Party |
| 36 | (C) | Ghadar newspaper = multi-language (Punjabi, Urdu, Hindi, Gujarati, Pashto) |
| 37 | (B) | Sarabha hanged at 19 (1915); Bhagat Singh's idol |
| 38 | (C) | Anushilan Samiti = 1902, Calcutta |
| 39 | (B) | Khudiram Bose = Muzaffarpur Bomb Case (1908), hanged at 18 |
| 40 | (B) | Abhinav Bharat inspired by Mazzini's "Young Italy" |
| 41 | (B) | Savarkar = 50 years, Cellular Jail (Kala Pani), Andaman |
| 42 | (B) | Birsa Munda = Chota Nagpur (present-day Jharkhand) |
| 43 | (C) | CNT Act 1908 = direct legacy of Birsa's Ulgulan (1899-1900) |
| 44 | (A) | Partition of Bengal 1905 = ordered by Lord Curzon (Viceroy) |
| 45 | (B) | Rowlatt Act = arrest without trial = "Black Laws" |
| 46 | (B) | Jallianwala Bagh = 13 April 1919, Amritsar, Punjab |
| 47 | (C) | Michael O'Dwyer = Lt. Governor of Punjab who supported Dyer |
| 48 | (C) | INC founded 1885 by A.O. Hume |
| 49 | (B) | Lucknow Pact 1916 = Congress + Muslim League alliance |
| 50 | (C) | All four statements I, II, III, IV are correct |

---
---

# 🔁 COMPLETE REVISION NOTES — LAST-DAY REFERENCE

## ⚡ DBMS ONE-LINE MASTERY

### Core Definitions:
```
DATABASE   = Structured organised collection of RELATED data
DBMS       = Software MANAGING the database; interface between user and data
NOT DBMS   = Google (search engine), Notepad, Excel standalone
METADATA   = Data ABOUT data (schema, column names, types, constraints)
SCHEMA     = Structure definition (permanent); INSTANCE = current data (dynamic)
```

### Key Hierarchy (Most Specific → Most General):
```
PRIMARY KEY ⊂ CANDIDATE KEY ⊂ SUPER KEY

Primary Key: ONE per table; CANNOT be NULL; chosen from candidates
Candidate:   MINIMAL super key; cannot remove any attribute
Super Key:   Any set that uniquely identifies rows (may have extras)
Foreign Key: References PK of another table; CAN be NULL
Unique Key:  Ensures uniqueness; CAN be NULL; MULTIPLE per table
Composite:   2+ attributes combined as key
Alternate:   Candidate keys NOT chosen as primary
```

### Normalization Speed Reference:
```
1NF: ATOMIC values (no lists in cells, no repeating columns)
2NF: No PARTIAL dependency (non-key depends on PART of composite PK)
     Only matters with COMPOSITE PK!
3NF: No TRANSITIVE dependency (A → B → C where B is non-key)
     MOST USED in practice!
BCNF: Every DETERMINANT = super key (stricter than 3NF)
      BCNF ⊂ 3NF (all BCNF is 3NF; not all 3NF is BCNF)
```

### SQL Category + Auto-Commit:
```
DDL (CREATE/ALTER/DROP/TRUNCATE): AUTO-COMMITTED → CANNOT rollback
DML (SELECT/INSERT/UPDATE/DELETE): NOT auto-committed → CAN rollback
DCL (GRANT/REVOKE): AUTO-COMMITTED → CANNOT rollback
TCL (COMMIT/ROLLBACK/SAVEPOINT): Manages DML transactions
```

### SQL Clauses Execution Order:
```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
"From Where Groups Have Select Order"
WHERE = before grouping; HAVING = after grouping
WHERE cannot use aggregates; HAVING can/must use aggregates
ORDER BY default = ASC (most tested PYQ!)
```

---

## ⚡ COMPLETE PYQ TRAP LIST

```
DBMS TRAPS:
01. DBMS does NOT support single-user only → MULTI-USER is a FEATURE
02. Google is NOT a DBMS → search engine
03. "Decentralized database" is not standard → correct = DISTRIBUTED
04. Database ≠ DBMS (data collection ≠ software)

KEY TRAPS:
05. Only ONE Primary Key per table
06. Primary Key CANNOT be NULL (ever!)
07. Unique Key CAN be NULL (multiple NULLs allowed)
08. Foreign Key references PK of another table (not FK)
09. Foreign Key CAN be NULL
10. Candidate Key MUST be minimal (super key with extras ≠ candidate key)

ER/RELATIONAL TRAPS:
11. Tuple = ROW (not column); Attribute = COLUMN; Relation = TABLE
12. Degree = # of COLUMNS; Cardinality = # of ROWS
13. Metadata = data ABOUT data (schema = metadata, not actual data)
14. Derived attribute NOT stored → calculated on demand (dashed oval in ER)
15. ER Model = Peter Chen (1976); Relational Model = E.F. Codd (1970)

NORMALIZATION TRAPS:
16. 2NF removes PARTIAL (not transitive); 3NF removes TRANSITIVE (not partial)
17. Single-attribute PK → automatically 2NF
18. Normalization DECREASES redundancy (not increases)
19. BCNF is STRICTER than 3NF (not weaker/equivalent)
20. Normalization = LOSSLESS (data always recoverable from joined tables)

SQL COMMAND TRAPS:
21. TRUNCATE = DDL (NOT DML!) → CANNOT rollback
22. SELECT = DML (NOT DDL!)
23. GRANT/REVOKE = DCL (NOT DML!)
24. After COMMIT → ROLLBACK has NO effect
25. ROLLBACK cannot undo DDL commands (auto-committed)

SQL CLAUSE TRAPS:
26. ORDER BY default = ASC (NOT DESC)
27. HAVING comes AFTER GROUP BY to filter groups
28. WHERE CANNOT use aggregate functions → use HAVING
29. BETWEEN is INCLUSIVE (includes boundary values)
30. % = multiple chars; _ = exactly ONE char (LIKE patterns)
31. COUNT(*) counts NULLs; COUNT(col) skips NULLs

AGGREGATE TRAPS:
32. COMPUTE is NOT a valid aggregate function (NOT COUNT/SUM/AVG/MAX/MIN)
33. AVG ignores NULL values (doesn't count NULL as 0)

CONSTRAINT TRAPS:
34. UNION is NOT a constraint (it's a SET OPERATION)
35. Valid constraints: PK, FK, UNIQUE, NOT NULL, DEFAULT, CHECK
```

---

## ⚡ HISTORY QUICK FACTS

```
GANDHIAN MOVEMENTS TIMELINE:
  1917 → Champaran Satyagraha (FIRST in India; Bihar; indigo/Tinkathia; Rajkumar Shukla invited Gandhi)
  1918 → Kheda Satyagraha (Gujarat; Patel's rise)
  1919 → Rowlatt Act + Jallianwala Bagh (13 April, Amritsar; General Dyer)
  1920 → Non-Cooperation Movement begins
  1922 → Chauri Chaura (4 Feb, Gorakhpur) → NCM called off
  1930 → Civil Disobedience; Dandi March (12 March, Sabarmati→Dandi, 241 miles)
  1931 → Gandhi-Irwin Pact (5 March)
  1942 → Quit India (9 August); "Do or Die" = Gandhi; "Quit India" = Yusuf Meherally

REVOLUTIONARY MOVEMENTS:
  1902 → Anushilan Samiti (Calcutta; P.N. Mitra; Khudiram Bose hanged 1908 age 18)
  1904 → Abhinav Bharat (Nasik; Savarkar; Mazzini inspiration; 50 yrs Kala Pani)
  1913 → Ghadar Party (San Francisco; Sohan Singh Bhakna; Har Dayal intellect; non-communal)
  1915 → Ghadar Mutiny FAILED; Kartar Singh Sarabha (age 19) = Bhagat Singh's idol

BIHAR SPECIFIC:
  1899-1900 → Birsa Munda's Ulgulan (Chota Nagpur; "Dharti Abba"; died Ranchi Jail 1900)
  1908 → CNT Act (Chota Nagpur Tenancy Act) = Birsa's legacy
  1917 → Champaran Satyagraha → Rajendra Prasad emerged (First President of India!)
  15 Nov = Birsa's birthday = JHARKHAND FOUNDATION DAY (state formed 2000)
  "Sorrow of Bihar" = KOSI River (floods in North Bihar)
```

---

## 🎯 FINAL REVISION CHECKLIST

### DBMS — Can You Answer These?
```
□ What is DBMS? What does it sit between?
□ What are the 3 anomalies normalization solves?
□ What does 1NF, 2NF, 3NF each remove?
□ Super Key vs Candidate Key (key difference)?
□ Can Primary Key be NULL? Can Foreign Key be NULL?
□ Which key can appear multiple times per table?
□ TRUNCATE vs DELETE (category, rollback, WHERE)?
□ What does ORDER BY do by default?
□ When to use WHERE vs HAVING?
□ Is COMPUTE a valid aggregate? Is UNION a constraint?
□ What does COMMIT do? Can ROLLBACK undo it?
□ WITH clause = temporary or permanent?
□ DDL commands = auto-committed? DML?
```

### History — Can You Answer These?
```
□ Gandhi's first Satyagraha in India = ?
□ Who invited Gandhi to Champaran?
□ What system did Champaran fight against?
□ Why was Non-Cooperation called off? Where? When?
□ Dandi March: date, distance, from where to where?
□ "Do or Die" = whose slogan, which movement?
□ "Quit India" = whose coinage?
□ Ghadar Party: year, place, founder-president?
□ Who was Bhagat Singh's idol in the Ghadar Party?
□ Anushilan Samiti: year, place, key event?
□ Abhinav Bharat: founder, inspiration, fate?
□ Birsa Munda's revolt name? Legacy?
□ 15 November = significance?
```

---

*🚀 This module covers everything you need to revise DBMS + SQL + Modern Indian History in one comprehensive session. Mark your weak areas, review those sections, and you'll be exam-ready! You're 25%+ through the 170-day journey — stay consistent, the foundation is strong!*
