# 📅 BPSC TRE 4.0 — DAY 53 COMPLETE STUDY MODULE
### SQL Quick Revision (CS) + Medieval Indian History — Delhi Sultanate, Mughals, Bhakti, Sufism (GS)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): SQL + DBMS shortcuts — every PYQ-tested fact in rapid-fire mode
> - Afternoon (1 hr): Medieval Indian History — story-based deep learning + PYQ facts
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 SQL + DBMS — Complete Quick Revision for Day 53

> **Day 53 Context:** SQL/DBMS = ~12% of CS paper (~10 questions). Covered in depth on Days 38–42 and revised on Day 50. Today is pure speed-recall mode — no new concepts. Work through each block and tick it only if you can recall the fact without reading.

---

## 🔷 BLOCK 1: DBMS Foundations — The Tricky Definitions

```
DATABASE:
  = Organised collection of data that can be ACCESSED, UPDATED, and MANAGED

DBMS:
  = Software that manages the database
  = Acts as interface between: DATABASE APPLICATION and THE DATABASE ← PYQ exact
  NOT an interface between: "user and hardware" (that's OS)

METADATA:
  = Information ABOUT data ← PYQ
  = Describes structure, format, constraints of data
  Example: Column names, data types, table relationships = metadata

NOT a DBMS (PYQ trap):
  → GOOGLE = a search engine, NOT a DBMS ← appeared in TRE paper!
  → A DBMS stores and manages data; Google retrieves web pages

DBMS FEATURES (what it DOES have):
  ✅ Minimum redundancy
  ✅ High security
  ✅ Multi-user access
  ✅ Data integrity
  ✅ Concurrent access control

DBMS does NOT have (wrong option planted in PYQs):
  ❌ Single-user access only ← this is a LIMITATION of file systems, NOT a DBMS feature

TYPES OF DATABASES:
  Relational   → tables (most common; MySQL, Oracle, PostgreSQL)
  Network      → graph of records
  Hierarchical → tree structure
  Distributed  → data spread across multiple physical locations

⚠️ "DECENTRALIZED" is NOT a standard database type ← PYQ trap
   Options will include Decentralized — it is WRONG; correct type = Distributed
```

### 🚨 PYQ TRAP #1:
> DBMS acts as interface between **database application and the database** (NOT user and hardware).
> **Google** is NOT a DBMS — it is a search engine.
> **Decentralized** is NOT a database type — say **Distributed**.

---

## 🔷 BLOCK 2: Keys — Full Precision Recall

```
SUPERKEY:
  = ANY set of attributes that UNIQUELY identifies a record ← PYQ definition
  = The broadest category

CANDIDATE KEY:
  = MINIMAL superkey (no extra/redundant attributes)
  = A table can have MULTIPLE candidate keys

PRIMARY KEY:
  = One candidate key CHOSEN to be the main identifier
  = UNIQUE + NOT NULL
  = Only ONE primary key per table
  = If primary key is a SINGLE attribute → called simple primary key
  = If primary key is MULTIPLE attributes → called COMPOSITE primary key

FOREIGN KEY:
  = References the PRIMARY KEY of ANOTHER table
  = Enforces REFERENTIAL INTEGRITY ← PYQ term
  = CAN be NULL
  = CAN have duplicate values
  = Links two tables in a relationship

UNIQUE KEY:
  = Like primary key, but CAN have ONE NULL value
  = A table can have MULTIPLE unique keys

REFERENTIAL INTEGRITY:
  = Rule that a foreign key value must match an existing primary key
  = OR be NULL (if NULLs are allowed)
  = Prevents "orphan records" (records that reference non-existent parent records)
```

### 🚨 PYQ TRAP #2:
> **Superkey** = any set uniquely identifying a record (broadest).
> **Candidate key** = minimal superkey (no redundant attributes).
> **Referential integrity** = enforced by foreign key.
> Primary key: NULL → ❌ | Foreign key: NULL → ✅ (can be NULL).

---

## 🔷 BLOCK 3: SQL Command Categories — DDL / DML / DCL / TCL / DQL

```
DDL — Data Definition Language (defines STRUCTURE):
  CREATE   → create table/view/index
  ALTER    → modify structure (add/drop/modify columns)
  DROP     → delete table/view/index (STRUCTURE is removed)
  TRUNCATE → remove ALL data; faster than DELETE; cannot rollback
             (⚠️ Some classify TRUNCATE as DDL, not DML — exam may test either)

DML — Data Manipulation Language (manipulates DATA):
  INSERT   → add new rows
  UPDATE   → modify existing rows
  DELETE   → remove specific rows; CAN be rolled back; slower

DCL — Data Control Language (controls PERMISSIONS):
  GRANT    → give access rights to users
  REVOKE   → take back access rights

TCL — Transaction Control Language (controls TRANSACTIONS):
  COMMIT    → permanently saves all changes ← PYQ
  ROLLBACK  → undoes all changes since last COMMIT ← PYQ
  SAVEPOINT → creates a checkpoint for partial rollback

DQL — Data Query Language:
  SELECT   → retrieves data (some include this in DML)

CORRECT DELETE SYNTAX:
  DELETE FROM teaches;    ← removes ALL rows from teaches table ← PYQ exact
  (not: DELETE teaches; or DROP teaches;)
```

### 🚨 PYQ TRAP #3:
> `DELETE FROM teaches;` removes ALL rows from the relation "teaches" — this exact syntax appeared in TRE.
> `COMMIT` = saves permanently | `ROLLBACK` = undoes changes.
> `TRUNCATE` cannot be rolled back; `DELETE` can be rolled back.

---

## 🔷 BLOCK 4: SELECT Statement — Clause Order + Special Clauses

```
THE MANDATORY ORDER OF CLAUSES:
  SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
  ← This exact order is PYQ-tested!

CLAUSE FUNCTIONS:
  SELECT   → choose columns to display
  FROM     → specify table(s)
  WHERE    → filter ROWS (before grouping) ← acts on individual rows
  GROUP BY → group rows with same values in specified columns
  HAVING   → filter GROUPS (after GROUP BY) ← acts on groups ← PYQ
  ORDER BY → sort the result set

KEY RULES:
  → WHERE cannot use aggregate functions (COUNT, SUM, AVG, etc.)
  → HAVING can use aggregate functions ← that's the whole point
  → After GROUP BY, use HAVING for predicates with aggregate functions ← PYQ

ORDER BY:
  → Default sort = ASC (ascending) ← PYQ trap
  → DESC must be explicitly written

WITH clause:
  → Creates a TEMPORARY RELATION (Common Table Expression / CTE) ← PYQ
  → Syntax: WITH temp_name AS (SELECT ...) SELECT ... FROM temp_name;

ROUND() FUNCTION — CRITICAL PYQ:
  ROUND(65.726,  1) =  65.7   (1 decimal place)
  ROUND(65.726,  0) =  66     (nearest integer)
  ROUND(65.726, -1) =  70     (nearest 10) ← APPEARED IN PYQ!
  ROUND(65.726, -2) = 100     (nearest 100)
  Rule: NEGATIVE second argument → rounds LEFT of decimal point

AGGREGATE FUNCTIONS (valid):
  COUNT, SUM, AVG, MAX, MIN ← all five are valid
  NOT valid: COMPUTE ← PYQ trap — "COMPUTE" is NOT an aggregate function

NOT a SQL CONSTRAINT:
  UNION ← PYQ trap — UNION is a SET OPERATION, not a constraint
  Actual constraints: PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE, CHECK, DEFAULT
```

### 🚨 PYQ TRAP #4:
> `ROUND(65.726, -1)` = **70** — the most tested SQL calculation.
> `COMPUTE` is **NOT** a valid aggregate function.
> `UNION` is **NOT** a SQL constraint — it is a set operation.
> Clause order: SELECT→FROM→**WHERE**→GROUP BY→**HAVING**→ORDER BY.

