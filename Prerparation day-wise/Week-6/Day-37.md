# 📅 BPSC TRE 4.0 — DAY 37
## CS: DBMS — All Types of Keys | GS: Birsa Munda, Tribal Movements & Peasant Revolts

> **Target:** Score 23+/25 CS | 23+/25 GS | **Overall Goal: TOP 50 RANK**
> **Phase:** Phase 1 — Foundation | **Week 6 (DBMS Week)**
> **Day 37 of 170**

---

# ════════════════════════════════════════════
# 💻 PART A: COMPUTER SCIENCE
# DBMS — ALL TYPES OF KEYS (Complete Mastery)
# ════════════════════════════════════════════

---

## 🔑 WHY KEYS MATTER IN DBMS?

A **KEY** in DBMS is an attribute (or set of attributes) that is used to:
1. **Uniquely identify** a tuple (row) in a relation (table)
2. **Establish relationships** between tables
3. **Enforce data integrity** and avoid duplicate/invalid records

> Think of a KEY as your **Aadhaar Number** — it uniquely identifies YOU among all citizens of India.

---

## 🧠 CONCEPT 1: Understanding Uniqueness First

Before learning key types, understand what "uniquely identifies" means:

```
STUDENT TABLE:
┌────────┬──────────┬──────┬──────────┬────────────┐
│ Stu_ID │ Name     │ Age  │ City     │ Phone      │
├────────┼──────────┼──────┼──────────┼────────────┤
│  101   │ Rahul    │  20  │ Patna    │ 9800000001 │
│  102   │ Priya    │  21  │ Patna    │ 9800000002 │
│  103   │ Rahul    │  20  │ Gaya     │ 9800000003 │
│  104   │ Amit     │  22  │ Muzaff.  │ 9800000004 │
└────────┴──────────┴──────┴──────────┴────────────┘

Which attribute UNIQUELY identifies each student?
→ Name?    NO! Two students are named "Rahul"
→ Age?     NO! Multiple students age 20
→ City?    NO! Multiple students from "Patna"
→ Stu_ID?  YES! Each student has a unique ID
→ Phone?   YES! Each phone number is unique

Both Stu_ID and Phone can uniquely identify a student.
These are called CANDIDATE KEYS.
```

---

## 🧠 CONCEPT 2: SUPER KEY — The Broadest Category

**Super Key** = ANY set of one or more attributes that can **uniquely identify** a tuple.

> **Rule:** If an attribute or combination of attributes can uniquely identify a row → it is a Super Key.

```
For the STUDENT table above, Super Keys include:
┌────────────────────────────────────────────────────┐
│ {Stu_ID}                    ← uniquely identifies  │
│ {Phone}                     ← uniquely identifies  │
│ {Stu_ID, Name}              ← still unique (Stu_ID │
│                               is already unique,   │
│                               adding Name doesn't  │
│                               break uniqueness)    │
│ {Stu_ID, Age}               ← super key           │
│ {Stu_ID, Name, Age, City}   ← super key           │
│ {Phone, Name}               ← super key           │
│ {Stu_ID, Phone, Name, Age, City} ← super key      │
│                                                    │
│ NOT a Super Key:                                   │
│ {Name}    ← two students named Rahul               │
│ {Age}     ← multiple students same age            │
│ {City}    ← multiple students from same city      │
└────────────────────────────────────────────────────┘

KEY INSIGHT: A Super Key may contain EXTRA/UNNECESSARY attributes.
```

> 💡 **Memory Trick:** Super Key = ANY key that works (including ones with extra attributes). "Super" because it's the most general / inclusive category.

---

## 🧠 CONCEPT 3: CANDIDATE KEY — Minimal Super Key

**Candidate Key** = A Super Key with **NO unnecessary attributes** (minimal super key).

> **Rule:** If you remove ANY attribute from a Candidate Key, it NO LONGER uniquely identifies a tuple.

```
CANDIDATE KEYS from the Student table:

{Stu_ID}  → Remove Stu_ID? Can't identify uniquely. ✓ MINIMAL → CANDIDATE KEY
{Phone}   → Remove Phone? Can't identify uniquely. ✓ MINIMAL → CANDIDATE KEY

{Stu_ID, Name} → Remove Name? {Stu_ID} still unique. ✗ NOT MINIMAL → NOT Candidate Key
{Stu_ID, Age}  → Remove Age?  {Stu_ID} still unique. ✗ NOT MINIMAL → NOT Candidate Key

So for this table:
CANDIDATE KEYS = {Stu_ID} and {Phone}
```

```
RELATIONSHIP DIAGRAM:
┌──────────────────────────────────────────────────┐
│                 ALL ATTRIBUTES                   │
│  ┌────────────────────────────────────────────┐  │
│  │              SUPER KEYS                    │  │
│  │  ┌──────────────────────────────────────┐  │  │
│  │  │          CANDIDATE KEYS              │  │  │
│  │  │   ┌───────────────────────────────┐  │  │  │
│  │  │   │     PRIMARY KEY (1 only)      │  │  │  │
│  │  │   └───────────────────────────────┘  │  │  │
│  │  │   (remaining = ALTERNATE KEYS)       │  │  │
│  │  └──────────────────────────────────────┘  │  │
│  └────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────┘

HIERARCHY: Primary Key ⊂ Candidate Key ⊂ Super Key
```

> ⚠️ **PYQ FACT:** Candidate Key = Minimal Super Key. Every Candidate Key is a Super Key but NOT every Super Key is a Candidate Key.

---

## 🧠 CONCEPT 4: PRIMARY KEY — The Chosen One

**Primary Key** = ONE Candidate Key selected by the Database Designer to be the **main identifier** for a table.

### Rules of Primary Key (CRITICAL FOR EXAM):
```
┌─────────────────────────────────────────────────────┐
│           PRIMARY KEY RULES — MEMORIZE!             │
├─────────────────────────────────────────────────────┤
│ Rule 1: Only ONE primary key per table              │
│ Rule 2: Value must be UNIQUE for every row          │
│ Rule 3: Value CANNOT be NULL (Not Null constraint)  │
│ Rule 4: Value should NOT change over time           │
│         (e.g., phone number can change → bad PK)   │
│ Rule 5: Should be minimal (single attribute        │
│         preferred over composite)                  │
└─────────────────────────────────────────────────────┘
```

```
STUDENT TABLE with Primary Key:
┌────────┬──────────┬──────┬──────────┐
│ Stu_ID │ Name     │ Age  │ City     │
├────────┼──────────┼──────┼──────────┤    Stu_ID is
│  101   │ Rahul    │  20  │ Patna    │ ← PRIMARY KEY
│  102   │ Priya    │  21  │ Patna    │
│  103   │ NULL     │  20  │ Gaya     │ ← ❌ INVALID! 
│        │          │      │          │    PK cannot be NULL
│  101   │ Suresh   │  22  │ Muzaff.  │ ← ❌ INVALID!
│        │          │      │          │    Duplicate PK!
└────────┴──────────┴──────┴──────────┘
```

