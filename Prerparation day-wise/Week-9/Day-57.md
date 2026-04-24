# 📅 BPSC TRE 4.0 — DAY 57 COMPLETE STUDY MODULE
### SQL Advanced: Views, Joins & Subqueries + Indian Polity — State Legislature
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): SQL — Views, All Join Types, Subqueries, ROUND function, SQL Hierarchy
> - Afternoon (1 hr): Polity — State Legislature (Vidhan Sabha, Vidhan Parishad, Governor)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 SQL Advanced — Views, Joins, Subqueries & Key Functions

---

## 🔷 SECTION 1: SQL Views — Virtual Tables

### What is a View?

Think of a view like a **window in a wall**. The window doesn't CREATE a room — it just gives you a specific, controlled look INTO the room. The room itself (the actual data) is unchanged, but the view frames exactly what you want to see.

> **A SQL View is a VIRTUAL TABLE based on the result of a SELECT query. It does NOT store data itself — it stores only the query definition.**

```
REAL TABLE (actual data stored on disk):
  ┌────────────────────────────────────────────────┐
  │ TABLE: employees                                │
  │ emp_id │ name    │ dept    │ salary │ location  │
  │ 101    │ Rahul   │ CS      │ 60000  │ Patna     │
  │ 102    │ Priya   │ HR      │ 45000  │ Delhi     │
  │ 103    │ Amit    │ CS      │ 75000  │ Patna     │
  │ 104    │ Sneha   │ Finance │ 55000  │ Mumbai    │
  └────────────────────────────────────────────────┘

VIEW (virtual table — only the query is stored):
  CREATE VIEW cs_employees AS
  SELECT emp_id, name, salary
  FROM employees
  WHERE dept = 'CS';

  RESULT OF VIEW:
  ┌────────────────────────┐
  │ VIEW: cs_employees      │
  │ emp_id │ name  │ salary │
  │ 101    │ Rahul │ 60000  │
  │ 103    │ Amit  │ 75000  │
  └────────────────────────┘

  ↑ This is NOT stored as a table.
    Every time you query cs_employees,
    SQL RUNS the underlying SELECT afresh.
```

### Key Properties of Views:

```
PROPERTY 1 — VIRTUAL TABLE:
  → A view is NOT a real table. It has NO physical storage.
  → It is simply a SAVED SELECT QUERY with a name.
  → When queried, the underlying SELECT runs and returns results.

PROPERTY 2 — SIMPLIFICATION:
  → Complex joins or filters can be wrapped into a view.
  → End users query the simple view instead of writing complex SQL.
  → Example: HR sees only HR-relevant columns; Finance sees only financial data.

PROPERTY 3 — SECURITY:
  → Restrict columns visible to a user (hide salary, SSN, etc.)
  → Users can be given access to VIEW without access to base table.

PROPERTY 4 — UPDATABLE VIEWS (limited):
  → Some simple views can be updated (INSERT/UPDATE/DELETE)
  → Views with GROUP BY, DISTINCT, aggregate functions = NOT updatable

PROPERTY 5 — SYNTAX:
  CREATE VIEW view_name AS
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition;

  DROP VIEW view_name;   ← to delete a view
  
  Query a view exactly like a table:
  SELECT * FROM cs_employees;
```

### 🎯 PYQ FACTS:
```
✅ View = VIRTUAL TABLE (most tested fact!)
✅ View does NOT store data — only stores the query definition
✅ View provides SECURITY by hiding sensitive columns
✅ View simplifies COMPLEX QUERIES
✅ Views with GROUP BY, DISTINCT, aggregate functions = NOT updatable
🚨 TRAP: "A view stores data like a table" → FALSE! View = VIRTUAL, no physical storage.
🚨 TRAP: "All views can be updated" → FALSE! Only simple views (without GROUP BY/DISTINCT) can be updated.
```

---

## 🔷 SECTION 2: SQL Joins — Combining Tables

### Why Do Joins Exist?

In a well-designed relational database, data is **spread across multiple tables** to avoid redundancy. Joins bring related data BACK together when you need it.

```
TWO TABLES:

TABLE: students                     TABLE: courses
┌──────┬─────────┬──────────┐       ┌──────────┬──────────────┬────────┐
│ s_id │ name    │ course_id│       │ course_id│ course_name  │ marks  │
├──────┼─────────┼──────────┤       ├──────────┼──────────────┼────────┤
│ 1    │ Rahul   │ C101     │       │ C101     │ Data Struct  │ 85     │
│ 2    │ Priya   │ C102     │       │ C102     │ Networks     │ 90     │
│ 3    │ Amit    │ C103     │       │ C104     │ OS           │ 78     │
│ 4    │ Sneha   │ NULL     │
└──────┴─────────┴──────────┘

NOTE: Amit (C103) has no matching course. Sneha has no course_id.
      C104 (OS) has no student enrolled.
      These "missing matches" show the DIFFERENCE between join types.
```

---

### TYPE 1: INNER JOIN (Most Common)

```
DEFINITION: Returns ONLY rows where there is a MATCH in BOTH tables.
            Unmatched rows from EITHER side are excluded.

VENN DIAGRAM:
           students        courses
          ┌─────────┐     ┌─────────┐
          │  only   │▓▓▓▓▓│  only   │
          │students │▓▓▓▓▓│ courses │
          └─────────┘     └─────────┘
                    ↑
              ONLY THE INTERSECTION (matching rows)

SYNTAX:
  SELECT students.name, courses.course_name, courses.marks
  FROM students
  INNER JOIN courses ON students.course_id = courses.course_id;

RESULT:
  ┌─────────┬──────────────┬───────┐
  │ name    │ course_name  │ marks │
  ├─────────┼──────────────┼───────┤
  │ Rahul   │ Data Struct  │ 85    │
  │ Priya   │ Networks     │ 90    │
  └─────────┴──────────────┴───────┘
  (Amit → no match in courses; Sneha → NULL course; OS → no student → all excluded)

REAL-LIFE ANALOGY: "Show me ONLY students who ARE enrolled in SOME course."
```

---

### TYPE 2: LEFT JOIN (LEFT OUTER JOIN)

```
DEFINITION: Returns ALL rows from the LEFT table + matching rows from RIGHT.
            If no match in right table → NULL values for right table columns.

VENN DIAGRAM:
           students        courses
          ┌─────────┐     ┌─────────┐
          │▓▓▓▓▓▓▓▓▓│▓▓▓▓▓│         │
          │  ALL    │▓▓▓▓▓│ matched │
          │students │     │ courses │
          └─────────┘     └─────────┘
                ↑
          ALL LEFT + intersection

SYNTAX:
  SELECT students.name, courses.course_name
  FROM students
  LEFT JOIN courses ON students.course_id = courses.course_id;

RESULT:
  ┌─────────┬──────────────┐
  │ name    │ course_name  │
  ├─────────┼──────────────┤
  │ Rahul   │ Data Struct  │
  │ Priya   │ Networks     │
  │ Amit    │ NULL         │  ← Amit has no match → NULL
  │ Sneha   │ NULL         │  ← Sneha has NULL course_id → NULL
  └─────────┴──────────────┘
  (OS / C104 is excluded — it belongs to the RIGHT table)

REAL-LIFE ANALOGY: "Show me ALL students — whether enrolled or not."
```

---

### TYPE 3: RIGHT JOIN (RIGHT OUTER JOIN)

