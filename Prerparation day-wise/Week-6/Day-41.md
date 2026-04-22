# 📅 BPSC TRE 4.0 — DAY 41 COMPLETE STUDY MODULE
### SQL SELECT Queries, Clauses & Functions + Immunity & Lymphocytes (Biology)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): SQL SELECT — Basic to Advanced Queries, All Clauses, Aggregate Functions
> - Afternoon (1 hr): Biology — Immunity, Innate vs Acquired, B-cells, T-cells
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 SQL SELECT Queries, Clauses & Functions — Deep Conceptual Guide

---

## 🔷 SECTION 1: The Working Table — Our Reference

All SQL examples in this module use the following tables:

```
STUDENTS TABLE:
┌────────┬──────────────┬────────┬──────────┬────────┬─────────────┐
│ RollNo │    Name      │ DeptID │  City    │ Marks  │   Email     │
├────────┼──────────────┼────────┼──────────┼────────┼─────────────┤
│  101   │  Ravi Kumar  │  CS    │  Patna   │   85   │ r@mail.com  │
│  102   │  Priya Singh │  Math  │  Delhi   │   92   │ p@mail.com  │
│  103   │  Aman Gupta  │  CS    │  Patna   │   78   │ a@mail.com  │
│  104   │  Kavya Verma │  Phys  │  Mumbai  │   91   │ k@mail.com  │
│  105   │  Rohit Jha   │  Math  │  Patna   │   65   │ ro@mail.com │
│  106   │  Sita Devi   │  CS    │  Delhi   │   88   │ s@mail.com  │
│  107   │  Mohan Lal   │  Phys  │  Mumbai  │   72   │ m@mail.com  │
│  108   │  Nita Patel  │  CS    │  Patna   │   95   │ n@mail.com  │
└────────┴──────────────┴────────┴──────────┴────────┴─────────────┘

DEPARTMENTS TABLE:
┌────────┬──────────────────┬──────────────┐
│ DeptID │   DeptName       │    HOD       │
├────────┼──────────────────┼──────────────┤
│  CS    │ Computer Science │  Dr. Rao     │
│  Math  │  Mathematics     │  Dr. Jha     │
│  Phys  │  Physics         │  Dr. Gupta   │
│  Bio   │  Biology         │  Dr. Sharma  │
└────────┴──────────────────┴──────────────┘
```

---

## 🔷 SECTION 2: Basic SELECT Syntax

### The SELECT Statement Structure:

```
COMPLETE SYNTAX:
  SELECT  [DISTINCT] column1, column2, ...
  FROM    table_name
  WHERE   condition
  GROUP BY column_name
  HAVING  group_condition
  ORDER BY column_name [ASC|DESC]
  LIMIT   n;

EXECUTION ORDER (How SQL actually processes):
  Step 1: FROM    → Identify source table
  Step 2: WHERE   → Filter individual rows
  Step 3: GROUP BY → Group the filtered rows
  Step 4: HAVING  → Filter groups
  Step 5: SELECT  → Choose which columns to display
  Step 6: DISTINCT → Remove duplicate rows from result
  Step 7: ORDER BY → Sort the result
  Step 8: LIMIT   → Restrict number of rows shown

⚠️ KEY INSIGHT: The ORDER we WRITE the query ≠ ORDER SQL EXECUTES it!
   We write: SELECT...FROM...WHERE...GROUP BY...HAVING...ORDER BY
   SQL runs:  FROM→WHERE→GROUP BY→HAVING→SELECT→ORDER BY
```

### Example 1 — Select All Columns:
```sql
SELECT * FROM STUDENTS;
-- Returns ALL rows, ALL columns
-- * means "all columns"
-- Most basic query possible
```

### Example 2 — Select Specific Columns:
```sql
SELECT RollNo, Name, Marks FROM STUDENTS;
-- Returns only the 3 specified columns for all rows

Result:
┌────────┬──────────────┬────────┐
│ RollNo │    Name      │ Marks  │
├────────┼──────────────┼────────┤
│  101   │  Ravi Kumar  │   85   │
│  102   │  Priya Singh │   92   │
│  103   │  Aman Gupta  │   78   │
... (all 8 rows)
```

### Example 3 — Column Aliases:
```sql
SELECT Name AS StudentName, Marks AS FinalMarks
FROM STUDENTS;
-- AS renames columns in the output (doesn't change table)

Result:
┌──────────────┬────────────┐
│ StudentName  │ FinalMarks │
├──────────────┼────────────┤
│  Ravi Kumar  │    85      │
...
```

### Example 4 — DISTINCT (Remove Duplicates):
```sql
SELECT DISTINCT City FROM STUDENTS;
-- Returns only unique city values

Result:
┌──────────┐
│   City   │
├──────────┤
│  Patna   │
│  Delhi   │
│  Mumbai  │
└──────────┘
-- Patna appeared 4 times, Delhi 2 times, Mumbai 2 times
-- DISTINCT shows each city ONCE
```

---

## 🔷 SECTION 3: WHERE Clause — Filtering Rows

### Purpose: Filter rows BEFORE any processing. Show only rows that match a condition.

```
SYNTAX:
  SELECT columns FROM table WHERE condition;
```

### Comparison Operators:
```sql
-- Equal to:
SELECT * FROM STUDENTS WHERE DeptID = 'CS';
→ Returns: Ravi (101), Aman (103), Sita (106), Nita (108)

-- Not equal to:
SELECT * FROM STUDENTS WHERE DeptID != 'CS';  -- OR <>
→ Returns: Priya (102), Kavya (104), Rohit (105), Mohan (107)

-- Greater than:
SELECT * FROM STUDENTS WHERE Marks > 85;
→ Returns: Priya (92), Kavya (91), Sita (88), Nita (95)

-- Greater than or equal to:
SELECT * FROM STUDENTS WHERE Marks >= 85;
→ Returns: Ravi (85), Priya (92), Kavya (91), Sita (88), Nita (95)

-- Less than:
SELECT * FROM STUDENTS WHERE Marks < 80;
→ Returns: Aman (78), Rohit (65), Mohan (72)

-- Less than or equal to:
SELECT * FROM STUDENTS WHERE Marks <= 78;
→ Returns: Aman (78), Rohit (65), Mohan (72)
```

### Logical Operators — AND, OR, NOT:
```sql
-- AND (both conditions must be true):
SELECT * FROM STUDENTS WHERE DeptID = 'CS' AND Marks > 80;
→ Returns: Ravi (85), Sita (88), Nita (95)  [CS students with >80 marks]

-- OR (at least one condition must be true):
SELECT * FROM STUDENTS WHERE City = 'Delhi' OR City = 'Mumbai';
→ Returns: Priya, Sita (Delhi) + Kavya, Mohan (Mumbai)

-- NOT (negates the condition):
SELECT * FROM STUDENTS WHERE NOT DeptID = 'CS';
→ Same as: WHERE DeptID != 'CS'
→ Returns: Math and Physics students
```

### Special WHERE Operators:
```sql
-- BETWEEN (range, inclusive):
SELECT * FROM STUDENTS WHERE Marks BETWEEN 80 AND 92;
→ Returns students with marks from 80 to 92 inclusive
→ Ravi(85), Priya(92), Kavya(91), Sita(88)

-- IN (check multiple values):
SELECT * FROM STUDENTS WHERE City IN ('Patna', 'Delhi');
→ Returns students from Patna OR Delhi
→ Ravi, Aman, Rohit, Nita (Patna) + Priya, Sita (Delhi)

-- NOT IN:
SELECT * FROM STUDENTS WHERE City NOT IN ('Patna');
→ Returns students NOT from Patna

-- LIKE (pattern matching):
SELECT * FROM STUDENTS WHERE Name LIKE 'R%';
→ Returns students whose name STARTS WITH R: Ravi, Rohit

SELECT * FROM STUDENTS WHERE Name LIKE '%a%';
→ Returns students whose name CONTAINS 'a': Ravi, Aman, Kavya, Sita, Nita

SELECT * FROM STUDENTS WHERE Name LIKE '____a%';
→ Names with exactly 4 chars before 'a' (use _ for single char)

-- NULL checks:
SELECT * FROM STUDENTS WHERE Email IS NULL;
SELECT * FROM STUDENTS WHERE Email IS NOT NULL;
-- Never use = NULL or != NULL (NULL needs IS/IS NOT)
```

### LIKE Wildcard Reference:
```
% = Zero or more characters (any string)
_ = Exactly ONE character

Examples:
  'R%'    = starts with R (Ravi, Rohit, Ram, R)
  '%a'    = ends with a (India, Patna)
  '%a%'   = contains a anywhere
  'Ra_i'  = Ra + any one char + i (Ravi, Ragi)
  '_avi'  = any char + avi (Ravi, Kavi)

🎯 PYQ FACT: In SQL LIKE, % matches multiple characters, _ matches exactly one.
```

