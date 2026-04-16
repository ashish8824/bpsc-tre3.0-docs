# 📅 BPSC TRE 4.0 — DAY 18 COMPLETE STUDY MODULE
### Queue Data Structure (FIFO) + India Geography — Peninsular Plateau
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Queue — FIFO, Operations, Linear Queue, Circular Queue Intro, Applications
> - Afternoon (1 hr): India Geography — Peninsular Plateau
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Queue Data Structure — Deep Conceptual Guide

---

## 🔷 SECTION 1: What is a Queue?

### Real-Life Analogy — The Bank Counter:
Imagine a **line at a bank counter**:
- People join the line from the **BACK** (rear)
- People are served from the **FRONT**
- The person who arrived FIRST is served FIRST → FIFO
- You CANNOT skip anyone in the middle
- Once served, person leaves from the front

```
Bank Queue (entering from right, served from left):

REAR (new people join here)         FRONT (served first)
         ↓                                ↓
   ┌─────────┬─────────┬─────────┬─────────┐
   │ Person4 │ Person3 │ Person2 │ Person1 │
   └─────────┴─────────┴─────────┴─────────┘
              ← ← ← ← ← movement direction ← ← ←

Person1 joined first → served first (FIFO)
Person4 joined last  → served last
```

### Other Real-Life Queue Examples:
```
1. Ticket counter line → first person = first ticket
2. Print spooler → first document sent = first printed
3. CPU scheduling → processes wait in queue
4. Supermarket checkout → first in line = first checked out
5. Traffic signal → first car = first to go
6. WhatsApp message delivery → messages sent in order received
7. Customer service call center → first caller = first answered
```

### Formal Definition:
A **queue** is a linear data structure that follows the **FIFO (First In, First Out)** principle — the element inserted FIRST is the element removed FIRST. Insertions happen at the **REAR** and deletions happen at the **FRONT**.

---

## 🔷 SECTION 2: FIFO Principle — The Core Concept

### FIFO = First In, First Out:
```
ENQUEUE order: A → B → C → D   (A enqueued first, D last)
DEQUEUE order: A → B → C → D   (A dequeued first — same order!)

Queue PRESERVES the order of insertion.
This is the exact OPPOSITE of a Stack which REVERSES order.
```

### FIFO vs LIFO Side-by-Side:
```
QUEUE (FIFO):                      STACK (LIFO):
┌───┬───┬───┬───┐                  ┌───┐ ← TOP
│ A │ B │ C │ D │                  │ D │
└───┴───┴───┴───┘                  ├───┤
  ↑               ↑                │ C │
FRONT           REAR               ├───┤
(remove here)   (add here)         │ B │
                                   ├───┤
A was added first → removed first  │ A │ ← BOTTOM
                                   └───┘
                                   D was added last → removed first
```

---

## 🔷 SECTION 3: Queue Representation Using Array

### Two Pointer System:
```
Queue uses TWO pointers (unlike Stack which uses only one):

front → index of the FIRST element (dequeue from here)
rear  → index of the LAST element  (enqueue here)

INITIAL STATE (empty queue):
front = -1
rear  = -1

Convention: front = rear = -1 means EMPTY queue
```

### Queue State Diagram:
```
Empty queue (MAX = 6):
front = -1, rear = -1
Index:  0      1      2      3      4      5
      ┌──────┬──────┬──────┬──────┬──────┬──────┐
      │  _   │  _   │  _   │  _   │  _   │  _   │
      └──────┴──────┴──────┴──────┴──────┴──────┘

After ENQUEUE 10, 20, 30:
front = 0, rear = 2
      ┌──────┬──────┬──────┬──────┬──────┬──────┐
      │  10  │  20  │  30  │  _   │  _   │  _   │
      └──────┴──────┴──────┴──────┴──────┴──────┘
          ↑                    ↑
        front=0              rear=2

After DEQUEUE (removes 10):
front = 1, rear = 2
      ┌──────┬──────┬──────┬──────┬──────┬──────┐
      │  _   │  20  │  30  │  _   │  _   │  _   │
      └──────┴──────┴──────┴──────┴──────┴──────┘
               ↑        ↑
            front=1  rear=2
```

---

## 🔷 SECTION 4: Queue Operations — Complete Guide

### All Operations at a Glance:

| Operation | Action | Condition Check | Time Complexity |
|-----------|--------|----------------|----------------|
| **Enqueue** | Insert at REAR | Check FULL first | O(1) |
| **Dequeue** | Remove from FRONT | Check EMPTY first | O(1) |
| **Peek/Front** | View front element | Check EMPTY first | O(1) |
| **isEmpty** | Is queue empty? | front == -1 | O(1) |
| **isFull** | Is queue full? | rear == MAX-1 | O(1) |

**ALL queue operations are O(1)** — same as Stack.

---

### Operation 1: ENQUEUE (Insertion at Rear)

```
Algorithm:
ENQUEUE(queue, front, rear, MAX, value):
  Step 1: Check full → if rear == MAX - 1 → OVERFLOW, stop
  Step 2: If empty (front==-1): set front = 0
  Step 3: Increment rear → rear = rear + 1
  Step 4: Insert → queue[rear] = value

Pseudocode:
void enqueue(int queue[], int &front, int &rear, int MAX, int value) {
    if (rear == MAX - 1) {
        cout << "Queue Overflow!";
        return;
    }
    if (front == -1) front = 0;   // first element
    rear++;
    queue[rear] = value;
}
```

### Operation 2: DEQUEUE (Deletion from Front)

```
Algorithm:
DEQUEUE(queue, front, rear):
  Step 1: Check empty → if front == -1 → UNDERFLOW, stop
  Step 2: Store value → value = queue[front]
  Step 3: If front == rear → only one element was there
            set front = -1, rear = -1 (back to empty state)
          Else: Increment front → front = front + 1
  Step 4: Return value

Pseudocode:
int dequeue(int queue[], int &front, int &rear) {
    if (front == -1) {
        cout << "Queue Underflow!";
        return -1;
    }
    int value = queue[front];
    if (front == rear) {
        front = -1; rear = -1;   // queue becomes empty
    } else {
        front++;
    }
    return value;
}
```