> ⚠️ **PYQ TRAP:** "How many primary keys can a table have?" → **ONLY ONE** (not one or more — exactly ONE)

---

## 🧠 CONCEPT 5: ALTERNATE KEY — The Backup

**Alternate Key** = All Candidate Keys that are **NOT chosen** as the Primary Key.

```
If a table has Candidate Keys: {Stu_ID} and {Phone}
→ DBA chooses {Stu_ID} as Primary Key
→ {Phone} becomes the ALTERNATE KEY

Remember:
Primary Key + Alternate Keys = All Candidate Keys
```

> 💡 Alternate Keys are also unique! They just weren't chosen as the primary key.

---

## 🧠 CONCEPT 6: FOREIGN KEY — The Linking Key

**Foreign Key** = An attribute in one table that **refers to the Primary Key of another table**.

> Foreign Key establishes a **relationship (link)** between two tables.

```
TWO TABLES EXAMPLE:

STUDENT TABLE:                      DEPARTMENT TABLE:
┌────────┬────────┬─────────┐       ┌────────┬──────────────┐
│ Stu_ID │ Name   │ Dept_ID │       │ Dept_ID│ Dept_Name    │
├────────┼────────┼─────────┤       ├────────┼──────────────┤
│  101   │ Rahul  │   10    │──────▶│  10    │ Computer Sc. │
│  102   │ Priya  │   20    │──────▶│  20    │ Mathematics  │
│  103   │ Amit   │   10    │──────▶│  10    │ Computer Sc. │
└────────┴────────┴─────────┘       └────────┴──────────────┘
         ↑ STUDENT Table                      ↑ DEPARTMENT Table
    Dept_ID here is                      Dept_ID here is
    FOREIGN KEY                          PRIMARY KEY
    (references Dept Table)

FOREIGN KEY RULES:
→ FK in Student table = Dept_ID
→ FK refers to PK (Dept_ID) of Department table
→ Every value in FK must EXIST in the referenced PK column
  (this is REFERENTIAL INTEGRITY)
→ A table can have MULTIPLE foreign keys
→ FK value CAN be NULL (unlike Primary Key)
```

### Referential Integrity Constraint:
```
VALID situation:
Student has Dept_ID = 10 → Department 10 EXISTS ✓

INVALID situation:
Student has Dept_ID = 99 → Department 99 does NOT EXIST ✗
                        → REFERENTIAL INTEGRITY VIOLATED!
```

> ⚠️ **PYQ FACT:** Foreign Key REFERENCES the Primary Key of another table. FK maintains **Referential Integrity**. A table can have MULTIPLE foreign keys (unlike primary key which can have only ONE).

---

## 🧠 CONCEPT 7: COMPOSITE KEY

**Composite Key** = A key made up of **TWO OR MORE attributes** together to uniquely identify a tuple.

```
ENROLLMENT TABLE:
(A student can enroll in multiple courses)

┌────────┬───────────┬────────────┬──────────┐
│ Stu_ID │ Course_ID │ Semester   │ Grade    │
├────────┼───────────┼────────────┼──────────┤
│  101   │  CS101    │  Sem-1     │  A       │
│  101   │  CS102    │  Sem-1     │  B       │ ← Same Stu_ID
│  102   │  CS101    │  Sem-1     │  A+      │ ← Same Course_ID
│  101   │  CS101    │  Sem-2     │  B       │ ← Same pair?
└────────┴───────────┴────────────┴──────────┘

Here:
→ Stu_ID alone? NOT unique (101 appears 3 times)
→ Course_ID alone? NOT unique (CS101 appears 3 times)
→ {Stu_ID + Course_ID} alone? Rows 1 and 4 have same values!
→ {Stu_ID + Course_ID + Semester}? UNIQUE for every row! ✓

So PRIMARY KEY = {Stu_ID, Course_ID, Semester}
This is a COMPOSITE KEY (3 attributes together)
```

> 💡 **Key Point:** Composite key = multiple attributes. Primary key CAN be composite.

---

## 🧠 CONCEPT 8: UNIQUE KEY

**Unique Key** = Similar to Primary Key — enforces uniqueness — BUT allows **NULL values**.

```
COMPARISON: PRIMARY KEY vs UNIQUE KEY

┌─────────────────┬──────────────────┬─────────────────┐
│ PROPERTY        │ PRIMARY KEY      │ UNIQUE KEY      │
├─────────────────┼──────────────────┼─────────────────┤
│ Uniqueness      │ Must be unique   │ Must be unique  │
│ NULL values     │ NOT ALLOWED      │ ALLOWED (once)  │
│ Per table       │ Only ONE         │ Can have MANY   │
│ Purpose         │ Main identifier  │ Alternate unique│
│                 │ of table         │ constraint      │
└─────────────────┴──────────────────┴─────────────────┘

Example: Email address column — unique for each user,
but some users may not provide email → can be NULL
→ Suitable for UNIQUE KEY, not PRIMARY KEY
```

> ⚠️ **PYQ TRAP:** "Which key allows NULL values?" → **UNIQUE KEY** allows NULL. **PRIMARY KEY** does NOT allow NULL.

---

## 🧠 CONCEPT 9: NATURAL KEY vs SURROGATE KEY

```
NATURAL KEY:
→ A key that has real-world meaning/significance
→ Examples: Aadhaar number, PAN card, Email address, Employee ID
→ Naturally exists in the data

SURROGATE KEY:
→ An artificially created key with NO real-world meaning
→ System-generated unique identifier
→ Examples: Auto-increment ID (1, 2, 3...), UUID
→ Used when no good natural key exists
→ Also called: Artificial Key, Synthetic Key

Which is better? Surrogate keys are preferred in practice:
→ Never changes (natural keys like email CAN change)
→ Simple integer (faster joins and lookups)
→ No business meaning leaking into the database
```

---

## 🧠 CONCEPT 10: COMPLETE KEY COMPARISON TABLE

