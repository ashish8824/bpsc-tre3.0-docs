# 📅 BPSC TRE 4.0 — DAY 36 COMPLETE STUDY MODULE
### DBMS Basics & Database Concepts + Revolutionary Movements (Pre-Independence)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): DBMS Basics — Core Concepts, Types, Features, DBMS vs File System
> - Afternoon (1 hr): History — Revolutionary Movements: Ghadar Party, Anushilan Samiti, Abhinav Bharat, Birsa Munda
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 DBMS Basics & Database Concepts — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is Data?

### Real-Life Analogy — The School Notice Board:

Imagine your school has a notice board covered with scraps of paper:
- "Ravi scored 85 in Maths"
- "Priya is absent today"
- "Exam on 15th March"

Each scrap = **Data** — raw, isolated, unprocessed facts.

Now, if a teacher **organises** these scraps into a register with student names, roll numbers, marks and attendance in neat rows and columns — that organised collection becomes **meaningful information**.

> **Data = Raw, unprocessed facts and figures that alone have no meaning.**

### Examples of Data:
```
Raw Data:              What it represents when organised:
  "85"          →      Ravi's score in Mathematics
  "15-03-2024"  →      Date of upcoming exam
  "450"         →      Some number (salary? age? price? — meaningless alone!)

Data becomes information when given context and structure.
```

### 🎯 PYQ FACT: Data by itself is meaningless. It needs context to become information.

---

## 🔷 SECTION 2: What is a Database?

### Real-Life Analogy — The Railway Reservation System:

Think about booking a train ticket:
- There are THOUSANDS of trains
- MILLIONS of passengers
- Seats, schedules, prices, routes...

All of this is stored in ONE central, organised system. Anyone — ticket counter staff, app users, station masters — can access it instantly. That is a **Database**.

### Formal Definition:
> **A Database is a structured, organised collection of related data stored electronically so it can be easily accessed, managed, and updated.**

### Key Points:
```
DATABASE = Collection of RELATED data, stored SYSTEMATICALLY

"Related" means: Data in a database belongs to the SAME context/domain
  Example:
    Hospital Database: patient names, diagnoses, medicines, doctor schedules
    School Database:   student names, marks, attendance, fee records
    Bank Database:     account numbers, balances, transactions, loan records

Each row = one RECORD
Each column = one FIELD/ATTRIBUTE
The full table = one RELATION (in relational databases)
```

### What a Database is NOT:
```
NOT a database:
  → A single Excel sheet saved on your computer (no management system)
  → A folder with random files
  → Google Search (search ENGINE, not a database!)
  → A text file with student names written manually

A database needs ORGANISATION + MANAGEMENT SYSTEM to truly be called a database.
```

---

## 🔷 SECTION 3: What is a DBMS?

### Real-Life Analogy — The Librarian:

A library has THOUSANDS of books (= Database). If books were just dumped on the floor, no one could find anything. The **librarian** organises them, issues books, tracks returns, finds books for you, ensures two people don't take the same book — that entire management system is the **DBMS**.

```
LIBRARY ANALOGY:
  Books               = Data
  Library             = Database
  Librarian + System  = DBMS (Database Management System)
  
The librarian (DBMS):
  → Organises books (data structure)
  → Controls who can access which books (security)
  → Ensures no conflicts (concurrency control)
  → Recovers lost records (backup & recovery)
  → Answers queries ("Do you have a book on DBMS?") = Query processing
```

### Formal Definition:
> **DBMS (Database Management System) is a software system that creates, manages, and controls access to a database. It acts as an INTERFACE between the user/application and the actual database.**

### DBMS Architecture:

```
┌─────────────────────────────────────────────────────────────┐
│                        USERS / APPLICATIONS                  │
│        (Bank app, Hospital app, School software, etc.)       │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                           DBMS                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │Query Processor│  │Transaction   │  │Security &        │  │
│  │(SQL Engine)  │  │Manager       │  │Access Control     │  │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │Storage Manager│  │Concurrency   │  │Backup & Recovery │  │
│  │              │  │Controller    │  │Manager           │  │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                        DATABASE                              │
│   (Actual stored data — tables, records, files on disk)      │
└─────────────────────────────────────────────────────────────┘

KEY POINT: DBMS sits BETWEEN the user and the database.
           User never directly touches the raw data!
```

### Popular DBMS Software Examples:
```
Relational DBMS:
  → MySQL           (open source, web applications)
  → Oracle Database (enterprise, banking)
  → PostgreSQL      (open source, advanced features)
  → Microsoft SQL Server (enterprise, Windows)
  → SQLite          (lightweight, mobile apps)

NoSQL DBMS:
  → MongoDB   (document-based)
  → Cassandra (column-based, Facebook)
  → Redis     (key-value, caching)
```

### 🚨 PYQ TRAP #1: Google is NOT a DBMS!
```
Google = SEARCH ENGINE (it searches the web, indexes pages)
        NOT a Database Management System

DBMS manages a structured, controlled database.
Google crawls the internet and returns search results.

PYQ ANSWER: "Which of the following is NOT a DBMS?"
            → Google (always the trap option!)
```

---

## 🔷 SECTION 4: Database vs DBMS — The Critical Difference

This is one of the **most commonly confused concepts** in BPSC exams.

```
┌──────────────────────────────────────────────────────────────┐
│              DATABASE vs DBMS                                 │
├─────────────────────┬────────────────────────────────────────┤
│      DATABASE       │              DBMS                       │
├─────────────────────┼────────────────────────────────────────┤
│ Collection of DATA  │ SOFTWARE that manages the database      │
│ (the "what")        │ (the "how")                            │
├─────────────────────┼────────────────────────────────────────┤
│ Like a LIBRARY      │ Like the LIBRARIAN + management system  │
│ (books on shelves)  │ (who organises & controls access)       │
├─────────────────────┼────────────────────────────────────────┤
│ Example:            │ Example:                               │
│ "All student data   │ "MySQL software that manages            │
│  stored on server"  │  that student data"                    │
├─────────────────────┼────────────────────────────────────────┤
│ PASSIVE — just sits │ ACTIVE — performs operations:           │
│ there as stored data│ insert, delete, search, secure          │
├─────────────────────┼────────────────────────────────────────┤
│ Can exist without   │ Cannot function without a               │
│ DBMS (raw files)    │ database to manage                      │
└─────────────────────┴────────────────────────────────────────┘

SIMPLE FORMULA:
  Database = DATA container
  DBMS     = SOFTWARE that manages that container

ANALOGY:
  Database = Warehouse full of goods
  DBMS     = Warehouse Management System (who tracks, organises, secures goods)
```

### 🎯 PYQ FACT: A database is what you store; DBMS is what manages the storage.

---

## 🔷 SECTION 5: DBMS vs File System — The Most Important Comparison

**This is the #1 most-tested topic in DBMS basics questions!**

Before DBMS existed, data was stored in **File Systems** — ordinary files on a computer. Understanding WHY DBMS is better is key.

### What is a File System?
```
FILE SYSTEM (Old approach):
  Each department creates its own files:
  
  HR Department:
    hr_employees.txt → [EmpID | Name | Salary | Department]
  
  Payroll Department:
    payroll_data.txt → [EmpID | Name | Salary | Bank Account]
  
  Admin Department:
    admin_records.txt → [EmpID | Name | Address | Phone]
  
  PROBLEM: EmpID, Name, Salary stored in MULTIPLE files!
           If Ravi's salary changes → must update ALL three files!
           If only one is updated → INCONSISTENCY!
```

### DBMS vs File System — Comparison Table:

```
┌────────────────────┬──────────────────────────┬──────────────────────────┐
│      FEATURE       │       FILE SYSTEM         │          DBMS            │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Data Redundancy    │ HIGH — same data stored   │ LOW — centralised        │
│                    │ in multiple files          │ storage, no duplication  │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Data Inconsistency │ HIGH — updates in one     │ LOW — single update      │
│                    │ file don't reflect others  │ reflects everywhere      │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Data Sharing       │ Difficult — files are     │ Easy — multiple users    │
│                    │ isolated per department   │ access same DB           │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Security           │ Poor — file-level only    │ Strong — user roles,     │
│                    │ (anyone with file access) │ passwords, permissions   │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Concurrent Access  │ No — file locked when     │ Yes — multiple users     │
│                    │ one user uses it          │ simultaneously           │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Data Integrity     │ No constraints — any      │ Enforced — data types,   │
│                    │ value can be stored       │ constraints, validations  │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Query Processing   │ Manual — write programs   │ SQL — simple queries     │
│                    │ to search/filter data     │ answer complex questions  │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Crash Recovery     │ Manual — data may be lost │ Automatic — transactions │
│                    │ if system crashes          │ ensure recovery          │
├────────────────────┼──────────────────────────┼──────────────────────────┤
│ Data Independence  │ None — change in file     │ Yes — logical/physical   │
│                    │ format affects all programs│ independence layers      │
└────────────────────┴──────────────────────────┴──────────────────────────┘
```