### Operation 3: PEEK (View Front, No Removal)

```
int peek(int queue[], int front) {
    if (front == -1) {
        cout << "Queue is empty!";
        return -1;
    }
    return queue[front];  // front NOT changed
}
```

### Operation 4: isEmpty

```
bool isEmpty(int front) {
    return (front == -1);
}
```

### Operation 5: isFull

```
bool isFull(int rear, int MAX) {
    return (rear == MAX - 1);
}
```

---

## 🔷 SECTION 5: Complete Dry Run — Enqueue & Dequeue

### Setup: Queue of MAX size 5

```
INITIAL STATE:
front = -1, rear = -1
[  _  |  _  |  _  |  _  |  _  ]
 [0]   [1]   [2]   [3]   [4]

─────────────────────────────────────────────────────
ENQUEUE 10:
  rear == -1 (empty) → set front=0
  rear becomes 0; queue[0] = 10
  front=0, rear=0
[ 10  |  _  |  _  |  _  |  _  ]
   ↑f,r

─────────────────────────────────────────────────────
ENQUEUE 20:
  rear becomes 1; queue[1] = 20
  front=0, rear=1
[ 10  | 20  |  _  |  _  |  _  ]
   ↑f    ↑r

─────────────────────────────────────────────────────
ENQUEUE 30:
  rear becomes 2; queue[2] = 30
  front=0, rear=2
[ 10  | 20  | 30  |  _  |  _  ]
   ↑f         ↑r

─────────────────────────────────────────────────────
DEQUEUE:
  value = queue[front] = queue[0] = 10
  front becomes 1
  front=1, rear=2   RETURNED: 10
[  _  | 20  | 30  |  _  |  _  ]
         ↑f    ↑r

─────────────────────────────────────────────────────
ENQUEUE 40:
  rear becomes 3; queue[3] = 40
  front=1, rear=3
[  _  | 20  | 30  | 40  |  _  ]
         ↑f          ↑r

─────────────────────────────────────────────────────
ENQUEUE 50:
  rear becomes 4; queue[4] = 50
  front=1, rear=4
[  _  | 20  | 30  | 40  | 50  ]
         ↑f                ↑r

─────────────────────────────────────────────────────
ENQUEUE 60 (attempt):
  rear == MAX-1 == 4 → OVERFLOW! Cannot enqueue 60.
  But notice: index [0] is EMPTY — memory wasted!
  ← THIS IS THE LINEAR QUEUE PROBLEM ←
```

---

## 🔷 SECTION 6: Overflow & Underflow

### Queue Overflow:
```
OVERFLOW condition:  rear == MAX - 1
Meaning: The rear pointer has reached the last index.
Action: Print "Queue Overflow", do NOT enqueue.

⚠️ NOTE: In linear queue, overflow can occur even when
         the queue is not truly full — there may be empty
         slots at the beginning (wasted by dequeue operations)!
         → This is the MAIN LIMITATION of linear queue.
```

### Queue Underflow:
```
UNDERFLOW condition:  front == -1 (queue is empty)
Meaning: No elements in the queue to dequeue.
Action: Print "Queue Underflow", do NOT dequeue.
```

### 🚨 PYQ TRAP #1: Linear Queue Limitation
> In a linear queue of size N, even if (N-1) elements have been dequeued, the system reports OVERFLOW when rear == N-1, because the rear pointer never moves backward. The vacated front positions are wasted. This is why **Circular Queue** was invented.

---

## 🔷 SECTION 7: Linear Queue Limitation & Why Circular Queue?

### The Problem Visualized:
```
Queue MAX = 5, after multiple enqueue + dequeue operations:

[ _ | _ | _ | 40 | 50 ]
               ↑f    ↑r
front=3, rear=4

Now try ENQUEUE 60:
  rear == 4 == MAX-1 → OVERFLOW reported!
  BUT indices 0, 1, 2 are EMPTY (wasted)

This is FALSE OVERFLOW in linear queue.
```

### The Solution — Circular Queue:
```
In a Circular Queue:
  → After reaching the last index, rear wraps around to index 0
  → Uses MODULO arithmetic: rear = (rear + 1) % MAX
  → Similarly: front = (front + 1) % MAX after dequeue
  → The queue is truly full only when NO slots are empty
  → Eliminates the false overflow problem of linear queue

CIRCULAR QUEUE full condition:
  (rear + 1) % MAX == front  ← this means queue is full

CIRCULAR QUEUE empty condition:
  front == rear  (both at same position, no elements)
  or front == -1 (initial convention)
```

### Circular Queue Visual:
```
Circular Queue of size 6 (indices 0-5):

        0
     5     1
   4          2
     3     (...)
        
Elements wrap around:
After index 5 is full → next insertion goes to index 0
(if front has moved away from 0)
```

### 🚨 PYQ TRAP #2: Circular vs Linear Queue
> Linear Queue: Full when `rear == MAX-1` (may have empty slots)
> Circular Queue: Full when `(rear+1) % MAX == front` (truly full)
> Circular Queue solves the MEMORY WASTAGE problem of linear queue.

---

## 🔷 SECTION 8: Types of Queues

```
TYPES OF QUEUES:
│
├── 1. Simple (Linear) Queue
│      → Basic FIFO, insert at rear, delete from front
│      → Problem: memory wastage (false overflow)
│
├── 2. Circular Queue
│      → Rear wraps around using modulo: (rear+1) % MAX
│      → Solves false overflow
│      → Most efficient for fixed-size queue
│
├── 3. Double-Ended Queue (Deque — pronounced "deck")
│      → Insert and delete from BOTH ends
│      → More flexible than simple queue
│      → Two types: Input-restricted, Output-restricted
│
└── 4. Priority Queue
       → Elements have priorities
       → Highest priority element dequeued first
       → Used in Dijkstra's algorithm, Huffman coding
       → NOT strictly FIFO — order depends on priority
```

