# 📅 DAY 19 — BPSC TRE 4.0 TOPPER STUDY MATERIAL
## CS: Circular Queue & Deque | GS: India Climate & Monsoon
### 🎯 Target: TOPPER RANK | Phase 1 — Week 3

---

> **EXAM REMINDER:** Every question has 5 options (A/B/C/D/E).
> **Option D = "More than one of the above"** | **Option E = "None of the above"**
> 20–25% of correct answers are D or E. NEVER ignore them!

---

# ═══════════════════════════════════════════
# 🖥️ COMPUTER SCIENCE — CIRCULAR QUEUE & DEQUE
# ═══════════════════════════════════════════

---

## 📌 SECTION 1: RECAP — WHY DO WE NEED CIRCULAR QUEUE?

### The Problem With Linear Queue

```
LINEAR QUEUE — THE MEMORY WASTAGE PROBLEM:

 Index:  [0]   [1]   [2]   [3]   [4]   [5]
         [ ]   [ ]   [ ]   [30]  [40]  [50]
          ^                       ^
       FRONT                    REAR
          |
     Already deleted!
     WASTED SPACE ← Even though 3 cells are empty, 
                    we CANNOT reuse them in Linear Queue!

When rear = MAX_SIZE - 1:
→ Queue is declared FULL (OVERFLOW condition)
→ But positions 0,1,2 are EMPTY and WASTED!
→ This is the "False Overflow" or memory wastage problem!
```

### The Solution: Circular Queue

```
CIRCULAR QUEUE — RING BUFFER:

         [0]
        /   \
      [5]   [1]
      |       |
      [4]   [2]
        \   /
         [3]

Arrows show: After index 5, it WRAPS BACK to index 0!
rear = (rear + 1) % SIZE  ← This formula creates the ring!
front = (front + 1) % SIZE
```

**KEY PYQ FACT:** Circular Queue is also called **"Ring Buffer"**.
**Created to avoid:** Memory wastage / False Overflow in Linear Queue.

---

## 📌 SECTION 2: CIRCULAR QUEUE — ALL CONDITIONS

### The Critical Formulas (PYQ Hotspot!)

```
┌─────────────────────────────────────────────────────────────┐
│              CIRCULAR QUEUE CONDITIONS                       │
├─────────────────────────┬───────────────────────────────────┤
│ EMPTY Condition         │  front == rear == -1              │
│                         │  OR front == (rear + 1) % SIZE    │
├─────────────────────────┼───────────────────────────────────┤
│ FULL Condition          │  (rear + 1) % SIZE == front       │
├─────────────────────────┼───────────────────────────────────┤
│ Insert (Enqueue)        │  rear = (rear + 1) % SIZE         │
├─────────────────────────┼───────────────────────────────────┤
│ Delete (Dequeue)        │  front = (front + 1) % SIZE       │
├─────────────────────────┼───────────────────────────────────┤
│ Size of Queue           │  (rear - front + SIZE) % SIZE     │
└─────────────────────────┴───────────────────────────────────┘
```

### Visual: Enqueue and Dequeue in Circular Queue

**Initial State (SIZE = 6, Empty):**
```
front = -1, rear = -1
[ _ ][ _ ][ _ ][ _ ][ _ ][ _ ]
  0    1    2    3    4    5
```

**After Enqueue(10), Enqueue(20), Enqueue(30):**
```
front = 0, rear = 2
[10 ][20 ][30 ][ _ ][ _ ][ _ ]
  0    1    2    3    4    5
  ^              ^
front           rear
```

**After Dequeue(), Dequeue() (removing 10, 20):**
```
front = 2, rear = 2
[ _ ][ _ ][30 ][ _ ][ _ ][ _ ]
  0    1    2    3    4    5
             ^
          front = rear = 2
```

**After Enqueue(40), Enqueue(50), Enqueue(60), Enqueue(70), Enqueue(80):**
```
front = 2, rear = 1  ← rear wrapped around!
[70 ][80 ][30 ][40 ][50 ][60 ]
  0    1    2    3    4    5
       ^    ^
      rear  front

FULL Condition check: (rear + 1) % SIZE = (1 + 1) % 6 = 2 = front ✓ FULL!
```

---

## 📌 SECTION 3: CIRCULAR QUEUE OPERATIONS — STEP BY STEP

### Enqueue Algorithm:

```
ENQUEUE(CQ, item):
Step 1: Check OVERFLOW
        IF (rear + 1) % SIZE == front:
            PRINT "Queue is FULL — OVERFLOW!"
            RETURN

Step 2: IF front == -1 (first element ever):
            front = 0
            rear = 0
        ELSE:
            rear = (rear + 1) % SIZE

Step 3: CQ[rear] = item
Step 4: RETURN
```

### Dequeue Algorithm:

```
DEQUEUE(CQ):
Step 1: Check UNDERFLOW
        IF front == -1:
            PRINT "Queue is EMPTY — UNDERFLOW!"
            RETURN

Step 2: item = CQ[front]

Step 3: IF front == rear (only one element):
            front = -1
            rear = -1   ← Reset to empty state!
        ELSE:
            front = (front + 1) % SIZE

Step 4: RETURN item
```

### ⚠️ TRAP ALERT: BPSC PYQ Pattern
```
Q: What happens when front == rear in circular queue after dequeue?
→ Answer: Queue becomes EMPTY. Set front = rear = -1.
→ This is NOT the same as front == (rear + 1) % SIZE (which is FULL).
→ BPSC often confuses students between EMPTY and FULL conditions!
```

---

## 📌 SECTION 4: ADVANTAGES OF CIRCULAR QUEUE

```
┌────────────────────────────────────────────────────────────┐
│        CIRCULAR QUEUE vs LINEAR QUEUE                      │
├────────────────────────┬───────────────────────────────────┤
│ Feature                │ Circular Queue    Linear Queue    │
├────────────────────────┼───────────────────────────────────┤
│ Memory Utilization     │ Efficient ✓       Wasteful ✗      │
│ False Overflow         │ NOT possible ✓    Possible ✗      │
│ Wrap-around            │ YES ✓             NO ✗            │
│ Implementation         │ Slightly complex  Simple          │
│ Also called            │ Ring Buffer       Normal Queue     │
└────────────────────────┴───────────────────────────────────┘
```

### Real-World Applications of Circular Queue:
1. **CPU Scheduling** — Round Robin algorithm uses circular queue
2. **Traffic Light Control Systems** — Cyclic rotation
3. **Memory Buffering** — Audio/video streaming buffers
4. **Producer-Consumer Problem** — In OS

