# 📅 BPSC TRE 4.0 — DAY 41
## CS Topic: SQL SELECT Query — Clauses, Aggregate Functions, Joins, Subqueries
## GS Topic: Biology — Human Immune System, Lymphocytes, Vaccines & Human Diseases

> **Target:** 130+/150 | Top 50 Rank
> **Today's Focus:** SQL SELECT is the most-tested SQL topic in BPSC TRE. Biology Immunity is HIGH-YIELD for GS.

---

# ═══════════════════════════════════════════════════════
# 📘 PART 1: COMPUTER SCIENCE — SQL SELECT & CLAUSES
# ═══════════════════════════════════════════════════════

## 🎯 Why SQL SELECT Matters

In BPSC TRE exams, SQL SELECT questions test:
- Correct clause ordering (SELECT execution order)
- WHERE vs HAVING (classic trap)
- Aggregate function names (COMPUTE is NOT valid!)
- ORDER BY default direction
- GROUP BY behavior
- DISTINCT keyword
- JOINs (INNER, LEFT, RIGHT, FULL)

---

## 📐 The Complete SELECT Syntax

```sql
SELECT   [DISTINCT] column1, column2, aggregate_function(col)
FROM     table_name / joined_tables
WHERE    row_level_condition         ← filters INDIVIDUAL ROWS
GROUP BY column_name                 ← groups rows
HAVING   group_level_condition       ← filters GROUPS
ORDER BY column_name [ASC | DESC]    ← sorts results
LIMIT    n;                          ← limits number of rows returned
```

### 🔑 THE TWO CRITICAL ORDERS:

```
WRITING ORDER (how you write the query):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT

EXECUTION ORDER (how SQL engine processes it):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

**Memory Trick for Execution Order:** **"For Whales, Groups Have Special Order, Later"**
```
F  → FROM
W  → WHERE
G  → GROUP BY
H  → HAVING
S  → SELECT
O  → ORDER BY
L  → LIMIT
```

---

## 🔵 DISTINCT — Remove Duplicates

```sql
-- Without DISTINCT (shows duplicates)
SELECT City FROM Student;
-- Result: Patna, Patna, Delhi, Mumbai, Patna, Delhi

-- With DISTINCT (removes duplicates)
SELECT DISTINCT City FROM Student;
-- Result: Patna, Delhi, Mumbai
```

```
Table: Student
┌─────────┬──────────┬────────┬───────┐
│ Roll_No │ Name     │ City   │ Marks │
├─────────┼──────────┼────────┼───────┤
│ 101     │ Rohan    │ Patna  │ 85    │
│ 102     │ Priya    │ Delhi  │ 92    │
│ 103     │ Amit     │ Patna  │ 78    │
│ 104     │ Neha     │ Mumbai │ 88    │
│ 105     │ Vijay    │ Delhi  │ 95    │
└─────────┴──────────┴────────┴───────┘

SELECT DISTINCT City FROM Student;
Result:
┌────────┐
│ City   │
├────────┤
│ Patna  │
│ Delhi  │
│ Mumbai │
└────────┘
```

---

## 🟡 WHERE Clause — Filter Individual Rows

```sql
-- Simple condition
SELECT * FROM Student WHERE Marks > 80;

-- Multiple conditions with AND
SELECT Name, Marks FROM Student WHERE City = 'Patna' AND Marks >= 80;

-- Multiple conditions with OR
SELECT Name FROM Student WHERE City = 'Patna' OR City = 'Delhi';

-- BETWEEN operator (inclusive on both ends)
SELECT Name, Marks FROM Student WHERE Marks BETWEEN 75 AND 90;

-- IN operator (checks membership in a list)
SELECT Name FROM Student WHERE City IN ('Patna', 'Delhi', 'Mumbai');

-- NOT IN
SELECT Name FROM Student WHERE City NOT IN ('Chennai', 'Kolkata');

-- LIKE operator (pattern matching)
SELECT Name FROM Student WHERE Name LIKE 'R%';   -- starts with R
SELECT Name FROM Student WHERE Name LIKE '%a';   -- ends with a
SELECT Name FROM Student WHERE Name LIKE '_o%';  -- second char is 'o'

-- IS NULL / IS NOT NULL
SELECT Name FROM Student WHERE Email IS NULL;
SELECT Name FROM Student WHERE Email IS NOT NULL;
```

**LIKE Pattern Characters:**
```
%  →  Matches ANY sequence of characters (including zero)
       'R%'  → Rohan, Riya, Rahul...
       '%a'  → Priya, Neha, Rekha...
       '%oh%'→ Rohan, Mohit...

_  →  Matches exactly ONE character
       '_o%' → Rohan, Mohit (2nd char = o)
       '__a' → 3-letter words ending in a (Riya → No, Mia → Yes)
```

---

## 🟢 GROUP BY — Group Rows for Aggregation

GROUP BY **groups rows with the same value** in a column into summary rows.

```sql
-- Count students in each city
SELECT City, COUNT(*) AS Total_Students
FROM Student
GROUP BY City;
```

```
Input (Student table):          Output (Grouped):
┌─────────┬──────┬────────┐    ┌────────┬────────────────┐
│ Roll_No │ Name │ City   │    │ City   │ Total_Students │
├─────────┼──────┼────────┤    ├────────┼────────────────┤
│ 101     │Rohan │ Patna  │    │ Patna  │ 2              │
│ 102     │Priya │ Delhi  │ ──►│ Delhi  │ 2              │
│ 103     │Amit  │ Patna  │    │ Mumbai │ 1              │
│ 104     │Neha  │ Mumbai │    └────────┴────────────────┘
│ 105     │Vijay │ Delhi  │
└─────────┴──────┴────────┘
```

**More GROUP BY examples:**
```sql
-- Average marks per city
SELECT City, AVG(Marks) AS Avg_Marks
FROM Student
GROUP BY City;

-- Maximum marks in each city
SELECT City, MAX(Marks) AS Top_Marks
FROM Student
GROUP BY City;

-- Count and average together
SELECT City, COUNT(*) AS Count, AVG(Marks) AS Avg
FROM Student
GROUP BY City;
```

---

## 🔴 HAVING — Filter Groups (NOT Individual Rows!)

> **🔔 THE MOST IMPORTANT BPSC PYQ TRAP:**
> - **WHERE** filters INDIVIDUAL ROWS (before grouping)
> - **HAVING** filters GROUPS (after grouping)
> - You CANNOT use aggregate functions in WHERE clause
> - You CAN use aggregate functions in HAVING clause

```
WHERE vs HAVING — Visual Comparison:

ALL ROWS:                          GROUPS:
┌────────────────────────┐         ┌──────────────────────┐
│ 101 Rohan Patna  85    │         │ Patna  → 2 students  │
│ 102 Priya Delhi  92    │──GROUP──►│ Delhi  → 2 students  │
│ 103 Amit  Patna  78    │  BY City │ Mumbai → 1 student   │
│ 104 Neha  Mumbai 88    │         └──────────────────────┘
│ 105 Vijay Delhi  95    │              ↑
└────────────────────────┘         HAVING filters HERE
          ↑
    WHERE filters HERE
    (individual rows)
```

```sql
-- CORRECT: HAVING with aggregate function
SELECT City, COUNT(*) AS Total
FROM Student
GROUP BY City
HAVING COUNT(*) > 1;         -- Shows cities with MORE than 1 student