```
┌────────────────┬──────────────────────────────────────────────────────┐
│ KEY TYPE       │ DEFINITION & PROPERTIES                              │
├────────────────┼──────────────────────────────────────────────────────┤
│ SUPER KEY      │ Any set of attributes that uniquely identifies       │
│                │ a tuple. Can have extra/unnecessary attributes.      │
│                │ BROADEST category. Every key is a super key.        │
├────────────────┼──────────────────────────────────────────────────────┤
│ CANDIDATE KEY  │ Minimal super key. No redundant attributes.         │
│                │ Multiple candidate keys possible per table.         │
├────────────────┼──────────────────────────────────────────────────────┤
│ PRIMARY KEY    │ One chosen candidate key. NOT NULL. UNIQUE.         │
│                │ Only ONE per table. Never changes ideally.          │
├────────────────┼──────────────────────────────────────────────────────┤
│ ALTERNATE KEY  │ Candidate keys NOT chosen as primary key.           │
│                │ Unique but not the main identifier.                 │
├────────────────┼──────────────────────────────────────────────────────┤
│ FOREIGN KEY    │ References PK of another table. Can be NULL.        │
│                │ Table can have MULTIPLE foreign keys.               │
│                │ Enforces Referential Integrity.                     │
├────────────────┼──────────────────────────────────────────────────────┤
│ COMPOSITE KEY  │ Key made of 2+ attributes together.                 │
│                │ Used when no single attribute is unique.            │
├────────────────┼──────────────────────────────────────────────────────┤
│ UNIQUE KEY     │ Enforces uniqueness like PK but allows NULL.        │
│                │ Multiple per table allowed.                         │
├────────────────┼──────────────────────────────────────────────────────┤
│ SURROGATE KEY  │ System-generated artificial key (no real meaning).  │
│                │ e.g., Auto-increment integers, UUID                 │
└────────────────┴──────────────────────────────────────────────────────┘
```

---

## 🧠 CONCEPT 11: PYQ-Focused Trick Questions on Keys

```
COMMON EXAM TRAPS:

TRAP 1: "A table can have multiple primary keys" → FALSE
         A table has EXACTLY ONE primary key.

TRAP 2: "Primary key can have NULL values" → FALSE
         Primary key CANNOT be NULL (Entity Integrity).

TRAP 3: "Foreign key must always have a value" → FALSE
         Foreign key CAN be NULL.

TRAP 4: "Candidate key = Primary key" → FALSE
         Candidate key is ANY minimal super key.
         Primary key is ONE chosen candidate key.

TRAP 5: "All super keys are candidate keys" → FALSE
         Candidate key ⊂ Super key (not the other way).

TRAP 6: "Composite key = Foreign key" → FALSE
         Composite key = key with multiple attributes.
         Foreign key = key referencing another table's PK.

TRAP 7: "Unique key does not allow NULL" → FALSE
         Unique key ALLOWS NULL (unlike primary key).
```

---

## 🎯 QUICK REVISION FLASH CARDS (CS — Keys)

```
┌──────────────────────────────────────────────────────┐
│ FC-1: HIERARCHY                                     │
│ Primary Key ⊂ Candidate Key ⊂ Super Key             │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-2: PRIMARY KEY — 3 hard rules                    │
│ 1. Only ONE per table                               │
│ 2. UNIQUE (no duplicates)                           │
│ 3. NOT NULL (can never be empty)                    │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-3: FOREIGN KEY — 3 key facts                     │
│ 1. References PK of ANOTHER table                   │
│ 2. CAN be NULL                                      │
│ 3. Table can have MULTIPLE FKs                      │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-4: NULL RULES                                    │
│ Primary Key → NULL NOT allowed                      │
│ Foreign Key → NULL ALLOWED                          │
│ Unique Key  → NULL ALLOWED                          │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-5: Candidate vs Super Key                        │
│ Candidate Key = Minimal Super Key                   │
│ Super Key may have extra attributes                 │
│ Candidate Key has NO extra attributes               │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-6: Referential Integrity                         │
│ FK value must EXIST in the referenced PK column     │
│ Cannot insert FK value that doesn't exist in PK!   │
└──────────────────────────────────────────────────────┘
```

---

# ══════════════════════════════════════════════════
# 📜 PART B: GENERAL STUDIES (HISTORY)
# Birsa Munda, Tribal Revolts & Peasant Movements
# (Bihar-Focus — HIGH PRIORITY for BPSC TRE)
# ══════════════════════════════════════════════════

---

## 🧠 CONCEPT 12: Context — Why Tribal & Peasant Revolts?

Before the "organized" freedom struggle of the 20th century, India saw **numerous rebellions by tribals, peasants, and zamindars** against British exploitation. These were driven by:

```
REASONS FOR TRIBAL/PEASANT REVOLTS:
──────────────────────────────────────────────────
1. ECONOMIC: Heavy taxation, revenue demands,
             moneylenders exploiting tribal land
2. SOCIAL:   British disrupting traditional tribal
             customs and forest rights
3. RELIGIOUS: Missionary activity threatening
              tribal culture and identity
4. POLITICAL: British taking away land rights,
              Forest Acts restricting access to
              forests that tribals depended on
5. DISPLACEMENT: Tribals forced off their land
                 by British policies
```

---

## 🧠 CONCEPT 13: BIRSA MUNDA — "Dharti Aaba" (Father of the Earth)

### ⭐ MOST IMPORTANT TOPIC FOR BPSC — BIRSA MUNDA

```
┌──────────────────────────────────────────────────────────┐
│                    BIRSA MUNDA                          │
├──────────────────────────────────────────────────────────┤
│ Born:         November 15, 1875                         │
│               Ulihatu village, Ranchi district,         │
│               (present-day Jharkhand)                   │
│ Community:    Munda tribe                               │
│ Nickname:     "Dharti Aaba" (Father of the Earth)      │
│               Also called "Bhagwan" (God) by tribals    │
│ Movement:     Ulgulan (meaning: "Great Tumult/Storm")   │
│ Region:       Chotanagpur (Bihar/Jharkhand)            │
│ Died:         June 9, 1900 (in British custody,        │
│               Ranchi Jail — officially "cholera")       │
│ Age at death: Only 25 years old!                       │
└──────────────────────────────────────────────────────────┘
```

### Background — The Munda Community's Grievances:
```
MUNDA TRIBAL GRIEVANCES:
──────────────────────────────────────────────────
→ KHUNTKATTI system: Traditional Munda land ownership
  (communal land held by the Munda family who cleared it)
  
→ British introduced ZAMINDARI SYSTEM → outsiders
  (Diku = outsiders) took over Munda land

→ "DIKU" (non-tribals = moneylenders, landlords, merchants)
  exploited Mundas through:
  - Moneylending at high interest
  - Forced labour (Beth-Begari)
  - Land grabbing when loans couldn't be repaid

→ Forest Acts (1882) restricted Munda access to forests
  → couldn't collect firewood, graze cattle

→ Christian missionaries pressuring conversions
```

### Birsa Munda's Religious and Political Mission:
```
BIRSA'S THREE-PRONGED MISSION:

1. RELIGIOUS/SPIRITUAL:
   → Declared himself a prophet: "Birsa Bhagwan"
   → Preached: One God (Sing Bonga), no idol worship,
     no liquor, no animal sacrifice
   → Combined elements of Christianity, Vaishnava
     Hinduism, and traditional Munda beliefs
   → His followers = "Birsaites"

2. SOCIAL REFORM:
   → Fight against the Diku (outsiders/exploiters)
   → Restore Munda land rights (Khuntkatti system)
   → End Beth-Begari (forced unpaid labour)
   → Oppose missionary conversions

3. POLITICAL/MILITARY:
   → "Ulgulan" = Armed uprising (1899–1900)
   → Aim: Establish Munda Raj (self-rule)
   → "Abua Raj" (Our Rule) replacing "Maharani Raj"
     (Queen's Rule = British Rule)
```