---

## 📌 SECTION 5: DEQUE (DOUBLE-ENDED QUEUE)

### What is Deque?

```
DEQUE = Double-Ended Queue
      = Insert AND Delete from BOTH ENDS (Front AND Rear)

Normal Queue:
Insert → [  ][  ][  ][  ] → Delete
         REAR              FRONT
         (only here)       (only here)

DEQUE:
Insert ←→ [  ][  ][  ][  ] ←→ Delete
          FRONT          REAR
          (both ends)    (both ends)
```

### Types of Deque:

```
┌─────────────────────────────────────────────────────────────┐
│                  TYPES OF DEQUE                             │
├───────────────────────┬─────────────────────────────────────┤
│ Input-Restricted      │ • Insert allowed at ONE end ONLY    │
│ Deque                 │ • Delete allowed at BOTH ends       │
│                       │ • Front = rear = restricted insert  │
├───────────────────────┼─────────────────────────────────────┤
│ Output-Restricted     │ • Insert allowed at BOTH ends       │
│ Deque                 │ • Delete allowed at ONE end ONLY    │
│                       │ • Think: Output goes from one side  │
└───────────────────────┴─────────────────────────────────────┘

MEMORY TRICK:
• Input-Restricted  = "I" → Input restricted → Insert restricted
• Output-Restricted = "O" → Output restricted → Delete restricted
```

### Deque Visual Diagram:

```
INPUT-RESTRICTED DEQUE:
                    Insert ONLY here
                         ↓
[  ] ←→ [  ] ←→ [  ] ←→ [  ]
 ↑                          ↑
Delete                    Delete
from here                from here

OUTPUT-RESTRICTED DEQUE:
Insert here              Insert here
    ↓                        ↓
[  ] ←→ [  ] ←→ [  ] ←→ [  ]
 ↑
Delete ONLY from here
```

---

## 📌 SECTION 6: DEQUE OPERATIONS & COMPLEXITY

### Operations Table:

```
┌───────────────────────────────────────────────────────────┐
│                 DEQUE OPERATIONS                          │
├──────────────────────────┬────────────────────────────────┤
│ Operation                │ Time Complexity                 │
├──────────────────────────┼────────────────────────────────┤
│ Insert at Front          │ O(1)                           │
│ Insert at Rear           │ O(1)                           │
│ Delete from Front        │ O(1)                           │
│ Delete from Rear         │ O(1) with Doubly Linked List   │
│ Delete from Rear         │ O(N) with Singly Linked List   │
│ Peek at Front/Rear       │ O(1)                           │
└──────────────────────────┴────────────────────────────────┘
```

### ⚠️ KEY PYQ FACT — TOPPER LEVEL:
```
Q: Why is "Delete from Rear" O(N) in Singly Linked List?

Answer: In a Singly Linked List, each node only has a pointer
        to the NEXT node. There is NO backward pointer.
        
        To delete the LAST node, you must:
        1. Start from HEAD (front)
        2. Traverse ALL the way to the SECOND-LAST node
        3. Set second-last's next = NULL
        
        This traversal takes O(N) time.
        
        With DOUBLY Linked List: O(1) because each node has
        a PREV pointer — you can reach second-last directly!

BPSC TRAP: "Delete from rear with singly linked list = O(N)"
           This is a frequently asked PYQ!
```

---

## 📌 SECTION 7: STACK vs QUEUE vs DEQUE — MASTER COMPARISON TABLE

```
┌──────────────────────────────────────────────────────────────────┐
│              COMPLETE COMPARISON TABLE (BPSC TOPPER LEVEL)       │
├──────────────┬──────────┬────────────────┬────────────────────── │
│ Feature      │ Stack    │ Queue          │ Deque                 │
├──────────────┼──────────┼────────────────┼───────────────────────┤
│ Order        │ LIFO     │ FIFO           │ Both possible         │
│ Insert End   │ Top only │ Rear only      │ Both ends             │
│ Delete End   │ Top only │ Front only     │ Both ends             │
│ Use for      │Recursion,│CPU scheduling, │Palindrome check,      │
│              │Undo ops  │BFS, spooling   │Sliding window         │
│ Overflow     │ Top=MAX  │ rear=MAX-1     │ Both ends full        │
│ Underflow    │ Top=-1   │ front=-1       │ Both ends empty       │
└──────────────┴──────────┴────────────────┴───────────────────────┘
```

---

## 📌 SECTION 8: PRIORITY QUEUE — BRIEF PREVIEW (PYQ CONNECTION)

```
Priority Queue ≠ Normal Queue (FIFO)
Priority Queue = Element with HIGHEST PRIORITY leaves first
               = NOT based on arrival order

Implementation:
┌─────────────────────────────────────────────────────────────┐
│ Best Implementation: BINARY HEAP                            │
│   • Min-Heap → Smallest element = Highest priority         │
│   • Max-Heap → Largest element = Highest priority          │
│ Applications: Dijkstra's algorithm, Huffman coding,        │
│               CPU scheduling                               │
└─────────────────────────────────────────────────────────────┘

BPSC PYQ: "Which data structure is best for Priority Queue?"
          Answer: Binary Heap (not sorted array, not linked list)
```

---

## 📌 SECTION 9: PYQ ANALYSIS — CIRCULAR QUEUE & DEQUE

### From TRE 1.0, 2.0, 3.0 Papers:

| PYQ Topic | Paper | Frequency |
|-----------|-------|-----------|
| Circular Queue full condition | TRE 1.0, 2.0 | High |
| Ring Buffer = Circular Queue | TRE 2.0 | Medium |
| Deque types (input/output restricted) | TRE 1.0, 3.0 | High |
| Delete from rear: Singly LL = O(N) | TRE 2.0, 3.0 | High |
| Why circular queue? Memory wastage | TRE 1.0 | High |
| Difference: empty vs full condition | TRE 3.0 | Medium |

### ⚡ QUICK REVISION — 10 MUST-REMEMBER FACTS:

```
1. Circular Queue = Ring Buffer (same thing, different names!)
2. Created to solve: MEMORY WASTAGE / False Overflow in Linear Queue
3. EMPTY Condition: front == rear == -1
4. FULL Condition: (rear + 1) % SIZE == front
5. Enqueue formula: rear = (rear + 1) % SIZE
6. Dequeue formula: front = (front + 1) % SIZE
7. Deque = Insert AND Delete from BOTH ends
8. Input-Restricted Deque: Insert from ONE end only
9. Output-Restricted Deque: Delete from ONE end only
10. Delete from rear in Singly LL = O(N) because no backward pointer!
```

