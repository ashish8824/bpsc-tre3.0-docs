# 📅 BPSC TRE 4.0 — DAY 39
## CS Topic: Database Normalization (1NF, 2NF, 3NF, BCNF)
## GS Topic: India's Climate — Seasons, Monsoon, Rainfall Zones

> **Target:** 130+/150 | Top 50 Rank
> **Day Structure:** CS Concepts → GS Concepts → 25 CS MCQs → 25 GS MCQs → Answer Key at End

---

# ═══════════════════════════════════════════════
# 📘 PART 1: COMPUTER SCIENCE — NORMALIZATION
# ═══════════════════════════════════════════════

## 🎯 Why Normalization? The Core Problem

Imagine a poorly designed table storing student-course data:

```
┌──────────┬────────────┬──────────────┬─────────────────┬──────────┐
│ Stud_ID  │ Stud_Name  │ Course_ID    │ Course_Name     │ Teacher  │
├──────────┼────────────┼──────────────┼─────────────────┼──────────┤
│ 101      │ Rohan      │ CS101        │ C++ Basics      │ Mr. Sinha│
│ 101      │ Rohan      │ CS102        │ Data Structures │ Mr. Kumar│
│ 102      │ Priya      │ CS101        │ C++ Basics      │ Mr. Sinha│
└──────────┴────────────┴──────────────┴─────────────────┴──────────┘
```

**Problems with this design:**

| Anomaly | What Happens | Example |
|---------|-------------|---------|
| **Insert Anomaly** | Cannot insert data without other data | Can't add a course unless a student enrols |
| **Delete Anomaly** | Deleting one fact accidentally deletes another | Deleting Priya's record deletes CS101 info |
| **Update Anomaly** | Updating one fact requires updating many rows | If Mr. Sinha changes name → update ALL rows |

**Normalization = Process of organizing a database to reduce these anomalies and remove redundancy.**

---

## 📐 Functional Dependency — The Foundation

**Definition:** If knowing the value of attribute A allows you to determine attribute B, we say **A → B** (A functionally determines B).

```
A → B  means:  "For every value of A, there is exactly ONE value of B"
```

**Examples:**
```
Stud_ID → Stud_Name         (Each student ID maps to ONE name)
Course_ID → Course_Name     (Each course ID maps to ONE course name)
Stud_ID, Course_ID → Grade  (Both together determine the grade)
```

**Types of Functional Dependencies:**

```
┌─────────────────────────────────────────────────────────────────┐
│  FULL FD:     A,B → C  (C depends on BOTH A and B)             │
│  PARTIAL FD:  A,B → C  but also A → C alone (B is redundant)   │
│  TRANSITIVE:  A → B and B → C  therefore  A → C               │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📊 Normal Forms — The Ladder

```
        HIGHEST ──► BCNF  (Boyce-Codd Normal Form)  ← Strictest
                      │
                     3NF  ← Adequate for most real systems ★
                      │
                     2NF
                      │
        LOWEST  ──► 1NF  ← Starting point
                      │
                  Unnormalized (with repeating groups)
```

---

## 🔵 First Normal Form (1NF)

### Rule: Every cell must contain an ATOMIC (indivisible) value. No repeating groups.

**Violation Example:**
```
┌──────────┬────────────────────────────────────┐
│ Stud_ID  │ Courses                            │
├──────────┼────────────────────────────────────┤
│ 101      │ CS101, CS102, CS103               │  ← VIOLATION! Multi-valued
│ 102      │ CS101                              │
└──────────┴────────────────────────────────────┘
```

**Fixed (1NF):**
```
┌──────────┬───────────┐
│ Stud_ID  │ Course_ID │
├──────────┼───────────┤
│ 101      │ CS101     │
│ 101      │ CS102     │
│ 101      │ CS103     │
│ 102      │ CS101     │
└──────────┴───────────┘
```

### 1NF Requirements Checklist:
- ✅ Each column has atomic values (no comma-separated lists)
- ✅ Each row is unique (has a primary key)
- ✅ No repeating groups or arrays in a column
- ✅ Column values are of the same domain/type

> **🔔 Exam Trap:** A table with `{Phone1, Phone2, Phone3}` columns violates 1NF (repeating groups). Splitting into one row per phone fixes it.

---

## 🟡 Second Normal Form (2NF)

### Rule: Must be in 1NF + No PARTIAL DEPENDENCIES (every non-key attribute must depend on the WHOLE primary key)

**This applies ONLY when Primary Key is COMPOSITE (multiple columns).**

**Violation Example:**

Table: `Enrollment(Stud_ID, Course_ID, Stud_Name, Course_Name, Grade)`
Primary Key = (Stud_ID, Course_ID) — composite key

```
Stud_ID, Course_ID → Grade      ✅ Full dependency (OK)
Stud_ID → Stud_Name             ❌ PARTIAL dependency! (violation)
Course_ID → Course_Name         ❌ PARTIAL dependency! (violation)
```

**Why?** `Stud_Name` depends only on `Stud_ID`, not on the FULL composite key. This is a partial dependency.

**Fix — Decompose into 3 tables:**
```
Student(Stud_ID, Stud_Name)           ← Stud_Name fully depends on Stud_ID
Course(Course_ID, Course_Name)         ← Course_Name fully depends on Course_ID
Enrollment(Stud_ID, Course_ID, Grade) ← Grade depends on FULL composite key
```

```
DIAGRAM: Partial vs Full Dependency

