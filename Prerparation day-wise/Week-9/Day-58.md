# 📅 BPSC TRE 4.0 — DAY 58 COMPLETE STUDY MODULE
### SQL: Transaction Management & Constraints + Current Affairs — Space Technology
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): SQL — ACID Properties, Transactions, COMMIT/ROLLBACK/SAVEPOINT, DELETE vs TRUNCATE vs DROP, Concurrency Control, RAW Data Type, Constraints
> - Afternoon (1 hr): Current Affairs — Space Technology (ISRO, Gaganyaan, Aditya-L1, Chandrayaan)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 SQL Transaction Management & Database Constraints

---

## 🔷 SECTION 1: What is a Transaction?

### The Core Idea:

Imagine you are transferring ₹5000 from your **SBI account** to your friend's **PNB account**. This involves two operations:
1. **Deduct ₹5000** from your SBI account
2. **Add ₹5000** to your friend's PNB account

Now — what if the power fails AFTER step 1 but BEFORE step 2? ₹5000 is gone from your account but never arrived at your friend's account. **Money vanished!**

This is why we need **TRANSACTIONS** — a mechanism that ensures either BOTH operations happen, or NEITHER does.

> **A Transaction is a sequence of one or more SQL operations treated as a single logical unit of work. Either ALL operations in a transaction succeed (COMMIT), or ALL are undone (ROLLBACK).**

```
TRANSACTION = ATOMIC UNIT OF WORK

BEGIN TRANSACTION
  ┌───────────────────────────────────────────────┐
  │  Step 1: UPDATE account SET balance =         │
  │          balance - 5000 WHERE acc = 'SBI101'; │
  │                                               │
  │  Step 2: UPDATE account SET balance =         │
  │          balance + 5000 WHERE acc = 'PNB202'; │
  └───────────────────────────────────────────────┘
                    ↓
       Did BOTH steps succeed? 
       YES → COMMIT  (changes are permanent)
       NO  → ROLLBACK (undo ALL changes — back to start)
```

### Transaction States:

```
TRANSACTION LIFECYCLE:

    BEGIN
      │
      ▼
  [ACTIVE] ──────────────────────────────────────────────────────────┐
      │ (operations executing)                                        │
      │ (an error occurs / rollback requested)                        │
      ▼                                                              ▼
  [PARTIALLY COMMITTED] ─── fails ──► [FAILED] ──► [ABORTED/ROLLED BACK]
      │ (all operations done,                            │
      │  writing to disk)                                ▼
      ▼ (success)                              Database restored to state
  [COMMITTED]                                 before transaction began
      │
      ▼
  Changes are PERMANENT — cannot be undone

STATES SUMMARY:
  Active     → Transaction is executing
  Partially Committed → All operations done, awaiting final confirmation
  Committed  → Changes written to disk permanently (COMMIT issued)
  Failed     → Error occurred; cannot proceed
  Aborted    → ROLLBACK done; database restored to pre-transaction state
```

---

## 🔷 SECTION 2: ACID Properties — The Four Pillars of Transactions

**ACID** is the most tested concept in transaction management. Every property must be known cold.

### 🧠 MNEMONIC: "A Bank Always Confirms Integrity Daily"
```
A → Atomicity
C → Consistency
I → Isolation
D → Durability
```

---

### PROPERTY 1 — ATOMICITY

```
DEFINITION: A transaction is treated as a SINGLE INDIVISIBLE unit.
            Either ALL operations in the transaction execute completely,
            or NONE of them execute at all.
            There is NO partial execution.

"ALL or NOTHING"

EXAMPLE:
  Transfer ₹5000:
  ✅ ATOMIC SUCCESS: Debit + Credit BOTH happen → COMMIT
  ✅ ATOMIC FAILURE: Debit + Credit NEITHER happen → ROLLBACK
  ❌ NOT ATOMIC: Debit happens, Credit fails → this is REJECTED by Atomicity!

WHO ENSURES IT?
  → Transaction Management component of DBMS
  → Uses ROLLBACK to undo partial transactions

REAL-LIFE ANALOGY:
  A light switch — it's either ON or OFF. It cannot be "half-on."
  A transaction is either fully done or fully undone.

🎯 PYQ FACT: Atomicity = "All or Nothing" principle
🎯 PYQ FACT: If a transaction fails midway → Atomicity triggers ROLLBACK
```

---

### PROPERTY 2 — CONSISTENCY

```
DEFINITION: A transaction must bring the database from ONE VALID STATE
            to ANOTHER VALID STATE.
            The database must satisfy all defined integrity constraints
            BEFORE and AFTER the transaction.

"DATABASE RULES MUST ALWAYS BE SATISFIED"

EXAMPLE:
  Bank transfer rule: "Total money in system = constant"
  Before transaction: SBI ₹10,000 + PNB ₹5,000 = ₹15,000 total
  During transaction: SBI ₹5,000 + PNB ₹5,000 = ₹10,000 ← inconsistent (temporary!)
  After transaction:  SBI ₹5,000 + PNB ₹10,000 = ₹15,000 ← consistent ✅

  The temporary inconsistency DURING a transaction is allowed.
  But the FINAL state must be consistent.

WHAT DEFINES "VALID STATE"?
  → Integrity constraints (NOT NULL, PRIMARY KEY, FOREIGN KEY, CHECK)
  → Business rules defined by the application
  → Any violation = transaction aborted (rolled back)

REAL-LIFE ANALOGY:
  A jigsaw puzzle: each piece fits correctly at the start and end.
  Mid-puzzle, pieces can be out of place.
  But the FINAL picture must be correct.

🎯 PYQ FACT: Consistency = Valid state → Valid state (integrity constraints satisfied)
🎯 PYQ FACT: Consistency is ensured by both the DBMS AND the APPLICATION developer
```

---

### PROPERTY 3 — ISOLATION

```
DEFINITION: Concurrent (simultaneous) transactions execute as if they
            were running SERIALLY (one after another).
            Each transaction is ISOLATED from others — intermediate
            results of one transaction are NOT visible to other transactions.

"TRANSACTIONS DON'T INTERFERE WITH EACH OTHER"

THE PROBLEM WITHOUT ISOLATION (Lost Update Problem):
  Time │ Transaction T1 (reads balance = ₹1000, adds ₹500)
  ─────┼─────────────────────────────────────────────────
    1  │ T1 reads balance: ₹1000
    2  │         T2 reads balance: ₹1000
    3  │ T1 writes balance: ₹1500 (1000 + 500)
    4  │         T2 writes balance: ₹1200 (1000 + 200) ← OVERWRITES T1!
  
  Result: ₹200 added but ₹500 LOST! T1's update was overwritten.
  Isolation PREVENTS this by making T2 wait until T1 completes.

ISOLATION LEVELS (weaker to stronger):
  Read Uncommitted  → Can read UNCOMMITTED changes (dirty reads possible)
  Read Committed    → Can only read COMMITTED data (most DBMS default)
  Repeatable Read   → Same data read twice gives same result within transaction
  Serializable      → Strongest; transactions execute as if serial

HOW IS ISOLATION ACHIEVED?
  → Locks (shared locks, exclusive locks)
  → Timestamps (ordering transactions by time)
  → MVCC (Multi-Version Concurrency Control — used in PostgreSQL)

REAL-LIFE ANALOGY:
  Two chefs cooking from the same recipe book.
  Isolation means each chef reads their own copy — one chef changing
  the recipe mid-cook doesn't suddenly change what the other is making.

🎯 PYQ FACT: Isolation prevents "dirty reads" — reading uncommitted data
🎯 PYQ FACT: Concurrency problems solved by Isolation: Lost Update, Dirty Read, Phantom Read
```

---

### PROPERTY 4 — DURABILITY

```
DEFINITION: Once a transaction is COMMITTED, its changes are PERMANENT.
            They survive system failures (power cuts, crashes, errors).
            Committed data CANNOT be lost.

"COMMITTED = PERMANENT"

HOW IS DURABILITY ACHIEVED?
  → Write-Ahead Logging (WAL): changes written to LOG FILE before actual data
  → Transaction logs (journal): records what changes were made
  → Database backups and checkpoints

THE GUARANTEE:
  After COMMIT → even if server crashes immediately → data is SAFE
  On restart → DBMS recovers using the transaction log

REAL-LIFE ANALOGY:
  Once money is withdrawn from ATM and ATM prints receipt (COMMIT),
  the transaction is permanent. Even if the bank's system crashes
  right after, the withdrawal is still recorded and won't be reversed.

🎯 PYQ FACT: Durability = changes survive system failures after COMMIT
🎯 PYQ FACT: Durability achieved through: logs, WAL (Write-Ahead Logging)
```

---

