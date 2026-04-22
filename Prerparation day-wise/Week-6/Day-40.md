# 📅 BPSC TRE 4.0 — DAY 40 COMPLETE STUDY MODULE
### SQL Commands (DDL, DML, DCL, TCL) + Photoperiodism (Biology)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): SQL Commands — DDL, DML, DCL, TCL with examples and traps
> - Afternoon (1 hr): Biology — Photoperiodism, Garner & Allard, Light in plant growth
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 SQL Commands — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is SQL?

### Real-Life Analogy — The Bank Teller Language:

Imagine you walk into a bank. You need to:
- Open a new account (CREATE)
- Deposit money (INSERT)
- Check your balance (SELECT)
- Withdraw money (DELETE/UPDATE)
- Lock your account (REVOKE)
- Permanently record a transaction (COMMIT)

Every operation you ask the bank to perform follows a standard protocol — a scripted language both you and the bank understand perfectly.

**SQL is exactly that — the standard language for communicating with a relational database.**

### Formal Definition:
> **SQL (Structured Query Language) is a standardised language used to create, manage, query, and control data in Relational Database Management Systems (RDBMS).**

### Key Facts:
```
FULL FORM:    SQL = Structured Query Language
DEVELOPED BY: IBM (Donald Chamberlin & Raymond Boyce), early 1970s
              Originally called "SEQUEL" (Structured English Query Language)
STANDARDISED: ANSI (American National Standards Institute) — 1986
              ISO standard also maintained
              
USED WITH: MySQL, Oracle, PostgreSQL, SQL Server, SQLite, etc.

SQL IS:
  → NOT a programming language (no loops, conditionals in basic SQL)
  → A DECLARATIVE language: you say WHAT you want, not HOW to get it
  → Case-INSENSITIVE for keywords (SELECT = select = Select)
  → Case-SENSITIVE for data values in most databases

🎯 PYQ FACT: SQL is a DECLARATIVE language, not procedural.
             It was developed by IBM and standardised by ANSI.
```

---

## 🔷 SECTION 2: SQL Command Categories — Overview

SQL commands are divided into **four major categories** based on their PURPOSE:

```
                         SQL COMMANDS
                              │
        ┌─────────────────────┼─────────────────────┐
        │              │              │              │
       DDL            DML            DCL            TCL
  (Definition)    (Manipulation)  (Control)   (Transaction)
        │              │              │              │
  CREATE         SELECT          GRANT          COMMIT
  ALTER          INSERT          REVOKE         ROLLBACK
  DROP           UPDATE                         SAVEPOINT
  TRUNCATE       DELETE
  RENAME

MEMORY TRICK: "Do Data Daily, Technically"
  D = DDL (Definition)
  D = DML (Manipulation)  
  D = DCL (Control)
  T = TCL (Transaction)
```

### Master Classification Table:

```
┌──────────────┬──────────────────────┬────────────────────────────────────┐
│   CATEGORY   │       PURPOSE        │            COMMANDS                │
├──────────────┼──────────────────────┼────────────────────────────────────┤
│ DDL          │ Define/modify the    │ CREATE, ALTER, DROP,               │
│ (Data        │ STRUCTURE of         │ TRUNCATE, RENAME                   │
│ Definition   │ database objects     │                                    │
│ Language)    │ (tables, schemas)    │                                    │
├──────────────┼──────────────────────┼────────────────────────────────────┤
│ DML          │ Manipulate/work      │ SELECT, INSERT,                    │
│ (Data        │ with the ACTUAL DATA │ UPDATE, DELETE                     │
│ Manipulation │ inside tables        │                                    │
│ Language)    │                      │                                    │
├──────────────┼──────────────────────┼────────────────────────────────────┤
│ DCL          │ Control ACCESS and   │ GRANT, REVOKE                      │
│ (Data        │ PERMISSIONS to       │                                    │
│ Control      │ database objects     │                                    │
│ Language)    │                      │                                    │
├──────────────┼──────────────────────┼────────────────────────────────────┤
│ TCL          │ Manage TRANSACTIONS  │ COMMIT, ROLLBACK,                  │
│ (Transaction │ (make changes        │ SAVEPOINT                          │
│ Control      │ permanent or undo)   │                                    │
│ Language)    │                      │                                    │
└──────────────┴──────────────────────┴────────────────────────────────────┘
```

---

## 🔷 SECTION 3: DDL — Data Definition Language

### Purpose: Define and manage the STRUCTURE (schema) of the database.

DDL commands work on DATABASE OBJECTS (tables, indexes, views) — not on data inside them.

> **DDL commands are AUTO-COMMITTED** — changes are permanent immediately. They cannot be rolled back with ROLLBACK!

---

### COMMAND 1: CREATE

```
PURPOSE: Create new database objects (tables, databases, indexes, views)

SYNTAX — Create a Table:
  CREATE TABLE table_name (
      column1  datatype  constraint,
      column2  datatype  constraint,
      ...
  );

EXAMPLE — Create STUDENTS table:
  CREATE TABLE STUDENTS (
      RollNo    INT         PRIMARY KEY,
      Name      VARCHAR(50) NOT NULL,
      Email     VARCHAR(100) UNIQUE,
      DeptID    VARCHAR(10),
      Marks     INT         DEFAULT 0,
      DOB       DATE
  );

EXAMPLE — Create a DATABASE:
  CREATE DATABASE CollegeDB;

EXAMPLE — Create a VIEW:
  CREATE VIEW CS_Students AS
  SELECT RollNo, Name, Marks
  FROM STUDENTS
  WHERE DeptID = 'CS';

CONSTRAINTS used in CREATE:
  PRIMARY KEY    → unique identifier, not null
  NOT NULL       → column must always have a value
  UNIQUE         → all values must be distinct
  DEFAULT value  → if no value given, use this default
  FOREIGN KEY    → references another table's PK
  CHECK          → value must satisfy a condition
  
EXAMPLE with all constraints:
  CREATE TABLE EMPLOYEES (
      EmpID   INT          PRIMARY KEY,
      Name    VARCHAR(50)  NOT NULL,
      Salary  DECIMAL(10,2) DEFAULT 20000,
      Age     INT          CHECK (Age >= 18 AND Age <= 65),
      Email   VARCHAR(100) UNIQUE,
      DeptID  INT,
      FOREIGN KEY (DeptID) REFERENCES DEPARTMENTS(DeptID)
  );
```

---

### COMMAND 2: ALTER

```
PURPOSE: Modify the STRUCTURE of an existing table
         → Add/remove/modify columns
         → Add/drop constraints
         → Rename table or column

TYPES OF ALTER OPERATIONS:

1. ADD a new column:
   ALTER TABLE STUDENTS ADD PhoneNo VARCHAR(15);

2. DROP (remove) a column:
   ALTER TABLE STUDENTS DROP COLUMN PhoneNo;

3. MODIFY/ALTER a column's data type or constraint:
   ALTER TABLE STUDENTS MODIFY Marks DECIMAL(5,2);  -- MySQL syntax
   ALTER TABLE STUDENTS ALTER COLUMN Marks DECIMAL(5,2);  -- SQL Server

4. RENAME a column:
   ALTER TABLE STUDENTS RENAME COLUMN Marks TO FinalMarks;

5. RENAME a table:
   ALTER TABLE STUDENTS RENAME TO ENROLLED_STUDENTS;

6. ADD a constraint:
   ALTER TABLE STUDENTS ADD CONSTRAINT chk_marks CHECK (Marks >= 0 AND Marks <= 100);

7. DROP a constraint:
   ALTER TABLE STUDENTS DROP CONSTRAINT chk_marks;

KEY POINT: ALTER does NOT delete data. 
           It changes the structure around existing data.
           
🎯 PYQ FACT: ALTER modifies structure WITHOUT deleting existing data.
```

---

### COMMAND 3: DROP

```
PURPOSE: PERMANENTLY DELETE an entire database object (table, database, view, index)
         ALL DATA and STRUCTURE are deleted.

SYNTAX:
  DROP TABLE table_name;
  DROP DATABASE database_name;
  DROP VIEW view_name;
  DROP INDEX index_name;

EXAMPLES:
  DROP TABLE STUDENTS;           -- Deletes table AND all its data permanently!
  DROP DATABASE CollegeDB;       -- Deletes entire database!
  DROP VIEW CS_Students;         -- Deletes the view definition

WARNING:
  → DROP is IRREVERSIBLE (cannot be undone!)
  → The entire table including structure and data is GONE
  → Unlike DELETE (which removes rows but keeps the table structure)

🎯 PYQ: DROP removes BOTH structure AND data permanently.
         DELETE removes only ROWS but keeps the table structure.
```

---

### COMMAND 4: TRUNCATE