---

## 🔷 SECTION 4: ORDER BY Clause — Sorting Results

### Purpose: Sort the final results in ascending or descending order.

```
SYNTAX:
  SELECT columns FROM table ORDER BY column [ASC|DESC];

DEFAULT = ASC (ASCENDING)  ← THIS IS THE MOST TESTED PYQ FACT!
```

### Examples:
```sql
-- Sort by Marks ASCENDING (default — lowest first):
SELECT RollNo, Name, Marks FROM STUDENTS ORDER BY Marks;
-- Same as: ORDER BY Marks ASC

Result:
┌────────┬──────────────┬────────┐
│ RollNo │    Name      │ Marks  │
├────────┼──────────────┼────────┤
│  105   │  Rohit Jha   │   65   │  ← lowest
│  107   │  Mohan Lal   │   72   │
│  103   │  Aman Gupta  │   78   │
│  101   │  Ravi Kumar  │   85   │
│  106   │  Sita Devi   │   88   │
│  104   │  Kavya Verma │   91   │
│  102   │  Priya Singh │   92   │
│  108   │  Nita Patel  │   95   │  ← highest
└────────┴──────────────┴────────┘

-- Sort by Marks DESCENDING (highest first):
SELECT RollNo, Name, Marks FROM STUDENTS ORDER BY Marks DESC;
-- Nita (95) first... Rohit (65) last

-- Sort by Name ALPHABETICALLY (ASC = A to Z):
SELECT * FROM STUDENTS ORDER BY Name ASC;

-- Sort by Name REVERSE ALPHABETICALLY (Z to A):
SELECT * FROM STUDENTS ORDER BY Name DESC;

-- Sort by MULTIPLE columns:
SELECT * FROM STUDENTS ORDER BY DeptID ASC, Marks DESC;
-- First sort by DeptID alphabetically, then within each dept sort by Marks highest first
```

### 🚨 PYQ TRAP: ORDER BY Default = ASC (Ascending)
```
Q: "If ORDER BY is used without specifying ASC or DESC, the result is sorted in:"
A: ASCENDING order (ASC is the DEFAULT)

This appears in BPSC exams almost every year!
ORDER BY Marks = ORDER BY Marks ASC (ascending, lowest first)
```

---

## 🔷 SECTION 5: GROUP BY Clause — Grouping Records

### Purpose: Group rows that have the same value in a specified column. Used with aggregate functions.

```
SYNTAX:
  SELECT column, AGGREGATE(col) FROM table GROUP BY column;

RULE: Every column in SELECT must either be:
  (a) In the GROUP BY clause, OR
  (b) Inside an aggregate function
```

### Examples:
```sql
-- Count students per department:
SELECT DeptID, COUNT(*) AS StudentCount
FROM STUDENTS
GROUP BY DeptID;

Result:
┌────────┬──────────────┐
│ DeptID │ StudentCount │
├────────┼──────────────┤
│  CS    │      4       │  (101, 103, 106, 108)
│  Math  │      2       │  (102, 105)
│  Phys  │      2       │  (104, 107)
└────────┴──────────────┘

-- Average marks per department:
SELECT DeptID, AVG(Marks) AS AvgMarks
FROM STUDENTS
GROUP BY DeptID;

Result:
┌────────┬──────────┐
│ DeptID │ AvgMarks │
├────────┼──────────┤
│  CS    │  86.50   │  (85+78+88+95)/4
│  Math  │  78.50   │  (92+65)/2
│  Phys  │  81.50   │  (91+72)/2
└────────┴──────────┘

-- Total marks per city:
SELECT City, SUM(Marks) AS TotalMarks, COUNT(*) AS Students
FROM STUDENTS
GROUP BY City;
```

---

## 🔷 SECTION 6: HAVING Clause — Filtering Groups

### Purpose: Filter groups AFTER GROUP BY. Works like WHERE but for groups.

```
SYNTAX:
  SELECT column, AGGREGATE(col) FROM table
  GROUP BY column
  HAVING aggregate_condition;
```

### Examples:
```sql
-- Show departments with MORE THAN 2 students:
SELECT DeptID, COUNT(*) AS StudentCount
FROM STUDENTS
GROUP BY DeptID
HAVING COUNT(*) > 2;

Result:
┌────────┬──────────────┐
│ DeptID │ StudentCount │
├────────┼──────────────┤
│  CS    │      4       │  ← only CS has > 2 students
└────────┴──────────────┘
Math(2) and Phys(2) are filtered OUT by HAVING.

-- Show departments where average marks > 80:
SELECT DeptID, AVG(Marks) AS AvgMarks
FROM STUDENTS
GROUP BY DeptID
HAVING AVG(Marks) > 80;

Result:
┌────────┬──────────┐
│ DeptID │ AvgMarks │
├────────┼──────────┤
│  CS    │  86.50   │
│  Phys  │  81.50   │
└────────┴──────────┘
Math (78.50) filtered OUT.
```

---

## 🔷 SECTION 7: WHERE vs HAVING — The Critical Comparison

```
┌──────────────────────┬──────────────────────────────┬──────────────────────────────┐
│       FEATURE        │            WHERE             │           HAVING             │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ When it runs         │ BEFORE GROUP BY              │ AFTER GROUP BY               │
│                      │ (filters individual rows)    │ (filters groups)             │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Works on             │ Individual ROWS              │ GROUPS of rows               │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Aggregate functions  │ CANNOT use aggregate         │ CAN and MUST use aggregates  │
│                      │ (COUNT, SUM, AVG, etc.)      │ (HAVING COUNT(*) > 5 ✓)      │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Used with GROUP BY?  │ Not required (independent)   │ Usually WITH GROUP BY        │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Example (Correct)    │ WHERE Marks > 80             │ HAVING COUNT(*) > 2          │
├──────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Example (WRONG)      │ WHERE COUNT(*) > 2 ← ERROR!  │ HAVING Marks > 80 ← USUALLY  │
│                      │ Can't use aggregate in WHERE │   incorrect (use WHERE)      │
└──────────────────────┴──────────────────────────────┴──────────────────────────────┘

COMBINED EXAMPLE — Using both WHERE and HAVING together:
SELECT DeptID, AVG(Marks) AS AvgMarks, COUNT(*) AS Students
FROM STUDENTS
WHERE City = 'Patna'           -- STEP 1: Filter to only Patna students
GROUP BY DeptID                 -- STEP 2: Group those by department
HAVING COUNT(*) >= 2;           -- STEP 3: Only departments with 2+ Patna students

EXPLANATION:
→ WHERE first removes all non-Patna students (keeps: Ravi, Aman, Rohit, Nita)
→ GROUP BY groups remaining by DeptID (CS: Ravi/Aman/Nita; Math: Rohit)
→ HAVING keeps only groups with 2+ students (CS has 3, Math has 1 — only CS shown)
```

---

## 🔷 SECTION 8: Aggregate Functions — The Five Pillars

### What are Aggregate Functions?
> **Aggregate functions perform calculations on a SET of rows and return a SINGLE summarised value.**

```
THE 5 STANDARD AGGREGATE FUNCTIONS:
┌──────────────┬───────────────────────────────┬───────────────────────────┐
│   FUNCTION   │          PURPOSE              │         EXAMPLE           │
├──────────────┼───────────────────────────────┼───────────────────────────┤
│ COUNT()      │ Count number of rows/values   │ COUNT(*) = total rows     │
│              │ COUNT(*) counts ALL rows      │ COUNT(Email) = non-NULL   │
│              │ COUNT(col) skips NULLs        │                           │
├──────────────┼───────────────────────────────┼───────────────────────────┤
│ SUM()        │ Add all values in a column    │ SUM(Marks) = total marks  │
│              │ Ignores NULL values           │ = 85+92+78+91+65+88+72+95 │
│              │                               │ = 666                     │
├──────────────┼───────────────────────────────┼───────────────────────────┤
│ AVG()        │ Calculate average of values   │ AVG(Marks) = 666/8 = 83.25│
│              │ = SUM / COUNT (of non-NULLs)  │                           │
├──────────────┼───────────────────────────────┼───────────────────────────┤
│ MAX()        │ Find the maximum value        │ MAX(Marks) = 95 (Nita)    │
│              │ Works on numbers AND text     │ MAX(Name) = alphabetically│
│              │                               │ last name                 │
├──────────────┼───────────────────────────────┼───────────────────────────┤
│ MIN()        │ Find the minimum value        │ MIN(Marks) = 65 (Rohit)   │
│              │ Works on numbers AND text     │ MIN(Name) = alphabetically│
│              │                               │ first name                │
└──────────────┴───────────────────────────────┴───────────────────────────┘
```

