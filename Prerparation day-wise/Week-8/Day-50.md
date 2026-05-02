# 📅 BPSC TRE 4.0 — DAY 50 COMPLETE STUDY MODULE
### DBMS Quick Revision (CS) + INA & Missing Modern History PYQs (GS)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): DBMS Shortcuts — rapid-fire revision of all high-yield facts
> - Afternoon (1 hr): INA + Missing Modern History — every PYQ fact from TRE 1.0/2.0/3.0
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 DBMS — Quick Revision Shortcuts for Day 50

> **Day 50 Context:** Today's CS session is a *light revision* day — not new learning. You covered DBMS deeply on Days 38–42. Today: speed-drill every single PYQ-tested fact. Read each block, cover it, recall it. If you can't recall → re-read and mark it for tonight's notebook.

---

## 🔷 BLOCK 1: DBMS Fundamentals

```
DBMS = Software to STORE, RETRIEVE, MANIPULATE data

Key Property → DBMS is a MULTI-USER system
⚠️ TRAP: "Single-user access" is a LIMITATION of file systems, NOT of DBMS

DBMS vs File System:
  File System → No relationship between files, redundancy, no security
  DBMS        → Relationships maintained, data integrity, security, multi-user

Types of DBMS:
  Hierarchical → tree structure (like a filing cabinet by customer)
  Network      → graph structure (records linked in any pattern)
  Relational   → tables with rows/columns (most common — Oracle, MySQL)
  Object-oriented → stores objects directly
```

### 🚨 PYQ TRAP #1:
> A traditional filing cabinet organized by customer = **Hierarchical DBMS** model.
> This exact analogy appeared in TRE 2.0!

---

## 🔷 BLOCK 2: Keys in DBMS

```
PRIMARY KEY:
  → Uniquely identifies each row in a table
  → Cannot be NULL
  → Cannot have duplicates
  → Only ONE primary key per table

CANDIDATE KEY:
  → All columns/combinations that COULD be a primary key
  → Primary key is chosen FROM candidate keys

FOREIGN KEY:
  → References PRIMARY KEY of another table
  → Used to establish relationships between tables
  → CAN be NULL (unless constrained)
  → Can have duplicate values

SUPER KEY:
  → Any set of attributes that uniquely identifies a row
  → Candidate key ⊂ Super key (every candidate key is a super key)

COMPOSITE KEY:
  → Primary key made of TWO OR MORE columns

UNIQUE KEY:
  → Like primary key, but CAN have ONE NULL value
  → A table can have MULTIPLE unique keys
```

### 🚨 PYQ TRAP #2:
> Primary key: NULL → ❌ NOT ALLOWED | Duplicate → ❌ NOT ALLOWED
> Foreign key: NULL → ✅ ALLOWED | Duplicate → ✅ ALLOWED
> This distinction is the most frequently tested key concept!

---

## 🔷 BLOCK 3: ER Model

```
Entity       = real-world object (e.g., Student, Course)
Attribute    = property of entity (e.g., Roll No, Name)
Relationship = association between entities (e.g., ENROLLED_IN)

Cardinality types:
  1:1   → One-to-One   (one person has one passport)
  1:N   → One-to-Many  (one teacher has many students)
  M:N   → Many-to-Many (many students enrolled in many courses)

Weak Entity:
  → Cannot be uniquely identified without its "owner" entity
  → Represented with DOUBLE RECTANGLE in ER diagram
  → Has partial key (dashed underline)
  → Depends on strong entity for existence

Multivalued Attribute:
  → Can have more than one value for the same entity
  → Represented with DOUBLE ELLIPSE
  → Example: Phone numbers of a person
```

### 🚨 PYQ TRAP #3:
> Weak entity = **double rectangle** in ER diagram.
> Multivalued attribute = **double ellipse**.
> Derived attribute = **dashed ellipse**.

---

## 🔷 BLOCK 4: Normalization — The Exam Core

```
WHY NORMALIZE?
  → Remove redundancy
  → Eliminate insert/update/delete anomalies
  → Make data consistent

1NF (First Normal Form):
  → No multi-valued attributes
  → All values must be ATOMIC (indivisible)
  → Each column has a single value per row

2NF (Second Normal Form):
  → Must be in 1NF
  → No PARTIAL DEPENDENCY
  → Every non-key attribute must depend on the ENTIRE primary key
  → Only relevant when primary key is COMPOSITE

3NF (Third Normal Form):
  → Must be in 2NF
  → No TRANSITIVE DEPENDENCY
  → Non-key attributes must NOT depend on other non-key attributes
  → 3NF = ADEQUATE for normal relational database design ← MEMORIZE!

BCNF (Boyce-Codd Normal Form):
  → Stricter than 3NF
  → For every functional dependency X → Y, X must be a superkey
  → Eliminates all anomalies but may lose some dependencies
```

### 🚨 PYQ TRAP #4:
> **3NF is considered ADEQUATE for normal RDBMS design.**
> BCNF is stricter but not always achievable while preserving all dependencies.
> This exact statement appeared in TRE 2.0!

### Normalization Summary Table:
```
NF    | Eliminates
──────┼────────────────────────────────────────
1NF   | Multi-valued attributes (non-atomic data)
2NF   | Partial dependencies (on part of composite key)
3NF   | Transitive dependencies (non-key → non-key)
BCNF  | All functional dependency anomalies
```