### Real-Life Scenario — Why DBMS Wins:

```
HOSPITAL EXAMPLE:

FILE SYSTEM approach:
  Doctor's file: PatientID | Name | Diagnosis
  Billing file:  PatientID | Name | Amount
  Pharmacy file: PatientID | Name | Medicines

  Problem: If patient name changes (married name) →
           Must update ALL 3 files manually!
           If pharmacy file is missed → INCONSISTENCY!
           Receptionist and pharmacist BOTH editing files → CONFLICT!

DBMS approach:
  ONE central PATIENTS table: PatientID | Name | Address | Phone
  Doctor references: PatientID (linked to central table)
  Billing references: PatientID (linked to central table)
  Pharmacy references: PatientID (linked to central table)

  Solution: Change name in ONE place → reflects EVERYWHERE automatically!
            Multiple staff access simultaneously → DBMS manages conflicts!
```

### 🎯 PYQ KEY: The PRIMARY disadvantage of File System = DATA REDUNDANCY and INCONSISTENCY.
### 🎯 PYQ KEY: The PRIMARY advantage of DBMS = REDUCED REDUNDANCY + DATA CONSISTENCY.

---

## 🔷 SECTION 6: Types of Databases

### Overview Diagram:

```
                    TYPES OF DATABASES
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
  RELATIONAL        HIERARCHICAL           NETWORK
  (Most common)      (Tree-based)          (Graph-based)
  MySQL, Oracle      IMS (IBM)             IDMS
        │
        ├──────────────────┐
        │                  │
  DISTRIBUTED         NoSQL/Object-Oriented
  (Multiple sites)    (MongoDB, Redis)
```

---

### 1. RELATIONAL DATABASE (RDBMS)

```
CONCEPT: Data stored in TABLES (relations) with rows and columns.
         Tables are LINKED using keys (foreign keys).

STRUCTURE:
  ┌─────────────────────────────────────┐
  │         STUDENTS Table              │
  ├────────┬──────────┬──────────┬──────┤
  │ StdID  │  Name    │ Course   │ Marks│
  ├────────┼──────────┼──────────┼──────┤
  │  101   │  Ravi    │ CS       │  85  │
  │  102   │  Priya   │ Math     │  90  │
  │  103   │  Aman    │ CS       │  78  │
  └────────┴──────────┴──────────┴──────┘

  ┌──────────────────────────────────────┐
  │         COURSES Table                │
  ├──────────┬────────────────┬──────────┤
  │ CourseID │  CourseName    │ Credits  │
  ├──────────┼────────────────┼──────────┤
  │  CS      │ Comp Science   │  4       │
  │  Math    │ Mathematics    │  3       │
  └──────────┴────────────────┴──────────┘

Tables are RELATED → hence "Relational"

EXAMPLES: MySQL, Oracle, MS SQL Server, PostgreSQL, SQLite
LANGUAGE: SQL (Structured Query Language)
USE: Banks, hospitals, schools, e-commerce (most common type!)
```

### 🎯 PYQ FACT: Relational databases use SQL. They are the MOST WIDELY USED type of database.

---

### 2. HIERARCHICAL DATABASE

```
CONCEPT: Data organised in a TREE structure (parent-child relationships).
         Each parent can have MULTIPLE children, but each child has ONLY ONE parent.
         Like an organisation chart or file system folder structure.

STRUCTURE:
            [Company] ← ROOT (only 1 root)
           /          \
     [HR Dept]      [IT Dept]
     /      \        /      \
 [Ravi]  [Priya] [Aman]  [Kavya]

Rules:
  → ONE root node at top
  → Parent can have MANY children
  → Each child has EXACTLY ONE parent
  → Navigate TOP-DOWN only (can't go from Ravi directly to Aman!)

EXAMPLE: IBM's IMS (Information Management System) — used in banks
         Windows Registry (hierarchical structure)
         XML data (somewhat hierarchical)

LIMITATION:
  → Can't represent MANY-TO-MANY relationships
  → Ravi can't belong to BOTH HR and IT — rigid structure!
  → Navigation must be done from the root downward
```

### 🎯 PYQ FACT: In hierarchical DB, a child can have ONLY ONE parent (unlike network DB where multiple parents are allowed).

---

### 3. NETWORK DATABASE

```
CONCEPT: Extension of hierarchical model.
         Data organised as a GRAPH — nodes connected by links.
         A child CAN have MULTIPLE parents (solves hierarchical limitation!).

STRUCTURE:
      [Project A] ←──────→ [Project B]
          │    ↖          ↗     │
          ↓      [Shared]       ↓
       [Ravi] ──────────── [Priya]
          │                    │
          └────→ [Team Lead] ←─┘

  → Ravi can work on BOTH Project A and Project B (multiple parents!)
  → Priya also connected to both projects
  → More flexible than hierarchical

EXAMPLE: IDMS (Integrated Database Management System)
         Early network databases from 1960s-70s

KEY DIFFERENCE from HIERARCHICAL:
  Hierarchical: Child → exactly ONE parent (tree)
  Network:      Child → MULTIPLE parents (graph)

LIMITATION:
  → Complex to design and maintain
  → No standard query language (unlike SQL for relational)
  → Programming required for navigation
```

---

### 4. DISTRIBUTED DATABASE

```
CONCEPT: Database DISTRIBUTED across MULTIPLE physical locations
         (different computers, cities, or even countries).
         But appears as ONE logical database to users.

STRUCTURE:
  ┌──────────────────────────────────────────────┐
  │           LOGICAL VIEW (User sees this)       │
  │        ONE unified database                   │
  └────────────────┬─────────────────────────────┘
                   │
      ┌────────────┴──────────────┐
      │                           │
  ┌───────────┐           ┌───────────┐
  │ Node 1    │           │ Node 2    │
  │ Mumbai    │           │ Delhi     │
  │ Server    │           │ Server    │
  └───────────┘           └───────────┘
       +
  ┌───────────┐
  │ Node 3    │
  │ Bengaluru │
  │ Server    │
  └───────────┘

REAL EXAMPLE:
  SBI (State Bank of India):
  → Mumbai branch data stored in Mumbai server
  → Delhi branch data in Delhi server
  → ALL connected → your account accessible from ANY branch!

TYPES:
  Homogeneous: All nodes use SAME DBMS software
  Heterogeneous: Different nodes use DIFFERENT DBMS software

EXAMPLES: Google Spanner, Apache Cassandra, Amazon DynamoDB
USE: Banks, airlines, large corporations with multiple branches
```

### 🚨 PYQ TRAP #2: "Decentralized" is NOT a standard type of database!

```
COMMON EXAM TRAP: Options include:
  (A) Relational
  (B) Hierarchical
  (C) Network
  (D) Decentralized   ← TRAP!
  (E) None of the above

"Decentralized" sounds similar to "Distributed" but is NOT a standard database type.
Standard types: Relational, Hierarchical, Network, Distributed, Object-Oriented, NoSQL

CORRECT ANSWER: If "Decentralized" appears as an option → it is NOT a standard type!
The correct term is "DISTRIBUTED database."
```

### Database Types — Summary Table:

```
┌───────────────┬──────────────────┬──────────────────┬───────────────────┐
│     TYPE      │    STRUCTURE     │    EXAMPLE       │   KEY FEATURE     │
├───────────────┼──────────────────┼──────────────────┼───────────────────┤
│ Relational    │ Tables (rows &   │ MySQL, Oracle,   │ Uses SQL; most    │
│               │ columns)         │ PostgreSQL       │ widely used       │
├───────────────┼──────────────────┼──────────────────┼───────────────────┤
│ Hierarchical  │ Tree (parent-    │ IBM IMS,         │ Each child has    │
│               │ child)           │ Windows Registry │ only ONE parent   │
├───────────────┼──────────────────┼──────────────────┼───────────────────┤
│ Network       │ Graph (nodes &   │ IDMS, IDS        │ Child can have    │
│               │ links)           │                  │ MULTIPLE parents  │
├───────────────┼──────────────────┼──────────────────┼───────────────────┤
│ Distributed   │ Multiple         │ Google Spanner,  │ Data spread across│
│               │ locations, one   │ Amazon DynamoDB  │ locations; appears│
│               │ logical DB       │                  │ as single DB      │
├───────────────┼──────────────────┼──────────────────┼───────────────────┤
│ Object-       │ Objects (like    │ db4o, ObjectDB   │ Stores objects,   │
│ Oriented      │ OOP classes)     │                  │ not just tables   │
└───────────────┴──────────────────┴──────────────────┴───────────────────┘
```

---

## 🔷 SECTION 7: Features / Advantages of DBMS

These are the **core selling points** of DBMS — heavily tested in exams!

---

### 1. REDUCED DATA REDUNDANCY

```
WHAT: Eliminates storage of same data in multiple places.

FILE SYSTEM PROBLEM:
  HR file:      [EmpID | Name | Dept | Salary]
  Payroll file: [EmpID | Name | Salary | Bank]
  Admin file:   [EmpID | Name | Address | Phone]
  
  Name and Salary stored THREE times = REDUNDANCY!

DBMS SOLUTION:
  ONE EMPLOYEES table: [EmpID | Name | Dept | Salary | Bank | Address | Phone]
  All departments REFERENCE the same table.
  → Name stored ONCE = Zero redundancy!
```

---

### 2. DATA CONSISTENCY

```
WHAT: When data changes, the change is reflected uniformly everywhere.

EXAMPLE: Employee Ravi gets a salary hike.
  File System: Must update HR file, Payroll file, Admin file separately.
               If one file is missed → Ravi earns 3 different salaries!
               
  DBMS: Update ONE central record.
        All queries, all departments see the SAME updated salary.
        → CONSISTENCY guaranteed!
```

---

### 3. DATA SECURITY

```
WHAT: Controls who can access what data.

DBMS provides:
  → User Authentication: Login required
  → Authorization: Different users get different permissions
     DBA (Database Admin) → Full access
     Doctor              → View + update patient records
     Receptionist        → View + update appointments only
     Finance staff       → View billing only
  → Encryption of sensitive data
  → Audit trails — who accessed what, when

FILE SYSTEM: Any person with file access can read EVERYTHING.
DBMS: Role-based access control — nurses can't see doctor notes!
```

---

### 4. MULTI-USER ACCESS (Concurrent Access)

```
WHAT: Multiple users can access and modify data simultaneously without conflicts.

EXAMPLE: Railway Reservation System
  → 10,000 users checking ticket availability at the SAME time
  → 500 users trying to book the SAME seat simultaneously
  
  Without DBMS: Two users might book the SAME seat → conflict!
  
  DBMS Solution: CONCURRENCY CONTROL
  → Locks ensure only ONE user can book a specific seat at a time
  → Other users either wait or are told seat is taken
  → Result: No double-booking, no conflicts!

🚨 PYQ TRAP: "Single-user access" is a LIMITATION, not a FEATURE of DBMS!
   FEATURE = MULTI-user access
   LIMITATION of file systems = usually single-user at a time
```

---

### 5. DATA INTEGRITY

```
WHAT: Ensures data is ACCURATE, VALID, and CONSISTENT at all times.

Types of integrity constraints in DBMS:
  → Domain Constraint: Age must be a number (not letters)
  → Entity Integrity: Primary key cannot be NULL
  → Referential Integrity: Foreign key must match a valid primary key

EXAMPLE:
  Student marks table: marks column accepts ONLY values 0-100.
  If someone tries to enter 150 → DBMS REJECTS it!
  
  FILE SYSTEM: No such protection. 
               You could type "abc" in the marks column.
               No validation!
```

---

### 6. DATA INDEPENDENCE

```
WHAT: Changes in data storage structure don't require changes in application programs.

TWO LEVELS:
  Physical Independence:
    → Change how data is STORED (new disk format, new storage structure)
    → Applications DO NOT need to be rewritten!
    
  Logical Independence:
    → Change the LOGICAL structure (add a new column to a table)
    → Other applications using the table are unaffected

ANALOGY: 
  When a library physically rearranges its bookshelves (storage),
  the library's catalogue (logical structure) remains the same.
  Readers (users) still search the catalogue the same way!
```

---

### 7. BACKUP AND RECOVERY

```
WHAT: DBMS provides automatic mechanisms to restore data after failures.

SCENARIO: Power cut while updating a bank transaction!
  Step 1: Deduct ₹10,000 from Account A ✓
  Step 2: POWER CUTS OUT before crediting Account B ✗
  
  FILE SYSTEM: Money is LOST — deducted but not credited!
  
  DBMS Solution: TRANSACTIONS with ACID properties:
    → Transaction = a complete unit of work (both steps together)
    → If power cuts, the ENTIRE transaction is rolled back
    → Account A is restored to original balance
    → No partial updates!
    
  ACID = Atomicity, Consistency, Isolation, Durability
  (Covered in detail in later DBMS days)
```

---

### Features Summary — Quick Reference:

```
┌────────────────────────┬──────────────────────────────────────────────┐
│       FEATURE          │                MEANING                        │
├────────────────────────┼──────────────────────────────────────────────┤
│ Reduced Redundancy     │ Data stored ONCE, referenced everywhere       │
│ Data Consistency       │ One update = reflected universally            │
│ Data Security          │ Role-based access, encryption                 │
│ Multi-user Access      │ Concurrent users without conflicts            │
│ Data Integrity         │ Constraints ensure valid, accurate data       │
│ Data Independence      │ Storage changes don't affect applications     │
│ Backup & Recovery      │ Automatic restore after failures (ACID)       │
│ Query Processing       │ SQL — easy retrieval of complex data          │
│ Centralised Control    │ DBA manages everything from one point         │
└────────────────────────┴──────────────────────────────────────────────┘
```

---

## 🔷 SECTION 8: DBMS Acts as Interface — Key Concept

```
THE INTERFACE CONCEPT:

Users/Applications NEVER directly interact with raw data.
DBMS sits between them.

  APPLICATION  ←→  DBMS  ←→  DATABASE
   (programs)               (raw stored data)

Why this matters:
  → Application only knows: "Give me all students who scored > 80"
  → DBMS knows: WHERE data is stored, how to retrieve it efficiently
  → Application doesn't care about physical storage — DBMS handles that!
  
This separation is called DATA ABSTRACTION — a core DBMS concept.

THREE LEVELS (ANSI-SPARC Architecture):
  
  [External Level]  ← What each user SEES (views, subsets)
        ↕               Different users see different views
  [Conceptual Level] ← Full logical structure (all tables, relationships)
        ↕               DBA sees this
  [Internal Level]  ← Physical storage (how data saved on disk)
                        Storage engineers see this
```

---

## 🔷 SECTION 9: Common PYQ Patterns and Traps Summary

```
TRAP 1: "Google is a DBMS" → FALSE. Google is a search engine.

TRAP 2: "Decentralized database" is a type → FALSE. 
        Correct term = DISTRIBUTED. "Decentralized" is not standard.

TRAP 3: "Single-user access is a feature of DBMS" → FALSE.
        Multi-user access is a FEATURE. Single-user is a LIMITATION of file systems.

TRAP 4: "Database and DBMS are the same thing" → FALSE.
        Database = data collection; DBMS = software managing it.

TRAP 5: "DBMS reduces data security" → FALSE.
        DBMS IMPROVES security through access control.

TRAP 6: "Hierarchical DB allows multiple parents" → FALSE.
        Hierarchical = ONE parent per child. NETWORK = multiple parents.

TRAP 7: "Relational DB is the oldest type" → FALSE.
        Hierarchical and Network came FIRST. Relational (1970s) came later.

TRAP 8: "File system has better data integrity than DBMS" → FALSE.
        DBMS has far superior integrity enforcement.

TRAP 9: "Distributed DB = data stored in multiple files on ONE computer" → FALSE.
        Distributed = data on MULTIPLE computers/locations.

TRAP 10: "DBMS is used only for small data" → FALSE.
         DBMS scales from small (SQLite) to massive (Oracle for banks).
```