---

# ═══════════════════════════════════════════
# 🌏 GENERAL STUDIES — INDIA CLIMATE & MONSOON
# ═══════════════════════════════════════════
> Reference: Lucent GK — Section 3.10 (Climate of India), Section 3.7 (Weather & Climate)

---

## 📌 SECTION 10: INDIA'S CLIMATE — OVERVIEW

### India is a TROPICAL MONSOON country:

```
INDIA'S CLIMATE TYPE:
┌─────────────────────────────────────────────────────────────┐
│ Climate Type: Tropical Monsoon                              │
│ Why? Most of India lies between Tropic of Cancer (23.5°N)  │
│      and the Equator → Tropical zone                       │
│ Monsoon = Arabic word "MAUSAM" meaning SEASON              │
│ Controlling factor: MONSOON WINDS                          │
└─────────────────────────────────────────────────────────────┘
```

### The 4 Seasons of India:

```
┌──────────────────────────────────────────────────────────────┐
│               INDIA'S 4 SEASONS (IMD Classification)        │
├───────────────┬────────────────┬──────────────────────────── │
│ Season        │ Months         │ Key Feature                 │
├───────────────┼────────────────┼─────────────────────────────┤
│ 1. Winter     │ Dec – Feb      │ NE trade winds, cold & dry  │
│ 2. Pre-Monsoon│ Mar – May      │ Hot & dry, dust storms (NW) │
│   (Hot Season)│                │ "Loo" wind in North India   │
│ 3. SW Monsoon │ Jun – Sep      │ Most rainfall (~75% annual) │
│   (Rainy)     │                │ Arabian Sea + Bay of Bengal │
│ 4. NE Monsoon │ Oct – Nov      │ Rain in Tamil Nadu, AP      │
│   (Retreating)│                │ Also called "winter monsoon"│
└───────────────┴────────────────┴─────────────────────────────┘
```

### KEY PYQ FACT: LOO WIND
```
LOO = Hot, dry, dusty wind
    = Blows in: North India & Pakistan
    = Blows in: Summer (May–June)
    = Direction: West to East
    = Can cause HEAT STROKE — dangerous!
```

---

## 📌 SECTION 11: THE MONSOON MECHANISM — HOW IT WORKS

### Step-by-Step Monsoon Formation:

```
SOUTHWEST MONSOON MECHANISM:

STEP 1: HEATING OF LAND (April-May)
        The Indian subcontinent heats up rapidly
        Land heats FASTER than sea
        Hot air rises → LOW PRESSURE created over India
        
        INDIA [HOT AIR RISING ↑]        INDIAN OCEAN [COOL]
              LOW PRESSURE                  HIGH PRESSURE
        
STEP 2: PRESSURE GRADIENT
        Air flows from HIGH pressure to LOW pressure
        Wind blows: Ocean → Land (from SW direction)
        
STEP 3: MOISTURE PICKUP
        Winds cross the warm Indian Ocean
        Pick up enormous MOISTURE (water vapor)
        
STEP 4: LANDFALL & RAINFALL
        Winds hit the Western Ghats → OROGRAPHIC RAINFALL
        Western slopes → Heavy rain (Windward side)
        Eastern slopes → Rain shadow zone (Leeward/Lee side)
        
STEP 5: ADVANCEMENT
        Two branches reach India in JUNE:
        ┌─────────────────────────────────────┐
        │ Arabian Sea Branch → Hits Kerala    │
        │                    → Western Ghats  │
        │                    → Reaches NW     │
        ├─────────────────────────────────────┤
        │ Bay of Bengal Branch → Hits Myanmar │
        │                      → NE India     │
        │                      → Gangetic Plain│
        └─────────────────────────────────────┘
```

### The Monsoon Arrives — Dates to Remember:

```
┌──────────────────────────────────────────────────────────────┐
│              MONSOON ARRIVAL DATES (PYQ HOTSPOT!)           │
├──────────────────────────────┬───────────────────────────────┤
│ Region                       │ Arrival Date                  │
├──────────────────────────────┼───────────────────────────────┤
│ Kerala (FIRST to receive)    │ 1st June (approx.)            │
│ Mumbai                       │ 10th June                     │
│ Delhi                        │ 29th June – 1st July          │
│ Bihar / Jharkhand            │ 10th – 15th June              │
│ All of India covered         │ By 15th July                  │
├──────────────────────────────┼───────────────────────────────┤
│ Withdrawal starts from       │ 1st September (NW India)      │
│ Withdrawal from Kerala       │ October end                   │
└──────────────────────────────┴───────────────────────────────┘

MEMORY TRICK: "Kerela Welcomes Monsoon on June 1st"
              KW = Kerala → Winter (June 1st entry point)
```

---

## 📌 SECTION 12: RAINFALL DISTRIBUTION IN INDIA

### Highest & Lowest Rainfall Areas:

```
┌──────────────────────────────────────────────────────────────┐
│            RAINFALL EXTREMES (PYQ REPEATED!)                │
├──────────────────────────┬───────────────────────────────────┤
│ HIGHEST Rainfall         │                                   │
│ Place                    │ Mawsynram, Meghalaya              │
│ State                    │ Meghalaya                         │
│ Avg Annual Rainfall      │ ~11,871 mm (WORLD'S HIGHEST)      │
│ Previous Record Holder   │ Cherrapunji (also in Meghalaya)   │
├──────────────────────────┼───────────────────────────────────┤
│ LOWEST Rainfall          │                                   │
│ Place                    │ Leh, Ladakh / Jaisalmer           │
│ Region                   │ Thar Desert / Cold Desert Ladakh  │
│ Avg Annual Rainfall      │ Less than 50 mm                   │
└──────────────────────────┴───────────────────────────────────┘

BIHAR SPECIFIC: Bihar receives GOOD rainfall from Bay of Bengal
branch of SW Monsoon (June-September)
Average annual rainfall in Bihar: 1000-1200 mm
```

### Rain Shadow Zone:

```
WINDWARD vs LEEWARD SIDE:

                    ↑ Moist Wind
         RAIN       |
         Heavy ↑    |    Lee (Rain Shadow)
              _____/\_____ 
             /  Western   \  
            /    Ghats     \  DRY
           /     (High      \ 
ARABIAN   /      Rainfall)   \  DECCAN
SEA       ✓                   X  PLATEAU
                               (Low Rainfall)

Western Ghats Windward side: Kerala, Goa, Konkan → Very HIGH rainfall
Western Ghats Leeward side: Deccan Plateau, Marathwada → LOW rainfall

BPSC TRAP: "Which state lies in rain shadow of Western Ghats?"
Answer: Parts of Maharashtra, Karnataka (Deccan Plateau side)
```