---

## 🔷 BLOCK 5: SQL — All Clauses in One View

```
COMMAND TYPES:
  DDL → CREATE, ALTER, DROP, TRUNCATE (structure)
  DML → INSERT, UPDATE, DELETE (data manipulation)
  DCL → GRANT, REVOKE (permissions)
  TCL → COMMIT, ROLLBACK, SAVEPOINT (transactions)
  DQL → SELECT (data query)

SELECT QUERY ORDER (must follow this):
  SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY

KEY CLAUSE RULES:
  WHERE  → filters ROWS (before grouping)
  HAVING → filters GROUPS (after GROUP BY) — cannot use WHERE for groups!
  ORDER BY → default = ASC (ascending) ← PYQ TRAP
  GROUP BY → groups rows with same values
  WITH    → creates a TEMPORARY RELATION (common table expression)

ROUND() FUNCTION — CRITICAL PYQ:
  ROUND(65.726,  1) = 65.7  (rounds right of decimal)
  ROUND(65.726, -1) = 70    (rounds to nearest 10) ← APPEARED IN PYQ!
  ROUND(65.726, -2) = 100   (rounds to nearest 100)
  Negative second argument = rounds LEFT of decimal point

DELETE vs TRUNCATE vs DROP:
  DELETE   → removes specific rows, CAN ROLLBACK, slower
  TRUNCATE → removes ALL rows, CANNOT ROLLBACK, faster, resets auto-increment
  DROP     → removes entire table including structure

db_accessadmin role → used for adding/removing USER IDs

SQL Hierarchy (outermost to innermost):
  Environments → Catalogs → Schemas → Tables
```

### 🚨 PYQ TRAP #5:
> `HAVING` is used for filtering **GROUPS** (after GROUP BY).
> `WHERE` is used for filtering **ROWS** (before GROUP BY).
> You CANNOT use WHERE to filter grouped results — use HAVING.

### 🚨 PYQ TRAP #6:
> `ROUND(65.726, -1)` = **70** (not 65.7, not 66).
> The negative second argument rounds to the LEFT of the decimal.
> This appeared verbatim in TRE 2.0!

---

## 🔷 BLOCK 6: Transactions & ACID Properties

```
ACID = Atomicity + Consistency + Isolation + Durability

Atomicity   → All or nothing. Transaction completes fully OR rolls back fully.
Consistency → Database moves from one valid state to another valid state.
Isolation   → Concurrent transactions execute as if they were serial.
Durability  → Once committed, changes are PERMANENT (even after crash).

TCL Commands:
  COMMIT    → permanently saves all changes in the transaction
  ROLLBACK  → undoes all changes since last COMMIT
  SAVEPOINT → creates a checkpoint within a transaction for partial rollback

RAW data type:
  → Used to store UNSTRUCTURED data in a column
  → Does not enforce any format or structure
```

---

## 🔷 BLOCK 7: DBMS Views & Joins

```
VIEW = VIRTUAL TABLE
  → Not a stored data table
  → Computed on every query
  → Used for: security (hide columns), simplification, reusability

TYPES OF JOINS:
  INNER JOIN  → returns only matching rows from both tables
  LEFT JOIN   → all rows from left + matching from right (NULL if no match)
  RIGHT JOIN  → all rows from right + matching from left (NULL if no match)
  FULL JOIN   → all rows from both tables (NULL where no match)
  CROSS JOIN  → Cartesian product (every row of A × every row of B)
  NATURAL JOIN → joins on common column names automatically
                → described as "basic approach" for joining tables ← PYQ fact
```

---

## 📊 DBMS RAPID FIRE — 1-LINE RECALL TABLE

| Concept | Key Fact |
|---------|----------|
| DBMS key feature | MULTI-USER (not single-user) |
| Primary key | Unique + NOT NULL + only ONE per table |
| Foreign key | References primary key; CAN be NULL |
| Weak entity | Double rectangle in ER diagram |
| Multivalued attribute | Double ellipse in ER diagram |
| 1NF eliminates | Non-atomic (multi-valued) attributes |
| 2NF eliminates | Partial dependencies |
| 3NF eliminates | Transitive dependencies |
| 3NF is | ADEQUATE for normal RDBMS design |
| ORDER BY default | ASC (ascending) |
| HAVING clause | Filters GROUPS (after GROUP BY) |
| ROUND(65.726, -1) | **70** |
| TRUNCATE vs DELETE | TRUNCATE cannot be rolled back |
| Views | Virtual tables (not stored data) |
| Natural JOIN | Basic approach for joining |
| RAW data type | Stores unstructured data |
| db_accessadmin | Adds/removes user IDs |
| Filing cabinet = | Hierarchical DBMS model |

---
---

# PART 2: GENERAL STUDIES
## 🏛️ INA + Missing Modern History — PYQ-Focused Deep Dive

> **Why Day 50?** This entire week (Days 50–56) covers topics that appeared in TRE 1.0, 2.0, and 3.0 but were **missing** from earlier study plans. These are HIGH-PROBABILITY questions for TRE 4.0 because BPSC tends to repeat themes. Every fact below has been sourced from an actual PYQ.

---