---

# PART 2: GENERAL STUDIES
## ⚔️ History — Revolutionary Movements: Pre-Independence India

---

## 🔷 SECTION 1: Overview — The Birth of Revolutionary Nationalism

### Setting the Stage:

By the early 1900s, many Indian nationalists had grown frustrated with the **moderate approach** of the Congress. Petitions, memorandums, appeals to British conscience — these seemed to yield nothing. A younger generation of leaders believed:

> **"Freedom cannot be begged. It must be seized."**

These revolutionaries built secret societies, carried out political assassinations, organised armed resistance, and created fear in British hearts — even if they could not immediately overthrow the empire. Their contribution was immense: they raised **the cost of imperialism** for Britain.

### Timeline Snapshot:

```
1857 → First War of Independence (Sepoy Mutiny) — seeds of revolution planted
1897 → Chapekar Brothers assassinate Rand & Ayerst (Pune Plague Commissioner)
1902 → Anushilan Samiti founded (Bengal)
1904 → Abhinav Bharat founded (V.D. Savarkar)
1907 → Ghadar Party precursors form in diaspora
1908 → Khudiram Bose hanged — youngest revolutionary martyr
1913 → Ghadar Party officially founded (San Francisco)
1915 → Ghadar Mutiny attempt (unsuccessful)
1899-1900 → Birsa Munda's Ulgulan (Revolt) in Jharkhand
```

---

## 🔷 SECTION 2: ANUSHILAN SAMITI

### Formation and Background:

```
NAME MEANING: Anushilan = "Practice" or "Cultivation" (of revolutionary qualities)

FOUNDED: 1902, Calcutta (Kolkata)
FOUNDERS: Pramathanath Mitra (original founder, lawyer)
           Sarala Devi Chaudhurani (Rabindranath Tagore's niece) — helped organise youth
           
KEY LEADER: Barindra Kumar Ghosh (Aurobindo Ghosh's younger brother)
             Aurobindo Ghosh (Sri Aurobindo) — intellectual backing

BRANCHES:
  → Calcutta Anushilan Samiti (main centre)
  → Dhaka Anushilan Samiti (1906) — became most active branch
     Founded in Dhaka by Pulin Bihari Das
```

### Structure and Activities:

```
STRUCTURE:
  → Organised as a physical training society (to hide revolutionary activities!)
  → Publicly: gymnasiums, lathi practice, wrestling, physical training
  → Secretly: bomb-making, weapons training, revolutionary planning
  
ACTIVITIES:
  → Manufacturing and collecting firearms and explosives
  → Propagating revolutionary literature
  → Training youth in guerrilla tactics
  → Collecting funds for revolution (sometimes through "political dacoities")
  
IDEOLOGY:
  → Hindu religious symbolism used to inspire nationalism
  → Inspired by Bankim Chandra Chatterjee's "Anandamath" (Vande Mataram)
  → Violence as a legitimate tool for independence
```

### Key Events:

```
ALIPORE BOMB CASE (1908):
  → Khudiram Bose and Prafulla Chaki threw a bomb at a carriage carrying
    Magistrate Kingsford in Muzaffarpur.
  → The carriage was EMPTY (wrong target — carried British ladies instead)
  → Prafulla Chaki killed himself upon arrest
  → Khudiram Bose was captured, tried, and HANGED on 11 August 1908
  → Age at execution: 18 years — became a symbol of revolutionary sacrifice
  → Alipore Bomb Case trial → Aurobindo Ghosh arrested but acquitted
```

### 🎯 PYQ FACTS:
```
✅ Anushilan Samiti = 1902, Calcutta — used physical training as cover
✅ Dhaka branch = 1906, Pulin Bihari Das — most radical branch  
✅ Khudiram Bose (youngest martyr, 18 yrs) — linked to Anushilan activities
✅ Aurobindo Ghosh associated with revolutionary movement before becoming a spiritual leader
```

---

## 🔷 SECTION 3: ABHINAV BHARAT SOCIETY

### Formation:

```
FULL NAME: Abhinav Bharat Society
            (Abhinav = "New" or "Young"; Bharat = India)
            Meaning: "Young India" society

FOUNDED: 1904, Nasik, Maharashtra
FOUNDER: Vinayak Damodar Savarkar (V.D. Savarkar)
          Also known as "Veer Savarkar"

CO-FOUNDER: Ganesh Damodar Savarkar (Veer Savarkar's elder brother)

INSPIRED BY: Giuseppe Mazzini's "Young Italy" revolutionary movement
             → Savarkar translated Mazzini's biography into Marathi
             → Believed in ARMED revolution like Mazzini
```

### Ideology and Activities:

```
IDEOLOGY:
  → Complete independence from British rule (Purna Swaraj) — 
    at a time when even Congress only demanded dominion status!
  → Armed revolution is necessary and justified
  → Reinterpretation of 1857 as "First War of Independence" 
    (Savarkar's book "The Indian War of Independence, 1857")

ACTIVITIES:
  → Secret society with oath-bound membership
  → Smuggled pistols from Paris (via fellow revolutionary Madame Cama)
  → Political assassinations planned and carried out
  → Recruitment in London among Indian students (India House)
  → Published revolutionary pamphlets

SAVARKAR IN LONDON:
  → Studied at Inner Temple (law) in London
  → Connected with Shyamji Krishna Varma at India House, London
  → Organised revolutionary activities among Indian students abroad
```

### Key Events:

```
NASIK CONSPIRACY CASE (1909):
  → Anant Laxman Kanhere (a member linked to Abhinav Bharat) 
    assassinated Jackson, the District Collector of Nasik
  → Kanhere executed
  → V.D. Savarkar charged with conspiracy

JACKSON MURDER CASE:
  → Pistols used traced back to Savarkar (who had them smuggled)
  → Savarkar arrested in London (1910), escaped but re-captured at Marseilles
  → Transported to India
  → Sentenced to 50 YEARS imprisonment — sent to Cellular Jail, Andaman

CELLULAR JAIL ("Kala Pani"):
  → Savarkar spent years in Cellular Jail, Port Blair
  → Today, Cellular Jail is a National Memorial
  → Known as "Kala Pani" — most feared punishment
```

### 🎯 PYQ FACTS:
```
✅ Abhinav Bharat = 1904, Nasik, V.D. Savarkar
✅ Inspired by Mazzini's "Young Italy"
✅ Savarkar's book: "The Indian War of Independence, 1857"
   (First to call 1857 a War of Independence — not a mutiny!)
✅ Savarkar sentenced to 50 years, imprisoned in Cellular Jail (Kala Pani)
✅ Nasik Conspiracy Case = linked to Abhinav Bharat
```

---

## 🔷 SECTION 4: GHADAR PARTY

### Background — The Diaspora Rises:

```
CONTEXT:
  Thousands of Indian labourers (mainly Punjabi Sikhs) had migrated to
  North America (USA & Canada) to work on farms, railways, sawmills.
  Despite hard work, they faced:
  → Racial discrimination ("Asiatic exclusion")
  → Denial of voting rights
  → Immigration restrictions (Continuous Journey Regulation, 1908)
  → Deportation threats
  
  These experiences radicalised them: 
  "We are denied rights in our OWN colony as much as in America.
   Only independence will give us dignity."
```

### Formation:

```
NAME: GHADAR (also spelled Ghadr)
MEANING: "Ghadar" = REVOLT / MUTINY / Revolution (in Urdu/Punjabi)
         Named to invoke the spirit of 1857!

FOUNDED: 1913, San Francisco, California, USA
FORMAL ORGANISATION DATE: 21 April 1913

FOUNDER: Sohan Singh Bhakna (first President)
KEY LEADER: Har Dayal (intellectual force; left later, deported by USA)
             Kartar Singh Sarabha (young revolutionary leader)
             Bhagwan Singh, Rahmat Ali Shah, Barkatullah

HEADQUARTERS: Astoria, Oregon (later San Francisco, California)
NEWSPAPER: "Ghadar" (published from San Francisco)
           — Published in Punjabi, Urdu, Hindi, Gujarati, Pashto!
           — Smuggled into India to spread revolutionary ideas
```

### Structure and Ideology:

```
IDEOLOGY:
  → Complete independence from British rule
  → INCLUSIVE nationalism — no caste, no religion (Sikhs, Hindus, Muslims together!)
  → Armed revolution against British — inspired by 1857
  → Strong anti-imperialist, anti-colonial ideology
  → Some socialist influences

STRUCTURE:
  → International network — USA, Canada, Philippines, Singapore, Fiji, Hong Kong
  → Collected funds from Indian workers abroad
  → Recruited from Punjabi diaspora, especially former soldiers

NEWSPAPER "GHADAR":
  → First edition: November 1, 1913
  → Tagline: "Angrezi Raj ka Dushman" (Enemy of British Rule)
  → Distributed free of cost
  → Highly inflammatory — called for immediate revolt
```

### The Ghadar Mutiny (1915):

```
PLAN: When World War I began (1914), Ghadar leaders saw opportunity:
  "Britain is busy fighting Germany. NOW is the time to revolt in India!"

PLAN:
  → Thousands of Ghadarites left USA/Canada to return to India
  → Plan: Incite Indian soldiers in British Indian Army to mutiny
  → Coordinate simultaneous uprising across Punjab

WHAT WENT WRONG:
  → British intelligence (aided by informers) got wind of the plan
  → Key meetings, weapons caches discovered
  → Leaders arrested as they arrived in India
  → February 19, 1915 mutiny date revealed by informers → British cracked down

OUTCOME:
  → Mutiny FAILED — mass arrests across Punjab
  → 42 Ghadarites hanged (including Kartar Singh Sarabha, age 19)
  → Hundreds sentenced to transportation (Kala Pani) or imprisonment
  → Ghadar Party weakened but NOT eliminated

KARTAR SINGH SARABHA:
  → Only 19 years old when hanged (1915)
  → Known as "the first revolutionary to die for Punjab"
  → Bhagat Singh kept his photo in his pocket — called Sarabha his "guru"!
```

### 🎯 PYQ FACTS:
```
✅ Ghadar Party = 1913, San Francisco, founder = Sohan Singh Bhakna
✅ Intellectual leader = Har Dayal; young leader = Kartar Singh Sarabha
✅ Newspaper "Ghadar" = multi-language, smuggled into India
✅ 1915 Ghadar Mutiny FAILED due to British intelligence
✅ Bhagat Singh was inspired by Kartar Singh Sarabha
✅ Inclusive nationalism — no caste/religion divisions
✅ "Ghadar" means revolt/mutiny (invokes 1857 spirit)
```

---

## 🔷 SECTION 5: BIRSA MUNDA — Tribal Revolutionary

### Context — The Tribal Revolt:

```
NOTE: Birsa Munda was NOT a "revolutionary movement" in the urban educated sense.
      He led a TRIBAL REVOLT — a grassroots uprising of the Munda tribal community.
      But he is equally important as a symbol of resistance against British exploitation.

COMMUNITY: Munda tribe (Adivasi community)
REGION: Chota Nagpur region (now Jharkhand)
         Khunti district (his birthplace — Ulihatu village)
BORN: 15 November 1875, Ulihatu, Ranchi district
```

### Background — Why Did Birsa Revolt?

```
BRITISH EXPLOITATION OF TRIBAL LANDS:
  1. DIKU System: Non-tribal moneylenders (Dikuahs/Dikurs) took over tribal lands
     through debt traps.
  2. Landlord System (Zamindari): Tribals became bonded laborers on their OWN land.
  3. Forest Laws: British Forest Acts (1878) denied tribals access to forests 
     they had lived in for centuries!
  4. Christian Missionaries: Changing tribal cultural and religious identity.
  5. Forced Labour (Bethegari): Tribals forced to work without pay for landlords.

RESULT: Munda tribals had lost their land, dignity, and traditional way of life.
        Birsa emerged as their messiah.
```

### Birsa as "Dharti Abba" (Father of the Earth):

```
RELIGIOUS AWAKENING:
  Birsa Munda declared himself a DIVINE PROPHET around 1895.
  
  He proclaimed:
  → "I am the messenger of God (Singbonga)"
  → "We must reclaim our ancestral lands"
  → "Stop paying rent to landlords (dikuahs)"
  
  He was called "DHARTI ABBA" (Father of the Earth) by his followers.
  Also called "BHAGWAN" by tribals who believed he had divine powers.
  
  His movement had TWO dimensions:
  1. Religious/social: Purification of tribal religion (no alcohol, no superstition)
  2. Political: Armed revolt against British and exploitative landlords
```

### ULGULAN (1899-1900):

```
ULGULAN = "The Great Tumult" or "The Great Revolt"
(Ulgulan = disturbance/uprising in Mundari language)

WHAT HAPPENED:
  → Birsa mobilised thousands of Munda tribals
  → December 1899 - January 1900: Armed uprising began
  → Tribals attacked police stations, churches, landlord properties
  → British forces deployed → Birsa's forces fought with bows, arrows, axes
  
OUTCOME:
  → British forces crushed the revolt (superior weapons)
  → Birsa Munda captured on 3 February 1900 near Jamkopai forest
  → Imprisoned in Ranchi jail
  → Died in prison on 9 June 1900 (officially "cholera" — many believe poisoned)
  → Age at death: 25 years

LEGACY:
  → Inspired the Chota Nagpur Tenancy Act (1908):
    Gave tribal land PROTECTION — tribals' lands cannot be sold to non-tribals!
    This is Birsa's greatest legal legacy still in force today.
  → Jharkhand state created in 2000 — partly to honour tribal homeland demand
  → 15 November (Birsa's birthday) = Jharkhand Foundation Day
  → Birsa Munda = declared NATIONAL HERO; his portrait in Parliament!
```

### 🎯 PYQ FACTS:
```
✅ Birsa Munda = Munda tribe, Chota Nagpur (Jharkhand)
✅ Born: 15 November 1875 — Jharkhand Foundation Day is on this date!
✅ Ulgulan = 1899-1900 armed uprising
✅ Called "Dharti Abba" (Father of the Earth) and "Bhagwan"
✅ Captured: 3 February 1900; Died: 9 June 1900 (age 25) in Ranchi jail
✅ Result: Chota Nagpur Tenancy Act (1908) — tribal land protection!
✅ His image is in the Central Hall of Parliament
✅ Led against: Diku moneylenders + British zamindars + forest restrictions
```

---

## 🔷 SECTION 6: Revolutionary Movements — Comparative Timeline

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    REVOLUTIONARY MOVEMENTS TIMELINE                          │
├──────────┬────────────────────┬───────────────────┬─────────────────────────┤
│   YEAR   │     MOVEMENT       │    KEY LEADER(S)  │     SIGNIFICANCE        │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1897     │ Chapekar Brothers  │ Bal Gangadhar &   │ First political murder  │
│          │ Assassination      │ Damodar Chapekar  │ of a British official   │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1899-1900│ ULGULAN            │ Birsa Munda       │ Tribal revolt; led to   │
│          │ (Munda Revolt)     │ "Dharti Abba"     │ CNT Act 1908            │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1902     │ Anushilan Samiti   │ P.N. Mitra,       │ Bengal's underground    │
│          │                    │ Barindra Ghosh    │ revolutionary network   │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1904     │ Abhinav Bharat     │ V.D. Savarkar     │ First call for complete │
│          │                    │                   │ independence (Purna     │
│          │                    │                   │ Swaraj) + 1857 as "war" │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1905     │ Partition of Bengal│ Mass agitation    │ Swadeshi Movement       │
│          │ + Swadeshi         │ across India      │ radicalises politics    │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1908     │ Alipore Bomb Case  │ Khudiram Bose,    │ First bomb attack;      │
│          │                    │ Prafulla Chaki    │ Khudiram hanged at 18   │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1913     │ GHADAR PARTY       │ Sohan Singh Bhakna│ Diaspora revolution;    │
│          │ founded            │ Har Dayal,        │ inclusive, anti-imperial│
│          │                    │ Kartar Singh      │ newspaper published     │
├──────────┼────────────────────┼───────────────────┼─────────────────────────┤
│ 1915     │ Ghadar Mutiny      │ Kartar Singh      │ Failed; 42 hanged;      │
│          │ (attempted)        │ Sarabha & others  │ Sarabha inspired Bhagat │
│          │                    │                   │ Singh                   │
└──────────┴────────────────────┴───────────────────┴─────────────────────────┘
```

---

## 🔷 SECTION 7: Key Personalities — Quick Reference

```
┌──────────────────────┬──────────────┬──────────────────────────────────────┐
│      PERSON          │  MOVEMENT    │          KEY CONTRIBUTION            │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ V.D. Savarkar        │ Abhinav      │ Coined "First War of Independence"   │
│ (Veer Savarkar)      │ Bharat       │ for 1857; 50 yr sentence; Kala Pani  │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Sohan Singh Bhakna   │ Ghadar Party │ Founder/President of Ghadar Party    │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Har Dayal            │ Ghadar Party │ Intellectual backbone; deported by   │
│                      │              │ USA; edited "Ghadar" newspaper        │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Kartar Singh Sarabha │ Ghadar Party │ Hanged at 19 (1915); Bhagat Singh's  │
│                      │              │ inspiration; youngest Ghadar martyr  │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Barindra Kumar Ghosh │ Anushilan    │ Led Calcutta branch; younger brother │
│                      │ Samiti       │ of Aurobindo Ghosh                   │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Khudiram Bose        │ Anushilan    │ Youngest revolutionary martyr        │
│                      │ (linked)     │ Hanged at 18 (1908); Muzaffarpur bomb│
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Birsa Munda          │ Ulgulan      │ "Dharti Abba"; tribal revolt;        │
│                      │ (Munda)      │ CNT Act 1908 as legacy               │
├──────────────────────┼──────────────┼──────────────────────────────────────┤
│ Pulin Bihari Das     │ Anushilan    │ Founded Dhaka Anushilan Samiti (1906)│
│                      │ Samiti       │ Most radical branch                  │
└──────────────────────┴──────────────┴──────────────────────────────────────┘
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: DBMS Basics, Types of Databases, Features, DBMS vs File System