```
DEFINITION: Returns ALL rows from the RIGHT table + matching rows from LEFT.
            If no match in left table → NULL values for left table columns.

VENN DIAGRAM:
           students        courses
          ┌─────────┐     ┌─────────┐
          │         │▓▓▓▓▓│▓▓▓▓▓▓▓▓▓│
          │ matched │▓▓▓▓▓│   ALL   │
          │students │     │ courses │
          └─────────┘     └─────────┘
                                ↑
                    intersection + ALL RIGHT

SYNTAX:
  SELECT students.name, courses.course_name
  FROM students
  RIGHT JOIN courses ON students.course_id = courses.course_id;

RESULT:
  ┌─────────┬──────────────┐
  │ name    │ course_name  │
  ├─────────┼──────────────┤
  │ Rahul   │ Data Struct  │
  │ Priya   │ Networks     │
  │ NULL    │ OS           │  ← OS/C104 has no enrolled student → NULL
  └─────────┴──────────────┘
  (Amit, Sneha excluded — they belong to LEFT table only)

REAL-LIFE ANALOGY: "Show me ALL courses — whether students enrolled or not."
```

---

### TYPE 4: FULL OUTER JOIN (FULL JOIN)

```
DEFINITION: Returns ALL rows from BOTH tables.
            Where there's no match → NULL values for the missing side.

VENN DIAGRAM:
           students        courses
          ┌─────────┐     ┌─────────┐
          │▓▓▓▓▓▓▓▓▓│▓▓▓▓▓│▓▓▓▓▓▓▓▓▓│
          │   ALL   │▓▓▓▓▓│   ALL   │
          │students │     │ courses │
          └─────────┘     └─────────┘
               ↑              ↑
          EVERYTHING — ALL ROWS from both sides

SYNTAX:
  SELECT students.name, courses.course_name
  FROM students
  FULL OUTER JOIN courses ON students.course_id = courses.course_id;

RESULT:
  ┌─────────┬──────────────┐
  │ name    │ course_name  │
  ├─────────┼──────────────┤
  │ Rahul   │ Data Struct  │
  │ Priya   │ Networks     │
  │ Amit    │ NULL         │  ← Amit: unmatched left
  │ Sneha   │ NULL         │  ← Sneha: unmatched left
  │ NULL    │ OS           │  ← OS: unmatched right
  └─────────┴──────────────┘

REAL-LIFE ANALOGY: "Show me ALL students AND ALL courses — matched or not."
```

---

### TYPE 5: CROSS JOIN (Cartesian Product)

```
DEFINITION: Returns EVERY combination of rows from BOTH tables.
            Result = m × n rows (m rows from table1, n rows from table2).
            NO JOIN condition required.

SYNTAX:
  SELECT students.name, courses.course_name
  FROM students
  CROSS JOIN courses;

RESULT: 4 students × 3 courses = 12 rows
  (Rahul, Data Struct), (Rahul, Networks), (Rahul, OS),
  (Priya, Data Struct), (Priya, Networks), (Priya, OS),
  (Amit, Data Struct), (Amit, Networks), (Amit, OS),
  (Sneha, Data Struct), (Sneha, Networks), (Sneha, OS)

REAL-LIFE ANALOGY: "Match EVERY student with EVERY course — regardless of enrollment."
USAGE: Used in scenarios requiring all combinations (testing, scheduling).
```

---

### TYPE 6: SELF JOIN

```
DEFINITION: A table joined with ITSELF.
            Useful for hierarchical data (employee → manager).

SYNTAX:
  SELECT e1.name AS employee, e2.name AS manager
  FROM employees e1
  INNER JOIN employees e2 ON e1.manager_id = e2.emp_id;

USAGE: Organization charts, finding pairs within same table.
```

---

### Join Summary Table:

```
┌─────────────────────┬────────────────────────────────────────────────────────────┐
│   JOIN TYPE         │   WHAT IT RETURNS                                          │
├─────────────────────┼────────────────────────────────────────────────────────────┤
│ INNER JOIN          │ Only MATCHING rows from BOTH tables                        │
├─────────────────────┼────────────────────────────────────────────────────────────┤
│ LEFT (OUTER) JOIN   │ ALL rows from LEFT + matching from RIGHT (NULL if no match)│
├─────────────────────┼────────────────────────────────────────────────────────────┤
│ RIGHT (OUTER) JOIN  │ ALL rows from RIGHT + matching from LEFT (NULL if no match)│
├─────────────────────┼────────────────────────────────────────────────────────────┤
│ FULL (OUTER) JOIN   │ ALL rows from BOTH tables (NULL where no match)            │
├─────────────────────┼────────────────────────────────────────────────────────────┤
│ CROSS JOIN          │ Cartesian product — EVERY combination (m × n rows)        │
├─────────────────────┼────────────────────────────────────────────────────────────┤
│ SELF JOIN           │ Table joined with itself (hierarchical/recursive data)     │
└─────────────────────┴────────────────────────────────────────────────────────────┘
```

### 🎯 PYQ FACTS — Joins:
```
✅ INNER JOIN = intersection only (most common join)
✅ LEFT JOIN = ALL from left + matched from right
✅ RIGHT JOIN = ALL from right + matched from left
✅ FULL OUTER JOIN = ALL from both tables
✅ CROSS JOIN = Cartesian product (no WHERE/ON condition)
🚨 TRAP: "LEFT JOIN excludes unmatched left rows" → FALSE! LEFT JOIN includes ALL left rows.
🚨 TRAP: "INNER JOIN returns all rows" → FALSE! Only MATCHED rows are returned.
🚨 TRAP: "CROSS JOIN requires a JOIN condition" → FALSE! Cross join has NO condition.
```

---

## 🔷 SECTION 3: Subqueries

### What is a Subquery?

A **query within a query**. The inner query (subquery) runs first; its result is used by the outer query.

```
REAL-LIFE ANALOGY:
  "Find all students who scored higher than the CLASS AVERAGE."
  
  Step 1: Calculate the class average first.  ← INNER QUERY (subquery)
  Step 2: Find students above that average.   ← OUTER QUERY

  SQL:
  SELECT name, marks
  FROM students
  WHERE marks > (SELECT AVG(marks) FROM students);  ← subquery in parentheses

  The subquery (SELECT AVG(marks)...) runs FIRST,
  returns a single value (say, 72),
  then outer query becomes: WHERE marks > 72
```

### Types of Subqueries:

```
TYPE 1 — SCALAR SUBQUERY:
  Returns a SINGLE VALUE (one row, one column).
  Used in WHERE, HAVING, or SELECT clause.
  
  Example:
  SELECT name FROM students
  WHERE salary = (SELECT MAX(salary) FROM employees);
                  ↑ returns one value (max salary)

─────────────────────────────────────────────────────

TYPE 2 — ROW SUBQUERY:
  Returns a SINGLE ROW (one row, multiple columns).
  
  Example:
  SELECT * FROM employees
  WHERE (dept, salary) = (SELECT dept, salary FROM employees WHERE emp_id = 101);

─────────────────────────────────────────────────────

TYPE 3 — COLUMN SUBQUERY (Table Subquery):
  Returns MULTIPLE ROWS (single column).
  Used with IN, ANY, ALL operators.
  
  Example: Find students enrolled in courses offered by CS dept.
  SELECT name FROM students
  WHERE course_id IN (SELECT course_id FROM courses WHERE dept = 'CS');
                     ↑ returns multiple course_ids

─────────────────────────────────────────────────────

TYPE 4 — CORRELATED SUBQUERY:
  The inner query REFERENCES the outer query.
  Executes ONCE FOR EACH ROW of the outer query.
  (Unlike non-correlated which runs ONCE)
  
  Example: Find all employees who earn more than the AVERAGE of their OWN DEPARTMENT:
  
  SELECT e1.name, e1.salary, e1.dept
  FROM employees e1
  WHERE e1.salary > (
      SELECT AVG(e2.salary)          ← inner query
      FROM employees e2
      WHERE e2.dept = e1.dept        ← e1.dept references OUTER query!
  );

  NOTICE: e1.dept inside inner query is from the OUTER query → CORRELATED.
  This runs once per outer row — can be slower but very powerful.
```