## 🔷 SECTION 1: Indian National Army (INA) — Complete Story

### Background: The Context of INA

```
Setting: World War II (1939–1945)
         Japan advancing into Southeast Asia
         Indian soldiers captured as prisoners of war by Japan in Malaya & Singapore
         Idea: Use these soldiers to fight the British from OUTSIDE India
```

### The Founder — MOHAN SINGH (The Most Tested Fact):

```
INA FOUNDED BY → MOHAN SINGH
Year           → 1942
Place          → Singapore (after fall of Singapore to Japan)
Who was he?    → An officer in the British Indian Army
                 Captured by Japanese forces in Malaya
                 Agreed to organize Indian POWs into a fighting force

INA's full name → Azad Hind Fauj (Army of Free India)

⚠️ MOST COMMON EXAM TRAP:
   Many students write "Subhash Chandra Bose founded INA"
   WRONG! Mohan Singh founded INA in 1942.
   Bose came LATER and REORGANISED it.
```

### Subhash Chandra Bose — The Reorganizer:

```
Bose's Journey to INA:
  → Bose escaped from house arrest in India (1941)
  → Traveled to Germany first (met Hitler, got limited support)
  → Traveled by submarine to Southeast Asia
  → Arrived in Singapore (1943)
  → Took over INA leadership from Mohan Singh
  → REORGANISED and EXPANDED the INA

Bose's INA:
  → Established AZAD HIND GOVERNMENT (Provisional Government of Free India)
    in Singapore, October 1943
  → INA fought alongside Japanese forces in Burma and Northeast India
  → Reached Manipur (Imphal and Kohima) — closest point to Indian mainland
  → Failed due to Japanese defeat in the region (1944)

Famous Slogans by Bose:
  → "Jai Hind" — became India's national salute
  → "Give me blood, I will give you freedom"
  → "Delhi Chalo" (March to Delhi) — battle cry of INA
```

### INA Trials — Red Fort, Delhi:

```
When: 1945–1946 (after Japanese surrender, INA officers captured)
Where: RED FORT, DELHI ← PYQ TESTED

Three main accused (the "Three INA Officers"):
  → Shah Nawaz Khan
  → P.K. Sehgal
  → G.S. Dhillon

Defence lawyers: Jawaharlal Nehru, Bhulabhai Desai, Tej Bahadur Sapru
Outcome: British had to free the accused due to massive public outrage
Significance: INA trials sparked huge nationalist sentiment across India
              Naval Mutiny of 1946 followed → accelerated independence
```

### INA Complete Timeline:
```
1941 → Bose escapes India to Germany
1942 → Mohan Singh founds INA in Singapore (after fall of Singapore)
1943 → Bose takes over; Azad Hind Government formed (October 21, 1943)
1944 → INA fights in Manipur (Imphal-Kohima battles) — closest to India
1945 → Japan surrenders; INA collapses; Bose dies (August 18, 1945)
       INA officers arrested; Trials begin at Red Fort
1945–46 → INA Trials; public outrage; officers released
1946 → Royal Indian Navy Mutiny partly inspired by INA sentiment
1947 → India independent
```

---

## 🔷 SECTION 2: Missing Modern History PYQ Facts

> Every fact below appeared in TRE 1.0, TRE 2.0, or TRE 3.0. Learn each one as a standalone bullet — the exam will test them individually.

---

### 2.1 — "Prophet of New India"

```
"Prophet of New India" = RAJA RAM MOHAN ROY

Why this title?
  → He started the modern reform movement in India
  → Founded Brahmo Samaj (1828)
  → Campaigned against Sati, child marriage, untouchability
  → Supported English education and Western science
  → Called "Father of Indian Renaissance" and "Prophet of New India"
  → Died in Bristol, England (1833)

⚠️ TRAP: Don't confuse with "Father of Nation" (Gandhi)
         or "Maker of Modern India" (also used for Nehru sometimes)
```

---

### 2.2 — Anandamath and the Sannyasi Revolt

```
"Anandamath" = Novel by BANKIM CHANDRA CHATTOPADHYAY (1882)
Content: Describes the SANNYASI REVOLT (revolt by wandering monks/ascetics)
         Set in Bengal during the Bengal famine (1770)
         Fictional account inspired by REAL Sannyasi-Fakir Revolt (1763–1800)

Famous content:
  → Contains the poem "VANDE MATARAM" — became rallying song of independence movement
  → Vande Mataram = "I bow to thee, Mother" (praise of Mother India)

⚠️ MOST TESTED PYQ TRAP:
   Q: "What revolt does Anandamath describe?"
   A: SANNYASI REVOLT (NOT Sepoy Mutiny, NOT tribal revolt)
   This appeared in BOTH TRE 1.0 and TRE 2.0!
```

---

### 2.3 — 1857 as "First War of Independence"

```
Who described 1857 as "The First Indian War of Independence"?
→ V.D. SAVARKAR (Vinayak Damodar Savarkar)

His book: "The Indian War of Independence 1857" (written 1909, published 1909)
Significance: This was the FIRST systematic nationalist interpretation of 1857

British view of 1857: "Sepoy Mutiny" — a military rebellion
Indian nationalist view: "First War of Independence"
Savarkar's view: A planned national uprising, not just a sepoy mutiny

Other names given to 1857:
  → British: "Sepoy Mutiny" or "Indian Mutiny"
  → S.N. Sen: "Popular revolt"
  → R.C. Majumdar: Not a national war of independence (he disagreed with Savarkar)
```

