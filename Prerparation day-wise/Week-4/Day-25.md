# 📅 DAY 25 — BPSC TRE 4.0 TOPPER GUIDE
## CS: Binary Search Tree (BST) — Complete Mastery
## GS: Physics — Electricity, Current, Circuits & Magnetism
### Phase 1 | Week 4 | Target: TOP RANK

---

> **🎯 Today's Targets:**
> - CS: Master BST property, operations (Search/Insert/Delete), Catalan numbers, traversal tricks
> - GS: Master Electricity — Ohm's Law, P=I²R, circuits, magnetism, nuclear physics
> - Solve: 25 CS + 25 GS PYQ-style questions (answers ONLY at very end)
> - Key PYQ: C(4) = 14 distinct BSTs | Inorder of BST = sorted | Skewed BST = O(n)

---

# ═══════════════════════════════════════════════
# 🖥️ PART 1: COMPUTER SCIENCE
## BINARY SEARCH TREE (BST) — COMPLETE TOPPER GUIDE
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: WHAT IS A BST?

A **Binary Search Tree** is a **Binary Tree** with a special ordering property that makes searching very efficient.

```
BST PROPERTY (The Golden Rule):
For EVERY node X in the BST:

  ALL values in LEFT subtree of X  <  X.data
  ALL values in RIGHT subtree of X  >  X.data

This must hold for EVERY node, not just the root!
```

### Simple Example — Is this a BST?

```
        8
       / \
      3   10
     / \    \
    1   6    14
       / \
      4   7

Check BST property at EVERY node:
  Node 8: left subtree {1,3,4,6,7} all < 8 ✓  |  right subtree {10,14} all > 8 ✓
  Node 3: left {1} < 3 ✓  |  right {4,6,7} all > 3 ✓
  Node 10: left = empty ✓  |  right {14} > 10 ✓
  Node 6: left {4} < 6 ✓  |  right {7} > 6 ✓

YES → This is a valid BST ✓
```

### Counter-Example — NOT a BST:

```
        8
       / \
      3   10
     / \    \
    1   12   14
           ← 12 is in LEFT subtree of 8, but 12 > 8
             This VIOLATES BST property!
```

> ⚠️ **BPSC PYQ TRAP:** Students check only the immediate parent-child relationship.
> You must verify that **ALL nodes in the left subtree** are less than the root,
> not just the direct left child.

---

## 📌 SECTION 2: BST NODE STRUCTURE

```cpp
// C++ BST Node
struct Node {
    int data;
    Node* left;    // points to left child (smaller values)
    Node* right;   // points to right child (larger values)
};
```

```java
// Java BST Node
class Node {
    int data;
    Node left;
    Node right;
    Node(int d) { data = d; left = null; right = null; }
}
```

---

## 📌 SECTION 3: BST SEARCH OPERATION

This is why BST is powerful — searching is like **binary search on a sorted array**!

```
ALGORITHM: Search(root, key)
  if root == NULL → return NOT FOUND
  if key == root.data → return FOUND!
  if key < root.data → Search(root.LEFT, key)   ← go left
  if key > root.data → Search(root.RIGHT, key)  ← go right
```

### Traced Example — Search for 6 in our BST:

```
        8             ← key 6 < 8 → go LEFT
       / \
      3   10          ← key 6 > 3 → go RIGHT
     / \    \
    1   6    14       ← key 6 == 6 → FOUND! ✓
       / \
      4   7

Steps: 8 → 3 → 6 = 3 comparisons = O(height) = O(log n) average
```

### Search Complexity:

```
┌───────────────────────┬──────────────────────────────────────┐
│    CASE               │   TIME COMPLEXITY                    │
├───────────────────────┼──────────────────────────────────────┤
│ Best Case             │ O(1) — element is at root            │
│ Average Case          │ O(log n) — balanced BST              │
│ Worst Case            │ O(n) — completely skewed BST         │
└───────────────────────┴──────────────────────────────────────┘
```

> ⚠️ **BPSC PYQ TRAP:** "BST search is always O(log n)"
> **Answer: FALSE** — It is O(log n) on AVERAGE (balanced BST).
> Worst case is O(n) when BST is SKEWED (degenerate).

---

## 📌 SECTION 4: SKEWED BST — THE WORST CASE

If you insert elements in **sorted order** into a BST, you get a completely skewed tree:

```
Insert: 1, 2, 3, 4, 5 (sorted order) → Creates RIGHT-SKEWED BST:

  1
   \
    2
     \
      3
       \
        4
         \
          5

HEIGHT = n-1 = 4  (for 5 nodes)
SEARCH = O(n) = same as Linear Search → BST loses all advantage!

Insert: 5, 4, 3, 2, 1 (reverse sorted) → Creates LEFT-SKEWED BST:
5
 \    (wait — it's actually left skewed)
  4
   ...
```

> 🔑 **KEY INSIGHT:** Inserting elements in sorted/reverse-sorted order creates a
> degenerate BST (a linked list). This is why **self-balancing BSTs** (AVL, Red-Black)
> were invented — to prevent this worst case.

---

## 📌 SECTION 5: BST INSERT OPERATION

Insertion always happens at a **LEAF position**:

```
ALGORITHM: Insert(root, key)
  if root == NULL → create new node with key, return it
  if key < root.data → root.left = Insert(root.left, key)
  if key > root.data → root.right = Insert(root.right, key)
  return root
```

### Traced Example — Insert 5 into BST:

```
ORIGINAL BST:          INSERT 5:
      8                     8
     / \       5 < 8,      / \
    3   10     go left →  3   10
   / \    \    5 > 3,    / \    \
  1   6    14  go right→ 1   6    14
     / \        5 < 6,      / \
    4   7       go left →  4   7
                5 > 4,    /
                go right→5 (inserted here!)
                
RESULT:
      8
     / \
    3   10
   / \    \
  1   6    14
     / \
    4   7
   /
  5   ← new leaf node
```

**Time: O(log n) average, O(n) worst case (skewed)**

---

## 📌 SECTION 6: BST DELETE OPERATION — THREE CASES

Deletion is the most complex BST operation. Three cases:

### Case 1: Delete a LEAF node (easiest)

```
Delete 4 from BST:
      8                   8
     / \                 / \
    3   10    →         3   10
   / \    \            / \    \
  1   6    14         1   6    14
     / \                   \
    4   7                   7
    ↑
  delete this leaf — just remove it
```

### Case 2: Delete a node with ONE child

```
Delete 10 from BST (10 has only right child 14):
      8                   8
     / \                 / \
    3   10    →         3   14
   / \    \            / \
  1   6    14         1   6
     / \                 / \
    4   7               4   7

Replace deleted node with its only child
```

### Case 3: Delete a node with TWO children (hardest)

```
Delete 3 from BST (3 has two children: 1 and 6):

METHOD: Replace with INORDER SUCCESSOR (smallest in right subtree)
        OR replace with INORDER PREDECESSOR (largest in left subtree)

Inorder Successor of 3 = 4 (smallest in right subtree of 3)

Step 1: Copy 4 into node 3's position
Step 2: Delete 4 from its original position

BEFORE:        AFTER (delete 3, replace with 4):
    8                8
   / \              / \
  3   10   →       4   10
 / \    \         / \    \
1   6    14       1   6    14
   / \                 \
  4   7                 7
```

> 🔑 **PYQ FACT:** Inorder Successor of a node = smallest element in its RIGHT subtree
> Inorder Predecessor of a node = largest element in its LEFT subtree

---

## 📌 SECTION 7: TRAVERSALS ON BST — THE GOLDEN RULE