### Aggregate Function Examples:
```sql
-- Total number of students:
SELECT COUNT(*) AS TotalStudents FROM STUDENTS;
→ Result: 8

-- Total marks of all students:
SELECT SUM(Marks) AS TotalMarks FROM STUDENTS;
→ Result: 666

-- Average marks:
SELECT AVG(Marks) AS AverageMarks FROM STUDENTS;
→ Result: 83.25

-- Highest marks:
SELECT MAX(Marks) AS HighestMark FROM STUDENTS;
→ Result: 95

-- Lowest marks:
SELECT MIN(Marks) AS LowestMark FROM STUDENTS;
→ Result: 65

-- Find who has the highest marks:
SELECT Name, Marks FROM STUDENTS WHERE Marks = (SELECT MAX(Marks) FROM STUDENTS);
→ Result: Nita Patel — 95

-- Count of students per department:
SELECT DeptID, COUNT(*) AS Count FROM STUDENTS GROUP BY DeptID;
→ CS:4, Math:2, Phys:2

-- COUNT(*) vs COUNT(column):
SELECT COUNT(*) FROM STUDENTS;           -- counts ALL rows including NULLs: 8
SELECT COUNT(Email) FROM STUDENTS;       -- counts only non-NULL Email values
-- (if one Email is NULL, COUNT(Email) = 7, COUNT(*) = 8)
```

### 🚨 PYQ TRAP — COMPUTE Is NOT an Aggregate Function:
```
VALID AGGREGATE FUNCTIONS: COUNT, SUM, AVG, MAX, MIN
(Some databases also: VARIANCE, STDDEV, FIRST, LAST)

INVALID / NOT STANDARD: COMPUTE
→ COMPUTE is NOT a standard SQL aggregate function!
→ It existed as a proprietary extension in old Sybase/SQL Server (deprecated)
→ If "COMPUTE" appears as an option in an MCQ about aggregate functions → it's WRONG!

EXAM TRAP: "Which of the following is NOT a valid aggregate function?"
Answer: COMPUTE (or MULTIPLY, DIVIDE, etc.)
```

---

## 🔷 SECTION 9: The WITH Clause (Common Table Expression — CTE)

### Purpose: Create a temporary named result set (like a temporary table) that exists only for the duration of the query.

```
SYNTAX:
  WITH cte_name AS (
      SELECT ...  -- This is the temporary result
  )
  SELECT * FROM cte_name WHERE ...;  -- Use it here

ANALOGY:
  WITH is like creating a "named scratch pad" — you compute something first,
  give it a name, then reference that name in the main query.
  Like creating a temporary variable in programming.

EXAMPLE:
  -- Find students who score above the class average:
  
  WITHOUT WITH (complex subquery):
  SELECT Name, Marks FROM STUDENTS
  WHERE Marks > (SELECT AVG(Marks) FROM STUDENTS);
  
  WITH WITH clause (cleaner):
  WITH AvgMarks AS (
      SELECT AVG(Marks) AS ClassAvg FROM STUDENTS
  )
  SELECT S.Name, S.Marks
  FROM STUDENTS S, AvgMarks A
  WHERE S.Marks > A.ClassAvg;

ANOTHER EXAMPLE:
  -- List departments with above-average student counts:
  WITH DeptCount AS (
      SELECT DeptID, COUNT(*) AS NumStudents
      FROM STUDENTS
      GROUP BY DeptID
  )
  SELECT DeptID, NumStudents
  FROM DeptCount
  WHERE NumStudents > (SELECT AVG(NumStudents) FROM DeptCount);

🎯 PYQ FACT: WITH clause creates a TEMPORARY RELATION (CTE).
             It doesn't permanently store data.
             It's also called "Common Table Expression" (CTE).
```

---

## 🔷 SECTION 10: SQL Constraints — Quick Overview

```
CONSTRAINTS = Rules applied to table columns to enforce data integrity

┌──────────────────┬──────────────────────────────────────────────────────┐
│   CONSTRAINT     │                    PURPOSE                           │
├──────────────────┼──────────────────────────────────────────────────────┤
│ PRIMARY KEY      │ Unique identifier for each row; NOT NULL + UNIQUE    │
├──────────────────┼──────────────────────────────────────────────────────┤
│ FOREIGN KEY      │ Enforces referential integrity between tables        │
├──────────────────┼──────────────────────────────────────────────────────┤
│ UNIQUE           │ All values in column must be distinct (NULLs allowed)│
├──────────────────┼──────────────────────────────────────────────────────┤
│ NOT NULL         │ Column must always have a value (NULL not allowed)   │
├──────────────────┼──────────────────────────────────────────────────────┤
│ DEFAULT          │ Assigns default value if no value specified          │
├──────────────────┼──────────────────────────────────────────────────────┤
│ CHECK            │ Value must satisfy a specified condition              │
│                  │ e.g., CHECK(Age >= 18)                               │
└──────────────────┴──────────────────────────────────────────────────────┘
```

### 🚨 PYQ TRAP — UNION Is NOT a Constraint:
```
VALID SQL CONSTRAINTS: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, DEFAULT, CHECK

NOT a Constraint: UNION
→ UNION is a SET OPERATION that combines results of two SELECT queries!
→ It is NOT a constraint on a table column.

UNION example (set operation, not constraint):
  SELECT Name FROM STUDENTS WHERE DeptID = 'CS'
  UNION
  SELECT Name FROM STUDENTS WHERE Marks > 90;
  → Returns all CS students + all students with marks > 90 (no duplicates)
  
EXAM TRAP: "Which of the following is a constraint in SQL?"
Options: PRIMARY KEY / FOREIGN KEY / UNION / NOT NULL
Answer: UNION is NOT a constraint!
```

---

## 🔷 SECTION 11: SQL Set Operations — UNION, INTERSECT, EXCEPT

```
SET OPERATIONS combine results of multiple SELECT statements:

UNION: Returns ALL rows from both queries (removes duplicates)
  SELECT Name FROM STUDENTS WHERE DeptID = 'CS'
  UNION
  SELECT Name FROM STUDENTS WHERE City = 'Patna';
  → CS students + Patna students (each name once)

UNION ALL: Returns ALL rows including duplicates
  (Use when you want duplicates)

INTERSECT: Returns only rows common to BOTH queries
  SELECT Name FROM STUDENTS WHERE DeptID = 'CS'
  INTERSECT
  SELECT Name FROM STUDENTS WHERE City = 'Patna';
  → Only CS students who are ALSO from Patna

EXCEPT / MINUS: Returns rows in first query NOT in second
  SELECT Name FROM STUDENTS WHERE DeptID = 'CS'
  EXCEPT
  SELECT Name FROM STUDENTS WHERE City = 'Patna';
  → CS students who are NOT from Patna

CONDITIONS for Set Operations:
  → Both SELECT statements must have SAME number of columns
  → Corresponding columns must have COMPATIBLE data types
```

---

## 🔷 SECTION 12: Complete Query Example — All Clauses Together

```sql
-- SCENARIO: Find departments (not Admin) having avg marks > 75,
--           show top 2 departments by avg marks

SELECT 
    DeptID,
    COUNT(*) AS StudentCount,
    AVG(Marks) AS AvgMarks,
    MAX(Marks) AS TopMark,
    MIN(Marks) AS LowestMark
FROM STUDENTS
WHERE DeptID != 'Admin'          -- Filter: exclude Admin dept rows
GROUP BY DeptID                  -- Group by department
HAVING AVG(Marks) > 75           -- Filter: only depts with avg > 75
ORDER BY AvgMarks DESC           -- Sort: highest avg first
LIMIT 2;                         -- Show: only top 2

STEP-BY-STEP EXECUTION:
  1. FROM STUDENTS           → Load all 8 rows
  2. WHERE DeptID != 'Admin' → Keep all rows (none are Admin): 8 rows remain
  3. GROUP BY DeptID         → CS group(4), Math group(2), Phys group(2)
  4. HAVING AVG > 75         → CS(86.5 ✓), Math(78.5 ✓), Phys(81.5 ✓) — all pass
  5. SELECT DeptID, COUNT, AVG, MAX, MIN → Compute for each group
  6. ORDER BY AvgMarks DESC  → CS(86.5), Phys(81.5), Math(78.5)
  7. LIMIT 2                 → Show only CS and Phys

RESULT:
┌────────┬──────────────┬──────────┬─────────┬────────────┐
│ DeptID │ StudentCount │ AvgMarks │ TopMark │ LowestMark │
├────────┼──────────────┼──────────┼─────────┼────────────┤
│  CS    │     4        │  86.50   │   95    │    78      │
│  Phys  │     2        │  81.50   │   91    │    72      │
└────────┴──────────────┴──────────┴─────────┴────────────┘
```

