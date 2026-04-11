# 📅 DAY 17 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
## CS: Stack — Expression Conversion (Infix / Postfix / Prefix)
## GS: India Geography — Physical Features (Eastern Ghats, Western Ghats, Peninsular Plateau)

> **Target:** TOP RANK | **Format:** 5-option BPSC ABCDE | **PYQs integrated throughout**
> ⚠️ **RULE:** Solve ALL 50 questions FIRST → Answers are at the END of this file.

---

# ═══════════════════════════════════════════
# 🖥️ COMPUTER SCIENCE SECTION
# STACK: EXPRESSION CONVERSION
# ═══════════════════════════════════════════

---

## 📌 CONCEPT 1: What is an Expression?

An **expression** is a combination of **operands** (variables/numbers) and **operators** (+, -, *, /) arranged in a specific notation.

There are **3 types** of notation:

```
┌─────────────────────────────────────────────────────────────────┐
│              THREE NOTATIONS AT A GLANCE                        │
│                                                                 │
│  Expression: A plus B                                           │
│                                                                 │
│  INFIX    →   A + B   (operator BETWEEN operands)               │
│  POSTFIX  →   A B +   (operator AFTER operands)                 │
│  PREFIX   →   + A B   (operator BEFORE operands)                │
│                                                                 │
│  Infix    = Human-readable  (we use this daily)                 │
│  Postfix  = Computer-friendly (also: Reverse Polish Notation)   │
│  Prefix   = Polish Notation                                     │
└─────────────────────────────────────────────────────────────────┘
```

### Real World Analogy:
- **Infix:** "Ram **loves** India" → Subject-Verb-Object (normal English)
- **Postfix:** "Ram India **loves**" → like Yoda speech ("Luke, I am your father" style)
- **Prefix:** "**loves** Ram India" → Verb-Subject-Object

---

## 📌 CONCEPT 2: Why do we need Postfix/Prefix?

**Problem with Infix:**
1. Requires **parentheses** to resolve ambiguity → `(A + B) * C` vs `A + (B * C)`
2. Requires knowledge of **operator precedence** and **associativity**
3. Computers cannot directly evaluate infix — they must first convert it

**Advantage of Postfix:**
1. ✅ No parentheses needed — order is already embedded
2. ✅ No precedence rules needed during evaluation
3. ✅ Easily evaluated using a single Stack
4. ✅ Used internally by compilers and calculators

> **PYQ FACT:** Postfix notation is also called **Reverse Polish Notation (RPN)**. It was invented by Jan Łukasiewicz.

---

## 📌 CONCEPT 3: Operator Precedence & Associativity

This is CRITICAL for correct conversion. Memorize this table:

```
┌─────────────────────────────────────────────────────────────┐
│           OPERATOR PRECEDENCE TABLE (HIGH to LOW)           │
│                                                             │
│  Priority 1 (Highest): ^ (Exponentiation)                   │
│                         Associativity: RIGHT to LEFT        │
│                                                             │
│  Priority 2:            * / % (Multiply, Divide, Modulo)   │
│                         Associativity: LEFT to RIGHT        │
│                                                             │
│  Priority 3 (Lowest):   + - (Addition, Subtraction)        │
│                         Associativity: LEFT to RIGHT        │
│                                                             │
│  TRICK: "BODMAS" → Exponent > Multiply/Divide > Add/Sub    │
└─────────────────────────────────────────────────────────────┘
```

**Associativity matters when precedence is EQUAL:**
- `A - B - C` → Evaluated as `(A - B) - C` → LEFT to RIGHT
- `A ^ B ^ C` → Evaluated as `A ^ (B ^ C)` → RIGHT to LEFT

---

## 📌 CONCEPT 4: Infix to Postfix — The Stack Algorithm

### Visual Diagram of the Algorithm:

```
┌─────────────────────────────────────────────────────────────────────┐
│              INFIX TO POSTFIX ALGORITHM                             │
│                                                                     │
│  INPUT: Read expression from LEFT to RIGHT                          │
│  OUTPUT: Postfix string                                             │
│  TOOL: One Stack (for operators)                                    │
│                                                                     │
│  RULES:                                                             │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ TOKEN      │ ACTION                                          │   │
│  ├────────────┼─────────────────────────────────────────────── │   │
│  │ Operand    │ → DIRECTLY add to OUTPUT                        │   │
│  │ (          │ → PUSH to Stack                                 │   │
│  │ )          │ → POP from Stack and add to OUTPUT until (      │   │
│  │            │   found. Discard both parentheses               │   │
│  │ Operator   │ → POP operators with HIGHER or EQUAL precedence │   │
│  │            │   from Stack to OUTPUT, then PUSH current op    │   │
│  │            │   (For ^: only POP if strictly HIGHER)          │   │
│  │ End        │ → POP all remaining operators to OUTPUT         │   │
│  └─────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
```

### Time & Space Complexity:
| Metric | Value |
|--------|-------|
| Time Complexity | **O(N)** — each character processed once |
| Space Complexity | **O(N)** — Stack can hold at most N operators |

> **⭐ PYQ DIRECT FACT:** Time complexity of Infix to Postfix = **O(N)**. This appeared in TRE 2.0!

---

## 📌 CONCEPT 5: Worked Example — Infix to Postfix

### Example 1: `A + B * C - D`

```
┌──────────────────────────────────────────────────────────────────┐
│  Expression: A + B * C - D                                       │
│                                                                  │
│  STEP-BY-STEP TRACE:                                             │
│                                                                  │
│  Token │ Stack (bottom→top) │ Output                            │
│  ──────┼────────────────────┼────────────────────────────────── │
│  A     │ (empty)            │ A                                  │
│  +     │ +                  │ A                                  │
│  B     │ +                  │ A B                                │
│  *     │ + *                │ A B      (* has higher prec. than+)│
│  C     │ + *                │ A B C                              │
│  -     │ -                  │ A B C * +  (pop * then +, push -)  │
│  D     │ -                  │ A B C * + D                        │
│  END   │ (empty)            │ A B C * + D -  (pop -)             │
│                                                                  │
│  FINAL POSTFIX: A B C * + D -                                    │
└──────────────────────────────────────────────────────────────────┘
```

**Verification:** `A + B * C - D`
- First evaluate `B * C` = X
- Then `A + X` = Y
- Then `Y - D`
✅ Postfix `A B C * + D -` gives same result.

---

### Example 2: `(A + B) * (C - D)` — With Parentheses

```
┌──────────────────────────────────────────────────────────────────┐
│  Token │ Stack           │ Output                                │
│  ──────┼─────────────────┼───────────────────────────────────── │
│  (     │ (               │                                       │
│  A     │ (               │ A                                     │
│  +     │ ( +             │ A                                     │
│  B     │ ( +             │ A B                                   │
│  )     │ (empty)         │ A B +     ← pop + until (, discard (  │
│  *     │ *               │ A B +                                 │
│  (     │ * (             │ A B +                                 │
│  C     │ * (             │ A B + C                               │
│  -     │ * ( -           │ A B + C                               │
│  D     │ * ( -           │ A B + C D                             │
│  )     │ *               │ A B + C D -  ← pop -, discard (       │
│  END   │ (empty)         │ A B + C D - *                         │
│                                                                  │
│  FINAL POSTFIX: A B + C D - *                                    │
└──────────────────────────────────────────────────────────────────┘
```

---

### Example 3: `A ^ B ^ C` — Right-to-Left Associativity