```
Given the BST:
      8
     / \
    3   10
   / \    \
  1   6    14
     / \
    4   7

INORDER (Left → Root → Right):
  Result: 1, 3, 4, 6, 7, 8, 10, 14  ← SORTED! ✓

PREORDER (Root → Left → Right):
  Result: 8, 3, 1, 6, 4, 7, 10, 14

POSTORDER (Left → Right → Root):
  Result: 1, 4, 7, 6, 3, 14, 10, 8
```

> ⭐ **GOLDEN RULE:** Inorder traversal of ANY valid BST ALWAYS gives elements in
> **sorted ascending order**. This is the single most important BST fact in BPSC exams.

---

## 📌 SECTION 8: RECONSTRUCT BST FROM TRAVERSALS

If you are given **PREORDER traversal**, you can reconstruct the BST because:
- First element of Preorder = ROOT
- Then insert remaining elements one by one using BST property

### Example: Preorder = [5, 3, 1, 4, 7, 6]

```
Step 1: Insert 5 → root
      5

Step 2: Insert 3 → 3 < 5 → left of 5
      5
     /
    3

Step 3: Insert 1 → 1 < 5 → go left → 1 < 3 → left of 3
      5
     /
    3
   /
  1

Step 4: Insert 4 → 4 < 5 → go left → 4 > 3 → right of 3
      5
     /
    3
   / \
  1   4

Step 5: Insert 7 → 7 > 5 → right of 5
      5
     / \
    3   7
   / \
  1   4

Step 6: Insert 6 → 6 > 5 → right of 5 → 6 < 7 → left of 7
      5
     / \
    3   7
   / \ /
  1  4 6

Now compute INORDER: 1, 3, 4, 5, 6, 7 ← sorted! ✓
Now compute POSTORDER: 1, 4, 3, 6, 7, 5
```

---

## 📌 SECTION 9: CATALAN NUMBERS — BPSC PYQ GOLD

**How many distinct BSTs can be formed from n distinct keys?**

The answer is the **nth Catalan number**:

```
CATALAN NUMBER FORMULA:
  C(n) = (2n)! / [(n+1)! × n!]

OR the recurrence:
  C(0) = 1
  C(1) = 1
  C(2) = 2
  C(3) = 5
  C(4) = 14   ← MOST TESTED IN BPSC!
  C(5) = 42
  C(6) = 132
```

### Why C(4) = 14? Let's verify with logic:

```
For 4 keys {1, 2, 3, 4}, the root can be:

Root = 1: Left subtree empty, right subtree has {2,3,4} → C(3) = 5 BSTs
Root = 2: Left has {1} → C(1)=1 BST, Right has {3,4} → C(2)=2 BSTs → 1×2 = 2 BSTs
Root = 3: Left has {1,2} → C(2)=2 BSTs, Right has {4} → C(1)=1 BST → 2×1 = 2 BSTs
Root = 4: Left subtree has {1,2,3} → C(3) = 5 BSTs, Right empty → 5×1 = 5 BSTs

TOTAL = 5 + 2 + 2 + 5 = 14 = C(4) ✓
```

```
CATALAN NUMBERS TO MEMORIZE:
┌─────┬────────────────────────────────┐
│ n   │  C(n) = distinct BSTs          │
├─────┼────────────────────────────────┤
│ 0   │  1                             │
│ 1   │  1                             │
│ 2   │  2                             │
│ 3   │  5                             │
│ 4   │  14  ← BPSC MOST TESTED       │
│ 5   │  42                            │
└─────┴────────────────────────────────┘
```

> ⚠️ **BPSC PYQ:** "How many distinct binary search trees can be constructed with 4 keys?"
> **Answer: 14** (Catalan number C(4))
> This has appeared in TRE exams multiple times!

---

## 📌 SECTION 10: BST vs BALANCED BST (AVL TREE)

```
PROBLEM WITH REGULAR BST:
  If insertions happen in sorted order → SKEWED TREE → O(n) operations
  Performance degrades to linear search!

SOLUTION: BALANCED BST
  AVL Tree: Self-balancing BST
  Property: For every node, |height(left) - height(right)| ≤ 1
  
  Maintains balance after every insert/delete using ROTATIONS.
  
AVL TREE ROTATIONS:
  LL Rotation (Right Rotation)
  RR Rotation (Left Rotation)  
  LR Rotation (Left-Right Rotation)
  RL Rotation (Right-Left Rotation)
```

```
COMPARISON: BST vs AVL vs Red-Black Tree

┌─────────────┬────────────┬────────────┬────────────────┐
│  OPERATION  │  BST (avg) │  BST (worst│  AVL Tree      │
├─────────────┼────────────┼────────────┼────────────────┤
│ Search      │  O(log n)  │   O(n)     │  O(log n)      │
│ Insert      │  O(log n)  │   O(n)     │  O(log n)      │
│ Delete      │  O(log n)  │   O(n)     │  O(log n)      │
│ Balance     │  Not guar. │  Not guar. │  GUARANTEED    │
└─────────────┴────────────┴────────────┴────────────────┘
```

---

## 📌 SECTION 11: BST OPERATIONS SUMMARY TABLE

```
┌──────────────────────────┬─────────────┬─────────────────┐
│      OPERATION           │  AVERAGE    │   WORST CASE    │
├──────────────────────────┼─────────────┼─────────────────┤
│ Search                   │  O(log n)   │  O(n) (skewed)  │
│ Insert                   │  O(log n)   │  O(n) (skewed)  │
│ Delete                   │  O(log n)   │  O(n) (skewed)  │
│ Find Min (leftmost leaf) │  O(log n)   │  O(n)           │
│ Find Max (rightmost leaf)│  O(log n)   │  O(n)           │
│ Inorder Traversal        │  O(n)       │  O(n)           │
└──────────────────────────┴─────────────┴─────────────────┘

Min element in BST = LEFTMOST node (keep going left until leaf)
Max element in BST = RIGHTMOST node (keep going right until leaf)
```

---

## 📌 SECTION 12: FINDING MIN & MAX IN BST

```
FIND MINIMUM:
  Start at root → keep going LEFT until NULL
  The leftmost node = MINIMUM

  In our BST:  8 → 3 → 1 → NULL  ∴ Min = 1

FIND MAXIMUM:
  Start at root → keep going RIGHT until NULL
  The rightmost node = MAXIMUM

  In our BST:  8 → 10 → 14 → NULL  ∴ Max = 14
```

---

## 📌 SECTION 13: INORDER SUCCESSOR & PREDECESSOR

```
INORDER SUCCESSOR of node X:
  = Next larger element after X in sorted order
  = Smallest element in X's RIGHT subtree
  
  If X has no right subtree:
  = First ancestor where X is in the LEFT subtree

INORDER PREDECESSOR of node X:
  = Previous smaller element before X in sorted order
  = Largest element in X's LEFT subtree
  
  If X has no left subtree:
  = First ancestor where X is in the RIGHT subtree

EXAMPLE (BST: 8,3,10,1,6,14,4,7):
  Inorder: 1, 3, 4, 6, 7, 8, 10, 14
  
  Inorder Successor of 6 = 7 (next in sorted order)
  Inorder Successor of 7 = 8
  Inorder Predecessor of 6 = 4
  Inorder Predecessor of 3 = 1
```

---

## 📌 SECTION 14: IMPORTANT BST FACTS FOR BPSC

| # | Fact | Answer |
|---|------|--------|
| 1 | BST inorder traversal result | Sorted ascending order |
| 2 | BST search average case | O(log n) |
| 3 | BST search worst case (skewed) | O(n) |
| 4 | Distinct BSTs with 4 keys | 14 (Catalan C(4)) |
| 5 | Distinct BSTs with 3 keys | 5 (Catalan C(3)) |
| 6 | Min element in BST | Leftmost node |
| 7 | Max element in BST | Rightmost node |
| 8 | Inorder successor of node X | Smallest in X's right subtree |
| 9 | When does BST become O(n)? | When it's completely skewed (sorted insertion) |
| 10 | BST vs Array binary search | BST allows dynamic insert/delete; array doesn't |
| 11 | Balanced BST maintains | O(log n) always (unlike regular BST) |
| 12 | AVL tree balance condition | \|height(L) - height(R)\| ≤ 1 at every node |