---

## 🔷 SECTION 13: SELECT Query Execution Flowchart

```
WRITE ORDER vs EXECUTION ORDER:

WE WRITE:          SQL EXECUTES:
─────────          ─────────────────────────────────────────
SELECT          6. SELECT columns → build output columns
FROM            1. FROM → identify source table(s)
WHERE           2. WHERE → filter rows by condition
GROUP BY        3. GROUP BY → group filtered rows
HAVING          4. HAVING → filter groups
ORDER BY        7. ORDER BY → sort final result
LIMIT           8. LIMIT → restrict number of output rows

And DISTINCT happens after SELECT (step 6.5)

VISUAL FLOW:
  [RAW TABLE DATA]
       │
       ▼ FROM — load table
       │
       ▼ WHERE — remove rows that don't match condition
       │
       ▼ GROUP BY — cluster rows into groups
       │
       ▼ HAVING — remove groups that don't match condition
       │
       ▼ SELECT — pick which columns to show; compute expressions
       │
       ▼ DISTINCT — remove duplicate rows from result
       │
       ▼ ORDER BY — sort remaining rows
       │
       ▼ LIMIT — cut to N rows
       │
  [FINAL RESULT SET]
```

---

## 🔷 SECTION 14: PYQ Traps Summary

```
TRAP 1: "ORDER BY default is DESC"
  → FALSE! ORDER BY default is ASC (Ascending). Must explicitly write DESC for descending.

TRAP 2: "HAVING can replace WHERE"
  → FALSE! HAVING works on GROUPS after GROUP BY.
           WHERE works on individual ROWS before grouping.
           You cannot use aggregate functions (COUNT, AVG) in WHERE.

TRAP 3: "COMPUTE is a valid aggregate function"
  → FALSE! Valid aggregate functions: COUNT, SUM, AVG, MAX, MIN.
           COMPUTE is NOT standard SQL.

TRAP 4: "UNION is a constraint in SQL"
  → FALSE! UNION is a SET OPERATION (combines queries).
           Constraints: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, DEFAULT, CHECK.

TRAP 5: "COUNT(*) and COUNT(column) always give the same result"
  → FALSE! COUNT(*) counts all rows including those with NULLs.
           COUNT(column) counts only non-NULL values in that column.

TRAP 6: "SELECT * shows only rows where all columns have values"
  → FALSE! SELECT * shows ALL rows regardless of NULL values.

TRAP 7: "AVG(Marks) counts NULL values as 0"
  → FALSE! AVG (and all aggregate functions except COUNT(*)) ignore NULL values.
           AVG calculates SUM of non-NULL values / COUNT of non-NULL values.

TRAP 8: "WITH clause permanently stores data in the database"
  → FALSE! WITH (CTE) creates a TEMPORARY relation valid only for that query.
           Data is not permanently stored.

TRAP 9: "LIKE '%' matches exactly one character"
  → FALSE! % matches ZERO or MORE characters. _ matches exactly ONE.

TRAP 10: "GROUP BY is required whenever HAVING is used"
  → MOSTLY TRUE — HAVING is almost always used with GROUP BY.
    Some databases allow HAVING without GROUP BY (treats entire table as one group).
```

---

# PART 2: GENERAL STUDIES
## 🛡️ Biology — Immunity & Lymphocytes

---

## 🔷 SECTION 1: What is Immunity?

### Real-Life Analogy — The Army of the Body:

Your country has THREE layers of defence:
1. **Border walls and fences** — physical barriers (like skin and mucous membranes)
2. **Army at the border** — immediate responders (innate immunity)
3. **Trained special forces** — targeted response against specific threats (adaptive immunity)

Your body's immune system works exactly the same way.

### Definition:
> **Immunity is the ability of an organism to resist and fight disease-causing microorganisms (pathogens — bacteria, viruses, fungi, parasites) and their toxins.**

```
THE IMMUNE SYSTEM'S JOBS:
  1. RECOGNITION: Identify what is "self" (body's own cells) vs "non-self" (foreign)
  2. RESPONSE: Attack and destroy the foreign invader
  3. MEMORY: Remember past invaders for faster response next time (basis of vaccination!)
```

---

## 🔷 SECTION 2: Types of Immunity — The Big Picture

```
                    IMMUNITY
                        │
        ┌───────────────┴───────────────┐
        │                               │
  INNATE IMMUNITY               ACQUIRED IMMUNITY
  (Natural/Non-specific)        (Adaptive/Specific)
        │                               │
  Present from birth           Develops during life
  Does not learn               Learns and remembers
  Fast response                Slower but more powerful
        │                               │
  Physical barriers            ┌────────┴────────┐
  Chemical barriers            │                 │
  Cellular (NK cells,    ACTIVE IMMUNITY   PASSIVE IMMUNITY
  phagocytes)            (body makes       (ready antibodies
  Inflammatory response  own antibodies)   given from outside)
                               │                 │
                         ┌─────┴─────┐    ┌──────┴──────┐
                       NATURAL     ARTIFICIAL  NATURAL   ARTIFICIAL
                      (infection)  (vaccine)  (maternal  (antiserum/
                                              antibodies) immunoglobulin)
```

---

## 🔷 SECTION 3: INNATE IMMUNITY — The First Line of Defence

### Definition:
> **Innate (natural/non-specific) immunity is the INBORN, NON-SPECIFIC resistance that provides immediate but non-targeted defence against all pathogens.**

```
KEY FEATURES:
  → Present from BIRTH (no learning needed)
  → NON-SPECIFIC — attacks ALL foreign invaders the same way
  → No MEMORY — same response every time the pathogen appears
  → FAST — responds within minutes to hours
  → Acts as the FIRST LINE and SECOND LINE of defence

FOUR TYPES OF INNATE DEFENCE:

TYPE 1: ANATOMICAL / PHYSICAL BARRIERS (1st line of defence)
  → SKIN: tough outer barrier (intact skin prevents most pathogens)
    Even dead skin cells act as a physical wall.
    Sebaceous glands secrete SEBUM (slightly acidic, kills bacteria)
  → MUCOUS MEMBRANES: Line respiratory, digestive, urinary tracts
    Trap pathogens in sticky mucus
  → CILIA: Hair-like projections in respiratory tract
    Beat rhythmically to sweep trapped pathogens toward throat (mucociliary clearance)
  → TEARS: Contain lysozyme (an enzyme that breaks bacterial cell walls)
  → SALIVA: Contains lysozyme + immunoglobulin A (IgA)
  → STOMACH ACID (HCl): Kills most ingested bacteria (pH ~2)
  → URINE FLOW: Flushes bacteria from urinary tract

TYPE 2: PHYSIOLOGICAL BARRIERS
  → FEVER: High temperature slows bacterial/viral replication
  → INTERFERON: Proteins secreted by virus-infected cells
    Warn neighbouring cells to prepare defences against virus
    "Molecular alarm signal"
  → LOW pH: Acidic skin, stomach acid, vaginal secretions kill pathogens
  → LYSOZYME: Enzyme in tears, saliva, sweat — dissolves bacterial cell walls

TYPE 3: PHAGOCYTIC / CELLULAR BARRIERS
  → NEUTROPHILS: Most abundant white blood cells (WBC)
    First responders — engulf and destroy bacteria (PHAGOCYTOSIS)
    Short-lived (hours to days)
  → MACROPHAGES: "Big eaters" (macro = big, phage = eat)
    Patrol tissues, engulf dead cells, bacteria, foreign particles
    Also PRESENT antigens to T cells (link between innate and adaptive)
  → NATURAL KILLER (NK) CELLS: 
    Destroy virus-infected cells and cancer cells
    Without needing specific antigen recognition
    Important "surveillance" cells against tumours

TYPE 4: INFLAMMATORY BARRIERS
  → When tissue is damaged or infected:
    Damaged cells release HISTAMINE
    Blood vessels dilate → more blood to area (redness, warmth)
    Blood vessels become leaky → fluid enters tissue (swelling)
    Pain signals sent to brain
    WBCs rush to site
  → The classic 4 signs of inflammation:
    RUBOR (redness), CALOR (warmth), TUMOR (swelling), DOLOR (pain)
```

---

## 🔷 SECTION 4: ACQUIRED (ADAPTIVE) IMMUNITY — The Targeted Attack

### Definition:
> **Acquired (adaptive/specific) immunity is the TARGETED, LEARNED immune response that develops after exposure to a specific pathogen. It involves LYMPHOCYTES and has MEMORY.**