```
┌──────────────────────────────────────────────────────────────────┐
│  Token │ Stack │ Output                                          │
│  ──────┼───────┼──────────────────────────────────────────────  │
│  A     │       │ A                                               │
│  ^     │ ^     │ A                                               │
│  B     │ ^     │ A B                                             │
│  ^     │ ^ ^   │ A B   ← ^ has EQUAL prec; but ^ is RIGHT assoc │
│        │       │   so we DO NOT pop the existing ^               │
│  C     │ ^ ^   │ A B C                                           │
│  END   │       │ A B C ^ ^                                       │
│                                                                  │
│  FINAL POSTFIX: A B C ^ ^                                        │
│  Which means: A ^ (B ^ C)  ✓ Right-to-Left                      │
└──────────────────────────────────────────────────────────────────┘
```

> **⚠️ TRAP:** For `^` with equal precedence, do NOT pop (right-associative). For `+,-,*,/` with equal precedence, DO pop (left-associative). **This is a classic BPSC trap question!**

---

## 📌 CONCEPT 6: Infix to Prefix — The Algorithm

Converting to Prefix is slightly different:

```
┌─────────────────────────────────────────────────────────────────┐
│              INFIX TO PREFIX — 3-STEP METHOD                    │
│                                                                 │
│  STEP 1: REVERSE the infix expression                           │
│          (Also swap all '(' with ')' and vice versa)            │
│                                                                 │
│  STEP 2: Apply the INFIX TO POSTFIX algorithm on reversed expr  │
│          BUT: for equal precedence, use RIGHT-to-LEFT for all   │
│                                                                 │
│  STEP 3: REVERSE the result → This is your PREFIX expression    │
└─────────────────────────────────────────────────────────────────┘
```

### Example: `A + B * C` → Prefix

- **Step 1:** Reverse → `C * B + A`
- **Step 2:** Infix to Postfix of `C * B + A` → `C B * A +`
- **Step 3:** Reverse → `+ A * B C`
- **Final PREFIX:** `+ A * B C` ✅

**Verification:** `+ A * B C` → `A + (B * C)` ✓

---

## 📌 CONCEPT 7: Postfix Evaluation using Stack

Once you have a Postfix expression, how does the computer evaluate it?

```
┌─────────────────────────────────────────────────────────────────┐
│              POSTFIX EVALUATION ALGORITHM                       │
│                                                                 │
│  RULES:                                                         │
│  ┌────────────────────────────────────────────────────────┐    │
│  │ TOKEN     │ ACTION                                      │    │
│  ├───────────┼─────────────────────────────────────────── │    │
│  │ Operand   │ PUSH onto Stack                             │    │
│  │ Operator  │ POP two operands from Stack                 │    │
│  │           │ Apply operator: (second_popped OP first_pop)│    │
│  │           │ PUSH result back onto Stack                 │    │
│  │ End       │ Stack top = FINAL ANSWER                    │    │
│  └────────────────────────────────────────────────────────┘    │
│                                                                 │
│  ⚠️ ORDER MATTERS: If A and B are popped (B first, A second):  │
│     Operation is: A OP B   (first popped is right operand)     │
└─────────────────────────────────────────────────────────────────┘
```

### Example: Evaluate `3 4 2 * + 1 -` (which is `3 + 4 * 2 - 1`)

```
Token │ Stack (bottom→top) │ Action
──────┼────────────────────┼──────────────────────────────
3     │ 3                  │ Push 3
4     │ 3 4                │ Push 4
2     │ 3 4 2              │ Push 2
*     │ 3 8                │ Pop 2,4 → 4*2=8 → Push 8
+     │ 11                 │ Pop 8,3 → 3+8=11 → Push 11
1     │ 11 1               │ Push 1
-     │ 10                 │ Pop 1,11 → 11-1=10 → Push 10

FINAL ANSWER = 10 ✅
```

---

## 📌 CONCEPT 8: Quick Conversion Reference Table

| Infix Expression | Postfix | Prefix |
|-----------------|---------|--------|
| A + B | A B + | + A B |
| A + B * C | A B C * + | + A * B C |
| (A + B) * C | A B + C * | * + A B C |
| A * B + C * D | A B * C D * + | + * A B * C D |
| A + B - C | A B + C - | - + A B C |
| A ^ B ^ C | A B C ^ ^ | ^ A ^ B C |

---

## 📌 CONCEPT 9: Important Facts & Traps for BPSC

```
┌─────────────────────────────────────────────────────────────────┐
│            ⭐ HIGH-YIELD BPSC FACTS — MEMORIZE THESE            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. Infix → Postfix uses STACK  ✓                               │
│  2. Infix → Postfix time = O(N) ✓ (Direct PYQ!)                │
│  3. Postfix is also called: REVERSE POLISH NOTATION (RPN)       │
│  4. Prefix is also called: POLISH NOTATION                      │
│  5. Postfix evaluation uses STACK                               │
│  6. Parentheses are NOT needed in Prefix or Postfix             │
│  7. ^ is RIGHT associative; +,-,*,/ are LEFT associative        │
│  8. Postfix/Prefix avoids ambiguity without parentheses         │
│  9. Algorithm invented by: Dijkstra's Shunting Yard Algorithm   │
│  10. In Postfix eval: first popped = RIGHT operand              │
│                                                                 │
│  ⚠️ TRAPS TO WATCH:                                             │
│  ❌ "Postfix is read right-to-left" → FALSE (read left-to-right)│
│  ❌ "Prefix needs Stack for eval" → TRUE (same stack approach)  │
│  ❌ "A + B = BA+" → FALSE, correct is "A B +"                   │
│  ❌ "Time complexity is O(N²)" → FALSE, it's O(N)               │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📌 CONCEPT 10: Complete Notation Comparison

```
┌────────────────────────────────────────────────────────────────────┐
│                  NOTATION COMPARISON CHART                         │
├──────────────────┬────────────────┬──────────────┬────────────────┤
│ Feature          │ Infix          │ Postfix      │ Prefix         │
├──────────────────┼────────────────┼──────────────┼────────────────┤
│ Operator Place   │ Between        │ After        │ Before         │
│ Human Readable   │ ✅ Yes         │ ❌ No        │ ❌ No          │
│ Computer Friendly│ ❌ No          │ ✅ Yes       │ ✅ Yes         │
│ Needs Parens     │ Sometimes      │ Never        │ Never          │
│ Needs Precedence │ Yes            │ No           │ No             │
│ Also Called      │ -              │ RPN          │ Polish Notation│
│ Eval Uses Stack  │ No (indirect)  │ Yes          │ Yes            │
│ Read Direction   │ L to R         │ L to R       │ R to L         │
└──────────────────┴────────────────┴──────────────┴────────────────┘
```

---

# ═══════════════════════════════════════════════════
# 🌍 GENERAL STUDIES SECTION
# INDIA GEOGRAPHY — PHYSICAL FEATURES
# Eastern Ghats | Western Ghats | Peninsular Plateau
# ═══════════════════════════════════════════════════

---

## 📌 GS CONCEPT 1: The Big Picture — India's Physical Divisions

```
┌────────────────────────────────────────────────────────────────────┐
│              INDIA'S PHYSICAL DIVISIONS                            │
│                                                                    │
│  1. The Himalayas (Northern Mountain Wall)                         │
│  2. The Northern Plains (Indo-Gangetic Plain)                      │
│  3. The Peninsular Plateau ← TODAY'S MAIN FOCUS                    │
│  4. The Coastal Plains (East & West)                               │
│  5. The Islands (Andaman & Nicobar + Lakshadweep)                  │
│  6. The Thar Desert (Rajasthan)                                     │
│                                                                    │
│         [NORTH]                                                    │
│    ~~~~~~~~~~~~~~~~~~~~ HIMALAYAS ~~~~~~~~~~~~~~~~~~~              │
│    ════════════════ NORTHERN PLAINS ════════════════               │
│         THAR │    ┌──────────────────────┐                        │
│        DESERT │    │   PENINSULAR PLATEAU │                        │
│               │    │   (DECCAN PLATEAU)   │                        │
│               │    │                      │                        │
│    WESTERN    │    │     EASTERN           │                       │
│    GHATS      │    │     GHATS             │                       │
│    (West      │    │     (East Coast)      │                       │
│     Coast)   │    └──────────────────────┘                        │
│    [Arabian   │                  [Bay of Bengal]                   │
│    Sea Coast] │                                                    │
└────────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS CONCEPT 2: The Peninsular Plateau