---

# ═══════════════════════════════════════════════
# 📚 PART 2: GENERAL STUDIES
## PHYSICS — ELECTRICITY, MAGNETISM & NUCLEAR PHYSICS
### Complete BPSC-Level Coverage
# ═══════════════════════════════════════════════

---

## 📌 SECTION 1: ELECTRIC CHARGE & COULOMB'S LAW

```
ELECTRIC CHARGE:
  Two types: Positive charge (+), Negative charge (-)
  Unit: Coulomb (C)
  Electron charge: -1.6 × 10⁻¹⁹ C

COULOMB'S LAW:
  Force between two charges:
  F = k × q₁ × q₂ / r²
  
  where k = 9 × 10⁹ N⋅m²/C² (Coulomb's constant)
        q₁, q₂ = charges
        r = distance between them
  
  Like charges REPEL, Unlike charges ATTRACT
```

---

## 📌 SECTION 2: ELECTRIC CURRENT & OHM'S LAW

```
ELECTRIC CURRENT (I):
  Rate of flow of electric charge
  I = Q/t   (Charge per unit time)
  Unit: Ampere (A)
  
  Conventional current flows: Positive → Negative terminal (outside battery)
  Actual electron flow: Negative → Positive (opposite!)

OHM'S LAW:
  V = IR
  
  V = Voltage (Volt) — potential difference
  I = Current (Ampere)
  R = Resistance (Ohm, Ω)
  
  REARRANGEMENTS:
    I = V/R   (more voltage → more current)
    R = V/I   (more resistance → less current for same voltage)
```

### Visual Circuit Diagram:

```
   +──────────────────────────────────+
   │                                  │
  [Battery: V volts]            [R: Resistance]
   │                                  │
   +──────────────────────────────────+
   
   Current I = V/R flows clockwise (conventional)
```

---

## 📌 SECTION 3: RESISTANCE — FACTORS AND COMBINATIONS

```
FACTORS AFFECTING RESISTANCE:
  R = ρL/A
  
  where:
  ρ (rho) = resistivity (material property)
  L = length of conductor
  A = cross-sectional area
  
  Resistance INCREASES with:  longer wire, smaller cross-section
  Resistance DECREASES with:  shorter wire, larger cross-section
  
  Temperature effect:
  Metals: Resistance INCREASES with temperature
  Semiconductors: Resistance DECREASES with temperature (opposite!)
```

### SERIES COMBINATION:

```
Series Circuit:
  ──[R₁]──[R₂]──[R₃]──
  
  Same current through ALL resistors
  Voltage divides
  R_total = R₁ + R₂ + R₃
  
  Example: 2Ω + 3Ω + 5Ω = 10Ω total
```

### PARALLEL COMBINATION:

```
Parallel Circuit:
         ┌──[R₁]──┐
  ───────┤──[R₂]──├───────
         └──[R₃]──┘
  
  Same voltage across ALL resistors
  Current divides
  1/R_total = 1/R₁ + 1/R₂ + 1/R₃
  
  Example: Two 6Ω resistors in parallel:
  1/R = 1/6 + 1/6 = 2/6 = 1/3
  R_total = 3Ω  ← LESS than 6Ω (any single resistor)!
  
  KEY FACT: Parallel total resistance < smallest individual resistance
```

---

## 📌 SECTION 4: ELECTRICAL POWER — THE MOST TESTED FORMULA

```
ELECTRICAL POWER:
  P = Work done / Time = Energy consumed / Time
  Unit: Watt (W)
  
  P = VI              ... (1)
  P = I²R             ... (2)  [substituting V = IR]
  P = V²/R            ... (3)  [substituting I = V/R]
  
  All three are equivalent and correct!
```

### Power Calculation Examples (BPSC Style):

```
EXAMPLE 1: A heater has resistance 100Ω and current 2A flows through it.
  P = I²R = (2)² × 100 = 4 × 100 = 400 Watts

EXAMPLE 2: If current is DOUBLED (from I to 2I):
  Original power: P₁ = I²R
  New power: P₂ = (2I)²R = 4I²R = 4P₁
  ∴ Power becomes 4 TIMES the original!
  
EXAMPLE 3: If voltage is DOUBLED (from V to 2V):
  P₂ = (2V)²/R = 4V²/R = 4P₁
  ∴ Power becomes 4 TIMES if voltage is doubled!

EXAMPLE 4: If resistance is DOUBLED (from R to 2R), current constant:
  P₂ = I²(2R) = 2I²R = 2P₁
  ∴ Power DOUBLES if resistance doubles (current same)
```

> ⚠️ **BPSC PYQ GOLD:** "If current through a resistor is doubled, how does power change?"
> **Answer: Power becomes 4 times** (P = I²R → quadruples with doubled current)

---

## 📌 SECTION 5: ELECTRICAL ENERGY & UNITS

```
ELECTRICAL ENERGY:
  E = P × t = VIt = I²Rt
  Unit: Joule (J) = Watt × second
  Commercial unit: kilowatt-hour (kWh)
  
  1 kWh = 1 unit of electricity (what you pay for!)
  1 kWh = 1000 W × 3600 s = 3.6 × 10⁶ J = 3.6 MJ

PRACTICAL EXAMPLE:
  A 100W bulb running for 10 hours:
  Energy = 100W × 10h = 1000 Wh = 1 kWh = 1 unit
  Cost depends on your electricity rate (e.g., ₹5/unit → costs ₹5)
```

---

## 📌 SECTION 6: HEATING EFFECT OF CURRENT (JOULE'S LAW)

```
JOULE'S HEATING EFFECT:
  When current flows through a conductor, electrical energy → HEAT
  
  H = I²Rt   (heat generated)
  
  where H = heat (Joules), I = current, R = resistance, t = time
  
  This is why:
  → Electric heater coil gets HOT (high resistance wire)
  → Electric bulb filament glows (tungsten, high resistance, high melting point)
  → Fuse melts when excess current flows (designed to melt at safe threshold)
```

### Applications of Heating Effect:

```
1. ELECTRIC IRON: Nichrome wire (high resistance) heats up
2. ELECTRIC HEATER: Similar principle
3. ELECTRIC BULB: Tungsten filament (mp=3380°C) glows white-hot
4. FUSE WIRE: Low melting point metal (tin-lead alloy) melts at excess current
   Protects circuit from damage
5. ELECTRIC TOASTER, GEYSER: Same heating principle
```

---

## 📌 SECTION 7: MAGNETISM — COMPLETE COVERAGE

```
TYPES OF MAGNETS:
  1. Natural magnet: Magnetite (Fe₃O₄) — "lodestone"
  2. Artificial magnet: Made from iron/steel by induction or electrical means
  3. Permanent magnet: Steel (retains magnetism) — used in speakers, motors
  4. Temporary magnet: Soft iron (loses magnetism) — used in electromagnets

PROPERTIES OF MAGNETS:
  → Like poles REPEL, Unlike poles ATTRACT
  → Magnetic poles always exist in PAIRS (no isolated monopole)
  → If you break a magnet → each piece has BOTH north and south poles
  → Magnetic field lines go from North to South outside the magnet
```

### Earth's Magnetic Field:

```
EARTH AS A MAGNET:
  Earth behaves like a giant bar magnet
  Geographic North = Magnetic South (compass needle's N points there)
  Magnetic field tilted at ~11° from geographic axis
  
  MAGNETIC DECLINATION: Angle between true north and magnetic north
  MAGNETIC INCLINATION (Dip): Angle that Earth's magnetic field makes with horizontal
    At equator: dip = 0°
    At poles: dip = 90°
```

