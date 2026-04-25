# 📅 BPSC TRE 4.0 — DAY 63 COMPLETE STUDY MODULE
### Digital Electronics: Boolean Algebra, Laws, De Morgan's Theorem, SOP & POS + Indian Economy — Banking & Monetary Policy
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Digital Electronics — Boolean Algebra Laws, De Morgan's Theorem (both forms), Truth Table Verification, SOP & POS, Canonical Forms (SOM & POM)
> - Afternoon (1 hr): Economics — Banking Basics, Types of Banks, RBI Functions, Monetary Policy Tools (Repo, Reverse Repo, CRR, SLR)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Digital Electronics — Boolean Algebra & De Morgan's Theorem

---

## 🔷 SECTION 1: What is Boolean Algebra?

### Real-Life Analogy — A Two-Switch World:

In regular algebra, numbers can take any value: 1, 2, 3.14, -7... But imagine a world where ONLY two values exist: a light switch is either ON or OFF. No in-between. Every calculation, every decision, every circuit in a computer lives in THIS world — the world of 0 and 1.

Boolean Algebra is the mathematics of this two-switch world.

> **Boolean Algebra is a branch of algebra that operates on variables that can take only two values: TRUE (1) and FALSE (0). It provides the mathematical foundation for digital circuits, logic gates, and computer processors.**

### Who Invented It?
```
GEORGE BOOLE (1815–1864) — English mathematician
→ Published "The Laws of Thought" (1854)
→ Created this algebra to express LOGICAL REASONING mathematically
→ Never imagined computers — but his algebra became the backbone of all digital computing!

CLAUDE SHANNON (1937) — Applied Boolean algebra to electronic circuits
→ Showed that Boolean algebra maps perfectly to electronic switches
→ This is why Boolean algebra is the foundation of digital electronics.

🎯 PYQ FACT: Boolean algebra was developed by George Boole.
🎯 PYQ FACT: Boolean variables take only two values: 0 or 1.
```

### Why Boolean Algebra is Critical:
```
WITHOUT BOOLEAN ALGEBRA:
  Engineers would have to manually trace every wire and circuit
  to understand what a chip does.

WITH BOOLEAN ALGEBRA:
  → Complex circuits can be written as equations: Y = AB + A'C + BC
  → Equations can be simplified to use FEWER gates (saves cost, power, space!)
  → Circuits can be verified mathematically without building them
  → The same expression can be implemented in multiple ways

FLOW:
  Problem/Logic → Boolean Expression → Simplify using Laws → Build minimal circuit
```

---

## 🔷 SECTION 2: Basic Boolean Operations (Quick Recap)

```
THREE BASIC OPERATIONS:

1. AND  (·)   →  Y = A · B   →  Multiplication in logic
   Output 1 ONLY when ALL inputs = 1

2. OR   (+)   →  Y = A + B   →  Addition in logic
   Output 0 ONLY when ALL inputs = 0

3. NOT  (')   →  Y = A'      →  Complement/inversion
   Output = OPPOSITE of input

BASIC EXAMPLES:
  1 · 1 = 1        1 + 1 = 1        (1)' = 0
  1 · 0 = 0        1 + 0 = 1        (0)' = 1
  0 · 0 = 0        0 + 0 = 0
  0 · 1 = 0        0 + 1 = 1

🚨 KEY DIFFERENCE FROM REGULAR ALGEBRA:
  In regular math:  1 + 1 = 2
  In Boolean:       1 + 1 = 1  (because OR of two TRUEs is still TRUE!)

  In regular math:  1 · 1 = 1
  In Boolean:       1 · 1 = 1  (same — AND of two TRUEs is TRUE)
```

---

## 🔷 SECTION 3: Laws of Boolean Algebra — Complete Mastery

### Understanding the Layout:
```
Each law comes in TWO FORMS:
  → AND form  (using · multiplication)
  → OR  form  (using + addition)

These two forms are called DUALS of each other.
To get the DUAL of any Boolean expression:
  Swap AND (·) ↔ OR (+)  AND  Swap 0 ↔ 1
```

---

### LAW 1: IDENTITY LAW

```
DEFINITION:
  Any variable operated with the IDENTITY ELEMENT returns the variable unchanged.
  Identity for AND = 1  (multiplying by 1 doesn't change anything)
  Identity for OR  = 0  (adding 0 doesn't change anything)

STATEMENTS:
  AND form:  A · 1 = A     ← "A AND 1 = A" (1 doesn't change A)
  OR  form:  A + 0 = A     ← "A OR 0 = A"  (0 doesn't change A)

INTUITION (Real Life):
  If you multiply any score by 1 → same score. (identity for multiplication)
  If you add 0 to any score → same score. (identity for addition)
  Boolean Identity works exactly the same way!

EXAMPLES:
  1 · 1 = 1 ✅    0 · 1 = 0 ✅   (A=1: 1·1=1; A=0: 0·1=0 → returns A)
  1 + 0 = 1 ✅    0 + 0 = 0 ✅   (A=1: 1+0=1; A=0: 0+0=0 → returns A)

🎯 PYQ FACT: A·1 = A and A+0 = A → Identity Law
```

---

### LAW 2: NULL LAW (Dominance Law)

```
DEFINITION:
  When a variable is operated with the DOMINANT ELEMENT, the result is
  always the dominant element regardless of the variable's value.
  Null/dominant for AND = 0
  Null/dominant for OR  = 1

STATEMENTS:
  AND form:  A · 0 = 0     ← "A AND 0 = ALWAYS 0" (0 dominates AND)
  OR  form:  A + 1 = 1     ← "A OR 1 = ALWAYS 1"  (1 dominates OR)

INTUITION (Real Life):
  Multiply ANY number by 0 → always get 0. Zero "dominates" multiplication.
  OR with 1: "true OR anything = true" — 1 is always true, so result is always 1.

EXAMPLES:
  5 · 0 = 0 (regular math)     →   A · 0 = 0 (Boolean — same!)
  True OR True = True           →   A + 1 = 1 (always TRUE regardless of A)
  True OR False = True          →   A + 1 = 1 (still TRUE)

🎯 PYQ FACT: A·0 = 0 and A+1 = 1 → Null Law
🚨 TRAP: Students confuse Identity and Null laws.
   Identity: · with 1, + with 0  → NO change (identity element)
   Null:     · with 0, + with 1  → FORCED result (dominant element)
```

---

### LAW 3: IDEMPOTENT LAW

```
DEFINITION:
  When a variable is operated with ITSELF, the result is the variable itself.
  "Idempotent" = "same power" (idem = same, potent = power)

STATEMENTS:
  AND form:  A · A = A     ← "A AND A = A"
  OR  form:  A + A = A     ← "A OR A = A"

INTUITION (Real Life):
  "Is it raining AND is it raining?" = "Is it raining?" (redundant!)
  "Is it raining OR is it raining?" = "Is it raining?" (still redundant!)
  Repeating the same condition doesn't change the answer.

EXAMPLES:
  0 · 0 = 0 ✅   (0 AND 0 = 0)
  1 · 1 = 1 ✅   (1 AND 1 = 1)
  0 + 0 = 0 ✅   (0 OR 0 = 0)
  1 + 1 = 1 ✅   (1 OR 1 = 1 — NOTE: NOT 2! Boolean OR, not arithmetic!)

🎯 PYQ FACT: A·A = A and A+A = A → Idempotent Law
🚨 TRAP: In Boolean algebra, 1+1 = 1 (NOT 2!). This is Idempotent Law in action.
```

---

### LAW 4: COMPLEMENT LAW

```
DEFINITION:
  When a variable is operated with its COMPLEMENT (opposite), the result is
  determined by which operation:
  AND with complement → ALWAYS 0
  OR  with complement → ALWAYS 1

STATEMENTS:
  AND form:  A · A' = 0    ← "A AND NOT-A = always 0" (contradiction!)
  OR  form:  A + A' = 1    ← "A OR NOT-A = always 1"  (tautology!)

INTUITION (Real Life):
  "Is it raining AND NOT raining?" → IMPOSSIBLE → always FALSE (0)
  "Is it raining OR NOT raining?"  → ALWAYS TRUE (one must be true) → always TRUE (1)

EXAMPLES:
  If A=0: A·A' = 0·1 = 0 ✅    If A=1: A·A' = 1·0 = 0 ✅  (always 0!)
  If A=0: A+A' = 0+1 = 1 ✅    If A=1: A+A' = 1+0 = 1 ✅  (always 1!)

DOUBLE COMPLEMENT (Also part of Complement Law):
  (A')' = A     ← Double negation = original value
  "NOT(NOT A) = A" — two inversions cancel out!

  Example: (1')' = (0)' = 1 = A ✅

🎯 PYQ FACT: A·A' = 0 and A+A' = 1 → Complement Law
🎯 PYQ FACT: (A')' = A → Double Complement
```

---

### LAW 5: COMMUTATIVE LAW

```
DEFINITION:
  The ORDER of operands does NOT affect the result.
  Same as regular arithmetic commutativity (2+3 = 3+2).

STATEMENTS:
  AND form:  A · B = B · A    ← order of AND doesn't matter
  OR  form:  A + B = B + A    ← order of OR doesn't matter

INTUITION:
  "A is true AND B is true" = "B is true AND A is true" — same thing!
  
EXAMPLES:
  1 · 0 = 0 · 1 = 0 ✅
  1 + 0 = 0 + 1 = 1 ✅

🎯 PYQ FACT: Boolean algebra is commutative for both AND and OR.
```