-- Result: Patna (2), Delhi (2)  [Mumbai excluded — only 1 student]

-- WRONG: Cannot use aggregate in WHERE
SELECT City, COUNT(*) AS Total
FROM Student
WHERE COUNT(*) > 1           -- ERROR! Cannot use COUNT() in WHERE
GROUP BY City;
```

**More HAVING examples:**
```sql
-- Cities where average marks > 85
SELECT City, AVG(Marks) AS Avg_Marks
FROM Student
GROUP BY City
HAVING AVG(Marks) > 85;

-- Departments with more than 5 employees AND avg salary > 50000
SELECT Dept, COUNT(*), AVG(Salary)
FROM Employee
GROUP BY Dept
HAVING COUNT(*) > 5 AND AVG(Salary) > 50000;
```

---

## 🟣 ORDER BY — Sort Results

```sql
-- Sort by Marks ascending (default — ASC is optional to write)
SELECT Name, Marks FROM Student ORDER BY Marks;
SELECT Name, Marks FROM Student ORDER BY Marks ASC;  -- Same result

-- Sort by Marks descending
SELECT Name, Marks FROM Student ORDER BY Marks DESC;

-- Sort by multiple columns
SELECT Name, City, Marks FROM Student ORDER BY City ASC, Marks DESC;
-- Sorts by City alphabetically, within same City sorts by Marks highest first
```

> **🔔 KEY PYQ FACT:** `ORDER BY` default = **ASC (Ascending)**. This is directly asked in exams.

---

## 📊 AGGREGATE FUNCTIONS — The Core 5

Aggregate functions operate on a **set of rows** and return a **single value**.

```
┌──────────────┬───────────────────────────────────────────────────────┐
│ Function     │ What It Does + Example                                │
├──────────────┼───────────────────────────────────────────────────────┤
│ COUNT(*)     │ Counts ALL rows (including NULLs)                     │
│ COUNT(col)   │ Counts rows where col is NOT NULL                     │
│              │ SELECT COUNT(*) FROM Student;  → 5                    │
├──────────────┼───────────────────────────────────────────────────────┤
│ SUM(col)     │ Adds up all values in a column (ignores NULLs)       │
│              │ SELECT SUM(Marks) FROM Student;  → 438                │
├──────────────┼───────────────────────────────────────────────────────┤
│ AVG(col)     │ Calculates average (ignores NULLs)                   │
│              │ SELECT AVG(Marks) FROM Student;  → 87.6              │
├──────────────┼───────────────────────────────────────────────────────┤
│ MAX(col)     │ Returns the maximum value                             │
│              │ SELECT MAX(Marks) FROM Student;  → 95                 │
├──────────────┼───────────────────────────────────────────────────────┤
│ MIN(col)     │ Returns the minimum value                             │
│              │ SELECT MIN(Marks) FROM Student;  → 78                 │
└──────────────┴───────────────────────────────────────────────────────┘
```

> **🔔 PYQ TRAP: COMPUTE is NOT a valid aggregate function in SQL!**
> Valid: COUNT, SUM, AVG, MAX, MIN
> NOT Valid: COMPUTE, TOTAL, CALCULATE

**Key behaviors of aggregate functions:**
- They IGNORE NULL values (except COUNT(*))
- They work on a group of rows and return ONE value
- They can only be used in SELECT and HAVING clauses (NOT in WHERE)

```sql
-- Complete example combining everything
SELECT City,
       COUNT(*)    AS Total_Students,
       AVG(Marks)  AS Average_Marks,
       MAX(Marks)  AS Highest_Marks,
       MIN(Marks)  AS Lowest_Marks,
       SUM(Marks)  AS Total_Marks
FROM Student
WHERE Marks >= 75          -- Filter individual rows first
GROUP BY City              -- Then group
HAVING COUNT(*) >= 2       -- Filter groups: only cities with 2+ students
ORDER BY Average_Marks DESC;  -- Sort by avg marks highest first
```

---

## 🔗 SQL JOINS — Combining Tables

Joins combine rows from two or more tables based on a related column.

**Tables used for examples:**
```
Student Table:                    Course Table:
┌─────────┬──────┬─────────┐     ┌──────────┬─────────────────┐
│ Roll_No │ Name │ Dept_ID │     │ Dept_ID  │ Dept_Name       │
├─────────┼──────┼─────────┤     ├──────────┼─────────────────┤
│ 101     │Rohan │ D1      │     │ D1       │ Computer Science│
│ 102     │Priya │ D2      │     │ D2       │ Mathematics     │
│ 103     │Amit  │ D3      │     │ D4       │ Physics         │
│ 104     │Neha  │ NULL    │     └──────────┴─────────────────┘
└─────────┴──────┴─────────┘
Note: Amit's Dept (D3) not in Course table. Neha has NULL dept.
```

### INNER JOIN — Only matching rows from BOTH tables

```sql
SELECT S.Name, C.Dept_Name
FROM Student S
INNER JOIN Course C ON S.Dept_ID = C.Dept_ID;
```
```
Result (only rows where Dept_ID matches in BOTH tables):
┌───────┬─────────────────┐
│ Name  │ Dept_Name       │
├───────┼─────────────────┤
│ Rohan │ Computer Science│   ← D1 matched
│ Priya │ Mathematics     │   ← D2 matched
└───────┴─────────────────┘
(Amit excluded — D3 not in Course table)
(Neha excluded — NULL dept_id)
(Physics dept excluded — no student has D4)
```

### LEFT JOIN (LEFT OUTER JOIN) — All rows from LEFT table + matching from RIGHT

```sql
SELECT S.Name, C.Dept_Name
FROM Student S
LEFT JOIN Course C ON S.Dept_ID = C.Dept_ID;
```
```
Result (ALL students shown, Course info where available):
┌───────┬─────────────────┐
│ Name  │ Dept_Name       │
├───────┼─────────────────┤
│ Rohan │ Computer Science│   ← matched
│ Priya │ Mathematics     │   ← matched
│ Amit  │ NULL            │   ← no match in Course, shown with NULL
│ Neha  │ NULL            │   ← no dept, shown with NULL
└───────┴─────────────────┘
```

### RIGHT JOIN — All rows from RIGHT table + matching from LEFT

```sql
SELECT S.Name, C.Dept_Name
FROM Student S
RIGHT JOIN Course C ON S.Dept_ID = C.Dept_ID;
```
```
Result (ALL courses shown, Student info where available):
┌───────┬─────────────────┐
│ Name  │ Dept_Name       │
├───────┼─────────────────┤
│ Rohan │ Computer Science│   ← matched
│ Priya │ Mathematics     │   ← matched
│ NULL  │ Physics         │   ← no student has D4, shown with NULL
└───────┴─────────────────┘
```

### FULL OUTER JOIN — ALL rows from BOTH tables (with NULLs where no match)

```
JOIN SUMMARY DIAGRAM:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

INNER JOIN:          LEFT JOIN:          RIGHT JOIN:
  ┌──┐ ┌──┐           ┌──┐ ┌──┐           ┌──┐ ┌──┐
  │  ███  │           │██████  │           │  ██████│
  └──┘ └──┘           └──┘ └──┘           └──┘ └──┘
  Only overlap        All Left + overlap  All Right + overlap