The **Peninsular Plateau** is one of the oldest and most stable landmasses of India (part of the **Gondwana Supercontinent**).

### Key Facts:

| Feature | Detail |
|---------|--------|
| Formation | Part of ancient Gondwana land |
| Age | One of the OLDEST landmasses — Archaean rocks |
| Composition | Hard crystalline, igneous & metamorphic rocks |
| Area | About 16 lakh sq. km |
| Shape | Triangular |
| Highest point | Anamudi (2695 m) in Western Ghats |
| Rivers direction | Most rivers flow WEST to EAST (drain into Bay of Bengal) |
| Exception | Narmada & Tapi flow WEST (fault valleys / rift valleys) |

### Sub-divisions of Peninsular Plateau:
1. **Central Highlands** — North of Narmada river, slope towards north
   - Aravalli Hills (oldest fold mountain of India)
   - Vindhya Range
   - Satpura Range
   
2. **Deccan Plateau** — South of Narmada river; bounded by:
   - Western Ghats on the west
   - Eastern Ghats on the east
   - Slopes gently from **west to east**

> **PYQ FACT:** Deccan Plateau slopes from **West to East**, which is why most rivers flow **East** into the Bay of Bengal.

---

## 📌 GS CONCEPT 3: Western Ghats (Sahyadri)

```
┌────────────────────────────────────────────────────────────────────┐
│                    WESTERN GHATS — KEY FACTS                       │
├──────────────────────────────────────────────────────────────────  │
│  Also called: SAHYADRI Mountains                                   │
│  Location: Parallel to West Coast of India                         │
│  Stretch: From Tapi River (Gujarat) to Kanyakumari (Tamil Nadu)   │
│  Length: About 1600 km                                             │
│  UNESCO Status: World Heritage Site (2012)                         │
│                                                                    │
│  KEY PASSES (Ghats):                                               │
│  • Thalghat / Thal Ghat → Mumbai to Nashik (Maharashtra)           │
│  • Bhorghat / Bhor Ghat → Mumbai to Pune (Maharashtra)             │
│  • Palakkad Gap (Palghat Gap) → Connects Kerala & Tamil Nadu        │
│    (Lowest pass in Western Ghats - very important!)                │
│                                                                    │
│  HIGHEST PEAKS:                                                    │
│  • Anamudi → 2695 m → HIGHEST peak of Peninsular India            │
│    (in Kerala, in Anaimalai Hills)                                 │
│  • Doddabetta → 2637 m → Highest peak of Nilgiri Hills             │
│  • Kudremukh → 1892 m → Karnataka                                 │
│                                                                    │
│  RIVERS ORIGINATING from Western Ghats:                            │
│  • Godavari, Krishna, Cauvery (flow EAST to Bay of Bengal)         │
│  • Periyar, Bharathapuzha (flow WEST to Arabian Sea)               │
└────────────────────────────────────────────────────────────────────┘
```

### Biodiversity Hotspot:
- Western Ghats is a **Biodiversity Hotspot** (one of 34 in the world)
- Home to: Lion-tailed macaque, Nilgiri Tahr, Purple frog
- Declared as **UNESCO World Natural Heritage Site in 2012**

> **PYQ TRAP:** "Which is higher — Western Ghats or Eastern Ghats?" → **Western Ghats** are higher (steeper escarpment on western side). Eastern Ghats are **discontinuous and lower**.

---

## 📌 GS CONCEPT 4: Eastern Ghats

```
┌────────────────────────────────────────────────────────────────────┐
│                    EASTERN GHATS — KEY FACTS                       │
├──────────────────────────────────────────────────────────────────  │
│  Location: Parallel to East Coast of India (Coromandel Coast)      │
│  Stretch: From Mahanadi (Odisha) to Nilgiri Hills (Tamil Nadu)    │
│  Length: About 1750 km                                             │
│  Nature: DISCONTINUOUS (cut by rivers into separate ranges)        │
│  Average height: 600 m (LOWER than Western Ghats)                 │
│                                                                    │
│  WHY DISCONTINUOUS?                                                │
│  → Major rivers (Mahanadi, Godavari, Krishna, Kaveri) cross        │
│    Eastern Ghats and break them into separate hill ranges          │
│                                                                    │
│  KEY HILL RANGES within Eastern Ghats:                             │
│  • Shevroy Hills                                                   │
│  • Javadi Hills                                                    │
│  • Nallamalai Hills                                                │
│  • Mahendragiri Hills (Odisha — highest point of Eastern Ghats)   │
│  • Shevaroy Hills / Servaroyan Hills (Tamil Nadu)                  │
│                                                                    │
│  HIGHEST PEAK:                                                     │
│  • Mahendragiri → 1501 m (Odisha)                                  │
│  • Jindhagada Peak → 1690 m (Andhra Pradesh) [some sources differ]│
│                                                                    │
│  STATES covered: Odisha, Andhra Pradesh, Tamil Nadu                │
└────────────────────────────────────────────────────────────────────┘
```

---

## 📌 GS CONCEPT 5: Western Ghats vs Eastern Ghats — COMPARISON

This comparison is a **DIRECT PYQ topic** — memorize every row:

```
┌────────────────────────────────────────────────────────────────────┐
│         WESTERN GHATS vs EASTERN GHATS — COMPARISON               │
├────────────────────┬────────────────────────┬──────────────────────┤
│ Feature            │ Western Ghats          │ Eastern Ghats        │
├────────────────────┼────────────────────────┼──────────────────────┤
│ Other Name         │ Sahyadri               │ No standard alt name │
│ Location           │ West Coast             │ East Coast           │
│ Length             │ ~1600 km               │ ~1750 km             │
│ Continuity         │ CONTINUOUS             │ DISCONTINUOUS        │
│ Height             │ HIGHER (~900-1500 m)   │ LOWER (~600 m avg)   │
│ Highest Peak       │ Anamudi (2695 m)       │ Mahendragiri (1501 m)│
│ Rainfall           │ HEAVY (windward side)  │ Moderate             │
│ UNESCO Status      │ World Heritage (2012)  │ Not UNESCO listed    │
│ Biodiversity       │ Hotspot                │ Not a hotspot        │
│ Passes             │ Palakkad, Thal, Bhor   │ No major passes      │
│ Escarpment         │ Steep on western side  │ Gentle slopes        │
│ Rivers             │ Periyar flows West;    │ Mahanadi, Krishna,   │
│                    │ Godavari flows East    │ Godavari cut through │
└────────────────────┴────────────────────────┴──────────────────────┘
```

---

## 📌 GS CONCEPT 6: Important Hill Ranges in Peninsular India