### 🚨 PYQ TRAP #3: Priority Queue
> In a **Priority Queue**, the element with the HIGHEST priority is served first — not necessarily the one that arrived first. This violates FIFO. Priority queue is used in CPU scheduling (preemptive), Dijkstra's shortest path algorithm, and Huffman encoding.

---

## 🔷 SECTION 9: Applications of Queue

### 1. CPU Scheduling
```
When multiple processes want CPU time:
→ Processes enter a READY QUEUE (waiting for CPU)
→ CPU serves them in order of arrival (FCFS - First Come First Served)
→ FIFO queue manages the order
→ Round Robin scheduling also uses a circular queue
```

### 2. Print Spooling
```
Multiple users send print jobs to a shared printer:
→ Jobs enter a PRINT QUEUE (spool)
→ Printer serves them FIFO — first job sent = first printed
→ Users don't have to wait for the printer to be free to send jobs
```

### 3. BFS (Breadth-First Search)
```
Graph traversal algorithm:
→ Start at source node
→ Visit all neighbors first (level by level)
→ Uses a QUEUE to track which node to visit next
→ Enqueue neighbors; dequeue and visit next node
→ Guarantees SHORTEST PATH in unweighted graphs
```

### 4. Asynchronous Data Transfer
```
When sender and receiver operate at different speeds:
→ Data is stored in a BUFFER QUEUE
→ Producer (sender) enqueues data when ready
→ Consumer (receiver) dequeues when ready
→ Examples: keyboard buffer, IO buffers, network packet queues
→ Classic producer-consumer problem uses Queue
```

### 5. Other Applications
```
→ Handling of interrupts in operating systems
→ Web server request handling
→ Shared resource management (database connections)
→ Cashier billing system
→ Call center systems
→ Traffic management at signals
```

---

## 🔷 SECTION 10: Non-Applications (Exam Traps)

### What is NOT a Queue Application:

| Task | Correct Structure | Why NOT Queue |
|------|------------------|---------------|
| Recursion | Stack | LIFO — last call returns first |
| Balancing of symbols `{[()]}` | Stack | Match latest opening bracket first |
| Undo operation | Stack | Undo most recent action = LIFO |
| DFS (Depth-First Search) | Stack | Go deep, then backtrack = LIFO |
| Browser back button | Stack | Last page = first back |

### 🚨 PYQ TRAP #4 — Most Tested:
> **"Balancing of symbols uses STACK, not Queue"**
> **"Recursion uses STACK, not Queue"**
> **"Asynchronous data transfer uses QUEUE, not Stack"**
> These three are the most frequently tested distinctions in BPSC TRE CS.

---

## 🔷 SECTION 11: Stack vs Queue — Master Comparison

```
Feature              STACK                      QUEUE
────────────────────────────────────────────────────────────
Principle            LIFO                       FIFO
Real example         Plate stack                Bank line / ticket queue
Ends used            ONE end (TOP)              TWO ends (FRONT & REAR)
Insert               PUSH at top                ENQUEUE at rear
Delete               POP from top               DEQUEUE from front
Pointer(s)           top (one pointer)          front AND rear (two pointers)
Empty condition      top == -1                  front == -1
Full condition       top == MAX-1               rear == MAX-1 (linear)
Empty/Full check     One comparison             One/two comparisons
Applications         Recursion, Undo, DFS,      BFS, Scheduling,
                     Expression eval,           Async transfer,
                     Balancing                  Print spooling
Order preservation   REVERSES order             PRESERVES order
```

---

## 📊 VISUAL SUMMARY — Queue Operations Flow

```
                QUEUE (FIFO)
                     │
       ┌─────────────┼─────────────┐
       │             │             │
   ENQUEUE       DEQUEUE        PEEK
   at REAR       from FRONT     (no removal)
   rear++        front++        return queue[front]
   O(1)          O(1)           O(1)
       │             │
  Check FULL    Check EMPTY
  rear==MAX-1   front==-1
       │             │
  OVERFLOW      UNDERFLOW

LINEAR QUEUE PROBLEM:
  rear==MAX-1 even if front has moved → WASTED SPACE
  Solution: CIRCULAR QUEUE (rear = (rear+1)%MAX)

TYPES: Simple → Circular → Deque → Priority Queue
```

---
---

# PART 2: GENERAL STUDIES
## 🗺️ India Geography — The Peninsular Plateau

---

## 🔷 WHY THIS MATTERS FOR BPSC TRE:
- Peninsular Plateau questions appear in every geography section
- Rivers, minerals, geological age are common PYQ topics
- Deccan Plateau, Vindhyas, and Satpura are high-frequency topics

---

## 🔷 THE PENINSULAR PLATEAU — BIG PICTURE

### What is the Peninsular Plateau?
```
The Peninsular Plateau is the OLDEST and most STABLE landmass of India.
It forms the core of the Indian subcontinent.

KEY CHARACTERISTICS:
→ Made of ancient IGNEOUS and METAMORPHIC rocks (Precambrian era)
→ Average elevation: 600–900 metres above sea level
→ Broadly triangular shape with apex pointing south
→ Divided by Narmada River into TWO main parts:
   NORTH = Central Highlands
   SOUTH = Deccan Plateau
```

### Location:
```
PENINSULAR PLATEAU occupies:
  → Most of central and southern India
  → Bounded by:
      North:   Aravalli Range + Bundelkhand + Chota Nagpur Plateau
      West:    Western Ghats
      East:    Eastern Ghats
      South:   Tip of Indian peninsula (Kanyakumari)
  → Covers: MP, Maharashtra, AP, Telangana, Karnataka, TN,
            Jharkhand, Chhattisgarh (major portion)
```