---

### LAW 6: ASSOCIATIVE LAW

```
DEFINITION:
  The GROUPING of operands does NOT affect the result.
  Same as regular arithmetic associativity: (2+3)+4 = 2+(3+4)

STATEMENTS:
  AND form:  (A · B) · C = A · (B · C)    ← grouping doesn't matter for AND
  OR  form:  (A + B) + C = A + (B + C)    ← grouping doesn't matter for OR

EXAMPLES:
  (1·0)·1 = 0·1 = 0 = 1·(0·1) = 1·0 = 0 ✅
  (1+0)+1 = 1+1 = 1 = 1+(0+1) = 1+1 = 1 ✅

🎯 PYQ FACT: Boolean algebra is associative for both AND and OR.
```

---

### LAW 7: DISTRIBUTIVE LAW ⭐ VERY IMPORTANT

```
DEFINITION:
  One operation can be DISTRIBUTED over another — exactly like regular algebra
  distributes multiplication over addition: a(b+c) = ab + ac

  BUT Boolean algebra has TWO distributive laws (regular math has only one!):

STATEMENTS:
  FORM 1 (AND over OR):
    A · (B + C) = (A · B) + (A · C)
    ← Distribute AND over OR — same as regular algebra!

  FORM 2 (OR over AND) — UNIQUE TO BOOLEAN:
    A + (B · C) = (A + B) · (A + C)
    ← Distribute OR over AND — NO equivalent in regular arithmetic!

VERIFICATION — FORM 1:  A(B+C) = AB + AC
  Let A=1, B=0, C=1:
  Left side:  1·(0+1) = 1·1 = 1
  Right side: (1·0) + (1·1) = 0+1 = 1 ✅

VERIFICATION — FORM 2:  A+(B·C) = (A+B)·(A+C)
  Let A=0, B=1, C=1:
  Left side:  0+(1·1) = 0+1 = 1
  Right side: (0+1)·(0+1) = 1·1 = 1 ✅

🎯 PYQ FACT: Boolean has TWO distributive laws (regular algebra has only one).
🎯 PYQ FACT: A+(B·C) = (A+B)·(A+C) — the second form has NO regular-algebra equivalent.
```

---

### LAW 8: ABSORPTION LAW ⭐ VERY IMPORTANT FOR SIMPLIFICATION

```
DEFINITION:
  A variable "absorbs" a more complex expression that contains it.
  These laws are VERY useful in simplifying Boolean expressions!

STATEMENTS:
  FORM 1:  A + A·B = A         ← "A absorbs A·B"
  FORM 2:  A · (A + B) = A     ← "A absorbs (A+B)"

PROOF of FORM 1 — A + AB = A:
  A + AB
  = A·1 + A·B        (Identity Law: A = A·1)
  = A·(1 + B)        (Distributive Law: factor out A)
  = A·1              (Null Law: 1+B = 1)
  = A                (Identity Law: A·1 = A)
  ✅ Proved!

PROOF of FORM 2 — A·(A+B) = A:
  A·(A+B)
  = A·A + A·B        (Distributive Law)
  = A + A·B          (Idempotent: A·A = A)
  = A                (Absorption Form 1: A + AB = A)
  ✅ Proved!

INTUITION:
  Think of A as a big circle and A·B as a smaller region inside A.
  "A OR (something inside A)" = just A (the bigger circle absorbs the smaller!)

EXAMPLE — Simplifying with Absorption:
  Y = AB + A    →   Apply Absorption (A + AB = A, reading A as A and B as B)
  But here it's written AB + A = A + AB = A ✅ (same by commutativity)

🎯 PYQ FACT: A + AB = A → Absorption Law (simplification shortcut!)
```

---

### Complete Laws Summary Table:

```
┌────────────────────┬──────────────────────┬──────────────────────┐
│        LAW         │      AND FORM        │       OR FORM        │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Identity Law       │ A · 1 = A            │ A + 0 = A            │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Null Law           │ A · 0 = 0            │ A + 1 = 1            │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Idempotent Law     │ A · A = A            │ A + A = A            │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Complement Law     │ A · A' = 0           │ A + A' = 1           │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Double Complement  │ (A')' = A            │ (same for both)      │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Commutative Law    │ A · B = B · A        │ A + B = B + A        │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Associative Law    │ (AB)C = A(BC)        │ (A+B)+C = A+(B+C)   │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Distributive Law   │ A(B+C) = AB+AC       │ A+(BC) = (A+B)(A+C) │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Absorption Law     │ A·(A+B) = A          │ A + A·B = A          │
└────────────────────┴──────────────────────┴──────────────────────┘
```

---

## 🔷 SECTION 4: De Morgan's Theorem ⭐ HIGHEST PYQ PRIORITY

### What is De Morgan's Theorem?

```
Named after Augustus De Morgan (1806–1871), a British mathematician.

De Morgan's Theorem provides rules for DISTRIBUTING COMPLEMENTATION
(the NOT operation) over AND or OR operations.

It is the SINGLE MOST IMPORTANT theorem in Boolean algebra for:
  → Simplifying complex expressions
  → Implementing NOR/NAND gates as combinations of basic gates
  → Proving equivalence of circuits
  → Understanding NAND and NOR as universal gates (Day 62 connection!)
```

---

### THEOREM 1: Complement of AND → OR of Complements

```
STATEMENT:
  (A · B)' = A' + B'

READ AS:
  "NOT (A AND B) = (NOT A) OR (NOT B)"
  "The complement of a product = the sum of complements"

REAL-LIFE ANALOGY:
  "It is NOT the case that (it is raining AND it is hot)"
  = "It is NOT raining OR it is NOT hot"
  (At least one of the conditions is false!)

LOGIC GATE MEANING:
  A NAND gate = AND gate + NOT at output = (A·B)'
  De Morgan says: NAND(A,B) = (A·B)' = A' + B'
  So a NAND gate is EQUIVALENT to an OR gate with inverted inputs!
  This is why NAND can be used to build all other gates!
```

### Truth Table Verification — Theorem 1: (AB)' = A' + B'

```
┌───┬───┬───────┬──────────┬────┬────┬──────────┐
│ A │ B │ A · B │ (A · B)' │ A' │ B' │  A' + B' │
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 0 │ 0 │   0   │    1     │ 1  │ 1  │    1     │  ✅ Equal
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 0 │ 1 │   0   │    1     │ 1  │ 0  │    1     │  ✅ Equal
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 1 │ 0 │   0   │    1     │ 0  │ 1  │    1     │  ✅ Equal
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 1 │ 1 │   1   │    0     │ 0  │ 0  │    0     │  ✅ Equal
└───┴───┴───────┴──────────┴────┴────┴──────────┘

Column (A·B)' = Column (A'+B') for ALL rows → THEOREM VERIFIED ✅
```

---

### THEOREM 2: Complement of OR → AND of Complements

```
STATEMENT:
  (A + B)' = A' · B'

READ AS:
  "NOT (A OR B) = (NOT A) AND (NOT B)"
  "The complement of a sum = the product of complements"

REAL-LIFE ANALOGY:
  "It is NOT the case that (it is raining OR it is hot)"
  = "It is NOT raining AND it is NOT hot"
  (BOTH conditions must be false for the OR to be false!)

LOGIC GATE MEANING:
  A NOR gate = OR gate + NOT at output = (A+B)'
  De Morgan says: NOR(A,B) = (A+B)' = A'·B'
  So a NOR gate is EQUIVALENT to an AND gate with inverted inputs!
  This is why NOR can also build all other gates!
```

### Truth Table Verification — Theorem 2: (A+B)' = A'·B'

```
┌───┬───┬───────┬──────────┬────┬────┬──────────┐
│ A │ B │ A + B │ (A + B)' │ A' │ B' │  A' · B' │
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 0 │ 0 │   0   │    1     │ 1  │ 1  │    1     │  ✅ Equal
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 0 │ 1 │   1   │    0     │ 1  │ 0  │    0     │  ✅ Equal
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 1 │ 0 │   1   │    0     │ 0  │ 1  │    0     │  ✅ Equal
├───┼───┼───────┼──────────┼────┼────┼──────────┤
│ 1 │ 1 │   1   │    0     │ 0  │ 0  │    0     │  ✅ Equal
└───┴───┴───────┴──────────┴────┴────┴──────────┘

Column (A+B)' = Column (A'·B') for ALL rows → THEOREM VERIFIED ✅
```

---

### De Morgan's — Both Theorems Side by Side:

```
┌────────────────────────────────────────────────────────────────────┐
│                    DE MORGAN'S THEOREMS                             │
├──────────────────────────────┬─────────────────────────────────────┤
│     THEOREM 1                │         THEOREM 2                   │
├──────────────────────────────┬─────────────────────────────────────┤
│  (A · B)' = A' + B'          │  (A + B)' = A' · B'                │
│                              │                                      │
│  Complement of AND           │  Complement of OR                   │
│  = OR of complements         │  = AND of complements               │
│                              │                                      │
│  NAND = OR with NOT inputs   │  NOR = AND with NOT inputs          │
├──────────────────────────────┴─────────────────────────────────────┤
│  MEMORY TRICK:                                                      │
│  "Break the bar, change the sign"                                   │
│                                                                     │
│  To apply De Morgan's to any expression:                            │
│  Step 1: Complement the whole expression (break the bar)           │
│  Step 2: Complement each individual variable                        │
│  Step 3: Change AND(·) to OR(+) or OR(+) to AND(·)                │
│                                                                     │
│  (A·B·C)' = A' + B' + C'    ← Extends to 3 or more variables!    │
│  (A+B+C)' = A' · B' · C'    ← Works for any number of variables! │
└────────────────────────────────────────────────────────────────────┘

🎯 PYQ FACT: (A+B)' = A'·B' — THIS EXACT FORM appears in BPSC TRE PYQs!
🎯 PYQ FACT: De Morgan's is used to simplify NAND/NOR gate expressions.
🚨 TRAP: "(A+B)' = A'+B'" → FALSE! The operation FLIPS: + becomes ·
         Correct: (A+B)' = A'·B'
🚨 TRAP: "(A·B)' = A'·B'" → FALSE! The operation FLIPS: · becomes +
         Correct: (A·B)' = A'+B'
```

---

### DUAL of a Boolean Expression:

```
DEFINITION:
  The DUAL of a Boolean expression is obtained by:
  1. Swapping AND (·) with OR (+)
  2. Swapping 0 with 1
  (Do NOT complement variables — variables stay unchanged!)

EXAMPLES:
  Expression: A · B + 0
  Dual:       A + B · 1     (AND↔OR, 0↔1)

  Expression: (A+B)(C+D)
  Dual:       (A·B)+(C·D)

  De Morgan's Theorem is essentially stating:
  The complement of an expression = dual of the expression with complemented variables!

🎯 PYQ FACT: To find dual: swap AND↔OR and 0↔1 (don't complement variables!).
🚨 TRAP: "Dual means complement all variables" → FALSE! Only swap operators and constants.
```

---

## 🔷 SECTION 5: Boolean Expression Simplification — Step by Step

### Approach:
```
SIMPLIFICATION STRATEGY:
  1. Look for Complement Law patterns: A·A' = 0, A+A' = 1
  2. Look for Null Law shortcuts: A·0 = 0, A+1 = 1
  3. Look for Identity Law: A·1 = A, A+0 = A
  4. Look for Absorption: A+AB = A, A·(A+B) = A
  5. Apply Distributive Law to factor or expand
  6. Apply De Morgan's when you see complements over groups

GOAL: Reduce to fewest literals (variables/complements) possible.
```

### SIMPLIFICATION EXAMPLE 1 — Using Basic Laws:

```
SIMPLIFY: Y = A + A'B

STEP 1: Apply Distributive Law in reverse (OR distributes over AND):
  A + A'B
  = (A + A') · (A + B)    [Distributive: X + YZ = (X+Y)(X+Z)]

STEP 2: Apply Complement Law:
  A + A' = 1

STEP 3: Substitute:
  = 1 · (A + B)

STEP 4: Apply Identity Law:
  1 · (A + B) = A + B

RESULT: Y = A + A'B = A + B  ✅
(Simplified from 2 terms with 3 literals to 1 term with 2 literals)
```

### SIMPLIFICATION EXAMPLE 2 — Using Absorption:

```
SIMPLIFY: Y = AB + A

STEP 1: Rewrite using Commutative Law:
  Y = A + AB    (same expression, reordered)

STEP 2: Apply Absorption Law (A + AB = A):
  Y = A

RESULT: Y = AB + A = A  ✅ (Dramatically simplified!)
```

### SIMPLIFICATION EXAMPLE 3 — Using De Morgan's Theorem:

```
SIMPLIFY: Y = (A' + B')'

STEP 1: Recognize the form (A' + B')' — this is a complement over an OR expression.
  Apply De Morgan's Theorem 2: (X + Y)' = X'·Y' where X=A', Y=B'

STEP 2: Apply De Morgan's:
  (A' + B')' = (A')' · (B')'

STEP 3: Apply Double Complement Law: (A')' = A, (B')' = B:
  = A · B = AB

RESULT: Y = (A' + B')' = AB  ✅
(A NOR gate with inverted inputs = AND gate — confirms De Morgan's meaning!)
```

### SIMPLIFICATION EXAMPLE 4 — Multi-Step:

```
SIMPLIFY: Y = AB + AB'

STEP 1: Factor out A using Distributive Law:
  Y = A(B + B')

STEP 2: Apply Complement Law: B + B' = 1:
  Y = A · 1

STEP 3: Apply Identity Law: A · 1 = A:
  Y = A

RESULT: Y = AB + AB' = A  ✅
(Intuition: AB means "A and B", AB' means "A and not B" — together they just mean "A"!)
```

### SIMPLIFICATION EXAMPLE 5 — PYQ Level:

```
SIMPLIFY: Y = A'B + AB + AB'

STEP 1: Group terms AB' + AB and apply Distributive:
  AB + AB' = A(B + B') = A·1 = A

STEP 2: Substitute back:
  Y = A'B + A

STEP 3: Apply Distributive (reverse): A + A'B = (A+A')(A+B) = 1·(A+B) = A+B:
  Y = A + B

RESULT: Y = A'B + AB + AB' = A + B  ✅
```

---

## 🔷 SECTION 6: SOP and POS Forms ⭐ IMPORTANT

### SOP — Sum of Products:

```
DEFINITION:
  SOP = A Boolean expression written as a SUM (OR) of PRODUCT (AND) terms.
  Each product term is called a MINTERM.

FORMAT:  Y = AB + BC + A'C + A'B'C
         (multiple AND terms, joined by OR)

STRUCTURE:
  → Each individual term: variables ANDed together (product)
  → Multiple terms: ORed together (sum)
  → "Sum of Products" = OR of AND-terms

EXAMPLE:
  Y = AB + A'C + BC
  → Term 1: AB (A AND B)
  → Term 2: A'C (NOT-A AND C)
  → Term 3: BC (B AND C)
  → Final: (AB) OR (A'C) OR (BC)

WHEN OUTPUT = 1:
  SOP gives output 1 when ANY of the product terms is 1.

REAL CIRCUIT:
  SOP is implemented with AND gates feeding into an OR gate.
  (AND gates for each product term → OR gate combines them)
```

### POS — Product of Sums:

```
DEFINITION:
  POS = A Boolean expression written as a PRODUCT (AND) of SUM (OR) terms.
  Each sum term is called a MAXTERM.

FORMAT:  Y = (A+B)(B+C)(A'+C)
         (multiple OR terms, joined by AND)

STRUCTURE:
  → Each individual term: variables ORed together (sum)
  → Multiple terms: ANDed together (product)
  → "Product of Sums" = AND of OR-terms

EXAMPLE:
  Y = (A+B)(A'+C)(B+C')
  → Term 1: (A+B)   — A OR B
  → Term 2: (A'+C)  — NOT-A OR C
  → Term 3: (B+C')  — B OR NOT-C
  → Final: (A+B) AND (A'+C) AND (B+C')

WHEN OUTPUT = 0:
  POS gives output 0 when ANY of the sum terms is 0.

REAL CIRCUIT:
  POS is implemented with OR gates feeding into an AND gate.
  (OR gates for each sum term → AND gate combines them)
```

### SOP vs POS — Comparison Table:

```
┌──────────────────────────┬────────────────────────┬────────────────────────┐
│         FEATURE          │         SOP             │         POS            │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Full Name                │ Sum of Products        │ Product of Sums        │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Structure                │ (AND terms) OR'd       │ (OR terms) AND'd       │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Individual term          │ Product term (minterm) │ Sum term (maxterm)     │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Example                  │ AB + A'C + BC          │ (A+B)(A'+C)(B+C')     │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Output 1 when            │ Any AND-term = 1       │ All OR-terms = 1       │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Output 0 when            │ All AND-terms = 0      │ Any OR-term = 0        │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Gate structure           │ AND gates → OR gate    │ OR gates → AND gate    │
│                          │ (AND-OR structure)     │ (OR-AND structure)     │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Canonical form           │ Sum of Minterms (SOM)  │ Product of Maxterms   │
│                          │                        │ (POM)                  │
├──────────────────────────┼────────────────────────┼────────────────────────┤
│ Related to rows where    │ Output = 1 rows        │ Output = 0 rows        │
│ (in truth table)         │                        │                        │
└──────────────────────────┴────────────────────────┴────────────────────────┘

🎯 PYQ FACT: SOP = OR of AND terms; POS = AND of OR terms.
🎯 PYQ FACT: SOP uses AND gates feeding OR gate; POS uses OR gates feeding AND gate.
```

---

## 🔷 SECTION 7: Canonical Forms — SOM and POM

### What are Canonical Forms?

```
A canonical form is a UNIQUE, STANDARD representation of a Boolean function.
Just like a fraction in "lowest terms" is the canonical form of a rational number.

There are TWO canonical forms:
  SOM = Canonical SOP  (Sum of Minterms)
  POM = Canonical POS  (Product of Maxterms)
```

### Minterms:

```
DEFINITION:
  A MINTERM for n variables is a product (AND) term in which
  each variable appears EXACTLY ONCE — either complemented or uncomplemented.

For 2 variables (A, B): there are 2² = 4 minterms:
  m₀: A'B' (when A=0, B=0 → index 0 in binary)
  m₁: A'B  (when A=0, B=1 → index 1)
  m₂: AB'  (when A=1, B=0 → index 2)
  m₃: AB   (when A=1, B=1 → index 3)

A minterm mₙ = 1 ONLY for the specific row n in the truth table.
All other rows → minterm = 0.

SOM (Sum of Minterms) = OR all minterms where the function output = 1.

EXAMPLE:
  If function f(A,B) = 1 for rows 1 and 3:
  f = m₁ + m₃ = A'B + AB
  Written as: f(A,B) = Σ(1,3)   [Sigma notation for SOM]
```