| Hill Range | State | Special Fact |
|-----------|-------|-------------|
| **Aravalli** | Rajasthan (mostly) | **Oldest fold mountain** of India; runs NE to SW |
| **Vindhya Range** | MP, UP | Divides North India from South India historically |
| **Satpura Range** | MP, Maharashtra | "Fold & Block" mountains; Pachmarhi hill station |
| **Nilgiri Hills** | Kerala, TN, Karnataka | "Junction" of Western & Eastern Ghats; Ooty here |
| **Cardamom Hills** | Kerala | Part of Western Ghats; spice region |
| **Anaimalai Hills** | Tamil Nadu, Kerala | Contains Anamudi (highest peak of South India) |
| **Nallamalai** | Andhra Pradesh | Part of Eastern Ghats |
| **Mahendragiri** | Odisha | Highest point of Eastern Ghats |

> **⭐ PYQ FACT:** Aravalli Hills is the **oldest fold mountain** of India. It is so old and worn down that it no longer appears as high mountains.

---

## 📌 GS CONCEPT 7: Rivers of the Peninsular Plateau

**Why do most peninsular rivers flow East?**
Because the Deccan Plateau **tilts from West to East** (western side is higher due to Western Ghats).

```
┌──────────────────────────────────────────────────────────────────┐
│                PENINSULAR RIVERS                                 │
│                                                                  │
│  EAST-FLOWING (into Bay of Bengal):                              │
│  • Mahanadi → Bay of Bengal (Odisha delta — largest delta)       │
│  • Godavari → "Vriddha Ganga" or "Dakshin Ganga"; largest       │
│    peninsular river; flows through AP & Telangana                │
│  • Krishna → Flows through Telangana, AP                         │
│  • Kaveri (Cauvery) → "Rice bowl river"; Karnataka & TN          │
│    Disputes: Karnataka vs Tamil Nadu water dispute               │
│  • Tungabhadra → Tributary of Krishna                            │
│                                                                  │
│  WEST-FLOWING (into Arabian Sea):                                │
│  • Narmada → Flows through RIFT VALLEY (not delta, estuary!)    │
│    → Marks boundary of Vindhya & Satpura; flows W to E... wait! │
│    → Actually flows WEST (anomaly because it flows in rift valley)│
│  • Tapi (Tapti) → Also flows WEST through rift valley            │
│  • Periyar, Bharathapuzha → Kerala rivers flowing west           │
│                                                                  │
│  ⭐ KEY FACT: Narmada & Tapi form ESTUARIES (not deltas)         │
│  because they flow through rift valleys at high speed            │
└──────────────────────────────────────────────────────────────────┘
```

> **PYQ TRAP:** "Which river forms a delta?" → Mahanadi, Godavari, Krishna, Kaveri form **deltas**. Narmada & Tapi form **estuaries** — common exam question!

---

## 📌 GS CONCEPT 8: Coastal Plains of India

```
┌──────────────────────────────────────────────────────────────────┐
│              COASTAL PLAINS COMPARISON                           │
├────────────────────┬───────────────────────┬─────────────────────┤
│ Feature            │ Western Coastal Plain  │ Eastern Coastal Plain│
├────────────────────┼───────────────────────┼─────────────────────┤
│ Coast Name         │ Konkan + Malabar Coast │ Coromandel Coast     │
│ Width              │ NARROW (avg 64 km)     │ WIDER (avg 100-120km)│
│ Rivers             │ Short, rapid rivers    │ Long, large rivers   │
│ Lagoons/Lakes      │ Some                   │ Chilika, Pulicat,    │
│                    │                        │ Kolleru lakes        │
│ Backwaters         │ Kerala — famous        │ Less prominent       │
│ Major Ports        │ Mumbai, Goa, Kochi,    │ Chennai, Visakhapatnam│
│                    │ Mangalore              │ Paradip, Kolkata     │
└────────────────────┴───────────────────────┴─────────────────────┘
```

### Famous Coastal Features:
- **Chilika Lake** (Odisha) — Largest coastal lagoon in India; Ramsar site
- **Vembanad Lake** (Kerala) — Longest lake in India; backwater
- **Pulicat Lake** (AP/TN border) — Second largest coastal lagoon
- **Kerala Backwaters** — Network of lagoons, canals, rivers along Malabar Coast

---

## 📌 GS CONCEPT 9: Important Passes in India

| Pass | State/Region | Connects |
|------|-------------|---------|
| **Palakkad Gap** | Kerala-Tamil Nadu | Only major gap in Western Ghats |
| **Bhor Ghat** | Maharashtra | Mumbai ↔ Pune |
| **Thal Ghat** | Maharashtra | Mumbai ↔ Nashik |
| **Zoji La** | J&K/Ladakh | Srinagar ↔ Leh |
| **Rohtang Pass** | Himachal Pradesh | Manali ↔ Lahaul-Spiti |
| **Nathu La** | Sikkim | India ↔ Tibet (China) |
| **Shipki La** | Himachal Pradesh | India ↔ Tibet |
| **Bomdi La** | Arunachal Pradesh | India ↔ Tibet |

> **PYQ FACT:** **Nathu La** in Sikkim is an important trade route between India and China. It was reopened in 2006 after 44 years.

---

## 📌 GS CONCEPT 10: Bihar-Specific Geography (Always Asked!)

Since this is Bihar exam, **Bihar geography questions appear every year**:

```
┌────────────────────────────────────────────────────────────────────┐
│                 BIHAR GEOGRAPHY — MUST KNOW FACTS                  │
├────────────────────────────────────────────────────────────────────┤
│  Location: 24°20'N to 27°31'N latitude; 83°19'E to 88°17'E        │
│  Area: 94,163 sq km → 12th largest state                           │
│  Borders: Nepal (N), West Bengal (E), Jharkhand (S), UP (W)        │
│                                                                    │
│  RIVERS OF BIHAR:                                                  │
│  • Ganga — main river, flows E-W through Bihar                     │
│  • Sone — major south bank tributary of Ganga in Bihar             │
│  • Gandak — north bank tributary; enters from Nepal                │
│  • Kosi — "Sorrow of Bihar"; very prone to flooding                │
│  • Bagmati — flows through North Bihar (from Nepal)                │
│  • Punpun — flows through Patna district                           │
│  • Falgu — flows through Gaya district (religious importance)      │
│                                                                    │
│  DIVISIONS & REGIONS:                                              │
│  • North Bihar (Mithila, Saran) — alluvial, flood-prone            │
│  • South Bihar (Magadha region) — Gaya, Patna; plateau-like       │
│                                                                    │
│  GEOGRAPHY FACTS:                                                  │
│  • No coastline (landlocked state)                                 │
│  • Mostly flat alluvial plains (part of Indo-Gangetic Plain)       │
│  • Kaimur Plateau (south-west) — part of Vindhya Range             │
│  • Rajgir Hills — oldest geological formations in Bihar            │
│  • Highest point: Soma Peak (in Kaimur district)                   │
└────────────────────────────────────────────────────────────────────┘
```

---

# ═══════════════════════════════════════════════════
# 📝 PRACTICE QUESTIONS
# ⚠️ SOLVE ALL QUESTIONS FIRST — ANSWERS ARE AT THE END
# ═══════════════════════════════════════════════════

---

# 🖥️ CS PRACTICE QUESTIONS (25 Questions)
### Topic: Stack — Expression Conversion (Infix/Postfix/Prefix)

---

**Q1.** The postfix form of the expression `A + B * C - D` is:

(A) A B C * + D -
(B) A B + C * D -
(C) A B C * D + -
(D) More than one of the above
(E) None of the above

---

**Q2.** The notation in which the operator comes AFTER its operands is called:

(A) Infix notation
(B) Prefix notation
(C) Polish notation
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the time complexity of converting an infix expression to postfix using a stack?