### Electromagnetism:

```
OERSTED'S DISCOVERY (1820):
  "A current-carrying conductor creates a MAGNETIC FIELD around it"
  Direction of field: Right-hand thumb rule
  
ELECTROMAGNET:
  Coil of wire with iron core → becomes magnet when current flows
  Magnetic strength depends on: number of turns, current, core material
  
  Applications:
  → Electric motors, generators
  → Cranes for lifting iron/steel
  → MRI machines (hospitals)
  → Doorbells, electric bells
  → Loudspeakers, earphones
```

---

## 📌 SECTION 8: ELECTROMAGNETIC INDUCTION (FARADAY'S LAW)

```
FARADAY'S LAW:
  "A changing magnetic field induces an EMF (voltage) in a conductor"
  
  Basis of: Electric generators, transformers, inductors

LENZ'S LAW:
  "Induced current opposes the change that caused it"
  (Conservation of energy)

APPLICATIONS:
  GENERATOR: Mechanical energy → Electrical energy (Faraday's principle)
  MOTOR: Electrical energy → Mechanical energy (reverse)
  TRANSFORMER: Changes voltage level using electromagnetic induction
    Step-up: Increases voltage, decreases current
    Step-down: Decreases voltage, increases current
```

---

## 📌 SECTION 9: ATOMIC & NUCLEAR PHYSICS

### Atomic Structure:

```
ATOM STRUCTURE:
  Nucleus: Protons (positive) + Neutrons (neutral)
  Electrons: Negative, orbit nucleus in shells

  Proton mass ≈ Neutron mass ≈ 1.67 × 10⁻²⁷ kg
  Electron mass ≈ 9.11 × 10⁻³¹ kg (much lighter!)
  
  Atomic number (Z) = number of protons
  Mass number (A) = protons + neutrons
  Neutrons = A - Z

MODELS OF ATOM:
  Dalton (1803): Solid sphere — first atomic theory
  Thomson (1897): "Plum pudding" model — electrons embedded in positive sphere
  Rutherford (1911): Nuclear model — nucleus at center, electrons orbit
  Bohr (1913): Electrons in fixed energy orbits (shells)
  Modern: Quantum mechanical model (orbitals, not orbits)
```

### Radioactivity:

```
RADIOACTIVITY (discovered by Henri Becquerel, 1896):
  Some nuclei are UNSTABLE → emit radiation spontaneously

THREE TYPES OF RADIATION:
┌───────────────┬───────────────┬──────────────────────────────┐
│   TYPE        │  COMPOSITION  │     PROPERTIES               │
├───────────────┼───────────────┼──────────────────────────────┤
│ Alpha (α)     │ ₂He⁴ nucleus  │ Heaviest, +2 charge          │
│               │ (2p + 2n)     │ Least penetrating (paper)    │
│               │               │ Most ionizing                │
├───────────────┼───────────────┼──────────────────────────────┤
│ Beta (β)      │ Electron (e⁻) │ Medium penetrating (aluminum)│
│               │               │ -1 charge, medium ionizing   │
├───────────────┼───────────────┼──────────────────────────────┤
│ Gamma (γ)     │ EM radiation  │ MOST penetrating (lead/concrete)│
│               │ (photons)     │ No charge, least ionizing    │
└───────────────┴───────────────┴──────────────────────────────┘

PENETRATING POWER: γ > β > α
IONIZING POWER:    α > β > γ
```

---

## 📌 SECTION 10: NUCLEAR FISSION & FUSION

```
NUCLEAR FISSION:
  Heavy nucleus SPLITS into smaller nuclei + ENERGY
  Used in: ATOM BOMB, Nuclear Reactors (power plants)
  
  Example: U-235 + neutron → Ba + Kr + 3 neutrons + ENERGY
  
  Chain reaction: Each split releases neutrons → causes more splits
  Controlled chain reaction = Nuclear power plant (produces electricity)
  Uncontrolled chain reaction = Atom bomb

NUCLEAR FUSION:
  Light nuclei COMBINE to form heavier nucleus + MORE ENERGY
  Used in: HYDROGEN BOMB (thermonuclear bomb)
  
  Example: H + H → He + ENORMOUS ENERGY
  
  Energy from SUN comes from nuclear fusion!
  Requires extremely HIGH temperature (millions of degrees)
  Fusion produces MORE energy than fission per kg of fuel
  Clean energy (no radioactive waste) — research ongoing (ITER project)
```

```
┌──────────────────┬──────────────────────────────────────────┐
│   COMPARISON     │  FISSION              │   FUSION         │
├──────────────────┼───────────────────────┼──────────────────┤
│ Process          │ Split heavy nucleus   │ Combine light    │
│ Fuel             │ Uranium-235, Plutonium│ Hydrogen (H,D,T) │
│ Energy           │ Less per reaction     │ MORE per reaction│
│ Waste            │ Radioactive waste     │ Less waste       │
│ Weapon           │ Atom bomb             │ H-bomb           │
│ Peacetime        │ Nuclear power plants  │ Future energy!   │
│ Temperature      │ Room temperature OK   │ Millions of °C   │
└──────────────────┴───────────────────────┴──────────────────┘
```

> 🔑 **PYQ FACT:** Sun's energy comes from NUCLEAR FUSION (not fission).
> Atom bomb = fission | Hydrogen bomb = fusion.

---

## 📌 SECTION 11: IMPORTANT PHYSICS UNITS — BPSC COMPLETE

```
┌──────────────────────┬─────────────────────────────────────┐
│   QUANTITY           │   SI UNIT (Symbol)                  │
├──────────────────────┼─────────────────────────────────────┤
│ Length               │ Metre (m)                           │
│ Mass                 │ Kilogram (kg)                       │
│ Time                 │ Second (s)                          │
│ Electric Current     │ Ampere (A)                          │
│ Temperature          │ Kelvin (K)                          │
│ Force                │ Newton (N) = kg⋅m/s²               │
│ Work/Energy          │ Joule (J) = N⋅m                    │
│ Power                │ Watt (W) = J/s                      │
│ Pressure             │ Pascal (Pa) = N/m²                  │
│ Electric charge      │ Coulomb (C)                         │
│ Voltage (Potential)  │ Volt (V) = J/C                     │
│ Resistance           │ Ohm (Ω) = V/A                      │
│ Capacitance          │ Farad (F)                           │
│ Magnetic field       │ Tesla (T)                           │
│ Frequency            │ Hertz (Hz) = cycles/second          │
│ Radioactivity        │ Becquerel (Bq) or Curie (Ci)        │
└──────────────────────┴─────────────────────────────────────┘
```

---

## 📌 SECTION 12: WORK, ENERGY & POWER — KEY FORMULAS

```
WORK:
  W = F × d × cos θ
  Unit: Joule (J)
  
  Work done = 0 when:
  → Force perpendicular to displacement (θ = 90°)
  → No displacement (d = 0)
  → No force (F = 0)
  
  Example: Carrying a bag while walking horizontally = ZERO WORK
  (gravity and displacement are perpendicular!)

KINETIC ENERGY:
  KE = ½mv²
  If speed doubles → KE becomes 4 times (v²)
  If mass doubles → KE doubles

POTENTIAL ENERGY:
  PE = mgh
  
CONSERVATION OF ENERGY:
  Total energy (KE + PE) = constant (no friction)
  
POWER:
  P = W/t = Force × Velocity
  Unit: Watt (W)
  1 Horsepower (HP) = 746 Watts

ESCAPE VELOCITY (from Earth's surface):
  v_escape = √(2gR) ≈ 11.2 km/s
  (Speed needed to escape Earth's gravity)

ORBITAL VELOCITY (for satellite):
  v_orbital = √(gR) ≈ 7.9 km/s
  (Speed needed to maintain circular orbit)
```