```
KEY FEATURES:
  → NOT present at birth — ACQUIRED during life
  → SPECIFIC — responds to a particular antigen/pathogen
  → Has MEMORY — next exposure triggers faster, stronger response
  → SLOWER to develop (days to weeks for first exposure)
  → Involves LYMPHOCYTES (B-cells and T-cells)
  → TWO BRANCHES: Humoral (B-cells, antibodies) + Cell-mediated (T-cells)

ANTIGEN: Any molecule that triggers an immune response (usually on pathogen surface)
ANTIBODY: Protein made by B-cells that specifically binds to one antigen
```

---

## 🔷 SECTION 5: LYMPHOCYTES — The Key Players

### What are Lymphocytes?
```
LYMPHOCYTES = White blood cells (WBCs/leukocytes) that are the MAIN CELLS 
              of the adaptive immune system.

ORIGIN: ALL lymphocytes originate from STEM CELLS in BONE MARROW.

After originating in bone marrow, they go different ways:
  → B-lymphocytes: Stay in BONE MARROW to mature → B-cells
  → T-lymphocytes: Travel to THYMUS to mature → T-cells

MEMORY TRICK:
  B = Bone marrow (mature here) → Bursa in birds (original discovery)
  T = Thymus (mature here)
```

---

### B-LYMPHOCYTES (B-CELLS):

```
FULL NAME: B-Lymphocytes / B-Cells
ORIGIN:    Bone Marrow (stem cells)
MATURATION: BONE MARROW (in mammals)
            BURSA OF FABRICIUS (in birds — that's where "B" originally came from!)

FUNCTION: HUMORAL IMMUNITY — produce ANTIBODIES
          "Humoral" = from Latin "humor" (liquid/fluid) — antibodies are in blood/fluids

HOW B-CELLS WORK:
  1. Pathogen enters body → its ANTIGENS are detected
  2. B-cell with matching antibody receptor binds to the antigen
  3. With help from Helper T-cells → B-cell is ACTIVATED
  4. Activated B-cell PROLIFERATES (divides many times)
  5. Divides into:
     (a) PLASMA CELLS: Produce ANTIBODIES in huge quantities
     (b) MEMORY B-CELLS: Long-lived; remember this pathogen for future

ANTIBODIES (Immunoglobulins):
  Structure: Y-shaped protein with two identical binding sites
  Types: IgM, IgG, IgA, IgE, IgD
  
  IgG = Most abundant in blood (main protection in secondary response)
  IgM = First antibody made in primary response (large, stays in blood)
  IgA = Found in secretions (saliva, tears, breast milk, mucus)
  IgE = Involved in ALLERGIES and anti-parasite defence
  IgD = Mainly on B-cell surface as receptor

WHAT ANTIBODIES DO:
  → NEUTRALISATION: Block pathogen from entering cells
  → OPSONISATION: Tag pathogen for destruction by phagocytes
  → COMPLEMENT ACTIVATION: Trigger cascade that destroys pathogens
  → AGGLUTINATION: Clump pathogens together for easier removal

🎯 PYQ FACT: B-cells produce ANTIBODIES. This is HUMORAL IMMUNITY.
             B-cells mature in BONE MARROW.
```

---

### T-LYMPHOCYTES (T-CELLS):

```
FULL NAME: T-Lymphocytes / T-Cells
ORIGIN:    Bone Marrow (stem cells)
MATURATION: THYMUS gland (in the chest, above heart)
            "T" stands for THYMUS

TYPES OF T-CELLS:
  1. HELPER T-CELLS (CD4+ T-cells / TH cells):
     → The "COMMANDER" of the immune response
     → When an antigen is presented (by macrophage/dendritic cell):
       Helper T-cell ACTIVATES both B-cells AND Cytotoxic T-cells
     → Secretes CYTOKINES (chemical messengers) to coordinate the response
     → HIV TARGETS HELPER T-CELLS! (why HIV/AIDS is so devastating)
     → CD4 count is used to monitor HIV progression

  2. CYTOTOXIC T-CELLS (CD8+ T-cells / Killer T-cells / Tc cells):
     → The "SOLDIERS" — directly KILL infected cells and cancer cells
     → Recognise infected cells (virus-infected, cancerous) by their surface markers
     → Release PERFORIN (punches holes in target cell membrane)
     → Release GRANZYMES (enter through holes and trigger cell death)
     → Target cells die by APOPTOSIS (programmed cell death)
     → CELL-MEDIATED IMMUNITY

  3. REGULATORY T-CELLS (Treg / Suppressor T-cells):
     → "PEACEKEEPERS" — prevent overactive immune responses
     → Suppress immune activity AFTER pathogen is cleared
     → Prevent autoimmune reactions (attacking own cells)
     → Important in preventing allergies and autoimmune diseases

  4. MEMORY T-CELLS:
     → Long-lived cells that remember specific pathogens
     → Basis of LONG-TERM IMMUNITY after infection or vaccination
     → Respond MUCH FASTER and STRONGER to second exposure

CELL-MEDIATED IMMUNITY:
  → Direct killing of infected cells by Cytotoxic T-cells
  → Does NOT involve antibodies
  → Important against: INTRACELLULAR pathogens (viruses, some bacteria like TB),
    cancer cells, and in organ transplant rejection

🎯 PYQ FACT: T-cells mature in THYMUS. 
             Helper T-cells are targeted by HIV.
             Cytotoxic T-cells kill virus-infected cells directly.
             T-cells mediate CELL-MEDIATED IMMUNITY.
```

---

## 🔷 SECTION 6: B-cells vs T-cells Comparison Table

```
┌──────────────────────┬────────────────────────────────┬────────────────────────────────┐
│       FEATURE        │           B-CELLS              │           T-CELLS              │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Full Name            │ B-Lymphocytes                  │ T-Lymphocytes                  │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Origin               │ Bone Marrow (stem cells)       │ Bone Marrow (stem cells)       │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Maturation site      │ BONE MARROW (mammals)          │ THYMUS gland                   │
│                      │ BURSA OF FABRICIUS (birds)     │                                │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Type of immunity     │ HUMORAL immunity               │ CELL-MEDIATED immunity         │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Main weapon          │ ANTIBODIES (immunoglobulins)   │ Direct cell killing            │
│                      │ (Y-shaped proteins)            │ (Perforin + Granzymes)         │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Against what?        │ FREE pathogens in blood/fluids │ Infected cells, cancer cells   │
│                      │ (bacteria, viruses in blood)   │ (intracellular pathogens)      │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Sub-types            │ Plasma cells, Memory B-cells   │ Helper T, Cytotoxic T,         │
│                      │                                │ Regulatory T, Memory T         │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ HIV attacks?         │ NO (B-cells not targeted)      │ YES — Helper T-cells (CD4+)    │
├──────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Memory?              │ YES — Memory B-cells           │ YES — Memory T-cells           │
└──────────────────────┴────────────────────────────────┴────────────────────────────────┘
```

---

## 🔷 SECTION 7: Active vs Passive Immunity

```
┌──────────────────┬────────────────────────────────┬────────────────────────────────┐
│     TYPE         │       ACTIVE IMMUNITY          │       PASSIVE IMMUNITY         │
├──────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Definition       │ Body PRODUCES its own antibodies│ Ready-made antibodies given    │
│                  │ in response to antigen         │ from an external source         │
├──────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Memory formed?   │ YES — long-lasting immunity    │ NO — temporary protection       │
├──────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Onset            │ SLOW (days to weeks)           │ FAST (immediate)               │
├──────────────────┼────────────────────────────────┼────────────────────────────────┤
│ Duration         │ LONG — years to lifetime       │ SHORT — weeks to months        │
├──────────────────┼────────────────────────────────┼────────────────────────────────┤
│ NATURAL          │ After actual INFECTION          │ Mother → baby via placenta     │
│                  │ (recovering from chickenpox)   │ (IgG) or breast milk (IgA)     │
├──────────────────┼────────────────────────────────┼────────────────────────────────┤
│ ARTIFICIAL       │ VACCINATION (weakened/killed   │ Antiserum injection (snake bite │
│                  │ pathogen or its parts)         │ antivenom, tetanus shot)        │
└──────────────────┴────────────────────────────────┴────────────────────────────────┘

🎯 PYQ FACT: Vaccination = ACTIVE ARTIFICIAL immunity
             Antivenom (snake bite treatment) = PASSIVE ARTIFICIAL immunity
             Mother's antibodies to baby = PASSIVE NATURAL immunity
             Recovering from an infection = ACTIVE NATURAL immunity
```

---

## 🔷 SECTION 8: Key Immunity PYQ Facts

