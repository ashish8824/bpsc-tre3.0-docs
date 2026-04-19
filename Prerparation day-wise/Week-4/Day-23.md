# 📅 BPSC TRE 4.0 — DAY 23 COMPLETE STUDY MODULE
### Doubly Linked List & Circular Linked List + Indian Polity — DPSP
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): DLL & CLL — Concepts, Node Structure, Operations, Complexity
> - Afternoon (1 hr): Indian Polity — Directive Principles of State Policy (DPSP)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Doubly Linked List & Circular Linked List — Deep Conceptual Guide

---

## 🔷 SECTION 1: Recap — Why DLL Was Needed

### The Problem with Singly Linked List (SLL):
```
SLL limitation: You can ONLY go FORWARD.

SLL: HEAD --> [10|next-->] --> [20|next-->] --> [30|NULL]
                                   ↑
              If you are at node 20 and want to go BACK to node 10 → IMPOSSIBLE!
              You must restart from HEAD and traverse again → O(n) waste.

Real example:
  - Music player: going to PREVIOUS song
  - Browser: going BACK one page
  - Text editor: UNDO last action
  → All need backward movement → SLL is useless here!

SOLUTION → Doubly Linked List (DLL)
```

---

## 🔷 SECTION 2: Structure of a DLL Node

### The Three-Part Node:
```
A DLL node has THREE fields:

┌──────┬──────┬──────┐
│ PREV │ DATA │ NEXT │
│(addr)│(val) │(addr)│
└──────┴──────┴──────┘
   ↑               ↑
Points to       Points to
previous node   next node
(or NULL if     (or NULL if
 first node)     last node)
```

### In C++ Code:
```cpp
struct Node {
    int data;       // stores the value
    Node* prev;     // pointer to PREVIOUS node
    Node* next;     // pointer to NEXT node
};
```

### In Java Code:
```java
class Node {
    int data;
    Node prev;   // reference to previous node
    Node next;   // reference to next node
    
    Node(int val) {
        data = val;
        prev = null;
        next = null;
    }
}
```

### How a 3-Node DLL Looks:
```
NULL <-- [prev|10|next] <--> [prev|20|next] <--> [prev|30|next] --> NULL
              ↑                                          ↑
            HEAD                                        TAIL
            (first node:                          (last node:
             prev = NULL)                          next = NULL)

Detailed pointer view:
Node 1: prev=NULL,  data=10, next=Node2
Node 2: prev=Node1, data=20, next=Node3
Node 3: prev=Node2, data=30, next=NULL

↔ means BIDIRECTIONAL link (can go both ways!)
```

### Memory Overhead Comparison:
```
SLL node:  [data(4B) | next(8B)]         = 12 bytes per node
DLL node:  [prev(8B) | data(4B) | next(8B)] = 20 bytes per node
                ↑
        Extra 8 bytes per node for prev pointer — the PRICE of bidirectionality
```

### 🚨 PYQ TRAP #1: Memory Cost
> A DLL requires MORE memory per node than SLL because of the extra `prev` pointer.
> If SLL uses X bytes per node, DLL uses approximately X + pointer_size bytes.
> Pointer size = 4 bytes on 32-bit system, 8 bytes on 64-bit system.

---

## 🔷 SECTION 3: DLL Traversal — Forward and Backward

### Forward Traversal (HEAD to TAIL):
```
List: NULL <-- [10] <--> [20] <--> [30] --> NULL
HEAD points to [10]

Step 1: curr = HEAD  → print curr.data = 10 → curr = curr.next
Step 2: curr = [20]  → print curr.data = 20 → curr = curr.next
Step 3: curr = [30]  → print curr.data = 30 → curr = curr.next
Step 4: curr = NULL  → STOP

Output (forward): 10 → 20 → 30 → NULL
```

### Backward Traversal (TAIL to HEAD):
```
TAIL points to [30]

Step 1: curr = TAIL  → print curr.data = 30 → curr = curr.prev
Step 2: curr = [20]  → print curr.data = 20 → curr = curr.prev
Step 3: curr = [10]  → print curr.data = 10 → curr = curr.prev
Step 4: curr = NULL  → STOP

Output (backward): 30 → 20 → 10 → NULL

This is IMPOSSIBLE in SLL! DLL's key advantage.
```

**Time Complexity: O(n)** for both directions
**Space Complexity: O(1)**

---

## 🔷 SECTION 4: DLL — Insertion Operations

---

### ✅ INSERT AT BEGINNING — O(1)

**Before:** NULL ← [10] ↔ [20] ↔ [30] → NULL (HEAD = [10])
**Goal:** Insert 5 at beginning

```
Step 1: Create newNode = [NULL|5|NULL]

Step 2: Set newNode.next = HEAD
        newNode.next = [10]
        newNode: [NULL|5|-->10]

Step 3: Set HEAD.prev = newNode
        [10].prev = newNode
        newNode: [NULL|5|-->10]  ←→  [10]

Step 4: Update HEAD = newNode
        HEAD now points to [5]

RESULT:
NULL ← [5] ↔ [10] ↔ [20] ↔ [30] → NULL
         ↑
        HEAD
```

**Pointer Diagram:**
```
BEFORE:   HEAD
            |
            v
        [NULL|10|-->] <--> [<--|20|-->] <--> [<--|30|NULL]

STEP 2+3:
newNode   HEAD
  |         |
  v         v
[NULL|5|-->10] <--> [<--10|10|-->] (after setting [10].prev = newNode)
      ↓
    next = HEAD (old)

AFTER:  HEAD
          |
          v
      [NULL|5|-->] <--> [<--|10|-->] <--> [<--|20|-->] <--> [<--|30|NULL]
```

**Why O(1)?** Only pointer changes at HEAD — no traversal.

---

### ✅ INSERT AT END — O(1) WITH TAIL POINTER

**Before:** NULL ← [10] ↔ [20] ↔ [30] → NULL (TAIL = [30])
**Goal:** Insert 40 at end

```
Step 1: Create newNode = [NULL|40|NULL]

Step 2: Set newNode.prev = TAIL
        newNode: [<--30|40|NULL]

Step 3: Set TAIL.next = newNode
        [30].next = newNode

Step 4: Update TAIL = newNode

RESULT:
NULL ← [10] ↔ [20] ↔ [30] ↔ [40] → NULL
                                ↑
                              TAIL
```

**KEY ADVANTAGE over SLL:** In DLL with TAIL pointer, end insertion is O(1).
In SLL without tail pointer, end insertion is O(n).

---

### ✅ INSERT AT MIDDLE (After node with value k) — O(n)

**Goal:** Insert 25 between [20] and [30] in NULL ← [10] ↔ [20] ↔ [30] → NULL

```
Step 1: Traverse to find node with value 20 (= prevNode)
        nextNode = prevNode.next (= [30])

Step 2: Create newNode = [NULL|25|NULL]

Step 3: Connect all 4 pointers (in safe order):
        newNode.next = nextNode      → [25]-->[30]
        newNode.prev = prevNode      → [20]<--[25]
        prevNode.next = newNode      → [20]-->[25]
        nextNode.prev = newNode      → [25]<--[30]

RESULT:
NULL ← [10] ↔ [20] ↔ [25] ↔ [30] → NULL
```