### Subquery vs JOIN — When to use which?

```
USE SUBQUERY WHEN:
  → Result needed is an aggregate (MAX, MIN, AVG, COUNT)
  → Checking existence (EXISTS clause)
  → Logic flows naturally as "first find X, then find Y where condition = X"

USE JOIN WHEN:
  → You need columns from BOTH tables in the result
  → Performance matters (joins usually faster than correlated subqueries)
  → Joining on foreign key relationships

🎯 PYQ FACT: Correlated subquery executes once per row of the outer query (NOT just once).
```

---

## 🔷 SECTION 4: ROUND Function — The PYQ Favourite

The `ROUND` function is a **CONFIRMED PYQ topic** — it appears regularly!

### Syntax:
```
ROUND(number, decimal_places)
  → decimal_places > 0: rounds RIGHT of decimal point
  → decimal_places = 0: rounds to nearest integer
  → decimal_places < 0: rounds LEFT of decimal point (tens, hundreds, etc.)
```

### Examples (Memorize These!):

```
ROUND(65.726, 2)  = 65.73   ← rounds to 2 decimal places
ROUND(65.726, 1)  = 65.7    ← rounds to 1 decimal place
ROUND(65.726, 0)  = 66      ← rounds to integer
ROUND(65.726, -1) = 70      ← rounds to NEAREST TEN    ← 🎯 PYQ ANSWER!
ROUND(65.726, -2) = 100     ← rounds to nearest hundred

STEP-BY-STEP for ROUND(65.726, -1):
  -1 means round to nearest 10 (LEFT of decimal)
  65.726 → the tens digit is 6 (in 65)
  The units digit is 5 → round UP the tens digit
  65 → 70
  Answer: 70 ✅

ROUND(34.567, -1):
  34 → tens digit is 3, units is 4 → round DOWN
  34 → 30
  Answer: 30

ROUND(65.726, -2):
  Round to nearest 100 → 65 is closer to 100 than 0 → 100
```

### 🎯 PYQ FACTS:
```
✅ ROUND(65.726, -1) = 70  ← MOST TESTED VARIATION
✅ Negative second argument rounds LEFT of the decimal point
✅ Positive second argument rounds RIGHT of the decimal point
✅ ROUND(65.726, 0) = 66 (rounds up because .7 > .5)
🚨 TRAP: "ROUND(65.726, -1) = 65.7" → FALSE! Negative -1 means tens place.
🚨 TRAP: "ROUND(65.726, -1) = 60" → FALSE! 65 rounded to nearest 10 = 70, not 60.
```

---

## 🔷 SECTION 5: SQL Hierarchy

### The 4-Level Hierarchy (PYQ Confirmed):

```
LEVEL 1: ENVIRONMENT (Cluster)
  → The top-level container
  → A database server/cluster
  
  ↓ contains one or more...

LEVEL 2: CATALOG
  → A named group of schemas
  → Corresponds to a "database" in common usage
  
  ↓ contains one or more...

LEVEL 3: SCHEMA
  → A named group of related database objects
  → Contains tables, views, indexes, stored procedures
  
  ↓ contains...

LEVEL 4: TABLE (and other objects — Views, Indexes, etc.)
  → Actual data stored here

DIAGRAM:
  ENVIRONMENT
    └── CATALOG (e.g., "university_db")
          └── SCHEMA (e.g., "academics", "finance", "hr")
                ├── TABLE: students
                ├── TABLE: courses
                ├── VIEW: cs_students
                └── INDEX: idx_student_id
```

### Memory Aid:
```
"Every Cat Sits Tail-up"
  E → Environment
  C → Catalog
  S → Schema
  T → Table
```

### 🎯 PYQ FACTS:
```
✅ SQL hierarchy: Environment → Catalog → Schema → Table
✅ Catalogs contain SCHEMAS
✅ Schemas contain TABLES and other objects (views, indexes)
🚨 TRAP: "Schema is at the top level" → FALSE! Environment > Catalog > Schema
🚨 TRAP: "Tables contain schemas" → FALSE! Schemas contain tables (opposite!)
```

---

## 🔷 SECTION 6: db_accessadmin Role

This is a **confirmed PYQ topic** from SQL Server administration:

```
db_accessadmin ROLE:
  → A built-in database role in Microsoft SQL Server
  → Members of this role can ADD or REMOVE user IDs (logins)
    from the database
  → Controls who has ACCESS to the database
  → "db_accessadmin" = database access administrator

OTHER COMMON SQL SERVER ROLES (for context):
  db_owner        → Full control over the database
  db_datareader   → Can read ALL tables
  db_datawriter   → Can INSERT, UPDATE, DELETE in ALL tables
  db_accessadmin  → Can ADD/REMOVE user IDs (access control)

🎯 PYQ FACT: db_accessadmin = for adding/removing user IDs from a database
```

---

## 🔷 SECTION 7: Key SQL Clauses — Quick Revision

```
┌────────────────────┬─────────────────────────────────────────────────────────┐
│   CLAUSE / KEYWORD │   KEY FACT                                              │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ ORDER BY default   │ ASC (ascending) — must explicitly write DESC for descend│
├────────────────────┼─────────────────────────────────────────────────────────┤
│ HAVING             │ Used with GROUP BY — filters GROUPS (not individual rows)│
│                    │ Like WHERE but for aggregates (after GROUP BY)           │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ WITH clause        │ Creates a TEMPORARY RELATION (Common Table Expression)  │
│                    │ Valid only within the same query                         │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ COMMIT             │ Makes transaction changes PERMANENT                      │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ ROLLBACK           │ UNDOES all changes since last COMMIT                    │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ SAVEPOINT          │ Sets a point within a transaction to ROLLBACK TO         │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ TRUNCATE           │ Removes ALL rows; CANNOT be rolled back (DDL command)   │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ DELETE             │ Removes specific rows; CAN be rolled back (DML command) │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ DROP               │ Removes the entire TABLE structure + data (DDL command) │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ IN operator        │ Matches against a list of values (used with subqueries) │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ EXISTS             │ Returns TRUE if subquery returns ANY rows               │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ GROUP BY           │ Groups rows sharing a value; use HAVING for conditions  │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ DISTINCT           │ Removes duplicate rows from result                      │
├────────────────────┼─────────────────────────────────────────────────────────┤
│ UNION              │ Combines results of two queries (NOT a SQL constraint!)  │
└────────────────────┴─────────────────────────────────────────────────────────┘

🚨 COMMON PYQ TRAP: "UNION is a SQL constraint" → FALSE! Constraints = PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE, CHECK. UNION is a SET OPERATION.
🚨 TRAP: "COMPUTE is a valid aggregate function" → FALSE! Valid aggregates = COUNT, SUM, AVG, MAX, MIN.
```

---

## 🔷 SECTION 8: PYQ Trap List — SQL (Day 57)