```
🎯 LYMPHOCYTES = Main cells of adaptive immunity
🎯 B-cells mature in BONE MARROW; T-cells mature in THYMUS
🎯 B-cells produce ANTIBODIES → HUMORAL immunity
🎯 T-cells → CELL-MEDIATED immunity (direct killing)
🎯 HIV attacks HELPER T-CELLS (CD4+ cells) → causes AIDS
🎯 CD4 count < 200 = AIDS diagnosis
🎯 ANTIBODIES = IMMUNOGLOBULINS (Y-shaped proteins)
🎯 IgG = most abundant antibody in blood (secondary response)
🎯 IgA = in body secretions (saliva, tears, breast milk)
🎯 IgE = in ALLERGIES and anti-parasite
🎯 IgM = first antibody produced in primary response
🎯 PLASMA CELLS = antibody-producing cells (derived from B-cells)
🎯 MEMORY CELLS = basis of vaccination and long-term immunity
🎯 VACCINATION = Active Artificial immunity
🎯 ANTIVENOM = Passive Artificial immunity
🎯 INTERFERON = anti-viral protein (innate immunity)
🎯 MACROPHAGE = "big eater" — phagocyte; also links innate and adaptive
🎯 NATURAL KILLER CELLS = kill cancer cells + virus-infected cells (innate)
🎯 LYSOZYME = enzyme in tears/saliva/sweat that destroys bacteria
🎯 PRIMARY RESPONSE = slower, weaker (first exposure to antigen)
🎯 SECONDARY RESPONSE = faster, stronger (memory cells activated)
```

---

## 🔷 SECTION 9: Memory Tricks

