# 📅 BPSC TRE 4.0 — DAY 67 COMPLETE STUDY MODULE
### REVISION DAY: Digital Electronics Complete (Days 61–66) + Science & Technology Revision
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (2 hrs): Complete Digital Electronics Revision — work through the checklist, then attempt all 25 CS MCQs
> - Afternoon (1 hr): Science & Technology Revision — attempt all 25 GS MCQs
> - Evening (30 min): Read all detailed explanations carefully; flag weak spots
> - Night (30 min): Write your personal "I still confuse these" trap list in your notebook

---

> ⚠️ **TODAY'S FORMAT IS DIFFERENT**
> Revision Day = MCQs WITH detailed explanations included inline.
> Read the explanation for EVERY question — even the ones you got right.
> The explanations contain the deepest PYQ insight.

---

# PART 1: DIGITAL ELECTRONICS REVISION
## 📋 Checklist — Self-Assessment Before You Begin

Rate yourself on each item: ✅ Solid | ⚠️ Shaky | ❌ Need to review

```
LOGIC GATES (Day 61):
[ ] AND gate: output HIGH only when ALL inputs HIGH
[ ] OR gate: output LOW only when ALL inputs LOW
[ ] NOT gate: single input, inverts output
[ ] XOR gate: output HIGH when inputs are DIFFERENT
[ ] XNOR gate: output HIGH when inputs are SAME
[ ] Truth table rows = 2ⁿ formula (n = number of inputs)
[ ] XNOR = equality gate; XOR = difference gate

UNIVERSAL GATES (Day 62):
[ ] NAND and NOR are BOTH universal gates
[ ] NAND: output LOW only when ALL inputs HIGH
[ ] NOR: output HIGH only when ALL inputs LOW
[ ] NOT from NAND = 1 gate (tie both inputs)
[ ] AND from NAND = 2 gates; OR from NAND = 3 gates
[ ] OR from NOR = 2 gates; AND from NOR = 3 gates
[ ] Half adder: SUM = XOR; CARRY = AND (NOT product/difference!)
[ ] Seven-segment display: 7 segments for digits 0–9

BOOLEAN ALGEBRA (Day 63):
[ ] Identity: A·1=A, A+0=A
[ ] Null: A·0=0, A+1=1
[ ] Idempotent: A·A=A, A+A=A
[ ] Complement: A·A'=0, A+A'=1, (A')'=A
[ ] Absorption: A+AB=A, A·(A+B)=A
[ ] De Morgan 1: (A·B)' = A'+B'
[ ] De Morgan 2: (A+B)' = A'·B'
[ ] RULE: "Break the bar, CHANGE THE SIGN"
[ ] SOP = OR of AND terms; POS = AND of OR terms
[ ] SOM = canonical SOP (minterms); POM = canonical POS (maxterms)

K-MAP (Day 64):
[ ] Groups = powers of 2 only (1,2,4,8,16)
[ ] Columns/rows follow Gray code: 00, 01, 11, 10
[ ] Wraparound allowed — all 4 edges connect
[ ] 4 corners of 4-var K-Map = valid group of 4
[ ] Larger group = fewer literals = simpler expression
[ ] Don't-care (X) = may be included in groups
[ ] EPI = Essential Prime Implicant (only group covering a minterm)

NUMBER SYSTEMS (Day 65):
[ ] (1234)₁₀ = (10011010010)₂ = (2322)₈ = (4D2)₁₆
[ ] (1011.1101)₂ = 11.8125₁₀
[ ] BCD max digit = 9 (NOT 15!)
[ ] Binary→Octal: group 3 bits; Binary→Hex: group 4 bits
[ ] Hex: A=10, B=11, C=12, D=13, E=14, F=15
[ ] Booth's algorithm = binary MULTIPLICATION (not division!)

FLIP-FLOPS, MUX, ROM (Day 66):
[ ] SR: S=R=1 → FORBIDDEN; JK: J=K=1 → TOGGLE
[ ] D flip-flop: Q_next = D (delay)
[ ] T flip-flop: T=1 → Toggle, T=0 → Hold
[ ] 8:1 MUX → 3 select lines; 4:1 MUX → 2 select lines
[ ] PLA = Programmable Logic Array (BOTH AND + OR programmable)
[ ] EPROM = UV light erasure; EEPROM = electrical erasure
[ ] MROM, PROM, EPROM all valid ROM types → Answer D
[ ] Hamming corrects; Parity/CRC/Checksum only detect
[ ] Error codes: Hamming + CRC + Checksum all valid → Answer D
```

---

## 📝 COMPUTER SCIENCE — 25 PYQ-STYLE MCQs WITH DETAILED EXPLANATIONS
### ⚠️ Attempt each question FIRST, then read the explanation

---

**Q1.** Which of the following gates is called the "equality gate"?
(A) XOR gate
(B) NAND gate
(C) XNOR gate
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
The XNOR gate is called the **equality gate** because its output is HIGH (1) only when both inputs are **SAME** (equal). Think: XNOR checks if A equals B.

```
XOR truth table corners:   (0,0)→0  (1,1)→0   ← SAME inputs give 0
XNOR truth table corners:  (0,0)→1  (1,1)→1   ← SAME inputs give 1
```

XOR is called the **difference gate** — HIGH when inputs are DIFFERENT.
XNOR is called the **equality gate** — HIGH when inputs are SAME.

🚨 **PYQ TRAP**: Students confuse "XOR = same = 1" — this is BACKWARDS. XOR = DIFFERENT = 1. XNOR = SAME = 1.

**Memory Trick**: X**NOR** → **N** = **N**ot different → **SAME** → 1.

---

**Q2.** A 2-input AND gate truth table has how many rows?
(A) 2
(B) 8
(C) 4
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
Number of rows in a truth table = **2ⁿ**, where n = number of inputs.

For a **2-input** gate: 2² = **4 rows**.

```
A  B  | Output
0  0  |   ?
0  1  |   ?
1  0  |   ?
1  1  |   ?
```

This formula applies regardless of which gate type (AND, OR, XOR, NAND...) — the number of rows depends ONLY on the number of INPUT variables.

For 4 inputs: 2⁴ = 16 rows.
For 3 inputs: 2³ = 8 rows.

🚨 **PYQ TRAP**: Students calculate 2×n instead of 2ⁿ. For 4 inputs: answer is 16, NOT 4×2=8.

---

**Q3.** NAND and NOR gates are called universal gates because:
(A) They are the fastest gates in digital circuits
(B) They can implement ANY Boolean function by themselves
(C) They use fewer transistors than AND/OR gates
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**DETAILED EXPLANATION:**
**Universal gate** means a gate that can implement **ANY Boolean function** — it can build NOT, AND, OR, XOR, and every other gate, all by itself.

```
FROM NAND ALONE:           FROM NOR ALONE:
NOT:  NAND(A,A) = A'       NOT:  NOR(A,A) = A'
AND:  NAND → NAND(as NOT)  OR:   NOR → NOR(as NOT)
OR:   NOT A, NOT B, NAND   AND:  NOT A, NOT B, NOR
```