### The Ulgulan (1899–1900):
```
ULGULAN (THE GREAT TUMULT):
────────────────────────────────────────────────
→ Birsa organized armed revolt: December 24, 1899
  (Christmas Eve — strategic timing)
→ Birsa's followers attacked:
  - Police stations
  - Churches (symbol of missionary influence)
  - Property of zamindars and merchants

→ January 5, 1900: Battle at Dombari Hill (Ranchi)
  British opened fire on a gathering of tribals
  → MASSACRE at Dombari Hill
  → Many tribals killed (including women and children)

→ February 3, 1900: Birsa ARRESTED at Jamkopai forest,
  Chakradharpur

→ June 9, 1900: Birsa Munda DIED in Ranchi Jail
  (officially: cholera; suspected: British killed him)
  Age: 25 years

SIGNIFICANCE:
→ Birsa is the YOUNGEST person whose portrait is
  displayed in the Central Hall of Parliament
→ November 15 (his birthday) = "Janjati Gaurav Diwas"
  (Tribal Pride Day) declared in 2021
→ Jharkhand was formed on November 15, 2000
  (his birth anniversary — deliberate tribute!)
→ His struggle led to the
  CHOTA NAGPUR TENANCY ACT (1908)
  which protected tribal land rights
```

> 🏆 **Bihar/Jharkhand Connection:** Birsa Munda was from Chotanagpur — which was part of Bihar before Jharkhand was carved out in 2000. This is HIGHEST PRIORITY for BPSC Bihar context.

---

## 🧠 CONCEPT 14: Other Important Munda & Tribal Revolts

```
TIMELINE OF TRIBAL REVOLTS IN CHOTANAGPUR REGION:
──────────────────────────────────────────────────────

1. CHUAR UPRISING (1771–1809):
   Region: Midnapore, Bengal
   By: Chuar tribals
   Cause: Land revenue demands, famine

2. KOLS REVOLT / KOLS UPRISING (1831–32):
   Region: Chotanagpur (Bihar/Jharkhand)
   By: Kols (Mundas and Oraons combined)
   Cause: Alienation of land by zamindars,
          moneylenders
   Significance: First major tribal revolt in
                 Chotanagpur

3. SANTHAL HOOL (REBELLION) (1855–56):
   ─────────────────────────────────────
   Leaders: SIDO and KANHU (Murmu brothers)
   Also:    CHAND and BHAIRAV (brothers)
            PHULO and JHANO (sisters — also involved)
   Region:  Santhal Parganas (now Jharkhand/Bihar)
   Date:    June 30, 1855 (Hool Diwas)
   Cause:
   → Exploitation by "Mahajans" (moneylenders)
     and zamindars
   → Diku system — outsiders taking Santhal land
   → Oppressive revenue collection by Company
   
   What happened:
   → Sido declared "Company Rule over, God's Rule begins"
   → Massive armed uprising — thousands of Santhals
   → British suppressed it with army — 15,000+ Santhals killed
   → Sido and Kanhu were HANGED (1856)
   
   Legacy:
   → Led to creation of SANTHAL PARGANAS as a
     separate administrative district (1856)
   → June 30 = Hool Diwas (observed in Jharkhand)

4. MUNDA REVOLT (ULGULAN) (1899–1900):
   Leader: Birsa Munda (detailed above)

5. TAna BHAGAT MOVEMENT (1914):
   Leader: Jatra Oraon (later Tana Bhagat)
   Region: Chotanagpur (Ranchi)
   Nature: Socio-religious reform movement
           Influenced by Birsa Munda's legacy
   Method: Non-violence (unlike Birsa's armed revolt)
   Later: Merged with Gandhian Non-Cooperation Movement
```

---

## 🧠 CONCEPT 15: SANTHAL REVOLT (1855) — Detailed

```
SANTHAL HOOL — KEY FACTS:
┌──────────────────────────────────────────────────────┐
│ Year:    1855–56                                    │
│ Region:  Santhal Parganas (Rajmahal Hills area)    │
│          Present-day Jharkhand + parts of Bengal   │
│ Leaders: SIDO and KANHU Murmu (two brothers)       │
│ Date:    June 30, 1855 = HOOL DIWAS                │
│ Slogan:  "Abua Raj Seter Janaa, Maharani Raj Tundu │
│          Janaa" (Our rule has come, Queen's rule   │
│          has ended)                                │
│ Cause:   Exploitation by zamindars, mahajans       │
│          (moneylenders), and the East India Company│
│ Result:  Suppressed by British Army                │
│          → Santhal Parganas District created 1856  │
│          → Santhal Parganas Tenancy Act (1876)     │
└──────────────────────────────────────────────────────┘
```

---

## 🧠 CONCEPT 16: PEASANT MOVEMENTS — Key Revolts

```
IMPORTANT PEASANT REVOLTS:
────────────────────────────────────────────────────────

1. INDIGO (NEEL) REVOLT (1859–60):
   Region: Bengal (mainly Nadia, Jessore districts)
   By: Indigo cultivators forced by British planters
   Context: Farmers FORCED to grow indigo (Neel)
            on their best land at fixed low prices
   Leaders: Digambar Biswas, Bishnu Biswas
   Impact:
   → Dinabandhu Mitra wrote play "Nil Darpan" (1860)
     (Mirror of Indigo) exposing British cruelty
   → British set up Indigo Commission (1860)
   → Indigo cultivation declined

2. DECCAN RIOTS (1875):
   Region: Pune and Ahmednagar (Maharashtra)
   By: Peasants against moneylenders (mainly Marwari
       and Gujarati traders)
   Cause: Heavy debt burden from moneylenders
   Nature: Mainly social — burning of debt bonds

3. CHAMPARAN SATYAGRAHA (1917):
   Region: Champaran, Bihar
   Leader: GANDHI (first Satyagraha in India)
   Issue: Tinkathia system — indigo farmers forced
          to grow indigo on 3/20 of their land
   Result:
   → Gandhi's investigation exposed British injustice
   → Champaran Agrarian Act (1917) passed
   → Tinkathia system abolished
   → Gandhi became famous nationally

4. KHEDA SATYAGRAHA (1918):
   Region: Kheda, Gujarat
   Leader: Gandhi + Vallabhbhai Patel
   Issue: Despite crop failure, British demanded
          full land revenue
   Result: Revenue collection suspended

5. BARDOLI SATYAGRAHA (1928):
   Region: Bardoli, Surat (Gujarat)
   Leader: SARDAR VALLABHBHAI PATEL
   Issue: Government raised land revenue by 30%
   Result: Revenue hike withdrawn
   Note: "Sardar" title given to Patel by women
         of Bardoli after this movement's success
```

