# 📅 DAY 18 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## CS Topic: Queue — FIFO, Types, Operations & Applications
## GS Topic: India Geography — Peninsular Plateau, Soil Types, Climate & Agriculture

> **Target: TOP RANK | Format: 5-option BPSC ABCDE | PYQs Integrated Throughout**
> ⚠️ **GOLDEN RULE: Attempt ALL 50 Questions FIRST → Answers + Explanations are at the VERY END**

---

# ══════════════════════════════════════════════
# 🖥️ COMPUTER SCIENCE — QUEUE DATA STRUCTURE
# ══════════════════════════════════════════════

---

## 📌 CS CONCEPT 1: What is a Queue?

A **Queue** is a linear data structure that follows the **FIFO** principle.

```
┌──────────────────────────────────────────────────────────────────────┐
│                  QUEUE — THE FIFO PRINCIPLE                          │
│                                                                      │
│   FIFO = First In, First Out                                         │
│                                                                      │
│   Real-life analogy:  People standing in a LINE at a ticket counter │
│                                                                      │
│       REAR (back)              FRONT (front)                         │
│   ┌──────────────────────────────────────────┐                      │
│   │  40  │  30  │  20  │  10  │              │                      │
│   └──────────────────────────────────────────┘                      │
│      ↑ New people join here       ↑ People exit (served) here       │
│   ENQUEUE (INSERT)              DEQUEUE (DELETE)                     │
│                                                                      │
│   • Person who joined FIRST → leaves FIRST                          │
│   • Person who joined LAST → waits the longest                      │
│                                                                      │
│   COMPARE with STACK (LIFO):                                         │
│   Stack = Pile of plates (last placed = first taken)                 │
│   Queue = Ticket line (first arrived = first served)                 │
└──────────────────────────────────────────────────────────────────────┘
```

### Stack vs Queue — Side-by-Side:

| Feature | Stack | Queue |
|---------|-------|-------|
| Principle | LIFO (Last In First Out) | FIFO (First In First Out) |
| Insert at | TOP | REAR |
| Delete from | TOP | FRONT |
| Insert operation | PUSH | ENQUEUE |
| Delete operation | POP | DEQUEUE |
| Overflow check | Before PUSH | Before ENQUEUE |
| Underflow check | Before POP | Before DEQUEUE |
| Real-world example | Book stack, browser history | Ticket counter, print queue |

---

## 📌 CS CONCEPT 2: Queue Operations — In Detail

A Queue has **5 core operations**. Know each one perfectly for BPSC:

```
┌──────────────────────────────────────────────────────────────────────┐
│                     QUEUE OPERATIONS                                  │
├────────────────┬────────────────────────────────────────────────────┤
│ Operation      │ Description                                         │
├────────────────┼────────────────────────────────────────────────────┤
│ 1. Enqueue     │ Insert element at the REAR                          │
│                │ Check OVERFLOW first (is queue FULL?)               │
│                │ rear = rear + 1; queue[rear] = element              │
├────────────────┼────────────────────────────────────────────────────┤
│ 2. Dequeue     │ Remove element from the FRONT                       │
│                │ Check UNDERFLOW first (is queue EMPTY?)             │
│                │ element = queue[front]; front = front + 1           │
├────────────────┼────────────────────────────────────────────────────┤
│ 3. Peek/Front  │ View the FRONT element WITHOUT removing it          │
│                │ Returns queue[front]                                 │
├────────────────┼────────────────────────────────────────────────────┤
│ 4. isEmpty     │ Check if queue has NO elements                      │
│                │ Condition: front > rear OR front = -1               │
├────────────────┼────────────────────────────────────────────────────┤
│ 5. isFull      │ Check if queue is COMPLETELY full                   │
│                │ Condition: rear = MAX_SIZE - 1 (for linear queue)  │
└────────────────┴────────────────────────────────────────────────────┘
```

### ⭐ CRITICAL PYQ FACTS — BPSC Loves These!:
```
┌──────────────────────────────────────────────────────────────────────┐
│  ⚠️  BEFORE DELETION  →  Check UNDERFLOW  (queue might be EMPTY)   │
│  ⚠️  BEFORE INSERTION →  Check OVERFLOW   (queue might be FULL)    │
│                                                                      │
│  These appeared directly in TRE 2.0 paper!                          │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 CS CONCEPT 3: Linear Queue — Array Implementation

### How a Linear Queue Works (Step by Step):

```
Initial State: Queue of size 5, empty
front = -1, rear = -1

ENQUEUE 10:
front=0, rear=0  →  [10][ ][ ][ ][ ]

ENQUEUE 20:
front=0, rear=1  →  [10][20][ ][ ][ ]

ENQUEUE 30:
front=0, rear=2  →  [10][20][30][ ][ ]

DEQUEUE (removes 10):
front=1, rear=2  →  [ ][20][30][ ][ ]
                     ^-- This slot is WASTED in LINEAR queue!

ENQUEUE 40:
front=1, rear=3  →  [ ][20][30][40][ ]

ENQUEUE 50:
front=1, rear=4  →  [ ][20][30][40][50]

NOW rear = MAX_SIZE-1 = 4 → Queue reports OVERFLOW!
BUT there is 1 free slot at index 0!
→ This is the PROBLEM of LINEAR QUEUE = Memory Wastage!
→ Solution = CIRCULAR QUEUE (Day 19 topic)
```

### Overflow Condition (Linear Queue):
```
rear == MAX_SIZE - 1   →   OVERFLOW (even if front slots are free!)
```

### Underflow Condition:
```
front == -1   OR   front > rear   →   UNDERFLOW (empty queue)
```

---

## 📌 CS CONCEPT 4: Types of Queue

```
┌──────────────────────────────────────────────────────────────────────┐
│                    TYPES OF QUEUE                                    │
│                                                                      │
│  1. LINEAR QUEUE                                                     │
│     • Simple, basic queue                                            │
│     • Insert at REAR, delete from FRONT                              │
│     • Problem: Memory wastage (once front moves, slots wasted)       │
│                                                                      │
│  2. CIRCULAR QUEUE (Ring Buffer)                                     │
│     • Overcomes memory wastage of linear queue                       │
│     • Rear wraps around to beginning using modulo                    │
│     • Full condition: (rear+1) % SIZE == front                       │
│     • [Covered in detail on Day 19]                                  │
│                                                                      │
│  3. DOUBLE-ENDED QUEUE (DEQUE)                                       │
│     • Insert AND delete from BOTH ends                               │
│     • Input-restricted Deque: insert at one end only                 │
│     • Output-restricted Deque: delete from one end only              │
│     • [Covered in detail on Day 19]                                  │
│                                                                      │
│  4. PRIORITY QUEUE                                                   │
│     • Elements served based on PRIORITY, not arrival time            │
│     • Best implemented using Binary Heap (Min or Max)                │
│     • [Covered on Day 20]                                            │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 CS CONCEPT 5: Time Complexity of Queue Operations

| Operation | Array-based Queue | Linked-List Queue |
|-----------|------------------|-------------------|
| Enqueue | **O(1)** | O(1) |
| Dequeue | **O(1)** | O(1) |
| Peek/Front | **O(1)** | O(1) |
| isEmpty | **O(1)** | O(1) |
| Search | **O(N)** | O(N) |
| Space | **O(N)** | O(N) |

> **Key insight:** All basic queue operations (enqueue, dequeue, peek) are **O(1)** — constant time. This makes Queue very efficient for its use cases.

---

## 📌 CS CONCEPT 6: Applications of Queue — MASTER LIST

This is a HIGH-FREQUENCY BPSC topic. Know all applications + what is NOT an application:

```
┌──────────────────────────────────────────────────────────────────────┐
│              APPLICATIONS OF QUEUE ✅                                │
├──────────────────────────────────────────────────────────────────────┤
│  1. CPU Scheduling (Ready Queue in OS)                               │
│     → Processes wait in queue for CPU; served in FIFO order          │
│                                                                      │
│  2. Printer Spooling / Print Queue                                   │
│     → Print jobs line up; first submitted = first printed            │
│                                                                      │
│  3. BFS (Breadth-First Search) in Graph/Tree                         │
│     → Uses Queue to visit nodes level by level                       │
│                                                                      │
│  4. Asynchronous Data Transfer                                       │
│     → Between two processes running at different speeds              │
│     → IO Buffers, Pipes use Queue concept                            │
│                                                                      │
│  5. Handling of Interrupts in Operating Systems                      │
│     → Interrupt queue in OS                                          │
│                                                                      │
│  6. Keyboard Input Buffer                                            │
│     → Keystrokes stored in queue; processed in order                 │
│                                                                      │
│  7. Traffic Management Systems                                       │
│     → Vehicles wait in queue at traffic lights                       │
│                                                                      │
│  8. Call Center Waiting Systems                                      │
│     → Customer calls wait in queue                                   │
│                                                                      │
├──────────────────────────────────────────────────────────────────────┤
│              NOT an Application of Queue ❌                          │
│  • Balancing of symbols/parentheses  →  Uses STACK                  │
│  • Recursion implementation          →  Uses STACK                  │
│  • Undo/Redo operations              →  Uses STACK                  │
│  • Expression evaluation (Postfix)   →  Uses STACK                  │
│  • DFS (Depth First Search)          →  Uses STACK (or recursion)   │
└──────────────────────────────────────────────────────────────────────┘
```

> **⭐ BPSC PYQ TRAP:** "Which uses Queue?" → Asynchronous data transfer ✅ | Balancing of symbols ❌ (Stack)
> This exact distinction appeared in TRE 1.0 and TRE 2.0!

---

## 📌 CS CONCEPT 7: Queue using Linked List

Sometimes BPSC asks about implementing Queue using Linked List. Key facts:

```
QUEUE using SINGLY LINKED LIST:

  HEAD (front)                           TAIL (rear)
     ↓                                       ↓
  ┌────┬──┐   ┌────┬──┐   ┌────┬──┐   ┌────┬──┐
  │ 10 │──┼──►│ 20 │──┼──►│ 30 │──┼──►│ 40 │ / │
  └────┴──┘   └────┴──┘   └────┴──┘   └────┴──┘

  ENQUEUE: Add new node at TAIL (rear) → O(1) with tail pointer
  DEQUEUE: Remove node from HEAD (front) → O(1)

  ADVANTAGE over Array Queue:
  → No overflow (dynamic size — memory allocated as needed)
  → No wasted slots like linear array queue

  DISADVANTAGE:
  → Extra memory for pointers in each node
  → No random access
```

---

## 📌 CS CONCEPT 8: Queue in Operating System — Ready Queue & Job Queue

This connects Queue to Operating Systems (another BPSC topic):

```
┌──────────────────────────────────────────────────────────────────────┐
│              QUEUE IN OPERATING SYSTEM                               │
│                                                                      │
│  JOB QUEUE:                                                          │
│  → All processes in the system are in Job Queue                      │
│  → Long-term scheduler picks from here                               │
│                                                                      │
│  READY QUEUE:                                                         │
│  → Processes in RAM, waiting for CPU                                 │
│  → Short-term scheduler (CPU scheduler) picks from here              │
│  → Uses Queue structure (FIFO-based, though can be priority)         │
│                                                                      │
│  DEVICE QUEUE (I/O Queue):                                           │
│  → Processes waiting for I/O (disk, printer) go in device queue      │
│  → After I/O completes → move back to Ready Queue                    │
│                                                                      │
│  PROCESS FLOW:                                                        │
│  New → [Job Queue] → [Ready Queue] → CPU → Done                     │
│                              ↑                  ↓                    │
│                         [Device Queue] ←── I/O Request               │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 CS CONCEPT 9: BFS Uses Queue — How and Why

Breadth-First Search (BFS) on a graph/tree uses a Queue:

```
TREE:
           A
          / \
         B   C
        / \   \
       D   E   F

BFS traversal using Queue:

Step 1: Enqueue A → Queue: [A]
Step 2: Dequeue A, visit A, Enqueue B, C → Queue: [B, C]
Step 3: Dequeue B, visit B, Enqueue D, E → Queue: [C, D, E]
Step 4: Dequeue C, visit C, Enqueue F → Queue: [D, E, F]
Step 5: Dequeue D, visit D → Queue: [E, F]
Step 6: Dequeue E, visit E → Queue: [F]
Step 7: Dequeue F, visit F → Queue: []

BFS Order: A → B → C → D → E → F  (Level by level ✓)
```

> **Key:** BFS visits nodes **level by level** → needs Queue (FIFO, processes in arrival order).
> DFS visits nodes **depth first** → needs **Stack** (or recursion).

---

## 📌 CS CONCEPT 10: All Queue Facts at a Glance — BPSC Cheatsheet

```
┌──────────────────────────────────────────────────────────────────────┐
│          ⭐ MUST-MEMORIZE QUEUE FACTS FOR BPSC TRE 4.0              │
├──────────────────────────────────────────────────────────────────────┤
│  1. Queue principle = FIFO (First In First Out)                      │
│  2. Insert = ENQUEUE at REAR                                         │
│  3. Delete = DEQUEUE from FRONT                                      │
│  4. Before deletion → check UNDERFLOW (empty?)                       │
│  5. Before insertion → check OVERFLOW (full?)                        │
│  6. Linear queue overflow: rear == MAX_SIZE - 1                      │
│  7. Linear queue problem = MEMORY WASTAGE                            │
│  8. Circular queue solves memory wastage                             │
│  9. Queue uses: BFS, CPU scheduling, Printer spooling                │
│  10. Queue uses: Asynchronous data transfer                          │
│  11. NOT Queue: Symbol balancing, Recursion → these use STACK        │
│  12. BFS → Queue | DFS → Stack                                       │
│  13. Priority Queue → implemented with Binary Heap                   │
│  14. All basic operations (enqueue/dequeue) → O(1) time             │
│  15. Deque = Double-Ended Queue (insert/delete from both ends)       │
└──────────────────────────────────────────────────────────────────────┘
```

---

# ══════════════════════════════════════════════════════
# 🌍 GENERAL STUDIES — INDIA GEOGRAPHY
# Peninsular Plateau | Soil Types | Climate | Agriculture
# ══════════════════════════════════════════════════════

> **Note:** Day 17 covered Eastern/Western Ghats. Today we go DEEPER into the Peninsular Plateau with Soil, Climate, and Agriculture — all high-frequency BPSC GS topics from Lucent GK.

---

## 📌 GS CONCEPT 1: Soil Types of India — Complete Coverage

Soil is asked EVERY year in BPSC. Know all 6 types with their crop associations:

```
┌──────────────────────────────────────────────────────────────────────┐
│                   6 MAJOR SOIL TYPES OF INDIA                        │
│                                                                      │
│  1. ALLUVIAL SOIL (Most Widespread in India)                         │
│     Color: Light grey to dark grey                                   │
│     Found: Indo-Gangetic Plain, river deltas, coastal areas          │
│     States: UP, Bihar, Punjab, Haryana, WB, Assam                    │
│     Rich in: Potash, phosphoric acid                                 │
│     Deficient in: Nitrogen, humus                                    │
│     Best crops: WHEAT, RICE, SUGARCANE, MAIZE, Pulses               │
│     Types: Khadar (new alluvium — fertile) & Bhangar (old alluvium)  │
│     → Largest area under any soil type in India                      │
│                                                                      │
│  2. BLACK SOIL (Regur Soil) / Cotton Soil                            │
│     Color: Black (due to titaniferous magnetite)                     │
│     Found: Deccan Plateau — Maharashtra, MP, Gujarat, AP             │
│     Rich in: Iron, lime, calcium, magnesium                          │
│     Deficient in: Nitrogen, phosphorus, organic matter               │
│     Special property: HIGH water-retaining capacity                  │
│                        Self-ploughing (cracks when dry)              │
│     Best crops: COTTON (hence "cotton soil"), Tobacco, Jowar         │
│                                                                      │
│  3. RED SOIL                                                         │
│     Color: Red (due to presence of iron oxide / ferric oxide)        │
│     Found: Peninsular India — Tamil Nadu, AP, Karnataka, Odisha      │
│     Rich in: Iron                                                    │
│     Deficient in: Nitrogen, phosphorus, humus, lime                 │
│     Best crops: GROUNDNUT, COTTON, WHEAT, RICE (with irrigation)    │
│                                                                      │
│  4. LATERITE SOIL                                                    │
│     Color: Brick red / brownish                                      │
│     Found: High rainfall + high temp areas — Kerala, Karnataka,      │
│            Tamil Nadu, Assam, MP, Odisha                             │
│     Formed by: LEACHING (soluble minerals washed away by rain)       │
│     Rich in: Iron and aluminium oxides                               │
│     Deficient in: Nitrogen, phosphorus, calcium, organic matter      │
│     Best crops: TEA, COFFEE, CASHEW, RUBBER, COCONUT                │
│     Note: Used as building material (laterite = "brick" in Latin)   │
│                                                                      │
│  5. DESERT SOIL (Arid Soil)                                          │
│     Color: Red to brown                                              │
│     Found: Rajasthan, parts of Gujarat, Haryana                      │
│     Rich in: Phosphate, soluble salts                                │
│     Deficient in: Nitrogen, humus, water                            │
│     Best crops: BAJRA (pearl millet), with irrigation — cotton       │
│     Note: Sandy, low water retention, needs irrigation               │
│                                                                      │
│  6. MOUNTAIN/FOREST SOIL                                             │
│     Color: Varies — dark brown to grey                               │
│     Found: Himalayan slopes, forests of NE India                     │
│     Rich in: Humus (organic matter)                                  │
│     Deficient in: Potash, phosphorus                                 │
│     Best crops: TEA, COFFEE, SPICES (in hilly areas)                │
└──────────────────────────────────────────────────────────────────────┘
```

### Quick Memory Trick for Soil Types:
**"All Black Remains Largely Dry on Mountains"**
→ **A**lluvial, **B**lack, **R**ed, **L**aterite, **D**esert, **M**ountain

---

## 📌 GS CONCEPT 2: Soil — State-wise Distribution Map

```
┌──────────────────────────────────────────────────────────────────────┐
│              SOIL DISTRIBUTION IN INDIA                              │
│                                                                      │
│         [NORTH]                                                      │
│  ┌──────────────────────────────────┐                                │
│  │   Punjab, Haryana, UP, Bihar     │ ← ALLUVIAL SOIL                │
│  │   (Indo-Gangetic Plain)          │   (Most fertile, largest area) │
│  ├────────────────┬─────────────────┤                                │
│  │  DESERT SOIL   │   ALLUVIAL      │                                │
│  │  (Rajasthan)   │   (Gujarat      │                                │
│  │                │    coastal)     │                                │
│  ├────────────────┴─────────────────┤                                │
│  │  BLACK SOIL (Deccan Plateau)     │ ← Maharashtra, MP, Gujarat     │
│  │  Great for Cotton                │                                │
│  ├──────────────────────────────────┤                                │
│  │  RED SOIL (South Deccan)         │ ← TN, AP, Karnataka, Odisha    │
│  ├──────────────────────────────────┤                                │
│  │  LATERITE SOIL (Coastal/Hills)   │ ← Kerala, Karnataka, Assam     │
│  └──────────────────────────────────┘                                │
│                                                                      │
│  MOUNTAIN SOIL: Himalayan slopes + NE India forests                  │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS CONCEPT 3: Climate of India — Seasons & Monsoon