---

## 📌 SECTION 13: BIHAR ELECTRICITY FACTS

```
BIHAR POWER SECTOR:
  Major Thermal Power Plants in Bihar:
  → Barauni Thermal Power Station (BTPS), Begusarai
    On the banks of Ganga
  → Muzaffarpur Thermal Power Station (MNTPS)
  → Kahalgaon Super Thermal Power Station (KSTPS), Bhagalpur
    Largest in Bihar! On Ganga bank
    Capacity: 2340 MW
  
  Hydro Power:
  → Koshi Project (on Nepal border)
  
  Nuclear:
  → No nuclear plant in Bihar itself
  
  BSES = Bihar State Electricity Supply
  Now: South Bihar Power Distribution Company (SBPDCL)
       North Bihar Power Distribution Company (NBPDCL)
       
  Electrification:
  → Saubhagya Scheme: 100% household electrification
  → Rajiv Gandhi Grameen Vidyutikaran Yojana (RGGVY)
```

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 1 (CS)
## 25 Questions on Binary Search Tree (BST)
### ⚠️ ATTEMPT ALL 25 FIRST — ANSWERS ONLY AT THE VERY END
# ═══════════════════════════════════════════════

---

**Q1.** The fundamental property of a Binary Search Tree states that for any node X:
- (A) Left child > X and Right child < X
- (B) Left subtree values < X and Right subtree values > X
- (C) All values are equal
- (D) More than one of the above
- (E) None of the above

---

**Q2.** What does inorder traversal of a valid BST always produce?
- (A) Values in reverse sorted (descending) order
- (B) Values in sorted (ascending) order
- (C) Values in random order
- (D) More than one of the above
- (E) None of the above

---

**Q3.** The AVERAGE case time complexity for SEARCHING in a balanced BST with n nodes is:
- (A) O(n)
- (B) O(n²)
- (C) O(log n)
- (D) More than one of the above
- (E) None of the above

---

**Q4.** The WORST case time complexity for searching in a BST occurs when:
- (A) The tree is perfectly balanced
- (B) The tree is completely skewed (degenerate)
- (C) The tree has only one node
- (D) More than one of the above
- (E) None of the above

---

**Q5.** How many distinct Binary Search Trees can be formed using 4 distinct keys?
- (A) 5
- (B) 12
- (C) 14
- (D) More than one of the above
- (E) None of the above

---

**Q6.** The MINIMUM element in a BST is found at:
- (A) The root node
- (B) The rightmost node
- (C) The leftmost node
- (D) More than one of the above
- (E) None of the above

---

**Q7.** Consider BST with values: 50, 30, 70, 20, 40, 60, 80
What is the INORDER traversal?
- (A) 50, 30, 70, 20, 40, 60, 80
- (B) 20, 30, 40, 50, 60, 70, 80
- (C) 80, 70, 60, 50, 40, 30, 20
- (D) More than one of the above
- (E) None of the above

---

**Q8.** When inserting into a BST, the new node is ALWAYS inserted as a:
- (A) Root node (replaces current root)
- (B) Internal node
- (C) Leaf node
- (D) More than one of the above
- (E) None of the above

---

**Q9.** The INORDER SUCCESSOR of a node X in BST is:
- (A) Parent of X
- (B) Largest element in X's left subtree
- (C) Smallest element in X's right subtree
- (D) More than one of the above
- (E) None of the above

---

**Q10.** If you insert the elements 1, 2, 3, 4, 5 into an empty BST (in this order), the resulting tree is:
- (A) A perfectly balanced BST
- (B) A right-skewed BST (degenerate)
- (C) A left-skewed BST
- (D) More than one of the above
- (E) None of the above

---

**Q11.** The number of distinct BSTs from 3 keys equals Catalan number C(3) =
- (A) 5
- (B) 14
- (C) 3
- (D) More than one of the above
- (E) None of the above

---

**Q12.** To DELETE a node with TWO children from a BST, one correct approach is to:
- (A) Remove the node and leave the subtrees disconnected
- (B) Replace the node with its inorder successor (or predecessor) and delete that
- (C) Delete the entire subtree
- (D) More than one of the above
- (E) None of the above

---

**Q13.** Given preorder traversal of a BST: [8, 3, 1, 6, 4, 7, 10, 14]
The INORDER traversal of the same BST is:
- (A) 8, 3, 1, 6, 4, 7, 10, 14 (same as preorder)
- (B) 1, 3, 4, 6, 7, 8, 10, 14
- (C) 14, 10, 7, 6, 4, 3, 1, 8
- (D) More than one of the above
- (E) None of the above

---

**Q14.** Which of the following correctly states the BST property for the node with value 15?
```
      15
     /  \
    9    20
   / \
  5   12
```
- (A) Left subtree {9,5,12} all < 15 AND right subtree {20} > 15 → VALID BST
- (B) This cannot be a BST because 12 < 15
- (C) 5 < 9 < 12 so it's valid
- (D) More than one of the above
- (E) None of the above

---

**Q15.** The height of a BST with n nodes in the WORST CASE (completely skewed) is:
- (A) O(log n)
- (B) O(n)
- (C) O(n log n)
- (D) More than one of the above
- (E) None of the above

---

**Q16.** Which self-balancing BST maintains the property that the height difference between left and right subtrees of ANY node is at most 1?
- (A) Red-Black Tree
- (B) AVL Tree
- (C) Splay Tree
- (D) More than one of the above
- (E) None of the above

---

**Q17.** In a BST, which operation is most COMPLEX to implement?
- (A) Search
- (B) Insert
- (C) Delete
- (D) More than one of the above
- (E) None of the above

---

**Q18.** Is the following tree a valid BST?
```
      10
     /  \
    5    20
   / \
  3   15
```
- (A) Yes — it is a valid BST
- (B) No — because 15 is in the left subtree of 10, but 15 > 10 (violation!)
- (C) Yes — because 15 > 5 (its immediate parent)
- (D) More than one of the above
- (E) None of the above

---

**Q19.** The MAXIMUM element in a BST is located at:
- (A) Root node
- (B) Leftmost leaf node
- (C) Rightmost leaf node
- (D) More than one of the above
- (E) None of the above

---

**Q20.** If Preorder traversal of a BST is: 5, 3, 1, 4, 7, 6
Then Postorder traversal is:
- (A) 1, 4, 3, 6, 7, 5
- (B) 1, 3, 4, 5, 6, 7
- (C) 5, 7, 6, 3, 4, 1
- (D) More than one of the above
- (E) None of the above

---

**Q21.** Catalan number C(n) gives the count of:
- (A) Minimum number of nodes in a BST of height n
- (B) Maximum number of nodes in a BST of height n
- (C) Number of distinct BSTs that can be formed with n distinct keys
- (D) More than one of the above
- (E) None of the above

---

**Q22.** In a BST, the INORDER PREDECESSOR of a node X with a LEFT subtree is:
- (A) Parent of X
- (B) Leftmost node in X's left subtree
- (C) Rightmost (largest) node in X's left subtree
- (D) More than one of the above
- (E) None of the above

---

**Q23.** A BST is given: root = 50, left subtree has elements {30, 20, 40}, right subtree has {70, 60, 80}.
Which of the following is CORRECT?
- (A) Min = 20 (leftmost), Max = 80 (rightmost)
- (B) Inorder: 20, 30, 40, 50, 60, 70, 80
- (C) Root is always visited second in inorder traversal
- (D) More than one of the above
- (E) None of the above

---

**Q24.** Why is a balanced BST (like AVL) preferred over a regular BST in practice?
- (A) AVL uses less memory than regular BST
- (B) AVL guarantees O(log n) operations even in worst case by maintaining balance
- (C) AVL trees do not support deletion
- (D) More than one of the above
- (E) None of the above