---

## 🧠 CONCEPT 17: ANUSHILAN SAMITI — Full Details

```
┌──────────────────────────────────────────────────────┐
│              ANUSHILAN SAMITI                       │
├──────────────────────────────────────────────────────┤
│ Founded:    1902                                    │
│ Location:   Calcutta (Bengal)                      │
│ Founders:   Satish Chandra Bose, P. Mitter,        │
│             Promotha Mitter                         │
│             (Aurobindo Ghosh also linked)          │
│ Inspired by: Bal Gangadhar Tilak's writings        │
│ Nature:     Secret revolutionary organization       │
│             focused on physical fitness + armed    │
│             resistance                             │
│                                                     │
│ DHAKA BRANCH (1906):                               │
│ → Founded by Pulin Bihari Das                      │
│ → More radical and militant                        │
│ → Involved in bombmaking, revolutionary acts       │
│                                                     │
│ KEY MEMBERS:                                        │
│ → Barindra Kumar Ghosh (Aurobindo's brother)       │
│ → Yugantar group emerged from Anushilan Samiti     │
│   activities                                       │
└──────────────────────────────────────────────────────┘
```

---

## 🧠 CONCEPT 18: Important British Acts Related to Tribal Areas

```
KEY LEGISLATION FOR TRIBAL PROTECTION:
──────────────────────────────────────────────────────

1. SANTHAL PARGANAS TENANCY ACT (1876):
   → Protected Santhal land from being sold to non-tribals
   → After the Santhal Hool (1855)

2. CHOTA NAGPUR TENANCY ACT (1908):
   → Protected tribal land rights in Chotanagpur
   → Direct result of Birsa Munda's Ulgulan
   → Restricted transfer of tribal land to non-tribals
   → Strengthened Khuntkatti rights

3. SCHEDULED AREAS AND SCHEDULED TRIBES
   (ARTICLES 244, 275 in Constitution):
   → After independence, 5th Schedule protects
     tribal areas
   → Governor has special powers for Scheduled Areas

Note for BPSC:
The Chota Nagpur Tenancy Act (1908) is a DIRECT
consequence of Birsa Munda's movement — very
frequently asked in BPSC Bihar context!
```

---

## 🎯 QUICK REVISION FLASH CARDS (GS — History)

```
┌──────────────────────────────────────────────────────┐
│ FC-1: BIRSA MUNDA — Core Facts                     │
│ Born: Nov 15, 1875 | Died: June 9, 1900 (age 25)  │
│ Place: Ulihatu, Ranchi | Community: Munda tribe    │
│ Movement: Ulgulan | Nickname: Dharti Aaba           │
│ Result: Chota Nagpur Tenancy Act (1908)             │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-2: SANTHAL HOOL — Core Facts                    │
│ Year: 1855–56 | Date: June 30 = Hool Diwas         │
│ Leaders: SIDO and KANHU Murmu                      │
│ Region: Santhal Parganas                           │
│ Result: Santhal Parganas district created           │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-3: KOLS REVOLT                                  │
│ Year: 1831–32 | Region: Chotanagpur                │
│ By: Kols (Mundas + Oraons)                         │
│ First major tribal revolt in Chotanagpur           │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-4: INDIGO REVOLT                                │
│ Year: 1859–60 | Region: Bengal                     │
│ Leaders: Digambar Biswas, Bishnu Biswas            │
│ Play: "Nil Darpan" by Dinabandhu Mitra             │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-5: CHAMPARAN — Bihar Connection                 │
│ Year: 1917 | Leader: Gandhi                        │
│ Issue: Tinkathia (3/20 land for indigo)            │
│ First Satyagraha in India by Gandhi                │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-6: BARDOLI SATYAGRAHA                           │
│ Year: 1928 | Leader: Vallabhbhai Patel             │
│ Title "Sardar" given by women of Bardoli           │
│ Issue: 30% revenue hike → reversed                 │
└──────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────┐
│ FC-7: JHARKHAND CONNECTION (BPSC-specific!)        │
│ Jharkhand formed: November 15, 2000                │
│ = Birsa Munda's birthday! (deliberate tribute)     │
│ Janjati Gaurav Diwas = November 15                 │
└──────────────────────────────────────────────────────┘
```

---

# ══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 37
# Attempt ALL 50 FIRST → Check answers ONLY at end
# ══════════════════════════════════════════════

---

## 💻 SECTION 1: CS — DBMS Keys (25 Questions)
### Easy → Medium → Hard → PYQ-Style → Tricky

> ⚠️ **DO NOT look at the answer key while solving. Write your answers (A/B/C/D/E) on paper first!**

---

**Q1. [EASY] Which type of key can uniquely identify a tuple and may contain extra/redundant attributes?**

(A) Candidate Key
(B) Primary Key
(C) Super Key
(D) More than one of the above
(E) None of the above

---

**Q2. [EASY] A Primary Key in a relational table CANNOT have which of the following?**

(A) Unique values
(B) Single attribute
(C) NULL values
(D) More than one of the above
(E) None of the above

---

**Q3. [EASY] How many Primary Keys can a single table have in a relational database?**

(A) As many as needed
(B) Two at most
(C) One and exactly one
(D) More than one of the above
(E) None of the above

---

**Q4. [EASY] A Foreign Key in a table refers to the __________ of another table.**

(A) Foreign Key
(B) Candidate Key
(C) Primary Key
(D) More than one of the above
(E) None of the above

---

**Q5. [EASY] The constraint that states "every value of a foreign key must exist in the referenced primary key" is called:**

(A) Entity Integrity Constraint
(B) Domain Constraint
(C) Referential Integrity Constraint
(D) More than one of the above
(E) None of the above

---

**Q6. [EASY] A key made up of two or more attributes to uniquely identify a tuple is called:**

(A) Super Key
(B) Alternate Key
(C) Composite Key
(D) More than one of the above
(E) None of the above

---

**Q7. [MEDIUM] What is the relationship between Candidate Key and Super Key?**

(A) Every Super Key is a Candidate Key
(B) Every Candidate Key is a Super Key, but not vice versa
(C) They are the same thing
(D) More than one of the above
(E) None of the above

---

**Q8. [MEDIUM] In a student table, both {StudentID} and {EmailAddress} can uniquely identify each student. If {StudentID} is chosen as the Primary Key, then {EmailAddress} becomes:**

(A) Foreign Key
(B) Super Key only
(C) Alternate Key
(D) More than one of the above
(E) None of the above

---

**Q9. [MEDIUM] Which of the following keys ALLOWS NULL values?**

(A) Primary Key
(B) Candidate Key
(C) Unique Key
(D) More than one of the above (Foreign Key also allows NULL)
(E) None of the above

---

**Q10. [MEDIUM] Consider a table with attributes {A, B, C, D}. If {A} alone can uniquely identify each tuple, which of the following is definitely a Super Key?**