### ACID Summary Table:

```
┌────────────────┬──────────────────────────────────────────────────────┬──────────────────────┐
│   PROPERTY     │   MEANING (One-line)                                  │   MECHANISM          │
├────────────────┼──────────────────────────────────────────────────────┼──────────────────────┤
│ Atomicity      │ ALL or NOTHING — no partial execution                 │ ROLLBACK on failure  │
├────────────────┼──────────────────────────────────────────────────────┼──────────────────────┤
│ Consistency    │ DB goes from valid state to valid state               │ Integrity constraints│
├────────────────┼──────────────────────────────────────────────────────┼──────────────────────┤
│ Isolation      │ Concurrent transactions don't interfere               │ Locks, Timestamps    │
├────────────────┼──────────────────────────────────────────────────────┼──────────────────────┤
│ Durability     │ Committed changes survive system failures             │ WAL, Transaction logs│
└────────────────┴──────────────────────────────────────────────────────┴──────────────────────┘
```

### 🎯 PYQ FACTS — ACID:
```
✅ ACID = Atomicity, Consistency, Isolation, Durability (in order)
✅ Atomicity = All or Nothing
✅ Consistency = Valid state → Valid state (integrity constraints hold)
✅ Isolation = Concurrent transactions isolated from each other
✅ Durability = Committed data survives crashes

🚨 TRAP: "Atomicity means transactions run simultaneously" → FALSE!
   Atomicity = All or Nothing execution (not about simultaneity — that's Isolation)
🚨 TRAP: "Isolation means one transaction at a time" → FALSE!
   Multiple transactions CAN run concurrently — Isolation just prevents interference.
🚨 TRAP: "ROLLBACK ensures Durability" → FALSE!
   ROLLBACK is the mechanism for Atomicity. Durability is via WAL/logs.
```

---

## 🔷 SECTION 3: COMMIT, ROLLBACK & SAVEPOINT

### Transaction Control Commands:

```
THERE ARE 3 KEY TCL (Transaction Control Language) COMMANDS:

1. COMMIT
2. ROLLBACK
3. SAVEPOINT
```

---

### COMMIT

```
DEFINITION: Permanently saves all changes made in the current transaction.
            After COMMIT, changes CANNOT be undone with ROLLBACK.

SYNTAX: COMMIT;

EXAMPLE:
  BEGIN TRANSACTION;
    UPDATE students SET marks = marks + 5 WHERE dept = 'CS';
    INSERT INTO results VALUES (101, 'Pass');
  COMMIT;   ← changes are now PERMANENT

THINK OF IT AS:
  Saving a document → Ctrl+S → the work is saved permanently.
  COMMIT = the database's "Save" button.

AFTER COMMIT:
  → Changes visible to all other users
  → Cannot be rolled back
  → Satisfies DURABILITY property
```

---

### ROLLBACK

```
DEFINITION: Undoes all changes made in the current transaction (since the
            last COMMIT or SAVEPOINT).
            Restores database to its state BEFORE the transaction began.

SYNTAX: ROLLBACK;

EXAMPLE:
  BEGIN TRANSACTION;
    DELETE FROM students WHERE dept = 'CS';  ← accidentally deleted!
    -- Oh no! That was wrong!
  ROLLBACK;   ← ALL rows restored, deletion undone ✅

THINK OF IT AS:
  Undo button (Ctrl+Z) for database operations.

WHEN IS ROLLBACK TRIGGERED?
  1. Explicitly: developer writes ROLLBACK;
  2. Implicitly: system failure / crash (DBMS auto-rolls back uncommitted work)
  3. Deadlock: DBMS picks a victim transaction to rollback

AFTER ROLLBACK:
  → Database is in the state it was before the transaction started
  → No changes committed
```

---

### SAVEPOINT

```
DEFINITION: Sets a NAMED CHECKPOINT within a transaction.
            Allows PARTIAL rollback — you can roll back to a savepoint
            without undoing the ENTIRE transaction.

SYNTAX:
  SAVEPOINT savepoint_name;
  ROLLBACK TO savepoint_name;
  RELEASE SAVEPOINT savepoint_name;  ← optional, removes savepoint

EXAMPLE — Why Savepoints Are Useful:
  BEGIN TRANSACTION;
    INSERT INTO orders VALUES (1, 'Laptop', 50000);    -- Step 1
    SAVEPOINT after_laptop;   ← CHECKPOINT SET
    
    INSERT INTO orders VALUES (2, 'Phone', 30000);     -- Step 2
    SAVEPOINT after_phone;    ← CHECKPOINT SET
    
    INSERT INTO orders VALUES (3, 'WRONG ITEM', -999); -- Step 3 → ERROR!
    
    ROLLBACK TO after_phone;  ← Undo Step 3 ONLY (go back to after_phone)
                              (Step 1 and Step 2 are still intact!)
  COMMIT;   ← commit the valid parts

WITHOUT SAVEPOINT: ROLLBACK would undo ALL 3 steps.
WITH SAVEPOINT: ROLLBACK TO rolls back only to the named checkpoint.

THINK OF IT AS:
  A video game checkpoint. If you die, you restart from the LAST CHECKPOINT
  not from the beginning of the level.

🎯 PYQ FACT: SAVEPOINT allows PARTIAL rollback within a transaction
🎯 PYQ FACT: ROLLBACK TO savepoint_name — restores to that specific point only
```

### TCL Commands Summary:

```
┌──────────────────┬─────────────────────────────────────────────────┐
│   COMMAND        │   WHAT IT DOES                                  │
├──────────────────┼─────────────────────────────────────────────────┤
│ COMMIT           │ Makes changes PERMANENT (cannot be undone)      │
├──────────────────┼─────────────────────────────────────────────────┤
│ ROLLBACK         │ UNDOES all changes since last COMMIT/SAVEPOINT  │
├──────────────────┼─────────────────────────────────────────────────┤
│ SAVEPOINT name   │ Sets a named CHECKPOINT within a transaction    │
├──────────────────┼─────────────────────────────────────────────────┤
│ ROLLBACK TO name │ Reverts to the named SAVEPOINT (partial rollback│
└──────────────────┴─────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 4: DELETE vs TRUNCATE vs DROP — The Most-Tested Comparison

This is one of the **most frequently tested** SQL topics. Know every difference.

```
COMPARISON TABLE:

┌──────────────────────┬─────────────────────────┬─────────────────────────┬─────────────────────────┐
│     FEATURE          │        DELETE           │       TRUNCATE          │         DROP            │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ SQL Category         │ DML                     │ DDL                     │ DDL                     │
│                      │ (Data Manipulation)     │ (Data Definition)       │ (Data Definition)       │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ What it removes      │ Specific rows (or all   │ ALL rows from table     │ Entire table (structure │
│                      │ rows if no WHERE clause)│                         │ + data + indexes)       │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Table structure      │ PRESERVED               │ PRESERVED               │ REMOVED (table gone!)   │
│                      │ (table still exists)    │ (table still exists)    │                         │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ WHERE clause         │ ✅ CAN use WHERE         │ ❌ CANNOT use WHERE      │ ❌ Not applicable        │
│                      │ (delete specific rows)  │ (removes ALL rows)      │                         │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ ROLLBACK possible?   │ ✅ YES — can be          │ ❌ NO — cannot be        │ ❌ NO — cannot be        │
│                      │ rolled back             │ rolled back (DDL)       │ rolled back (DDL)       │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Triggers fired?      │ ✅ YES — fires DELETE    │ ❌ NO — does not fire    │ ❌ NO                    │
│                      │ triggers                │ triggers                │                         │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Speed                │ SLOW (logs each row)    │ FAST (logs only pages)  │ FAST                    │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ AUTO_INCREMENT reset │ NOT reset               │ RESET to 1              │ Removed with table      │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Space released?      │ Not immediately         │ Releases space to OS    │ Releases all space      │
├──────────────────────┼─────────────────────────┼─────────────────────────┼─────────────────────────┤
│ Syntax example       │ DELETE FROM teaches;    │ TRUNCATE TABLE teaches; │ DROP TABLE teaches;     │
│                      │ DELETE FROM t WHERE     │                         │                         │
│                      │   id = 5;               │                         │                         │
└──────────────────────┴─────────────────────────┴─────────────────────────┴─────────────────────────┘
```

### Memory Trick — DELETE vs TRUNCATE vs DROP:

```
Think of a NOTEBOOK (= database TABLE):

DELETE = Using an ERASER to remove specific lines from the notebook
         → You can erase one line or all lines
         → Notebook still exists and has blank pages
         → If you make a mistake, you can re-write (rollback)

TRUNCATE = Tearing out ALL pages but keeping the notebook cover
           → All content gone instantly
           → Notebook (structure) still exists but empty
           → Cannot un-tear pages (no rollback)