Composite PK = (A, B)

         A ──────────────► X   ← PARTIAL (only A, not B) ❌
         │
         B ──────────────► Y   ← PARTIAL (only B, not A) ❌
         │
        A,B ─────────────► Z   ← FULL dependency ✅
```

> **🔔 Key PYQ Fact:** 2NF violation occurs ONLY when PK is composite. If PK is a single column, 1NF table is automatically in 2NF.

---

## 🟢 Third Normal Form (3NF)

### Rule: Must be in 2NF + No TRANSITIVE DEPENDENCIES (non-key attribute should NOT depend on another non-key attribute)

**Violation Example:**

Table: `Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name, Dept_Location)`
Primary Key = Emp_ID

```
Emp_ID → Emp_Name      ✅ Direct dependency (OK)
Emp_ID → Dept_ID       ✅ Direct dependency (OK)
Dept_ID → Dept_Name    ← Dept_Name depends on Dept_ID (non-key)
Dept_ID → Dept_Location ← Dept_Location depends on Dept_ID (non-key)
```

So: `Emp_ID → Dept_ID → Dept_Name` = **Transitive Dependency** ❌

**The chain:**
```
Emp_ID ──► Dept_ID ──► Dept_Name
    │                    │
    └────────────────────┘
         TRANSITIVE! (Dept_Name depends on PK only via Dept_ID)
```

**Fix — Decompose:**
```
Employee(Emp_ID, Emp_Name, Dept_ID)
Department(Dept_ID, Dept_Name, Dept_Location)
```

### 3NF — The Star Form for Real Databases
- 3NF is considered **adequate** for most real-world RDBMS designs
- Balances redundancy removal with query performance
- BCNF is stricter but can sometimes lose information (lossy decomposition possible)

> **🔔 Exam Trap:** "Which normal form is adequate for normal RDBMS design?" → Answer = **3NF**

---

## 🔴 Boyce-Codd Normal Form (BCNF)

### Rule: Must be in 3NF + For every functional dependency X → Y, X must be a SUPER KEY

**3NF allows non-key attributes to determine other non-key attributes in some cases. BCNF removes even that.**

**Violation Example (passes 3NF but fails BCNF):**

Table: `Exam(Student, Subject, Teacher)`
- Each teacher teaches only one subject
- Each student has one teacher per subject

FDs:
```
Student, Subject → Teacher   (PK = Student, Subject)
Teacher → Subject             ← Teacher is NOT a super key! ❌ BCNF violation
```

Even though this is in 3NF, it violates BCNF because `Teacher → Subject` has Teacher as a non-super-key determinant.

**Fix:**
```
Teacher_Subject(Teacher, Subject)
Student_Teacher(Student, Teacher)
```

---

## 📊 Normalization Quick Comparison Table

```
┌────────┬─────────────────────────────────────────────────────────────┐
│  Form  │  What It Eliminates                                         │
├────────┼─────────────────────────────────────────────────────────────┤
│  1NF   │  Repeating groups, multi-valued attributes (non-atomic)     │
│  2NF   │  Partial dependencies (on part of composite PK)            │
│  3NF   │  Transitive dependencies (non-key → non-key)               │
│  BCNF  │  Any FD where LHS is not a super key                       │
└────────┴─────────────────────────────────────────────────────────────┘
```

---

## 🧠 Memory Tricks

| Normal Form | Remember As |
|-------------|-------------|
| **1NF** | "**1 value per cell**" — No lists, no repeating groups |
| **2NF** | "**2 keys? Full dependency!**" — No partial deps on composite PK |
| **3NF** | "**3rd degree = no middlemen**" — No transitive deps |
| **BCNF** | "**Boss rules**" — Determinant must be a superkey, period |

**The Story Method:** Think of normalization as tidying a messy house:
- **1NF** = Put each item in its own box (atomic)
- **2NF** = Put each item in the RIGHT room (no partial deps)
- **3NF** = Don't let one item depend on another random item (no transitive)
- **BCNF** = Only the master key controls everything

---

## 🔥 PYQ High-Frequency Facts for Normalization

| Fact | Answer |
|------|--------|
| Normal form removing partial dependencies | 2NF |
| Normal form removing transitive dependencies | 3NF |
| Normal form adequate for RDBMS design | 3NF |
| If PK is single column, which NF is automatic? | 2NF (since no composite PK to have partial deps) |
| Storing same data in two places causes | Wasted space AND data inconsistency (BOTH) |
| A → B means | A functionally determines B |
| Stronger than 3NF | BCNF |
| BCNF is stricter than | 3NF |
| Decomposition goal | Lossless join + dependency preservation |

---

## 📝 Denormalization

After normalizing, sometimes we deliberately **denormalize** (join tables back) for **performance** reasons — fewer JOINs = faster queries.

- Used in **data warehouses** and **OLAP** systems
- Trade-off: redundancy vs query speed

---

# ═══════════════════════════════════════════════
# 🌍 PART 2: GS — INDIA'S CLIMATE
# ═══════════════════════════════════════════════

## 🌡️ Why India Has Unique Climate — The Basics

India's climate is classified as **Tropical Monsoon Climate** — influenced by:
1. **Latitudinal position** — Tropic of Cancer (23.5°N) passes through middle of India
2. **Himalayan barrier** — blocks cold Central Asian winds
3. **Indian Ocean, Arabian Sea, Bay of Bengal** — moisture sources
4. **Land-sea differential heating** — causes seasonal wind reversal (monsoon)

---

## 📅 India's Four Seasons

```
┌────────────────────┬─────────────────┬──────────────────────────────────────────┐
│   Season           │   Months        │   Key Features                           │
├────────────────────┼─────────────────┼──────────────────────────────────────────┤
│ Cold Weather       │ December–Feb    │ NE trade winds, low temp, fog in north   │
│ (Winter)           │                 │ Tamil Nadu gets rainfall (retreating)    │
├────────────────────┼─────────────────┼──────────────────────────────────────────┤
│ Hot Weather        │ March–May       │ Rising temp, Loo winds (hot dry N/NW)   │
│ (Pre-monsoon)      │                 │ Norwesters/Kalbaisakhi in Bengal/NE     │
├────────────────────┼─────────────────┼──────────────────────────────────────────┤
│ SW Monsoon         │ June–September  │ Main rainy season, 75–90% of rainfall   │
│ (Advancing)        │                 │ Two branches: Arabian Sea + Bay of Bengal│
├────────────────────┼─────────────────┼──────────────────────────────────────────┤
│ NE Monsoon         │ October–Nov     │ Retreating monsoon, SE India gets rain  │
│ (Retreating)       │                 │ Cyclones in Bay of Bengal               │
└────────────────────┴─────────────────┴──────────────────────────────────────────┘
```

---

## 🌊 The Monsoon Mechanism

**What is Monsoon?** From Arabic word **"Mausim"** = Season. It refers to the seasonal reversal of wind direction.

```
SUMMER (SW Monsoon — June to Sept):
Ocean ──────────────────────────────► Land
(Cool, Moist)     Winds blow FROM SEA TO LAND (Rain!)