---

**Q25.** Given inorder: [1, 2, 3, 4, 5] and preorder: [3, 1, 2, 4, 5], what is the root of the BST?
- (A) 1
- (B) 5
- (C) 3 (first element of preorder is always root)
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS — PART 2 (GS)
## 25 Questions on Physics — Electricity, Magnetism & Nuclear
### ⚠️ ATTEMPT ALL 25 FIRST — ANSWERS ONLY AT THE VERY END
# ═══════════════════════════════════════════════

---

**Q26.** According to Ohm's Law, if voltage across a resistor is doubled (current remaining same), then resistance:
- (A) Doubles
- (B) Halves
- (C) Stays the same
- (D) More than one of the above
- (E) None of the above

---

**Q27.** A resistor carries current I and has resistance R. If the current is TRIPLED (3I), the power dissipated becomes:
- (A) 3 times the original
- (B) 6 times the original
- (C) 9 times the original
- (D) More than one of the above
- (E) None of the above

---

**Q28.** Which of the following is the CORRECT formula for electrical power?
- (A) P = VI
- (B) P = I²R
- (C) P = V²/R
- (D) More than one of the above
- (E) None of the above

---

**Q29.** In a PARALLEL circuit with resistors R₁, R₂, R₃, the total resistance is:
- (A) R₁ + R₂ + R₃
- (B) Less than the smallest of R₁, R₂, R₃
- (C) Greater than the largest of R₁, R₂, R₃
- (D) More than one of the above
- (E) None of the above

---

**Q30.** In a SERIES circuit with resistors R₁ = 4Ω, R₂ = 6Ω, total resistance is:
- (A) 2.4Ω
- (B) 10Ω
- (C) 5Ω
- (D) More than one of the above
- (E) None of the above

---

**Q31.** The HEATING EFFECT of electric current is the principle behind which devices?
- (A) Electric iron
- (B) Electric bulb (incandescent)
- (C) Electric fuse
- (D) More than one of the above
- (E) None of the above

---

**Q32.** Oersted's experiment (1820) showed that:
- (A) A changing magnetic field induces an electric current
- (B) A current-carrying conductor produces a magnetic field around it
- (C) Moving charges experience force in magnetic field
- (D) More than one of the above
- (E) None of the above

---

**Q33.** Nuclear FISSION is the process used in:
- (A) Hydrogen bomb and Sun's energy
- (B) Atom bomb and nuclear power plants
- (C) Solar cells and batteries
- (D) More than one of the above
- (E) None of the above

---

**Q34.** The energy released by the SUN comes from:
- (A) Nuclear Fission
- (B) Nuclear Fusion
- (C) Chemical combustion
- (D) More than one of the above
- (E) None of the above

---

**Q35.** Among alpha, beta, and gamma radiations, which has the HIGHEST penetrating power?
- (A) Alpha (α)
- (B) Beta (β)
- (C) Gamma (γ)
- (D) More than one of the above
- (E) None of the above

---

**Q36.** Which radiation has the HIGHEST ionizing power?
- (A) Gamma (γ)
- (B) Beta (β)
- (C) Alpha (α)
- (D) More than one of the above
- (E) None of the above

---

**Q37.** 1 kWh (one unit of electricity) equals how many Joules?
- (A) 1000 J
- (B) 3.6 × 10⁶ J
- (C) 4.2 × 10³ J
- (D) More than one of the above
- (E) None of the above

---

**Q38.** A STEP-UP transformer:
- (A) Increases voltage and decreases current
- (B) Decreases voltage and increases current
- (C) Increases both voltage and current
- (D) More than one of the above
- (E) None of the above

---

**Q39.** If the kinetic energy of a moving object is doubled (mass remains same), its speed becomes:
- (A) √2 times original
- (B) 2 times original
- (C) 4 times original
- (D) More than one of the above
- (E) None of the above

---

**Q40.** The ESCAPE VELOCITY from Earth's surface is approximately:
- (A) 7.9 km/s
- (B) 11.2 km/s
- (C) 3 × 10⁸ km/s
- (D) More than one of the above
- (E) None of the above

---

**Q41.** Radioactivity was discovered by:
- (A) Marie Curie
- (B) Ernest Rutherford
- (C) Henri Becquerel
- (D) More than one of the above
- (E) None of the above

---

**Q42.** Alpha particles are identical to the nucleus of which element?
- (A) Hydrogen
- (B) Helium
- (C) Lithium
- (D) More than one of the above
- (E) None of the above

---

**Q43.** Which of the following correctly describes Faraday's Law of Electromagnetic Induction?
- (A) A current-carrying conductor experiences force in magnetic field
- (B) A changing magnetic field induces an EMF in a conductor
- (C) Electric charge creates magnetic field
- (D) More than one of the above
- (E) None of the above

---

**Q44.** The Kahalgaon Super Thermal Power Station (largest in Bihar) is located in which district?
- (A) Patna
- (B) Bhagalpur
- (C) Begusarai
- (D) More than one of the above
- (E) None of the above

---

**Q45.** In an electric circuit, a FUSE is always connected:
- (A) In parallel with the device it protects
- (B) In series with the circuit
- (C) Either series or parallel — doesn't matter
- (D) More than one of the above
- (E) None of the above

---

**Q46.** The resistance of a conductor is DIRECTLY proportional to its:
- (A) Cross-sectional area
- (B) Length
- (C) Temperature (for metals)
- (D) More than one of the above
- (E) None of the above

---

**Q47.** Work done is ZERO when:
- (A) A force is applied but object doesn't move
- (B) Force is perpendicular to displacement (like gravity on horizontal motion)
- (C) No force is applied
- (D) More than one of the above
- (E) None of the above

---

**Q48.** Which of the following is used in MRI (Magnetic Resonance Imaging) machines in hospitals?
- (A) Natural magnets (lodestones)
- (B) Powerful electromagnets
- (C) Permanent bar magnets
- (D) More than one of the above
- (E) None of the above

---

**Q49.** A 60W bulb and a 100W bulb are connected in PARALLEL to the same 220V supply. Which bulb is brighter?
- (A) 60W bulb (less resistance, more current)
- (B) 100W bulb (glows at its rated power)
- (C) Both glow equally bright
- (D) More than one of the above
- (E) None of the above

---

**Q50.** Conventional direction of electric current is:
- (A) From negative to positive terminal (inside battery)
- (B) From positive to negative terminal (outside battery)
- (C) In the direction of electron flow
- (D) More than one of the above
- (E) None of the above

---

# ═══════════════════════════════════════════════
# ✅ ANSWER KEY WITH DETAILED EXPLANATIONS
## CS Answers (Q1–Q25) | GS Answers (Q26–Q50)
# ═══════════════════════════════════════════════

---

## 🖥️ CS ANSWERS — BINARY SEARCH TREE

---

**A1. → (B) Left subtree values < X and Right subtree values > X**
This is the BST property. Critically, it applies to ALL values in the subtree, NOT just the immediate child. This is the #1 trap — check ALL nodes in subtrees, not just direct children.

---

**A2. → (B) Values in sorted (ascending) order**
Inorder traversal (Left → Root → Right) of any valid BST always gives keys in sorted ascending order. This is because: left subtree has smaller values, then root, then right subtree has larger values — exactly the inorder order.

---

**A3. → (C) O(log n)**
In a balanced BST, each comparison halves the search space (like binary search). Height ≈ log n → O(log n) comparisons. This is the average case; worst case (skewed) is O(n).

---

**A4. → (B) The tree is completely skewed (degenerate)**
A skewed BST has height n-1 (like a linked list). Searching the last element requires visiting all n nodes → O(n). This happens when elements are inserted in sorted order.

---