```
PURPOSE: REMOVE ALL ROWS from a table QUICKLY, but KEEP the table structure.

SYNTAX:
  TRUNCATE TABLE STUDENTS;
  TRUNCATE STUDENTS;  -- (shorter form in some databases)

WHAT HAPPENS:
  BEFORE TRUNCATE:
  ┌────────┬──────────┬────────┐
  │ RollNo │  Name    │ Marks  │
  ├────────┼──────────┼────────┤
  │  101   │  Ravi    │  85    │
  │  102   │  Priya   │  90    │
  │  103   │  Aman    │  78    │
  └────────┴──────────┴────────┘

  AFTER TRUNCATE:
  ┌────────┬──────────┬────────┐
  │ RollNo │  Name    │ Marks  │
  ├────────┼──────────┼────────┤
  └────────┴──────────┴────────┘
  (Table is EMPTY but still EXISTS with its structure!)

WHY IS TRUNCATE FASTER THAN DELETE?
  TRUNCATE: Drops entire data pages at once (OS-level operation)
            Does NOT log individual row deletions
            Resets AUTO-INCREMENT counters
  DELETE:   Logs each row deletion individually (slower for large tables)
            Can use WHERE clause to delete selective rows
            Does NOT reset AUTO-INCREMENT counters

🚨 PYQ TRAP — THE MOST IMPORTANT TRUNCATE FACT:
  TRUNCATE is a DDL command → AUTO-COMMITTED → CANNOT BE ROLLED BACK!
  
  If you do: TRUNCATE TABLE STUDENTS;
             ROLLBACK;  ← This DOES NOT bring data back!
  
  vs.
  If you do: DELETE FROM STUDENTS;
             ROLLBACK;  ← This DOES bring data back! (DELETE is DML)
```

---

### COMMAND 5: RENAME

```
PURPOSE: Rename a database object

SYNTAX:
  RENAME TABLE old_name TO new_name;        -- MySQL
  ALTER TABLE old_name RENAME TO new_name;  -- Standard SQL

EXAMPLE:
  RENAME TABLE STUDENTS TO ENROLLED_STUDENTS;
```

---

## 🔷 SECTION 4: DML — Data Manipulation Language

### Purpose: Operate on the ACTUAL DATA inside tables.

DML commands work on ROWS and DATA — not on structure.

> **DML commands are NOT auto-committed** — changes can be undone with ROLLBACK until COMMIT is executed.

---

### COMMAND 1: SELECT

```
PURPOSE: RETRIEVE/QUERY data from tables — the most used SQL command!

BASIC SYNTAX:
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition
  ORDER BY column [ASC|DESC]
  GROUP BY column
  HAVING group_condition
  LIMIT n;

STEP-BY-STEP EXAMPLES:

1. Select ALL columns:
   SELECT * FROM STUDENTS;
   (Returns all rows, all columns)

2. Select SPECIFIC columns:
   SELECT RollNo, Name, Marks FROM STUDENTS;

3. WHERE clause (filter rows):
   SELECT * FROM STUDENTS WHERE Marks > 80;
   SELECT * FROM STUDENTS WHERE DeptID = 'CS';
   SELECT * FROM STUDENTS WHERE Marks BETWEEN 70 AND 90;
   SELECT * FROM STUDENTS WHERE Name LIKE 'R%';  -- starts with R

4. ORDER BY (sort results):
   SELECT * FROM STUDENTS ORDER BY Marks DESC;  -- highest first
   SELECT * FROM STUDENTS ORDER BY Name ASC;    -- alphabetical

5. GROUP BY (aggregate groups):
   SELECT DeptID, AVG(Marks) as AvgMarks
   FROM STUDENTS
   GROUP BY DeptID;
   
6. HAVING (filter after grouping — WHERE for groups):
   SELECT DeptID, COUNT(*) as StudentCount
   FROM STUDENTS
   GROUP BY DeptID
   HAVING COUNT(*) > 5;  -- only depts with more than 5 students

7. AGGREGATE FUNCTIONS:
   SELECT COUNT(*) FROM STUDENTS;          -- total rows
   SELECT SUM(Marks) FROM STUDENTS;        -- total of marks
   SELECT AVG(Marks) FROM STUDENTS;        -- average marks
   SELECT MAX(Marks) FROM STUDENTS;        -- highest mark
   SELECT MIN(Marks) FROM STUDENTS;        -- lowest mark

8. DISTINCT (remove duplicates):
   SELECT DISTINCT DeptID FROM STUDENTS;   -- unique departments

🎯 PYQ FACT: WHERE filters BEFORE grouping; HAVING filters AFTER grouping.
             HAVING is used WITH GROUP BY.
```

---

### COMMAND 2: INSERT

```
PURPOSE: Add new rows to a table

SYNTAX — Insert with all columns:
  INSERT INTO table_name VALUES (val1, val2, val3, ...);

SYNTAX — Insert with specific columns:
  INSERT INTO table_name (col1, col2, col3) VALUES (val1, val2, val3);

EXAMPLES:
  -- Insert a complete student record:
  INSERT INTO STUDENTS VALUES (101, 'Ravi Kumar', 'r@mail.com', 'CS', 85);

  -- Insert with specific columns (others get DEFAULT or NULL):
  INSERT INTO STUDENTS (RollNo, Name, DeptID) VALUES (104, 'Kavya', 'Math');

  -- Insert MULTIPLE rows at once:
  INSERT INTO STUDENTS VALUES
    (102, 'Priya Singh', 'p@mail.com', 'Math', 90),
    (103, 'Aman Gupta', 'a@mail.com', 'CS', 78);
```

---

### COMMAND 3: UPDATE

```
PURPOSE: MODIFY existing data in one or more rows

SYNTAX:
  UPDATE table_name
  SET column1 = value1, column2 = value2, ...
  WHERE condition;

EXAMPLES:
  -- Update one student's marks:
  UPDATE STUDENTS SET Marks = 92 WHERE RollNo = 101;

  -- Update multiple columns at once:
  UPDATE STUDENTS 
  SET Marks = 88, DeptID = 'Math' 
  WHERE RollNo = 102;

  -- Update ALL rows (dangerous! — no WHERE clause):
  UPDATE STUDENTS SET Marks = 0;  -- ALL students get marks = 0!

⚠️ WARNING: Always use WHERE with UPDATE!
            Without WHERE → ALL rows are modified!

🎯 PYQ: UPDATE without WHERE affects ALL rows in the table.
```

---

### COMMAND 4: DELETE

```
PURPOSE: REMOVE specific rows from a table

SYNTAX:
  DELETE FROM table_name WHERE condition;

EXAMPLES:
  -- Delete one specific student:
  DELETE FROM STUDENTS WHERE RollNo = 101;

  -- Delete students with low marks:
  DELETE FROM STUDENTS WHERE Marks < 40;

  -- Delete ALL rows (dangerous! — no WHERE clause):
  DELETE FROM STUDENTS;  -- ALL rows deleted, but table structure remains!

KEY DIFFERENCES FROM TRUNCATE:
  DELETE:   → DML command (can be rolled back!)
             → Logs each row deletion (slower)
             → Can use WHERE to delete selective rows
             → Does NOT reset auto-increment counter
             → Triggers fire for each deleted row
             
  TRUNCATE: → DDL command (CANNOT be rolled back!)
             → Faster (drops data pages at once)
             → No WHERE clause allowed
             → Resets auto-increment counter
             → Triggers do NOT fire
```

---

## 🔷 SECTION 5: DELETE vs TRUNCATE — The Most Tested Comparison

```
┌──────────────────────┬──────────────────────────┬──────────────────────────┐
│       FEATURE        │          DELETE           │         TRUNCATE         │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Category             │ DML (Data Manipulation)   │ DDL (Data Definition)    │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Can be ROLLED BACK?  │ YES — can be undone       │ NO — auto-committed!     │
│                      │ (if not yet committed)    │ PERMANENT immediately    │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ WHERE clause?        │ YES — can delete          │ NO — removes ALL rows    │
│                      │ specific rows             │ always                   │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Speed                │ SLOWER (logs each row)    │ FASTER (bulk operation)  │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Table structure?     │ Keeps structure           │ Keeps structure          │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Auto-increment reset?│ NO — counter continues    │ YES — resets to 1        │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Triggers?            │ YES — triggers fire       │ NO — triggers don't fire │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Log individual rows? │ YES (detailed log)        │ NO (deallocation only)   │
├──────────────────────┼──────────────────────────┼──────────────────────────┤
│ Selective deletion?  │ YES (WHERE condition)     │ NO (all rows always)     │
└──────────────────────┴──────────────────────────┴──────────────────────────┘

MEMORY TRICK:
  "DELETE is careful — logs each step, can undo"
  "TRUNCATE is fast and final — no undo, no WHERE, resets everything"
```

---

## 🔷 SECTION 6: DCL — Data Control Language

### Purpose: Control WHO can do WHAT in the database (permissions/privileges).

```
DCL COMMANDS: GRANT and REVOKE

These are used by the DATABASE ADMINISTRATOR (DBA) to:
→ Give users permission to access/modify database objects
→ Remove previously given permissions
```

