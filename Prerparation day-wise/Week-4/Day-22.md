# 📅 DAY 22 — BPSC TRE 4.0 TOPPER GUIDE
## CS: Singly Linked List (Complete) | GS: Indian Polity — Fundamental Rights
### Phase 1 | Week 4 | Target: TOP RANK

---

> **🎯 Today's Targets:**
> - CS: Master Singly Linked List — all operations, complexities, PYQ traps
> - GS: Master Fundamental Rights (Articles 12–35) — most tested Polity topic
> - Solve: 25 CS + 25 GS PYQ-style questions (answers ONLY at end)

---

# ═══════════════════════════════════════════════
# 🖥️ PART 1: COMPUTER SCIENCE
## SINGLY LINKED LIST — COMPLETE TOPPER GUIDE
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A LINKED LIST?

A **Linked List** is a **linear data structure** where elements (called **nodes**) are stored at **non-contiguous memory locations**, connected via **pointers**.

```
ARRAY (contiguous memory):
[10][20][30][40][50]
 100 101 102 103 104   ← memory addresses

LINKED LIST (non-contiguous memory):
[10|→300]   [20|→550]   [30|→120]   [40|NULL]
  100           300         550         120
```

> 🔑 **KEY INSIGHT:** In an array, elements sit next to each other. In a linked list, they are scattered in memory — each node has a **pointer to the next node's address**.

---

## 📌 SECTION 2: NODE STRUCTURE

A node in a **Singly Linked List (SLL)** has exactly **TWO parts**:

```
+--------+----------+
|  DATA  |   NEXT   |
|  part  | (pointer)|
+--------+----------+
    ^           ^
  stores      stores address
  the value   of next node
```

### C++ Node Structure:
```cpp
struct Node {
    int data;       // stores the value
    Node* next;     // pointer to next node
};
```

### Java Node Structure:
```java
class Node {
    int data;
    Node next;      // reference to next node
    Node(int d) { data = d; next = null; }
}
```

---

## 📌 SECTION 3: TYPES OF LINKED LISTS

```
┌─────────────────────────────────────────────────────┐
│                  LINKED LISTS                        │
│                      │                               │
│        ┌─────────────┼─────────────┐                │
│        │             │             │                 │
│   SINGLY LL    DOUBLY LL    CIRCULAR LL              │
│  (1 pointer) (2 pointers) (last→first)               │
└─────────────────────────────────────────────────────┘
```

| Type | Pointers per Node | Traversal | Memory |
|------|-------------------|-----------|--------|
| Singly LL | 1 (next only) | Forward only | Less |
| Doubly LL | 2 (prev + next) | Both directions | More |
| Circular LL | 1 (last→first) | Forward (circular) | Less |

---

## 📌 SECTION 4: SINGLY LINKED LIST — VISUAL DIAGRAM

```
HEAD
 │
 ▼
[10 | •]──►[20 | •]──►[30 | •]──►[40 | NULL]
  Node1       Node2       Node3       Node4
```

- **HEAD** = pointer to the first node
- **NULL** at last node = marks end of list
- If HEAD = NULL → **empty list**

---

## 📌 SECTION 5: OPERATIONS ON SINGLY LINKED LIST

### 5.1 TRAVERSAL
Visit each node one by one from HEAD to NULL.

```
Algorithm: Traverse(HEAD)
  curr = HEAD
  while curr ≠ NULL:
      print curr.data
      curr = curr.next
```

```
Step 1: curr → [10|→]──►[20|→]──►[30|NULL]
              ^curr

Step 2: curr → [10|→]──►[20|→]──►[30|NULL]
                          ^curr

Step 3: curr → [10|→]──►[20|→]──►[30|NULL]
                                    ^curr
Step 4: curr = NULL → STOP
Output: 10 20 30
```

**Time Complexity: O(n)** — must visit every node
**Space Complexity: O(1)**

---

### 5.2 INSERTION — THREE CASES

#### CASE 1: Insert at BEGINNING ← O(1)

```
BEFORE:
HEAD──►[20|→]──►[30|→]──►[40|NULL]

Insert 10 at beginning:
Step 1: Create new node [10|→]
Step 2: newNode.next = HEAD
Step 3: HEAD = newNode

AFTER:
HEAD──►[10|→]──►[20|→]──►[30|→]──►[40|NULL]
```

```cpp
void insertAtBeginning(Node*& head, int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->next = head;   // point to old first
    head = newNode;         // update head
}
```

**Time: O(1)** ← This is FAST! No traversal needed.

---

#### CASE 2: Insert at END ← O(n)

```
BEFORE:
HEAD──►[10|→]──►[20|→]──►[30|NULL]

Insert 40 at end:
Step 1: Create [40|NULL]
Step 2: Traverse to last node (30)
Step 3: lastNode.next = newNode

AFTER:
HEAD──►[10|→]──►[20|→]──►[30|→]──►[40|NULL]
```

**Time: O(n)** ← Must traverse entire list to find last node.

---

#### CASE 3: Insert at Middle (after given position) ← O(n)

```
Insert 25 after position 2:

BEFORE: [10]→[20]→[30]→[40]
                ↑pos=2

Step 1: Traverse to position 2 → reach node [20]
Step 2: newNode.next = node[20].next (→[30])
Step 3: node[20].next = newNode

AFTER: [10]→[20]→[25]→[30]→[40]
```

**Time: O(n)** ← Traversal needed

---

### 5.3 DELETION — THREE CASES

#### CASE 1: Delete from BEGINNING ← O(1)

```
BEFORE:
HEAD──►[10|→]──►[20|→]──►[30|NULL]

Step 1: temp = HEAD
Step 2: HEAD = HEAD.next    ← move head forward
Step 3: delete temp

AFTER:
HEAD──►[20|→]──►[30|NULL]
```

**Time: O(1)**

---

#### CASE 2: Delete from END ← O(n)

```
Must find SECOND-LAST node (traverse to it)
Then: secondLast.next = NULL

Time: O(n)
```

---

#### CASE 3: Delete a given node (by value/position) ← O(n)

```
Delete node with value 20:

BEFORE: [10]→[20]→[30]→[40]

Step 1: Traverse to node BEFORE 20, i.e., node [10]
Step 2: node[10].next = node[20].next  (skip 20)
Step 3: delete node[20]

AFTER: [10]→[30]→[40]
```

**Time: O(n)** ← Need to find the previous node

---

### 5.4 SEARCHING

```
Search for value 30:
[10]→[20]→[30]→[40]→NULL
  ↑    ↑    ↑
  no   no   FOUND! return position 3
```

**Time: O(n)** — linear search (no random access!)

---

## 📌 SECTION 6: COMPLEXITY SUMMARY TABLE