**Pointer Update Diagram:**
```
BEFORE:
   prevNode              nextNode
      |                     |
     [20|-->]  --old link--> [<--|30]

STEP 3:
   prevNode   newNode    nextNode
      |          |           |
     [20|-->] → [<--|25|-->] → [<--|30]
      ↑                            ↑
  .next=newNode              .prev=newNode
```

### 🚨 PYQ TRAP #2: 4 Pointer Updates in DLL Middle Insertion
> Middle insertion in DLL requires **4 pointer updates** (compared to 2 in SLL):
> 1. newNode.next = nextNode
> 2. newNode.prev = prevNode
> 3. prevNode.next = newNode
> 4. nextNode.prev = newNode
> Missing any one of these will break the bidirectional links.

---

## 🔷 SECTION 5: DLL — Deletion Operations

---

### ✅ DELETE FROM BEGINNING — O(1)

**Before:** NULL ← [10] ↔ [20] ↔ [30] → NULL

```
Step 1: Check if HEAD == NULL (empty list)

Step 2: If only ONE node: HEAD = NULL, TAIL = NULL, done.

Step 3: Store: temp = HEAD (= [10])

Step 4: HEAD = HEAD.next  (HEAD now = [20])

Step 5: HEAD.prev = NULL  (sever backward link from [20] to [10])
        [20].prev = NULL

Step 6: Free temp (delete [10])

RESULT: NULL ← [20] ↔ [30] → NULL
```

**Why O(1)?** In DLL, HEAD.next gives us [20] directly, and [20].prev = NULL removes the backward link. No traversal needed.

---

### ✅ DELETE FROM END — O(1) WITH TAIL POINTER ← KEY ADVANTAGE OVER SLL!

**Before:** NULL ← [10] ↔ [20] ↔ [30] → NULL (TAIL = [30])

```
Step 1: Check if empty list

Step 2: If only ONE node: HEAD = NULL, TAIL = NULL, done.

Step 3: Store: temp = TAIL (= [30])

Step 4: TAIL = TAIL.prev  (TAIL now = [20])
        [20] has prev pointer → O(1) access!

Step 5: TAIL.next = NULL  (sever forward link from [20] to [30])

Step 6: Free temp (delete [30])

RESULT: NULL ← [10] ↔ [20] → NULL
```

### 🚨 PYQ TRAP #3: DLL vs SLL End Deletion
```
SLL end deletion: O(n) — must traverse to find second-to-last node
DLL end deletion: O(1) — TAIL.prev directly gives second-to-last node

This is the MOST IMPORTANT advantage of DLL over SLL!
Exams test this repeatedly.
```

---

### ✅ DELETE FROM GIVEN POSITION — O(n)

**Delete [20] from: NULL ← [10] ↔ [20] ↔ [30] → NULL**

```
Step 1: Traverse to find node with value 20 (= delNode)
        prevNode = delNode.prev (= [10])
        nextNode = delNode.next (= [30])

Step 2: Connect prevNode directly to nextNode:
        prevNode.next = nextNode  → [10] points to [30]
        nextNode.prev = prevNode  → [30] points back to [10]

Step 3: Free delNode (delete [20])

RESULT: NULL ← [10] ↔ [30] → NULL
```

**Pointer Diagram:**
```
BEFORE:
[10|-->] → [<--|20|-->] → [<--|30]
prevNode     delNode      nextNode

AFTER (prevNode.next = nextNode; nextNode.prev = prevNode):
[10|-->] → [<--|30]  (20 is deleted and freed)
```

**Why O(n)?** Must traverse to find the node to delete.
**BUT** once found, the actual deletion is O(1) — just 2 pointer updates.
**In SLL**, you also need to find the PREVIOUS node separately (extra traversal).
**In DLL**, the node itself has `.prev` — so deletion once found is easier.

---

## 🔷 SECTION 6: DLL Complete Complexity Table

| Operation | DLL Time | SLL Time | DLL Advantage? |
|-----------|----------|----------|----------------|
| Traversal (forward) | O(n) | O(n) | Same |
| Traversal (backward) | O(n) | NOT POSSIBLE | YES — DLL wins |
| Access by index | O(n) | O(n) | Same |
| Insert at BEGINNING | O(1) | O(1) | Same |
| Insert at END (with tail) | O(1) | O(1) | Same |
| Insert at END (no tail) | O(n) | O(n) | Same |
| Insert at MIDDLE | O(n) | O(n) | Same |
| Delete at BEGINNING | O(1) | O(1) | Same |
| Delete at END (with tail) | **O(1)** | **O(n)** | **YES — DLL wins!** |
| Delete at MIDDLE | O(n) | O(n) | Easier in DLL (has prev pointer) |
| Memory per node | MORE | LESS | SLL wins (less overhead) |

### Summary: When DLL beats SLL:
```
1. Backward traversal → Only DLL can do it
2. End deletion → O(1) in DLL, O(n) in SLL
3. Middle deletion → Simpler in DLL (no need to separately track prev)
4. Deque implementation → DLL enables O(1) at both ends
```

---

## 🔷 SECTION 7: Deque Using Doubly Linked List

### What is a Deque?
A **Deque (Double-Ended Queue)** allows insertion and deletion from **BOTH ends** in O(1).

```
DEQUE operations:
  addFront(x) → insert at beginning → O(1) in DLL
  addRear(x)  → insert at end       → O(1) in DLL (with tail pointer)
  removeFront()→ delete from beginning → O(1) in DLL
  removeRear() → delete from end    → O(1) in DLL (with tail pointer!)

Why DLL is perfect for Deque:
  HEAD pointer → O(1) access to front
  TAIL pointer → O(1) access to rear
  prev + next  → O(1) pointer updates in both directions

SLL CANNOT efficiently implement Deque:
  removeRear() in SLL = O(n) (must traverse to find second-to-last)
```

### 🚨 PYQ TRAP #4: Deque & DLL
> A Deque (Double-Ended Queue) is most efficiently implemented using a **Doubly Linked List**.
> All 4 deque operations (insert/delete at both ends) are O(1) with DLL + head + tail pointers.

---

## 🔷 SECTION 8: Circular Linked List (CLL)

### What is Circular Linked List?
A linked list where the **LAST node's NEXT pointer points back to the FIRST node** (HEAD), instead of NULL.

```
REGULAR SLL:
HEAD → [10|→] → [20|→] → [30|NULL]
                              ↑
                           dead end

CIRCULAR SLL:
HEAD → [10|→] → [20|→] → [30|→] ─────┐
  ↑                                    │
  └────────────────────────────────────┘
   last node's NEXT = HEAD (no NULL!)

Think of it as a RING or CIRCLE — no beginning, no end.
```

### Real-Life Analogy — Round-Robin Game:
```
Imagine children sitting in a circle playing a game:
- You start with Child 1
- Pass to Child 2, Child 3, ...
- After the LAST child, you're back to Child 1
- The game continues forever (no "end")

This is exactly Circular Linked List!
Used in:
  → CPU Round-Robin Scheduling (OS)
  → Circular Buffer / Ring Buffer
  → Multiplayer board games (players take turns)
  → Media player (repeat all)
```

---

## 🔷 SECTION 9: Circular Singly Linked List (CSLL) — Structure