WINTER (NE Monsoon — Oct to Feb):
Land ──────────────────────────────► Ocean
(Cool, Dry)       Winds blow FROM LAND TO SEA (Dry!)
```

### Why SW Monsoon Occurs:
1. In summer, the Thar Desert (Rajasthan) creates a **low pressure zone**
2. This pulls moisture-laden winds from the Indian Ocean northward
3. **Inter-Tropical Convergence Zone (ITCZ)** shifts northward
4. Winds deflect due to **Coriolis Effect** → become SW winds

### Two Branches of SW Monsoon:
```
           ARABIAN SEA BRANCH               BAY OF BENGAL BRANCH
           ─────────────────               ──────────────────────
Start:     Arabian Sea                     Bay of Bengal
Entry:     Kerala coast (June 1)           NE India, Assam first
Reaches:   Western Ghats, then Gujarat,   Then moves westward across
           Maharashtra, central India      Gangetic plains
Rain area: West coast, W. Ghats, Mumbai  Northeast India, Bengal,
           (heavy) Gujarat (light)         Bihar, eastern UP
```

> **🔔 Exam Fact:** Monsoon arrives in **Kerala by June 1** — this is the official onset date used by IMD (India Meteorological Department).

---

## ☔ Rainfall Distribution in India

```
HIGHEST RAINFALL:
━━━━━━━━━━━━━━━━
Mawsynram (Meghalaya) — Wettest place in the world
                        (~11,871 mm annual rainfall)
Cherrapunji (Meghalaya) — Second wettest
                          (~11,430 mm annual rainfall)
Both located in southern slopes of Khasi Hills
— Bay of Bengal branch funnels into hills (orographic rain)

LOWEST RAINFALL:
━━━━━━━━━━━━━━━
Leh (Ladakh/J&K) — lies in rain shadow of Himalayas
Jaisalmer (Rajasthan) — Thar Desert, very low (~100 mm)
Runn of Kutch — arid region
```

---

## 🌡️ Special Local Winds of India

| Wind Name | Region | Season | Nature |
|-----------|--------|---------|--------|
| **Loo** | Punjab, Rajasthan, UP, Haryana | May–June | Hot, dry westerly — causes heat strokes |
| **Kalbaisakhi / Norwesters** | West Bengal, Assam | Pre-monsoon (April–May) | Violent, dusty thunderstorms |
| **Mango Showers** | Karnataka, Kerala | Pre-monsoon | Light rain helps mango ripening |
| **Cherry Blossom Showers** | Karnataka (coffee region) | Pre-monsoon | Helps coffee flowering |
| **Andhis** | Rajasthan | Summer | Hot dusty whirlwinds |

---

## 🗺️ Climatic Regions of India (Koeppen Classification)

India has **6 major climatic regions** based on temperature and rainfall:

```
1. TROPICAL RAINFOREST (Af)
   Location: Western coast (Konkan, Malabar), NE India
   Features: High rainfall (>200 cm), no dry season, hot all year

2. TROPICAL SAVANNA / MONSOON (Aw)
   Location: Most of Peninsula (Deccan plateau, south India)
   Features: Distinct wet and dry season, moderate rainfall

3. TROPICAL SEMI-ARID STEPPE (BS)
   Location: Rain shadow areas — Deccan (leeward of W. Ghats),
             interior Tamil Nadu, S. Karnataka
   Features: Low rainfall (<50 cm), hot summers

4. TROPICAL HOT DESERT (BW)
   Location: Western Rajasthan, Rann of Kutch
   Features: Very low rainfall (<25 cm), extreme temperatures