```
LYMPHOCYTE MEMORY TRICKS:

B-cells:
  "B-cells Born in Bone marrow and Become antibody-producing factories"
  "B = Bursa (birds) = Bone Marrow (mammals) = anti-Bodies"
  B → Bursa/Bone → Builds antibodies → Blood/Body fluids (humoral)

T-cells:
  "T-cells Trained in Thymus to Touch and kill Targeted cells"
  T → Thymus → Target (specific cell killing)
  
  Types of T-cells: "HCRoM"
  H = Helper (coordinates response)
  C = Cytotoxic (killer cells)
  R = Regulatory (suppress overreaction)
  M = Memory (remembers for future)

HIV TRICK:
  "HIV Hunts Helper T-cells" (both start with H)
  HIV destroys Helper T-cells → no coordination → entire immune system collapses

INNATE vs ADAPTIVE:
  INNATE  = INborn + INstant + INdiscriminate (non-specific)
  ADAPTIVE = Acquired + Adapts + rememers (specific + memory)
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: SQL SELECT, Clauses, Aggregate Functions, ORDER BY, GROUP BY, HAVING

---

**Q1.** The DEFAULT sorting order of the ORDER BY clause in SQL is:
(A) DESC (Descending — highest to lowest)
(B) ASC (Ascending — lowest to highest)
(C) RANDOM (no specific order)
(D) More than one of the above
(E) None of the above

---

**Q2.** Which SQL clause is used to filter individual rows BEFORE any grouping?
(A) HAVING
(B) ORDER BY
(C) WHERE
(D) More than one of the above
(E) None of the above

---

**Q3.** Which SQL clause is used to filter GROUPS after GROUP BY?
(A) WHERE
(B) HAVING
(C) DISTINCT
(D) More than one of the above
(E) None of the above

---

**Q4.** Which of the following is NOT a valid standard SQL aggregate function?
(A) COUNT()
(B) AVG()
(C) COMPUTE()
(D) More than one of the above
(E) None of the above

---

**Q5.** What does SELECT DISTINCT City FROM STUDENTS; return?
(A) All rows from STUDENTS table
(B) Only the City column with each unique city name listed exactly once
(C) Only cities where more than one student lives
(D) More than one of the above
(E) None of the above

---

**Q6.** The query: SELECT * FROM STUDENTS ORDER BY Marks;
will display results in which order?
(A) Descending order of marks (95 first, 65 last)
(B) Ascending order of marks (65 first, 95 last) — ASC is default
(C) Random order
(D) More than one of the above
(E) None of the above

---

**Q7.** Which SQL aggregate function would you use to find the HIGHEST marks scored?
(A) SUM(Marks)
(B) TOP(Marks)
(C) MAX(Marks)
(D) More than one of the above
(E) None of the above

---

**Q8.** The following query has an ERROR. Identify it:
SELECT DeptID, COUNT(*) FROM STUDENTS WHERE COUNT(*) > 2 GROUP BY DeptID;
(A) COUNT(*) cannot be used in any SQL query
(B) COUNT(*) cannot be used in the WHERE clause — use HAVING instead
(C) GROUP BY and WHERE cannot appear in the same query
(D) More than one of the above
(E) None of the above

---

**Q9.** What does the WITH clause create in SQL?
(A) A permanent new table in the database
(B) A temporary named result set (Common Table Expression) valid only for that query
(C) A security level for accessing tables
(D) More than one of the above
(E) None of the above

---

**Q10.** UNION in SQL is:
(A) A constraint that enforces uniqueness across two tables
(B) A set operation that combines results of two SELECT queries (removes duplicates)
(C) An aggregate function
(D) More than one of the above
(E) None of the above

---

**Q11.** The difference between COUNT(*) and COUNT(column_name) is:
(A) There is no difference — they always give the same result
(B) COUNT(*) counts all rows including those with NULL; COUNT(col) counts only non-NULL values
(C) COUNT(column) is faster than COUNT(*)
(D) More than one of the above
(E) None of the above

---

**Q12.** SELECT DeptID, AVG(Marks) FROM STUDENTS GROUP BY DeptID HAVING AVG(Marks) > 80;
This query returns:
(A) All students with marks > 80
(B) All departments where at least one student has marks > 80
(C) Only departments where the AVERAGE marks across all students in that dept exceed 80
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following is a valid SQL CONSTRAINT?
(A) UNION
(B) GROUP BY
(C) CHECK
(D) More than one of the above
(E) None of the above

---

**Q14.** What does the LIKE operator '%a%' match?
(A) Strings that start with 'a'
(B) Strings that end with 'a'
(C) Strings that contain the letter 'a' anywhere
(D) More than one of the above
(E) None of the above

---

**Q15.** The correct execution ORDER of SQL clauses is:
(A) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
(B) FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY
(C) WHERE → FROM → SELECT → GROUP BY → HAVING → ORDER BY
(D) More than one of the above
(E) None of the above

---

**Q16.** SELECT Name FROM STUDENTS WHERE Marks BETWEEN 80 AND 90;
Which students are included?
(A) Students with marks strictly between 80 and 90 (excludes 80 and 90)
(B) Students with marks 80 to 90 INCLUSIVE (includes both 80 and 90)
(C) Students with marks greater than 80 only
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following correctly calculates total marks of all CS students?
(A) SELECT COUNT(Marks) FROM STUDENTS WHERE DeptID = 'CS';
(B) SELECT SUM(Marks) FROM STUDENTS WHERE DeptID = 'CS';
(C) SELECT AVG(Marks) FROM STUDENTS WHERE DeptID = 'CS';
(D) More than one of the above
(E) None of the above

---

**Q18.** What does SELECT * FROM STUDENTS WHERE Name LIKE 'R_vi'; match?
(A) All names starting with R
(B) Names that are exactly 4 characters: R + any character + vi
(C) Names with R and vi anywhere
(D) More than one of the above
(E) None of the above

---

**Q19.** The AVG() function in SQL:
(A) Includes NULL values as 0 in the calculation
(B) Ignores NULL values and calculates average of non-NULL values only
(C) Returns NULL if any value in the column is NULL
(D) More than one of the above
(E) None of the above

---

**Q20.** Which SQL operation removes DUPLICATE ROWS from the union of two SELECT queries?
(A) UNION ALL
(B) INTERSECT
(C) UNION (without ALL)
(D) More than one of the above
(E) None of the above

---

**Q21.** SELECT City, COUNT(*) AS Students FROM STUDENTS GROUP BY City ORDER BY Students DESC;
What does this query do?
(A) Lists cities alphabetically with student counts
(B) Lists cities with their student counts, sorted from most students to least
(C) Lists cities filtered to show only those with more than one student
(D) More than one of the above
(E) None of the above

---

**Q22.** In SQL, the NOT operator in WHERE NOT DeptID = 'CS' is equivalent to:
(A) WHERE DeptID = 'CS'
(B) WHERE DeptID != 'CS' (or WHERE DeptID <> 'CS')
(C) WHERE DeptID IS NULL
(D) More than one of the above
(E) None of the above

---

**Q23.** Why can't aggregate functions be used in the WHERE clause?
(A) It is a syntax limitation that may be fixed in future SQL versions
(B) WHERE runs before GROUP BY, so groups don't exist yet; aggregate functions need groups/sets of rows
(C) Aggregate functions are only allowed in SELECT statements
(D) More than one of the above
(E) None of the above

---

**Q24.** SELECT MIN(Marks), MAX(Marks), MAX(Marks) - MIN(Marks) AS Range FROM STUDENTS;
What does the "Range" column show?
(A) The average marks
(B) The difference between highest and lowest marks (95 - 65 = 30)
(C) The total number of students
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following SQL queries finds students whose marks are ABOVE the class average?
(A) SELECT * FROM STUDENTS WHERE Marks > AVG(Marks);
(B) SELECT * FROM STUDENTS HAVING Marks > AVG(Marks);
(C) SELECT * FROM STUDENTS WHERE Marks > (SELECT AVG(Marks) FROM STUDENTS);
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Immunity, Innate vs Acquired, B-cells, T-cells, Lymphocytes, Antibodies

---

**Q26.** The type of immunity that is present from birth and provides non-specific protection is:
(A) Acquired (adaptive) immunity
(B) Innate (natural/non-specific) immunity
(C) Humoral immunity
(D) More than one of the above
(E) None of the above

---

**Q27.** B-lymphocytes (B-cells) in mammals mature in:
(A) Thymus gland
(B) Spleen
(C) Bone Marrow
(D) More than one of the above
(E) None of the above

---

**Q28.** T-lymphocytes (T-cells) mature in:
(A) Bone Marrow
(B) Thymus gland
(C) Lymph nodes
(D) More than one of the above
(E) None of the above

---

**Q29.** The type of immunity provided by B-cells through antibody production is called:
(A) Cell-mediated immunity
(B) Humoral immunity
(C) Innate immunity
(D) More than one of the above
(E) None of the above

---

**Q30.** HIV (Human Immunodeficiency Virus) primarily attacks which cells?
(A) B-lymphocytes
(B) Natural Killer (NK) cells
(C) Helper T-cells (CD4+ T-cells)
(D) More than one of the above
(E) None of the above

---

**Q31.** Antibodies (immunoglobulins) are produced by:
(A) T-lymphocytes
(B) Macrophages
(C) Plasma cells (derived from B-cells)
(D) More than one of the above
(E) None of the above

---

**Q32.** VACCINATION provides which type of immunity?
(A) Passive Natural immunity
(B) Passive Artificial immunity
(C) Active Artificial immunity
(D) More than one of the above
(E) None of the above

---

**Q33.** A mother's antibodies passing to her baby through the PLACENTA during pregnancy is an example of:
(A) Active Natural immunity
(B) Passive Natural immunity
(C) Active Artificial immunity
(D) More than one of the above
(E) None of the above

---

**Q34.** Anti-snake venom (antivenom) injection given to a snakebite victim is an example of:
(A) Active Artificial immunity
(B) Active Natural immunity
(C) Passive Artificial immunity
(D) More than one of the above
(E) None of the above

---

**Q35.** Which type of immunoglobulin (antibody) is found in body secretions like saliva, tears, and breast milk?
(A) IgG
(B) IgM
(C) IgA
(D) More than one of the above
(E) None of the above

---

**Q36.** The FIRST antibody produced during a PRIMARY immune response is:
(A) IgG
(B) IgM
(C) IgA
(D) More than one of the above
(E) None of the above

---

**Q37.** Which antibody is involved in ALLERGIC REACTIONS and defence against parasites?
(A) IgG
(B) IgD
(C) IgE
(D) More than one of the above
(E) None of the above

---

**Q38.** CYTOTOXIC T-CELLS (Killer T-cells) kill infected cells by releasing:
(A) Antibodies and interferons
(B) Perforin (punches holes in cell membrane) and Granzymes (trigger cell death)
(C) Lysozyme and complement proteins
(D) More than one of the above
(E) None of the above

---

**Q39.** Which cells of the immune system are responsible for MEMORY — ensuring faster response on re-exposure to the same pathogen?
(A) Neutrophils
(B) Memory B-cells and Memory T-cells
(C) Natural Killer (NK) cells
(D) More than one of the above
(E) None of the above

---

**Q40.** MACROPHAGES in the immune system serve which function?
(A) Produce antibodies for humoral immunity
(B) Engulf and destroy foreign particles (phagocytosis) and present antigens to T-cells
(C) Directly kill cancer cells using perforin
(D) More than one of the above
(E) None of the above

---

**Q41.** The enzyme LYSOZYME, found in tears, saliva, and sweat, provides innate immunity by:
(A) Producing antibodies against bacteria
(B) Breaking down and destroying bacterial cell walls
(C) Stimulating B-cells to produce immunoglobulins
(D) More than one of the above
(E) None of the above

---

**Q42.** "Bursa of Fabricius" is associated with which cells in birds?
(A) T-lymphocytes (T-cells)
(B) Natural Killer cells
(C) B-lymphocytes (B-cells) — where they were first discovered to mature in birds
(D) More than one of the above
(E) None of the above

---

**Q43.** INTERFERON, an important component of innate immunity, is:
(A) An antibody produced by B-cells against viruses
(B) A protein secreted by virus-infected cells to warn neighbouring cells and inhibit viral replication
(C) A type of T-cell that directly kills virus-infected cells
(D) More than one of the above
(E) None of the above

---

**Q44.** The SECONDARY immune response (upon re-exposure to the same antigen) compared to the primary response is:
(A) Slower and weaker (body must start from scratch)
(B) Faster and stronger (memory cells are activated quickly)
(C) Identical — there is no difference between primary and secondary response
(D) More than one of the above
(E) None of the above

---

**Q45.** NATURAL KILLER (NK) cells are part of which branch of immunity?
(A) Adaptive (acquired) immunity — they need to learn the antigen first
(B) Innate (non-specific) immunity — they kill without needing prior sensitisation
(C) Humoral immunity — they work through antibodies
(D) More than one of the above
(E) None of the above

---

**Q46.** Which T-cell type is known as the "commander" of the adaptive immune response, activating both B-cells and cytotoxic T-cells?
(A) Cytotoxic T-cells (CD8+)
(B) Regulatory T-cells (Tregs)
(C) Helper T-cells (CD4+)
(D) More than one of the above
(E) None of the above

---

**Q47.** The four cardinal signs of INFLAMMATION (innate immune response) are:
(A) Fever, chills, sweating, fatigue
(B) Rubor (redness), Calor (warmth), Tumor (swelling), Dolor (pain)
(C) Antibodies, T-cells, B-cells, NK cells
(D) More than one of the above
(E) None of the above

---

**Q48.** IgG is the most clinically important antibody because:
(A) It is only found in saliva and tears
(B) It is the most abundant antibody in blood and provides the major protection in the secondary immune response
(C) It is only produced during the primary immune response
(D) More than one of the above
(E) None of the above

---

**Q49.** Which immune cell type directly kills VIRUS-INFECTED cells and CANCER cells without requiring prior antibody production?
(A) B-cells via antibody-dependent cytotoxicity only
(B) Neutrophils (primarily kill bacteria, not virus-infected cells)
(C) Both Natural Killer (NK) cells (innate) AND Cytotoxic T-cells (adaptive)
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following statements about immunity:
I.   B-cells mature in Bone Marrow and produce antibodies for humoral immunity.
II.  T-cells mature in the Thymus and mediate cell-mediated immunity.
III. HIV targets and destroys Helper T-cells (CD4+ cells), collapsing the immune response.
IV.  Vaccination provides Active Artificial immunity by introducing antigens to stimulate immune memory.

How many of the above statements are CORRECT?
(A) Only I and II
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
| 1 | (B) | ORDER BY default = ASC (Ascending) — most tested PYQ |
| 2 | (C) | WHERE filters rows BEFORE grouping |
| 3 | (B) | HAVING filters GROUPS after GROUP BY |
| 4 | (C) | COMPUTE is NOT a standard aggregate function; COUNT/SUM/AVG/MAX/MIN are valid |
| 5 | (B) | DISTINCT shows each unique City once (removes duplicates) |
| 6 | (B) | No ASC/DESC specified → default is ASC (65 first, 95 last) |
| 7 | (C) | MAX(Marks) returns the highest value |
| 8 | (B) | COUNT(*) cannot be in WHERE — aggregate functions need HAVING after GROUP BY |
| 9 | (B) | WITH clause = CTE = temporary named result set, not permanently stored |
| 10 | (B) | UNION is a SET OPERATION combining queries; it is NOT a constraint |
| 11 | (B) | COUNT(*) = all rows; COUNT(col) = only non-NULL values |
| 12 | (C) | HAVING AVG > 80 filters entire departments by their average marks |
| 13 | (C) | CHECK is a valid constraint; UNION is a set operation, not a constraint |
| 14 | (C) | '%a%' = contains 'a' anywhere (% = zero or more chars on either side) |
| 15 | (B) | Execution: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY |
| 16 | (B) | BETWEEN is INCLUSIVE — includes both boundary values (80 and 90) |
| 17 | (B) | SUM(Marks) calculates TOTAL marks; COUNT gives count, AVG gives average |
| 18 | (B) | R_vi: R + exactly one char + vi = 4 chars (Ravi, Revi, etc.) |
| 19 | (B) | AVG ignores NULL values — only averages non-NULL values |
| 20 | (C) | UNION (without ALL) automatically removes duplicate rows |
| 21 | (B) | ORDER BY Students DESC = most students first; no HAVING so no filtering |
| 22 | (B) | NOT DeptID = 'CS' equivalent to DeptID != 'CS' |
| 23 | (B) | WHERE runs before GROUP BY; at that stage, groups don't exist yet |
| 24 | (B) | MAX-MIN = Range = 95-65 = 30 (spread of marks) |
| 25 | (C) | Subquery (SELECT AVG(Marks) FROM STUDENTS) needed; can't use AVG directly in WHERE |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Innate = present from birth, non-specific |
| 27 | (C) | B-cells mature in BONE MARROW (in mammals) |
| 28 | (B) | T-cells mature in THYMUS gland |
| 29 | (B) | B-cells → antibodies → HUMORAL immunity (in blood/body fluids) |
| 30 | (C) | HIV targets HELPER T-CELLS (CD4+ cells) → destroys immune coordination |
| 31 | (C) | PLASMA CELLS (derived from activated B-cells) produce antibodies |
| 32 | (C) | Vaccination = Active Artificial immunity (body produces own antibodies) |
| 33 | (B) | Mother → baby through placenta = PASSIVE NATURAL immunity |
| 34 | (C) | Antivenom = ready-made antibodies given = PASSIVE ARTIFICIAL immunity |
| 35 | (C) | IgA = secretory immunoglobulin in saliva, tears, milk, mucus |
| 36 | (B) | IgM = first antibody produced in primary response (large, in blood) |
| 37 | (C) | IgE = involved in ALLERGIES and anti-parasite defence |
| 38 | (B) | Cytotoxic T-cells use PERFORIN (punches holes) + GRANZYMES (trigger death) |
| 39 | (B) | Memory B-cells and Memory T-cells enable faster secondary response |
| 40 | (B) | Macrophages = phagocytosis + antigen presentation to T-cells |
| 41 | (B) | Lysozyme breaks down bacterial cell walls (peptidoglycan) |
| 42 | (C) | Bursa of Fabricius in birds = where B-cells were discovered to mature (hence "B") |
| 43 | (B) | Interferon = anti-viral protein secreted by infected cells |
| 44 | (B) | Secondary response = faster + stronger due to memory cells |
| 45 | (B) | NK cells = innate immunity; kill without prior sensitisation |
| 46 | (C) | Helper T-cells (CD4+) = commanders of adaptive immune response |
| 47 | (B) | Rubor, Calor, Tumor, Dolor = 4 cardinal signs of inflammation |
| 48 | (B) | IgG = most abundant in blood = main protection in secondary response |
| 49 | (C) | NK cells (innate) AND Cytotoxic T-cells (adaptive) both kill infected/cancer cells |
| 50 | (C) | All four statements I, II, III, IV are correct |

---
---

# 🔁 DAY 41 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — SQL SELECT

### The Golden Rule: Execution Order
```
WE WRITE:   SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
SQL RUNS:   FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
"From Where Groups Have Select Order" (mnemonic)
```

### Clause Comparison — 3-Second Version:
```
WHERE  = Filter ROWS before grouping | NO aggregate functions allowed
HAVING = Filter GROUPS after GROUP BY | Aggregate functions REQUIRED/ALLOWED
ORDER BY = Sort final result | DEFAULT = ASC (ascending)
GROUP BY = Cluster rows | Use with aggregate functions
DISTINCT = Remove duplicate rows from output
```

### Aggregate Functions — The 5 Valid:
```
COUNT() → count rows/values (COUNT(*) includes NULL; COUNT(col) excludes NULL)
SUM()   → total of values
AVG()   → average (ignores NULLs)
MAX()   → highest value
MIN()   → lowest value

