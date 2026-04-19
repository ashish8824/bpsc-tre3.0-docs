# 📅 BPSC TRE 4.0 — DAY 22 COMPLETE STUDY MODULE
### Singly Linked List (SLL) + Indian Polity — Fundamental Rights
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Singly Linked List — Concepts, Node Structure, Operations, Complexity
> - Afternoon (1 hr): Indian Polity — Fundamental Rights (Articles 12–35)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Singly Linked List — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Linked List?

### Real-Life Analogy — The Treasure Hunt Chain:
Imagine a **treasure hunt game**:
- You start at **Clue #1** — it tells you something AND gives you the **location of Clue #2**
- Clue #2 tells you something AND gives you the **location of Clue #3**
- The last clue says: "No more clues ahead" (NULL)

This is exactly how a **Linked List** works!
- Each **clue = a node** (contains data + address of next node)
- The **starting point = HEAD pointer** (tells you where the list begins)
- "No more clues" = **NULL** (marks the end of the list)

```
Treasure Hunt Chain (Singly Linked List):

HEAD
 |
 v
[Data:10 | Next:-->] ---> [Data:20 | Next:-->] ---> [Data:30 | Next:NULL]
   Node 1                    Node 2                     Node 3 (last)
```

### Another Analogy — Railway Coaches:
```
Each coach has:
  - Passengers (DATA)
  - A coupling hook to the NEXT coach (POINTER/NEXT)
  - The last coach has no coupling hook attached (NULL)
  - The engine = HEAD (tells us where the train starts)

ENGINE(HEAD) ---> [Coach A | -->] ---> [Coach B | -->] ---> [Coach C | NULL]
```

### Formal Definition:
A **Linked List** is a **linear data structure** where elements (called **nodes**) are stored at **non-contiguous (random) memory locations**. Each node contains:
1. **Data** — the actual value stored
2. **Pointer (Next)** — the memory address of the NEXT node

---

## 🔷 SECTION 2: Structure of a Node — The Building Block

### What a Node Looks Like in Memory:

```
A Single Node:
+----------+----------+
|   DATA   |   NEXT   |
| (value)  |(address) |
+----------+----------+
    4 bytes   4/8 bytes
              (pointer)
```

### In C++ Code:
```cpp
struct Node {
    int data;       // stores the value
    Node* next;     // pointer to the next node
};
```

### In Java Code:
```java
class Node {
    int data;       // stores the value
    Node next;      // reference to next node
    
    Node(int val) {
        data = val;
        next = null;
    }
}
```

### How a 3-Node Linked List Looks in Memory:

```
Memory Address:   1000          2500          1800
                  +-----------+ +-----------+ +-----------+
                  | 10 | 2500 | | 20 | 1800 | | 30 | NULL |
                  +-----------+ +-----------+ +-----------+
                    Node 1         Node 2         Node 3
                      ^
                     HEAD = 1000

HEAD stores address 1000 (Node 1)
Node 1's NEXT stores 2500 (Node 2's address)
Node 2's NEXT stores 1800 (Node 3's address)
Node 3's NEXT stores NULL (end of list)

CRITICAL: Nodes are at RANDOM addresses (1000, 2500, 1800)
          NOT contiguous like arrays!
```

### 🚨 PYQ TRAP #1: Memory Allocation
> In a linked list, nodes are stored at **non-contiguous** (scattered/random) memory locations.
> This is the FUNDAMENTAL difference from arrays.
> Each node is dynamically allocated using `new` (C++) or `new` (Java) — heap memory.

---

## 🔷 SECTION 3: Types of Linked Lists — Brief Overview

### 1. Singly Linked List (SLL) — TODAY'S FOCUS
```
HEAD --> [10|-->] --> [20|-->] --> [30|NULL]
- Each node has ONE pointer (to next)
- Can traverse ONLY forward (left to right)
- Last node points to NULL
```

### 2. Doubly Linked List (DLL)
```
HEAD --> [NULL|10|-->] <--> [<--|20|-->] <--> [<--|30|NULL]
- Each node has TWO pointers (prev + next)
- Can traverse BOTH forward and backward
- More memory per node (extra pointer)
```

### 3. Circular Linked List
```
HEAD --> [10|-->] --> [20|-->] --> [30|-->] --+
           ^                                   |
           +-----------------------------------+
- Last node's NEXT points back to HEAD (not NULL)
- No NULL pointer
- Used in round-robin scheduling, circular queues
```

### Quick Comparison:
| Type | Pointers/Node | Direction | NULL at end |
|------|--------------|-----------|-------------|
| Singly (SLL) | 1 (next) | Forward only | YES |
| Doubly (DLL) | 2 (prev + next) | Both ways | YES (both ends) |
| Circular | 1 (next) | Forward (loops) | NO (points to HEAD) |

---

## 🔷 SECTION 4: Array vs Linked List — The Core Comparison

### Side-by-Side Memory Model:

```
ARRAY (Contiguous):
Address:  1000  1004  1008  1012  1016
         +----+----+----+----+----+
         | 10 | 20 | 30 | 40 | 50 |
         +----+----+----+----+----+
          All elements sit TOGETHER in memory

LINKED LIST (Non-Contiguous):
                    1800         3200         1000
                  +------+     +------+     +------+
                  |10|-->|---->|20|-->|---->|30|NULL|
                  +------+     +------+     +------+
          Nodes can be ANYWHERE in memory
```

### Master Comparison Table:

| Feature | Array | Singly Linked List |
|---------|-------|--------------------|
| Memory layout | Contiguous | Non-contiguous (scattered) |
| Access by index | O(1) — DIRECT | O(n) — must traverse from HEAD |
| Insertion at beginning | O(n) — shift all | O(1) — just change pointers |
| Insertion at end | O(1) — if space | O(n) — traverse to last node |
| Insertion at middle | O(n) — shift | O(n) — traverse to position |
| Deletion at beginning | O(n) — shift all | O(1) — move HEAD forward |
| Deletion at end | O(1) | O(n) — traverse to second-last |
| Deletion at middle | O(n) | O(n) — traverse to position |
| Memory per element | Only data | Data + pointer (overhead) |
| Size | Fixed (static) | Dynamic (grows/shrinks) |
| Cache performance | Excellent (spatial locality) | Poor (random memory) |
| Binary search | O(log n) possible | NOT efficient (no random access) |
| Reverse traversal | Easy (index--) | NOT possible in SLL |

### 🚨 PYQ TRAP #2: The Key Trade-off
> Array: FAST access (O(1)) but SLOW insertion/deletion at beginning (O(n))
> SLL: SLOW access (O(n)) but FAST insertion/deletion at beginning (O(1))
> This trade-off is the most tested comparison in exams.

---

## 🔷 SECTION 5: Traversal Operation

### What is Traversal?
Visiting every node in the linked list from HEAD to the last node (NULL).

