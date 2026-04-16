# 📅 BPSC TRE 4.0 — DAY 36
## CS: DBMS — Concepts, Types & Features | GS: Ghadar Party, Abhinav Bharat & Revolutionary Nationalism

> **Target:** Score 23+/25 in CS | 23+/25 in GS | **Overall Target: TOP 50 RANK**
> **Phase:** Phase 1 — Foundation | **Week 6**
> **Date:** Day 36 of 170

---

# ═══════════════════════════════════════
# 💻 PART A: COMPUTER SCIENCE
# DBMS — Introduction, Types & Features
# ═══════════════════════════════════════

---

## 🧠 CONCEPT 1: What is a Database?

A **Database** is an organized, structured collection of interrelated data that can be stored, accessed, updated, and managed efficiently.

### Simple Analogy:
```
LIBRARY ANALOGY:
┌──────────────────────────────────────┐
│  Library = DATABASE                  │
│  Books   = DATA (records/rows)       │
│  Catalog = METADATA (data about data)│
│  Sections= TABLES                    │
│  Librarian = DBMS Software           │
└──────────────────────────────────────┘
```

### Key Distinction: Database vs DBMS

| Term | Meaning |
|------|---------|
| **Database** | The actual stored data (collection of data) |
| **DBMS** | Software that manages and controls the database |
| **Examples of DBMS** | MySQL, Oracle, PostgreSQL, MS Access, SQLite |
| **NOT a DBMS** | Google (it's a Search Engine), Excel (it's a Spreadsheet) |

> ⚠️ **PYQ TRAP:** "Which of the following is NOT a DBMS?" → Google is NOT a DBMS. It is a **search engine**.

---

## 🧠 CONCEPT 2: What is a DBMS?

**DBMS (Database Management System)** = Software that acts as an **interface** between the user/application and the physical database.

```
┌─────────────────────────────────────────────────────┐
│                    USER / APPLICATION                │
└─────────────────────────┬───────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────┐
│                    DBMS SOFTWARE                     │
│         (MySQL, Oracle, PostgreSQL, etc.)            │
│   ┌──────────────────────────────────────────────┐  │
│   │  Query Processor | Security | Concurrency    │  │
│   │  Transaction Manager | Recovery Manager      │  │
│   └──────────────────────────────────────────────┘  │
└─────────────────────────┬───────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────┐
│              PHYSICAL DATABASE (Disk)                │
│         (Actual data files stored on HDD/SSD)       │
└─────────────────────────────────────────────────────┘
```

**DBMS acts as interface between:** Database Application ↔ Database

---

## 🧠 CONCEPT 3: DBMS vs File System

This is a HIGH-FREQUENCY comparison in BPSC TRE!

```
FILE SYSTEM PROBLEMS:              HOW DBMS SOLVES IT:
─────────────────────              ──────────────────────
Data Redundancy (duplicates)   →   Minimum Redundancy
Data Inconsistency             →   Data Consistency
No Data Security               →   High Security (roles/passwords)
No Multi-user Access           →   Multi-user Concurrent Access
No Backup/Recovery             →   Built-in Backup & Recovery
Data Dependence               →   Data Independence
No Query Language             →   SQL (Structured Query Language)
```

### Features of DBMS (MEMORIZE ALL):
1. **Minimum data redundancy** — same data not stored multiple times
2. **High data security** — access control, encryption
3. **Multi-user access** — many users can access simultaneously
4. **Data consistency** — same data everywhere
5. **Data integrity** — valid data only
6. **Data independence** — change structure without affecting programs
7. **Concurrency control** — handles simultaneous transactions
8. **Backup and recovery** — protects against data loss
9. **Query language (SQL)** — easy data retrieval

> ⚠️ **PYQ TRAP — VERY IMPORTANT:** "Which is NOT a feature of DBMS?"
> → **Single-user access only** = NOT a feature (DBMS supports MULTI-USER access)
> → "Increases redundancy" = NOT a feature (DBMS REDUCES redundancy)

---

## 🧠 CONCEPT 4: Types of Database Models

```
                    DATABASE MODELS
                         │
         ┌───────────────┼────────────────┐
         ▼               ▼                ▼
   HIERARCHICAL      NETWORK          RELATIONAL
      MODEL           MODEL             MODEL
         │               │                │
   Tree structure   Graph structure   Table structure
   Parent-Child     Many-to-Many      Most widely used
   relationship     relationships     (MySQL, Oracle)
   
   e.g., IBM IMS   e.g., IDS         e.g., MySQL
         │
         └── Also: OBJECT-ORIENTED, DISTRIBUTED, NoSQL
```

### Four Classical Database Models — Detailed:

#### 1. Hierarchical Model
```
                    ROOT (Company)
                   /              \
           DEPT-A                  DEPT-B
          /      \                /      \
      EMP-1    EMP-2          EMP-3    EMP-4

Structure: TREE (Parent → Child, one-to-many)
Limitation: Cannot represent many-to-many relationships
Example: IBM's IMS (Information Management System)
```

#### 2. Network Model
```
       STUDENT ←──────→ COURSE
          ↕                ↕
       PROJECT ←──────→ FACULTY

Structure: GRAPH (records = nodes, relationships = edges)
Advantage: Can represent many-to-many relationships
Limitation: Complex, difficult to modify
Standard: CODASYL (Conference on Data Systems Languages)
```

#### 3. Relational Model (MOST IMPORTANT FOR EXAM)
```
STUDENT TABLE:
┌────────┬──────────┬──────┬──────────┐
│ Stu_ID │ Name     │ Age  │ Course   │
├────────┼──────────┼──────┼──────────┤
│  101   │ Rahul    │  20  │  BCA     │
│  102   │ Priya    │  21  │  MCA     │
│  103   │ Amit     │  19  │  BSc CS  │
└────────┴──────────┴──────┴──────────┘

Key Terms:
  Relation  = TABLE (the whole structure)
  Tuple     = ROW (one record, e.g., 101, Rahul, 20, BCA)
  Attribute = COLUMN (e.g., Name, Age)
  Domain    = Set of valid values for an attribute
  Degree    = Number of attributes (columns) in a relation
  Cardinality = Number of tuples (rows) in a relation
```

#### 4. Object-Oriented Model
- Data stored as **objects** (like in OOP)
- Supports complex data types, inheritance
- Used in modern applications