```
🚨 TRAP 1: "A View stores data like a table" → FALSE!
   View = VIRTUAL table — stores query definition, NOT data.

🚨 TRAP 2: "All views are updatable" → FALSE!
   Views with GROUP BY, DISTINCT, aggregate functions are NOT updatable.

🚨 TRAP 3: "INNER JOIN returns all rows from both tables" → FALSE!
   INNER JOIN = ONLY MATCHING rows. FULL JOIN = all rows from both.

🚨 TRAP 4: "LEFT JOIN excludes unmatched rows from left table" → FALSE!
   LEFT JOIN keeps ALL left rows; unmatched right side becomes NULL.

🚨 TRAP 5: "CROSS JOIN requires a join condition" → FALSE!
   CROSS JOIN has NO condition — returns Cartesian product.

🚨 TRAP 6: "ROUND(65.726, -1) = 65.7" → FALSE!
   ROUND(65.726, -1) = 70 (rounds to nearest TEN — not decimal places!)

🚨 TRAP 7: "Correlated subquery runs ONCE" → FALSE!
   Correlated subquery runs ONCE PER ROW of the outer query.

🚨 TRAP 8: "SQL hierarchy: Environment → Table → Schema → Catalog" → FALSE!
   Correct order: Environment → Catalog → Schema → Table

🚨 TRAP 9: "TRUNCATE can be rolled back" → FALSE!
   TRUNCATE is DDL — it CANNOT be rolled back. DELETE can be.

🚨 TRAP 10: "HAVING is used for filtering individual rows" → FALSE!
   HAVING = filtering GROUPS (after GROUP BY). WHERE = filtering rows.
```

---

# PART 2: GENERAL STUDIES
## 🏛️ Indian Polity — State Legislature

---

## 🔷 SECTION 1: Overview — What is State Legislature?

### The Parallel to Parliament:

Just as Parliament is the supreme law-making body at the **national** level, each state has its own **State Legislature** that makes laws at the **state** level.

```
NATIONAL LEVEL:
  PARLIAMENT = President + Rajya Sabha + Lok Sabha

STATE LEVEL:
  STATE LEGISLATURE = Governor + (Vidhan Parishad) + Vidhan Sabha
                                   ↑ NOT all states have this

RELATIONSHIP:
  Parliament → National/Union laws (subjects in Union List + Concurrent List)
  State Legislature → State laws (subjects in State List + Concurrent List)
```

### Constitutional Provisions:
```
PART VI of Constitution → deals with STATES
ARTICLE 168 → Constitution of the State Legislature
  "For every state there shall be a legislature which shall consist of:
   (a) the Governor, and
   (b) in the States of Bihar, Maharashtra, Karnataka, UP, AP, Telangana
       — two Houses (Vidhan Parishad + Vidhan Sabha)
   (c) in other States — one House (only Vidhan Sabha)"

KEY FACT:
  States with BICAMERAL legislature (two houses): 6 states
  → Bihar, Uttar Pradesh, Maharashtra, Karnataka, Andhra Pradesh, Telangana
  
  All other states: UNICAMERAL (only Vidhan Sabha)
  
🎯 BIHAR-SPECIFIC: Bihar has BICAMERAL legislature (both Vidhan Sabha + Vidhan Parishad)
```

---

## 🔷 SECTION 2: VIDHAN SABHA — State Legislative Assembly

### Basic Facts:
```
OFFICIAL NAME:    Legislative Assembly (Vidhan Sabha)
TYPE:             Lower House (direct election)
NATURE:           TEMPORARY — dissolved at end of term or earlier
REPRESENTS:       Directly elected by people of the state

ARTICLE REFERENCE: Article 170, 171, 172, 174
```

### Composition:
```
MAXIMUM STRENGTH:   Not more than 500 members + not less than 60 members
  → 500 = maximum
  → 60 = minimum (EXCEPT for Goa, Sikkim, Puducherry — they have fewer)

SMALLEST VIDHAN SABHA: Sikkim — 32 members
LARGEST VIDHAN SABHA: Uttar Pradesh — 403 members

ELECTED BY: Direct election by adult voters of the state

NOMINATED MEMBERS:
  → Governor can nominate 1 member from Anglo-Indian community
    (but this was also affected by 104th Amendment — effectively lapsed)

QUALIFYING AGE:   Minimum 25 years (same as Lok Sabha)
```

### Term and Dissolution:
```
NORMAL TERM: 5 years from the date of its FIRST SITTING
EXCEPTION 1: Governor can dissolve Vidhan Sabha before 5 years
             (on recommendation of Chief Minister/Council of Ministers)
EXCEPTION 2: Under President's Rule (Article 356) — Vidhan Sabha
             dissolved OR suspended
EXTENSION: During National Emergency — can be extended by 1 year at a time
```

### Key Powers of Vidhan Sabha:
```
1. FINANCIAL POWERS:
   → Money Bills originate ONLY in Vidhan Sabha (NOT Vidhan Parishad)
   → Vidhan Parishad can only suggest changes; Vidhan Sabha's decision is FINAL
   → Budget of the state is presented in Vidhan Sabha

2. GOVERNMENT ACCOUNTABILITY:
   → Council of Ministers is COLLECTIVELY responsible to Vidhan Sabha
   → If Vidhan Sabha passes no-confidence → State government MUST resign
   → Only Vidhan Sabha can pass no-confidence motion (NOT Vidhan Parishad)

3. LEGISLATION:
   → All bills (ordinary + money) pass through Vidhan Sabha
   → In states with Vidhan Parishad, Vidhan Sabha has SUPERIOR powers

PRESIDING OFFICER:
   → SPEAKER of Vidhan Sabha (elected by members)
   → Deputy Speaker (elected by members)

🎯 PYQ FACTS:
  ✅ Vidhan Sabha = Lower House = Temporary (5 years)
  ✅ Minimum age = 25 years (same as Lok Sabha)
  ✅ Maximum members = 500; Minimum = 60
  ✅ Money Bills originate ONLY in Vidhan Sabha
  ✅ State government responsible to Vidhan Sabha
  ✅ Presided by SPEAKER
```

---

## 🔷 SECTION 3: VIDHAN PARISHAD — State Legislative Council

### Basic Facts:
```
OFFICIAL NAME:    Legislative Council (Vidhan Parishad)
TYPE:             Upper House (partly elected, partly nominated)
NATURE:           PERMANENT (like Rajya Sabha — never dissolved as a whole)
EXISTS IN:        Bihar, UP, Maharashtra, Karnataka, Andhra Pradesh, Telangana

ARTICLE REFERENCE: Article 171
```

### Composition:
```
MAXIMUM STRENGTH: 1/3rd of total Vidhan Sabha strength
MINIMUM STRENGTH: 40 members

Example: Bihar Vidhan Sabha = 243 members
         Bihar Vidhan Parishad = max 1/3 of 243 = 75 seats (actually 75)

HOW MEMBERS ARE ELECTED (5 categories — Article 171):
  1/3 → Elected by LOCAL BODIES (municipalities, panchayats)
  1/3 → Elected by MEMBERS OF VIDHAN SABHA
  1/12 → Elected by GRADUATES of at least 3 years standing (within state)
  1/12 → Elected by TEACHERS of secondary schools and above
  1/6 → NOMINATED by Governor (persons with distinguished record in:
          literature, science, art, cooperative movement, social service)

QUALIFYING AGE:   Minimum 30 years (same as Rajya Sabha)
```

### Retirement Mechanism:
```
TERM OF EACH MEMBER: 6 years
RETIREMENT: 1/3rd members retire every 2 YEARS
RESULT: Vidhan Parishad is PERMANENT — never fully dissolved
        (Same mechanism as Rajya Sabha)

ANALOGY with Rajya Sabha:
  Rajya Sabha : Parliament :: Vidhan Parishad : State Legislature
  (Both are permanent upper houses with rotating retirements)
```

### Powers of Vidhan Parishad (LIMITED):
```
WHAT VIDHAN PARISHAD CANNOT DO:
  → CANNOT introduce Money Bills
  → CANNOT pass vote of no-confidence against state government
  → In deadlock on ordinary bills → Vidhan Sabha's will PREVAILS

WHAT HAPPENS WITH ORDINARY BILLS:
  → Bill passed by Vidhan Sabha → sent to Vidhan Parishad
  → Vidhan Parishad can delay by 3 months (first time) + 1 month (second time)
  → Maximum delay = 4 months total
  → After 4 months, bill considered PASSED even without Vidhan Parishad's approval

CREATION / ABOLITION of Vidhan Parishad:
  → Vidhan Sabha passes resolution with SPECIAL MAJORITY
  → Parliament then LEGISLATES to create or abolish the council
  (Parliament's role is required — state alone cannot do it)
```

