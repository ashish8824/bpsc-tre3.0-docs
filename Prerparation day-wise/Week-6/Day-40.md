# 📅 BPSC TRE 4.0 — DAY 40
## CS Topic: SQL Commands — DDL, DML, DCL, TCL (Complete Guide)
## GS Topic: Biology — Plant Physiology, Photoperiodism, Plant Hormones

> **Target:** 130+/150 | Top 50 Rank
> **Strategy:** Master SQL command categories + Biology plant topics — both are HIGH-YIELD in BPSC TRE

---

# ═══════════════════════════════════════════════════════
# 📘 PART 1: COMPUTER SCIENCE — SQL COMMANDS
# ═══════════════════════════════════════════════════════

## 🎯 What is SQL?

**SQL = Structured Query Language**

- Developed by IBM in the 1970s (originally called **SEQUEL**)
- Standardized by **ANSI** and **ISO**
- Used to communicate with **Relational Database Management Systems (RDBMS)**
- SQL is **NOT** a procedural language — it is a **declarative** language (you say WHAT you want, not HOW to get it)
- SQL is **case-insensitive** for keywords (SELECT = select = Select)

---

## 🗂️ The Four SQL Command Categories

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        SQL COMMAND CATEGORIES                           │
├──────────┬──────────────────────────────────┬──────────────────────────┤
│ Category │ Full Form                        │ Commands                 │
├──────────┼──────────────────────────────────┼──────────────────────────┤
│ DDL      │ Data Definition Language         │ CREATE, ALTER, DROP,     │
│          │                                  │ TRUNCATE, RENAME         │
├──────────┼──────────────────────────────────┼──────────────────────────┤
│ DML      │ Data Manipulation Language       │ SELECT, INSERT, UPDATE,  │
│          │                                  │ DELETE                   │
├──────────┼──────────────────────────────────┼──────────────────────────┤
│ DCL      │ Data Control Language            │ GRANT, REVOKE            │
├──────────┼──────────────────────────────────┼──────────────────────────┤
│ TCL      │ Transaction Control Language     │ COMMIT, ROLLBACK,        │
│          │                                  │ SAVEPOINT, SET TRANSACTION│
└──────────┴──────────────────────────────────┴──────────────────────────┘
```

**Memory Trick:**
```
DDL  = "Define the Design"  → Creating/changing STRUCTURE of database
DML  = "Deal with the Data" → Inserting/reading/changing actual DATA
DCL  = "Decide who Controls"→ Who gets PERMISSION to do what
TCL  = "Transaction Control"→ SAVE or UNDO your work
```

---

## 🔵 DDL — Data Definition Language

DDL commands work on the **structure (schema)** of the database — tables, columns, indexes.

> **Key property:** DDL commands are **auto-committed** — changes are permanent immediately, NO rollback possible.

### CREATE — Make a new table or database

```sql
-- Create a Database
CREATE DATABASE College;

-- Create a Table
CREATE TABLE Student (
    Roll_No     INT PRIMARY KEY,
    Name        VARCHAR(50) NOT NULL,
    Age         INT,
    City        VARCHAR(30),
    Marks       DECIMAL(5,2)
);
```

**Diagram of what CREATE does:**
```
Before CREATE:         After CREATE:
                       ┌─────────────────────────────────┐
  (nothing)     ──►    │ Student Table                   │
                       ├─────────┬──────┬─────┬──────────┤
                       │Roll_No  │ Name │ Age │ City ... │
                       ├─────────┼──────┼─────┼──────────┤
                       │ (empty) │      │     │          │
                       └─────────┴──────┴─────┴──────────┘
```

---

### ALTER — Modify an existing table structure

```sql
-- Add a new column
ALTER TABLE Student ADD Email VARCHAR(100);

-- Remove (drop) a column
ALTER TABLE Student DROP COLUMN Email;

-- Change the data type of a column
ALTER TABLE Student MODIFY Age SMALLINT;

-- Rename a column
ALTER TABLE Student RENAME COLUMN City TO Location;
```

---

### DROP — Delete the entire table (structure + data, permanently)

```sql
DROP TABLE Student;
-- This deletes the table COMPLETELY — structure AND all data gone
-- CANNOT be rolled back
```

---

### TRUNCATE — Delete ALL rows but keep the table structure

```sql
TRUNCATE TABLE Student;
-- All rows are deleted, but the table still exists (empty)
-- CANNOT be rolled back (auto-committed like DROP)
-- Faster than DELETE because it does not log individual row deletions
```

---

### TRUNCATE vs DROP vs DELETE — The Critical Comparison

```
┌─────────────┬────────────────┬──────────────┬─────────────────────────┐
│ Feature     │ DROP           │ TRUNCATE     │ DELETE (DML)            │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ Removes     │ Entire table   │ All rows     │ Specific/all rows       │
│             │ (structure too)│ (keeps table)│ (based on WHERE clause) │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ Structure   │ DELETED        │ KEPT         │ KEPT                    │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ Rollback?   │ NO             │ NO           │ YES (can rollback)      │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ WHERE clause│ Not applicable │ Not allowed  │ YES — can filter rows   │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ Auto-commit │ YES            │ YES          │ NO (needs COMMIT)       │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ Category    │ DDL            │ DDL          │ DML                     │
├─────────────┼────────────────┼──────────────┼─────────────────────────┤
│ Speed       │ Fastest        │ Fast         │ Slower (logs each row)  │
└─────────────┴────────────────┴──────────────┴─────────────────────────┘
```

> **🔔 PYQ Trap:** "Which command deletes all rows but CANNOT be rolled back?" → TRUNCATE (DDL, not DML). DELETE can be rolled back; TRUNCATE cannot.

---

## 🟡 DML — Data Manipulation Language

DML commands work on the **data (rows)** inside tables.

> **Key property:** DML commands are **NOT auto-committed** — changes can be undone with ROLLBACK until you COMMIT.

### SELECT — Retrieve/Read data

```sql
-- Basic syntax
SELECT column1, column2 FROM table_name WHERE condition;

-- Select all columns
SELECT * FROM Student;

-- Select with condition
SELECT Name, Marks FROM Student WHERE Marks > 80;

-- Select distinct values (no duplicates)
SELECT DISTINCT City FROM Student;

-- Select with ordering
SELECT Name, Marks FROM Student ORDER BY Marks DESC;

-- Select with limit
SELECT Name FROM Student WHERE City = 'Patna' LIMIT 5;
```

**SELECT execution order (important for BPSC):**
```
Execution Order:   FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
Writing Order:     SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT
```

---

### INSERT — Add new rows

```sql
-- Insert with all columns (values must match column order)
INSERT INTO Student VALUES (101, 'Prag', 25, 'Patna', 92.5);