(A) {B, C} only
(B) {A, B, C, D}
(C) {C, D} only
(D) More than one of the above (any set containing A is a super key)
(E) None of the above

---

**Q11. [MEDIUM] A table in a university database has the following candidate keys: {StudentID} and {AadhaarNumber}. The DBA has chosen {StudentID} as the primary key. Which statement is TRUE?**

(A) {AadhaarNumber} is now a foreign key
(B) {AadhaarNumber} is now an alternate key
(C) {AadhaarNumber} loses its uniqueness property
(D) More than one of the above
(E) None of the above

---

**Q12. [MEDIUM] In which scenario is a COMPOSITE KEY most commonly used as a Primary Key?**

(A) When the table has only one attribute
(B) When no single attribute can uniquely identify a tuple
(C) When the table has a foreign key
(D) More than one of the above
(E) None of the above

---

**Q13. [MEDIUM] A SURROGATE KEY is best described as:**

(A) A key that references another table's primary key
(B) A system-generated artificial identifier with no real-world meaning
(C) A key formed by combining two natural keys
(D) More than one of the above
(E) None of the above

---

**Q14. [HARD] A relation R has attributes: {EmployeeID, SSN, Name, Department, Phone}. Both EmployeeID and SSN uniquely identify each employee. What is the MINIMUM number of candidate keys in R?**

(A) One
(B) Two
(C) Three
(D) More than one of the above
(E) None of the above (depends on other attributes)

---

**Q15. [HARD] If a foreign key column in a child table contains a NULL value, which statement is CORRECT?**

(A) It violates Referential Integrity
(B) It is a valid situation — FK can be NULL
(C) It violates Entity Integrity
(D) More than one of the above
(E) None of the above

---

**Q16. [HARD] Consider the following table: ORDERS(OrderID, CustomerID, ProductID, Quantity). CustomerID is a FK referencing CUSTOMERS table. ProductID is a FK referencing PRODUCTS table. How many foreign keys does the ORDERS table have?**

(A) One
(B) Two
(C) Three
(D) More than one of the above
(E) None of the above

---

**Q17. [HARD] Which integrity constraint ensures that a Primary Key attribute can never contain a NULL value?**

(A) Referential Integrity
(B) Domain Integrity
(C) Entity Integrity
(D) More than one of the above
(E) None of the above

---

**Q18. [PYQ-STYLE] Which of the following statements about Primary Key is CORRECT?**

(A) A table can have more than one primary key
(B) Primary key values can be NULL if no better option exists
(C) Primary key uniquely identifies each tuple and cannot be NULL
(D) More than one of the above
(E) None of the above

---

**Q19. [PYQ-STYLE] Consider the following statements:
(I) Candidate Key is always a Super Key
(II) Super Key is always a Candidate Key
(III) Primary Key is always a Candidate Key
(IV) Alternate Key is a Primary Key

Which of the above are CORRECT?**

(A) I and II only
(B) I and III only
(C) II and IV only
(D) More than one of the above (I, II and III are correct)
(E) None of the above

---

**Q20. [PYQ-STYLE] A Foreign Key establishes which of the following?**

(A) Entity Integrity between rows of the same table
(B) Referential Integrity between two tables
(C) Domain constraint on attribute values
(D) More than one of the above
(E) None of the above

---

**Q21. [PYQ-STYLE] Which key uniquely identifies records but DIFFERS from the Primary Key in that it allows NULL?**

(A) Alternate Key
(B) Candidate Key
(C) Unique Key
(D) More than one of the above
(E) None of the above

---

**Q22. [TRICKY] In a table, a set of attributes {A, B} forms a Super Key. If removing attribute B still leaves {A} as a valid unique identifier, then {A, B} is:**

(A) A Candidate Key
(B) Only a Super Key (not a Candidate Key)
(C) A Primary Key
(D) More than one of the above
(E) None of the above

---

**Q23. [TRICKY] A teacher table has: {TeacherID, AadhaarNo, Name, Subject}. If both TeacherID and AadhaarNo are unique for every teacher, how many candidate keys does this table have (assuming no other attribute is unique)?**

(A) One
(B) Three
(C) Two
(D) More than one of the above
(E) None of the above

---

**Q24. [TRICKY] A student's email address changes because they graduate and lose their university email. This is a reason why email is NOT recommended as a:**

(A) Foreign Key
(B) Composite Key
(C) Primary Key
(D) More than one of the above
(E) None of the above

---

**Q25. [TRICKY] Which of the following CAN appear multiple times in the same table as different keys?**

(A) Primary Keys
(B) Foreign Keys
(C) Super Keys of the minimal type only
(D) More than one of the above (Foreign Keys and Unique Keys can appear multiple times)
(E) None of the above

---
---

## 📜 SECTION 2: GS — Birsa Munda, Tribal & Peasant Revolts (25 Questions)

> ⚠️ **Attempt ALL 25 questions first. No peeking at answers!**

---

**Q26. [EASY] Birsa Munda's movement is known as:**

(A) Tana Bhagat Movement
(B) Ulgulan
(C) Hool
(D) More than one of the above
(E) None of the above

---

**Q27. [EASY] Birsa Munda was born on:**

(A) November 15, 1875
(B) June 9, 1875
(C) January 30, 1880
(D) More than one of the above
(E) None of the above

---

**Q28. [EASY] The Santhal Hool of 1855 was led by:**

(A) Birsa Munda and Tana Bhagat
(B) Sido and Kanhu Murmu
(C) Jatra Oraon and Singhbhum leaders
(D) More than one of the above
(E) None of the above

---

**Q29. [EASY] Champaran Satyagraha (1917) was related to which crop issue?**

(A) Jute cultivation under forced conditions
(B) Rice cultivation and zamindari oppression
(C) Forced indigo cultivation (Tinkathia system)
(D) More than one of the above
(E) None of the above

---

**Q30. [EASY] The title "Sardar" was given to Vallabhbhai Patel after which movement?**

(A) Kheda Satyagraha (1918)
(B) Bardoli Satyagraha (1928)
(C) Non-Cooperation Movement (1920)
(D) More than one of the above
(E) None of the above

---

**Q31. [EASY] Birsa Munda's nickname "Dharti Aaba" means:**

(A) Son of the Earth
(B) Father of the Earth
(C) King of the Jungle
(D) More than one of the above
(E) None of the above

---

**Q32. [MEDIUM] The Chotanagpur Tenancy Act (1908) was a direct outcome of which movement?**

(A) Santhal Hool (1855)
(B) Tana Bhagat Movement (1914)
(C) Birsa Munda's Ulgulan (1899–1900)
(D) More than one of the above
(E) None of the above

---

**Q33. [MEDIUM] The Jharkhand state was carved out of Bihar on which date — and why is that date significant?**