### Presiding Officer:
```
CHAIRMAN of Vidhan Parishad (elected by members)
— NOT ex-officio (unlike Rajya Sabha where VP is Chairman)

DEPUTY CHAIRMAN also elected by members.
```

---

## 🔷 SECTION 4: Comparison — Vidhan Sabha vs Vidhan Parishad

```
┌──────────────────────────┬──────────────────────────────┬──────────────────────────────┐
│         FEATURE          │       VIDHAN SABHA           │      VIDHAN PARISHAD         │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Official Name            │ Legislative Assembly         │ Legislative Council          │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Type                     │ Lower House                  │ Upper House                  │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Nature                   │ TEMPORARY (5 year term)      │ PERMANENT (never dissolved)  │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Maximum Strength         │ 500 members                  │ 1/3rd of Vidhan Sabha (max)  │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Minimum Strength         │ 60 members                   │ 40 members                   │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Min Age of Member        │ 25 years                     │ 30 years                     │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Term of Members          │ 5 years (or till dissolution)│ 6 years                      │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Election Method          │ Direct election by voters    │ Partly elected, partly       │
│                          │                              │ nominated (5 categories)     │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Presiding Officer        │ SPEAKER (elected by members) │ CHAIRMAN (elected by members)│
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Money Bills              │ Originates ONLY here         │ CANNOT originate             │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ No-Confidence Motion     │ CAN pass it                  │ CANNOT pass it               │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ In deadlock (Ord. Bills) │ Vidhan Sabha PREVAILS        │ Can delay max 4 months       │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Present in               │ ALL states                   │ Only 6 states                │
└──────────────────────────┴──────────────────────────────┴──────────────────────────────┘
```

---

## 🔷 SECTION 5: THE GOVERNOR — Role in State Legislature

### Constitutional Provisions:
```
ARTICLE 153 → There shall be a Governor for each State
ARTICLE 154 → Executive power of State vested in Governor
ARTICLE 163 → Council of Ministers to aid and advise Governor
ARTICLE 168 → Governor is part of State Legislature
```

### Governor's Powers in State Legislature:
```
1. SUMMONING & PROROGUING:
   → Governor SUMMONS the Vidhan Sabha (calls it to meet)
   → Governor PROROGUES the session (ends a session)

2. DISSOLVING VIDHAN SABHA:
   → Governor dissolves Vidhan Sabha on recommendation of
     Chief Minister + Council of Ministers
   → Governor can use DISCRETION if CM has lost majority
   → Can refuse dissolution and recommend President's Rule (Article 356)

3. ADDRESS TO LEGISLATURE:
   → Governor addresses both Houses of State Legislature:
     • At the start of first session after each general election
     • At the start of first session of each year

4. ASSENT TO BILLS:
   → State bills become Acts ONLY after Governor's assent
   → Governor can WITHHOLD assent (reserve for President's consideration)
   → Governor can return (non-money) bills for reconsideration ONCE
   → If returned bill is passed again → Governor MUST give assent

5. NOMINATE MEMBERS:
   → Governor nominates 1/6th members to Vidhan Parishad

IMPORTANT DIFFERENCE FROM PRESIDENT:
  → President acts ONLY on advice of Union Cabinet
  → Governor has some DISCRETIONARY POWERS (e.g., choosing CM when no clear majority,
    dismissing ministry that lost majority, reserving bills for President)

🎯 PYQ FACT: Governor is part of State Legislature but NOT a member of either house.
🎯 PYQ FACT: Governor nominates 1/6th of Vidhan Parishad members.
```

---

## 🔷 SECTION 6: Bihar State Legislature — Special Focus

```
🎯 BIHAR-SPECIFIC FACTS (Frequently asked in BPSC TRE):

BIHAR VIDHAN SABHA:
  → Number of seats: 243 constituencies
  → Unicameral/Bicameral: BICAMERAL (Bihar has Vidhan Parishad too)
  → Present Speaker: (check current — Nand Kishore Yadav as of 2024)

BIHAR VIDHAN PARISHAD:
  → Number of seats: 75
  → Bihar was one of the original states with Vidhan Parishad

IMPORTANT HISTORICAL FACT:
  → Bihar was the FIRST state to have a Legislative Council after independence
  → Bihar Vidhan Sabha constituency map was reorganized after delimitation

CURRENT POSITIONS (as of 2024 — verify before exam):
  → Governor of Bihar: Rajendra Arlekar
  → Chief Minister of Bihar: Nitish Kumar
  → Ruling Alliance: NDA

🚨 Always verify current position-holders before the exam as these change.
```

---

## 🔷 SECTION 7: PYQ Traps — State Legislature