FULL OUTER JOIN:
  ┌──┐ ┌──┐
  │████████│
  └──┘ └──┘
  Everything from both tables
```

---

## 📝 SUBQUERIES (Nested Queries)

A subquery is a SELECT inside another SELECT.

```sql
-- Find students who scored above average
SELECT Name, Marks FROM Student
WHERE Marks > (SELECT AVG(Marks) FROM Student);

-- Find students in the same city as student 101
SELECT Name FROM Student
WHERE City = (SELECT City FROM Student WHERE Roll_No = 101);

-- Find students who are in any of the cities where marks > 90 exist
SELECT Name FROM Student
WHERE City IN (SELECT City FROM Student WHERE Marks > 90);
```

---

## 📊 WITH Clause — Common Table Expressions (CTE)

The WITH clause creates a **temporary named result set** (like a temporary table) used within a single query.

```sql
WITH TopStudents AS (
    SELECT Name, Marks, City
    FROM Student
    WHERE Marks > 85
)
SELECT City, COUNT(*) AS Count
FROM TopStudents
GROUP BY City;
```

> **🔔 Exam Fact:** WITH clause creates a **temporary relation** (not a permanent table). It exists only for the duration of the query.

---

## 🔥 Complete BPSC PYQ High-Frequency SQL Facts

| PYQ Question Trigger | Answer |
|---------------------|--------|
| ORDER BY default direction | **ASC (Ascending)** |
| HAVING is used with | **GROUP BY** — filters groups |
| WHERE filters | **Individual rows** (before grouping) |
| HAVING filters | **Groups** (after GROUP BY) |
| Valid aggregate functions | **COUNT, SUM, AVG, MAX, MIN** |
| INVALID aggregate function | **COMPUTE** (NOT valid!) |
| DISTINCT is used for | Removing duplicate rows from result |
| Can aggregate functions be in WHERE? | **NO** — only in SELECT and HAVING |
| WITH clause creates | **Temporary relation** (CTE) |
| INNER JOIN returns | Only **matching rows from BOTH** tables |
| LEFT JOIN returns | **All left table rows** + matching right rows |
| LIKE pattern: any characters | **%** (percent) |
| LIKE pattern: single character | **_** (underscore) |
| BETWEEN is | Inclusive on both ends |
| NULL check in SQL | Use **IS NULL** or **IS NOT NULL** (NOT = NULL!) |
| Correct: Check for NULL | `WHERE col IS NULL` (not `WHERE col = NULL`) |

---

## 🧠 Memory Master — WHERE vs HAVING

```
W → WHERE  → Works on individual ROWS  → Written BEFORE GROUP BY
H → HAVING → Handles group-level       → Written AFTER GROUP BY

Simple rule: If you use an aggregate function (COUNT, SUM, AVG, MAX, MIN)
in your condition → use HAVING.
If you're filtering by regular column values → use WHERE.
```

---

# ═══════════════════════════════════════════════════════
# 🦠 PART 2: GS — HUMAN IMMUNE SYSTEM & DISEASES
# ═══════════════════════════════════════════════════════

## 🎯 Immune System — Your Body's Army

The **immune system** is the body's defence mechanism against pathogens (bacteria, viruses, fungi, parasites).

---

## 🏰 Lines of Defence

```
FIRST LINE OF DEFENCE (Physical/Chemical Barriers):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
• Skin         — physical barrier against most pathogens
• Mucus        — traps pathogens in respiratory and digestive tracts
• Saliva/Tears — contain lysozyme enzyme that kills bacteria
• Stomach acid — kills most ingested microbes (HCl, pH ~2)
• Cilia        — hair-like structures that sweep pathogens out of airways
• Sebaceous glands — produce oil (acidic pH inhibits bacterial growth)

SECOND LINE OF DEFENCE (Non-specific/Innate Immunity):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
• Inflammation — increased blood flow to infection site
• Fever        — high temperature inhibits pathogen growth
• Phagocytes   — white blood cells that engulf and destroy pathogens
  - Neutrophils (most common WBC)
  - Macrophages (big eater cells)
• Natural Killer (NK) cells — destroy virus-infected and cancer cells
• Complement system — proteins that destroy bacterial cell membranes
• Interferon   — antiviral proteins released by virus-infected cells

THIRD LINE OF DEFENCE (Specific/Adaptive Immunity):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
• Lymphocytes (T cells and B cells) — specific to each pathogen
• Antibody production
• Immunological memory
```

---

## 🔬 LYMPHOCYTES — The Specific Defenders

Lymphocytes are a type of **White Blood Cell (WBC / Leukocyte)**.

```
LYMPHOCYTES
     │
     ├── T LYMPHOCYTES (T cells)
     │        │
     │        ├── Helper T cells (CD4+)  — Coordinate immune response
     │        │                            Activate B cells and Killer T cells
     │        │                            HIV attacks these! (causes AIDS)
     │        │
     │        ├── Killer/Cytotoxic T cells (CD8+)
     │        │                            Destroy virus-infected cells directly
     │        │
     │        └── Memory T cells         — Remember the pathogen for future attack
     │
     └── B LYMPHOCYTES (B cells)
              │
              ├── Plasma cells (activated B cells)
              │                            Produce ANTIBODIES
              │
              └── Memory B cells         — Remember pathogen; faster response next time
```

### Where Are They Made?
```
T cells: Made in BONE MARROW, mature in THYMUS GLAND (T = Thymus)
B cells: Made AND mature in BONE MARROW (B = Bone marrow)

Both circulate in BLOOD and LYMPH nodes
```

> **🔔 Exam Fact:** T cells mature in the **Thymus** gland. B cells mature in **Bone Marrow**. Both are types of lymphocytes.

---

## 🛡️ TYPES OF IMMUNITY

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          TYPES OF IMMUNITY                              │
├───────────────────────┬─────────────────────────────────────────────────┤
│ INNATE / NATURAL      │ • Present from birth                            │
│ (Non-specific)        │ • Does NOT improve with exposure                │
│                       │ • First and second lines of defence             │
│                       │ • Same response every time                      │
│                       │ Examples: Skin, tears, phagocytes, fever        │
├───────────────────────┼─────────────────────────────────────────────────┤
│ ACQUIRED / ADAPTIVE   │ • Develops after exposure to pathogens          │
│ (Specific)            │ • Improves with repeated exposure (memory)      │
│                       │ • Two types: Active and Passive                 │
│                       │ Examples: Antibodies, T cells, B cells          │
└───────────────────────┴─────────────────────────────────────────────────┘

ACQUIRED IMMUNITY FURTHER DIVIDED:
┌───────────────────────────────────────────────────────────────────────┐
│           ACTIVE IMMUNITY              │    PASSIVE IMMUNITY          │
│  Body PRODUCES its OWN antibodies      │  Antibodies GIVEN from       │
│                                        │  OUTSIDE (donor)             │
├────────────────────────────────────────┼──────────────────────────────┤
│ Natural Active:                        │ Natural Passive:             │
│ • From actual infection/disease        │ • Mother's antibodies to     │
│ • Long-lasting                         │   baby through placenta      │
│                                        │   (IgG) and breast milk (IgA)│
├────────────────────────────────────────┼──────────────────────────────┤
│ Artificial Active:                     │ Artificial Passive:          │
│ • From VACCINATION (vaccine)           │ • Antiserum / Antitoxin      │
│ • Body makes antibodies after vaccine  │   injection                  │
│ • Long-lasting                         │ • Immediate but short-lived  │
│                                        │ • Used for rabies, tetanus   │
└────────────────────────────────────────┴──────────────────────────────┘
```