```
CSLL with HEAD pointer:

HEAD
 |
 v
[10|→] → [20|→] → [30|→]
  ↑                    |
  └────────────────────┘
  last.next = HEAD

How to detect end during traversal:
  Instead of checking curr != NULL,
  Check curr.next != HEAD (stop when you've gone full circle)
  OR traverse while curr != HEAD
```

### CSLL Node (same as SLL node):
```cpp
struct Node {
    int data;
    Node* next;   // points to next node OR back to HEAD
};
```

---

## 🔷 SECTION 10: CSLL — Traversal

### Algorithm:
```
Step 1: Start at HEAD. Set curr = HEAD.
Step 2: Print curr.data
Step 3: curr = curr.next
Step 4: If curr == HEAD → STOP (full circle completed)
        Else → go to Step 2

For list [10 → 20 → 30 → back to 10]:
  curr = [10]: print 10, move to [20]
  curr = [20]: print 20, move to [30]
  curr = [30]: print 30, move to [10]
  curr = [10] == HEAD → STOP

Output: 10 → 20 → 30 → (back to 10)
```

### 🚨 PYQ TRAP #5: Infinite Loop in CLL
> If you traverse a Circular Linked List checking `curr != NULL` (instead of `curr != HEAD`),
> you will get an **INFINITE LOOP** because no node has NULL — last node points back to HEAD.
> Always use `curr != HEAD` as the termination condition.

---

## 🔷 SECTION 11: CSLL — Insertion

### Insert at Beginning — O(1):
```
List: [10] → [20] → [30] → back to [10]
HEAD points to [10]

Step 1: Find LAST node (traverse to where .next == HEAD)
        OR maintain a TAIL pointer → O(1)!
        
Step 2: Create newNode = [5|NULL]

Step 3: newNode.next = HEAD    → [5] points to [10]

Step 4: LAST.next = newNode    → [30] points to [5] (was pointing to [10])

Step 5: HEAD = newNode         → HEAD now points to [5]

RESULT: HEAD → [5] → [10] → [20] → [30] → back to [5]

WHY MAINTAIN TAIL POINTER?
  Without tail pointer → finding LAST node = O(n) traversal
  With tail pointer    → TAIL.next = newNode, then HEAD = newNode → O(1)!
```

### Insert at End — O(1) with TAIL pointer:
```
Step 1: newNode.next = HEAD    (new node points to first node)
Step 2: TAIL.next = newNode    (old last node points to new node)
Step 3: TAIL = newNode         (update tail)

RESULT: The circle now includes the new node as the last node.
```

---

## 🔷 SECTION 12: CSLL — Deletion

### Delete from Beginning — O(1):
```
Step 1: Find LAST node (TAIL) — has .next == HEAD
Step 2: TAIL.next = HEAD.next  (last node now points to second node)
Step 3: Free old HEAD node
Step 4: HEAD = HEAD.next       (update HEAD)

Special case: if only 1 node → HEAD = NULL, TAIL = NULL
```

### Delete from End — O(n) without tail tracking:
```
Step 1: Traverse to second-to-last node (curr.next.next == HEAD)
Step 2: curr.next = HEAD       (second-to-last now points to HEAD)
Step 3: Free old last node
Step 4: TAIL = curr            (update TAIL)
```

---

## 🔷 SECTION 13: Circular Doubly Linked List (CDLL)

### What is CDLL?
Combines properties of both DLL and CLL:
- Each node has `prev` and `next`
- Last node's NEXT = FIRST node (HEAD)
- First node's PREV = LAST node (TAIL)

```
CDLL Structure:
         ┌──────────────────────────────────┐
         ↓                                  |
HEAD → [<--|10|→] ↔ [<--|20|→] ↔ [<--|30|→]
         |                              ↑
         └──────────────────────────────┘
         
HEAD.prev = TAIL (last node)
TAIL.next = HEAD (first node)

Used in: Operating system process scheduling (circular queue of processes)
```

---

## 🔷 SECTION 14: Master Comparison — SLL vs DLL vs CLL

```
STRUCTURE COMPARISON:

SLL:   HEAD → [D|→] → [D|→] → [D|NULL]
DLL:   NULL←[←|D|→]↔[←|D|→]↔[←|D|→]→NULL
CSLL:  HEAD → [D|→] → [D|→] → [D|→] ─→ (back to HEAD)
CDLL:  HEAD ↔ [←|D|→] ↔ [←|D|→] ↔ [←|D|→] ↔ (circular)
```

### Master Comparison Table:

| Feature | SLL | DLL | CSLL | CDLL |
|---------|-----|-----|------|------|
| Pointers per node | 1 (next) | 2 (prev+next) | 1 (next) | 2 (prev+next) |
| NULL at end | YES | YES (both ends) | NO | NO |
| Forward traversal | YES | YES | YES | YES |
| Backward traversal | NO | YES | NO | YES |
| End deletion | O(n) | O(1) | O(n) | O(1) |
| Memory overhead | LOW | HIGH | LOW | HIGH |
| Complexity | Simple | Moderate | Moderate | Complex |
| Last node points to | NULL | NULL | HEAD | HEAD |
| Deque implementation | Poor | Excellent | Poor | Excellent |
| Use case | Simple lists | Music players, browsers, deque | Round-robin, scheduling | OS process scheduling |

### 🚨 PYQ TRAP #6: The Most-Tested Comparison Points
```
Q: Which linked list supports BACKWARD traversal?
A: DLL and CDLL

Q: Which linked list has NO NULL pointer?
A: CLL (Circular — both CSLL and CDLL)

Q: Which linked list allows O(1) deletion from BOTH ends?
A: DLL (with head + tail pointers) and CDLL

Q: Which linked list is used in round-robin CPU scheduling?
A: Circular Linked List (CSLL or CDLL)

Q: Which linked list is most MEMORY-EFFICIENT per node?
A: SLL (only one pointer per node)
```

---

## 🔷 SECTION 15: Advantages & Disadvantages Summary

### DLL Advantages:
```
1. BIDIRECTIONAL TRAVERSAL → Forward and backward
2. O(1) END DELETION       → TAIL.prev gives second-to-last instantly
3. EASIER DELETION         → Node has prev pointer — no separate tracking
4. DEQUE SUPPORT           → O(1) at both ends
5. UNDO/REDO               → Browser back-forward, text editor undo
```

### DLL Disadvantages:
```
1. EXTRA MEMORY            → One extra pointer per node
2. MORE COMPLEX CODE       → 4 pointer updates for middle insert/delete
3. MORE ERROR-PRONE        → Forgetting to update prev links → corruption
```

### CLL Advantages:
```
1. CIRCULAR ACCESS         → From any node, can reach any other node
2. EFFICIENT SCHEDULING    → Natural for round-robin (no "end" to reset)
3. NO NULL CHECK           → Traverse without NULL termination
4. EFFICIENT FOR CIRCULAR  → Buffer, ring buffer applications
```

### CLL Disadvantages:
```
1. INFINITE LOOP RISK      → If traversal condition wrong → infinite loop
2. COMPLEX INSERTION/DEL   → Must update last node's pointer carefully
3. NO CLEAR END            → Hard to determine where list ends
```

---

## 🔷 SECTION 16: Visual Summary — All Linked Lists