### Maxterms:

```
DEFINITION:
  A MAXTERM for n variables is a sum (OR) term in which
  each variable appears EXACTLY ONCE — either complemented or uncomplemented.
  A maxterm is 0 for exactly ONE combination of inputs.

For 2 variables (A, B): there are 4 maxterms:
  M₀: A+B    (= 0 when A=0, B=0 → index 0)
  M₁: A+B'   (= 0 when A=0, B=1 → index 1)
  M₂: A'+B   (= 0 when A=1, B=0 → index 2)
  M₃: A'+B'  (= 0 when A=1, B=1 → index 3)

NOTE: Maxterm is the COMPLEMENT of the corresponding minterm!
  M₀ = (m₀)' = (A'B')' = A+B  (De Morgan's!)

POM (Product of Maxterms) = AND all maxterms where the function output = 0.

EXAMPLE:
  If function f(A,B) = 0 for rows 0 and 2:
  f = M₀ · M₂ = (A+B)(A'+B)
  Written as: f(A,B) = Π(0,2)   [Pi notation for POM]
```

### SOM vs POM Quick Reference:

```
┌─────────────────────────┬───────────────────────┬───────────────────────┐
│        FEATURE          │    SOM (Min terms)    │    POM (Maxterms)     │
├─────────────────────────┼───────────────────────┼───────────────────────┤
│ Full name               │ Sum of Minterms       │ Product of Maxterms   │
├─────────────────────────┼───────────────────────┼───────────────────────┤
│ Built from rows where   │ Output = 1            │ Output = 0            │
├─────────────────────────┼───────────────────────┼───────────────────────┤
│ Notation                │ Σ(row numbers)        │ Π(row numbers)        │
├─────────────────────────┼───────────────────────┼───────────────────────┤
│ Type of term            │ AND terms (products)  │ OR terms (sums)       │
├─────────────────────────┼───────────────────────┼───────────────────────┤
│ Relationship            │ SOM and POM are complementary forms of same  │
│                         │ function — SOM uses 1-rows; POM uses 0-rows  │
└─────────────────────────┴───────────────────────┴───────────────────────┘

🎯 PYQ FACT: Canonical forms = SOM (Sum of Minterms) and POM (Product of Maxterms)
🎯 PYQ FACT: SOM written using Σ notation; POM using Π notation.
```

---

## 🔷 SECTION 8: PYQ Traps — Boolean Algebra & De Morgan's

```
🚨 TRAP 1: "(A+B)' = A' + B'" → FALSE!
   The SIGN CHANGES when applying De Morgan's!
   (A+B)' = A' · B'  (OR becomes AND)
   (A·B)' = A' + B'  (AND becomes OR)
   "Break the bar, CHANGE THE SIGN"

🚨 TRAP 2: "De Morgan's theorem only works for 2 variables" → FALSE!
   Extends to ANY number of variables:
   (A+B+C+D)' = A'·B'·C'·D'
   (ABCD)' = A'+B'+C'+D'

🚨 TRAP 3: "The dual of an expression = complement of expression" → FALSE!
   DUAL: swap AND↔OR and 0↔1 (variables UNCHANGED)
   COMPLEMENT: apply De Morgan's (variables complemented too)
   These are DIFFERENT operations!

🚨 TRAP 4: "In Boolean algebra, 1+1 = 2" → FALSE!
   Boolean: 1+1 = 1 (OR: true OR true = true — not arithmetic addition!)
   Regular arithmetic: 1+1 = 2

🚨 TRAP 5: "Identity Law: A·0 = A" → FALSE!
   Identity Law: A·1 = A and A+0 = A
   A·0 = 0 is the NULL LAW (not identity!)

🚨 TRAP 6: "Null Law: A+0 = 0" → FALSE!
   Null Law (AND): A·0 = 0  |  Null Law (OR): A+1 = 1
   A+0 = A is the IDENTITY LAW!

🚨 TRAP 7: "SOP = AND of OR terms" → FALSE!
   SOP = Sum of Products = OR of AND terms (AND first, then OR!)
   POS = Product of Sums = AND of OR terms (OR first, then AND!)

🚨 TRAP 8: "Minterms are used in POM" → FALSE!
   SOM uses MINTERMS (rows where output = 1)
   POM uses MAXTERMS (rows where output = 0)

🚨 TRAP 9: "Absorption Law: A + AB = AB" → FALSE!
   Absorption: A + AB = A (A absorbs the AB term, not the other way!)
   The SIMPLER term wins!

🚨 TRAP 10: "Boolean algebra has only ONE distributive law" → FALSE!
   Boolean has TWO distributive laws:
   Form 1: A(B+C) = AB+AC (standard — same as regular algebra)
   Form 2: A+(B·C) = (A+B)(A+C) (UNIQUE to Boolean — no equivalent in regular math!)
```

---

# PART 2: GENERAL STUDIES
## 🏦 Indian Economy — Banking & Monetary Policy

---

## 🔷 SECTION 1: What is a Bank?

### Real-Life Analogy — The Money Warehouse:

Imagine a safe warehouse in your city. People deposit their valuables there for safekeeping. The warehouse keeper uses those valuables to give loans to others who need them — charging a small fee. When the depositors want their valuables back, the keeper returns them. This is essentially what a bank does — but with money.

> **A bank is a financial institution that accepts deposits from the public, safeguards them, and uses those funds to provide loans and credit to individuals, businesses, and governments — earning profit from the interest rate difference.**

---

## 🔷 SECTION 2: Functions of Banks

### Primary Functions:
```
1. ACCEPTING DEPOSITS:
   → Savings Account: Low interest, flexible withdrawal
   → Current Account: No interest, unlimited transactions (businesses use this)
   → Fixed Deposit (FD): Higher interest, locked for a period
   → Recurring Deposit (RD): Monthly instalments, fixed return

2. LENDING / ADVANCING LOANS:
   → Home loans, personal loans, business loans, education loans
   → Banks charge INTEREST on loans (higher than deposit interest)
   → This SPREAD between deposit interest and loan interest = bank's profit

3. CREDIT CREATION:
   → Banks create credit by lending out deposits multiple times
   → This is the BASIS of the money multiplier effect
   → Example: ₹100 deposited → bank lends ₹80 → borrower deposits ₹80
     → bank lends ₹64 from that → chain continues → total money in economy > ₹100!

🎯 PYQ FACT: Banks create credit through fractional reserve banking.
```

### Secondary Functions:
```
4. REMITTANCE:  Transfer of money (NEFT, RTGS, IMPS)
5. AGENCY:      Collect cheques, pay insurance premiums on behalf of customers
6. FOREIGN EXCHANGE: Buy/sell foreign currency
7. LOCKER FACILITY: Safe deposit lockers for valuables
8. ADVISORY:    Financial advice, investment products
```

---

## 🔷 SECTION 3: Types of Banks

```
┌──────────────────────────────────────────────────────────────────────┐
│                    BANKING SYSTEM IN INDIA                           │
├────────────────────────────────────────────────────────────────────  ┤
│                                                                      │
│  1. CENTRAL BANK (RBI — Reserve Bank of India)                      │
│     → Apex bank of India; NOT a commercial bank                     │
│     → Does NOT deal directly with the public                        │
│     → Controls the entire banking system                            │
│     → Issues currency, controls monetary policy                     │
│                                                                      │
│  2. COMMERCIAL BANKS                                                 │
│     a) Public Sector Banks (Govt owned):                            │
│        → SBI (State Bank of India) — largest bank in India          │
│        → Punjab National Bank, Bank of Baroda, Canara Bank, etc.   │
│                                                                      │
│     b) Private Sector Banks:                                        │
│        → HDFC Bank, ICICI Bank, Axis Bank, Kotak Mahindra          │
│                                                                      │
│     c) Foreign Banks:                                               │
│        → Citibank, HSBC, Standard Chartered                        │
│                                                                      │
│  3. COOPERATIVE BANKS                                               │
│     → Serve rural and agricultural communities                      │
│     → NABARD (National Bank for Agriculture & Rural Dev.) oversees  │
│                                                                      │
│  4. DEVELOPMENT BANKS / FINANCIAL INSTITUTIONS                      │
│     → NABARD (Agriculture), NHB (Housing), SIDBI (Small Industries)│
│     → EXIM Bank (Export-Import financing)                           │
│                                                                      │
│  5. PAYMENTS BANKS (NEW — RBI licensed)                             │
│     → Can accept deposits but CANNOT give loans                     │
│     → Paytm Payments Bank, Airtel Payments Bank                    │
│                                                                      │
│  6. SMALL FINANCE BANKS                                             │
│     → Serve underbanked segments; give small loans                  │
└──────────────────────────────────────────────────────────────────────┘

🎯 PYQ FACT: SBI = largest bank in India (public sector).
🎯 PYQ FACT: RBI is India's CENTRAL BANK (not a commercial bank).
🎯 PYQ FACT: NABARD = National Bank for Agriculture and Rural Development.
```

---

## 🔷 SECTION 4: RBI — Reserve Bank of India ⭐ HIGH PRIORITY