#### 5. Distributed Database
```
┌─────────────────────────────────────────┐
│         DISTRIBUTED DATABASE            │
│                                         │
│  [Node 1: Delhi] ←──→ [Node 2: Mumbai] │
│         ↕                    ↕          │
│  [Node 3: Chennai] ←→ [Node 4: Kolkata]│
│                                         │
│  Data DISTRIBUTED across multiple       │
│  physical locations / machines          │
│  BUT logically appears as ONE database  │
└─────────────────────────────────────────┘

NOT called "Decentralized Database"!
```

> ⚠️ **PYQ TRAP:** Database where data is stored at multiple locations = **DISTRIBUTED** (NOT Decentralized, NOT Parallel)

---

## 🧠 CONCEPT 5: Data Independence (HIGH PRIORITY)

**Data Independence** = Ability to change the database schema at one level without affecting the schema at the next higher level.

```
THREE-SCHEMA ARCHITECTURE (ANSI/SPARC):

┌────────────────────────────────────────────┐
│         EXTERNAL LEVEL (View Level)        │  ← User view
│   What each user/group of users sees       │
├────────────────────────────────────────────┤
│       CONCEPTUAL LEVEL (Logical Level)     │  ← DBA view
│   Entire database structure (tables, etc.) │
├────────────────────────────────────────────┤
│       INTERNAL LEVEL (Physical Level)      │  ← Storage view
│   How data is actually stored on disk      │
└────────────────────────────────────────────┘

TWO TYPES OF DATA INDEPENDENCE:

1. LOGICAL Data Independence:
   → Change CONCEPTUAL schema without affecting EXTERNAL schema
   → e.g., Add a new column to a table → existing user views unaffected

2. PHYSICAL Data Independence:
   → Change INTERNAL schema without affecting CONCEPTUAL schema
   → e.g., Change storage from HDD to SSD → logical structure unchanged
   → EASIER to achieve than logical data independence
```

> 💡 **Key Fact:** Physical data independence is EASIER to achieve. Logical data independence is HARDER.

---

## 🧠 CONCEPT 6: Important DBMS Terminology (Must Memorize)

```
┌─────────────────┬──────────────────────────────────────────────┐
│ TERM            │ MEANING                                       │
├─────────────────┼──────────────────────────────────────────────┤
│ Metadata        │ Data ABOUT data (e.g., table name, columns)  │
│ Data Dictionary │ Repository of metadata (also: System Catalog)│
│ Schema          │ Structure/design of the database             │
│ Instance        │ Actual data at a specific point in time      │
│ Query           │ Request for data (usually in SQL)            │
│ DDL             │ Data Definition Language (CREATE, DROP, ALTER)│
│ DML             │ Data Manipulation Language (INSERT, UPDATE,  │
│                 │ DELETE, SELECT)                              │
│ DCL             │ Data Control Language (GRANT, REVOKE)        │
│ TCL             │ Transaction Control Language (COMMIT,        │
│                 │ ROLLBACK, SAVEPOINT)                         │
└─────────────────┴──────────────────────────────────────────────┘
```

> ⚠️ **PYQ FACT:** **Metadata** = Information about data = Data Dictionary stores it.

---

## 🧠 CONCEPT 7: Roles in DBMS Environment

```
┌──────────────────┬────────────────────────────────────────────┐
│ ROLE             │ RESPONSIBILITIES                           │
├──────────────────┼────────────────────────────────────────────┤
│ DBA              │ Database Administrator — manages entire    │
│ (Database        │ database, creates schemas, grants access,  │
│ Administrator)   │ ensures security & performance            │
├──────────────────┼────────────────────────────────────────────┤
│ Database Designer│ Designs schema, ER diagrams, normalization │
├──────────────────┼────────────────────────────────────────────┤
│ End User         │ Queries/updates data (using applications) │
├──────────────────┼────────────────────────────────────────────┤
│ Application      │ Writes programs that interact with DB      │
│ Programmer       │                                            │
└──────────────────┴────────────────────────────────────────────┘
```

> 💡 **DBA = Most powerful role in DBMS** — has all privileges.

---

## 🧠 CONCEPT 8: NoSQL Databases (Modern DBMS — Brief)

```
NOSQL (Not Only SQL) — for BIG DATA / Unstructured data

┌─────────────┬─────────────────┬───────────────────────────┐
│ TYPE        │ STRUCTURE       │ EXAMPLE                   │
├─────────────┼─────────────────┼───────────────────────────┤
│ Key-Value   │ Key → Value     │ Redis, DynamoDB            │
│ Document    │ JSON documents  │ MongoDB, CouchDB           │
│ Column      │ Column families │ Cassandra, HBase           │
│ Graph       │ Nodes + Edges   │ Neo4j                      │
└─────────────┴─────────────────┴───────────────────────────┘

Traditional RDBMS: MySQL, Oracle, PostgreSQL, MS SQL Server
```

---

## 🎯 QUICK REVISION FLASH CARDS (CS)

```
┌─────────────────────────────────────────────────────┐
│ FLASH CARD 1: Interface role of DBMS               │
│ DBMS = Interface between APPLICATION and DATABASE  │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ FLASH CARD 2: What DBMS is NOT                     │
│ DBMS does NOT provide SINGLE-USER access only      │
│ → It provides MULTI-USER concurrent access         │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ FLASH CARD 3: Google is NOT a DBMS                 │
│ Google = Search Engine                             │
│ MySQL, Oracle, PostgreSQL = DBMS                   │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ FLASH CARD 4: Key relational model terms           │
│ Relation = Table | Tuple = Row | Attribute = Column│
│ Domain = Valid values | Metadata = Data about data │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ FLASH CARD 5: Distributed Database               │
│ Data stored at multiple locations = DISTRIBUTED   │
│ NOT "Decentralized", NOT "Parallel"                │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ FLASH CARD 6: DDL vs DML                          │
│ DDL = CREATE, DROP, ALTER (Structure)             │
│ DML = SELECT, INSERT, UPDATE, DELETE (Data)       │
└─────────────────────────────────────────────────────┘
```

---

# ═══════════════════════════════════════════════
# 📜 PART B: GENERAL STUDIES (HISTORY)
# Ghadar Party, Abhinav Bharat & Revolutionary Nationalism
# ═══════════════════════════════════════════════