```
LINKED LIST FAMILY TREE:

                    LINKED LIST
                         |
          ┌──────────────┼───────────────┐
          |              |               |
        SINGLY        DOUBLY         CIRCULAR
       LINKED LIST   LINKED LIST    LINKED LIST
       [D|next]      [prev|D|next]     [D|next→HEAD]
          |              |               |
          |              |         ┌─────┴──────┐
          |              |         |            |
       Simple         Bidirectional  CSLL      CDLL
       One-way        Navigation   (singly)  (doubly)
       HEAD to NULL   HEAD↔TAIL    No NULL   No NULL
                                  Circular  Circular+Bidirectional
```

---

# PART 2: GENERAL STUDIES
## 📜 Indian Polity — Directive Principles of State Policy (DPSP)

---

## 🔷 SECTION 1: What are DPSP?

### Definition:
**Directive Principles of State Policy** are guidelines/instructions given to the **State** (government) to keep in mind while formulating laws and policies. They are contained in **Part IV, Articles 36–51** of the Indian Constitution.

### Origin:
```
DPSP are borrowed from the IRISH CONSTITUTION (Ireland's Constitution of 1937).
Ireland in turn borrowed it from the Spanish Constitution.

Influenced by: The UN Declaration of Human Rights (1948)
               Gandhian principles of social welfare
               Socialist ideology (Fabian Socialism)
```

### The Core Idea:
```
Fundamental Rights say:       "The State SHALL NOT..."
                               (negative duties — things State must NOT do)

DPSP say:                     "The State SHALL try to..."
                               (positive duties — things State SHOULD do)

Example:
  FR (Art. 19):  State SHALL NOT restrict freedom of speech unreasonably.
  DPSP (Art. 39): State SHALL try to ensure equal pay for equal work.
```

---

## 🔷 SECTION 2: Key Features of DPSP

### Feature 1 — NON-JUSTICIABLE:
```
DPSP are NOT enforceable by courts.
If the State ignores a DPSP, you CANNOT go to court against it.
(Unlike Fundamental Rights which are justiciable — courts can enforce them)

Why include non-enforceable principles?
→ Framers wanted ideals to guide governance without making ALL goals legally mandatory
→ Developing country: resources needed time to implement social goals
→ Acts as a MORAL and POLITICAL obligation on the State
```

### Feature 2 — FUNDAMENTAL IN GOVERNANCE:
```
Article 37 says DPSP are "fundamental in the governance of the country"
and "it shall be the duty of the State to apply these principles in making laws"

So while not legally enforceable, they are MORALLY binding.
The State is duty-bound to try to achieve them.
```

### Feature 3 — WELFARE STATE VISION:
```
DPSP represent India's commitment to building a WELFARE STATE —
a state that actively promotes social and economic well-being of its citizens.

Together with FRs, they form the CONSCIENCE of the Constitution.
```

### 🚨 PYQ TRAP #1: DPSP vs FR
> **DPSP = Non-justiciable** (cannot be enforced in courts)
> **Fundamental Rights = Justiciable** (enforceable in courts via Article 32/226)
> This is the single most tested difference between the two.

---

## 🔷 SECTION 3: DPSP Articles Overview (36–51)

| Article | Content |
|---------|---------|
| **36** | Definition of "State" (same as Article 12) |
| **37** | DPSP are non-justiciable but fundamental in governance |
| **38** | State to secure social order for welfare of people |
| **39** | Certain policy principles (equal pay, equal distribution of resources) |
| **39A** | Equal justice and free legal aid (added by 42nd Amendment, 1976) |
| **40** | Organisation of Village Panchayats |
| **41** | Right to work, education, public assistance in unemployment/illness |
| **42** | Provision for just and humane conditions of work + maternity relief |
| **43** | Living wage for workers |
| **43A** | Participation of workers in management of industries (42nd Amendment) |
| **43B** | Promotion of cooperative societies (97th Amendment, 2011) |
| **44** | Uniform Civil Code for citizens |
| **45** | Free and compulsory education for children (now shifted to FR via Art. 21A) |
| **46** | Promote educational and economic interests of SC/ST and weaker sections |
| **47** | Duty to raise nutrition, standard of living; prohibit liquor |
| **48** | Organisation of agriculture and animal husbandry; prohibit slaughter of cows |
| **48A** | Protection and improvement of environment and wildlife (42nd Amendment) |
| **49** | Protection of monuments, places and objects of national importance |
| **50** | Separation of judiciary from executive |
| **51** | Promotion of international peace and security |

---

## 🔷 SECTION 4: Classification of DPSP — 3 Categories

### Classification 1 — SOCIALIST PRINCIPLES (Economic/Social Justice):

```
These reflect SOCIALIST ideology — State should reduce inequality and ensure welfare:

Art. 38: Promote welfare, reduce inequalities of income, status, facilities
Art. 39(a): Equal right to livelihood for men and women
Art. 39(b): Material resources of community distributed for common good
Art. 39(c): Prevent concentration of wealth (prevent monopolies)
Art. 39(d): Equal pay for equal work for men and women
Art. 39(e): Protect health of workers (especially children)
Art. 39(f): Children given opportunities in healthy manner
Art. 39A: Free legal aid (added 42nd Amendment) → equal justice
Art. 41: Right to work, education, unemployment/sickness assistance
Art. 42: Just and humane work conditions + maternity relief
Art. 43: Living wage + decent standard of life for workers
Art. 43A: Workers' participation in management of industries
Art. 47: Improve nutrition, standard of living; ban intoxicating drinks
```

### Classification 2 — GANDHIAN PRINCIPLES:

```
Based on Gandhiji's vision of Gram Swaraj and village-centric India:

Art. 40: Organise VILLAGE PANCHAYATS (gram swaraj — most Gandhian!)
Art. 43: Promote cottage industries in rural areas
Art. 43B: Promotion of cooperative societies (97th Amendment, 2011)
Art. 46: Promote educational and economic interests of SC/ST/weaker sections
Art. 47: Prohibition of intoxicating drinks and drugs
Art. 48: Prohibit slaughter of COWS and CALVES; protect cattle
         Organise agriculture and animal husbandry on modern scientific lines
```

**Memory Trick for Gandhian Principles — "PPPCA":**
```
P = Panchayats (Art. 40)
P = Prohibition of liquor (Art. 47)
P = Prohibition of cow slaughter (Art. 48)
C = Cottage industries (Art. 43)
A = Advancement of SC/ST/weaker sections (Art. 46)
```

### Classification 3 — LIBERAL-INTELLECTUAL PRINCIPLES:

```
Based on liberal democracy and international vision:

Art. 44: UNIFORM CIVIL CODE — one law for all citizens regardless of religion
         (Highly debated — not implemented yet)
Art. 45: Free and compulsory education for children
         (Now a FR via 21A for ages 6-14; DPSP extends this vision)
Art. 48: Modernise agriculture and animal husbandry
Art. 48A: Protect and improve ENVIRONMENT and safeguard forests and wildlife
          (Added by 42nd Amendment, 1976)
Art. 49: Protect monuments and places of national/historical importance
Art. 50: SEPARATION OF JUDICIARY from EXECUTIVE in public services
Art. 51: Promote INTERNATIONAL PEACE and security
         Foster respect for international law and treaties
         Encourage settlement of disputes by arbitration
```