### Basic Facts:
```
FULL NAME:     Reserve Bank of India (RBI)
ESTABLISHED:   1 April 1935 (under Reserve Bank of India Act, 1934)
HEADQUARTERS:  Mumbai (Maharashtra)
NATIONALIZED:  1949 (brought under government ownership)
GOVERNOR:      Head of RBI — appointed by the Union Government
               (Current Governor: Check latest — changes periodically)
TYPE:          Central Bank of India
```

### RBI's Core Functions:

```
FUNCTION 1 — ISSUE OF CURRENCY (NOTES):
  → RBI is the SOLE authority to issue currency notes in India
  → EXCEPT: One Rupee note and coins — issued by the Ministry of Finance
  → All notes above ₹1 are issued by RBI
  → The Governor's signature appears on currency notes

  🎯 PYQ FACT: RBI issues all currency notes EXCEPT ₹1 note and coins.
  🎯 PYQ FACT: ₹1 note is signed by the Finance Secretary (not RBI Governor).

FUNCTION 2 — BANKER TO THE GOVERNMENT:
  → Manages accounts of the Central and State governments
  → Manages public debt (government borrowings)
  → Advises government on financial and economic matters
  → Acts as agent for the government in financial matters

FUNCTION 3 — BANKER'S BANK:
  → Acts as the "bank for banks"
  → Commercial banks maintain accounts with RBI
  → RBI is the LENDER OF LAST RESORT — if a commercial bank faces crisis,
    RBI provides emergency funds to prevent collapse
  → Supervises and regulates commercial banks

  🎯 PYQ FACT: RBI = "Banker's Bank" and "Lender of Last Resort"

FUNCTION 4 — CONTROLLER OF CREDIT (MONETARY POLICY):
  → Controls money supply and credit in the economy
  → Uses monetary policy tools (Repo Rate, CRR, SLR, OMO)
  → Targets INFLATION CONTROL (2–6% inflation band — RBI's mandate)
  → Works to maintain price stability and economic growth

FUNCTION 5 — FOREIGN EXCHANGE MANAGEMENT:
  → Manages India's FOREIGN EXCHANGE RESERVES
  → Maintains stability of the Indian Rupee exchange rate
  → Administers FEMA (Foreign Exchange Management Act, 1999)

FUNCTION 6 — CLEARING HOUSE:
  → Operates inter-bank clearing and settlement systems
  → Runs RTGS (Real Time Gross Settlement) and NEFT systems
```

---

## 🔷 SECTION 5: Monetary Policy — Complete Coverage ⭐

### What is Monetary Policy?

```
DEFINITION:
  Monetary Policy is the process by which the Reserve Bank of India (RBI)
  controls the SUPPLY OF MONEY and INTEREST RATES in the economy
  to achieve macroeconomic objectives.

OBJECTIVES of Monetary Policy:
  → Control inflation (keep prices stable)
  → Promote economic growth
  → Maintain employment
  → Stabilize the exchange rate

TYPES:
  EXPANSIONARY (Loose) Monetary Policy:
    → RBI INCREASES money supply
    → LOWERS interest rates
    → Used to STIMULATE growth (during recession/slowdown)
    → Effect: More credit → more spending → more growth

  CONTRACTIONARY (Tight) Monetary Policy:
    → RBI DECREASES money supply
    → RAISES interest rates
    → Used to CONTROL INFLATION
    → Effect: Less credit → less spending → inflation falls
```

---

### TOOL 1: REPO RATE ⭐ MOST TESTED

```
FULL FORM: Repurchase Agreement Rate

DEFINITION:
  The rate at which the RBI LENDS money to commercial banks
  for SHORT-TERM (usually overnight) needs.
  Banks BORROW from RBI at the Repo Rate.

MECHANISM:
  Banks sell government securities to RBI + promise to REPURCHASE them next day.
  The interest charged on this = REPO RATE.

DIRECTION OF EFFECT:
  Repo Rate ↑ (RBI increases) →
    → Banks' cost of borrowing from RBI increases
    → Banks raise their lending rates (home loans, business loans become costlier)
    → People and businesses borrow less
    → Less spending and investment
    → Demand falls → Inflation comes down ✅

  Repo Rate ↓ (RBI decreases) →
    → Banks' borrowing cost falls
    → Banks lower their lending rates
    → More loans taken → more spending → economic activity increases ✅

USE: RBI raises Repo Rate to FIGHT INFLATION.
     RBI lowers Repo Rate to STIMULATE GROWTH.

🎯 PYQ FACT: Repo Rate = rate at which RBI LENDS to commercial banks.
🎯 PYQ FACT: Repo Rate ↑ → credit expensive → inflation controlled.
```

---

### TOOL 2: REVERSE REPO RATE ⭐

```
DEFINITION:
  The rate at which the RBI BORROWS money from commercial banks.
  Banks LEND their excess funds to RBI at the Reverse Repo Rate.

MECHANISM:
  Commercial banks park their surplus funds with RBI overnight.
  RBI pays interest on this = REVERSE REPO RATE.

DIRECTION OF EFFECT:
  Reverse Repo Rate ↑ →
    → Banks find it MORE ATTRACTIVE to park money with RBI (earn more interest)
    → Banks lend LESS to public (park more with RBI instead)
    → Money supply in economy DECREASES
    → Inflation controlled ✅

  Reverse Repo Rate ↓ →
    → Less attractive for banks to park with RBI
    → Banks lend MORE to public
    → Money supply INCREASES → economic activity ↑

RELATIONSHIP: Reverse Repo Rate is ALWAYS LOWER than Repo Rate.
  (RBI borrows cheap, lends at a higher rate — like any bank!)

FORMULA: Reverse Repo Rate < Repo Rate (always)

🎯 PYQ FACT: Reverse Repo Rate = rate at which RBI BORROWS from commercial banks.
🎯 PYQ FACT: Reverse Repo Rate is LOWER than Repo Rate.
🚨 TRAP: "Reverse Repo Rate = rate at which banks borrow from RBI" → FALSE!
         Banks BORROW at REPO RATE.
         Banks LEND (park money) at REVERSE REPO RATE.
```

---

### TOOL 3: CRR — Cash Reserve Ratio ⭐

```
DEFINITION:
  The percentage of a bank's total DEMAND AND TIME LIABILITIES (deposits)
  that it must maintain as CASH with the RBI.
  This cash earns NO INTEREST for banks.

EXAMPLE:
  CRR = 4% (hypothetical)
  Bank has ₹100 crore in deposits
  → Must keep ₹4 crore as CASH with RBI at all times
  → Only ₹96 crore available for lending

DIRECTION OF EFFECT:
  CRR ↑ (RBI increases) →
    → Banks must keep MORE cash with RBI
    → LESS money available for lending
    → Credit in economy falls
    → Inflation controlled ✅

  CRR ↓ (RBI decreases) →
    → Banks keep LESS cash with RBI
    → MORE money available for lending
    → Credit expands → economic activity increases ✅

🎯 PYQ FACT: CRR increase → banks have less to lend → money supply falls.
🎯 PYQ FACT: CRR cash kept with RBI earns NO interest for banks.
```

---

### TOOL 4: SLR — Statutory Liquidity Ratio ⭐

```
DEFINITION:
  The percentage of a bank's total NET DEMAND AND TIME LIABILITIES (deposits)
  that it must invest in APPROVED LIQUID ASSETS:
  → Government securities (G-secs)
  → Cash (in their own vaults — not with RBI)
  → Gold

EXAMPLE:
  SLR = 18% (hypothetical)
  Bank has ₹100 crore in deposits
  → Must invest ₹18 crore in government securities/gold/cash
  → Only ₹82 crore available for other lending

DIRECTION OF EFFECT:
  SLR ↑ →
    → More funds locked in government securities
    → Less available for private sector lending
    → Credit contracts → inflation controlled ✅

  SLR ↓ →
    → Less locked up
    → More available for lending
    → Credit expands ✅

🎯 PYQ FACT: SLR = investment in government securities, gold, cash.
🎯 PYQ FACT: SLR ensures banks always have liquid assets to meet obligations.
```

---

### TOOL 5: Bank Rate & Open Market Operations (OMO)

```
BANK RATE:
  Rate at which RBI lends LONG-TERM funds to commercial banks.
  (Repo = short-term/overnight; Bank Rate = long-term)
  Bank Rate ↑ → borrowing expensive → credit contracts → inflation falls.

OPEN MARKET OPERATIONS (OMO):
  RBI buys or sells government securities in the open market.
  
  RBI SELLS securities:
    → Banks use their cash to buy securities from RBI
    → Cash moves from banks to RBI
    → Money supply in economy DECREASES → inflation controlled

  RBI BUYS securities:
    → RBI pays cash to banks for their securities
    → Cash moves from RBI to banks
    → Money supply INCREASES → stimulates growth
```

---

### Monetary Policy Tools — Master Comparison Table:

```
┌────────────────┬──────────────────────────────┬──────────────────────────────┐
│     TOOL       │        DEFINITION             │     EFFECT ON INFLATION      │
├────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Repo Rate      │ Rate RBI lends to banks       │ ↑ Rate → ↓ credit → ↓       │
│                │ (short-term/overnight)        │ inflation                    │
├────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Reverse Repo   │ Rate RBI borrows from banks   │ ↑ Rate → banks park more     │
│ Rate           │ (banks lend to RBI)           │ with RBI → ↓ money supply   │
├────────────────┼──────────────────────────────┼──────────────────────────────┤
│ CRR            │ % of deposits kept as cash    │ ↑ CRR → less to lend →      │
│                │ with RBI (earns no interest!) │ ↓ money supply              │
├────────────────┼──────────────────────────────┼──────────────────────────────┤
│ SLR            │ % of deposits in approved     │ ↑ SLR → less for private    │
│                │ liquid assets (G-secs/gold)   │ lending → ↓ money supply    │
├────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Bank Rate      │ Rate RBI lends long-term      │ ↑ Rate → costly borrowing   │
│                │ to banks                      │ → ↓ credit                  │
├────────────────┼──────────────────────────────┼──────────────────────────────┤
│ OMO            │ RBI buys/sells govt           │ Sell → ↓ money supply       │
│                │ securities in market          │ Buy  → ↑ money supply       │
└────────────────┴──────────────────────────────┴──────────────────────────────┘

RELATIONSHIP BETWEEN RATES:
  Reverse Repo Rate < Repo Rate < Bank Rate
  (Banks park at lowest rate; borrow short-term at middle; borrow long-term at highest)

🎯 PYQ FACT: Reverse Repo < Repo < Bank Rate (always in this order!)
```

---

### Memory Tricks — Banking & Monetary Policy:

```
REPO vs REVERSE REPO — NEVER CONFUSE AGAIN:
  REPO   = "RE-PO" = RBI POuring money to banks (RBI lends TO banks)
  REVERSE REPO = REVERSE direction = banks pour money to RBI (banks lend TO RBI)

CRR vs SLR — REMEMBER THE DIFFERENCE:
  CRR = Cash with RBI (C for Cash, R for RBI — CRR = Cash at RBI)
         Earns ZERO interest for banks (it just sits idle at RBI!)
  SLR = Securities + Liquid assets (S for Securities — can earn interest!)
         Banks invest in govt bonds — they do earn some return!

INFLATION FIGHTING TOOLS SUMMARY:
  "RAISE to fight inflation" — RBI RAISES all these:
  ↑ Repo Rate → ↑ Reverse Repo Rate → ↑ CRR → ↑ SLR
  All these reduce money supply → fight inflation

LENDER OF LAST RESORT:
  "When all else fails, RBI is there"
  Like a safety net for the banking system — no bank can fail for lack of funds
  as long as RBI is standing.
```

---

## 🔷 SECTION 6: PYQ Traps — Banking & Monetary Policy