---

## 🔷 PART A: CENTRAL HIGHLANDS

### Definition:
```
The part of the Peninsular Plateau NORTH of the Narmada River
is called the CENTRAL HIGHLANDS.

Key sub-regions:
1. Malwa Plateau     → western part (Madhya Pradesh/Rajasthan)
2. Bundelkhand       → northern part (MP/UP border)
3. Baghelkhand       → eastern part (MP/Chhattisgarh)
4. Chota Nagpur Plateau → eastern extension
```

### Malwa Plateau:
```
Location:  Western part of Central Highlands
           Covers MP, Gujarat, Rajasthan border areas
Elevation: 300–600 m
Bounded by:
  North  → Aravalli Range
  South  → Vindhya Range
  West   → Gujarat plains
Rivers:   Chambal, Betwa, Ken (all tributaries of Yamuna — flow NORTH)
Soil:     Black cotton soil (good for agriculture)
Crops:    Soybean, wheat, cotton
```

### Chota Nagpur Plateau:
```
Location:  Jharkhand, extending into West Bengal, Odisha, Chhattisgarh
Elevation: 700–1,000 m (higher part)
Highest:   Parasnath Hill (1,350 m) — also sacred Jain pilgrimage site

MINERAL WEALTH — MOST IMPORTANT EXAM FACT:
→ Called the "MINERAL HEARTLAND" of India
→ Coal:   Jharia, Raniganj, Bokaro, Giridih coalfields
→ Iron ore: Noamundi, Chiria (among India's largest deposits)
→ Copper: Singhbhum (Jaduguda area)
→ Mica:   Bihar-Jharkhand region (India's top mica producer)
→ Uranium: Jaduguda (Jharkhand) — India's first uranium mine
→ Manganese, Bauxite, Limestone also found

Why so mineral-rich?
→ Very old Precambrian igneous/metamorphic rocks
→ Geological processes concentrated minerals here
→ Called the "Ruhr of India" (Ruhr = Germany's industrial heartland)
```

### Vindhya Range:
```
Location:   Runs east-west, separating Central Highlands from Deccan
States:     MP, UP, Rajasthan border
Significance:
→ Acts as watershed between Indo-Gangetic Plain and Deccan Plateau
→ Historically: "Vindhyas" = traditional divide between North and South India
→ Vindhya Scarp (steep northern face) faces Indo-Gangetic plain
→ Rivers: Narmada and Son flow from Amarkantak (Vindhya-Satpura junction)

AMARKANTAK — KEY JUNCTION:
→ Where Vindhya and Satpura ranges meet
→ Source of NARMADA (flows WEST) and SON (flows EAST) — same origin!
→ This is a major PYQ fact
```

### Satpura Range:
```
Location:   Parallel to Vindhyas (south of Vindhyas), separating
            Narmada and Tapi valleys
States:     MP, Maharashtra border
Highest:    Dhupgarh (1,350 m) — highest peak of Satpura, also highest
            in MP (Madhya Pradesh)
Rivers:     Between Narmada (north) and Tapi (south)
Forest:     Satpura Tiger Reserve, Pachmarhi Hill Station
Pachmarhi:  Only hill station in Madhya Pradesh
            UNESCO Biosphere Reserve
```

### 🚨 PYQ TRAP: Amarkantak
> **Amarkantak** is the source of BOTH the Narmada (flows west to Arabian Sea) and the Son (flows east to Ganga). Same origin, completely OPPOSITE directions. Very frequent exam question.

---

## 🔷 PART B: DECCAN PLATEAU

### Overview:
```
The part of the Peninsular Plateau SOUTH of the Narmada River
is called the DECCAN PLATEAU.

"Deccan" comes from Sanskrit "Dakshin" = South
Largest plateau in India (and one of the largest in the world)
Tilts slightly from WEST to EAST (so rivers flow east → Bay of Bengal)
```

### Boundaries:
```
DECCAN PLATEAU:
  West:   Western Ghats (highest edge)
  East:   Eastern Ghats (lower edge)
  North:  Satpura, Vindhya, Narmada valley
  South:  Nilgiri Hills (where Eastern + Western Ghats meet)

The plateau is HIGHER in the west (near Western Ghats)
and LOWER in the east (near Bay of Bengal coast)
→ This is why rivers flow WEST to EAST on the plateau
```

### Sub-divisions of Deccan Plateau:

#### 1. Maharashtra Plateau (Lava/Basalt Region):
```
Location:  Maharashtra, northern Karnataka
Rock type: BASALT (volcanic) — Deccan Traps
Soil:      REGUR (Black Cotton Soil) — world's most extensive
Crops:     Cotton, sugarcane, sorghum (jowar)
Geology:   Deccan Volcanic Province — massive lava outpourings
           ~65 million years ago (Cretaceous-Paleogene boundary)
           This coincided with Dinosaur extinction!
```

### 🚨 PYQ TRAP: Regur Soil
> **Regur Soil = Black Cotton Soil** is formed from weathering of Deccan Trap basalt rock. It is:
> - Self-ploughing (shrinks and cracks in summer, swells when wet)
> - Retains moisture well → ideal for cotton
> - Found in Maharashtra, Gujarat, MP, and parts of AP
> - Also called "Black Lava Soil"

#### 2. Karnataka Plateau (Mysore Plateau):
```
Location:  Karnataka
Elevation: 600–900 m
Rocks:     Ancient gneiss and granite (very old Precambrian rocks)
Minerals:  Gold (Kolar Gold Fields — KGF), manganese, iron ore
Crops:     Coffee, sandalwood, silk (Mysore = India's silk capital)
Key fact:  Kolar Gold Fields (KGF), Karnataka — historically India's
           richest gold mine (now mostly depleted)
           Famous "KGF" movie references this!
```