---

## 📌 SECTION 13: PRESSURE BELTS & WIND SYSTEMS

### Global Pressure Belts:

```
90°N ← Arctic → HIGH PRESSURE (Polar High)
60°N            LOW PRESSURE (Sub-polar Low)
30°N            HIGH PRESSURE (Sub-tropical High / Horse Latitudes)
 0°             LOW PRESSURE (Equatorial Low / Doldrums)
30°S            HIGH PRESSURE (Sub-tropical High)
60°S            LOW PRESSURE (Sub-polar Low)
90°S → Antarctic → HIGH PRESSURE (Polar High)
```

### Wind Systems:

```
┌──────────────────────────────────────────────────────────────┐
│                  MAJOR WIND SYSTEMS                         │
├────────────────┬─────────────────────────────────────────── │
│ Wind Name      │ Direction & Region                         │
├────────────────┼────────────────────────────────────────────┤
│ Trade Winds    │ 30° → 0° (towards Equator)                │
│                │ NE Trade Winds (N Hemisphere)              │
│                │ SE Trade Winds (S Hemisphere)              │
├────────────────┼────────────────────────────────────────────┤
│ Westerlies     │ 30° → 60° (towards poles)                 │
│                │ SW Westerlies (N Hemisphere)               │
│                │ NW Westerlies (S Hemisphere)               │
├────────────────┼────────────────────────────────────────────┤
│ Polar Easterly │ 90° → 60° (towards equator)               │
│                │ From Polar High → Sub-polar Low            │
└────────────────┴────────────────────────────────────────────┘

MEMORY TRICK: "Trade — Westerly — Polar" = T-W-P
               Corresponds to: 0-30, 30-60, 60-90 degrees
```

---

## 📌 SECTION 14: CYCLONES & EL NIÑO — PYQ TOPICS

### Cyclone vs Anticyclone:

```
┌──────────────────────────────────────────────────────────────┐
│             CYCLONE vs ANTICYCLONE                          │
├─────────────────────┬────────────────────────────────────── │
│ Feature             │ Cyclone        │ Anticyclone           │
├─────────────────────┼────────────────┼───────────────────────┤
│ Pressure Center     │ LOW Pressure   │ HIGH Pressure         │
│ Wind Direction (N)  │ Anticlockwise  │ Clockwise             │
│ Wind Direction (S)  │ Clockwise      │ Anticlockwise         │
│ Weather             │ Stormy, Rainy  │ Clear, Fair           │
│ Also called         │ Hurricane (Atl)│ -                     │
│                     │ Typhoon (Pac)  │                       │
└─────────────────────┴────────────────┴───────────────────────┘

BPSC PYQ: "In Northern Hemisphere, cyclone rotates ___?"
Answer: Anticlockwise (due to Coriolis effect)
```

### El Niño & La Niña:

```
EL NIÑO:
• Spanish for "The Boy/Christ Child"
• Unusual WARMING of Pacific Ocean waters (near Peru)
• Effect on India: WEAKER monsoon → DROUGHT conditions
• Occurs every 2-7 years
• India 2002 drought was linked to El Niño

LA NIÑA (opposite of El Niño):
• Unusual COOLING of Pacific Ocean waters
• Effect on India: STRONGER monsoon → Excess rainfall
• Floods in India more likely during La Niña years

INDIAN OCEAN DIPOLE (IOD):
• Temperature difference between W and E Indian Ocean
• Positive IOD → MORE rainfall in India
• Negative IOD → LESS rainfall in India
```

---

## 📌 SECTION 15: TYPES OF RAINFALL IN INDIA

```
┌──────────────────────────────────────────────────────────────┐
│                  TYPES OF RAINFALL                          │
├──────────────────┬───────────────────────────────────────── │
│ Type             │ Cause                   │ Example Region │
├──────────────────┼─────────────────────────┼───────────────-│
│ Orographic       │ Wind hits mountains      │ Western Ghats, │
│ (Relief)         │ → forced to rise → rain  │ NE India       │
├──────────────────┼─────────────────────────┼────────────────│
│ Convectional     │ Hot land heats air       │ Equatorial     │
│                  │ → air rises → condenses  │ regions, NE    │
│                  │ → heavy local rain       │ India summers  │
├──────────────────┼─────────────────────────┼────────────────│
│ Cyclonic         │ Air masses meet          │ Temperate      │
│ (Frontal)        │ → fronts form → rain     │ regions, W     │
│                  │                          │ disturbances   │
└──────────────────┴─────────────────────────┴────────────────┘

WESTERN DISTURBANCES:
• Extra-tropical cyclones from Mediterranean Sea
• Bring WINTER RAIN to NW India (Punjab, Haryana, UP, Bihar)
• IMPORTANT for RABI crops (wheat!)
• Bihar receives some Western Disturbance rainfall in winter
```

---

## 📌 SECTION 16: BIHAR — CLIMATE SPECIFIC FACTS (HIGH PYQ VALUE!)

```
┌──────────────────────────────────────────────────────────────┐
│              BIHAR CLIMATE — MUST KNOW FOR BPSC             │
├──────────────────────────────────────────────────────────────┤
│ Climate type: Sub-tropical Humid Monsoon                     │
│                                                              │
│ Summer (Apr-Jun): Very hot; max temp 40-45°C                │
│ "Loo" wind blows in Bihar in summer                         │
│                                                              │
│ Monsoon (Jun-Sep): Bay of Bengal branch brings rain         │
│ Annual rainfall: 1000-1200 mm (good for agriculture)        │
│                                                              │
│ Winter (Nov-Feb): Cold; influenced by Western Disturbances  │
│ Fog is common in Ganga plains during winter                 │
│                                                              │
│ HIGHEST RAINFALL DISTRICT IN BIHAR:                         │
│ → Kishanganj (far NE Bihar, near Nepal/Bengal border)       │
│ → Gets extra rainfall from Bay of Bengal + Himalayas       │
│                                                              │
│ LOWEST RAINFALL AREA IN BIHAR:                              │
│ → Gaya, Jehanabad area (semi-arid pockets in south Bihar)   │
│                                                              │
│ RIVERS in Bihar receive heavy rain in monsoon →             │
│ Kosi, Gandak, Bagmati, Kamla-Balan rivers flood annually   │
│ Kosi = "Sorrow of Bihar" due to repeated floods            │
└──────────────────────────────────────────────────────────────┘
```

---