---

## 💉 ANTIBODIES — The Precision Weapons

**Antibody = Immunoglobulin (Ig)**

```
Antibody Structure:
        Y-shape

     ┌─────┐ ┌─────┐
     │     │ │     │  ← Variable region (antigen-binding site)
     │  Fab│ │Fab  │     SPECIFIC to one antigen only
     │     │ │     │
     └──┬──┘ └──┬──┘
        │       │
        └───┬───┘
            │
          ┌─┴─┐
          │Fc │  ← Constant region
          └───┘
```

**Types of Immunoglobulins:**
```
┌──────┬──────────────────────────────────────────────────────────────┐
│ Type │ Key Role                                                      │
├──────┼──────────────────────────────────────────────────────────────┤
│ IgG  │ Most abundant (80%). Crosses placenta → protects newborn     │
│ IgA  │ Found in secretions — saliva, tears, breast milk, mucus      │
│ IgM  │ First to appear during infection. Largest antibody           │
│ IgE  │ Involved in ALLERGIES and parasitic infections               │
│ IgD  │ Found on surface of B cells (acts as receptor)              │
└──────┴──────────────────────────────────────────────────────────────┘
```

> **🔔 Exam Facts:**
> - **IgG** = crosses placenta → gives passive immunity to baby
> - **IgA** = in mother's milk (colostrum)
> - **IgM** = first antibody produced during primary immune response
> - **IgE** = allergies and asthma

---

## 🦠 VACCINES — Training the Immune System

**Vaccine** = A preparation containing weakened/killed pathogens or their antigens, given to stimulate immunity WITHOUT causing disease.

### Edward Jenner — Father of Vaccination
- 1796: Used **cowpox** virus to protect against **smallpox**
- First vaccine ever developed
- Word "vaccine" comes from Latin **"vacca"** = cow

### Types of Vaccines:
```
┌──────────────────────┬──────────────────────────────────────────────────┐
│ Type                 │ Examples                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Live Attenuated      │ BCG (TB), Oral Polio (OPV), MMR (Measles-       │
│ (Weakened pathogen)  │ Mumps-Rubella), Yellow Fever, Chickenpox        │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Killed/Inactivated   │ IPV (Inactivated Polio), Rabies, Influenza,     │
│ (Dead pathogen)      │ Hepatitis A                                      │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Toxoid               │ Tetanus, Diphtheria (DPT vaccine)               │
│ (Inactivated toxin)  │                                                  │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Subunit              │ Hepatitis B, HPV (Human Papillomavirus)         │
│ (Antigen component)  │                                                  │
├──────────────────────┼──────────────────────────────────────────────────┤
│ mRNA (newest)        │ COVID-19 vaccines (Pfizer, Moderna)             │
└──────────────────────┴──────────────────────────────────────────────────┘
```

### Important Vaccines and Discoverers:
```
┌─────────────────────────┬──────────────────────┬────────────────────────────┐
│ Vaccine / Discovery     │ Discoverer            │ Year                       │
├─────────────────────────┼──────────────────────┼────────────────────────────┤
│ Smallpox vaccine        │ Edward Jenner         │ 1796                       │
│ Rabies vaccine          │ Louis Pasteur         │ 1885                       │
│ BCG (TB vaccine)        │ Calmette & Guérin     │ 1921                       │
│ Polio vaccine (IPV)     │ Jonas Salk            │ 1955                       │
│ Oral Polio vaccine(OPV) │ Albert Sabin          │ 1961                       │
│ Hepatitis B vaccine     │ Blumberg/Merck        │ 1969/1981                  │
└─────────────────────────┴──────────────────────┴────────────────────────────┘
```

> **🔔 Exam Trap:** Jonas Salk = **IPV** (Injected). Albert Sabin = **OPV** (Oral). Both are polio vaccines but different!

---

## 🦠 HUMAN DISEASES — High-Yield BPSC Table

### Bacterial Diseases:
```
┌─────────────────┬─────────────────────┬───────────────────────────────────────┐
│ Disease         │ Causative Organism  │ Key Facts                             │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Tuberculosis(TB)│ Mycobacterium       │ Affects lungs, BCG vaccine, DOTS      │
│                 │ tuberculosis        │ treatment, droplet infection           │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Typhoid         │ Salmonella typhi    │ Contaminated food/water, slow fever,  │
│                 │                     │ Rose spots on abdomen, Widal test      │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Cholera         │ Vibrio cholerae     │ Contaminated water, rice-water stools,│
│                 │                     │ El Tor strain, ORS treatment           │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Plague          │ Yersinia pestis     │ Spread by rat flea (Xenopsylla cheopis)│
│                 │                     │ Types: Bubonic, Pneumonic, Septicaemic │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Leprosy         │ Mycobacterium leprae│ Hansen's disease, nerve damage,       │
│                 │                     │ MDT (Multi-Drug Therapy) treatment     │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Tetanus         │ Clostridium tetani  │ Lockjaw, neurotoxin, DPT vaccine      │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Diphtheria      │ Corynebacterium     │ Pseudomembrane in throat, DPT vaccine │
│                 │ diphtheriae         │                                        │
└─────────────────┴─────────────────────┴───────────────────────────────────────┘
```

### Viral Diseases:
```
┌─────────────────┬─────────────────────┬───────────────────────────────────────┐
│ Disease         │ Virus               │ Key Facts                             │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ AIDS            │ HIV (Retrovirus)    │ Attacks CD4+ T cells, no cure,        │
│                 │                     │ transmitted via blood/sex/mother-child │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Polio           │ Poliovirus          │ Destroys motor neurons, paralysis,    │
│                 │ (Enterovirus)       │ OPV/IPV vaccines                       │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Rabies          │ Rhabdovirus         │ Dog/animal bite, hydrophobia,         │
│                 │                     │ Pasteur vaccine, fatal if not treated  │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Dengue          │ Flavivirus          │ Aedes mosquito, low platelets,        │
│                 │                     │ hemorrhagic fever, no specific drug    │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Hepatitis B     │ Hepadnavirus (HBV)  │ Liver disease, vaccine available,     │
│                 │                     │ blood-borne, jaundice                  │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Influenza       │ Influenza virus     │ Droplet, 3 types (A, B, C),           │
│                 │                     │ Pandemic H1N1 (Swine flu)             │
│ Chickenpox      │ Varicella Zoster    │ Skin rash/blisters, highly contagious │
│ Measles         │ Paramyxovirus       │ MMR vaccine, Koplik spots in mouth    │
└─────────────────┴─────────────────────┴───────────────────────────────────────┘
```

### Parasitic / Protozoan Diseases:
```
┌─────────────────┬─────────────────────┬───────────────────────────────────────┐
│ Disease         │ Parasite            │ Key Facts                             │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Malaria         │ Plasmodium spp.     │ Female Anopheles mosquito, affects    │
│                 │ (P. falciparum      │ RBCs, cyclic fever, Quinine/           │
│                 │ most dangerous)     │ Chloroquine treatment                  │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Amoebic Dysentery│ Entamoeba histolytica│ Contaminated food/water, diarrhoea  │
├─────────────────┼─────────────────────┼───────────────────────────────────────┤
│ Kala-azar       │ Leishmania donovani │ Sandfly (Phlebotomus), fever,        │
│ (Black fever)   │                     │ spleen/liver enlargement              │
│                 │                     │ ENDEMIC in Bihar (Muzaffarpur, Gaya)  │
└─────────────────┴─────────────────────┴───────────────────────────────────────┘
```

