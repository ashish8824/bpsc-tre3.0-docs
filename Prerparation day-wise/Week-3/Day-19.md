# 📅 BPSC TRE 4.0 — DAY 19 COMPLETE STUDY MODULE
### Circular Queue & Deque + India Climate — Monsoon System
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Circular Queue (why needed, conditions, dry run) + Deque (types, operations)
> - Afternoon (1 hr): India Climate — Monsoon System
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Circular Queue & Deque — Deep Conceptual Guide

---

## 🔷 SECTION 1: Recap — The Problem with Linear Queue

### Why Does the Problem Exist?
```
LINEAR QUEUE of size 5: MAX = 5 (indices 0–4)

After: ENQUEUE 10,20,30,40,50 → then DEQUEUE 3 times:

Index:  [0]   [1]   [2]   [3]   [4]
        [ _  |  _  |  _  | 40  | 50 ]
                              ↑f        ↑r
         ^     ^     ^
     WASTED  WASTED  WASTED   (3 dequeues freed these slots)

front=3, rear=4

Now try ENQUEUE 60:
  rear == 4 == MAX-1 → "OVERFLOW!" reported
  But 3 slots (indices 0,1,2) are EMPTY and unused!

This is called FALSE OVERFLOW.
The linear queue does NOT recycle those freed positions.
```

### The Solution: Circular Queue
```
In a CIRCULAR QUEUE:
  → After index [4], the NEXT position wraps to index [0]
  → Think of the array as a CIRCLE, not a straight line
  → rear = (rear + 1) % SIZE    ← circular increment
  → front = (front + 1) % SIZE  ← circular increment
  → No memory is ever permanently wasted!
```

---

## 🔷 SECTION 2: What is a Circular Queue?

### Real-Life Analogy — The Revolving Door / Merry-Go-Round:
```
Think of a MERRY-GO-ROUND with 5 seats (numbered 0–4):

       [0]
   [4]     [1]
   [3]     [2]
        ↑
   Seats wrap around — after seat 4, next is seat 0 again!

In a circular queue:
  → People sit from rear
  → People exit from front
  → After the last seat, the next seat wraps to the first
  → No seat is permanently lost!
```

### Another Analogy — Circular Buffer in Computers:
```
Audio streaming buffer, keyboard input buffer, network packet buffer:
  → Data arrives at one end (rear), consumed from other (front)
  → Once the last slot is used, new data wraps to the first slot
    (if that slot has been consumed/freed already)
  → This is exactly Circular Queue = Ring Buffer

CIRCULAR QUEUE = RING BUFFER (alternate name — very important!)
```

### Formal Definition:
A **Circular Queue** is a linear data structure that follows FIFO principle, but the **last position is connected to the first position** to form a circle, eliminating the false overflow problem of linear queues.

---

## 🔷 SECTION 3: Circular Queue — Key Conditions

### This section contains the MOST tested formulas. Memorize them perfectly.

```
Let SIZE = total capacity of circular queue (e.g., 5)
Indices run from 0 to SIZE-1

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONDITION         FORMULA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Empty             front == -1  (before first enqueue)
                  OR front == rear (after last dequeue in some implementations)
Full              (rear + 1) % SIZE == front
Next REAR index   rear = (rear + 1) % SIZE
Next FRONT index  front = (front + 1) % SIZE
Number of         (rear - front + SIZE) % SIZE   (when NOT empty)
  elements
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Why (rear + 1) % SIZE == front means FULL?
```
Circular queue of SIZE = 5 (indices 0,1,2,3,4)

Scenario: front=1, rear=0
           ↓        ↓
  [ 20 | 30 | 40 | 50 |  ? ]
    [1]  [2]  [3]  [4]  [0]
         ↑f                ↑r

  Can we insert at rear's next position?
  (rear+1)%SIZE = (0+1)%5 = 1 = front position!
  That position already has data (index 1 = value 20)!
  → Queue IS FULL → we CANNOT insert

  If we insert anyway, we'd OVERWRITE front's data → data loss!
  So: (rear+1)%SIZE == front → FULL → STOP

NOTE: In this implementation, 1 slot is always WASTED to
      distinguish between FULL and EMPTY states.
      A circular queue of SIZE=5 can hold only 4 elements!
```

### 🚨 PYQ TRAP #1: Circular Queue Capacity
> A circular queue of declared size N can hold at most **N-1 elements** (not N), because 1 slot is reserved to distinguish full from empty state.
> Some implementations use a `count` variable to avoid this waste, but the standard exam answer is **N-1**.

---

## 🔷 SECTION 4: Circular Queue — Enqueue & Dequeue

### ENQUEUE Algorithm:
```
ENQUEUE(cq, front, rear, SIZE, value):
  1. Check FULL: if (rear+1)%SIZE == front → "Overflow", stop
  2. If empty (front==-1): set front=0
  3. Update rear: rear = (rear+1) % SIZE
  4. Insert: cq[rear] = value
```

### DEQUEUE Algorithm:
```
DEQUEUE(cq, front, rear, SIZE):
  1. Check EMPTY: if front==-1 → "Underflow", stop
  2. Store value: value = cq[front]
  3. If this was the LAST element (front==rear):
       Reset: front = -1, rear = -1  (back to empty)
     Else:
       Update front: front = (front+1) % SIZE
  4. Return value
```

---

## 🔷 SECTION 5: Circular Queue — Complete Dry Run

### Setup: Circular Queue of SIZE = 5 (indices 0–4, holds max 4 elements)

```
INITIAL STATE: front=-1, rear=-1
 ┌────┬────┬────┬────┬────┐
 │ _  │ _  │ _  │ _  │ _  │
 └────┴────┴────┴────┴────┘
  [0]  [1]  [2]  [3]  [4]