## 📌 SECTION 17: CLIMATIC REGIONS OF INDIA

```
┌──────────────────────────────────────────────────────────────┐
│           CLIMATIC REGIONS OF INDIA (Trewartha's)           │
├───────────────────────┬──────────────────────────────────── │
│ Region/Climate Type   │ Area                                │
├───────────────────────┼─────────────────────────────────────┤
│ Tropical Rainforest   │ Western Ghats, Andaman & Nicobar   │
│ Tropical Savanna      │ Interior Peninsular India          │
│ Arid/Semi-arid        │ Rajasthan, Gujarat (Thar Desert)   │
│ Humid Subtropical     │ Gangetic Plains (Bihar!) + Punjab  │
│ Humid Tropical (NE)   │ Assam, Meghalaya → Highest rain    │
│ Alpine / Tundra       │ High altitude Himalayas            │
│ Coastal Tropical      │ Kerala, Konkan, Coastal TN         │
└───────────────────────┴─────────────────────────────────────┘
```

---

## 📌 SECTION 18: GS QUICK FACTS TABLE — TOPPER REVISION

```
┌──────────────────────────────────────────────────────────────┐
│         30 RAPID-FIRE FACTS — INDIA CLIMATE (PYQs)          │
├─────────────────────────────────────────────────────────────┤
│  1. India = Tropical Monsoon climate country                 │
│  2. Monsoon word from: Arabic "Mausam" = Season              │
│  3. SW Monsoon enters India via: Kerala (June 1)            │
│  4. 75% of India's annual rain from: SW Monsoon             │
│  5. Highest rainfall place: Mawsynram, Meghalaya            │
│  6. Previous record: Cherrapunji, Meghalaya                 │
│  7. Lowest rainfall: Leh-Ladakh / Thar Desert               │
│  8. Loo = Hot dry wind, North India, summer months         │
│  9. Rain Shadow = Deccan Plateau (leeward of W. Ghats)      │
│ 10. El Niño = Weak monsoon in India                         │
│ 11. La Niña = Strong monsoon in India                       │
│ 12. Western Disturbances = Winter rain to NW India         │
│ 13. NE Monsoon gives rain to: Tamil Nadu, Andhra Pradesh   │
│ 14. Cyclone in N Hemisphere rotates: Anticlockwise         │
│ 15. Anticyclone = High pressure, clear weather             │
│ 16. Kosi = Sorrow of Bihar (floods every year)             │
│ 17. Bihar gets rain from: Bay of Bengal branch            │
│ 18. Bihar climate type: Sub-tropical Humid Monsoon         │
│ 19. Orographic rain = Wind hits mountain → rises → rains  │
│ 20. Convectional rain = Hot surface heats air → rises     │
│ 21. Four seasons: Winter, Hot (Pre-monsoon), Monsoon, NE  │
│ 22. Monsoon retreats from NW India by: September           │
│ 23. IOD Positive = MORE rain in India                      │
│ 24. Kishanganj = Highest rainfall district in Bihar        │
│ 25. Thar Desert = Hottest desert of India                  │
│ 26. Coromandel Coast = Rain in October-December (NE moon.) │
│ 27. Arabian Sea branch hits: Western Ghats (Kerala first) │
│ 28. Bay of Bengal branch hits: NE India first             │
│ 29. Trade winds blow: From subtropical high → equator     │
│ 30. Westerlies blow: From subtropical high → 60° latitude │
└──────────────────────────────────────────────────────────────┘
```

---

# ═══════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 19
# ═══════════════════════════════════════════

> ⚠️ **INSTRUCTION:** Solve ALL 50 questions FIRST.
> **DO NOT look at answers until you have attempted every question.**
> Answers are given ONLY at the very END of this document.
> Option D = "More than one of the above" | Option E = "None of the above"

---

## 🖥️ CS QUESTIONS (Q1–Q25): Circular Queue & Deque

---

**Q1.** A Circular Queue is also commonly referred to as:
- (A) Linear Buffer
- (B) Ring Buffer
- (C) Double Buffer
- (D) More than one of the above
- (E) None of the above

---

**Q2.** The primary reason for using a Circular Queue over a Linear Queue is:
- (A) Faster insertion time
- (B) Avoiding memory wastage / false overflow
- (C) Simpler implementation
- (D) More than one of the above
- (E) None of the above

---

**Q3.** In a Circular Queue of SIZE = 8, the condition to check if the queue is FULL is:
- (A) rear == SIZE - 1
- (B) front == rear
- (C) (rear + 1) % SIZE == front
- (D) More than one of the above
- (E) None of the above

---

**Q4.** In a Circular Queue, the initial (EMPTY) state is indicated by:
- (A) front = 0, rear = 0
- (B) front = -1, rear = 0
- (C) front = -1, rear = -1
- (D) More than one of the above
- (E) None of the above

---

**Q5.** Consider a Circular Queue with SIZE = 5. Current state: front = 2, rear = 2. What does this imply?
- (A) Queue is FULL
- (B) Queue has exactly one element
- (C) Queue is EMPTY (just became empty after dequeue)
- (D) More than one of the above
- (E) None of the above

---

**Q6.** When we perform an ENQUEUE operation in a Circular Queue, the rear pointer is updated as:
- (A) rear = rear + 1
- (B) rear = (rear + 1) / SIZE
- (C) rear = (rear + 1) % SIZE
- (D) More than one of the above
- (E) None of the above

---

**Q7.** In a Circular Queue of SIZE = 6, if rear = 5 and we enqueue one more element, the new value of rear is:
- (A) 6
- (B) -1
- (C) 0
- (D) More than one of the above
- (E) None of the above

---

**Q8.** Which of the following statements about Deque is CORRECT?
- (A) Deque allows insertion from front and rear both
- (B) Deque allows deletion from front and rear both
- (C) Deque stands for Double-Ended Queue
- (D) More than one of the above
- (E) None of the above

---

**Q9.** In an Input-Restricted Deque:
- (A) Insertion is allowed from ONE end only
- (B) Deletion is allowed from BOTH ends
- (C) It is a type of Deque
- (D) More than one of the above
- (E) None of the above

---

**Q10.** In an Output-Restricted Deque:
- (A) Insertion is allowed from BOTH ends
- (B) Deletion is allowed from ONE end only
- (C) It restricts the output (delete) to one end
- (D) More than one of the above
- (E) None of the above

---

**Q11.** The time complexity of deleting an element from the REAR of a Deque implemented using a SINGLY Linked List is:
- (A) O(1)
- (B) O(log N)
- (C) O(N)
- (D) More than one of the above
- (E) None of the above