---

**Q1.** What is a DBMS?
(A) A programming language used to create websites
(B) Software that creates, manages, and controls access to a database
(C) A hardware component for storing data
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following correctly defines a DATABASE?
(A) A software program that processes user queries
(B) A programming interface for application development
(C) A structured, organised collection of related data stored electronically
(D) More than one of the above
(E) None of the above

---

**Q3.** DBMS acts as an interface between:
(A) Hardware and software
(B) User/application and the database
(C) CPU and RAM
(D) More than one of the above
(E) None of the above

---

**Q4.** Which of the following is NOT a DBMS?
(A) MySQL
(B) Oracle
(C) Google
(D) More than one of the above
(E) None of the above

---

**Q5.** The PRIMARY disadvantage of a File System compared to DBMS is:
(A) File System is too expensive
(B) File System requires internet connection
(C) File System leads to data redundancy and inconsistency
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following is a FEATURE of DBMS?
(A) Single-user access only
(B) High data redundancy
(C) Multi-user concurrent access with concurrency control
(D) More than one of the above
(E) None of the above

---

**Q7.** In which type of database is data stored in a TREE structure where each child has exactly ONE parent?
(A) Relational Database
(B) Network Database
(C) Hierarchical Database
(D) More than one of the above
(E) None of the above

---

**Q8.** In a Network Database, how many parents can a child record have?
(A) Exactly one
(B) Zero
(C) Multiple (more than one)
(D) More than one of the above
(E) None of the above

---

**Q9.** Which type of database is MOST WIDELY USED in banking, hospitals, and e-commerce?
(A) Hierarchical Database
(B) Network Database
(C) Relational Database
(D) More than one of the above
(E) None of the above

---

**Q10.** A Distributed Database is defined as:
(A) A database stored on a single computer but accessed by many users
(B) A database distributed across multiple physical locations that appears as one logical database
(C) A database that stores only distributed computing data
(D) More than one of the above
(E) None of the above

---

**Q11.** "Decentralized Database" as a type of database is:
(A) Another name for a relational database
(B) The same as a distributed database
(C) NOT a standard recognised type of database — "Distributed" is the correct term
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following is a key ADVANTAGE of DBMS over File System?
(A) DBMS stores all data in plain text files for easy access
(B) DBMS eliminates the need for any query language
(C) DBMS reduces data redundancy and ensures consistency
(D) More than one of the above
(E) None of the above

---

**Q13.** Data INTEGRITY in DBMS refers to:
(A) Making data available to all users without restriction
(B) Ensuring data is accurate, valid, and consistent through constraints
(C) Compressing data to save storage space
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following CORRECTLY distinguishes Database from DBMS?
(A) Database is the software; DBMS is the stored data
(B) Database is the collection of data; DBMS is the software managing it
(C) They are the same — Database and DBMS refer to the same thing
(D) More than one of the above
(E) None of the above

---

**Q15.** In which database model is IBM's IMS (Information Management System) an example?
(A) Relational
(B) Network
(C) Hierarchical
(D) More than one of the above
(E) None of the above

---

**Q16.** "Data Independence" in DBMS means:
(A) Data that cannot be shared with others
(B) Changes in storage structure don't require changes in application programs
(C) Data stored independently in different files
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following is NOT an example of DBMS software?
(A) MySQL
(B) PostgreSQL
(C) Microsoft Excel (as a standalone spreadsheet)
(D) More than one of the above
(E) None of the above

---

**Q18.** The MAIN reason hospitals switched from file-based systems to DBMS was:
(A) DBMS is cheaper to purchase
(B) File systems don't work on computers
(C) DBMS reduces inconsistency and enables multi-user access with security
(D) More than one of the above
(E) None of the above

---

**Q19.** A Network Database differs from a Hierarchical Database in that:
(A) Network DB uses tables while Hierarchical uses trees
(B) Network DB allows a record to have multiple parents; Hierarchical allows only one
(C) Network DB uses SQL; Hierarchical does not use any language
(D) More than one of the above
(E) None of the above

---

**Q20.** Which DBMS feature ensures that if a system crashes mid-transaction (e.g., during a bank transfer), the data is restored to its consistent state?
(A) Multi-user access
(B) Data redundancy
(C) Backup and Recovery (ACID transactions)
(D) More than one of the above
(E) None of the above

---

**Q21.** In the context of DBMS vs File System, which statement is TRUE?
(A) File System provides better security than DBMS
(B) File System allows easier concurrent access than DBMS
(C) DBMS provides better security and supports concurrent access; File System is weak in both
(D) More than one of the above
(E) None of the above

---

**Q22.** "Single-user access" is correctly classified as:
(A) A key FEATURE of DBMS
(B) An advantage of DBMS over network databases
(C) A LIMITATION of traditional file systems (not a feature of DBMS)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following statements about Relational Databases is CORRECT?
(A) They use a tree structure to organise data
(B) They use SQL to interact with data stored in tables
(C) They were the FIRST type of database invented (predating hierarchical)
(D) More than one of the above
(E) None of the above

---

**Q24.** Consider this scenario: A college stores student data in three separate department files — Examination, Hostel, and Library. Ravi's name appears in all three. When Ravi changes his name (marriage), only the Examination file is updated. The PROBLEM this illustrates is:
(A) Data security failure in DBMS
(B) Data inconsistency caused by redundancy in a file system
(C) A correct use of distributed databases
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is TRUE about the ANSI-SPARC three-level DBMS architecture?
(A) It has two levels: user level and storage level
(B) It has three levels: External, Conceptual, and Internal — providing data abstraction
(C) It is specific only to hierarchical databases
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Revolutionary Movements — Ghadar Party, Abhinav Bharat, Anushilan Samiti, Birsa Munda

---

**Q26.** Anushilan Samiti was founded in which year and city?
(A) 1905, Dhaka
(B) 1904, Pune
(C) 1902, Calcutta (Kolkata)
(D) More than one of the above
(E) None of the above

---

**Q27.** The Abhinav Bharat Society was founded by:
(A) Bal Gangadhar Tilak
(B) Vinayak Damodar Savarkar (V.D. Savarkar)
(C) Bipin Chandra Pal
(D) More than one of the above
(E) None of the above

---

**Q28.** The Ghadar Party was officially founded in:
(A) 1905, London
(B) 1913, San Francisco, USA
(C) 1915, Lahore
(D) More than one of the above
(E) None of the above

---

**Q29.** Who was the FOUNDER-PRESIDENT of the Ghadar Party?
(A) Har Dayal
(B) Kartar Singh Sarabha
(C) Sohan Singh Bhakna
(D) More than one of the above
(E) None of the above

---