DROP = Throwing the entire notebook IN THE DUSTBIN
       → Notebook is completely GONE (structure + content)
       → Cannot recover it (no rollback)
       → Have to buy a new notebook (create new table)
```

### PYQ-Confirmed Syntax:
```
✅ DELETE from relation: DELETE FROM teaches;    ← removes all rows from teaches
✅ To delete specific rows: DELETE FROM teaches WHERE course_id = 'CS101';
✅ TRUNCATE: TRUNCATE TABLE students;            ← removes all rows, faster
✅ DROP: DROP TABLE students;                    ← entire table is gone
```

### 🎯 PYQ FACTS:
```
✅ DELETE = DML → CAN be rolled back
✅ TRUNCATE = DDL → CANNOT be rolled back
✅ DROP = DDL → CANNOT be rolled back (table itself is deleted)
✅ DELETE can use WHERE; TRUNCATE cannot
✅ TRUNCATE fires NO triggers; DELETE DOES fire triggers
✅ TRUNCATE resets AUTO_INCREMENT; DELETE does not
🚨 TRAP: "TRUNCATE can be rolled back" → FALSE! TRUNCATE is DDL — no rollback.
🚨 TRAP: "DELETE removes the table structure" → FALSE! DELETE only removes rows.
🚨 TRAP: "DROP and TRUNCATE do the same thing" → FALSE! DROP removes the table entirely; TRUNCATE only empties it.
```

---

## 🔷 SECTION 5: Concurrency Control

### The Problem — What Happens Without It?

When multiple transactions run simultaneously, they can interfere with each other, causing:

```
CONCURRENCY PROBLEMS:

1. DIRTY READ (Read Uncommitted Data):
   T1 reads data that T2 has modified but NOT yet committed.
   If T2 rolls back → T1 has read "phantom" (never-existing) data.
   
   T1: reads account balance = ₹15,000 (T2 added ₹5000 but not yet committed)
   T2: ROLLBACK (balance should still be ₹10,000)
   T1 has wrong data → DIRTY READ
   
   Prevention: Don't allow reading uncommitted data (Isolation Level: Read Committed)

2. LOST UPDATE:
   Two transactions read the same value, then BOTH update it.
   One update OVERWRITES the other.
   
   T1: reads marks = 80, adds 5, writes 85
   T2: reads marks = 80 (same original value!), adds 10, writes 90
   Result: T1's update (85) is LOST — final value is 90 instead of 95
   
   Prevention: Locking (T1 locks the row; T2 must wait)

3. NON-REPEATABLE READ:
   T1 reads a value. T2 modifies+commits. T1 reads the same value again.
   The value is DIFFERENT on second read.
   
   Prevention: Repeatable Read isolation level

4. PHANTOM READ:
   T1 reads a set of rows matching a condition.
   T2 inserts new rows matching the SAME condition.
   T1 reads again → sees new "phantom" rows that weren't there before.
   
   Prevention: Serializable isolation level
```

### Solutions — How to Achieve Concurrency Control:

```
METHOD 1: LOCKING (Most common)

   SHARED LOCK (S-Lock / Read Lock):
   → Multiple transactions can hold shared lock simultaneously
   → Used when READING data
   → Other transactions can also READ but CANNOT write while S-lock held
   
   EXCLUSIVE LOCK (X-Lock / Write Lock):
   → Only ONE transaction can hold exclusive lock at a time
   → Used when WRITING (UPDATE, INSERT, DELETE) data
   → Other transactions CANNOT read or write while X-lock held
   
   LOCK COMPATIBILITY TABLE:
   ┌──────────────┬───────────┬─────────────┐
   │              │ S-Lock    │ X-Lock      │
   ├──────────────┼───────────┼─────────────┤
   │ S-Lock       │ Compatible│ Incompatible│
   │ (can share?) │ (both OK) │ (must wait) │
   ├──────────────┼───────────┼─────────────┤
   │ X-Lock       │Incompatible│Incompatible│
   │ (can share?) │ (must wait)│ (must wait)│
   └──────────────┴───────────┴─────────────┘
   
   Two-Phase Locking (2PL) Protocol:
   Phase 1 — GROWING: Transaction acquires locks (can only GET locks)
   Phase 2 — SHRINKING: Transaction releases locks (can only RELEASE locks)
   This guarantees SERIALIZABILITY.

METHOD 2: TIMESTAMP-BASED ORDERING
   → Each transaction gets a timestamp when it starts
   → Older transactions (smaller timestamp) get PRIORITY
   → Younger transactions conflicting with older → ROLLBACK and restart

METHOD 3: MVCC (Multi-Version Concurrency Control)
   → Each write creates a NEW VERSION of the data (instead of overwriting)
   → Readers see the version appropriate for their transaction start time
   → Writers don't block readers; readers don't block writers
   → Used by: PostgreSQL, Oracle, MySQL (InnoDB)

DEADLOCK:
   When two transactions WAIT FOR EACH OTHER to release locks:
   T1 holds Lock on A, waiting for Lock on B
   T2 holds Lock on B, waiting for Lock on A
   → DEADLOCK! Neither can proceed.
   
   DETECTION: DBMS detects cycle in wait-for graph
   RESOLUTION: DBMS selects a VICTIM transaction and ROLLS IT BACK

🎯 PYQ FACT: Concurrency control mechanisms: Locks, Timestamps, MVCC
🎯 PYQ FACT: Shared lock = multiple readers; Exclusive lock = one writer
🎯 PYQ FACT: Two-phase locking ensures serializability
🎯 PYQ FACT: Deadlock → DBMS detects and rolls back one victim transaction
```

---

## 🔷 SECTION 6: RAW Data Type

```
RAW DATA TYPE (Oracle SQL):
  → Stores BINARY data (raw bytes) — NOT interpreted as character data
  → Used for UNSTRUCTURED data (images, audio, fingerprints, binary files)
  → Variable length: RAW(n) where n = max bytes (up to 2000 bytes)
  → LONG RAW: stores up to 2 GB of unstructured binary data

COMPARISON:
  VARCHAR2  → stores character/text data (interpreted as text)
  NUMBER    → stores numeric data
  DATE      → stores date/time data
  RAW(n)    → stores RAW binary data (no interpretation)
  BLOB      → Binary Large Object (larger unstructured binary data)
  CLOB      → Character Large Object (large text data)

REAL-LIFE USE CASES FOR RAW:
  → Storing biometric fingerprint data
  → Storing encrypted passwords (raw bytes)
  → Storing small images or thumbnails

🎯 PYQ FACT: RAW data type stores UNSTRUCTURED (raw binary) data
🎯 PYQ FACT: RAW ≠ VARCHAR (VARCHAR stores text/characters; RAW stores binary bytes)
```

---

## 🔷 SECTION 7: SQL Constraints — Complete Guide

### What Are Constraints?

Constraints are **rules enforced on columns** to ensure data integrity.

```
┌─────────────────────┬──────────────────────────────────────────────────────────────────┐
│   CONSTRAINT        │   WHAT IT DOES                                                   │
├─────────────────────┼──────────────────────────────────────────────────────────────────┤
│ PRIMARY KEY         │ Uniquely identifies EACH ROW; cannot be NULL; only 1 per table  │
├─────────────────────┼──────────────────────────────────────────────────────────────────┤
│ FOREIGN KEY         │ Links to PRIMARY KEY of another table; enforces referential      │
│                     │ integrity (no orphan records)                                    │
├─────────────────────┼──────────────────────────────────────────────────────────────────┤
│ UNIQUE              │ All values in column must be UNIQUE; can have multiple per table;│
│                     │ UNLIKE primary key, can allow ONE NULL value                     │
├─────────────────────┼──────────────────────────────────────────────────────────────────┤
│ NOT NULL            │ Column CANNOT contain NULL values; value must always be provided │
├─────────────────────┼──────────────────────────────────────────────────────────────────┤
│ CHECK               │ Validates that values in column satisfy a specific condition     │
│                     │ e.g., CHECK (age >= 18) — no one under 18 can be inserted       │
├─────────────────────┼──────────────────────────────────────────────────────────────────┤
│ DEFAULT             │ Provides a default value when no value is specified during INSERT│
└─────────────────────┴──────────────────────────────────────────────────────────────────┘
```

### PRIMARY KEY vs UNIQUE:

```
FEATURE          │ PRIMARY KEY           │ UNIQUE
─────────────────┼───────────────────────┼──────────────────────────
NULL allowed?    │ NO — never NULL       │ YES — can be NULL (once)
Number per table │ Only ONE              │ Can have MULTIPLE
Clustered index? │ Creates clustered     │ Creates non-clustered
                 │ index (usually)       │ index
