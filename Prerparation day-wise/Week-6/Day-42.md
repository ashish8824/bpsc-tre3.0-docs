# 📅 BPSC TRE 4.0 — DAY 42
## 🔁 REVISION DAY — DBMS Complete Review (Days 36–41)
## GS Topic: Modern Indian History — Socio-Religious Reforms + Freedom Struggle

> **Target:** 130+/150 | Top 50 Rank
> **Day 42 Strategy:** This is a POWER REVISION day. Every concept is condensed, every PYQ trap highlighted.
> Today = Consolidate everything → Score 20+/25 in DBMS questions in actual exam!

---

# ═══════════════════════════════════════════════════════
# 📘 PART 1: CS — COMPLETE DBMS REVISION (Days 36–41)
# ═══════════════════════════════════════════════════════

## 🗺️ DBMS MASTER MAP — Everything at a Glance

```
                    ┌─────────────────────────────────────┐
                    │         DATABASE CONCEPTS           │
                    └──────────────┬──────────────────────┘
                                   │
         ┌─────────────────────────┼──────────────────────────┐
         ▼                         ▼                          ▼
   ┌───────────┐          ┌──────────────┐          ┌──────────────────┐
   │  DATABASE │          │  DATA MODELS │          │  DBMS vs File    │
   │  CONCEPTS │          │  ER Diagram  │          │  System          │
   └─────┬─────┘          └──────┬───────┘          └──────────────────┘
         │                       │
         ▼                       ▼
   ┌───────────┐          ┌──────────────┐
   │   KEYS    │          │ NORMALIZATION│
   │ PK,FK,SK  │          │ 1NF→2NF→    │
   └─────┬─────┘          │ 3NF→BCNF    │
         │                └──────┬───────┘
         ▼                       │
   ┌───────────────────────────────────────────────────────────────────┐
   │                     SQL COMMANDS                                  │
   ├──────────────────────────────────────────────────────────────────┤
   │  DDL           DML            DCL           TCL                  │
   │  CREATE        SELECT         GRANT         COMMIT               │
   │  ALTER         INSERT         REVOKE        ROLLBACK             │
   │  DROP          UPDATE                       SAVEPOINT            │
   │  TRUNCATE      DELETE                                            │
   └──────────────────────────────────────────────────────────────────┘
```

---

## 🔵 BLOCK 1: DATABASE FUNDAMENTALS (Day 36 Revision)

### What is a DBMS?
**Database Management System** = Software that manages databases. It sits between the user/application and the actual database.

```
USER / APPLICATION
        │
        ▼
   ┌─────────┐
   │  DBMS   │  ← Manages access, security, concurrency
   └────┬────┘
        │
        ▼
   [DATABASE]
```

### Key DBMS Features (What DBMS DOES support):
```
✅ Reduces data redundancy
✅ Ensures data security
✅ Supports MULTI-USER access (concurrent)
✅ Provides data integrity
✅ Provides backup and recovery
✅ Data abstraction (hides complexity)
```

### What DBMS does NOT support:
```
❌ Single-user access ONLY  ← PYQ TRAP — "DBMS does NOT support single-user only"
```

### Types of DBMS:
```
┌─────────────────┬────────────────────────────────────────────────────┐
│ Type            │ Description + Example                              │
├─────────────────┼────────────────────────────────────────────────────┤
│ Relational DBMS │ Data in tables (rows/columns). SQL used.          │
│ (RDBMS)         │ Examples: MySQL, Oracle, PostgreSQL, MS SQL Server│
├─────────────────┼────────────────────────────────────────────────────┤
│ Network DBMS    │ Record-based, many-to-many links                  │
│                 │ Example: Integrated Data Store (IDS)               │
├─────────────────┼────────────────────────────────────────────────────┤
│ Hierarchical    │ Tree structure, parent-child relationships         │
│ DBMS            │ Example: IBM IMS                                   │
├─────────────────┼────────────────────────────────────────────────────┤
│ Distributed     │ Data spread across multiple locations/systems      │
│ DBMS            │ Example: Apache Cassandra                          │
└─────────────────┴────────────────────────────────────────────────────┘
```

> **🔔 PYQ TRAPS from Day 36:**
> - Google is **NOT** a DBMS — it is a Search Engine
> - Types of DBMS = Relational, Network, Hierarchical, Distributed (NOT "Decentralized")
> - DBMS acts as interface between **database application** and the **database**

### Relational Model Key Terms:
```
Relation  =  TABLE
Tuple     =  ROW (one record)
Attribute =  COLUMN (one field)
Domain    =  Set of valid values for an attribute
Metadata  =  Data about data (schema — table structure)
Cardinality = Number of ROWS (tuples) in a table
Degree    =  Number of COLUMNS (attributes) in a table
```

---

## 🟡 BLOCK 2: KEYS IN DBMS (Day 37 Revision)

### The Key Hierarchy:

```
SUPERKEY
    │  (all superkeys — any combo that uniquely identifies)
    ▼
CANDIDATE KEY  (minimal superkeys — no redundant attributes)
    │
    ├──► PRIMARY KEY  (chosen candidate key — only ONE per table)
    │                  NOT NULL + UNIQUE
    │
    └──► ALTERNATE KEY (candidate keys NOT chosen as PK)


FOREIGN KEY  (references PRIMARY KEY of another table)
             enforces REFERENTIAL INTEGRITY
```

### Critical Key Differences:
```
┌─────────────────┬──────────────────┬───────────────────────────────────────┐
│ Key Type        │ NULL Allowed?    │ How Many Per Table?                   │
├─────────────────┼──────────────────┼───────────────────────────────────────┤
│ Primary Key     │ NO (NOT NULL)    │ Only ONE                              │
│ Unique Key      │ YES              │ Multiple allowed                      │
│ Foreign Key     │ YES              │ Multiple allowed                      │
│ Candidate Key   │ NO               │ Multiple (but only one becomes PK)    │
│ Super Key       │ NO               │ Multiple                              │
└─────────────────┴──────────────────┴───────────────────────────────────────┘
```

> **🔔 PYQ TRAPS from Day 37:**
> - Only **1 PRIMARY KEY** per table (this is asked directly)
> - **UNIQUE key allows NULL** — Primary Key does NOT
> - Foreign Key references the **Primary Key** of another table
> - **Referential Integrity** = FK value must exist in the referenced table

---

## 🟢 BLOCK 3: ER MODEL & RELATIONAL MODEL (Day 38 Revision)

### ER Diagram — Key Shapes:
```
ENTITY        →  Rectangle  [  Student  ]
ATTRIBUTE     →  Ellipse    (  Roll_No  )
RELATIONSHIP  →  Diamond    <  Enrolls  >
WEAK ENTITY   →  Double Rectangle  [[ Order ]]
KEY ATTRIBUTE →  Underlined ellipse

Multivalued Attribute  →  Double ellipse   (( Phone ))
Derived Attribute      →  Dashed ellipse   - - Age - -
```

### Cardinality Types:
```
1:1  (One-to-One)    →  One student has one ID card
1:N  (One-to-Many)   →  One teacher teaches many students
M:N  (Many-to-Many)  →  Many students enrol in many courses
```

### Strong vs Weak Entity:
```
STRONG ENTITY:               WEAK ENTITY:
• Has its own Primary Key    • No Primary Key of its own
• Exists independently       • Depends on a Strong Entity (owner)
• Single Rectangle           • Double Rectangle
• Example: Student           • Example: Order Item (depends on Order)
```

> **🔔 PYQ TRAPS from Day 38:**
> - **Metadata** = information about data (data about data) = schema
> - **Relation = Table**, **Tuple = Row**, **Attribute = Column**
> - Weak entity uses **partial key + owner's PK** = composite identifier