### COMMAND 1: GRANT

```
PURPOSE: Give specific PERMISSIONS (privileges) to a user

SYNTAX:
  GRANT privilege_list ON object TO user;

PRIVILEGE TYPES:
  SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, ALL PRIVILEGES

EXAMPLES:
  -- Give Ravi permission to SELECT from STUDENTS:
  GRANT SELECT ON STUDENTS TO 'ravi'@'localhost';

  -- Give Priya permission to INSERT and UPDATE:
  GRANT INSERT, UPDATE ON STUDENTS TO 'priya'@'localhost';

  -- Give ALL permissions to admin user:
  GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost';

  -- Grant with ability to pass the privilege to others:
  GRANT SELECT ON STUDENTS TO 'manager'@'localhost' WITH GRANT OPTION;
  
  (WITH GRANT OPTION allows manager to grant this permission to others)

REAL-WORLD USE:
  Hospital DB: Nurse → GRANT SELECT, UPDATE on PATIENT_RECORDS
               Receptionist → GRANT SELECT, INSERT on APPOINTMENTS
               Billing staff → GRANT SELECT on BILLING only
```

### COMMAND 2: REVOKE

```
PURPOSE: REMOVE previously granted permissions

SYNTAX:
  REVOKE privilege_list ON object FROM user;

EXAMPLES:
  -- Remove Ravi's SELECT permission:
  REVOKE SELECT ON STUDENTS FROM 'ravi'@'localhost';

  -- Remove ALL permissions from a user:
  REVOKE ALL PRIVILEGES ON STUDENTS FROM 'priya'@'localhost';

IMPORTANT: If user A granted permission to user B with GRANT OPTION,
           and A's permission is revoked → B's permission is also revoked!
           This is called CASCADE REVOKE.
```

---

## 🔷 SECTION 7: TCL — Transaction Control Language

### What is a Transaction?

```
TRANSACTION = A sequence of SQL operations that are treated as a SINGLE UNIT.
              Either ALL operations succeed together, OR ALL fail together.
              
ANALOGY: BANK TRANSFER of ₹10,000 from Account A to Account B:
  Step 1: DEDUCT ₹10,000 from Account A
  Step 2: ADD ₹10,000 to Account B
  
  These TWO steps are ONE TRANSACTION.
  → If Step 1 succeeds but Step 2 fails (power cut) →
    Both steps must be UNDONE (rolled back)
  → Money can't vanish in the middle of a transfer!

ACID Properties of Transactions:
  A = Atomicity    → All or nothing (whole transaction or none)
  C = Consistency  → DB moves from one valid state to another
  I = Isolation    → Concurrent transactions don't interfere
  D = Durability   → Committed transactions survive failures
```

---

### COMMAND 1: COMMIT

```
PURPOSE: PERMANENTLY SAVE all changes made in the current transaction.
         Once committed, changes CANNOT be undone by ROLLBACK.

SYNTAX:
  COMMIT;
  COMMIT WORK;  -- alternative syntax

ANALOGY: Saving a document (Ctrl+S).
         After you save, the changes are permanent.
         "Commit" = officially recording the transaction in the database.

EXAMPLE:
  BEGIN TRANSACTION;
  INSERT INTO ACCOUNTS VALUES (101, 5000);
  UPDATE ACCOUNTS SET Balance = Balance - 1000 WHERE AccID = 101;
  COMMIT;  ← Changes are NOW permanently saved!
  
  -- After COMMIT, ROLLBACK does nothing:
  ROLLBACK;  ← This CANNOT undo the committed changes!

🎯 PYQ FACT: COMMIT = makes changes PERMANENT. Cannot be undone by ROLLBACK.
```

---

### COMMAND 2: ROLLBACK

```
PURPOSE: UNDO all changes made since the last COMMIT (or SAVEPOINT).
         Restores the database to its previous consistent state.

SYNTAX:
  ROLLBACK;
  ROLLBACK WORK;  -- alternative
  ROLLBACK TO SAVEPOINT savepoint_name;  -- partial rollback

ANALOGY: Ctrl+Z (Undo). Goes back to the last saved state.

EXAMPLE:
  START TRANSACTION;
  DELETE FROM STUDENTS WHERE RollNo = 101;  -- Ravi deleted
  DELETE FROM STUDENTS WHERE RollNo = 102;  -- Priya deleted
  -- Realise this was a mistake!
  ROLLBACK;  ← Both deletes are UNDONE! Ravi and Priya are back.

IMPORTANT CONDITIONS FOR ROLLBACK:
  ✅ Works only on DML commands (SELECT, INSERT, UPDATE, DELETE)
  ❌ CANNOT rollback DDL commands (CREATE, DROP, TRUNCATE — auto-committed!)
  ❌ CANNOT rollback DCL commands (GRANT, REVOKE — auto-committed!)
  ❌ Cannot rollback after COMMIT

🎯 PYQ FACT: ROLLBACK undoes uncommitted DML changes.
             ROLLBACK cannot undo TRUNCATE or DROP!
```

---

### COMMAND 3: SAVEPOINT

```
PURPOSE: Create a CHECKPOINT within a transaction.
         Allows PARTIAL rollback (go back to savepoint, not full rollback).

SYNTAX:
  SAVEPOINT savepoint_name;
  ROLLBACK TO SAVEPOINT savepoint_name;
  RELEASE SAVEPOINT savepoint_name;  -- removes the savepoint

ANALOGY: Multiple save slots in a video game!
         You can save your progress at different points and go back to any slot.

EXAMPLE:
  START TRANSACTION;
  
  INSERT INTO STUDENTS VALUES (101, 'Ravi', 'CS', 85);
  SAVEPOINT sp1;  ← CHECKPOINT 1 (Ravi is in)
  
  INSERT INTO STUDENTS VALUES (102, 'Priya', 'Math', 90);
  SAVEPOINT sp2;  ← CHECKPOINT 2 (Ravi + Priya are in)
  
  INSERT INTO STUDENTS VALUES (103, 'Wrong', 'Error', -5);  -- mistake!
  
  ROLLBACK TO SAVEPOINT sp2;  ← Go back to sp2 (undo only the wrong insert)
  -- Now ONLY Ravi and Priya are in; the wrong entry is undone.
  -- Ravi (sp1) is NOT affected!
  
  COMMIT;  ← Permanently save Ravi and Priya.

VISUAL:
  Start ──→ [Ravi inserted] ──(sp1)──→ [Priya inserted] ──(sp2)──→ [Wrong data] ──→ ROLLBACK TO sp2
                                                               ↑
                                                         Rolls back to here
                                                       (Wrong data removed,
                                                        Ravi + Priya kept)
```

---

## 🔷 SECTION 8: TCL — COMMIT vs ROLLBACK Comparison

```
┌──────────────────────┬────────────────────────────┬───────────────────────────┐
│       FEATURE        │          COMMIT             │         ROLLBACK          │
├──────────────────────┼────────────────────────────┼───────────────────────────┤
│ Purpose              │ Makes changes PERMANENT     │ UNDOES all changes since  │
│                      │                             │ last COMMIT or SAVEPOINT  │
├──────────────────────┼────────────────────────────┼───────────────────────────┤
│ After execution      │ Changes saved to disk,      │ Database returns to       │
│                      │ cannot be undone            │ previous state            │
├──────────────────────┼──────────────────────────  ┼───────────────────────────┤
│ Works on             │ DML, DDL (DDL auto-commits) │ DML only; NOT DDL or DCL  │
├──────────────────────┼────────────────────────────┼───────────────────────────┤
│ After COMMIT         │ ROLLBACK has no effect      │ N/A (too late)            │
├──────────────────────┼────────────────────────────┼───────────────────────────┤
│ Analogy              │ Ctrl+S (Save document)      │ Ctrl+Z (Undo)             │
└──────────────────────┴────────────────────────────┴───────────────────────────┘
```

---

## 🔷 SECTION 9: Important WHERE, GROUP BY, HAVING — Quick Reference

```
WHERE:    Filter rows BEFORE any grouping
          Used with: SELECT, UPDATE, DELETE
          Can reference any column
          Example: WHERE Marks > 80

GROUP BY: Group rows with same value in a column
          Used after WHERE, before HAVING
          Must use aggregate functions with GROUP BY
          Example: GROUP BY DeptID

HAVING:   Filter GROUPS after GROUP BY (like WHERE for groups)
          Cannot use HAVING without GROUP BY (usually)
          Example: HAVING COUNT(*) > 5

ORDER OF EXECUTION:
  FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
  
  Mentally: "Take data → Filter rows → Group → Filter groups → Display → Sort → Limit"

EXAMPLE combining all:
  SELECT DeptID, AVG(Marks) as AvgMarks, COUNT(*) as Students
  FROM STUDENTS
  WHERE DeptID != 'Admin'        ← Remove Admin dept rows first
  GROUP BY DeptID                ← Group remaining by dept
  HAVING AVG(Marks) > 75         ← Only depts with avg > 75
  ORDER BY AvgMarks DESC         ← Sort by avg marks
  LIMIT 3;                       ← Show top 3 only

🎯 PYQ: WHERE is used BEFORE GROUP BY; HAVING is used AFTER GROUP BY.
        Cannot use aggregate functions (AVG, COUNT) in WHERE clause!
```