**Q30.** The word "Ghadar" means:
(A) Freedom in Urdu
(B) Revolt/Mutiny/Revolution (in Urdu/Punjabi)
(C) Sacrifice in Punjabi
(D) More than one of the above
(E) None of the above

---

**Q31.** Birsa Munda belonged to which tribal community?
(A) Santhal
(B) Gond
(C) Munda
(D) More than one of the above
(E) None of the above

---

**Q32.** What does "ULGULAN" mean in the context of Birsa Munda's revolt?
(A) Sacred prayer in Mundari
(B) The Great Tumult / Great Revolt (in Mundari language)
(C) Forest rights movement
(D) More than one of the above
(E) None of the above

---

**Q33.** Birsa Munda was called "Dharti Abba." What does this mean?
(A) God of the forest
(B) Father of the Earth
(C) Son of the revolution
(D) More than one of the above
(E) None of the above

---

**Q34.** The Ghadar newspaper was significant because:
(A) It was the first newspaper in Hindi
(B) It was published in multiple languages (Punjabi, Urdu, Hindi, Gujarati) and smuggled into India
(C) It was published in London by the British government
(D) More than one of the above
(E) None of the above

---

**Q35.** Khudiram Bose was associated with which event and what was his age at the time of execution?
(A) Nasik Conspiracy (1909), 22 years
(B) Muzaffarpur Bomb Case (1908), 18 years
(C) Lahore Conspiracy (1929), 23 years
(D) More than one of the above
(E) None of the above

---

**Q36.** V.D. Savarkar was inspired by which foreign revolutionary movement when founding Abhinav Bharat?
(A) French Revolution's principles
(B) Giuseppe Mazzini's "Young Italy" movement
(C) Lenin's Russian Revolution
(D) More than one of the above
(E) None of the above

---

**Q37.** The Ghadar Mutiny of 1915 FAILED primarily because:
(A) The Ghadar leaders had no weapons
(B) British intelligence was informed by informers, leading to mass arrests
(C) The plan was announced publicly and British prepared in advance
(D) More than one of the above
(E) None of the above

---

**Q38.** Which legislation was a DIRECT result / legacy of Birsa Munda's Ulgulan (1899-1900)?
(A) Indian Forest Act (1878)
(B) Government of India Act (1909)
(C) Chota Nagpur Tenancy Act (1908) — protecting tribal land rights
(D) More than one of the above
(E) None of the above

---

**Q39.** Abhinav Bharat's Nasik Conspiracy Case (1909) involved the assassination of:
(A) The Governor-General of India
(B) A.M.T. Jackson, District Collector of Nasik
(C) Rand, the Plague Commissioner of Pune
(D) More than one of the above
(E) None of the above

---

**Q40.** Birsa Munda was born on 15 November 1875. This date is significant today because:
(A) It is observed as National Tribal Day
(B) It is celebrated as Jharkhand Foundation Day
(C) It is observed as the death anniversary of Birsa Munda
(D) More than one of the above
(E) None of the above

---

**Q41.** The Dhaka branch of Anushilan Samiti (founded 1906) was led by:
(A) Barindra Kumar Ghosh
(B) Sri Aurobindo
(C) Pulin Bihari Das
(D) More than one of the above
(E) None of the above

---

**Q42.** Savarkar's book on 1857 was historically significant because:
(A) It was the first history book written in Marathi
(B) It was the first work to call 1857 a "War of Independence" rather than a "mutiny"
(C) It praised British administration of India
(D) More than one of the above
(E) None of the above

---

**Q43.** Kartar Singh Sarabha of the Ghadar Party is notable for:
(A) Being the founder of the Ghadar newspaper
(B) Being one of the youngest revolutionaries hanged (age 19) in 1915, and being Bhagat Singh's inspiration
(C) Leading the Dhaka Anushilan Samiti
(D) More than one of the above
(E) None of the above

---

**Q44.** The Ghadar Party's membership was primarily drawn from:
(A) Urban intellectuals and lawyers in Calcutta
(B) Punjabi Sikh workers and former soldiers in North America
(C) Students studying in England at India House
(D) More than one of the above
(E) None of the above

---

**Q45.** V.D. Savarkar was sentenced to _____ years of imprisonment and sent to which jail?
(A) 25 years, Lahore Central Jail
(B) 50 years, Cellular Jail (Kala Pani), Andaman Islands
(C) Life imprisonment, Yeravada Jail, Pune
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following pairs is CORRECTLY matched?
(A) Ghadar Party — V.D. Savarkar
(B) Anushilan Samiti — Sohan Singh Bhakna
(C) Abhinav Bharat — V.D. Savarkar
(D) More than one of the above
(E) None of the above

---

**Q47.** The Ghadar Party was DISTINCTIVE among early revolutionary organisations because:
(A) It was based only in Calcutta and had no international connections
(B) It was an international organisation with a non-communal ideology — Sikhs, Hindus, Muslims together
(C) It worked only through peaceful, non-violent methods
(D) More than one of the above
(E) None of the above

---

**Q48.** Birsa Munda died on 9 June 1900. The official reason given was cholera. He was in:
(A) Andaman Cellular Jail
(B) Ranchi Jail
(C) Lahore Jail
(D) More than one of the above
(E) None of the above

---