Purpose          │ Main identifier of row│ Ensure uniqueness (not main ID)

🚨 TRAP: "PRIMARY KEY and UNIQUE are identical" → FALSE!
   Primary Key: NO nulls, only ONE per table.
   UNIQUE: allows one NULL, can have multiple per table.
```

### What is NOT a Constraint?

```
CONFIRMED PYQ TRAP:
  UNION = NOT a constraint! UNION is a SET OPERATION (combines query results)
  
  VALID CONSTRAINTS: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, CHECK, DEFAULT
  NOT CONSTRAINTS: UNION, SELECT, JOIN, ORDER BY, GROUP BY
```

### SQL Constraint Syntax:

```sql
-- Column-level constraints
CREATE TABLE students (
    s_id     INT          PRIMARY KEY,          -- PRIMARY KEY
    email    VARCHAR(50)  UNIQUE,               -- UNIQUE
    name     VARCHAR(100) NOT NULL,             -- NOT NULL
    age      INT          CHECK (age >= 18),    -- CHECK
    grade    CHAR(1)      DEFAULT 'B',          -- DEFAULT
    dept_id  INT          REFERENCES dept(d_id) -- FOREIGN KEY
);
```

---

## 🔷 SECTION 8: SQL Command Categories — DML, DDL, DCL, TCL

```
┌────────────┬──────────────────────────────────┬────────────────────────────────────────────┐
│  CATEGORY  │          FULL FORM               │   COMMANDS INCLUDED                        │
├────────────┼──────────────────────────────────┼────────────────────────────────────────────┤
│ DDL        │ Data Definition Language         │ CREATE, ALTER, DROP, TRUNCATE, RENAME      │
│            │ (defines structure)              │ → Auto COMMIT (cannot be rolled back)      │
├────────────┼──────────────────────────────────┼────────────────────────────────────────────┤
│ DML        │ Data Manipulation Language       │ SELECT, INSERT, UPDATE, DELETE             │
│            │ (manipulates data)               │ → Can be rolled back (except SELECT)       │
├────────────┼──────────────────────────────────┼────────────────────────────────────────────┤
│ DCL        │ Data Control Language            │ GRANT, REVOKE                              │
│            │ (controls access)                │ → Manages permissions                      │
├────────────┼──────────────────────────────────┼────────────────────────────────────────────┤
│ TCL        │ Transaction Control Language     │ COMMIT, ROLLBACK, SAVEPOINT                │
│            │ (manages transactions)           │ → Controls transaction lifecycle           │
└────────────┴──────────────────────────────────┴────────────────────────────────────────────┘

IMPORTANT DISTINCTION:
  DDL commands = AUTO-COMMIT (implicit commit; cannot rollback!)
  DML commands = Part of explicit transaction; can rollback
  
  That's why TRUNCATE (DDL) cannot be rolled back,
  but DELETE (DML) can be rolled back.

🎯 PYQ FACT: DDL = auto-commit; DML = explicit transaction
🎯 PYQ FACT: TRUNCATE is DDL; DELETE is DML (hence rollback difference)
```

---

## 🔷 SECTION 9: Complete PYQ Trap List — SQL Transactions

```
🚨 TRAP 1: "Atomicity means transactions run at the same time" → FALSE!
   Atomicity = ALL or NOTHING execution (one transaction, not about simultaneity).

🚨 TRAP 2: "ROLLBACK ensures Durability" → FALSE!
   ROLLBACK is the mechanism for Atomicity. Durability = WAL/logs.

🚨 TRAP 3: "TRUNCATE can be rolled back using ROLLBACK" → FALSE!
   TRUNCATE is DDL — it auto-commits and CANNOT be rolled back.

🚨 TRAP 4: "DELETE removes the table structure" → FALSE!
   DELETE removes ROWS only. Table structure remains. DROP removes structure.

🚨 TRAP 5: "TRUNCATE fires triggers" → FALSE!
   TRUNCATE does NOT fire triggers. DELETE fires triggers.

🚨 TRAP 6: "UNION is a SQL constraint" → FALSE!
   UNION is a set operation. Constraints = PRIMARY KEY, NOT NULL, CHECK, UNIQUE, FK.

🚨 TRAP 7: "PRIMARY KEY allows one NULL value" → FALSE!
   PRIMARY KEY: NEVER NULL. UNIQUE constraint can allow ONE NULL.

🚨 TRAP 8: "Multiple PRIMARY KEYs can exist in one table" → FALSE!
   A table has only ONE PRIMARY KEY (may be composite — multiple columns — but
   it is still ONE primary key constraint).

🚨 TRAP 9: "SAVEPOINT permanently saves data" → FALSE!
   SAVEPOINT only sets a checkpoint WITHIN a transaction.
   Only COMMIT permanently saves data.

🚨 TRAP 10: "Concurrency problems are caused only by hardware failures" → FALSE!
   Concurrency problems (dirty read, lost update) are caused by
   multiple TRANSACTIONS running simultaneously.