5. HUMID SUBTROPICAL (Cwa)
   Location: Gangetic Plains, northern India
   Features: Hot summers, cool winters, moderate rainfall
   This is the most extensive climate zone in India

6. MOUNTAIN / HIGHLAND CLIMATE (H)
   Location: Himalayas, J&K, Himachal Pradesh, Uttarakhand
   Features: Temperature varies with altitude, heavy snowfall
```

---

## 🌧️ Types of Rainfall in India

```
┌──────────────────┬────────────────────────────────────────────────────┐
│ Type             │ Explanation & Example                              │
├──────────────────┼────────────────────────────────────────────────────┤
│ OROGRAPHIC/       │ Moist winds strike a mountain → forced upward →   │
│ RELIEF RAIN       │ cools → condenses → rains on WINDWARD side        │
│                  │ Example: Western Ghats get heavy rain,             │
│                  │ Deccan Plateau (leeward) stays dry                 │
├──────────────────┼────────────────────────────────────────────────────┤
│ CONVECTIONAL      │ Intense heating of land → hot air rises →         │
│ RAIN              │ cools rapidly → thunder and lightning + rain      │
│                  │ Example: Interior peninsular India in summer       │
├──────────────────┼────────────────────────────────────────────────────┤
│ CYCLONIC /        │ Cyclone brings heavy rain along its path          │
│ FRONTAL RAIN      │ Example: Cyclones in Bay of Bengal hit            │
│                  │ Odisha, Andhra Pradesh, Tamil Nadu                 │
└──────────────────┴────────────────────────────────────────────────────┘
```

---

## 🌊 El Niño and La Niña — Impact on India

| Phenomenon | What Happens | Effect on India's Monsoon |
|------------|--------------|---------------------------|
| **El Niño** | Warm water accumulates in eastern Pacific Ocean near Peru | **Weakens** SW Monsoon → drought tendency in India |
| **La Niña** | Cool water in eastern Pacific | **Strengthens** SW Monsoon → above-normal rainfall |
| **ENSO** | El Niño Southern Oscillation — the combined cycle | Affects global climate including Indian monsoon |

> **🔔 Exam Fact:** El Niño years often correlate with drought/poor monsoon in India. 2002, 2009 droughts were El Niño years.

---

## 📍 Bihar's Climate

Since this is BPSC, Bihar-specific climate is important:

- **Climate:** Humid Subtropical (Cwa)
- **Rainfall:** 1000–1500 mm annually, mostly June–September
- **Rivers:** Ganga, Gandak, Kosi, Son, Bagmati (seasonal flooding)
- **Floods:** North Bihar floods (Kosi river — "Sorrow of Bihar")
- **Droughts:** South Bihar (Palamu, Gaya) — less rainfall
- **Winters:** Cold December–January, fog common
- **Summers:** Hot dry winds (Loo) common in May–June

---

## 📝 High-Frequency GS PYQ Facts — Climate

| Question Trigger | Answer |
|-----------------|--------|
| Wettest place in India / World | Mawsynram (Meghalaya) |
| Official onset of SW Monsoon | Kerala, June 1 |
| "Mausim" meaning | Season (Arabic origin) |
| Hot dry wind of north India | Loo |
| Norwesters / Kalbaisakhi — region | West Bengal / Assam |
| Monsoon — wind type arriving in June | SW Monsoon |
| Tamil Nadu gets rain from | NE/Retreating Monsoon (Oct–Dec) |
| India's main rainy season | SW Monsoon (June–September) |
| El Niño effect on India | Drought / weak monsoon |
| Rain shadow area in India | Deccan Plateau (behind W. Ghats) |
| Thar Desert climate type | Tropical Hot Desert (BW) |
| Koeppen climate type of Gangetic plains | Cwa (Humid Subtropical) |
| ITCZ full form | Inter-Tropical Convergence Zone |
| Mango showers fall in | Karnataka, Kerala |
| Kosi river nickname | Sorrow of Bihar |

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS
# ═══════════════════════════════════════════════

> ⚠️ **INSTRUCTION:** Attempt ALL questions before looking at the Answer Key.
> The Answer Key with explanations is provided AFTER all 50 questions.
> Option D = "More than one of the above" | Option E = "None of the above"

---

# 💻 SECTION A: CS QUESTIONS — NORMALIZATION (Q1–Q25)

---

**Q1.** Which of the following anomalies is associated with an unnormalized or poorly normalized database?

(A) Insertion Anomaly
(B) Deletion Anomaly
(C) Updation Anomaly
(D) More than one of the above
(E) None of the above

---

**Q2.** A table is in First Normal Form (1NF) if:

(A) It has no partial functional dependencies
(B) It has no transitive functional dependencies
(C) Every column contains atomic (indivisible) values
(D) More than one of the above
(E) None of the above

---

**Q3.** Consider a relation R(A, B, C, D) where the Primary Key is (A, B) composite. If C depends only on A (not on B), this violates:

(A) 1NF
(B) 2NF
(C) 3NF
(D) More than one of the above
(E) None of the above

---

**Q4.** The process of removing redundancy and improving data integrity in a database is called:

(A) Denormalization
(B) Normalization
(C) Decomposition
(D) More than one of the above
(E) None of the above

---

**Q5.** If attribute A functionally determines attribute B, which of the following notations is correct?

(A) B → A
(B) A ↔ B
(C) A → B
(D) More than one of the above
(E) None of the above

---

**Q6.** A relation is in 2NF if and only if:

(A) It is in 1NF and has no partial dependencies
(B) It is in 1NF and has no transitive dependencies
(C) It has no repeating groups
(D) More than one of the above
(E) None of the above

---

**Q7.** Which normal form is considered adequate for most real-world RDBMS database designs?

(A) 1NF
(B) 2NF
(C) 3NF
(D) BCNF

---

**Q8.** Consider a table: Employee(Emp_ID, Dept_ID, Dept_Name). Here Emp_ID → Dept_ID and Dept_ID → Dept_Name. The dependency Emp_ID → Dept_Name (through Dept_ID) is called:

(A) Partial Dependency
(B) Full Dependency
(C) Transitive Dependency
(D) More than one of the above
(E) None of the above

---

**Q9.** Removing transitive dependencies from a relation converts it to:

(A) 1NF
(B) 2NF
(C) 3NF
(D) BCNF

---

**Q10.** A table with attributes (OrderID, ProductID, ProductName, Quantity) where Primary Key = (OrderID, ProductID). The dependency ProductID → ProductName is a:

(A) Full functional dependency
(B) Partial functional dependency
(C) Transitive dependency
(D) Multi-valued dependency

---

**Q11.** Which of the following statements about BCNF is CORRECT?

(A) BCNF is weaker than 3NF
(B) Every relation in BCNF is also in 3NF
(C) BCNF allows non-superkey determinants
(D) More than one of the above

---

**Q12.** Storing the same data in two different places in a database causes:

(A) Wasted storage space
(B) Data inconsistency
(C) Faster queries
(D) More than one of the above
(E) None of the above

---

**Q13.** A relation having a SINGLE ATTRIBUTE primary key is automatically in:

(A) 1NF only
(B) 2NF (since no partial dependency is possible with a single PK)
(C) 3NF
(D) BCNF

---

**Q14.** Consider a student record table where a student can have multiple phone numbers stored in the same column as "9876543210, 8765432109". This violates:

(A) 2NF
(B) 3NF
(C) 1NF
(D) BCNF

---

**Q15.** In normalization, the correct sequence (from lowest to highest) is:

(A) 1NF → 3NF → 2NF → BCNF
(B) 1NF → 2NF → 3NF → BCNF
(C) 2NF → 1NF → BCNF → 3NF
(D) BCNF → 3NF → 2NF → 1NF

---

**Q16.** Which of the following is NOT a goal of normalization?

(A) Eliminate data redundancy
(B) Prevent update anomalies
(C) Improve query performance at all costs
(D) Ensure data integrity

---

**Q17.** A functional dependency X → Y where X is a proper subset of the primary key is called:

(A) Full functional dependency
(B) Partial functional dependency
(C) Trivial dependency
(D) Transitive dependency

---

**Q18.** Consider: Student(Roll_No, Name, City, Pincode) where Pincode → City. If Roll_No is the primary key, which NF is violated?

(A) 1NF
(B) 2NF
(C) 3NF
(D) BCNF

---

**Q19.** The decomposition of a relation into smaller relations to achieve normalization should ideally be:

(A) Lossy
(B) Lossless
(C) Redundant
(D) More than one of the above

---

**Q20.** In BCNF, for every non-trivial functional dependency X → Y:

(A) X must be a candidate key or superkey
(B) Y must be a candidate key
(C) X must be a non-key attribute
(D) Y must depend on partial key

---

**Q21.** A table Employee(EmpID, EmpName, DeptID, DeptName, DeptLocation) with EmpID as primary key. Dept_ID → DeptName and Dept_ID → DeptLocation. To achieve 3NF, we should:

(A) Split into Employee(EmpID, EmpName) and Department(DeptID, DeptName, DeptLocation, EmpID)
(B) Split into Employee(EmpID, EmpName, DeptID) and Department(DeptID, DeptName, DeptLocation)
(C) Keep the table as is — it is already in 3NF
(D) Remove DeptID from the table

---

**Q22.** Which normal form specifically deals with the problem where a determinant in a functional dependency is NOT a superkey?

(A) 1NF
(B) 2NF
(C) 3NF
(D) BCNF

---

**Q23.** The term "denormalization" refers to:

(A) Converting an unnormalized table to 1NF
(B) Deliberately introducing redundancy to improve read/query performance
(C) Removing all functional dependencies
(D) Achieving BCNF from 3NF

---

**Q24.** Consider a relation R(A, B, C) with functional dependencies: A → B, B → C. Which of the following is NOT a violation of 3NF if A is the primary key?

(A) B → C is a transitive dependency
(B) A → C is derived transitively
(C) A → B is a direct dependency — this is fine
(D) More than one of the above

---

**Q25.** Which of the following is the correct statement about normalization forms?

(A) A relation in BCNF may not be in 3NF
(B) A relation in 3NF is always in BCNF
(C) A relation in BCNF is always in 3NF
(D) 2NF and 3NF are the same

---

# 🌍 SECTION B: GS QUESTIONS — INDIA'S CLIMATE (Q26–Q50)

---

**Q26.** Which of the following is the wettest place in India and also considered the wettest place in the world?

(A) Cherrapunji, Meghalaya
(B) Mawsynram, Meghalaya
(C) Agumbe, Karnataka
(D) Lachen, Sikkim

---

**Q27.** The word "Monsoon" is derived from:

(A) Sanskrit word "Mausam"
(B) Arabic word "Mausim"
(C) Portuguese word "Monção"
(D) More than one of the above
(E) None of the above

---

**Q28.** The SW Monsoon officially arrives in India by which date?

(A) 15th May — Andhra Pradesh
(B) 1st June — Kerala
(C) 15th June — Maharashtra
(D) 1st July — Delhi

---

**Q29.** Which season does Tamil Nadu receive most of its rainfall?

(A) SW Monsoon (June–September)
(B) Retreating/NE Monsoon (October–December)
(C) Winter (December–February)
(D) Pre-monsoon (March–May)

---

**Q30.** Kalbaisakhi / Norwesters are violent pre-monsoon storms associated with which region?

(A) Rajasthan and Gujarat
(B) West Bengal and Assam
(C) Kerala and Tamil Nadu
(D) Punjab and Haryana

---

**Q31.** The hot dry wind called "Loo" blows over which region of India?

(A) Kerala and Karnataka
(B) Punjab, Haryana, UP, Rajasthan
(C) Bihar and Jharkhand
(D) More than one of the above
(E) None of the above

---

**Q32.** The Deccan Plateau lies in the rain shadow of the Western Ghats. What type of rainfall does the Deccan Plateau receive?

(A) Heavy orographic rainfall
(B) Very little — it is on the leeward side
(C) Cyclonic rainfall throughout the year
(D) No rainfall at all

---

**Q33.** Which of the following climatic phenomena WEAKENS the South-West Monsoon in India?

(A) La Niña
(B) El Niño
(C) ITCZ shifting northward
(D) Low pressure over Thar Desert

---

**Q34.** "Mango Showers" — pre-monsoon rains that help in the ripening of mangoes — fall mainly in:

(A) Maharashtra and Gujarat
(B) Karnataka and Kerala
(C) Odisha and West Bengal
(D) Uttar Pradesh and Bihar

---

**Q35.** According to the Koeppen classification, which climate type covers the maximum area in India?

(A) Tropical Rainforest (Af)
(B) Hot Desert (BW)
(C) Humid Subtropical (Cwa) — Gangetic Plains
(D) Highland/Mountain (H)

---

**Q36.** The ITCZ stands for:

(A) Indian Thermal Convergence Zone
(B) Inter-Tropical Convergence Zone
(C) International Tropical Climate Zone
(D) Intra-Terrestrial Cyclonic Zone

---

**Q37.** Which river in Bihar is known as the "Sorrow of Bihar" due to recurring floods?

(A) Ganga
(B) Son
(C) Gandak
(D) Kosi

---

**Q38.** Orographic / Relief rainfall occurs when:

(A) Hot air rises convectively due to surface heating
(B) Moist winds are forced to rise over a mountain barrier
(C) Cold and warm air masses meet at a front
(D) Cyclonic winds converge at a low pressure center

---

**Q39.** India's climate is broadly classified as:

(A) Equatorial Climate
(B) Tropical Monsoon Climate
(C) Mediterranean Climate
(D) Continental Climate

---

**Q40.** The Western Ghats receive very heavy rainfall on their western slopes because:

(A) They face the retreating monsoon
(B) The SW Monsoon hits the windward (western) slopes causing orographic rain
(C) Cyclones frequently hit the western coast
(D) Convectional rain is more intense here

---

**Q41.** During which season do cyclones most frequently strike the eastern coast (Odisha, Andhra Pradesh, Tamil Nadu) of India?

(A) SW Monsoon (June–July)
(B) Winter (December–January)
(C) Retreating Monsoon / Post-monsoon (Oct–Nov)
(D) Pre-monsoon (March–May)

---

**Q42.** The Thar Desert (Western Rajasthan) has very low rainfall because:

(A) It lies in the rain shadow of the Aravallis
(B) The SW monsoon loses its moisture before reaching Rajasthan, and the Aravallis are parallel to the monsoon winds
(C) It is too close to the equator
(D) The winds are offshore throughout the year

---

**Q43.** Leh (Ladakh) is one of the driest places in India because:

(A) It has no rivers nearby
(B) It lies in the rain shadow of the Himalayas, blocking both monsoon branches
(C) It is at sea level
(D) More than one of the above

---

**Q44.** Which two branches does the South-West Monsoon divide into when entering India?

(A) Himalayan Branch and Peninsular Branch
(B) Arabian Sea Branch and Bay of Bengal Branch
(C) Eastern Branch and Western Branch
(D) More than one of the above

---

**Q45.** "Cherry Blossom Showers" that help in flowering of coffee plants occur in:

(A) Tamil Nadu
(B) Kerala
(C) Karnataka
(D) Andhra Pradesh

---

**Q46.** The monsoon trough (axis of low pressure) lies over the northern plains during peak monsoon. When it shifts northward toward the Himalayas, what typically happens?

(A) Rainfall increases over northern plains
(B) A break in the monsoon occurs — reduced rainfall over plains
(C) Monsoon withdraws immediately
(D) The Arabian Sea branch intensifies

---

**Q47.** The Coriolis effect on the South-West Monsoon causes the winds to deflect in which direction in the Northern Hemisphere?

(A) Left (westward)
(B) Right (eastward/northeastward)
(C) No deflection — straight northward
(D) Downward toward land

---

**Q48.** Bihar's climate can best be described as:

(A) Tropical Savanna (Aw)
(B) Hot Desert (BW)
(C) Humid Subtropical (Cwa)
(D) Tropical Rainforest (Af)

---

**Q49.** Which of the following pairs is CORRECTLY matched?

(A) Loo — West Bengal | Kalbaisakhi — Rajasthan
(B) Loo — North India (Punjab/UP/Rajasthan) | Kalbaisakhi — West Bengal/Assam
(C) Loo — Kerala | Kalbaisakhi — Punjab
(D) Loo — Tamil Nadu | Kalbaisakhi — Gujarat

---

**Q50.** Consider the following statements about Indian monsoon:
1. El Niño strengthens the SW Monsoon in India
2. La Niña is associated with above-normal rainfall in India
3. ENSO stands for El Niño Southern Oscillation

Which of the above statements is/are CORRECT?

(A) Only 1
(B) Only 2 and 3
(C) Only 1 and 3
(D) More than one of the above — 2 and 3 only
(E) All three (1, 2, and 3)

---

# ═══════════════════════════════════════════════
# 🔑 ANSWER KEY — ALL 50 QUESTIONS
# ═══════════════════════════════════════════════

> Scroll here ONLY after attempting all 50 questions!

---

## 💻 CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| 1 | **(D)** | All three — Insertion, Deletion, and Updation anomalies occur in un-normalized databases. |
| 2 | **(C)** | 1NF requires every column to have atomic (indivisible) values. No multi-valued or composite attributes. |
| 3 | **(B)** | C depends only on A (part of composite PK), not on the full key (A,B). This is a partial dependency → violates 2NF. |
| 4 | **(B)** | Normalization is the systematic process of reducing redundancy and organizing a database. |
| 5 | **(C)** | A → B is the correct notation for "A functionally determines B". |
| 6 | **(A)** | 2NF = 1NF + No partial dependencies on composite primary key. |
| 7 | **(C)** | **3NF is considered adequate for normal RDBMS design.** This is a direct PYQ fact — memorize it. |
| 8 | **(C)** | Emp_ID → Dept_ID → Dept_Name forms a chain through a non-key attribute = Transitive Dependency. |
| 9 | **(C)** | **3NF eliminates transitive dependencies.** 2NF eliminates partial deps. |
| 10 | **(B)** | ProductID → ProductName: ProductID is PART of the composite PK (OrderID, ProductID). Depends on PART of PK = partial functional dependency. |
| 11 | **(B)** | Every BCNF relation is in 3NF (BCNF is stricter). But 3NF does NOT guarantee BCNF. |
| 12 | **(D)** | Storing data in two places causes BOTH wasted space AND data inconsistency — classic PYQ answer is D. |
| 13 | **(B)** | With a single-attribute PK, there can be no partial dependency (which only happens with composite PK). So the relation is automatically in 2NF. |
| 14 | **(C)** | Storing multiple phone numbers in one cell = non-atomic value = violates **1NF**. |
| 15 | **(B)** | 1NF → 2NF → 3NF → BCNF — this is the correct ascending ladder of normalization. |
| 16 | **(C)** | Normalization actually MAY DECREASE query performance (more JOINs needed). "Improve query performance at all costs" is NOT a goal of normalization. |
| 17 | **(B)** | When X is a PROPER SUBSET of the composite PK and X → Y, it is a Partial Functional Dependency. |
| 18 | **(C)** | Pincode → City: Pincode is a non-key attribute determining another non-key attribute (City). This is a transitive dependency → violates **3NF**. |
| 19 | **(B)** | Decomposition should be **lossless** (no data loss when tables are joined back). Lossy decomposition is bad design. |
| 20 | **(A)** | **BCNF rule:** For every FD X → Y, X must be a superkey or candidate key. No exceptions. |
| 21 | **(B)** | Correct: Move Dept info to a separate Dept table. Employee keeps DeptID as FK. This eliminates transitive dep → achieves 3NF. |
| 22 | **(D)** | **BCNF** is specifically about ensuring that every determinant in an FD is a superkey. 3NF still allows some exceptions. |
| 23 | **(B)** | Denormalization = deliberately adding controlled redundancy back to improve read/query performance. Used in data warehouses. |
| 24 | **(C)** | A → B with A as PK is a direct full dependency — perfectly fine. The violation is B → C (transitive). |
| 25 | **(C)** | **BCNF is stricter than 3NF.** Any relation in BCNF automatically satisfies 3NF. But 3NF doesn't guarantee BCNF. |

---

## 🌍 GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| 26 | **(B)** | **Mawsynram** (Meghalaya) is the wettest place in India and world (~11,871 mm). Cherrapunji was previously considered the wettest. |
| 27 | **(B)** | "Monsoon" comes from **Arabic "Mausim"** = Season. Direct PYQ fact. |
| 28 | **(B)** | SW Monsoon officially arrives in **Kerala by June 1**. This is the standard IMD onset date. |
| 29 | **(B)** | Tamil Nadu (eastern coast) is in rain shadow during SW Monsoon. It gets rain from the **retreating/NE monsoon** (Oct–Dec). |
| 30 | **(B)** | Kalbaisakhi / Norwesters are violent pre-monsoon thunderstorms characteristic of **West Bengal and Assam**. |
| 31 | **(B)** | **Loo** = hot, dry wind blowing in **Punjab, Haryana, UP, and Rajasthan** during May–June. Can be fatal. |
| 32 | **(B)** | The Deccan Plateau is on the **leeward (rain shadow) side** of the Western Ghats → receives very little rainfall. |
| 33 | **(B)** | **El Niño** = warm eastern Pacific → weakens SW Monsoon → drought tendency in India. La Niña strengthens it. |
| 34 | **(B)** | **Mango Showers** fall in **Karnataka and Kerala** — help mango ripening. |
| 35 | **(C)** | The **Humid Subtropical (Cwa)** climate covering the Gangetic Plains is the most extensive climate zone in India. |
| 36 | **(B)** | **ITCZ = Inter-Tropical Convergence Zone** — the belt near equator where trade winds converge; shifts north in summer. |
| 37 | **(D)** | **Kosi River** is called the "Sorrow of Bihar" — it changes course frequently, causing massive floods in North Bihar. |
| 38 | **(B)** | **Orographic rain** = moist winds forced upward over a mountain → cools → condenses → rains on windward side. |
| 39 | **(B)** | India has a **Tropical Monsoon Climate** — characterized by distinct wet and dry seasons with seasonal wind reversal. |
| 40 | **(B)** | SW Monsoon hits the **windward (western) slopes** of W. Ghats → forced upward → orographic rain. Leeward (eastern/Deccan) stays dry. |
| 41 | **(C)** | Cyclones in Bay of Bengal most frequently strike during **October–November** (retreating/post-monsoon season). |
| 42 | **(B)** | The Aravallis run **parallel** to the Arabian Sea branch of monsoon (SW to NE) — winds pass alongside rather than being blocked, so little rain falls in Rajasthan. |
| 43 | **(B)** | Leh/Ladakh is in the **rain shadow of the Himalayas** — both the Arabian Sea and Bay of Bengal monsoon branches are blocked by the high mountains. |
| 44 | **(B)** | SW Monsoon splits into two: **Arabian Sea Branch** (enters Kerala, western coast) and **Bay of Bengal Branch** (enters NE India, Assam). |
| 45 | **(C)** | **Cherry Blossom Showers** fall in **Karnataka** (coffee growing region) during pre-monsoon, helping coffee plants flower. |
| 46 | **(B)** | When the monsoon trough shifts northward toward Himalayas, a **break in the monsoon** occurs — the plains get less rain temporarily. |
| 47 | **(B)** | **Coriolis effect** in the Northern Hemisphere deflects winds to the **right** — so northward-moving winds become SW winds (deflected to the right = NE deflection in original motion). |
| 48 | **(C)** | Bihar has **Humid Subtropical (Cwa)** climate — hot summers, cool winters, rainfall mainly in monsoon season. |
| 49 | **(B)** | Correctly matched: **Loo → North India (Punjab/UP/Rajasthan)** and **Kalbaisakhi → West Bengal/Assam**. |
| 50 | **(B)** | Statement 1 is WRONG (El Niño WEAKENS monsoon). Statements 2 and 3 are correct. Answer = 2 and 3 only = **(B)**. |

---

# ═══════════════════════════════════════════════
# 🎯 TOPPER'S CORNER — DAY 39 CHECKLIST
# ═══════════════════════════════════════════════

## CS Normalization — Must-Know Before Exam Day

- [ ] Can explain all 4 normal forms from memory in 30 seconds each
- [ ] Know: 3NF = adequate for normal RDBMS design (direct PYQ)
- [ ] Know: 2NF eliminates partial dependencies
- [ ] Know: 3NF eliminates transitive dependencies
- [ ] Know: BCNF = every determinant must be a superkey
- [ ] Know: Redundant data = wasted space + inconsistency (BOTH)
- [ ] Know: Single-column PK → automatically in 2NF
- [ ] Practiced identifying FDs in a table

## GS Climate — Must-Know Before Exam Day

- [ ] Mawsynram = wettest (Meghalaya) — NOT Cherrapunji
- [ ] Monsoon from Arabic "Mausim"
- [ ] SW Monsoon: June 1 Kerala onset
- [ ] Tamil Nadu rain = from NE/Retreating Monsoon (NOT SW Monsoon)
- [ ] El Niño = weak monsoon; La Niña = strong monsoon
- [ ] Loo = North India dry hot wind
- [ ] Kalbaisakhi = West Bengal/Assam pre-monsoon storms
- [ ] Kosi = Sorrow of Bihar
- [ ] ITCZ = Inter-Tropical Convergence Zone

---

## 📊 Score Yourself

| Score | What It Means | Action |
|-------|--------------|--------|
| 45–50 | 🏆 Excellent — Topper Level | Revise once and move on |
| 38–44 | ✅ Good — On Track | Re-read missed topics tonight |
| 30–37 | ⚠️ Average — Need Revision | Re-read concepts + retry tomorrow |
| <30 | ❌ Need more practice | Do full concept re-read today |

---

## 📅 Day 40 Preview

**CS:** SQL Commands — DDL, DML, DCL, TCL (CREATE, ALTER, DROP, SELECT, INSERT, COMMIT, ROLLBACK)
**GS:** Biology — Photoperiodism (Garner & Allard), Plant Growth, Hormones

Key PYQ Fact for tomorrow: COMMIT = permanent. ROLLBACK = undo. TRUNCATE = cannot be rolled back.

---

*Day 39 Complete ✅ | Target: 130+/150 | You are on track for TOP 50! 🎯*