---

## 🔴 BLOCK 4: NORMALIZATION — THE COMPLETE STAIRCASE (Day 39 Revision)

### Why Normalize?
Data stored in two places → **Wasted space + Data inconsistency** (BOTH — PYQ answer is D)

### The 4 Normal Forms — Quick Recap:

```
┌────────┬─────────────────────────────┬──────────────────────────────────┐
│  Form  │  What It REMOVES            │  Key Rule                        │
├────────┼─────────────────────────────┼──────────────────────────────────┤
│  1NF   │  Multi-valued attributes    │  Every cell = atomic value       │
│        │  Repeating groups           │  No lists in a single cell       │
├────────┼─────────────────────────────┼──────────────────────────────────┤
│  2NF   │  Partial dependencies       │  In 1NF + every non-key          │
│        │  (on part of composite PK)  │  attribute depends on FULL PK    │
│        │  Only applies if PK is      │  ★ Only matters with             │
│        │  COMPOSITE                  │    COMPOSITE primary key         │
├────────┼─────────────────────────────┼──────────────────────────────────┤
│  3NF   │  Transitive dependencies    │  In 2NF + no non-key attr        │
│        │  (non-key → non-key)        │  depends on another non-key attr │
│        │                             │  ★ ADEQUATE for normal RDBMS     │
├────────┼─────────────────────────────┼──────────────────────────────────┤
│  BCNF  │  Every FD where LHS is      │  For every FD X→Y,               │
│        │  not a superkey             │  X must be a SUPERKEY            │
│        │                             │  ★ Stricter than 3NF             │
└────────┴─────────────────────────────┴──────────────────────────────────┘
```

### Functional Dependency Quick Reference:
```
A → B           =  A determines B (knowing A gives exact B)
FULL FD         =  A,B → C  and NEITHER A alone nor B alone → C
PARTIAL FD      =  A,B → C  but also  A alone → C  (B is redundant)
TRANSITIVE FD   =  A → B and B → C  therefore  A → C (via B)
```

> **🔔 CRITICAL PYQ FACTS (Day 39):**
> - **3NF = adequate for normal RDBMS design** (most asked)
> - **2NF removes partial dependencies**
> - **3NF removes transitive dependencies**
> - **BCNF** = every determinant must be a superkey
> - Single-column PK → automatically in **2NF** (no partial deps possible)

---

## 🟣 BLOCK 5: SQL COMMANDS — ALL CATEGORIES (Day 40 Revision)

### The SQL Command Master Table:

```
┌────────────┬──────────────────────────────────────────────────────────────────┐
│ Category   │ Commands + Key Facts                                            │
├────────────┼──────────────────────────────────────────────────────────────────┤
│ DDL        │ CREATE, ALTER, DROP, TRUNCATE, RENAME                           │
│ (Structure)│ • AUTO-COMMITTED — cannot be rolled back!                       │
│            │ • TRUNCATE = DDL (not DML) — removes all rows, keeps structure  │
├────────────┼──────────────────────────────────────────────────────────────────┤
│ DML        │ SELECT, INSERT, UPDATE, DELETE                                  │
│ (Data)     │ • NOT auto-committed — needs explicit COMMIT                    │
│            │ • DELETE = DML — CAN be rolled back ← PYQ trap                 │
├────────────┼──────────────────────────────────────────────────────────────────┤
│ DCL        │ GRANT, REVOKE                                                   │
│(Permissions│ • GRANT = give permissions                                      │
│            │ • REVOKE = remove permissions                                   │
├────────────┼──────────────────────────────────────────────────────────────────┤
│ TCL        │ COMMIT, ROLLBACK, SAVEPOINT, SET TRANSACTION                    │
│(Transactions│• COMMIT = permanent ★ PYQ                                     │
│            │ • ROLLBACK = undo all uncommitted changes ★ PYQ                │
│            │ • SAVEPOINT = intermediate checkpoint for partial rollback      │
└────────────┴──────────────────────────────────────────────────────────────────┘
```

### The DROP vs TRUNCATE vs DELETE Triangle:

```
            REMOVES ALL   REMOVES         REMOVES SPECIFIC
            STRUCTURE     ALL ROWS        ROWS (with WHERE)
            + DATA        (keeps table)
               │                │                │
               ▼                ▼                ▼
            DROP           TRUNCATE          DELETE
            (DDL)           (DDL)            (DML)
               │                │                │
               ▼                ▼                ▼
          Cannot          Cannot           CAN be
          rollback        rollback         rolled back!
```

### SQL Constraints Quick Recap:
```
Valid Constraints:    PRIMARY KEY | NOT NULL | UNIQUE | FOREIGN KEY | CHECK | DEFAULT
NOT a Constraint:    UNION  ← Direct PYQ trap! (UNION is a SET OPERATION)
```

> **🔔 CRITICAL PYQ FACTS (Day 40):**
> - TRUNCATE = DDL, cannot rollback. DELETE = DML, can rollback
> - COMMIT = permanent | ROLLBACK = undo
> - GRANT/REVOKE = DCL commands
> - UNION is NOT a constraint
> - SQL developed by IBM (declarative language)

---

## 🔵 BLOCK 6: SQL SELECT — CLAUSES & FUNCTIONS (Day 41 Revision)

### The SELECT Execution Pipeline:

```
Step 1: FROM       →  Identify the source table(s)
Step 2: WHERE      →  Filter individual ROWS (NO aggregate functions here!)
Step 3: GROUP BY   →  Group remaining rows
Step 4: HAVING     →  Filter GROUPS (aggregate functions allowed here!)
Step 5: SELECT     →  Choose columns + apply aggregates
Step 6: ORDER BY   →  Sort the output
Step 7: LIMIT      →  Restrict number of rows returned
```

### WHERE vs HAVING — The Eternal Trap:

```
      ALL ROWS                  GROUPED ROWS
         │                           │
         │  WHERE filters here       │  HAVING filters here
         │  (individual rows)        │  (groups — use aggregates!)
         │                           │
    ┌────▼────┐                ┌─────▼─────┐
    │WHERE    │ ──GROUP BY──►  │ HAVING    │
    │Marks>80 │                │COUNT(*)>2 │
    └─────────┘                └───────────┘

RULE: If your filter uses COUNT/SUM/AVG/MAX/MIN → use HAVING
      If your filter uses regular column values → use WHERE
```

### Aggregate Functions — Valid vs Invalid:

```
VALID (memorize all 5):              INVALID (direct PYQ trap):
✅ COUNT(*)  — counts all rows       ❌ COMPUTE  ← NOT a valid function!
✅ COUNT(col)— counts non-NULLs
✅ SUM(col)  — adds values
✅ AVG(col)  — average
✅ MAX(col)  — maximum value
✅ MIN(col)  — minimum value

All of COUNT, SUM, AVG, MAX, MIN → IGNORE NULL values
EXCEPT COUNT(*) which counts NULLs too
```

### ORDER BY Rule:
```
ORDER BY Marks       → sorts ASCENDING (lowest first) — DEFAULT!
ORDER BY Marks ASC   → same as above (explicit)
ORDER BY Marks DESC  → sorts DESCENDING (highest first)
```

> **🔔 CRITICAL PYQ FACTS (Day 41):**
> - ORDER BY default = **ASC (Ascending)** ← most asked
> - **HAVING** = for groups (after GROUP BY)
> - **COMPUTE** = NOT a valid aggregate function
> - **DISTINCT** = removes duplicates
> - `WHERE col IS NULL` (NOT `WHERE col = NULL`)
> - WITH clause = **temporary relation** (CTE)