---

### 2.4 — Abhinav Bharat Society

```
Founded by:  V.D. SAVARKAR
When:        1904
Where:       LONDON (India House, also called "Abhinav Bharat" in London)
Purpose:     Secret revolutionary society to overthrow British rule
             Planned armed revolution

⚠️ TRAP: Do NOT confuse with:
   → Shyamji Krishna Varma: Founded "India House" (the base), NOT Abhinav Bharat
   → P.M. Bapat: Associated with Nasik Conspiracy, not Abhinav Bharat
   → Correct answer: V.D. SAVARKAR founded Abhinav Bharat in London
```

---

### 2.5 — Ghadar Party

```
Founded:  1913
Where:    SAN FRANCISCO, USA (United States of America)
By:       Lala Har Dayal (main leader) + Sohan Singh Bhakna (president)
Members:  Mainly Indian immigrants in USA and Canada (Punjab origin)
Purpose:  Overthrow British rule in India through armed revolution
Name:     "Ghadar" = revolt/mutiny (Punjabi/Urdu)

Key event: During World War I (1914-15), Ghadar leaders tried to organize
           mass return to India and spark a revolution
           The plan failed due to British intelligence

⚠️ TRAP: Ghadar Party = USA (San Francisco), NOT UK, NOT Canada (though
         members were from Canada too, it was founded in USA)
```

---

### 2.6 — Bihar Socialist Party

```
Founded by: PHULAN PRASAD VARMA + JAYAPRAKASH NARAYAN
Year:       1931

Phulan Prasad Varma = first president
Jayaprakash Narayan (JP) = major figure, later became famous as
                           "Loknayak" during the 1974 JP Movement

Significance: Bihar had its own socialist tradition alongside the national movement
```

---

### 2.7 — Bihar Provincial Congress Committee

```
Formed: 1908
Where:  PATNA (Bihar)

Significance:
  → Organized Bihar's participation in the national movement
  → Champaran, Non-Cooperation, Civil Disobedience — all organized through this body
  → Rajendra Prasad was a key figure in Bihar Provincial Congress
```

---

### 2.8 — Anushilan Samiti (Patna Branch)

```
Anushilan Samiti:
  → Bengali revolutionary organization
  → Main branch: Calcutta (founded 1902 by Pramathanath Mitra)
  → Patna branch was established separately

Patna branch (1913):
  → Founded by SACHINDRA NATH SANYAL
  → Sanyal was a revolutionary who also worked with Rash Bihari Bose

⚠️ TRAP: Do NOT confuse Anushilan Samiti (Patna, 1913, Sachindra Nath Sanyal)
         with the Calcutta main branch (1902)
```

---

### 2.9 — Birsa Munda's Military Commander

```
Birsa Munda:
  → Tribal leader of the Munda community (Jharkhand/Bihar region)
  → Led "Ulgulan" (meaning "Great Tumult") revolt — 1899–1900
  → Against British land policies and missionary conversions

Birsa Munda appointed as Commander-in-Chief:
  → GAYA MUNDA

⚠️ TRAP: The question asks "Who did Birsa Munda appoint as Commander-in-Chief?"
         Answer = GAYA MUNDA (not Birsa himself as commander)
         Birsa was the supreme leader; Gaya Munda commanded the military operations
```

---

### 2.10 — Hindu College, Calcutta (1817)

```
Founded:   1817
Location:  Calcutta (Kolkata)
Founded by: DAVID HARE (primary founder)
            Also associated with: Alexander Duff, Raja Ram Mohan Roy

Henry Derozio:
  → Was a TEACHER at Hindu College (not founder)
  → Inspired the "Young Bengal Movement" — rational thinking, questioning orthodoxy
  → Students called "Derozians"

⚠️ TRAP: "Hindu College Calcutta was founded by ___?"
         Answer = DAVID HARE (not Derozio, not Duff alone)
         Derozio = teacher, not founder
```

---

## 🔷 SECTION 3: KEY FIGURES MASTER TABLE

| Person | What they did — PYQ tested fact |
|--------|----------------------------------|
| **Mohan Singh** | **Founded INA (1942, Singapore)** — #1 tested fact |
| **Subhash Chandra Bose** | Reorganised INA; Azad Hind Government; "Give me blood…"; "Jai Hind"; "Delhi Chalo" |
| **V.D. Savarkar** | Called 1857 "First War of Independence"; Founded Abhinav Bharat (London) |
| **Raja Ram Mohan Roy** | "Prophet of New India"; Brahmo Samaj; Anti-Sati; Father of Renaissance |
| **Bankim Chandra** | Wrote Anandamath (Sannyasi revolt); Vande Mataram |
| **Lala Har Dayal** | Founded Ghadar Party (USA, San Francisco, 1913) |
| **Phulan Prasad Varma + J.P. Narayan** | Founded Bihar Socialist Party (1931) |
| **Sachindra Nath Sanyal** | Established Anushilan Samiti Patna branch (1913) |
| **Birsa Munda** | Led Ulgulan revolt 1899–1900; appointed GAYA MUNDA as Commander-in-Chief |
| **Gaya Munda** | Commander-in-Chief under Birsa Munda |
| **David Hare** | Founded Hindu College Calcutta (1817) |
| **Henry Derozio** | Teacher at Hindu College; Young Bengal Movement |
| **Shah Nawaz Khan** | INA trial accused at Red Fort |