(A) O(log N)
(B) O(N²)
(C) O(N)
(D) More than one of the above
(E) None of the above

---

**Q4.** The infix expression `(A + B) * (C - D)` when converted to postfix becomes:

(A) A B + C D - *
(B) A B C D + - *
(C) + A B - C D *
(D) More than one of the above
(E) None of the above

---

**Q5.** Which data structure is primarily used for converting infix expression to postfix?

(A) Queue
(B) Linked List
(C) Stack
(D) More than one of the above
(E) None of the above

---

**Q6.** The Reverse Polish Notation (RPN) is another name for which type of expression?

(A) Infix
(B) Prefix
(C) Postfix
(D) More than one of the above
(E) None of the above

---

**Q7.** The prefix form of `A + B * C` is:

(A) A B C * +
(B) + A * B C
(C) * + A B C
(D) More than one of the above
(E) None of the above

---

**Q8.** When evaluating a postfix expression `5 3 2 * +`, what is the final result?

(A) 25
(B) 11
(C) 16
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following is a correct property of postfix notation?

(A) Parentheses are NOT needed
(B) Operator precedence rules are not required during evaluation
(C) It uses a Stack for evaluation
(D) More than one of the above
(E) None of the above

---

**Q10.** The infix expression `A ^ B ^ C` converts to postfix as:

(A) A B ^ C ^
(B) A B C ^ ^
(C) ^ A ^ B C
(D) More than one of the above
(E) None of the above

---

**Q11.** In the Infix to Postfix conversion algorithm, when we encounter a closing parenthesis `)`, we should:

(A) Push it onto the stack
(B) Pop operators until opening parenthesis `(` is found, and discard both parentheses
(C) Immediately add it to output
(D) More than one of the above
(E) None of the above

---

**Q12.** Which expression notation was invented by Jan Łukasiewicz?

(A) Infix notation
(B) Postfix notation (RPN)
(C) Prefix (Polish) notation
(D) More than one of the above
(E) None of the above

---

**Q13.** During postfix expression evaluation, two operands are popped. The operation is performed as:

(A) First_popped OPERATOR Second_popped
(B) Second_popped OPERATOR First_popped
(C) The order doesn't matter
(D) More than one of the above
(E) None of the above

---

**Q14.** Consider the postfix expression: `A B C + * D -`. What is its equivalent infix?

(A) A * B + C - D
(B) A * (B + C) - D
(C) (A * B) + (C - D)
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following operators has the HIGHEST precedence during infix to postfix conversion?

(A) + (Addition)
(B) * (Multiplication)
(C) ^ (Exponentiation)
(D) More than one of the above
(E) None of the above

---

**Q16.** The expression `A + B + C` in postfix is:

(A) A B C + +
(B) A B + C +
(C) + + A B C
(D) More than one of the above
(E) None of the above

---

**Q17.** Postfix notation is preferred over infix notation in computer systems primarily because:

(A) It is more human-readable
(B) It does not require knowledge of operator precedence during evaluation
(C) It always produces shorter expressions
(D) More than one of the above
(E) None of the above

---

**Q18.** The space complexity of Infix to Postfix conversion using a Stack is:

(A) O(1)
(B) O(log N)
(C) O(N)
(D) More than one of the above
(E) None of the above

---

**Q19.** When converting `A + B * C + D` to postfix, which is correct?

(A) A B C * + D +
(B) A B + C * D +
(C) A B C + * D +
(D) More than one of the above
(E) None of the above

---

**Q20.** The prefix expression `* + A B - C D` is equivalent to which infix expression?

(A) A + B * C - D
(B) (A + B) * (C - D)
(C) A * B + C * D
(D) More than one of the above
(E) None of the above

---

**Q21.** Evaluate the postfix expression: `2 3 ^ 4 -`

(A) 2
(B) 5
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q22.** The operator `^` (exponentiation) has which type of associativity?

(A) Left-to-Right
(B) Right-to-Left
(C) No associativity (not used)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following statements about Infix, Prefix, and Postfix is/are TRUE?

(i) Infix expressions sometimes require parentheses
(ii) Postfix expressions never require parentheses
(iii) Prefix expressions are read from Right to Left during evaluation

(A) Only (i) and (ii)
(B) Only (i)
(C) All of (i), (ii), and (iii)
(D) More than one of the above
(E) None of the above

---

**Q24.** If we reverse an infix expression, swap all `(` with `)` and vice versa, then apply infix-to-postfix algorithm, and finally reverse the result — we get:

(A) Postfix expression
(B) Prefix expression
(C) Same infix expression
(D) More than one of the above
(E) None of the above

---

**Q25.** In the Shunting Yard Algorithm developed by Edsger Dijkstra, operators with equal precedence are handled based on:

(A) Their ASCII value
(B) Their associativity (left or right)
(C) The length of the expression
(D) More than one of the above
(E) None of the above

---

# 🌍 GS PRACTICE QUESTIONS (25 Questions)
### Topic: India Geography — Physical Features (Eastern Ghats, Western Ghats, Peninsular Plateau)

---

**Q26.** Western Ghats is also known as:

(A) Satpura
(B) Sahyadri
(C) Aravalli
(D) More than one of the above
(E) None of the above

---

**Q27.** The highest peak of Peninsular India (South of Narmada) is:

(A) Doddabetta
(B) Mahendragiri
(C) Anamudi
(D) More than one of the above
(E) None of the above

---

**Q28.** Eastern Ghats are described as "discontinuous" because:

(A) They are lower in height than Western Ghats
(B) Major rivers like Godavari, Krishna, and Mahanadi cut through them
(C) They were formed later than Western Ghats
(D) More than one of the above
(E) None of the above

---

**Q29.** The Palakkad Gap (Palghat Gap) is located in:

(A) Maharashtra
(B) Karnataka
(C) Kerala — Tamil Nadu border
(D) More than one of the above
(E) None of the above

---

**Q30.** Which of the following rivers forms an estuary and NOT a delta?

(A) Godavari
(B) Mahanadi
(C) Narmada
(D) More than one of the above
(E) None of the above

---

**Q31.** The Deccan Plateau generally slopes from:

(A) East to West
(B) West to East
(C) North to South
(D) More than one of the above
(E) None of the above

---

**Q32.** Which of the following is a correct statement about Western Ghats?

(A) It was declared a UNESCO World Heritage Site in 2012
(B) It is a global biodiversity hotspot
(C) It is continuous (unlike Eastern Ghats)
(D) More than one of the above
(E) None of the above

---

**Q33.** The oldest fold mountain in India is:

(A) Vindhya Range
(B) Satpura Range
(C) Aravalli Hills
(D) More than one of the above
(E) None of the above

---

**Q34.** Chilika Lake, the largest coastal lagoon in India, is located in:

(A) Andhra Pradesh
(B) Tamil Nadu
(C) Odisha
(D) More than one of the above
(E) None of the above

---

**Q35.** The "Sorrow of Bihar" refers to which river?

(A) Gandak
(B) Kosi
(C) Ganga
(D) More than one of the above
(E) None of the above

---

**Q36.** Nathu La pass, reopened in 2006 for trade with China, is located in:

(A) Arunachal Pradesh
(B) Himachal Pradesh
(C) Sikkim
(D) More than one of the above
(E) None of the above

---

**Q37.** The Narmada river flows westward (contrary to most Peninsular rivers) because:

(A) It originates in the Western Ghats
(B) It flows through a rift valley (fault valley)
(C) It is the longest Peninsular river
(D) More than one of the above
(E) None of the above

---