---

## 🎯 DBMS SUPER QUICK REFERENCE — ALL PYQ TRAPS IN ONE TABLE

```
┌────┬─────────────────────────────────────────────┬──────────────────────┐
│ #  │ QUESTION TYPE (What BPSC Asks)              │ CORRECT ANSWER       │
├────┼─────────────────────────────────────────────┼──────────────────────┤
│ 1  │ Is Google a DBMS?                           │ NO — Search Engine   │
│ 2  │ DBMS supports single-user only?             │ NO — Multi-user      │
│ 3  │ How many Primary Keys per table?            │ Only ONE             │
│ 4  │ UNIQUE key + NULL values?                   │ YES (PK cannot NULL) │
│ 5  │ FK references which key of another table?  │ Primary Key          │
│ 6  │ Redundant data causes what?                 │ Wasted space + inconsistency (BOTH) │
│ 7  │ 3NF is adequate for what?                  │ Normal RDBMS design  │
│ 8  │ 2NF removes what?                          │ Partial dependencies │
│ 9  │ 3NF removes what?                          │ Transitive dependencies │
│ 10 │ BCNF rule?                                 │ Every determinant = superkey │
│ 11 │ Which SQL command is auto-committed?        │ DDL (CREATE,DROP,TRUNCATE) │
│ 12 │ TRUNCATE category?                          │ DDL (not DML!)       │
│ 13 │ Can TRUNCATE be rolled back?               │ NO                   │
│ 14 │ Can DELETE be rolled back?                 │ YES (it's DML)       │
│ 15 │ COMMIT does what?                          │ Makes changes PERMANENT │
│ 16 │ ROLLBACK does what?                        │ UNDOES changes       │
│ 17 │ GRANT and REVOKE belong to?               │ DCL                  │
│ 18 │ UNION — is it a constraint?               │ NO — set operation   │
│ 19 │ COMPUTE — is it an aggregate function?    │ NO — NOT valid!      │
│ 20 │ ORDER BY default direction?               │ ASC (Ascending)      │
│ 21 │ WHERE vs HAVING — what's different?       │ WHERE=rows, HAVING=groups │
│ 22 │ WITH clause creates what?                 │ Temporary relation   │
│ 23 │ Relation = ? Tuple = ? Attribute = ?      │ Table, Row, Column   │
│ 24 │ Metadata = ?                              │ Data about data      │
│ 25 │ SQL developed by?                         │ IBM (declarative)    │
│ 26 │ Strong entity vs Weak entity — main diff? │ Weak has no PK of own │
│ 27 │ 1NF removes what?                         │ Multi-valued/non-atomic values │
│ 28 │ INNER JOIN returns?                       │ Only matching rows   │
│ 29 │ LEFT JOIN returns?                        │ All left + matching right │
│ 30 │ NULL check syntax?                        │ IS NULL / IS NOT NULL │
└────┴─────────────────────────────────────────────┴──────────────────────┘
```

---

# ═══════════════════════════════════════════════════════
# 🏛️ PART 2: GS — MODERN INDIAN HISTORY
# ═══════════════════════════════════════════════════════

## 🎯 Why Modern History is Critical for BPSC

Modern Indian History (1757–1947) consistently accounts for **8–12 questions** in BPSC GS section. Focus areas:
1. Socio-Religious Reform Movements (19th century)
2. The Revolt of 1857
3. Indian National Congress — Moderate vs Extremist phase
4. Gandhian Era movements
5. Important British Acts + Governor Generals

---

## 🕌 SOCIO-RELIGIOUS REFORM MOVEMENTS (19th–20th Century)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│              SOCIO-RELIGIOUS REFORM MOVEMENTS — COMPLETE TABLE              │
├────────────────────┬──────────────────────┬─────────────────────────────────┤
│ Movement/Society   │ Founder              │ Key Facts                       │
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ BRAHMO SAMAJ       │ Raja Ram Mohan Roy   │ Founded 1828, Calcutta          │
│                    │ (1772–1833)          │ Opposed: Sati, idol worship,    │
│                    │                      │ caste, child marriage           │
│                    │                      │ Sati abolished: 1829 (Lord      │
│                    │                      │ William Bentinck)               │
│                    │                      │ Roy = "Father of Modern India"  │
│                    │                      │ Roy = "Prophet of New Age"      │
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ PRARTHANA SAMAJ    │ Atmaram Pandurang    │ Founded 1867, Bombay            │
│                    │ (later MG Ranade)    │ Offshoot of Brahmo Samaj        │
│                    │                      │ Also opposed caste & child marriage│
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ ARYA SAMAJ         │ Dayananda Saraswati  │ Founded 1875, Bombay            │
│                    │ (1824–1883)          │ Slogan: "Back to the Vedas"     │
│                    │                      │ Opposed: Idol worship, caste,   │
│                    │                      │ child marriage, untouchability  │
│                    │                      │ Suddhi Movement: reconversion   │
│                    │                      │ DAV schools founded             │
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ RAMAKRISHNA        │ Swami Vivekananda    │ Founded 1897                    │
│ MISSION            │ (disciple of        │ Spread Vedanta philosophy       │
│                    │ Ramakrishna          │ Chicago Speech: 1893 World's    │
│                    │ Paramhansa)          │ Parliament of Religions         │
│                    │                      │ "Service to man = service to God"│
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ ALIGARH            │ Sir Syed Ahmad Khan  │ Founded 1875: MAO College       │
│ MOVEMENT           │ (1817–1898)          │ (Muhammedan Anglo-Oriental)     │
│                    │                      │ Later became Aligarh Muslim     │
│                    │                      │ University (AMU) — 1920         │
│                    │                      │ Modernise Muslim education      │
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ THEOSOPHICAL       │ Madame Blavatsky     │ Founded 1875 (USA), India: 1882 │
│ SOCIETY            │ + Henry Olcott       │ HQ: Adyar, Chennai              │
│                    │ Annie Besant         │ Annie Besant = first woman       │
│                    │ (later leader)       │ President of INC (1917)         │
│                    │                      │ Promoted universal brotherhood  │
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ SATYASHODHAK       │ Jyotiba Phule        │ Founded 1873, Pune              │
│ SAMAJ              │ (1827–1890)          │ Fought for lower caste rights   │
│                    │                      │ First school for girls in India │
│                    │                      │ Wife: Savitribai Phule          │
│                    │                      │ Gautama Buddha + Kabir influence│
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ SINGH SABHA        │ Dayal Singh Majithia │ Punjab, 1873                    │
│ MOVEMENT           │                      │ Reform Sikhism, promote         │
│                    │                      │ Gurumukhi literacy              │
├────────────────────┼──────────────────────┼─────────────────────────────────┤
│ SIKH REFORM:       │ Khem Singh Bedi      │ Akali movement (1920s)          │
│ AKALI MOVEMENT     │                      │ Reform of Gurudwara management  │
│                    │                      │ Led to Gurudwara Act 1925       │
└────────────────────┴──────────────────────┴─────────────────────────────────┘
```

> **🔔 BPSC PYQ Facts:**
> - Sati abolished = **1829** by Lord **William Bentinck** (influenced by Ram Mohan Roy)
> - Chicago Parliament of Religions = **1893** — Swami **Vivekananda's** famous speech
> - MAO College Aligarh = **1875** — Sir **Syed Ahmad Khan**
> - Annie Besant = first woman INC President = **1917**
> - Jyotiba Phule's wife = **Savitribai Phule** — pioneer of girls' education

---

## ⚔️ THE REVOLT OF 1857

```
REVOLT OF 1857 — OVERVIEW DIAGRAM

         CAUSES
    ┌────┴──────┐
    │           │