> **🔔 BIHAR BPSC SPECIAL:** Kala-azar (Black Fever/Visceral Leishmaniasis) is **endemic in Bihar** — especially Muzaffarpur, Vaishali, Sitamarhi, Gaya districts. This is frequently asked in BPSC exams!

---

## 🩸 BLOOD — Key Facts

```
BLOOD COMPOSITION:
━━━━━━━━━━━━━━━━━
Blood (55% Plasma + 45% Cells)
       │                │
   Plasma            Blood Cells
   ├─ 92% Water      ├─ RBC (Red Blood Cells) = Erythrocytes
   ├─ Proteins       │   • Carry O₂ (via haemoglobin)
   ├─ Glucose        │   • No nucleus in mature human RBCs
   ├─ Hormones       │   • Life = 120 days
   └─ Antibodies     │   • Made in: Bone marrow
                     │
                     ├─ WBC (White Blood Cells) = Leukocytes
                     │   • Fight infections
                     │   • Types: Neutrophils, Monocytes,
                     │            Eosinophils, Basophils,
                     │            Lymphocytes (T and B cells)
                     │   • Life = days to weeks
                     │
                     └─ Platelets = Thrombocytes
                         • Blood clotting
                         • Life = 5-10 days
```

### Blood Groups (ABO System — discovered by Karl Landsteiner, 1901):
```
┌────────────┬──────────────┬──────────────┬──────────────┬──────────────┐
│ Blood Group│ Antigen on   │ Antibody in  │ Can Donate   │ Can Receive  │
│            │ RBC          │ Plasma       │ To           │ From         │
├────────────┼──────────────┼──────────────┼──────────────┼──────────────┤
│ A          │ A            │ Anti-B       │ A, AB        │ A, O         │
│ B          │ B            │ Anti-A       │ B, AB        │ B, O         │
│ AB         │ A and B      │ None         │ AB only      │ ALL (universal│
│            │              │              │              │  recipient)  │
│ O          │ None         │ Anti-A, Anti-B│ ALL (universal│ O only      │
│            │              │              │  donor)      │              │
└────────────┴──────────────┴──────────────┴──────────────┴──────────────┘
```

> **🔔 Exam Facts:**
> - **Universal Donor** = Blood Group **O** (can donate to everyone)
> - **Universal Recipient** = Blood Group **AB** (can receive from everyone)
> - Discovered by: **Karl Landsteiner** (Nobel Prize 1930)
> - **Rh Factor:** Rh+ = has Rh antigen; Rh- = lacks Rh antigen

---

## 📝 High-Frequency GS PYQ Facts — Immunity & Diseases

| Question Trigger | Answer |
|-----------------|--------|
| Father of Vaccination | **Edward Jenner** |
| First vaccine used cowpox to protect against | **Smallpox** |
| HIV attacks which cells | **CD4+ T Helper cells** |
| Universal blood donor | **Group O** |
| Universal blood recipient | **Group AB** |
| Blood group system discovered by | **Karl Landsteiner (1901)** |
| T cells mature in | **Thymus** gland |
| B cells mature in | **Bone Marrow** |
| IgG crosses placenta → protects | **Newborn baby** |
| IgE involved in | **Allergies** |
| IgA found in | **Secretions (saliva, tears, milk)** |
| IgM is | **First antibody in primary response** |
| Malaria spread by | **Female Anopheles mosquito** |
| Dengue spread by | **Aedes mosquito** |
| Most dangerous Plasmodium species | **P. falciparum** |
| Kala-azar spread by | **Sandfly (Phlebotomus)** |
| Kala-azar endemic state in India | **Bihar** |
| Plague spread by | **Rat flea (Xenopsylla cheopis)** |
| Polio vaccine (oral) discoverer | **Albert Sabin** |
| Polio vaccine (injected) discoverer | **Jonas Salk** |
| BCG vaccine is for | **Tuberculosis** |
| DPT vaccine covers | **Diphtheria, Pertussis (Whooping cough), Tetanus** |
| MMR vaccine covers | **Measles, Mumps, Rubella** |
| Vaccine word from Latin | **"vacca" = cow** (Jenner used cowpox) |
| "Passive immunity" in newborns from mother via | **IgG through placenta; IgA through breast milk** |
| Antigens | **Substances that trigger immune response** |
| Antibodies are also called | **Immunoglobulins (Ig)** |

---

# ═══════════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 41
# ═══════════════════════════════════════════════════════

> ⚠️ **RULE:** Attempt ALL 50 questions FIRST. Answer Key is ONLY after Q50.
> Option D = "More than one of the above" | Option E = "None of the above"

---

# 💻 SECTION A: CS QUESTIONS — SQL SELECT & CLAUSES (Q1–Q25)

---

**Q1.** What is the DEFAULT sorting order when you use `ORDER BY` in SQL without specifying ASC or DESC?

(A) DESC (Descending)
(B) ASC (Ascending)
(C) Random order
(D) Alphabetical only
(E) None of the above

---

**Q2.** Which SQL clause is used to filter the results AFTER a GROUP BY operation?

(A) WHERE
(B) FILTER
(C) HAVING
(D) ORDER BY
(E) None of the above

---

**Q3.** Which of the following is NOT a valid SQL aggregate function?

(A) COUNT
(B) SUM
(C) COMPUTE
(D) AVG
(E) MIN

---

**Q4.** Consider the following SQL query:
```sql
SELECT City, COUNT(*) AS Total
FROM Student
GROUP BY City
HAVING COUNT(*) > 2;
```
What does this query return?

(A) All cities and their student counts
(B) Only cities where the number of students is more than 2
(C) Only cities where the total marks are greater than 2
(D) Cities sorted by student count
(E) None of the above

---

**Q5.** Which SQL clause is used to remove duplicate rows from the result of a SELECT query?

(A) UNIQUE
(B) NODUPLICATE
(C) DISTINCT
(D) FILTER
(E) None of the above

---

**Q6.** The correct execution order of SQL clauses is:

(A) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
(B) FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY
(C) FROM → SELECT → WHERE → GROUP BY → HAVING → ORDER BY
(D) WHERE → FROM → SELECT → GROUP BY → HAVING → ORDER BY
(E) None of the above

---

**Q7.** Which of the following SQL queries will produce an ERROR?

(A) `SELECT City FROM Student WHERE Marks > 80;`
(B) `SELECT City, COUNT(*) FROM Student GROUP BY City HAVING COUNT(*) > 1;`
(C) `SELECT City, COUNT(*) FROM Student WHERE COUNT(*) > 1 GROUP BY City;`
(D) `SELECT DISTINCT City FROM Student;`
(E) None of the above — all are valid

---

**Q8.** The LIKE operator with the pattern `'%on%'` will match:

(A) Only strings starting with 'on'
(B) Only strings ending with 'on'
(C) Any string containing 'on' anywhere
(D) Strings with exactly 2 characters 'on'
(E) None of the above