### Step-by-Step Traversal:
```
List: HEAD --> [10|-->] --> [20|-->] --> [30|NULL]

Step 1: curr = HEAD (curr points to Node with 10)
        Print curr->data = 10
        curr = curr->next (move to Node with 20)

Step 2: curr points to Node with 20
        Print curr->data = 20
        curr = curr->next (move to Node with 30)

Step 3: curr points to Node with 30
        Print curr->data = 30
        curr = curr->next = NULL

Step 4: curr == NULL → STOP

Output: 10 → 20 → 30 → NULL
```

### Pointer Movement Diagram:
```
Pass 1:                Pass 2:               Pass 3:
curr                                          
 |                     curr                   
 v                      |                    curr
[10|-->]-->[20|-->]-->[30|NULL]               |
                                             [30|NULL]
print 10                print 20              print 30
```

### Code (Java):
```java
Node curr = head;
while (curr != null) {
    System.out.print(curr.data + " -> ");
    curr = curr.next;
}
System.out.println("NULL");
```

**Time Complexity: O(n)** — must visit all n nodes
**Space Complexity: O(1)** — only one `curr` pointer used

---

## 🔷 SECTION 6: Insertion Operations (Most Important for Exam)

---

### ✅ INSERTION AT BEGINNING — O(1)

This is the MOST important operation — it is O(1) unlike arrays!

**Before:**
```
HEAD --> [20|-->] --> [30|-->] --> [40|NULL]
```

**Goal: Insert 10 at beginning**

```
Step 1: Create a new node with data = 10
        newNode = new Node(10)
        newNode.next = NULL (initially)

        newNode: [10|NULL]

Step 2: Point newNode's NEXT to current HEAD
        newNode.next = HEAD
        
        newNode: [10|-->] --> [20|-->] --> [30|-->] --> [40|NULL]

Step 3: Update HEAD to point to newNode
        HEAD = newNode

        HEAD --> [10|-->] --> [20|-->] --> [30|-->] --> [40|NULL]
```

**Pointer Movement (Visual):**
```
BEFORE:    HEAD
            |
            v
           [20|-->] --> [30|-->] --> [40|NULL]

STEP 2:   newNode       HEAD
            |            |
            v            v
           [10|  ]      [20|-->] --> [30|-->] --> [40|NULL]
                |________|
          (newNode.next = HEAD)

AFTER:    HEAD
            |
            v
           [10|-->] --> [20|-->] --> [30|-->] --> [40|NULL]
```

**Why O(1)?** Only 2 pointer changes needed — regardless of list size!

---

### ✅ INSERTION AT END — O(n)

**Before:**
```
HEAD --> [10|-->] --> [20|-->] --> [30|NULL]
```

**Goal: Insert 40 at end**

```
Step 1: Create new node
        newNode = [40|NULL]

Step 2: Traverse to the LAST node
        curr = HEAD
        While curr.next != NULL:
            curr = curr.next
        (After loop, curr points to [30|NULL])

Step 3: Point last node's NEXT to newNode
        curr.next = newNode

AFTER:  HEAD --> [10|-->] --> [20|-->] --> [30|-->] --> [40|NULL]
```

**Pointer Movement:**
```
TRAVERSE:   curr starts at HEAD
            curr                curr               curr (LAST: next==NULL)
             |                   |                   |
            [10|-->] -->        [20|-->] -->        [30|NULL]
            
            Move curr forward until curr.next == NULL

ATTACH:     curr.next = newNode
            
            [30|-->] --> [40|NULL]
                   ^
                   curr
```

**Why O(n)?** Must traverse entire list to find the LAST node.

**Optimization:** Maintain a **TAIL pointer** → insertion at end becomes O(1)!

---

### ✅ INSERTION AT MIDDLE (at position k) — O(n)

**Goal: Insert 25 at position 2 in: HEAD --> [10|-->] --> [20|-->] --> [30|NULL]**

```
Step 1: Create newNode = [25|NULL]

Step 2: Traverse to node at position (k-1) — the node BEFORE insertion point
        curr = HEAD
        Move (k-1) = 1 times: curr now points to [10|-->]

Step 3: newNode.next = curr.next  (newNode points to what curr was pointing to)
        newNode: [25|-->] --> [20|-->] --> [30|NULL]

Step 4: curr.next = newNode       (previous node now points to newNode)
        [10|-->] --> [25|-->] --> [20|-->] --> [30|NULL]

RESULT: HEAD --> [10|-->] --> [25|-->] --> [20|-->] --> [30|NULL]
```

**⚠️ CRITICAL ORDER: Step 3 MUST come before Step 4!**
```
If you do Step 4 before Step 3:
curr.next = newNode   (now [10] points to [25])
newNode.next = curr.next   ← WRONG! curr.next is now newNode itself!
                             You create a circular reference and LOSE [20] and [30]!

ALWAYS: newNode.next = curr.next  FIRST
         curr.next = newNode       SECOND
```

### 🚨 PYQ TRAP #3: Order of Pointer Assignment
> When inserting in the middle, ALWAYS connect the new node to the NEXT node BEFORE disconnecting the previous node's link. Reversing this order causes data loss (the rest of the list is lost).

---

## 🔷 SECTION 7: Deletion Operations

---

### ✅ DELETION FROM BEGINNING — O(1)

**Before:** HEAD --> [10|-->] --> [20|-->] --> [30|NULL]

```
Step 1: Check if HEAD == NULL (empty list) → nothing to delete

Step 2: Store HEAD in a temp variable: temp = HEAD

Step 3: Move HEAD forward: HEAD = HEAD.next
        HEAD now points to [20|-->]

Step 4: Free temp (delete the old first node)
        free(temp) in C++ / garbage collected in Java

AFTER: HEAD --> [20|-->] --> [30|NULL]
```

**Why O(1)?** Just move HEAD one step forward — no traversal!

---

### ✅ DELETION FROM END — O(n)

**Before:** HEAD --> [10|-->] --> [20|-->] --> [30|NULL]

```
Step 1: Special case: if only ONE node (HEAD.next == NULL)
        HEAD = NULL → list is now empty

Step 2: Traverse to the SECOND-TO-LAST node
        curr = HEAD
        While curr.next.next != NULL:
            curr = curr.next
        (curr now points to [20|-->])

Step 3: Store the last node: temp = curr.next (= [30|NULL])

Step 4: Set curr.next = NULL
        [20|NULL] ← second-to-last becomes new last

Step 5: Free temp (delete [30])

AFTER: HEAD --> [10|-->] --> [20|NULL]
```

**Pointer Movement:**
```
FIND SECOND-TO-LAST:
        curr                curr (second-to-last: curr.next.next == NULL)
         |                   |
        [10|-->] -->        [20|-->] -->        [30|NULL]
                                                   ^
                                                  temp

SET NULL:   curr.next = NULL
            [20|NULL]  ← new last node
```

