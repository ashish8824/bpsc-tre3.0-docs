# 📅 DAY 23 — BPSC TRE 4.0 TOPPER GUIDE
## CS: Doubly Linked List & Circular Linked List | GS: Directive Principles of State Policy (DPSP)
### Phase 1 | Week 4 | Target: TOP RANK

---

> **🎯 Today's Targets:**
> - CS: Master Doubly LL + Circular LL — structures, operations, comparisons, PYQ traps
> - GS: Master DPSP (Articles 36–51) + Fundamental Duties (Article 51A)
> - Solve: 25 CS + 25 GS PYQ-style questions (answers ONLY at end)
> - Bonus: FR vs DPSP conflict — landmark cases every topper knows

---

# ═══════════════════════════════════════════════
# 🖥️ PART 1: COMPUTER SCIENCE
## DOUBLY LINKED LIST & CIRCULAR LINKED LIST
## — COMPLETE TOPPER GUIDE
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: QUICK RECAP — WHERE WE ARE

Yesterday (Day 22) you learned **Singly Linked List (SLL)**:
- One pointer per node (`next` only)
- Forward traversal only
- Insert at beginning = O(1); Insert at end = O(n)
- No random access

Today we go DEEPER with two more types:

```
LINKED LIST FAMILY TREE:
                    LINKED LIST
                        │
          ┌─────────────┼──────────────┐
          │             │              │
    SINGLY LL      DOUBLY LL     CIRCULAR LL
    (1 pointer)   (2 pointers)  (last → first)
     Day 22          TODAY           TODAY
                        │
                   Can also be
                   CIRCULAR DLL
```

---

## 📌 SECTION 2: DOUBLY LINKED LIST (DLL) — STRUCTURE

A **Doubly Linked List** node has **THREE parts**:

```
+----------+--------+----------+
|   PREV   |  DATA  |   NEXT   |
| (pointer)|        | (pointer)|
+----------+--------+----------+
     ^                   ^
  points to           points to
  previous node       next node
```

### Full DLL Visualization:

```
NULL ←─[PREV|10|NEXT]─⇄─[PREV|20|NEXT]─⇄─[PREV|30|NEXT]─⇄─[PREV|40|NEXT]→ NULL
        ↑                                                           ↑
       HEAD                                                        TAIL
```

- `HEAD.prev = NULL` (first node has no previous)
- `TAIL.next = NULL` (last node has no next)
- Each node links **both forward AND backward**

---

### C++ Node Structure for DLL:

```cpp
struct Node {
    int data;
    Node* prev;    // pointer to previous node
    Node* next;    // pointer to next node
};
```

### Java Node Structure for DLL:

```java
class Node {
    int data;
    Node prev;
    Node next;
    Node(int d) {
        data = d;
        prev = null;
        next = null;
    }
}
```

---

## 📌 SECTION 3: DLL OPERATIONS — STEP BY STEP

### 3.1 INSERTION AT BEGINNING — O(1)

```
BEFORE:
NULL ←[10]⇄[20]⇄[30]→ NULL
       HEAD

Insert 5 at beginning:

Step 1: Create new node [5]
Step 2: newNode.next = HEAD          → newNode → [10]
Step 3: newNode.prev = NULL          → NULL ← newNode
Step 4: HEAD.prev = newNode          → [10].prev → [5]
Step 5: HEAD = newNode               → HEAD now points to [5]

AFTER:
NULL ←[5]⇄[10]⇄[20]⇄[30]→ NULL
      HEAD
```

**Time: O(1)**

---

### 3.2 INSERTION AT END — O(1) if TAIL pointer maintained, O(n) otherwise

```
BEFORE:
NULL ←[10]⇄[20]⇄[30]→ NULL
                  TAIL

Insert 40 at end:

Step 1: Create new node [40]
Step 2: newNode.prev = TAIL          → [40].prev → [30]
Step 3: newNode.next = NULL          → [40].next = NULL
Step 4: TAIL.next = newNode          → [30].next → [40]
Step 5: TAIL = newNode               → TAIL now points to [40]

AFTER:
NULL ←[10]⇄[20]⇄[30]⇄[40]→ NULL
                       TAIL
```

**Time: O(1) with TAIL pointer** ← ADVANTAGE over SLL!

---

### 3.3 DELETION — THE BIG DLL ADVANTAGE ← KEY PYQ TOPIC

**In SLL:** To delete a node, you needed the PREVIOUS node's reference (because you can't go backward).

**In DLL:** Every node HAS a `prev` pointer, so you can delete ANY node given just that node's reference!

```
Delete node [20] from: NULL ←[10]⇄[20]⇄[30]⇄[40]→ NULL

Given only the reference to [20]:

Step 1: [20].prev.next = [20].next   → [10].next → [30]
Step 2: [20].next.prev = [20].prev   → [30].prev → [10]
Step 3: delete [20]

AFTER:
NULL ←[10]⇄[30]⇄[40]→ NULL
```

**Time: O(1)** if you have the node reference!
In SLL this was O(n) because you had to find the previous node by traversal.

> 🔑 **PYQ GOLD:** "In DLL, deletion of a given node is O(1) if you have a pointer to it — because the prev pointer gives direct access to the previous node."

---

### 3.4 TRAVERSAL — BIDIRECTIONAL ← DLL's Crown Feature

```
FORWARD traversal (HEAD → TAIL):
  curr = HEAD
  while curr ≠ NULL:
      print curr.data
      curr = curr.next

BACKWARD traversal (TAIL → HEAD):
  curr = TAIL
  while curr ≠ NULL:
      print curr.data
      curr = curr.prev
```

**SLL:** Can only go forward (HEAD → NULL)
**DLL:** Can go BOTH forward AND backward ← BIG advantage!

---

## 📌 SECTION 4: DLL COMPLEXITY TABLE

```
┌─────────────────────────────┬────────────┬────────────┐
│         OPERATION           │  DLL TIME  │  SLL TIME  │
├─────────────────────────────┼────────────┼────────────┤
│ Insert at beginning         │   O(1)     │   O(1)     │
│ Insert at end (with TAIL)   │   O(1) ✓   │   O(1)     │
│ Insert at end (no TAIL)     │   O(n)     │   O(n)     │
│ Delete given node reference │   O(1) ✓   │   O(n) ✗   │
│ Delete from beginning       │   O(1)     │   O(1)     │
│ Delete from end (with TAIL) │   O(1) ✓   │   O(n) ✗   │
│ Search                      │   O(n)     │   O(n)     │
│ Traversal (forward)         │   O(n)     │   O(n)     │
│ Traversal (backward)        │   O(n) ✓   │  NOT possible ✗ │
└─────────────────────────────┴────────────┴────────────┘
```

---

## 📌 SECTION 5: DLL ADVANTAGES vs DISADVANTAGES

### ✅ ADVANTAGES of DLL over SLL:

```
1. BIDIRECTIONAL traversal (forward + backward)
2. Deletion is O(1) when node reference is given
   (no need to find previous node)
3. Easier to implement DEQUE (Double Ended Queue)
   → O(1) insert/delete at BOTH ends
4. Insert before a given node is easier
```

### ❌ DISADVANTAGES of DLL vs SLL:

```
1. MORE MEMORY per node (extra prev pointer)
2. HARDER TO IMPLEMENT (more pointers to manage)
   → Every operation must update BOTH prev and next
3. Slightly more complex logic in all operations
```