Political    Economic         Social/Religious     Military
• Doctrine   • Drain of      • Widow remarriage   • Enfield Rifle
  of Lapse    Wealth          forbidden            Cartridge
• Annexation • Land revenue  • Sati practices      (Immediate Cause)
  policies    burden         • Missionary           greased with
• Subsidiary • Destruction    activities           cow/pig fat
  Alliance    of handicrafts
```

### Leaders and Their Centres:
```
┌──────────────────────────┬────────────────┬─────────────────────────────────┐
│ Leader                   │ Centre         │ Key Fact                        │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Mangal Pandey            │ Barrackpore    │ First rebel soldier, hanged     │
│                          │ (Bengal)       │ Apr 1857. Triggered the revolt. │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Bahadur Shah Zafar II    │ Delhi          │ Last Mughal emperor, became     │
│                          │                │ symbolic leader                 │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Rani Lakshmibai          │ Jhansi         │ "Mardani thi woh" — fought      │
│                          │                │ British, died in battle 1858    │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Nana Sahib               │ Kanpur         │ Adopted son of Peshwa Baji      │
│ (Dhondu Pant)            │                │ Rao II, led Kanpur revolt       │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Tantia Tope              │ Gwalior/Central│ Commander of Nana Sahib,        │
│ (Ramachandra Panduranga) │ India          │ continued guerrilla warfare     │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Begum Hazrat Mahal       │ Lucknow        │ Led revolt in Lucknow,          │
│                          │                │ wife of Nawab Wajid Ali Shah    │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Khan Bahadur Khan        │ Bareilly       │ Led revolt in Rohilkhand        │
├──────────────────────────┼────────────────┼─────────────────────────────────┤
│ Kunwar Singh             │ Arrah, Bihar   │ 80-year-old Bihar zamindar      │
│                          │                │ ★ BPSC SPECIAL — Bihar leader  │
└──────────────────────────┴────────────────┴─────────────────────────────────┘
```

### Aftermath and Significance:
```
• 1858: British Crown took over directly from East India Company
• Queen Victoria's Proclamation (1858): Promised equality, non-interference
• Viewed as: "Sepoy Mutiny" by British | "First War of Independence" by V.D. Savarkar
• Immediate cause: Enfield rifle cartridges — greased with cow/pig fat
• British Regiments that DID NOT revolt: Madras, Bombay (remained loyal)
```

> **🔔 BPSC PYQ Facts:**
> - Immediate cause of 1857 = **Enfield Rifle greased cartridge**
> - Bihar leader in 1857 = **Kunwar Singh** (Arrah/Jagdishpur)
> - First War of Independence term = **V.D. Savarkar** (1909 book)
> - Last Mughal emperor = **Bahadur Shah Zafar II**

---

## 🏛️ INDIAN NATIONAL CONGRESS — PHASES

### Foundation:
```
Indian National Congress (INC) founded:
• Year: 1885
• Founder: A.O. Hume (British civil servant)
• First Session: December 1885, Bombay
• First President: W.C. Bonnerjee (Womesh Chandra Bonnerjee)
```

### Moderate Phase (1885–1905):
```
Leaders: Dadabhai Naoroji, Gopal Krishna Gokhale, Surendranath Banerjee
Method:  Prayers, petitions, constitutional means ("3P" — Prayers, Petitions, Protestations)
Demands: More Indians in civil services, Legislative councils, reduction of taxes

KEY CONTRIBUTIONS:
• Dadabhai Naoroji — "Drain of Wealth" theory, "Grand Old Man of India"
  Wrote: "Poverty and Un-British Rule in India"
• Gopal Krishna Gokhale — political guru of Gandhi, founded Servants of India Society (1905)
• Surendranath Banerjee — "Nation Maker," founded Indian Association 1876

Partition of Bengal (1905) by Lord Curzon → ended Moderate phase
```

### Extremist Phase (1905–1919):
```
Leaders: BAL Gangadhar TILAK + BIPIN Chandra PAL + LALA Lajpat Rai = "LAL-BAL-PAL"
Method:  Swaraj, Swadeshi, Boycott, National Education
Slogan:  Tilak: "Swaraj is my birthright and I shall have it!"

KEY EVENTS:
• Surat Split (1907): Moderates vs Extremists split within INC
• Tilak founded: Ganapati Festival (1893), Shivaji Festival as mass mobilisation tools
• Lucknow Pact (1916): Congress-Muslim League cooperation (Tilak-Jinnah)
• Home Rule League (1916): Tilak (Maharashtra) + Annie Besant (Madras)

Revolutionary Nationalism:
• Bhagat Singh — HSRA (Hindustan Socialist Republican Association)
  Central Assembly bombing (1929), Lahore Conspiracy Case, hanged 1931
• Chandrashekhar Azad — "never to be caught alive" — died Allahabad park (1931)
• Subhas Chandra Bose — INA (Indian National Army), "Give me blood, I'll give freedom"
  INA founded: 1942, Singapore
```

---

## 🕊️ GANDHIAN ERA — THE 4 MAJOR MOVEMENTS

```
TIMELINE OF GANDHI'S MAJOR MOVEMENTS:

1917 ──► CHAMPARAN SATYAGRAHA
         • Bihar (Champaran district)
         • Against: Tinkathia system (indigo cultivation)
         • Gandhi's FIRST Satyagraha in India
         • Importance: Gandhi entered Indian politics from Bihar!
         • ★ BPSC SPECIAL (Bihar connection)

1919 ──► ROWLATT SATYAGRAHA
         • Against: Rowlatt Act 1919 (detention without trial)
         • Jallianwala Bagh massacre: April 13, 1919 (Amritsar)
         • General Dyer ordered firing; Rabindranath Tagore returned knighthood

1920–22 ► NON-COOPERATION MOVEMENT
         • Started: September 1920
         • Methods: Boycott of councils, courts, schools, foreign goods
         • Withdrawal: Chauri Chaura incident (Feb 1922) — mob burned police station
         • Gandhi called off — "premature violence"
         • Khilafat Movement (1919–24) ran parallel — Hindu-Muslim unity

1930 ──► CIVIL DISOBEDIENCE MOVEMENT (Salt March/Dandi March)
         • March 12, 1930: Gandhi started Dandi March from Sabarmati Ashram
         • 241 miles / 24 days / reached Dandi on April 6, 1930
         • Made salt to break salt law — symbolic defiance
         • Gandhi-Irwin Pact (1931): suspended movement
         • Second Round Table Conference: Gandhi attended (1931)

1942 ──► QUIT INDIA MOVEMENT
         • August 8, 1942 — Bombay session of INC
         • Slogan: "Do or Die" (Gandhi)
         • Immediate arrest of all leaders
         • Underground leaders: Aruna Asaf Ali, Ram Manohar Lohia
         • Most violent and widespread mass movement
         • Parallel Government: Ballia (UP), Tamluk (Bengal)