---

**Q12.** Why is deleting from the rear O(N) in a Singly Linked List implementation of Deque?
- (A) Because there is no backward (previous) pointer in SLL
- (B) We must traverse to find the second-last node
- (C) Both A and B are correct reasons
- (D) More than one of the above
- (E) None of the above

---

**Q13.** If Deque is implemented using a DOUBLY Linked List, deleting from the rear has time complexity:
- (A) O(N)
- (B) O(log N)
- (C) O(1)
- (D) More than one of the above
- (E) None of the above

---

**Q14.** Consider a Circular Queue with SIZE = 5 and the following sequence of operations:
Enqueue(10), Enqueue(20), Enqueue(30), Dequeue(), Dequeue(), Enqueue(40)
What is the value of front after these operations?
- (A) 0
- (B) 1
- (C) 2
- (D) More than one of the above
- (E) None of the above

---

**Q15.** Which of the following is/are applications of Circular Queue?
- (A) Round Robin CPU scheduling
- (B) Memory buffering in audio/video streaming
- (C) Traffic light control systems
- (D) More than one of the above
- (E) None of the above

---

**Q16.** Which data structure is used internally when a program implements RECURSION?
- (A) Queue
- (B) Stack
- (C) Deque
- (D) More than one of the above
- (E) None of the above

---

**Q17.** In a Linear Queue, the OVERFLOW condition occurs when:
- (A) front == -1
- (B) rear == MAX_SIZE - 1
- (C) front == rear
- (D) More than one of the above
- (E) None of the above

---

**Q18.** The false overflow problem in a Linear Queue means:
- (A) Queue gives overflow error even when empty positions exist at the front
- (B) Front positions are wasted and cannot be reused
- (C) Both A and B
- (D) More than one of the above
- (E) None of the above

---

**Q19.** Before performing a DEQUEUE operation, which condition must be checked?
- (A) OVERFLOW
- (B) UNDERFLOW
- (C) Both Overflow and Underflow
- (D) More than one of the above
- (E) None of the above

---

**Q20.** In a Deque, if we want to implement a STACK using Deque, which operations would we use?
- (A) Insert at front, Delete at front (LIFO behavior)
- (B) Insert at rear, Delete at rear (LIFO behavior)
- (C) Insert at front, Delete at rear
- (D) More than one of the above
- (E) None of the above

---

**Q21.** Which of the following best describes the Priority Queue?
- (A) Elements are served based on arrival order
- (B) Elements are served based on their assigned priority
- (C) Best implemented using Binary Heap
- (D) More than one of the above
- (E) None of the above

---

**Q22.** Consider a Circular Queue with SIZE = 4.
State after some operations: front = 1, rear = 3.
Is the queue FULL?
Check: (rear + 1) % SIZE = (3 + 1) % 4 = ?
- (A) No, because (3+1)%4 = 0 ≠ 1 (front), so NOT full
- (B) Yes, queue is full
- (C) Cannot be determined
- (D) More than one of the above
- (E) None of the above

---

**Q23.** After a Dequeue operation when the queue had exactly ONE element, what should front and rear be set to?
- (A) front = 0, rear = 0
- (B) front = -1, rear = -1
- (C) front = -1, rear = 0
- (D) More than one of the above
- (E) None of the above

---

**Q24.** Which of the following is NOT an application of Stack?
- (A) Expression evaluation (Infix to Postfix)
- (B) Function call management (Recursion)
- (C) Asynchronous data transfer between processes
- (D) More than one of the above
- (E) None of the above

---

**Q25.** A Deque supports which of the following operations?
- (A) insertFront() — insert at front
- (B) deleteFront() — delete from front
- (C) insertRear() and deleteRear()
- (D) More than one of the above
- (E) None of the above

---

## 🌏 GS QUESTIONS (Q26–Q50): India Climate & Monsoon

---

**Q26.** The word "Monsoon" is derived from:
- (A) Hindi word "Mausam"
- (B) Arabic word "Mausam" meaning "Season"
- (C) Portuguese word for rain
- (D) More than one of the above
- (E) None of the above

---

**Q27.** Which state in India receives the FIRST arrival of Southwest Monsoon?
- (A) Maharashtra
- (B) Goa
- (C) Kerala
- (D) More than one of the above
- (E) None of the above

---

**Q28.** The place in India with the HIGHEST annual rainfall is:
- (A) Cherrapunji, Meghalaya
- (B) Mawsynram, Meghalaya
- (C) Agumbe, Karnataka
- (D) More than one of the above
- (E) None of the above

---

**Q29.** Which of the following are branches of the Southwest Monsoon that enter India?
- (A) Arabian Sea Branch
- (B) Bay of Bengal Branch
- (C) Indian Ocean Branch
- (D) More than one of the above
- (E) None of the above

---

**Q30.** El Niño has which of the following effects on India?
- (A) Causes stronger monsoon and excess rainfall
- (B) Causes weaker monsoon leading to drought conditions
- (C) Has no effect on India's monsoon
- (D) More than one of the above
- (E) None of the above

---

**Q31.** The "LOO" wind in India is characterized as:
- (A) A hot, dry, and dusty wind
- (B) It blows in North India during summer months
- (C) It can cause heat stroke
- (D) More than one of the above
- (E) None of the above

---

**Q32.** What is the "Rain Shadow Zone" with respect to the Western Ghats?
- (A) The windward (western) side gets heavy rainfall
- (B) The leeward (eastern) side gets low rainfall
- (C) Deccan Plateau is in the rain shadow zone
- (D) More than one of the above
- (E) None of the above

---

**Q33.** Which of the following states receives rain from the Northeast Monsoon (Retreating Monsoon)?
- (A) Punjab
- (B) Tamil Nadu
- (C) Bihar
- (D) More than one of the above
- (E) None of the above

---

**Q34.** Western Disturbances are:
- (A) Extra-tropical cyclones originating from the Mediterranean Sea
- (B) Responsible for winter rainfall in North and Northwest India
- (C) Important for Rabi crop (wheat) cultivation
- (D) More than one of the above
- (E) None of the above

---

**Q35.** In the Northern Hemisphere, the direction of wind rotation in a CYCLONE is:
- (A) Clockwise
- (B) Anticlockwise
- (C) Can be either direction
- (D) More than one of the above
- (E) None of the above

---

**Q36.** Which of the following statements about India's seasons is CORRECT?
- (A) India has 4 seasons: Winter, Hot Season, SW Monsoon, Retreating Monsoon
- (B) SW Monsoon season is from June to September
- (C) About 75% of annual rainfall comes from SW Monsoon
- (D) More than one of the above
- (E) None of the above