(A) October 2, 2000 — Gandhi Jayanti
(B) November 15, 2000 — Birsa Munda's birth anniversary
(C) August 15, 2000 — Independence Day
(D) More than one of the above
(E) None of the above

---

**Q34. [MEDIUM] The play "Nil Darpan" written by Dinabandhu Mitra (1860) exposed the exploitation in which movement?**

(A) Santhal Hool
(B) Indigo (Neel) Revolt
(C) Deccan Riots
(D) More than one of the above
(E) None of the above

---

**Q35. [MEDIUM] The Santhal Parganas region was constituted as a separate district mainly as a result of:**

(A) Birsa Munda's Ulgulan (1899)
(B) Santhal Hool (1855)
(C) Kols Revolt (1831)
(D) More than one of the above
(E) None of the above

---

**Q36. [MEDIUM] "Hool Diwas" is observed on June 30 every year in Jharkhand to commemorate:**

(A) Birsa Munda's birth anniversary
(B) The Santhal Hool which began on June 30, 1855
(C) The formation of Jharkhand state
(D) More than one of the above
(E) None of the above

---

**Q37. [MEDIUM] The Kols Revolt (1831–32) in Chotanagpur was a combined uprising of which communities?**

(A) Mundas and Santhal tribes
(B) Mundas and Oraon tribes
(C) Santhal and Gond tribes
(D) More than one of the above
(E) None of the above

---

**Q38. [MEDIUM] In Birsa Munda's ideology, the term "Diku" referred to:**

(A) British colonial officers
(B) Non-tribal outsiders who exploited tribals (moneylenders, zamindars, merchants)
(C) The traditional tribal village head
(D) More than one of the above
(E) None of the above

---

**Q39. [MEDIUM] The Anushilan Samiti was founded in Calcutta in 1902. Its Dhaka branch was established by:**

(A) Barindra Kumar Ghosh
(B) Aurobindo Ghosh
(C) Pulin Bihari Das
(D) More than one of the above
(E) None of the above

---

**Q40. [HARD] Which of the following correctly describes the "Tinkathia System" that led to the Champaran Satyagraha?**

(A) Peasants had to cultivate indigo on 3/20 of their land for British planters
(B) Peasants had to pay 3 types of taxes on their land
(C) Three categories of land revenue were imposed on peasants
(D) More than one of the above
(E) None of the above

---

**Q41. [HARD] The "Khuntkatti" system referred to in Birsa Munda's movement was:**

(A) A British revenue collection method
(B) Traditional Munda communal land ownership system
(C) A form of forced labour (Beth-Begari) imposed on tribals
(D) More than one of the above
(E) None of the above

---

**Q42. [HARD] Birsa Munda was arrested on February 3, 1900, from which location?**

(A) Dombari Hill, Ranchi
(B) Ulihatu village
(C) Jamkopai forest, Chakradharpur
(D) More than one of the above
(E) None of the above

---

**Q43. [HARD] The "Dombari Hill" incident (January 5, 1900) during Birsa Munda's Ulgulan resulted in:**

(A) British being defeated and forced to retreat
(B) Birsa Munda's arrest at this location
(C) British opening fire on a tribal gathering — massacre
(D) More than one of the above
(E) None of the above

---

**Q44. [PYQ-STYLE] Consider the following pairs (Movement — Year):
(I) Santhal Hool — 1855
(II) Kols Revolt — 1831
(III) Birsa Munda's Ulgulan — 1885
(IV) Indigo Revolt — 1859

Which pairs are CORRECTLY matched?**

(A) I, II and IV only
(B) I and II only
(C) All four are correct
(D) More than one of the above
(E) None of the above

---

**Q45. [PYQ-STYLE] Which of the following is correctly matched?
(Person — Title/Nickname)**

(A) Birsa Munda — "Lokmanya"
(B) Birsa Munda — "Dharti Aaba"
(C) Sido Murmu — "Dharti Aaba"
(D) More than one of the above
(E) None of the above

---

**Q46. [PYQ-STYLE] Which of the following statements about the Tana Bhagat Movement is CORRECT?**

(A) It was founded by Birsa Munda in 1899
(B) It was started by Jatra Oraon in 1914 and was non-violent
(C) It was an armed revolt against British rule in Santhal Parganas
(D) More than one of the above
(E) None of the above

---

**Q47. [PYQ-STYLE] "Janjati Gaurav Diwas" (Tribal Pride Day) celebrated on November 15 was officially declared in:**

(A) 2000, when Jharkhand was formed
(B) 2021, by the Central Government
(C) 1947, at independence
(D) More than one of the above
(E) None of the above

---

**Q48. [TRICKY] In which jail did Birsa Munda die, and what was the official cause?**

(A) Hazaribagh Jail — tuberculosis
(B) Ranchi Jail — cholera
(C) Calcutta Jail — dysentery
(D) More than one of the above
(E) None of the above

---

**Q49. [TRICKY] Birsa Munda is the youngest person whose portrait is displayed in:**

(A) The Bihar Legislative Assembly
(B) The Central Hall of Parliament (Lok Sabha), New Delhi
(C) The Jharkhand Raj Bhavan
(D) More than one of the above
(E) None of the above

---

**Q50. [TRICKY] The Bardoli Satyagraha (1928) was launched against which specific issue?**

(A) Forced indigo cultivation
(B) A 30% hike in land revenue by the British government
(C) Caste discrimination against peasants
(D) More than one of the above
(E) None of the above

---

# ════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 37
# (Check ONLY after completing all 50 questions!)
# ════════════════════════════════════════════

---

## 💻 CS ANSWERS (Q1–Q25)