---

## 🧠 CONCEPT 9: Background — Rise of Revolutionary Nationalism

After the **Moderate Phase** (INC founded 1885) and the **Extremist Phase** (Lal-Bal-Pal), a third strand of the freedom struggle emerged — **Revolutionary Nationalism** — where young patriots turned to **armed revolution** against British rule.

```
TIMELINE OF REVOLUTIONARY NATIONALISM:
─────────────────────────────────────
1897  → Chapekar Brothers assassinate British officers (Pune)
1899  → Abhinav Bharat society precursor activities
1904  → Abhinav Bharat Society founded (Nasik)
1905  → Partition of Bengal → massive radicalisation
1906  → Yugantar newspaper founded (Bengal)
1907  → Surat Split — Moderates vs Extremists
1907  → Ghadar of Rawalpindi (Sikh soldiers inspired)
1913  → Ghadar Party founded (USA/Canada)
1914  → World War I → Ghadar activists try to return to India
1915  → Komagata Maru tragedy + February Conspiracy attempt
```

---

## 🧠 CONCEPT 10: Abhinav Bharat Society (1904)

```
┌─────────────────────────────────────────────────────────┐
│               ABHINAV BHARAT SOCIETY                   │
├─────────────────────────────────────────────────────────┤
│ Founded:    1904 (some sources say 1899 as Mitra Mela) │
│ Founder:    Vinayak Damodar Savarkar                   │
│                    (Veer Savarkar)                     │
│ Location:   Nasik (Maharashtra)                        │
│ Inspired by: Giuseppe Mazzini's "Young Italy"         │
│ Full name:  "Abhinav Bharat" (Young India/New India)  │
│ Nature:     Secret revolutionary society               │
└─────────────────────────────────────────────────────────┘
```

### Key Facts About Abhinav Bharat:

**Veer Savarkar (1883–1966):**
- Full name: **Vinayak Damodar Savarkar**
- Born: Bhagur, Nashik district (Maharashtra)
- Founded **Mitra Mela** in 1899 (secret revolutionary group)
- Renamed it **Abhinav Bharat** in 1904
- Went to London (1906) on a scholarship — **India House** activities
- Wrote ***"The Indian War of Independence 1857"*** — British **banned** this book BEFORE publication
- Organized supply of **20 Browning pistols** smuggled from Paris to India
- The **Nasik Conspiracy Case (1909)**: Jackson, Collector of Nasik, was assassinated by Anant Laxman Kanhere (Abhinav Bharat member)
- Savarkar was **transported for life twice** (double life transportation = 50 years!) to **Andaman (Cellular Jail/Kala Pani)**
- Also wrote ***"Hindutva"*** (1923)

```
SAVARKAR'S BOOK: "The Indian War of Independence 1857"
┌──────────────────────────────────────────────────────┐
│ → Described 1857 revolt as a PLANNED WAR OF          │
│   INDEPENDENCE (not just a Sepoy Mutiny)             │
│ → British BANNED this book even BEFORE publication   │
│ → One of few books banned before being published!    │
│ → Significance: Changed narrative from "mutiny"      │
│   to "first war of independence"                     │
└──────────────────────────────────────────────────────┘
```

### Other Abhinav Bharat Notable Members:
- **Nasik Conspiracy**: Anant Kanhere shot Collector A.M.T. Jackson (1909)
- This case led to Savarkar's arrest and transportation

---

## 🧠 CONCEPT 11: Ghadar Party (1913) — VERY HIGH FREQUENCY

```
┌─────────────────────────────────────────────────────────┐
│                    GHADAR PARTY                        │
├─────────────────────────────────────────────────────────┤
│ Founded:    1913                                       │
│ Location:   San Francisco, USA (also active in Canada) │
│ Founder:    Lala Har Dayal (main ideologue)           │
│             Sohan Singh Bhakna (first president)      │
│ Newspaper:  "Ghadar" (meaning: Revolt/Revolution)    │
│ Language:   Published in Urdu, Punjabi, Hindi,       │
│             Gurmukhi, English                         │
│ Members:    Mostly Punjabi Sikhs settled in           │
│             USA & Canada (expatriate Indians)         │
└─────────────────────────────────────────────────────────┘
```

### Key Facts — Ghadar Party:

**1. Founders and Leaders:**
```
LALA HAR DAYAL:
→ Ideological founder of Ghadar Party
→ Educated at Oxford (Rhodes Scholar)
→ Resigned ICS to join revolutionary movement
→ Taught at Stanford University
→ Founded Ghadar Party in San Francisco, 1913
→ Deported from USA by British pressure (1914)
→ Later took refuge in Sweden, Germany
→ Believed in armed revolution to overthrow British rule

SOHAN SINGH BHAKNA:
→ First President of Ghadar Party
→ Came from agricultural background
→ Gurditt Singh (Komagata Maru incident) was inspired by Ghadar
```

**2. The Ghadar Newspaper:**
```
"GHADAR" NEWSPAPER:
→ Founded: 1913
→ Languages: Urdu, Punjabi, Gurmukhi, Hindi, English
→ Published from: San Francisco (later Stockton)
→ First issue: November 1, 1913
→ Motto: "Angrezi Raj ka Dushman" (Enemy of British Rule)
→ Distributed FREE to Indians worldwide
→ Had masthead slogan: "Wanted — Brave Soldiers to overthrow British rule"
```

**3. 1914–1915 — The Failed Uprising:**
```
WORLD WAR I OPPORTUNITY:
→ With Britain at war, Ghadaris saw it as chance to revolt
→ Thousands of Ghadaris boarded ships from USA/Canada
  to return to India and start revolution
→ KOMAGATA MARU (1914):
   - Ship carrying 376 Punjabi immigrants
   - Vancouver refused entry → kept on ship for 2 months
   - Returned to India → British fired at ship in Budge Budge (Calcutta)
   - 20 killed, rest arrested
→ FEBRUARY 1915 CONSPIRACY:
   - Plan to mutiny in British Indian Army
   - Betrayed by informers → British crushed it
   - Massive arrests, deportations, executions
→ Kartar Singh Sarabha: Youngest Ghadar martyr (19 years old)
   - Hanged November 16, 1915
   - Bhagat Singh considered him his idol!
```