---

## 🔷 SECTION 4: COMPARISON TABLE — INA vs Other Organisations

| Feature | INA (Azad Hind Fauj) | Ghadar Party | Anushilan Samiti |
|---------|---------------------|--------------|-----------------|
| Founded | 1942 | 1913 | 1902 (Calcutta) / 1913 (Patna) |
| Founded by | Mohan Singh | Lala Har Dayal | Pramathanath Mitra / Sachindra Nath Sanyal |
| Location | Singapore | San Francisco, USA | Bengal/Bihar |
| Method | Military (armed) | Revolutionary | Revolutionary |
| Context | World War II | World War I | Pre-WWI nationalism |
| Famous for | Fighting alongside Japan against British | Indian diaspora revolution attempt | Revolutionary nationalism in Bengal/Bihar |

---

## 🔷 SECTION 5: MEMORY TRICKS

```
INA MEMORY TRICK:
  "MOHAN STARTED, BOSE COMPLETED"
  → Mohan Singh started INA (1942)
  → Bose reorganised and completed the mission (1943)

SAVARKAR = TWO THINGS:
  1. Wrote "First War of Independence" (about 1857)
  2. Founded Abhinav Bharat (in London)
  Both = Savarkar!

GHADAR PARTY = USA
  "GAH-dur" sounds like "Gardner" — think of Gardens of San Francisco (Golden Gate Park)
  Ghadar = USA (San Francisco) 1913

ANANDAMATH = SANNYASI revolt (NOT Sepoy)
  "ANA" in Anandamath → "ANA" monks/sannyasis
  Novel about MONKS fighting the British

PROPHET of New India = RAJA RAM MOHAN ROY
  "Prophet" = one who predicts the future direction
  Roy predicted and shaped MODERN India → Prophet of New India

HINDU COLLEGE = DAVID HARE (not Derozio)
  HARE started it → Derozio TAUGHT there
  "Hare ran the place; Derozio had the grace"
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topic: DBMS — All Concepts (Normalization, SQL, Keys, ER Model)

---

**Q1.** Which of the following is a key feature of a Database Management System (DBMS)?
(A) It supports only a single user at a time
(B) It provides multi-user access with data integrity
(C) It stores data in flat files without relationships
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is TRUE about a Primary Key?
(A) It can contain NULL values
(B) A table can have more than one primary key
(C) It uniquely identifies each row and cannot be NULL
(D) More than one of the above
(E) None of the above

---

**Q3.** A Foreign Key in a relational database:
(A) Must always have a unique value in its own table
(B) References the Primary Key of another table
(C) Cannot contain NULL values
(D) More than one of the above
(E) None of the above

---

**Q4.** The difference between a Candidate Key and a Super Key is:
(A) Candidate key = minimal super key (no extra attributes)
(B) Super key contains all candidate keys and possibly more
(C) Every candidate key is a super key, but not vice versa
(D) More than one of the above
(E) None of the above

---

**Q5.** In an ER diagram, a Weak Entity is represented by:
(A) A single rectangle
(B) A double ellipse
(C) A double rectangle
(D) More than one of the above
(E) None of the above

---

**Q6.** A multivalued attribute in an ER diagram is represented by:
(A) A dashed ellipse
(B) A double ellipse
(C) A double rectangle
(D) More than one of the above
(E) None of the above

---

**Q7.** First Normal Form (1NF) requires:
(A) Removal of partial dependencies
(B) All attribute values to be atomic (no multi-valued attributes)
(C) Removal of transitive dependencies
(D) More than one of the above
(E) None of the above

---

**Q8.** Second Normal Form (2NF) eliminates:
(A) Transitive dependencies
(B) Partial dependencies on the primary key
(C) Multi-valued attributes
(D) More than one of the above
(E) None of the above

---

**Q9.** Which normal form is considered ADEQUATE for a normal relational database design?
(A) 1NF
(B) 2NF
(C) 3NF
(D) More than one of the above
(E) None of the above

---

**Q10.** The HAVING clause in SQL is used to:
(A) Filter rows before grouping
(B) Sort the result in ascending order
(C) Filter groups after a GROUP BY operation
(D) More than one of the above
(E) None of the above

---

**Q11.** What is the default sort order of the ORDER BY clause in SQL?
(A) DESC (Descending)
(B) ASC (Ascending)
(C) Random
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the result of `ROUND(65.726, -1)` in SQL?
(A) 65.7
(B) 66
(C) 70
(D) More than one of the above
(E) None of the above

---

**Q13.** The correct order of clauses in a SQL SELECT statement is:
(A) SELECT → WHERE → FROM → GROUP BY → HAVING → ORDER BY
(B) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
(C) SELECT → FROM → GROUP BY → WHERE → ORDER BY → HAVING
(D) More than one of the above
(E) None of the above

---

**Q14.** Which SQL command removes ALL rows from a table, cannot be rolled back, and resets auto-increment?
(A) DELETE
(B) DROP
(C) TRUNCATE
(D) More than one of the above
(E) None of the above

---

**Q15.** A SQL VIEW is:
(A) A physical copy of a table stored on disk
(B) A virtual table computed on every query
(C) A backup table for transaction rollback
(D) More than one of the above
(E) None of the above

---

**Q16.** Which type of JOIN returns all rows from both tables, with NULL where there is no match?
(A) INNER JOIN
(B) LEFT JOIN
(C) FULL OUTER JOIN
(D) More than one of the above
(E) None of the above

---

**Q17.** NATURAL JOIN is described as:
(A) A join that creates the Cartesian product of two tables
(B) A basic approach to joining tables (joins on common column names)
(C) A join that can only be used with Primary and Foreign keys
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following is a Transaction Control Language (TCL) command?
(A) GRANT
(B) TRUNCATE
(C) SAVEPOINT
(D) More than one of the above
(E) None of the above

---

**Q19.** The ACID property that ensures a transaction is treated as "all or nothing" is:
(A) Consistency
(B) Isolation
(C) Atomicity
(D) More than one of the above
(E) None of the above

---

**Q20.** The `RAW` data type in SQL is used to store:
(A) Large text data
(B) Structured numeric data only
(C) Unstructured data in a column
(D) More than one of the above
(E) None of the above

---

**Q21.** The SQL hierarchy from outermost to innermost is:
(A) Catalogs → Environments → Schemas → Tables
(B) Environments → Catalogs → Schemas → Tables
(C) Schemas → Catalogs → Environments → Tables
(D) More than one of the above
(E) None of the above

---

**Q22.** BCNF (Boyce-Codd Normal Form) is:
(A) Weaker than 3NF
(B) Stricter than 3NF
(C) The same as 3NF but with a different name
(D) More than one of the above
(E) None of the above

---

**Q23.** Which DBMS model is described as organizing data like "a traditional filing cabinet organized by customer"?
(A) Relational DBMS
(B) Object-Oriented DBMS
(C) Hierarchical DBMS
(D) More than one of the above
(E) None of the above

---

**Q24.** The `db_accessadmin` role in a database is used for:
(A) Backing up and restoring databases
(B) Adding and removing user IDs for database access
(C) Creating and dropping tables
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following correctly describes 3NF?
(A) It only requires atomic values (no multi-valued attributes)
(B) A relation is in 3NF if there are no transitive dependencies among non-key attributes
(C) 3NF is more strict than BCNF
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### INA + Missing Modern History PYQs

---

**Q26.** Who was the FOUNDER of the Indian National Army (INA)?
(A) Subhash Chandra Bose
(B) Mohan Singh
(C) Rash Bihari Bose
(D) More than one of the above
(E) None of the above

---

**Q27.** The Indian National Army (INA) was also known as:
(A) Azad Hind Fauj
(B) Bharatiya Sena
(C) Swadhin Fauj
(D) More than one of the above
(E) None of the above

---

**Q28.** Where was the INA founded?
(A) Tokyo, Japan
(B) Berlin, Germany
(C) Singapore
(D) More than one of the above
(E) None of the above

---

**Q29.** The INA Trials of 1945–46 were held at:
(A) Victoria Memorial, Calcutta
(B) Red Fort, Delhi
(C) Gateway of India, Bombay
(D) More than one of the above
(E) None of the above

---

**Q30.** The famous slogan "Give me blood, I will give you freedom" was given by:
(A) Mohan Singh
(B) Bhagat Singh
(C) Subhash Chandra Bose
(D) More than one of the above
(E) None of the above

---

**Q31.** Subhash Chandra Bose established the "Azad Hind Government" (Provisional Government of Free India) in:
(A) Berlin, Germany (1942)
(B) Singapore (October 1943)
(C) Tokyo, Japan (1944)
(D) More than one of the above
(E) None of the above

---

**Q32.** The title "Prophet of New India" is associated with:
(A) Mahatma Gandhi
(B) Jawaharlal Nehru
(C) Raja Ram Mohan Roy
(D) More than one of the above
(E) None of the above

---

**Q33.** The novel "Anandamath" written by Bankim Chandra Chattopadhyay describes which revolt?
(A) Sepoy Mutiny of 1857
(B) Sannyasi Revolt
(C) Santhal Rebellion
(D) More than one of the above
(E) None of the above

---

**Q34.** Who described the revolt of 1857 as "The First Indian War of Independence"?
(A) Jawaharlal Nehru
(B) Bal Gangadhar Tilak
(C) V.D. Savarkar
(D) More than one of the above
(E) None of the above

---

**Q35.** "Abhinav Bharat" society in London was founded by:
(A) Shyamji Krishna Varma
(B) P.M. Bapat
(C) V.D. Savarkar
(D) More than one of the above
(E) None of the above

---

**Q36.** The Ghadar Party was established in:
(A) London, United Kingdom
(B) San Francisco, USA
(C) Toronto, Canada
(D) More than one of the above
(E) None of the above

---

**Q37.** The Ghadar Party was founded in the year:
(A) 1905
(B) 1913
(C) 1920
(D) More than one of the above
(E) None of the above

---

**Q38.** The Bihar Socialist Party was founded by:
(A) Jayaprakash Narayan alone
(B) Phulan Prasad Varma and Jayaprakash Narayan
(C) Rajendra Prasad and Jayaprakash Narayan
(D) More than one of the above
(E) None of the above

---

**Q39.** The Bihar Provincial Congress Committee was formed in which year and city?
(A) 1905, Patna
(B) 1908, Patna
(C) 1916, Lucknow
(D) More than one of the above
(E) None of the above

---

**Q40.** The Patna branch of Anushilan Samiti (1913) was established by:
(A) Rash Bihari Bose
(B) Aurobindo Ghosh
(C) Sachindra Nath Sanyal
(D) More than one of the above
(E) None of the above

---

**Q41.** Who did Birsa Munda appoint as Commander-in-Chief of his forces?
(A) Sidhu Murmu
(B) Kanhu Murmu
(C) Gaya Munda
(D) More than one of the above
(E) None of the above

---

**Q42.** Hindu College, Calcutta (1817) was primarily founded by:
(A) Henry Derozio
(B) David Hare
(C) Raja Ram Mohan Roy
(D) More than one of the above
(E) None of the above

---

**Q43.** Henry Derozio's connection to Hindu College, Calcutta was as a:
(A) Co-founder
(B) First principal
(C) Teacher who inspired the Young Bengal Movement
(D) More than one of the above
(E) None of the above

---

**Q44.** The Vande Mataram song first appeared in which literary work?
(A) Gitanjali by Rabindranath Tagore
(B) Anandamath by Bankim Chandra Chattopadhyay
(C) Gora by Rabindranath Tagore
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following is TRUE about the INA under Subhash Chandra Bose?
(A) INA fought alongside Allied forces against Japan
(B) INA fought alongside Japan against British India
(C) INA never reached Indian territory
(D) More than one of the above
(E) None of the above

---

**Q46.** The Ghadar Party's membership mainly came from:
(A) Bengali intellectuals in Calcutta
(B) Indian immigrants (mainly Punjabi) in USA and Canada
(C) Students studying in Britain
(D) More than one of the above
(E) None of the above

---

**Q47.** Birsa Munda's revolt ("Ulgulan") was primarily against:
(A) British land policies and missionary activities
(B) Forced indigo cultivation (Tinkathia system)
(C) Salt tax imposed by the British
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following CORRECTLY matches the organization with its founder?
(A) Ghadar Party — Lala Har Dayal | Abhinav Bharat — V.D. Savarkar
(B) INA — Subhash Chandra Bose | Brahmo Samaj — Bankim Chandra
(C) Anushilan Samiti (Patna) — Rash Bihari Bose
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following CHRONOLOGICAL ORDER is correct?
1. Founding of Hindu College, Calcutta
2. Founding of Ghadar Party
3. Founding of INA by Mohan Singh
4. INA Trials at Red Fort

(A) 1 → 2 → 3 → 4
(B) 2 → 1 → 3 → 4
(C) 1 → 3 → 2 → 4
(D) More than one of the above
(E) None of the above

---

**Q50.** The famous "Delhi Chalo" (March to Delhi) slogan was associated with:
(A) The Non-Cooperation Movement of 1920
(B) The INA under Subhash Chandra Bose
(C) The Quit India Movement of 1942
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ Attempt all 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (B) | DBMS = multi-user + data integrity — core feature |
| 2 | (C) | Primary key = unique + NOT NULL; only one per table |
| 3 | (B) | Foreign key references primary key of another table |
| 4 | (D) | All three options about candidate key vs super key are correct |
| 5 | (C) | Weak entity = double rectangle in ER diagram |
| 6 | (B) | Multivalued attribute = double ellipse |
| 7 | (B) | 1NF = atomic values (no multi-valued attributes) |
| 8 | (B) | 2NF = no partial dependencies (on composite key) |
| 9 | (C) | 3NF = adequate for normal RDBMS design — PYQ tested! |
| 10 | (C) | HAVING filters groups (after GROUP BY) |
| 11 | (B) | ORDER BY default = ASC (ascending) |
| 12 | (C) | ROUND(65.726, -1) = 70 (rounds to nearest 10) |
| 13 | (B) | SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY |
| 14 | (C) | TRUNCATE = removes all rows, cannot rollback |
| 15 | (B) | View = virtual table, computed on every query |
| 16 | (C) | FULL OUTER JOIN = all rows from both, NULL where no match |
| 17 | (B) | Natural JOIN = basic approach, joins on common column names |
| 18 | (C) | SAVEPOINT is TCL; GRANT=DCL; TRUNCATE=DDL |
| 19 | (C) | Atomicity = all or nothing |
| 20 | (C) | RAW data type = stores unstructured data |
| 21 | (B) | Environments → Catalogs → Schemas → Tables |
| 22 | (B) | BCNF is STRICTER than 3NF |
| 23 | (C) | Filing cabinet by customer = Hierarchical DBMS |
| 24 | (B) | db_accessadmin = adding/removing user IDs |
| 25 | (B) | 3NF = no transitive dependencies among non-key attributes |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Mohan Singh founded INA in 1942 — NOT Bose |
| 27 | (A) | INA = Azad Hind Fauj |
| 28 | (C) | INA founded in Singapore (after its fall to Japan) |
| 29 | (B) | INA Trials held at Red Fort, Delhi (1945–46) |
| 30 | (C) | "Give me blood…" = Subhash Chandra Bose's slogan |
| 31 | (B) | Azad Hind Government = Singapore, October 21, 1943 |
| 32 | (C) | "Prophet of New India" = Raja Ram Mohan Roy |
| 33 | (B) | Anandamath describes the SANNYASI revolt |
| 34 | (C) | 1857 as "First War of Independence" = V.D. Savarkar |
| 35 | (C) | Abhinav Bharat (London) = V.D. Savarkar |
| 36 | (B) | Ghadar Party = San Francisco, USA |
| 37 | (B) | Ghadar Party founded 1913 |
| 38 | (B) | Bihar Socialist Party = Phulan Prasad Varma + JP Narayan |
| 39 | (B) | Bihar Provincial Congress = 1908, Patna |
| 40 | (C) | Anushilan Samiti Patna (1913) = Sachindra Nath Sanyal |
| 41 | (C) | Birsa Munda appointed GAYA MUNDA as Commander-in-Chief |
| 42 | (B) | Hindu College Calcutta (1817) = David Hare (primary founder) |
| 43 | (C) | Derozio = Teacher at Hindu College, inspired Young Bengal |
| 44 | (B) | Vande Mataram = from Anandamath by Bankim Chandra |
| 45 | (B) | INA fought alongside JAPAN against British India |
| 46 | (B) | Ghadar Party = Indian immigrants (Punjabi) in USA/Canada |
| 47 | (A) | Ulgulan = against British land policies + missionary activities |
| 48 | (A) | Ghadar→Lala Har Dayal; Abhinav Bharat→Savarkar — BOTH CORRECT |
| 49 | (A) | 1817 Hindu College → 1913 Ghadar → 1942 INA → 1945 Trials |
| 50 | (B) | "Delhi Chalo" = INA under Subhash Chandra Bose |

---
---

# 🔁 DAY 50 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — DBMS Key Facts

```
Core Rules:
  DBMS = MULTI-USER (single-user = limitation of file systems)
  Primary key = NOT NULL + UNIQUE + only ONE per table
  Foreign key = CAN be NULL + CAN have duplicates
  Weak entity = DOUBLE RECTANGLE in ER diagram
  Multivalued attribute = DOUBLE ELLIPSE