| Q# | Ans | Explanation |
|----|-----|-------------|
| Q1 | **(C)** | **Super Key** = any set of attributes that uniquely identifies, including sets with extra attributes |
| Q2 | **(C)** | Primary Key **CANNOT have NULL values** (Entity Integrity constraint) |
| Q3 | **(C)** | **Exactly ONE** primary key per table — neither zero nor two |
| Q4 | **(C)** | Foreign Key references the **Primary Key** of another (referenced) table |
| Q5 | **(C)** | **Referential Integrity** = every FK value must exist in referenced PK |
| Q6 | **(C)** | **Composite Key** = key formed by 2 or more attributes together |
| Q7 | **(B)** | Every Candidate Key IS a Super Key (minimal one), but Super Keys may have extra attributes making them NOT Candidate Keys |
| Q8 | **(C)** | When one candidate key is chosen as PK, remaining ones become **Alternate Keys** |
| Q9 | **(D)** | **More than one** — both Unique Key AND Foreign Key allow NULL values |
| Q10 | **(D)** | **More than one** — ANY set containing {A} is a super key: {A}, {A,B}, {A,B,C}, {A,B,C,D}, etc. |
| Q11 | **(B)** | AadhaarNumber remains unique — it becomes the **Alternate Key** |
| Q12 | **(B)** | Composite key used **when no single attribute is unique** by itself |
| Q13 | **(B)** | Surrogate Key = **artificially created, system-generated** identifier (no real-world meaning) |
| Q14 | **(B)** | {EmployeeID} and {SSN} are both minimal unique identifiers = **2 candidate keys** |
| Q15 | **(B)** | FK **CAN be NULL** — this does NOT violate referential integrity (null means "no relationship") |
| Q16 | **(B)** | ORDERS table has **two** foreign keys: CustomerID and ProductID |
| Q17 | **(C)** | **Entity Integrity** states PK cannot be NULL. Referential Integrity is about FK. |
| Q18 | **(C)** | Primary Key must be **unique AND NOT NULL** — this is the core definition |
| Q19 | **(B)** | I ✓ (Candidate Key IS a Super Key) | II ✗ (Super Key need NOT be Candidate Key) | III ✓ (Primary Key IS a Candidate Key) | IV ✗ (Alternate Key is NOT Primary Key) |
| Q20 | **(B)** | FK establishes **Referential Integrity between two tables** |
| Q21 | **(C)** | **Unique Key** — unique like PK but allows NULL (PK does not allow NULL) |
| Q22 | **(B)** | Since {A} alone uniquely identifies (making B redundant), {A,B} is **only a Super Key**, NOT a Candidate Key (not minimal) |
| Q23 | **(C)** | **Two** candidate keys: {TeacherID} and {AadhaarNo} |
| Q24 | **(C)** | Primary Key should ideally **never change** — a changeable value like email is a poor choice for PK |
| Q25 | **(D)** | **More than one** — Foreign Keys (multiple allowed per table) AND Unique Keys (multiple allowed per table) can appear multiple times |

---

## 📜 GS ANSWERS (Q26–Q50)

| Q# | Ans | Explanation |
|----|-----|-------------|
| Q26 | **(B)** | Birsa Munda's armed movement = **Ulgulan** (Great Tumult) |
| Q27 | **(A)** | Born **November 15, 1875** — Ulihatu, Ranchi |
| Q28 | **(B)** | Santhal Hool led by **Sido and Kanhu Murmu** (brothers) |
| Q29 | **(C)** | Tinkathia = forced to grow indigo on **3/20 (3 kathhas per bigha) of land** |
| Q30 | **(B)** | "Sardar" title given after **Bardoli Satyagraha (1928)** |
| Q31 | **(B)** | "Dharti Aaba" = **Father of the Earth** |
| Q32 | **(C)** | Chotanagpur Tenancy Act 1908 = direct result of **Birsa Munda's Ulgulan** |
| Q33 | **(B)** | Jharkhand formed **November 15, 2000** — deliberately chosen as Birsa Munda's birth anniversary |
| Q34 | **(B)** | "Nil Darpan" exposed cruelty in the **Indigo (Neel) Revolt** |
| Q35 | **(B)** | Santhal Parganas district created after the **Santhal Hool (1855)** |
| Q36 | **(B)** | Hool Diwas = **June 30, 1855** — when Santhal Hool began |
| Q37 | **(B)** | Kols Revolt = combined uprising of **Mundas and Oraon** tribes |
| Q38 | **(B)** | "Diku" = **non-tribal outsiders** (moneylenders, merchants, zamindars) who exploited tribals |
| Q39 | **(C)** | Dhaka branch of Anushilan Samiti = **Pulin Bihari Das** (1906) |
| Q40 | **(A)** | Tinkathia = peasants forced to grow indigo on **3/20 (3 kattha per bigha) of their land** |
| Q41 | **(B)** | Khuntkatti = **traditional Munda communal land ownership** by the family that cleared the forest |
| Q42 | **(C)** | Arrested at **Jamkopai forest, Chakradharpur** (Feb 3, 1900) |
| Q43 | **(C)** | Dombari Hill = British **fired on tribal gathering** → massacre of Munda men, women, children |
| Q44 | **(A)** | I ✓ (1855), II ✓ (1831), III ✗ (Ulgulan was 1899–1900, NOT 1885!), IV ✓ (1859) |
| Q45 | **(B)** | **Birsa Munda = "Dharti Aaba"** (Father of the Earth). "Lokmanya" = Bal Gangadhar Tilak |
| Q46 | **(B)** | Tana Bhagat Movement = **Jatra Oraon, 1914, non-violent**, later merged with Gandhi's movement |
| Q47 | **(B)** | Janjati Gaurav Diwas declared by Central Government in **2021** |
| Q48 | **(B)** | Died in **Ranchi Jail**, officially **cholera** (June 9, 1900) |
| Q49 | **(B)** | Youngest person's portrait in the **Central Hall of Parliament (Lok Sabha), New Delhi** |
| Q50 | **(B)** | Bardoli Satyagraha was against **30% hike in land revenue** |

---

# 📊 YOUR SCORE TRACKER — DAY 37

```
CS Score:  _____ / 25      Target: 23+/25
GS Score:  _____ / 25      Target: 23+/25
Total:     _____ / 50      Target: 46+/50

Review Mistakes:
→ CS below 20? Reread Key Hierarchy + FK/PK rules
→ GS below 20? Reread Birsa Munda and Santhal flash cards
```

---

# 🔁 NIGHT REVISION — 5 BULLET SUMMARY

Write these from memory before sleeping tonight:

**CS — DBMS Keys:**
1. Super Key ⊃ Candidate Key ⊃ Primary Key | Candidate Key = Minimal Super Key
2. Primary Key: Only ONE per table | NOT NULL | UNIQUE — non-negotiable!
3. Foreign Key: References PK of another table | CAN be NULL | Multiple FKs allowed
4. Unique Key: Like PK but ALLOWS NULL | Multiple per table
5. Referential Integrity: FK value must EXIST in referenced PK | violated if FK value absent

**GS — Tribal/Peasant Revolts:**
1. Birsa Munda: Born Nov 15, 1875 | Ulgulan (1899–1900) | Dharti Aaba | Died age 25 in jail
2. Santhal Hool: 1855 | Sido-Kanhu | Hool Diwas = June 30 | Santhal Parganas district created
3. Kols Revolt: 1831–32 | Mundas + Oraons | Chotanagpur | First major tribal revolt
4. Indigo Revolt: 1859–60 | Bengal | Nil Darpan play by Dinabandhu Mitra
5. Champaran (1917) Gandhi's first Satyagraha | Bardoli (1928) Patel → "Sardar" title

---

# 🚀 TOMORROW — DAY 38 PREVIEW

**CS:** ER Model & Relational Model — Entities, Attributes, Relationships, Cardinality (1:1, 1:N, M:N)
**GS:** Geography — Types of Soil in India, Black Soil, Cotton Belt, Red Soil, Laterite

*"Every key concept you master today = one question you won't miss on exam day!"* 🎯

---
*Day 37 of 170 | BPSC TRE 4.0 | CS + GS Dual Track | Target: TOP 50 RANK | 130+/150*