══════════════════════════════════════
ENQUEUE 10:
  Full check: (rear+1)%5 = 0 ≠ front(-1) → not full
  Empty: front==-1 → set front=0
  rear = (-1+1)%5 = 0; cq[0] = 10
  front=0, rear=0
 ┌────┬────┬────┬────┬────┐
 │ 10 │ _  │ _  │ _  │ _  │
 └────┴────┴────┴────┴────┘
   ↑f,r

══════════════════════════════════════
ENQUEUE 20:
  rear = (0+1)%5 = 1; cq[1] = 20
  front=0, rear=1
 ┌────┬────┬────┬────┬────┐
 │ 10 │ 20 │ _  │ _  │ _  │
 └────┴────┴────┴────┴────┘
   ↑f    ↑r

══════════════════════════════════════
ENQUEUE 30:
  rear = (1+1)%5 = 2; cq[2] = 30
  front=0, rear=2
 ┌────┬────┬────┬────┬────┐
 │ 10 │ 20 │ 30 │ _  │ _  │
 └────┴────┴────┴────┴────┘
   ↑f         ↑r

══════════════════════════════════════
ENQUEUE 40:
  rear = (2+1)%5 = 3; cq[3] = 40
  front=0, rear=3
 ┌────┬────┬────┬────┬────┐
 │ 10 │ 20 │ 30 │ 40 │ _  │
 └────┴────┴────┴────┴────┘
   ↑f              ↑r

══════════════════════════════════════
ENQUEUE 50 (attempt):
  Full check: (rear+1)%5 = (3+1)%5 = 4 ≠ 0(front) → not full yet
  rear = (3+1)%5 = 4; cq[4] = 50
  front=0, rear=4
 ┌────┬────┬────┬────┬────┐
 │ 10 │ 20 │ 30 │ 40 │ 50 │
 └────┴────┴────┴────┴────┘
   ↑f                   ↑r

══════════════════════════════════════
ENQUEUE 60 (attempt):
  Full check: (rear+1)%5 = (4+1)%5 = 0 == front(0) → OVERFLOW!
  Cannot insert 60. (SIZE=5 holds max 4 elements)

══════════════════════════════════════
DEQUEUE:
  value = cq[front] = cq[0] = 10
  front ≠ rear (0 ≠ 4), so front = (0+1)%5 = 1
  front=1, rear=4   RETURNED: 10
 ┌────┬────┬────┬────┬────┐
 │ _  │ 20 │ 30 │ 40 │ 50 │
 └────┴────┴────┴────┴────┘
         ↑f                ↑r
  (slot [0] is now FREE and REUSABLE!)

══════════════════════════════════════
DEQUEUE again:
  value = cq[1] = 20; front = (1+1)%5 = 2
  front=2, rear=4   RETURNED: 20
 ┌────┬────┬────┬────┬────┐
 │ _  │ _  │ 30 │ 40 │ 50 │
 └────┴────┴────┴────┴────┘
              ↑f            ↑r

══════════════════════════════════════
ENQUEUE 60 (try again after dequeues):
  Full check: (4+1)%5 = 0 ≠ 2(front) → NOT full!
  rear = (4+1)%5 = 0; cq[0] = 60   ← WRAPS AROUND!
  front=2, rear=0
 ┌────┬────┬────┬────┬────┐
 │ 60 │ _  │ 30 │ 40 │ 50 │
 └────┴────┴────┴────┴────┘
   ↑r        ↑f
  CIRCULAR WRAP-AROUND ACHIEVED! ✅
  Index 0 (previously freed by dequeue) is reused!
```

---

## 🔷 SECTION 6: Circular Queue State Visualization

```
Circular structure (SIZE = 5):

         [0] = 60
     [4]         [1]
   50               _
     [3]         [2]
         40 [3] is [3]
              30 at [2]

Front (f) at [2] = 30 (next to be served)
Rear  (r) at [0] = 60 (last inserted)

Order of elements: 30, 40, 50, 60 (FIFO)

FULL condition visualization:
  (r+1)%5 would equal f → no more space

Empty condition:
  front == -1 (initial) or front == rear (some implementations)
```

---

## 🔷 SECTION 7: Deque — Double-Ended Queue

### What is a Deque?
```
DEQUE (pronounced "deck") = Double-Ended Queue

A Deque allows insertion and deletion from BOTH ends:
  → Insert from FRONT
  → Insert from REAR
  → Delete from FRONT
  → Delete from REAR

It is MORE FLEXIBLE than both Stack and Queue.
A Deque can simulate BOTH Stack and Queue behavior!
```

### Deque vs Stack vs Queue:

```
Feature          Stack       Queue       Deque
─────────────────────────────────────────────────
Insert at front  ✅(push)   ❌          ✅
Insert at rear   ❌          ✅(enqueue) ✅
Delete from front❅(pop)    ✅(dequeue)  ✅
Delete from rear ❌          ❌          ✅
Simulates Stack? YES(front ops only) NO  YES
Simulates Queue? NO     YES(front del, rear ins)  YES
```

### Deque Operations:
```
All Deque operations and their time complexity:

Operation          Action                        Time
─────────────────────────────────────────────────────
insertFront(x)     Insert x at front pointer     O(1)
insertRear(x)      Insert x at rear pointer      O(1)
deleteFront()      Remove from front             O(1)
deleteRear()       Remove from rear              O(1)
getFront()         View front element (no remove) O(1)
getRear()          View rear element (no remove)  O(1)
isEmpty()          Check if empty                O(1)
isFull()           Check if full                 O(1)
```

---

## 🔷 SECTION 8: Types of Deque

### Type 1: Input-Restricted Deque
```
INPUT-RESTRICTED DEQUE:
  → Insertion allowed from ONE end only (rear)
  → Deletion allowed from BOTH ends

         INSERT only ──→ [REAR] [elements] [FRONT] ←── DELETE
                                                     ←── DELETE