**Q38.** Which of the following hill ranges form the junction of Eastern and Western Ghats?

(A) Cardamom Hills
(B) Shevaroy Hills
(C) Nilgiri Hills
(D) More than one of the above
(E) None of the above

---

**Q39.** The Peninsular Plateau of India is considered one of the oldest landmasses because:

(A) It is part of the ancient Gondwana supercontinent
(B) It is made of hard crystalline Archaean rocks
(C) It was formed by volcanic activity
(D) More than one of the above
(E) None of the above

---

**Q40.** The Western Coastal Plain (Malabar Coast) is known for which of the following unique features?

(A) Backwaters and lagoons (Kerala)
(B) Highest rainfall area in India (Cherrapunji)
(C) Delta formation by Narmada and Tapi
(D) More than one of the above
(E) None of the above

---

**Q41.** Which river is called "Dakshin Ganga" or "Vriddha Ganga"?

(A) Krishna
(B) Kaveri
(C) Godavari
(D) More than one of the above
(E) None of the above

---

**Q42.** The state of Bihar is bordered by which neighboring country to the north?

(A) China
(B) Bhutan
(C) Nepal
(D) More than one of the above
(E) None of the above

---

**Q43.** Mahendragiri, the highest point of Eastern Ghats, is located in:

(A) Andhra Pradesh
(B) Tamil Nadu
(C) Odisha
(D) More than one of the above
(E) None of the above

---

**Q44.** The Kaveri river dispute is between which two states?

(A) Andhra Pradesh and Karnataka
(B) Karnataka and Tamil Nadu
(C) Tamil Nadu and Kerala
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following is/are tributary/tributaries of the Ganga in Bihar?

(A) Sone
(B) Gandak
(C) Kosi
(D) More than one of the above
(E) None of the above

---

**Q46.** The Kaimur Plateau in Bihar is geologically part of:

(A) Eastern Ghats
(B) Satpura Range
(C) Vindhya Range
(D) More than one of the above
(E) None of the above

---

**Q47.** The Vembanad Lake, the longest lake in India, is located in:

(A) Goa
(B) Odisha
(C) Kerala
(D) More than one of the above
(E) None of the above

---

**Q48.** Which pass in Maharashtra connects Mumbai to Pune?

(A) Thal Ghat
(B) Bhor Ghat
(C) Palakkad Gap
(D) More than one of the above
(E) None of the above

---

**Q49.** The Godavari river drains into:

(A) Arabian Sea
(B) Bay of Bengal
(C) Gulf of Kutch
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following statements is/are CORRECT about Bihar?

(A) Bihar is a landlocked state with no coastline
(B) Bihar's Kosi river is known for frequent floods
(C) The Falgu river flows through Gaya district and has religious significance
(D) More than one of the above
(E) None of the above

---

---
---

# ═══════════════════════════════════════════════════
# ✅ ANSWER KEY — DAY 17
# (Check only AFTER attempting all 50 questions)
# ═══════════════════════════════════════════════════

---

## 🖥️ CS ANSWERS (Q1–Q25)

---

### Q1. Answer: **(A) A B C * + D -**

**Explanation:**
Expression: `A + B * C - D`

Step-by-step trace:
- `A` → Output: `A`
- `+` → Stack: `+`
- `B` → Output: `A B`
- `*` → Stack: `+ *` (higher precedence than +)
- `C` → Output: `A B C`
- `-` → Pop `*` (higher prec), pop `+` (equal prec to -), push `-`; Output: `A B C * +`
- `D` → Output: `A B C * + D`
- END → Pop `-`; Output: `A B C * + D -`

✅ Answer = A B C * + D -

---

### Q2. Answer: **(E) None of the above**

**Explanation:**
The notation where operator comes AFTER operands is called **Postfix notation** (also called Reverse Polish Notation). None of the options (A), (B), (C) says "Postfix" explicitly. Option (C) says "Polish notation" which is actually **PREFIX** notation. So the correct term is **Postfix**, which is not in options A/B/C → **(E) None of the above**.

⚠️ **TRAP:** Polish Notation = PREFIX; Reverse Polish Notation = POSTFIX. Don't confuse!

---

### Q3. Answer: **(C) O(N)**

**Explanation:**
Each character of the expression is processed exactly ONCE — either pushed to stack or added to output. Hence Time = O(N). This was a **direct PYQ in TRE 2.0**.

---

### Q4. Answer: **(A) A B + C D - ***

**Explanation:**
`(A + B) * (C - D)`:
- `(` → push
- `A` → output: A
- `+` → stack: `( +`
- `B` → output: A B
- `)` → pop `+` → output: A B +
- `*` → stack: `*`
- `(` → stack: `* (`
- `C` → output: A B + C
- `-` → stack: `* ( -`
- `D` → output: A B + C D
- `)` → pop `-` → output: A B + C D -
- END → pop `*` → output: A B + C D - *

✅ = A B + C D - *

---

### Q5. Answer: **(C) Stack**

**Explanation:**
The Infix to Postfix algorithm requires exactly ONE Stack to hold operators temporarily. This is a fundamental data structure application question.

---

### Q6. Answer: **(C) Postfix**

**Explanation:**
RPN = Reverse Polish Notation = POSTFIX. Polish Notation (PN) = PREFIX. Never mix these up in exam!

---

### Q7. Answer: **(B) + A * B C**

**Explanation:**
`A + B * C` in Prefix means: `+` applied to `A` and `(* B C)`
→ `+ A * B C`

Verification: `+ A * B C` = A + (B * C) ✓

Option (A) is the POSTFIX form, not prefix.

---

### Q8. Answer: **(B) 11**

**Explanation:**
Postfix: `5 3 2 * +`
- Push 5 → Stack: [5]
- Push 3 → Stack: [5, 3]
- Push 2 → Stack: [5, 3, 2]
- `*` → Pop 2,3 → 3*2 = 6 → Stack: [5, 6]
- `+` → Pop 6,5 → 5+6 = 11 → Stack: [11]

Result = **11**

---

### Q9. Answer: **(D) More than one of the above**

**Explanation:**
ALL THREE statements (A), (B), and (C) are correct properties of Postfix notation:
- Parentheses NOT needed ✓
- Operator precedence NOT required during evaluation ✓
- Uses Stack for evaluation ✓

When multiple options are correct → Answer is **(D)**. This is the classic BPSC TRE trap!

---

### Q10. Answer: **(B) A B C ^ ^**

**Explanation:**
`A ^ B ^ C` — `^` is RIGHT-to-LEFT associative.
This means: `A ^ (B ^ C)`.

During conversion:
- `A` → output: A
- `^` → stack: `^`
- `B` → output: A B
- `^` → Because `^` is RIGHT associative, when we see same-precedence `^`, we DO NOT pop the existing `^`. Push → stack: `^ ^`
- `C` → output: A B C
- END → pop `^` → A B C ^, then pop `^` → A B C ^ ^

Result = A B C ^ ^

---

### Q11. Answer: **(B)**

**Explanation:**
When `)` is encountered: pop operators from stack and add to output UNTIL `(` is found. Discard BOTH `(` and `)`. The `(` is never added to output.

---

### Q12. Answer: **(C) Prefix (Polish) notation**

**Explanation:**
Jan Łukasiewicz was a Polish logician who invented **Prefix notation**, which is why it's called **Polish Notation**. Postfix (RPN = Reverse Polish) was named after him too, but HE invented Prefix. Dijkstra invented the Shunting Yard algorithm for conversion.

---

### Q13. Answer: **(B) Second_popped OPERATOR First_popped**