```

### Round Table Conferences:
```
1st RTC (1930–31): INC boycotted — only minority groups attended
2nd RTC (1931):    GANDHI attended as INC representative (post Gandhi-Irwin Pact)
3rd RTC (1932):    INC boycotted again — no fruitful outcome
```

---

## 📜 IMPORTANT BRITISH ACTS — QUICK REFERENCE

```
┌─────────────────────┬──────────────────────────────────────────────────────┐
│ Act                 │ Key Provision                                       │
├─────────────────────┼──────────────────────────────────────────────────────┤
│ Regulating Act 1773 │ First act to regulate EIC; Governor of Bengal       │
│                     │ became Governor General; First GG: Warren Hastings  │
├─────────────────────┼──────────────────────────────────────────────────────┤
│ Pitt's India Act    │ Board of Control created; Dual govt of EIC          │
│ 1784               │                                                      │
├─────────────────────┼──────────────────────────────────────────────────────┤
│ Charter Act 1833    │ Abolished EIC trade monopoly; India = British colony│
├─────────────────────┼──────────────────────────────────────────────────────┤
│ Govt of India Act   │ Montagu-Chelmsford Reforms; Dyarchy in provinces;   │
│ 1919               │ Bicameral central legislature; Rowlatt Act same year │
├─────────────────────┼──────────────────────────────────────────────────────┤
│ Govt of India Act   │ Provincial autonomy; Federal scheme; Burma          │
│ 1935               │ separated; basis of 1950 Constitution                │
├─────────────────────┼──────────────────────────────────────────────────────┤
│ Indian Independence │ India independent August 15, 1947; partition into   │
│ Act 1947            │ India and Pakistan                                   │
└─────────────────────┴──────────────────────────────────────────────────────┘
```

---

## 👑 KEY GOVERNOR GENERALS & VICEROYS

```
GOVERNOR GENERALS OF INDIA:
━━━━━━━━━━━━━━━━━━━━━━━━━━━
Warren Hastings (1773–85)  — First GG; Regulating Act; Rohilla War
Lord Cornwallis (1786–93)  — Permanent Settlement 1793 (Bengal)
                             Cornwallis Code; Civil service reform
Lord Wellesley (1798–1805) — Subsidiary Alliance system
Lord Dalhousie (1848–56)   — Doctrine of Lapse; Railways; Telegraph
                             Widows Remarriage Act 1856