**4. Why Ghadar Party Failed:**
```
REASONS FOR FAILURE:
1. Betrayal by informers (British intelligence was strong)
2. British were well-prepared in 1915
3. Lack of coordination between different groups
4. Weapons promised from Germany (via Berlin Committee) 
   were intercepted
5. Indian soldiers did not mass-revolt as expected
```

---

## 🧠 CONCEPT 12: Bengal Revolutionaries — Anushilan Samiti & Yugantar

```
REVOLUTIONARY GROUPS IN BENGAL:
┌────────────────────┬────────────────────────────────────┐
│ ORGANIZATION       │ KEY FACTS                          │
├────────────────────┼────────────────────────────────────┤
│ ANUSHILAN SAMITI   │ Founded: 1902 in Calcutta          │
│                    │ Founders: Satish Chandra Bose,      │
│                    │           P. Mitter                 │
│                    │ Inspired: Bal Gangadhar Tilak       │
│                    │ Activities: Physical training,      │
│                    │   bomb-making, revolutionary acts  │
│                    │ Dhaka branch (1906): Pulin Das     │
├────────────────────┼────────────────────────────────────┤
│ YUGANTAR           │ Newspaper founded 1906, Calcutta   │
│                    │ Editors: Barindra Kumar Ghosh,     │
│                    │          Bhupendranath Dutta        │
│                    │ (Barindra = Aurobindo's brother)   │
│                    │ Published revolutionary content    │
├────────────────────┼────────────────────────────────────┤
│ ALIPORE BOMB CASE  │ 1908 — Khudiram Bose &            │
│ (Muzaffarpur)      │ Prafulla Chaki threw bombs at     │
│                    │ Magistrate Kingsford's carriage   │
│                    │ → Wrong target (killed two         │
│                    │   English ladies)                 │
│                    │ Khudiram Bose: Hanged at age 18   │
│                    │ Prafulla Chaki: Shot himself      │
└────────────────────┴────────────────────────────────────┘
```

---

## 🧠 CONCEPT 13: Khudiram Bose — The Young Martyr

```
KHUDIRAM BOSE (1889–1908):
┌──────────────────────────────────────────────────────┐
│ Born: December 3, 1889, Medinipur, Bengal           │
│ Age at execution: 18 years (youngest revolutionary  │
│                   martyr of Bengal)                 │
│                                                     │
│ MUZAFFARPUR BOMB CASE (April 30, 1908):             │
│ → Target: Kingsford (magistrate who harshly         │
│   sentenced revolutionaries)                        │
│ → Threw bomb at his carriage — but WRONG carriage!  │
│ → Two English women (Mrs. Kennedy & daughter) died  │
│ → Khudiram arrested, Prafulla Chaki killed himself │
│ → Khudiram hanged: August 11, 1908                  │
│ → Became symbol of youthful martyrdom              │
│ → Tilak's newspaper Kesari condemned the hanging   │
└──────────────────────────────────────────────────────┘
```

---

## 🧠 CONCEPT 14: Bhagat Singh, Rajguru, Sukhdev — The Supreme Sacrifice

```
THE LAHORE CONSPIRACY CASE:
────────────────────────────────────────────────────────
CONTEXT:
→ October 30, 1928: Lala Lajpat Rai led protest 
  against Simon Commission
→ Police lathi-charged → Lala Lajpat Rai severely beaten
→ Died November 17, 1928 (injuries aggravated)
→ Bhagat Singh, Sukhdev, Rajguru vowed to avenge

SAUNDERS MURDER (December 17, 1928):
→ Plan was to kill Superintendent Scott
→ Mistakenly shot J.P. Saunders (Deputy SP) instead
→ Bhagat Singh (main shooter), Chandrashekhar Azad (backup)

ASSEMBLY BOMB CASE (April 8, 1929):
→ Bhagat Singh + B.K. Dutt threw bombs in Central Legislature
→ Deliberately did NOT kill anyone (smoke bombs)
→ Shouted "Inquilab Zindabad!" and "Down with Imperialism!"
→ Voluntarily surrendered to prove a point
→ Slogan "Inquilab Zindabad" = coined by Maulana Hasrat Mohani
  (Bhagat Singh popularised it)

EXECUTION:
→ Bhagat Singh, Rajguru, Sukhdev: Hanged March 23, 1931
→ Lahore Central Jail
→ Originally scheduled for March 24 — hanged one day EARLY
→ Age of Bhagat Singh at hanging: 23 years
```

```
BHAGAT SINGH — KEY FACTS:
┌─────────────────────────────────────────────────────┐
│ Born: September 27/28, 1907, Lyallpur (now Pakistan)│
│ Organisations:                                      │
│  → Naujawan Bharat Sabha (1926) — founded by him    │
│  → Hindustan Socialist Republican Association (HSRA)│
│    [formerly HSRA = Hindustan Republican Association]│
│ Influenced by: Kartar Singh Sarabha (Ghadar Party) │
│                Bhagat Singh's idol!                 │
│ Jail diary: Mentioned Lenin, Marx                  │
│ Hunger strike: 116 days (died in jail: Jatin Das)  │
│ Stated: "I am an atheist"                          │
└─────────────────────────────────────────────────────┘
```

---

## 🧠 CONCEPT 15: Chandrashekhar Azad — "Azad" (Free)

```
CHANDRASHEKHAR AZAD (1906–1931):
┌─────────────────────────────────────────────────────┐
│ Born: July 23, 1906, Bhavra (Madhya Pradesh)       │
│ Real name: Chandrashekhar Tiwari                   │
│ "Azad" = he renamed himself "Azad" (free)          │
│                                                     │
│ Key Events:                                         │
│ → Non-Cooperation Movement: Arrested age 15        │
│   Magistrate: "Your name?" — He said "Azad"        │
│   "Father's name?" — "Swatantrata (Freedom)"       │
│   "Address?" — "Jail" → Publicly flogged           │
│ → Kakori Train Robbery: August 9, 1925            │
│ → Assisting Bhagat Singh in Saunders murder (1928) │
│ → Death: Alfred Park, Allahabad, February 27, 1931│
│   Surrounded by police → shot himself with last    │
│   bullet to keep his promise of never being caught │
│ Vow: "I will never be arrested by the British"    │
│       — kept his promise till the end             │
└─────────────────────────────────────────────────────┘
```