---

## 🔷 SECTION 5: DPSP Classification Visual Table

| Principle Type | Articles | Key Focus |
|---------------|----------|-----------|
| **Socialist** | 38, 39, 39A, 41, 42, 43, 43A, 47 | Economic equality, workers' welfare, legal aid |
| **Gandhian** | 40, 43, 43B, 46, 47, 48 | Village panchayats, cottage industry, cow protection, SC/ST welfare |
| **Liberal-Intellectual** | 44, 45, 48A, 49, 50, 51 | Uniform Civil Code, environment, judicial independence, world peace |

### 🚨 PYQ TRAP #2: Articles That Appear in Two Categories
> **Art. 43** (Living wage + cottage industries) = appears in both Socialist AND Gandhian
> **Art. 47** (Nutrition + prohibit liquor) = appears in both Socialist AND Gandhian
> Different textbooks classify these differently — be aware of both possibilities.

---

## 🔷 SECTION 6: Fundamental Rights vs DPSP — Master Comparison

| Feature | Fundamental Rights | DPSP |
|---------|-------------------|------|
| **Part of Constitution** | Part III (Art. 12–35) | Part IV (Art. 36–51) |
| **Nature** | Negative (restrict State) | Positive (guide State) |
| **Justiciability** | Justiciable (enforceable) | Non-justiciable (not enforceable) |
| **Effect if violated** | Courts can enforce | No court remedy |
| **Origin** | American Bill of Rights | Irish Constitution |
| **Focus** | Individual liberties | Social and economic welfare |
| **Priority** | Paramount law | Subordinate to FRs |
| **Amendment** | Amendable (but not basic structure) | Easily amended |
| **Enforcement by** | Article 32 (SC), Article 226 (HC) | No enforcement mechanism |
| **Whose duty** | State must NOT violate | State SHOULD implement |

### 🚨 PYQ TRAP #3: Conflict Between FR and DPSP
> **Historically:**
> - Initially, in **Champakam Dorairajan case (1951)**, SC held FR prevails over DPSP.
> - **42nd Amendment (1976)**: Added Art. 31C — laws implementing Art. 39(b) and 39(c) cannot be challenged on grounds of violating Art. 14 and 19.
> - **Minerva Mills case (1980)**: SC struck down part of 42nd Amendment; held FR and DPSP must be in HARMONY — neither can totally override the other.
> - **Current position**: DPSP and FRs must be read together (harmony approach).

---

## 🔷 SECTION 7: Important DPSP Articles — Exam Focus

### Article 39 — The Most Article-Rich DPSP:
```
39(a): Equal right to livelihood (men AND women)
39(b): Material resources = community owned, distributed for common good
39(c): Prevent concentration of wealth and means of production
39(d): Equal pay for equal work — men and women
39(e): Workers' health and strength not abused; children not forced into unsuitable work
39(f): Children given opportunities to develop in healthy manner (freedom, dignity)
```

### Article 44 — Uniform Civil Code (UCC):
```
Most controversial DPSP.
"State shall endeavour to secure for citizens a UNIFORM CIVIL CODE throughout India."

Currently: Personal laws (marriage, divorce, inheritance) differ by religion
           Hindu law, Muslim law (Shariat), Christian law, Parsi law

UCC would mean: ONE common code for ALL citizens regardless of religion
Status: Not implemented yet. Active political debate.
SC has repeatedly asked Parliament to consider it.

🚨 PYQ TRAP: UCC is a DPSP (Art. 44) — not a FR. 
             Courts CANNOT force the State to implement UCC.
```

### Article 48A — Environmental Protection:
```
"State shall endeavour to protect and improve the ENVIRONMENT
 and safeguard the forests and wildlife of the country."

Added by 42nd Constitutional Amendment, 1976
Related to: Article 51A(g) — Fundamental Duty to protect environment
The Forest Conservation Act and Wildlife Protection Act are inspired by this DPSP.
```

### Article 50 — Separation of Judiciary:
```
"State shall take steps to SEPARATE the JUDICIARY from the EXECUTIVE
 in the public services of the State."

This DPSP was partially implemented through:
- Criminal Procedure Code separating judicial magistrates from executive
- Creating independent judiciary at district level
```

### Article 51 — International Peace:
```
"State shall endeavour to:
 (a) Promote international peace and security
 (b) Maintain just and honourable relations between nations
 (c) Foster respect for international law and treaty obligations
 (d) Encourage settlement of international disputes by arbitration"

India's foreign policy (Panchsheel, NAM, SAARC) is inspired by Art. 51.
```

---

## 🔷 SECTION 8: Important Amendments Related to DPSP

| Amendment | Year | What was Added to DPSP |
|-----------|------|------------------------|
| **42nd Amendment** | 1976 | Art. 39A (free legal aid), Art. 43A (workers in management), Art. 48A (environment) |
| **44th Amendment** | 1978 | Art. 38(2) — minimize inequality of status, facilities, opportunities |
| **86th Amendment** | 2002 | Art. 45 modified — free education for children under 6 (above 6 = now Art. 21A FR) |
| **97th Amendment** | 2011 | Art. 43B added — promotion of cooperative societies |

### 🚨 PYQ TRAP #4: 42nd Amendment and DPSP
> The **42nd Amendment (1976)** is called the "Mini Constitution" because it made the most sweeping changes. For DPSP specifically, it added three new Articles: **39A, 43A, and 48A**.

---

## 🔷 SECTION 9: DPSP Quick Memory Tricks

### Key Article Numbers to Remember:
```
Art. 39(d) → Equal pay for equal work (most tested DPSP)
Art. 40    → Village Panchayats (most Gandhian)
Art. 44    → Uniform Civil Code (most controversial)
Art. 47    → Prohibit liquor + improve nutrition
Art. 48    → Cow protection (prohibit cow slaughter)
Art. 48A   → Environment protection (42nd Amendment)
Art. 50    → Separation of Judiciary from Executive
Art. 51    → International peace
```

### Memory Trick — "E-PEEL-S" for Categories:
```
E = Economic equality (Socialist: Art. 38, 39, 41–43)
P = Panchayats (Gandhian: Art. 40)
E = Equal pay (Socialist: Art. 39d)
E = Environment (Liberal: Art. 48A)
L = Legal aid (Socialist: Art. 39A)
S = Separation of judiciary (Liberal: Art. 50)
```

### "The 4 most exam-critical DPSPs":
```
1. Art. 39(d)  = Equal pay for equal work
2. Art. 44     = Uniform Civil Code
3. Art. 40     = Village Panchayats
4. Art. 48A    = Environmental protection
```

---

## 🔷 SECTION 10: DPSP Implementation — Real Laws Enacted

| DPSP Article | Law/Policy Enacted in Implementation |
|-------------|--------------------------------------|
| Art. 39A | Legal Services Authorities Act, 1987 |
| Art. 40 | Panchayati Raj institutions (73rd & 74th Amendments, 1992) |
| Art. 41 | MNREGA (Mahatma Gandhi National Rural Employment Guarantee Act, 2005) |
| Art. 42 | Maternity Benefit Act; Factories Act provisions |
| Art. 43 | Minimum Wages Act, 1948 |
| Art. 46 | Reservations for SC/ST; Scholarship schemes |
| Art. 47 | Prohibition laws in several states |
| Art. 48 | Prevention of Cruelty to Animals Act; state cow protection laws |
| Art. 48A | Forest Conservation Act; Wildlife Protection Act; Environment Protection Act |
| Art. 50 | CrPC provisions separating judicial and executive magistrates |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: DLL, CLL, Operations, Complexity, Deque, Comparisons