---

**Q9.** What does `SELECT AVG(Marks) FROM Student` return?

(A) The marks of the student with average rank
(B) The sum of all marks divided by the count of non-NULL marks
(C) The marks at the middle position when sorted
(D) The most frequent marks value
(E) None of the above

---

**Q10.** To check if a column value is NULL in SQL, which syntax is CORRECT?

(A) `WHERE column = NULL`
(B) `WHERE column == NULL`
(C) `WHERE column IS NULL`
(D) `WHERE column EQUALS NULL`
(E) None of the above

---

**Q11.** The `WITH` clause in SQL creates:

(A) A permanent table in the database
(B) A temporary named result set (CTE) used within the query
(C) A new database schema
(D) An index on the specified columns
(E) None of the above

---

**Q12.** Which type of JOIN returns only the rows that have MATCHING values in BOTH tables?

(A) LEFT JOIN
(B) RIGHT JOIN
(C) FULL OUTER JOIN
(D) INNER JOIN
(E) None of the above

---

**Q13.** Which of the following correctly describes a LEFT JOIN?

(A) Returns all rows from the RIGHT table and matching rows from the LEFT table
(B) Returns all rows from the LEFT table and matching rows from the RIGHT table, with NULLs for non-matching right rows
(C) Returns only rows where both tables have matching values
(D) Returns all rows from both tables regardless of matching
(E) None of the above

---

**Q14.** `SELECT COUNT(*) FROM Student` vs `SELECT COUNT(Email) FROM Student` — when will they give different results?

(A) Never — both always give the same result
(B) When the Email column contains NULL values (COUNT(*) counts NULLs, COUNT(col) ignores NULLs)
(C) When there are duplicate values in Email
(D) When the table has more than 100 rows
(E) None of the above

---

**Q15.** The SQL `BETWEEN` operator:

(A) Excludes both boundary values
(B) Includes the lower boundary but excludes the upper boundary
(C) Includes BOTH boundary values (inclusive on both ends)
(D) Excludes the lower boundary but includes the upper boundary
(E) None of the above

---

**Q16.** Which of the following SQL statements finds students whose name STARTS with the letter 'A'?

(A) `SELECT * FROM Student WHERE Name LIKE 'A_';`
(B) `SELECT * FROM Student WHERE Name LIKE 'A%';`
(C) `SELECT * FROM Student WHERE Name LIKE '%A';`
(D) `SELECT * FROM Student WHERE Name LIKE '_A%';`
(E) None of the above

---

**Q17.** Which aggregate function would you use to find the HIGHEST salary in an Employee table?

(A) `SUM(Salary)`
(B) `COUNT(Salary)`
(C) `MAX(Salary)`
(D) `TOP(Salary)`
(E) `AVG(Salary)`

---

**Q18.** Consider: A Student table has 10 rows. 3 rows have NULL in the Email column. What will `SELECT COUNT(Email) FROM Student` return?

(A) 10
(B) 3
(C) 7
(D) NULL
(E) None of the above

---

**Q19.** In SQL, the `IN` operator:

(A) Checks if a value falls within a numeric range
(B) Checks if a value matches ANY value in a specified list
(C) Checks if a column contains a pattern
(D) Checks if a value is NOT NULL
(E) None of the above

---

**Q20.** The following query: `SELECT Dept, SUM(Salary) FROM Employee GROUP BY Dept ORDER BY SUM(Salary) DESC;` will:

(A) Show departments sorted by name
(B) Show departments with total salary, highest total first
(C) Show all employees sorted by salary
(D) Show only the department with maximum salary
(E) None of the above

---

**Q21.** Which of the following is TRUE about aggregate functions and NULL values?

(A) AVG(col) includes NULL values in its calculation
(B) COUNT(*) ignores NULL values
(C) SUM(col), AVG(col), MAX(col), MIN(col) all IGNORE NULL values
(D) NULL values are treated as 0 in SUM calculations
(E) None of the above

---

**Q22.** A subquery in SQL is:

(A) A query stored permanently in the database
(B) A SELECT statement nested inside another SQL statement
(C) A query that creates a new table
(D) A query executed automatically on schedule
(E) None of the above

---

**Q23.** What is the correct SQL query to find the 2nd highest marks in the Student table?

(A) `SELECT MAX(Marks) FROM Student WHERE Marks < MAX(Marks);`
(B) `SELECT MAX(Marks) FROM Student WHERE Marks < (SELECT MAX(Marks) FROM Student);`
(C) `SELECT SECOND(Marks) FROM Student;`
(D) `SELECT TOP(2) Marks FROM Student;`
(E) None of the above

---

**Q24.** Which of the following pairs is CORRECTLY matched?

(A) WHERE → filters groups after GROUP BY
(B) HAVING → filters individual rows before grouping
(C) HAVING → requires GROUP BY and filters groups
(D) ORDER BY → filters rows based on a condition
(E) None of the above

---

**Q25.** The `%` wildcard in the LIKE operator matches:

(A) Exactly one character
(B) Only alphabetic characters
(C) Any sequence of characters including zero characters
(D) Only numeric characters
(E) None of the above

---

# 🦠 SECTION B: GS QUESTIONS — IMMUNITY & DISEASES (Q26–Q50)

---

**Q26.** The blood group that is called the "Universal Donor" is:

(A) A
(B) B
(C) AB
(D) O
(E) None of the above

---

**Q27.** HIV (Human Immunodeficiency Virus) primarily attacks which cells in the human body?

(A) B lymphocytes
(B) Red Blood Cells
(C) CD4+ T Helper cells
(D) Neutrophils
(E) None of the above

---

**Q28.** Edward Jenner is known as the "Father of Vaccination." His first vaccine used:

(A) Smallpox virus directly
(B) Cowpox virus to protect against smallpox
(C) Chickenpox virus
(D) Measles virus
(E) None of the above

---

**Q29.** T lymphocytes mature in which organ?

(A) Bone Marrow
(B) Spleen
(C) Thymus
(D) Lymph Nodes
(E) None of the above

---

**Q30.** Which type of antibody (Immunoglobulin) crosses the placenta to provide passive immunity to the newborn?

(A) IgA
(B) IgM
(C) IgE
(D) IgG
(E) IgD

---

**Q31.** Malaria is caused by which parasite and transmitted by which vector?

(A) Leishmania donovani — Sandfly
(B) Plasmodium — Female Anopheles mosquito
(C) Trypanosoma — Tsetse fly
(D) Wuchereria — Culex mosquito
(E) None of the above

---

**Q32.** The BCG vaccine provides protection against:

(A) Cholera
(B) Typhoid
(C) Tuberculosis (TB)
(D) Diphtheria
(E) None of the above

---

**Q33.** Which of the following diseases is ENDEMIC in Bihar and spread by the sandfly?

(A) Malaria
(B) Dengue
(C) Filaria
(D) Kala-azar (Visceral Leishmaniasis)
(E) None of the above

---

**Q34.** The DPT vaccine provides immunity against:

(A) Dengue, Polio, Typhoid
(B) Diphtheria, Pertussis (Whooping cough), Tetanus
(C) Dysentery, Plague, Tetanus
(D) More than one of the above
(E) None of the above

---

**Q35.** Which blood group is called the "Universal Recipient"?