> ⚠️ **BPSC PYQ TRAP:** "Doubly linked list is EASIER to implement than singly linked list"
> **Answer: FALSE** — DLL is HARDER to implement (more pointers to maintain).
> This has appeared multiple times in BPSC TRE exams!

---

## 📌 SECTION 6: CIRCULAR LINKED LIST (CLL) — STRUCTURE

In a **Circular Linked List**, the **last node points back to the FIRST node** instead of NULL.

### Singly Circular LL:

```
     HEAD
      │
      ▼
    [10|→]──►[20|→]──►[30|→]──►[40|→]─┐
      ▲                                │
      └────────────────────────────────┘
                (40 points back to 10)
```

**Key difference from SLL:** NO NULL at the end. Last node's `next` = `HEAD` (first node).

---

### Doubly Circular LL:

```
  ┌───────────────────────────────────────────┐
  │                                           │
  ▼                                           │
[←|10|→]⇄[←|20|→]⇄[←|30|→]⇄[←|40|→]       │
  │                            │              │
  │   HEAD.prev → last node ───┘              │
  └── last.next → HEAD ───────────────────────┘
```

---

## 📌 SECTION 7: CLL — EMPTY vs NON-EMPTY CONDITIONS

```
SINGLY CIRCULAR LL:
  Empty:    HEAD = NULL
  One node: HEAD.next = HEAD  (points to itself!)
  
DOUBLY CIRCULAR LL:
  Empty:    HEAD = NULL
  One node: HEAD.next = HEAD AND HEAD.prev = HEAD
```

> ⚠️ **PYQ TRAP:** In Circular LL, an empty list has HEAD = NULL (same as SLL).
> A list with ONE node has HEAD.next = HEAD (points to itself).

---

## 📌 SECTION 8: HOW TO DETECT END OF LIST

```
SINGLY LL:    Stop when curr.next == NULL
DOUBLY LL:    Stop when curr.next == NULL

CIRCULAR LL:  Stop when curr.next == HEAD  ← DIFFERENT!
              (because there is no NULL at end)
```

This is a very common PYQ question — how do you know when traversal is complete in CLL?

---

## 📌 SECTION 9: CLL APPLICATIONS — WHERE IS IT USED?

```
CIRCULAR LL is used in:
┌────────────────────────────────────────────────────┐
│ 1. ROUND ROBIN CPU SCHEDULING                      │
│    (processes cycle through — perfect for CLL!)    │
│                                                    │
│ 2. MULTIPLAYER GAMES (turn rotation)               │
│    Player 1 → Player 2 → Player 3 → Player 1...   │
│                                                    │
│ 3. MUSIC PLAYLIST (repeat mode)                    │
│    Last song → first song (circular)               │
│                                                    │
│ 4. BUFFER/MEMORY MANAGEMENT (circular buffer)      │
│                                                    │
│ 5. JOSEPHUS PROBLEM (classic algorithm problem)    │
│                                                    │
│ 6. Implementation of CIRCULAR QUEUE                │
└────────────────────────────────────────────────────┘
```

> ⚠️ **BPSC Option D Trap:**
> Q: "Which is an application of Circular Linked List?"
> (A) Round Robin Scheduling (B) Music playlists (C) Circular buffers
> → Answer = **(D) More than one of the above**

---

## 📌 SECTION 10: DEQUE USING DOUBLY LINKED LIST

**Deque** = Double Ended Queue = insert/delete from BOTH ends.

```
DLL implementation of Deque:
  HEAD ←[←|1|→]⇄[←|2|→]⇄[←|3|→]⇄[←|4|→]→ TAIL

Operations:
  insertFront()  → Insert at HEAD → O(1)
  insertRear()   → Insert at TAIL → O(1)
  deleteFront()  → Delete HEAD    → O(1)
  deleteRear()   → Delete TAIL    → O(1)
```

ALL FOUR operations = **O(1)** using DLL with HEAD and TAIL pointers.

> 🔑 **PYQ GOLD:** "Best data structure to implement a Deque with O(1) operations at both ends?"
> **Answer: Doubly Linked List**

---

## 📌 SECTION 11: MASTER COMPARISON TABLE — ALL 3 TYPES

```
┌──────────────────┬────────────┬────────────┬──────────────┐
│   PARAMETER      │  SINGLY LL │  DOUBLY LL │ CIRCULAR LL  │
├──────────────────┼────────────┼────────────┼──────────────┤
│ Pointers/node    │     1      │     2      │     1        │
│ Memory/node      │   Less     │   MORE     │   Less       │
│ Traversal        │ Forward    │ BOTH ways  │ Forward(loop)│
│ Implementation   │  Simpler   │  HARDER    │  Medium      │
│ Last node points │   NULL     │   NULL     │  to HEAD     │
│ Backward traverse│  NO        │   YES      │  NO (singly) │
│ Insert at end    │   O(n)*    │   O(1)**   │   O(n)*      │
│ Delete given node│   O(n)     │   O(1)     │   O(n)       │
│ Best for         │General use │ Deque/Undo │ Round Robin  │
└──────────────────┴────────────┴────────────┴──────────────┘
* Without tail pointer  ** With tail pointer
```

---

## 📌 SECTION 12: IMPORTANT PYQ FACTS — MEMORIZE!

| # | Statement | True/False |
|---|-----------|-----------|
| 1 | DLL requires more memory than SLL | **TRUE** |
| 2 | DLL is easier to implement than SLL | **FALSE** ← PYQ Trap |
| 3 | In DLL, bidirectional traversal is possible | **TRUE** |
| 4 | Circular LL last node points to NULL | **FALSE** → points to HEAD |
| 5 | DLL deletion of given node is O(1) | **TRUE** |
| 6 | SLL deletion of given node is O(n) | **TRUE** |
| 7 | Best structure for Deque = DLL | **TRUE** |
| 8 | CLL is used in Round Robin Scheduling | **TRUE** |
| 9 | CLL traversal ends when curr.next = NULL | **FALSE** → ends when curr.next = HEAD |
| 10 | DLL can easily implement Stack and Queue | **TRUE** |

---

## 📌 SECTION 13: MEMORY DIAGRAM FOR DLL (BPSC Exam Style)

```
DLL: 10 ⇄ 20 ⇄ 30

Address | Prev  | Data | Next
--------|-------|------|------
  200   | NULL  |  10  | 450     ← HEAD (first node, prev=NULL)
  450   |  200  |  20  | 800     ← Middle node
  800   |  450  |  30  | NULL    ← Last node (next=NULL)

HEAD = 200
TAIL = 800
```

---

## 📌 SECTION 14: SPECIAL OPERATIONS — DLL REVERSE

Reversing a DLL = swap prev and next pointers of every node:

```
Original:  NULL ←[10]⇄[20]⇄[30]→ NULL

After reverse: NULL ←[30]⇄[20]⇄[10]→ NULL

Algorithm:
  curr = HEAD
  while curr ≠ NULL:
      swap(curr.prev, curr.next)   ← swap the two pointers
      curr = curr.prev             ← move to next (which is now prev after swap)
  HEAD = last node visited
```

**Time: O(n)** — single traversal

---

## 📌 SECTION 15: UNDO/REDO USING DOUBLY LINKED LIST

One of the most elegant applications:

```
TEXT EDITOR STATE:
NULL ←[State1]⇄[State2]⇄[State3]⇄[State4]→ NULL
                                    ↑
                               current position

UNDO: curr = curr.prev  (go backward in DLL)
REDO: curr = curr.next  (go forward in DLL)
```