-- Insert with specific columns (safer practice)
INSERT INTO Student (Roll_No, Name, Marks) VALUES (102, 'Riya', 88.0);
```

---

### UPDATE — Modify existing rows

```sql
-- Update with WHERE (recommended)
UPDATE Student SET Marks = 95.0 WHERE Roll_No = 101;

-- Update multiple columns
UPDATE Student SET City = 'Delhi', Age = 26 WHERE Roll_No = 101;

-- DANGER: Update without WHERE (affects ALL rows!)
UPDATE Student SET Marks = 0;   -- All students get 0!
```

---

### DELETE — Remove specific rows

```sql
-- Delete specific row(s)
DELETE FROM Student WHERE Roll_No = 101;

-- Delete multiple rows with condition
DELETE FROM Student WHERE Marks < 35;

-- Delete ALL rows (like TRUNCATE but CAN be rolled back)
DELETE FROM Student;
```

---

## 🟢 DCL — Data Control Language

DCL manages **permissions and access rights** for database objects.

### GRANT — Give permissions to a user

```sql
-- Give SELECT and INSERT permission on Student table to user 'Rohan'
GRANT SELECT, INSERT ON Student TO Rohan;

-- Give ALL privileges
GRANT ALL PRIVILEGES ON Student TO Rohan;

-- Give permission to ALL users
GRANT SELECT ON Student TO PUBLIC;

-- WITH GRANT OPTION — Rohan can also give this permission to others
GRANT SELECT ON Student TO Rohan WITH GRANT OPTION;
```

### REVOKE — Take back permissions

```sql
-- Remove specific permission
REVOKE INSERT ON Student FROM Rohan;

-- Remove all privileges
REVOKE ALL PRIVILEGES ON Student FROM Rohan;
```

**GRANT/REVOKE diagram:**
```
DBA (Database Admin)
        │
        ├── GRANT SELECT ON Student TO Rohan;
        │         ↓
        │      Rohan can now SELECT from Student
        │
        └── REVOKE SELECT ON Student FROM Rohan;
                  ↓
               Rohan CANNOT select anymore
```

---

## 🔴 TCL — Transaction Control Language

TCL manages **transactions** — a transaction is a unit of work that should be completed fully or not at all (ACID properties).

### What is a Transaction?

```
A transaction is a sequence of SQL operations treated as ONE unit.

Example: Bank Transfer ₹1000 from Account A to Account B:
  Step 1: UPDATE Account SET Balance = Balance - 1000 WHERE AccNo = 'A';
  Step 2: UPDATE Account SET Balance = Balance + 1000 WHERE AccNo = 'B';

Both steps MUST succeed. If Step 2 fails, Step 1 must be reversed → ROLLBACK
```

### COMMIT — Make changes permanent

```sql
-- Start some DML work
INSERT INTO Student VALUES (103, 'Anjali', 22, 'Gaya', 78.5);
UPDATE Student SET Marks = 90 WHERE Roll_No = 101;

-- COMMIT makes ALL pending changes permanent
COMMIT;
-- After COMMIT: changes are saved to disk permanently, cannot be undone
```

### ROLLBACK — Undo all uncommitted changes

```sql
-- Start some DML work
DELETE FROM Student WHERE Roll_No = 103;
UPDATE Student SET Marks = 0 WHERE City = 'Patna';

-- Oops! That was a mistake — ROLLBACK to undo
ROLLBACK;
-- All changes since last COMMIT are reversed
```

### SAVEPOINT — Mark a point to roll back to

```sql
INSERT INTO Student VALUES (104, 'Dev', 23, 'Muzaffarpur', 85.0);
SAVEPOINT sp1;   -- Mark this point

INSERT INTO Student VALUES (105, 'Asha', 21, 'Darbhanga', 91.0);
SAVEPOINT sp2;   -- Mark another point

UPDATE Student SET City = 'Bihar' WHERE Roll_No = 104;  -- Made a mistake

ROLLBACK TO sp2;  -- Undo only the UPDATE, keep rows 104 and 105

-- Or rollback further:
ROLLBACK TO sp1;  -- Undo rows 105 AND the UPDATE, keep only row 104

COMMIT;  -- Now save what remains
```

**SAVEPOINT Diagram:**
```
BEGIN TRANSACTION
       │
       ▼
 INSERT row 104  ──► SAVEPOINT sp1
       │
       ▼
 INSERT row 105  ──► SAVEPOINT sp2
       │
       ▼
 UPDATE mistake
       │
   ROLLBACK TO sp2 ──► Goes back to this point
       │               (undoes UPDATE, keeps row 104 + 105)
       ▼
   ROLLBACK TO sp1 ──► Goes back further
                       (undoes row 105 + UPDATE, keeps only row 104)