```
┌─────────────────────────┬──────────┬──────────┐
│       OPERATION         │  TIME    │  SPACE   │
├─────────────────────────┼──────────┼──────────┤
│ Insert at BEGINNING     │  O(1)    │  O(1)    │
│ Insert at END           │  O(n)    │  O(1)    │
│ Insert at Middle        │  O(n)    │  O(1)    │
│ Delete from BEGINNING   │  O(1)    │  O(1)    │
│ Delete from END         │  O(n)    │  O(1)    │
│ Delete middle node      │  O(n)    │  O(1)    │
│ Search                  │  O(n)    │  O(1)    │
│ Traversal               │  O(n)    │  O(1)    │
│ Access by index         │  O(n)    │  O(1)    │
└─────────────────────────┴──────────┴──────────┘
```

> ⚠️ **BPSC TRAP:** "Insert at beginning of Linked List is O(1)" — TRUE.
> But "Insert at end of Linked List is O(1)" — FALSE for SLL (it's O(n)).
> Exception: If you maintain a **TAIL pointer**, insert at end becomes O(1).

---

## 📌 SECTION 7: ADVANTAGES vs DISADVANTAGES

### ✅ ADVANTAGES (Why use Linked List over Array?)

```
┌────────────────────────────────────────────────┐
│  ADVANTAGE             │  EXPLANATION           │
│────────────────────────│────────────────────────│
│ Dynamic size           │ Grows/shrinks at runtime│
│ Easy insert at start   │ O(1) — no shifting      │
│ Easy deletion          │ No shifting elements    │
│ Memory efficient       │ Allocate only as needed │
└────────────────────────────────────────────────┘
```

### ❌ DISADVANTAGES (Why NOT use Linked List over Array?)

```
┌────────────────────────────────────────────────┐
│  DISADVANTAGE          │  EXPLANATION           │
│────────────────────────│────────────────────────│
│ NO random access       │ Cannot do list[5]       │
│ Extra memory per node  │ Pointer uses memory too │
│ Not cache-friendly     │ Non-contiguous storage  │
│ Reverse traversal hard │ Need to go HEAD→NULL    │
└────────────────────────────────────────────────┘
```

> 🔑 **PYQ GOLD:** "Which data structure does NOT support random access?"
> **Answer: Linked List** (Array DOES support random access in O(1))

---

## 📌 SECTION 8: LINKED LIST vs ARRAY — MASTER COMPARISON

```
┌──────────────────┬──────────────────┬──────────────────┐
│   PARAMETER      │     ARRAY        │  LINKED LIST     │
├──────────────────┼──────────────────┼──────────────────┤
│ Memory           │ Contiguous       │ Non-contiguous   │
│ Size             │ Fixed (static)   │ Dynamic          │
│ Access by index  │ O(1) ✓           │ O(n) ✗           │
│ Insert at start  │ O(n) — shifting  │ O(1) ✓           │
│ Insert at end    │ O(1) (if space)  │ O(n) SLL         │
│ Cache friendly   │ YES ✓            │ NO ✗             │
│ Extra memory     │ No overhead      │ Pointer overhead │
│ Binary Search    │ Possible O(logn) │ NOT possible     │
└──────────────────┴──────────────────┴──────────────────┘
```

> ⚠️ **BPSC TRAP:** "Binary search can be applied on linked list"
> **Answer: NO/FALSE** — Binary search requires random access (O(1) index).
> Linked list has only O(n) access, so binary search cannot be applied.

---

## 📌 SECTION 9: IMPORTANT PYQ FACTS — MEMORIZE THESE!

| # | Fact | Correct Answer |
|---|------|----------------|
| 1 | Linked list random access? | NOT possible (no index) |
| 2 | Insert at beginning SLL? | O(1) |
| 3 | Insert at end SLL (no tail ptr)? | O(n) |
| 4 | Main advantage over array? | Dynamic size + easy insert/delete |
| 5 | Main disadvantage vs array? | No random access |
| 6 | Head pointer in empty list? | NULL |
| 7 | Which sorting works on LL? | Merge Sort (preferred) |
| 8 | Binary search on LL? | NOT possible |
| 9 | How to detect cycle in LL? | Floyd's cycle detection algorithm |
| 10 | Memory per node in SLL? | data size + 1 pointer size |

---

## 📌 SECTION 10: SPECIAL LINKED LIST CONCEPTS (BPSC LEVEL)

### 10.1 Floyd's Cycle Detection Algorithm (Tortoise & Hare)

Used to detect if a linked list has a **cycle (loop)**:

```
Two pointers:
  SLOW pointer → moves 1 step at a time
  FAST pointer → moves 2 steps at a time

If Fast == Slow at any point → CYCLE EXISTS
If Fast reaches NULL → NO CYCLE
```

```
Example — Cycle:
[1]→[2]→[3]→[4]→[5]
              ↑        ↑
              └────────┘  (5 points back to 3)

Slow: 1→2→3→4→5→3→4...
Fast: 1→3→5→4→3→4...
They MEET → cycle detected!
```

### 10.2 Merge Sort on Linked List — O(n log n)

**Best sorting algorithm for Linked Lists** because:
- It requires no random access
- It works on sequential access (perfect for LL)
- Quick Sort is BAD for LL (needs random access for pivot)

### 10.3 Reverse a Singly Linked List

```
Original:  [1]→[2]→[3]→[4]→NULL
Reversed:  NULL←[1]←[2]←[3]←[4]

Algorithm (Iterative — 3 pointers):
  prev = NULL
  curr = HEAD
  while curr ≠ NULL:
      next = curr.next   ← save next
      curr.next = prev   ← reverse the link
      prev = curr        ← move prev forward
      curr = next        ← move curr forward
  HEAD = prev
```

### 10.4 Find Middle of Linked List

Use **Two Pointer** approach:
- Slow pointer: 1 step
- Fast pointer: 2 steps
- When fast reaches end → slow is at MIDDLE

**Time: O(n) in single pass!**

---

## 📌 SECTION 11: MEMORY REPRESENTATION (BPSC Diagram Type)

```
How [10]→[20]→[30] looks in memory:

Address  | Data | Next
---------|------|-----
  200    |  10  | 450     ← Node 1 (HEAD points here)
  300    |  XX  | XXX     ← some other data (not our list)
  450    |  20  | 800     ← Node 2
  600    |  XX  | XXX     ← some other data
  800    |  30  | NULL    ← Node 3 (last)

HEAD = 200
```

> This shows nodes are **NOT contiguous** — they are scattered in memory, linked only through pointers.

---

## 📌 SECTION 12: APPLICATIONS OF LINKED LIST

```
┌──────────────────────────────────────────────────┐
│           WHERE LINKED LISTS ARE USED            │
├──────────────────────────────────────────────────┤
│ 1. Implementation of STACK and QUEUE             │
│ 2. Implementation of Hash Tables (chaining)      │
│ 3. Dynamic memory allocation                     │
│ 4. Representing POLYNOMIALS (each term = node)   │
│ 5. Music playlist (circular LL)                  │
│ 6. Browser history (doubly LL)                   │
│ 7. Undo/Redo in editors                          │
│ 8. Adjacency list in Graphs                      │
└──────────────────────────────────────────────────┘
```

> ⚠️ **BPSC TRAP — Option D Watch:**
> "Which of the following use linked lists?"
> (A) Stack implementation  (B) Queue implementation
> (C) Hash table chaining   (D) More than one of the above ← **CORRECT**

---

# ═══════════════════════════════════════════════
# 📚 PART 2: GENERAL STUDIES
## INDIAN POLITY — FUNDAMENTAL RIGHTS (Articles 12–35)
### Most Tested Polity Topic in BPSC TRE
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: WHERE DO FUNDAMENTAL RIGHTS COME FROM?

```
PART III of the Indian Constitution
Articles 12 to 35
Inspired by: Bill of Rights of USA
Called: "Magna Carta of India"
```

> 🔑 **Fundamental Rights are JUSTICIABLE** = enforceable in courts.
> Unlike DPSP (non-justiciable), FRs can be challenged in court if violated.

---

## 📌 SECTION 2: THE 6 FUNDAMENTAL RIGHTS — COMPLETE CHART

```
┌────┬─────────────────────────────────┬─────────────────┐
│ #  │         RIGHT                   │   ARTICLES      │
├────┼─────────────────────────────────┼─────────────────┤
│ 1  │ Right to Equality               │  14 – 18        │
│ 2  │ Right to Freedom                │  19 – 22        │
│ 3  │ Right Against Exploitation      │  23 – 24        │
│ 4  │ Right to Freedom of Religion    │  25 – 28        │
│ 5  │ Cultural & Educational Rights   │  29 – 30        │
│ 6  │ Right to Constitutional Remedies│  32             │
└────┴─────────────────────────────────┴─────────────────┘

NOTE: Originally 7 FRs — Right to Property (Article 31) REMOVED
      by 44th Amendment, 1978 → now a LEGAL RIGHT (Article 300A)
```

---

## 📌 SECTION 3: RIGHT TO EQUALITY (Articles 14–18)

### Article 14 — Equality before Law
```
"The State shall not deny to any person equality before 
 the law or the equal protection of the laws"

Equality before Law    = British concept (negative concept)
                       = No one is above law
Equal Protection       = American concept (positive concept)
                       = Like should be treated alike
```

### Article 15 — Prohibition of Discrimination
```
No discrimination on grounds of:
R  – Race
R  – Religion  
C  – Caste
S  – Sex
P  – Place of birth

MNEMONIC: "RRCSP" or "Religion, Race, Caste, Sex, Place"

EXCEPTION: State CAN make special provisions for:
  → Women and children
  → Socially/educationally backward classes
  → SC/ST communities
```

### Article 16 — Equality of Opportunity in Public Employment
```
Equal opportunity in matters of public employment.
No discrimination in government jobs based on:
Religion, Race, Caste, Sex, Descent, Place of Birth/Residence

EXCEPTION: State CAN reserve posts for backward classes.
```

### Article 17 — Abolition of Untouchability
```
Untouchability ABOLISHED and its practice is FORBIDDEN
Practice of untouchability = PUNISHABLE OFFENCE

This is an ABSOLUTE RIGHT — no exceptions, 
cannot be suspended even during Emergency
```

> ⚠️ **PYQ TRAP:** Article 17 is ABSOLUTE — no exceptions, no suspension even during National Emergency.

### Article 18 — Abolition of Titles
```
State CANNOT confer any title (except military/academic)
Citizens CANNOT accept title from foreign State

BHARAT RATNA, PADMA AWARDS = NOT titles under Art 18
  (they are civilian honours, court verdict in 1996)
```

---

## 📌 SECTION 4: RIGHT TO FREEDOM (Articles 19–22)

### Article 19 — Six Freedoms (originally 7, one removed)

```
ARTICLE 19 FREEDOMS:
┌────────────────────────────────────────────────────┐
│ 19(1)(a) → Freedom of Speech and Expression        │
│ 19(1)(b) → Freedom of Peaceful Assembly            │
│ 19(1)(c) → Freedom to form Associations/Unions     │
│ 19(1)(d) → Freedom of Movement throughout India    │
│ 19(1)(e) → Freedom to Reside anywhere in India     │
│ 19(1)(g) → Freedom to practice any Profession/Trade│
└────────────────────────────────────────────────────┘

NOTE: 19(1)(f) = Freedom to acquire property → REMOVED 
      by 44th Amendment 1978

So NOW only 6 freedoms remain (not 7)
```

> ⚠️ **KEY PYQ FACT:** Article 19 freedoms are available ONLY to CITIZENS (not foreigners).
> Article 14 is available to ALL PERSONS (including foreigners).

### Article 20 — Protection in Respect of Conviction
```
THREE PROTECTIONS:
1. Ex-post-facto law protection:
   No person convicted for an act which was NOT an offence when done
   
2. Double Jeopardy protection:
   No person prosecuted TWICE for same offence
   ("Nemo debet bis vexari" — no one should be vexed twice)
   
3. Self-incrimination protection:
   No person compelled to be witness against himself
```

> ⚠️ **EXAM TIP:** Article 20 CANNOT be suspended even during National Emergency!

### Article 21 — Protection of Life and Personal Liberty
```
"No person shall be deprived of his life or personal liberty 
 except according to procedure established by law"

This is the MOST LITIGATED fundamental right.
Supreme Court has expanded it to include:
  → Right to live with dignity
  → Right to livelihood
  → Right to education (before Art 21A was added)
  → Right to privacy (Puttaswamy case 2017)
  → Right to a clean environment
  → Right to speedy trial
```

### Article 21A — Right to Education
```
Added by: 86th Constitutional Amendment, 2002
"Free and compulsory education to all children 
 aged 6–14 years"

Implemented by: Right to Education Act (RTE Act), 2009
```

> ⚠️ **BPSC PYQ TRAP:** Art 21A is RIGHT TO EDUCATION for 6–14 age group.
> It is NOT in the original constitution — added by 86th Amendment.

### Article 22 — Protection Against Arrest and Detention
```
Rights of an arrested person:
1. Right to be informed of grounds of arrest
2. Right to consult and be defended by a lawyer
3. Produced before magistrate within 24 hours of arrest

EXCEPTIONS (Preventive Detention):
→ Enemy alien
→ Person arrested under Preventive Detention Law
   (can be detained for 3 months without magistrate approval)
```

---

## 📌 SECTION 5: RIGHT AGAINST EXPLOITATION (Articles 23–24)

### Article 23 — Prohibition of Traffic in Human Beings
```
PROHIBITS:
→ Traffic in human beings (human trafficking)
→ Begar (forced labour without payment)
→ Other forms of forced labour

EXCEPTION: State can impose compulsory service for 
           public purpose (without discrimination)
```

### Article 24 — Prohibition of Child Labour
```
"No child below the age of 14 years shall be employed 
 to work in any factory, mine, or other hazardous employment"

Age: 14 years
Applicable: Factories, Mines, Hazardous work
```

> ⚠️ **BPSC TRAP:** Article 24 says 14 years for hazardous employment.
> Child Labour Act 2016 amended this to 14 years generally,
> and 18 years for hazardous occupations.

---

## 📌 SECTION 6: RIGHT TO FREEDOM OF RELIGION (Articles 25–28)

### Article 25 — Freedom of Conscience and Religion
```
Every person has the right to:
→ Freely profess, practice, and propagate religion

SUBJECT TO: Public order, morality, health, other FRs

EXCEPTIONS (State CAN regulate):
→ Economic, financial, political secular activities 
   associated with religion
→ Social reforms (e.g., abolish untouchability)
```

### Article 26 — Freedom to Manage Religious Affairs
```
Every RELIGIOUS DENOMINATION has right to:
→ Establish and maintain institutions
→ Manage its own affairs in religious matters
→ Own and acquire property
→ Administer property as per law
```

### Article 27 — Freedom from Taxation for Religion
```
No person shall be compelled to pay taxes for 
promotion of any particular religion

State CANNOT use tax money to promote a religion
```

### Article 28 — Freedom from Religious Instruction
```
NO religious instruction in fully state-funded institutions

Institutions RECEIVING state aid → can give religious 
instruction but no student can be compelled to attend
```

---

## 📌 SECTION 7: CULTURAL AND EDUCATIONAL RIGHTS (Articles 29–30)

### Article 29 — Protection of Interests of Minorities
```
Any section of citizens having:
  → distinct language, script, culture
  → have right to CONSERVE it

NO citizen shall be DENIED ADMISSION to 
state-aided institutions on grounds of:
  → Religion, Race, Caste, Language
```

### Article 30 — Right of Minorities to Establish Educational Institutions
```
All minorities (religious OR linguistic) have right to:
  → Establish educational institutions
  → Administer educational institutions

State cannot discriminate in granting aid to 
minority-managed institutions
```

> ⚠️ **KEY DIFFERENCE:**
> Art 29 = available to ALL citizens (not just minorities)
> Art 30 = available to MINORITIES ONLY (religious or linguistic)

---

## 📌 SECTION 8: RIGHT TO CONSTITUTIONAL REMEDIES (Article 32)

```
Called the "HEART AND SOUL of the Constitution" 
by Dr. B.R. Ambedkar

Article 32 = Right to approach SUPREME COURT 
             for enforcement of FRs

Article 226 = Right to approach HIGH COURT 
              for enforcement of ANY right (wider scope)
```

### The 5 Writs (BPSC Most Important!)

```
┌─────────────────┬────────────────────────────────────────┐
│     WRIT        │           MEANING & USE                │
├─────────────────┼────────────────────────────────────────┤
│ HABEAS CORPUS   │ "Have the body"                        │
│                 │ To produce detained person in court    │
│                 │ Against illegal detention              │
│                 │ Available to: ALL persons (not just    │
│                 │ citizens)                              │
├─────────────────┼────────────────────────────────────────┤
│ MANDAMUS        │ "We command"                           │
│                 │ Directs public official to perform     │
│                 │ their DUTY                             │
│                 │ Cannot be issued against: President,  │
│                 │ Governors, Private persons             │
├─────────────────┼────────────────────────────────────────┤
│ PROHIBITION     │ "Stop it"                              │
│                 │ Issued by superior court to inferior   │
│                 │ court to STOP proceedings              │
│                 │ (Preventive writ)                      │
├─────────────────┼────────────────────────────────────────┤
│ CERTIORARI      │ "To be certified"                      │
│                 │ Issued to quash order of inferior court│
│                 │ (Corrective writ — AFTER decision)     │
├─────────────────┼────────────────────────────────────────┤
│ QUO WARRANTO   │ "By what authority"                    │
│                 │ Challenges a person's right to hold   │
│                 │ a public office                        │
│                 │ Only for PUBLIC offices (not private)  │
└─────────────────┴────────────────────────────────────────┘
```

> 🔑 **MNEMONIC FOR WRITS:** **"H M P C Q"**
> **H**abeas Corpus | **M**andamus | **P**rohibition | **C**ertiorari | **Q**uo Warranto

---

## 📌 SECTION 9: ARTICLE 13 — LAWS INCONSISTENT WITH FRs

```
Article 13 = GUARDIAN of Fundamental Rights

"Any law inconsistent with or in derogation of FRs 
 shall be VOID to the extent of inconsistency"

This gives courts power of JUDICIAL REVIEW
```

---

## 📌 SECTION 10: FRs SUSPENDED DURING EMERGENCY

```
NATIONAL EMERGENCY (Article 352):
  → Article 19 suspended (6 freedoms)
  → Art 20, 21 CANNOT be suspended (ABSOLUTE)

PRESIDENT'S RULE (Article 356):
  → FRs NOT automatically suspended

FINANCIAL EMERGENCY (Article 360):
  → FRs NOT suspended
```

> ⚠️ **BPSC GOLD:** Articles 20 and 21 CANNOT be suspended even during National Emergency.
> This is tested EVERY year in GS section.

---

## 📌 SECTION 11: IMPORTANT ARTICLES QUICK REFERENCE

| Article | Subject |
|---------|---------|
| 12 | Definition of "State" |
| 13 | Laws inconsistent with FRs — void |
| 14 | Equality before law |
| 15 | Prohibition of discrimination |
| 16 | Equality of opportunity in employment |
| 17 | Abolition of untouchability |
| 18 | Abolition of titles |
| 19 | Six freedoms |
| 20 | Protection in conviction (ex-post-facto, double jeopardy, self-incrimination) |
| 21 | Right to life and personal liberty |
| 21A | Right to Education (6–14 years) — 86th Amendment |
| 22 | Protection against arrest (24-hour rule) |
| 23 | Prohibition of traffic in humans and forced labour |
| 24 | Prohibition of child labour (under 14 years) |
| 25 | Freedom of religion |
| 26 | Manage religious affairs |
| 27 | No tax for religion |
| 28 | No religious instruction in state schools |
| 29 | Protection of minority interests |
| 30 | Minorities' right to educational institutions |
| 32 | Right to Constitutional Remedies (Heart & Soul) |

---

## 📌 SECTION 12: BIHAR-SPECIFIC POLITY FACTS

```
BIHAR SPECIFIC:
→ Bihar has UNICAMERAL legislature (Vidhan Sabha only)
  WAIT — Actually Bihar HAS BICAMERAL:
  • Vidhan Sabha (243 seats)
  • Vidhan Parishad (75 seats) ← Upper House (Bihar is one of 6 states with it)

States WITH Vidhan Parishad (6 states):
  UP, Maharashtra, Karnataka, Bihar, Telangana, Andhra Pradesh
  MNEMONIC: "UP MaKaBATA"

Bihar Governor: Appointed by President
Chief Minister: Nitish Kumar (as of last data)

Bihar Panchayati Raj:
→ 3-tier: Gram Panchayat → Panchayat Samiti → Zila Parishad
→ Under 73rd Amendment (1992)
```

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 1 (CS)
## 25 Questions on Singly Linked List
### ⚠️ SOLVE ALL 25 FIRST. ANSWERS AT END OF FILE.
# ═══════════════════════════════════════════════

---

**Q1.** What is the time complexity of inserting a new node at the BEGINNING of a singly linked list?
- (A) O(log n)
- (B) O(n)
- (C) O(n²)
- (D) More than one of the above
- (E) None of the above

---

**Q2.** Which of the following is the MAIN disadvantage of a linked list over an array?
- (A) Dynamic memory allocation
- (B) No random access (cannot access by index)
- (C) Easy insertion and deletion
- (D) More than one of the above
- (E) None of the above

---

**Q3.** In a singly linked list, the last node contains:
- (A) Address of the first node
- (B) Address of the previous node
- (C) NULL pointer
- (D) More than one of the above
- (E) None of the above

---

**Q4.** The time complexity to search for an element in a singly linked list is:
- (A) O(1)
- (B) O(log n)
- (C) O(n)
- (D) More than one of the above
- (E) None of the above

---

**Q5.** A singly linked list node in C++ has the correct definition as:
- (A) `struct Node { int data; Node* prev; Node* next; };`
- (B) `struct Node { int data; Node* next; };`
- (C) `struct Node { int data; int next; };`
- (D) More than one of the above
- (E) None of the above

---

**Q6.** Which sorting algorithm is BEST suited for sorting a singly linked list?
- (A) Quick Sort
- (B) Bubble Sort
- (C) Merge Sort
- (D) More than one of the above
- (E) None of the above

---

**Q7.** What is the space complexity of a singly linked list with n nodes compared to an array of n elements?
- (A) Less than array
- (B) Same as array
- (C) More than array (due to pointer overhead)
- (D) More than one of the above
- (E) None of the above

---

**Q8.** Floyd's cycle detection algorithm uses:
- (A) One pointer moving one step at a time
- (B) Two pointers — one fast (2 steps), one slow (1 step)
- (C) Three pointers — prev, curr, next
- (D) More than one of the above
- (E) None of the above

---

**Q9.** An empty singly linked list is represented by:
- (A) HEAD pointing to a dummy node
- (B) HEAD = -1
- (C) HEAD = NULL
- (D) More than one of the above
- (E) None of the above

---

**Q10.** Which of the following operations on a singly linked list has O(1) time complexity?
- (A) Access the 5th element
- (B) Insert at the beginning
- (C) Delete from the end
- (D) More than one of the above
- (E) None of the above

---

**Q11.** Binary search CANNOT be applied on a singly linked list because:
- (A) It is not a sorted data structure
- (B) It does not support random access
- (C) It requires more memory
- (D) More than one of the above
- (E) None of the above

---

**Q12.** To find the MIDDLE element of a singly linked list efficiently in O(n) single pass, we use:
- (A) Stack and queue
- (B) Two pointers — fast and slow
- (C) Recursive function
- (D) More than one of the above
- (E) None of the above

---

**Q13.** In a singly linked list, deletion of a node requires:
- (A) Access to the node to be deleted only
- (B) Access to the previous node of the node to be deleted
- (C) Rebuilding the entire list
- (D) More than one of the above
- (E) None of the above

---

**Q14.** Which of the following correctly identifies the ADVANTAGE of a linked list over an array?
- (A) Better cache performance
- (B) Support for random access
- (C) Dynamic memory allocation without wasting space
- (D) More than one of the above
- (E) None of the above

---

**Q15.** In memory, the nodes of a linked list are stored:
- (A) In contiguous memory locations
- (B) In non-contiguous memory locations
- (C) In stack memory only
- (D) More than one of the above
- (E) None of the above

---

**Q16.** Which data structure is typically used to IMPLEMENT a stack?
- (A) Array only
- (B) Linked List only
- (C) Both array and linked list can be used
- (D) More than one of the above
- (E) None of the above

---

**Q17.** Given a singly linked list: 1→2→3→4→5. After reversing, the list becomes:
- (A) 5→4→3→2→1
- (B) 1→2→3→4→5 (unchanged)
- (C) 5→4→3→2→NULL
- (D) More than one of the above
- (E) None of the above

---

**Q18.** What is the time complexity of DELETING a node from the BEGINNING of a singly linked list?
- (A) O(n)
- (B) O(log n)
- (C) O(1)
- (D) More than one of the above
- (E) None of the above

---

**Q19.** A polynomial can be represented using a linked list where each node stores:
- (A) Only the coefficient
- (B) Only the exponent
- (C) Both coefficient and exponent
- (D) More than one of the above
- (E) None of the above

---

**Q20.** Which of the following is TRUE about a singly linked list?
- (A) It supports bidirectional traversal
- (B) It requires extra memory for the pointer field
- (C) It can perform binary search in O(log n)
- (D) More than one of the above
- (E) None of the above

---

**Q21.** If a singly linked list has a TAIL pointer maintained, what is the time complexity of inserting at the END?
- (A) O(n)
- (B) O(log n)
- (C) O(1)
- (D) More than one of the above
- (E) None of the above

---

**Q22.** To detect a cycle in a linked list, Floyd's algorithm works because:
- (A) If a cycle exists, the fast pointer will eventually catch up to the slow pointer
- (B) If no cycle, the fast pointer reaches NULL
- (C) Both A and B
- (D) More than one of the above
- (E) None of the above

---

**Q23.** Which of the following is an APPLICATION of a linked list?
- (A) Implementing adjacency list representation of graphs
- (B) Dynamic memory allocation
- (C) Polynomial representation
- (D) More than one of the above
- (E) None of the above

---

**Q24.** In a linked list containing n nodes, what is the time complexity for accessing the LAST node?
- (A) O(1)
- (B) O(log n)
- (C) O(n)
- (D) More than one of the above
- (E) None of the above

---

**Q25.** What is the CORRECT order of steps to INSERT a node after a given node X in a singly linked list?
- (A) newNode.next = X.next; X.next = newNode
- (B) X.next = newNode; newNode.next = X.next
- (C) newNode.next = X; X.next = newNode
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 2 (GS)
## 25 Questions on Fundamental Rights (Articles 12–35)
### ⚠️ SOLVE ALL 25 FIRST. ANSWERS AT END OF FILE.
# ═══════════════════════════════════════════════

---

**Q26.** Fundamental Rights in India are contained in which PART of the Constitution?
- (A) Part II
- (B) Part III
- (C) Part IV
- (D) More than one of the above
- (E) None of the above

---

**Q27.** Dr. B.R. Ambedkar called which article the "Heart and Soul of the Constitution"?
- (A) Article 14
- (B) Article 21
- (C) Article 32
- (D) More than one of the above
- (E) None of the above

---

**Q28.** The Right to Property was removed from Fundamental Rights by which Constitutional Amendment?
- (A) 42nd Amendment, 1976
- (B) 44th Amendment, 1978
- (C) 86th Amendment, 2002
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Article 17 of the Constitution deals with:
- (A) Right to equality before law
- (B) Abolition of untouchability
- (C) Abolition of titles
- (D) More than one of the above
- (E) None of the above

---

**Q30.** Article 19 of the Constitution provides freedom of speech to:
- (A) All persons including foreigners
- (B) Only citizens of India
- (C) Only minority communities
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Under Article 21A (added by 86th Amendment), free and compulsory education is provided to children of age:
- (A) 0–6 years
- (B) 6–14 years
- (C) 14–18 years
- (D) More than one of the above
- (E) None of the above

---

**Q32.** The writ of HABEAS CORPUS can be issued against:
- (A) Only Central Government
- (B) Only private individuals
- (C) Both public authorities and private individuals in case of illegal detention
- (D) More than one of the above
- (E) None of the above

---

**Q33.** Which of the following CANNOT be suspended even during a National Emergency?
- (A) Article 14
- (B) Article 19
- (C) Article 20 and Article 21
- (D) More than one of the above
- (E) None of the above

---

**Q34.** The writ of MANDAMUS CANNOT be issued against:
- (A) Government department
- (B) Public authority
- (C) President of India
- (D) More than one of the above
- (E) None of the above

---

**Q35.** Article 24 prohibits employment of children below which age in hazardous occupations?
- (A) 12 years
- (B) 14 years
- (C) 16 years
- (D) More than one of the above
- (E) None of the above

---

**Q36.** Which writ is issued to challenge a person's right to hold a PUBLIC OFFICE?
- (A) Habeas Corpus
- (B) Mandamus
- (C) Quo Warranto
- (D) More than one of the above
- (E) None of the above

---

**Q37.** Article 15 prohibits discrimination on grounds of:
- (A) Religion and Race
- (B) Caste and Sex
- (C) Place of Birth
- (D) More than one of the above
- (E) None of the above

---

**Q38.** "No person shall be compelled to be a witness against himself" is guaranteed under:
- (A) Article 19
- (B) Article 20(3) — Right against self-incrimination
- (C) Article 21
- (D) More than one of the above
- (E) None of the above

---

**Q39.** Which Article states that the State shall not deny any person EQUALITY BEFORE LAW?
- (A) Article 13
- (B) Article 14
- (C) Article 15
- (D) More than one of the above
- (E) None of the above

---

**Q40.** Under Article 22, an arrested person must be produced before a magistrate within:
- (A) 12 hours
- (B) 24 hours (excluding travel time)
- (C) 48 hours
- (D) More than one of the above
- (E) None of the above

---

**Q41.** The RIGHT TO LIFE (Article 21) was interpreted to include right to PRIVACY in which landmark case?
- (A) Kesavananda Bharati Case (1973)
- (B) K.S. Puttaswamy vs Union of India (2017)
- (C) Maneka Gandhi Case (1978)
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Article 30 gives the right to establish and administer educational institutions to:
- (A) All citizens of India
- (B) Only religious minorities
- (C) Religious AND linguistic minorities
- (D) More than one of the above
- (E) None of the above

---

**Q43.** Bihar has how many seats in the STATE LEGISLATIVE ASSEMBLY (Vidhan Sabha)?
- (A) 200
- (B) 243
- (C) 294
- (D) More than one of the above
- (E) None of the above

---

**Q44.** Which writ literally means "TO BE CERTIFIED" and is used to quash the order of a lower court?
- (A) Prohibition
- (B) Certiorari
- (C) Mandamus
- (D) More than one of the above
- (E) None of the above

---

**Q45.** How many states in India have a LEGISLATIVE COUNCIL (Vidhan Parishad)?
- (A) 4
- (B) 6
- (C) 8
- (D) More than one of the above
- (E) None of the above

---

**Q46.** Article 29 protects:
- (A) Minority groups only
- (B) Any section of citizens with distinct language, script, or culture
- (C) Only linguistic minorities
- (D) More than one of the above
- (E) None of the above

---

**Q47.** Under the DOCTRINE OF DOUBLE JEOPARDY (Article 20), a person cannot be:
- (A) Arrested without warrant
- (B) Prosecuted and punished for the SAME offence more than once
- (C) Forced to testify against himself
- (D) More than one of the above
- (E) None of the above

---

**Q48.** Article 23 deals with:
- (A) Prohibition of child labour
- (B) Prohibition of traffic in human beings and forced labour
- (C) Freedom of religion
- (D) More than one of the above
- (E) None of the above

---

**Q49.** The writ of PROHIBITION is different from CERTIORARI because:
- (A) Prohibition is issued before judgment; Certiorari after judgment
- (B) Prohibition is issued after judgment; Certiorari before judgment
- (C) Both are issued at the same time
- (D) More than one of the above
- (E) None of the above

---

**Q50.** Under Article 32, which court has the power to issue writs for enforcement of Fundamental Rights?
- (A) High Court
- (B) Supreme Court
- (C) District Court
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY WITH DETAILED EXPLANATIONS
## CS Answers (Q1–Q25) | GS Answers (Q26–Q50)
# ═══════════════════════════════════════════════

---

## 🖥️ CS ANSWERS (Q1–Q25)

---

**A1. → (E) None of the above**
**Correct answer: O(1)**
Insert at beginning = Just create new node, point it to current HEAD, update HEAD. No traversal needed. Time = O(1). None of the options A/B/C said O(1), so answer is (E).

---

**A2. → (B) No random access**
Linked list does NOT support index-based access. You cannot do `list[5]` — you must traverse from HEAD. This is the MAIN disadvantage vs arrays.
- Option A (dynamic memory) = ADVANTAGE, not disadvantage
- Option C (easy insertion/deletion) = ADVANTAGE, not disadvantage

---

**A3. → (C) NULL pointer**
The last node of a singly linked list always has `next = NULL`, marking the end of the list. Option A would make it circular (not singly). Option B would make it doubly linked.

---

**A4. → (C) O(n)**
Search in SLL = Linear Search. Must traverse from HEAD checking each node. Worst case = element at last position = n comparisons. Hence O(n).

---

**A5. → (B) `struct Node { int data; Node* next; };`**
Singly Linked List node has only ONE pointer (next). Option A has two pointers (doubly linked list). Option C uses `int next` (wrong — must be pointer type `Node*`).

---

**A6. → (C) Merge Sort**
Merge Sort works on sequential access — perfect for linked lists. Quick Sort requires random access for pivot selection — BAD for LL. Merge Sort on LL = O(n log n) without extra space.

---

**A7. → (C) More than array (due to pointer overhead)**
Each node in a linked list stores: data + pointer (extra 4 or 8 bytes). An array stores only data. So linked list uses MORE memory per element.

---

**A8. → (B) Two pointers — one fast (2 steps), one slow (1 step)**
Floyd's Tortoise and Hare: Slow moves 1 step, Fast moves 2 steps. If cycle exists, Fast catches up with Slow. If no cycle, Fast reaches NULL.

---

**A9. → (C) HEAD = NULL**
An empty linked list has HEAD = NULL. NULL means the pointer points to nothing — no nodes exist.

---

**A10. → (B) Insert at the beginning**
- Access 5th element → O(n) (traverse)
- Insert at beginning → O(1) ✓
- Delete from end → O(n) (traverse to second-last)

---

**A11. → (B) It does not support random access**
Binary search requires accessing middle element directly (index-based). Linked list = O(n) to reach middle. No random access = binary search not applicable.

> Note: Option A says "not sorted" — but even if sorted, binary search still won't work because of no random access. The PRIMARY reason is (B).

---

**A12. → (B) Two pointers — fast and slow**
Slow moves 1 step, Fast moves 2 steps. When Fast reaches end (or NULL), Slow is at the middle. Single O(n) pass — efficient!

---

**A13. → (B) Access to the previous node**
To delete node X: you must set `prev.next = X.next`. You need the PREVIOUS node's reference. In SLL (singly), you cannot go backward, so you need to traverse from HEAD to find the previous node.

---

**A14. → (C) Dynamic memory allocation without wasting space**
- Option A (cache performance) = DISADVANTAGE of LL (arrays are cache-friendly)
- Option B (random access) = ADVANTAGE of arrays, NOT LL
- Option C = TRUE advantage of LL ✓

---

**A15. → (B) Non-contiguous memory locations**
Linked list nodes are scattered in memory. They are connected via pointers, NOT by being adjacent in memory (unlike arrays).

---

**A16. → (C) Both array and linked list can be used**
Stack can be implemented using:
1. Array: top pointer moves up/down
2. Linked list: HEAD acts as top
Both are valid implementations → Option D might seem right, but (C) already captures "both" — answer is (C).

---

**A17. → (A) 5→4→3→2→1**
Reversing 1→2→3→4→5 gives 5→4→3→2→1. The last node (5) becomes HEAD, and the original HEAD (1) becomes tail pointing to NULL.

---

**A18. → (C) O(1)**
Delete from beginning: Save HEAD, move HEAD to HEAD.next, delete saved node. No traversal needed → O(1).

---

**A19. → (C) Both coefficient and exponent**
A polynomial term like 3x⁴ needs BOTH:
- coefficient = 3
- exponent = 4
Each node stores both. Multiple nodes → complete polynomial.

---

**A20. → (B) It requires extra memory for the pointer field**
- Option A: SLL only traverses FORWARD (no bidirectional) → FALSE
- Option B: TRUE — each node has extra pointer field
- Option C: Cannot do binary search → FALSE
Answer = (B)

---

**A21. → (C) O(1)**
If a TAIL pointer is maintained separately (always points to last node), inserting at end just requires: `tail.next = newNode; tail = newNode` → O(1). No traversal needed!

---

**A22. → (D) More than one of the above**
Both A and B are correct:
- If cycle: fast eventually meets slow (like running on circular track)
- If no cycle: fast reaches NULL
Both statements describe why Floyd's algorithm works → (D).

---

**A23. → (D) More than one of the above**
All three are applications of linked list:
- Adjacency list for graphs ✓
- Dynamic memory allocation ✓
- Polynomial representation ✓
→ Answer = (D)

---

**A24. → (C) O(n)**
To access LAST node in SLL: must traverse from HEAD node by node until NULL. In worst case (accessing last), traversal = n steps → O(n).

---

**A25. → (A) newNode.next = X.next; X.next = newNode**
CORRECT ORDER:
1. First: `newNode.next = X.next` (save link to next node)
2. Then: `X.next = newNode` (connect X to new node)

Option B is WRONG — if you do `X.next = newNode` first, you LOSE the reference to the original next node!

---

## 📚 GS ANSWERS (Q26–Q50)

---

**A26. → (B) Part III**
Fundamental Rights = Part III, Articles 12–35.
- Part II = Citizenship
- Part IV = DPSP (Directive Principles)

---

**A27. → (C) Article 32**
Dr. Ambedkar called Article 32 the "Heart and Soul of the Constitution" — it gives the right to approach the Supreme Court to enforce Fundamental Rights.

---

**A28. → (B) 44th Amendment, 1978**
Right to Property (Article 31) was removed from Part III (Fundamental Rights) by the 44th Amendment, 1978 under Janata Party government. It became a legal/constitutional right under Article 300A.

---

**A29. → (B) Abolition of untouchability**
- Article 14 = Equality before law
- Article 17 = Abolition of untouchability ✓
- Article 18 = Abolition of titles

---

**A30. → (B) Only citizens of India**
Article 19 freedoms (including speech) are available ONLY to CITIZENS. Foreigners do NOT get Article 19 rights. However, Articles 14 and 21 apply to ALL persons including foreigners.

---

**A31. → (B) 6–14 years**
Article 21A (86th Amendment, 2002): Free and compulsory education for all children aged **6 to 14 years**. Implemented through RTE Act, 2009.

---

**A32. → (C) Both public authorities and private individuals**
Habeas Corpus is unique — it can be issued against ANY person (public or private) detaining someone illegally. It is available to protect personal liberty broadly.

---

**A33. → (C) Article 20 and Article 21**
During National Emergency (Article 352):
- Article 19 (six freedoms) CAN be suspended
- Articles 20 and 21 CANNOT be suspended — absolute protection
This was reinforced by the 44th Amendment.

---

**A34. → (C) President of India**
Mandamus ("we command") directs public officials to do their duty.
CANNOT be issued against:
- President of India
- Governors of States
- Private individuals or organizations
- Inferior court for judicial decisions

---

**A35. → (B) 14 years**
Article 24: "No child below the age of **14 years** shall be employed to work in any factory or mine or engaged in any other hazardous employment."

---

**A36. → (C) Quo Warranto**
Quo Warranto = "By what authority?" Used to challenge a person's legal right to hold a public office. Example: If someone is holding a government post without proper qualification/authority.

---

**A37. → (D) More than one of the above**
Article 15 prohibits discrimination on ALL of these grounds:
- Religion ✓ (A)
- Race ✓ (A)
- Caste ✓ (B)
- Sex ✓ (B)
- Place of Birth ✓ (C)
All three options A, B, C are correct → Answer = (D)

---

**A38. → (B) Article 20(3)**
Self-incrimination protection = Article 20(3): "No person accused of any offence shall be compelled to be a witness against himself."
This is one of the three protections under Article 20.

---

**A39. → (B) Article 14**
Article 14: "The State shall not deny to any person equality before the law or the equal protection of the laws within the territory of India."

---

**A40. → (B) 24 hours**
Article 22: An arrested person must be produced before the nearest magistrate within **24 hours** of arrest (excluding travel time). This is a fundamental protection against illegal detention.

---

**A41. → (B) K.S. Puttaswamy vs Union of India (2017)**
The 9-judge bench in Puttaswamy case declared RIGHT TO PRIVACY as a fundamental right under Article 21 in 2017.
- Maneka Gandhi case (1978) expanded Art 21 to "procedure must be fair, just and reasonable"

---

**A42. → (C) Religious AND linguistic minorities**
Article 30: Right of minorities to establish and administer educational institutions applies to BOTH:
- Religious minorities (e.g., Christians, Muslims)
- Linguistic minorities (e.g., Tamil speakers in Maharashtra)
Note: Article 29 is broader — applies to ANY section of citizens.

---

**A43. → (B) 243**
Bihar Vidhan Sabha = **243 seats**
Bihar Vidhan Parishad = 75 seats
Bihar is one of only 6 states with a bicameral legislature.

---

**A44. → (B) Certiorari**
Certiorari = "To be certified" = issued by superior court to QUASH (cancel) the order/decision already made by a lower court or tribunal. It is a corrective writ (issued AFTER the decision).

---

**A45. → (B) 6**
States with Legislative Council (Vidhan Parishad):
1. Uttar Pradesh
2. Maharashtra
3. Karnataka
4. Bihar
5. Telangana
6. Andhra Pradesh
MNEMONIC: **UP MaKaBATA**

---

**A46. → (B) Any section of citizens with distinct language, script, or culture**
Article 29 is NOT limited to minorities. It protects ANY SECTION of citizens (majority or minority) that has a distinct language, script, or culture. This is broader than Art 30.

---

**A47. → (B) Prosecuted and punished for the same offence more than once**
Article 20(2) = Double Jeopardy = "No person shall be prosecuted and punished for the same offence more than once."
- Option A = covered by Article 22
- Option C = covered by Article 20(3) — self-incrimination

---

**A48. → (B) Prohibition of traffic in human beings and forced labour**
Article 23 = Prohibits:
1. Traffic in human beings (begar, slavery, human trafficking)
2. Forced labour
Article 24 = Child labour prohibition

---

**A49. → (A) Prohibition issued BEFORE judgment; Certiorari issued AFTER judgment**
- PROHIBITION = PREVENTIVE — stops inferior court from PROCEEDING with a case (before decision)
- CERTIORARI = CORRECTIVE — quashes an order ALREADY MADE by inferior court (after decision)

---

**A50. → (B) Supreme Court**
Article 32 = Supreme Court issues writs for enforcement of FRs.
Article 226 = High Courts can ALSO issue writs, but for enforcement of ANY legal right (not just FRs).
Note: High Court's jurisdiction (Art 226) is WIDER than Supreme Court's (Art 32).

---

# ═══════════════════════════════════════════════
# 📊 DAY 22 REVISION SUMMARY
## Quick-Recall Flash Points
# ═══════════════════════════════════════════════

---

## 🖥️ CS — LINKED LIST: 10 MUST-REMEMBER FACTS

```
1. Insert at BEGINNING of SLL → O(1)
2. Insert at END of SLL (no tail ptr) → O(n)
3. Search in SLL → O(n)
4. Access by index (random access) → NOT POSSIBLE in LL
5. Binary search on LL → NOT POSSIBLE
6. Best sort for LL → MERGE SORT
7. Empty LL → HEAD = NULL
8. Floyd's algorithm → uses slow (1 step) + fast (2 step) pointers
9. Nodes in LL → stored at NON-CONTIGUOUS memory
10. SLL node → data + ONE next pointer
```

## 📚 GS — FUNDAMENTAL RIGHTS: 10 MUST-REMEMBER FACTS

```
1. FRs → Part III, Articles 12–35
2. "Heart & Soul" of Constitution → Article 32 (Dr. Ambedkar)
3. FRs inspired by → USA Bill of Rights
4. Right to Property removed by → 44th Amendment 1978
5. Article 21A (Education 6-14 yrs) added by → 86th Amendment 2002
6. Articles 20 & 21 → Cannot be suspended even during Emergency
7. Article 19 → Only for CITIZENS (not foreigners)
8. Article 14 → For ALL PERSONS (including foreigners)
9. Writs: HMPCQ = Habeas Corpus, Mandamus, Prohibition, Certiorari, Quo Warranto
10. Bihar Vidhan Sabha → 243 seats | Vidhan Parishad → 75 seats
```

---

## ⚡ OPTION D TRAPS TO WATCH FOR (BPSC Specialty)

```
TOPIC                          | When Option D applies
-------------------------------|--------------------------------
Applications of LL             | Multiple correct (graphs + hash + poly)
Advantages of LL over Array    | Check carefully — only dynamic size + easy insert
Writs issued by Supreme Court  | Only for FR enforcement (Art 32)
Article 15 grounds             | ALL 5 grounds = D is correct
States with Vidhan Parishad    | List exactly 6 states
```

---

## 🎯 TONIGHT'S REVISION TASK (30 min)

Write these from memory (close this file):
1. Draw a 5-node SLL diagram with data 10→20→30→40→50
2. Write the 5 writs with their meanings
3. Write Articles 14, 17, 19, 20, 21, 21A, 24, 32 with one-line descriptions
4. State: O complexity for insert-beginning, insert-end, search in SLL

---

*Day 22 Complete | Next: Day 23 — Doubly Linked List + DPSPs*
*Target Score Today: 22/25 CS + 22/25 GS = 44/50 minimum*