> This is why DLL is used in browser history (back/forward buttons) and text editors!

---

# ═══════════════════════════════════════════════
# 📚 PART 2: GENERAL STUDIES
## DIRECTIVE PRINCIPLES OF STATE POLICY (DPSP)
## Articles 36–51 + Fundamental Duties (Article 51A)
### Most Important Polity GS Topic After FRs
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT ARE DPSPs?

```
PART IV of the Indian Constitution
Articles 36 to 51

Source: Inspired by Irish Constitution (Ireland)
         (also influenced by Spanish Constitution)

Nature: NON-JUSTICIABLE
        = Cannot be enforced in any court of law
        = Court CANNOT compel the State to implement them
        
Purpose: Guidelines to State for making laws and policies
         Welfare state goals
```

> 🔑 **KEY CONTRAST:**
> **Fundamental Rights** = JUSTICIABLE (enforceable in court) → Part III
> **DPSPs** = NON-JUSTICIABLE (not enforceable in court) → Part IV

---

## 📌 SECTION 2: ORIGIN AND PHILOSOPHY

```
DPSP = "Instrument of Instructions" in Government of India Act, 1935
       (similar concept existed in colonial era)

Borrowed from: IRELAND (Directive Principles in Irish Constitution)

Dr. Ambedkar said: "DPSPs are novel features of the Constitution"

Granville Austin called them:
"Conscience of the Constitution"

DPSPs aim for:
→ Welfare State (social and economic justice)
→ Reduce inequality
→ Protect weaker sections
```

---

## 📌 SECTION 3: THREE CATEGORIES OF DPSPs

DPSPs are classified into THREE categories:

```
┌──────────────────────────────────────────────────────────┐
│                  DPSP CATEGORIES                         │
│                                                          │
│  ┌──────────────┬──────────────┬──────────────────────┐  │
│  │ SOCIALISTIC  │  GANDHIAN    │ LIBERAL-INTELLECTUAL │  │
│  │  (Art 38-48) │ (Art 40-48)  │   (Art 44-51)        │  │
│  │              │              │                      │  │
│  │ Social &     │ Reconstruction│ Individual Liberty   │  │
│  │ Economic     │ of Rural India│ & International     │  │
│  │ Justice      │               │ Peace               │  │
│  └──────────────┴──────────────┴──────────────────────┘  │
└──────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 4: SOCIALISTIC DPSPs — DETAIL

These aim for **social and economic democracy**:

| Article | Provision |
|---------|-----------|
| 38 | State to promote WELFARE of people — reduce inequalities |
| 39(a) | Adequate means of livelihood for all citizens |
| 39(b) | Distribution of community resources for common good |
| 39(c) | Prevent concentration of wealth |
| 39(d) | Equal pay for equal work (men and women) |
| 39(e) | Protect health of workers and children |
| 39(f) | Children given free environment for development |
| 41 | Right to work, education, public assistance |
| 42 | Just and humane conditions of work + maternity relief |
| 43 | Living wage for workers |
| 43A | Workers' participation in management of industries |
| 47 | Raise level of nutrition and public health |

> 🔑 **PYQ FACT:** Article 39(d) = Equal pay for equal work.
> This is a DPSP, NOT a Fundamental Right! People often confuse this.

---

## 📌 SECTION 5: GANDHIAN DPSPs — DETAIL

These aim to **reconstruct rural India** on Gandhian lines:

| Article | Provision |
|---------|-----------|
| 40 | Organise VILLAGE PANCHAYATS (Panchayati Raj) |
| 43 | Promote cottage industries in rural areas |
| 43B | Promote co-operative societies |
| 46 | Promote educational and economic interests of SC, ST, other weaker sections |
| 47 | Prohibit consumption of intoxicating drinks and drugs |
| 48 | Organise agriculture and animal husbandry — improve cattle breeds, prohibit cow slaughter |

> ⚠️ **BPSC TRAP:** Article 40 — organise Village Panchayats — is a DPSP (Gandhian).
> The actual 73rd Amendment (1992) made Panchayati Raj a Constitutional provision.
> Article 40 = DPSP; 73rd Amendment = Constitutional right.

> ⚠️ **TRAP 2:** Article 48 — prohibit cow slaughter — is a DPSP (not a law itself).
> States can make their own laws based on this directive.

---

## 📌 SECTION 6: LIBERAL-INTELLECTUAL DPSPs — DETAIL

These reflect **modern liberal values** and **international peace**:

| Article | Provision |
|---------|-----------|
| 44 | UNIFORM CIVIL CODE for all citizens |
| 45 | Early childhood care & education for children under 6 years |
| 48 | Modern scientific agriculture and animal husbandry |
| 48A | Protect and improve ENVIRONMENT and forests (added by 42nd Amendment) |
| 49 | Protect monuments, places of historical/national importance |
| 50 | SEPARATION OF JUDICIARY from Executive |
| 51 | Promote international peace and security |

> 🔑 **THE MOST FAMOUS DPSP — Article 44: UNIFORM CIVIL CODE (UCC)**
> - Directive to have ONE personal law for ALL citizens regardless of religion
> - Currently: different personal laws for Hindus, Muslims, Christians, etc.
> - Goa has a UCC (uniform civil code) — ONLY state in India
> - UCC has been a politically debated topic

> 🔑 **Article 50 — Separation of Judiciary from Executive:**
> - Currently in India they are NOT fully separate
> - Magistrates work under executive in many areas
> - This is the DPSP goal but not fully achieved

> 🔑 **Article 48A — Environment Protection:**
> - Added by **42nd Amendment, 1976** (Mini Constitution)
> - Also added to Fundamental Duties (Art 51A(g))

---

## 📌 SECTION 7: FR vs DPSP — THE CLASSIC CONFLICT

This is one of the MOST tested topics in BPSC TRE GS section.

```
FUNDAMENTAL RIGHTS vs DPSP:

FUNDAMENTAL RIGHTS          │  DIRECTIVE PRINCIPLES
(Part III, Art 12–35)       │  (Part IV, Art 36–51)
─────────────────────────────┼──────────────────────────────
Negative obligations         │  Positive obligations
(State must NOT do things)   │  (State SHOULD do things)
                             │
Justiciable                  │  Non-justiciable
(enforceable in court)       │  (not enforceable in court)
                             │
Promote political democracy  │  Promote socio-economic democracy
                             │
Borrowed from USA            │  Borrowed from IRELAND
                             │
Can be suspended (some)      │  Cannot be suspended BUT also
during Emergency             │  cannot be enforced
                             │
Individual rights            │  Community rights
```

---

## 📌 SECTION 8: LANDMARK CASES — FR vs DPSP CONFLICT

These cases are HEAVILY tested in BPSC. Memorize them!

### Case 1: Champakam Dorairajan Case (1951) — FIRST CONFLICT

```
FACTS:
Madras government reserved seats in medical colleges 
based on religion and caste under a DPSP.
Champakam challenged it as violation of Art 15 (FR).

VERDICT: Supreme Court held → FR prevails over DPSP
         (when conflict arises, FRs win)
         
RESULT: Parliament passed 1st Constitutional Amendment (1951)
        Added Art 15(4) — allowed reservations for backward classes
```

### Case 2: Golaknath Case (1967)

```
FACTS: Punjab government took land under agrarian reform law.
       Golaknath family challenged it as violation of FR.

VERDICT: Supreme Court held → Parliament CANNOT amend FRs
         (FRs are sacred and immutable)
         