**Q49.** Which statement about the Anushilan Samiti is INCORRECT?
(A) It was founded in Calcutta in 1902
(B) It used physical training organisations as a cover for revolutionary activities
(C) Its primary ideology was peaceful protest and petition to British government
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following statements about the Ghadar Party:
I. The Ghadar newspaper was published only in Punjabi language.
II. The party's ideology had no religious divisions — united Hindus, Sikhs, and Muslims.
III. The 1915 Ghadar Mutiny succeeded in its aim of inciting a mass uprising.
Which of the above statements is/are CORRECT?
(A) I and III only
(B) Only II
(C) II and III only
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
| 1 | (B) | DBMS = software that creates, manages, and controls access to databases |
| 2 | (C) | Database = structured, organised collection of related data |
| 3 | (B) | DBMS interfaces between user/application and the actual database |
| 4 | (C) | Google = search engine, NOT a DBMS |
| 5 | (C) | File system's biggest flaw = redundancy and inconsistency |
| 6 | (C) | Multi-user concurrent access is a FEATURE; single-user is a limitation of file systems |
| 7 | (C) | Hierarchical = tree structure; each child has EXACTLY one parent |
| 8 | (C) | Network DB = graph; a child can have MULTIPLE parents |
| 9 | (C) | Relational DB is the most widely used; powers banks, hospitals, e-commerce |
| 10 | (B) | Distributed DB = multiple physical locations, single logical appearance |
| 11 | (C) | "Decentralized" is NOT a standard type; correct term = "Distributed" |
| 12 | (C) | DBMS's core advantage = reduced redundancy + ensured consistency |
| 13 | (B) | Integrity = accurate, valid, consistent data through constraints |
| 14 | (B) | Database = data; DBMS = software managing that data |
| 15 | (C) | IBM IMS = Hierarchical database system |
| 16 | (B) | Data independence = storage changes don't affect applications |
| 17 | (C) | Excel alone is a spreadsheet application, not a DBMS |
| 18 | (C) | Main reasons for switching = multi-user access, consistency, security |
| 19 | (B) | Network: multiple parents allowed; Hierarchical: exactly one parent |
| 20 | (C) | Backup & Recovery + ACID transactions ensure crash recovery |
| 21 | (C) | DBMS is superior in security and concurrent access vs file system |
| 22 | (C) | Single-user = limitation of file systems; MULTI-user is DBMS feature |
| 23 | (B) | Relational DB uses SQL; tables are its structure; NOT the oldest type |
| 24 | (B) | Illustrates data inconsistency caused by file system redundancy |
| 25 | (B) | ANSI-SPARC = 3 levels: External, Conceptual, Internal |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Anushilan Samiti = 1902, Calcutta, P.N. Mitra |
| 27 | (B) | Abhinav Bharat = V.D. Savarkar, 1904, Nasik |
| 28 | (B) | Ghadar Party = 1913, San Francisco, USA |
| 29 | (C) | Sohan Singh Bhakna = founder-president; Har Dayal was intellectual leader |
| 30 | (B) | Ghadar = revolt/mutiny/revolution in Urdu-Punjabi |
| 31 | (C) | Birsa Munda = Munda tribal community, Chota Nagpur |
| 32 | (B) | Ulgulan = "the great tumult" or "great revolt" in Mundari |
| 33 | (B) | Dharti Abba = Father of the Earth |
| 34 | (B) | Published in multiple languages; distributed free; smuggled into India |
| 35 | (B) | Muzaffarpur Bomb Case, 1908; Khudiram hanged at age 18 |
| 36 | (B) | Inspired by Mazzini's "Young Italy" movement |
| 37 | (B) | Failed due to British intelligence + informers revealing the plan |
| 38 | (C) | Chota Nagpur Tenancy Act 1908 = direct legacy of Birsa's revolt |
| 39 | (B) | A.M.T. Jackson, District Collector of Nasik, assassinated 1909 |
| 40 | (B) | 15 November = Jharkhand Foundation Day (Birsa's birthday) |
| 41 | (C) | Pulin Bihari Das founded Dhaka Anushilan Samiti in 1906 |
| 42 | (B) | First work to call 1857 a "War of Independence" — not a mutiny |
| 43 | (B) | Hanged at 19 in 1915; Bhagat Singh's idol |
| 44 | (B) | Punjabi Sikh workers and former soldiers in North America |
| 45 | (B) | 50 years; Cellular Jail (Kala Pani), Andaman Islands |
| 46 | (C) | Only C is correct: Abhinav Bharat = Savarkar |
| 47 | (B) | International + non-communal ideology = Ghadar's distinctiveness |
| 48 | (B) | Birsa Munda died in Ranchi Jail, 9 June 1900 |
| 49 | (C) | Statement C is WRONG — Anushilan Samiti was NOT peaceful; it was revolutionary |
| 50 | (B) | Only Statement II is correct; Ghadar newspaper was multilingual (not Punjabi only); 1915 mutiny FAILED |

---
---

# 🔁 DAY 36 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — DBMS Basics

### One-Liner Definitions:
```
DATA:     Raw, unprocessed facts that have no meaning by themselves.
DATABASE: Structured, organised collection of RELATED data stored electronically.
DBMS:     Software that creates, manages, and controls access to a database.

FORMULA:  Database = CONTAINER of data
          DBMS = SOFTWARE that manages the container
          
DBMS = INTERFACE between USER and DATABASE (never forget this!)
```

### Google ≠ DBMS (The Golden Trap):
```
Google = Search Engine (crawls web, returns results)
Google ≠ DBMS (does NOT manage a structured, controlled database)

If exam asks "Which is NOT a DBMS?" → Google is the answer!
```

### DBMS vs File System — 5 Key Differences:
```
File System PROBLEM → DBMS SOLUTION:
1. High redundancy    → Reduced redundancy (central storage)
2. Inconsistency      → Consistency (one update = everywhere)
3. No security        → Strong security (role-based access)
4. Single-user only   → Multi-user concurrent access
5. No integrity check → Data integrity via constraints
```

### Database Types — 4 + 1 Trap:
```
STANDARD TYPES:
  1. Relational    → Tables + SQL (MySQL, Oracle) — MOST COMMON
  2. Hierarchical  → Tree, ONE parent per child (IBM IMS)
  3. Network       → Graph, MULTIPLE parents allowed (IDMS)
  4. Distributed   → Multiple locations, ONE logical database

TRAP: "Decentralized" = NOT a standard type! Correct = "Distributed"

KEY DISTINCTION:
  Hierarchical vs Network:
  → Hierarchical: child has EXACTLY 1 parent (like a family tree)
  → Network: child can have MULTIPLE parents (more flexible)
```

### DBMS Features — 7 to Remember:
```
1. Reduced Redundancy    — data stored ONCE
2. Data Consistency      — change once, reflects everywhere
3. Data Security         — role-based access control
4. Multi-user Access     — concurrent users, no conflict
5. Data Integrity        — constraints ensure valid data
6. Data Independence     — storage changes don't break apps
7. Backup & Recovery     — ACID transactions, crash safety
```

### Common PYQ Traps — One-Liners:
```
✅ Single-user access = LIMITATION (not feature) of file systems
✅ Google = NOT a DBMS
✅ "Decentralized" = NOT a standard DB type (use "Distributed")
✅ Database ≠ DBMS (data vs software)
✅ Hierarchical DB = each child has exactly ONE parent
✅ Network DB = child can have MULTIPLE parents
✅ Relational DB uses SQL (not hierarchical or network)
```

---

## ⚡ RAPID FIRE — Revolutionary Movements

### Movement-Year-Place-Founder Grid:
```
MOVEMENT          YEAR    PLACE         FOUNDER(S)
Anushilan Samiti  1902    Calcutta      Pramathanath Mitra; Barindra Ghosh
Dhaka Anushilan   1906    Dhaka         Pulin Bihari Das
Abhinav Bharat    1904    Nasik         V.D. Savarkar
Ghadar Party      1913    San Francisco Sohan Singh Bhakna
Ghadar newspaper  Nov'13  San Francisco Har Dayal (edited)
```

### Key Persons — One-Line Memory:
```
V.D. Savarkar:    Abhinav Bharat; coined "1857 = War of Independence"; 50 yrs Kala Pani
Sohan Singh Bhakna: Ghadar Party founder-president (San Francisco, 1913)
Har Dayal:        Ghadar's brain; deported by USA; edited Ghadar newspaper
Kartar Singh Sarabha: Ghadar; hanged at 19 (1915); Bhagat Singh's idol
Khudiram Bose:    Anushilan-linked; Muzaffarpur bomb (1908); hanged at 18
Pulin Bihari Das: Led Dhaka Anushilan Samiti (1906)
Birsa Munda:      Munda tribe; Ulgulan (1899-1900); "Dharti Abba"; died 1900, age 25
```

### Birsa Munda Key Facts:
```
Born:     15 November 1875 → Jharkhand Foundation Day!
Region:   Chota Nagpur (Jharkhand)
Revolt:   Ulgulan = 1899-1900
Captured: 3 February 1900
Died:     9 June 1900, Ranchi Jail (age 25)
Called:   "Dharti Abba" (Father of the Earth)
Legacy:   Chota Nagpur Tenancy Act (1908) — tribal land protection
Symbol:   Portrait in Central Hall of Indian Parliament
```

### Ghadar Party Key Facts:
```
Founded:    1913, San Francisco, USA
Newspaper:  "Ghadar" — multilingual (Punjabi, Urdu, Hindi, Gujarati, Pashto)
First issue: 1 November 1913
Tagline:    "Angrezi Raj ka Dushman" (Enemy of British Rule)
1915 Mutiny: FAILED — informers betrayed the plan
42 hanged including Kartar Singh Sarabha (age 19)
Bhagat Singh's inspiration: Kartar Singh Sarabha
Distinctive: International + non-communal (Sikh + Hindu + Muslim together)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **DBMS = Interface**: Database = container of data; DBMS = software managing it; DBMS sits BETWEEN user and database; Google is NOT a DBMS (search engine).
2. **DB Types trap**: Hierarchical = ONE parent per child (tree); Network = MULTIPLE parents (graph); "Decentralized" is NOT a standard type — correct term is "Distributed."
3. **File System vs DBMS**: File system has redundancy, inconsistency, no security, single-user; DBMS solves all — reduced redundancy, consistency, multi-user, security, integrity.
4. **Ghadar Party (1913)**: San Francisco; Sohan Singh Bhakna (founder); Har Dayal (intellect); Kartar Singh Sarabha (youngest martyr, 19); 1915 mutiny FAILED; non-communal + international.
5. **Birsa Munda**: Munda tribe; Ulgulan 1899-1900; "Dharti Abba"; died Ranchi Jail 1900 (age 25); legacy = CNT Act 1908; 15 Nov birthday = Jharkhand Foundation Day.

---

## 📅 DAY 37 PREVIEW — What's Coming Next:
**CS**: ER Model (Entity-Relationship Model) — Entities, Attributes, Relationships, ER Diagrams, Weak Entities, Cardinality (1:1, 1:N, M:N), Participation Constraints
**GS**: Indian Polity — Fundamental Rights (Articles 12-35): Right to Equality, Right to Freedom, Right Against Exploitation, Right to Freedom of Religion, Cultural & Educational Rights, Right to Constitutional Remedies

---

*🚀 Day 36 of 170 — You're 21% through the journey. The DBMS section builds up every day — master the basics today to ace the advanced topics tomorrow. Stay consistent!*
