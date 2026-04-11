# 📅 DAY 26 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## CS Topic: Red-Black Trees, AVL Trees, Balanced Trees & Spanning Trees
## GS Topic: Biology — Human Reproduction + Plant Reproduction

> **Target:** TOP RANK | Phase 1 — Foundation | Week 4
> **Date:** Use this sheet every revision cycle
> **Format:** 25 CS MCQs + 25 GS MCQs (BPSC 5-option format) | Answers at END

---

# ═══════════════════════════════════════════════
# PART A — COMPUTER SCIENCE
# Red-Black Trees | AVL Trees | Balanced Trees | Spanning Trees | Heaps
# ═══════════════════════════════════════════════

---

## 🔴 SECTION 1: RED-BLACK TREE

### What is a Red-Black Tree?

A Red-Black Tree is a **self-balancing Binary Search Tree (BST)** where every node has an extra attribute: a **colour** — either RED or BLACK.

It automatically balances itself during insertions and deletions, so the height never becomes too large.

**WHY DO WE NEED IT?**

A normal BST can become a straight line (skewed) if we insert sorted data:

```
Insert: 10, 20, 30, 40, 50  →  Skewed BST
10
  \
   20
     \
      30
        \
         40
           \
            50

Search time = O(n) ← TERRIBLE!
```

Red-Black Tree prevents this. Search is always O(log n).

---

### 🔴⚫ The 5 Red-Black Tree Properties (MEMORIZE ALL 5!)

```
┌─────────────────────────────────────────────────────────────┐
│              5 RED-BLACK TREE PROPERTIES                     │
├─────────────────────────────────────────────────────────────┤
│ Property 1: Every node is RED or BLACK                       │
│                                                             │
│ Property 2: ROOT is always BLACK                            │
│             (Even if we insert at root → colour it BLACK)   │
│                                                             │
│ Property 3: Every LEAF (NIL node) is BLACK                  │
│             (NULL pointers = BLACK sentinel nodes)          │
│                                                             │
│ Property 4: If a node is RED →                              │
│             BOTH its children must be BLACK                  │
│             (No two consecutive RED nodes allowed)          │
│                                                             │
│ Property 5: All simple paths from any node to              │
│             its descendant NIL leaves must have             │
│             the SAME number of BLACK nodes                  │
│             (This is called BLACK HEIGHT)                   │
└─────────────────────────────────────────────────────────────┘
```

### BPSC KEY FACTS ⭐

| Fact | Value |
|------|-------|
| Root colour | Always **BLACK** |
| Newly inserted non-root node | Initially **RED** |
| No two consecutive | **RED nodes** allowed |
| NIL leaf nodes | Treated as **BLACK** |
| Height of RB Tree with n nodes | At most **2 log(n+1)** |
| Operations time complexity | O(log n) — guaranteed |

---

### 📊 Red-Black Tree DIAGRAM

```
         13(B)               ← Root is BLACK
        /     \
      8(R)    17(B)          ← RED node, children must be BLACK
     /   \    /   \
   1(B) 11(B) 15(R) 25(R)   ← No two RED nodes in a row
  / \   / \   / \   / \
 N  N  N  N  N  N  N  N     ← NULL = BLACK sentinel nodes
 
B = BLACK, R = RED, N = NULL (BLACK)
Black Height of this tree = 3
(Count BLACK nodes from root to NULL: 13→8→1→NULL = B,B,B = 3 black nodes)
```

---

### 🔄 Rotations in Red-Black Tree

When inserting or deleting, RB Tree may violate properties. We fix violations using:
1. **Recolouring** — change node colours
2. **Rotations** — restructure tree (Left Rotation / Right Rotation)

```
LEFT ROTATION at node X:
     X                Y
    / \              / \
   A   Y    →       X   C
      / \          / \
     B   C        A   B

RIGHT ROTATION at node Y:
       Y              X
      / \            / \
     X   C    →     A   Y
    / \                / \
   A   B              B   C
```

**Rotations are O(1) operations** — they only change pointers, not data.

---

### ⚠️ PYQ TRAP QUESTIONS (BPSC frequently asks these!)

**PYQ Trap 1:** "In a Red-Black tree, a newly inserted node is coloured ___"
→ Answer: **RED** (We colour it RED first, then fix violations if any)

**PYQ Trap 2:** "The root of a Red-Black tree is always ___"
→ Answer: **BLACK** (Root is ALWAYS black — this is a fixed property)

**PYQ Trap 3:** "What is NOT a property of a Red-Black tree?"
→ Trick option: "All paths from root to leaves have same total nodes" — This is FALSE! Only BLACK nodes must be equal, not total nodes.

---

## 🌳 SECTION 2: AVL TREE

### What is an AVL Tree?

AVL Tree (Adelson-Velsky and Landis Tree) is another **self-balancing BST** that is STRICTER than Red-Black Tree.

**Balance Factor (BF) = Height(Left Subtree) − Height(Right Subtree)**

**Rule: |Balance Factor| must be ≤ 1 for EVERY node**

```
┌──────────────────────────────────────────┐
│        BALANCE FACTOR RULES               │
│                                          │
│  BF = -1, 0, or +1 → Node is BALANCED   │
│  BF = -2 or +2      → VIOLATION!         │
│                       Must ROTATE         │
└──────────────────────────────────────────┘
```

### AVL Tree Example:

```
        30 (BF = 0)
       /   \
    20(BF=0) 40(BF=0)
   /   \
 10     25
(BF=0) (BF=0)

Calculate BF of 30:
Height(Left subtree of 30) = 2  (goes to 10 or 25)
Height(Right subtree of 30) = 1  (just 40)
BF of 30 = 2 - 1 = 1  ← VALID (|1| ≤ 1)
```

### AVL vs Red-Black Tree Comparison:

```
┌──────────────────┬─────────────────┬──────────────────────┐
│ Feature          │ AVL Tree         │ Red-Black Tree        │
├──────────────────┼─────────────────┼──────────────────────┤
│ Balance type     │ Strictly balanced│ Loosely balanced      │
│ Balance factor   │ |BF| ≤ 1         │ No BF — uses colours  │
│ Search speed     │ Faster (shorter) │ Slightly slower       │
│ Insert/Delete    │ More rotations   │ Fewer rotations       │
│ Used in          │ Databases,       │ Linux kernel,         │
│                  │ Lookup tables    │ Java TreeMap/TreeSet  │
│ Height guarantee │ 1.44 log(n)      │ 2 log(n+1)           │
└──────────────────┴─────────────────┴──────────────────────┘
```

**KEY PYQ FACT:** AVL tree is **more strictly balanced** than RB Tree. AVL is preferred for **search-heavy** applications. RB Tree preferred for **insert/delete-heavy** applications.

---

## 🌲 SECTION 3: SPANNING TREE

### Definition:

A **Spanning Tree** of a connected graph G with **N vertices** is a subgraph that:
- Includes **ALL N vertices** of G
- Has **exactly N-1 edges**
- Has **NO cycles** (it is a tree)
- Is **connected** (all vertices reachable)

```
┌────────────────────────────────────────┐
│    SPANNING TREE FORMULA               │
│                                        │
│    N vertices → N-1 edges              │
│    ALWAYS! No exceptions!              │
└────────────────────────────────────────┘
```

### Diagram Example:

```
Original Graph G (5 vertices, 7 edges):      Spanning Tree (5 vertices, 4 edges):

    1 ─── 2                                       1 ─── 2
    │ ╲   │ ╲                                     │         \
    │  ╲  │  ╲                                   │          3
    │   ╲ │   ╲                                  │
    5 ─── 3 ─── 4                                5 ─── 3 ─── 4

Multiple spanning trees possible from same graph!
```

### Minimum Spanning Tree (MST):

An MST is a spanning tree with the **minimum total edge weight**.

**Two famous algorithms to find MST:**

```
┌────────────────────────────────────────────────────────┐
│  1. KRUSKAL'S ALGORITHM                                │
│     → Sort all edges by weight (ascending)             │
│     → Keep adding minimum weight edge                  │
│     → Skip edge if it forms a CYCLE                    │
│     → Stop when N-1 edges selected                     │
│     → Uses: Disjoint Set (Union-Find)                  │
│     → Time: O(E log E)                                 │
│                                                        │
│  2. PRIM'S ALGORITHM                                   │
│     → Start from any vertex                            │
│     → Always add minimum weight edge to nearest vertex │
│     → Uses: Priority Queue / Min-Heap                  │
│     → Time: O(E log V) with binary heap                │
└────────────────────────────────────────────────────────┘
```

