# 📅 BPSC TRE 4.0 — DAY 61 COMPLETE STUDY MODULE
### Digital Electronics: Basic Logic Gates (AND, OR, NOT, XOR, XNOR) + Indian Polity — Fundamental Duties
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Digital Electronics — Logic Gates, Truth Tables, XOR vs XNOR, Truth Table Row Formula
> - Afternoon (1 hr): Polity — Fundamental Duties: Article 51A, All 11 Duties, Key Facts
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Digital Electronics — Basic Logic Gates

---

## 🔷 SECTION 1: What is Digital Electronics?

### Real-Life Analogy — Switches and Light Bulbs:

Imagine a simple light bulb circuit. If the switch is ON → bulb glows (HIGH = 1). If the switch is OFF → bulb doesn't glow (LOW = 0). Now imagine combining TWO switches — if both must be ON for the bulb to glow, that's an AND gate. If EITHER switch can turn it on, that's an OR gate.

Digital electronics deals with circuits that have only TWO states:
- **HIGH / ON / 1 / TRUE**
- **LOW / OFF / 0 / FALSE**

> **A Logic Gate is a basic building block of digital circuits. It takes one or more binary inputs (0 or 1) and produces a single binary output based on a logical rule.**

### Why Logic Gates Matter (BPSC Context):
```
Every digital device — computer, calculator, phone — is built from millions of
tiny logic gates on a chip. Understanding gates means understanding how computers
"think" at the hardware level.

Binary (0 and 1) → Logic Gates → Circuits → Processors → Computers
```

---

## 🔷 SECTION 2: Truth Tables — The Foundation

### What is a Truth Table?

A **Truth Table** lists ALL possible input combinations and their corresponding output.

### How Many Rows? — The Formula:
```
NUMBER OF ROWS IN A TRUTH TABLE = 2ⁿ

Where n = number of INPUT variables

  n = 1 input  →  2¹ = 2 rows
  n = 2 inputs →  2² = 4 rows
  n = 3 inputs →  2³ = 8 rows
  n = 4 inputs →  2⁴ = 16 rows
  n = 8 inputs →  2⁸ = 256 rows

🎯 PYQ FACT: A 2-input gate has 4 rows (2²). A 4-input gate has 16 rows (2⁴).
🚨 TRAP: Students confuse "rows" with "inputs". Rows = 2ⁿ, NOT 2×n.
         For 4 inputs: rows = 2⁴ = 16 (NOT 4×2 = 8!)
```

### Binary Counting Pattern (How to fill rows):
```
For a 3-input truth table (A, B, C):
Count in binary from 000 to 111 — that gives all 8 rows!

A  B  C
─────────
0  0  0   ← Row 1 (Binary: 000 = Decimal 0)
0  0  1   ← Row 2 (Binary: 001 = Decimal 1)
0  1  0   ← Row 3 (Binary: 010 = Decimal 2)
0  1  1   ← Row 4 (Binary: 011 = Decimal 3)
1  0  0   ← Row 5 (Binary: 100 = Decimal 4)
1  0  1   ← Row 6 (Binary: 101 = Decimal 5)
1  1  0   ← Row 7 (Binary: 110 = Decimal 6)
1  1  1   ← Row 8 (Binary: 111 = Decimal 7)
```

---

## 🔷 SECTION 3: AND Gate

### Concept:
```
AND gate = ALL inputs must be HIGH (1) for output to be HIGH (1).
           Even ONE LOW (0) input makes output LOW (0).

Real-life analogy: A car needs BOTH the key AND the brake pressed to start.
                   Both conditions must be true!

Boolean Expression:  Y = A · B   (read as "A AND B")
Also written as:     Y = AB

Symbol: ─┤         ├─
         A ─┐     ┌─ Y
            └─AND─┘
         B ─┘
```

### 2-Input AND Gate Truth Table:
```
┌───┬───┬────────┐
│ A │ B │ Y=A·B  │
├───┼───┼────────┤
│ 0 │ 0 │   0    │  Both LOW  → Output LOW
├───┼───┼────────┤
│ 0 │ 1 │   0    │  One LOW   → Output LOW
├───┼───┼────────┤
│ 1 │ 0 │   0    │  One LOW   → Output LOW
├───┼───┼────────┤
│ 1 │ 1 │   1    │  Both HIGH → Output HIGH ✅
└───┴───┴────────┘

KEY INSIGHT: Output is 1 ONLY when ALL inputs are 1.
             Output is 0 if ANY input is 0.
```

### 3-Input AND Gate:
```
Y = A · B · C
Output is HIGH only when A=1, B=1, C=1 (all three HIGH).
Total rows = 2³ = 8. Only ONE row gives output = 1.
```

### 🎯 PYQ FACTS — AND Gate:
```
✅ AND gate: Output HIGH only when ALL inputs HIGH
✅ Boolean expression: Y = A·B or Y = AB
✅ AND gate output = 1 only for input combination (1,1) in 2-input case
✅ 3-input AND: output = 1 only for (1,1,1)
```

---

## 🔷 SECTION 4: OR Gate

### Concept:
```
OR gate = Output is HIGH (1) when ANY input is HIGH (1).
          Output is LOW (0) ONLY when ALL inputs are LOW (0).

Real-life analogy: A door can be opened by EITHER a key card OR a PIN.
                   Either condition being true is enough!

Boolean Expression:  Y = A + B   (read as "A OR B")

Symbol: ─┤        ├─
         A ─┐    ┌─ Y
            └─OR─┘
         B ─┘
```

### 2-Input OR Gate Truth Table:
```
┌───┬───┬────────┐
│ A │ B │ Y=A+B  │
├───┼───┼────────┤
│ 0 │ 0 │   0    │  Both LOW  → Output LOW ❌ (only case!)
├───┼───┼────────┤
│ 0 │ 1 │   1    │  One HIGH  → Output HIGH ✅
├───┼───┼────────┤
│ 1 │ 0 │   1    │  One HIGH  → Output HIGH ✅
├───┼───┼────────┤
│ 1 │ 1 │   1    │  Both HIGH → Output HIGH ✅
└───┴───┴────────┘

KEY INSIGHT: Output is 0 ONLY when ALL inputs are 0.
             Output is 1 if ANY input is 1.
```

### 4-Input OR Gate:
```
Y = A + B + C + D
Total rows = 2⁴ = 16 rows.
Output = 0 ONLY for one row: (0,0,0,0). All other 15 rows give output = 1.

🎯 PYQ FACT: A 4-input OR gate truth table has 16 rows (2⁴ = 16).
```

### AND vs OR — Quick Comparison:
```
┌─────────────────────────────────────────────────────┐
│ AND Gate:   Output = 1 ONLY when ALL inputs = 1     │
│ OR  Gate:   Output = 0 ONLY when ALL inputs = 0     │
│                                                      │
│ Think of it:                                         │
│   AND = Strict (everyone must agree)                │
│   OR  = Lenient (anyone agreeing is enough)         │
└─────────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 5: NOT Gate (Inverter)

### Concept:
```
NOT gate = Flips / Inverts the input.
           HIGH → LOW, LOW → HIGH.
           Only ONE input, ONE output.