---

**Q1.** How many pointer fields does a Doubly Linked List node contain?
(A) 1 (only next)
(B) 2 (prev and next)
(C) 3 (prev, data pointer, and next)
(D) More than one of the above
(E) None of the above

---

**Q2.** In a Doubly Linked List, the FIRST node's `prev` pointer contains:
(A) Address of the last node
(B) Address of the second node
(C) NULL
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the time complexity of deleting the LAST node of a Doubly Linked List (with a tail pointer)?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q4.** Why is end-deletion O(1) in DLL but O(n) in SLL?
(A) DLL uses more memory, making operations faster
(B) DLL's last node has a `prev` pointer that directly gives access to the second-to-last node
(C) DLL nodes are stored in sorted order
(D) More than one of the above
(E) None of the above

---

**Q5.** How many pointer updates are required when inserting a node in the MIDDLE of a Doubly Linked List?
(A) 1
(B) 2
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q6.** Which linked list type is best suited for implementing a DEQUE (Double-Ended Queue) with O(1) operations at both ends?
(A) Singly Linked List
(B) Doubly Linked List
(C) Array
(D) More than one of the above
(E) None of the above

---

**Q7.** In a Circular Singly Linked List, the LAST node's `next` pointer points to:
(A) NULL
(B) The previous node
(C) The HEAD (first node)
(D) More than one of the above
(E) None of the above

---

**Q8.** What is the correct termination condition when traversing a Circular Linked List?
(A) curr != NULL
(B) curr.next != NULL
(C) curr != HEAD (or curr.next == HEAD for certain implementations)
(D) More than one of the above
(E) None of the above

---

**Q9.** Which application is most naturally implemented using a Circular Linked List?
(A) Stack
(B) Binary search
(C) Round-Robin CPU Scheduling
(D) More than one of the above
(E) None of the above

---

**Q10.** What happens if you traverse a Circular Linked List checking `curr != NULL` instead of `curr != HEAD`?
(A) The traversal stops immediately
(B) The traversal completes correctly
(C) The traversal enters an infinite loop
(D) More than one of the above
(E) None of the above

---

**Q11.** What is the main MEMORY disadvantage of a Doubly Linked List compared to a Singly Linked List?
(A) DLL requires twice the data storage
(B) DLL requires an extra pointer (prev) per node
(C) DLL cannot be stored in heap memory
(D) More than one of the above
(E) None of the above

---

**Q12.** Which linked list type supports BOTH forward and backward traversal?
(A) Singly Linked List
(B) Circular Singly Linked List
(C) Doubly Linked List
(D) More than one of the above
(E) None of the above

---

**Q13.** In a Doubly Linked List, the LAST node's `next` pointer contains:
(A) Address of the first node (HEAD)
(B) NULL
(C) Address of the second-to-last node
(D) More than one of the above
(E) None of the above

---

**Q14.** A Circular Doubly Linked List (CDLL) has the following property:
(A) The last node's next = NULL and first node's prev = NULL
(B) The last node's next = HEAD and first node's prev = TAIL
(C) All nodes point to the same address
(D) More than one of the above
(E) None of the above

---

**Q15.** Time complexity of inserting a node at the BEGINNING of a Doubly Linked List is:
(A) O(n)
(B) O(1)
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following correctly identifies a benefit of DLL over SLL for deletion?
(A) DLL uses less memory per node
(B) DLL allows O(1) deletion from end due to prev pointer
(C) DLL is faster because it stores elements in sorted order
(D) More than one of the above
(E) None of the above

---

**Q17.** In a Circular Singly Linked List, to efficiently insert at the BEGINNING in O(1), you should maintain:
(A) HEAD pointer only
(B) TAIL pointer (since TAIL.next = HEAD, and we only update TAIL.next)
(C) A sorted index
(D) More than one of the above
(E) None of the above

---

**Q18.** Which linked list does NOT have a NULL pointer in any of its nodes?
(A) Singly Linked List
(B) Doubly Linked List
(C) Circular Linked List
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is TRUE about Doubly Linked Lists?
(A) DLL cannot be used for stack implementation
(B) DLL allows traversal in both forward and reverse directions
(C) DLL access by index is O(1)
(D) More than one of the above
(E) None of the above

---

**Q20.** Music player "previous track" and "next track" functionality is best implemented using:
(A) Array
(B) Stack
(C) Doubly Linked List
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following statements about Circular Linked List is CORRECT?
(A) Traversal from any node can reach all other nodes
(B) It requires NULL check to detect end of list
(C) It is useful only when the list has exactly 2 nodes
(D) More than one of the above
(E) None of the above

---

**Q22.** A Deque implemented with Doubly Linked List supports which operations in O(1)?
(A) Insert at front only
(B) Delete from rear only
(C) Insert at front, Insert at rear, Delete from front, Delete from rear
(D) More than one of the above
(E) None of the above

---

**Q23.** In SLL, the time complexity for deleting a node when you have a pointer TO THAT NODE is:
(A) O(1) — just use the pointer
(B) O(n) — must traverse from HEAD to find previous node
(C) O(log n)
(D) More than one of the above
(E) None of the above

---

**Q24.** Which combination best describes the difference between SLL and DLL nodes?
(A) SLL: [data|next]; DLL: [prev|data|next]
(B) SLL: [prev|data]; DLL: [data|next]
(C) SLL and DLL have identical node structures
(D) More than one of the above
(E) None of the above

---

**Q25.** If a Singly Linked List has n nodes, which operation has DIFFERENT time complexity in a DLL?
(A) Traversal
(B) Search
(C) Deletion from end
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Indian Polity — Directive Principles of State Policy (DPSP)

---

**Q26.** Directive Principles of State Policy are contained in which Part of the Indian Constitution?
(A) Part II, Articles 5–11
(B) Part III, Articles 12–35
(C) Part IV, Articles 36–51
(D) More than one of the above
(E) None of the above

---

**Q27.** The concept of Directive Principles of State Policy was borrowed from the constitution of which country?
(A) USA
(B) Ireland
(C) UK
(D) More than one of the above
(E) None of the above

---

**Q28.** Which Article states that DPSP are "fundamental in governance" but not justiciable?
(A) Article 36
(B) Article 38
(C) Article 37
(D) More than one of the above
(E) None of the above

---

**Q29.** "Equal pay for equal work for men and women" is guaranteed under:
(A) Article 14 (Fundamental Right)
(B) Article 39(d) (Directive Principle)
(C) Article 15 (Fundamental Right)
(D) More than one of the above
(E) None of the above

---

**Q30.** Organisation of Village Panchayats is directed under which Article?
(A) Article 43
(B) Article 44
(C) Article 40
(D) More than one of the above
(E) None of the above

---

**Q31.** The Uniform Civil Code is mentioned in which Article of the Constitution?
(A) Article 40
(B) Article 51
(C) Article 44
(D) More than one of the above
(E) None of the above