Real-life analogy: A queue at a service center where you can
  only join at the back, but can be served from either end
  (e.g., VIP customers can exit from the front, normal from front,
   both can leave but only join at rear)

KEY: Input restricted = restricted insert = only rear insert
```

### Type 2: Output-Restricted Deque
```
OUTPUT-RESTRICTED DEQUE:
  → Insertion allowed from BOTH ends
  → Deletion allowed from ONE end only (front)

  INSERT ──→ [REAR] [elements] [FRONT] ←── DELETE only
  INSERT ──→ [FRONT]

Real-life analogy: Both regular and express entry allowed
  (front and rear), but only one exit lane

KEY: Output restricted = restricted delete = only front delete
```

### Memory Trick:
```
INPUT-restricted:   Think "you can only INPUT from one place" (rear)
                    But OUTPUT from both places
OUTPUT-restricted:  Think "you can only OUTPUT from one place" (front)
                    But INPUT from both places
```

### 🚨 PYQ TRAP #2: Deque Names
> Input-restricted Deque: Insert only at REAR; Delete from both FRONT and REAR
> Output-restricted Deque: Delete only from FRONT; Insert from both FRONT and REAR
> This is frequently confused in exams — focus on which operation is restricted.

---

## 🔷 SECTION 9: Deque Operations — Dry Run

### Example: Output-Restricted Deque, SIZE = 5
```
Initial: front=-1, rear=-1, deque = [_|_|_|_|_]

insertRear(10):  rear=0, front=0; deque=[10|_|_|_|_]
insertRear(20):  rear=1;          deque=[10|20|_|_|_]
insertFront(5):  front-1 → but front=0, so front=(0-1+SIZE)%SIZE=4
                            deque=[10|20|_|_|5]  front=4, rear=1

  Visual:
   [0]  [1]  [2]  [3]  [4]
   [10 | 20 |  _ |  _ |  5]
                         ↑f(4)  ↑r(1) — wrapped!

insertRear(30):  rear=(1+1)%5=2; deque=[10|20|30|_|5]
deleteFront():   value=deque[4]=5; front=(4+1)%5=0
                 deque=[10|20|30|_|_]  front=0, rear=2
                 RETURNED: 5

deleteRear():    value=deque[2]=30; rear=(2-1+5)%5=1
                 deque=[10|20|_|_|_]  front=0, rear=1
                 RETURNED: 30
```

### Key Formula for deleteRear (moving rear backward):
```
rear = (rear - 1 + SIZE) % SIZE

Why (+SIZE)?  To avoid negative result when rear=0:
  (0-1) = -1 → WRONG in modulo
  (0-1+5) = 4 → CORRECT circular backward move
```

---

## 🔷 SECTION 10: Delete from Rear — Linked List Context

### Important Exam Fact:
```
SINGLY LINKED LIST: Delete from rear = O(N)

Why? Because in a singly linked list:
  → Each node only has a NEXT pointer (no PREVIOUS pointer)
  → To delete the last node, you need to find the SECOND-TO-LAST node
  → You must traverse from HEAD to find it
  → This requires O(N) traversal

DOUBLY LINKED LIST: Delete from rear = O(1)
  → Because each node has BOTH next and prev pointers
  → Tail's prev pointer directly gives second-to-last node

This is why Deque is more efficiently implemented using
DOUBLY LINKED LIST than singly linked list!
```

### 🚨 PYQ TRAP #3: Deletion from Rear Complexity
> In a **Singly Linked List**, deletion from the rear (tail) requires **O(N)** time because you must traverse the entire list to find the second-to-last node.
> In a **Doubly Linked List**, deletion from rear is **O(1)** due to the `prev` pointer.

---

## 🔷 SECTION 11: Circular Queue vs Deque vs Linear Queue — Master Table

```
Feature              Linear Queue    Circular Queue    Deque
─────────────────────────────────────────────────────────────────
Insert at front      ❌               ❌                ✅
Insert at rear       ✅               ✅                ✅
Delete from front    ✅               ✅                ✅
Delete from rear     ❌               ❌                ✅
Full condition       rear==MAX-1     (r+1)%S==front    (r+1)%S==front
Empty condition      front==-1       front==-1         front==-1
Memory wastage       YES (false OFW) NO (reuses slots) NO
Flexibility          Low             Medium            High
Use case             Simple FIFO     Buffer (audio,IO) Editor (undo+redo)
```

---

## 📊 VISUAL SUMMARY — Circular Queue & Deque

```
CIRCULAR QUEUE (Ring Buffer):
         ┌──── CIRCULAR WRAP ─────┐
         ↓                        ↑
  [0] → [1] → [2] → [3] → [4] → back to [0]

  rear = (rear+1)%SIZE  ← enqueue
  front = (front+1)%SIZE ← dequeue
  FULL: (rear+1)%SIZE == front
  EMPTY: front == -1

DEQUE (Double-Ended Queue):
  ←DELETE/INSERT   [FRONT] ... [REAR]   DELETE/INSERT→
  All 4 operations: O(1)
  
  INPUT-RESTRICTED:  Insert REAR only; Delete BOTH ends
  OUTPUT-RESTRICTED: Delete FRONT only; Insert BOTH ends
  
  Best implemented with: DOUBLY LINKED LIST
  deleteRear in singly LL: O(N) — PYQ trap!
```

---
---

# PART 2: GENERAL STUDIES
## 🌧️ India Climate — The Monsoon System

---

## 🔷 WHY THIS MATTERS FOR BPSC TRE:
- Monsoon is the most tested climate topic in Indian geography
- SW/NE monsoon direction, onset dates, and regional effects = PYQ favourites
- Agriculture dependence on monsoon = Bihar-specific context

---

## 🔷 WHAT IS MONSOON?

### Definition:
```
"Monsoon" comes from the Arabic word "MAUSAM" meaning SEASON.
Monsoon = a seasonal reversal of wind direction.
  Summer → winds blow from SEA to LAND (bring rain)
  Winter → winds blow from LAND to SEA (dry)