Real-life analogy: A photo negative — what's dark becomes light, what's light becomes dark!
                   A toggle switch — press to INVERT current state.

Boolean Expression: Y = A'   (read as "NOT A" or "A complement")
Also written as:    Y = Ā   (A with a bar on top)

Symbol: A ──○── Y   (the small circle = inversion)
```

### NOT Gate Truth Table:
```
┌───┬────────┐
│ A │  Y=A'  │
├───┼────────┤
│ 0 │   1    │  LOW  → HIGH (inverted!)
├───┼────────┤
│ 1 │   0    │  HIGH → LOW  (inverted!)
└───┴────────┘

Only 2 rows (n=1 input, 2¹ = 2 rows).
```

### 🎯 PYQ FACTS — NOT Gate:
```
✅ NOT gate = Inverter (only gate with one input)
✅ NOT gate output = complement of input
✅ Double NOT = original value: (A')' = A
✅ Symbol has a bubble/circle at output — that circle means INVERSION
```

---

## 🔷 SECTION 6: XOR Gate (Exclusive OR) ⭐ HIGH PRIORITY

### Concept — The "DIFFERENT" Gate:
```
XOR gate = Output is HIGH (1) when inputs are DIFFERENT.
           Output is LOW (0) when inputs are SAME.

"EX-OR" stands for EXCLUSIVE OR.

Real-life analogy: A toggle light switch with two switches (like in a staircase).
                   The light changes state only when ONE switch is operated, NOT both.
                   If BOTH switch ON or BOTH switch OFF — light doesn't change.
                   Only DIFFERENT states cause a change!

Boolean Expression: Y = A ⊕ B   (⊕ is the XOR symbol)
Also written as:    Y = A'B + AB'  (expanded form — useful for proofs)
```

### 2-Input XOR Gate Truth Table:
```
┌───┬───┬──────────┐
│ A │ B │  Y=A⊕B   │
├───┼───┼──────────┤
│ 0 │ 0 │    0     │  SAME inputs    → Output LOW  ❌
├───┼───┼──────────┤
│ 0 │ 1 │    1     │  DIFFERENT      → Output HIGH ✅
├───┼───┼──────────┤
│ 1 │ 0 │    1     │  DIFFERENT      → Output HIGH ✅
├───┼───┼──────────┤
│ 1 │ 1 │    0     │  SAME inputs    → Output LOW  ❌
└───┴───┴──────────┘

🧠 MEMORY TRICK: XOR = eXclusive = "eXtra special OR"
   Regular OR: 1+1 = 1 (output HIGH for same inputs)
   XOR:        1⊕1 = 0 (output LOW for same inputs — it's EXCLUSIVE!)
```

### XOR Properties (Very Useful for MCQs):
```
A ⊕ 0 = A          (XOR with 0 = no change)
A ⊕ 1 = A'         (XOR with 1 = inverts, like NOT gate!)
A ⊕ A = 0          (XOR with itself = always 0)
A ⊕ A' = 1         (XOR with complement = always 1)
A ⊕ B = B ⊕ A      (commutative)

🎯 PYQ FACT: XOR of a number with itself = 0. Very commonly tested!
🎯 PYQ FACT: XOR with 1 acts like NOT gate.
```

### XOR Application — Parity Checker:
```
XOR is used in PARITY CHECKING (error detection in data transmission).
Even parity bit: XOR of all data bits gives parity bit.
This is a very common exam application of XOR!
```

---

## 🔷 SECTION 7: XNOR Gate (Exclusive NOR) ⭐ HIGH PRIORITY

### Concept — The "SAME" Gate:
```
XNOR gate = Output is HIGH (1) when inputs are SAME.
            Output is LOW (0) when inputs are DIFFERENT.

XNOR = NOT (XOR) — the exact complement/inverse of XOR!

Real-life analogy: An "agreement detector" — outputs HIGH when both people
                   AGREE (both say YES or both say NO).

Boolean Expression: Y = A ⊙ B   (⊙ is the XNOR symbol)
Also written as:    Y = (A⊕B)'  = AB + A'B'  (expanded form)
```

### 2-Input XNOR Gate Truth Table:
```
┌───┬───┬──────────┐
│ A │ B │  Y=A⊙B   │
├───┼───┼──────────┤
│ 0 │ 0 │    1     │  SAME inputs    → Output HIGH ✅
├───┼───┼──────────┤
│ 0 │ 1 │    0     │  DIFFERENT      → Output LOW  ❌
├───┼───┼──────────┤
│ 1 │ 0 │    0     │  DIFFERENT      → Output LOW  ❌
├───┼───┼──────────┤
│ 1 │ 1 │    1     │  SAME inputs    → Output HIGH ✅
└───┴───┴──────────┘

🧠 MEMORY TRICK: XNOR = "Equals detector"
   Output = 1 means "A EQUALS B"
   That's why XNOR is also called an EQUALITY GATE!
```

### XNOR Properties:
```
A ⊙ 0 = A'    (XNOR with 0 = inverts)
A ⊙ 1 = A     (XNOR with 1 = no change)
A ⊙ A = 1     (XNOR with itself = always 1)
A ⊙ A' = 0    (XNOR with complement = always 0)
```

---

## 🔷 SECTION 8: XOR vs XNOR — The Most-Tested Comparison ⭐

```
┌──────────────────────────────────────────────────────────────────────┐
│                  XOR vs XNOR — MASTER TABLE                          │
├──────────────────┬───────────────────┬───────────────────────────────┤
│    FEATURE       │      XOR (⊕)      │          XNOR (⊙)             │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Full Name        │ Exclusive OR      │ Exclusive NOR                 │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Output HIGH when │ Inputs DIFFERENT  │ Inputs SAME                   │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Output LOW when  │ Inputs SAME       │ Inputs DIFFERENT              │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Also called      │ "Difference gate" │ "Equality gate"               │
│                  │ Odd-parity gate   │ Even-parity gate              │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Truth table      │ (0,0)→0           │ (0,0)→1                       │
│ highlights       │ (0,1)→1           │ (0,1)→0                       │
│                  │ (1,0)→1           │ (1,0)→0                       │
│                  │ (1,1)→0           │ (1,1)→1                       │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Boolean symbol   │ A ⊕ B             │ A ⊙ B = (A⊕B)'               │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ Relation         │ They are COMPLEMENTS of each other!               │
│                  │ XNOR output = NOT (XOR output)                    │
├──────────────────┼───────────────────┼───────────────────────────────┤
│ PYQ Direction    │ Tests: "When is XOR output HIGH?" → DIFFERENT     │
│                  │ Tests: "When is XNOR output HIGH?" → SAME         │
└──────────────────┴───────────────────┴───────────────────────────────┘

🚨 TRAP: Students mix up XOR and XNOR!
   XOR HIGH → DIFFERENT inputs  (X = eXclusive — only one can be 1)
   XNOR HIGH → SAME inputs      (N = NOT XOR, so opposite!)

🧠 TRICK TO REMEMBER:
   XOR → Think "X marks the spot" → CROSS (different = crossed states)
   XNOR → N = NORMAL agreement → SAME (both agree)
```

---

## 🔷 SECTION 9: Complete Truth Table — All 5 Gates Together

```
2-Input Truth Table for ALL Gates:

┌───┬───┬─────────┬────────┬────────┬──────────┬──────────┐
│ A │ B │ AND(A·B)│ OR(A+B)│ NOT(A')│  XOR(A⊕B)│ XNOR(A⊙B)│
├───┼───┼─────────┼────────┼────────┼──────────┼──────────┤
│ 0 │ 0 │    0    │   0    │   1    │     0    │    1     │
├───┼───┼─────────┼────────┼────────┼──────────┼──────────┤
│ 0 │ 1 │    0    │   1    │   1    │     1    │    0     │
├───┼───┼─────────┼────────┼────────┼──────────┼──────────┤
│ 1 │ 0 │    0    │   1    │   0    │     1    │    0     │
├───┼───┼─────────┼────────┼────────┼──────────┼──────────┤
│ 1 │ 1 │    1    │   1    │   0    │     0    │    1     │
└───┴───┴─────────┴────────┴────────┴──────────┴──────────┘

NOTE: NOT gate column shows NOT(A) only — it doesn't use B input.

PATTERN OBSERVATIONS:
  AND:  Only last row is 1 (needs ALL inputs HIGH)
  OR:   Only first row is 0 (needs ALL inputs LOW to output 0)
  NOT:  Simply flips A
  XOR:  Middle two rows are 1 (DIFFERENT inputs → HIGH)
  XNOR: First and last rows are 1 (SAME inputs → HIGH)
        XNOR is the EXACT COMPLEMENT of XOR (column is flipped!)
```

---

## 🔷 SECTION 10: Gate Symbols & Boolean Summary

```
┌────────────┬──────────────────────┬───────────────┬────────────────────────┐
│    GATE    │    BOOLEAN EXPR      │   MNEMONIC    │   OUTPUT = 1 WHEN      │
├────────────┼──────────────────────┼───────────────┼────────────────────────┤
│ AND        │  Y = A · B           │ ALL must be 1 │ ALL inputs = 1         │
├────────────┼──────────────────────┼───────────────┼────────────────────────┤
│ OR         │  Y = A + B           │ ANY can be 1  │ ANY input = 1          │
├────────────┼──────────────────────┼───────────────┼────────────────────────┤
│ NOT        │  Y = A'              │ Flip it!      │ Input = 0              │
├────────────┼──────────────────────┼───────────────┼────────────────────────┤
│ XOR        │  Y = A ⊕ B           │ DIFFERENT → 1 │ Inputs are DIFFERENT   │
├────────────┼──────────────────────┼───────────────┼────────────────────────┤
│ XNOR       │  Y = A ⊙ B = (A⊕B)' │ SAME → 1      │ Inputs are SAME        │
└────────────┴──────────────────────┴───────────────┴────────────────────────┘
```

---

## 🔷 SECTION 11: Truth Table Row Count — Quick Practice

```
PRACTICE: Calculate rows for these gates:

Q: How many rows in a 2-input AND gate truth table?
A: 2² = 4 rows ✅

Q: How many rows in a 4-input OR gate truth table?
A: 2⁴ = 16 rows ✅

Q: How many rows in a 3-input XOR gate truth table?
A: 2³ = 8 rows ✅

Q: How many rows for an 8-input gate?
A: 2⁸ = 256 rows ✅

Q: A gate has 16 rows in its truth table. How many inputs does it have?
A: 2ⁿ = 16 → n = 4 inputs ✅

🎯 PYQ FACT: Rows = 2ⁿ (where n = number of inputs). Always.
🚨 TRAP: "A 4-input gate has 8 rows" → FALSE! 2⁴ = 16, NOT 4×2 = 8.
```

---

## 🔷 SECTION 12: PYQ Traps — Logic Gates

```
🚨 TRAP 1: "XOR output is HIGH when inputs are SAME" → FALSE!
   XOR = HIGH when inputs are DIFFERENT.
   XNOR = HIGH when inputs are SAME.

🚨 TRAP 2: "XNOR is completely different from XOR" → FALSE!
   XNOR = NOT (XOR). They are complements. Same circuit with an inverter added!

🚨 TRAP 3: "AND gate output is 1 when ANY input is 1" → FALSE!
   AND requires ALL inputs to be 1.
   OR gate is the one that outputs 1 when ANY input is 1.

🚨 TRAP 4: "OR gate output is 0 when ANY input is 0" → FALSE!
   OR output is 0 ONLY when ALL inputs are 0.
   AND gate output is 0 when ANY input is 0.

🚨 TRAP 5: "NOT gate has 2 inputs" → FALSE!
   NOT gate has exactly 1 input and 1 output. It's a unary gate.

🚨 TRAP 6: "Truth table for 4-input gate has 8 rows" → FALSE!
   4 inputs → 2⁴ = 16 rows. Remember: EXPONENTIAL, not multiplicative!

🚨 TRAP 7: "XOR of 1 ⊕ 1 = 1" → FALSE!
   1 ⊕ 1 = 0 (same inputs → XOR output = 0).
   1 + 1 = 1 (OR gate), but XOR is different!

🚨 TRAP 8: "AND gate and multiplication are unrelated" → FALSE!
   AND gate is the DIGITAL equivalent of binary multiplication!
   0·0=0, 0·1=0, 1·0=0, 1·1=1 — exactly the AND truth table.

🚨 TRAP 9: "OR gate is the same as addition in binary" → PARTIALLY TRUE but TRAP!
   For OR: 1+1=1 (not 2!). In regular addition 1+1=2, but in OR logic 1+1=1.
   Don't confuse Boolean OR with arithmetic addition for (1,1) case.

🚨 TRAP 10: "XNOR gate is called difference gate" → FALSE!
   XOR is called difference gate (detects difference).
   XNOR is called equality gate (detects equality/sameness).
```

---

# PART 2: GENERAL STUDIES
## 🏛️ Indian Polity — Fundamental Duties

---

## 🔷 SECTION 1: Overview — What are Fundamental Duties?

### Real-Life Analogy — Rights and Responsibilities:

If a citizen has the RIGHT to use a public park (a Fundamental Right), they also have the RESPONSIBILITY not to litter or damage the park. Rights and duties go hand-in-hand. You cannot enjoy rights while ignoring duties.

> **Fundamental Duties are a set of moral and civic obligations of every citizen of India, listed in the Constitution to remind citizens that rights come with corresponding responsibilities.**

### Constitutional Background:
```
PART:           Part IV-A of the Indian Constitution
ARTICLE:        Article 51A
ORIGINALLY:     Not in the original Constitution of 1950!
ADDED BY:       42nd Constitutional Amendment Act, 1976
                (During Emergency period, PM Indira Gandhi)
INSPIRED BY:    Constitution of the USSR (Soviet Union) — first country
                to include such duties in its Constitution
ORIGINALLY:     10 Fundamental Duties added in 1976
ADDED 11th:     86th Constitutional Amendment Act, 2002
                (Added duty related to education for children)
TOTAL NOW:      11 Fundamental Duties (under Article 51A)
```

### Why Were They Added?
```
BEFORE 1976: Constitution had only Fundamental Rights (Part III) and
             Directive Principles (Part IV) — NO Duties section!

POST-EMERGENCY 1976: Government felt citizens were enjoying rights
                     without fulfilling civic responsibilities.
                     Swaran Singh Committee recommended adding duties.

PURPOSE:
  → To remind citizens that rights come with responsibilities
  → To promote national integration and patriotism
  → To create a sense of civic consciousness
```

---

## 🔷 SECTION 2: All 11 Fundamental Duties — Complete List (Article 51A)

```
ARTICLE 51A: It shall be the duty of every citizen of India —

DUTY 1 [51A(a)] — ABIDE BY THE CONSTITUTION & RESPECT NATIONAL SYMBOLS:
  To abide by the Constitution and respect its ideals and institutions,
  the National Flag and the National Anthem.

DUTY 2 [51A(b)] — CHERISH FREEDOM MOVEMENT IDEALS:
  To cherish and follow the noble ideals which inspired our national struggle
  for freedom.
  (Example: Gandhi's values of non-violence, truth, secularism)

DUTY 3 [51A(c)] — UPHOLD SOVEREIGNTY & INTEGRITY:
  To uphold and protect the sovereignty, unity and integrity of India.
  (Key words: sovereignty, unity, integrity — all three!)

DUTY 4 [51A(d)] — DEFEND THE COUNTRY:
  To defend the country and render national service when called upon to do so.
  (Military service if the country needs you)

DUTY 5 [51A(e)] — PROMOTE HARMONY & BROTHERHOOD:
  To promote harmony and the spirit of common brotherhood amongst all the
  people of India transcending religious, linguistic and regional diversities;
  to renounce practices derogatory to the dignity of women.
  (Two parts: brotherhood + renounce anti-women practices)

DUTY 6 [51A(f)] — PRESERVE COMPOSITE CULTURE:
  To value and preserve the rich heritage of our composite culture.
  (Protect India's diverse art, music, history, literature, culture)

DUTY 7 [51A(g)] — PROTECT NATURAL ENVIRONMENT: ⭐ FREQUENTLY TESTED
  To protect and improve the natural environment including forests, lakes,
  rivers and wildlife, and to have compassion for living creatures.
  (Environment + compassion for animals — both included!)

DUTY 8 [51A(h)] — DEVELOP SCIENTIFIC TEMPER:
  To develop the scientific temper, humanism and the spirit of inquiry
  and reform.
  (Scientific thinking + humanism + reform — all three!)

DUTY 9 [51A(i)] — SAFEGUARD PUBLIC PROPERTY:
  To safeguard public property and to abjure violence.
  (Don't damage public property + be non-violent)

DUTY 10 [51A(j)] — STRIVE FOR EXCELLENCE:
  To strive towards excellence in all spheres of individual and collective
  activity so that the nation constantly rises to higher levels of endeavour
  and achievement.
  (Give your best in all you do — for national progress)

DUTY 11 [51A(k)] — PROVIDE EDUCATION TO CHILDREN: ⭐ IMPORTANT (Added 2002)
  Who is a parent or guardian, to provide opportunities for education to his
  child or, as the case may be, ward between the age of 6 and 14 years.
  (11th duty — added by 86th Amendment 2002; education for 6-14 age group)
```

---

## 🔷 SECTION 3: Key Features of Fundamental Duties

### Are Fundamental Duties Enforceable?
```
NON-JUSTICIABLE — Fundamental Duties are NOT legally enforceable in courts.
                   Unlike Fundamental Rights, you CANNOT file a court case
                   if a person fails to perform their Fundamental Duty.

HOWEVER — Parliament CAN make laws to enforce them indirectly.
Example: Environmental Protection Act enforces Duty 7 (protect environment)
         Prevention of Insults to National Honour Act enforces Duty 1

CONTRAST:
  Fundamental Rights → JUSTICIABLE (courts can enforce them)
  Fundamental Duties → NON-JUSTICIABLE (courts cannot directly enforce)
  Directive Principles → NON-JUSTICIABLE (like Duties)

🎯 PYQ FACT: Fundamental Duties = non-justiciable (cannot be enforced in court directly)
```

### Who must perform Fundamental Duties?
```
ONLY CITIZENS of India (NOT foreigners / non-citizens).

CONTRAST: Fundamental Rights are available to BOTH citizens AND foreigners
          (with some exceptions — like Right to Vote, only for citizens).

🎯 PYQ FACT: Fundamental Duties apply ONLY to CITIZENS (not foreigners).
🚨 TRAP: "Fundamental Duties apply to all persons in India" → FALSE!
         Only CITIZENS. Foreigners are NOT bound by Fundamental Duties.
```

---

## 🔷 SECTION 4: Important Numbers & Amendments

```
┌─────────────────────────────────────────────────────────────────────┐
│                FUNDAMENTAL DUTIES — KEY NUMBERS                     │
├─────────────────────────────────────────────────────────────────────┤
│ Part of Constitution    │  Part IV-A                               │
│ Article Number          │  Article 51A                             │
│ Originally Added by     │  42nd Amendment Act, 1976               │
│ Original Number         │  10 Fundamental Duties                  │
│ 11th Duty Added by      │  86th Amendment Act, 2002               │
│ Total Now               │  11 Fundamental Duties                  │
│ Based on recommendations│  Swaran Singh Committee (1976)          │
│ Inspired by             │  Constitution of USSR                   │
│ Applicable to           │  Citizens ONLY (not foreigners)         │
│ Justiciability          │  NON-justiciable (not directly in courts)│
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 5: Swaran Singh Committee

```
The 42nd Amendment added Fundamental Duties based on the recommendations of
the SWARAN SINGH COMMITTEE (1976).

WHAT IT RECOMMENDED:
  → Add Fundamental Duties to the Constitution
  → 8 Duties were recommended; the government added 10
  → Also recommended that Parliament should be empowered to impose penalties
    for violation of duties (this part was NOT included in the Constitution!)

🎯 PYQ FACT: Swaran Singh Committee recommended Fundamental Duties.
```

---

## 🔷 SECTION 6: Fundamental Duties vs Fundamental Rights vs DPSPs

```
┌─────────────────────┬──────────────────────┬──────────────────────┬───────────────────────┐
│      FEATURE        │  FUNDAMENTAL RIGHTS  │ FUNDAMENTAL DUTIES   │       DPSPs           │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Part                │ Part III             │ Part IV-A            │ Part IV               │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Articles            │ Articles 12–35       │ Article 51A          │ Articles 36–51        │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Justiciable?        │ YES — enforceable    │ NO — not directly    │ NO — not directly     │
│                     │ in courts            │ enforceable          │ enforceable           │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Applicable to       │ Citizens + some      │ CITIZENS ONLY        │ State (government     │
│                     │ foreigners           │                      │ must follow)          │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Added               │ Original 1950        │ 42nd Amdt 1976       │ Original 1950         │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Inspired by         │ US Bill of Rights    │ USSR Constitution    │ Irish Constitution    │
├─────────────────────┼──────────────────────┼──────────────────────┼───────────────────────┤
│ Nature              │ Rights of citizens   │ Duties of citizens   │ Directions to state   │
└─────────────────────┴──────────────────────┴──────────────────────┴───────────────────────┘
```

---

## 🔷 SECTION 7: Most Important Duties for PYQ (Frequently Tested)

```
DUTY 7 (Environment): ⭐ MOST TESTED
  "protect and improve natural environment including forests, lakes,
  rivers and wildlife AND have compassion for living creatures"
  → Two parts: protect environment + compassion for creatures
  → Environmental laws are based on this duty

DUTY 1 (National Symbols): ⭐ FREQUENTLY TESTED
  Respect Constitution, National Flag, National Anthem.
  → Prevention of Insults to National Honour Act (1971) is related.

DUTY 11 (Children's Education): ⭐ KEY — ADDED LAST
  → Added by 86th Amendment 2002
  → Right to Education (RTE Act 2009) enforces this duty
  → Age group: 6 to 14 years
  → This is the ONLY duty that was NOT part of the original 10 (1976)

DUTY 8 (Scientific Temper): ⭐ TRICKY
  Three elements: scientific temper + humanism + spirit of inquiry and reform
  → Often tested as: "Which duty mentions 'humanism'?" → Duty 8 (51A-h)

DUTY 5 (Harmony + Women's Dignity): ⭐ TWO PARTS — TRAP ALERT
  Two parts in ONE duty:
  Part 1: Promote harmony and brotherhood
  Part 2: Renounce practices derogatory to dignity of women
  → Both are in the SAME article 51A(e)!
```

---

## 🔷 SECTION 8: PYQ Traps — Fundamental Duties

```
🚨 TRAP 1: "Fundamental Duties were in the original Constitution (1950)" → FALSE!
   Fundamental Duties were added by 42nd Amendment Act, 1976.
   Original Constitution had NO Fundamental Duties.

🚨 TRAP 2: "There are 10 Fundamental Duties" → FALSE (Now)!
   ORIGINALLY: 10 Duties (added 1976)
   CURRENTLY: 11 Duties (11th added by 86th Amendment 2002)
   ANSWER: 11 Fundamental Duties.

🚨 TRAP 3: "Fundamental Duties are justiciable" → FALSE!
   Non-justiciable. Courts cannot directly enforce them.
   (Unlike Fundamental Rights which ARE justiciable.)

🚨 TRAP 4: "Fundamental Duties apply to all persons including foreigners" → FALSE!
   Only CITIZENS of India. Not foreigners.

🚨 TRAP 5: "Fundamental Duties are in Part IV of the Constitution" → FALSE!
   DPSPs are in Part IV (Articles 36–51).
   Fundamental Duties are in Part IV-A (Article 51A).

🚨 TRAP 6: "The 11th Fundamental Duty was added by 44th Amendment" → FALSE!
   11th Duty added by 86th Constitutional Amendment Act, 2002.

🚨 TRAP 7: "The Swaran Singh Committee recommended 10 Fundamental Duties" → FALSE!
   Swaran Singh Committee recommended 8 duties.
   The government ultimately included 10 (not 8).

🚨 TRAP 8: "Duty to protect environment is about forests and rivers only" → FALSE!
   Duty 7 covers: forests, lakes, rivers AND wildlife AND compassion for living creatures.
   All these are part of ONE duty (Article 51A-g).

🚨 TRAP 9: "Fundamental Duties were inspired by the US Constitution" → FALSE!
   Inspired by the USSR (Soviet) Constitution.
   Fundamental Rights were inspired by the US Constitution.

🚨 TRAP 10: "The 11th duty relates to voting in elections" → FALSE!
   11th duty (86th Amendment) = parent/guardian must provide education
   to child between 6 and 14 years of age.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Basic Logic Gates — AND, OR, NOT, XOR, XNOR, Truth Tables

---

**Q1.** An AND gate produces a HIGH output (1) when:
(A) Any one of the inputs is HIGH
(B) All inputs are LOW
(C) All inputs are HIGH
(D) More than one of the above
(E) None of the above

---

**Q2.** An OR gate produces a LOW output (0) when:
(A) Any one input is LOW
(B) All inputs are HIGH
(C) All inputs are LOW
(D) More than one of the above
(E) None of the above

---

**Q3.** A NOT gate is also called:
(A) A universal gate
(B) An inverter
(C) A buffer gate
(D) More than one of the above
(E) None of the above

---

**Q4.** The XOR gate produces HIGH output (1) when:
(A) Both inputs are HIGH (1,1)
(B) Both inputs are LOW (0,0)
(C) The inputs are DIFFERENT (one HIGH, one LOW)
(D) More than one of the above
(E) None of the above

---

**Q5.** The XNOR gate is also called:
(A) Exclusive OR gate
(B) Difference gate
(C) Equality gate
(D) More than one of the above
(E) None of the above

---

**Q6.** For a 2-input XOR gate, what is the output when both inputs are 1?
(A) 1
(B) 0
(C) Depends on the circuit
(D) More than one of the above
(E) None of the above

---

**Q7.** For a 2-input XNOR gate, what is the output when both inputs are 1?
(A) 0
(B) 1
(C) Depends on the input voltage
(D) More than one of the above
(E) None of the above

---

**Q8.** A 4-input AND gate truth table will have how many rows?
(A) 4
(B) 8
(C) 16
(D) More than one of the above
(E) None of the above

---

**Q9.** A 3-input OR gate truth table has how many rows where the output is 0?
(A) 1 (only when all inputs are 0)
(B) 3 (one for each input being 0)
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q10.** Which Boolean expression correctly represents the XOR operation?
(A) Y = A · B
(B) Y = A + B
(C) Y = A ⊕ B
(D) More than one of the above
(E) None of the above

---

**Q11.** The Boolean expression for a 2-input AND gate is:
(A) Y = A + B
(B) Y = A ⊕ B
(C) Y = A · B
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the output of the following Boolean expression when A = 1, B = 0?
Y = A ⊕ B
(A) 0
(B) 1
(C) Undefined
(D) More than one of the above
(E) None of the above

---

**Q13.** What is the output of Y = A ⊙ B when A = 0, B = 1?
(A) 1
(B) 0
(C) Same as XOR output for these inputs
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following gates has only ONE input?
(A) AND gate
(B) XOR gate
(C) NOT gate
(D) More than one of the above
(E) None of the above

---

**Q15.** Consider A ⊕ A = ?
(A) 1
(B) A
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q16.** Consider A ⊙ A = ?
(A) 0
(B) A
(C) 1
(D) More than one of the above
(E) None of the above

---

**Q17.** Which gate is commonly used for PARITY CHECKING in data communication?
(A) AND gate
(B) XNOR gate
(C) XOR gate
(D) More than one of the above
(E) None of the above

---

**Q18.** An 8-input gate has a truth table with how many rows?
(A) 16
(B) 64
(C) 256
(D) More than one of the above
(E) None of the above

---

**Q19.** The output of a NOT gate when input A = 0 is:
(A) 0
(B) 1
(C) Undefined
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following correctly describes the relationship between XOR and XNOR?
(A) XNOR is the complement (NOT) of XOR
(B) XOR and XNOR have exactly opposite truth tables
(C) XNOR = NOT(XOR)
(D) More than one of the above
(E) None of the above

---

**Q21.** For inputs A = 1, B = 1, which gates produce output = 1?
(A) AND and OR only
(B) AND, OR, and XNOR
(C) XOR and XNOR
(D) More than one of the above
(E) None of the above

---

**Q22.** For inputs A = 0, B = 0, which gates produce output = 1?
(A) AND and OR
(B) XOR and XNOR
(C) XNOR only
(D) More than one of the above
(E) None of the above

---

**Q23.** The Boolean expression A ⊕ 1 equals:
(A) A (no change)
(B) A' (complement of A)
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following is TRUE about AND gate and binary multiplication?
(A) AND gate has nothing to do with binary multiplication
(B) AND gate is the digital equivalent of binary multiplication (0·0=0, 0·1=0, 1·1=1)
(C) AND gate is equivalent to binary addition
(D) More than one of the above
(E) None of the above

---

**Q25.** A truth table for a logic gate has 32 rows. How many input variables does this gate have?
(A) 4 inputs
(B) 6 inputs
(C) 5 inputs
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Fundamental Duties — Article 51A, All 11 Duties, Key Facts

---

**Q26.** Fundamental Duties are listed in which Part of the Indian Constitution?
(A) Part III
(B) Part IV
(C) Part IV-A
(D) More than one of the above
(E) None of the above

---

**Q27.** Fundamental Duties of Indian citizens are covered under which Article?
(A) Article 48A
(B) Article 50
(C) Article 51A
(D) More than one of the above
(E) None of the above

---

**Q28.** Fundamental Duties were added to the Constitution by which Amendment?
(A) 44th Constitutional Amendment Act, 1978
(B) 42nd Constitutional Amendment Act, 1976
(C) 86th Constitutional Amendment Act, 2002
(D) More than one of the above
(E) None of the above

---

**Q29.** How many Fundamental Duties does the Indian Constitution currently have?
(A) 8
(B) 10
(C) 11
(D) More than one of the above
(E) None of the above

---

**Q30.** The 11th Fundamental Duty (relating to education of children) was added by:
(A) 42nd Amendment Act, 1976
(B) 44th Amendment Act, 1978
(C) 86th Amendment Act, 2002
(D) More than one of the above
(E) None of the above

---

**Q31.** Fundamental Duties in the Indian Constitution were inspired by the Constitution of:
(A) USA (United States of America)
(B) Ireland
(C) USSR (Soviet Union)
(D) More than one of the above
(E) None of the above

---

**Q32.** Which committee recommended the inclusion of Fundamental Duties in the Constitution?
(A) Mandal Commission
(B) Swaran Singh Committee
(C) Sarkaria Commission
(D) More than one of the above
(E) None of the above

---

**Q33.** Are Fundamental Duties justiciable (directly enforceable by courts)?
(A) Yes, courts can enforce them like Fundamental Rights
(B) No, they are non-justiciable
(C) Only duty to protect the environment is justiciable
(D) More than one of the above
(E) None of the above

---

**Q34.** Fundamental Duties under Article 51A are applicable to:
(A) All persons within the territory of India including foreigners
(B) Only government officials and public servants
(C) Only citizens of India
(D) More than one of the above
(E) None of the above

---

**Q35.** Which Fundamental Duty specifically mentions "to have compassion for living creatures"?
(A) Duty to promote harmony and brotherhood [51A(e)]
(B) Duty to protect and improve the natural environment [51A(g)]
(C) Duty to develop scientific temper [51A(h)]
(D) More than one of the above
(E) None of the above

---

**Q36.** Which Fundamental Duty mentions "humanism and the spirit of inquiry and reform"?
(A) Duty to value composite culture [51A(f)]
(B) Duty to defend the country [51A(d)]
(C) Duty to develop scientific temper [51A(h)]
(D) More than one of the above
(E) None of the above

---

**Q37.** The Fundamental Duty to "renounce practices derogatory to the dignity of women" is part of which duty?
(A) Duty to safeguard public property [51A(i)]
(B) Duty to promote harmony and spirit of common brotherhood [51A(e)]
(C) Duty to value and preserve composite culture [51A(f)]
(D) More than one of the above
(E) None of the above

---

**Q38.** The 11th Fundamental Duty (added 2002) requires parents/guardians to provide education to children between the ages of:
(A) 5 to 12 years
(B) 6 to 14 years
(C) 5 to 14 years
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following is a Fundamental Duty under Article 51A?
(A) To pay taxes regularly to the government
(B) To uphold and protect the sovereignty, unity and integrity of India
(C) To vote in every general election
(D) More than one of the above
(E) None of the above

---

**Q40.** Fundamental Duties were originally inserted in the Constitution on the recommendation of which panel?
(A) Rajmannar Committee
(B) Swaran Singh Committee
(C) Balwant Rai Mehta Committee
(D) More than one of the above
(E) None of the above

---

**Q41.** Consider the following statements about Fundamental Duties:
I. Fundamental Duties are justiciable like Fundamental Rights.
II. They apply only to citizens of India, not to foreigners.
III. They were originally a part of the Constitution when it came into force in 1950.
IV. There are currently 11 Fundamental Duties.

Which statements are CORRECT?
(A) I and III only
(B) II and IV only
(C) I, II, and IV only
(D) More than one of the above
(E) None of the above

---

**Q42.** The Fundamental Duty to "abide by the Constitution and respect the National Flag and National Anthem" is under:
(A) Article 51A(b)
(B) Article 51A(a)
(C) Article 51A(c)
(D) More than one of the above
(E) None of the above

---

**Q43.** Which Fundamental Duty requires citizens to "cherish and follow noble ideals of the national struggle for freedom"?
(A) Article 51A(a)
(B) Article 51A(b)
(C) Article 51A(d)
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following is NOT a Fundamental Duty under the Indian Constitution?
(A) To protect and improve the natural environment
(B) To develop scientific temper and humanism
(C) To file income tax returns honestly every year
(D) More than one of the above
(E) None of the above

---

**Q45.** The Directive Principles of State Policy (Part IV) and Fundamental Duties (Part IV-A) are both:
(A) Justiciable — courts can enforce them directly
(B) Non-justiciable — courts cannot directly enforce them
(C) Applicable to foreigners in India
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following correctly identifies the Articles for these Constitutional provisions?
I.   Fundamental Rights → Articles 12–35
II.  DPSPs → Articles 36–51
III. Fundamental Duties → Article 51A
IV.  Preamble → Article 1

(A) I, II, and IV only
(B) I, II, and III only
(C) All of I, II, III, and IV
(D) More than one of the above
(E) None of the above

---

**Q47.** Fundamental Duties are contained in which Part of the Constitution, inserted BETWEEN which two existing Parts?
(A) Between Part III (Fundamental Rights) and Part IV (DPSPs)
(B) Between Part IV (DPSPs) and Part V (The Union)
(C) Between Part II (Citizenship) and Part III (Fundamental Rights)
(D) More than one of the above
(E) None of the above

---

**Q48.** Which Fundamental Duty deals specifically with NATIONAL SERVICE (e.g., military)?
(A) Article 51A(c) — uphold sovereignty
(B) Article 51A(d) — defend the country and render national service when called upon
(C) Article 51A(j) — strive for excellence
(D) More than one of the above
(E) None of the above

---

**Q49.** The Right to Education Act (RTE Act, 2009) is most directly related to which Fundamental Duty?
(A) Duty to develop scientific temper [51A(h)]
(B) Duty to promote harmony [51A(e)]
(C) Duty to provide education to children aged 6–14 [51A(k)] — the 11th duty
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider the following pairs (Fundamental Duty → Article Clause):
I.   Protect natural environment + compassion for creatures → 51A(g)
II.  Safeguard public property + abjure violence → 51A(i)
III. Develop scientific temper + humanism → 51A(h)
IV.  Provide children's education (6–14 yrs) → 51A(k)

Which pairs are CORRECTLY matched?
(A) I, II and III only
(B) I and IV only
(C) All — I, II, III, and IV
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|------------|
| 1  | (C) | AND gate: output HIGH only when ALL inputs HIGH |
| 2  | (C) | OR gate: output LOW only when ALL inputs LOW |
| 3  | (B) | NOT gate = Inverter (flips input; one input only) |
| 4  | (C) | XOR output HIGH when inputs are DIFFERENT |
| 5  | (C) | XNOR = equality gate (output HIGH when inputs SAME) |
| 6  | (B) | XOR: 1⊕1 = 0 (same inputs → output LOW!) |
| 7  | (B) | XNOR: 1⊙1 = 1 (same inputs → output HIGH!) |
| 8  | (C) | 4-input gate: 2⁴ = 16 rows |
| 9  | (A) | 3-input OR: output 0 only when all 3 inputs are 0 — just 1 row |
| 10 | (C) | XOR Boolean = Y = A⊕B |
| 11 | (C) | AND Boolean = Y = A·B |
| 12 | (B) | A=1, B=0: different inputs → XOR output = 1 |
| 13 | (B) | A=0, B=1: different inputs → XNOR output = 0 (XNOR = opposite of XOR) |
| 14 | (C) | NOT gate has only 1 input. AND and XOR need 2+ inputs |
| 15 | (C) | A⊕A = 0 (XOR of any value with itself = 0) |
| 16 | (C) | A⊙A = 1 (XNOR of any value with itself = 1; opposite of XOR) |
| 17 | (C) | XOR is used for parity checking in data communication |
| 18 | (C) | 8-input gate: 2⁸ = 256 rows |
| 19 | (B) | NOT(0) = 1; NOT gate inverts the input |
| 20 | (D) | All three options A, B, C are correct and say the same thing — XNOR = complement of XOR |
| 21 | (B) | A=1,B=1: AND=1 ✅, OR=1 ✅, XOR=0 ❌, XNOR=1 ✅ → AND, OR, XNOR |
| 22 | (C) | A=0,B=0: AND=0, OR=0, XOR=0, XNOR=1 → Only XNOR gives output 1 |
| 23 | (B) | A⊕1 = A' (XOR with 1 acts as NOT/inverter) |
| 24 | (B) | AND gate is the digital equivalent of binary multiplication |
| 25 | (C) | 2ⁿ = 32 → n = 5 inputs (2⁵ = 32) |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|------------|
| 26 | (C) | Fundamental Duties = Part IV-A (not Part III = FR, not Part IV = DPSPs) |
| 27 | (C) | Article 51A = Fundamental Duties |
| 28 | (B) | 42nd Amendment Act, 1976 added Fundamental Duties (originally 10 duties) |
| 29 | (C) | Currently 11 Fundamental Duties (10 original + 11th added in 2002) |
| 30 | (C) | 86th Amendment Act, 2002 added the 11th duty (children's education) |
| 31 | (C) | Inspired by USSR Constitution (Fundamental Rights inspired by USA) |
| 32 | (B) | Swaran Singh Committee recommended inclusion of Fundamental Duties |
| 33 | (B) | Non-justiciable — courts cannot directly enforce them |
| 34 | (C) | Only citizens of India (not foreigners) |
| 35 | (B) | 51A(g) = protect environment including forests, lakes, rivers, wildlife AND compassion for living creatures |
| 36 | (C) | 51A(h) = develop scientific temper, humanism and spirit of inquiry and reform |
| 37 | (B) | 51A(e) has TWO parts: promote harmony AND renounce practices derogatory to women's dignity |
| 38 | (B) | 6 to 14 years (linked to RTE Act 2009) |
| 39 | (B) | 51A(c) = uphold sovereignty, unity and integrity of India — is a Fundamental Duty |
| 40 | (B) | Swaran Singh Committee (1976) |
| 41 | (B) | Only II (citizens only) and IV (11 duties) are correct; I is false (non-justiciable); III is false (added 1976, not 1950) |
| 42 | (B) | 51A(a) = abide by Constitution + respect National Flag and National Anthem |
| 43 | (B) | 51A(b) = cherish noble ideals of national freedom struggle |
| 44 | (C) | "File income tax returns" is NOT a Fundamental Duty — it's a legal obligation under tax law, not Article 51A |
| 45 | (B) | Both DPSPs and Fundamental Duties are non-justiciable |
| 46 | (B) | I, II, and III are correct; IV is wrong (Preamble has no Article number) |
| 47 | (B) | Part IV-A is inserted between Part IV (DPSPs, ending at Art 51) and Part V (The Union) |
| 48 | (B) | 51A(d) = defend the country and render national service when called upon |
| 49 | (C) | RTE Act 2009 directly implements 51A(k) — the 11th Fundamental Duty on children's education |
| 50 | (C) | All four pairs are correctly matched (I, II, III, IV all correct → Answer D would be "more than one" but since the question asks which pairs are correctly matched and all are correct, Answer C = all of I, II, III, IV) |

---

# 🔁 DAY 61 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Logic Gates

### Gate Output Rules (Core):
```
AND:   Output = 1 ONLY when ALL inputs = 1
OR:    Output = 0 ONLY when ALL inputs = 0
NOT:   Output = COMPLEMENT of single input (1→0, 0→1)
XOR:   Output = 1 when inputs are DIFFERENT  (opposite → 1)
XNOR:  Output = 1 when inputs are SAME       (equal → 1)
```

### XOR vs XNOR — The Most-Tested Pair:
```
XOR  → DIFFERENT inputs → HIGH output   (X = "eXclusive difference")
XNOR → SAME inputs     → HIGH output   (N = "NOT XOR" = opposite)

XOR truth table corners: (0,0)=0  (1,1)=0  →  same=0
XNOR truth table corners: (0,0)=1  (1,1)=1 →  same=1

XNOR = exact complement (flip) of XOR column!
```

### Boolean Expressions:
```
AND  → Y = A · B  (or AB)
OR   → Y = A + B
NOT  → Y = A'     (or Ā)
XOR  → Y = A ⊕ B
XNOR → Y = A ⊙ B  = (A⊕B)'
```

### Truth Table Row Count:
```
Formula: Rows = 2ⁿ  (n = number of inputs)
n=1 → 2 rows   |   n=2 → 4 rows
n=3 → 8 rows   |   n=4 → 16 rows
n=5 → 32 rows  |   n=8 → 256 rows
```

### Key Properties:
```
A ⊕ A = 0     (XOR with self = 0)
A ⊙ A = 1     (XNOR with self = 1)
A ⊕ 1 = A'    (XOR with 1 = inverter)
A ⊕ 0 = A     (XOR with 0 = no change)
```

### PYQ Trap List — Gates:
```
✅ XOR = HIGH for DIFFERENT (not same!) inputs
✅ XNOR = HIGH for SAME (not different!) inputs
✅ NOT gate = ONLY gate with 1 input
✅ Rows = 2ⁿ NOT 2×n (4 inputs = 16 rows, not 8!)
✅ XOR: 1⊕1 = 0 (same inputs → LOW!)
✅ XNOR: 1⊙1 = 1 (same inputs → HIGH!)
✅ XNOR = equality gate; XOR = difference gate
✅ XOR used for parity checking
✅ AND = digital equivalent of binary multiplication
```

---

## ⚡ RAPID FIRE — Fundamental Duties

### The Big Numbers:
```
Part IV-A  →  Article 51A  →  11 Fundamental Duties
42nd Amendment (1976) → Original 10 Duties
86th Amendment (2002) → Added 11th Duty (children's education, 6-14 yrs)
Swaran Singh Committee → Recommended duties
Inspired by → USSR Constitution
Applicable to → CITIZENS ONLY (not foreigners)
Justiciable? → NO (non-justiciable)
```

### All 11 Duties — Quick Memory Aid:
```
51A(a) → Abide Constitution + National Flag/Anthem
51A(b) → Cherish freedom movement ideals
51A(c) → Uphold sovereignty, unity, integrity
51A(d) → Defend country + national service
51A(e) → Promote harmony + renounce anti-women practices [TWO PARTS!]
51A(f) → Preserve composite culture/heritage
51A(g) → Protect environment + compassion for creatures [TWO PARTS!]
51A(h) → Scientific temper + humanism + inquiry/reform [THREE PARTS!]
51A(i) → Safeguard public property + abjure violence
51A(j) → Strive for excellence
51A(k) → Education for children 6-14 yrs [11th Duty — Added 2002]
```

### PYQ Trap List — Fundamental Duties:
```
✅ NOT in original 1950 Constitution (added 1976 by 42nd Amendment)
✅ Currently 11 duties (NOT 10 — 11th added 2002)
✅ NON-justiciable (courts CANNOT directly enforce)
✅ Only CITIZENS (NOT foreigners)
✅ Part IV-A (NOT Part IV = DPSPs; NOT Part III = FR)
✅ Inspired by USSR (NOT USA; USA inspired Fundamental Rights)
✅ 11th duty = education 6–14 years by 86th Amendment 2002
✅ Swaran Singh Committee recommended (8 duties; govt added 10)
✅ 51A(e) has TWO parts: harmony + women's dignity (one article!)
✅ 51A(g) = environment + compassion for living creatures (both in one!)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Logic Gate Rules**: AND = ALL inputs HIGH → output HIGH; OR = ALL inputs LOW → output LOW; NOT = inverts; XOR = DIFFERENT inputs → HIGH; XNOR = SAME inputs → HIGH. Rows = 2ⁿ formula.
2. **XOR vs XNOR (Most Tested)**: XOR is the "difference gate" (1 when inputs differ); XNOR is the "equality gate" (1 when inputs match). XNOR = NOT(XOR). Key: 1⊕1=0 but 1⊙1=1.
3. **XOR Properties**: A⊕A=0; A⊕1=A' (acts as NOT); XOR used for parity checking in data transmission.
4. **Fundamental Duties**: Part IV-A, Article 51A; 11 duties total (10 added 1976 by 42nd Amendment + 11th added 2002 by 86th Amendment); non-justiciable; citizens only; inspired by USSR.
5. **Key Duty Traps**: 51A(e) has TWO parts (harmony + women's dignity); 51A(g) covers environment AND compassion for creatures; 51A(h) has THREE parts (scientific temper + humanism + inquiry/reform); 11th duty = children's education ages 6–14.

---

## 📅 DAY 62 PREVIEW — What's Coming Next:
**CS**: Digital Electronics — Universal Gates (NAND and NOR): Why they're called universal, implementing all gates from NAND only, implementing all gates from NOR only, Half Adder (Sum + Carry outputs), Seven-Segment Decoder
**GS**: Indian Economy — Inflation, GDP, Types of Unemployment

---

*🚀 Day 61 of 170 — Phase 2 begins! Digital Electronics is one of the BIGGEST scoring topics in TRE 3.0 and expected to dominate TRE 4.0. Logic gates are the foundation — every PDU, every circuit, every flip-flop is built on these basics. Master the XOR vs XNOR distinction and the 2ⁿ rows formula — they appear in EVERY paper! 🎯*