---

## 🔷 SECTION 10: DDL Auto-Commit — The Most Critical PYQ Concept

```
AUTO-COMMIT RULE (THE GOLDEN PYQ RULE):

DDL Commands → AUTO-COMMITTED (automatically permanent, cannot rollback)
DCL Commands → AUTO-COMMITTED
DML Commands → NOT auto-committed (can rollback until COMMIT is called)

THIS IS THE MOST TESTED CONCEPT IN SQL!

SCENARIO 1: (DDL — cannot rollback)
  CREATE TABLE TEMP (id INT);       -- DDL auto-committed
  INSERT INTO TEMP VALUES (1);      -- DML: not yet committed
  TRUNCATE TABLE TEMP;              -- DDL: auto-committed → data GONE permanently
  ROLLBACK;                         -- This does NOTHING for TRUNCATE!
  SELECT * FROM TEMP;               -- Returns EMPTY TABLE (truncate wasn't undone)

SCENARIO 2: (DML — can rollback)
  INSERT INTO STUDENTS VALUES (999, 'Test', 'CS', 50);   -- DML
  DELETE FROM STUDENTS WHERE RollNo = 999;               -- DML
  ROLLBACK;                                              -- Both undone!
  SELECT * FROM STUDENTS WHERE RollNo = 999;             -- Returns row! (rollback restored it)

SCENARIO 3: (COMMIT blocks rollback)
  INSERT INTO STUDENTS VALUES (888, 'New', 'CS', 70);    -- DML
  COMMIT;                                                -- Permanently saved!
  ROLLBACK;                                              -- Too late! Can't undo committed data.
  SELECT * FROM STUDENTS WHERE RollNo = 888;             -- Row still exists.
```

---

## 🔷 SECTION 11: Complete SQL Command Summary Table

```
┌────────────┬──────────────┬────────────────────┬─────────────┬─────────────┐
│  CATEGORY  │   COMMAND    │      PURPOSE        │AUTO-COMMIT? │ROLLBACK-ABLE│
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ DDL        │ CREATE       │ Create new object   │    YES      │     NO      │
│            │ ALTER        │ Modify structure    │    YES      │     NO      │
│            │ DROP         │ Delete object       │    YES      │     NO      │
│            │ TRUNCATE     │ Empty table fast    │    YES      │     NO      │
│            │ RENAME       │ Rename object       │    YES      │     NO      │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ DML        │ SELECT       │ Read/query data     │    NO       │    YES      │
│            │ INSERT       │ Add new rows        │    NO       │    YES      │
│            │ UPDATE       │ Modify existing rows│    NO       │    YES      │
│            │ DELETE       │ Remove specific rows│    NO       │    YES      │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ DCL        │ GRANT        │ Give permissions    │    YES      │     NO      │
│            │ REVOKE       │ Remove permissions  │    YES      │     NO      │
├────────────┼──────────────┼────────────────────┼─────────────┼─────────────┤
│ TCL        │ COMMIT       │ Save permanently    │    N/A      │     NO      │
│            │ ROLLBACK     │ Undo changes        │    N/A      │     N/A     │
│            │ SAVEPOINT    │ Create checkpoint   │    N/A      │    YES      │
└────────────┴──────────────┴────────────────────┴─────────────┴─────────────┘
```

---

## 🔷 SECTION 12: PYQ Traps Summary

```
TRAP 1: "TRUNCATE is a DML command"
  → FALSE! TRUNCATE is DDL. DELETE is DML.

TRAP 2: "TRUNCATE can be rolled back"
  → FALSE! TRUNCATE is DDL → AUTO-COMMITTED → CANNOT be rolled back.
           DELETE can be rolled back (it's DML).

TRAP 3: "DELETE removes the table structure"
  → FALSE! DELETE removes ROWS only; table structure remains.
           DROP removes both structure AND data.

TRAP 4: "COMMIT undoes recent changes"
  → FALSE! COMMIT SAVES changes permanently. ROLLBACK undoes changes.

TRAP 5: "ROLLBACK can undo a COMMIT"
  → FALSE! Once COMMITted, changes are permanent. ROLLBACK cannot undo them.

TRAP 6: "SELECT is a DDL command"
  → FALSE! SELECT is DML (it manipulates/retrieves data).

TRAP 7: "HAVING can be used without GROUP BY"
  → Generally FALSE in standard SQL (HAVING works with GROUP BY).
           WHERE is used for row-level filtering without GROUP BY.

TRAP 8: "GRANT and REVOKE are DML commands"
  → FALSE! GRANT and REVOKE are DCL (Data Control Language).

TRAP 9: "WHERE and HAVING serve the same purpose"
  → FALSE! WHERE filters rows BEFORE grouping.
           HAVING filters groups AFTER GROUP BY.
           Aggregate functions (COUNT, AVG) can be used in HAVING, not WHERE.

TRAP 10: "ALTER TABLE deletes existing data in the table"
  → FALSE! ALTER modifies structure without deleting data.
           (Exception: DROP COLUMN removes column and its data)
```

---

# PART 2: GENERAL STUDIES
## 🌱 Biology — Photoperiodism

---

## 🔷 SECTION 1: What is Photoperiodism?

### Real-Life Observation:

Have you ever noticed that:
- Some flowers bloom in SUMMER (long days, short nights)?
- Some flowers bloom in WINTER (short days, long nights)?
- Some plants seem to flower at any time of year?

This is not random — plants MEASURE the length of day (or night) and use it as a signal for when to flower. This phenomenon is called **PHOTOPERIODISM**.

### Definition:
> **Photoperiodism is the response of plants to the RELATIVE LENGTH of day and night (photoperiod) — particularly the flowering response triggered by the duration of light and darkness in a 24-hour cycle.**

### Key Insight — It's Actually About DARKNESS, Not Light!
```
COMMON MISCONCEPTION: Plants respond to the LENGTH OF DAY (light period)
SCIENTIFIC TRUTH:     Plants actually measure the LENGTH OF NIGHT (dark period)!

The critical period is the DARK PERIOD (night length), not the light period.
This was discovered by Garner and Allard initially based on day length,
but later Hamner and Bonner (1938) showed the NIGHT LENGTH is critical.

However: For exam purposes (especially BPSC), the textbook answer is
         that plants respond to RELATIVE LENGTH OF DAY and NIGHT.
         
🎯 PYQ EXAM ANSWER: Photoperiodism = response to relative length of DAY AND NIGHT
```

---

## 🔷 SECTION 2: Discovery of Photoperiodism

### Garner and Allard — The Discoverers:

```
SCIENTISTS: W.W. GARNER and H.A. ALLARD
YEAR:       1920
INSTITUTION: U.S. Department of Agriculture (USDA), Maryland, USA

THE DISCOVERY STORY:

OBSERVATION 1: Maryland Mammoth Tobacco
  → W.W. Garner was growing tobacco plants
  → A special mutant variety called "MARYLAND MAMMOTH TOBACCO" grew 
    very tall (3-5 meters!) but REFUSED to flower during summer
  → This same plant FLOWERED in a greenhouse in WINTER!
  → WHY would it flower in winter but not summer?
  
OBSERVATION 2: Soybean (Biloxi variety)
  → H.A. Allard noticed that soybeans planted at DIFFERENT TIMES in the 
    growing season all flowered at the SAME TIME in late summer
  → Plants planted in May AND plants planted in July both flowered together!
  → This meant: flowering was NOT triggered by plant age, but by some 
    environmental signal that happened at the SAME TIME every year.

CONCLUSION (1920): Both scientists concluded that the RELATIVE LENGTH OF DAY 
AND NIGHT (the photoperiod) was the controlling factor for flowering!

KEY PUBLICATION: "Effect of the Relative Length of Day and Night and Other 
                  Factors of the Environment on Growth and Reproduction in Plants"
                  (1920)

🎯 PYQ FACT: GARNER and ALLARD discovered photoperiodism in 1920.
             Their experimental plants: Maryland Mammoth Tobacco + Biloxi Soybean.
```

---

## 🔷 SECTION 3: Types of Plants Based on Photoperiodism

### TYPE 1: SHORT-DAY PLANTS (SDP) — Winter Bloomers