India's agriculture is 60–70% dependent on monsoon rainfall.
```

### Why Does Monsoon Happen — Basic Mechanism:
```
STEP-BY-STEP MONSOON MECHANISM:

SUMMER (June–September):
  1. Indian landmass heats up rapidly (land heats faster than sea)
  2. A strong LOW PRESSURE area forms over India (especially NW India)
  3. The Indian Ocean stays relatively COOLER → HIGH PRESSURE
  4. Winds ALWAYS blow from HIGH pressure to LOW pressure
  5. So: winds blow from Indian Ocean (high) → Indian landmass (low)
  6. These moisture-laden winds = SOUTHWEST MONSOON

WINTER (October–February):
  1. Land cools rapidly; sea stays warmer
  2. HIGH PRESSURE forms over land; LOW PRESSURE over sea
  3. Winds reverse: blow from land to sea
  4. These dry winds from NE = NORTHEAST MONSOON
     (picks up moisture over Bay of Bengal → brings rain to SE India)

This reversal of wind direction = MONSOON
```

---

## 🔷 TWO BRANCHES OF SOUTHWEST MONSOON

### The Southwest Monsoon splits into two branches:

```
SW MONSOON BRANCHES:
              Bay of Bengal Branch
             ↗ (hits Assam, NE India, Bihar, UP, NW India)
Arabian Sea
         ↖
          Arabian Sea Branch
             ↘ (hits Western Ghats first, then moves NE)
```

### Branch 1: Arabian Sea Branch
```
Origin:        Arabian Sea
Direction:     Hits Western Ghats first (June 1 — Kerala)
Effect on WG:  HEAVY rain on windward side (west-facing slope)
               Western Ghats = highest rainfall in India
               Mawsynram/Cherrapunji = world's wettest places nearby
Rain shadow:   Leeward (east) side of Western Ghats gets LESS rain
               → Deccan Plateau interior is DRY
Further path:  Moves northeast → meets Bay of Bengal branch
               → Together bring rain to rest of India
```

### Branch 2: Bay of Bengal Branch
```
Origin:        Bay of Bengal
Direction:     Hits Assam, northeastern India, then deflected by
               Himalayas → moves westward along Gangetic plain
Effect:        Brings rain to Bihar, UP, and northwest India
Bihar Rain:    Bihar receives 80–90% of annual rainfall from
               Bay of Bengal Branch of SW Monsoon
               (Average: ~1100-1200 mm annually)
```

---

## 🔷 SOUTHWEST MONSOON (JUNE–SEPTEMBER)

### Key Facts:
```
Origin:        Indian Ocean + Arabian Sea + Bay of Bengal
Direction:     SOUTH to NORTH (enters India from south/southwest)
Season:        June to September (4 months)
Onset:         June 1 — Kerala (southwest tip of India)
               June 10-15 — Mumbai
               June end — Delhi
               July first week — reaches entire India

Normal retreat: September 1 — Rajasthan (starts retreating NW first)
                October 15 — retreats from most of peninsular India
                November 15 — retreats completely from India

Rainfall share: Provides ~75–80% of India's TOTAL annual rainfall!
```

### Onset Dates — EXAM CRITICAL:
```
June 1    → Kerala (Thiruvananthapuram)
June 7-10 → Goa/Karnataka
June 10-15 → Mumbai
June 20-25 → Bihar / Eastern India
July 1    → Delhi / Most of North India
July 15   → Entire country covered

"June 1 = Monsoon enters Kerala" — most asked date fact
```

### 🚨 PYQ TRAP: Mawsynram vs Cherrapunji
> **Mawsynram** (Meghalaya) — officially the world's wettest place (~11,871 mm annual rainfall)
> **Cherrapunji** (Sohra, Meghalaya) — second, also extremely wet (~11,430 mm)
> Both in Meghalaya, both in the funnel of Bay of Bengal branch of SW monsoon
> Both face the Bay of Bengal branch head-on due to hill topography

---

## 🔷 NORTHEAST MONSOON (OCTOBER–DECEMBER)

### Key Facts:
```
Origin:          Forms over Central Asia / Northwest India as land cools
Direction:       NORTH to SOUTH, from land toward Bay of Bengal
Season:          October to December
Which state affected MOST: Tamil Nadu (southeast India)
Why Tamil Nadu?  The NE monsoon blows from NE to SW
               → Picks up moisture from Bay of Bengal
               → Hits southeastern coast = Tamil Nadu coast = HEAVY RAIN
               → Rest of India gets DRY weather during this period

Tamil Nadu = Unique among Indian states:
  → Gets rain from BOTH Southwest (June-Sept) AND Northeast (Oct-Dec) monsoon
  → Chennai's October-December = wettest period (from NE monsoon)
```

### 🚨 PYQ TRAP: Northeast Monsoon
> The Northeast Monsoon brings rain to **Tamil Nadu**, not to Bihar, UP, or Maharashtra.
> While the rest of India has its dry winter season, Tamil Nadu enjoys heavy rainfall.
> This is why Cyclone season in Bay of Bengal coincides with NE monsoon (Oct-Dec).

---

## 🔷 MONSOON ONSET MECHANISM — PRESSURE SYSTEMS

```
INTER TROPICAL CONVERGENCE ZONE (ITCZ):
  → A belt of low pressure near the equator
  → Moves northward in summer (May-June) as the sun moves north
  → When ITCZ shifts over the Indian subcontinent → SW monsoon onset
  → Also called the "Monsoon Trough"

MASCARENE HIGH:
  → High pressure system near Mascarene Islands (south of Madagascar)
  → The source of SW monsoon winds in summer