```
🚨 TRAP 1: "All states have Vidhan Parishad" → FALSE!
   Only 6 states have Vidhan Parishad. Most states are UNICAMERAL.

🚨 TRAP 2: "Vidhan Parishad can originate Money Bills" → FALSE!
   Money Bills originate ONLY in Vidhan Sabha (same as Lok Sabha in Parliament).

🚨 TRAP 3: "Minimum age for Vidhan Parishad = 25 years" → FALSE!
   Vidhan Parishad = 30 years; Vidhan Sabha = 25 years.

🚨 TRAP 4: "Vidhan Parishad can pass no-confidence motion" → FALSE!
   No-confidence ONLY in Vidhan Sabha (like Lok Sabha at national level).

🚨 TRAP 5: "Governor is a member of the Vidhan Sabha" → FALSE!
   Governor is PART of State Legislature but NOT a member of any house.

🚨 TRAP 6: "Vidhan Parishad Chairman = Governor" → FALSE!
   Chairman of Vidhan Parishad is ELECTED by its members (unlike Rajya Sabha
   where VP is ex-officio Chairman).

🚨 TRAP 7: "Vidhan Sabha maximum = 545 members" → FALSE!
   Maximum = 500 (Parliament Lok Sabha = 552; confuse-trap!)

🚨 TRAP 8: "State can independently create/abolish Vidhan Parishad" → FALSE!
   Requires: (a) Vidhan Sabha special majority resolution + (b) Parliament legislation.

🚨 TRAP 9: "Vidhan Sabha can be extended indefinitely during National Emergency" → FALSE!
   Can only be extended 1 year at a time (like Lok Sabha).

🚨 TRAP 10: "President's Rule dissolves Rajya Sabha" → FALSE!
   President's Rule (Article 356) suspends/dissolves VIDHAN SABHA, not Rajya Sabha.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: SQL Views, Joins, Subqueries, ROUND, SQL Hierarchy, Key Clauses

---

**Q1.** A SQL VIEW is best described as:
(A) A permanent table that stores a copy of the base table data
(B) A virtual table based on the result of a SELECT statement
(C) A special type of index used to speed up queries
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following statements about SQL Views is CORRECT?
(A) A view stores its own copy of data and updates independently
(B) A view with GROUP BY clause can be directly updated
(C) A view provides security by restricting access to specific columns and rows of a table
(D) More than one of the above
(E) None of the above

---

**Q3.** Which type of SQL JOIN returns ONLY the rows that have matching values in BOTH tables?
(A) LEFT JOIN
(B) FULL OUTER JOIN
(C) INNER JOIN
(D) More than one of the above
(E) None of the above

---

**Q4.** In a LEFT JOIN between Table A (left) and Table B (right), the result will:
(A) Include only rows where both tables have matching values
(B) Include ALL rows from Table A and only matched rows from Table B (with NULLs for no match)
(C) Include ALL rows from Table B and only matched rows from Table A
(D) More than one of the above
(E) None of the above

---

**Q5.** Which SQL JOIN produces the Cartesian product of two tables (every row of Table A paired with every row of Table B)?
(A) INNER JOIN
(B) FULL OUTER JOIN
(C) CROSS JOIN
(D) More than one of the above
(E) None of the above

---

**Q6.** Consider two tables: Employee (10 rows) and Department (5 rows). If you perform a CROSS JOIN between them with no WHERE condition, the result will have:
(A) 10 rows (only matching rows)
(B) 15 rows (sum of both tables)
(C) 50 rows (10 × 5 = Cartesian product)
(D) More than one of the above
(E) None of the above

---

**Q7.** A FULL OUTER JOIN in SQL:
(A) Returns only rows present in both tables
(B) Returns all rows from both tables, with NULLs where there are no matches on either side
(C) Is identical to an INNER JOIN
(D) More than one of the above
(E) None of the above

---

**Q8.** A subquery where the inner query references a column from the OUTER query is called:
(A) A scalar subquery
(B) A nested subquery
(C) A correlated subquery
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the output of the SQL expression: `SELECT ROUND(65.726, -1);`
(A) 65.7
(B) 66
(C) 70
(D) More than one of the above
(E) None of the above

---

**Q10.** What is the output of: `SELECT ROUND(34.567, -1);`
(A) 34.6
(B) 35
(C) 30
(D) More than one of the above
(E) None of the above

---

**Q11.** What does a negative second argument in the SQL ROUND function indicate?
(A) The number is rounded to the given number of decimal places to the right
(B) The number is rounded to the given position to the LEFT of the decimal point (e.g., tens, hundreds)
(C) The function returns a negative number
(D) More than one of the above
(E) None of the above

---

**Q12.** The correct hierarchy of SQL database objects from highest to lowest level is:
(A) Schema → Catalog → Environment → Table
(B) Table → Schema → Catalog → Environment
(C) Environment → Catalog → Schema → Table
(D) More than one of the above
(E) None of the above

---

**Q13.** In the SQL environment hierarchy, a CATALOG contains:
(A) Tables directly (no intermediate structure)
(B) Schemas, which in turn contain tables and other objects
(C) Individual rows of a table
(D) More than one of the above
(E) None of the above

---

**Q14.** The `db_accessadmin` role in SQL Server is used to:
(A) Grant or revoke read/write permissions on specific tables
(B) Add or remove user IDs (logins) from the database
(C) Create and drop databases on the server
(D) More than one of the above
(E) None of the above

---

**Q15.** Which SQL clause is used to FILTER GROUPS (formed by GROUP BY) rather than individual rows?
(A) WHERE
(B) HAVING
(C) DISTINCT
(D) More than one of the above
(E) None of the above

---

**Q16.** The SQL `WITH` clause (Common Table Expression) creates:
(A) A permanent table in the database
(B) A temporary relation/result set usable within the same query
(C) A permanent view stored in the schema
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following is NOT a valid SQL aggregate function?
(A) COUNT
(B) AVG
(C) COMPUTE
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following is a SQL constraint?
(A) UNION
(B) SELECT
(C) PRIMARY KEY
(D) More than one of the above
(E) None of the above

---

**Q19.** The difference between `DELETE` and `TRUNCATE` in SQL is:
(A) DELETE removes specific rows and can be rolled back; TRUNCATE removes all rows and CANNOT be rolled back
(B) TRUNCATE removes specific rows; DELETE removes all rows
(C) Both DELETE and TRUNCATE can be rolled back using ROLLBACK
(D) More than one of the above
(E) None of the above

---

**Q20.** In SQL, the ORDER BY clause — when no order is specified — sorts results in:
(A) Descending order (DESC) by default
(B) Random order
(C) Ascending order (ASC) by default
(D) More than one of the above
(E) None of the above

---

**Q21.** A correlated subquery differs from a non-correlated (regular) subquery because:
(A) It always returns a single value
(B) It executes once per row of the outer query (not just once overall)
(C) It uses INNER JOIN instead of WHERE
(D) More than one of the above
(E) None of the above

---

**Q22.** Which JOIN type should be used when you need to see ALL employees AND ALL departments, including those with no match?
(A) INNER JOIN — returns only matching rows
(B) LEFT JOIN — returns all employees with matched departments
(C) FULL OUTER JOIN — returns all rows from both tables, with NULLs for non-matches
(D) More than one of the above
(E) None of the above

---

**Q23.** Consider: Table X has 3 rows, Table Y has 4 rows. Which JOIN produces the MOST rows in the result (in the worst/maximum case)?
(A) INNER JOIN
(B) FULL OUTER JOIN
(C) CROSS JOIN
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following SQL views would NOT be directly updatable?
(A) A view selecting all columns from a single table with no conditions
(B) A view using GROUP BY and aggregate functions
(C) A view selecting specific columns from one table using WHERE
(D) More than one of the above
(E) None of the above

---

**Q25.** The SQL statement `DELETE FROM teaches;` will:
(A) Drop the entire teaches table including its structure
(B) Delete all ROWS from the teaches table but keep the table structure
(C) Delete the schema containing the teaches table
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: State Legislature — Vidhan Sabha, Vidhan Parishad, Governor, Powers

---

**Q26.** Which Article of the Indian Constitution deals with the Constitution of the State Legislature?
(A) Article 79
(B) Article 112
(C) Article 168
(D) More than one of the above
(E) None of the above

---

**Q27.** Which of the following states has a BICAMERAL legislature (both Vidhan Sabha and Vidhan Parishad)?
(A) Rajasthan
(B) Gujarat
(C) Bihar
(D) More than one of the above
(E) None of the above

---

**Q28.** The MAXIMUM number of members in a Vidhan Sabha (State Legislative Assembly) is:
(A) 250 members
(B) 500 members
(C) 552 members
(D) More than one of the above
(E) None of the above

---

**Q29.** The minimum age required to become a MEMBER OF VIDHAN PARISHAD is:
(A) 21 years
(B) 25 years
(C) 30 years
(D) More than one of the above
(E) None of the above

---

**Q30.** Vidhan Parishad (Legislative Council) is called a "Permanent House" because:
(A) Its members hold permanent tenure for life
(B) It is never dissolved as a whole; 1/3rd members retire every 2 years
(C) It was established before Vidhan Sabha
(D) More than one of the above
(E) None of the above

---

**Q31.** Who is the PRESIDING OFFICER of the Vidhan Parishad?
(A) The Governor of the state (ex-officio)
(B) The Speaker elected from Vidhan Sabha members
(C) The Chairman elected by members of the Vidhan Parishad
(D) More than one of the above
(E) None of the above

---

**Q32.** A Money Bill in a state with bicameral legislature can be introduced ONLY in:
(A) Vidhan Parishad
(B) Either House with the Governor's permission
(C) Vidhan Sabha only
(D) More than one of the above
(E) None of the above

---

**Q33.** The State Council of Ministers is collectively responsible to:
(A) Vidhan Parishad — as it's the Upper House
(B) The Governor of the State
(C) Vidhan Sabha
(D) More than one of the above
(E) None of the above

---

**Q34.** How many members does the GOVERNOR NOMINATE to the Vidhan Parishad?
(A) 12 members
(B) 1/3rd of the total strength
(C) 1/6th of the total strength
(D) More than one of the above
(E) None of the above

---

**Q35.** A no-confidence motion against the State Government (Council of Ministers) can be passed ONLY in:
(A) Vidhan Parishad
(B) A joint session of both Houses
(C) Vidhan Sabha
(D) More than one of the above
(E) None of the above

---

**Q36.** The MAXIMUM strength of Vidhan Parishad is:
(A) 40 members
(B) 1/4th of Vidhan Sabha strength
(C) 1/3rd of Vidhan Sabha strength
(D) More than one of the above
(E) None of the above

---

**Q37.** How can a state CREATE or ABOLISH its Vidhan Parishad?
(A) Vidhan Sabha alone can do it by simple majority vote
(B) The Governor can create or abolish it by ordinance
(C) Vidhan Sabha passes a special majority resolution, then Parliament legislates
(D) More than one of the above
(E) None of the above

---

**Q38.** Bihar's Vidhan Parishad currently has how many members?
(A) 40 members
(B) 63 members
(C) 75 members
(D) More than one of the above
(E) None of the above

---

**Q39.** If a Vidhan Parishad (Upper House) rejects or does not pass an ordinary bill sent by Vidhan Sabha, Vidhan Sabha's will ultimately prevails after a maximum delay of:
(A) 1 month
(B) 6 months
(C) 4 months (3 months first time + 1 month second time)
(D) More than one of the above
(E) None of the above

---

**Q40.** The term of a Vidhan Parishad member is:
(A) 5 years
(B) 6 years
(C) Life (permanent members)
(D) More than one of the above
(E) None of the above

---

**Q41.** Which of the following is a CORRECT statement about the Governor's role in the State Legislature?
(A) Governor is a permanent member of the Vidhan Sabha
(B) Governor is part of State Legislature but NOT a member of either house; summons, prorogues, dissolves Vidhan Sabha
(C) Governor presides over joint sessions of both houses
(D) More than one of the above
(E) None of the above

---

**Q42.** The minimum strength of a Vidhan Sabha is:
(A) 30 members
(B) 60 members
(C) 100 members
(D) More than one of the above
(E) None of the above

---

**Q43.** The minimum age for MEMBERSHIP OF VIDHAN SABHA is:
(A) 18 years
(B) 25 years
(C) 30 years
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following pairs of state legislature vs Parliament is INCORRECTLY matched?
(A) Vidhan Sabha — Lok Sabha
(B) Vidhan Parishad — Rajya Sabha
(C) Governor (State) — Prime Minister (Centre)
(D) More than one of the above
(E) None of the above

---

**Q45.** Consider these statements about Vidhan Parishad membership elections:
I. 1/3rd elected by local bodies (panchayats, municipalities)
II. 1/3rd elected by members of Vidhan Sabha
III. 1/6th nominated by Governor
IV. 1/12th elected by graduates (3+ years standing)
Which are CORRECT as per Article 171?

(A) I and II only
(B) I, II, and III only
(C) All of I, II, III, and IV
(D) More than one of the above
(E) None of the above

---

**Q46.** Under which Article is PRESIDENT'S RULE (imposition on a state) provided?
(A) Article 352
(B) Article 356
(C) Article 360
(D) More than one of the above
(E) None of the above

---

**Q47.** The NORMAL TERM of the Vidhan Sabha is 5 years. However, it can be EXTENDED during:
(A) President's Rule by the Governor
(B) A national emergency, by Parliament for 1 year at a time
(C) By a 2/3 majority vote of Vidhan Sabha itself
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following statements about the Vidhan Parishad Chairman is CORRECT?
(A) The Chairman is the Governor (ex-officio) — like Vice President is for Rajya Sabha
(B) The Chairman is elected by members of the Vidhan Parishad (NOT ex-officio)
(C) The Chief Minister automatically becomes the Vidhan Parishad Chairman
(D) More than one of the above
(E) None of the above

---

**Q49.** In which Indian state is the SMALLEST Vidhan Sabha located?
(A) Goa
(B) Tripura
(C) Sikkim
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about State Legislature:
I. All Indian states have bicameral legislature (both Vidhan Sabha and Vidhan Parishad).
II. Vidhan Parishad cannot be dissolved as a whole.
III. The minimum age for Vidhan Sabha is same as Lok Sabha (25 years).
IV. Vidhan Parishad has superior powers over Money Bills compared to Vidhan Sabha.
Which are CORRECT?

(A) I and IV only
(B) II and III only
(C) I, II, and III only
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (B) | View = virtual table based on SELECT statement — no physical storage |
| 2  | (C) | View provides security by restricting column/row access to users |
| 3  | (C) | INNER JOIN = only matching rows from both tables |
| 4  | (B) | LEFT JOIN = ALL rows from left + matched right rows (NULL if no match) |
| 5  | (C) | CROSS JOIN = Cartesian product (all combinations) |
| 6  | (C) | CROSS JOIN: 10 × 5 = 50 rows |
| 7  | (B) | FULL OUTER JOIN = all rows from both tables with NULLs where no match |
| 8  | (C) | Correlated subquery = inner query references outer query column |
| 9  | (C) | ROUND(65.726, -1) = 70 (negative argument = round to nearest ten) |
| 10 | (C) | ROUND(34.567, -1) = 30 (34 → nearest ten = 30, since units digit 4 < 5) |
| 11 | (B) | Negative second argument rounds to LEFT of decimal (tens, hundreds) |
| 12 | (C) | Correct hierarchy: Environment → Catalog → Schema → Table |
| 13 | (B) | Catalog contains schemas; schemas contain tables and other objects |
| 14 | (B) | db_accessadmin = adds/removes user IDs (logins) from database |
| 15 | (B) | HAVING filters groups (used after GROUP BY); WHERE filters rows |
| 16 | (B) | WITH clause = creates temporary relation valid within the same query |
| 17 | (C) | COMPUTE is NOT a valid aggregate; valid ones = COUNT, SUM, AVG, MAX, MIN |
| 18 | (C) | PRIMARY KEY is a constraint; UNION is a set operation (not a constraint) |
| 19 | (A) | DELETE = can rollback (DML); TRUNCATE = cannot rollback (DDL) |
| 20 | (C) | ORDER BY default = ASC (ascending) |
| 21 | (B) | Correlated subquery executes once per row of outer query |
| 22 | (C) | FULL OUTER JOIN = all employees + all departments + NULLs for no match |
| 23 | (C) | CROSS JOIN produces 3 × 4 = 12 rows (maximum possible) |
| 24 | (B) | View with GROUP BY and aggregates = NOT directly updatable |
| 25 | (B) | DELETE FROM teaches → removes all ROWS; table structure remains |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (C) | Article 168 = Constitution of State Legislature |
| 27 | (C) | Bihar has bicameral legislature (both Vidhan Sabha + Vidhan Parishad) |
| 28 | (B) | Maximum Vidhan Sabha strength = 500 (minimum = 60) |
| 29 | (C) | Vidhan Parishad min age = 30 years (same as Rajya Sabha) |
| 30 | (B) | Permanent = never dissolved; 1/3rd retire every 2 years |
| 31 | (C) | Vidhan Parishad Chairman = ELECTED by members (not ex-officio) |
| 32 | (C) | Money Bills originate ONLY in Vidhan Sabha |
| 33 | (C) | State Council of Ministers collectively responsible to Vidhan Sabha |
| 34 | (C) | Governor nominates 1/6th of Vidhan Parishad members |
| 35 | (C) | No-confidence ONLY in Vidhan Sabha |
| 36 | (C) | Max Vidhan Parishad = 1/3rd of Vidhan Sabha strength |
| 37 | (C) | Vidhan Sabha special majority + Parliament legislation required |
| 38 | (C) | Bihar Vidhan Parishad = 75 members |
| 39 | (C) | Vidhan Sabha prevails after 4 months max delay (3 months + 1 month) |
| 40 | (B) | Vidhan Parishad member term = 6 years |
| 41 | (B) | Governor = part of legislature, not a member; summons/prorogues/dissolves VS |
| 42 | (B) | Minimum Vidhan Sabha strength = 60 members |
| 43 | (B) | Vidhan Sabha minimum age = 25 years |
| 44 | (C) | Governor (state) ≠ Prime Minister (centre); correct parallel is President (centre). Governor ≠ PM role-wise. President pairs with Governor; PM pairs with CM |
| 45 | (C) | All four categories of Vidhan Parishad election (Art. 171) are correct |
| 46 | (B) | Article 356 = President's Rule on states |
| 47 | (B) | Vidhan Sabha can be extended during national emergency by Parliament, 1 year at a time |
| 48 | (B) | Vidhan Parishad Chairman = elected by members (NOT ex-officio unlike Rajya Sabha VP) |
| 49 | (C) | Sikkim = smallest Vidhan Sabha (32 seats) |
| 50 | (B) | II (VP never dissolved) and III (Vidhan Sabha min age = 25) are correct; I is wrong (only 6 states bicameral); IV is wrong (Vidhan Sabha superior in Money Bills) |

---

# 🔁 DAY 57 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — SQL Views, Joins & Subqueries

### SQL View — The 3 Key Facts:
```
VIEW = VIRTUAL TABLE (never stores data — only stores the query)
VIEW purpose = SECURITY (hide sensitive columns) + SIMPLIFICATION (wrap complex queries)
VIEW with GROUP BY / DISTINCT / aggregates = NOT updatable
```

### Joins Quick Reference:
```
JOIN TYPE         │ WHAT IT RETURNS
──────────────────┼─────────────────────────────────────────────────
INNER JOIN        │ ONLY matching rows from BOTH tables
LEFT JOIN         │ ALL left rows + matched right (NULL for no match)
RIGHT JOIN        │ ALL right rows + matched left (NULL for no match)
FULL OUTER JOIN   │ ALL rows from BOTH tables (NULLs where no match)
CROSS JOIN        │ Cartesian product = m × n rows (all combinations)
SELF JOIN         │ Table joined with itself (hierarchy/pairs)
```

### ROUND Function:
```
ROUND(number, d)
  d > 0 → round RIGHT of decimal (decimal places)
  d = 0 → round to integer
  d < 0 → round LEFT of decimal (tens, hundreds, etc.)