---

## 🧠 CONCEPT 16: Kakori Train Robbery (1925)

```
KAKORI TRAIN ROBBERY (August 9, 1925):
────────────────────────────────────────
Place: Near Kakori village, Uttar Pradesh (near Lucknow)
Organization: Hindustan Republican Association (HRA)
Leader: Ram Prasad Bismil (planned the operation)
Participants: Ram Prasad Bismil, Ashfaqullah Khan,
              Chandrashekhar Azad, Roshan Singh,
              Rajendra Lahiri, and others

What happened:
→ British government's treasury (money) train was looted
→ Aim: Funds for revolutionary activities
→ Rs. 8,000 taken from the train

Consequences:
→ Massive crackdown — 40+ arrested
→ RAM PRASAD BISMIL: Hanged December 19, 1927 (Gorakhpur jail)
→ ASHFAQULLAH KHAN: Hanged December 19, 1927 (Faizabad jail)
→ ROSHAN SINGH: Hanged December 19, 1927
→ RAJENDRA LAHIRI: Hanged December 17, 1927 (2 days early)
→ Chandrashekhar Azad: ESCAPED (never caught)

Famous: "Sarfaroshi ki Tamanna" — poem by Bismil
```

---

## 🎯 QUICK REVISION FLASH CARDS (GS/History)

```
┌────────────────────────────────────────────────────────┐
│ FLASH CARD 1: Ghadar Party                           │
│ Founded: 1913 | Place: San Francisco, USA            │
│ Founders: Lala Har Dayal + Sohan Singh Bhakna        │
│ Paper: "Ghadar" | President: Sohan Singh Bhakna      │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│ FLASH CARD 2: Abhinav Bharat                         │
│ Founded: 1904 | Place: Nasik                         │
│ Founder: Veer Savarkar                               │
│ Inspired by: Mazzini's "Young Italy"                 │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│ FLASH CARD 3: Khudiram Bose                          │
│ Age at hanging: 18 years | Year: 1908               │
│ Case: Muzaffarpur Bomb Case                          │
│ Target: Kingsford (missed — killed two English women)│
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│ FLASH CARD 4: Bhagat Singh                           │
│ Hanged: March 23, 1931 | Age: 23 years              │
│ With: Rajguru, Sukhdev                              │
│ Assembly bomb: April 8, 1929                        │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│ FLASH CARD 5: Chandrashekhar Azad                   │
│ Died: February 27, 1931 | Place: Alfred Park,       │
│ Allahabad | Shot himself with last bullet           │
│ Kakori robbery: August 9, 1925                      │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│ FLASH CARD 6: Komagata Maru (1914)                  │
│ Ship with 376 Punjabi immigrants                    │
│ Refused entry in Vancouver, Canada                  │
│ Returned → Budge Budge massacre (20 killed)        │
└────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────┐
│ FLASH CARD 7: Inquilab Zindabad                     │
│ Coined by: Maulana Hasrat Mohani                    │
│ Popularized by: Bhagat Singh                        │
│ Meaning: Long Live the Revolution                   │
└────────────────────────────────────────────────────────┘
```

---

# ═════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 36
# (Solve ALL questions FIRST, then check answers)
# ═════════════════════════════════════════

---

## 💻 SECTION 1: CS — DBMS (25 Questions)
### [Easy → Medium → Hard → PYQ-Style → Tricky]
### BPSC 5-Option Format

> **IMPORTANT INSTRUCTION:** Attempt ALL 25 questions first. Write your answers (A/B/C/D/E) on paper. Check the answer key only AFTER completing all questions. **Do NOT look at answers while solving!**

---

**Q1. [EASY] A Database Management System (DBMS) primarily acts as an interface between:**

(A) User and Operating System
(B) Database Application and the Database
(C) Hardware and Software
(D) More than one of the above
(E) None of the above

---

**Q2. [EASY] Which of the following is a feature of DBMS?**

(A) Single-user access only
(B) Increases data redundancy
(C) Minimum data redundancy
(D) More than one of the above
(E) None of the above

---

**Q3. [EASY] In a relational database, a row in a table is called a:**

(A) Attribute
(B) Relation
(C) Domain
(D) More than one of the above
(E) None of the above (it is called a Tuple)

---

**Q4. [EASY] Which of the following is NOT an example of a DBMS?**

(A) MySQL
(B) Oracle
(C) Google
(D) More than one of the above
(E) None of the above

---

**Q5. [EASY] In relational database terminology, a TABLE is also called a:**

(A) Tuple
(B) Attribute
(C) Relation
(D) More than one of the above
(E) None of the above

---

**Q6. [EASY] DDL stands for:**

(A) Data Definition Language
(B) Data Distribution Language
(C) Data Deletion Language
(D) More than one of the above
(E) None of the above

---

**Q7. [MEDIUM] Which of the following correctly describes "Metadata" in the context of databases?**

(A) Large amounts of data stored in a database
(B) Data about data (e.g., table names, column types, constraints)
(C) The actual records stored in a table
(D) More than one of the above
(E) None of the above

---

**Q8. [MEDIUM] A database where data is stored and managed across multiple physical locations, yet appears as a single unified database to users, is called a:**

(A) Parallel Database
(B) Decentralized Database
(C) Distributed Database
(D) More than one of the above
(E) None of the above

---

**Q9. [MEDIUM] In the Three-Schema Architecture (ANSI/SPARC), which level describes how data is physically stored on the disk?**

(A) External Level
(B) Conceptual Level
(C) Internal Level
(D) More than one of the above
(E) None of the above

---

**Q10. [MEDIUM] The ability to change the physical storage structure of the database without affecting the logical schema is called:**

(A) Logical Data Independence
(B) Physical Data Independence
(C) Schema Independence
(D) More than one of the above
(E) None of the above

---

**Q11. [MEDIUM] Which SQL command is used to REMOVE an entire table structure along with its data from a database?**

(A) DELETE
(B) REMOVE
(C) DROP
(D) More than one of the above
(E) None of the above

---

**Q12. [MEDIUM] Which type of database model represents data as a TREE structure with parent-child relationships?**

(A) Network Model
(B) Relational Model
(C) Hierarchical Model
(D) More than one of the above
(E) None of the above

---

**Q13. [MEDIUM] The Network Database Model was standardized by which organization?**