TIBETAN PLATEAU HEATING:
  → Tibetan Plateau at very high altitude heats up significantly
  → Creates additional upper-level high pressure in summer
  → Strengthens the low pressure system over India
  → Acts as a heat engine driving monsoon circulation
```

---

## 🔷 IMPORTANT RAINFALL REGIONS IN INDIA

```
VERY HIGH RAINFALL (>200 cm):
  → Assam, Meghalaya (Mawsynram/Cherrapunji)
  → Western Ghats (Konkan coast, Kerala, Goa)
  → Andaman & Nicobar Islands
  → Northeastern states

HIGH RAINFALL (100–200 cm):
  → Most of Bihar, Bengal
  → Coastal Odisha, AP
  → Western Maharashtra

MODERATE RAINFALL (50–100 cm):
  → Most of the Deccan Plateau
  → Punjab, Haryana, UP (western)

LOW RAINFALL (<50 cm):
  → Rajasthan desert (Thar)
  → Gujarat interior
  → Leh-Ladakh
  → Rain shadow areas behind Western Ghats
```

### Bihar Rainfall Profile:
```
Bihar:
  → Annual rainfall: ~1100 mm (north Bihar gets more, south less)
  → Season: June to September (4 months of SW monsoon)
  → Source: Bay of Bengal branch of SW monsoon
  → North Bihar: higher rainfall (Himalayan rivers also contribute floods)
  → South Bihar: moderate rainfall, less flood-prone
  → Kosi region (Supaul, Saharsa): among highest rainfall in Bihar
```

---

## 🔷 MONSOON & AGRICULTURE — INDIA'S DEPENDENCE

```
India's agricultural calendar revolves entirely around monsoon:

KHARIF CROPS (Monsoon/Summer crops):
  Sowing: June-July (with monsoon onset)
  Harvest: September-October
  Examples: Rice, Maize, Cotton, Soybean, Jowar, Bajra, Groundnut
  → Bihar's main Kharif crop = RICE (paddy)

RABI CROPS (Winter crops):
  Sowing: October-November (after monsoon withdrawal)
  Harvest: March-April
  Examples: Wheat, Mustard, Peas, Barley, Gram
  → Bihar's main Rabi crop = WHEAT + MUSTARD

ZAID CROPS (Summer/spring):
  Between Rabi harvest and Kharif sowing
  Examples: Watermelon, Cucumber, Pumpkin, Sunflower
```

### 🚨 PYQ Fact: Monsoon Failure = Food Security Crisis
> When SW monsoon fails or is deficient (< 90% of normal rainfall), India experiences drought conditions → Kharif crop failure → food inflation. This is why the Budget speech often mentions "good monsoon outlook."

---

## 🔷 CYCLONES — MONSOON RELATED

```
BAY OF BENGAL is WARMER than Arabian Sea:
  → More cyclones form in Bay of Bengal (approx. 6 times more)
  → Arabian Sea cyclones: less frequent but affect Gujarat, Maharashtra

Cyclone Season (Bay of Bengal):
  → PRE-MONSOON: April-May (hits Odisha, AP, WB coast)
  → POST-MONSOON: October-December (hits Tamil Nadu, AP coast)
     ← This coincides with NE monsoon season

Famous Bihar cyclone impact: Kosi floods are often worsened by
cyclonic systems in Bay of Bengal during October
```

---

## 🔷 MEMORY TRICKS — Monsoon

### SW vs NE Monsoon Quick Recall:
```
"SW MONSOON = SUMMER = SEA to LAND = JUNE to SEPT = WESTERN/NORTHERN India"
"NE MONSOON = WINTER = LAND to SEA = OCT to DEC = TAMIL NADU only"
```

### Monsoon Onset Sequence (North to South retreat, South to North onset):
```
ONSET (south to north): Kerala June 1 → Bihar June 20 → Delhi July 1
RETREAT (north to south): Rajasthan Sept 1 → retreats by Nov 15
```

### Wettest Places:
```
"Mawsynram = Most Wet" (M for Most, M for Mawsynram)
Both Mawsynram AND Cherrapunji = Meghalaya = Bay of Bengal branch monsoon
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Circular Queue, Deque, Ring Buffer, Conditions, Complexity

---

**Q1.** What is the full form of "Deque"?
(A) Delayed Queue
(B) Double-Ended Queue
(C) Dynamic Queue
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the full condition for a Circular Queue (SIZE = N)?
(A) rear == N - 1
(B) front == rear
(C) (rear + 1) % N == front
(D) More than one of the above
(E) None of the above

---

**Q3.** A Circular Queue of declared SIZE = 6 can hold a maximum of how many elements (standard implementation)?
(A) 6
(B) 7
(C) 5
(D) More than one of the above
(E) None of the above

---

**Q4.** In a Circular Queue, after enqueuing to the LAST index (SIZE-1), the next rear position becomes:
(A) SIZE
(B) -1
(C) 0 (wraps around)
(D) More than one of the above
(E) None of the above

---

**Q5.** The formula to update `rear` in a Circular Queue after enqueue is:
(A) rear = rear + 1
(B) rear = rear % SIZE
(C) rear = (rear + 1) % SIZE
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the EMPTY condition of a Circular Queue (initial state)?
(A) front == rear == 0
(B) front == rear == -1
(C) rear == SIZE - 1
(D) More than one of the above
(E) None of the above

---

**Q7.** A Circular Queue is also called:
(A) Priority Buffer
(B) Ring Buffer
(C) Circular Stack
(D) More than one of the above
(E) None of the above

---

**Q8.** Which problem of the Linear Queue is solved by Circular Queue?
(A) Slow insertion speed
(B) High memory usage for single elements
(C) False overflow — memory wastage due to front moving forward
(D) More than one of the above
(E) None of the above