**Why O(n)?** Must traverse to the SECOND-TO-LAST node (can't go backwards in SLL!).

### 🚨 PYQ TRAP #4: Why O(n) for end deletion?
> In SLL, we cannot go BACKWARD. To delete the last node, we need to update the SECOND-TO-LAST node's pointer. To find it, we must traverse from HEAD. Hence O(n).
> In DLL (doubly linked list), last node has a `prev` pointer, so end deletion is O(1)!

---

### ✅ DELETION FROM GIVEN POSITION k — O(n)

**Delete node at position 2 from: HEAD --> [10|-->] --> [20|-->] --> [30|NULL]**

```
Step 1: Traverse to node at position (k-1) = position 1
        curr = HEAD (curr = [10|-->])

Step 2: Store node to delete: temp = curr.next (= [20|-->])

Step 3: Skip over it: curr.next = curr.next.next
        [10|-->] now points to [30|NULL]

Step 4: Free temp (delete [20|-->])

AFTER: HEAD --> [10|-->] --> [30|NULL]
```

**Visual:**
```
BEFORE:   HEAD --> [10|-->] --> [20|-->] --> [30|NULL]
                    curr         temp

SKIP:     curr.next = curr.next.next
          
AFTER:    HEAD --> [10|-->] --> [30|NULL]
                               ^
                         (temp [20] is freed)
```

---

## 🔷 SECTION 8: Complete Complexity Table — SLL

| Operation | Time Complexity | Space | Key Reason |
|-----------|----------------|-------|-----------|
| Traversal (visit all) | O(n) | O(1) | Visit all n nodes |
| Access by index | O(n) | O(1) | No random access — must traverse |
| Search | O(n) | O(1) | Linear scan only |
| Insert at BEGINNING | **O(1)** | O(1) | Only pointer changes — no traversal |
| Insert at END | O(n) | O(1) | Traverse to last node |
| Insert at END (with tail ptr) | **O(1)** | O(1) | Tail pointer gives direct access |
| Insert at MIDDLE (position k) | O(n) | O(1) | Traverse to position k-1 |
| Delete from BEGINNING | **O(1)** | O(1) | Just advance HEAD |
| Delete from END | O(n) | O(1) | Traverse to second-to-last |
| Delete from MIDDLE | O(n) | O(1) | Traverse to position k-1 |
| Find Length | O(n) | O(1) | Count all nodes |
| Reverse SLL | O(n) | O(1) | Visit each node once |

### 🚨 PYQ TRAP #5: The O(1) Exceptions in SLL
> The only O(1) operations in SLL are:
> 1. Insert at BEGINNING
> 2. Delete from BEGINNING
> 3. Insert at END — ONLY when a TAIL pointer is maintained
> Everything else is O(n) because we must traverse from HEAD.

---

## 🔷 SECTION 9: Dynamic Memory Allocation in Linked Lists

### What is Dynamic Allocation?
Memory is **allocated at runtime** (when the program runs), NOT at compile time.

```
Array: int arr[100];
       → 100 × 4 = 400 bytes reserved at COMPILE TIME
       → Even if you use only 3 elements, 400 bytes are occupied

Linked List: Node* newNode = new Node(10);
             → Memory allocated ONLY when you create a new node
             → Use 3 nodes? Only 3 nodes' worth of memory used
             → This is DYNAMIC allocation (from HEAP memory)
```

### Heap vs Stack:
```
STACK memory:    Local variables, function calls (auto-freed)
HEAP memory:     Dynamic allocation (new/malloc) — manual management

Linked List nodes live on the HEAP:
  C++:  Node* p = new Node(5);   // allocate
        delete p;                 // you must manually free!
  
  Java: Node p = new Node(5);    // allocate
        p = null;                 // garbage collector frees automatically
```

### 🚨 PYQ TRAP #6: Memory Leak
> In C++, if you delete a node from a linked list without calling `delete`, the memory remains allocated but unreachable — this is called a **MEMORY LEAK**.
> Java avoids this through automatic garbage collection.

---

## 🔷 SECTION 10: Advantages & Disadvantages of Singly Linked List

### Advantages:
```
1. DYNAMIC SIZE     → Can grow/shrink at runtime (no wasted memory)
2. O(1) INSERT/DEL  → At beginning: extremely fast (no shifting like arrays)
3. FLEXIBLE         → Easy to merge, split, or rearrange lists
4. MEMORY EFFICIENT → Use exactly as much memory as needed
5. BASIS for other  → Stacks, Queues, Graphs (adjacency list) built on it
```

### Disadvantages:
```
1. NO RANDOM ACCESS    → Cannot do arr[i]; must traverse from HEAD every time
2. EXTRA MEMORY        → Each node stores a pointer (4–8 extra bytes overhead)
3. POOR CACHE PERF     → Non-contiguous memory → frequent cache misses
4. NO BACKWARD TRAVEL  → SLL is one-directional; cannot go backwards
5. COMPLEX CODE        → Pointer manipulation is error-prone
6. NO BINARY SEARCH    → Without random access, binary search is inefficient
```

### Memory Overhead Calculation:
```
Array of 100 ints:
  100 × 4 = 400 bytes total

SLL of 100 ints (assuming 4-byte pointer):
  100 × (4 + 4) = 800 bytes total
  DOUBLE the memory for same data!

This overhead is the PRICE of dynamic sizing.
```

---

## 🔷 SECTION 11: SLL Mind Map — Visual Summary

```
                    SINGLY LINKED LIST
                           |
          ┌────────────────┼─────────────────┐
          |                |                 |
     NODE STRUCTURE    OPERATIONS       PROPERTIES
          |                |                 |
   [DATA | NEXT]      INSERT:           Dynamic size
          |           - Beginning O(1)  No random access
   HEAD pointer       - End O(n)        Memory overhead
   NULL = end         - Middle O(n)     Non-contiguous
                           |            Cache unfriendly
                      DELETE:
                      - Beginning O(1)       |
                      - End O(n)        VS ARRAY:
                      - Middle O(n)     Array: fast access
                           |            SLL: fast begin-insert
                      TRAVERSAL O(n)
                      SEARCH O(n)
                      ACCESS O(n)
```

---

# PART 2: GENERAL STUDIES
## ⚖️ Indian Polity — Fundamental Rights (Articles 12–35)

---

## 🔷 SECTION 1: What are Fundamental Rights?

### Definition:
**Fundamental Rights** are the basic rights guaranteed to every citizen of India by **Part III (Articles 12–35)** of the Indian Constitution. They are called "fundamental" because:
1. They are **essential** for the all-round development of individuals
2. They are **justiciable** — enforceable by courts (you can go to court if violated)
3. They are **supreme** — no law can take them away (only constitutional amendment can)

### Key Features:
```
1. JUSTICIABLE → Courts can enforce them (vs. Directive Principles which are non-justiciable)
2. NOT ABSOLUTE → Subject to reasonable restrictions by the State
3. SOME FOR ALL  → Some rights for all persons (citizens + foreigners)
4. SOME ONLY FOR CITIZENS → Like cultural rights, right to equality in employment
5. SUSPENDED DURING EMERGENCY → Article 352 emergency can suspend some rights
   Exception: Articles 20 and 21 CANNOT be suspended even during emergency
6. AMENDABLE → Parliament can amend but cannot destroy the BASIC STRUCTURE
```

### 🚨 PYQ TRAP #1: Justiciability
> **Fundamental Rights** = Justiciable (Part III, enforceable by courts)
> **Directive Principles of State Policy (DPSP)** = Non-justiciable (Part IV, guidelines for govt)
> This distinction is very frequently tested!

---

## 🔷 SECTION 2: Overview of Articles 12–35

### Article 12 — Definition of "State"
```
"State" includes:
  → Government of India (Central)
  → Parliament of India
  → State Governments
  → State Legislatures
  → Local/Statutory Authorities under State control

IMPORTANT: Fundamental Rights are against the STATE — not against private individuals.
(You can't sue a private person for violating your FR — only the State)
```

### Article 13 — Laws Inconsistent with FRs are Void
```
→ Any law that violates Fundamental Rights is VOID (invalid)
→ This gives courts power of JUDICIAL REVIEW
→ Pre-constitutional laws = void to the extent of inconsistency
→ "Law" here includes ordinances, orders, regulations, bye-laws
```

### 🚨 PYQ TRAP #2: Doctrine of Eclipse
> A pre-constitutional law that violates FR is not dead — it is merely "eclipsed" (shadowed). If the FR is later amended, the law revives. This is the **Doctrine of Eclipse**.

---

## 🔷 SECTION 3: The SIX Fundamental Rights — Detailed

---

### RIGHT 1: Right to Equality (Articles 14–18)

| Article | Content | Key Point |
|---------|---------|-----------|
| **14** | Equality before law and equal protection of laws | Two concepts: (1) Rule of Law (2) Equal protection |
| **15** | Prohibition of discrimination on grounds of religion, race, caste, sex, place of birth | State cannot discriminate; exceptions for women, children, SC/ST |
| **16** | Equality of opportunity in public employment | No discrimination in govt jobs; exceptions for reservations |
| **17** | Abolition of Untouchability | Made a PUNISHABLE OFFENCE |
| **18** | Abolition of Titles | State cannot confer titles (Bharat Ratna, Padma awards are NOT titles) |

**Article 14 — Two Key Concepts:**
```
Equality BEFORE law:   Everyone is equal in the eyes of law
                       (British concept — Rule of Law by Dicey)

Equal PROTECTION of law: Equals to be treated equally
                          Unequals CAN be treated differently
                          (American concept — allows reasonable classification)
```

**Article 15 — Exceptions (Protective Discrimination):**
```
Article 15(3): State CAN make special provisions for WOMEN and CHILDREN
Article 15(4): State CAN make special provisions for SC/ST/OBC (added by 1st Amendment 1951)
Article 15(5): State CAN reserve seats in private unaided educational institutions for SC/ST/OBC
               (added by 93rd Amendment 2005)
```

### 🚨 PYQ TRAP #3: Article 17
> Untouchability was ABOLISHED by Article 17. Practising untouchability is a punishable offence under the **Protection of Civil Rights Act, 1955** (earlier called Untouchability Offences Act).
> Article 17 applies to ALL persons — State AND private individuals (unique exception!)

---

### RIGHT 2: Right to Freedom (Articles 19–22)

| Article | Content |
|---------|---------|
| **19** | Six Freedoms (originally 7, now 6 after 44th Amendment) |
| **20** | Protection in respect of conviction for offences |
| **21** | Protection of life and personal liberty |
| **21A** | Right to Education (added by 86th Amendment, 2002) |
| **22** | Protection against arrest and detention |

**Article 19 — Six Freedoms:**
```
19(1)(a) → Freedom of SPEECH AND EXPRESSION
19(1)(b) → Freedom to ASSEMBLE peacefully without arms
19(1)(c) → Freedom to form ASSOCIATIONS and UNIONS
19(1)(d) → Freedom to MOVE FREELY throughout India
19(1)(e) → Freedom to RESIDE and SETTLE in any part of India
19(1)(g) → Freedom to PRACTISE any profession or trade/business

REMOVED: 19(1)(f) — Right to acquire, hold and dispose of PROPERTY
         (Removed by 44th Constitutional Amendment Act, 1978)
```

**Article 20 — Three Protections:**
```
20(1) → No EX-POST FACTO LAW
        Cannot be convicted for an act that was not a crime when committed

20(2) → No DOUBLE JEOPARDY
        Cannot be prosecuted twice for the same offence

20(3) → No SELF-INCRIMINATION
        Cannot be compelled to be a witness against yourself
        (Right to REMAIN SILENT — like US 5th Amendment)
```

**Article 21 — The Most Important Fundamental Right:**
```
"No person shall be deprived of his LIFE or PERSONAL LIBERTY
 except according to PROCEDURE ESTABLISHED BY LAW"

→ Interpreted VERY broadly by Supreme Court over decades
→ Has expanded to include: Right to livelihood, Right to privacy,
  Right to health, Right to education, Right to die with dignity,
  Right against solitary confinement, etc.

LANDMARK CASE: Maneka Gandhi v. Union of India (1978)
  The procedure must be "fair, just, and reasonable" (not merely any procedure)
```

**Article 21A — Right to Education:**
```
→ Added by 86th Constitutional Amendment, 2002
→ Free and compulsory education for children aged 6 to 14 years
→ Implemented through Right to Education (RTE) Act, 2009
```

**Article 22 — Protection from Arbitrary Arrest:**
```
On ARREST, a person has the right to:
  (a) Be informed of GROUNDS of arrest (immediately)
  (b) Consult and be defended by a LAWYER of choice
  (c) Be produced before a MAGISTRATE within 24 hours
  (d) Not be detained beyond 24 hours without magistrate's order

Exceptions: Preventive Detention laws (MISA, NSA, COFEPOSA, etc.)
```

### 🚨 PYQ TRAP #4: Articles 20 and 21 During Emergency
> Articles 20 and 21 CANNOT be suspended even during a National Emergency under Article 352.
> All other Fundamental Rights (including Article 19) can be suspended.
> This was reinforced by the 44th Constitutional Amendment, 1978 (after Emergency of 1975-77).

---

### RIGHT 3: Right against Exploitation (Articles 23–24)

| Article | Content | Key Point |
|---------|---------|-----------|
| **23** | Prohibition of human trafficking and forced labour (begar) | Includes bonded labour, child labour, trafficking |
| **24** | Prohibition of employment of children in factories and hazardous work | Children below 14 years cannot work in factories/mines |

```
Article 23: BEGAR (forced labour without payment) is prohibited
            Violation = punishable offence
            Applies to BOTH State and private individuals

Article 24: Children below 14 = CANNOT work in:
              → Factories
              → Mines
              → Other hazardous occupations
            CAN work in: non-hazardous jobs, family businesses, artistic work

IMPORTANT: Article 24 does NOT prohibit ALL child labour —
           only hazardous employment below age 14.
           The Child Labour (Prohibition & Regulation) Act, 1986 governs this.
```

### 🚨 PYQ TRAP #5: Begar vs. Bonded Labour
> **Begar** = forced labour WITHOUT payment (traditional form of exploitation)
> **Bonded labour** = working to pay off debt (also covered under Article 23)
> Both are prohibited. Bonded Labour System (Abolition) Act, 1976 was enacted under Article 23.

---

### RIGHT 4: Right to Freedom of Religion (Articles 25–28)

| Article | Content |
|---------|---------|
| **25** | Freedom of CONSCIENCE and right to PROFESS, PRACTISE, and PROPAGATE religion |
| **26** | Freedom to manage RELIGIOUS AFFAIRS and establish religious institutions |
| **27** | Freedom from paying taxes for promotion of any particular religion |
| **28** | Freedom from religious instruction in State-funded educational institutions |

```
Article 25 — For INDIVIDUALS (Personal Religious Freedom)
Article 26 — For RELIGIOUS DENOMINATIONS (Institutional Freedom)
             A religious denomination can:
             (a) Establish and maintain institutions
             (b) Manage its own religious affairs
             (c) Own and acquire property
             (d) Administer property according to law

Article 27 — State cannot FORCE you to pay tax that goes to promote a religion
Article 28 — Three types of educational institutions:
             Type 1: Wholly State-maintained → NO religious instruction at all
             Type 2: Administered by State but founded by endowment → CAN have religious instruction
             Type 3: Recognized by State but not funded → CAN have compulsory religious instruction
```

### 🚨 PYQ TRAP #6: Article 25 vs 26
> Article 25 is for INDIVIDUALS (right to personal religious practice)
> Article 26 is for RELIGIOUS DENOMINATIONS (institutions/groups)
> Both are subject to public order, morality, and health

---

### RIGHT 5: Cultural and Educational Rights (Articles 29–30)

| Article | Content |
|---------|---------|
| **29** | Protection of INTERESTS OF MINORITIES (language, script, culture) |
| **30** | Right of MINORITIES to establish and administer educational institutions |

```
Article 29:
→ Any section of citizens (not just religious minorities) with a DISTINCT
  language, script, or culture has the right to conserve it
→ No citizen can be denied admission to State-aided educational institutions
  on grounds of religion, race, caste, language

Article 30:
→ ALL minorities (religious OR linguistic) can:
  (a) Establish educational institutions
  (b) Administer them freely
→ State cannot discriminate against minority institutions in giving aid
→ LANDMARK: Minorities have absolute right to establish, but NOT absolute right to bad management
```

### 🚨 PYQ TRAP #7: Article 29 vs 30
> Article 29 is available to ALL citizens (any section with distinct culture)
> Article 30 is available ONLY to minorities (religious or linguistic)
> Note: Article 30 does NOT include the right to get government grants — just to establish and administer.

---

### RIGHT 6: Right to Constitutional Remedies (Article 32)

**This is called the "HEART and SOUL" of the Constitution — Dr. B.R. Ambedkar's words.**

```
Article 32 → Right to move the SUPREME COURT for enforcement of Fundamental Rights

Article 226 → Similar power of HIGH COURTS (but wider — can enforce ANY legal right)

Article 32 vs 226:
  Article 32: Only Supreme Court, only for FRs, itself a Fundamental Right
  Article 226: Any High Court, for FRs AND other legal rights, NOT a FR
```

### WRITS — The Five Weapons of Article 32:

| Writ | Meaning | Purpose |
|------|---------|---------|
| **Habeas Corpus** | "To have the body" | Release an illegally detained person |
| **Mandamus** | "We command" | Direct a public authority to perform its duty |
| **Prohibition** | "To forbid" | Prevent inferior court from exceeding jurisdiction |
| **Certiorari** | "To be certified" | Quash order of inferior court/tribunal |
| **Quo Warranto** | "By what authority" | Challenge a person's right to hold public office |

**Memory Trick for Writs — "H M P C Q":**
```
H = Habeas Corpus   (Free the body — personal liberty)
M = Mandamus        (Must do your duty)
P = Prohibition     (Prevent going beyond limits)
C = Certiorari      (Cancel a bad order)
Q = Quo Warranto   (Question authority to hold office)
```

### 🚨 PYQ TRAP #8: Article 32 during Emergency
> Article 32 can be SUSPENDED during a National Emergency (Article 359).
> BUT Article 20 and 21 cannot be suspended (44th Amendment).
> During suspension of Article 32, you CANNOT move Supreme Court for enforcement of FRs.
> However, you can still move HIGH COURT under Article 226 (since it's not suspended by Article 359).

---

## 🔷 SECTION 4: Important Miscellaneous Articles (12–35 Range)

| Article | Content | Exam Importance |
|---------|---------|----------------|
| **12** | Definition of State | HIGH |
| **13** | Pre-constitutional laws void if violating FR | HIGH |
| **17** | Abolition of Untouchability | VERY HIGH |
| **18** | Abolition of Titles | MEDIUM |
| **19(1)(a)** | Freedom of Speech & Expression | VERY HIGH |
| **20** | Protection against ex-post facto laws, double jeopardy, self-incrimination | VERY HIGH |
| **21** | Right to Life and Personal Liberty | HIGHEST |
| **21A** | Right to Education (added 2002) | VERY HIGH |
| **24** | No child labour in hazardous occupations (below 14) | HIGH |
| **25** | Freedom of religion (individual) | HIGH |
| **32** | Right to Constitutional Remedies | HIGHEST |
| **33** | Parliament can restrict FRs of Armed Forces | MEDIUM |
| **34** | FRs can be restricted during martial law | MEDIUM |
| **35** | Parliament has power to legislate on matters in Articles 16, 32, 33, 34 | LOW |

---

## 🔷 SECTION 5: Fundamental Rights — Quick Reference Summary

```
PART III: Articles 12 to 35
TOTAL FUNDAMENTAL RIGHTS: 6 (originally 7; Right to Property removed in 1978)

1. RIGHT TO EQUALITY          → Articles 14–18
2. RIGHT TO FREEDOM           → Articles 19–22
3. RIGHT AGAINST EXPLOITATION → Articles 23–24
4. RIGHT TO RELIGION          → Articles 25–28
5. CULTURAL & EDUCATIONAL     → Articles 29–30
6. RIGHT TO CONST. REMEDIES   → Article 32 (Articles 31A, 31B, 31C are exceptions)

REMOVED RIGHT:
   Right to PROPERTY (Article 31) → Removed by 44th Amendment Act, 1978
   Now a Legal Right under Article 300A (not a FR)
```

### Memory Trick — "E F E R C C":
```
E = Equality (14–18)
F = Freedom (19–22)
E = Exploitation prevention (23–24)
R = Religion (25–28)
C = Cultural & Educational (29–30)
C = Constitutional Remedies (32)
```

---

## 🔷 SECTION 6: Article 21 Expanded Rights (Supreme Court Interpretations)

Article 21 has been expanded by the Supreme Court to include:

```
Right to LIVELIHOOD (Olga Tellis case)
Right to PRIVACY (Puttaswamy case, 2017 — 9-judge bench)
Right to HEALTH and Medical Care
Right to EDUCATION (before 21A was added)
Right to CLEAN ENVIRONMENT
Right against SEXUAL HARASSMENT (Vishaka case — gave POSH guidelines)
Right to DIE WITH DIGNITY (Common Cause case)
Right against SOLITARY CONFINEMENT
Right to SPEEDY TRIAL
Right to LEGAL AID (Hussainara Khatoon case)
```

### 🚨 PYQ TRAP #9: Right to Privacy
> In **K.S. Puttaswamy v. Union of India (2017)**, a 9-judge Supreme Court bench unanimously declared **Right to Privacy** as a Fundamental Right under Article 21.
> This is a recent landmark judgment — high exam probability!

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Singly Linked List, Node Structure, Operations, Complexity, Array vs SLL

---

**Q1.** In a Singly Linked List, each node contains:
(A) Only data
(B) Data and pointer to previous node
(C) Data and pointer to next node
(D) More than one of the above
(E) None of the above

---

**Q2.** What does the HEAD pointer in a Singly Linked List point to?
(A) The last node
(B) The middle node
(C) The first node
(D) More than one of the above
(E) None of the above

---

**Q3.** In a Singly Linked List, the last node's NEXT pointer contains:
(A) Address of the first node
(B) Address of the head node
(C) NULL
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the time complexity of inserting a node at the BEGINNING of a Singly Linked List?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q5.** What is the time complexity of inserting a node at the END of a Singly Linked List (without tail pointer)?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the time complexity of ACCESSING the k-th element in a Singly Linked List?
(A) O(1)
(B) O(k) in worst case, which is O(n)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q7.** When inserting a new node at the MIDDLE of a Singly Linked List, what is the CORRECT order of pointer operations?
(A) First connect previous node to new node, then connect new node to next node
(B) First connect new node to next node, then connect previous node to new node
(C) The order doesn't matter
(D) More than one of the above
(E) None of the above

---

**Q8.** Why is deletion from the END of a Singly Linked List O(n)?
(A) Memory deallocation is time-consuming
(B) The second-to-last node must be found, requiring traversal from HEAD
(C) All nodes must be deleted and recreated
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the MAIN ADVANTAGE of Singly Linked List over Array?
(A) O(1) random access
(B) Better cache performance
(C) Dynamic size and O(1) insertion at beginning
(D) More than one of the above
(E) None of the above

---

**Q10.** Which memory is used for dynamic allocation of linked list nodes?
(A) Stack memory
(B) ROM
(C) Heap memory
(D) More than one of the above
(E) None of the above

---

**Q11.** In a Singly Linked List with n nodes, what is the time complexity of searching for a value?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the time complexity of deleting the FIRST node of a Singly Linked List?
(A) O(n)
(B) O(1)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following is NOT possible in a Singly Linked List (without modification)?
(A) Inserting a node at the beginning
(B) Traversing in reverse order
(C) Deleting the first node
(D) More than one of the above
(E) None of the above

---

**Q14.** A Singly Linked List with a tail pointer allows END insertion in:
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q15.** What happens if you incorrectly REVERSE the pointer assignment order during middle insertion in an SLL?
(A) Nothing — both orders work equally
(B) The insertion succeeds but traversal slows
(C) You lose the rest of the list (all nodes after insertion point)
(D) More than one of the above
(E) None of the above

---

**Q16.** In Singly Linked List, nodes are stored in:
(A) Contiguous memory locations
(B) Non-contiguous (random) memory locations
(C) Stack memory only
(D) More than one of the above
(E) None of the above

---

**Q17.** What additional memory overhead does each Singly Linked List node carry compared to an array element of the same data type?
(A) No additional memory
(B) Memory for one pointer (4 or 8 bytes)
(C) Memory for two pointers
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following structures uses Linked List internally?
(A) Hash table (chaining method)
(B) Stack (linked implementation)
(C) Queue (linked implementation)
(D) More than one of the above
(E) None of the above

---

**Q19.** What is the time complexity of finding the LENGTH of a Singly Linked List?
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q20.** What distinguishes a Circular Linked List from a Singly Linked List?
(A) Nodes have two pointers each
(B) The last node's NEXT points back to HEAD instead of NULL
(C) All nodes are stored contiguously
(D) More than one of the above
(E) None of the above

---

**Q21.** In C++, when you delete a node from a linked list without using `delete` keyword, the result is:
(A) Runtime error
(B) Compile error
(C) Memory leak
(D) More than one of the above
(E) None of the above

---

**Q22.** Binary Search is NOT efficient on a Singly Linked List because:
(A) Linked lists cannot store sorted data
(B) No random access — cannot jump to middle element directly
(C) Linked lists use too much memory for sorting
(D) More than one of the above
(E) None of the above

---

**Q23.** What is the correct code-level representation of a Singly Linked List node in C++?
(A) `struct Node { int data; Node* prev; Node* next; };`
(B) `struct Node { int data; Node* next; };`
(C) `struct Node { int data; int next; };`
(D) More than one of the above
(E) None of the above

---

**Q24.** The time complexity of REVERSING a Singly Linked List is:
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following correctly identifies an advantage of ARRAY over Singly Linked List?
(A) Array supports dynamic resizing
(B) Array provides O(1) access by index (random access)
(C) Array uses less memory per element when compared to SLL
(D) More than one of the above (B and C are both correct)
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Indian Polity — Fundamental Rights (Articles 12–35)

---

**Q26.** Fundamental Rights in the Indian Constitution are contained in:
(A) Part II, Articles 5–11
(B) Part III, Articles 12–35
(C) Part IV, Articles 36–51
(D) More than one of the above
(E) None of the above

---

**Q27.** Which article of the Indian Constitution defines the term "State" for the purpose of Fundamental Rights?
(A) Article 13
(B) Article 14
(C) Article 12
(D) More than one of the above
(E) None of the above

---

**Q28.** Article 14 of the Indian Constitution guarantees:
(A) Right to freedom of speech
(B) Equality before law and equal protection of laws
(C) Abolition of untouchability
(D) More than one of the above
(E) None of the above

---

**Q29.** Untouchability was abolished by which Article of the Indian Constitution?
(A) Article 14
(B) Article 16
(C) Article 17
(D) More than one of the above
(E) None of the above

---

**Q30.** How many Freedoms are currently guaranteed under Article 19(1) of the Indian Constitution?
(A) 7
(B) 4
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q31.** The Right to Property was removed as a Fundamental Right by which Constitutional Amendment?
(A) 42nd Amendment, 1976
(B) 44th Amendment, 1978
(C) 86th Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q32.** Article 21A, which guarantees the Right to Education, was added by:
(A) 73rd Constitutional Amendment
(B) 86th Constitutional Amendment, 2002
(C) 44th Constitutional Amendment, 1978
(D) More than one of the above
(E) None of the above

---

**Q33.** Which Articles of the Indian Constitution CANNOT be suspended even during a National Emergency?
(A) Articles 14 and 19
(B) Articles 19 and 21
(C) Articles 20 and 21
(D) More than one of the above
(E) None of the above

---

**Q34.** "No person shall be prosecuted and punished for the same offence more than once" — this principle is called:
(A) Ex-post facto law
(B) Double jeopardy
(C) Self-incrimination
(D) More than one of the above
(E) None of the above

---

**Q35.** Dr. B.R. Ambedkar described which Article as the "Heart and Soul" of the Constitution?
(A) Article 14
(B) Article 21
(C) Article 32
(D) More than one of the above
(E) None of the above

---

**Q36.** The writ of HABEAS CORPUS is issued to:
(A) Direct a public official to perform a duty
(B) Secure release of a person illegally detained
(C) Question a person's right to hold public office
(D) More than one of the above
(E) None of the above

---

**Q37.** Which writ literally means "What is your authority?" and is used to question the right to hold public office?
(A) Mandamus
(B) Certiorari
(C) Quo Warranto
(D) More than one of the above
(E) None of the above

---

**Q38.** Under Article 24, employment of children below what age in factories and hazardous occupations is prohibited?
(A) 12 years
(B) 16 years
(C) 14 years
(D) More than one of the above
(E) None of the above

---

**Q39.** The Right to Freedom of Religion under Article 25 includes the right to:
(A) Profess and practise religion only
(B) Profess, practise, and propagate religion
(C) Propagate religion using State funds
(D) More than one of the above
(E) None of the above

---

**Q40.** Article 32 gives citizens the right to approach which Court for enforcement of Fundamental Rights?
(A) District Court
(B) High Court
(C) Supreme Court
(D) More than one of the above
(E) None of the above

---

**Q41.** The Right to Privacy was declared a Fundamental Right under Article 21 in which landmark case?
(A) Maneka Gandhi v. Union of India (1978)
(B) Kesavananda Bharati v. State of Kerala (1973)
(C) K.S. Puttaswamy v. Union of India (2017)
(D) More than one of the above
(E) None of the above

---

**Q42.** Article 29 of the Indian Constitution protects the interests of:
(A) Religious minorities only
(B) Linguistic minorities only
(C) Any section of citizens having a distinct language, script, or culture
(D) More than one of the above
(E) None of the above

---

**Q43.** The writ of MANDAMUS is issued to:
(A) Release an illegally detained person
(B) Stop an inferior court from exceeding its jurisdiction
(C) Direct a public authority to perform its legal duty
(D) More than one of the above
(E) None of the above

---

**Q44.** Article 30 grants which right to minorities?
(A) Right to vote in elections
(B) Right to establish and administer educational institutions
(C) Right to receive mandatory government grants
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following is NOT a Fundamental Right in the Indian Constitution?
(A) Right to Equality (Article 14)
(B) Right against Exploitation (Article 23)
(C) Right to Property
(D) More than one of the above
(E) None of the above

---

**Q46.** The protection against Ex-Post Facto laws, Double Jeopardy, and Self-Incrimination is guaranteed by:
(A) Article 19
(B) Article 22
(C) Article 20
(D) More than one of the above
(E) None of the above

---

**Q47.** High Courts can issue writs under which Article of the Constitution?
(A) Article 32
(B) Article 226
(C) Article 142
(D) More than one of the above
(E) None of the above

---

**Q48.** The "Doctrine of Eclipse" in Constitutional Law means:
(A) Fundamental Rights can be permanently removed by Parliament
(B) A pre-constitutional law violating FR is dormant but revives if FR is amended
(C) Courts can eclipse Parliament's power to amend the Constitution
(D) More than one of the above
(E) None of the above

---

**Q49.** Which Article prohibits the State from levying taxes for promotion of any particular religion?
(A) Article 25
(B) Article 28
(C) Article 27
(D) More than one of the above
(E) None of the above

---

**Q50.** Article 19(1)(f) — Freedom to acquire, hold, and dispose of property — was removed by:
(A) 42nd Constitutional Amendment, 1976
(B) 44th Constitutional Amendment, 1978
(C) 24th Constitutional Amendment, 1971
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
| 1 | (C) | Node = data + pointer to NEXT node |
| 2 | (C) | HEAD always points to first node |
| 3 | (C) | Last node's NEXT = NULL (end marker) |
| 4 | (C) | Insert at beginning = O(1) — only pointer changes |
| 5 | (C) | Must traverse to last node → O(n) |
| 6 | (B) | No random access; must traverse from HEAD |
| 7 | (B) | newNode.next = next node FIRST; then prev.next = newNode |
| 8 | (B) | SLL is one-directional; must find second-to-last node |
| 9 | (C) | Dynamic size + O(1) beginning insertion |
| 10 | (C) | Dynamic allocation uses HEAP memory |
| 11 | (C) | Linear scan from HEAD → O(n) |
| 12 | (B) | Just move HEAD forward → O(1) |
| 13 | (B) | Reverse traversal not possible in SLL (no prev pointer) |
| 14 | (C) | Tail pointer gives direct end access → O(1) |
| 15 | (C) | Wrong order breaks chain → lose rest of list |
| 16 | (B) | Non-contiguous (random) memory locations |
| 17 | (B) | One pointer per node = 4 or 8 extra bytes |
| 18 | (D) | Hash chaining + linked stack + linked queue — all use LL |
| 19 | (C) | Count all nodes = O(n) |
| 20 | (B) | Last node's NEXT points to HEAD (not NULL) |
| 21 | (C) | Memory leak — allocated memory not freed |
| 22 | (B) | No random access → cannot jump to middle |
| 23 | (B) | `struct Node { int data; Node* next; }` |
| 24 | (C) | Must visit each node once → O(n) |
| 25 | (D) | Both O(1) access AND less memory per element are advantages |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Part III, Articles 12–35 |
| 27 | (C) | Article 12 defines "State" |
| 28 | (B) | Article 14 = Equality before law + equal protection |
| 29 | (C) | Article 17 abolishes untouchability |
| 30 | (C) | 6 freedoms (Article 19(1)(f) removed in 1978) |
| 31 | (B) | 44th Amendment, 1978 removed property as FR |
| 32 | (B) | 86th Amendment, 2002 added Article 21A |
| 33 | (C) | Articles 20 and 21 — cannot be suspended even during emergency |
| 34 | (B) | Double jeopardy — Article 20(2) |
| 35 | (C) | Article 32 — "Heart and Soul" per Ambedkar |
| 36 | (B) | Habeas Corpus = release of illegally detained person |
| 37 | (C) | Quo Warranto = challenge to public office authority |
| 38 | (C) | Article 24 — below 14 years |
| 39 | (B) | Article 25 — profess, practise, AND propagate |
| 40 | (C) | Article 32 → Supreme Court |
| 41 | (C) | K.S. Puttaswamy v. Union of India (2017) |
| 42 | (C) | Any section of citizens (not just minorities) |
| 43 | (C) | Mandamus = direct public authority to perform duty |
| 44 | (B) | Article 30 = establish and administer educational institutions |
| 45 | (C) | Right to Property was removed as FR in 1978 |
| 46 | (C) | Article 20 — three protections |
| 47 | (B) | Article 226 — High Courts |
| 48 | (B) | Dormant law revives if FR is subsequently amended |
| 49 | (C) | Article 27 — no tax for religion promotion |
| 50 | (B) | 44th Constitutional Amendment, 1978 |

---
---

# 🔁 DAY 22 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Singly Linked List

### Core One-Liners:
1. **Node Structure** = Data + Pointer to NEXT node (two fields)
2. **HEAD** = pointer to first node; **NULL** = marks end of list
3. **Non-contiguous memory** = nodes scattered in RAM (key difference from array)
4. **Insert at beginning = O(1)** — only 2 pointer changes, NO traversal
5. **Insert at end = O(n)** — must find last node by traversal
6. **Delete at beginning = O(1)** — just advance HEAD
7. **Delete at end = O(n)** — must find SECOND-TO-LAST node
8. **Access/Search = O(n)** — no random access; must traverse from HEAD
9. **Middle insertion order**: newNode.next = next FIRST, then prev.next = newNode (CRITICAL!)
10. **Memory leak** = in C++, forgetting to `delete` a removed node

### Complexity Cheat Sheet:
```
Operation                    | Time  | Key Reason
-----------------------------|-------|----------------------------------
Access by index              | O(n)  | No random access; traverse needed
Search                       | O(n)  | Linear scan from HEAD
Insert at BEGINNING          | O(1)  | Just 2 pointer changes
Insert at END (no tail ptr)  | O(n)  | Traverse to last node
Insert at END (with tail ptr)| O(1)  | Direct access via tail
Insert at MIDDLE             | O(n)  | Traverse to position k-1
Delete at BEGINNING          | O(1)  | Advance HEAD
Delete at END                | O(n)  | Traverse to second-to-last
Delete at MIDDLE             | O(n)  | Traverse to position k-1
Traversal                    | O(n)  | Visit all n nodes
Reversal                     | O(n)  | Visit all n nodes
```

### SLL vs Array — 3-Line Summary:
```
Array:  FAST access O(1), SLOW begin-insert O(n), FIXED size, CONTIGUOUS memory
SLL:    SLOW access O(n), FAST begin-insert O(1), DYNAMIC size, NON-CONTIGUOUS memory
DLL:    Like SLL but can traverse BOTH ways (needs 2 pointers; O(1) end deletion)
```

### Types of Linked Lists:
```
SLL:      [data|next] → [data|next] → [data|NULL]
DLL:      NULL←[prev|data|next] ↔ [prev|data|next]→NULL
Circular: [data|next] → [data|next] → [data|next] → (back to HEAD)
```

---

## ⚡ RAPID FIRE — Fundamental Rights

### The 6 Fundamental Rights + Articles:
```
1. Right to EQUALITY         → Articles 14–18
2. Right to FREEDOM          → Articles 19–22
3. Right AGAINST EXPLOITATION→ Articles 23–24
4. Right to RELIGION         → Articles 25–28
5. CULTURAL & EDUCATIONAL    → Articles 29–30
6. RIGHT TO CONST. REMEDIES  → Article 32
```

### Must-Know Articles:
```
Art. 12:  Definition of "State" (FRs apply against State)
Art. 13:  Laws violating FRs = VOID (Judicial Review)
Art. 14:  Equality before law + equal protection
Art. 17:  Abolition of untouchability (PUNISHABLE offence)
Art. 19:  6 freedoms (speech, assembly, association, movement, residence, profession)
Art. 20:  Ex-post facto, Double Jeopardy, Self-incrimination protection
Art. 21:  Life + Personal Liberty (most expansive FR)
Art. 21A: Free education 6–14 years (86th Amendment, 2002)
Art. 22:  Protection from arbitrary arrest (produce before magistrate within 24 hrs)
Art. 23:  No begar/forced labour
Art. 24:  No child labour below 14 in hazardous jobs
Art. 25:  Freedom of religion (profess, practise, propagate)
Art. 26:  Religious denomination rights
Art. 27:  No tax for religion promotion
Art. 29:  Minority culture protection
Art. 30:  Minorities can establish & administer educational institutions
Art. 32:  "Heart & Soul" — remedies via Supreme Court; 5 writs
```

### The 5 Writs (HMPCQ):
```
H = Habeas Corpus  → Illegal detention → Release the body
M = Mandamus       → Public duty not done → Do your duty
P = Prohibition    → Inferior court exceeding jurisdiction → Stop!
C = Certiorari     → Bad order by inferior court → Quash the order
Q = Quo Warranto  → Illegal occupancy of public office → By what authority?
```

### Critical Emergency Facts:
```
Articles 20 & 21 → CANNOT be suspended even during National Emergency (44th Amendment)
Article 19 freedoms → CAN be suspended during National Emergency
Article 32 → CAN be suspended under Article 359 (President's order)
But Article 226 (HC writs) → CANNOT be suspended
```

### PYQ Traps — One-Line Reminders:
```
FR vs DPSP: FR = justiciable; DPSP = non-justiciable
Right to Property: Removed as FR by 44th Amendment 1978 → now Article 300A (legal right)
Article 21A: 86th Amendment 2002 → RTE Act 2009 → ages 6–14
Art. 17 is unique: applies to PRIVATE individuals too (not just State)
Right to Privacy: Declared FR under Art. 21 in Puttaswamy case (2017)
Art. 32 vs Art. 226: SC can only enforce FRs; HC can enforce FRs + other rights
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. SLL node = Data + Next pointer; HEAD = first node; NULL = end; memory is NON-CONTIGUOUS
2. Insert/Delete at BEGINNING = O(1) in SLL (key advantage over arrays); everything else = O(n)
3. Middle insertion: ALWAYS connect newNode.next first, then previous.next = newNode (wrong order = data loss)
4. Fundamental Rights = Part III, Articles 12–35; 6 rights; justiciable; Articles 20 & 21 cannot be suspended even in emergency
5. Article 32 = "Heart and Soul" (Ambedkar); 5 writs = Habeas Corpus, Mandamus, Prohibition, Certiorari, Quo Warranto

---

*Next: Day 23 — Doubly Linked List + Stacks (LIFO, Operations, Applications using Arrays & LL) | GS: Indian Polity — Directive Principles & Fundamental Duties*