IMPACT: Parliament could NOT override FRs for DPSP implementation
```

### Case 3: Kesavananda Bharati Case (1973) — MOST IMPORTANT

```
FACTS: Kerala government took Church lands under land reform law.
       Kesavananda Bharati challenged under FR of religion.

VERDICT: Supreme Court held → Parliament CAN amend FRs
         BUT cannot alter the BASIC STRUCTURE of Constitution
         
BASIC STRUCTURE DOCTRINE established here.
Key elements: Supremacy of Constitution, Republican & Democratic 
form of government, Secularism, Separation of powers,
Judicial Review, FRs are part of basic structure
         
IMPACT: Parliament CAN amend FRs to implement DPSPs BUT 
        CANNOT destroy the basic structure
```

### Case 4: Minerva Mills Case (1980)

```
FACTS: 42nd Amendment (1976) gave DPSP absolute supremacy 
       over FRs (Art 31C was expanded).
       Minerva Mills challenged this.

VERDICT: Supreme Court struck down the 42nd Amendment's 
         claim of absolute DPSP supremacy.
         
HELD: "There must be HARMONY between FRs and DPSPs"
      "Neither can be sacrificed for the other"
      Balance between them is part of basic structure.
```

### Summary of FR vs DPSP Evolution:

```
1950: FR > DPSP (FR wins in any conflict)
1951: Champakam — confirmed FR supremacy
1967: Golaknath — Parliament can't amend FRs
1973: Kesavananda — Basic Structure Doctrine
      Parliament CAN amend but not destroy basics
1976: 42nd Amendment — gave DPSP supremacy (overreach)
1980: Minerva Mills — HARMONY is required
      Balance between FR and DPSP = Basic Structure
```

> 🔑 **ONE-LINE ANSWER:** "What is the current relationship between FRs and DPSPs?"
> **FRs and DPSPs must be harmoniously interpreted — neither can be made absolutely supreme over the other (Minerva Mills, 1980).**

---

## 📌 SECTION 9: FUNDAMENTAL DUTIES (Article 51A)

```
PART IV-A (added by 42nd Amendment, 1976)
Article 51A

Originally: 10 Fundamental Duties
After 86th Amendment (2002): 11 Fundamental Duties

Source: USSR Constitution (Soviet Union)

Nature: NON-JUSTICIABLE
        (like DPSPs — not directly enforceable)
        BUT Parliament CAN enact laws to enforce them
```

### ALL 11 FUNDAMENTAL DUTIES:

```
Article 51A — Every citizen of India shall:

(a)  Abide by Constitution and respect National Flag & National Anthem
(b)  Cherish noble ideals of national struggle for freedom
(c)  Uphold and protect sovereignty, unity, integrity of India
(d)  Defend the country and render national service
(e)  Promote harmony and brotherhood — transcend religious, 
     linguistic, regional or sectional diversities
(f)  Preserve rich heritage of our composite culture
(g)  Protect and improve NATURAL ENVIRONMENT
     (forests, lakes, rivers, wildlife)
(h)  Develop scientific temper, humanism, spirit of enquiry & reform
(i)  Safeguard public property; abjure violence
(j)  Strive towards excellence in individual and collective activity
(k)  [11th Duty — added by 86th Amendment, 2002]
     Parent or guardian shall provide opportunities for education
     to children/wards between ages 6 and 14

MNEMONIC for remembering count: "10 + 1 = 11 duties"
(10 original in 1976 + 1 added in 2002)
```

> ⚠️ **PYQ TRAPS on Fundamental Duties:**
> 1. Added by 42nd Amendment (1976) — in Indira Gandhi's government during Emergency
> 2. Originally 10 duties; 86th Amendment (2002) added the 11th
> 3. Source = USSR (Soviet Union) Constitution
> 4. Non-justiciable (but Parliament can pass laws to enforce them)
> 5. The 11th duty (Article 51A(k)) relates to EDUCATION for children 6–14

---

## 📌 SECTION 10: ARTICLE 44 — UNIFORM CIVIL CODE (Special Focus)

```
WHAT IS UCC?
One set of personal laws for ALL citizens regardless of religion:
  • Marriage, divorce, inheritance, adoption
  
CURRENT SITUATION:
  • Hindus: Hindu Marriage Act, Hindu Succession Act
  • Muslims: Muslim Personal Law (Shariat)
  • Christians: Indian Christian Marriage Act
  • Parsis: Parsi Marriage and Divorce Act

ONLY GOA has Uniform Civil Code (Portuguese Civil Code — colonial era)
Goa = only state with UCC in India

CONSTITUTIONAL PROVISION: Article 44 (DPSP) directs the State to 
secure UCC — but it's been a matter of political debate since 1949

SUPREME COURT repeatedly called on Parliament to enact UCC:
  → Shah Bano case (1985)
  → Sarla Mudgal case (1995)
```

---

## 📌 SECTION 11: KEY ARTICLES QUICK REFERENCE — DPSP

| Article | Subject | Category |
|---------|---------|---------|
| 36 | Definition of "State" for DPSP | General |
| 37 | Application of DPSP | General |
| 38 | Welfare State, reduce inequalities | Socialistic |
| 39 | Livelihood, resources, equal pay | Socialistic |
| 39A | Equal justice and free legal aid | Added by 42nd Amendment |
| 40 | Organise Village Panchayats | Gandhian |
| 41 | Right to work, education, assistance | Socialistic |
| 42 | Just conditions of work + maternity | Socialistic |
| 43 | Living wage + cottage industries | Gandhian/Socialistic |
| 43A | Workers' participation in management | Added by 42nd Amendment |
| 44 | Uniform Civil Code | Liberal-Intellectual |
| 45 | Early childhood care (under 6 yrs) | Liberal-Intellectual |
| 46 | Promote SC/ST interests | Gandhian |
| 47 | Nutrition, public health, prohibit intoxicants | Gandhian |
| 48 | Agriculture, animal husbandry, cow slaughter | Gandhian |
| 48A | Protect environment | Liberal-Intellectual (42nd Amdt) |
| 49 | Protect monuments of national importance | Liberal-Intellectual |
| 50 | Separation of Judiciary from Executive | Liberal-Intellectual |
| 51 | International peace and security | Liberal-Intellectual |

---

## 📌 SECTION 12: BIHAR-SPECIFIC DPSP APPLICATIONS

```
BIHAR context of DPSPs:

1. Bihar Panchayati Raj Act (Article 40 DPSP → 73rd Amendment):
   3-tier system: Gram Panchayat → Panchayat Samiti → Zila Parishad

2. Bihar has reservation for SC/ST/OBC in Panchayats
   (implementing Art 46 — protect weaker sections)

3. Bihar Land Reforms Act: Implemented Art 39(b) — distribution 
   of resources for common good

4. Bihar Prohibition and Excise Act 2016:
   Total liquor prohibition in Bihar
   Implementing Art 47 (prohibit intoxicants) — Gandhian DPSP
   *** BPSC IMPORTANT: Bihar enacted alcohol prohibition in April 2016 ***

5. Mid-Day Meal Scheme in Bihar schools:
   Implementing Art 47 (nutrition) + Art 21A (education)