---

**Q9.** In a Deque, which operations are allowed?
(A) Insert at front only
(B) Delete from rear only
(C) Insert and delete from BOTH front and rear
(D) More than one of the above
(E) None of the above

---

**Q10.** An Input-Restricted Deque allows:
(A) Insertion from both ends; deletion from front only
(B) Insertion from rear only; deletion from both ends
(C) Insertion and deletion from both ends
(D) More than one of the above
(E) None of the above

---

**Q11.** An Output-Restricted Deque allows:
(A) Insertion from both ends; deletion from front only
(B) Insertion from rear only; deletion from both ends
(C) Insertion and deletion from both ends
(D) More than one of the above
(E) None of the above

---

**Q12.** The time complexity of insertFront() in a Deque is:
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q13.** Which data structure can simulate BOTH Stack and Queue behavior?
(A) Priority Queue
(B) Circular Queue
(C) Deque
(D) More than one of the above
(E) None of the above

---

**Q14.** In a Circular Queue of SIZE=5, if front=2 and rear=1, how many elements are in the queue?
(A) 1
(B) 3
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q15.** The deleteRear() operation in a Circular Queue or Deque uses which formula for rear update?
(A) rear = rear - 1
(B) rear = (rear - 1 + SIZE) % SIZE
(C) rear = (rear + 1) % SIZE
(D) More than one of the above
(E) None of the above

---

**Q16.** Why is Deque more efficiently implemented using a Doubly Linked List than a Singly Linked List?
(A) Doubly Linked List uses less memory
(B) Singly Linked List cannot implement Deque at all
(C) Deletion from rear requires O(N) in singly LL; O(1) in doubly LL
(D) More than one of the above
(E) None of the above

---

**Q17.** Round Robin CPU scheduling (used in OS) uses which type of queue?
(A) Priority Queue
(B) Deque
(C) Circular Queue
(D) More than one of the above
(E) None of the above

---

**Q18.** In a Circular Queue, when the LAST element is dequeued (queue becomes empty), the reset is:
(A) front = 0, rear = 0
(B) front = -1, rear = -1
(C) front = 1, rear = 0
(D) More than one of the above
(E) None of the above

---

**Q19.** The keyboard input buffer in a computer uses which data structure concept?
(A) Stack
(B) Circular Queue (Ring Buffer)
(C) Binary Tree
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following correctly lists ALL operations supported by a Deque?
(A) insertRear, deleteRear only
(B) insertFront, insertRear, deleteFront, deleteRear
(C) insertRear, deleteFront only
(D) More than one of the above
(E) None of the above

---

**Q21.** In a Circular Queue of SIZE=4, front=3, rear=2. Attempting enqueue gives:
(A) Insertion succeeds normally
(B) (rear+1)%4 = 3 = front → OVERFLOW, cannot insert
(C) rear wraps to rear=3
(D) More than one of the above
(E) None of the above

---

**Q22.** What is the number of elements in a Circular Queue when front=1 and rear=4 (SIZE=7)?
(A) 3
(B) 4
(C) (4-1+7)%7 = (3)%7 = 4 elements (using formula)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following is TRUE about a Circular Queue?
(A) It wastes memory just like a linear queue
(B) It can store exactly SIZE elements in standard implementation
(C) It recycles freed positions by wrapping rear/front using modulo
(D) More than one of the above
(E) None of the above

---

**Q24.** A Deque in which deletion is restricted to the front end only is called:
(A) Input-Restricted Deque
(B) Output-Restricted Deque
(C) Priority Deque
(D) More than one of the above
(E) None of the above

---