---

**Q32.** Article 48A, which directs the State to protect the environment and wildlife, was added by:
(A) 44th Constitutional Amendment, 1978
(B) 42nd Constitutional Amendment, 1976
(C) 86th Constitutional Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q33.** Which of the following is a GANDHIAN Directive Principle?
(A) Uniform Civil Code (Article 44)
(B) International peace (Article 51)
(C) Prohibition of cow slaughter (Article 48)
(D) More than one of the above
(E) None of the above

---

**Q34.** Article 39A, which directs the State to provide free legal aid, was added by:
(A) 44th Amendment, 1978
(B) 42nd Amendment, 1976
(C) 86th Amendment, 2002
(D) More than one of the above
(E) None of the above

---

**Q35.** Which among the following is CORRECT regarding DPSP?
(A) DPSP are justiciable and enforceable by courts
(B) DPSP are non-justiciable but fundamental in governance
(C) DPSP can never be amended by Parliament
(D) More than one of the above
(E) None of the above

---

**Q36.** MNREGA (Mahatma Gandhi National Rural Employment Guarantee Act) was enacted to implement which DPSP?
(A) Article 40 — Village Panchayats
(B) Article 41 — Right to work
(C) Article 44 — Uniform Civil Code
(D) More than one of the above
(E) None of the above

---

**Q37.** Separation of Judiciary from the Executive is directed under which Article?
(A) Article 44
(B) Article 51
(C) Article 50
(D) More than one of the above
(E) None of the above

---

**Q38.** Which Article directs the State to promote international peace and security?
(A) Article 48
(B) Article 49
(C) Article 51
(D) More than one of the above
(E) None of the above

---

**Q39.** The Legal Services Authorities Act, 1987 was enacted to implement which DPSP Article?
(A) Article 39 (b)
(B) Article 43
(C) Article 39A
(D) More than one of the above
(E) None of the above

---

**Q40.** In the landmark Champakam Dorairajan case (1951), the Supreme Court held that:
(A) DPSP override Fundamental Rights
(B) Fundamental Rights prevail over DPSP
(C) Both are equally enforceable
(D) More than one of the above
(E) None of the above

---

**Q41.** The 97th Constitutional Amendment (2011) added which new DPSP Article?
(A) Article 43A — Workers in management
(B) Article 43B — Promotion of cooperative societies
(C) Article 48A — Environmental protection
(D) More than one of the above
(E) None of the above

---

**Q42.** Article 47 of the Constitution directs the State to:
(A) Provide free legal aid to citizens
(B) Raise nutrition levels, standard of living and prohibit intoxicating drinks
(C) Protect monuments and places of national importance
(D) More than one of the above
(E) None of the above

---

**Q43.** Which DPSP Article is directly related to the Minimum Wages Act, 1948?
(A) Article 39(d)
(B) Article 41
(C) Article 43
(D) More than one of the above
(E) None of the above

---

**Q44.** In the Minerva Mills case (1980), the Supreme Court held that:
(A) DPSP are superior to Fundamental Rights in all cases
(B) Parliament cannot amend Fundamental Rights at all
(C) Both FR and DPSP are necessary; neither can totally override the other
(D) More than one of the above
(E) None of the above

---

**Q45.** Article 43A, which directs workers' participation in management of industries, was added by:
(A) 44th Amendment, 1978
(B) 42nd Amendment, 1976
(C) 73rd Amendment, 1992
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following correctly classifies the DPSP as Socialist, Gandhian, and Liberal-Intellectual?
(A) Art. 40 = Socialist; Art. 44 = Gandhian; Art. 51 = Liberal-Intellectual
(B) Art. 40 = Gandhian; Art. 44 = Liberal-Intellectual; Art. 39 = Socialist
(C) Art. 40 = Liberal-Intellectual; Art. 39 = Gandhian; Art. 51 = Socialist
(D) More than one of the above
(E) None of the above

---

**Q47.** Article 49 of the Indian Constitution directs the State to:
(A) Promote international peace and security
(B) Protect monuments, places and objects of national and historical importance
(C) Separate judiciary from executive
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following DPSP has been given the status of a Fundamental Right through a Constitutional Amendment?
(A) Equal pay for equal work (Article 39d)
(B) Free and compulsory education (originally Article 45 — now Article 21A)
(C) Uniform Civil Code (Article 44)
(D) More than one of the above
(E) None of the above

---

**Q49.** The key difference between Fundamental Rights and DPSP is:
(A) FRs are in Part II; DPSP are in Part III
(B) FRs are justiciable; DPSP are non-justiciable
(C) FRs apply only to citizens; DPSP apply to all persons
(D) More than one of the above
(E) None of the above

---

**Q50.** Article 38 of the Constitution directs the State to:
(A) Provide free legal aid to weaker sections
(B) Secure a social order for the promotion of welfare of the people and minimise inequalities
(C) Organise cottage industries in rural areas
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
| 1 | (B) | DLL node: prev + next (2 pointers) |
| 2 | (C) | First node has no previous → prev = NULL |
| 3 | (C) | TAIL.prev gives second-to-last directly → O(1) |
| 4 | (B) | prev pointer gives direct access — no traversal needed |
| 5 | (C) | 4 updates: newNode.next, newNode.prev, prevNode.next, nextNode.prev |
| 6 | (B) | DLL with head+tail allows O(1) at both ends |
| 7 | (C) | CLL: last node.next = HEAD (no NULL!) |
| 8 | (C) | Stop when curr == HEAD (gone full circle) |
| 9 | (C) | Round-Robin Scheduling = circular, no end |
| 10 | (C) | No node has NULL → loop never terminates |
| 11 | (B) | Extra prev pointer = extra memory per node |
| 12 | (C) | DLL and CDLL both support bidirectional traversal |
| 13 | (B) | DLL last node: next = NULL |
| 14 | (B) | CDLL: TAIL.next = HEAD; HEAD.prev = TAIL |
| 15 | (B) | Just pointer changes at HEAD → O(1) |
| 16 | (B) | prev pointer → O(1) end deletion (vs O(n) in SLL) |
| 17 | (B) | TAIL.next = HEAD; update TAIL.next and HEAD for O(1) begin insert |
| 18 | (C) | Circular LL: no node is NULL (last points back to HEAD) |
| 19 | (B) | DLL: bidirectional traversal is its defining feature |
| 20 | (C) | DLL: prev = previous track, next = next track |
| 21 | (A) | From any node in CLL, full circle traversal reaches all nodes |
| 22 | (C) | All 4 Deque operations are O(1) with DLL + head + tail |
| 23 | (B) | SLL: need previous node to delete; must traverse to find it |
| 24 | (A) | SLL: [data|next]; DLL: [prev|data|next] |
| 25 | (C) | End deletion: O(n) in SLL, O(1) in DLL — the one key difference |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (C) | Part IV, Articles 36–51 |
| 27 | (B) | Borrowed from Irish Constitution (1937) |
| 28 | (C) | Article 37 states DPSP are non-justiciable but fundamental |
| 29 | (B) | Art. 39(d) — DPSP, not a Fundamental Right |
| 30 | (C) | Article 40 — Village Panchayats (most Gandhian) |
| 31 | (C) | Article 44 — Uniform Civil Code |
| 32 | (B) | 42nd Amendment, 1976 added Art. 48A |
| 33 | (C) | Art. 48 (cow slaughter prohibition) = Gandhian |
| 34 | (B) | 42nd Amendment, 1976 added Art. 39A |
| 35 | (B) | DPSP = non-justiciable but fundamental in governance |
| 36 | (B) | MNREGA implements Art. 41 — right to work |
| 37 | (C) | Article 50 — Separation of Judiciary from Executive |
| 38 | (C) | Article 51 — International peace and security |
| 39 | (C) | Legal Services Authorities Act → Art. 39A |
| 40 | (B) | Champakam case: FR prevails over DPSP |
| 41 | (B) | 97th Amendment added Art. 43B (cooperative societies) |
| 42 | (B) | Art. 47 — nutrition + standard of living + prohibit liquor |
| 43 | (C) | Art. 43 — living wage → Minimum Wages Act |
| 44 | (C) | Minerva Mills: harmony between FR and DPSP |
| 45 | (B) | 42nd Amendment, 1976 added Art. 43A |
| 46 | (B) | Art. 40=Gandhian; Art. 44=Liberal-Intellectual; Art. 39=Socialist |
| 47 | (B) | Art. 49 — protection of national monuments |
| 48 | (B) | Art. 45 (free education DPSP) → became Art. 21A FR (86th Amendment) |
| 49 | (B) | Justiciable vs Non-justiciable is the fundamental difference |
| 50 | (B) | Art. 38 — social order, welfare, minimise inequalities |