(A) O
(B) A
(C) B
(D) AB
(E) None of the above

---

**Q36.** The oral polio vaccine (OPV) was developed by:

(A) Jonas Salk
(B) Edward Jenner
(C) Albert Sabin
(D) Louis Pasteur
(E) None of the above

---

**Q37.** Dengue fever is spread by which mosquito?

(A) Female Anopheles
(B) Male Culex
(C) Aedes aegypti
(D) Phlebotomus
(E) None of the above

---

**Q38.** Which immunoglobulin (antibody) is associated with ALLERGIC reactions?

(A) IgG
(B) IgM
(C) IgA
(D) IgE
(E) IgD

---

**Q39.** The Widal test is used for diagnosis of which disease?

(A) Malaria
(B) Typhoid
(C) Cholera
(D) Dengue
(E) None of the above

---

**Q40.** Which of the following is a VIRAL disease?

(A) Tuberculosis
(B) Typhoid
(C) Cholera
(D) Rabies
(E) Plague

---

**Q41.** The ABO blood group system was discovered by:

(A) William Harvey
(B) Karl Landsteiner
(C) Edward Jenner
(D) Robert Koch
(E) None of the above

---

**Q42.** In the context of immunity, what does "antigen" mean?

(A) A substance produced by the body to fight infection
(B) Any foreign substance that triggers an immune response
(C) A type of white blood cell
(D) A vaccine component that prevents disease
(E) None of the above

---

**Q43.** Plague is caused by Yersinia pestis and is spread by:

(A) Female Anopheles mosquito
(B) Aedes mosquito
(C) Rat flea (Xenopsylla cheopis)
(D) Sandfly (Phlebotomus)
(E) None of the above

---

**Q44.** Which of the following represents ARTIFICIAL ACTIVE immunity?

(A) A baby receiving antibodies through mother's breast milk
(B) A patient receiving antitoxin injection after snake bite
(C) A person getting vaccinated against polio
(D) Antibodies crossing the placenta to the fetus
(E) None of the above

---

**Q45.** IgA antibody is found primarily in:

(A) Blood plasma only
(B) Secretions like saliva, tears, and mother's milk
(C) Bone marrow
(D) Thymus gland
(E) None of the above

---

**Q46.** Robert Koch is associated with the discovery of the causative organism of which disease?

(A) Malaria
(B) Typhoid
(C) Tuberculosis (Mycobacterium tuberculosis)
(D) Cholera (Vibrio cholerae)
(E) More than one of the above

---

**Q47.** Which of the following is TRUE about Natural Killer (NK) cells?

(A) They are a type of B lymphocyte
(B) They require specific antigens to be activated
(C) They destroy virus-infected cells and cancer cells as part of innate immunity
(D) They are only active during allergic reactions
(E) None of the above

---

**Q48.** The word "VACCINE" is derived from the Latin word:

(A) "Vacuus" = empty
(B) "Vacca" = cow
(C) "Vaccinus" = vaccination
(D) "Vaccaer" = to protect
(E) None of the above

---

**Q49.** Consider the following statements about blood:
1. Mature human RBCs have no nucleus
2. RBCs live for approximately 120 days
3. IgM is the FIRST antibody produced in a primary immune response
4. Blood group AB has both anti-A and anti-B antibodies in plasma

Which of the above statements are CORRECT?

(A) Only 1 and 2
(B) Only 1, 2, and 3
(C) Only 2 and 4
(D) More than one of the above — 1, 2, and 3 are correct
(E) All four are correct

---