#### 3. Telangana Plateau:
```
Location:  Telangana, northern AP
Rivers:    Godavari, Krishna, Tungabhadra
Elevation: 500–600 m
Features:  Rocky terrain, scrub forests
```

#### 4. Tamil Nadu Plateau (Tamilnadu uplands):
```
Location:  Interior Tamil Nadu
Features:  Deccan continues into Tamil Nadu uplands
           Coimbatore plateau (important for cotton textiles)
```

---

## 🔷 RIVERS OF THE PENINSULAR PLATEAU

### East-Flowing Rivers (Bay of Bengal):
```
These rivers flow from the WESTERN GHATS eastward, crossing the
Deccan Plateau and Eastern Ghats into Bay of Bengal.

River      Origin                  Mouth
────────────────────────────────────────────────────────
Mahanadi   Chhattisgarh (Sihawa)  Paradip, Odisha
Godavari   Nasik, Maharashtra     Rajahmundry, AP
           → LONGEST peninsular river, "Dakshin Ganga"
           → Also called "Vridha Ganga" (old Ganga)
Krishna    Mahabaleshwar (Sahyadri) Hamsaladeevi, AP
Kaveri     Talakaveri, Karnataka  Cuddalore area, Tamil Nadu
           → Called "Dakshin Ganga" or "Ponni" in Tamil
Tungabhadra Tributary of Krishna, Karnataka
```

### West-Flowing Rivers (Arabian Sea) — UNIQUE:
```
Most peninsular rivers flow EAST. Only TWO major ones flow WEST:

River      Origin              Mouth/Sea
────────────────────────────────────────────────────────
Narmada    Amarkantak (MP)     Gulf of Khambhat (Arabian Sea)
Tapi       Multai, Betul (MP)  Gulf of Khambhat (Arabian Sea)

WHY do Narmada and Tapi flow WEST?
→ They flow through RIFT VALLEYS (tectonic fault valleys)
   between the Vindhya and Satpura ranges
→ The rift structure tilts the land WESTWARD here
→ They do NOT form deltas (unlike east-flowing rivers)
   → They form ESTUARIES instead

KEY EXAM FACT: Narmada and Tapi = west-flowing = rift valley rivers
               = no delta = estuary at mouth
```

### 🚨 PYQ TRAP: Narmada/Tapi = Rift Valley
> Narmada flows through a **rift valley** (graben), not a normal valley carved by erosion. Both Narmada and Tapi flow through structural depressions (rifts) between parallel fault lines. They DO NOT have deltas — they have **estuaries** at their mouths.

---

## 🔷 MINERAL RESOURCES OF PENINSULAR PLATEAU

```
Region              Minerals              States
──────────────────────────────────────────────────────────
Chota Nagpur        Coal, Iron, Copper,   Jharkhand, WB
(Mineral heartland) Mica, Uranium         Odisha, Chhattisgarh
Deccan Trap area    Manganese, Bauxite    Maharashtra, AP
Karnataka           Gold (KGF), Manganese Karnataka
Vindhyan region     Limestone, Coal       MP
Rajasthan fringe    Lead-Zinc (Zawar)     Rajasthan
                    Copper (Khetri)
```

---

## 🔷 GEOLOGICAL IMPORTANCE

```
AGE: Peninsular Plateau = OLDEST part of India
  → Precambrian era rocks (more than 540 million years old)
  → Part of the ancient Gondwana supercontinent
  → India "drifted" northward from Gondwana → collided with Asia
    → Himalayas formed from this collision
  → Peninsular plateau remained geologically STABLE (no earthquakes)

DECCAN TRAPS:
  → Enormous volcanic lava outflow ~65 million years ago
  → Covered about 500,000 sq km of Maharashtra/Gujarat/MP
  → Created basalt rock → weathered to form Regur (black) soil
  → Associated with mass extinction (dinosaurs?)
```

---

## 🔷 MEMORY TRICKS

### Two Main Parts:
```
"Narmada DIVIDES the Peninsular Plateau"
North of Narmada → Central Highlands (Malwa, Chota Nagpur)
South of Narmada → Deccan Plateau (Maharashtra, Karnataka, AP, TN)
```

### Plateaus Quick Memory — "MCK T" (Maharashtra, Karnataka, Chota Nagpur, Telangana):
```
M = Maharashtra Plateau → Basalt, Regur soil, Cotton
C = Chota Nagpur → Coal, Copper, Mica, Uranium (Mineral heartland)
K = Karnataka (Mysore) → Gold (KGF), Coffee, Silk
T = Telangana → Godavari, Krishna rivers
```

### West-Flowing Rivers Memory:
```
Only TWO major west-flowing peninsular rivers:
"No Trees (Narmada + Tapi)" → flow to ARABIAN SEA
All others flow EAST to BAY OF BENGAL
```