---
---

# 🔁 DAY 23 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — DLL & CLL

### DLL Node = [prev | data | next]
```
First node: prev = NULL
Last node:  next = NULL
Both ends have NULL (unlike CLL)
```

### Key Complexity Rules — DLL:
```
Operation                        | DLL   | SLL   | Winner
---------------------------------|-------|-------|--------
Traversal (forward)              | O(n)  | O(n)  | Tie
Traversal (backward)             | O(n)  | ❌     | DLL!
Insert at beginning              | O(1)  | O(1)  | Tie
Insert at end (with tail)        | O(1)  | O(1)  | Tie
Delete at beginning              | O(1)  | O(1)  | Tie
Delete at END (with tail)        | O(1)  | O(n)  | DLL WINS!
Middle insert pointer updates    | 4     | 2     | SLL simpler
Memory per node                  | MORE  | LESS  | SLL efficient
```

### DLL vs CLL — Key Differences:
```
DLL: NULL ← [prev|D|next] ↔ [prev|D|next] → NULL
     Has NULL at both ends
     Bidirectional but NOT circular

CLL: HEAD → [D|next] → [D|next] → [D|next] → (back to HEAD)
     NO NULL — last.next = HEAD
     Circular — no end; good for round-robin

CDLL: Combines both → bidirectional + circular
      HEAD ↔ [prev|D|next] ↔ ... ↔ [prev|D|next] ↔ (circular)
```

### Common PYQ Traps:
```
TRAP 1: DLL end deletion = O(1) (not O(n)) — because TAIL.prev exists
TRAP 2: DLL middle insert = 4 pointer updates (not 2 like SLL)
TRAP 3: CLL traversal ends at curr == HEAD (not curr == NULL)
TRAP 4: CLL has NO NULL pointer in any node
TRAP 5: Deque (O(1) both ends) needs DLL, not SLL
TRAP 6: Music player prev/next = DLL; game players turn = CLL
```

### SLL vs DLL vs CLL — One-Line Each:
```
SLL:  One pointer, one direction, simple but limited (O(n) end deletion)
DLL:  Two pointers, both directions, best for deque & O(1) end delete
CLL:  No NULL, circular, best for round-robin scheduling
CDLL: Circular + bidirectional, used in OS process scheduling
```

---

## ⚡ RAPID FIRE — DPSP

### Quick Identity:
```
Part IV, Articles 36–51
NON-JUSTICIABLE (courts cannot enforce)
Borrowed from: IRISH CONSTITUTION (1937)
Concept: Positive obligations on the State
Goal: Welfare State / Social & Economic democracy
```

### The 3 Categories + Key Articles:
```
SOCIALIST (Economic justice):
  39(a) = Right to livelihood (men + women)
  39(b) = Community ownership of material resources
  39(c) = Prevent concentration of wealth
  39(d) = EQUAL PAY FOR EQUAL WORK ← most tested!
  39A   = Free legal aid (42nd Amendment)
  41    = Right to work, education, public assistance
  42    = Humane work conditions + maternity relief
  43    = Living wage for workers
  43A   = Workers in management (42nd Amendment)
  47    = Nutrition + prohibit liquor

GANDHIAN (Village-centric India):
  40  = VILLAGE PANCHAYATS ← Gandhiji's gram swaraj
  43  = Cottage industries
  43B = Cooperative societies (97th Amendment)
  46  = Promote SC/ST/weaker sections
  47  = Prohibition of intoxicating drinks
  48  = COW PROTECTION + modern agriculture

LIBERAL-INTELLECTUAL (Rights & World Peace):
  44  = UNIFORM CIVIL CODE (most controversial)
  48A = ENVIRONMENT protection (42nd Amendment)
  49  = Protect national monuments
  50  = SEPARATION of Judiciary from Executive
  51  = INTERNATIONAL PEACE
```

### FR vs DPSP — One-Table Summary:
```
FRs: Part III | Art. 12–35 | Justiciable | Negative duties | American origin
DPSP: Part IV | Art. 36–51 | Non-justiciable | Positive duties | Irish origin
```

### Key Landmarks:
```
Champakam case (1951):  FR > DPSP (FR prevails in conflict)
42nd Amendment (1976):  Added Art. 39A, 43A, 48A to DPSP
Minerva Mills (1980):   Harmony — neither FR nor DPSP can completely override
44th Amendment (1978):  Added Art. 38(2) — minimise inequality
97th Amendment (2011):  Added Art. 43B — cooperative societies
86th Amendment (2002):  Art. 21A made education a FR; Art. 45 modified for under-6
```

### "4 Most Exam-Critical DPSP Articles":
```
Art. 39(d) = Equal pay for equal work
Art. 40    = Village Panchayats
Art. 44    = Uniform Civil Code
Art. 48A   = Environment protection
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. DLL node = [prev|data|next]; end deletion = O(1) because TAIL.prev gives second-to-last directly (key DLL advantage over SLL)
2. DLL middle insert needs 4 pointer updates; CLL traversal ends at curr == HEAD (not NULL — CLL has no NULL!)
3. Deque uses DLL: O(1) insert/delete at BOTH ends with head + tail pointers
4. DPSP = Part IV (Art. 36–51), non-justiciable, borrowed from Irish Constitution; FR = justiciable; Minerva Mills = harmony between both
5. Critical DPSP: Art. 39(d)=equal pay, Art. 40=Panchayats, Art. 44=UCC, Art. 48A=environment (42nd Amendment), Art. 50=Judiciary separation

---

*Next: Day 24 — Stack Data Structure (LIFO, Array & LL Implementation, Applications: Expression evaluation, Infix/Postfix) | GS: Indian Polity — Fundamental Duties & Amendment Procedure*