```

> ⚠️ **BPSC SPECIAL:** Bihar's alcohol prohibition (Nitish Kumar government, 2016) is the most famous state-level implementation of the Gandhian DPSP (Article 47).

---

## 📌 SECTION 13: DIFFERENCE — DPSP vs FUNDAMENTAL DUTIES

```
┌──────────────────┬───────────────────┬───────────────────────┐
│   PARAMETER      │       DPSPs       │  FUNDAMENTAL DUTIES   │
├──────────────────┼───────────────────┼───────────────────────┤
│ Part             │ Part IV (36–51)   │ Part IV-A (51A)       │
│ For whom         │ State/Government  │ Citizens              │
│ Nature           │ Non-justiciable   │ Non-justiciable       │
│ Added            │ Original (1950)   │ 42nd Amdt (1976)      │
│ Source           │ Ireland           │ USSR                  │
│ Count            │ No fixed number   │ 11 duties             │
│ Direction        │ State's obligation│ Citizen's obligation  │
└──────────────────┴───────────────────┴───────────────────────┘
```

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 1 (CS)
## 25 Questions on Doubly LL & Circular LL
### ⚠️ ATTEMPT ALL 25 FIRST — ANSWERS ARE AT THE VERY END
# ═══════════════════════════════════════════════

---

**Q1.** A node in a Doubly Linked List contains:
- (A) Data and one pointer (next only)
- (B) Data and two pointers (prev and next)
- (C) Data and three pointers
- (D) More than one of the above
- (E) None of the above

---

**Q2.** Which statement about Doubly Linked List is CORRECT?
- (A) It is easier to implement than Singly Linked List
- (B) It is harder to implement than Singly Linked List
- (C) It requires less memory per node than Singly Linked List
- (D) More than one of the above
- (E) None of the above

---

**Q3.** The MAIN ADVANTAGE of Doubly Linked List over Singly Linked List is:
- (A) Uses less memory per node
- (B) Bidirectional traversal and O(1) deletion of a given node
- (C) Supports random access using index
- (D) More than one of the above
- (E) None of the above

---

**Q4.** In a Circular Linked List, the next pointer of the last node points to:
- (A) NULL
- (B) Previous node
- (C) First node (HEAD)
- (D) More than one of the above
- (E) None of the above

---

**Q5.** Deletion of a given node (when only its reference is given) in DLL has time complexity:
- (A) O(n) — same as SLL
- (B) O(log n)
- (C) O(1) — because prev pointer gives direct access
- (D) More than one of the above
- (E) None of the above

---

**Q6.** A Deque (Double Ended Queue) with O(1) operations at both ends is BEST implemented using:
- (A) Singly Linked List
- (B) Circular Linked List
- (C) Doubly Linked List with HEAD and TAIL pointers
- (D) More than one of the above
- (E) None of the above

---

**Q7.** In Circular Linked List traversal, the loop terminates when:
- (A) current.next == NULL
- (B) current.next == HEAD
- (C) current == NULL
- (D) More than one of the above
- (E) None of the above

---

**Q8.** Which of the following applications uses CIRCULAR Linked List?
- (A) Round Robin CPU Scheduling
- (B) Music playlist with repeat all mode
- (C) Multiplayer games — turn rotation
- (D) More than one of the above
- (E) None of the above

---

**Q9.** In an EMPTY Singly Circular Linked List:
- (A) HEAD = NULL
- (B) HEAD.next = HEAD
- (C) HEAD = -1
- (D) More than one of the above
- (E) None of the above

---

**Q10.** When a Circular Linked List contains EXACTLY ONE node, then:
- (A) HEAD.next = NULL
- (B) HEAD.next = HEAD (points to itself)
- (C) HEAD.prev = NULL
- (D) More than one of the above
- (E) None of the above

---

**Q11.** Which of the following is TRUE about Doubly Linked List?
- (A) Traversal can be done in both forward and backward directions
- (B) It requires extra memory for the additional prev pointer
- (C) Deletion from the end is O(1) with a TAIL pointer
- (D) More than one of the above
- (E) None of the above

---

**Q12.** In a Doubly Linked List, what is the prev pointer of the HEAD (first) node?
- (A) Points to the last node
- (B) Points to itself
- (C) NULL
- (D) More than one of the above
- (E) None of the above

---

**Q13.** Which data structure is used internally in a BROWSER to implement the BACK and FORWARD buttons?
- (A) Singly Linked List
- (B) Circular Linked List
- (C) Doubly Linked List
- (D) More than one of the above
- (E) None of the above

---

**Q14.** The time complexity of INSERTING a node at the beginning of a Doubly Linked List is:
- (A) O(n)
- (B) O(log n)
- (C) O(1)
- (D) More than one of the above
- (E) None of the above

---

**Q15.** A Doubly Circular Linked List with HEAD and TAIL pointers — what is TAIL.next?
- (A) NULL
- (B) HEAD (first node)
- (C) TAIL itself
- (D) More than one of the above
- (E) None of the above

---

**Q16.** To REVERSE a Doubly Linked List, for each node we need to:
- (A) Set the node's data to zero
- (B) Swap the prev and next pointers of each node
- (C) Delete all nodes and rebuild from scratch
- (D) More than one of the above
- (E) None of the above

---

**Q17.** Which of the following correctly states the DISADVANTAGE of Doubly Linked List?
- (A) Cannot traverse in forward direction
- (B) Extra memory required for prev pointer + harder to implement
- (C) Cannot perform insertion at beginning
- (D) More than one of the above
- (E) None of the above

---

**Q18.** In a DLL with 5 nodes: 10⇄20⇄30⇄40⇄50. After deleting node 30 (given its direct reference), what is 20.next and 40.prev?
- (A) 20.next = NULL; 40.prev = NULL
- (B) 20.next = 40; 40.prev = 20
- (C) 20.next = 50; 40.prev = 10
- (D) More than one of the above
- (E) None of the above

---

**Q19.** The JOSEPHUS PROBLEM is a classic algorithmic problem best solved using:
- (A) Array
- (B) Stack
- (C) Circular Linked List
- (D) More than one of the above
- (E) None of the above

---

**Q20.** Compared to SLL, which operations are MORE EFFICIENT in DLL? (Choose all that apply)
- (A) Deletion of last node (with TAIL pointer)
- (B) Backward traversal
- (C) Delete a node given only its reference
- (D) More than one of the above
- (E) None of the above

---

**Q21.** In a DLL, which operation has the SAME time complexity as in SLL?
- (A) Delete a given node by reference
- (B) Backward traversal
- (C) Search for an element
- (D) More than one of the above
- (E) None of the above

---

**Q22.** An UNDO/REDO feature in a text editor is BEST implemented using:
- (A) Stack only
- (B) Queue only
- (C) Doubly Linked List (current position moves forward/backward)
- (D) More than one of the above
- (E) None of the above

---

**Q23.** Which of these statements about memory usage is CORRECT?
- (A) DLL uses same memory as SLL per node
- (B) DLL uses MORE memory than SLL per node (extra prev pointer)
- (C) CLL uses more memory than both SLL and DLL
- (D) More than one of the above
- (E) None of the above

---

**Q24.** A Doubly Linked List is to SLL what a ______ is to a one-way road.
- (A) Circular road
- (B) Two-way (bidirectional) road
- (C) Dead end
- (D) More than one of the above
- (E) None of the above

---

**Q25.** In which scenario is a CIRCULAR Linked List PREFERRED over a regular SLL?
- (A) When you need random access to elements
- (B) When traversal needs to cycle back to the beginning automatically
- (C) When you need backward traversal
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 2 (GS)
## 25 Questions on DPSP + Fundamental Duties
### ⚠️ ATTEMPT ALL 25 FIRST — ANSWERS ARE AT THE VERY END
# ═══════════════════════════════════════════════

---

**Q26.** Directive Principles of State Policy are contained in which Part of the Indian Constitution?
- (A) Part III (Articles 12–35)
- (B) Part IV (Articles 36–51)
- (C) Part IV-A (Article 51A)
- (D) More than one of the above
- (E) None of the above

---

**Q27.** DPSPs in the Indian Constitution were inspired by the Constitution of which country?
- (A) United States of America
- (B) United Kingdom
- (C) Ireland
- (D) More than one of the above
- (E) None of the above

---

**Q28.** Which of the following CORRECTLY describes the nature of DPSPs?
- (A) Justiciable — enforceable in courts
- (B) Non-justiciable — cannot be enforced by courts
- (C) Enforceable only by the President
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Granville Austin described DPSPs as:
- (A) "The Heart and Soul of the Constitution"
- (B) "Conscience of the Constitution"
- (C) "Fundamental Law of the Land"
- (D) More than one of the above
- (E) None of the above

---

**Q30.** Article 39(d) of the Constitution directs the State to ensure:
- (A) Free education to children 6–14 years
- (B) Equal pay for equal work for both men and women
- (C) Prohibition of child labour
- (D) More than one of the above
- (E) None of the above

---

**Q31.** Article 44 of the Constitution directs the State to secure:
- (A) Equal justice and free legal aid
- (B) Uniform Civil Code for all citizens
- (C) Separation of Judiciary from Executive
- (D) More than one of the above
- (E) None of the above

---

**Q32.** Article 40 (Gandhian DPSP) directs the State to:
- (A) Prohibit consumption of intoxicants
- (B) Organise Village Panchayats
- (C) Protect cow from slaughter
- (D) More than one of the above
- (E) None of the above

---

**Q33.** Article 48A (Protect and improve environment) was added to the Constitution by:
- (A) 44th Amendment, 1978
- (B) 42nd Amendment, 1976
- (C) 86th Amendment, 2002
- (D) More than one of the above
- (E) None of the above

---

**Q34.** In the CHAMPAKAM DORAIRAJAN case (1951), the Supreme Court held that:
- (A) DPSPs override Fundamental Rights
- (B) Fundamental Rights override DPSPs
- (C) Both are equal and must be balanced
- (D) More than one of the above
- (E) None of the above

---

**Q35.** The KESAVANANDA BHARATI case (1973) is famous for establishing the:
- (A) Doctrine of Eclipse
- (B) Basic Structure Doctrine
- (C) Doctrine of Harmonious Construction
- (D) More than one of the above
- (E) None of the above

---

**Q36.** In the MINERVA MILLS case (1980), the Supreme Court held that:
- (A) DPSPs are absolutely supreme over Fundamental Rights
- (B) Fundamental Rights are absolutely supreme over DPSPs
- (C) There must be HARMONY between FRs and DPSPs
- (D) More than one of the above
- (E) None of the above

---

**Q37.** The Fundamental Duties were added to the Constitution by which Amendment?
- (A) 44th Amendment, 1978
- (B) 42nd Amendment, 1976
- (C) 86th Amendment, 2002
- (D) More than one of the above
- (E) None of the above

---

**Q38.** Fundamental Duties in the Indian Constitution were inspired by the Constitution of:
- (A) Ireland
- (B) Germany
- (C) USSR (Soviet Union)
- (D) More than one of the above
- (E) None of the above

---

**Q39.** How many Fundamental Duties are there currently in the Indian Constitution?
- (A) 10
- (B) 11
- (C) 12
- (D) More than one of the above
- (E) None of the above

---

**Q40.** The 11th Fundamental Duty (added by 86th Amendment, 2002) relates to:
- (A) Protecting the environment
- (B) Developing scientific temper
- (C) Parents providing education to children (6–14 years)
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Article 47 (a Gandhian DPSP) directs the State to:
- (A) Organise village panchayats
- (B) Raise the level of nutrition, public health, and prohibit intoxicating drinks
- (C) Ensure equal pay for equal work
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Which DPSP directs separation of Judiciary from Executive?
- (A) Article 44
- (B) Article 48A
- (C) Article 50
- (D) More than one of the above
- (E) None of the above

---

**Q43.** Bihar enacted a total ALCOHOL PROHIBITION law in which year, implementing Article 47 DPSP?
- (A) 2014
- (B) 2016
- (C) 2018
- (D) More than one of the above
- (E) None of the above

---

**Q44.** Which is the ONLY state in India that has implemented a Uniform Civil Code (Article 44)?
- (A) Gujarat
- (B) Goa
- (C) Maharashtra
- (D) More than one of the above
- (E) None of the above

---

**Q45.** Article 43A (added by 42nd Amendment) directs the State to:
- (A) Protect monuments of national importance
- (B) Ensure workers' participation in the management of industries
- (C) Promote international peace
- (D) More than one of the above
- (E) None of the above

---

**Q46.** Which of the following is a GANDHIAN DPSP?
- (A) Uniform Civil Code (Article 44)
- (B) International Peace (Article 51)
- (C) Prohibit cow slaughter (Article 48)
- (D) More than one of the above
- (E) None of the above

---

**Q47.** Which Fundamental Duty relates to PROTECTING THE ENVIRONMENT?
- (A) Article 51A(d)
- (B) Article 51A(g)
- (C) Article 51A(k)
- (D) More than one of the above
- (E) None of the above

---

**Q48.** The GOLAKNATH case (1967) was overruled by which subsequent case?
- (A) Champakam Dorairajan (1951)
- (B) Minerva Mills (1980)
- (C) Kesavananda Bharati (1973)
- (D) More than one of the above
- (E) None of the above

---

**Q49.** Article 51A is contained in which Part of the Constitution?
- (A) Part III
- (B) Part IV
- (C) Part IV-A
- (D) More than one of the above
- (E) None of the above

---

**Q50.** Which of the following CORRECTLY distinguishes DPSPs from Fundamental Rights?
- (A) DPSPs are in Part III; FRs in Part IV
- (B) FRs are justiciable; DPSPs are non-justiciable
- (C) FRs are borrowed from USA; DPSPs from Ireland
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY WITH DETAILED EXPLANATIONS
## CS Answers (Q1–Q25) | GS Answers (Q26–Q50)
# ═══════════════════════════════════════════════

---

## 🖥️ CS ANSWERS — DOUBLY LL & CIRCULAR LL

---

**A1. → (B) Data and two pointers (prev and next)**
DLL node = 3 fields total: data field + prev pointer + next pointer.
SLL = 2 fields (data + next). DLL has ONE extra pointer (prev).

---

**A2. → (B) It is harder to implement than Singly Linked List**
DLL is HARDER because every operation (insert, delete, update) must correctly update BOTH prev and next pointers. More logic, more chances of bugs. Memory per node is MORE, not less.

---

**A3. → (B) Bidirectional traversal and O(1) deletion of a given node**
These are the two crown advantages:
1. Can traverse both forward (next) and backward (prev)
2. Deletion of a given node = O(1) because prev pointer is already there
DLL does NOT support random access (that's arrays).

---

**A4. → (C) First node (HEAD)**
In Circular LL, last.next = HEAD (first node). There is NO NULL at the end.
This "circular" linking is what distinguishes it from regular SLL.

---

**A5. → (C) O(1)**
In DLL: given node X, deletion = `X.prev.next = X.next` and `X.next.prev = X.prev`. Since X already has the prev pointer, no traversal needed → O(1). In SLL, you'd need O(n) to find the previous node.

---

**A6. → (C) Doubly Linked List with HEAD and TAIL pointers**
DLL with HEAD + TAIL gives O(1) for:
- insertFront (at HEAD)
- insertRear (at TAIL)
- deleteFront (at HEAD)
- deleteRear (at TAIL via prev pointer)
This is exactly what a Deque needs.

---

**A7. → (B) current.next == HEAD**
In Circular LL, there is no NULL. Traversal ends when you come back to the first node i.e., `current.next == HEAD`. If you check for NULL, the loop will NEVER end (infinite loop)!

---

**A8. → (D) More than one of the above**
ALL three are applications of Circular Linked List:
- Round Robin Scheduling ✓ (processes cycle through)
- Music playlist repeat ✓ (last song → first song)
- Game turn rotation ✓ (last player → first player)
→ Answer = (D)

---

**A9. → (A) HEAD = NULL**
An EMPTY list (zero nodes) always has HEAD = NULL, whether SLL, DLL, or CLL. There are no nodes, so HEAD points to nothing.
Option B (HEAD.next = HEAD) = single node list, NOT empty.

---

**A10. → (B) HEAD.next = HEAD (points to itself)**
When exactly ONE node exists in a Circular LL:
- That one node's next must point to the first node = itself
- So HEAD.next = HEAD

---

**A11. → (D) More than one of the above**
ALL three statements about DLL are true:
(A) Bidirectional traversal ✓
(B) Extra memory for prev pointer ✓
(C) With TAIL pointer, delete from end = O(1) ✓
→ Answer = (D)

---

**A12. → (C) NULL**
HEAD (first node) has NO previous node. Therefore HEAD.prev = NULL.
Similarly, TAIL.next = NULL in a non-circular DLL.

---

**A13. → (C) Doubly Linked List**
Browser history = classic DLL application:
- BACK button = move to curr.prev
- FORWARD button = move to curr.next
Each page is a node; DLL enables bidirectional navigation.

---

**A14. → (C) O(1)**
Insert at beginning of DLL:
1. newNode.next = HEAD
2. newNode.prev = NULL
3. HEAD.prev = newNode
4. HEAD = newNode
No traversal needed → O(1). Same as SLL insert at beginning.

---

**A15. → (B) HEAD (first node)**
In Doubly CIRCULAR LL: TAIL.next = HEAD (it's circular).
Also HEAD.prev = TAIL. This creates a fully bidirectional circular structure.

---

**A16. → (B) Swap the prev and next pointers of each node**
To reverse DLL: for every node, swap prev↔next. Then update HEAD to point to what was previously the last node. Simple and elegant — O(n) single pass.

---

**A17. → (B) Extra memory + harder to implement**
Both are correct disadvantages of DLL:
- Extra memory: each node has an additional prev pointer
- Harder to implement: every operation manages 2 pointers
Option A is wrong (DLL can traverse forward). Option C is wrong (can insert at beginning in O(1)).

---

**A18. → (B) 20.next = 40; 40.prev = 20**
After deleting 30:
- 20.next must be updated to point to 40 (skip 30)
- 40.prev must be updated to point to 20 (skip 30)
This is the standard DLL deletion — both links are updated.

---

**A19. → (C) Circular Linked List**
Josephus Problem: n people in a circle, every k-th person is eliminated until one remains. The circular nature perfectly matches Circular Linked List — you go around and around eliminating nodes.

---

**A20. → (D) More than one of the above**
All three are MORE EFFICIENT in DLL vs SLL:
(A) Delete last node with TAIL = O(1) in DLL vs O(n) in SLL ✓
(B) Backward traversal = possible in DLL, impossible in SLL ✓
(C) Delete given node by reference = O(1) DLL vs O(n) SLL ✓
→ Answer = (D)

---

**A21. → (C) Search for an element**
Search = O(n) in BOTH SLL and DLL. You still need to traverse from HEAD checking each node. DLL's bidirectionality doesn't help with search complexity (same n nodes to check). Options A and B are where DLL is BETTER.

---

**A22. → (C) Doubly Linked List**
Undo/Redo uses current position in history:
- UNDO: curr = curr.prev
- REDO: curr = curr.next
DLL's bidirectional navigation is perfect. Stack alone handles only UNDO (one direction). For UNDO + REDO together → DLL is the clean solution.

---

**A23. → (B) DLL uses MORE memory than SLL per node**
SLL: data + 1 pointer = data_size + 4 bytes (or 8 on 64-bit)
DLL: data + 2 pointers = data_size + 8 bytes (or 16 on 64-bit)
CLL (singly circular): data + 1 pointer = same as SLL

---

**A24. → (B) Two-way (bidirectional) road**
This is a conceptual analogy: SLL = one-way road (go forward only). DLL = two-way road (go both directions). A perfect way to remember DLL's bidirectional traversal.

---

**A25. → (B) When traversal needs to cycle back to the beginning automatically**
CLL is preferred when the logic is inherently circular:
- Round Robin Scheduling
- Playlists on repeat
- Games with rotating turns
Option A (random access) → Array. Option C (backward traversal) → DLL.

---

## 📚 GS ANSWERS — DPSP + FUNDAMENTAL DUTIES

---

**A26. → (B) Part IV (Articles 36–51)**
DPSPs = Part IV, Articles 36–51.
FRs = Part III, Articles 12–35.
Fundamental Duties = Part IV-A, Article 51A.

---

**A27. → (C) Ireland**
DPSPs were directly inspired by the Irish Constitution (Ireland). Ireland borrowed the concept from Spain. India adopted it from Ireland.

---

**A28. → (B) Non-justiciable — cannot be enforced by courts**
DPSPs = Non-justiciable. Courts cannot compel the government to implement DPSPs. Unlike FRs (justiciable), DPSPs are merely guidelines/directives for the State.

---

**A29. → (B) "Conscience of the Constitution"**
Granville Austin called DPSPs the "Conscience of the Constitution." Dr. Ambedkar called Article 32 (not DPSP) the "Heart and Soul." Don't confuse these two famous quotes.

---

**A30. → (B) Equal pay for equal work for both men and women**
Article 39(d) = Equal pay for equal work. IMPORTANT: This is a DPSP (not a Fundamental Right). Many students mistake it for a FR because it sounds like a rights provision.

---

**A31. → (B) Uniform Civil Code for all citizens**
Article 44 = Uniform Civil Code. This is the most famous and debated DPSP — one set of personal laws for all citizens regardless of religion.

---

**A32. → (B) Organise Village Panchayats**
Article 40 = Organise Village Panchayats (Gandhian DPSP). This DPSP was eventually given constitutional force by the 73rd Amendment (1992).
- Article 47 = prohibit intoxicants
- Article 48 = cow slaughter prohibition

---

**A33. → (B) 42nd Amendment, 1976**
Article 48A (protect and improve environment, forests) was added by the 42nd Amendment in 1976. This is also reflected in Fundamental Duty 51A(g). The 42nd Amendment is called the "Mini Constitution" as it added many provisions.

---

**A34. → (B) Fundamental Rights override DPSPs**
Champakam Case (1951) = FIRST conflict case. Court held FRs prevail. Madras government's caste/religion-based reservations (done under DPSP) violated Art 15 (FR) → FR won.

---

**A35. → (B) Basic Structure Doctrine**
Kesavananda Bharati (1973) = Most important constitutional law case. 13-judge bench. Established that Parliament can amend the Constitution BUT cannot destroy its Basic Structure (federal character, separation of powers, judicial review, FRs, etc.).

---

**A36. → (C) There must be HARMONY between FRs and DPSPs**
Minerva Mills (1980): Court struck down 42nd Amendment's absolute supremacy of DPSPs. Held that the BALANCE between FRs and DPSPs is itself part of the Basic Structure. Neither can be sacrificed for the other.

---

**A37. → (B) 42nd Amendment, 1976**
Fundamental Duties were added by the 42nd Amendment (1976) during the Emergency period under Indira Gandhi. The 86th Amendment (2002) added the 11th duty about children's education.

---

**A38. → (C) USSR (Soviet Union)**
Fundamental Duties were inspired by the USSR (Soviet Union) Constitution, which had a concept of duties alongside rights. Not from Ireland (which gave DPSPs), not from USA (which gave FRs).

---

**A39. → (B) 11**
Currently 11 Fundamental Duties:
- 10 added by 42nd Amendment (1976)
- 11th added by 86th Amendment (2002)
Total = 11 duties.

---

**A40. → (C) Parents providing education to children (6–14 years)**
The 11th Fundamental Duty [Art 51A(k)] added by 86th Amendment (2002): "It shall be the duty of every citizen who is a parent or guardian to provide opportunities for education to his child or ward between the age of six and fourteen years." This complements Art 21A (Right to Education).

---

**A41. → (B) Raise level of nutrition, public health, and prohibit intoxicating drinks**
Article 47 = Raise level of nutrition + public health + prohibit intoxicants.
Bihar's liquor prohibition (2016) directly implements this Gandhian DPSP.

---

**A42. → (C) Article 50**
Article 50 = Separation of Judiciary from Executive. This is a Liberal-Intellectual DPSP. It means the judicial functions of magistrates should be separate from executive functions of state.

---

**A43. → (B) 2016**
Bihar enacted the Bihar Prohibition and Excise Act, 2016 imposing total alcohol prohibition. This was implemented under Nitish Kumar's government. It is a direct implementation of Art 47 (Gandhian DPSP). This is a BPSC-specific fact!

---

**A44. → (B) Goa**
Goa has a Uniform Civil Code — inherited from the Portuguese Civil Code during colonial era. All citizens in Goa (regardless of religion) are subject to the same personal law. Goa is the ONLY Indian state with UCC.

---

**A45. → (B) Ensure workers' participation in management of industries**
Article 43A was added by the 42nd Amendment (1976). It directs the State to take steps to secure participation of workers in management of undertakings, establishments, or organizations. This is about industrial democracy.

---

**A46. → (C) Prohibit cow slaughter (Article 48)**
Article 48 = Organize agriculture and animal husbandry on modern scientific lines AND prohibit slaughter of cows, calves, and other milch/draught cattle. This is a Gandhian DPSP.
- Article 44 (UCC) = Liberal-Intellectual
- Article 51 (International peace) = Liberal-Intellectual

---

**A47. → (B) Article 51A(g)**
Article 51A(g) = "To protect and improve the natural environment including forests, lakes, rivers and wildlife, and to have compassion for living creatures." This is the environmental protection Fundamental Duty.

---

**A48. → (C) Kesavananda Bharati (1973)**
Golaknath (1967) said Parliament CANNOT amend FRs.
Kesavananda Bharati (1973) OVERRULED Golaknath — said Parliament CAN amend FRs but cannot damage the Basic Structure.

---

**A49. → (C) Part IV-A**
Article 51A (Fundamental Duties) is in Part IV-A. This is a separate Part added by the 42nd Amendment. It is neither Part III (FRs) nor Part IV (DPSPs).

---

**A50. → (D) More than one of the above**
Options B and C are both correct:
(B) FRs are justiciable; DPSPs are non-justiciable ✓
(C) FRs borrowed from USA; DPSPs from Ireland ✓
Option A is WRONG: FRs = Part III; DPSPs = Part IV (not the other way)
→ Answer = (D) [B and C are both true]

---

# ═══════════════════════════════════════════════
# 📊 DAY 23 REVISION SUMMARY
## Quick-Recall Flash Points Before Sleeping
# ═══════════════════════════════════════════════

---

## 🖥️ CS FLASH CARDS — 10 MUST-REMEMBER FACTS

```
1. DLL node = DATA + PREV + NEXT (3 parts)
2. DLL is HARDER to implement than SLL (more pointers!)
3. DLL deletion of given node = O(1) (prev pointer helps)
4. DLL traversal = BIDIRECTIONAL (forward + backward)
5. Circular LL: last.next = HEAD (NOT NULL!)
6. Empty CLL: HEAD = NULL
7. Single-node CLL: HEAD.next = HEAD (self-loop!)
8. CLL traversal ends when: curr.next == HEAD
9. Best for Deque → DLL with HEAD + TAIL pointers
10. CLL used in: Round Robin, music playlists, Josephus problem
```

---

## 📚 GS FLASH CARDS — 10 MUST-REMEMBER FACTS

```
1. DPSPs = Part IV, Articles 36–51
2. DPSPs source = IRELAND (Fundamental Duties = USSR)
3. DPSPs = NON-JUSTICIABLE (FRs = justiciable)
4. Article 44 = Uniform Civil Code (most debated DPSP)
5. Article 40 = Village Panchayats (Gandhian DPSP)
6. Article 47 = Nutrition + health + prohibit intoxicants
7. Fundamental Duties = Part IV-A, Article 51A = 11 duties
8. 42nd Amdt (1976) added Fundamental Duties + Art 48A
9. 86th Amdt (2002) added 11th Fundamental Duty (education 6-14 yrs)
10. Minerva Mills (1980) = HARMONY between FRs and DPSPs
```

---

## 🔥 OPTION D TRAPS — KNOW BEFORE EXAM

```
TOPIC                                 │ When D applies
──────────────────────────────────────┼────────────────────────────
Applications of Circular LL          │ Multiple (scheduling + music + games)
Advantages of DLL over SLL           │ Multiple (bidirectional + O(1) deletion)
Which DPSPs are Gandhian?            │ Art 40, 43, 46, 47, 48 — multiple
Article 15 grounds                   │ ALL 5 grounds (Religion+Race+Caste+Sex+Place)
Art 51A Fundamental Duty on env.     │ Only Art 51A(g) = (B), not D
True statements about DLL            │ Often D (multiple true statements)
```

---

## 🗺️ LANDMARK CASE TIMELINE (BPSC Exam Shortcut)

```
1951 → Champakam   : FR > DPSP (FR wins)
1967 → Golaknath   : Parliament CANNOT amend FRs
1973 → Kesavananda : Basic Structure Doctrine
                     (can amend FRs but not Basic Structure)
1980 → Minerva Mills: HARMONY between FRs + DPSPs required
```

---

## 🎯 TONIGHT'S 30-MINUTE REVISION TASK

Write from memory (without looking at notes):

1. Draw a 4-node DLL diagram with pointers
2. State the correct termination condition for CLL traversal
3. Name 3 applications of CLL
4. Write the 3 categories of DPSPs with 2 examples each
5. State what Minerva Mills (1980) held
6. List the 5 Gandhian DPSPs by article number

---

*Day 23 Complete | Next: Day 24 — Trees (Binary Tree + Traversals) + Physics (Bernoulli's Principle)*
*Score Target Today: 22/25 CS + 22/25 GS = 44/50 minimum*
*Running Total Target: Days 22+23 combined = 88/100*