(A) ANSI
(B) IEEE
(C) CODASYL
(D) More than one of the above
(E) None of the above

---

**Q14. [HARD] In a relation with 5 attributes and 100 tuples, which of the following is correct?**

(A) Degree = 100, Cardinality = 5
(B) Degree = 5, Cardinality = 100
(C) Degree = 5, Cardinality = 5
(D) More than one of the above
(E) None of the above

---

**Q15. [HARD] Which of the following SQL commands belongs to TCL (Transaction Control Language)?**

(A) GRANT
(B) ALTER
(C) ROLLBACK
(D) More than one of the above
(E) None of the above

---

**Q16. [HARD] Which statement about the DBMS Three-Schema Architecture is CORRECT?**

(A) Logical data independence is easier to achieve than physical data independence
(B) Physical data independence is easier to achieve than logical data independence
(C) Both types of data independence are equally difficult to achieve
(D) More than one of the above
(E) None of the above

---

**Q17. [HARD] The "Data Dictionary" in a DBMS is also known as:**

(A) Database Schema
(B) System Catalog
(C) Query Processor
(D) More than one of the above (both B and another name apply)
(E) None of the above

---

**Q18. [PYQ-STYLE] Which of the following is NOT a feature/advantage of DBMS over the file system?**

(A) Data redundancy is minimized
(B) Data is more secure due to access control
(C) Single-user access at a time only
(D) More than one of the above
(E) None of the above

---

**Q19. [PYQ-STYLE] Consider the following statements about DBMS:
(I) DBMS supports multi-user concurrent access
(II) DBMS eliminates data redundancy completely
(III) DBMS provides a backup and recovery mechanism
(IV) DBMS increases data inconsistency

Which statements are CORRECT?**

(A) I and III only
(B) I, II and III only
(C) II and IV only
(D) More than one of the above
(E) None of the above

---

**Q20. [PYQ-STYLE] In DBMS terminology, a COLUMN in a relational table is called an:**

(A) Tuple
(B) Relation
(C) Attribute
(D) More than one of the above
(E) None of the above

---

**Q21. [PYQ-STYLE] Which of the following SQL command(s) belong to DML (Data Manipulation Language)?**

(A) CREATE and DROP
(B) SELECT and INSERT
(C) GRANT and REVOKE
(D) More than one of the above (SELECT, INSERT, UPDATE, DELETE are all DML)
(E) None of the above

---

**Q22. [TRICKY] A student database stores: Student ID, Name, Age, Department. How many attributes does this relation have?**

(A) Depends on the number of students
(B) 1 (Student ID is the only key attribute)
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q23. [TRICKY] Which of the following statements about DBMS is INCORRECT?**

(A) DBMS provides data independence
(B) DBMS supports concurrent access by multiple users
(C) DBMS completely eliminates the need for any data redundancy
(D) More than one of the above
(E) None of the above

---

**Q24. [TRICKY] IBM's IMS (Information Management System) is an example of which type of database model?**

(A) Relational Model
(B) Network Model
(C) Hierarchical Model
(D) More than one of the above
(E) None of the above

---

**Q25. [TRICKY] DCL (Data Control Language) in SQL includes which of the following commands?**

(A) COMMIT and ROLLBACK
(B) SELECT and UPDATE
(C) GRANT and REVOKE
(D) More than one of the above
(E) None of the above

---
---

## 📜 SECTION 2: GS — History (Ghadar Party, Abhinav Bharat) — 25 Questions

> **IMPORTANT INSTRUCTION:** Attempt ALL 25 questions first. Check answers only at the end!

---

**Q26. [EASY] The Ghadar Party was founded in:**

(A) London, England
(B) San Francisco, USA
(C) Lahore, British India
(D) More than one of the above
(E) None of the above

---

**Q27. [EASY] Who was the main ideological founder/organizer of the Ghadar Party?**

(A) Sohan Singh Bhakna
(B) Lala Har Dayal
(C) Bhagat Singh
(D) More than one of the above
(E) None of the above

---

**Q28. [EASY] The Abhinav Bharat Society was founded by:**

(A) Bal Gangadhar Tilak
(B) Lala Lajpat Rai
(C) Vinayak Damodar Savarkar
(D) More than one of the above
(E) None of the above

---

**Q29. [EASY] Bhagat Singh, Rajguru, and Sukhdev were hanged on:**

(A) March 23, 1931
(B) August 15, 1930
(C) January 26, 1931
(D) More than one of the above
(E) None of the above

---

**Q30. [EASY] Khudiram Bose was involved in which case?**

(A) Lahore Conspiracy Case
(B) Kakori Train Robbery
(C) Muzaffarpur Bomb Case
(D) More than one of the above
(E) None of the above

---

**Q31. [EASY] "Inquilab Zindabad" was originally coined by:**

(A) Bhagat Singh
(B) Chandrashekhar Azad
(C) Maulana Hasrat Mohani
(D) More than one of the above
(E) None of the above

---

**Q32. [MEDIUM] Abhinav Bharat Society was inspired by which European organization?**

(A) Young Germany (Mazzini)
(B) Young Italy (Mazzini)
(C) Young Europe (Herder)
(D) More than one of the above
(E) None of the above

---

**Q33. [MEDIUM] The newspaper "Ghadar" was published in which languages?**

(A) Hindi and English only
(B) Urdu, Punjabi, Gurmukhi, Hindi, and English
(C) Sanskrit and English
(D) More than one of the above
(E) None of the above

---

**Q34. [MEDIUM] Who was the first President of the Ghadar Party?**

(A) Lala Har Dayal
(B) Lala Lajpat Rai
(C) Sohan Singh Bhakna
(D) More than one of the above
(E) None of the above

---

**Q35. [MEDIUM] The Komagata Maru incident (1914) involved:**

(A) A train carrying Indian revolutionaries
(B) A ship carrying 376 Punjabi immigrants denied entry in Canada
(C) A failed bombing attempt in Calcutta
(D) More than one of the above
(E) None of the above

---

**Q36. [MEDIUM] The Kakori Train Robbery took place on:**

(A) August 9, 1925
(B) December 17, 1928
(C) April 8, 1929
(D) More than one of the above
(E) None of the above

---

**Q37. [MEDIUM] Which revolutionary organization was founded by Bhagat Singh in 1926?**