**Explanation:**
When we pop two operands: first pop = right operand, second pop = left operand.
Example: Stack has [5, 3], pop gives 3 first (right), 5 second (left).
`5 - 3` = 2, not `3 - 5` = -2.
So: **second_popped OPERATOR first_popped** = correct.

---

### Q14. Answer: **(B) A * (B + C) - D**

**Explanation:**
Evaluate postfix `A B C + * D -`:
- A → push
- B → push
- C → push
- `+` → pop C, B → B+C → push (B+C)
- `*` → pop (B+C), A → A*(B+C) → push
- D → push
- `-` → pop D, A*(B+C) → A*(B+C) - D

Result = **A * (B + C) - D**

---

### Q15. Answer: **(C) ^ (Exponentiation)**

**Explanation:**
Operator precedence (High to Low): `^` > `* / %` > `+ -`
Exponentiation has the HIGHEST precedence in standard expression evaluation.

---

### Q16. Answer: **(B) A B + C +**

**Explanation:**
`A + B + C` — `+` is left-associative, so: `(A + B) + C`
- A → output: A
- `+` → stack: `+`
- B → output: A B
- `+` → equal prec, left-assoc → pop `+` → output: A B +, push new `+`
- C → output: A B + C
- END → pop `+` → A B + C +

Result = **A B + C +**

---

### Q17. Answer: **(B)**

**Explanation:**
The PRIMARY reason postfix is preferred is: **no need for precedence rules during evaluation**. This makes it efficient for stack-based computer evaluation. It is NOT more human-readable (that's infix's advantage). Expressions aren't necessarily shorter in postfix.

---

### Q18. Answer: **(C) O(N)**

**Explanation:**
The Stack used in Infix-to-Postfix can hold at most N operators (in case of all operators, no operands). Hence Space Complexity = **O(N)**.

---

### Q19. Answer: **(A) A B C * + D +**

**Explanation:**
`A + B * C + D`:
- A → output: A
- `+` → stack: `+`
- B → output: A B
- `*` → stack: `+ *` (higher prec)
- C → output: A B C
- `+` → pop `*` → output: A B C *, pop `+` → output: A B C * +, push `+`
- D → output: A B C * + D
- END → pop `+` → A B C * + D +

Result = **A B C * + D +**

---

### Q20. Answer: **(B) (A + B) * (C - D)**

**Explanation:**
Prefix `* + A B - C D`:
- `*` applied to (`+ A B`) and (`- C D`)
- `+ A B` = A + B
- `- C D` = C - D
- Result = (A + B) * (C - D)

---

### Q21. Answer: **(B) 5**

**Explanation:**
Postfix: `2 3 ^ 4 -`
- Push 2 → [2]
- Push 3 → [2, 3]
- `^` → pop 3,2 → 2^3 = 8 → [8]
- Push 4 → [8, 4]
- `-` → pop 4, 8 → 8 - 4 = 4... 

Wait — recalculate: 2^3 = 8, then 8 - 4 = **4**.

Hmm — re-checking: 2^3 = 8. 8 - 4 = 4. 

So answer is **(E) None of the above** since 4 is option C... Actually option C is 4.

✅ **Answer: (C) 4**

*(The answer for Q21 is (C) 4. Correction: 2^3 = 8, 8-4 = 4)*

---

### Q22. Answer: **(B) Right-to-Left**

**Explanation:**
Exponentiation `^` has RIGHT-to-LEFT associativity. This means `A ^ B ^ C` = `A ^ (B ^ C)`. This is critical for correct postfix conversion and a BPSC trap question!

---

### Q23. Answer: **(D) More than one of the above**

**Explanation:**
All three statements are correct:
- (i) Infix sometimes needs parentheses ✓
- (ii) Postfix never needs parentheses ✓
- (iii) Prefix expressions are evaluated by reading from Right to Left ✓

All three are true → **(D)** which means "More than one of the above"

---

### Q24. Answer: **(B) Prefix expression**

**Explanation:**
This is the standard algorithm for **Infix to PREFIX conversion**:
1. Reverse the infix (and swap parentheses)
2. Apply Infix-to-Postfix algorithm
3. Reverse the result

This gives you the PREFIX (Polish Notation) of the original expression.

---

### Q25. Answer: **(B) Their associativity (left or right)**

**Explanation:**
In Dijkstra's Shunting Yard Algorithm: when two operators have EQUAL precedence, the decision to pop or not pop is based on **associativity**:
- Left-associative: Pop the existing operator (push new one)
- Right-associative: Do NOT pop (push the new one directly)

---

## 🌍 GS ANSWERS (Q26–Q50)

---

### Q26. Answer: **(B) Sahyadri**

**Explanation:**
Western Ghats = **Sahyadri** Mountains. This is a direct and frequently asked BPSC question. Satpura is a separate range in Madhya Pradesh. Aravalli is in Rajasthan.

---

### Q27. Answer: **(C) Anamudi**

**Explanation:**
**Anamudi** (2695 m) is the highest peak of Peninsular India (South of Narmada), located in Kerala's Anaimalai Hills. Doddabetta (2637 m) is the highest peak of Nilgiri Hills but lower than Anamudi. Mahendragiri (1501 m) is the highest peak of Eastern Ghats only.

---

### Q28. Answer: **(B)**

**Explanation:**
Eastern Ghats are **discontinuous** because major rivers — Mahanadi, Godavari, Krishna, Kaveri — flow through them (east-draining rivers), cutting the range into isolated hills. This is a direct PYQ-level fact!

Option (D) would be "More than one" — but only (B) is correct here. (A) is a fact but doesn't explain WHY they're discontinuous.

---

### Q29. Answer: **(C) Kerala — Tamil Nadu border**

**Explanation:**
**Palakkad Gap** (also called Palghat Gap) is the only significant gap/break in the Western Ghats, located between Kerala and Tamil Nadu. It is an important route for railways and roads connecting these two states. Highest point avoided! Many rivers and transport routes pass through here.

---

### Q30. Answer: **(C) Narmada**

**Explanation:**
**Narmada** and Tapi (Tapti) form **estuaries** (not deltas) because they flow through rift/fault valleys with fast-moving water. They don't deposit enough sediment to form deltas. Godavari and Mahanadi form **deltas**. Classic BPSC exam question!

---

### Q31. Answer: **(B) West to East**

**Explanation:**
The Deccan Plateau slopes from **West to East**. Western Ghats form the western rim and are higher, so water drains eastward. This is why most peninsular rivers (Godavari, Krishna, Kaveri) flow east into the Bay of Bengal.

---

### Q32. Answer: **(D) More than one of the above**

**Explanation:**
ALL THREE statements (A), (B), and (C) are CORRECT:
- UNESCO World Heritage Site (2012) ✓
- Global biodiversity hotspot ✓
- Continuous range ✓

Classic **Option D trap** — when all options are correct, answer is D!

---

### Q33. Answer: **(C) Aravalli Hills**

**Explanation:**
**Aravalli Hills** is the **oldest fold mountain** of India, running northeast to southwest through Rajasthan and Gujarat. It is so ancient and eroded that it barely looks like a mountain range anymore. Vindhya and Satpura are relatively younger geological formations.

---

### Q34. Answer: **(C) Odisha**

**Explanation:**
**Chilika Lake** is located in Odisha and is India's largest coastal lagoon and saltwater lake. It is a **Ramsar site** (internationally important wetland). It is also famous for Irrawaddy dolphins and migratory birds.

---

### Q35. Answer: **(B) Kosi**

**Explanation:**
**Kosi river** is called the "**Sorrow of Bihar**" because it frequently changes course and causes devastating floods in North Bihar. It is known as "the river that mourns" in local culture.