The reason for their universality is rooted in **De Morgan's Theorem**:
- NAND(A,B) = (AB)' = A' + B' (can produce OR behavior with inverted inputs)
- NOR(A,B) = (A+B)' = A'·B' (can produce AND behavior with inverted inputs)

Speed and transistor count are secondary engineering benefits — they are NOT why NAND/NOR are called "universal."

🚨 **PYQ TRAP**: "Only NAND is universal; NOR is not" → FALSE. **BOTH** are universal.

---

**Q4.** What are the OUTPUTS of a half adder?
(A) Sum and Product
(B) Sum and Difference
(C) Sum and Carry
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
A half adder is the simplest digital **arithmetic** circuit. It adds two 1-bit binary numbers.

```
HALF ADDER:
  Inputs:  A, B
  Outputs: SUM   = A ⊕ B  (XOR gate)
           CARRY = A · B  (AND gate)

Truth table:
A=0, B=0: SUM=0, CARRY=0  (0+0=00)
A=0, B=1: SUM=1, CARRY=0  (0+1=01)
A=1, B=0: SUM=1, CARRY=0  (1+0=01)
A=1, B=1: SUM=0, CARRY=1  (1+1=10 in binary!)
```

The outputs are **always** SUM and CARRY. Never "product" (that's multiplication), never "difference" (that's subtraction), never "quotient" (that's division).

🚨 **#1 PYQ TRAP in half adder**: "Half adder outputs are Sum and Product" → ABSOLUTELY FALSE. Sum and **Carry** — always, only, forever.

---

**Q5.** Apply De Morgan's Theorem to simplify: (A + B)'
(A) A' + B'
(B) A + B
(C) A' · B'
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
De Morgan's Second Theorem states:
**(A + B)' = A' · B'**

"The complement of an OR = the AND of the complements"

**Step-by-step application — the "Break the Bar, Change the Sign" rule:**
1. **Break the bar** (remove the complementation over the whole expression)
2. **Change the sign** (OR + becomes AND ·)
3. **Complement each variable** (A → A', B → B')

Result: (A + B)' = A' · B'

**Truth Table Verification:**
```
A  B | A+B | (A+B)' | A' | B' | A'·B'
0  0 |  0  |   1    |  1 |  1 |   1   ✅
0  1 |  1  |   0    |  1 |  0 |   0   ✅
1  0 |  1  |   0    |  0 |  1 |   0   ✅
1  1 |  1  |   0    |  0 |  0 |   0   ✅
```

🚨 **THE MOST COMMON PYQ TRAP**: Students write (A+B)' = A' + B'. **WRONG!** The sign MUST change from + to ·. Remember: complement of OR = AND of complements.

---

**Q6.** Simplify the Boolean expression: Y = AB + AB'
(A) Y = A + B
(B) Y = AB
(C) Y = A
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
```
Y = AB + AB'

Step 1: Factor out A using the Distributive Law:
  Y = A(B + B')

Step 2: Apply Complement Law: B + B' = 1
  Y = A · 1

Step 3: Apply Identity Law: A · 1 = A
  Y = A
```

**Intuition**: AB means "A is true AND B is true." AB' means "A is true AND B is false." Together, they cover ALL cases where A is true (regardless of B). So the result is just A.

**Visual check:**
- When A=0: AB=0, AB'=0, so Y=0 ✓ (A=0 gives Y=0)
- When A=1: AB = B, AB' = B', so Y = B + B' = 1 ✓ (A=1 gives Y=1)
This confirms Y = A.

---

**Q7.** In a K-Map, which of the following group sizes is VALID?
(A) 3 cells
(B) 6 cells
(C) 8 cells
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
K-Map groups **must** be powers of 2: **1, 2, 4, 8, 16, 32...**

Valid sizes: 1, 2, 4, **8**, 16 ✅
Invalid sizes: 3, 5, 6, 7, 9, 10, 11, 12, 13, 14, 15 ❌

**Why powers of 2 only?**
The fundamental principle of K-Map is that adjacent cells differ by exactly 1 variable. When you group 2 cells → 1 variable cancels. Group 4 → 2 variables cancel. Group 8 → 3 variables cancel. Only powers of 2 maintain this "one variable per doubling" relationship perfectly.

A group of 3 cannot maintain proper adjacency (you'd be mixing different levels of simplification). A group of 6 = 4+2, meaning it's not a pure power and can't form a valid rectangle.

🚨 **PYQ TRAP**: "A group of 6 is valid because 2+4=6" → FALSE. 6 is NOT a power of 2. You cannot form a single valid rectangular group of 6.

---

**Q8.** In a K-Map, the column order for a 3-variable map (variables B and C) is:
(A) BC = 00, 01, 10, 11
(B) BC = 00, 10, 11, 01
(C) BC = 00, 01, 11, 10
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
K-Map columns follow **Gray Code** order: **00, 01, 11, 10**

The critical property: each adjacent pair differs by **exactly 1 bit**:
- 00 → 01: only the last bit changes ✅
- 01 → 11: only the first bit changes ✅
- 11 → 10: only the last bit changes ✅
- 10 → 00: only the first bit changes ✅ (wraparound!)

**Why NOT regular binary (00, 01, 10, 11)?**
In regular binary: 01 → 10 changes 2 bits simultaneously. This would break the adjacency property, and your groupings would be incorrect.

**Most damaging mistake in K-Map**: using regular binary order 00,01,10,11 instead of Gray code 00,01,11,10. This swaps cells m2 and m3, making all your group readings wrong.

---

**Q9.** What is the decimal equivalent of hexadecimal 4D2?
(A) 1124
(B) 1256
(C) 1234
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
Convert (4D2)₁₆ to decimal using positional values:

```
4 × 16² + D × 16¹ + 2 × 16⁰
= 4 × 256 + 13 × 16 + 2 × 1
= 1024   +  208    +   2
= 1234
```

Key: D in hexadecimal = **13** in decimal.

**The famous BPSC TRE PYQ triplet — memorize this completely:**
```
(1234)₁₀ = (10011010010)₂ = (2322)₈ = (4D2)₁₆
```

**Verification approach**: 4×256=1024 is the anchor. 1024 is close to 1234. Then 13×16=208, 1024+208=1232, +2=1234. ✅

🚨 **PYQ TRAP**: "Hex 4D2 = 4E2 in decimal context" — students confuse D=13 with E=14. The answer is 4D2 for 1234, not 4E2.

---

**Q10.** What is the maximum decimal digit that can be represented in BCD (Binary Coded Decimal)?
(A) 7
(B) 15
(C) 9
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
BCD (Binary Coded Decimal) represents each decimal digit (0–9) using **4 binary bits**.

Valid BCD codes: 0000 (=0) through 1001 (=9)
Invalid BCD codes: 1010 (=10) through 1111 (=15)

**Why maximum is 9, not 15?**
Although 4 bits CAN represent 0–15 in pure binary, BCD only uses codes 0000 to 1001 because it encodes **decimal digits** (0–9 only). The codes 1010–1111 represent 10–15 which are NOT single decimal digits. They are **invalid** in BCD.

```
Valid BCD:   0000 0001 0010 0011 0100 0101 0110 0111 1000 1001
Decimal:        0    1    2    3    4    5    6    7    8    9
Invalid BCD: 1010 1011 1100 1101 1110 1111 (10,11,12,13,14,15 — not single decimal digits!)
```

🚨 **THE MOST FAMOUS BCD TRAP**: "BCD maximum = 15 (1111)" → FALSE! Max = 9 (1001). This appears in EVERY BPSC TRE paper.

---

**Q11.** The binary number 1011.1101 in decimal is:
(A) 13.8125
(B) 11.75
(C) 11.8125
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
Split at the binary point:

**Integer part (1011):**
```
1×2³ + 0×2² + 1×2¹ + 1×2⁰
= 8 + 0 + 2 + 1 = 11
```

**Fractional part (.1101):**
```
1×2⁻¹ + 1×2⁻² + 0×2⁻³ + 1×2⁻⁴
= 0.5 + 0.25 + 0 + 0.0625
= 0.8125
```

**Total**: 11 + 0.8125 = **11.8125**

**Fractional powers of 2 — must know:**
2⁻¹=0.5, 2⁻²=0.25, 2⁻³=0.125, 2⁻⁴=0.0625

🚨 **PYQ TRAP**: Integer part 1011 = 11 (NOT 13!). Students miscalculate: 8+4+1=13 is WRONG because the middle bit is 0, not 1. The correct value: 1011 = 8+0+2+1=11.

---

**Q12.** How many select lines does an 8:1 MUX require?
(A) 8
(B) 4
(C) 3
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
Formula: For an N:1 MUX, number of select lines = **log₂(N)**

For 8:1 MUX: log₂(8) = log₂(2³) = **3 select lines**

**Why?** The select lines act as a binary ADDRESS for which input to choose:
- 3 select lines → 2³ = 8 different binary combinations → can address 8 inputs

```
Select lines S₂ S₁ S₀ → select input number (S₂×4 + S₁×2 + S₀×1):
000 → Input 0    100 → Input 4
001 → Input 1    101 → Input 5
010 → Input 2    110 → Input 6
011 → Input 3    111 → Input 7
```

**Full MUX reference:**
- 2:1 → 1 line
- 4:1 → 2 lines
- 8:1 → 3 lines ← PYQ FAVOURITE
- 16:1 → 4 lines

🚨 **BIGGEST MUX TRAP**: "8:1 MUX needs 8 select lines" → COMPLETELY WRONG. It needs 3. The "8" means 8 DATA inputs, not 8 select lines.

---

**Q13.** PLA stands for:
(A) Parallel Logic Architecture
(B) Programmable Logic Array
(C) Programmable Latch Array
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**DETAILED EXPLANATION:**
**PLA = Programmable Logic Array**

In a PLA:
- **AND array** = programmable (creates product terms / minterms)
- **OR array** = programmable (creates sum of products)

Both arrays being programmable gives maximum flexibility to implement any Boolean function.

**Contrast with PAL (Programmable Array Logic):**
- Only AND array is programmable; OR array is FIXED
- PAL is LESS flexible than PLA

**Memory trick:** PL**A** = both **A**rrays programmable. P**A**L = only **A**nd programmable (OR is fixed).

A very common BPSC TRE question: "What does PLA stand for?" The answer is always **Programmable Logic Array** — not "Programmable Latch Array" (there's no such thing) and not "Parallel Logic Architecture."

---

**Q14.** Which of the following correctly states De Morgan's First Theorem?
(A) (A · B)' = A' · B'
(B) (A + B)' = A' + B'
(C) (A · B)' = A' + B'
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
De Morgan's **First Theorem** (complement of AND):
**(A · B)' = A' + B'**

The operation CHANGES from AND (·) to OR (+).

De Morgan's **Second Theorem** (complement of OR):
**(A + B)' = A' · B'**

The operation CHANGES from OR (+) to AND (·).

**The Universal Rule — "Break the bar, CHANGE THE SIGN":**
1. Complement the whole expression (break the bar)
2. Complement each individual variable
3. **FLIP** the operator: AND → OR or OR → AND

```
Option A: (A·B)' = A'·B' → WRONG (sign didn't change!)
Option B: (A+B)' = A'+B' → WRONG (sign didn't change!)
Option C: (A·B)' = A'+B' → CORRECT ✅ (AND became OR)
```

🚨 **Most dangerous trap**: Writing (A·B)' = A'·B' (keeping AND). The complement of AND is OR of complements — the operation MUST change.

---

**Q15.** Which flip-flop eliminates the forbidden state of the SR flip-flop?
(A) D flip-flop
(B) T flip-flop
(C) JK flip-flop
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
The **SR flip-flop** has a fundamental weakness: when S=1 and R=1, the output is FORBIDDEN (indeterminate, invalid).

The **JK flip-flop** was specifically designed to fix this:
- In SR: S=1, R=1 → FORBIDDEN ❌
- In JK: J=1, K=1 → **TOGGLE** (Q changes to Q') ✅

The JK flip-flop maps J=S (Set) and K=R (Reset), but adds a **feedback** from the output to the input gates. This feedback makes J=K=1 produce a well-defined TOGGLE rather than an indeterminate state.

**The evolution chain:**
SR → JK (adds toggle, fixes forbidden) → D (ties K=J', simplifies) → T (ties J=K, only toggle/hold)

The D flip-flop and T flip-flop also don't have forbidden states, but they weren't DESIGNED to eliminate SR's forbidden state — they are derived from JK for specific applications. The JK was the direct solution to SR's weakness.

---

**Q16.** In K-Map simplification, wrapping around is:
(A) Not allowed — edges are treated as boundaries
(B) Allowed only on left-right edges, not top-bottom
(C) Allowed on ALL four edges (left-right and top-bottom)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
A K-Map is topologically equivalent to a **TORUS** (donut shape). This means:
- Left edge connects to right edge (horizontal wrap)
- Top edge connects to bottom edge (vertical wrap)

**All 4 edges wrap around in both dimensions.**

**Practical examples of valid wraparound groups:**

In a 4-variable K-Map (4×4):
1. **Left-right wrap**: Column CD=00 is adjacent to column CD=10 (the first and last columns)
   → Cells m0 and m2 in the same row are adjacent
   
2. **Top-bottom wrap**: Row AB=00 is adjacent to row AB=10 (first and last rows)
   → Cells m0 and m8 in the same column are adjacent
   
3. **Corner wrap**: m0, m2, m8, m10 (all four corners) form a valid group of 4!

🚨 **Most missed PYQ trap**: Students see cells at opposite edges and think they CAN'T be grouped. They absolutely CAN. Missing wraparound groups means you won't find the simplest expression.

---

**Q17.** Which of the following ROM types is erased using ultraviolet (UV) light?
(A) MROM
(B) EEPROM
(C) EPROM
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
**EPROM = Erasable Programmable ROM**

The "E" in EPROM stands for **Erasable** — specifically, erasable by **UV light**.
- Has a **quartz window** on top of the chip
- UV light shines through this window for 15–30 minutes
- UV energy breaks the charge trapped in floating-gate transistors
- After erasure, chip can be reprogrammed

**EEPROM** = Electrically Erasable PROM — the EXTRA "E" means Electrically.
- No UV light needed
- Erased by electrical signals
- Can be erased byte by byte while in-circuit

**Memory trick:**
- EPROM = "E" = Erasable (needs external UV light — you must REMOVE the chip)
- EEPROM = "EE" = Electrically Erasable (stays in circuit, electrical signals)
- The extra "E" in EEPROM = Electrical!

MROM (Mask ROM) = NEVER erased or reprogrammed. Made once by manufacturer.

🚨 **TRAP**: Confusing EPROM (UV) with EEPROM (Electrical). The extra E in EEPROM = Electrically.

---

**Q18.** Booth's algorithm is used for:
(A) Binary division of unsigned numbers
(B) Binary addition with carry propagation
(C) Binary multiplication of signed numbers
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
**Booth's Algorithm** was developed by **Andrew Donald Booth (1950)** specifically for **binary MULTIPLICATION** of **signed (2's complement) binary numbers**.

Key facts:
- Used for **MULTIPLICATION** (not addition, not division, not subtraction)
- Works for **SIGNED** numbers (both positive and negative — 2's complement)
- **Reduces** the number of additions needed compared to naive multiplication
- Uses: add/subtract, arithmetic RIGHT SHIFT operations
- Pattern: examines 2 bits at a time (current bit and previous bit)

**Why it was invented:** Standard binary multiplication of negative numbers is complex. Booth's algorithm handles the sign automatically through a clever encoding.

🚨 **TRAPS:**
- "Booth's = binary DIVISION" → FALSE (it's multiplication!)
- "Booth's works only for positive numbers" → FALSE (designed for signed numbers!)
- "Booth's = addition algorithm" → FALSE (it's multiplication!)

---

**Q19.** The canonical Sum of Minterms (SOM) form is obtained from which rows of the truth table?
(A) Rows where output = 0
(B) Rows where output = X (don't-care)
(C) Rows where output = 1
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
**SOM (Sum of Minterms) = Canonical SOP form**

A minterm mₙ = 1 for exactly ONE input combination (row n) and 0 for all others.

SOM = OR all minterms where the function output = **1**

```
TRUTH TABLE → SOM CONNECTION:
Output = 1 at row 3 → include minterm m₃
Output = 1 at row 5 → include minterm m₅
Output = 1 at row 7 → include minterm m₇

SOM: f = m₃ + m₅ + m₇ = Σ(3, 5, 7)
```

**POM (Product of Maxterms) = Canonical POS form**
→ Uses rows where output = **0**
→ M₀·M₂·M₄ = Π(0, 2, 4)

**Notation:**
- SOM written as: Σ(row numbers with output=1)
- POM written as: Π(row numbers with output=0)

**Memory trick:** S in **SOM** → **S**elect the **1**s (Sum = OR = looking for 1s)
P in **POM** → **P**ick the **0**s (Product = AND = looking for 0s)

---

**Q20.** Which of the following correctly lists valid types of ROM?
(A) MROM only
(B) PROM and EPROM only
(C) MROM, PROM, and EPROM — all three are valid ROM types
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (D)**

**DETAILED EXPLANATION:**
This question has the classic **BPSC TRE "Option D" pattern**.

ALL of the following are valid types of ROM:
- **MROM** (Mask ROM) — programmed by manufacturer ✅
- **PROM** (Programmable ROM) — programmed once by user ✅
- **EPROM** (Erasable Programmable ROM) — UV light erasable ✅
- **EEPROM** (Electrically Erasable PROM) ✅
- **Flash Memory** (advanced EEPROM) ✅

The key insight: EPROM, EEPROM, and Flash are all forms of ROM even though they can be erased and reprogrammed. They are still **primarily read devices** and **non-volatile** — which makes them ROM variants.

The question's answer = **(D) More than one of the above** because the question in BPSC format typically gives only two of these as options A and B, and the correct answer acknowledges ALL are valid ROM types.

---

**Q21.** Which error detection code can both DETECT AND CORRECT single-bit errors?
(A) CRC (Cyclic Redundancy Check)
(B) Checksum
(C) Hamming code
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
```
ERROR CODE CAPABILITIES:
  Parity bit:  Detect 1-bit errors   | CANNOT correct
  Checksum:    Detect most errors    | CANNOT correct
  CRC:         Detect burst errors   | CANNOT correct
  Hamming:     Detect 1-bit + 2-bit  | CAN CORRECT 1-bit ✅
```

**Why can Hamming code correct errors?**
Hamming places **parity bits at power-of-2 positions** (1, 2, 4, 8...). When an error occurs:
- Each parity bit covers specific bit positions
- The pattern of which parity checks FAIL creates a binary number
- That binary number is the **EXACT BIT POSITION** of the error!
- Flip that bit → error corrected!

**Hamming code key formula:**
2^r ≥ m + r + 1 (where r = parity bits, m = data bits)

For m=4 data bits → need r=3 parity bits (2³=8 ≥ 4+3+1=8 ✅)

🚨 **TRAP**: "CRC can correct errors" → FALSE! CRC is powerful for DETECTION but does NOT correct. Only Hamming (and related ECC codes) provide correction.

---

**Q22.** In Boolean algebra, which law states: A + AB = A?
(A) Idempotent Law
(B) Complement Law
(C) Absorption Law
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
**Absorption Law**: A + AB = A (AND form: A·(A+B) = A)

**Why?** "A absorbs AB" — AB is a subset of A. If A is true, then A OR (A AND something) is still just A.

**Proof using other laws:**
```
A + AB
= A·1 + A·B          (Identity: A = A·1)
= A·(1 + B)          (Distributive: factor out A)
= A·1                 (Null: 1+B = 1)
= A                   (Identity: A·1 = A)
```

**Absorption is extremely useful for simplification:**
```
Y = AB + A    → same as A + AB = A    → Y = A
Y = XY + X + Z = X + Z               (X absorbs XY)
```

**Other related absorption forms:**
- A·(A+B) = A (dual form)
- A + A'B = A + B (generalized form — uses distributive then complement)

---

**Q23.** A T flip-flop with T permanently connected to 1 (always HIGH) will:
(A) Always output Q=1 regardless of clock
(B) Toggle output with every clock pulse (act as a divide-by-2 circuit)
(C) Reset to Q=0 and stay there
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**DETAILED EXPLANATION:**
T flip-flop behavior: T=1 → TOGGLE at every clock edge

If T is **permanently HIGH (T=1)**:
- Every clock pulse → Q changes to Q'
- Clock 1: Q: 0→1
- Clock 2: Q: 1→0
- Clock 3: Q: 0→1
- Clock 4: Q: 1→0
- ... (toggles every single clock pulse)

**Output frequency** = Clock frequency ÷ 2

This is called a **frequency divider** or **divide-by-2 circuit**.

**Application in counters:**
Chain 4 T flip-flops with T=1:
- FF1: divides by 2
- FF2: divides by 4
- FF3: divides by 8
- FF4: divides by 16
Together: a 4-bit binary counter (counts 0–15)!

🎯 **KEY PYQ FACT**: T flip-flop with T=1 = divide-by-2 frequency divider = basic building block of binary counters.

---

**Q24.** In the K-Map for a 4-variable function, the four corner cells belong to:
(A) No valid group — corners cannot be grouped together
(B) Two separate groups of 2 cells each
(C) A valid group of 4 cells (via wraparound in both dimensions)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**DETAILED EXPLANATION:**
In a 4-variable K-Map (AB rows, CD columns):

The four corners are: **m0 (AB=00,CD=00), m2 (AB=00,CD=10), m8 (AB=10,CD=00), m10 (AB=10,CD=10)**

```
         CD=00  CD=01  CD=11  CD=10
AB=00  [  m0  ]  m1     m3  [  m2  ]
AB=01    m4     m5     m7     m6
AB=11    m12    m13    m15    m14
AB=10  [  m8  ]  m9     m11 [  m10 ]
```

**Are these 4 corners adjacent?**
- m0 and m2: same row (AB=00), columns wrap (CD=00 ↔ CD=10) ✅
- m8 and m10: same row (AB=10), columns wrap ✅
- m0 and m8: same column (CD=00), rows wrap (AB=00 ↔ AB=10) ✅
- m2 and m10: same column (CD=10), rows wrap ✅
- All four corners → **valid group of 4!**

**What does this group represent?**
Check which variables are constant:
m0(0000), m2(0010), m8(1000), m10(1010)
- A: 0,0,1,1 → changes → cancels
- B: 0,0,0,0 → CONSTANT = 0 → B' appears
- C: 0,0,0,0 → CONSTANT = 0 → C' appears (wait: m2 has C=1? Let me recheck)

Actually m0=ABCD=0000, m2=ABCD=0010, m8=ABCD=1000, m10=ABCD=1010:
- A: 0,0,1,1 → changes → cancels
- B: 0,0,0,0 → CONSTANT 0 → B'
- C: 0,1,0,1 → changes → cancels (Note: C is the 3rd bit)
- D: 0,0,0,0 → CONSTANT 0 → D'

Result: **B'D'** (two literals from a group of 4 ✅)

---

**Q25.** Which of the following are valid error detection/correction methods in digital systems?
(A) Hamming code is the only valid error correction method
(B) CRC is the only valid error detection method
(C) Hamming code, CRC, and Checksum are ALL valid error detection codes
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (D)**

**DETAILED EXPLANATION:**
This question uses the **classic BPSC TRE "Option D" answer pattern**.

**All three are valid error detection/correction codes:**

```
CHECKSUM:
  Method: Sum all data bytes; append sum (or complement)
  Used in: TCP/IP headers, UDP, IP protocol
  Strength: Simple; catches most single and some multi-bit errors

CRC (Cyclic Redundancy Check):
  Method: Polynomial division with a generator polynomial
  Used in: Ethernet, ZIP/RAR files, USB, CDs/DVDs, hard drives
  Strength: Excellent burst error detection

HAMMING CODE:
  Method: Parity bits at power-of-2 positions
  Used in: ECC RAM, RAID systems, deep space communications
  Strength: Detects 2-bit errors; CORRECTS 1-bit errors
```

**Why answer (D)?**
In BPSC TRE's 5-option format, when multiple options given (like "Hamming only" or "CRC only") are each partially correct, the answer is **(D) More than one** — because BOTH the statement "Hamming is valid" AND "CRC is valid" AND "Checksum is valid" are all true.

The question tests whether you know that **all three** are legitimate error detection approaches — not just one.

---

# PART 2: SCIENCE & TECHNOLOGY REVISION
## 📝 GS — 25 MCQs WITH DETAILED EXPLANATIONS

---

**Q26.** Green Hydrogen is produced by:
(A) Steam Methane Reforming from natural gas
(B) Electrolysis of water using renewable energy
(C) Coal gasification
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
Green hydrogen = **electrolysis of water** (2H₂O → 2H₂ + O₂) powered by **renewable energy** (solar, wind, hydro). Zero CO₂ emissions.

Grey = natural gas + high emissions. Blue = natural gas + CCS. Black/Brown = coal.
Only GREEN uses renewable energy for electrolysis.

---

**Q27.** In electrolysis of water, hydrogen gas is produced at:
(A) Anode (positive electrode)
(B) Cathode (negative electrode)
(C) Both electrodes simultaneously
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
```
ANODE (+):   2H₂O → O₂ + 4H⁺ + 4e⁻   (OXYGEN produced)
CATHODE (−): 4H⁺ + 4e⁻ → 2H₂          (HYDROGEN produced)
```
H₂ at CATHODE; O₂ at ANODE. Memory trick: **H**ydrogen at **C**athode — H.C. = **H**appy **C**athode.

---

**Q28.** Chandrayaan-3 made India the first country to:
(A) Land on the Moon (any location)
(B) Land near the Moon's South Pole
(C) Orbit the Moon for more than 1 year
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
Chandrayaan-3 landed near the **Moon's South Pole** on **23 August 2023** — the FIRST mission ever to do so. India became the **4th country** to soft-land on the Moon overall (after USA, USSR, China), but the **1st at the South Pole**.

🚨 TRAP: India was NOT the first country to land on Moon overall — USA was first (Apollo 11, 1969).

---

**Q29.** Chandrayaan-3 lander is named _____ and rover is named _____:
(A) Pragyan (lander) and Vikram (rover)
(B) Vikram (lander) and Pragyan (rover)
(C) Aditya (lander) and Shakti (rover)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**Vikram** = lander (named after Vikram Sarabhai, father of Indian space program)
**Pragyan** = rover (Sanskrit for "wisdom")

Memory: **V**ikram **L**ands first (VL → Vikram Lander), **P**ragyan **R**olls out (PR → Pragyan Rover). The lander comes first (VIKRAM), then the rover rolls out (PRAGYAN).

---

**Q30.** Aditya-L1 is India's mission to study:
(A) Mars
(B) The Moon's far side
(C) The Sun
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
**Aditya-L1** (launched 2 September 2023) = India's first **solar observatory** mission.
- Aditya = Sanskrit for Sun
- L1 = positioned at **Lagrange Point 1** between Earth and Sun (~1.5 million km from Earth)
- Studies: Solar corona, solar wind, solar flares, Coronal Mass Ejections (CMEs)

---

**Q31.** Blue hydrogen differs from grey hydrogen because blue hydrogen:
(A) Uses renewable energy for production
(B) Captures and stores the CO₂ produced (Carbon Capture and Storage)
(C) Is produced from water using nuclear energy
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
Grey and blue hydrogen are BOTH produced from natural gas via steam methane reforming. The difference: Blue adds **CCS (Carbon Capture and Storage)** to capture the CO₂ before it enters the atmosphere. Grey releases all CO₂ freely.

Option A = Green hydrogen (renewables). Option C = Pink hydrogen (nuclear + electrolysis).

---

**Q32.** India's National Green Hydrogen Mission target for 2030 is to produce:
(A) 50 MMT per year
(B) 5 MMT per year
(C) 500 kg per year
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**5 MMT** (Million Metric Tonnes) per year by 2030. This would make India one of the world's largest green hydrogen producers.

The mission also targets:
- 125 GW renewable energy capacity
- 6 lakh green jobs
- Reducing fossil fuel imports

SIGHT scheme provides financial incentives for production and electrolyser manufacturing.

---

**Q33.** A qubit (quantum bit) can be in which state(s)?
(A) Only 0
(B) Only 1
(C) Both 0 AND 1 simultaneously (superposition)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
Classical bit = either 0 OR 1 (at any given moment)
Quantum bit (qubit) = 0 AND 1 **simultaneously** — this is called **SUPERPOSITION**.

When measured, the qubit "collapses" to either 0 or 1. But BEFORE measurement, it exists in a superposition of both states. This allows quantum computers to process many possibilities simultaneously — exponentially faster for certain problems.

India's National Quantum Mission: ₹6,003 crore (2023–2031) to develop 50–1000 qubit quantum computers.

---

**Q34.** 5G mobile network was commercially launched in India in:
(A) 2019
(B) October 2020
(C) October 2022
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
5G was commercially launched in India in **October 2022** by Reliance Jio and Bharti Airtel at the India Mobile Congress in Delhi. PM Modi inaugurated it.

Key 5G facts:
- Speed: up to 20 Gbps (vs 4G: ~100 Mbps) — 20× faster
- Latency: ~1ms (vs 4G: ~40ms)
- Enables: IoT, smart cities, autonomous vehicles, AR/VR

---

**Q35.** The byproduct of hydrogen combustion or use in a fuel cell is:
(A) Carbon dioxide (CO₂)
(B) Nitrogen oxide (NOₓ)
(C) Water vapour (H₂O)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
H₂ + ½O₂ → H₂O (in combustion or fuel cell)

The ONLY byproduct is **water vapour** — this is why hydrogen is called a zero-emission fuel. No CO₂, no NOₓ, no particulates. Just water.

This makes green hydrogen truly clean — clean production (electrolysis with renewables) AND clean use (only water output).

---

**Q36.** Gaganyaan is India's mission to:
(A) Send a probe to the Sun
(B) Land on Mars
(C) Send Indian astronauts to space (human spaceflight)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
**Gaganyaan** = India's first **human spaceflight** mission.
- Will carry 3 Indian astronauts (called **Vyomanauts** or Gagannauts)
- Target orbit: 400 km above Earth
- Duration: 3 days in orbit
- Astronauts trained in Russia
- Unmanned test flights (TV-D1) conducted first

If successful, India will become the 4th country with independent human spaceflight capability (after USA, Russia, China).

---

**Q37.** XPoSat, launched by India in January 2024, studies:
(A) Atmosphere of Venus
(B) X-ray polarimetry — extreme cosmic X-ray sources
(C) Asteroid composition
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**XPoSat (X-ray Polarimeter Satellite)** — India's first dedicated X-ray polarimetry mission.
- Studies bright X-ray sources like **pulsars, black holes, neutron stars** in extreme environments
- India is only the 2nd country after USA to launch such a mission (NASA's IXPE was first)
- Instruments: POLIX (Polarimeter Instrument in X-rays) + XSPECT (X-ray spectroscopy)

---

**Q38.** LLM in the context of Artificial Intelligence stands for:
(A) Logic and Language Mechanism
(B) Large Language Model
(C) Linear Learning Method
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**LLM = Large Language Model**

LLMs are AI systems trained on massive text datasets to understand and generate human language. They power tools like ChatGPT (OpenAI), Gemini (Google), and Claude (Anthropic).

Key LLM concepts:
- **Transformer architecture** (introduced 2017) = foundation of LLMs
- **Parameters**: LLMs have billions of parameters (GPT-4 ~1.7 trillion)
- **Generative AI**: LLMs can generate new text, code, analysis, creative content
- **India AI Mission**: ₹10,372 crore to develop Indian LLMs for Indic languages

---

**Q39.** The SIGHT scheme under India's National Green Hydrogen Mission provides incentives for:
(A) Solar panel installation on residential buildings
(B) Green hydrogen production AND domestic electrolyser manufacturing
(C) Electric vehicle purchase subsidies
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**SIGHT = Strategic Interventions for Green Hydrogen Transition**

Two components:
1. **Incentive for green hydrogen production** (reduce cost to make it competitive with grey hydrogen)
2. **Incentive for domestic electrolyser manufacturing** (build India's own electrolyser industry — currently dominated by foreign companies)

Goal: Bring down the cost of green hydrogen from ~$5/kg to under $1/kg by 2030.

---

**Q40.** Pink hydrogen is produced using which energy source?
(A) Solar panels
(B) Wind farms
(C) Nuclear power plants
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
**Pink hydrogen** = electrolysis of water powered by **nuclear energy**.

Hydrogen colour-energy source map:
- **Green** = Solar + Wind + Hydro (renewables) → zero emissions
- **Pink** = Nuclear power → very low emissions (no CO₂ from nuclear itself)
- **Grey** = Natural gas (Steam Methane Reforming) → high CO₂
- **Blue** = Natural gas + CCS → lower CO₂
- **Black/Brown** = Coal → highest CO₂

---

**Q41.** India's National Quantum Mission was approved with a budget of approximately:
(A) ₹600 crore
(B) ₹6,003 crore
(C) ₹60,000 crore
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**National Quantum Mission** approved by Cabinet in April 2023:
- Budget: **₹6,003 crore** for 2023–2031 (8 years)
- Goal: Develop quantum computers with **50–1000 qubits**
- Establish Thematic Hubs (T-Hubs) in top academic/research institutions
- Applications: Secure communication, drug discovery, financial modeling, AI acceleration

---

**Q42.** The POLIX instrument on XPoSat is used for:
(A) X-ray spectroscopy of solar flares
(B) X-ray polarimetry of cosmic sources
(C) Plasma wave measurement
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**POLIX = Polarimeter Instrument in X-rays**

POLIX studies the **polarization** of X-rays from bright cosmic X-ray sources (pulsars, black hole binary systems, Active Galactic Nuclei). Polarimetry reveals the geometry of the X-ray emission region — providing information that spectroscopy alone cannot.

XPoSat carries two instruments: POLIX (polarimetry) + XSPECT (spectroscopy and temporal study).

---

**Q43.** The Chandrayaan-3 mission was launched using which launch vehicle?
(A) PSLV (Polar Satellite Launch Vehicle)
(B) LVM3 (Launch Vehicle Mark 3 — formerly GSLV Mk III)
(C) SSLV (Small Satellite Launch Vehicle)
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
Chandrayaan-3 was launched on **14 July 2023** using **LVM3** (Launch Vehicle Mark 3, previously known as GSLV Mk III or "Bahubali").

LVM3 is ISRO's **heaviest rocket**:
- Payload to GTO: 4 tonnes
- Payload to LEO: 8 tonnes
- Previously used for: Chandrayaan-2, OneWeb commercial satellites

PSLV (workhorse rocket) is used for lighter payloads. LVM3 needed here because Chandrayaan-3 required high-energy trajectory to Moon.

---

**Q44.** Deep learning is a subset of which broader field?
(A) Quantum computing
(B) Machine learning
(C) Cloud computing
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**Hierarchy of AI fields:**
```
Artificial Intelligence (AI)
  └── Machine Learning (ML)
        └── Deep Learning (DL)
              └── Neural Networks → many layers → "deep"
```

Deep learning uses **neural networks with many layers** (hence "deep"). It learns hierarchical representations of data:
- Layer 1: detects edges
- Layer 2: detects shapes
- Layer 3: detects objects
- etc.

Powers: Image recognition, speech recognition, language translation, AlphaGo, GPT models.

---

**Q45.** India was the _____ country to soft-land on the Moon:
(A) First
(B) Second
(C) Fourth
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
Countries with successful Moon soft landings before India (Chandrayaan-3, 2023):
1. **USSR** — Luna 9 (1966) — first ever soft landing
2. **USA** — Surveyor 1 (1966), Apollo 11 (1969 — first humans)
3. **China** — Chang'e 3 (2013) — first in 21st century

**India** = 4th country overall (Chandrayaan-3, August 2023).

BUT India is **1st to land near the Moon's South Pole** — no other country has done this!

---

**Q46.** Consider the following — which are correct?
I. Green hydrogen uses electrolysis with renewable energy
II. Aditya-L1 is India's mission to the Moon
III. Chandrayaan-3 landed at the Moon's South Pole region
IV. 5G was launched in India in 2022

(A) I and III only
(B) II and IV only
(C) I, III, and IV only
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
- **I = TRUE** ✅ Green hydrogen = electrolysis + renewables
- **II = FALSE** ❌ Aditya-L1 = SUN mission (not Moon!) at Lagrange Point L1
- **III = TRUE** ✅ Chandrayaan-3 landed near Moon's South Pole region
- **IV = TRUE** ✅ 5G launched India October 2022

So I, III, IV are correct → **(C) I, III, and IV only**

---

**Q47.** The Voyager missions (USA) are significant because they:
(A) Were the first missions to land on Mars
(B) Have traveled beyond the solar system into interstellar space
(C) Were the first missions to orbit Jupiter
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**Voyager 1** (launched 1977) = first human-made object to enter **interstellar space** (2012).
**Voyager 2** (launched 1977) = second to enter interstellar space (2018).

Both are now in **interstellar space** — beyond the heliopause (boundary of Sun's influence).

Voyager 1 is the **most distant human-made object** ever.

Still communicating with Earth after 47 years — remarkable engineering achievement!

---

**Q48.** Generative AI refers to AI that can:
(A) Only analyze existing data without creating new content
(B) Generate new content (text, images, audio, code) that didn't exist before
(C) Control physical robots and machines
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**Generative AI** = AI systems that can **create new content**:
- Text: ChatGPT, Claude, Gemini
- Images: DALL-E, Midjourney, Stable Diffusion
- Audio: Music generation tools
- Video: Sora (OpenAI), Google Veo
- Code: GitHub Copilot

Contrast with **Discriminative AI** = classifies existing data (spam detection, image recognition — tells you WHAT something is, doesn't create).

India's INDIAai Mission includes developing Indic language generative AI models.

---

**Q49.** The term "heliopause" refers to:
(A) A temporary pause in solar flare activity
(B) The boundary where the Sun's solar wind meets interstellar space
(C) The area around a black hole
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (B)**

**EXPLANATION:**
**Heliopause** = the boundary where the **Sun's solar wind pressure equals the pressure of interstellar space**. It's the effective "edge" of the solar system.

Beyond the heliopause = **interstellar space**.

Regions from inside out:
1. **Heliosphere**: region dominated by Sun's solar wind
2. **Termination shock**: solar wind slows abruptly
3. **Heliosheath**: slowed solar wind region
4. **Heliopause**: boundary with interstellar medium
5. **Interstellar space**: beyond Sun's influence

Voyager 1 crossed the heliopause in 2012.

---

**Q50.** Consider these science & technology statements:
I. Chandrayaan-3 lander = Vikram; rover = Pragyan
II. Green hydrogen = zero CO₂ emissions; grey hydrogen = high CO₂
III. Booth's algorithm = binary MULTIPLICATION (signed numbers)
IV. BCD maximum digit = 9 (codes 1010–1111 are invalid)

Which are CORRECT?
(A) I and II only
(B) I, II, and III only
(C) All of I, II, III, and IV
(D) More than one of the above
(E) None of the above

**✅ ANSWER: (C)**

**EXPLANATION:**
All four statements are CORRECT:

- **I ✅** Vikram = lander (lands first), Pragyan = rover (rolls out from lander)
- **II ✅** Green hydrogen (electrolysis + renewables) = zero CO₂; grey hydrogen (SMR from natural gas) = high CO₂ emissions
- **III ✅** Booth's algorithm (Andrew Booth, 1950) = efficient binary MULTIPLICATION of signed (2's complement) numbers
- **IV ✅** BCD uses 4 bits per digit but only codes 0000–1001 (0–9) are valid; 1010–1111 (10–15) are INVALID in BCD; maximum valid digit = 9

All four → **(C) All of I, II, III, and IV** → which is also represented as **(D) More than one of the above** in BPSC format.

---

# 🔁 DAY 67 — COMPLETE DIGITAL ELECTRONICS REVISION NOTES

## ⚡ MASTER RAPID FIRE — All 6 Days Consolidated

### LOGIC GATES (Day 61):
```
AND:  ALL inputs HIGH → output HIGH    |  XOR: DIFFERENT inputs → HIGH
OR:   ALL inputs LOW  → output LOW     |  XNOR: SAME inputs → HIGH
NOT:  Single input, inverts            |  Rows = 2ⁿ (n = number of inputs)
XNOR = equality gate; XOR = difference gate
```

### UNIVERSAL GATES (Day 62):
```
UNIVERSAL = NAND and NOR (BOTH!)
NAND: output 0 ONLY when ALL inputs = 1 | NOR: output 1 ONLY when ALL inputs = 0

From NAND:         |  From NOR:
NOT  = 1 gate      |  NOT = 1 gate
AND  = 2 gates     |  OR  = 2 gates  ← NOR's natural gate
OR   = 3 gates     |  AND = 3 gates

Half Adder: SUM = XOR gate; CARRY = AND gate  ← NEVER "product" or "difference"!
Seven-segment display: 7 LED segments, shows digits 0–9
```

### BOOLEAN ALGEBRA (Day 63):
```
Identity:     A·1=A | A+0=A        Null:         A·0=0 | A+1=1
Idempotent:   A·A=A | A+A=A        Complement:   A·A'=0 | A+A'=1 | (A')'=A
Absorption:   A+AB=A | A(A+B)=A   (most useful for simplification!)

DE MORGAN'S: "BREAK THE BAR, CHANGE THE SIGN"
(A·B)' = A' + B'    ← AND → OR of complements
(A+B)' = A' · B'    ← OR → AND of complements
TRAP: (A+B)' ≠ A'+B' — THE SIGN MUST CHANGE!

SOP = OR of AND terms | POS = AND of OR terms
SOM = Σ(rows where output=1) | POM = Π(rows where output=0)
```

### K-MAP (Day 64):
```
GROUPS: Powers of 2 only (1,2,4,8,16) | Rectangular | Can wraparound
Column/row order: GRAY CODE (00,01,11,10) — NOT regular binary (00,01,10,11)!
Wraparound: ALL 4 edges connect (K-Map = torus topology)
4 corners of 4-variable K-Map = valid group of 4!
Larger group → fewer literals → simpler expression
Don't-care X: MAY be included (not mandatory)
EPI: Essential Prime Implicant = MUST be in final answer
```

### NUMBER SYSTEMS (Day 65):
```
THE THREE KEY PYQ FACTS — MEMORIZE DIRECTLY:
(1234)₁₀ = (10011010010)₂ = (2322)₈ = (4D2)₁₆
(1011.1101)₂ = 11.8125₁₀
BCD max digit = 9 (NOT 15!)

Hex: A=10,B=11,C=12,D=13,E=14,F=15
Binary→Octal: group 3 bits | Binary→Hex: group 4 bits
Read remainders BOTTOM→TOP in division conversions
Booth's = binary MULTIPLICATION of signed numbers
```

### FLIP-FLOPS, MUX, ROM, ERROR CODES (Day 66):
```
SR: S=R=1 → FORBIDDEN | JK: J=K=1 → TOGGLE | D: Q=D | T: T=1→Toggle
MUX: N:1 → log₂(N) select lines | 4:1→2 | 8:1→3 | 16:1→4
PLA = BOTH AND + OR programmable | PAL = only AND programmable

ROM Types:
MROM → manufacturer only (permanent)
PROM → user once (permanent after)
EPROM → UV LIGHT erasure (quartz window)
EEPROM → ELECTRICAL erasure (in circuit, byte by byte)
All three MROM/PROM/EPROM valid ROM types → ANSWER = D!

Error codes:
Hamming → CORRECTS 1-bit errors (strongest)
CRC → detects burst errors (polynomial division)
Checksum → simple sum method (used in TCP/IP)
All three valid → ANSWER = D!
```

---

## 🚨 THE ULTIMATE PYQ TRAP LIST — All 6 Days

```
GATES:
✅ XNOR = SAME inputs = HIGH (NOT XOR!)
✅ XOR = DIFFERENT inputs = HIGH
✅ Truth table rows = 2ⁿ (NOT 2×n!)
✅ BOTH NAND and NOR are universal (not just NAND!)
✅ Half adder = SUM + CARRY (NEVER product/difference!)

BOOLEAN:
✅ (A+B)' = A'·B' NOT A'+B' (sign MUST change!)
✅ (A·B)' = A'+B' NOT A'·B'
✅ A+AB = A (Absorption — NOT AB!)
✅ 1+1 = 1 in Boolean (NOT 2!)
✅ Dual = swap AND↔OR, 0↔1 (DON'T complement variables)

K-MAP:
✅ Groups of 3, 5, 6 = INVALID (powers of 2 only!)
✅ Column order = 00,01,11,10 (Gray code, NOT 00,01,10,11!)
✅ Wraparound = ALLOWED on all 4 edges
✅ 4 corners = valid group of 4!
✅ X = don't-care = MAY (not must) be in groups

NUMBER SYSTEMS:
✅ 1234 hex = 4D2 (D=13, NOT E=14!)
✅ 1011.1101 binary = 11.8125 (integer part = 11, NOT 13!)
✅ BCD max = 9 (NOT 15!)
✅ Binary→Octal = 3 bits; Binary→Hex = 4 bits (don't swap!)
✅ Read remainders BOTTOM to TOP
✅ Booth's = MULTIPLICATION (NOT division!)

FLIP-FLOPS & MEMORY:
✅ SR forbidden = S=R=1; JK toggle = J=K=1 (DIFFERENT behaviors!)
✅ 8:1 MUX = 3 select lines (NOT 8!)
✅ EPROM = UV light; EEPROM = electrical (extra E = Electrical!)
✅ PLA = BOTH arrays programmable; PAL = only AND
✅ ROM = NON-volatile (data survives power off)
✅ Hamming CORRECTS errors; parity/CRC/checksum only DETECT
✅ MROM + PROM + EPROM all valid ROM → Answer = D
✅ Hamming + CRC + Checksum all valid → Answer = D
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Gate Identity**: XNOR=SAME=HIGH; XOR=DIFFERENT=HIGH; Half adder=SUM(XOR)+CARRY(AND); NAND AND NOR both universal; 2-input truth table=4 rows (2²); rows=2ⁿ.
2. **De Morgan's Rule**: "(A+B)' = A'·B' and (A·B)' = A'+B' — BREAK THE BAR, CHANGE THE SIGN." The operation always flips (AND↔OR). This is the single most tested Boolean theorem in every BPSC TRE paper.
3. **Number Systems Core**: 1234 = 10011010010₂ = 2322₈ = 4D2₁₆. Binary 1011.1101 = 11.8125. BCD max=9. Binary→Octal=group 3; Binary→Hex=group 4. Booth's=MULTIPLICATION.
4. **Memory Devices**: EPROM=UV light erasure (has quartz window); EEPROM=electrical erasure (extra E!). 8:1 MUX=3 select lines. PLA=both AND+OR programmable. MROM+PROM+EPROM all ROM→Answer D. Hamming corrects; others only detect→Answer D.
5. **K-Map Must-Remember**: Gray code order 00,01,11,10 (not regular binary). Groups=powers of 2 only. All 4 edges wrap. 4 corners=valid group of 4. Larger group=fewer literals. EPI must always be in final answer.

---

## 📅 DAY 68 PREVIEW — What's Coming Next:
**Phase 2 — Week 11 begins: Operating Systems**
**CS**: OS Introduction & Types — Batch OS, Time-sharing OS, Real-time OS, Distributed OS, Embedded OS. Time-sharing = marks beginning of computer communications. Process vs Program vs Thread. Process states (New, Ready, Running, Waiting, Terminated). Types of interrupts (Hardware, Software, Trap — NOT "Memory interrupt"). Kernel.
**GS**: Current Affairs — India Policy developments, recent government schemes, economic updates

---

*🚀 Day 67 of 170 — WEEK 10 COMPLETE! You have now fully mastered Digital Electronics — one of the highest-scoring CS topics in BPSC TRE. The checklist at the start of today's module is your personal exam blueprint. Any item marked ❌ or ⚠️ needs one more targeted session before the exam. Phase 2's Digital Electronics week is now behind you — Operating Systems begins tomorrow. Every day you're getting closer to that top 50 rank! 🎯*