---

**Q37.** La Niña conditions in the Pacific Ocean generally cause:
- (A) Drought in India
- (B) Stronger than normal monsoon in India
- (C) No change in India's rainfall
- (D) More than one of the above
- (E) None of the above

---

**Q38.** The Kosi River is called the "Sorrow of Bihar" because:
- (A) It changes its course frequently causing widespread floods
- (B) It flows through highly populated areas of Bihar
- (C) It causes annual floods affecting millions in Bihar
- (D) More than one of the above
- (E) None of the above

---

**Q39.** Which type of rainfall is caused when moist winds are forced to rise due to a mountain barrier?
- (A) Convectional Rainfall
- (B) Cyclonic Rainfall
- (C) Orographic (Relief) Rainfall
- (D) More than one of the above
- (E) None of the above

---

**Q40.** Which district of Bihar is known for receiving the HIGHEST rainfall?
- (A) Patna
- (B) Gaya
- (C) Kishanganj
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Which of the following correctly matches the global pressure belts?
- (A) Equator → Low Pressure (Doldrums)
- (B) 30°N/S → High Pressure (Horse Latitudes)
- (C) 60°N/S → Low Pressure (Sub-polar Low)
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Trade Winds blow from:
- (A) Sub-tropical High Pressure belts towards the Equator
- (B) The equator towards the poles
- (C) The poles towards the equator
- (D) More than one of the above
- (E) None of the above

---

**Q43.** India's climate is classified as:
- (A) Tropical Monsoon
- (B) Arid and Semi-arid throughout
- (C) Temperate in all regions
- (D) More than one of the above
- (E) None of the above

---

**Q44.** Which of the following statements about the Indian Ocean Dipole (IOD) is CORRECT?
- (A) Positive IOD leads to MORE rainfall in India
- (B) Negative IOD leads to LESS rainfall in India
- (C) IOD refers to temperature differences in Indian Ocean
- (D) More than one of the above
- (E) None of the above

---

**Q45.** Southwest Monsoon generally arrives in Delhi by:
- (A) 1st June
- (B) 15th June
- (C) Last days of June / 1st July
- (D) More than one of the above
- (E) None of the above

---

**Q46.** Bihar's climate is best described as:
- (A) Arid monsoon
- (B) Sub-tropical Humid Monsoon
- (C) Tropical Rainforest
- (D) More than one of the above
- (E) None of the above

---

**Q47.** Which of the following are correct about Cyclone and Anticyclone?
- (A) Cyclone = Low Pressure Center; Anticyclone = High Pressure Center
- (B) Cyclone brings stormy weather; Anticyclone brings fair weather
- (C) Hurricane and Typhoon are different names for cyclone in different oceans
- (D) More than one of the above
- (E) None of the above

---

**Q48.** The Retreating Monsoon (NE Monsoon) brings rainfall to which coast of India?
- (A) Malabar Coast (Western)
- (B) Coromandel Coast (Eastern — Tamil Nadu, South AP)
- (C) Konkan Coast
- (D) More than one of the above
- (E) None of the above

---

**Q49.** Which of the following is the CORRECT order of Southwest Monsoon arrival in India?
- (A) Delhi → Mumbai → Kerala
- (B) Kerala → Bihar → Delhi
- (C) Bihar → Kerala → Delhi
- (D) More than one of the above
- (E) None of the above

---

**Q50.** Mawsynram and Cherrapunji receive very high rainfall because:
- (A) They lie on the windward side of the Meghalaya Hills
- (B) Moist Bay of Bengal winds are forced to rise by the hills
- (C) They lie in the rain shadow zone
- (D) More than one of the above
- (E) None of the above

---

---

# ═══════════════════════════════════════════
# ✅ ANSWER KEY WITH EXPLANATIONS — DAY 19
# ═══════════════════════════════════════════

> **Only look here AFTER attempting all 50 questions!**
> Count your score. Target: 40+ out of 50 to be on TOPPER track.

---

## 🖥️ CS ANSWERS (Q1–Q25)