**Q25.** Deletion from the REAR in a Singly Linked List has time complexity:
(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### India Climate — Monsoon System

---

**Q26.** The word "Monsoon" is derived from which language?
(A) Sanskrit
(B) Arabic ("Mausam" = season)
(C) Portuguese
(D) More than one of the above
(E) None of the above

---

**Q27.** The Southwest Monsoon normally arrives at Kerala on approximately which date?
(A) July 1
(B) June 15
(C) June 1
(D) More than one of the above
(E) None of the above

---

**Q28.** The Southwest Monsoon brings what percentage of India's total annual rainfall?
(A) 40–50%
(B) 60–65%
(C) 75–80%
(D) More than one of the above
(E) None of the above

---

**Q29.** The Bay of Bengal branch of the Southwest Monsoon primarily brings rainfall to:
(A) Rajasthan and Gujarat
(B) Tamil Nadu (from NE Monsoon — not SW)
(C) Assam, Northeast India, Bihar, UP, and Northwest India
(D) More than one of the above
(E) None of the above

---

**Q30.** Which state of India receives rainfall from BOTH the Southwest AND Northeast Monsoon?
(A) Bihar
(B) Maharashtra
(C) Tamil Nadu
(D) More than one of the above
(E) None of the above

---

**Q31.** The Northeast Monsoon season in India is approximately:
(A) June to September
(B) October to December
(C) January to March
(D) More than one of the above
(E) None of the above

---

**Q32.** Mawsynram in Meghalaya is among the world's wettest places because:
(A) It is near the Bay of Bengal branch of SW monsoon and has funnel-shaped hills
(B) It receives Western Disturbances year-round
(C) It is located at the highest altitude in Meghalaya
(D) More than one of the above
(E) None of the above

---

**Q33.** The leeward (rain shadow) side of the Western Ghats receives:
(A) More rainfall than the windward side
(B) Less rainfall — because moisture has already fallen on the windward side
(C) The same rainfall as the windward side
(D) More than one of the above
(E) None of the above

---

**Q34.** Kharif crops are sown during which season in India?
(A) October–November (after monsoon)
(B) June–July (with monsoon onset)
(C) January–February (winter)
(D) More than one of the above
(E) None of the above

---

**Q35.** Which of the following is a Kharif crop?
(A) Wheat
(B) Mustard
(C) Rice (Paddy)
(D) More than one of the above
(E) None of the above

---

**Q36.** The monsoon in India is essentially a result of:
(A) Seasonal reversal of wind direction due to differential heating of land and sea
(B) Permanent wind systems blowing from Arabia
(C) Rainfall from tropical cyclones throughout the year
(D) More than one of the above
(E) None of the above

---

**Q37.** Southwest Monsoon starts withdrawing from India beginning with which region?
(A) Kerala (south)
(B) Bihar and UP (east)
(C) Rajasthan (northwest)
(D) More than one of the above
(E) None of the above

---

**Q38.** The Inter-Tropical Convergence Zone (ITCZ) shifting northward over India in summer is associated with:
(A) Northeast Monsoon onset
(B) Southwest Monsoon onset
(C) Western Disturbances
(D) More than one of the above
(E) None of the above

---

**Q39.** Bihar receives most of its rainfall from which branch of the Southwest Monsoon?
(A) Arabian Sea Branch
(B) Bay of Bengal Branch
(C) Cyclonic Branch
(D) More than one of the above
(E) None of the above

---

**Q40.** The season in India when SW Monsoon brings maximum rainfall is:
(A) March–May
(B) June–September
(C) October–December
(D) More than one of the above
(E) None of the above

---

**Q41.** Cyclones in the Bay of Bengal are most frequent during which months?
(A) January–March
(B) June–August
(C) October–December (post-monsoon) and April–May (pre-monsoon)
(D) More than one of the above
(E) None of the above

---

**Q42.** The Tibetan Plateau's heating in summer contributes to the Indian Monsoon by:
(A) Cooling the upper atmosphere and weakening monsoon
(B) Creating upper-level high pressure that helps strengthen the low pressure over India
(C) Deflecting monsoon winds toward Pakistan
(D) More than one of the above
(E) None of the above

---

**Q43.** Which of the following correctly matches the crop type with its sowing season?
(A) Kharif – October; Rabi – June
(B) Kharif – June/July; Rabi – October/November
(C) Both Kharif and Rabi are sown in June
(D) More than one of the above
(E) None of the above

---

**Q44.** Rajasthan (Thar Desert) receives very low rainfall despite being in India because:
(A) It is too cold for rain to fall
(B) The monsoon has already lost most moisture before reaching Rajasthan, and lack of geographic barriers causes winds to continue without rising
(C) Rajasthan is not in the path of any monsoon branch
(D) More than one of the above
(E) None of the above

---

**Q45.** The Arabian Sea Branch of the SW Monsoon hits India first at:
(A) Maharashtra coast
(B) Goa
(C) Kerala (Western Ghats)
(D) More than one of the above
(E) None of the above

---

**Q46.** What is the approximate average annual rainfall of Bihar?
(A) 400–500 mm
(B) 700–800 mm
(C) 1,000–1,200 mm
(D) More than one of the above
(E) None of the above

---

**Q47.** Rabi crops in Bihar include:
(A) Rice and maize
(B) Wheat, mustard, and gram
(C) Cotton and groundnut
(D) More than one of the above
(E) None of the above

---

**Q48.** The Mascarene High pressure system (near Madagascar) is associated with:
(A) Bringing cold winds to India in winter
(B) Being the source of SW Monsoon winds that flow toward India
(C) Causing Western Disturbances in North India
(D) More than one of the above
(E) None of the above

---

**Q49.** The Bay of Bengal produces MORE cyclones than the Arabian Sea because:
(A) It is saltier than the Arabian Sea
(B) It is warmer and has more moisture, favoring cyclone formation
(C) It is closer to the equator
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following states receives the LEAST monsoon rainfall in India?
(A) Assam
(B) Tamil Nadu
(C) Rajasthan (Thar Desert region)
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
| 1 | (B) | Deque = Double-Ended Queue |
| 2 | (C) | Full: (rear+1)%N == front |
| 3 | (C) | SIZE=6 → max 5 elements (1 slot reserved) |
| 4 | (C) | After SIZE-1, next = 0 (modulo wrap) |
| 5 | (C) | rear = (rear+1)%SIZE |
| 6 | (B) | Empty: front=rear=-1 |
| 7 | (B) | Circular Queue = Ring Buffer |
| 8 | (C) | False overflow = memory wastage problem solved |
| 9 | (C) | Deque: insert/delete from BOTH ends |
| 10 | (B) | Input-restricted: insert REAR only; delete BOTH ends |
| 11 | (A) | Output-restricted: insert BOTH ends; delete FRONT only |
| 12 | (C) | O(1) — direct front pointer manipulation |
| 13 | (C) | Deque simulates both Stack and Queue |
| 14 | (C) | (rear-front+SIZE)%SIZE = (1-2+5)%5 = 4%5 = 4 elements |
| 15 | (B) | deleteRear: rear = (rear-1+SIZE)%SIZE |
| 16 | (C) | Singly LL: deleteRear = O(N); Doubly LL = O(1) |
| 17 | (C) | Round Robin uses Circular Queue |
| 18 | (B) | After last dequeue: front=-1, rear=-1 |
| 19 | (B) | Keyboard buffer = Circular Queue (Ring Buffer) |
| 20 | (B) | All 4 operations: insertFront, insertRear, deleteFront, deleteRear |
| 21 | (B) | (2+1)%4=3=front → OVERFLOW |
| 22 | (C) | (4-1+7)%7=4 elements |
| 23 | (C) | Circular: recycles freed positions using modulo |
| 24 | (B) | Output-restricted: delete from front ONLY |
| 25 | (C) | Singly LL delete at rear = O(n) traversal |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Arabic "Mausam" = season |
| 27 | (C) | June 1 = Monsoon arrives at Kerala |
| 28 | (C) | SW Monsoon = 75–80% of India's annual rainfall |
| 29 | (C) | BoB branch → Assam, NE India, Bihar, UP, NW India |
| 30 | (C) | Tamil Nadu = SW + NE Monsoon both |
| 31 | (B) | NE Monsoon = October to December |
| 32 | (A) | Bay of Bengal branch + funnel hills → Mawsynram wettest |
| 33 | (B) | Leeward/rain shadow = less rainfall |
| 34 | (B) | Kharif = June-July sowing (monsoon season) |
| 35 | (C) | Rice = Kharif crop |
| 36 | (A) | Seasonal wind reversal due to land-sea differential heating |
| 37 | (C) | Retreat starts from Rajasthan (NW) in September |
| 38 | (B) | ITCZ moving north = SW Monsoon onset |
| 39 | (B) | Bihar = Bay of Bengal Branch of SW Monsoon |
| 40 | (B) | June–September = peak SW Monsoon |
| 41 | (C) | BoB cyclones peak Oct-Dec and April-May |
| 42 | (B) | Tibetan Plateau heating → strengthens monsoon |
| 43 | (B) | Kharif June/July; Rabi October/November |
| 44 | (B) | Monsoon weakens before reaching; no geographic barriers to force ascent |
| 45 | (C) | Arabian Sea branch hits Kerala Western Ghats first |
| 46 | (C) | Bihar ≈ 1,000–1,200 mm annual rainfall |
| 47 | (B) | Rabi = wheat, mustard, gram (winter crops) |
| 48 | (B) | Mascarene High = source of SW Monsoon winds |
| 49 | (B) | BoB warmer → more evaporation → more cyclones |
| 50 | (C) | Rajasthan (Thar Desert) = lowest rainfall |

---
---

# 🔁 DAY 19 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Circular Queue & Deque

### Circular Queue — All Critical Formulas:
```
Empty condition:     front == -1  (initial state)
                     OR front == rear (after last dequeue — some implementations)
Full condition:      (rear + 1) % SIZE == front
Enqueue rear update: rear = (rear + 1) % SIZE
Dequeue front update:front = (front + 1) % SIZE
deleteRear update:   rear = (rear - 1 + SIZE) % SIZE  ← (+SIZE avoids negative)
Element count:       (rear - front + SIZE) % SIZE
Max elements:        SIZE - 1 (NOT SIZE — 1 slot reserved!)
```

### Circular Queue Key Points:
```
1. Also called RING BUFFER
2. Solves LINEAR QUEUE's false overflow problem
3. All operations O(1)
4. Max capacity = SIZE - 1 (standard implementation)
5. After last element dequeued: reset front = -1, rear = -1
6. Used in: keyboard buffer, audio streaming, Round Robin OS scheduling
```

### Deque Quick Summary:
```
Deque = Double-Ended Queue
ALL 4 operations: insertFront, insertRear, deleteFront, deleteRear → all O(1)

INPUT-RESTRICTED:
  Insert: REAR only        Delete: BOTH ends
  
OUTPUT-RESTRICTED:
  Insert: BOTH ends        Delete: FRONT only

Best implemented with: DOUBLY LINKED LIST
deleteRear in Singly LL: O(N)  ← KEY PYQ TRAP
deleteRear in Doubly LL: O(1)

Deque can simulate Stack (use front ops) and Queue (standard FIFO ops)
```

### Master Rule:
```
CIRCULAR QUEUE full?   (rear+1)%SIZE == front   ← MOST ASKED FORMULA
CIRCULAR QUEUE empty?  front == -1
```

---

## ⚡ RAPID FIRE — India Monsoon System

### 5 Core Facts:
```
1. SW Monsoon = June to Sept; 75-80% of India's rainfall
2. NE Monsoon = Oct to Dec; affects Tamil Nadu mainly
3. SW Monsoon onset: June 1 = Kerala
4. Mawsynram (Meghalaya) = world's wettest; BoB branch + funnel hills
5. Rajasthan (Thar) = lowest rainfall; Tamil Nadu = both SW + NE monsoon
```

### Two Branches of SW Monsoon:
```
Arabian Sea Branch → hits Kerala/WG first → rain shadow on Deccan
Bay of Bengal Branch → hits NE India, Bihar, UP, Delhi
Bihar rainfall source = Bay of Bengal Branch
```

### Retreat Sequence:
```
Starts from: Rajasthan/NW India (September 1)
Ends: Entire India by November 15
(Opposite of onset which was south-to-north)
```

### Crops and Monsoon:
```
Kharif: Sow June-July (with monsoon); Harvest Sept-Oct
        Rice, Maize, Cotton, Soybean, Jowar, Bajra
Rabi:   Sow Oct-Nov (after monsoon); Harvest March-April
        Wheat, Mustard, Barley, Gram
```

### Monsoon Mechanism Key Terms:
```
ITCZ → moves north in summer → triggers SW Monsoon
Mascarene High → source pressure system for SW Monsoon winds
Tibetan Plateau → heating strengthens monsoon circulation
Land = heats/cools FAST; Sea = heats/cools SLOWLY → pressure difference → winds
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Circular Queue full: (rear+1)%SIZE==front; empty: front==-1; max elements = SIZE-1
2. Deque = Double-Ended Queue; Input-restricted: insert rear only; Output-restricted: delete front only
3. deleteRear in Singly Linked List = O(N); in Doubly Linked List = O(1)
4. SW Monsoon: June 1 (Kerala onset) → June-Sept → 75-80% of India's rain; Bay of Bengal branch → Bihar
5. NE Monsoon: Oct-Dec → Tamil Nadu; Mawsynram = world's wettest; Rajasthan = driest; Kharif crops = rice/maize

---

*Next: Day 20 — Linked Lists: Singly, Doubly, Circular + Bihar Economy & Agriculture*