Normalization:
  1NF = no multi-valued (non-atomic) attributes
  2NF = no partial dependencies (composite key scenarios)
  3NF = no transitive dependencies → ADEQUATE for normal RDBMS
  BCNF = stricter than 3NF

SQL PYQ-Tested Rules:
  ORDER BY default     = ASC
  HAVING               = filters GROUPS (not rows)
  WHERE                = filters ROWS (not groups)
  ROUND(65.726, -1)    = 70   ← PYQ exact question
  TRUNCATE             = cannot rollback
  VIEW                 = virtual table
  Natural JOIN         = basic approach to joining
  RAW data type        = unstructured data storage
  db_accessadmin       = add/remove user IDs
  SQL hierarchy: Environments → Catalogs → Schemas → Tables
  Hierarchical DBMS    = filing cabinet by customer (PYQ analogy)
```

---

## ⚡ RAPID FIRE — INA & Modern History

```
INA CORE FACTS:
  Founder       = MOHAN SINGH (1942, Singapore)
  Full name     = Azad Hind Fauj
  Bose's role   = Reorganised INA (1943); Azad Hind Government (Oct 21, 1943)
  INA fought    = alongside JAPAN against British India
  INA Trials    = RED FORT, Delhi (1945–46)
  Bose slogans  = "Jai Hind", "Give me blood I will give you freedom", "Delhi Chalo"