| Q | Answer | Key Explanation |
|---|--------|-----------------|
| Q1 | **(B)** | Circular Queue = Ring Buffer. This is a direct PYQ-level synonym. |
| Q2 | **(B)** | Main reason = avoid memory wastage / false overflow. Insertion time is NOT faster. |
| Q3 | **(C)** | Full condition: `(rear + 1) % SIZE == front`. NOT rear==SIZE-1 (that's linear queue). |
| Q4 | **(C)** | Empty state: `front = -1, rear = -1`. Both must be -1. |
| Q5 | **(B)** | front == rear but both are NOT -1, so there is EXACTLY ONE element in the queue. front==rear==-1 means empty. front==rear but ≠ -1 means one element. |
| Q6 | **(C)** | `rear = (rear + 1) % SIZE` — the modulo creates the circular wrapping. |
| Q7 | **(C)** | `(5 + 1) % 6 = 0`. Rear wraps from 5 back to 0 — that's the ring buffer behavior! |
| Q8 | **(D)** | All three statements (A, B, C) are correct about Deque. D = More than one. |
| Q9 | **(D)** | All three statements are correct for Input-Restricted Deque. D = More than one. |
| Q10 | **(D)** | All three statements (A, B, C) are correct for Output-Restricted Deque. D = More than one. |
| Q11 | **(C)** | O(N) — must traverse entire list from head to reach second-last node. |
| Q12 | **(D)** | Both A and B are correct reasons — they are actually the same reason stated differently. D = More than one. |
| Q13 | **(C)** | O(1) with Doubly LL — each node has PREV pointer → directly access second-last node. |
| Q14 | **(C)** | Initial: f=-1, r=-1. After Enq(10): f=0,r=0. Enq(20): f=0,r=1. Enq(30): f=0,r=2. Deq(): f=1,r=2. Deq(): f=2,r=2. Enq(40): r=(2+1)%5=3. Final front=2. |
| Q15 | **(D)** | All three (A, B, C) are correct applications. D = More than one. |
| Q16 | **(B)** | Recursion uses STACK (function call stack). This is a VERY COMMON PYQ. |
| Q17 | **(B)** | Linear Queue OVERFLOW: rear == MAX_SIZE - 1. |
| Q18 | **(D)** | Both A and B describe the same problem from different angles. D = More than one. |
| Q19 | **(B)** | Before DEQUEUE → check UNDERFLOW (is queue empty?). Before ENQUEUE → check OVERFLOW. |
| Q20 | **(D)** | Both A and B implement LIFO behavior (Stack using Deque). Both are valid. D = More than one. |
| Q21 | **(D)** | B and C are both correct (served by priority, best with Binary Heap). A is wrong (A describes normal Queue). D = More than one. |
| Q22 | **(A)** | (3+1)%4 = 0 ≠ 1 (front value). So NOT full. The queue has space. |
| Q23 | **(B)** | When last element is dequeued, reset to empty state: front = -1, rear = -1. |
| Q24 | **(C)** | Asynchronous data transfer = Queue application, NOT Stack. Stack = recursion, expression eval. |
| Q25 | **(D)** | All three options (A, B, C) are correct Deque operations. D = More than one. |

---

## 🌏 GS ANSWERS (Q26–Q50)

| Q | Answer | Key Explanation |
|---|--------|-----------------|
| Q26 | **(B)** | Arabic "Mausam" = Season. This is the origin of the word Monsoon. Direct PYQ. |
| Q27 | **(C)** | Kerala — SW Monsoon first hits Kerala around June 1st every year. |
| Q28 | **(B)** | Mawsynram holds the CURRENT world record. Cherrapunji held it previously. Both are in Meghalaya. |
| Q29 | **(D)** | Both (A) Arabian Sea Branch and (B) Bay of Bengal Branch are correct. D = More than one. |
| Q30 | **(B)** | El Niño = WEAKER monsoon = drought risk in India. La Niña = stronger monsoon. |
| Q31 | **(D)** | All three statements (A, B, C) about Loo wind are correct. D = More than one. |
| Q32 | **(D)** | All three statements (A, B, C) are correct about Rain Shadow Zone. D = More than one. |
| Q33 | **(B)** | Tamil Nadu (Coromandel Coast) gets most rain from NE Monsoon (Oct-Dec). |
| Q34 | **(D)** | All three statements (A, B, C) about Western Disturbances are correct. D = More than one. |
| Q35 | **(B)** | Northern Hemisphere cyclone rotates ANTICLOCKWISE (Coriolis effect deflects winds left in SH). Wait — Coriolis deflects RIGHT in NH. Winds flow INTO center (low pressure) and deflect RIGHT → resulting spiral is ANTICLOCKWISE. |
| Q36 | **(D)** | All three statements (A, B, C) are correct about India's seasons. D = More than one. |
| Q37 | **(B)** | La Niña = cooling of Pacific = stronger monsoon in India = more rainfall. |
| Q38 | **(D)** | Both A and C are correct (frequently changes course AND causes floods). D = More than one. |
| Q39 | **(C)** | Orographic (Relief) Rainfall = moist winds hit mountain → forced up → cool → rain. |
| Q40 | **(C)** | Kishanganj in NE Bihar receives highest rainfall — located near Bengal and Nepal border. |
| Q41 | **(D)** | All three statements (A, B, C) correctly describe pressure belts. D = More than one. |
| Q42 | **(A)** | Trade Winds: Sub-tropical High (30°N/S) → Equatorial Low (0°). Blow towards equator. |
| Q43 | **(A)** | India = Tropical Monsoon climate. Not arid throughout, not temperate throughout. |
| Q44 | **(D)** | All three statements (A, B, C) about IOD are correct. D = More than one. |
| Q45 | **(C)** | Delhi receives monsoon around June 29th – July 1st (last days of June typically). |
| Q46 | **(B)** | Bihar = Sub-tropical Humid Monsoon climate. Hot summers, good monsoon rainfall, cold winters. |
| Q47 | **(D)** | All three statements (A, B, C) are correct about cyclones and anticyclones. D = More than one. |
| Q48 | **(B)** | Coromandel Coast (Tamil Nadu, South Andhra Pradesh) — gets rain from NE Monsoon in Oct-Dec. |
| Q49 | **(B)** | Kerala (June 1) → Bihar (June 10-15) → Delhi (June 29-July 1). This is the correct sequence. |
| Q50 | **(D)** | Both A and B are correct — windward side + forced rising of moist Bay of Bengal winds. D = More than one. |

---

## 📊 YOUR SCORE ANALYSIS:

```
┌────────────────────────────────────────────────────┐
│           TOPPER SCORE TRACKER — DAY 19            │
├───────────────┬────────────────────────────────────┤
│ CS Score      │ ___ / 25                           │
│ GS Score      │ ___ / 25                           │
│ TOTAL         │ ___ / 50                           │
├───────────────┴────────────────────────────────────┤
│ 47–50  → TOPPER Level 🏆 Outstanding!              │
│ 42–46  → Excellent ✅ On track for rank!           │
│ 35–41  → Good ✅ Revise D/E option questions       │
│ 28–34  → Average ⚠️ Re-read concepts today         │
│ Below 28 → Needs Work ❌ Revise and retry tomorrow │
└────────────────────────────────────────────────────┘

NOTE: Count how many D/E answers you got WRONG.
If you got 5+ D/E questions wrong → Spend 15 min on
"Option D trap" pattern recognition tomorrow.
```

---

## 🌙 NIGHT REVISION — 5 BULLET POINTS (Write these from memory!)

```
CS:
1. Circular Queue = ________ Buffer; solves ________ wastage
2. FULL condition: ________ ; EMPTY condition: ________
3. Deque = insert/delete from ________ ends
4. Input-Restricted Deque = insert from ________ end only
5. Delete from rear in Singly LL = O(___) because ________

GS:
1. Monsoon word from: ________ , meaning ________
2. First state to get SW Monsoon: ________ on ________
3. Highest rainfall place in India: ________, ________
4. El Niño effect on India: ________ monsoon
5. Bihar's highest rainfall district: ________
```

---

## ⚡ DAY 19 — TOPPER CHECKLIST

- [ ] Read Circular Queue concepts (30 min)
- [ ] Understood full/empty conditions with diagrams
- [ ] Read Deque types with examples
- [ ] Understood why SLL deletion from rear = O(N)
- [ ] Read India Climate & Monsoon section
- [ ] Learned Bihar-specific climate facts
- [ ] Attempted all 50 practice questions
- [ ] Checked answers only after finishing
- [ ] Wrote 5-bullet night revision summary
- [ ] Score: ___ / 50

---

> 🎯 **DAY 20 PREVIEW:** Priority Queue + Real-world Queue Applications | GS: Indian Polity — Constitution Basics
> Come back tomorrow and say **"Day-20"** to continue your topper journey!

---
*Day 19 | BPSC TRE 4.0 Topper Study Plan | Phase 1 — Week 3*
*CS: Circular Queue & Deque | GS: India Climate & Monsoon*