**KEY PYQ FACTS:**
- Spanning tree of N vertices always has **N-1 edges** ← Most asked!
- Maximum number of spanning trees for complete graph Kn = **n^(n-2)** (Cayley's formula)
- For complete graph K4: spanning trees = 4^(4-2) = 4² = **16**
- MST may not be unique if edges have equal weights

---

## 🔺 SECTION 4: HEAP (Binary Heap)

### What is a Heap?

A **Heap** is a **Complete Binary Tree** (filled level by level, left to right) with the **Heap Property**.

```
┌──────────────────────────────────────────────┐
│  MAX-HEAP PROPERTY:                           │
│  Parent ≥ Both children (root = maximum)      │
│                                               │
│  MIN-HEAP PROPERTY:                           │
│  Parent ≤ Both children (root = minimum)      │
└──────────────────────────────────────────────┘
```

### Heap Diagram:

```
MAX-HEAP:                    MIN-HEAP:
        90                          1
       /  \                        / \
      80   70                     5   3
     / \  / \                    / \ / \
    50  60 40 30                8  6 4  7

Root = 90 (maximum)            Root = 1 (minimum)
```

### Heap Array Representation:

A heap is stored in an **array** (not linked nodes):

```
For node at index i (0-based indexing):
  Left child  → index 2i + 1
  Right child → index 2i + 2
  Parent      → index (i-1)/2

Max-Heap array:  [90, 80, 70, 50, 60, 40, 30]
                   0   1   2   3   4   5   6
```

### Heap Operations (Time Complexity):

```
┌────────────────────────────────────┐
│  HEAP TIME COMPLEXITIES            │
│                                    │
│  Insert:       O(log n)            │
│  Delete Max:   O(log n)            │
│  Get Max/Min:  O(1) ← ROOT!       │
│  Heapify:      O(n)                │
│  Heap Sort:    O(n log n)          │
│  Build Heap:   O(n)                │
└────────────────────────────────────┘
```

**KEY PYQ FACT:** Heap is the **best data structure for Priority Queue** implementation.

---

## 🧠 SECTION 5: B-TREE & B+ TREE (Quick Reference)

| Feature | B-Tree | B+ Tree |
|---------|--------|---------|
| Data stored | All nodes | Only leaf nodes |
| Leaf nodes linked | No | Yes (linked list) |
| Search | Varies | Always O(log n) |
| Used in | File systems | Database indexes |
| Range queries | Slow | Fast (linked leaves) |

**KEY PYQ FACT:** B+ Tree stores **data only at leaf nodes**. Leaves are **linked** for range queries. Used in **database indexing** (MySQL InnoDB uses B+ Tree).

---

## 📊 SECTION 6: COMPLETE COMPLEXITY TABLE (Must Memorize!)

```
┌────────────────────┬──────────────┬──────────────┬──────────────┐
│ Data Structure     │ Search       │ Insert       │ Delete       │
├────────────────────┼──────────────┼──────────────┼──────────────┤
│ Unsorted Array     │ O(n)         │ O(1) end     │ O(n)         │
│ Sorted Array       │ O(log n)     │ O(n)         │ O(n)         │
│ Linked List        │ O(n)         │ O(1) front   │ O(n)         │
│ BST (avg)          │ O(log n)     │ O(log n)     │ O(log n)     │
│ BST (worst/skewed) │ O(n)         │ O(n)         │ O(n)         │
│ AVL Tree           │ O(log n)     │ O(log n)     │ O(log n)     │
│ Red-Black Tree     │ O(log n)     │ O(log n)     │ O(log n)     │
│ Heap (Max/Min)     │ O(n)         │ O(log n)     │ O(log n)     │
│ Hash Table (avg)   │ O(1)         │ O(1)         │ O(1)         │
└────────────────────┴──────────────┴──────────────┴──────────────┘
```

**TRICK TO REMEMBER:** AVL and RB Trees GUARANTEE O(log n) for ALL operations — unlike plain BST which can degrade to O(n).

---

## 🔑 SECTION 7: QUICK REVISION BULLETS (Night Revision — 5 Min!)

```
╔══════════════════════════════════════════════════════╗
║         DAY 26 CS — TOPPER QUICK REVISION            ║
╠══════════════════════════════════════════════════════╣
║ 1. RB Tree root = BLACK (ALWAYS)                     ║
║ 2. New non-root insertion = RED first                 ║
║ 3. No two consecutive RED nodes                       ║
║ 4. All paths → same BLACK node count                  ║
║ 5. AVL: |Balance Factor| ≤ 1 for every node          ║
║ 6. Spanning Tree: N vertices → N-1 edges             ║
║ 7. MST algorithms: Kruskal's + Prim's                ║
║ 8. Heap: Complete Binary Tree + Heap Property        ║
║ 9. Get Max in Max-Heap = O(1) (just read root)       ║
║ 10. Heap Sort = O(n log n)                           ║
║ 11. B+ Tree: data at leaves, leaves linked           ║
║ 12. RB Tree used in Linux kernel, Java TreeMap       ║
╚══════════════════════════════════════════════════════╝
```

---

# ═══════════════════════════════════════════════
# PART B — GENERAL SCIENCE (GS)
# Biology: Human Reproduction + Plant Reproduction
# (As per Day 26 Plan + Lucent GK Coverage)
# ═══════════════════════════════════════════════

---

## 🌸 SECTION 8: HUMAN REPRODUCTIVE SYSTEM

### Male Reproductive System:

```
┌──────────────────────────────────────────────────────────────┐
│              MALE REPRODUCTIVE ORGANS                         │
├──────────────────────┬───────────────────────────────────────┤
│ Organ                │ Function                               │
├──────────────────────┼───────────────────────────────────────┤
│ Testes (2)           │ Produce SPERM + hormone TESTOSTERONE  │
│ Epididymis           │ Sperm maturation and storage           │
│ Vas Deferens         │ Carries sperm from epididymis          │
│ Seminal Vesicles     │ Secrete fluid (60% of semen)           │
│ Prostate Gland       │ Secretes alkaline fluid (protects sperm│
│                      │ from acid in vagina)                   │
│ Cowper's Gland       │ Pre-ejaculatory fluid (lubrication)    │
│ Urethra              │ Passage for both urine and semen       │
│ Penis                │ Copulatory organ                       │
└──────────────────────┴───────────────────────────────────────┘
```

**KEY FACT:** Testes are located OUTSIDE the body (in scrotum) because sperm production requires temperature **2-3°C LOWER** than body temperature (37°C). So scrotum temperature ≈ 34-35°C.

### Female Reproductive System:

```
┌──────────────────────────────────────────────────────────────┐
│              FEMALE REPRODUCTIVE ORGANS                       │
├──────────────────────┬───────────────────────────────────────┤
│ Organ                │ Function                               │
├──────────────────────┼───────────────────────────────────────┤
│ Ovaries (2)          │ Produce EGGS (ova) + hormones         │
│                      │ ESTROGEN and PROGESTERONE              │
│ Fallopian Tubes (2)  │ Egg travels from ovary to uterus      │
│                      │ FERTILIZATION occurs here!            │
│ Uterus               │ Where fetus develops (9 months)        │
│ Cervix               │ Lower narrow part of uterus            │
│ Vagina               │ Birth canal + receives semen           │
│ Endometrium          │ Inner lining of uterus                 │
│                      │ (Sheds during menstruation)            │
└──────────────────────┴───────────────────────────────────────┘
```

---

### 🔄 Menstrual Cycle (28 days — Approximate)

```
DAY 1-5:    MENSTRUATION PHASE
            ↓ Endometrium lining sheds
            ↓ Estrogen and Progesterone low

DAY 6-13:   FOLLICULAR (PROLIFERATIVE) PHASE
            ↓ FSH (from pituitary) stimulates follicle growth
            ↓ Estrogen rises → endometrium thickens

DAY 14:     OVULATION
            ↓ LH SURGE triggers release of egg from ovary
            ↓ Most fertile day!
            ↓ Egg survives only 12-24 hours

DAY 15-28:  LUTEAL (SECRETORY) PHASE
            ↓ Corpus luteum forms at ovulation site
            ↓ Progesterone rises → maintains endometrium
            ↓ If no fertilization → progesterone drops
            ↓ Back to Day 1 (menstruation)
```

**KEY HORMONES:**

```
┌────────────────────────────────────────────────────┐
│  REPRODUCTIVE HORMONES — BPSC MUST KNOW            │
├────────────┬───────────────────────────────────────┤
│ FSH        │ Follicle Stimulating Hormone           │
│            │ Made by: Anterior Pituitary            │
│            │ Function: Stimulates follicle growth   │
│            │           + sperm production (males)   │
│ LH         │ Luteinising Hormone                    │
│            │ Made by: Anterior Pituitary            │
│            │ Function: Triggers OVULATION in females│
│            │           + Testosterone in males      │
│ Estrogen   │ Made by: Ovaries (mainly)              │
│            │ Function: Female secondary sex chars   │
│            │           + endometrium thickening     │
│ Progesterone│ Made by: Corpus luteum / Placenta     │
│            │ Function: MAINTAINS PREGNANCY          │
│            │           + prepares endometrium        │
│ Testosterone│ Made by: Testes (Leydig cells)        │
│            │ Function: Male secondary sex chars,    │
│            │           sperm production             │
│ HCG        │ Human Chorionic Gonadotropin           │
│            │ Made by: Placenta (after implantation) │
│            │ Function: BASIS OF PREGNANCY TEST      │
└────────────┴───────────────────────────────────────┘
```

---

### 🥚 Fertilization and Development

```
STEP 1: OVULATION → Egg released from ovary

STEP 2: FERTILIZATION
        ↓ Sperm meets egg in FALLOPIAN TUBE
        ↓ ONE sperm penetrates egg
        ↓ Zygote formed (46 chromosomes)
        ↓ Sperm: 23 chromosomes (X or Y)
        ↓ Egg: 23 chromosomes (always X)
        ↓ Girl = XX (X from sperm + X from egg)
        ↓ Boy = XY (Y from sperm + X from egg)
        ↓ SEX DETERMINED BY FATHER'S SPERM!

STEP 3: CLEAVAGE (Cell division)
        Zygote → 2 cells → 4 cells → 8 cells...
        Morula (16-32 cells) → Blastocyst

STEP 4: IMPLANTATION
        Blastocyst implants in UTERINE WALL
        (about 6-7 days after fertilization)

STEP 5: EMBRYO → FETUS → BIRTH (9 months / 40 weeks)

GESTATION PERIOD:
  Humans:    280 days (40 weeks / 9 months)
  Elephant:  660 days (longest in land mammals)
  Dog:       63 days
  Cat:       65 days
  Rabbit:    30 days
```

---

### 👶 Placenta — "The Lifeline"

```
┌─────────────────────────────────────────────┐
│          FUNCTIONS OF PLACENTA              │
│                                             │
│  1. Nutrition: Passes glucose, amino acids  │
│     from mother to fetus                    │
│                                             │
│  2. Respiration: O₂ → fetus, CO₂ ← fetus  │
│                                             │
│  3. Excretion: Removes waste from fetus     │
│                                             │
│  4. Hormone secretion: HCG, Progesterone,  │
│     Estrogen (after 3 months)              │
│                                             │
│  5. Barrier: Protects from some pathogens  │
│              (but NOT all — HIV can cross) │
└─────────────────────────────────────────────┘
```

---

### 🌱 SECTION 9: PLANT REPRODUCTION

#### Types of Plant Reproduction:

```
ASEXUAL REPRODUCTION IN PLANTS
(No gametes, offspring genetically identical — clones)

1. VEGETATIVE PROPAGATION:
   → Stem: Potato (tubers), Ginger (rhizome), Onion (bulb)
             Sugarcane (stem cutting), Rose (stem cutting)
   → Root: Dahlia, Sweet potato (tuberous roots)
   → Leaf:  Bryophyllum (leaf buds at margins!)
             Begonia

2. SPORE FORMATION:
   → Fungi (Rhizopus), Mosses, Ferns
   → Spores are asexual reproductive units

3. BUDDING:
   → Yeast (unicellular fungus)
   → Hydra (animal but classic example)

4. FRAGMENTATION:
   → Spirogyra (algae) — breaks into pieces,
     each piece grows into new organism

5. TISSUE CULTURE (Modern/Artificial):
   → In vitro (in laboratory glass)
   → Small tissue → full plant
   → Used for: Orchids, potato, banana,
     disease-free plants, endangered species
```

**BPSC SPECIAL FACTS:**

| Plant | Reproductive Part | Type |
|-------|------------------|------|
| Potato | Tuber (stem) | Vegetative |
| Ginger | Rhizome (stem) | Vegetative |
| Onion | Bulb (modified stem) | Vegetative |
| Bryophyllum | Leaf margins (adventitious buds) | Vegetative |
| Rose | Stem cutting | Vegetative |
| Yeast | Budding | Asexual |
| Spirogyra | Fragmentation | Asexual |
| Ferns | Spores | Asexual |
| Amoeba | Binary fission | Asexual |

---

#### Sexual Reproduction in Plants (Flowers):

```
FLOWER STRUCTURE:
                    🌸
        ___________/|\___________
       |           | |           |
    CALYX       COROLLA      ANDROECIUM   GYNOECIUM
  (Sepals)     (Petals)      (Stamens)   (Pistil/Carpel)
   Protects    Attracts       MALE         FEMALE
   bud         pollinators    PART         PART
                              |               |
                           Filament       Stigma
                           Anther    →    Style
                           (Pollen)       Ovary → Ovule
                                          (contains eggs)
```

**POLLINATION Types:**

```
┌─────────────────────────────────────────────────────┐
│  SELF-POLLINATION (Autogamy)                        │
│  Pollen from SAME flower or SAME plant              │
│  Example: Wheat, Rice, Pea (Mendel's plant!)        │
│  Advantage: No dependency on external agents        │
│                                                     │
│  CROSS-POLLINATION (Allogamy)                       │
│  Pollen from DIFFERENT plant of same species        │
│  Agents: Wind (Anemophily), Water (Hydrophily),    │
│           Insects (Entomophily), Birds (Ornithophily)│
│  Example: Maize (wind), Lotus (insects)             │
└─────────────────────────────────────────────────────┘
```

---

### 🦠 SECTION 10: ASEXUAL REPRODUCTION — ORGANISMS

```
┌────────────────┬───────────────────┬────────────────────────┐
│ Organism       │ Method            │ Key Feature             │
├────────────────┼───────────────────┼────────────────────────┤
│ Amoeba         │ Binary Fission    │ Cell splits into 2      │
│ Bacteria       │ Binary Fission    │ Fastest reproduction    │
│ Yeast          │ Budding           │ Small bud grows off     │
│ Hydra          │ Budding           │ Bud grows → new Hydra  │
│ Planaria       │ Regeneration      │ Each part → new worm   │
│ Starfish       │ Regeneration      │ Cut arm → new starfish │
│ Spirogyra      │ Fragmentation     │ Breaks, each part grows│
│ Ferns          │ Spore formation   │ Sporangia produce spores│
│ Bryophyllum    │ Leaf buds         │ Buds on leaf margins   │
│ Plasmodium     │ Multiple Fission  │ One cell → many cells  │
│ (Malaria)      │ (Schizogony)      │                        │
└────────────────┴───────────────────┴────────────────────────┘
```

---

### 🔬 SECTION 11: REPRODUCTIVE HEALTH (Quick Facts)

```
IMPORTANT DEFINITIONS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STI (Sexually Transmitted Infections) — formerly STD:
  → HIV/AIDS (Virus — No cure, only managed)
  → Syphilis (Bacteria — Treponema pallidum)
  → Gonorrhoea (Bacteria — Neisseria gonorrhoeae)
  → Chlamydia (Bacteria)
  → Hepatitis B (Virus)

CONTRACEPTION METHODS:
  Barrier: Condom (protects against STIs too!), diaphragm
  Hormonal: Birth control pills (Estrogen + Progesterone)
  Intrauterine: IUD (Copper-T)
  Surgical: Vasectomy (male), Tubectomy (female)

FERTILITY TREATMENTS:
  IVF = In Vitro Fertilization
        Fertilization outside body → implanted in uterus
        "Test tube baby" — Louise Brown (1978, first IVF baby)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

### 🌟 BPSC SPECIAL: IMPORTANT BIOLOGY FACTS (PYQ-Based)

```
╔════════════════════════════════════════════════════════╗
║         MUST-MEMORIZE BIOLOGY FACTS                    ║
╠════════════════════════════════════════════════════════╣
║ 1. Fertilization in humans occurs in: FALLOPIAN TUBE  ║
║ 2. Sex determined by: FATHER (sperm carries X or Y)   ║
║ 3. Twins:                                              ║
║    Identical (Monozygotic) → 1 zygote splits into 2   ║
║    Fraternal (Dizygotic)   → 2 eggs fertilized by     ║
║                              2 different sperms        ║
║ 4. Pregnancy test detects: HCG hormone                 ║
║ 5. Progesterone = "Hormone of Pregnancy"              ║
║ 6. Estrogen = Female sex hormone, produced by ovary   ║
║ 7. Testosterone = Male sex hormone, produced by testes║
║ 8. Ginger reproduces by: RHIZOME (modified stem)      ║
║ 9. Potato reproduces by: TUBER (modified stem)        ║
║ 10. Bryophyllum reproduces by: LEAVES                 ║
║ 11. Yeast reproduces by: BUDDING                      ║
║ 12. Plasmodium (malaria parasite): MULTIPLE FISSION   ║
║ 13. First IVF baby: Louise Brown (1978, UK)           ║
║ 14. Placenta: Connects mother and fetus               ║
║ 15. Gestation period of humans: 280 days              ║
╚════════════════════════════════════════════════════════╝
```

---

# ═══════════════════════════════════════════════
# PRACTICE QUESTIONS — DAY 26
# ═══════════════════════════════════════════════

> ⚠️ **IMPORTANT INSTRUCTION:**
> Attempt ALL 50 questions BEFORE looking at answers.
> Answers are provided ONLY AFTER all 50 questions.
> This builds real exam skills — do NOT scroll to answers early!

---

## 📘 SECTION I: COMPUTER SCIENCE QUESTIONS (Q1–Q25)
### Topic: Red-Black Trees | AVL Trees | Balanced Trees | Spanning Trees | Heaps

---

**Q1.** Which of the following is a property of a Red-Black Tree?

(A) The root is always RED
(B) Every leaf (NIL) node is RED
(C) The root is always BLACK
(D) New nodes are always inserted as BLACK
(E) All paths from root must have equal total nodes

---

**Q2.** In a Red-Black Tree, when a new non-root node is inserted, what colour is it initially given?

(A) BLACK
(B) WHITE
(C) RED
(D) More than one of the above
(E) None of the above

---

**Q3.** Consider a Red-Black Tree. If a node is RED, which of the following statements is/are CORRECT?

(i) Both its children must be BLACK
(ii) Its parent must be BLACK
(iii) It can never be the root

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (i) and (iii)
(D) More than one of the above (all three)
(E) None of the above

---

**Q4.** What is the maximum height of a Red-Black Tree with n nodes?

(A) log(n)
(B) n/2
(C) 2 log(n+1)
(D) More than one of the above
(E) None of the above

---

**Q5.** In an AVL Tree, the Balance Factor of a node is defined as:

(A) Right subtree height − Left subtree height
(B) Left subtree height − Right subtree height
(C) Left subtree nodes − Right subtree nodes
(D) More than one of the above (A and B are equivalent definitions)
(E) None of the above

---

**Q6.** Which of the following Balance Factor values makes an AVL tree node UNBALANCED and requires rotation?

(A) -1
(B) 0
(C) +1
(D) More than one of the above (-1 and +1 both require rotation)
(E) None of the above (only -2 or +2 requires rotation)

---

**Q7.** A spanning tree of a graph with N vertices has exactly how many edges?

(A) N
(B) N+1
(C) N-1
(D) More than one of the above
(E) None of the above

---

**Q8.** Which algorithm uses a GREEDY approach by sorting ALL edges first and then adding minimum weight edges while avoiding cycles to find MST?

(A) Prim's Algorithm
(B) Dijkstra's Algorithm
(C) Floyd-Warshall Algorithm
(D) More than one of the above
(E) Kruskal's Algorithm

---

**Q9.** A complete graph K4 has 4 vertices. How many spanning trees does it have? (Use Cayley's formula: n^(n-2))

(A) 4
(B) 8
(C) 16
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following statements about a Binary Min-Heap is/are CORRECT?

(i) The root contains the minimum element
(ii) It is a complete binary tree
(iii) Retrieving the minimum element takes O(1) time

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q11.** What is the time complexity of INSERTING an element into a Binary Heap?

(A) O(1)
(B) O(log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q12.** In which data structure is a heap BEST implemented?

(A) Linked List
(B) Array
(C) Doubly Linked List
(D) More than one of the above (A and B are equally efficient)
(E) None of the above

---

**Q13.** In a MAX-Heap stored as an array with 0-based indexing, where is the RIGHT CHILD of node at index i?

(A) 2i
(B) 2i + 1
(C) 2i + 2
(D) More than one of the above
(E) (i+1)/2

---

**Q14.** Which of the following is the CORRECT sequence of complexities from LOWEST to HIGHEST?

(A) O(1) < O(n) < O(log n) < O(n log n) < O(n²)
(B) O(1) < O(log n) < O(n) < O(n log n) < O(n²)
(C) O(log n) < O(1) < O(n) < O(n²) < O(n log n)
(D) More than one of the above
(E) None of the above

---

**Q15.** Which self-balancing BST is used in the LINUX KERNEL scheduler and Java's TreeMap/TreeSet?

(A) AVL Tree
(B) B-Tree
(C) Red-Black Tree
(D) More than one of the above (AVL and Red-Black are equally used)
(E) None of the above

---

**Q16.** In a B+ Tree (as used in database indexing), which of the following is/are TRUE?

(i) All actual data records are stored ONLY at leaf nodes
(ii) Leaf nodes are linked together as a linked list
(iii) Internal nodes store only KEYS (not actual data)

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are true)
(E) None of the above

---

**Q17.** Consider inserting values 1, 2, 3, 4, 5 into a normal (unbalanced) BST in this order. What is the search complexity in the WORST CASE?

(A) O(log n)
(B) O(n log n)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q18.** Which of the following correctly distinguishes AVL Tree from Red-Black Tree?

(A) AVL Tree is more strictly balanced; Red-Black Tree allows more imbalance
(B) Red-Black Tree is more strictly balanced; AVL Tree allows more imbalance
(C) Both maintain exactly the same balance
(D) More than one of the above
(E) None of the above

---

**Q19.** The operation of fixing a violation in a Red-Black Tree uses two techniques. Which are they?

(A) Splitting and Merging
(B) Recolouring and Rotations
(C) Hashing and Chaining
(D) More than one of the above
(E) None of the above

---

**Q20.** What is the time complexity of BUILDING a heap from an unsorted array of n elements?

(A) O(n log n)
(B) O(n²)
(C) O(n)
(D) More than one of the above
(E) None of the above

---

**Q21.** A graph has 8 vertices and is connected. Its spanning tree will have exactly:

(A) 8 edges
(B) 6 edges
(C) 7 edges
(D) More than one of the above
(E) None of the above

---

**Q22.** Which traversal of a BST gives elements in SORTED (ascending) order?

(A) Preorder (Root → Left → Right)
(B) Postorder (Left → Right → Root)
(C) Inorder (Left → Root → Right)
(D) More than one of the above
(E) Level-order traversal

---

**Q23.** In the context of Red-Black Trees, "Black Height" means:

(A) The height of the tree measured only by black nodes in any path
(B) The total number of black nodes in the tree
(C) The number of black nodes on any path from a node to a descendant NIL leaf (not counting the node itself)
(D) More than one of the above
(E) None of the above

---

**Q24.** Prim's Algorithm for finding Minimum Spanning Tree is BEST implemented using which data structure?

(A) Stack
(B) Queue
(C) Priority Queue (Min-Heap)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following statements about a spanning tree is/are CORRECT?

(i) It includes all vertices of the original graph
(ii) It contains no cycles
(iii) It may have more than N-1 edges for a graph of N vertices

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (i, ii, and iii are all correct)
(E) None of the above

---

## 🌿 SECTION II: GENERAL SCIENCE (BIOLOGY) QUESTIONS (Q26–Q50)
### Topic: Human Reproduction + Plant Reproduction + Asexual Reproduction

---

**Q26.** Where does FERTILIZATION primarily occur in the human female reproductive system?

(A) Uterus
(B) Ovary
(C) Cervix
(D) More than one of the above
(E) Fallopian Tube

---

**Q27.** Sex determination in humans is primarily decided by:

(A) Mother's egg chromosome
(B) Father's sperm chromosome
(C) The temperature at the time of fertilization
(D) More than one of the above
(E) None of the above

---

**Q28.** Which of the following hormones is detected in a PREGNANCY TEST?

(A) Estrogen
(B) Progesterone
(C) LH (Luteinising Hormone)
(D) More than one of the above
(E) HCG (Human Chorionic Gonadotropin)

---

**Q29.** Which hormone is called the "hormone of pregnancy" because it maintains the uterine lining during pregnancy?

(A) Estrogen
(B) FSH
(C) Testosterone
(D) More than one of the above
(E) Progesterone

---

**Q30.** Testes are located outside the body in the scrotum because:

(A) They need more blood supply than the body can provide internally
(B) Sperm production requires a temperature 2–3°C LOWER than body temperature
(C) They produce hormones that are needed externally
(D) More than one of the above
(E) None of the above

---

**Q31.** Which of the following correctly pairs the plant with its method of vegetative reproduction?

(i) Potato — Tuber (modified stem)
(ii) Ginger — Rhizome (modified stem)
(iii) Bryophyllum — Leaf margins (adventitious buds)

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q32.** Yeast reproduces asexually by which method?

(A) Binary Fission
(B) Budding
(C) Fragmentation
(D) More than one of the above
(E) Spore Formation

---

**Q33.** The malaria parasite Plasmodium reproduces inside human red blood cells by which method?

(A) Binary Fission
(B) Budding
(C) Multiple Fission (Schizogony)
(D) More than one of the above
(E) None of the above

---

**Q34.** Which of the following is/are example(s) of asexual reproduction by FRAGMENTATION?

(A) Yeast
(B) Spirogyra
(C) Hydra
(D) More than one of the above (Yeast and Hydra)
(E) None of the above

---

**Q35.** The first "test tube baby" (IVF baby) was born in:

(A) 1970 in USA
(B) 1985 in India
(C) 1978 in UK (Louise Brown)
(D) More than one of the above
(E) None of the above

---

**Q36.** FSH (Follicle Stimulating Hormone) is secreted by which gland?

(A) Ovaries
(B) Thyroid Gland
(C) Anterior Pituitary Gland
(D) More than one of the above
(E) None of the above

---

**Q37.** Which of the following functions is/are performed by the PLACENTA?

(i) Transfer of nutrition from mother to fetus
(ii) Exchange of O₂ and CO₂ between mother and fetus
(iii) Production of HCG hormone during pregnancy

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are correct)
(E) None of the above

---

**Q38.** In plants, pollen transfer by INSECTS is called:

(A) Anemophily
(B) Hydrophily
(C) Entomophily
(D) More than one of the above
(E) Ornithophily

---

**Q39.** In which part of the flower does the OVULE develop into a SEED after fertilization?

(A) Stigma
(B) Style
(C) Ovary
(D) More than one of the above
(E) None of the above

---

**Q40.** IDENTICAL TWINS (Monozygotic twins) result from:

(A) Two eggs fertilized by two different sperms
(B) A single fertilized egg (zygote) that splits into two
(C) Asexual reproduction in humans
(D) More than one of the above
(E) None of the above

---

**Q41.** Spirogyra is an alga that reproduces asexually by fragmentation. What other type of reproduction can Spirogyra undergo?

(A) Budding
(B) Binary fission
(C) Sexual reproduction (conjugation)
(D) More than one of the above
(E) None of the above

---

**Q42.** The GESTATION PERIOD of a human (time from fertilization to birth) is approximately:

(A) 180 days
(B) 240 days
(C) 280 days (40 weeks)
(D) More than one of the above
(E) None of the above

---

**Q43.** Ovulation (release of egg from ovary) is triggered by a SURGE in which hormone?

(A) FSH
(B) Estrogen
(C) LH (Luteinising Hormone)
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following is the CORRECT statement about TISSUE CULTURE in plants?

(A) It is a method of sexual reproduction
(B) It requires a large piece of plant material (whole branch)
(C) A small piece of plant tissue is grown in nutrient medium to produce a whole plant
(D) More than one of the above
(E) None of the above

---

**Q45.** Testosterone is primarily produced by which cells in the testes?

(A) Sertoli Cells
(B) Leydig Cells (Interstitial Cells)
(C) Spermatogonia
(D) More than one of the above
(E) None of the above

---

**Q46.** Mendel conducted his famous genetics experiments on which plant? What type of pollination does this plant primarily use?

(A) Maize — Cross pollination
(B) Pea (Pisum sativum) — Self pollination
(C) Wheat — Cross pollination
(D) More than one of the above
(E) None of the above

---

**Q47.** Which of the following is/are SEXUALLY TRANSMITTED INFECTIONS (STIs)?

(i) HIV/AIDS
(ii) Syphilis (caused by Treponema pallidum)
(iii) Hepatitis B

(A) Only (i)
(B) Only (i) and (ii)
(C) Only (ii) and (iii)
(D) More than one of the above (all three are STIs)
(E) None of the above

---

**Q48.** In human reproduction, the CORPUS LUTEUM forms after ovulation. What is its PRIMARY function?

(A) Producing FSH
(B) Producing Estrogen only
(C) Producing Progesterone to maintain the uterine lining
(D) More than one of the above
(E) None of the above

---

**Q49.** Which contraceptive method provides protection against BOTH pregnancy AND sexually transmitted infections?

(A) Birth control pills
(B) Copper-T (IUD)
(C) Condom
(D) More than one of the above (pills + condom together)
(E) None of the above

---

**Q50.** A starfish can regenerate a complete new organism from a severed arm. Planaria (flatworm) can regrow any missing part. This type of reproduction is called:

(A) Fragmentation
(B) Budding
(C) Regeneration
(D) More than one of the above (Fragmentation and Regeneration are same)
(E) None of the above

---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 26
# (Scroll here ONLY after attempting all 50 questions!)
# ═══════════════════════════════════════════════

---

## COMPUTER SCIENCE ANSWERS (Q1–Q25)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q1  | **(C)** | Root is ALWAYS BLACK — fundamental RB Tree property |
| Q2  | **(C) RED** | Newly inserted node is always coloured RED first, then violations fixed |
| Q3  | **(D) More than one** | All three (i, ii, iii) are correct! If RED: children=BLACK, parent=BLACK, can't be root |
| Q4  | **(C) 2 log(n+1)** | RB Tree maximum height guarantee |
| Q5  | **(B)** | BF = Left Height − Right Height (standard definition) |
| Q6  | **(E) None of the above** | -1, 0, +1 are ALL balanced. Only BF = -2 or +2 requires rotation — trick question! |
| Q7  | **(C) N-1** | Spanning tree of N vertices = EXACTLY N-1 edges. Most asked PYQ! |
| Q8  | **(E) Kruskal's** | Kruskal sorts ALL edges first → adds min weight edge avoiding cycles |
| Q9  | **(C) 16** | Cayley's: n^(n-2) = 4^(4-2) = 4² = 16 |
| Q10 | **(D) More than one** | All three are correct: root = min, complete binary tree, O(1) get-min |
| Q11 | **(B) O(log n)** | Insert in heap → add at end + bubble up = O(log n) |
| Q12 | **(B) Array** | Heap is best implemented as array (efficient parent-child index formulas) |
| Q13 | **(C) 2i+2** | 0-based: left child = 2i+1, right child = 2i+2 |
| Q14 | **(B)** | Correct order: O(1) < O(log n) < O(n) < O(n log n) < O(n²) |
| Q15 | **(C) Red-Black Tree** | Java TreeMap/TreeSet, Linux CFS scheduler use Red-Black Trees |
| Q16 | **(D) More than one** | ALL THREE are true for B+ Tree |
| Q17 | **(C) O(n)** | Inserting 1,2,3,4,5 in order → skewed BST → worst case O(n) |
| Q18 | **(A)** | AVL is MORE strictly balanced (|BF|≤1 at every node) vs RB Tree |
| Q19 | **(B)** | RB Tree violations fixed by Recolouring AND Rotations |
| Q20 | **(C) O(n)** | Building heap from array = O(n) — NOT O(n log n). Common trick! |
| Q21 | **(C) 7 edges** | 8 vertices → 8-1 = 7 edges in spanning tree |
| Q22 | **(C) Inorder** | Inorder traversal of BST → sorted ascending order |
| Q23 | **(C)** | Black height = count of black nodes from node to NIL leaf (not counting node itself) |
| Q24 | **(C) Priority Queue (Min-Heap)** | Prim's uses Min-Heap for efficient vertex selection |
| Q25 | **(B) Only (i) and (ii)** | Spanning tree: all vertices ✓, no cycles ✓, BUT always exactly N-1 edges (iii is FALSE) |

---

## GENERAL SCIENCE (BIOLOGY) ANSWERS (Q26–Q50)

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| Q26 | **(E) Fallopian Tube** | FERTILIZATION occurs in Fallopian Tube — most common PYQ! |
| Q27 | **(B) Father's sperm** | Egg always has X; sperm has X or Y → father determines sex |
| Q28 | **(E) HCG** | Pregnancy test detects HCG hormone produced by placenta |
| Q29 | **(E) Progesterone** | Progesterone = "hormone of pregnancy" — maintains uterine lining |
| Q30 | **(B)** | Sperm production needs 34-35°C (2-3°C below body temp 37°C) |
| Q31 | **(D) More than one** | ALL THREE are correct! Potato=tuber, Ginger=rhizome, Bryophyllum=leaf buds |
| Q32 | **(B) Budding** | Yeast reproduces by budding — small bud grows off parent cell |
| Q33 | **(C) Multiple Fission** | Plasmodium = Multiple Fission (Schizogony) inside RBCs |
| Q34 | **(B) Spirogyra** | Only Spirogyra reproduces by fragmentation. Yeast=budding, Hydra=budding |
| Q35 | **(C) 1978 in UK** | Louise Brown — first IVF baby — born 1978 in UK |
| Q36 | **(C) Anterior Pituitary** | FSH and LH both secreted by Anterior Pituitary gland |
| Q37 | **(D) More than one** | Placenta does ALL three: nutrition transfer, gas exchange, HCG production |
| Q38 | **(C) Entomophily** | Insect pollination = Entomophily (Ento = insect) |
| Q39 | **(C) Ovary** | Ovule (inside ovary) → seed; ovary wall → fruit |
| Q40 | **(B)** | Identical twins = ONE zygote splits into two (same genetic material) |
| Q41 | **(C) Sexual reproduction** | Spirogyra undergoes conjugation (sexual) besides fragmentation (asexual) |
| Q42 | **(C) 280 days** | Human gestation = 280 days = 40 weeks = ~9 months |
| Q43 | **(C) LH** | LH SURGE on Day 14 triggers ovulation — most asked reproductive hormone fact! |
| Q44 | **(C)** | Tissue culture = small tissue piece grown in nutrient medium in lab |
| Q45 | **(B) Leydig Cells** | Testosterone produced by Leydig (interstitial) cells in testes |
| Q46 | **(B) Pea — Self pollination** | Mendel used Pea (Pisum sativum); pea is self-pollinating |
| Q47 | **(D) More than one** | HIV, Syphilis, AND Hepatitis B are ALL STIs |
| Q48 | **(C)** | Corpus luteum's PRIMARY function = secreting Progesterone |
| Q49 | **(C) Condom** | ONLY condom protects against BOTH pregnancy AND STIs |
| Q50 | **(C) Regeneration** | Starfish and Planaria = Regeneration (not mere fragmentation) |

---

## 📊 SCORE EVALUATION

```
┌────────────────────────────────────────────┐
│  CS Score (Q1-25):   _____ / 25            │
│  GS Score (Q26-50):  _____ / 25            │
│  TOTAL:              _____ / 50            │
├────────────────────────────────────────────┤
│  48-50: TOPPER LEVEL 🏆                   │
│  43-47: Excellent — On Track ✅            │
│  35-42: Good — Review Weak Areas           │
│  25-34: Revise Concepts Again 📖           │
│  <25:   Re-read concepts before next test  │
└────────────────────────────────────────────┘
```

---

## 🎯 TOPPER STRATEGY — OPTION D/E AWARENESS

> **BPSC TRE Pattern:** Option D ("More than one of the above") is correct 20–25% of the time!

**Questions where Option D was correct today:**
- Q3 (RB Tree RED node properties — ALL THREE correct)
- Q10 (Min-Heap properties — ALL THREE correct)
- Q16 (B+ Tree — ALL THREE correct)
- Q31 (Plant vegetative reproduction — ALL THREE correct)
- Q37 (Placenta functions — ALL THREE correct)
- Q47 (STIs — ALL THREE are STIs)

**LESSON:** When you see a question with statements (i), (ii), (iii) — DON'T rush to pick one. Read all carefully. BPSC often makes ALL statements correct to trap students who stop reading after finding one correct answer.

---

## 📝 NIGHT REVISION — 5 BULLET POINTS (Write from memory)

Before sleeping, write these 5 things from memory (don't look):

1. ______ (RB Tree root colour) ______ (New node colour)
2. Balance Factor in AVL = ______ , violation at BF = ______
3. Spanning Tree with N vertices = ______ edges
4. Fertilization in humans occurs in ______
5. Sex determination: Boy = ______ + X, Girl = X + ______

**Answers:** 1. BLACK, RED | 2. Left−Right height, ±2 | 3. N-1 | 4. Fallopian Tube | 5. Y+X, X+X

---

*Day 26 of 170 Complete — BPSC TRE 4.0 | Target: TOP RANK*
*CS Topic: Red-Black Tree, AVL Tree, Spanning Tree, Heap*
*GS Topic: Biology — Human and Plant Reproduction*