```
🚨 TRAP 1: "RBI issues all Indian currency including ₹1 coin" → FALSE!
   RBI issues all notes EXCEPT ₹1 note and coins.
   ₹1 note and all coins = issued by Government (Ministry of Finance).

🚨 TRAP 2: "Repo Rate = rate at which banks lend to RBI" → FALSE!
   REPO RATE = RBI LENDS to banks (banks borrow from RBI at repo rate).
   REVERSE REPO = RBI BORROWS from banks (banks lend to RBI at reverse repo rate).

🚨 TRAP 3: "Reverse Repo Rate is HIGHER than Repo Rate" → FALSE!
   Reverse Repo Rate is ALWAYS LOWER than Repo Rate.
   Order: Reverse Repo < Repo < Bank Rate

🚨 TRAP 4: "To STIMULATE growth, RBI raises Repo Rate" → FALSE!
   To STIMULATE: RBI LOWERS Repo Rate (cheap credit → more borrowing → growth)
   To FIGHT INFLATION: RBI RAISES Repo Rate (costly credit → less borrowing)

🚨 TRAP 5: "CRR earns interest for commercial banks" → FALSE!
   CRR cash kept with RBI earns ZERO INTEREST for commercial banks.
   SLR investments (government securities) DO earn some interest.

🚨 TRAP 6: "RBI was established in 1947 after independence" → FALSE!
   RBI was established on 1 April 1935 (under British rule!).
   It was NATIONALIZED in 1949 (after independence).

🚨 TRAP 7: "SBI is India's central bank" → FALSE!
   SBI = State Bank of India = largest COMMERCIAL bank.
   RBI = Reserve Bank of India = India's CENTRAL BANK.
   Very different roles!

🚨 TRAP 8: "OMO involves buying/selling STOCKS" → FALSE!
   OMO = buying/selling GOVERNMENT SECURITIES (bonds/G-secs), not stocks.

🚨 TRAP 9: "Payments Banks can give loans" → FALSE!
   Payments Banks can ONLY accept deposits (up to ₹2 lakh limit);
   they CANNOT give loans or credit cards.

🚨 TRAP 10: "NABARD is a commercial bank" → FALSE!
   NABARD = National Bank for Agriculture and Rural Development.
   It is a DEVELOPMENT BANK (apex bank for agriculture/rural finance),
   NOT a commercial bank.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Boolean Laws, De Morgan's Theorem, Simplification, SOP & POS, Canonical Forms

---

**Q1.** Boolean algebra was developed by:
(A) Charles Babbage
(B) Claude Shannon
(C) George Boole
(D) More than one of the above
(E) None of the above

---

**Q2.** In Boolean algebra, the Identity Law states:
(A) A · 0 = 0 and A + 1 = 1
(B) A · 1 = A and A + 0 = A
(C) A · A = A and A + A = A
(D) More than one of the above
(E) None of the above

---

**Q3.** Which law states: A · 0 = 0 and A + 1 = 1?
(A) Identity Law
(B) Idempotent Law
(C) Null Law (Dominance Law)
(D) More than one of the above
(E) None of the above

---

**Q4.** The Idempotent Law in Boolean algebra states:
(A) A · 1 = A and A + 0 = A
(B) A · A = A and A + A = A
(C) A · A' = 0 and A + A' = 1
(D) More than one of the above
(E) None of the above

---

**Q5.** According to the Complement Law of Boolean algebra:
(A) A · A = A and A + A = A
(B) A · A' = 0 and A + A' = 1
(C) A · 1 = A and A + 0 = A
(D) More than one of the above
(E) None of the above

---

**Q6.** De Morgan's Theorem states that (A · B)' equals:
(A) A' · B'
(B) A · B
(C) A' + B'
(D) More than one of the above
(E) None of the above

---

**Q7.** De Morgan's Theorem states that (A + B)' equals:
(A) A' + B'
(B) A' · B'
(C) A + B
(D) More than one of the above
(E) None of the above

---

**Q8.** Using De Morgan's Theorem, simplify: (A' + B')'
(A) A + B
(B) A' · B'
(C) A · B
(D) More than one of the above
(E) None of the above

---

**Q9.** Using De Morgan's Theorem, what is (A' · B')'?
(A) A · B
(B) A' + B'
(C) A + B
(D) More than one of the above
(E) None of the above

---

**Q10.** Which law states: A + A·B = A?
(A) Distributive Law
(B) Complement Law
(C) Absorption Law
(D) More than one of the above
(E) None of the above

---

**Q11.** Simplify: Y = AB + AB'
(A) Y = A + B
(B) Y = AB
(C) Y = A
(D) More than one of the above
(E) None of the above

---

**Q12.** Simplify: Y = A + A'B
(A) Y = A
(B) Y = A + B
(C) Y = AB
(D) More than one of the above
(E) None of the above

---

**Q13.** Simplify: Y = (A + B)(A + B')
(A) Y = A + B
(B) Y = AB
(C) Y = A
(D) More than one of the above
(E) None of the above

---

**Q14.** What is the double complement of A, i.e., (A')'?
(A) A' (complement of A)
(B) 0
(C) A (original value)
(D) More than one of the above
(E) None of the above

---

**Q15.** Boolean algebra has how many Distributive Laws?
(A) One — same as regular algebra
(B) Two — one for AND over OR, one for OR over AND
(C) Three — one for each basic operation
(D) More than one of the above
(E) None of the above

---

**Q16.** SOP (Sum of Products) is a Boolean expression written as:
(A) AND of OR terms
(B) OR of AND terms
(C) OR of OR terms
(D) More than one of the above
(E) None of the above

---

**Q17.** POS (Product of Sums) is a Boolean expression written as:
(A) OR of AND terms
(B) AND of AND terms
(C) AND of OR terms
(D) More than one of the above
(E) None of the above

---

**Q18.** The expression AB + A'C + BC is an example of:
(A) POS form
(B) SOP form
(C) Canonical POS form (POM)
(D) More than one of the above
(E) None of the above

---

**Q19.** The expression (A+B)(A'+C)(B+C') is an example of:
(A) SOP form
(B) Canonical SOP form (SOM)
(C) POS form
(D) More than one of the above
(E) None of the above

---

**Q20.** Minterms are used to form which canonical expression?
(A) Product of Maxterms (POM)
(B) Sum of Minterms (SOM) — canonical SOP
(C) Product of Sums (POS)
(D) More than one of the above
(E) None of the above

---

**Q21.** To find the DUAL of a Boolean expression, you must:
(A) Complement all variables and keep operators the same
(B) Swap AND with OR, and swap 0 with 1 (variables unchanged)
(C) Apply De Morgan's theorem to the entire expression
(D) More than one of the above
(E) None of the above

---

**Q22.** Simplify using Boolean laws: Y = A·1 + B·0 + A'·A
(A) Y = A + B
(B) Y = A
(C) Y = A + 1
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly applies De Morgan's theorem to 3 variables?
(A) (A+B+C)' = A'+B'+C'
(B) (A·B·C)' = A'·B'·C'
(C) (A·B·C)' = A'+B'+C'
(D) More than one of the above
(E) None of the above

---

**Q24.** In Boolean algebra, the Distributive Law A + (B·C) = (A+B)·(A+C) is:
(A) The same as the regular algebraic distributive law
(B) Unique to Boolean algebra — has NO equivalent in regular arithmetic
(C) Only valid when A=1
(D) More than one of the above
(E) None of the above

---

**Q25.** Simplify: Y = A'B + AB + AB'
(A) Y = A'B + A
(B) Y = A + B
(C) Y = A + AB'
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Banking, RBI Functions, Monetary Policy Tools

---

**Q26.** The Reserve Bank of India (RBI) was established on:
(A) 15 August 1947
(B) 26 January 1950
(C) 1 April 1935
(D) More than one of the above
(E) None of the above

---

**Q27.** The headquarters of the Reserve Bank of India is located in:
(A) New Delhi
(B) Kolkata
(C) Mumbai
(D) More than one of the above
(E) None of the above

---

**Q28.** Which currency notes in India are NOT issued by the Reserve Bank of India?
(A) ₹500 and ₹2000 notes
(B) ₹100 and ₹50 notes
(C) ₹1 note and all coins
(D) More than one of the above
(E) None of the above

---

**Q29.** The Repo Rate is defined as:
(A) The rate at which commercial banks lend to the RBI
(B) The rate at which the RBI lends money to commercial banks
(C) The rate at which banks lend to each other overnight
(D) More than one of the above
(E) None of the above

---

**Q30.** The Reverse Repo Rate is the rate at which:
(A) RBI lends to commercial banks for long-term needs
(B) RBI borrows money from commercial banks
(C) Commercial banks lend to each other
(D) More than one of the above
(E) None of the above

---

**Q31.** Which of the following correctly describes the relationship between Repo Rate and Reverse Repo Rate?
(A) Reverse Repo Rate > Repo Rate
(B) Reverse Repo Rate = Repo Rate
(C) Reverse Repo Rate < Repo Rate
(D) More than one of the above
(E) None of the above

---

**Q32.** Cash Reserve Ratio (CRR) requires banks to:
(A) Invest a percentage of deposits in government securities
(B) Maintain a percentage of deposits as CASH with the RBI
(C) Keep a percentage of deposits in gold vaults
(D) More than one of the above
(E) None of the above

---

**Q33.** Statutory Liquidity Ratio (SLR) requires banks to maintain a percentage of their deposits in:
(A) Cash kept with RBI only
(B) Foreign exchange reserves
(C) Approved liquid assets — government securities, gold, or cash in vaults
(D) More than one of the above
(E) None of the above

---

**Q34.** When the RBI increases the CRR, what is the immediate effect?
(A) Banks have MORE funds available to lend
(B) Money supply in the economy increases
(C) Banks have LESS funds available to lend; money supply decreases
(D) More than one of the above
(E) None of the above

---

**Q35.** To combat rising inflation, which action would the RBI most likely take?
(A) Reduce the Repo Rate to make borrowing cheaper
(B) Reduce the CRR to release more funds into the economy
(C) Increase the Repo Rate to make borrowing more expensive
(D) More than one of the above
(E) None of the above

---

**Q36.** RBI is described as the "Lender of Last Resort" because:
(A) It provides emergency funds to commercial banks facing liquidity crises
(B) It is the last institution that gives loans to individuals who are rejected elsewhere
(C) It lends to government only when all other sources of funds are exhausted
(D) More than one of the above
(E) None of the above

---

**Q37.** Open Market Operations (OMO) by RBI involves:
(A) Opening new bank branches in rural areas
(B) Buying and selling government securities in the open market to control money supply
(C) Regulating the stock markets (NSE and BSE)
(D) More than one of the above
(E) None of the above

---

**Q38.** When RBI SELLS government securities in the open market (OMO), the effect is:
(A) Money supply in the economy increases (inflationary)
(B) Money supply in the economy decreases (anti-inflationary)
(C) No effect on money supply
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following is the largest PUBLIC SECTOR bank in India?
(A) HDFC Bank
(B) ICICI Bank
(C) State Bank of India (SBI)
(D) More than one of the above
(E) None of the above

---

**Q40.** NABARD (National Bank for Agriculture and Rural Development) primarily serves:
(A) Large multinational corporations
(B) Export-import financing for Indian companies
(C) Agriculture and rural development financing
(D) More than one of the above
(E) None of the above

---

**Q41.** A Payments Bank in India is different from a commercial bank in that it:
(A) Can provide home loans and personal loans
(B) Can accept deposits up to a limit but CANNOT provide loans or issue credit cards
(C) Is managed entirely by the RBI directly
(D) More than one of the above
(E) None of the above

---

**Q42.** The Cash Reserve Ratio (CRR) cash kept with RBI earns:
(A) Interest at the Repo Rate
(B) Interest at the Reverse Repo Rate
(C) No interest (zero interest)
(D) More than one of the above
(E) None of the above

---

**Q43.** Which of the following is a function of the Reserve Bank of India?
(A) Collecting direct taxes from citizens (income tax)
(B) Managing India's foreign exchange reserves and administering FEMA
(C) Issuing passports and travel documents
(D) More than one of the above
(E) None of the above

---

**Q44.** The monetary policy committee (MPC) of RBI sets which rate primarily?
(A) CRR
(B) SLR
(C) Repo Rate (policy rate)
(D) More than one of the above
(E) None of the above

---

**Q45.** When RBI lowers the Repo Rate, the most likely economic effect is:
(A) Inflation increases as credit becomes cheaper and demand rises
(B) Inflation decreases as borrowing becomes more expensive
(C) No change in economic activity
(D) More than one of the above
(E) None of the above

---

**Q46.** RBI was nationalized (brought under government ownership) in:
(A) 1935
(B) 1947
(C) 1949
(D) More than one of the above
(E) None of the above

---

**Q47.** The ₹1 note in India is signed by:
(A) Governor of RBI
(B) Deputy Governor of RBI
(C) Finance Secretary, Ministry of Finance
(D) More than one of the above
(E) None of the above

---

**Q48.** Consider the following about monetary policy tools:
I. Repo Rate is the rate at which RBI lends to banks.
II. Reverse Repo Rate is always higher than Repo Rate.
III. CRR cash kept with RBI earns no interest for banks.
IV. SLR requires investment in approved liquid assets including government securities.

Which statements are CORRECT?
(A) I, II, and III only
(B) I, III, and IV only
(C) II, III, and IV only
(D) More than one of the above
(E) None of the above

---

**Q49.** The Bank Rate is different from Repo Rate in that:
(A) Bank Rate is for short-term (overnight) borrowing; Repo is for long-term
(B) Bank Rate is for long-term lending by RBI; Repo Rate is for short-term/overnight
(C) Bank Rate is set by commercial banks; Repo Rate is set by RBI
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following statements about Indian banking are CORRECT?
I. RBI is India's central bank, established in 1935.
II. SBI is the largest commercial bank in India.
III. NABARD is a commercial bank that gives personal loans.
IV. Payments banks can issue credit cards and give home loans.

(A) I and II only
(B) I, II, and III only
(C) All four are correct
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|------------|
| 1  | (C) | Boolean algebra was developed by George Boole (1854) |
| 2  | (B) | Identity Law: A·1 = A and A+0 = A (identity elements are 1 for AND, 0 for OR) |
| 3  | (C) | Null Law: A·0 = 0 and A+1 = 1 (dominant elements force the result) |
| 4  | (B) | Idempotent Law: A·A = A and A+A = A |
| 5  | (B) | Complement Law: A·A' = 0 and A+A' = 1 |
| 6  | (C) | De Morgan Theorem 1: (A·B)' = A' + B' (AND → OR of complements) |
| 7  | (B) | De Morgan Theorem 2: (A+B)' = A'·B' (OR → AND of complements) |
| 8  | (C) | (A'+B')': Apply De Morgan to (A'+B') — treat A' as X, B' as Y: (X+Y)' = X'·Y' = (A')'·(B')' = A·B |
| 9  | (C) | (A'·B')': Apply De Morgan to (A'·B'): (X·Y)' = X'+Y' = (A')'+(B')' = A+B |
| 10 | (C) | Absorption Law: A + AB = A |
| 11 | (C) | AB+AB' = A(B+B') = A·1 = A (Distributive + Complement + Identity) |
| 12 | (B) | A+A'B: Apply A+(BC)=(A+B)(A+C): = (A+A')(A+B) = 1·(A+B) = A+B |
| 13 | (C) | (A+B)(A+B'): Apply Distributive in reverse: A+(B·B') = A+0 = A |
| 14 | (C) | Double Complement: (A')' = A (two inversions cancel) |
| 15 | (B) | Boolean has TWO distributive laws (regular algebra has only one) |
| 16 | (B) | SOP = Sum of Products = OR of AND terms |
| 17 | (C) | POS = Product of Sums = AND of OR terms |
| 18 | (B) | AB + A'C + BC is SOP form (OR of AND terms) |
| 19 | (C) | (A+B)(A'+C)(B+C') is POS form (AND of OR terms) |
| 20 | (B) | Minterms → Sum of Minterms (SOM) = canonical SOP form |
| 21 | (B) | Dual: swap AND↔OR and 0↔1; variables remain uncomplemented |
| 22 | (B) | A·1 = A (Identity); B·0 = 0 (Null); A'·A = 0 (Complement). So Y = A + 0 + 0 = A |
| 23 | (C) | (A·B·C)' = A'+B'+C' — De Morgan extends: complement of AND = OR of complements |
| 24 | (B) | A+(B·C)=(A+B)(A+C) is UNIQUE to Boolean — no equivalent in regular arithmetic |
| 25 | (B) | A'B+AB+AB': Group AB+AB'=A(B+B')=A. Then A'B+A=A+A'B=(A+A')(A+B)=A+B |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|------------|
| 26 | (C) | RBI established 1 April 1935 (under RBI Act 1934, during British rule) |
| 27 | (C) | RBI headquarters = Mumbai |
| 28 | (C) | ₹1 note and all coins issued by Ministry of Finance (not RBI) |
| 29 | (B) | Repo Rate = rate at which RBI LENDS to commercial banks |
| 30 | (B) | Reverse Repo Rate = rate at which RBI BORROWS from commercial banks |
| 31 | (C) | Reverse Repo Rate < Repo Rate (always lower) |
| 32 | (B) | CRR = % of deposits maintained as CASH with RBI |
| 33 | (C) | SLR = approved liquid assets: government securities, gold, or vault cash |
| 34 | (C) | CRR ↑ → banks have less to lend → money supply decreases |
| 35 | (C) | To fight inflation: RBI RAISES Repo Rate → credit expensive → demand ↓ |
| 36 | (A) | Lender of Last Resort = provides emergency funds to banks in liquidity crisis |
| 37 | (B) | OMO = buying/selling government securities to control money supply |
| 38 | (B) | RBI SELLS securities → cash moves from banks to RBI → money supply ↓ |
| 39 | (C) | SBI = largest public sector bank in India |
| 40 | (C) | NABARD = apex bank for agriculture and rural development |
| 41 | (B) | Payments banks: accept deposits (up to limit) but CANNOT give loans or credit cards |
| 42 | (C) | CRR cash earns ZERO INTEREST for banks (unlike SLR which earns some return) |
| 43 | (B) | RBI manages foreign exchange reserves and administers FEMA |
| 44 | (C) | MPC sets the Repo Rate (policy rate) — primary tool of monetary policy |
| 45 | (A) | RBI lowers Repo Rate → borrowing cheaper → more credit → demand ↑ → inflation risk ↑ |
| 46 | (C) | RBI nationalized in 1949 (after Independence; established 1935) |
| 47 | (C) | ₹1 note signed by Finance Secretary (Ministry of Finance), not RBI Governor |
| 48 | (B) | I ✅ (Repo = RBI lends), II ✗ (Reverse Repo < Repo, not higher), III ✅ (CRR = 0 interest), IV ✅ (SLR = govt sec/gold) → I, III, IV correct |
| 49 | (B) | Bank Rate = long-term lending rate; Repo Rate = short-term/overnight |
| 50 | (A) | I ✅ (RBI est. 1935), II ✅ (SBI largest), III ✗ (NABARD is development bank, not commercial), IV ✗ (Payments banks CANNOT give loans) → Only I and II correct |

---

# 🔁 DAY 63 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Boolean Algebra

### Laws at a Glance:
```
Identity:     A·1 = A      |   A+0 = A
Null:         A·0 = 0      |   A+1 = 1
Idempotent:   A·A = A      |   A+A = A
Complement:   A·A' = 0     |   A+A' = 1
Double Comp:  (A')' = A
Commutative:  A·B = B·A    |   A+B = B+A
Associative:  (AB)C=A(BC)  |   (A+B)+C=A+(B+C)
Distributive: A(B+C)=AB+AC | A+(BC)=(A+B)(A+C)   ← Boolean has TWO!
Absorption:   A+AB = A     |   A·(A+B) = A
```

### De Morgan's — MASTER THESE:
```
THEOREM 1: (A·B)' = A' + B'   ← Complement of AND = OR of complements
THEOREM 2: (A+B)' = A'·B'     ← Complement of OR  = AND of complements

RULE: "Break the bar, CHANGE THE SIGN"
  Break (complement) → flip AND to OR (or OR to AND)

EXTENDED:
  (A·B·C)' = A'+B'+C'
  (A+B+C)' = A'·B'·C'

MOST COMMON TRAP:
  (A+B)' ≠ A'+B'   ← WRONG!
  (A+B)' = A'·B'   ← CORRECT (sign changes from + to ·)
```

### SOP vs POS:
```
SOP = OR of AND terms  → AB + A'C + BC
POS = AND of OR terms  → (A+B)(A'+C)

SOM = Canonical SOP (uses minterms — rows where output = 1) → Σ notation
POM = Canonical POS (uses maxterms — rows where output = 0) → Π notation
```

### PYQ Trap List — Boolean:
```
✅ (A+B)' = A'·B' NOT A'+B' (sign changes!)
✅ (A·B)' = A'+B' NOT A'·B'
✅ Dual = swap AND↔OR and 0↔1 (DON'T complement variables!)
✅ 1+1 = 1 in Boolean (NOT 2! — Idempotent Law)
✅ A+AB = A (Absorption — A absorbs AB!)
✅ Boolean has TWO distributive laws (regular algebra has one)
✅ Identity: ·1 and +0; Null: ·0 and +1 (don't mix up!)
✅ SOM uses minterms (1-rows); POM uses maxterms (0-rows)
```

---

## ⚡ RAPID FIRE — Banking & Monetary Policy

### RBI Quick Facts:
```
Established:   1 April 1935  |  Nationalized: 1949
HQ:            Mumbai
Issues:        All notes EXCEPT ₹1 note and coins
₹1 note:       Signed by Finance Secretary (not RBI Governor)
Role:          Central Bank + Banker's Bank + Lender of Last Resort
```

### Monetary Policy Tools — Rate Order:
```
Reverse Repo Rate < Repo Rate < Bank Rate   (always this order!)

Repo Rate    = RBI LENDS to banks (banks borrow FROM RBI)
Reverse Repo = RBI BORROWS from banks (banks LEND to RBI)
CRR          = % deposits as CASH with RBI (ZERO interest!)
SLR          = % deposits in G-secs/gold/cash in vaults (earns some interest)
```

### Inflation vs Growth Actions:
```
FIGHT INFLATION → RBI RAISES: Repo Rate ↑, CRR ↑, SLR ↑, OMO sells securities
STIMULATE GROWTH → RBI LOWERS: Repo Rate ↓, CRR ↓, SLR ↓, OMO buys securities
```

### PYQ Trap List — Banking:
```
✅ Repo Rate = RBI LENDS to banks (not borrows!)
✅ Reverse Repo = RBI BORROWS from banks (not lends!)
✅ Reverse Repo < Repo (ALWAYS lower, not higher!)
✅ CRR earns ZERO interest for banks
✅ ₹1 note issued by Finance Ministry (not RBI)
✅ RBI established 1935, nationalized 1949 (not 1947!)
✅ SBI = largest COMMERCIAL bank; RBI = CENTRAL bank (very different!)
✅ NABARD = development bank for agriculture (NOT commercial bank)
✅ Payments banks CANNOT give loans or issue credit cards
✅ OMO SELL = money supply ↓; OMO BUY = money supply ↑
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Boolean Laws Core**: Identity (A·1=A, A+0=A), Null (A·0=0, A+1=1), Idempotent (A·A=A, A+A=A), Complement (A·A'=0, A+A'=1), Absorption (A+AB=A). Boolean has TWO distributive laws (regular algebra has one). In Boolean, 1+1=1 (not 2!).
2. **De Morgan's — Never Confuse**: (A·B)' = A'+B' | (A+B)' = A'·B'. KEY RULE: "Break the bar, CHANGE THE SIGN" — the operation flips (AND→OR or OR→AND). Most common trap: writing (A+B)' = A'+B' is WRONG.
3. **SOP & POS**: SOP = OR of AND terms (AB+A'C); POS = AND of OR terms ((A+B)(A'+C)). SOM = canonical SOP from 1-rows (Σ notation); POM = canonical POS from 0-rows (Π notation).
4. **RBI Core**: Established 1 April 1935, nationalized 1949, HQ Mumbai. Issues all notes EXCEPT ₹1 note and coins. Roles: Banker's Bank, Lender of Last Resort, controls monetary policy using Repo Rate, Reverse Repo, CRR, SLR.
5. **Rates — Never Confuse**: Reverse Repo < Repo < Bank Rate (always!). Repo = RBI LENDS to banks. Reverse Repo = RBI BORROWS from banks. CRR = 0% interest. Fight inflation → RAISE all rates. Stimulate growth → LOWER all rates.

---

## 📅 DAY 64 PREVIEW — What's Coming Next:
**CS**: Digital Electronics — Karnaugh Map (K-Map) Simplification: 2-variable, 3-variable, and 4-variable K-Maps; grouping rules (powers of 2 only); wraparound groups; don't-care conditions; prime implicants and essential prime implicants
**GS**: Indian Economy / History — Green Revolution: M.S. Swaminathan, HYV seeds, achievements (Punjab, Haryana, UP wheat revolution), limitations, second Green Revolution concept

---

*🚀 Day 63 of 170 — Boolean Algebra and De Morgan's Theorem appear in EVERY BPSC TRE paper. The De Morgan sign-change trap and the SOP/POS confusion are the most repeated mistakes. Today's module also deeply covers Banking — one of the highest-scoring GS topics across all three TRE papers. Master both and you've locked in guaranteed marks! 🎯*