```

---

## 🧱 SQL CONSTRAINTS — Types and Usage

Constraints enforce rules on data in tables.

```
┌─────────────────┬──────────────────────────────────────────────────────┐
│ Constraint      │ What It Does                                         │
├─────────────────┼──────────────────────────────────────────────────────┤
│ PRIMARY KEY     │ Uniquely identifies each row. NOT NULL + UNIQUE.     │
│                 │ Only ONE per table.                                  │
├─────────────────┼──────────────────────────────────────────────────────┤
│ NOT NULL        │ Column cannot have NULL value.                       │
├─────────────────┼──────────────────────────────────────────────────────┤
│ UNIQUE          │ All values in column must be different.              │
│                 │ CAN have NULL (unlike PRIMARY KEY).                  │
├─────────────────┼──────────────────────────────────────────────────────┤
│ FOREIGN KEY     │ References PRIMARY KEY of another table.            │
│                 │ Enforces referential integrity.                      │
├─────────────────┼──────────────────────────────────────────────────────┤
│ CHECK           │ Ensures values satisfy a condition.                  │
│                 │ e.g., CHECK (Age >= 18)                              │
├─────────────────┼──────────────────────────────────────────────────────┤
│ DEFAULT         │ Sets default value when no value is provided.        │
└─────────────────┴──────────────────────────────────────────────────────┘
```

**NOT a Constraint:** `UNION` (it is a SET OPERATION, not a constraint) — Direct PYQ trap!

```sql
CREATE TABLE Student (
    Roll_No  INT          PRIMARY KEY,       -- PK constraint
    Name     VARCHAR(50)  NOT NULL,          -- NOT NULL constraint
    Email    VARCHAR(100) UNIQUE,            -- UNIQUE constraint
    Age      INT          CHECK (Age >= 5),  -- CHECK constraint
    City     VARCHAR(30)  DEFAULT 'Patna',   -- DEFAULT constraint
    Dept_ID  INT          REFERENCES Dept(Dept_ID)  -- FOREIGN KEY
);
```

---

## 📊 Complete SQL Commands Summary Table

```
┌───────────┬──────────────┬────────────────────────────────────────────────┐
│ Category  │ Command      │ Action & Key Points                            │
├───────────┼──────────────┼────────────────────────────────────────────────┤
│           │ CREATE       │ Create new table/database                      │
│   DDL     │ ALTER        │ Add/modify/drop columns in existing table      │
│ (Structure│ DROP         │ Delete table completely (structure + data)     │
│  changes) │ TRUNCATE     │ Delete all rows, keep structure. No rollback!  │
│           │ RENAME       │ Rename a table                                 │
├───────────┼──────────────┼────────────────────────────────────────────────┤
│           │ SELECT       │ Read/retrieve data from table                  │
│   DML     │ INSERT       │ Add new rows to table                          │
│  (Data    │ UPDATE       │ Modify existing row values                     │
│  changes) │ DELETE       │ Remove specific rows. Can be rolled back!      │
├───────────┼──────────────┼────────────────────────────────────────────────┤
│   DCL     │ GRANT        │ Give permissions to users                      │
│(Permissions│ REVOKE      │ Take away permissions from users               │
├───────────┼──────────────┼────────────────────────────────────────────────┤
│           │ COMMIT       │ Save all changes permanently ★ PYQ             │
│   TCL     │ ROLLBACK     │ Undo all uncommitted changes ★ PYQ             │
│(Transactions│ SAVEPOINT  │ Set intermediate checkpoint in transaction     │
│           │ SET TRANSACTION│ Set transaction properties                   │
└───────────┴──────────────┴────────────────────────────────────────────────┘
```

---

## 🔥 BPSC PYQ High-Frequency Facts — SQL Commands

| PYQ Question Trigger | Answer |
|---------------------|--------|
| COMMIT does what? | Makes changes **PERMANENT** |
| ROLLBACK does what? | **UNDOES** all uncommitted changes |
| TRUNCATE vs DELETE — which can be rolled back? | **DELETE** can be rolled back; **TRUNCATE** cannot |
| DDL commands examples | CREATE, ALTER, DROP, TRUNCATE |
| DML commands examples | SELECT, INSERT, UPDATE, DELETE |
| DCL commands examples | GRANT, REVOKE |
| TCL commands examples | COMMIT, ROLLBACK, SAVEPOINT |
| Which command gives permissions? | **GRANT** |
| Which command removes permissions? | **REVOKE** |
| Which is NOT a constraint? | **UNION** (it's a set operation) |
| How many PRIMARY KEYS per table? | Only **1** |
| Can UNIQUE key have NULL? | **YES** (PRIMARY KEY cannot have NULL, UNIQUE can) |
| TRUNCATE category | **DDL** (not DML!) — many students confuse this |
| SQL was developed by | **IBM** |
| SQL standardized by | **ANSI** |
| SQL type of language | **Declarative** (not procedural) |

---

## 🧠 Memory Tricks for SQL Categories

```
"Careful DICT" mnemonic:

D → DDL  = Define/Design  (CREATE, ALTER, DROP, TRUNCATE)
I        = (skip)
C → DCL  = Control/Access  (GRANT, REVOKE)
T → TCL  = Transactions    (COMMIT, ROLLBACK, SAVEPOINT)

And the most used:
M → DML  = Manipulate Data (SELECT, INSERT, UPDATE, DELETE)
```

**For DDL commands:**
> **"CAD TR"** → Create, Alter, Drop, Truncate, Rename

**For COMMIT vs ROLLBACK:**
> **"COMMIT = Confirm it. ROLLBACK = Take it back."**

**For TRUNCATE:**
> **"TRUNCATE = Cut all rows but keep the skeleton (table structure). Like cutting all branches but keeping the tree trunk."**

---

# ═══════════════════════════════════════════════════════
# 🌿 PART 2: GS — BIOLOGY (Plant Physiology + Photoperiodism)
# ═══════════════════════════════════════════════════════

## 🎯 Why This Section Matters for BPSC

Biology questions appear regularly in BPSC GS section. Plant physiology — especially **Photoperiodism** and **Plant Hormones** — has appeared multiple times. This section covers everything from photosynthesis to plant movements.

---

## ☀️ Photosynthesis — The Energy Factory of Plants

**Definition:** The process by which green plants use sunlight, water, and CO₂ to manufacture food (glucose) and release oxygen.

**Overall Equation:**
```
6CO₂ + 6H₂O  ──── Sunlight / Chlorophyll ────►  C₆H₁₂O₆  +  6O₂
  Carbon         Water                           Glucose       Oxygen
  dioxide
```

### Two Stages of Photosynthesis:

```
STAGE 1: LIGHT REACTIONS (Light-dependent) — occurs in THYLAKOID MEMBRANE
────────────────────────────────────────────────────────────────────────
• Requires: Sunlight + Chlorophyll
• Water molecules are SPLIT (photolysis of water): 2H₂O → 4H⁺ + O₂
• Oxygen is released here
• Produces: ATP (energy) + NADPH (reducing power)
• This stage produces O₂ that we breathe!

                Sunlight
                   │
               Chlorophyll
                   │
         H₂O ──────►  O₂ (released) + ATP + NADPH

STAGE 2: DARK REACTIONS / CALVIN CYCLE (Light-independent) — in STROMA
────────────────────────────────────────────────────────────────────────
• Does NOT need direct light (but uses products from Stage 1)
• Uses ATP + NADPH from Stage 1
• CO₂ is FIXED (converted to glucose)
• Also called: C3 cycle (Calvin-Benson cycle)
• Discovered by: Melvin Calvin (Nobel Prize, 1961)
```

**Key Pigment:** Chlorophyll (in **chloroplasts**)
- Chlorophyll a → Main photosynthetic pigment (blue-green color)
- Chlorophyll b → Accessory pigment (yellow-green)
- Carotenoids → Also accessory (orange, yellow)

> **🔔 Exam Fact:** Photosynthesis occurs in **chloroplasts**. The **leaf** is the primary organ of photosynthesis. Aquatic plants can use dissolved CO₂.

---

## 🌙 PHOTOPERIODISM — The Most Important Topic Today

### Definition:
**Photoperiodism** = The response of plants to the **relative length of day (light period) and night (dark period)** that determines FLOWERING.

### Discovered By:
**W.W. Garner and H.A. Allard** (American Scientists, 1920) — while working on Tobacco plant (Maryland Mammoth variety).

```
KEY DISCOVERY:
Garner & Allard found that the tobacco plant flowers only in SHORT DAYS (long nights)
They named this phenomenon: PHOTOPERIODISM
```

### The Critical Night (Not Day!) Concept:

> **🔔 The BIG Exam Trap:** Plants actually respond to the **length of the DARK PERIOD (night)**, NOT the light period — even though it is called "photoperiodism"!

```
The critical factor = LENGTH OF CONTINUOUS DARK PERIOD (night length)
        ↑
  This is what actually controls flowering!
```

---

### 🌸 Classification of Plants Based on Photoperiodism:

```
┌─────────────────────────┬───────────────────────────────────────────────────────┐
│ Plant Type              │ Description + Examples                                │
├─────────────────────────┼───────────────────────────────────────────────────────┤
│ SHORT DAY PLANTS (SDP)  │ • Flower when day is SHORTER than critical length     │
│ = Long Night Plants     │ • Need long continuous dark period to flower          │
│                         │ • Flower in WINTER / late autumn                      │
│                         │ Examples: Rice, Soybean, Sugarcane, Chrysanthemum,    │
│                         │           Cotton, Tobacco (Maryland Mammoth),         │
│                         │           Cocklebur (Xanthium), Poinsettia            │
├─────────────────────────┼───────────────────────────────────────────────────────┤
│ LONG DAY PLANTS (LDP)   │ • Flower when day is LONGER than critical length      │
│ = Short Night Plants    │ • Need short continuous dark period to flower         │
│                         │ • Flower in SUMMER / spring                           │
│                         │ Examples: Wheat, Barley, Oat, Radish, Spinach,        │
│                         │           Henbane (Hyoscyamus), Sugar beet,           │
│                         │           Carnation, Larkspur                         │
├─────────────────────────┼───────────────────────────────────────────────────────┤
│ DAY NEUTRAL PLANTS (DNP)│ • NOT affected by day/night length                   │
│                         │ • Flower regardless of photoperiod                    │
│                         │ Examples: Tomato, Maize/Corn, Sunflower, Cucumber,   │
│                         │           Castor, Rose, Pea                           │
└─────────────────────────┴───────────────────────────────────────────────────────┘
```

**Visual Diagram:**
```
SHORT DAY PLANT (e.g., Rice):
Day:   ████░░░░░░░░░░░░░░  (Short Day < Critical Length)
Night: ░░░░████████████████  (Long Night > Critical Length)
Result: FLOWERS ✿

LONG DAY PLANT (e.g., Wheat):
Day:   ██████████████░░░░  (Long Day > Critical Length)
Night: ░░░░░░░░████████████  (Short Night < Critical Length)  
Result: FLOWERS ✿

DAY NEUTRAL PLANT (e.g., Tomato):
Day:   Any length
Night: Any length
Result: FLOWERS regardless ✿
```

---

### 🧬 Phytochrome — The Photoreceptor

The protein responsible for detecting light/dark signals is **PHYTOCHROME**.

```
Phytochrome exists in TWO forms:

Pr (Red-absorbing form)    ←────── Red Light (660 nm)
        │
        │ absorbs red light
        ▼
Pfr (Far-red absorbing)    ←────── Far-red Light (730 nm)
        │
        │ Pfr is the ACTIVE form that promotes/inhibits flowering
        │
        ▼
    DARKNESS converts Pfr → Pr (slowly)
```

**Key Point:** During continuous night (dark period), Pfr slowly converts back to Pr. This is how plants "measure" night length.

> **🔔 Exam Fact:** If you interrupt the dark period with a brief flash of **RED LIGHT** (660 nm) → inhibits SDP flowering (converts Pr → Pfr). If followed by **FAR-RED LIGHT** (730 nm) → reverses the effect.

---

## 🌱 PLANT HORMONES (Phytohormones)

Plant hormones are **chemical messengers** produced in one part of the plant that affect another part. Also called **Phytohormones**.

```
┌────────────────┬──────────────────┬────────────────────────────────────────────┐
│ Hormone        │ Primary Site of  │ Main Functions                             │
│                │ Production       │                                            │
├────────────────┼──────────────────┼────────────────────────────────────────────┤
│ AUXIN          │ Shoot tip (apical│ • Cell elongation (growth promotion)       │
│ (IAA)          │ meristem)        │ • Phototropism (bending toward light)      │
│                │                  │ • Geotropism                               │
│                │                  │ • Apical dominance (suppresses side buds) │
│                │                  │ • Root initiation in stem cuttings         │
│                │                  │ Discovered by: Charles Darwin (initially)  │
│                │                  │ Isolated by: F.W. Went (1926)             │
├────────────────┼──────────────────┼────────────────────────────────────────────┤
│ GIBBERELLIN    │ Young leaves,    │ • Stem elongation (tallness)               │
│ (GA₃)          │ seeds, roots     │ • Breaks seed dormancy                     │
│                │                  │ • Promotes germination                     │
│                │                  │ • Delays senescence (aging) of leaves      │
│                │                  │ • Causes 'bolting' in rosette plants        │
│                │                  │ Discovered in rice disease: Bakanae        │
│                │                  │ (foolish seedling disease) by Kurosawa    │
├────────────────┼──────────────────┼────────────────────────────────────────────┤
│ CYTOKININ      │ Root tips,       │ • Cell division (cytokinesis)              │
│ (Zeatin)       │ developing seeds │ • Delays leaf senescence                   │
│                │                  │ • Promotes lateral bud growth              │
│                │                  │ • Overcomes apical dominance               │
│                │                  │ Discovered by: Skoog and Miller (1955)    │
├────────────────┼──────────────────┼────────────────────────────────────────────┤
│ ABSCISIC ACID  │ Leaves, roots,   │ • STRESS HORMONE — called "stress hormone" │
│ (ABA)          │ seeds            │ • Causes stomata CLOSURE in drought        │
│                │                  │ • Induces seed dormancy                    │
│                │                  │ • Promotes leaf/fruit abscission (shedding)│
│                │                  │ • Inhibits growth (growth inhibitor)       │
│                │                  │ Also called: Dormin                        │
├────────────────┼──────────────────┼────────────────────────────────────────────┤
│ ETHYLENE       │ Ripening fruits, │ • Fruit RIPENING (most important role)     │
│ (Gas hormone)  │ nodes, leaves    │ • Promotes senescence (aging + death)      │
│                │                  │ • Causes epinasty (downward bending)       │
│                │                  │ • Triple response in seedlings             │
│                │                  │ • Only GASEOUS plant hormone               │
│                │                  │ Commercial use: banana/mango ripening      │
└────────────────┴──────────────────┴────────────────────────────────────────────┘
```

---

### 🌿 Quick Memory Trick for Plant Hormones:

```
"AGACE" — All Good Children Always Excel

A → Auxin      → Apical growth, cell elongation
G → Gibberellin → Growth (stem elongation), Germination  
A → ABA         → Abscission, Arrest growth (stress, drought)
C → Cytokinin   → Cell division
E → Ethylene    → Every fruit ripens (gas hormone)
```

---

## 🌸 TROPISMS — Directional Plant Movements

Tropisms are growth movements in response to directional stimuli.

```
┌───────────────┬──────────────────┬──────────────────────────────────────────┐
│ Tropism       │ Stimulus         │ Example                                  │
├───────────────┼──────────────────┼──────────────────────────────────────────┤
│ PHOTOTROPISM  │ Light            │ Shoot bends TOWARD light (+ve phototropism│
│               │                  │ Roots grow AWAY from light (-ve)          │
├───────────────┼──────────────────┼──────────────────────────────────────────┤
│ GEOTROPISM    │ Gravity          │ Roots grow DOWNWARD (+ve geotropism)      │
│ (Gravitropism)│                  │ Shoots grow UPWARD (-ve geotropism)       │
├───────────────┼──────────────────┼──────────────────────────────────────────┤
│ HYDROTROPISM  │ Water            │ Roots grow TOWARD water (+ve)             │
├───────────────┼──────────────────┼──────────────────────────────────────────┤
│ THIGMOTROPISM │ Touch/contact    │ Tendrils of pea, grapevine coil around   │
│               │                  │ support                                  │
├───────────────┼──────────────────┼──────────────────────────────────────────┤
│ CHEMOTROPISM  │ Chemicals        │ Pollen tube grows toward ovule           │
└───────────────┴──────────────────┴──────────────────────────────────────────┘
```

**Key:** Auxin is responsible for PHOTOTROPISM.
- More auxin accumulates on the DARK side of the stem
- Dark side elongates MORE → stem bends TOWARD light

---

## 🌿 RESPIRATION IN PLANTS

Plants respire (break down glucose for energy) in ALL living cells, ALL the time — unlike photosynthesis which needs light.

```
Aerobic Respiration:
C₆H₁₂O₆  +  6O₂  ──►  6CO₂  +  6H₂O  +  38 ATP (energy)
 Glucose    Oxygen      Carbon   Water     Energy
                        dioxide

Anaerobic Respiration (no oxygen):
C₆H₁₂O₆  ──►  2C₂H₅OH  +  2CO₂  +  2 ATP
 Glucose       Ethanol    Carbon    Energy
```

**Key Difference:**
- Photosynthesis: Takes CO₂, Releases O₂ (in light)
- Respiration: Takes O₂, Releases CO₂ (always, day and night)

> **🔔 Exam Trap:** During DAY — both photosynthesis AND respiration occur in plants. Net effect = O₂ released (photosynthesis rate >> respiration rate). During NIGHT — only respiration occurs.

---

## 🌸 OTHER IMPORTANT PLANT PHYSIOLOGY TOPICS

### Transpiration — Loss of water through leaves

- Occurs mainly through **stomata** (tiny pores in leaves)
- Guard cells control opening/closing of stomata
- Functions: Cools the plant, drives water absorption from roots, nutrient transport
- **Transpiration Pull** = mechanism that pulls water from roots to leaves against gravity

### Stomata:
```
Open Stomata (Day):           Closed Stomata (Night/Drought):
  [Guard Cell]  [Guard Cell]      [Guard Cell][Guard Cell]
       \      /                         |    |
        [ OPEN ]                        [CLOSED]
     → Gas exchange                  → Water conservation
```

---

## 📝 High-Frequency GS PYQ Facts — Biology

| Question Trigger | Answer |
|-----------------|--------|
| Photoperiodism discovered by | **Garner and Allard** (1920) |
| Photoperiodism = plant response to | **Relative length of day and night** |
| Critical factor in photoperiodism | **Length of continuous dark period (night length)** |
| Short Day Plants example | Rice, Soybean, Chrysanthemum, Tobacco, Sugarcane |
| Long Day Plants example | Wheat, Barley, Spinach, Radish, Sugar beet |
| Day Neutral Plants example | Tomato, Maize, Sunflower, Pea |
| Hormone for fruit ripening | **Ethylene** |
| Gaseous plant hormone | **Ethylene** |
| Stress hormone in plants | **ABA (Abscisic Acid)** |
| Hormone causing stem elongation | **Gibberellin** |
| Hormone for cell division | **Cytokinin** |
| Auxin responsible for | **Phototropism, cell elongation** |
| Gibberellin discovered from | **Bakanae disease** of rice |
| Photoreceptor for photoperiodism | **Phytochrome** |
| Photosynthesis occurs in | **Chloroplasts** (specifically thylakoid membranes) |
| O₂ released in photosynthesis from | **Water** (not CO₂) |
| Calvin Cycle is also called | **Dark Reactions / C3 cycle** |
| Auxin isolated by | **F.W. Went (1926)** |
| Plant hormone = ABA also called | **Dormin** |
| Stomata controlled by | **Guard cells** |

---

# ═══════════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 40
# ═══════════════════════════════════════════════════════

> ⚠️ **STRICT RULE:** Solve ALL 50 questions before scrolling to the Answer Key.
> The Answer Key is provided ONLY after Q50.
> Option D = "More than one of the above" | Option E = "None of the above"

---

# 💻 SECTION A: CS QUESTIONS — SQL COMMANDS (Q1–Q25)

---

**Q1.** Which of the following is the correct classification of SQL commands?

(A) DDL, DML, DCL, TCL
(B) DDL, DQL, DAL, TCL
(C) DDL, DML, SQL, DCL
(D) More than one of the above
(E) None of the above

---

**Q2.** The SQL command used to make all pending transaction changes PERMANENT is:

(A) ROLLBACK
(B) SAVEPOINT
(C) COMMIT
(D) SET TRANSACTION
(E) None of the above

---

**Q3.** Which of the following SQL commands CANNOT be rolled back?

(A) DELETE
(B) UPDATE
(C) INSERT
(D) More than one of the above
(E) TRUNCATE

---

**Q4.** The command GRANT belongs to which category of SQL?

(A) DDL
(B) DML
(C) TCL
(D) DCL

---

**Q5.** Consider the following SQL commands:
```
INSERT INTO Employee VALUES (201, 'Mohan', 'HR');
SAVEPOINT S1;
UPDATE Employee SET Dept = 'IT' WHERE Emp_ID = 201;
ROLLBACK TO S1;
```
After executing all four statements, what is the department of employee 201?

(A) IT
(B) HR
(C) NULL
(D) The row is deleted
(E) None of the above

---

**Q6.** Which SQL command removes ALL rows from a table but preserves the table structure, and CANNOT be rolled back?

(A) DELETE
(B) DROP
(C) TRUNCATE
(D) REMOVE
(E) None of the above

---

**Q7.** The SQL command to add a new column "Email" to an existing table "Customer" is:

(A) `CREATE TABLE Customer ADD Email VARCHAR(100);`
(B) `ALTER TABLE Customer ADD Email VARCHAR(100);`
(C) `UPDATE TABLE Customer ADD Email VARCHAR(100);`
(D) `MODIFY TABLE Customer ADD Email VARCHAR(100);`
(E) None of the above

---

**Q8.** Which of the following is NOT a valid DML command in SQL?

(A) SELECT
(B) UPDATE
(C) TRUNCATE
(D) INSERT
(E) DELETE

---

**Q9.** The REVOKE command in SQL is used to:

(A) Delete a user from the database
(B) Undo the last transaction
(C) Remove previously granted permissions from a user
(D) More than one of the above
(E) None of the above

---

**Q10.** ROLLBACK in SQL:

(A) Saves all changes permanently
(B) Undoes all changes made since the last COMMIT or beginning of transaction
(C) Rolls back only DDL changes
(D) Creates a savepoint to return to
(E) None of the above

---

**Q11.** Which of the following is a DDL command?

(A) SELECT
(B) COMMIT
(C) GRANT
(D) DROP
(E) None of the above

---

**Q12.** Consider: `DELETE FROM Student;` — What does this command do?

(A) Drops the Student table completely
(B) Deletes all rows but keeps the table structure; can be rolled back
(C) Same as TRUNCATE
(D) Removes selected rows based on a condition
(E) None of the above

---

**Q13.** SQL was originally developed by:

(A) Microsoft
(B) Oracle
(C) IBM
(D) Sun Microsystems
(E) None of the above

---

**Q14.** Which of the following is NOT a valid table constraint in SQL?

(A) PRIMARY KEY
(B) FOREIGN KEY
(C) NOT NULL
(D) UNION
(E) CHECK

---

**Q15.** The difference between UNIQUE key and PRIMARY KEY is:

(A) UNIQUE key allows NULL values; PRIMARY KEY does NOT allow NULL
(B) PRIMARY KEY allows NULL; UNIQUE does not
(C) Both allow NULL values
(D) Both do not allow NULL values
(E) None of the above

---

**Q16.** A SAVEPOINT in SQL is used for:

(A) Permanently saving changes to the database
(B) Setting an intermediate point in a transaction to which a partial rollback can be done
(C) Creating a backup of the database
(D) More than one of the above
(E) None of the above

---

**Q17.** Which SQL command gives the user 'Admin' ALL privileges on the 'Orders' table?

(A) `ALLOW ALL ON Orders TO Admin;`
(B) `GRANT ALL PRIVILEGES ON Orders TO Admin;`
(C) `PERMIT ALL ON Orders FOR Admin;`
(D) `ACCESS ALL ON Orders TO Admin;`
(E) None of the above

---

**Q18.** The TCL command SET TRANSACTION is used to:

(A) Delete a transaction
(B) Set the properties of a transaction (like isolation level)
(C) Create a new database transaction table
(D) More than one of the above
(E) None of the above

---

**Q19.** In SQL, DDL commands are:

(A) Not auto-committed — require explicit COMMIT
(B) Auto-committed — changes are permanent immediately and cannot be rolled back
(C) Can be rolled back using ROLLBACK command
(D) Require SAVEPOINT before execution
(E) None of the above

---

**Q20.** Which of the following SQL commands DELETES the entire table including its structure from the database?

(A) TRUNCATE
(B) DELETE
(C) DROP
(D) REMOVE
(E) None of the above

---

**Q21.** The SELECT command belongs to which category?

(A) DDL
(B) DML
(C) DCL
(D) TCL
(E) None of the above

---

**Q22.** Which of the following is the correct syntax to create a table with a check constraint?

(A) `CREATE TABLE T (Age INT CHECK Age >= 18);`
(B) `CREATE TABLE T (Age INT CHECK (Age >= 18));`
(C) `CREATE TABLE T (Age INT VALIDATE (Age >= 18));`
(D) `CREATE TABLE T (Age INT RESTRICT (Age >= 18));`
(E) None of the above

---

**Q23.** Consider two statements:
Statement 1: TRUNCATE is a DDL command.
Statement 2: TRUNCATE cannot be rolled back.

(A) Only Statement 1 is correct
(B) Only Statement 2 is correct
(C) Both statements are correct
(D) Both statements are incorrect
(E) None of the above

---

**Q24.** Which of the following correctly describes the FOREIGN KEY constraint?

(A) It ensures all values in a column are unique
(B) It references the PRIMARY KEY of the same or another table to enforce referential integrity
(C) It allows NULL values to be stored
(D) More than one of the above
(E) None of the above

---

**Q25.** SQL is classified as what type of language?

(A) Procedural language
(B) Object-Oriented language
(C) Declarative language
(D) Machine language
(E) None of the above

---

# 🌿 SECTION B: GS QUESTIONS — BIOLOGY (Q26–Q50)

---

**Q26.** Photoperiodism was discovered by:

(A) Charles Darwin and Francis Darwin
(B) W.W. Garner and H.A. Allard
(C) F.W. Went and T. Cholodny
(D) Mendel and Morgan
(E) None of the above

---

**Q27.** Photoperiodism in plants refers to the response of plants to:

(A) Intensity of light
(B) Wavelength of light
(C) Relative duration of light and dark periods
(D) Total amount of light received per year
(E) None of the above

---

**Q28.** The actual critical factor that controls flowering in photoperiodism is:

(A) Length of light period (day length)
(B) Intensity of light
(C) Length of continuous dark period (night length)
(D) Temperature of the environment
(E) None of the above

---

**Q29.** Which of the following is a SHORT DAY PLANT?

(A) Wheat
(B) Barley
(C) Rice
(D) More than one of the above
(E) None of the above

---

**Q30.** Long Day Plants (LDP) flower when:

(A) The day length is SHORTER than the critical photoperiod
(B) The day length is LONGER than the critical photoperiod
(C) Temperature drops below 10°C
(D) The dark period is longer than 12 hours
(E) None of the above

---

**Q31.** Which of the following plants is classified as a DAY NEUTRAL PLANT?

(A) Rice
(B) Wheat
(C) Tomato
(D) Chrysanthemum
(E) None of the above

---

**Q32.** The photoreceptor protein responsible for detecting the light/dark signal in photoperiodism is:

(A) Chlorophyll
(B) Phytochrome
(C) Carotenoid
(D) Flavoprotein
(E) None of the above

---

**Q33.** Which plant hormone is responsible for FRUIT RIPENING and is also the ONLY GASEOUS plant hormone?

(A) Auxin
(B) Gibberellin
(C) Cytokinin
(D) Abscisic Acid
(E) Ethylene

---

**Q34.** Abscisic Acid (ABA) is also known as the "stress hormone" because:

(A) It promotes rapid cell division under stress
(B) It causes stomata to close during water stress/drought
(C) It accelerates fruit ripening during heat stress
(D) More than one of the above
(E) None of the above

---

**Q35.** The hormone GIBBERELLIN was first discovered in connection with which plant disease?

(A) Mosaic disease of tobacco
(B) Bakanae (foolish seedling) disease of rice
(C) Black stem rust of wheat
(D) Late blight of potato
(E) None of the above

---

**Q36.** The plant hormone that promotes CELL DIVISION and helps overcome apical dominance is:

(A) Auxin
(B) Gibberellin
(C) Cytokinin
(D) Ethylene
(E) ABA

---

**Q37.** Apical dominance in plants is caused by:

(A) High concentration of Cytokinin at the shoot tip
(B) High concentration of Auxin produced at the shoot tip that suppresses lateral bud growth
(C) Ethylene produced in the roots
(D) ABA accumulation in the stem
(E) None of the above

---

**Q38.** In photosynthesis, OXYGEN is released from the splitting of:

(A) Carbon dioxide (CO₂)
(B) Water (H₂O)
(C) Glucose (C₆H₁₂O₆)
(D) Both CO₂ and H₂O
(E) None of the above

---

**Q39.** The Calvin Cycle (Dark Reactions) in photosynthesis occurs in:

(A) Thylakoid membranes of chloroplasts
(B) Mitochondria
(C) Stroma of chloroplasts
(D) Nucleus
(E) None of the above

---

**Q40.** Which of the following is CORRECT about plant respiration?

(A) Plants respire only during night time
(B) Plants respire only in the presence of light
(C) Plants respire continuously — in all living cells, day and night
(D) Plants respire only in leaves
(E) None of the above

---

**Q41.** The bending of plants TOWARD light is called:

(A) Geotropism
(B) Hydrotropism
(C) Phototropism
(D) Thigmotropism
(E) None of the above

---

**Q42.** Which plant hormone was isolated by F.W. Went in 1926 from the coleoptile tips of oat seedlings?

(A) Gibberellin
(B) Cytokinin
(C) Auxin (IAA — Indole Acetic Acid)
(D) Ethylene
(E) ABA

---

**Q43.** The stomata in plant leaves are controlled by:

(A) Mesophyll cells
(B) Guard cells
(C) Epidermal cells
(D) Trichomes
(E) None of the above

---

**Q44.** Transpiration in plants primarily occurs through:

(A) Roots
(B) Stomata on leaves
(C) Lenticels on stem
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following correctly matches the hormone with its function?

(A) Auxin → Fruit ripening
(B) Gibberellin → Stomata closure
(C) Cytokinin → Cell division
(D) Ethylene → Seed dormancy
(E) ABA → Cell elongation

---

**Q46.** The process by which a plant loses water vapour through its aerial parts (mainly leaves) is called:

(A) Transpiration
(B) Guttation
(C) Translocation
(D) Plasmolysis
(E) None of the above

---

**Q47.** Which of the following plants is a LONG DAY PLANT (requires short nights to flower)?

(A) Rice
(B) Chrysanthemum
(C) Tobacco
(D) Spinach
(E) Sugarcane

---

**Q48.** If the dark period of a short day plant is interrupted by a brief flash of light, the result is:

(A) Flowering is promoted
(B) Flowering is inhibited because the continuous dark period is disrupted
(C) No effect on flowering
(D) Vegetative growth stops
(E) None of the above

---

**Q49.** Consider the following pairs:
1. Photoperiodism — Garner and Allard
2. Auxin isolation — F.W. Went
3. Cytokinin discovery — Skoog and Miller
4. Gibberellin — Bakanae disease of rice

How many of the above pairs are CORRECTLY matched?

(A) Only 1 and 2
(B) Only 1, 2, and 3
(C) All four pairs are correctly matched
(D) Only 2 and 4
(E) None of the above

---

**Q50.** ABA (Abscisic Acid) in plants is also known as:

(A) Florigen
(B) Traumatin
(C) Dormin
(D) Vernalin
(E) None of the above

---

# ═══════════════════════════════════════════════════════
# 🔑 ANSWER KEY — ALL 50 QUESTIONS
# ═══════════════════════════════════════════════════════

> ✅ Only check answers AFTER attempting all 50 questions!

---

## 💻 CS ANSWERS — SQL Commands (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| 1 | **(A)** | The four SQL command categories are DDL, DML, DCL, and TCL. This is the standard classification. |
| 2 | **(C)** | **COMMIT** makes all pending transaction changes permanent. Key PYQ fact — memorize it. |
| 3 | **(E)** | **TRUNCATE** cannot be rolled back. DELETE, UPDATE, INSERT are all DML and can be rolled back. Option E here is TRUNCATE specifically. |
| 4 | **(D)** | GRANT belongs to **DCL (Data Control Language)**. DCL manages permissions. |
| 5 | **(B)** | ROLLBACK TO S1 undoes the UPDATE command, reverting Emp 201's dept back to 'HR' (the state at SAVEPOINT S1). |
| 6 | **(C)** | **TRUNCATE** removes all rows, keeps table structure, and CANNOT be rolled back (it is a DDL command). |
| 7 | **(B)** | `ALTER TABLE Customer ADD Email VARCHAR(100);` — ALTER is the correct DDL command to modify an existing table structure. |
| 8 | **(C)** | **TRUNCATE** is NOT a DML command — it is a DDL command. SELECT, UPDATE, INSERT, DELETE are all DML. |
| 9 | **(C)** | REVOKE removes previously granted permissions from a user. It is a DCL command. |
| 10 | **(B)** | ROLLBACK **undoes all changes** made since the last COMMIT or beginning of the transaction. |
| 11 | **(D)** | **DROP** is a DDL command. SELECT is DML, COMMIT is TCL, GRANT is DCL. |
| 12 | **(B)** | `DELETE FROM Student;` removes ALL rows but keeps the table structure, and **can be rolled back** (it's DML). Different from TRUNCATE. |
| 13 | **(C)** | SQL was originally developed by **IBM** in the 1970s (originally called SEQUEL). |
| 14 | **(D)** | **UNION** is a SET OPERATION (combines results of two SELECT queries), NOT a constraint. PRIMARY KEY, FOREIGN KEY, NOT NULL, CHECK are all valid constraints. |
| 15 | **(A)** | **UNIQUE allows NULL; PRIMARY KEY does NOT allow NULL.** Both enforce uniqueness, but only PK rejects NULL. |
| 16 | **(B)** | SAVEPOINT sets an intermediate checkpoint in a transaction, allowing **partial rollback** to that point. |
| 17 | **(B)** | `GRANT ALL PRIVILEGES ON Orders TO Admin;` is the correct SQL DCL syntax. |
| 18 | **(B)** | SET TRANSACTION sets the properties of a transaction such as isolation level (READ COMMITTED, SERIALIZABLE, etc.). |
| 19 | **(B)** | DDL commands are **auto-committed** — changes are permanent immediately and cannot be rolled back using ROLLBACK. |
| 20 | **(C)** | **DROP** deletes the entire table including its structure. TRUNCATE only removes rows. DELETE removes rows with WHERE. |
| 21 | **(B)** | SELECT is a **DML (Data Manipulation Language)** command — it reads/retrieves data. |
| 22 | **(B)** | Correct CHECK syntax: `CHECK (Age >= 18)` with parentheses. |
| 23 | **(C)** | Both statements are correct: TRUNCATE is DDL (Statement 1 ✓) and TRUNCATE cannot be rolled back (Statement 2 ✓). |
| 24 | **(B)** | FOREIGN KEY references the PRIMARY KEY of the same or another table to enforce referential integrity. |
| 25 | **(C)** | SQL is a **Declarative language** — you specify WHAT you want, not HOW to get it. Unlike procedural languages (C, Java). |

---

## 🌿 GS ANSWERS — Biology (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| 26 | **(B)** | **W.W. Garner and H.A. Allard** discovered Photoperiodism in 1920 while working on tobacco plants. Direct PYQ fact. |
| 27 | **(C)** | Photoperiodism = response to the **relative duration of light and dark periods** (NOT intensity or wavelength). |
| 28 | **(C)** | The critical factor is the **length of continuous dark period (night)**, NOT day length. This is the classic exam trap — despite the name "photoperiodism", darkness controls it. |
| 29 | **(C)** | **Rice** is a Short Day Plant. Wheat and Barley are Long Day Plants. |
| 30 | **(B)** | Long Day Plants flower when day length is **LONGER than the critical photoperiod** (i.e., short nights, long days). |
| 31 | **(C)** | **Tomato** is a Day Neutral Plant — flowers regardless of day/night length. Rice and Chrysanthemum are SDP, Wheat is LDP. |
| 32 | **(B)** | **Phytochrome** is the photoreceptor protein that detects the light/dark signals. It exists in two interconvertible forms (Pr and Pfr). |
| 33 | **(E)** | **Ethylene** is responsible for fruit ripening AND is the only gaseous plant hormone. |
| 34 | **(B)** | ABA causes **stomata closure** during water stress/drought, conserving water — hence called the "stress hormone." |
| 35 | **(B)** | Gibberellin was discovered from **Bakanae (foolish seedling) disease of rice** — infected rice grew abnormally tall. |
| 36 | **(C)** | **Cytokinin** promotes cell division and helps overcome apical dominance (allowing lateral buds to grow). |
| 37 | **(B)** | **Auxin** produced at the shoot tip in high concentrations suppresses the growth of lateral buds — this is apical dominance. |
| 38 | **(B)** | In photosynthesis, O₂ is released from the splitting of **water (H₂O)** during the light reactions (photolysis of water). NOT from CO₂. |
| 39 | **(C)** | The Calvin Cycle / Dark Reactions occurs in the **stroma of chloroplasts**. Light reactions occur in the thylakoid membranes. |
| 40 | **(C)** | Plants **respire continuously** — in ALL living cells, ALL the time (day and night). Only photosynthesis needs light. |
| 41 | **(C)** | Bending toward light = **Phototropism**. Bending toward gravity = geotropism. |
| 42 | **(C)** | **Auxin (IAA — Indole Acetic Acid)** was isolated by F.W. Went in 1926 from oat coleoptile tips. |
| 43 | **(B)** | Stomata are controlled by **guard cells** — they swell (open) or shrink (close) based on water content. |
| 44 | **(B)** | Transpiration occurs mainly through **stomata on leaves** (also via lenticels and cuticle, but stomata is primary). |
| 45 | **(C)** | Correct: **Cytokinin → Cell division**. Auxin = elongation; Gibberellin = stem elongation/germination; Ethylene = ripening; ABA = dormancy/closure. |
| 46 | **(A)** | **Transpiration** = loss of water vapor through aerial parts (mainly leaves through stomata). |
| 47 | **(D)** | **Spinach** is a Long Day Plant (requires short nights/long days). Rice, Chrysanthemum, Tobacco, Sugarcane are SDP. |
| 48 | **(B)** | Interrupting the dark period of a Short Day Plant with light **inhibits flowering** — the continuous dark period is broken, so the SDP cannot achieve the required night length to flower. |
| 49 | **(C)** | **All four pairs are correctly matched**: Photoperiodism-Garner&Allard ✓, Auxin-F.W.Went ✓, Cytokinin-Skoog&Miller ✓, Gibberellin-Bakanae disease ✓. |
| 50 | **(C)** | ABA is also called **Dormin** — an older name used when it was first discovered as a dormancy-inducing compound. |

---

# ═══════════════════════════════════════════════════════
# 🎯 TOPPER'S CORNER — DAY 40 CHECKLIST
# ═══════════════════════════════════════════════════════

## CS SQL Commands — Must-Know Before Exam Day

- [ ] All 4 categories with commands memorized (DDL, DML, DCL, TCL)
- [ ] COMMIT = permanent. ROLLBACK = undo. (Direct PYQ)
- [ ] TRUNCATE = DDL (NOT DML), cannot be rolled back
- [ ] DELETE = DML, CAN be rolled back
- [ ] GRANT = give permissions (DCL), REVOKE = remove permissions (DCL)
- [ ] UNION is NOT a constraint (constraint trap in PYQ)
- [ ] UNIQUE allows NULL; PRIMARY KEY does not
- [ ] DDL = auto-committed; DML = requires explicit COMMIT
- [ ] SQL was developed by IBM (declarative language)
- [ ] SAVEPOINT = intermediate checkpoint in transaction

## GS Biology — Must-Know Before Exam Day

- [ ] Photoperiodism discovered by Garner and Allard (1920)
- [ ] Critical factor = length of dark period (NOT light period!)
- [ ] SDP examples: Rice, Soybean, Chrysanthemum, Tobacco
- [ ] LDP examples: Wheat, Barley, Spinach, Radish
- [ ] DNP examples: Tomato, Maize, Sunflower, Pea
- [ ] Ethylene = fruit ripening + only gaseous hormone
- [ ] ABA = stress hormone (stomata closure)
- [ ] Gibberellin = from Bakanae disease of rice
- [ ] Cytokinin = cell division
- [ ] Auxin = phototropism, cell elongation, apical dominance
- [ ] O₂ in photosynthesis comes from WATER (not CO₂)
- [ ] Calvin Cycle is in STROMA; Light reactions in THYLAKOID
- [ ] Phytochrome = photoreceptor for photoperiodism

---

## 📊 Score Yourself

| Score | Performance | Action |
|-------|-------------|--------|
| 45–50 | 🏆 Topper Level | Brief revision + move to Day 41 |
| 38–44 | ✅ On Track | Re-read missed points tonight |
| 30–37 | ⚠️ Needs Work | Re-read both CS and GS concepts today |
| < 30  | ❌ Revise | Re-study from scratch before Day 41 |

---

## 📅 Day 41 Preview

**CS:** SQL SELECT Query — ORDER BY, GROUP BY, HAVING, Aggregate Functions (COUNT, SUM, AVG, MAX, MIN)
**GS:** Biology — Immunity, Lymphocytes, Vaccines, Human Diseases

Key PYQ Fact for tomorrow: **ORDER BY default = ASC. HAVING = for GROUP BY results. COMPUTE = NOT a valid aggregate function.**

---

*Day 40 Complete ✅ | SQL + Plant Biology mastered | Target: 130+/150 | TOP 50 Rank 🎯*