---

## 🔷 BLOCK 5: Views, Joins, and Special Constructs

```
SQL VIEW:
  = VIRTUAL TABLE ← PYQ definition
  = Does not store data physically
  = Recomputed every time it is queried
  = Used for: security (hide columns), simplification, reusability
  Syntax: CREATE VIEW view_name AS SELECT ...;

JOINS (all types):
  INNER JOIN    → only MATCHING rows from both tables
  LEFT JOIN     → ALL rows from LEFT + matching from right (NULL if no match)
  RIGHT JOIN    → ALL rows from RIGHT + matching from left (NULL if no match)
  FULL OUTER JOIN → ALL rows from BOTH (NULL where no match on either side)
  CROSS JOIN    → Cartesian product (every row of A × every row of B)
  NATURAL JOIN  → joins on COMMON COLUMN NAMES automatically
                  = described as "basic approach" for joining tables ← PYQ

SQL HIERARCHY (outermost → innermost):
  Environments → Catalogs → Schemas → Tables ← PYQ tested order

db_accessadmin ROLE:
  = Used for ADDING and REMOVING user IDs ← PYQ

RAW DATA TYPE:
  = Stores UNSTRUCTURED data in a column ← PYQ

DATA IN TWO PLACES:
  → Causes BOTH: wasted space AND data inconsistency ← PYQ (both, not one)
  = This is why normalisation is needed
```

---

## 🔷 BLOCK 6: Normalisation — Ultra-Fast Recall

```
PURPOSE: Remove redundancy + eliminate anomalies

ANOMALIES (caused by poor design):
  Insert anomaly  → cannot insert data without inserting other unwanted data
  Update anomaly  → updating one place doesn't update all duplicates
  Delete anomaly  → deleting data unintentionally removes other important data

1NF → atomic values (no multi-valued attributes, no repeating groups)
2NF → no PARTIAL DEPENDENCIES (all non-key attributes depend on FULL primary key)
      (only relevant when primary key is COMPOSITE)
3NF → no TRANSITIVE DEPENDENCIES (non-key attributes do not depend on other non-key attributes)
      3NF = ADEQUATE for normal RDBMS design ← PYQ exact phrase
BCNF → stricter than 3NF; for every functional dependency X→Y, X must be a superkey

DATA IN TWO PLACES:
  → wasted space AND data inconsistency ← both problems, answer is (D) in BPSC format
```

---

## 📊 SQL RAPID FIRE — 1-LINE RECALL TABLE