(A) Ghadar Party
(B) Naujawan Bharat Sabha
(C) Hindustan Republican Association
(D) More than one of the above
(E) None of the above

---

**Q38. [MEDIUM] Chandrashekhar Azad died at which place?**

(A) Lahore Central Jail
(B) Alfred Park, Allahabad
(C) Andaman Cellular Jail
(D) More than one of the above
(E) None of the above

---

**Q39. [MEDIUM] Veer Savarkar's book on 1857 was notable because:**

(A) It was the first book written about 1857
(B) It was banned by the British BEFORE publication
(C) It was written in prison
(D) More than one of the above
(E) None of the above

---

**Q40. [HARD] Kartar Singh Sarabha, who was hanged at age 19, was associated with:**

(A) Anushilan Samiti
(B) Abhinav Bharat
(C) Ghadar Party
(D) More than one of the above
(E) None of the above

---

**Q41. [HARD] The Anushilan Samiti was founded in:**

(A) 1902, Calcutta
(B) 1905, Dhaka
(C) 1906, Lahore
(D) More than one of the above
(E) None of the above

---

**Q42. [HARD] Ram Prasad Bismil and Ashfaqullah Khan were hanged in connection with which case?**

(A) Lahore Conspiracy Case
(B) Alipore Bomb Case
(C) Kakori Conspiracy Case
(D) More than one of the above
(E) None of the above

---

**Q43. [HARD] The Hindustan Republican Association (HRA) was renamed Hindustan Socialist Republican Association (HSRA) in:**

(A) 1924 after the Kakori robbery
(B) 1928, at Feroz Shah Kotla, Delhi — inspired by Bhagat Singh
(C) 1929 after the Assembly Bomb case
(D) More than one of the above
(E) None of the above

---

**Q44. [PYQ-STYLE] Consider the following pairs (Organization — Founder):
(I) Ghadar Party — Lala Har Dayal
(II) Abhinav Bharat — Veer Savarkar
(III) Naujawan Bharat Sabha — Chandrashekhar Azad
(IV) Anushilan Samiti — Satish Chandra Bose

Which pairs are correctly matched?**

(A) I and II only
(B) I, II and IV only
(C) II and III only
(D) More than one of the above
(E) None of the above

---

**Q45. [PYQ-STYLE] The Budge Budge incident (1914), where British forces fired on returning Indians, was related to:**

(A) Kakori Train Robbery passengers
(B) Ghadar Party members returning from USA
(C) Komagata Maru passengers
(D) More than one of the above
(E) None of the above

---

**Q46. [PYQ-STYLE] Bhagat Singh threw bombs in the Central Legislative Assembly on April 8, 1929. The purpose was:**

(A) To kill British officers
(B) To make the deaf hear — protest, not to kill
(C) To destroy the Parliament building
(D) More than one of the above
(E) None of the above

---

**Q47. [PYQ-STYLE] Which revolutionary is known by the vow "I will never be arrested by the British" — and kept this promise by shooting himself?**

(A) Bhagat Singh
(B) Ram Prasad Bismil
(C) Chandrashekhar Azad
(D) More than one of the above
(E) None of the above

---

**Q48. [TRICKY] Lala Lajpat Rai died after being lathi-charged during a protest against which commission?**

(A) Hunter Commission
(B) Rowlatt Committee
(C) Simon Commission
(D) More than one of the above
(E) None of the above

---

**Q49. [TRICKY] In the Nasik Conspiracy Case (1909), who shot Collector A.M.T. Jackson?**

(A) Veer Savarkar himself
(B) Anant Laxman Kanhere
(C) Bal Gangadhar Tilak
(D) More than one of the above
(E) None of the above

---

**Q50. [TRICKY] Savarkar's Abhinav Bharat was originally established under what name?**

(A) Young India Society
(B) Mitra Mela
(C) Naujawan Bharat Sabha
(D) More than one of the above
(E) None of the above

---

# ═══════════════════════════════════════
# ✅ ANSWER KEY — DAY 36
# (Check ONLY after attempting all 50 questions)
# ═══════════════════════════════════════

---

## 💻 CS ANSWERS (Q1–Q25)

| Q# | Ans | Topic | Key Explanation |
|----|-----|-------|-----------------|
| Q1 | **(B)** | DBMS role | DBMS = Interface between **Database Application and Database** |
| Q2 | **(C)** | DBMS features | DBMS provides **minimum data redundancy** (reduces, not eliminates) |
| Q3 | **(E)** | Relational terms | A row is called a **Tuple** (E = None of A/B/C/D as given) |
| Q4 | **(C)** | DBMS examples | **Google** is a Search Engine, NOT a DBMS |
| Q5 | **(C)** | Relational terms | Table = **Relation** in relational database terminology |
| Q6 | **(A)** | SQL categories | DDL = **Data Definition Language** (CREATE, DROP, ALTER) |
| Q7 | **(B)** | Metadata | Metadata = **Data about data** (schema info, column names, types) |
| Q8 | **(C)** | DB types | Data spread across locations = **Distributed Database** (NOT Decentralized) |
| Q9 | **(C)** | 3-Schema | **Internal Level** = how data is physically stored on disk |
| Q10 | **(B)** | Data Independence | Physical storage change without affecting logical = **Physical Data Independence** |
| Q11 | **(C)** | SQL DDL | **DROP** removes table structure + data. DELETE removes only data rows. |
| Q12 | **(C)** | DB models | **Hierarchical Model** = Tree structure (Parent-Child) |
| Q13 | **(C)** | Network model | **CODASYL** standardized the Network Database Model |
| Q14 | **(B)** | Degree/Cardinality | **Degree** = # attributes (columns) = 5; **Cardinality** = # tuples (rows) = 100 |
| Q15 | **(C)** | SQL categories | **ROLLBACK** is TCL. GRANT = DCL. ALTER = DDL. |
| Q16 | **(B)** | Data Independence | **Physical data independence is EASIER** to achieve than logical |
| Q17 | **(B)** | Data Dictionary | Data Dictionary = **System Catalog** (metadata repository) |
| Q18 | **(C)** | DBMS features | **Single-user access only** is NOT a feature — DBMS supports MULTI-USER access |
| Q19 | **(A)** | DBMS properties | Statement I (multi-user) and III (backup/recovery) are correct. II is wrong (reduces, not eliminates). IV is wrong (DBMS reduces inconsistency). |
| Q20 | **(C)** | Relational terms | Column = **Attribute** |
| Q21 | **(D)** | DML commands | **More than one** — SELECT, INSERT, UPDATE, DELETE are ALL DML |
| Q22 | **(C)** | Attributes | Student ID, Name, Age, Department = **4 attributes** |
| Q23 | **(C)** | DBMS correction | "DBMS completely eliminates all data redundancy" is INCORRECT — it **minimizes** it |
| Q24 | **(C)** | DB history | IBM's IMS = **Hierarchical Model** (classic example) |
| Q25 | **(C)** | DCL | DCL = **GRANT and REVOKE** (access control commands) |