India has **4 seasons** based on the Indian Meteorological Department:

```
┌──────────────────────────────────────────────────────────────────────┐
│                  SEASONS OF INDIA                                     │
├──────────────────┬───────────────┬──────────────────────────────────┤
│ Season           │ Months        │ Key Features                      │
├──────────────────┼───────────────┼──────────────────────────────────┤
│ 1. Winter        │ Dec – Feb     │ Cool, dry; NE trade winds        │
│                  │               │ Western disturbances bring rain  │
│                  │               │ to NW India (wheat belt)          │
├──────────────────┼───────────────┼──────────────────────────────────┤
│ 2. Pre-monsoon   │ Mar – May     │ Hot, dry; Nor'westers in Bengal  │
│ (Hot dry season) │               │ "Loo" hot winds in NW India      │
│                  │               │ Mango showers in Kerala/TN       │
├──────────────────┼───────────────┼──────────────────────────────────┤
│ 3. SW Monsoon    │ Jun – Sep     │ Main rainy season                 │
│ (Advancing)      │               │ Arabian Sea + Bay of Bengal arms │
│                  │               │ Enters India through Kerala       │
│                  │               │ ~75% of India's annual rainfall  │
├──────────────────┼───────────────┼──────────────────────────────────┤
│ 4. Retreating    │ Oct – Nov     │ NE Monsoon; Tamil Nadu gets rain  │
│ Monsoon          │               │ Cyclones in Bay of Bengal        │
│                  │               │ "October Heat" phenomenon         │
└──────────────────┴───────────────┴──────────────────────────────────┘
```

### The SW Monsoon — How it Reaches India:

```
┌──────────────────────────────────────────────────────────────────────┐
│              SW MONSOON MECHANISM                                     │
│                                                                      │
│  CAUSE: Differential heating of land and sea                         │
│  → In summer, Indian subcontinent heats up faster than Indian Ocean  │
│  → Low pressure forms over Thar Desert (Rajasthan)                   │
│  → High pressure over Indian Ocean (cool)                            │
│  → Winds blow from High → Low: Ocean to Land = MONSOON!             │
│                                                                      │
│  TWO BRANCHES:                                                        │
│                                                                      │
│  BRANCH 1 — Arabian Sea Branch:                                      │
│  → Enters through Kerala coast (around June 1)                       │
│  → Moves north along Western Ghats                                   │
│  → Hits Western Ghats → Heavy rain on windward (west) side          │
│  → Leeward side (east) = Rain Shadow = less rain                    │
│  → Reaches Mumbai, Goa, then moves into Gujarat and Rajasthan        │
│                                                                      │
│  BRANCH 2 — Bay of Bengal Branch:                                    │
│  → Enters through Arakan coast (Myanmar) + NE India                 │
│  → Moves into Gangetic Plains from east                              │
│  → Cherrapunji/Mawsynram gets world's highest rainfall here         │
│  → Reaches Delhi, Punjab, Haryana last                               │
│                                                                      │
│  NORMAL ONSET IN KERALA: June 1 (±7 days)                           │
│  COVERS ALL INDIA BY: July 15                                        │
└──────────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS CONCEPT 4: Rainfall Facts — Must-Know for BPSC

| Fact | Location | Detail |
|------|----------|--------|
| Highest rainfall in India | **Mawsynram** (Meghalaya) | ~11,871 mm/year |
| 2nd highest / also famous | **Cherrapunji** (Meghalaya) | ~11,430 mm/year |
| Lowest rainfall in India | **Leh** (Ladakh) | ~50 mm/year |
| Most rainfall state | Meghalaya | NE India |
| Least rainfall area | Thar Desert / Jaisalmer | Rajasthan |
| Highest rainfall in Bihar | **Kishanganj** district | NE Bihar |
| Lowest rainfall in Bihar | **Rohtas** / **Kaimur** | SW Bihar |
| Rainiest city India | Mumbai (among metros) | — |

> **⭐ PYQ FACT:** Mawsynram in Meghalaya receives the highest average annual rainfall in the world and in India. Cherrapunji used to hold this record but Mawsynram surpassed it.

---

## 📌 GS CONCEPT 5: Agriculture in India — Crops & Seasons

BPSC loves questions on which crop is grown in which season and which state:

```
┌──────────────────────────────────────────────────────────────────────┐
│              CROP SEASONS IN INDIA                                    │
├──────────────┬────────────────┬─────────────────────────────────────┤
│ Season       │ Sowing         │ Main Crops                          │
├──────────────┼────────────────┼─────────────────────────────────────┤
│ KHARIF       │ June–July      │ RICE, Maize, Jowar, Bajra,          │
│ (Monsoon)    │ (SW Monsoon)   │ Cotton, Jute, Groundnut, Soybean   │
│              │ Harvest: Oct   │ Sugarcane (takes 10–12 months)      │
├──────────────┼────────────────┼─────────────────────────────────────┤
│ RABI         │ October–Nov    │ WHEAT, Barley, Mustard, Gram,       │
│ (Winter)     │ Harvest: Apr   │ Peas, Linseed, Sunflower            │
├──────────────┼────────────────┼─────────────────────────────────────┤
│ ZAID         │ March–June     │ WATERMELON, Muskmelon, Cucumber,    │
│ (Summer)     │ (Short season) │ Vegetables, Fodder crops            │
└──────────────┴────────────────┴─────────────────────────────────────┘
```

> **Memory trick:** **K**harif → **K**ay (June = beginning of rains) | **R**abi → **R**est period (winter wheat)

---

## 📌 GS CONCEPT 6: Major Crops — State-wise Leaders

```
┌──────────────────────────────────────────────────────────────────────┐
│              LEADING STATES IN MAJOR CROPS                           │
├──────────────┬────────────────────────────────────────────────────  │
│ Crop         │ Leading State(s)                                      │
├──────────────┼────────────────────────────────────────────────────  │
│ RICE         │ West Bengal (largest producer), UP, Punjab            │
│ WHEAT        │ Uttar Pradesh (largest), Punjab, Haryana              │
│ COTTON       │ Gujarat (largest), Maharashtra, AP, Telangana         │
│ JUTE         │ West Bengal (>80% of India's jute), Bihar, Assam     │
│ SUGARCANE    │ Uttar Pradesh (largest), Maharashtra, Karnataka       │
│ TEA          │ Assam (largest), West Bengal, Tamil Nadu, Kerala     │
│ COFFEE       │ Karnataka (largest ~70%), Kerala, Tamil Nadu          │
│ GROUNDNUT    │ Gujarat (largest), AP, Rajasthan                      │
│ RUBBER       │ Kerala (>90% of India's rubber)                       │
│ SPICES       │ Kerala ("Spice Garden of India")                      │
│ SOYBEAN      │ Madhya Pradesh (largest)                              │
│ SUNFLOWER    │ Karnataka, Maharashtra                                │
│ MUSTARD      │ Rajasthan (largest), Haryana, UP                      │
│ BANANA       │ Tamil Nadu, Maharashtra                               │
│ MANGO        │ Uttar Pradesh (largest), AP, Bihar                   │
│ LITCHI       │ Bihar (Muzaffarpur = litchi capital of India!)        │
│ MAIZE        │ Karnataka, AP, Bihar                                  │
└──────────────┴────────────────────────────────────────────────────  │
```

> **⭐ BIHAR SPECIAL:** Bihar is famous for **Litchi** — Muzaffarpur district is the litchi capital. This is asked in every Bihar exam!

---

## 📌 GS CONCEPT 7: Green Revolution, White Revolution, Blue Revolution

This is a **direct PYQ topic** — know all revolutions:

```
┌──────────────────────────────────────────────────────────────────────┐
│              AGRICULTURAL REVOLUTIONS IN INDIA                        │
├────────────────────┬────────────────────────────────────────────────┤
│ Revolution         │ Related to                                      │
├────────────────────┼────────────────────────────────────────────────┤
│ GREEN Revolution   │ Food grains — Wheat & Rice                      │
│                    │ Father: M.S. Swaminathan                        │
│                    │ Period: 1960s–70s; started in Punjab/Haryana     │
│                    │ HYV seeds, fertilizers, irrigation              │
├────────────────────┼────────────────────────────────────────────────┤
│ WHITE Revolution   │ Milk / Dairy                                    │
│ (Operation Flood)  │ Father: Dr. Verghese Kurien                     │
│                    │ Amul model (Gujarat); NDDB formed               │
├────────────────────┼────────────────────────────────────────────────┤
│ BLUE Revolution    │ Fish / Fisheries / Aquaculture                  │
├────────────────────┼────────────────────────────────────────────────┤
│ YELLOW Revolution  │ Oilseeds (especially Mustard, Groundnut)        │
├────────────────────┼────────────────────────────────────────────────┤
│ PINK Revolution    │ Prawn / Meat / Tomato (multiple meanings!)      │
├────────────────────┼────────────────────────────────────────────────┤
│ GOLDEN Revolution  │ Fruits, Honey & Horticulture                    │
├────────────────────┼────────────────────────────────────────────────┤
│ SILVER Revolution  │ Eggs / Poultry                                  │
├────────────────────┼────────────────────────────────────────────────┤
│ BROWN Revolution   │ Leather / Non-conventional energy sources       │
├────────────────────┼────────────────────────────────────────────────┤
│ RED Revolution     │ Meat & Tomato                                   │
├────────────────────┼────────────────────────────────────────────────┤
│ ROUND Revolution   │ Potato                                          │
│ RAINBOW Revolution │ All revolutions combined; India overall growth  │
└────────────────────┴────────────────────────────────────────────────┘
```

> **⭐ Direct PYQ:** "Father of Green Revolution in India" = **M.S. Swaminathan**. Father of Green Revolution in the World = **Norman Borlaug**.

---

## 📌 GS CONCEPT 8: Minerals & Industries of Peninsular Plateau

The Peninsular Plateau is India's **mineral treasure chest**:

```
┌──────────────────────────────────────────────────────────────────────┐
│              MINERALS OF PENINSULAR INDIA                            │
├──────────────────┬───────────────────────────────────────────────── │
│ Mineral          │ Major Producing States                            │
├──────────────────┼───────────────────────────────────────────────── │
│ IRON ORE         │ Odisha (largest), Jharkhand, Chhattisgarh, Goa   │
│                  │ Major mines: Noamundi, Kiriburu, Bailadila        │
│ COAL             │ Jharkhand (largest), Odisha, WB, MP, Chhattisgarh│
│                  │ Jharia = largest coalfield of India (Jharkhand)   │
│ MANGANESE        │ Odisha (largest), MP, Karnataka, Maharashtra      │
│ BAUXITE          │ Odisha (largest), Jharkhand, Maharashtra         │
│ (Aluminium ore)  │                                                   │
│ COPPER           │ Rajasthan (Khetri mines = largest copper mine)    │
│                  │ Jharkhand (Singhbhum), MP (Malanjkhand)           │
│ MICA             │ Jharkhand (largest), Rajasthan, AP               │
│                  │ India = largest mica producer in world!           │
│ GOLD             │ Karnataka (Kolar Gold Fields = deepest mine)      │
│ DIAMOND          │ MP (Panna mines), AP (Golconda, historical)       │
│ LIMESTONE        │ MP, Rajasthan, AP (for cement industry)           │
│ URANIUM          │ Jharkhand (Jaduguda), AP (Tummalapalle)           │
└──────────────────┴───────────────────────────────────────────────── │
```

> **⭐ BPSC PYQ:** "Which state is largest producer of Coal?" → **Jharkhand**. "Largest coalfield of India?" → **Jharia** (Jharkhand).

---

## 📌 GS CONCEPT 9: National Parks & Wildlife of India

Frequently asked in BPSC GS:

```
┌──────────────────────────────────────────────────────────────────────┐
│              IMPORTANT NATIONAL PARKS                                │
├────────────────────────┬─────────────────────────────────────────── │
│ National Park          │ State / Famous For                         │
├────────────────────────┼─────────────────────────────────────────── │
│ Jim Corbett NP         │ Uttarakhand — FIRST NP of India (1936)     │
│ Kaziranga NP           │ Assam — One-horned Rhinoceros; UNESCO WHS  │
│ Gir NP                 │ Gujarat — ONLY habitat of Asiatic Lion     │
│ Sundarbans NP          │ WB — Royal Bengal Tiger; UNESCO WHS        │
│ Kanha NP               │ Madhya Pradesh — Tiger; Barasingha (deer) │
│ Bandhavgarh NP         │ MP — Highest tiger density in India        │
│ Ranthambore NP         │ Rajasthan — Tiger                          │
│ Periyar NP             │ Kerala — Elephant, Tiger                   │
│ Valley of Flowers NP   │ Uttarakhand — UNESCO WHS; flowers          │
│ Valmiki NP             │ BIHAR — Only National Park in Bihar!       │
│ Betla NP               │ Jharkhand — Tiger, Elephant                │
└────────────────────────┴─────────────────────────────────────────── │
```

> **⭐ BIHAR EXAM MUST-KNOW:** **Valmiki National Park** (West Champaran, Bihar) is the **only National Park in Bihar**. It is also a Tiger Reserve. This is asked in EVERY Bihar exam!

---

## 📌 GS CONCEPT 10: Key Bihar Agriculture Facts

```
┌──────────────────────────────────────────────────────────────────────┐
│              BIHAR AGRICULTURE — EXAM-READY FACTS                   │
├──────────────────────────────────────────────────────────────────────┤
│  • Bihar = Primarily AGRICULTURAL state                              │
│  • ~80% population depends on agriculture                           │
│                                                                      │
│  KEY CROPS OF BIHAR:                                                 │
│  • Rice and Wheat — main food crops                                  │
│  • Maize — Bihar is a top maize producer in India                    │
│  • Litchi — MUZAFFARPUR is litchi capital; GI tagged                 │
│  • Makhana (Fox nuts) — DARBHANGA & MADHUBANI; Bihar produces       │
│    ~85% of world's Makhana! GI tag given.                           │
│  • Shahi Litchi of Muzaffarpur — GI Tag                              │
│  • Katarni Rice (Bhagalpur) — GI Tag; premium variety               │
│  • Magic Mushroom (Champaran) — Medicinal mushroom cultivation       │
│  • Jute — North Bihar along Ganga belt                               │
│  • Sugarcane — West Champaran, Saran districts                       │
│  • Vegetables — Bihar supplies veggies to Delhi, Kolkata            │
│                                                                      │
│  IRRIGATION IN BIHAR:                                                │
│  • Sone Canal System — largest canal system in Bihar                 │
│  • Kosi Barrage — Birpur (Nepal-Bihar border)                        │
│  • Gandak Barrage — Valmikinagar                                     │
│                                                                      │
│  AGRICULTURAL RESEARCH:                                              │
│  • ICAR-RCER (Research Complex for Eastern Region) — Patna          │
│  • Bihar Agricultural University — Sabour, Bhagalpur                │
└──────────────────────────────────────────────────────────────────────┘
```

---

# ══════════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — DAY 18
# ⚠️ DO NOT LOOK AT ANSWERS — SOLVE ALL 50 FIRST!
# ANSWERS ARE AT THE VERY END OF THIS FILE
# ══════════════════════════════════════════════════════

---

# 🖥️ CS QUESTIONS (Q1–Q25) — Queue Data Structure

---

**Q1.** Queue data structure follows which principle?

(A) LIFO (Last In First Out)
(B) FIFO (First In First Out)
(C) Random access
(D) More than one of the above
(E) None of the above

---

**Q2.** In a queue, insertion is done at _______ and deletion is done at _______.

(A) Front, Rear
(B) Rear, Rear
(C) Rear, Front
(D) More than one of the above
(E) None of the above

---

**Q3.** Which condition must be checked BEFORE performing a deletion operation in a queue?

(A) Overflow
(B) Underflow
(C) Whether queue is full
(D) More than one of the above
(E) None of the above

---

**Q4.** Which condition must be checked BEFORE performing an insertion operation in a queue?

(A) Underflow
(B) Whether queue is empty
(C) Overflow
(D) More than one of the above
(E) None of the above

---

**Q5.** The overflow condition for a linear queue implemented with an array of size MAX_SIZE is:

(A) front == 0
(B) rear == 0
(C) rear == MAX_SIZE - 1
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following is a correct application of the QUEUE data structure?

(A) Balancing of parentheses and symbols
(B) Recursion implementation
(C) CPU scheduling (Ready Queue)
(D) More than one of the above
(E) None of the above

---

**Q7.** Which traversal algorithm on a graph uses a QUEUE as its underlying data structure?

(A) Depth-First Search (DFS)
(B) In-order traversal
(C) Breadth-First Search (BFS)
(D) More than one of the above
(E) None of the above

---

**Q8.** Asynchronous data transfer between processes uses which data structure?

(A) Stack
(B) Tree
(C) Queue
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the time complexity of the ENQUEUE operation in a queue implemented using an array?

(A) O(N)
(B) O(log N)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q10.** A linear queue of size 5 has front=2 and rear=4. Elements are at positions 2, 3, 4. If we try to insert a new element, what happens?

(A) Insertion succeeds normally
(B) Underflow occurs
(C) Overflow occurs (even though positions 0 and 1 are free)
(D) More than one of the above
(E) None of the above

---

**Q11.** The problem of memory wastage in a linear queue (when rear reaches MAX_SIZE-1 but front has moved) is solved by:

(A) Increasing the array size dynamically
(B) Using a Circular Queue
(C) Using a Stack instead
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following is the INSERT operation in a queue called?

(A) Push
(B) Pop
(C) Enqueue
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following is NOT an application of Queue?

(A) Printer spooling
(B) Keyboard input buffer
(C) Undo operation in text editor
(D) More than one of the above
(E) None of the above

---

**Q14.** Consider a queue with elements: 10 (front) → 20 → 30 → 40 (rear). After one DEQUEUE and one ENQUEUE of 50, what is the front element?

(A) 10
(B) 20
(C) 30
(D) More than one of the above
(E) None of the above

---

**Q15.** In which type of queue can elements be inserted and deleted from BOTH ends?

(A) Circular Queue
(B) Priority Queue
(C) Double-Ended Queue (Deque)
(D) More than one of the above
(E) None of the above

---

**Q16.** Which data structure is used to implement the READY QUEUE in an Operating System?

(A) Stack
(B) Linked List only
(C) Queue
(D) More than one of the above
(E) None of the above

---

**Q17.** In BFS traversal of a graph, nodes are visited:

(A) In depth-first order, using a stack
(B) Level by level, using a queue
(C) In random order
(D) More than one of the above
(E) None of the above

---

**Q18.** The operation that views the FRONT element of a queue without removing it is called:

(A) Pop
(B) Peek or Front
(C) Dequeue
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following correctly describes a Priority Queue?

(A) Elements are served in FIFO order regardless of value
(B) Elements are served based on their priority, not insertion order
(C) Elements are always removed from the rear
(D) More than one of the above
(E) None of the above

---

**Q20.** A queue is implemented using a singly linked list. The HEAD pointer represents the FRONT and a TAIL pointer represents the REAR. What is the time complexity of ENQUEUE?

(A) O(N)
(B) O(log N)
(C) O(1)
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following statements about Queue is/are TRUE?

(i) Queue uses FIFO principle
(ii) Elements are inserted at the rear and removed from the front
(iii) Queue is used in BFS traversal

(A) Only (i)
(B) Only (i) and (ii)
(C) All of (i), (ii) and (iii)
(D) More than one of the above
(E) None of the above

---

**Q22.** In which scenario would a QUEUE be the most appropriate data structure to use?

(A) Evaluating a postfix expression
(B) Checking if a string is a palindrome
(C) Handling print jobs sent to a shared printer
(D) More than one of the above
(E) None of the above

---

**Q23.** What happens when DEQUEUE is called on an EMPTY queue?

(A) The first inserted element is returned
(B) Zero is returned
(C) UNDERFLOW condition occurs
(D) More than one of the above
(E) None of the above

---

**Q24.** The INPUT-RESTRICTED DEQUE allows:

(A) Insertion at both ends, deletion from one end only
(B) Insertion at one end only, deletion from both ends
(C) Insertion and deletion from both ends
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is true about the difference between Stack and Queue?

(A) Stack uses FIFO; Queue uses LIFO
(B) Stack inserts/deletes from the same end (TOP); Queue inserts at REAR, deletes from FRONT
(C) Stack is used for BFS; Queue is used for DFS
(D) More than one of the above
(E) None of the above

---

# 🌍 GS QUESTIONS (Q26–Q50) — India Geography: Plateau, Soil, Climate, Agriculture

---

**Q26.** Which soil type is best suited for growing COTTON in India?

(A) Alluvial soil
(B) Red soil
(C) Black soil (Regur soil)
(D) More than one of the above
(E) None of the above

---

**Q27.** The Black soil (Regur) is mainly found in which region of India?

(A) Indo-Gangetic Plains
(B) Deccan Plateau (Maharashtra, MP, Gujarat)
(C) Himalayan slopes
(D) More than one of the above
(E) None of the above

---

**Q28.** Which soil type is formed by the process of LEACHING and is found in high rainfall, high temperature regions?

(A) Black soil
(B) Desert soil
(C) Laterite soil
(D) More than one of the above
(E) None of the above

---

**Q29.** The most WIDESPREAD soil type in India, found mainly in the Indo-Gangetic Plains, is:

(A) Red soil
(B) Laterite soil
(C) Alluvial soil
(D) More than one of the above
(E) None of the above

---

**Q30.** Which of the following crops belongs to the KHARIF season?

(A) Wheat
(B) Mustard
(C) Rice
(D) More than one of the above
(E) None of the above

---

**Q31.** The "Father of Green Revolution in India" is:

(A) Norman Borlaug
(B) Dr. Verghese Kurien
(C) M.S. Swaminathan
(D) More than one of the above
(E) None of the above

---

**Q32.** Which revolution in India is related to milk and dairy production?

(A) Green Revolution
(B) Blue Revolution
(C) White Revolution (Operation Flood)
(D) More than one of the above
(E) None of the above

---

**Q33.** The place receiving the HIGHEST average annual rainfall in India is:

(A) Cherrapunji
(B) Mawsynram
(C) Mumbai
(D) More than one of the above
(E) None of the above

---

**Q34.** Approximately what percentage of India's annual rainfall is received during the South-West Monsoon?

(A) 25%
(B) 50%
(C) 75%
(D) More than one of the above
(E) None of the above

---

**Q35.** The ONLY National Park in Bihar is:

(A) Betla National Park
(B) Valmiki National Park
(C) Rajgir Wildlife Sanctuary
(D) More than one of the above
(E) None of the above

---

**Q36.** India is the world's largest producer of which of the following minerals?

(A) Coal
(B) Iron Ore
(C) Mica
(D) More than one of the above
(E) None of the above

---

**Q37.** The largest coalfield in India, "Jharia," is located in which state?

(A) Odisha
(B) West Bengal
(C) Jharkhand
(D) More than one of the above
(E) None of the above

---

**Q38.** Which state is known as the "Spice Garden of India"?

(A) Karnataka
(B) Kerala
(C) Tamil Nadu
(D) More than one of the above
(E) None of the above

---

**Q39.** Muzaffarpur in Bihar is famous for which fruit with a GI tag?

(A) Mango
(B) Banana
(C) Litchi (Shahi Litchi)
(D) More than one of the above
(E) None of the above

---

**Q40.** Which state produces MORE than 90% of India's natural rubber?

(A) Tamil Nadu
(B) Karnataka
(C) Kerala
(D) More than one of the above
(E) None of the above

---

**Q41.** The Gir National Park, the only habitat of the Asiatic Lion in India, is located in:

(A) Rajasthan
(B) Gujarat
(C) Madhya Pradesh
(D) More than one of the above
(E) None of the above

---

**Q42.** Which district of Bihar produces approximately 85% of the world's Makhana (fox nuts)?

(A) Muzaffarpur
(B) Patna
(C) Darbhanga and Madhubani
(D) More than one of the above
(E) None of the above

---

**Q43.** The Kolar Gold Fields (deepest gold mine in India) is located in:

(A) Rajasthan
(B) Jharkhand
(C) Karnataka
(D) More than one of the above
(E) None of the above

---

**Q44.** Which crop season in India runs from October to April and primarily includes wheat, barley, and mustard?

(A) Kharif
(B) Zaid
(C) Rabi
(D) More than one of the above
(E) None of the above

---

**Q45.** The South-West Monsoon normally arrives in Kerala around:

(A) March 1
(B) June 1
(C) August 1
(D) More than one of the above
(E) None of the above

---

**Q46.** Which soil type is DEFICIENT in nitrogen, phosphorus, and organic matter, but is excellent for growing cotton?

(A) Red soil
(B) Alluvial soil
(C) Black soil (Regur)
(D) More than one of the above
(E) None of the above

---

**Q47.** The Kaziranga National Park, famous for the one-horned rhinoceros, is located in:

(A) West Bengal
(B) Assam
(C) Meghalaya
(D) More than one of the above
(E) None of the above

---

**Q48.** Bihar's agriculture is primarily based on which type of soil?

(A) Red soil
(B) Black soil
(C) Alluvial soil
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following statements about the Blue Revolution in India is CORRECT?

(A) It relates to fish production and aquaculture
(B) It relates to milk and dairy
(C) It relates to oilseeds
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following is/are CORRECTLY matched regarding Bihar's agriculture?

(A) Muzaffarpur — Litchi (Shahi Litchi)
(B) Bhagalpur — Katarni Rice
(C) Makhana production — Darbhanga/Madhubani region
(D) More than one of the above
(E) None of the above

---

---
---
---

# ══════════════════════════════════════════════════════
# ✅ ANSWER KEY WITH FULL EXPLANATIONS — DAY 18
# (Check only AFTER you have attempted all 50 questions!)
# ══════════════════════════════════════════════════════

---

## 🖥️ CS ANSWERS (Q1–Q25)

---

### Q1. Answer: **(B) FIFO (First In First Out)**

**Explanation:**
Queue = FIFO. The first element inserted is the first one to be removed — like a line of people at a bank. Stack = LIFO. Never confuse these two in the exam. Option (A) LIFO is Stack's principle, not Queue's.

---

### Q2. Answer: **(C) Rear, Front**

**Explanation:**
In a Queue:
- **INSERTION** (Enqueue) happens at the **REAR** (back of line)
- **DELETION** (Dequeue) happens at the **FRONT** (people leave from front)

This is the fundamental structure of Queue. Option (A) "Front, Rear" is exactly reversed — a classic trap!

---

### Q3. Answer: **(B) Underflow**

**Explanation:**
Before DELETION (Dequeue), we must check if the queue is **empty** — this condition is called **UNDERFLOW**. If we try to delete from an empty queue, it causes underflow error. This was a direct PYQ in TRE 2.0. Overflow is checked before INSERTION, not deletion.

---

### Q4. Answer: **(C) Overflow**

**Explanation:**
Before INSERTION (Enqueue), we must check if the queue is **full** — this condition is called **OVERFLOW**. If we try to insert into a full queue, overflow occurs. The complementary pair: Insertion → check Overflow; Deletion → check Underflow.

---

### Q5. Answer: **(C) rear == MAX_SIZE - 1**

**Explanation:**
In a linear array-based queue, OVERFLOW occurs when `rear == MAX_SIZE - 1` (rear pointer has reached the last valid index). Even if front has moved (leaving free slots at the beginning), the queue reports overflow — this is the main drawback of linear queue!

---

### Q6. Answer: **(C) CPU scheduling (Ready Queue)**

**Explanation:**
CPU scheduling uses Queue (FIFO-based Ready Queue). Options (A) and (B) are STACK applications:
- Balancing parentheses → Stack
- Recursion → Stack
Only CPU scheduling is a Queue application here.

---

### Q7. Answer: **(C) Breadth-First Search (BFS)**

**Explanation:**
BFS uses a Queue to visit nodes level by level. DFS uses a Stack (or recursion). This distinction — BFS→Queue, DFS→Stack — is a perennial BPSC favorite and appeared in TRE 1.0 and TRE 3.0.

---

### Q8. Answer: **(C) Queue**

**Explanation:**
Asynchronous data transfer (e.g., IO Buffers, Pipes between processes) uses **Queue**. Data produced by one process is placed in a queue and consumed by another at a different speed. This is a classic application of Queue, NOT Stack. Direct PYQ from TRE 1.0!

---

### Q9. Answer: **(C) O(1)**

**Explanation:**
ENQUEUE in an array-based queue is O(1) — we simply increment `rear` by 1 and insert the element. No shifting of elements is needed. Same for DEQUEUE — just increment `front`. All basic queue operations are O(1).

---

### Q10. Answer: **(C) Overflow occurs (even though positions 0 and 1 are free)**

**Explanation:**
This is the classic "Memory Wastage" problem of Linear Queue. With front=2 and rear=4 (in a queue of size 5), rear has reached MAX_SIZE-1=4. Even though positions 0 and 1 are free, the linear queue declares OVERFLOW. This is WHY Circular Queue was invented!

---

### Q11. Answer: **(B) Using a Circular Queue**

**Explanation:**
**Circular Queue** solves the memory wastage problem by wrapping the rear pointer back to the beginning using modulo arithmetic: `rear = (rear + 1) % SIZE`. This allows reuse of empty slots at the beginning of the array. (Covered in detail on Day 19!)

---

### Q12. Answer: **(C) Enqueue**

**Explanation:**
- Queue insert = **Enqueue**
- Queue delete = **Dequeue**
- Stack insert = Push
- Stack delete = Pop

Don't confuse Push/Pop (Stack) with Enqueue/Dequeue (Queue)!

---

### Q13. Answer: **(C) Undo operation in text editor**

**Explanation:**
Undo operation uses a **STACK** (LIFO — the most recently done action is undone first). Queue applications include printer spooling ✅ and keyboard buffer ✅. Only "Undo" is NOT a queue application here.

---

### Q14. Answer: **(B) 20**

**Explanation:**
Initial Queue: 10 → 20 → 30 → 40 (front=10, rear=40)

After DEQUEUE: 10 is removed → Queue: 20 → 30 → 40 (front=20)
After ENQUEUE 50: Queue: 20 → 30 → 40 → 50 (front=20, rear=50)

Front element = **20** ✓

---

### Q15. Answer: **(C) Double-Ended Queue (Deque)**

**Explanation:**
**Deque** (Double-Ended Queue) allows insertion AND deletion from BOTH front and rear ends. Circular Queue still inserts at rear and deletes from front. Priority Queue serves based on priority. Deque is the most versatile queue type.

---

### Q16. Answer: **(C) Queue**

**Explanation:**
The **Ready Queue** in an OS is a queue of processes waiting for the CPU. The OS uses Queue structure (typically FIFO or Priority Queue based on scheduling algorithm). This is one of the most important OS applications of Queue.

---

### Q17. Answer: **(B) Level by level, using a queue**

**Explanation:**
BFS = Breadth-First Search = visits nodes **level by level** (all nodes at depth 1 before depth 2, etc.) using a **Queue**. DFS visits nodes depth-first using a **Stack**. Option (A) describes DFS, not BFS.

---

### Q18. Answer: **(B) Peek or Front**

**Explanation:**
**Peek** (also called **Front**) is the operation that returns the value of the front element without removing it. This is analogous to `Top` in a Stack. It's a READ operation, not a modification.

---

### Q19. Answer: **(B)**

**Explanation:**
Priority Queue serves elements based on their **priority value**, not insertion order. A high-priority element is served before a low-priority one, even if it arrived later. It is NOT simple FIFO. Options (A) and (C) are incorrect descriptions of Priority Queue.

---

### Q20. Answer: **(C) O(1)**

**Explanation:**
With a **TAIL pointer** maintained for the linked list, ENQUEUE is O(1) — we simply add a new node at the tail and update the tail pointer. Without a tail pointer, ENQUEUE would be O(N). Most implementations maintain the tail pointer, so ENQUEUE = O(1).

---

### Q21. Answer: **(D) More than one of the above**

**Explanation:**
ALL THREE statements are correct:
- (i) Queue uses FIFO ✓
- (ii) Insert at rear, remove from front ✓
- (iii) BFS uses Queue ✓

When multiple options are correct → **(D)**. Classic BPSC trap! Always check if all options are correct before choosing A/B/C.

---

### Q22. Answer: **(C) Handling print jobs sent to a shared printer**

**Explanation:**
Print spooling is the textbook application of Queue — jobs are added to the queue as they arrive and printed in FIFO order. Options (A) and (B) use Stack: postfix evaluation → Stack; palindrome check → Stack (or two pointers, but typically Stack is used for comparing characters).

---

### Q23. Answer: **(C) UNDERFLOW condition occurs**

**Explanation:**
When DEQUEUE is called on an **empty queue**, an **UNDERFLOW** condition occurs — this is an error condition. Proper implementations check `isEmpty()` before calling dequeue and handle this gracefully. Never assume the queue has elements without checking.

---

### Q24. Answer: **(B) Insertion at one end only, deletion from both ends**

**Explanation:**
- **Input-restricted Deque**: INSERT at ONE end only; DELETE from BOTH ends
- **Output-restricted Deque**: INSERT at BOTH ends; DELETE from ONE end only

Don't confuse these. Option (A) describes OUTPUT-restricted Deque (deletion from one end only).

---

### Q25. Answer: **(B)**

**Explanation:**
Key difference: Stack inserts AND deletes from the **same end** (TOP). Queue inserts at REAR (back) and deletes from FRONT. Option (A) is reversed (Stack=LIFO, Queue=FIFO). Option (C) is reversed (BFS uses Queue, DFS uses Stack).

---

## 🌍 GS ANSWERS (Q26–Q50)

---

### Q26. Answer: **(C) Black soil (Regur soil)**

**Explanation:**
Black soil (Regur) is specifically called **"Cotton Soil"** because it is ideal for cotton cultivation. It has high water-retaining capacity and is rich in minerals needed by cotton. Found in Deccan Plateau — Maharashtra, MP, Gujarat, AP.

---

### Q27. Answer: **(B) Deccan Plateau (Maharashtra, MP, Gujarat)**

**Explanation:**
Black/Regur soil is formed from volcanic lava (Deccan Trap basalt) and is mainly found in the **Deccan Plateau** region — Maharashtra, Madhya Pradesh, Gujarat, parts of AP. NOT in Indo-Gangetic Plains (that's Alluvial soil) or Himalayan slopes (Mountain soil).

---

### Q28. Answer: **(C) Laterite soil**

**Explanation:**
**Laterite soil** is formed by the process of **leaching** — in high rainfall + high temperature regions, soluble minerals (calcium, nitrogen, phosphorus) are washed away by rain, leaving behind iron and aluminium oxides (giving it a brick-red color). Found in Kerala, Karnataka, Assam.

---

### Q29. Answer: **(C) Alluvial soil**

**Explanation:**
**Alluvial soil** is the most widespread soil type in India, covering the entire Indo-Gangetic Plain (Bihar, UP, Punjab, Haryana, WB). It is the most fertile soil and supports the most agriculture. Largest area under any single soil type in India.

---

### Q30. Answer: **(C) Rice**

**Explanation:**
**Rice** is a Kharif crop — sown in June-July with onset of Southwest Monsoon, harvested in October-November. Wheat and Mustard are **Rabi** crops (winter crops). This is a frequently asked basic agriculture question in BPSC.

---

### Q31. Answer: **(C) M.S. Swaminathan**

**Explanation:**
**M.S. Swaminathan** is the Father of Green Revolution in India. He introduced High Yielding Variety (HYV) seeds of wheat and rice in India in the 1960s-70s. Norman Borlaug (Option A) is the Father of Green Revolution in the WORLD. Dr. Verghese Kurien = Father of White Revolution (milk/dairy).

---

### Q32. Answer: **(C) White Revolution (Operation Flood)**

**Explanation:**
**White Revolution** = Milk/Dairy production. Also called **Operation Flood**, launched by NDDB (National Dairy Development Board). Father = **Dr. Verghese Kurien**. The **Amul** cooperative model was the foundation of White Revolution.

---

### Q33. Answer: **(B) Mawsynram**

**Explanation:**
**Mawsynram** (Meghalaya) holds the record for the highest average annual rainfall in India (~11,871 mm) and is also recognized as the wettest place on Earth. **Cherrapunji** (also in Meghalaya) was the earlier record-holder. Both are in the same region (East Khasi Hills) but Mawsynram gets slightly more rain on average.

---

### Q34. Answer: **(C) 75%**

**Explanation:**
The **South-West Monsoon** (June-September) accounts for approximately **75%** of India's total annual rainfall. This makes it the most critical season for Indian agriculture. The remaining 25% comes from retreating monsoon, western disturbances (winter), and pre-monsoon showers.

---

### Q35. Answer: **(B) Valmiki National Park**

**Explanation:**
**Valmiki National Park** in **West Champaran district of Bihar** is the ONLY National Park in Bihar. It is also a Tiger Reserve. This is one of the most frequently asked Bihar geography questions — know it cold! Betla NP is in **Jharkhand**, not Bihar.

---

### Q36. Answer: **(C) Mica**

**Explanation:**
India is the **world's largest producer of MICA**. Major mica-producing states: Jharkhand (largest in India), Rajasthan, Andhra Pradesh. Coal — India is 2nd or 3rd worldwide. Iron ore — India is a top producer but not necessarily the largest globally. Mica is the correct answer for "world's largest."

---

### Q37. Answer: **(C) Jharkhand**

**Explanation:**
**Jharia** coalfield is located in **Jharkhand** (Dhanbad district) and is the largest coalfield in India. Jharkhand is the largest coal-producing state in India. This is a direct PYQ question that has appeared multiple times in Bihar competitive exams!

---

### Q38. Answer: **(B) Kerala**

**Explanation:**
**Kerala** is known as the "**Spice Garden of India**" because it produces a wide variety of spices — pepper, cardamom, cloves, ginger, turmeric, cinnamon. Kerala also produces 90%+ of India's rubber. Karnataka is called "Sandalwood State" or known for coffee.

---

### Q39. Answer: **(C) Litchi (Shahi Litchi)**

**Explanation:**
**Muzaffarpur** in Bihar is famous for the **Shahi Litchi** — it has a GI (Geographical Indication) tag. Muzaffarpur is called the "Litchi Capital of India." Bihar produces approximately 40% of India's total litchi production. This Bihar-specific fact appears in every exam!

---

### Q40. Answer: **(C) Kerala**

**Explanation:**
**Kerala** produces more than **90% of India's natural rubber**. The rubber plantations are concentrated in the districts of Kottayam, Ernakulam, and Idukki. India is the world's 4th largest natural rubber producer, almost entirely due to Kerala.

---

### Q41. Answer: **(B) Gujarat**

**Explanation:**
**Gir National Park** in **Gujarat** is the ONLY habitat of the **Asiatic Lion** in the world. As of the latest census, ~700 lions live in Gir. This is one of India's most significant conservation successes. Ranthambore (Rajasthan) and Kanha (MP) are tiger reserves.

---

### Q42. Answer: **(C) Darbhanga and Madhubani**

**Explanation:**
**Makhana (Fox nuts/Lotus seeds)** is Bihar's unique crop. The **Darbhanga** and **Madhubani** districts of North Bihar produce approximately **85% of the world's makhana**. Makhana has a GI tag. This is a very important Bihar-specific agriculture question!

---

### Q43. Answer: **(C) Karnataka**

**Explanation:**
The **Kolar Gold Fields (KGF)** in **Karnataka** is the deepest gold mine in India (and among the deepest in the world, over 3 km deep). It became famous internationally, and the blockbuster film "KGF" is set here. Most of KGF mines are currently closed or minimally operational due to economic viability.

---

### Q44. Answer: **(C) Rabi**

**Explanation:**
**Rabi** season: sown in October-November, harvested in March-April. Main crops: Wheat, Barley, Gram (Chickpea), Mustard, Peas, Linseed. Kharif = monsoon crops (June-Oct). Zaid = summer crops (March-June). Wheat is India's most important Rabi crop.

---

### Q45. Answer: **(B) June 1**

**Explanation:**
The Southwest Monsoon normally arrives in **Kerala around June 1** (±7 days). This date is fixed in the Indian meteorological calendar. It then progresses northward, covering the entire country by approximately July 15. The Kerala arrival date is a classic exam fact!

---

### Q46. Answer: **(C) Black soil (Regur)**

**Explanation:**
Black soil is deficient in nitrogen, phosphorus, and organic matter but is EXCELLENT for cotton (due to its high water-retention capacity, iron and magnesium content). Alluvial soil is also good for cotton but the question specifically asks for the soil that is deficient in N, P, and organic matter while being best for cotton — that uniquely describes Black soil.

---

### Q47. Answer: **(B) Assam**

**Explanation:**
**Kaziranga National Park** is located in **Assam**, in the floodplains of the Brahmaputra river. It is a UNESCO World Heritage Site and is famous for the **Indian one-horned rhinoceros** (Rhinoceros unicornis). It also has the highest density of tigers among all national parks in India.

---

### Q48. Answer: **(C) Alluvial soil**

**Explanation:**
Bihar lies almost entirely in the **Indo-Gangetic Plain**, so its agriculture is primarily based on **Alluvial soil** brought by rivers like Ganga, Sone, Gandak, and Kosi. This alluvial soil makes Bihar one of India's most agriculturally productive states for rice, wheat, maize, and vegetables.

---

### Q49. Answer: **(A) It relates to fish production and aquaculture**

**Explanation:**
**Blue Revolution** relates to **fish production, fisheries, and aquaculture**. White Revolution = milk/dairy. Yellow Revolution = oilseeds. Option (A) is the correct and only correct statement here, so the answer is (A), not (D).

---

### Q50. Answer: **(D) More than one of the above**

**Explanation:**
ALL THREE are correct Bihar agriculture facts:
- (A) Muzaffarpur — Shahi Litchi (GI tagged) ✓
- (B) Bhagalpur — Katarni Rice (GI tagged premium variety) ✓
- (C) Makhana — Darbhanga/Madhubani region (85% world production) ✓

All three correct → Classic **(D) — More than one of the above** trap!

---

# ══════════════════════════════════════════════════════
# 📋 DAY 18 — QUICK REVISION SUMMARY
# ══════════════════════════════════════════════════════

## 🖥️ CS Quick Facts:
```
1.  Queue = FIFO (First In, First Out)
2.  Insert = ENQUEUE at REAR | Delete = DEQUEUE from FRONT
3.  Before DELETE → check UNDERFLOW (queue empty?)
4.  Before INSERT → check OVERFLOW (queue full?)
5.  Linear queue overflow: rear == MAX_SIZE - 1
6.  Linear queue problem: MEMORY WASTAGE (solution: Circular Queue)
7.  Queue applications: BFS, CPU scheduling, Printer spooling, Async transfer
8.  NOT Queue: Symbol balancing, Recursion, Undo → all use STACK
9.  BFS → Queue | DFS → Stack
10. All basic queue operations (enqueue/dequeue/peek) → O(1)
11. Deque = Double-Ended Queue (insert/delete from BOTH ends)
12. Input-restricted Deque: insert ONE end, delete BOTH ends
13. Priority Queue → implemented with Binary Heap (Min or Max)
14. Linked list queue with tail pointer → ENQUEUE O(1)
15. Ready Queue in OS → Queue data structure
```

## 🌍 GS Quick Facts:
```
1.  Alluvial soil = Most widespread, Indo-Gangetic Plains, Wheat+Rice+Sugarcane
2.  Black soil = Regur/Cotton Soil, Deccan Plateau, self-ploughing
3.  Laterite soil = formed by LEACHING, Tea+Coffee+Rubber crops
4.  Red soil = Peninsular India, iron gives red color, Groundnut
5.  Kharif = Rice, Cotton, Jute (June-Oct, monsoon)
6.  Rabi = Wheat, Mustard, Barley (Oct-Apr, winter)
7.  Green Revolution Father (India) = M.S. Swaminathan
8.  White Revolution Father = Dr. Verghese Kurien (milk/Amul)
9.  Blue Revolution = Fish/Aquaculture
10. Highest rainfall India = MAWSYNRAM (Meghalaya)
11. SW Monsoon arrives Kerala = June 1; ~75% of India's rainfall
12. Only NP in Bihar = VALMIKI National Park (West Champaran)
13. Jharia = Largest coalfield (Jharkhand)
14. India = World's largest Mica producer
15. Muzaffarpur = Litchi capital | Darbhanga = Makhana capital
16. Kerala = Spice Garden of India + 90%+ rubber
17. Gir NP (Gujarat) = Only Asiatic Lion habitat
18. Kaziranga NP (Assam) = One-horned Rhino, UNESCO WHS
```

---

> **Score yourself:** CS ___/25 | GS ___/25 | Total ___/50
> **Target:** 45+ → Topper Level | 40–44 → Good | Below 38 → Re-read concepts
> **Next:** Day 19 → Circular Queue & Deque | GS: India Climate — Monsoon in detail