🚨 TRAP 11: "RAW data type stores text data" → FALSE!
   RAW stores UNSTRUCTURED BINARY data (not text — that's VARCHAR/CHAR).

🚨 TRAP 12: "Isolation means one transaction at a time" → FALSE!
   Multiple transactions CAN run concurrently — Isolation prevents interference.
```

---

# PART 2: GENERAL STUDIES
## 🚀 Current Affairs — Space Technology (India's Space Programme)

---

## 🔷 SECTION 1: ISRO Overview

```
ISRO = Indian Space Research Organisation
Founded: 1969 (15 August 1969)
Headquarters: Bengaluru (Bangalore), Karnataka
Chairman (as of 2024): S. Somanath (V. Narayanan appointed Jan 2025)
Parent Ministry: Department of Space (directly under Prime Minister)

LAUNCH CENTRES:
  SHAR (Satish Dhawan Space Centre): Sriharikota, Andhra Pradesh
    → Primary rocket launch centre
    → Location: Pulicate Lake region, east coast of India
  
  VSSC (Vikram Sarabhai Space Centre): Thiruvananthapuram, Kerala
    → Develops launch vehicles (rockets)
  
  SAC (Space Applications Centre): Ahmedabad, Gujarat
    → Develops satellite payloads and applications

FOUNDING FATHER OF INDIAN SPACE PROGRAMME:
  Dr. Vikram Sarabhai (the "Father of Indian Space Programme")
  First ISRO Chairman: Dr. Vikram Sarabhai

🎯 PYQ FACT: ISRO founded in 1969
🎯 PYQ FACT: HQ: Bengaluru | Launch site: Sriharikota (SHAR)
🎯 PYQ FACT: Father of Indian Space Programme = Dr. Vikram Sarabhai
```

---

## 🔷 SECTION 2: Chandrayaan Missions

```
CHANDRAYAAN-1 (2008):
  Launch date: October 22, 2008
  Rocket: PSLV-C11
  Achievement:
  → Discovered evidence of WATER MOLECULES on the Moon's surface
  → First Indian mission to the Moon
  → Confirmed by NASA's Moon Mineralogy Mapper (M3) instrument on board
  
  🎯 KEY FACT: Chandrayaan-1 = Discovery of water on Moon

─────────────────────────────────────────────────────────────────────

CHANDRAYAAN-2 (2019):
  Launch date: July 22, 2019
  Rocket: GSLV Mk-III (LVM3)
  Components: Orbiter + Vikram Lander + Pragyan Rover
  
  What happened:
  → Orbiter successfully deployed and is STILL operational
  → Vikram lander's hard landing (crash-landed) on Sep 7, 2019
    (lost communication 2.1 km above surface)
  → Could not achieve soft landing
  
  Achievement:
  → Orbiter still sending valuable data
  → Precise South Pole mapping
  
  🎯 KEY FACT: Chandrayaan-2 = Vikram lander CRASH-LANDED (soft landing failed)

─────────────────────────────────────────────────────────────────────

CHANDRAYAAN-3 (2023): ← 🎯 MOST IMPORTANT FOR EXAM
  Launch date: July 14, 2023
  Landing date: August 23, 2023
  Rocket: LVM3-M4 (GSLV Mk-III)
  Components: Propulsion Module + Vikram Lander + Pragyan Rover
  
  Landing site: Near Moon's South Pole
    Shiv Shakti Point (PM Modi named it)
  
  Crash site of Chandrayaan-2: Named "Tiranga Point" (by ISRO)
  
  ACHIEVEMENTS:
  → India = FIRST country to soft-land near the Moon's South Pole ✅
  → India = FOURTH country overall to achieve soft landing on Moon
    (After USA, USSR/Russia, China)
  → Pragyan rover operated for ~14 Earth days (one lunar day)
  → Confirmed presence of Sulphur, Oxygen, Iron, Titanium and other
    elements near the south pole
  
  Mission duration: 14 days (Vikram lander + Pragyan rover operational
  for one lunar day = ~14 Earth days)
  
  🎯 KEY FACT: India = FIRST to land near Moon's South Pole (Chandrayaan-3)
  🎯 KEY FACT: Landing on August 23, 2023 (National Space Day declared)
  🎯 KEY FACT: Landing site = Shiv Shakti Point
  🎯 KEY FACT: Chandrayaan-2 crash site = Tiranga Point
  🎯 KEY FACT: India = 4th country to soft-land on Moon

NATIONAL SPACE DAY:
  → August 23 declared as National Space Day by PM Modi
  → To commemorate Chandrayaan-3 landing date
```

---

## 🔷 SECTION 3: Aditya-L1 Mission (Sun Mission)

```
MISSION NAME: Aditya-L1
Launch date: September 2, 2023
Rocket: PSLV-C57
Destination: Lagrange Point 1 (L1) between Earth and Sun

WHAT IS LAGRANGE POINT L1?
  → A point in space where gravitational forces of Earth and Sun balance
  → About 1.5 million km from Earth (1% of Earth-Sun distance)
  → Object placed here stays stable — doesn't fall towards Earth or Sun
  → Ideal for studying the Sun CONTINUOUSLY (no eclipses!)
  
  ┌───────────────────────────────────────────────────────────────────────┐
  │   SUN           L1 point          EARTH                              │
  │    ☀️ ──────────── 🛸 ──────────────── 🌍                             │
  │         (1.5 million km)   (148.5 million km)                        │
  └───────────────────────────────────────────────────────────────────────┘

L1 arrival: January 6, 2024 (successfully reached L1 halo orbit)

PURPOSE:
  → Study the Sun — especially solar corona, solar wind, solar flares
  → Understand space weather and its effect on Earth
  → Study the magnetic field of the Sun

PAYLOADS (7 instruments on board):
  Most important:
  → VELC (Visible Emission Line Coronagraph) — studies solar corona
  → SUIT (Solar Ultraviolet Imaging Telescope)
  → ASPEX (Aditya Solar Wind Particle Experiment)

WHY "ADITYA"?
  → "Aditya" = Sanskrit word for the Sun

🎯 KEY FACTS:
  ✅ Aditya-L1 = India's FIRST space-based solar observatory
  ✅ Destination = L1 Lagrange Point (1.5 million km from Earth)
  ✅ Launched September 2, 2023 (just 10 days after Chandrayaan-3 landing)
  ✅ Reached L1 orbit: January 6, 2024
  ✅ Studies: Solar corona, solar wind, solar flares
  
🚨 TRAP: "Aditya-L1 lands on the Sun" → FALSE! It orbits the L1 Lagrange point.
🚨 TRAP: "Aditya-L1 went to L2 (beyond Earth)" → FALSE! L1 = between Earth and Sun.
```

---

## 🔷 SECTION 4: Gaganyaan Mission (India's First Crewed Mission)

```
MISSION NAME: Gaganyaan
Purpose: India's FIRST Human Spaceflight Mission
Objective: Send 3 Indian astronauts (Vyomanauts) to Low Earth Orbit (LEO)
Target orbit: 400 km above Earth
Mission duration: 3 days (72 hours)

"VYOMANAUT" = Indian term for astronaut (from Sanskrit "Vyoma" = space)

GAGANYAAN MILESTONES:
  
  Test Flight 1 (TV-D1): October 21, 2023
  → Tested the Crew Escape System (CES)
  → Successful — the escape system would save astronauts if rocket fails
  → Crew Module separated and recovered from Bay of Bengal
  
  G1 Mission (Unmanned): Planned 2024–25
  → First unmanned test flight with crew module
  
  G2 Mission (Vyommitra robot): Planned 2025
  → "Vyommitra" = Female humanoid robot (half-body)
  → Will test life support systems, communicate, operate switches
  
  G3 Mission (Crewed): Target 2026–27
  → First Indian humans in space

THE FOUR ASTRONAUTS SELECTED:
  (Indian Air Force test pilots — all Gaganyaan candidates):
  1. Group Captain Prashanth Balakrishnan Nair
  2. Group Captain Ajit Krishnan
  3. Group Captain Angad Pratap
  4. Wing Commander Shubhanshu Shukla

VYOMMITRA:
  → Half-humanoid robot developed by ISRO
  → Will precede human crew in space
  → Can speak, recognize people, switch panels, carry out science experiments

ROCKET USED: LVM3 (GSLV Mk-III / renamed as Launch Vehicle Mark-3)

🎯 KEY FACTS:
  ✅ Gaganyaan = India's FIRST crewed (human spaceflight) mission
  ✅ Indian astronauts called VYOMANAUTS
  ✅ Vyommitra = ISRO's female humanoid robot for Gaganyaan
  ✅ LVM3 / GSLV Mk-III rocket used
  ✅ Target orbit = 400 km above Earth
  ✅ Mission duration = 3 days

🚨 TRAP: "India has already sent humans to space via Gaganyaan" → NOT YET (as of 2024)
   Gaganyaan's crewed mission is still upcoming.
🚨 TRAP: "Vyommitra is a male robot" → FALSE! Vyommitra is a FEMALE humanoid.
```

---

## 🔷 SECTION 5: Other Important ISRO Missions

```
MANGALYAAN (Mars Orbiter Mission — MOM):
  Launch: November 5, 2013
  Mars orbit insertion: September 24, 2014
  
  RECORDS:
  → India = FIRST Asian country to reach Mars
  → FIRST country to succeed in its FIRST attempt to Mars
  → Most COST-EFFECTIVE Mars mission: ₹450 crore (~$74 million)
    (cheaper than Hollywood movie "Gravity"!)
  
  Status: Lost contact September 2022 (end of mission after 8 years)
  
  🎯 KEY FACT: India = first Asian country to Mars (and first attempt success)

──────────────────────────────────────────────────────────────────────

PSLV (Polar Satellite Launch Vehicle):
  → Workhorse rocket of ISRO — most reliable launch vehicle
  → Used for launching satellites into polar and sun-synchronous orbits
  → PSLV-C37 (2017): Launched 104 satellites in ONE go → World record!
  
  🎯 KEY FACT: PSLV = ISRO's workhorse rocket; PSLV-C37 = 104 satellites (record)

──────────────────────────────────────────────────────────────────────

GSLV Mk-III / LVM3:
  → Heaviest rocket of ISRO
  → Used for geosynchronous satellites and Chandrayaan-3, Gaganyaan
  → Can carry 4,000 kg to GTO or 10,000 kg to LEO
  
  🎯 KEY FACT: LVM3/GSLV Mk-III = heaviest ISRO rocket

──────────────────────────────────────────────────────────────────────

ONE WEB SATELLITE LAUNCHES:
  → ISRO launched OneWeb satellites (UK company) on LVM3
  → Commercial launch success — ISRO as a commercial launch provider

──────────────────────────────────────────────────────────────────────

REUSABLE LAUNCH VEHICLE (RLV-TD):
  → India's step towards reusable rockets (like SpaceX Falcon 9)
  → Technology Demonstrator tests conducted
  → First successful RLV landing: April 2023 (RLV-LEX experiment)
  
  🎯 KEY FACT: RLV = India's reusable rocket technology demonstrator
```

---

## 🔷 SECTION 6: Global Space — Key Facts for BPSC

```
FIRST IN SPACE (Global):
  → First human in space: Yuri Gagarin (USSR, April 12, 1961)
  → First man on Moon: Neil Armstrong (USA, July 20, 1969) — Apollo 11
  → First woman in space: Valentina Tereshkova (USSR, 1963)
  → First Indian in space: Rakesh Sharma (1984, Soyuz T-11, USSR mission)
    Quote: "Sare Jahan Se Achha" (when asked how India looked from space)

RECENT GLOBAL MISSIONS:
  → NASA Artemis II (planned): First crewed Moon flyby since Apollo 17 (1972)
  → SpaceX Starship: World's most powerful rocket (Elon Musk / SpaceX)
  → China: Tiangong Space Station, Chang'e Moon missions, Zhurong Mars rover
  → James Webb Space Telescope (JWST): Launched Dec 25, 2021 — observes early universe

SPACE AGENCIES:
  → NASA: USA — National Aeronautics and Space Administration
  → ESA: European Space Agency
  → Roscosmos: Russia
  → CNSA: China National Space Administration
  → JAXA: Japan Aerospace Exploration Agency
  → ISRO: India

🎯 KEY FACT: First Indian in space = Rakesh Sharma (1984)
🎯 KEY FACT: Rakesh Sharma's quote = "Sare Jahan Se Achha" (when asked about India from space)
🎯 KEY FACT: James Webb Space Telescope launched Dec 25, 2021
🎯 KEY FACT: Yuri Gagarin = first human in space (April 12, 1961)
```

---

## 🔷 SECTION 7: Space Technology PYQ Traps

```
🚨 TRAP 1: "Chandrayaan-3 was the first mission to land on the Moon" → FALSE!
   First Moon landing = Apollo 11, USA (July 1969).
   Chandrayaan-3 = First to land near the SOUTH POLE specifically.

🚨 TRAP 2: "India was the first country to land on the Moon" → FALSE!
   USA (1969) was first. India is 4th. China, Russia also preceded India.

🚨 TRAP 3: "Aditya-L1 mission is to land on the Sun" → FALSE!
   Aditya-L1 orbits L1 Lagrange Point (1.5 million km from Earth) — doesn't land anywhere.

🚨 TRAP 4: "Gaganyaan has already sent humans to space" → FALSE!
   Gaganyaan crewed mission is still upcoming (as of 2024); only test flights done.

🚨 TRAP 5: "PSLV is India's heaviest rocket" → FALSE!
   Heaviest = LVM3/GSLV Mk-III. PSLV is most reliable/workhorse.

🚨 TRAP 6: "Rakesh Sharma was the first Asian in space" → FALSE!
   Rakesh Sharma was first INDIAN in space (1984), but several Asians had gone before.

🚨 TRAP 7: "Mangalyaan is still operational" → FALSE!
   Mangalyaan lost contact in September 2022 after 8 successful years.

🚨 TRAP 8: "Chandrayaan-1 confirmed the presence of Sulphur on Moon" → FALSE!
   Chandrayaan-1 = discovered water molecules.
   Chandrayaan-3 (Pragyan rover) = detected Sulphur, Oxygen near south pole.

🚨 TRAP 9: "ISRO was founded in 1972" → FALSE!
   ISRO founded: August 15, 1969. 1972 is unrelated.

🚨 TRAP 10: "The National Space Day of India is July 14" → FALSE!
   July 14 = Chandrayaan-3 launch date.
   National Space Day = August 23 (Chandrayaan-3 LANDING date).
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: ACID Properties, Transactions, COMMIT/ROLLBACK/SAVEPOINT, DELETE/TRUNCATE/DROP, Concurrency, Constraints

---

**Q1.** The ACID property that ensures a transaction is treated as a single indivisible unit (either fully executes or fully undoes) is:
(A) Consistency
(B) Isolation
(C) Atomicity
(D) More than one of the above
(E) None of the above

---

**Q2.** Which ACID property ensures that a committed transaction's changes survive system failures such as power cuts?
(A) Atomicity
(B) Consistency
(C) Durability
(D) More than one of the above
(E) None of the above

---

**Q3.** The ACID property that ensures multiple concurrent transactions execute as if they were running one at a time (no interference) is:
(A) Atomicity
(B) Isolation
(C) Durability
(D) More than one of the above
(E) None of the above

---

**Q4.** Which mechanism is primarily used to ensure DURABILITY in a DBMS?
(A) ROLLBACK and COMMIT commands only
(B) Write-Ahead Logging (WAL) and transaction logs
(C) Two-phase locking protocol
(D) More than one of the above
(E) None of the above

---

**Q5.** A transaction is in the process of executing its operations. At this point, the transaction is in which state?
(A) Committed
(B) Partially Committed
(C) Active
(D) More than one of the above
(E) None of the above

---

**Q6.** The SQL command that makes all changes made in the current transaction PERMANENT is:
(A) SAVEPOINT
(B) ROLLBACK
(C) COMMIT
(D) More than one of the above
(E) None of the above

---

**Q7.** A developer accidentally deletes all rows from a critical table. Which SQL command can recover the data IF no COMMIT has been issued?
(A) TRUNCATE
(B) ROLLBACK
(C) DROP
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following correctly describes the purpose of SAVEPOINT in SQL transactions?
(A) It permanently saves the transaction to disk like COMMIT
(B) It creates a named checkpoint within a transaction, allowing PARTIAL rollback to that point
(C) It ends the current transaction and starts a new one
(D) More than one of the above
(E) None of the above

---

**Q9.** Consider this sequence: BEGIN TRANSACTION → DELETE rows → SAVEPOINT sp1 → INSERT rows → Error occurs. Which command should be used to undo ONLY the INSERT (not the DELETE)?
(A) ROLLBACK (full rollback)
(B) ROLLBACK TO sp1
(C) COMMIT
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is a DDL (Data Definition Language) command?
(A) DELETE
(B) INSERT
(C) TRUNCATE
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following correctly compares DELETE and TRUNCATE?
(A) Both DELETE and TRUNCATE can be rolled back using ROLLBACK
(B) DELETE is DML (can rollback); TRUNCATE is DDL (cannot rollback)
(C) TRUNCATE fires DELETE triggers; DELETE does not
(D) More than one of the above
(E) None of the above

---

**Q12.** Which SQL command removes BOTH the data AND the entire table structure (columns, indexes, constraints)?
(A) DELETE FROM table_name
(B) TRUNCATE TABLE table_name
(C) DROP TABLE table_name
(D) More than one of the above
(E) None of the above

---

**Q13.** The difference between TRUNCATE and DELETE when both are used WITHOUT a WHERE clause is:
(A) They are functionally identical in all ways
(B) TRUNCATE cannot be rolled back and is faster; DELETE can be rolled back and is slower
(C) DELETE removes the table structure; TRUNCATE only removes data
(D) More than one of the above
(E) None of the above

---

**Q14.** Which concurrency problem occurs when Transaction T1 reads data modified (but not yet committed) by Transaction T2, and T2 then performs a ROLLBACK?
(A) Lost Update
(B) Dirty Read
(C) Phantom Read
(D) More than one of the above
(E) None of the above

---

**Q15.** In concurrency control, a SHARED LOCK allows:
(A) Only one transaction to read the data; all others are blocked
(B) Multiple transactions to read simultaneously, but no transaction can write
(C) One transaction to write and others to read concurrently
(D) More than one of the above
(E) None of the above

---

**Q16.** The Two-Phase Locking (2PL) protocol consists of which two phases?
(A) Read Phase and Write Phase
(B) Growing Phase (acquiring locks) and Shrinking Phase (releasing locks)
(C) Active Phase and Committed Phase
(D) More than one of the above
(E) None of the above

---

**Q17.** When two transactions are each waiting for the other to release a lock, this situation is called:
(A) Starvation
(B) Thrashing
(C) Deadlock
(D) More than one of the above
(E) None of the above

---

**Q18.** The RAW data type in Oracle SQL is used to store:
(A) Plain text data like names and addresses
(B) Numerical data for calculations
(C) Unstructured binary data (raw bytes)
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is NOT a valid SQL constraint?
(A) PRIMARY KEY
(B) NOT NULL
(C) UNION
(D) More than one of the above
(E) None of the above

---

**Q20.** Difference between PRIMARY KEY and UNIQUE constraint:
(A) Both allow NULL values; PRIMARY KEY allows more
(B) PRIMARY KEY: no NULL allowed, only one per table; UNIQUE: allows one NULL, multiple per table
(C) Both are identical — they have no differences
(D) More than one of the above
(E) None of the above

---

**Q21.** The FOREIGN KEY constraint in SQL enforces:
(A) That the column values are unique within the table
(B) That the column values reference existing values in the PRIMARY KEY of another table
(C) That the column cannot contain NULL values
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following SQL command categories includes COMMIT, ROLLBACK, and SAVEPOINT?
(A) DDL (Data Definition Language)
(B) DML (Data Manipulation Language)
(C) TCL (Transaction Control Language)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which ACID property ensures that the database moves from one VALID state to another VALID state, satisfying all integrity constraints?
(A) Atomicity
(B) Consistency
(C) Isolation
(D) More than one of the above
(E) None of the above

---

**Q24.** Consider: A transaction executes all its operations successfully and is about to write changes to disk. This state is called:
(A) Active
(B) Committed
(C) Partially Committed
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following about the TRUNCATE command is CORRECT?
(A) It can remove specific rows using a WHERE clause
(B) It fires DELETE triggers
(C) It resets AUTO_INCREMENT counter and cannot be rolled back
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: ISRO, Chandrayaan, Aditya-L1, Gaganyaan, Space Milestones

---

**Q26.** ISRO (Indian Space Research Organisation) was founded in:
(A) 1962
(B) 1969
(C) 1975
(D) More than one of the above
(E) None of the above

---

**Q27.** The headquarters of ISRO is located in:
(A) New Delhi
(B) Hyderabad
(C) Bengaluru (Bangalore)
(D) More than one of the above
(E) None of the above

---

**Q28.** India's primary rocket launch centre (SHAR) is located at:
(A) Thumba, Kerala
(B) Sriharikota, Andhra Pradesh
(C) Chandipur, Odisha
(D) More than one of the above
(E) None of the above

---

**Q29.** The "Father of the Indian Space Programme" is:
(A) A.P.J. Abdul Kalam
(B) Vikram Sarabhai
(C) Satish Dhawan
(D) More than one of the above
(E) None of the above

---

**Q30.** Chandrayaan-1 (2008) made a significant discovery — it confirmed:
(A) Presence of Sulphur near the Moon's South Pole
(B) Presence of water molecules on the Moon's surface
(C) The Moon has a liquid iron core
(D) More than one of the above
(E) None of the above

---

**Q31.** India's Chandrayaan-3 successfully soft-landed on the Moon on:
(A) July 14, 2023
(B) August 23, 2023
(C) September 2, 2023
(D) More than one of the above
(E) None of the above

---

**Q32.** With Chandrayaan-3's successful landing, India became:
(A) The first country to land on the Moon
(B) The first country to land near the Moon's South Pole
(C) The second country to land on the Moon (after the USA)
(D) More than one of the above
(E) None of the above

---

**Q33.** The landing site of Chandrayaan-3 was named:
(A) Tiranga Point
(B) Vikram Point
(C) Shiv Shakti Point
(D) More than one of the above
(E) None of the above

---

**Q34.** The Government of India declared August 23 as National Space Day to commemorate:
(A) The launch of Chandrayaan-3
(B) The landing of Chandrayaan-3 on the Moon
(C) The founding of ISRO
(D) More than one of the above
(E) None of the above

---

**Q35.** India's Aditya-L1 mission was launched to study:
(A) Mars and its atmosphere
(B) The Sun — particularly its corona, solar wind, and flares
(C) The Moon's South Pole permanently shadowed craters
(D) More than one of the above
(E) None of the above

---

**Q36.** Aditya-L1 was placed at which Lagrange point?
(A) L2 (beyond Earth, away from Sun)
(B) L4 (stable triangular point)
(C) L1 (between Earth and Sun, ~1.5 million km from Earth)
(D) More than one of the above
(E) None of the above

---

**Q37.** Aditya-L1 was launched on:
(A) August 23, 2023
(B) September 2, 2023
(C) January 6, 2024
(D) More than one of the above
(E) None of the above

---

**Q38.** India's first human spaceflight mission is called:
(A) Mangalyaan
(B) Shukrayaan
(C) Gaganyaan
(D) More than one of the above
(E) None of the above

---

**Q39.** Indian astronauts under the Gaganyaan programme are called:
(A) Cosmonauts
(B) Astronauts
(C) Vyomanauts
(D) More than one of the above
(E) None of the above

---

**Q40.** "Vyommitra" associated with India's Gaganyaan mission is:
(A) A male humanoid robot
(B) A female humanoid robot to precede human crew in Gaganyaan
(C) The name of the crewed spacecraft
(D) More than one of the above
(E) None of the above

---

**Q41.** India's Mars Orbiter Mission (Mangalyaan) was significant because India was:
(A) The first country to reach Mars (before USA and Russia)
(B) The first Asian country to reach Mars and the first country to succeed in its first attempt
(C) The first country to land a rover on Mars
(D) More than one of the above
(E) None of the above

---

**Q42.** PSLV-C37 set a world record in 2017 by launching:
(A) The heaviest single satellite ever
(B) 104 satellites in a single mission
(C) India's first astronaut into orbit
(D) More than one of the above
(E) None of the above

---

**Q43.** The first Indian to travel to space was:
(A) A.P.J. Abdul Kalam
(B) Kalpana Chawla
(C) Rakesh Sharma (1984, aboard Soyuz T-11)
(D) More than one of the above
(E) None of the above

---

**Q44.** When asked how India looks from space, Rakesh Sharma famously replied:
(A) "Jai Hind"
(B) "Sare Jahan Se Achha"
(C) "India is a shining star"
(D) More than one of the above
(E) None of the above

---

**Q45.** The GSLV Mk-III (renamed LVM3) is significant in ISRO's fleet because:
(A) It is ISRO's lightest and smallest rocket
(B) It is ISRO's heaviest and most powerful launch vehicle
(C) It is exclusively used for planetary missions
(D) More than one of the above
(E) None of the above

---

**Q46.** The Chandrayaan-3 mission's Pragyan rover detected the presence of which element near the Moon's South Pole (for the FIRST time by in-situ analysis)?
(A) Gold and Silver
(B) Hydrogen and Helium
(C) Sulphur (along with Oxygen, Iron, and other elements)
(D) More than one of the above
(E) None of the above

---

**Q47.** India's Mangalyaan (Mars Orbiter Mission) lost contact with ISRO in:
(A) 2017 after 3 years of operation
(B) 2020 due to fuel exhaustion
(C) 2022 after 8 years of successful operation
(D) More than one of the above
(E) None of the above

---

**Q48.** The James Webb Space Telescope (JWST), launched on December 25, 2021, is primarily designed to:
(A) Monitor Earth's climate and weather systems
(B) Observe the early universe and distant galaxies in infrared light
(C) Track near-Earth asteroids and comets
(D) More than one of the above
(E) None of the above

---

**Q49.** The crash site of Chandrayaan-2's Vikram lander on the Moon was named:
(A) Shiv Shakti Point
(B) Tiranga Point
(C) Vikram Valley
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following statements about India's space milestones is/are CORRECT?
I. Chandrayaan-3 = first landing near Moon's South Pole
II. Aditya-L1 = India's first space-based solar observatory
III. PSLV-C37 = launched 104 satellites in one mission (world record in 2017)
IV. Rakesh Sharma = first Indian in space (1984)

(A) I and II only
(B) I, II, and III only
(C) All of I, II, III, and IV are correct
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (C) | Atomicity = All or Nothing — single indivisible unit |
| 2  | (C) | Durability = committed changes survive system failures |
| 3  | (B) | Isolation = concurrent transactions don't interfere with each other |
| 4  | (B) | Durability achieved by WAL (Write-Ahead Logging) and transaction logs |
| 5  | (C) | Active state = transaction is executing its operations |
| 6  | (C) | COMMIT = makes changes permanent |
| 7  | (B) | ROLLBACK = undoes uncommitted changes (works only before COMMIT) |
| 8  | (B) | SAVEPOINT = named checkpoint within transaction; allows partial rollback |
| 9  | (B) | ROLLBACK TO sp1 = undo only operations after sp1 (keeps DELETE) |
| 10 | (C) | TRUNCATE is DDL; DELETE and INSERT are DML |
| 11 | (B) | DELETE = DML (rollback possible); TRUNCATE = DDL (no rollback) |
| 12 | (C) | DROP TABLE = removes structure + all data + indexes (completely gone) |
| 13 | (B) | TRUNCATE: no rollback, faster, resets AUTO_INCREMENT; DELETE: rollback possible, slower |
| 14 | (B) | Dirty Read = reading uncommitted (then rolled back) data |
| 15 | (B) | Shared lock = multiple readers allowed; NO writer allowed simultaneously |
| 16 | (B) | 2PL: Growing phase (acquire locks) + Shrinking phase (release locks) |
| 17 | (C) | Deadlock = circular wait between transactions for each other's locks |
| 18 | (C) | RAW data type = stores unstructured binary data (raw bytes) |
| 19 | (C) | UNION is a set operation, NOT a SQL constraint |
| 20 | (B) | PK: no NULL, one per table; UNIQUE: allows one NULL, multiple per table |
| 21 | (B) | FOREIGN KEY = references PRIMARY KEY of another table (referential integrity) |
| 22 | (C) | TCL = Transaction Control Language (COMMIT, ROLLBACK, SAVEPOINT) |
| 23 | (B) | Consistency = DB moves from valid state to valid state (integrity constraints) |
| 24 | (C) | Partially Committed = all operations done, awaiting disk write confirmation |
| 25 | (C) | TRUNCATE: resets AUTO_INCREMENT, cannot be rolled back; NO WHERE clause; NO triggers |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (B) | ISRO founded August 15, 1969 |
| 27 | (C) | ISRO HQ = Bengaluru (Bangalore) |
| 28 | (B) | SHAR = Sriharikota, Andhra Pradesh (primary launch centre) |
| 29 | (B) | Vikram Sarabhai = Father of Indian Space Programme |
| 30 | (B) | Chandrayaan-1 discovered water molecules on Moon (2008) |
| 31 | (B) | Chandrayaan-3 landed August 23, 2023 |
| 32 | (B) | India = FIRST country to land near Moon's South Pole (4th overall) |
| 33 | (C) | Chandrayaan-3 landing site = Shiv Shakti Point |
| 34 | (B) | National Space Day = August 23 (Chandrayaan-3 landing date) |
| 35 | (B) | Aditya-L1 = studies the Sun (corona, solar wind, solar flares) |
| 36 | (C) | Aditya-L1 → L1 Lagrange Point (~1.5 million km from Earth, between Earth-Sun) |
| 37 | (B) | Aditya-L1 launched September 2, 2023 (Jan 6, 2024 = reached L1 orbit) |
| 38 | (C) | Gaganyaan = India's first human spaceflight mission |
| 39 | (C) | Indian astronauts = Vyomanauts (from Sanskrit "Vyoma" = space) |
| 40 | (B) | Vyommitra = female humanoid robot for Gaganyaan (precedes human crew) |
| 41 | (B) | Mangalyaan: 1st Asian country to Mars + 1st country to succeed on first attempt |
| 42 | (B) | PSLV-C37 = launched 104 satellites in one mission (2017 world record) |
| 43 | (C) | Rakesh Sharma = first Indian in space, 1984 (Soyuz T-11, USSR mission) |
| 44 | (B) | Rakesh Sharma's famous quote = "Sare Jahan Se Achha" |
| 45 | (B) | LVM3/GSLV Mk-III = ISRO's heaviest and most powerful rocket |
| 46 | (C) | Pragyan rover detected Sulphur (+ Oxygen, Iron, Titanium) near South Pole |
| 47 | (C) | Mangalyaan lost contact September 2022 (after 8 successful years) |
| 48 | (B) | JWST = observes early universe and distant galaxies in infrared |
| 49 | (B) | Chandrayaan-2 Vikram crash site = Tiranga Point |
| 50 | (C) | All four statements (I, II, III, IV) are correct → Answer = (C) all correct → but option (D) "More than one" is the structure here. Wait — all four are correct so (C) says "All of I, II, III, and IV" → Ans = (C) |

---

# 🔁 DAY 58 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — SQL Transactions

### ACID Properties — One-Line Each:
```
A = Atomicity    → ALL or NOTHING (no partial execution; ROLLBACK on failure)
C = Consistency  → Valid state → Valid state (integrity constraints satisfied)
I = Isolation    → Concurrent transactions don't interfere (locks/timestamps)
D = Durability   → Committed changes survive failures (WAL/transaction logs)
```

### TCL Commands:
```
COMMIT       → Makes changes PERMANENT (cannot undo after this)
ROLLBACK     → UNDOES all changes since last COMMIT (recovers data)
SAVEPOINT sp → Sets CHECKPOINT within transaction
ROLLBACK TO sp → Partial rollback to named checkpoint (keeps earlier work)
```

### DELETE vs TRUNCATE vs DROP:
```
COMMAND   │ CATEGORY │ ROLLBACK? │ WHERE? │ TRIGGERS? │ STRUCTURE?
──────────┼──────────┼───────────┼────────┼───────────┼──────────────
DELETE    │ DML      │ ✅ YES    │ ✅ YES │ ✅ YES    │ Remains
TRUNCATE  │ DDL      │ ❌ NO     │ ❌ NO  │ ❌ NO     │ Remains (empty)
DROP      │ DDL      │ ❌ NO     │ ❌ N/A │ ❌ NO     │ REMOVED
```

### PYQ Traps — Transactions:
```
✅ ACID = Atomicity, Consistency, Isolation, Durability
✅ Atomicity = ALL or NOTHING (not "simultaneous")
✅ TRUNCATE = DDL = CANNOT rollback (most tested trap!)
✅ DELETE = DML = CAN rollback
✅ DROP = removes table structure completely
✅ UNION = NOT a constraint (set operation)
✅ RAW data type = unstructured binary data
✅ Shared lock = multiple readers, no writers
✅ Deadlock = circular wait → DBMS rolls back one victim
✅ Dirty Read = reading uncommitted (then rolled back) data
```

---

## ⚡ RAPID FIRE — Space Technology

### ISRO Key Facts:
```
Founded:    1969 (August 15) | HQ: Bengaluru
Father:     Dr. Vikram Sarabhai
Launch site: SHAR, Sriharikota (Andhra Pradesh)
Rockets:    PSLV (workhorse) | LVM3/GSLV Mk-III (heaviest)
```

### Mission Quick Reference:
```
MISSION         │ YEAR   │ KEY FACT
────────────────┼────────┼──────────────────────────────────────────────
Chandrayaan-1   │ 2008   │ Discovered WATER on Moon (PSLV-C11)
Chandrayaan-2   │ 2019   │ Vikram lander CRASHED (Tiranga Point)
Chandrayaan-3   │ 2023   │ FIRST landing near South Pole (Aug 23)
                │        │ Landing site = Shiv Shakti Point; 4th nation
Aditya-L1       │ 2023   │ India's 1st solar observatory; orbits L1;
                │        │ Reached L1: Jan 6, 2024 (studies Sun)
Gaganyaan       │ ~2026  │ India's 1st crewed mission; Vyomanauts
                │        │ Vyommitra = female robot (precursor)
Mangalyaan      │ 2013   │ 1st Asian country to Mars; 1st attempt
                │        │ success; lost contact 2022
PSLV-C37        │ 2017   │ 104 satellites (world record)
```

### Space Firsts:
```
First human in space:  Yuri Gagarin (USSR, April 12, 1961)
First on Moon:         Neil Armstrong (USA, July 20, 1969)
First Indian in space: Rakesh Sharma (1984) — "Sare Jahan Se Achha"
National Space Day:    August 23 (Chandrayaan-3 landing anniversary)
```

### PYQ Traps — Space:
```
✅ Chandrayaan-3 landing = August 23, 2023 (NOT July 14 = launch date!)
✅ National Space Day = August 23 (landing, not launch)
✅ Shiv Shakti Point = Chandrayaan-3 landing; Tiranga Point = Ch-2 crash
✅ India = 4th country on Moon (not 1st; not 2nd)
✅ Aditya-L1 = L1 point (not L2, not "landed on Sun")
✅ LVM3/GSLV Mk-III = heaviest rocket (PSLV = workhorse, not heaviest)
✅ Pragyan rover (Ch-3) detected Sulphur; Chandrayaan-1 detected water
✅ Rakesh Sharma = first Indian in space (NOT first Asian)
✅ Mangalyaan lost contact 2022 (not still operational)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **ACID = Atomicity (All or Nothing) + Consistency (Valid→Valid state) + Isolation (no interference) + Durability (committed = permanent via WAL)**. Atomicity uses ROLLBACK; Durability uses transaction logs.
2. **COMMIT = permanent; ROLLBACK = undo all; SAVEPOINT = checkpoint for partial rollback**. After COMMIT → no rollback possible. ROLLBACK TO savepoint_name → undoes only operations after that savepoint.
3. **DELETE (DML) = can rollback; TRUNCATE (DDL) = cannot rollback, faster, resets AUTO_INCREMENT, no triggers; DROP = removes entire table structure**. UNION is NOT a constraint.
4. **Chandrayaan-3 landed August 23, 2023** (National Space Day) = FIRST near Moon's South Pole (4th overall). Landing site = Shiv Shakti Point. Chandrayaan-2 crash = Tiranga Point. Aditya-L1 = L1 Lagrange Point (~1.5 million km), India's 1st solar observatory.
5. **Gaganyaan = India's 1st crewed mission; astronauts = Vyomanauts; Vyommitra = female robot precursor**. ISRO founded 1969, Bengaluru HQ, SHAR Sriharikota launch site. First Indian in space = Rakesh Sharma (1984), quote: "Sare Jahan Se Achha".

---

## 📅 DAY 59 PREVIEW — What's Coming Next:
**CS**: Computer Networks Advanced — Subnetting & VLSM (Variable Length Subnet Masking), TDM (Time Division Multiplexing) vs FDM vs WDM, Memory-Mapped I/O vs I/O-Mapped I/O
**GS**: Modern Indian History — Salt Satyagraha (1930), Civil Disobedience Movement, Bihar's role, Purna Swaraj resolution, Round Table Conferences

---

*🚀 Day 58 of 170 — ACID properties + TRUNCATE vs DELETE is a CONFIRMED PYQ combination. The #1 trap is "TRUNCATE can be rolled back" — make sure this is locked in. Chandrayaan-3 landing date, Shiv Shakti Point, and Aditya-L1 at L1 are space questions that WILL appear. Excellent work keeping pace — 34% through the plan!*