**Q50.** Leprosy (Hansen's Disease) is caused by:

(A) Mycobacterium tuberculosis
(B) Bacillus anthracis
(C) Mycobacterium leprae
(D) Clostridium tetani
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🔑 ANSWER KEY — ALL 50 QUESTIONS
# ═══════════════════════════════════════════════════════

> ✅ Check ONLY after attempting all 50 questions!

---

## 💻 CS ANSWERS — SQL SELECT & Clauses (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| 1 | **(B)** | `ORDER BY` default is **ASC (Ascending)**. This is a direct, frequently asked PYQ fact. |
| 2 | **(C)** | **HAVING** filters results AFTER GROUP BY. WHERE filters individual rows BEFORE grouping. |
| 3 | **(C)** | **COMPUTE is NOT a valid SQL aggregate function.** Valid ones: COUNT, SUM, AVG, MAX, MIN. This is a direct PYQ trap. |
| 4 | **(B)** | HAVING COUNT(*) > 2 returns only cities that have MORE THAN 2 students. |
| 5 | **(C)** | **DISTINCT** removes duplicate rows from SELECT query results. |
| 6 | **(B)** | Execution order: **FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY**. This differs from writing order. |
| 7 | **(C)** | Query C uses `WHERE COUNT(*) > 1` — **CANNOT use aggregate function in WHERE clause**. This causes an error. Use HAVING instead. |
| 8 | **(C)** | `'%on%'` matches **any string containing 'on' anywhere** — before, after, or in the middle. |
| 9 | **(B)** | AVG = **sum of all non-NULL values divided by the count of non-NULL values** (NULLs are ignored). |
| 10 | **(C)** | Correct syntax is **`IS NULL`**. You cannot use `= NULL` — NULL is not equal to anything, not even itself. |
| 11 | **(B)** | WITH clause creates a **temporary named result set (CTE — Common Table Expression)** used only within that query. |
| 12 | **(D)** | **INNER JOIN** returns only rows with matching values in BOTH tables. |
| 13 | **(B)** | LEFT JOIN returns **ALL rows from the left table** + matching rows from right table (NULLs where no match in right). |
| 14 | **(B)** | `COUNT(*)` counts ALL rows including NULLs. `COUNT(Email)` counts only rows where Email is NOT NULL. They differ when Email has NULLs. |
| 15 | **(C)** | BETWEEN is **inclusive on both ends**: `BETWEEN 75 AND 90` includes 75 and 90. |
| 16 | **(B)** | `Name LIKE 'A%'` — matches names starting with 'A' followed by any characters. `'A_'` would only match 2-character names. |
| 17 | **(C)** | **`MAX(Salary)`** returns the highest salary value. |
| 18 | **(C)** | `COUNT(Email)` counts only non-NULL values. 10 rows minus 3 NULLs = **7**. |
| 19 | **(B)** | `IN` checks if a value **matches any value in a specified list**: `WHERE City IN ('Patna','Delhi')`. |
| 20 | **(B)** | Groups by Dept, sums salary per dept, then ORDER BY SUM DESC → **shows departments with highest total salary first**. |
| 21 | **(C)** | **SUM, AVG, MAX, MIN all IGNORE NULL values.** Only COUNT(*) counts NULLs. This is an important distinction. |
| 22 | **(B)** | A subquery is **a SELECT statement nested inside another SQL statement** (within WHERE, HAVING, FROM, or SELECT). |
| 23 | **(B)** | `SELECT MAX(Marks) FROM Student WHERE Marks < (SELECT MAX(Marks) FROM Student)` — finds the max that is less than the overall max = 2nd highest. |
| 24 | **(C)** | Correct: **HAVING requires GROUP BY and filters groups** (not individual rows). WHERE filters individual rows. |
| 25 | **(C)** | `%` matches **any sequence of characters including zero characters** (empty string). `_` matches exactly one character. |

---

## 🦠 GS ANSWERS — Immunity & Diseases (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| 26 | **(D)** | **Blood Group O** = Universal Donor (no A or B antigens, so no immune reaction in any recipient). |
| 27 | **(C)** | HIV specifically targets and destroys **CD4+ T Helper cells**, crippling the immune system, leading to AIDS. |
| 28 | **(B)** | Jenner used **cowpox virus** (vaccinia) to immunise against smallpox. The similarity in the viruses provided cross-immunity. |
| 29 | **(C)** | T lymphocytes are produced in bone marrow but **mature in the THYMUS** gland (T = Thymus). |
| 30 | **(D)** | **IgG** is the only immunoglobulin that crosses the placenta, providing passive immunity to the fetus/newborn. |
| 31 | **(B)** | Malaria is caused by **Plasmodium** species and transmitted by the bite of **female Anopheles mosquito**. |
| 32 | **(C)** | **BCG (Bacillus Calmette-Guérin)** vaccine is used for **Tuberculosis (TB)**. |
| 33 | **(D)** | **Kala-azar (Visceral Leishmaniasis)** caused by Leishmania donovani, spread by sandfly, **endemic in Bihar**. Direct BPSC special fact. |
| 34 | **(B)** | DPT = **Diphtheria, Pertussis (Whooping cough), Tetanus**. Given as a combined vaccine. |
| 35 | **(D)** | **Blood Group AB** = Universal Recipient (has both A and B antigens, no antibodies against A or B in plasma). |
| 36 | **(C)** | **Albert Sabin** developed OPV (Oral Polio Vaccine, 1961). Jonas Salk developed IPV (Injected, 1955). |
| 37 | **(C)** | Dengue is spread by **Aedes aegypti** mosquito (also Aedes albopictus). Unlike malaria which uses Anopheles. |
| 38 | **(D)** | **IgE** is associated with **allergic reactions** (asthma, hay fever, food allergies) and parasitic infections. |
| 39 | **(B)** | **Widal test** is the diagnostic test for **Typhoid** (Salmonella typhi infection). |
| 40 | **(D)** | **Rabies** is a **viral** disease caused by Rhabdovirus. TB = bacterial, Typhoid = bacterial, Cholera = bacterial, Plague = bacterial. |
| 41 | **(B)** | **Karl Landsteiner** discovered the ABO blood group system in 1901 (Nobel Prize 1930). |
| 42 | **(B)** | **Antigen** = any **foreign substance that triggers an immune response** (and stimulates antibody production). |
| 43 | **(C)** | Plague spreads via the **rat flea (Xenopsylla cheopis)** from infected rats to humans. |
| 44 | **(C)** | **Artificial Active immunity** = **vaccination** — body actively produces its own antibodies after receiving a vaccine. |
| 45 | **(B)** | **IgA** is found primarily in **secretions** — saliva, tears, intestinal secretions, and mother's milk (colostrum). |
| 46 | **(E)** | Robert Koch discovered the TB bacillus (Mycobacterium tuberculosis) AND Vibrio cholerae. **Both** are correct — answer is D/E (More than one). Correct answer = **(D)** — More than one of the above. |
| 47 | **(C)** | Natural Killer cells **destroy virus-infected cells and cancer cells** as part of **innate** (non-specific) immunity without needing prior sensitisation. |
| 48 | **(B)** | "Vaccine" derives from Latin **"vacca"** = cow — because Jenner used cowpox (from cows) for the first vaccine. |
| 49 | **(D)** | Statements 1 ✓ (RBCs have no nucleus), 2 ✓ (120 days lifespan), 3 ✓ (IgM is first in primary response) are correct. Statement 4 is WRONG — AB blood group has NO antibodies in plasma (that's why it's universal recipient). So 1, 2, 3 are correct = **(D)** More than one (1, 2, 3). |
| 50 | **(C)** | Leprosy (Hansen's Disease) is caused by **Mycobacterium leprae** — discovered by G.H. Armauer Hansen in 1873. |

---

# ═══════════════════════════════════════════════════════
# 🎯 TOPPER'S CORNER — DAY 41 CHECKLIST
# ═══════════════════════════════════════════════════════

## ✅ CS SQL SELECT — Must Know Before Exam Day

- [ ] ORDER BY default = **ASC** (Ascending)
- [ ] COMPUTE = **NOT a valid** aggregate function (COUNT, SUM, AVG, MAX, MIN are valid)
- [ ] WHERE = filters **individual rows** | HAVING = filters **groups**
- [ ] Aggregate functions CANNOT be used in WHERE clause
- [ ] Cannot use `WHERE col = NULL` — must use `WHERE col IS NULL`
- [ ] COUNT(*) counts NULLs; COUNT(col) ignores NULLs
- [ ] DISTINCT removes duplicate values from output
- [ ] INNER JOIN = only matching rows from both tables
- [ ] LEFT JOIN = all left rows + matching right rows
- [ ] % wildcard = any number of characters | _ wildcard = exactly one character
- [ ] WITH clause = temporary named result set (CTE)
- [ ] Execution order: FROM→WHERE→GROUP BY→HAVING→SELECT→ORDER BY

## ✅ GS Immunity — Must Know Before Exam Day

- [ ] Universal Donor = **O** | Universal Recipient = **AB**
- [ ] ABO system discovered by **Karl Landsteiner** (1901)
- [ ] HIV attacks **CD4+ T Helper cells**
- [ ] Father of Vaccination = **Edward Jenner** (cowpox → smallpox)
- [ ] T cells mature in **THYMUS** | B cells mature in **BONE MARROW**
- [ ] IgG = crosses placenta (passive immunity to baby)
- [ ] IgA = secretions (saliva, tears, breast milk)
- [ ] IgM = first antibody in primary immune response
- [ ] IgE = allergies
- [ ] Malaria = **Plasmodium** + **Female Anopheles** mosquito
- [ ] Dengue = **Aedes** mosquito
- [ ] Kala-azar = **endemic in Bihar** + sandfly (Phlebotomus)
- [ ] Plague = **rat flea** (Xenopsylla cheopis)
- [ ] BCG = TB vaccine | DPT = Diphtheria, Pertussis, Tetanus
- [ ] OPV = Albert Sabin | IPV = Jonas Salk
- [ ] "Vaccine" from Latin **"vacca"** = cow

---

## 📊 Score Yourself

| Score | Performance | Action |
|-------|-------------|--------|
| 45–50 | 🏆 Topper Level | Revise once → move to Day 42 |
| 38–44 | ✅ On Track | Re-read weak areas tonight |
| 30–37 | ⚠️ Needs Work | Full concept re-read + retry tomorrow |
| < 30  | ❌ Revise Now | Re-study completely before Day 42 |

---

## 📅 Day 42 Preview — DBMS REVISION DAY

**CS:** Full DBMS Revision (Days 36–41) — Database concepts, Keys, ER Model, Normalization, SQL Commands, SQL SELECT
**GS:** Modern Indian History revision — Reform movements, Freedom struggle

Key revision facts: COMMIT=permanent, ROLLBACK=undo, 3NF=adequate, COMPUTE=invalid, ORDER BY default=ASC, Universal Donor=O, Kala-azar endemic=Bihar

---

*Day 41 Complete ✅ | SQL SELECT + Immunity & Diseases mastered! | Target: 130+/150 | TOP 50 Rank! 🎯*