EXAMPLES TO MEMORIZE:
  ROUND(65.726, 2)  = 65.73    → 2 decimal places
  ROUND(65.726, -1) = 70       ← 🎯 PYQ FAVORITE (nearest 10)
  ROUND(65.726, -2) = 100      → nearest 100
  ROUND(34.567, -1) = 30       → nearest 10 (4 < 5 → round down)
```

### SQL Hierarchy:
```
"Every Cat Sits Tail-up"
  Environment → Catalog → Schema → Table
```

### PYQ Traps — SQL:
```
✅ View = VIRTUAL (no physical storage)
✅ INNER JOIN = only matching (not all rows)
✅ CROSS JOIN = NO condition required (Cartesian product)
✅ ROUND(65.726, -1) = 70 (NOT 65.7!)
✅ Correlated subquery = once per outer row (not just once)
✅ TRUNCATE = cannot rollback; DELETE = can rollback
✅ HAVING = for groups; WHERE = for rows
✅ UNION = set operation (NOT a constraint!)
✅ db_accessadmin = adds/removes user IDs
```

---

## ⚡ RAPID FIRE — State Legislature

### State Legislature Formula:
```
STATE LEGISLATURE = GOVERNOR + (VIDHAN PARISHAD) + VIDHAN SABHA
                                    ↑ only in 6 states
                                    (Bihar, UP, Maharashtra, Karnataka, AP, Telangana)