### River Nicknames:
```
Godavari = "Dakshin Ganga" / "Vridha Ganga" (South Ganga)
Kaveri   = "Dakshin Ganga" / "Ponni" (in Tamil)
Narmada  = "Life Line of Madhya Pradesh"
Son      = "Sone" (Gold) — from Amarkantak
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Queue Operations, FIFO, Overflow/Underflow, Applications, Circular Queue

---

**Q1.** What does FIFO stand for in the context of Queue?
(A) First Input, Final Output
(B) First In, First Out
(C) Fixed Index, Forward Order
(D) More than one of the above
(E) None of the above

---

**Q2.** In a Queue, elements are inserted at the _____ and deleted from the _____.
(A) Front; Rear
(B) Rear; Rear
(C) Rear; Front
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the initial value of BOTH `front` and `rear` pointers in an empty queue?
(A) 0 and 0
(B) -1 and -1
(C) 0 and -1
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the time complexity of the ENQUEUE operation in a queue?
(A) O(n)
(B) O(log n)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q5.** In a linear queue of MAX size 5, after how many enqueue operations does `rear` reach MAX-1 (index 4)?
(A) 4
(B) 5
(C) 6
(D) More than one of the above
(E) None of the above

---

**Q6.** The OVERFLOW condition in a linear queue is:
(A) front == -1
(B) rear == MAX - 1
(C) front == rear
(D) More than one of the above
(E) None of the above

---

**Q7.** The UNDERFLOW condition in a queue is:
(A) rear == MAX
(B) front == rear
(C) front == -1
(D) More than one of the above
(E) None of the above

---

**Q8.** Elements are enqueued in order A, B, C, D. What is the order in which they are dequeued?
(A) D, C, B, A
(B) A, B, C, D
(C) A, D, C, B
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following is the main LIMITATION of a linear queue?
(A) It cannot store more than 5 elements
(B) Memory wastage — false overflow when front has moved forward
(C) It does not support insertion at rear
(D) More than one of the above
(E) None of the above

---

**Q10.** A Circular Queue solves the linear queue problem by:
(A) Increasing the size of the array automatically
(B) Using modulo arithmetic to wrap rear around to index 0
(C) Deleting old elements automatically
(D) More than one of the above
(E) None of the above

---

**Q11.** In a Circular Queue of size MAX, the rear pointer is updated as:
(A) rear = rear + 1
(B) rear = rear % MAX
(C) rear = (rear + 1) % MAX
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following is a correct APPLICATION of a Queue?
(A) Undo operation in an editor
(B) Recursive function call management
(C) CPU scheduling (First Come First Served)
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following uses a QUEUE (not a Stack)?
(A) Balancing of symbols like `{[()]}`
(B) BFS (Breadth-First Search)
(C) Tower of Hanoi
(D) More than one of the above
(E) None of the above

---

**Q14.** Asynchronous data transfer between a producer and consumer is handled using:
(A) Stack
(B) Binary Tree
(C) Queue (buffer)
(D) More than one of the above
(E) None of the above

---

**Q15.** Which type of queue allows insertion and deletion from BOTH ends?
(A) Priority Queue
(B) Circular Queue
(C) Deque (Double-Ended Queue)
(D) More than one of the above
(E) None of the above

---

**Q16.** In a Priority Queue, the order of deletion is based on:
(A) Insertion order (FIFO)
(B) Priority of the element (highest priority first)
(C) Alphabetical order
(D) More than one of the above
(E) None of the above

---

**Q17.** How many pointers are required in an array-based Queue implementation (compared to Stack)?
(A) Stack uses 1 pointer (top); Queue uses 2 pointers (front and rear)
(B) Both use 1 pointer
(C) Queue uses 1 pointer; Stack uses 2
(D) More than one of the above
(E) None of the above

---

**Q18.** After 3 enqueues and 1 dequeue in a queue (initially empty), what are the values of front and rear?
(A) front=0, rear=2
(B) front=1, rear=2
(C) front=0, rear=3
(D) More than one of the above
(E) None of the above

---

**Q19.** The print spooler in an operating system uses which data structure?
(A) Stack
(B) Queue
(C) Linked List
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following is TRUE about a Queue?
(A) Queue reverses the order of elements
(B) Queue preserves the order of elements (FIFO)
(C) Queue is used for DFS traversal
(D) More than one of the above
(E) None of the above

---

**Q21.** BFS (Breadth-First Search) uses which data structure?
(A) Stack
(B) Queue
(C) Priority Queue
(D) More than one of the above
(E) None of the above

---

**Q22.** In a linear queue, if MAX=6, front=3, rear=5, how many elements are in the queue?
(A) 5
(B) 3
(C) 2 (indices 3 and 4 and 5 = rear-front+1 = 3)
(D) More than one of the above
(E) None of the above

---

**Q23.** When the only element in a queue is dequeued, the queue should be reset to:
(A) front = 0, rear = 0
(B) front = -1, rear = -1
(C) front = -1, rear = 0
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following correctly compares Stack and Queue?
(A) Stack uses FIFO; Queue uses LIFO
(B) Both Stack and Queue use LIFO
(C) Stack uses LIFO; Queue uses FIFO
(D) More than one of the above
(E) None of the above

---

**Q25.** Round Robin CPU scheduling uses which type of queue?
(A) Simple linear queue
(B) Circular queue
(C) Priority queue
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### India Geography — Peninsular Plateau

---

**Q26.** The Peninsular Plateau of India is divided into two main parts by which river?
(A) Godavari
(B) Narmada
(C) Krishna
(D) More than one of the above
(E) None of the above

---

**Q27.** The Deccan Plateau is located:
(A) North of the Narmada River
(B) South of the Narmada River
(C) East of the Aravalli Range
(D) More than one of the above
(E) None of the above

---

**Q28.** The Chota Nagpur Plateau is known as the "mineral heartland" of India primarily because of its deposits of:
(A) Petroleum and natural gas
(B) Coal, iron ore, copper, mica, and uranium
(C) Gold and silver
(D) More than one of the above
(E) None of the above

---

**Q29.** Both the Narmada and Son rivers originate from:
(A) Nilgiri Hills
(B) Amarkantak (Vindhya-Satpura junction)
(C) Western Ghats
(D) More than one of the above
(E) None of the above

---

**Q30.** The Narmada river flows towards which sea/ocean?
(A) Bay of Bengal
(B) Indian Ocean (southward)
(C) Arabian Sea
(D) More than one of the above
(E) None of the above

---

**Q31.** Why do the Narmada and Tapi rivers NOT form deltas at their mouths?
(A) They are too short to carry sediment
(B) They flow through rift valleys and form estuaries, not deltas
(C) They are dammed completely before reaching the sea
(D) More than one of the above
(E) None of the above

---

**Q32.** Regur (Black Cotton Soil) is primarily formed from the weathering of:
(A) Granite rocks
(B) Basalt (Deccan Trap volcanic rock)
(C) Limestone
(D) More than one of the above
(E) None of the above

---

**Q33.** The Deccan Traps were formed approximately how many million years ago?
(A) 5 million
(B) 200 million
(C) ~65 million
(D) More than one of the above
(E) None of the above

---

**Q34.** The Godavari river is also known as:
(A) Ponni
(B) Vridha Ganga / Dakshin Ganga
(C) Life Line of MP
(D) More than one of the above
(E) None of the above

---

**Q35.** The Kolar Gold Fields (KGF) are located in which state?
(A) Andhra Pradesh
(B) Tamil Nadu
(C) Karnataka
(D) More than one of the above
(E) None of the above

---

**Q36.** Dhupgarh is the highest peak of the Satpura Range. It is located in:
(A) Gujarat
(B) Maharashtra
(C) Madhya Pradesh
(D) More than one of the above
(E) None of the above

---

**Q37.** Pachmarhi, the only hill station of Madhya Pradesh, is located in which range?
(A) Vindhya Range
(B) Satpura Range
(C) Aravalli Range
(D) More than one of the above
(E) None of the above

---

**Q38.** The Malwa Plateau is bounded in the north by the Aravalli Range and in the south by:
(A) Satpura Range
(B) Vindhya Range
(C) Western Ghats
(D) More than one of the above
(E) None of the above

---

**Q39.** India's first uranium mine is located at:
(A) Khetri (Rajasthan)
(B) Jaduguda (Jharkhand)
(C) Singhbhum (Jharkhand)
(D) More than one of the above
(E) None of the above

---

**Q40.** Which two rivers flow through the valley BETWEEN the Vindhya and Satpura ranges?
(A) Godavari and Krishna
(B) Narmada and Tapi (Tapti)
(C) Chambal and Betwa
(D) More than one of the above
(E) None of the above

---

**Q41.** The geological age of the Peninsular Plateau rocks is:
(A) Mesozoic era (about 200 million years)
(B) Cenozoic era (last 65 million years)
(C) Precambrian era (more than 540 million years old)
(D) More than one of the above
(E) None of the above

---

**Q42.** The Kaveri river is known by which name in Tamil Nadu?
(A) Dakshin Ganga
(B) Ponni
(C) Vridha Ganga
(D) More than one of the above
(E) None of the above

---

**Q43.** The Chambal, Betwa, and Ken rivers (tributaries of Yamuna) flow through which plateau?
(A) Chota Nagpur Plateau
(B) Malwa Plateau
(C) Mysore Plateau
(D) More than one of the above
(E) None of the above

---

**Q44.** The Parasnath Hill in Jharkhand (sacred to Jains) is located in:
(A) Vindhya Range
(B) Chota Nagpur Plateau
(C) Satpura Range
(D) More than one of the above
(E) None of the above

---

**Q45.** Deccan Plateau tilts from west to east. This causes rivers to:
(A) Flow northward to the Ganga
(B) Flow westward to the Arabian Sea
(C) Flow eastward to the Bay of Bengal
(D) More than one of the above
(E) None of the above

---

**Q46.** The Jharia coalfield, one of India's richest coalfields, is located in:
(A) Odisha
(B) Chhattisgarh
(C) Jharkhand
(D) More than one of the above
(E) None of the above

---

**Q47.** The Mysore (Karnataka) Plateau is primarily composed of which type of rock?
(A) Sedimentary rocks (sandstone, limestone)
(B) Ancient gneiss and granite (Precambrian)
(C) Volcanic basalt
(D) More than one of the above
(E) None of the above

---

**Q48.** The Peninsular Plateau is described as "geologically stable" because:
(A) It has no rivers flowing through it
(B) It is made of very old, hard Precambrian rocks not prone to tectonic activity
(C) It is located away from all oceans
(D) More than one of the above
(E) None of the above

---

**Q49.** Which river is known as the "Life Line of Madhya Pradesh"?
(A) Son
(B) Chambal
(C) Narmada
(D) More than one of the above
(E) None of the above

---

**Q50.** The Coromandel coast and Malabar coast lie to the _____ of the Peninsular Plateau:
(A) North and South respectively
(B) East and West respectively
(C) West and East respectively
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
| 1 | (B) | FIFO = First In, First Out |
| 2 | (C) | Enqueue at REAR; Dequeue from FRONT |
| 3 | (B) | Empty queue: front = -1, rear = -1 |
| 4 | (C) | Enqueue = O(1) — direct rear insertion |
| 5 | (B) | 5 enqueues → rear goes 0,1,2,3,4 = MAX-1 |
| 6 | (B) | Overflow: rear == MAX-1 (linear queue) |
| 7 | (C) | Underflow: front == -1 (empty) |
| 8 | (B) | FIFO: A,B,C,D → dequeued A,B,C,D (same order) |
| 9 | (B) | Memory wastage — false overflow problem |
| 10 | (B) | Circular: rear = (rear+1)%MAX — wraps around |
| 11 | (C) | Correct modulo formula for circular queue |
| 12 | (C) | CPU scheduling (FCFS) uses Queue |
| 13 | (B) | BFS uses Queue |
| 14 | (C) | Async data transfer = Queue (buffer) |
| 15 | (C) | Deque = Double-Ended Queue |
| 16 | (B) | Priority Queue: highest priority first |
| 17 | (A) | Stack: 1 pointer (top); Queue: 2 pointers (front, rear) |
| 18 | (B) | 3 enqueues (front=0,rear=2), 1 dequeue (front becomes 1) |
| 19 | (B) | Print spooler = Queue |
| 20 | (B) | Queue preserves order (FIFO) |
| 21 | (B) | BFS uses Queue |
| 22 | (D) | rear-front+1 = 5-3+1 = 3 elements (not in options as stated) → D |
| 23 | (B) | After last dequeue: reset front=-1, rear=-1 |
| 24 | (C) | Stack=LIFO; Queue=FIFO |
| 25 | (B) | Round Robin uses Circular Queue |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Narmada divides plateau into Central Highlands (N) + Deccan (S) |
| 27 | (B) | Deccan = south of Narmada |
| 28 | (B) | Chota Nagpur: coal, iron, copper, mica, uranium |
| 29 | (B) | Amarkantak = source of both Narmada and Son |
| 30 | (C) | Narmada → Arabian Sea (west-flowing) |
| 31 | (B) | Rift valley rivers → estuary, not delta |
| 32 | (B) | Regur = weathered Deccan Trap basalt |
| 33 | (C) | Deccan Traps ≈ 65 million years ago |
| 34 | (B) | Godavari = Vridha Ganga / Dakshin Ganga |
| 35 | (C) | KGF = Kolar, Karnataka |
| 36 | (C) | Dhupgarh = Satpura, Madhya Pradesh |
| 37 | (B) | Pachmarhi = Satpura Range, MP |
| 38 | (B) | Malwa bounded south by Vindhya Range |
| 39 | (B) | Jaduguda (Jharkhand) = India's first uranium mine |
| 40 | (B) | Narmada and Tapi flow between Vindhya and Satpura |
| 41 | (C) | Precambrian = 540+ million years old |
| 42 | (B) | Kaveri = "Ponni" in Tamil |
| 43 | (B) | Chambal, Betwa, Ken = Malwa Plateau (Yamuna tributaries) |
| 44 | (B) | Parasnath = Chota Nagpur Plateau, Jharkhand |
| 45 | (C) | Westward tilt → rivers flow east to Bay of Bengal |
| 46 | (C) | Jharia coalfield = Jharkhand |
| 47 | (B) | Mysore Plateau = ancient gneiss and granite |
| 48 | (B) | Old hard Precambrian rocks = geologically stable |
| 49 | (C) | Narmada = Life Line of Madhya Pradesh |
| 50 | (B) | Coromandel = east coast; Malabar = west coast |

---
---

# 🔁 DAY 18 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Queue Data Structure

### Core Rules — One-Liners:
```
1. FIFO: First In, First Out — order PRESERVED (opposite of Stack)
2. Initial state: front = -1, rear = -1 (both -1 = empty)
3. ENQUEUE at REAR; DEQUEUE from FRONT
4. Overflow: rear == MAX - 1 (linear queue)
5. Underflow: front == -1 (empty queue)
6. All operations O(1): Enqueue, Dequeue, Peek, isEmpty, isFull
7. Stack = 1 pointer (top); Queue = 2 pointers (front + rear)
8. Linear Queue problem: false overflow — wasted space at front
9. Circular Queue fix: rear = (rear+1)%MAX — wraps around
10. Round Robin CPU scheduling → Circular Queue
```

### After last element dequeued: reset front = -1, rear = -1

### Types of Queue:
```
Simple Linear → false overflow problem
Circular → (rear+1)%MAX — solves linear problem
Deque → insert/delete from BOTH ends
Priority → highest priority served first (not FIFO)
```

### Applications (Must Know):
```
Queue Applications:
✅ CPU Scheduling (FCFS, Round Robin)
✅ Print Spooler
✅ BFS (Breadth-First Search)
✅ Asynchronous data transfer (producer-consumer)
✅ Interrupt handling in OS
✅ Traffic management