NOT aggregate: COMPUTE (PYQ trap!) | MULTIPLY | DIVIDE
```

### PYQ One-Liners:
```
✅ ORDER BY default = ASC (ascending)
✅ COMPUTE is NOT a valid aggregate function
✅ UNION is a SET OPERATION, NOT a constraint
✅ COUNT(*) ≠ COUNT(col): * includes NULL rows; col ignores NULL
✅ HAVING comes AFTER GROUP BY; WHERE comes BEFORE
✅ Cannot use aggregate in WHERE clause → use HAVING instead
✅ WITH clause = CTE = TEMPORARY relation (not permanent)
✅ BETWEEN is INCLUSIVE (includes both boundary values)
✅ % = multiple chars; _ = exactly one char (LIKE patterns)
```

---

## ⚡ RAPID FIRE — Immunity & Lymphocytes

### B vs T — 5-Second Comparison:
```
B-cells:
  Mature in BONE MARROW
  Make ANTIBODIES = HUMORAL immunity
  Fight free pathogens in blood/fluids

T-cells:
  Mature in THYMUS
  CELL-MEDIATED immunity (direct killing)
  Types: Helper (CD4+ = HIV target), Cytotoxic (killer), Regulatory, Memory
```

### Immunity Types Flash:
```
INNATE = Inborn, Non-specific, Fast, No memory
         Barriers (skin, mucus), Phagocytes (neutrophils, macrophages), NK cells
         
ADAPTIVE = Acquired, Specific, Slower, HAS MEMORY
           B-cells (humoral) + T-cells (cell-mediated)

ACTIVE = Body makes own antibodies (longer lasting, has memory)
  Natural Active = After infection | Artificial Active = VACCINATION

PASSIVE = Ready-made antibodies given (faster but NO memory, temporary)
  Natural Passive = Mother → baby (placenta/milk) | Artificial Passive = Antivenom
```

### Antibody Types:
```
IgG = Most abundant in blood; secondary response protection
IgM = FIRST in primary response; large pentameric structure
IgA = SECRETIONS (saliva, tears, breast milk) 
IgE = ALLERGIES + anti-parasite
IgD = On B-cell surface as receptor
```

### Key PYQ Facts:
```
HIV → destroys HELPER T-CELLS (CD4+) → AIDS
Plasma cells → produce antibodies (derived from B-cells)
Lysozyme → enzyme in tears/saliva → breaks bacterial walls
Interferon → anti-viral innate protein
NK cells → innate; kill cancer + infected cells without prior learning
Memory cells → basis of VACCINATION effectiveness
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **SQL execution order**: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY; ORDER BY default = ASC; HAVING filters groups (after GROUP BY); WHERE filters rows (before GROUP BY).
2. **Aggregate functions**: COUNT, SUM, AVG, MAX, MIN are valid; COMPUTE is NOT valid; COUNT(*) includes NULL rows, COUNT(col) excludes NULLs; AVG ignores NULLs.
3. **SQL traps**: UNION = set operation (NOT a constraint); WITH clause = temporary CTE; aggregate functions CANNOT go in WHERE clause; BETWEEN is inclusive.
4. **B-cells vs T-cells**: B-cells mature in Bone Marrow → make Antibodies (humoral immunity); T-cells mature in Thymus → direct killing (cell-mediated); HIV targets Helper T-cells (CD4+).
5. **Immunity types**: Vaccination = Active Artificial; Antivenom = Passive Artificial; Mother → baby = Passive Natural; After infection = Active Natural; IgM = first in primary response; IgG = most abundant in blood.

---

## 📅 DAY 42 PREVIEW — What's Coming Next:
**CS**: Operating System Basics — What is OS, Functions, Types of OS (Batch, Time-sharing, Real-time, Distributed, Embedded), Process Management (Process, Thread, States), CPU Scheduling algorithms overview
**GS**: Indian Polity — Fundamental Rights: Right to Equality (Articles 14-18), Right to Freedom (Articles 19-22), with focus on Bihar-specific applications and Article 32 (Dr. Ambedkar's "Heart and Soul" of the Constitution)

---

*🚀 Day 41 of 170 — You're 24.1% through! SQL SELECT queries and aggregate functions appear in almost every BPSC CS paper. The ORDER BY default (ASC) and COMPUTE-not-valid traps are golden PYQ facts worth memorising firmly. You're building excellent DBMS mastery!*