```
DEFINITION: Plants that flower only when the DARK PERIOD (night) 
            is LONGER THAN a critical minimum.
            They need LONG NIGHTS to flower.
            
ALTERNATIVE NAME: Long-Night Plants (more scientifically accurate!)

IN SIMPLE TERMS: These plants flower when DAYS ARE SHORT (nights are long)
                 → They flower in AUTUMN and WINTER

REQUIREMENT:
  Day length: LESS THAN a critical daylength (typically < 12-14 hours)
  Night length: MORE THAN a critical minimum (typically > 10-12 hours)

EXAMPLES:
  ✅ Chrysanthemum (Guldaudi)  → flowers in autumn/winter
  ✅ Tobacco (Maryland Mammoth) → Garner & Allard's original plant!
  ✅ Poinsettia (Christmas flower) → blooms in December!
  ✅ Cocklebur (Xanthium) → classic lab experimental plant
  ✅ Strawberry → short-day plant
  ✅ Dahlia → flowers in autumn
  ✅ Hemp (Cannabis)
  ✅ Rice (many varieties) → some rice varieties are short-day plants

AGRICULTURAL IMPORTANCE:
  → Chrysanthemums grown commercially: farmers use BLACK PLASTIC SHEETS
    to artificially CREATE LONG NIGHTS → force flowering at any time of year
  → Poinsettias sold at Christmas: growers keep them in darkness for
    extended periods to ensure they're ready for the holiday season.
```

### TYPE 2: LONG-DAY PLANTS (LDP) — Summer Bloomers

```
DEFINITION: Plants that flower only when the LIGHT PERIOD (day) 
            is LONGER THAN a critical minimum.
            They need SHORT NIGHTS to flower.
            
ALTERNATIVE NAME: Short-Night Plants

IN SIMPLE TERMS: These plants flower when DAYS ARE LONG (nights are short)
                 → They flower in SPRING and SUMMER

REQUIREMENT:
  Day length: MORE THAN a critical daylength (typically > 14-16 hours)
  Night length: LESS THAN a critical minimum (typically < 10 hours)

EXAMPLES:
  ✅ Wheat
  ✅ Barley
  ✅ Oats
  ✅ Spinach
  ✅ Sugar beet
  ✅ Radish
  ✅ Lettuce
  ✅ Mustard (Brassica) → some varieties
  ✅ Carnation
  ✅ Iris
  ✅ Henbane (Hyoscyamus niger) — classic experimental plant

AGRICULTURAL IMPORTANCE:
  → Wheat is a long-day plant → needs long summer days to head and grain
  → Growing wheat in tropical regions (short days year-round) requires
    special varieties or artificial light extension
```

### TYPE 3: DAY-NEUTRAL PLANTS (DNP)

```
DEFINITION: Plants that CAN FLOWER regardless of the photoperiod.
            Their flowering is NOT triggered by day/night length.
            They use OTHER signals (temperature, age, etc.)
            
IN SIMPLE TERMS: These plants are "photoperiod blind" — they don't care
                 how long the day or night is.

EXAMPLES:
  ✅ Tomato       → flowers whenever conditions are right
  ✅ Cucumber     → day-neutral
  ✅ Cotton       → day-neutral
  ✅ Rose         → can flower throughout the year
  ✅ Sunflower    → day-neutral (some varieties)
  ✅ Maize/Corn   → most varieties are day-neutral
  ✅ Snapdragon

NOTE: Maize is often listed as day-neutral in modern cultivars, but
      traditional varieties may show some day-length sensitivity.
```

---

## 🔷 SECTION 4: The Critical Night Length — Most Important Concept

```
THE CRITICAL NIGHT (OR CRITICAL DARK PERIOD):

Each short-day and long-day plant has a CRITICAL NIGHT LENGTH:
  → SDP: must receive a dark period LONGER than its critical night to flower
  → LDP: must receive a dark period SHORTER than its critical night to flower

EXAMPLE:
  Cocklebur (SDP): Critical night = 8.5 hours
    → Night longer than 8.5 hours → FLOWERS ✓
    → Night shorter than 8.5 hours → NO FLOWERING ✗

THE NIGHT INTERRUPTION EXPERIMENT (Hamner & Bonner, 1938):
  A short-day plant in long-night conditions (should flower):
  → Give it a BRIEF FLASH OF LIGHT in the middle of the night
  → This INTERRUPTS the continuous dark period
  → The plant thinks it has TWO SHORT NIGHTS instead of one long night
  → Result: DOES NOT FLOWER!
  
  This PROVED that it's the NIGHT LENGTH (not day length) that matters!
  
  Short-Day Plant Flowering = Requires CONTINUOUS long dark period
  Even a BRIEF LIGHT FLASH in the middle of the night STOPS flowering!

┌──────────────────────────────────────────────────────────────────┐
│              NIGHT INTERRUPTION DIAGRAM                           │
├──────────────────────────────────────────────────────────────────┤
│                                                                   │
│ SDP in LONG NIGHT (flowers normally):                            │
│ ████ LIGHT ████ | ░░░░░░░░░░░ DARKNESS (LONG) ░░░░░░░░░░ = 🌸  │
│                                                                   │
│ SDP in LONG NIGHT with light interruption (blocked):             │
│ ████ LIGHT ████ | ░░░░░ DARK ░░░░ FLASH ░░░░░ DARK ░░░░ = 🚫  │
│                            ↑                                      │
│                    Brief light flash blocks flowering             │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 5: The Role of Phytochrome

```
HOW DO PLANTS "MEASURE" LIGHT?

The light-sensing pigment in plants is called PHYTOCHROME.

PHYTOCHROME exists in two forms:
  Pr (Phytochrome Red) → absorbs RED light (660 nm) → converts to Pfr
  Pfr (Phytochrome Far-Red) → absorbs FAR-RED light (730 nm) → converts to Pr

DURING DAYTIME (light present):
  Pr → (red light) → Pfr (active form accumulates)
  
DURING NIGHTTIME (darkness):
  Pfr slowly converts BACK to Pr
  
AFTER LONG NIGHT:
  Most Pfr → Pr
  High Pr = "signal" for SDP that night was long enough → FLOWER!
  
AFTER SHORT NIGHT:
  Some Pfr remains (not enough conversion time)
  High Pfr = signal for LDP that night was short → LDP flowers!

FOR EXAM: Remember:
  Phytochrome = light-sensing pigment in plants
  Controls photoperiodism and seed germination
  Two forms: Pr and Pfr (interconvertible)

🎯 PYQ: PHYTOCHROME is the photoreceptor that detects light changes for photoperiodism.
```

---

## 🔷 SECTION 6: Florigen — The Flowering Hormone

```
THE FLORIGEN CONCEPT:
  When a plant detects the right photoperiod, the LEAF produces a signal
  that travels to the SHOOT APEX (growing tip) and triggers FLOWERING.
  
  This hypothetical "flowering hormone" is called FLORIGEN.

HISTORY:
  → MIKHAIL CHAILAKHYAN (1937): Soviet scientist who proposed Florigen
  → He grafted photoperiod-induced leaves onto non-induced plants
    → The non-induced plants ALSO flowered!
  → Conclusion: a transmissible chemical (florigen) moves from leaves to buds

MODERN UNDERSTANDING:
  → "Florigen" is now identified as the protein FT (FLOWERING LOCUS T)
  → Produced in leaves → travels via phloem → reaches shoot apex → flower initiation
  
FOR EXAM: Florigen = Flowering Hormone, proposed by Chailakhyan (1937)