NOT Queue Applications:
❌ Balancing symbols → Stack
❌ Recursion → Stack
❌ Undo/Redo → Stack
❌ DFS → Stack
❌ Browser back → Stack
```

---

## ⚡ RAPID FIRE — Peninsular Plateau

### Core Structure:
```
Narmada River DIVIDES Peninsular Plateau:
  NORTH → Central Highlands (Malwa, Chota Nagpur, Bundelkhand)
  SOUTH → Deccan Plateau (Maharashtra, Karnataka, AP, TN)
```

### 5 Must-Know Facts:
```
1. Narmada + Tapi = ONLY west-flowing peninsular rivers
   → Rift valley origin → NO DELTA → ESTUARY
2. Narmada + Son = SAME origin (Amarkantak, Vindhya-Satpura junction)
   but flow in OPPOSITE directions
3. Chota Nagpur = "Mineral Heartland" (Coal, Iron, Copper, Mica, Uranium)
4. Regur (Black Cotton) Soil = Deccan Trap basalt weathering → good for cotton
5. Godavari = "Dakshin Ganga" = longest peninsular river
```

### Key Peaks:
```
Dhupgarh (1,350m) = highest in Satpura = highest in MP
Parasnath (1,350m) = highest in Chota Nagpur / Jharkhand
```

### River Nicknames:
```
Godavari → Dakshin Ganga, Vridha Ganga (longest peninsular)
Kaveri   → Ponni (Tamil name), Dakshin Ganga
Narmada  → Life Line of MP
```

### Mineral Location Quick Match:
```
Coal → Jharia, Bokaro, Raniganj (Jharkhand/WB)
Uranium → Jaduguda (Jharkhand) — India's FIRST uranium mine
Gold → Kolar (Karnataka) — KGF
Copper → Singhbhum (Jharkhand)
Mica → Bihar-Jharkhand region
Lead-Zinc → Zawar (Rajasthan)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Queue = FIFO; Insert at REAR (enqueue); Delete from FRONT (dequeue); both initially at -1
2. Linear queue problem = false overflow (wasted space); Circular queue solves it using (rear+1)%MAX
3. BFS uses Queue; DFS uses Stack; Async data transfer = Queue; Recursion = Stack
4. Narmada divides Peninsular Plateau; Narmada + Tapi flow WEST (rift valleys, estuary, no delta)
5. Narmada and Son both originate at Amarkantak; Chota Nagpur = Mineral Heartland of India

---

*Next: Day 19 — Linked Lists (Singly, Doubly, Circular) + Bihar Economy and Agriculture*