---

### Q36. Answer: **(C) Sikkim**

**Explanation:**
**Nathu La** pass is located in **Sikkim**, on the India-China (Tibet) border. It was a historic Silk Route pass. It was reopened in 2006 after being closed since the 1962 Indo-China war.

---

### Q37. Answer: **(B)**

**Explanation:**
Narmada flows westward because it flows through a **rift valley** (also called fault valley or graben) formed by geological faults. The Vindhya and Satpura ranges form the boundaries of this rift. This creates a funnel that directs the river westward into the Arabian Sea — forming an estuary, not a delta.

---

### Q38. Answer: **(C) Nilgiri Hills**

**Explanation:**
**Nilgiri Hills** form the point where Eastern and Western Ghats meet (the junction). This is why Nilgiri Hills are broader and higher than the Eastern Ghats. The famous hill station Ooty (Udhagamandalam) is located here. Cardamom Hills are part of Western Ghats only.

---

### Q39. Answer: **(D) More than one of the above**

**Explanation:**
BOTH (A) and (B) are correct:
- Part of ancient **Gondwana supercontinent** ✓
- Made of hard **crystalline Archaean rocks** ✓

(C) is not entirely correct — not formed by volcanic activity (that's Deccan Traps, a different feature). Since A and B are both correct → **(D)**.

---

### Q40. Answer: **(A)**

**Explanation:**
The Western Coastal Plain (Malabar Coast, Kerala) is specifically famous for **backwaters and lagoons** — a unique network of canals, rivers, and lagoons. Cherrapunji (highest rainfall) is in Meghalaya, not Western Coast. Narmada & Tapi form estuaries, not deltas.

---

### Q41. Answer: **(C) Godavari**

**Explanation:**
**Godavari** is called "**Dakshin Ganga**" (Ganga of the South) or "**Vriddha Ganga**" (Old Ganga) because it is the largest peninsular river. It flows through Maharashtra, Telangana, and Andhra Pradesh before entering the Bay of Bengal.

---

### Q42. Answer: **(C) Nepal**

**Explanation:**
Bihar shares its northern border with **Nepal**. Bihar's borders: Nepal (North), West Bengal (East), Jharkhand (South), Uttar Pradesh (West). Several rivers like Kosi, Gandak, and Bagmati enter Bihar from Nepal.

---

### Q43. Answer: **(C) Odisha**

**Explanation:**
**Mahendragiri** (approximately 1501 m) is considered the highest point of Eastern Ghats, located in **Odisha** (Gajapati district). Some sources give Jindhagada Peak in Andhra Pradesh as higher, but in standard BPSC/competitive exams, Mahendragiri is the accepted answer.

---

### Q44. Answer: **(B) Karnataka and Tamil Nadu**

**Explanation:**
The **Kaveri (Cauvery) water dispute** is between **Karnataka** (upstream) and **Tamil Nadu** (downstream). The Cauvery Water Tribunal gave its final award in 2007. This dispute has been ongoing for decades and is a frequently asked GK question.

---

### Q45. Answer: **(D) More than one of the above**

**Explanation:**
ALL THREE — Sone, Gandak, and Kosi — are tributaries of Ganga in Bihar:
- **Sone** — south bank tributary ✓
- **Gandak** — north bank, from Nepal ✓
- **Kosi** — north bank, from Nepal ✓

All three are correct → **(D)**.

---

### Q46. Answer: **(C) Vindhya Range**

**Explanation:**
The **Kaimur Plateau** in southwestern Bihar is geologically an extension of the **Vindhya Range**. It runs along the Bihar-UP-MP border. This is a frequently asked Bihar geography question. The plateau contains forests and is part of the Kaimur Wildlife Sanctuary.

---

### Q47. Answer: **(C) Kerala**

**Explanation:**
**Vembanad Lake** is located in **Kerala** and is the longest lake in India (96.5 km long). It is a backwater lake. The famous Nehru Trophy Boat Race is held on Vembanad Lake. It is also a Ramsar Wetland site.

---

### Q48. Answer: **(B) Bhor Ghat**

**Explanation:**
**Bhor Ghat** (Bhorghat) connects **Mumbai to Pune** in Maharashtra. Thal Ghat connects Mumbai to Nashik. Both are important passes in the Western Ghats through which major railway and road routes pass.

---

### Q49. Answer: **(B) Bay of Bengal**

**Explanation:**
**Godavari** flows from Nasik in Maharashtra and empties into the **Bay of Bengal** near Rajahmundry in Andhra Pradesh, forming a large delta. All major east-flowing peninsular rivers (Mahanadi, Godavari, Krishna, Kaveri) drain into the Bay of Bengal.

---

### Q50. Answer: **(D) More than one of the above**

**Explanation:**
ALL THREE statements are correct about Bihar:
- (A) Bihar is landlocked — no coastline ✓
- (B) Kosi = Sorrow of Bihar, known for floods ✓
- (C) Falgu river flows through Gaya; it has immense religious significance (Pindadan — offering to ancestors; site of Buddha's enlightenment nearby) ✓

All three correct → **(D)** — the classic BPSC D-option trap!

---

# ═══════════════════════════════════════════════════
# 📋 DAY 17 — QUICK REVISION SUMMARY
# ═══════════════════════════════════════════════════

## CS Quick Facts to Remember:

```
1. Infix → uses operators BETWEEN operands (A + B)
2. Postfix → uses operators AFTER operands (A B +) = RPN
3. Prefix → uses operators BEFORE operands (+ A B) = Polish Notation
4. Infix to Postfix: uses STACK, Time O(N), Space O(N)
5. ^ is RIGHT-to-LEFT associative; +,-,*,/ are LEFT-to-RIGHT
6. Postfix needs NO parentheses, NO precedence during evaluation
7. When evaluating postfix: 2nd popped is LEFT operand, 1st popped is RIGHT
8. Shunting Yard Algorithm (Dijkstra) → converts infix to postfix
9. Postfix evaluation: operand→push; operator→pop 2, operate, push result
10. Prefix: read RIGHT to LEFT for evaluation
```

## GS Quick Facts to Remember:

```
1. Western Ghats = SAHYADRI; Continuous; Higher; Biodiversity Hotspot
2. Eastern Ghats = Discontinuous (cut by rivers); Lower; No UNESCO status
3. Highest peak South India = ANAMUDI (2695 m) in Kerala
4. Highest peak Eastern Ghats = MAHENDRAGIRI (Odisha)
5. Oldest fold mountain India = ARAVALLI HILLS
6. Deccan Plateau slopes WEST to EAST → rivers flow EAST
7. Narmada & Tapi form ESTUARIES (not deltas) — flow through RIFT valleys
8. Godavari = Dakshin Ganga / Vriddha Ganga
9. Kosi = Sorrow of Bihar
10. Chilika Lake = Largest coastal lagoon (Odisha) = Ramsar site
11. Palakkad Gap = only break in Western Ghats (Kerala-TN border)
12. Nathu La = Sikkim → Trade pass with China (reopened 2006)
13. Nilgiri Hills = Junction of Eastern + Western Ghats
14. Bihar: Landlocked; bordered by Nepal (N), WB (E), Jharkhand (S), UP (W)
```

---

*Day 17 Complete | Next: Day 18 → Queue: FIFO, Types & Operations | GS: India Physical Geography (Peninsular Plateau)*

---
> **Score yourself:** CS ___/25 | GS ___/25 | Total ___/50
> **Target:** 45+ → Excellent | 40+ → Good | Below 35 → Revise concepts again