MISSING MODERN HISTORY:
  Prophet of New India          = RAJA RAM MOHAN ROY
  Anandamath → revolt described = SANNYASI REVOLT (NOT Sepoy)
  1857 "First War of Independ." = V.D. SAVARKAR (wrote this)
  Abhinav Bharat (London)       = V.D. SAVARKAR (not Shyamji Krishna Varma)
  Ghadar Party                  = San Francisco, USA, 1913 (Lala Har Dayal)
  Bihar Socialist Party         = Phulan Prasad Varma + J.P. Narayan (1931)
  Bihar Provincial Congress     = 1908, Patna
  Anushilan Samiti Patna (1913) = Sachindra Nath Sanyal
  Birsa Munda's C-in-C          = GAYA MUNDA
  Hindu College Calcutta (1817) = David Hare (founder); Derozio = Teacher
  Vande Mataram appeared in     = Anandamath (Bankim Chandra)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. INA was founded by **MOHAN SINGH** in 1942 (Singapore) — Bose reorganised it later; INA Trials = Red Fort
2. "Prophet of New India" = Raja Ram Mohan Roy; Anandamath = Sannyasi revolt (NOT 1857)
3. Abhinav Bharat (London) = V.D. Savarkar; Ghadar Party = USA, 1913 (Lala Har Dayal)
4. DBMS = multi-user; 3NF = adequate for RDBMS; ROUND(65.726, -1) = 70; HAVING = groups
5. Birsa Munda appointed **Gaya Munda** as Commander-in-Chief; Hindu College = David Hare (founder)

---

*Next: Day 51 — Tana Bhagat, Santhal Rebellion, Birsa Munda Timeline + INC Sessions*