(Article 168)
```

### Vidhan Sabha vs Vidhan Parishad Quick Comparison:
```
FEATURE           │ VIDHAN SABHA               │ VIDHAN PARISHAD
──────────────────┼────────────────────────────┼────────────────────────────
Type              │ Lower House                │ Upper House
Nature            │ Temporary (5 yrs)          │ PERMANENT (never dissolved)
Max Strength      │ 500                        │ 1/3rd of Vidhan Sabha
Min Strength      │ 60                         │ 40
Min Age           │ 25 years                   │ 30 years
Member Term       │ 5 years                    │ 6 years
Election          │ Direct (voters)            │ 5 categories (indirect + nominated)
Gov Nominated     │ 1 (Anglo-Indian — lapsed)  │ 1/6th of total strength
Presiding Officer │ SPEAKER (elected members)  │ CHAIRMAN (elected members)
Money Bills       │ ONLY here                  │ CANNOT originate
No-Confidence     │ CAN pass it                │ CANNOT pass it
Present in        │ ALL states                 │ Only 6 states
```

### Bihar-Specific Numbers:
```
Bihar Vidhan Sabha:   243 seats
Bihar Vidhan Parishad: 75 seats
Bihar's legislature: BICAMERAL (one of 6 bicameral states)
```

### PYQ Trap List — State Legislature:
```
✅ Vidhan Parishad Chairman = ELECTED by members (NOT ex-officio)
   (Different from Rajya Sabha where VP is ex-officio Chairman!)
✅ Vidhan Parishad CANNOT be dissolved (Permanent)
✅ Vidhan Parishad min age = 30 years (NOT 25)
✅ Money Bills ONLY in Vidhan Sabha (NOT Vidhan Parishad)
✅ No-confidence motion ONLY in Vidhan Sabha
✅ Max delay by Vidhan Parishad for ordinary bills = 4 months
✅ Governor nominates 1/6th to Vidhan Parishad (NOT 1/3rd!)
✅ Only 6 states have Vidhan Parishad (NOT all states)
✅ Article 356 = President's Rule (suspends/dissolves Vidhan Sabha)
✅ Smallest Vidhan Sabha = Sikkim (32 seats)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **SQL View = VIRTUAL TABLE** — no physical storage; stores only the query definition; provides security + simplification; views with GROUP BY/aggregates are NOT updatable.
2. **Joins**: INNER = only matches; LEFT = all left + matched right; RIGHT = all right + matched left; FULL = all from both; CROSS = m × n Cartesian (no condition). Correlated subquery = once per outer row.
3. **ROUND(65.726, -1) = 70** — negative second argument rounds LEFT of decimal (to nearest ten/hundred). SQL hierarchy: Environment → Catalog → Schema → Table. TRUNCATE ≠ rollback-able; DELETE = rollback-able.
4. **State Legislature (Art. 168)** = Governor + Vidhan Parishad (only 6 states) + Vidhan Sabha; Bihar is BICAMERAL (Vidhan Sabha = 243, Vidhan Parishad = 75).
5. **Vidhan Parishad traps**: Chairman = ELECTED (not ex-officio, unlike RS where VP is chairman); min age = 30 years; Money Bills = Vidhan Sabha only; No-confidence = Vidhan Sabha only; Governor nominates 1/6th; PERMANENT house (never dissolved).

---

## 📅 DAY 58 PREVIEW — What's Coming Next:
**CS**: SQL Transaction Management — ACID Properties (Atomicity, Consistency, Isolation, Durability), COMMIT / ROLLBACK / SAVEPOINT, DELETE vs TRUNCATE vs DROP (detailed), Concurrency Control basics, RAW data type
**GS**: Indian Polity — Fundamental Rights (Articles 12–35): Right to Equality (14–18), Right to Freedom (19–22), Right Against Exploitation (23–24), Right to Constitutional Remedies (Article 32 — "Heart and Soul" of Constitution)

---

*🚀 Day 57 of 170 — SQL Joins and Views are CONFIRMED PYQ topics. ROUND with negative argument is a sneaky trap that appears every paper. Vidhan Parishad's Chairman being ELECTED (not ex-officio) is the #1 trap to remember for today's GS. You're building an unbeatable edge — keep going!*