**A5. → (C) 14**
C(4) = 14. This is the 4th Catalan number. Formula: C(n) = (2n)! / [(n+1)! × n!].
C(4) = 8! / (5! × 4!) = 40320 / (120 × 24) = 40320/2880 = 14. This is a guaranteed PYQ fact.

---

**A6. → (C) The leftmost node**
BST property: all smaller values go left. The minimum is reached by going left repeatedly until you can't go further. The leftmost leaf = minimum element.

---

**A7. → (B) 20, 30, 40, 50, 60, 70, 80**
Inorder of BST = sorted order. The values {50,30,70,20,40,60,80} sorted = 20,30,40,50,60,70,80.
Tree structure: 50 is root, 30 left, 70 right; 20 and 40 are children of 30; 60 and 80 are children of 70.

---

**A8. → (C) Leaf node**
BST insertion: compare with root → go left or right → repeat until NULL is found → insert there as a leaf. New nodes are ALWAYS inserted at leaf positions.

---

**A9. → (C) Smallest element in X's right subtree**
Inorder successor = next element in sorted order after X = the smallest value greater than X = the leftmost node in X's right subtree (keep going left in right subtree).

---

**A10. → (B) A right-skewed BST (degenerate)**
Inserting 1: root. Insert 2: 2>1 → goes right. Insert 3: 3>1 →right, 3>2 →right again. Insert 4: same... All go to the right → completely right-skewed. This is the worst case for BST!

---

**A11. → (A) 5**
C(3) = 5. Catalan numbers: C(0)=1, C(1)=1, C(2)=2, C(3)=5, C(4)=14.
For 3 keys, there are 5 distinct BST shapes.

---

**A12. → (B) Replace the node with its inorder successor (or predecessor) and delete that**
The standard algorithm for deleting a node with two children: find its inorder successor (smallest in right subtree), copy its value to the deleted node's position, then delete the successor (which has at most one child, making it easier). 

---

**A13. → (B) 1, 3, 4, 6, 7, 8, 10, 14**
Preorder [8,3,1,6,4,7,10,14] constructs the BST. Inorder of that BST = sorted order = 1,3,4,6,7,8,10,14.
(The values sorted: 1<3<4<6<7<8<10<14)

---

**A14. → (A) Left subtree {9,5,12} all < 15 AND right subtree {20} > 15 → VALID BST**
All values in left subtree: 9,5,12 — all less than 15 ✓. Right subtree: 20 > 15 ✓.
Within the subtree rooted at 9: 5 < 9 ✓, 12 > 9 ✓. This IS a valid BST.

---

**A15. → (B) O(n)**
Worst case BST height = completely skewed tree = n-1 ≈ O(n).
This occurs with sorted input insertion. Hence search/insert/delete all become O(n) worst case.

---

**A16. → (B) AVL Tree**
AVL Tree (Adelson-Velsky and Landis, 1962): strictly balanced BST where for EVERY node, |height(left) - height(right)| ≤ 1. Uses rotations to maintain balance after each insert/delete.

---

**A17. → (C) Delete**
Search = simple comparison and move. Insert = search + add leaf. Delete = 3 cases (leaf, 1 child, 2 children). The 2-children case requires finding inorder successor and careful pointer updates — most complex.

---