| Concept | Key Fact |
|---------|----------|
| DBMS interface | Between database application and database |
| Google | NOT a DBMS — it is a search engine |
| Decentralized DB | NOT a type; correct word = Distributed |
| Metadata | Information ABOUT data |
| Superkey | Any set uniquely identifying a record |
| Referential integrity | Enforced by foreign key |
| Primary key NULL | ❌ NOT allowed |
| Foreign key NULL | ✅ Allowed |
| Clause order | SELECT→FROM→WHERE→GROUP BY→HAVING→ORDER BY |
| WHERE vs HAVING | WHERE=rows; HAVING=groups (after GROUP BY) |
| ORDER BY default | ASC (ascending) |
| WITH clause | Creates temporary relation |
| ROUND(65.726, -1) | **70** |
| COMPUTE | NOT a valid aggregate function |
| UNION | NOT a SQL constraint (it's a set operation) |
| DELETE FROM teaches; | Removes all rows from teaches table |
| COMMIT | Makes updates permanent |
| ROLLBACK | Undoes changes |
| TRUNCATE | Cannot rollback; faster than DELETE |
| SQL VIEW | Virtual table (not stored physically) |
| Natural JOIN | Basic approach; joins on common column names |
| SQL hierarchy | Environments→Catalogs→Schemas→Tables |
| db_accessadmin | Adds/removes user IDs |
| RAW data type | Stores unstructured data |
| 3NF | Adequate for normal RDBMS design |
| Data in two places | Wasted space AND data inconsistency |

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Medieval Indian History — Complete PYQ-Focused Deep Dive

> **Why Day 53?** Medieval History appeared strongly in TRE 3.0 (Razia Sultana, Akbar's Din-i-Ilahi, Bhakti saints) and is expected to continue. The approach here: short crisp stories for each ruler/period so facts stick as narrative, not as isolated memorised lines.

---

## 🔷 SECTION 1: DELHI SULTANATE (1206–1526)

### The Big Picture:
```
Period:   1206 CE – 1526 CE
Founded:  By QUTB-UD-DIN AIBAK (a slave/general of Muhammad of Ghor)
Ended:    By BABUR at First Battle of Panipat (1526)
Capital:  DELHI (throughout its existence)

FIVE DYNASTIES IN ORDER ← PYQ-tested sequence:
  1. SLAVE DYNASTY (Mamluk)  → 1206–1290
  2. KHILJI DYNASTY          → 1290–1320
  3. TUGHLAQ DYNASTY         → 1320–1414
  4. SAYYID DYNASTY          → 1414–1451
  5. LODI DYNASTY            → 1451–1526

Memory trick: "Some Kings Take Special Leave"
  S = Slave | K = Khilji | T = Tughlaq | S = Sayyid | L = Lodi
```

---

### 1.1 SLAVE DYNASTY (1206–1290)

```
QUTB-UD-DIN AIBAK (1206–1210):
  → FOUNDER of Delhi Sultanate ← PYQ
  → Was a slave/general of Muhammad of Ghor
  → "Aibak" means "lord of the horses"
  → Built the QUTB MINAR (construction started; completed later by Iltutmish)
  → Also built QUWWAT-UL-ISLAM mosque (Delhi's first mosque) ← PYQ
  → Known as "Lakh Bakhsh" (Giver of Lakhs) for his generosity
  → Died in a polo accident (1210)

ILTUTMISH (1210–1236):
  → Son-in-law of Qutb-ud-din Aibak
  → COMPLETED the Qutb Minar ← PYQ
  → Introduced the SILVER TANKA and COPPER JITAL (coins) ← PYQ
  → Consolidated the Delhi Sultanate as a stable state
  → Received recognition from the Caliph of Baghdad — legitimised his rule
  → Made his DAUGHTER Razia his successor

RAZIA SULTANA (1236–1240):
  → FIRST FEMALE SULTAN of Delhi ← #1 PYQ fact for this dynasty
  → Daughter of Iltutmish
  → Did NOT wear purdah — held open court, rode elephants, led armies
  → Faced resistance from Turkish nobles (the "Forty" or Chahalgani)
  → Gave high posts to non-Turks (including an Abyssinian called Yakut)
  → Overthrown and killed (1240)

BALBAN (1266–1287):
  → Last great ruler of Slave dynasty
  → "Theory of Kingship" — divine right of kings; king as shadow of God
  → Persian court culture; strict discipline
  → Destroyed the "Chahalgani" (forty Turkish nobles)
  → Introduced SIJDA (prostration before the king) ← PYQ
  → Maintained strong law and order
```

### 🚨 PYQ TRAP #5:
> Qutb Minar: **Started by** Qutb-ud-din Aibak, **completed by** Iltutmish.
> **Razia Sultana = first female sultan** of Delhi (not first female ruler of India — that distinction is debated).
> **Iltutmish introduced silver tanka** (not Qutb-ud-din, not Balban).

---

### 1.2 KHILJI DYNASTY (1290–1320)

```
JALAL-UD-DIN KHILJI (1290–1296):
  → Founded Khilji dynasty; first elderly man to become Sultan
  → Known for relatively mild policies

ALAUDDIN KHILJI (1296–1316) — THE MOST POWERFUL KHILJI ← heavy PYQ focus:

  HOW HE CAME TO POWER:
  → Murdered his uncle Jalal-ud-din Khilji
  → Bribed the army with looted wealth from Devagiri (Deccan)

  MILITARY ACHIEVEMENTS:
  → First sultan to conquer and hold the Deccan and South India
  → Defeated Yadavas (Devagiri), Kakatiyas (Warangal), Hoysalas, Pandyas
  → Mongol invasions: repelled MULTIPLE Mongol attacks (most any Delhi Sultan)
  → General: MALIK KAFUR (his famous slave-general who led southern campaigns)

  MARKET REFORMS (most unique feature): ← PYQ
  → Set up FOUR MARKETS in Delhi:
    1. Grain market (mandi)
    2. Cloth market
    3. Cattle and horse market
    4. General goods market
  → Fixed prices for all goods (price control)
  → Appointed a SHAHNA (Controller) to monitor prices
  → DIWAN-I-RIYASAT = ministry overseeing market reforms ← PYQ
  → Diwan-i-Riyasat was held by MALIK QABUL
  → Spies placed in markets to report violations

  ADMINISTRATIVE REFORMS:
  → Land revenue = 50% of produce (increased from ~1/3 to 1/2)
  → Horse branding system (to prevent fraud in military supplies)
  → Soldiers paid in CASH (not land grants) ← unusual for medieval period
  → Token currency experiment (later abandoned)
```

### 🚨 PYQ TRAP #6:
> **Alauddin Khilji = market reforms (price control)**.
> **Diwan-i-Riyasat** = the ministry supervising market reforms.
> **Malik Kafur** = Alauddin's general who conquered South India.
> Alauddin repelled the most Mongol invasions of any Delhi Sultan.

---

### 1.3 TUGHLAQ DYNASTY (1320–1414)

```
GHIYASUDDIN TUGHLAQ (1320–1325):
  → Founded Tughlaq dynasty
  → Built Tughlaqabad (fortified city near Delhi)

MUHAMMAD BIN TUGHLAQ (1325–1351) — The "Wise Fool":
  → Highly educated but implemented impractical schemes
  → Nicknamed "wise fool" or "wisest fool"

  KEY SCHEMES (all controversial) ← heavy PYQ focus:

  1. TRANSFER OF CAPITAL (1327):
     → Moved capital from DELHI to DAULATABAD (Devagiri, Maharashtra)
     → Reason: Daulatabad was more central; safer from Mongol attacks
     → Forced entire population of Delhi to march 1100 km
     → Many died during the forced march
     → Then moved back to Delhi (a complete disaster)
     ← "Moved capital to Daulatabad" = PYQ's favourite Muhammad bin Tughlaq fact

  2. TOKEN CURRENCY (1329–1330):
     → Introduced BRASS/COPPER tokens as currency with value of silver coins
     → People forged coins massively (no security features)
     → Complete economic collapse; experiment abandoned

  3. TAXATION IN DOAB (1326):
     → Increased land revenue in the DOAB (Ganga-Yamuna region)
     → Coincided with a severe drought
     → Farmers ruined; massive revolts

  → His reign saw the BEGINNING OF THE DECLINE of the Delhi Sultanate
  → Morocco-born traveller IBN BATTUTA visited his court ← PYQ
    Ibn Battuta's book: RIHLA (his travel account)

FIRUZ SHAH TUGHLAQ (1351–1388):
  → Reversed Muhammad bin Tughlaq's harsh policies
  → Built hospitals (dar-ul-shafa), rest houses (sarai), canals for irrigation
  → Moved Ashoka's pillars to Delhi (Topra and Meerut pillars)
  → Created a welfare state (relatively speaking)
  → Introduced hereditary system of military service (weakened army quality)
```

### 🚨 PYQ TRAP #7:
> Muhammad bin Tughlaq moved capital to **Daulatabad** (not Agra, not Lahore).
> **Ibn Battuta** visited his court and wrote **Rihla**.
> Token currency = Muhammad bin Tughlaq (copper coins with silver value).

---

### 1.4 SAYYID AND LODI DYNASTIES

```
SAYYID DYNASTY (1414–1451):
  → Established after Timur's invasion weakened the Tughlaqs
  → Weak rulers; kingdom shrank significantly
  → Khizr Khan (first ruler) — claimed descent from Prophet Muhammad (hence "Sayyid")

LODI DYNASTY (1451–1526):
  → Founded by BAHLUL LODI (Afghan origin — first Afghan dynasty)
  → IBRAHIM LODI = last ruler of Delhi Sultanate
  → Ibrahim Lodi was defeated by BABUR at the
    FIRST BATTLE OF PANIPAT (1526) ← PYQ key battle
    Result: Delhi Sultanate ended; Mughal Empire began
```

---

## 🔷 SECTION 2: MUGHAL EMPIRE (1526–1707)

### The Six Great Mughals in Order:
```
BABUR → HUMAYUN → AKBAR → JAHANGIR → SHAH JAHAN → AURANGZEB

Memory trick: "Big Hungry Animals Jump Swiftly Away"
  B = Babur | H = Humayun | A = Akbar | J = Jahangir | S = Shah Jahan | A = Aurangzeb
```

---

### 2.1 BABUR (1526–1530)

```
Full name: Zahir-ud-din Muhammad Babur
Origin:    Fergana (Central Asia) — descendant of Timur + Genghis Khan
Founded:   Mughal Empire after winning First Battle of Panipat (1526)

THREE KEY BATTLES:
  First Battle of Panipat (1526) → Babur vs Ibrahim Lodi (Delhi Sultanate)
                                    BABUR WINS → Mughal Empire begins ← PYQ
  Battle of Khanwa (1527)       → Babur vs Rana Sanga (Rajput)
                                    BABUR WINS → consolidated North India
  Battle of Chanderi (1528)     → Babur vs Medini Rai (Rajput chief)

KEY CONTRIBUTION:
  → Introduced GUNPOWDER and ARTILLERY in Indian warfare ← PYQ
  → This gave him decisive advantage over traditional Indian armies
  → BABURNAMA ← his autobiography (written in Chagatai Turkish)
    First memoir/autobiography by an Indian ruler ← PYQ

KRISHNADEVA RAYA (contemporary):
  → Greatest ruler of Vijayanagara Empire
  → Reigned at the same time as Babur ← PYQ "who was contemporary of Babur?"
```

---

### 2.2 HUMAYUN (1530–1540, restored 1555–1556)

```
→ Lost throne to SHER SHAH SURI (1540) — Afghan chieftain who defeated him
→ Spent 15 years in exile (Persia, Sindh)
→ Recaptured throne in 1555
→ Died falling from his library steps in 1556 ← PYQ (ironic death for an educated man)

SHER SHAH SURI (1540–1545) — IMPORTANT INTERLUDE:
  → Built the GRAND TRUNK ROAD (GT Road) from Bengal to Kabul ← PYQ
  → Introduced the RUPEE (silver coin) ← PYQ
  → Efficient postal system (horse relay system)
  → Land revenue reforms (accurate measurement)
  → Divided empire into SARKARS and PARGANAS (administrative units)
```

### 🚨 PYQ TRAP #8:
> **Sher Shah Suri built the Grand Trunk Road** (not Akbar, not Babur).
> **Rupee was introduced by Sher Shah Suri** (not the Mughals).
> Humayun died **falling from library steps** (1556).

---

### 2.3 AKBAR (1556–1605) — The Greatest Mughal

```
Full name: Jalal-ud-din Muhammad Akbar
Regent:    BAIRAM KHAN (till Akbar became independent, ~1560)
Second Battle of Panipat (1556) — Akbar (via Bairam Khan) vs Hemu
  → AKBAR WINS → Mughal power secured in North India ← PYQ

RELIGIOUS POLICY — DIN-I-ILAHI (1582): ← #1 PYQ fact for Akbar
  → "Divine Faith" or "Divine Religion"
  → A syncretic religion founded by Akbar
  → Combined elements of Islam, Hinduism, Zoroastrianism, Christianity, Jainism
  → Purpose: unite all religions under one tolerant faith
  → Members: very few (~18 prominent courtiers accepted)
  → BIRBAL (his famous Hindu courtier) accepted Din-i-Ilahi ← PYQ
  → NOT compulsory — voluntary acceptance only
  → Ended after Akbar's death (no successor continued it)

OTHER RELIGIOUS POLICIES:
  → Abolished JAZIYA (tax on non-Muslims) in 1564 ← PYQ
  → Abolished PILGRIMAGE TAX on Hindus
  → Married Rajput princess (Jodha Bai / Harka Bai) — political + religious tolerance
  → Built IBADAT KHANA (House of Worship) at Fatehpur Sikri — for religious debates

ADMINISTRATIVE INNOVATIONS:
  MANSABDARI SYSTEM ← PYQ:
  → Graded the nobles/military commanders by MANSAB (rank)
  → Each mansabdar = zat (personal rank) + sawar (cavalry rank)
  → Higher mansab = more soldiers to maintain + higher salary
  → Made military service direct to emperor (no feudal intermediaries)
  → Abolished hereditary jagirs (mostly)

REVENUE SYSTEM:
  ZABT SYSTEM (Todar Mal's reform):
  → TODAR MAL = Akbar's finance minister ← PYQ
  → Classified land into 4 types based on cultivation
  → Fixed revenue in cash (not kind)
  → Accurate measurement of land (kabuliyat + patta documents)

NAVRATNAS (Nine Gems of Akbar's court): ← PYQ — names often tested
  1. BIRBAL          → wit, wisdom, Hindu courtier who accepted Din-i-Ilahi
  2. TODAR MAL       → finance minister; land revenue (zabt system)
  3. ABUL FAZL       → chief minister; wrote AKBARNAMA (chronicle of Akbar's reign)
  4. FAIZI           → poet-laureate; Abul Fazl's brother
  5. TANSEN          → greatest classical singer of medieval India ← PYQ
  6. RAJA MAN SINGH  → Rajput commander; Akbar's trusted general
  7. BHAGWAN DAS     → Rajput nobleman; Man Singh's father
  8. MULLA DO PYAZA  → nobleman and wit
  9. KHAN-I-KHANA (Abdur Rahim) → poet, general, Bairam Khan's son

CAPITAL: FATEHPUR SIKRI (built by Akbar, near Agra)
          Later abandoned (water shortage)
```

### 🚨 PYQ TRAP #9:
> **Din-i-Ilahi** = founded by **Akbar** (NOT Akbar's father or Birbal).
> **Birbal accepted Din-i-Ilahi** (Hindu courtier).
> **Todar Mal** = finance minister (revenue reforms).
> **Tansen** = Akbar's court musician (not Shah Jahan's, not Humayun's).
> Jaziya abolished by **Akbar** in **1564**.

---

### 2.4 JAHANGIR (1605–1627)

```
→ Son of Akbar; real name: Salim (called himself Jahangir = "World Conqueror")
→ Married NUR JAHAN (an influential Persian noblewoman who effectively co-ruled) ← PYQ
→ Nur Jahan's father: Itimad-ud-Daulah (whose tomb in Agra = "Baby Taj")
→ Promoted MINIATURE PAINTING (Mughal painting reached peak under him) ← PYQ
→ Famous quote: "If justice is not done, you can pull this chain" → CHAIN OF JUSTICE ← PYQ
   (he hung a golden chain with bells outside his palace — anyone could ring it for justice)
→ British ambassador SIR THOMAS ROE visited his court (1615) ← PYQ
```

---

### 2.5 SHAH JAHAN (1628–1658)

```
→ Son of Jahangir; "King of the World"
→ Peak of Mughal architecture ← PYQ association

MAJOR ARCHITECTURAL WORKS: ← All PYQ-tested
  → TAJ MAHAL (Agra) ← world-famous
    Built in memory of wife MUMTAZ MAHAL (who died in 1631)
    Architect: USTAD AHMAD LAHAURI ← PYQ exact name
    Construction: 1631–1653 (22 years)
    Made of: white marble
    UNESCO World Heritage Site

  → RED FORT (Lal Qila, Delhi) ← PYQ
    Shah Jahan's capital: SHAHJAHANABAD (old Delhi)

  → JAMA MASJID (Delhi) — largest mosque in India

  → PEACOCK THRONE (Takht-e-Taus) ← PYQ
    Jewelled throne; later taken by Nadir Shah (Persian invader, 1739)

→ Imprisoned by his own son AURANGZEB in Agra Fort in 1658
→ Died in captivity (1666), looking at Taj Mahal from his window
```

### 🚨 PYQ TRAP #10:
> Taj Mahal built in memory of **Mumtaz Mahal** (wife, NOT mother).
> Architect of Taj Mahal = **Ustad Ahmad Lahauri**.
> **Peacock Throne** = Shah Jahan's (later taken by Nadir Shah in 1739).

---

### 2.6 AURANGZEB (1658–1707)

```
→ Last of the six "great" Mughals
→ Real name: Muhi-ud-din Muhammad Aurangzeb
→ Imprisoned father Shah Jahan; killed three brothers to take power

RELIGIOUS POLICY (reversed Akbar's):
  → Reimposed JAZIYA (tax on non-Muslims) in 1679 ← PYQ
  → Destroyed Hindu temples (including Kashi Vishwanath, Krishna Janmabhoomi)
  → Tried to impose Sharia law
  → This created massive Hindu + Sikh + Rajput resistance

MILITARY:
  → Fought long DECCAN CAMPAIGNS (27 years in Deccan, 1681–1707)
  → Against Marathas (Shivaji and later Maratha chiefs)
  → Captured Maratha leader SAMBHAJI (Shivaji's son) and executed him (1689)
  → But Marathas kept fighting; he could never fully subdue them
  → Deccan campaigns drained the treasury and exhausted the army

DECLINE:
  → Aurangzeb's intolerant policies + Deccan drain = Mughal decline began
  → After his death (1707), Mughal empire rapidly fragmented
```

---

## 🔷 SECTION 3: BHAKTI MOVEMENT

### Overview:
```
Period:   7th–17th century CE (peaked 12th–16th century)
Core Idea: Personal devotion (bhakti) to God — no need for:
           → Priests (Brahmins) as intermediaries
           → Complex rituals and sacrifices
           → CASTE DISTINCTIONS ← PYQ key phrase
           → Sanskrit (bhaktas composed in vernacular languages)

Two streams:
  SAGUNA  → God with form and attributes (e.g., Vishnu, Ram, Krishna)
  NIRGUNA → God without form, formless (e.g., Kabir, Guru Nanak)
```

### Key Bhakti Saints — Master Table:

| Saint | Region | Language | God Worshipped | Key Facts |
|-------|--------|----------|----------------|-----------|
| **KABIR** | UP (Varanasi) | Hindi (dohas) | Nirguna (formless) | Weaver; rejected both Hindu rituals AND Muslim orthodoxy; "Ram and Rahim are one" |
| **MIRABAI** | Rajasthan | Rajasthani/Hindi | Krishna | Rajput princess; her devotional songs to Krishna are famous; left royal life |
| **TULSIDAS** | UP | Awadhi Hindi | Ram | Wrote **RAMCHARITMANAS** (Ram story in Hindi) ← PYQ |
| **SURDAS** | UP (Agra-Mathura) | Braj Bhasha | Krishna | Blind poet; wrote **SURSAGAR** (stories of Krishna's childhood) ← PYQ |
| **TUKARAM** | Maharashtra | Marathi | Vitthal (Vishnu) | Peasant-saint; abhangas (devotional poems) |
| **RAMDAS** | Maharashtra | Marathi | Ram | Spiritual guru of Shivaji Maharaj ← PYQ |
| **CHAITANYA** | Bengal | Bengali | Krishna | Started VAISHNAVISM revival in Bengal; ecstatic devotion |
| **RAMANUJA** | South India | Tamil/Sanskrit | Vishnu | Philosopher; Vishishtadvaita philosophy |
| **SHANKARACHARYA** | Kerala | Sanskrit | Advaita (non-dual) | Earlier reformer (8th century); Advaita Vedanta |

### 🚨 PYQ TRAP #11:
> **Tulsidas** wrote **Ramcharitmanas** (NOT Ramayana — that's Valmiki's original Sanskrit text).
> **Surdas** was **blind** and wrote **Sursagar** (Krishna's childhood stories).
> **Ramdas** was Shivaji's **spiritual guru** (not Tukaram, not Kabir).
> **Kabir** — Nirguna saint; rejected both Hindu caste system AND Islamic orthodoxy.

---

## 🔷 SECTION 4: SUFI MOVEMENT

### Overview:
```
Sufism = mystical dimension of Islam
Core belief: Direct personal union with God through love and devotion
             Rather than just following formal rituals/law
             God is inside us — seek God through inner purification

KHANQAH = Sufi hospice/lodge where disciples gathered around a Sheikh ← PYQ term
SHEIKH/PIR = Sufi master/teacher
SILSILA = chain/lineage of Sufi masters (order/school of Sufism)
```

### Four Major Sufi Orders in India:

```
ORDER          | FOUNDER IN INDIA          | HEADQUARTERS | KEY FACTS
───────────────┼───────────────────────────┼──────────────┼─────────────────────────────
CHISHTI        | MOINUDDIN CHISHTI         | AJMER (Raj.) | Most POPULAR in India ← PYQ
               | (came 1193, died 1236)     |              | Khwaja Moinuddin Chishti
               |                           |              | Dargah at Ajmer = major pilgrimage
               | Also: NIZAMUDDIN AULIYA   | Delhi        | "Mehboob-e-Ilahi"
               | (Delhi; 13th-14th century) |              | Amir Khusrau was his disciple ← PYQ
───────────────┼───────────────────────────┼──────────────┼─────────────────────────────
SUHRAWARDI     | Bahauddin Zakariya        | Multan       | More orthodox; accepted state
               |                           |              | patronage (unlike Chishtis)
───────────────┼───────────────────────────┼──────────────┼─────────────────────────────
QADIRI         | Shah Nimatullah Qadiri    | Punjab       | Prevalent in Punjab and Sindh
───────────────┼───────────────────────────┼──────────────┼─────────────────────────────
NAQSHBANDI     | Khwaja Baqi Billah        | Delhi        | Opposed Akbar's Din-i-Ilahi
               |                           |              | Sheikh Ahmad Sirhindi = prominent
               |                           |              | Called "Mujaddid Alf Sani" ← PYQ
```

### Key Sufi Facts for PYQ:
```
CHISHTI ORDER:
  → MOST POPULAR Sufi order in India ← #1 PYQ fact about Sufism
  → Founded at Chisht (Afghanistan); brought to India by Moinuddin Chishti
  → Ajmer Dargah = most visited Sufi shrine in India
  → Chishtis did NOT accept gifts from rulers (maintained independence) ← PYQ distinction

AMIR KHUSRAU:
  → Disciple of Nizamuddin Auliya (Chishti order) ← PYQ connection
  → Poet, musician, inventor of SITAR and TABLA (credited, though debated)
  → Invented QAWWALI (devotional music form) ← PYQ
  → Wrote in Persian and Hindavi (early Hindi)
  → Called "Tuti-e-Hind" (Parrot of India) ← PYQ

SHEIKH AHMAD SIRHINDI:
  → Naqshbandi order
  → Called "MUJADDID ALF SANI" = Reviver of the Second Millennium ← PYQ
  → Opposed Akbar's and Jahangir's liberal religious policies
  → Fought for return to orthodox Islam
```

---

## 🔷 SECTION 5: VIJAYANAGARA AND MARATHA EMPIRES

### Vijayanagara Empire (1336–1646):
```
Founded:   1336 CE
Founders:  HARIHARA and BUKKA (two brothers) ← PYQ
Location:  South India (capital at HAMPI, Karnataka)
Why founded: To resist Muslim (Delhi Sultanate) advance into South India

KRISHNADEVARAYA (1509–1529) ← GREATEST RULER ← PYQ
  → Most powerful ruler of Vijayanagara
  → Contemporary of BABUR (First Mughal) ← PYQ "who was contemporary of Babur?"
  → Poet: wrote Amuktamalyada (Telugu) ← PYQ
  → Defeated the Sultans of Bijapur, Golconda, Bidar
  → "Andhra Bhoja" title ← a patron of Telugu literature
  → Eight ASHTADIGGAJAS = eight poets in his court ← PYQ term

DECLINE:
  → Battle of Talikota (1565): Combined forces of Deccan Sultanates defeated Vijayanagara
  → Capital Hampi was SACKED AND DESTROYED
```

### Maratha Empire:
```
SHIVAJI MAHARAJ (1627–1680): ← BPSC Bihar — Shivaji is tested less; quick facts only
  → Founded Maratha kingdom (crowned 1674)
  → GUERRILLA WARFARE (mountain warfare) against Mughals ← PYQ strategy
  → Built a NAVY (fort-based navy on Konkan coast) ← PYQ
  → Spiritual guru: SAMARTH RAMDAS ← PYQ (tested under Bhakti section too)
  → Administrative system: ASHTA PRADHAN (council of 8 ministers)

After Shivaji: PESHWAS (hereditary prime ministers) effectively ran the Maratha empire
```

---

## 🔷 SECTION 6: MEMORY TRICKS — COMPLETE SET

```
DELHI SULTANATE ORDER: "Some Kings Take Special Leave"
  Slave → Khilji → Tughlaq → Sayyid → Lodi

QUTB MINAR: "Aibak STARTED, Iltutmish COMPLETED"
  (Aibak laid foundation; Iltutmish built the remaining stories)

RAZIA SULTANA: FIRST FEMALE SULTAN — daughter of ILTUTMISH

ALAUDDIN KHILJI: MARKET REFORMS + DIWAN-I-RIYASAT + MALIK KAFUR

MUHAMMAD BIN TUGHLAQ: "MOVED capital to DAULATABAD + TOKEN currency + IBN BATTUTA visited"
  All three = Muhammad bin Tughlaq (nobody else)

SHER SHAH SURI: "GT ROAD + RUPEE" — both introduced by him, NOT Mughals

MUGHAL ORDER: "Big Hungry Animals Jump Swiftly Away"
  Babur→Humayun→Akbar→Jahangir→Shah Jahan→Aurangzeb

AKBAR'S THREE: "DAT" — Din-i-Ilahi + Abolish Jaziya + Todar Mal

TAJ MAHAL = Mumtaz Mahal (wife) + Ustad Ahmad Lahauri (architect)

BHAKTI:
  Tulsidas → Ramcharitmanas (Ram, Hindi)
  Surdas   → Sursagar (Krishna, BLIND poet)
  Ramdas   → Shivaji's guru
  Kabir    → Nirguna, weaver

SUFI: CHISHTI = MOST POPULAR in India
  Moinuddin Chishti → Ajmer
  Nizamuddin Auliya → Delhi → Amir Khusrau (disciple)
  Mujaddid Alf Sani = Sheikh Ahmad Sirhindi (Naqshbandi)

VIJAYANAGARA:
  Founded by Harihara + Bukka (1336)
  Greatest ruler = Krishnadevaraya (contemporary of Babur)
```

---

## 🔷 SECTION 7: MASTER QUICK-REFERENCE TABLE

| Question | Answer |
|----------|--------|
| Founded Delhi Sultanate | Qutb-ud-din Aibak (1206) |
| 5 dynasties of Delhi Sultanate | Slave→Khilji→Tughlaq→Sayyid→Lodi |
| First female sultan | Razia Sultana (daughter of Iltutmish) |
| Qutb Minar completed by | Iltutmish |
| Iltutmish introduced | Silver tanka + copper jital |
| Alauddin Khilji famous for | Market reforms; Diwan-i-Riyasat |
| Malik Kafur | Alauddin's general; conquered South India |
| Muhammad bin Tughlaq capital | Moved to Daulatabad |
| Ibn Battuta | Visited Muhammad bin Tughlaq; wrote Rihla |
| Grand Trunk Road | Built by Sher Shah Suri |
| Rupee (coin) | Introduced by Sher Shah Suri |
| First Battle of Panipat (1526) | Babur vs Ibrahim Lodi; Babur wins |
| Second Battle of Panipat (1556) | Akbar (via Bairam Khan) vs Hemu; Akbar wins |
| Baburnama | Babur's autobiography (first Mughal autobiography) |
| Gunpowder/Artillery in India | Introduced by Babur |
| Din-i-Ilahi | Akbar's syncretic religion (1582) |
| Birbal | Accepted Din-i-Ilahi; Akbar's witty courtier |
| Jaziya abolished | Akbar (1564); reimposed by Aurangzeb (1679) |
| Todar Mal | Akbar's finance minister; zabt revenue system |
| Tansen | Court musician of Akbar |
| Akbarnama | Written by Abul Fazl |
| Nur Jahan | Jahangir's influential wife |
| Chain of Justice | Jahangir's symbol of justice |
| Sir Thomas Roe | British ambassador; visited Jahangir's court |
| Taj Mahal builder | Shah Jahan; in memory of Mumtaz Mahal |
| Taj Mahal architect | Ustad Ahmad Lahauri |
| Peacock Throne | Shah Jahan's; taken by Nadir Shah (1739) |
| Most popular Sufi order | **CHISHTI** |
| Chishti in India | Moinuddin Chishti (Ajmer) |
| Amir Khusrau | Disciple of Nizamuddin Auliya; invented qawwali |
| Mujaddid Alf Sani | Sheikh Ahmad Sirhindi (Naqshbandi) |
| Tulsidas wrote | Ramcharitmanas |
| Surdas | Blind poet; wrote Sursagar; Krishna devotee |
| Ramdas | Shivaji's spiritual guru |
| Vijayanagara founders | Harihara and Bukka (1336) |
| Krishnadevaraya contemporary | Babur |
| Battle of Talikota (1565) | Vijayanagara defeated; Hampi destroyed |
| Shivaji's warfare | Guerrilla tactics; built navy |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topic: SQL + DBMS — All Concepts

---

**Q1.** A Database Management System (DBMS) acts as an interface between:
(A) The user and the hardware
(B) The database application and the database
(C) The operating system and the application software
(D) More than one of the above
(E) None of the above

---

**Q2.** Which of the following is NOT a Database Management System?
(A) MySQL
(B) Oracle
(C) Google
(D) More than one of the above
(E) None of the above

---

**Q3.** METADATA in a database refers to:
(A) The actual data stored in the tables
(B) Information ABOUT data — such as column names, data types, and structure
(C) The physical storage format of data on disk
(D) More than one of the above
(E) None of the above

---

**Q4.** "Decentralized" as a type of database is:
(A) A valid standard database type alongside Relational, Network, and Hierarchical
(B) NOT a standard database type — the correct term is "Distributed"
(C) Another name for a Hierarchical database
(D) More than one of the above
(E) None of the above

---

**Q5.** A SUPERKEY is defined as:
(A) The primary key of a table
(B) The foreign key that links two tables
(C) Any set of attributes that uniquely identifies a record in a table
(D) More than one of the above
(E) None of the above

---

**Q6.** Which SQL command is used to PERMANENTLY save all changes made in a transaction?
(A) ROLLBACK
(B) SAVEPOINT
(C) COMMIT
(D) More than one of the above
(E) None of the above

---

**Q7.** What is the correct syntax to DELETE ALL ROWS from a table named "teaches"?
(A) `DROP teaches;`
(B) `REMOVE FROM teaches;`
(C) `DELETE FROM teaches;`
(D) More than one of the above
(E) None of the above

---

**Q8.** The correct order of clauses in a SQL SELECT statement is:
(A) SELECT → WHERE → FROM → GROUP BY → ORDER BY → HAVING
(B) SELECT → FROM → GROUP BY → WHERE → HAVING → ORDER BY
(C) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
(D) More than one of the above
(E) None of the above

---

**Q9.** The HAVING clause in SQL is used to:
(A) Filter individual rows before any grouping is applied
(B) Sort the final result set
(C) Filter groups after a GROUP BY operation, especially with aggregate functions
(D) More than one of the above
(E) None of the above

---

**Q10.** What is the default sort order of the ORDER BY clause?
(A) DESC (descending)
(B) Random order
(C) ASC (ascending)
(D) More than one of the above
(E) None of the above

---

**Q11.** The `WITH` clause in SQL is used to:
(A) Grant permissions to a user
(B) Create a temporary relation (Common Table Expression)
(C) Join two or more tables
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

**Q13.** Which of the following is NOT a valid SQL aggregate function?
(A) COUNT
(B) SUM
(C) COMPUTE
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following is NOT a SQL constraint?
(A) PRIMARY KEY
(B) NOT NULL
(C) UNION
(D) More than one of the above
(E) None of the above

---

**Q15.** A SQL VIEW is best described as:
(A) A physical copy of data stored in a separate table
(B) A virtual table that is recomputed each time it is queried
(C) A backup mechanism for transaction recovery
(D) More than one of the above
(E) None of the above

---

**Q16.** NATURAL JOIN in SQL is described as:
(A) A join that creates the Cartesian product of two tables
(B) A basic approach that joins tables automatically on common column names
(C) A join that only works with primary and foreign key relationships
(D) More than one of the above
(E) None of the above

---

**Q17.** The SQL hierarchy from outermost to innermost is:
(A) Schemas → Catalogs → Environments → Tables
(B) Tables → Schemas → Catalogs → Environments
(C) Environments → Catalogs → Schemas → Tables
(D) More than one of the above
(E) None of the above

---

**Q18.** The `db_accessadmin` role is used for:
(A) Backing up and restoring the database
(B) Creating and dropping tables
(C) Adding and removing user IDs for database access
(D) More than one of the above
(E) None of the above

---

**Q19.** Storing the same data in TWO places in a database causes:
(A) Only wasted storage space
(B) Only data inconsistency
(C) Both wasted space AND data inconsistency
(D) More than one of the above
(E) None of the above

---

**Q20.** Which normal form is considered ADEQUATE for normal relational database design?
(A) 1NF
(B) 2NF
(C) 3NF
(D) More than one of the above
(E) None of the above

---

**Q21.** REFERENTIAL INTEGRITY is enforced by:
(A) Primary key constraints
(B) NOT NULL constraints
(C) Foreign key constraints
(D) More than one of the above
(E) None of the above

---

**Q22.** Which SQL command type does GRANT and REVOKE belong to?
(A) DDL (Data Definition Language)
(B) DML (Data Manipulation Language)
(C) DCL (Data Control Language)
(D) More than one of the above
(E) None of the above

---

**Q23.** The difference between DELETE and TRUNCATE is:
(A) DELETE can be rolled back; TRUNCATE cannot be rolled back
(B) TRUNCATE is slower than DELETE
(C) DELETE removes the table structure; TRUNCATE only removes data
(D) More than one of the above
(E) None of the above

---

**Q24.** A CANDIDATE KEY is defined as:
(A) Any set of attributes that uniquely identifies a record (including redundant ones)
(B) A minimal superkey — it uniquely identifies a record with no extra attributes
(C) The foreign key chosen to link two tables
(D) More than one of the above
(E) None of the above

---

**Q25.** The RAW data type in SQL is used to store:
(A) Very large text (CLOB) data
(B) Date and time values
(C) Unstructured data in a column
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Medieval Indian History — Delhi Sultanate, Mughals, Bhakti, Sufism

---

**Q26.** Who FOUNDED the Delhi Sultanate in 1206 CE?
(A) Iltutmish
(B) Razia Sultana
(C) Qutb-ud-din Aibak
(D) More than one of the above
(E) None of the above

---

**Q27.** The correct chronological order of the FIVE dynasties of the Delhi Sultanate is:
(A) Khilji → Slave → Tughlaq → Lodi → Sayyid
(B) Slave → Khilji → Tughlaq → Sayyid → Lodi
(C) Tughlaq → Khilji → Slave → Lodi → Sayyid
(D) More than one of the above
(E) None of the above

---

**Q28.** RAZIA SULTANA is historically significant because she was:
(A) The first woman to rule any territory in South Asia
(B) The first female Sultan of Delhi
(C) The founder of the Slave dynasty
(D) More than one of the above
(E) None of the above

---

**Q29.** The Qutb Minar was COMPLETED by:
(A) Qutb-ud-din Aibak
(B) Balban
(C) Iltutmish
(D) More than one of the above
(E) None of the above

---

**Q30.** ALAUDDIN KHILJI's most distinctive administrative innovation was:
(A) Moving the capital from Delhi to Daulatabad
(B) Introducing token copper currency with silver value
(C) Establishing market reforms with fixed price controls (Diwan-i-Riyasat)
(D) More than one of the above
(E) None of the above

---

**Q31.** MUHAMMAD BIN TUGHLAQ moved the capital of the Delhi Sultanate from Delhi to:
(A) Agra
(B) Lahore
(C) Daulatabad (Devagiri)
(D) More than one of the above
(E) None of the above

---

**Q32.** The Moroccan traveller who visited Muhammad bin Tughlaq's court and wrote "Rihla" was:
(A) Xuanzang (Hiuen Tsang)
(B) Megasthenes
(C) Ibn Battuta
(D) More than one of the above
(E) None of the above

---

**Q33.** The GRAND TRUNK ROAD (from Bengal to Kabul) and the RUPEE (silver coin) were introduced by:
(A) Akbar
(B) Babur
(C) Sher Shah Suri
(D) More than one of the above
(E) None of the above

---

**Q34.** DIN-I-ILAHI was:
(A) A tax on non-Muslims reimposed by Aurangzeb
(B) A syncretic religion founded by Akbar in 1582 combining elements of multiple faiths
(C) A market reform system introduced by Alauddin Khilji
(D) More than one of the above
(E) None of the above

---

**Q35.** Who among Akbar's Navratnas accepted Din-i-Ilahi?
(A) Todar Mal
(B) Tansen
(C) Birbal
(D) More than one of the above
(E) None of the above

---

**Q36.** TODAR MAL in Akbar's court is associated with:
(A) Music and the arts
(B) Land revenue reforms (Zabt system)
(C) Military campaigns in the Deccan
(D) More than one of the above
(E) None of the above

---

**Q37.** JAZIYA (tax on non-Muslims) was abolished by Akbar and later reimposed by:
(A) Jahangir (1610)
(B) Shah Jahan (1640)
(C) Aurangzeb (1679)
(D) More than one of the above
(E) None of the above

---

**Q38.** The TAJ MAHAL was built by Shah Jahan in memory of:
(A) His mother Nur Jahan
(B) His daughter Jahanara Begum
(C) His wife Mumtaz Mahal
(D) More than one of the above
(E) None of the above

---

**Q39.** The architect of the Taj Mahal was:
(A) Todar Mal
(B) Abul Fazl
(C) Ustad Ahmad Lahauri
(D) More than one of the above
(E) None of the above

---

**Q40.** The CHISHTI order is described as the MOST POPULAR Sufi order in India. Its most famous saint in India was:
(A) Sheikh Ahmad Sirhindi
(B) Bahauddin Zakariya
(C) Moinuddin Chishti (Khwaja of Ajmer)
(D) More than one of the above
(E) None of the above

---

**Q41.** AMIR KHUSRAU was a disciple of which Sufi saint?
(A) Moinuddin Chishti (Ajmer)
(B) Nizamuddin Auliya (Delhi)
(C) Sheikh Ahmad Sirhindi (Sirhind)
(D) More than one of the above
(E) None of the above

---

**Q42.** "MUJADDID ALF SANI" (Reviver of the Second Millennium) was the title of:
(A) Nizamuddin Auliya
(B) Moinuddin Chishti
(C) Sheikh Ahmad Sirhindi
(D) More than one of the above
(E) None of the above

---

**Q43.** TULSIDAS wrote the RAMCHARITMANAS in which language?
(A) Sanskrit
(B) Braj Bhasha
(C) Awadhi (a dialect of Hindi)
(D) More than one of the above
(E) None of the above

---

**Q44.** SURDAS, the devotional poet who composed the SURSAGAR, was:
(A) A Sufi saint from Ajmer
(B) A blind bhakti poet devoted to Krishna
(C) The spiritual guru of Shivaji
(D) More than one of the above
(E) None of the above

---

**Q45.** Samarth RAMDAS is historically significant as:
(A) The founder of the Bhakti movement in Maharashtra
(B) The spiritual guru of Shivaji Maharaj
(C) The poet who composed the Ramcharitmanas
(D) More than one of the above
(E) None of the above

---

**Q46.** The Vijayanagara Empire was FOUNDED in 1336 by:
(A) Krishna Deva Raya and Narasimha Raya
(B) Harihara and Bukka (two brothers)
(C) Malik Kafur and Alauddin Khilji
(D) More than one of the above
(E) None of the above

---

**Q47.** KRISHNADEVARAYA (greatest ruler of Vijayanagara) was a contemporary of which Mughal emperor?
(A) Akbar
(B) Humayun
(C) Babur
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following is a key feature of the BHAKTI MOVEMENT?
(A) It emphasised complex Vedic rituals as the path to God
(B) It promoted personal devotion to God without caste distinctions
(C) It was exclusively for Brahmin scholars
(D) More than one of the above
(E) None of the above

---

**Q49.** Match the following medieval works with their authors:
```
Work              Author
1. Akbarnama    A. Babur
2. Baburnama    B. Abul Fazl
3. Rihla        C. Ibn Battuta
```
(A) 1-B, 2-A, 3-C
(B) 1-A, 2-B, 3-C
(C) 1-C, 2-A, 3-B
(D) More than one of the above
(E) None of the above

---

**Q50.** The FIRST BATTLE OF PANIPAT (1526) resulted in:
(A) Akbar defeating Hemu and establishing Mughal power
(B) Babur defeating Ibrahim Lodi, ending the Delhi Sultanate and founding the Mughal Empire
(C) Humayun defeating Sher Shah Suri
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
| 1 | (B) | DBMS = interface between database application and database |
| 2 | (C) | Google = search engine, NOT a DBMS |
| 3 | (B) | Metadata = information ABOUT data |
| 4 | (B) | "Decentralized" NOT standard; correct = Distributed |
| 5 | (C) | Superkey = any set uniquely identifying a record |
| 6 | (C) | COMMIT = permanently saves changes |
| 7 | (C) | `DELETE FROM teaches;` = correct syntax |
| 8 | (C) | SELECT→FROM→WHERE→GROUP BY→HAVING→ORDER BY |
| 9 | (C) | HAVING filters groups (after GROUP BY) |
| 10 | (C) | ORDER BY default = ASC |
| 11 | (B) | WITH clause = creates temporary relation (CTE) |
| 12 | (C) | ROUND(65.726, -1) = 70 |
| 13 | (C) | COMPUTE = NOT a valid aggregate function |
| 14 | (C) | UNION = NOT a constraint (it's a set operation) |
| 15 | (B) | VIEW = virtual table, recomputed each query |
| 16 | (B) | Natural JOIN = basic approach, common column names |
| 17 | (C) | Environments→Catalogs→Schemas→Tables |
| 18 | (C) | db_accessadmin = add/remove user IDs |
| 19 | (C) | Data in two places = wasted space AND inconsistency |
| 20 | (C) | 3NF = adequate for normal RDBMS design |
| 21 | (C) | Foreign key enforces referential integrity |
| 22 | (C) | GRANT + REVOKE = DCL commands |
| 23 | (A) | DELETE can rollback; TRUNCATE cannot rollback |
| 24 | (B) | Candidate key = minimal superkey |
| 25 | (C) | RAW data type = stores unstructured data |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Delhi Sultanate founded by Qutb-ud-din Aibak (1206) |
| 27 | (B) | Slave→Khilji→Tughlaq→Sayyid→Lodi |
| 28 | (B) | Razia Sultana = first FEMALE SULTAN of Delhi |
| 29 | (C) | Qutb Minar completed by Iltutmish |
| 30 | (C) | Alauddin Khilji = market reforms + Diwan-i-Riyasat |
| 31 | (C) | Muhammad bin Tughlaq moved capital to Daulatabad |
| 32 | (C) | Ibn Battuta visited; wrote Rihla |
| 33 | (C) | GT Road + Rupee = Sher Shah Suri |
| 34 | (B) | Din-i-Ilahi = Akbar's syncretic religion (1582) |
| 35 | (C) | Birbal accepted Din-i-Ilahi |
| 36 | (B) | Todar Mal = Zabt land revenue reform |
| 37 | (C) | Jaziya reimposed by Aurangzeb (1679) |
| 38 | (C) | Taj Mahal = in memory of Mumtaz Mahal (wife) |
| 39 | (C) | Taj Mahal architect = Ustad Ahmad Lahauri |
| 40 | (C) | Chishti's most famous = Moinuddin Chishti (Ajmer) |
| 41 | (B) | Amir Khusrau = disciple of Nizamuddin Auliya |
| 42 | (C) | Mujaddid Alf Sani = Sheikh Ahmad Sirhindi (Naqshbandi) |
| 43 | (C) | Ramcharitmanas written in Awadhi |
| 44 | (B) | Surdas = blind poet, Krishna devotee, wrote Sursagar |
| 45 | (B) | Ramdas = spiritual guru of Shivaji Maharaj |
| 46 | (B) | Vijayanagara founded by Harihara and Bukka (1336) |
| 47 | (C) | Krishnadevaraya contemporary of Babur |
| 48 | (B) | Bhakti = devotion to God without caste distinctions |
| 49 | (A) | Akbarnama→Abul Fazl; Baburnama→Babur; Rihla→Ibn Battuta |
| 50 | (B) | 1st Battle Panipat 1526 = Babur defeats Ibrahim Lodi |

---
---

# 🔁 DAY 53 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — SQL + DBMS

```
DBMS = interface between database application and database
Google = NOT a DBMS (search engine)
Decentralized = NOT a DB type → say Distributed
Metadata = information ABOUT data
Superkey = any set uniquely identifying a record
Candidate key = MINIMAL superkey (no extra attributes)
Referential integrity = enforced by FOREIGN KEY
PRIMARY KEY → NULL: ❌ | FOREIGN KEY → NULL: ✅

SQL CLAUSE ORDER: SELECT→FROM→WHERE→GROUP BY→HAVING→ORDER BY
WHERE = filters ROWS | HAVING = filters GROUPS
ORDER BY default = ASC
WITH clause = creates TEMPORARY RELATION
ROUND(65.726, -1) = 70  ← most tested SQL calculation
COMPUTE = NOT an aggregate function
UNION = NOT a SQL constraint (set operation)
DELETE FROM teaches; = removes all rows from teaches
COMMIT = permanent save | ROLLBACK = undo
TRUNCATE = no rollback; faster than DELETE
VIEW = virtual table
Natural JOIN = basic approach; common column names
Environments→Catalogs→Schemas→Tables
db_accessadmin = add/remove user IDs
RAW = unstructured data | 3NF = adequate RDBMS design
Data in two places → wasted space AND inconsistency
```

---

## ⚡ RAPID FIRE — Medieval Indian History

```
DELHI SULTANATE: "Some Kings Take Special Leave"
  Slave(1206)→Khilji(1290)→Tughlaq(1320)→Sayyid(1414)→Lodi(1451)

SLAVE DYNASTY:
  Founder: Qutb-ud-din Aibak (1206)
  Qutb Minar: STARTED by Aibak, COMPLETED by Iltutmish
  Iltutmish introduced: silver tanka + copper jital (coins)
  Razia Sultana: FIRST FEMALE SULTAN; daughter of Iltutmish
  Balban: Sijda (prostration before king)

KHILJI: Alauddin = market reforms + Diwan-i-Riyasat + Malik Kafur (S.India)
TUGHLAQ: Muhammad bin Tughlaq = Daulatabad + token currency + Ibn Battuta (Rihla)
SHER SHAH SURI (non-Mughal): GT Road + Rupee ← NOT Akbar or Babur

MUGHAL: "Big Hungry Animals Jump Swiftly Away"
  Babur→Humayun→Akbar→Jahangir→Shah Jahan→Aurangzeb

KEY MUGHAL FACTS:
  Babur: introduced gunpowder/artillery; wrote Baburnama (1st autobiography)
  1st Battle Panipat (1526): Babur vs Ibrahim Lodi → Mughal Empire
  Akbar: Din-i-Ilahi (1582) + abolished Jaziya (1564) + Todar Mal + Tansen
  Birbal: accepted Din-i-Ilahi
  Jahangir: Nur Jahan + Chain of Justice + Sir Thomas Roe
  Shah Jahan: Taj Mahal (Mumtaz Mahal) + Ustad Ahmad Lahauri (architect)
  Aurangzeb: reimposed Jaziya (1679) + 27 years Deccan campaigns

SUFI: CHISHTI = MOST POPULAR in India
  Moinuddin Chishti → Ajmer | Nizamuddin Auliya → Delhi
  Amir Khusrau = Nizamuddin's disciple; invented qawwali
  Mujaddid Alf Sani = Sheikh Ahmad Sirhindi (Naqshbandi)

BHAKTI:
  Tulsidas → Ramcharitmanas (Ram, Awadhi)
  Surdas → Sursagar (Krishna, BLIND poet)
  Ramdas → Shivaji's GURU
  Kabir → Nirguna; rejected Hindu ritual + Islamic orthodoxy

VIJAYANAGARA: Harihara + Bukka (1336); Krishnadevaraya = greatest; contemporary of Babur
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Delhi Sultanate: 5 dynasties = **Slave→Khilji→Tughlaq→Sayyid→Lodi**; **Razia Sultana = first female sultan**; Muhammad bin Tughlaq moved capital to **Daulatabad**
2. **Sher Shah Suri** built Grand Trunk Road and introduced the **Rupee** (NOT Akbar or Babur)
3. Akbar = **Din-i-Ilahi (1582)** + abolished **Jaziya (1564)** + **Todar Mal** (revenue) + **Tansen** (music); **Birbal** accepted Din-i-Ilahi
4. Taj Mahal = Shah Jahan + **Mumtaz Mahal** (wife) + architect **Ustad Ahmad Lahauri**; **Chishti = most popular Sufi order**; Amir Khusrau = Nizamuddin's disciple
5. SQL: ROUND(65.726, -1) = **70**; HAVING = **groups**; ORDER BY default = **ASC**; **COMPUTE** is NOT aggregate; **UNION** is NOT a constraint

---

*Next: Day 54 — E-Commerce, Multimedia & Computer Generations (CS) + Science GK (Physics + Biology)*