🎯 PYQ: FLORIGEN = hypothetical flowering hormone proposed by CHAILAKHYAN
```

---

## 🔷 SECTION 7: Photoperiodism Summary Table

```
┌───────────────────┬────────────────────┬────────────────────┬─────────────────┐
│   PLANT TYPE      │ CONDITION TO FLOWER│   EXAMPLES         │  SEASON         │
├───────────────────┼────────────────────┼────────────────────┼─────────────────┤
│ SHORT-DAY PLANT   │ Night > Critical   │ Chrysanthemum,     │ Autumn/Winter   │
│ (SDP)             │ length             │ Tobacco, Poinsettia│                 │
│ (=Long-Night Plant│ Short day needed   │ Cocklebur, Dahlia, │                 │
│                   │                    │ Rice (some vars)   │                 │
├───────────────────┼────────────────────┼────────────────────┼─────────────────┤
│ LONG-DAY PLANT    │ Day > Critical     │ Wheat, Barley,     │ Spring/Summer   │
│ (LDP)             │ length             │ Spinach, Sugar beet│                 │
│ (=Short-Night     │ Long day needed    │ Oats, Radish,      │                 │
│ Plant)            │                    │ Henbane, Mustard   │                 │
├───────────────────┼────────────────────┼────────────────────┼─────────────────┤
│ DAY-NEUTRAL       │ Not affected by    │ Tomato, Cotton,    │ Year-round      │
│ PLANT (DNP)       │ photoperiod        │ Cucumber, Rose,    │ (whenever other │
│                   │                    │ Sunflower, Corn    │ conditions met) │
└───────────────────┴────────────────────┴────────────────────┴─────────────────┘
```

---

## 🔷 SECTION 8: Agricultural Importance of Photoperiodism

```
1. CROP PLANNING:
   Farmers must choose crop varieties appropriate for their latitude/season.
   Short-day rice varieties: plant in summer to flower in short-day autumn.
   Long-day wheat: plant in winter/spring so long summer days trigger flowering.

2. ARTIFICIAL MANIPULATION OF FLOWERING:
   Commercial horticulture uses light control:
   → EXTENDING LIGHT (using artificial lights at night): Makes short-day 
     conditions into long-day → Long-day plants flower even in winter.
   → INTERRUPTING NIGHT (brief flash): Prevents short-day plants from flowering
     when growers want vegetative growth (e.g., spinach kept vegetative by night break).
   → BLACK SHEATHING (shading): Creates artificial long nights → short-day 
     plants like chrysanthemums can be made to flower year-round.

3. INTRODUCTION OF CROPS TO NEW REGIONS:
   When moving crops to new latitudes, photoperiod response must be considered.
   A short-day rice variety from tropical India (10-12 hrs day) cannot flower
   well in temperate regions (16+ hrs day in summer) → needs different variety.

4. VERNALIZATION CONNECTION:
   Some plants need both correct photoperiod AND cold temperature (vernalization)
   to flower. Wheat (winter wheat) needs cold + long days.
```

---

## 🔷 SECTION 9: Key PYQ Facts for Biology

```
🎯 PHOTOPERIODISM = response to relative length of day and night
🎯 DISCOVERED BY = W.W. GARNER and H.A. ALLARD (1920), USDA, USA
🎯 Experimental plants: Maryland Mammoth TOBACCO + Biloxi SOYBEAN
🎯 SHORT-DAY PLANT = needs LONG NIGHTS (flowers in autumn/winter)
   Examples: Chrysanthemum, Tobacco, Poinsettia, Cocklebur, Dahlia
🎯 LONG-DAY PLANT = needs SHORT NIGHTS / LONG DAYS (flowers in summer)
   Examples: Wheat, Barley, Oats, Spinach, Sugar beet, Henbane
🎯 DAY-NEUTRAL PLANT = not affected by photoperiod
   Examples: Tomato, Cotton, Rose, Cucumber, Sunflower
🎯 PHYTOCHROME = light-sensing pigment; two forms: Pr and Pfr
🎯 FLORIGEN = hypothetical flowering hormone; proposed by CHAILAKHYAN (1937)
🎯 NIGHT INTERRUPTION = brief flash of light at night stops SDP flowering
🎯 SDP is more accurately called "Long-Night Plant" (night length controls it)
🎯 CRITICAL NIGHT PERIOD = minimum dark period for SDP; cocklebur = 8.5 hrs
🎯 RICE: most tropical varieties are short-day plants
🎯 WHEAT: long-day plant (requires long days for grain formation)
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: SQL Commands, DDL/DML/DCL/TCL, DELETE vs TRUNCATE, Transactions

---

**Q1.** SQL stands for:
(A) Sequential Query Language
(B) Structured Query Language
(C) Simple Query Language
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is a DDL (Data Definition Language) command?
(A) SELECT
(B) INSERT
(C) CREATE
(D) More than one of the above
(E) None of the above

---

**Q3.** Which SQL command is used to ADD a new column to an existing table?
(A) CREATE TABLE
(B) MODIFY TABLE
(C) ALTER TABLE ... ADD column_name datatype
(D) More than one of the above
(E) None of the above

---

**Q4.** TRUNCATE TABLE command:
(A) Deletes the table and all its structure permanently
(B) Removes all rows quickly but keeps the table structure; cannot be rolled back
(C) Is a DML command that can be undone with ROLLBACK
(D) More than one of the above
(E) None of the above

---

**Q5.** Which of the following SQL commands CANNOT be rolled back using ROLLBACK?
(A) DELETE FROM STUDENTS WHERE RollNo = 101
(B) INSERT INTO STUDENTS VALUES (102, 'Priya', 'CS', 90)
(C) TRUNCATE TABLE STUDENTS
(D) More than one of the above
(E) None of the above

---

**Q6.** The PRIMARY difference between DELETE and TRUNCATE is:
(A) DELETE removes both data and structure; TRUNCATE removes only data
(B) DELETE is DML (can rollback, uses WHERE); TRUNCATE is DDL (auto-committed, no WHERE, faster)
(C) TRUNCATE can filter rows using WHERE; DELETE cannot
(D) More than one of the above
(E) None of the above

---

**Q7.** Which SQL clause is used to filter rows BEFORE grouping?
(A) HAVING
(B) ORDER BY
(C) WHERE
(D) More than one of the above
(E) None of the above

---

**Q8.** Which SQL clause is used to filter GROUPS (after GROUP BY)?
(A) WHERE
(B) HAVING
(C) DISTINCT
(D) More than one of the above
(E) None of the above

---

**Q9.** The COMMIT command in SQL:
(A) Undoes all recent changes made in the current transaction
(B) Creates a checkpoint within a transaction for partial rollback
(C) Permanently saves all changes made in the current transaction; cannot be undone by ROLLBACK
(D) More than one of the above
(E) None of the above

---

**Q10.** What does ROLLBACK TO SAVEPOINT sp1 do?
(A) Permanently saves changes up to sp1
(B) Undoes all changes made AFTER savepoint sp1 was created, restoring the state at sp1
(C) Deletes the savepoint sp1 and commits everything before it
(D) More than one of the above
(E) None of the above

---

**Q11.** GRANT and REVOKE commands belong to which SQL category?
(A) DDL (Data Definition Language)
(B) DML (Data Manipulation Language)
(C) DCL (Data Control Language)
(D) More than one of the above
(E) None of the above

---

**Q12.** Which SQL command permanently removes an ENTIRE TABLE including its structure and all data?
(A) DELETE FROM table_name (removes rows, keeps structure)
(B) TRUNCATE TABLE table_name (removes rows, keeps structure)
(C) DROP TABLE table_name (removes BOTH structure and data permanently)
(D) More than one of the above
(E) None of the above

---

**Q13.** In SQL, SELECT * FROM STUDENTS WHERE Marks > 80 ORDER BY Marks DESC; will:
(A) Show students with marks > 80, sorted from lowest to highest
(B) Show all students sorted by marks with those > 80 highlighted
(C) Show only students with marks greater than 80, sorted from highest to lowest marks
(D) More than one of the above
(E) None of the above

---

**Q14.** After executing COMMIT, a ROLLBACK command:
(A) Undoes all committed changes
(B) Has NO EFFECT — committed changes are permanent and cannot be undone
(C) Creates a new savepoint at the commit point
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following SQL statements uses an AGGREGATE function correctly?
(A) SELECT * FROM STUDENTS WHERE AVG(Marks) > 80; (aggregate in WHERE)
(B) SELECT DeptID, AVG(Marks) FROM STUDENTS GROUP BY DeptID HAVING AVG(Marks) > 80;
(C) SELECT DeptID FROM STUDENTS GROUP BY DeptID ORDER BY COUNT(*);
(D) More than one of the above
(E) None of the above

---

**Q16.** DDL commands are described as "AUTO-COMMITTED." This means:
(A) They run automatically every hour
(B) Their effects are immediately and permanently saved — they cannot be undone by ROLLBACK
(C) They commit only when the session ends
(D) More than one of the above
(E) None of the above

---

**Q17.** Which command gives USER "Ravi" permission to only READ data from the STUDENTS table?
(A) GRANT ALL ON STUDENTS TO ravi;
(B) GRANT SELECT ON STUDENTS TO ravi;
(C) REVOKE INSERT ON STUDENTS FROM ravi;
(D) More than one of the above
(E) None of the above

---

**Q18.** UPDATE STUDENTS SET Marks = 100; (without WHERE clause) will:
(A) Update only the first student's marks to 100
(B) Give a syntax error — WHERE is mandatory in UPDATE
(C) Update ALL students' marks to 100
(D) More than one of the above
(E) None of the above

---

**Q19.** ACID properties of a transaction include:
(A) Atomicity, Consistency, Isolation, Durability
(B) Accuracy, Consistency, Independence, Data integrity
(C) Atomicity, Compression, Isolation, Durability
(D) More than one of the above
(E) None of the above

---

**Q20.** Which SQL command is used to REMOVE permissions that were previously granted?
(A) DELETE permissions
(B) DROP USER
(C) REVOKE
(D) More than one of the above
(E) None of the above

---

**Q21.** The correct execution order of SQL clauses is:
(A) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
(B) FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY
(C) WHERE → FROM → SELECT → GROUP BY → HAVING → ORDER BY
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following is a DML (Data Manipulation Language) command?
(A) CREATE
(B) TRUNCATE
(C) DELETE
(D) More than one of the above
(E) None of the above

---

**Q23.** SAVEPOINT in SQL is used for:
(A) Permanently saving data at regular intervals automatically
(B) Creating named checkpoints within a transaction, allowing partial rollback to that point
(C) Saving the database schema before any DDL operations
(D) More than one of the above
(E) None of the above

---

**Q24.** A bank transfer debits Account A and credits Account B. If the debit succeeds but the credit fails (due to system crash), ACID's "ATOMICITY" ensures:
(A) Both operations are marked as successful regardless
(B) Only the successful debit is kept; the credit is retried later
(C) Both operations are undone — the debit is reversed, restoring the original state
(D) More than one of the above
(E) None of the above

---

**Q25.** Which statement about TRUNCATE is INCORRECT?
(A) TRUNCATE removes all rows from a table
(B) TRUNCATE keeps the table structure intact
(C) TRUNCATE can use a WHERE clause to remove specific rows
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Photoperiodism, Garner & Allard, Plant Types, Phytochrome, Florigen

---

**Q26.** Photoperiodism in plants was discovered by:
(A) Gregor Mendel and Charles Darwin
(B) W.W. Garner and H.A. Allard (1920)
(C) Mikhail Chailakhyan and Hamner
(D) More than one of the above
(E) None of the above

---

**Q27.** Photoperiodism is defined as the response of plants to:
(A) Total amount of sunlight energy received
(B) The relative length of day and night (photoperiod)
(C) The temperature changes in the environment
(D) More than one of the above
(E) None of the above

---

**Q28.** The experimental plants used by Garner and Allard to discover photoperiodism were:
(A) Wheat and Barley
(B) Maryland Mammoth Tobacco and Biloxi Soybean
(C) Chrysanthemum and Poinsettia
(D) More than one of the above
(E) None of the above

---

**Q29.** SHORT-DAY PLANTS (SDP) flower when:
(A) The day length is longer than a critical minimum
(B) The night length is longer than a critical minimum (they need long nights)
(C) Temperature drops below a certain level
(D) More than one of the above
(E) None of the above

---

**Q30.** Which of the following is a SHORT-DAY PLANT?
(A) Wheat
(B) Spinach
(C) Chrysanthemum
(D) More than one of the above
(E) None of the above

---

**Q31.** LONG-DAY PLANTS (LDP) require:
(A) More than a critical length of DARK period to flower
(B) More than a critical length of LIGHT period (day) / shorter nights to flower
(C) Exposure to cold temperatures for a prolonged period before flowering
(D) More than one of the above
(E) None of the above

---

**Q32.** Which of the following is a LONG-DAY PLANT?
(A) Chrysanthemum
(B) Poinsettia
(C) Spinach
(D) More than one of the above
(E) None of the above

---

**Q33.** DAY-NEUTRAL PLANTS are characterised by:
(A) Flowering only during the equinox when day and night are equal
(B) Ability to flower regardless of photoperiod (not sensitive to day/night length)
(C) Flowering only when day length exceeds 16 hours
(D) More than one of the above
(E) None of the above

---

**Q34.** Which of the following is a DAY-NEUTRAL PLANT?
(A) Cocklebur
(B) Henbane
(C) Tomato
(D) More than one of the above
(E) None of the above

---

**Q35.** Night interruption experiment (giving a brief light flash in the middle of a long night) to a SHORT-DAY PLANT will:
(A) Stimulate flowering because more light = more energy for the plant
(B) PREVENT flowering because the continuous dark period is broken (plant "thinks" night is short)
(C) Have no effect because the total darkness hours remain roughly the same
(D) More than one of the above
(E) None of the above

---

**Q36.** The light-sensing pigment in plants responsible for detecting photoperiod changes is:
(A) Chlorophyll
(B) Carotenoid
(C) Phytochrome
(D) More than one of the above
(E) None of the above

---

**Q37.** Phytochrome exists in two interconvertible forms. These are:
(A) Pr (absorbs red light) and Pfr (absorbs far-red light)
(B) Chlorophyll-a and Chlorophyll-b
(C) Carotene and Xanthophyll
(D) More than one of the above
(E) None of the above

---

**Q38.** "FLORIGEN" in the context of plant physiology refers to:
(A) A growth inhibiting hormone found in roots
(B) A hypothetical flowering hormone that transmits the flowering signal from leaves to buds
(C) The pigment responsible for red colour in flowers
(D) More than one of the above
(E) None of the above

---

**Q39.** The concept of Florigen (flowering hormone) was proposed by:
(A) W.W. Garner
(B) M.K. Chailakhyan (1937)
(C) Hamner and Bonner
(D) More than one of the above
(E) None of the above

---

**Q40.** POINSETTIA (the Christmas flower sold in December) is a short-day plant. Horticulturists ensure it flowers in time for Christmas by:
(A) Keeping it in bright lights for 16 hours a day throughout autumn
(B) Covering it with black cloth/shades to create artificially long nights (extending dark period)
(C) Exposing it to cold temperatures (vernalization)
(D) More than one of the above
(E) None of the above

---

**Q41.** RICE is generally classified as:
(A) Long-day plant (requires long summer days to flower)
(B) Day-neutral plant (photoperiod has no effect)
(C) Short-day plant (many tropical rice varieties need short days/long nights to flower)
(D) More than one of the above
(E) None of the above

---

**Q42.** WHEAT is classified as:
(A) Short-day plant
(B) Long-day plant (requires long days for grain formation and heading)
(C) Day-neutral plant
(D) More than one of the above
(E) None of the above

---

**Q43.** In which organ of the plant is the photoperiod perceived (detected)?
(A) Roots
(B) Stem (shoot apex)
(C) Leaves (where phytochrome is located and the signal is generated)
(D) More than one of the above
(E) None of the above

---

**Q44.** Short-day plants are more accurately described as "Long-Night Plants" because:
(A) They grow taller at night
(B) Scientific evidence shows it is the LENGTH OF THE DARK PERIOD (night), not the day length, that controls flowering
(C) They only absorb nutrients during nighttime
(D) More than one of the above
(E) None of the above

---

**Q45.** Garner and Allard's discovery of photoperiodism was made at:
(A) Cambridge University, England
(B) Indian Agricultural Research Institute (IARI), New Delhi
(C) U.S. Department of Agriculture (USDA), Maryland, USA
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following pairs is CORRECTLY matched?
(A) Chrysanthemum — Long-day plant
(B) Spinach — Short-day plant
(C) Cocklebur (Xanthium) — Short-day plant (classic experimental SDP)
(D) More than one of the above
(E) None of the above

---

**Q47.** If a florist wants chrysanthemums (a short-day plant) to bloom year-round (even in summer), they should:
(A) Expose them to 16+ hours of bright light daily
(B) Use black plastic covers to create artificially long dark periods (simulating winter nights)
(C) Reduce watering to trigger stress-induced flowering
(D) More than one of the above
(E) None of the above

---

**Q48.** The CRITICAL DARK PERIOD for flowering in cocklebur (a SDP) is approximately:
(A) 2 hours
(B) 8.5 hours (uninterrupted dark period needed)
(C) 16 hours
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following correctly represents the CATEGORIES of plants based on photoperiodism?
(A) Photosynthetic plants, Non-photosynthetic plants, Semi-photosynthetic plants
(B) Short-day plants, Long-day plants, Day-neutral plants
(C) Tropical plants, Temperate plants, Alpine plants
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following statements:
I.   Garner and Allard discovered photoperiodism in 1920 using tobacco and soybean.
II.  Short-day plants need night length LONGER than a critical minimum to flower.
III. Phytochrome is the light-sensing pigment that mediates photoperiodic response.
IV.  Florigen is the hypothetical flowering hormone proposed by Chailakhyan in 1937.

How many of the above statements are CORRECT?
(A) Only I and II
(B) Only II and III
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
| 1 | (B) | SQL = Structured Query Language |
| 2 | (C) | CREATE is DDL; SELECT and INSERT are DML |
| 3 | (C) | ALTER TABLE ... ADD is used to add a new column to existing table |
| 4 | (B) | TRUNCATE = DDL; removes all rows fast; keeps structure; CANNOT rollback |
| 5 | (C) | TRUNCATE is DDL (auto-committed); DELETE and INSERT are DML (can rollback) |
| 6 | (B) | DELETE = DML (rollback-able, WHERE allowed); TRUNCATE = DDL (auto-committed, faster, no WHERE) |
| 7 | (C) | WHERE filters rows BEFORE grouping |
| 8 | (B) | HAVING filters groups AFTER GROUP BY |
| 9 | (C) | COMMIT = permanently saves changes; cannot be undone by ROLLBACK |
| 10 | (B) | ROLLBACK TO SAVEPOINT undoes only changes AFTER that savepoint |
| 11 | (C) | GRANT and REVOKE are DCL (Data Control Language) |
| 12 | (C) | DROP TABLE removes BOTH structure and data permanently |
| 13 | (C) | WHERE Marks > 80 filters; ORDER BY Marks DESC sorts highest first |
| 14 | (B) | After COMMIT, ROLLBACK has no effect — changes are permanent |
| 15 | (B) | HAVING AVG(Marks) > 80 is correct; AVG in WHERE clause is invalid |
| 16 | (B) | Auto-committed = immediately permanent; cannot be undone by ROLLBACK |
| 17 | (B) | GRANT SELECT gives only read permission |
| 18 | (C) | UPDATE without WHERE affects ALL rows |
| 19 | (A) | ACID = Atomicity, Consistency, Isolation, Durability |
| 20 | (C) | REVOKE removes previously granted permissions |
| 21 | (B) | Execution order: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY |
| 22 | (C) | DELETE is DML; CREATE and TRUNCATE are DDL |
| 23 | (B) | SAVEPOINT creates checkpoint within transaction for partial rollback |
| 24 | (C) | Atomicity = all or nothing; if credit fails, debit also reversed |
| 25 | (C) | Statement C is INCORRECT: TRUNCATE has NO WHERE clause — it removes ALL rows |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Garner and Allard (1920) — USDA, USA |
| 27 | (B) | Photoperiodism = response to relative length of day AND night |
| 28 | (B) | Maryland Mammoth Tobacco + Biloxi Soybean = their experimental plants |
| 29 | (B) | SDP needs LONG NIGHTS (night > critical length) to flower |
| 30 | (C) | Chrysanthemum = classic short-day plant |
| 31 | (B) | LDP requires more than critical day length (long days, short nights) |
| 32 | (C) | Spinach = long-day plant |
| 33 | (B) | Day-neutral = not sensitive to photoperiod; flowers regardless |
| 34 | (C) | Tomato = day-neutral plant |
| 35 | (B) | Night interruption PREVENTS SDP flowering (breaks continuous dark period) |
| 36 | (C) | Phytochrome = light-sensing pigment for photoperiodism |
| 37 | (A) | Pr (absorbs red 660nm) and Pfr (absorbs far-red 730nm) |
| 38 | (B) | Florigen = hypothetical flowering hormone transmits signal leaf→bud |
| 39 | (B) | Chailakhyan (1937) proposed florigen concept |
| 40 | (B) | Black cloth creates artificial long nights → SDP poinsettia flowers |
| 41 | (C) | Rice = short-day plant (many tropical varieties need long nights) |
| 42 | (B) | Wheat = long-day plant |
| 43 | (C) | Leaves detect photoperiod (phytochrome in leaves) |
| 44 | (B) | It's the dark period (night) length that actually controls flowering |
| 45 | (C) | USDA Maryland USA — not UK or India |
| 46 | (C) | Cocklebur (Xanthium) = classic short-day plant experimental specimen |
| 47 | (B) | Black covers create artificial long nights → year-round flowering |
| 48 | (B) | Cocklebur critical dark period ≈ 8.5 hours |
| 49 | (B) | Three categories: SDP, LDP, DNP |
| 50 | (C) | All four statements I, II, III, IV are correct |

---
---

# 🔁 DAY 40 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — SQL Commands

### The Four Categories — One Line Each:
```
DDL = Define STRUCTURE: CREATE, ALTER, DROP, TRUNCATE, RENAME
DML = Work with DATA:   SELECT, INSERT, UPDATE, DELETE
DCL = Control ACCESS:   GRANT, REVOKE
TCL = Manage TRANSACTIONS: COMMIT, ROLLBACK, SAVEPOINT

MEMORY: "DDL Makes Structure; DML Handles Data; DCL Decides Access; TCL Tracks Transactions"
```

### The #1 PYQ Fact — Auto-Commit:
```
DDL commands = AUTO-COMMITTED = CANNOT be rolled back
DML commands = NOT auto-committed = CAN be rolled back (until COMMIT)
DCL commands = AUTO-COMMITTED

SO:
  DROP    → auto-committed → CANNOT rollback
  TRUNCATE → auto-committed → CANNOT rollback (most tested!)
  CREATE  → auto-committed → CANNOT rollback
  DELETE  → can rollback ✓
  INSERT  → can rollback ✓
  UPDATE  → can rollback ✓
```

### DELETE vs TRUNCATE — 3 Key Differences:
```
1. CATEGORY: DELETE = DML (rollback-able); TRUNCATE = DDL (not rollback-able)
2. WHERE:    DELETE = can filter rows; TRUNCATE = no WHERE clause
3. SPEED:    TRUNCATE = faster (bulk page deallocation); DELETE = slower (logs each row)
Both keep table STRUCTURE; only DROP removes structure.
```

### TCL Commands:
```
COMMIT    = Save permanently (no undo after this)
ROLLBACK  = Undo to last COMMIT (or SAVEPOINT)
SAVEPOINT = Create checkpoint; ROLLBACK TO SAVEPOINT = partial undo
```

### WHERE vs HAVING:
```
WHERE  = Before GROUP BY; filters individual ROWS; NO aggregate functions
HAVING = After GROUP BY; filters GROUPS; aggregate functions ALLOWED
```

---

## ⚡ RAPID FIRE — Photoperiodism

### Key Flash Cards:
```
PHOTOPERIODISM = Plant response to relative length of day and night
DISCOVERED BY  = W.W. GARNER + H.A. ALLARD (1920), USDA, USA
EXPERIMENTAL PLANTS = Maryland Mammoth TOBACCO + Biloxi SOYBEAN

SHORT-DAY PLANT (SDP):
  → Needs LONG NIGHT (night > critical length)
  → Flowers in AUTUMN/WINTER
  → Examples: Chrysanthemum, Tobacco, Poinsettia, Cocklebur, Dahlia, Rice

LONG-DAY PLANT (LDP):
  → Needs SHORT NIGHT / LONG DAY (day > critical length)
  → Flowers in SPRING/SUMMER
  → Examples: Wheat, Barley, Oats, Spinach, Sugar beet, Henbane

DAY-NEUTRAL PLANT (DNP):
  → NOT affected by photoperiod
  → Examples: Tomato, Cotton, Rose, Cucumber, Sunflower

PHYTOCHROME = Light-sensing pigment; two forms: Pr (red) and Pfr (far-red)
FLORIGEN    = Hypothetical flowering hormone; proposed by CHAILAKHYAN (1937)
```

### Night Interruption Rule:
```
Give a SHORT LIGHT FLASH in the middle of long night to a SDP:
→ PREVENTS FLOWERING (breaks the required continuous dark period)
→ This PROVED that NIGHT LENGTH (not day length) is the actual signal
```

### Memory Tricks:
```
SHORT-Day Plant = LONG Night = flowers in SHORT days of winter
  "SHORT Day = LONG Night = AUTUMN flowers" (Chrysanthemum, Poinsettia)

LONG-Day Plant = SHORT Night = flowers when DAYS ARE LONG = SUMMER
  "LONG Day = SHORT Night = SUMMER flowers" (Wheat, Spinach)
  
"Rice is SDP — needs Long Night like it needs a long soak in water!"
"Wheat grows TALL in LONG summer days — it's LDP!"
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **SQL categories**: DDL (CREATE, ALTER, DROP, TRUNCATE) = structure; DML (SELECT, INSERT, UPDATE, DELETE) = data; DCL (GRANT, REVOKE) = access; TCL (COMMIT, ROLLBACK, SAVEPOINT) = transactions.
2. **Critical auto-commit rule**: DDL and DCL = AUTO-COMMITTED = CANNOT rollback; DML = can rollback; TRUNCATE is DDL → CANNOT rollback (most tested PYQ!).
3. **DELETE vs TRUNCATE**: DELETE = DML, can rollback, uses WHERE, slower; TRUNCATE = DDL, cannot rollback, no WHERE, faster, resets auto-increment.
4. **Photoperiodism**: Garner & Allard (1920), USDA; SDP = long night needed (Chrysanthemum, Tobacco, Rice); LDP = long day needed (Wheat, Spinach); DNP = not affected (Tomato, Cotton).
5. **Phytochrome & Florigen**: Phytochrome (Pr/Pfr) = light sensor in leaves; Florigen = flowering hormone proposed by Chailakhyan (1937); Night interruption breaks SDP flowering.

---

## 📅 DAY 41 PREVIEW — What's Coming Next:
**CS**: SQL Joins — INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, CROSS JOIN, SELF JOIN; JOIN with conditions; Subqueries (basic); SQL functions (UPPER, LOWER, LENGTH, ROUND, NOW)
**GS**: Indian Polity — Fundamental Rights (Articles 12-35): Right to Equality (14-18), Right to Freedom (19-22), Right Against Exploitation (23-24), Right to Freedom of Religion (25-28), Cultural & Educational Rights (29-30), Right to Constitutional Remedies (Article 32 — Dr. Ambedkar called it the "Heart and Soul" of the Constitution)

---

*🚀 Day 40 of 170 — You're 23.5% through! SQL is a goldmine of MCQ marks in BPSC TRE CS paper. Master the command categories and the TRUNCATE-cannot-rollback trap — these appear almost every year!*