**A18. → (B) No — because 15 is in the left subtree of 10, but 15 > 10 (violation!)**
The BST property requires ALL values in the left subtree to be LESS than the root. Node 15 is in the left subtree of 10 (via 5's right child), but 15 > 10. This violates BST property!
This is the classic "check immediate parent only" trap.

---

**A19. → (C) Rightmost leaf node**
Maximum in BST: go right from root repeatedly until NULL. The rightmost node has no larger element in its right subtree → it's the maximum.

---

**A20. → (A) 1, 4, 3, 6, 7, 5**
Build BST from Preorder [5,3,1,4,7,6]:
```
      5
     / \
    3   7
   / \ /
  1  4 6
```
Postorder (Left → Right → Root): 1, 4, 3, 6, 7, 5 ✓

---

**A21. → (C) Number of distinct BSTs that can be formed with n distinct keys**
Catalan number C(n) counts the number of structurally distinct BSTs (and also binary trees) that can be built using n distinct keys. C(4)=14 is the most tested value.

---

**A22. → (C) Rightmost (largest) node in X's left subtree**
Inorder Predecessor = largest element smaller than X = the rightmost node in X's left subtree (keep going right in left subtree until NULL).

---

**A23. → (D) More than one of the above**
Both (A) and (B) are correct:
(A) Min=20 (leftmost in left subtree) ✓, Max=80 (rightmost in right subtree) ✓
(B) Inorder = sorted = 20,30,40,50,60,70,80 ✓
(C) is wrong — root (50) is visited as the 4th element in inorder, not second.
→ Answer = (D)

---

**A24. → (B) AVL guarantees O(log n) operations even in worst case by maintaining balance**
Regular BST degrades to O(n) with sorted insertions. AVL tree uses rotations to always keep balanced → height always O(log n) → all operations O(log n) guaranteed.
Option A is wrong (AVL uses same memory). Option C is wrong (AVL supports all operations).

---

**A25. → (C) 3 (first element of preorder is always root)**
In Preorder (Root→Left→Right), the FIRST element is always the ROOT. So root = 3.
This can be verified: 3 is in the middle of inorder [1,2,3,4,5] → everything before 3 is left subtree {1,2}, everything after is right subtree {4,5}.

---

## 📚 GS ANSWERS — ELECTRICITY, MAGNETISM & NUCLEAR PHYSICS

---

**A26. → (A) Doubles**
Ohm's Law: V = IR → R = V/I.
If voltage doubles (2V) and current stays same (I): R = 2V/I = 2(V/I) = 2R → Doubles.
But wait — Ohm's Law says resistance is a property of the conductor (temperature dependent), not the voltage! If V doubles and R is constant, then I doubles.
The question says current remains same → R = V/I. If V doubles and I same → R = 2V/I = 2× original R. So answer is (A) Doubles.

---

**A27. → (C) 9 times the original**
P = I²R. If current becomes 3I: P_new = (3I)²R = 9I²R = 9P.
Power is proportional to I² → tripling current makes power 9 times (3² = 9).

---

**A28. → (D) More than one of the above**
All three formulas are correct for electrical power:
P = VI ✓ (from definition)
P = I²R ✓ (substitute V=IR)
P = V²/R ✓ (substitute I=V/R)
→ Answer = (D)

---

**A29. → (B) Less than the smallest of R₁, R₂, R₃**
Parallel: 1/R_total = 1/R₁ + 1/R₂ + 1/R₃. Adding more terms to the sum makes 1/R_total larger → R_total smaller. R_total is always less than the smallest individual resistance.

---

**A30. → (B) 10Ω**
Series: R_total = R₁ + R₂ = 4 + 6 = 10Ω.
Option A (2.4Ω) would be the parallel combination: 1/R = 1/4 + 1/6 = 5/12 → R = 2.4Ω.

---

**A31. → (D) More than one of the above**
ALL three devices use the heating effect of current:
- Electric iron: Nichrome wire heats up ✓
- Incandescent bulb: Tungsten filament glows due to heat ✓
- Fuse: Melts when excess current generates too much heat ✓
→ Answer = (D)

---

**A32. → (B) A current-carrying conductor produces a magnetic field around it**
Oersted (1820): Placed compass near current-carrying wire → needle deflected → proved current creates magnetic field. This was the first experimental link between electricity and magnetism.

---

**A33. → (B) Atom bomb and nuclear power plants**
Nuclear FISSION = splitting heavy nucleus. Used in atom bomb AND nuclear reactors.
Hydrogen bomb and sun use FUSION (not fission).
Solar cells use photovoltaic effect (not nuclear).

---

**A34. → (B) Nuclear Fusion**
Sun fuses hydrogen nuclei into helium, releasing enormous energy. This is nuclear FUSION. The sun is essentially a giant continuous hydrogen bomb. Fusion produces more energy per kg than fission and is what powers stars.

---

**A35. → (C) Gamma (γ)**
Penetrating power: γ > β > α.
Gamma rays can penetrate thick lead/concrete. Beta passes through aluminum. Alpha is stopped by paper or skin.
MNEMONIC: Gamma = Greatest penetration.

---

**A36. → (C) Alpha (α)**
Ionizing power: α > β > γ (opposite of penetrating power!).
Alpha particles are heavy, slow, doubly charged → interact strongly with matter → HIGH ionization.
Gamma rays pass through quickly → LOW ionization.

---

**A37. → (B) 3.6 × 10⁶ J**
1 kWh = 1000 W × 3600 s = 3,600,000 J = 3.6 × 10⁶ J.
This is the commercial unit of electrical energy (one "unit" you pay for on your electricity bill).

---

**A38. → (A) Increases voltage and decreases current**
Step-up transformer: more turns on secondary coil → higher voltage output.
Power conservation: P = VI = constant. Higher V → lower I.
Used in power transmission (high voltage, low current = less energy loss in wires).

---

**A39. → (A) √2 times original**
KE = ½mv². If KE doubles (2 × KE) and mass stays same:
2 × ½mv² = ½m(v_new)² → v_new² = 2v² → v_new = v√2.
Speed becomes √2 ≈ 1.414 times original.

---

**A40. → (B) 11.2 km/s**
Escape velocity from Earth's surface = √(2gR) ≈ 11.2 km/s.
Orbital velocity (to maintain circular orbit) = √(gR) ≈ 7.9 km/s.
These are two different values — don't confuse them!

---

**A41. → (C) Henri Becquerel**
Radioactivity was DISCOVERED by Henri Becquerel in 1896 (accidentally — he left uranium on photographic plates). Marie Curie and Pierre Curie studied it extensively and named the phenomenon "radioactivity." Rutherford identified the types of radiation.

---

**A42. → (B) Helium**
Alpha particle = helium-4 nucleus = 2 protons + 2 neutrons = ₂He⁴.
When a nucleus emits an alpha particle, its atomic number decreases by 2 and mass number by 4.

---

**A43. → (B) A changing magnetic field induces an EMF in a conductor**
Faraday's Law (1831): EMF is induced when magnetic flux through a conductor changes. This is the basis of generators, transformers, and induction coils.
Option A = Lorentz force law. Option C = Oersted's discovery.

---

**A44. → (B) Bhagalpur**
Kahalgaon Super Thermal Power Station (KSTPS) is located in Bhagalpur district, Bihar, on the banks of the Ganga. It is the largest thermal power plant in Bihar with capacity ~2340 MW. This is a high-frequency BPSC Bihar GK fact.

---

**A45. → (B) In series with the circuit**
A fuse must be in SERIES because the full current of the circuit passes through it. If excess current flows → fuse wire melts → circuit breaks. If in parallel, current would bypass the fuse → fuse would be useless!

---

**A46. → (D) More than one of the above**
Resistance R = ρL/A:
- R ∝ L (directly proportional to length) ✓ Option B
- R ∝ 1/A (inversely proportional to area — not directly)
For metals, resistance also increases with temperature ✓ Option C
Options B and C are both correct → Answer = (D)
Note: Option A (area) is inverse relationship, not direct.

---

**A47. → (D) More than one of the above**
Work = F × d × cos θ. Work = 0 when:
(A) F ≠ 0 but d = 0 (no displacement) ✓ — e.g., pushing wall
(B) θ = 90° (force perpendicular to displacement, cos 90° = 0) ✓
(C) F = 0 (no force applied) ✓
All three give zero work → Answer = (D)

---

**A48. → (B) Powerful electromagnets**
MRI machines use extremely powerful superconducting electromagnets (not permanent magnets or natural magnets). These create strong magnetic fields (1.5T to 3T) to align hydrogen atoms in the body for imaging.

---

**A49. → (B) 100W bulb (glows at its rated power)**
In PARALLEL, both bulbs receive the SAME voltage (220V) — their rated voltage. Each operates at its rated power. 100W bulb gets 100W, 60W bulb gets 60W. So 100W is brighter.
Note: If connected in series, the 60W bulb (higher resistance) would be brighter — common trap!

---

**A50. → (B) From positive to negative terminal (outside battery)**
CONVENTIONAL current flows from positive (+) terminal through external circuit to negative (-) terminal. This is opposite to actual electron flow (electrons go from - to +). Conventional direction is used in circuit analysis (historical — before electrons were discovered).

---

# ═══════════════════════════════════════════════
# 📊 DAY 25 REVISION SUMMARY
## Quick-Recall Flash Points
# ═══════════════════════════════════════════════

---

## 🖥️ CS FLASH CARDS — 12 MUST-REMEMBER FACTS

```
1.  BST property: Left subtree < Root < Right subtree (ALL nodes!)
2.  Inorder of BST = SORTED ASCENDING always
3.  BST search: O(log n) average | O(n) worst case (skewed)
4.  C(4) = 14 distinct BSTs with 4 keys ← BPSC #1 PYQ
5.  C(3) = 5 | C(2) = 2 | C(1) = 1
6.  Sorted insertion → SKEWED BST (worst case!)
7.  Min in BST = LEFTMOST node
8.  Max in BST = RIGHTMOST node
9.  Inorder Successor = smallest in RIGHT subtree
10. Delete node with 2 children → replace with inorder successor
11. New BST node always inserted as LEAF
12. AVL tree: |height(L)-height(R)| ≤ 1 at every node
```

## 📚 GS FLASH CARDS — 12 MUST-REMEMBER FACTS

```
1.  P = I²R → if current doubles, power becomes 4 TIMES
2.  P = VI = I²R = V²/R (all three are correct!)
3.  Parallel circuit: R_total < smallest resistance
4.  Series circuit: R_total = R₁ + R₂ + ... (add up)
5.  Gamma rays: MOST penetrating | Alpha: LEAST penetrating
6.  Alpha: MOST ionizing | Gamma: LEAST ionizing
7.  Sun's energy = Nuclear FUSION | Atom bomb = Nuclear FISSION
8.  Radioactivity discovered by: Henri Becquerel (1896)
9.  Fuse = always in SERIES | protects by melting
10. 1 kWh = 3.6 × 10⁶ J = 1 unit of electricity
11. Escape velocity = 11.2 km/s | Orbital velocity = 7.9 km/s
12. Kahalgaon STPS = largest power plant in Bihar (Bhagalpur dist.)
```

---

## ⚡ KEY OPTION D TRAPS — DAY 25

```
TOPIC                               │ Why D applies
────────────────────────────────────┼────────────────────────────────
Power formulas                      │ All 3 correct (P=VI, P=I²R, P=V²/R)
Heating effect devices              │ Iron + Bulb + Fuse all use it
Work done = 0 cases                 │ Multiple scenarios (no force, no displacement, perpendicular)
BST: Min=leftmost, sorted inorder   │ Sometimes both A and B are right
Radiation: penetrating vs ionizing  │ These are OPPOSITE orders — read carefully
```

---

## 🎯 TONIGHT'S 30-MINUTE REVISION TASK

Write from memory (close the file):
1. Build a BST by inserting: 10, 5, 15, 3, 7, 12, 20
2. Write its Inorder traversal (should be sorted)
3. State: what is C(4)? What is C(3)?
4. State Ohm's Law and all 3 forms of Power formula
5. Penetrating power order of α, β, γ
6. Name 3 applications of Joule's heating effect

---

*Day 25 Complete | Next: Day 26 — Red-Black Trees + Biology (Reproduction)*
*Score Target Today: 22/25 CS + 22/25 GS = 44/50*
*Running Total Target: Days 22–25 combined = 176/200*