VICEROYS OF INDIA (after 1858):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Lord Canning (1856–62)     — First Viceroy; after 1857 revolt
Lord Lytton (1876–80)      — Vernacular Press Act 1878; Delhi Durbar 1877
Lord Ripon (1880–84)       — Ilbert Bill controversy; Factory Act 1881
Lord Curzon (1899–1905)    — Partition of Bengal 1905
Lord Minto (1905–10)       — Morley-Minto Reforms 1909
Lord Hardinge (1910–16)    — Capital shifted Delhi (1911)
Lord Chelmsford (1916–21)  — Montagu-Chelmsford Reforms 1919; Rowlatt Act
Lord Irwin (1926–31)       — Gandhi-Irwin Pact 1931
Lord Mountbatten (1947)    — Last Viceroy; Indian Independence
```

> **🔔 BPSC PYQ Facts:**
> - First Governor General = **Warren Hastings** (1773)
> - Permanent Settlement = **Lord Cornwallis** (1793)
> - Doctrine of Lapse = **Lord Dalhousie**
> - Capital shifted from Calcutta to Delhi = **1911** by **Lord Hardinge**
> - First Viceroy = **Lord Canning**
> - Last Viceroy = **Lord Mountbatten**
> - Partition of Bengal = **Lord Curzon** (1905)

---

## 📝 COMPLETE PYQ FACT TABLE — MODERN INDIAN HISTORY

| Topic | Key Fact |
|-------|---------|
| Brahmo Samaj founded | 1828 by Raja Ram Mohan Roy |
| Sati abolished | 1829, Lord William Bentinck |
| Arya Samaj founded | 1875 by Dayananda Saraswati |
| Arya Samaj slogan | "Back to the Vedas" |
| Chicago speech | Swami Vivekananda, 1893 |
| MAO College Aligarh | 1875, Sir Syed Ahmad Khan |
| Theosophical Society HQ India | Adyar, Chennai |
| First woman INC President | Annie Besant (1917) |
| INC founded | 1885 by A.O. Hume |
| First INC President | W.C. Bonnerjee |
| First INC session location | Bombay (now Mumbai) |
| Lal-Bal-Pal trio | Lala Lajpat Rai, Bal G. Tilak, Bipin Chandra Pal |
| Surat Split | 1907 (Moderates vs Extremists) |
| Drain of Wealth theory | Dadabhai Naoroji |
| Immediate cause 1857 revolt | Enfield rifle greased cartridge |
| Bihar leader in 1857 | Kunwar Singh (Arrah/Jagdishpur) |
| First War of Independence phrase | V.D. Savarkar (1909) |
| Gandhi's first Satyagraha in India | Champaran 1917 (Bihar) |
| Champaran issue | Tinkathia system (indigo) |
| Jallianwala Bagh massacre | April 13, 1919, General Dyer |
| Tagore returned knighthood after | Jallianwala Bagh massacre |
| NCM withdrawn due to | Chauri Chaura incident (Feb 1922) |
| Dandi March started | March 12, 1930 from Sabarmati |
| Dandi March ended (salt made) | April 6, 1930 at Dandi |
| Gandhi-Irwin Pact | 1931 |
| Quit India Movement | August 8, 1942 |
| Quit India slogan | "Do or Die" — Gandhi |
| Underground QIM leaders | Aruna Asaf Ali, Ram Manohar Lohia |
| INA founded | 1942, by Subhas Chandra Bose (Singapore) |
| INA slogan | "Give me blood, I'll give freedom" |
| Bhagat Singh hanged | March 23, 1931 (Lahore) |
| Govt of India Act 1935 | Provincial autonomy, basis of Constitution |
| Capital shifted to Delhi | 1911, Lord Hardinge |
| Permanent Settlement | 1793, Lord Cornwallis |
| Doctrine of Lapse | Lord Dalhousie |
| Satyashodhak Samaj | Jyotiba Phule (1873) |
| First school for girls India | Jyotiba Phule + Savitribai Phule |

---

# ═══════════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 42
# ═══════════════════════════════════════════════════════

> ⚠️ **RULE:** Attempt ALL 50 questions FIRST. Answer Key strictly after Q50!
> Option D = "More than one of the above" | Option E = "None of the above"

---

# 💻 SECTION A: CS QUESTIONS — DBMS FULL REVISION (Q1–Q25)

---

**Q1.** A DBMS (Database Management System) acts as an interface between:

(A) The user and the hardware
(B) The database application and the database
(C) The operating system and the network
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is TRUE about a DBMS?

(A) It supports single-user access only
(B) It increases data redundancy
(C) It supports multi-user concurrent access
(D) It is a type of search engine
(E) None of the above

---

**Q3.** In the relational model, a ROW is called a:

(A) Attribute
(B) Domain
(C) Relation
(D) Tuple
(E) Schema

---

**Q4.** Which of the following KEYS allows NULL values?

(A) Primary Key
(B) Candidate Key
(C) Unique Key
(D) More than one of the above
(E) None of the above

---

**Q5.** How many PRIMARY KEYS can a table have?

(A) Unlimited
(B) Two
(C) Only one
(D) Depends on the number of columns
(E) None of the above

---

**Q6.** Foreign Key in a relational database enforces:

(A) Entity Integrity
(B) Domain Integrity
(C) Referential Integrity
(D) More than one of the above
(E) None of the above

---

**Q7.** In an ER diagram, a RELATIONSHIP is represented by:

(A) Rectangle
(B) Ellipse
(C) Diamond
(D) Triangle
(E) None of the above

---

**Q8.** A WEAK ENTITY in ER diagram:

(A) Has its own Primary Key
(B) Does NOT have a Primary Key of its own and depends on another entity
(C) Cannot have any attributes
(D) Always has 1:1 cardinality with the owner entity
(E) None of the above

---

**Q9.** The term "METADATA" in databases refers to:

(A) Main data stored in tables
(B) Data about data — structure/schema information
(C) Transaction log data
(D) Backup data
(E) None of the above

---

**Q10.** Which Normal Form is considered ADEQUATE for normal RDBMS database design?

(A) 1NF
(B) 2NF
(C) 3NF
(D) BCNF

---

**Q11.** Storing the same data in two different places in a database causes:

(A) Only wasted storage space
(B) Only data inconsistency
(C) Both wasted storage space AND data inconsistency
(D) Better performance
(E) None of the above

---

**Q12.** Which Normal Form specifically eliminates PARTIAL DEPENDENCIES?

(A) 1NF
(B) 2NF
(C) 3NF
(D) BCNF

---

**Q13.** A relation has primary key (A, B) composite. If attribute C depends only on A, this violates:

(A) 1NF — non-atomic values
(B) 2NF — partial dependency
(C) 3NF — transitive dependency
(D) BCNF — non-superkey determinant
(E) None of the above

---

**Q14.** The SQL command TRUNCATE is classified as:

(A) DML (Data Manipulation Language)
(B) TCL (Transaction Control Language)
(C) DDL (Data Definition Language)
(D) DCL (Data Control Language)
(E) None of the above

---

**Q15.** Which of the following SQL commands CAN be rolled back using ROLLBACK?

(A) DROP TABLE
(B) TRUNCATE TABLE
(C) CREATE TABLE
(D) DELETE FROM TABLE WHERE condition
(E) None of the above

---

**Q16.** The SQL command COMMIT:

(A) Undoes all uncommitted changes
(B) Creates a checkpoint in a transaction
(C) Makes all pending changes permanent
(D) Removes all permissions from users
(E) None of the above

---

**Q17.** Which of the following is NOT a valid SQL constraint?

(A) PRIMARY KEY
(B) NOT NULL
(C) UNION
(D) FOREIGN KEY
(E) CHECK

---

**Q18.** The default sort order of `ORDER BY` in SQL is:

(A) Descending
(B) Ascending
(C) Random
(D) Alphabetical only
(E) None of the above

---

**Q19.** Which SQL clause is used to filter GROUPS after a GROUP BY operation?

(A) WHERE
(B) FILTER
(C) HAVING
(D) ORDER BY
(E) SORT BY

---

**Q20.** Which of the following is NOT a valid aggregate function in SQL?

(A) COUNT
(B) MAX
(C) COMPUTE
(D) AVG
(E) SUM

---

**Q21.** The `WITH` clause in SQL is used to:

(A) Create a permanent table in the database
(B) Create a temporary named result set (CTE) used within the query
(C) Grant permissions to users
(D) Begin a transaction
(E) None of the above

---

**Q22.** `SELECT COUNT(*) FROM Employee` vs `SELECT COUNT(Email) FROM Employee` — these will give the SAME result only when:

(A) The table has exactly 100 rows
(B) The Email column has no NULL values
(C) All employees have unique emails
(D) The table has only one column
(E) None of the above

---

**Q23.** An INNER JOIN between two tables returns:

(A) All rows from the left table
(B) All rows from the right table
(C) Only rows that have matching values in BOTH tables
(D) All rows from both tables
(E) None of the above

---

**Q24.** Consider the following SQL query:
```sql
SELECT Dept, AVG(Salary)
FROM Employee
WHERE Salary > 30000
GROUP BY Dept
HAVING AVG(Salary) > 50000
ORDER BY AVG(Salary) DESC;
```
In what order are the SQL clauses executed?

(A) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
(B) WHERE → GROUP BY → HAVING → FROM → SELECT → ORDER BY
(C) FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY
(D) FROM → SELECT → WHERE → GROUP BY → HAVING → ORDER BY
(E) None of the above

---

**Q25.** Which of the following pairs of SQL commands belong to DCL (Data Control Language)?

(A) COMMIT and ROLLBACK
(B) CREATE and DROP
(C) GRANT and REVOKE
(D) SELECT and UPDATE
(E) None of the above

---

# 🏛️ SECTION B: GS QUESTIONS — MODERN INDIAN HISTORY (Q26–Q50)

---

**Q26.** The Brahmo Samaj was founded in 1828 by:

(A) Dayananda Saraswati
(B) Swami Vivekananda
(C) Raja Ram Mohan Roy
(D) Jyotiba Phule
(E) None of the above

---

**Q27.** The practice of Sati was legally abolished in India in which year, and by which Governor General?

(A) 1835, Lord William Bentinck
(B) 1829, Lord William Bentinck
(C) 1829, Lord Wellesley
(D) 1856, Lord Dalhousie
(E) None of the above

---

**Q28.** Which reform movement had the slogan "Back to the Vedas"?

(A) Brahmo Samaj
(B) Ramakrishna Mission
(C) Arya Samaj
(D) Prarthana Samaj
(E) None of the above

---

**Q29.** Swami Vivekananda delivered his famous speech at the World Parliament of Religions in:

(A) London, 1890
(B) Paris, 1895
(C) Chicago, 1893
(D) New York, 1900
(E) None of the above

---

**Q30.** The Muhammedan Anglo-Oriental (MAO) College at Aligarh was founded by:

(A) Maulana Azad
(B) Sir Syed Ahmad Khan
(C) Muhammad Iqbal
(D) Muhammad Ali Jinnah
(E) None of the above

---

**Q31.** The IMMEDIATE CAUSE of the Revolt of 1857 was:

(A) Doctrine of Lapse policy of Lord Dalhousie
(B) Drain of Wealth and economic exploitation
(C) Introduction of greased cartridges in the Enfield rifle
(D) Partition of Bengal by Lord Curzon
(E) None of the above

---

**Q32.** Which leader from Bihar played a prominent role in the Revolt of 1857?

(A) Mangal Pandey
(B) Begum Hazrat Mahal
(C) Kunwar Singh
(D) Rani Lakshmibai
(E) None of the above

---

**Q33.** The term "First War of Independence" for the 1857 revolt was coined by:

(A) Bal Gangadhar Tilak
(B) Subhas Chandra Bose
(C) V.D. Savarkar
(D) Dadabhai Naoroji
(E) None of the above

---

**Q34.** The Indian National Congress was founded in 1885. Who was its founder?

(A) Dadabhai Naoroji
(B) Surendranath Banerjee
(C) A.O. Hume
(D) W.C. Bonnerjee
(E) None of the above

---

**Q35.** The political trio known as "Lal-Bal-Pal" refers to:

(A) Lala Lajpat Rai, Bal Gangadhar Tilak, Bipin Chandra Pal
(B) Lala Hardayal, Bal Gangadhar Tilak, Prafulla Chaki
(C) Lala Lajpat Rai, Bhagat Singh, Chandrashekhar Azad
(D) More than one of the above
(E) None of the above

---

**Q36.** Gandhi's FIRST Satyagraha in India was the Champaran Satyagraha (1917). It was against:

(A) Salt tax imposed by the British
(B) The Rowlatt Act 1919
(C) The Tinkathia system forcing indigo cultivation
(D) Partition of Bengal
(E) None of the above

---

**Q37.** The Champaran Satyagraha (1917) has special significance for BPSC because:

(A) It was Gandhi's last movement
(B) It was Bihar's contribution to the freedom struggle — Gandhi's first Satyagraha in India
(C) It led to the formation of the INC
(D) It took place in Muzaffarpur, Bihar
(E) None of the above

---

**Q38.** The Non-Cooperation Movement (1920–22) was called off by Gandhi due to:

(A) Gandhi's arrest
(B) Round Table Conference invitation
(C) Chauri Chaura incident where a mob burned a police station
(D) Jallianwala Bagh massacre
(E) None of the above

---

**Q39.** The Jallianwala Bagh massacre occurred on April 13, 1919. In response, who returned their knighthood/Nobel Prize?

(A) Mahatma Gandhi returned his Kaiser-i-Hind medal
(B) Rabindranath Tagore returned his knighthood
(C) Motilal Nehru resigned from the legislative council
(D) More than one of the above
(E) None of the above

---

**Q40.** The Dandi March (Salt March) began on which date from which place?

(A) April 6, 1930 from Dandi beach
(B) March 12, 1930 from Sabarmati Ashram
(C) January 26, 1930 from Lahore
(D) August 8, 1942 from Bombay
(E) None of the above

---

**Q41.** The Quit India Movement was launched on August 8, 1942. The slogan given by Gandhi was:

(A) "Swaraj is my birthright"
(B) "Do or Die"
(C) "Give me blood, I'll give freedom"
(D) "Jai Hind"
(E) None of the above

---

**Q42.** Who was the FIRST woman President of the Indian National Congress?

(A) Sarojini Naidu
(B) Indira Gandhi
(C) Annie Besant
(D) Vijaya Lakshmi Pandit
(E) None of the above

---

**Q43.** The permanent settlement of land revenue was introduced in Bengal by:

(A) Lord Wellesley
(B) Lord Dalhousie
(C) Warren Hastings
(D) Lord Cornwallis
(E) None of the above

---

**Q44.** The Indian capital was shifted from Calcutta to Delhi in the year:

(A) 1905
(B) 1911
(C) 1919
(D) 1935
(E) None of the above

---

**Q45.** Bhagat Singh, Rajguru, and Sukhdev were hanged on:

(A) January 30, 1930
(B) March 23, 1931
(C) August 15, 1929
(D) April 12, 1930
(E) None of the above

---

**Q46.** The Satyashodhak Samaj was founded by Jyotiba Phule in 1873. Its primary objective was:

(A) Reform of Hindu religion and return to Vedas
(B) Liberation of lower castes from the domination of upper castes
(C) Promoting Muslim education in Maharashtra
(D) Encouraging widow remarriage
(E) None of the above

---

**Q47.** The "Doctrine of Lapse" — a controversial policy of annexation — was introduced by which Governor General?

(A) Lord Cornwallis
(B) Lord Wellesley
(C) Lord Dalhousie
(D) Lord Curzon
(E) None of the above

---

**Q48.** The Government of India Act 1935 is important because:

(A) It introduced Dyarchy at the Centre
(B) It provided for Provincial Autonomy and became the basis for the Indian Constitution
(C) It ended the East India Company's rule
(D) It introduced the Morley-Minto Reforms
(E) None of the above

---

**Q49.** Consider the following pairs of Movements and their leaders:
1. Brahmo Samaj — Raja Ram Mohan Roy
2. Arya Samaj — Swami Vivekananda
3. Aligarh Movement — Sir Syed Ahmad Khan
4. Ramakrishna Mission — Swami Vivekananda

How many pairs are CORRECTLY matched?

(A) Only 1 and 3
(B) Only 1, 3, and 4
(C) All four pairs
(D) Only 2 and 4
(E) Only 1 and 4

---

**Q50.** The Indian National Army (INA) was reorganized by Subhas Chandra Bose in:

(A) 1939, in Germany
(B) 1942, in Singapore
(C) 1940, in Burma
(D) 1945, in Japan
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🔑 ANSWER KEY — ALL 50 QUESTIONS
# ═══════════════════════════════════════════════════════

> ✅ Only check AFTER solving all 50 questions!

---

## 💻 CS ANSWERS — DBMS Full Revision (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| 1 | **(B)** | DBMS acts as interface between **database application** and the **database**. It manages all access. |
| 2 | **(C)** | DBMS supports **multi-user concurrent access** — NOT single-user only. Supporting only single-user access is a limitation, not a feature. |
| 3 | **(D)** | In relational model: Row = **Tuple**, Column = Attribute, Table = Relation, Domain = set of valid values. |
| 4 | **(C)** | **UNIQUE key allows NULL values.** Primary Key does NOT allow NULL. Candidate Key also does not allow NULL. |
| 5 | **(C)** | A table can have **ONLY ONE Primary Key** — this is a direct, high-frequency PYQ fact. |
| 6 | **(C)** | Foreign Key enforces **Referential Integrity** — FK value must exist in referenced table's PK. |
| 7 | **(C)** | In ER diagram: Relationship = **Diamond** shape. Entity = Rectangle. Attribute = Ellipse. |
| 8 | **(B)** | Weak entity has **NO Primary Key** of its own — it depends on its owner (strong entity) for identification. |
| 9 | **(B)** | **Metadata** = data about data = schema information (table structure, column names, data types). |
| 10 | **(C)** | **3NF is adequate for normal RDBMS design** — this is a direct PYQ fact asked multiple times. |
| 11 | **(C)** | Redundant data causes **BOTH** wasted storage space AND data inconsistency. BPSC answer = D (More than one). |
| 12 | **(B)** | **2NF** eliminates partial dependencies (non-key attribute depending on part of composite PK). |
| 13 | **(B)** | C depends only on A (part of composite PK A,B) = **Partial Dependency** = violates **2NF**. |
| 14 | **(C)** | **TRUNCATE is DDL** — this is the classic trap! Many students say DML but it is DDL. |
| 15 | **(D)** | **DELETE is DML** and CAN be rolled back. DROP, TRUNCATE, CREATE are DDL — auto-committed, no rollback. |
| 16 | **(C)** | **COMMIT makes all pending changes permanent** — it saves them to disk. Direct PYQ fact. |
| 17 | **(C)** | **UNION is NOT a constraint** — it is a SET OPERATION. Valid constraints: PRIMARY KEY, NOT NULL, UNIQUE, FOREIGN KEY, CHECK, DEFAULT. |
| 18 | **(B)** | ORDER BY default = **ASC (Ascending)**. You must write DESC explicitly for descending. |
| 19 | **(C)** | **HAVING** filters groups after GROUP BY. WHERE filters individual rows before grouping. |
| 20 | **(C)** | **COMPUTE is NOT a valid SQL aggregate function.** Valid: COUNT, SUM, AVG, MAX, MIN only. |
| 21 | **(B)** | WITH clause creates a **temporary named result set (CTE)** — used within a single query, not permanent. |
| 22 | **(B)** | COUNT(*) vs COUNT(Email) give same result only when **Email has no NULL values**. COUNT(col) ignores NULLs. |
| 23 | **(C)** | **INNER JOIN** returns only rows where there is a **match in BOTH tables**. Non-matching rows from either table are excluded. |
| 24 | **(C)** | SQL execution order: **FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY**. Writing order is different. |
| 25 | **(C)** | **GRANT and REVOKE** are DCL (Data Control Language) commands that manage user permissions. |

---

## 🏛️ GS ANSWERS — Modern Indian History (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| 26 | **(C)** | **Brahmo Samaj** was founded in **1828** by **Raja Ram Mohan Roy** in Calcutta. |
| 27 | **(B)** | Sati was abolished in **1829** by **Lord William Bentinck** — Raja Ram Mohan Roy's campaign influenced this. |
| 28 | **(C)** | **"Back to the Vedas"** was the slogan of **Arya Samaj** founded by Dayananda Saraswati in 1875. |
| 29 | **(C)** | Vivekananda's famous address was at the **World Parliament of Religions, Chicago, 1893**. He began with "Sisters and Brothers of America." |
| 30 | **(B)** | **Sir Syed Ahmad Khan** founded MAO College at Aligarh in **1875** — which later became AMU in 1920. |
| 31 | **(C)** | **Immediate cause** = greased cartridges of the Enfield rifle — soldiers had to bite them; greased with cow/pig fat offended both Hindus and Muslims. |
| 32 | **(C)** | **Kunwar Singh** of Arrah (Jagdishpur), Bihar — led the revolt at age ~80. Direct BPSC-special fact. |
| 33 | **(C)** | **V.D. Savarkar** coined "First War of Independence" in his 1909 book "The Indian War of Independence." |
| 34 | **(C)** | INC founded by **A.O. Hume** (British civil servant) in 1885. W.C. Bonnerjee was the first PRESIDENT. |
| 35 | **(A)** | **Lal-Bal-Pal** = **Lala Lajpat Rai** (Punjab) + **Bal Gangadhar Tilak** (Maharashtra) + **Bipin Chandra Pal** (Bengal). |
| 36 | **(C)** | Champaran Satyagraha was against the **Tinkathia system** — indigo planters forced farmers to grow indigo on 3/20 of their land. |
| 37 | **(B)** | Champaran 1917 is **Bihar's entry into national freedom struggle** and Gandhi's first Satyagraha on Indian soil. Critical BPSC fact. |
| 38 | **(C)** | NCM was called off due to the **Chauri Chaura incident (Feb 5, 1922)** in UP — mob set fire to a police station killing 22 policemen. |
| 39 | **(D)** | **Both A and B** — Gandhi returned his Kaiser-i-Hind medal AND Tagore returned his knighthood in response to Jallianwala Bagh. Answer = D (More than one). |
| 40 | **(B)** | Dandi March started **March 12, 1930 from Sabarmati Ashram**, Ahmedabad. Reached Dandi on April 6 (241 miles, 24 days). |
| 41 | **(B)** | Gandhi's slogan for Quit India Movement = **"Do or Die"** (Karo ya Maro). August 8, 1942, Bombay. |
| 42 | **(C)** | **Annie Besant** was the first woman President of INC in **1917**. Sarojini Naidu was first Indian woman President (1925). |
| 43 | **(D)** | **Lord Cornwallis** introduced the **Permanent Settlement** in Bengal in **1793**. |
| 44 | **(B)** | Capital shifted from Calcutta to Delhi in **1911** during the reign of **Lord Hardinge**. |
| 45 | **(B)** | Bhagat Singh, Rajguru, and Sukhdev were hanged on **March 23, 1931** — now observed as Shaheed Diwas. |
| 46 | **(B)** | Satyashodhak Samaj's primary goal was **liberation of lower castes (Shudras and Ati-Shudras)** from Brahminic domination. |
| 47 | **(C)** | **Doctrine of Lapse** = Lord **Dalhousie's** policy to annex states with no natural heir (Jhansi, Satara, Nagpur etc.). |
| 48 | **(B)** | Govt of India Act 1935 introduced **Provincial Autonomy** and served as the **basis for the Indian Constitution** 1950. |
| 49 | **(B)** | Pair 2 is WRONG: Arya Samaj was founded by **Dayananda Saraswati**, NOT Vivekananda. Correct pairs: 1 ✓, 3 ✓, 4 ✓. Answer = **B** (1, 3, and 4). |
| 50 | **(B)** | Subhas Chandra Bose reorganized the INA in **1942** in **Singapore** after Mohan Singh's earlier version. |

---

# ═══════════════════════════════════════════════════════
# 🎯 TOPPER'S CORNER — DAY 42 MASTER CHECKLIST
# ═══════════════════════════════════════════════════════

## ✅ DBMS FINAL REVISION — 30 Things to Know Cold

**Database Basics:**
- [ ] Google = NOT a DBMS. DBMS supports multi-user (not single-user only)
- [ ] Relation=Table | Tuple=Row | Attribute=Column | Metadata=Data about data

**Keys:**
- [ ] Only 1 PRIMARY KEY per table | UNIQUE allows NULL, PK does NOT
- [ ] FK → enforces Referential Integrity → references PK of another table

**Normalization:**
- [ ] 1NF=atomic | 2NF=no partial deps | 3NF=no transitive deps | BCNF=determinant=superkey
- [ ] 3NF = adequate for RDBMS | 2NF only matters with composite PK

**SQL Commands:**
- [ ] DDL=auto-committed (no rollback) | DML=needs COMMIT | TRUNCATE=DDL not DML!
- [ ] COMMIT=permanent | ROLLBACK=undo | SAVEPOINT=checkpoint
- [ ] GRANT/REVOKE=DCL | UNION=NOT a constraint | COMPUTE=NOT an aggregate

**SQL SELECT:**
- [ ] ORDER BY default=ASC | HAVING=for groups | WHERE=for rows
- [ ] Valid aggregates ONLY: COUNT, SUM, AVG, MAX, MIN
- [ ] WITH clause = temporary relation | IS NULL (not = NULL)
- [ ] Execution: FROM→WHERE→GROUP BY→HAVING→SELECT→ORDER BY

## ✅ MODERN HISTORY — 20 Must-Know Before Exam

- [ ] Brahmo Samaj = 1828, Ram Mohan Roy | Sati abolished = 1829, Bentinck
- [ ] Arya Samaj = 1875, Dayananda Saraswati | "Back to Vedas"
- [ ] Chicago Parliament of Religions = 1893, Vivekananda
- [ ] MAO College = 1875, Sir Syed Ahmad Khan
- [ ] First woman INC President = Annie Besant (1917)
- [ ] INC = 1885, A.O. Hume | First President = W.C. Bonnerjee
- [ ] Immediate cause 1857 = Enfield rifle greased cartridge
- [ ] Bihar leader 1857 = Kunwar Singh (Arrah/Jagdishpur) ★ BPSC
- [ ] "First War of Independence" = V.D. Savarkar
- [ ] Lal-Bal-Pal = Lajpat Rai + Tilak + Bipin Pal
- [ ] Champaran 1917 = Gandhi's first Satyagraha, Bihar ★ BPSC
- [ ] NCM withdrawn = Chauri Chaura incident (1922)
- [ ] Dandi March = March 12, 1930 from Sabarmati
- [ ] Quit India = August 8, 1942 | "Do or Die"
- [ ] Capital shifted to Delhi = 1911, Lord Hardinge
- [ ] Permanent Settlement = 1793, Lord Cornwallis
- [ ] Doctrine of Lapse = Lord Dalhousie
- [ ] Bhagat Singh hanged = March 23, 1931
- [ ] INA reorganized = 1942, Singapore, Subhas Chandra Bose
- [ ] Govt of India Act 1935 = basis of Indian Constitution

---

## 📊 Score Yourself

| Score | Performance | Action |
|-------|-------------|--------|
| 45–50 | 🏆 Excellent — Topper Level | Ready for Week 7 Networks! |
| 38–44 | ✅ On Track | Recheck 5–7 wrong answers |
| 30–37 | ⚠️ Needs Work | Re-read DBMS blocks + History timeline |
| < 30  | ❌ Revise | Re-study Days 36–41 before moving forward |

---

## 📅 Day 43 Preview — Computer Networks Begin!

**CS:** OSI Model — 7 Layers (Application → Physical)
**GS:** Indian Polity — Parliament Structure (Lok Sabha + Rajya Sabha)

Key Day 43 fact: OSI Layers memory trick: **"All People Seem To Need Data Processing"**
(Application, Presentation, Session, Transport, Network, Data Link, Physical)

---

*Day 42 Complete ✅ | DBMS + Modern History MASTERED! | Phase 1 DBMS Block Done! 🎯*
*Target: 130+/150 | TOP 50 Rank | You're on Track! 💪*