---

## 📜 GS ANSWERS (Q26–Q50)

| Q# | Ans | Topic | Key Explanation |
|----|-----|-------|-----------------|
| Q26 | **(B)** | Ghadar Party | Founded in **San Francisco, USA** (1913) |
| Q27 | **(B)** | Ghadar Party | **Lala Har Dayal** = ideological founder; Sohan Singh Bhakna = first President |
| Q28 | **(C)** | Abhinav Bharat | **Veer Savarkar** founded Abhinav Bharat (1904, Nasik) |
| Q29 | **(A)** | Bhagat Singh | Hanged on **March 23, 1931** (one day before scheduled date) |
| Q30 | **(C)** | Khudiram Bose | **Muzaffarpur Bomb Case** (1908) — threw bomb at Kingsford |
| Q31 | **(C)** | Slogan | **Maulana Hasrat Mohani** coined "Inquilab Zindabad"; Bhagat Singh popularized it |
| Q32 | **(B)** | Inspiration | Inspired by **Mazzini's "Young Italy"** (not Young Germany) |
| Q33 | **(B)** | Ghadar paper | Published in **Urdu, Punjabi, Gurmukhi, Hindi, English** |
| Q34 | **(C)** | Ghadar Party | **Sohan Singh Bhakna** = First President; Lala Har Dayal = ideologue/organizer |
| Q35 | **(B)** | Komagata Maru | Ship with **376 Punjabi immigrants** denied entry in Vancouver, Canada |
| Q36 | **(A)** | Kakori robbery | Kakori Train Robbery = **August 9, 1925** |
| Q37 | **(B)** | Bhagat Singh | **Naujawan Bharat Sabha** (1926) founded by Bhagat Singh |
| Q38 | **(B)** | Azad death | Died at **Alfred Park, Allahabad** (February 27, 1931) |
| Q39 | **(B)** | Savarkar book | **Banned BEFORE publication** by British — unique distinction! |
| Q40 | **(C)** | Sarabha | Kartar Singh Sarabha = **Ghadar Party** member (Bhagat Singh's idol) |
| Q41 | **(A)** | Anushilan | Founded **1902, Calcutta** (Dhaka branch 1906) |
| Q42 | **(C)** | Kakori case | Bismil and Ashfaqullah Khan hanged in **Kakori Conspiracy Case** |
| Q43 | **(B)** | HSRA | Renamed to HSRA at **Feroz Shah Kotla, Delhi, 1928** on Bhagat Singh's insistence |
| Q44 | **(B)** | Org-Founder pairs | I ✓ (Ghadar-Lala Har Dayal), II ✓ (Abhinav Bharat-Savarkar), IV ✓ (Anushilan-Satish Chandra). III wrong (Naujawan Bharat Sabha was Bhagat Singh's, not Azad's) |
| Q45 | **(C)** | Komagata Maru | Budge Budge firing was on **Komagata Maru passengers** returning to India |
| Q46 | **(B)** | Assembly bomb | Bhagat Singh's own statement: "To make the **deaf hear**" — not to kill |
| Q47 | **(C)** | Azad | **Chandrashekhar Azad** — shot himself at Alfred Park with his last bullet |
| Q48 | **(C)** | Lala Lajpat Rai | Lathi-charged during **Simon Commission** protest (1928) |
| Q49 | **(B)** | Nasik case | **Anant Laxman Kanhere** shot Collector Jackson (Abhinav Bharat member) |
| Q50 | **(B)** | Abhinav Bharat | Originally named **Mitra Mela** (1899) by Savarkar, renamed Abhinav Bharat in 1904 |

---

# 📊 YOUR SCORE TRACKER

```
CS Score:  _____ / 25      Target: 23+/25
GS Score:  _____ / 25      Target: 23+/25
Total:     _____ / 50      Target: 46+/50

If CS < 20: Revise DBMS concept sections above
If GS < 20: Revise History flash cards above
```

---

# 🔁 NIGHT REVISION — 5-BULLET SUMMARY

Write these from memory before sleeping:

**CS — DBMS Today:**
1. DBMS = Interface between **DB Application and DB** | NOT a DBMS: Google
2. DBMS features: Multi-user, Min redundancy, Security, Independence, Backup
3. NOT a DBMS feature: **Single-user access only**
4. Relational terms: Relation=Table | Tuple=Row | Attribute=Column | Metadata=Data about data
5. Distributed DB = data at multiple locations | DDL: CREATE/DROP | DML: SELECT/INSERT/UPDATE/DELETE

**GS — Revolutionary Nationalism Today:**
1. Ghadar Party: 1913, San Francisco | Har Dayal (ideologue) | Sohan Singh Bhakna (President)
2. Abhinav Bharat: 1904, Nasik | Veer Savarkar | inspired by Mazzini's Young Italy
3. Khudiram Bose: Muzaffarpur 1908, hanged age 18
4. Bhagat Singh + Rajguru + Sukhdev: Hanged **March 23, 1931** | Azad: Alfred Park, **Feb 27, 1931**
5. Kakori: Aug 9, 1925 | "Inquilab Zindabad" coined by Hasrat Mohani

---

# 🚀 TOMORROW — DAY 37 PREVIEW

**CS:** DBMS Keys — Primary Key, Foreign Key, Super Key, Candidate Key
**GS:** History — Birsa Munda, Santhal Rebellion, Tribal Movements in Bihar

*"Topper mindset: Score tomorrow's paper today by reviewing tonight's flash cards."*

---
*Day 36 of 170 | BPSC TRE 4.0 Complete Prep | Target: TOP 50 RANK | 130+/150*
